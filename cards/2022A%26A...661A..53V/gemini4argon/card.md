# Survey of Orion Disks with ALMA (SODA). I. Cloud-level demographics of 873 protoplanetary disks

`2022A&A...661A..53V` | Astronomy and Astrophysics 2022 | first author: van Terwisga, S. E. | arXiv: 2202.11057 | DOI: 10.1051/0004-6361/202141913

Card schema 1.0 | model gemini-4-argon | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What is the disk dust mass distribution across 873 Class II protoplanetary disks in the L1641 and L1647 regions of the Orion A cloud, and how do median disk masses vary with position, YSO clustering, and compared to nearby star-forming regions?  
  > "We conduct a survey of the unresolved millimeter continuum emission of 873 protoplanetary disks identified by *Spitzer* in the L1641 and L1647 regions of the Orion A cloud." (abstract); "This is the largest such survey yet, allowing us to identify even weak trends in the median disk mass as a function of position in the cloud and cluster membership." (abstract); "In particular, it is difficult to say if disks are formed with some universal initial mass distribution, which then evolves similarly in the absence of external photoevaporation" (Introduction)
- Target **873 Class II protoplanetary disks in Orion A (L1641 and L1647)**: coordinates below -6 deg in declination, or above l ~ 209.5 deg in Galactic longitude  
  > "We selected all Class II YSOs from (cite: megeath12) located in Orion A and below $-6^{\circ}$ degrees in declination, or above $\ell \sim 209.5^{\circ}$ degrees in Galactic longitude." (Sample selection); "YSOs with well-known distances from DR2 are placed in 16 bins in galactic longitude (oversampled by a factor of two), and the distances of the YSOs in our sample are interpolated based on the distances of these bins." (The distance structure of Orion A); z/distance 384 - 454 pc (interpolated in galactic longitude bins)  
  > "We selected all Class II YSOs from (cite: megeath12) located in Orion A and below $-6^{\circ}$ degrees in declination, or above $\ell \sim 209.5^{\circ}$ degrees in Galactic longitude." (Sample selection); "YSOs with well-known distances from DR2 are placed in 16 bins in galactic longitude (oversampled by a factor of two), and the distances of the YSOs in our sample are interpolated based on the distances of these bins." (The distance structure of Orion A); distance from Gaia DR2 interpolated following Großschedl et al. (2018)  
  > "We selected all Class II YSOs from (cite: megeath12) located in Orion A and below $-6^{\circ}$ degrees in declination, or above $\ell \sim 209.5^{\circ}$ degrees in Galactic longitude." (Sample selection); "YSOs with well-known distances from DR2 are placed in 16 bins in galactic longitude (oversampled by a factor of two), and the distances of the YSOs in our sample are interpolated based on the distances of these bins." (The distance structure of Orion A)

## Data provenance

- ALMA projects: 2019.1.01813.S
- bands: Band 6 (225 GHz)  
  > "The sample was observed with the Atacama Large Millimeter/submillimeter Array (ALMA) at 225 GHz, with a median rms of $0.08$ mJy beam$^{-1}$, or $1.5\,\textrm{M}_{\oplus}$." (abstract); "All of our targets were observed in Band 6 including 4 spectral windows centered at frequencies of 224, 226, 240, and 242 GHz, respectively" (Observations)
- frequencies and spectral setup: 4 spectral windows centered at 224, 226, 240, and 242 GHz, each with 1.8 GHz bandwidth and 31 MHz resolution  
  > "All of our targets were observed in Band 6 including 4 spectral windows centered at frequencies of 224, 226, 240, and 242 GHz, respectively, each with total bandwidth of 1.8 GHz and resolution of 31 MHz." (Observations)
- continuum bandwidth: 4 x 1.8 GHz  
  > "All of our targets were observed in Band 6 including 4 spectral windows centered at frequencies of 224, 226, 240, and 242 GHz, respectively, each with total bandwidth of 1.8 GHz and resolution of 31 MHz." (Observations)
- arrays: 12m-array  
  > "All observations were carried out with the most compact 12m-array configuration (C43-1) with a minimum of 41 antennas" (Observations)
- configurations: C43-1  
  > "All observations were carried out with the most compact 12m-array configuration (C43-1) with a minimum of 41 antennas" (Observations)
- baselines: _not stated_
- angular resolution: ~ 1.4" x 1.1" (580 AU x 414 AU)  
  > "The individual maps show typical synthesized beam sizes of $\sim$ 1.4” $\times$ 1.1”, that is, approximately 580 AU $\times$ 414 AU at the distance of Orion." (Parallel data reduction at the SURFsara Data Processing Facility)
- max recoverable scale: 10.9"  
  > "The primary beam for this configuration is $\sim 1.1''$, with a Maximum Recoverable Scale (MRS) of $10.9''$." (Observations)
- sensitivity: 0.08 mJy beam^-1 (1.5 M_earth at 4 sigma)  
  > "The sample was observed with the Atacama Large Millimeter/submillimeter Array (ALMA) at 225 GHz, with a median rms of $0.08$ mJy beam$^{-1}$, or $1.5\,\textrm{M}_{\oplus}$." (abstract); "The typical noise level of our maps is 0.08 mJy beam$^{-1}$ which translates into a median sensitivity threshold of $1.5\,M_{\oplus}$ at the 4$\sigma$ level for our adopted opacities (see Section 4.1.1)." (Parallel data reduction at the SURFsara Data Processing Facility)
