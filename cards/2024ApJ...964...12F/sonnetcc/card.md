# ALMA-LEGUS. I. The Influence of Galaxy Morphology on Molecular Cloud Properties

`2024ApJ...964...12F` | The Astrophysical Journal 2024 | first author: Finn, Molly K. | arXiv: 2401.01450 | DOI: 10.3847/1538-4357/ad1eec

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: Which molecular cloud properties differ between barred spiral NGC 1313 and flocculent spiral NGC 7793 (similar mass, metallicity and SFR) and could explain NGC 1313 forming many more massive young star clusters  
  > "we directly compare the molecular gas in these two similar galaxies to determine the physical conditions responsible for their large disparity in cluster formation." (abstract)
- Target **NGC 1313**: coordinates _not stated_; z/distance 4.6 Mpc  
  > "at a distance of 4.6 Mpc" (Observations: NGC 1313 CO(2-1)); "(cite: Qing15), (cite: Gao16) for NGC 1313; (cite: RadburnSmith11), (cite: Sabbi18) for NGC 7793" (Table 1 notes); distance from Qing15, Gao16 (cited in Table notes)  
  > "at a distance of 4.6 Mpc" (Observations: NGC 1313 CO(2-1)); "(cite: Qing15), (cite: Gao16) for NGC 1313; (cite: RadburnSmith11), (cite: Sabbi18) for NGC 7793" (Table 1 notes)
- Target **NGC 7793**: coordinates _not stated_; z/distance 3.7 Mpc  
  > "at a distance of 3.7 Mpc" (Observations: NGC 7793 CO(2-1)); "(cite: Qing15), (cite: Gao16) for NGC 1313; (cite: RadburnSmith11), (cite: Sabbi18) for NGC 7793" (Table 1 notes); distance from RadburnSmith11, Sabbi18 (cited in Table notes)  
  > "at a distance of 3.7 Mpc" (Observations: NGC 7793 CO(2-1)); "(cite: Qing15), (cite: Gao16) for NGC 1313; (cite: RadburnSmith11), (cite: Sabbi18) for NGC 7793" (Table 1 notes)

## Data provenance

- ALMA projects: 2015.1.00782.S
- bands: Band 6  
  > "NGC 1313 was observed by ALMA in Band 6 (project code 2015.1.00782.S; PI: K. E. Johnson) with the 12m array." (Observations: NGC 1313 CO(2-1))
- frequencies and spectral setup: 12CO(2-1); velocity channel width 1.33 km/s  
  > "Using ALMA CO(2-1) observations of the two galaxies" (abstract); "the velocity channel width of the observations, 1.33 km s$^{-1}$" (5.2 Velocity Dispersion)
- continuum bandwidth: _not stated_
- arrays: 12m array only (no 7m or total power)  
  > "The total integration time is 3 hours with the 12-m array" (Observations: NGC 7793 CO(2-1)); "our observations do not cover the whole galaxy and we do not include 7m and total power data" (5.1 Mass)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: matched to 13 pc in both galaxies (after smoothing to a circular beam)  
  > "Using ALMA CO(2-1) observations of the two galaxies with the same sensitivities and resolutions of 13 pc" (abstract)
- max recoverable scale: 7.4 arcsec (150 pc) for NGC 1313; 7.0 arcsec (125 pc) for NGC 7793  
  > "The largest angular scale recovered with these observations is 7.4$''$, which corresponds to a spatial scale of 150 pc" (Observations: NGC 1313 CO(2-1)); "The largest angular scale recovered with these observations is 7.0$''$, which corresponds to a spatial scale of 125 pc" (Observations: NGC 7793 CO(2-1))
- sensitivity: ~0.2 K surface brightness sensitivity, matched between galaxies  
  > "carefully matched spatial resolutions of 13 pc and surface brightness sensitivities of $\sim0.2$ K" (Introduction)
- time on source: NGC 1313: north mosaic 68 pointings x 1.9 min (2.2 hr), central mosaic 104 pointings x 2.2 min (3.75 hr); NGC 7793: 148 pointings x 1.2 min (3 hr)  
  > "The northern arm mosaic consists of 68 pointings with 1.9 minutes of integration per pointing with a spacing of 12.9$''$ for a total integration time of 2.2 hours." (Observations: NGC 1313 CO(2-1)); "The central mosaic consists of 104 pointings with 2.2 minutes of integration per pointing for a total integration time of 3.75 hours" (Observations: NGC 1313 CO(2-1)); "The total integration time is 3 hours with the 12-m array with 148 pointings at 1.2 minutes of integration per pointing" (Observations: NGC 7793 CO(2-1))
- observing dates: NGC 1313: Cycle 4 (2016) then re-observed in Cycle 5 (2018); NGC 7793: Cycle 4 (2016)  
  > "It was originally observed in Cycle 4 in 2016 but did not meet sensitivity requirements and so was observed again in Cycle 5 in 2018." (Observations: NGC 1313 CO(2-1)); "NGC 7793 was observed by ALMA in Band 6 during Cycle 4 in 2016" (Observations: NGC 7793 CO(2-1))
- pi or archival as stated: Project 2015.1.00782.S, PI K. E. Johnson; NGC 7793 data previously used in Grasha18  
  > "NGC 1313 was observed by ALMA in Band 6 (project code 2015.1.00782.S; PI: K. E. Johnson) with the 12m array." (Observations: NGC 1313 CO(2-1)); "These data also appeared in (cite: Grasha18)." (Observations: NGC 7793 CO(2-1))
- Line: 12CO J=2-1 (not stated)
- Other facility **HST (LEGUS Treasury Program)**: Star cluster catalogs (positions, masses, ages, extinctions) from LEGUS  
  > "a Hubble Space Telescope (HST) Treasury Program that observed 50 nearby ($<12$ Mpc) galaxies" (Introduction); "we use catalogs of star clusters and their SED-fitted properties from the LEGUS collaboration" (Cluster Catalogs)
