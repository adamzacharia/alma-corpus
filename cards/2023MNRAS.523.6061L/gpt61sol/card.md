# Multiscale stellar associations across the star formation hierarchy in PHANGS-HST nearby galaxies: methodology and properties

`2023MNRAS.523.6061L` | Monthly Notices of the Royal Astronomical Society 2023 | first author: Larson, Kirsten L. | arXiv: 2212.11425 | DOI: 10.1093/mnras/stad1600

Card schema 1.0 | model gpt-6.1-sol | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, nearby_galaxies
- Question: Identify multi-scale stellar associations and compare their properties and spatial distribution with clusters, Hα emission, and molecular clouds.  
  > "We desire to trace the structures at multiple physical scales in the hierarchy in a way that easily allows for comparisons between multiple galaxies and joint analysis of molecular clouds and H II regions." (Introduction)
- Target **NGC 3351**: coordinates RA 160.99065 deg; Dec 11.70367 deg  
  > "| NGC 3351 | 160.99065 | 11.70367 | 10 | 1.88e10 (0.10 dex) | 1.2 (0.2) | Sb |" (Sample & Data); "NGC 3351 (10 Mpc), NGC 1566 (18 Mpc)." (Abstract); z/distance 10 Mpc  
  > "| NGC 3351 | 160.99065 | 11.70367 | 10 | 1.88e10 (0.10 dex) | 1.2 (0.2) | Sb |" (Sample & Data); "NGC 3351 (10 Mpc), NGC 1566 (18 Mpc)." (Abstract); distance from _not stated_
- Target **NGC 1566**: coordinates RA 65.00159 deg; Dec -54.93801 deg  
  > "| NGC 1566 | 65.00159 | $-$54.93801 | 18 | 4.56e10 (0.10 dex) | 4.4 (0.2) | SABb |" (Sample & Data); "NGC 3351 (10 Mpc), NGC 1566 (18 Mpc)." (Abstract); z/distance 18 Mpc  
  > "| NGC 1566 | 65.00159 | $-$54.93801 | 18 | 4.56e10 (0.10 dex) | 4.4 (0.2) | SABb |" (Sample & Data); "NGC 3351 (10 Mpc), NGC 1566 (18 Mpc)." (Abstract); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00925.S, 2015.1.00956.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ALMA beam: NGC 3351, 71 pc; NGC 1566, 110 pc  
  > "The ALMA beam size for NGC 3351 is $71$ pc while the beam for the more distant NGC 1566 is $110$ pc." (Comparison to Molecular Cloud Population)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 2–1 (not stated)
- Other facility **HST / PHANGS–HST / LEGUS**: F275W, F336W, F438W, F555W, F814W imaging with WFC3 or ACS  
  > "all galaxies in the PHANGS–HST programme have *HST* F275W (NUV), F336W (U), F438W (B), F555W (V), and F814W (I) imaging with Wide Field Camera 3 (WFC3) or Advanced Camera for Surveys (ACS)" (Sample & Data)
- Other facility **PHANGS–Hα**: Hα images for an independent check on association definition and ages  
  > "We compare the spacial distribution of stellar associations to H$\alpha$ images from the PHANGS–H$\alpha$ survey (Razza et al. in prep.) as an independent check on our association definition and age estimates." (Comparison to H II Region Population)
- Other facility **Digitized Sky Survey**: Background images for HST, MUSE, and ALMA footprints  
  > "shows the footprints of the HST imaging together with those for the MUSE and ALMA CO maps, overlaid on Digitized Sky Survey images" (Sample & Data)
- Other facility **Mikulski Archive for Space Telescopes**: GO-15654 data, science ready mosaicked imaging, multi-scale association regions and calculated properties  
  > "The data underlying this article can be retrieved from the Mikulski Archive for Space Telescopes" (Data Availability); "including science ready mosaicked imaging associated with HST GO-15654 with digital object identifier and all multi-scale association regions and calculated properties developed in this paper." (Data Availability)
- External data: PHANGS molecular cloud catalogues and velocity-collapsed CPROPS maps  
  > "We use the molecular cloud catalogues developed by the PHANGS project using PYCPROPS, an updated version of the CPROPS algorithm (cite: rosolowsky06), described in detail in (cite: rosolowsky21)." (Comparison to Molecular Cloud Population); "Full details on the construction of the CPROPS molecular cloud catalogues and associated maps are given in (cite: rosolowsky21)." (Comparison to Molecular Cloud Population) [from (cite: rosolowsky21)]
- External data: Public LEGUS star cluster catalogues for both galaxies  
  > "LEGUS star cluster catalogues have also been publicly released for both galaxies (cite: adamo17)" (Introduction) [from (cite: adamo17)]
- External data: Galaxy stellar masses and star formation rates  
  > "NGC 3351 is an Sb spiral galaxy with a mass of $1.88\times 10^{10}$ M$_\odot$ and a star formation rate (SFR) of $1.165$ M$_\odot$ yr$^{-1}$ (cite: leroy21a)." (Sample & Data); "This potentially follows from the higher SFR values quoted by (cite: leroy21a)" (Number of regions identified and their sizes) [from (cite: leroy21a)]
- External data: Padova stellar model tracks  
  > "the Padova stellar model tracks" (Selection of Tracer Stars); "(cite: girardi02; marigo08)" (Selection of Tracer Stars) [from (cite: girardi02; marigo08)]
