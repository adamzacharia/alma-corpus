# Modeling the Milky Way Circumnuclear Disk: Rosettes and Rings

`2026ApJ..1004..171U` | The Astrophysical Journal 2026 | first author: Ukani, Asad | arXiv: 2512.11958 | DOI: 10.3847/1538-4357/ae690b

Card schema 1.0 | model gpt-6.1-sol | depth full | type theory_or_simulation_compared_to_alma

## Science

- Fields: milky_way_ism
- Question: Which circular-disk or non-Keplerian rosette models best reproduce the CND velocity field and spatial coverage?  
  > "Here, we present the first comprehensive study of the CND that models its rotation using both a circular disk and non-Keplerian rosette orbits." (Introduction); "We then evaluate models based on their deviation from the observed velocities and their spatial coverage of the CND’s on-sky area." (Introduction)
- Target **Milky Way circumnuclear disk/ring (CND), around Sgr A***: coordinates _not stated_; z/distance R0 = 8.28 kpc  
  > "At the center, there is a $\sim4\times10^{6}\,M_\odot$ supermassive black hole (SMBH), Sagittarius A\* (Sgr A\*; (cite: Gravity2019; Do2019)), which is surrounded by two dominant structures: the circumnuclear disk/ring (CND) and the nuclear star cluster (NSC)." (Introduction); "Throughout this paper, we assume a central black hole mass of $M_{\textrm{SgrA*}} = 4.30\times10^{6}\,M_\odot$ and a distance to the Galactic Center of $R_{0} = 8.28\,$kpc (cite: GRAVITY_2022)." (Gravitational Potential in the Galactic Center); distance from (cite: GRAVITY_2022)  
  > "At the center, there is a $\sim4\times10^{6}\,M_\odot$ supermassive black hole (SMBH), Sagittarius A\* (Sgr A\*; (cite: Gravity2019; Do2019)), which is surrounded by two dominant structures: the circumnuclear disk/ring (CND) and the nuclear star cluster (NSC)." (Introduction); "Throughout this paper, we assume a central black hole mass of $M_{\textrm{SgrA*}} = 4.30\times10^{6}\,M_\odot$ and a distance to the Galactic Center of $R_{0} = 8.28\,$kpc (cite: GRAVITY_2022)." (Gravitational Potential in the Galactic Center)

## Data provenance

- ALMA projects: 2017.1.00040.S
- bands: _not stated_
- frequencies and spectral setup: Spectral resolution: 0.8 km s−1  
  > "The cube has an RMS of 0.11 Jy/beam, and a spectral resolution of $0.8~\mathrm{km\,s^{-1}}$." (Observational Map)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 3.″69 × 2.″34; position angle 85°.2  
  > "The synthesized beam for this data is $3.''69\times \,2.''34$, with a position angle of $85\degree.2$." (Observational Map)
- max recoverable scale: _not stated_
- sensitivity: Cube RMS: 0.11 Jy/beam  
  > "The cube has an RMS of 0.11 Jy/beam, and a spectral resolution of $0.8~\mathrm{km\,s^{-1}}$." (Observational Map)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Public ALMA archive data and images; (cite: Hsieh_2021)  
  > "The data and the images from this project are publicly available through the ALMA archive (cite: Hsieh_2021)." (Observational Map)
- Line: HCN J=1−0 (not stated)
- Other facility **Northwestern University / CIERA**: Computing resources  
  > "This work used computing resources provided by Northwestern University and the Center for Interdisciplinary Exploration and Research in Astrophysics (CIERA)." (Acknowledgements)
- Other facility **Quest high performance computing facility**: Computational resources and staff contributions  
  > "This research was supported in part through the computational resources and staff contributions provided for the Quest high performance computing facility at Northwestern University" (Acknowledgements)
- External data: CND HCN (J=1−0) observational data  
  > "To test model accuracy, we conduct mock observations for each of our models and compare them with an observational velocity map of the CND in the HCN ($J=1{-}0$) line, constructed from the data of (cite: Hsieh_2021)." (Conclusion) [from (cite: Hsieh_2021)]
- External data: Central black hole mass 4.30×10^6 M⊙; Galactic Center distance 8.28 kpc  
  > "Throughout this paper, we assume a central black hole mass of $M_{\textrm{SgrA*}} = 4.30\times10^{6}\,M_\odot$ and a distance to the Galactic Center of $R_{0} = 8.28\,$kpc (cite: GRAVITY_2022)." (Gravitational Potential in the Galactic Center) [from (cite: GRAVITY_2022)]
- External data: Two-component spherical γ-model for the NSC density  
  > "We adopt the NSC mass density profile ($\rho_{\text{NSC}}$) from the two-component spherical $\gamma$-model of (cite: Chatzopoulos_2015):" (Gravitational Potential in the Galactic Center) [from (cite: Chatzopoulos_2015)]
- External data: NSC first-component mass M_NSC,1 = 2.7×10^7 M⊙  
  > "the NSC parameters are $M_\textrm{NSC,\,1} = 2.7\times10^7\,M_\odot$ (cite: schodel_2014; Fritz_2016; Feldmeier-Krause_2025)" (Gravitational Potential in the Galactic Center) [from (cite: schodel_2014; Fritz_2016; Feldmeier-Krause_2025)]
- External data: NSC axis ratio q ∼ 0.80 within 68″  
  > "The NSC is observed to be flattened along the Galactic plane (GP), with an axis ratio of $q \sim 0.80$ within $68''$ (cite: schodel_2014; Fritz_2016; Gallego-Cano_2020)." (On the NSC Potential) [from (cite: schodel_2014; Fritz_2016; Gallego-Cano_2020)]
- External data: CND tilt relative to the Galactic plane: 5° at 1.7 pc; up to 25° at 2.5–4.1 pc  
  > "Additionally, at a projected radius of $1.7$ pc ($42''$), the CND is estimated to be tilted by $5\degree$ relative to the GP." (On the NSC Potential); "It increases up to a tilt of $25\degree$ for radii between $2.5$ pc ($62''$) and $4.1$ pc ($103''$) (cite: Genzel_1989; Genzel_2010)." (On the NSC Potential) [from (cite: Genzel_1989; Genzel_2010)]