- time on source: ~ 30 sec per target  
  > "We observe each target of our sample with a single ALMA 12-m array pointing for a total integration time of approximately 30 sec on source." (Observations)
- observing dates: November 21 to December 2, 2019  
  > "We observed the 873 SODA disks using ALMA (Project ID: 2019.1.01813.S, PI: S. van Terwisga) between November 21 and December 2 2019 as part of Cycle 7." (Observations)
- pi or archival as stated: PI: S. van Terwisga  
  > "We observed the 873 SODA disks using ALMA (Project ID: 2019.1.01813.S, PI: S. van Terwisga) between November 21 and December 2 2019 as part of Cycle 7." (Observations)
- Other facility **Spitzer Space Telescope**: Input YSO catalog and infrared classifications  
  > "As most other similar studies, this survey relies on a *Spitzer* survey of YSO colors, which is sensitive to the (optically thick) emission from warm dust in the inner disk, conducted by (cite: megeath12)." (Survey design)
- Other facility **Herschel Space Observatory (HOPS)**: Longer-wavelength observations to refine YSO classifications of embedded sources  
  > "To correct for this effect, we refined the classifications from (cite: megeath12) to include the observations from the *Herschel* Orion Protostars Survey (HOPS) (cite: furlan16) at longer wavelengths, targeting embedded sources." (Sample selection)
- Other facility **VISTA (VISION survey)**: Near-infrared (J, H, Ks) images for visual overlays and multiplicity checks  
  > "The top panel shows, for each source, the ALMA contours on top of near-infrared (J, H, K$_s$) images from the Vienna Survey in Orion (VISION) using the VISTA telescope (cite: meingast16)." (Results)
- Other facility **Gaia**: DR2 and EDR3 parallaxes and astrometry for distance interpolation and astrometric fidelity  
  > "YSOs with well-known distances from DR2 are placed in 16 bins in galactic longitude (oversampled by a factor of two), and the distances of the YSOs in our sample are interpolated based on the distances of these bins." (The distance structure of Orion A); "Even with *Gaia* EDR3 the fraction of sources with accurate astrometry is fairly low: 284/873, using version 1.0 of the astrometric fidelity classifier presented in (cite: rybizki21)" (Disk masses in YSO clusters)
- External data: Spitzer YSO catalog in Orion A  
  > "We selected all Class II YSOs from (cite: megeath12) located in Orion A and below $-6^{\circ}$ degrees in declination, or above $\ell \sim 209.5^{\circ}$ degrees in Galactic longitude." (Sample selection) [from (cite: megeath12)]
- External data: Herschel Orion Protostars Survey (HOPS) classifications  
  > "To correct for this effect, we refined the classifications from (cite: megeath12) to include the observations from the *Herschel* Orion Protostars Survey (HOPS) (cite: furlan16) at longer wavelengths, targeting embedded sources." (Sample selection) [from (cite: furlan16)]
- External data: ALMA survey of 104 Herschel-detected Class II disks in L1641  
  > "Recently, (cite: grant21) surveyed protoplanetary disks in L1641 with ALMA for the first time. Their sample consists of 104 Class II candidates from  that were also detected by *Herschel* at 70 $\mu$m." (Introduction) [from (cite: grant21)]
- External data: Class III YSO catalog in L1641 from XMM-Newton  
  > "In this section, we use the (cite: pillitteri13) catalog for Class III source numbers, and (cite: tobin20) for all embedded sources (Class I and 0)." (Discussion) [from (cite: pillitteri13)]
- External data: Class 0 and Class I protostellar disk masses and numbers in Orion from VANDAM  
  > "In this section, we use the (cite: pillitteri13) catalog for Class III source numbers, and (cite: tobin20) for all embedded sources (Class I and 0)." (Discussion); "Figure 13 extends this comparison between the SODA sample and Class II disk masses in other nearby star-forming regions, as well as the Class 0 and Class I disk mass distributions in Orion A and B presented by (cite: tobin20)." (Star-forming regions in Orion A and B) [from (cite: tobin20)]
- External data: Upper Sco disk mass catalog and Class III/II ratio  
  > "we artificially construct a sample of disks by randomly sampling (with replacement) disks from both the $\ell > 213.1^{\circ}$ area in Orion, and from the Upper Sco catalog published by (cite: barenfeld16)." (Impact of age gradients); "Using a Class III to Class II ratio for Upper Sco of 4.2 (cite: luhman22) and $\sim 1$ for the southern L1641 sample leads to an $N_{III}/N_{II}$ ratio of $\sim 2$ for the mixed sample" (Impact of age gradients) [from (cite: barenfeld16); (cite: luhman22)]
- External data: Disk mass surveys of nearby star-forming regions (Lupus, Taurus, Cha I, rho Oph, CrA, OMC-2, ONC, NGC 2024, lambda Ori)  
  > "This behavior was seen in surveys of disks at submillimeter wavelengths in the Taurus (cite: andrews13), Lupus (cite: ansdell16; ansdell18), and Chamaeleon I (cite: pascucci16) SFRs, as well as (more recently) the Corona Australis (cite: cazzoletti19) and $\rho$ Ophiuchus (cite: cieza19; williams19) regions." (Introduction) [from (cite: andrews13; ansdell16; pascucci16; cazzoletti19; cieza19; williams19; mann14; eisner18; vanterwisga19b; vanterwisga20; ansdell20)]

