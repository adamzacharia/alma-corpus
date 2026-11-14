# ASW<SUP>2</SUP>DF: Census of the obscured star formation in a galaxy cluster in formation at z = 2.2

`2024A&A...692A..22Z` | Astronomy and Astrophysics 2024 | first author: Zhang, Y. H. | arXiv: 2410.10169 | DOI: 10.1051/0004-6361/202451379

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, galaxy_clusters_and_sz
- Question: Census of dust-obscured star-forming galaxies in the Spiderweb protocluster: ALMA 1.2 mm number counts, overdensity, spatial distribution relative to HAEs and CO emitters, and single-dish multiplicity  
  > "mapping dusty star-forming galaxies through ALMA band 6 observations on the Spiderweb protocluster at $z=2.16$" (1 Introduction)
- Target **Spiderweb protocluster (around radio galaxy MRC1138-262)**: coordinates _not stated_; z/distance z = 2.16  
  > "One of the most overdense structures is the prominent Spiderweb protocluster at $z=2.16$" (1 Introduction); "The high redshift radio galaxy MRC1138-262" (1 Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2021.1.00435.S
- bands: Band 6 (1.2 mm), six contiguous fields, each an 87-pointing mosaic covering 1' x 3'  
  > "each field is made up by a 87-pointing mosaic covering an area of $1^\prime\times3^\prime$" (2.1 Observations); "between 31 December 2021 and 17 April 2022 in ALMA band 6" (2.1 Observations)
- frequencies and spectral setup: single tuning, four SPWs centred at 239.0, 241.0, 255.0, 257.0 GHz; 128 channels of 15.625 MHz per SPW, dual polarization, 1.875 GHz per SPW  
  > "The correlator was set up at a single tuning, with four spectral windows centered at 239.0, 241.0, 255.0 and 257.0 GHz respectively." (2.1 Observations); "Each spectral window contains 128 channels of 15.625 MHz each in dual polarization with a bandwidth of 1.875 GHz." (2.1 Observations)
- continuum bandwidth: 6.375 GHz final available bandwidth  
  > "The final available bandwidth is 6.375 GHz." (2.2 Data reduction)
- arrays: _not stated_
- configurations: C4 (Fields 1-3 and two EBs of Field 4); C2 (eight EBs in Fields 4-6)  
  > "All the EBs in Field 1$-$3 and two in Field 4 were observed in C4 configuration, with a baseline range of 14.9$-$976.6 m and a theoretical resolution of 0.4$''$." (2.1 Observations); "The remaining eight EBs in Field 4$-$6 were observed in C2 configuration, with a baseline range of 15.0 m to 500.2 m and a theoretical resolution of 0.7$''$." (2.1 Observations)
- baselines: 14.9-976.6 m (C4); 15.0-500.2 m (C2)  
  > "with a baseline range of 14.9$-$976.6 m and a theoretical resolution of 0.4$''$" (2.1 Observations); "with a baseline range of 15.0 m to 500.2 m and a theoretical resolution of 0.7$''$" (2.1 Observations)
- angular resolution: average 0.49'' x 0.34'' (Fields 1-3); 0.87'' x 0.60'' (Fields 4-6)  
  > "The average resolution is 0.49$''$ $\times$ 0.34$''$ with a pixel scale of 0.07$''$ for Field 1$-$3" (2.2 Data reduction); "while the average resolution is 0.87$''$ $\times$ 0.60$''$ with a pixel scale of 0.14$''$ for Field 4$-$6" (2.2 Data reduction)
- max recoverable scale: 4.5'' (C4) and 8.2'' (C2)  
  > "The maximum recoverable scales are 4.5$''$ and 8.2$''$ in C4 and C2 configurations, respectively." (2.1 Observations)
- sensitivity: 1 sigma rms 40.3-57.1 uJy across the six fields  
  > "and a sensitivity range from 40.3 $\mu$Jy to 57.1 $\mu$Jy" (2.2 Data reduction)
- time on source: 2.03 h per field (2.70 h for Field 4); 12.84 h total  
  > "The on source time was 2.03 h for each field (except 2.70 h for Field 4), resulting in a total on source time of 12.84 h." (2.1 Observations)
- observing dates: 31 December 2021 to 17 April 2022 (Cycle 8)  
  > "The observations were carried out in Cycle 8 (Project ID: 2021.1.00435.S; PI: Y. Koyama) between 31 December 2021 and 17 April 2022 in ALMA band 6." (2.1 Observations)
- pi or archival as stated: Cycle 8 project, PI Y. Koyama  
  > "Cycle 8 (Project ID: 2021.1.00435.S; PI: Y. Koyama)" (2.1 Observations)
- Line: CO 7-6 (covered by the tuning; results deferred to a later paper) (806.65 GHz)
- Line: CI 2-1 (covered by the tuning; results deferred to a later paper) (809.34 GHz)
- Other facility **ATCA (COALAS CO(1-0) large program)**: CO(1-0) emitter catalogue and line luminosities used for spatial comparison and gas masses  
  > "is complemented by the existing COALAS CO(1-0) large program (cite: Jin2021)" (2 Observations and data reduction)
- Other facility **H-alpha narrow-band imaging (HAEs)**: H-alpha emitter positions and density map tracing the filamentary structure  
  > "This survey covers the central part of the filamentary structure traced by HAEs (cite: Koyama2013; Shimakawa2018b)" (2 Observations and data reduction)
- Other facility **APEX/LABOCA**: 870 um single-dish SMGs for multiplicity and flux-recovery comparison  
  > "reported 16 SMGs detected by APEX LABOCA" (5.1 Overdensity of DSFGs detected by ALMA)
- Other facility **ASTE/AzTEC**: 1.1 mm single-dish sources for multiplicity and flux-recovery comparison  
  > "47 sources are detected by ASTE/AzTEC at 1.1 mm in the Spiderweb field" (5.1 Overdensity of DSFGs detected by ALMA)
- External data: HAE catalogue and density map method  
  > "The adopted method and the constructed HAE density map are identical to those of (cite: Shimakawa2018b)." (5.2 Spatial correlation between different populations) [from (cite: Shimakawa2018b)]
- External data: CO(1-0) emitter catalogue with alpha_CO assignment per source  
  > "Following (cite: Jin2021), we assign different $\alpha_{\rm CO}$ values for each source individually" (5.2 Spatial correlation between different populations) [from (cite: Jin2021)]
- External data: Average ALESS SED used for flux conversion between wavelengths and to 850 um for SFRs  
  > "We adopt an average spectral energy distribution from a sample of ALESS SMGs (cite: da_Cunha2015), and assume a redshift of 2.2" (4.3 Number counts) [from (cite: da_Cunha2015)]
- External data: General-field cumulative number counts used as the baseline for overdensity  
  > "We adopt the recent results from the ALMACAL (cite: Chen2023a) and GOODS-ALMA (cite: Franco2018; Gomez2022) surveys" (5.1 Overdensity of DSFGs detected by ALMA) [from (cite: Chen2023a); (cite: Franco2018); (cite: Gomez2022)]
- External data: General-field best-fitting curve for ADF22/SSA22-style overdensity comparison  
  > "We compare our number counts with the fitting curve of general fields given in (cite: Umehata2018)" (5.1 Overdensity of DSFGs detected by ALMA) [from (cite: Umehata2018)]
- External data: LABOCA SMG fluxes and positions  
  > "reported 16 SMGs detected by APEX LABOCA" (5.1 Overdensity of DSFGs detected by ALMA) [from (cite: Dannerbauer2014)]
- External data: SFR-to-850 um linear relation  
  > "then derive the SFR for each source based on the linear relation from (cite: Cowie2017)" (5.2 Spatial correlation between different populations) [from (cite: Cowie2017)]
- External data: Average cosmic SFR density for comparison  
  > "being around 14 times that of the average cosmic SFR density (cite: Madau2014)" (5.2 Spatial correlation between different populations) [from (cite: Madau2014)]
- Simulation/model as data: Monte Carlo mock catalogue of injected point-like artificial sources (30 flux bins 0.1-3.1 mJy, 20 sources per bin, 1000 iterations per bin and field) used for completeness and flux boosting  
  > "we divided the flux range from 0.1 to 3.1 mJy into 30 flux bins with a step of 0.1 mJy" (4.1 Completeness and flux boosting); "The procedure was repeated for 1000 iterations in each flux bin and each field." (4.1 Completeness and flux boosting)

## Processing

### Calibration

- pipeline or manual: calibrated and flagged with the scripts provided by the ALMA archive  
  > "The visibilities were calibrated and flagged using the scripts provided by the ALMA archive." (2.2 Data reduction)
- casa version: _not stated_
- pipeline version: ALMA pipeline 2021.2.0.128  
  > "with the ALMA pipeline version 2021.2.0.128 (cite: Hunter2023)" (2.2 Data reduction)
- archive products used as is: _not stated_
- flux calibrator: J1256-0547 (Fields 1-3 and two EBs of Field 4); J1037-2934 (Fields 5-6 and one EB of Field 4); J1107-4449 (one EB of Field 4); J1146-2859 phase calibrator for all EBs  
  > "One quasar J1256$-$0547 was used for flux and bandpass calibrations in 11 EBs (Field 1$-$3 and two in Field 4)" (2.1 Observations); "another quasar J1037$-$2934 was used in seven EBs (Field 5-6 and one in Field 4)" (2.1 Observations); "The remaining one EB of Field 4 used quasar J1107$-$4449 as a flux and bandpass calibrator" (2.1 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean, mosaic gridder  
  > "within the “mosaic” gridder mode and the “hogbom” deconvolver" (2.2 Data reduction)
- deconvolver: hogbom  
  > "within the “mosaic” gridder mode and the “hogbom” deconvolver" (2.2 Data reduction)
- weighting robust: Briggs, robust = 0.5  
  > "The “Briggs” data weighting with the robust parameter of 0.5 was employed to optimize between angular resolution, noise, and sidelobe levels" (2.2 Data reduction)
- uv taper: _not stated_
- cell size: 0.07'' (Fields 1-3); 0.14'' (Fields 4-6)  
  > "with a pixel scale of 0.07$''$ for Field 1$-$3" (2.2 Data reduction); "with a pixel scale of 0.14$''$ for Field 4$-$6" (2.2 Data reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: SPW edge channels, bad baselines and potential emission lines were flagged for continuum imaging; channel ranges not given  
  > "We note that the channels at the edge of the spectral window and the bad baselines, as well as the potential emission lines mentioned above were flagged for the continuum imaging." (2.2 Data reduction)
- primary beam correction: noise estimation and source extraction on non-PB-corrected images; flux measurement on PB-corrected images  
  > "We use science images without the primary beam (PB) correction for rms noise estimation and source extraction" (3.1 Noise estimation); "The PB-corrected images will be used for the flux measurement of detected objects." (3.1 Noise estimation)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 1 sigma 40.3-57.1 uJy per field  
  > "and a sensitivity range from 40.3 $\mu$Jy to 57.1 $\mu$Jy" (2.2 Data reduction)

### Inherited from earlier work

- Elliptical Gaussian flux fitting with Levenberg-Marquardt (astropy.modeling)  
  > "Following (cite: Chen2023a), we fit the sources using the Levenberg-Marquardt algorithm in the Python package astropy.modeling." (3.3 Flux measurement) [from (cite: Chen2023a)]
- Elliptical aperture of 2 x synthesized beam for aperture photometry  
  > "While (cite: Chen2023a) reported the scaled elliptical aperture (i.e. $2\times$ synthesized beam), which results in reliable flux measurement." (3.3 Flux measurement) [from (cite: Chen2023a)]
- Visual inspection of the maps to verify catalogues and find faint extended sources  
  > "an independent visual inspection was conducted on the ALMA maps to verify the source catalogs extracted by the different codes and identify faint, extended sources below the detection limit (cite: Gonzalez2020)" (3.2 Source extraction) [from (cite: Gonzalez2020)]
- 1.1 mm to 1.2 mm flux conversion factor 1.29 from a modified black body with the ALESS average SED  
  > "to be 1.29, identical to that in (cite: Umehata2018) by using a modified black body model" (4.3 Number counts) [from (cite: Umehata2018)]
- HAE 5th-neighbour density map method  
  > "The adopted method and the constructed HAE density map are identical to those of (cite: Shimakawa2018b)." (5.2 Spatial correlation between different populations) [from (cite: Shimakawa2018b)]
- ALMA-CO cross-matching with a radius of 2-6 arcsec scaled by the ATCA beam, equivalent to a fixed 3 arcsec radius  
  > "The matching results are the same as those using a fixed radius of 3 arcsec adopted in (cite: Jin2021)." (5.2 Spatial correlation between different populations) [from (cite: Jin2021)]
- Gas mass from dust luminosity on the Rayleigh-Jeans tail  
  > "that the gas mass can be determined from the dust luminosity" (5.2 Spatial correlation between different populations) [from (cite: Scoville2023); (cite: Scoville2014; Scoville2016)]
- Per-source alpha_CO (0.8 starburst, 3.6 star-forming) assignment  
  > "Following (cite: Jin2021), we assign different $\alpha_{\rm CO}$ values for each source individually" (5.2 Spatial correlation between different populations) [from (cite: Jin2021)]

### Not stated but needed to reproduce (our reading)

- Exact CASA version used for tclean (only a CASA citation and the pipeline version are given)
- Whether the archive calibration scripts were run unmodified or with extra flagging, and the specific bad baselines flagged
- tclean parameters beyond gridder/deconvolver/robust: niter, cleaning mask, threshold per field, image size, phase centres of the 87 pointings
- Channel ranges excluded around CO(7-6) and CI(2-1) and at SPW edges for the continuum
- How the C2 and C4 execution blocks in Field 4 were combined in one tclean run (weighting/uv ranges)
- Full SoFiA and AEGEAN configuration beyond the key parameters in Table 1; how the 2D noise maps were produced inside each code
- Bin edges and bin centres used for the differential counts; how the flux-boosting correction was applied to the counts
- Which alpha_CO (0.8 or 3.6) was assigned to each CO emitter and the CO luminosities themselves (from COALAS catalogue)
- Gas-to-dust ratio is printed as 105; the intended value should be confirmed with the authors
- Literature positions and fluxes of HAEs, CO emitters, LABOCA and AzTEC sources and the general-field counts used for the overdensity baseline
- Volume and distance definitions for the SFR densities (line-of-sight lengths are chosen, not derived)

## Analysis recipe

1. **calibrate and image the six mosaics in continuum**: ALMA pipeline/archive scripts for calibration, then CASA tclean mosaic imaging with MFS over the four SPWs, cleaned to 3 sigma  
  > "The visibilities were calibrated and flagged using the scripts provided by the ALMA archive." (2.2 Data reduction); "After measuring the 1$\sigma$ rms within the entire dirty maps, the cleaning process was repeated until reaching the 3$\sigma$ levels in order to obtain the final clean maps." (2.2 Data reduction)
   - software: CASA, tclean, ALMA pipeline
   - parameter: mosaic gridder, hogbom deconvolver, Briggs robust 0.5  
  > "within the “mosaic” gridder mode and the “hogbom” deconvolver" (2.2 Data reduction); "The “Briggs” data weighting with the robust parameter of 0.5 was employed" (2.2 Data reduction)
   - parameter: multi-frequency synthesis over four SPWs  
  > "The multi-frequency synthesis algorithm was used to combine the four spectral windows into the single dirty continuum image." (2.2 Data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **estimate the map noise**: 'fixed' method: standard deviation of the whole non-PB-corrected image after sigma clipping; compared with 'individual' sliding-box noise maps from SEP, AEGEAN, SoFiA  
  > "The “fixed” method is straightforward by calculating the standard deviation of the entire image in each field as the 1$\sigma$ noise, after five iterations of the 5-sigma-clipping process." (3.1 Noise estimation)
   - software: SEP, AEGEAN, SoFiA
   - parameter: individual method: 100x100 pixel box, step of one pixel  
  > "we use the rms box of $100\times100$ pixels with a step size of one pixel to calculate the standard deviation for the central pixel of the box" (3.1 Noise estimation)
   - parameter: only pixels with primary beam response above 50 percent  
  > "All the pixels used for noise estimation are within the coverage where the primary beam response is larger than 50 percent." (3.1 Noise estimation)
   - fitting: _not stated_
   - validation: median ratio of individual to fixed noise ~0.984 for SEP and AEGEAN  
  > "The median ratio of the results of SEP and AEGEAN is both $\sim$ 0.984" (3.1 Noise estimation)
3. **extract sources and build the main and supplementary catalogues**: SEP, AEGEAN and SoFiA run on the non-PB-corrected map at >4 sigma with the 'fixed' noise; plus independent visual inspection; 47 sources detected by all three codes form the main catalogue (categories A and B)  
  > "Interestingly, all three codes produced the same catalog containing 47 detections when we use the 1$\sigma$ noise values from the “fixed” method." (3.2 Source extraction); "We visually identified 53 sources on the six ALMA maps, bypassing the use of any source extraction code." (3.2 Source extraction)
   - software: SEP, AEGEAN, SoFiA
   - parameter: minarea = 5 contiguous pixels above 4 sigma (linker.minPixels = 5 in SoFiA)  
  > "meaning that a source can only be identified when it has at least five contiguous pixels above 4$\sigma$" (3.2 Source extraction)
   - fitting: _not stated_
   - validation: all sources above 5 sigma recovered by visual inspection; all 16 robust visual sources in the main catalogue  
  > "all sources above 5$\sigma$ in the main catalog are recovered by visual inspection" (3.2 Source extraction)
4. **measure purity from negative detections**: p = (N_pos - N_neg)/N_pos per S/N bin, negative peaks found by running the same extraction on the sign-inverted map  
  > "We obtain the negative detections by inverting the science map (multiplying the map by $-1$) and applying the same source extraction process used to detect positive peaks in the original map." (3.2 Source extraction)
   - software: SEP, AEGEAN, SoFiA
   - parameter: S/N range 3.5-5.5, 'fixed' noise  
  > "within the S/N range of $3.5-5.5$ from the “fixed” method" (3.2 Source extraction)
   - fitting: _not stated_
   - validation: purity of the 'fixed' method at 4 sigma is higher than for any 'individual' method  
  > "detections above 4$\sigma$ significance from the “fixed” method have the highest purity compared to any of the three codes using the “individual” method" (3.2 Source extraction)
5. **measure source fluxes**: peak flux on PB-corrected images; elliptical Gaussian fit; elliptical aperture photometry (2 x synthesized beam)  
  > "We firstly extract the peak fluxes of the ALMA sources from the images after the primary beam correction." (3.3 Flux measurement); "we measure the source fluxes using the aperture photometry, which is performed by the Python package photutils" (3.3 Flux measurement)
   - software: astropy.modeling, photutils
   - parameter: Gaussian fit on a cutout of 5 x major axis; amplitude, axial ratio and position angle free  
  > "A cutout image with a size of 5$\times$major axis is extracted, centered on each source, and used for the fitting process." (3.3 Flux measurement)
   - parameter: Gaussian-fit flux uncertainty from 1000 iterations at random positions  
  > "The uncertainty in the integrated flux for each source is estimated through the standard deviation obtained from 1000 iterations of the flux measurements using the same best-fitting Gaussian aperture at random positions." (3.3 Flux measurement)
   - fitting: Levenberg-Marquardt elliptical Gaussian fit (astropy.modeling)  
  > "we fit the sources using the Levenberg-Marquardt algorithm in the Python package astropy.modeling" (3.3 Flux measurement)
   - validation: Gaussian and aperture fluxes both recover intrinsic flux within 3 percent above 5 sigma in the Monte Carlo test  
  > "within a 3 percent difference than intrinsic flux" (4.1 Completeness and flux boosting)
6. **derive completeness and flux boosting by Monte Carlo injection**: inject point-like artificial sources convolved with the synthesized beam into the PB-corrected image, convert to PB-uncorrected, re-run extraction and flux measurement, compare recovered to input  
  > "We used a Monte Carlo simulation to characterize the completeness of our science catalog." (4.1 Completeness and flux boosting); "We obtained the flux boosting factor by dividing the recovered flux ($S_{\rm out}$) by the input flux ($S_{\rm in}$) of each source in the matched catalog." (4.1 Completeness and flux boosting)
   - software: SEP, photutils, astropy.modeling
   - parameter: 20 sources per bin, normal random flux, random positions with PB response > 0.5 and separations of at least 1 arcsec  
  > "In each flux bin, we generate an artificial catalog with 20 sources with assigned fluxes from the normal random distribution." (4.1 Completeness and flux boosting)
   - parameter: recovered if extracted within 1 arcsec of the injected position  
  > "The artificial sources were considered recovered when they were extracted less than 1 arcsec from their original injected positions." (4.1 Completeness and flux boosting)
   - assumption: artificial sources are point-like (conservative choice)  
  > "We introduced point-like sources instead of sources with specific sizes (cite: Gomez2022)" (4.1 Completeness and flux boosting)
   - fitting: _not stated_
   - validation: completeness of Field 3 and Field 4 compared with the overall curve; overall curve used for all fields  
  > "We used the overall one for all six fields to correct for our science catalog." (4.1 Completeness and flux boosting)
7. **compute effective area and differential/cumulative number counts**: each source contributes xi = p/(A_eff C); summed per flux bin for dN/dS and above S0 for N(>S); effective area from local noise (fixed noise divided by PB response)  
  > "$C(S)$ is the completeness associated with the source flux." (4.3 Number counts); "We calculate the effective area as a function of the local noise that increases from the center to the edges of the images." (4.2 Effective area)
   - parameter: uncertainties from 1000 resamplings of source fluxes with their measured flux and 1 sigma noise; median and 1 sigma dispersion adopted  
  > "We calculate the uncertainties of the number counts by constructing 1000 rounds of the number counts." (4.3 Number counts); "In each iteration, the flux of each source is randomly sampled based on its measured flux and the 1$\sigma$ noise." (4.3 Number counts)
   - parameter: Gaussian-fit fluxes used for the counts; aperture fluxes give consistent results  
  > "The Gaussian fitting fluxes are adopted in the following analysis, including the number counts calculation." (4.1 Completeness and flux boosting)
   - fitting: _not stated_
   - validation: tested with aperture photometry fluxes  
  > "We also tested the analysis with aperture photometry and obtained consistent results." (4.1 Completeness and flux boosting)
8. **quantify the DSFG overdensity relative to general fields**: ratio of cumulative number counts in Spiderweb to literature general-field counts (ALMACAL, GOODS-ALMA) in five log flux bins 0.25-1.69 mJy; also simple surface densities above 0.23 mJy  
  > "The overdensity is characterized by the ratio between the number counts in the Spiderweb protocluster and the results from general fields." (5.1 Overdensity of DSFGs detected by ALMA); "we adopt the five flux bins in logarithmic space within a flux range of 0.25$-$1.69 mJy and calculate the cumulative number counts" (5.1 Overdensity of DSFGs detected by ALMA)
   - parameter: 1.1 mm counts converted to 1.2 mm with factor 1.29  
  > "We convert the number counts at 1.1 mm in GOODS-ALMA survey to that at 1.2 mm by using the factor of 1.29 mentioned above." (5.1 Overdensity of DSFGs detected by ALMA)
   - assumption: ALESS average SED at z = 2.2 for the wavelength conversion  
  > "We adopt an average spectral energy distribution from a sample of ALESS SMGs (cite: da_Cunha2015), and assume a redshift of 2.2" (4.3 Number counts)
   - fitting: _not stated_
   - validation: repeated with >5 sigma sources only (overdensity 1.7 at lowest flux bin)  
  > "This results in an overdensity of 1.7 at the lowest flux bin compared to field" (5.1 Overdensity of DSFGs detected by ALMA)
9. **compare spatial distributions of DSFGs, HAEs and CO emitters**: 5th-neighbour density maps, per-field surface-density excess normalised by the footprint mean, cumulative distributions with distance to the Spiderweb galaxy, and 2D Kolmogorov-Smirnov tests  
  > "We build the density maps of HAEs (in blue), DSFGs (in orange), and CO emitters (in green) based on the 5th neighbor analysis." (5.2 Spatial correlation between different populations); "we adopted a 2D Kolmogorov-Smirnov test (cite: Peacock1983; Fasano1987)" (5.2 Spatial correlation between different populations)
   - parameter: CO matching radius 2-6 arcsec scaled by ATCA beams; HAE matching radius 1 arcsec  
  > "by cross-matching these two populations with a varied radius of $2-6$ arcsec scaled by the ATCA synthesized beams (cite: Jin2021)" (5.2 Spatial correlation between different populations); "10 of 47 DSFGs in our main catalog are HAEs within a matching radius of 1 arcsec" (5.2 Spatial correlation between different populations)
   - fitting: _not stated_
   - validation: K-S significance below 2 sigma for HAE vs DSFG and HAE vs CO, so distinctness is not established  
  > "we cannot determine that they are totally distinct populations" (5.2 Spatial correlation between different populations)
10. **derive dust-based gas masses and compare with CO gas masses**: gas mass from Rayleigh-Jeans dust luminosity (Gaussian-fit fluxes), compared with CO(1-0)-based masses for the 13 matched sources  
  > "we derive the gas masses of our ALMA sources to be $2.0-27.3\times10^{10}\,{\rm M}_{\odot}$ based on the Gaussian fitting flux measurements" (5.2 Spatial correlation between different populations)
   - parameter: alpha_CO 0.8 (starburst) and 3.6 (star-forming), also tested as single values for all sources  
  > "a $\alpha_{\rm CO, SB}=0.8$ and $\alpha_{\rm CO,SFG}= 3.6$" (5.2 Spatial correlation between different populations)
   - assumption: dust temperature 25 K, beta = 2, gas-to-dust mass ratio 105 (as printed)  
  > "By assuming a dust temperature of 25 K, spectral index $\beta=2$, and a constant gas-to-dust-mass ratio of 105 (cite: Draine2011)" (5.2 Spatial correlation between different populations)
   - fitting: _not stated_
   - validation: direct comparison with CO-derived masses (Figure 9)  
  > "It is clearly seen that the gas masses obtained from dust and CO emissions do not agree with each other." (5.2 Spatial correlation between different populations)
11. **derive SFRs, SFR densities and group properties**: convert 1.2 mm fluxes to 850 um via ALESS SED, SFR from the Cowie et al. linear relation; SFR density for several assumed volumes; depletion time from SFR and dust-based gas mass  
  > "We firstly convert the fluxes of these ALMA sources into fluxes at 850 $\mu$m according to the ALESS SED (cite: da_Cunha2015), then derive the SFR for each source based on the linear relation from (cite: Cowie2017)." (5.2 Spatial correlation between different populations)
   - parameter: volumes: 120 cMpc line of sight over ~20 arcmin^2 (48 cMpc^2); 2 Mpc sphere; ~400 kpc sphere  
  > "However, if considering a 2 Mpc sphere as adopted in (cite: Dannerbauer2014), which is representative of a core-like volume" (5.2 Spatial correlation between different populations)
   - assumption: volume choice drives the SFR density  
  > "The derived SFR density depends significantly on the assumed volume." (5.2 Spatial correlation between different populations)
   - fitting: _not stated_
   - validation: _not stated_
12. **compare ALMA with single-dish LABOCA/AzTEC detections**: sum ALMA fluxes inside each single-dish beam, scale single-dish fluxes to 1.2 mm, and compute the ratio and multiplicity  
  > "We sum up the fluxes of ALMA sources located within each LABOCA/AzTEC beam." (5.4 Comparison between ALMA and single-dish observations)
   - parameter: AzTEC beam FWHM 30 arcsec  
  > "under the same instrument beam size of FWHM=30 arcsec" (5.4 Comparison between ALMA and single-dish observations)
   - assumption: single-dish fluxes scaled to 1.2 mm with the same SED method as in Sec. 4.3  
  > "The fluxes of the single-dish sources are scaled to 1.2 mm by using the same method described in Sec." (5.4 Comparison between ALMA and single-dish observations)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration (with ALMA pipeline 2021.2.0.128) and continuum imaging  
  > "The Common Astronomy Software Applications (cite: CASA2022) with the ALMA pipeline version 2021.2.0.128 (cite: Hunter2023) were used to perform the data reduction." (2.2 Data reduction)
- **tclean** : mosaic continuum imaging with hogbom deconvolver  
  > "within the “mosaic” gridder mode and the “hogbom” deconvolver" (2.2 Data reduction)
- **SEP** : source extraction (SExtractor core algorithms) and noise maps  
  > "We extract ALMA sources with the Python package SEP (cite: Barbary2016), which uses the core algorithms of SExtractor (cite: Bertin1996)." (3 Source catalog)
- **AEGEAN** : second source finder and noise maps  
  > "We also use AEGEAN (cite: Hancock2012; Hancock2018) which is specifically designed and often used in the radio domain" (3 Source catalog)
- **SoFiA** : third source finder, used as a further check  
  > "we use the Source Finding Application (SoFiA) (cite: Serra2015; Westmeier2021) to extract the ALMA sources as a further check" (3 Source catalog)
- **astropy.modeling** : elliptical Gaussian fitting of source fluxes  
  > "we fit the sources using the Levenberg-Marquardt algorithm in the Python package astropy.modeling" (3.3 Flux measurement)
- **photutils** : aperture photometry  
  > "we measure the source fluxes using the aperture photometry, which is performed by the Python package photutils" (3.3 Flux measurement)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1 sigma rms noise range across the six fields | 40.3-57.1 | not stated | uJy | 1 | the final maps in the six fields reach the 1$\sigma$ rms noise in a range of $40.3-57.1\,\mu$Jy |
| median ratio of 'individual' to 'fixed' noise (SEP and AEGEAN) | ~0.984 | not stated | dimensionless | 2 | The median ratio of the results of SEP and AEGEAN is both $\sim$ 0.984 |
| sources in main catalogue (all three codes, fixed noise, >4 sigma) | 47 | not stated | sources | 3 | all three codes produced the same catalog containing 47 detections |
| tentative sources in supplementary catalogue | 21 | not stated | sources | 3 | we obtain a supplementary catalog including 21 tentative sources in total |
| purity at S/N = 4 ('fixed' method) | ~0.9 | not stated | dimensionless | 4 | The purity reaches $\sim0.9$ at a threshold of S/N=4 |
| completeness thresholds | 80% at ~0.3 mJy; 100% at ~0.6 mJy | not stated | mJy | 6 | reaching 80% and 100% completeness at around 0.3 mJy and 0.6 mJy, respectively |
| total effective survey area | 19.3 at noise of 120 uJy | not stated | arcmin^2 | 7 | reach the maximum of 19.3 arcmin$^2$ at the noise of 120 $\mu$Jy |
| 1.1 mm to 1.2 mm flux conversion factor S_1.1mm/S_1.2mm | 1.29 | not stated | dimensionless | 8 | to be 1.29, identical to that in (cite: Umehata2018) by using a modified black body model |
| number density of ALMA sources in Spiderweb vs general fields | 2.1 (Spiderweb) vs 1.0 (general fields) | 0.3 (Spiderweb); 0.4 (general fields) | arcmin^-2 | 8 | We obtain a number density of $\rho\sim2.1\pm0.3\,\rm arcmin^{-2}$ in the field of the Spiderweb protocluster |
| overdensity of the entire Spiderweb field vs Umehata et al. fitted field curve | 2.08 | not stated | dimensionless | 8 | obtain an overdensity of 2.08 in the entire Spiderweb field |
| overdensity factor around the Spiderweb galaxy in radii <150, 150-300, 300-450, 450-600, 600-750, 750-900, 900-1050 kpc | 3.5, 2.4, 2.8, 4.0, 1.6, 1.3, 1.4 | not stated | dimensionless | 8 | we measured the overdensity factor around the Spiderweb galaxy of 3.5, 2.4, 2.8, 4.0, 1.6, 1.3 and 1.4 in radii of |
| 2D K-S probability that HAEs and DSFGs share a distribution | 0.084 | not stated | dimensionless | 9 | the probability of them being drawn from the same distribution is 0.084 |
| 2D K-S probability that DSFGs and CO emitters share a distribution | 62.3% | not stated | percent | 9 | ALMA-detected DSFGs and CO emitters have a rather high probability (62.3% |
| ALMA sources confirmed as CO emitters (of 43 in the COALAS footprint) | 13 | not stated | sources | 9 | We find that 13 ALMA sources are confirmed as CO emitters by cross-matching these two populations |
| DSFGs in main catalogue that are HAEs within 1 arcsec | 10 of 47 (20 percent) | not stated | sources | 9 | 10 of 47 DSFGs in our main catalog are HAEs within a matching radius of 1 arcsec |
| dust-based gas masses of ALMA sources | 2.0-27.3e10 | not stated | Msun | 10 | we derive the gas masses of our ALMA sources to be $2.0-27.3\times10^{10}\,{\rm M}_{\odot}$ |
| SFR density over 120 cMpc line of sight | 1.78 | 0.35 | Msun yr^-1 cMpc^-3 | 11 | we obtain an SFR density to be $1.78\pm0.35\,{\rm M}_\odot\,\rm{yr}^{-1}\rm{cMpc}^{-3}$ |
| SFR density in a 2 Mpc sphere | 58.21 | 11.41 | Msun yr^-1 cMpc^-3 | 11 | we obtain a SFR density to be $58.21\pm11.41\,{\rm M}_\odot\,\rm{yr}^{-1}\rm{cMpc}^{-3}$ |
| total SFR of groups SW-GE1 and SW-GE2 | 2688 and 806 | 385 and 121 | Msun yr^-1 | 11 | We calculate the total SFR of these two groups to be $2688\pm385$ and $806\pm121\,{\rm M}_\odot\,\rm{yr}^{-1}$. |
| depletion time of ALMA-detected DSFGs | 340 | 48 | Myr | 11 | the depletion time is estimated to be $340\pm48$ Myr |
| multiplicity fraction of LABOCA sources | ~57% | not stated | percent | 12 | indicating a multiplicity fraction of $\sim$57% |
| median ratio of summed ALMA flux to single-dish flux (LABOCA; AzTEC) | 0.62; 0.60 | 0.12; 0.04 | dimensionless | 12 | The median ratios for the LABOCA sources and AzTEC sources are $0.62\pm0.12$ and $0.60\pm0.04$ |

## Qualitative findings

- Overdensity of ALMA sources is prominent in the eastern Fields 1-3; Fields 4-6 are close to general fields  
  > "The overdensity is prominent in the eastern part of the Spiderweb protocluster (from Field 1 to Field 3)" (5.1 Overdensity of DSFGs detected by ALMA)
- Protocluster centre shows a relative lack of DSFGs; DSFGs sit on the outskirts  
  > "Contrarily, the protocluster center shows a relative lack of DSFGs and is believed to be nearly virialized" (5.3 DSFGs related to the evolution of the Spiderweb protocluster)
- About half of the CO emitters with ALMA counterparts are extended gas reservoirs  
  > "seven (6 robust, 1 tentative) out of the 13 CO emitters with ALMA counterparts are extended molecular gas reservoirs" (5.2 Spatial correlation between different populations)

## Claim tuples

- H: Is the DSFG population in the Spiderweb protocluster overdense compared with general fields? | E: ALMA 1.2 mm mosaic number counts corrected for purity and completeness, compared with ALMACAL and GOODS-ALMA field counts | R: Cumulative counts about 2 times general fields (1.77 +/- 0.45 at 0.25 mJy), higher in Fields 1-3 | F: DSFG number counts in the protocluster are overall two times those of general fields | **supported**
- H: Are ALMA DSFGs drawn from the same spatial distribution as CO emitters but not as HAEs? | E: 5th-neighbour density maps, CDFs vs distance to the central galaxy and 2D K-S tests | R: K-S probability 0.623 for DSFG vs CO, 0.084 for HAE vs DSFG (below 2 sigma) | F: DSFGs likely share the CO emitter distribution and are plausibly distinct from HAEs, but the HAE difference is not statistically firm | **partially**
- H: Are molecular gas masses from dust measurements consistent with those from CO(1-0)? | E: Dust-luminosity gas masses compared with CO-based masses for 13 matched sources using alpha_CO of 0.8, 3.6 and per-source values | R: Dust and CO masses disagree for alpha_CO = 0.8 and agree only with large scatter for alpha_CO = 3.6 | F: Dust-based molecular gas masses should be used with caution | **supported**
- H: Do two extreme concentrations of ALMA sources trace infalling galaxy groups? | E: Counted DSFGs within 400 kpc around DKB01/DKB03 and DKB02 and compared to general-field density | R: Eight and six DSFGs within 400 kpc, excess above 12 times general fields; SW-GE2 has only half its sources above 5 sigma | F: Two groups (SW-GE1, SW-GE2) are tentatively identified; SW-GE1 is better supported than SW-GE2 | **partially**
- H: Is the multiplicity of single-dish sources higher in the protocluster than in general fields? | E: Matched LABOCA and AzTEC sources to ALMA detections | R: All 7 LABOCA sources detected, 4 multiple (~57%); 4 of 5 AzTEC sources multiple (80%); ALMA recovers about 60 percent of single-dish flux | F: Multiplicity of single-dish DSFGs is higher than in the field, supporting the overdensity | **supported**

## Reasoning

- Why this data: contiguous ALMA mapping is needed to study individual DSFGs and their link to large-scale structure in SMG overdensities  
  > "Therefore, ALMA (contiguous) mapping of these SMG overdensities is indispensable to study DSFGs individually and their connection with the surrounding large-scale structure." (1 Introduction)
- Why this method: the 'fixed' noise method is more representative and conservative than local noise maps whose scale depends on arbitrary box choices  
  > "The 1$\sigma$ noise with the “fixed” method is more representative as it is directly derived from the standard deviation of the Gaussian profile drawn in the flux distribution." (3.2 Source extraction)
- Alternative: 'Individual' sliding-box noise maps gave 54, 48 and 49 sources (SEP, AEGEAN, SoFiA) instead of the common 47; those extra sources became tentative, not main-catalogue sources  
  > "Interestingly, all three codes produced the same catalog containing 47 detections when we use the 1$\sigma$ noise values from the “fixed” method." (3.2 Source extraction)
- Alternative: Aperture photometry fluxes were tested as an alternative to Gaussian fits for the counts and gave consistent results  
  > "We also tested the analysis with aperture photometry and obtained consistent results." (4.1 Completeness and flux boosting)
- How they decided it was enough: above 5 sigma sources treated as real; the analysis was repeated with >5 sigma sources only to test robustness  
  > "Sources above 5$\sigma$ are all considered to be real" (3.2 Source extraction)
- Limitation (authors): Tentative sources are not used for counts and must be treated with caution  
  > "The tentative sources in the supplementary catalog must be taken with caution and will not be used in the following number counts analysis." (3.2 Source extraction)
- Limitation (authors): 2D K-S test uses sky positions only, so redshift-space correlation is not tested  
  > "The 2D K-S test are solely based on the sky positions and thus cannot determine the correlation between DSFGs and CO emitters in redshift space." (5.2 Spatial correlation between different populations)
- Limitation (authors): SFR densities depend strongly on the assumed cosmic volume  
  > "We emphasize that due to the uncertainty of the calculations of the cosmic volume, one should take the cosmic SFR density with caution." (5.2 Spatial correlation between different populations)
- Limitation (authors): ALMA may miss flux because of Briggs weighting and high resolution  
  > "but may still miss some fluxes due to the weighing scheme and the high resolution" (5.4 Comparison between ALMA and single-dish observations)
- Caveat (inferred, ours): Membership of most ALMA sources is not confirmed spectroscopically, so source counts include unrelated foreground/background galaxies along the line of sight
- Caveat (inferred, ours): Overdensity depends on the chosen general-field baseline (1.8 vs 2.08 for different baselines) and on a flux conversion that assumes one SED at z=2.2
- Caveat (inferred, ours): Sources between 4 and 5 sigma include about five spurious detections by the authors' own purity estimate
- Caveat (inferred, ours): Completeness assumes point-like sources, but several sources look extended and the Gaussian fluxes of some are much larger than aperture fluxes
- Caveat (inferred, ours): The printed gas-to-dust ratio of 105 and the choice of alpha_CO per source drive the dust-versus-CO gas mass conclusion
- Caveat (inferred, ours): Two-dimensional K-S results are below 2 sigma for HAE comparisons, so the HAE-DSFG distinction is weak

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: calibration used archive-provided scripts  
  > "The visibilities were calibrated and flagged using the scripts provided by the ALMA archive." (2.2 Data reduction)
- Missing: CASA version and full tclean parameter set (mask, niter, threshold, image size, phase centres)
- Missing: Public data status is not stated in the paper
- Missing: Machine-readable catalogues or scripts are not stated as released
- Missing: Literature catalogues (HAEs, CO emitters, LABOCA/AzTEC, general-field counts) must be gathered from other papers
- Missing: Bin definitions and correction details for the differential counts
- Data volume (inferred): About 19 execution blocks of a 128-channel x 4-SPW mosaic dataset; raw measurement sets likely several hundred GB to ~1 TB, calibrated continuum images a few GB
- Score (inferred): 3/5, Project code, array configs, spectral setup, robust, tclean mode, noise method, source-finder parameters and the Monte Carlo recipe are given and the catalogue is tabulated, but the CASA version, clean masks/thresholds, channel selection and several literature inputs are missing.
- Rediscovery candidate: yes, The paper does not state that the data are public, but Cycle 8 data from a named project code are likely out of the proprietary period; the recipe (continuum imaging, noise, extraction, Monte Carlo counts) is mostly complete and results are tabulated numerically.

## Links

- Method: (cite: Chen2023a) (Gaussian fitting, aperture photometry and completeness/purity approach followed here)
- Method: (cite: Gomez2022) (Completeness simulation with point-like sources, effective area and general-field counts)
- Method: (cite: Umehata2018) (ADF22 protocluster counts, 1.1-to-1.2 mm conversion and single-dish comparison approach)
- Method: (cite: Scoville2023) (Gas mass from Rayleigh-Jeans dust luminosity)
- Companion: (cite: Jin2021) (COALAS CO(1-0) emitter catalogue used for matching)
- Companion: (cite: Chen2024) (Extended CO gas reservoirs around Spiderweb galaxies)
- Companion: (cite: Dannerbauer2014) (LABOCA SMGs in the Spiderweb field)
- Companion: (cite: Shimakawa2018b) (HAE catalogue and density map of the Spiderweb protocluster)
- Related: ASW2DF
- Related: COALAS
- Related: ADF22 (SSA22 protocluster)
- Related: GOODS-ALMA 2.0
- Related: ALMACAL
- Related: MQN01 protocluster
- Related: A3COSMOS

## Checks

```json
{
 "quotes": 164,
 "quotes_ok": 164,
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
  "facts": 138,
  "stated": 108,
  "rate": 0.783
 },
 "evidence_ok": true
}
```
