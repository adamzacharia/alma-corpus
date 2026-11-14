# Components of star formation in NGC 253: Non-negative matrix factorization analysis with the ALCHEMI integrated intensity images

`2025PASJ...77....1K` | Publications of the Astronomical Society of Japan 2025 | first author: Kishikawa, Ryo | arXiv: 2411.03867 | DOI: 10.1093/pasj/psae095

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, astrochemistry, star_formation
- Question: Can non-negative matrix factorization of ALCHEMI integrated intensity images of NGC 253 extract molecular/physical components involved in star formation, and how does it compare with PCA?  
  > "We used non-negative matrix factorization (NMF) to extract individual molecular or physical components involved in the star formation process in NGC 253." (abstract); "We also compared our results using principal component analysis (PCA) previously applied to the same dataset." (abstract)
- Target **NGC 253**: coordinates _not stated_; z/distance 3.5 Mpc  
  > "It is located at a distance of $3.5 \> \mathrm{Mpc}$ (cite: Rekola2005)" (Introduction); "observed the central molecular zone (CMZ) of NGC 253" (ALCHEMI data); distance from (cite: Rekola2005)  
  > "It is located at a distance of $3.5 \> \mathrm{Mpc}$ (cite: Rekola2005)" (Introduction); "observed the central molecular zone (CMZ) of NGC 253" (ALCHEMI data)

## Data provenance

- ALMA projects: 2017.1.00161.L, 2018.1.00162.S
- bands: ALMA Bands 3-7 spectral scan (ALCHEMI); continuum images at Bands 3 and 7 included  
  > "The survey consisted of a spectral scan over most of the frequency coverage in ALMA Bands 3-7." (ALCHEMI data); "Additionally, we included the continuum images at ALMA Bands 3 and 7 from the same dataset." (abstract)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.6 arcsec (= 27 pc)  
  > "with an angular resolution of $1.6^{"}$ (= 27 pc)" (ALCHEMI data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALCHEMI large program data (2017.1.00161.L, 2018.1.00162.S); images taken from Harada2024  
  > "We used images of 148 transitions from 44 different species of the ALMA large program ALCHEMI." (abstract); "We took exactly the same integrated intensity images used in the PCA study by (cite: Harada2024)" (ALCHEMI data)
- External data: Integrated intensity (moment 0) images of 150 molecular lines, recombination lines and continuum maps, with blended transitions omitted and NaN masking  
  > "We took exactly the same integrated intensity images used in the PCA study by (cite: Harada2024), which omitted transitions with blending above certain levels." (ALCHEMI data); "because we masked out locations in the position-position-velocity cube of transitions where emission is not expected as described in (cite: Harada2024)" (Footnote 1) [from (cite: Harada2024)]
- External data: Complete list of transitions (Table 3 of Harada2024)  
  > "An complete list of transitions can be found in Table 3 of (cite: Harada2024)." (ALCHEMI data) [from (cite: Harada2024)]
- External data: PCA variance fractions used for comparison: 79.4% for PC1, 9.0% for PC2, 5.0% for PC3  
  > "the percentage of variance explained by PC1 is very large compared with other PCs (79.4$\>\%$ for PC1, 9.0$\>\%$ for PC2, 5.0$\>\%$, $\cdots$)" (Comparison with PCA) [from (cite: Harada2024)]
- External data: Positions of the giant molecular clouds (GMCs) in the central region of NGC 253  
  > "The positions of the GMCs of NGC 253 are provided in table" (ALCHEMI data) [from not stated in the text given]
- External data: Super star cluster ages and locations used to interpret NF5  
  > "determined the age of the SSCs from the luminosity of the SSCs and the protostars" (Interpretation of each NF component) [from (cite: Rico2020)]
- External data: Starburst region locations from 99.02 GHz free-free and H40alpha emission, used to interpret NF4  
  > "identified the location of starburst regions based on 99.02 GHz free-free emission and H40$\alpha$ emission in the central region of NGC 253" (Interpretation of each NF component) [from (cite: Bendo2013)]

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

- Moment 0 images, transition list, line blending cuts and NaN masking taken from the earlier PCA study  
  > "We took exactly the same integrated intensity images used in the PCA study by (cite: Harada2024), which omitted transitions with blending above certain levels." (ALCHEMI data); "because we masked out locations in the position-position-velocity cube of transitions where emission is not expected as described in (cite: Harada2024)" (Footnote 1) [from (cite: Harada2024)]