## Processing

### Calibration

- pipeline or manual: facility-provided scripts executed in parallel across 6 SBs  
  > "First, each of the 6 SB are independently calibrated using facility-provided scripts in order to recreate their corresponding visibilities." (Parallel data reduction at the SURFsara Data Processing Facility)
- casa version: v5.6.1  
  > "Each imaging process is run using an independent realization of CASA v5.6.1 and distributed over multiple cores and nodes by a Grid-based processing environment." (Parallel data reduction at the SURFsara Data Processing Facility)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0725-0054  
  > "Pointing, bandpass, and flux calibrations (J0725-0054) were carried out at the beginning of each SB." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "We deconvolved each of our target fields with the CASA task *tclean* using standard Briggs weighting and a robust parameter of 0.5." (Parallel data reduction at the SURFsara Data Processing Facility)
- deconvolver: _not stated_
- weighting robust: Briggs weighting, robust = 0.5  
  > "We deconvolved each of our target fields with the CASA task *tclean* using standard Briggs weighting and a robust parameter of 0.5." (Parallel data reduction at the SURFsara Data Processing Facility)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied to each resulting image  
  > "Each of the resulting images is then corrected by their corresponding primary beam response." (Parallel data reduction at the SURFsara Data Processing Facility)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ~ 1.4" x 1.1"  
  > "The individual maps show typical synthesized beam sizes of $\sim$ 1.4” $\times$ 1.1”, that is, approximately 580 AU $\times$ 414 AU at the distance of Orion." (Parallel data reduction at the SURFsara Data Processing Facility)
- final rms: 0.08 mJy beam^-1  
  > "The typical noise level of our maps is 0.08 mJy beam$^{-1}$ which translates into a median sensitivity threshold of $1.5\,M_{\oplus}$ at the 4$\sigma$ level for our adopted opacities (see Section 4.1.1)." (Parallel data reduction at the SURFsara Data Processing Facility)

### Inherited from earlier work

- False positive rate calculation for alignment with background submillimeter galaxies  
  > "This false positive rate includes both pure noise and the chance alignment of an IR excess source in the input catalog with a submillimeter galaxy in the background, following (cite: sadavoy19)." (Flux extraction) [from (cite: sadavoy19)]
- Effective dust temperature assumption of T_dust,eff = 20 K  
  > "For this survey, we assume $T_{\rm{dust, eff}} = 20$ K. This is based on the result in (cite: andrews05) for disks in Taurus, and followed by most other disk surveys." (Temperature and opacity assumptions for disk masses) [from (cite: andrews05)]
- Dust grain opacity kappa_230GHz = 2.3 cm^2 g^-1 and beta = 1  
  > "Here, we used common assumptions on the opacities of the grains, derived from (cite: beckwith90): $\kappa_{\nu = 230\,\rm{GHz}} = 2.3$ cm$^2$ g$^{-1}$, and a power-law frequency-dependence with $\beta = 1$." (Temperature and opacity assumptions for disk masses) [from (cite: beckwith90)]
- Distance interpolation in galactic longitude bins using Gaia DR2  
  > "To solve this problem, we use the same approach as (cite: grossschedl18): YSOs with well-known distances from DR2 are placed in 16 bins in galactic longitude (oversampled by a factor of two), and the distances of the YSOs in our sample are interpolated based on the distances of these bins." (The distance structure of Orion A) [from (cite: grossschedl18)]
- Subtracting data from a constant to handle left-censored data in log-rank tests  
  > "For log-rank correlation tests, we follow (cite: feigelson85) in subtracting our data from a constant, since `lifelines` only implements this test for right-censored data." (Disk mass distribution in SODA) [from (cite: feigelson85)]

### Not stated but needed to reproduce (our reading)

- tclean image size and pixel/cell size
- tclean stopping threshold, niter, and masking strategy
- Whether any spectral channels were flagged for line contamination before continuum imaging
- Exact distance values for each of the 16 galactic longitude bins used for interpolation
- Specific software or fitter used for the parametric Weibull and log-normal censored distribution fits (lifelines or custom)
- Software implementation and exact distance scaling metric used for the OPTICS clustering algorithm

## Analysis recipe

1. **Calibrate visibilities and image continuum for all 882 pointings in parallel**: Parallel calibration of 6 Scheduling Blocks using facility-provided scripts, extraction of individual target fields, and parallel deconvolution of each target combining all 4 continuum spectral windows  
  > "First, each of the 6 SB are independently calibrated using facility-provided scripts in order to recreate their corresponding visibilities. Second, each target field is extracted from the visibility file and individually imaged using identical cleaning parameters (see below)." (Parallel data reduction at the SURFsara Data Processing Facility); "For all our targets, we combine the four available continuum spectra windows in order to maximize the sensitivity of our maps, but did not further spectrally average them." (Parallel data reduction at the SURFsara Data Processing Facility)
   - software: CASA, tclean
   - parameter: Briggs weighting with robust = 0.5  
  > "We deconvolved each of our target fields with the CASA task *tclean* using standard Briggs weighting and a robust parameter of 0.5." (Parallel data reduction at the SURFsara Data Processing Facility)
   - parameter: Primary beam correction applied  
  > "Each of the resulting images is then corrected by their corresponding primary beam response." (Parallel data reduction at the SURFsara Data Processing Facility)
   - fitting: _not stated_
   - validation: Visual inspection of reconstructed images for issues  
  > "After imaging, we inspected the images for issues, but did not identify any." (Parallel data reduction at the SURFsara Data Processing Facility)