- External data: Observed CND velocity dispersion: 5–40 km s−1  
  > "the observed dispersion value of $5{-}40\,\mathrm{km\,s^{-1}}$ (cite: Hsieh_2021; Oka_2011; Ferriere_2012; SW_2014; Genzel_2010)." (The Filled-Rosette Model) [from (cite: Hsieh_2021; Oka_2011; Ferriere_2012; SW_2014; Genzel_2010)]
- External data: Anomaly A: possible CND feeding channel with strong shocks and velocity widths ∼50 km s−1  
  > "This southwest region corresponds to the southern end of “Anomaly A” from (cite: Tsuboi_2018)." (Residuals in the Southwest Region); "The authors identify this feature as a possible feeding channel for the CND and find that it indicates sites of strong shocks (velocity widths of $\sim50\,\mathrm{km\,s^{-1}}$)." (Residuals in the Southwest Region) [from (cite: Tsuboi_2018)]
- Simulation/model as data: Circular Disk: smooth disk of concentric rings separated by Δr ∼ 10−3 pc  
  > "The Circular Disk model describes the CND as a smooth disk that is formed using a set of concentric rings, which are separated by a width of $\Delta\,r\sim10^{-3}\,$pc." (Circular Disk Model)
- Simulation/model as data: Million-Years-Rosette: single trajectory integrated for 10^6 yrs, ∼10 orbital cycles  
  > "*The Million-Years-Rosette model* is created by integrating a rosette trajectory for $10^{6}$ yrs, which corresponds to $\sim10$ orbital cycles of the CND and is closer to its estimated lifetime (cite: Sanders_1998; vollmer_2002; scoville_2005)." (Rosette Models)
- Simulation/model as data: Filled-Rosette: single trajectory evolved for 10^8 yrs  
  > "It is constructed by evolving a single rosette trajectory for $10^{8}$ yrs." (Rosette Models)
- Simulation/model as data: 157,448 Circular Disk; 69,696 Filled-Rosette; 101,376 Million-Years-Rosette grid points  
  > "| Total Grid Points | 157,448 | 69,696 | 101,376 |" (Table 1)

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
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 3.″69 × 2.″34; position angle 85°.2  
  > "The synthesized beam for this data is $3.''69\times \,2.''34$, with a position angle of $85\degree.2$." (Observational Map)
- final rms: 0.11 Jy/beam  
  > "The cube has an RMS of 0.11 Jy/beam, and a spectral resolution of $0.8~\mathrm{km\,s^{-1}}$." (Observational Map)

### Inherited from earlier work

- CND observational data used to construct the HCN velocity map  
  > "To test model accuracy, we conduct mock observations for each of our models and compare them with an observational velocity map of the CND in the HCN ($J=1{-}0$) line, constructed from the data of (cite: Hsieh_2021)." (Conclusion) [from (cite: Hsieh_2021)]
- Adopted central black hole mass and Galactic Center distance  
  > "Throughout this paper, we assume a central black hole mass of $M_{\textrm{SgrA*}} = 4.30\times10^{6}\,M_\odot$ and a distance to the Galactic Center of $R_{0} = 8.28\,$kpc (cite: GRAVITY_2022)." (Gravitational Potential in the Galactic Center) [from (cite: GRAVITY_2022)]
- NSC density profile from the two-component spherical γ-model  
  > "We adopt the NSC mass density profile ($\rho_{\text{NSC}}$) from the two-component spherical $\gamma$-model of (cite: Chatzopoulos_2015):" (Gravitational Potential in the Galactic Center) [from (cite: Chatzopoulos_2015)]

### Not stated but needed to reproduce (our reading)

- Exact archive cube/image product identifiers and product versions used.
- Moment-map velocity integration range, voxel masking, and whether the S/N ≥20 cut applies to channel emission or a moment-map statistic.
- Exact observational WCS, spatial grid origin, and velocity reference frame used for model binning.
- Runge–Kutta timestep, output cadence, integration accuracy checks, and circular-ring azimuthal sampling.
- Gaussian-kernel truncation, image-edge handling, and the criterion for treating a mock moment-map pixel as a model point.
- Executable implementation of the weighted median: the prose describes intensity weighting, while the footnote accumulates β_i I_i.
- Exact southwest-region mask used to calculate ΔW_SW.

## Analysis recipe

1. **Prepare the observational comparison maps**: Construct the CND HCN (J=1−0) moment-1 map from ALMA project 2017.1.00040.S; crop around Sgr A* and retain S/N ≥20 data.  
  > "We construct it using data from the Atacama Large Millimeter/submillimeter Array (ALMA) project 2017.1.00040.S." (Observational Map); "we crop it at $-50 ''\leq \Delta\mathrm{R.A.} \leq 50''$ and $-70'' \leq \Delta\mathrm{decl.} \leq 70''$ from the location of Sgr A\* to retain only the most prominent features of the CND." (Observational Map); "For comparison with our models, we only use the observational data with a signal-to-noise ratio $\sigma \geq 20.$" (Observational Map)
   - parameter: HCN (J=1−0) velocity (moment-1) map  
  > "We evaluate the quality of our models by comparing them with a velocity (moment-1) map of the CND in the HCN ($J=1{-}0$) line." (Observational Map)
   - parameter: Beam 3.″69 × 2.″34 at 85°.2; RMS 0.11 Jy/beam; spectral resolution 0.8 km s−1  
  > "The synthesized beam for this data is $3.''69\times \,2.''34$, with a position angle of $85\degree.2$." (Observational Map); "The cube has an RMS of 0.11 Jy/beam, and a spectral resolution of $0.8~\mathrm{km\,s^{-1}}$." (Observational Map)
   - fitting: _not stated_
   - validation: _not stated_
