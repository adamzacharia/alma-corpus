# exoALMA. IX. Regularized Maximum Likelihood Imaging of Non-Keplerian Features

`2025ApJ...984L..14Z` | The Astrophysical Journal Letters 2025 | first author: Zawadzki, Brianna | arXiv: 2504.19111 | DOI: 10.3847/2041-8213/adc434

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: protoplanetary_disks
- Question: Do regularized maximum likelihood (RML) images made with MPoL independently reproduce the non-Keplerian features (NKFs) seen in the fiducial CLEAN exoALMA images, and how should RML hyperparameters be chosen (cross-validation) for velocity-resolved multi-channel data?  
  > "Crucially, in the context of exoALMA, RML images serve as an independent verification of marginal features seen in the fiducial CLEAN images." (abstract); "best practices for synthesizing RML images of multi-channeled (i.e. velocity-resolved) data remain undefined" (abstract)
- Target **AA Tau**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **HD 135344B**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **J1604**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **J1615**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **J1842**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **LkCa 15**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **SY Cha**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2021.1.01123.L
- bands: _not stated_
- frequencies and spectral setup: spectral resolution up to 30.5 kHz (26 m/s); CLEAN and RML cubes here use 100 m/s channels (CS J=7-6 fiducial CLEAN set has 200 m/s)  
  > "at moderate angular (maximum baselines up to 3697 m) and high spectral (up to 30.5 kHz, 26 m/s) resolution" (Source Selection and Data Processing); "but with a finer channel spacing than the CS J=7-6 fiducial set of images (which has 200 m/s spacings)" (Source Selection and Data Processing)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: maximum baselines up to 3697 m  
  > "at moderate angular (maximum baselines up to 3697 m) and high spectral (up to 30.5 kHz, 26 m/s) resolution" (Source Selection and Data Processing)
- angular resolution: fiducial CLEAN beam 0.15''; highest-resolution data about 0.06''  
  > "We thus generate two sets of beam-convolved RML cubes: one with a circular 0.15$''$ convolution kernel (equivalent to the fiducial CLEAN beam)" (5.1 Resolution and Noise of RML Images); "Given that the highest resolution data from the interferometer corresponds to resolutions of about 0.06$''$" (Limitations and Future Work)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Cycle 8 ALMA large program exoALMA (2021.1.01123.L)  
  > "The Cycle 8 ALMA large program exoALMA has observed 15 protoplanetary disks" (Introduction)
- Line: 12CO J=3-2 (not stated)
- Line: 13CO J=3-2 (not stated)
- Line: CS J=7-6 (not stated)
- External data: Fiducial exoALMA calibration and CLEAN image cubes (100 m/s channels, 0.15'' beams) used for comparison  
  > "The full data calibration and CLEAN imaging procedures are detailed in (cite: Loomis_exoALMA)." (Source Selection and Data Processing) [from (cite: Loomis_exoALMA); (cite: Teague_exoALMA)]
- External data: Embedded-planet interpretation and planet masses of the NKFs (e.g. 2 M_Jup AA Tau, J1615, LkCa 15; 1 M_Jup J1842; 5 M_Jup SY Cha) and source selection of NKFs  
  > "These are the same five sources for which (cite: Pinte_exoALMA) find evidence of embedded protoplanets and place constraints on the planet masses." (Introduction) [from (cite: Pinte_exoALMA)]
- External data: CLEAN-cube emission surfaces and radial temperature profiles used as the comparison for RML  
  > "We compared the non-parametric emission surfaces and radial temperature profiles, presented in full in (cite: Galloway_exoALMA), between the CLEAN cubes and the RML cubes." (5.2 Emission Surfaces and Temperatures) [from (cite: Galloway_exoALMA)]

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

- task: CASA cvel2 to LSRK frame, then MPoL RML imaging (not tclean) on gridded visibilities  
  > "using the `CASA cvel2` task such that the data were in an LSRK reference frame." (Source Selection and Data Processing); "We use the RML imaging package `MPoL` for all imaging (cite: mpol_2023; Zawadzki_2023; mpol_2025)." (Source Selection and Data Processing)