2. **Extract continuum fluxes and check for resolved emission**: Search for brightest pixel within a 1.4" radius around catalog position; adopt 4 sigma detection threshold; fit double Gaussians to check for resolved emission  
  > "To identify disks, we search within a 1.4” radius around the catalog position for the brightest pixel in the reconstructed image. We use a $4\sigma$ detection limit, in order to ensure the number of false positive detections is $< 1$ for our dataset." (Flux extraction); "To test the validity of this hypothesis, we fit double Gaussians to the emission, using the location of the peak emission as a prior." (Flux extraction)
   - parameter: Search radius = 1.4"  
  > "To identify disks, we search within a 1.4” radius around the catalog position for the brightest pixel in the reconstructed image." (Flux extraction)
   - parameter: Detection limit = 4 sigma  
  > "We use a $4\sigma$ detection limit, in order to ensure the number of false positive detections is $< 1$ for our dataset." (Flux extraction)
   - assumption: Unresolved continuum emission for Class II disks  
  > "The assumption of unresolved flux is based on observations of nearby star-forming regions at higher resolution, which find median dust emission extents of $\sim 60$ AU" (Flux extraction)
   - fitting: Double Gaussian fit with peak emission location as a prior  
  > "To test the validity of this hypothesis, we fit double Gaussians to the emission, using the location of the peak emission as a prior." (Flux extraction)
   - validation: Check if best-fit axis ratios are inconsistent at the 4 sigma level with unresolved emission (found 14 objects)  
  > "We identify only 14 objects which have SEDs consistent with Class II objects and best-fit axis ratios inconsistent at the 4$\sigma$ level with the assumption of unresolved emission." (Flux extraction)
3. **Calculate disk dust masses**: Convert 225 GHz continuum flux densities (and 4 sigma upper limits) to dust masses using optically thin greybody equation and interpolated Gaia DR2 distances  
  > "Generally, disk masses are inferred by assuming that their millimeter continuum flux is optically thin, with a known opacity and distance. In this case, the mass is found from: $$\begin{equation} \label{eq:mass} M_{\rm{dust}} = \frac{F_{\nu} d^2}{\kappa_{\nu} B_{\nu}(T_{\rm{dust, eff}})} \end{equation}$$" (Disk luminosities and masses); "YSOs with well-known distances from DR2 are placed in 16 bins in galactic longitude (oversampled by a factor of two), and the distances of the YSOs in our sample are interpolated based on the distances of these bins." (The distance structure of Orion A)
   - parameter: 16 galactic longitude bins (oversampled by factor of 2) for distance interpolation  
  > "YSOs with well-known distances from DR2 are placed in 16 bins in galactic longitude (oversampled by a factor of two), and the distances of the YSOs in our sample are interpolated based on the distances of these bins." (The distance structure of Orion A)
   - assumption: Optically thin 225 GHz dust continuum emission  
  > "Generally, disk masses are inferred by assuming that their millimeter continuum flux is optically thin, with a known opacity and distance." (Disk luminosities and masses)
   - assumption: Effective dust temperature T_dust,eff = 20 K  
  > "For this survey, we assume $T_{\rm{dust, eff}} = 20$ K." (Temperature and opacity assumptions for disk masses)
   - assumption: Dust opacity kappa_230GHz = 2.3 cm^2 g^-1 with power-law index beta = 1  
  > "Here, we used common assumptions on the opacities of the grains, derived from (cite: beckwith90): $\kappa_{\nu = 230\,\rm{GHz}} = 2.3$ cm$^2$ g$^{-1}$, and a power-law frequency-dependence with $\beta = 1$." (Temperature and opacity assumptions for disk masses)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit nonparametric and parametric disk mass distributions and compare populations**: Estimate censored cumulative disk mass distributions using the Kaplan-Meier estimator, fit parametric log-normal and Weibull distributions, and compare distributions using log-rank tests  
  > "Figure 6 shows the inferred disk mass distribution using the Kaplan-Meier estimator for the full SODA Class II sample of 873 disks." (Disk mass distribution in SODA); "Throughout this section and in the following, we use the `lifelines` Python package (cite: lifelines) for fitting the (censored) disk mass distributions. For log-rank correlation tests, we follow (cite: feigelson85) in subtracting our data from a constant, since `lifelines` only implements this test for right-censored data." (Disk mass distribution in SODA); "Interestingly, Figure 7 shows that SODA sample is not best described by a log-normal distribution, but by a Weibull distribution." (Disk mass distribution in SODA)
   - software: lifelines
   - parameter: p = 0.05 cutoff for log-rank statistical significance  
  > "Two results are readily apparent (and confirmed statistically, using a cutoff of $p = 0.05$ in a log-rank test)" (Comparison to literature results)
   - assumption: Censoring is independent of disk mass for Kaplan-Meier, or underlying distribution is parametric (log-normal or Weibull)  
  > "If we can fit log-normal distributions to our observed disk populations, the mass-dependent censoring problem is less relevant." (Disk mass distribution in SODA)
   - fitting: Kaplan-Meier nonparametric estimator and two-parameter log-normal and Weibull parametric fits  
  > "Figure 7 shows the quantile-quantile plots of the empirical distribution of source masses versus a Weibull (top panel) and log-normal (bottom panel) distribution fit to the data." (Disk mass distribution in SODA)
   - validation: Akaike Information Criterion (AIC) comparison and quantile-quantile plots between Weibull and log-normal fits  
  > "That the Weibull distribution is indeed a better fit is confirmed from a comparison of the Akaike Information Criterion (AIC): $\Delta_{\rm{AIC}} = 16$ in favor of the Weibull distribution." (Disk mass distribution in SODA)