- Other facility **GALEX**: Far-UV images used (via Calzetti15) for galaxy SFRs  
  > "Calculated by (cite: Calzetti15) using GALEX far-UV images, dust corrected with methods of (cite: Lee09)" (Table 1 notes)
- External data: LEGUS star cluster catalogs (masses, ages, extinctions) for NGC 1313 and NGC 7793  
  > "we use catalogs of star clusters and their SED-fitted properties from the LEGUS collaboration, which used the methodology described in (cite: Adamo17)" (Cluster Catalogs) [from (cite: Adamo17); (cite: Calzetti15)]
- External data: Galaxy SFR (GALEX far-UV based), stellar mass and HI mass used in Table 1  
  > "Calculated by (cite: Calzetti15) using GALEX far-UV images, dust corrected with methods of (cite: Lee09)" (Table 1 notes) [from (cite: Calzetti15)]
- External data: NGC 1313 oxygen abundance 8.4+-0.1, no radial gradient  
  > "For NGC 1313, we use an oxygen abundance of $12+\log{\text{(O/H)}}=8.4\pm0.1$ with no radial gradient in the galaxy (cite: WalshRoy97)." (5.1 Mass) [from (cite: WalshRoy97)]
- External data: NGC 7793 radial oxygen abundance gradient (8.572 - 0.054 dex/kpc x R_gal)  
  > "NGC 7793 has a measured radial gradient of $12+\log{\text{(O/H)}}=8.572 - 0.054$ dex kpc$^{-1} \times R_\text{gal}$ (cite: Stanghellini15)." (5.1 Mass) [from (cite: Stanghellini15)]
- External data: Solar oxygen abundance 8.69  
  > "Using a solar oxygen abundance of $12+\log{\text{(O/H)}}=8.69$ (cite: Asplund09)" (5.1 Mass) [from (cite: Asplund09)]
- External data: Alternative NGC 7793 metallicity gradient (8.945 - 0.083 dex/kpc x R_gal), tested but not adopted  
  > "which instead finds $12+\log{\text{(O/H)}}=8.945 - 0.083$ dex kpc$^{-1} \times R_\text{gal}$" (5.1 Mass) [from (cite: Grasha22)]
- External data: Line used to flag clusters with age-reddening degeneracy (E(B-V) versus log(Age))  
  > "we remove the clusters that fall above the E(B-V)-log(Age) line from (cite: Whitmore23) only when comparing age measurements between the two galaxies" (Cluster Catalogs) [from (cite: Whitmore23)]
- External data: Standard 10% ALMA flux calibration uncertainty  
  > "the standard 10% ALMA flux calibration uncertainty (cite: Fomalont14)" (5.1 Mass) [from (cite: Fomalont14)]
- External data: Milky Way size-linewidth reference a0 = 1.0+-0.1, a1 = 0.5+-0.05  
  > "which found $a_0 = 1.0\pm0.1$ and $a_1 = 0.5\pm0.05$ for clouds mapped in CO(1-0) in the disk of the Milky Way" (6 Size-Linewidth Relations) [from (cite: Solomon87)]

## Processing

### Calibration

- pipeline or manual: ALMA data pipeline  
  > "The data were calibrated with the ALMA data pipeline version Pipeline-CASA54-P1-B (cite: Hunter23) in CASA 5.4.0-68" (Observations: NGC 1313 CO(2-1)); "The data were calibrated with the ALMA data pipeline version 2020.1.0-40 (cite: Hunter23) in CASA 6.1.1.15" (Observations: NGC 7793 CO(2-1))
- casa version: NGC 1313: calibrated in CASA 5.4.0-68, imaged in CASA 6.1.1.15; NGC 7793: calibrated in CASA 6.1.1.15  
  > "in CASA 5.4.0-68 using J2258-2758 for bandpass and amplitude calibration and J2353-3037 for phase calibration" (Observations: NGC 1313 CO(2-1)); "It was imaged in CASA 6.1.1.15 with a robust parameter of 0.5" (Observations: NGC 1313 CO(2-1)); "The data were calibrated with the ALMA data pipeline version 2020.1.0-40 (cite: Hunter23) in CASA 6.1.1.15" (Observations: NGC 7793 CO(2-1))
- pipeline version: NGC 1313: Pipeline-CASA54-P1-B; NGC 7793: 2020.1.0-40 (the Software section lists Pipeline-CASA51-P2-B v.40896, inconsistent with the Observations text)  
  > "ALMA data pipeline version Pipeline-CASA54-P1-B (cite: Hunter23)" (Observations: NGC 1313 CO(2-1)); "ALMA data pipeline version 2020.1.0-40 (cite: Hunter23)" (Observations: NGC 7793 CO(2-1)); "Pipeline-CASA51-P2-B v.40896 (cite: Davis21)" (Software)
- archive products used as is: _not stated_
- flux calibrator: Bandpass and amplitude: J2258-2758 (NGC 1313); J0519-4546 and J0334-4008 (NGC 7793)  
  > "using J2258-2758 for bandpass and amplitude calibration and J2353-3037 for phase calibration" (Observations: NGC 1313 CO(2-1)); "using J0519-4546 and J0334-4008 for bandpass and amplitude calibration and J0303-6211 for phase calibration" (Observations: NGC 7793 CO(2-1))
- flux scale uncertainty: 10% (standard ALMA flux calibration uncertainty)  
  > "We adopt a 10% error on the resulting masses due to the standard 10% ALMA flux calibration uncertainty (cite: Fomalont14)" (5.1 Mass)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5 (NGC 1313); Briggs robust = 2.0 (NGC 7793)  
  > "It was imaged in CASA 6.1.1.15 with a robust parameter of 0.5" (Observations: NGC 1313 CO(2-1)); "It was imaged using a Briggs weighting with a robust parameter of 2.0" (Observations: NGC 7793 CO(2-1))
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: none; 12m array data only  
  > "since we only use the 12m array data" (5.1 Mass)
