# On the Magnetic Field Properties of Protostellar Envelopes in Orion

`2024ApJ...963L..31H` | The Astrophysical Journal Letters 2024 | first author: Huang, Bo | arXiv: 2402.07267 | DOI: 10.3847/2041-8213/ad27d4

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: star_formation
- Question: What are the magnetic field (B-field) morphologies of Orion protostellar envelopes, how are they oriented relative to outflows and envelope velocity gradients, and is compact polarization from self-scattering?  
  > "Its main objective is to investigate the role of *B*-fields on spatial scales ranging from 400 to thousands of au, fully encompassing the protostellar envelope surrounding the youngest protostars." (Introduction)
- Target **BOPS sample: 61 protostars in 57 ALMA fields in the Orion molecular clouds**: coordinates listed per source (R.A./Dec.) in the parameters table in the Appendix  
  > "to observe 57 fields, each centered on a different protostar as identified by the VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey of Orion Protostars (cite: tobin2020vla)" (Observations and Data Reduction); "The names and coordinates of these protostars are listed in Table [\[Tab:parameters\]](#Tab:parameters) of Appendix [9](#App:Table)." (Observations and Data Reduction); z/distance 355.4 to 460.0 pc per source (column D of the parameters table)  
  > "to observe 57 fields, each centered on a different protostar as identified by the VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey of Orion Protostars (cite: tobin2020vla)" (Observations and Data Reduction); "The names and coordinates of these protostars are listed in Table [\[Tab:parameters\]](#Tab:parameters) of Appendix [9](#App:Table)." (Observations and Data Reduction); distance from _not stated_
- Target **HH212M**: coordinates 05:43:51.41 -01:02:53.25 (h:m:s, d:m:s)  
  > "HH212M & 05:43:51.41 & -01:02:53.25 & 0.95$\times$0.70 & -70.0 & 429.2" (Table); z/distance 429.2 pc  
  > "HH212M & 05:43:51.41 & -01:02:53.25 & 0.95$\times$0.70 & -70.0 & 429.2" (Table); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: Band 7 (870 um)  
  > "The BOPS (PI: Ian Stephens, 2019.1.00086) survey used ALMA Band 7 (870 $\mu$m) to observe 57 fields" (2 Observations and Data Reduction)
- frequencies and spectral setup: FDM; four spectral windows, two per sideband; spw1 CO (3-2) 345.79599 GHz, 468.75 MHz, 1920 ch, 0.21 km/s; spw2-4 continuum at 348.5, 334.5, 336.5 GHz, 1875 MHz each; C17O (3-2) in spw4  
  > "The observations were taken in Frequency Division Mode (FDM), providing modest spectral resolutions." (2 Observations and Data Reduction); "We used four spectral windows, two in each sideband" (2 Observations and Data Reduction); "1: CO (3–2) | 1920 | 345.79599 | 468.75 | 0.24 | 0.21" (Table)
- continuum bandwidth: 1.875 GHz per spectral window (continuum windows)  
  > "The maximum bandwidth (1.875 GHz per spectral window) was selected for the continuum" (2 Observations and Data Reduction)
- arrays: ALMA compact configurations plus an intermediate configuration of both  
  > "using the ALMA compact configurations C43-1 and C43-2, and an intermediate configuration of both" (2 Observations and Data Reduction)
- configurations: C43-1, C43-2, and an intermediate configuration of both  
  > "using the ALMA compact configurations C43-1 and C43-2, and an intermediate configuration of both" (2 Observations and Data Reduction)
- baselines: about 14 m to 312 m  
  > "which provided baselines between about 14 m and 312 m" (2 Observations and Data Reduction)
- angular resolution: ~400 au (1 arcsec); restoring beams about 0.8-0.97 x 0.65-0.71 arcsec  
  > "with $\sim$400 au (1$\ensuremath{''}$) resolution using the Atacama Large Millimeter/submillimeter Array" (abstract); "HH212M & 05:43:51.41 & -01:02:53.25 & 0.95$\times$0.70 & -70.0" (Table)
- max recoverable scale: _not stated_
- sensitivity: Stokes I noise ~0.1 mJy/beam; Stokes Q and U ~0.07 mJy/beam; Stokes I S/N 750 to 4200  
  > "is strongly detected with a signal-to-noise ratio (S/N) ranging from 750 to 4200 for all targets" (2 Observations and Data Reduction); "which is higher than the noise level of $\sigma_{QU} \sim0.07$ mJy/beam in both the Stokes *Q* and *U* maps" (2 Observations and Data Reduction)
