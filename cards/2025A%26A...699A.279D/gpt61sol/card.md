# Origin of the ring ellipticity in the black hole images of M87<SUP>*</SUP>

`2025A&A...699A.279D` | Astronomy and Astrophysics 2025 | first author: Dahale, Rohan | arXiv: 2505.10333 | DOI: 10.1051/0004-6361/202555235

Card schema 1.0 | model gpt-6.1-sol | depth full | type archival_reuse

## Science

- Fields: agn_and_quasars
- Question: Disentangle gravitational ellipticity, emission ellipticity, and imaging artifacts in the M87* emission ring.  
  > "Our goal is to assess the degree to which the observed ellipticity in EHT images is a result of fundamental spacetime properties, astrophysical factors, or artifacts introduced by imaging algorithms." (Introduction)
- Target **M87***: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00841.V, 2016.1.01154.V
- bands: EHT higher frequency bands 3 and 4; these are the paper's EHT band labels.  
  > "The GLT participated only in the band 3 and 4, so we focus on data from the higher frequency bands in this study." (Introduction)
- frequencies and spectral setup: EHT band 3: 227.1 GHz; band 4: 229.1 GHz.  
  > "two at higher frequencies (band 3 and 4 at 227.1 GHz and 229.1 GHz)." (Introduction)
- continuum bandwidth: _not stated_
- arrays: EHT 2018, including GLT; ALMA used as a gain-phase reference station.  
  > "The addition of the Greenland Telescope (GLT; (cite: GLT)) in 2018 substantially improved $(u,v)$-coverage" (Introduction); "For the gain phases, the gain phase for ALMA is set to be zero." (Bayesian imaging methods)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: April 21, 2018.  
  > "Among the four observing days, we use April 21, which had the highest number of participating stations." (Introduction); "We estimate the precision with which the parameters of this model, fitted to data on April 21, 2018 at band 4, can be recovered." (Fisher information analysis)
- pi or archival as stated: _not stated_
- Other facility **Event Horizon Telescope (EHT)**: 2018 observations used to measure the emission-ring ellipticity.  
  > "In this study, we measured the ellipticity of the emission ring in the black hole images of using the EHT 2018 observations." (Summary and conclusions)
- Other facility **Greenland Telescope (GLT)**: Additional north-south (u,v)-coverage in EHT bands 3 and 4.  
  > "The addition of the Greenland Telescope (GLT; (cite: GLT)) in 2018 substantially improved $(u,v)$-coverage" (Introduction); "The GLT participated only in the band 3 and 4, so we focus on data from the higher frequency bands in this study." (Introduction); "Fisher information analysis was employed to first assess the feasibility of ellipticity measurements, after the addition of the GLT, which filled gaps in the north-south $(u,v)$-coverage." (Summary and conclusions)
- Other facility **James Clerk Maxwell Telescope (JCMT)**: Single-polarization-feed EHT data; retained after an exclusion test.  
  > "During the 2017 and 2018 EHT campaigns the James Clerk Maxwell Telescope (JCMT) only recorded a single polarization feed, which could have contributed to systematic polarization leakage in 2018." (Fisher information analysis); "Therefore, JCMT data is retained for the remainder of the analysis." (Fisher information analysis)
- Other facility **CyVerse**: Access to the EHTC_M87-2018_Mar2024 data collection.  
  > "Data accessed from <https://datacommons.cyverse.org/browse/iplant/home/shared/commons_repo/curated/EHTC_M87-2018_Mar2024/>" (Ring ellipticity of M87*)
- External data: M87 black-hole inclination approximately 17 degrees; inclination uncertainty 3 degrees.  
  > "the $\sim17^\circ$ inclination estimated for the M 87 black hole, (cite: Mertens2016)." (Introduction); "a $3^{\circ}$ uncertainty (cite: Mertens2016)" (Origin of the M87* ring ellipticity) [from (cite: Mertens2016)]
- External data: 2018 EHT ring diameter 43.3^{+1.5}_{-3.1} μas.  
  > "The 2018 observations confirmed the persistent structure of the black hole shadow with a consistent ring diameter of $43.3^{+1.5}_{-3.1}$ μas, consistent with the 2017 results (cite: EHTC2024a)." (Introduction) [from (cite: EHTC2024a)]
- External data: Previous ellipticity range τ=0-0.3 and interpretation in terms of accretion turbulence.  
  > "The measured $\tau$ is also consistent with (cite: Tiede2022), who reported $\tau=0-0.3$ and inferred accretion turbulence as the dominant source of the measured ellipticity" (Ring ellipticity of M87*) [from (cite: Tiede2022)]
- External data: Previous 2017 EHT ellipticity τ=0.09^{+0.07}_{-0.06}.  
  > "with (cite: Tiede2024) who reported $\tau=0.09^{+0.07}_{-0.06}$." (Ring ellipticity of M87*); "We note that while this work uses 2018 EHT observations, the above comparisons are made with the works that use 2017 EHT observations." (Ring ellipticity of M87*) [from (cite: Tiede2024)]
- External data: Two GRMHD libraries.  
  > "For this purpose, we used two GRMHD libraries of (cite: Prather_2021) and (cite: Porth_2017)." (Comparison with GRMHD simulations) [from (cite: Prather_2021); (cite: Porth_2017)]
- External data: Non-thermal electron-distribution models with a kappa distribution.  
  > "non-thermal electron distribution (kappa distribution) models were sourced from (cite: Fromm2022; Osorio2022)." (Comparison with GRMHD simulations) [from (cite: Fromm2022; Osorio2022)]
- External data: 86 GHz M87 image ellipticity τ=0.06 ± 0.04.  
  > "(cite: Kim2025) reported $\tau = 0.06 \pm 0.04$ for the image of M87 at 86 GHz" (Summary and conclusions) [from (cite: Kim2025)]