- smoothing: both cubes smoothed to a circular 13 pc beam  
  > "we show the image data after smoothing to a circular beam size of 13 pc to match the observations of NGC 1313" (Observations: NGC 7793 CO(2-1)); "we show the image data after smoothing to a circular beam size of 13 pc to match the observations of NGC 7793" (Observations: NGC 1313 CO(2-1))
- final beam: native synthesized beams 0.579" x 0.486" (NGC 1313) and 0.686" x 0.595" (NGC 7793); matched 13 pc after smoothing  
  > "resulting in a synthesized beam of 0.579$''$$\times$0.486$''$ (12.8$\times$11.2 pc at a distance of 4.6 Mpc)" (Observations: NGC 1313 CO(2-1)); "resulting in a synthesized beam size of 0.686$''$$\times$0.595$''$ (12.3$\times$10.7 pc at a distance of 3.7 Mpc)" (Observations: NGC 7793 CO(2-1))
- final rms: ~0.2 K surface brightness sensitivity, matched between the galaxies  
  > "carefully matched spatial resolutions of 13 pc and surface brightness sensitivities of $\sim0.2$ K" (Introduction)

### Inherited from earlier work

- LEGUS cluster catalog methodology (SED fitting for masses, ages, extinctions)  
  > "we use catalogs of star clusters and their SED-fitted properties from the LEGUS collaboration, which used the methodology described in (cite: Adamo17)" (Cluster Catalogs) [from (cite: Adamo17)]
- X_CO(2-1) prescription depending on peak brightness temperature, beam size and metallicity  
  > "We use the $X_\text{CO(2-1)}$ calibration from (cite: Gong20), Table 3, Equation 3b" (5.1 Mass) [from (cite: Gong20), Table 3, Equation 3b]
- Effective radius conversion factor 1.91 applied to sigma_R  
  > "multiply $\sigma_R$ by 1.91 to get an" (5.3 Radii) [from (cite: Solomon87)]
- External pressure definition at the cloud edge  
  > "the external pressure will be equal to the pressure at the edge of cloud defined by (cite: Elmegreen89)" (5.4 Derived Quantities) [from (cite: Elmegreen89)]
- Filtering of clusters with age-reddening degeneracy  
  > "we remove the clusters that fall above the E(B-V)-log(Age) line from (cite: Whitmore23) only when comparing age measurements between the two galaxies" (Cluster Catalogs) [from (cite: Whitmore23)]
- NGC 7793 ALMA data previously published  
  > "These data also appeared in (cite: Grasha18)." (Observations: NGC 7793 CO(2-1)) [from (cite: Grasha18)]
- Completeness limit of LEGUS clusters at the galaxies' distances (about 1000 Msun)  
  > "at the distances of NGC 1313 and NGC 7793, we expect this limit to be much lower, closer to 1000 M$_\odot$ (cite: Grasha18)" (Cluster Catalogs) [from (cite: Grasha18)]

### Not stated but needed to reproduce (our reading)

- tclean parameters: cell size, image size, deconvolver, niter/threshold, masks, primary-beam cutoff, mosaic gridder
- spectral window selection and velocity range/starting channel of the CO(2-1) cubes; how the two NGC 1313 mosaics were combined
- continuum subtraction method and line-free channels
- how and with what tool the cubes were smoothed to the common 13 pc beam, and whether rms was re-measured after smoothing
- how the noise sigma used for dendrogram and quickclump thresholds was measured
- definition of T_peak used in the X_CO prescription (per voxel, per clump, after smoothing)
- which map (moment-0 or cube) the half-power contour ellipses were fitted to, and how the intensity-weighted mean line profile was constructed
- sample size and random seed for the bootstrapped KS/AD subsamples (text for the sample size is garbled)
- definition of the area used for surface density and of the footprint used for cluster-to-cloud matching
- ODR initial guesses and weighting for the size-linewidth fit; how the quoted a0 uncertainty was derived
- which pipeline version actually calibrated NGC 1313 (Observations text and Software section disagree)
- the LEGUS cluster catalog files used (version, filtering) and the final merged east/west catalogs

## Analysis recipe

1. **calibrate, image and smooth the CO(2-1) cubes**: ALMA pipeline calibration, CASA imaging with Briggs weighting, then smoothing both cubes to a common circular 13 pc beam  
  > "The data were calibrated with the ALMA data pipeline version Pipeline-CASA54-P1-B (cite: Hunter23) in CASA 5.4.0-68" (Observations: NGC 1313 CO(2-1)); "It was imaged using a Briggs weighting with a robust parameter of 2.0" (Observations: NGC 7793 CO(2-1)); "we show the image data after smoothing to a circular beam size of 13 pc to match the observations of NGC 1313" (Observations: NGC 7793 CO(2-1))
   - software: CASA, ALMA data pipeline
   - parameter: robust 0.5 (NGC 1313), 2.0 (NGC 7793)  
  > "It was imaged in CASA 6.1.1.15 with a robust parameter of 0.5" (Observations: NGC 1313 CO(2-1)); "It was imaged using a Briggs weighting with a robust parameter of 2.0" (Observations: NGC 7793 CO(2-1))
   - parameter: channel width 1.33 km/s  
  > "the velocity channel width of the observations, 1.33 km s$^{-1}$" (5.2 Velocity Dispersion)
   - assumption: distances 4.6 Mpc (NGC 1313) and 3.7 Mpc (NGC 7793)  
  > "at a distance of 4.6 Mpc" (Observations: NGC 1313 CO(2-1)); "at a distance of 3.7 Mpc" (Observations: NGC 7793 CO(2-1))
   - fitting: _not stated_
   - validation: _not stated_
