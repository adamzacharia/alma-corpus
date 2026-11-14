# The initial conditions for young massive cluster formation in the Galactic Centre: convergence of large-scale gas flows

`2022MNRAS.514..578W` | Monthly Notices of the Royal Astronomical Society 2022 | first author: Williams, Bethan A. | arXiv: 2205.07807 | DOI: 10.1093/mnras/stac1378

Card schema 1.0 | model gemini-4-argon | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: Determine whether star formation is occurring at the scale of individual cores (~1000 au) in Galactic Centre dust ridge cloud ‘d’ (G0.412+0.052) and understand its fate by investigating the gas density distribution and large-scale gas kinematics.  
  > "We aim to determine whether or not star formation is occurring at the scale of individual cores and understand the fate of this cloud by investigating the gas density distribution in relation to large scale gas kinematics." (Introduction)
- Target **G0.412+0.052 (Cloud 'd' / clump 'd6')**: coordinates RA ~ 266.595 deg, Dec ~ -28.560 deg (G0.412+0.052)  
  > "showing that Galactic Centre dust ridge ‘Cloud d’ (G0.412$+$0.052, mass $=7.6 \times 10^4$ M$_{\odot}$, radius $=3.2$ pc) has the potential to become an Arches-like YMC" (Abstract); "The angular resolution is $\sim$0.13${}^{\prime\prime}$, which allows us to resolve scales of 1000 au, the scale of individual cores, at a distance of 8.1 kpc (cite: abuter19)." (Observations); "1 | 266.5949552 | -28.56055698 | 0.71 | 1.71 | 6.04 | 0.06 | 0.54" (Tables); z/distance 8.1 kpc  
  > "showing that Galactic Centre dust ridge ‘Cloud d’ (G0.412$+$0.052, mass $=7.6 \times 10^4$ M$_{\odot}$, radius $=3.2$ pc) has the potential to become an Arches-like YMC" (Abstract); "The angular resolution is $\sim$0.13${}^{\prime\prime}$, which allows us to resolve scales of 1000 au, the scale of individual cores, at a distance of 8.1 kpc (cite: abuter19)." (Observations); "1 | 266.5949552 | -28.56055698 | 0.71 | 1.71 | 6.04 | 0.06 | 0.54" (Tables); distance from (cite: abuter19)  
  > "showing that Galactic Centre dust ridge ‘Cloud d’ (G0.412$+$0.052, mass $=7.6 \times 10^4$ M$_{\odot}$, radius $=3.2$ pc) has the potential to become an Arches-like YMC" (Abstract); "The angular resolution is $\sim$0.13${}^{\prime\prime}$, which allows us to resolve scales of 1000 au, the scale of individual cores, at a distance of 8.1 kpc (cite: abuter19)." (Observations); "1 | 266.5949552 | -28.56055698 | 0.71 | 1.71 | 6.04 | 0.06 | 0.54" (Tables)

## Data provenance

- ALMA projects: 2016.1.00949.S
- bands: Band 6 (1.3 mm, ~230 GHz)  
  > "The observations were performed during ALMA’s Cycle 4 (project ID: 2016.1.00949.S, PI: D. Walker), at a frequency of $\sim$230GHz (1.3 mm, frequency band 6)." (Observations)
- frequencies and spectral setup: 7 spectral windows: 5 in LSB (217.105, 218.222, 218.476, 218.760 GHz with BW 0.234 GHz and ~0.78 km/s; 220.709 GHz with BW 0.934 GHz and 0.77 km/s) and 2 in USB (232.500 and 235.000 GHz with BW 1.875 GHz and ~2.5 km/s)  
  > "The observations contain 7 spectral windows, 5 of which targeted specific molecular transitions (Table [1](#tab:specparam)) in the lower sideband with a spectral resolution of $\sim$0.77 km s$^{-1}$." (Observations); "The remaining two spectral windows were dedicated to broad-band continuum detection in the upper sideband, with a spectral resolution of $\sim$2.5 km s$^{-1}$." (Observations)
- continuum bandwidth: ~5.6 GHz aggregate; ~5 GHz effective after flagging line contamination  
  > "The total aggregate bandwidth is approximately 5.6 GHz." (Observations); "We estimate that no more than 10% of the aggregate bandwidth is flagged due to line contamination, and the effective bandwidth used for continuum generation is $\sim$5 GHz." (Image Cleaning & Processing)
- arrays: 12m array (41-45 antennas)  
  > "Each execution used 41-45 antennas, with baselines ranging from 15 - 3696 m." (Observations); "For the spectral lines, we only have 12m data, and so we are missing the larger scale structure." (Image Cleaning & Processing)
- configurations: C40-6, C40-3  
  > "14/10/2016 | C40-6 | 41 | 18 - 2535 | 45.37 | J1924-2914 | J1924-2914 | J1744-3116" (Observations); "25/04/2017 | C40-3 | 41 | 15 - 450 | 27.22 | J1924-2914 | J1924-2914 | J1744-3116" (Observations)
- baselines: 15 - 3696 m  
  > "Each execution used 41-45 antennas, with baselines ranging from 15 - 3696 m." (Observations)
- angular resolution: ~0.13 arcsec (synthesised beam 0.14 arcsec x 0.11 arcsec, ~1100 au x 890 au)  
  > "The angular resolution is $\sim$0.13${}^{\prime\prime}$, which allows us to resolve scales of 1000 au, the scale of individual cores, at a distance of 8.1 kpc (cite: abuter19)." (Observations); "The resultant image has a synthesised beam size of $0.14{}^{\prime\prime}\times 0.11^{\prime\prime}$ ($\sim$1100 au $\times$ 890 au)." (Image Cleaning & Processing)
- max recoverable scale: _not stated_
- sensitivity: Continuum rms: ~15 microJy (~0.1 M_sun 5sigma mass sensitivity at 20 K); Line rms: ~0.6 mJy before smoothing, ~1 mJy after smoothing  
  > "After feathering, the rms continuum sensitivity is $\sim$15 $\mu$Jy, corresponding to a 5$\sigma$ mass sensitivity of $\sim$0.1 M$_{\odot}$, assuming a dust temperature of 20 K (see $\S$ [3.1](#sub:cont_source_props))." (Image Cleaning & Processing); "This increased the rms of the line images from $\sim$0.6 mJy to $\sim$1 mJy." (Image Cleaning & Processing)
- time on source: 45.37 min, 27.22 min, 45.37 min, 45.37 min across 4 execution blocks  
  > "14/10/2016 | C40-6 | 41 | 18 - 2535 | 45.37 | J1924-2914 | J1924-2914 | J1744-3116" (Observations); "25/04/2017 | C40-3 | 41 | 15 - 450 | 27.22 | J1924-2914 | J1924-2914 | J1744-3116" (Observations)
