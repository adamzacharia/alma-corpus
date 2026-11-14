# Star formation scaling relations at ∼100 pc from PHANGS: Impact of completeness and spatial scale

`2021A&A...650A.134P` | Astronomy and Astrophysics 2021 | first author: Pessa, I. | arXiv: 2104.09536 | DOI: 10.1051/0004-6361/202140733

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: nearby_galaxies, star_formation
- Question: Do the resolved star formation main sequence, resolved Kennicutt-Schmidt relation and resolved molecular gas main sequence exist at 100 pc to 1 kpc in PHANGS galaxies, and how do their slope and scatter depend on environment, spatial scale and the treatment of non-detections  
  > "In this paper we aim to probe these scaling relations to understand the mechanisms that locally regulate star formation, using ${\sim}100$ pc spatial resolution data from the PHANGS survey." (1 Introduction)
- Target **18 PHANGS star-forming galaxies (NGC 1087, NGC 1300, NGC 1365, NGC 1385, NGC 1433, NGC 1512, NGC 1566, NGC 1672, NGC 2835, NGC 3351, NGC 3627, NGC 4254, NGC 4303, NGC 4321, NGC 4535, NGC 5068, NGC 7496, IC 5332)**: coordinates per-galaxy RA/DEC in degrees given in the sample table  
  > "We use a sample of $18$ star-forming galaxies, all of them are close to the SFMS of galaxies." (2 Data); "we use the global parameters as reported by (cite: Leroy2021b) based on the distance compilation of (cite: Anand2021) as well as the inclinations determined by (cite: Lang2020)" (2 Data); z/distance 5.2 to 19.57 Mpc (per-galaxy values in the sample table)  
  > "We use a sample of $18$ star-forming galaxies, all of them are close to the SFMS of galaxies." (2 Data); "we use the global parameters as reported by (cite: Leroy2021b) based on the distance compilation of (cite: Anand2021) as well as the inclinations determined by (cite: Lang2020)" (2 Data); distance from distance compilation of Anand et al. 2021 as reported by Leroy et al. 2021b; inclinations from Lang et al. 2020  
  > "We use a sample of $18$ star-forming galaxies, all of them are close to the SFMS of galaxies." (2 Data); "we use the global parameters as reported by (cite: Leroy2021b) based on the distance compilation of (cite: Anand2021) as well as the inclinations determined by (cite: Lang2020)" (2 Data)

## Data provenance

- ALMA projects: 2013.1.01161.S, 2015.1.00925.S, 2015.1.00956.S, 2017.1.00886.L
- bands: _not stated_
- frequencies and spectral setup: CO(2-1)  
  > "The $18$ galaxies have CO(2–1) data from the PHANGS-ALMA Large Program" (2.2 ALMA)
- continuum bandwidth: _not stated_
- arrays: ALMA 12m and 7m arrays combined with total power antennas  
  > "We used the ALMA $12$m and $7$m arrays combined with the total power antennas to map CO emission" (2.2 ALMA)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.0'' - 1.5''  
  > "to map CO emission at a spatial resolution of $1.0\ensuremath{''} {-} 1.5\ensuremath{''}$" (2.2 ALMA)
- max recoverable scale: sensitive to emission at all spatial scales (ACA 7m and total power included)  
  > "The inclusion of the Atacama Compact Array (ACA) $7$m and total power data means that these maps are sensitive to emission at all spatial scales." (2.2 ALMA)
- sensitivity: rms noise ~0.1 K per 2.5 km/s channel  
  > "The CO data cubes have an rms noise of ${\sim}0.1$ K per $2.5$ km s$^{-1}$ channel" (2.2 ALMA)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PHANGS-ALMA Large Program; MUSE target selection used galaxies with ALMA data from the ALMA pilot project or the ALMA archive  
  > "The $18$ galaxies have CO(2–1) data from the PHANGS-ALMA Large Program" (2.2 ALMA); "The target selection for the PHANGS-MUSE sample focused on galaxies from the PHANGS parent sample that had already available ALMA data, as part of the ALMA pilot project, or from the ALMA archival." (2.1 VLT/MUSE)
- Line: CO J=2-1 (not stated)
- Other facility **VLT/MUSE (PHANGS-MUSE survey)**: Optical IFU mosaics used for stellar mass (SSP fitting) and Halpha/Hbeta emission-line maps for SFR  
  > "We make use of the PHANGS-MUSE survey (PI: E. Schinnerer; Emsellem et al. in prep.)." (2.1 VLT/MUSE); "The total on-source exposure time per pointing for galaxies in the PHANGS-MUSE Large Program is $43$ min." (2.1 VLT/MUSE)
- Other facility **Spitzer Survey of Stellar structure in Galaxies (S4G)**: Photometric data used to build the environmental masks  
  > "This classification was done using photometric data mostly from the Spitzer Survey of Stellar structure in Galaxies (cite: Sheth2010)." (2.3 Environmental masks)
- External data: Global galaxy parameters and distances (Leroy et al. 2021b; Anand et al. 2021) and inclinations (Lang et al. 2020)  
  > "we use the global parameters as reported by (cite: Leroy2021b) based on the distance compilation of (cite: Anand2021) as well as the inclinations determined by (cite: Lang2020)" (2 Data) [from (cite: Leroy2021b); (cite: Anand2021); (cite: Lang2020)]
