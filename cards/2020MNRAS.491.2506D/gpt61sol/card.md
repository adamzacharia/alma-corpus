# Using machine learning to study the kinematics of cold gas in galaxies

`2020MNRAS.491.2506D` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Dawson, James M. | arXiv: 1911.00291 | DOI: 10.1093/mnras/stz3097

Card schema 1.0 | model gpt-6.1-sol | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: nearby_galaxies
- Question: Can a convolutional autoencoder trained on simulated velocity maps distinguish disturbed from ordered cold gas and recover position angles?  
  > "With this in mind, we create a binary classifier to predict whether the cold gas in galaxies exhibit dispersion dominated or disk dominated rotation in order to maximise the recall of rare galaxies with disturbed cold gas." (Introduction); "Given that position angle is clearly encoded in our latent $xy$ plane (see Figure [5](#Figure:latent_3d)), it is possible to return predicted position angles with associated errors." (Recovering position angle)
- Target **ESO358-G063**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **ESO359-G002**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **FCC207**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **FCC261**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **FCC282**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **FCC332**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **MCG-06-08-024**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC1351A**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC1365**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC1380**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC1386**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC1387**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC1436**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC1437B**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **PGC013571**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC0383**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC0404**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC0449**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC0524**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC0612**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC1194**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC1574**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC3368**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC3393**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC4429**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC4501**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC4697**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC4826**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC5064**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NGC7052**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00493.S, 2015.1.00086.S, 2015.1.00419.S, 2015.1.00466.S, 2015.1.00598.S, 2016.1.00437.S, 2016.1.00839.S, 2015.1.01135.S, 2016.1.01553.S, 2016.2.00046.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: 15 WISDOM velocity maps and 15 AlFoCS velocity maps  
  > "For our test sample we use an aggregated selection of 15 velocity maps" (Test case III: ALMA data); "WISDOM) CO(1-0, 2-1, and 3-2) and 15 CO(1-0) velocity maps" (Test case III: ALMA data)
- Line: CO 1-0 (not stated)
- Line: CO 2-1 (not stated)
- Line: CO 3-2 (not stated)
- Other facility **LVHIS**: HI velocity fields for a separate transfer-learning test  
  > "we used it to classify velocity maps of HI velocity fields from the the" (Test case IV: LVHIS data); "LVHIS; (cite: koribalski_local_2018)" (Test case IV: LVHIS data)
- Other facility **SIMBAD Astronomical Database**: Galaxy positions queried through astroquery  
  > "All galaxies whose positions could not be found using the `Python` package `astroquery`[^9] (searching the SIMBAD Astronomical Database[^10]), or whose HI structures were clearly misaligned with the true galaxy centres, were omitted from further testing." (Test case IV: LVHIS data)
- External data: 15 AlFoCS CO(1-0) velocity maps  
  > "and 15 CO(1-0) velocity maps from the" (Test case III: ALMA data); "AlFoCS, (cite: zabel_alma_2019)" (Test case III: ALMA data) [from (cite: zabel_alma_2019)]
- External data: 15 WISDOM CO(1-0, 2-1, and 3-2) velocity maps  
  > "For our test sample we use an aggregated selection of 15 velocity maps" (Test case III: ALMA data); "WISDOM) CO(1-0, 2-1, and 3-2)" (Test case III: ALMA data) [from not stated]
- External data: LVHIS HI velocity fields  
  > "we used it to classify velocity maps of HI velocity fields from the the" (Test case IV: LVHIS data); "LVHIS; (cite: koribalski_local_2018)" (Test case IV: LVHIS data) [from (cite: koribalski_local_2018)]
- Simulation/model as data: EAGLE cosmological hydrodynamical simulations in a closed-volume ΛCDM universe  
  > "is a collection of cosmological hydrodynamical simulations which follow the evolution of galaxies and black holes in a closed volume $\Lambda$ cold dark matter ($\Lambda$CDM) universe." (EAGLE); "The simulations boast subgrid models which account for physical processes below a known resolution limit ((cite: schaye_eagle_2015; crain_eagle_2015; the_eagle_team_eagle_2017))." (EAGLE)
- Simulation/model as data: RefL0025N0376 and RefL050N0752 snapshot 28; RefL0100N1504 snapshots 28, 27, 26, 25; z = 0–0.27  
  > "for this work we utilise snapshot $28$ for `RefL0025N0376` and `RefL050N0752` and snapshots 28, 27, 26, and 25 for `RefL0100N1504` (i.e. redshifts $z = 0$-$0.27$)." (EAGLE)
- Simulation/model as data: 14,846 simulated galaxies  
  > "With these selection criteria, we work with a set of $14,846$ simulated galaxies." (EAGLE)

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

- Circularity as the fraction of kinetic energy invested in circular, ordered rotation  
  > "analyses the fraction of kinetic energy invested in circular, ordered, rotation ((cite: sales_origin_2012))." (Circularity parameter) [from (cite: sales_origin_2012)]
