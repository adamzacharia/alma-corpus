# Detailed analysis of multiline molecular distributions in the Seyfert galaxy NGC 1068: Possible effect of the active galactic nucleus outflow to the starburst ring

`2025PASJ...77..834O` | Publications of the Astronomical Society of Japan 2025 | first author: Okubo, Hiroma | arXiv: 2506.15999 | DOI: 10.1093/pasj/psaf054

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, agn_and_quasars, astrochemistry
- Question: Can PCA of multi-line integrated intensity maps extract meaningful features in a galaxy hosting both an AGN and a starburst ring, and does the AGN outflow influence gas in the SB ring?  
  > "The first objective is to assess the validity of PCA for feature extraction in galaxies that host both the AGN and the SB ring." (1 Introduction); "The second objective is to investigate the potential influence of the AGN outflow on the SB ring." (1 Introduction)
- Target **NGC 1068**: coordinates _not stated_; z/distance systemic velocity 1116 km/s; distance not stated  
  > "NGC 1068 is a nearby type-2 Seyfert galaxy with both an Active Galactic Nucleus (AGN) and a starburst (SB) ring." (1 Introduction); "from 1116 km/s, which is the systemic velocity of NGC 1068" (2.1 ALMA Observations, Ancillary Data, and Data Processing); distance from systemic velocity from (cite: GarcíaBurillo et al. 2014); distance not stated  
  > "NGC 1068 is a nearby type-2 Seyfert galaxy with both an Active Galactic Nucleus (AGN) and a starburst (SB) ring." (1 Introduction); "from 1116 km/s, which is the systemic velocity of NGC 1068" (2.1 ALMA Observations, Ancillary Data, and Data Processing)

## Data provenance

- ALMA projects: 2013.1.00279.S, 2011.0.00061.S, 2012.1.00657.S, 2013.1.00060.S, 2015.1.00960.S, 2017.1.00586.S, 2018.1.01506.S, 2018.1.01684.S, 2019.1.00130.S
- bands: Band 3 (3 mm)  
  > "We carried out an imaging spectral scan at 3 mm toward NGC 1068 using Band 3 of ALMA with its 12 m array" (2.1 ALMA Observations, Ancillary Data, and Data Processing)
- frequencies and spectral setup: imaging spectral scan at 3 mm for 2013.1.00279.S; spectral setups of the archival projects not stated  
  > "We carried out an imaging spectral scan at 3 mm toward NGC 1068" (2.1 ALMA Observations, Ancillary Data, and Data Processing)
- continuum bandwidth: _not stated_
- arrays: 12 m array only (7 m and total power data not used)  
  > "we restricted our analysis to data from the 12 m array to ensure consistent maximum recoverable scales across all detected lines" (2.1 ALMA Observations, Ancillary Data, and Data Processing)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: archival data selected with spatial resolution of 150 pc or better (angular resolution < 2.08 arcsec); cubes smoothed to 150 pc  
  > "we selected observations with a spatial resolution of 150 pc or better" (2.1 ALMA Observations, Ancillary Data, and Data Processing); "Next, we smoothed the cube data to a spatial resolution of 150 pc." (2.1 ALMA Observations, Ancillary Data, and Data Processing)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: 2013.1.00279.S (PI: T. Nakajima) plus publicly available archival Band 3 data as of summer 2021  
  > "we retrieved and processed all publicly available archival Band 3 data for NGC 1068 as of summer 2021" (2.1 ALMA Observations, Ancillary Data, and Data Processing)
- Line: C2H N=1-0 (87.316898 GHz)
- Line: HCN J=1-0 (88.631602 GHz)
- Line: HCO+ J=1-0 (89.188525 GHz)
- Line: HNC J=1-0 (90.663568 GHz)
- Line: HC3N J=10-9 (90.979023 GHz)
- Line: N2H+ J=1-0 (93.173977 GHz)
- Line: CH3OH J=2_K-1_K (96.744550 GHz)
- Line: CS J=2-1 (97.980953 GHz)
- Line: C18O J=1-0 (109.782173 GHz)
- Line: 13CO J=1-0 (110.201354 GHz)
- Line: CN N=1_1/2-0_1/2 (113.191279 GHz)
- Line: CN N=1_3/2-0_1/2 (113.490970 GHz)
- Line: CO J=1-0 (115.271202 GHz)
- External data: Systemic velocity of NGC 1068, 1116 km/s, used as the centre of the integration window  
  > "from 1116 km/s, which is the systemic velocity of NGC 1068" (2.1 ALMA Observations, Ancillary Data, and Data Processing) [from (cite: GarcíaBurillo et al. 2014)]

