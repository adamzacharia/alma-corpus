# The PHANGS-AstroSat Atlas of Nearby Star-forming Galaxies

`2024ApJS..271....2H` | The Astrophysical Journal Supplement Series 2024 | first author: Hassani, Hamid | arXiv: 2312.06031 | DOI: 10.3847/1538-4365/ad152c

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type data_release_or_catalog

## Science

- Fields: nearby_galaxies, star_formation
- Question: Build a homogeneous AstroSat UVIT far/near-UV atlas of 31 PHANGS galaxies, check its quality against GALEX, and use it with PHANGS-ALMA CO(2-1) and PHANGS-MUSE Halpha to study extended UV disks, UV vs CO clumping, and what drives the FUV/Halpha ratio.  
  > "Our main focus is to reduce and assess the quality of the data set and compare it with previous low-resolution observations." (Introduction); "Additionally, we study the variation of the UV and molecular gas clumpiness in different morphological regions of galaxies." (Introduction)
- Target **PHANGS-AstroSat sample of 31 nearby star-forming galaxies (e.g. IC 5332, NGC 0628, NGC 1365, NGC 1566, NGC 6744, NGC 7793)**: coordinates _not stated_; z/distance D < 22 Mpc; per-galaxy distances tabulated (e.g. NGC 0300 2.09 Mpc, NGC 4654 21.98 Mpc)  
  > "galaxies within a distance of 22 Mpc" (abstract); "Properties are taken from (cite: Leroy2021)." (Adopted Galaxy Properties table notes); distance from Leroy2021 (PHANGS-ALMA sample paper)  
  > "galaxies within a distance of 22 Mpc" (abstract); "Properties are taken from (cite: Leroy2021)." (Adopted Galaxy Properties table notes)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 6 (CO(2-1) maps from PHANGS-ALMA)  
  > "The emission lines were observed at the rest frequency of $\nu=230.538$ GHz (Band 6)" (2.3.1 PHANGS-ALMA)
