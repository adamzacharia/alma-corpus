# The ALMA-QUARKS Survey. II. The ACA 1.3 mm Continuum Source Catalog and the Assembly of Dense Gas in Massive Star-Forming Clumps

`2024RAA....24f5011X` | Research in Astronomy and Astrophysics 2024 | first author: Xu, Fengwei | arXiv: 2404.02275 | DOI: 10.1088/1674-4527/ad3dc3

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: star_formation, milky_way_ism
- Question: How dense gas is assembled in massive clumps: build the QUARKS ACA 1.3 mm continuum source catalog (physical parameters) and test clump-fragment mass correlation, dense gas fraction and its evolution, and limited fragmentation  
  > "Investigating how dense gas is concentrated and structured within these massive clumps serves as an intermediate step in understanding this intricate process." (Introduction); "we find a mass correlation between clumps and their fragments" (Introduction)
- Target **QUARKS clumps (139 ATOMS massive clumps)**: coordinates not stated (per-source ICRS coordinates given in Table 2)  
  > "As a result, 139 ATOMS massive clumps are selected as the QUARKS sample, hereafter the QUARKS clumps." (Observing Strategy); "equivalent to 0.07 pc at a typical distance of 3 kpc within the QUARKS sample" (Introduction); "and the latest model for the rotation curve of the Milky Way (cite: Reid2019Distance)" (QUARKS Atlas); z/distance typical 3 kpc; per-clump distances listed in Table A of Liu2023QUARKS  
  > "As a result, 139 ATOMS massive clumps are selected as the QUARKS sample, hereafter the QUARKS clumps." (Observing Strategy); "equivalent to 0.07 pc at a typical distance of 3 kpc within the QUARKS sample" (Introduction); "and the latest model for the rotation curve of the Milky Way (cite: Reid2019Distance)" (QUARKS Atlas); distance from H13CO+ lines of ATOMS plus the Milky Way rotation curve model of Reid2019Distance (cite: Reid2019Distance)  
  > "As a result, 139 ATOMS massive clumps are selected as the QUARKS sample, hereafter the QUARKS clumps." (Observing Strategy); "equivalent to 0.07 pc at a typical distance of 3 kpc within the QUARKS sample" (Introduction); "and the latest model for the rotation curve of the Milky Way (cite: Reid2019Distance)" (QUARKS Atlas)
- Target **I13291-6229 (example field)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2021.1.00095.S, 2019.1.00685.S
- bands: Band 6 (1.3 mm), dual polarization  
  > "The observations utilized ALMA Band 6 receivers in dual-polarization mode, with the correlator frequencies configured into four spectral windows (SPWs 1–4)." (Observing Strategy)
- frequencies and spectral setup: four SPWs centred at ~217.92, 220.32, 231.37, 233.52 GHz, each 2 GHz wide with 4096 channels  
  > "The four SPWs were designed with center frequencies at approximately 217.92 GHz, 220.32 GHz, 231.37 GHz, and 233.52 GHz, each with a bandwidth of 2 GHz and 4096 channels." (Observing Strategy)
- continuum bandwidth: _not stated_
- arrays: ACA 7-m  
  > "In this paper, we focus mainly on the Atacama Compact Array (ACA) 7-m continuum and line data sets." (Introduction)
- configurations: _not stated_
- baselines: per-group minimum and maximum baselines given in Table 1 column (4)  
  > "so they share similar minimum and maximum baselines (BL), angular resolution (AR), and maximum recoverable scale (MRS)" (Observing Strategy)
- angular resolution: ~5 arcsec (0.07 pc at 3 kpc); per-group AR in Table 1 column (5)  
  > "With an angular resolution of $\sim5$$''$, equivalent to 0.07 pc at a typical distance of 3 kpc within the QUARKS sample" (Introduction)
- max recoverable scale: ~27 arcsec (per-group MRS in Table 1 column (6))  
  > "a maximum recoverable scale as large as $\sim27$$''$" (Introduction)
- sensitivity: continuum rms varies by group (Table 1 column 9), limited by dynamic range; typical 7-m continuum sensitivity 15 mJy (mass limit ~3 Msun at 3 kpc, 20 K)  
  > "The rms levels have large variations between groups because some sources are too strong and the continuum sensitivities are limited by the dynamic range." (Data Calibration and Imaging); "typical ATOMS and QUARKS 7-m continuum sensitivities of 0.2 and 15 mJy give sensitivity limits of 1.5 and 3 $M_\odot$, respectively" (Protocluster ensembles)
- time on source: about 5 minutes per pointing (156 pointings)  
  > "The on-source time of each pointing was about 5 minutes." (Observing Strategy); "A total of 156 ALMA 1.3 mm pointings were performed" (Observing Strategy)
- observing dates: ALMA Cycle 8 and 9; 1-3 execution blocks per group, dates in Table 1 column (3)  
  > "QUARKS ACA data were acquired during the ALMA Cycle 8 and 9 observations." (Data Calibration and Imaging); "1–3 execution blocks (EBs) were performed on different observing dates, which are listed in column (3)" (Observing Strategy)
- pi or archival as stated: QUARKS survey, PIs Lei Zhu, Guido Garay and Tie Liu; ACA 1.3 mm images of ASHES clumps retrieved for a comparison sample  
  > "QUARKS; PIs: Lei Zhu, Guido Garay and Tie Liu; Project ID: 2021.1.00095.S" (Introduction); "We also retrieved 39 ACA 1.3 mm continuum images from the" (Self-similarity in protocluster formation)
- Line: p-H2CO 3(0,3)-2(0,2) (218.22219 GHz)
- Line: p-H2CO 3(2,2)-2(2,1) (218.47563 GHz)
- Line: p-H2CO 3(2,1)-2(2,0) (218.76007 GHz)
- Other facility **ATOMS (ALMA 3 mm, 12m+ACA)**: 3 mm continuum data and dense core catalog cross-matched with ACA sources  
  > "the ATOMS 12m+ACA combined 3 mm continuum data can trace both the dust emission from cold dense cores" (QUARKS Atlas); "we performed a spatial cross-match between the ATOMS 3 mm continuum dense cores by (cite: Liu2021ATOMS-III) and the QUARKS ACA 1.3 mm continuum sources" (Protocluster ensembles)
