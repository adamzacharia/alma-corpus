# The Rosetta Stone project: III. ALMA synthetic observations of fragmentation in high-mass star-forming clumps

`2025A&A...701A.219N` | Astronomy and Astrophysics 2025 | first author: Nucara, Alice | arXiv: 2507.11032 | DOI: 10.1051/0004-6361/202554775

Card schema 1.0 | model gemini-4-argon | depth full | type theory_or_simulation_compared_to_alma

## Science

- Fields: star_formation
- Question: How do the initial conditions of a high-mass clump (mass, turbulence, magnetic field) and its environment affect the fragmentation properties observed with ALMA at ~7000 AU scales?  
  > "The physical mechanisms that regulate the collapse of high-mass parsec-scale clumps and allow them to form clusters of new stars, including high-mass stars, represent a crucial aspect of star formation." (The Rosetta Stone project); "On each field, we performed source extraction and photometry using the Hyper software, as in the SQUALO project, to quantitatively characterize how the initial conditions of the clump and the environment affect the observed fragmentation properties." (The Rosetta Stone project)
- Target **HIGALBM24.0116+0.4897 (HG24)**: coordinates _not stated_; z/distance 5.2 kpc  
  > "In particular, we reproduce the observational strategy used to observe the target source HIGALBM24.0116+0.4897 (HG24), on which forthcoming studies from the SQUALO survey are focusing (Jones et al. in prep.)." (Setup: Simulations and radiative transfer); "The source is located at a heliocentric distance of 5.2 kpc ((cite: 2021A&A...646A..74M))." (Setup: Simulations and radiative transfer); distance from (cite: 2021A&A...646A..74M)  
  > "In particular, we reproduce the observational strategy used to observe the target source HIGALBM24.0116+0.4897 (HG24), on which forthcoming studies from the SQUALO survey are focusing (Jones et al. in prep.)." (Setup: Simulations and radiative transfer); "The source is located at a heliocentric distance of 5.2 kpc ((cite: 2021A&A...646A..74M))." (Setup: Simulations and radiative transfer)
- Target **SQUALO survey sample (13 high-mass star-forming regions)**: coordinates _not stated_; z/distance 2.0 to 5.5 kpc  
  > "The SQUALO sample consists of $13$ high-mass star-forming regions of the Galaxy at different evolutionary stages, and all have evidence of infall motions at the clump scales." (The Rosetta Stone project); "Col. 5: Source distances adopted in (cite: 2023MNRAS.520.2306T)." (The SQUALO sample); distance from (cite: 2023MNRAS.520.2306T)  
  > "The SQUALO sample consists of $13$ high-mass star-forming regions of the Galaxy at different evolutionary stages, and all have evidence of infall motions at the clump scales." (The Rosetta Stone project); "Col. 5: Source distances adopted in (cite: 2023MNRAS.520.2306T)." (The SQUALO sample)

## Data provenance

- ALMA projects: 2018.1.00443.S
- bands: Band 6 (1.3 mm)  
  > "iii. The radiative transfer - Our simulations are post-processed at Spitzer 24 $\mu$m, Herschel and ALMA Band 6 wavelengths by means of the RADMC-3D code by Tung et al. (hereafter Paper II)." (The Rosetta Stone project); "The frequency of the central channel: 231.1 GHz, that is the 1.3 mm wavelength used for the radiative transfer;" (Rosetta Stone (SQUALO) pipeline)
- frequencies and spectral setup: 231.1 GHz (1.3 mm continuum)  
  > "The frequency of the central channel: 231.1 GHz, that is the 1.3 mm wavelength used for the radiative transfer;" (Rosetta Stone (SQUALO) pipeline)
- continuum bandwidth: _not stated_
- arrays: 12 m array and 7 m array (ACA)  
  > "post-processed using the CASA software to mimic the observing strategy of SQUALO (combining ACA and 12 m array)." (The Rosetta Stone project); "Specifically, the archival data for the 2018.1.00443.S project (ALMA Cycle 6) include a single observing block on the 12 m array (C43-1 configuration), and five observing blocks on the 7 m array for the HG24 reference source." (Rosetta Stone (SQUALO) pipeline)
- configurations: C43-1 (47 antennas on 12 m array; 10 to 12 antennas on 7 m array)  
  > "Specifically, the archival data for the 2018.1.00443.S project (ALMA Cycle 6) include a single observing block on the 12 m array (C43-1 configuration), and five observing blocks on the 7 m array for the HG24 reference source." (Rosetta Stone (SQUALO) pipeline); "The fiducial antenna configurations, made up of $10$ to $12$ antennas for the execution blocks on the 7 m array, and $47$ antennas for the 12 m array;" (Rosetta Stone (SQUALO) pipeline)
- baselines: _not stated_
- angular resolution: ~1.4" (1.29" x 1.51" synthetic beam; ~7000 AU at 5.2 kpc)  
  > "At the SQUALO angular resolution of $\sim1.4^{\prime\prime}$, we are therefore able to probe the fragmentation process at $\sim7000$ AU scales." (Setup: Simulations and radiative transfer); "Cell size: 0.2$^{\prime\prime}$, to sample our 1.29$^{\prime\prime}\times$1.51$^{\prime\prime}$ synthetic beam with $\sim 7$ pixels." (Rosetta Stone (SQUALO) pipeline)
- max recoverable scale: _not stated_
- sensitivity: 0.02 to 15 mJy/beam (mean 2.9 mJy/beam for synthetic; 0.78 to 15.18 mJy/beam for SQUALO; 1.42 mJy/beam for HG24)  
  > "The estimated r.m.s. for the set of synthetic observations, calculated using the Hyper software directly on the cleaned (primary beam non-corrected) maps, ranges from $\sim0.02$ to $\sim15$ mJy/beam." (Noise consistency analysis); "The mean r.m.s. of 2.9 mJy/beam across the sample is consistent with the 1.42 mJy/beam r.m.s. of the HG24 reference source." (Noise consistency analysis)
- time on source: ~470 s per block (5 blocks) on 7 m array, ~360 s (1 block) on 12 m array  
  > "The time on source, with $\sim470$ s of integration for each block on the 7 m array, and $\sim360$ s for the 12 m array;" (Rosetta Stone (SQUALO) pipeline)
- observing dates: _not stated_
- pi or archival as stated: archival  
  > "Specifically, the archival data for the 2018.1.00443.S project (ALMA Cycle 6) include a single observing block on the 12 m array (C43-1 configuration), and five observing blocks on the 7 m array for the HG24 reference source." (Rosetta Stone (SQUALO) pipeline)
