# PHANGS-ML: Dissecting Multiphase Gas and Dust in Nearby Galaxies Using Machine Learning

`2024ApJ...968...24B` | The Astrophysical Journal 2024 | first author: Baron, Dalya | arXiv: 2402.04330 | DOI: 10.3847/1538-4357/ad39e5

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, milky_way_ism, astrochemistry
- Question: Can unsupervised machine learning on multi-wavelength (ALMA, MUSE, JWST) 150 pc-scale maps of three PHANGS galaxies identify groups and new correlations between PAH band ratios and optical line ratios?  
  > "Here we use unsupervised machine learning algorithms to mine this information-rich dataset to identify novel patterns." (abstract)
- Target **NGC 0628**: coordinates _not stated_; z/distance 9.84 Mpc  
  > "NGC 0628 & 9.84 & 9 & 1.75 & 10.2 & no & 3.14$''$" (Table 1); distance from Lee et al. 2023 (cite: lee23)  
  > "NGC 0628 & 9.84 & 9 & 1.75 & 10.2 & no & 3.14$''$" (Table 1)
- Target **NGC 1365**: coordinates _not stated_; z/distance 19.57 Mpc  
  > "NGC 1365 & 19.57 & 55 & 16.90 & 10.8 & yes & 1.58$''$" (Table 1); distance from Lee et al. 2023 (cite: lee23)  
  > "NGC 1365 & 19.57 & 55 & 16.90 & 10.8 & yes & 1.58$''$" (Table 1)
