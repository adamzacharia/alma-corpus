# LATIS: Comparing Galaxy and IGM Tomography Maps as Tracers of Large-scale Structure and Protoclusters at z ∼ 2.5

`2025ApJ...988...48N` | The Astrophysical Journal 2025 | first author: Newman, Andrew B. | arXiv: 2507.10949 | DOI: 10.3847/1538-4357/ade3c3

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, cosmology
- Question: Are IGM Lya tomography and galaxy (LBG, LAE, submm) surveys consistent tracers of the cosmic web and protoclusters at z~2.5; do candidate UV-dim protoclusters such as IGM-A in Antu host galaxies missed by rest-UV surveys (ALMA part: do 38 submm-selected sources include CO(3-2) members of IGM-A)  
  > "We investigate the consistency of intergalactic medium (IGM) tomography and galaxy surveys as tracers of the cosmic web and protoclusters at $z \sim 2.5$." (abstract); "As a next step toward identifying the missing galaxies in the vicinity of IGM-A, we searched for dusty star-forming galaxies." (An ALMA Search for Dusty Star-forming Members)
- Target **Antu (extended IGM absorption region containing IGM-A to IGM-E)**: coordinates _not stated_; z/distance z = 2.685  
  > "Antu is defined by contiguous Ly$\alpha$ absorption with $\delta_F / \sigma_{\rm map}< -2$ over a volume of $9.9 \times 10^3$ $h^{-3}$ cMpc${}^3$ centered around $z = 2.685$." (A Multitracer Characterization of Antu); distance from LATIS IGM tomography map  
  > "Antu is defined by contiguous Ly$\alpha$ absorption with $\delta_F / \sigma_{\rm map}< -2$ over a volume of $9.9 \times 10^3$ $h^{-3}$ cMpc${}^3$ centered around $z = 2.685$." (A Multitracer Characterization of Antu)
- Target **IGM-A (LATIS2-D2-00), candidate UV-dim protocluster**: coordinates _not stated_; z/distance z ~ 2.685 (within 4 h^-1 cMpc of the z = 2.685 slice)  
  > "This set includes a candidate UV-dim protocluster, LATIS2-D2-00: the strongest single feature in the LATIS COSMOS map." (A Multitracer Characterization of Antu); distance from LATIS IGM tomography map  
  > "This set includes a candidate UV-dim protocluster, LATIS2-D2-00: the strongest single feature in the LATIS COSMOS map." (A Multitracer Characterization of Antu)
- Target **38 SCUBA-2 850 um selected sources near IGM-A (ALMA targets)**: coordinates not stated (Jin18 super-deblended catalog coordinates used)  
  > "In total 38 sources were observed with ALMA in band 3." (An ALMA Search for Dusty Star-forming Members); "We use the (cite: Jin18) coordinates, which agree very well (median separation $0.2\ensuremath{''}$) with ALMA coordinates for a subset of targets with prior continuum detections (cite: Liu19)." (An ALMA Search for Dusty Star-forming Members); z/distance photometric z within 2 sigma (~0.76) of Antu; CO(3-2) searched at redshift of Antu  
  > "In total 38 sources were observed with ALMA in band 3." (An ALMA Search for Dusty Star-forming Members); "We use the (cite: Jin18) coordinates, which agree very well (median separation $0.2\ensuremath{''}$) with ALMA coordinates for a subset of targets with prior continuum detections (cite: Liu19)." (An ALMA Search for Dusty Star-forming Members); distance from Jin18 optical/NIR-based and FIR-based photometric redshifts  
  > "In total 38 sources were observed with ALMA in band 3." (An ALMA Search for Dusty Star-forming Members); "We use the (cite: Jin18) coordinates, which agree very well (median separation $0.2\ensuremath{''}$) with ALMA coordinates for a subset of targets with prior continuum detections (cite: Liu19)." (An ALMA Search for Dusty Star-forming Members)

## Data provenance

- ALMA projects: 2021.1.01005.S
- bands: Band 3  
  > "In total 38 sources were observed with ALMA in band 3." (An ALMA Search for Dusty Star-forming Members)