2. **assemble the LEGUS cluster sample**: Use LEGUS catalogs (Cardelli89 extinction law, averaged aperture correction, Padova tracks via Yggdrasil), keep all cluster candidates, merge east and west maps using the better-fit entry for duplicates, drop age-degenerate clusters only for age comparisons  
  > "we use their catalog that uses the Milky Way extinction law from (cite: Cardelli89), averaged aperture correction method, and Padova stellar evolutionary tracks implemented by Yggdrasil (cite: Zackrisson11)." (Cluster Catalogs); "We then used the cluster properties from the map that had the better fit, based on their reported quality of fit Q parameter." (Cluster Catalogs); "We include all objects identified by LEGUS as cluster candidates, which required that they were brighter than M$_{V}$ of -6, detected above $3\sigma$ in the UBVI set of filters" (Cluster Catalogs)
   - software: Yggdrasil
   - parameter: massive clusters M > 1e4 Msun; young clusters age < 10 Myr  
  > "especially young massive clusters ($<10$ Myr, $>10^4$ M$_\odot$)" (abstract)
   - parameter: 67 overlapping clusters in NGC 1313, 47 in NGC 7793  
  > "We identified 67 overlapping clusters in NGC 1313 and 47 in NGC 7793." (Cluster Catalogs)
   - assumption: SFR fraction inside the LEGUS footprint from GALEX far-UV light used to scale cluster counts to the full galaxy  
  > "In NGC 1313, 57% of the total SFR is included in the LEGUS footprint, and in NGC 7793 53% is included." (Cluster Counts)
   - fitting: _not stated_
   - validation: Compared with other catalog methods by cited work; original catalogs kept for consistency  
  > "However, we use the original LEGUS catalogs still to maintain a consistent method between the two galaxies." (Cluster Catalogs)
3. **decompose the CO cube into dendrogram structures and clumps**: astrodendro hierarchical dendrograms (used for size-linewidth and virial analysis) and quickclump non-overlapping clumps (used for property distributions and counts)  
  > "We use the package `astrodendro` (cite: Rosolowsky08) to decompose the structures in each galaxy into dendrograms." (4.1 Dendrogram Segmentation); "We use the algorithm `quickclump` (cite: Sidorin17) to decompose the emission into clumps that have no overlap." (4.2 Clump Segmentation)
   - software: astrodendro, quickclump
   - parameter: astrodendro: min_value=3 sigma, min_delta=2.5 sigma, min_npix=2 beams  
  > "We use the input parameters `min_value`=3$\sigma$, `min_delta`=2.5$\sigma$, and `min_npix`=2 beams" (4.1 Dendrogram Segmentation)
   - parameter: quickclump: Tcutoff=4 sigma, dTleaf=4 sigma, Npixmin=2 beams (65 voxels for NGC 1313, 70 for NGC 7793)  
  > "We used the input parameters `Tcutoff`=4$\sigma$, `dTleaf`=4$\sigma$, and `Npixmin`=2 beams (equal to 65 and 70 for NGC 1313 and NGC 7793, respectively)." (4.2 Clump Segmentation)
   - assumption: Dendrograms count emission multiple times so are used only where multiple counting is allowed  
  > "However, dendrograms count emission multiple times and so they cannot be used for any counting statistics." (4 Molecular Gas Structure Decomposition)
   - fitting: _not stated_
   - validation: _not stated_
4. **compute cloud masses with a metallicity-dependent X_CO**: X_CO(2-1) from Gong20 (function of T_peak, beam size 13 pc, metallicity), H2 column density summed over pixel area, times 1.4 for total gas mass  
  > "We use the $X_\text{CO(2-1)}$ calibration from (cite: Gong20), Table 3, Equation 3b, which determines the $X_\text{CO(2-1)}$ conversion factor between $N_{H_2}$ and CO(2-1) based on the peak brightness temperature of the clump" (5.1 Mass); "then multiply by the pixel size in cm$^2$ and sum over all pixels to get the mass of H$_2$." (5.1 Mass)
   - parameter: Z = 0.51 Zsun (NGC 1313); Z = (0.56-0.76) Zsun (NGC 7793, Stanghellini15 gradient)  
  > "these abundances correspond to metallicities of $Z=0.51Z_\odot$ for NGC 1313 and a range of $Z=(0.56-0.76)Z_\odot$ for NGC 7793" (5.1 Mass)
   - parameter: mass error = 10% flux calibration added in quadrature with rms noise error  
  > "We adopt a 10% error on the resulting masses due to the standard 10% ALMA flux calibration uncertainty (cite: Fomalont14), which we add in quadrature with the error from the measured rms noise" (5.1 Mass)
   - assumption: factor 1.4 (mean mass per hydrogen atom, all hydrogen molecular)  
  > "multiply this M$_{H_2}$ by a factor of 1.4 (which is the mean mass per hydrogen atom and assumes all the hydrogen is molecular) to get the total mass of the gas" (5.1 Mass)
   - assumption: NGC 1313 metallicity with no radial gradient; solar 12+log(O/H) = 8.69  
  > "For NGC 1313, we use an oxygen abundance of $12+\log{\text{(O/H)}}=8.4\pm0.1$ with no radial gradient in the galaxy (cite: WalshRoy97)." (5.1 Mass); "Using a solar oxygen abundance of $12+\log{\text{(O/H)}}=8.69$ (cite: Asplund09)" (5.1 Mass)
   - fitting: _not stated_
   - validation: Alternative NGC 7793 metallicity gradient (Grasha22) gave no significant change to results  
  > "We find that the difference in metallicity prescription and resulting masses does not significantly affect any of the results in this paper" (5.1 Mass)