- time on source: _not stated_
- observing dates: November 29, 2019 to December 20, 2019  
  > "Observations were made from November 29, 2019, to December 20, 2019" (2 Observations and Data Reduction)
- pi or archival as stated: PI: Ian Stephens (BOPS survey)  
  > "The BOPS (PI: Ian Stephens, 2019.1.00086) survey used ALMA Band 7" (2 Observations and Data Reduction)
- Line: 12CO J=3-2 (345.79599 GHz)
- Line: C17O J=3-2 (not stated)
- Other facility **VLA / VANDAM Survey**: Sample selection from VLA 9 mm fluxes and VANDAM protostar identification; disk sizes and orientations from 0.1 arcsec observations  
  > "We targeted the brightest Class 0 sources using their VLA, C-array, 9 mm fluxes ($\sim 1\ensuremath{''}$ resolution)." (2 Observations and Data Reduction); "The disk’s major axis angles are derived from high resolution ($0.1\ensuremath{''}$, $\sim$40 au) observations as reported in (cite: tobin2020vla)." (3 Results)
- External data: Disk major-axis position angles (and inclinations) of the protostars from high-resolution VANDAM observations  
  > "The disk’s major axis angles are derived from high resolution ($0.1\ensuremath{''}$, $\sim$40 au) observations as reported in (cite: tobin2020vla)." (3 Results) [from (cite: tobin2020vla)]
- External data: Disk radii of 30 to 250 au for the BOPS sample  
  > "In the BOPS sample, the disks have radii between 30 and 250 au (0.08$''$ and 0.63$''$) (cite: tobin2020vla)." (3 Results) [from (cite: tobin2020vla)]
- External data: Protostar identification and sample selection (VANDAM) and VLA C-array 9 mm fluxes  
  > "as identified by the VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey of Orion Protostars (cite: tobin2020vla)" (2 Observations and Data Reduction) [from (cite: tobin2020vla)]
- Simulation/model as data: 2D simulated intersecting angles uniformly projected from 3D (parallel: 0-22.5 deg; random: 0-90 deg; perpendicular: 67.5-90 deg), self-generated and compared with observed angle differences by K-S test  
  > "compare it with 2D simulated intersecting angles uniformly projected from a three-dimensional space" (3.4 Geometric projection effect)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Three successive rounds of phase-only self-calibration per source, Stokes I image as model, solution intervals 600 s, 30 s, 10 s; 12CO (3-2) flagged before self-cal  
  > "Then we performed three successive rounds of phase-only self-calibration for each source to improve the image quality." (2 Observations and Data Reduction); "with solution intervals set to 600, 30, and 10 seconds for the first, second, and third iterations, respectively" (2 Observations and Data Reduction)

### Imaging

