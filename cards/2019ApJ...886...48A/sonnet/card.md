# Multi-wavelength Properties of Radio- and Machine-learning-identified Counterparts to Submillimeter Sources in S2COSMOS

`2019ApJ...886...48A` | The Astrophysical Journal 2019 | first author: An, Fang Xia | arXiv: 1910.03596 | DOI: 10.3847/1538-4357/ab4d53

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: Which radio and optical/NIR counterparts do the S2COSMOS SCUBA-2 sources have when a radio+machine-learning method trained on ALMA SMGs is applied, and what are the multi-wavelength and clustering properties of these SMGs?  
  > "We identify multi-wavelength counterparts to 1,147 submillimeter sources from the S2COSMOS SCUBA-2 survey of the COSMOS field" (abstract)
- Target **S2COSMOS SCUBA-2 sources in the COSMOS field**: coordinates COSMOS field (about 2 deg^2); no single position stated  
  > "In this work, we use the whole sample of 1,147 sources in our analysis." (2.1 S2COSMOS); z/distance photometric redshifts z=0.2-5.7, median 2.3  
  > "In this work, we use the whole sample of 1,147 sources in our analysis." (2.1 S2COSMOS); distance from COSMOS2015 catalog (Laigle16)  
  > "In this work, we use the whole sample of 1,147 sources in our analysis." (2.1 S2COSMOS)

## Data provenance

- ALMA projects: 2016.1.00463.S, 2012.1.00090.S, 2015.1.01528.S, 2016.1.00434.S
- bands: Band 7 (870 um)  
  > "The ALMA follow-up observations were taken in Band 7 (870 $\mu$m) in April and May 2018." (2.2.1 AS2COSMOS)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA Cycle 4 pilot  
  > "We have completed an ALMA Cycle 4 pilot study of the brightest 160 single-dish submillimeter sources from S2COSMOS" (2.2.1 AS2COSMOS)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: median synthesised beam 0.8x0.79 arcsec  
  > "The median synthesised beams of the 184 ALMA maps is 0$\ensuremath{''}8\times0.79\ensuremath{''}$." (2.2.1 AS2COSMOS)
- max recoverable scale: _not stated_
- sensitivity: median sigma_870um = 0.2 mJy/beam over 184 maps  
  > "our full AS2COSMOS sample includes 184 ALMA maps with median sensitivity $\sigma_{\rm 870\,\mu m}=0.2$ mJy beam$^{-1}$" (2.2.1 AS2COSMOS)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **JCMT SCUBA-2 (S2COSMOS)**: 850 um survey with 1,147 sources  
  > "In total, 1020 and 127 submillimeter sources are detected at a significance level of $>4\,\sigma$ and $>4.3\,\sigma$ in the main and supp regions" (2.1 S2COSMOS)
- Other facility **VLA 3 GHz**: radio counterparts  
  > "(cite: Smolcic17) detected 10,830 3 GHz radio sources at $\ge5\,\sigma$" (2.3.1 VLA-3 GHz radio maps)
- Other facility **COSMOS2015 catalog**: optical/NIR photometry, photo-z, stellar masses  
  > "The COSMOS2015 catalog (cite: Laigle16) from UltraVISTA-DR2 surveys are used to identify optical/NIR counterparts" (2.3.2 Optical/NIR/FIR catalogs)
- External data: A3COSMOS ALMA detections used as training set  
  > "All the publicly available ALMA archive data in the COSMOS field were processed, imaged and analysed in the on-going ALMA archive mining project A$^{3}$COSMOS (cite: dLiu19)" (2.2.2 A3COSMOS) [from (cite: dLiu19)]
- External data: Super-deblended FIR photometry and SFRs  
  > "In our work, we use these estimates of SFR to investigate the star-formation efficiency" (2.3.2 Optical/NIR/FIR catalogs) [from (cite: Jin18)]