- frequencies and spectral setup: CO(2-1) at 230.538 GHz; bandwidth 937.5 MHz, channel width 244 kHz, velocity resolution 2.5 km/s  
  > "The emission lines were observed at the rest frequency of $\nu=230.538$ GHz (Band 6)" (2.3.1 PHANGS-ALMA); "These observations were conducted using a bandwidth of 937.5  MHz with a channel width of $\Delta \nu = 244$ kHz." (2.3.1 PHANGS-ALMA); "The velocity resolution of 2.5 km s$^{-1}$ is chosen to improve the signal-to-noise ratio and quality of the deconvolution process." (2.3.1 PHANGS-ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1 arcsec (100 pc at 20 Mpc)  
  > "The ALMA data set provides a unique, $\sim$1$''$ (100 pc at 20 Mpc) view of nearby main-sequence galaxies at GMCs scale." (2.3.1 PHANGS-ALMA)
- max recoverable scale: _not stated_
- sensitivity: median 1 sigma noise 6.2 mJy/beam at native resolution (~0.17 K)  
  > "The median of 1$\sigma$ noise in the cube of all targets is estimated to be 6.2 mJy beam$^{-1}$ at native resolution" (2.3.1 PHANGS-ALMA)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PHANGS-ALMA CO(2-1) maps taken from the PHANGS-ALMA survey release (Leroy2021)  
  > "We used CO (2-1) emission line maps from the PHANGS–ALMA project (cite: Leroy2021)." (2.3.1 PHANGS-ALMA)
- Line: CO J=2-1 (230.538 GHz)
- Other facility **AstroSat UVIT (FUV/NUV)**: Primary data: UV images of 31 galaxies; 11 from dedicated PHANGS programs (1-3 ks actually acquired), 20 from the AstroSat archive  
  > "We observed 11 of the 31 selected galaxies under programs T03-032, T03-033, A05-022, A07-027, A08-003, and A10-021." (2.2 Observations); "However, instrumental fluctuations and orbital accessibility limit the actual time acquired to $1-3$ ks." (2.2 Observations)
- Other facility **VLT/MUSE (PHANGS-MUSE)**: Halpha and Hbeta emission-line maps and stellar-population age/mass/metallicity products  
  > "We also utilized products from PHANGS-MUSE (program IDs: 1100.B-0651/PI: E. Schinnerer; 095.C-0473/PI: G. Blanc; and 094.C-0623/PI: K. Kreckel)." (2.3.2 PHANGS-MUSE)
- Other facility **GALEX (z0MGS maps)**: Background-subtracted, extinction-corrected GALEX UV maps used to check the AstroSat flux scale  
  > "These GALEX maps are background-subtracted for UV background emission and corrected for foreground Galactic extinction." (2.3.3 Literature data sets)
- Other facility **Gaia DR3**: Stars used for PSF measurement  
  > "we cross match to objects identified in Gaia Data Release 3 (cite: gaia2)" (3.3.1 Resolution and Alignment)
- Other facility **HST (PHANGS-HST F275W)**: NUV reference for checking astrometric alignment  
  > "We evaluate the quality of the solution by comparing NUV data (where available)" (3.3.1 Resolution and Alignment)
- External data: PHANGS-ALMA CO(2-1) broad-mask integrated-intensity (zero-moment) maps and uncertainty maps  
  > "Along with zero-moment maps that we used in this study, the uncertainty maps are also provided based on a three-dimensional noise model (cite: Leroy2021)." (2.3.1 PHANGS-ALMA) [from Leroy2021]
- External data: Galaxy properties (stellar mass, SFR, distance, inclination, PA)  
  > "Properties are taken from (cite: Leroy2021)." (Adopted Galaxy Properties table notes) [from Leroy2021]
- External data: PHANGS-MUSE emission-line maps (Halpha, Hbeta) and stellar-population fits  
  > "We use the emission line maps from (cite: phangs-muse), which are created through the MUSE Data Analysis Pipeline (DAP)" (2.3.2 PHANGS-MUSE) [from phangs-muse]
- External data: GALEX FUV/NUV and WISE maps for comparison  
  > "we use the infrared and UV maps of our targets provided by (cite: z0mgs)" (2.3.3 Literature data sets) [from z0mgs]
- External data: Foreground color excess E(B-V) per galaxy  
  > "Second column: foreground color excess from (cite: sfd98)." (Table 3 notes) [from sfd98]
- External data: Environment masks (center, bar, spiral arms, interarm, disk)  
  > "We use the environment masks from (cite: mask) to measure the clumping factor in different morphological regions of galaxies." (5.1 Clumping Factor) [from mask]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Released PHANGS-ALMA CO moment maps used; no ALMA calibration done in this paper  
  > "Along with zero-moment maps that we used in this study, the uncertainty maps are also provided based on a three-dimensional noise model (cite: Leroy2021)." (2.3.1 PHANGS-ALMA)
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
- masking: High-completeness 'broad' mask, built by convolving cube to lower resolutions  
  > "The broad mask is built by convolving the cube into several lower resolution cubes and then a mask was created." (2.3.1 PHANGS-ALMA)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Analysis of FUV and CO at common resolution of 175 pc (also 1 kpc hexagonal apertures)  
  > "We restrict our analysis to the regions where FUV maps overlap with the ALMA CO observations and carry out the analysis at a common resolution of 175 pc." (5.1 Clumping Factor)
- final beam: ~1 arcsec native resolution  
  > "The ALMA data set provides a unique, $\sim$1$''$ (100 pc at 20 Mpc) view of nearby main-sequence galaxies at GMCs scale." (2.3.1 PHANGS-ALMA)
- final rms: median 1 sigma 6.2 mJy/beam (~0.17 K) at native resolution  
  > "The median of 1$\sigma$ noise in the cube of all targets is estimated to be 6.2 mJy beam$^{-1}$ at native resolution" (2.3.1 PHANGS-ALMA)

### Inherited from earlier work

- All ALMA CO(2-1) observing, calibration, imaging and masking  
  > "We used CO (2-1) emission line maps from the PHANGS–ALMA project (cite: Leroy2021)." (2.3.1 PHANGS-ALMA) [from (cite: Leroy2021)]
- Foreground extinction correction procedure  
  > "for foreground extinction following the (cite: z0mgs) procedure" (3.2 Foreground extinction) [from (cite: z0mgs)]
- Clumping factor definition  
  > "We define the clumping factor following (cite: Leroy_2013; Sun_2022):" (5.1 Clumping Factor) [from (cite: Leroy_2013; Sun_2022)]
- Gini coefficient definition  
  > "Following (cite: Davis), we define the parameter as:" (5.2 Gini coefficient) [from (cite: Davis)]
- LASSO with 5-fold cross-validation  
  > "Following (cite: day), we use 5-fold cross-validation (CV) to fine-tune the hyperparameters of the model" (6.3.1 Drivers of the FUV/Halpha Ratio) [from (cite: day)]
- Astrometric solution in CCDLAB  
  > "following the approach outlined in (cite: postma20)" (3.3.1 Resolution and Alignment) [from (cite: postma20)]

### Not stated but needed to reproduce (our reading)

- ALMA project codes and the PHANGS-ALMA release/version (all ALMA calibration, imaging and masking is deferred to Leroy2021)
- Which AstroSat pipeline version (v2.1 or v2.2) and CCDLAB settings were used for each galaxy, and the zero-point and lambda_mean values per UVIT filter
- Bounds and starting values and optimizer of the exponential-plus-constant regression, and the fit radius range per galaxy
- Per-galaxy annulus radii for the mean-level background and the apertures chosen for NGC 6744
- Hexagonal aperture size definition, centers and masking of bright stars for the 1 kpc and 175 pc measurements
- LASSO alpha grid, number of bootstrap resamples, how the Halpha EW weighting was applied, and treatment of non-detections/thresholds
- How CO integrated intensity was convolved/reprojected to 175 pc and 1 kpc and which noise cut was applied to CO and FUV maps
- MUSE product versions and Balmer-decrement E(B-V) recipe, extinction curve for the Halpha correction beyond R_V=3.1
- Parameters of the Boquien (2012) FUV attenuation prescription used

## Analysis recipe

1. **Reduce and calibrate UVIT images**: AstroSat Level-1 pipeline, Level-2 in CCDLAB, counts/s converted to flux density with HZ4-based zero points, images reprojected onto cardinal axes with adaptive resampling  
  > "and the Level-2 data were processed with the CCDLAB software package (cite: postma17)." (3 AstroSat Data Processing); "We align each image along the cardinal directions by reprojecting with the REPROJECT python package" (3 AstroSat Data Processing)
   - software: CCDLAB, REPROJECT
   - parameter: HZ4 white dwarf as photometric calibrator; flux density from CPS times unit conversion factor derived from AB zero point  
  > "A bright white dwarf (HZ4) was adopted as a photometric calibration source." (3 AstroSat Data Processing); "where UC is the unit conversion factor derived from the zero-point (ZP) magnitude in the AB system as (cite: tandon20)" (3 AstroSat Data Processing)
   - parameter: Final pixel size 0.42 arcsec using adaptive resampling  
  > "Using the adaptive resampling method in REPROJECT, we can maintain the same pixel scales as the original images." (3 AstroSat Data Processing); "The final images have a pixel size of $0.42\ensuremath{''}$." (3 AstroSat Data Processing)
   - assumption: Only CPS (Poisson) uncertainty propagated; UC errors taken as small  
  > "In this study, we only propagate the uncertainty in CPS as the UC errors are taken to be small." (3 AstroSat Data Processing)
   - fitting: _not stated_
   - validation: Flux density uncertainty of 5% per filter  
  > "These uncertainties yield $5\%$ uncertainty in the flux density for each filter (cite: Singh2021)." (3 AstroSat Data Processing)
2. **Estimate and subtract the UV background**: Fit radial profile of each galaxy with an exponential disk plus constant background; fall back to a mean-level annulus estimate with Chauvenet rejection where the fit fails  
  > "We estimate the background by assuming the galaxy emission profile is an exponential disk (cite: Regan_2001) and include a constant background term:" (3.1 Background subtraction); "We reject bright sources using Chauvenet’s criterion in the annulus data distribution" (3.1 Background subtraction)
   - software: astropy.stats
   - parameter: Annuli of 500 pc width out to <50 kpc; bar region excluded at 1.3 x R_Bar  
  > "We determine the radial profiles by averaging the flux in annuli with widths of 500 pc from the center of the galaxy up to a maximum galactocentric distance of $<50$ kpc." (3.1 Background subtraction); "we exclude the bar region from the radial profile by using a radius of $1.3\times R_{\mathrm{Bar}}$" (3.1 Background subtraction)
   - parameter: Same exponential model applied to CO with B = 0 to derive CO scale lengths  
  > "we apply the same exponential model to the CO emission, fixing $B=0$" (3.1 Background subtraction)
   - assumption: Mean-level backgrounds used for NGC 0300, NGC 3621, NGC 5128, NGC 1512 (and NGC 0253); NGC 6744 background from hand-picked 1.5 arcmin apertures  
  > "In the cases of NGC 3621 and NGC 5128, we decided not to use the regression to determine the background level due to a number of nearby bright sources." (3.1 Background subtraction)
   - fitting: Regression of exponential-plus-constant model with parameters confined to an initial range; optimizer and bounds not stated  
  > "We also observe that the obtained parameters of this galaxy, such as FUV scale length, amplitude, and background, are close to being outside of the reasonable range that we confined our initial regression parameters to." (4.2 New candidates)
   - validation: Maximum radius chosen by visual inspection  
  > "This maximum distance is chosen through visual inspection of different galaxies to exclude any bright nearby sources." (3.1 Background subtraction)
3. **Correct for Milky Way foreground extinction**: A_lambda = R_lambda E(B-V) with R from Peek & Schiminovich (2013) and SFD98 E(B-V)  
  > "The extinction is estimated using $A_{\lambda} = R_{\lambda}\, E(B-V)$ at the FUV and NUV wavelengths." (3.2 Foreground extinction)
   - assumption: Uniform foreground dust across each target  
  > "A uniform foreground dust distribution is expected due to the small angular size of each target." (3.2 Foreground extinction)
   - fitting: _not stated_
   - validation: _not stated_
4. **Quality assurance: PSF, astrometry, GALEX flux scale**: Stack Gaia-matched point sources and fit a Moffat PSF; check astrometry against HST F275W; compare AstroSat to GALEX at 7.5 arcsec using OLS line fits  
  > "To measure the PSF, we identify point sources in the image, stack the images, and fit a Moffat PSF model (cite: MoffatProfile) to the resulting image stack." (3.3.1 Resolution and Alignment); "Ordinary Least Squares (OLS) regression, we also fit a line to average of every 30 pixel values" (3.3.2 Comparison with GALEX)
   - software: photutils, scikit-learn, astropy.stats
   - parameter: Image smoothed with Gaussian of 2 pixel sigma, then DAO Star Finder  
  > "First, we smooth the image with a Gaussian kernel with a standard deviation of 2 pixels." (3.3.1 Resolution and Alignment); "We then identify point sources using the DAO Star Finder algorithm (cite: Stetson87) as implemented in the PHOTUTILS package (cite: photutils) in PYTHON." (3.3.1 Resolution and Alignment)
   - parameter: GALEX pixels below 5 sigma RMS masked; later masking below 3 sigma for both  
  > "Pixel values below 5$\sigma$ RMS are masked using the ASTROPY.STATS.SIGMA-CLIPPED-STATS module on GALEX maps." (3.3.2 Comparison with GALEX)
   - fitting: 2D Moffat profile to stacked stars; OLS slope and offset of AstroSat vs GALEX  
  > "We stack the extracted sources on the maximum brightness pixel to form a single representative star image and fit a two-dimensional Moffat profile to the resulting stack." (3.3.1 Resolution and Alignment)
   - validation: Astrometry better than 0.4 arcsec vs HST; F148W vs GALEX FUV agree at ~10 percent  
  > "In all cases, we find better than $0.4''$ accuracy in the astrometric alignment." (3.3.1 Resolution and Alignment)
5. **Measure FUV and CO scale lengths and identify XUV disk candidates**: Compare FUV and CO exponential scale lengths; apply a FUV surface-brightness threshold to find UV clumps beyond the optical disk  
  > "we measured the scale lengths of FUV emission and CO molecular gas." (4.2 New candidates); "we used a foreground-extinction-corrected, background-subtracted UV surface brightness ($\mu_\mathrm{FUV}$=27.25 AB magnitudes arcsec$^{-2}$) as a threshold level to identify FUV clumps in XUV disks." (4.2 New candidates)
   - parameter: mu_FUV = 27.25 AB mag/arcsec^2 threshold, equal to Sigma_SFR = 3e-4 Msun/yr/kpc^2  
  > "This UV surface brightness corresponds to $\Sigma_\mathrm{SFR}$= $3\times10^{-4}$ M$_{\odot}$ yr$^{-1}$ kpc$^{-2}$, which is based on a Salpeter IMF and calibrations from (cite: Kennicutt98)." (4.2 New candidates)
   - assumption: Salpeter IMF; Thilker (2007) Type 1/Type 2 XUV classification  
  > "Following the prescriptions of (cite: Thilker2007) and (cite: Lemonias2011)" (4.2 New candidates)
   - fitting: _not stated_
   - validation: _not stated_
6. **Measure clumping factor and Gini coefficient of FUV and CO**: Compute clumping factor and Gini coefficient of FUV and CO maps at 175 pc and in 1 kpc hexagonal apertures within environment masks; compare distributions with K-S tests  
  > "We use the environment masks from (cite: mask) to measure the clumping factor in different morphological regions of galaxies." (5.1 Clumping Factor); "To analyze the differences between these two distributions further, we applied the Kolmogorov-Smirnov (K-S) statistics." (5.1 Clumping Factor)
   - parameter: Common resolution of 175 pc; also 1 kpc hexagonal apertures  
  > "carry out the analysis at a common resolution of 175 pc." (5.1 Clumping Factor)
   - fitting: _not stated_
   - validation: Comparison with Sun et al. (2022) CO clumping factor in hexagonal apertures  
  > "Our results are in good agreement with (cite: Sun_2022), where they used highly-sensitive ALMA observations of 90 nearby galaxies and reported $c_\mathrm{CO}=1.9$ within hexagonal apertures." (5.1 Clumping Factor)
7. **Regress log FUV/Halpha on physical drivers (LASSO) and simplified models**: LASSO multivariate regression in log space at 175 pc and 1 kpc with E(B-V), I_CO, Halpha EW, stellar age, mass, metallicity and environment flags; simplified one- to three-parameter fits  
  > "We use the Least Absolute Shrinkage and Selection Operator regression (cite: lasso_paper) to understand how each predictor control the variation of the log ratio." (6.3.1 Drivers of the FUV/Halpha Ratio); "We aim to predict log FUV/H$\alpha$ using variables such as E$(B-V)$, $I_\mathrm{CO}$, H$\alpha$ EW, stellar age, mass, and metallicity using the panchromatic PHANGS data." (6.3.1 Drivers of the FUV/Halpha Ratio)
   - parameter: 5-fold cross-validation to tune regularization alpha; Halpha EW used as weighting factor  
  > "Following (cite: day), we use 5-fold cross-validation (CV) to fine-tune the hyperparameters of the model" (6.3.1 Drivers of the FUV/Halpha Ratio); "we have incorporated the EW of H$\alpha$ emission as a weighting factor in the LASSO analysis." (6.3.1 Drivers of the FUV/Halpha Ratio)
   - assumption: Linear relationship in log space between each predictor and the outcome  
  > "we assume a linear relationship in log space between each predictor and the outcome variable" (6.3.1 Drivers of the FUV/Halpha Ratio)
   - fitting: LASSO with cross-validated penalty; coefficient errors from bootstrap resampling  
  > "we employ a bootstrap resampling method. This approach involves generating multiple bootstrap samples by repeating the same LASSO regression with cross-validation." (6.3.1 Drivers of the FUV/Halpha Ratio)
   - validation: Bootstrap standard deviations on coefficients below 0.1 at 1 kpc and below 0.01 at 175 pc  
  > "Our findings reveal that the standard deviation on $\alpha_i$ at a scale of 1 kpc is below 0.1 for all predictors." (6.3.1 Drivers of the FUV/Halpha Ratio)
8. **Dust-correct FUV and Halpha and test age dependence**: Measure UV slope beta from FUV and NUV for five galaxies, correct FUV via Boquien et al. (2012), correct Halpha with Balmer decrement and E(B-V), regress at 1 kpc on age, stellar mass surface density and metallicity, then partial regression residual vs age  
  > "Using the available NUV AstroSat observations for five of our targets, we first measure the slope of the UV continuum ($\beta$) to correct the FUV emission for internal attenuation." (6.4 Dust attenuation correction to FUV/Halpha)
   - parameter: R_V = 3.1 for Halpha correction  
  > "based on a typical value of the total-to-selective value $R_{V}=3.1$ (cite: Calzetti2000; Belfiore)" (6.4 Dust attenuation correction to FUV/Halpha)
   - assumption: R_V = 3.1 (Calzetti 2000 curve cited)  
  > "based on a typical value of the total-to-selective value $R_{V}=3.1$ (cite: Calzetti2000; Belfiore)" (6.4 Dust attenuation correction to FUV/Halpha)
   - fitting: Linear regression of attenuation-corrected log ratio on age, Sigma_star, [Z/H]  
  > "We found that this model can describe the variation of the dust-attenuation corrected log ratio with an $R^{2} = 0.49$." (6.4 Dust attenuation correction to FUV/Halpha)
   - validation: _not stated_

## Software

- **CCDLAB** : UVIT Level-2 processing and astrometric solution  
  > "and the Level-2 data were processed with the CCDLAB software package (cite: postma17)." (3 AstroSat Data Processing)
- **AstroSat UVIT pipeline** v2.1 and v2.2: Level-1 data products  
  > "The Level-1 data products were generated using v2.1 and v2.2 of the" (3 AstroSat Data Processing)
- **REPROJECT** : Reprojecting images to cardinal axes (adaptive resampling) and to GALEX grid  
  > "We align each image along the cardinal directions by reprojecting with the REPROJECT python package" (3 AstroSat Data Processing)
- **photutils (DAO Star Finder)** : Point-source detection for PSF measurement  
  > "We then identify point sources using the DAO Star Finder algorithm (cite: Stetson87) as implemented in the PHOTUTILS package (cite: photutils) in PYTHON." (3.3.1 Resolution and Alignment)
- **astropy.stats** : MAD standard deviation and sigma-clipped statistics  
  > "Pixel values below 5$\sigma$ RMS are masked using the ASTROPY.STATS.SIGMA-CLIPPED-STATS module on GALEX maps." (3.3.2 Comparison with GALEX)
- **scikit-learn** : OLS regression of AstroSat vs GALEX pixel values  
  > "Using SKLEARN.LINEAR_MODEL module" (3.3.2 Comparison with GALEX)
- **numpy** : Listed in Software section; specific use not stated  
  > "numpy (cite: numpy)" (Software)
- **spectral-cube** : Listed in Software section; specific use not stated  
  > "spectral-cube (cite: spectral-cube)" (Software)
- **matplotlib** : Listed in Software section (plotting implied; not stated)  
  > "and matplotlib (cite: matplotlib)" (Software)
- **ChatGPT** : Refining English-language presentation of the paper  
  > "HH acknowledges the use of ChatGPT to refine the English-language presentation of the ideas in this paper." (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median resolution of FUV bands | 1.4 | not stated | arcsec | 4 | The median resolution of the FUV bands is $1.4''$ and the median resolution of the NUV bands is $1.2''$. |
| Median resolution of NUV bands | 1.2 | not stated | arcsec | 4 | The median resolution of the FUV bands is $1.4''$ and the median resolution of the NUV bands is $1.2''$. |
| Flux density uncertainty per filter | 5 | not stated | percent | 1 | These uncertainties yield $5\%$ uncertainty in the flux density for each filter (cite: Singh2021). |
| Median foreground FUV extinction | 0.21 | not stated | mag | 3 | resulting in a median foreground of A$_{\mathrm{FUV}}=0.21$ mag |
| AstroSat F148W vs GALEX FUV slope (median beta) and offset | beta = 0.92, C = 0.001 MJy/sr | not stated | dimensionless (slope); MJy/sr (offset) | 4 | with a median of $\beta=0.92$ and with an offset of $C=0.001$ MJy/sr |
| AstroSat N219M vs GALEX NUV slope and offset | beta = 0.83, C = 0.002 MJy/sr | not stated | dimensionless (slope); MJy/sr (offset) | 4 | In the NUV, we found a median of $\beta=0.83$ and $C=0.002$ MJy/sr among targets at N219M band |
| Average FUV scale length | ~3500 | not stated | pc | 5 | On average, the scale length of FUV ($\gamma_\mathrm{FUV} \simeq 3500$ pc) is about twice that of CO molecular gas. |
| NGC 6744 FUV and CO scale lengths | gamma_FUV = 9 kpc; gamma_CO = 3.8 kpc | likely underestimated (not quantified) | kpc | 5 | NGC 6744 possesses the largest scale length, with $\gamma_{\mathrm{FUV}}=9$ kpc and $\gamma_{\mathrm{CO}}=3.8$ kpc. |
| Median clumping factor in galaxy centers, FUV and CO | FUV 1.51; CO 1.35 | not stated | dimensionless | 6 | The median of the FUV clumping factor is 1.51, whereas the clumping factor for CO is 1.35 in the center of galaxies. |
| K-S statistic FUV vs CO clumping in centers | 0.4 (p = 0.04) | not stated | dimensionless | 6 | This analysis resulted in a KS value of 0.4 in the center, indicating a modestly significant difference between the distributions with a p-value of 0.04. |
| Median clumping factor in spiral arms, FUV and CO | FUV 2.7; CO 2.5 | not stated | dimensionless | 6 | the median clumping factor is $c=2.7$ for the FUV and $c=2.5$ for CO. |
| Median clumping factor in 1 kpc hexagonal apertures, CO and FUV | CO 1.7; FUV 1.3 | 0.1 (each) | dimensionless | 6 | the median CO clumping factor is still higher ($c=1.7 \pm 0.1$) than the FUV values ($c=1.3 \pm 0.1$). |
| Median Gini coefficient in 1 kpc apertures, CO and FUV | CO 0.43; FUV 0.3 | not stated | dimensionless | 6 | our measurements of $G_{\rm CO}=0.43$ are higher than $G_{\rm FUV}=0.3$ |
| Median log(FUV/Halpha) at 1 kpc in hexagonal apertures (uncorrected) | 2.1 | not stated | dimensionless (log ratio) | 7 | At the coarser 1 kpc resolution, the log ratio exhibits a median of 2.1 within hexagonal apertures for all targets. |
| Median log(FUV/Halpha) in galaxy centers | 1.7 | not stated | dimensionless (log ratio) | 7 | The centers of galaxies have a median of $\log(\mathrm{FUV/H}\alpha) = 1.7$, the lowest among all environments |
| Center log ratio, AGN vs non-AGN galaxies | AGN 1.13; non-AGN 1.88 | not stated | dimensionless (log ratio) | 7 | also exhibit a lower log ratio (1.13) compared to non-AGN galaxies (1.88) in the center |
| Full LASSO model R^2 at 175 pc and 1 kpc | approximately 0.65 | not stated | dimensionless | 7 | achieving approximately $R^{2}\sim0.65$. |
| E(B-V)-only model: coefficient and R^2 at 175 pc | coefficient approx -1.7; R^2 = 0.5 | 0.01 (Table 5: -1.68 +/- 0.01) | dimensionless | 7 | This resulted in dust reddening coefficients of approximately $-1.7$ at 175 pc scale. The goodness of fit, represented by $R^{2}$, yielded values of 0.5. |
| CO-only model R^2 and coefficient | R^2 = 0.4; coefficient -0.4 | not stated | dimensionless | 7 | a standalone model of CO can predict the log ratio as effectively as a single reddening component, with an $R^{2}$ of 0.4. |
| Spearman rank correlation between CO and E(B-V) at kpc scale | ~0.75 | not stated | dimensionless | 7 | supported by a Spearman rank coefficient of $\rho \approx 0.75$ |
| Attenuation-corrected model R^2 at 1 kpc (age, Sigma_star, [Z/H]) | 0.49 | not stated | dimensionless | 8 | We found that this model can describe the variation of the dust-attenuation corrected log ratio with an $R^{2} = 0.49$. |
| Attenuation-corrected model coefficients: age, Sigma_star, [Z/H], intercept | 0.84, -1.39, 0.33, alpha_0 = 2.98 | 0.02 each (Table 5) | dimensionless | 8 | Our results show coefficients of 0.84 for age, $-1.39$ for the stellar mass surface density, and 0.33 for the stellar metallicity, along with an intercept of $\alpha_0 = 2.98$ |

## Qualitative findings

- NGC 6744 proposed as a new Type 1 XUV disk and IC 5332 as a Type 2 candidate  
  > "we propose that NGC 6744 is a Type 1 XUV-disk" (4.2 New candidates); "The origin of the IC 5332 XUV emission remains unclear, but this target remains a candidate for an XUV disk." (4.2 New candidates)
- Bars and spiral arms are the most clumped environments  
  > "We find that bars and spiral arms exhibit the highest degree of clumping" (abstract)

## Claim tuples

- H: The reduced AstroSat UVIT maps have a flux scale consistent with GALEX | E: Convolve and reproject AstroSat maps to GALEX resolution, fit AstroSat vs GALEX pixel values with OLS | R: F148W vs GALEX FUV median slope 0.92, offset 0.001 MJy/sr; N219M vs GALEX NUV slope 0.83 | F: Flux scales agree within about 10 percent | **supported**
- H: Large FUV-to-CO scale length ratios identify new extended UV (XUV) disk galaxies | E: Exponential fits to FUV and CO radial profiles plus a UV surface-brightness threshold | R: NGC 6744 (gamma_FUV = 9 kpc, gamma_CO = 3.8 kpc) and IC 5332 show FUV-bright structures beyond the optical disk | F: NGC 6744 and IC 5332 are new XUV disk candidates | **partially**
- H: FUV emission is clumped differently from molecular gas traced by ALMA CO | E: Clumping factor and Gini coefficient of FUV and CO at 175 pc and 1 kpc in environment masks | R: Median c(CO) = 1.7 vs c(FUV) = 1.3 in 1 kpc apertures; G(CO) = 0.43 vs G(FUV) = 0.3 | F: CO is more clumped than FUV overall, except in centers and spiral arms where FUV clumping is slightly higher; bars are most clumped | **supported**
- H: Dust attenuation and star formation history parameters explain variation in log FUV/Halpha | E: LASSO regression and simplified models at 175 pc and 1 kpc using PHANGS-ALMA and PHANGS-MUSE products | R: Full model R^2 ~ 0.65; E(B-V) alone gives R^2 = 0.5 | F: Dust attenuation is the dominant factor controlling the log ratio | **supported**
- H: After dust correction, FUV/Halpha traces stellar population age | E: Correct FUV with UV slope and Halpha with Balmer decrement in five galaxies, remove Sigma_star and metallicity dependence, compare residual with age | R: Regression with age, Sigma_star, [Z/H] gives R^2 = 0.49; positive residual correlation with age | F: A positive correlation emerges between the corrected ratio and stellar age | **supported**

## Reasoning

- Why this data: Galaxies already in the PHANGS survey were chosen so UV data complement ALMA, MUSE, HST data  
  > "To maximize the opportunity for multiwavelength science, we selected galaxies that have been observed as part of the PHANGS survey" (2.1 Sample Selection)
- Why this method: Moffat model chosen for PSF because it describes bright-source PSFs with a core and extended wings  
  > "We adopt the Moffat PSF model since it appears to characterize the PSF of bright sources well" (3.3.1 Resolution and Alignment)
- Alternative: Other interpolation and flux-conserving reprojection methods rejected because they produced Moire artifacts  
  > "Other interpolation and flux conserving methods produced a Moiré artifact pattern in the reprojected image" (3 AstroSat Data Processing)
- Alternative: Radial-profile regression for background rejected for NGC 3621 and NGC 5128 in favour of mean-level estimates  
  > "In the cases of NGC 3621 and NGC 5128, we decided not to use the regression to determine the background level due to a number of nearby bright sources." (3.1 Background subtraction)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA maps cover only the inner disk  
  > "ALMA maps only cover the infrared-bright portion of the inner disk ($R_\mathrm{gal}=5-6\,$kpc) of our targets." (2.3.1 PHANGS-ALMA)
- Limitation (authors): Exponential fit uncertain for NGC 6744; scale-length error likely underestimated  
  > "We note that the radial profile of this galaxy is not exponential, which has resulted in poor regression results, and hence the uncertainty is likely underestimated." (4.2 New candidates)
- Limitation (authors): Collinearity among regression predictors  
  > "we anticipate colinearity between parameters, particularly between $E(B-V)$ and CO intensity, or age and metallicity." (6.3.1 Drivers of the FUV/Halpha Ratio)
- Limitation (authors): Gini coefficient in disks inflated by ALMA noise at 175 pc  
  > "We note that the high clumpiness measured by Gini in disks are due to the high level of noise in ALMA data at 175 pc." (5.2 Gini coefficient)
- Caveat (inferred, ours): NGC 6744 FUV scale length of 9 kpc is quoted in the text but the table lists no gamma_FUV for it (mean-level/aperture background used)
- Caveat (inferred, ours): ALMA is only a comparison data set; no ALMA calibration or imaging is reproduced here, so ALMA-related results depend on Leroy2021 products
- Caveat (inferred, ours): LASSO coefficients are affected by collinearity and by the assumed log-linear form, and the age coefficient is counter-intuitive
- Caveat (inferred, ours): Quoted regression R^2 and residual values at 175 pc and 1 kpc depend on masks and aperture choices not fully specified

## Reproducibility

- Data public (paper): AstroSat archival data from the AstroSat archive; reduced atlas released online; ALMA data public status not stated in this paper  
  > "We supplement these observations with additional archival data for 20 additional PHANGS targets" (2.2 Observations); "The PHANGS-AstroSAT atlas is available online" (Conclusion)
- Products in archive: PHANGS-ALMA released products (moment maps, masks, uncertainty maps); AstroSat atlas at CANFAR  
  > "Final data products are released using two different signal-selection masks" (2.3.1 PHANGS-ALMA)
- Missing: ALMA project codes and PHANGS-ALMA product version
- Missing: Per-galaxy CCDLAB reduction settings, zero points and pipeline version
- Missing: Regression bounds and per-galaxy radial fit settings
- Missing: Exact aperture and masking definitions and noise cuts
- Missing: LASSO alpha grid and bootstrap count
- Missing: No analysis code released
- Data volume (inferred): Tens of GB: AstroSat UVIT images for 31 galaxies plus PHANGS-ALMA CO moment maps and MUSE maps (derived products, not raw visibilities).
- Score (inferred): 3/5, Inputs are public derived products and many numeric results are given, but ALMA processing is deferred to another paper, and reduction/fit/mask settings are incompletely specified, with no code released.
- Rediscovery candidate: no, ALMA is a minor ancillary input and the AstroSat reduction recipe is not complete enough to redo from the paper alone.

## Links

- Method: Leroy2021 (PHANGS-ALMA calibration, imaging and masks that this paper inherits)
- Method: phangs-muse (Source of MUSE emission-line and stellar-population maps)
- Method: postma17 (CCDLAB UVIT data processing)
- Method: tandon20 (UVIT in-orbit calibration)
- Method: Leroy_2013; Sun_2022 (Clumping factor definition)
- Method: z0mgs (GALEX/WISE maps and extinction procedure)
- Companion: Leroy2021 (PHANGS-ALMA CO(2-1) survey and galaxy sample properties)
- Companion: phangs-hst (PHANGS-HST UV imaging used for astrometric check)
- Related: PHANGS-ALMA
- Related: PHANGS-MUSE
- Related: PHANGS-HST
- Related: PHANGS-JWST
- Related: z0MGS
- Related: GALEX
- Related: AstroSat UVIT

## Checks

```json
{
 "quotes": 137,
 "quotes_ok": 137,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00650.S",
  "2013.1.00803.S",
  "2013.1.01161.S",
  "2015.1.00121.S",
  "2015.1.00782.S",
  "2015.1.00925.S",
  "2015.1.00956.S",
  "2016.1.00386.S",
  "2017.1.00392.S",
  "2017.1.00766.S",
  "2017.1.00886.L",
  "2018.1.00484.S",
  "2018.1.01321.S",
  "2018.1.01651.S",
  "2018.A.00062.S",
  "2019.2.00129.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 22,
 "numeric_problems": 0,
 "fill": {
  "facts": 118,
  "stated": 85,
  "rate": 0.72
 },
 "evidence_ok": true
}
```