- Target **NGC 7496**: coordinates _not stated_; z/distance 18.72 Mpc  
  > "NGC 7496 & 18.72 & 36 & 2.26 & 9.8 & yes & 1.65$''$" (Table 1); distance from Lee et al. 2023 (cite: lee23)  
  > "NGC 7496 & 18.72 & 36 & 2.26 & 9.8 & yes & 1.65$''$" (Table 1)

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 150 pc convolved maps; effective 3.14", 1.58", 1.65" for NGC 0628, 1365, 7496  
  > "We list the effective angular resolution ($''$) of the convolved maps for each of the galaxies in table" (2 Data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PHANGS-ALMA survey data products used (CO(2-1) moment maps)  
  > "We use the PHANGS-ALMA data products obtained after convolving the cubes to a spatial resolution of 150 pc." (2.1 ALMA)
- Line: 12CO J=2-1 (not stated)
- Other facility **VLT-MUSE**: Ionized gas line maps and stellar population properties (PHANGS DR2.2, convolved to 150 pc)  
  > "we use various properties (see below) derived from the MUSE cubes after they have been convolved to a resolution of 150 pc (PHANGS DR2.2 release)." (2.2 MUSE)
- Other facility **JWST NIRCam/MIRI**: PAH and dust surface brightness maps (F335M, F770W, F1000W, F1130W, F2100W), version 0.8  
  > "We use the same version of the surface brightness maps presented and described in the PHANGS-JWST Cycle 1 Focus Issue" (2.3 JWST)
- External data: PAH emission models (band ratios vs SED, size, charge distribution)  
  > "We use the infrared spectra predicted by (cite: draine21)." (4.2.1) [from Draine et al. 2021 (cite: draine21)]
- External data: Galaxy distances, inclinations, SFR, stellar mass  
  > "(1)-(5) Galaxy properties from (cite: lee23): name, distance, inclination, star formation rate, and stellar mass." (Table 1) [from Lee et al. 2023 (cite: lee23)]

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
- smoothing: Cubes convolved to 150 pc resolution; maps reprojected and downsampled to 2 pixels per 150 pc  
  > "We then downsample the RA-DEC coordinate grid to have two pixels per resolution element of 150 pc in each of the galaxies" (2 Data)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA CO maps, strict/broad masks and 150 pc convolution  
  > "we use the PHANGS-ALMA survey (cite: leroy21a; leroy21b)." (2.1 ALMA) [from (cite: leroy21a; leroy21b)]
- 3.3 micron PAH flux estimation by subtracting starlight using F300M and F360M  
  > "follow the procedure outlined by (cite: sandstrom23a) to estimate the 3.3 $\mathrm{\mu m}$  PAH flux" (2.3 JWST) [from (cite: sandstrom23a)]
- MUSE line fitting and stellar population analysis  
  > "These are estimated by fitting the spectra in the convolved cubes with a set of Gaussians (see details in (cite: emsellem22))." (2.2 MUSE) [from (cite: emsellem22)]

### Not stated but needed to reproduce (our reading)

- Exact PHANGS-ALMA product file names/versions and CO noise thresholds used
- Hierarchical clustering linkage cluster-count and random seeds for UMAP
- ALMA project codes and observation details
- Details of polynomial fit procedure for 11.3/7.7 vs optical line ratios

## Analysis recipe

1. **Build feature maps**: Reproject convolved ALMA/MUSE/JWST maps to ALMA grid, downsample, mask pixels below 3 sigma, compute log ratios, clip to 0.5-99.5 percentile, normalize, KNN-impute missing values  
  > "For each feature, we clip its values to be between the 0.5th and 99.5th percentiles of the distribution." (3.1 Feature Extraction)
   - software: astropy, reproject, scikit-learn
   - assumption: Case-B recombination, T=10^4 K, dusty screen, Cardelli et al. extinction law  
  > "we assume case-B recombination ($T=10^{4}$ K), a dusty-screen, and the (cite: cardelli89) extinction law" (2.2 MUSE)
   - fitting: _not stated_
   - validation: Compared KNN and Random Forest imputation; comparable results  
  > "The two methods gave comparable results, and neither had a significant impact on the resulting two-dimensional embedding." (3.1 Feature Extraction)
2. **Dimensionality reduction**: UMAP to 2D with metric=correlation, n_neighbors=10, min_dist=0  
  > "we adopt the two-dimensional umap embedding obtained using `metric=correlation`, `n_neighbors=10`, and `min_dist=0`." (3.2)
   - software: UMAP
   - fitting: _not stated_
   - validation: Tested 11 metrics and n_neighbors 10-500; global structure stable  
  > "We find that the global structure of the data in the two-dimensional space remains stable when changing the metric and/or `n_neighbors`." (3.2)
3. **Cluster the embedding**: Hierarchical clustering with average linkage, 6 clusters, chosen after comparing K-means, Birch, OPTICS, DBSCAN and other linkages  
  > "The results reported in section [4](#sec:results) are therefore based on the clusters identified with Hierarchical clustering with the average linkage method." (3.3)
   - software: scikit-learn
   - fitting: _not stated_
   - validation: Visual inspection of cluster separation  
  > "To select an embedding where identifying clusters is expected to be less challenging, we favor embeddings where clusters that we identify by eye are more separated from each other" (Methods, Dimensionality Reduction with UMAP)
4. **Interpret PAH vs optical line correlations with PAH and SED models**: Compare observed trends with Draine et al. 2021 PAH models and SED sequences (FSPS, BC03, BPASS, HOLMES, AGN+SF); polynomial fits of 11.3/7.7 vs line ratios propagated to 3.3/11.3  
  > "we show two polynomial fits to the observed relation between 11.3/7.7 and the optical lines." (4.2.2)
   - software: FSPS
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **UMAP** : 2D embedding  
  > "we use the dimensionality reduction algorithm umap (Uniform Manifold Approximation and Projection; (cite: mcinnes18))" (3.2)
- **scikit-learn** : Clustering and KNN imputation  
  > "We used the python sklearn library to apply these different clustering algorithms (cite: pedregosa11)." (3.3)
- **reproject** : Reprojecting maps to ALMA WCS  
  > "We project all the convolved maps into the world coordinate system (WCS) defined by the ALMA observations using reproject.exact by astropy" (2 Data)
- **FSPS** : Simulating stellar population SEDs  
  > "We used the flexible stellar population synthesis (FSPS) code by (cite: conroy09) to simulate single stellar populations." (9.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of pixels in analysis | 24007 | not stated | pixels | 1 | the input dataset has 24 007 objects with 13 features each. |
| Scatter in 11.3/7.7 vs optical line ratio relation | ~0.03 | not stated | dex | 4 | The very small scatter ($\sim 0.03$ dex) in the relation between 11.3/7.7 and $\text{[O\,{\sc iii}]}$/H$\beta$ |
| Best-fit slope 11.3/7.7 vs [SII]/Ha, all pixels | 0.22 | not stated | dimensionless | 4 | to the best-fitting slope found for all PHANGS pixels in figure [13](#f:PAH_optical_interpretation_sii_halpha) (0.22). |

## Qualitative findings

- Pixels divide into six groups: AGN-photoionized gas, two diffuse ionized gas groups, CMZ, and two star-forming/ISM groups  
  > "divide the pixels into six groups" (4)

## Claim tuples

- H: Unsupervised ML can identify groups with distinct gas and PAH properties | E: UMAP plus hierarchical clustering on 13 features | R: Six groups mapping to coherent galactic structures | F: Groups have distinct ionization and PAH properties | **supported**
- H: PAH band ratios correlate with optical line ratios due to a common varying radiation field | E: Compare observed correlations with Draine et al. models and SED sequences | R: Expected slope roughly consistent with observed | F: PAHs and ionized gas see different parts of the same varying radiation field | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Varying ionization parameter disfavored in SF+ISM groups in favor of stellar age sequence  
  > "We disfavor the interpretation that the optical line ratios are driven by a varying ionization parameter" (4.2.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Analysis incomplete in diffuse ISM because CO and 3.3 micron detections are required  
  > "Therefore, our results may not be applicable to the most diffuse parts of local galaxies." (3.1)
- Caveat (inferred, ours): Clusters are admitted to be somewhat arbitrary; hyperparameters chosen visually
- Caveat (inferred, ours): Only three galaxies; galaxy dominates regions of embedding
- Caveat (inferred, ours): Broad-mask CO adds noise and low-SNR pixels

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Code and exact random seeds not stated
- Missing: Exact data product versions for ALMA maps
- Data volume (inferred): small (<10 GB of derived maps)
- Score (inferred): 3/5, Uses public PHANGS data products and named software with key hyperparameters, but clustering is subjective and code release and some choices are not stated.
- Rediscovery candidate: no, ALMA role is minor and clustering results are not primarily numeric.

## Links

- Method: Leroy et al. 2021a (cite: leroy21a) (PHANGS-ALMA data products)
- Method: Emsellem et al. 2022 (cite: emsellem22) (PHANGS-MUSE pipeline)
- Companion: Lee et al. 2023 (cite: lee23) (PHANGS-JWST overview)
- Related: PHANGS-ALMA
- Related: PHANGS-MUSE
- Related: PHANGS-JWST
- Related: PHANGS-HST

## Checks

```json
{
 "quotes": 40,
 "quotes_ok": 40,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00650.S",
  "2013.1.01161.S",
  "2015.1.00925.S",
  "2017.1.00392.S",
  "2017.1.00886.L"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 32,
  "rate": 0.421
 },
 "evidence_ok": true
}
```
