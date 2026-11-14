# ALMA 2D super-resolution imaging survey of Ophiuchus Class I/flat spectrum/II disks. I. Discovery of new disk substructures

`2025PASJ...77..572S` | Publications of the Astronomical Society of Japan 2025 | first author: Shoshi, Ayumu | arXiv: 2503.21060 | DOI: 10.1093/pasj/psaf026

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Do Class I, Flat Spectrum and Class II disks in Ophiuchus show substructures, and when do they appear, as revealed by SpM super-resolution imaging of archival ALMA Band 6 data?  
  > "to unveil signs of substructure formation in these disks" (abstract)
- Target **78 Ophiuchus Class I/FS/II disks (ODISEA sample)**: coordinates _not stated_; z/distance ~140 pc (Gaia DR2/DR3 where available)  
  > "the Ophiuchus molecular cloud (at a distance of $\sim140$ pc" (1 Introduction); "we adopted the average distance of 140.0 pc, derived from the systems detected by Gaia DR2 and DR3, for the undetected objects" (2.1 Observation Data: Targets and Reduction); distance from Gaia DR2/DR3; average 140.0 pc adopted otherwise  
  > "the Ophiuchus molecular cloud (at a distance of $\sim140$ pc" (1 Introduction); "we adopted the average distance of 140.0 pc, derived from the systems detected by Gaia DR2 and DR3, for the undetected objects" (2.1 Observation Data: Targets and Reduction)

## Data provenance