- External data: ALMA 1.3 mm continuum observations and fragment-scale properties of 13 high-mass star-forming regions from the SQUALO survey  
  > "i. The reference observations - Our first case study takes as reference ALMA 1.3 mm continuum dust emission observations from the Star formation in QUiescent And Luminous Objects (SQUALO) survey by (cite: 2023MNRAS.520.2306T)." (The Rosetta Stone project); "Specifically, the clump properties have been taken from the latest release of the Hi-GAL clump catalog ((cite: 2021MNRAS.504.2742E)) and fragment-scale properties have been taken from (cite: 2023MNRAS.520.2306T) or derived from the analysis therein." (The SQUALO sample) [from (cite: 2023MNRAS.520.2306T)]
- External data: Clump properties from the Hi-GAL clump catalog  
  > "Specifically, the clump properties have been taken from the latest release of the Hi-GAL clump catalog ((cite: 2021MNRAS.504.2742E)) and fragment-scale properties have been taken from (cite: 2023MNRAS.520.2306T) or derived from the analysis therein." (The SQUALO sample) [from (cite: 2021MNRAS.504.2742E)]
- External data: Heliocentric distance of 5.2 kpc for reference source HG24  
  > "The source is located at a heliocentric distance of 5.2 kpc ((cite: 2021A&A...646A..74M))." (Setup: Simulations and radiative transfer) [from (cite: 2021A&A...646A..74M)]
- External data: L/M ranges for clump reference temperatures  
  > "Table notes: Col. 1: $L/M$ ranges taken from (cite: 2016ApJ...826L...8M)." (Table 2) [from (cite: 2016ApJ...826L...8M)]