- External data: BC03 single-aged population synthesis models  
  > "The fitting is based on the single-aged population synthesis models of (cite: bruzual03)" (SED Fitting) [from (cite: bruzual03)]
- External data: Chabrier IMF, mass limits 0.1–100 M⊙  
  > "a (cite: chabrier03) initial mass function (IMF; with standard mass limits of $0.1{-}100$ M$_{\odot}$)" (SED Fitting) [from (cite: chabrier03)]
- External data: Cardelli extinction curve, R_V = 3.1  
  > "The (cite: cardelli89) extinction curve with $R_\mathrm{V} = 3.1$ is used" (SED Fitting) [from (cite: cardelli89)]
- Simulation/model as data: Solar-metallicity BC03 SSP models for colours and SED fitting  
  > "the solar metallicity single-aged stellar population (SSP) models from (cite: bruzual03)" (Selection of Tracer Stars); "The fitting is based on the single-aged population synthesis models of (cite: bruzual03), assuming solar metallicity" (SED Fitting)
- Simulation/model as data: Composite stellar populations with exponentially declining SFR, τ = 2 and 4 Myr  
  > "We also compare to composite stellar populations (CSPs) that are formed from exponentially declining star formation rate, $\mathrm{SFR}(t) \sim \mathrm{exp}(-t/\tau)$, with both $\tau$ of $2$ and $4$ Myr." (Colors)
- Simulation/model as data: Padova stellar model tracks for tracer colour comparison  
  > "the Padova stellar model tracks" (Selection of Tracer Stars); "Most of the tracer stars lie redward of the Padova stellar tracks." (Selection of Tracer Stars)

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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- DOLPHOT source catalogues from the PHANGS–HST catalogue pipeline  
  > "Our analysis makes use of DOLPHOT source catalogues, which are produced as the first step in the overall PHANGS–HST catalogue pipeline (cite: lee22)." (Sample & Data) [from (cite: lee22)]
- DOLPHOT catalogue production and adopted parameters  
  > "(cite: thilker22) provides a detailed description of the production of DOLPHOT catalogues for PHANGS–HST and lists the adopted DOLPHOT parameters." (Sample & Data) [from (cite: thilker22)]
- CIGALE augmentations for single-aged populations and detailed modelling assumptions  
  > "Augmentations to CIGALE have been made to enable fitting of single-aged stellar populations as described in (cite: turner21)." (SED Fitting); "A more detailed description of the assumptions in the modelling can be found in (cite: turner21)." (SED Fitting) [from (cite: turner21)]
- PYCPROPS cloud catalogues and associated maps  
  > "Full details on the construction of the CPROPS molecular cloud catalogues and associated maps are given in (cite: rosolowsky21)." (Comparison to Molecular Cloud Population) [from (cite: rosolowsky21)]

### Not stated but needed to reproduce (our reading)

- Exact PHANGS–ALMA cloud catalogue and velocity-collapsed map release identifiers.
- Map registration, reprojection, pixel grid, and interpolation used for the HST–CPROPS pixel comparison.
- Exact joint-coverage masks and treatment of partially covered association or cloud regions.
- Minimum shared-pixel criterion for counting a region as overlapping.
- DOLPHOT parameter files and foreground-star masks.
- Gaussian convolution boundary handling and scikit-image version.
- CIGALE age and reddening grids, version, and single-population augmentation code.
- ALMA calibration, imaging, sensitivity, and spectral setup if rebuilding the molecular cloud maps from observations.

## Analysis recipe

1. **Select tracer sources**: Select NUV and V tracer sources from DOLPHOT catalogues; exclude foreground stars.  
  > "The first step is to select point sources from the DOLPHOT source catalogues to serve as ‘tracer’ stars" (Selection of Tracer Stars); "We perform our analysis using both *NUV* and *V*-band light as the detection band for the DOLPHOT stellar catalogues." (Selection of Tracer Stars); "Additionally, foreground galactic stars are masked out and excluded from the tracer stars for both and *V*-band selection." (Selection of Tracer Stars)
   - software: DOLPHOT
   - parameter: NUV S/N > 7; sharpness² < 0.15; quality flag < 4  
  > "*NUV*-band signal-to-noise $> 7$" (Selection of Tracer Stars); "*NUV*-band sharpness$^2 < 0.15$" (Selection of Tracer Stars); "*NUV*-band quality flag $< 4$" (Selection of Tracer Stars)
   - parameter: NUV selection also requires U-band S/N > 3  
  > "U-band signal-to-noise $> 3$." (Selection of Tracer Stars)
   - parameter: V S/N > 7; sharpness² < 0.15; quality flag < 4  
  > "*V*-band signal-to-noise $> 7$" (Selection of Tracer Stars); "*V*-band sharpness$^2 < 0.15$" (Selection of Tracer Stars); "*V*-band quality flag $< 4$" (Selection of Tracer Stars)
   - parameter: V selection also requires B-band S/N > 3 and V-band flux/sky level ≥ 2.0  
  > "B-band signal-to-noise $> 3$" (Selection of Tracer Stars); "an additional criterion to remove objects with high local sky background." (Selection of Tracer Stars); "$\ge 2.0$." (Selection of Tracer Stars)
   - assumption: Tracer objects may include double stars or unresolved clusters  
  > "Since the goal is to find stellar associations, it is acceptable for our purposes if some of the tracer objects are in fact double stars or even unresolved clusters." (Selection of Tracer Stars)
   - fitting: _not stated_
   - validation: Compare tracer colours with Padova stellar tracks and BC03 SSP models  
  > "Most of the tracer stars lie redward of the Padova stellar tracks." (Selection of Tracer Stars); "the solar metallicity single-aged stellar population (SSP) models from (cite: bruzual03)" (Selection of Tracer Stars)