- Other facility **Spitzer GLIMPSE**: 3.6, 4.5, 8.0 micron images for the atlas  
  > "Here we combine the Galactic Legacy Infrared Mid-Plane Survey Extraordinaire (GLIMPSE) data at 3.6, 4.5, and 8.0" (QUARKS Atlas)
- Other facility **ALLWISE**: 3.4, 4.6, 22.0 micron images where no Spitzer data  
  > "for these we use ALLWISE data at 3.4, 4.6, and 22.0" (QUARKS Atlas)
- Other facility **ATLASGAL**: ~870 micron large-scale dust emission for the atlas  
  > "We use the ATLASGAL data to trace the large scale cold and dense gas which indicates the star formation region" (QUARKS Atlas)
- Other facility **Herschel Hi-GAL**: 500 micron images where no ATLASGAL data  
  > "If no ATLASGAL data are available, far infrared (FIR) Herschel data from" (QUARKS Atlas)
- Other facility **MeerKAT Galactic Plane Survey**: 1.28 GHz radio continuum tracing ionized gas for the atlas  
  > "The MeerKAT Galactic Plane Survey 1.28 GHz data (cite: Padmanabh2023MeerKAT; Goedhart2023MGPS) provides essential radio information with a resolution of" (QUARKS Atlas)
- Other facility **ASHES (ALMA ACA 1.3 mm)**: 39 ACA continuum images of early-stage clumps used as a comparison sample for the dense gas fraction  
  > "We also retrieved 39 ACA 1.3 mm continuum images from the" (Self-similarity in protocluster formation); "To maintain consistency, we cropped the ASHES continuum images to the same size as the QUARKS." (Self-similarity in protocluster formation)
- External data: QUARKS clump masses and radii  
  > "We collect the QUARKS clump mass $M_{\rm clump}$ and radius $R_{\rm clump}$ from (cite: Liu2023QUARKS)" (Fragments with self-similar gravitational collapse) [from (cite: Liu2023QUARKS)]
- External data: QUARKS clump distances  
  > "as listed in Table A. of (cite: Liu2023QUARKS)" (QUARKS Atlas) [from (cite: Liu2023QUARKS)]
- External data: Clump-averaged dust temperatures from infrared-to-submillimeter SED fitting  
  > "determined through infrared-to-submillimeter SED fitting (cite: Urquhart2018ATLASGAL)" (Temperature Estimation from Formaldehyde) [from (cite: Urquhart2018ATLASGAL)]
- External data: Clump masses for the combined, ASHES, Csengeri and SQUALO samples  
  > "all the clump masses are retrieved from (cite: Urquhart2018ATLASGAL) in the following discussion" (Dense gas grows with evolution) [from (cite: Urquhart2018ATLASGAL)]
- External data: ATOMS 3 mm dense core catalog  
  > "Dense cores identified in (cite: Liu2021ATOMS-III) are marked with red ellipses and ID numbers." (QUARKS Atlas) [from (cite: Liu2021ATOMS-III)]
- External data: Dust opacity (1 cm2 g-1 at ~230 GHz)  
  > "which is interpolated from the given table in (cite: O&H1994dust)" (Physical Parameters of Sources) [from (cite: O&H1994dust); size distribution (cite: MRN1997)]
- External data: Uncertainties of 28% (gas-to-dust ratio) and 23% (dust opacity)  
  > "We adopt the uncertainties derived by (cite: Sanhueza2017G28) of 28% for the gas-to-dust ratio and of 23% for the dust opacity" (Physical Parameters of Sources) [from (cite: Sanhueza2017G28)]
- External data: Flux calibration uncertainty of 10%  
  > "from flux calibration (assumed to be 10%; Yun et al. 2022" (Physical Parameters of Sources) [from Yun et al. 2022 (ALMA Memo 211)]
- External data: H2CO collision rates for RADEX  
  > "the collision rates were taken from (cite: Wiesenfeld2013H2CO)" (Non-LTE Model Fitting of H2CO) [from (cite: Wiesenfeld2013H2CO)]
- External data: DGF results from ACA 0.87 mm survey and SQUALO  
  > "We incorporate the DGF results from an ACA 0.87 mm survey (cite: Csengeri2017ACA) and the" (Dense gas grows with evolution) [from (cite: Csengeri2017ACA); (cite: Traficante2023SQUALO-I)]
- Simulation/model as data: RADEX non-LTE model grid for p-H2CO: 100 densities 10^2.5-10^7 cm-3, 100 N(H2CO) 10^11-10^15 cm-2, 50 Tkin 10-350 K, line gradient 5 km/s/pc  
  > "we used RADEX (cite: van2007RADEX) to create model grids for the p-H$_2$CO molecular lines over 100 densities of $n=10^{2.5}$–$10^{7}$ cm$^{-3}$" (Non-LTE Model Fitting of H2CO); "with a fixed assumed line gradient of 5 km s$^{-1}$ pc$^{-1}$" (Non-LTE Model Fitting of H2CO)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline (routine calibration)  
  > "The data were routinely calibrated using the ALMA pipelines" (Data Calibration and Imaging)
- casa version: CASA 6.2.1 and 6.4.1 for pipeline calibration; CASA 6.5.6 for tclean imaging  
  > "in the corresponding versions of 6.2.1 and 6.4.1" (Data Calibration and Imaging); "The continuum and line cube imaging processes were performed by the task *tclean* in CASA 6.5.6" (Data Calibration and Imaging)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: bandpass/flux calibrators listed per group in Table 1 column (8), e.g. J1058+0133, J1427-4206, J1924-2914, J2232+1143  
  > "while bandpass and flux calibrators are listed in column (8)" (Observing Strategy); "J1427-4206" (Table 1); "J1924-2914" (Table 1)
- flux scale uncertainty: 10% (assumed)  
  > "from flux calibration (assumed to be 10%; Yun et al. 2022" (Physical Parameters of Sources)
- self calibration: not performed  
  > "self-calibration has not been performed on our released ACA data" (Data Calibration and Imaging)

### Imaging

- task: tclean in CASA 6.5.6  
  > "The continuum and line cube imaging processes were performed by the task *tclean* in CASA 6.5.6, with `briggs` robust weighting of 0.5." (Data Calibration and Imaging)
