# Solving self-calibration of ALMA data with an optimization method

`2025PASJ...77..260I` | Publications of the Astronomical Society of Japan 2025 | first author: Ikeda, Shiro | arXiv: 2412.03183 | DOI: 10.1093/pasj/psae114

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type technical_calibration_or_instrument

## Science

- Fields: instrumentation, protoplanetary_disks
- Question: Can self-calibration (gain correction) be reformulated as a regularized optimization problem and combined with the PRIISM RML imaging into a single optimization that estimates both gains and image for ALMA data?  
  > "Combining this new method with our previously proposed imaging method, PRIISM, the whole process of the self-calibration of radio interferometry is redefined as a single optimization problem with regularization." (abstract)
- Target **HL Tau**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **SDP.81**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **HD 142527**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00425.S, 2011.0.00015.SV, 2011.0.00016.SV
- bands: HL Tau and SDP.81: Band 6; HD 142527: Band 7 (343 GHz)  
  > "We used the spectral window 0 out of the total of four spectral windows at Band 6." (4.1 HL Tau); "The observations were performed on March 11, 2015, at 343 GHz (Band 7)." (4.3 HD 142527)
- frequencies and spectral setup: HD 142527: four 2 GHz spectral windows, lowest centered at 336 GHz used; HL Tau: spw 0 of four; SDP.81: first spectral channel  
  > "Among the four 2 GHz spectral windows, the lowest band centered at 336 GHz was used for image reconstruction." (4.3 HD 142527); "We used the first spectral channel of Band 6" (4.2 SDP. 81)
- continuum bandwidth: _not stated_
- arrays: HD 142527: thirty-eight 12 m antennas  
  > "The observing array consisted of thirty-eight 12 m antennas, and the on-source time of HD 142527 was 1.2 h." (4.3 HD 142527)
- configurations: HL Tau and SDP.81 from the 2014 ALMA Long Baseline Campaign  
  > "This was observed as a part of the 2014 ALMA Long Baseline Campaign (cite: 2015.ALMA.apjl)." (4.1 HL Tau)
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: HD 142527: 1.2 h  
  > "the on-source time of HD 142527 was 1.2 h" (4.3 HD 142527)
- observing dates: HL Tau: 29 October 2014 used (of 5 days); SDP.81: all 5 days; HD 142527: March 11, 2015  
  > "we used the data from 29 October 2014 for the imaging" (4.1 HL Tau); "The observations were performed on March 11, 2015" (4.3 HD 142527)
- pi or archival as stated: _not stated_

## Processing

### Calibration

- pipeline or manual: HL Tau/SDP.81: tweaked standard calibration scripts with calwt=True; HD 142527: ALMA pipeline as in Kataoka et al. 2016, no iterative self-calibration  
  > "The data were calibrated using a tweaked version of the standard calibration scripts provided together with the uncalibrated data." (4.1 HL Tau); "using the ALMA pipeline with CASA 4.7.2, except for performing iterative self-calibration" (4.3 HD 142527)
- casa version: CASA 4.2.2 (HL Tau, SDP.81); CASA 4.7.2 (HD 142527)  
  > "We performed the calibration with CASA 4.2.2." (4.1 HL Tau); "using the ALMA pipeline with CASA 4.7.2" (4.3 HD 142527)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: PRIISM RML imaging (MFISTA, L1 + TSV regularization) instead of CLEAN  
  > "We have implemented the Monotonic Fast Iterative Shrinkage-Thresholding Algorithm (MFISTA) introduced in (cite: 2009.BeckTeboulle.siam)" (3.1 PRIISM: an RML method for imaging)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: HL Tau 4.5x4.5 arcsec, 512x512 pix; SDP.81 8.0x8.0 arcsec, 2048x2048 pix; HD 142527 5.12x5.12 arcsec, 512x512 pix  
  > "The size of the image field was set to $4.5\,\mbox{arcsec}\times4.5\,\mbox{arcsec}$, and the number of pixels was set to $512\times512$ pixels." (4.1 HL Tau); "the number of pixels was set to 2048$\times$2048 pixels" (4.2 SDP. 81)
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

- HD 142527 calibration done the same way as the earlier paper  
  > "The data set was calibrated in the same way as (cite: 2016.Kataoka.apjl), using the ALMA pipeline with CASA 4.7.2" (4.3 HD 142527) [from Kataoka et al. 2016 (cite: 2016.Kataoka.apjl)]
- L1 + TSV regularization for imaging  
  > "we follow our proposal in (cite: 2018.Kuramochi.apj) where $L^1$ norm and the Total Squared Variation (TSV) for promoting sparsity and smoothness of the image" (3.1 PRIISM: an RML method for imaging) [from (cite: 2018.Kuramochi.apj)]
