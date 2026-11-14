# ALMA Observations of the DART Impact: Characterizing the Ejecta at Submillimeter Wavelengths

`2023PSJ.....4..206R` | The Planetary Science Journal 2023 | first author: Roth, Nathan X. | arXiv: 2306.05908 | DOI: 10.3847/PSJ/acfcaa

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: Measure Didymos-Dimorphos' millimeter spectral emissivity pre-impact, then isolate the DART impact ejecta post-impact to derive dust mass and gas-phase upper limits  
  > "We conducted pre-impact observations in order to characterize Didymos-Dimorphos’ spectral emissivity at millimeter wavelengths for the first time, and post-impact observations to measure the gas and dust produced in the ejecta plume." (Introduction)
- Target **Didymos-Dimorphos binary asteroid system**: coordinates _not stated_; z/distance geocentric distance 0.075 au at impact (heliocentric 1.045 au post-impact)  
  > "We tracked the asteroids’ position using JPL Horizons ephemerides (#187)." (Pre-Impact 12m Observations); "The small geocentric distance of the Didymos-Dimorphos system ($\Delta_{min}$ = 0.075 au) at impact" (Introduction); distance from not stated beyond JPL Horizons ephemeris tracking  
  > "We tracked the asteroids’ position using JPL Horizons ephemerides (#187)." (Pre-Impact 12m Observations); "The small geocentric distance of the Didymos-Dimorphos system ($\Delta_{min}$ = 0.075 au) at impact" (Introduction)

## Data provenance

- ALMA projects: 2021.A.00013.S
- bands: Band 7 (343.5 GHz pre-impact; 344.25-347.45 GHz post-impact)  
  > "using the Band 7 receiver in Time Division Mode (TDM) for pre-impact continuum observations centered at 343.5 GHz" (Pre-Impact 12m Observations); "covering frequencies from 344.25 GHz to 347.45 GHz" (Post Impact 12m and ACA Observations)
- frequencies and spectral setup: Pre: TDM, 31.25 MHz channels, 27 km/s resolution. Post: FDM, six non-contiguous spws (117-2000 MHz wide), 3 GHz total; 15.625 MHz continuum channels, 61-122 kHz line channels (0.05-0.11 km/s)  
  > "in six non-contiguous spectral windows ranging from 117 MHz to 2000 MHz wide and a total bandwidth of 3 GHz in two polarizations" (Post Impact 12m and ACA Observations); "The channel spacing was 15.625 MHz for continuum windows and 61 kHz – 122 kHz for spectral line windows" (Post Impact 12m and ACA Observations)
- continuum bandwidth: 8 GHz pre-impact (two polarizations); 3 GHz post-impact  
  > "with a total bandwidth of 8 GHz in two polarizations" (Pre-Impact 12m Observations); "a total bandwidth of 3 GHz in two polarizations" (Post Impact 12m and ACA Observations)
- arrays: ALMA 12 m array pre-impact; simultaneous 12 m array and ACA post-impact  
  > "four consecutive (46 minutes each), simultaneous executions of the ALMA 12 m array and the Atacama Compact Array (ACA)" (Post Impact 12m and ACA Observations)
- configurations: C3 (post-impact 12 m array)  
  > "with the 12 m array at 345 GHz in configuration C3" (Analysis of the Ejecta)
- baselines: 12 m pre-impact 15-782 m; 12 m post-impact 15-500 m; ACA 9-49 m  
  > "15–782" (Table 1); "15–500" (Table 1); "9–49" (Table 1)
- angular resolution: Pre-impact 0.38''-0.56''; post-impact 12 m 0.48''-1.11''; ACA 2.79''-6.95''  
  > "was 0.38$''$ – 0.56$''$" (Pre-Impact 12m Observations); "The spatial scale was 0.48$''$ – 1.11$''$ for the 12 m array" (Post Impact 12m and ACA Observations); "$2.79\ensuremath{''}$ – $6.95\ensuremath{''}$ for the ACA" (Post Impact 12m and ACA Observations)
- max recoverable scale: Pre-impact 3.3'' (236 km); post-impact 12 m 4.7'' (254 km; text gives 4.68''); ACA 19.3'' (1050 km)  
  > "$\theta$~MRS~ = $3.3\ensuremath{''}$ (236 km)" (Table 1); "$\theta$~MRS~ = $19.3\ensuremath{''}$ (1050 km)" (Table 1); "the MRS is 4.68$\ensuremath{''}$, corresponding to 254 km" (Analysis of the Ejecta)
- sensitivity: _not stated_
- time on source: Pre-impact 12 m: 5 min; post-impact 12 m: 4 x 46 min; ACA: 4 x 45.7 min (Table 1 T_int)  
  > "is the total on-source integration time." (Table 1 notes); "four consecutive (46 minutes each), simultaneous executions" (Post Impact 12m and ACA Observations); "in a short pre-impact execution of the 12 m array" (12 m Array Pre-Impact Observations)
- observing dates: Pre-impact UT 2022 September 15; post-impact UT 2022 September 27 (impact UT 23:14 2022 September 26)  
  > "On UT 2022 September 15 we targeted Didymos-Dimorphos with one execution of the ALMA 12 m array" (Pre-Impact 12m Observations); "On UT 2022 September 27 we targeted Didymos-Dimorphos in four consecutive (46 minutes each)" (Post Impact 12m and ACA Observations)