- deconvolver: _not stated_
- weighting robust: visibilities averaged onto a Fourier grid, equivalent to uniform weighting (no robust value)  
  > "averaged the ungridded visibility data to grid cells in the visibility domain before imaging (equivalent to uniform weighting)" (Source Selection and Data Processing)
- uv taper: _not stated_
- cell size: 0.0125'' per pixel (half the fiducial CLEAN pixel)  
  > "the pixel size of 0.0125$''$ used in this study" (Limitations and Future Work)
- image size: 1024 x 1024 pixels  
  > "in this study, all RML images are $1024 \times 1024$ pixels" (Source Selection and Data Processing)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: both continuum-subtracted and non-continuum-subtracted cubes imaged; subtraction method not stated  
  > "we generated continuum-subtracted and non-continuum-subtracted RML image cubes of the" (4 Results)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: RML cubes released native (no restoring beam), convolved with 0.05'' and with 0.15'' circular kernels  
  > "We thus generate two sets of beam-convolved RML cubes" (5.1 Resolution and Noise of RML Images); "Different versions will be released with the native RML resolution (no beam convolution)" (Conclusions)
- final beam: _not stated_
- final rms: AA Tau 12CO channel signal-free region: 0.043 mJy/beam (0.15'' RML) vs 3.953 mJy/beam (0.15'' CLEAN)  
  > "(0.043 mJy/beam and 3.953 mJy/beam, respectively)" (5.1 Resolution and Noise of RML Images)

### Inherited from earlier work

- Calibration and fiducial CLEAN imaging of the exoALMA data  
  > "The full data calibration and CLEAN imaging procedures are detailed in (cite: Loomis_exoALMA)." (Source Selection and Data Processing) [from (cite: Loomis_exoALMA)]
- Basic RML loss function: entropy + sparsity + TSV regularizers  
  > "we adopt the same basic loss function as in (cite: Zawadzki_2023), using a combination of entropy, sparsity, and total squared variation (cite: Kuramochi_2018) regularization." (3 RML Techniques for Image Cubes) [from (cite: Zawadzki_2023); (cite: Kuramochi_2018)]
- RML imaging workflow (random cell cross-validation procedure) adapted for multi-channel data; the citation is blank in the paper text  
  > "we followed the RML workflow laid out in , except adapted for working with multi-channeled data:" (3.2 Cross-Validation for Multi-Channeled Data) [from blank citation in the converted text]
- Emission-surface extraction procedure with disksurf  
  > "We follow identical procedures to those outlined in Section 3 of (cite: Galloway_exoALMA) to obtain the RML emission surfaces." (5.2 Emission Surfaces and Temperatures) [from (cite: Galloway_exoALMA) Section 3]
- Radial temperature profile derivation from disksurf r-z points  
  > "For further details, see Section 4 of (cite: Galloway_exoALMA)." (5.2 Emission Surfaces and Temperatures) [from (cite: Galloway_exoALMA) Section 4]

### Not stated but needed to reproduce (our reading)

- Optimizer, learning rate, number of iterations, initial image and convergence criterion for the MPoL minimization
- How the per-visibility sigma_i (weights) were derived/rescaled for the likelihood
- Random seed and partition realization for the K=10 CV folds
- Total CLEAN-image flux per source used as the entropy normalization zeta
- Continuum subtraction method and line-free channels used to make the continuum-subtracted measurement sets
- Access path/version of the exoALMA calibrated measurement sets and any self-calibration applied (in Loomis et al.)
- cvel2 parameters (start, width, nchan) and the exact MPoL version/commit
- Implementation of the restoring-beam convolution and of the signal-free region used for RMS
- Disk geometry (inclination, PA, distance, stellar mass) used by disksurf for each source (in Galloway et al.)

## Analysis recipe