5. **Analyze spatial variations along galactic longitude and identify YSO clusters**: Bin sources into galactic longitude bins and identify 2D (RA, Dec) clusters using OPTICS algorithm; fit log-normal distributions to each bin/cluster and compare with Class III and embedded source fractions and simulated mixed populations  
  > "Median disk masses are derived by fitting a log-normal distribution to the mass distribution of objects in each bin, with errors reflecting the errors on the fit." (The distribution of disk masses across the Orion A cloud); "To search for clusters, we used the OPTICS algorithm (cite: optics99). The data distances were scaled, and we required a minimum of five samples in the neighborhood for core points to be considered, as well as a minimum reachability steepness of $\xi = 0.05$. We additionally set a minimum cluster size of 50 members of Class II or earlier." (Disk masses in YSO clusters); "we artificially construct a sample of disks by randomly sampling (with replacement) disks from both the $\ell > 213.1^{\circ}$ area in Orion, and from the Upper Sco catalog published by (cite: barenfeld16)." (Impact of age gradients)
   - parameter: OPTICS min_samples = 5, minimum reachability steepness xi = 0.05, minimum cluster size = 50 members of Class II or earlier  
  > "The data distances were scaled, and we required a minimum of five samples in the neighborhood for core points to be considered, as well as a minimum reachability steepness of $\xi = 0.05$. We additionally set a minimum cluster size of 50 members of Class II or earlier." (Disk masses in YSO clusters)
   - parameter: 10 longitudinal bins listed in Table (209.5 to 214.2 deg)  
  > "209.5 | 71" (Table (disk masses along the cloud))
   - assumption: Gas-to-dust ratio of 100 and 1 Myr evolution timescale from Class I to Class II for mass loss rate estimate  
  > "If we assume the evolution from Class I to Class II takes about 1 Myr and continue to use a gas-to-dust mass ratio of 100, that implies an average disk mass loss rate of $\dot{M} \sim 10^{-8}\,M_{\odot}$ yr$^{-1}$ during this period." (Mass evolution from Class I to Class II in Orion)
   - fitting: Log-normal distribution fit to each longitudinal bin and cluster; linear vs constant trend tested with AICc  
  > "Below $\ell = 212.6^{\circ}$, a linear decrease in median disk mass is marginally favored over a constant median disk mass, with corrected Akaike Information Criteria of AICc $= 14.2$ versus AICc $= 17.6$." (The distribution of disk masses across the Orion A cloud)
   - validation: Bootstrap/random sampling simulation of mixed southern L1641 and Upper Sco populations compared against l = 209 deg bin  
  > "For a ratio $f = 0.68 - 0.84$ between these populations, the median disk mass of the mixed sample is indistinguishable from $\ell = 209^{\circ}$ disks, to within $1\sigma$." (Impact of age gradients)

## Software

- **CASA** v5.6.1: Parallel calibration and imaging of ALMA scheduling blocks and target fields  
  > "Each imaging process is run using an independent realization of CASA v5.6.1 and distributed over multiple cores and nodes by a Grid-based processing environment." (Parallel data reduction at the SURFsara Data Processing Facility)
- **tclean** : Deconvolution of individual target continuum images  
  > "We deconvolved each of our target fields with the CASA task *tclean* using standard Briggs weighting and a robust parameter of 0.5." (Parallel data reduction at the SURFsara Data Processing Facility)
- **lifelines** v0.25.4: Fitting censored disk mass distributions (Kaplan-Meier estimator) and performing log-rank correlation tests  
  > "Throughout this section and in the following, we use the `lifelines` Python package (cite: lifelines) for fitting the (censored) disk mass distributions." (Disk mass distribution in SODA); "(ref: lifelines) Davidson-Pilon, C., Kalderstam, J., Jacobson, N., et al. 2020, CamDavidsonPilon/lifelines: v0.25.4" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Class II disk detection rate | 58 | 2.6 | % | 2 | We detected $58\%$ (502/873) of the observed disks.; In total, we detect 502 of 873 sources ($58 \pm 2.6 \%$) in the sample. |
