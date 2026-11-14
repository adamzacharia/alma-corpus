# Kinematic Analysis of a Protostellar Multiple System: Measuring the Protostar Masses and Assessing Gravitational Instability in the Disks of L1448 IRS3B and L1448 IRS3A

`2021ApJ...907L..10R` | The Astrophysical Journal Letters 2021 | first author: Reynolds, Nickalas K. | arXiv: 2011.08293 | DOI: 10.3847/2041-8213/abcc02

Card schema 1.0 | model gpt-6.1-sol | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Constrain protostellar masses, disk gravitational stability, and formation pathways of IRS3B and IRS3A.  
  > "To constrain the main pathways for forming multiple systems, we must first constrain the protostellar geometrical parameters and then the (in)stability of the circum-multiple disk." (Origin of Triple System and Wide Companion)
- Target **L1448 IRS3B-ab**: coordinates J2000 RA 03:25:36.317, Dec 30:45:15.005  
  > "IRS3B-ab | 03:25:36.317 | 30:45:15.005" (Table 3); "where $D$ is the distance to the region (288 pc)" (Disk Masses); z/distance 288 pc  
  > "IRS3B-ab | 03:25:36.317 | 30:45:15.005" (Table 3); "where $D$ is the distance to the region (288 pc)" (Disk Masses); distance from _not stated_
- Target **L1448 IRS3B-c**: coordinates J2000 RA 03:25:36.382, Dec 30:45:14.715  
  > "IRS3B-c | 03:25:36.382 | 30:45:14.715" (Table 3); "where $D$ is the distance to the region (288 pc)" (Disk Masses); z/distance 288 pc  
  > "IRS3B-c | 03:25:36.382 | 30:45:14.715" (Table 3); "where $D$ is the distance to the region (288 pc)" (Disk Masses); distance from _not stated_
- Target **L1448 IRS3A**: coordinates J2000 RA 03:25:36.502, Dec 30:45:21.859  
  > "IRS3A | 03:25:36.502 | 30:45:21.859" (Table 3); "where $D$ is the distance to the region (288 pc)" (Disk Masses); z/distance 288 pc  
  > "IRS3A | 03:25:36.502 | 30:45:21.859" (Table 3); "where $D$ is the distance to the region (288 pc)" (Disk Masses); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01520.S
- bands: Band 7 (879 μm)  
  > "We observed L1448 IRS3B with ALMA in Band 7 (879 $\mu$m) during Cycle 4" (Observations)
- frequencies and spectral setup: Center frequencies: 341.0, 346.778059, 347.2698586, 345.3520738, 347.010582, 337.0730133, 335.4708304 GHz; channel widths and counts in Table 2.  
  > "| Center Freq. (GHz) | 341.0 | 346.778059 | 347.2698586 | 345.3520738 | 347.010582 | 337.0730133 | 335.4708304 |" (Table 2); "| Chan. Width (km/s) | 2747.96 | 0.212 |  | 0.053 | 0.053 | 0.054 | 0.873 |" (Table 2); "| Num. Chan. | 1 | 1920 | 1920 | 1920 | 1920 | 3840 | 1920 |" (Table 2)
- continuum bandwidth: ∼1.2 GHz from emission-free channels plus 1.875 GHz continuum window; ∼3 GHz aggregate at 341.0 GHz.  
  > "The total bandwidth recovered from this method was $\sim$1.2 GHz" (Observations); "in conjunction with the continuum spectral window bandwidth of 1.875 GHz, yields $\sim$3 GHz of aggregate continuum bandwidth with an average frequency center of 341.0 GHz." (Observations)
- arrays: 45 antennas in C40-6; 41 antennas in C40-3.  
  > "C40-6, was used on 2016 October 1 and 4 with 45 antennas." (Observations); "C40-3, was used on 19 December 2016 with 41 antennas." (Observations)
- configurations: C40-6 extended; C40-3 compact.  
  > "an extended (C40-6) and a compact (C40-3) configuration" (Observations)
- baselines: C40-6: 15–3200 meters; C40-3: 15–490 meters.  
  > "The baselines ranged from 15 to 3200 meters" (Observations); "The baselines covered 15 to 490 meters" (Observations)
- angular resolution: C40-6: 0.12″; C40-3: 0.59″; combined continuum: 0.11″ × 0.05″.  
  > "| L1448 IRS3B | 03:25:36.382 | 30:45:14.715 | C40-6 | 0.12$''$ | 1.3$''$ | 1 and 4 October 2016 | J0336$+$3218,J0237$+$2848,J0238$+$1636 |" (Table 1); "| L1448 IRS3B | 03:25:36.382 | 30:45:14.715 | C40-3 | 0.59$''$ | 5.6$''$ | 19 December 2016 | J0336$+$3218,J0237$+$2848,J0238$+$1636 |" (Table 1); "The beamsize of the combined continuum image is 0.11$''$$\times$0.05$''$(32$\times$15 au)." (Observations)
- max recoverable scale: LAS: C40-6 1.3″; C40-3 5.6″.  
  > "| L1448 IRS3B | 03:25:36.382 | 30:45:14.715 | C40-6 | 0.12$''$ | 1.3$''$ | 1 and 4 October 2016 | J0336$+$3218,J0237$+$2848,J0238$+$1636 |" (Table 1); "| L1448 IRS3B | 03:25:36.382 | 30:45:14.715 | C40-3 | 0.59$''$ | 5.6$''$ | 19 December 2016 | J0336$+$3218,J0237$+$2848,J0238$+$1636 |" (Table 1)
- sensitivity: Continuum 69 μJy beam−1; RMS/channel: 12CO 4.0, SiO 0.5, H13CN/SO2 4.5, H13CO+ 4.5, C17O 3.7 mJy.  
  > "We achieved 69 $\mu$Jy beam$^{-1}$sensitivity for the aggregate continuum data" (Observations); "| RMS/chan. (mJy) | 0.069 | 4.0 | 0.5 | 4.5 | 4.5 | 3.7 | \- |" (Table 2)
- time on source: C40-6: 4495 seconds for both executions; C40-3: 1335 seconds.  
  > "for a total of 4495 seconds on source (8052 seconds total) for both executions." (Observations); "for a total of 1335 seconds on source (3098 seconds total)." (Observations)