## Processing

### Calibration

- pipeline or manual: observatory-delivered calibration with minor manual data flagging  
  > "We applied observatory-delivered calibration with minor manual data flagging using the appropriate CASA version." (2.1 ALMA Observations, Ancillary Data, and Data Processing)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: PHANGS-ALMA imaging pipeline (CLEAN)  
  > "we reconstructed the integrated intensity maps using the PHANGS-ALMA imaging pipeline" (2.1 ALMA Observations, Ancillary Data, and Data Processing); "We performed imaging and deconvolution using CLEAN." (2.1 ALMA Observations, Ancillary Data, and Data Processing)
- deconvolver: single-scale CLEAN only (no multiscale CLEAN)  
  > "While the standard PHANGS-ALMA pipeline applies both single-scale CLEAN and multiscale CLEAN, we applied only single-scale CLEAN in this study." (2.1 ALMA Observations, Ancillary Data, and Data Processing)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: hexagonal grid with 150 pc grid size  
  > "We set the grid size to 150 pc" (2.1 ALMA Observations, Ancillary Data, and Data Processing); "we choose the hexagonal grid to minimize the inter-pixel correlation" (2.1 ALMA Observations, Ancillary Data, and Data Processing)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane, first-degree polynomial fit, CASA uvcontsub  
  > "by fitting a first-degree polynomial function using the CASA uvcontsub task" (2.1 ALMA Observations, Ancillary Data, and Data Processing)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12 m array only; no 7 m or total power combination  
  > "we restricted our analysis to data from the 12 m array to ensure consistent maximum recoverable scales across all detected lines" (2.1 ALMA Observations, Ancillary Data, and Data Processing)
- smoothing: cubes smoothed to a spatial resolution of 150 pc  
  > "Next, we smoothed the cube data to a spatial resolution of 150 pc." (2.1 ALMA Observations, Ancillary Data, and Data Processing)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Details of the 2013.1.00279.S observations  
  > "Detailed information about these observations is available in (cite: Nakajima et al. 2023)." (2.1 ALMA Observations, Ancillary Data, and Data Processing) [from (cite: Nakajima et al. 2023)]
- Imaging and integrated-intensity-map construction follow the PHANGS-ALMA imaging pipeline  
  > "we reconstructed the integrated intensity maps using the PHANGS-ALMA imaging pipeline ((cite: Leroy et al. 2021))" (2.1 ALMA Observations, Ancillary Data, and Data Processing) [from (cite: Leroy et al. 2021)]
- Further details of the data processing are deferred to earlier work  
  > "For more details, refer to (cite: Leroy et al. 2021), (cite: Saito et al. 2022a) and (cite: Saito et al. 2022)." (2.1 ALMA Observations, Ancillary Data, and Data Processing) [from (cite: Leroy et al. 2021); (cite: Saito et al. 2022a); (cite: Saito et al. 2022)]

### Not stated but needed to reproduce (our reading)

- CASA version(s) used for each of the nine projects (paper says only 'the appropriate CASA version')
- PHANGS-ALMA pipeline version and its configuration: weighting/robust, clean masks, thresholds, channel width, cell size of the intermediate cubes
- Line-free channels used for the uvcontsub first-degree polynomial fit, per project and per line
- Which project and spectral window supplied each of the 13 lines, and how lines observed in several projects were combined
- Definition and computation of the 'error moment 0 map' and of S/N per hexagon (noise estimate, masking of the moment 0 integration)
- Hexagonal grid origin, orientation and centre position, and the adopted distance that converts 150 pc to angular size
- Exact definition of the overall region and SB ring region masks (centre, 10 arcsec and 27.5 arcsec annulus geometry) and how the 683 and 482 hexagons were selected
- How the NGC 1068 centre/position and unit conversion to K km/s were set
- Monte Carlo details: random seed, whether PCA axis sign/ordering was re-aligned across the 100,000 trials, and how the 1-sigma values were taken (percentiles)
- scikit-learn version and PCA options (svd solver, whitening)
- Correlation coefficient type and moment 2 map construction used for the PC2 and PC3 comparisons

