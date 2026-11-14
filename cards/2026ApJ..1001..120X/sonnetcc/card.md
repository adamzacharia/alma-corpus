# Disk Wind Feedback from High-mass Protostars. V. Application of Multimodal Machine Learning to Characterize Outflow Properties

`2026ApJ..1001..120X` | The Astrophysical Journal 2026 | first author: Xu, Duo | arXiv: 2601.21100 | DOI: 10.3847/1538-4357/ae50fa

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: star_formation
- Question: Can a multi-modal deep learning model using CO spatial and spectral information infer protostellar mass, inclination and position angle of high-mass protostellar outflows, and how does it behave on real ALMA data?  
  > "We present a multi-modal deep learning framework that jointly leverages spatial and spectral information from CO observations to infer protostellar mass, inclination, and position angle" (abstract)
- Target **G35.20-0.74N (G35.20)**: coordinates _not stated_; z/distance 2.2 kpc  
  > "Their distances are 2.2 kpc, 8.4 kpc, and 2.1 kpc, respectively." (4 Application to Real ALMA-Observed Protostellar Outflows and Uncertainty Assessment); distance from _not stated_
- Target **G45.47+0.05 (G45.47)**: coordinates _not stated_; z/distance 8.4 kpc  
  > "Their distances are 2.2 kpc, 8.4 kpc, and 2.1 kpc, respectively." (4 Application to Real ALMA-Observed Protostellar Outflows and Uncertainty Assessment); distance from _not stated_
- Target **G339.88-1.26 (G339.88)**: coordinates _not stated_; z/distance 2.1 kpc  
  > "Their distances are 2.2 kpc, 8.4 kpc, and 2.1 kpc, respectively." (4 Application to Real ALMA-Observed Protostellar Outflows and Uncertainty Assessment); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.01454.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C36-3  
  > "obtained with ALMA in the C36-3 configuration in 2016 (project ID: 2015.1.01454.S)" (4 Application to Real ALMA-Observed Protostellar Outflows and Uncertainty Assessment)
- baselines: 15 m to 463 m  
  > "with baselines ranging from 15 m to 463 m and an on-source integration time of 3.5 minutes per target" (4 Application to Real ALMA-Observed Protostellar Outflows and Uncertainty Assessment)
- angular resolution: major axes 0.87'', 0.90'', 0.93''; minor axes 0.83'', 0.84'', 0.74'' (G35.20, G45.47, G339.88)  
  > "The synthesized beams have major axes of 0.87$''$, 0.90$''$, and 0.93$''$, and minor axes of 0.83$''$, 0.84$''$, and 0.74$''$ for G35.20, G45.47, and G339.88, respectively." (4 Application to Real ALMA-Observed Protostellar Outflows and Uncertainty Assessment)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 3.5 minutes per target  
  > "with baselines ranging from 15 m to 463 m and an on-source integration time of 3.5 minutes per target" (4 Application to Real ALMA-Observed Protostellar Outflows and Uncertainty Assessment)
- observing dates: 2016  
  > "obtained with ALMA in the C36-3 configuration in 2016 (project ID: 2015.1.01454.S)" (4 Application to Real ALMA-Observed Protostellar Outflows and Uncertainty Assessment)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- External data: SED-fitting protostellar masses and inclinations for the three sources, used for comparison with the ML estimates  
  > "estimated protostellar masses of 13-28 $M_\odot$ for G35.20, 23-53 $M_\odot$ for G45.47, and 11-42 $M_\odot$ for G339.88 based on SED fitting" (4.2 Comparison with Previous Estimates) [from (cite: 2023ApJ...942....7F)]
- Simulation/model as data: 3D ideal MHD disk wind simulations of a massive protostar (Staff et al. 2023, Paper II), same snapshots as Paper III, protostellar masses 2, 4, 8, 12, 16, 20, 24 Msun  
  > "We utilize the 3D ideal MHD simulations from (cite: 2023ApJ...947...40S), which model a disk wind outflow from a massive protostar." (2.1 Magnetohydrodynamics Simulations); "we adopt the same simulation snapshots as those used by (cite: 2024ApJ...966..117X)" (2.1 Magnetohydrodynamics Simulations)

## Processing

### Calibration