1. **Prepare calibrated visibilities**: Transform each calibrated measurement set to LSRK with CASA cvel2 and regrid to 0.1 km/s channels to match the fiducial CLEAN cubes  
  > "using the `CASA cvel2` task such that the data were in an LSRK reference frame." (Source Selection and Data Processing); "we regridded the data to enable a direct comparison to the fiducial CLEAN images" (Source Selection and Data Processing)
   - software: CASA
   - parameter: channel width 0.1 km/s  
  > "The data were regridded to a channel width of $0.1$ km/s" (Source Selection and Data Processing)
   - fitting: _not stated_
   - validation: _not stated_
2. **Export and grid visibilities**: Export regridded measurement sets as complex visibility arrays for MPoL; average ungridded visibilities onto a 1024x1024 Fourier grid by weighted average  
  > "We then defined a corresponding $1024 \times 1024$ Fourier grid and averaged the ungridded visibility data to the Fourier cells using a simple weighted average." (Source Selection and Data Processing)
   - software: MPoL
   - parameter: pixel size 0.0125'', 1024x1024 image  
  > "the pixel size of 0.0125$''$ used in this study" (Limitations and Future Work)
   - fitting: _not stated_
   - validation: Verified that gridding does not introduce interpolation artifacts at the data SNR  
  > "We have verified that this gridding procedure does not introduce interpolation artifacts to the images at the SNR of the data." (Source Selection and Data Processing)
3. **Choose regularizer hyperparameters by cross-validation**: Random-cell 10-fold CV on one representative channel of the continuum-subtracted 12CO J=3-2 data per source; choose the lambda set minimizing the CV score  
  > "We performed 10-fold CV on the continuum-subtracted" (3.2 Cross-Validation for Multi-Channeled Data); "For each source, we selected a single channel to use for CV by examining the fiducial continuum-subtracted" (3.2 Cross-Validation for Multi-Channeled Data)
   - software: MPoL
   - parameter: lambda_ent grid [0, 8e-8, 2e-7, 8e-7, 2e-6, 8e-6, 2e-5]  
  > "[0, 8e-8, 2e-7, 8e-7, 2e-6, 8e-6, 2e-5" (Table 1)
   - parameter: lambda_TSV grid [5e-5, 1e-4, 5e-4, 1e-3, 5e-3, 1e-2]  
  > "[5e-5, 1e-4, 5e-4, 1e-3, 5e-3, 1e-2" (Table 1)
   - parameter: lambda_spa grid [5e-6, 1e-5, 5e-5]  
  > "[5e-6, 1e-5, 5e-5" (Table 1)
   - parameter: K = 10 folds  
  > "We use $K=10$, which has been shown to effectively balance bias and variance in the parameter error estimates" (3.2 Cross-Validation for Multi-Channeled Data)
   - assumption: Grid cells with the highest 1% of gridded weights are included in every subset  
  > "drawing cells without replacement with the minor exception that grid cells with the highest 1% of gridded weight values are included in each subset in order to avoid numerical instabilities that delay or prevent convergence." (3.2 Cross-Validation for Multi-Channeled Data)
   - assumption: Hyperparameters from one channel apply to the whole cube; hand tuning after CV not done  
  > "we do not take this optional tuning step and use strictly the hyperparameter values which minimized the CV score for each source." (3.2 Cross-Validation for Multi-Channeled Data)
   - fitting: CV score is the summed chi^2 of held-out cells against the model fit to training cells  
  > "This model is then compared to the withheld testing data to quantify the predictive power of the RML model and obtain a CV score" (3.2 Cross-Validation for Multi-Channeled Data)
   - validation: Tested on LkCa 15 across 12CO, 13CO, CS, with and without continuum subtraction and 5 channels: optimal values nearly constant across cube  
  > "The optimal hyperparameter values tended to remain nearly constant throughout a given image cube, with only slight variations from channel to channel or no variation at all." (3.2 Cross-Validation for Multi-Channeled Data)