- Number of components (5) chosen following the PCA study  
  > "Following this, we decided to use 5 components in this study." (NMF) [from (cite: Harada2024)]
- ALCHEMI observations and data processing (survey description)  
  > "The ALCHEMI survey ((cite: Martin2021)) observed the central molecular zone (CMZ) of NGC 253" (ALCHEMI data) [from (cite: Martin2021)]
- Treatment of K-ladder transitions as one blended transition  
  > "all the $K$-ladder transitions are blended, and we treat them as one transition" (Footnote 2) [from (cite: Harada2024)]

### Not stated but needed to reproduce (our reading)

- The scikit-learn NMF parameter table (init, solver, max_iter, tol, random_state, alpha_W, alpha_H, l1_ratio) is referenced but its values are not in the text given
- The Harada2024 moment 0 images and the NaN masks themselves are needed; this paper does not describe how they were made from the ALCHEMI cubes (velocity windows, continuum subtraction, imaging, beam matching)
- Which transitions make up the 150 images (the list is only in Table 3 of Harada2024)
- scikit-learn and Python versions
- Exact positions of the GMCs (table of GMC positions)
- Which initialization was used for the published maps
- Calibration, imaging and self-calibration choices of the ALCHEMI data are all not stated

## Analysis recipe

1. **Prepare moment 0 images**: Replace NaN and negative values with 0 in each moment 0 image, normalize each image to min 0 and max 1, flatten 512 x 640 pixels to one dimension  
  > "we begin by replacing all non-numbers and negative values" (NMF); "Subsequently, we normalize the minimum value to be 0 and the maximum value to be 1" (NMF)
   - software: Python
   - parameter: Image size 512 x 640 pixels per transition  
  > "make the two-dimensional data (512 pixels $\times$ 640 pixels) from a given transition one-dimensional" (NMF)
   - assumption: Negative values come from absorption lines near GMC 5 and are set to zero; NMF assumes emission only adds intensity if absorption is ignored  
  > "Negative values come from absorption lines that are present around GMC 5 for limited transition." (Footnote 1); "An addition of a cloud with certain physical parameters should only increase the emission intensity, and not decrease it if we can ignore absorption." (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Build the data matrix**: Stack all 150 flattened images as columns of a 327,680 x 150 matrix E  
  > "Then, we integrate all the emission line data into a matrix ($327,680 \mathrm{\>rows} \times 150 \mathrm{\>columns}$) by applying the same procedure to the 150 images." (NMF)
   - software: Python
   - fitting: _not stated_
   - validation: _not stated_
3. **Factorize with NMF**: Factorize E into non-negative base matrix B and coefficient matrix C with M = 5 components using sklearn.decomposition.NMF; each column of B reshaped into a 2D map (NF1-NF5)  
  > "In our implementation, we used the `scikit-learn` module of Python (cite: scikit-learn)." (NMF); "Each column of the base matrix is then converted into a two-dimensional map, resulting in five maps defined as non-negative factor (NF) components (NF1 – NF5)." (NMF)
   - software: scikit-learn, Python
   - parameter: M = 5 components  
  > "Following this, we decided to use 5 components in this study." (NMF)
   - parameter: Frobenius norm loss; with the parameters used the objective reduces to the Frobenius norm of E - BC  
  > "The loss function is commonly chosen to be the Frobenius norm, which we use here." (Derivation method of base and coefficient matrices in scikit-learn); "the objective function simply becomes the Frobenius norm of E $-$ BC" (Derivation method of base and coefficient matrices in scikit-learn)
   - fitting: scikit-learn NMF minimizing the Frobenius-norm reconstruction error; no sampler or priors  
  > "the algorithm in `scikit-learn` minimizes the following function called the objective function" (Derivation method of base and coefficient matrices in scikit-learn)
   - validation: Results unchanged across scikit-learn initializations (nndsvda, nndsvd, nndsvdar, random); reconstruction error versus M plateaus beyond M = 4; M = 8 gives localized or noisy components  
  > "we confirmed that changing the initialization methods does not change our results when using standard methods of initialization in `scikit-learn`, nndsvda, nndsvd, nndsvdar, and random." (Derivation method of base and coefficient matrices in scikit-learn); "The reconstruction error decreases steeply with the number of components for $M<4$, but it plateaus for larger $M$." (The error before and after applying NMF); "As the number of components increases, more components contain structures that are too localized or noisy." (The case of another number of components)
4. **Rescale base and coefficient matrices**: Scale each column of B so its L1 norm is 1 and recompute C, so coefficients are the flux each NF contributes to each input image  
  > "Because we scaled the base matrix so that the sum of each column is 1" (Results); "After scaling the base matrices, coefficients directly reflect how much flux each NF contributes to the total flux of input images." (Derivation method of base and coefficient matrices in scikit-learn)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compute NF fractions and contribution rates**: From C compute the NF fraction of each transition (c_xn / sum_m c_mn) and the contribution rate of each NF; list the top 30 transitions per NF  
  > "we calculate a quantity called NF fraction (defined below)" (Outline of each component); "We show transitions with the top 30 NF fractions for each" (Outline of each component)
   - fitting: _not stated_
   - validation: _not stated_
6. **Test dependence on upper-state energy**: Plot NF1, NF3, NF5 fractions of multi-transition species against upper-state energy  
  > "using upper-state energy ($E_\mathrm{up}$) as an indicator" (Energy dependence of the NF components)
   - assumption: Upper-state energy is an indicator of excitation  
  > "using upper-state energy ($E_\mathrm{up}$) as an indicator" (Energy dependence of the NF components)
   - fitting: _not stated_
   - validation: _not stated_
7. **Compare NMF with PCA**: Compare NF maps with PC score maps of the earlier PCA and compute pixel-to-pixel Spearman rank correlations among NFs and among PCs  
  > "Figure [12](#fig:NFPC_relation) shows the pixel-to-pixel relation between the NF maps (left panel) and PC scores (right panel)." (Comparison with PCA); "We choose this coefficient over the Pearson correlation coefficient because Pearson correlation coefficients become zero for PCA because PC scores are orthogonal to each other" (Comparison with PCA)
   - fitting: _not stated_
   - validation: _not stated_
8. **Select tracers per band**: Define a tracer as a transition with NF fraction >= 0.6 for any component and tabulate by ALMA band  
  > "a tracer was defined as one with an NF fraction of 0.6 or greater for any of the components." (Useful tracers to understand the physical state)
   - parameter: NF fraction threshold 0.6  
  > "a tracer was defined as one with an NF fraction of 0.6 or greater for any of the components." (Useful tracers to understand the physical state)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **scikit-learn** : sklearn.decomposition.NMF for the factorization  
  > "The NMF algorithms are described in the `sklearn.decomposition.NMF` class" (NMF)
- **Python** : Implementation of the NMF analysis  
  > "In our implementation, we used the `scikit-learn` module of Python (cite: scikit-learn)." (NMF)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Contribution rate of NF1 | 23.1 | not stated | % | 5 | contribution rate of 23.1$\>\%$ for NF1 |
| Contribution rate of NF2 | 37.0 | not stated | % | 5 | 37.0$\>\%$ for NF2 |
| Contribution rate of NF3 | 16.5 | not stated | % | 5 | 16.5$\>\%$ for NF3 |
| Contribution rate of NF4 | 14.8 | not stated | % | 5 | 14.8$\>\%$ for NF4 |
| Contribution rate of NF5 | 8.6 | not stated | % | 5 | and 8.6$\>\%$ for NF5 |
| Highest NF3 fraction of SiO | 0.33 | not stated | dimensionless | 5 | the highest NF3 fraction of SiO (strong shock tracer) overall NF3 fraction is 0.33 |
| NF3 fraction of low-excitation transitions of other shock tracers | 0.61 - 0.94 | not stated | dimensionless | 5 | This fraction is relatively low compared to 0.61 – 0.94 for the low-excitation transitions of other shock tracers. |
| NF4 fraction of RRLs and 3 mm continuum | >= 0.89 | not stated | dimensionless | 5 | the RRLs and the 3 mm continuum contain an NF4 fraction of $\geq 0.89$, and the 0.8 mm continuum contains about 0.5 |
| NF4 fraction of 0.8 mm continuum | about 0.5 | not stated | dimensionless | 5 | the RRLs and the 3 mm continuum contain an NF4 fraction of $\geq 0.89$, and the 0.8 mm continuum contains about 0.5 |

## Qualitative findings

- NMF components are less orthogonal-constrained than PCs; NFs are mutually weakly correlated while PCs show strong rank correlations  
  > "On the other hand, each NF component does not have a strong correlation with each other." (Comparison with PCA)
- NF2 traces low-density extended gas including outflow streamers, extracted well by NMF but only weakly by PCA (PC4, PC5)  
  > "We argue that NF2 represents the low-density gas spreading throughout the galaxy." (Interpretation of each NF component)

## Claim tuples

- H: Can NMF separate molecular and physical components involved in star formation in NGC 253? | E: NMF with 5 components on 150 ALCHEMI moment 0 images, then interpretation of each NF map and its characteristic transitions | R: Five NF maps with distinct spatial distributions and characteristic transitions | F: NF2 is low-density gas, NF3 shocks, NF4 starburst regions, NF5 young star-forming regions, NF1 mid-excitation shock tracers | **supported**
- H: Do NF components depend on excitation? | E: NF fractions of multi-transition species versus upper-state energy | R: NF3 fraction falls and NF5 fraction rises with upper-state energy; NF1 is intermediate | F: NF3, NF1 and NF5 represent low-, intermediate- and high-excitation | **supported**
- H: Is NMF better than PCA at isolating single physical components in this dataset? | E: Compare NF maps with PCA maps of the same data and compare Spearman correlations among components | R: NF components are weakly correlated with each other while PCs are strongly rank-correlated; diffuse/outflow gas appears as one NF but only weakly in PCA | F: NMF extracts components tied to a single physical component, PCA components mix several | **supported**
- H: Which tuning would capture tracers of all components? | E: Select transitions with NF fraction >= 0.6 and tabulate by band | R: NF tracers are concentrated in Band 3 | F: Observing about 85-100 GHz in Band 3 gives structures involved in star formation | **supported**

## Reasoning

- Why this data: Use exactly the same images as the earlier PCA study for a direct comparison  
  > "We took exactly the same integrated intensity images used in the PCA study by (cite: Harada2024)" (ALCHEMI data)
- Why this method: NMF expected to give more unique physical components than PCA because emission only adds  
  > "Therefore, components obtained by NMF are expected to represent more unique components representing certain physical parameters than PCA." (Introduction)
- Alternative: More components (up to eight) rejected because components became too localized or noisy  
  > "As the number of components increases, more components contain structures that are too localized or noisy." (The case of another number of components)
- Alternative: Spearman correlation used instead of Pearson, which is zero for orthogonal PC scores  
  > "We choose this coefficient over the Pearson correlation coefficient because Pearson correlation coefficients become zero for PCA because PC scores are orthogonal to each other" (Comparison with PCA)
- How they decided it was enough: M = 5 chosen following the PCA study and checked against the reconstruction error  
  > "Following this, we decided to use 5 components in this study." (NMF)
- Limitation (authors): NMF can group multiple components of similar properties  
  > "It is important to note that there are some caveats in using NMF." (Interpretation of each NF component)
- Limitation (authors): NF numbering has no meaning and the NMF could not extract a component corresponding to the PCA PC1  
  > "PC1 is the prominent component of PCA, but NMF could not extract the component corresponding to PC1." (Comparison with PCA)
- Caveat (inferred, ours): Physical labels (shocks, starburst, young star formation) are interpretive and rest on spatial coincidence with literature, with no independent test such as radiative-transfer modelling
- Caveat (inferred, ours): Choice of M = 5 is partly inherited from PCA rather than determined by an objective criterion
- Caveat (inferred, ours): Results depend on the Harada2024 masking and image processing, and on normalizing each image to max 1, which favors extended maps in contribution rates
- Caveat (inferred, ours): No uncertainties on NF fractions or contribution rates, and no noise propagation or bootstrap

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: NMF parameter table (init, solver, tolerances, random state)
- Missing: The moment 0 images and masks of Harada2024 (the paper does not describe their creation)
- Missing: Software versions
- Missing: No statement of code or product release
- Data volume (inferred): Small (about 150 images of 512 x 640 pixels) if the Harada2024 moment 0 images are available; reproducing them from the ALCHEMI cubes would need hundreds of GB to TB
- Score (inferred): 3/5, The NMF recipe (matrix size, M = 5, Frobenius loss, normalization, scikit-learn) is clear and the results are numeric, but the parameter table and input images are not in the paper and come from an earlier paper.
- Rediscovery candidate: no, The inputs are processed images from an earlier paper and the data are not stated to be public, so the recipe cannot be redone from the text alone.

## Links

- Method: (cite: Harada2024) (Source of the moment 0 images, transition list, masking and the PCA used for comparison)
- Method: (cite: Martin2021) (Describes the ALCHEMI survey observations)
- Companion: (cite: Mijolla2024) (Applied NMF to simulated molecular line data)
- Related: ALCHEMI (ALMA Comprehensive High-resolution Extragalactic Molecular Inventory)

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 91,
  "stated": 43,
  "rate": 0.473
 },
 "evidence_ok": true
}
```
