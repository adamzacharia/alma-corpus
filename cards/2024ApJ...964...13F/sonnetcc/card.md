# ALMA-LEGUS. II. The Influence of Subgalactic Environments on Molecular Cloud Properties

`2024ApJ...964...13F` | The Astrophysical Journal 2024 | first author: Finn, Molly K. | arXiv: 2401.01451 | DOI: 10.3847/1538-4357/ad198a

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: How do molecular cloud properties differ between sub-galactic regions (bar, arms, interarm, center, ring, outer) of barred spiral NGC 1313 and flocculent spiral NGC 7793, and how does this relate to their different massive cluster formation?  
  > "We compare the molecular cloud properties in sub-galactic regions of two galaxies, barred spiral NGC 1313, which is forming many massive clusters, and flocculent spiral NGC 7793" (abstract)
- Target **NGC 1313**: coordinates _not stated_; z/distance _not stated_; distance from cited as RadburnSmith11; Qing15; Gao16; Sabbi18 (values not given in this paper)  
  > "their similar distances (cite: RadburnSmith11; Qing15; Gao16; Sabbi18)" (Introduction)
- Target **NGC 7793**: coordinates _not stated_; z/distance _not stated_; distance from cited as RadburnSmith11; Qing15; Gao16; Sabbi18 (values not given in this paper)  
  > "their similar distances (cite: RadburnSmith11; Qing15; Gao16; Sabbi18)" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00782.S
- bands: Band 6  
  > "using Band 6 covering the" (Observations: CO(2-1))
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m array  
  > "with the 12m array" (Observations: CO(2-1))
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Beam 0.58 arcsec (13 pc) for NGC 1313; 0.72 arcsec (13 pc) for NGC 7793  
  > "| NGC 1313 |   0.58   |  13  | 0.15  |       1.33        |" (Table 1); "| NGC 7793 |   0.72   |  13  |  0.2  |       1.33        |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: rms 0.15 K (NGC 1313); 0.2 K (NGC 7793); velocity resolution 1.33 km/s  
  > "| NGC 1313 |   0.58   |  13  | 0.15  |       1.33        |" (Table 1); "| NGC 7793 |   0.72   |  13  |  0.2  |       1.33        |" (Table 1)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Program 2015.1.00782.S, PI K. E. Johnson  
  > "(project code 2015.1.00782.S; PI: K. E. Johnson)" (Observations: CO(2-1))
- Line: 12CO J=2-1 (not stated)
- Other facility **HST LEGUS**: Star cluster catalogs with SED-fitted masses, ages and extinctions  
  > "we use the catalogs of identified star clusters and their SED-fitted masses, ages, and extinctions from the LEGUS collaboration" (Cluster Catalogs)
- Other facility **Digitized Sky Survey (DSS2-red)**: Red-filter image contours used to define sub-galactic regions  
  > "we use contours of the red filter from Digitized Sky Survey (DSS) images of the two galaxies" (Region Selection)
- External data: Cloud structures (clumps, dendrogram trunks/branches/leaves) and their properties (M, R, sigma_v, alpha_vir, Sigma, P_e, t_ff) from Paper 1 Appendix A tables  
  > "as well as all the properties calculated for these structures in Paper 1 as described in Section 5 and published in the tables of that paper" (Observations: CO(2-1)) [from Finn et al. 2024, Paper 1 (cite: Finn23a)]
- External data: LEGUS star cluster catalogs (masses, ages, extinctions); 90% mass completeness approx 1000 Msun for ages up to 200 Myr  
  > "we expect the 90% mass completeness limit of these catalogs to be approximately 1000 M$_\odot$ for clusters up to ages of 200 Myr" (Cluster Catalogs) [from LEGUS collaboration, methodology of (cite: Adamo17)]