## Analysis recipe

1. **Calibrate, image and build 150 pc integrated intensity maps**: Observatory-delivered calibration with minor manual flagging; uv-plane continuum subtraction; single-scale CLEAN imaging with the PHANGS-ALMA pipeline; smoothing to 150 pc; integration over +-300 km/s around 1116 km/s; regridding to a hexagonal grid  
  > "We applied observatory-delivered calibration with minor manual data flagging using the appropriate CASA version." (2.1 ALMA Observations, Ancillary Data, and Data Processing); "Finally, we regridded the data into a hexagonal grid to minimize correlations between grids." (2.1 ALMA Observations, Ancillary Data, and Data Processing)
   - software: CASA, PHANGS-ALMA pipeline
   - parameter: Continuum subtraction: first-degree polynomial in the uv-plane (CASA uvcontsub)  
  > "by fitting a first-degree polynomial function using the CASA uvcontsub task" (2.1 ALMA Observations, Ancillary Data, and Data Processing)
   - parameter: Integration range +-300 km/s about 1116 km/s  
  > "integrating over the range of $\pm$300 km/s from 1116 km/s" (2.1 ALMA Observations, Ancillary Data, and Data Processing)
   - parameter: Final resolution and grid 150 pc, hexagonal  
  > "We set the grid size to 150 pc" (2.1 ALMA Observations, Ancillary Data, and Data Processing)
   - assumption: Same procedure applied to all molecular lines  
  > "These operations were applied to all molecular lines using the same procedure." (2.1 ALMA Observations, Ancillary Data, and Data Processing)
   - fitting: _not stated_
   - validation: _not stated_
2. **Select grid points and molecular lines for the PCA**: Remove hexagons where CO(1-0) S/N <= 4; keep lines with at least 60 hexagons at S/N > 4 within the CO S/N > 4 region, leaving 13 lines  
  > "we remove the grids from all molecular integrated intensity maps where the S/N of the CO" (2.1 ALMA Observations, Ancillary Data, and Data Processing); "we set a threshold of 60 grid points where each molecular line has S/N" (2.1 ALMA Observations, Ancillary Data, and Data Processing)
   - parameter: Threshold of 60 grid points, about one-tenth of all grid points in the overall region  
  > "This threshold corresponds to approximately one-tenth of all grid points in the overall region." (2.1 ALMA Observations, Ancillary Data, and Data Processing)
   - parameter: Final data sets (13, 683) overall region and (13, 482) SB ring region  
  > "The final data set is (13, 683) for the overall region" (2.1 ALMA Observations, Ancillary Data, and Data Processing); "The data set of the SB ring region is (13, 482)." (2.1 ALMA Observations, Ancillary Data, and Data Processing)
   - fitting: _not stated_
   - validation: _not stated_
3. **Standardize the integrated intensity maps**: For each line, subtract the mean and divide by the standard deviation, separately for the overall and SB ring regions  
  > "For each molecular line, we subtract the mean and divide by the standard deviation of its integrated intensity." (2.1 ALMA Observations, Ancillary Data, and Data Processing)
   - fitting: _not stated_
   - validation: Appendix repeats the PCA with min-max normalization (0 to 1) instead; differences generally minor, except for the PC3 negative score maps  
  > "Although the PCA score maps show some visual differences, they are generally minor and do not significantly alter the interpretation." (3 Results)
