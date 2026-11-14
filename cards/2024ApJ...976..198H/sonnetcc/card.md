# Whole-disk Sampling of Molecular Clouds in M83

`2024ApJ...976..198H` | The Astrophysical Journal 2024 | first author: Hirota, Akihiko | arXiv: 2410.05424 | DOI: 10.3847/1538-4357/ad8228

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, star_formation
- Question: Identify molecular clouds over the whole disk of M83 from 12CO(1-0) data and examine their properties, scaling relations, spatial distribution, mass function, cloud-to-cloud velocity dispersion, and the impact of beam dilution on virial parameter and surface density  
  > "to examine the cloud properties, distributions, scaling relations, and mass distributions." (1 Introduction); "we discuss the impact of beam-dilution (beam filling factor) on the cloud parameters" (1 Introduction)
- Target **M83**: coordinates _not stated_; z/distance not stated (45.6 pc per 2.09 arcsec beam major axis at the assumed distance)  
  > "at the assumed distance of M83 (cite: Thim2003M83Distance)" (2.1 Data); "We adopt ${v_{\mathrm{sys}}}$ of 511 $\mathrm{km\ s}^{-1}$ and $i$ of 24$\ensuremath{^\circ}$ (cite: Koda2023M83)" (5.1 Method to estimate vertical velocity dispersion of clouds); distance from Thim et al. 2003 (cite: Thim2003M83Distance)  
  > "at the assumed distance of M83 (cite: Thim2003M83Distance)" (2.1 Data); "We adopt ${v_{\mathrm{sys}}}$ of 511 $\mathrm{km\ s}^{-1}$ and $i$ of 24$\ensuremath{^\circ}$ (cite: Koda2023M83)" (5.1 Method to estimate vertical velocity dispersion of clouds)

## Data provenance

- ALMA projects: 2017.1.00079.S
- bands: _not stated_
- frequencies and spectral setup: 12CO(J=1-0); three cubes prepared at 1, 2 and 5 km/s velocity resolution; the 1 km/s cube adopted  
  > "Three data cubes were prepared in (cite: Koda2023M83) with velocity resolutions of 1, 2, and 5" (2.1 Data); "We here adopt the one with 1" (2.1 Data)