- pipeline or manual: standard pipeline calibration in CASA  
  > "After standard pipeline calibration, self-calibration using the continuum was applied to the CO line data" (4 Application to Real ALMA-Observed Protostellar Outflows and Uncertainty Assessment)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: self-calibration using the continuum applied to the CO line data  
  > "After standard pipeline calibration, self-calibration using the continuum was applied to the CO line data" (4 Application to Real ALMA-Observed Protostellar Outflows and Uncertainty Assessment)

### Imaging

- task: tclean in CASA  
  > "imaging was carried out with the tclean task using Briggs weighting with robust = 0.5" (4 Application to Real ALMA-Observed Protostellar Outflows and Uncertainty Assessment)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "imaging was carried out with the tclean task using Briggs weighting with robust = 0.5" (4 Application to Real ALMA-Observed Protostellar Outflows and Uncertainty Assessment)
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

- Full observational details of the real ALMA data deferred to original publications  
  > "We refer readers to the original publications for full observational details." (4 Application to Real ALMA-Observed Protostellar Outflows and Uncertainty Assessment) [from original publications of the sources (cite: 2022ApJ...936...68Z; 2019ApJ...886L...4Z; 2019ApJ...873...73Z)]
- Simulation setup, code and parameters  
  > "A comprehensive description of the MHD simulation setup, code, and parameters can be found in (cite: 2023ApJ...947...40S)." (2.1 Magnetohydrodynamics Simulations) [from (cite: 2023ApJ...947...40S)]
- Dust temperature calculation for the radiative transfer  
  > "dust temperatures are calculated as described in (cite: 2024ApJ...966..117X)" (2.2 Synthetic Observations) [from (cite: 2024ApJ...966..117X)]