4. **Run PCA on the overall and SB ring regions**: PCA of the standardized maps (each hexagon a sample, 13 lines as features) with scikit-learn; PC scores mapped back on the sky, PC coefficients interpreted; axis sign set so that the maximum absolute score is positive  
  > "We used the PCA implementation from the scikit-learn project" (2.2 Principal Component Analysis); "we determined the axes such that the maximum absolute value of the PCA scores is positive" (3 Results)
   - software: scikit-learn
   - parameter: First three PCs retained (>97% of the variance in each region)  
  > "We will focus on these first three principal components since they explain more than 97% of the total information." (3.1 Overall region)
   - assumption: Each grid represents a single molecular cloud, inter-grid correlations ignored  
  > "under the assumption that each grid represents a single molecular cloud, with no consideration of inter-grid correlations" (2.2 Principal Component Analysis)
   - fitting: _not stated_
   - validation: _not stated_
5. **Estimate PCA coefficient errors by Monte Carlo**: Add normally distributed noise (sigma from the error moment 0 map) to every grid and every map, redo the PCA, repeat 100,000 times; take +-1 sigma values of the coefficients as error bars  
  > "random values are drawn from a normal distribution with the error moment 0 map as the standard deviation" (2.3 Evaluation of error in PCA analysis); "This procedure is repeated 100,000 times." (2.3 Evaluation of error in PCA analysis)
   - parameter: 100,000 Monte Carlo realisations  
  > "This procedure is repeated 100,000 times." (2.3 Evaluation of error in PCA analysis)
   - fitting: _not stated_
   - validation: _not stated_
6. **Interpret PC maps with tracer roles and test with extra correlations**: Interpret PC coefficients by tracer type (molecular gas, dense gas, shock, UV, high temperature); correlate PC2_OA scores with other Band 3 lines not used in the PCA and PC3_SB negative scores with velocity dispersion maps  
  > "Additionally, we use only integrated intensity maps with more than 5 grids satisfying S/N" (4.1.2 PC2_OA); "We examine the correlation between the velocity dispersion of" (4.2.3 PC3_SB)
   - assumption: C2H velocity dispersion taken from the N=1_1/2-0_1/2 fine structure line only, since hyperfine splitting within each fine structure line is nearly identical  
  > "This study utilizes only C$_2$H ($N$=1$_{1/2}$-0$_{1/2}$) because the hyperfine splitting within each fine structure line is nearly identical" (4.2.3 PC3_SB)
   - fitting: _not stated_
   - validation: Interpretations compared with earlier studies (e.g. Scourfield 2020, Tosaki 2017, Tsai 2012, Saito 2022); described as not contradicting them  
  > "Therefore, the PC2$_{\rm OA}$ results do not contradict this study of (cite: Scourfield et al. 2020)." (4.1.2 PC2_OA)

## Software

- **CASA** : Calibration (observatory-delivered, appropriate version) and uv-plane continuum subtraction with uvcontsub  
  > "We applied observatory-delivered calibration with minor manual data flagging using the appropriate CASA version." (2.1 ALMA Observations, Ancillary Data, and Data Processing); "by fitting a first-degree polynomial function using the CASA uvcontsub task" (2.1 ALMA Observations, Ancillary Data, and Data Processing)
- **PHANGS-ALMA Pipeline** : Imaging and construction of integrated intensity maps  
  > "we reconstructed the integrated intensity maps using the PHANGS-ALMA imaging pipeline" (2.1 ALMA Observations, Ancillary Data, and Data Processing)
- **scikit-learn** : PCA implementation  
  > "We used the PCA implementation from the scikit-learn project" (2.2 Principal Component Analysis)
