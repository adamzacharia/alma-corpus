# High-resolution Study of the Outflow Activity and Chemical Environment of Chamaeleon-MMS1

`2024ApJ...971..187A` | The Astrophysical Journal 2024 | first author: Allen, Veronica | arXiv: 2010.01151 | DOI: 10.3847/1538-4357/ad5182

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Characterise the local outflow activity of Cha-MMS1 and its effect on the surrounding gas (CO, CS, H2CO, CH3OH) to determine whether the source is a First Hydrostatic Core or a very young Class 0 protostar  
  > "and its effect on the surrounding material in order to determine the evolutionary state of this young low-mass source." (abstract); "The molecular tracers CS, formaldehyde (H$_2$CO), and methanol (CH$_3$OH) were used to analyze the effect of the outflow on the surrounding gas" (abstract)
- Target **Chamaeleon-MMS1 (Cha-MMS1)**: coordinates _not stated_; z/distance 192 pc  
  > "is a young protostar located at a distance of 192 pc (cite: Dzib2018)" (Introduction); "The pointing position of our ALMA observations was the millimeter position reported in (cite: Reipurth1996) rather than the Spitzer IR peak" (Observations and data reduction); distance from Dzib2018  
  > "is a young protostar located at a distance of 192 pc (cite: Dzib2018)" (Introduction); "The pointing position of our ALMA observations was the millimeter position reported in (cite: Reipurth1996) rather than the Spitzer IR peak" (Observations and data reduction)

## Data provenance

- ALMA projects: 2013.1.01113.S
- bands: Band 6, 220 GHz  
  > "We observed Cha-MMS1 with ALMA in Band 6 at high angular resolution" (Conclusions); "to observe Chamaeleon-MMS1 at 220 GHz" (abstract)