- observing dates: 14/10/2016, 25/04/2017, 19/07/2017, 08/08/2017  
  > "14/10/2016 | C40-6 | 41 | 18 - 2535 | 45.37 | J1924-2914 | J1924-2914 | J1744-3116" (Observations); "19/07/2017 | C40-6 | 42 | 18 - 3696 | 45.37 | J1924-2914 | J1733-1304 | J1744-3116" (Observations); "08/08/2017 | C40-6 | 45 | 21 - 3696 | 45.37 | J1924-2914 | J1733-1304 | J1744-3116" (Observations)
- pi or archival as stated: PI: D. Walker (Cycle 4 project ID: 2016.1.00949.S)  
  > "The observations were performed during ALMA’s Cycle 4 (project ID: 2016.1.00949.S, PI: D. Walker), at a frequency of $\sim$230GHz (1.3 mm, frequency band 6)." (Observations)
- Line: SiO (5-4) (217.105 GHz)
- Line: H2CO (3_{0,3} - 2_{0,2}) (218.222 GHz)
- Line: H2CO (3_{2,2} - 2_{2,1}) (218.476 GHz)
- Line: H2CO (3_{2,1} - 2_{2,0}) (218.760 GHz)
- Line: 13CO / CH3CN (2-1) / (12-11) (220.709 GHz)
- Other facility **Mopra / MALT90**: 40 arcsec resolution single-dish HNCO (4_{0,4} - 3_{0,3}) and SiO (2-1) molecular line data to investigate pc-scale gas kinematics  
  > "We present high-resolution (0.13$^{\prime\prime}$, $\sim$1000 au) ALMA observations and Mopra single-dish data" (Abstract); "We use MALT90 data (cite: foster11; foster13; jackson13), specifically the HNCO (4$_{0,4}$ - 3$_{0,3}$) and SiO (2-1) lines, to investigate the gas kinematics in cloud ‘d’ at a larger scale." (Gas flows at the cloud scale)
- Other facility **ALMA 12m+7m + BOLOCAM Galactic Plane Survey (BGPS)**: ~1 arcsec resolution combined 259 GHz continuum map used for feathering to recover large-scale continuum emission, plus BGPS contours  
  > "To recover the continuum emission, we use $\sim$1$^{\prime\prime}$ resolution data from (cite: barnes19), which combines observations from ALMA’s 12m array and 7m array with BOLOCAM Galactic Plane Survey (cite: ginsburg13) data." (Image Cleaning & Processing)
- External data: ~1 arcsec combined ALMA 12m+7m and BGPS continuum image at ~259 GHz used for feathering  
  > "To recover the continuum emission, we use $\sim$1$^{\prime\prime}$ resolution data from (cite: barnes19), which combines observations from ALMA’s 12m array and 7m array with BOLOCAM Galactic Plane Survey (cite: ginsburg13) data." (Image Cleaning & Processing) [from (cite: barnes19)]
- External data: Clump 'd6' effective radius (0.16 pc), upper and lower mass estimates (239 and 69 M_sun), line width (~5 km/s, velocity dispersion ~2.1 km/s), gas temperature upper limit (~60 K), and 15 SMA clumps for mass-radius and pressure equilibrium plots  
  > "Using the effective radius (0.16 pc) and upper and lower mass estimates (239 and 69 M${}_{\odot}$, respectively) of clump ‘d6’ from (cite: walker18), we estimate upper and lower thermal Jeans length limits" (Nearest neighbour analysis of compact continuum source separations); "They report a line width of $\sim$5 kms${}^{-1}$, which translates to a velocity dispersion of $\sim$2.1 kms${}^{-1}$." (Nearest neighbour analysis of compact continuum source separations) [from (cite: walker18)]
- External data: Cloud 'd' mass (7.6 x 10^4 M_sun), radius (3.2 pc), and line widths (~16 km/s)  
  > "From (cite: walker15), cloud ‘d’ has a radius of 3.2 pc and line widths of $\sim$ 16 kms${}^{-1}$, and so we estimate that all mass will converge across the entirety of cloud ‘d’ in around 3 $\times$ 10$^{5}$ years." (Gas flows at the cloud scale); "Once again considering the whole cloud, using the mass of 7.6 $\times$ 10${}^4$ M${}_{\odot}$ from (cite: walker15), we estimate a mass inflow rate across the entire cloud of around 0.25 M${}_{\odot}$yr${}^{-1}$." (Gas flows at the cloud scale) [from (cite: walker15)]
- External data: Cores in the CMZ and Galactic disc for the mass-radius comparison plot  
  > "Also plotted are (cite: walker18)’s 15 SMA clumps and the cloud ‘a’ core (aka the ‘maser core’ in the ‘Brick’) mass and radius from (cite: rathborne14)." (Do the properties of sources vary with environment?); "The plot also includes a sample of high-mass protostellar cores found in the Galactic disc, taken from (cite: peretto13), as well as high-mass protostellar cores in the W43-MM1 ridge, a likely precursor to a ‘starburst cluster’, taken from (cite: louvet14)." (Do the properties of sources vary with environment?); "We have also plotted masses and radii for multiple CMZ cores from (cite: lu20) and the masses and radii of eighteen cores in cloud ‘a’ (cite: walker21)." (Do the properties of sources vary with environment?) [from (cite: rathborne14), (cite: peretto13), (cite: louvet14), (cite: lu20), (cite: walker21)]