- deconvolver: multiscale for line cubes, scales [0,5,15]; continuum deconvolver not stated  
  > "we applied the `multiscale` deconvolver (cite: Cornwell2008Multiscale) to the cleaning process of line cubes, with scales of \[0,5,15\]" (Data Calibration and Imaging)
- weighting robust: briggs, robust = 0.5  
  > "with `briggs` robust weighting of 0.5" (Data Calibration and Imaging)
- uv taper: _not stated_
- cell size: 1 arcsec  
  > "We uniformly set the image size of $108\times108$ pix$^2$ and cell size of 1$''$" (Data Calibration and Imaging)
- image size: 108 x 108 pix  
  > "We uniformly set the image size of $108\times108$ pix$^2$ and cell size of 1$''$" (Data Calibration and Imaging)
- masking: auto-multithresh (noisethreshold 5 sigma, sidelobethreshold 1.25 sigma); manual masks for some fields  
  > "Within the cleaning mask, we set the stopping `noisethreshold` to be 5$\sigma$ and `sidelobethreshold` to be $1.25\sigma$ in the dirty image/cube." (Data Calibration and Imaging); "For these fields, we performed a manual mask to further improve the imaging fidelity." (Data Calibration and Imaging)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, linear fit (order 1), line channels flagged  
  > "in the Fourier space using the task *uvcontsub* with linear fitting (polynomial order of 1)" (Data Calibration and Imaging)
- line free channels: model-spectrum mask shifted and expanded to a width of 50 km/s per source  
  > "For each source, the model spectrum was shifted and expanded with a width of 50 km s$^{-1}$ to ensure clean channels free from multiple velocity components and spectral line wings." (Data Calibration and Imaging)
- primary beam correction: pblimit = 0.2  
  > "The primary beam correction was performed with ` pblimit = 0.2`." (Data Calibration and Imaging)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: continuum rms per group in Table 1 column (9)  
  > "The noise rms of the cleaned continuum image is tabulated in column (9) of Table" (Data Calibration and Imaging)

### Inherited from earlier work

- Survey description and showcase of data combinations  
  > "The details of the survey description and the showcase of data combinations can be found in (cite: Liu2023QUARKS)." (Introduction) [from (cite: Liu2023QUARKS)]
- Basics of the main targeted lines  
  > "The basics of the main targeted lines are summarized in Table 2 of (cite: Liu2023QUARKS)." (Observing Strategy) [from (cite: Liu2023QUARKS) Table 2]
- Line identification and model-spectrum line-channel mask  
  > "(cite: Liu2023QUARKS) identified all the transitions of strong lines within the four SPWs by matching the reduced data cubes of the ALMA pipeline" (Data Calibration and Imaging) [from (cite: Liu2023QUARKS)]
- auto-multithresh input parameters  
  > "whose input parameters are recommended by the official guides [^2] for the ACA data" (Data Calibration and Imaging) [from casaguide:automask (CASA Automasking Guide)]
- Clump distances (updated with H13CO+ and rotation curve)  
  > "as listed in Table A. of (cite: Liu2023QUARKS)" (QUARKS Atlas) [from (cite: Liu2023QUARKS) Table A]
- H2CO triplet fitting approach (RADEX grid)  
  > "Following the method introduced in (cite: Ginsburg2016CMZTemp), we used RADEX (cite: van2007RADEX)" (Non-LTE Model Fitting of H2CO) [from (cite: Ginsburg2016CMZTemp)]
- Source angular size definition with eta = 2.4  
  > "Following (cite: Rosolowsky2010BGPSII) and (cite: Contreras2013ATLASGAL; Urquhart2014ATLASGAL), the source angular size can be calculated as the geometric mean of the deconvolved major and minor axes." (Physical Parameters of Sources) [from (cite: Rosolowsky2010BGPSII); (cite: Contreras2013ATLASGAL; Urquhart2014ATLASGAL)]
- Mass uncertainty terms for gas-to-dust ratio and opacity  
  > "We adopt the uncertainties derived by (cite: Sanhueza2017G28) of 28% for the gas-to-dust ratio and of 23% for the dust opacity" (Physical Parameters of Sources) [from (cite: Sanhueza2017G28)]
- Clump SED masses and dust temperatures  
  > "performed the photometry from near- to far-infrared data of these massive clumps, by which the spectral energy distribution (SED) are fitted" (Dense Gas Fraction and Its Assembly) [from (cite: Urquhart2018ATLASGAL)]

### Not stated but needed to reproduce (our reading)

- tclean niter, cleaning threshold, and the remaining auto-multithresh parameters (lownoisethreshold, negativethreshold, minbeamfrac etc.); only noisethreshold and sidelobethreshold are given
- Continuum deconvolver (hogbom vs multiscale) is not stated; multiscale is stated only for line cubes
- Which fields needed manual masks and the mask shapes
- Which channels per source form the continuum image (model-spectrum line mask lives in Liu2023QUARKS) and the continuum reference frequency
- Restoring beam per field and the beam used in the deconvolution of source sizes (sigma_bm)
- Full SExtractor configuration: detection threshold semantics, filter, background box and rms map values, SNR cut that defines the 207-source catalog (SNR > 9 is mentioned as 'solid' only for the example)
- Spectral extraction aperture/region for the source-averaged H2CO spectra, pyspeckit initial guesses, parameter bounds, fitter and error estimation
- Ortho/para and background (CMB) settings in RADEX
- Number of Monte Carlo draws and the input distributions for the mass uncertainties
- Regression method (OLS vs orthogonal, weights, treatment of unresolved sources and upper limits) for the M-R, mass-correlation and DGF fits
- How L/M for each clump is obtained (taken from Urquhart2018ATLASGAL but not listed); clump distances, masses and temperatures are needed from outside tables
- Which ALMA project supplies the ASHES comparison images and what 2019.1.00685.S covers
- Observed velocity dispersion sigma_obs measurement from the fitted FWHM, and how the 30 outflow-wing sources are treated beyond the fixed 1.66 km/s

## Analysis recipe

