# A machine-learning approach for identifying the counterparts of submillimetre galaxies and applications to the GOODS-North field

`2019MNRAS.489.1770L` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Liu, Ruihan Henry | arXiv: 1901.09594 | DOI: 10.1093/mnras/stz2228

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: Can machine-learning classifiers trained on ALMA-identified SMG counterparts in UDS identify SMG counterparts in fields lacking interferometric follow-up (GOODS-N)?  
  > "We apply our trained neural network to the GOODS-North field, which also has single-dish submm observations from the S2CLS and deep multiwavelength data but little high-resolution interferometric submm imaging" (abstract)
- Target **UKIDSS UDS field SMGs (AS2UDS, 716 SCUBA-2 sources)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **GOODS-North field (67 SCUBA-2 sources)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00090.S, 2015.1.01528.S, 2016.1.00434.S
- bands: 870 um  
  > "have been followed up with ALMA at 870 $\mu$m in the AS2UDS survey" (2.1.2 Interferometric follow-up)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: tapered 0.5 arcsec at 870 um  
  > "The maps produced by these observations had a tapered angular resolution of 0.5 arcsec" (2.1.2 Interferometric follow-up)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **SCUBA-2/JCMT S2CLS**: 850 um single-dish catalogue of UDS and GOODS-N sources  
  > "we used the subset of the S2CLS covering the UDS field, which encompasses an area of 0.9 deg$^2$ at 850 $\mu$m" (2.1.1 The single-dish survey)
- Other facility **UKIDSS/VISTA/CFHT/Subaru/Spitzer**: 12-band optical/NIR photometry for UDS  
  > "spanning the 12 wavebands described above" (2.1.3 The multiwavelength follow-up)
- Other facility **SMA**: partial interferometric follow-up of GOODS-N used for comparison  
  > "the GOODS-N field has seen a partial interferometric follow-up from the SMA" (2.2 Prediction catalogue)
- External data: AS2UDS ALMA catalogue of SMGs  
  > "In all, a total of 695 SMGs were detected above $4.3\sigma$ by ALMA." (2.1.2 Interferometric follow-up) [from (cite: Stach2018)]
- External data: GOODS-N optical/NIR catalogue  
  > "(see (cite: hsu2019) for details)" (2.2 Prediction catalogue) [from (cite: hsu2019)]
- External data: SMA detections in GOODS-N  
  > "the 33 SMA detections of SCUBA-2 sources found in their work" (5.2 Comparison with known GOODS-N SMGs) [from (cite: cowie2017)]

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

- UDS multiwavelength photometric catalogue and matching to ALMA SMGs  
  > "the details of the photometric-matched catalogue will be described in Hartley et al. in prep." (2.1.3 The multiwavelength follow-up) [from Hartley et al. in prep.; (cite: an2018)]
- Use of UDS subset of S2CLS as training field  
  > "Following the previous work carried out by (cite: an2018), we used the subset of the S2CLS covering the UDS field" (2.1.1 The single-dish survey) [from (cite: an2018)]

### Not stated but needed to reproduce (our reading)

- Hartley et al. photometric catalogue is unpublished (in prep.)
- Random seeds and exact hyperparameter grids/final values for non-NN models
- Full per-NN layer configuration is only given in a garbled table
- Exact ALMA data reduction (done in AS2UDS paper)

## Analysis recipe

1. **Build training set**: SMGs from ALMA matches; non-SMGs are multiwavelength sources within 7 arcsec of SCUBA-2 sources with ALMA detections, stars removed with SExtractor classification  
  > "The resulting training set for our ML testing contained a total of 1439 sources: 514 SMGs; and 925 non-SMGs" (2.1.3 The multiwavelength follow-up)
   - software: SExtractor
   - fitting: _not stated_
   - validation: _not stated_
2. **Train and compare classifiers**: 14 features (12 magnitudes, 850 um flux, scaled angular separation); LR, SVM, RF, LDA, KNN, GNB, DT, BDT and four NNs; hyperparameters tuned by 4-fold CV on F1  
  > "We chose to set $k=4$ in order to have a more reasonable computation time." (3.2 Hyperparameter optimization)
   - software: scikit-learn, XGBoost, Keras, Tensorflow, fancyimpute
   - parameter: NN: 150 epochs, batch 64, ADAM lr 0.001 with time-based decay  
  > "training each network for 150 epochs, with 64 samples per batch provided a good solution." (9 Deep Neural Networks)
   - fitting: _not stated_
   - validation: 4-fold CV repeated 50 times; blank-field tests  
  > "we repeated this process 50 times, thus obtaining a total of 200 estimates" (3.3 Validation)
