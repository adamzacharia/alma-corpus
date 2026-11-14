# An ALMA Search for Substructure and Fragmentation in Starless Cores in Orion B North

`2024ApJ...968...10F` | The Astrophysical Journal 2024 | first author: Fielder, Samuel D. | arXiv: 2404.13520 | DOI: 10.3847/1538-4357/ad3d56

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Do starless cores in Orion B North show compact substructure at the rate predicted by turbulent fragmentation, and does core boundedness explain differences between Chamaeleon I, Ophiuchus and Orion B North?  
  > "Utilizing comparable datasets for all three regions, we analyze the boundedness of the dense core populations, and use these results to interpret the number of detections of high density peaks within Orion B North in the broader context." (1 Introduction); "We detect a total of 34 continuum sources at 106 GHz, and after comparisons with other data, 4 of these sources appear to be starless." (abstract)
- Target **73 SCUBA starless/protostellar dense cores in Orion B North (NGC 2068/2071)**: coordinates per-field R.A./Decl. (J2000) listed in Table 1 (05:46 to 05:47, -00:13 to +00:26)  
  > "and positional information is given in Table" (2.1 Target Selection: SCUBA); "with the Orion B North portion of the complex situated at a distance of approximately 419 pc" (1 Introduction); z/distance 419 pc  
  > "and positional information is given in Table" (2.1 Target Selection: SCUBA); "with the Orion B North portion of the complex situated at a distance of approximately 419 pc" (1 Introduction); distance from Zucker et al. 2019 (cite: Zucker2019)  
  > "and positional information is given in Table" (2.1 Target Selection: SCUBA); "with the Orion B North portion of the complex situated at a distance of approximately 419 pc" (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.00094.S
- bands: Band 3 (106 GHz central), Cycle 3  
  > "The ALMA Band 3 data were observed between 2016 March 08 and 2016 August 27, and consisted of 7 unique observation times, using an average of 38 antennas." (2.2 ALMA Data)
- frequencies and spectral setup: 4 spws: three continuum at 101, 103, 113 GHz (1875 MHz each) plus a 12CO(1-0) spw at 115 GHz  
  > "Four spectral windows were used, with three configured for continuum measurements, centered at 101 GHz, 103 GHz, and 113 GHz, each with a bandwidth of 1875 MHz." (2.2 ALMA Data)
- continuum bandwidth: approximately 6 GHz at 106 GHz  
  > "The total continuum bandwidth is therefore approximately 6 GHz at a central frequency of 106 GHz." (2.2 ALMA Data)
- arrays: _not stated_
- configurations: C-2/3 for first five execution blocks; C-4/5 for final two  
  > "The array was in a relatively compact configuration for the first five observation windows (C-2/3)" (2.2 ALMA Data); "In the final two observations, the array was in a slightly more expanded configuration (C-4/5)" (2.2 ALMA Data)
- baselines: 15 m to 460 m (C-2/3); 15 m to 1125 m (C-4/5)  
  > "with antenna separations ranging from approximately 15 m to 460 m." (2.2 ALMA Data); "with antenna separations ranging from approximately 15 m to 1125 m." (2.2 ALMA Data)
- angular resolution: average synthesized beam 1.5 x 1.3 arcsec (~630 x 550 au), PA 75 deg  
  > "This yields an average synthesized beam of 1.5$''$ $\times$ 1.3$''$ ($\sim$ 630 au $\times$ 550 au) at a position angle of 75 degrees" (2.2 ALMA Data)
- max recoverable scale: approximately 14 arcsec  
  > "along with a maximum recoverable scale of approximately 14$''$." (2.2 ALMA Data)
- sensitivity: requested and achieved 1-sigma rms 0.07 mJy/beam (per-field 0.042-0.076 in Table 1); CO cube 1.1 K in 0.5 km/s channel  
  > "This brought all fields to the rms noise level requested for the observations, 0.07 mJy beam$^{-1}$." (2.2 ALMA Data); "the data achieves a sensitivity of 1.1 K in a 0.5 km s$^{-1}$ channel" (2.2 ALMA Data)
- time on source: 270 s (50 fields) or 230 s (23 fields) per field  
  > "Most sources (50) were observed during all 7 execution blocks, totalling 270 seconds of on source time, with the remaining (23) sources missing the last execution block, totalling 230 seconds of on-source time." (2.2 ALMA Data)
- observing dates: 2016 March 08 to 2016 August 27 (7 execution blocks)  
  > "The ALMA Band 3 data were observed between 2016 March 08 and 2016 August 27, and consisted of 7 unique observation times" (2.2 ALMA Data)
- pi or archival as stated: observations obtained by the authors' team for the proposal (proposal mentioned; PI not named)  
  > "We obtained ALMA Cycle 3 observations observations of all 73 starless cores identified by" (2.1 Target Selection: SCUBA); "While not available at the time of the ALMA proposal" (8 Comparison of SCUBA and SCUBA-2 data)
- Line: 12CO J=1-0 (115 GHz (as stated))
- Other facility **JCMT SCUBA (850 um)**: source catalog of 73 starless cores used for target selection, core masses and sizes  
  > "Both the Ophiuchus and Orion B North datasets were observed with the SCUBA instrument on the JCMT at a wavelength of 850" (6.1.1 Dust Continuum-based Properties)
- Other facility **JCMT SCUBA-2 (Gould Belt Survey)**: more sensitive 850 um map and independent core catalog used to bound the number of starless cores (47 to 61)  
  > "the Orion molecular cloud was observed by the JCMT Gould Belt Survey with the SCUBA-2 instrument" (8 Comparison of SCUBA and SCUBA-2 data)
- Other facility **Spitzer (Megeath et al. YSO catalog)**: nearest-YSO association to classify ALMA detections as protostellar (<2 arcsec)  
  > "We first search for the nearest Spitzer YSO in the" (3.1.1 Associations with Spitzer YSOs)
- Other facility **VANDAM (ALMA Band 7 / VLA 9 mm)**: ALMA catalog used to verify protostellar associations  
  > "The VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey of Orion Protostars." (3.1.2 Associations with ALMA-based Catalogs)
- Other facility **ALMASOP**: Band 6 comparison for 9 overlapping detections  
  > "through the ALMA Survey of Orion Planck Galactic Cold Clumps (ALMASOP)" (3.1.2 Associations with ALMA-based Catalogs)
- Other facility **Green Bank Ammonia Survey (GBT)**: NH3 line widths and kinetic temperatures for Ophiuchus and Orion B North cores used in virial analysis  
  > "The Green Bank Ammonia Survey" (6.1.2 Dense Gas Kinematics)
- Other facility **CfA all-sky CO survey (Dame & Thaddeus 2022)**: 12CO line widths for large-scale turbulent pressure  
  > "We choose to utilize the newer Northern Sky Survey of" (6.1.3 Larger Scale Turbulent Material)
- External data: SCUBA dense core catalog of Orion (positions, peak/integrated fluxes, masses, sizes)  
  > "identified a total of 393 dense cores in the Orion molecular cloud complex." (2.1 Target Selection: SCUBA) [from Nutter & Ward-Thompson 2007 (cite: Nutter2007)]
- External data: Masses and sizes of Chamaeleon I (Belloche 2011) and Ophiuchus (Jorgensen 2008) cores adopted directly  
  > "We directly adopt the masses and sizes as reported in these aforementioned papers for our analysis." (6.1.1 Dust Continuum-based Properties) [from Belloche2011; Jorgensen2008; Nutter2007]
- External data: Dust opacity OH5 model at 106 GHz  
  > "specifically the OH5 model corresponding to thin ice mantles after" (4.1 Mass Estimates) [from Ossenkopf & Henning 1994 (cite: Ossenkopf1994)]
- External data: Class I protostellar lifetime of 0.74 Myr  
  > "We adopt a reference Class I protostellar lifetime of 0.74 Myr from" (5.3 Evolutionary Lifetime Estimate) [from Konyves et al. 2015 (cite: Konyves2015)]
- External data: Chamaeleon I N2H+ line widths for pointed observations of Cha I cores (19 cores)  
  > "we adopt the N$_{2}$H$^{+}(1-0)$ data as being the most comparable to the NH$_3$ data available for the other two clouds." (6.1.2 Dense Gas Kinematics) [from Tsitali et al. 2015 (cite: Tsitali2015)]
- External data: All-sky dust extinction maps (N=25 star maps) for cloud weight  
  > "we utilize the all-sky dust extinction maps of" (6.1.4 Cloud Weight) [from Rowles & Froebrich 2009 (cite: Rowles2009)]
- External data: SESNA Class I source counts (37 Class I cores in footprint)  
  > "By comparing the 37 Class I cores found within the survey footprint from the SESNA catalog" (5.3 Evolutionary Lifetime Estimate) [from R. Gutermuth et al. 2024, in preparation]
- Simulation/model as data: ORION AMR MHD simulation of an isolated collapsing 0.4 Msun starless core (same snapshots as Dunham+2016 and Kirk+2017), converted to synthetic ALMA observations; also a 4 Msun core in appendix  
  > "with an initial core mass of $0.4M_{\odot}$, using the ORION Adaptive Mesh Refinement (AMR) code base" (5.1 Numerical Simulations and Synthetic Observations); "To generate synthetic ALMA observations, we use the same turbulent simulation snapshots as in" (5.1 Numerical Simulations and Synthetic Observations)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "The calibration and reduction was conducted in the pipeline version 4.7.0 of the Common Astronomy Software Applications (CASA) software." (2.2 ALMA Data)
- casa version: CASA 6.5.0 for imaging and analysis  
  > "For imaging and analysis, CASA version 6.5.0 was utilized for its refined automasking routines" (2.2 ALMA Data)
- pipeline version: 4.7.0 (CASA pipeline)  
  > "The calibration and reduction was conducted in the pipeline version 4.7.0 of the Common Astronomy Software Applications (CASA) software." (2.2 ALMA Data)
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: performed where peak emission above ~10 mJy/beam  
  > "Self-calibration routines were performed on the continuum where it improved image quality, which in our case was where the peak emission was above approximately 10 mJy beam$^{-1}$." (2.2 ALMA Data)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust R = 0.5 (continuum); briggsbwtaper with R = 0.5 (line cube)  
  > "Briggs weighting with a robust value of $R = 0.5$" (2.2 ALMA Data); "with the same robust value of $R=0.5$" (2.2 ALMA Data)
- uv taper: 0.8 arcsec  
  > "a uvtaper of 0.8$''$ to reduce sidelobe contamination" (2.2 ALMA Data)
- cell size: 0.17 arcsec  
  > "the same imaging cell size of 0.17$''$ used to image the real observations" (5.1 Numerical Simulations and Synthetic Observations)
- image size: _not stated_
- masking: default automasking parameters  
  > "and default automasking parameters." (2.2 ALMA Data)
- multiscale scales: _not stated_
- continuum subtraction: line emission subtracted from the CO spectral window to recover its continuum; continuum subtracted for the line cube  
  > "the line emission was first subtracted from the last spectral window in order to make use of all available continuum emission present" (2.2 ALMA Data); "For line emission imaging, the continuum was first subtracted" (2.2 ALMA Data)
- line free channels: _not stated_
- primary beam correction: applied to all final images  
  > "All final images produced were corrected for primary beam attenuation." (2.2 ALMA Data)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: average 1.5 x 1.3 arcsec at PA 75 deg  
  > "This yields an average synthesized beam of 1.5$''$ $\times$ 1.3$''$ ($\sim$ 630 au $\times$ 550 au) at a position angle of 75 degrees" (2.2 ALMA Data)
- final rms: 0.07 mJy/beam requested and reached for all fields; per-field 1-sigma 0.042-0.076 mJy/beam in Table 1  
  > "This brought all fields to the rms noise level requested for the observations, 0.07 mJy beam$^{-1}$." (2.2 ALMA Data)

### Inherited from earlier work

- Synthetic-observation approach and expected-detection calculation follow the Chamaeleon I and Ophiuchus ALMA studies  
  > "In this section, we perform the same approach as" (5.1 Numerical Simulations and Synthetic Observations) [from Dunham et al. 2016 (cite: Dunham2016); Kirk et al. 2017 (cite: Kirk2017)]
- Same turbulent simulation snapshots as earlier ALMA population studies  
  > "To generate synthetic ALMA observations, we use the same turbulent simulation snapshots as in" (5.1 Numerical Simulations and Synthetic Observations) [from Dunham2016; Kirk2017]
- Simulation details deferred to earlier paper  
  > "For more in-depth details on the descriptions of the simulations, we refer to the reader to Section 5.1.1 in" (5.1 Numerical Simulations and Synthetic Observations) [from Section 5.1.1 of Dunham et al. 2016 (cite: Dunham2016)]
- Expected number of detections formula assumes continuous star formation, as in earlier studies  
  > "With the assumption of a continuous rate of star formation over the timescale at least as long as the core lifetimes, then similar to" (5.2 Detecting Starless Cores) [from Dunham2016; Kirk2017]
- Virial parameter computed with the standard method  
  > "following the standard method outlined in" (6.3 Jeans Analysis) [from Bertoldi & McKee 1992 (cite: Bertoldi1992)]
- Full virial energy terms follow Pattle et al. method  
  > "Following the method outlined in" (6.4 Virial Analysis) [from Pattle et al. 2015 (cite: Pattle2015)]
- Constant factor of -3/5 for gravitational term  
  > "and choose a constant factor of" (6.4 Virial Analysis) [from Kerr et al. 2019 (cite: Kerr2019)]
- Central concentration definition  
  > "We measure the central concentration of dense cores from the catalog, with the following definition:" (4.3 SCUBA Core Concentration) [from Johnstone et al. 2000 (cite: Johnstone2000)]

### Not stated but needed to reproduce (our reading)

- Which channels were treated as line-free for continuum subtraction and the CO spectral window continuum estimate
- tclean settings for the real data: deconvolver, niter, threshold, gain, nsigma, and the actual automask parameter values
- Self-calibration details: solution intervals, number of rounds, refsources, and which fields were self-calibrated
- Flux, bandpass and phase calibrator names and the absolute flux scale uncertainty
- Mosaic construction details (which pointings were combined, weighting, pbmod) beyond the mosaic names in Table 1
- Formal ALMA source-detection criterion and threshold used to define the 34 detections (only individual significances such as 8 and 7.4 times local rms are given)
- How the integrated flux used in the mass equation relates to Table 2 Tot values for unresolved sources and how the effective radius was derived exactly
- simalma setup details: antenna configuration files used, thermal-noise parameters, and the primary beam and pointing used for the synthetic observations
- Simulation snapshots and their time steps are not provided in this paper; the 5 sigma detection criterion applied to the synthetic images is not fully described
- Origin of the central density 1.86e7 cm^-3 used for the free-fall time of the one genuinely starless detection
- SESNA catalog (R. Gutermuth et al. 2024) is unpublished, so the Class I count of 37 cannot be reproduced
- Procedure for fitting single-component Gaussians to the CO spectra and the pixel selection for GAS values

## Analysis recipe

1. **Calibrate and image continuum and CO data**: Pipeline calibration, then CASA imaging with Briggs weighting, uv taper, automasking, self-calibration where bright, mosaicking of overlapping fields, primary beam correction; separate 12CO cube imaging with briggsbwtaper  
  > "The calibration and reduction was conducted in the pipeline version 4.7.0 of the Common Astronomy Software Applications (CASA) software." (2.2 ALMA Data); "In the case where the field of view of individual ALMA observations overlapped, mosaicking was conducted (prior to self-calibration where appropriate) to improve the final sensitivity of the image." (2.2 ALMA Data)
   - software: CASA 4.7.0 pipeline, CASA 6.5.0
   - parameter: Briggs robust R = 0.5; uvtaper 0.8 arcsec; cell 0.17 arcsec  
  > "Briggs weighting with a robust value of $R = 0.5$" (2.2 ALMA Data); "a uvtaper of 0.8$''$ to reduce sidelobe contamination" (2.2 ALMA Data)
   - fitting: _not stated_
   - validation: Self-calibration applied only where it improved image quality; rms measured in non-detection areas of the non-primary-beam-corrected image  
  > "Self-calibration routines were performed on the continuum where it improved image quality" (2.2 ALMA Data); "computed in non-detection areas of the (mosaicked, if applicable) field." (Table 1)
2. **Extract continuum sources by Gaussian fitting**: Fit elliptical Gaussians to every continuum source with imfit, giving peak, integrated flux, FWHM axes, PA and deconvolved sizes (Table 2)  
  > "to fit elliptical Gaussians to all continuum sources found" (2.2 ALMA Data); "We detect a total of 34 continuum sources across 19 individual ALMA pointings." (3 Detections)
   - software: CASA imfit
   - fitting: Elliptical 2D Gaussian; unresolved sources flagged with -1 for deconvolved sizes  
  > "Unresolved sources are indicated by values of -1." (Table 2)
   - validation: _not stated_
3. **Classify detections as protostellar or starless**: Cross-match with Spitzer YSO (coincident if <2 arcsec), VANDAM, ALMASOP, VISTA, SESNA, WISE and HGBS catalogs; inspect 12CO cube for outflows toward the unassociated detections; reclassify SCUBA cores using protostars within 14 arcsec  
  > "In this study, we classify separations of less than 2$''$ to the nearest Spitzer YSO to be coincident detections." (3.1.1 Associations with Spitzer YSOs); "We classify any protostellar object lying within 14$''$ of the peak of the core as associated, based on the beamsize of the SCUBA catalog." (3.3 Associations Summary)
   - parameter: 27 Spitzer coincidences; 25 of 27 within VANDAM coverage matched to VANDAM protostars (<0.50 arcsec)  
  > "In total, we find that 27 of our ALMA detections are found in the Spitzer catalog" (3.1.1 Associations with Spitzer YSOs); "Of the 27 detections lying within VANDAM coverage, 25 have direct correspondences with VANDAM protostars" (3.1.2 Associations with ALMA-based Catalogs)
   - assumption: VANDAM is expected to detect only protostellar sources  
  > "hence VANDAM is expected to only detect protostellar sources." (3.1.2 Associations with ALMA-based Catalogs)
   - fitting: _not stated_
   - validation: Multiple independent catalogs plus CO outflow search; no new candidates found in the additional catalogs  
  > "No new protostellar candidates were identified based on these catalogues" (3.1.3 Other Published Catalogs)
4. **Derive masses, radii and number densities**: Optically thin dust mass from integrated flux with a Planck function at 10 K and a gas-to-dust ratio of 100; effective radius from geometric mean of deconvolved axes (synthesized beam as upper limit for unresolved); mean number density from mass and radius  
  > "The effective radius is computed from a geometric mean of the semi-major and semi-minor axes of the deconvolved size, and if the source is unresolved, the synthesized beam is used in place" (4 Derived Properties); "and the factor of 100 represents the gas-to-dust ratio." (4.1 Mass Estimates)
   - parameter: d = 419 pc  
  > "We adopt a slightly updated value of distance, $d=419~\text{pc}$, consistent with newer estimates from" (4.1 Mass Estimates)
   - parameter: kappa = 0.23 cm^2/g at 106 GHz (OH5)  
  > "Extending the model to an effective frequency of 106 GHz yields our choice in opacity of $\kappa_{\nu} = 0.23~\text{cm}^2~\text{g}^{-1}$." (4.1 Mass Estimates)
   - parameter: mu = 2.80 for number density  
  > "where $\mu = 2.80$ is the mean molecular weight per hydrogen molecule" (4.1 Mass Estimates)
   - assumption: Dust temperature 10 K  
  > "along with a core temperature of $T=10~\text{K}$." (4.1 Mass Estimates)
   - assumption: Gas-to-dust ratio 100  
  > "and the factor of 100 represents the gas-to-dust ratio." (4.1 Mass Estimates)
   - fitting: _not stated_
   - validation: Uncertainties are acknowledged as systematic: opacity uncertain by factors of 2-4; halving kappa doubles mass  
  > "Since the mass is inversely proportional to" (4.1 Mass Estimates)
5. **Measure SCUBA core central concentration**: Central concentration C from beam size, integrated flux, effective radius and peak flux of the SCUBA cores; compared with Bonnor-Ebert limits 0.33 and 0.72  
  > "We measure the central concentration of dense cores from the catalog, with the following definition:" (4.3 SCUBA Core Concentration); "Our starless core candidates lie in SCUBA dense cores with concentration values of 0.55 (source 1), 0.84 (source 4), and 0.69 (sources 23 and 24)." (4.3 SCUBA Core Concentration)
   - fitting: _not stated_
   - validation: Compared with SCUBA-2 cores of Kirk et al. 2016, which all have C above 0.33  
  > "In all cases, the associated SCUBA-2 dense cores do have concentrations above the minimum 0.33" (4.3 SCUBA Core Concentration)
6. **Generate synthetic ALMA observations of a collapsing turbulent core**: Convert simulated column density to flux maps with the mass equation, observe with simalma for the real antenna configurations, on-source times and distance, and re-image with tclean using the real imaging parameters  
  > "The synthetic observations were generated using CASA" (5.1 Numerical Simulations and Synthetic Observations); "to mimic all imaging parameters used in the physical observations" (5.1 Numerical Simulations and Synthetic Observations)
   - software: CASA simalma, CASA tclean, ORION AMR
   - parameter: 270 s on source (190 s compact, 80 s extended); 2 s integrations; 106 GHz; 6 GHz bandwidth; default atmospheric noise model; phase center 05:47:00 +00:05:00  
  > "We use a total on source time of 270 s, with 190 s at the more compact configuration, and 80 s at the more extended configuration, to match our real observations." (5.1 Numerical Simulations and Synthetic Observations); "include the default atmospheric noise model" (5.1 Numerical Simulations and Synthetic Observations)
   - assumption: Starting core of 0.4 Msun, 10 K, initial density 1.6e5 cm^-3 with uniform B field in z, decaying turbulence  
  > "with an initial number density of $1.6 \times10^5~\text{cm}^{-3}$" (5.1 Numerical Simulations and Synthetic Observations)
   - fitting: _not stated_
   - validation: Also run for a 4 Msun core; detectability threshold differs by less than a factor of two  
  > "find less than a factor of two difference in the detectability threshold despite the change in initial mass of an order of magnitude" (5.2 Detecting Starless Cores)
7. **Predict number of detectable starless-core substructures**: Detections > (2/3) N_total (n_Detectable / n_Limit)^-0.5 with Poisson statistics; n_Detectable from the density at which the simulated central peak reaches 5 sigma in the synthetic image; n_Limit from a beam-sized core at the SCUBA 5 sigma limit  
  > "The central core peak in the simulations is only detected at a 5$\sigma$ level after 0.149 Myr, when the central core density reaches $1.36 \times 10^7~\text{cm}^{-3}$." (5.2 Detecting Starless Cores); "This corresponds to a minimum detectable density of $2.11 \times10^4~\text{cm}^{-3}$." (5.2 Detecting Starless Cores)
   - parameter: N_total = 58 starless cores  
  > "we have $N_{\text{total}} = 58$ starless cores" (5.2 Detecting Starless Cores)
   - assumption: Continuous star formation over a timescale at least as long as the core lifetimes; all observed cores collapse  
  > "With the assumption of a continuous rate of star formation over the timescale at least as long as the core lifetimes" (5.2 Detecting Starless Cores)
   - fitting: Poisson statistics for the uncertainty  
  > "along with Poisson statistics" (5.2 Detecting Starless Cores)
   - validation: Sensitivity tests: alternative lower density limit gives 0.79; SCUBA-2 based range of 47-61 cores gives 1.23-1.60; 4 Msun simulation gives 1.23  
  > "we would lower our expected number of starless core detections to 0.79." (5.2 Detecting Starless Cores); "This range places the number of predicted detections between 1.23 and 1.60." (5.2 Detecting Starless Cores)
8. **Estimate the ALMA-detectable starless core lifetime**: Relative number counts: ratio of the one ALMA starless detection to 37 Class I cores, scaled by the 0.74 Myr Class I lifetime; compared with the free-fall time at the core central density  
  > "we estimate the lifetime for ALMA detectability to be $2.0\times10^4$ yr." (5.3 Evolutionary Lifetime Estimate); "Our starless core has an estimated central density of $1.86 \times 10^7~\text{cm}^{-3}$, implying a free-fall timescale of $7.12 \times 10^3~\text{yr}$." (5.3 Evolutionary Lifetime Estimate)
   - assumption: Continuous star formation rate  
  > "Assuming a continuous star formation rate, the ratio of lifetimes of earlier and later phase objects is directly reflected in the relative number counts." (5.3 Evolutionary Lifetime Estimate)
   - fitting: _not stated_
   - validation: Authors stress large uncertainty from a single detection  
  > "noting the inherently large uncertainty with only one starless core detected in our sample" (5.3 Evolutionary Lifetime Estimate)
9. **Compare core boundedness across Chamaeleon I, Ophiuchus and Orion B North**: Jeans/virial parameter alpha from core mass, size and NH3 (N2H+ for Cha I) line width, then a fuller virial energy balance adding external pressure from cloud weight (extinction maps) and large-scale turbulence (12CO line widths); magnetic term excluded  
  > "while a ratio less than one indicates that the core is unbounded and most likely will disperse over time." (6.4 Virial Analysis); "unfortunately no such uniform data was available for the magnetic field strength, so we exclude this term." (6 Comparison to Chamaeleon I and Ophiuchus)
   - parameter: Extinction to column density: 1 mag = 9.4e20 cm^-2; mean surface density from pixels with Av > 3 mag  
  > "We compute the mean mass surface density using all pixels above $A_{\text{v}} = 3~\text{mag}$ associated with the cloud." (6.4 Virial Analysis); "using a conversion of $1~\text{mag} = 9.4\times 10^{20}~\text{cm}^{-2}$ from" (6.4 Virial Analysis)
   - parameter: n_CO = 250 cm^-3 for the CO-probed gas  
  > "we utilize the mean density found in star forming cloud environments, 250 cm$^{-3}$" (6.4 Virial Analysis)
   - assumption: T = 15 K for Orion B North cores with line width only  
  > "We assume a temperature of $T=15~\text{K}$ for all cores which only have line width measurements" (Table 4 notes)
   - assumption: T = 13 K for Ophiuchus cores with line width only; T = 10 K for Chamaeleon I  
  > "we assume a temperature of $T=13~\text{K}$ for all cores that have only line width information available" (6.2.1 Ophiuchus)
   - assumption: Single-component Gaussian for CO spectra  
  > "We utilize a single component Gaussian model, which is a reasonable representation based on visual checks of the spectra." (6.4 Virial Analysis)
   - fitting: Single-component Gaussian fit to CO spectra at each core position  
  > "We utilize a single component Gaussian model" (6.4 Virial Analysis)
   - validation: Using higher-resolution individual CO surveys changes fitted linewidths by about 20% on average (at most 30%) without altering conclusions; compared with Kerr et al. 2019  
  > "yielded differences in the fitted linewidths of approximately 20% on average, and no more than 30% in difference." (6.4 Virial Analysis)

## Software

- **CASA** pipeline 4.7.0 (calibration); 6.5.0 (imaging and analysis): pipeline calibration, imaging, self-calibration, mosaicking, line cubes  
  > "The calibration and reduction was conducted in the pipeline version 4.7.0 of the Common Astronomy Software Applications (CASA) software." (2.2 ALMA Data); "For imaging and analysis, CASA version 6.5.0 was utilized for its refined automasking routines" (2.2 ALMA Data)
- **CASA imfit** : elliptical Gaussian fits to continuum sources  
  > "to fit elliptical Gaussians to all continuum sources found" (2.2 ALMA Data)
- **CASA simalma** : generating synthetic ALMA observations of the simulated cores  
  > "The synthetic observations were generated using CASA" (5.1 Numerical Simulations and Synthetic Observations)
- **ORION AMR code** : MHD simulation of collapsing starless cores that provides the synthetic-observation inputs  
  > "using the ORION Adaptive Mesh Refinement (AMR) code base" (5.1 Numerical Simulations and Synthetic Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of ALMA 106 GHz continuum sources detected | 34 | not stated | sources | 2 | We detect a total of 34 continuum sources across 19 individual ALMA pointings. |
| ALMA pointings with detections | 19 | not stated | pointings | 2 | We detect a total of 34 continuum sources across 19 individual ALMA pointings. |
| Detections classified as likely starless | 4 (sources 1, 4, 23, 24) | not stated | sources | 3 | we classify sources 1, 4, 23, and 24 as likely being starless. |
| Detections coincident with a Spitzer YSO (<2 arcsec) | 27 | not stated | sources | 3 | In total, we find that 27 of our ALMA detections are found in the Spitzer catalog |
| SCUBA cores reclassified as protostellar | 15 | not stated | cores | 3 | A total of 15 SCUBA cores are re-classified as protostellar based on the catalogs studied |
| Truly starless fields among 73 observed | 58 | not stated | fields | 3 | we find that 58 fields are truly starless after verifying all ancillary data. |
| Detection significance of source 1 | 8 | not stated | times local rms | 2 | has a detection significance of 8 times the local rms noise. |
| Detection significance of source 4 | 7.4 | not stated | times local rms | 2 | has a detection significance of 7.4 times the local rms noise. |
| SCUBA core concentration, source 1 / source 4 / sources 23 and 24 | 0.55 / 0.84 / 0.69 | not stated | dimensionless | 5 | Our starless core candidates lie in SCUBA dense cores with concentration values of 0.55 (source 1), 0.84 (source 4), and 0.69 (sources 23 and 24). |
| Minimum detectable density n_Limit (SCUBA) | 2.11e4 | not stated | cm^-3 | 7 | This corresponds to a minimum detectable density of $2.11 \times10^4~\text{cm}^{-3}$. |
| ALMA detectability density n_Detectable (central core density at 5 sigma, 0.149 Myr) | 1.36e7 | not stated | cm^-3 | 7 | The central core peak in the simulations is only detected at a 5$\sigma$ level after 0.149 Myr, when the central core density reaches $1.36 \times 10^7~\text{cm}^{-3}$. |
| Predicted starless core detections | 2 (1.52) | +/-1 (Poisson) | cores | 7 | and find at least two (1.52) starless core should be detectable, consistent with our data. |
| Predicted detections if lowest-density core (5.68e3 cm^-3) sets the limit | 0.79 | not stated | cores | 7 | we would lower our expected number of starless core detections to 0.79. |
| Predicted detections for 47 to 61 starless cores | 1.23 to 1.60 | range | cores | 7 | This range places the number of predicted detections between 1.23 and 1.60. |
| Predicted detections from 4 Msun simulation | 1.23 | not stated | cores | 7 | suggesting a similar number of detections (1.23) |
| Lifetime for ALMA detectability of the starless core | 2.0e4 | not stated (large, one detection) | yr | 8 | we estimate the lifetime for ALMA detectability to be $2.0\times10^4$ yr. |
| Free-fall timescale at central density 1.86e7 cm^-3 | 7.12e3 | not stated | yr | 8 | Our starless core has an estimated central density of $1.86 \times 10^7~\text{cm}^{-3}$, implying a free-fall timescale of $7.12 \times 10^3~\text{yr}$. |
| Ratio of ALMA-detectable lifetime to free-fall time | 2.80 | not stated | dimensionless | 8 | larger than this free-fall timescale by a factor of 2.80 |
| Cores in virial analysis (Cha I / Oph / Orion B North / total) | 19 / 55 / 18 / 92 | not stated | cores | 9 | In total, we present the 19 dense cores in Chamaeleon I, 55 dense cores in Ophiuchus, and 18 dense cores in Orion B North, for a total of 92 dense cores in our virial analysis. |
| Cores with alpha <= 2 in Jeans analysis (Ophiuchus, Orion B North) | 15% (8/55), 22% (4/18); 0 in Chamaeleon I | not stated | fraction | 9 | In contrast, 15% ($8/55$) and 22% ($4/18$) dense cores have |
| Starless cores bound with all virial terms (Cha I, Oph, Orion B North) | 54% (7/13), 8% (3/36), 38% (5/13) | not stated | fraction | 9 | 54% ($7/13$) of starless cores in Chamaeleon I, 8% ($3/36$) of starless cores in Ophiuchus, and 38% ($5/13$) of cores in Orion B North qualify as bound. |
| Mean extinction of cloud pixels with Av > 3 mag (Cha I, Oph, Orion B North) | 4.95, 5.23, 4.91 | not stated | mag | 9 | The mean extinctions are similar across all three clouds, with values of 4.95 mag, 5.23 mag, and 4.91 mag, for Chamaeleon I, Ophiuchus, and Orion B North respectively. |

## Qualitative findings

- Three of the four starless candidates sit near groupings of protostellar sources in fragmenting cores; one is an isolated detection  
  > "The other three all appear to be associated with fragmenting cores that already contain one of more protostellar sources." (3.4 Candidate Starless Core Detections)
- Source 5 shows red- and blue-shifted CO emission and is a possible first hydrostatic core candidate  
  > "this structure is likely a deeply embedded object, possibly a candidate first hydrostatic core." (3.2 ALMA CO Data)
- Starless detections all lie in the lowest ALMA peak-flux bin  
  > "All of our starless core detections notably lie in the lowest peak flux bin" (4.2 ALMA Peak Flux)

## Claim tuples

- H: Is the number of starless-core compact detections in Orion B North consistent with the turbulent fragmentation model? | E: Synthetic ALMA observations of a turbulent MHD core simulation combined with the observed SCUBA starless core population | R: Predicted at least 2 (1.52) detections; one detection in a truly starless core | F: The single detection is consistent with the turbulent fragmentation prediction, and with Ophiuchus | **supported**
- H: Does core boundedness explain the lack of detections in Chamaeleon I versus Ophiuchus and Orion B North? | E: Jeans and virial analyses of 92 cores using NH3/N2H+ line widths plus cloud weight and turbulent pressure terms | R: No Cha I cores bound under self-gravity alone; with external pressure 54%, 8% and 38% are bound in Cha I, Oph and ONB | F: Cha I cores are less bound and external pressure dominates their binding; this offers a plausible explanation | **supported**
- H: How many of the ALMA 3 mm detections are truly starless? | E: Cross-matching 34 ALMA detections with Spitzer, VANDAM, ALMASOP and other catalogs plus 12CO outflow search | R: 4 starless candidates, only one within a truly starless SCUBA core | F: Most ALMA starless candidates are fragments in cores already containing protostars | **supported**
- H: What is the lifetime of cores at densities near 1e7 cm^-3? | E: Relative counts of one ALMA starless detection versus 37 Class I sources scaled by the Class I lifetime | R: 2.0e4 yr, a factor 2.80 above the free-fall time | F: Lifetime is closer to the free-fall time than to ten times it, with large uncertainty | **partially**

## Reasoning

- Why this data: A similarly designed survey in Orion B to complement the Chamaeleon I and Ophiuchus ALMA studies  
  > "we present results from a similarly designed survey of starless cores in the Orion B molecular cloud." (1 Introduction)
- Why this method: Population statistics of detections test thermal versus turbulent fragmentation  
  > "Population studies, in general, through the total number of detections, can provide a basis to evaluate whether fragmentation within the core is more consistent with thermal or turbulent origins." (1 Introduction)
- Alternative: Bonnor-Ebert sphere density profiles would make even a single detection very unlikely  
  > "we note that under the BE sphere-like model, it would be very unlikely to get a single detection." (5.2 Detecting Starless Cores)
- Alternative: Alternative lower density limit (lowest-density elongated core) gives 0.79 expected detections; results unaffected  
  > "we would lower our expected number of starless core detections to 0.79." (5.2 Detecting Starless Cores)
- Alternative: Individual all-sky CO surveys instead of the Dame and Thaddeus survey changed linewidths by about 20% without changing results  
  > "These specific changes in the fitted spectra do not significantly change the results shown." (6.4 Virial Analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): A single detection is a small sample for model testing  
  > "A single detection under the turbulent fragmentation model is not a large number for model testing" (5.2 Detecting Starless Cores)
- Limitation (authors): Mass and density uncertainties are dominated by systematics (temperature, distance, opacity)  
  > "The uncertainties are dominated by systematic effects (such as temperature, distance, dust opacity, etc.)" (4.1 Mass Estimates)
- Limitation (authors): Turbulent pressures likely overestimated because of coarse CO spectral resolution  
  > "we are likely to have over-estimated our turbulent pressures across all three core populations." (6.4 Virial Analysis)
- Limitation (authors): Orion B North kinematic coverage is only 31% (18 of 58 cores)  
  > "In Orion B North, only 18 of the 58 dense cores, or 31% have GAS line width measurements" (6.2.2 Orion B North)
- Caveat (inferred, ours): Only one genuinely starless detection, so agreement with a predicted 2+/-1 has little discriminating power against the BE-sphere or other models
- Caveat (inferred, ours): Detections are called starless by absence of catalog counterparts; low-luminosity or very young embedded sources could be missed
- Caveat (inferred, ours): Predicted counts hinge on a single 0.4 Msun simulation set and an assumed 5 sigma criterion and on n_Limit chosen by the authors
- Caveat (inferred, ours): Chamaeleon I, Ophiuchus and Orion datasets differ (different surveys, tracers, assumed temperatures), so virial comparisons are partly heterogeneous
- Caveat (inferred, ours): Assumed constant T = 10 K and kappa = 0.23 cm^2/g give systematic mass errors of factors of a few

## Reproducibility

- Data public (paper): Associated data products, figures and tables hosted at CADC (DOI link given)  
  > "All associated data, including compiled figures and tables, are publicly available at the CADC via the following link:" (Data Availability)
- Products in archive: _not stated_
- Missing: Line-free channel selection and continuum-subtraction details
- Missing: Self-calibration solution intervals and the list of fields self-calibrated
- Missing: Full tclean parameters for real data and mosaics
- Missing: simalma configuration details and the simulation snapshots
- Missing: Unpublished SESNA catalog used for the Class I count
- Missing: Details of the formal source-detection threshold
- Data volume (inferred): Band 3, 73 fields x 7 execution blocks with 4 spws; likely tens of GB raw for the project (not stated in the paper)
- Score (inferred): 3/5, ALMA project code and a CADC data release are given with numeric results and formulas, but self-calibration, tclean, simalma and catalog inputs (SESNA, simulation snapshots) are incompletely specified
- Rediscovery candidate: no, ALMA data are likely public, but the paper does not state it, key imaging and self-calibration settings are missing and the expected-detection step relies on simulation snapshots and an unpublished catalog

## Links

- Method: Dunham et al. 2016 (cite: Dunham2016) (Original Chamaeleon I design, simulations and synthetic observation recipe reused here)
- Method: Kirk et al. 2017 (cite: Kirk2017) (Ophiuchus ALMA study using the same approach and snapshots)
- Method: The CASA Team 2022 (cite: TheCASATeam2022) (CASA reference for imaging tasks and briggsbwtaper)
- Method: Pattle et al. 2015 (cite: Pattle2015) (Virial energy balance method followed)
- Companion: Nutter & Ward-Thompson 2007 (cite: Nutter2007) (SCUBA catalog used for target selection and core properties)
- Companion: Kirk et al. 2016 (cite: Kirk2016) (SCUBA-2 Orion core catalog for comparison)
- Companion: Tobin et al. 2020 (cite: Tobin2020) (VANDAM protostar catalog for associations)
- Companion: Sahu et al. 2021 (cite: Sahu2021) (ALMASOP study of the G205.46-14.56M3 core coincident with source 1)
- Related: VANDAM
- Related: ALMASOP
- Related: Green Bank Ammonia Survey (GAS)
- Related: JCMT Gould Belt Survey
- Related: Herschel Orion Protostellar Survey (HOPS)
- Related: SESNA

## Checks

```json
{
 "quotes": 162,
 "quotes_ok": 162,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 22,
 "numeric_problems": 0,
 "fill": {
  "facts": 125,
  "stated": 105,
  "rate": 0.84
 },
 "evidence_ok": true
}
```