1. **Calibrate and image ACA continuum and line data**: ALMA pipeline calibration, line-channel flagging with a model-spectrum mask, uvcontsub, then tclean with auto-multithresh  
  > "The data were routinely calibrated using the ALMA pipelines" (Data Calibration and Imaging); "The continuum and line cube imaging processes were performed by the task *tclean* in CASA 6.5.6, with `briggs` robust weighting of 0.5." (Data Calibration and Imaging)
   - software: CASA, tclean, uvcontsub, auto-multithresh
   - parameter: uvcontsub linear fit (order 1); line channels flagged using model spectrum widened to 50 km/s  
  > "in the Fourier space using the task *uvcontsub* with linear fitting (polynomial order of 1)" (Data Calibration and Imaging); "For each source, the model spectrum was shifted and expanded with a width of 50 km s$^{-1}$ to ensure clean channels free from multiple velocity components and spectral line wings." (Data Calibration and Imaging)
   - parameter: briggs robust 0.5; noisethreshold 5 sigma; sidelobethreshold 1.25 sigma; line cubes multiscale [0,5,15]; pblimit 0.2; image 108x108 pix, 1 arcsec cell  
  > "Within the cleaning mask, we set the stopping `noisethreshold` to be 5$\sigma$ and `sidelobethreshold` to be $1.25\sigma$ in the dirty image/cube." (Data Calibration and Imaging); "We uniformly set the image size of $108\times108$ pix$^2$ and cell size of 1$''$" (Data Calibration and Imaging)
   - parameter: edge channels (~2x128 per SPW) flagged in the first data release; no self-calibration  
  > "The edge channels of each spectral window ($\sim2\times128$) were flagged in the first version of data release" (Data Calibration and Imaging); "self-calibration has not been performed on our released ACA data" (Data Calibration and Imaging)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract 1.3 mm continuum sources and measure fluxes**: SExtractor on background-subtracted unpbcor continuum map with local rms map; fluxes divided by the primary beam response at barycenter/peak  
  > "We adopted an automatic source extraction algorithm SEXTRACTOR [^3] (cite: Bertin1996SExtractor) on the ACA 1.3 mm continuum emission maps to extract the 1.3 mm continuum sources." (ACA 1.3 mm Continuum Source Catalog); "the `pb` map is interpolated to the barycenter and at the intensity peak of the source, by which the measured integrated flux and peak intensity are divided, respectively." (Source Extraction)
   - software: SExtractor
   - parameter: background clipping at 3 sigma in boxes equal to the maximum recoverable scale  
  > "Within each unit of boxes, whose size is equivalent to the maximum recoverable scale, we performed iterative clipping of the local background histogram until convergence was achieved at $\pm3\sigma$ around its median" (Source Extraction)
   - parameter: nthresh = 4 (times local rms)  
  > "Before the program runs, $\texttt{nthresh}=4$ is set to mask the low SNR (`nthresh`$\times$local rms) pixels." (Source Extraction)
   - parameter: deblend_nthresh = 512, deblend_cont = 1e-5, minarea = effective beam size  
  > "are set $\texttt{deblend\_nthresh}=512$ and $\texttt{deblend\_cont}=10^{-5}$" (Source Extraction); "we set the parameter controlling the minimum pixel count for a source, `minarea`, to match the effective beam size." (Source Extraction)
   - assumption: missing flux ignored because maximum observed source size (~14 arcsec) is about half the MRS  
  > "We thus ignore the effects of missing flux in the following analyses." (ACA 1.3 mm Continuum Source Catalog)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit p-H2CO triplet for kinetic temperature and line width**: five-parameter pyspeckit model on source-averaged SPW1 spectra, using a pre-computed RADEX non-LTE grid  
  > "perform a five-parameter model using the formaldehyde official model[^4] by PYSPECKIT (cite: Ginsburg2011Pyspeckit; Ginsburg2022Pyspeckit) with a non-LTE RADEX model." (Temperature Estimation from Formaldehyde); "Three source-averaged formaldehyde transition lines p-H$_2$CO (3–2) are fitted using non-LTE radiative transfer model, to obtain the gas kinetic temperature and line width." (Summary)
   - software: PySpecKit, RADEX
   - parameter: free parameters: Tkin, log N(H2CO), log n(H2), v_lsr, FWHM; single velocity component  
  > "The five parameters are kinetic temperature ($T_{\rm kin}$), formaldehyde column density ($\log N(\rm H_2CO)$), hydrogen molecule volume density ($\log n(\rm H_2)$), centroid velocity ($v_{\rm lsr}$) and line width (FWHM)." (Non-LTE Model Fitting of H2CO); "For all the sources, only one velocity component is considered." (Non-LTE Model Fitting of H2CO)
   - parameter: RADEX grid with line gradient fixed at 5 km/s/pc and Wiesenfeld & Faure collision rates  
  > "with a fixed assumed line gradient of 5 km s$^{-1}$ pc$^{-1}$" (Non-LTE Model Fitting of H2CO); "the collision rates were taken from (cite: Wiesenfeld2013H2CO)" (Non-LTE Model Fitting of H2CO)
   - parameter: failed fits (seven spectra) assigned the clump-averaged dust temperature  
  > "If the fitting fails (for seven spectra), then the $T_{\rm kin}$ is set to be equal to clump-averaged dust temperature $T_{\rm dust,clump}$" (Non-LTE Model Fitting of H2CO)
   - fitting: least-squares line fitting on the pre-built RADEX grid; priors and likelihood not stated  
  > "Based on the preconstructed non-LTE model grids, the line fitting is performed." (Non-LTE Model Fitting of H2CO); "For example, line wings can make least-square method fall into a false local minimum." (Caveats)
   - validation: compared RADEX-derived H2 density with dust-derived density (bulk trend, RADEX systematically higher); Tkin lies above clump dust temperature for all sources  
  > "The data points follow a bulk increasing trend although with a large dispersion, further justifying the self-consistency of the temperature estimation." (Validation); "All the data points lie above the “isothermal line”" (Temperature Estimation from Formaldehyde)