2. **Construct density maps**: Create binary source-position maps, Gaussian smooth, then subtract a map smoothed at four times the scale.  
  > "The position map has a value of one at the pixel position of the tracer stars and a value of zero at all other pixels." (Tracer Star Maps); "Gaussian kernel density maps are then created by smoothing the position map with a Gaussian profile with different full-width-half-maximum (FWHM): 8, 16, 32, 64, 128, and 256 pc" (Tracer Star Maps); "is created by subtracting a map which is smoothed to 64 pc (a scale 4 times larger)." (Tracer Star Maps)
   - parameter: Minimum smoothing: 8 pc for NGC 3351; 16 pc for NGC 1566  
  > "A lower limit in the smoothing level is set for each galaxy dependent on the galaxy’s distance: 8 pc for NGC 3351 and 16 pc for NGC 1566." (Tracer Star Maps)
   - parameter: 4 times high-pass filter  
  > "Therefore, we will use the 4 times high-pass filter as our fiducial choice." (High-pass filtering)
   - assumption: Distances: NGC 3351, 10 Mpc; NGC 1566, 18 Mpc  
  > "NGC 3351 (10 Mpc), NGC 1566 (18 Mpc)." (Abstract)
   - fitting: _not stated_
   - validation: Compare unfiltered, 4 times, and 8 times filtered size distributions; choose tighter, less overlapping distributions.  
  > "Both of the high-pass filtered images therefore have a tighter distribution of sizes than the unfiltered image" (High-pass filtering); "we adopt the smaller filter step which produces a tighter distribution of region sizes." (High-pass filtering)
3. **Segment associations**: Seeded watershed segmentation with local-maxima markers and an edge-threshold image mask  
  > "We use the seeded watershed routine from the publicly available python package scikit-image (SKIMAGE.SEGMENTATION.WATERSHED) to define our stellar associations." (Watershed Parameters); "We define our marker positions as the local maxima of the smoothed, filtered tracer star map using the routine SKIMAGE.FEATURE.PEAK_LOCAL_MAX." (Watershed Parameters)
   - software: scikit-image, SKIMAGE.SEGMENTATION.WATERSHED, SKIMAGE.FEATURE.PEAK_LOCAL_MAX
   - parameter: Peak threshold: 1.5 times the maximum for a single object  
  > "We define the peak threshold to be $1.5$ times the maximum value for a single object to ensure that there will be at least two point-like sources per region." (Watershed Parameters)
   - parameter: Edge threshold: surface brightness at the FWHM of a single object  
  > "We use an edge threshold equal to the surface ‘brightness’ at the FWHM of a single object." (Watershed Parameters)
   - parameter: Minimum distance between maxima: FWHM of a single object  
  > "We set the minimum allowed distance between maxima equal to the FWHM of a single object." (Watershed Parameters)
   - fitting: _not stated_
   - validation: Check size distributions against the defining Gaussian FWHM  
  > "The sizes peak near the defining Gaussian FWHM used to create the tracer star maps for each scale level (8, 16, 32, and 64 pc)" (Number of regions identified and their sizes)
4. **Measure association photometry**: Sum all enclosed DOLPHOT PSF photometry and propagate individual-source photometric errors.  
  > "The PSF photometry of the stellar associations is found by summing DOLPHOT PSF photometry from all the DOLPHOT sources contained within the region." (Stellar Association Photometry); "The photometric error for the associations is calculated by propagating the DOLPHOT photometry errors for the individual sources." (Stellar Association Photometry)
   - software: DOLPHOT
   - parameter: Use all DOLPHOT sources, not just selected tracers  
  > "the PSF photometry uses all DOLPHOT sources." (Stellar Association Photometry); "No additional selection criteria are applied to the DOLPHOT sources." (Stellar Association Photometry)
   - parameter: DOLPHOT iteratively fitted 5 times  
  > "DOLPHOT is iteratively fitted 5 times." (Stellar Association Photometry)
   - assumption: No aperture correction or additional local background subtraction for PSF photometry  
  > "Since the DOLPHOT photometry is PSF fitted and represents the total flux for that object, it does not require an aperture correction or local background subtraction which can be difficult in crowded environments." (Stellar Association Photometry)
   - fitting: DOLPHOT PSF fitting  
  > "The DOLPHOT photometry package (cite: dolphin02) uses point spread function (PSF)-fitting to detect and deblend sources in the high-resolution *HST* images." (Sample & Data)
   - validation: Compare PSF sums with regional sky-subtracted pixel photometry  
  > "We compare the the regional sky subtracted pixel photometry to the PSF photometry of the stellar associations." (Stellar Association Photometry)