- **ALMA Calibration Pipeline** : _not stated_
- **Astropy** : _not stated_
- **NumPy** : _not stated_
- **SciPy** : _not stated_
- **spectral-cube** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Contribution rates of PC1, PC2, PC3 (overall region) | PC1 about 80%, PC2 approximately 15%, PC3 around 2% | not stated | percent of variance | 4 | The PC1$_{\rm OA}$ score map retains about 80% of the information, PC2$_{\rm OA}$ score map retains approximately 15%, and PC3$_{\rm OA}$ score map retains around 2%. |
| Contribution rates of PC1, PC2, PC3 (SB ring region) | PC1 nearly 90%, PC2 5%, PC3 2% | not stated | percent of variance | 4 | PC1$_{\rm SB}$, PC2$_{\rm SB}$, and PC3$_{\rm SB}$ retain nearly 90%, 5%, and 2% of the information, respectively. |
| Number of hexagons x lines, overall region | (13, 683) | not stated | dimensionless | 2 | The final data set is (13, 683) for the overall region |
| Number of hexagons x lines, SB ring region | (13, 482) | not stated | dimensionless | 2 | The data set of the SB ring region is (13, 482). |
| PC2_OA coefficient of 13CO (J=1-0) | -0.51 | +0.0018/-0.0018 | dimensionless | 4 | $-0.51_{-0.0018}^{+0.0018}$ |
| PC3_OA coefficient of CH3OH (J=2-1) | 0.66 | +0.025/-0.0089 | dimensionless | 4 | $0.66_{-0.0089}^{+0.025}$ |
| PC2_SB coefficient of CN (N=1_1/2-0_1/2) | 0.52 | +0.0061/-0.010 | dimensionless | 4 | $0.52_{-0.010}^{+0.0061}$ |
| PC3_SB coefficient of HC3N (J=10-9) | 0.66 | +0.052/-0.0050 | dimensionless | 4 | $0.66_{-0.0050}^{+0.052}$ |

## Qualitative findings

- PC1 (both regions) has all-positive coefficients and resembles the line maps, interpreted as approximate H2 column density  
  > "suggesting that it reflects the approximate H$_2$ column density" (4.1.1 PC1_OA)
- PC3_SB negative scores lie along the AGN outflow direction and are contributed by CN, C2H and HCN, suggesting possible AGN outflow interaction with SB ring gas  
  > "we suggest that the AGN outflow interacts with gas in the SB ring, as this feature is consistent with the direction of the AGN outflow" (abstract)
- PCA is linear, so complex nonlinear phenomena make PC3 capture several features at once  
  > "However, PC3 appears to capture multiple pieces of information." (4.2.3 PC3_SB)

## Claim tuples

- H: PCA can effectively extract features in a galaxy with both an AGN and an SB ring | E: PCA of standardized 150 pc integrated intensity maps of 13 lines, for the overall (~2 kpc) region and the SB ring region | R: PC1 traces approximate H2 column density; PC2_OA separates CND/AGN from the SB ring; PC3 and PC2_SB separate bar-end, spiral-arm, SSC and outflow-direction features | F: PCA effectively extracts features even in AGN + SB ring galaxies | **supported**
- H: The overall-region PCA maps reflect H2 column density and density/chemistry differences between the CND and SB ring | E: Inspection of PC1_OA and PC2_OA score maps and coefficients, with correlations to extra lines | R: PC1_OA coefficients all positive; PC2_OA positive scores near AGN and CND, negative along the SB ring | F: PC1 reconstructs approximate H2 column density; PC2 reflects CND vs SB ring density and/or chemical composition | **partially**
- H: SB ring PCA separates starburst-dominated from shock-dominated regions | E: PCA of the SB ring region only; PC2_SB score map and coefficients compared with SSC positions and shock tracers | R: PC2_SB positive scores at bar-end/SSCs (HC3N, N2H+, CN, C2H); negative scores at spiral arms (CH3OH, CO) | F: Approximate H2 column density and a starburst-versus-shock distinction | **partially**
- H: The AGN outflow interacts with gas in the SB ring | E: PC3_SB negative score map compared with outflow direction, tracer coefficients and velocity dispersion maps | R: Negative scores along the AGN outflow direction, with CN, C2H, HCN contributing, and anti-correlation with velocity dispersion for most lines | F: Possible interaction between the AGN outflow and SB ring gas; further investigation needed | **partially**
- H: Low-contribution PCs are interpretable by linear PCA | E: Interpretation of PC3 for both regions | R: PC1 and PC2 are easy to interpret, PC3 captures several pieces of information | F: Nonlinear methods may be needed for low-contribution maps | **partially**

## Reasoning

- Why this data: Band 3 archival data selected for resolution of 150 pc or better  
  > "we selected observations with a spatial resolution of 150 pc or better" (2.1 ALMA Observations, Ancillary Data, and Data Processing)
- Why this method: PCA extracts key information through dimensionality reduction from many lines  
  > "PCA is a powerful unsupervised machine learning technique that extracts key information through dimensionality reduction." (abstract)