- External data: AGN classifications of radio sources  
  > "(cite: Smolcic17b) has identified AGNs from the VLA-COSMOS 3 GHz radio data using the X-ray, mid-infrared (MIR) color-color and multi-wavelength SEDs selection methods" (4.3 AGN fraction) [from (cite: Smolcic17b)]

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

- Radio+ML identification method, p<=0.065 cut and performance estimates  
  > "we employ the same radio$+$machine-learning method developed in An18 to our new SCUBA-2 submillimeter survey in the COSMOS field" (1 Introduction) [from An18 (cite: An18)]
- ALMA data reduction and source detection similar to AS2UDS  
  > "The data reduction procedures and source detection method are similar to that of the ALMA-SCUBA-2 Ultra Deep Survey (cite: Stach18; Stach19)." (2.2.1 AS2COSMOS) [from (cite: Stach18; Stach19)]
- Full AS2COSMOS observation details  
  > "Full details of the observations are presented in J. M. Simpson et al. (in preparation)." (2.2.1 AS2COSMOS) [from J. M. Simpson et al. 2019 in preparation]

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging settings (robust, cleaning, calibrators) for AS2COSMOS
- SVM/XGBoost hyperparameters and optimised values
- Which COSMOS2015 magnitudes and quality cuts define features exactly
- Random-catalogue generation details for clustering

## Analysis recipe

1. **Radio identification**: Corrected-Poissonian p-value for 3 GHz sources within 8.7 arcsec error circles, p<=0.065  
  > "In this work, we adopt this limit in the radio identification." (3.1 Radio identification)
   - fitting: _not stated_
   - validation: _not stated_
2. **Machine-learning classification of SMGs**: XGBoost trained on A3COSMOS+AS2COSMOS using z_phot, M_H and NIR colours  
  > "Therefore, we choose the training set based on the A$^{3}+$AS2COSMOS surveys to train the machine-learning classifier in this work." (3.2.1 Training set)
   - software: XGBoost, SVM
   - fitting: parameters optimised by five-fold cross-validation  
  > "The parameters of both SVM and XGBoost classifiers are optimized by five-fold cross-validation (cite: Kohavi95)" (3.2.1 Training set)
   - validation: five-fold CV repeated 100 times; recall, precision, FPR, F1, ROC AUC  
  > "We repeat the five-fold cross-validation 100 times to estimate the scatter in evaluation metrics." (3.2.1 Training set)
3. **Clustering and halo mass**: Landy-Szalay ACF with integral constraint, jackknife covariance, bias relative to CAMB dark matter ACF  
  > "we first divide our sample into $N_{sub}=32$ subsamples and remove one subsample at a time for each Jackknife realization" (4.6 SMG clustering)
   - software: CAMB
   - assumption: power-law w=A theta^-0.8; Planck 2015 cosmology  
  > "A power-law model $w(\theta)=A\,\theta^{-0.8}$ is assumed for the ACF of galaxies" (4.6 SMG clustering)
   - fitting: multivariate Gaussian fit over 8-500 arcsec using jackknife covariance  
  > "We then fit the observed ACF (Equation [\[e:equation2\]](#e:equation2)) by performing a multivariate Gaussian fit on the scales of 8–500$\ensuremath{''}$" (4.6 SMG clustering)
   - validation: _not stated_

## Software

- **CASA** v4.2.2-5.1.1: ALMA data reduction  
  > "The ALMA data were reduced using the the Common Astronomy Software Application (cite: McMullin07) v4.2.2-5.1.1." (2.2.1 AS2COSMOS)
- **XGBoost** : SMG classification  
  > "we use two machine-learning algorithms, Support Vector Machine (SVM) (cite: Vapnik95) and XGBoost (cite: CG16)" (3.2 Machine-learning classification)
- **CAMB** 1.0.7: matter power spectrum  
  > "The power spectrum $P(k, z)$ in this fiducial cosmology is computed using the software CAMB (cite: Lewis00; Lewis19)" (4.6 SMG clustering)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Identification rate | 78 | 9 | % | 2 | yielding an overall identification rate of ($78\pm9$)% |