| Number of detected Class II disks | 502 | not stated | dimensionless | 2 | In total, we detect 502 of 873 sources ($58 \pm 2.6 \%$) in the sample. |
| Number of disks with dust mass > 100 M_earth | 20 | not stated | dimensionless | 3 | This includes 20 disks with dust masses $> 100\,\textrm{M}_{\oplus}$, and two objects associated with extended dust emission.; Figure 1 shows the locations of all disks with masses (assuming optically thin emission) higher than $100\,M_{\oplus}$ in dust in Orion A. We find 20 such objects |
| Dust mass of most massive disk ([MGM2012]-540) | 364 | 0.5 | M_earth | 3 | The most massive object is [MGM2012]-540, with $M_{\textrm{dust}} = 364 \pm 0.5\,M_{\oplus}$. |
| Median disk dust mass (full SODA sample, Kaplan-Meier) | 1.97 | +0.15/-0.19 | M_earth | 4 | Figure 6 shows the inferred disk mass distribution using the Kaplan-Meier estimator for the full SODA Class II sample of 873 disks. We find a median disk dust mass of $1.97 ^{+0.15}_{-0.19} \,M_{\oplus}$. |
| Median disk dust mass (full SODA sample, log-normal fit) | 2.2 | +0.2/-0.2 | M_earth | 4 | By fitting a log-normal distribution to the data, we infer a median disk dust mass in the full sample of $2.2^{+0.2}_{-0.2}\,M_{\oplus}$.; / SODA (all) / 873 / $2.2^{+0.2}_{-0.2}$ / 2.0$\pm$0.1 / |
| Median disk dust mass (full SODA sample, Weibull fit) | 2.2 | 0.19 | M_earth | 4 | However, the values for the median dust mass agree to within their respective errors: these are $2.2 \pm 0.19\,\rm{M}_{\oplus}$ for the Weibull, and $2.2^{+0.17}_{-0.17}$ for the log-normal distribution. |
| Median disk dust mass in L1641 (log-normal fit) | 2.1 | +0.2/-0.2 | M_earth | 4 | In L1641 and L1647, median dust masses are $2.1^{+0.2}_{-0.2}\,M_{\oplus}$ and $2.6^{+0.4}_{-0.5}\,M_{\oplus}$, respectively.; / L1641 (all) / 708 / $2.1^{+0.2}_{-0.2}$ / 2.0$\pm$0.1 / |
| Median disk dust mass in L1647 (log-normal fit) | 2.6 | +0.4/-0.5 | M_earth | 4 | In L1641 and L1647, median dust masses are $2.1^{+0.2}_{-0.2}\,M_{\oplus}$ and $2.6^{+0.4}_{-0.5}\,M_{\oplus}$, respectively.; / L1647 (all) / 165 / $2.6^{+0.4}_{-0.5}$ / 1.9$\pm$0.2 / |
| Median disk dust mass in L1641S (reduced) | 3.2 | +0.4/-0.4 | M_earth | 5 | / L1641S (red.) / 301 / $3.2^{+0.4}_{-0.4}$ / 1.9$\pm$0.1 / |
| Median disk dust mass in L1641N | 1.6 | +0.2/-0.2 | M_earth | 5 | / L1641N / 407 / $1.6^{+0.2}_{-0.2}$ / 2.0$\pm$0.1 / |
| Occurrence rate of extended dust emission morphology in Class II sample | 0.23 | 0.16 | % | 2 | Regardless of the origin of the observed extended dust tails seen in these two sources, the advantage of the size of this homogeneous dataset is that it is possible to say that this kind of morphology must be rare, occurring only $0.23 \pm 0.16 \%$ of the time. |
| Disk mass reduction factor from Class I to Class II | 13 | 3 | dimensionless | 5 | From Class I to Class II, the disk mass is reduced by a factor of $13 \pm 3$, based on these observations. |
| Average disk mass loss rate from Class I to Class II | 10^-8 | not stated | M_sun yr^-1 | 5 | with disk mass loss rates of $\sim 10^{-8}\,\textrm{M}_{\odot}\,\textrm{yr}^{-1}$.; If we assume the evolution from Class I to Class II takes about 1 Myr and continue to use a gas-to-dust mass ratio of 100, that implies an average disk mass loss rate of $\dot{M} \sim 10^{-8}\,M_{\odot}$ yr$^{-1}$ during this period. |

## Qualitative findings

- The SODA Class II disk mass distribution has a heavy high-mass tail (> 100 M_earth) that is better fit by a Weibull distribution than a single log-normal distribution (Delta_AIC = 16).  
  > "Interestingly, Figure 7 shows that SODA sample is not best described by a log-normal distribution, but by a Weibull distribution." (Disk mass distribution in SODA); "It is clear that the difference is driven by the better fit of the Weibull distribution at masses $> 100\,\textrm{M}_{\oplus}$: the SODA sample has a more massive tail than a log-normal distribution can account for." (Disk mass distribution in SODA)
- Disk mass distributions in L1641 and L1647 are statistically indistinguishable, and the previous Herschel-selected L1641 sample of Grant et al. (2021) was biased toward higher disk masses.  
  > "Two results are readily apparent (and confirmed statistically, using a cutoff of $p = 0.05$ in a log-rank test): L1641 and L1647 have highly similar disk mass distributions, and the *Herschel*-detected subsample in L1641 (shown in pink) is indeed biased toward higher disk masses." (Comparison to literature results)
- Median disk masses show only weak variations across ~100 pc along the Orion A cloud and across 6 YSO clusters, with lower disk masses in northern L1641 coinciding with higher Class III/Class II ratios and lower embedded source fractions (consistent with an older foreground population).  
  > "We find only weak trends in disk (dust) masses with galactic longitude and between the Young Stellar Object (YSO) clusters identified in the sample, with median masses varying by $\lesssim 50\%$." (abstract); "toward the northern part of L1641, the disk masses apparently decrease, even as the fraction of Class III sources increases and embedded sources become rarer. This is consistent with earlier results showing an older foreground population toward this region." (Conclusions)
