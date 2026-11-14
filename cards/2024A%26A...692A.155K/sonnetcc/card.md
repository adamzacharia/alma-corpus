# Binary orbit and disks properties of the RW Aur system using ALMA observations

`2024A&A...692A.155K` | Astronomy and Astrophysics 2024 | first author: Kurtovic, N. T. | arXiv: 2407.18828 | DOI: 10.1051/0004-6361/202347583

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Nature (bound or unbound) of the RW Aur binary interaction and its impact on the dust and gas of the two disks, from multi-epoch 1.3 mm ALMA data  
  > "Thus, the present work aims to study the nature and impact of the binary interaction in the distribution of the gas and dust emission in the individual disks." (Introduction); "In order to constrain the impact and nature of the binary interaction in the RW Aur system (bound or unbound), we analyzed the circumstellar material at 1.3 mm wavelengths" (abstract)
- Target **RW Aur (A and B)**: coordinates _not stated_; z/distance 154 pc  
  > "The RW Aur system is composed of at least two stars located at 154 pc away from us (cite: gaia2016b; gaia2021edr3), each hosting its own disk" (Introduction); distance from Gaia (cite: gaia2016b; gaia2021edr3)  
  > "The RW Aur system is composed of at least two stars located at 154 pc away from us (cite: gaia2016b; gaia2021edr3), each hosting its own disk" (Introduction)

## Data provenance

- ALMA projects: 2015.1.01506.S, 2016.1.00877.S, 2016.1.01164.S, 2017.1.01631.S, 2018.1.00973.S
- bands: 1.3 mm  
  > "This work includes 1.3 mm observations of the system RW Aur from several different ALMA projects" (Observations)
- frequencies and spectral setup: SB4: 5 spws (2 continuum at 218.503 and 232.003 GHz; 12CO, 13CO, C18O J=2-1); LB1: 4 spws (3 continuum, 1 12CO); continuum channel width 1128.91 kHz  
  > "the correlator was configured to observe five and four spectral windows, respectively" (Observations); "SB4 contains two spectral windows covering dust continuum emission centered at $218.503$ GHz and $232.003$ GHz" (Observations); "The LB1 observation, on the other hand, has three spectral windows for the continuum and one spectral window for $^{12}$CO (J=2-1)." (Observations)
- continuum bandwidth: _not stated_
- arrays: ACA 7m (SB2) plus 12m array up to configuration C-10 (LB1)  
  > "starting from the 7m antennas of the ACA array from SB2, to the longest baselines from ALMA antenna configuration C-10 with LB1" (Results: Continuum visibility modeling)
- configurations: _not stated_
- baselines: SB1 15-3248 m; SB2 9-45 m; SB3 21-3697 m; LB1 41-16196 m (SB4 15-952 and 15-784 m)  
  > "15 - 3248" (Table 1); "9 - 45" (Table 1); "41 - 16196" (Table 1)
- angular resolution: LB1 continuum 18x30 mas (3 au in abstract); SB 12CO 267x414 mas; LB 12CO 69x98 mas  
  > "has an angular resolution of $18\times30$ mas" (Observations); "We imaged the dust continuum emission of RW Aur with a resolution of 3 au" (abstract)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2016-09 to 2018-12; time span about 2 years and 2 months (LB1 taken 2017-10)  
  > "with an approximate time-span of 2 years and 2 months" (Observations)
- pi or archival as stated: SB1 and SB2 already published (Rodriguez 2018); SB3 part of the Taurus survey (Long 2019, Manara 2019); SB4 and LB1 unpublished; PIs in Table 1 (Rodriguez, Herczeg, Facchini)  
  > "The projects SB1 and SB2 were already published in (cite: rodriguez2018), while SB3 was part of the Taurus survey published in (cite: long2019) and (cite: manara2019)." (Observations); "For the datasets SB4 and LB1, which have not been published before" (Observations)
- Line: 12CO J=2-1 (230.538 GHz)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- Other facility **Gaia**: System distance (154 pc) and DR3 astrometry used in orbit-fit tests  
  > "located at 154 pc away from us (cite: gaia2016b; gaia2021edr3)" (Introduction); "(iii) with historical astrometry, the ALMA radial velocity, and the *Gaia* DR3 astrometry" (Results: RW Aur B orbit, excluding ALMA astrometry)
- External data: Historical astrometric separations of RW Aur A and B, epochs 1944 to 2013 (two outliers excluded)  
  > "We combined our ALMA astrometry with the historical separation between RW Aur A and B as compiled by (cite: csepany2017), covering epochs from 1944 to 2013." (Results: RW Aur B orbit, with ALMA astrometry) [from (cite: csepany2017)]
- External data: Dust mass absorption coefficient kappa_nu = 2.3 (nu/230 GHz)^0.4 cm2 g-1  
  > "$\kappa_\nu=2.3(\nu/230\,\text{GHz})^{0.4}\,\text{cm}^{2}\text{g}^{-1}$ is the frequency-dependent mass absorption coefficient (cite: andrews2013)" (Results: Dust continuum emission) [from (cite: andrews2013)]
- External data: Reference dust temperature of 20 K for the dust mass  
  > "a known temperature, that is commonly set to 20 K for standard reference (cite: ansdell2016; cieza2019)" (Results: Dust continuum emission) [from (cite: ansdell2016; cieza2019)]
- External data: ALMA flux calibration uncertainty up to 10%  
  > "it is known that the ALMA flux calibration uncertainties can reach up to 10%, and even higher in particular cases (cite: Andrews2018)" (Results: Continuum visibility modeling) [from (cite: Andrews2018)]
- External data: Stellar luminosities of RW Aur A and B (0.88 and 0.53 Lsun)  
  > "The luminosities of stars A and B are 0.88$\,L_\odot$ and 0.53$\,L_\odot$, respectively (cite: Herczeg2014)" (Introduction) [from (cite: Herczeg2014)]