2. **Construct the central gravitational potential**: Integrate the two-component NSC density to obtain enclosed stellar mass; combine the NSC potential with the central black hole potential.  
  > "We adopt the NSC mass density profile ($\rho_{\text{NSC}}$) from the two-component spherical $\gamma$-model of (cite: Chatzopoulos_2015):" (Gravitational Potential in the Galactic Center); "The enclosed mass of the NSC within radius $r$ $(M_{\mathrm{NSC}}(r))$ can be obtained by integrating" (Gravitational Potential in the Galactic Center); "The combined gravitational potential of the SMBH and the NSC has the form" (Gravitational Potential in the Galactic Center)
   - parameter: M_NSC,1 = 2.7×10^7 M⊙; a1 = 3.97 pc; γ1 = 0.51; M_NSC,2 = 2.8×10^9 M⊙; a2 = 95.38 pc; γ2 = 0.07  
  > "the NSC parameters are $M_\textrm{NSC,\,1} = 2.7\times10^7\,M_\odot$ (cite: schodel_2014; Fritz_2016; Feldmeier-Krause_2025)" (Gravitational Potential in the Galactic Center); "$a_1 = 3.97\,$pc, $\gamma_1 = 0.51$, $M_\textrm{NSC,\,2} = 2.8\times10^9 \,M_\odot$, $a_2 = 95.38\,$pc, and $\gamma_2 = 0.07$." (Gravitational Potential in the Galactic Center)
   - assumption: M_SgrA* = 4.30×10^6 M⊙; R0 = 8.28 kpc  
  > "Throughout this paper, we assume a central black hole mass of $M_{\textrm{SgrA*}} = 4.30\times10^{6}\,M_\odot$ and a distance to the Galactic Center of $R_{0} = 8.28\,$kpc (cite: GRAVITY_2022)." (Gravitational Potential in the Galactic Center)
   - assumption: Spherical central potential; orbits aligned with the Galactic plane  
  > "Therefore, we presently adopt a spherical central potential and consider orbits that are aligned with the GP." (On the NSC Potential)
   - fitting: _not stated_
   - validation: Using the values from (cite: Do2019) would change estimations by ∼5%.  
  > "If we use the values from (cite: Do2019) instead, our estimations would change by $\sim5\%$." (Gravitational Potential in the Galactic Center)
3. **Generate circular-disk models**: Construct concentric rings separated by Δr ∼10−3 pc, rotating counterclockwise with v(r) = √[G M_enc(<r)/r].  
  > "The Circular Disk model describes the CND as a smooth disk that is formed using a set of concentric rings, which are separated by a width of $\Delta\,r\sim10^{-3}\,$pc." (Circular Disk Model); "In its orbital plane, each individual ring rotates about the dynamical center in the counterclockwise direction with a rotation velocity" (Circular Disk Model); "v(r) = \sqrt{\frac{G M_\mathrm{enc}(<r)}{r}}," (Circular Disk Model)
   - parameter: r_in = 0.5–2.0 pc; r_out = 2.0–4.0 pc  
  > "| Inner Radius (pc) | $0.5\leq r_{\text{in}} \leq2.0$ |" (Table 1); "| Outer Radius (pc) | $2.0\leq r_{\text{out}} \leq4.0$ |" (Table 1)
   - parameter: i = 40–80°; PA = 20–40°; ω = 0°  
  > "| Inclination (deg) | $40\leq i \leq80$ |" (Table 1); "| Position Angle (deg) | $20\leq \mathrm{PA} \leq40$ |" (Table 1); "Additionally, the argument of pericenter is set to $\omega = 0\degree$ for this model, since it is composed of concentric rings." (Mock Observations)
   - parameter: Δr_in = Δr_out = 0.1 pc; Δi = ΔPA = 1°  
  > "$\Delta r_\mathrm{in}=\Delta r_\mathrm{out}=0.1\,$pc, $\Delta i= \Delta \mathrm{PA} =1\degree,$ (Circular Disk model)" (Table 1)
   - assumption: Uniformly distributed, fully circularized gas  
  > "It is an idealized representation of a gas disk in which the material is assumed to be uniformly distributed and fully circularized." (Motivating the Models)
   - fitting: Four-dimensional parameter grid  
  > "The Circular Disk model has $N=4$ parameters" (Table 1)
   - validation: _not stated_
4. **Generate rosette models**: Use fourth-order Runge–Kutta integration; launch counterclockwise at pericenter with angular momentum and initial velocity set by the chosen pericenter and apocenter.  
  > "There is no exact solution for a rosette orbit in this potential, so we solve for it numerically using the $4^{\text{th}}$-order Runge${-}$Kutta method." (Rosette Models); "We initialize a counterclockwise orbit at pericenter $r_{\mathrm{in}}$ with angular momentum $\ell$ and velocity $v_{\text{init}}$" (Rosette Models); "\ell^{2} = -2 \frac{\Phi(r_{\mathrm{in}}) - \Phi(r_{\mathrm{out}})}{r_{\mathrm{in}}^{-2}\, - \,r_{\mathrm{out}}^{-2}}, \qquad