- frequencies and spectral setup: Spectral resolution ~0.08 km/s in three windows (12CO, 13CO, CS), 0.17 km/s for H2CO (218222 MHz), 0.3 km/s in the other four windows; seven windows in total  
  > "spectral resolutions of $\sim$0.08 km s$^{-1}$ in three spectral windows (covering $^{12}$CO, $^{13}$CO and CS), 0.17 km s$^{-1}$ for H$_2$CO (218222 MHz), and 0.3 km s$^{-1}$ in the other four spectral windows" (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 26 antennas (16 July 2014); 37-39 antennas (6 and 7 June 2015); array type not stated  
  > "using 26 antennas on 16 July, and 37-39 antennas on 6 and 7 June" (Observations and data reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.7 arcsec (~75 AU)  
  > "with an angular resolution of $\sim0.7''$" (Observations and data reduction); "at high spatial ($\sim75$ AU)" (abstract)
- max recoverable scale: _not stated_
- sensitivity: RMS noise in line-free channels typically 2-4 mJy  
  > "The RMS noise for line-free channels was typically 2-4 mJy." (Observations and data reduction)
- time on source: _not stated_
- observing dates: 16 July 2014; 6 and 7 June 2015  
  > "on 16 July 2014 and 6 and 7 June 2015" (Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: CO 2-1 (230.5380 GHz)
- Line: 13CO 2-1 (220.3986 GHz)
- Line: CS 5-4 (244.9355 GHz)
- Line: H2CO 3_{0,3}-2_{2,1} (218.2221 GHz)
- Line: H2CO 3_{2,2}-2_{2,1} (218.4756 GHz)
- Line: H2CO 3_{1,2}-2_{1,1} (225.6977 GHz)
- Line: CH3OH 5_{3,2}-4_{3,1} (218.4400 GHz)
- Line: CH3OH 5_{-1,5}-4_{-1,4} (241.7672 GHz)
- Line: CH3OH 5_{0,5}-4_{0,4}++ (241.7914 GHz)
- Line: HC3N 24-23 (not detected) (218.3247 GHz)
- External data: Upper-level energies and Einstein A coefficients of the targeted lines from CDMS  
  > "Targeted spectral lines (E$_{\mathrm{up}}$ and A$_{\mathrm{ij}}$ from CDMS)" (Table 1) [from CDMS (no cite key given)]
- External data: Distance to Cha-MMS1 of 192 pc  
  > "is a young protostar located at a distance of 192 pc (cite: Dzib2018)" (Introduction) [from (cite: Dzib2018)]
- External data: Internal luminosity of Cha-MMS1 between 0.08 and 0.18 Lsun  
  > "as either an extremely young VeLLO or an FHSC with an internal luminosity between 0.08 and 0.18" (Introduction) [from (cite: Tsitali)]
- External data: Typical CO abundance of 1e-4 used to convert CO to H2 column density  
  > "assuming a CO abundance of 10$^{-4}$, as is typical (cite: Bolatto2013)" (3.2.3 Mechanical outflow properties) [from (cite: Bolatto2013)]
- External data: Expected outflow momentum rate, mass and mechanical luminosity for a young star of given bolometric luminosity (trends)  
  > "Using the trends outlined in (cite: Wu2004), we calculated the momentum rate, outflow mass, and mechanical luminosity expected from a young star" (3.2.3 Mechanical outflow properties) [from (cite: Wu2004)]
- External data: H2CO sublimation temperature 144 K from experiments  
  > "based on the experimentally-measured sublimation temperature (144 K, (cite: Noble2012))" (3.4 H2CO emission) [from (cite: Noble2012)]
- External data: CH3OH sublimation temperature 128 K from experiments  
  > "the sublimation temperature of CH$_3$OH derived from experiments (128 K; (cite: Penteado2017))" (3.5 CH3OH emission) [from (cite: Penteado2017)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.4.0  
  > "Data reduction was performed with the CASA package (version 5.4.0)." (Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Calibrators listed (roles not stated): Callisto, Ganymede, J0635-7516, J1058-8003, J1208-7809, J1107-4449, J0538-4405  
  > "The calibrators used were Callisto, Ganymede, J0635-7516, J1058-8003, J1208-7809, J1107-4449, and J0538-4405." (Observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "Imaging was done using the tclean process with a Hogbom deconvolver" (Observations and data reduction)
- deconvolver: Hogbom  
  > "Imaging was done using the tclean process with a Hogbom deconvolver and Briggs weighting with a robust parameter of 0.5" (Observations and data reduction)
- weighting robust: Briggs, robust = 0.5  
  > "Briggs weighting with a robust parameter of 0.5" (Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum subtracted after concatenating spectral windows (method not stated)  
  > "Corresponding spectral windows from different observation dates were concatenated and the continuum was subtracted." (Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: All images primary beam corrected  
  > "all images are primary beam corrected" (Observations and data reduction)
- array combination: Corresponding spectral windows from the different observation dates concatenated  
  > "Corresponding spectral windows from different observation dates were concatenated" (Observations and data reduction)
- smoothing: _not stated_
- final beam: ~0.7 arcsec angular resolution  
  > "with an angular resolution of $\sim0.7''$" (Observations and data reduction)
- final rms: typically 2-4 mJy in line-free channels  
  > "The RMS noise for line-free channels was typically 2-4 mJy." (Observations and data reduction)

### Inherited from earlier work

- Approach for calculating outflow mechanical properties  
  > "We used the approach described in (cite: AlvaroOutflows) and (cite: AnaOutflows) to calculate the mechanical outflow properties." (3.2.3 Mechanical outflow properties) [from (cite: AlvaroOutflows) and (cite: AnaOutflows)]
- Optically thin CO column density using equations (10) and (19)  
  > "The CO column density was determined assuming optically thin emission as in (cite: Goldsmith1999) equations (10) and (19) assuming excitation temperatures of 10, 20, and 30 K." (3.2.3 Mechanical outflow properties) [from (cite: Goldsmith1999)]
- Inclination correction factors for outflow properties  
  > "we applied the inclination correction factors from (cite: Ana2010) assuming an inclination of 80$^{\circ}$" (3.2.3 Mechanical outflow properties) [from (cite: Ana2010)]

### Not stated but needed to reproduce (our reading)

- Array configurations, baseline range and maximum recoverable scale of the three execution blocks
- Which calibrator was used for flux, bandpass, phase and pointing, and any self-calibration or flux scale uncertainty
- Whether the pipeline or manual scripts were used, and the exact calibration scripts
- Image cell size, image size, mask definition, clean threshold and number of iterations
- Method and line-free channels used for continuum subtraction, and the continuum bandwidth
- Channel width and any smoothing of the cubes used for moment maps and spectra
- Exact apertures and regions (Main, N, S, W) and lobe boundaries used for spectra and outflow measurements, and the velocity limits used for each lobe
- Which systemic velocity was used (4.5, 4.9 and 6.94 km/s all appear) and how V_max was defined for each lobe
- Details of the CASSIS rotational-diagram fits (line-width treatment, optical depth, error treatment, beam filling)
- Source coordinates and the millimeter position used for the phase centre

## Analysis recipe

1. **Make cubes, continuum image and moment maps**: tclean imaging then integrated-intensity (moment) maps of broad and narrow 12CO, 13CO, CS, H2CO and CH3OH features  
  > "Moment maps were also made of narrow spectral features in $^{12}$CO and $^{13}$CO" (3.1 Continuum and Line Detection); "integrated intensity maps (between 5.7 and 8.7 km s$^{-1}$ and 5.1 and 6.0 km s$^{-1}$, respectively)" (3.2.2 Narrow bipolar outflow)
   - software: CASA, tclean
   - parameter: Hogbom deconvolver, Briggs robust 0.5, primary beam corrected  
  > "Imaging was done using the tclean process with a Hogbom deconvolver and Briggs weighting with a robust parameter of 0.5 and all images are primary beam corrected." (Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit Gaussian profiles to outflow components**: Gaussian fits to the 12CO (and 13CO) line profiles of the broad red, narrow red and blue components to get centre velocity and FWHM  
  > "A Gaussian fit made to this component of the $^{12}$CO emission shows that the center is at 10.9$\pm$0.2 km s$^{-1}$" (3.2.1 Broad red outflow component)
   - fitting: Gaussian line-profile fit; fitting code, priors and likelihood not stated  
  > "A Gaussian fit of the southern blue component has a central velocity of 3.40$\pm$0.01 km s$^{-1}$" (3.2.1 Broad red outflow component)
   - validation: _not stated_
3. **Derive outflow mechanical properties per lobe**: Measure v_max, major-axis length at 5 sigma, lobe area as an ellipse and integrated intensity; compute CO column density (optically thin, Tex 10, 20, 30 K averaged), H2 column density, outflow mass, kinetic time, energy, momentum, mass-loss rate, momentum rate and mechanical luminosity, with inclination correction  
  > "The measured properties for each outflow lobe are: the difference between the maximum velocity and systemic velocity (v$_{max}$), the length of the major axis (at the 5$\sigma$ contour), the area of the outflow (as an ellipse)" (3.2.3 Mechanical outflow properties); "kinetic energy (outflow mass times 0.5 v$_{max}^2$), momentum (outflow mass times v$_{max}$)" (3.2.3 Mechanical outflow properties)
   - parameter: Excitation temperatures of 10, 20 and 30 K; average CO column density used  
  > "The calculated CO column densities varied by a factor of 3-4 between the different temperatures, so we used the average for calculating the hydrogen column density" (3.2.3 Mechanical outflow properties)
   - assumption: CO abundance 1e-4 relative to H2  
  > "assuming a CO abundance of 10$^{-4}$, as is typical (cite: Bolatto2013)" (3.2.3 Mechanical outflow properties)
   - assumption: Optical depth correction tau = 5 for self-absorbed CO near systemic velocity  
  > "Because the CO emission showed strong self-absorption at velocities near the velocity of the system (v$_{\mathrm{LSR}}$=4.9 km s$^{-1}$), the CO intensities were corrected assuming an $\tau$ value of 5." (3.2.3 Mechanical outflow properties)
   - assumption: Inclination 80 deg, determined geometrically from the northern red opening angle and presence of red and blue components  
  > "We determined this inclination geometrically taking into account the opening angle of the northern red outflow and the presence of red and blue components in each direction." (3.2.3 Mechanical outflow properties)
   - fitting: _not stated_
   - validation: Compared with the CO(3-2) outflow properties of Busch2020  
  > "The line of sight outflow properties we calculated using the CO (2-1) transition are generally similar to the values in (cite: Busch2020)" (4.2.1 Mechanical properties)
4. **Compare outflow with expected values for a young star**: Compare outflow mass, momentum rate and mechanical luminosity with the trends of Wu2004 for L_bol of 0.08-0.18  
  > "Using the trends outlined in (cite: Wu2004), we calculated the momentum rate, outflow mass, and mechanical luminosity expected from a young star" (3.2.3 Mechanical outflow properties)
   - fitting: _not stated_
   - validation: _not stated_
5. **Rotation temperature and column density of H2CO in four regions**: Rotational diagrams from three H2CO transitions toward Main, N, S and W regions  
  > "determined using the H$_2$CO transitions in a rotational diagram in the CASSIS software" (3.4 H2CO emission)
   - software: CASSIS, CDMS
   - assumption: Rotational, gas and dust temperatures are equal at the densities of the condensations  
  > "The gas in these condensations appears to be sufficiently dense for the rotational temperature, gas temperature, and dust temperature to be equal" (3.4 H2CO emission)
   - fitting: _not stated_
   - validation: Fit toward N flagged as poor because of low flux of the 218.475 GHz line  
  > "the fit for N was poor due to the low flux of the transition at 219475 MHz" (Table 2)
6. **Rotation temperature and column density of CH3OH**: Rotational diagrams from three CH3OH transitions toward N, S and W; upper limit toward Main  
  > "Using detected emission from three H$_2$CO transitions and three CH$_3$OH, we created rotational diagrams to determine the gas temperature and column density" (4.3 Chemistry)
   - software: CASSIS, CDMS
   - parameter: Main upper limit assumes Trot 51 K and line width 0.7 km/s  
  > "The upper limit for the column density of CH$_3$OH toward the main source was calculated assuming a T$_{rot}$ of 51 K (to match the temperature of H$_2$CO toward Main) and a line width of 0.7 km s$^{-1}$." (3.5 CH3OH emission)
   - fitting: _not stated_
   - validation: _not stated_
7. **Compare with other FHSC candidates and VeLLOs**: Literature comparison of maximum velocity, dynamical time and mechanical luminosity  
  > "Cha-MMS1 has a similar maximum velocity range, generally lower dynamical time, and higher mechanical luminosity (by at least 2 orders of magnitude)." (4.2 Status of Cha-MMS1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4.0: Data reduction  
  > "Data reduction was performed with the CASA package (version 5.4.0)." (Observations and data reduction)
- **tclean** : Imaging with Hogbom deconvolver, Briggs weighting  
  > "Imaging was done using the tclean process with a Hogbom deconvolver" (Observations and data reduction)
- **CASSIS** : Rotational diagrams of H2CO and CH3OH  
  > "determined using the H$_2$CO transitions in a rotational diagram in the CASSIS software" (3.4 H2CO emission)
- **CDMS** : Line parameters (E_up, A_ij) of the targeted transitions  
  > "Targeted spectral lines (E$_{\mathrm{up}}$ and A$_{\mathrm{ij}}$ from CDMS)" (Table 1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Broad red 12CO component centre velocity | 10.9 | 0.2 | km/s | 2 | the center is at 10.9$\pm$0.2 km s$^{-1}$ and the full-width half-maximum (FWHM) is 6.7$\pm$0.4 km s$^{-1}$. |
| Broad red 12CO component FWHM | 6.7 | 0.4 | km/s | 2 | the center is at 10.9$\pm$0.2 km s$^{-1}$ and the full-width half-maximum (FWHM) is 6.7$\pm$0.4 km s$^{-1}$. |
| Broad red outflow collimation factor | 5.5 | not stated | dimensionless | 0 | It is quite collimated with a collimation factor of 5.5. |
| Southern blue 12CO component central velocity | 3.40 | 0.01 | km/s | 2 | A Gaussian fit of the southern blue component has a central velocity of 3.40$\pm$0.01 km s$^{-1}$ and a FWHM of 0.77$\pm$0.03 km s$^{-1}$. |
| Southern blue 12CO component FWHM | 0.77 | 0.03 | km/s | 2 | A Gaussian fit of the southern blue component has a central velocity of 3.40$\pm$0.01 km s$^{-1}$ and a FWHM of 0.77$\pm$0.03 km s$^{-1}$. |
| V_max, northern red lobe | 12.4 | 0.1 | km/s | 3 | 12.4 (0.1) |
| V_max, southern red lobe | 4.0 | 0.1 | km/s | 3 | 4.0 (0.1) |
| V_max, northern blue lobe | 3.2 | 0.1 | km/s | 3 | 3.2 (0.1) |
| V_max, southern blue lobe | 2.9 | 0.1 | km/s | 3 | 2.9 (0.1) |
| Kinetic time, northern red lobe | 130 | 10 | yr | 3 | 130 (10) |
| Kinetic time, southern red lobe | 490 | 20 | yr | 3 | 490 (20) |
| Kinetic time, northern blue lobe | 720 | 20 | yr | 3 | 720 (20) |
| Kinetic time, southern blue lobe | 800 | 30 | yr | 3 | 800 (30) |
| Outflow mass, northern red lobe | 5.2e-5 | 1.0e-5 | Msun | 3 | 5.2 (1.0)$\times10^{-5}$ |
| Outflow mass, southern red lobe | 7.4e-5 | 1.7e-5 | Msun | 3 | 7.4 (1.7)$\times10^{-5}$ |
| Outflow mass, northern blue lobe | 4.7e-5 | 0.6e-5 | Msun | 3 | 4.7 (0.6)$\times10^{-5}$ |
| Outflow mass, southern blue lobe | 2.1e-4 | 0.1e-4 | Msun | 3 | 2.1 (0.1)$\times10^{-4}$ |
| Momentum rate, northern red lobe | 2.9e-5 | 0.7e-5 | Msun km/s / yr | 3 | 2.9 (0.7)$\times10^{-5}$ |
| Momentum rate, southern red lobe | 3.6e-6 | 1.4e-6 | Msun km/s / yr | 3 | 3.6 (1.4)$\times10^{-6}$ |
| Momentum rate, northern blue lobe | 1.4e-6 | 0.1e-6 | Msun km/s / yr | 3 | 1.4 (0.1)$\times10^{-6}$ |
| Momentum rate, southern blue lobe | 1.1e-5 | 0.1e-5 | Msun km/s / yr | 3 | 1.1 (0.1)$\times10^{-5}$ |
| Mechanical luminosity, northern red lobe | 1.1e-1 | 2.7e-1 | Lsun | 3 | 1.1 (2.7)$\times10^{-1}$ |
| Mechanical luminosity, southern red lobe | 5.7e-3 | 3.1e-3 | Lsun | 3 | 5.7 (3.1)$\times10^{-3}$ |
| Mechanical luminosity, northern blue lobe | 2.3e-3 | 0.8e-3 | Lsun | 3 | 2.3 (0.8)$\times10^{-3}$ |
| Mechanical luminosity, southern blue lobe | 2.4e-2 | 0.2e-2 | Lsun | 3 | 2.4 (0.2)$\times10^{-2}$ |
| H2CO rotational temperature, Main | 40.4 | +2.7/-2.4 | K | 5 | 40.4 (+2.7, -2.4) |
| H2CO rotational temperature, N | 73 | +101/-27 | K | 5 | 73 (+101, -27) |
| H2CO rotational temperature, S | 10.8 | +0.3/-0.2 | K | 5 | 10.8 (+0.3, -0.2) |
| H2CO rotational temperature, W | 36.5 | +7.0/-5.1 | K | 5 | 36.5 (+7.0, -5.1) |
| H2CO rotational temperature toward continuum source (text value) | 51.0 | 36.2 | K | 5 | with a temperature of 51.0 ($\pm$36.2) K toward the continuum source. |
| H2CO column density, Main | 3.8e13 | 0.4e13 | cm^-2 | 5 | 3.8 (0.4) $\times 10^{13}$ |
| H2CO column density, N | 2.8e13 | +0.08e13/-0.01e13 | cm^-2 | 5 | 2.8 (+0.08, -0.01) $\times 10^{13}$ |
| H2CO column density, S | 1.4e13 | 0.1e13 | cm^-2 | 5 | 1.4 (0.1) $\times 10^{13}$ |
| H2CO column density, W | 3.9e13 | +1.2e13/-0.9e13 | cm^-2 | 5 | 3.9 (+1.2, -0.9) $\times 10^{13}$ |
| CH3OH rotational temperature, N | 41.2 | 30.8 | K | 6 | 41.2 (30.8) |
| CH3OH rotational temperature, S | 23.2 | 2.3 | K | 6 | 23.2 (2.3) |
| CH3OH rotational temperature, W | 15.7 | 1.9 | K | 6 | 15.7 (1.9) |
| CH3OH column density, N | 8.6e13 | 6.4e13 | cm^-2 | 6 | 8.6 (6.4) $\times 10^{13}$ |
| CH3OH column density, S | 4.8e13 | 0.8e13 | cm^-2 | 6 | 4.8 (0.8) $\times 10^{13}$ |
| CH3OH column density, W | 1.1e14 | 0.4e14 | cm^-2 | 6 | 1.1 (0.4) $\times 10^{14}$ |
| CH3OH column density upper limit, Main | <1.2e13 | not stated | cm^-2 | 6 | $<$1.2 $\times 10^{13}$ |

## Qualitative findings

- 12CO emission is resolved out on large scales; a weak broad feature at 8.7-17.1 km/s lies northeast of the continuum source  
  > "a weak spectral feature covering the broad velocity range of 8.7-17.1 km s$^{-1}$ is detected in $^{12}$CO to the northeast of the continuum source" (3.1 Continuum and Line Detection)
- CS emission shows an hourglass-like morphology within 1.5 arcsec of the continuum source and traces a wide cone on larger scales  
  > "Within 1.5$''$ (288 AU) of the continuum source spectral emission of CS shows shows an hourglass-like morphology." (3.1 Continuum and Line Detection); "Figure [6](#CScontours) shows CS emission tracing a wide cone on larger scales" (3.3 CS)
- CH3OH is detected toward clumps associated with H2CO emission but not toward the continuum source, consistent with ice sputtering in outflow shocks  
  > "CH$_3$OH emission is detected towards the clumps associated with H$_2$CO emission to the northeast, south, and southwest of the continuum source, but not toward the continuum source itself." (3.5 CH3OH emission); "the observed methanol is likely being produced by ice sputtering in shock waves." (3.5 CH3OH emission)
- Kinetic time is hundreds of years, making time-dependent quantities an order of magnitude higher than Busch2020  
  > "We find the kinetic time to be on the order of hundreds of years, rather than thousands, which results in our time-dependent values being an order of magnitude higher." (4.2.1 Mechanical properties)

## Claim tuples

- H: Cha-MMS1 is a First Hydrostatic Core | E: Mapped CO, CS, H2CO and CH3OH, derived outflow mechanical properties and compared with other FHSC candidates and VeLLOs | R: Molecular emission, high outflow speeds and higher mechanical luminosity than other FHSC candidates | F: Cha-MMS1 is not a viable FHSC; it is one of the youngest known Class 0 objects | **supported**
- H: Cha-MMS1 drives a detectable outflow | E: 12CO and 13CO moment maps and Gaussian fits of line profiles | R: A weak outflow with a broad northeast red component and narrow bipolar components | F: A low-energy outflow nearly perpendicular to the line of sight is seen through its interaction with the surrounding cloud | **supported**
- H: The outflow affects the chemistry and temperature of the surrounding gas | E: Rotational diagrams of H2CO and CH3OH toward four regions | R: H2CO Trot ~40-51 K toward the continuum source and 10-75 K in clumps; CH3OH only toward off-source clumps | F: Methanol is released by outflow shocks through ice sputtering; low gas temperatures indicate a very young source | **supported**
- H: What drives the outflow structure (single precessing outflow versus binary) | E: Morphology and kinematics of CO, 13CO, CS and H2CO | R: S-shaped red emission, distant blue emission and a broad red component without a blue counterpart | F: A single precessing outflow is favoured, but two outflows from a close binary are not excluded | **partially**
- H: Outflow mechanical properties are consistent with those expected for the source luminosity | E: Compared derived mass, momentum rate and mechanical luminosity with Wu2004 trends | R: Outflow mass 100-1000 times lower, momentum rate and mechanical luminosity comparable | F: The outflow is weak and low-energy | **partially**

## Reasoning

- Why this data: Targeted molecular species expected in very young low-mass star-forming regions  
  > "Our observations targeted several molecular species expected in very young low-mass star-forming regions" (3.1 Continuum and Line Detection)
- Why this method: Pointing at the millimeter position rather than the Spitzer IR peak  
  > "The pointing position of our ALMA observations was the millimeter position reported in (cite: Reipurth1996) rather than the Spitzer IR peak" (Observations and data reduction)
- Alternative: Alternative scenarios for the S-shaped emission: a dense clump diverting the outflow versus a precessing outflow; and for precession, magnetic misalignment or turbulent infall instead of a binary  
  > "The alternative scenario is that this S-shaped emission and slower, more distant blue-shifted emission indicates a precessing outflow." (4.1 Physical origin of outflow emission); "Alternative scenarios can also produce outflow precession" (4.1 Physical origin of outflow emission)
- Alternative: Thermal desorption from warm dust rejected as the origin of H2CO and CH3OH given the low temperatures  
  > "it is unlikely that the detected H$_2$CO originates in thermal desorption from warm dust." (3.4 H2CO emission)
- How they decided it was enough: _not stated_
- Limitation (authors): The blue components lie at the field-of-view edge so the outflow ends cannot be confirmed  
  > "These blue components appear to be the ends of the outflow, but as we do not have a larger field-of-view, we cannot confirm." (3.2.2 Narrow bipolar outflow)
- Limitation (authors): H2CO fit toward N is poor because of the low flux of the 218.475 GHz line  
  > "the fit for N was poor due to the low flux of the transition at 219475 MHz" (Table 2)
- Limitation (authors): 12CO emission resolved out on large scales  
  > "$^{12}$CO emission is resolved out on large scales" (3.1 Continuum and Line Detection)
- Caveat (inferred, ours): The H2CO rotational temperature toward Main is 40 K in the abstract and Table 2 but 51.0 K in the text and in the CH3OH upper-limit assumption
- Caveat (inferred, ours): Three different systemic velocities appear (4.5, 4.9 and 6.94 km/s), so velocity offsets and V_max are not unambiguous
- Caveat (inferred, ours): Rotation temperatures rest on three lines with large errors (e.g. 73 +101/-27 K) and one poorly constrained fit; LTE and equal gas and dust temperature are assumed
- Caveat (inferred, ours): Outflow mass and energy rely on assumed Tex, CO abundance, tau = 5 and an 80 deg inclination, and the 12CO is partly resolved out and self-absorbed
- Caveat (inferred, ours): Mechanical luminosity of the northern red lobe has an uncertainty larger than its value, and the table shows 1.6 (1.9)e41 erg for the northern blue lobe
- Caveat (inferred, ours): No flux scale uncertainty, self-calibration or cube parameters are given

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration scripts and calibrator roles
- Missing: Cell size, image size, masks, clean threshold, channel width
- Missing: Line-free channels and continuum subtraction method
- Missing: Lobe regions, velocity limits and region definitions for spectra
- Missing: CASSIS fit settings and error treatment
- Missing: Which systemic velocity was adopted for each lobe
- Data volume (inferred): Three execution blocks with seven spectral windows over two cycles; likely tens of GB of raw data (inferred, not stated)
- Score (inferred): 3/5, Project code, CASA version, tclean deconvolver and robust are given and results are tabulated, but array configuration, cube parameters, masks, regions and CASSIS fit settings are missing and the text has internal inconsistencies in temperature and velocity values.
- Rediscovery candidate: no, The paper does not state that the data are public and region, mask and fit settings needed to redo the outflow and rotational-diagram numbers are not given.

## Links

- Method: (cite: AlvaroOutflows) Sanchez-Monge et al. 2013, A&A, 557, A94 (Approach used to calculate outflow mechanical properties)
- Method: (cite: AnaOutflows) Lopez-Sepulcre et al. 2009, A&A, 499, 811 (Approach used to calculate outflow mechanical properties)
- Method: (cite: Goldsmith1999) Goldsmith & Langer 1999, ApJ, 517, 209 (Optically thin CO column density equations (10) and (19))
- Method: (cite: Ana2010) Lopez-Sepulcre et al. 2010, A&A, 517, A66 (Inclination correction factors)
- Companion: (cite: Busch2020) Busch et al. 2020, A&A, 633, A126 (CO(3-2) analysis of Cha-MMS1 outflow; results compared with this work)
- Companion: (cite: MariaJose2020) Maureira et al. 2020, MNRAS (Dense-envelope tracer analysis of FHSC candidates including Cha-MMS1)

## Checks

```json
{
 "quotes": 136,
 "quotes_ok": 136,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 41,
 "numeric_problems": 0,
 "fill": {
  "facts": 94,
  "stated": 61,
  "rate": 0.649
 },
 "evidence_ok": true
}
```