- Gain optimization algorithm extended from Repetti et al.  
  > "We followed the idea in (cite: 2017.Repetti.mnras) for the optimization" (3.2 Regularized optimization problem for gain correction) [from (cite: 2017.Repetti.mnras)]

### Not stated but needed to reproduce (our reading)

- Search ranges (integer limits) of Lambda and M exponents for Bayesian optimization
- Selected lambda and mu values (in tables not included in text)
- Convergence criteria and rho schedule for the gain solver
- Integration time / averaging interval of each dataset
- Which SDP.81 channel/frequency exactly and how the 5 days were combined
- Weighting/sigma_k computation details
- Self-calibration code is not yet released
- Comparison CLEAN imaging parameters, if any

## Analysis recipe

1. **Calibrate visibilities**: Tweaked standard calibration scripts with calwt=True (HL Tau, SDP.81); ALMA pipeline for HD 142527  
  > "we changed `calwt` parameter for the application of bandpass, gain, and flux scaling solutions to `True` in the standard calibration scripts" (4.2 SDP. 81)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Image estimation by RML**: Minimize weighted squared error plus L1 and TSV regularization with non-negativity using MFISTA and NUFFT  
  > "For the computation of $\mathcal{F}_k(\bm{x})$, we realized the NonUniform FFT (NUFFT) described in (cite: 2004.LeslieLee.siam) with the FFTW3 package." (3.1 PRIISM: an RML method for imaging)
   - software: PRIISM, FFTW3
   - fitting: Convex optimization for fixed lambda1, lambda2  
  > "Once positive coefficients $\lambda_1$ and $\lambda_2$ are given, this optimization problem is convex with respect to $\bm{x}$." (3.1 PRIISM: an RML method for imaging)
   - validation: _not stated_
3. **Gain correction by regularized optimization**: Minimize misfit plus temporal smoothness penalties on gain (mu1, mu2) with per-station amplitude constraint; solved via splitting g,h with increasing rho and closed-form updates  
  > "Starting with a small $\rho$, solve the above equation with respect to $h_{\alpha l}$ and $g_{\alpha l}$ alternatively." (Solving Self-Calibration Problem)
   - parameter: Initial gains g=1; alternate image and gain steps up to 10 iterations  
  > "In the following examples, we set the maximum iterations of steps 2 and 3 to 10." (3.3 Overall imaging)
   - assumption: Gain constant across field of view, smooth in time  
  > "assuming that the gain of each telescope does not change within the field of view but changes over time" (3.2 Regularized optimization problem for gain correction)
   - fitting: Non-convex; local minimum  
  > "The problem is non-convex, and we propose an efficient method that converges to a local minimum." (Conclusion)
   - validation: Compared with image without self-calibration; checked C1, C2 statistics  
  > "Almost all the power of the image is concentrated in the covering ellipsoid ($C_1 > 0.99$), and the power of the residual is distributed equally over $u$–$v$ distance ($C_2 > 0.99$)." (HL Tau)
4. **Select hyperparameters by Bayesian optimization**: scikit-optimize with 30 trials; lambdas minimize misfit under soft constraints C1>=0.995, C2>=0.99 (kappa=1e6); mus tune gain std to targets (5 deg, 0.05) or (15 deg, 0.10); parameters as powers of 10 with integer exponents; alternate 10 iterations  
  > "The number of trials is fixed to 30 for `scikit-optimize`." (3.4 Choosing the parameters); "one is $(5\mbox{\,deg}, 0.05)$ and the other is $(15\mbox{\,deg}, 0.10)$" (3.4 Choosing the parameters)
   - software: scikit-optimize
   - assumption: Target gain variances set by hand  
  > "We set the target values by hand in this work." (3.4 Choosing the parameters)
   - fitting: Bayesian optimization of soft-constrained objective  
  > "The two conditions of $\lambda$’s are implemented as soft constraints in equation ([\[eq:Bayes_lambda\]](#eq:Bayes_lambda))." (Choosing the parameters)
   - validation: Check C1 and C2 values and gain variances in tables  
  > "The statistics related to the image and the gains are shown in table [\[tab:HLTau stats\]](#tab:HLTau stats)." (HL Tau)

## Software

- **PRIISM** : RML imaging and new self-calibration  
  > "We also have developed and released the RML software Python module for Radio Interferometry Imaging with Sparse Modeling (PRIISM) for imaging with ALMA" (Introduction)
- **CASA** 4.2.2 / 4.7.2: Calibration of visibilities  
  > "We performed the calibration with CASA 4.2.2." (4.1 HL Tau)
- **scikit-optimize** : Bayesian optimization of regularization parameters  
  > "we used a Python implementation, `scikit-optimize` (cite: skopt), for the Bayesian optimization." (3.4 Choosing the parameters)