- frequencies and spectral setup: spectral windows covering +/-1000 km/s around 93.84 GHz (CO(3-2) at redshift of Antu), also extending to lower redshifts  
  > "Spectral windows were set up to encompass $\pm 1000$ km s${}^{-1}$ around 93.84 GHz corresponding to the redshift of Antu" (ALMA Target Selection and Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: typical synthesized beam 1.9'' x 1.4''  
  > "The typical synthesized beam size was $1.9\ensuremath{''} \times 1.4\ensuremath{''}$" (An ALMA Search for Dusty Star-forming Members)
- max recoverable scale: _not stated_
- sensitivity: required 0.16-0.32 mJy/beam integrated over 500 km/s (S850 = 2-10 mJy); design target 5.2 sigma line detection for 90% of sources  
  > "Given our range of $S_{850} = 2$-10 mJy, the required sensitivities ranged from 0.16-0.32 mJy beam${}^{-1}$ (integrated over 500 km s${}^{-1}$)." (ALMA Target Selection and Observations); "Target sensitivities were designed to produce a $5.2 \sigma$ line detection for 90% of sources, as estimated from their 850 $\mu$m flux densities." (An ALMA Search for Dusty Star-forming Members)
- time on source: four bins of integration time, 4-16 min per source  
  > "We sorted the targets into four bins with different integration times of 4-16 min" (ALMA Target Selection and Observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (not stated)
- Other facility **LATIS (Magellan Baade / IMACS spectroscopy)**: IGM Lya tomography maps (3012 sight lines) and LBG density maps (2570 redshifts) used as the context for the ALMA search  
  > "We measure the Ly$\alpha$ forest absorption in 3012 sight lines." (2.1 Observations); "Within the same volume, we map the galaxy distribution using 2570 high-confidence redshifts of LBGs and QSOs from LATIS." (2.1 Observations)
- Other facility **Magellan Baade IMACS narrowband NB448 imaging and spectroscopy**: 945 candidate LAEs over 0.473 deg2 and spectroscopic redshifts for 227 LAEs  
  > "We imaged 0.473 deg${}^2$ of the LATIS COSMOS field through this filter with IMACS (cite: Dressler11) at the Magellan Baade telescope." (5.3 Antu in Lya Emitter Maps); "Follow-up IMACS spectroscopy provided redshifts for 227 LAEs." (5.3 Antu in Lya Emitter Maps)
- Other facility **VUDS and zCOSMOS spectroscopic surveys**: independent galaxy redshifts to check the low LBG density at IGM-A  
  > "We selected galaxies from a merged VUDS+zCOSMOS sample (cite: Lemaux22) with high quality flags (XX3 or XX4)." (5.2 Antu in Lyman-break Galaxy Maps)
- Other facility **C3VO survey maps**: independent galaxy overdensity maps around IGM-A  
  > "We examined galaxy maps from the C3VO survey (cite: Hung25), which use a Voronoi tessellation Monte Carlo mapping technique based on both LBG spectroscopic redshifts and photometric redshifts." (5.2 Antu in Lyman-break Galaxy Maps)
- Other facility **COSMOS2020 catalog**: photometric redshift maps  
  > "We use the COSMOS2020 (cite: Weaver22) catalog built on Farmer photometry (cite: Weaver23)." (5.5 Photometric Redshift Maps)
- External data: SCUBA-2-COSMOS 850 um catalog of sources with SNR > 4 from which ALMA targets were drawn  
  > "We targeted 850-$\mu$m-selected sources with signal-to-noise ratio (SNR) $> 4$ in the SCUBA-2–COSMOS survey catalog (cite: Simpson19)." (An ALMA Search for Dusty Star-forming Members) [from Simpson19 (cite: Simpson19)]
- External data: FIR-to-radio super-deblended catalog used for precise coordinates and photometric redshifts of the targets  
  > "The sources were cross-matched to the far-IR-to-radio “super-deblended” catalog of (cite: Jin18) to provide more precise coordinates and photometric redshift estimates." (An ALMA Search for Dusty Star-forming Members) [from Jin18 (cite: Jin18)]
- External data: Archival ALMA continuum observations used to calibrate SCUBA-2 positional uncertainties and check coordinates  
  > "which were estimated by comparing the Simpson et al. coordinates to those derived from archival ALMA continuum observations for a subset of sources (cite: Liu19)" (ALMA Target Selection and Observations) [from Liu19 (cite: Liu19)]
- External data: L_IR to CO(3-2) line flux relation used to set integration times  
  > "Second, for each source, we estimate the CO(3-2) line flux $S_{\rm CO(3-2)}$ from $L_{\rm IR}$ using the (cite: Greve14) relation, including scatter." (ALMA Target Selection and Observations) [from Greve14 (cite: Greve14)]
- External data: Expected CO line FWHM (500 km/s) used for smoothing kernel  
  > "We first smooth the data cubes along the frequency axis with a 500 km s${}^{-1}$ boxcar kernel, roughly matched to the expected emission line FWHM (cite: Ivison11; CalistroRivera18)." (An ALMA Search for Dusty Star-forming Members) [from Ivison11; CalistroRivera18 (cite: Ivison11; CalistroRivera18)]
- External data: LAE bias b = 1.8 +/- 0.3 at z = 2.1 used for mock LAE populations  
  > "Instead we rely on (cite: Guaita10), who measured a bias of $b = 1.8 \pm 0.3$ for LAEs at $z = 2.1$." (5.3 Antu in Lya Emitter Maps) [from Guaita10 (cite: Guaita10)]
- External data: Merged VUDS+zCOSMOS redshift sample  
  > "We selected galaxies from a merged VUDS+zCOSMOS sample (cite: Lemaux22) with high quality flags (XX3 or XX4)." (5.2 Antu in Lyman-break Galaxy Maps) [from Lemaux22 (cite: Lemaux22)]
- Simulation/model as data: MultiDark Planck 2 (MDPL2) dark matter simulation snapshot at z=2.535 used for mock LATIS surveys  
  > "The first set relies on the 1 $h^{-3}$ Gpc${}^3$ MultiDark Planck 2 (MDPL2; (cite: Klypin16)) dark matter simulation snapshot at $z=2.535$." (2.2 Mock surveys)
- Simulation/model as data: IllustrisTNG300 magnetohydrodynamic simulation mock surveys  
  > "In the second set of mock surveys, we instead use the IllustrisTNG300 (cite: Nelson19) magnetohydrodynamic simulation as described by (cite: Qezlou22)." (2.2 Mock surveys)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline data products  
  > "We use the ALMA pipeline data products and analyze the data cubes in the spectral window of interest, uncorrected for the primary beam in order to provide spatially uniform noise." (5.4 An ALMA Search for Dusty Star-forming Members)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: ALMA pipeline data products used directly for the line search; no further calibration or reprocessing described  
  > "We use the ALMA pipeline data products and analyze the data cubes in the spectral window of interest" (5.4 An ALMA Search for Dusty Star-forming Members)
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
- primary beam correction: cubes analysed uncorrected for the primary beam to give spatially uniform noise  
  > "analyze the data cubes in the spectral window of interest, uncorrected for the primary beam in order to provide spatially uniform noise" (5.4 An ALMA Search for Dusty Star-forming Members)
- array combination: _not stated_
- smoothing: 500 km/s boxcar kernel along the frequency axis  
  > "We first smooth the data cubes along the frequency axis with a 500 km s${}^{-1}$ boxcar kernel, roughly matched to the expected emission line FWHM" (5.4 An ALMA Search for Dusty Star-forming Members)
- final beam: typical synthesized beam 1.9'' x 1.4''  
  > "The typical synthesized beam size was $1.9\ensuremath{''} \times 1.4\ensuremath{''}$" (5.4 An ALMA Search for Dusty Star-forming Members)
- final rms: _not stated_

### Inherited from earlier work

- LATIS IGM and LBG maps, mock surveys and other data are described in the companion paper  
  > "The data and mocks surveys are fully described in the companion paper (N25); here we provide a summary." (2 Summary of Observations and Mock Surveys) [from N25 (cite: Newman25)]
- LATIS survey area and spectroscopy/LBG selection  
  > "LATIS covers the survey area outlined by (cite: Newman20) spanning 1.65 deg${}^2$." (2.1 Observations) [from (cite: Newman20)]
- Halo mass limit for LBGs from galaxy clustering and effective sampling rate  
  > "where the halo mass limit $\log M_{\rm vir} > 11.56$ is chosen to match the autocorrelation function of the halos to that of the observed LBGs (cite: Newman24)" (2.2 Mock surveys) [from (cite: Newman24)]
- LAE spectroscopic data reduction  
  > "The spectroscopic data reduction followed (cite: Newman20)." (9.3 LAE Spectroscopy and 3D Maps) [from (cite: Newman20)]
- Mock survey noise properties and processing mimic LATIS  
  > "we mimic the exact spatial distribution, noise properties, and processing of the LATIS sight lines (cite: Newman22; Newman24)" (2.2 Mock surveys) [from (cite: Newman22; Newman24)]
- Mapping method for IGM maps  
  > "From these sight lines, we create 3D maps of $\delta_F$ using a Wiener filter (cite: Stark15) and smooth the maps using a Gaussian kernel with $\sigma_{\rm sm} = 4$ $h^{-1}$ cMpc." (2.1 Observations) [from (cite: Stark15)]

### Not stated but needed to reproduce (our reading)

- ALMA array, configurations, baselines and observing dates for 2021.1.01005.S
- ALMA pipeline / CASA version and whether archive-delivered products or reprocessed data were used
- Spectral resolution / channel width of the cubes and any continuum subtraction
- Order of the low-order polynomial fitted to rms versus frequency and how the SNR cube was normalised
- Exact positions and IDs of the 38 targets and of the five cases given 4'' search apertures
- Per-source achieved rms and the number of sources reaching the design sensitivity
- Flux calibrator and flux-scale uncertainty
- How non-detections were converted to limits on CO(3-2) flux or L_IR
- IGM-A tomographic map values and catalog depend on the companion paper N25 and the unreleased LATIS data release

## Analysis recipe

1. **Build LATIS IGM and LBG overdensity maps**: Wiener-filter 3D reconstruction of delta_F from sight lines, Gaussian smoothing; LBG density from inverse-ESR-weighted galaxies smoothed with the same kernel  
  > "From these sight lines, we create 3D maps of $\delta_F$ using a Wiener filter (cite: Stark15) and smooth the maps using a Gaussian kernel with $\sigma_{\rm sm} = 4$ $h^{-1}$ cMpc." (2.1 Observations); "Maps of the galaxy density $n$ are created by weighting each galaxy by the inverse of the effective sampling rate (cite: Newman24)" (2.1 Observations)
   - parameter: maps span z=2.2-2.8 with voxel size (1 h^-1 cMpc)^3  
  > "The maps span $z=2.2$–2.8 and have a voxel size of $(1~h^{-1}~\textrm{cMpc})^3$." (2.1 Observations)
   - fitting: _not stated_
   - validation: uncertainties in delta_LBG estimated from mock surveys  
  > "We estimate the uncertainties in $\delta_{\rm LBG}$ using the mock surveys described below." (2.1 Observations)
2. **Compare observed delta_F-delta_LBG distribution and peak trends with FGPA mock surveys**: Joint distribution over voxels compared to MDPL2 mocks; Pearson test on independent subset; LOESS conditional-mean trend for absorption peaks compared to mocks  
  > "Since neighboring voxels are correlated by our smoothing kernel, for this test, we considered an approximately independent subset spaced by 9 $h^{-1}$ cMpc on each axis" (3 The Global Correlation between IGM Absorption and LBG Density); "We estimate this trend in the conditional mean $\langle \delta_{\rm LBG} | \delta_F \rangle$ using locally estimated scatterplot smoothing (LOESS, (cite: Cleveland79))" (4 The LBG Content of IGM-selected Overdensities)
   - software: MDPL2 mocks, IllustrisTNG300 mocks, LOESS
   - parameter: Peaks defined as local minima of the delta_F map  
  > "defined as the locations where the $\delta_F$ map reaches a local minimum (i.e., absorption is maximal)" (4 The LBG Content of IGM-selected Overdensities)
   - parameter: Outlier = below bottom 5% of mock delta_halo distribution conditional on delta_F  
  > "Gray bands in Fig. [3](#fig:dFdgalindiv) denote the bottom 1% and 5% of the $\delta_{\rm halo}$ distribution in the mocks, conditional on $\delta_F$." (4 The LBG Content of IGM-selected Overdensities)
   - assumption: Ly-alpha optical depth from the fluctuating Gunn-Peterson approximation; spatially uniform ionizing radiation field  
  > "which assumes that the IGM gas follows a tight global relation between temperature and density and that the ionizing radiation field is spatially uniform" (2.2 Mock surveys)
   - assumption: LBGs trace dark matter halos with log Mvir > 11.56 independent of large-scale environment  
  > "where the halo mass limit $\log M_{\rm vir} > 11.56$ is chosen to match the autocorrelation function of the halos to that of the observed LBGs" (2.2 Mock surveys)
   - fitting: _not stated_
   - validation: Observed data always compared with forward-modelled mocks; HCD contamination tested with IllustrisTNG300 mocks  
  > "When analyzing LATIS data, we always compare to the mock surveys and thereby naturally incorporate all variance and biases produced by the known sources of noise." (3 The Global Correlation between IGM Absorption and LBG Density); "To investigate this possibility, we repeated our analysis using the IllustrisTNG300 mocks, which do include HCD lines with a realistic incidence as a function of column density" (4 The LBG Content of IGM-selected Overdensities)
3. **Measure LBG, LAE and photometric-redshift content of Antu and its IGM peaks**: delta_LBG, delta_LAE (narrowband photometric and spectroscopic) measured at IGM peaks and compared to mock conditional distributions; independent check with VUDS+zCOSMOS  
  > "We considered the galaxy redshift distribution along a sight line toward IGM-A, using the same isotropic Gaussian kernel ($\sigma = 4$ $h^{-1}$ cMpc) applied to the LATIS maps." (5.2 Antu in Lyman-break Galaxy Maps); "For each mock survey, we subsample $M_{\rm vir} > 10^{10.9} M_{\odot}$ halos to match the mean number density of our spectroscopic LAEs" (5.3 Antu in Lya Emitter Maps)
   - software: SExtractor, scamp, swarp, EAZY, Colossus
   - parameter: NB448 filter transmits Lya within +/-3500 km/s of z=2.685  
  > "We obtained a custom narrowband filter NB448 designed to transmit Ly$\alpha$ emission within $\pm 3500$ km s${}^{-1}$ of $z=2.685$." (5.3 Antu in Lya Emitter Maps)
   - assumption: LAE halo mass threshold set from clustering bias b = 1.8 +/- 0.3 of Guaita10  
  > "Instead we rely on (cite: Guaita10), who measured a bias of $b = 1.8 \pm 0.3$ for LAEs at $z = 2.1$." (5.3 Antu in Lya Emitter Maps)
   - fitting: _not stated_
   - validation: Bootstrap resampling used for VUDS+zCOSMOS delta_LBG uncertainty  
  > "where the uncertainty is estimated from bootstrap resampling" (5.2 Antu in Lyman-break Galaxy Maps)
4. **Select ALMA targets near IGM-A**: SCUBA-2 COSMOS 850 um sources cross-matched to Jin18, kept if a photometric redshift is within 2 sigma of the targeted peak, and not already excluded by spectroscopic redshifts or archival proposals  
  > "we next required that either photometric redshift estimate be within $2\sigma$ of one of the targeted Ly$\alpha$ absorption peaks." (ALMA Target Selection and Observations)
   - parameter: SCUBA-2 sources with SNR > 4 within 8 arcmin (~10 h^-1 cMpc) of LATIS2-D2-00 or LATIS2-D2-07  
  > "We first identified sources within 8 arcmin ($\approx 10$ $h^{-1}$ cMpc) of either of two nearby IGM absorption peaks, LATIS2-D2-00 or LATIS2-D2-07" (ALMA Target Selection and Observations)
   - parameter: Jin18 match found for 92% of sources  
  > "We found a positional match to 92% of sources." (ALMA Target Selection and Observations)
   - parameter: 61 sources after photo-z cut; 16 removed by spectroscopic z and 7 by archival ALMA proposals, leaving 38  
  > "Of the 61 remaining sources, 16 were eliminated on the basis of a LATIS or literature spectroscopic redshift inconsistent with LATIS2-D2-00" (ALMA Target Selection and Observations); "The remaining 38 sources were observed with ALMA using band 3 to target the CO(3-2) emission line." (ALMA Target Selection and Observations)
   - assumption: optical/NIR photo-z uncertainty 2 sigma ~ 0.76, allowing z_phot ~ 1.9-3.4  
  > "we empirically estimated $2 \sigma_{z_{\rm phot}} \approx 0.76$ by comparing to LATIS and literature spectroscopic redshifts" (ALMA Target Selection and Observations)
   - fitting: _not stated_
   - validation: _not stated_
5. **Set ALMA integration times from expected CO(3-2) fluxes**: Mean S850-L_IR relation from Jin18, CO(3-2) flux from L_IR with Greve14 relation, then conservative S_CO(3-2) = 0.34 S850 (10th percentile); targets sorted into four integration-time bins  
  > "Third, rather than using this noisy estimate for each source, we derived a relation $S_{\rm CO(3-2)} = 0.34 S_{850}$ that conservatively is based on the 10th percentile of the individual $S_{\rm CO(3-2)}$ estimates." (ALMA Target Selection and Observations)
   - parameter: aim SNR > 3 over FWHM/3, or SNR > 5.2 over the FWHM; integration times 4-16 min  
  > "We sorted the targets into four bins with different integration times of 4-16 min, aiming to reach ${\rm SNR} > 3$ over FWHM/3, or ${\rm SNR} > 5.2$ over the FWHM." (ALMA Target Selection and Observations)
   - assumption: CO(3-2) line FWHM of 500 km/s  
  > "assuming a FWHM of 500 km s${}^{-1}$" (ALMA Target Selection and Observations)
   - fitting: _not stated_
   - validation: _not stated_
6. **Search ALMA cubes for CO(3-2) emission at the redshift of IGM-A**: Smooth cubes in frequency with a 500 km/s boxcar, fit low-order polynomial to rms versus frequency, build SNR cube, search within 2'' diameter apertures (4'' for five ambiguous counterparts) for SNR > 4.5 within +/-1000 km/s; negative-cube test for lower-threshold candidates  
  > "We then fit a low-order polynomial to the rms fluctuations as a function of frequency, built a SNR cube, and finally search for significant line emission within the search apertures described above." (5.4 An ALMA Search for Dusty Star-forming Members); "We find no lines with ${\rm SNR} > 4.5$ within $\pm 1000$ km s${}^{-1}$ of IGM-A" (5.4 An ALMA Search for Dusty Star-forming Members)
   - software: ALMA pipeline
   - parameter: 2'' diameter search circle, 4'' for five outlier sources  
  > "We search for significant detection of emission near each target, generally within a $2''$-diameter circle, slightly larger than the synthesized beam." (5.4 An ALMA Search for Dusty Star-forming Members); "In these few cases, we allow a larger $4''$-diameter search aperture." (5.4 An ALMA Search for Dusty Star-forming Members)
   - assumption: Jin18 coordinates used as target positions  
  > "We use the (cite: Jin18) coordinates, which agree very well (median separation $0.2\ensuremath{''}$) with ALMA coordinates for a subset of targets with prior continuum detections (cite: Liu19)." (5.4 An ALMA Search for Dusty Star-forming Members)
   - fitting: _not stated_
   - validation: Result unchanged when search aperture radii doubled; lower-threshold candidates equal in number in negative SNR cubes, consistent with noise  
  > "a conclusion that is unchanged even if we double the search aperture radii" (5.4 An ALMA Search for Dusty Star-forming Members); "the number of such candidates is similar if we analyze the negative of the SNR cubes, suggesting that they are consistent with expected noise peaks" (5.4 An ALMA Search for Dusty Star-forming Members)

## Software

- **ALMA pipeline** : calibrated data products and cubes used for the CO(3-2) line search  
  > "We use the ALMA pipeline data products and analyze the data cubes in the spectral window of interest" (5.4 An ALMA Search for Dusty Star-forming Members)
- **SExtractor** : dual-image source catalogs and NB448/B flux measurements  
  > "`SExtractor` (cite: sextractor) was then used in dual-image mode to create catalogs of $B$-band selected sources and measure $B$ and NB448 fluxes." (9.1 Narrowband Imaging)
- **scamp and swarp** : registering NB448 images to a Subaru SuprimeCam B-band image  
  > "We used `scamp` (cite: scamp) and `swarp` (cite: swarp) to register the NB448 images to a Subaru SuprimeCam $B$-band image (cite: Capak07)." (9.1 Narrowband Imaging)
- **EAZY** : photometric redshifts in COSMOS2020, compared with spectroscopic redshifts to calibrate bias and scatter  
  > "By comparing redshifts $z_{\rm phot}$ estimated using `EAZY` (cite: Brammer08) to spectroscopic redshifts from LATIS and other sources" (5.5 Photometric Redshift Maps)
- **Colossus** : halo mass limit matching the LAE bias  
  > "We estimate this limit using the `Colossus` code (cite: Diemer18), the bias relation of (cite: Tinker10), and the halo mass function of (cite: Comparat17)." (Footnote 9)
- **LOESS** : trend of conditional mean delta_LBG given delta_F  
  > "We estimate this trend in the conditional mean $\langle \delta_{\rm LBG} | \delta_F \rangle$ using locally estimated scatterplot smoothing (LOESS, (cite: Cleveland79))" (4 The LBG Content of IGM-selected Overdensities)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA band 3 targets observed | 38 | not stated | sources | 4 | In total 38 sources were observed with ALMA in band 3. |
| Significant CO(3-2) lines (SNR > 4.5) within +/-1000 km/s of IGM-A | 0 detections | not stated | dimensionless | 6 | We find no lines with ${\rm SNR} > 4.5$ within $\pm 1000$ km s${}^{-1}$ of IGM-A |
| Adopted S_CO(3-2) to S_850 relation for sensitivity planning | 0.34 | not stated | dimensionless | 5 | we derived a relation $S_{\rm CO(3-2)} = 0.34 S_{850}$ |
| Significance of delta_F-delta_LBG Pearson correlation | 35 sigma (p = 1e-258) | not stated | sigma | 2 | The $p$-value for a Pearson correlation test is $10^{-258}$ corresponding to $35\sigma$ significance. |
| Strongest absorption peaks (delta_F/sigma_map < -3.5) with delta_LBG in bottom 5% of mocks | 4 of 16 (25%) | not stated | peaks | 2 | Among the 16 strongest absorption peaks, we find that 4 (25%) are in the bottom 5% of the mocks. |
| Fraction of mock surveys with as many or more low-delta_LBG outliers | 0.3-0.8% | not stated | percent | 2 | We find an equal or larger number of such outliers in just 0.3-0.8% of mock survey realizations. |
| Antu tomographic mass M_tomo | 10^15.5 | +/-0.2 (dex) | Msun | 3 | Antu has about half the mass, $M_{\rm tomo} = 10^{15.5 \pm 0.2}M_{\odot}$. |
| Antu contiguous absorption volume (delta_F/sigma_map < -2) | 9.9e3 | not stated | h^-3 cMpc^3 | 3 | over a volume of $9.9 \times 10^3$ $h^{-3}$ cMpc${}^3$ centered around $z = 2.685$ |
| LBG overdensity at IGM-A (LATIS) | -0.5 | not stated | dimensionless | 3 | On the other hand, IGM-A has a surprisingly low $\delta_{\rm LBG} = -0.5$ |
| LBG overdensity at IGM-A from VUDS+zCOSMOS | 0.3 | 0.5 | dimensionless | 3 | In particular, at the redshift of IGM-A we find $\delta_{\rm LBG}^{\rm VUDS+zC} = 0.3 \pm 0.5$, where the uncertainty is estimated from bootstrap resampling. |
| Expected number of LATIS-parent-sample galaxies in IGM-A if normally populated | 26 | 9 | galaxies | 3 | Therefore we expect IGM-A to contain $(1 + \delta_{\rm halo}) \langle N \rangle = 26 \pm 9$ galaxies within the LATIS spectroscopic parent sample |
| Fraction of mock structures with matched delta_F having lower delta_LAE than IGM-A | 1.6% | not stated | percent | 3 | just 1.6% of mock-observed structures with matched $\delta_F$ have a lower $\delta_{\rm LAE}$ |
| Narrowband LAE candidates / spectroscopic LAE redshifts | 945 candidates; 227 redshifts | not stated | sources | 3 | we identified 945 candidate LAEs with a rest-frame equivalent width ${\rm EW}_0 \gtrsim 20$ Å and line fluxes $F_{\rm Ly\alpha} \gtrsim 1 \times 10^{-17}$ erg cm${}^{-2}$ s${}^{-1}$.; Follow-up IMACS spectroscopy provided redshifts for 227 LAEs. |
| Number of strong Lya absorption peaks (delta_F < -0.15) in LATIS | 29 | not stated | peaks | 2 | LATIS contains 29 strong Ly$\alpha$ absorption peaks in this range. |

## Qualitative findings

- No ALMA-targeted submillimeter-selected source is a likely member of IGM-A  
  > "We conclude that none of the ALMA targets are likely to be members of IGM-A." (5.4 An ALMA Search for Dusty Star-forming Members)
- Lya emitters trace Antu overall but IGM-A is deficient in both LBGs and LAEs  
  > "Ly$\alpha$ emitters trace the overall structure of Antu but avoid the center of the candidate UV-dim protocluster, which also appears to contain no submillimeter-selected sources." (abstract)
- Photometric redshift maps do not show a large overdensity in Antu; non-detection is not informative at these masses  
  > "Fig. [5](#fig:montage) shows that there is no large overdensity of $z_{\rm phot}$-selected galaxies within Antu." (5.5 Photometric Redshift Maps)

## Claim tuples

- H: IGM absorption and LBG density, as traced by LATIS, follow a simple FGPA plus halo-tracer model | E: Compare observed delta_F-delta_LBG joint distribution and conditional means with forward-modelled MDPL2 mock surveys | R: Correlation at 35 sigma; mocks reproduce the joint distribution over nearly all of the volume and the mean trends | F: A simple physical model describes the mean relation between IGM absorption and LBG density | **supported**
- H: Some strong IGM absorption peaks are UV-dim protoclusters lacking detected LBGs | E: Measure delta_LBG at 16 strongest absorption peaks and compare to conditional mock distributions | R: 4 of 16 (25%) lie in the bottom 5% of mocks; only 0.3-0.8% of mocks contain as many | F: Four systems are excellent candidates for UV-dim protoclusters, but follow-up is needed to verify | **partially**
- H: IGM-A within Antu hosts galaxies missed by LBG selection, such as LAEs or dusty submillimeter galaxies | E: LAE narrowband and spectroscopic maps, VUDS/zCOSMOS and C3VO comparison, photo-z maps, and ALMA Band 3 CO(3-2) search of 38 SCUBA-2 sources | R: IGM-A is low in LBGs and LAEs; LAEs trace the rest of Antu; no CO(3-2) lines with SNR > 4.5 among ALMA targets | F: IGM-A shows deficits in LBGs and LAEs and no submm-selected members, so the missing population is not obscured starbursts at these flux levels | **supported**
- H: Hydrodynamics or feedback strongly alter the Lya transmission-density relation at high density | E: Compare the number of strong absorption peaks in mocks with a shift in delta_F to the observed count | R: Modest uniform shift of +0.013 in delta_F/sigma_map would produce a 5 sigma underproduction of strong peaks | F: LATIS peak counts rule out a systematic deviation from the FGPA as strong as that proposed by Kooistra22a | **supported**

## Reasoning

- Why this data: ALMA search follows from wanting to find the missing galaxies in IGM-A, targeting dusty star-forming galaxies; sources chosen for photo-z consistency to improve efficiency  
  > "As a next step toward identifying the missing galaxies in the vicinity of IGM-A, we searched for dusty star-forming galaxies." (5.4 An ALMA Search for Dusty Star-forming Members); "To improve the program’s efficiency, we selected only sources for which at least one of the two cataloged photometric redshift estimates (optical/near-IR-based, or far-IR based) is within $|\Delta z| < 2 \sigma \approx 0.76$ of Antu." (5.4 An ALMA Search for Dusty Star-forming Members)
- Why this method: _not stated_
- Alternative: Spuriously enhanced IGM absorption in IGM-A; judged unlikely because absorption is spread over many sight lines and insensitive to removing individual sight lines  
  > "We also considered the possibility that the IGM absorption in IGM-A is spuriously enhanced, such that the matter and the expected galaxy overdensities are simply overestimated." (6.3 Antu)
- Alternative: High column density absorbers as the origin of outliers; statistically argued not to explain all outliers  
  > "we find that it cannot readily explain the outlier population either" (4 The LBG Content of IGM-selected Overdensities)
- How they decided it was enough: Integration times set to give a 5.2 sigma line detection for 90% of sources  
  > "Target sensitivities were designed to produce a $5.2 \sigma$ line detection for 90% of sources, as estimated from their 850 $\mu$m flux densities." (5.4 An ALMA Search for Dusty Star-forming Members)
- Limitation (authors): ALMA coverage is a subregion near IGM-A and does not cover the full extent of Antu  
  > "The ALMA observations do not cover the full extent of Antu, but rather target a subregion within $\simeq 8$ arcmin ($\simeq 10$ $h^{-1}$ cMpc) of IGM-A." (5.4 An ALMA Search for Dusty Star-forming Members)
- Limitation (authors): Submillimeter selection probes galaxies about 10x more massive than the LBG-mass galaxies that are missing, so lower-mass dusty galaxies remain possible  
  > "Lower-mass dusty galaxies thus remain a candidate" (6.3 Antu)
- Limitation (authors): IGM-A being a real overdensity cannot be confirmed until a coincident galaxy overdensity is found  
  > "Until we find a commensurate and coincident galaxy overdensity, this will remain a possibility." (6.3 Antu)
- Caveat (inferred, ours): ALMA depth is shallow (4-16 min per source) and is tuned to a conservative L_IR-derived CO flux, so non-detections constrain only bright CO emitters
- Caveat (inferred, ours): Only 38 pre-selected submm sources were observed; fainter or lower-mass dusty members would be missed
- Caveat (inferred, ours): No upper limits on CO flux or L_IR are reported for the non-detections
- Caveat (inferred, ours): ALMA array, calibration and imaging details are absent, so the ALMA result cannot be independently re-derived from the paper alone
- Caveat (inferred, ours): Main results rely on the unreleased LATIS data and mocks described in N25

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: LATIS IGM maps, LBG maps and mock surveys (described in N25, not in this paper)
- Missing: ALMA array, calibration, imaging and cube-making details for project 2021.1.01005.S
- Missing: Target list with IDs and coordinates
- Missing: Polynomial order and noise normalisation for the SNR cubes
- Data volume (inferred): Moderate (tens of GB): 38 short Band 3 pointings for one ALMA project; the LATIS and Magellan data are not on ALMA archive.
- Score (inferred): 2/5, The ALMA part is a brief non-detection search with sparse settings, and the main results rely on LATIS maps, mocks and Magellan data that are not public or fully described in this paper.
- Rediscovery candidate: no, ALMA plays a minor role, the recipe is incomplete, and the key results depend on non-public LATIS data and companion-paper products.

## Links

- Method: Newman20 (cite: Newman20) (LATIS survey design, spectroscopy and LBG selection)
- Method: Newman24 (cite: Newman24) (LATIS galaxy clustering and halo mass for the mock galaxy model)
- Method: Jin18 (cite: Jin18) (super-deblended catalog for ALMA target coordinates and redshifts)
- Method: Simpson19 (cite: Simpson19) (SCUBA-2 COSMOS 850 um catalog used for target selection)
- Companion: Newman25 (N25) (cite: Newman25) (catalog of 37 protogroups and protoclusters from LATIS IGM maps; full description of data and mocks)
- Companion: Newman22 (cite: Newman22) (earlier LATIS analysis of UV-dim protoclusters, revised here)
- Related: LATIS
- Related: CLAMATO
- Related: COSMOS
- Related: SCUBA-2 COSMOS
- Related: VUDS
- Related: zCOSMOS
- Related: C3VO

## Checks

```json
{
 "quotes": 120,
 "quotes_ok": 120,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 116,
  "stated": 79,
  "rate": 0.681
 },
 "evidence_ok": true
}
```