4. **Derive source mass, size, densities, turbulence and Mach number**: optically thin single-temperature dust mass formula, deconvolved size, N_H2, surface and volume density, thermal and non-thermal velocity dispersions, 3D Mach number  
  > "Assuming that all the emission comes from dust in a single component with $T_{\rm dust}$ and that the dust emission is optically thin, the masses of the sources can be calculated using" (Physical Parameters of Sources); "The three-dimensional (3D) Mach number is defined as," (Physical Parameters of Sources)
   - parameter: gas-to-dust ratio 100  
  > "$\mathcal{R}$ is the gas-to-dust mass ratio (assumed to be 100)" (Physical Parameters of Sources)
   - parameter: kappa = 1 cm2/g at ~230 GHz (Ossenkopf & Henning 1994, thin ice mantles)  
  > "$\kappa_{\nu}$ is assumed to be 1 cm$^2$ g$^{-1}$ at $\nu\sim230$ GHz which is interpolated from the given table in (cite: O&H1994dust)" (Physical Parameters of Sources)
   - parameter: eta = 2.4 for deconvolved size  
  > "$\eta=2.4$, the median value derived for a range of models consisting of a spherical emissivity distribution (cite: Rosolowsky2010BGPSII), is adopted here." (Physical Parameters of Sources)
   - parameter: mu_H2 = 2.81; mu_p = 2.37; channel width 1.34 km/s; m_H2CO = 30 m_H  
  > "Throughout the paper, we adopt the molecular weight per hydrogen molecule $\mu_{\scriptscriptstyle\rm H_2} = 2.81$ (cite: Evans2022SlowSF)." (Physical Parameters of Sources); "where $\mu_{p}=2.37$ for a mean molecular weight per free particle (cite: Kauffmann2008dust)" (Physical Parameters of Sources); "where $\Delta_{\rm chan}=1.34$ km s$^{-1}$ is the channel width." (Physical Parameters of Sources)
   - parameter: 30 sources with line width > 7 km/s (outflow wings) assigned an averaged observed velocity dispersion of 1.66 km/s  
  > "We check that 30 sources with line width $>7$ km s$^{-1}$ are strongly influenced by outflow wings" (Physical Parameters of Sources); "and set an averaged observed velocity dispersion of $1.66$ km s$^{-1}$." (Physical Parameters of Sources)
   - assumption: dust temperature of each ACA source equals the H2CO kinetic temperature  
  > "we assume that the dust temperature of ACA source/fragment ($T_{\rm dust,frag}$) equals to the kinetic temperature derived from H$_2$CO triplet line fitting ($T_{\rm kin,H_2CO}$)." (Temperature Estimation from Formaldehyde)
   - assumption: distance uncertainty 20% and flux calibration uncertainty 10% included in mass errors  
  > "the uncertainty of distance (assumed to be 20%) are included" (Physical Parameters of Sources)
   - fitting: Monte Carlo propagation of uncertainties, 1 sigma intervals  
  > "Monte Carlo methods are adopted for uncertainty estimation and $1\sigma$ confidence intervals are given." (Physical Parameters of Sources)
   - validation: _not stated_
5. **Fit mass-radius and clump-fragment mass relations**: linear regression in log space of M-R for clumps and fragments, and of Msource,max and Msource,total against Mclump  
  > "We perform a linear regression on the $M$–$R$ diagram for the QUARKS clumps" (Fragments with self-similar gravitational collapse); "Linear regression is used to correlate $M_{\rm source,max}$ with $M_{\rm clump}$." (Correlation Between Clumps and Fragments)
   - parameter: distance bins for robustness: <=3 kpc, 3-6 kpc, >6 kpc  
  > "$d\leq3$ kpc (Near), $3<d\leq6$ kpc (Mid), and $d>6$ kpc (Far)" (Distance Effects on Mass Correlation)
   - assumption: clump masses from SED fitting scaled to the updated distances  
  > "were derived and are scaled with the updated distances in this work" (Dense Gas Fraction and Its Assembly)
   - fitting: ordinary linear regression (method details not stated); correlation coefficient and 1 sigma scatter reported  
  > "with the correlation coefficient of 0.82 and 1$\sigma$ data scatter of 0.34 dex" (Correlation Between Clumps and Fragments)
   - validation: repeated regression in three distance bins gives similar quasi-linear correlations  
  > "We perform linear regression on the three groups individually and obtain similar quasi-linear correlations as observed in the total sample." (Distance Effects on Mass Correlation)
6. **Compute dense gas fraction and its dependence on size and L/M**: DGF = summed ACA source mass in a clump / clump mass; compared against clump radius and L/M with a QUARKS plus ASHES combined sample  
  > "where $M_{\rm dense}=\sum\limits^{\rm \in clump} M_{\rm source}$ is the total ACA source mass within the clump." (Dense Gas Fraction and Its Assembly); "After adopting the same source extraction algorithm and mass calculation, we derive the DGF of 39 ASHES clumps" (Self-similarity in protocluster formation)
   - parameter: ASHES continuum images cropped to the QUARKS field size  
  > "To maintain consistency, we cropped the ASHES continuum images to the same size as the QUARKS." (Self-similarity in protocluster formation)
   - parameter: linear regression on combined sample in log(DGF) vs log(L/M)  
  > "a linear regression is performed on the data points from the combined sample" (Dense gas grows with evolution)
   - assumption: L/M indicates evolutionary stage  
  > "The ratio of bolometric luminosity to envelope mass $L/M$, can thus be used to indicate the evolutionary stage" (Dense gas grows with evolution)
   - fitting: linear regression with Spearman coefficient and p value (method details not stated)  
  > "The correlation yields a Spearman correlation coefficient of $R_s=0.41$ and an associated $p$ value of $2.9\times10^{-8}$" (Dense gas grows with evolution)
   - validation: independent Csengeri2017 and SQUALO data show a similar increasing trend  
  > "As a result, two independent data sets mutually verify a dense mass growth in massive star-forming clumps as they evolve." (Dense gas grows with evolution)