v_{\text{init}} = \frac{\ell}{r_{\mathrm{in}}} \, ," (Rosette Models)
   - parameter: Both rosette classes: r_in = 1.0–1.5 pc; r_out = 2.0–3.5 pc  
  > "| Inner Radius (pc) | $0.5\leq r_{\text{in}} \leq2.0$ | $1.0\leq r_{\text{in}} \leq1.5$ | $1.0\leq r_{\text{in}} \leq1.5$ |" (Table 1); "| Outer Radius (pc) | $2.0\leq r_{\text{out}} \leq4.0$ | $2.0\leq r_{\text{out}} \leq3.5$ | $2.0\leq r_{\text{out}} \leq3.5$ |" (Table 1)
   - parameter: Filled-Rosette: i = 60–80°; Ω = 20–40°; 0 ≤ ω < 360°  
  > "| Inclination (deg) | $40\leq i \leq80$ | $60\leq i \leq80$ | $50\leq i \leq80$ |" (Table 1); "| Longitude of Ascending Node (deg) | — | $20\leq \Omega \leq40$ | $20\leq \Omega \leq40$ |" (Table 1); "| Argument of Pericenter (deg) | 0.0 | $0\leq \omega < 360$ | — |" (Table 1)
   - parameter: Million-Years-Rosette: i = 50–80°; Ω = 20–40°; 0 ≤ φ_init < 360°  
  > "| Inclination (deg) | $40\leq i \leq80$ | $60\leq i \leq80$ | $50\leq i \leq80$ |" (Table 1); "| Longitude of Ascending Node (deg) | — | $20\leq \Omega \leq40$ | $20\leq \Omega \leq40$ |" (Table 1); "| Initialization Angle (deg) | — | — | $0\leq \phi_{\text{init}} < 360$ |" (Table 1)
   - parameter: Δr_in = Δr_out = 0.1 pc; Δi = ΔΩ = 2°; Δω = Δφ_init = 60°  
  > "$\Delta r_\mathrm{in}=\Delta r_\mathrm{out}=0.1\,$pc" (Table 1); "$\Delta i= \Delta \Omega=2\degree$ (rosette models), and $\Delta \omega =\Delta \phi_{\mathrm{init}}=60\degree$." (Table 1)
   - parameter: Million-Years-Rosette: 10^6 yrs; Filled-Rosette: 10^8 yrs  
  > "*The Million-Years-Rosette model* is created by integrating a rosette trajectory for $10^{6}$ yrs" (Rosette Models); "It is constructed by evolving a single rosette trajectory for $10^{8}$ yrs." (Rosette Models)
   - assumption: Planar orbits in a spherical potential  
  > "As the potential $\Phi(r)$ is spherically symmetric, the orbit remains confined to a plane." (Rosette Models)
   - assumption: Rosettes represent present-day snapshots and omit shocks at trajectory self-intersections  
  > "We note that neither rosette models account for the shocks that would be produced at points of self-intersection along the planar trajectory." (Motivating the Models); "Instead, they simply present a snapshot that approximates the disk’s present-day morphology and velocity field." (Motivating the Models)
   - fitting: Five-dimensional parameter grids  
  > "The Filled-Rosette and the Million-Years-Rosette models have $N = 5$ parameters" (Table 1)
   - validation: Longer Filled-Rosette integration makes the final velocity profile insensitive to initialization and removes gaps in on-sky coverage.  
  > "The longer integration period ensures that the final velocity profile is insensitive to where the orbit is initialized and there are no gaps in the model’s on-sky area." (Rosette Models)
5. **Construct mock-observational moment maps**: Rotate positions and velocities to the sky; count model points on the observational position–velocity grid; convolve velocity slices with the beam; construct moments 0, 1, and 2.  
  > "After transforming the model onto the plane of the sky, we bin the model data onto a uniform position-velocity grid, whose sampling exactly matches that of the observational data." (Mock Observations); "Each three-dimensional bin in this cube stores a count of the number of model points assigned to it." (Mock Observations); "This produces a mock-observational data cube, from which we can construct our integrated emission map (moment-0), velocity map (moment-1), and velocity dispersion map (moment-2)." (Mock Observations)
   - parameter: Two-dimensional elliptical Gaussian convolution; FWHM matches the telescope beam  
  > "We convolve every velocity slice of the model cube with a two-dimensional elliptical Gaussian kernel whose FWHM matches the telescope beam." (Mock Observations)
   - parameter: Rotate coordinates and velocities using the supplied matrix T; sky x east, y north, z away from observer  
  > "To rotate the coordinates and velocities from the orbital plane to the plane of the sky, the following matrix is used:" (Rotation to the plane of the sky); "On the plane of the sky, the $x$-axis is positive along east, indicating the direction of increasing R.A. and the $y$-axis is positive along north, indicating the direction of increasing decl." (Rotation to the plane of the sky); "The positive $z$-axis is then oriented away from the observer." (Rotation to the plane of the sky)
   - parameter: Circular-disk PA measured east of north; Million-Years-Rosette ω = 120° − φ_init  
  > "The PA is measured east of north." (Rotation to the plane of the sky); "These angles are connected by the relation $\omega = 120\degree - \phi_{\textrm{init}}$." (Rotation to the plane of the sky)
   - fitting: _not stated_
   - validation: Mock observations match the observational sampling and beam FWHM  
  > "After transforming the model onto the plane of the sky, we bin the model data onto a uniform position-velocity grid, whose sampling exactly matches that of the observational data." (Mock Observations); "We convolve every velocity slice of the model cube with a two-dimensional elliptical Gaussian kernel whose FWHM matches the telescope beam." (Mock Observations)
6. **Rank models by velocity agreement and coverage**: Minimize W·P: W is the normalized, emission-weighted mean of Gaussian-neighborhood velocity RMS offsets; P penalizes incomplete observational coverage and excessive model extent.  
  > "\mathfrak{D} &= \frac{\sum_i \beta_{i}\, \cdot \,I_i}{\sum_i I_i}, \qquad \beta_{i} = \sqrt{\frac{\sum_j \Delta v^{2}_{ij}\, \cdot \,w_{ij}}{\sum_j w_{ij}}}," (Quantifying Model Accuracy); "The first term under the square root" (Quantifying Model Accuracy); "as a measure of the model quality, we use the product $(\mathcal{W \cdot P})$, since it ties together how well a model captures both the velocities and spatial distribution of the CND." (Issues with an Unweighted Fit Metric)
   - parameter: Gaussian spatial weights w_ij = exp[−d_ij²/(2σ_w²)]; σ_w = 2″  
  > "w_{ij} = \exp{-\frac{d^{2}_{ij}}{2\,\sigma_w^{2}}}," (Quantifying Model Accuracy); "we set $\sigma_w = 2''$, which is equal to about half the resolution of the observations." (Quantifying Model Accuracy)
   - parameter: Neighborhood cutoff d_ij ≤25″  
  > "we only use points that lie within a radius of $d_{ij}\leq 25''$, as contributions from points with $d_{ij}> 25''$ to $\beta_i$ are negligible." (Quantifying Model Accuracy)
   - parameter: W = D/N; normalization N is the emission-weighted mean absolute observed velocity for a zero-velocity model with perfect coverage  
  > "\mathcal{W} = \frac{\mathfrak{D}}{\mathcal{N}}" (Quantifying Model Accuracy); "\mathcal{N} = \left. \mathfrak{D} \right|_{v_{\mathrm{model},j}\,=\,0} =\frac{\sum_i \sqrt{v^{2}_{\textrm{obs},\,i}}\, \cdot \,I_i}{\sum_i I_i}" (Quantifying Model Accuracy)
   - parameter: P = √[0.5(N′/N)^−2 + 0.5(M′/M)^−2]; observational-to-model radius r_N = 0.″82; model-to-observational radius r_M = 5″  
  > "\mathcal{P} = \sqrt{ \frac{1}{2}\left( \frac{N'}{N} \right)^{-2} + \frac{1}{2}\left( \frac{M'}{M} \right)^{-2} }," (Quantifying Model Accuracy); "$N'$ is the number of points in the observational velocity map that have at least one model point within a radius of $r_{N}=0.''82$" (Quantifying Model Accuracy); "$M'$ is the number of points in the mock-observed model velocity map that have at least one observational point within a radius of $r_M=5''$" (Quantifying Model Accuracy)
   - parameter: Reject models with N′ = 0 or M′ = 0  
  > "In the cases where either $N'=0$ or $M'=0$, the penalty is infinite and the model is rejected." (Quantifying Model Accuracy)
   - assumption: Strong-emission regions provide more reliable constraints; prioritize general velocity trends over small spatial offsets  
  > "The weights $I_i$ reward models that provide a better fit to parts of the CND with stronger detected emission, as these areas yield more reliable constraints." (Quantifying Model Accuracy); "we must make our metric prioritize models with better fits to general trends, even in the cases where the model values are slightly offset spatially from the observational points." (Issues with an Unweighted Fit Metric)
   - fitting: Select the grid model minimizing W·P  
  > "Our best-fit model is the one that minimizes the product of these two quantities:" (Quantifying Model Accuracy); "{(\mathcal{W} \cdot \mathcal{P}) \to \min\, .}" (Quantifying Model Accuracy)
   - validation: Compare against the shortcomings of unweighted velocity RMS: thin-ring bias, patchy data, and equal weighting of weak and strong emission  
  > "First, an unweighted velocity RMS is strongly biased toward thin-ring models that fail to capture a majority of the CND’s gas distribution" (Issues with an Unweighted Fit Metric); "Second, the observational map is somewhat patchy and is expected to have some contribution from both background and foreground emission." (Issues with an Unweighted Fit Metric); "Last, the unweighted velocity RMS assigns the same weight to all residuals, as it does not know about which parts of the observational velocity map are detected more robustly." (Issues with an Unweighted Fit Metric)