5. **Infer ages, masses, and reddening**: CIGALE SED fitting of five-band NUV, U, B, V, I photometry  
  > "We compute the ages and masses of our stellar associations using the SED fitting code CIGALE with five-band *NUV, U, B, V, I* photometry as input" (Ages and Masses); "To estimate ages, masses, and reddenings of the stellar associations, the CIGALE SED fitting package (cite: boquien19) is used" (SED Fitting)
   - software: CIGALE
   - parameter: Maximum E(B−V) = 1.5  
  > "a maximum $E(B{-}V) = 1.5$ is imposed." (SED Fitting)
   - assumption: BC03 single-aged populations; solar metallicity  
  > "The fitting is based on the single-aged population synthesis models of (cite: bruzual03), assuming solar metallicity" (SED Fitting)
   - assumption: Chabrier IMF, 0.1–100 M⊙; no nebular emission  
  > "a (cite: chabrier03) initial mass function (IMF; with standard mass limits of $0.1{-}100$ M$_{\odot}$), and no addition of nebular emission." (SED Fitting)
   - assumption: Cardelli extinction curve, R_V = 3.1  
  > "The (cite: cardelli89) extinction curve with $R_\mathrm{V} = 3.1$ is used" (SED Fitting)
   - fitting: Minimum reduced chi-squared SED; no additional age or mass prior weighting  
  > "all of the results presented are based on the best-fitting SED corresponding to the minimum reduced chi-squared value" (SED Fitting); "we do not introduce additional weighting with priors on the age or mass distributions." (SED Fitting)
   - validation: UBVI colour–colour comparison with SSP and CSP tracks  
  > "Determining whether the photometric properties of the structures are consistent with single-age populations in this way provides a sanity-check on the validity of our watershed method for selecting stellar associations, and on whether to proceed with SED fitting with SSP models." (Colors)
6. **Test selection sensitivity**: Repeat NGC 3351 watershed selection at brighter magnitude limits and compare young NUV- and V-selected associations.  
  > "We perform the watershed analysis for NGC 3351 with brighter limits of $M_\mathrm{V} < -4.2$ and $M_\mathrm{NUV} < -6.3$." (Dependence on absolute magnitude limit of tracer stars); "We now directly compare the overlap between young ($<10$ Myr) associations found by both bands." (Comparison for Selection of Young Stellar Associations)
   - parameter: M_V < -4.2; M_NUV < -6.3; young associations <10 Myr  
  > "We perform the watershed analysis for NGC 3351 with brighter limits of $M_\mathrm{V} < -4.2$ and $M_\mathrm{NUV} < -6.3$." (Dependence on absolute magnitude limit of tracer stars); "We now directly compare the overlap between young ($<10$ Myr) associations found by both bands." (Comparison for Selection of Young Stellar Associations)
   - fitting: _not stated_
   - validation: Compare counts, sizes, ages, masses, attenuation, and colour distributions  
  > "While the average size and age of the associations remains approximately the same with the magnitude limits applied, the average mass increases slightly at all scale levels." (Dependence on absolute magnitude limit of tracer stars); "To test this, we looked at the distribution of both the unique and common associations on a colour–colour diagram." (Comparison for Selection of Young Stellar Associations)
7. **Validate against independent tracers**: Compare association containment of LEGUS objects and age-binned V-selected associations with Hα emission.  
  > "We compare the previously found LEGUS Class 1, 2, and 3 objects in our two test galaxies to our watershed-defined stellar associations." (Comparison to LEGUS Star Clusters and Associations); "We therefore compare the H$\alpha$ emission to age-binned stellar association regions created using the *V*-band tracer stars to see the distribution of both young and old associations." (Comparison to H II Region Population)
   - parameter: Hα comparisons: 1–3 Myr, 3–5 Myr, and >60 Myr  
  > "the youngest stellar associations with ages of $1$ to $3$ Myr" (Comparison to H II Region Population); "Stellar associations with slightly older ages of $3$ to $5$ Myr" (Comparison to H II Region Population); "The oldest stellar associations traced by the *V*-band light with ages greater than $60$ Myr" (Comparison to H II Region Population)
   - fitting: _not stated_
   - validation: Youngest associations trace Hα; older associations are less associated  
  > "Since only the youngest ($1{-}3$ Myr) associations trace the H$\alpha$ light, which is only produced by young stars, this is a good independent check that our stellar associations are indeed tracing the young starlight." (Comparison to H II Region Population)
8. **Prepare molecular cloud comparison**: Use inherited PYCPROPS cloud catalogues and velocity-collapsed maps; select the most massive cloud along each line of sight.  
  > "We use the molecular cloud catalogues developed by the PHANGS project using PYCPROPS, an updated version of the CPROPS algorithm (cite: rosolowsky06), described in detail in (cite: rosolowsky21)." (Comparison to Molecular Cloud Population); "Since the *HST* data have no velocity information, we use a velocity-collapsed CPROPS map." (Comparison to Molecular Cloud Population); "When multiple CO clouds are detected along the same line of sight, we compare with the most massive cloud detected along the line of sight." (Comparison to Molecular Cloud Population)
   - software: PYCPROPS, CPROPS
   - parameter: Inherited cloud maxima: at least twice the local merge level  
  > "Maxima must have a brightness that is as least twice as bright as the local ‘merge level’, the emission level that contains at least one neighbour." (Comparison to Molecular Cloud Population)
   - parameter: Inherited cloud maxima: N > 0.25 Ω_bm/Ω_pix  
  > "($N > 0.25\Omega_{\rm{bm}}/\Omega_{\rm{pix}}$)." (Comparison to Molecular Cloud Population)
   - assumption: Most massive line-of-sight cloud represents the collapsed comparison  
  > "When multiple CO clouds are detected along the same line of sight, we compare with the most massive cloud detected along the line of sight." (Comparison to Molecular Cloud Population)
   - fitting: _not stated_
   - validation: _not stated_