- External data: PHANGS-ALMA CO(2-1) broad-mask integrated intensity maps  
  > "For our analysis we use the integrated intensity maps from the broad masking scheme" (2.2 ALMA); "The strategy for observing, data reduction and product generation are described in (cite: Leroy2021a)." (2.2 ALMA) [from (cite: Leroy2021a)]
- External data: Environmental masks (disk, spiral arms, rings, bars, centers)  
  > "We have used the environmental masks described in (cite: Querejeta2021) to morphologically classify the different environments of each galaxy" (2.3 Environmental masks) [from (cite: Querejeta2021)]
- External data: Radially varying gas-phase metallicity profile used in the alpha_CO prescription  
  > "The radially-varying metallicity is estimated from the radial profile of gas-phase abundances" (2.2 ALMA) [from (cite: Kreckel2020)]
- External data: Offset from the global star formation main sequence (Delta MS) of each galaxy  
  > "vertical offset of the galaxy from the global star formation main sequence of galaxies ($\Delta$MS) as computed in (cite: Leroy2019)" (4.2 Scaling relations in individual galaxies) [from (cite: Leroy2019)]
- External data: HII region catalog used for the strict HII-region masking test  
  > "region catalog from F. Santoro et al. (in prep.)" (5.4.1 Role of diffuse gas emission) [from F. Santoro et al. (in prep.)]

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
- masking: integrated intensity maps from the broad masking scheme  
  > "For our analysis we use the integrated intensity maps from the broad masking scheme, which are optimized for completeness" (2.2 ALMA)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12m + 7m (ACA) + total power  
  > "We used the ALMA $12$m and $7$m arrays combined with the total power antennas to map CO emission" (2.2 ALMA)
- smoothing: resampling into larger pixels only, no convolution before resampling  
  > "The degrading of the data to larger spatial scales is done by only resampling into larger pixel, rather than performing a convolution before resampling." (3.1 Sampling the data at larger spatial scales)
- final beam: 1.0'' - 1.5'' CO resolution; maps then resampled to 100 pc, 500 pc and 1 kpc pixels  
  > "to map CO emission at a spatial resolution of $1.0\ensuremath{''} {-} 1.5\ensuremath{''}$" (2.2 ALMA)
- final rms: ~0.1 K per 2.5 km/s channel (1 sigma(Sigma_mol.gas) ~ 2 Msun pc^-2 per 5 km/s)  
  > "The CO data cubes have an rms noise of ${\sim}0.1$ K per $2.5$ km s$^{-1}$ channel" (2.2 ALMA)

### Inherited from earlier work

- PHANGS-ALMA observing strategy, data reduction and product generation  
  > "The strategy for observing, data reduction and product generation are described in (cite: Leroy2021a)." (2.2 ALMA) [from (cite: Leroy2021a)]
- PHANGS-MUSE reduction pipeline and data analysis pipeline (SSP fitting, emission-line measurements)  
  > "The DAP will be described in detail in Emsellem et al. (in prep.)." (2.1 VLT/MUSE) [from Emsellem et al. (in prep.)]
- Metallicity-scaled alpha_CO prescription  
  > "scaled prescription as described in (cite: Accurso2017) and (cite: Sun2020)" (2.2 ALMA) [from (cite: Accurso2017); (cite: Sun2020)]
- CO(2-1)-to-CO(1-0) ratio of 0.65  
  > "adopting a ratio CO(2-1)-to-CO(1-0) = 0.65 (cite: Leroy2013; denBrok2021)" (2.2 ALMA) [from (cite: Leroy2013; denBrok2021)]
- Diffuse ionized gas correction of the Halpha flux  
  > "we followed the approach described in (cite: Blanc2009) with the modifications introduced in (cite: Kaplan2016)" (2.5 Star formation rate measurements) [from (cite: Blanc2009); (cite: Kaplan2016)]
- BPT AGN/LINER cut  
  > "to remove pixels that are dominated by AGN ionization from our sample" (2.5 Star formation rate measurements) [from (cite: Kewley2006)]