- Simulated ALMA observing setup (C36-3 configuration, 210 s integration) matched to the real observations; insensitivity to distance supported by Paper III  
  > "making the training process largely insensitive to distance, as also supported by (cite: 2024ApJ...966..117X)" (2.2 Synthetic Observations) [from (cite: 2024ApJ...966..117X)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals, number of iterations and reference channels for the real ALMA CO data
- Line-free channels / continuum subtraction, channel width, cell size, image size, cleaning threshold and masks for the tclean imaging of the real data
- Systemic velocity (v_lsr) adopted for each real source and the velocity cutoffs used to make red/blue integrated-intensity maps from real data
- CASA version and pipeline version
- Calibrators and flux scale; ALMA band and spectral setup for 2015.1.01454.S
- Sky coordinates of the three targets and source of the adopted distances
- simalma parameters (antenna list, thermal noise settings, spectral resolution, pointing, cell size) for the synthetic observations
- Learning rates, batch size, optimizer, scheduler and random seeds for each training stage; cross-attention and MLP dimensions; 1D CNN layer specification
- How the 224x224 images were cropped/regridded from the simulated and observed images
- Public availability of the MHD snapshots, synthetic data cubes and trained model weights/code

## Analysis recipe

1. **Generate synthetic 12CO(2-1) data from MHD simulations**: RADMC-3D non-LTE radiative transfer on the mirrored MHD snapshots, 20 viewing angles  
  > "We use the publicly available radiative transfer code radmc-3d (cite: 2012ascl.soft02015D) to generate synthetic" (2.2 Synthetic Observations); "Level populations are computed based on local density and temperature, assuming that gas and dust temperatures are coupled." (2.2 Synthetic Observations)
   - software: RADMC-3D
   - parameter: 20 inclinations, cosine uniformly spaced between 0.025 and 0.975 (about 12.8 to 88.6 deg)  
  > "where the inclination angles are sampled by uniformly spacing the cosine of inclination angles between 0.025 and 0.975" (2.2 Synthetic Observations)
   - parameter: Synthetic source distances 500 pc, 1 kpc, 2 kpc (2 kpc fiducial)  
  > "we include synthetic sources at distances of 500 pc, 1 kpc, and 2 kpc, using 2 kpc as the fiducial setup." (2.2 Synthetic Observations)
   - assumption: Constant 12CO abundance 1e-4 relative to H2; gas-to-dust mass ratio 100; gas and dust temperatures coupled  
  > "we assume a constant $^{12}$CO abundance of $10^{-4}$ relative to $H_2$ and a gas-to-dust mass ratio of 100" (2.2 Synthetic Observations)
   - fitting: _not stated_
   - validation: Synthetic spectra shown to reproduce features of real outflows in Paper III  
  > "The resulting synthetic spectra were shown to closely reproduce the features of real ALMA-observed protostellar outflows." (1 Introduction)
2. **Simulate ALMA observations of the synthetic cubes**: CASA simalma post-processing with the C36-3 configuration and 210 s integration matching the real data  
  > "To simulate ALMA observations, we post-process the synthetic line data using CASA" (2.2 Synthetic Observations); "adopting the same C36-3 array configuration and 210-second integration time as used in the real observations discussed in" (2.2 Synthetic Observations)
   - software: CASA, simalma
   - fitting: _not stated_
   - validation: _not stated_
3. **Build ML inputs (images, spectra) with augmentation**: Three-channel image (blue, red, total integrated intensity, normalized 0-1) plus a normalized spectrum clipped at +/-50 km/s; randomized velocity cutoff; data-loader augmentations  
  > "integrated intensities, along with the total integrated intensity, each normalized between 0 and 1." (2.2 Synthetic Observations); "we employ a randomized velocity cutoff strategy." (2.2 Synthetic Observations); "The corresponding spectrum is clipped at $\pm$50 km/s and similarly normalized." (2.2 Synthetic Observations)
   - parameter: Velocity exclusion |v - v_lsr| > 3, 5, 8 or 10 km/s  
  > "which mimics the filtering of low-velocity gas while preserving the large-scale structure of the outflow lobes" (2.2 Synthetic Observations)
   - parameter: Training beam-convolution sigma between 0.75 and 2.0 pixels for 224x224 inputs; zoom up to 20%; rotations 0-360 deg  
  > "convolving the images with random beam sizes ($\sigma$ between 0.75 and 2.0 pixels for 224$\times$224 inputs)" (2.4 Multi-Modal Machine Learning Framework)
   - fitting: _not stated_
   - validation: Visual inspection that morphologies are robust across velocity cutoffs  
  > "Visual inspection confirms that the resulting morphologies are robust across these ranges" (2.2 Synthetic Observations)
4. **Train multi-modal network for mass, inclination, position angle**: Image encoder (pretrained ResNet50/152 or ViT_B_16/ViT_L_16) plus from-scratch 1D CNN spectrum encoder, cross-attention fusion, MLP head predicting Gaussian mean and log-variance; progressive fine-tuning  
  > "we adopt widely used pretrained architectures, including ResNet50 (cite: 2016cvpr.confE...1H) and ViT_L_16 (cite: 2020arXiv201011929D)" (2.3 Multi-Modal Machine Learning Framework); "The spectrum encoder is designed from scratch using a 1D CNN" (2.3 Multi-Modal Machine Learning Framework); "we employ a cross-attention mechanism that fuses spatial and spectral features" (2.3 Multi-Modal Machine Learning Framework)
   - parameter: Train on 1 kpc and 2 kpc models; validate and test on 500 pc models  
  > "synthetic models placed at 1 kpc and 2 kpc are used exclusively for training, while models placed at 500 pc are reserved entirely for validation and testing." (2.3 Multi-Modal Machine Learning Framework)
   - parameter: Three stages: freeze image encoder; unfreeze last image-encoder layer after 10 epochs without validation improvement; unfreeze all; stop after 10 further epochs without improvement; best validation model kept  
  > "After the validation loss fails to improve for 10 consecutive epochs, we unfreeze the last layer of the image encoder and continue training with a lower learning rate." (2.3 Multi-Modal Machine Learning Framework); "We save the model with the best validation performance as our fiducial model." (2.3 Multi-Modal Machine Learning Framework)
   - parameter: Random masking of spectrum segments (set to zero) during training; PA represented as sine and cosine  
  > "During training, random segments of the input spectrum are set to zero, mimicking missing or corrupted spectral channels that often arise in observations." (2.3 Multi-Modal Machine Learning Framework); "we represent it as a two-component vector using sine and cosine values." (2.3 Multi-Modal Machine Learning Framework)
   - fitting: Gaussian negative log-likelihood loss on predicted mean and log-variance; optimizer and priors not stated  
  > "The model is trained by minimizing the Gaussian Negative Log-Likelihood (NLL) of the true value" (2.3 Multi-Modal Machine Learning Framework)
   - validation: Held-out validation set with early stopping; restricted-training stress test excluding 12 Msun and five inclinations  
  > "we deliberately withhold specific physical configurations from the training phase to evaluate the model’s performance on entirely unseen data." (2.3 Multi-Modal Machine Learning Framework)
5. **Evaluate on synthetic tests and interpret the network**: Restricted-set generalization test, full-space test on 500 pc data, Gaussian smoothing robustness test, spectrum ablation, Smooth Grad-CAM++, Integrated Gradients with mean baseline, occlusion sensitivity  
  > "we employ three complementary interpretability techniques: Smooth Grad-CAM++, Integrated Gradients (IG), and Occlusion Sensitivity Analysis." (3.2 Interpretable Analysis of Physical Feature Contributions in the Multi-Modal Network); "we perform a controlled ablation test to isolate the contribution of the spectral modality." (3.1 Assessing Model Performance)
   - software: Smooth Grad-CAM++, Integrated Gradients
   - parameter: Test set of 6,720 samples (7 masses x 20 inclinations x 4 velocity cutoffs x 12 position angles at 30 deg)  
  > "The final testing set comprises 6,720 distinct samples" (2.3 Multi-Modal Machine Learning Framework)
   - parameter: Grad-CAM++ averaged over N=10 noisy inputs; IG with 30-50 interpolation steps and mean image/spectrum baseline  
  > "by averaging Grad-CAM++ maps over multiple noisy realizations of the input ($N=10$)" (3.2.1 Smooth Grad-CAM++ Visualization); "By integrating gradients over 30-50 interpolation steps" (3.2.2 Integrated Gradients with Mean Baseline)
   - fitting: _not stated_
   - validation: Three attribution methods agree that spatial features dominate  
  > "The strong agreement across Smooth Grad-CAM++, Integrated Gradients, and Occlusion Sensitivity Analysis" (3.2.3 Occlusion Sensitivity Analysis)
6. **Apply trained models to real ALMA CO images with rotation-based uncertainty**: Rotate each outflow image in 3 deg steps (120 versions), run all through the trained models, average means and combine mean aleatoric variance with dispersion of means (epistemic)  
  > "we rotate the outflow image by steps of 3$^{\circ}$, producing 120 rotated versions that are independently passed through the trained models." (4.1 Rotation-Based Evaluation and Uncertainty Decomposition)
   - assumption: Physical quantities such as mass and inclination should be invariant under image rotation  
  > "Ideally, physical quantities such as mass and inclination should be invariant under image rotation." (4.1 Rotation-Based Evaluation and Uncertainty Decomposition)
   - fitting: _not stated_
   - validation: Qualitative side-by-side comparison of real maps with synthetic counterparts from the grid at the predicted parameters; PA compared with apparent outflow orientation  
  > "a side-by-side comparison between the real ALMA $^{12}$CO (2–1) observations of our three targets and synthetic counterparts retrieved from the simulation grid" (4.2 Comparison with Previous Estimates)
7. **Compare ML masses and inclinations with SED-based estimates**: Compare ML predictions with SED-fitting values from the literature; interpret predicted mass as a proxy for m*/Mcore given the fixed 60 Msun core  
  > "should not be interpreted as an absolute physical mass for real systems, but rather as a proxy for the evolutionary fraction of the core" (4.2 Comparison with Previous Estimates)
   - assumption: Training simulations assume a fixed initial core mass of 60 Msun (single evolutionary track)  
  > "our training simulations assume a fixed initial core mass of 60 $M_\odot$." (4.2 Comparison with Previous Estimates)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : simalma synthetic ALMA observations; calibration, self-calibration and tclean imaging of the real data  
  > "To simulate ALMA observations, we post-process the synthetic line data using CASA" (2.2 Synthetic Observations); "Data calibration and imaging were performed in CASA." (4 Application to Real ALMA-Observed Protostellar Outflows and Uncertainty Assessment)
- **tclean** : imaging the real CO data  
  > "imaging was carried out with the tclean task using Briggs weighting with robust = 0.5" (4 Application to Real ALMA-Observed Protostellar Outflows and Uncertainty Assessment)
- **RADMC-3D** : non-LTE synthetic 12CO(2-1) line emission  
  > "We use the publicly available radiative transfer code radmc-3d (cite: 2012ascl.soft02015D) to generate synthetic" (2.2 Synthetic Observations)
- **ResNet50 / ResNet152** : pretrained image encoder  
  > "To enable a fair comparison across architectures, we also include ResNet152 and ViT_B_16, which have comparable numbers of parameters." (2.3 Multi-Modal Machine Learning Framework)
- **ViT_L_16 / ViT_B_16** : pretrained Vision Transformer image encoders  
  > "we adopt widely used pretrained architectures, including ResNet50 (cite: 2016cvpr.confE...1H) and ViT_L_16 (cite: 2020arXiv201011929D)" (2.3 Multi-Modal Machine Learning Framework)
- **Smooth Grad-CAM++** : localizing input regions driving predictions  
  > "we employ three complementary interpretability techniques: Smooth Grad-CAM++, Integrated Gradients (IG), and Occlusion Sensitivity Analysis." (3.2 Interpretable Analysis of Physical Feature Contributions in the Multi-Modal Network)
- **Integrated Gradients** : quantifying image versus spectrum importance  
  > "we apply Integrated Gradients (IG)." (3.2.2 Integrated Gradients with Mean Baseline)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ML-inferred protostellar masses for the three ALMA sources | ~12-15 | not stated | Msun | 6 | The predicted masses for the three outflows cluster around $\sim$12-15 $M_\odot$ with relatively small total uncertainties. |
| Inclinations inferred for G35.20 and G45.47 (pole-on) versus G339.88 (near edge-on) | G35.20 and G45.47 ~10-20; G339.88 ~70-80 | not stated | deg | 6 | The models infer G35.20 and G45.47 to be relatively pole-on (inclinations $\sim$10-20$^{\circ}$), whereas G339.88 is predicted to be close to edge-on (inclinations $\sim$70-80$^{\circ}$). |
| Fiducial ViT_L_16 best validation NLL (epoch 392) | -4.927 | not stated | dimensionless | 4 | the fiducial ViT model achieved its best performance at epoch 392 with a validation NLL of -4.927 |
| ResNet50 best validation NLL (epoch 4273) | -4.61 | not stated | dimensionless | 4 | reached its optimal performance at Epoch 4273, with a validation NLL of $-4.61$ |
| Parameter counts of ResNet50 and ViT_L_16 configurations | ~27 million and ~307 million | not stated | parameters | 4 | which contains $\sim$27 million parameters in the ResNet50 configuration and $\sim$307 million in the ViT_L_16 configuration |
| Reduction of training sample in restricted dataset | 35 | not stated | percent | 4 | we reduce the total training sample by 35% |
| Test set size | 6,720 | not stated | samples | 5 | The final testing set comprises 6,720 distinct samples |

## Qualitative findings

- All models degrade significantly when the smoothing kernel exceeds sigma ~5; ViT_L_16 gives the most stable position angle under heavy blurring  
  > "ViT_L_16 consistently provides the most stable position angle predictions under heavy blurring." (3.1 Assessing Model Performance)
- Spatial features dominate all predictions; spectra give a secondary role for mass and inclination and minimal for position angle  
  > "In all cases, spatial information dominates the prediction of physical properties." (3.2.2 Integrated Gradients with Mean Baseline)
- Predicted position angles are consistent across models and match visible outflow orientations  
  > "The mean position angles are broadly consistent across models and align well with the apparent outflow orientations in the images" (4.3 Position Angle as a Robust Validation Metric)

## Claim tuples

- H: Do ViT backbones generalize and resist resolution loss better than ResNets? | E: Compared ResNet50/152 and ViT_B_16/ViT_L_16 on restricted-set tests and on test data convolved with increasing Gaussian kernels | R: ViT_L_16 gives the most stable position angle under heavy blurring; ViT_B_16 generalizes better than ResNets with comparable parameters | F: Transformer architectures are better suited for unseen observational conditions and degraded spatial information | **supported**
- H: Which modality drives the inferred parameters? | E: Grad-CAM++, Integrated Gradients, occlusion and spectrum-ablation tests | R: Image attributions exceed spectral ones for all quantities; spectral omission has little impact at moderate smoothing | F: Spatial morphology is the dominant driver; spectra give secondary constraints for mass and inclination | **supported**
- H: Can the framework recover mass and inclination of real massive-protostar outflows in ALMA data? | E: Applied the trained models to 12CO(2-1) ALMA images of three sources with rotation-based uncertainty decomposition and compared with SED estimates | R: Masses ~12-15 Msun, below SED estimates; inclinations differ from SED values, pole-on for G35.20 and G45.47 | F: Absolute masses should be read as evolutionary-stage proxies because of the fixed 60 Msun core, and inclinations show larger discrepancies | **partially**
- H: Is position angle a robust quantity on real data? | E: Compared position angle predictions from four models on the three sources with epistemic uncertainties | R: Mean position angles are broadly consistent across models and align with outflow orientations in the images | F: The models capture physically meaningful geometry despite the simulation-to-real domain shift | **supported**

## Reasoning

- Why this data: Synthetic observations mimic the C36-3 setup of the real ALMA observations so the model can be applied to them  
  > "adopting the same C36-3 array configuration and 210-second integration time as used in the real observations discussed in" (2.2 Synthetic Observations)
- Why this method: Earlier work used only 1D spectral profiles and ignored outflow-lobe morphology in 2D maps  
  > "However, the approach was based solely on 1D spectral profiles, without incorporating the rich morphological information present in 2D integrated intensity maps of the red- and blue-shifted outflow lobes." (1 Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Predicted mass is degenerate with accretion rate because training uses a single 60 Msun core evolutionary track  
  > "the model is trained on a single evolutionary track." (Conclusions)
- Limitation (authors): Framework trained only on synthetic 12CO(2-1) emission and optimized for ALMA interferometric data; other tracers or instruments would need fine-tuning  
  > "the current framework is trained exclusively on synthetic $^{12}$CO (2-1) emission." (Conclusions)
- Limitation (authors): Validation on real data is qualitative because simulations are stochastic realizations rather than pixel-level templates  
  > "This qualitative approach to validation is necessitated by the nature of the 3D MHD simulations" (4.2 Comparison with Previous Estimates)
- Limitation (authors): G35.20 contains multiple outflows, which affects single-source interpretation  
  > "the region is known to contain multiple protostellar outflows" (4.2 Comparison with Previous Estimates)
- Caveat (inferred, ours): No ground truth for real sources; comparison is only against SED values from one paper and visual agreement, so accuracy on real data is unquantified
- Caveat (inferred, ours): Only three sources observed with a single short C36-3 setup, so the real-data test is very small
- Caveat (inferred, ours): Training set uses one MHD track (60 Msun core), so mass inference is not an absolute measurement
- Caveat (inferred, ours): Test samples share the same simulation snapshots as training (differing only by distance), so generalization beyond the simulation family is weakly tested
- Caveat (inferred, ours): Single training run per model; no seed variance reported

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Trained network code, weights and hyperparameters (learning rates, optimizer, batch size, architecture details)
- Missing: Synthetic training dataset and the MHD snapshots or a statement of their availability
- Missing: simalma and tclean parameters, self-calibration details and line-free channels for the real data
- Missing: Systemic velocities and the velocity cuts used for the real-source integrated-intensity maps
- Missing: Numerical per-model test errors (results are presented mainly as figures)
- Data volume (inferred): ALMA side: small (three short C36-3 pointings, a few GB raw). The main cost is generating RADMC-3D cubes for 7 masses x 20 inclinations x 3 distances and training large ViT models, which needs GPU compute.
- Score (inferred): 2/5, The real ALMA data are only a three-source test; the core results are ML training on private synthetic data with no released code or hyperparameter recipe, and key results are given in figures.
- Rediscovery candidate: no, The paper does not state that code, simulation snapshots or synthetic data are public, the training recipe is incomplete, and the main results are mostly figure-based and model-dependent.

## Links

- Method: (cite: 2024ApJ...966..117X) (Paper III: radiative transfer and simalma synthetic CO observations, dust temperature calculation and the same simulation snapshots)
- Method: (cite: 2023ApJ...947...40S) (Paper II: 3D MHD simulations used as the training data source)
- Companion: (cite: 2019ApJ...882..123S) (Paper I of the series (MHD simulations))
- Companion: (cite: 2024ApJ...967..145G) (Paper IV of the series (radio emission from shock-ionized outflow structures))
- Companion: (cite: 2022ApJ...936...68Z; 2019ApJ...886L...4Z; 2019ApJ...873...73Z) (Original publications of the ALMA data for G35.20, G45.47 and G339.88)
- Related: Disk Wind Feedback from High-mass Protostars series (Papers I-V)

## Checks

```json
{
 "quotes": 87,
 "quotes_ok": 87,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 102,
  "stated": 60,
  "rate": 0.588
 },
 "evidence_ok": true
}
```
