# Precision Millimeter Astrometry of the α Centauri AB System

`2021AJ....162...14A` | The Astronomical Journal 2021 | first author: Akeson, Rachel | arXiv: 2104.10086 | DOI: 10.3847/1538-3881/abfaff

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: exoplanets, stellar_physics
- Question: Can ALMA Band 7 astrometry of alpha Cen A and B give precise absolute and differential positions to refine the orbit, masses, parallax and proper motion, and ultimately to search for planets in the AB system  
  > "Here we describe initial results from an ALMA program to search for planets in the" (abstract); "using differential astrometry at millimeter wavelengths" (abstract)
- Target **alpha Cen A**: coordinates AB barycentre ICRS J2019.5: RA 14:39:26.1413, Dec -60:49:53.875 (Table 9); individual ALMA positions in Table 2  
  > "At a distance of 1.34 pc," (Introduction); "14:39:26.1413 $\pm 1.50$ mas" (Table 9); "$-60$:49:53.875 $\pm 1.17$ mas" (Table 9); "The parallax determined in the present work ($\varpi = 750.81$ mas, $d=1.3319 \pm 0.0007$ pc)" (3.5 Prospects for Improved Stellar Properties); z/distance 1.34 pc (introduction); d = 1.3319 +/- 0.0007 pc from orbital parallax 750.81 mas  
  > "At a distance of 1.34 pc," (Introduction); "14:39:26.1413 $\pm 1.50$ mas" (Table 9); "$-60$:49:53.875 $\pm 1.17$ mas" (Table 9); "The parallax determined in the present work ($\varpi = 750.81$ mas, $d=1.3319 \pm 0.0007$ pc)" (3.5 Prospects for Improved Stellar Properties); distance from orbital parallax derived in this paper (RV plus differential astrometry fit)  
  > "At a distance of 1.34 pc," (Introduction); "14:39:26.1413 $\pm 1.50$ mas" (Table 9); "$-60$:49:53.875 $\pm 1.17$ mas" (Table 9); "The parallax determined in the present work ($\varpi = 750.81$ mas, $d=1.3319 \pm 0.0007$ pc)" (3.5 Prospects for Improved Stellar Properties)
- Target **alpha Cen B**: coordinates AB barycentre ICRS J2019.5: RA 14:39:26.1413, Dec -60:49:53.875 (Table 9); individual ALMA positions in Table 2  
  > "the angular sizes are 8.5 and 6.0 mas" (2.1 Observations); "14:39:26.1413 $\pm 1.50$ mas" (Table 9); "The parallax determined in the present work ($\varpi = 750.81$ mas, $d=1.3319 \pm 0.0007$ pc)" (3.5 Prospects for Improved Stellar Properties); z/distance same system as A: d = 1.3319 +/- 0.0007 pc  
  > "the angular sizes are 8.5 and 6.0 mas" (2.1 Observations); "14:39:26.1413 $\pm 1.50$ mas" (Table 9); "The parallax determined in the present work ($\varpi = 750.81$ mas, $d=1.3319 \pm 0.0007$ pc)" (3.5 Prospects for Improved Stellar Properties); distance from orbital parallax derived in this paper  
  > "the angular sizes are 8.5 and 6.0 mas" (2.1 Observations); "14:39:26.1413 $\pm 1.50$ mas" (Table 9); "The parallax determined in the present work ($\varpi = 750.81$ mas, $d=1.3319 \pm 0.0007$ pc)" (3.5 Prospects for Improved Stellar Properties)

## Data provenance

- ALMA projects: 2018.1.00557.S
- bands: Band 7 (343 GHz, 874 um)  
  > "we selected to observe in band 7" (2.1 Observations); "our ALMA wavelength (Band 7; 343 Ghz or 874" (2.4 Astrometric Noise due to Stellar Activity)