9. **Measure cloud–association overlap**: Pixel-by-pixel area comparison and region-overlap fractions for NUV associations and velocity-collapsed CPROPS clouds.  
  > "We find the percent area of overlapping CPROPS and NUV-selected stellar association regions by doing a pixel-by-pixel comparison of the maps." (Comparison to Molecular Cloud Population); "We also calculate the percentage of stellar association regions that overlap with CPROPS clouds at every stellar association scale level." (Comparison to Molecular Cloud Population)
   - parameter: Only regions with both ALMA and HST coverage  
  > "For consistency, we will only consider regions with both ALMA and *HST* coverage." (Comparison to Molecular Cloud Population)
   - parameter: 64-pc association scale closest to ALMA beam size  
  > "This means that our 64-pc scale level is closest to the beam size of the ALMA data." (Comparison to Molecular Cloud Population)
   - assumption: NUV selection excludes older associations and provides a more coeval selection  
  > "we use the *NUV*-selected associations since (i) we are not interested in the older associations found with the *V*-band and (ii) to ensure a more coeval selection of stellar associations." (Comparison to Molecular Cloud Population)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **DOLPHOT** : PSF-fitting source detection, deblending, tracer catalogues, and association photometry  
  > "The DOLPHOT photometry package (cite: dolphin02) uses point spread function (PSF)-fitting to detect and deblend sources in the high-resolution *HST* images." (Sample & Data); "The PSF photometry of the stellar associations is found by summing DOLPHOT PSF photometry from all the DOLPHOT sources contained within the region." (Stellar Association Photometry)
- **scikit-image** : Seeded watershed association segmentation  
  > "We use the seeded watershed routine from the publicly available python package scikit-image (SKIMAGE.SEGMENTATION.WATERSHED) to define our stellar associations." (Watershed Parameters)
- **SKIMAGE.SEGMENTATION.WATERSHED** : Define stellar association regions  
  > "We use the seeded watershed routine from the publicly available python package scikit-image (SKIMAGE.SEGMENTATION.WATERSHED) to define our stellar associations." (Watershed Parameters)
- **SKIMAGE.FEATURE.PEAK_LOCAL_MAX** : Identify local-maxima watershed markers  
  > "We define our marker positions as the local maxima of the smoothed, filtered tracer star map using the routine SKIMAGE.FEATURE.PEAK_LOCAL_MAX." (Watershed Parameters)
- **CIGALE** : SED fitting for association ages, masses, and reddenings  
  > "To estimate ages, masses, and reddenings of the stellar associations, the CIGALE SED fitting package (cite: boquien19) is used" (SED Fitting)
- **PYCPROPS** : Production of inherited PHANGS molecular cloud catalogues  
  > "We use the molecular cloud catalogues developed by the PHANGS project using PYCPROPS, an updated version of the CPROPS algorithm (cite: rosolowsky06), described in detail in (cite: rosolowsky21)." (Comparison to Molecular Cloud Population)
- **CPROPS** : Cloud-identification algorithm underlying PYCPROPS; velocity-collapsed cloud maps used for comparison  
  > "PYCPROPS, an updated version of the CPROPS algorithm (cite: rosolowsky06)" (Comparison to Molecular Cloud Population); "Since the *HST* data have no velocity information, we use a velocity-collapsed CPROPS map." (Comparison to Molecular Cloud Population)
- **NASA/IPAC Extragalactic Database (NED)** : Research use acknowledged; specific contribution not stated  
  > "This research has made use of the NASA/IPAC Extragalactic Database (NED)" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| NGC 3351 NUV median log10(age/yr), 16 pc | 6.6 | not stated | dimensionless | 5 | / 16 pc       / 6.6 (6.48,6.78) / 3.15 (2.72,3.64)        / 0.18 (0.08,0.28)  / |