7. **Cross-match ACA sources with ATOMS 3 mm dense cores**: elliptical mask from each ACA source geometry; an ATOMS core inside it defines a QUARKS-ATOMS link, with a fidelity value  
  > "Elliptical mask is defined by the geometrical measurement of the ACA 1.3 mm continuum source" (QUARKS-ATOMS Link); "The link fidelity, defined as how close the ATOMS source is to the QUARKS source, with values from 0 (unreliable) to 1 (reliable)" (QUARKS-ATOMS Link)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.2.1 and 6.4.1 (pipeline); 6.5.6 (imaging): ALMA pipeline calibration and imaging  
  > "The data were routinely calibrated using the ALMA pipelines" (Data Calibration and Imaging); "in the corresponding versions of 6.2.1 and 6.4.1" (Data Calibration and Imaging)
- **tclean** CASA 6.5.6: continuum and line cube imaging  
  > "The continuum and line cube imaging processes were performed by the task *tclean* in CASA 6.5.6" (Data Calibration and Imaging)
- **uvcontsub** : continuum subtraction in the uv plane after line-channel flagging  
  > "in the Fourier space using the task *uvcontsub* with linear fitting (polynomial order of 1)" (Data Calibration and Imaging)
- **auto-multithresh** : automatic cleaning masks  
  > "the images/cubes were automatically masked by `auto-multithresh` algorithm" (Data Calibration and Imaging)
- **SExtractor** : source extraction on ACA 1.3 mm continuum maps  
  > "We adopted an automatic source extraction algorithm SEXTRACTOR [^3] (cite: Bertin1996SExtractor) on the ACA 1.3 mm continuum emission maps to extract the 1.3 mm continuum sources." (ACA 1.3 mm Continuum Source Catalog)
- **PySpecKit** : fitting the p-H2CO triplet  
  > "perform a five-parameter model using the formaldehyde official model[^4] by PYSPECKIT" (Temperature Estimation from Formaldehyde)
- **RADEX** : non-LTE model grids for p-H2CO  
  > "we used RADEX (cite: van2007RADEX) to create model grids for the p-H$_2$CO molecular lines" (Non-LTE Model Fitting of H2CO)
- **Astropy** : named in the software statement; specific use not stated  
  > "This research uses ASTROPY, a community-developed core Python package for Astronomy" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of ACA 1.3 mm continuum sources | 207 | not stated | count | 2 | a total of 207 ACA 1.3 mm continuum sources are extracted from the 139 massive star-forming clumps |
| Sources per clump | 1 to 5 | not stated | count | 2 | At least one and at most five sources have been detected in one clump. |
| Maximum observed angular size of ACA sources | ~14 | not stated | arcsec | 2 | We note that the maximum observed angular size (convolved with the beam) of ACA sources is $\sim14\ensuremath{''}$, which is only half of the maximum recoverable scale in most cases |
| H2CO kinetic temperature range and median (Section 4.2) | 24 to 180 K, median 72 K | not stated | K | 3 | The derived kinetic temperatures have values between 24 to 180 K with median of 72 K |
| H2CO kinetic temperature mean and median (Section 5.1.1) | ~68 | not stated | K | 3 | In panel (a), $T_{\rm kin}$ ranges from $\sim20$ to $\sim180$ K, with a mean and median of $\sim$68 K. |
| Fraction of sources with Tkin above 30 K | >97% | not stated | percent | 3 | More than 97% sources have a temperature larger than 30 K |
| Number of failed H2CO fits | 7 (6 self-absorbed, 1 weak) | not stated | count | 3 | seven sources with failed fitting (six with a strong self-absorption line profile and one with a weak detection) |
| Tkin of example source I13291-6229_ACA2 (Figure 8) | 53 | +/-11 | K | 3 | where $T_{\rm kin}$ is estimated to be 53($\pm11$) K |
| Source mass 16th and 84th percentiles | 6 and 160 | not stated | Msun | 4 | with 16 and 84 percentile values of 6 and 160 $M_\odot$ |
| Sources with mass > 8 Msun | 120 (58%) | not stated | count | 4 | 120 ACA sources (58%) are massive enough to form a massive star ($>8$ $M_\odot$) |
| Sources able to form massive stars with Larson cluster relation | 72 of 207 | not stated | count | 4 | we find that 72 out of 207 sources can form massive stars if only mass *in situ* participates in star formation |
| Sources with surface density > 1 g/cm2 | 35 | not stated | count | 4 | A total of 35 ACA sources exceed the more stringent surface density threshold of 1 g cm$^{-2}$ |
| Source size range (R_dec) | 0.02 to 0.4 | not stated | pc | 4 | the ACA sources exhibit sizes ranging from 0.02 to 0.4 pc |
| Median volume density of ACA sources | 1.6e5 | not stated | cm^-3 | 4 | The median volume density of the ACA sources is $1.6\times10^5$ cm$^{-3}$, which is 20 times larger than that of the clumps. |
| Sources with volume density above 1e5 cm^-3 | 107 | not stated | count | 4 | with 107 of them surpassing $10^5$ cm$^{-3}$ |
| M-R power-law index for QUARKS clumps (correlation coefficient 0.91, scatter 0.26) | 1.8 | not stated | dimensionless | 5 | a correlation of $M\propto R^{1.8}$ (shown as orange line) with correlation coefficient of 0.91 and $1\sigma$ data scatter of 0.26 |
| M-R power-law index for ACA fragments | 1.1 | not stated | dimensionless | 5 | A linear regression applied to the ACA fragments reveals a correlation of $M\propto R^{1.1}$ |
| log(Msource,max/Msun) vs log(Mclump/Msun): slope 0.96, intercept -1.33, r 0.82 | slope 0.96, intercept -1.33 | 1 sigma scatter 0.34 dex | dimensionless | 5 | The derived scaling relation is $\log (M_{\rm source,max}/M_{\odot}) = 0.96 (\log M_{\rm clump}/M_{\odot}) - 1.33$; with the correlation coefficient of 0.82 and 1$\sigma$ data scatter of 0.34 dex |
| log(Msource,total/Msun) vs log(Mclump/Msun): slope 0.94, intercept -1.22, r 0.85 | slope 0.94, intercept -1.22 | 1 sigma scatter 0.30 dex | dimensionless | 5 | linear regression gives $\log (M_{\rm source,total}/M_\odot) = 0.94 (\log M_{\rm clump}/M_{\odot}) - 1.22$; Intriguingly, the correlation is even tighter with coefficient of 0.85 and 1$\sigma$ data scatter of 0.30 dex |
| Correlation coefficients in three distance bins | 0.72 to 0.74 (scatter 0.25 to 0.35) | not stated | dimensionless | 5 | The correlation coefficients for the three fittings are substantial, ranging from 0.72 to 0.74, and the $1\sigma$ scatters fall between 0.25 and 0.35. |
| Dense gas fraction (DGF) | 6% (intercept 10^-1.22) | scatter 1-10% | percent | 6 | giving a value directly by its intercept of $10^{-1.22}$, i.e., 6%; Although showing invariance with $M_{\rm clump}$, DGF still has a scatter of 1–10%. |
| Spearman coefficient DGF vs clump radius | -0.12 | not stated | dimensionless | 6 | Linear regression shows a weak correlation with a Spearman correlation coefficient of -0.12 |
| log(DGF) vs log(L/M) fit (QUARKS+ASHES): slope 0.13, intercept -1.59 | slope 0.13, intercept -1.59; Rs = 0.41, p = 2.9e-8 | not stated | dimensionless | 6 | a correlation of $\log({\rm DGF}) = 0.13\log{(L/M)}-1.59$; The correlation yields a Spearman correlation coefficient of $R_s=0.41$ and an associated $p$ value of $2.9\times10^{-8}$ |
| Number of QUARKS-ATOMS links | 301 | not stated | count | 7 | we have identified a total of 301 |
| ATOMS field sources without an ACA counterpart | 128 | not stated | count | 7 | The remaining 128 ATOMS dense cores, without any associated ACA sources, are referred to as |
| ACA sources containing more than one ATOMS core | 86 (42%); 25 with three or more | not stated | count | 7 | There are 86 ACA sources (42%) with more than one ATOMS dense cores, and among them, 25 have three or more ATOMS dense cores |
| ACA sources associated with a single ATOMS core | 95 | not stated | count | 7 | there are 95 ACA sources associated with single ATOMS dense cores |
| Mean number of fragments per clump | ~1.5 (93 clumps with one fragment) | not stated | count | 2 | The facts that the mean number of fragments per clump is $\bar N_{\rm frag}\sim1.5$ and that 93 clumps have only one fragment |