## Processing

### Calibration

- pipeline or manual: Started from pipeline-calibrated measurement sets (scriptforPI) delivered by ALMA  
  > "We started from the pipeline-calibrated measurement set generated with the `scriptforPI` delivered by ALMA." (Observations)
- casa version: CASA 5.6.2  
  > "Using `CASA 5.6.2`, we extracted the dust continuum emission from the spectral windows targeting gas emission lines" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: Up to 10%; a free per-epoch flux scaling factor i_obs fitted relative to SB4 (fixed to 1)  
  > "it is known that the ALMA flux calibration uncertainties can reach up to 10%, and even higher in particular cases (cite: Andrews2018)" (Results: Continuum visibility modeling); "we used observation SB4, which has a fixed $i_{SB4}=1$" (Results: Continuum visibility modeling)
- self calibration: Each project self-calibrated separately on the pseudo-continuum; Briggs robust 0.5 (LB1: 1.0) for the self-cal images; all scans and spws combined per gaincal  
  > "The signal-to-noise ratio (S/N) for each project was sufficient to self-calibrate each by itself" (Observations); "The imaging for the self-calibration process was made with a Briggs robust parameter of 0.5, except for LB1, where we used 1.0." (Observations); "We combined all the scans and spectral windows for each `gaincal` execution." (Observations)

### Imaging