- External data: Maximum gravitational ellipticity approximately 0.03 for inclination 20 degrees and spin a=0.999.  
  > "with $20^{\circ}$ inclination and spin $a=0.999$, the maximum ellipticity reaches only $\sim 0.03$ (cite: Johnson_2020)." (Origin of the M87* ring ellipticity) [from (cite: Johnson_2020)]
- Simulation/model as data: Four training elliptical crescents: m=1, τ=0.187, ξ=[0°,45°,90°,315°].  
  > "The first test selects the Top Set imaging parameter combinations of RML and CLEAN methods using four elliptical crescent models ($m=1$) of $\tau=0.187$ and $\xi=[0^\circ, 45^\circ, 90^\circ, 315^\circ]$." (Geometric tests)
- Simulation/model as data: 42 validation crescents: m=1; τ=[0.0,0.05,0.1,0.15,0.2,0.25,0.3]; ξ=[0°,60°,120°,180°,240°,300°].  
  > "The second test evaluates the ellipticity feature extraction using 42 elliptical crescent models ($m=1$) with $\tau=[0.0, 0.05, 0.1, 0.15, 0.2, 0.25, 0.3]$ and $\xi=[0^\circ, 60^\circ, 120^\circ, 180^\circ, 240^\circ, 300^\circ]$." (Geometric tests)
- Simulation/model as data: 100 GRMHD models for reconstruction tests: 72 thermal, 28 non-thermal; 83 MAD, 17 SANE.  
  > "There were 18 models for each spin value of $-0.94$, $-0.5$, $+0.5$, and $+0.94$ from the thermal models, resulting in 72 thermal models in total." (Comparison with GRMHD simulations); "The remaining 28 models were chosen from the non-thermal models that met the threshold, selecting 7 models for each spin." (Comparison with GRMHD simulations); "Among the 100 selected GRMHD models, 83 are strongly magnetized magnetically arrested disk (MAD) models and 17 are weakly magnetized standard and normal evolution (SANE) models." (Comparison with GRMHD simulations)
- Simulation/model as data: All 299 GRMHD models used for physical-parameter comparisons; snapshots scaled to best-fit mass and blurred by a 12 μas Gaussian.  
  > "We utilize all 299 GRMHD models" (Origin of the M87* ring ellipticity); "For each model, we measure the image ellipticity from the corresponding groundtruth GRMHD snapshot, scaled to the best-fit mass and blurred with a $12$ μas Gaussian" (Origin of the M87* ring ellipticity)

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

- task: RML and Bayesian forward modeling; CLEAN-based deconvolution.  
  > "The forward modeling consists of RML and Bayesian methods, while the inverse modeling employs a CLEAN-based deconvolution method." (Geometric tests)