- External data: Global size-linewidth intercepts: a0 = 0.41 +/- 0.01 (NGC 1313), 0.33 +/- 0.01 (NGC 7793)  
  > "In Paper 1, we fit intercepts of $a_0=0.41\pm0.01$ in NGC 1313, and $a_0=0.33\pm0.01$ for NGC 7793" (Size-Linewidth Relations) [from Paper 1 (cite: Finn23a)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: Pipeline-CASA51-P2-B v.40896 (listed in Software section)  
  > "Pipeline-CASA51-P2-B v.40896 (cite: Davis21)" (Software)
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
- final beam: 0.58 arcsec (13 pc) NGC 1313; 0.72 arcsec (13 pc) NGC 7793  
  > "| NGC 1313 |   0.58   |  13  | 0.15  |       1.33        |" (Table 1); "| NGC 7793 |   0.72   |  13  |  0.2  |       1.33        |" (Table 1)
- final rms: 0.15 K (NGC 1313); 0.2 K (NGC 7793)  
  > "| NGC 1313 |   0.58   |  13  | 0.15  |       1.33        |" (Table 1); "| NGC 7793 |   0.72   |  13  |  0.2  |       1.33        |" (Table 1)

### Inherited from earlier work

- ALMA observation details, data reduction and imaging  
  > "The details of these observations, the data reduction, and the imaging process are discussed in Paper 1" (Observations: CO(2-1)) [from Paper 1 (cite: Finn23a)]
- Clump and dendrogram identification with quickclump and astrodendro  
  > "the clumps and dendrogram structures identified in Section 4 of Paper 1 using" (Observations: CO(2-1)) [from Section 4 of Paper 1 (cite: Finn23a); (cite: Sidorin17); (cite: Rosolowsky08)]
- Calculation of cloud properties (mass, radius, velocity dispersion, virial parameter, surface density, external pressure, free-fall time)  
  > "all the properties calculated for these structures in Paper 1 as described in Section 5" (Observations: CO(2-1)) [from Section 5 and Appendix A of Paper 1 (cite: Finn23a)]
- LEGUS cluster catalogs and their methodology  
  > "As in Paper 1, we use the catalogs of identified star clusters and their SED-fitted masses, ages, and extinctions from the LEGUS collaboration, which follow the methodology of (cite: Adamo17)." (Cluster Catalogs) [from Paper 1 (cite: Finn23a); (cite: Adamo17)]
- Bootstrapped two-sample KS and AD tests for comparing distributions  
  > "As in Paper 1, we also quantify these differences in property distributions using bootstrapped two-sample Kolmogorov-Smirnoff (KS) tests and Anderson-Darling (AD) tests." (Property Distribution Comparisons) [from Paper 1 (cite: Finn23a)]
- Global size-linewidth intercepts for the two galaxies  
  > "Note: Global fitted intercepts from Paper 1." (Table 2) [from Paper 1 (cite: Finn23a)]

### Not stated but needed to reproduce (our reading)

- Calibration, CASA version, imaging (tclean) settings, robust, continuum subtraction and cube construction are all deferred to Paper 1
- Paper 1 Appendix A cloud property tables (or the cubes plus quickclump/astrodendro parameters) needed to reproduce any result
- Distances and inclinations adopted for NGC 1313 and NGC 7793 and the CO-to-H2 conversion factor used for masses
- Exact region polygons or contour levels' numerical map and how each clump or cluster is assigned to a region
- How the intercept a0 and its uncertainty were fit (algorithm, weighting, treatment of errors)
- Bandwidth and normalisation of the 2D KDE contours in the virial plots
- Whether bootstrap subsamples are drawn with or without replacement, random seed, and p-value averaging details
- DSS2-red image source and version used for the contours
- Which of the dendrogram structure levels (leaves, branches, trunks) enter each size-linewidth fit

## Analysis recipe

1. **Define sub-galactic regions**: Contours of DSS2-red images define bar, N arm, S arm, interarm (NGC 1313) and center, ring, outer (NGC 7793) regions  
  > "The bar region is based on the 75% brightness contour in the DSS2-red image" (Region Selection); "we instead split the galaxy up into a circular" (Region Selection)
   - parameter: NGC 1313 arms: 60% contour around emission, following arm out to 40% contour; NGC 7793 center 75% contour, ring 60% contour  
  > "the arm regions enclose the emission within the 60% contours, then follow the arm pattern out to the edges of the CO(2-1) map following the 40% contour" (Region Selection); "region surrounding the center following the 60% contour" (Region Selection)
   - assumption: Red DSS2 light traces the bulk of the stellar population  
  > "which traces the bulk of the stellar population" (Region Selection)
   - fitting: _not stated_
   - validation: _not stated_
2. **Compare cluster mass and age distributions by region**: Gaussian KDEs and CDFs of LEGUS cluster masses and ages, for all and for young clusters  
  > "we plot their mass and age distributions using Gaussian kernel density estimations (KDEs) from" (Cluster Property Distributions)
   - software: scipy
   - parameter: KDE scalar bandwidth 0.5 dex; young = age < 10 Myr; massive = M > 10^4 Msun  
  > "we adopt a scalar estimator bandwidth of 0.5 dex" (Cluster Property Distributions)
   - fitting: _not stated_
   - validation: CDFs used alongside KDEs because they do not depend on binning  
  > "while CDFs do not rely on binning and so are more robust but less intuitive in understanding the underlying distribution" (Cluster Property Distributions)
3. **Fit size-linewidth relation per region**: Power law sigma_v = a0 R^a1 fitted to dendrogram structures in each region, fitting only the intercept  
  > "We fit power laws to the dendrogram structures in each region of the form" (Size-Linewidth Relations)
   - parameter: Slope fixed at a1 = 0.5  
  > "we fit only the intercept of this power law relation, holding the slope constant at a value of $a_1=0.5$" (Size-Linewidth Relations)
   - assumption: Fitted intercept indicates relative kinetic energy of clouds at a given size scale  
  > "This fitted intercept indicates the relative amount of kinetic energy in clouds of a given size scale between regions." (Size-Linewidth Relations)
   - fitting: _not stated_
   - validation: Fixed-slope choice said not to change conclusions about relative kinetic energy; intercepts compared at 3 sigma  
  > "The assumed value of the fixed slope affects the value of the fitted intercept, but not the conclusions about the relative kinetic energy in the regions." (Size-Linewidth Relations)
4. **Compare virialization by region**: Plot sigma_v^2/R against surface density per region with the virial equilibrium line and 2D KDE contours  
  > "We next compare the balance between gravitational and kinetic energy in the clouds of the different regions by plotting their velocity metrics" (Virialization)
   - software: scipy
   - parameter: KDE contours at 20% and 50% of the maximum density; free-fall line at alpha_vir = 2  
  > "the distribution of clouds in each region are depicted with contours of the two-dimensional KDEs showing 20% and 50% of the maximum density" (Virialization)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare cloud property distributions by region**: KDEs and CDFs of non-overlapping clump properties (mass, radius, linewidth, alpha_vir, surface density, P_e, t_ff) within each region and against the global distribution of the other galaxy  
  > "by looking at KDEs and CDFs of the non-overlapping clump structures" (Property Distribution Comparisons)
   - software: scipy
   - parameter: Clumps used for counting statistics because dendrograms count emission multiple times  
  > "dendrograms count emission multiple times, and so cannot be used in any sort of counting statistic" (Observations: CO(2-1))
   - fitting: _not stated_
   - validation: _not stated_
6. **Test distribution differences between regions**: Bootstrapped two-sample KS and AD tests: 1000 random subsamples of 65 points, average p-value, for every property and region pair  
  > "We take 1000 random subsamples with a size of 65 data points, perform KS and AD tests between each pairing of regions, and report the average $p$-value for the 1000 subsamples." (Kolmogorov-Smirnoff and Anderson-Darling Tests)
   - parameter: Subsample size 65, limited by the number of clumps in the NGC 1313 bar; significance threshold p < 0.05  
  > "We choose a sample size of 65 because we are limited by the the number of clumps identified in the bar of NGC 1313." (Property Distribution Comparisons)
   - assumption: Full-sample KS/AD tests are overpowered and detect variations below measurement errors  
  > "Using the full sample size of the galaxies results in an overpowered statistic as described in (cite: Lazariv18)" (Property Distribution Comparisons)
   - fitting: _not stated_
   - validation: p-values depend strongly on subsample size, so used only to rank which properties are more likely to differ  
  > "This is meant as an indication of which pairings are the most likely to be different, not whether the underlying distributions are truly, statistically different." (Kolmogorov-Smirnoff and Anderson-Darling Tests)

## Software

- **CASA Pipeline (Pipeline-CASA51-P2-B)** v.40896: _not stated_
- **CASA** : _not stated_
- **astrodendro** : Dendrogram structure identification (done in Paper 1)  
  > "the clumps and dendrogram structures identified in Section 4 of Paper 1 using" (Observations: CO(2-1))
- **quickclump** : Clump identification (done in Paper 1)  
  > "the clumps and dendrogram structures identified in Section 4 of Paper 1 using" (Observations: CO(2-1))
- **scipy** : Gaussian kernel density estimates  
  > "we plot their mass and age distributions using Gaussian kernel density estimations (KDEs) from" (Cluster Property Distributions)
- **Astropy** : _not stated_
- **Matplotlib** : _not stated_
- **NumPy** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of clumps, NGC 1313 / NGC 7793 (all regions) | 531 / 965 | not stated | dimensionless | 0 | / NGC 1313 / All      / 65       / 82       / 442      / 531      / 137; / NGC 7793 / All      / 130      / 187      / 761      / 965      / 306 |
| Number of LEGUS clusters, NGC 1313 / NGC 7793 (all) | 1201 / 467 | not stated | dimensionless | 0 | / 1201  / 618       / 333         / 37         /; / 467   / 296       / 53          / 3          / |

## Qualitative findings

- Spiral arms and the center of NGC 7793 have higher masses, linewidths, pressures and virial parameters than interarm and outer regions; surface densities differ little between regions.  
  > "There are higher masses, linewidths, pressures, and virial parameters in the arms of NGC 1313 and center of NGC 7793 than in the interarm and outer regions of the galaxies." (abstract)
- NGC 7793 clouds are as massive and have as much kinetic energy as NGC 1313 arm clouds but lower density and pressure, so are less inclined to collapse.  
  > "Meanwhile NGC 7793 has clouds that are as massive and have as much kinetic energy as clouds in the arms of NGC 1313" (abstract)

## Claim tuples

- H: Do cloud property variations between regions within a galaxy exceed the variations between the two galaxies globally? | E: Compared size-linewidth intercepts, virial plots and cloud property distributions across regions and galaxies | R: Larger regional variation within each galaxy than between galaxies globally, especially in NGC 1313 | F: Local environment influences cloud properties more than global galaxy environment | **supported**
- H: Do NGC 1313 spiral arms contain clouds with more kinetic energy than the bar and interarm? | E: Fixed-slope size-linewidth fits per region | R: Intercepts 0.49 (S arm), 0.40 (N arm) vs 0.32 (bar), 0.27 (interarm); N arm consistent with bar within 3 sigma | F: Arms have higher kinetic energy than bar or interarm | **partially**
- H: Is the NGC 7793 disk uniform in cloud properties apart from its center? | E: Regional intercepts, virial plots, distribution comparisons and bootstrapped KS/AD tests | R: All NGC 7793 intercepts consistent within 3 sigma; center has more extreme properties than ring and outer | F: NGC 7793 disk is relatively uniform, with a more extreme center | **supported**
- H: Do arm and interarm regions differ in cloud surface density at 13 pc resolution as at lower resolution? | E: Compared clump surface density distributions between regions of NGC 1313 | R: Surprisingly little difference in surface density between arm and interarm regions | F: Lower-resolution surface density contrasts may reflect cloud sparsity (beam filling) rather than true surface density | **supported**
- H: Is NGC 1313's greater massive cluster formation linked to its greater variety of environments? | E: Compared cluster and cloud property variation across regions in both galaxies | R: No single cloud parameter explains the difference; NGC 1313 shows greater regional variation | F: Massive cluster formation may be driven by NGC 1313's greater variation in environments | **partially**

## Reasoning

- Why this data: The two galaxies have similar mass, metallicity, SFR and distance but very different massive cluster populations, making a controlled comparison  
  > "makes the pair an excellent laboratory for directly comparing how the molecular gas conditions and galactic structure affect star cluster formation" (Introduction)
- Why this method: Dendrograms for size-linewidth and virial analyses (hierarchical scales); clumps for histogram/counting statistics; subsampled KS/AD tests to avoid overpowered statistics  
  > "Dendrograms are hierarchical and include substructure at many size scales, so are preferred for analyses where including the various size scales of the molecular clouds is useful" (Observations: CO(2-1))
- Alternative: Full-sample KS/AD tests rejected as overpowered; two supermassive old clusters in NGC 7793 center disregarded as irrelevant  
  > "Since these overpowered tests are unreliable, we instead perform a bootstrapped version" (Property Distribution Comparisons)
- How they decided it was enough: _not stated_
- Limitation (authors): Bootstrapped p-values depend strongly on subsample size and cannot establish whether distributions truly differ  
  > "The absolute value of these test results are highly subject to the size of the subsamples used in the bootstrapping" (Property Distribution Comparisons)
- Limitation (authors): Fitted slope uncertain, so only intercepts compared with slope held fixed  
  > "These slopes are also often poorly constrained and difficult to compare." (Size-Linewidth Relations)
- Limitation (authors): LEGUS catalogs miss the youngest, highly embedded clusters  
  > "the clusters in the LEGUS catalogs do not include many of the youngest, highly embedded clusters" (Discussion)
- Caveat (inferred, ours): Nearly all inputs (cubes, cloud catalogs, properties) come from Paper 1, so this paper cannot be checked independently
- Caveat (inferred, ours): Region boundaries from DSS2-red contours are arbitrary and NGC 7793 regions are by radius, not arms, limiting direct comparison
- Caveat (inferred, ours): KS/AD p-values at fixed n=65 are not a calibrated significance test
- Caveat (inferred, ours): Intercept comparison depends on the fixed slope 0.5 and on the dendrogram structures chosen
- Caveat (inferred, ours): Small sample in NGC 1313 bar (69 clumps) and some regions with few young massive clusters

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Paper 1 data reduction, imaging and cloud-identification parameters
- Missing: Paper 1 Appendix A cloud catalogs and LEGUS cluster catalogs with region assignments
- Missing: Fit procedure for intercepts and bootstrap details (seed, replacement)
- Data volume (inferred): Two Band 6 12m CO(2-1) cubes (tens of GB raw MOUS data, likely) plus small catalogs
- Score (inferred): 2/5, Analysis here is simple and described, but all heavy processing and the cloud catalogs live in Paper 1, and several fit and bootstrap details are unstated.
- Rediscovery candidate: no, Key inputs (calibrated cubes, cloud catalogs) come from Paper 1 and the paper does not state that data are public; recipe depends on unpublished-here choices.

## Links

- Method: Finn et al. 2024, Paper 1 (cite: Finn23a) (Data reduction, imaging, cloud identification and property calculation)
- Method: (cite: Sidorin17) (quickclump clump identification)
- Method: (cite: Rosolowsky08) (astrodendro dendrograms)
- Method: (cite: Adamo17) (LEGUS cluster catalog methodology)
- Method: (cite: Lazariv18) (Rationale for overpowered KS tests on large samples)
- Companion: Finn et al. 2024, ALMA-LEGUS I (Paper 1) (cite: Finn23a) (Global comparison of NGC 1313 and NGC 7793 cloud properties using the same data)
- Related: LEGUS (Legacy ExtraGalactic UV Survey)
- Related: PHANGS-ALMA
- Related: PAWS
- Related: CANON

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 98,
  "stated": 51,
  "rate": 0.52
 },
 "evidence_ok": true
}
```