- Halpha to SFR conversion  
  > "we adopted the prescription described in (cite: Calzetti-book)" (2.5 Star formation rate measurements) [from (cite: Calzetti-book)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration details and CASA version: all deferred to Leroy et al. 2021a (ApJS submitted at the time); no pipeline or imaging settings in this paper
- Which PHANGS-ALMA data release / product version (and whether 'broad' maps at native resolution) was used; no download location or version given
- PHANGS-MUSE DAP outputs (stellar mass maps, line maps) are 'in prep.'; the code and exact version are needed to regenerate them
- Exact data-quality masks and pixel-level S/N cuts for CO and stellar mass maps (only a 1.5 S/N cut after resampling for the gas map is given)
- How the stellar mass surface density is derived from the pPXF weights (mass-to-light conversion details) is not spelled out
- Treatment of per-pixel uncertainty maps for stellar mass and SFR used in the bootstrap perturbation
- Definition and treatment of the nonzero detection threshold for Sigma_SFR and Sigma_stellar in the N/D classification beyond the S/N cuts
- Exact resampling algorithm (flux-conserving or not) used to degrade the maps to 100 pc, 500 pc, 1 kpc pixels
- Bootstrap random seeds; the 10th/90th percentile reference ratios for the DIG fit per galaxy

## Analysis recipe

1. **Derive stellar mass surface density maps from MUSE**: Voronoi-bin the MUSE mosaics and fit stellar population synthesis templates with pPXF, in two steps (Calzetti extinction fit, then fit with a multiplicative polynomial)  
  > "We use then the Penalized Pixel-Fitting (pPXF) code (cite: Capellari2004; Capellari2017) to fit the spectrum of each Voronoi bin." (2.4 Stellar mass surface density maps); "The SSP fitting was done in two steps." (2.4 Stellar mass surface density maps)
   - software: pPXF, Voronoi tessellation, PHANGS-MUSE DAP
   - parameter: Voronoi bins to minimum S/N ~35 (measured at 5300-5500 Angstrom)  
  > "to bin our MUSE data to a minimum signal-to-noise ratio (S/N) of ${\sim}35$" (2.4 Stellar mass surface density maps)
   - parameter: Template grid of 13 ages (30 Myr to 13.5 Gyr) and six metallicity bins  
  > "we used a grid of templates consisting of $13$ ages, ranging from $30$ Myr to $13.5$ Gyr, logarithmically-spaced" (2.4 Stellar mass surface density maps)
   - parameter: Fit range 4850-7000 Angstrom  
  > "We fit the wavelength range $4850{-}7000$ Å, in order to avoid spectral regions strongly affected by sky residuals." (2.4 Stellar mass surface density maps)
   - parameter: 12 degree multiplicative polynomial in the second iteration  
  > "including a $12$ degree multiplicative polynomial in this iteration in the fit" (2.4 Stellar mass surface density maps)
   - assumption: eMILES templates, Chabrier IMF, BaSTI isochrones with Galactic abundance pattern  
  > "We used templates from the eMILES (cite: Vazdekis2010; Vazdekis2012) database, assuming a (cite: Chabrier2003) IMF and BaSTI isochrone (cite: Pietrinferni2004) with a Galactic abundance pattern." (2.4 Stellar mass surface density maps)
   - assumption: Milky Way extinction corrected with Cardelli et al. 1989 law and Schlafly & Finkbeiner E(B-V); internal extinction with Calzetti et al. 2000 law  
  > "we correct the full mosaic for Milky Way extinction assuming a (cite: Cardelli89) extinction law" (2.4 Stellar mass surface density maps); "First, we fitted our data assuming a (cite: Calzetti2000) extinction law to correct for internal extinction." (2.4 Stellar mass surface density maps)
   - fitting: pPXF template fitting per Voronoi bin; foreign stars identified as velocity outliers and masked  
  > "we have identified foreground stars as velocity outliers in the SSP fitting" (2.4 Stellar mass surface density maps)
   - validation: Bootstrapped data at different S/N levels to choose the bin S/N keeping mass uncertainty below 15%; compared overlapping MUSE pointings (~3% offsets)  
  > "we bootstrapped our data to have an estimate of the uncertainties at each S/N level" (2.4 Stellar mass surface density maps)
2. **Derive SFR surface density maps from Halpha**: Fit Gaussians to emission lines per pixel, de-redden Halpha with the Balmer decrement, remove AGN-dominated pixels with a BPT cut, correct for diffuse ionized gas, convert Halpha to SFR  
  > "we fit Gaussian profiles to a number of emission lines for each pixel of the final combined MUSE mosaic of each galaxy in our sample" (2.5 Star formation rate measurements); "to remove pixels that are dominated by AGN ionization from our sample" (2.5 Star formation rate measurements)
   - software: PHANGS-MUSE DAP
   - parameter: Intrinsic Halpha/Hbeta = 2.86 (case B)  
  > "assuming that $\mathrm{H}\alpha_\mathrm{corr} / \mathrm{H}\beta_\mathrm{corr} = 2.86$" (2.5 Star formation rate measurements)
   - parameter: O'Donnell 1994 law: k_alpha = 2.52, k_beta = 3.66, R_V = 3.1  
  > "Opting for an (cite: ODonnell1994) extinction law, we use $k_{\alpha} = 2.52$, $k_{\beta} = 3.66$, and $R_\mathrm{V} = 3.1$." (2.5 Star formation rate measurements)
   - parameter: S/N cut of 4 for Halpha and 2 for Hbeta  
  > "A S/N cut of 4 for H$\alpha$ and 2 for H$\beta$ was then applied" (2.5 Star formation rate measurements)
   - parameter: DIG and HII reference [SII]/Halpha ratios taken at the 10th and 90th percentile of the Halpha distribution  
  > "faint (10th percentile) and bright (90th percentile) end of the H$\alpha$ distribution" (2.5 Star formation rate measurements)
   - parameter: SFR = 5.5e-42 x Halpha_corr (erg/s) in Msun/yr  
  > "= 5.5\times10^{-42}" (2.5 Star formation rate measurements)
   - assumption: SFR conversion scaled to a Kroupa IMF, assumed to differ little from the Chabrier IMF used for SSP fitting  
  > "This equation is scaled to a Kroupa universal IMF (cite: Kroupa2001)" (2.5 Star formation rate measurements)
   - assumption: Fully sampled IMF assumed  
  > "We acknowledge that Eq. [\[eq:sfr\]](#eq:sfr) assumes a fully-sampled IMF" (2.5 Star formation rate measurements)
   - fitting: Least-squares fit of C_HII = 1 - (f0/Halpha)^beta per galaxy for the DIG fraction  
  > "Then, we perform a least squares fitting to find the best $\beta$ and $f_{0}$ parameters such that:" (2.5 Star formation rate measurements)
   - validation: Example C_HII fit shown in an appendix; tested setting SFR of non-star-forming pixels to zero and an alternative HII-region mask  
  > "However, our main findings do not change qualitatively when we set to zero the SFR of these pixels" (2.5 Star formation rate measurements)
3. **Convert CO(2-1) intensity to molecular gas surface density**: Apply a metallicity-scaled alpha_CO to the PHANGS-ALMA broad-mask integrated intensity maps  
  > "For our analysis we use the integrated intensity maps from the broad masking scheme, which are optimized for completeness" (2.2 ALMA)
   - parameter: alpha_CO = 4.35 Z'^-1.6 Msun pc^-2 (K km/s)^-1 with CO(2-1)/CO(1-0) = 0.65  
  > "= 4.35 Z'^{-1.6}" (2.2 ALMA); "adopting a ratio CO(2-1)-to-CO(1-0) = 0.65" (2.2 ALMA)
   - parameter: IC 5332 excluded from rKS and rMGMS (no significant CO detection)  
  > "IC 5332 has no significant detection of CO(2–1) emission and therefore has been excluded from the rKS and rMGMS analysis." (2.2 ALMA)
   - assumption: Metallicity from radial gas-phase abundance profile; azimuthal metallicity variations (0.04-0.05 dex) neglected  
  > "these variations are small ($0.04 - 0.05$ dex), implying variations of $\sim0.06$ dex in $\alpha_{\mathrm{CO}}$) and therefore do not impact our results" (2.2 ALMA)
   - fitting: _not stated_
   - validation: Tested a constant alpha_CO = 4.35 (Bolatto et al. 2013)  
  > "We test the robustness of our results against a constant $\alpha_\mathrm{CO} = 4.35$" (2.2 ALMA)
4. **Resample maps to 100 pc, 500 pc and 1 kpc and correct for inclination**: Resample native MUSE and ALMA maps to larger pixels (no convolution), apply BPT/extinction/DIG correction at each scale, S/N cut on gas, multiply by cos(i)  
  > "we have resampled our native resolution MUSE and ALMA maps to pixel sizes of $100$ pc, $500$ pc and $1$ kpc" (3.1 Sampling the data at larger spatial scales); "we have corrected the maps by inclination, using a multiplicative factor of $\cos(i)$" (3.1 Sampling the data at larger spatial scales)
   - parameter: S/N cut of 1.5 on the molecular gas surface density after resampling  
  > "Additionally we have imposed a S/N cut of $1.5$ for the molecular gas mass surface density map after the resampling" (3.1 Sampling the data at larger spatial scales)
   - parameter: DIG parameters f0 and beta measured only at native MUSE resolution; DIG correction done independently at each scale  
  > "The parameters $f_{0}$ and $\beta$ used for the DIG correction are calculated only at the native MUSE resolution, and do not change with spatial scale." (3.1 Sampling the data at larger spatial scales)
   - assumption: Typical DIG flux surface density does not vary with spatial scale  
  > "This assumes that the typical DIG flux surface density does not vary with spatial scale" (3.1 Sampling the data at larger spatial scales)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit the rSFMS, rKS and rMGMS power laws**: Bin the x-axis in 0.15 dex steps, take the mean in linear space including non-detections as zeros, bootstrap the bin errors, fit a power law with weighted least squares  
  > "To fit each scaling relation, we binned the $x$-axis of our data in steps of $0.15$ dex, and calculated the mean within each bin." (3.2 Fitting technique); "therefore we adopt the mean measured in linear space as our fiducial approach" (3.2 Fitting technique)
   - parameter: Minimum 5 nonzero points per bin at 100 pc for individual galaxies; minimum 10 per bin for the full sample at all scales  
  > "A minimum of 5 data points with nonzero signal per bin was imposed at the $100$ pc spatial scale for individual galaxies" (3.2 Fitting technique); "For the full-sample relations, we imposed a minimum of 10 nonzero data points per bin at all spatial scales." (3.2 Fitting technique)
   - parameter: 100 bootstrap subsamples with data perturbed by their uncertainties; bin error = standard deviation of the 100 means  
  > "we repeatedly chose $100$ subsamples (allowing for repetitions), perturbed the data according to their uncertainties, and calculated their mean values." (3.2 Fitting technique)
   - parameter: Scatter = median absolute deviation of detected points about the best-fitting power law  
  > "the scatter reported throughout the paper for the fitted power laws corresponds to the median absolute deviation of each data point, considering detections only, with respect to the best-fitting power law." (3.2 Fitting technique)
   - assumption: x-axis uncertainty of each bin negligible compared with y-axis uncertainty  
  > "by construction, the $x$-axis uncertainty of each bin is negligible, compared to its $y$-axis uncertainty" (3.2 Fitting technique)
   - fitting: Weighted least squares per bootstrap iteration, weights = inverse variance of each bin; final slope and error = mean and standard deviation of the 100 slopes  
  > "To do this, we use a weighted least square fitting routine (WLS), where each bin is weighted by the inverse of its variance." (3.2 Fitting technique); "The final slope and its error correspond to the mean and standard deviation of the slopes distribution, respectively." (3.2 Fitting technique)
   - validation: Tested radial binning (rejected) and averaging in log space; compared binning schemes including/excluding non-detections  
  > "We have also tested radial binning in the $x$-axis (i.e., calculating the means in bins defined as data points located at similar galactocentric radius), but this raised the scatter within each bin" (3.2 Fitting technique)
6. **Compare relations across individual galaxies and environments**: Fit each relation per galaxy; measure vertical offset Delta_env and slope of the binned relation in each morphological environment against the overall fit; correlate slope differences with global parameters (Delta MS) via the Pearson coefficient  
  > "We use the offset ($\Delta_\mathrm{env}$) defined as the vertical offset between the binned scaling relation from each environment and the overall best-fitting power law" (4.2 Scaling relations in individual galaxies); "Figure [10](#fig:slope_var_vs_SFR) shows the difference between the slope derived from the full sample and that of each individual galaxy" (4.2 Scaling relations in individual galaxies)
   - parameter: Delta alpha_overall = alpha_gal - alpha_overall  
  > "\Delta\alpha_\mathrm{overall} = \alpha_\mathrm{gal} - \alpha_\mathrm{overall}" (4.2 Scaling relations in individual galaxies)
   - fitting: _not stated_
   - validation: _not stated_
7. **Test the role of non-detections and detection fraction**: Refit excluding non-detections (alpha_D/O, sigma_D/O); measure the Halpha detection fraction in 1 kpc^2 boxes on the 100 pc maps and correlate its mean and standard deviation with slope changes  
  > "We define $\alpha_{\rm D/O}$ and $\sigma_{\rm D/O}$ as the measured slope and scatter considering pixels with nonzero detections only." (5.2.2 Slope changes in our scaling relations); "We measured the detection fraction of the SFR inside $1$ kpc$^2$ boxes in the $100$ pc spatial scale maps." (5.2.3 Treatment of non-detections and its effect on the slope of the scaling relations)
   - parameter: Delta alpha_D/O = alpha - alpha_D/O  
  > "\Delta\alpha_\mathrm{D/O} = \alpha - \alpha_\mathrm{D/O}" (5.2.3 Treatment of non-detections and its effect on the slope of the scaling relations)
   - fitting: _not stated_
   - validation: Compared with simulation results of Hani et al. 2020 and Calzetti et al. 2012  
  > "This steepening of the rSFMS is mainly a consequence of the methodology used (i.e., excluding N/D in the fitting process)." (5.2.2 Slope changes in our scaling relations)
8. **Systematics tests: HII-region mask, constant alpha_CO, 150 Myr SFR tracer, baryonic surface density**: Repeat the fits after (a) masking all emission outside HII regions identified with HIIphot/DAOStarFinder, (b) using a constant alpha_CO, (c) using an SFR from the SSP star formation histories over the last 150 Myr, (d) using Sigma_stellar + Sigma_mol.gas as x-axis  
  > "are identified in the H$\alpha$ map using HIIphot (cite: Thilker2000) for resolved sources and DAOStarFinder (cite: Bradley2020) for point-like sources" (5.4.1 Role of diffuse gas emission); "Multiplying this fraction with the stellar mass surface density and dividing it by $1.5\times10^{7}$ yr results in a SFR surface density map that probes longer timescales." (5.4.3 Probing SFR on a 150 Myr timescale with spectral fitting)
   - software: HIIphot, DAOStarFinder
   - parameter: Constant alpha_CO = 4.35 Msun pc^-2 (K km/s)^-1  
  > "assuming a constant conversion factor of $4.35$ M$_{\odot}$ pc$^{-2}$ (K km s$^{-1}$)$^{-1}$" (5.4.2 Impact of the chosen CO-to-H2 conversion factor)
   - parameter: Long-timescale SFR from mass fraction formed in the youngest 4 age bins (last 150 Myr)  
  > "(i.e., the youngest 4 age bins in our age–metallicity grid)" (5.4.3 Probing SFR on a 150 Myr timescale with spectral fitting)
   - parameter: Sigma_b = Sigma_stellar + Sigma_mol.gas  
  > "computed the “baryonic” mass surface density as $\Sigma_\mathrm{b} = \Sigma_\mathrm{stellar} + \Sigma_\mathrm{mol. gas}$" (5.3 Role of baryonic mass surface density in regulating SFR)
   - fitting: Same binned weighted least-squares fitting as the fiducial case  
  > "We derived the $\Sigma_\mathrm{b}$ versus $\Sigma_\mathrm{SFR}$ relation at $100$ pc spatial scale" (5.3 Role of baryonic mass surface density in regulating SFR)
   - validation: Results compared with the fiducial slopes and scatter at each scale  
  > "The inferred slopes agree relatively well with those obtained using the fiducial method" (5.4.1 Role of diffuse gas emission)

## Software

- **pPXF** : Stellar population (SSP) fitting of Voronoi-binned MUSE spectra  
  > "We use then the Penalized Pixel-Fitting (pPXF) code (cite: Capellari2004; Capellari2017) to fit the spectrum of each Voronoi bin." (2.4 Stellar mass surface density maps)
- **Voronoi tessellation binning** : Binning MUSE data to S/N ~35  
  > "First, we used a Voronoi tessellation (cite: Capellari2003) to bin our MUSE data" (2.4 Stellar mass surface density maps)
- **esorex-based PHANGS-MUSE reduction pipeline** : Reduction of MUSE observations  
  > "Observations were reduced using a pipeline built on esorex and developed by the PHANGS team" (2.1 VLT/MUSE)
- **PHANGS-MUSE data analysis pipeline (DAP)** : SSP fitting and emission line measurements for stellar mass and SFR maps  
  > "we have used the PHANGS data analysis pipeline (DAP, developed by Francesco Belfiore and Ismael Pessa) to derive various physical quantities." (2.1 VLT/MUSE)
- **HIIphot** : Identifying resolved HII regions for the HII-region mask test  
  > "are identified in the H$\alpha$ map using HIIphot (cite: Thilker2000) for resolved sources and DAOStarFinder (cite: Bradley2020) for point-like sources" (5.4.1 Role of diffuse gas emission)
- **DAOStarFinder** : Identifying point-like HII regions for the HII-region mask test  
  > "are identified in the H$\alpha$ map using HIIphot (cite: Thilker2000) for resolved sources and DAOStarFinder (cite: Bradley2020) for point-like sources" (5.4.1 Role of diffuse gas emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| rSFMS slope at 100 pc (full sample) | 1.05 | 0.01 | dimensionless | 5 | We have measured a slope of $1.05\pm0.01$ for the rSFMS, $1.06\pm0.01$ for the rKS, and $1.18\pm0.01$ for the rMGMS. |
| rKS slope at 100 pc (full sample) | 1.06 | 0.01 | dimensionless | 5 | We have measured a slope of $1.05\pm0.01$ for the rSFMS, $1.06\pm0.01$ for the rKS, and $1.18\pm0.01$ for the rMGMS. |
| rMGMS slope at 100 pc (full sample) | 1.18 | 0.01 | dimensionless | 5 | We have measured a slope of $1.05\pm0.01$ for the rSFMS, $1.06\pm0.01$ for the rKS, and $1.18\pm0.01$ for the rMGMS. |
| Intercepts of rSFMS, rKS, rMGMS at 100 pc | -10.63, -9.96, -2.23 | not stated | dimensionless | 5 | the intercepts that set the normalization of these relations are $-10.63$, $-9.96$, $-2.23$. |
| Scatter at 100 pc: rMGMS, rKS, rSFMS | 0.34, 0.41, 0.51 | not stated | dex | 5 | we find that the rMGMS has the lowest scatter ($\sigma \approx 0.34$ dex), followed by the rKS and the rSFMS with scatter $\sigma \approx 0.41$ dex and $\sigma \approx 0.51$ dex, respectively |
| Number of data points at 100 pc (rSFMS, rKS, rMGMS) | 313227, 110084, 309569 | not stated | pixels | 4 | The number of data points used is $313\,227$, $110\,084$ and $309\,569$ for the rSFMS, rKS, and rMGMS, respectively. |
| Detection fraction at 100 pc (rSFMS, rKS, rMGMS) | 0.50, 0.84, 0.35 | not stated | dimensionless | 4 | the total detection fraction, defined as the fraction of pixels with a nonzero detection in the $y$-axis ($1-f_\mathrm{N/D}$), is $0.50$, $0.84$, and $0.35$. |
| rKS scatter at 1 kpc | 0.27 | not stated | dex | 5 | with the resolved Kennicutt–Schmidt relation being the tightest ($0.27$ dex) at a spatial scale of $1$ kpc |
| Pixels at 1 kpc (rSFMS, rKS, rMGMS) and detection fractions | 2860, 1510, 2820 pixels; detection fractions 0.62, 0.90, 0.52 | not stated | pixels; dimensionless | 4 | the number of pixels used at $1$ kpc resolution drops to $2860$, $1510$, and $2820$, and the fraction of pixels with detected signal increases to $0.62$, $0.90$, and $0.52$ |
| Dispersion of per-galaxy slopes (rSFMS, rMGMS, rKS) | 0.34, 0.32, 0.17 | not stated | dimensionless | 6 | The rSFMS relation shows the largest dispersion in slopes among galaxies ($\sigma\approx0.34$), followed by the rMGMS ($\sigma\approx0.32$), and finally the rKS ($\sigma\approx0.17$) |
| Pearson correlation of rSFMS slope difference with Delta MS | ~0.49 | not stated | dimensionless | 6 | (Pearson correlation coefficient (PCC) of ${\sim}0.49$) |
| Pearson correlation of slope change (excluding N/D) with mean Halpha detection fraction | -0.68 | not stated | dimensionless | 7 | The figure shows a negative correlation ($\mathrm{PCC} \approx {-}0.68$) |
| Pearson correlation of Delta alpha_overall with sigma of the detection fraction distribution (rSFMS) | 0.72 | not stated | dimensionless | 7 | The figure shows a clear positive correlation ($\mathrm{PCC} \approx 0.72$) |
| Sigma_b vs Sigma_SFR slope and scatter at 100 pc | slope 1.21; scatter 0.49 | slope 0.01 | dimensionless; dex | 8 | measured a slope of $1.21\pm0.01$ and a scatter of $0.49$ dex |
| Sigma_b vs Sigma_SFR slope and scatter at 500 pc and 1 kpc | 500 pc: slope 1.22, scatter 0.46; 1 kpc: slope 1.14, scatter 0.42 | slope 0.02 (500 pc), 0.03 (1 kpc) | dimensionless; dex | 8 | At $500$ pc we obtain a slope of $1.22\pm0.02$ and a scatter of $0.46$ dex, and at $1$ kpc a slope of $1.14\pm0.03$ and a scatter of $0.42$ dex. |
| Slopes of rKS and rMGMS with constant alpha_CO at 100 pc | rKS 1.01; rMGMS 1.28 | 0.01 each | dimensionless | 8 | the slope of the rKS decreases to $1.01\pm0.01$ and that of the rMGMS increases to $1.28\pm0.01$ |
| Intercepts of rKS and rMGMS with constant alpha_CO | -9.29, -3.36 | not stated | dimensionless | 8 | we find an intercept of $-9.29$ for the rKS and $-3.36$ for the rMGMS |
| rSFMS and rKS slopes with 150 Myr SFR tracer at 100 pc | rSFMS 0.61; rKS 0.60 | 0.01 each | dimensionless | 8 | the slope of the rSFMS decreases to $0.61\pm0.01$ and the slope of the rKS to $0.60\pm0.01$. |
| rSFMS and rKS scatter with 150 Myr SFR tracer | 0.27, 0.24 | not stated | dex | 8 | This also drastically reduces the scatter in both relations to $0.27$ dex and $0.24$ dex, respectively. |
| Scatter increase with strict HII-region mask | factor ~1.1-1.4 | not stated | dimensionless | 8 | the scatter is systematically enhanced in both relations by a factor of $\sim1.1 - 1.4$ |
| Spiral arm offset above overall rSFMS and rMGMS | up to ~0.4 | not stated | dex | 6 | The spiral arms share a similar slope, but are systematically offset above the overall relations by up to ${\sim}0.4$ dex. |

## Qualitative findings

- The three resolved relations (rSFMS, rKS, rMGMS) are all recovered at 100 pc  
  > "All three relations were recovered at the highest spatial resolution ($100$ pc)." (abstract)
- The rKS shows the least variation across galaxies and environments, while rSFMS and rMGMS vary more  
  > "Surprisingly, the resolved Kennicutt–Schmidt relation shows the least variation across galaxies and environments" (abstract)
- Excluding non-detections systematically changes the inferred slope with spatial scale  
  > "The exclusion of non-detections has a systematic impact on the inferred slope as a function of the spatial scale." (abstract)
- Bars lie systematically below the overall relations, especially in the rSFMS  
  > "Finally, bars lie systematically below the overall relations, especially in the case of the rSFMS" (4.2 Scaling relations in individual galaxies)

## Claim tuples

- H: Do the rSFMS, rKS and rMGMS exist at 100 pc and how do their scatters rank | E: Binned weighted power-law fits to MUSE-derived Sigma_stellar and Sigma_SFR and ALMA CO-derived Sigma_mol.gas for 18 PHANGS galaxies at 100 pc | R: Slopes 1.05, 1.06, 1.18; scatter 0.51, 0.41, 0.34 dex for rSFMS, rKS, rMGMS | F: All three relations are recovered at 100 pc, with rMGMS the tightest, consistent with the timescale ordering tau_Halpha < tau_CO < tau_stars | **supported**
- H: How do slope and scatter depend on spatial scale when non-detections are included | E: Resampled maps to 100 pc, 500 pc, 1 kpc and refit | R: Slopes consistent within 2 sigma across scales; scatter decreases at coarser scale; rKS tightest at 1 kpc (0.27 dex) | F: No systematic slope dependence on spatial scale when non-detections are included; scatter falls with scale | **supported**
- H: Does excluding non-detections bias the slope as a function of spatial scale | E: Refit excluding non-detected pixels at 100 pc, 500 pc and 1 kpc and relate slope change to Halpha detection fraction | R: Systematic steepening with larger scale in rSFMS and rMGMS; correlations with detection fraction (PCC -0.68, 0.72) | F: Excluding non-detections artificially flattens relations at small scales | **supported**
- H: Do the relations vary across galactic environments | E: Binned relations and offsets for disk, spiral arms, rings, bars and centers using the environmental masks | R: rKS slope and normalization are similar across environments; rSFMS and rMGMS vary by up to ~0.4 dex | F: Environment strongly impacts rSFMS and rMGMS but little the rKS | **supported**
- H: Does baryonic surface density predict SFR better than molecular gas alone | E: Fit Sigma_SFR against Sigma_stellar + Sigma_mol.gas at three spatial scales | R: Scatter 0.49, 0.46, 0.42 dex at 100 pc, 500 pc, 1 kpc, higher than the rKS | F: Molecular gas is a better predictor of SFR than baryonic mass surface density | **supported**

## Reasoning

- Why this data: PHANGS galaxies chosen within 20 Mpc and low inclination to resolve star-forming regions of 50-100 pc  
  > "have been selected to have a distance lower than $20$ Mpc to resolve the typical scale of star-forming regions ($50{-}100$ pc)" (2 Data)
- Why this method: Bin the x-axis and fit bin means so outer disk regions with more pixels do not dominate; adopt linear-space mean including non-detections to compare consistently across scales  
  > "Fitting bins rather than single data points avoids giving statistically larger weight to the outer part of a galaxy, where more pixels are available." (3.2 Fitting technique); "therefore we adopt the mean measured in linear space as our fiducial approach" (3.2 Fitting technique)
- Alternative: Radial binning on the x-axis rejected because it raised scatter within each bin; log-space averaging considered as a comparison  
  > "We have also tested radial binning in the $x$-axis (i.e., calculating the means in bins defined as data points located at similar galactocentric radius), but this raised the scatter within each bin" (3.2 Fitting technique)
- Alternative: Strict HII-region mask, constant alpha_CO and 150 Myr SFR tracer tested as alternatives to the fiducial choices  
  > "We applied a different approach to remove non-star-forming (diffuse) emission contaminating our SFR tracer before measuring the scaling relations, a different CO-to-H$_{2}$ conversion factor prescription, and a SFR tracer probing a longer timescale." (6 Summary)
- How they decided it was enough: _not stated_
- Limitation (authors): Quoted slope errors do not include systematic uncertainties  
  > "it does not reflect the uncertainties induced by systematic effects" (3.2 Fitting technique)
- Limitation (authors): Fiducial scatter is possibly underestimated because of contaminating Halpha emission boosting the faintest pixels  
  > "Hence, in our fiducial approach the scatter of these relations is possibly underestimated due to contaminant H$\alpha$ emission boosting the SFR of the faintest pixels." (5.4.1 Role of diffuse gas emission)
- Limitation (authors): The rSFMS correlation with Delta MS is not robust given scatter and limited number of points  
  > "we stress here that even though the rSFMS shows hints of a correlation, the scatter and the limited number of data points make it hard to draw a robust conclusion." (5.1.1 Variations with spatial scale between and within galaxies)
- Caveat (inferred, ours): Pixels are resampled without convolution, so 100 pc pixels are smaller than the 1.0-1.5 arcsec CO beam for many galaxies; neighbouring pixels are not independent and bootstrap errors may be too small
- Caveat (inferred, ours): Non-detection definition depends on S/N cuts that differ between MUSE (4 and 2) and CO (1.5 after resampling), which may drive the detection fractions and thus the slopes
- Caveat (inferred, ours): Slope uncertainties (0.01) are statistical only and are tiny relative to the galaxy-to-galaxy dispersion
- Caveat (inferred, ours): Metallicity-dependent alpha_CO couples Sigma_mol.gas to the same metallicity gradient that varies with radius, which may induce correlations in the rKS and rMGMS

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: PHANGS-MUSE DAP not released; to be described in Emsellem et al. (in prep.). No analysis code for the scaling-relation fits is mentioned  
  > "The DAP will be described in detail in Emsellem et al. (in prep.)." (2.1 VLT/MUSE)
- Missing: PHANGS-MUSE DAP products (stellar mass, line flux maps) with version and download location
- Missing: Exact PHANGS-ALMA map release used and its processing parameters
- Missing: Per-galaxy DIG parameters (f0, beta) and the full environmental-mask files
- Missing: Resampling and error-propagation code used for the 100 pc/500 pc/1 kpc maps
- Data volume (inferred): Derived maps only: tens of GB if MUSE mosaics are re-processed; under 1 GB for CO integrated intensity maps and masks of 18 galaxies
- Score (inferred): 3/5, The fitting recipe (binning, bootstrap, WLS, scatter definition) and many numeric results are fully given, but the MUSE DAP outputs and PHANGS-ALMA products come from papers in preparation or submission and no data locations or code are given.
- Rediscovery candidate: no, The paper does not state that the input maps are public and the MUSE DAP is unpublished, so the upstream products cannot be regenerated from the text alone.

## Links

- Method: (cite: Leroy2021a) (PHANGS-ALMA observing strategy, data reduction and product generation)
- Method: (cite: Leroy2021b) (PHANGS-ALMA survey and global galaxy parameters)
- Method: Emsellem et al. (in prep.) (PHANGS-MUSE survey and data analysis pipeline)
- Method: (cite: Querejeta2021) (Environmental masks)
- Method: (cite: Blanc2009); (cite: Kaplan2016) (Diffuse ionized gas correction of Halpha)
- Method: (cite: Sun2020) (Metallicity-scaled alpha_CO prescription)
- Companion: (cite: Lin2019); (cite: Ellison2020); (cite: Morselli2020) (Earlier reports of the resolved molecular gas main sequence compared with the results)
- Companion: (cite: Kruijssen2014); (cite: Kruijssen2018) (Uncertainty principle used to interpret the scatter versus spatial scale)
- Companion: (cite: Barrera-Ballesteros2021) (Baryonic surface density relation at kpc scale compared with this work)
- Related: PHANGS-ALMA
- Related: PHANGS-MUSE
- Related: Spitzer Survey of Stellar structure in Galaxies (S4G)

## Checks

```json
{
 "quotes": 146,
 "quotes_ok": 146,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 21,
 "numeric_problems": 0,
 "fill": {
  "facts": 126,
  "stated": 94,
  "rate": 0.746
 },
 "evidence_ok": true
}
```
