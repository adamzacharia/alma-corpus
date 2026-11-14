# ALMAGAL: III. Compact source catalog: Fragmentation statistics and physical evolution of the core population

`2025A&A...696A.151C` | Astronomy and Astrophysics 2025 | first author: Coletta, A. | arXiv: 2503.05663 | DOI: 10.1051/0004-6361/202452706

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: star_formation, milky_way_ism
- Question: How do 1013 massive dense Galactic clumps fragment into compact cores, and how do core properties and the core mass function (CMF) vary with clump evolutionary stage (L/M)?  
  > "We characterize and discuss the revealed fragmentation properties and the photometric and estimated physical parameters of the core population." (abstract); "We evaluated the variation in the core mass function (CMF) with evolution as traced by the clump" (abstract)
- Target **ALMAGAL clump sample (1013 massive dense clumps, fields named AGlll.llll+bb.bbbb)**: coordinates _not stated_; z/distance heliocentric distances of about 2-8 kpc (near sample about 2-4.7 kpc, far sample about 4.7-8 kpc)  
  > "The sample covers a broad range of heliocentric distances" (2.1 The ALMAGAL clump sample); "mainly produced by the refinement of clump distances performed between the time of the proposal preparation and the present work" (2.3 Continuum maps properties); distance from clump distances from the ALMAGAL survey paper (Molinari+25), refined after proposal preparation; relative error on distance about 10% on average  
  > "The sample covers a broad range of heliocentric distances" (2.1 The ALMAGAL clump sample); "mainly produced by the refinement of clump distances performed between the time of the proposal preparation and the present work" (2.3 Continuum maps properties)

## Data provenance