| NGC 3351 NUV median log10(age/yr), 64 pc | 6.9 | not stated | dimensionless | 5 | / 64 pc       / 6.9 (6.6,7.0)   / 3.57 (3.24,3.97)        / 0.14 (0.06,0.26)  / |
| NGC 1566 NUV median log10(age/yr), 16 pc | 6.6 | not stated | dimensionless | 5 | / 16 pc       / 6.6 (6.48,6.78) / 3.62 (3.2,4.02)         / 0.15 (0.06,0.25) / |
| NGC 1566 NUV median log10(age/yr), 64 pc | 6.85 | not stated | dimensionless | 5 | / 64 pc       / 6.85 (6.6,6.9)  / 4.04 (3.62,4.48)        / 0.14 (0.04,0.25) / |
| NGC 3351 NUV median log10(M/M⊙), 16 pc | 3.15 | not stated | dimensionless | 5 | / 16 pc       / 6.6 (6.48,6.78) / 3.15 (2.72,3.64)        / 0.18 (0.08,0.28)  / |
| NGC 3351 NUV median log10(M/M⊙), 64 pc | 3.57 | not stated | dimensionless | 5 | / 64 pc       / 6.9 (6.6,7.0)   / 3.57 (3.24,3.97)        / 0.14 (0.06,0.26)  / |
| NGC 1566 NUV median log10(M/M⊙), 16 pc | 3.62 | not stated | dimensionless | 5 | / 16 pc       / 6.6 (6.48,6.78) / 3.62 (3.2,4.02)         / 0.15 (0.06,0.25) / |
| NGC 1566 NUV median log10(M/M⊙), 64 pc | 4.04 | not stated | dimensionless | 5 | / 64 pc       / 6.85 (6.6,6.9)  / 4.04 (3.62,4.48)        / 0.14 (0.04,0.25) / |
| Regional photometry deficit relative to PSF photometry, 8 pc | 45 | not stated | per cent | 4 | The difference is largest at the 8-pc scale level with the regional photometry being on average $45$-per-cent smaller than the PSF photometry. |
| Regional versus PSF photometry difference, 64 pc | 11 | not stated | per cent | 4 | By the 64-pc level, the regional photometry is $\sim$ $11$-per-cent different from the PSF photometry. |
| Reduction factor in detected associations with brighter tracer limits | 2.4 | not stated | dimensionless | 6 | We find that the number of detected associations ${\sim}2.4$ times less with brighter magnitude limits. |
| NGC 3351 young NUV associations overlapping young V associations, 8 pc | 75 | not stated | per cent | 6 | $75$ per cent of the young *NUV*-band 8-pc associations have overlap with the young *V*-band associations. |
| NGC 3351 young NUV associations also detected in V, 64 pc | 85 | not stated | per cent | 6 | the percentage of *NUV*-band regions that are also detected in *V*-band increases to $85$ per cent |
| NGC 3351 LEGUS Class 3 containment in V associations, 16 pc | 93 | not stated | per cent | 7 | include 93 per cent of the LEGUS Class 3 compact associations. |
| NGC 1566 LEGUS Class 3 containment in V associations, 16 pc | 68 | not stated | per cent | 7 | For NGC 1566, the 16-pc *V*-band associations contain 28 per cent of the Class 1 clusters and 68 per cent of the LEGUS Class 3 compact associations. |
| NGC 3351 CPROPS area overlapping NUV associations, 64 pc | 15 | not stated | per cent | 9 | only $15$ per cent of the CPROPS area overlaps the NUV-selected stellar associations |
| NGC 3351 NUV association area overlapping CPROPS, 64 pc | 18 | not stated | per cent | 9 | $18$ per cent of the area covered by the 64-pc scale level associations overlaps with the CPROPS regions |
| NGC 1566 NUV association area overlapping CPROPS, 64 pc | 55 | not stated | per cent | 9 | $55$ per cent of the 64-pc scale level area overlapping with the CPROPS regions |
| NGC 1566 CPROPS area overlapping stellar associations, 64 pc | 12 | not stated | per cent | 9 | the percentage of the CPROPS area that contains 64-pc stellar associations is similarly small at only $12$ per cent. |
| CPROPS regions overlapping 64-pc stellar associations, both galaxies | 58 | not stated | per cent | 9 | We find that the percentage of CPROPS regions that have overlap with 64-pc stellar associations is ${\sim}58$ per cent for both galaxies. |
| NGC 3351 64-pc stellar associations overlapping CPROPS regions | 29 | not stated | per cent | 9 | the percentage of 64-pc stellar associations that overlap with the CPROPS regions is only $29$ per cent for NGC 3351 and $67$ per cent for NGC 1566. |
| NGC 1566 64-pc stellar associations overlapping CPROPS regions | 67 | not stated | per cent | 9 | the percentage of 64-pc stellar associations that overlap with the CPROPS regions is only $29$ per cent for NGC 3351 and $67$ per cent for NGC 1566. |

## Qualitative findings

- Associations occupy UBVI loci consistent with published compact cluster and association catalogues.  
  > "We find that our application of the algorithm successfully identifies populations that are well-characterised by single-age stellar populations, and occupy loci in the $UBVI$ colour–colour diagram consistent with previously published catalogues of compact clusters and associations." (Summary and Conclusions)
- NUV selection provides cleaner young coeval associations; V selection spans a wider age range and is less affected by dust.  
  > "Therefore, the *NUV*-band can provide a cleaner selection of young coeval stellar associations however the detection of these associations is limited by attenuation." (Comparison for Selection of Young Stellar Associations); "The *V*-band selection will allow for detection of associations with a wider ranges of ages and is less effected by dust." (Comparison for Selection of Young Stellar Associations)
- Cloud–association correlation varies with galactic environment.  
  > "In the dense spiral arms of NGC 1566, there are large overlaps between CPROPS regions and stellar associations." (Summary and Conclusions); "In more diffuse CO regions like the inter-arm region of NGC 1566 and disk of NGC 3351, there is less overlap between the CPROPS regions and stellar associations." (Summary and Conclusions)

## Claim tuples