- deconvolver: CLEAN using Difmap.  
  > "We thank Martin Shepherd for the addition of extra features in the Difmap software that were used for the CLEAN imaging results presented in this paper." (Acknowledgements)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: One Bayesian model: 64×64 raster, 200 μas field of view; another: 6×6 raster.  
  > "The image model is a $64\times64$ raster with a field of view of $200$ μas." (Bayesian imaging methods); "According to these values, $6\times6$ raster has the highest evidence." (Bayesian imaging methods)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: GRMHD groundtruth images convolved with a 12 μas circular Gaussian for comparison with reconstructions.  
  > "The groundtruth GRMHD snapshot images were convolved with 12 μas circular Gaussian to take resolution effect into account." (Comparison with GRMHD simulations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Ellipticity-measurement formalism.  
  > "we follow the formalism based on (cite: Tiede2024)" (Introduction) [from (cite: Tiede2024)]
- Extension of the m-ring model.  
  > "For this analysis, we will use an extension of the m-ring model from (cite: Johnson_2020)." (Fisher information analysis) [from (cite: Johnson_2020)]
- Broad per-scan station gain-amplitude and phase priors for Fisher forecasts.  
  > "The parameter precision estimates assume that the fitting process utilizes complex visibilities as input data, with broad priors imposed on the station gain amplitudes and phases for each scan (cite: Pesce2022)." (Fisher information analysis) [from (cite: Pesce2022)]
- Training-model ellipticity and position-angle choices.  
  > "The values of $\tau$ and $\xi$ are chosen to be consistent with (cite: Tiede2022)." (Geometric tests) [from (cite: Tiede2022)]
- Original RML and deconvolution imaging parameter combinations, subsequently sub-selected.  
  > "For imaging with the RML and deconvolution methods, the imaging parameter combinations were sub-selected from the original ones" (Summary and conclusions) [from not stated]
- VIDA m-ring template: order four in azimuth and order one in width.  
  > "For all feature extraction in this work, we use m-ring of order four in azimuth and order one in width, following (cite: Tiede2022)." (Evaluation with the elliptical crescent models) [from (cite: Tiede2022)]
- Bootstrap method for Spearman correlation coefficients.  
  > "We compute Spearman correlation coefficients between this quantity and the measured image ellipticity, using a bootstrapping method to account for sample variance (cite: Curran_2014; Cheng_2023)." (Origin of the M87* ring ellipticity) [from (cite: Curran_2014; Cheng_2023)]
- Thermodynamic integration and parallel tempering for Bayesian evidence.  
  > "The Bayesian evidence was computed using thermodynamic integration (cite: lartillot2006computing), utilizing the parallel tempering scheme from (cite: syed_non-reversible_2019)." (Bayesian imaging methods) [from (cite: lartillot2006computing); (cite: syed_non-reversible_2019)]
- Gain-amplitude priors inherited from earlier work.  
  > "The amplitude gain priors are the same as used" (Bayesian imaging methods) [from not stated]

### Not stated but needed to reproduce (our reading)

- Mapping of the two ALMA project codes to the selected EHT data products and observing epochs.
- Exact calibrated input files, flags, scan selections, visibility averaging, uncertainties, and calibration provenance.
- Original Top Set parameter lists and the surviving RML/CLEAN combinations, including regularizers, optimization controls, and CLEAN settings.
- Names of the Bayesian pipelines attached to the 6×6 and 64×64 raster descriptions, which are missing in the supplied text.
- Numerical gain-amplitude priors, GMRF hyperpriors, sampler settings, chain lengths, convergence criteria, and random seeds.
- VIDA fitting objective, optimizer or sampler, initialization, parameter bounds, and image preprocessing.
- Weights used to combine methods and bands into weighted medians and 1σ intervals.
- Synthetic-data generator, station-gain corruption values, thermal-noise realizations, and extended-Gaussian parameters.
- GRMHD model and snapshot identifiers, best-fit mass scalings, and the source of the thermal model collection.
- Bootstrap resampling settings and uncertainty treatment for correlations.

## Analysis recipe

1. **Forecast ellipticity precision**: Fisher information analysis of stretched m-rings using April 21, 2018 EHT band 4 sampling.  
  > "We estimate the precision with which the parameters of this model, fitted to data on April 21, 2018 at band 4, can be recovered." (Fisher information analysis); "We employ the above Fisher information approach implemented within the `ngEHTforecast` package" (Fisher information analysis)
   - software: ngEHTforecast
   - parameter: m=1; τ=0 to 0.3; ξ=0 to 360 degrees.  
  > "We use a first-order (i.e., $m=1$) stretched m-ring model" (Fisher information analysis); "For this analysis, we test m-ring models with $\tau$ ranging from $0$ to $0.3$ and $\xi$ ranging from 0 to 360 degrees." (Fisher information analysis)
   - parameter: d=√ab=46 μas; 10 μas circular Gaussian blur; β1=0.23.  
  > "The diameter of the thin elliptical m-rings is $d=\sqrt{ab} = 46$ μas, which is then blurred by a $10$ μas circular Gaussian (cite: Tiede2022)." (Fisher information analysis); "We assume a brightness asymmetry $\beta_1=0.23$ for the m-ring" (Fisher information analysis)
   - assumption: Gaussian posterior; aligned brightness and ellipticity position angles.  
  > "We assume a Gaussian posterior distribution for the parameters" (Fisher information analysis); "For this analysis, we keep the brightness position angle (PA), $\eta$, aligned with the ellipticity PA, $\xi$." (Fisher information analysis)
   - assumption: Complex visibilities with broad station gain-amplitude and phase priors for each scan.  
  > "The parameter precision estimates assume that the fitting process utilizes complex visibilities as input data, with broad priors imposed on the station gain amplitudes and phases for each scan (cite: Pesce2022)." (Fisher information analysis)
   - fitting: Second-order probability expansion around the best-fit location; no explicit m-ring fit to the data.  
  > "This method does not explicitly fit the m-ring model to the data." (Fisher information analysis); "Instead, it performs a second-order expansion of the logarithmic probability density around the best-fit location, providing an estimate of the uncertainty of each of fitted parameter." (Fisher information analysis)
   - validation: Compare forecasts with and without GLT and without JCMT.  
  > "We compute $\sigma_{\tau}$ and $\sigma_{\xi}$ for data with and without GLT to assess its relevance in $(u,v)$-coverage." (Fisher information analysis); "To evaluate this issue, we perform a similar analysis for data without JCMT." (Fisher information analysis)
2. **Select and validate imaging parameters**: Image synthetic elliptical crescents, sub-select the original RML/CLEAN Top Set, and evaluate all methods on 42 further models.  
  > "The data set for the first test is used to sub-select the Top Set imaging parameter combinations for the RML and CLEAN methods." (Imaging parameter selection with the elliptical crescent models); "The second test evaluates the ellipticity feature extraction using 42 elliptical crescent models" (Geometric tests)
   - software: Difmap, VIDA
   - parameter: Training: τ=0.187; ξ=[0°,45°,90°,315°].  
  > "four elliptical crescent models ($m=1$) of $\tau=0.187$ and $\xi=[0^\circ, 45^\circ, 90^\circ, 315^\circ]$." (Geometric tests)
   - parameter: Normalized cross-correlation cutoff 0.75 in bands 3 and 4; original reduced χ²<2.  
  > "Since the latter is already satisfied in the original Top Set (i.e., $\chi^{2}<2$)" (Imaging parameter selection with the elliptical crescent models); "Then the cutoff value is determined as 0.75 for both band 3 and 4, with no variations across the models." (Imaging parameter selection with the elliptical crescent models)
   - assumption: Add a milli-arcsec-scale Gaussian to mimic extended jet emission.  
  > "Before generating the synthetic data, we also add a milli-arcsec scale Gaussian to these geometric models." (Geometric tests); "This Gaussian mimics jet emission on scales of milliarcsecond to arcsecond, to which short intra-site baselines of the EHT are sensitive" (Geometric tests)
   - fitting: Top Set selected by normalized cross correlation with groundtruth, subject to the previously satisfied reduced-χ² criterion.  
  > "The Top Set selection is based on two metrics: (i) the normalized cross correlation" (Imaging parameter selection with the elliptical crescent models); "(ii) the reduced $\chi^{2}$ on the real data." (Imaging parameter selection with the elliptical crescent models)
   - validation: Recover τ and ξ within method-specific resolution limits; test brightness PA perpendicular to ellipticity PA.  
  > "As a result, all imaging methods successfully recover the true $\tau$ and $\xi$ values within its own resolution limit." (Evaluation with the elliptical crescent models); "We chose the $\eta$ to be perpendicular to $\xi$ to test the extreme case." (Additional geometric tests)
3. **Choose a Bayesian raster size**: Survey raster sizes using Bayesian evidence on one synthetic elliptical ring.  
  > "we performed a small survey of different imaging models, changing the number of pixels and computing the Bayesian evidence to find the optimal raster size." (Bayesian imaging methods)
   - parameter: Synthetic ring τ=0.1, ξ=120°; selected raster 6×6.  
  > "Specifically, we considered the elliptical ring with $\tau=0.1$ and $\xi=120^{\circ}$." (Bayesian imaging methods); "According to these values, $6\times6$ raster has the highest evidence." (Bayesian imaging methods)
   - fitting: Bayesian evidence from thermodynamic integration with parallel tempering.  
  > "The Bayesian evidence was computed using thermodynamic integration (cite: lartillot2006computing), utilizing the parallel tempering scheme from (cite: syed_non-reversible_2019)." (Bayesian imaging methods)
   - validation: 6×6 raster correctly recovers τ=0.1 and ξ=120°.  
  > "the true value of $\tau=0.1$ and $\xi=120^{\circ}$ is recovered correctly by the $6\times6$ raster." (Bayesian imaging methods)
4. **Reconstruct the observed emission ring**: Apply geometrically validated imaging pipelines and parameter combinations to the observations.  
  > "Following the geometric tests that validated the imaging pipelines and their parameter combinations for ellipticity measurement, they were applied to the data" (Ring ellipticity of M87*)
   - software: Difmap, AdvancedHMC.jl
   - parameter: One Bayesian model: 64×64 raster over 200 μas; extended Gaussian size fixed at 1000 μas.  
  > "The image model is a $64\times64$ raster with a field of view of $200$ μas." (Bayesian imaging methods); "An extended Gaussian component was used to model the emission on milliarcsecond scales." (Bayesian imaging methods); "The location, position angle, and fractional flux are the model parameters, while the size is fixed as $1000$ μas." (Bayesian imaging methods)
   - parameter: Gains vary every scan; ALMA phase fixed to zero, otherwise the next station alphabetically is the reference.  
  > "We allow gains to vary every scan." (Bayesian imaging methods); "For the gain phases, the gain phase for ALMA is set to be zero." (Bayesian imaging methods); "In the case when ALMA is not present in the scan, we select the next reference station alphabetically." (Bayesian imaging methods)
   - assumption: Image plus extended Gaussian flux fixed at 1.1 Jy, as assumed in network calibration.  
  > "The total flux of the image plus the Gaussian component was fixed to 1.1 Jy as assumed in network calibration for the M87\* data." (Bayesian imaging methods)
   - assumption: First-order GMRF prior on log-ratio pixel intensities, added to a 40 μas Gaussian mean image; variance and correlation length fitted.  
  > "For the raster, we use a first-order Gaussian Markov random field (GMRF) prior on the log-ratio transformed pixel intensities." (Bayesian imaging methods); "The GMRF is added to a mean image which is a $40$ μas Gaussian" (Bayesian imaging methods); "The variance and the correlation length are included as parameters in the model." (Bayesian imaging methods)
   - assumption: Other gain phases: zero-mean von Mises prior with concentration π^{-2}.  
  > "For rest of the gain phase priors, we use von Mises prior with zero mean and a concentration parameter $\pi^{-2}$" (Bayesian imaging methods)
   - fitting: For the detailed 64×64 Bayesian model, fit complex visibilities and amplitude/phase gains; NUTS sampling in AdvancedHMC.jl.  
  > "In this paper, we used complex visibilities as the data products and fit for both amplitude and phase gains (with reference to one station)." (Bayesian imaging methods); "Sampling is performed using (cite: NUTS), in the Julia sampling package `AdvancedHMC.jl`" (Bayesian imaging methods)
   - validation: Cross-compare five imaging methods and both frequency bands.  
  > "we then managed to extract the ellipticity successfully from five different methods that cross-compare the results." (Summary and conclusions); "The measured ellipticities are consistent across all imaging approaches and at both frequency bands 3 and 4" (Ring ellipticity of M87*)
5. **Measure and combine ring features**: Extract τ and ξ with VIDA stretched m-rings; combine methods and bands by weighted median and 1σ error.  
  > "To measure ellipticity and the ellipticity position angle, we use a stretched m-ring template from `VIDA` (cite: Tiede2022b)." (Evaluation with the elliptical crescent models); "The average across all methods and bands is computed by taking weighted median and $1\sigma$ error." (Ring ellipticity of M87*)
   - software: VIDA
   - parameter: m-ring order four in azimuth and order one in width.  
  > "For all feature extraction in this work, we use m-ring of order four in azimuth and order one in width, following (cite: Tiede2022)." (Evaluation with the elliptical crescent models)
   - assumption: τ=1-b/a; ξ is the major-axis angle East of North.  
  > "The ellipticity parameter $\tau$ is defined as $\tau=1-b/a$, where $a$ and $b$ are the major and minor axes of the ellipse, respectively." (Fisher information analysis); "The ellipticity position angle $\xi$ represents the angle of the major axis $a$, measured counterclockwise from the North (East of North)" (Fisher information analysis)
   - fitting: _not stated_
   - validation: Bayesian-only averages agree with averages across all methods.  
  > "These averages are in good agreement with the values obtained by averaging over all methods." (Ring ellipticity of M87*)
6. **Validate reconstruction with GRMHD snapshots**: Generate synthetic data from scaled snapshots, reconstruct with representative RML and Bayesian methods, and compare VIDA features with blurred groundtruth.  
  > "The scaled snapshots were then used to generate synthetic data following the same procedure described in Sect." (Comparison with GRMHD simulations); "We then extracted the ellipticities from these images using `VIDA` and compared them with the true ellipticity." (Comparison with GRMHD simulations)
   - software: VIDA
   - parameter: Select 100 models after an outflow-power threshold exceeding 10^{42} erg/s.  
  > "we selected 218 models with an outflow power exceeding $10^{42}$ erg/s" (Comparison with GRMHD simulations); "After the outflow threshold was applied, we selected 100 models for imaging and feature extraction" (Comparison with GRMHD simulations)
   - parameter: Groundtruth convolved with 12 μas circular Gaussian.  
  > "The groundtruth GRMHD snapshot images were convolved with 12 μas circular Gaussian to take resolution effect into account." (Comparison with GRMHD simulations)
   - assumption: Random snapshots scaled to best-fit mass using observed-to-simulated mass-to-distance ratios.  
  > "Random snapshots were taken from each model and scaled to the best-fit mass" (Comparison with GRMHD simulations); "The scaling factor is a ratio of observed to simulated mass-to-distance ratios." (Comparison with GRMHD simulations)
   - fitting: Estimate effective resolution by comparing reconstructed images with groundtruth blurred using different circular-Gaussian sizes.  
  > "estimated by comparing between the original and blurred groundtruths images with different sizes of circular Gaussian kernel." (Comparison with GRMHD simulations)
   - validation: Reconstruction-minus-truth differences centered at zero in τ and ξ.  
  > "the differences of $\tau$ and $\xi$ between reconstructed images" (Comparison with GRMHD simulations); "and the true values that are centered at zero in both parameters." (Comparison with GRMHD simulations)
7. **Identify the physical origin of ellipticity**: Measure all 299 GRMHD groundtruth snapshots; compare physical parameters and non-ring flux fraction with ellipticity using bootstrapped Spearman correlations.  
  > "We utilize all 299 GRMHD models" (Origin of the M87* ring ellipticity); "We compute Spearman correlation coefficients between this quantity and the measured image ellipticity, using a bootstrapping method to account for sample variance (cite: Curran_2014; Cheng_2023)." (Origin of the M87* ring ellipticity)
   - software: VIDA
   - parameter: Non-ring flux fraction: subtract best-fit circular Gaussian ring, zero negative residuals, divide remaining positive flux by total flux.  
  > "we define a “non-ring flux fraction” by subtracting the best-fit circular Gaussian ring (using `VIDA`) from each GRMHD image and setting negative residuals to zero." (Origin of the M87* ring ellipticity); "The ratio of the remaining positive flux to the total flux defines the non-ring flux fraction." (Origin of the M87* ring ellipticity)
   - assumption: Groundtruth snapshots scaled to best-fit mass and blurred with a 12 μas Gaussian.  
  > "For each model, we measure the image ellipticity from the corresponding groundtruth GRMHD snapshot, scaled to the best-fit mass and blurred with a $12$ μas Gaussian" (Origin of the M87* ring ellipticity)
   - fitting: Best-fit circular Gaussian ring using VIDA; bootstrapped Spearman coefficients.  
  > "subtracting the best-fit circular Gaussian ring (using `VIDA`)" (Origin of the M87* ring ellipticity); "We compute Spearman correlation coefficients between this quantity and the measured image ellipticity, using a bootstrapping method to account for sample variance (cite: Curran_2014; Cheng_2023)." (Origin of the M87* ring ellipticity)
   - validation: Observed ellipticity falls within the GRMHD distribution's median and 68% intervals; visually inspect correlation outliers.  
  > "the observed ellipticity is consistent with the distribution of all 299 GRMHD models, falling within their median and 68% confidence intervals." (Origin of the M87* ring ellipticity); "We note that upon visual inspection, it does not appear that the outliers appear from transient flux eruption events." (Origin of the M87* ring ellipticity)
8. **Quantify resolution bias**: Blur geometric elliptical m-rings with circular Gaussians, measure ellipticity using VIDA, and fit its dependence on blur width.  
  > "we used geometric elliptical m-ring models with $\xi=120^{\circ}$ and $\tau_{0}=[0.05, 0.1, 0.15, 0.2, 0.25, 0.3]$ and measured the ellipticity with `VIDA` by blurring the models with different circular Gaussian FWHM ($\alpha$)." (The effect of resolution on the measured ellipticity)
   - software: VIDA
   - parameter: ξ=120°; τ0=[0.05,0.1,0.15,0.2,0.25,0.3].  
  > "geometric elliptical m-ring models with $\xi=120^{\circ}$ and $\tau_{0}=[0.05, 0.1, 0.15, 0.2, 0.25, 0.3]$" (The effect of resolution on the measured ellipticity)
   - fitting: Gaussian fit τ=A exp[-(α-μ)²/(2σ²)]; obtained μ=0 and A=τ0.  
  > "We then fitted a Gaussian to each measured $\tau-\alpha$ data" (The effect of resolution on the measured ellipticity); "\tau = A * e^{-(\alpha-\mu)^2/(2\sigma^2)}" (The effect of resolution on the measured ellipticity); "we get $\mu=0$ and $A=\tau_{0}$ for all the cases" (The effect of resolution on the measured ellipticity)
   - validation: Fit evaluated across the different input ellipticities; data extend only to one fitted σ.  
  > "where $\sigma$ was measured as $21.5\pm0.5$ μas for all the cases." (The effect of resolution on the measured ellipticity); "We note that we have data only up to one $\sigma$ of the fitted Gaussians." (The effect of resolution on the measured ellipticity)

## Software

- **ngEHTforecast** git commit 115bf73: Fisher information forecasts.  
  > "We employ the above Fisher information approach implemented within the `ngEHTforecast` package" (Fisher information analysis); "<https://github.com/aeb/ngEHTforecast>, accessed with the git commit `115bf73`." (Fisher information analysis)
- **VIDA** : Stretched m-ring feature extraction and circular Gaussian ring fits for non-ring flux.  
  > "To measure ellipticity and the ellipticity position angle, we use a stretched m-ring template from `VIDA` (cite: Tiede2022b)." (Evaluation with the elliptical crescent models); "subtracting the best-fit circular Gaussian ring (using `VIDA`)" (Origin of the M87* ring ellipticity)
- **Difmap** : CLEAN imaging.  
  > "We thank Martin Shepherd for the addition of extra features in the Difmap software that were used for the CLEAN imaging results presented in this paper." (Acknowledgements)
- **eht-imaging** : RML imaging; named in the cited software reference.  
  > "For RML imaging, we use (cite: Chael_2016; Chael_2018; Chael_2019) and (cite: Akiyama_2017a; Akiyama_2017b; Akiyama_2019)." (Geometric tests); "eht-imaging: v1.1.0: Imaging interferometric data with regularized maximum likelihood" (Summary and conclusions)
- **SMILI** : RML imaging; named in the cited software reference.  
  > "For RML imaging, we use (cite: Chael_2016; Chael_2018; Chael_2019) and (cite: Akiyama_2017a; Akiyama_2017b; Akiyama_2019)." (Geometric tests); "SMILI: Sparse Modeling Imaging Library for Interferometry" (Summary and conclusions)
- **AdvancedHMC.jl** : NUTS sampling for Bayesian imaging.  
  > "Sampling is performed using (cite: NUTS), in the Julia sampling package `AdvancedHMC.jl`" (Bayesian imaging methods)
- **DiFX** : EHT-specific use acknowledged; processing role not stated.  
  > "We would like to thank A. Deller and W. Brisken for EHT-specific support with the use of DiFX." (Acknowledgements)
- **CyVerse** : Data access and computing resources.  
  > "Data accessed from <https://datacommons.cyverse.org/browse/iplant/home/shared/commons_repo/curated/EHTC_M87-2018_Mar2024/>" (Ring ellipticity of M87*); "This work used the Extreme Science and Engineering Discovery Environment (XSEDE), supported by NSF grant ACI-1548562, and CyVerse, supported by NSF grants DBI-0735191, DBI-1265383, and DBI-1743442." (Acknowledgements)
- **XSEDE** : Computing resources.  
  > "This work used the Extreme Science and Engineering Discovery Environment (XSEDE)" (Acknowledgements)
- **OSG Consortium** : Computing services.  
  > "This research was done using services provided by the OSG Consortium (cite: osg07; osg09)" (Acknowledgements)
- **NASA’s Astrophysics Data System** : Research service; specific use not stated.  
  > "This research has made use of NASA’s Astrophysics Data System." (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Emission-ring ellipticity, all methods and both bands | 0.08 | +0.03/-0.02 | dimensionless | 5 | yielding an average ellipticity of $\tau=0.08^{+0.03}_{-0.02}$. |
| Ellipse position angle, all methods and both bands | 50.1 | +6.2/-7.6 | degrees | 5 | The average position angle of the ellipse is $\xi=50.1^{+6.2}_{-7.6}$ degrees |
| Emission-ring ellipticity, Bayesian methods only | 0.08 | +0.02/-0.02 | dimensionless | 5 | we compute the average $\tau = 0.08 ^{+0.02}_{-0.02}$ and $\xi = 44.4^{+5.8}_{-6.4}$ only from these methods. |
| Ellipse position angle, Bayesian methods only | 44.4 | +5.8/-6.4 | degrees | 5 | we compute the average $\tau = 0.08 ^{+0.02}_{-0.02}$ and $\xi = 44.4^{+5.8}_{-6.4}$ only from these methods. |
| Precision improvement from GLT | ~3-5 | not stated | dimensionless | 1 | This analysis shows that the inclusion of GLT improves the precision in constraining ellipticity parameters by $\sim3-5$ times. |
| Effect of excluding JCMT on marginalized ellipticity uncertainties | <10% | not stated | dimensionless | 1 | removing JCMT has a minimal effect ($<10\%$) on the marginalized uncertainties of $\tau$ and $\xi$. |
| Effective super-resolution for GRMHD comparisons | 12 | not stated | μas | 6 | The groundtruth GRMHD snapshot images were convolved with 12 μas circular Gaussian to take resolution effect into account.; This is an average from results for all 100 GRMHD models |
| All-model ellipticity versus electron-distribution function: Spearman C | -0.31 | not stated | dimensionless | 7 | / Models / eDF / Magnetic Field State / Spin /  /  /; / All / $C= -0.31, p=0.05$ / $C=-0.09, p=0.44$ / $C=-0.12, p=0.22$ / $C=0.20, p=0.04$ / $C=-0.02, p=0.50$ / |
| All-model ellipticity versus electron-distribution function: p-value | 0.05 | not stated | dimensionless | 7 | / Models / eDF / Magnetic Field State / Spin /  /  /; / All / $C= -0.31, p=0.05$ / $C=-0.09, p=0.44$ / $C=-0.12, p=0.22$ / $C=0.20, p=0.04$ / $C=-0.02, p=0.50$ / |
| All-model ellipticity versus magnetic field state: Spearman C | -0.09 | not stated | dimensionless | 7 | / Models / eDF / Magnetic Field State / Spin /  /  /; / All / $C= -0.31, p=0.05$ / $C=-0.09, p=0.44$ / $C=-0.12, p=0.22$ / $C=0.20, p=0.04$ / $C=-0.02, p=0.50$ / |
| All-model ellipticity versus magnetic field state: p-value | 0.44 | not stated | dimensionless | 7 | / Models / eDF / Magnetic Field State / Spin /  /  /; / All / $C= -0.31, p=0.05$ / $C=-0.09, p=0.44$ / $C=-0.12, p=0.22$ / $C=0.20, p=0.04$ / $C=-0.02, p=0.50$ / |
| All-model ellipticity versus spin: Spearman C | -0.12 | not stated | dimensionless | 7 | / Models / eDF / Magnetic Field State / Spin /  /  /; / All / $C= -0.31, p=0.05$ / $C=-0.09, p=0.44$ / $C=-0.12, p=0.22$ / $C=0.20, p=0.04$ / $C=-0.02, p=0.50$ / |
| All-model ellipticity versus spin: p-value | 0.22 | not stated | dimensionless | 7 | / Models / eDF / Magnetic Field State / Spin /  /  /; / All / $C= -0.31, p=0.05$ / $C=-0.09, p=0.44$ / $C=-0.12, p=0.22$ / $C=0.20, p=0.04$ / $C=-0.02, p=0.50$ / |
| Gaussian scale σ of ellipticity suppression by image blurring | 21.5 | ±0.5 | μas | 8 | where $\sigma$ was measured as $21.5\pm0.5$ μas for all the cases. |

## Qualitative findings

- Measured ellipticities agree across imaging approaches and EHT bands 3 and 4.  
  > "The measured ellipticities are consistent across all imaging approaches and at both frequency bands 3 and 4" (Ring ellipticity of M87*)
- No statistically significant correlation between GRMHD image ellipticity and spin or magnetic field state.  
  > "there is no statistically significant correlation between spin and the measured ellipticity in full GRMHD images." (Origin of the M87* ring ellipticity); "also shows no significant correlation between ellipticity and magnetic field state (SANE and MAD)" (Origin of the M87* ring ellipticity)
- Non-ring flux fraction correlates positively with ellipticity.  
  > "reveals a positive correlation between the non-ring flux fraction and ellipticity." (Origin of the M87* ring ellipticity)
- Turbulent astrophysical emission is the dominant explanation for the measured ellipticity.  
  > "This supports the conclusion that emission ellipticity, driven by turbulent accretion structures outside the ring, is the dominant contributor to ellipticity in GRMHD images." (Origin of the M87* ring ellipticity); "to explain the measured ellipticity of M87, the astrophysical effects such as turbulent accretion flow are required." (Summary and conclusions)

## Claim tuples

- H: The emission-ring ellipticity is recoverable and is not solely an imaging artifact. | E: Validate imaging methods on synthetic geometric and GRMHD data, then measure the observed ring across five methods and two bands. | R: τ=0.08^{+0.03}_{-0.02}; ξ=50.1^{+6.2}_{-7.6} degrees. | F: The measured ellipticity is real and consistent across methods. | **supported**
- H: Adding GLT improves ellipticity constraints. | E: Compare Fisher forecasts with and without GLT baselines. | R: Ellipticity-parameter precision improves by approximately 3-5 times. | F: Additional GLT coverage substantially improves the measurement. | **supported**
- H: Spin-induced gravitational ellipticity dominates the observed ring shape. | E: Compare the observation with gravitational expectations and GRMHD models spanning spin. | R: No statistically significant spin-ellipticity correlation in full GRMHD images. | F: Spin contributes but does not dominate the observed ellipticity. | **refuted**
- H: Asymmetric non-ring emission drives image ellipticity. | E: Subtract VIDA circular Gaussian ring fits from GRMHD images and correlate the positive residual flux fraction with ellipticity. | R: Non-ring flux fraction is positively correlated with ellipticity. | F: Turbulent accretion structures provide the dominant emission-ellipticity contribution. | **supported**

## Reasoning

- Why this data: Use higher-frequency EHT bands containing GLT, and April 21 with the most participating stations.  
  > "The GLT participated only in the band 3 and 4, so we focus on data from the higher frequency bands in this study." (Introduction); "Among the four observing days, we use April 21, which had the highest number of participating stations." (Introduction)
- Why this method: Validate imaging and feature extraction against known ellipticities and position angles before applying them to observations.  
  > "Before analyzing the data, two sets of tests with geometric models were conducted to evaluate the accuracy of the imaging and feature extraction methods in recovering the truth values and assessing potential biases in the imaging methods." (Geometric tests)
- Alternative: Exclude JCMT to test possible single-feed polarization leakage; retain it because forecast effects are below 10%.  
  > "removing JCMT has a minimal effect ($<10\%$) on the marginalized uncertainties of $\tau$ and $\xi$." (Fisher information analysis); "Therefore, JCMT data is retained for the remainder of the analysis." (Fisher information analysis)
- Alternative: Select 6×6 over 5×5 and 7×7 Bayesian rasters by evidence.  
  > "| Raster size | $5\times5$ | $6\times6$ | $7\times7$ |" (Table 2); "| Evidence    |  $-2890$   |  $-2885$   |  $-2889$   |" (Table 2); "According to these values, $6\times6$ raster has the highest evidence." (Bayesian imaging methods)
- Alternative: Tilted accretion disks or exotic spacetime remain possible additional sources of non-circularity.  
  > "It is worth noting that the additional non-circularity by the inclined black hole (e.g., tilted accretion disk) or exotic spacetime are not completely ruled out." (Summary and conclusions)
- Alternative: Long-term temporal averaging and space VLBI proposed to isolate gravitational ellipticity.  
  > "allowing for temporal averaging of the turbulent effects, thereby enabling the underlying gravitational signature to emerge more clearly." (Summary and conclusions); "The second approach entails space VLBI observations, which would provide the necessary angular resolution to detect the photon ring (cite: Gralla_2019; Johnson_2020)." (Summary and conclusions)
- How they decided it was enough: Top Set cross-correlation cutoff 0.75; synthetic-model recovery judged within each method's resolution limit.  
  > "Then the cutoff value is determined as 0.75 for both band 3 and 4, with no variations across the models." (Imaging parameter selection with the elliptical crescent models); "As a result, all imaging methods successfully recover the true $\tau$ and $\xi$ values within its own resolution limit." (Evaluation with the elliptical crescent models)
- Limitation (authors): North-south position angles are less constrained by (u,v)-coverage.  
  > "the results indicate that $\xi$ is less constrained at $0^\circ$ and $180^\circ$ due to relatively poorer ($u,v$)-coverage in these directions" (Evaluation with the elliptical crescent models)
- Limitation (authors): Resolution suppresses measured ellipticity; RML and deconvolution can underestimate extreme ellipticities.  
  > "measured ellipticities from reconstructed images that are up to $\sim30\,\%$ lower than the true value are considered acceptable" (Evaluation with the elliptical crescent models); "the RML and deconvolution imaging methods tend to underestimate the ellipticity for models with extreme ellipticities in all 42 tests." (Evaluation with the elliptical crescent models)
- Limitation (authors): No strong constraints on physical parameters, including spin.  
  > "no strong constraints on the parameters including the spin are yet found." (Summary and conclusions)
- Limitation (authors): Turbulent direct-image emission limits gravitational ellipticity measurements with the current ground-based array.  
  > "With the current ground-based array, our ability to precisely measure the ellipticity of the emission ring is constrained by the dominance of turbulent astrophysical effects associated with the direct image (cite: Gralla2020a; Johnson_2020)." (Summary and conclusions)
- Limitation (authors): The resolution-bias Gaussian fit is sampled only to one fitted σ.  
  > "We note that we have data only up to one $\sigma$ of the fitted Gaussians." (The effect of resolution on the measured ellipticity)
- Caveat (inferred, ours): The supplied conversion omits several pipeline names, inherited references, and physical-parameter labels, preventing an unambiguous implementation.
- Caveat (inferred, ours): A raster-size choice tested on one synthetic geometry may not establish optimality across all observed or simulated morphologies.
- Caveat (inferred, ours): Cross-method agreement uses shared observations and feature extraction; it is not fully independent validation.
- Caveat (inferred, ours): A single observing day and selected random GRMHD snapshots limit temporal and model-population generality.
- Caveat (inferred, ours): The non-ring-flux correlation supports an emission origin but does not uniquely establish turbulence as the causal mechanism.
- Caveat (inferred, ours): The bootstrap implementation and weighted-combination rules are insufficiently specified to reproduce reported uncertainties exactly.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Data accessed from the CyVerse EHTC_M87-2018_Mar2024 collection; product contents not stated.  
  > "Data accessed from <https://datacommons.cyverse.org/browse/iplant/home/shared/commons_repo/curated/EHTC_M87-2018_Mar2024/>" (Ring ellipticity of M87*)
- Code: ngEHTforecast GitHub URL and accessed commit provided.  
  > "<https://github.com/aeb/ngEHTforecast>, accessed with the git commit `115bf73`." (Fisher information analysis)
- Code: AdvancedHMC.jl GitHub URL provided.  
  > "<https://github.com/TuringLang/AdvancedHMC.jl>" (Bayesian imaging methods)
- Missing: An explicit public-access statement and exact calibrated data-product manifest.
- Missing: Paper-specific scripts, environment versions, imaging configurations, and surviving Top Set lists.
- Missing: Unambiguous pipeline names and references omitted from the supplied conversion.
- Missing: Complete Bayesian priors, sampling controls, diagnostics, and output posterior samples.
- Missing: VIDA fit configuration and weights for the reported combined statistics.
- Missing: GRMHD library files, model/snapshot identifiers, mass scalings, and synthetic corruption realizations.
- Missing: Bootstrap settings and full physical-parameter labels for the correlation table.
- Data volume (inferred): Cannot estimate from the supplied text: visibility counts, integration times, bandwidths, and simulation file sizes are absent.
- Score (inferred): 5/5, 5/10: numeric answer keys, project codes, a data-access link, and substantial validation are supplied, but essential imaging configurations, model identifiers, priors, and combination rules are missing.
- Rediscovery candidate: no, Main results are numeric, but public availability is not explicitly stated and the supplied recipe lacks essential configurations and model provenance.

## Links

- Method: (cite: Tiede2024) (Ellipticity formalism and motivation for the Bayesian raster survey.)
- Method: (cite: Johnson_2020) (m-ring model and gravitational-ellipticity comparison.)
- Method: (cite: Pesce2022) (Fisher forecasts with station-gain nuisance parameters.)
- Method: (cite: Tiede2022) (Geometric training choices and feature-extraction template orders.)
- Method: (cite: Tiede2022b) (VIDA stretched m-ring feature extraction.)
- Method: (cite: Chael_2016; Chael_2018; Chael_2019) (RML imaging.)
- Method: (cite: Akiyama_2017a; Akiyama_2017b; Akiyama_2019) (RML imaging and SMILI.)
- Method: (cite: Tiede2022_Comrade) (Bayesian imaging method; package name absent from the supplied prose.)
- Method: (cite: Broderick_2020a; Broderick_2020b) (Bayesian imaging method; package name absent from the supplied prose.)
- Method: (cite: Shepherd_1997; Shepherd_2011) (CLEAN-based deconvolution and Difmap.)
- Method: (cite: Curran_2014; Cheng_2023) (Bootstrapped Spearman correlations.)
- Method: (cite: lartillot2006computing) (Thermodynamic integration for Bayesian evidence.)
- Method: (cite: syed_non-reversible_2019) (Parallel tempering for evidence computation.)
- Method: (cite: NUTS) (Bayesian posterior sampling.)
- Method: (cite: Moscibrodzka2016) (Definitions of ion-to-electron temperature-ratio parameters.)
- Related: Event Horizon Telescope (EHT)
- Related: next-generation EHT (ngEHT)
- Related: Event Horizon Imager (EHI)
- Related: Terahertz Exploration and Zooming-in for Astrophysics (THEZA)
- Related: Black Hole Explorer (BHEX)

## Checks

```json
{
 "quotes": 200,
 "quotes_ok": 200,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 139,
  "stated": 108,
  "rate": 0.777
 },
 "evidence_ok": true
}
```