5. **measure velocity dispersion and radius of each structure**: Gaussian fit to the intensity-weighted mean line profile, deconvolved with channel width; ellipse fit to half-power contours, converted to effective radius and deconvolved with the beam, geometric mean of axes  
  > "We calculate the velocity dispersion for each structure by finding the intensity-weighted mean line profile and fitting a Gaussian, resulting in a fitted $\sigma_v$." (5.2 Velocity Dispersion); "To determine the sizes of the structures, we fit ellipses to the half-power contours and take the two axes as the HWHM of the structure." (5.3 Radii)
   - parameter: channel width 1.33 km/s with FWHM = 2.35 sigma; beam radius 6.5 pc; effective radius factor 1.91  
  > "converted from FWHM to $\sigma$ with FWHM$=2.35\sigma$" (5.2 Velocity Dispersion); "We deconvolve each axis with the radius of the beam, 6.5 pc, then take the geometric mean of the axes to get a final $R$." (5.3 Radii)
   - parameter: structures with deconvolved sigma_v < 0.1 x velocity resolution or R < 0.1 x beam size removed  
  > "We also remove from our analysis any structures that have a deconvolved $\sigma_v$ less than a tenth of the velocity resolution." (5.2 Velocity Dispersion); "We also remove from our analysis any structures that have a reported $R$ less than a tenth of the beam size." (5.3 Radii)
   - fitting: Gaussian line-profile fit; error from fit propagated through deconvolution; radius error from non-circularity plus half a pixel  
  > "The reported error in the size is determined by how non-circular the structure is, added in quadrature with a measurement error of half a pixel size, propagated through the deconvolution." (5.3 Radii)
   - validation: _not stated_
6. **derive surface density, virial parameter, external pressure and free-fall time**: Sigma = M / area; alpha_vir = 5 sigma_v^2 R / (G M); P_e = 3 Pi M sigma_v^2 / (4 pi R^3); t_ff = sqrt(pi^2 R^3 / (8 G M))  
  > "\alpha_\text{vir} = \frac{5 \sigma_v^2 R}{GM}." (5.4 Derived Quantities); "t_{ff} = \sqrt{\frac{3\pi}{32G\rho}} = \sqrt{\frac{\pi^2 R^3}{8GM}}." (5.4 Derived Quantities)
   - parameter: Pi = 0.5 for external pressure; collapse threshold alpha_vir < 1, unbound above 2  
  > "here we take $\Pi=0.5$" (5.4 Derived Quantities); "Values greater than two suggest that the cloud is not gravitationally bound and must either disperse or be constrained by an external pressure" (5.4 Derived Quantities)
   - assumption: cloud in pressure equilibrium with surrounding medium for P_e  
  > "Assuming a simplified case in which the cloud is in pressure equilibrium with the surrounding medium" (5.4 Derived Quantities)
   - fitting: _not stated_
   - validation: _not stated_