- continuum bandwidth: _not stated_
- arrays: 12-m array, ACA 7-m array and Total-Power array  
  > "The observations used the main 12-m array and Atacama Compact Array (ACA), i.e., the 7-m short-baseline interferometric array and the Total-Power (TP) single-dish array, to recover the flux." (2.1 Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Original beam 2.09 x 1.68 arcsec (45.6 pc x 36.7 pc); smoothed to circular beam 2.1 arcsec (~46 pc)  
  > "major and minor axes of 2$\ensuremath{''}$.09 $\times$ 1$\ensuremath{''}$.68 in full-width half maximum (FWHM)" (2.1 Data); "to achieve a circular beam with an FWHM size of 2$\ensuremath{''}$.1, corresponding to $\sim$46 pc" (2.1 Data)
- max recoverable scale: _not stated_
- sensitivity: Median rms noise 6.5 mJy per beam; mass sensitivity ~1e4 Msun (3 sigma)  
  > "The median noise level across the observed field is 6.5 mJy per beam." (2.1 Data); "a mass sensitivity of $\sim$10$^4$ ${M}_{\odot}$ (3 $\sigma$)" (abstract)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Data from Koda et al. 2023 (cite: Koda2023M83); project 2017.1.00079.S  
  > "mapping data of M83 observed with ALMA (cite: Koda2023M83)." (2.1 Data)
- Line: 12CO J=1-0 (not stated)
- Other facility **2MASS Large Galaxy Atlas (via Hirota 2014 rotation curve)**: Stellar mass distribution used in the adopted rotation curve  
  > "using the 2MASS Large Galaxy Atlas image (cite: Jarrett20032MASS)" (5.1 Method to estimate vertical velocity dispersion of clouds)
- External data: Calibrated and imaged 12CO(1-0) cubes (12-m + 7-m + TP) at 1, 2, 5 km/s  
  > "Three data cubes were prepared in (cite: Koda2023M83) with velocity resolutions of 1, 2, and 5" (2.1 Data) [from Koda et al. 2023 (cite: Koda2023M83)]
- External data: Distance to M83  
  > "at the assumed distance of M83 (cite: Thim2003M83Distance)" (2.1 Data) [from (cite: Thim2003M83Distance)]
- External data: Systemic velocity 511 km/s and inclination 24 deg  
  > "We adopt ${v_{\mathrm{sys}}}$ of 511 $\mathrm{km\ s}^{-1}$ and $i$ of 24$\ensuremath{^\circ}$ (cite: Koda2023M83)" (5.1 Method to estimate vertical velocity dispersion of clouds) [from (cite: Koda2023M83)]
- External data: Rotation curve of M83  
  > "we use the rotation curve of (cite: Hirota2014)" (5.1 Method to estimate vertical velocity dispersion of clouds) [from (cite: Hirota2014)]
- External data: CO-to-H2 conversion factor 2.0e20 cm^-2 (K km/s)^-1 with He correction 1.36  
  > "by applying a CO-to-H$_{2}$ conversion factor of 2.0 $\times$ 10$^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ in combination with a correction factor of 1.36" (2.3.2 Derived properties) [from (cite: Bolatto2013ConversionFactor)]
- External data: Galactic cloud catalog of S87 (273 clouds) used for scaling-relation comparison  
  > "The scaling relations of S87 are determined from 273 clouds sampled from the inner Galactic disk" (Comparison of Galactic cloud catalogs) [from (cite: Solomon1987Larson)]
- External data: R16 Galactic cloud catalog (1064 clouds)  
  > "The R16 catalog contains 1064 clouds with a total cloud mass of" (Catalogs for comparison) [from (cite: Rice2016)]
- External data: M17 Galactic cloud catalog (8107 clouds)  
  > "the M17 catalog lists 8107 clouds" (Catalogs for comparison) [from (cite: MivilleDeschenes2017MWGMC)]
- Simulation/model as data: Gaussian model clouds (Mcl 0.5-8e5 Msun, alpha_vir 1.5, Sigma 100 Msun/pc2) injected into a ~0.8 kpc2 field of the M83 cube, 40 repeats per setup, to test beam-dilution assumptions  
  > "Input model clouds are generated by assuming a Gaussian profile in both spatial and velocity directions." (Source injection test); "The injection-identification sequence is repeated 40 times for each setup." (Source injection test)

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
- array combination: TP data converted to visibilities with TP2VIS; 12-m, 7-m and TP visibilities jointly deconvolved in MIRIAD  
  > "The calibrated TP array data was converted into interferometric visibilities using the TP2VIS software (cite: Koda2019TP2VIS)." (2.1 Data); "Then, the 12-m, 7-m, and TP array visibilities were inverted onto the image plane and jointly deconvolved using the MIRIAD software package (cite: SaultTeubenWright1995MIRIAD)." (2.1 Data)
- smoothing: Spatial smoothing of the cube to a circular beam of 2.1 arcsec (~46 pc)  
  > "to achieve a circular beam with an FWHM size of 2$\ensuremath{''}$.1, corresponding to $\sim$46 pc" (2.1 Data)
- final beam: 2.09 x 1.68 arcsec original; 2.1 arcsec circular after smoothing  
  > "major and minor axes of 2$\ensuremath{''}$.09 $\times$ 1$\ensuremath{''}$.68 in full-width half maximum (FWHM)" (2.1 Data)
- final rms: Median 6.5 mJy per beam  
  > "The median noise level across the observed field is 6.5 mJy per beam." (2.1 Data)

### Inherited from earlier work

- Calibration of the interferometric and single-dish data  
  > "The calibration procedure is described in (cite: Koda2023M83)." (2.1 Data) [from (cite: Koda2023M83)]
- Further details on data processing (imaging, joint deconvolution)  
  > "We refer the readers to (cite: Koda2023M83) for further details on the data processing." (2.1 Data) [from (cite: Koda2023M83)]
- Cloud property calculation  
  > "calculated in a way similar to the one adopted in (cite: Hirota2018M83)" (2.3 Derivation of cloud properties) [from (cite: Hirota2018M83)]
- Extrapolation of moments to the 0 K level  
  > "extrapolated to the 0 K level with the procedure of (cite: Rosolowsky2006CPROPS)" (2.3.1 Measured properties) [from (cite: Rosolowsky2006CPROPS)]
- Effective radius factor 3.4/sqrt(pi)  
  > "is an empirical factor that is determined by S87" (2.3.2 Derived properties) [from S87 (cite: Solomon1987Larson)]
- Virial mass definition  
  > "Following (cite: BertoldiMcKee1992) virial mass is calculated as" (2.3.2 Derived properties) [from (cite: BertoldiMcKee1992)]
- Density profile index k = 1 in the geometrical factor  
  > "we adopt $k$=1 to keep consistency with previous studies." (2.3.2 Derived properties) [from S87]
- Method for vertical cloud-to-cloud velocity dispersion  
  > "We adopt a method similar to the one used by (cite: Hernandez2019) to estimate the vertical velocity dispersion of stellar clusters." (5.1 Method to estimate vertical velocity dispersion of clouds) [from (cite: Hernandez2019)]

### Not stated but needed to reproduce (our reading)

- Location/DOI of the Koda et al. 2023 1 km/s cube and whether it already includes TP2VIS and the exact MIRIAD parameters (weighting, deconvolver, cell size, masks)
- astrodendro min_value, min_delta and min_npix expressed as exact keyword values, and how the SNR cube was built from the noise map
- Watershed segmentation settings (markers, connectivity, compactness) in scikit-image
- Implementation of the CPROPS-style 0 K extrapolation (software or own code) and the exact bootstrap scheme
- Per-cloud L_CO summation boundary and the definition of T_peak when smoothed cubes are used
- Fit details for the Mvir-LCO and sigma/sqrt(R)-Sigma least-square fits (weights, which variable on which axis, 2 K split handling)
- emcee settings (walkers, steps, burn-in, likelihood form) for the Schechter-like fit and handling of mass bins
- Fitting procedure used for the logarithmic spiral arms and arm mask construction
- Source-injection details: field coordinates, injection convolution kernel, exact cross-match algorithm
- Catalog is said to be available as an electronic table but no access location is given in the paper text

## Analysis recipe

1. **Prepare the 1 km/s cube at a common circular beam**: Adopt the 1 km/s cube of Koda et al. 2023 and smooth spatially to a circular beam  
  > "We here adopt the one with 1" (2.1 Data); "To avoid complexities associated with the non-circular beam, we smoothed the original data cube in spatial directions" (2.1 Data)
   - parameter: Circular beam FWHM 2.1 arcsec (~46 pc)  
  > "to achieve a circular beam with an FWHM size of 2$\ensuremath{''}$.1, corresponding to $\sim$46 pc" (2.1 Data)
   - assumption: Assumed distance of M83 from Thim et al. 2003  
  > "at the assumed distance of M83 (cite: Thim2003M83Distance)" (2.1 Data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Build a noise-free noise map**: MIRIAD mossen expected noise map scaled to the median of the measured rms map  
  > "to generate a two-dimensional noise distribution expected from the integration time and system noise temperature assigned to visibilities." (2.1 Data); "measuring rms noise along the velocity axis at each position in the data cube." (2.1 Data)
   - software: MIRIAD
   - parameter: Median noise 6.5 mJy per beam  
  > "The median noise level across the observed field is 6.5 mJy per beam." (2.1 Data)
   - fitting: _not stated_
   - validation: Expected and measured maps agree in relative spatial variation but differ in absolute scaling by a few tens of percent  
  > "are discrepant in the absolute scaling by a few tens of percent." (2.1 Data)
3. **Construct the signal mask**: Seed regions of SNR>=4, drop regions smaller than 0.6 beam area or confined to one channel, expand to connected voxels with SNR>=2  
  > "first identifying a set of regions that consist of voxels with SNR $\ge$ 4" (2.2 Cloud identification); "then discarding small regions whose spatial extents are less than 0.6 times the beam area" (2.2 Cloud identification); "finally expanding the remaining regions to include the morphologically connected surrounding voxels with SNR $\ge$ 2" (2.2 Cloud identification)
   - fitting: _not stated_
   - validation: _not stated_
4. **Decompose the masked cube into clouds**: astrodendro leaves only, then watershed segmentation of unassigned voxels  
  > "The masked data cube was decomposed into a set of independent closed surfaces using the" (2.2 Cloud identification); "The unassigned voxels to any seed structures are further segmented with the watershed algorithm, using the" (2.2 Cloud identification)
   - software: astrodendro, scikit-image
   - parameter: Only voxels with SNR>2 included  
  > "only voxels with SNR $>2$ are included in the analysis" (2.2 Cloud identification)
   - parameter: Leaf candidates with peak-to-edge SNR contrast <2 discarded  
  > "candidates with SNR contrasts between their peak and edge-level $<2$ are discarded" (2.2 Cloud identification)
   - parameter: 5724 leaves accepted as clouds  
  > "are accepted as molecular clouds" (2.2 Cloud identification)
   - assumption: Only leaves are needed because the 46 pc resolution is only a factor of two below the molecular disk height  
  > "examining structures larger than individual leaves is unnecessary." (2.2 Cloud identification)
   - fitting: _not stated_
   - validation: About 91 percent of the total CO luminosity sampled as clouds  
  > "About 91 percent of the total CO luminosity within the mapped area was sampled as molecular clouds" (2.2 Cloud identification)
5. **Measure basic cloud properties**: Intensity-weighted first moments for centroid; second moments for size and velocity dispersion, extrapolated to 0 K; L_CO summed and extrapolated  
  > "centroid position and velocity are measured as the intensity-weighted first moments." (2.3.1 Measured properties); "extrapolated to the 0 K level with the procedure of (cite: Rosolowsky2006CPROPS)" (2.3.1 Measured properties)
   - parameter: Bootstrap error estimation with 1000 trials  
  > "by performing a bootstrap error estimation with 1000 trials." (2.3.1 Measured properties)
   - fitting: _not stated_
   - validation: Flux extrapolation slightly over-corrects in the central 550 pc (f_cl 1.04 +/- 0.03)  
  > "which indicates that the flux extrapolation is over-correcting the cloud flux by a few percent." (2.6 Fraction of CO luminosity sampled as GMC)
6. **Derive physical cloud properties**: Deconvolve beam and channel width in quadrature; Reff = 3.4/sqrt(pi) sqrt(sx sy); Mcl from L_CO with alpha_CO; Sigma = Mcl/(pi Reff^2); Mvir = 5 R sigma_v^2/(a1 G); alpha_vir = Mvir/Mcl  
  > "is an empirical factor that is determined by S87" (2.3.2 Derived properties); "Following (cite: BertoldiMcKee1992) virial mass is calculated as" (2.3.2 Derived properties)
   - parameter: CO-to-H2 factor 2.0e20 cm^-2 (K km/s)^-1 with He factor 1.36 (alpha_CO 4.4 Msun/(K km/s pc2))  
  > "by applying a CO-to-H$_{2}$ conversion factor of 2.0 $\times$ 10$^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ in combination with a correction factor of 1.36" (2.3.2 Derived properties)
   - parameter: Density profile index k = 1  
  > "we adopt $k$=1 to keep consistency with previous studies." (2.3.2 Derived properties)
   - parameter: 225 clouds fail deconvolution and are flagged  
  > "Out of the 5724 clouds identified, 225 clouds have" (2.3.2 Derived properties)
   - assumption: Isolated clouds with simple geometry and density distribution; no support from external pressure and magnetic fields  
  > "has a limitation in characterizing the dynamical status of molecular clouds." (2.3.2 Derived properties)
   - fitting: _not stated_
   - validation: _not stated_
7. **Compare with Larson/S87 scaling relations**: Plot sigma_v-Reff, Mvir-LCO, Mcl-Reff and sigma_v/sqrt(R)-Sigma, split clouds at Tpeak 2 K, compare with S87 and Galactic catalogs R16 and M17; least-square fits  
  > "In what follows, we show clouds with $T_{\mathrm{peak}}>$2 K and $<2$ K as separate subsets" (3.2 Scaling relations); "The least-square fitting to $>2$ K clouds yield" (3.2.2 Virial mass-CO luminosity relation)
   - parameter: Spearman correlation coefficient reported for each relation  
  > "shows an apparent correlation with a correlation coefficient of 0.78" (Summary)
   - assumption: S87 relations used as reference with Sigma ~200 Msun/pc2 and C = 0.72 km/s pc^-1/2  
  > "have a constant surface density of" (3.2 Scaling relations)
   - fitting: Least-square fits; weights and priors not stated  
  > "The least-square fitting to $>2$ K clouds yield" (3.2.2 Virial mass-CO luminosity relation)
   - validation: Comparison with R16 and M17 Galactic catalogs (Appendix)  
  > "Here, we extend the examination made in" (Comparison of Galactic cloud catalogs)
8. **Fit the cloud mass function**: Restricted power-law fit by least squares to the cumulative distribution; Schechter-like fit by emcee MCMC; both above completeness limit; K-S test  
  > "We fitted the power-law form using the cumulative mass distribution function and least-square minimization against the integral form" (4.2 Cloud mass spectra); "software library, which implements a Markov chain Monte Carlo method" (4.2 Cloud mass spectra)
   - software: emcee
   - parameter: Completeness limit 2e5 Msun; only clouds above it fitted  
  > "Hereafter, we regard $2\times10^{5}$ ${M}_{\odot}$ as the effective completeness limit." (4.2 Cloud mass spectra)
   - parameter: Prior on gamma_exp uniform between -5 and 0; Mu,exp log-uniform between 1e5 and 1e9 Msun  
  > "is uniform between -5 and 0" (4.2 Cloud mass spectra)
   - fitting: emcee MCMC for Schechter-like form; least-square for power law; walkers and steps not stated  
  > "software library, which implements a Markov chain Monte Carlo method" (4.2 Cloud mass spectra)
   - validation: Two-sample K-S test p-values  
  > "calculated with the two-sample K-S test for both forms with the null hypothesis that the fitted and observed cumulative mass distributions are drawn from the same distribution." (4.2 Cloud mass spectra)
9. **Estimate vertical cloud-to-cloud velocity dispersion**: Subtract systemic and circular rotation velocities from each cloud's LOS velocity and take the dispersion of v_res/cos(i) in radial bins, split at 5e5 Msun  
  > "We adopt a method similar to the one used by (cite: Hernandez2019) to estimate the vertical velocity dispersion of stellar clusters." (5.1 Method to estimate vertical velocity dispersion of clouds); "The radial bins are configured with a width and increment of 24" (5.2 Vertical cloud-to-cloud velocity dispersion)
   - parameter: v_sys 511 km/s, inclination 24 deg  
  > "We adopt ${v_{\mathrm{sys}}}$ of 511 $\mathrm{km\ s}^{-1}$ and $i$ of 24$\ensuremath{^\circ}$ (cite: Koda2023M83)" (5.1 Method to estimate vertical velocity dispersion of clouds)
   - parameter: Rotation curve of Hirota et al. 2014  
  > "we use the rotation curve of (cite: Hirota2014)" (5.1 Method to estimate vertical velocity dispersion of clouds)
   - assumption: In-plane non-circular motions neglected outside the bar  
  > "is that the impact of in-plane non-circular motion is just neglected." (5.3 Assessment of the impact of streaming motions)
   - fitting: _not stated_
   - validation: Levene's test between mass groups and arm vs inter-arm clouds, p<0.05 threshold  
  > "We discard the null hypothesis if the $p$-value of the test is below 0.05." (5.2 Vertical cloud-to-cloud velocity dispersion)
10. **Correct for beam dilution (area-filling factor) and test with source injection**: Assume alpha_vir = alpha_vir0 f^-1/2 and Sigma = f Sigma0; select single-component clouds with T_eq > 0.5 K; derive f assuming alpha_vir0 of 1 and 2; verify with injected model clouds  
  > "we adopt $T_{\mathrm{eq}}$ $>$ 0.5 K as a criterion to select clouds to estimate" (6.2.1 Criterion to select clouds for filling factor estimation); "1 (virialized clouds) and 2 (loosely gravitationally-bound clouds)." (6.2.2 Estimation of intrinsic cloud properties)
   - parameter: Injection-identification sequence repeated 40 times per setup  
  > "The injection-identification sequence is repeated 40 times for each setup." (Source injection test)
   - assumption: Beam dilution affects Reff but not sigma_v or Mcl  
  > "we assume that the beam dilution affects the observed cloud radius" (6.1 Impact of sampling clouds with a relatively large beam)
   - assumption: Constant CO-to-H2 conversion factor and H2-dominated cloud masses  
  > "involves the assumptions of a constant CO-to-H$_{2}$ conversion factor and dominance of H$_{2}$ in the cloud masses." (6.2.2 Estimation of intrinsic cloud properties)
   - fitting: _not stated_
   - validation: Source injection test with model clouds in noise-only and blended setups  
  > "which injects model sources with known properties into a portion of the data cube and samples the injected sources via the same identification procedure" (Source injection test)

## Software

- **astrodendro** : Decomposition of the masked cube into leaves  
  > "The masked data cube was decomposed into a set of independent closed surfaces using the" (2.2 Cloud identification)
- **scikit-image** : Watershed segmentation of voxels not assigned to leaves  
  > "The unassigned voxels to any seed structures are further segmented with the watershed algorithm, using the" (2.2 Cloud identification)
- **MIRIAD** : Joint deconvolution of 12-m, 7-m and TP visibilities; mossen for the expected noise map  
  > "jointly deconvolved using the MIRIAD software package (cite: SaultTeubenWright1995MIRIAD)." (2.1 Data)
- **TP2VIS** : Converting calibrated TP data to interferometric visibilities  
  > "The calibrated TP array data was converted into interferometric visibilities using the TP2VIS software (cite: Koda2019TP2VIS)." (2.1 Data)
- **emcee** : MCMC sampling of the Schechter-like mass function fit  
  > "software library, which implements a Markov chain Monte Carlo method" (4.2 Cloud mass spectra)
- **APLpy** : Plotting package named in the acknowledgements  
  > "This research made use of APLpy, an open-source plotting package for Python" (Summary)
- **matplotlib** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of clouds identified | 5724 | not stated | clouds | 4 | allowed us to sample 5724 molecular clouds |
| Median rms noise | 6.5 | not stated | mJy per beam | 2 | The median noise level across the observed field is 6.5 mJy per beam. |
| Fraction of total CO luminosity sampled as clouds | 91 | not stated | percent | 4 | About 91 percent of the total CO luminosity within the mapped area was sampled as molecular clouds |
| Detectable minimum cloud mass in isolation | ~3e4 | not stated | Msun | 6 | the expected minimum cloud mass would be $\sim3 \times 10^{4}$ ${M}_{\odot}$ |
| Median cloud mass (unweighted) | ~1.9e5 | not stated | Msun | 6 | with a median mass of $\sim1.9$ $\times$ $10^5$ ${M}_{\odot}$ |
| Unweighted and mass-weighted median Tpeak | 1.3 and 3.4 | not stated | K | 5 | The unweighted and mass-weighted median values among all the GMCs are 1.3 K and 3.4 K, respectively |
| Unweighted median surface density | 22 | not stated | Msun pc^-2 | 6 | The unweighted and mass-weighted median values are 22 |
| Median virial parameter quoted in the abstract | ~2.7 | not stated | dimensionless | 6 | (median ${\alpha_{\mathrm{vir}}}$ $\sim2.7$) |
| Share of clouds more massive than 1e6 Msun | 16 | not stated | percent of clouds | 6 | Such massive clouds comprise 16 percent of the total clouds in number |
| Clouds in arm/bar/center mask | 498 | not stated | clouds | 7 | 498 clouds reside in the arm/bar/center mask. |
| Mvir-LCO correlation coefficient (all clouds) | 0.78 | not stated | dimensionless | 7 | shows an apparent correlation with a correlation coefficient of 0.78 |
| Fit of Mvir vs LCO for Tpeak>2 K clouds | Mvir = 114 LCO^0.75 | 114 +/- 5; index +/- 0.02 | Msun with LCO in K km/s pc^2 | 7 | (114 \pm 5) \left[ {L}_{\mathrm{CO}}\left( \mathrm{K}\ \mathrm{km\ s}^{-1}\ \mathrm{pc}^2\right) \right]^{0.75\pm0.02} |
| Fit of sigma_v/sqrt(Reff) vs Sigma (all clouds) | 0.16 Sigma^0.30 | 0.16 +/- 0.01; index +/- 0.01 | km s^-1 pc^-1/2 with Sigma in Msun pc^-2 | 7 | (0.16 \pm 0.01) \left[ \Sigma( {M}_{\odot}\ \mathrm{pc}^{-2} ) \right]^{0.30 \pm 0.01} |
| Power-law mass function index (all clouds) | ~-1.85 | not stated | dimensionless | 8 | The power-law fit gives ${\gamma_{\mathrm{PL}}}\sim -1.85$ |
| Schechter-like mass function index (all clouds) | ~-1.57 | not stated | dimensionless | 8 | The Schechter-like form yields an index ${\gamma_{\mathrm{exp}}}$ of $\sim-1.57$ |
| Upper cutoff masses (power-law, Schechter-like) | ~8.6e6 and ~8.0e6 | not stated | Msun | 8 | namely ${M_{\mathrm{u,PL}}}$ of $\sim$8.6$\times$10$^6$ ${M}_{\odot}$ and ${M_{\mathrm{u,exp}}}$ of $\sim$8.0$\times$10$^6$ ${M}_{\odot}$ |
| Vertical cloud-to-cloud velocity dispersion at Rgal>100 arcsec (clouds >5e5 Msun and <5e5 Msun) | ~8.3 and ~11 | not stated | km s^-1 | 9 | is found to be almost constant around 8.3 |
| Fraction of clouds with observed alpha_vir below 1 (2) | 12 (24) | not stated | percent | 10 | about 12 (24) percent of the clouds indicate |
| Fraction of clouds compatible with single-component approximation (Teq>0.5 K) | ~57 | not stated | percent | 10 | ($\sim$57 percent) are compatible with the single-component approximation |
| Median intrinsic surface density for alpha_vir0 of 1 (2) | ~150 (~90) | spread ~0.3 dex (1 sigma) | Msun pc^-2 | 10 | The median ${\Sigma_{{0}}}$ is $\sim$150 ($\sim90$) for ${\alpha_{\mathrm{vir,0}}}$ of 1 (2) |

## Qualitative findings

- Massive clouds are concentrated toward the arm, bar and center, while smaller clouds prevail in inter-arm regions  
  > "tend to concentrate toward the arm, bar, and center, while smaller clouds are more prevalent in inter-arm regions." (abstract)
- Clouds with Tpeak>2 K follow S87 relations; Tpeak<2 K clouds, dominant in number, deviate  
  > "clouds, which are dominant in number, deviate significantly." (abstract)
- The power-law index steepens and the upper cutoff mass falls toward the outer disk  
  > "indicating a relative deficit of massive clouds toward the outer disk." (4.4 Possible origins of the radial variation of mass spectra)

## Claim tuples

- H: A sensitive whole-disk map samples the full range of GMC masses in M83 and shows where the gas mass resides | E: astrodendro plus watershed cloud identification on the 12CO(1-0) cube, 46 pc resolution | R: 5724 clouds with median mass ~1.9e5 Msun; massive clouds hold most CO luminosity and are concentrated in arm, bar and center | F: The catalog samples the GMC mass range comparable with Galactic surveys, with mass dominated by a minority of massive clouds | **supported**
- H: M83 clouds follow the S87 scaling relations | E: Compare sigma_v-Reff, Mvir-LCO, Mcl-Reff with S87 splitting at Tpeak 2 K | R: Tpeak>2 K clouds align with S87; Tpeak<2 K clouds deviate with lower Sigma and higher alpha_vir | F: Bright clouds resemble S87 clouds while most (faint) clouds do not without beam dilution correction | **partially**
- H: Beam dilution explains the high alpha_vir and low Sigma of faint clouds | E: Area-filling factor model with Teq>0.5 K selection and source injection tests | R: ~57 percent of clouds by number and ~90 percent by mass compatible with alpha_vir0 of 1-2; Sigma0 narrow around ~150 (~90) Msun/pc2 | F: A significant fraction of M83 clouds may be S87-like but beam-diluted; presented as a hypothesis | **partially**
- H: The cloud mass function steepens and the cutoff mass declines with galactocentric radius | E: Power-law and Schechter-like fits in five radial bins above 2e5 Msun | R: gamma_PL steepens from -1.3 to -2.0 and the cutoff mass declines; gamma_exp shows no clear trend; K-S tests inconclusive between forms | F: Relative deficit of massive clouds in the outer disk in the power-law description | **partially**
- H: Vertical cloud-to-cloud velocity dispersion depends on cloud mass | E: Residual LOS velocity after subtracting rotation, in radial bins, split at 5e5 Msun, Levene test | R: ~8.3 km/s for >5e5 Msun and ~11 km/s for <5e5 Msun clouds outside 2.2 kpc | F: Weak mass dependence; more massive clouds are more settled near the plane | **supported**

## Reasoning

- Why this data: Unprecedented mass sensitivity for a full-disk map of a substantial spiral galaxy  
  > "is unprecedented for such a full-disk mapping of substantial spiral galaxies." (1 Introduction)
- Why this method: Only leaves were used because larger structures are unnecessary at this resolution relative to the disk height  
  > "examining structures larger than individual leaves is unnecessary." (2.2 Cloud identification)
- Alternative: Schechter-like form not preferred over the restricted power law because K-S tests gave no clear preference and gamma_exp may be biased  
  > "As the K-S test gives no clear preference and as we suspect the fitted values" (4.3 Comparison of the fitted results between the two forms)
- How they decided it was enough: _not stated_
- Limitation (authors): alpha_vir has limited power to characterise dynamical state  
  > "has a limitation in characterizing the dynamical status of molecular clouds." (2.3.2 Derived properties)
- Limitation (authors): Mass completeness limit is raised in crowded regions  
  > "and the mass completeness limit is elevated in crowded regions." (2.6 Fraction of CO luminosity sampled as GMC)
- Limitation (authors): Flux extrapolation over-corrects by a few percent in the center  
  > "which indicates that the flux extrapolation is over-correcting the cloud flux by a few percent." (2.6 Fraction of CO luminosity sampled as GMC)
- Limitation (authors): Beam-dilution formulation rests on a crude approximation  
  > "A caveat is that the formulation made here is based on a crude approximation" (6.1 Impact of sampling clouds with a relatively large beam)
- Limitation (authors): In-plane streaming motions neglected in the velocity dispersion estimate  
  > "is that the impact of in-plane non-circular motion is just neglected." (5.3 Assessment of the impact of streaming motions)
- Caveat (inferred, ours): A single standard alpha_CO is applied across the disk although the paper cites a radial alpha_CO variation in M83
- Caveat (inferred, ours): Reported medians are not consistent across sections (alpha_vir median quoted as 2.4, 2.7 and 3.0; share of clouds above 1e6 Msun quoted as 16 and 13 percent; luminosity share as 60, 50 and 65 percent; f_cl 0.93 in the table versus 91 percent in the text)
- Caveat (inferred, ours): The filling-factor correction assumes alpha_vir0 of 1 or 2 and then finds Sigma0 near-constant, which is partly circular
- Caveat (inferred, ours): Cloud radii are resolution-limited (Reff 41 pc 16th percentile vs 46 pc beam), so scaling relations of small clouds are affected by the identification algorithm
- Caveat (inferred, ours): Mass-function power-law fit uncertainties of 0.00 in the table look too small for a least-squares fit to a cumulative distribution

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Public location of the Koda et al. 2023 processed cubes and their MIRIAD/TP2VIS parameters
- Missing: Exact astrodendro and watershed parameters in code form
- Missing: Implementation of moment extrapolation, bootstrap and fits
- Missing: Access location of the full electronic cloud catalog
- Data volume (inferred): Large if starting from raw 12-m, 7-m and TP data of a whole-disk mosaic (likely hundreds of GB); small if starting from the published 1 km/s cube
- Score (inferred): 3/5, Cloud identification recipe and many numeric results are given, but the input cube is a product of a prior paper with processing deferred to it and several algorithm settings are unstated
- Rediscovery candidate: no, Public status of the cube is not stated in the paper and the data reduction and several identification settings are deferred or missing, so the full recipe cannot be redone from the text alone

## Links

- Method: Koda et al. 2023 (cite: Koda2023M83) (Source of the calibrated and imaged M83 12CO cubes and data processing)
- Method: Koda et al. 2019 (cite: Koda2019TP2VIS) (TP2VIS conversion of total-power data to visibilities)
- Method: Rosolowsky and Leroy 2006 (cite: Rosolowsky2006CPROPS) (Moment extrapolation to 0 K)
- Method: Hirota et al. 2018 (cite: Hirota2018M83) (Cloud property derivation followed here)
- Method: Hernandez et al. 2019 (cite: Hernandez2019) (Vertical velocity dispersion method)
- Companion: Koda et al. 2023 (cite: Koda2023M83) (Whole-disk ALMA 12CO(1-0) map of M83 used here)
- Companion: Lee et al. 2024 (cite: Lee2024M83) (Radial variation of alpha_CO in M83 discussed in the text)
- Related: ALMA project 2017.1.00079.S
- Related: PHANGS-ALMA

## Checks

```json
{
 "quotes": 136,
 "quotes_ok": 136,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 20,
 "numeric_problems": 0,
 "fill": {
  "facts": 129,
  "stated": 88,
  "rate": 0.682
 },
 "evidence_ok": true
}
```