- frequencies and spectral setup: nominal continuum setup, four 1.9 GHz spectral windows at 336.5, 338.5, 348.5 and 350.5 GHz  
  > "using the nominal continuum setup of four 1.9 GHz spectral windows at frequencies 336.5, 338.5, 348.5 and 350.5 GHz" (2.1 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: config 6 (max baseline 2.5 km, one block), config 8 (8 km, two blocks), config 7 (3.6 km, two blocks); nine calibrated observations from five blocks  
  > "one block in configuration 6 (max baseline 2.5 km), two blocks in configuration 8 (max baseline 8 km) and two blocks in configuration 7 (max baseline 3.6 km)" (2.1 Observations)
- baselines: _not stated_
- angular resolution: 20 mas to 150 mas depending on configuration  
  > "The image resolution varied from 20 mas to 150 mas, depending on the configuration." (2.2 Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 70-min observations (about one hour each); alternating 18-s phase calibrator and 50-s target scans, about 55 cycles  
  > "we placed the phase center for each 70-min observation at the center of mass" (2.1 Observations); "the main science target portion of the observation of about 55 observing cycles, each with an 18-sec scan on the phase calibrator J1452-6502, alternating with a 50-sec scan on" (2.1 Observations)
- observing dates: Cycle 6, 2018 October to 2019 August  
  > "in Cycle 6 between 2018 October and 2019 August at band 7" (2.1 Observations)
- pi or archival as stated: dedicated program requested by the authors in three configurations (not stated as archival)  
  > "Hence, observations were requested in three configurations, one in Fall 2018 and two in Summer 2019." (2.1 Observations)
- Other facility **ESO 3.6m HARPS**: 5184 RVs for A and 12383 for B used with differential astrometry in the orbit fit  
  > "Our final sample of RV measurements includes 5184 RV measurements for A and 12383 for B." (3.2.2 Radial Velocity Data); "ALMA, ESO:3.6m(HARPS)" (Facilities)
- Other facility **Hipparcos**: absolute positions of A and B at 1991.25 (new reduction)  
  > "and 1 from Hipparcos (cite: vanLeeuwen07) UT = 1991-04-02T13:30:00.000" (3.2.1 Astrometry Data)
- Other facility **Nobeyama Radio Interferometer (17 GHz solar maps)**: daily solar maps used to estimate centroid jitter of free-free emission  
  > "taken daily by the Nobeyama Radio Interferometer (cite: Shibasaki2013)" (2.4 Astrometric Noise due to Stellar Activity)
- Other facility **Archival visual/interferometric differential astrometry of the AB pair**: differential astrometry from 1940 onward combined with the ALMA separations  
  > "of the AB pair (cite: Hart01) starting in the year 1940 (one full 80 yr orbit as of the year 2020)" (3.2.1 Astrometry Data)
- External data: Hipparcos absolute positions of A and B (1991-04-02)  
  > "and 1 from Hipparcos (cite: vanLeeuwen07) UT = 1991-04-02T13:30:00.000" (3.2.1 Astrometry Data) [from van Leeuwen 2007 (cite: vanLeeuwen07)]
- External data: archival differential astrometry of the AB pair from 1940 onward  
  > "of the AB pair (cite: Hart01) starting in the year 1940 (one full 80 yr orbit as of the year 2020)" (3.2.1 Astrometry Data) [from Hartkopf et al. 2001 (cite: Hart01)]
- External data: earlier ALMA observations of alpha Cen reused only for the differential astrometry  
  > "We do, however, use these data as part of the differential astrometric data." (3.2.1 Astrometry Data) [from Liseau et al. 2015, 2016 (cite: Liseau2015; Liseau2016)]
- External data: HARPS radial velocities of A and B from the ESO archive (B RVs from Lisogorskyi et al.)  
  > "obtained since 2004, publicly available from the ESO archive" (3.2.2 Radial Velocity Data); "As noted by (cite: Lisogorskyi2019), a significant fraction of the spectra collected for" (3.2.2 Radial Velocity Data) [from ESO HARPS archive; Lisogorskyi et al. 2019 (cite: Lisogorskyi2019)]
- External data: angular diameters of A and B (8.5 and 6.0 mas) and stellar radii/parallax used for the SED model  
  > "the angular sizes are 8.5 and 6.0 mas (cite: Kervella2017a)" (2.1 Observations) [from Kervella et al. 2017 (cite: Kervella2017a)]
- External data: HARPS fibre-exchange RV zero-point shift applied to pipeline RVs  
  > "We corrected the RV shift caused by the HARPS fiber exchange in 2015, as recommended by (cite: Trifonov2020)." (3.2.2 Radial Velocity Data) [from Trifonov et al. 2020 (cite: Trifonov2020)]
- External data: relative gravitational redshift and convective shift of B subtracted from its RVs (314 m/s)  
  > "Following (cite: Pourbaix2016) (cite: Pourbaix2002; Kervella2016), we subtracted a constant velocity shift of" (3.2.2 Radial Velocity Data) [from Pourbaix & Boffin 2016; Pourbaix et al. 2002; Kervella et al. 2016]
- External data: sub-mm/IR SED photometry of alpha Cen A and B, with ALMA values recalibrated  
  > "as tabulated in (cite: Liseau2013; Trigilio2018) using ALMA values as updated with an improved calibration model (cite: Liseau2019)" (2.4 Astrometric Noise due to Stellar Activity) [from Liseau et al. 2013; Trigilio et al. 2018; Liseau 2019]
- External data: 17 GHz solar maps for 2001 and 2010  
  > "taken daily by the Nobeyama Radio Interferometer (cite: Shibasaki2013)" (2.4 Astrometric Noise due to Stellar Activity) [from Shibasaki 2013 (cite: Shibasaki2013)]
- External data: bolometric fluxes used for luminosities of A and B  
  > "The luminosities of A and B are computed adopting the bolometric flux by (cite: Boyajian2013)" (3.3 Orbital parameters, masses and barycentric proper motion) [from Boyajian et al. 2013 (cite: Boyajian2013)]
- External data: Hipparcos-Gaia proper motion of Proxima  
  > "We adopt the Hipparcos-Gaia proper motion determined by (cite: Kervella2019) for Proxima" (3.5 The orbit of Proxima Centauri) [from Kervella et al. 2019 (cite: Kervella2019)]
- External data: Proxima radial velocity  
  > "and the radial velocity from (cite: Kervella2017b)" (3.5 The orbit of Proxima Centauri) [from Kervella et al. 2017b (cite: Kervella2017b)]
- Simulation/model as data: BT-Settle photosphere model, Teff = 5800 K, R = 1.22 Rsun at 1.334 pc for alpha Cen A (Teff = 5300 K for B)  
  > "we fitted the absolute flux densities for a T$_{eff}=$5800 K B-T Settle model (cite: Baraffe2015)" (2.4 Astrometric Noise due to Stellar Activity)

## Processing

### Calibration

- pipeline or manual: standard ALMA data calibration (pipeline or manual not specified)  
  > "We used the standard ALMA data calibration for all observations." (2.2 Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1427-4206 (bright quasar, known flux density); also sets amplitude and phase scale  
  > "a 2-min scan at the beginning of each observation of the bright quasar, J1427-4206, with a known flux density" (2.1 Observations); "The amplitude calibration for each antenna/spectral-window channel was determined from the 2-min scan of J1427-4206 and applied to the rest of the observation." (2.2 Data Reduction)
- flux scale uncertainty: 10-15% absolute (no primary flux standards observed)  
  > "no primary flux calibration standards were observed, thus the absolute calibration uncertainty is 10-15" (2.2 Data Reduction)
- self calibration: phase self-calibration on alpha Cen A and B (case 3), used only for the A-B separation, not for absolute positions  
  > "As the radio emission from the two stars is sufficiently bright and compact, we self-calibrate the" (2.3 Differential Astrometry); "As absolute position information is not preserved during self-calibration, these data are only used for the A to B separation" (2.3 Differential Astrometry)

### Imaging

- task: CASA tclean for each calibrated observation; imfit for fluxes, jmfit for positions  
  > "to produce images for each of the calibrated observations, using the nominal data weighting (weighting=briggs, robust=0)." (2.2 Data Reduction); "The integrated flux was determined using the" (2.2 Data Reduction)
- deconvolver: _not stated_
- weighting robust: briggs, robust = 0  
  > "using the nominal data weighting (weighting=briggs, robust=0)" (2.2 Data Reduction)
- uv taper: _not stated_
- cell size: 5 mas  
  > "pixels, with grid separation 5 mas, covered nearly all of the ALMA primary beam." (2.2 Data Reduction)
- image size: 2048x2048 pixels (512x512 for the check source)  
  > "The image size of 2048" (2.2 Data Reduction); "For the J1424-6807 check source, we analyzed an image size of 512" (2.2 Data Reduction)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: image resolution 20 to 150 mas depending on configuration  
  > "The image resolution varied from 20 mas to 150 mas, depending on the configuration." (2.2 Data Reduction)
- final rms: _not stated_

### Inherited from earlier work

- orbit and proper-motion fitting approach follows Kervella et al. 2016  
  > "we generally followed the same approach as (cite: Kervella2016)" (3.2.3 Orbital and proper motion fit procedure) [from (cite: Kervella2016)]
- HARPS fibre-exchange RV correction  
  > "We corrected the RV shift caused by the HARPS fiber exchange in 2015, as recommended by (cite: Trifonov2020)." (3.2.2 Radial Velocity Data) [from (cite: Trifonov2020)]
- constant velocity shift removed from B RVs  
  > "Following (cite: Pourbaix2016) (cite: Pourbaix2002; Kervella2016), we subtracted a constant velocity shift of" (3.2.2 Radial Velocity Data) [from (cite: Pourbaix2016) (cite: Pourbaix2002; Kervella2016)]
- astrometric precision relation sigma ~ FWHM/(2 SNR)  
  > "An empirical relationship (cite: Monet2010) shows the dependence of astrometric precision," (2.3 Differential Astrometry) [from (cite: Monet2010)]
- self-calibration algorithm  
  > "we self-calibrate the" (2.3 Differential Astrometry) [from (cite: Sch80)]
- starspot jitter model for the Sun at visible wavelengths  
  > "A detailed analysis (cite: Makarov2009) suggests that a quiescent star like the Sun would have a photospheric jitter at visible wavelengths of" (2.4 Astrometric Noise due to Stellar Activity) [from (cite: Makarov2009)]
- free-free emission formula for the chromosphere  
  > "simplified representation of free-free chromospheric emission following (cite: Mezger1967)" (2.4 Astrometric Noise due to Stellar Activity) [from (cite: Mezger1967)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the standard ALMA pipeline or manual calibration was used (no version given)
- tclean deconvolver, niter, threshold, masks and uv range; the CLEAN settings beyond weighting, cell and image size
- self-calibration details: initial model, solution interval, number of rounds, which data were included
- jmfit/imfit fit regions and settings and how component positions were converted to Table 2 and Table 4 values
- how the check-source offset and pair differences were converted into the adopted 3 mas / 6 mas absolute uncertainties
- how the 2018 Oct second observation (20 mas offset) was identified and which antennas/scans were used
- time-dependent perspective and light-time corrections: exact formulae and parameters beyond the quoted effects
- treatment of Hipparcos covariance and weights of the heterogeneous archival differential astrometry
- the preliminary best-fit solution used for 5 sigma RV clipping and weighting between A and B
- full machine-readable Tables 6 and 7 (only excerpts printed); photometry values behind the SED fit
- exact Nobeyama map list and the chord-centroid algorithm, plus the Monte Carlo draw counts

## Analysis recipe

1. **calibrate ALMA data and check source**: standard ALMA calibration; amplitude and phase from the J1427-4206 scan applied to the whole observation; phase referencing on J1452-6502 for target and check source J1424-6807  
  > "The amplitude calibration for each antenna/spectral-window channel was determined from the 2-min scan of J1427-4206 and applied to the rest of the observation." (2.2 Data Reduction); "was obtained in the normal phase referencing method from the antenna-based phase from each of the fifty 18-sec scans on J1452-6502." (2.2 Data Reduction)
   - software: CASA
   - parameter: antenna/spectral-window scale factor constant within 5% over the observation  
  > "The measured antenna/spectral-window scale factor is constant within 5% over the" (2.2 Data Reduction)
   - fitting: _not stated_
   - validation: five 20-s scans of the ICRF quasar J1424-6807 per epoch as an independent absolute-position check  
  > "To provide an independent check of the absolute accuracy of these observations, we included five 20-sec scans of the quasar J1424-6807 near" (2.2 Data Reduction)
2. **image each observation and measure fluxes**: tclean images per observation (briggs robust 0, 2048x2048 at 5 mas), Gaussian fit with imfit for fluxes; positions from images, not uv analysis  
  > "to produce images for each of the calibrated observations, using the nominal data weighting (weighting=briggs, robust=0)." (2.2 Data Reduction); "We derived all astrometric positions from the images; we did not use uv data analysis to obtain the source positions." (2.2 Data Reduction)
   - software: CASA tclean, CASA imfit
   - parameter: 5 mas grid, 2048x2048 pixels covering nearly all of the primary beam  
  > "pixels, with grid separation 5 mas, covered nearly all of the ALMA primary beam." (2.2 Data Reduction)
   - assumption: photospheres unresolved (diameters 8.5 and 6.0 mas)  
  > "Thus, the individual photospheres are not resolved in these observations." (2.2 Data Reduction)
   - fitting: Gaussian fit to each star with imfit; uncertainty is fit error only  
  > "The uncertainty reported is the fitting uncertainty and does not include the absolute flux error." (2.2 Data Reduction)
   - validation: fluxes agree with Liseau et al. 2016 within the 10-15% absolute uncertainty  
  > "Within this absolute uncertainty, our fluxes agree with those of (cite: Liseau2016)." (2.2 Data Reduction)
3. **measure absolute positions and calibrate their accuracy**: jmfit positions per one-hour observation on the ICRS frame, averaged per pair; accuracy from check source and pair differences  
  > "The measured positions from each one-hour observation of" (2.2.1 Absolute Astrometry); "Each hour-long observation can be combined into an average position with no significant loss of precision in the absolute position." (2.2.1 Absolute Astrometry)
   - software: CASA jmfit
   - parameter: adopted absolute uncertainty 3 mas (2019 July and August) and 6 mas (2018 October)  
  > "we use a conservative value of 3 mas for the absolute astrometric uncertainty for the higher resolution configurations (2019 July and August) and 6 mas for the lower resolution (2018 October) data" (2.2.1 Absolute Astrometry)
   - assumption: check source to phase calibrator separation 4.1 deg is similar to alpha Cen to phase calibrator (4.5 deg), so offsets transfer after SNR scaling  
  > "We note that the angular separation between the check source and the phase calibrator is 4.1 degrees" (2.2.1 Absolute Astrometry)
   - fitting: _not stated_
   - validation: check source offset ~2.5 mas; pair differences about a factor of 3 above the internal error; one anomalous observation (20 mas offset) discarded  
  > "the average offset of the check source between our measured ALMA position and its International Celestial Reference System (ICRS) position is about 2.5 mas" (2.2.1 Absolute Astrometry); "Hence, this observation is not used in our analysis below." (2.2.1 Absolute Astrometry)
4. **measure the A-B differential separation after self-calibration**: phase self-calibration on both stars, then jmfit of the A-B separation per epoch  
  > "we self-calibrate the" (2.3 Differential Astrometry); "The angular separation and estimated error (using the casa routine" (2.3 Differential Astrometry)
   - software: CASA jmfit
   - parameter: separation uncertainties 0.3 to 0.6 mas from positional fitting  
  > "The uncertainties in total separation are from the positional fitting and range from 0.3 to 0.6 mas." (2.3 Differential Astrometry)
   - assumption: atmospheric distortions act nearly identically on A and B  
  > "the atmospheric distortions act nearly identically on" (2.3 Differential Astrometry)
   - fitting: _not stated_
   - validation: separations agreed within uncertainties for no self-cal, self-cal on A only, and self-cal on A and B; image SNR improved by ~2  
  > "The separations for these three methods agreed to within the uncertainties" (2.3 Differential Astrometry); "which increases by factor of $\sim$2 and by the significantly lower residuals" (2.3 Differential Astrometry)
5. **estimate astrometric jitter from stellar activity**: fit SED with BT-Settle photosphere plus free-free chromosphere to get photospheric and chromospheric fractions in Band 7, then scale solar 17 GHz centroid shifts (2001 and 2010) by stellar diameters and chromospheric fraction  
  > "We evaluated the shift between the intensity-weighted centroid and the nominal disk center by calculating the centroid of all chords across the solar disk in both the vertical and horizontal directions." (2.4 Astrometric Noise due to Stellar Activity); "We fit the free-free emission from" (2.4 Astrometric Noise due to Stellar Activity)
   - parameter: 244 solar maps in 2001 and 300 in 2010  
  > "for which there were maps of suitable quality (244 in 2001 and 300 in 2010)" (2.4 Astrometric Noise due to Stellar Activity)
   - assumption: starspots of ~4000 K on a 5800 K photosphere  
  > "starspots having an average temperature of T$_{spot}\sim$4000 K vs a photospheric temperature of T$_{phot}\sim$5800 K" (2.4 Astrometric Noise due to Stellar Activity)
   - assumption: Sun is a template for solar-like activity of alpha Cen A and B  
  > "but both are similar in their activity levels to the Sun" (2.4 Astrometric Noise due to Stellar Activity)
   - fitting: two-parameter (T_gas, EM) free-free fit added to a photosphere with 9% normalization uncertainty; Monte Carlo propagation; chi2 62 for 24 dof  
  > "The fit has a $\chi^2$ of 62 with 24 degrees of freedom." (2.4 Astrometric Noise due to Stellar Activity); "A Monte Carlo simulation varying $T_C$, $EM$ and the photospheric normalization, $1.02\pm0.09$, relative to their uncertainties gives a photospheric fraction of" (2.4 Astrometric Noise due to Stellar Activity)
   - validation: _not stated_
6. **fit orbit from RV plus differential astrometry**: Keplerian two-body model fit for epoch 2019.5 to RVs and differential astrometry, with perspective and light-time corrections applied in a second fitting round  
  > "We first determined the orbital parameters (Keplerian orbital elements, dynamical parallax, total mass of the system, and mass ratio) for epoch 2019.5 based only on the RV and differential astrometry data and a simple Keplerian two-body model." (3.2.3 Orbital and proper motion fit procedure); "We then computed a second round of orbital and proper motion fitting on these corrected observations" (3.2.3 Orbital and proper motion fit procedure)
   - software: SciPy scipy.optimize.leastsq, Astropy SkyCoord
   - parameter: 2 m/s uniform jitter added in quadrature to RVs; RVs with sigma > 10 m/s rejected; 5 sigma clipping (0.9% of A, 1.0% of B)  
  > "Therefore we added in quadrature a uniform uncertainty of 2 m s$^{-1}$ to all measurements." (3.2.2 Radial Velocity Data); "filtered out the RV measurements whose uncertainty is larger than 10 m s$^{-1}$, and cleaned the strongest outliers with a $5\sigma$ clipping with respect to the best fit preliminary solution." (3.2.2 Radial Velocity Data)
   - assumption: reference epoch 2019.5 chosen to match the majority of the ALMA data; second-order effects treated as linear perturbations  
  > "This reference time was arbitrarily chosen to correspond to the majority of our ALMA measurements" (3.2.3 Orbital and proper motion fit procedure)
   - assumption: intrinsic RV shift of A taken as zero  
  > "whose intrinsic shift is assumed to be zero" (3.2.2 Radial Velocity Data)
   - fitting: Levenberg-Marquardt least squares on the full data set (scipy.optimize.leastsq); uncertainties normalised to data dispersion  
  > "using a classical multi-parameter Levenberg-Marquardt least-squares fitting algorithm on the complete data set." (3.2.3 Orbital and proper motion fit procedure)
   - validation: reduced chi2 of 1.2; a third iteration did not change the parameters; adopting Trifonov RV shift gave no significant change  
  > "We obtain a satisfactory reduced $\chi^2$ for the best fit orbit model of 1.2." (3.3 Orbital parameters, masses and barycentric proper motion); "We checked that a third iteration of fitting did not result in a significant change of the derived parameters." (3.2.3 Orbital and proper motion fit procedure)
7. **determine barycentric proper motion and parallax check**: adopt dynamical parallax and mass ratio, compute barycentre positions at Hipparcos and ALMA epochs, fit linear space motion  
  > "In a second step, we adopted the dynamical parallax and mass ratio to determine the barycentric proper motion from the absolute Hipparcos and ALMA absolute astrometric positions of" (3.2.3 Orbital and proper motion fit procedure); "The space velocity of the barycenter of the AB system was then determined from this set of barycenter positions through a linear fit." (3.2.3 Orbital and proper motion fit procedure)
   - software: SciPy scipy.optimize.leastsq
   - parameter: ALMA absolute positions assigned 3 mas (6 mas for Oct 2018); 10 absolute points in total  
  > "Our complete sample of absolute astrometric measurements includes a total of 10 points; 9 from our ALMA data as given in Table" (3.2.1 Astrometry Data)
   - fitting: Levenberg-Marquardt least squares; uncertainties scaled by about sqrt(1.6)  
  > "In practice, this means that the $1\sigma$ uncertainties of the derived parameters are scaled by a factor of $\approx \sqrt{1.6}$." (3.3 Orbital parameters, masses and barycentric proper motion)
   - validation: reduced chi2 of 1.6; independent trigonometric parallax fit consistent with orbital parallax  
  > "The reduced $\chi^2$ of the best fit barycenter proper motion vector model is 1.6." (3.3 Orbital parameters, masses and barycentric proper motion); "Both values are, however, statistically consistent." (3.3 Orbital parameters, masses and barycentric proper motion)
8. **derive stellar masses, radii and luminosities**: masses from fitted total mass and mass fraction; radii from limb-darkened angular diameters and the new parallax; luminosities from bolometric fluxes  
  > "The radii are computed adopting the limb darkened angular diameters measured by (cite: Kervella2017a)." (3.3 Orbital parameters, masses and barycentric proper motion)
   - parameter: L_sun = 3.828e26 W  
  > "$L_\odot = 3.828\ 10 ^{26}$ W" (3.3 Orbital parameters, masses and barycentric proper motion)
   - fitting: _not stated_
   - validation: masses and radii close to theoretical values from asteroseismic analyses  
  > "The masses and radii values are close to the theoretical values determined by (cite: Thevenin2002) and (cite: Yildiz2008)" (3.4 Prospects for Improved Stellar Properties)
9. **estimate planet detection limits and Proxima binding**: scale ALMA single-epoch accuracy (500, 250, 100 uas; 20 epochs over 5 yr) against PRV limits; compare AB-Proxima differential velocity with escape limit  
  > "we adopt three cases based on single measurement accuracy of 500, 250, 100 $\mu$as and a series of 20 observations spread over 5 years." (3.5 Prospects for Planet Detection based on Differential Astrometry); "We obtain a differential space velocity of" (3.6 The orbit of Proxima Centauri)
   - assumption: differential astrometric performance continues to scale with baseline length  
  > "thus if the differential astrometry performance continues to scale with baseline length, single epoch observations at" (3.5 Prospects for Planet Detection based on Differential Astrometry)
   - fitting: _not stated_
   - validation: compared with the HST/FGS HD 202206 c detection of Benedict and Harrison 2017  
  > "To check our detection estimate, we compare with the astrometric data presented by (cite: Benedict2017)." (3.5 Prospects for Planet Detection based on Differential Astrometry)

## Software

- **CASA** : calibration and imaging with tclean, flux fits with imfit and position fits with jmfit  
  > "(cite: McMullin2007) to produce images for each of the calibrated observations" (2.2 Data Reduction); "CASA (McMullin et al. 2007), astropy (The Astropy Collaboration 2013, 2018)" (Software)
- **SciPy (scipy.optimize.leastsq)** : Levenberg-Marquardt orbit and proper motion fits  
  > "It is based on the `scipy.optimize.leastsq` routine of the SciPy[^1] library." (3.2.3 Orbital and proper motion fit procedure)
- **Astropy** : SkyCoord class and coordinate transformations for the perspective and light-time corrections  
  > "we extensively used the `SkyCoord` class and celestial coordinate system transformation routines available in the `Astropy`[^2] library." (3.2.3 Orbital and proper motion fit procedure)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| absolute astrometric uncertainty adopted per ALMA epoch | 3 mas (2019 observations); 6 mas (2018 October) | not stated | mas | 3 | we use a conservative value of 3 mas for the absolute astrometric uncertainty for the higher resolution configurations (2019 July and August) and 6 mas for the lower resolution (2018 October) data |
| mean check-source offset from ICRS position (four highest resolution observations) | about 2.5 | not stated | mas | 3 | the average offset of the check source between our measured ALMA position and its International Celestial Reference System (ICRS) position is about 2.5 mas |
| A-B separation uncertainty from ALMA | 0.3 to 0.6 | not stated | mas | 4 | The uncertainties in total separation are from the positional fitting and range from 0.3 to 0.6 mas. |
| photospheric fraction of Band 7 emission, alpha Cen A | 85 | 1.3 | percent | 5 | gives a photospheric fraction of $\Phi_p=85\pm$1.3% photospheric vs. $\Phi_c=1-\Phi_p=15\pm$1.4% chromospheric. |
| photospheric fraction of Band 7 emission, alpha Cen B | 69 | 7 | percent | 5 | derived $\Phi_p=69\pm$7% photospheric vs. $\Phi_c=31\pm$7% chromospheric. |
| free-free fit gas temperature and emission measure, alpha Cen A | T_gas = 5100 K; EM = 3.0e10 pc cm^-6 | 650 K; 0.4e10 | K; pc cm^-6 | 5 | $T_{gas}$=5100$\pm$650 K and $EM=3.0\pm 0.4\times10^{10}$ pc cm$^{-6}$ |
| solar centroid jitter during 2001 (active) | 6.46 arcsec, 0.36% of disk | not stated | arcsec; percent of solar disk | 5 | with a 1$\sigma$ standard deviation of 6.46$''$, or $\sigma_{\odot,active}=$0.36% of the solar disk during 2001 |
| total astrometric jitter in the A-B separation, active and quiet | 15 (active) and 6 (quiet) | 10 and 4 (Table 5) | microarcsec | 5 | and varies between 15 and 6 $\mu$arcsec in the active and quiet sun cases. |
| semi-major axis of the AB orbit | 17.4930 | 0.0096 | arcsec | 6 | $17.4930 \pm 0.0096$ |
| orbital period | 79.762 | 0.019 | yr | 6 | $79.762 \pm 0.019$ |
| orbital eccentricity | 0.51947 | 0.00015 | dimensionless | 6 | $0.51947 \pm 0.00015$ |
| orbital inclination | 79.2430 | 0.0089 | deg | 6 | $79.2430 \pm 0.0089$ |
| orbital parallax | 750.81 | 0.38 | mas | 6 | orbital parallax ($\varpi_\mathrm{orb} =750.81 \pm 0.38$ mas) |
| trigonometric parallax from barycentre positions | 747.1 | 5.2 | mas | 7 | the accuracy of the best fit trigonometric parallax ($\varpi_\mathrm{trig} = 747.1 \pm 5.2$ mas) |
| distance to alpha Cen AB | 1.3319 | 0.0007 | pc | 6 | The parallax determined in the present work ($\varpi = 750.81$ mas, $d=1.3319 \pm 0.0007$ pc) |
| masses of A and B | m_A = 1.0788; m_B = 0.9092 | 0.0029; 0.0025 | Msun | 8 | We find stellar parameters of $m_{\rm A} =1.0788 \pm 0.0029$ $M_\odot$ and $m_{\rm B} = 0.9092 \pm 0.0025$ $M_\odot$ |
| radii of A and B | R_A = 1.2175; R_B = 0.8591 | 0.0055; 0.0036 | Rsun | 8 | we revise the linear radii of the two stars to $R_{\rm A} = 1.2175 \pm 0.0055\,R_\odot$ and $R_{\rm B} = 0.8591 \pm 0.0036\,R_\odot$ |
| barycentre proper motion in RA (epoch 2019.5) | -3639.95 | 0.42 | mas/yr | 7 | $-3639.95 \pm 0.42$ |
| barycentre proper motion in Dec (epoch 2019.5) | +700.40 | 0.17 | mas/yr | 7 | $+700.40 \pm 0.17$ |
| perspective RV acceleration | +0.421 | not stated | m/s/yr | 6 | The RV geometrically increases with an acceleration of $\dot{V} = +0.421$ m s$^{-1}$yr$^{-1}$ |
| reduced chi2 of the orbit fit and of the proper-motion fit | 1.2 and 1.6 | not stated | dimensionless | 7 | We obtain a satisfactory reduced $\chi^2$ for the best fit orbit model of 1.2.; The reduced $\chi^2$ of the best fit barycenter proper motion vector model is 1.6. |
| differential velocity between AB and Proxima, and unbound limit | 280 (observed); 554 (limit) | 32; 7 | m/s | 9 | limit of $v_\mathrm{max} = 554 \pm 7$ m s$^{-1}$ for a gravitationally bound system; $\Delta v_{\alpha-\mathrm{Prox}} = 280 \pm 32$ m s$^{-1}$ |
| significance of the AB-Proxima gravitational link | 8.3 | not stated | sigma | 9 | to $5.5\sigma$ in (cite: Kervella2019) to $8.3\sigma$ in the present work |
| projected noise floor of a 20-epoch ALMA campaign | about 55 (two sigma 110) | not stated | microarcsec | 9 | a two sigma value of 110 $\mu$as and could lead to the identification of a 25 M$_\oplus$ planet with a 2 AU orbital semi-major axis |

## Qualitative findings

- separations from no self-cal, self-cal on A only and on A and B agree within uncertainties  
  > "The separations for these three methods agreed to within the uncertainties" (2.3 Differential Astrometry)
- purely photospheric starspot jitter is negligible in Band 7; chromospheric terms dominate the jitter budget  
  > "These terms dominate the purely photospheric component due to starspots." (2.4 Astrometric Noise due to Stellar Activity)
- new parallax is larger than Kervella et al. 2016 by 0.49 percent, lowering radii by about 1 sigma  
  > "is larger by 0.49% compared to the value previously determined by" (3.4 Prospects for Improved Stellar Properties)

## Claim tuples

- H: ALMA can deliver precise absolute astrometry of alpha Cen A and B | E: nine calibrated Band 7 observations in three configurations with a check source and repeated pairs | R: check-source offset ~2.5 mas; adopted absolute uncertainty 3 mas (6 mas for the low-resolution epoch) | F: absolute precision and accuracy of order 3 mas | **supported**
- H: self-calibrated ALMA images give sub-mas A-B separations | E: jmfit separations from self-calibrated images at nine epochs | R: separation uncertainties of 0.3 to 0.6 mas | F: differential separation uncertainties of 300 to 600 microarcsec | **supported**
- H: stellar activity jitter limits mm astrometry of alpha Cen | E: SED decomposition plus solar 17 GHz centroid variations scaled to the stars | R: total jitter 15 (active) and 6 (quiet) microarcsec | F: jitter below 15 microarcsec, negligible compared with instrumental terms for planets well above Earth mass | **supported**
- H: adding ALMA absolute and differential astrometry improves the orbit, masses and proper motion | E: joint fit of HARPS RVs, archival differential astrometry, Hipparcos and ALMA positions | R: m_A = 1.0788 +/- 0.0029 Msun, m_B = 0.9092 +/- 0.0025 Msun, parallax 750.81 +/- 0.38 mas | F: improved orbital elements, system proper motion, parallax and component masses | **supported**
- H: alpha Cen AB and Proxima form a bound system | E: compared differential space velocity with the unbound velocity limit | R: 280 +/- 32 m/s vs limit 554 +/- 7 m/s; significance 8.3 sigma | F: the three stars constitute a bound system | **supported**
- H: continued ALMA astrometry can detect planets in the stable region around A and B | E: noise-floor estimate from a hypothetical 20-epoch campaign with 100-500 microarcsec per-epoch precision | R: noise floor about 55 microarcsec, enough for a 25 Earth-mass planet at 2 AU | F: sensitivity to planets of a few 10s of Earth masses at 1-3 AU is expected, not yet demonstrated | **partially**

## Reasoning

- Why this data: Band 7 chosen to balance SNR, angular resolution and field of view for 10-100 mJy stars at 2-21 arcsec separation  
  > "From these parameters and looking to balance the SNR, the angular resolution and the field of view, we selected to observe in band 7." (2.1 Observations)
- Why this method: astrometric precision scales with angular resolution, so long baselines are preferred  
  > "As the astrometric precision scales directly with the angular resolution, observations when ALMA is in configurations with maximum baselines of 2 km or larger are most desirable" (2.1 Observations)
- Alternative: RVs from CES and UVES rejected because zero-point shifts add fit variables and degrade reliability  
  > "We tested incorporating additional radial velocity measurements from other spectrographs (in particular CES and UVES)." (3.2.2 Radial Velocity Data)
- Alternative: astrometry older than 1940 excluded  
  > "Measurements older than 1940 do not significantly improve the orbital parameters" (3.2.1 Astrometry Data)
- Alternative: earlier ALMA data of Liseau et al. not used for absolute astrometry (poorer resolution, no check source)  
  > "cross checks using a check source or between adjacent observations are not possible with those observations" (3.2.1 Astrometry Data)
- How they decided it was enough: _not stated_
- Limitation (authors): absolute flux scale 10-15% uncertain because no primary flux standard observed  
  > "no primary flux calibration standards were observed, thus the absolute calibration uncertainty is 10-15" (2.2 Data Reduction)
- Limitation (authors): one October 2018 observation had a 20 mas offset attributed to a tracking error and was dropped  
  > "believe it was caused by an error in the ALMA celestial position tracking system of" (2.2.1 Absolute Astrometry)
- Limitation (authors): trigonometric parallax is poorly constrained by the few absolute points  
  > "due to relatively poor phase coverage of the parallactic ellipse because of our limited number of absolute measurements" (3.3 Orbital parameters, masses and barycentric proper motion)
- Limitation (authors): jitter estimate is only an order of magnitude  
  > "This value represents only an order of magnitude estimate" (2.4 Astrometric Noise due to Stellar Activity)
- Limitation (authors): alpha Cen A RVs could not be recomputed with the correct mask because the ESO pipeline is not public  
  > "because that pipeline is not publicly accessible" (3.2.2 Radial Velocity Data)
- Caveat (inferred, ours): Chromospheric fraction of alpha Cen A is 15 +/- 1.4 percent in one place and 32 +/- 13 percent in another, and B is 31 vs 36 percent (text vs Table 5); the jitter numbers depend on which is used
- Caveat (inferred, ours): Absolute uncertainty of 3 mas is a judgement from check-source offsets and pair differences, not a propagated error budget
- Caveat (inferred, ours): Only nine epochs and five blocks; the planet sensitivity is projected, not measured
- Caveat (inferred, ours): Self-calibration details are missing, so the differential separation cannot be exactly reproduced
- Caveat (inferred, ours): Solar chromospheric jitter template at 17 GHz is assumed to transfer to Band 7 emission of other stars

## Reproducibility

- Data public (paper): HARPS RVs publicly available from the ESO archive; ALMA data cited by project code, public status not stated  
  > "obtained since 2004, publicly available from the ESO archive" (3.2.2 Radial Velocity Data); "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00557.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and calibration route
- Missing: self-calibration recipe
- Missing: jmfit settings and per-epoch fit regions
- Missing: full tables of archival differential astrometry and RVs are only partially printed
- Missing: orbit-fit code not released; perspective and light-time corrections described only in prose
- Data volume (inferred): ALMA: nine 70-min Band 7 observations, likely tens of GB of raw/calibrated data; HARPS RVs: small tables
- Score (inferred): 3/5, ALMA project code and key imaging parameters (briggs 0, 5 mas, 2048 px), the orbit-fit method (leastsq), and numeric results are given, but CASA version, self-calibration, fit settings and some data tables are not.
- Rediscovery candidate: yes, Orbit and proper-motion refit is redoable from public RVs, the Hipparcos position and the published ALMA position tables; main results are numeric; the ALMA imaging and self-calibration steps are only partly specified.

## Links

- Method: Kervella et al. 2016 (cite: Kervella2016) (orbit and proper-motion fit approach followed)
- Method: Monet et al. 2010 (cite: Monet2010) (astrometric precision relation FWHM/(2 SNR))
- Method: Makarov et al. 2009 (cite: Makarov2009) (starspot astrometric jitter model)
- Method: Mezger & Henderson 1967 (cite: Mezger1967) (free-free emission formula)
- Companion: Liseau et al. 2015, 2016 (cite: Liseau2015; Liseau2016) (earlier ALMA detections of both stars, flux comparison)
- Companion: Kervella et al. 2017 (cite: Kervella2017a) (angular diameters of A and B)
- Companion: Trigilio et al. 2018 (cite: Trigilio2018) (chromospheric properties for comparison)
- Related: ALMA Cycle 6 project 2018.1.00557.S
- Related: NEAR mid-infrared direct imaging project
- Related: HARPS archive of alpha Cen

## Checks

```json
{
 "quotes": 175,
 "quotes_ok": 175,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 24,
 "numeric_problems": 0,
 "fill": {
  "facts": 127,
  "stated": 101,
  "rate": 0.795
 },
 "evidence_ok": true
}
```
