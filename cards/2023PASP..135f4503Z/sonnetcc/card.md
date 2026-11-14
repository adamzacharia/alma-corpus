# Regularized Maximum Likelihood Image Synthesis and Validation for ALMA Continuum Observations of Protoplanetary Disks

`2023PASP..135f4503Z` | Publications of the Astronomical Society of the Pacific 2023 | first author: Zawadzki, Brianna | arXiv: 2209.11813 | DOI: 10.1088/1538-3873/acdf84

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, instrumentation
- Question: Which RML regularizers and cross-validation procedures give the best images of ALMA continuum protoplanetary disk data, and how does RML (MPoL) compare with CLEAN in resolution and sensitivity  
  > "there has not yet been a systematic exploration to test the imaging outcomes of various regularizers on ALMA protoplanetary disk observations" (Introduction); "We provide general recommendations for building an RML workflow for image synthesis of ALMA protoplanetary disk observations, including effective use of CV." (abstract)
- Target **HD 143006**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **ALMA logo (mock dataset)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **Synthetic protoplanetary disk (from Pinte et al. 2016 simulation)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00484.L
- bands: Band 6 (HD 143006, DSHARP)  
  > "The second dataset in this study is a real Band 6 ALMA dataset containing the observations of the protoplanetary disk hosted by HD 143006" (Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-7 (alma.cycle7.7.cfg) for the simulated ALMA logo dataset only  
  > "with the C43-7 reference ALMA configuration from simobserve (`alma.cycle7.7.cfg`), to “observe” the source as it transits zenith for 1 hour under median atmospheric conditions." (Data)
- baselines: _not stated_
- angular resolution: 45 mas (HD 143006 DSHARP data)  
  > "obtained by the DSHARP survey (cite: Andrews_2018) at a resolution of 45 mas." (Data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 1 hour (simulated ALMA logo dataset only)  
  > "to “observe” the source as it transits zenith for 1 hour under median atmospheric conditions." (Data)
- observing dates: _not stated_
- pi or archival as stated: DSHARP survey archival observations, calibrated visibilities from the DSHARP archive  
  > "The full listing of archival observations can be found in (cite: Andrews_2018)" (Data); "the calibrated visibilities can be downloaded from the DSHARP archive" (Data)
- Other facility **DSHARP survey (ALMA large program)**: Calibrated Band 6 continuum visibilities and the fiducial CLEAN image of HD 143006  
  > "obtained by the DSHARP survey (cite: Andrews_2018) at a resolution of 45 mas." (Data); "We also provide a comparison to the CLEAN image synthesized by the DSHARP team (cite: Andrews_2018)." (Results)
- Other facility **Pinte et al. 2016 disk simulation**: Model image used to build the synthetic ground-truth dataset  
  > "The third dataset is a synthetic ALMA dataset we generated from a protoplanetary disk simulation described in (cite: Pinte_2016)." (Data)
- External data: DSHARP calibrated visibilities of HD 143006 (calibration by the DSHARP team)  
  > "The visibilities were originally calibrated by the DSHARP team following the standardized CASA procedures described in (cite: Andrews_2018)." (Data) [from Andrews et al. 2018 (cite: Andrews_2018)]
- External data: Total flux of HD 143006 (59 mJy) used to scale the synthetic image  
  > "we scaled the total flux of the image to 59 mJy, matching the total flux of HD 143006 (cite: Andrews_2018)." (Data) [from Andrews et al. 2018 (cite: Andrews_2018)]
- External data: Protoplanetary disk simulation image used as ground truth  
  > "The third dataset is a synthetic ALMA dataset we generated from a protoplanetary disk simulation described in (cite: Pinte_2016)." (Data) [from Pinte et al. 2016 (cite: Pinte_2016)]
- External data: DSHARP fiducial CLEAN image of HD 143006 used as comparison  
  > "We found that RML methods successfully recover all features that appear in the fiducial CLEAN image of HD 143006 synthesized by the DSHARP team (cite: Andrews_2018)" (Results) [from Andrews et al. 2018 (cite: Andrews_2018)]
- Simulation/model as data: Mock ALMA logo dataset made with CASA simobserve (C43-7, 1 hour)  
  > "The first is a small, mock dataset created from the ALMA logo" (Data)
- Simulation/model as data: Synthetic disk dataset: Pinte et al. 2016 simulation image, 512 x 512 pixels of 0.01 arcsec, 59 mJy, DSHARP HD 143006 (u,v) sampling, Gaussian noise from the weights, visibilities from the MPoL NuFFT routine  
  > "We scaled the simulated image to $512 \times 512$ pixels, with each pixel measuring 0.01 arcsec across" (Data); "We used the same $(u,v)$ sampling of the DSHARP observations of HD 143006." (Data)

## Processing

### Calibration

- pipeline or manual: Calibrated by the DSHARP team with standardized CASA procedures (Andrews et al. 2018)  
  > "The visibilities were originally calibrated by the DSHARP team following the standardized CASA procedures described in (cite: Andrews_2018)." (Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: DSHARP-calibrated visibilities used with one extra step: empirical per-spectral-window rescaling of the weights  
  > "We performed one additional step of calibration beyond that of the DSHARP team." (Data); "Each spectral window was corrected individually by multiplying $\sigma$ by a scale factor for that spectral window" (Data)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: MPoL RML images start from uniformly weighted gridded visibilities; residual dirty images use Briggs weighting, robust = 0.0  
  > "RML images in `MPoL` always begin with uniformly weighted visibilities" (Data); "imaged from the residual visibilities using the `DirtyImager` with Briggs weighting (robust = 0.0)" (Results)
- uv taper: _not stated_
- cell size: 0.01 arcsec per pixel (synthetic disk image)  
  > "with each pixel measuring 0.01 arcsec across" (Data)
- image size: 512 x 512 pixels (synthetic disk image)  
  > "We scaled the simulated image to $512 \times 512$ pixels" (Data)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Optional circular Gaussian restoring beams applied in the image plane with astropy.convolution  
  > "We used `astropy.convolution` to convolve the model with circular Gaussians directly in the image plane." (Determining Image Resolution with RML)
- final beam: No restoring beam for the base RML image; test beams of 11.5, 15.3, 23.0, 46.0 and 69.0 mas (1/4, 1/3, 1/2, 1, 3/2 of the DSHARP tclean synthesized beam)  
  > "restoring beams equal to 1/4, 1/3, 1/2, 1, and 3/2 times the synthesized beam size of the DSHARP continuum `tclean` image of HD 143006 (11.5, 15.3, 23.0, 46.0, and 69.0 mas, respectively)" (Determining Image Resolution with RML)
- final rms: _not stated_

### Inherited from earlier work

- HD 143006 calibration and the full list of archival observations  
  > "The full listing of archival observations can be found in (cite: Andrews_2018)" (Data) [from Andrews et al. 2018 (cite: Andrews_2018)]
- Full data-processing steps for the datasets  
  > "A full accounting of the data processing steps are available on the `mpoldatasets` repository" (Data) [from mpoldatasets repository (github.com/MPoL-dev/mpoldatasets)]
- Walkthrough of the weight rescaling process  
  > "A walkthrough of this rescaling process is described as part of the `MPoL` documentation" (Data) [from MPoL documentation and mpoldatasets repository]
- Definition of the maximum entropy loss  
  > "We follow the definition in (cite: EHTCollab_2019) and define maximum entropy loss as" (Regularizers) [from (cite: EHTCollab_2019)]
- Definition of the TV loss  
  > "Following (cite: Rudin_1992), we define the TV loss as" (Regularizers) [from (cite: Rudin_1992)]
- Choice of K=10 for K-fold cross-validation  
  > "the standard $K=10$ has been used with success for such applications (cite: Akiyama_2017a; Akiyama_2017b; Yamaguchi_2020)" (Best Practices for Image Validation) [from (cite: Akiyama_2017a; Akiyama_2017b; Yamaguchi_2020)]

### Not stated but needed to reproduce (our reading)

- Number of spectral windows and execution blocks of the HD 143006 data and the per-spw scale factors
- Image size and pixel size used for the HD 143006 RML images
- Optimizer, learning rate and number of iterations for the full-data HD 143006 images
- Lambda values of the entropy and sparsity terms in the final combined HD 143006 image (only lambda_TSV is given)
- TV softening parameter epsilon
- The lambda grids used for the cross-validation runs and the CV score values
- Number of dartboard radial and azimuthal bins and the random seeds for the partitioning
- MPoL version used (only a citation is given)
- How the quoted resolution gain of up to a factor of 3 (abstract) or 2-3 (conclusion) was measured
- CASA task parameters of the DSHARP tclean image used for comparison
- HD 143006 coordinates and distance

## Analysis recipe

1. **Rescale visibility weights of the DSHARP HD 143006 data**: Build a tclean model, subtract it from the visibilities, and compare the scatter of the residuals with the Gaussian envelope expected from the thermal weights; multiply sigma by a per-spectral-window scale factor  
  > "We found empirical weight scalings for each dataset by creating a `tclean` model, subtracting it from the visibilities, and examining the scatter in the visibility residuals compared to the Gaussian envelope expected from the thermal weights ($w=\sigma^{-2}$)." (Data)
   - software: CASA tclean, MPoL, visread
   - parameter: Scale factors per spectral window: minimum 1.46, maximum 1.91, average 1.75  
  > "with a minimum scale factor of 1.46, a maximum of 1.91, and an average of 1.75 over all spectral windows" (Data)
   - assumption: Thermal weights w = sigma^-2  
  > "the Gaussian envelope expected from the thermal weights ($w=\sigma^{-2}$)" (Data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Grid the visibilities and make dirty images**: Average ungridded visibilities onto a Fourier grid with as many cells as image pixels (weighted average, equivalent to uniform weighting)  
  > "Before performing any imaging (either creating a dirty image or an RML image), we take the ungridded visibility data and average it to grid cells in the visibility domain." (Data)
   - software: MPoL
   - parameter: RML images always begin with uniformly weighted visibilities  
  > "RML images in `MPoL` always begin with uniformly weighted visibilities" (Data)
   - fitting: _not stated_
   - validation: _not stated_
3. **Forward-model the image with RML in MPoL**: Minimize a loss made of the negative log likelihood (chi^2/2) plus regularizer terms with lambda prefactors, by gradient descent with PyTorch auto-differentiation; pixel values mapped through Softplus for positivity; model initialised from the dirty image or other images  
  > "We use gradient descent methods, which are iterative processes with several components." (Minimizing the Loss Function); "We chose the Softplus function" (Image Positivity)
   - software: MPoL, PyTorch
   - parameter: Entropy reference pixels: uniform, 1e-7 Jy per arcsec^2  
  > "with a positive, uniform set of reference pixels ($\mathbf{I}=10^{-7} \; \rm{Jy \; arcsec}^{-2}$)" (Entropy Performance)
   - parameter: Dirty-image initialisation recommended; converged result insensitive to initial state  
  > "We recommend initializing the model with the dirty image." (Recommendations for RML with ALMA)
   - assumption: Noise uncorrelated across baselines and Gaussian  
  > "the noise is uncorrelated across baselines and follows a normal distribution with standard deviation $\sigma$" (Forward Modeling with RML)
   - fitting: Gradient descent minimization of negative log likelihood plus regularizers (entropy, sparsity, TV, TSV); regularizers act like priors  
  > "In a Bayesian framework, these regularizing terms would be akin to prior probability distributions imposed on various parameters of the model" (Forward Modeling with RML)
   - validation: Check that the loss and gradient have converged  
  > "It is essential to check that the optimization algorithm has converged" (Minimizing the Loss Function)
4. **Explore each regularizer on HD 143006 and the synthetic disk**: Image with each regularizer alone over a range of lambda values and inspect images and residual dirty images  
  > "The images shown were generated using an arbitrarily chosen range of $\lambda$ values in order to show the breadth of images possible with different regularizer tunings." (Results)
   - software: MPoL
   - parameter: Residual visibilities imaged with DirtyImager, Briggs robust = 0.0  
  > "imaged from the residual visibilities using the `DirtyImager` with Briggs weighting (robust = 0.0)" (Results)
   - fitting: _not stated_
   - validation: Qualitative inspection; the simulated disk dataset was checked to show similar behavior  
  > "we verified that the simulated disk dataset exhibits similar behavior" (Results)
5. **Tune lambda hyperparameters with K-fold cross-validation**: K-fold CV with K=10, using random cell or dartboard partitioning of gridded visibilities; CV score is the sum of chi^2 on held-out folds  
  > "In this study, we restricted our exploration of CV to K-fold CV with $K=10$." (Best Practices for Image Validation); "Dartboard partitioning uses polar grid lines to create a new layer of azimuthal and radial bins, each of which contains many visibility grid cells." (Cross-Validation)
   - software: MPoL
   - parameter: 15000 iterations per fold; one CV score took about 11-12 minutes on an NVIDIA Tesla K80 GPU  
  > "computing a single CV score ($K=10$, 15000 iterations each) took around 11-12 minutes on a NVIDIA Tesla K80 GPU" (Recommendations for RML with ALMA)
   - parameter: Random cell partitioning draws grid cells without replacement into K subsets  
  > "Random cell partitioning utilizes $K$ subsets that are composed of randomly-selected visibility grid cells." (Cross-Validation)
   - fitting: _not stated_
   - validation: Each fold must converge, otherwise the CV score is invalid  
  > "If each K-fold does not reach convergence, the final CV score is invalid and the entire CV process must be repeated with enough iterations to ensure full convergence." (Best Practices for Image Validation)
6. **Validate RML against the synthetic ground truth**: Compare RML images tuned by hand, by random cell CV, by dartboard CV, by minimum NRMSE and by minimum summed absolute residual against the true image; compare model and true visibility amplitudes  
  > "We find the minimum residual image for each combination of hyperparameters by summing the absolute value of the difference" (Hyperparameter Tuning); "We also compute the normalized root mean squared error (NRMSE)" (Hyperparameter Tuning)
   - software: MPoL
   - assumption: Synthetic image is the ground truth  
  > "The purpose of this dataset is to compare RML model results with a realistic reference image which we can use as a" (Data)
   - fitting: _not stated_
   - validation: All tuning methods gave similar results and recovered the most prominent rings and gaps but not the smallest scales  
  > "but failed to suppress enough noise to recover features at the smallest spatial scales or with low contrast flux variations." (Hyperparameter Tuning)
7. **Make the combined-regularizer HD 143006 image and compare with CLEAN**: Combine entropy, sparsity and TSV; start from random cell CV and raise lambda_TSV by hand; compare with the DSHARP CLEAN image  
  > "We combined entropy, sparsity, and TSV regularization to generate an image of HD 143006" (Hyperparameter Tuning); "To tune the hyperparameters, we used random cell CV to identify a starting point, then adjusted $\lambda_{\rm{TSV}}$ by hand to introduce more smoothing into the model image." (Hyperparameter Tuning)
   - software: MPoL
   - parameter: lambda_TSV raised from 2.15e-4 to 2.15e-3  
  > "We increased the $\lambda_{\rm{TSV}}$ from $2.15 \times 10^{-4}$ to $2.15 \times 10^{-3}$" (Hyperparameter Tuning)
   - fitting: _not stated_
   - validation: All features of the DSHARP CLEAN image are recovered, with less background noise and better resolution  
  > "We found that RML methods successfully recover all features that appear in the fiducial CLEAN image of HD 143006 synthesized by the DSHARP team (cite: Andrews_2018)" (Hyperparameter Tuning)
8. **Characterize resolution and test restoring beams**: Convolve RML images with circular Gaussian restoring beams of various sizes and find the NRMSE-minimizing beam on the synthetic dataset  
  > "We used `astropy.convolution` to convolve the model with circular Gaussians directly in the image plane." (Determining Image Resolution with RML)
   - software: astropy
   - parameter: Beams of 1/4, 1/3, 1/2, 1 and 3/2 times the DSHARP tclean beam (11.5 to 69.0 mas); NRMSE-minimizing beam FWHM = 24.0 mas  
  > "Because the NRMSE at a relatively small beam size (FWHM = 24.0 mas)" (Determining Image Resolution with RML)
   - fitting: _not stated_
   - validation: No spurious high-frequency features seen in the base RML image  
  > "In this case, we do not observe spurious high-frequency features in the base RML image" (Determining Image Resolution with RML)

## Software

- **MPoL** : GPU-accelerated RML imaging, dirty images, synthetic data generation and cross-validation  
  > "is an open-source Python package we have designed as a foundation to enable RML imaging for a variety of interferometric workflows." (The MPoL Package)
- **PyTorch** : Tensor arrays and auto-differentiation underlying MPoL  
  > "`MPoL` is built on PyTorch (cite: PyTorch_2019)" (The MPoL Package)
- **CASA simobserve** : Simulating the mock ALMA logo observation  
  > "We then used the CASA task `simobserve` (cite: McMullin_2007)" (Data)
- **CASA tclean** : Model used to derive empirical weight scalings; DSHARP CLEAN comparison  
  > "creating a `tclean` model, subtracting it from the visibilities" (Data)
- **Astropy (astropy.convolution)** : Convolving RML images with circular Gaussian restoring beams  
  > "We used `astropy.convolution` to convolve the model with circular Gaussians directly in the image plane." (Determining Image Resolution with RML)
- **Python Imaging Library** : Scaling the total flux of the synthetic image to 59 mJy  
  > "Using the Python Imaging Library, we scaled the total flux of the image to 59 mJy" (Data)
- **casatools** : Reading visibilities from CASA measurement sets  
  > "Visibilities can be obtained from CASA measurement sets using `casatools`." (Recommendations for RML with ALMA)
- **visread** : Helping to extract visibilities from measurement sets  
  > "Open source software packages like visread" (Recommendations for RML with ALMA)
- **DirtyImager (MPoL)** : Imaging residual visibilities with Briggs weighting  
  > "using the `DirtyImager` with Briggs weighting (robust = 0.0)" (Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Visibility weight scale factor, minimum over spectral windows | 1.46 | not stated | dimensionless | 1 | with a minimum scale factor of 1.46, a maximum of 1.91, and an average of 1.75 over all spectral windows |
| Visibility weight scale factor, maximum over spectral windows | 1.91 | not stated | dimensionless | 1 | with a minimum scale factor of 1.46, a maximum of 1.91, and an average of 1.75 over all spectral windows |
| Visibility weight scale factor, average over spectral windows | 1.75 | not stated | dimensionless | 1 | with a minimum scale factor of 1.46, a maximum of 1.91, and an average of 1.75 over all spectral windows |
| Resolution improvement of RML over CLEAN for HD 143006 (abstract) | up to a factor of 3 | not stated | dimensionless | 7 | finding that RML imaging improved the spatial resolution of the image by up to a factor of $3$ without sacrificing sensitivity |
| Angular resolution improvement over CLEAN (conclusion) | 2-3 | not stated | dimensionless | 7 | With these methods we improved the angular resolution of the images by a factor of $2-3$ compared to CLEAN. |
| Final lambda_TSV, before hand adjustment | 2.15e-4 | not stated | dimensionless | 7 | We increased the $\lambda_{\rm{TSV}}$ from $2.15 \times 10^{-4}$ to $2.15 \times 10^{-3}$ |
| Final lambda_TSV, after hand adjustment | 2.15e-3 | not stated | dimensionless | 7 | We increased the $\lambda_{\rm{TSV}}$ from $2.15 \times 10^{-4}$ to $2.15 \times 10^{-3}$ |
| lambda_TSV minimizing CV score (HD 143006, TSV only, two partition seeds) | 3e-4 and 1e-4 | not stated | dimensionless | 5 | the minimum CV score occurs at $\lambda_{\rm{TSV}} = 10^{-4}$ instead of $\lambda_{\rm{TSV}} = 3 \times 10^{-4}$ |
| NRMSE-minimizing restoring beam FWHM (synthetic disk, random cell CV model) | 24.0 | not stated | mas | 8 | Because the NRMSE at a relatively small beam size (FWHM = 24.0 mas) |
| Mean noise sigma of a non-zero gridded visibility cell (3000 to 5000 klambda) | 2.9e-3 | not stated | Jy | 6 | mean $\sigma = 2.9\times 10^{-3}$ Jy, for baselines |
| Time for one image of HD 143006 on an NVIDIA Tesla K80 GPU | about 10 | not stated | seconds | 3 | generating a single image took about 10 seconds NVIDIA Tesla K80 GPU |

## Qualitative findings

- A combination of entropy, sparsity and TSV works well on HD 143006 and the synthetic disk; TV degrades fine detail  
  > "a combination of entropy, sparsity, and TSV regularization works well, while TV regularization does not adequately retain fine details in the images" (Conclusion)
- Many lambda values give comparably low CV scores, so a coarse grid suffices  
  > "there commonly exists a range of hyperparameters that result in similar images" (Hyperparameter Tuning)
- Over-regularized sparsity can remove diffuse emission and whole rings  
  > "sparsity regularization with a high $\lambda$ value removed some of the more diffuse emission, and in extreme cases removed some rings entirely" (Sparsity Performance)

## Claim tuples

- H: RML imaging with MPoL can improve resolution over CLEAN for ALMA disk continuum data without losing sensitivity | E: Image DSHARP HD 143006 with entropy + sparsity + TSV and compare with the DSHARP CLEAN image | R: RML recovers all CLEAN features with less background noise; resolution gain up to a factor of 3 (2-3 in conclusion) | F: RML improves angular resolution without sacrificing sensitivity | **supported**
- H: Cross-validation can tune regularization strengths efficiently | E: K=10 CV on HD 143006 and the synthetic disk with random cell and dartboard partitioning | R: CV scores are loosely U-shaped with a range of lambda giving comparable scores | F: A coarse grid of lambda values is enough to identify good models | **supported**
- H: Which regularizers work best for disk continuum images | E: Image HD 143006 and the synthetic disk with entropy, sparsity, TV and TSV alone and combined | R: Entropy gives high resolution, sparsity removes background noise, TSV defines rings, TV degrades resolution | F: Entropy + sparsity + TSV is the preferred combination | **supported**
- H: Random cell and dartboard CV partitioning give comparable tuned images relative to hand tuning | E: Compare tuned RML images of the synthetic disk with the ground truth | R: Random cell CV and hand tuning gave the images closest to truth; dartboard was slightly noisier | F: Both partitionings are viable, random cell slightly better | **supported**
- H: RML recovers the true structure of a simulated disk | E: RML imaging of the synthetic dataset compared with the input image in image and visibility space | R: Prominent rings and gaps recovered; smallest scales and low-contrast variations not recovered; long-baseline extrapolation only partial | F: RML recovers main structure but not the finest scales | **partially**
- H: A restoring beam is needed for RML images | E: Convolve RML images with Gaussian beams of 1/4 to 3/2 of the tclean beam | R: No qualitative differences for beams up to 1/2 of the tclean beam | F: A modest restoring beam of 1/3-1/2 nominal resolution is recommended but not required | **supported**

## Reasoning

- Why this data: HD 143006 chosen as a well-studied disk with potential small-scale structure  
  > "We chose this protoplanetary disk because it is well-studied and has potential for structures at small spatial scales, including azimuthal asymmetries." (Data)
- Why this method: Regularizers avoid CLEAN drawbacks by adding information to image synthesis  
  > "Many of the drawbacks encountered with CLEAN can be partially or completely avoided by using an alternative class of imaging techniques which incorporate additional information into the image synthesis routine through the use of regularizers." (Introduction)
- Alternative: TV excluded from the final combined image because it degraded resolution  
  > "but excluded TV because it degraded the resolution of the image." (Hyperparameter Tuning)
- Alternative: Exponential mapping of pixel values rejected in favor of Softplus  
  > "$I_i = \exp(Z_i)$ is another potential mapping function, however, we found the Softplus function hastened model optimization." (Image Positivity)
- How they decided it was enough: Run enough iterations for the loss to converge  
  > "it is essential to use enough iterations so that the loss function fully converges on a solution." (Minimizing the Loss Function)
- Limitation (authors): RML images failed to recover the smallest-scale and low-contrast features of the synthetic disk  
  > "but failed to suppress enough noise to recover features at the smallest spatial scales or with low contrast flux variations." (Hyperparameter Tuning)
- Limitation (authors): RML model only partly extrapolates to long baselines  
  > "The model appears to interpolate well at $(u,v)$ that is already thoroughly sampled by the original data (i.e. $q<4000$), but only partially extrapolates to long baselines." (Hyperparameter Tuning)
- Caveat (inferred, ours): Only one real disk (HD 143006) and one synthetic disk are tested, so the regularizer ranking may not generalize
- Caveat (inferred, ours): The quoted resolution gain (up to 3 versus 2-3) has no stated measurement method
- Caveat (inferred, ours): Final lambda values for entropy and sparsity are not reported, and the final lambda_TSV was tuned by eye
- Caveat (inferred, ours): Ground truth comes from a simulation with a Hann-windowed, rescaled image and the same uv sampling, which favours RML
- Caveat (inferred, ours): No uncertainty estimates on CV scores or on the resolution gain

## Reproducibility

- Data public (paper): Calibrated DSHARP HD 143006 visibilities downloadable from the DSHARP archive; MPoL and mpoldatasets are public  
  > "the calibrated visibilities can be downloaded from the DSHARP archive" (Data)
- Products in archive: _not stated_
- Code: MPoL is open source; data-processing steps in the mpoldatasets repository  
  > "is an open-source Python package we have designed as a foundation to enable RML imaging for a variety of interferometric workflows." (The MPoL Package); "A full accounting of the data processing steps are available on the `mpoldatasets` repository" (Data)
- Missing: Lambda values for entropy and sparsity in the final image, and CV grid values
- Missing: Optimizer settings, learning rate, iteration counts for the full-data images
- Missing: Image size and pixel size for the HD 143006 RML image
- Missing: Dartboard bin numbers and random seeds
- Missing: MPoL version
- Data volume (inferred): Not stated in the paper; the DSHARP HD 143006 continuum measurement set is likely of order a few GB (inferred), the mock logo dataset is small
- Score (inferred): 3/5, Data and code are public and the method and loss functions are described, but several key settings for the final image (entropy and sparsity lambdas, optimizer settings, image grid) are not given
- Rediscovery candidate: no, Public data and open code, but the recipe for the main final image is incomplete and the central results are qualitative or image-based rather than numeric

## Links

- Method: Andrews et al. 2018 (cite: Andrews_2018) (DSHARP calibration procedures and fiducial CLEAN image)
- Method: Czekala et al. 2021 MPoL v0.1.1 (cite: mpol_2021) (The MPoL software used for all RML imaging)
- Method: EHT Collaboration 2019 (cite: EHTCollab_2019) (Definition of the maximum entropy regularizer)
- Method: Rudin et al. 1992 (cite: Rudin_1992) (Definition of the TV loss)
- Companion: Pinte et al. 2016 (cite: Pinte_2016) (Source of the simulated disk used as ground truth)
- Companion: Yamaguchi et al. 2020 (cite: Yamaguchi_2020) (Earlier RML imaging of a protoplanetary disk with sparsity and TSV and K-fold CV)
- Related: DSHARP (ALMA large program 2016.1.00484.L)

## Checks

```json
{
 "quotes": 106,
 "quotes_ok": 106,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 116,
  "stated": 75,
  "rate": 0.647
 },
 "evidence_ok": true
}
```