3. **Predict GOODS-N counterparts**: Ensemble of 100 1-layer NNs, mean score cutoff 0.5  
  > "training 100 NNs in parallel and taking the average and standard deviation of the resulting prediction scores." (5.1 A catalogue of ML-identified SMGs)
   - software: Keras
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **scikit-learn** : traditional ML models  
  > "Most of our additional models were implemented using the `scikit-learn`[^3] package for `Python`" (3.1 Algorithms)
- **XGBoost** : boosted decision trees  
  > "This model is implemented with the `xgboost` package." (8 Machine Learning Models)
- **Keras** : neural networks with Tensorflow backend  
  > "we constructed our NNs using the `Keras`[^4] NN interface library" (3.1 Algorithms)
- **fancyimpute** : imputation tests  
  > "We used the `fancyimpute` package for `Python`" (3.4 Imputation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1-layer NN F1 score (CV) | 85.6 | 2.7 | per cent | 2 | 1 Layer & $92.5 \pm 1.4$ & $85.9 \pm 3.5$ & $85.4 \pm 3.7$ & $85.6 \pm 2.7$ |
| Manual colour-cut F1 score | 81.4 | not stated | per cent | 2 | Manual & 90.2 & 78.5 & 84.6 & 81.4 |
| GOODS-N SCUBA-2 sources with ML-identified counterpart | 36 of 67 (45 SMG candidates in 290 sources) | not stated | sources | 3 | These 45 multiwavelength ML-identified SMG candidates lie in 36 SCUBA-2 sources (out of a possible 67) |
| GOODS-N blank-field false positive rate | 3.7 | not stated | per cent | 3 | only 37 out of 1000 fake ‘beams’ contained any false positive IDs, giving a false positive of 3.7 per cent |

## Qualitative findings


## Claim tuples

- H: ML can identify SMG counterparts better than manual colour cuts | E: Compare ML classifiers and tuned colour cuts by 4-fold CV | R: NN F1 ~85.6 vs manual 81.4 per cent | F: Neural network best, but improvement is modest (~5 per cent) | **supported**
- H: The UDS-trained network transfers to GOODS-N | E: Apply ensemble NN to GOODS-N and compare with SMA and super-deblending | R: 36/67 sources classified; 15 of 33 SMA detections matched | F: Reasonable agreement with other catalogues | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Imputation of missing features gave no significant improvement, so only full-featured sources were used  
  > "Even with this specific imputation method, we saw no significant improvement compared to removing examples with missing data." (4.2 Performance of imputation)
- How they decided it was enough: _not stated_
- Limitation (authors): Only fully featured sources classified; photometric uncertainties ignored  
  > "Currently, our classification algorithm does not take into account missing features or flux density uncertainties." (6.3 Missing Features and uncertainties)
- Caveat (inferred, ours): Training and prediction catalogues differ in depth
- Caveat (inferred, ours): Training labels depend on 4.3 sigma ALMA detection threshold
- Caveat (inferred, ours): Non-SMG labels may include undetected SMGs

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Hartley et al. UDS photometric catalogue
- Missing: GOODS-N catalogue details (hsu2019)
- Missing: Code and random seeds
- Data volume (inferred): small (catalogues only, MB)
- Score (inferred): 3/5, Methods are described but depend on unpublished catalogues; ALMA data used only via a published catalogue.
- Rediscovery candidate: no, Analysis uses catalogues not ALMA visibilities, and the key input catalogue is unpublished.

## Links

- Method: (cite: Stach2018) (AS2UDS ALMA catalogue)
- Method: (cite: an2018) (previous ML SMG identification with SVM)
- Companion: (cite: cowie2017) (SMA follow-up in GOODS-N)
- Companion: (cite: liu2018) (super-deblending catalogue compared)
- Related: AS2UDS
- Related: S2CLS
- Related: UKIDSS UDS
- Related: GOODS-North

## Checks

```json
{
 "quotes": 32,
 "quotes_ok": 32,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 22,
  "rate": 0.31
 },
 "evidence_ok": true
}
```