- task: CASA tclean (continuum Stokes I, Q, U and line cubes)  
  > "The dust continuum images were produced using the `tclean` task in CASA (cite: casateam2022casa)" (2 Observations and Data Reduction); "Finally, we performed the `tclean` task to produce Stokes *I*, *Q* and *U* image cubes using self-calibrated, continuum-subtracted data for each spectral window." (2 Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "with a *Briggs* weighting *robust* parameter set to 0.5, which is a good compromise between resolution and sensitivity (cite: Briggs95)" (2 Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in the uv plane on self-calibrated line data  
  > "The `uvcontsub` task was used to perform continuum fitting and subtraction in the UV plane." (2 Observations and Data Reduction)
- line free channels: Continuum channels identified from full non-channel-averaged dirty cubes; channels exceeding 1.5 times the continuum baseline flagged after third self-cal round; continuum maps from line-free data of all spws  
  > "Then, the full, non-channel-averaged dirty image cubes were produced to identify the channels of continuum." (2 Observations and Data Reduction); "channels exceeding 1.5 times the continuum baseline were flagged after the third round of self-calibration" (2 Observations and Data Reduction); "The final Stokes *I*, *Q*, *U* continuum maps were produced independently using line-free and self-calibrated data of all spectral windows." (2 Observations and Data Reduction)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: about 0.8-0.97 x 0.65-0.71 arcsec (per-source values in the parameters table)  
  > "HH212M & 05:43:51.41 & -01:02:53.25 & 0.95$\times$0.70 & -70.0" (Table)
- final rms: Stokes I ~0.1 mJy/beam (average); Stokes Q and U ~0.07 mJy/beam  
  > "The average noise level in the final Stokes *I* image is $\sim0.1$ mJy beam$^{-1}$" (2 Observations and Data Reduction); "which is higher than the noise level of $\sigma_{QU} \sim0.07$ mJy/beam in both the Stokes *Q* and *U* maps" (2 Observations and Data Reduction)

### Inherited from earlier work

- Target identification and sample definition from the VANDAM survey  
  > "as identified by the VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey of Orion Protostars (cite: tobin2020vla)" (2 Observations and Data Reduction) [from (cite: tobin2020vla)]
- Debiased polarized intensity definition  
  > "(cite: vaillancourt2006placing; hull2015stokes), using a 3$\sigma_{QU}$ cutoff value" (2 Observations and Data Reduction) [from (cite: vaillancourt2006placing; hull2015stokes)]
- Intensity-weighted mean B-field angle method  
  > "giving more weight to polarization directions in higher-density regions (cite: hull2013misalignment; hull2014tadpol)" (6 Weighted mean B-field position angle) [from (cite: hull2013misalignment; hull2014tadpol)]
- Uncertainty-weighted mean position angle method  
  > "we also follow the approach discussed by (cite: galametz2020observational) and average the position angle of polarization by weighting it with its uncertainty" (6 Weighted mean B-field position angle) [from (cite: galametz2020observational)]
- Pixel size of one-third to half of the beam FWHM for derivatives  
  > "the pixel size used here falls within a region of one-third to half of the beam FWHM (cite: soler2017relation)" (6 Weighted mean B-field position angle) [from (cite: soler2017relation)]
- 2D linear regression fit to the C17O moment 1 map for velocity gradient  
  > "we fit a 2D linear regression fit to the moment 1 map following (cite: goodman1993dense) and (cite: tobin2011ism)" (3.3 B-field at scales of 400-1000 au) [from (cite: goodman1993dense; tobin2011ism)]
- Standard hourglass morphology definition  
  > "show the expected morphology (cite: girart2006magnetic)" (3.2 B-field at envelope scales) [from (cite: girart2006magnetic)]
- Comparison of cumulative distribution of observed angle differences  
  > "we plot the cumulative distribution function of the observed angle difference (cite: hull2013misalignment; hull2014tadpol; stephens2017alignment)" (3.4 Geometric projection effect) [from (cite: hull2013misalignment; hull2014tadpol; stephens2017alignment)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the ALMA pipeline or manual calibration products were used as the starting point
- Calibrator/flux scale and measurement-set selection used before self-calibration
- tclean image size, cell size, deconvolver, masks and clean threshold for continuum and cubes
- Which channels were treated as line-free per source for uvcontsub, and how the 12CO/other lines were flagged exactly
- Spectral binning, channel width and restoring-beam choices for the C17O and 12CO cubes
- How the 'continuum baseline' for the 1.5x channel flagging was defined
- Exact selection of channels/velocity ranges for the 14 manually treated outflow sources and for companion sources
- Source of the distances, Lbol and Tbol values in the parameters table
- Self-scattering selection criteria for 'compact polarized emission' and the Gaussian-fit procedure details
- Rules used to classify B-field morphologies (standard-hourglass, rotated, spiral, complex) and the P-V cut width
- Number of pixels used and the Monte Carlo/sample details behind the K-S test simulations

## Analysis recipe

1. **self-calibrate and image the dust continuum in Stokes I, Q, U**: Three rounds of phase-only self-calibration using the Stokes I image as model, then tclean continuum maps in Stokes I, Q, U from line-free self-calibrated data  
  > "Then we performed three successive rounds of phase-only self-calibration for each source to improve the image quality." (2 Observations and Data Reduction); "The final Stokes *I*, *Q*, *U* continuum maps were produced independently using line-free and self-calibrated data of all spectral windows." (2 Observations and Data Reduction)
   - software: CASA, tclean
   - parameter: Briggs robust = 0.5  
  > "with a *Briggs* weighting *robust* parameter set to 0.5, which is a good compromise between resolution and sensitivity (cite: Briggs95)" (2 Observations and Data Reduction)
   - parameter: Solution intervals 600, 30, 10 s  
  > "with solution intervals set to 600, 30, and 10 seconds for the first, second, and third iterations, respectively" (2 Observations and Data Reduction)
   - fitting: _not stated_
   - validation: Stokes I S/N 750 to 4200 reported for all targets after self-calibration  
  > "is strongly detected with a signal-to-noise ratio (S/N) ranging from 750 to 4200 for all targets" (2 Observations and Data Reduction)
2. **derive debiased polarized intensity, fractional polarization and angle maps**: P = (Q^2+U^2-sigma_QU^2)^1/2 with 3 sigma_QU cutoff; P_frac = P/I; theta = 0.5 arctan(U/Q) with 3 sigma threshold on the polarization intensity map  
  > "The debiased polarized intensity is defined as $P=(Q^{2}+U^{2}-\sigma_{QU}^{2})^{1/2}$ (cite: vaillancourt2006placing; hull2015stokes), using a 3$\sigma_{QU}$ cutoff value." (2 Observations and Data Reduction); "The polarization angle is calculated as $\theta=0.5\cdot \arctan(U/Q)$, using a 3$\sigma$ value of the polarization intensity map as a threshold." (2 Observations and Data Reduction)
   - parameter: 3 sigma_QU cutoff for debiased P  
  > "using a 3$\sigma_{QU}$ cutoff value" (2 Observations and Data Reduction)
   - assumption: Polarization angle rotated by 90 deg gives B-field direction if polarization arises from B-field aligned grains  
  > "should be rotated by 90$^\circ$ to infer the mean direction of *B*-field $\langle \theta_{B} \rangle$ if the polarization arises from *B*-field aligned grains" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **make continuum-subtracted line cubes**: Apply self-cal solutions to full data, identify continuum channels in dirty cubes, uvcontsub, then tclean Stokes I, Q, U cubes per spectral window  
  > "For the line data, we first applied the self-calibration solutions to the entire dataset." (2 Observations and Data Reduction); "The `uvcontsub` task was used to perform continuum fitting and subtraction in the UV plane." (2 Observations and Data Reduction)
   - software: CASA, uvcontsub, tclean
   - fitting: _not stated_
   - validation: _not stated_
4. **determine envelope V_LSR and make outflow and velocity-field maps**: Gaussian fit to C17O spectrum within 1000 au for V_LSR; immoments for 12CO blue/red outflow maps (velocity range from +/-5 km/s from V_LSR, channels above 5 sigma, some channels chosen manually); C17O moment 1 over channels above 3 sigma  
  > "The envelope’s centroid velocity ($V_{\rm LSR}$) was estimated by fitting a Gaussian to the spectrum obtained from averaging the C$^{17}$O (3–2) emission within a scale of 1000 au around the position of the protostar." (2 Observations and Data Reduction); "The `immoments` task was used to generate the outflow maps." (2 Observations and Data Reduction); "This map covers all channels with emission exceeding 3$\sigma$." (2 Observations and Data Reduction)
   - software: CASA, immoments
   - parameter: Outflow channels: starting from +/- 5 km/s w.r.t. V_LSR, emission at least 5 sigma  
  > "included all channels where the emission was at least 5$\sigma$" (2 Observations and Data Reduction)
   - parameter: Outflow edges at 5 sigma and radius R = 1000 au for position angle  
  > "The edges of the lobes are defined using the 5$\sigma$ level of the emission." (7 Outflow parameters); "Uniformly, the radius from center to lobe edge is set to $R=1000$ au, as most sources have clear outflows at this scale." (7 Outflow parameters)
   - assumption: C17O emission optically thin in the envelope  
  > "Since C$^{17}$O emission is optically thin in the envelope region (see Appendix [8](#App:VG))" (2 Observations and Data Reduction)
   - fitting: Gaussian fit to C17O spectrum for V_LSR (details not stated)  
  > "was estimated by fitting a Gaussian to the spectrum obtained from averaging the C$^{17}$O (3–2) emission" (2 Observations and Data Reduction)
   - validation: _not stated_
5. **identify self-scattering sources from compact polarized emission**: Gaussian fits to the polarized intensity of compact polarized sources; compare polarization angle to outflow direction and disk major axis; fractional polarization range check  
  > "We performed Gaussian fits to the polarized intensity and found that in each cases, the upper limits of the size of polarized emission are comparable to disk sizes, suggesting that the polarization arises from disk scales." (3.1 Self-scattering); "The fractional polarization of these 16 ptotostars is between 0.5% to 2.0%, suggesting that the compact polarization detected arises from self-scattering" (3.1 Self-scattering)
   - assumption: Self-scattering polarization is parallel to the minor axis of an inclined disk, so aligned with outflow  
  > "Self-scattering polarization is observed parallel to the minor axis of an inclined disk" (3.1 Self-scattering)
   - fitting: Gaussian fit (sampler/priors not stated)  
  > "We performed Gaussian fits to the polarized intensity" (3.1 Self-scattering)
   - validation: Deconvolved Gaussian sizes compared with resolved disk sizes from high-resolution data  
  > "The deconvolved major and minor axes from the Gaussian fits are consistent with the resolved disk sizes obtained from high resolution data by (cite: tobin2020vla)." (3.1 Self-scattering)
6. **compute mean B-field position angles (intensity- and uncertainty-weighted)**: Total-intensity-weighted average of Stokes Q and U over pixels above 4 sigma, with error propagation; also uncertainty-weighted average with chi-squared scaled error; 400-1000 au annulus used to avoid disk contamination  
  > "i.e. all Stokes *Q* and *U* pixels larger than 4$\sigma$ are enclosed" (6 Weighted mean B-field position angle); "we select an annular region from 1$\ensuremath{''}$ ($\sim$400 au) to 2.5$''$ ($\sim$1000 au)" (3.3 B-field at scales of 400-1000 au); "we also follow the approach discussed by (cite: galametz2020observational) and average the position angle of polarization by weighting it with its uncertainty" (6 Weighted mean B-field position angle)
   - parameter: Pixel size one-third to half of beam FWHM (e.g. 0.28-0.42 arcsec for HH212M)  
  > "the pixel size used here falls within a region of one-third to half of the beam FWHM (cite: soler2017relation)" (6 Weighted mean B-field position angle)
   - fitting: _not stated_
   - validation: Annular 400-1000 au result compared with all-polarization-data result; found very similar  
  > "Within this region the difference between the outflow and the intensity-weighted average *B*-field direction appears to be very similar to the one obtained using all polarization data" (3.3 B-field at scales of 400-1000 au)
7. **measure envelope velocity gradients and classify sources**: P-V cuts of C17O (3-2) perpendicular to outflow; absolute gradient from 5 sigma red/blue emission at 400 au; 2D linear fit to the moment 1 map for gradient direction; classify into Perp, Nonperp, Unres types  
  > "We generated position-velocity (P–V) cuts from the C$^{17}$O (3–2) channel maps centered at the dust peak intensity and perpendicular to the outflow axis." (3.3 B-field at scales of 400-1000 au); "In cases without a significant velocity gradient, we use the spectral resolution divided by the angular resolution as an upper limit." (3.3 B-field at scales of 400-1000 au); "Perp-Type: velocity gradient is perpendicular to the outflow ($67.5\ensuremath{^\circ}\le \vert \theta_{\rm Out}-\theta_{v} \vert \le 90\ensuremath{^\circ}$, 8 out of 39);" (3.3 B-field at scales of 400-1000 au)
   - parameter: Significant gradient threshold ~1.0 km/s/arcsec  
  > "Unres-Type: velocity gradient is unresolved ($\vert \nabla v_{\rm {abs}} \vert \lesssim 1.0$ km s$^{-1}$ arcsec$^{-1}$, 25 out of 39)." (3.3 B-field at scales of 400-1000 au)
   - assumption: Envelope angular momentum expected parallel to the outflow  
  > "The envelope’s angular momentum is expected to be parallel to the outflow (cite: pudritz2019role)." (3.3 B-field at scales of 400-1000 au)
   - fitting: Least-squares fit of v_lsr = v_alpha dAlpha + v_delta dDelta + v0 to moment 1 map  
  > "We estimate the velocity gradient by fitting the following function (cite: goodman1993dense; tobin2011ism)" (8 C17O opacity and velocity gradient)
   - validation: _not stated_
8. **classify B-field morphologies and test B-field vs outflow and disk alignment**: Visual classification of B-field patterns into standard-hourglass, rotated-hourglass, spiral, complex; histogram of angle difference between outflow and mean B-field; correlation coefficients per velocity-gradient type  
  > "In the standard-hourglass category, 8 protostars show the expected morphology (cite: girart2006magnetic), in which their outflow is roughly parallel to the direction of the hourglass axis." (3.2 B-field at envelope scales); "However, in Perp-Type sources, a correlation between the *B*-field and outflow is evident, with a correlation coefficient of 0.83" (3.3 B-field at scales of 400-1000 au)
   - parameter: Uncertainty-weighted B angles at 400-1000 au used for type analysis  
  > "We use the uncertainty-weighted position angles of the *B*-field on scales of 400–1000 au" (3.3 B-field at scales of 400-1000 au)
   - assumption: Envelope-scale polarization (including HOPS-250) assumed to be magnetically aligned grains; self-scattering not significant in the envelope  
  > "we assume that the polarization is produced by magnetically aligned grains" (3.2 B-field at envelope scales)
   - fitting: _not stated_
   - validation: 4 sigma_QU threshold used to avoid noise-generated vectors  
  > "3$\sigma$ polarized emission in some regions may be generated by noise in the data" (3.2 B-field at envelope scales)
9. **test projection effects on the B-field vs outflow angle distribution**: Compare observed cumulative angle-difference distribution of 39 sources with simulated 3D-to-2D projected parallel, random and perpendicular models via K-S test  
  > "We run the Kolmogorov–Smirnov (K-S) test on the angle difference distribution of our sample." (3.4 Geometric projection effect); "The parallel case uses the angles randomly selected within 0 and 22.5$^\circ$ in 3D, and then project onto the plane of the sky in the simulation" (3.4 Geometric projection effect)
   - assumption: 3D angles uniformly projected onto the plane of the sky  
  > "compare it with 2D simulated intersecting angles uniformly projected from a three-dimensional space" (3.4 Geometric projection effect)
   - fitting: K-S test (not a fit)  
  > "We run the Kolmogorov–Smirnov (K-S) test on the angle difference distribution of our sample." (3.4 Geometric projection effect)
   - validation: Applied to the entire sample only  
  > "it is prudent to exclusively employ the 3D projection analysis on the entire sample only" (3.4 Geometric projection effect)
10. **check that C17O is optically thin**: Derive T_R from peak intensity and beam, T_ex(12CO) from optically thick line, assume T_ex(C17O) ~ 50 K, compute opacity  
  > "Assuming $T_{EX}({\rm C}^{17}{\rm O})\approx 50$ K, we then obtained the opacity of C$^{17}$O for each source, with a range of 0.04 to 0.26, which is considered to be optically thin." (8 C17O opacity and velocity gradient)
   - assumption: Rayleigh-Jeans approximation accurate; 12CO optically thick; T_ex(C17O) ~ 50 K  
  > "Assuming the Rayleigh–Jeans approximation is accurate, then the observable source radiation temperature $T_{R}$ is estimated as:" (8 C17O opacity and velocity gradient); "We have $^{12}{\rm CO}$ detection, which is usually optically thick in the OMCs" (8 C17O opacity and velocity gradient)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Imaging, uv-plane continuum subtraction and moment maps  
  > "The dust continuum images were produced using the `tclean` task in CASA (cite: casateam2022casa)" (2 Observations and Data Reduction)
- **tclean** : Continuum Stokes I, Q, U images and line cubes  
  > "Finally, we performed the `tclean` task to produce Stokes *I*, *Q* and *U* image cubes using self-calibrated, continuum-subtracted data for each spectral window." (2 Observations and Data Reduction)
- **uvcontsub** : uv-plane continuum fit and subtraction  
  > "The `uvcontsub` task was used to perform continuum fitting and subtraction in the UV plane." (2 Observations and Data Reduction)
- **immoments** : Generating outflow maps  
  > "The `immoments` task was used to generate the outflow maps." (2 Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stokes I S/N range of continuum | 750 to 4200 | not stated | dimensionless | 1 | is strongly detected with a signal-to-noise ratio (S/N) ranging from 750 to 4200 for all targets |
| Average Stokes I noise | ~0.1 | not stated | mJy/beam | 1 | The average noise level in the final Stokes *I* image is $\sim0.1$ mJy beam$^{-1}$ |
| Stokes Q and U noise sigma_QU | ~0.07 | not stated | mJy/beam | 1 | which is higher than the noise level of $\sigma_{QU} \sim0.07$ mJy/beam in both the Stokes *Q* and *U* maps |
| Sources with both dust polarization and outflow detected | 56 | not stated | dimensionless | 4 | we successfully detected both dust polarization and molecular outflows in 56 sources |
| Sources with self-scattering polarization | 16 | not stated | dimensionless | 5 | Self-scattering is observed in 16 sources, most of them are Class 0 |
| Fractional polarization of self-scattering sources | 0.5% to 2.0% | not stated | percent | 5 | The fractional polarization of these 16 ptotostars is between 0.5% to 2.0% |
| Median difference between polarization direction and outflow direction (compact sources, excluding HOPS-250) | 7 | not stated | deg | 5 | Excluding this source, we find that the median difference between polarization direction and the the outflow direction is 7$^\circ$ |
| Median difference between polarization direction and disk major axis (compact sources, excluding HOPS-250) | 86 | not stated | deg | 5 | and the median difference between polarization direction and the the disk major axis is 86$^\circ$ |
| Number of standard-hourglass protostars | 8 | not stated | dimensionless | 8 | In the standard-hourglass category, 8 protostars show the expected morphology |
| Number of rotated-hourglass protostars | 13 | not stated | dimensionless | 8 | There are 13 protostars that exhibit a similar hourglass structure |
| Number of spiral protostars | 9 | not stated | dimensionless | 8 | The spiral category encompasses 9 protostars |
| Protostars with mean B-field approximately perpendicular to outflow | 16 of 40 (40.0%) | +/-3.0% | percent | 8 | 40.0% ($\pm$3.0%) of the protostars exhibit a mean magnetic field direction approximately perpendicular to the outflow; two-fifths of the protostars (16 out of 40) are located in the last quartile |
| Protostars with significant velocity gradient (>~1.0 km/s/arcsec) | 14 | not stated | count | 7 | toward 14 protostars, which is probably indicative of rotation |
| Perp-Type / Nonperp-Type / Unres-Type counts | 8 / 6 / 25 of 39 | not stated | count | 7 | velocity gradient is unresolved ($\vert \nabla v_{\rm {abs}} \vert \lesssim 1.0$ km s$^{-1}$ arcsec$^{-1}$, 25 out of 39) |
| Correlation coefficient between B-field and outflow, Perp-Type | 0.83 | not stated | dimensionless | 8 | in Perp-Type sources, a correlation between the *B*-field and outflow is evident, with a correlation coefficient of 0.83 |
| Fraction of Perp-Type sources with B-field perpendicular to outflow | 75.0% | +/-12.5% | percent | 8 | Specifically, 75.0% ($\pm$12.5%) of the sources show a trend that the *B*-field is perpendicular to the outflow. |
| Correlation coefficient between B-field and disk orientation, Perp-Type | 0.96 | not stated | dimensionless | 8 | with a correlation coefficient of 0.96 |
| K-S probability of drawing observed distribution from parallel model | <0.001 | not stated | dimensionless | 9 | The probability of our results being drawn from parallel models is $<$0.001, ruling out this scenario. |
| K-S probability, random model | 0.325 | not stated | dimensionless | 9 | The probability that the distribution is drawn from a random model is 0.325, and from a perpendicular model is 0.615. |
| K-S probability, perpendicular model | 0.615 | not stated | dimensionless | 9 | The probability that the distribution is drawn from a random model is 0.325, and from a perpendicular model is 0.615. |
| Opacity of C17O (3-2) range | 0.04 to 0.26 | not stated | dimensionless | 10 | with a range of 0.04 to 0.26, which is considered to be optically thin |
| T_ex(12CO) range at 400 au envelope scales | 15.3 to 50.4 | not stated | K | 10 | ranges from 15.3 K to 50.4 K at envelope scales of 400 au |

## Qualitative findings

- Self-scattering signatures in several Class 0 sources suggest grain growth already in disks at early protostellar phases  
  > "Self-scattering signatures are seen in several Class 0 sources, suggesting that grain growth appears to be significant in disks at earlier protostellar phases." (abstract)
- Envelope B-field morphology falls into standard-hourglass, rotated-hourglass and spiral categories  
  > "whose morphology can be approximately classified into three categories: standard-hourglass, rotated-hourglass (with its axis perpendicular to outflow), and spiral-like morphology" (abstract)
- All standard-hourglass sources are in the Unres-Type  
  > "Notably, all of the sources with *B*-field patterns showing a standard-hourglass structure of *B*-field are in the Unres-Type" (Summary)
- Six protostars show polarized emission along streamer-like dust structures, possibly accretion streamers  
  > "We speculate that these could be accretion streamers" (Discussion)

## Claim tuples

- H: Is compact polarization in the BOPS protostars produced by self-scattering by grown grains in disks? | E: Compare polarization angle of compact polarized sources with outflow direction and disk major axis; check fractional polarization | R: Median offset 7 deg from outflow and 86 deg from disk major axis; fractional polarization 0.5% to 2.0% for 16 sources | F: Self-scattering in 16 sources implies grain growth in disks at early Class 0 stages | **supported**
- H: Is the mean envelope B-field systematically perpendicular to protostellar outflows? | E: Histogram of angle difference between outflow and total-intensity-weighted mean B-field for 40 protostars | R: 16 of 40 in the 67.5-90 deg quartile; distribution otherwise appears random | F: Two-fifths show perpendicular B-field and the rest random relative orientation | **partially**
- H: Does the B-field orientation relative to outflow depend on envelope velocity-gradient type? | E: Classify protostars by C17O velocity-gradient direction and compare B-field and outflow angles per type on 400-1000 au scales | R: Perp-Type: correlation coefficient 0.83, 75.0% (+/-12.5%) perpendicular; no significant relation in Nonperp-Type and Unres-Type | F: Sources with velocity gradient perpendicular to outflow have B-field preferentially perpendicular to outflow | **supported**
- H: Are standard-hourglass B-field morphologies associated with weak envelope rotation due to magnetic braking? | E: Cross-tabulate B-field morphology with velocity-gradient type | R: All standard-hourglass protostars are Unres-Type; strong-gradient sources mostly have rotated-hourglass or spiral morphology | F: Strong B-fields may slow rotation in standard-hourglass sources; strong rotation twists field into spirals | **partially**
- H: Can the observed B-field and outflow angle distribution be explained by projection of parallel, random or perpendicular 3D orientations? | E: K-S test of observed angle-difference distribution (39 sources) against simulated projected models | R: Parallel p<0.001; random p=0.325; perpendicular p=0.615 | F: Parallel scenario ruled out; random and perpendicular both remain possible | **partially**

## Reasoning

- Why this data: Earlier polarization surveys had limited sensitivity and mixed regions and evolutionary stages, giving biased non-uniform samples; BOPS observes one region uniformly  
  > "The limited sensitivity of previous surveys (cite: hull2014tadpol; zhang2014magnetic) probed sources at varying evolutionary stages and in different star-forming regions, thus resulting in samples that were biased and non-uniform." (Introduction)
- Why this method: Briggs robust 0.5 chosen as a compromise between resolution and sensitivity; annulus 400-1000 au chosen to avoid disk self-scattering contamination  
  > "which is a good compromise between resolution and sensitivity (cite: Briggs95)" (2 Observations and Data Reduction); "To avoid possible contamination from disk self-scattering polarization (see Section [3.1](#Sec:selfscat))" (3.3 B-field at scales of 400-1000 au)
- Alternative: Intensity-weighted mean B-field direction rejected as sole estimator for extended sources because extended regions with low density contribute too much; uncertainty-weighted average used for comparison  
  > "The intensity-weighted method always makes sense when applied to point sources, but it may lead to misjudgment in certain extended cases" (6 Weighted mean B-field position angle)
- How they decided it was enough: _not stated_
- Limitation (authors): Limited spectral resolution (~0.9 km/s) prevents detecting velocity gradients in most sources  
  > "However, most of the sources do not show a clear gradient, which may due to the limited spectral resolution of the observations ($\sim$0.9 km s$^{-1}$)." (3.3 B-field at scales of 400-1000 au)
- Limitation (authors): Self-scattering may also be present in other sources but only visible near the intensity peak; higher angular resolution needed  
  > "It is possible that other sources in the sample also have polarized emission from self-scattering, but this would only be apparent around the intensity peak." (Discussion)
- Limitation (authors): Outflow and B-field angles are projected on the plane of the sky  
  > "The position angles of the outflow and *B*-field we measured are projected onto the plane of the sky." (3.4 Geometric projection effect)
- Caveat (inferred, ours): Small subsamples per velocity-gradient type (8, 6, 25) make correlation coefficients and percentages fragile
- Caveat (inferred, ours): B-field morphology classification is visual and subjective; no quantitative criteria given
- Caveat (inferred, ours): Unres-Type dominated by spectral-resolution-limited non-detections, so absence of gradient is weak evidence for slow rotation
- Caveat (inferred, ours): Self-scattering identification relies on angle alignment and fractional polarization range, not on a modelled scattering test
- Caveat (inferred, ours): K-S test applied once on 39 sources; models for parallel/random/perpendicular are idealized

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version and calibration route (pipeline vs manual) not stated
- Missing: tclean image size, cell size, masks, thresholds and cube binning not stated
- Missing: Per-source line-free channel selection and manual outflow channel choices not fully specified
- Missing: Morphology classification and compact-source selection criteria are qualitative
- Missing: Source of distances, Lbol, Tbol not stated
- Data volume (inferred): 57 Band 7 fields x 4 spectral windows (1920 channels each) in compact configurations; likely several hundred GB of measurement sets for full reprocessing (rough estimate)
- Score (inferred): 3/5, Scale 1-5. Data identified by project code and key steps (self-cal solints, robust, annulus, weighting formulas, classification thresholds) are given, but imaging geometry, CASA version, masks and morphology criteria are missing, so exact numbers are only approximately reproducible.
- Rediscovery candidate: no, The paper does not state that the data are public, and the recipe lacks imaging parameters and objective morphology criteria needed to redo the main classifications exactly.

## Links

- Method: (cite: hull2014tadpol) (TADPOL survey method for intensity-weighted mean B-field direction and comparison sample)
- Method: (cite: galametz2020observational) (Uncertainty-weighted mean position angle approach)
- Method: (cite: goodman1993dense) (Velocity gradient fitting method)
- Companion: (cite: tobin2020vla) (VANDAM survey: protostar sample, disk sizes and orientations)
- Companion: (cite: liu2023omc3) (Higher angular resolution observations of disk self-scattering in OMC-3)
- Related: BOPS (B-field Orion Protostellar Survey)
- Related: VANDAM
- Related: TADPOL

## Checks

```json
{
 "quotes": 146,
 "quotes_ok": 146,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2019.1.00086.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 22,
 "numeric_problems": 0,
 "fill": {
  "facts": 116,
  "stated": 83,
  "rate": 0.716
 },
 "evidence_ok": true
}
```