7. **Evaluate residuals and velocity dispersions**: Calculate the emission-weighted median velocity offset, signed neighborhood residual maps, residual histograms, and model moment-2 ranges.  
  > "We use the weighted median of the velocity offsets" (Velocity Offsets); "For the best-fit maps, for visualization purposes" (Velocity Offsets); "\mathcal{V}_{i} = \frac{\sum_j \Delta v_{ij} \cdot w_{ij}}{\sum_j w_{ij}}" (Velocity Offsets)
   - parameter: Signed residual V_i uses the same Gaussian weights and d_ij ≤25″ neighborhood  
  > "As before, when calculating the sum and $w_{ij}$, we only use model points that are within a radius of $d_{ij}\leq 25''$ from each observational point $i$." (Velocity Offsets)
   - fitting: _not stated_
   - validation: Compare model dispersion ranges with the literature observed range of 5–40 km s−1  
  > "the observed dispersion value of $5{-}40\,\mathrm{km\,s^{-1}}$ (cite: Hsieh_2021; Oka_2011; Ferriere_2012; SW_2014; Genzel_2010)." (The Filled-Rosette Model); "For the velocity dispersion properties of the CND, the closest fit is achieved by the Million-Years-Rosette model" (Conclusion)
8. **Assess the southwest residual contribution**: Retain the anomalous southwest feature in the fit; estimate its contribution ΔW_SW and compare W−ΔW_SW across models.  
  > "For consistency, we chose to retain it, since it punishes all models equally." (Residuals in the Southwest Region); "The approximate contribution of the southwest region to the fit metric $\mathcal{W}$ is about half." (Residuals in the Southwest Region); "and $(\mathcal{W}-\Delta\mathcal{W}_{SW})$ is the fit metric with residuals from the southwest region subtracted" (Table 2)
   - parameter: High-residual region near −40″ < ΔR.A. < −10″ and −30″ < Δdecl. < 20″  
  > "the velocity residuals for all models peak near $-40''<\Delta\mathrm{R.A.}<-10''$ and $-30'' <\Delta\mathrm{decl.} < 20''$." (Residuals in the Southwest Region)
   - assumption: Southwest gas dynamics likely affected by unmodeled non-gravitational processes  
  > "Hence, the gas dynamics in this region are likely affected by non-gravitational processes, which we do not consider." (Residuals in the Southwest Region)
   - fitting: _not stated_
   - validation: Circular Disk remains favored after subtracting southwest residual contributions  
  > "It outperforms both rosette models by about 50% according to the fit metric without the residuals from the southwest region" (Conclusion)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Circular Disk best-fit inner radius | 1.0 | not stated | pc | 6 | / Circular Disk / 1.0 / 2.9 / 35 / 60 / — / — / — / 12.4 / 0.37 / 1.61 / $\simeq 0.15$ / |