7. **fit the size-linewidth intercept**: Power-law sigma_v = a0 R^a1 fit to dendrogram structures with orthogonal distance regression, slope fixed at a1 = 0.5, intercept fitted per galaxy  
  > "where the power law is fit with orthogonal distance regression to take into account the error in both axes (cite: scipy)" (6 Size-Linewidth Relations); "We fit the intercept only of a power-law relation by holding the slope constant at a fixed value of $a_1=0.5$." (6 Size-Linewidth Relations)
   - software: SciPy
   - parameter: 2-D Gaussian KDE (scipy.stats, Scott's rule bandwidth) used only to display the point distribution  
  > "using the default Scott’s rule to determine the estimator bandwidth" (6 Size-Linewidth Relations)
   - assumption: fixed slope 0.5, chosen because fitted slopes in the literature vary widely with resolution, tracer and method  
  > "Consequently, we focus instead on the fitted intercept of this relation, which still gives us information about the relative kinetic energy of the clouds" (6 Size-Linewidth Relations)
   - fitting: orthogonal distance regression with errors on both axes; no priors  
  > "where the power law is fit with orthogonal distance regression to take into account the error in both axes (cite: scipy)" (6 Size-Linewidth Relations)
   - validation: Repeated with other fixed slopes from the literature; conclusion unchanged  
  > "Changing the fixed slope affects the values of the fitted intercepts, but not the conclusion that NGC 1313 has a significantly higher intercept and so more kinetic energy." (6 Size-Linewidth Relations)
8. **assess virial state of dendrogram structures**: Plot sigma_v^2/R against surface density for each dendrogram structure with the alpha_vir = 1 line and compare scatter between galaxies  
  > "we plot the velocity metric, $\sigma_v^2/R$, against the surface density, $\Sigma$, of each dendrogram structure." (7 Virialization)
   - assumption: only gravitational and kinetic energies considered; external pressure and magnetic fields neglected in the plot  
  > "The virial equilibrium line only considers the gravitational and kinetic energies of the cloud" (7 Virialization)
   - fitting: _not stated_
   - validation: _not stated_
9. **compare cloud and cluster property distributions between galaxies**: Histograms, KDEs and CDFs of non-overlapping clumps; two-sample KS and AD tests on 1000 random subsamples, averaging p-values  
  > "After taking 1000 random subsamples, we report the average $p$-values for each property comparison as the bootstrapped result." (8 Property Distribution Comparisons); "perform a KS and AD test, using a sample size instead of 65" (8 Property Distribution Comparisons)
   - software: SciPy
   - parameter: KDE scalar bandwidth 0.5 dex  
  > "We use a scalar estimator bandwidth of 0.5 dex for all KDEs in this section" (3.2 Cluster Property Distributions)
   - assumption: full-sample KS/AD tests are overpowered at large N, so subsampling is used only to rank which properties differ most  
  > "Rather, we use these results only to determine which properties show the biggest difference between the galaxies relative to the other properties." (8 Property Distribution Comparisons)
   - fitting: _not stated_
   - validation: Authors note full-sample tests give p < 5% for every property because of large N  
  > "the comparison of every property for the two galaxies have $p$-values less than 5%, and most are also much less than 1%." (8 Property Distribution Comparisons)
10. **test spatial correlation of bound clouds and cloud properties with young clusters**: Build gridded density maps of clouds, bound clouds and young clusters and compute correlation coefficients, repeated over cell sizes and alpha_vir thresholds; also nearest cloud distances for clusters  
  > "we create density maps of each and calculate the correlation coefficient between them." (9 Property Spatial Distributions); "These density maps split the area of the galaxy into cells and count the number of objects (either clouds, bound clouds, or young clusters) in each cell." (9 Property Spatial Distributions)
   - parameter: cell sizes 50 to 200 pixels (110 to 450 pc); alpha_vir thresholds 1 to 3; main bound-cloud map uses alpha_vir < 1.5 and young clusters < 10 Myr  
  > "a variety of cell sizes ranging from 50 to 200 pixels in the ALMA maps" (9 Property Spatial Distributions); "a variety of $\alpha_\text{vir}$ thresholds to determine cloud boundedness, ranging from values of 1 to 3." (9 Property Spatial Distributions); "we show for each galaxy the locations of the clouds that have $\alpha_\text{vir}$$<1.5$ and the youngest clusters ($<10$ Myr)" (9 Property Spatial Distributions)
   - assumption: clump (non-overlapping) definitions used for clouds  
  > "Here we use the clump definitions rather than the dendrogram structures for the clouds." (9 Property Spatial Distributions)
   - fitting: _not stated_
   - validation: Conclusion checked with the full cluster population as well as only young clusters  
  > "This conclusion is the same if we consider the full cluster population as well instead of only the youngest clusters." (9 Property Spatial Distributions)

## Software

- **CASA** 5.4.0-68 (NGC 1313 calibration); 6.1.1.15 (NGC 1313 imaging, NGC 7793 calibration): Calibration and imaging of the ALMA data  
  > "It was imaged in CASA 6.1.1.15 with a robust parameter of 0.5" (Observations: NGC 1313 CO(2-1)); "The data were calibrated with the ALMA data pipeline version 2020.1.0-40 (cite: Hunter23) in CASA 6.1.1.15" (Observations: NGC 7793 CO(2-1))
- **ALMA data pipeline** Pipeline-CASA54-P1-B (NGC 1313); 2020.1.0-40 (NGC 7793): Calibration of the ALMA observations  
  > "The data were calibrated with the ALMA data pipeline version Pipeline-CASA54-P1-B (cite: Hunter23) in CASA 5.4.0-68" (Observations: NGC 1313 CO(2-1))
- **astrodendro** : Dendrogram decomposition of the CO emission into trunks, branches and leaves  
  > "We use the package `astrodendro` (cite: Rosolowsky08) to decompose the structures in each galaxy into dendrograms." (4.1 Dendrogram Segmentation)
- **quickclump** : Non-overlapping clump decomposition of the CO emission  
  > "We use the algorithm `quickclump` (cite: Sidorin17) to decompose the emission into clumps that have no overlap." (4.2 Clump Segmentation)
- **SciPy** : Gaussian KDEs, orthogonal distance regression, KS and AD tests  
  > "Gaussian kernel density estimations (KDEs) from `scipy` (cite: scipy)" (3.2 Cluster Property Distributions); "where the power law is fit with orthogonal distance regression to take into account the error in both axes (cite: scipy)" (6 Size-Linewidth Relations)
- **Yggdrasil** : Stellar population models (with Padova tracks) in the LEGUS cluster catalog fits  
  > "Padova stellar evolutionary tracks implemented by Yggdrasil (cite: Zackrisson11)" (Cluster Catalogs)
- **Astropy** : _not stated_
- **Matplotlib** : _not stated_
- **NumPy** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Size-linewidth intercept a0, NGC 1313 (slope fixed at 0.5) | 0.41 | 0.01 | km/s pc^-0.5 (reported without units) | 7 | For NGC 1313, we fit a value of $a_0=0.41\pm0.01$, and for NGC 7793 we fit a value of $a_0=0.33\pm0.01$ |
| Size-linewidth intercept a0, NGC 7793 (slope fixed at 0.5) | 0.33 | 0.01 | km/s pc^-0.5 (reported without units) | 7 | For NGC 1313, we fit a value of $a_0=0.41\pm0.01$, and for NGC 7793 we fit a value of $a_0=0.33\pm0.01$ |
| Significance of intercept difference NGC 1313 vs NGC 7793 | more than 3 sigma | not stated | sigma | 7 | The intercept of NGC 1313 is significantly higher than that of NGC 7793 by more than $3\sigma$ |
| Number of LEGUS clusters, NGC 1313 / NGC 7793 | 1201 / 467 | not stated | clusters | 2 | with a total of 1201 clusters compared to 467 for NGC 7793 |
| Massive clusters (M > 1e4 Msun), NGC 1313 / NGC 7793 | 333 / 53 | not stated | clusters | 2 | having 333 massive clusters identified by LEGUS where NGC 7793 has 53 |
| Young massive clusters (< 10 Myr), NGC 1313 / NGC 7793 | 37 / 3 | not stated | clusters | 2 | 37 of those massive clusters are young; compared to only 3 in NGC 7793 |
| SFR ratio NGC 1313 / NGC 7793 | 2.2 | 0.8 | dimensionless | 2 | we get a ratio of 2.2$\pm$0.8 in the SFR between the two galaxies |
| Number of non-overlapping clumps, NGC 1313 / NGC 7793 | 531 / 965 | not stated | clumps | 3 | Clumps$^d$ / 531 / 965 |
| X_CO(2-1) range, NGC 1313 | (0.69-2.56)e20 | not stated | cm^-2 / (K km s^-1) | 4 | results in values of $X_\text{CO(2-1)}=(0.69-2.56)\times10^{20}$ cm$^{-2}$/(K km s$^{-1}$) for NGC 1313 and $X_\text{CO}$$=(0.64-2.65)\times10^{20}$ cm$^{-2}$/(K km s$^{-1}$) for NGC 7793 |
| X_CO(2-1) range, NGC 7793 | (0.64-2.65)e20 | not stated | cm^-2 / (K km s^-1) | 4 | results in values of $X_\text{CO(2-1)}=(0.69-2.56)\times10^{20}$ cm$^{-2}$/(K km s$^{-1}$) for NGC 1313 and $X_\text{CO}$$=(0.64-2.65)\times10^{20}$ cm$^{-2}$/(K km s$^{-1}$) for NGC 7793 |
| Total observed molecular gas mass in footprint, NGC 1313 / NGC 7793 | 7.6e6 / 1.4e7 | not stated | Msun | 4 | with measured totals of $7.6\times10^6$ M$_\odot$ in NGC 1313 and $1.4\times10^7$ M$_\odot$ in NGC 7793 |
| Fraction of CO mass in clump structures, NGC 1313 / NGC 7793 | 82% / 95% | not stated | percent | 4 | approximately 82% of the total observed CO mass in NGC 1313 and 95% in NGC 7793 |
| Correlation of young clusters with bound clouds / all clouds, NGC 1313 | 0.24 / 0.32 | 0.06 / 0.05 | dimensionless | 10 | the correlation coefficient of the young clusters with the bound clouds is 0.24$\pm$0.06 and with the general cloud population is 0.32$\pm$0.05 |
| Correlation of young clusters with bound clouds / all clouds, NGC 7793 | 0.36 / 0.44 | 0.18 / 0.13 | dimensionless | 10 | In NGC 7793, the correlation coefficients are 0.36$\pm$0.18 and 0.44$\pm$0.13 for the bound clouds and all clouds, respectively. |
| Bootstrapped KS / AD p-value, cluster mass | 0.04 / 0.02 | not stated | dimensionless | 9 | Cluster Mass / 0.04 / 0.02 |
| Bootstrapped KS / AD p-value, young cluster mass | 0.02 / 0.01 | not stated | dimensionless | 9 | Young Cluster Mass / 0.02 / 0.01 |

## Qualitative findings

- NGC 7793 has more molecular gas mass and nearly all of it is in identified clouds; NGC 1313 appears to have more diffuse molecular gas  
  > "NGC 7793 has significantly more molecular gas mass than NGC 1313 and nearly all of that molecular mass is accounted for with identified clouds, suggesting that NGC 1313 has more diffuse molecular gas than NGC 7793." (10 Discussion)
- Both galaxies mostly lie above the virial equilibrium line (kinetic-energy dominated)  
  > "Both galaxies fall mostly above the virial equilibrium line, suggesting that they are dominated by kinetic energy." (7 Virialization)
- Clusters in NGC 1313 are farther from molecular clouds than in NGC 7793  
  > "Both the full cluster population and the young clusters of NGC 1313 are further from molecular clouds than those in NGC 7793." (9 Property Spatial Distributions)

## Claim tuples

- H: Clouds in NGC 1313 carry more kinetic energy per size scale than clouds in NGC 7793 | E: Fit the size-linewidth intercept with slope fixed at 0.5 to dendrogram structures in each galaxy | R: a0 = 0.41+-0.01 (NGC 1313) versus 0.33+-0.01 (NGC 7793) | F: NGC 1313 has a significantly higher intercept, so more kinetic energy in its clouds | **supported**
- H: NGC 1313 has more clouds near virial equilibrium, possibly linked to its higher rate of massive cluster formation | E: Plot sigma_v^2/R against surface density for dendrogram structures and compare to the alpha_vir = 1 line; compare alpha_vir distributions | R: Both galaxies mostly above the virial line; NGC 1313 has larger scatter and more clouds close to virial equilibrium | F: NGC 1313 has more clouds near virial equilibrium, which may be connected to massive cluster formation | **partially**
- H: Virially bound clouds are more closely associated with young clusters than the general cloud population | E: Gridded density-map correlations between young clusters and bound clouds versus all clouds over many cell sizes and alpha_vir thresholds | R: Correlation with bound clouds (0.24 and 0.36) is not higher than with all clouds (0.32 and 0.44) in NGC 1313 and NGC 7793 | F: Bound clouds do not show a stronger correlation with young clusters than the general cloud population | **refuted**
- H: Large differences in molecular cloud properties explain the large difference in massive cluster formation between the two galaxies | E: Compare distributions of cloud mass, radius, linewidth, virial parameter, surface density, pressure and free-fall time using clumps, with bootstrapped KS and AD tests | R: Differences are small; the largest are higher surface density and lower free-fall time in NGC 1313; only cluster mass distributions cross the 5% p-value threshold | F: Cloud properties differ surprisingly little, with NGC 1313 having higher surface densities and lower free-fall times | **partially**
- H: The molecular gas content differs between the galaxies despite NGC 1313 having more HI and more massive clusters | E: Sum CO(2-1) emission in the footprint with average X_CO and factor 1.4, and compute the fraction of CO mass in clumps | R: 7.6e6 Msun (NGC 1313) versus 1.4e7 Msun (NGC 7793); 82% versus 95% of CO mass in clumps | F: NGC 7793 has nearly twice the molecular mass in the footprint; NGC 1313 likely has more diffuse molecular gas | **supported**

## Reasoning

- Why this data: Observe both galaxies in CO(2-1) at matched 13 pc resolution and matched sensitivity so cloud properties can be compared without resolution or sensitivity effects  
  > "To robustly compare the properties of the molecular clouds in this pair of galaxies, we have observed both in CO(2-1) with carefully matched spatial resolutions of 13 pc and surface brightness sensitivities of $\sim0.2$ K." (Introduction)
- Why this method: Dendrograms capture the hierarchy of gas from large GMCs to knots; non-overlapping clumps are needed for counting statistics  
  > "Dendrograms are superior for examining the full spatial scale of molecular clouds in the region because they are able to capture the hierarchical nature of the gas, from large GMCs to smaller knots." (4 Molecular Gas Structure Decomposition)
- Alternative: Alternative NGC 7793 metallicity gradient (Grasha22) tested; did not change results, so the lower Stanghellini15 metallicities were kept  
  > "We find that the difference in metallicity prescription and resulting masses does not significantly affect any of the results in this paper" (5.1 Mass)
- Alternative: Other fixed slopes for the size-linewidth fit tried; intercept values change but the conclusion does not  
  > "Changing the fixed slope affects the values of the fitted intercepts, but not the conclusion that NGC 1313 has a significantly higher intercept and so more kinetic energy." (6 Size-Linewidth Relations)
- Alternative: Embedded clusters of Messa21 in NGC 1313 not used because no equivalent catalog exists for NGC 7793  
  > "However, since we do not also have embedded clusters identified in NGC 7793 to compare, we do not include those clusters in this work." (Cluster Catalogs)
- Alternative: Keeping or removing age-degenerate clusters does not substantially change results  
  > "We also note that there are few enough of these objects that keeping or removing them does not substantially alter our results." (Cluster Catalogs)
- How they decided it was enough: _not stated_
- Limitation (authors): Footprints are partial and 7m and total power data are not included, so diffuse emission and total molecular masses are missed  
  > "It is important to note that our observations do not cover the whole galaxy and we do not include 7m and total power data, so we are likely missing diffuse emission" (5.1 Mass)
- Limitation (authors): SFR ratio between galaxies is not statistically significant given counting statistics and 25% SFR uncertainty  
  > "In this case, the ratios reported here are not statistically significant when considering error from counting statistics." (Cluster Counts)
- Limitation (authors): Bootstrapped KS and AD p-values do not necessarily indicate statistically significant differences and are used only to rank properties  
  > "We recommend caution when interpreting the bootstrapped KS and AD tests" (8 Property Distribution Comparisons)
- Limitation (authors): Missing flux at large scales may explain why cloud masses are smaller than the maximum cluster masses  
  > "This observation could be in part caused by missing flux at the largest size scales since our observations do not include ACA 7m or TP data." (8 Property Distribution Comparisons)
- Limitation (authors): Clusters used may be too old to be associated with their natal molecular gas  
  > "This may be because the clusters used in this study are too old to be associated with their natal molecular gas." (11 Conclusions)
- Caveat (inferred, ours): Only two galaxies are compared, so morphology cannot be isolated from other differences (NGC 1313 has a minor interaction and a southwest starburst outside the footprint).
- Caveat (inferred, ours): The two datasets were calibrated with different CASA and pipeline versions, calibrators and imaged with different robust values (0.5 vs 2.0); residual systematics after smoothing to 13 pc are not quantified.
- Caveat (inferred, ours): Cloud masses depend on the Gong20 X_CO with metallicity assumptions (no gradient in NGC 1313), and X_CO varies by about a factor of 4 within each galaxy.
- Caveat (inferred, ours): 12m-only data lose diffuse emission and large-scale structure, which can bias linewidths, sizes and the molecular mass comparison.
- Caveat (inferred, ours): The bootstrapped KS/AD p-values depend on the arbitrary subsample size (65) and the paper itself cautions against over-reading them.
- Caveat (inferred, ours): The size-linewidth analysis fixes the slope at 0.5 and quotes only statistical intercept errors; dendrogram structures are nested so points are not independent.
- Caveat (inferred, ours): Pipeline version is inconsistent between the Observations text and the Software section.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: tclean imaging parameters (cell, imsize, deconvolver, threshold, masks, mosaic settings) and cube velocity range
- Missing: continuum subtraction and line-free channels
- Missing: noise estimation used for sigma-based thresholds in astrodendro and quickclump
- Missing: exact definition and measurement of T_peak for the X_CO prescription
- Missing: bootstrap subsample size and random seed; ODR fit setup
- Missing: the specific LEGUS catalog files and the merged east/west cluster tables
- Data volume (inferred): Roughly 100-300 GB of raw ASDMs/measurement sets for the two Band 6 12m mosaics (about 320 pointings in total), with final cubes of a few GB each (inferred).
- Score (inferred): 3/5, Score on a 1-5 scale. Project code, calibrators, pipeline/CASA versions, robust values, decomposition parameters and all formulas are given, but the tclean setup, cube definition, noise estimation and bootstrap details are missing and the pipeline version is inconsistent.
- Rediscovery candidate: yes, ALMA project 2015.1.00782.S is given with archival-style acknowledgement, calibration and decomposition recipes are mostly specified, and main results (intercepts, cluster counts, masses, correlations) are numeric; imaging details must be chosen by the reproducer.

## Links

- Method: (cite: Hunter23) (ALMA data pipeline used for calibration)
- Method: (cite: Adamo17) (LEGUS cluster catalog methodology)
- Method: (cite: Gong20) (X_CO(2-1) calibration used for cloud masses)
- Method: (cite: Rosolowsky08) (astrodendro dendrogram algorithm)
- Method: (cite: Sidorin17) (quickclump clump-finding algorithm)
- Companion: (cite: Finn23b) (Follow-up study of cloud properties by sub-galactic region in these two galaxies)
- Companion: (cite: Grasha18) (Earlier use of the NGC 7793 ALMA data and cluster-cloud correlation)
- Companion: (cite: Calzetti15) (LEGUS survey paper and source of galaxy properties)
- Related: LEGUS (Legacy ExtraGalactic UV Survey)
- Related: PHANGS-ALMA
- Related: PAWS
- Related: CANON

## Checks

```json
{
 "quotes": 172,
 "quotes_ok": 172,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 139,
  "stated": 103,
  "rate": 0.741
 },
 "evidence_ok": true
}
```