- In the age-homogeneous L1641S (reduced) sample, the disk mass distribution is statistically indistinguishable from those of similar-age nearby low-mass SFRs like Lupus and Taurus, as well as OMC-2.  
  > "Remarkably, the mass distributions for disks in L1641S (reduced) and Lupus are indistinguishable statistically ($p < 0.05$)." (Nearby star-forming regions); "First, it is clear that the median disk mass of the L1641S (reduced) sample is indistinguishable from that in OMC-2, almost on the opposite side of Orion A from the Trapezium." (Star-forming regions in Orion A and B)

## Claim tuples

- H: The previous ALMA survey of Herschel-detected Class II disks in L1641 by Grant et al. (2021) suffered from selection bias toward more massive disks. | E: Observe an unbiased Spitzer-selected sample of 873 Class II disks in L1641 and L1647 with ALMA at 225 GHz and compare its disk mass distribution with the Grant et al. (2021) sample using log-rank tests. | R: SODA finds a median dust mass in L1641 of 2.1 +/- 0.2 M_earth compared to 11.1 M_earth in Grant et al. (2021), while doubling the number of >100 M_earth disks in L1641 from 6 to 16. | F: The Herschel 70 um detection requirement biased the earlier sample toward higher disk masses, while also missing massive disks not covered by HOPS. | **supported**
- H: Spatial variations in median disk dust mass along the Orion A cloud and across YSO clusters are driven by local stellar age variations rather than intrinsic environmental differences. | E: Bin the 873 disks by galactic longitude and into 6 OPTICS-defined spatial clusters, fit log-normal disk mass distributions to each, compare with Class III/Class II and embedded/Class II ratios, and simulate a mixed population using southern L1641 and Upper Sco disks. | R: Median disk masses decrease below l ~ 212 deg (down to 0.9 M_earth at l = 209.5 deg) where Class III ratios rise and embedded fractions drop; a mixed population with ratio f = 0.68 - 0.84 reproduces the l = 209 deg median mass within 1 sigma. | F: Observed variations in median disk mass across L1641/L1647 and between YSO clusters are small and consistent with stellar age gradients or an older foreground population toward northern L1641. | **supported**
- H: In the absence of external photoevaporation from O-type stars, protoplanetary disks form with a universal initial mass distribution and evolve at similar rates across different star-forming regions. | E: Compare the Kaplan-Meier and log-normal disk mass distributions of the age-uniform L1641S (reduced) sample (N=301) to nearby low-mass SFRs (Lupus, Taurus, Cha I, Upper Sco) and other Orion regions (OMC-2, Class I/0 from VANDAM). | R: The L1641S (reduced) median dust mass (3.2 +/- 0.4 M_earth) and distribution are statistically indistinguishable (p < 0.05) from Lupus (3.0 M_earth), Taurus (3.3 M_earth), and OMC-2 (2.9 M_earth), and show a factor of 13 +/- 3 mass drop from Class I (~10^-8 M_sun yr^-1 loss rate). | F: Disk masses are essentially constant across ~100 pc scales in Orion A and match independent nearby SFRs of the same age, supporting universal initial disk mass distributions and evolution rates in non-irradiated environments. | **supported**

## Reasoning

- Why this data: Orion A (L1641 and L1647) contains a large, unbiased Spitzer-identified sample of Class II YSOs spanning ~90 pc away from the ionizing O-stars of the ONC, enabling statistical subsampling by position and clustering with a compact ALMA Band 6 continuum snapshot setup.  
  > "In particular, the part of the cloud consisting of L1641 and L1647 is a key region for studying the properties of disks at $\sim 1$ Myr ages in giant molecular clouds, away from young O-type stars." (Introduction); "This choice of frequencies and array setups maximize the detection of line-free continuum emission from point-like sources in the shortest integration time possible." (Observations)
- Why this method: Parallelizing calibration across 6 SBs and deconvolution across 150 jobs per SB on SURFsara SPIDER reduces processing time by ~2 orders of magnitude, while parametric (log-normal/Weibull) and Kaplan-Meier survival analysis handles censored non-detections.  
  > "The combination of high performance, flexibility, and number of cores at SURFsara-Spider allows us to reduce the total reduction time by 2 orders of magnitude ($\sim 6 \times 150 = 900$ times) compared to standard linear procedures." (Parallel data reduction at the SURFsara Data Processing Facility); "If we can fit log-normal distributions to our observed disk populations, the mass-dependent censoring problem is less relevant." (Disk mass distribution in SODA)
- Alternative: Using CASA in parallel mode (mpicasa) was tested and rejected because it did not improve performance on the SURFsara architecture.  
  > "Independent experiments show that the use of CASA in parallel mode (i.e., mpicasa) does not introduce additional improvements in the SURFsara architecture. Therefore this method is not considered for our data reduction pipeline." (Parallel data reduction at the SURFsara Data Processing Facility)
- Alternative: 3D clustering with Gaia EDR3 astrometry was rejected in favor of 2D (RA, Dec) clustering because only 284/873 sources have high-fidelity astrometry.  
  > "We restrict ourselves to finding clusters in two-dimensional (RA, Dec) space, as a first-order approach that has been successfully used for this dataset before. Even with *Gaia* EDR3 the fraction of sources with accurate astrometry is fairly low: 284/873" (Disk masses in YSO clusters)
- How they decided it was enough: _not stated_
- Limitation (authors): Possible contamination by background galaxies (~24 +/- 12 galaxies or ~2.3%) or offset IR nebulae, which would slightly underestimate the median disk luminosity.  
  > "The inclusion of these types of objects will therefore always lead us to underestimate of the median disk luminosity. The galaxy contamination fraction of the catalog is expected to be approximately $6.1 \pm 3.1$ deg$^{-2}$, or $24 \pm 12$ galaxies in total" (Catalog completeness)