| Circular Disk best-fit outer radius | 2.9 | not stated | pc | 6 | / Circular Disk / 1.0 / 2.9 / 35 / 60 / — / — / — / 12.4 / 0.37 / 1.61 / $\simeq 0.15$ / |
| Circular Disk best-fit position angle | 35 | not stated | deg | 6 | / Circular Disk / 1.0 / 2.9 / 35 / 60 / — / — / — / 12.4 / 0.37 / 1.61 / $\simeq 0.15$ / |
| Circular Disk best-fit inclination | 60 | not stated | deg | 6 | / Circular Disk / 1.0 / 2.9 / 35 / 60 / — / — / — / 12.4 / 0.37 / 1.61 / $\simeq 0.15$ / |
| Filled-Rosette best-fit inner radius | 1.1 | not stated | pc | 6 | / Filled-Rosette / 1.1 / 3.0 / 28.5$^{*}$ / 64 / 30 / 60 / — / 20.4 / 0.41 / 1.61 / $\simeq 0.21$ / |
| Filled-Rosette best-fit outer radius | 3.0 | not stated | pc | 6 | / Filled-Rosette / 1.1 / 3.0 / 28.5$^{*}$ / 64 / 30 / 60 / — / 20.4 / 0.41 / 1.61 / $\simeq 0.21$ / |
| Filled-Rosette effective position angle | 28.5 | not stated | deg | 6 | / Filled-Rosette / 1.1 / 3.0 / 28.5$^{*}$ / 64 / 30 / 60 / — / 20.4 / 0.41 / 1.61 / $\simeq 0.21$ /; $^*$ denotes effective PAs calculated for the projected semi-major axes of the ellipses traced by the inner and outer edges of the rosettes. |
| Filled-Rosette best-fit inclination | 64 | not stated | deg | 6 | / Filled-Rosette / 1.1 / 3.0 / 28.5$^{*}$ / 64 / 30 / 60 / — / 20.4 / 0.41 / 1.61 / $\simeq 0.21$ / |
| Filled-Rosette best-fit longitude of ascending node | 30 | not stated | deg | 6 | / Filled-Rosette / 1.1 / 3.0 / 28.5$^{*}$ / 64 / 30 / 60 / — / 20.4 / 0.41 / 1.61 / $\simeq 0.21$ / |
| Filled-Rosette best-fit argument of pericenter | 60 | not stated | deg | 6 | / Filled-Rosette / 1.1 / 3.0 / 28.5$^{*}$ / 64 / 30 / 60 / — / 20.4 / 0.41 / 1.61 / $\simeq 0.21$ / |
| Million-Years-Rosette best-fit inner radius | 1.2 | not stated | pc | 6 | / Million-Years-Rosette / 1.2 / 2.7 / 27.1$^{*}$ / 60 / 28 / — / 180 / 22.2 / 0.41 / 1.66 / $\simeq 0.23$ / |
| Million-Years-Rosette best-fit outer radius | 2.7 | not stated | pc | 6 | / Million-Years-Rosette / 1.2 / 2.7 / 27.1$^{*}$ / 60 / 28 / — / 180 / 22.2 / 0.41 / 1.66 / $\simeq 0.23$ / |
| Million-Years-Rosette effective position angle | 27.1 | not stated | deg | 6 | / Million-Years-Rosette / 1.2 / 2.7 / 27.1$^{*}$ / 60 / 28 / — / 180 / 22.2 / 0.41 / 1.66 / $\simeq 0.23$ /; $^*$ denotes effective PAs calculated for the projected semi-major axes of the ellipses traced by the inner and outer edges of the rosettes. |
| Million-Years-Rosette best-fit inclination | 60 | not stated | deg | 6 | / Million-Years-Rosette / 1.2 / 2.7 / 27.1$^{*}$ / 60 / 28 / — / 180 / 22.2 / 0.41 / 1.66 / $\simeq 0.23$ / |
| Million-Years-Rosette best-fit longitude of ascending node | 28 | not stated | deg | 6 | / Million-Years-Rosette / 1.2 / 2.7 / 27.1$^{*}$ / 60 / 28 / — / 180 / 22.2 / 0.41 / 1.66 / $\simeq 0.23$ / |
| Million-Years-Rosette best-fit initialization angle | 180 | not stated | deg | 6 | / Million-Years-Rosette / 1.2 / 2.7 / 27.1$^{*}$ / 60 / 28 / — / 180 / 22.2 / 0.41 / 1.66 / $\simeq 0.23$ / |
| Circular Disk fit metric W | 0.37 | not stated | dimensionless | 6 | The best-fit model has $\mathcal{W} = 27.3\,\mathrm{km\,s^{-1}}/ \,73.9\,\mathrm{km\,s^{-1}} = 0.37$ and a penalty factor of $\mathcal{P}=1.61$. |
| Circular Disk penalty factor P | 1.61 | not stated | dimensionless | 6 | The best-fit model has $\mathcal{W} = 27.3\,\mathrm{km\,s^{-1}}/ \,73.9\,\mathrm{km\,s^{-1}} = 0.37$ and a penalty factor of $\mathcal{P}=1.61$. |
| Filled-Rosette fit metric W | 0.41 | not stated | dimensionless | 6 | The best-fit Filled-Rosette model yields $\mathcal{W} = 0.41$ and a penalty factor of $\mathcal{P}=1.61$. |
| Filled-Rosette penalty factor P | 1.61 | not stated | dimensionless | 6 | The best-fit Filled-Rosette model yields $\mathcal{W} = 0.41$ and a penalty factor of $\mathcal{P}=1.61$. |
| Million-Years-Rosette fit metric W | 0.41 | not stated | dimensionless | 6 | The best-fit Million-Years-Rosette model results in $\mathcal{W} = 0.41$ and a penalty factor of $\mathcal{P}=1.66$. |
| Million-Years-Rosette penalty factor P | 1.66 | not stated | dimensionless | 6 | The best-fit Million-Years-Rosette model results in $\mathcal{W} = 0.41$ and a penalty factor of $\mathcal{P}=1.66$. |
| Circular Disk emission-weighted median velocity offset | 12.4 | not stated | km s−1 | 7 | / Circular Disk / 1.0 / 2.9 / 35 / 60 / — / — / — / 12.4 / 0.37 / 1.61 / $\simeq 0.15$ / |
| Filled-Rosette emission-weighted median velocity offset | 20.4 | not stated | km s−1 | 7 | / Filled-Rosette / 1.1 / 3.0 / 28.5$^{*}$ / 64 / 30 / 60 / — / 20.4 / 0.41 / 1.61 / $\simeq 0.21$ / |
| Million-Years-Rosette emission-weighted median velocity offset | 22.2 | not stated | km s−1 | 7 | / Million-Years-Rosette / 1.2 / 2.7 / 27.1$^{*}$ / 60 / 28 / — / 180 / 22.2 / 0.41 / 1.66 / $\simeq 0.23$ / |
| Circular Disk model velocity-dispersion range | 0–7.1 | not stated | km s−1 | 7 | the velocity field of this model is very smooth and has velocity dispersions (moment-2) in the range of $0{-}7.1\,\mathrm{km\,s^{-1}},$ |
| Filled-Rosette model velocity-dispersion range | 0–63 | not stated | km s−1 | 7 | The Filled-Rosette model admits velocity dispersion (moment-2) values in the range $0{-}63\,\mathrm{km\,s^{-1}},$ |
| Million-Years-Rosette model velocity-dispersion range | 0–53 | not stated | km s−1 | 7 | The Million-Years-Rosette model has a velocity dispersion (moment-2) map that ranges between $0{-}53\,\mathrm{km\,s^{-1}},$ |
| Circular Disk signed-residual histogram peak | 8.8 | not stated | km s−1 | 7 | It admits a narrow peak that is centered at $8.8\,\mathrm{km\,s^{-1}}$. |
| Filled-Rosette signed-residual histogram peak | 11.8 | not stated | km s−1 | 7 | peaks at $11.8\,\mathrm{km\,s^{-1}}$ and is fairly symmetric about this value. |
| Million-Years-Rosette signed-residual histogram peak | 4.3 | not stated | km s−1 | 7 | appears to be approximately symmetric about its peak value of $4.3\,\mathrm{km\,s^{-1}}$. |
| Circular Disk southwest contribution ΔW_SW | ≃0.22 | not stated | dimensionless | 8 | It is $\Delta \mathcal{W}_{SW} \simeq 0.22$ for the Circular Disk model |
| Filled-Rosette southwest contribution ΔW_SW | ≃0.20 | not stated | dimensionless | 8 | $\Delta \mathcal{W}_{SW} \simeq 0.20$ for the Filled-Rosette model |
| Million-Years-Rosette southwest contribution ΔW_SW | ≃0.18 | not stated | dimensionless | 8 | $\Delta \mathcal{W}_{SW} \simeq 0.18$ for the Million-Years-Rosette model. |
| Circular Disk W−ΔW_SW | ≃0.15 | not stated | dimensionless | 8 | $(\mathcal{W}-\Delta\mathcal{W}_{SW})\simeq 0.15$ for the Circular Disk model |
| Filled-Rosette W−ΔW_SW | ≃0.21 | not stated | dimensionless | 8 | $(\mathcal{W}-\Delta\mathcal{W}_{SW})\simeq 0.21$ for the Filled-Rosette model |
| Million-Years-Rosette W−ΔW_SW | ≃0.23 | not stated | dimensionless | 8 | $(\mathcal{W}-\Delta\mathcal{W}_{SW})\simeq 0.23$ for the Million-Years-Rosette model. |
| Stated Circular Disk advantage over rosettes after southwest subtraction | about 50 | not stated | % | 8 | It outperforms both rosette models by about 50% according to the fit metric without the residuals from the southwest region |