- pi or archival as stated: Director's Discretionary Time  
  > "using the Atacama Large Millimeter/Submillimeter Array (ALMA) with Director’s Discretionary Time" (Introduction)
- Line: SiO J=8-7 (347.331 GHz)
- Line: SiS J=19-18 (344.779 GHz)
- Line: SO J_K=8_8-7_7 (344.310 GHz)
- Line: AlO J_F=9_12-8_11 (344.476 GHz)
- Line: KCl J=45-44 (344.820 GHz)
- Line: NaCN J_Ka,Kc=22_3,20-21_3,19 (344.269 GHz)
- Other facility **Hubble Space Telescope**: Ejecta particle size distribution used for dust mass modeling  
  > "Based on the ejecta particle size distribution measured by the Hubble Space Telescope (cite: Li2023)" (Introduction)
- Other facility **JWST**: Beaming parameter used in the NEATM thermal model  
  > "a beaming parameter of 1.93 based on JWST observations of Didymos-Dimorphos taken at a similar solar phase angle to the ALMA observations (cite: Rivkin2023)" (Modeling and Interpretation)
- Other facility **DART spacecraft (DRACO)**: Asteroid sizes (volume equivalent sphere diameters)  
  > "calculated volume equivalent sphere diameters of 761 m and 151 m for Didymos and Dimorphos, respectively, based on imaging by the DRACO instrument on DART" (Observing Geometry)
- External data: Volume equivalent sphere diameters: Didymos 761 m, Dimorphos 151 m  
  > "calculated volume equivalent sphere diameters of 761 m and 151 m for Didymos and Dimorphos, respectively" (Observing Geometry) [from (cite: Daly2023)]
- External data: Dimorphos total mass 4.3e9 kg  
  > "Dimorphos’ total mass of $4.3\times10^9$ kg (cite: Daly2023)" (Analysis of the Ejecta) [from (cite: Daly2023)]
- External data: Piece-wise ejecta particle size distribution a^-2.7 (0.5 um to 2 mm), a^-3.7 (to 2.5 cm)  
  > "piece-wise differential particle size distribution of $a^{-2.7}$ for particles of radius 0.5 $\mu$m to 2 mm and of $a^{-3.7}$ for larger particles up to a radius of 2.5 cm as derived by (cite: Li2023)" (Calculation of the Dust Ejecta Masses) [from (cite: Li2023)]
- External data: Optical constants of low-Fe crystalline olivine  
  > "Optical constants from (cite: Fabian2001)" (Table 2 notes) [from (cite: Fabian2001)]
- External data: Optical constants of amorphous olivine and amorphous pyroxene  
  > "Optical constants from (cite: Jager2003)" (Table 2 notes) [from (cite: Jager2003)]
- External data: Bond albedo 0.067 (geometric albedo 0.16, phase integral 0.42)  
  > "We assumed a Bond albedo of 0.067 based on Didymos-Dimorphos’ geometric albedo of 0.16 and a phase integral of 0.42 derived from the HG phase function using the DART Design Reference Asteroid parameters (cite: Rivkin2021; Bowell1989)" (Modeling and Interpretation) [from (cite: Rivkin2021; Bowell1989)]
- External data: Beaming parameter 1.93  
  > "a beaming parameter of 1.93 based on JWST observations of Didymos-Dimorphos taken at a similar solar phase angle to the ALMA observations (cite: Rivkin2023)" (Modeling and Interpretation) [from (cite: Rivkin2023)]
- External data: Average porosity of ordinary chondrites 8.2%  
  > "We assumed an 8.2% average porosity of ordinary chondrites (cite: Tsuchiyama2011)" (Calculation of the Dust Ejecta Masses) [from (cite: Tsuchiyama2011)]
- External data: Grain density 3500 kg m^-3  
  > "We assumed $\rho = 3500$ kg m$^{-3}$ as measured in ordinary chondrites and the Itokawa returned samples (cite: Tsuchiyama2011)" (Calculation of the Dust Ejecta Masses) [from (cite: Tsuchiyama2011)]