- External data: Galactic Ring Survey (GRS) disc cloud data for the pressure-bounded virial equilibrium comparison  
  > "Figure [8](#fig:h2copress) shows a replica of Figure 3 in (cite: field11), along with the SMA dust ridge cloud data in (cite: walker18)." (Are the sources in hydrostatic equilibrium?) [from (cite: field11), (cite: heyer09), (cite: jackson06)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "The ALMA pipeline calibrated data sets for each execution block were combined to obtain final data products, which were then imaged in CASA Version 5.6.0.68 (cite: mcmullin07)." (Image Cleaning & Processing)
- casa version: CASA Version 5.6.0.68 (used for imaging)  
  > "The ALMA pipeline calibrated data sets for each execution block were combined to obtain final data products, which were then imaged in CASA Version 5.6.0.68 (cite: mcmullin07)." (Image Cleaning & Processing)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1924-2914, J1733-1304  
  > "14/10/2016 | C40-6 | 41 | 18 - 2535 | 45.37 | J1924-2914 | J1924-2914 | J1744-3116" (Observations); "19/07/2017 | C40-6 | 42 | 18 - 3696 | 45.37 | J1924-2914 | J1733-1304 | J1744-3116" (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "We use CASA’s `tclean` task to image both the continuum and line cubes." (Image Cleaning & Processing)
- deconvolver: _not stated_
- weighting robust: Briggs weighting, robust = 0.5  
  > "A cleaning threshold of 15 $\mu$Jy (the rms sensitivity of the continuum image) was used, with Briggs weighting and a `robust` parameter of 0.5." (Image Cleaning & Processing); "We again use Briggs weighting and a `robust` parameter of 0.5, although here we use a cleaning threshold of 0.06 mJy." (Image Cleaning & Processing)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Continuum: automasking over 10^5 iterations (threshold 15 microJy); Lines: interactive manual clean (threshold 0.06 mJy)  
  > "Due to the complex structure of cloud ‘d’, we opt for `tclean`’s ‘automasking’ mode over 10${}^5$ iterations." (Image Cleaning & Processing); "We use the interactive manual clean so we can stop defining masks when all the emission had been cleaned and the residuals look like noise with no remaining structure." (Image Cleaning & Processing)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub on split target spectral windows  
  > "We subtract the continuum from the isolated lines using the `uvcontsub` task." (Image Cleaning & Processing)
- line free channels: Channels with spectral line contamination flagged prior to continuum generation (<=10% of aggregate bandwidth flagged; no line emission in USB windows)  
  > "Prior to generating the dust continuum, any channels with spectral line contamination were flagged." (Image Cleaning & Processing); "We estimate that no more than 10% of the aggregate bandwidth is flagged due to line contamination, and the effective bandwidth used for continuum generation is $\sim$5 GHz." (Image Cleaning & Processing)
- primary beam correction: _not stated_
- array combination: Continuum feathered with Barnes et al. (2019) ALMA 12m+7m+BGPS data using CASA feather task after scaling flux by ~0.6 (using alpha_nu = 3.75 from 259 GHz to 225 GHz)  
  > "Using $\alpha_{\nu} = 3.75$, as (cite: barnes19) did, we get:" (Image Cleaning & Processing); "We use the `feather` task in CASA when combining the (cite: barnes19) data with the cleaned ALMA data." (Image Cleaning & Processing)
- smoothing: Spatial Gaussian smoothing on molecular line cubes using CASA imsmooth with kernel major and minor axes = ~0.34 arcsec  
  > "We use CASA’s `imsmooth` task to perform a spatial Gaussian smoothing on the molecular line data to improve the signal to noise." (Image Cleaning & Processing); "We set the major and minor axes parameters of the Gaussian smoothing kernel to equal $\sim$0.34${}^{\prime\prime}$, double the size of the major axis of the synthesised beam." (Image Cleaning & Processing)
- final beam: 0.14 arcsec x 0.11 arcsec (~1100 au x 890 au) for continuum  
  > "The resultant image has a synthesised beam size of $0.14{}^{\prime\prime}\times 0.11^{\prime\prime}$ ($\sim$1100 au $\times$ 890 au)." (Image Cleaning & Processing)
- final rms: Continuum: ~15 microJy; Line images: ~0.6 mJy (unsmoothed), ~1 mJy (after Gaussian smoothing)  
  > "After feathering, the rms continuum sensitivity is $\sim$15 $\mu$Jy, corresponding to a 5$\sigma$ mass sensitivity of $\sim$0.1 M$_{\odot}$, assuming a dust temperature of 20 K (see $\S$ [3.1](#sub:cont_source_props))." (Image Cleaning & Processing); "This increased the rms of the line images from $\sim$0.6 mJy to $\sim$1 mJy." (Image Cleaning & Processing)

### Inherited from earlier work

- Observational and spectral setup  
  > "In this study, we present high angular resolution (0.13${}^{\prime\prime}$) ($\sim$1000 au) ALMA Band 6 observations towards the peak of the single-dish continuum emission in cloud ‘d’ (cite: walker18) using the same observational and spectral setup as (cite: walker21)" (Introduction) [from (cite: walker21)]
- Flux scaling relation and spectral index alpha_nu = 3.75 for combining continuum images at different frequencies  
  > "Using $\alpha_{\nu} = 3.75$, as (cite: barnes19) did, we get:" (Image Cleaning & Processing) [from (cite: barnes19)]
- Dust mass and opacity equations and parameters (kappa_0 = 0.04 cm^2 g^-1 at 505 GHz, gas-to-dust ratio = 100, beta = 1.75, T = 20 K)  
  > "By extracting the fluxes of each leaf we calculate the mass of each source using the relation:" (Spatial distribution, mass, radius and density of compact continuum sources); "The numbers used in this relation come from (cite: ossenkopf94)." (Spatial distribution, mass, radius and density of compact continuum sources); "Additionally, we have assumed a spectral index, $\beta$, of 1.75 (cite: battersby11)." (Spatial distribution, mass, radius and density of compact continuum sources) [from (cite: kauffmann08), (cite: ossenkopf94), (cite: battersby11), (cite: tang20)]
- Pressure-bounded virial equilibrium analysis framework  
  > "We follow the analysis of both (cite: field11) and (cite: walker18) to investigate this possibility in cloud ‘d’." (Are the sources in hydrostatic equilibrium?) [from (cite: field11), (cite: walker18)]

### Not stated but needed to reproduce (our reading)

- Exact pixel cell size and image dimensions (imsize) used in CASA tclean (though N_pix = 77 per beam implies cell size ~ 0.015 arcsec)
- Exact channel ranges flagged for line contamination prior to continuum imaging and used for uvcontsub continuum fitting
- Deconvolver algorithm in tclean (e.g., hogbom, clark, multiscale, mtmfs)
- Primary beam correction settings (pbcor) during imaging and feathering
- Exact coordinates and position angles of the slices used for CASA impv position-velocity diagrams

## Analysis recipe

1. **Image and feather the 1.3 mm dust continuum and image molecular line cubes**: Flag line-contaminated channels, image continuum with tclean (automasking), scale Barnes et al. (2019) 259 GHz ALMA+BGPS continuum by 0.6 and combine using CASA feather. Split line windows, subtract continuum with uvcontsub, image with tclean (manual masking), create moment maps with immoments, and smooth spatially with imsmooth.  
  > "We use CASA’s `tclean` task to image both the continuum and line cubes." (Image Cleaning & Processing); "We use the `feather` task in CASA when combining the (cite: barnes19) data with the cleaned ALMA data." (Image Cleaning & Processing); "We use CASA’s `imsmooth` task to perform a spatial Gaussian smoothing on the molecular line data to improve the signal to noise." (Image Cleaning & Processing)
   - software: CASA, tclean, feather, split, uvcontsub, immoments, imsmooth
   - parameter: robust = 0.5, continuum threshold = 15 microJy, 10^5 iterations; line threshold = 0.06 mJy; Gaussian smoothing kernel = 0.34 arcsec  
  > "A cleaning threshold of 15 $\mu$Jy (the rms sensitivity of the continuum image) was used, with Briggs weighting and a `robust` parameter of 0.5." (Image Cleaning & Processing); "We again use Briggs weighting and a `robust` parameter of 0.5, although here we use a cleaning threshold of 0.06 mJy." (Image Cleaning & Processing); "We set the major and minor axes parameters of the Gaussian smoothing kernel to equal $\sim$0.34${}^{\prime\prime}$, double the size of the major axis of the synthesised beam." (Image Cleaning & Processing)
   - assumption: Spectral index alpha_nu = 3.75 between 225 GHz and 259 GHz resulting in a flux scaling factor of ~0.6  
  > "Using $\alpha_{\nu} = 3.75$, as (cite: barnes19) did, we get:" (Image Cleaning & Processing)
   - fitting: _not stated_
   - validation: Compared total flux before (0.0247 Jy) and after (1.077 Jy) feathering and checked that footprint loss did not affect the main area of dust emission.  
  > "The total flux of the image before feathering is 0.0247 Jy, whereas after feathering it is 1.077 Jy." (Image Cleaning & Processing); "We do not, however, lose any of the main area of dust emission, and so continue with this feathered image." (Image Cleaning & Processing)
2. **Extract compact continuum sources and derive masses, radii, and densities**: Compute dendrogram on feathered continuum map using astrodendro to identify leaves, extract integrated flux, and compute masses, effective radii, and spherical volume densities (both with and without background subtraction).  
  > "We use the astrodendro software package to produce these dendrograms, setting a threshold of 3$\sigma$ and an increment of at least $\sigma$ between structures, where $\sigma$ is the rms sensitivity of 15 $\mu$Jy." (Spatial distribution, mass, radius and density of compact continuum sources); "Using the calculated masses and effective radii, we then compute the volume densities of the sources, assuming a spherical geometry." (Spatial distribution, mass, radius and density of compact continuum sources)
   - software: astrodendro
   - parameter: min_value (threshold) = 3 sigma (and 5 sigma for comparison), min_delta (increment) = 1 sigma (sigma = 15 microJy), min_npix = 77  
  > "We use the astrodendro software package to produce these dendrograms, setting a threshold of 3$\sigma$ and an increment of at least $\sigma$ between structures, where $\sigma$ is the rms sensitivity of 15 $\mu$Jy." (Spatial distribution, mass, radius and density of compact continuum sources); "For this dendrogram we used an $N_{\rm pix}$ value of 77, which corresponds to the size of approximately one synthesised beam." (Spatial distribution, mass, radius and density of compact continuum sources)
   - assumption: Distance d = 8.1 kpc, dust temperature T = 20 K, spectral index beta = 1.75, dust opacity kappa_nu = 0.04 cm^2 g^-1 * (225 GHz / 505 GHz)^1.75, gas-to-dust ratio = 100, spherical geometry  
  > "The angular resolution is $\sim$0.13${}^{\prime\prime}$, which allows us to resolve scales of 1000 au, the scale of individual cores, at a distance of 8.1 kpc (cite: abuter19)." (Observations); "where $\nu$ is the frequency and the gas-to-dust ratio is assumed to be 100, which may not be the case in the CMZ (cite: longmore13; giannetti17)." (Spatial distribution, mass, radius and density of compact continuum sources); "Therefore, our mass and density estimates, using a $\beta$ value of 1.75 and dust temperature of 20 K, may be underestimates." (Spatial distribution, mass, radius and density of compact continuum sources)
   - fitting: _not stated_
   - validation: Repeated dendrogram extraction with 5 sigma threshold (detecting 9 sources instead of 96), computed background-subtracted properties using the minimum pixel value in each leaf, and evaluated sensitivity to beta = 2.4 and T = 17 K.  
  > "We have varied the parameters of the dendrogram to see how this affects our results, namely by increasing the threshold to 5$\sigma$." (Spatial distribution, mass, radius and density of compact continuum sources); "To do this we use the minimum pixel value in each leaf as a proxy for the background emission (cite: pineda15; henshaw16b)." (Spatial distribution, mass, radius and density of compact continuum sources)
3. **Search for star formation tracers and outflows towards continuum sources**: Inspect 13CO (2-1), CH3CN (12-11), and SiO (5-4) cubes and integrated intensity maps towards the continuum sources, manually inspecting every channel in the SiO cube for outflow morphology.  
  > "We searched for $^{13}$CO, CH$_3$CN and SiO emission towards the cloud ‘d’ continuum sources." (Search for star formation tracers within cloud ‘d’ continuum sources); "We searched for SiO outflows by manually inspecting every channel in the SiO cube and although we detect SiO emission, no distinct outflow morphology can be seen." (Search for star formation tracers within cloud ‘d’ continuum sources)
   - fitting: _not stated_
   - validation: Compared against external maser, infrared (8, 24, 70 micron), and radio continuum surveys, as well as detections in the 'Brick' using an identical ALMA setup.  
  > "(cite: walker21) detected both strong CH$_3$CN emission and SiO outflows toward the young, low-mass star-forming cores in the ‘Brick’." (Search for star formation tracers within cloud ‘d’ continuum sources)
4. **Measure nearest neighbour separations and compare with Jeans fragmentation scales**: Compute 2D nearest neighbour distances using scikit-learn neighbors, convert to 3D deprojected mean separation lengths by multiplying by ~2.8 (2.3 for PDF expectation value * sqrt(3/2) for 3D deprojection), and compare to thermal and turbulent Jeans lengths and masses of clump 'd6'.  
  > "In order to calculate the separations of the compact continuum sources within cloud ‘d’ and compare them to theoretically predicted values, we carry out nearest neighbour analysis using the `scikit-learn` module `neighbors`." (Nearest neighbour analysis of compact continuum source separations); "Combined with the earlier factor of 2.3, this means we must multiply our mean nearest neighbour separation by a factor of $\sim$2.8." (Nearest neighbour analysis of compact continuum source separations)
   - software: scikit-learn
   - parameter: n_neighbors = 2, algorithm = 'auto'  
  > "We use a `n_neighbors` parameter of 2 and set the `algorithm` parameter to `auto`." (Nearest neighbour analysis of compact continuum source separations)
   - assumption: Clump 'd6' effective radius = 0.16 pc, mass = 69-239 M_sun, velocity dispersion = 2.1 km/s, gas temperature = 20-40 K  
  > "Using the effective radius (0.16 pc) and upper and lower mass estimates (239 and 69 M${}_{\odot}$, respectively) of clump ‘d6’ from (cite: walker18), we estimate upper and lower thermal Jeans length limits" (Nearest neighbour analysis of compact continuum source separations); "Based on this, we use upper and lower limits of 20 K and 40 K." (Nearest neighbour analysis of compact continuum source separations)
   - fitting: _not stated_
   - validation: Repeated comparison for the 9 sources above 5 sigma and tested half-wavelength Jeans fragmentation values.  
  > "Repeating this analysis but using a value of half the thermal Jeans and turbulent Jeans fragmentation wavelengths (to represent the fact that fragments may form at half-wavelength-spaced nodes), the distribution marginally favours the turbulent fragmentation length." (Nearest neighbour analysis of compact continuum source separations)
5. **Perform virial and pressure-bounded hydrostatic equilibrium analysis of sources**: Extract leaf-averaged spectra in SiO and three H2CO transitions, fit Gaussian profiles using pyspeckit to measure velocity dispersions from H2CO (3_{0,3}-2_{0,2}), compute virial parameters alpha = 5 R sigma^2 / (G M), aspect ratios, and required confining pressures P_e.  
  > "We then use the `pyspeckit` Python package to fit each these spectra with a Gaussian profile in order to obtain velocity dispersions." (Virial analysis of cloud ‘d’ continuum sources); "We find that only 13 of the continuum sources have clearly detected spectra, and we calculate the virial parameters of them using the equation:" (Virial analysis of cloud ‘d’ continuum sources); "Each of the curved black lines represent pressure-bounded virial equilibrium for several different external pressures." (Are the sources in hydrostatic equilibrium?)
   - software: pyspeckit
   - parameter: guesses = [max amplitude, velocity at max amplitude, FWHM]; Gamma = 0.73 for pressure-bounded virial equation  
  > "We set the `guesses` parameter as: the amplitude is equal to the maximum amplitude within the spectrum, the velocity is equal to the velocity at the point of highest amplitude, and the width is equal to full width half maximum of the line." (Virial analysis of cloud ‘d’ continuum sources); "We assume $\Gamma$ = 0.73, corresponding to a centrally concentrated density structure." (Are the sources in hydrostatic equilibrium?)
   - assumption: H2CO (3_{0,3}-2_{0,2}) traces the compact source kinematics; centrally concentrated density structure (Gamma = 0.73)  
  > "We note that only H${}_2$CO effectively traces the mass (see supplementary online material), and so we only use the lowest energy formaldehyde transition in later analysis." (Virial analysis of cloud ‘d’ continuum sources); "We assume $\Gamma$ = 0.73, corresponding to a centrally concentrated density structure." (Are the sources in hydrostatic equilibrium?)
   - fitting: Gaussian profile fitting via pyspeckit  
  > "We then use the `pyspeckit` Python package to fit each these spectra with a Gaussian profile in order to obtain velocity dispersions." (Virial analysis of cloud ‘d’ continuum sources)
   - validation: Checked correlation between virial parameter and source aspect ratio (major/minor axis) and tested on the 5 sigma subsample.  
  > "We also plot the virial parameter against the aspect ratio (Figure [5](#fig:asprat)) to see if continuum sources with a lower virial parameter correspond to a smaller aspect ratio." (Virial analysis of cloud ‘d’ continuum sources)
6. **Analyze large-scale and small-scale gas kinematics and estimate inflow rates**: Construct integrated intensity channel maps (0-30 km/s in 5 km/s bins) of MALT90 HNCO (4_{0,4}-3_{0,3}) and SiO (2-1) and ALMA H2CO (3_{0,3}-2_{0,2}) and SiO (5-4) (5-30 km/s), generate PV diagrams of MALT90 HNCO using CASA impv, and calculate convergence timescales t = d/v and mass inflow rates m_dot = m/t.  
  > "To make these plots, we map integrated intensity in spacings of 5 kms${}^{-1}$ in the range $0 - 30$ kms${}^{-1}$." (Gas flows at the cloud scale); "The diagrams were computed using the `impv` task within `CASA`." (Gas flows at the cloud scale); "If this interpretation is correct, we estimate the time, $t$, it will take for all of the mass to end up at the convergence point through $t = d/v$, where $v$ is the velocity of the gas and $d$ is the distance the gas will travel." (Gas flows at the cloud scale)
   - software: CASA, impv
   - parameter: Channel map bins = 5 km/s; impv slice widths = 5 pixels (left flow) and 1 pixel (right flow)  
  > "To make these plots, we map integrated intensity in spacings of 5 kms${}^{-1}$ in the range $0 - 30$ kms${}^{-1}$." (Gas flows at the cloud scale); "The left-hand diagram was computed with a width of 5 pixels and the right-hand diagram was computed with a width of 1 pixel." (Gas flows at the cloud scale)
   - assumption: Velocity along the line of sight is comparable to velocity in the plane of the sky; material sits in the same plane of the sky  
  > "The following interpretation of the three-dimensional motion assumes that the velocity along the line of sight is comparable to the velocity in the plane of the sky." (Gas flows at the cloud scale); "These estimates are all under the assumption that the material is all sitting in the same plane of the sky." (Gas flows at the cloud scale)
   - fitting: _not stated_
   - validation: Verified that the spatial offset between ALMA SiO and H2CO/dust continuum is ~7 beam widths and not an observational artefact.  
  > "This spatial offset is consistently equivalent to $\sim$7 beam widths, so must be real and not an observational artefact." (Gas flows at the cloud scale)

## Software

- **CASA** 5.6.0.68: Combining calibrated executions, imaging continuum and spectral lines (tclean), feathering (feather), splitting (split), continuum subtraction (uvcontsub), moment maps (immoments), Gaussian smoothing (imsmooth), and PV diagrams (impv)  
  > "The ALMA pipeline calibrated data sets for each execution block were combined to obtain final data products, which were then imaged in CASA Version 5.6.0.68 (cite: mcmullin07)." (Image Cleaning & Processing); "We use the `feather` task in CASA when combining the (cite: barnes19) data with the cleaned ALMA data." (Image Cleaning & Processing); "The diagrams were computed using the `impv` task within `CASA`." (Gas flows at the cloud scale)
- **astrodendro** : Computing dendrograms on the feathered continuum image to extract compact continuum sources (leaves)  
  > "We use the astrodendro software package to produce these dendrograms, setting a threshold of 3$\sigma$ and an increment of at least $\sigma$ between structures, where $\sigma$ is the rms sensitivity of 15 $\mu$Jy." (Spatial distribution, mass, radius and density of compact continuum sources)
- **scikit-learn** : Nearest neighbour analysis of compact continuum source separations using the neighbors module  
  > "In order to calculate the separations of the compact continuum sources within cloud ‘d’ and compare them to theoretically predicted values, we carry out nearest neighbour analysis using the `scikit-learn` module `neighbors`." (Nearest neighbour analysis of compact continuum source separations)
- **pyspeckit** : Fitting Gaussian profiles to leaf-averaged molecular line spectra to obtain velocity dispersions  
  > "We then use the `pyspeckit` Python package to fit each these spectra with a Gaussian profile in order to obtain velocity dispersions." (Virial analysis of cloud ‘d’ continuum sources)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total continuum flux before feathering | 0.0247 | not stated | Jy | 1 | The total flux of the image before feathering is 0.0247 Jy, whereas after feathering it is 1.077 Jy. |
| Total continuum flux after feathering | 1.077 | not stated | Jy | 1 | The total flux of the image before feathering is 0.0247 Jy, whereas after feathering it is 1.077 Jy. |
| Number of compact continuum sources (3 sigma threshold) | 96 | not stated | dimensionless | 2 | Using these dendrogram parameters, we isolate 96 compact continuum sources. |
| Number of compact continuum sources (5 sigma threshold) | 9 | not stated | dimensionless | 2 | In this case, we detect nine sources as opposed to 96. |
| Mass range of 3 sigma continuum sources | 0.21 - 3.1 | factor of ~2 systematic | M_sun | 2 | These range in mass from $0.21 - 3.1$ M$_{\odot}$, have radii of $\sim$10$^3$ au and densities of 10$^{6-7}$ cm$^{-3}$.; The uncertainties in the dust temperature and opacity mean that systematic uncertainties in the mass estimates are a factor of $\sim$2 (cite: kauffmann08). |
| Mean mass of 3 sigma continuum sources | 0.67 | not stated | M_sun | 2 | The mean mass, radius and number density of the 96 compact continuum sources are 0.67 M${}_{\odot}$, $\sim$1.6 $\times$ 10${}^3$ au and 7.1 $\times$ 10${}^6$ cm${}^{-3}$ respectively, all computed from within the footprint of the dendrogram leaf. |
| Mean effective radius of 3 sigma continuum sources | 1.6e3 | not stated | au | 2 | The mean mass, radius and number density of the 96 compact continuum sources are 0.67 M${}_{\odot}$, $\sim$1.6 $\times$ 10${}^3$ au and 7.1 $\times$ 10${}^6$ cm${}^{-3}$ respectively, all computed from within the footprint of the dendrogram leaf. |
| Mean number density of 3 sigma continuum sources | 7.1e6 | not stated | cm^-3 | 2 | The mean mass, radius and number density of the 96 compact continuum sources are 0.67 M${}_{\odot}$, $\sim$1.6 $\times$ 10${}^3$ au and 7.1 $\times$ 10${}^6$ cm${}^{-3}$ respectively, all computed from within the footprint of the dendrogram leaf. |
| Total combined mass of 96 continuum sources (3 sigma) | 65 | not stated | M_sun | 2 | The total combined mass of the sources is 65 M${}_{\odot}$. |
| Mean mass of 5 sigma continuum sources | 0.94 | not stated | M_sun | 2 | Repeating this analysis for the nine sources detected above 5$\sigma$ gives a mean mass, radius and number density of 0.94 M${}_{\odot}$, $\sim$1.6 $\times$ 10${}^3$ au and 9.7 $\times$ 10${}^6$ cm${}^{-3}$ respectively, with a total combined mass of 8.4 M${}_{\odot}$. |
| Total combined mass of 9 continuum sources (5 sigma) | 8.4 | not stated | M_sun | 2 | Repeating this analysis for the nine sources detected above 5$\sigma$ gives a mean mass, radius and number density of 0.94 M${}_{\odot}$, $\sim$1.6 $\times$ 10${}^3$ au and 9.7 $\times$ 10${}^6$ cm${}^{-3}$ respectively, with a total combined mass of 8.4 M${}_{\odot}$. |
| Mean 2D nearest neighbour separation | 2.6e3 | not stated | au | 4 | Most continuum sources have a nearest neighbour separation of less than $\sim$7.5 $\times$ 10${}^3$ au, with a mean of $\sim$2.6 $\times$ 10${}^3$ au. |
| Mean 3D deprojected separation length (3 sigma sources) | 1.5e4 | not stated | au | 4 | Converting each nearest neighbour separation to a separation length gives a mean separation length of $\sim$1.5 $\times$ 10${}^4$ au. |
| Mean 3D deprojected separation length (5 sigma sources) | 1.3e4 | not stated | au | 4 | The mean separation, however, still lies between the two predictions, with a mean value of 1.3 $\times$ 10${}^4$ au. |
| Thermal Jeans length of clump d6 | 8.0e3 | +4.2e3/-3.4e3 | au | 4 | Using both of these gas temperature estimates, as well as both estimates of mass, we derive thermal Jeans length estimates of $\lambda_\mathrm{J,therm}$ = 8.0${}^{+4.2}_{-3.4}$ $\times$ 10${}^{3}$ au. |
| Turbulent Jeans length of clump d6 | 5.3e4 | +1.6e4/-1.6e4 | au | 4 | The expected value of the turbulent Jeans fragmentation length is $\lambda_\mathrm{J,turb}$ = 5.3${}^{+1.6}_{-1.6}$ $\times$ 10${}^{4}$ au. |
| Thermal Jeans mass of clump d6 | 0.54 | +0.70/-0.35 | M_sun | 4 | The estimated thermal Jeans mass is $M_\mathrm{J,therm}$ = 0.54${}^{+0.70}_{-0.35}$ $M_{\odot}$. |
| Turbulent Jeans mass of clump d6 | 144 | +43/-43 | M_sun | 4 | The estimated turbulent Jeans mass is $M_\mathrm{J,turb}$ = 144${}^{+43}_{-43}$ $M_{\odot}$. |
| Virial parameter (alpha) range for 13 sources with H2CO detections | 5 - 45 | +13/-4.94 to +55/-33 | dimensionless | 5 | For continuum sources where we could measure reliable velocity dispersions, we calculate $\alpha$ values in the range 5${}^{+13}_{-4.94}$ - 45${}^{+55}_{-33}$ (see Table [\[tab:virial\]](#tab:virial) in the appendix for a full list of these calculated values). |
| Source aspect ratio range (mean) | 1 - 4.5 (mean 1.92) | not stated | dimensionless | 5 | We find ratios in the range of 1 - 4.5, with a mean value of $\sim$1.92. |
| External pressure required for pressure-bounded equilibrium of sources | 1e9 | not stated | K cm^-3 | 5 | From Fig. [8](#fig:h2copress) we can see that the pressures required to confine sources on the scale of these sources are $\sim$10${}^9$ K cm${}^{-3}$. |
| Mass convergence timescale across clump d6 | 1e5 | not stated | yr | 6 | In this way, we estimate that it will take $\sim$10$^5$ years for all the mass to reach the convergent point across clump ‘d6’. |
| Mass convergence timescale across entire cloud d | 3e5 | not stated | yr | 6 | From (cite: walker15), cloud ‘d’ has a radius of 3.2 pc and line widths of $\sim$ 16 kms${}^{-1}$, and so we estimate that all mass will converge across the entirety of cloud ‘d’ in around 3 $\times$ 10$^{5}$ years. |
| Mass inflow rate across clump d6 | 1e-3 | not stated | M_sun yr^-1 | 6 | Using the upper mass limit of clump ‘d6’ of 239 M${}_{\odot}$ from (cite: walker18), we estimate a mass inflow rate towards the convergent point of the clump of 10$^{-3}$ M${}_{\odot}$yr${}^{-1}$. |
| Mass inflow rate across entire cloud d | 0.25 | not stated | M_sun yr^-1 | 6 | Once again considering the whole cloud, using the mass of 7.6 $\times$ 10${}^4$ M${}_{\odot}$ from (cite: walker15), we estimate a mass inflow rate across the entire cloud of around 0.25 M${}_{\odot}$yr${}^{-1}$. |

## Qualitative findings

- Cloud 'd' contains very low column density contrast on 1000 au scales, with most continuum substructures only 3-5 sigma above the noise and no high-mass starless cores.  
  > "We expect this cloud to form many high-mass stars, but find no high-mass starless cores." (Abstract); "However, it leads to one of the main conclusions of this paper, that the column density contrast in the cloud is very small." (Spatial distribution, mass, radius and density of compact continuum sources)
- Cloud 'd' shows no evidence of active star formation on ~1000 au scales (no CH3CN hot core emission and no SiO or 13CO bipolar outflows), making it the youngest known pre-star-forming YMC progenitor cloud.  
  > "This would mean it is the youngest known pre-star forming massive cluster and therefore could be an ideal laboratory for studying the initial conditions of YMC formation." (Abstract); "However, we do not detect any CH$_3$CN emission towards the continuum sources, nor do we detect any SiO outflows." (Search for star formation tracers within cloud ‘d’ continuum sources)
- The mass distribution of the compact continuum sources is bottom-heavy (<~3 M_sun, mean ~0.67 M_sun), implying that sources must accrete significant mass from their surroundings to populate a normal IMF.  
  > "If these sources are the precursors to stars, in order for the resulting stellar distribution to conform to a normal IMF, the compact continuum sources must gain many times their current gas mass from the surrounding environment." (Discussion)
- Large-scale (~1 pc) converging gas flows in MALT90 HNCO and SiO data intersect at the ALMA continuum peak at V_LSR ~ 15-25 km/s, accompanied by an ALMA SiO (5-4) shock front wrapping around the dust continuum.  
  > "A natural interpretation of the HNCO and SiO kinematic structure in the Mopra data towards cloud ‘d’ is therefore that it is showing convergence of pc-scale gas flows at the continuum peak." (Gas flows at the cloud scale); "The fact that the SiO emission curves around the right-hand edge of the dust continuum emission provides strong evidence that there is a shock front at this location at V$_{\rm LSR} = 15 - 20$ kms$^{-1}$." (Gas flows at the cloud scale)

## Claim tuples

- H: Galactic Centre dust ridge cloud 'd' (clump 'd6') is a truly quiescent, pre-star-forming YMC progenitor cloud with no ongoing star formation at 1000 au core scales. | E: Observed clump 'd6' at 0.13 arcsec (~1000 au) resolution with ALMA Band 6 in 1.3 mm dust continuum and molecular line tracers (SiO 5-4, 13CO 2-1, CH3CN 12-11, H2CO) using the same setup that detected star formation in the 'Brick'. | R: Identified 96 low-mass continuum sources (<= 3.1 M_sun), with zero detections of CH3CN hot core emission and no SiO or 13CO outflow structures. | F: Cloud 'd' is not currently forming stars and is the earliest known pre-star-forming massive cluster progenitor. | **supported**
- H: Substructure formation on ~1000 au scales in cloud 'd' is governed by thermal Jeans fragmentation rather than turbulent Jeans fragmentation. | E: Measured 3D-corrected nearest neighbour separation lengths and dust masses for the 96 continuum sources (and 9 sources above 5 sigma) and compared them to predicted thermal and turbulent Jeans lengths and masses. | R: Source masses (0.21-3.1 M_sun, mean 0.67 M_sun) match the thermal Jeans mass (0.54 +0.70/-0.35 M_sun) and not the turbulent Jeans mass (144 +/- 43 M_sun); mean separation (1.5 x 10^4 au) lies between thermal (8.0 x 10^3 au) and turbulent (5.3 x 10^4 au) Jeans lengths, with a slight tendency towards thermal. | F: Thermal Jeans fragmentation is a better descriptor of the source structure on core scales than turbulent fragmentation, though the separation distribution alone cannot unambiguously distinguish between the two. | **partially**
- H: The compact continuum sources in cloud 'd' are gravitationally bound starless cores or in pressure-bounded hydrostatic equilibrium. | E: Fitted Gaussian profiles to H2CO (3_{0,3}-2_{0,2}) spectra towards the continuum sources to calculate virial parameters (alpha) and compared surface densities and velocity dispersions against pressure-bounded virial equilibrium curves. | R: Only 13 sources have clear H2CO spectra, yielding alpha = 5 to 45 with large uncertainties; confining them via external pressure requires P_e/k ~ 10^9 K cm^-3, an order of magnitude higher than the cloud-scale ambient pressure (~10^8 K cm^-3). | F: The virial state is unconstrained due to large uncertainties, and the sources are likely unbound and either confined by an undetected small-scale pressure or over-pressured and transient. | **partially**
- H: The high-density gas in clump 'd6' is being assembled by the convergence of large-scale (~pc) gas flows. | E: Mapped channel-by-channel kinematics and PV diagrams of pc-scale MALT90 HNCO (4-3) and SiO (2-1) emission alongside 1000 au scale ALMA H2CO (3-2) and SiO (5-4) emission. | R: Large-scale HNCO and SiO streams converge at the ALMA dust continuum peak at V_LSR ~ 15-25 km/s, where ALMA H2CO rings intersect and ALMA SiO (5-4) traces a bow-like shock front offset by ~7 beam widths, implying mass inflow of 10^-3 M_sun/yr (clump) to 0.25 M_sun/yr (cloud) over ~10^5 yr. | F: Cloud 'd' is at the convergence point of large-scale supersonic gas flows that shock and compress the gas, rapidly funnelling mass to trigger imminent star formation. | **supported**

## Reasoning

- Why this data: Cloud 'd' is the least studied dust ridge cloud and showed no star formation on >=0.01 pc scales; observing its continuum peak with ALMA Band 6 at 0.13 arcsec (~1000 au) using the identical setup that revealed embedded star formation in the 'Brick' tests for core-scale star formation.  
  > "In this study, we present high angular resolution (0.13${}^{\prime\prime}$) ($\sim$1000 au) ALMA Band 6 observations towards the peak of the single-dish continuum emission in cloud ‘d’ (cite: walker18) using the same observational and spectral setup as (cite: walker21) who found embedded star formation on 1000 au scales in the ‘Brick’." (Introduction)
- Why this method: Used automasking in tclean due to complex continuum structure; feathered with ALMA 12m+7m+BGPS data to recover extended flux lost to incomplete uv-coverage; used astrodendro to systematically characterize hierarchical substructure.  
  > "Due to the complex structure of cloud ‘d’, we opt for `tclean`’s ‘automasking’ mode over 10${}^5$ iterations." (Image Cleaning & Processing); "The data suffer with an inherent limited flux recovery due to the incomplete *uv*-coverage of the interferometer. We account for this by combining our interferometric data with the most appropriate large-scale data." (Image Cleaning & Processing); "We produce a dendrogram (cite: rosolowsky08) in order to describe the substructure in a systematic way." (Spatial distribution, mass, radius and density of compact continuum sources)
- Alternative: Using a 5 sigma dendrogram detection threshold instead of 3 sigma (reduces source count from 96 to 9, tested in parallel and shown not to change main conclusions)  
  > "We repeat our analysis on just these nine sources detected over 5$\sigma$ and report our results for comparison, but for completeness we show the properties of all 96 3$\sigma$ sources." (Spatial distribution, mass, radius and density of compact continuum sources)
- Alternative: Background subtraction of dendrogram leaves using minimum pixel value (reduces masses/densities by ~9x, noted as a lower bound while non-background-subtracted values are used for main analysis)  
  > "In the rest of our analysis we use the non-background-subtracted masses and densities, but we acknowledge that these could be overestimates if any flux in the continuum sources does not belong to the source itself." (Spatial distribution, mass, radius and density of compact continuum sources)
- Alternative: Bar-driven inflow collision as the driver of the converging flows (rejected because cloud 'd' is not near any proposed CMZ entry point and collision is ongoing)  
  > "However, it is unlikely that the collision observed in cloud ‘d’ is is driven by bar inflow, as cloud ‘d’ is not located near any proposed entry point to the CMZ (cite: henshaw22b)." (Source of converging flows)
- How they decided it was enough: Stopped interactive manual clean for spectral lines when all emission was cleaned and residuals looked like noise with no remaining structure.  
  > "We use the interactive manual clean so we can stop defining masks when all the emission had been cleaned and the residuals look like noise with no remaining structure." (Image Cleaning & Processing)
- Limitation (authors): Different footprints between the new ALMA data and the Barnes et al. (2019) ALMA+BGPS data cause loss of the upper right corner of the feathered continuum map.  
  > "Note that a section of the feathered continuum map is missing on the upper right side due to the ALMA data and the ALMA+BGPS data having different footprints." (Spatial distribution, mass, radius and density of compact continuum sources)
- Limitation (authors): Spectral lines only have 12m array data and therefore miss larger-scale structure.  
  > "For the spectral lines, we only have 12m data, and so we are missing the larger scale structure." (Image Cleaning & Processing)
- Limitation (authors): Most continuum structures are only 3-5 sigma above the noise, making it uncertain whether individual dendrogram leaves are physically distinct objects.  
  > "This makes it difficult to determine whether an individual dendrogram leaf is a physically distinct object or not – the nature of these sources is uncertain." (Spatial distribution, mass, radius and density of compact continuum sources)
- Limitation (authors): Dust opacity, gas-to-dust ratio (assumed 100), dust temperature (20 K), and spectral index beta (1.75) are not constrained on core scales, introducing systematic mass uncertainties of a factor of ~2.  
  > "The uncertainties in the dust temperature and opacity mean that systematic uncertainties in the mass estimates are a factor of $\sim$2 (cite: kauffmann08)." (Spatial distribution, mass, radius and density of compact continuum sources)
- Limitation (authors): Only 13 of 96 sources have clearly detected H2CO spectra, with large velocity dispersion uncertainties and potential contamination from extended H2CO emission along the line of sight, leaving the virial state unconstrained.  
  > "For the majority of continuum sources, we could not measure an appropriate velocity dispersion, and the ones that we could measure have large measurement uncertainties." (Virial analysis of cloud ‘d’ continuum sources); "This analysis of the virial parameter faces a potential issue, in that H${}_2$CO emission is extended." (Virial analysis of cloud ‘d’ continuum sources)
- Limitation (authors): 3D gas motions along the line of sight are unknown; line-of-sight offsets could imply net rotation rather than pure convergence at a single point.  
  > "However, we do not know the 3D motions of the cloud. If they don’t converge on this point, there could be net rotations in the gas." (Gas flows at the cloud scale)
- Caveat (inferred, ours): Gaussian spatial smoothing of the line cubes in the image plane (using imsmooth) increases the noise per beam in Jy/smoothed-beam (from 0.6 to 1 mJy) and does not recover missing short-spacing flux for the extended H2CO and SiO lines.
- Caveat (inferred, ours): In the nearest neighbour analysis, the text states that the mean 2D nearest neighbour separation (~2.6 x 10^3 au) is multiplied by ~2.8 to obtain the 3D separation length, which mathematically yields ~7.3 x 10^3 au, whereas the text reports ~1.5 x 10^4 au.

## Reproducibility

- Data public (paper): Publicly available on Zenodo (https://doi.org/10.5281/zenodo.6546462)  
  > "The data products used to conduct the research presented in this paper are made publicly available at the following Zenodo repository: <https://doi.org/10.5281/zenodo.6546462>." (Acknowledgements)
- Products in archive: Processed data products deposited in Zenodo (https://doi.org/10.5281/zenodo.6546462) and analysis scripts on GitHub (https://github.com/b-a-williams/Cloud-d-ALMA)  
  > "The data products used to conduct the research presented in this paper are made publicly available at the following Zenodo repository: <https://doi.org/10.5281/zenodo.6546462>." (Acknowledgements); "Scripts used to conduct this research are also made available on GitHub at: <https://github.com/b-a-williams/Cloud-d-ALMA>." (Acknowledgements)
- Code: Analysis scripts publicly released on GitHub at https://github.com/b-a-williams/Cloud-d-ALMA  
  > "Scripts used to conduct this research are also made available on GitHub at: <https://github.com/b-a-williams/Cloud-d-ALMA>." (Acknowledgements)
- Missing: Exact manual clean masks used for the molecular line cubes
- Missing: Exact pixel scale (cell size) and image size used in CASA tclean (unless starting directly from the FITS products on Zenodo)
- Missing: Exact slice coordinates for the CASA impv position-velocity diagrams
- Data volume (inferred): ~50-150 GB for raw/calibrated ALMA Cycle 4 visibility data (4 execution blocks, 7 SPWs); ~1-5 GB for the imaged FITS cubes and continuum maps on Zenodo.
- Score (inferred): 9/5, Both the processed data products (Zenodo) and analysis scripts (GitHub) are publicly released, and all key software packages, equations, assumptions, and parameters for source extraction, Jeans analysis, and virial analysis are explicitly documented.
- Rediscovery candidate: yes, Raw ALMA data (2016.1.00949.S), feathered FITS products (Zenodo), and analysis scripts (GitHub) are all public, and the main results (96 3-sigma sources, 9 5-sigma sources, masses, radii, separations, and virial parameters) are concrete numeric targets.

## Links

- Method: (cite: rosolowsky08) (Dendrogram technique for characterizing hierarchical substructure)
- Method: (cite: kauffmann08) (Dust continuum mass calculation equation)
- Method: (cite: ossenkopf94) (Dust opacity law parameters)
- Method: (cite: kruijssen19b) (Conversion from nearest neighbour distance expectation value to mean separation length)
- Method: (cite: bertoldi92) (Virial parameter formulation)
- Method: (cite: field11) (Pressure-bounded virial equilibrium formulation)
- Companion: (cite: walker18) (SMA+BGPS study identifying clump 'd6' in cloud 'd' and providing clump-scale physical parameters)
- Companion: (cite: barnes19) (ALMA 12m+7m+BGPS study of dust ridge clouds providing the ~1 arcsec continuum map used for feathering)
- Companion: (cite: walker21) (Companion ALMA Cycle 4 study of the 'Brick' using the identical observational and spectral setup)
- Related: MALT90 (Millimetre Astronomy Legacy Team 90 GHz Survey)
- Related: BGPS (BOLOCAM Galactic Plane Survey)
- Related: GRS (Galactic Ring Survey)

## Checks

```json
{
 "quotes": 185,
 "quotes_ok": 185,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 5,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 25,
 "numeric_problems": 0,
 "fill": {
  "facts": 100,
  "stated": 84,
  "rate": 0.84
 },
 "evidence_ok": true
}
```