4. **Synthesize RML image cubes**: Apply the CV-optimal hyperparameters to the loss function for every channel and image continuum-subtracted and non-continuum-subtracted 12CO, 13CO and CS cubes  
  > "We applied the hyperparameter values that minimized the CV score at this channel to our loss function" (3.2 Cross-Validation for Multi-Channeled Data)
   - software: MPoL, PyTorch
   - parameter: Per-source lambda_ent, lambda_TSV, lambda_spa from Table 2 (see results_numeric)  
  > "AA Tau | $v=7.9$ | 0 | 5e-5 | 1e-5" (Table 2)
   - assumption: Gaussian, uncorrelated noise across baselines; entropy normalization zeta set to the total flux of the CLEAN image  
  > "Assuming that the noise is normally distributed with standard deviation $\sigma$ and is uncorrelated across baselines" (3 RML Techniques for Image Cubes); "Here, $\zeta$ is a normalization factor which we set equal to the total flux of the CLEAN image." (3.1 The Loss Function)
   - fitting: Optimization: minimize negative log likelihood plus entropy, sparsity (L1) and TSV regularizer penalties  
  > "RML imaging is an optimization-based imaging framework; the image is obtained by maximizing a likelihood function subject to regularizer penalties." (Introduction)
   - validation: Compared to fiducial CLEAN images channel by channel and in zoomed NKF views  
  > "Each source is summarized with a figure comparing the RML and CLEAN images" (4 Results)
5. **Convolve and compare resolution and noise**: Produce native, 0.05'' and 0.15'' convolved RML cubes and compare with 0.15'' CLEAN; measure RMS in a signal-free region  
  > "Taking the extra step to convolve RML images with a restoring beam is a straightforward way to place a firm resolution limit on the image." (5.1 Resolution and Noise of RML Images); "We thus generate two sets of beam-convolved RML cubes" (5.1 Resolution and Noise of RML Images)
   - software: MPoL
   - parameter: kernels 0.15'' and 0.05'' (circular)  
  > "We thus generate two sets of beam-convolved RML cubes: one with a circular 0.15$''$ convolution kernel (equivalent to the fiducial CLEAN beam)" (5.1 Resolution and Noise of RML Images)
   - assumption: True resolution of a convolved cube estimated by adding native RML resolution and kernel in quadrature; stated resolutions are lower limits  
  > "the stated resolutions of our beam-convolved RML image cubes are lower limits on the true resolutions of the images." (5.1 Resolution and Noise of RML Images)
   - fitting: _not stated_
   - validation: No ground-truth image, so optimal restoring beam cannot be identified  
  > "without a “true” image it is not possible to firmly identify an optimal restoring beam size." (5.1 Resolution and Noise of RML Images)
6. **Compare emission surfaces and temperatures with CLEAN**: Run disksurf on 0.15'', 100 m/s non-continuum-subtracted RML cubes of AA Tau, J1615, J1842, LkCa 15, SY Cha to get r-z surfaces and brightness temperature profiles; compare with CLEAN-cube results  
  > "To compare the two, we used RML cubes of the same spatial and spectral resolution as those used for the CLEAN cube analysis" (5.2 Emission Surfaces and Temperatures); "We obtain the temperature as a function of radius using the $r-z$ points extracted by `disksurf`." (5.2 Emission Surfaces and Temperatures)
   - software: disksurf
   - parameter: five iterations, minimum SNR raised from 1.0 to 5.0 (12CO) and 1.0 to 3.5 (13CO); minimal masking  
  > "we do this process over five iterations, each time increasing the minimum signal to noise from 1.0 to 5.0 for" (5.2 Emission Surfaces and Temperatures); "Minimal masking is applied to the surfaces so that we can assess the differences between CLEAN and RML." (5.2 Emission Surfaces and Temperatures)
   - assumption: Non-continuum-subtracted cubes used so temperature is not underestimated  
  > "We use the non-continuum-subtracted cubes as to not underestimate the temperature." (5.2 Emission Surfaces and Temperatures)
   - fitting: _not stated_
   - validation: Tested temperature sensitivity to beam size by deriving profiles from RML cubes of SY Cha and AA Tau convolved with several kernels  
  > "To test this, we derived the temperatures using RML cubes of SY Cha and AA Tau convolved with multiple beam sizes" (5.2 Emission Surfaces and Temperatures)