- task: tclean with gain = 0.05, cyclefactor = 1.5, cleaned to 4 sigma; JvM correction applied  
  > "The gas and continuum emission were imaged using the task `tclean`." (Observations); "we lowered the `gain` parameter to $0.05$ and increased the `cyclefactor` to $1.5$" (Observations); "and we cleaned down to the 4$\sigma$ threshold" (Observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5 (LB1: 1.0), stated for the self-calibration imaging  
  > "The imaging for the self-calibration process was made with a Briggs robust parameter of 0.5, except for LB1, where we used 1.0." (Observations)
- uv taper: _not stated_
- cell size: 4 mas (velocity image pixels)  
  > "We did not downsample the velocity image pixels, which have a size of 4 mas." (Results: 12CO J=2-1 emission)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub on the self-calibrated line measurement sets  
  > "We subtracted the continuum emission with the task `uvcontsub` and obtained a measurement set for each molecular line for each epoch." (Observations)
- line free channels: Channels within +/-25 km/s of the systemic VLSR (about 6 km/s) flagged to build the continuum  
  > "we flagged the channels located at $\pm 25\,$km s$^{-1}$ from the system approximate velocity at the local standard of rest (VLSR), which is about 6 km s$^{-1}$ for RW Aur" (Observations)
- primary beam correction: _not stated_
- array combination: SB 12CO image from SB1+SB2+SB4; LB 12CO image from all observations; 13CO and C18O from SB1-SB4  
  > "The first image combined the observations SB1, SB2, and SB4 to optimize the sensitivity to large spatial scales" (Observations); "the second image combined all observations to maximize the sensitivity at high angular resolution" (Observations); "The $^{13}$CO and C$^{18}$O images have the same imaging setup as the SB $^{12}$CO image, but they include SB3." (Observations)
- smoothing: _not stated_
- final beam: SB 12CO 267x414 mas; LB 12CO 69x98 mas; LB1 continuum 18x30 mas  
  > "The angular resolution of the SB $^{12}$CO image is $267\times414$ mas, and the resolution in the LB $^{12}$CO image is $69\times98$ mas." (Observations); "has an angular resolution of $18\times30$ mas" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- JvM correction of the CLEAN images  
  > "We applied the JvM correction to our images, which scales the residuals to account for the volume ratio $\epsilon$ between the PSF of the images and the restored Gaussian of the `CLEAN` beam, as described in (cite: jorsater1995) and (cite: czekala2021)." (Observations) [from (cite: jorsater1995) and (cite: czekala2021)]
- Dust mass estimate formula  
  > "For an estimate of the dust mass, we followed (cite: hildebrand1983)" (Results: Dust continuum emission) [from (cite: hildebrand1983)]
- SB1 and SB2 data previously published; calibration and CO analysis of those data in earlier paper  
  > "The projects SB1 and SB2 were already published in (cite: rodriguez2018)" (Observations) [from (cite: rodriguez2018)]
- SB3 data from the Taurus survey  
  > "while SB3 was part of the Taurus survey published in (cite: long2019) and (cite: manara2019)" (Observations) [from (cite: long2019) and (cite: manara2019)]
- Peak intensity and moment images made with bettermoments  
  > "We used the package `bettermoments` (cite: bettermoments; teague2019) to create additional image products from the channel maps." (Observations) [from (cite: bettermoments; teague2019)]

### Not stated but needed to reproduce (our reading)

- CLEAN masks, deconvolver, niter, image size and cell size for the continuum and for the 12CO/13CO/C18O cubes, and the robust value used for the final images
- Self-calibration details: number of rounds, solution intervals, solution modes, reference antenna, and whether amplitude self-cal was done
- Which channels were flagged for lines other than the +/-25 km/s window, and the continuum bandwidth used per project
- Visibility weighting: whether statwt or any weight rescaling was applied before the visibility fits (the discussion only recommends standardising weights)
- galario and emcee settings for the continuum fit: number of walkers, steps, burn-in, parameter bounds, initial positions, image size, likelihood form, and how SB2 (ACA) offsets were treated
- Orbit-fit likelihood, the exact astrometric uncertainties used for each ALMA epoch, the adopted epochs, and the source of the parallax (6.406 +/- 0.044 mas) and of the 2.233 Msun total-mass prior
- How the single relative radial velocity of -0.954 km/s was measured from the 12CO cubes (method and region)
- eddy settings: fitting method, mask details beyond the ellipse sizes, and how uncertainties were obtained
- Flux calibrators per execution block and any flux corrections applied
- Aperture and centre used to compute the 12CO radii and brightness-temperature profiles

## Analysis recipe

1. **Build and self-calibrate a pseudo-continuum for each project**: Flag line channels, combine remaining channels with the continuum spws, average, and self-calibrate each project independently  
  > "The remaining channels were combined with the other continuum spectral windows to obtain a pseudo-continuum dataset" (Observations); "The signal-to-noise ratio (S/N) for each project was sufficient to self-calibrate each by itself" (Observations)
   - software: CASA 5.6.2, gaincal
   - parameter: Line channels within +/-25 km/s of VLSR (about 6 km/s) flagged  
  > "we flagged the channels located at $\pm 25\,$km s$^{-1}$ from the system approximate velocity at the local standard of rest (VLSR), which is about 6 km s$^{-1}$ for RW Aur" (Observations)
   - parameter: Averaged to 125 MHz channels and 6 s bins  
  > "we averaged into 125 MHz channels and $6\,$s bins to reduce data volume" (Observations)
   - parameter: Briggs robust 0.5 (LB1: 1.0) for self-cal images; observations not aligned to a common phase center before self-cal  
  > "The imaging for the self-calibration process was made with a Briggs robust parameter of 0.5, except for LB1, where we used 1.0." (Observations); "we did not align the different observations to the same phase center prior to self-calibration" (Observations)
   - assumption: Each project treated as a single epoch  
  > "Each project was completely observed within days between the first and last observation. We therefore treated each observation as a single epoch." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Apply self-cal to line data, subtract continuum, image gas and make moment maps**: Apply continuum self-cal tables to the original data, uvcontsub, tclean per line, combine epochs, then bettermoments for peak intensity, velocity, moment 0 and 1  
  > "The calibration tables obtained from the dust continuum self-calibration of each observation were then applied to the original measurement sets, which contained dust continuum and molecular line emission." (Observations); "We calculated the peak intensity image by fitting a quadratic function in each pixel along the velocity axis" (Observations)
   - software: CASA 5.6.2, uvcontsub, tclean, bettermoments
   - parameter: tclean gain 0.05, cyclefactor 1.5, clean to 4 sigma, JvM correction  
  > "we lowered the `gain` parameter to $0.05$ and increased the `cyclefactor` to $1.5$" (Observations); "and we cleaned down to the 4$\sigma$ threshold" (Observations)
   - parameter: Channel width 1.3 km/s for LB 12CO, 0.5 km/s for SB 12CO  
  > "When combined with the LB1 dataset, the highest allowed velocity resolution is 1.3 km s$^{-1}$, while the SB $^{12}$CO image was imaged with 0.5 km s$^{-1}$" (Observations)
   - parameter: Moment images clipped at 0 sigma with no mask; extra LB 12CO image clipped at 1.3 mJy/beam km/s  
  > "All the moment images were clipped at $0\sigma$ (negative emission is removed), and no mask was used." (Observations); "where we only considered pixels with emission over 1.3 mJy beam$^{-1}$ km s$^{-1}$" (Observations)
   - assumption: Spatial movement negligible across epochs at gas resolution, so epochs can be combined  
  > "under the assumption that spatial movement is negligible at the scales covered by the angular resolution of the gas observations" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit parametric visibility models to the continuum of both disks**: Joint multi-epoch fit with an axisymmetric brightness model per disk (A: point source + Gaussian + tapered power law; B: two Gaussian rings), visibilities of the two sources summed  
  > "we used the packages `galario` (cite: Tazzari2017) and `emcee` (cite: emcee2013) to fit a parametric visibility model to the data" (Results: Continuum visibility modeling); "This problem with the broken Gaussian description can be overcome by slightly increasing the complexity of the model to two Gaussian rings." (Results: Continuum visibility modeling); "The point and Gaussian components are needed to describe the inner emission of the disk" (Results: Continuum visibility modeling)
   - software: galario, emcee
   - parameter: Visibilities averaged to one channel per spw and 24 s; epochs not combined  
  > "To further reduce the data volume after completing the self-calibration, we averaged the continuum emission into one channel per spectral window and 24 s." (Observations)
   - parameter: All five epochs fit simultaneously with common intensity model but separate disk centers per epoch  
  > "However, we allowed the disk centers to be different in each observation" (Results: Continuum visibility modeling)
   - parameter: Free per-epoch flux scale i_obs, SB4 fixed to 1  
  > "we used observation SB4, which has a fixed $i_{SB4}=1$" (Results: Continuum visibility modeling)
   - parameter: Model pixel size 4 mas (2 mas test gave consistent results)  
  > "The pixel size for the model images was initially 4 mas, and we also tested the stability of the fit by running the same models with a pixel size of 2 mas, from which we obtained consistent results." (Results: Continuum visibility modeling)
   - assumption: Each disk brightness distribution constant over the two years; only relative positions change  
  > "with the underlying assumption that each disk brightness distribution is constant during the two years covered by our data" (Results: Continuum visibility modeling)
   - assumption: Azimuthally symmetric models  
  > "We fit azimuthally symmetric models to RW Aur A, and RW Aur B" (Results: Continuum visibility modeling)
   - fitting: MCMC (emcee) on all five epochs with flat priors; boundaries wide enough that walkers never reached them  
  > "We used a flat prior over the allowed parameter space, and the boundaries for each free parameter were wide enough such that walkers never interacted with them." (Results: Continuum visibility modeling)
   - validation: Residual visibilities imaged; highest peak residual 6 sigma for A, none structured at B  
  > "the highest peak residual is only $6\sigma$ (compared to $>300\sigma$ of the dust continuum image)" (Results: Continuum visibility modeling); "no structured residual is detected at the position of the source" (Results: Continuum visibility modeling)
4. **Derive fluxes, brightness temperatures and dust masses**: Integrate model images for flux; azimuthally averaged brightness temperature; dust mass from the Hildebrand formula  
  > "We constrained the flux of each source from the visibility modeling by integrating it from the model images." (Results: Dust continuum emission); "For an estimate of the dust mass, we followed (cite: hildebrand1983)" (Results: Dust continuum emission)
   - parameter: Dust temperature 20 K (also mean Tb of 27 K for RW Aur A within R90%)  
  > "When we assume a midplane temperature of 20 K (for comparison with other surveys and observations)" (Results: Dust continuum emission); "with an average brightness temperature of RW Aur A within its $R_{90\%}$ of 27 K" (Results: Dust continuum emission)
   - assumption: Optically thin dust at known temperature; fails for RW Aur A so only a lower limit  
  > "The additional assumption for this calculation was that the dust emission at 1.3 mm is emitted by optically thin dust with a known temperature" (Results: Dust continuum emission); "we can therefore only provide a lower limit to its dust mass" (Results: Dust continuum emission)
   - assumption: kappa_nu = 2.3 (nu/230 GHz)^0.4 cm2 g-1; distance 154 pc  
  > "$\kappa_\nu=2.3(\nu/230\,\text{GHz})^{0.4}\,\text{cm}^{2}\text{g}^{-1}$ is the frequency-dependent mass absorption coefficient (cite: andrews2013)" (Results: Dust continuum emission)
   - fitting: _not stated_
   - validation: _not stated_
5. **Test for a misaligned inner disk of RW Aur A**: Repeat the visibility MCMC letting the central Gaussian have its own inclination and position angle  
  > "We allowed the central Gaussian component describing the inner disk emission of RW Aur A to have a different inclination and position angle" (Results: Inner disk geometry of RW Aur A)
   - software: galario, emcee
   - parameter: Same procedure as the main visibility fit  
  > "we ran an additional visibility model for the dust continuum emission in the same way as described in Sect." (Results: Inner disk geometry of RW Aur A)
   - fitting: MCMC as in step 3  
  > "The results of the MCMC are shown in Table [3](#tab:warp_prop) and Fig. [6](#fig:uvmodel_cont_11)." (Results: Inner disk geometry of RW Aur A)
   - validation: Highest residual drops to 5 sigma but low-contrast non-axisymmetric residuals remain  
  > "we find that the highest amplitude residual is $5\sigma$, which is lower than for the non-warped disk model" (Results: Inner disk geometry of RW Aur A)
6. **Measure stellar masses from Keplerian rotation of the 12CO disks**: Fit a flat Keplerian disk to the velocity maps with eddy  
  > "We used the package `eddy` (cite: eddy) to fit the Keplerian rotation of each disk and estimate the mass of the central object." (Results: 12CO J=2-1 emission); "Therefore, we fit them with a flat Keplerian disk." (Results: 12CO J=2-1 emission)
   - software: eddy
   - parameter: Elliptical emission masks of 0.4 and 0.28 arcsec for A and B; velocity pixels 4 mas, not downsampled  
  > "The emission was masked using an elliptical mask with a size of 0.4” and 0.28” for A and B, respectively" (Results: 12CO J=2-1 emission); "We did not downsample the velocity image pixels, which have a size of 4 mas." (Results: 12CO J=2-1 emission)
   - parameter: Center, inclination and PA fixed from the continuum outer-disk fit; free: stellar mass and systemic velocity  
  > "The only free parameters for each disk are the stellar mass and the central velocity in the line of sight." (Results: 12CO J=2-1 emission)
   - assumption: Upper and lower emission surfaces cannot be distinguished, so a flat disk is assumed  
  > "our images cannot distinguish upper and lower emission surfaces" (Results: 12CO J=2-1 emission)
   - fitting: eddy fit with two free parameters per disk; formal errors a fraction of a percent  
  > "The uncertainty estimate from eddy suggests that the standard deviations are a fraction of a percent for the masses and velocity in the local standard of rest." (Results: 12CO J=2-1 emission)
   - validation: Masses agree with spectroscopic estimates  
  > "The two mass measurements are in agreement with spectroscopic estimates (cite: Herczeg2014; long2019; manara2019)." (Results: 12CO J=2-1 emission)
7. **Measure gas disk radii and gas-to-dust size ratio**: Integrate 12CO flux in elliptical apertures and find radii enclosing 68% and 90%; compare with continuum R90%  
  > "we integrated the flux over an elliptical aperture with a radius of $0.6''$ and $0.45''$ for RW Aur A and B, respectively" (Results: 12CO J=2-1 emission)
   - parameter: Aperture radii 0.6 arcsec (A) and 0.45 arcsec (B)  
  > "we integrated the flux over an elliptical aperture with a radius of $0.6''$ and $0.45''$ for RW Aur A and B, respectively" (Results: 12CO J=2-1 emission)
   - assumption: Radii are measured from a beam-convolved profile, so the ratio is an upper limit  
  > "this value should be considered as an upper limit, because the gas radius was measured from a beam-convolved $^{12}$CO profile" (Results: 12CO J=2-1 emission)
   - fitting: _not stated_
   - validation: _not stated_
8. **Fit the orbit of RW Aur B around RW Aur A**: MCMC over eight orbital parameters using ALMA disk-center astrometry, historical astrometry and one ALMA radial velocity; orbits computed with rebound for elliptical and hyperbolic regimes  
  > "Both families of orbits were calculated using the Python package `rebound` (cite: rein2012; rein2015)." (Results: RW Aur B orbit, with ALMA astrometry); "We sampled the probability density distribution of the orbital parameters using MCMC with `emcee` (cite: emcee2013)." (Results: RW Aur B orbit, with ALMA astrometry)
   - software: rebound, emcee
   - parameter: Eight free parameters; 24 times as many walkers as free parameters  
  > "We used 24 times as many walkers as the number of free parameters, which were eight for a given orbit" (Results: RW Aur B orbit, with ALMA astrometry)
   - parameter: Uniform prior on positive eccentricity, excluding |1-ecc|<1e-4; periastron distance fitted instead of semi-major axis  
  > "with a uniform prior for any positive eccentricity, except for a small forbidden region around $|1-\text{ecc}|<10^{-4}$ to avoid parabolic solutions" (Results: RW Aur B orbit, with ALMA astrometry)
   - parameter: Over 1e7 steps per walker; then one of every 80 steps recorded and last 1e5 recorded positions used  
  > "we ran an MCMC recording only one of every 80 steps to reduce data volume, and we derived the solutions from the last $10^5$ recorded positions for every walker" (Results: RW Aur B orbit, with ALMA astrometry)
   - parameter: Radial velocity -0.954 km/s of B relative to A with 1 sigma set to 100 m/s  
  > "we therefore set a conservative $1\sigma$ dispersion to 100 m s$^{-1}$ for the RV fitting" (Results: RW Aur B orbit, with ALMA astrometry)
   - parameter: Two historical outliers (1991 and 1944 measurements) excluded  
  > "We excluded two outlier measurements from the historical astrometric positions" (Results: RW Aur B orbit, with ALMA astrometry)
   - assumption: Disk centers coincide with the stars; disks axisymmetric with zero eccentricity  
  > "Assuming that the centers of the disks coincide with the location of the stars, we can use the visibility-modeled disk center as a precise astrometric measurement for each system." (Results: RW Aur B orbit, with ALMA astrometry)
   - assumption: Stars treated as point masses carrying the whole system mass  
  > "Another relevant approximation taken in this work was to consider the stars as point sources that contained all of the mass of the system" (Discussion: Astrometry with ALMA)
   - fitting: emcee MCMC; individual walkers did not converge but the density distribution was stable after >1e7 steps  
  > "However, the probability density distribution derived from the walkers positions reached stable values after $>10^7$ steps." (Results: RW Aur B orbit, with ALMA astrometry)
   - validation: Additional fits excluding the ALMA astrometry (historical only; plus ALMA RV; plus Gaia DR3)  
  > "Additional tests were run excluding the ALMA astrometry from the orbital fit." (Results: RW Aur B orbit, excluding ALMA astrometry)
9. **Compare elliptical and hyperbolic solutions**: Akaike information criterion on the best 99.85 percentile of elliptical and hyperbolic models  
  > "We compare the solutions with the Akaike information criterion (cite: akaike1974), which quantifies the loss of information for a given model." (Discussion: Testing the bound/unbound nature)
   - parameter: Best 99.85 percentile of each family compared  
  > "When comparing the best $99.85$ percentile of elliptical and hyperbolic models" (Discussion: Testing the bound/unbound nature)
   - assumption: Only the astrometric likelihood is used; 12CO morphology not used as a prior  
  > "This comparison only takes into account the likelihood from the astrometric fit" (Discussion: Testing the bound/unbound nature)
   - fitting: _not stated_
   - validation: _not stated_
10. **Compute disk-binary misalignment**: Compare disk inclination and PA (orientation set by the jet) with orbital inclination and node from the MCMC  
  > "When we compare the inclination and position angle of RW Aur A disk, using the orientation implied by the jet emission, with the inclination and longitude of the ascending node of the orbital solutions from the MCMC" (Discussion: Orientation of the orbit, disks, and jet emission)
   - assumption: Disk is close to perpendicular to the jet  
  > "Assuming that the disk is close to perpendicular to the jet" (Discussion: Orientation of the orbit, disks, and jet emission)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.6.2: Continuum extraction, self-calibration and imaging  
  > "Using `CASA 5.6.2`, we extracted the dust continuum emission from the spectral windows targeting gas emission lines" (Observations)
- **tclean** : Imaging of gas and continuum  
  > "The gas and continuum emission were imaged using the task `tclean`." (Observations)
- **gaincal** : Self-calibration gain solutions  
  > "We combined all the scans and spectral windows for each `gaincal` execution." (Observations)
- **uvcontsub** : Continuum subtraction for the line data  
  > "We subtracted the continuum emission with the task `uvcontsub`" (Observations)
- **scriptforPI** : Source of the pipeline-calibrated measurement sets  
  > "We started from the pipeline-calibrated measurement set generated with the `scriptforPI` delivered by ALMA." (Observations)
- **bettermoments** : Peak intensity, velocity, moment 0 and moment 1 maps  
  > "We used the package `bettermoments` (cite: bettermoments; teague2019) to create additional image products from the channel maps." (Observations)
- **galario** : Visibility modeling of the dust continuum  
  > "we used the packages `galario` (cite: Tazzari2017) and `emcee` (cite: emcee2013) to fit a parametric visibility model to the data" (Results: Continuum visibility modeling)
- **emcee** : MCMC for the visibility fits and for the orbit fits  
  > "we used the packages `galario` (cite: Tazzari2017) and `emcee` (cite: emcee2013) to fit a parametric visibility model to the data" (Results: Continuum visibility modeling); "We sampled the probability density distribution of the orbital parameters using MCMC with `emcee` (cite: emcee2013)." (Results: RW Aur B orbit, with ALMA astrometry)
- **eddy** : Keplerian fit to 12CO velocity maps for stellar masses  
  > "We used the package `eddy` (cite: eddy) to fit the Keplerian rotation of each disk and estimate the mass of the central object." (Results: 12CO J=2-1 emission)
- **rebound** : Computing elliptical and hyperbolic orbital positions from true anomaly  
  > "Both families of orbits were calculated using the Python package `rebound` (cite: rein2012; rein2015)." (Results: RW Aur B orbit, with ALMA astrometry)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| R90% of RW Aur A dust continuum | 123.77 | 0.12 | mas | 3 | $123.77 \pm 0.12$; compact ($R_{90\%}=0.124''$ or 19 au |
| R90% of RW Aur B dust continuum | 92.95 | 0.14 | mas | 3 | $92.95 \pm 0.14$ |
| R68% of RW Aur A dust continuum | 101.37 | 0.13 | mas | 3 | $101.37 \pm 0.13$ |
| R68% of RW Aur B dust continuum | 68.55 | 0.23 | mas | 3 | $68.55 \pm 0.23$ |
| Ring radius of RW Aur B | 41.49 | 0.29 | mas | 3 | $41.49  \pm 0.29$; We find that the RW Aur B ring peaks at about 42 mas, which is 6.5 au from the disk center. |
| Integrated 1.3 mm flux of RW Aur A | 34.504 | 0.010 | mJy | 3 | $34.504 \pm 0.010$ |
| Integrated 1.3 mm flux of RW Aur B | 4.427 | 0.006 | mJy | 3 | $4.427 \pm 0.006$ |
| Inclination of RW Aur A disk | 54.93 | 0.04 | deg | 3 | $54.93 \pm 0.04$ |
| Position angle of RW Aur A disk | 39.35 | 0.05 | deg | 3 | $39.35 \pm 0.05$ |
| Inclination of RW Aur B disk | 63.98 | 0.16 | deg | 3 | $63.98 \pm 0.16$ |
| Position angle of RW Aur B disk | 39.65 | 0.24 | deg | 3 | $39.65 \pm 0.24$ |
| Separation r_AB of B from A, SB1 | 1491.49 | 0.15 | mas | 3 | $1491.49 \pm 0.15$ |
| Separation r_AB of B from A, SB3 | 1493.49 | 0.64 | mas | 3 | $1493.49 \pm 0.64$ |
| Separation r_AB of B from A, SB4 | 1499.50 | 0.60 | mas | 3 | $1499.50 \pm 0.60$ |
| Separation r_AB of B from A, LB1 | 1493.56 | 0.15 | mas | 3 | $1493.56 \pm 0.15$ |
| Position angle theta_AB of B relative to A, SB1 | 254.155 | 0.008 | deg | 3 | $254.155 \pm 0.008$ |
| Position angle theta_AB of B relative to A, SB3 | 254.047 | 0.026 | deg | 3 | $254.047 \pm 0.026$ |
| Position angle theta_AB of B relative to A, SB4 | 254.041 | 0.033 | deg | 3 | $254.041 \pm 0.033$ |
| Position angle theta_AB of B relative to A, LB1 | 254.055 | 0.006 | deg | 3 | $254.055 \pm 0.006$ |
| Flux scaling factor i_SB1 | 1.063 | 0.001 | dimensionless | 3 | $1.063 \pm 0.001$ |
| Flux scaling factor i_SB2 | 1.055 | 0.006 | dimensionless | 3 | $1.055 \pm 0.006$ |
| Flux scaling factor i_SB3 | 1.006 | 0.002 | dimensionless | 3 | $1.006 \pm 0.002$ |
| Flux scaling factor i_LB1 | 0.970 | 0.001 | dimensionless | 3 | $0.970 \pm 0.001$ |
| Peak brightness temperature of RW Aur A | 120 | not stated | K | 4 | with a peak $T_b=120$ K in the disk center |
| Maximum brightness temperature of RW Aur B | 15 | not stated | K | 4 | the maximum brightness temperature of RW Aur B at any radii is 15 K |
| Dust mass of RW Aur A at 20 K | 23.9 | not stated | Earth masses | 4 | we obtain a dust mass of $23.9\,M_\oplus$ and $3.1\,M_\oplus$ for A and B, respectively |
| Dust mass of RW Aur B at 20 K | 3.1 | not stated | Earth masses | 4 | we obtain a dust mass of $23.9\,M_\oplus$ and $3.1\,M_\oplus$ for A and B, respectively |
| Dust mass of RW Aur A using mean Tb of 27 K | 16.4 | not stated | Earth masses | 4 | with an average brightness temperature of RW Aur A within its $R_{90\%}$ of 27 K, the dust mass becomes $16.4\,M_\oplus$ |
| Disk-disk misalignment (angular momentum same side) | 9.15 | not stated | deg | 3 | we find a misalignment of $9.15$ deg, or $118.8$ deg if they point in different directions |
| Inner-outer disk inclination difference, RW Aur A | 6.0 | 0.4 | deg | 5 | with a relative difference of $6.0\pm0.4$ deg between the inner and outer disk |
| Inner-outer disk position angle difference, RW Aur A | 4.0 | 0.6 | deg | 5 | a difference in PA of $4.0\pm0.6\,$deg |
| Dynamical mass of RW Aur A | 1.238 | a fraction of a percent (formal) | Msun | 6 | we obtain $M_A=1.238\,M_\odot$ and $VLSR_A=6172.44\,$m s$^{-1}$ |
| Dynamical mass of RW Aur B | 0.995 | a fraction of a percent (formal) | Msun | 6 | for RW Aur B we obtain $M_B=0.995\,M_\odot$ and $VLSR_A=5218.24\,$ m s$^{-1}$ |
| Peak of 12CO moment 0 in RW Aur A | 113 | 4 | mas | 7 | we obtained a peak at $113\pm{4}$ mas (about 18 au) for RW Aur A |
| 12CO R68% of RW Aur A | 327 | 25 | mas | 7 | $R_{A, CO, 68\%}=327\pm25\,$mas |
| 12CO R90% of RW Aur A | 456 | 64 | mas | 7 | $R_{A, CO, 90\%}=456\pm64\,$mas |
| 12CO R68% of RW Aur B | 238 | 29 | mas | 7 | $R_{B, CO, 68\%}=238\pm29\,$mas |
| 12CO R90% of RW Aur B | 343 | 60 | mas | 7 | $R_{B, CO, 90\%}=343\pm60\,$mas |
| Gas-to-dust size ratio (both disks) | 3.7 | not stated | dimensionless | 7 | both disks have a gas-to-dust size ratio of 3.7 |
| ALMA relative radial velocity of B w.r.t. A | -0.954 | 0.1 (adopted 1 sigma) | km/s | 8 | This radial velocity was assigned to RW Aur B with a value of $-0.954$ km s$^{-1}$ |
| Rate of relative motion of RW Aur B away from A | 3 | not stated | mas/yr | 3 | at an approximate rate of 3 mas yr$^{-1}$ (about 0.5 au yr$^{-1}$ in sky-projected distance) |
| Periastron distance d_peri (best) | 55.0 | +477.5/-27.0 | au | 8 | $55.0_{-27.0}^{+477.5}$ |
| Eccentricity (best) | 0.787 | +1.155/-0.284 | dimensionless | 8 | $0.787_{-0.284}^{+1.155}$ |
| Orbital inclination (best) | 129.8 | +21.2/-29.9 | deg | 8 | $129.8_{-29.9}^{+21.2}$ |
| Longitude of ascending node (best) | 73.8 | +73.7/-21.0 | deg | 8 | $73.8_{-21.0}^{+73.7}$ |
| Argument of periastron (best) | 42.3 | +77.6/-5.4 | deg | 8 | $42.3_{-5.4}^{+77.6}$ |
| Time since last periastron (relative to beginning of 2024) | 295 | +21/-74 | yr | 8 | which occurred $295_{-74}^{+21}$ yr ago relative to beginning of 2024 |
| Orbital period for elliptical orbits (t_peri>0) | 2773 | +27100/-366 | yr | 8 | we estimate that the period is $2773_{-366}^{+27100}$ yr |
| Parallax adopted in orbit fit | 6.406 | 0.044 | mas | 8 | $6.406 \pm 0.044$ |
| Total mass adopted in orbit fit | 2.233 | 0.05*sqrt(2) | Msun | 8 | $2.233 \pm 0.05\cdot\sqrt{2}$ |
| Relative likelihood of best hyperbolic vs best elliptical models | 0.28 | not stated | dimensionless | 9 | we find that the best hyperbolic models are 0.28 times as likely as the best elliptical models to be the solution that minimizes the information loss |
| Confidence that elliptical orbits are preferred over hyperbolic | ~1.1 | not stated | sigma | 9 | there is a $\sim1.1\sigma$ of confidence that elliptical orbits are preferred over hyperbolic orbits |
| Disk-binary misalignment (RW Aur A) | 27.1 | 26.7 (1 sigma dispersion) | deg | 10 | we obtain a disk-binary misalignment of ${27.1}\pm26.7$ deg |

## Qualitative findings

- 12CO shows an intricate system of tidal arcs, filaments and diffuse emission extending beyond 2000 au from RW Aur A, which favours bound (elliptical) solutions  
  > "into an intricate system of tidal arcs, filaments, and an extended diffuse background emission, which extends farther than 2000 au in projected distance from RW Aur A" (Results: 12CO J=2-1 emission)
- Neither disk is centrally peaked in 12CO moment 0, unexpected for RW Aur A where dust is centrally peaked  
  > "The high angular resolution $^{12}$CO moment 0 after continuum subtraction shows that neither of the disks is centrally peaked" (Results: 12CO J=2-1 emission)
- The last interaction was most likely prograde relative to RW Aur A; strongly retrograde excluded  
  > "We exclude the scenario of a strong retrograde interaction." (Discussion: Orientation of the orbit, disks, and jet emission)

## Claim tuples

- H: Is the RW Aur binary bound (elliptical orbit) or unbound (hyperbolic fly-by)? | E: MCMC orbit fit to ALMA disk-center astrometry, historical astrometry and one ALMA radial velocity, plus AIC comparison and fits without ALMA astrometry | R: Highest-likelihood solutions have ecc 0.5 to 0.95; hyperbolic tail allowed; hyperbolic best models 0.28 times as likely (~1.1 sigma preference for elliptical) | F: Most likely a high-eccentricity bound orbit with last periastron about 295 yr ago, but hyperbolic orbits are not ruled out | **partially**
- H: Can multi-epoch ALMA visibility modeling detect the relative motion of the two disks? | E: Joint visibility fit of five epochs with per-epoch disk centers | R: RW Aur B moves toward the southwest relative to A at about 3 mas/yr | F: A consistent relative motion is detected in ALMA astrometry | **supported**
- H: Does the inner disk of RW Aur A show a warp from the close interaction? | E: Visibility fit allowing the central Gaussian a separate inclination and PA | R: Inner component is 6.0+/-0.4 deg more inclined; peak residual falls from 6 to 5 sigma | F: A tentative 6 deg warp in the inner 3 au, consistent with the recent interaction | **partially**
- H: How large and compact are the two dust disks? | E: Parametric visibility modeling of the LB1-dominated continuum | R: R90% = 19 au (A) and 14 au (B); B has a ring at about 6.5 au | F: Both disks are compact; B shows a narrow ring | **supported**
- H: Is the narrow ring around RW Aur B due to material captured from RW Aur A's disk? | E: Compare ring and low brightness temperature of B with the orbit solutions and literature simulations | R: Ring peaks at about 6 au; B brightness temperature at most 15 K versus 120 K for A | F: Suggestive of captured material, labeled speculative and untested | **partially**

## Reasoning

- Why this data: Multi-epoch high-resolution 1.3 mm data trace both gas and dust and give astrometry from disk centers  
  > "This study uses ALMA observations at 1.3 mm at high angular resolution" (Introduction)
- Why this method: Two Gaussian rings chosen for RW Aur B because a broken Gaussian gives a very steep inner edge  
  > "However, this model returns a very steep inner edge to try to compensate for the slow decrease of its outer edge (cite: kurtovic2021)." (Results: Continuum visibility modeling)
- Alternative: Broken Gaussian ring for RW Aur B rejected in favour of two Gaussian rings  
  > "A possible parameterization for the dust continuum ring could have been made with a broken Gaussian" (Results: Continuum visibility modeling)
- Alternative: ALMA and Gaia DR3 astrometry not combined in one orbit fit because of a 6 mas offset  
  > "The astrometry of both instruments was not combined in a single fit, because of a non-negligible difference in astrometry between ALMA and *Gaia* DR3 of about 6mas" (Results: RW Aur B orbit, excluding ALMA astrometry)
- Alternative: Two historical astrometric points (1991 and 1944) excluded as outliers  
  > "We excluded two outlier measurements from the historical astrometric positions" (Results: RW Aur B orbit, with ALMA astrometry)
- How they decided it was enough: MCMC stopped once the probability density from all walkers was stable, although individual walkers had not converged  
  > "However, the probability density distribution derived from the walkers positions reached stable values after $>10^7$ steps." (Results: RW Aur B orbit, with ALMA astrometry)
- Limitation (authors): Dust mass of RW Aur A is only a lower limit because optically thin emission fails  
  > "the assumption of optically thin emission fails, and we can therefore only provide a lower limit to its dust mass" (Results: Dust continuum emission)
- Limitation (authors): Low frequency resolution produces a channelization problem and unrealistically small eddy uncertainties  
  > "This effect makes it challenging to obtain a meaningful uncertainty from the ALMA cube" (Results: RW Aur B orbit, with ALMA astrometry)
- Limitation (authors): Individual MCMC walkers did not converge in the orbit fit  
  > "we did not achieve convergence for each walker separately, in particular, in the low likelihood regime for $\Omega$" (Results: RW Aur B orbit, with ALMA astrometry)
- Limitation (authors): Axisymmetric RW Aur A model leaves asymmetric residuals that could shift the recovered disk center  
  > "These residuals are problematic, because an asymmetry in the inner disk region could slightly shift the recovered center of the disk." (Discussion: Astrometry with ALMA)
- Limitation (authors): Cannot confirm warped or tidally induced gas velocity structure  
  > "Due to the low-frequency resolution, we are unable to confirm or exclude warped or tidally induced velocity structures" (Discussion: Evidence of interaction in the 12CO emission)
- Caveat (inferred, ours): Orbit constraint rests on a handful of ALMA epochs whose spacing is not monotonic (SB1 to SB4 relative distances), and the paper itself attributes this to possible inner-disk asymmetries
- Caveat (inferred, ours): ALMA and Gaia DR3 astrometry disagree by about 6 mas and were never combined, so the final orbit relies on assuming disk centers equal stellar positions
- Caveat (inferred, ours): Eddy masses carry tiny formal errors yet set the total mass prior; real systematic uncertainty is larger
- Caveat (inferred, ours): Visibility weights across cycles were not standardized as the paper itself later recommends
- Caveat (inferred, ours): Warp significance is based on one model comparison with a 6 sigma to 5 sigma residual change and no formal model comparison

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Self-calibrated measurement sets and FITS images (with and without JvM) released on Zenodo; raw data are from five ALMA projects  
  > "All the selfcalibrated products, including measurement sets and fits files (with and without JvM correction) are available for download at <https://doi.org/10.5281/zenodo.12825068>." (Footnote 2)
- Missing: Self-calibration solution intervals, rounds and CLEAN masks (partly bypassed by the Zenodo self-calibrated products)
- Missing: MCMC walker counts, steps, bounds, likelihood and weighting for the visibility fit
- Missing: Historical astrometry values used (only the compilation citation and the two excluded points)
- Missing: Origin of the parallax and total-mass priors and the radial-velocity measurement method
- Missing: No analysis code released; only data products
- Data volume (inferred): Roughly 100-300 GB of raw ALMA data for 5 projects and 14 execution blocks (long-baseline LB1 is the largest); a few GB from the Zenodo self-calibrated products
- Score (inferred): 3/5, Public ALMA projects and Zenodo self-calibrated products plus full model equations and numeric tables, but key MCMC and imaging settings, priors for the orbit fit, and historical astrometry values are missing and no code is released.
- Rediscovery candidate: yes, Data are stated available (ALMA projects and Zenodo products), the visibility-fit and orbit-fit recipes are largely described, and results are numeric tables (disk sizes, fluxes, orbital elements).

## Links

- Method: Tazzari et al. 2017, A&A, 606, A88 (cite: Tazzari2017) (galario visibility modeling code)
- Method: Foreman-Mackey et al. 2013, PASP, 125, 306 (cite: emcee2013) (emcee MCMC sampler)
- Method: Teague 2019, JOSS, 4, 1220 (cite: eddy) (eddy Keplerian rotation fitting)
- Method: Teague & Foreman-Mackey 2018 (cite: bettermoments) (bettermoments moment and peak maps)
- Method: Rein & Liu 2012; Rein & Spiegel 2015 (cite: rein2012; rein2015) (rebound orbit calculation)
- Method: Czekala et al. 2021, ApJS, 257, 2 (cite: czekala2021) (JvM correction)
- Companion: Rodriguez et al. 2018, ApJ, 859, 150 (cite: rodriguez2018) (Earlier publication of SB1 and SB2 and the 12CO features)
- Companion: Long et al. 2019, ApJ, 882, 49 (cite: long2019) (Taurus survey containing SB3)
- Companion: Manara et al. 2019, A&A, 628, A95 (cite: manara2019) (Taurus survey containing SB3 and disk sizes)
- Companion: Csepany et al. 2017, A&A, 603, A74 (cite: csepany2017) (Compilation of historical RW Aur A-B astrometry)
- Related: ALMA Taurus survey (Long et al. 2019; Manara et al. 2019)

## Checks

```json
{
 "quotes": 209,
 "quotes_ok": 209,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 2,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 53,
 "numeric_problems": 0,
 "fill": {
  "facts": 138,
  "stated": 108,
  "rate": 0.783
 },
 "evidence_ok": true
}
```