- Limitation (authors): Compact binaries (< 400 AU) are unresolved by both Spitzer and ALMA (1.4" x 1.1" beam), so their fluxes represent combined system luminosities.  
  > "Both the input catalog resolution of $1''$ and the resolution of our ALMA data prevent us from resolving the most compact binaries (with separations $\lesssim 400$ AU)." (Results)
- Limitation (authors): Parts of the disks may be optically thick at 225 GHz, and dust temperature (assumed 20 K) and grain opacity are uncertain, potentially causing disk masses to be underestimated.  
  > "There is now increasing evidence that part of the disk can be optically thick even at the wavelengths used for this survey (e.g., (cite: andrews05; tripathi17; zhu19; macias21), the latter of which find optically thick emission even at 2.1 mm). The net effect of this is that we possibly underestimate our disk masses to some (model-dependent) extent." (Temperature and opacity assumptions for disk masses)
- Limitation (authors): Residual distance uncertainty of ~5% (20 pc) from interpolating Gaia DR2 distances in galactic longitude bins.  
  > "After correcting for the distances structure, we are left with a residual uncertainty in the distance of the sources of $\sim 5\%$ (20 pc), with small variations in galactic longitude." (The distance structure of Orion A)
- Limitation (authors): Limited statistical significance of the median disk mass variations in L1641 and uncertainties in individual stellar ages and stellar masses.  
  > "Ultimately, the limited statistical significance of the median disk mass variations in L1641, the assumptions on the disk mass distribution for 5–10 Myr old disks, and in particular the uncertainties in the (relative) stellar ages of the stars with protoplanetary disks in L1641 prevent us from drawing stronger conclusions." (Impact of age gradients)
- Caveat (inferred, ours): Individual host stellar masses (M_star) are not controlled for when comparing disk mass distributions across subsamples or regions, despite the well-known M_disk - M_star relation.
- Caveat (inferred, ours): Peak pixel search within a 1.4" radius for non-detections versus detections could introduce a slight positive noise bias if not uniformly extracted at the phase center for weak sources.
- Caveat (inferred, ours): Note: In Section 3.1 the text prints 'primary beam for this configuration is ~ 1.1"', which is a typo in the paper for synthesized beam (primary beam at 225 GHz on 12m antennas is ~25").

## Reproducibility

- Data public (paper): Continuum maps in FITS/PNG format are available on the project webpage, and Table 1 catalog is at CDS.  
  > "All our continuum maps are available as png figures and in FITS format on our webpage." (Parallel data reduction at the SURFsara Data Processing Facility); "Table 1 is only available in electronic form at the CDS via anonymous ftp to cdsarc.u-strasbg.fr (130.79.128.5) or via <http://cdsweb.u-strasbg.fr/cgi-bin/qcat?J/A+A/>" (Footnote 1)
- Products in archive: FITS continuum maps on EMERGE project webpage and catalog at CDS  
  > "All our continuum maps are available as png figures and in FITS format on our webpage." (Parallel data reduction at the SURFsara Data Processing Facility); "<https://emerge.alvarohacar.com/results/soda>" (Footnote 5)
- Missing: Exact tclean imaging parameters (cell size, imsize, niter, stopping threshold, mask)
- Missing: Exact script or likelihood used to fit censored log-normal and Weibull distributions
- Missing: Exact coordinate scaling used in OPTICS clustering
- Data volume (inferred): Moderate (~50-150 GB raw visibilities for 6 SBs in compact C43-1 configuration with 31 MHz channels; <5 GB for all 882 continuum FITS images)
- Score (inferred): 85/5, Raw data (2019.1.01813.S), calibrated continuum FITS maps, and the full flux/mass catalog (at CDS) are all public, and the flux extraction and mass conversion equations/assumptions are explicitly given; only minor tclean imaging parameters and the exact censored parametric fitting code are omitted.
- Rediscovery candidate: yes, All raw ALMA data and FITS continuum maps are public, the analysis recipe (peak flux extraction within 1.4", analytic dust mass conversion, Kaplan-Meier and log-normal fitting, and OPTICS clustering) is straightforward and well-specified, and the paper reports precise numeric answer keys.

## Links

- Method: (cite: grossschedl18) (Gaia DR2 distance interpolation method across galactic longitude bins in Orion A)
- Method: (cite: feigelson85) (Survival analysis method for left-censored astronomical data in log-rank tests)
- Method: (cite: optics99) (OPTICS clustering algorithm used to identify YSO clusters)
- Method: (cite: sadavoy19) (False positive rate estimation for background submillimeter galaxy alignment)
- Companion: Hacar et al., in prep. (Upcoming paper describing the implementation of the parallel SURFsara SPIDER reduction pipeline for mosaics and spectral cubes)
- Related: SODA (Survey of Orion Disks with ALMA)
- Related: EMERGE
- Related: HOPS (Herschel Orion Protostars Survey)
- Related: VISION (Vienna Survey in Orion)
- Related: VANDAM

## Checks

```json
{
 "quotes": 140,
 "quotes_ok": 140,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 15,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 102,
  "stated": 83,
  "rate": 0.814
 },
 "evidence_ok": true
}
```