## Software

- **MPoL** : RML imaging of all cubes, cross-validation  
  > "We use the RML imaging package `MPoL` for all imaging (cite: mpol_2023; Zawadzki_2023; mpol_2025)." (Source Selection and Data Processing)
- **CASA** : cvel2 reference-frame transformation and regridding; tclean used for the fiducial CLEAN images  
  > "using the `CASA cvel2` task such that the data were in an LSRK reference frame." (Source Selection and Data Processing)
- **tclean** : fiducial CLEAN comparison images  
  > "The fiducial exoALMA images were made with CLEAN, as described in (cite: Teague_exoALMA; Loomis_exoALMA)." (Introduction)
- **disksurf** : emission-surface extraction from RML cubes  
  > "We utilize the open-source Python package `disksurf`, which obtains emission surfaces via the method first demonstrated in (cite: pinte_IMLup_2018A&A...609A..47P)." (5.2 Emission Surfaces and Temperatures)
- **PyTorch** : _not stated_
- **Astropy** : _not stated_
- **GPUVMEM** : Earlier GPU RML package for ALMA disks, named as prior work (not used here)  
  > "introduced the `GPUVMEM` package which enabled GPU-accelerated RML imaging with a focus on ALMA protoplanetary disk imaging" (Introduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| AA Tau CV-optimal (lambda_ent, lambda_TSV, lambda_spa), CV channel v=7.9 km/s | 0, 5e-5, 1e-5 | not stated | dimensionless | 3 | AA Tau / $v=7.9$ / 0 / 5e-5 / 1e-5 |
| HD 135344B CV-optimal (lambda_ent, lambda_TSV, lambda_spa), CV channel v=6.6 km/s | 0, 5e-5, 5e-5 | not stated | dimensionless | 3 | HD 135344B / $v=6.6$ / 0 / 5e-5 / 5e-5 |
| J1604 CV-optimal (lambda_ent, lambda_TSV, lambda_spa), CV channel v=4.5 km/s | 0, 1e-4, 5e-5 | not stated | dimensionless | 3 | J1604 / $v=4.5$ / 0 / 1e-4 / 5e-5 |
| J1615 CV-optimal (lambda_ent, lambda_TSV, lambda_spa), CV channel v=3.7 km/s | 8e-6, 5e-4, 5e-5 | not stated | dimensionless | 3 | J1615 / $v=3.7$ / 8e-6 / 5e-4 / 5e-5 |
| J1842 CV-optimal (lambda_ent, lambda_TSV, lambda_spa), CV channel v=5.1 km/s | 8e-6, 5e-5, 5e-5 | not stated | dimensionless | 3 | J1842 / $v=5.1$ / 8e-6 / 5e-5 / 5e-5 |
| LkCa 15 CV-optimal (lambda_ent, lambda_TSV, lambda_spa), CV channel v=6.9 km/s | 0, 5e-4, 1e-5 | not stated | dimensionless | 3 | LkCa 15 / $v=6.9$ / 0 / 5e-4 / 1e-5 |
| SY Cha CV-optimal (lambda_ent, lambda_TSV, lambda_spa), CV channel v=3.6 km/s | 0, 5e-4, 1e-5 | not stated | dimensionless | 3 | SY Cha / $v=3.6$ / 0 / 5e-4 / 1e-5 |
| Time for one CV hyperparameter combination | about 30 minutes on an NVIDIA P100 GPU | not stated | minutes | 3 | A typical CV procedure for one combination of hyperparameters can take $30$ minutes on a NVIDIA P100 GPU |
| Signal-free RMS, AA Tau 12CO channel: 0.15'' RML vs 0.15'' CLEAN | 0.043 (RML) and 3.953 (CLEAN) | not stated | mJy/beam | 5 | (0.043 mJy/beam and 3.953 mJy/beam, respectively) |
| Mean 12CO temperature offset RML minus CLEAN (RML lower), maximum in SY Cha inner radii | about 3 (mean), up to 13 | not stated | K | 6 | but in some places it becomes as large as 13 K, such as in the inner radial regions of SY Cha. |
| Mean 13CO temperature offset, J1615 | 1.3 | not stated | K | 6 | For J1615 in $^{13}$CO J=3-2, the temperature difference, on average, is only 1.3 K. |
| Mean 13CO temperature offset, SY Cha | 8 | not stated | K | 6 | exhibits the largest temperature difference between the CLEAN and RML cubes, with the average offset being 8 K. |
| Radial extent of RML emission surfaces beyond CLEAN surfaces (SY Cha 12CO and 13CO) | over 200 | not stated | au | 6 | whose RML surface extends over 200 au further than that found using the CLEAN cube for both molecules. |

## Qualitative findings

- RML images reproduce all features of the CLEAN images for all seven disks, including the NKFs; RML is sharper for AA Tau, HD 135344B, J1842 but slightly more blurred for J1615 and SY Cha  
  > "The RML images of AA Tau appear sharper than the corresponding CLEAN images." (AA Tau); "While the RML images appear slightly more blurred than the CLEAN images for this target, the NKF remains visible in multiple channels." (J1615)
- Entropy regularization switched off (lambda_ent = 0) for five of seven disks; only J1615 and J1842 favor lambda_ent = 8e-6  
  > "The two remaining disks, J1615 and J1842, favor a modest degree of entropy regularization" (3.2 Cross-Validation for Multi-Channeled Data)
- Sparsity regularization strongly suppresses background noise in RML images, so RML RMS is not comparable to CLEAN thermal noise  
  > "This does not mean that the overall noise in the RML images is truly orders of magnitude better than the corresponding CLEAN products." (5.1 Resolution and Noise of RML Images)

## Claim tuples

- H: RML imaging independently reproduces the NKFs seen in the 12CO J=3-2 CLEAN images | E: MPoL RML cubes of 7 exoALMA disks compared channel by channel with fiducial CLEAN cubes | R: All features including the NKFs appear in the RML images of all 7 disks | F: NKFs are robust features rather than imaging artifacts | **supported**
- H: CV hyperparameters from one channel can be applied to a full cube and across lines and continuum subtraction | E: 30 CV tests on LkCa 15 across three lines, with and without continuum subtraction, in 5 channels each | R: Optimal lambdas nearly constant across channels, lines and continuum subtraction, with minor variations that did not change morphology | F: CV on a single representative channel suffices per source, cutting the computational cost; CV is still recommended once per source | **supported**
- H: RML cubes give the same emission surfaces and temperature profiles as CLEAN cubes | E: disksurf applied to RML cubes of five disks and compared with CLEAN-cube results | R: Surface morphology consistent but RML surfaces extend farther (sometimes 200 au); RML temperatures systematically lower (about 5 K, varying by radius and disk) | F: Broad agreement with offsets likely tied to the lower RML noise and sparsity regularization, needing further study | **partially**
- H: RML imaging improves resolution beyond the CLEAN beam | E: Native and 0.05'' and 0.15'' convolved RML cubes compared with 0.15'' CLEAN, with uniform CV-only hyperparameters | R: No clear resolution improvement in all images | F: Super-resolution would need source-specific tuning not done for this uniform sample | **partially**

## Reasoning

- Why this data: Seven disks chosen because they show prominent NKFs in 12CO CLEAN images; five from a visual search for kinks plus two with large-scale arcs  
  > "The source selection was motivated by a preliminary visual search for kink-like substructures caused by planets, resulting in an initial sample of five disks" (Introduction)
- Why this method: Multiple imaging techniques recommended for kinematic planet detection; RML gives an independent check on CLEAN  
  > "Thus, recent recommendations for kinematically detecting planets strongly suggest using multiple image synthesis techniques to image the data" (Introduction)
- Alternative: Hand-tuning hyperparameters after CV rejected because it introduces human bias  
  > "deviating from the set of hyperparameters which minimize the CV score introduces human bias" (3.2 Cross-Validation for Multi-Channeled Data)
- Alternative: Per-channel CV not adopted because CV is the most computationally expensive part  
  > "The CV process is by far the most computationally expensive component of RML imaging" (3.2 Cross-Validation for Multi-Channeled Data)
- How they decided it was enough: Hyperparameters fixed strictly at the CV minimum, without hand tuning, to treat all disks uniformly  
  > "we do not take this optional tuning step and use strictly the hyperparameter values which minimized the CV score for each source." (3.2 Cross-Validation for Multi-Channeled Data)
- Limitation (authors): Simple CV may be less effective for non-uniform uv coverage or low SNR; repeated partitioning suggested  
  > "also means that the simple CV procedure used here may not be as effective for observations with less uniform" (3.2 Cross-Validation for Multi-Channeled Data)
- Limitation (authors): Resolution of RML images is hard to define; stated convolved resolutions are lower limits  
  > "the spatial resolution of RML images can be difficult to define precisely" (5.1 Resolution and Noise of RML Images)
- Limitation (authors): Reasons for emission-surface and temperature differences between CLEAN and RML are unclear  
  > "The reasons for these morphological differences are unclear." (5.2 Emission Surfaces and Temperatures)
- Caveat (inferred, ours): Hyperparameter-stability claim rests on CV tests of one source (LkCa 15) only
- Caveat (inferred, ours): No injection-recovery or simulated-NKF test, so detection reliability of RML vs CLEAN is not quantified
- Caveat (inferred, ours): CLEAN and RML share the same calibrated visibilities, so calibration artifacts are not tested
- Caveat (inferred, ours): Single random CV partition per source; entropy normalization uses the CLEAN flux
- Caveat (inferred, ours): NKF agreement is judged by eye, with no quantitative metric

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: RML cubes (12CO, 13CO, CS; with and without continuum subtraction; native, 0.05'' and 0.15'' versions) stated to be publicly released; location not stated  
  > "For each target, the following data products will be publicly available:" (Conclusions)
- Code: Sample MPoL imaging scripts released on the MPoL GitHub (examples repository)  
  > "We have also released sample imaging scripts, available directly on the `MPoL` GitHub" (Conclusions)
- Missing: Optimizer settings, iteration counts and initialization for MPoL
- Missing: Per-source CLEAN total flux (zeta) and visibility weight treatment
- Missing: Continuum subtraction and calibration details (deferred to Loomis et al.)
- Missing: Disk geometry inputs for disksurf (deferred to Galloway et al.)
- Missing: Exact MPoL version and random seeds for CV partitions
- Data volume (inferred): Likely several hundred GB to a few TB of calibrated measurement sets for 7 disks and 3 lines, plus tens of GPU-hours per source for CV
- Score (inferred): 3/5, Loss function, regularizers, grid size, K, hyperparameter grids and per-source optima are all given and sample scripts exist, but optimizer settings, weights, calibrated-data access and calibration details are missing or deferred.
- Rediscovery candidate: no, Main results are mostly qualitative (feature recovery) and the recipe lacks optimizer and calibration details; data access is not stated in this paper.

## Links

- Method: Zawadzki et al. 2023 (cite: Zawadzki_2023) (RML method and loss function adopted here)
- Method: (cite: mpol_2025) (MPoL software reference)
- Method: (cite: Loomis_exoALMA) (exoALMA calibration and CLEAN imaging)
- Method: (cite: Galloway_exoALMA) (emission surface and temperature procedures)
- Companion: (cite: Teague_exoALMA) (exoALMA program overview)
- Companion: (cite: Pinte_exoALMA) (NKF analysis and planet mass constraints)
- Companion: (cite: Galloway_exoALMA) (CLEAN emission surfaces and temperatures for comparison)
- Related: exoALMA (ALMA large program 2021.1.01123.L)
- Related: MPoL
- Related: GPUVMEM

## Checks

```json
{
 "quotes": 100,
 "quotes_ok": 100,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 117,
  "stated": 65,
  "rate": 0.556
 },
 "evidence_ok": true
}
```