- ALMA projects: 2019.1.00195.L
- bands: Band 6, about 1.38 mm (about 217 GHz)  
  > "in the spectral Band 6 at around 1.38 mm" (2.2 ALMA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ACA-7m (7M) plus 12m array  
  > "ACA-7m + C-2 + C-5" (Table 1 (observing setups)); "ACA-7m + C-3 + C-6" (Table 1 (observing setups))
- configurations: Near sample (535 fields): 7M + C-2 + C-5; far sample (478 fields): 7M + C-3 + C-6  
  > "plus the C-2 and C-5 configurations of the" (2.2 ALMA observations); "were observed using the 7M array plus the C-3 and C-6 configurations of the" (2.2 ALMA observations)
- baselines: Compact configs (C-2, C-3, TM2) baselines up to 500 m; extended configs (C-5, C-6, TM1) up to 2.5 km; minimum baseline 9 m (7M)  
  > "are the compact configurations of the 12m array (baselines up to 500 m)" (2.2 ALMA observations); "featuring the longest baselines, up to 2.5 km" (2.2 ALMA observations); "The maximum recoverable scale (MRS) is set by the minimum baseline length (9 m, given by the 7M array)" (2.2 ALMA observations)
- angular resolution: Maximum angular resolution about 0.15 arcsec; beam bimodal, peaking at about 0.2 arcsec (far) and 0.4 arcsec (near); median linear resolution 1400 au (about 800-2000 au)  
  > "the distribution is clearly bimodal, peaking at" (2.3 Continuum maps properties); "Overall, the maximum angular resolution, achieved through the addition of the most extended baselines configurations (TM1) to the combined data" (2.3 Continuum maps properties); "with a median of 1400 au" (2.3 Continuum maps properties)
- max recoverable scale: about 29 arcsec, set by the 9 m minimum baseline (about 0.5 pc near, about 0.8 pc far)  
  > "The maximum recoverable scale (MRS) is set by the minimum baseline length (9 m, given by the 7M array)" (2.2 ALMA observations)
- sensitivity: map rms mostly about 0.05-0.2 mJy/beam; 1 sigma flux sensitivity about 0.05 mJy/beam (requested about 0.1 mJy/beam)  
  > "satisfying (and actually improving) the requested sensitivity of" (2.3 Continuum maps properties)
- time on source: 1 to 4 minutes per target  
  > "The observing time for each target ranged from 1 to 4 minutes." (2.2 ALMA observations)
- observing dates: October 2019 to March 2020, and March 2021 to July 2022  
  > "were conducted from October 2019 to March 2020, and from March 2021 to July 2022" (2.2 ALMA observations)
- pi or archival as stated: ALMA Cycle 7 Large Program, PIs Molinari, Battersby, Ho, Schilke  
  > "Large Program (2019.1.00195.L, PIs: Sergio Molinari, Cara Battersby, Paul Ho, Peter Schilke)" (1 Introduction)
- Other facility **Hi-GAL (Herschel)**: Parent survey of 915 of the ALMAGAL clump targets  
  > "Herschel Infrared Galactic Plane Survey (Hi-GAL," (2.1 The ALMAGAL clump sample)
- Other facility **RMS survey**: Parent survey of 98 of the ALMAGAL clump targets  
  > "Red MSX Source survey (RMS," (2.1 The ALMAGAL clump sample)
- Other facility **CORNISH and CORNISH-South (VLA)**: 5 GHz (6 cm) radio continuum maps used to flag cores potentially contaminated by free-free emission  
  > "providing radio continuum maps at 5 GHz (or 6 cm)" (Appendix: free-free emission contamination)
- External data: Clump distances, L/M and other clump-level parameters of the ALMAGAL sample (not re-derived in this paper)  
  > "Instead, we chose to base our assumptions on the properties of the respective hosting clumps" (5.2.1 Core temperature model) [from (cite: Molinari+25); Elia et al. in prep.]
- External data: Calibration of clump L/M with CH3C2H rotational temperature used to build the core temperature model  
  > "on which we based our core temperature model" (Appendix: core temperature model) [from (cite: Molinari+16)]
- External data: Alternative core temperature model proportional to core flux via a power law (gamma = 0.238), used as a robustness test  
  > "we first applied an alternative model taken from" (Appendix: resolution and temperature tests) [from (cite: Sadaghiani+20)]
- External data: Dust absorption coefficient kappa_1.3 = 0.9 cm2/g (coagulated MRN grains, thin ice mantles)  
  > "is the dust absorption coefficient at 1.3 mm wavelength, describing the opacity of dust grains with thin ice mantles" (5.2 Core masses) [from (cite: Ossenkopf&Henning94)]
- External data: Mean molecular mass of 2.8 m_H for the volume density  
  > "is the mean molecular mass, for which we assume" (5.3 Mass-size relation, mass surface density and molecular volume density) [from (cite: Kauffmann+08)]
- External data: CORNISH and CORNISH-South 5 GHz radio continuum maps matched to ALMAGAL fields  
  > "providing radio continuum maps at 5 GHz (or 6 cm)" (Appendix: free-free emission contamination) [from (cite: Purcell+08; Hoare+12); (cite: Irabor+23)]
- Simulation/model as data: Synthetic 2D elliptical Gaussian sources injected into real ALMAGAL maps to test completeness and photometric accuracy (60 fields, about 4000 sources per noise group)  
  > "We then injected synthetic 2D elliptical Gaussian sources (20 per field) at multiple (from 10 to 15) integrated flux levels into 60 selected ALMAGAL fields" (3.3 Flux completeness and photometric accuracy)
- Simulation/model as data: 1000 Monte Carlo realizations of core masses with random temperatures to propagate temperature uncertainty into the CMF  
  > "we performed a series of 1000 Monte Carlo (MC) simulations of masses of the whole population of extracted cores" (6 CMF variation with evolution)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Detection on non-primary-beam-corrected images; photometric fit on the primary-beam-corrected image  
  > "The detection procedure uses the non-primary beam-corrected intensity images" (3.2 Source detection and photometry pipeline); "the fit is executed on the primary beam-corrected image using a total of nine parameters" (3.2 Source detection and photometry pipeline)
- array combination: 7M, TM2 and TM1 data combined into continuum maps (7M+TM2+TM1) with CASA; details in Sanchez-Monge+25  
  > "Data from the different observational configurations employed were combined to produce continuum maps (called 7M+TM2+TM1 images)" (2.3 Continuum maps properties)
- smoothing: _not stated_
- final beam: Circularized beam FWHM (geometric mean of major and minor axes); bimodal about 0.2 arcsec (far) and 0.4 arcsec (near); median linear size 1400 au  
  > "the distribution is clearly bimodal, peaking at" (2.3 Continuum maps properties); "with a median of 1400 au" (2.3 Continuum maps properties)
- final rms: rms = standard deviation of the residual image with bright emission masked (header keyword AGSTDREM); mostly about 0.05-0.2 mJy/beam  
  > "estimated as the standard deviation of the residual image once masked to exclude regions with significantly bright emission in the final intensity image" (2.3 Continuum maps properties)

### Inherited from earlier work

- Full details of the ALMAGAL observations and survey design  
  > "Full details of the ALMAGAL observations can be found in" (2.2 ALMA observations) [from (cite: Molinari+25) and (cite: Sanchez+25)]
- Data acquisition, processing pipeline and calibration/imaging of the continuum maps  
  > "A fully detailed technical description of the ALMAGAL data acquisition and processing pipeline, and characterization of the obtained continuum maps can be found in" (2.3 Continuum maps properties) [from (cite: Sanchez+25)]
- Map rms definition via the AGSTDREM header keyword  
  > "corresponds to the AGSTDREM keyword stored in the header of the FITS images of ALMAGAL targets" (2.3 Continuum maps properties) [from (cite: Sanchez+25)]
- Refinement of clump distances after proposal preparation  
  > "mainly produced by the refinement of clump distances performed between the time of the proposal preparation and the present work" (2.3 Continuum maps properties) [from (cite: Molinari+25) and Benedettini et al. in prep.]
- Original CuTEx algorithm, further developed in this work  
  > "A detailed characterization and operational description of the original version of" (3.2 Source detection and photometry pipeline) [from (cite: Molinari+11)]
- Optically thin dust mass formula  
  > "the core mass has been estimated assuming optically thin dust continuum emission through the formula" (5.2 Core masses) [from (cite: Kainulainen+17)]
- Dust opacity choice kept for consistency with other interferometric fragmentation studies  
  > "This value allows for a consistent comparison with the results of several other interferometric studies of fragmentation at core scales" (5.2.3 Uncertainties and biases on core mass estimation) [from (cite: Ossenkopf&Henning94); (cite: Palau+13); (cite: Beuther+18); (cite: Sanhueza+17); (cite: Sanhueza+19); (cite: Svoboda+19); (cite: Morii+23)]
- Core temperature model built on the L/M versus CH3C2H temperature calibration  
  > "on which we based our core temperature model" (Appendix: core temperature model) [from (cite: Molinari+16)]
- Alternative temperature model for the CMF robustness test  
  > "we first applied an alternative model taken from" (Appendix: resolution and temperature tests) [from (cite: Sadaghiani+20)]

### Not stated but needed to reproduce (our reading)

- The ALMAGAL 7M+TM2+TM1 continuum FITS images and their CASA version, tclean settings (weighting/robust, cell size, image size, deconvolver, masks, self-calibration) are only in Sanchez-Monge+25, not here.
- The modified CuTEx version used (new derivative filter for about 6 pixels per beam) and its full parameter set; the paper gives only thresholds (3 sigma curvature, 4 sigma then 5 sigma peak) and fit constraints, and no code release is stated.
- Clump table (distances, L/M, luminosities, masses, evolutionary stage) from Molinari+25 and Elia et al. in prep. needed to assign temperatures and masses.
- Exact curvature filter kernel and handling of edge or primary-beam cutoff (fields restricted to primary beam value of 0.6 only stated for injections).
- Distribution used for the random temperature draws in the Monte Carlo CMF realizations (uniform assumed but not stated) and random seeds.
- Binning, weighting and uncertainty treatment for the M-R power-law fit (alpha = 2.612) and for the median M_max/M_min versus L/M bins.
- Which five clumps were re-tuned and the tuned parameters beyond the 6 sigma / 8 sigma flux cuts.
- Selection of the 60 injection fields and 10 comparison fields (names not listed).

## Analysis recipe

1. **obtain combined continuum maps and map rms**: Combine 7M, TM2 and TM1 data into 7M+TM2+TM1 continuum maps with CASA (pipeline in Sanchez-Monge+25); rms from residual image  
  > "Data from the different observational configurations employed were combined to produce continuum maps (called 7M+TM2+TM1 images)" (2.3 Continuum maps properties)
   - software: CASA
   - parameter: rms = standard deviation of the residual image masked to exclude bright emission (AGSTDREM keyword)  
  > "estimated as the standard deviation of the residual image once masked to exclude regions with significantly bright emission in the final intensity image" (2.3 Continuum maps properties)
   - fitting: _not stated_
   - validation: _not stated_
2. **detect compact sources with CuTEx**: CuTEx detection on curvature images from double differentiation of the non-primary-beam-corrected intensity image in four directions; adjacent pixels above a curvature threshold grouped as candidates  
  > "obtained with a double differentiation of the intensity image in four different directions" (3.2 Source detection and photometry pipeline); "The detection procedure uses the non-primary beam-corrected intensity images" (3.2 Source detection and photometry pipeline)
   - software: CuTEx
   - parameter: curvature threshold 3 times the rms of the curvature image, exceeded in all four directions  
  > "Adjacent pixels exceeding a curvature threshold (in our case three times the rms of the curvature image" (3.2 Source detection and photometry pipeline); "The threshold must be exceeded over all four differentiation directions" (3.2 Source detection and photometry pipeline)
   - parameter: first filtering stage: peak flux above 4 times the intensity map rms  
  > "is higher than four times the intensity map rms" (3.2 Source detection and photometry pipeline)
   - assumption: Cores are dense, compact, roundish sources with centrally peaked brightness profile at about 1400 au scales  
  > "Here, we define as cores the dense, compact sources of roundish (or slightly elliptical) shape with a centrally peaked brightness profile" (3.1 Source extraction strategy)
   - fitting: _not stated_
   - validation: Synthetic source injection compared CuTEx with astrodendro and hyper; visual inspection of every test run  
  > "we injected synthetic sources into selected ALMAGAL maps and conducted source extraction runs with" (3.1 Source extraction strategy); "was evaluated through a thorough visual inspection" (3.2 Source detection and photometry pipeline)
3. **measure core photometry and apply final S/N cut**: Fit each source with a 2D elliptical Gaussian plus an inclined planar background, simultaneously with neighbours, on the primary-beam-corrected image; integrated flux F_INT = 2 pi sigma_a sigma_b F_PEAK / Omega_beam; final cut F_PEAK > 5 sigma_rms  
  > "each source is simultaneously fit with a plane of variable inclination degree and direction" (3.2 Source detection and photometry pipeline); "is higher than five times the map rms" (3.2 Source detection and photometry pipeline)
   - software: CuTEx
   - parameter: neighbours fitted within a radius of 0.75 times the guessed source size  
  > "within a given radius, set to 0.75 times the guessed source size" (3.2 Source detection and photometry pipeline)
   - parameter: fit over an image area three times the beam width around the source; nine fitted parameters (six Gaussian, three plane)  
  > "The fit is performed over an image area that is three times the beam width around the source position" (3.2 Source detection and photometry pipeline); "the fit is executed on the primary beam-corrected image using a total of nine parameters" (3.2 Source detection and photometry pipeline)
   - parameter: source size free within 0.5-1.5 times the initial guess, with lower limit 0.95 times the map beam minor axis  
  > "the source size estimated by the fit is left free to vary within 0.5-1.5 times the initial guess" (3.2 Source detection and photometry pipeline); "assuming a defined lower limit of 0.95 times the map beam size" (3.2 Source detection and photometry pipeline)
   - parameter: five fields with cleaning artifacts needed dedicated tuning (6 sigma or 8 sigma flux cuts)  
  > "required a dedicated tuning of the extraction parameters in order to optimize the robustness of the compact source extraction" (4.1 ALMAGAL catalog of compact sources)
   - assumption: Source brightness profile is a 2D elliptical Gaussian with variable size and orientation  
  > "is based on the assumption that the source brightness profile can be represented by a 2D elliptical Gaussian with variable parameters, including size and orientation" (3.2 Source detection and photometry pipeline)
   - fitting: Simultaneous least-squares-type multi-Gaussian plus plane fit; optimiser and likelihood not stated  
  > "a detected source is simultaneously fit together with its neighbors (through a multiple Gaussians fit)" (3.2 Source detection and photometry pipeline)
   - validation: Injection tests; flux and size recovery within about 20%  
  > "Recovered integrated fluxes are overall consistent with the simulations, presenting average values correct within" (Appendix: flux completeness and photometric accuracy)
4. **estimate flux completeness and photometric accuracy**: Inject synthetic Gaussians into 60 real fields split into three rms groups, rerun CuTEx with the same parameters, match to truth tables within 2 pixels, define completeness as the 90% detection level  
  > "We then injected synthetic 2D elliptical Gaussian sources (20 per field) at multiple (from 10 to 15) integrated flux levels into 60 selected ALMAGAL fields" (3.3 Flux completeness and photometric accuracy); "adopting a matching radius of 2 pixels (about one-third of the map beam size)" (Appendix: flux completeness and photometric accuracy)
   - software: CuTEx, IDL
   - parameter: Completeness fluxes 0.58, 0.94 and 2.05 mJy for Groups 1, 2, 3 (rms < 0.06, 0.06-0.1, > 0.1 mJy/beam)  
  > "Completeness flux is 0.58 mJy for Group 1 (low noise fields, left panel), 0.94 mJy for Group 2 (medium noise fields, mid panel), and 2.05 mJy for Group 3" (3.3 Flux completeness and photometric accuracy)
   - assumption: Group 2 (76% of fields) completeness adopted as the overall reference  
  > "We decided to adopt the completeness limit computed for Group 2 targets as overall reference" (4.3.1 Integrated fluxes)
   - fitting: _not stated_
   - validation: Recovered fluxes and sizes consistent with injected values  
  > "Recovered integrated fluxes are overall consistent with the simulations, presenting average values correct within" (Appendix: flux completeness and photometric accuracy)
5. **derive core physical sizes**: Physical diameter D_core (au) = circularized FWHM (arcsec) x clump distance (pc), non-beam-deconvolved  
  > "its corresponding physical size (i.e., diameter) can be computed as" (5.1 Core physical sizes); "The non-deconvolved core physical diameter has been derived from the circularized FWHM of the fitted source ellipse" (5.4 Estimated physical parameters of the cores)
   - parameter: circularized FWHM = geometric mean of fitted ellipse axes; d is clump heliocentric distance  
  > "was computed as the geometric mean of the FWHM of the fitted source ellipse" (4.3.2 Angular sizes); "where d is the clump heliocentric distance." (5.1 Core physical sizes)
   - fitting: _not stated_
   - validation: Size uncertainty about 20% from injected sources; distance error about 10%  
  > "as deduced by comparing the angular sizes of a large population of synthetic sources measured by" (5.1 Core physical sizes)
6. **assign core temperatures from clump L/M**: Three-regime clump-L/M temperature model: 20 K (L/M <= 1), 35 K (1 < L/M <= 10), T = 21.1 (L/M)^0.22 K (L/M > 10)  
  > "i) 20 K to cores belonging to less evolved targets" (5.2.1 Core temperature model); "ii) 35 K to core pertaining to intermediate sources" (5.2.1 Core temperature model); "scaled with a proportionality factor (21.1) to best fit to the observed points in the" (5.2.1 Core temperature model)
   - parameter: 35 K adopted for the 1-10 L/M group, fitted to the Molinari+16 points  
  > "we took 35 K as the temperature value fitting the points within" (Appendix: core temperature model)
   - assumption: All cores in a clump share the temperature set by the clump evolutionary stage; direct core-level temperatures not available  
  > "Without such core-level estimates, educated assumptions on dust temperature for the cores must be made." (5.2.1 Core temperature model)
   - fitting: _not stated_
   - validation: Compared with temperature ranges used in other ALMA surveys; temperature range varied in Monte Carlo and alternative models  
  > "Such values are consistent with those used in other recent ALMA surveys" (5.2.1 Core temperature model)
7. **compute core masses and their uncertainties**: M_core = R_gd F_INT d^2 / (B_nu(T) kappa_1.3), optically thin dust, T from step 6; mass uncertainty explored with temperature ranges 10-40 K, 20-60 K and T_core +/- 30 K  
  > "the core mass has been estimated assuming optically thin dust continuum emission through the formula" (5.2 Core masses); "we set three ranges of temperatures around the reference values used for the three groups of sources described above" (5.2.3 Uncertainties and biases on core mass estimation)
   - parameter: gas-to-dust ratio 100  
  > "is the widely assumed gas-to-dust mass ratio" (5.2 Core masses)
   - parameter: kappa_1.3 = 0.9 cm2/g  
  > "is the dust absorption coefficient at 1.3 mm wavelength, describing the opacity of dust grains with thin ice mantles" (5.2 Core masses)
   - assumption: Optically thin emission; gas-to-dust 100; MRN grains with thin ice mantles at gas densities around 1e6 cm-3  
  > "We assumed a widely used gas-to-dust mass ratio" (5.2.3 Uncertainties and biases on core mass estimation)
   - fitting: _not stated_
   - validation: Mass sensitivity and completeness derived from the flux completeness limits at median T = 35 K  
  > "Using the median temperature of 35 K and an average distance of 4.5 kpc" (5.2.4 Mass sensitivity and completeness)
8. **derive surface density, volume density and mass-size relation**: Surface density Sigma = M/(pi R^2) and volume density n(H2) = M/(m_bar 4 pi R^3/3) assuming spherical cores; power-law fit M proportional to R^alpha to the mass-radius data  
  > "we computed the average mass surface density of the cores assuming a spherical shape as" (5.3 Mass-size relation, mass surface density and molecular volume density); "The gas volume density of the cores was also estimated assuming a spherical shape as" (5.3 Mass-size relation, mass surface density and molecular volume density)
   - parameter: mean molecular mass 2.8 m_H  
  > "is the mean molecular mass, for which we assume" (5.3 Mass-size relation, mass surface density and molecular volume density)
   - parameter: median M_core in bins of R_core shown as red points  
  > "Red points mark the median" (5.3 Mass-size relation, mass surface density and molecular volume density)
   - assumption: Spherical cores  
  > "we computed the average mass surface density of the cores assuming a spherical shape as" (5.3 Mass-size relation, mass surface density and molecular volume density)
   - fitting: power-law best fit M proportional to R^alpha; fitting method, weights and priors not stated  
  > "the best fit to the data points (solid blue line) corresponds to a power-law relation" (5.3 Mass-size relation, mass surface density and molecular volume density)
   - validation: Compared with literature mass-size slopes, surface densities and volume densities  
  > "Our estimates are roughly consistent with what found by" (5.3 Mass-size relation, mass surface density and molecular volume density)
9. **flag free-free contamination and select the CMF core sample**: Match cores to 7 sigma CORNISH / CORNISH-South 5 GHz contours; exclude matched cores, cores in clumps without radio maps, cores below mass completeness and cores in clumps farther than 9 kpc  
  > "We then generated flux contour levels at 3, 5, and 7 times the" (Appendix: free-free emission contamination); "allowing a tolerance of 1 radio continuum map pixel" (Appendix: free-free emission contamination); "First, we include here only cores with masses above the estimated average mass completeness limit for our catalog" (6.1 Core sample selection)
   - parameter: exclusion of cores positionally matched to strong radio emission  
  > "Moreover, we exclude cores that were positionally matched with strong radio continuum emission" (6.1 Core sample selection)
   - parameter: exclusion of distance outliers beyond 9 kpc  
  > "Lastly, we exclude cores from clumps farther than 9 kpc, i.e., distance outliers" (6.1 Core sample selection)
   - assumption: Positional coincidence with strong radio contours implies potential free-free flux contamination  
  > "since it is still possible that some of the positionally matched cores might actually not be significantly contaminated by the presence of local free-free emission" (Appendix: free-free emission contamination)
   - fitting: _not stated_
   - validation: _not stated_
10. **build CMFs per evolutionary group with Monte Carlo and robustness tests**: Inverse cumulative CMFs for the three L/M groups; 1000 Monte Carlo mass realizations with random temperatures in the Delta T range of each group  
  > "The CMF is shown and discussed in terms of inverse cumulative number density of objects." (6 CMF variation with evolution); "We assigned to each core a random temperature within the range" (6 CMF variation with evolution)
   - parameter: Monte Carlo: 1000 simulations of the whole core population  
  > "we performed a series of 1000 Monte Carlo (MC) simulations of masses of the whole population of extracted cores" (6 CMF variation with evolution)
   - assumption: Clump evolutionary stage (L/M) used as proxy for core evolution; CMF not fitted for slopes (power law only above about 3 Msun)  
  > "we find our CMFs to be reasonably consistent with a power law" (6.2 Evolutionary trend of the CMF)
   - fitting: No CMF slope fitting performed here  
  > "we do not focus on detailed computations of the CMF slopes" (6.2 Evolutionary trend of the CMF)
   - validation: Tests with 1000-2000 au resolution subsample, Sadaghiani+20 temperature model, and F_INT d^2 without temperature; near and far samples separately  
  > "we first applied an alternative model taken from" (Appendix: resolution and temperature tests); "Lastly, we considered a reduced version of the core mass formula" (6.2 Evolutionary trend of the CMF)
11. **analyse core mass growth and fragmentation versus evolution**: Median maximum and minimum core mass per clump in L/M bins; total mass in cores minus the most massive core versus the most massive core; number of fragments versus M_max  
  > "we report the median value of the maximum and the minimum core masses" (7.1 Core mass growth with evolution); "we report the total mass in cores within each clump minus the mass of the MMC, as a function of the latter." (7.1 Core mass growth with evolution); "we relate the number of detected fragments (cores) with" (7.2 Relation with clump fragmentation)
   - parameter: sample of 3973 cores, excluding all cores in clumps with any potentially free-free contaminated core, no mass completeness cut  
  > "the considered sample amounts to 3973 cores" (7 Core mass growth and fragmentation)
   - assumption: Clump L/M traces evolution; most massive core (MMC) mass growth interpreted as accretion with time  
  > "They show that, on average, the whole core population within a clump (or at least the majority of it) undergoes mass growth during evolution" (7.1 Core mass growth with evolution)
   - fitting: _not stated_
   - validation: N_frag trend confirmed using integrated fluxes instead of masses; compared with simulations of Bonnell+04 and Hennebelle+22  
  > "We also verified that the overall trend of" (7.2 Relation with clump fragmentation)

## Software

- **CASA** : Combining 7M, TM2 and TM1 data into the continuum maps  
  > "Data from the different observational configurations employed were combined to produce continuum maps (called 7M+TM2+TM1 images)" (2.3 Continuum maps properties)
- **CuTEx** not stated (modified version developed for this work): Compact source detection and photometry on the ALMAGAL continuum images  
  > "The identification and measurement of compact sources were performed on the processed continuum images with the" (3.2 Source detection and photometry pipeline)
- **astrodendro** : Comparison extractor on simulated maps, with an added local-background post-processing module  
  > "able to obtain a reliable estimate of the local background emission as the median intensity across a ring of pixels around each source" (Appendix: source extraction tests)
- **hyper** : Aperture photometry comparison test on the simulated maps  
  > "on the same set of simulated maps presented above, with the aim of testing the aperture photometry approach and its outcome compared to" (Appendix: aperture photometry tests with hyper)
- **IDL** : Routine that injects synthetic sources into real ALMAGAL continuum images  
  > "continuum images of real ALMAGAL fields with synthetic compact sources injected" (Appendix: source extraction tests)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of compact sources (cores) in the catalog | 6348 | not stated | cores | 3 | The ALMAGAL compact source catalog includes 6348 cores detected in 844 clumps |
| Clumps with at least one detection | 844 of 1013 (83%) | not stated | clumps | 3 | The ALMAGAL compact source catalog includes 6348 cores detected in 844 clumps |
| Cores per clump | range 1-49, median 5, mean 8 | not stated | cores per clump | 3 | with a number of cores per clump between 1 and 49 (median of 5) |
| Clumps with a single detection | 130 (15%) | not stated | clumps | 3 | showed only 1 detection |
| Median integrated flux of cores | 2 | about 20% (from injection tests) | mJy | 3 | The median of the integrated flux distribution is 2 mJy. |
| Median source FWHM relative to circularized beam | 1.15 | not stated | dimensionless | 3 | with a median value of 1.15 |
| Median source ellipticity | 0.25 | not stated | dimensionless | 3 | across the whole sample is 0.25 |
| Flux completeness (90% detection), Group 1 / 2 / 3 | 0.58 / 0.94 / 2.05 | not stated | mJy | 4 | Completeness flux is 0.58 mJy for Group 1 (low noise fields, left panel), 0.94 mJy for Group 2 (medium noise fields, mid panel), and 2.05 mJy for Group 3 |
| Median core diameter | 1700 | size uncertainty about 20% | au | 5 | (median of 1700 au) |
| Core temperature range and median from the L/M model | 20-81 K, median 35 K | not stated | K | 6 | Our model results in an overall range of core temperatures between 20 and 81 K, with a median value of the distribution of 35 K. |
| Core mass range | 0.002 to 345 | not stated | Msun | 7 | obtained core masses from 0.002 to 345 |
| Core mass mean and median | mean 1.5, median 0.4 | not stated | Msun | 7 | with a mean value of 1.5; and a median of 0.4 |
| Mass completeness limit (Group 2 reference) | 0.23 | not stated | Msun | 7 | (complete above 0.23 |
| Cores above 30 Msun | 28 cores in 25 clumps | not stated | cores | 7 | only in 28 cases (contained in 25 clumps) |
| Mass-radius power-law index alpha (M proportional to R^alpha) | 2.612 | 0.001 | dimensionless | 8 | the best fit to the data points (solid blue line) corresponds to a power-law relation; exhibiting a good correlation with the core radii |
| Core surface density mean and median | mean 4.5, median 1.7 | not stated | g cm-2 | 8 | with a mean value of 4.5 and a median of 1.7 g |
| Cores in the CMF analysis sample | 3324 (991, 1181, 1152 in the three L/M groups) | not stated | cores | 9 | we still end up with a large sample of 3324 cores |
| Cores positionally matched to strong radio continuum | 909 | not stated | cores | 9 | We identified 909 matched cores |
| Cores in the mass-growth sample | 3973 | not stated | cores | 11 | the considered sample amounts to 3973 cores |

## Qualitative findings

- The CMFs of the three L/M groups are clearly shifted and the high-mass tail flattens with evolution, beyond the temperature uncertainty  
  > "The CMF profiles for the three different evolutionary groups appear as clearly shifted relative to each other" (6.2 Evolutionary trend of the CMF); "In other words, more evolved clumps host more massive cores." (6.2 Evolutionary trend of the CMF)
- Near-sample clumps show more fragments than far ones; the difference disappears above the mass completeness limit  
  > "The total number of fragments detected in near sample targets is more than twice that found in far sample ones" (4.2.1 Sensitivity and physical effects on the observed fragmentation statistics)
- Minimum core mass per clump stays roughly constant with evolution while maximum core mass rises  
  > "The minimum core mass, instead, remains roughly constant on average around" (7.1 Core mass growth with evolution)
- A wider range of fragmentation degrees than other recent high-resolution surveys  
  > "Therefore, overall, in our clump sample we find a wider range of fragmentation degrees with respect to other similar recent high-resolution studies." (4.2 Detection and fragmentation statistics)

## Claim tuples

- H: Is the observed clump fragmentation (N_frag) driven by distance, resolution or mass sensitivity differences between the near and far setups? | E: Compared N_frag distributions of near and far subsamples, with and without a core-mass completeness cut | R: Near-sample clumps host more cores; near and far distributions become almost identical for cores above 0.23 Msun | F: Mass sensitivity is the predominant factor in the observed fragmentation statistics | **supported**
- H: Does the CMF shape change with clump evolutionary stage traced by L/M? | E: Cumulative CMFs for three L/M groups with temperature Monte Carlo, plus resolution, alternative-temperature and flux-only tests | R: Three CMFs are shifted with a flatter high-mass tail at later stages; trend holds in all tests | F: CMF shape is not constant but builds and flattens with evolution | **supported**
- H: Do all cores in a clump grow in mass with evolution, or only the most massive core? | E: Median M_max, M_min and total mass minus MMC versus clump L/M | R: M_max rises by about a factor 10 over about 3 dex in L/M; M_min stays near 0.2 Msun; total companion mass rises with MMC mass | F: All cores grow on average while a lower-mass population persists, possibly newly formed | **supported**
- H: Does the number of cores increase with the mass of the most massive core, i.e. does fragmentation continue during core growth? | E: Median N_frag versus M_core^max | R: N_frag rises from about 2 to about 12 up to about 10 Msun, then flattens, with limited statistics above that | F: Fragmentation and core growth coexist up to about 10 Msun; the later halt is not conclusive | **partially**
- H: Do the results favour clump-fed over core-fed high-mass star formation? | E: Combined interpretation of CMF evolution, core mass growth and N_frag trends | R: Cores form as low-mass seeds and gain mass with evolution while the clump keeps fragmenting | F: A clump-fed scenario is favoured | **supported**

## Reasoning

- Why this data: ALMAGAL combines a large, varied clump sample with high resolution and sensitivity in Band 6 for statistics of fragmentation  
  > "This is thanks to the size and variety of its target sample" (1 Introduction)
- Why this method: CuTEx chosen after tests because it detects compact sources and measures their flux better than astrodendro; a clump-L/M-based temperature model preferred over a single universal temperature  
  > "proved to be more efficient in detecting compact sources and accurately measuring their flux" (3.1 Source extraction strategy); "Assigning a single, universal temperature to the whole core sample would represent a too coarse and inaccurate" (5.2.1 Core temperature model)
- Alternative: astrodendro: no source-shape assumption and no background subtraction by default, so fluxes overestimated and detection rate lower in tests  
  > "performs a plain sum of the emission within the structure contour starting from the zero-level flux and does not include by default any background emission estimation and subtraction" (3.1 Source extraction strategy)
- Alternative: Lower S/N cut rejected because it gives many spurious detections  
  > "Based on thorough visual inspection, lower S/N would lead to a significant number of spurious detections." (3.2 Source detection and photometry pipeline)
- Alternative: hyper aperture photometry tested as an alternative on the same simulated maps  
  > "on the same set of simulated maps presented above, with the aim of testing the aperture photometry approach and its outcome compared to" (Appendix: aperture photometry tests with hyper)
- How they decided it was enough: 5 sigma peak-flux threshold chosen as conservative to avoid spurious detections, judged by visual inspection  
  > "We imposed this rather conservative S/N threshold to obtain a more robust and reliable core catalog" (3.2 Source detection and photometry pipeline)
- Limitation (authors): Temperature assumption per clump ignores individual core temperatures and is the largest mass uncertainty  
  > "Ultimately, a caveat has to be raised about these temperature assumptions." (5.2.1 Core temperature model); "Assigning the same temperature to all the cores within the same clump according to its properties, although representing a reasonably good approximation, inevitably ignores the distribution of temperatures" (6.2 Evolutionary trend of the CMF)
- Limitation (authors): Extraction is limited to compact sources and may miss more extended structures  
  > "we may be actually missing possible more extended structures which are instead revealed by other literature works" (5.1 Core physical sizes)
- Limitation (authors): Core diameters are not beam-deconvolved  
  > "The non-deconvolved core physical diameter has been derived from the circularized FWHM of the fitted source ellipse" (5.4 Estimated physical parameters of the cores)
- Limitation (authors): Free-free contamination may affect some cores in either direction  
  > "since it is still possible that some of the positionally matched cores might actually not be significantly contaminated by the presence of local free-free emission" (Appendix: free-free emission contamination)
- Limitation (authors): Mass accretion rates cannot be derived from these data  
  > "detailed estimations of mass accretion rates cannot be performed from these data" (7.1 Core mass growth with evolution)
- Caveat (inferred, ours): Clump L/M is used as an evolutionary clock for cores, but it is dominated by the brightest source and not independent of core mass (M_max versus L/M correlation partly built in).
- Caveat (inferred, ours): Temperature is tied to clump L/M, so mass trends with L/M are partly built in; flux-only test mitigates but also scales with d^2 and uses the same grouping.
- Caveat (inferred, ours): Single-pointing, filtered interferometric maps with different configurations for near and far samples; Gaussian-fit sizes are not deconvolved and are close to the beam, so mass-size slope and surface densities are resolution sensitive.
- Caveat (inferred, ours): CuTEx is a modified, not clearly released code, and the 5 sigma cut was tuned by visual inspection; the catalog is not independently reproducible from the paper alone.
- Caveat (inferred, ours): CMF slopes are not fitted and no statistical test (e.g. KS or slope uncertainty) is given for the shift between groups.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMAGAL continuum maps and the exact CASA imaging recipe (Sanchez-Monge+25)
- Missing: Modified CuTEx code and its parameter file
- Missing: Clump table with distances and L/M (Molinari+25)
- Missing: Monte Carlo temperature sampling details and seeds
- Missing: Binning and fit details for the mass-size relation and median trends
- Data volume (inferred): 1013 fields with 7M plus two 12m configurations in Band 6; raw MOUS data likely several TB to tens of TB, but only the continuum FITS images (about 35 arcsec FOV) are needed, of order GB; the catalog is at CDS.
- Score (inferred): 3/5, Catalog and many numeric results are stated, but the maps, modified CuTEx code, clump table and several fit settings come from other papers or are not given.
- Rediscovery candidate: no, The paper does not state that the data are public, the modified CuTEx code is not clearly released, and key inputs (continuum maps, clump L/M and distances) are only in companion papers.

## Links

- Method: Sanchez-Monge et al. 2025, A&A (accepted) (ALMAGAL data acquisition, processing pipeline and continuum map characterization)
- Method: Molinari et al. 2024/2025, A&A (submitted) (ALMAGAL survey description and sample)
- Method: Molinari et al. 2011, A&A, 530, A133 (Original CuTEx algorithm)
- Method: Molinari et al. 2016b, A&A, 591, A149 (CuTEx curvature filter and Hi-GAL usage)
- Method: Molinari et al. 2016a, ApJL, 826, L8 (L/M versus CH3C2H temperature calibration for the core temperature model)
- Method: Sadaghiani et al. 2020, A&A, 635, A2 (Alternative flux-dependent temperature model)
- Companion: Elia et al. in prep. (Clump-level properties and further core-clump correlations)
- Companion: Schisano et al. in prep. (Spatial distribution and mass segregation of the cores)
- Companion: Jones et al. in prep. (Core-level molecular-line temperature estimates)
- Companion: Nucara et al. in prep. (Comparison with numerical simulations matched to ALMAGAL)
- Companion: Wallace et al. in prep. (Hierarchical structure analysis (astrodendro))
- Related: ALMAGAL (2019.1.00195.L)
- Related: Hi-GAL
- Related: RMS survey
- Related: CORNISH and CORNISH-South
- Related: ASHES
- Related: ATOMS
- Related: SQUALO
- Related: TEMPO
- Related: ASSEMBLE
- Related: DIHCA
- Related: ALMA-IMF
- Related: CORE

## Checks

```json
{
 "quotes": 170,
 "quotes_ok": 170,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 19,
 "numeric_problems": 0,
 "fill": {
  "facts": 140,
  "stated": 107,
  "rate": 0.764
 },
 "evidence_ok": true
}
```