- Simulation/model as data: RS1.0 suite of 24 radiative magnetohydrodynamical (RMHD) simulations of high-mass clump fragmentation (244 data cubes, 732 2D projected fields) computed with RAMSES (Paper I) and post-processed with RADMC-3D (Paper II), plus out-of-the-grid control models  
  > "ii. The suite of RMHD simulations - We rely on a new set of 24 radiative magnetohydrodynamical simulations of high-mass clumps fragmentation produced by means of the RAMSES code by Lebreuilly et al. (hereafter Paper I)." (The Rosetta Stone project); "iii. The radiative transfer - Our simulations are post-processed at Spitzer 24 $\mu$m, Herschel and ALMA Band 6 wavelengths by means of the RADMC-3D code by Tung et al. (hereafter Paper II)." (The Rosetta Stone project); "In total, we rely on a set of 24 available combinations of initial conditions (see Table 1), corresponding to a statistically significant sample of 244 data cubes and 732 2D fields." (Setup: Simulations and radiative transfer)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: 6.5.4  
  > "To mimic the features of the SQUALO project ALMA observations, we post-process our data using the CASA software ((cite: 2007ASPC..376..127M)), version 6.5.4." (Synthetic observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "Then, the joint deconvolution with cleaning and masking was performed interactively with the task tclean with the same pipeline settings that were applied in the imaging of the reference SQUALO source, namely:" (Rosetta Stone (SQUALO) pipeline)
- deconvolver: Multiscale  
  > "Minor cycle algorithm (deconvolver): Multiscale with scales = [0, 7, 21], to look for point-like sources and multi-scale (multiples of the beam in pixels, corresponding to the beam and three times the beam) components" (Rosetta Stone (SQUALO) pipeline)
- weighting robust: Briggs, robust = 0.5  
  > "Weighting scheme: Briggs with robustness parameter of 0.5." (Rosetta Stone (SQUALO) pipeline)
- uv taper: _not stated_
- cell size: 0.2"  
  > "Cell size: 0.2$^{\prime\prime}$, to sample our 1.29$^{\prime\prime}\times$1.51$^{\prime\prime}$ synthetic beam with $\sim 7$ pixels." (Rosetta Stone (SQUALO) pipeline)
- image size: _not stated_
- masking: Auto-multithresh  
  > "Type of mask for deconvolution: Auto-multithresh, to automatically use multiple thresholds for deconvolution." (Rosetta Stone (SQUALO) pipeline)
- multiscale scales: [0, 7, 21]  
  > "Minor cycle algorithm (deconvolver): Multiscale with scales = [0, 7, 21], to look for point-like sources and multi-scale (multiples of the beam in pixels, corresponding to the beam and three times the beam) components" (Rosetta Stone (SQUALO) pipeline)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: performed (images produced with and without primary beam correction)  
  > "Cleaned images with and without primary beam (PB) correction, as the ones displayed in Fig. 2 (c) and (d) respectively, are produced along with the residual maps and the sources masks." (Rosetta Stone (SQUALO) pipeline)
- array combination: joint deconvolution of 12 m and 7 m arrays with mosaic gridding in tclean  
  > "Then, the joint deconvolution with cleaning and masking was performed interactively with the task tclean with the same pipeline settings that were applied in the imaging of the reference SQUALO source, namely:" (Rosetta Stone (SQUALO) pipeline); "Gridding options: mosaic, to resample visibilities onto a regular $uv$-grid with azimuthally symmetric beams without side lobes." (Rosetta Stone (SQUALO) pipeline)
- smoothing: _not stated_
- final beam: 1.29" x 1.51" (~7000 AU or ~0.036 pc at 5.2 kpc)  
  > "Cell size: 0.2$^{\prime\prime}$, to sample our 1.29$^{\prime\prime}\times$1.51$^{\prime\prime}$ synthetic beam with $\sim 7$ pixels. With this setup, we reach a linear resolution of $\sim 7000$ AU (or $\sim0.036$ pc) at the reference heliocentric distance of 5.2 kpc." (Rosetta Stone (SQUALO) pipeline)
- final rms: ~0.02 to ~15 mJy/beam (mean 2.9 mJy/beam)  
  > "The estimated r.m.s. for the set of synthetic observations, calculated using the Hyper software directly on the cleaned (primary beam non-corrected) maps, ranges from $\sim0.02$ to $\sim15$ mJy/beam." (Noise consistency analysis); "The mean r.m.s. of 2.9 mJy/beam across the sample is consistent with the 1.42 mJy/beam r.m.s. of the HG24 reference source." (Noise consistency analysis)

### Inherited from earlier work

- RMHD simulation suite RS1.0 setup, sink particle parameters, and stopping SFE criteria  
  > "ii. The suite of RMHD simulations - We rely on a new set of 24 radiative magnetohydrodynamical simulations of high-mass clumps fragmentation produced by means of the RAMSES code by Lebreuilly et al. (hereafter Paper I)." (The Rosetta Stone project); "To sample an evolution range of $\sim10^5\,$years from the formation of the first sink particle, we stop the calculations at a SFE of $\sim15\%$ and $\sim30\%$ for the M500 and M1000 realizations, respectively (Paper I)." (Setup: Simulations and radiative transfer) [from Lebreuilly et al. (Paper I)]
- Radiative transfer post-processing with RADMC-3D and the quantitative relationship between SFE and L/M  
  > "iii. The radiative transfer - Our simulations are post-processed at Spitzer 24 $\mu$m, Herschel and ALMA Band 6 wavelengths by means of the RADMC-3D code by Tung et al. (hereafter Paper II)." (The Rosetta Stone project); "Specifically, Paper II establishes the quantitative relationship between the timing in SFE from the simulations in Paper I and the observational $L/M$ parameter:" (Setup: Simulations and radiative transfer) [from Tung et al. (Paper II)]
- ALMA observing strategy, tclean imaging settings, Hyper source extraction settings, dust opacity assumption, and single-temperature fragment mass estimation method  
  > "Then, the joint deconvolution with cleaning and masking was performed interactively with the task tclean with the same pipeline settings that were applied in the imaging of the reference SQUALO source, namely:" (Rosetta Stone (SQUALO) pipeline); "In agreement with the settings used in the SQUALO project, we considered as compact sources all identified objects with semi-axes between one and two times the telescope beam size, having a maximum aspect ratio of 1.5." (Source extraction and photometry); "As in (cite: 2023MNRAS.520.2306T), we adopt the single temperature model to derive the mass of the fragments associated with the same parent clump." (Physical properties of the fragments) [from (cite: 2023MNRAS.520.2306T)]

### Not stated but needed to reproduce (our reading)

- Exact antenna configuration files (.cfg) used in CASA simobserve to represent the 10-12 antennas of the 7m array and 47 antennas of the 12m array
- Exact mosaic pointing pattern and number of pointings for the 7m and 12m array execution blocks
- Image size (imsize) in pixels used in tclean
- Exact formula or mapping rule for how the tclean noise threshold is automatically set according to the source evolutionary stage
- Auto-multithresh sub-parameters in tclean (sidelobethreshold, noisethreshold, lownoisethreshold, minbeamfrac)
- Bandwidth setting used in simobserve for the 231.1 GHz continuum channel

## Analysis recipe

1. **Run RMHD simulations of high-mass clump fragmentation**: 3D radiative magnetohydrodynamical simulations under ideal MHD using adaptive mesh refinement finite-volume code RAMSES with self-gravity, accretion luminosity radiation, turbulence, magnetic fields, and sink particles  
  > "Our simulations solve the three-dimensional equations for the conservation of gas mass, momentum, total energy, and radiation total energy, as well as the evolution of the magnetic field under the assumption of ideal MHD." (Setup: Simulations and radiative transfer); "In these models, which are computed by means of the adaptive mesh refinement finite-volume code RAMSES ((cite: 2002A&A...385..337T); (cite: 2006A&A...457..371F)), individual forming stars are represented by sink particles ((cite: 2014MNRAS.445.4015B)) that form self-consistently above a threshold of $n_{thre} = 10^9$ cm$^{-3}$." (Setup: Simulations and radiative transfer)
   - software: RAMSES
   - parameter: Clump mass M = [500, 1000] M_sun, radius R = 0.383 pc (~0.4 pc), initial temperature = 10 K  
  > "These values correspond to clump masses of 500 and 1000 M$_\odot$, a radius of $\sim 0.4$ pc (e.g., (cite: 2014MNRAS.443.1555U), (cite: 2017MNRAS.470.3882T), (cite: 2021MNRAS.504.2742E)), and a temperature of 10 K" (Setup: Simulations and radiative transfer); "$R$ (pc) [0.383]" (Table 1)
   - parameter: Mach number M = [7, 10], normalized mass-to-flux ratio mu = [3, 10, 100], turbulent seeds = [1, 2], 3 orthogonal projections (x, y, z)  
  > "Seed [1, 2] $M$ (M$_\odot$) [500, 1000] $R$ (pc) [0.383] $\mu$ [3, 10, 100] $\mathcal{M}$ [7, 10]" (Table 1); "For each time step, three orthogonal projections are analyzed. These are fixed for all realizations, and correspond to actual projections in the sky along the $x$, $y$, and $z$ axes." (Setup: Simulations and radiative transfer)
   - parameter: Sink formation threshold n_thre = 10^9 cm^-3, native resolution ~40 AU, accretion luminosity factor f_acc = 0.1, stopping SFE = ~15% (M500) and ~30% (M1000)  
  > "individual forming stars are represented by sink particles ((cite: 2014MNRAS.445.4015B)) that form self-consistently above a threshold of $n_{thre} = 10^9$ cm$^{-3}$." (Setup: Simulations and radiative transfer); "the numerical computation - native at a numerical resolution of $\sim40$ AU (Paper I)" (Comparison with numerical models); "In our suite of simulations RS1.0, we compute the accretion luminosity using a fixed factor of 0.1." (The necessity of having an end-to-end framework)
   - assumption: Ideal MHD, uniform initial cloud density, uniform initial magnetic field along z-axis, feedback only from accretion luminosity (no outflows or HII regions), no sink merging  
  > "As initial condition, the magnetic field is uniform and oriented along the $z$-axis." (Setup: Simulations and radiative transfer); "As anticipated above, this first suite of simulations has been developed including feedback in the form of radiation from luminosity accretion." (Setup: Simulations and radiative transfer)
   - fitting: _not stated_
   - validation: Tested out-of-the-grid control models with Bonnor-Ebert profile, M = 3, seeds S3 and S4, and varied f_acc  
  > "To further characterize potential relationships between the number of identified fragments and the initial conditions of clump collapse, we also use a suite of out-of-the-grid control models." (Fragmentation level)
2. **Perform radiative transfer to produce 1.3 mm dust continuum sky models and L/M evolutionary indicator**: Thermal Monte Carlo dust temperature calculation and ray-tracing radiative transfer at 1.3 mm (and Spitzer/Herschel bands in Paper II) using RADMC-3D (and POLARIS for f_acc control tests)  
  > "As a first step in the post-processing, we run the previously saved snapshots of our simulations through the radiative transfer code RADMC-3D ((cite: 2012ascl.soft02015D))." (Setup: Simulations and radiative transfer); "As a first test, we change $f_{\textrm{acc}}$ in the radiative transfer calculations, using the POLARIS code (cite: Reissl+2016; Reissl+2018) to calculate the temperature and the resulting intensity maps." (The necessity of having an end-to-end framework)
   - software: RADMC-3D, POLARIS
   - parameter: Wavelength = 1.3 mm (231.1 GHz), reference distance = 5.2 kpc  
  > "The source is located at a heliocentric distance of 5.2 kpc ((cite: 2021A&A...646A..74M))." (Setup: Simulations and radiative transfer); "We focus on the radiative post-processed dust continuum emission maps at 1.3 mm as the one displayed in Fig. 2 (b)." (Setup: Simulations and radiative transfer)
   - assumption: Dust opacity k_1.3 = 0.005 g cm^-2 including a gas-to-dust mass ratio of 100; log(L/M) = 1.20 log(SFE) + 3.28  
  > "The flux is here computed with the same opacity assumption in use for the reference observation, i.e. $k_{1.3}=0.005\,\mathrm{g}\,\mathrm{cm}^{-2}$ ((cite: 1993A&A...279..577P)), that already includes a gas-to-dust mass ratio of 100." (Setup: Simulations and radiative transfer); "$\log(L/M) = 1.20_{-0.02}^{+0.02} \log(\text{SFE}) +3.28_{-0.03}^{+0.03}\,.$" (Setup: Simulations and radiative transfer)
   - fitting: _not stated_
   - validation: Verified that POLARIS recovers about 96% of the total RADMC-3D emission from the box at 1.3 mm  
  > "Before running the test, we have ensured that outputs from the two codes are comparable: POLARIS recovers about 96% of the total RADMC-3D emission from the box at 1.3 mm." (The necessity of having an end-to-end framework)
3. **Generate synthetic ALMA visibilities and clean continuum maps**: Simulate ALMA 12m (C43-1, 1 EB) and 7m (ACA, 5 EBs) visibilities with CASA simobserve matching archival project 2018.1.00443.S for HG24, followed by joint multiscale mosaic deconvolution with tclean  
  > "Taking into account the details of each execution block, we used the CASA task simobserve to create synthetic measurement sets of the 1.3 mm sky models produced in Paper II, including the corresponding $uv$ coverage and visibilities." (Rosetta Stone (SQUALO) pipeline); "Then, the joint deconvolution with cleaning and masking was performed interactively with the task tclean with the same pipeline settings that were applied in the imaging of the reference SQUALO source, namely:" (Rosetta Stone (SQUALO) pipeline)
   - software: CASA, simobserve, tclean, simalma
   - parameter: Central frequency 231.1 GHz; 7m: 5 blocks x ~470 s, 10-12 antennas; 12m: 1 block x ~360 s, 47 antennas; PWV ~1.8 and ~2.9 mm; elevation ~45 to ~72 deg  
  > "The fiducial antenna configurations, made up of $10$ to $12$ antennas for the execution blocks on the 7 m array, and $47$ antennas for the 12 m array;" (Rosetta Stone (SQUALO) pipeline); "The time on source, with $\sim470$ s of integration for each block on the 7 m array, and $\sim360$ s for the 12 m array;" (Rosetta Stone (SQUALO) pipeline); "The observing conditions, with a mean precipitable water vapor (PWV) of $\sim1.8$ and $\sim2.9$ mm computed over the observing blocks in the two different configurations;" (Rosetta Stone (SQUALO) pipeline)
   - parameter: tclean: Mfs, mosaic gridding, Multiscale scales=[0, 7, 21], Briggs robust=0.5, Auto-multithresh, cell size=0.2", beam=1.29"x1.51"  
  > "Minor cycle algorithm (deconvolver): Multiscale with scales = [0, 7, 21], to look for point-like sources and multi-scale (multiples of the beam in pixels, corresponding to the beam and three times the beam) components" (Rosetta Stone (SQUALO) pipeline); "Weighting scheme: Briggs with robustness parameter of 0.5." (Rosetta Stone (SQUALO) pipeline); "Cell size: 0.2$^{\prime\prime}$, to sample our 1.29$^{\prime\prime}\times$1.51$^{\prime\prime}$ synthetic beam with $\sim 7$ pixels." (Rosetta Stone (SQUALO) pipeline)
   - assumption: Synthetic clumps placed at heliocentric distance of 5.2 kpc matching HG24  
  > "With this setup, we reach a linear resolution of $\sim 7000$ AU (or $\sim0.036$ pc) at the reference heliocentric distance of 5.2 kpc." (Rosetta Stone (SQUALO) pipeline)
   - fitting: _not stated_
   - validation: Checked flux recovery (80% to 95% of RADMC-3D flux in PB-corrected maps), r.m.s. consistency against SQUALO observations, and compared pipeline output against default CASA simalma  
  > "In the PB corrected maps, we recover from 80% to 95% of the flux present in the RADMC-3D projected maps as a function of clump evolution." (Rosetta Stone (SQUALO) pipeline); "In Appendix 8, we report on further consistency checks performed on the recovered r.m.s.. In Appendix 9, we address the differences between the results obtained with the Rosetta Stone pipeline and those obtained with simalma." (Rosetta Stone (SQUALO) pipeline)
4. **Extract compact fragments and measure 1.3 mm photometry**: Source peak identification on non-PB-corrected maps and aperture photometry with polynomial background modeling on PB-corrected maps using Hyper  
  > "Therefore, the source extraction is performed by using the extraction code Hyper ((cite: 2015A&A...574A.119T)), which went through a fine-tuning procedure by (cite: 2023MNRAS.520.2306T)." (Source extraction and photometry); "We modeled the background with polynomials up to the second order, and we performed the peak identification on the PB non-corrected images at three times above the locally estimated r.m.s., to then compute the photometry on the relative PB corrected images" (Source extraction and photometry)
   - software: Hyper
   - parameter: Detection threshold = 3 sigma above local r.m.s.; source semi-axes (FWHM) between 1 and 2 times beam size; maximum aspect ratio = 1.5; background polynomial order up to 2  
  > "In agreement with the settings used in the SQUALO project, we considered as compact sources all identified objects with semi-axes between one and two times the telescope beam size, having a maximum aspect ratio of 1.5." (Source extraction and photometry); "We modeled the background with polynomials up to the second order, and we performed the peak identification on the PB non-corrected images at three times above the locally estimated r.m.s., to then compute the photometry on the relative PB corrected images" (Source extraction and photometry)
   - assumption: Compact elliptical sources with FWHM between 1 and 2 beams represent physical clump fragments at ~7000 AU  
  > "In agreement with the settings used in the SQUALO project, we considered as compact sources all identified objects with semi-axes between one and two times the telescope beam size, having a maximum aspect ratio of 1.5." (Source extraction and photometry)
   - fitting: 2D elliptical source fitting and polynomial background up to second order in Hyper  
  > "We have accounted for different detection thresholds, polynomials for background modeling, source sizes and shapes (defined by centroid position, position angle, pixel weighting)." (Source extraction and photometry)
   - validation: Visual validation of all 2749 identified fragments across the 393 Seed 2 maps, and independent tuning of Hyper parameters  
  > "Even though our strategy involves performing the source extraction as on the reference observations, we have also conducted an independent tuning of the software parameters." (Source extraction and photometry); "Based on the criteria provided in Section 2.3, we are able to identify (and visually validate) 2749 fragments across the 393 maps under analysis." (Results)
5. **Derive fragment masses, fragment formation efficiency (FFE), and inter-fragment distances, and compare with simulations and SQUALO observations**: Convert integrated 1.3 mm fluxes to fragment masses using optically thin dust emission equation and single-temperature model based on clump L/M, estimate temperature uncertainties via 1000 MC runs, compute FFE and 2D distance matrices (d_min,2D, d_max,2D), and cross-match fragment footprints with 3D/2D projected RAMSES sink particles  
  > "The distribution of mass of the fragments was obtained by converting fluxes into masses as follows" (Physical properties of the fragments); "The relative mass uncertainties due to the possible error on the temperature estimate is computed via 1000 MC simulations of fragments temperature, which let the temperature vary within fixed ranges." (Physical properties of the fragments); "Both quantities are derived from the distance matrix of the fragments, using the centroids of the fragments as edges to compute the relative distances." (Relative distance between the fragments)
   - parameter: Reference temperatures: T_f = 20 K (10-40 K) for L/M < 1; T_f = 30 K (10-50 K) for 1 < L/M < 10; T_f = 40 K (20-60 K) for L/M > 10; 1000 MC runs  
  > "$L$/$M < 1$ 20 10 - 40 $1 < L$/$M < 10$ 30 10 - 50 $L$/$M > 10$ 40 20 - 60" (Table 2); "The relative mass uncertainties due to the possible error on the temperature estimate is computed via 1000 MC simulations of fragments temperature, which let the temperature vary within fixed ranges." (Physical properties of the fragments)
   - assumption: Optically thin 1.3 mm dust emission, single temperature per clump based on L/M, distance D = 5.2 kpc, kappa_1.3 = 0.005 g cm^-2 (gas-to-dust ratio 100)  
  > "The flux is here computed with the same opacity assumption in use for the reference observation, i.e. $k_{1.3}=0.005\,\mathrm{g}\,\mathrm{cm}^{-2}$ ((cite: 1993A&A...279..577P)), that already includes a gas-to-dust mass ratio of 100." (Setup: Simulations and radiative transfer); "As in (cite: 2023MNRAS.520.2306T), we adopt the single temperature model to derive the mass of the fragments associated with the same parent clump." (Physical properties of the fragments)
   - fitting: Power-law fit to RAMSES mean fragment temperature as a function of L/M  
  > "By fitting the RAMSES mean temperature, computed across $\sim7000$ AU fragments in the same synthetic field, we derive a power-law of: $T_{f,\,mean}\,\textrm{(K)}\, \sim 10.4+0.7\times (L/M)^{0.75}\, \,.$" (Temperature consistency evaluation)
   - validation: Compared derived fragment temperatures and masses against RAMSES 2D projected temperature maps and integrated column density maps within fragment footprints  
  > "Using the known position of the peaks and the area covered by each fragment, we obtain the footprints of the fragments on the RAMSES projected temperature maps. A mean fragment temperature can be then evaluated within these footprints." (Temperature consistency evaluation); "In this section we compare the variations in mass estimates caused by the different temperature assumptions with the masses obtained by integrating the column density maps from simulations." (Mass consistency evaluation)

## Software

- **RAMSES** : Adaptive mesh refinement finite-volume code used to run the 3D RMHD simulations of high-mass clump fragmentation  
  > "ii. The suite of RMHD simulations - We rely on a new set of 24 radiative magnetohydrodynamical simulations of high-mass clumps fragmentation produced by means of the RAMSES code by Lebreuilly et al. (hereafter Paper I)." (The Rosetta Stone project); "In these models, which are computed by means of the adaptive mesh refinement finite-volume code RAMSES ((cite: 2002A&A...385..337T); (cite: 2006A&A...457..371F)), individual forming stars are represented by sink particles" (Setup: Simulations and radiative transfer)
- **RADMC-3D** : Radiative transfer code used to post-process simulations into dust temperature and 1.3 mm continuum emission maps  
  > "iii. The radiative transfer - Our simulations are post-processed at Spitzer 24 $\mu$m, Herschel and ALMA Band 6 wavelengths by means of the RADMC-3D code by Tung et al. (hereafter Paper II)." (The Rosetta Stone project); "As a first step in the post-processing, we run the previously saved snapshots of our simulations through the radiative transfer code RADMC-3D ((cite: 2012ascl.soft02015D))." (Setup: Simulations and radiative transfer)
- **CASA** 6.5.4: Post-processing radiative transfer sky models into synthetic ALMA observations and imaging  
  > "To mimic the features of the SQUALO project ALMA observations, we post-process our data using the CASA software ((cite: 2007ASPC..376..127M)), version 6.5.4." (Synthetic observations)
- **simobserve** 6.5.4: CASA task used to create synthetic measurement sets and visibilities from 1.3 mm sky models  
  > "Taking into account the details of each execution block, we used the CASA task simobserve to create synthetic measurement sets of the 1.3 mm sky models produced in Paper II, including the corresponding $uv$ coverage and visibilities." (Rosetta Stone (SQUALO) pipeline)
- **tclean** 6.5.4: CASA task used for interactive joint deconvolution with multiscale cleaning and auto-multithresh masking  
  > "Then, the joint deconvolution with cleaning and masking was performed interactively with the task tclean with the same pipeline settings that were applied in the imaging of the reference SQUALO source, namely:" (Rosetta Stone (SQUALO) pipeline)
- **simalma** 6.5.4: CASA task used to compute synthetic ALMA observations under default setup for pipeline comparison in Appendix C  
  > "For a given simulated source, visibilities can be computed using the simalma task for ideal ALMA interferometer arrays setups." (Creating synthetic observations with the CASA software: Main challenges); "Specifically, we compare the results obtained using the Rosetta Stone pipeline - which includes a tailored computation of visibilities and the parameters of the SQUALO project, optimized for clump fragmentation observations - with those from the simalma pipeline" (Pipelines comparison)
- **Hyper** : Compact source extraction, background polynomial modeling, aperture photometry, and map r.m.s. estimation  
  > "v. The source extraction and photometry - We identify compact sources and we compute the photometry using the Hyper software ((cite: 2015A&A...574A.119T))." (The Rosetta Stone project); "For each map in our sample of 732, we used Hyper to estimate the fragment and field parameters." (Source extraction and photometry)
- **POLARIS** : Radiative transfer code used to test variations of the accretion luminosity factor f_acc in Appendix E  
  > "As a first test, we change $f_{\textrm{acc}}$ in the radiative transfer calculations, using the POLARIS code (cite: Reissl+2016; Reissl+2018) to calculate the temperature and the resulting intensity maps." (The necessity of having an end-to-end framework)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total number of identified fragments (Seed 2 sample of 393 maps) | 2749 | not stated | dimensionless | 4 | Based on the criteria provided in Section 2.3, we are able to identify (and visually validate) 2749 fragments across the 393 maps under analysis. |
| Number of fragments per synthetic field | 2 to 14 (average ~7) | not stated | dimensionless | 4 | The fragmentation levels we observe within individual fields range from $2$ to $14$ fragments, with an average of $\sim7$ fragments. |
| Radii of validated fragments (R_f) | 0.036 to 0.071 | not stated | pc | 4 | The sample of validated fragments is characterized by radii in the range $0.036\leq R_f \leq 0.071$ pc, computed as the geometrical mean of the two FWHMs estimated by Hyper. |
| Point-like source 1-sigma mass sensitivity across synthetic sample | 0.02 to 5.4 | not stated | M_odot | 5 | From this procedure, we estimate a point-like source mass sensitivity in the range between $\sim0.02$ and $\sim5.4$ M$_\odot$ across the whole sample. |
| Fragment mass range (M500 realizations, single-temperature) | 0.02 to 314 | 0.01 to 724 (from 1000 MC runs) | M_odot | 5 | For the M500 realizations, the range of mass covers structures from $\sim0.02$ to $\sim314$ M$_\odot$.; Following this strategy, the ranges of mass are updated: between $\sim0.01$ and $\sim724$ M$_\odot$, and between $\sim0.01$ and $\sim2338$ M$_\odot$, for the M500 and M1000 realizations, respectively. |
| Fragment mass range (M1000 realizations, single-temperature) | 0.02 to 1010 | 0.01 to 2338 (from 1000 MC runs) | M_odot | 5 | For the M1000 realizations the range in mass is wider, from $\sim0.02$ to $\sim1010$ M$_\odot$.; Following this strategy, the ranges of mass are updated: between $\sim0.01$ and $\sim724$ M$_\odot$, and between $\sim0.01$ and $\sim2338$ M$_\odot$, for the M500 and M1000 realizations, respectively. |
| Median fragment mass (M500 realizations) | 4 | not stated | M_odot | 5 | For each mass distribution we compute the median value, which corresponds to $\sim4$ and $\sim11$ M$_\odot$, respectively. |
| Median fragment mass (M1000 realizations) | 11 | not stated | M_odot | 5 | For each mass distribution we compute the median value, which corresponds to $\sim4$ and $\sim11$ M$_\odot$, respectively. |
| Power-law exponent of RAMSES mean fragment temperature vs L/M | 0.75 | not stated | dimensionless | 5 | By fitting the RAMSES mean temperature, computed across $\sim7000$ AU fragments in the same synthetic field, we derive a power-law of: $T_{f,\,mean}\,\textrm{(K)}\, \sim 10.4+0.7\times (L/M)^{0.75}\, \,.$ |
| Fraction of identified fragments corresponding to sink particles | 75.2 (2066 of 2749) | not stated | % | 5 | Fragments w/ sinks 2066 $\sim75.2$ |
| Fraction of identified fragments corresponding to a single sink particle | 16.7 (458 of 2749) | not stated | % | 5 | Fragments w/ one sink 458 $\sim16.7$ |
| Fraction of identified fragments corresponding to multiple sink particles | 58.5 (1608 of 2749) | not stated | % | 5 | Fragments w/ multiple sinks 1608 $\sim58.5$ |
| Fraction of identified fragments without any sink particle | 24.8 (683 of 2749) | not stated | % | 5 | Fragments w/out sinks 683 $\sim24.8$ |
| Fraction of sink particles corresponding to identified fragments | 76.4 (12389 of 16209) | not stated | % | 5 | Sinks w/ fragments 12389 $\sim76.4$ |
| Flux recovered in PB-corrected synthetic maps relative to RADMC-3D maps | 80 to 95 | not stated | % | 3 | In the PB corrected maps, we recover from 80% to 95% of the flux present in the RADMC-3D projected maps as a function of clump evolution. |
| Dynamic range across all synthetic fields | 2 to 115 | not stated | dimensionless | 3 | The dynamic range estimated across all realizations and all evolutionary steps goes from $\sim2$ to $\sim115$. |

## Qualitative findings

- Fragmentation occurs at every evolutionary stage across all synthetic maps, with fragment multiplicity only weakly dependent on initial clump mass or explored Mach numbers (7 vs 10).  
  > "On the contrary, our analysis indicates that fragmentation takes place within the clumps at every evolutionary stage, and that the number of fragments within each field is only weakly dependent on the initial mass of the clump." (Fragmentation level); "As shown in Fig. 5, the explored levels of turbulence do not appear to have a significant effect on the multiplicity of fragments." (Fragmentation level)
- Magnetic fields have the largest impact on fragment multiplicity at ~7000 AU scales for L/M >= 20 L_sun/M_sun, with weaker magnetic fields (mu = 100) producing more fragments and stronger magnetic fields favoring smaller maximum inter-fragment separations (d_max,2D).  
  > "Comparing the level of fragmentation for the three available clump magnetization (i.e., $\mu=3$, 10, and 100) we observe that, for $L/M \gtrsim 20$ L$_\odot$/M$_\odot$, a larger number of fragments are preferentially formed when the magnetic parameter $\mu$ is set to the highest of the three explored values." (Fragmentation level); "We find that slightly smaller mean values of $d_{\text{max,2D}}$ - reflecting a smaller separation between the most distant fragments - are preferentially observed toward evolved, magnetized clumps." (Relative distance between the fragments)
- Observationally driven single-temperature assumptions based on SQUALO L/M ranges underestimate total fragment mass by a factor ~10 in the earliest evolutionary step and overestimate it by a factor ~2 in the most evolved stages (L/M > 100 L_sun/M_sun).  
  > "In this case, the SQUALO temperature assumption, as the averaged RAMSES temperatures, do not reflect the actual RAMSES temperature along the line of sight causing the underestimation of the total mass in fragments. We observe a factor $\sim10$ of difference with respect to the mass derived from the column density." (Mass consistency evaluation); "Additionally, the SQUALO-like mass estimates in the latest evolutionary stages exhibit a factor $\sim2$ of difference with respect to the results obtained using RAMSES temperatures or column density maps." (Mass consistency evaluation)
- The Rosetta Stone simulations fail to systematically reproduce clumps with 1 fragment (zero occurrences) or 2 fragments as seen in 4 of the 13 SQUALO sources, even when exploring out-of-the-grid control models.  
  > "As of now, our suite of simulations does not systematically reproduce cases with $1$ (zero occurrence) or $2$ fragments, which are instead observed in the SQUALO sample." (Summary and conclusions); "None of these control models allows us to systematically reproduce the cases of low or no fragmentation." (The necessity of having an end-to-end framework)

## Claim tuples

- H: Initial clump magnetization and turbulence regulate the fragmentation multiplicity and spatial clustering observed at ~7000 AU scales. | E: Post-processed 24 RMHD simulations (varying mass, Mach number, and mass-to-flux ratio mu) with RADMC-3D and CASA simobserve/tclean to match the SQUALO ALMA 1.3 mm survey, extracting fragments with Hyper. | R: Synthetic fields show 2 to 14 fragments; for L/M >= 20 L_sun/M_sun, weakly magnetized clumps (mu=100) produce higher fragment multiplicities (>11) and larger d_max,2D than magnetized clumps (mu=3, 10), while Mach 7 vs 10 shows no significant difference. | F: Magnetic fields have the strongest impact among explored initial conditions on fragment multiplicity and clustering at ~7000 AU in advanced evolutionary stages, though line-of-sight projection and stochastic seed variations can partially mask the effect. | **supported**
- H: Clump fragments identified at ~7000 AU resolution evolve via continuous mass accretion from their parent clump (clump-fed scenario) rather than in isolation. | E: Tracked the total mass recovered in fragments and the fragment formation efficiency (FFE) as a function of the clump evolutionary indicator L/M across synthetic time steps and compared with SQUALO observations and sink formation efficiency (SFE). | R: Total mass in fragments and FFE increase continuously with L/M across all initial conditions, aligning well with the 13 SQUALO clumps, while FFE consistently exceeds SFE before converging toward the 1:1 line at advanced stages. | F: Fragments are not isolated from their environment and continuously accrete mass from the parent clump reservoir across scales, supporting a hierarchical, clump-fed star-formation scenario. | **supported**
- H: Fragments detected at ~7000 AU in 1.3 mm continuum maps correspond one-to-one with individual star-forming sink particles in the underlying simulations. | E: Cross-matched the 2D footprints of 2749 validated synthetic fragments with the projected positions of 16209 sink particles from the RAMSES simulations. | R: 75.2% of fragments match at least one sink (16.7% match a single sink, 58.5% match multiple sinks) and 24.8% contain no sinks (transients, pre-collapse overdensities, or beam-convolved diffuse gas along the line of sight). | F: Fragments at ~7000 AU do not correspond one-to-one with forming stars; most host multiple sinks due to hierarchical multi-scale fragmentation, while about a quarter are not actively forming stars at that time step. | **refuted**
- H: A tailored synthetic observation pipeline replicating multi-execution-block uv-coverage, weather, and multiscale cleaning is required over default CASA simalma to accurately reproduce real interferometric clump observations. | E: Compared synthetic 1.3 mm maps and Hyper source extractions produced with the custom Rosetta Stone (simobserve + tclean) pipeline against default CASA simalma at L/M ~ 10 and 250 L_sun/M_sun. | R: Default simalma loses up to ~80% (~40%) of large-scale clump flux and ~50% (~20%) of fragment flux in early (late) stages, yields a ~1.2x larger beam, and produces false positive and false negative fragment detections. | F: Tailored visibility simulation and multiscale auto-masked deconvolution are essential to avoid severe large-scale flux loss and spurious source detections when comparing simulations with interferometric surveys. | **supported**

## Reasoning

- Why this data: The SQUALO survey (specifically reference source HG24 at 5.2 kpc) provides a well-characterized sample of 13 high-mass star-forming clumps with infall motions observed at 1.3 mm with ALMA (12m + ACA) at ~7000 AU resolution.  
  > "i. The reference observations - Our first case study takes as reference ALMA 1.3 mm continuum dust emission observations from the Star formation in QUiescent And Luminous Objects (SQUALO) survey by (cite: 2023MNRAS.520.2306T)." (The Rosetta Stone project); "In particular, we reproduce the observational strategy used to observe the target source HIGALBM24.0116+0.4897 (HG24), on which forthcoming studies from the SQUALO survey are focusing (Jones et al. in prep.)." (Setup: Simulations and radiative transfer)
- Why this method: Using CASA simobserve with actual execution block reports, joint multiscale tclean, and Hyper source extraction identical to the SQUALO pipeline ensures that instrumental filtering, noise, and extraction biases match the real observations for a self-consistent comparison.  
  > "To effectively address the physics governing star-forming sites at the scales probed by the observations, it is therefore necessary to apply a rigorous post-processing routine to the simulations and ensure that these also mimic the observational features (instrumental effects and observational biases) of the dataset they will be compared against." (Introduction); "As for the previous post-processing steps, we want the source extraction and photometry to match that performed on the reference observations as much as possible. This approach further reduces the chance of introducing additional biases when comparing observations to simulations." (Source extraction and photometry)
- Alternative: Using default CASA simalma instead of custom simobserve + tclean pipeline (rejected because simalma loses up to 80% of extended flux and creates false positive/negative fragment detections).  
  > "For a given simulated source, visibilities can be computed using the simalma task for ideal ALMA interferometer arrays setups." (Creating synthetic observations with the CASA software: Main challenges); "In the simalma cleaned map at $L/M \sim 10$ L$_\odot$/M$_\odot$, the unrealistic UV coverage leads to the production of false positives and negatives (see Fig. 13), which make source identification and photometry unreliable" (Pipelines comparison)
- Alternative: Identifying 3D fragment-like structures directly within simulations smoothed to ~7000 AU instead of 2D synthetic observations (deferred as beyond scope because the primary goal is self-consistent 2D observational comparison with SQUALO).  
  > "A more robust characterization would require identifying three-dimensional, fragment-like structures directly within the simulations smoothed at $\sim7000$ AU, which is currently beyond the scope of this work." (Analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Simulations only include feedback from accretion luminosity, omitting protostellar outflows/jets and HII regions.  
  > "As anticipated above, this first suite of simulations has been developed including feedback in the form of radiation from luminosity accretion." (Setup: Simulations and radiative transfer); "Outflows and Hii regions are planned to be incorporated in a future set of Rosetta Stone models." (Setup: Simulations and radiative transfer)
- Limitation (authors): The SQUALO single-temperature prescription (T_f = 40 K, range 20-60 K for L/M > 10) was not designed for L/M > 100 L_sun/M_sun, causing systematic mass overestimation (by a factor ~2) in the most evolved synthetic clumps.  
  > "As a consequence, the reference temperature of 40 K was not conceived to represent clumps with $L/M > 100$ L$_\odot$/M$_\odot$." (Physical properties of the fragments); "The mismatch between the SQUALO assumption and the temperature estimates derived from the numerical simulation causes a systematical overestimation of the mass of the observed fragments in the most evolved clumps." (Temperature consistency evaluation)
- Limitation (authors): All synthetic clumps are placed at a single distance (5.2 kpc, the farthest in SQUALO, corresponding to ~7000 AU or ~0.036 pc linear resolution), whereas real SQUALO clumps span 2.0 to 5.5 kpc, biasing minimum separation d_min,2D and mass sensitivity comparisons.  
  > "While the synthetic clumps are all located at the same distance from the observer, SQUALO clumps are distributed across $13$ different distances, resulting in observations at varying resolutions." (Physical properties of the fragments); "Specifically, we are replicating the observations of the farthest source within the SQUALO sample, which corresponds to the lowest linear resolution in that dataset." (Comparison with relative distances from the SQUALO sample)
- Limitation (authors): Simulations model isolated uniform spherical clumps in boxes without large-scale filamentary inflow or external dynamics, limiting the ability to reproduce compact d_max,2D distributions or clumps with only 1-2 fragments.  
  > "In this case, $d_{\text{max,2D}}$ is likely not recovered properly due to the absence of large-scale dynamics in our simulations, as we are simulating clumps within isolated boxes." (Comparison with relative distances from the SQUALO sample)
- Limitation (authors): Sink particle merging is not allowed in the RAMSES prescription, so sink numbers can never decrease, and lack of tracer particles prevents tracking individual fragments across time steps.  
  > "We will be able to address these specific aspects more effectively by closely tracking the evolution of individual fragments through the use of tracer particles, which we plan to include in a forthcoming suite of simulations." (Fragments versus sinks multiplicity); "In our prescription, the merging of sink particles is not allowed. Consequently, the number of sink particles can never decrease." (Fragments versus sinks multiplicity)
- Caveat (inferred, ours): Placing all synthetic simulations at 5.2 kpc (the worst linear resolution in SQUALO) creates a resolution mismatch when comparing d_min,2D and multiplicity against closer SQUALO clumps (at 2-3 kpc).
- Caveat (inferred, ours): Visual validation of the 2749 Hyper-extracted fragments introduces a subjective human step that is not easily reproducible or automated.
- Caveat (inferred, ours): The two Mach numbers tested in the main grid (M = 7 and 10) are too close in value to meaningfully probe the role of turbulence on fragmentation.

## Reproducibility

- Data public (paper): ALMA archival data 2018.1.00443.S used for reference observation setups; project website provided for Rosetta Stone framework  
  > "To address this problem, we developed the Rosetta Stone project: an end-to-end (simulation $\Leftrightarrow$ observations) framework" (Introduction); "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00443.S." (Acknowledgements)
- Products in archive: _not stated_
- Code: Hyper code is publicly available on GitHub (https://github.com/Alessio-Traficante/hyper-py); Rosetta Stone project website listed (https://www.the-rosetta-stone-project.eu)  
  > "https://www.the-rosetta-stone-project.eu" (Introduction); "The latest Python-based version of the Hyper code is available at: https://github.com/Alessio-Traficante/hyper-py." (Source extraction and photometry)
- Missing: The 244 RAMSES 3D simulation snapshots (Paper I) and 732 RADMC-3D 1.3 mm sky model FITS files (Paper II) are not directly linked in a public data repository in the text.
- Missing: Exact CASA simobserve scripts, antenna configuration files (.cfg) with the specific flagged/active antenna subsets from 2018.1.00443.S, and mosaic pointing files.
- Missing: Exact rule/script for the automatic evolutionary-stage-dependent noise threshold used in tclean.
- Missing: Criteria used for the manual visual validation of the 2749 fragments extracted by Hyper.
- Data volume (inferred): ~50-200 GB (732 synthetic ALMA 12m+7m measurement sets and cleaned images, plus 244 3D RAMSES/RADMC-3D data cubes)
- Score (inferred): 65/5, The paper provides a remarkably detailed description of the CASA simobserve/tclean parameters, observing block setups from ALMA project 2018.1.00443.S, and Hyper extraction settings, as well as the SQUALO reference table. However, full reproduction is blocked unless the underlying RAMSES/RADMC-3D sky models from Papers I and II are obtained, and because of an unstated automated tclean threshold rule and manual visual validation of fragments.
- Rediscovery candidate: no, The primary dataset analyzed is a suite of 732 synthetic ALMA maps generated from custom RAMSES/RADMC-3D simulations (Papers I and II) rather than raw archival ALMA observations alone, and fragment selection involves visual validation.

## Links

- Method: (cite: 2002A&A...385..337T) (RAMSES adaptive mesh refinement code used for the RMHD simulations)
- Method: (cite: 2006A&A...457..371F) (MHD implementation in RAMSES)
- Method: (cite: 2014MNRAS.445.4015B) (Sink particle algorithm in RAMSES)
- Method: (cite: 2012ascl.soft02015D) (RADMC-3D radiative transfer code used to produce 1.3 mm dust emission sky models)
- Method: (cite: 2007ASPC..376..127M) (CASA software package used for visibility simulation and imaging)
- Method: (cite: 2015A&A...574A.119T) (Hyper source extraction and photometry software)
- Method: (cite: Reissl+2016; Reissl+2018) (POLARIS radiative transfer code used for accretion luminosity efficiency tests)
- Companion: Lebreuilly et al. (Paper I) (Introduces the RS1.0 suite of 24 RAMSES RMHD simulations of high-mass clump fragmentation)
- Companion: Tung et al. (Paper II) (Performs the RADMC-3D radiative transfer on the RS1.0 simulations and derives the SFE to L/M relation)
- Companion: (cite: 2023MNRAS.520.2306T) (Presents the reference SQUALO ALMA 1.3 mm survey observations, imaging pipeline, and fragment analysis)
- Related: Rosetta Stone project
- Related: SQUALO (Star formation in QUiescent And Luminous Objects)
- Related: Hi-GAL
- Related: ALMAGAL
- Related: ECOGAL

## Checks

```json
{
 "quotes": 169,
 "quotes_ok": 169,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 8,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 102,
  "stated": 80,
  "rate": 0.784
 },
 "evidence_ok": true
}
```