- External data: Secondary eclipse brightness decrease of 0.049 mag  
  > "developed a photometric model for predicting mutual events for Didymos-Dimorphos, with secondary eclipses resulting in a 0.049 mag decrease in brightness" (Didymos-Dimorphos' Spectral Emissivity) [from (cite: Scheirich2022)]
- External data: Gas rotational temperature 1000 K from pre-impact ejecta modeling  
  > "We assumed a gas rotational temperature $T_{rot}$ = 1000 K based on pre-impact modeling of temperatures achieved in the ejecta (cite: Raducan2022b)" (Upper Limits on Gas-Phase Ejecta) [from (cite: Raducan2022b)]
- External data: Line frequencies, statistical weights, upper state energies, Einstein-A coefficients (LAMDA for SiO, SiS, SO; CDMS for the rest)  
  > "Frequencies, statistical weights, upper state energies, and Einstein-A coefficients retrieved from the LAMDA database (cite: Schoier2005) for SiO, SiS, and SO and from the CDMS database (cite: Endres2016) for all other species." (Table 4 notes) [from (cite: Schoier2005; Endres2016)]
- External data: Rotational partition functions at 1000 K  
  > "reported in CDMS for SiO, SiS, AlO, and KCl (cite: Endres2016), in HITRAN for SO (cite: Gamache2021), and in (cite: Carlson1997) for NaCN" (Upper Limits on Gas-Phase Ejecta) [from (cite: Endres2016; Gamache2021; Carlson1997)]

## Processing

### Calibration

- pipeline or manual: Standard routines in CASA for flagging and calibration; automated ALMA pipeline flux scale checked and corrected for one execution  
  > "The data were flagged and calibrated using standard routines in Common Astronomy Software Applications (CASA) package version 6.5.2 (cite: CASA2022)." (Pre-Impact 12m Observations); "The automated ALMA pipeline calibration scheme extrapolated along the upward trend to assign a flux scale of 1.22 Jy to J0238+1636" (Post Impact 12m and ACA Observations)
- casa version: CASA 6.5.2  
  > "Self-calibration was performed using CASA 6.5.2 and an automated self-calibration procedure" (Self Calibration)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Pre-impact J2258-2758; post-impact 12 m: J0006-0623 (Exec 1,2), J0238+1636 (Exec 3), J0519-4546 (Exec 4); ACA: J2253+1608 (Exec 1,2), J2258-2758 (Exec 3), J0423-0120 (Exec 4)  
  > "J2258-2758 was used to calibrate the flux scale" (Pre-Impact 12m Observations); "J0006-0623 for 12 m Executions 1 and 2, J0238+1636 for 12 m Execution 3, J0519-4546 for 12 m Execution 4" (Post Impact 12m and ACA Observations); "J2253+1608 for ACA Executions 1 and 2, J2258-2758 for ACA Execution 3, and J0423-0120 for ACA Execution 4" (Post Impact 12m and ACA Observations)
- flux scale uncertainty: 10% absolute flux uncertainty adopted; J0238+1636 set to 1.11 Jy (not pipeline 1.22 Jy) for 12 m Execution 3  
  > "We instead applied the value of 1.11 Jy (measured for J0238+1636 on 2022 September 23) to our 12 m Execution 3 observations" (Post Impact 12m and ACA Observations); "we conservatively adopted the 10% uncertainty in absolute flux recommended by the ALMA observatory for our measurements" (Post Impact 12m and ACA Observations)
- self calibration: Automated phase-only self-cal (inf_EB, then per-scan 'inf', shorter intervals where possible) then amplitude (inf_ap) where phase succeeded; combine='scan,spw' fallback for all data; applycal applymode='calonly'  
  > "The first solution interval performed was a single solution over an entire execution block for each polarization independently, using gaincal parameters gaintype=‘G’ and combine=‘scan’, and solint=‘inf’" (Self Calibration); "gaincal was executed with the parameters combine=‘spw’, gaintype=‘T’, solmode=‘ap’, solint=‘inf’, and solnorm=True" (Self Calibration); "applymode=‘calonly’" (Self Calibration)

### Imaging

- task: tclean (auto-masking heuristics built into tclean named in the self-calibration appendix)  
  > "The automated self-calibration procedure utilizes best practices (cite: Brogan2018) and the auto-masking heuristics built into tclean (cite: Kepley2020)." (Self Calibration)
- deconvolver: MTMFS for continuum; Högbom for spectral-line cubes  
  > "we generated the final images using the multi-term multi-frequency synthesis (MTMFS) algorithm with Briggs visibility weighting" (Pre-Impact 12m Observations); "imaged before any self-calibration was applied using the Högbom algorithm with natural weighting and auto-masking" (Post Impact 12m and ACA Observations)
- weighting robust: Briggs, robust = 0.5 (continuum); natural weighting (spectral-line cubes)  
  > "Briggs visibility weighting (with a robust value of 0.5) was chosen to balance angular resolution and sensitivity to continuum emission." (Post Impact 12m and ACA Observations); "Natural weighting was chosen to maximize sensitivity to potential faint, extended spectral line emission." (Post Impact 12m and ACA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Auto-masking with the standard pipeline threshold parameters for compact 12 m array or ACA (continuum and line)  
  > "auto-masking using the standard pipeline threshold parameters specified for continuum measurements with a compact 12 m array (cite: Kepley2020)" (Pre-Impact 12m Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Applied after imaging  
  > "auto-masking using the standard pipeline threshold parameters specified for spectral line measurements with a compact 12 m array or the ACA (cite: Kepley2020), followed by primary beam correction." (Post Impact 12m and ACA Observations)
- array combination: 12 m and ACA imaged separately (no combination stated)  
  > "Figures [2](#fig:post-impact1) and [3](#fig:post-impact2) show our post-impact continuum maps for the 12 m array and the ACA." (12 m Array and ACA Post-Impact Continuum Observations)
- smoothing: _not stated_
- final beam: Table 1 synthesized beams: pre-impact 0.56x0.38''; post-impact 12 m 1.11x0.48'' to 0.63x0.50''; ACA 2.95x6.95'' to 2.71x4.39''  
  > "is the angular resolution (synthesized beam) at $\nu$ given in arcseconds" (Table 1 notes)
- final rms: Post-self-cal image RMS (mJy/beam): pre-impact 12 m 0.061; post-impact 12 m 0.067, 0.049, 0.048, 0.040; ACA 0.706, 0.447, 0.379, 0.424  
  > "Image RMS after self-calibration was applied." (Self Calibration Summary Table)

### Inherited from earlier work

- Auto-masking and threshold parameters for imaging follow the ALMA imaging pipeline standard  
  > "auto-masking using the standard pipeline threshold parameters specified for continuum measurements with a compact 12 m array (cite: Kepley2020)" (Pre-Impact 12m Observations) [from (cite: Kepley2020)]
- Post-impact tracking and calibration (including continuum self-calibration) follow the pre-impact procedure  
  > "Tracking and calibration were performed as in our pre-impact epoch, including the application of self-calibration to continuum measurements." (Post Impact 12m and ACA Observations) [from pre-impact epoch, this paper]
- Self-calibration follows best practices and tclean auto-masking heuristics  
  > "The automated self-calibration procedure utilizes best practices (cite: Brogan2018) and the auto-masking heuristics built into tclean (cite: Kepley2020)." (Self Calibration) [from (cite: Brogan2018); (cite: Kepley2020)]
- Dust mass calculation method  
  > "Dust masses were calculated for each execution following the methods of (cite: Jewitt1990) and (cite: Boissier2012)." (Calculation of the Dust Ejecta Masses) [from (cite: Jewitt1990); (cite: Boissier2012)]
- Thermal emission model (NEATM)  
  > "The Near Earth Asteroid Thermal model (cite: Harris1998; Delbo2002) was used to analyze thermal emission from the asteroids." (Didymos-Dimorphos' Spectral Emissivity) [from (cite: Harris1998; Delbo2002)]
- Column density relation to integrated intensity  
  > "can be related to the integrated intensity as (cite: Bockelee1994):" (Upper Limits on Gas-Phase Ejecta) [from (cite: Bockelee1994)]

### Not stated but needed to reproduce (our reading)

- Image cell size and image size for continuum and line imaging
- tclean niter, thresholds and any mask edits beyond the 'standard pipeline' auto-mask parameters
- Which spectral windows/channels were used for the continuum and whether any continuum subtraction was applied to line cubes
- Line-cube channel width and velocity grid used for the 3 sigma upper limits, and how the noise was measured
- Exact auto_selfcal version/commit and the per-execution solution intervals beyond Table of best solutions
- Pipeline (CASA pipeline) version and the flux scales assigned to each calibrator in each execution
- Aperture center and how the flux in 50 km / 200 km apertures was summed (e.g., beam-area conversion, background handling)
- How the weighted average and its uncertainty were computed
- Infrared emissivity epsilon value used in the NEATM Tss equation and how Didymos and Dimorphos contributions were split
- Mie calculation settings (size grid, wavelength) and Maxwell-Garnett implementation details
- Method for the 10% systematic term combination with image RMS in quadrature or linear sum

## Analysis recipe

1. **Calibrate and self-calibrate the visibilities**: Standard CASA calibration; automated phase (and where possible amplitude) self-calibration; flux scale of J0238+1636 corrected for 12 m Execution 3  
  > "The data were flagged and calibrated using standard routines in Common Astronomy Software Applications (CASA) package version 6.5.2 (cite: CASA2022)." (Pre-Impact 12m Observations)
   - software: CASA 6.5.2, auto_selfcal, gaincal, applycal
   - parameter: gaincal combine='scan,spw' fallback used for all observations  
  > "it fell back and used combine=‘scan,spw’, which was the case for all the observations presented here" (Self Calibration)
   - assumption: 10% absolute flux uncertainty  
  > "we conservatively adopted the 10% uncertainty in absolute flux recommended by the ALMA observatory for our measurements" (Post Impact 12m and ACA Observations)
   - fitting: _not stated_
   - validation: Success of each self-cal solution interval judged by increased image S/N  
  > "This first solution interval was successful for all data presented here as evaluated by an increased S/N in the resulting images following self-calibration." (Self Calibration)
2. **Image continuum and spectral-line data**: MTMFS continuum imaging with Briggs weighting; Högbom natural-weighted line cubes; auto-masking; primary beam correction; channel-averaged continuum MS to 250 MHz channels for post-impact  
  > "We then averaged the spectral line channels to a channel width of 250 MHz to create a channel-averaged continuum Measurement Set for both the 12 m and the ACA data" (Post Impact 12m and ACA Observations)
   - software: CASA, tclean
   - parameter: Briggs robust = 0.5 for continuum  
  > "Briggs visibility weighting (with a robust value of 0.5)" (Pre-Impact 12m Observations)
   - fitting: _not stated_
   - validation: Peak continuum position agrees with predicted ephemeris position within one synthesized beam  
  > "This peak continuum position was in agreement with the predicted ephemeris position of the asteroids to within one synthesized ALMA beam." (Pre-Impact 12m Observations)
3. **Fit the pre-impact point-source flux density**: uvmodelfit point-source model fit to visibilities, compared with image flux  
  > "Using the CASA `uvmodelfit` routine with a point-source model returns a best-fit flux density of 1.79 $\pm$ 0.18 mJy and a reduced $\chi^2$ of 1.31" (12 m Array Pre-Impact Observations)
   - software: CASA uvmodelfit
   - assumption: Asteroids unresolved (point source)  
  > "The image is consistent with an unresolved point source" (12 m Array Pre-Impact Observations)
   - fitting: Point-source model; reduced chi2 = 1.31; sampler and priors not stated  
  > "Using the CASA `uvmodelfit` routine with a point-source model returns a best-fit flux density of 1.79 $\pm$ 0.18 mJy and a reduced $\chi^2$ of 1.31" (12 m Array Pre-Impact Observations)
   - validation: Fit flux consistent with image flux density 1.73 +/- 0.18 mJy  
  > "consistent with the flux density in the image (1.73 $\pm$ 0.18 mJy) and indicative of a good fit to the visibilities as a point-source." (12 m Array Pre-Impact Observations)
4. **Derive millimeter spectral emissivity with NEATM**: NEATM with subsolar temperature and surface temperature distribution; integrated flux equation solved for emissivity using fit flux and Daly2023 diameters  
  > "The Near Earth Asteroid Thermal model (cite: Harris1998; Delbo2002) was used to analyze thermal emission from the asteroids." (Didymos-Dimorphos' Spectral Emissivity)
   - software: NEATM (model)
   - parameter: Bond albedo 0.067; beaming parameter 1.93; Tss = 324 K pre-impact  
  > "The resulting $T_{ss}$ is 324 K." (Didymos-Dimorphos' Spectral Emissivity)
   - assumption: Didymos and Dimorphos have the same spectral emissivity; no emission from the night side  
  > "As the asteroids were not spatially resolved during our pre-impact observations, we assumed that they have the same spectral emissivity." (Didymos-Dimorphos' Spectral Emissivity); "The temperature was calculated across the asteroid surface assuming that no emission originates from the night side as" (Didymos-Dimorphos' Spectral Emissivity)
   - fitting: _not stated_
   - validation: Compared with emissivities of other asteroids measured at mm wavelengths (C, S, M, E classes)  
  > "Our observed average emissivity of 0.95 ± 0.10 for Didymos-Dimorphos is consistent with its S-class classification" (Didymos-Dimorphos' Spectral Emissivity)
5. **Predict asteroid flux on the impact date**: Repeat NEATM at impact-date geometry; reduce flux for secondary eclipse  
  > "We predict a flux of 2.74 mJy attributable to the asteroids themselves when neither are in eclipse" (Didymos-Dimorphos' Spectral Emissivity)
   - software: NEATM (model)
   - parameter: rH = 1.045 au, Delta = 0.075 au, Tss = 330 K; eclipse reduction 0.049 mag gives 2.60 mJy  
  > "where we find $T_{ss}$ = 330 K" (Didymos-Dimorphos' Spectral Emissivity)
   - assumption: Emissivity from pre-impact measurement applies post-impact  
  > "Once their spectral emissivity is known, the flux attributable to Didymos-Dimorphos on the impact date can be calculated" (Modeling and Interpretation)
   - fitting: _not stated_
   - validation: _not stated_
6. **Measure post-impact continuum flux in apertures**: Integrate flux inside 50 km radius (12 m) and 200 km radius (ACA) apertures; examine visibility amplitudes versus baseline  
  > "We integrated the flux inside an aperture of 50 km radius for the 12 m images and of 200 km radius for the ACA images" (12 m Array and ACA Post-Impact Continuum Observations)
   - software: CASA
   - parameter: Apertures capture all emission at >=3 sigma  
  > "corresponding to radii which capture all emission at the $\geq3\sigma$ level" (12 m Array and ACA Post-Impact Continuum Observations)
   - fitting: _not stated_
   - validation: Measured flux densities in formal agreement among executions and arrays  
  > "The measured fluxes are in formal agreement between arrays and between executions." (Analysis of the Ejecta)
7. **Subtract asteroid flux to isolate ejecta flux**: Subtract predicted asteroid flux (2.74 mJy, or 2.60 mJy in eclipse) from each execution's flux  
  > "We calculated the ejecta flux density for each execution by subtracting our predicted flux density for Didymos-Dimorphos, using the appropriate value depending on whether the asteroids were in eclipse." (Analysis of the Ejecta)
   - parameter: Extra 10% uncertainty added  
  > "We incorporated an additional 10% uncertainty into our ejecta flux densities to account for systematic uncertainties in our prediction of Didymos-Dimorphos’ post-impact flux." (Analysis of the Ejecta)
   - fitting: _not stated_
   - validation: _not stated_
8. **Compute grain absorption efficiency and dust opacity**: Mie theory for spherical homogeneous grains with miepython; porous grains via two-component Maxwell-Garnett (hollow sphere); opacity integrated over size distribution  
  > "using Mie theory for spherical, homogeneous grains with the `miepython` package" (Calculation of the Dust Ejecta Masses); "The final refractive index for the porous grains was calculated using the two-component Maxwell-Garnett formula assuming vacuum as the core and the minerals as inclusions in the matrix" (Calculation of the Dust Ejecta Masses)
   - software: miepython
   - parameter: amin 0.5 um, amax 2.5 cm; a^-2.7 to 2 mm, a^-3.7 above; rho 3500 kg m^-3; porosity 8.2%  
  > "assuming minimum and maximum particles of radius 0.5 $\mu$m and 2.5 cm, respectively" (Table 2 notes)
   - assumption: Grain temperature independent of size and equal to blackbody equilibrium temperature of 266 K at 1.045 au; size distribution and chemistry uniform in the field of view  
  > "The grain temperature is assumed to be independent of size and equal to the blackbody equilibrium temperature for fast-rotating bodies of 266 K at *r*~H~ = 1.045 au." (Calculation of the Dust Ejecta Masses); "Assuming the dust size distribution and chemical properties do not vary within the field of view" (Calculation of the Dust Ejecta Masses)
   - fitting: _not stated_
   - validation: Alternative with amax = 0.5 m gives masses roughly twice as high  
  > "our resulting ejecta masses are higher by roughly a factor of two" (Calculation of the Dust Ejecta Masses)
9. **Convert ejecta flux to dust mass**: Rayleigh-Jeans relation S = 2kTM kappa/(lambda^2 Delta^2) solved for M for each execution and material; weighted average over executions  
  > "We used these derived ejecta flux densities to calculate the ejecta mass responsible for the flux density measured in each execution." (Analysis of the Ejecta); "Given the overall good agreement between the fluxes, we calculated the weighted average flux of all executions to compare with results for individual executions." (Calculation of the Dust Ejecta Masses)
   - parameter: Three compositions: crystalline olivine (Cry-Oli), amorphous olivine (Amo-Oli), amorphous pyroxene (Amo-Pyr)  
  > "we used optical constants to calculate refractive indexes for three separate materials when calculating $Q$~abs~" (Calculation of the Dust Ejecta Masses)
   - assumption: Weighted average treated as a lower limit on ejecta dust mass; crystalline favored  
  > "We consider this weighted average to be representative of the dust mass lower limit for the ejecta." (Calculation of the Dust Ejecta Masses)
   - fitting: _not stated_
   - validation: Compared with 0.3-0.5% lower limits from optical measurements and pre-impact simulations  
  > "Our calculated ejecta masses are consistent with lower limits of 0.3–0.5% of Dimorphos’ mass estimated by (cite: Graykowski2023) based on optical wavelength measurements of the ejecta." (Calculation of the Dust Ejecta Masses)
10. **Derive spectral-line upper limits and gas-phase masses**: 3 sigma integrated intensity limits in a 4.68'' diameter aperture; convert to upper-level and total column densities and vapor masses with Trot = 1000 K  
  > "within a 4.68$''$ diameter aperture centered on the asteroids" (12 m Array Post-Impact Spectral Line Observations); "we derived upper limits on column densities and masses of gas-phase ejecta along the line-of-sight during our observations" (Upper Limits on Gas-Phase Ejecta)
   - software: CASA, CDMS, LAMDA, HITRAN
   - parameter: Assumed line width 2 km/s  
  > "We assumed a line width of 2 km s$^{-1}$, consistent with the expansion velocity" (12 m Array Post-Impact Spectral Line Observations)
   - assumption: Gas rotational temperature 1000 K; gas extended perpendicular to line of sight filtered out so limits constrain line-of-sight emission  
  > "We assumed a gas rotational temperature $T_{rot}$ = 1000 K based on pre-impact modeling of temperatures achieved in the ejecta (cite: Raducan2022b)" (Upper Limits on Gas-Phase Ejecta)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.5.2: Flagging, calibration, self-calibration, imaging, uvmodelfit  
  > "The data were flagged and calibrated using standard routines in Common Astronomy Software Applications (CASA) package version 6.5.2 (cite: CASA2022)." (Pre-Impact 12m Observations)
- **tclean** : Imaging with auto-masking heuristics  
  > "the auto-masking heuristics built into tclean (cite: Kepley2020)" (Self Calibration)
- **auto_selfcal** : Automated self-calibration procedure  
  > "Self-calibration was performed using CASA 6.5.2 and an automated self-calibration procedure" (Self Calibration)
- **uvmodelfit** : Point-source fit to pre-impact visibilities  
  > "Using the CASA `uvmodelfit` routine with a point-source model returns a best-fit flux density" (12 m Array Pre-Impact Observations)
- **miepython** 2.3.0: Mie theory absorption efficiency Qabs  
  > "using Mie theory for spherical, homogeneous grains with the `miepython` package" (Calculation of the Dust Ejecta Masses)
- **JPL Horizons** : Ephemerides used to track the asteroids  
  > "We tracked the asteroids’ position using JPL Horizons ephemerides (#187)." (Pre-Impact 12m Observations)
- **ALMA Calibrator Source Catalog** : Check of pipeline flux scale assigned to quasars  
  > "We examined the ALMA Calibrator Source Catalog for each quasar to assess the absolute flux calibration scale assigned by the pipeline." (Post Impact 12m and ACA Observations)
- **LAMDA / CDMS / HITRAN** : Line parameters and partition functions  
  > "retrieved from the LAMDA database (cite: Schoier2005) for SiO, SiS, and SO and from the CDMS database (cite: Endres2016) for all other species." (Table 4 notes)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Pre-impact point-source flux density (uvmodelfit, 343.5 GHz) | 1.79 | 0.18 | mJy | 3 | returns a best-fit flux density of 1.79 $\pm$ 0.18 mJy and a reduced $\chi^2$ of 1.31 |
| Reduced chi-squared of point-source fit | 1.31 | not stated | dimensionless | 3 | returns a best-fit flux density of 1.79 $\pm$ 0.18 mJy and a reduced $\chi^2$ of 1.31 |
| Pre-impact image flux density | 1.73 | 0.18 | mJy | 3 | consistent with the flux density in the image (1.73 $\pm$ 0.18 mJy) |
| Spectral emissivity of Didymos-Dimorphos at 343.5 GHz | 0.95 | 0.10 | dimensionless | 4 | Our observed average emissivity of 0.95 ± 0.10 for Didymos-Dimorphos is consistent with its S-class classification |
| Subsolar temperature pre-impact | 324 | not stated | K | 4 | The resulting $T_{ss}$ is 324 K. |
| Subsolar temperature on impact date | 330 | not stated | K | 5 | where we find $T_{ss}$ = 330 K |
| Predicted asteroid flux, no eclipse | 2.74 | not stated | mJy | 5 | We predict a flux of 2.74 mJy attributable to the asteroids themselves when neither are in eclipse |
| Predicted asteroid flux, secondary eclipse | 2.60 | not stated | mJy | 5 | We reduced our predicted Didymos-Dimorphos flux a corresponding amount to 2.60 mJy |
| Weighted-average total flux (asteroids plus ejecta) | 4.72 | 0.19 | mJy | 6 | 4.72 $\pm$ 0.19 |
| Weighted-average ejecta flux | 2.03 | 0.22 | mJy | 7 | 2.03 $\pm$ 0.22 |
| Dust opacity at 0.87 mm, crystalline olivine | 4.15e-3 | not stated | m^2 kg^-1 | 8 | $4.15\times10^{-3}$ |
| Dust opacity at 0.87 mm, amorphous olivine | 2.05e-2 | not stated | m^2 kg^-1 | 8 | $2.05\times10^{-2}$ |
| Dust opacity at 0.87 mm, amorphous pyroxene | 1.88e-2 | not stated | m^2 kg^-1 | 8 | $1.88\times10^{-2}$ |
| Average ejecta mass, crystalline olivine | 6.39e7 | 0.64e7 | kg | 9 | 6.39 $\pm$ 0.64 |
| Average ejecta mass, amorphous olivine | 1.29e7 | 0.13e7 | kg | 9 | 1.29 $\pm$ 0.13 |
| Average ejecta mass, amorphous pyroxene | 1.41e7 | 0.14e7 | kg | 9 | 1.41 $\pm$ 0.14 |
| Ejecta mass range as fraction of Dimorphos mass | 0.3-1.5 | not stated | percent | 9 | These ejecta masses represent 0.3–1.5% of Dimorphos’ total mass |
| Fraction of flux from particles of radius 100 um to 10 mm | ~75 | not stated | percent | 9 | particles with radii between 100 $\mu$m and 10 mm contribute $\sim$75% of our measured flux density at $\lambda$ = 0.87 mm |
| 3 sigma integrated intensity upper limits (SiO, SiS, SO, AlO, KCl, NaCN) | <2.1e-2, <1.5e-2, <1.3e-2, <1.7e-2, <1.3e-2, <1.8e-2 | not stated | K km s^-1 | 10 | $<2.1\times10^{-2}$ K km s$^{-1}$, $<1.5\times10^{-2}$ K km s$^{-1}$, $<1.3\times10^{-2}$ K km s$^{-1}$, $<1.7\times10^{-2}$ K km s$^{-1}$, $<1.3\times10^{-2}$ K km s$^{-1}$, and $<1.8\times10^{-2}$ K km s$^{-1}$, respectively |
| Total column density upper limits (SiO, SiS, SO, AlO, KCl, NaCN) | <1.6e11, <3.3e11, <1.1e12, <6.2e11, <3.2e10, <7.9e11 | not stated | molecule cm^-2 | 10 | $<$ $1.6\times10^{11}$; $<$ $3.2\times10^{10}$ |
| Line-of-sight vapor mass upper limits (SiO, SiS, SO, AlO, KCl, NaCN) | <11.9, <24.5, <66.7, <37.1, <2.9, <47.3 | not stated | kg | 10 | $<$11.9 kg, $<$24.5 kg, $<$66.7 kg, $<$37.1 kg, $<$2.9 kg, and $<$47.3 kg for SiO, SiS, SO, AlO, KCl, and NaCN, respectively |

## Qualitative findings

- Post-impact visibility amplitudes indicate an extended source; images show extended ejecta but no clear jets  
  > "no clear structure (*e.g.,* jets) was found in the images." (12 m Array and ACA Post-Impact Continuum Observations)
- Measurements are lower limits on total sub-mm flux because emission beyond the MRS is filtered out  
  > "Thus, our measurements are lower limits on the total flux at sub-millimeter wavelengths" (Analysis of the Ejecta)
- Slight flux decrease during the secondary-eclipse executions  
  > "The slight decrease in flux during 12 m Execution 4 and ACA Execution 3" (Analysis of the Ejecta)

## Claim tuples

- H: Is Didymos-Dimorphos' millimeter emissivity consistent with other measured asteroids? | E: Pre-impact Band 7 12 m observation fit with a NEATM thermal model | R: Emissivity 0.95 +/- 0.10 at 343.5 GHz | F: Consistent with S-class silicate surface with minimal metal | **supported**
- H: How much mm-sized dust mass was in the ejecta T+3.5 to T+8.6 hr? | E: Subtracted scaled pre-impact asteroid flux from post-impact flux and converted to mass with Mie opacities | R: Average ejecta mass 1.3-6.4e7 kg (0.3-1.5% of Dimorphos mass) | F: Consistent with optical lower limits and pre-impact simulations | **supported**
- H: Is gas-phase ejecta (Si, S, Al, K, Na species) detectable? | E: Searched 12 m and ACA cubes for SiO, SiS, SO, AlO, KCl, NaCN | R: No lines detected; 3 sigma upper limits derived | F: Upper limits on line-of-sight vapor masses of ~3-67 kg | **supported**
- H: Is the ejecta continuum compact or extended? | E: Visibility amplitude versus baseline for post-impact data | R: Amplitudes vary significantly with baseline | F: Ejecta emission is extended (full modeling deferred) | **supported**
- H: Which grain composition best represents the ejecta? | E: Mass computed for crystalline olivine, amorphous olivine and amorphous pyroxene | R: Crystalline olivine gives the highest masses (~6.4e7 kg) | F: The higher crystalline-based mass is favored | **partially**

## Reasoning

- Why this data: Band 7 FDM setup chosen for both line and continuum sensitivity; 0.87 mm most sensitive to total ejecta mass  
  > "This correlator setup was chosen to be sensitive to spectral line emission from potential gas-phase ejecta as well as to thermal continuum emission." (Post Impact 12m and ACA Observations); "making our ALMA measurements at $\lambda$ = 0.87 mm the most sensitive observations to the total ejecta mass" (Introduction)
- Why this method: Briggs robust 0.5 balances resolution and sensitivity; natural weighting for faint extended line emission  
  > "Briggs visibility weighting (with a robust value of 0.5) was chosen to balance angular resolution and sensitivity to continuum emission." (Post Impact 12m and ACA Observations); "Natural weighting was chosen to maximize sensitivity to potential faint, extended spectral line emission." (Post Impact 12m and ACA Observations)
- Alternative: Pipeline-assigned flux scale of 1.22 Jy for J0238+1636 rejected in favour of 1.11 Jy  
  > "The automated ALMA pipeline calibration scheme extrapolated along the upward trend to assign a flux scale of 1.22 Jy to J0238+1636 during our 12 m Execution 3, resulting in artificially inflated flux for our Didymos-Dimorphos measurements." (Post Impact 12m and ACA Observations)
- Alternative: Extending the size distribution to meter-sized material (amax = 0.5 m) raises ejecta masses by about a factor of two; not adopted in the main result  
  > "our resulting ejecta masses are higher by roughly a factor of two" (Calculation of the Dust Ejecta Masses)
- How they decided it was enough: _not stated_
- Limitation (authors): Size distribution for meter-sized material unknown; major caveat  
  > "our assumptions regarding the particle size distribution for meter-sized material are a significant caveat" (Calculation of the Dust Ejecta Masses)
- Limitation (authors): Effective medium theories only approximate real optical properties  
  > "We note that EMT theories only provide approximations to the real optical properties of a substance" (Calculation of the Dust Ejecta Masses)
- Limitation (authors): No optical constants available for crystalline pyroxenes at 0.87 mm  
  > "as far as we are aware, there are no available optical constants for crystalline pyroxenes at $\lambda = 0.87$ mm." (Calculation of the Dust Ejecta Masses)
- Limitation (authors): Visibility modeling deferred to future work  
  > "A full modeling treatment of the visibilities is beyond the scope of this manuscript and is the subject of future work." (12 m Array and ACA Post-Impact Continuum Observations)
- Caveat (inferred, ours): Ejecta mass depends strongly on the assumed composition (factor ~5 between crystalline and amorphous), and the favored crystalline choice rests on indirect argument
- Caveat (inferred, ours): Asteroid flux subtraction relies on one 5-minute pre-impact point and an emissivity assumed equal for both bodies and constant to the impact date
- Caveat (inferred, ours): Aperture photometry is applied to an extended source with unmodelled visibility structure; MRS filtering makes masses lower limits
- Caveat (inferred, ours): Differing flux calibrators across executions, including one corrected by hand, may leave a systematic flux scale offset beyond the adopted 10%
- Caveat (inferred, ours): Gas limits assume Trot = 1000 K and a 2 km/s line width, so limits are model-dependent

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging cell size, image size, niter and thresholds
- Missing: Continuum spectral-window selection and line-free channel handling
- Missing: Auto_selfcal version and parameters
- Missing: Exact aperture centers and flux summation procedure
- Missing: Epsilon (infrared emissivity) value and size split used in NEATM
- Missing: Mie and Maxwell-Garnett implementation settings
- Missing: No public statement of data availability or product location in the paper text
- Data volume (inferred): Roughly 20-100 GB for nine short Band 7 executions (1 pre-impact 12 m, 4 post-impact 12 m, 4 ACA); estimate
- Score (inferred): 4/5, Project code, CASA version, calibrators, weighting and nearly all model parameters, equations and numeric results are given; imaging grid, masks, auto_selfcal settings and flux-summation details are missing.
- Rediscovery candidate: yes, Single ALMA project with stated executions, explicit thermal and dust-mass recipe and numeric results (emissivity, masses, upper limits); archive data presumably public but paper does not state it.

## Links

- Method: (cite: Kepley2020) (ALMA imaging pipeline heuristics used for auto-masking thresholds)
- Method: (cite: Brogan2018) (Self-calibration best practices)
- Method: (cite: Jewitt1990) (Dust flux and mass formalism)
- Method: (cite: Boissier2012) (Dust mass from sub-mm flux density)
- Method: (cite: Harris1998; Delbo2002) (NEATM thermal model)
- Method: (cite: Bockelee1994) (Column density from integrated intensity)
- Companion: (cite: Li2023) (HST ejecta imaging and particle size distribution)
- Companion: (cite: Daly2023) (DART results: sizes and mass of Didymos and Dimorphos)
- Companion: (cite: Rivkin2023) (JWST beaming parameter)
- Companion: (cite: Graykowski2023) (Ejecta velocity and optical mass lower limits)
- Companion: (cite: Shestakova2023) (Alkali vapor plume expansion velocity)
- Companion: (cite: Scheirich2022) (Mutual event photometric model)
- Related: DART mission
- Related: ALMA Director's Discretionary Time project 2021.A.00013.S

## Checks

```json
{
 "quotes": 172,
 "quotes_ok": 172,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 21,
 "numeric_problems": 0,
 "fill": {
  "facts": 128,
  "stated": 102,
  "rate": 0.797
 },
 "evidence_ok": true
}
```
