# Constraining the gas distribution in the PDS 70 disc as a method to assess the effect of planet-disc interactions

`2023A&A...677A..76P` | Astronomy and Astrophysics 2023 | first author: Portilla-Revelo, B. | arXiv: 2306.16850 | DOI: 10.1051/0004-6361/202346607

Card schema 1.0 | model gemini-4-argon | depth full | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks, exoplanets, astrochemistry
- Question: What is the spatial distribution of the gas and dust components in the PDS 70 disk, and how do the axisymmetric substructures relate to planet-disk interactions?  
  > "We aim to determine the spatial distribution of the gas and dust components in the PDS 70 disk. The axisymmetric substructures observed in the resulting profiles are interpreted in the context of planet-disk interactions." (abstract)
- Target **PDS 70**: coordinates _not stated_; z/distance 113.47 pc  
  > "Distance | $113.47$ pc" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2019.1.01619.S
- bands: Band 6  
  > "We work with ALMA band 6 observations taken as part of the program #2019.1.01619.S (PI S. Facchini)." (Observational data)
- frequencies and spectral setup: 217.194-233.955 GHz  
  > "The instrument configuration was targeted to detect spatially-resolved emission from molecular lines at 0.1 arcsec resolution covering the frequency range 217.194-233.955 GHz." (Observational data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.15 arcsec (17 au) for line cubes; 67x50 mas (~8x6 au) for 855 um continuum  
  > "with a beam FWHM of ${\sim} 0.15$ arcsec ($17$ au) and an rms noise level of ${\sim} 1.0$ $\mathrm{mJy}\ \mathrm{beam}^{-1}$ estimated on the mean value of the spectrum." (Observational data); "The ray-traced image was convolved with a Gaussian beam of size $67\times 50$ mas $({\sim} 8 \times 6 \ \mathrm{au})$ and position angle of $61.5^\circ$ as in (cite: Isella2019)." (Benchmark for the continuum model)
- max recoverable scale: _not stated_
- sensitivity: ~1.0 mJy beam^-1  
  > "with a beam FWHM of ${\sim} 0.15$ arcsec ($17$ au) and an rms noise level of ${\sim} 1.0$ $\mathrm{mJy}\ \mathrm{beam}^{-1}$ estimated on the mean value of the spectrum." (Observational data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PI S. Facchini (#2019.1.01619.S)  
  > "We work with ALMA band 6 observations taken as part of the program #2019.1.01619.S (PI S. Facchini)." (Observational data)
- Line: 12CO J=2-1 (230.537939 GHz)
- Line: 13CO J=2-1 (220.398682 GHz)
- Line: C18O J=2-1 (219.560296 GHz)
- Other facility **VLT/SPHERE**: Observation in polarised-scattered light at 1.25 um  
  > "That model reproduces the ALMA observation at $855 \, \mu \mathrm{m}$ and the VLT/SPHERE observation in polarised-scattered light at $1.25\, \mu \mathrm{m}$." (Radiative transfer simulations: from the continuum to gas-phase models)
- Other facility **VLTI/GRAVITY**: Planet mass and orbital constraints used for comparison  
  > "An upper limit for the level of gas depletion can be obtained applying Eq. ([\[eq:kanawaga15\]](#eq:kanawaga15)) to the lowest value of the combined planet mass that is consistent with the VLTI/GRAVITY measurements (cite: Wang2021)." (Gas stirring in the gap of PDS 70)
- External data: Imaged ALMA Band 6 data cubes for 12CO, 13CO, and C18O and line emitting surfaces  
  > "In particular, we use the imaged set for , , and presented in Law et al. (in prep) with a beam FWHM of ${\sim} 0.15$ arcsec ($17$ au)" (Observational data); "Law et al. (in prep) derive line emitting surfaces for several molecules in PDS 70." (Emitting surfaces) [from Law et al. (in prep)]
- External data: ALMA Band 6 chemical inventory observations and data reduction  
  > "A full description of the observations and data reduction process is presented in (cite: Facchini2021) and Law et al. (in prep)." (Observational data) [from (cite: Facchini2021)]
- External data: 855 um ALMA continuum observation and beam parameters  
  > "The ray-traced image was convolved with a Gaussian beam of size $67\times 50$ mas $({\sim} 8 \times 6 \ \mathrm{au})$ and position angle of $61.5^\circ$ as in (cite: Isella2019)." (Benchmark for the continuum model) [from (cite: Isella2019)]
- External data: 2D dust continuum radiative transfer model in MCMax3D  
  > "The two-dimensional model for the continuum presented in (cite: Portilla-Revelo2022) is taken as a starting point to develop a thermochemical model for the source." (Radiative transfer simulations: from the continuum to gas-phase models) [from (cite: Portilla-Revelo2022)]
- External data: Disk inclination and position angle  
  > "In this step, we adopted for the disk an inclination of $i=51.7^\circ$ with respect to the plane of sky and a position angle of $160.4^\circ$ measured east-of-north (cite: Keppler2019)." (Post-processing the model and comparing to the observation) [from (cite: Keppler2019)]
- External data: Best fit orbital solution and planet mass estimates for PDS 70 b and c  
  > "Using the best fit orbital solution for PDS 70 b and c from (cite: Wang2021), we found $q_\mathrm{crit}=0.002$." (Linking gas depletion to planet masses); "For comparison, we overlay the mass estimates for both planets given by (cite: Wang2021) which were obtained via analysis of near-infrared data." (Linking gas depletion to planet masses) [from (cite: Wang2021)]
- Simulation/model as data: 2D continuum model developed in MCMax3D and translated into ProDiMo  
  > "The two-dimensional model for the continuum presented in (cite: Portilla-Revelo2022) is taken as a starting point to develop a thermochemical model for the source." (Radiative transfer simulations: from the continuum to gas-phase models); "The 2D dust mass density distribution was mapped from the spherical grid of `MCMax3D` onto the cylindrical grid of `ProDiMo`" (Radiative transfer simulations: from the continuum to gas-phase models)
- Simulation/model as data: Semi-analytic scaling relations from hydrodynamical simulations of planet-disk interactions  
  > "Following the theoretical results by (cite: Duffell2015) and (cite: Kanagawa2015), we use the results in Fig. [5](#fig:density_profiles) to estimate the degree of gas depletion in the gap of the PDS 70 disk." (Linking gas depletion to planet masses)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: 6.4 (used for synthetic cube post-processing)  
  > "First, we use CASA version 6.4 (cite: McMullin2007) to convolve the cube with a Gaussian beam." (Post-processing the model and comparing to the observation)
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
- continuum subtraction: imcontsub with zero-order polynomial fit on synthetic cubes  
  > "Then, we use the `imcontsub` task to subtract the continuum signal from each channel in the convolved cube; one-third of the total number of channels were assumed to be line-free and were used to fit a zero-order polynomial" (Post-processing the model and comparing to the observation)
- line free channels: one-third of the total number of channels in synthetic cubes  
  > "one-third of the total number of channels were assumed to be line-free and were used to fit a zero-order polynomial to estimate the continuum level." (Post-processing the model and comparing to the observation)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: convolve2d with Gaussian beam matching observations  
  > "First, we use CASA version 6.4 (cite: McMullin2007) to convolve the cube with a Gaussian beam. The size and orientation of the resolution element passed to the `convolve2d` task to match the observation can be found in Table" (Post-processing the model and comparing to the observation)
- final beam: 0.13'' x 0.10'' (-83.75 deg) for 12CO; 0.15'' x 0.12'' (-79.95 deg) for 13CO; 0.16'' x 0.13'' (-82.40 deg) for C18O; ~0.15 arcsec (17 au) average; 67x50 mas (61.5 deg) for 855 um continuum  
  > "$230.537939$ | $0.13'' \times 0.10'' \ (-83.75^\circ)$" (Table 2); "$220.398682$ | $0.15'' \times 0.12'' \ (-79.95^\circ)$" (Table 2); "$219.560296$ | $0.16'' \times 0.13'' \ (-82.40^\circ)$" (Table 2)
- final rms: ~1.0 mJy beam^-1  
  > "with a beam FWHM of ${\sim} 0.15$ arcsec ($17$ au) and an rms noise level of ${\sim} 1.0$ $\mathrm{mJy}\ \mathrm{beam}^{-1}$ estimated on the mean value of the spectrum." (Observational data)

### Inherited from earlier work

- ALMA observations and data reduction process  
  > "A full description of the observations and data reduction process is presented in (cite: Facchini2021) and Law et al. (in prep)." (Observational data) [from (cite: Facchini2021) and Law et al. (in prep)]
- Initial 2D dust continuum model and stellar/disk parameters  
  > "The two-dimensional model for the continuum presented in (cite: Portilla-Revelo2022) is taken as a starting point to develop a thermochemical model for the source." (Radiative transfer simulations: from the continuum to gas-phase models) [from (cite: Portilla-Revelo2022)]
- Reduced chemical network with 100 species and 1286 reactions  
  > "For the chemistry we use a reduced chemical network with $100$ species and $1286$ reactions (cite: Kamp2017)." (Radiative transfer simulations: from the continuum to gas-phase models) [from (cite: Kamp2017)]
- Ratios for 12CO/13CO and 12CO/C18O in ProDiMo  
  > "The ratios for $^{12}\mathrm{CO}/^{13}\mathrm{CO}$ and $^{12}\mathrm{CO}/\mathrm{C}^{18}\mathrm{O}$ are taken from (cite: Henkel1994)." (Radiative transfer simulations: from the continuum to gas-phase models) [from (cite: Henkel1994)]
- Disk inclination and position angle for radial profile extraction  
  > "In this step, we adopted for the disk an inclination of $i=51.7^\circ$ with respect to the plane of sky and a position angle of $160.4^\circ$ measured east-of-north (cite: Keppler2019)." (Post-processing the model and comparing to the observation) [from (cite: Keppler2019)]
- 855 um continuum Gaussian beam size and position angle  
  > "The ray-traced image was convolved with a Gaussian beam of size $67\times 50$ mas $({\sim} 8 \times 6 \ \mathrm{au})$ and position angle of $61.5^\circ$ as in (cite: Isella2019)." (Benchmark for the continuum model) [from (cite: Isella2019)]

### Not stated but needed to reproduce (our reading)

- Complete imaging and calibration parameters (e.g., Briggs robust weighting, uv-tapering, self-calibration, channel width) for the CO isotopologue cubes from Law et al. (in prep)
- Exact numerical values of the 12CO/13CO and 12CO/C18O ratios adopted from Henkel et al. (1994) inside ProDiMo
- Velocity range and channel spacing used when ray-tracing the synthetic CO data cubes in ProDiMo
- Exact functional form or numerical table of the fine-tuned dust surface density profile

## Analysis recipe

1. **Translate 2D dust model to ProDiMo and benchmark continuum**: Map 2D dust mass density from MCMax3D spherical grid to ProDiMo cylindrical grid, homogenise grain size distribution across both zones, adopt alpha = 5e-3, fine-tune dust surface density to reproduce 855 um continuum and 1.25 um scattered light, and benchmark with gas-to-dust ratio of 100.  
  > "The 2D dust mass density distribution was mapped from the spherical grid of `MCMax3D` onto the cylindrical grid of `ProDiMo` to subsequently derive the column density per grain size by integrating over the vertical coordinate." (Radiative transfer simulations: from the continuum to gas-phase models); "Therefore, to compensate for a lower submillimeter flux, we homogenised the dust size distribution across both zones to be in the range $0.001 \ \mu \mathrm{m}$ to $3\ \mathrm{mm}$." (Radiative transfer simulations: from the continuum to gas-phase models); "To verify the translation of the `MCMax3D` disk setup into the ProDiMo 2D setup, we run the `ProDiMo` model using the same constant gas-to-dust ratio of $100$ from (cite: Portilla-Revelo2022)." (Benchmark for the continuum model)
   - software: MCMax3D, ProDiMo
   - parameter: 120 radial and 100 vertical grid points logarithmically spaced; two zones divided at 41 au, outer radius 130 au  
  > "The cylindrical grid has 120 radial and 100 vertical points logarithmically spaced." (Radiative transfer simulations: from the continuum to gas-phase models); "The protoplanetary disk is simulated as a two-zone object with a boundary at $41$ au that delimits the transition from the gap’s outer edge to the outer disk in the continuum." (Radiative transfer simulations: from the continuum to gas-phase models)
   - parameter: a_min = 0.001 um, a_max = 3000 um, power index p = 3.9, alpha = 5e-3, H_0 = 10.61 au at r_0 = 100 au, beta = 1.14  
  > "Turbulent settling parameter: $\alpha$ | $5\times 10^{-3}$ | $5\times 10^{-3}$" (Table 1); "Flaring exponent: $\beta$ | 1.14 | 1.14" (Table 1); "Scale height at $r_0$: $H_0$ (au) | 10.61 | 10.61" (Table 1)
   - assumption: Dust grains made of 19.2% carbon, 60.8% silicates, and 20% vacuum by volume; Dubrulle et al. (1995) dust settling; Gaussian vertical gas profile  
  > "Both zones are populated with dust grains made of carbon and silicates in percentages by volume of $19.2\%$ and $60.8\%$, respectively, and with a fraction of vacuum accounting for $20\%$ of the grain volume." (Radiative transfer simulations: from the continuum to gas-phase models); "In `ProDiMo`, the Shakura-Sunyaev $\alpha$ parameter (cite: Shakura1973) mimics dust settling according to (cite: Dubrulle1995)" (Radiative transfer simulations: from the continuum to gas-phase models); "We assume a Gaussian vertical profile:" (Radiative transfer simulations: from the continuum to gas-phase models)
   - fitting: Manual fine-tuning to match SED, 855 um continuum profile, and 1.25 um polarised scattered light  
  > "A final fine-tune to the surface density profile was required to reproduce the ALMA continuum image at $855\ \mu \mathrm{m}$ and the polarised scattered image at $1.25 \ \mu \mathrm{m}$." (Radiative transfer simulations: from the continuum to gas-phase models)
   - validation: Comparison of ProDiMo synthetic SED and 855 um radial profile (convolved with 67x50 mas beam) against observations and MCMax3D  
  > "The ray-traced image was convolved with a Gaussian beam of size $67\times 50$ mas $({\sim} 8 \times 6 \ \mathrm{au})$ and position angle of $61.5^\circ$ as in (cite: Isella2019). A comparison to the observed data set is made in Fig. [3](#fig:sed)." (Benchmark for the continuum model)
2. **Derive initial semi-analytic gas column density profile from optically thin C18O**: Relate observed azimuthally-averaged C18O moment-zero brightness temperature to C18O surface density assuming optically thin LTE slab emission, then scale to total gas surface density.  
  > "Combining the semi-analytic model given by Eq. ([\[eq:Tb_vs_Sigma\]](#eq:Tb_vs_Sigma)) with the observed azimuthally-averaged profile of the moment zero map for , we obtain an initial approximation to the column density distribution of  molecules." (Modelling optically thin lines)
   - parameter: i = 51.7 deg  
  > "In this step, we adopted for the disk an inclination of $i=51.7^\circ$ with respect to the plane of sky and a position angle of $160.4^\circ$ measured east-of-north (cite: Keppler2019)." (Post-processing the model and comparing to the observation)
   - assumption: C18O is optically thin and in LTE; excitation temperature equals midplane dust temperature; 12CO/C18O ~ 560; 12CO/H2 ~ 10^-4  
  > "For simplicity, the position-dependent excitation temperature $T_\mathrm{exc}(r)$ is assumed to be equal to the dust temperature at the corresponding midplane location" (Modelling optically thin lines); "we adopt the local interstellar medium value for the ratio $\ce{^{12}CO}/\ce{C^{18}O}\approx 560$ (cite: Wilson1994) alongside a canonical $\ce{^{12}CO}/\mathrm{H}_2 \approx 10^{-4}$ (cite: Dickman1978)." (Modelling optically thin lines)
   - fitting: Direct semi-analytic inversion via Eq. 4  
  > "Equation ([\[eq:N_up\]](#eq:N_up)) can be finally expressed in terms of the  surface density $\Sigma_\mathrm{C18O}$ as" (Modelling optically thin lines)
   - validation: Used as initial input for full thermochemical ProDiMo simulation  
  > "We use this initial gas distribution to run a first full thermochemical `ProDiMo` model" (Modelling optically thin lines)
3. **Iteratively solve for gas column density via thermochemical modelling and post-processing**: Run ProDiMo thermochemical model, ray-trace CO isotopologue cubes, convolve with Gaussian beam and subtract continuum in CASA, collapse to moment-0 maps, extract azimuthally-averaged radial profiles with GoFish, and iteratively multiply gas surface density by point-by-point C18O observation/model ratios until relative difference is <10%.  
  > "First, we use CASA version 6.4 (cite: McMullin2007) to convolve the cube with a Gaussian beam." (Post-processing the model and comparing to the observation); "The azimuthally-averaged radial profile of the moment-zero map is obtained using the `GoFish` package (cite: Teague2019)." (Post-processing the model and comparing to the observation); "We iterate over the same procedure until the relative difference between modelled and observed profiles for is $< 10\%$." (Modelling optically thin lines)
   - software: ProDiMo, CASA, GoFish
   - parameter: 5 iterations; radial bin spacing theta_maj/4; 1/3 line-free channels for zero-order continuum subtraction; no sigma clip in immoments; solar C/O = 0.457; PAH abundance = 1% ISM; thermal accommodation coefficient = 0.2  
  > "The moment zero map was binned radially with a spacing of $\theta_\mathrm{maj}/4$, where $\theta_\mathrm{maj}$ is the major axis of the resolution element of the observation." (Post-processing the model and comparing to the observation); "After five iterations, the procedure outlined in Sect. [2.4](#subsection:fit_thin) yielded a relative error $< 10\%$ with respect to the intensity profile of the observation." (Gas column density and gas-to-dust ratio profiles in the PDS 70 disk); "Our best representative model uses a canonical solar C/O ratio of $0.457$ that is assumed to be constant across the disk." (Variations in the C/O ratio)
   - assumption: Reduced chemical network (100 species, 1286 reactions); no CO isotopologue chemistry or isotope-selective photodissociation; fixed dust column density during iterations  
  > "In our model, CO isotopologue chemistry is not included and consequently the effects of isotope-selective photodissociation of CO are not simulated." (Radiative transfer simulations: from the continuum to gas-phase models); "During the iterations, the dust column density is kept fixed and only the gas column density is varied." (Modelling optically thin lines)
   - fitting: Point-by-point iterative scaling until C18O radial profile relative difference < 10%, plus visual inspection  
  > "The resulting radial profiles of the synthetic moment zero maps are overlaid to the observations and the goodness of the model is determined by visual inspection." (Post-processing the model and comparing to the observation); "We iterate over the same procedure until the relative difference between modelled and observed profiles for is $< 10\%$." (Modelling optically thin lines)
   - validation: Cross-check predicted 13CO and 12CO radial profiles, integrated line fluxes within 130 au, and 15%-85% vertical line emitting surfaces against observations  
  > "First, we can compare our results to the line flux emitted by the disk within the first $130$ au." (Modelling optically thick lines); "The comparison between the area of emission to the emitting surface observationally derived can be used as another proof of the robustness of the model." (Emitting surfaces)
4. **Integrate gas and dust masses and derive gas-to-dust ratio profile**: Divide gas surface density by dust surface density radially, and integrate surface densities azimuthally and radially over the dust cavity (16-41 au), inner disk (0.04-16 au), and full modelled disk (<130 au).  
  > "The amount of gas inside the dust gap $M_{\mathrm{gas}}^\mathrm{cav}$ can be readily estimated by integrating the gas column density over the radial extension of the dust cavity from $16$ au to $41$ au and over the entire azimuth." (Estimating the gas mass inside the dust gap)
   - parameter: Dust gap: 16 au to 41 au; inner disk: 0.04 au to 16 au; outer limit: 130 au  
  > "For the inner disk extending from $0.04$ au to $16$ au, the retrieved value for the gas mass is $7.6 \times 10^{-4}\, M_{\mathrm{Jup}}$" (Estimating the gas mass inside the dust gap)
   - assumption: Axisymmetric disk  
  > "For an axisymmetric disk, the gas mass relates to the column density via" (Estimating the gas mass inside the dust gap)
   - fitting: _not stated_
   - validation: _not stated_
5. **Estimate planet masses and assess gas stirring from gas gap depletion**: Measure gas surface density ratio between the orbit of PDS 70 c (34.3 au) and the peak density at the gap outer edge (75 au), and compare against multi-planet and single-planet hydrodynamical scaling relations from Duffell & Dong (2015) and Kanagawa et al. (2015).  
  > "Following the theoretical results by (cite: Duffell2015) and (cite: Kanagawa2015), we use the results in Fig. [5](#fig:density_profiles) to estimate the degree of gas depletion in the gap of the PDS 70 disk." (Linking gas depletion to planet masses); "We directly compare Eq. ([\[eq:gas_depletion_level\]](#eq:gas_depletion_level)) with Eq.(14) from (cite: Duffell2015) which is the fitting formula connecting the gas depletion with the planet mass." (Linking gas depletion to planet masses)
   - parameter: r_0 = 75 au, a_c = 34.3 au, a_b = 20.4 au, q_crit = 0.002, h_p = 0.059 at 34.3 au, alpha = 5e-3  
  > "The location of the gap edge for the gas distribution is assumed to match that of the peak value and therefore we adopt $\Sigma_\mathrm{0}=0.13\, \mathrm{g}\, \mathrm{cm}^{-2}$ at $r=75 \ \mathrm{au}$." (Linking gas depletion to planet masses); "The semi-major axis of planet c is $a_\mathrm{c}=34.3$ au (cite: Wang2021) and at that radius, the gas surface density is $\Sigma_\mathrm{p}=7.0\times 10^{-3} \ \mathrm{g}\ \mathrm{cm}^{-2}$." (Linking gas depletion to planet masses); "From the model, we also find a sound speed value of $0.26 \ \mathrm{km}\ \mathrm{s}^{-1}$ at $34.3$ au, implying $h_\mathrm{p}=0.059$ at the same radius." (Footnotes)
   - assumption: Equal-mass planets on circular orbits in 2:1 mean motion resonance; globally isothermal disk in hydrodynamical scaling law  
  > "Planets were assumed to have the same mass and to move on circular orbits under the effect of the combined gravitational potential of the star and the other planets. They were located in a 2:1 mean motion resonance with one another." (Linking gas depletion to planet masses)
   - fitting: Analytical intersection of measured depletion ratio with Eq. 14 of Duffell & Dong (2015) and Eq. 6 of Kanagawa et al. (2015)  
  > "The result is shown in Fig. [6](#fig:planet_mass) where the horizontal line intersects the theoretical curve at a planet mass of $4 \, M_{\mathrm{Jup}}$." (Linking gas depletion to planet masses)
   - validation: Comparison with VLTI/GRAVITY near-infrared planet mass estimates from Wang et al. (2021) and sensitivity tests for dust filtration, alpha, local dust heating, and C/O ratio  
  > "For comparison, we overlay the mass estimates for both planets given by (cite: Wang2021) which were obtained via analysis of near-infrared data." (Linking gas depletion to planet masses); "Instead, in the following subsections we investigate the robustness of our mass estimate for some key parameters." (Linking gas depletion to planet masses)

## Software

- **MCMax3D** : 3D dust continuum radiative transfer modelling used as starting point  
  > "The model for the dust emission was developed in the three-dimensional version of the continuum radiative transfer code `MCMax3D` (cite: Min2009)" (Radiative transfer simulations: from the continuum to gas-phase models)
- **ProDiMo** ebd47ddf: 2D radiation thermochemical disk modelling and line/continuum ray-tracing  
  > "To translate it into the thermochemical code `ProDiMo` (cite: Woitke2009; Kamp2010; Thi2011; Woitke2016)" (Radiative transfer simulations: from the continuum to gas-phase models); "In this work, we use `ProDiMo` version `ebd47ddf`. The code can be found in <https://prodimo.iwf.oeaw.ac.at/>" (Footnotes)
- **CASA** 6.4: Post-processing synthetic CO data cubes using convolve2d, imcontsub, and immoments  
  > "First, we use CASA version 6.4 (cite: McMullin2007) to convolve the cube with a Gaussian beam." (Post-processing the model and comparing to the observation); "Then, we use the `imcontsub` task to subtract the continuum signal from each channel in the convolved cube" (Post-processing the model and comparing to the observation); "Finally, we use the task `immoments` to collapse the cube and create the moment-zero map for each transition" (Post-processing the model and comparing to the observation)
- **GoFish** : Extracting azimuthally-averaged radial profiles of moment-zero maps  
  > "The azimuthally-averaged radial profile of the moment-zero map is obtained using the `GoFish` package (cite: Teague2019)." (Post-processing the model and comparing to the observation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk dust mass (inside 130 au) | 3.5e-5 | not stated | M_odot | 1 | This change produces a disk dust mass of $3.5\times 10^{-5}\ M_{\odot}$, that is $22\%$ less than the mass estimated in (cite: Portilla-Revelo2022). |
| Total disk gas mass (inside 130 au) | >3.0e-4 | not stated | M_odot | 4 | The total gas mass of the best representative model is $>3.0 \times 10^{-4} \, M_{\odot}$ (inside $130$ au). |
| Gas mass inside the dust gap (16-41 au) | 3.2e-3 | not stated | M_Jup | 4 | which yields $M_{\mathrm{gas}}^\mathrm{cav}\approx 3.2 \times 10^{-3}\, M_{\mathrm{Jup}}$. |
| Dust mass inside the dust gap (16-41 au) | 5.1e-6 | not stated | M_Jup | 4 | If we repeat this procedure for the dust component, we obtain $M_{\mathrm{dust}}^\mathrm{cav}\approx 5.1 \times 10^{-6}\, M_{\mathrm{Jup}}$. |
| Average gas-to-dust ratio in the dust gap (16-41 au) | 630 | not stated | dimensionless | 4 | Therefore, we find an average gas-to-dust ratio of ${\sim} 630$ within the limits of the dust gap. |
| Inner disk gas mass (0.04-16 au) | 7.6e-4 | not stated | M_Jup | 4 | For the inner disk extending from $0.04$ au to $16$ au, the retrieved value for the gas mass is $7.6 \times 10^{-4}\, M_{\mathrm{Jup}}$ and $7.9 \times 10^{-5}\, M_{\mathrm{Jup}}$ for the dust mass, implying a gas-to-dust ratio of ${\sim} 10$. |
| Inner disk dust mass (0.04-16 au) | 7.9e-5 | not stated | M_Jup | 4 | For the inner disk extending from $0.04$ au to $16$ au, the retrieved value for the gas mass is $7.6 \times 10^{-4}\, M_{\mathrm{Jup}}$ and $7.9 \times 10^{-5}\, M_{\mathrm{Jup}}$ for the dust mass, implying a gas-to-dust ratio of ${\sim} 10$. |
| Peak gas surface density (Sigma_0 at r = 75 au) | 0.13 | not stated | g cm^-2 | 5 | The location of the gap edge for the gas distribution is assumed to match that of the peak value and therefore we adopt $\Sigma_\mathrm{0}=0.13\, \mathrm{g}\, \mathrm{cm}^{-2}$ at $r=75 \ \mathrm{au}$. |
| Minimum gas surface density in gap (Sigma_min at r = 20.4 au) | 3.3e-3 | not stated | g cm^-2 | 5 | The minimum occurs at $20.4$ au and has a value of $\Sigma_\mathrm{min}=3.3\times 10^{-3} \ \mathrm{g}\ \mathrm{cm}^{-2}$. |
| Gas density drop factor at 20 au | 39 | not stated | dimensionless | 5 | These values imply a gas density drop by a factor of ${\sim} 39$ at $20$ au. |
| Gas surface density at PDS 70 c location (Sigma_p at a_c = 34.3 au) | 7.0e-3 | not stated | g cm^-2 | 5 | The semi-major axis of planet c is $a_\mathrm{c}=34.3$ au (cite: Wang2021) and at that radius, the gas surface density is $\Sigma_\mathrm{p}=7.0\times 10^{-3} \ \mathrm{g}\ \mathrm{cm}^{-2}$. |
| Level of gas depletion at PDS 70 c (Sigma_p / Sigma_0) | 0.054 | not stated | dimensionless | 5 | \frac{\Sigma_\mathrm{p}}{\Sigma_\mathrm{0}}\approx 0.054, |
| Gas density drop factor at PDS 70 c (34 au) | 19 | not stated | dimensionless | 5 | which is equivalent to a density drop factor of $\mathbf{{\sim} 19}$ at $a_\mathrm{c}=34$ au. |
| Estimated mass of each planet (PDS 70 b and c, multi-planet model) | 4 | not stated | M_Jup | 5 | Accordingly, we constrain the mass of each planet to be roughly $4 M_{\mathrm{Jup}}$. |
| Estimated planet mass accounting for dust filtration | 5 | not stated | M_Jup | 5 | This brings our initial estimate of $\mathbf{4\ M_{\mathrm{Jup}}}$ up to $\mathbf{5 \, M_{\mathrm{Jup}}}$. |
| Modelled integrated 12CO J=2-1 flux within 130 au | 3624 | not stated | mJy km s^-1 | 3 | The model predicts an integrated value of $3624 \ \mathrm{mJy}\ \mathrm{km}\ \mathrm{s}^{-1}$ for . This is close to the observed value of $3545 \ \mathrm{mJy}\ \mathrm{km}\ \mathrm{s}^{-1}$. |
| Observed integrated 12CO J=2-1 flux within 130 au | 3545 | not stated | mJy km s^-1 | 3 | The model predicts an integrated value of $3624 \ \mathrm{mJy}\ \mathrm{km}\ \mathrm{s}^{-1}$ for . This is close to the observed value of $3545 \ \mathrm{mJy}\ \mathrm{km}\ \mathrm{s}^{-1}$. |
| Modelled integrated 13CO J=2-1 flux within 130 au | 1355 | not stated | mJy km s^-1 | 3 | For we obtain a value of $1355 \ \mathrm{mJy}\ \mathrm{km}\ \mathrm{s}^{-1}$ which is again in good agreement to the observed value of $1331 \ \mathrm{mJy}\ \mathrm{km}\ \mathrm{s}^{-1}$. |
| Observed integrated 13CO J=2-1 flux within 130 au | 1331 | not stated | mJy km s^-1 | 3 | For we obtain a value of $1355 \ \mathrm{mJy}\ \mathrm{km}\ \mathrm{s}^{-1}$ which is again in good agreement to the observed value of $1331 \ \mathrm{mJy}\ \mathrm{km}\ \mathrm{s}^{-1}$. |

## Qualitative findings

- A homogeneous dust size distribution across the disk combined with low viscosity (alpha = 5e-3) reproduces the Band 6 continuum and scattered light observations.  
  > "We demonstrate that the combination of a homogeneous dust size distribution across the disk and relatively low values of the viscosity ($\alpha \lesssim 5\times 10^{-3}$) can explain the band 6 continuum observations." (abstract)
- The gas-to-dust ratio varies from ~1000 in the cavity to ~10 beyond the gap outer edge (r >= 40 au), consistent with dust accumulation in a planet-induced pressure bump.  
  > "The value of the gas-to-dust ratio ranges from $10$ in the region beyond the cavity’s outer edge ($r\gtrsim 40$ au) to almost $1000$ in the cavity." (Gas column density and gas-to-dust ratio profiles in the PDS 70 disk)
- The minimum of the gas surface density at 20.4 au matches the semi-major axis of planet PDS 70 b.  
  > "The minimum occurs at $20.4$ au and has a value of $\Sigma_\mathrm{min}=3.3\times 10^{-3} \ \mathrm{g}\ \mathrm{cm}^{-2}$. Interestingly, the location of the minimum matches the best fit solution for the semi-major axis of PDS 70 b found by (cite: Wang2021)." (Linking gas depletion to planet masses)
- 85% of the 12CO and 13CO emission in the outer disk (r > 60 au) originates from z > 6 au and z > 3 au above the midplane, respectively.  
  > "We estimate that $85\%$ of the and emission originating in the outer disk ($r>60$ au) comes from of $z > 6$ au and $z > 3$ au above the midplane, respectively." (Conclusions)

## Claim tuples

- H: A homogeneous dust grain size distribution across the disk combined with lower turbulent viscosity (alpha = 5e-3) can explain the ALMA 855 um continuum and 1.25 um scattered light observations. | E: Translated the MCMax3D dust model into ProDiMo, set alpha = 5e-3 and grain sizes 0.001 um to 3 mm across both zones, fine-tuned the dust surface density, and ray-traced the SED and 855 um continuum. | R: The synthetic SED and 855 um azimuthally-averaged continuum radial profile match the observations with a dust mass of 3.5e-5 M_odot. | F: Multiple degeneracies in forward modelling allow explaining the continuum observables with a homogeneous dust size distribution and alpha = 5e-3. | **supported**
- H: Planet-disk interactions in PDS 70 drive a radial variation in the gas-to-dust ratio and create a pressure bump at the outer edge of the gap. | E: Derived the radial gas surface density profile by iteratively fitting the C18O moment-0 profile in ProDiMo while keeping the continuum-constrained dust surface density fixed. | R: The gas-to-dust ratio spans from ~1000 inside the cavity (mean ~630 between 16-41 au) to ~10 beyond the cavity outer edge (r >= 40 au), with a gas minimum at 20.4 au and peak at 75 au. | F: The sharp gradient and low gas-to-dust ratio beyond 40 au are consistent with dust accumulation in a pressure bump driven by planet-disk interactions. | **supported**
- H: The level of gas depletion in the PDS 70 gap constrains the masses of the embedded protoplanets PDS 70 b and c. | E: Measured the gas surface density ratio Sigma_p/Sigma_0 = 0.054 (drop factor ~19 at 34.3 au relative to 75 au) and applied the multi-planet hydrodynamical scaling relation of Duffell & Dong (2015). | R: The depletion level corresponds to an equal planet mass of ~4 M_Jup for each planet (increasing to 5 M_Jup if dust filtration is included). | F: The submillimeter-derived planet mass of ~4 M_Jup is consistent with independent near-infrared estimates from Wang et al. (2021). | **supported**
- H: Mutual gravitational perturbations from the two planets stir the gas in the common gap, making it shallower than a single-planet gap. | E: Calculated the upper limit on Sigma_p/Sigma_0 for a single planet of 2.5 M_Jup using Kanagawa et al. (2015) and compared it to the observed depletion ratio of 0.054. | R: The single-planet depletion upper limit is 9.0e-3, which is a factor of 6 lower (deeper) than the measured value of 0.054. | F: Gas stirring processes driven by the two planets are operating in the common gap of the PDS 70 disk. | **supported**

## Reasoning

- Why this data: PDS 70 is the first disk with two young planets directly imaged within a dust-depleted gap, and high-resolution (0.15'') ALMA Band 6 observations of 12CO, 13CO, and C18O provide both optically thin and thick tracers to constrain gas density and temperature.  
  > "The pre-transitional disk around the star PDS 70 is the first case of two young planets imaged within a dust depleted gap that was likely carved by themselves." (abstract); "This suggests that  emission is moderately optically thick and accordingly, we assume  as a suitable proxy for optically thin emission." (Modelling optically thin lines)
- Why this method: Using a semi-analytic LTE inversion of C18O to initialize an iterative ProDiMo forward model avoids an expensive parameter space exploration while accounting for radial cumulative radiative transfer and thermochemical effects.  
  > "the semi-analytic approach is still useful because we do not require to perform an expensive exploration of the parameter space that defines the gas column density." (Modelling optically thin lines); "Nonetheless, the semi-analytic approach ignores complexities like any cumulative effect on the heating-cooling balance and on the chemistry that could arise from the column of material built up in the radial direction" (Modelling optically thin lines)
- Alternative: Using 13CO as the optically thin tracer (rejected because observed 13CO/C18O intensity ratios reach ~3 vs the ISM optical depth ratio of 7.3, showing 13CO is moderately optically thick)  
  > "However, the observed profiles suggest that there are regions in the disk where this ratio is close to 3, too low to be consistent with the uncertainties in the isotopologue ratio measurement. This suggests that  emission is moderately optically thick" (Modelling optically thin lines)
- Alternative: Alternative dust filtration model with segregated grain sizes (a_max = 100 um in inner disk, 3 mm in outer disk) and higher alpha (2e-2 inner, 1e-2 outer) from Portilla-Revelo et al. (2022)  
  > "Building on the dust model in (cite: Portilla-Revelo2022) that used $\alpha=2\times 10^{-2}$ and $a_{\mathrm{max}}=100\ \mu \mathrm{m}$, and $\alpha=10^{-2}$ and $a_{\mathrm{max}}=3$ mm, in the inner and outer zones respectively, we construct an alternative model for the gas" (Dependence on \alpha and \Sigma_\mathrm{0})
- Alternative: Locally increasing dust surface density by ~30% between 27 and 60 au to boost gas heating and improve the optically thick 12CO profile fit in the gap  
  > "We artificially increased the dust mass contained between $27$ and $60$ au by a factor of ${\sim} 30\%$ by deforming the column density using a Gaussian function with a standard deviation of $9$ au within those limits" (Modelling optically thick lines)
- Alternative: Increasing the elemental C/O ratio from 0.457 to ~1.1 to test sensitivity to carbon chemistry  
  > "To estimate the effect that a potentially higher C/O ratio would have in our synthetic observables, we decreased the elemental abundance of oxygen such that the C/O ratio goes up to ${\sim}1.1$." (Variations in the C/O ratio)
- How they decided it was enough: Iterations on the gas column density were stopped once the relative difference between the modelled and observed C18O radial intensity profiles was below 10% (achieved after 5 iterations).  
  > "We iterate over the same procedure until the relative difference between modelled and observed profiles for is $< 10\%$." (Modelling optically thin lines); "After five iterations, the procedure outlined in Sect. [2.4](#subsection:fit_thin) yielded a relative error $< 10\%$ with respect to the intensity profile of the observation." (Gas column density and gas-to-dust ratio profiles in the PDS 70 disk)
- Limitation (authors): CO isotopologue chemistry and isotope-selective photodissociation are not included in the chemical network.  
  > "In our model, CO isotopologue chemistry is not included and consequently the effects of isotope-selective photodissociation of CO are not simulated." (Radiative transfer simulations: from the continuum to gas-phase models)
- Limitation (authors): ProDiMo only models isotropic scattering rather than a full scattering phase function.  
  > "While `MCMax3D` uses a full treatment of the scattering phase function, `ProDiMo` only models isotropic scattering." (Benchmark for the continuum model)
- Limitation (authors): The model is radially restricted to 130 au by the sensitivity of the 855 um ALMA continuum observation, so total gas mass is a lower limit.  
  > "The dust model is limited by the ALMA continuum sensitivity at $855 \mu \mathrm{m}$ which explains why it is radially extended only up to $130$ au." (Radiative transfer simulations: from the continuum to gas-phase models); "The radial extent of the gas disk in PDS 70 is expected to go well beyond that traced by the (sub)millimeter dust. Thus, we interpret this value as a lower limit." (Estimating the gas mass inside the dust gap)
- Limitation (authors): Inner disk (<16 au) mass estimates are uncertain due to the limited spatial resolution (~17 au) of the ALMA line data.  
  > "These quantities for the inner disk must be taken with caution due to the limited spatial resolution of our data set." (Estimating the gas mass inside the dust gap)
- Limitation (authors): The planet mass estimate is degenerate and equal for both planets because the Duffell & Dong (2015) hydrodynamical simulations assumed equal-mass planets and fixed alpha = 10^-2.  
  > "We stress that the planet mass derived through this method is degenerate by construction because the underlying hydrodynamical models assumed equal mass planets." (Linking gas depletion to planet masses)
- Limitation (authors): Forward modelling prevents a full statistical uncertainty analysis, and the degeneracy between alpha and planet mass is not broken.  
  > "Due to the forward modelling approach implemented in this work, we cannot provide a full statistical account of the uncertainties associated to each parameter in the thermo-chemical model." (Linking gas depletion to planet masses); "Although these experiments help to quantify the impact of $\alpha$ on the mass estimate, they do not break the degeneracy between both quantities" (Dependence on \alpha and \Sigma_\mathrm{0})
- Caveat (inferred, ours): Omission of isotope-selective photodissociation can lead to an underestimation of the true gas surface density in the dust-depleted gap where C18O may be selectively photodissociated.
- Caveat (inferred, ours): Inconsistency between the turbulent viscosity alpha = 5e-3 adopted in ProDiMo (for vertical dust settling) and the fixed alpha = 1e-2 assumed in the Duffell & Dong (2015) hydrodynamical scaling law.
- Caveat (inferred, ours): Reliance on visual inspection for 13CO/12CO and continuum fits rather than quantitative chi-squared or Bayesian inference.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: ProDiMo version ebd47ddf is available at https://prodimo.iwf.oeaw.ac.at/  
  > "In this work, we use `ProDiMo` version `ebd47ddf`. The code can be found in <https://prodimo.iwf.oeaw.ac.at/>" (Footnotes)
- Missing: Imaged CO isotopologue cubes and radial profiles from Law et al. (in prep)
- Missing: Exact numerical table of the fine-tuned dust surface density profile mapped from MCMax3D
- Missing: ProDiMo input parameter files (Parameter.in) and exact spectral grid settings for ray-tracing
- Missing: Exact values of the 12CO/13CO and 12CO/C18O ratios taken from Henkel et al. (1994)
- Data volume (inferred): ~5-20 GB (high-resolution 0.15'' ALMA Band 6 spectral line cubes for three CO isotopologues plus ProDiMo simulation outputs)
- Score (inferred): 55/5, The thermochemical modelling workflow, ProDiMo commit hash (ebd47ddf), CASA post-processing tasks, and physical parameters (Table 1) are well documented, and the semi-analytic inversion equations are explicit. However, the observational data cubes and emitting surfaces come from an unpublished paper (Law et al. in prep), the exact numerical dust surface density profile is only plotted rather than tabulated, and initial dust setup details are inherited from Portilla-Revelo et al. (2022).
- Rediscovery candidate: no, Reproduction requires the specific reduced CO isotopologue cubes from Law et al. (in prep) and the custom 2D dust density grid from Portilla-Revelo et al. (2022), neither of which is fully tabulated in the paper.

## Links

- Method: (cite: Min2009) (MCMax3D continuum radiative transfer code)
- Method: (cite: Woitke2009; Kamp2010; Thi2011; Woitke2016) (ProDiMo radiation thermochemical disk code)
- Method: (cite: Kamp2017) (Reduced chemical network of 100 species and 1286 reactions used in ProDiMo)
- Method: (cite: Teague2019) (GoFish package used to extract azimuthally-averaged radial profiles)
- Method: (cite: Kanagawa2015) (Single-planet hydrodynamical scaling relation between gas gap depth and planet mass)
- Method: (cite: Duffell2015) (Multi-planet hydrodynamical scaling relation between gas gap depth and planet mass)
- Companion: (cite: Portilla-Revelo2022) (Previous paper by the same lead author providing the 2D MCMax3D dust continuum and scattered-light model of PDS 70)
- Companion: (cite: Facchini2021) (Overview paper presenting the ALMA Band 6 chemical inventory observations of PDS 70 from program 2019.1.01619.S)
- Companion: Law et al. (in prep) (Companion study providing the high-resolution imaged CO isotopologue cubes and empirical line emitting surfaces for PDS 70)

## Checks

```json
{
 "quotes": 144,
 "quotes_ok": 144,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 2,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 19,
 "numeric_problems": 0,
 "fill": {
  "facts": 104,
  "stated": 75,
  "rate": 0.721
 },
 "evidence_ok": true
}
```