## Qualitative findings

- All three model classes can provide a good fit to the observational data  
  > "We find that all three classes of models can provide a good fit to the observational data" (Conclusion)
- Circular Disk is favored for the moment-1 map but underpredicts velocity dispersions  
  > "The best model for the observational velocity map (moment-1) is achieved by a Circular Disk model" (Conclusion); "the velocity field of this model is very smooth and has velocity dispersions (moment-2) in the range of $0{-}7.1\,\mathrm{km\,s^{-1}},$" (Circular Disk Model)
- Million-Years-Rosette reproduces several velocity substructures and is the closest match to dispersion properties  
  > "this model correctly captures the spatial profile of the CND and reproduces the broad blue-to-redshift gradient as well as several substructures seen in its velocity field." (The Million-Years-Rosette Model); "For the velocity dispersion properties of the CND, the closest fit is achieved by the Million-Years-Rosette model" (Conclusion)
- A majority of CND gas may be nearly circularized  
  > "Since the Circular Disk model is favored, our results suggest that a majority of the gas in the CND may be nearly circularized." (Conclusion)

## Claim tuples

- H: A circular disk or a rosette model can reproduce the CND velocity field and spatial distribution. | E: Compare beam-smeared mock observations over the parameter grids using velocity agreement and spatial coverage. | R: All three classes fit; Circular Disk has W = 0.37 and P = 1.61. | F: Circular Disk provides the best moment-1 model. | **supported**
- H: Rosette trajectories can capture CND velocity substructure and dispersion properties. | E: Construct rosette mock moment maps and compare their structure and dispersion ranges with observations. | R: Million-Years-Rosette reproduces several velocity substructures and has moment-2 values of 0–53 km s−1. | F: Million-Years-Rosette is the closest dispersion match, although its velocity predictions are less accurate than Circular Disk. | **partially**
- H: The preference for Circular Disk indicates that most CND gas is nearly circularized. | E: Compare circular and rosette model fits to the observed moment-1 map. | R: Circular Disk is favored over the two rosette classes. | F: A majority of the gas may be nearly circularized. | **partially**
- H: The southwest anomaly accounts for a substantial shared mismatch without changing the preferred model. | E: Estimate southwest contributions to W and compare the metrics after subtraction. | R: W−ΔW_SW ≃0.15, ≃0.21, and ≃0.23 for Circular Disk, Filled-Rosette, and Million-Years-Rosette. | F: Circular Disk remains favored; southwest dynamics likely include unmodeled non-gravitational processes. | **supported**

## Reasoning

- Why this data: Detailed CND HCN velocity map; crop retains prominent features and restricts the fit to a region with mild NSC flattening and small CND tilt.  
  > "is one of the most detailed maps of the CND." (Observational Map); "we crop it at $-50 ''\leq \Delta\mathrm{R.A.} \leq 50''$ and $-70'' \leq \Delta\mathrm{decl.} \leq 70''$ from the location of Sgr A\* to retain only the most prominent features of the CND." (Observational Map); "Thus, the data we fit is drawn from a region where the cluster exhibits only mild flattening and the tilt angle of the CND relative to the GP is small." (On the NSC Potential)
- Why this method: Use circular disks as a limiting baseline and rosettes for substructure; combine intensity weighting, spatial tolerance, and coverage penalties to avoid spurious thin-ring fits.  
  > "This model thus provides a simple limiting-case description of the CND that is a useful baseline against which more complex configurations can be studied." (Motivating the Models); "its intertwined red- and blue-shifted rosette segments non-uniformly cover the CND’s on-sky area and produce velocity substructure with steep gradients" (Motivating the Models); "as a measure of the model quality, we use the product $(\mathcal{W \cdot P})$, since it ties together how well a model captures both the velocities and spatial distribution of the CND." (Issues with an Unweighted Fit Metric)