- ALMA projects: 2016.1.00545.S, 2016.1.00484.L
- bands: Band 6 continuum  
  > "two SPWs for continuum observations, with central frequencies of 218 and 233 GHz in Band 6" (2.1 Observation Data: Targets and Reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-5, 42–45 antennas  
  > "using 42–45 ALMA antennas in C40-5 configurations with baseline lengths ranging from 17 m to 2647 m" (2.1 Observation Data: Targets and Reduction)
- baselines: 17 m to 2647 m  
  > "baseline lengths ranging from 17 m to 2647 m" (2.1 Observation Data: Targets and Reduction)
- angular resolution: CLEAN ~0.30"x0.22"; SpM effective 0.02"-0.2"  
  > "The spatial resolution in CLEAN images is about $0.30\ensuremath{''}\times0.22\ensuremath{''}$ (42$\times$31 au)." (3 Reconstructed SpM Images)
- max recoverable scale: ~2.1 arcsec  
  > "within the maximum recoverable scale ($\sim$2.1 arcsec)" (2.3 Imaging with Sparse Modeling)
- sensitivity: sigma = 0.16 mJy/beam in initial CLEAN images  
  > "emissions above 5$\sigma$ ($\sigma=$0.16 mJy beam$^{-1}$) in the initial CLEAN images" (2.2 Imaging with CLEAN and Source Selection)
- time on source: less than one minute per source  
  > "the observation time per source was less than one minute" (4.1 Measurements and Statistical Analysis of Disk Sizes)
- observing dates: 2017 July 13 and 14  
  > "The observations were conducted on July 13 and 14, 2017" (2.1 Observation Data: Targets and Reduction)
- pi or archival as stated: Archival, PI Lucas A. Cieza (ODISEA)  
  > "ALMA archival data (Project 2016.1.00545.S, PI Lucas A. Cieza)" (2.1 Observation Data: Targets and Reduction)
- Other facility **Gaia DR2/DR3**: Distances and binarity checks  
  > "Distances are taken from Gaia Data Release 2 and 3" (2.1 Observation Data: Targets and Reduction)
- Other facility **DSHARP ALMA data**: Long-baseline comparison images for 7 disks  
  > "The disks around seven systems (Elias 27, DoAr 25, Elias 24, Elias 20, SR 4, WSB 52, and DoAr 33) were observed in the DSHARP project" (3 Reconstructed SpM Images)
- External data: L_bol, T_bol and alpha_IR for all systems  
  > "We referred to (cite: Dunham_2015) for $L_{\rm bol}$ and $T_{\rm bol}$ of all the systems." (2.1 Observation Data: Targets and Reduction) [from (cite: Dunham_2015)]
- External data: eDisk T_bol and dust disk radii  
  > "The bolometric temperatures $T_{\rm bol}$ and dust disk radii $R_{\rm disk}$ for the eDisk samples are taken from (cite: Yen_2024_edisk)." (5.1 Comparison with Targets in eDisk Project) [from (cite: Yen_2024_edisk)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "The raw data were calibrated using the ALMA pipeline in the Common Astronomy Software Application package" (2.1 Observation Data: Targets and Reduction)
- casa version: CASA 4.7.2 (calibration)  
  > "version 4.7.2" (2.1 Observation Data: Targets and Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1517-2422 and J1733-1304  
  > "The quasars J1517-2422 and J1733-1304 were used as flux calibrators" (2.1 Observation Data: Targets and Reduction)
- flux scale uncertainty: _not stated_
- self calibration: SNR>=100: 2 phase + 1 amp+phase rounds (OST, OST/5, OST); 30<=SNR<100: one phase (OST) and one ap (OST/5); faint sources not self-calibrated  
  > "For images with an SNR of at least 100, we performed two rounds of phase self-calibration (`calmode=p`) and one round of amplitude and phase self-calibration" (2.2 Imaging with CLEAN and Source Selection)

### Imaging

- task: tclean in CASA 6.1.0; SpM with PRIISM 0.11.5  
  > "the data were imaged using the CASA task `tclean` in version 6.1.0 of CASA" (2.2 Imaging with CLEAN and Source Selection)
- deconvolver: multi-frequency synthesis nterm=2, Cotton-Schwab  
  > "We consistently employed multi-frequency synthesis (`nterm`$=2$; (cite: Rau_2011))" (2.2 Imaging with CLEAN and Source Selection)
- weighting robust: Briggs robust = 0.5  
  > "with Briggs weighting with `robust`=0.5" (2.2 Imaging with CLEAN and Source Selection)
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
- final rms: CLEAN sigma ~1.8-2.6 mJy/arcsec^2 (Table 2)  
  > "ISO-Oph 54 | 300$\times$227 (-66.9) | 235$\times$187 (117.2) | 2.0" (Table 2)

### Inherited from earlier work

- SpM imaging methodology and substructure categorization  
  > "following the methodology of (cite: Yamaguchi_2024)" (2.3 Imaging with Sparse Modeling) [from (cite: Yamaguchi_2024)]
- Point-source injection resolution and 10-fold CV  
  > "The effective spatial resolution of the SpM images is evaluated using the ‘point-source injection’ method, as described in (cite: Yamaguchi_2021)." (2.3 Imaging with Sparse Modeling) [from (cite: Yamaguchi_2021)]
- Same ALMA data as ODISEA  
  > "we use the same ALMA archival data (Project 2016.1.00545.S, PI Lucas A. Cieza) as the Ophiuchus Disk Survey Employing ALMA" (2.1 Observation Data: Targets and Reduction) [from (cite: Cieza_2019)]

### Not stated but needed to reproduce (our reading)

- Imaging cell size, image size, mask and clean threshold for tclean
- Grid of (Lambda_l, Lambda_tsv) values tried in SpM CV
- Self-calibration reference antenna/spw combine and per-source solint results
- Per-source flux scaling and gain solutions after self-cal
- Exact visibility weighting/uv range used in PRIISM
- Priors/bounds for the emcee Gaussian fit
- Criteria for disk-center and ring determination in intensity profiles

## Analysis recipe

1. **CLEAN imaging and self-calibration**: tclean with Briggs robust 0.5, MFS nterm=2; SNR-dependent self-calibration  
  > "In this study, the integration time `solint` and gain calibration settings were determined based on the SNR of the initial CLEAN image." (2.2 Imaging with CLEAN and Source Selection)
   - software: CASA
   - parameter: 5 sigma detection, sigma=0.16 mJy/beam; SNR>20 selection  
  > "We carefully selected datasets with relatively high SNRs \>20 on their CLEAN images" (2.1 Observation Data: Targets and Reduction)
   - fitting: _not stated_
   - validation: SNR improvement factor 1.1-2.0 after self-cal  
  > "show a signal-to-noise ratio (SNR) improvement by a factor of 1.1–2.0 after the self-calibration" (2.2 Imaging with CLEAN and Source Selection)
2. **SpM super-resolution imaging**: l1+TSV regularized imaging with 10-fold cross validation; Lambda_tsv increased by 10x for 11 sources with patchy structure  
  > "we conservatively chose an image generated with the $\Lambda_{tsv}$ value that is one order of magnitude larger than that selected by the CV approach" (2.3 Imaging with Sparse Modeling)
   - software: PRIISM, CASA
   - fitting: minimise chi-squared + l1 + TSV cost function; hyperparameters by 10-fold CV  
  > "selected the most suitable combination for each image by minimizing the cost function using the 10-fold cross-validation (CV) approach" (2.3 Imaging with Sparse Modeling)
   - validation: Total flux agrees with CLEAN within 5-10%; point-source injection for effective resolution; DSHARP comparison  
  > "We confirmed that the total fluxes of the SpM images were consistent with those of the CLEAN images within 5-10% error." (2.3 Imaging with Sparse Modeling)
3. **Measure PA and inclination**: 2D Gaussian fit to SpM images with MCMC; ellipse fit for 13 ring disks  
  > "We applied the Gaussian fitting with the Markov Chain Monte Carlo (MCMC) method" (4.1 Measurements and Statistical Analysis of Disk Sizes)
   - software: emcee, astropy
   - parameter: 2000 iterations, 100 walkers  
  > "We set the number of iterations to 2000 and the number of walkers to 100" (A.1 Gaussian Fitting with MCMC)
   - fitting: Gaussian2D model with 6 parameters, MCMC posterior  
  > "In summary, we use six parameters for the model image: $I_{\rm peak}$, (dRA, dDec), $\sigma_{\rm disk}$, $i_{\rm disk}$, and PA." (A.1 Gaussian Fitting with MCMC)
   - validation: Consistent with imfit and uvmodelfit within 10%  
  > "we used `imfit` and `uvmodelfit` to verify that the PA and $i_{\rm disk}$ values were consistent with these methods within a 10% error" (A.1 Gaussian Fitting with MCMC)
4. **Disk radii by curve of growth**: Deproject, azimuthally average, integrate to get R68% and R95%; uncertainty = geometric mean theta_eff/(2 sqrt(2 ln2))  
  > "We estimated the uncertainty of disk radius as $\sigma_{\rm Radius}=\left<\theta_{\rm eff}\right>/2\sqrt{2\ln2}$" (4.1 Measurements and Statistical Analysis of Disk Sizes)
   - assumption: Flux converged when difference <0.01%  
  > "less than 0.01% of $F_\nu(r_2)$" (A.2 Curve Growth Method for Disk Radius)
   - fitting: _not stated_
   - validation: Compact disk radii checked against visibility profiles (reduced chi2~1)  
  > "align well with the observational visibilities (reaching reduced - $\chi^{2}\sim1$)" (B.2 Fidelity for Brightness Distribution of Compact Disks)
5. **Categorize substructures**: Radial and major-axis intensity profiles classified as Smooth, Ring, Inflection, Spiral  
  > "we categorized the detected disks as either having a ‘Smooth’ distribution or one of three distinct substructure types: ‘Ring’, ‘Inflection’, and ‘Spiral’." (4.2 Categorization of Substructures)
   - software: CASA viewer
   - fitting: _not stated_
   - validation: Compare SpM images from short baselines with DSHARP long-baseline CLEAN; residuals up to ~30%  
  > "show maximum differences of about 30%" (B.3 Comparison with the Targets in the DSHARP Project)
6. **Statistics vs T_bol, R_dust and inclination**: KS tests; Monte Carlo (10000 iterations) KS tests of cos i vs uniform  
  > "We adopted the Monte Carlo routine to repeat this analysis ten thousand times" (5.2 Selection Bias of Disk Evolutionary Stages)
   - software: SciPy, Linmix
   - assumption: cos i uniform in 0-1 for random orientation  
  > "In this sample, $\cos i_{\rm disk}$ was randomly distributed between 0 and 1." (5.2 Selection Bias of Disk Evolutionary Stages)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2 (calibration), 6.1.0 (imaging): Calibration, tclean, imsmooth, split, uvmodelfit, imfit  
  > "the data were imaged using the CASA task `tclean` in version 6.1.0 of CASA" (2.2 Imaging with CLEAN and Source Selection)
- **PRIISM** 0.11.5: SpM imaging  
  > "Using the SpM imaging software `PRIISM` version 0.11.5" (2.3 Imaging with Sparse Modeling)
- **emcee** : MCMC fitting of PA and inclination  
  > "we used the MCMC approach with the Python module `emcee`" (A.1 Gaussian Fitting with MCMC)
- **astropy** : Gaussian2D / Rotation2D models  
  > "using `modeling.Gaussian2D` from the Python module `astropy`" (A.1 Gaussian Fitting with MCMC)
- **Linmix** : Bayesian linear regression of resolution ratio  
  > "We performed Bayesian linear regression in logarithmic space using the Python module `Linmix`" (B.1 Improvements of Spatial Resolution)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median resolution improvement of SpM vs CLEAN | 3.8 | not stated | dimensionless | 2 | The SpM images achieve an effective spatial resolution that is a median of 3.8 times higher than that of the CLEAN images. |
| Median R68% and R95% | 18 and 27 | not stated | au | 4 | with medians of 18 and 27 au, respectively |
| Disk categories | 43 Smooth, 26 Ring, 1 Spiral, 5 Inflection, 3 candidates | not stated | disks | 5 | We classify the disks as follows: 43 ‘Smooth’, 26 ‘Ring’, one ‘Spiral’, and 5 ‘Inflection’. |
| Disks with substructures | 32 (41%); 15 new | not stated | disks | 5 | we detected 32 disks with distinct substructures (‘Ring’, ‘Spiral’, and ‘Inflection’), accounting for 41% of all detected disks |
| KS p-value Class I/FS vs Class II inclination | 3.2e-3 | not stated | dimensionless | 6 | The $p$-value is 3.2$\times10^{-3}$ |
| Ring probability Class I, FS, II | 40%, 33%, 38% | not stated | percent | 5 | The probabilities of Class I, Class FS, and Class II disks having ring structures are 40%, 33%, and 38%, respectively |

## Qualitative findings

- Disk radius distributions are similar across Class I, FS and II (KS p>0.10)  
  > "resulting in $p$-values greater than 0.10, which support the similarity in distributions" (4.1 Measurements and Statistical Analysis of Disk Sizes)

## Claim tuples

- H: Do substructures exist in Class I/FS disks as often as in Class II? | E: SpM imaging and profile categorization of 78 Ophiuchus disks | R: ~30-40% show substructures at all stages | F: Substructures may form as early as Class I | **supported**
- H: Why does eDisk find fewer substructures? | E: Compare T_bol vs R_dust with eDisk | R: Substructures appear where T_bol>200-300 K and R_dust>~30 au | F: Sample selection explains the difference | **partially**
- H: Are inclinations random? | E: KS tests with Monte Carlo on cos i | R: Class II lacks high inclinations; not random | F: Likely SED misclassification of edge-on disks | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: SpM gives higher resolution than CLEAN from the same archival data  
  > "This technique can produce high-fidelity images with spatial resolution improved by a factor of $\sim$2-3" (1 Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Very compact disks lack long baselines; Smooth disks may hide substructure; inner disks of SR 4 and WL 17 not recovered  
  > "we note that ‘Smooth’ disks may also contain hidden substructures" (4.2 Categorization of Substructures)
- Caveat (inferred, ours): Substructure detection from SpM images with <1 min per source and 2.6 km baselines may be affected by sparse uv coverage
- Caveat (inferred, ours): Classification by eye without quantitative significance
- Caveat (inferred, ours): Average 140 pc assumed for many sources
- Caveat (inferred, ours): Class II inclination deficit explanation untested

## Reproducibility

- Data public (paper): Archival ALMA data, PRIISM public  
  > "we use the same ALMA archival data (Project 2016.1.00545.S, PI Lucas A. Cieza)" (2.1 Observation Data: Targets and Reduction)
- Products in archive: _not stated_
- Code: PRIISM is public at github.com/tnakazato/priism  
  > "is the public software for imaging ALMA observations based on the SpM technique" (2.3 Imaging with Sparse Modeling)
- Missing: Hyperparameter grid and masks
- Missing: Self-cal details per source
- Missing: Category decision thresholds
- Data volume (inferred): ~tens of GB (ODISEA Band 6 continuum, two nights)
- Score (inferred): 3/5, Public data and software with tabulated hyperparameters, but many tclean/self-cal and classification details are missing.
- Rediscovery candidate: yes, Public archival data, PRIISM public, hyperparameters and numeric radii tabulated.

## Links

- Method: (cite: Yamaguchi_2024) (SpM method and categorization applied to Taurus)
- Method: (cite: Yamaguchi_2021) (CV and point-source injection)
- Method: (cite: Nakazato_2020) (PRIISM software)
- Companion: (cite: Cieza_2019) (ODISEA survey of the same data)
- Companion: (cite: Ohashi_2023) (eDisk comparison)
- Related: ODISEA
- Related: eDisk
- Related: DSHARP
- Related: CAMPOS
- Related: VANDAM

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 54,
  "rate": 0.675
 },
 "evidence_ok": true
}
```