- H: The watershed method identifies meaningful stellar associations at distinct physical scales. | E: Segment filtered tracer maps and compare size distributions and UBVI colours. | R: Sizes peak near the defining smoothing scales; colours occupy published cluster and association loci. | F: The method successfully identifies multi-scale stellar association populations. | **supported**
- H: Larger association scales include older stellar populations. | E: Fit five-band association SEDs and compare age distributions across scales. | R: Median log(age/yr) increases approximately from 6.6 to 6.9. | F: Median association age increases with smoothing scale. | **supported**
- H: NUV selection yields a cleaner sample of young coeval associations than V selection. | E: Compare young association overlap, attenuation, and colour–colour distributions between selections. | R: V-only associations have more large colour scatter; NUV detection is limited by attenuation. | F: Both selections are useful, with NUV favouring young coeval populations and V a wider age range. | **partially**
- H: Association identification and fitted ages recover physically associated young stars. | E: Compare age-binned V-selected association regions with independent Hα images. | R: Ages 1–3 Myr trace Hα; 3–5 Myr associations are less associated; >60 Myr associations are unassociated. | F: Hα provides an independent check on association definition and age fitting. | **supported**
- H: The association–molecular cloud correlation differs between the two galaxies. | E: Measure pixel and region overlap between NUV associations and velocity-collapsed CPROPS maps. | R: At 64 pc, 29 per cent of NGC 3351 associations and 67 per cent of NGC 1566 associations overlap clouds. | F: More stellar associations are correlated with molecular clouds in NGC 1566. | **supported**

## Reasoning

- Why this data: Two galaxies span the sample distance range and have LEGUS catalogues for independent comparison.  
  > "We choose these galaxies because they span the distance range of most of the galaxies in the PHANGS–HST sample (cite: anand21) and have been previously studied by the LEGUS programme (cite: calzetti15) to allow for catalogue comparisons." (Introduction)
- Why this method: Fixed physical scales facilitate cross-galaxy and ancillary-data comparisons; watershed controls markers and masks.  
  > "By relying on a fixed ladder of physical scales, our method facilitates comparison between galaxies." (Introduction); "it allows the user to control both the identification of the marker positions" (Watershed Parameters); "as well as to provide an image mask for pixels to consider when creating the segmented regions." (Watershed Parameters)
- Alternative: Dendrograms complicate comparisons at common surface brightness levels.  
  > "the organic branching results in identified ‘leaves’ with a wide range of surface brightness cutoffs (cite: rosolowsky08) and makes it difficult to compare structures at common surface brightness levels." (Introduction)
- Alternative: Choose the 4 times high-pass filter over the 8 times filter for tighter size distributions.  
  > "we adopt the smaller filter step which produces a tighter distribution of region sizes." (High-pass filtering); "Therefore, we will use the 4 times high-pass filter as our fiducial choice." (High-pass filtering)
- Alternative: Use PSF photometry instead of regional pixel photometry.  
  > "The regional photometry of the smaller regions at 8 and 16 pc are therefore most impacted by loss of flux due to small apertures." (Stellar Association Photometry); "We will therefore use the PSF photometry in our analysis for the rest of the paper." (Stellar Association Photometry)
- Alternative: Retain SSP analysis after testing exponentially declining CSP tracks.  
  > "Since the change in the stellar tracks from SSP to CSP is small and fails to explain the shifts in the colour distribution from the 16 to 64-pc scale levels, for the rest of the paper we focus our analysis on the BC03 SSP track." (Colors)
- Alternative: Retain signal-to-noise selection without a common absolute magnitude cut.  
  > "Since the overall change in the determined parameters is small, we chose to keep with a simple signal-to-noise selection and not apply an absolute magnitude cut on tracer stars" (Selection of Tracer Stars)
- How they decided it was enough: Colour consistency was judged sufficient for a proof of concept; Hα supplied an independent check.  
  > "the observed and physical properties appear to be reasonable (e.g., the colours of the associations track that of a single-aged stellar population) and sufficient for this proof of concept demonstration." (Stellar Association Photometry); "this is a good independent check that our stellar associations are indeed tracing the young starlight." (Comparison to H II Region Population)
- Limitation (authors): Tracer sources are not guaranteed to be individual stars.  
  > "While our criteria for the tracer stars are designed to select point-like sources, they do not guarantee that all sources are in fact individual stars." (Selection of Tracer Stars)
- Limitation (authors): Low-mass associations are susceptible to stochastic IMF sampling.  
  > "the regions which have the lowest mass also having the least number of DOLPHOT sources and therefore are more susceptible to stochastic sampling." (Ages and Masses)
- Limitation (authors): BC03 track structure produces an artificial age-distribution gap.  
  > "Part of this effect is due to a well known (cite: chandar10b) artifact that produces a gap between log(age/yr) = 7.0 and 7.5." (Ages and Masses)
- Limitation (authors): DOLPHOT splitting of slightly extended clusters can contaminate association samples.  
  > "the dolphot program occasionally breaks single, slightly extended objects into two or more separate sources, which are subsequently included as potential associations." (Ages and Masses)
- Limitation (authors): Larger associations may not be well described by a single-aged population.  
  > "It is possible that an SSP is not the best estimate for the larger scale level associations." (Colors); "Further study of more complex star formation histories will need to be done in the future." (Colors)