- Alternative: Unweighted velocity RMS without coverage penalties rejected because it favors thin rings, fits small features, and weights all residuals equally  
  > "First, an unweighted velocity RMS is strongly biased toward thin-ring models that fail to capture a majority of the CND’s gas distribution" (Issues with an Unweighted Fit Metric); "rather than fitting the smallest features in the data, we need to prioritize correctly fitting general trends at scales that encapsulate numerous observational points." (Issues with an Unweighted Fit Metric); "Last, the unweighted velocity RMS assigns the same weight to all residuals, as it does not know about which parts of the observational velocity map are detected more robustly." (Issues with an Unweighted Fit Metric)
- Alternative: Removing the southwest feature before fitting considered but rejected because its exact boundaries are not well defined  
  > "It is possible to remove this feature from the observational map prior to comparison with the models. However, its exact boundaries are not well defined." (Residuals in the Southwest Region); "For consistency, we chose to retain it, since it punishes all models equally." (Residuals in the Southwest Region)
- Alternative: Axisymmetric cluster and fitted CND tilt deferred to future work  
  > "In future work, we intend to model the CND in an axisymmetric cluster and fit for its tilt relative to the GP." (On the NSC Potential)
- Alternative: Multiple rosette segments on different planes avoided because of a large, highly degenerate parameter space  
  > "modeling the CND via multiple rosette segments on different planes introduces a large and highly degenerate parameter space." (On the NSC Potential)
- Alternative: Alternative central mass and distance from (cite: Do2019) would change estimations by ∼5%  
  > "If we use the values from (cite: Do2019) instead, our estimations would change by $\sim5\%$." (Gravitational Potential in the Galactic Center)
- How they decided it was enough: Filled-Rosette integration extended to 10^8 yrs to remove coverage gaps and initialization sensitivity  
  > "It is constructed by evolving a single rosette trajectory for $10^{8}$ yrs." (Rosette Models); "The longer integration period ensures that the final velocity profile is insensitive to where the orbit is initialized and there are no gaps in the model’s on-sky area." (Rosette Models)
- Limitation (authors): Rosettes omit shocks at self-intersections and do not describe CND time evolution  
  > "We note that neither rosette models account for the shocks that would be produced at points of self-intersection along the planar trajectory." (Motivating the Models); "Consequently, they do not describe the time evolution of the CND." (Motivating the Models)
- Limitation (authors): Spherical potential and Galactic-plane-aligned orbits simplify the flattened NSC and tilted CND  
  > "Therefore, we presently adopt a spherical central potential and consider orbits that are aligned with the GP." (On the NSC Potential); "In future work, we intend to model the CND in an axisymmetric cluster and fit for its tilt relative to the GP." (On the NSC Potential)
- Limitation (authors): Circular Disk does not reproduce the observed clumpy structure and large local velocity dispersions  
  > "These properties are not reproduced by the smooth Circular Disk model." (Motivating the Models); "the velocity field of this model is very smooth and has velocity dispersions (moment-2) in the range of $0{-}7.1\,\mathrm{km\,s^{-1}},$" (Circular Disk Model)
- Limitation (authors): Southwest residuals likely involve non-gravitational processes omitted from the models; feature boundaries are poorly defined  
  > "Hence, the gas dynamics in this region are likely affected by non-gravitational processes, which we do not consider." (Residuals in the Southwest Region); "However, its exact boundaries are not well defined." (Residuals in the Southwest Region)
- Limitation (authors): Numerical simulations are needed for temporal evolution and possible stream collisions  
  > "Numerical simulations are required to account for the temporal evolution and possible collisions of the CND streams, which will be the subject of our future works." (Conclusion)
- Caveat (inferred, ours): No parameter uncertainties, likelihood, or statistical significance for model preference are supplied.
- Caveat (inferred, ours): Ranking sensitivity to the adopted spatial-weight scale, coverage radii, S/N cut, and grid limits is not demonstrated.
- Caveat (inferred, ours): The dispersion preference is based on reported map properties and ranges; no quantitative joint moment-1/moment-2 fit is specified.
- Caveat (inferred, ours): Mock cube intensities count model points; the consequences of trajectory sampling for emission weighting need checking.
- Caveat (inferred, ours): The weighted-median prose and footnote specify different cumulative weighting conventions.
- Caveat (inferred, ours): The southwest-subtracted metric is an approximate diagnostic with an unspecified exact region mask.

## Reproducibility

- Data public (paper): Data and images publicly available through the ALMA archive  
  > "The data and the images from this project are publicly available through the ALMA archive (cite: Hsieh_2021)." (Observational Map)
- Products in archive: Data and images for project 2017.1.00040.S  
  > "We construct it using data from the Atacama Large Millimeter/submillimeter Array (ALMA) project 2017.1.00040.S." (Observational Map); "The data and the images from this project are publicly available through the ALMA archive (cite: Hsieh_2021)." (Observational Map)
- Missing: Exact archive products and observational moment-map construction settings.
- Missing: Named software, source code, package versions, and execution environment.
- Missing: Orbit integration timestep, sampling cadence, and convergence checks.
- Missing: Exact model-cube binning, convolution boundaries, and moment-map support rules.
- Missing: Clarification of the weighted-median implementation.
- Missing: Exact southwest mask and subtraction procedure.
- Data volume (inferred): One observational spectral cube and approximately 3.3×10^5 mock model configurations; byte volume cannot be estimated from the supplied text.
- Score (inferred): 6/5, 6/10: public project, potential, parameter grids, beam matching, metrics, and numeric answer keys are documented; product selection, moment-map construction, numerical sampling, and implementation details remain incomplete.
- Rediscovery candidate: no, Data are explicitly public and results are numeric, but the recipe lacks enough implementation and observational-product detail for an exact independent rerun.

## Links

- Method: (cite: Chatzopoulos_2015) (Source of the adopted two-component spherical NSC γ-model.)
- Method: (cite: BT_2008) (Cited for apsidal precession and rosette trajectories in the central potential.)

## Checks

```json
{
 "quotes": 206,
 "quotes_ok": 206,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 38,
 "numeric_problems": 0,
 "fill": {
  "facts": 126,
  "stated": 90,
  "rate": 0.714
 },
 "evidence_ok": true
}
```