- Adapted EAGLE team data-reading scripts  
  > "The scripts for reading in data, from the EAGLE project database, were adapted versions of the EAGLE team’s pre-written scripts[^3]." (EAGLE) [from EAGLE team’s pre-written scripts[^3]: https://github.com/jchelly/read_eagle]
- EAGLE Database centre of potential used as the rotation origin  
  > "using the centre of potential (as defined in the EAGLE Database, see (cite: the_eagle_team_eagle_2017)) as the origin." (Data preparation) [from (cite: the_eagle_team_eagle_2017)]
- KinMS for mock interferometric observations from EAGLE particles  
  > "We then made use of the `Python` based kinematic simulator `KinMS`[^4] (KINematic Molecular Simulation) from (cite: davis_black-hole_2013) to turn EAGLE data into mock interferometric observations." (Data preparation) [from (cite: davis_black-hole_2013)]
- Replace non-numerical values and infinities with 0 km s−1  
  > "It should be noted that we set all non-numerical values or infinities to a constant value, as passing such values to an ML algorithm will break its training." (Data preparation); "We adopt $0$ $\text{km\,s}^{-1}$ as our constant (similarly to (cite: diaz_classifying_2019)) to minimise the the background influencing feature extraction." (Data preparation) [from (cite: diaz_classifying_2019)]
- Smooth masking of noisy mock cubes  
  > "The resulting noisy data cubes are then masked using *smooth masking*, a method that is representative of how one would treat a real data cube ((cite: Dame2011))." (Simulating noise) [from (cite: Dame2011)]
- RMS-based clipping to mimic LVHIS database velocity-map preparation  
  > "each cube is clipped at some fraction of the RMS (calculated in line free channels) to mimic the noise removal processes used in generating velocity maps in the LVHIS database." (Test case IV: LVHIS data) [from LVHIS; (cite: koribalski_local_2018)]
- Adaptive Adam learning rate optimiser  
  > "We use an adaptive Adam learning rate optimiser ((cite: kingma_adam:\_2014)), starting with a learning rate of $0.001$ which halves every $30$ epochs;" (Model training: Rotationally invariant case) [from (cite: kingma_adam:\_2014)]

### Not stated but needed to reproduce (our reading)

- Which ALMA project and CO transition supplied each galaxy's exact velocity-map product.
- Calibration and imaging provenance of the reused ALMA maps, including beam, channel width and moment-map masking.
- ALMA input-map centring, spatial resampling, blank handling and velocity normalization.
- Exact EAGLE query, adapted reading scripts and particle-weighting implementation in KinMS.
- Training/test membership and whether rotations or repeated snapshots of the same galaxy cross the split.
- Random seeds for rotations, weighted sampling, network initialization and noise.
- Smooth-masking kernel and implementation; exact LVHIS RMS clipping fractions and line-free channels.
- Trained model weights, fitted PCA transformation and exact inference preprocessing.

## Analysis recipe

1. **Select simulated galaxies and calculate circularity labels**: Select EAGLE galaxies and star-forming particles; calculate κ = Krot/K from particle masses, positions and velocities.  
  > "\kappa = \frac{\text{K}_{\text{rot}}}{\text{K}}" (Circularity parameter); "we only accepted particles with a SFR $>0$ for pre-processing" (EAGLE); "Each galaxy, and therefore every cube, is assigned a label in the continuous range of $0$ to $1$ corresponding to the level of ordered rotation, $\kappa$, of that galaxy." (Labelling the training set)
   - software: EAGLE database, Adapted EAGLE reading scripts
   - parameter: Gas mass >1×10^9 M⊙; stellar mass >5×10^9 M⊙; 30 kpc aperture  
  > "we set lower limits on the total gas mass ($>1\times10^{9}$ M$_{\odot}$) and stellar mass ($>5\times10^{9}$ M$_{\odot}$) within an aperture size of $30$ kpc around each galaxy’s centre of potential" (EAGLE)
   - parameter: >200 particles within the 30 kpc aperture  
  > "At this stage we also set a lower limit on the number of particles within the $30$ kpc aperture to $>200$." (EAGLE)
   - assumption: Particles with SFR >0 represent cold, dense molecular gas capable of star formation.  
  > "In order to select particles which are representative of cold, dense, molecular gas capable of star formation, we only accepted particles with a SFR $>0$ for pre-processing" (EAGLE)
   - fitting: _not stated_
   - validation: Particle-count cut intended to support statistically valid kinematics and reduce low-brightness clipping scale problems.  
  > "This was to ensure we had enough particles to calculate statistically valid kinematic properties of the galaxies and reduce scaling issues caused by clipping pixels with low brightness when generating velocity maps." (EAGLE)
2. **Generate mock velocity maps**: Align angular momentum with +z, rotate and displace galaxies, and generate mock observations directly from their 3D particle distributions using KinMS.  
  > "Each galaxy was rotated so that their total angular momentum vector was aligned with the positive $z$-axis" (Data preparation); "Using `KinMS` we generate simulated interferometric observations of galaxies directly from their 3D particle distributions." (Data preparation)
   - software: Python, KinMS
   - parameter: 8 random integer rotations; 0°≤θpos<360°; 5°≤φinc≤85°  
  > "For any given distance projection, galaxies were given 8 random integer rotations in position-angle ($0^{\circ}\leq \theta_{\text{pos}}<360 ^{\circ}$) and inclination ($5^{\circ}\leq\phi_{\text{inc}}\leq85^{\circ}$)." (Data preparation)
   - parameter: 64″×64″ mock velocity-map field  
  > "Each galaxy is displaced such that they fill a $64^{\prime\prime}\times64^{\prime\prime}$ mock velocity map image" (Data preparation)
   - parameter: Galaxy radius = 98th percentile particle distance from centre of potential  
  > "Each galaxy’s radius is given as the $98$th percentile particle distance from its center of potential in kpc." (Data preparation)
   - parameter: Mock bmaj = 3″; stacked velocity-map dimensions 64×64×8  
  > "The EAGLE galaxies were passed to `KinMS` to create cubes of stacked velocity maps, with fixed mock beam sizes of $\text{bmaj} = 3^{\prime\prime}$, ready for labelling." (Data preparation); "Each cube measured $64\times64\times8$ where $64\times64$ corresponds to the image dimensions (in pixels) and $8$ corresponds to snapshots during position-angle and inclination rotations." (Data preparation)
   - parameter: Non-numerical values and infinities replaced with 0 km s−1  
  > "It should be noted that we set all non-numerical values or infinities to a constant value, as passing such values to an ML algorithm will break its training." (Data preparation); "We adopt $0$ $\text{km\,s}^{-1}$ as our constant (similarly to (cite: diaz_classifying_2019)) to minimise the the background influencing feature extraction." (Data preparation)
   - assumption: Centre of potential is the origin.  
  > "using the centre of potential (as defined in the EAGLE Database, see (cite: the_eagle_team_eagle_2017)) as the origin." (Data preparation)
   - fitting: _not stated_
   - validation: _not stated_
3. **Construct the noisy simulation test**: Add zero-mean Gaussian noise to mock cubes, smooth-mask, generate intensity-weighted moment-one maps, clip and normalize.  
  > "we seeded the mock-EAGLE-interferometric-datacubes with Gaussian distributed noise of mean $\mu = 0$" (Simulating noise); "The resulting noisy data cubes are then masked using *smooth masking*, a method that is representative of how one would treat a real data cube ((cite: Dame2011))." (Simulating noise); "An intensity weighted moment one map is then generated in `KinMS` from the masked cube" (Simulating noise)
   - software: KinMS
   - parameter: Noise standard deviation = 1/(S/N) times mean maximum intensity of cube channels containing line emission  
  > "i.e. some fraction, $\frac{1}{\text{S/N}}$, of the mean maximum intensity, I$_{\text{max}}$, of each cube-channel, $c$, containing line emission." (Simulating noise)
   - parameter: S/N = 10; masking at 3 times RMS  
  > "classifying noisy EAGLE test data with $\text{S/N} = 10$ and masking at $3$ times the RMS level" (Test case II: Noisy EAGLE data)
   - parameter: Clip noisy moment-one maps at the 96th percentile before normalization to −1 to 1  
  > "before being normalised into the range of $-1$ to $1$." (Simulating noise); "We clip all noisy moment 1 maps at a fixed $96$th percentile level, before normalising, in order to combat this effect." (Simulating noise)
   - assumption: Global clipping approximates a predetermined survey-wide procedure.  
  > "Although simple, this likely reflects the conditions of a next generation survey in which clipping *on the fly* will be done using a predetermined method globally rather than optimising on a case by case basis." (Simulating noise)
   - fitting: _not stated_
   - validation: Compare noisy-test classification with the noiseless case and inspect systematic latent shifts.  
  > "The combination of adding noise followed by using an arbitrary clipping level causes test objects to gravitate towards the low $\kappa$ region in latent space." (Test case II: Noisy EAGLE data)
4. **Train the convolutional autoencoder**: Train a convolutional encoder and reflected decoder to reconstruct velocity maps through a three-dimensional bottleneck.  
  > "The decoder structure is simply a reflection of the encoder for simplicity." (Model training: Rotationally invariant case); "The CAE learned to encode input images to 3 dimensional latent vectors." (Model training: Rotationally invariant case); "The model uses a mean squared error (MSE) loss," (Model training: Rotationally invariant case)
   - software: Python, PyTorch
   - parameter: 300 epochs; batch size 32; 6400 sampled images per epoch  
  > "The CAE is trained for 300 epochs (with a batch size of 32) where one epoch comprises a throughput of 6400 images sampled from the training set." (Model training: Rotationally invariant case)
   - parameter: Weighted sampling with replacement; κ bins of width δκ = 0.1  
  > "Images are selected for each mini-batch using a weighted sampler which aims to balance the number of images in each $\kappa$ bin of width $\delta\kappa=0.1$." (Model training: Rotationally invariant case); "Inputs are sampled with replacement allowing multiple sampling of objects to prevent under-filled bins." (Model training: Rotationally invariant case)
   - fitting: MSE reconstruction loss; gradient descent with Adam; learning rate 0.001, halved every 30 epochs  
  > "The model uses a mean squared error (MSE) loss," (Model training: Rotationally invariant case); "for evaluating the error between input and output images and weights are updated through gradient descent." (Model training: Rotationally invariant case); "We use an adaptive Adam learning rate optimiser ((cite: kingma_adam:\_2014)), starting with a learning rate of $0.001$ which halves every $30$ epochs;" (Model training: Rotationally invariant case)
   - validation: Inspect convergence and test MSE for overfitting.  
  > "we see that the model has converged well before the $300^{\text{th}}$ epoch and observe no turn-over of the test MSE loss, which would indicate overfitting." (Model training: Rotationally invariant case)
5. **Construct and test the circularity classifier**: PCA-rotate latent vectors; fold to |z| and √(x²+y²); separate κ above and below 0.5 with a vertical boundary.  
  > "principal component analysis (PCA) function on these vectors to rotate the latent space so that it aligns with one dominant latent axis, in this case the $z$ axis." (Model training: Rotationally invariant case); "the data is folded around the z and x axes consecutively to leave a 2-dimensional latent space devoid of structural symmetries with dimensions \|z\| and $\sqrt{x^{2}+y^{2}}$" (Model training: Rotationally invariant case); "we find that a simple vertical boundary line is best at separating the galaxies whose $\kappa$ are greater than or less than $0.5$." (Model training: Rotationally invariant case)
   - software: scikit-learn
   - parameter: κ classification boundary = 0.5  
  > "Note that $0.5$ is an arbitrarily chosen threshold for our classification boundary but is motivated by the notion of separating ordered from disturbed gas structures in galaxies." (Model training: Rotationally invariant case)
   - assumption: Optimize equal true-positive and true-negative scores rather than the underlying class distribution.  
  > "The intersection of TP and TN lines (and therefore the FP and FN lines)" (Model training: Rotationally invariant case); "This makes our classifier independent of the underlying distribution of high and low $\kappa$ galaxies in an attempt to maximise the recall of both classes." (Conclusions)
   - fitting: Move the boundary in x; choose the TP/TN intersection at √(x²+y²) = 2.961±0.002.  
  > "In order to optimise the boundary line location, we measure the true positive (TP), true negative (TN), false positive (FP) and false negative (FN) scores when progressively increasing the boundary line’s $x$ location." (Model training: Rotationally invariant case); "indicates the optimal position for our boundary, which is at $\sqrt{x^{2}+y^{2}}=2.961\pm0.002$." (Model training: Rotationally invariant case)
   - validation: Confusion matrices on noiseless training and test sets; separate noisy test.  
  > "shows the confusion matrix when testing the noiseless EAGLE test set using our boundary classifier." (Test case I: Noiseless EAGLE data); "The classifier has a mean training recall of $84\%$ for both classes." (Test case I: Noiseless EAGLE data); "classifying noisy EAGLE test data with $\text{S/N} = 10$ and masking at $3$ times the RMS level" (Test case II: Noisy EAGLE data)
6. **Evaluate transfer to ALMA observations**: Pass 30 ALMA velocity maps through the CAE and classifier; compare with disturbed/regular labels assigned by eye.  
  > "We tested 30 velocity maps of galaxies observed with ALMA to evaluate the performance of the classifier on real observations." (Test case III: ALMA data); "We classify each galaxy, by eye, as either disturbed or regularly rotating" (Test case III: ALMA data)
   - parameter: 15 WISDOM maps and 15 AlFoCS maps  
  > "For our test sample we use an aggregated selection of 15 velocity maps" (Test case III: ALMA data); "WISDOM) CO(1-0, 2-1, and 3-2) and 15 CO(1-0) velocity maps" (Test case III: ALMA data)
   - assumption: Visual disturbed/regular classifications provide a heuristic evaluation.  
  > "in order to heuristically evaluate the classifier’s performance." (Test case III: ALMA data)
   - fitting: _not stated_
   - validation: Compare predictions with human-eye classifications and inspect misclassified galaxies.  
  > "The classifier performs with an accuracy of $90\%$ when compared to the predictions by human eye." (Test case III: ALMA data); "The false negative classification of NGC1351A can be explained by its disconnected structure and edge-on orientation" (Test case III: ALMA data); "It should be noted that upon inspection the false positive classification of FCC282 can be attributed to the appearance of marginal rotation in the galaxy." (Test case III: ALMA data)
7. **Evaluate transfer to HI observations**: RMS-clip LVHIS cubes, reject missing or misaligned centres, create velocity maps, bilinearly rescale when needed and classify.  
  > "each cube is clipped at some fraction of the RMS (calculated in line free channels) to mimic the noise removal processes used in generating velocity maps in the LVHIS database." (Test case IV: LVHIS data); "All galaxies whose positions could not be found using the `Python` package `astroquery`[^9] (searching the SIMBAD Astronomical Database[^10]), or whose HI structures were clearly misaligned with the true galaxy centres, were omitted from further testing." (Test case IV: LVHIS data); "we used PyTorch’s `torch.nn.functional.interpolation` function (in bilinear mode) to rescale them up or down to the required dimensions prior to clipping." (Test case IV: LVHIS data)
   - software: Python, astroquery, SIMBAD Astronomical Database, PyTorch, torch.nn.functional.interpolation
   - parameter: 61 galaxies; 64×64-pixel inputs  
  > "This left $61$ galaxies" (Test case IV: LVHIS data); "Finally, where images were not $64 \times 64$ pixels," (Test case IV: LVHIS data)
   - assumption: Miscentred inputs can mimic disorderly rotation and increase false negatives.  
  > "This was to prevent misclassification based on pointing error which correlates with features of disorderly rotation to the CAE and would artificially increase the FN rate." (Test case IV: LVHIS data)
   - fitting: _not stated_
   - validation: Compare with visually identified low-κ candidates.  
  > "By eye, we identified $10$ galaxies in the LVHIS which are likely to be definitively classified as $\kappa < 0.5$" (Test case IV: LVHIS data); "Of these $10$ candidates, $8$ were correctly identified as $\kappa < 0.5$" (Test case IV: LVHIS data)
8. **Recover position angles from latent coordinates**: Use the angle in the latent xy plane; rotate by the median systematic offset and subtract 180°.  
  > "We define the predicted position angle, $\theta_{\text{latent}}$, as the clockwise angle between the positive latent $x$-axis and the position of data points in the latent $xy$ plane." (Recovering position angle); "by rotating the latent positions by the median offset, found to be $\delta\theta\sim36.6^{\circ}$, and subtracting an additional $180^{\circ}$." (Recovering position angle)
   - parameter: θlatent = tan−1(y/x) in the rotated frame  
  > "In the now rotated frame, $\theta_{\text{latent}}$ is defined as $\tan^{-1}\left(\frac{y}{x}\right)$, where $x$ and $y$ are the latent $x$ and $y$ positions of each galaxy" (Recovering position angle)
   - fitting: Systematic angular offset estimated by its median.  
  > "by rotating the latent positions by the median offset, found to be $\delta\theta\sim36.6^{\circ}$, and subtracting an additional $180^{\circ}$." (Recovering position angle)
   - validation: Standard deviation of residuals against true position angles; repeat with S/N = 10 and inspect inclination dependence.  
  > "We calculated errors on the resulting predictions of $\theta_{\text{latent}}$ by taking the standard deviation of residuals between $\theta_{\text{latent}}$ and $\theta_{\text{pos}}$." (Recovering position angle); "We repeated this procedure for the noisy EAGLE data, with $\text{S/N}=10$," (Recovering position angle); "We see that at higher inclinations the error in predicted $\theta_{\text{pos}}$ is better constrained than for lower inclinations." (Recovering position angle)

## Software

- **Python** : Language underlying KinMS and PyTorch  
  > "We then made use of the `Python` based kinematic simulator `KinMS`[^4] (KINematic Molecular Simulation) from (cite: davis_black-hole_2013) to turn EAGLE data into mock interferometric observations." (Data preparation); "Being grounded in `Python`, `PyTorch` is designed to be linear and intuitive for researchers with a C99 API backend for competitive computation speeds." (Model training: Rotationally invariant case)
- **KinMS** : Mock interferometric observations from EAGLE particles and intensity-weighted moment-one maps  
  > "Using `KinMS` we generate simulated interferometric observations of galaxies directly from their 3D particle distributions." (Data preparation); "An intensity weighted moment one map is then generated in `KinMS` from the masked cube" (Simulating noise)
- **EAGLE database** : Simulated particle data and centres of potential  
  > "Each simulation was conducted using smooth particle hydrodynamics, meaning users can directly work with the simulated data in the form of particles, whose properties are stored in output files and a database that can be queried." (EAGLE); "using the centre of potential (as defined in the EAGLE Database, see (cite: the_eagle_team_eagle_2017)) as the origin." (Data preparation)
- **Adapted EAGLE reading scripts** : Read data from the EAGLE project database  
  > "The scripts for reading in data, from the EAGLE project database, were adapted versions of the EAGLE team’s pre-written scripts[^3]." (EAGLE)
- **PyTorch** 0.4.1: Construct and train the ML model  
  > "In order to construct our ML model, we make use of `PyTorch`[^5] 0.4.1, an open source ML library capable of GPU accelerated tensor computation and automatic differentiation ((cite: paszke_automatic_2017))." (Model training: Rotationally invariant case)
- **scikit-learn** : PCA rotation of latent vectors  
  > "We use `scikit-learn`’s[^8] principal component analysis (PCA) function on these vectors to rotate the latent space so that it aligns with one dominant latent axis, in this case the $z$ axis." (Model training: Rotationally invariant case)
- **astroquery** : Search SIMBAD for LVHIS galaxy positions  
  > "All galaxies whose positions could not be found using the `Python` package `astroquery`[^9] (searching the SIMBAD Astronomical Database[^10]), or whose HI structures were clearly misaligned with the true galaxy centres, were omitted from further testing." (Test case IV: LVHIS data)
- **SIMBAD Astronomical Database** : Galaxy-position lookup  
  > "All galaxies whose positions could not be found using the `Python` package `astroquery`[^9] (searching the SIMBAD Astronomical Database[^10]), or whose HI structures were clearly misaligned with the true galaxy centres, were omitted from further testing." (Test case IV: LVHIS data)
- **torch.nn.functional.interpolation** : Bilinear rescaling of LVHIS images to required dimensions  
  > "we used PyTorch’s `torch.nn.functional.interpolation` function (in bilinear mode) to rescale them up or down to the required dimensions prior to clipping." (Test case IV: LVHIS data)
- **fit_kinematic_pa** : Mentioned as an alternative position-angle fitting routine  
  > "Other kinematic fitting routines exist for this purpose including `fit_kinematic_pa` ((cite: Krajnovi_kinemetry)) and the radon transform method ((cite: Stark_radon))." (Recovering position angle)
- **Astropy** : Used in the research; specific operations not stated  
  > "This research made use of Astropy[^11], a community-developed Python package for Astronomy (cite: astropy_collaboration_astropy:\_2013; astropy_collaboration_astropy_2018)." (Acknowledgements)
- **GitHub** : Hosting paper code and an ongoing development version  
  > "The code developed for this paper is available on GitHub[^6] as well as an ongoing development version[^7]." (Model training: Rotationally invariant case)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Optimized classifier boundary √(x²+y²) | 2.961 | ±0.002 | dimensionless | 5 | indicates the optimal position for our boundary, which is at $\sqrt{x^{2}+y^{2}}=2.961\pm0.002$. |
| Mean noiseless training recall for both classes | 84 | not stated | % | 5 | The classifier has a mean training recall of $84\%$ for both classes. |
| Mean simulated-data recall | 85 | not stated | % | 5 | Our tests on simulated data show a mean recall of $85\%$ when attempting to recover the circularity parameter |
| ALMA heuristic classification accuracy | 90 | not stated | % | 6 | The classifier performs with an accuracy of $90\%$ when compared to the predictions by human eye. |
| ALMA galaxies classified as low κ | 6 | not stated | galaxies | 6 | Of the $30$ galaxies observed with ALMA, $6$ ($20\%$) are classified as low $\kappa$ |
| ALMA fraction classified as low κ | 20 | not stated | % | 6 | Of the $30$ galaxies observed with ALMA, $6$ ($20\%$) are classified as low $\kappa$ |
| LVHIS heuristic classification accuracy | 97 | not stated | % | 7 | as well as $90\%$ and $97\%$ heuristic accuracy when recovering the circularity parameter for galaxies observed with ALMA and as part of LVHIS respectively. |
| LVHIS galaxies classified as low κ | 8 | not stated | galaxies | 7 | Of the $61$ galaxies, $8$ ($13\%$) are classified as low $\kappa$. |
| LVHIS fraction classified as low κ | 13 | not stated | % | 7 | Of the $61$ galaxies, $8$ ($13\%$) are classified as low $\kappa$. |
| Observational CO and HI heuristic accuracy reported in abstract | 95 | not stated | % | 0 | performs as expected on observational CO and HI velocity maps, with a heuristic accuracy of $95\%$. |
| Median latent position-angle offset | ∼36.6 | not stated | degrees | 8 | by rotating the latent positions by the median offset, found to be $\delta\theta\sim36.6^{\circ}$, and subtracting an additional $180^{\circ}$. |
| 1σ position-angle uncertainty at inclination 82.5° | ±17 | not stated | degrees | 8 | with a $1\sigma$ uncertainty range of $\pm17^{\circ}$ to $\pm23^{\circ}$ (for galaxies with inclinations of $82.5^{\circ}$ to $32.5^{\circ}$, respectively) |
| 1σ position-angle uncertainty at inclination 32.5° | ±23 | not stated | degrees | 8 | with a $1\sigma$ uncertainty range of $\pm17^{\circ}$ to $\pm23^{\circ}$ (for galaxies with inclinations of $82.5^{\circ}$ to $32.5^{\circ}$, respectively) |

## Qualitative findings

- Noise and global clipping shift test galaxies toward the low-κ latent region.  
  > "The combination of adding noise followed by using an arbitrary clipping level causes test objects to gravitate towards the low $\kappa$ region in latent space." (Test case II: Noisy EAGLE data)
- Position-angle recovery is better constrained at higher inclinations.  
  > "We see that at higher inclinations the error in predicted $\theta_{\text{pos}}$ is better constrained than for lower inclinations." (Recovering position angle)
- Inclinations could not be recovered because of overlapping latent-z positions.  
  > "Recovering inclinations, $\phi_{\text{inc}}$, of galaxies was not possible using our CAE due to the high overlap in latent $z$ positions for the entire range of $\phi_{\text{inc}}$." (Conclusions)
- Patchy high-κ ALMA galaxies appear closer to the classification boundary.  
  > "We see evidence of patchy high $\kappa$ galaxies residing closer to the classification boundary than non-patchy examples." (Test case III: ALMA data)

## Claim tuples

- H: Velocity-map compression can retain information about ordered gas rotation. | E: Train a three-dimensional convolutional autoencoder and binary κ classifier on simulated velocity maps. | R: Mean simulated-data recall of 85%. | F: A compact latent representation retains useful kinematic information. | **supported**
- H: The simulation-trained classifier can identify disturbed cold gas in ALMA observations. | E: Classify 30 ALMA velocity maps and compare with labels assigned by eye. | R: 90% heuristic accuracy; 6 of 30 maps classified as low κ. | F: The classifier transfers successfully to the tested ALMA maps under visual evaluation. | **supported**
- H: A model tailored to ALMA-like simulations can generalise to HI observations. | E: Classify LVHIS velocity maps and compare with visual classifications. | R: 97% heuristic accuracy. | F: Transfer to HI supports potential applicability to SKA science. | **supported**
- H: Latent xy coordinates can provide initial position-angle estimates. | E: Calculate latent angles, remove the systematic offset and measure residual scatter against true position angles. | R: 1σ uncertainty from ±17° to ±23° for inclinations 82.5° to 32.5°. | F: Position-angle estimates may initialize kinematic modelling. | **supported**
- H: Inclination can be recovered simply from the learned latent coordinates. | E: Inspect inclination distributions against latent-z position. | R: Substantial overlap across inclinations. | F: The CAE does not recover inclination by this approach. | **refuted**

## Reasoning

- Why this data: Simulations provide accessible large samples and empirical kinematic truths; spatial selection was designed for ALMA transfer tests.  
  > "Using simulations has certain advantages over collecting real data including accessibility, larger sample sizes, and the ability to calculate empirical truths from the data." (EAGLE); "However, as we are particularly interested in the performance of our models with ALMA observations, we instead impose a radial limit for this work." (EAGLE)
- Why this method: Three latent dimensions preserve performance while allowing interpretation; a simple boundary separates broad κ classes better than continuous regression.  
  > "compression to higher dimensions impaired our ability to directly observe correlations between features and latent positions with no improvement to the model’s performance." (Model training: Rotationally invariant case); "the spread on latent positions taken up by different $\kappa$ galaxies makes a regression to recover $\kappa$ too difficult." (Model training: Rotationally invariant case)
- Alternative: Higher-order polynomial and regional boundary classifiers were tested; a vertical line was preferred.  
  > "Having tested multiple classifiers on the 2D latent space (such as high order polynomial and regional boundary approaches), we find that a simple vertical boundary line is best" (Model training: Rotationally invariant case)
- Alternative: Lower-dimensional compression performed poorly; higher-dimensional compression did not improve performance and reduced interpretability.  
  > "Further testing showed that any higher compression, to lower dimensions, resulted in poor performance" (Model training: Rotationally invariant case); "compression to higher dimensions impaired our ability to directly observe correlations between features and latent positions with no improvement to the model’s performance." (Model training: Rotationally invariant case)
- Alternative: Alternative cold-gas selections were acknowledged; SFR >0 was chosen for simplicity.  
  > "There are many ways to select cold gas in the EAGLE simulations ((cite: 2015MNRAS.452.3815L)) but we use this method for its simplicity" (EAGLE)
- Alternative: fit_kinematic_pa and radon-transform position-angle methods were mentioned but not benchmarked here.  
  > "Other kinematic fitting routines exist for this purpose including `fit_kinematic_pa` ((cite: Krajnovi_kinemetry)) and the radon transform method ((cite: Stark_radon))." (Recovering position angle); "Bench marking an ML model against existing ones, as a dedicated standalone mechanism for recovering $\theta_{\text{pos}}$, is an avenue for future research." (Recovering position angle)
- How they decided it was enough: Training converged before epoch 300 without a turnover in test MSE.  
  > "we see that the model has converged well before the $300^{\text{th}}$ epoch and observe no turn-over of the test MSE loss, which would indicate overfitting." (Model training: Rotationally invariant case)
- Limitation (authors): Simulated training data have unproven assumptions, imperfect physics and a resolution/sample-size trade-off.  
  > "However, there are drawbacks, including: unproven model assumptions, imperfect physics, and trade-off between resolution and sample size due to computational constraints." (EAGLE)
- Limitation (authors): The CAE architecture was not optimized.  
  > "This means our CAE is unlikely to have the most optimised architecture" (Model training: Rotationally invariant case)
- Limitation (authors): The 96th-percentile clipping level was arbitrary and not optimized.  
  > "Note that this choice of clipping at the $96$th percentile level is arbitrarily based on a handful of test cases and represents no specific parameter optimisation." (Simulating noise)
- Limitation (authors): The minimum usable S/N was not tested.  
  > "we have not tested the lower limit of S/N for which it is appropriate to use our classifier" (Test case II: Noisy EAGLE data)
- Limitation (authors): Low-κ selections can contain contaminants in heavily imbalanced samples.  
  > "one should take care when testing heavily imbalanced datasets where, although the dataset has been drastically thinned of high $\kappa$ galaxies, it is likely that the user will still need to examine the low $\kappa$ classification set for contaminants." (Conclusions)
- Limitation (authors): Classification is sensitive to the proxy used for the centre of potential.  
  > "Our models rely on using maps of galaxies which are centred on their centres of potential (i.e. the position of the most bound particle); therefore, our classifier is sensitive to the choice of centre of potential proxy." (Conclusions)
- Limitation (authors): Position-angle accuracy was not benchmarked against existing dedicated methods.  
  > "These methods likely have higher accuracy than seen here, as our network was not optimised for the recovery of $\theta_{pos}$." (Recovering position angle); "Bench marking an ML model against existing ones, as a dedicated standalone mechanism for recovering $\theta_{\text{pos}}$, is an avenue for future research." (Recovering position angle)
- Caveat (inferred, ours): Observational accuracy measures agreement with subjective visual labels, not independently measured six-dimensional circularity.
- Caveat (inferred, ours): The supplied ALMA table labels NGC1351A as TN despite author/model predictions 1/0; the narrative also contains inconsistent false-positive/false-negative wording.
- Caveat (inferred, ours): The split procedure is insufficiently described to exclude shared galaxies, augmented views or related snapshots across training and test sets.
- Caveat (inferred, ours): No confidence intervals are supplied for observational accuracies from the small test samples.
- Caveat (inferred, ours): The abstract's 95% observational accuracy is not explicitly reconciled with the separate 90% ALMA and 97% LVHIS values.
- Caveat (inferred, ours): The 3″ beam and 64″ field describe mock observations and must not be treated as measured settings of the real ALMA data.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: Paper code and ongoing development version available on GitHub  
  > "The code developed for this paper is available on GitHub[^6] as well as an ongoing development version[^7]." (Model training: Rotationally invariant case)
- Code: https://github.com/SpaceMeerkat/CAE/releases/tag/v1.0.0  
  > "https://github.com/SpaceMeerkat/CAE/releases/tag/v1.0.0" (Information on test galaxies)
- Code: https://github.com/SpaceMeerkat/CAE  
  > "[^7]: <https://github.com/SpaceMeerkat/CAE>" (Information on test galaxies)
- Missing: Exact ALMA velocity-map files and their association with the ten project codes.
- Missing: ALMA calibration, imaging and moment-map preparation settings.
- Missing: Per-galaxy ALMA preprocessing and centring instructions.
- Missing: Exact simulated training/test split and random seeds.
- Missing: Availability of trained weights, fitted PCA parameters and the preprocessing implementation.
- Missing: Exact smooth-mask settings and LVHIS clipping fractions.
- Missing: Explicit statement of public availability for the observational input products.
- Data volume (inferred): The velocity-map inference stage is compact; full ALMA visibility and EAGLE particle-data volumes cannot be estimated from the supplied text.
- Score (inferred): 3/5, 3/5: code release, simulation selection and core learning settings are given, but observational product provenance, preprocessing and exact training state are incomplete.
- Rediscovery candidate: no, Main results are numeric, but public availability of the exact input data is not stated and the observational preprocessing recipe is incomplete.

## Links

- Method: (cite: sales_origin_2012) (Circularity measure based on rotational and total kinetic energy.)
- Method: (cite: davis_black-hole_2013) (KinMS mock interferometric observations.)
- Method: (cite: Dame2011) (Smooth masking of noisy cubes.)
- Method: (cite: kingma_adam:\_2014) (Adam optimizer.)
- Method: (cite: paszke_automatic_2017) (PyTorch automatic differentiation and tensor computation.)
- Method: (cite: schaye_eagle_2015; crain_eagle_2015; the_eagle_team_eagle_2017) (EAGLE simulations, subgrid models and database definitions.)
- Method: (cite: diaz_classifying_2019) (Precedent for zero-valued backgrounds and motivation for combining morphology and kinematics.)
- Related: EAGLE
- Related: WISDOM
- Related: AlFoCS
- Related: LVHIS

## Checks

```json
{
 "quotes": 176,
 "quotes_ok": 176,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 10,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 222,
  "stated": 91,
  "rate": 0.41
 },
 "evidence_ok": true
}
```