## Qualitative findings

- ACA sources are massive, gravity-dominated subclump fragments with supersonic turbulence and possibly embedded protoclusters  
  > "Statistically speaking, the nature of ACA sources is massive gravity-dominated fragments with at the subclump scale, with supersonic turbulence and possibly embedded star-forming protocluster." (Summary)
- H2CO temperatures of ACA sources exceed clump-averaged dust temperatures, implying an outward negative temperature gradient  
  > "This suggests an outward negative temperature gradient, with the inner dense gas traced by H$_2$CO being warmer than the surrounding low-density gas and warmer than gas on average." (Temperature Estimation from Formaldehyde)
- Quasi-linear clump-fragment mass correlation interpreted as clump-core coevolution in late stages  
  > "A quasi-linear correlation between clump mass and ACA source mass is found, which can be explained by the dynamic coevolution between clump and core in a late stage." (Summary)
- DGF increases with L/M across four orders of magnitude  
  > "With the data across four orders of magnitude of luminosity-to-mass ratio, we find a significantly increasing trend of DGF with clump evolution." (Summary)
- Fragmentation at the subclump scale is limited, possibly due to global clump collapse  
  > "The fragmentation on the subclump scale is limited and the reasons could be that equilibrium may never be reached at subclump scale and massive clumps are undergoing a global collapse." (Summary)

## Claim tuples

- H: Are ACA 1.3 mm continuum sources condensed, gravity-dominated fragments of massive clumps? | E: Derived Tkin from H2CO, masses, sizes, densities, Mach numbers for 207 ACA sources and compared with clumps | R: Median density 1.6e5 cm^-3 (20x the clumps), sizes 0.02-0.4 pc, Mach numbers mostly > 2, Tkin above clump dust T | F: ACA sources are subclump fragments (dense, turbulent, possibly protocluster ensembles) | **supported**
- H: Does the mass of the most massive fragment (or total fragment mass) correlate with clump mass? | E: Linear regression of log Msource,max and log Msource,total against log Mclump, plus distance-bin tests | R: Slopes 0.96 and 0.94, r = 0.82 and 0.85, scatter 0.34 and 0.30 dex | F: Quasi-linear clump-fragment mass correlation; total dense mass is the more direct correlate | **supported**
- H: Is the mass-radius relation of fragments consistent with self-similar gravitational collapse (rho ~ R^-2)? | E: Linear regression of M-R for clumps and for ACA fragments | R: Clumps M ~ R^1.8; fragments M ~ R^1.1 | F: Fragments show a shallower M-R relation consistent with scale-free, self-similar collapse | **partially**
- H: Is the dense gas fraction size-invariant, indicating self-similar fragmentation, and does it grow with evolution? | E: DGF vs clump radius and vs L/M for QUARKS, ASHES, Csengeri2017 and SQUALO clumps | R: DGF ~6% (1-10%); Spearman -0.12 vs radius; log(DGF) = 0.13 log(L/M) - 1.59, Rs 0.41, p 2.9e-8 | F: DGF is size-invariant but increases with L/M | **supported**
- H: Is fragmentation at the subclump scale limited? | E: Counted fragments per clump and cross-matched with ATOMS 3 mm cores | R: mean 1.5 fragments per clump, 93 clumps with one; 86 sources contain more than one ATOMS core | F: Limited fragmentation at the ACA scale, attributed to resolution/sensitivity and global clump collapse (partly speculative) | **partially**

## Reasoning

- Why this data: ACA 1.3 mm continuum has little free-free contamination and a large recoverable scale, suited to dense gas in massive clumps  
  > "With relatively little free-free emission contamination and a maximum recoverable scale as large as $\sim27$$''$, ACA 1.3 mm continuum data are useful for tracking dense molecular gas within massive clumps." (Introduction)
- Why this method: SExtractor handles background, local rms thresholds and deblending; p-H2CO minimizes optical depth uncertainties for temperature  
  > "The advantages of SEXTRACTOR in our case are: 1) to subtract the background diffuse emission and rms noise automatically;" (ACA 1.3 mm Continuum Source Catalog); "Therefore, temperature estimation from p-H$_2$CO transition lines minimizes the uncertainties from a high optical depth." (Temperature Estimation from Formaldehyde)