- Limitation (authors): Different ALMA beam sizes may affect overlap fractions.  
  > "This could be due in part to the larger ALMA beam size of $110$ pc for NGC 1566." (Comparison to Molecular Cloud Population)
- Limitation (authors): UV and optical observations may miss embedded star formation in dense clouds.  
  > "However, in the densest molecular clouds it may be impossible to detect ongoing embedded star formation with our UV and optical data." (Comparison to Molecular Cloud Population)
- Limitation (authors): Distance effects require further work for consistent cross-galaxy comparisons.  
  > "We will look more closely into the potential effects of distance as we seek to do future cross-galaxy correlations." (Discussion)
- Caveat (inferred, ours): Projected overlap does not by itself establish a physical association or a cloud evolutionary timescale.
- Caveat (inferred, ours): Unequal ALMA beam sizes, optical completeness, and extinction complicate the galaxy-to-galaxy overlap comparison.
- Caveat (inferred, ours): The text reports inconsistent association counts: 1324 versus 1401 for NGC 3351 and 2155 versus 2230 for NGC 1566 at the 16-pc V-selected level.
- Caveat (inferred, ours): Reported mass-growth and inter-galaxy mass ratios are inconsistent between the results, summary, and tabulated logarithmic medians.
- Caveat (inferred, ours): NGC 3351 64-pc association–cloud region overlap is reported as both 29 and 30 per cent.
- Caveat (inferred, ours): Tabulated quartiles describe population spread, not uncertainties on fitted medians.
- Caveat (inferred, ours): No overlap uncertainty, registration sensitivity test, or random-position control is provided.

## Reproducibility

- Data public (paper): HST data and association products retrievable from MAST; ALMA public availability not stated  
  > "The data underlying this article can be retrieved from the Mikulski Archive for Space Telescopes" (Data Availability); "including science ready mosaicked imaging associated with HST GO-15654 with digital object identifier and all multi-scale association regions and calculated properties developed in this paper." (Data Availability)
- Products in archive: PHANGS–HST HLSP mosaicked imaging, multi-scale association regions, and calculated properties  
  > "including science ready mosaicked imaging associated with HST GO-15654 with digital object identifier and all multi-scale association regions and calculated properties developed in this paper." (Data Availability)
- Code: Scripts planned for public release with full-sample association catalogues  
  > "The method presented here will be applied to the full sample of 38 PHANGS–HST galaxies to produce multi-scale association catalogues to be publicly released together with the scripts used." (Introduction)
- Missing: Exact ALMA-derived cloud catalogue and map files, release versions, and retrieval locations.
- Missing: Inherited DOLPHOT configuration and CIGALE single-population modifications.
- Missing: Software versions, complete SED parameter grids, and an executable analysis workflow.
- Missing: Foreground-star masks, common-coverage masks, and map-alignment details.
- Missing: Precise overlap-counting rules and resolution of inconsistent reported counts and mass ratios.
- Missing: ALMA visibility-to-cloud processing details if reproducing beyond the supplied literature products.
- Data volume (inferred): Not quantifiable from the text; product-level reproduction uses two-galaxy HST images, source catalogues, association masks, and collapsed CO cloud maps.
- Score (inferred): 6/5, 6/10: substantial association-method detail and archived HST products, but essential configurations and ALMA cloud products are inherited, overlap implementation is incomplete, and some answer-key numbers conflict.
- Rediscovery candidate: no, Results are numeric, but ALMA public availability is not stated and exact cloud-map products, processing dependencies, and overlap settings are insufficiently specified.

## Links

- Method: (cite: dolphin02) (DOLPHOT PSF photometry and source-characteristic definitions.)
- Method: (cite: boquien19) (CIGALE SED-fitting package.)
- Method: (cite: turner21) (Single-aged CIGALE augmentations and detailed modelling assumptions.)
- Method: (cite: rosolowsky06) (Original CPROPS algorithm underlying PYCPROPS.)
- Method: (cite: rosolowsky21) (PHANGS PYCPROPS cloud catalogue and map construction.)
- Method: (cite: gouliermis15; gouliermis17) (Kernel-density methodology combined with dendrogram concepts.)
- Method: (cite: rosolowsky08; rodriguez19; larson20) (Dendrogram methods informing the multi-scale identification approach.)
- Companion: (cite: lee22) (PHANGS–HST survey design, pipeline, and data products.)
- Companion: (cite: thilker22) (Compact-cluster detection and DOLPHOT catalogue production parameters.)
- Companion: (cite: deger22) (Cluster aperture correction and quantitative morphology.)
- Companion: (cite: whitmore21) (Star cluster candidate classification.)
- Companion: (cite: wei20) (Neural-network star cluster classification.)
- Companion: (cite: turner21) (PHANGS–HST SED fitting.)
- Companion: (cite: anand21) (TRGB distance analysis in PHANGS–HST parallel pointings.)
- Related: PHANGS
- Related: PHANGS–HST
- Related: PHANGS–ALMA
- Related: PHANGS–MUSE
- Related: PHANGS–Hα
- Related: PHANGS–JWST
- Related: LEGUS

## Checks

```json
{
 "quotes": 184,
 "quotes_ok": 184,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 2,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 22,
 "numeric_problems": 0,
 "fill": {
  "facts": 142,
  "stated": 98,
  "rate": 0.69
 },
 "evidence_ok": true
}
```