- Alternative: Min-max normalization instead of standardization, presented in the Appendix; generally minor differences, except for PC3 negative score maps  
  > "For reference, the results using normalization, which is another common scaling method and sets the minimum and maximum values of each molecular line to 0 and 1, are provided in the Appendix." (3 Results)
- Alternative: Only single-scale CLEAN used, not multiscale CLEAN  
  > "we applied only single-scale CLEAN in this study" (2.1 ALMA Observations, Ancillary Data, and Data Processing)
- How they decided it was enough: Lines kept only if detected over a sufficiently large part of the map (60 grid points at S/N > 4)  
  > "it is necessary to use molecular lines that are detected across a sufficiently large portion of the map" (2.1 ALMA Observations, Ancillary Data, and Data Processing)
- Limitation (authors): PCA is a linear combination of the input data and does not precisely extract H2 column density  
  > "PCA is inherently a linear combination of the input data" (4.1.1 PC1_OA)
- Limitation (authors): PC3_SB negative scores overlap with the bar-end and may extract several features  
  > "On the other hand, a more detailed analysis is required because these regions also overlap with the bar-end and have possibility that multiple features are being extracted." (4.2.3 PC3_SB)
- Caveat (inferred, ours): The AGN outflow interpretation of PC3_SB rests on map morphology and a correlation with velocity dispersion; no independent check of outflow-driven chemistry (e.g. line ratios, radiative transfer)
- Caveat (inferred, ours): PCA is linear and PC3 mixes several effects; interpretation of coefficients by tracer roles is qualitative and partly circular
- Caveat (inferred, ours): Choices such as standardization, the 60-hexagon line threshold and the SB ring mask can change low-order PCs (the appendix shows PC3 changes)
- Caveat (inferred, ours): Spatial correlations between hexagons and CND/AGN contamination of the ring region are not treated; Monte Carlo errors include only moment 0 noise
- Caveat (inferred, ours): Coefficient errors are tiny (1e-4 to 1e-2) and may understate systematic uncertainties from heterogeneous projects and calibration

## Reproducibility

- Data public (paper): Archival Band 3 data are publicly available; 2013.1.00279.S is a PI project cited to Nakajima et al. 2023  
  > "we retrieved and processed all publicly available archival Band 3 data for NGC 1068 as of summer 2021" (2.1 ALMA Observations, Ancillary Data, and Data Processing)
- Products in archive: _not stated_
- Missing: PHANGS-ALMA pipeline configuration and version, CASA versions, line-free channel choices
- Missing: Hexagonal grid definition and SB ring / overall region masks
- Missing: Mapping of lines to projects and the error moment 0 and S/N recipe
- Missing: No released code or processed maps stated
- Data volume (inferred): Nine Band 3 12 m projects, including a spectral scan; likely hundreds of GB of raw/calibrated data before imaging, with a few GB of cubes after 150 pc smoothing
- Score (inferred): 3/5, Data are public and the PCA recipe is clear, but the imaging pipeline settings, region masks, grid definition and line-to-project mapping are not given, and results are qualitative interpretations plus variance fractions.
- Rediscovery candidate: no, Public data and a numeric PCA outcome exist, but the PHANGS pipeline settings, hexagon grid and region masks are not specified well enough to redo the maps and PCA exactly.

## Links

- Method: (cite: Leroy et al. 2021) (PHANGS-ALMA imaging pipeline used for cubes and integrated intensity maps)
- Method: (cite: Saito et al. 2022) (Earlier processing and PCA-type analysis of the central region of NGC 1068, referred to for processing details)
- Method: (cite: Pedregosa et al. 2011) (scikit-learn PCA implementation)
- Companion: (cite: Nakajima et al. 2023) (Observations of project 2013.1.00279.S and AGN outflow extent)
- Companion: (cite: Harada et al. 2024) (PCA of ALCHEMI integrated intensity maps of NGC 253)
- Related: PHANGS-ALMA
- Related: ALCHEMI

## Checks

```json
{
 "quotes": 101,
 "quotes_ok": 101,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 9,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 90,
  "stated": 51,
  "rate": 0.567
 },
 "evidence_ok": true
}
```