| Total counterparts | 1,222 | not stated | sources | 2 | our radio combined machine-learning method identifies 1,222 optical/NIR/radio counterparts |
| Median photometric redshift | 2.3 | 0.1 | dimensionless | 0 | $z_{\rm median}=2.3\pm0.1$ |
| AGN fraction | 19 | 4 | % | 0 | the AGN fraction in our radio$+$machine-learning identified counterparts of S2COSMOS sources is ($19\pm4$)% |
| SMG halo mass | 1.2 | 0.3 | 1e13 h^-1 Msun | 3 | XGB IDs / $1.5^{+0.3}_{-0.2}$ / 2,226 / 3.0$^{+0.2}_{-0.2}$ / 1.2$\pm0.3$ |
| ML-identified SMGs in whole COSMOS | 6,877 | not stated | sources | 2 | Among them, 6,877 (2%) are classified as the likely counterparts of SMGs. |

## Qualitative findings

- Counterparts have higher SFR and stellar mass than the field NIR/radio population  
  > "tend to be at higher redshift, while having higher star-formation activity and higher stellar mass" (4.4 Star-formation rate and stellar mass)

## Claim tuples

- H: Radio+ML can identify counterparts for most S2COSMOS sources | E: Applied An18 method with A3COSMOS+AS2COSMOS training | R: 1,222 counterparts to 897 sources; 78% identification | F: A representative SMG sample at z<~3 was obtained | **supported**
- H: SMGs reside in massive halos and may be progenitors of massive ellipticals | E: Angular clustering of 6,877 ML-selected SMGs vs SFGs and passive galaxies | R: halo mass (1.2±0.3)e13 h^-1 Msun | F: Consistent with SMGs as progenitors of massive quiescent galaxies | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: SVM was slightly better but XGBoost chosen since it handles missing features, enlarging the sample  
  > "We therefore prefer to use the XGBoost classifier in this work to increase the sample size of both training set and test sample" (3.2.1 Training set)
- How they decided it was enough: _not stated_
- Limitation (authors): Multiplicity results are affected by incompleteness and false positives  
  > "although our result is affected by the incompleteness and false positive identification of the radio$+$machine-learning method" (4.2 Multiplicity)
- Caveat (inferred, ours): Photometric-redshift errors affect the selection function and clustering
- Caveat (inferred, ours): ML-selected SMGs lack direct submillimeter confirmation
- Caveat (inferred, ours): Precision is estimated from UDS self-tests, not COSMOS

## Reproducibility

- Data public (paper): A3COSMOS uses public archival ALMA data; AS2COSMOS details deferred  
  > "All the publicly available ALMA archive data in the COSMOS field were processed" (2.2.2 A3COSMOS)
- Products in archive: _not stated_
- Missing: Classifier hyperparameters
- Missing: Access to AS2COSMOS and A3COSMOS catalogs
- Missing: Details deferred to An18 and Simpson19
- Data volume (inferred): Mostly catalogs; ALMA maps not needed if catalogs obtained (~tens of GB otherwise)
- Score (inferred): 3/5, Catalog-based pipeline with public inputs but key details deferred to An18 and unpublished catalogs.
- Rediscovery candidate: no, Depends on unpublished AS2COSMOS catalog and An18 settings; ALMA is only used for the training set.

## Links

- Method: An18 (cite: An18) (Defines the radio+machine-learning method)
- Method: (cite: Simpson19) (S2COSMOS survey and catalog)
- Companion: (cite: dLiu19) (A3COSMOS database)
- Related: AS2COSMOS
- Related: A3COSMOS
- Related: AS2UDS
- Related: S2COSMOS
- Related: S2CLS

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 31,
  "rate": 0.456
 },
 "evidence_ok": true
}
```