- **FFTW3** : NUFFT computation  
  > "with the FFTW3 package" (3.1 PRIISM: an RML method for imaging)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HL Tau number of uv points | 1,884,732 | not stated | count | 0 | The numbers of the $u$–$v$ points and the gains are 1,884,732 and 116,399, respectively. |
| HL Tau number of gains | 116,399 | not stated | count | 0 | The numbers of the $u$–$v$ points and the gains are 1,884,732 and 116,399, respectively. |
| SDP.81 uv points / gains | 1,650,810 / 110,170 | not stated | count | 0 | The number of the $u$–$v$ points and the gains are 1,650,810 and 110,170, respectively. |
| HD 142527 uv points / gains | 49,662 / 3,288 | not stated | count | 0 | The numbers of the $u$–$v$ points and the gains are 49,662 and 3,288, respectively. |
| C1 and C2 for HL Tau and SDP.81 results | > 0.99 | not stated | dimensionless | 4 | Almost all the power of the image is concentrated in the covering ellipsoid ($C_1 > 0.99$), and the power of the residual is distributed equally over $u$–$v$ distance ($C_2 > 0.99$). |

## Qualitative findings

- With self-calibration the images look sharper and peak intensities are higher than without, for all three datasets  
  > "The images give sharper impressions, and the peak intensities are higher than that of figure [2](#fig:images_uncalibrated)a." (4.1 HL Tau)
- Larger allowed gain variance gives sharper images and higher peaks  
  > "As larger variances are allowed for the gains, the image becomes sharper, and the peak intensities get higher." (Conclusion)

## Claim tuples

- H: Gain correction can be solved as a regularized optimization jointly with RML imaging on ALMA data | E: Applied to HL Tau, SDP.81, HD 142527 with two gain-variance targets | R: Sharper images with higher peak intensities and smoothly varying gains | F: The method gives promising results | **supported**
- H: Hyperparameter choice via C1, C2 conditions and gain variance targets is workable | E: Bayesian optimization with 30 trials | R: C1>0.99 in all; C2>0.99 except HD 142527 small variance (not above 0.9); gain variances not exactly at targets | F: Partially achieved; target variance setting remains an open problem | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Stay with iterative gain-correction approach for ALMA rather than closure quantities, which are computationally demanding  
  > "we stay with the iterative method for ALMA, since the larger number of antennas and easier prior calibration means it is usually easier to obtain images" (2.4 Current approaches to self-calibration)
- Alternative: Cross-validation for lambda selection rejected as computationally demanding  
  > "we use a different approach in this paper because the computation of CV is demanding." (3.4 Choosing the parameters)
- How they decided it was enough: _not stated_
- Limitation (authors): Target gain variances set by hand; no ground truth; must be tested on more data and compared with CLEAN  
  > "The method must be tested with other ALMA data, and the results must be compared closely with traditional CLEAN methods." (Conclusion)
- Caveat (inferred, ours): No quantitative comparison with CLEAN plus standard self-calibration
- Caveat (inferred, ours): Image quality assessed qualitatively; no ground truth or simulations
- Caveat (inferred, ours): Results depend on hand-chosen variance targets
- Caveat (inferred, ours): Non-convex; local minima possible
- Caveat (inferred, ours): Self-calibration code not yet public

## Reproducibility

- Data public (paper): ALMA science verification data and project 2015.1.00425.S used  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2015.100425.S, #2011.0.00015.SV, and #2011.0.00016.SV." (Acknowledgments)
- Products in archive: _not stated_
- Code: PRIISM imaging public; self-calibration part to be provided later  
  > "The RML imaging algorithm has already been made available to the public as a PRIISM package, and we will soon provide the self-calibration part." (Conclusion)
- Missing: Self-calibration code release
- Missing: Selected parameter tables
- Missing: Search ranges for hyperparameters
- Data volume (inferred): Tens of GB (long-baseline HL Tau/SDP.81 raw data plus calibration)
- Score (inferred): 3/5, Data public and algorithm fully specified mathematically, but the self-calibration code is unreleased and several parameters are missing.
- Rediscovery candidate: no, Results are qualitative image quality and code is unreleased.

## Links

- Method: (cite: 2017.Repetti.mnras) (Basis of gain optimization algorithm)
- Method: (cite: 2018.Kuramochi.apj) (L1+TSV regularization)
- Method: (cite: 2020.NakazatoIkeda.priism) (PRIISM software)
- Companion: (cite: 2020.Yamaguchi.apj) (Earlier RML analysis of HD 142527 data)
- Companion: (cite: 2016.Kataoka.apjl) (HD 142527 data and calibration)
- Related: ALMA 2014 Long Baseline Campaign
- Related: ALMA Science Verification

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 37,
  "rate": 0.487
 },
 "evidence_ok": true
}
```