- observing dates: 2016 October 1 and 4; 19 December 2016.  
  > "C40-6, was used on 2016 October 1 and 4 with 45 antennas." (Observations); "C40-3, was used on 19 December 2016 with 41 antennas." (Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J = 3→2 (346.0 GHz)
- Line: C17O J = 3→2 (337.061104 GHz)
- Line: H13CO+ J = 4→3 (346.998347 GHz)
- Line: H13CN J = 4→3 (345.339756 GHz)
- Line: SO2 J = 13(2,12)→12(1,11) (345.3385377 GHz)
- Line: SiO J = 7→6 (347.000030579 GHz)
- Other facility **Gaia survey**: Distance uncertainty of 22 pc used in PV fitting.  
  > "Uncertainty in the distance (22 pc) from the *Gaia* survey (cite: 2018arXiv180803499O)" (IRS3B-ab)
- Other facility **OU Supercomputing Center for Education and Research (OSCER)**: Computing for radiative-transfer model convergence.  
  > "We run these models across 5 nodes with 24 cores/nodes each for $\sim$150 hours" (Application of Radiative Transfer Models); "The computing for this project was performed at the OU Supercomputing Center for Education & Research (OSCER) at the University of Oklahoma (OU)." (Acknowledgments)
- External data: Dust opacity at 1.3 mm: 0.899 cm2 g−1; dense cores with thin icy-mantles.  
  > "value of 0.899 cm$^2$ g$^{-1}$, typical of dense cores with thin icy-mantles (cite: 1994AA...291..943O)." (Disk Masses) [from (cite: 1994AA...291..943O)]
- External data: Bolometric luminosities: IRS3B 13.0 L⊙, IRS3A 14.4 L⊙; source-properties table states scaling to 288 pc.  
  > "13.0 L$_{\odot}$and 14.4 L$_{\odot}$for IRS3B and IRS3A at a distance of 300 pc, respectively (cite: 2016ApJ...818...73T)." (Disk Masses); "The bolometric luminosity is scaled to a distance of 288 pcfrom (cite: 2016ApJ...818...73T)." (Table 3) [from (cite: 2016ApJ...818...73T)]
- External data: Canonical ISM gas-to-dust mass ratio: 100:1.  
  > "the canonical ISM gas-to-dust mass ratio of 100:1 (cite: 1978ApJ...224..132B)" (Disk Masses) [from (cite: 1978ApJ...224..132B)]
- External data: Distance uncertainty: 22 pc.  
  > "Uncertainty in the distance (22 pc) from the *Gaia* survey (cite: 2018arXiv180803499O)" (IRS3B-ab) [from (cite: 2018arXiv180803499O)]
- External data: IRS3B system velocity of 4.8 km s−1 used to center PV diagrams.  
  > "The PV diagram velocity axis is centered on the system velocity of 4.8 km s$^{-1}$ (cite: 2016Natur.538..483T)" (PV Diagrams) [from (cite: 2016Natur.538..483T)]
- External data: Envelope-embedded disk models supporting a minimum temperature of 20 K.  
  > "The temperature profile has a minimum value of 20 K, based on models of disks embedded within envelopes (cite: 2003ApJ...591.1049W)." (Disk Structure) [from (cite: 2003ApJ...591.1049W)]
- External data: Protostellar birth-line models with surface cooling; Figure 3 supplies stellar-radius and stellar-luminosity estimates.  
  > "using the stellar birth-line in (cite: 1997ApJ...475..770H) (adopting the models with protostellar surface cooling which provides lower-estimates)" (Mass Accretion); "From Figure 3 in (cite: 1997ApJ...475..770H)we estimate the stellar radius to be 2.5 R$_{\odot}$, 2.5 R$_{\odot}$, and 2 R$_{\odot}$" (Mass Accretion); "From Figure 3 in (cite: 1997ApJ...475..770H)we estimate the stellar luminosity to be 1.9 L$_{\odot}$, 3.6 L$_{\odot}$, and 2.5 L$_{\odot}$" (Mass Accretion) [from (cite: 1997ApJ...475..770H)]
- External data: Empirical Class 0 and Class 0+I disk-radius–stellar-mass relations and comparison sample.  
  > "(cite: 2017ApJ...834..178Y) targeted several well known Class 0 protostars and compared their stellar properties against other well known sources" (Protostar Masses); "They derived an empirical power-law relation for Class 0 towards their observations" (Protostar Masses) [from (cite: 2017ApJ...834..178Y)]
- External data: Independent IRS3B/L1448-NB parameters: M* ∼1.4 M⊙, PA ∼29.5°, i ∼45°.  
  > "(cite: 2020AA...635A..15M) included IRS3B (labeled L1448-NB)" (Protostar Masses); "(M$_{*}$$\sim$1.4 M$_{\odot}$, *PA*$\sim$29.5$^\circ$, and *i*$\sim$45$^\circ$)." (Protostar Masses) [from (cite: 2020AA...635A..15M)]
- External data: L1489 IRS comparison mass ∼1.6 M⊙.  
  > "L1489 IRS, a Class I protostar with a M$_{*}\sim1.6$ M$_{\odot}$(cite: 2013ApJ...770..123G)" (Mass Accretion) [from (cite: 2013ApJ...770..123G)]
- External data: L1489 IRS comparison accretion rate ∼2.3 × 10−7 M⊙ yr−1.  
  > "$\dot{M}\sim2.3\times10^{-7}$ M$_{\odot}$ yr$^{-1}$ (cite: 2014ApJ...793....1Y)." (Mass Accretion) [from (cite: 2014ApJ...793....1Y)]
- Simulation/model as data: Dust opacity models for dense cores with thin icy-mantles.  
  > "value of 0.899 cm$^2$ g$^{-1}$, typical of dense cores with thin icy-mantles (cite: 1994AA...291..943O)." (Disk Masses)
- Simulation/model as data: Protostellar surface-cooling birth-line models for accretion estimates.  
  > "using the stellar birth-line in (cite: 1997ApJ...475..770H) (adopting the models with protostellar surface cooling which provides lower-estimates)" (Mass Accretion)

## Processing

### Calibration

- pipeline or manual: Cycle 4 ALMA pipeline in CASA; further processing in CASA.  
  > "The raw data were reduced using the Cycle 4 ALMA pipeline within the *Common Astronomy Software Application* (CASA) (cite: 2007ASPC..376..127M) version 4.7.0." (Observations); "All further processing was done using the CASA version 4.7.2" (Observations)
- casa version: 4.7.0 for pipeline reduction; 4.7.2 for further processing.  
  > "The raw data were reduced using the Cycle 4 ALMA pipeline within the *Common Astronomy Software Application* (CASA) (cite: 2007ASPC..376..127M) version 4.7.0." (Observations); "All further processing was done using the CASA version 4.7.2" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Monitored quasar J0238+1636.  
  > "the flux calibrator was the monitored quasar J0238$+$1636." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: Three phase rounds: inf, 30.25 s, 12.1 s; amplitude round: inf; C40-6 and C40-3 tabulated separately.  
  > "| phase-cal. 1 | 4.2 \| 25 | 140 \| 140 | 48 \| 40 | 100 \| 110 | “inf” |" (Table 7); "| phase-cal. 2 | 1.7 \| 11 | 310 \| 330 | 120 \| 100 | 300 \| 500 | 30.25 |" (Table 7); "12.1 |
| ampl.-cal. | 0.7 \| 4.3 | 1000 \| 840 | 390 \| 260 | 2500 \| 2500 | “inf” |" (Table 7)

### Imaging

- task: CASA clean.  
  > "taper the uv visibilities at 500 k$\lambda$ during deconvolution using the CASA *clean* task" (IRS3B-ab)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5; superuniform also used for IRS3A continuum.  
  > "The resulting images were generated from this concatenated dataset using *Briggs weighting* with a *robust* parameter of 0.5" (Observations); "We resolve the extended disk surrounding IRS3A (Briggs robust weight $=0.5$: Figure [1](#fig:contimage), superuniform: Figure [3](#fig:widesuperuniform))." (879 $\mu$m Dust Continuum)
- uv taper: H13CN/SO2: 1000 kλ; H13CO+ and C17O: 1500 kλ; IRS3B continuum geometry fit: 500 kλ.  
  > "| Taper (k$\lambda$) | \- | \- | \- | 1000 | 1500 | 1500 | \- |" (Table 2); "taper the uv visibilities at 500 k$\lambda$ during deconvolution using the CASA *clean* task" (IRS3B-ab)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Concatenated dataset used for combined continuum image.  
  > "The resulting images were generated from this concatenated dataset" (Observations); "The beamsize of the combined continuum image is 0.11$''$$\times$0.05$''$(32$\times$15 au)." (Observations)
- smoothing: Smooth IRS3B disk substructure with a 500 kλ uv taper before single-Gaussian geometry fitting.  
  > "To fit the general shape of the disk and not fit the shape of the spiral arms, we smooth the underlying disk structure" (IRS3B-ab); "taper the uv visibilities at 500 k$\lambda$ during deconvolution using the CASA *clean* task" (IRS3B-ab)
- final beam: Continuum 0.11″×0.05″; 12CO 0.19″×0.11″; SiO 0.85″×0.52″; H13CN/SO2 0.22″×0.14″; H13CO+ and C17O 0.21″×0.13″.  
  > "| Synth. Beam$^{f}$ | 0.11$''$$\times$0.05$''$ | 0.19$''$$\times$0.11$''$ | 0.85$''$$\times$0.52$''$ | 0.22$''$$\times$0.14$''$ | 0.21$''$$\times$0.13$''$ | 0.21$''$$\times$0.13$''$ | 0.21$''$$\times$0.13$''$ |" (Table 2)
- final rms: Aggregate continuum: 69 μJy beam−1; spectral RMS/channel in Table 2.  
  > "We achieved 69 $\mu$Jy beam$^{-1}$sensitivity for the aggregate continuum data" (Observations); "| RMS/chan. (mJy) | 0.069 | 4.0 | 0.5 | 4.5 | 4.5 | 3.7 | \- |" (Table 2)

### Inherited from earlier work

- Dust opacity normalization from thin icy-mantle models.  
  > "value of 0.899 cm$^2$ g$^{-1}$, typical of dense cores with thin icy-mantles (cite: 1994AA...291..943O)." (Disk Masses) [from (cite: 1994AA...291..943O)]
- Canonical ISM gas-to-dust mass ratio of 100:1.  
  > "the canonical ISM gas-to-dust mass ratio of 100:1 (cite: 1978ApJ...224..132B)" (Disk Masses) [from (cite: 1978ApJ...224..132B)]
- Optical-depth calculation from continuum flux, temperature, and disk radius.  
  > "\tau_{0.879~mm} &= \kappa_{0.879 mm}\Sigma" (Disk Masses); "from (cite: 2016Natur.538..483T)." (Disk Masses) [from (cite: 2016Natur.538..483T)]
- Numerical fitting of disk-coupled C17O PV emission.  
  > "We use a method of numerically fitting the C$^{17}$OPV diagrams employed by (cite: 2018ApJ...860..119G)and (cite: 2016MNRAS.459.1892S)" (IRS3B-ab) [from (cite: 2018ApJ...860..119G); (cite: 2016MNRAS.459.1892S)]
- Molecular-line radiative-transfer modeling and MCMC visibility fitting.  
  > "To further analyze the disk kinematics, we utilize the methods described in (cite: 2019ApJ...874..136S)" (Application of Radiative Transfer Models); "We sample the posterior distributions of the parameters to provide fits to the visibilities by utilizing a MCMC approach (cite: 2019ApJ...874..136S)." (Application of Radiative Transfer Models) [from (cite: 2019ApJ...874..136S)]
- Annulus size set to half the average synthesized beamsize.  
  > "the radius of the annuli is defined as half the average synthesized beamsize (cite: 1928TAIEE..47..617N)." (Disk Structure) [from (cite: 1928TAIEE..47..617N)]
- Minimum radial-profile temperature of 20 K from embedded-disk models.  
  > "The temperature profile has a minimum value of 20 K, based on models of disks embedded within envelopes (cite: 2003ApJ...591.1049W)." (Disk Structure) [from (cite: 2003ApJ...591.1049W)]
- Protostellar radius and luminosity estimates from surface-cooling birth-line models.  
  > "using the stellar birth-line in (cite: 1997ApJ...475..770H) (adopting the models with protostellar surface cooling which provides lower-estimates)" (Mass Accretion) [from (cite: 1997ApJ...475..770H)]
- Brightness-temperature conversion via Rayleigh-Jean’s Law.  
  > "We determine the peak brightness temperature of this clump by first converting the dust continuum image from Jy into K via the Rayleigh-Jean’s Law[^1]." (Disk Masses) [from (cite: 2009tra..book.....W)]

### Not stated but needed to reproduce (our reading)

- Exact line-free channel selections and line-emission flagging.
- Continuum-subtraction procedure for the molecular-line visibilities.
- Image cell size, image dimensions, CLEAN masks, thresholds, and deconvolution settings beyond robust and taper.
- Primary-beam correction procedure, particularly for off-axis IRS3A fluxes.
- Self-calibration reference antenna, gain-combination settings, solution acceptance criteria, and transfer to line data.
- Exact velocity integration ranges and extraction masks for moment maps and spectra.
- Numerical coefficients missing from the stated C17O/H2 and H13CN/H2 abundances.
- Full radiative-transfer prior bounds, visibility likelihood, visibility weights, chain lengths, and burn-in.
- Precise numerical convergence criterion and posterior-summary procedure.

## Analysis recipe

1. **Construct continuum and separate the tertiary**: Add emission-free spectral channels to continuum; fit IRS3B-c with two Gaussians plus zero-level offset; Fourier-transform its model and subtract it from visibilities.  
  > "To maximize the sensitivity of the continuum observations, emission free channels from the higher resolution windows were added to the continuum after appropriate flagging of line emission." (Observations); "we fit two Gaussians with a zero-level offset to the position of the source using the *imfit* task in CASA" (Tertiary Subtraction and Gaussian Fitting); "We then use the task *uvsub* to subtract this model from the data, producing the residual visibilities without the tertiary." (Tertiary Subtraction and Gaussian Fitting)
   - software: CASA, imfit, setjy, uvsub
   - parameter: Fit restricted to a 0.8″ × 0.7″ ellipse.  
  > "We also restricted the imfit task to a 0.8$''$$\times$0.7$''$ellipse around the source" (Tertiary Subtraction and Gaussian Fitting)
   - parameter: Briggs robust = 0.5.  
  > "The resulting images were generated from this concatenated dataset using *Briggs weighting* with a *robust* parameter of 0.5" (Observations)
   - assumption: Zero-level offset preserves underlying disk emission.  
  > "The offset serves to preserve the emission from the underlying IRS3B-ab disk emission." (Tertiary Subtraction and Gaussian Fitting)
   - fitting: Two Gaussians with a zero-level offset using imfit.  
  > "we fit two Gaussians with a zero-level offset to the position of the source using the *imfit* task in CASA" (Tertiary Subtraction and Gaussian Fitting)
   - validation: Point-source and single-Gaussian alternatives failed to preserve underlying emission; residual and model images shown together.  
  > "a point source and single Gaussian did not provide adequate fit while preserving the underlying disk emission" (Tertiary Subtraction and Gaussian Fitting); "A tertiary subtracted image is generated from this residual dataset and shown in Figure [32](#fig:subclump) along with the model of the tertiary used to construct this dataset." (Tertiary Subtraction and Gaussian Fitting)
2. **Measure continuum geometry**: Fit 2-D Gaussians to obtain deconvolved sizes, inclinations, and position angles; smooth IRS3B disk substructure before fitting.  
  > "We fit the semi-major and semi-minor axis of the IRS3B-ab disk with a 2-D Gaussian using the task *imfit* in CASA." (IRS3B-ab); "From this fit, we recovered the disk size, inclination, and position angle" (IRS3B-ab)
   - software: CASA, imfit, clean
   - parameter: 500 kλ uv taper for IRS3B geometry.  
  > "taper the uv visibilities at 500 k$\lambda$ during deconvolution using the CASA *clean* task" (IRS3B-ab)
   - assumption: Symmetric, geometrically thin disk for IRS3B inclination.  
  > "assuming the disk is symmetric and geometrically thin" (IRS3B-ab)
   - assumption: Flat, circular internal structure assumed for IRS3B-c.  
  > "the reported angles are assuming a flat, circular internal structure, similar to a disk." (IRS3B-c)
   - fitting: Single 2-D Gaussian after tertiary subtraction and tapering.  
  > "The image (Figure [33](#fig:subclumptaper)) is fit with a 2-D Gaussian using the *imfit* in CASA" (Tertiary Subtraction and Gaussian Fitting)
   - validation: Considered disk asymmetry; IRS3B inclination uncertainty may be as much as 25%.  
  > "We estimate the inclination angle uncertainty to be as much as 25% by considering the south-east side of the disk as asymmetric and more extended." (IRS3B-ab)
3. **Derive continuum masses and optical depths**: Mdust = D²Fλ/[κλBλ(Tdust)]; apply gas-to-dust ratio; derive average surface density and optical depth.  
  > "M_{dust} = \frac{D^2 F_{\lambda}}{\kappa_{\lambda}B_{\lambda}(T_{dust})}" (Disk Masses); "We calculate the average deprojected, cumulative surface density from the mass and radius" (Disk Masses); "\tau_{0.879~mm} &= \kappa_{0.879 mm}\Sigma" (Disk Masses)
   - parameter: D = 288 pc.  
  > "where $D$ is the distance to the region (288 pc)" (Disk Masses)
   - parameter: κ1.3mm = 0.899 cm2 g−1; scale with β = 1.78.  
  > "value of 0.899 cm$^2$ g$^{-1}$, typical of dense cores with thin icy-mantles (cite: 1994AA...291..943O)." (Disk Masses); "assuming $\beta$=1.78." (Disk Masses)
   - parameter: Adopted Tdust: IRS3B ∼40 K; IRS3B-c 55 K; IRS3A 51 K.  
  > "We adopt a $T_{dust}\approx\added{40}~K$ for the IRS3B" (Disk Masses); "Thus we adopt a T$_{dust}$ = 55 K" (Disk Masses); "We adopt a $T_{dust}$ = 51 K  for the IRS3A source." (Disk Masses)
   - assumption: Isothermal, optically thin emission; dust and gas well mixed.  
  > "If we make the assumption that the disk is isothermal, optically thin, , and the dust and gas are well mixed" (Disk Masses)
   - assumption: Gas-to-dust mass ratio 100:1.  
  > "the canonical ISM gas-to-dust mass ratio of 100:1 (cite: 1978ApJ...224..132B)" (Disk Masses)
   - fitting: _not stated_
   - validation: Optical-depth estimates identify IRS3B-c continuum mass as a likely lower limit.  
  > "Optically thick emission indicates that our dust continuum mass estimates are likely lower limits for the mass enclosed in the clump surrounding IRS3B-c" (Disk Masses)
4. **Identify disk tracers and extract kinematics**: Construct velocity-selected moment 0 maps, PV diagrams, and source-centered spectra; distinguish disk, envelope, and outflow emission.  
  > "We construct moment 0 maps, which integrate the data cube over the frequency axis" (Molecular Line Kinematics); "We then examine the sources using a position-velocity (PV) diagram" (PV Diagrams); "We can also construct spectra, centered on the sources, and integrated radially outwards in annuli." (Molecular Line Spectra)
   - parameter: IRS3B PV strip: 105 pixels (2.1″), PA 28°; velocity center 4.8 km s−1, ±5 km s−1.  
  > "The PV diagrams for IRS3B are generated over a 105 pixel (2.1$''$) width strip at a position angle 28$^\circ$." (PV Diagrams); "The PV diagram velocity axis is centered on the system velocity of 4.8 km s$^{-1}$ (cite: 2016Natur.538..483T) and spans $\pm$5 km s$^{-1}$ on either side" (PV Diagrams)
   - parameter: IRS3A PV strip: 31 pixels (0.62″), PA 133°; velocity center 5.4 km s−1, ±6.2 km s−1.  
  > "The PV diagrams for IRS3A are generated with a 31 pixel (0.62$''$) width strip at a position angle 133$^\circ$." (PV Diagrams); "The velocity cut is centered on the system velocity of 5.4 km s$^{-1}$ and spans 6.2 km s$^{-1}$ on either side." (PV Diagrams)
   - fitting: _not stated_
   - validation: Check spatial alignment, red/blue ordering, and consistency between tracers.  
  > "we first examine the moment 0 (integrated intensity) maps of the red- and blue-Doppler shifted C$^{17}$Oemission to determine if the emission appears well ordered" (PV Diagrams); "and consistent with H$^{13}$CO$^+$(Figure [7](#fig:h13copmomentc17o))." (PV Diagrams)
5. **Estimate central masses from PV diagrams**: Fit IRS3B C17O positions selected at 10σ with the Keplerian rotation-velocity formula; estimate IRS3A mass by eye.  
  > "extracting points in the PV-diagram that have emission 10 $\sigma$along the position axis for a given velocity channel and fitting these positions against the standard Keplerian rotation-velocity formula." (IRS3B-ab); "These estimates are provided by fitting the curve by eye" (Table 4)
   - software: emcee, Python
   - parameter: IRS3B mass prior limits: 0.1–2 M⊙.  
  > "Initial prior sampling limits of the mass were set to 0.1-2 M$_{\odot}$." (IRS3B-ab)
   - parameter: Include 22 pc distance uncertainty and estimated 10° inclination error.  
  > "Uncertainty in the distance (22 pc) from the *Gaia* survey (cite: 2018arXiv180803499O) and an estimate of the inclination error (10$^\circ$) were included" (IRS3B-ab)
   - assumption: Central protostellar source(s) dominate the gravitational potential; Keplerian rotation.  
  > "Assuming the gravitational potential is dominated by the central protostellar source(s), one would expect the disk to follow a Keplerian rotation pattern" (Keplerian Rotation)
   - fitting: MCMC with emcee for IRS3B; IRS3A PV estimate by eye supplies constraints for subsequent model priors.  
  > "The fitting procedure was achieved using a Markov Chain Monte Carlo (MCMC) employed by the Python MCMC program *emcee* (cite: 2013PASP..125..306F)." (IRS3B-ab); "simply provide further constraints for the priors for the more rigorous kinematic modeling." (Table 4)
   - validation: Compare kinematic centers and H13CO+ PV emission; center choices do not significantly affect mass.  
  > "The difference in the position of the kinematic centers is within $\sim$2 resolution elements of the C$^{17}$Omap and does not significantly affect our mass determination" (IRS3B-ab); "the H$^{13}$CO$^+$emission is still consistent with the central protostellar mass measured using C$^{17}$Oemission of 1.15 M$_{\odot}$" (IRS3B-ab)
6. **Limit the tertiary protostar mass**: Search for C17O velocities near IRS3B-c exceeding the main disk Keplerian profile.  
  > "we show the PV diagram of C$^{17}$Owithin a 2.0$''$ region centered on the tertiary" (IRS3B-c); "The velocity profile at IRS3B-c shows no evidence of any excess beyond the Keplerian profile from the main disk" (IRS3B-c)
   - parameter: 2.0″ region centered on IRS3B-c.  
  > "the PV diagram of C$^{17}$Owithin a 2.0$''$ region centered on the tertiary" (IRS3B-c)
   - assumption: Excess velocities could indicate the tertiary altering disk kinematics.  
  > "Emission in excess of the red-dashed lines could be attributed to the tertiary altering the gas kinematics." (IRS3B-c)
   - fitting: Upper limit from non-detection of excess velocities.  
  > "Based on the non-detection, we can place upper limits on the mass of IRS3B-c source of $<$0.2 M$_{\odot}$" (IRS3B-c)
   - validation: Larger protostellar masses would conflict with the observed velocity range.  
  > "A protostellar mass much in excess of this would be inconsistent with the range of velocities observed." (IRS3B-c)
7. **Fit radiative-transfer disk models**: Generate LTE, axisymmetric flared-disk channel maps with RADMC-3D; convert to visibilities with GALARIO; fit observed uv data using pdspy and MCMC.  
  > "The modeling framework uses RADMC-3D (cite: 2012ascl.soft02015D) to calculate the synthetic channel maps using 2D axisymmetric radiative transfer models in the local thermodynamic equilibrium (LTE)" (Application of Radiative Transfer Models); "GALARIO (cite: 2018MNRAS.476.4527T) to generate the model visibilities from those synthetic channel maps." (Application of Radiative Transfer Models); "The *pdspy*kinematic flared disk model results for IRS3B are shown in Figure [18](#fig:c17o_res)with the Keplerian disk fit compared to the data." (IRS3B)
   - software: pdspy, RADMC-3D, GALARIO, emcee
   - parameter: Rin = 0.1 au; temperature power-law index q = 0.35.  
  > "inner disk cutoff radius (R$_{in}$ = 0.1 au), and the temperature power law index (q = 0.35)." (Application of Radiative Transfer Models)
   - parameter: Free parameters include orientation, T0, stellar mass, disk radius/mass, γ, system velocity, and uniform microturbulent broadening.  
  > "position angle (p.a.), inclination (inc.), temperature (T$_0$), stellar mass (M$_{*}$), disk radius (R$_D$), disk mass (M$_{disk}$), surface density power law ($\gamma$), system source velocity (V$_{sys}$), and uniform microturbulent line broadening ($\alpha$)" (Application of Radiative Transfer Models)
   - assumption: Keplerian rotation and flared-disk geometry.  
  > "We assume the kinematic rotation of the disk is described by a Keplerian orbit" (Application of Radiative Transfer Models); "We assume the molecular line emission comes from a flared disk geometry" (Application of Radiative Transfer Models)
   - assumption: Truncated power-law surface density; vertical hydrostatic equilibrium; vertically isothermal and radial power-law temperature.  
  > "We assume the disk can be described via a power-law surface mass density profile that is truncated at some outer radius" (Application of Radiative Transfer Models); "the vertical structure of the disk is set by Local Hydro-static Equilibrium (LHSE) with a vertically isothermal temperature profile and a radial power-law temperature profile" (Application of Radiative Transfer Models)
   - assumption: Exclude chemical variations such as gas freeze-out.  
  > "Additionally, chemical variations such as gas freeze-out onto dust grains towards the midplane and outer disk are excluded from the models." (Application of Radiative Transfer Models)
   - fitting: Observationally constrained priors sampled uniformly with emcee; synthetic and observed visibilities compared in uv-plane; likelihood updated internally.  
  > "These *priors* are then sampled via a uniform distribution and fed into *emcee* to generate the samples" (Application of Radiative Transfer Models); "These are re-gridded and subsequently cross-compared with the observed data in the uv-plane." (Application of Radiative Transfer Models); "The likelihood of the parameters for this comparison is then updated internally" (Application of Radiative Transfer Models)
   - validation: Inspect walker steady state and residual maps; compare fitted masses and velocities with PV estimates.  
  > "The convergence state is determined when the *emcee* “walkers” reach a steady state solution where the ensemble of walkers is not changing by an appreciable amount" (Application of Radiative Transfer Models); "there is significant residual emission on the south-eastern side of the disk" (IRS3B); "The models yielded a similar stellar mass ($1.51^{+0.06}_{-0.07}$ M$_{\odot}$, 3-$\sigma$ uncertainties listed) to the estimate from the PV-diagram." (IRS3A)
8. **Construct radial surface-density profiles**: Azimuthally average continuum in annuli using PV geometry; convert flux to mass with a radial temperature law; use tertiary-subtracted IRS3B image.  
  > "The system geometry and image center were all adapted from the PV diagram fit parameters" (Disk Structure); "We then convert from flux density to mass" (Disk Structure); "we use the tertiary subtracted images" (Disk Structure)
   - parameter: Annuli sized at half the average synthesized beamsize; IRS3B outermost annulus 5″.  
  > "the radius of the annuli is defined as half the average synthesized beamsize (cite: 1928TAIEE..47..617N)." (Disk Structure); "The largest annulus extends out to 5$^{\prime\prime}$" (Disk Structure)
   - parameter: IRS3B: inclination 45°, PA 28°; IRS3A: inclination 69°, PA 133°.  
  > "The system geometric parameters used for the annuli correspond to an inclination of 45$^\circ$and a position angle of 28$^\circ$." (Disk Structure); "Towards IRS3A, the system geometry parameters used for the annuli correspond to an inclination of 69$^\circ$and a position angle of 133$^\circ$." (Disk Structure)
   - parameter: Temperature at 100 au: IRS3B-ab ≈40.1 K; IRS3A ≈50.9 K.  
  > "The temperature at 100 au for IRS3B-ab is taken to be $\approx$40.1 K." (Disk Structure); "The temperature at 100 au for IRS3A is taken to be $\approx$50.9 K." (Disk Structure)
   - assumption: Radial temperature power-law slope −0.5; minimum temperature 20 K.  
  > "we adopt a radial temperature power law with a slope of -0.5" (Disk Structure); "The temperature profile has a minimum value of 20 K" (Disk Structure)
   - fitting: _not stated_
   - validation: _not stated_
9. **Assess gravitational instability**: Calculate radial Toomre Q = csκ/(πGΣ) from surface-density, temperature, and orbital-frequency profiles.  
  > "Q = \frac{c_{s} \kappa}{\pi G \Sigma}" (Disk Stability); "The radial surface density profiles allow us to characterize the stability of the disk to its self-gravity as a function of radius." (Disk Stability)
   - parameter: Mean molecular weight 2.37; M* = 1.15 M⊙ in stated orbital-frequency calculation.  
  > "$\mu$ is the mean molecular weight (2.37)." (Disk Stability); "where M$_{*}=1.15$ M$_{\odot}$." (Disk Stability)
   - assumption: Thermalized disk; epicyclic frequency equals orbital frequency for Keplerian rotation.  
  > "We further assume the disk is thermalized" (Disk Stability); "$\kappa = \Omega$ in the case of a Keplerian disk" (Disk Stability)
   - fitting: _not stated_
   - validation: Compare unstable regions with embedded tertiary and spiral structures.  
  > "This coincides with the location of the spiral arms and the tertiary companion IRS3B-c, supporting the hypothesis that IRS3B-c was formed in situ via fragmentation of a gravitationally unstable disk." (abstract)
10. **Assess tertiary clump binding**: Evaluate virial ratio R = 2Ekin/|Epot| for the dust clump alone and with the upper-limit protostar mass.  
  > "$\mathcal{R} := \frac{2E_{kin}}{|E_{pot}|}$" (Gravitational Potential Energy of IRS3B-c); "we calculate $\mathcal{R} \approx1.4$for the dust clump alone" (Gravitational Potential Energy of IRS3B-c); "$\approx0.3$for the combined dust clump and protostar" (Gravitational Potential Energy of IRS3B-c)
   - parameter: Tpeak = 54.6 K; clump mass 0.07 M⊙; protostar upper bound 0.2 M⊙; diameter 78.5 au.  
  > "Assuming the clump is thermalized to the T$_{peak}=54.6$ K, the mass of the clump is $0.07$ M$_{\odot}$" (Gravitational Potential Energy of IRS3B-c); "the upper bound for the IRS3B-c protostar is $0.2$ M$_{\odot}$, and the diameter is 78.5 au" (Gravitational Potential Energy of IRS3B-c)
   - assumption: Ideal gas; mean molecular weight 2.37; potential energy −3GMclump²/(5Rclump).  
  > "Assuming the ideal gas scenario of N particles" (Gravitational Potential Energy of IRS3B-c); "$E_{pot} = \frac{-3}{5}\frac{GM^{2}_{clump}}{R_{clump}}$." (Gravitational Potential Energy of IRS3B-c); "$\mu$is the mean molecular weight (2.37)" (Gravitational Potential Energy of IRS3B-c)
   - fitting: _not stated_
   - validation: Interpret ratios as bounds because dust mass is a lower limit and protostar mass an upper limit.  
  > "this $\mathcal{R}$is likely an upper bound since our mass estimate for the dust is likely a lower limit due to the high optical depths" (Gravitational Potential Energy of IRS3B-c); "This $\mathcal{R}$is likely an lower bound since our mass estimate for the protostar an upper limit" (Gravitational Potential Energy of IRS3B-c)
11. **Estimate accretion rates**: Combine measured stellar masses and bolometric luminosities with birth-line radius/luminosity estimates; use Lbol ∼ L* + Lacc and Lacc = GM*Ṁ/R*.  
  > "L_{bol}\sim L_{*}+L_{acc}" (Mass Accretion); "L_{acc}=\frac{GM_{*}\dot{M}}{R_{*}}" (Mass Accretion); "using the stellar birth-line in (cite: 1997ApJ...475..770H) (adopting the models with protostellar surface cooling which provides lower-estimates)" (Mass Accretion)
   - parameter: IRS3B scenarios: two 0.575 M⊙ protostars or one 1.15 M⊙ protostar.  
  > "1.) the protostellar masses are equally divided (two 0.575 M$_{\odot}$protostars) and 2.) one protostar dominates the potential (one 1.15 M$_{\odot}$protostar)." (Mass Accretion)
   - assumption: Viscous, accreting disk; luminosity split into stellar and accretion contributions.  
  > "In a viscous, accreting disk, the total luminosity is the sum of the stellar and accretion luminosity" (Mass Accretion)
   - fitting: _not stated_
   - validation: Compare inferred rates against the time needed to build protostellar masses during the Class 0 lifetime and against a Class 0+I survey.  
  > "These accretion rates are unable to build up the observed protostellar masses within the typical lifetime of the Class 0 stage ($\sim$160 kyr)" (Mass Accretion); "We further compare the accretion rates derived here with a similar survey towards Class 0+I protostars (cite: 2017ApJ...834..178Y)." (Mass Accretion)

## Software

- **CASA** 4.7.0; 4.7.2: Pipeline reduction in 4.7.0; further processing in 4.7.2.  
  > "The raw data were reduced using the Cycle 4 ALMA pipeline within the *Common Astronomy Software Application* (CASA) (cite: 2007ASPC..376..127M) version 4.7.0." (Observations); "All further processing was done using the CASA version 4.7.2" (Observations)
- **clean** : Image reconstruction and uv-tapered deconvolution.  
  > "taper the uv visibilities at 500 k$\lambda$ during deconvolution using the CASA *clean* task" (IRS3B-ab)
- **imfit** : Gaussian fitting of continuum source geometry and tertiary model.  
  > "We fit the semi-major and semi-minor axis of the IRS3B-ab disk with a 2-D Gaussian using the task *imfit* in CASA." (IRS3B-ab); "we fit two Gaussians with a zero-level offset to the position of the source using the *imfit* task in CASA" (Tertiary Subtraction and Gaussian Fitting)
- **setjy** : Fourier-transform tertiary model image and populate measurement-set model column.  
  > "We used the CASA task *setjy* to Fourier transform the model image and fill the model column of the measurement set with the model visibility data." (Tertiary Subtraction and Gaussian Fitting)
- **uvsub** : Subtract tertiary model visibilities.  
  > "We then use the task *uvsub* to subtract this model from the data, producing the residual visibilities without the tertiary." (Tertiary Subtraction and Gaussian Fitting)
- **emcee** : MCMC PV fitting and radiative-transfer parameter sampling.  
  > "The fitting procedure was achieved using a Markov Chain Monte Carlo (MCMC) employed by the Python MCMC program *emcee* (cite: 2013PASP..125..306F)." (IRS3B-ab); "These *priors* are then sampled via a uniform distribution and fed into *emcee* to generate the samples" (Application of Radiative Transfer Models)
- **pdspy** : Kinematic flared-disk modeling.  
  > "The *pdspy*kinematic flared disk model results for IRS3B are shown in Figure [18](#fig:c17o_res)with the Keplerian disk fit compared to the data." (IRS3B)
- **RADMC-3D** : Synthetic molecular-line channel maps with 2D axisymmetric LTE radiative transfer.  
  > "The modeling framework uses RADMC-3D (cite: 2012ascl.soft02015D) to calculate the synthetic channel maps using 2D axisymmetric radiative transfer models in the local thermodynamic equilibrium (LTE)" (Application of Radiative Transfer Models)
- **GALARIO** : Generate model visibilities from synthetic channel maps.  
  > "GALARIO (cite: 2018MNRAS.476.4527T) to generate the model visibilities from those synthetic channel maps." (Application of Radiative Transfer Models)
- **Python** : MCMC program emcee and plotting package APLpy.  
  > "the Python MCMC program *emcee*" (IRS3B-ab); "This research made use of APLpy, an open-source plotting package for Python." (Acknowledgments)
- **Numpy** : _not stated_
- **scipy** : _not stated_
- **Matplotlib** : _not stated_
- **Astropy** : _not stated_
- **APLpy** : Plotting.  
  > "This research made use of APLpy, an open-source plotting package for Python." (Acknowledgments)
- **NASA’s Astrophysics Data System** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| IRS3B-ab continuum disk mass | 0.29 | not stated | M⊙ | 3 | we estimate the total mass of the IRS3B-ab disk (IRS3B-c subtracted) to be 0.29 M$_{\odot}$ |
| IRS3B-c circumstellar clump mass | 0.07 | not stated | M⊙ | 3 | We estimate 0.07 M$_{\odot}$to be associated with the circumstellar dust around IRS3B-c |
| IRS3A continuum disk mass | 0.04 | not stated | M⊙ | 3 | We perform the same analysis towards IRS3A and arrive at a disk mass estimate of 0.04 M$_{\odot}$ |
| IRS3B-ab continuum flux density | ≈1.51 | not stated | Jy | 3 | $F_{\lambda}\approx1.51~Jy$. |
| IRS3A continuum flux density | ≈0.19 | not stated | Jy | 3 | $F_{\lambda}\approx0.19~Jy$. |
| IRS3B-c peak brightness temperature | 55 | not stated | K | 3 | The compact clump around IRS3B-c has a peak brightness temperature of 55 K. |
| IRS3B-c average dust surface density | ∼2.6 | not stated | g cm−2 | 3 | The dust surrounding the tertiary source has an average dust surface density ($\Sigma$) of $\sim$2.6 g cm$^{-2}$ |
| IRS3B-c average optical depth | ∼2.14 | not stated | dimensionless | 3 | an optical depth ($\tau$) of $\sim$2.14, indicative of being optically thick |
| IRS3B-ab average dust surface density | ∼0.17 | not stated | g cm−2 | 3 | an average dust surface density of $\sim$0.17 g cm$^{-2}$and an optical depth of 0.34. |
| IRS3B-ab average optical depth | 0.34 | not stated | dimensionless | 3 | an average dust surface density of $\sim$0.17 g cm$^{-2}$and an optical depth of 0.34. |
| IRS3A average dust surface density | 0.32 | not stated | g cm−2 | 3 | L1448 IRS3A has an average dust surface density of 0.32 g cm$^{-2}$and an optical depth of 0.57. |
| IRS3A average optical depth | 0.57 | not stated | dimensionless | 3 | L1448 IRS3A has an average dust surface density of 0.32 g cm$^{-2}$and an optical depth of 0.57. |
| IRS3B-ab continuum inclination | 45.0 | +2.2/-2.2 | degrees | 2 | This corresponds to an inclination angle of 45.0$^\circ$$^{+2.2}_{-2.2}$ |
| IRS3B-ab continuum position angle | 28 | ±4 | degrees East-of-North | 2 | The position angle of the disk corresponds to 28$\pm$4$^\circ$East-of-North. |
| IRS3B-c continuum major-axis FWHM | 0.28 | ±0.05 | arcsec | 2 | a deconvolved major axis and minor axis FWHM of 0.28$''$$\pm$0.05$''$and 0.25$''$$\pm$0.04$''$ |
| IRS3B-c continuum minor-axis FWHM | 0.25 | ±0.04 | arcsec | 2 | a deconvolved major axis and minor axis FWHM of 0.28$''$$\pm$0.05$''$and 0.25$''$$\pm$0.04$''$ |
| IRS3B-c continuum inclination | 27.0 | +19/-19 | degrees | 2 | This corresponds to an inclination angle of 27.0$^\circ$$^{+19}_{-19}$ |
| IRS3B-c continuum position angle | 21 | ±1 | degrees East-of-North | 2 | we fit a position angle of 21$\pm$1$^\circ$East-of-North. |
| IRS3A continuum inclination | 68.6 | not stated | degrees | 2 | This corresponds to an inclination angle of 68.6$^\circ$assuming the disk is axially symmetric. |
| IRS3A continuum position angle | 133 | ±1 | degrees East-of-North | 2 | The position angle of the disk corresponds to 133$\pm$1$^\circ$East-of-North. |
| IRS3B central combined mass from PV fitting | 1.15 | ±0.09 (3-σ) | M⊙ | 5 | M$_{\*}$=1.15 M$_{\odot}$ with 3-$\sigma$ uncertainty$=0.09$ M$_{\odot}$ |
| IRS3B-c protostar mass upper limit | <0.2 | not stated | M⊙ | 6 | Based on the non-detection, we can place upper limits on the mass of IRS3B-c source of $<$0.2 M$_{\odot}$ |
| IRS3A central mass from by-eye PV comparison | 1.4 | not stated | M⊙ | 5 | The dotted white lines show the Keplerian velocity corresponding to a M$_{\*}$=1.4 M$_{\odot}$central protostar which is consistent with the PV diagram.; These estimates are provided by fitting the curve by eye |
| IRS3B stellar mass from pdspy | 1.19 | +0.13/-0.07 (3-σ) | M⊙ | 7 | The *pdspy*modeling of IRS3B finds a mass of $1.19^{+0.13}_{-0.07}$ M$_{\odot}$; The errors presented are the 3-$\sigma$confidence intervals of the best fit walkers generated from *emcee*. |
| IRS3A stellar mass from pdspy | 1.51 | +0.06/-0.07 (3-σ) | M⊙ | 7 | The models yielded a similar stellar mass ($1.51^{+0.06}_{-0.07}$ M$_{\odot}$, 3-$\sigma$ uncertainties listed) |
| IRS3B pdspy inclination | 66.0 | +3.0/-4.6 (3-σ) | degrees | 7 | $66.0^{+ 3.0}_{- 4.6}$; The errors presented are the 3-$\sigma$confidence intervals of the best fit walkers generated from *emcee*. |
| IRS3B pdspy position angle | 26.7 | +1.8/-2.9 (3-σ) | degrees | 7 | $26.7^{+  1.8}_{-  2.9}$; The errors presented are the 3-$\sigma$confidence intervals of the best fit walkers generated from *emcee*. |
| IRS3B pdspy disk radius | 299.0 | +24.9/-47.6 (3-σ) | au | 7 | $299.0^{+ 24.9}_{- 47.6}$; The errors presented are the 3-$\sigma$confidence intervals of the best fit walkers generated from *emcee*. |
| IRS3A pdspy disk radius | 39.9 | +2.4/-1.4 (3-σ) | au | 7 | $39.9^{+  2.4}_{-  1.4}$; The errors presented are the 3-$\sigma$confidence intervals of the best fit walkers generated from *emcee*. |
| IRS3B pdspy system velocity | 4.880 | +0.110/-0.090 (3-σ) | km s−1 | 7 | $4.880^{+0.110}_{-0.090}$; The errors presented are the 3-$\sigma$confidence intervals of the best fit walkers generated from *emcee*. |
| IRS3A pdspy system velocity | 5.288 | +0.090/-0.084 (3-σ) | km s−1 | 7 | $5.288^{+0.090}_{-0.084}$; The errors presented are the 3-$\sigma$confidence intervals of the best fit walkers generated from *emcee*. |
| IRS3B Toomre Q | <1 | not stated | dimensionless | 9 | We find the circum-multiple disk of IRS3B is gravitationally unstable (Q $<$ 1) for radii $>$ 120 au. |
| IRS3B instability inner radius | ∼120 | not stated | au | 9 | The disk has Q$<1$and therefore is gravitationally unstable starting near $\sim$120 au |
| IRS3B instability outer extent | ∼500 | not stated | au | 9 | extending out to the outer parts of the disk ($\sim$500 au) |
| IRS3A Toomre Q across entire disk | >5 | not stated | dimensionless | 9 | We find the protostellar disk of IRS3A is gravitationally stable (Q $>$5) for the entire disk. |
| IRS3B-c virial ratio, dust clump alone | ≈1.4 | not stated | dimensionless | 10 | we calculate $\mathcal{R} \approx1.4$for the dust clump alone |
| IRS3B-c virial ratio, clump plus upper-limit protostar | ≈0.3 | not stated | dimensionless | 10 | $\approx0.3$for the combined dust clump and protostar |
| IRS3A accretion rate, narrative | ∼4.95×10−7 | not stated | M⊙ yr−1 | 11 | we find the $\dot{M}\sim4.95\times10^{-7}$ M$_{\odot}$ yr$^{-1}$ for IRS3A. |
| IRS3B-ab equal-mass scenario accretion rate, narrative | ∼1.5×10−6 | not stated | M⊙ yr−1 | 11 | in the first scenario (two 0.575 M$_{\odot}$ protostars), we find $\dot{M}\sim1.5\times10^{-6}$ M$_{\odot}$ yr$^{-1}$ |
| IRS3B-ab single-protostar scenario accretion rate, narrative | ∼6.6×10−7 | not stated | M⊙ yr−1 | 11 | in the second scenario (one 1.15 M$_{\odot}$ protostar), we find $\dot{M}\sim6.6\times10^{-7}$ M$_{\odot}$ yr$^{-1}$. |
| IRS3A accretion rate, Table 6 | 5.43 | not stated | 10−7 M⊙ yr−1 | 11 | / IRS3A / 14.4$^{b}$ / 1.5 / 2 / 2.53 / 5.43 / |
| IRS3B-ab equal-mass and single-protostar accretion rates, Table 6 | (15.3, 6.56) | not stated | 10−7 M⊙ yr−1 | 11 | / IRS3B-ab$^{a}$ / 13.0$^{b}$ / (0.575, 1.2) / (2.5, 2.5) / (1.91, 3.57) / (15.3, 6.56) / |

## Qualitative findings

- IRS3B spiral arms contain the embedded tertiary IRS3B-c.  
  > "We resolve the spiral arm structure of IRS3B with high fidelity and observed IRS3B-c, the tertiary, to be embedded within one of the spiral arms." (Summary)
- C17O traces disk rotation in IRS3B; H13CO+ mainly traces the outer disk and inner envelope.  
  > "H$^{13}$CO$^+$traces the larger structure, corresponding to the outer disk and inner envelope for IRS3B." (Summary); "We found that the C$^{17}$Oemission is indicative of Keplerian rotation at the scale of the continuum disk" (Summary)
- The blended line likely reflects SO2 near IRS3B-c outflow launch locations, but H13CN in IRS3A.  
  > "the H$^{13}$CN/SO$_{2}$blended line most likely reflects SO$_{2}$emission, tracing outflow launch locations near IRS3B-c." (Summary); "For IRS3A, the H$^{13}$CN/SO$_{2}$emission likely reflects H$^{13}$CNemission due to a consistent velocity with C$^{17}$O." (Summary)
- The inner IRS3B continuum clumps cannot be uniquely identified as separate protostars.  
  > "Higher resolution kinematics and continuum observations are required to understand the architecture of the inner disk and whether each dust clump corresponds to a protostar, or if the clumps are components of the inner disk" (Protostar Masses)

## Claim tuples

- H: The IRS3B disk is gravitationally unstable and IRS3B-c formed by disk fragmentation. | E: Measure continuum surface density, fit central mass from disk kinematics, and calculate radial Toomre Q. | R: IRS3B has Q < 1 beyond ∼120 au; the tertiary lies within a spiral arm. | F: The observations support in-situ fragmentation of a gravitationally unstable disk. | **supported**
- H: The disks trace Keplerian rotation suitable for measuring central masses. | E: Compare PV rotation curves with radiative-transfer visibility fits. | R: IRS3B: PV 1.15 M⊙ and pdspy 1.19 M⊙; IRS3A: PV 1.4 M⊙ and pdspy 1.51 M⊙. | F: Kinematic model masses agree with PV estimates. | **supported**
- H: IRS3B-c measurably perturbs the surrounding disk kinematics. | E: Search its local C17O PV diagram for velocities above the main disk profile. | R: No excess detected; protostar mass <0.2 M⊙. | F: The tertiary has low mass and no detected excess kinematic signature. | **refuted**
- H: Possible IRS3A spiral substructure is driven by gravitational instability. | E: Calculate its Toomre Q profile from continuum surface density and central mass. | R: Q > 5 throughout the disk. | F: IRS3A is gravitationally stable under the adopted assumptions; substructure may have another origin. | **refuted**
- H: The wider IRS3A/B system formed through turbulent fragmentation. | E: Compare disk/outflow orientations and systemic velocities. | R: Nearly orthogonal disks and different system velocities. | F: Turbulent core fragmentation is the likely origin of the wider system. | **partially**
- H: The inferred present accretion rates can build the observed masses during the Class 0 stage. | E: Estimate accretion from luminosities, kinematic masses, and birth-line models. | R: Inferred rates are insufficient over ∼160 kyr. | F: Periods of higher accretion are required. | **refuted**

## Reasoning

- Why this data: Combine compact and extended configurations to recover ∼5″ emission while resolving disk structure.  
  > "in order to fully recover the total flux out to $\sim$5$^{\prime\prime}$angular scales in addition to resolving the structure in the disk." (Observations)
- Why this method: Use molecular-line kinematics because obscuration prevents spectral typing; favor C17O for Class 0 disk reconstruction near line center.  
  > "The protostars are completely obscured at $\lambda\space<\space3$ $\mu$m, rendering spectral typing impossible and kinematic measurements of the protostar masses from disk rotation are required to characterize the protostars themselves." (Keplerian Rotation); "we find C$^{17}$Ois possibly the best tracer for Class 0 disks, being the least abundant molecule and thus experiencing the least amount of spatial filtering" (Optimal Disk tracing Molecular lines)
- Alternative: A point source and a single Gaussian were inadequate tertiary models.  
  > "a point source and single Gaussian did not provide adequate fit while preserving the underlying disk emission" (Tertiary Subtraction and Gaussian Fitting)
- Alternative: Grain-growth opacity with β = 1 would lower reported continuum masses by a factor of 2.  
  > "and $\beta$=1, which would lower our reported masses by a factor of 2." (Disk Masses)
- Alternative: Dynamical ejection is disfavored for IRS3A by its low velocity offset, ordered disk, and core alignment.  
  > "the systems would not likely have formed via the dynamical ejection scenario from the IRS3B system (cite: 2012Natur.492..221R)." (Interpretation of the Formation Pathway)
- Alternative: Both an equal-mass inner binary and a single dominant central potential remain possible.  
  > "Thus, we can consider two scenarios (Section [6.7](#sec:massacc)), an equal mass binary and a single, dominate central potential." (IRS3B-ab)
- Alternative: IRS3A substructure could be spiral structure or a disk gap.  
  > "We marginally detect substructure in IRS3A, but at our resolution, we cannot definitely differentiate between spiral structure and a gap in the disk." (Summary)
- How they decided it was enough: Radiative-transfer MCMC stopped when the ensemble of walkers reached a steady state around a median with statistical variance.  
  > "the ensemble of walkers is not changing by an appreciable amount, simply oscillating around some median value with a statistical variance." (Application of Radiative Transfer Models)
- Limitation (authors): IRS3B-c continuum mass is likely a lower limit because of optical thickness.  
  > "Optically thick emission indicates that our dust continuum mass estimates are likely lower limits for the mass enclosed in the clump surrounding IRS3B-c" (Disk Masses)
- Limitation (authors): IRS3B-a/b mass ratio is unconstrained.  
  > "However with the current observations, we cannot constrain the mass ratio of the clumps." (IRS3B-ab)
- Limitation (authors): IRS3A PV fitting is limited by compact H13CN emission and low-S/N C17O.  
  > "from the PV diagram alone, strong constraints cannot be determined due to the compactness of the H$^{13}$CNemission and the low S/N of C$^{17}$O." (IRS3A)
- Limitation (authors): IRS3A has lower sensitivity away from the primary-beam center.  
  > "has lower sensitivity to emission because it is located $\sim$8 arcsec (beam efficiency$\sim$60%) from the primary beam center." (PV Diagrams)
- Limitation (authors): IRS3B gas and dust inclination estimates disagree; asymmetric emission and significant model residuals remain.  
  > "this discrepancy in inclination is most likely due to a difference in asymmetric gas and dust emission." (IRS3B); "there is significant residual emission on the south-eastern side of the disk" (IRS3B)
- Limitation (authors): Simple radial temperature laws are complicated by protostellar multiplicity.  
  > "protostellar multiples are expected to complicate simple radial temperature profiles." (Disk Structure)
- Limitation (authors): SiO was mistuned in C40-6; only C40-3 observed the line.  
  > "During the high-resolution execution, the central frequency of the SiO spectral window was set to 347.01 GHz with a bandwidth of 469 MHz, falling outside of the emission range for the target molecule." (Observations); "However, for the C40-3 configuration, the spectral setup was corrected and SiO was observed." (Observations)
- Limitation (authors): IRS3B-c inclination is conditional on unconstrained internal geometry.  
  > "the inclination estimates for IRS3B-c may not be realistic since the internal structure of the source (oblate, spherical, etc.) cannot be constrained from these observations" (IRS3B-c)
- Limitation (authors): Accretion rates are indirect estimates.  
  > "While these observations do not place a direct constraint on $\dot{M}$" (Mass Accretion)
- Caveat (inferred, ours): The supplied text loses coefficients in molecular abundances and several fitted quantities; exact radiative-transfer reproduction is blocked.
- Caveat (inferred, ours): IRS3B instability begins at ∼120 au in the body and summary, versus ∼200 au in the abstract.
- Caveat (inferred, ours): IRS3A accretion is 4.95×10−7 M⊙ yr−1 in the narrative and 5.43×10−7 in Table 6; retain both as distinct reported values.
- Caveat (inferred, ours): The stated 300 pc luminosity context and 288 pc table scaling require reconciliation before recalculating temperatures and accretion.
- Caveat (inferred, ours): Toomre Q depends on assumed temperature, opacity, gas-to-dust ratio, and azimuthal averaging of spiral structure.
- Caveat (inferred, ours): PV and radiative-transfer mass agreement does not independently test Keplerian rotation, which is assumed in both mass models.
- Caveat (inferred, ours): The tertiary upper limit has no stated confidence level or injection/recovery sensitivity test.
- Caveat (inferred, ours): Text and tables give differing continuum sizes, position angles, and systemic velocities; exact answer keys must identify the measurement method.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Public-access status and available calibrated or imaging products are not stated.
- Missing: No paper-specific scripts, parameter files, posterior chains, or numerical radial profiles are supplied.
- Missing: Exact channel selection, continuum subtraction, imaging masks, and primary-beam treatment are absent.
- Missing: Self-calibration intervals are supplied, but the full gain-solving and application configuration is absent.
- Missing: Radiative-transfer abundance coefficients are missing in the supplied text.
- Missing: Full prior ranges, likelihood definition, visibility weighting, burn-in, and chain lengths are absent.
- Missing: Accretion-rate and luminosity-scaling inconsistencies need resolution for a unique numerical reproduction.
- Data volume (inferred): Cannot estimate reliably: channel counts and observing durations are supplied, but visibility sampling and stored product sizes are not.
- Score (inferred): 5/5, 5/10: project code, correlator setup, CASA versions, self-calibration intervals, imaging weights, and main equations are supplied; exact imaging selections and radiative-transfer fitting inputs remain incomplete.
- Rediscovery candidate: no, Main results are numeric, but public availability is not stated and missing channel selections, abundance coefficients, and fitting settings prevent a complete recipe.

## Links

- Method: (cite: 2018ApJ...860..119G) (Inherited numerical PV-diagram fitting method.)
- Method: (cite: 2016MNRAS.459.1892S) (Inherited numerical PV-diagram fitting method.)
- Method: (cite: 2019ApJ...874..136S) (Radiative-transfer modeling framework, pdspy, and MCMC visibility fitting.)
- Method: (cite: 2013PASP..125..306F) (emcee MCMC implementation.)
- Method: (cite: 2012ascl.soft02015D) (RADMC-3D synthetic molecular-line channel maps.)
- Method: (cite: 2018MNRAS.476.4527T) (GALARIO generation of model visibilities.)
- Method: (cite: 1994AA...291..943O) (Adopted dust-opacity models.)
- Method: (cite: 1997ApJ...475..770H) (Birth-line model inputs for accretion estimates.)
- Method: (cite: 2009tra..book.....W) (Brightness-temperature conversion.)
- Companion: (cite: 2016Natur.538..483T) (Earlier IRS3B continuum, spiral-arm, and molecular-line observations; adopted systemic velocity and optical-depth method.)
- Companion: (cite: 2016ApJ...818...73T) (VANDAM multiplicity discovery, earlier kinematic context, and adopted luminosities.)
- Related: VLA Nascent Disk and Multiplicity (VANDAM) survey (cite: 2016ApJ...818...73T)
- Related: Gaia survey (cite: 2018arXiv180803499O)

## Checks

```json
{
 "quotes": 307,
 "quotes_ok": 307,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 42,
 "numeric_problems": 0,
 "fill": {
  "facts": 173,
  "stated": 144,
  "rate": 0.832
 },
 "evidence_ok": true
}
```