- Alternative: Self-calibration was not applied because it would not contribute much to the science goals  
  > "Self-calibration can improve the sensitivity, but will not contribute much to the science goals in this paper." (Data Calibration and Imaging)
- Alternative: Missing flux from extended emission was ignored  
  > "We thus ignore the effects of missing flux in the following analyses." (ACA 1.3 mm Continuum Source Catalog)
- How they decided it was enough: _not stated_
- Limitation (authors): Limited mass sensitivity (>~3 Msun) and spatial resolution (>~0.1 pc) cannot resolve small low-mass fragments  
  > "the QUARKS ACA observations have limited mass sensitivity of $\gtrsim3$ $M_\odot$, at a temperature of 20 K and distance of 4 kpc and limited spatial resolution of $\gtrsim0.1$ pc." (Limited Fragmentation)
- Limitation (authors): H2CO temperature fidelity depends on H2CO tracing dense core gas, which may fail (outflow-dominated emission)  
  > "The temperature estimation using the H$_2$CO triplet assumes that the H$_2$CO emission mainly traces dense gas, which is not the case in a sample of 12 infrared dark clouds" (Caveats)
- Limitation (authors): Multiple velocity components overestimate line width; line wings and self-absorption disturb the fit  
  > "If more than one velocity component is associated with an ACA source, the line width will be overestimated." (Caveats)
- Limitation (authors): QUARKS fields may not cover all dense gas in large clumps (very low DGF)  
  > "indicating that QUARKS field of views are not large enough to cover all the dense gas in clumps with large sizes" (Self-similarity in protocluster formation)
- Caveat (inferred, ours): Internal inconsistency: the Figure 8 example gives Tkin = 53(+/-11) K for I13291-6229_ACA2 while the sample table lists 74.8(1.4) K for the same source; Section 4.2 gives median 72 K, Section 5.1.1 gives mean and median ~68 K
- Caveat (inferred, ours): Dust temperature set equal to H2CO Tkin from source-averaged ACA-resolution spectra; Tkin errors in the table look very small compared with the +/-11 K of the example
- Caveat (inferred, ours): Clump and fragment masses both scale as d^2 with the same adopted distance, which can induce a correlation; only checked with three distance bins
- Caveat (inferred, ours): Clump masses from ATLASGAL SED fitting at much coarser resolution than the ACA data; DGF depends on the clump mass definition and field coverage (ATOMS-biased pointings)
- Caveat (inferred, ours): Regression method and error treatment (OLS vs orthogonal, selection effects from sensitivity limits, unresolved sources) are not specified; no slope uncertainties given
- Caveat (inferred, ours): DGF-L/M trend mixes samples with different temperature assumptions and different cropping; statistical weight of the 0.13 slope is modest (Rs = 0.41)
- Caveat (inferred, ours): Interpretation of M ~ R^1.1 as self-similar collapse is qualitative and not tested against alternative profiles

## Reproducibility

- Data public (paper): Public availability of the ALMA data is not explicitly stated; the paper refers to its 'released ACA data' and provides catalog tables in machine-readable form  
  > "self-calibration has not been performed on our released ACA data" (Data Calibration and Imaging); "The table is available in its entirety in machine-readable form." (Table 2)
- Products in archive: _not stated_
- Missing: Liu2023QUARKS Table A distances and the model-spectrum line mask
- Missing: Urquhart2018ATLASGAL clump masses, temperatures and L/M values
- Missing: Complete tclean/auto-multithresh parameters and manual masks
- Missing: SExtractor configuration and the catalog SNR cut
- Missing: pyspeckit fit settings (initial guesses, bounds, aperture)
- Missing: ASHES comparison data identification and processing
- Missing: Regression/Monte Carlo implementation details
- Data volume (inferred): 15 ACA scheduling blocks (1-3 EBs each) in 4 x 2 GHz x 4096 channel setup; raw MS likely tens to a few hundred GB in total, plus several GB of per-field cubes
- Score (inferred): 3/5, Project codes, imaging parameters, SExtractor settings, mass formulae and many numeric results are given, but clump masses, distances, line masks, several tclean parameters and fit/regression details are inherited or missing, and the catalog depends on external tables.
- Rediscovery candidate: yes, ALMA ACA data under stated project codes are archive data, imaging and extraction recipe is largely explicit, and key results are numeric (207 sources, DGF 6%, regression coefficients), though external clump tables are needed.

## Links

- Method: (cite: Liu2023QUARKS) (QUARKS survey description, data combinations, line list, distances and clump masses)
- Method: (cite: Ginsburg2016CMZTemp) (RADEX-grid p-H2CO temperature fitting method)
- Method: (cite: Bertin1996SExtractor) (SExtractor source extraction)
- Method: (cite: Rosolowsky2010BGPSII) (deconvolved source size definition with eta = 2.4)
- Method: (cite: Sanhueza2017G28) (mass uncertainty terms for gas-to-dust ratio and opacity)
- Companion: (cite: Liu2020ATOMS-I) (ATOMS survey that QUARKS follows up)
- Companion: (cite: Liu2021ATOMS-III) (ATOMS dense core catalog used for the cross-match)
- Companion: (cite: Xu2024ASSEMBLE) (high-resolution clump-core mass correlation in 11 protoclusters)
- Companion: (cite: Urquhart2018ATLASGAL) (clump masses, temperatures and L/M)
- Companion: (cite: Morii2023ASHES) (ASHES early-stage clumps used as comparison)
- Companion: (cite: Traficante2023SQUALO-I) (SQUALO ACA survey with comparable mass correlation and DGF)
- Related: QUARKS
- Related: ATOMS
- Related: ASHES
- Related: ATLASGAL
- Related: SQUALO
- Related: ALMA-IMF
- Related: Hi-GAL
- Related: GLIMPSE
- Related: MeerKAT Galactic Plane Survey

## Checks

```json
{
 "quotes": 200,
 "quotes_ok": 200,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 28,
 "numeric_problems": 0,
 "fill": {
  "facts": 135,
  "stated": 114,
  "rate": 0.844
 },
 "evidence_ok": true
}
```
