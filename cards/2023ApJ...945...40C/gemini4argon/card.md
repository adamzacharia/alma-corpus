# Multifrequency Black Hole Imaging for the Next-generation Event Horizon Telescope

`2023ApJ...945...40C` | The Astrophysical Journal 2023 | first author: Chael, Andrew | arXiv: 2210.12226 | DOI: 10.3847/1538-4357/acb7e4

Card schema 1.0 | model gemini-4-argon | depth light | type technical_calibration_or_instrument

## Science

- Fields: agn_and_quasars, protoplanetary_disks, instrumentation
- Question: How to simultaneously reconstruct interferometric images at multiple frequencies along with their spectral index and curvature maps using Regularized Maximum Likelihood (RML) methods.  
  > "Here we present a new method of simultaneously reconstructing interferometric images at multiple frequencies along with their spectral index maps." (Abstract); "It combines heterogeneous data products observed at multiple frequencies in a simultaneous fit of a reference frequency image, spectral index map, and potentially a spectral curvature map." (Introduction)
- Target **M87***: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **S5 0212+73**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NRAO530**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **HL Tau**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.000015.SV
- bands: Band 6, Band 7  
  > "We reconstructed multifrequency images from the publicly available ALMA datasets across the four spectral windows in both ALMA Band 6 (centered on 241 GHz) and Band 7 (centered at 324 GHz)." (ALMA imaging of HL Tau)
- frequencies and spectral setup: Eight spectral windows (224, 226, 240, 242, 336, 338, 345, 351 GHz); Band 6 centered on 241 GHz, Band 7 centered at 324 GHz  
  > "We reconstructed multifrequency images from the publicly available ALMA datasets across the four spectral windows in both ALMA Band 6 (centered on 241 GHz) and Band 7 (centered at 324 GHz)." (ALMA imaging of HL Tau); "with a reconstruction of the spectral index structure of the protoplanetary disk in HL Tau from 2014 ALMA observations between $224-350$ GHz (cite: ALMA_HlTau)." (Example Reconstructions: Real VLBA and ALMA data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2014  
  > "with a reconstruction of the spectral index structure of the protoplanetary disk in HL Tau from 2014 ALMA observations between $224-350$ GHz (cite: ALMA_HlTau)." (Example Reconstructions: Real VLBA and ALMA data)
- pi or archival as stated: archival (ALMA science verification)  
  > "In 14, we present multi-frequency reconstructions of observations of the protoplanetary disk in HL Tau conducted as part of the ALMA science verification process and published in (cite: ALMA_HlTau)." (ALMA imaging of HL Tau)
- Other facility **VLBA (MOJAVE)**: Real VLBI observations of S5 0212+73 and NRAO 530 at 8.1, 8.4, and 12.1 GHz  
  > "In 12 and 13 we present multi-frequency reconstructions of two jet sources observed at 8.1, 8.4, and 12.1 GHz as part of the MOJAVE program in July 2006 (cite: Hovatta_2014; Lister2018)." (VLBA imaging of MOJAVE data sets)
- External data: Total flux densities and multi-frequency CLEAN images of HL Tau  
  > "During the eht-imaging procedure, we rescale the total flux density of the intermediate images used for self-calibration to the total flux density values reported in Table 1 of (cite: ALMA_HlTau)." (ALMA imaging of HL Tau); "We compare our results to the original images presented in (cite: ALMA_HlTau), which were conducted with multi-frequency CLEAN imaging in CASA (cite: Rau_2011)." (ALMA imaging of HL Tau) [from (cite: ALMA_HlTau)]
- External data: MOJAVE VLBA datasets and CLEAN images at 8.1, 8.4, and 12.1 GHz  
  > "We then enforced the total flux density at each frequency through self-calibration of the visibility amplitudes using the total flux densities taken from the publicly available MOJAVE images reconstructed with CLEAN." (VLBA imaging of MOJAVE data sets); "In 12 and 13 we show results for both our simultaneous eht-imaging RML reconstructions and the original CLEAN reconstructions presented in (cite: Hovatta_2014), which were preformed independently at the three frequencies and then aligned." (VLBA imaging of MOJAVE data sets) [from (cite: Hovatta_2014; Lister2018)]
- External data: Historical atmospheric data from the MERRA-2 database  
  > "We use historical atmospheric data from the MERRA-2 database (cite: Gelaro_2017) as inputs to the am radiative transfer code (cite: Paine_2019)," (Generating synthetic ngEHT data) [from (cite: Gelaro_2017)]
- Simulation/model as data: Radiative GRMHD simulation R17 of M87* in MAD state using KORAL and grtrans  
  > "We first consider synthetic images of the near-horizon accretion flow and jet in M87* from a radiative GRMHD simulation (simulation R17 from (cite: ChaelM87))." ((cite: ChaelM87) model); "We generated images of the 345 GHz, 230 GHz, 86 GHz synchrotron emission from the simulation using the GR radiative transfer code grtrans (cite: Dexter16)." ((cite: ChaelM87) model)
- Simulation/model as data: GRMHD simulation of M87* in MAD state using BHAC and BHOSS  
  > "during this time period the simulation is well within the MAD state." (Mizuno2021 model); "The simulations used the GRMHD code BHAC (cite: Porth2017; Olivares2020) using three layers of adaptive mesh refinement in logarithmic Kerr-Schild coordinates." ((cite: Mizuno2021) model)
- Simulation/model as data: MAD and SANE GRMHD models of M87* using kharma and ipole  
  > "In this section, we consider reconstructions from simulated ngEHT data taken from two GRMHD models of M87* studied in (cite: Ricarte_2022)." (ngEHT Case Study: 230 GHz spectral index maps across the band); "Both models were generated with the GRMHD code kharma (cite: Prather_2021), and synchrotron radiative transfer was performed with ipole (cite: Moscibrodzka&Gammie2018)." (ngEHT Case Study: 230 GHz spectral index maps across the band)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Started with initial calibration in public ALMA data, self-calibrated all eight spectral window datasets three times to intermediate results during imaging, rescaling total flux density to Table 1 of ALMA Partnership et al. (2015)  
  > "We start with the initial amplitude and phase calibration provided in the public ALMA data, but we self-calibrate all eight spectral window datasets three times to intermediate results during the imaging process." (ALMA imaging of HL Tau); "During the eht-imaging procedure, we rescale the total flux density of the intermediate images used for self-calibration to the total flux density values reported in Table 1 of (cite: ALMA_HlTau)." (ALMA imaging of HL Tau)

### Imaging

- task: eht-imaging RML multi-frequency reconstruction  
  > "In eht-imaging, we fit the eight spectral window datasets from Band 6 and Band 7 simultaneously to an image model and spectral index map $\boldsymbol\alpha$ (setting the spectral curvature $\boldsymbol\beta=0$)." (ALMA imaging of HL Tau)
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

- Regularizer terms and likelihood terms for single-frequency RML imaging and optimization restart procedure  
  > "A full list of the image regularizers implemented in the eht-imaging RML code and used in this paper can be found in (cite: Chael18_Closure) and (cite: PaperIV)." (Imaging with Regularized Maximum Likelihood (RML)); "To avoid local minima in the objective function, we follow the procedure introduced in (cite: Chael18_Closure) and run each objective function optimization multiple times with different initial conditions." (Imaging procedure in `eht-imaging`) [from (cite: Chael18_Closure; PaperIV)]
- Proposed ngEHT reference array station locations, telescope parameters, and time-dependent SEFD calculation procedure  
  > "For ngEHT station locations and telescope parameters, we use the proposed ngEHT reference array presented in (cite: Issaoun_2022) that was developed from the site-selection considerations presented in (cite: Raymond_2021)." (Example Reconstructions: Synthetic ngEHT data); "In synthetic data generation for this paper, we determine SEFDs for each station as a function of time (rather than assuming a single fixed value) by following a similar procedure to (cite: Raymond_2021)." (Generating synthetic ngEHT data) [from (cite: Issaoun_2022; Raymond_2021)]
- Initial calibration and total flux density values for HL Tau ALMA data  
  > "We start with the initial amplitude and phase calibration provided in the public ALMA data, but we self-calibrate all eight spectral window datasets three times to intermediate results during the imaging process." (ALMA imaging of HL Tau); "During the eht-imaging procedure, we rescale the total flux density of the intermediate images used for self-calibration to the total flux density values reported in Table 1 of (cite: ALMA_HlTau)." (ALMA imaging of HL Tau) [from (cite: ALMA_HlTau)]

### Not stated but needed to reproduce (our reading)

- Exact numerical values of the regularizer hyperparameters (lambda_I, lambda_alpha, lambda_beta) and data weights (kappa_D) in the text (though scripts are provided on GitHub)
- Pixel size and grid dimensions (n x n) used for the HL Tau, MOJAVE, and synthetic ngEHT reconstructions

## Analysis recipe

1. **Generate synthetic ngEHT multi-frequency data from GRMHD models**: Simulate uv-coverage for the proposed ngEHT array, sample the Fourier transform of GRMHD model images (from KORAL/grtrans, BHAC/BHOSS, kharma/ipole), and add thermal noise (using MERRA-2 and am atmospheric model) plus systematic gain and phase errors.  
  > "samples the Fourier transform on the appropriate baselines, and adds random thermal noise and systematic gain and phase errors following" (Generating synthetic ngEHT data); "We use historical atmospheric data from the MERRA-2 database (cite: Gelaro_2017) as inputs to the am radiative transfer code (cite: Paine_2019), which then provides atmospheric opacity $\tau$ and atmospheric temperature $T_{\text{atm}}$ at each site as a function of observing frequency." (Generating synthetic ngEHT data)
   - software: eht-imaging, am, KORAL, grtrans, BHAC, BHOSS, kharma, ipole
   - parameter: Bandwidth 2 GHz per sub-band, integration time 120 s, quantization efficiency 0.88  
  > "where $\Delta\nu$ is the bandwidth, $\Delta t$ is the integration time, and $\eta$ is an efficiency factor relating to the data quantization (for 2-bit quantization used by the EHT, $\eta=0.88$)." (Generating synthetic ngEHT data); "In the ngEHT examples in this section, we assume a bandwidth $\Delta\nu=2$GHz for each ngEHT sub-band and we use an integration time $\Delta t=120$s." (Generating synthetic ngEHT data)
   - parameter: Receiver temperatures: 40 K at 86 GHz, 50 K at 230 GHz, 75 K at 345 GHz  
  > "We assume receiver temperatures $T_{\text{rx}}$ of 40 K at 86 GHz, 50 K at 230 GHz, and 75 K at 345 GHz." (Generating synthetic ngEHT data)
   - assumption: No frequency phase transfer (FPT) techniques used  
  > "However, in this paper we do not simulate observations that take advantage of FPT techniques." (Generating synthetic ngEHT data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Reconstruct multi-frequency images and spectral maps from synthetic ngEHT and real MOJAVE VLBI data**: Simultaneously fit reference image, spectral index map, and spectral curvature map by minimizing the RML objective function first using closure phases and log-closure amplitudes, then self-calibrating once and re-imaging with calibrated visibility amplitudes and closure phases.  
  > "In the RML imaging in this paper, we usually self-calibrate only once to an initial image generated by fitting closure phases and amplitudes." (Imaging procedure in eht-imaging); "In the RML imaging in this paper, we usually self-calibrate only once to an initial image generated by fitting closure phases and amplitudes." (Imaging procedure in `eht-imaging`); "We then re-image by fitting to the calibrated visibility amplitudes $|V|$ and closure phases $\psi_\mathcal{C}$." (Imaging procedure in `eht-imaging`)
   - software: eht-imaging, Scipy, NFFT
   - parameter: Curvature beta=0 for 230 GHz narrow-band ngEHT and MOJAVE reconstructions  
  > "As a result, we fix $\boldsymbol\beta=0$ in the reconstructions considered here and only reconstruct the spectral index map $\boldsymbol\alpha$." (ngEHT Case Study: 230 GHz spectral index maps across the band); "In both sources, the spectral curvature over the observed frequency range is minimal, so we reconstructed only the first-order spectral index map $\boldsymbol\alpha$ and set the spectral curvature term $\boldsymbol\beta=0$." (VLBA imaging of MOJAVE data sets)
   - assumption: Good independent measurements of total flux density are available to rescale closure-only images prior to self-calibration  
  > "We assume that we have good independent measurements of the total flux density and re-scale the closure-only image results (which are insensitive to total flux) to the correct values before self-calibrating." (Imaging procedure in `eht-imaging`)
   - fitting: L-BFGS gradient descent minimizing RML objective function with l2 and total variation regularizers on spectral maps  
  > "uses the Limited-Memory BFGS gradient descent algorithm" (Objective Function Minimization and Gradients); "In this work, we only employ $S_{\rm TV}$ and $S_{\ell_2}$ regularizers for both the spectral index $\boldsymbol\alpha$ and spectral curvature $\boldsymbol\beta$ maps," (RML imaging across frequency)
   - validation: Compute reduced chi-squared statistics for closure phases, log closure amplitudes, and visibility amplitudes, and compute NRMSE as a function of restoring beam size against ground truth.  
  > "For each beam-convolved reconstruction image, we compute the normalized root-mean square error (NRMSE) with the unblurred simulation image" (Quantifying Reconstruction Fidelity); "For each beam-convolved reconstruction image, we compute the normalized root-mean square error (NRMSE) with the unblurred simulation image (the ‘ground-truth’) at the appropriate frequency." (Quantifying Reconstruction Fidelity)
3. **Average and reconstruct multi-frequency ALMA images and spectral index map of HL Tau**: Average ALMA Band 6 and Band 7 complex visibilities across eight spectral windows and in 300 s time windows, then simultaneously fit reference image (at 287 GHz) and spectral index map directly to complex visibilities with three rounds of self-calibration.  
  > "Before imaging, we reduced the data by averaging the complex visibilities in frequency across the eight spectral windows and in time windows of 300 seconds to reduce the data volume." (ALMA imaging of HL Tau); "In eht-imaging, we fit the eight spectral window datasets from Band 6 and Band 7 simultaneously to an image model and spectral index map $\boldsymbol\alpha$ (setting the spectral curvature $\boldsymbol\beta=0$)." (ALMA imaging of HL Tau); "We start with the initial amplitude and phase calibration provided in the public ALMA data, but we self-calibrate all eight spectral window datasets three times to intermediate results during the imaging process." (ALMA imaging of HL Tau)
   - software: eht-imaging, Scipy, NFFT
   - parameter: Time averaging window = 300 s; reference frequency = 287 GHz; spectral curvature beta = 0; fiducial spectral index alpha_0 = 0  
  > "Before imaging, we reduced the data by averaging the complex visibilities in frequency across the eight spectral windows and in time windows of 300 seconds to reduce the data volume." (ALMA imaging of HL Tau); "averaging the complex visibilities in frequency across the eight spectral windows and in time windows of 300 seconds to reduce the data volume." (ALMA imaging of HL Tau)
   - assumption: Total flux densities rescaled to Table 1 of ALMA Partnership et al. (2015)  
  > "During the eht-imaging procedure, we rescale the total flux density of the intermediate images used for self-calibration to the total flux density values reported in Table 1 of (cite: ALMA_HlTau)." (ALMA imaging of HL Tau)
   - fitting: L-BFGS minimization fitting directly to complex visibilities with maximum entropy and total variation regularizers on reference image, plus total variation and l2 norm regularizers on spectral index map  
  > "for this image reconstruction we used use complex visibilities directly in the likelihood terms of the objective function" (ALMA imaging of HL Tau); "we use maximum entropy and total variation on the reference image (at 287 GHz) as well as total variation on the spectral index map" (ALMA imaging of HL Tau)
   - validation: Compare with published multi-frequency CLEAN images from ALMA Partnership et al. (2015) and compute reduced chi-squared statistics for complex visibilities across all eight bands.  
  > "We compare our results to the original images presented in (cite: ALMA_HlTau), which were conducted with multi-frequency CLEAN imaging in CASA (cite: Rau_2011)." (ALMA imaging of HL Tau); "which were conducted with multi-frequency CLEAN imaging in CASA" (ALMA imaging of HL Tau)

## Software

- **eht-imaging** v1.2.4: Multi-frequency RML image reconstruction, synthetic ngEHT data generation, self-calibration, and visualization  
  > "The method is based on existing Regularized Maximum Likelihood (RML) methods commonly used for EHT imaging and is implemented in the eht-imaging Python software library." (Abstract); "In the examples that follow in 4, we use the eht-imaging library to generate synthetic data on ngEHT baselines." (Generating synthetic ngEHT data); "(ref: ehtim) Chael, A., kwan Chan, C., klbouman, et al. 2022, achael/eht-imaging: v1.2.4, v1.2.4, Zenodo, doi: 10.5281/zenodo.6519440" (References)
- **Scipy** : Limited-Memory BFGS gradient descent optimization of the RML objective function  
  > "uses the Limited-Memory BFGS gradient descent algorithm" (Objective Function Minimization and Gradients)
- **NFFT** : Nonequispaced Fast Fourier Transform to generate synthetic visibilities from trial images at each minimization step  
  > "At each step in the minimization, we generate synthetic data from the trial images at each frequency using the Nonequispaced Fast Fourier Transform (NFFT; (cite: NFFT))." (Imaging procedure in `eht-imaging`)
- **am** 11.0: Radiative transfer calculation of atmospheric opacity and temperature for synthetic ngEHT data generation  
  > "We use historical atmospheric data from the MERRA-2 database (cite: Gelaro_2017) as inputs to the am radiative transfer code (cite: Paine_2019), which then provides atmospheric opacity $\tau$ and atmospheric temperature $T_{\text{atm}}$ at each site as a function of observing frequency." (Generating synthetic ngEHT data); "(ref: Paine_2019) Paine, S. 2019, The am atmospheric model, 11.0, Zenodo, Zenodo, doi: 10.5281/zenodo.3406483" (References)
- **KORAL** : Radiative GRMHD simulation R17 of M87*  
  > "The simulation was performed using the radiative GRMHD code KORAL (cite: KORAL13; KORAL14; KORAL16)." ((cite: ChaelM87) model)
- **grtrans** : General relativistic radiative transfer to generate 345, 230, and 86 GHz synchrotron emission images from the KORAL simulation  
  > "We generated images of the 345 GHz, 230 GHz, 86 GHz synchrotron emission from the simulation using the GR radiative transfer code grtrans (cite: Dexter16)." ((cite: ChaelM87) model)
- **BHAC** : GRMHD simulation of M87* from Mizuno et al. (2021)  
  > "The simulations used the GRMHD code BHAC (cite: Porth2017; Olivares2020) using three layers of adaptive mesh refinement in logarithmic Kerr-Schild coordinates." ((cite: Mizuno2021) model)
- **BHOSS** : General relativistic radiative transfer calculations for the BHAC simulation  
  > "The radiative transfer calculations to produce the images in 5 used the GRRT code BHOSS (cite: Younsi2012; Younsi2020)." ((cite: Mizuno2021) model)
- **kharma** : MAD and SANE GRMHD simulations of M87* from Ricarte et al. (2022)  
  > "Both models were generated with the GRMHD code kharma (cite: Prather_2021), and synchrotron radiative transfer was performed with ipole (cite: Moscibrodzka&Gammie2018)." (ngEHT Case Study: 230 GHz spectral index maps across the band)
- **ipole** : Synchrotron radiative transfer for the kharma GRMHD models  
  > "Both models were generated with the GRMHD code kharma (cite: Prather_2021), and synchrotron radiative transfer was performed with ipole (cite: Moscibrodzka&Gammie2018)." (ngEHT Case Study: 230 GHz spectral index maps across the band)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HL Tau unresolved spectral index (224 to 351 GHz, eht-imaging) | 2.74 | not stated | dimensionless | 3 | This procedure produces an unresolved spectral index $\alpha=2.74$ over the band from 224 to 351 GHz, which matches the reported unresolved spectral index of $\alpha=2.77\pm0.13$ in (cite: ALMA_HlTau). |
| HL Tau reduced chi-squared for complex visibilities at 224 GHz | 1.07 | not stated | dimensionless | 3 | / HL Tau ([14](#fig:HLTau)) / Multi-Frequency /  224 GHz  /     1.07     / |
| HL Tau reduced chi-squared for complex visibilities at 345 GHz | 1.01 | not stated | dimensionless | 3 | /                           /                 /  345 GHz  /     1.01     / |
| S5 0212+735 downstream jet lowest spectral index (eht-imaging) | -1.5 | not stated | dimensionless | 2 | The recovered spectral index far from the core in S5 0212+735 (12) is more negative in the original CLEAN reconstructions of these datasets (where it reaches values of $\alpha\sim-2.5$) than in the eht-imaging reconstruction (where the lowest values are $\alpha\sim-1.5$). |

## Qualitative findings

- Simultaneous RML multi-frequency imaging shares structural information across frequencies, recovering extended 345 GHz jet emission in M87* and super-resolving the 86 GHz central brightness depression ('inner shadow').  
  > "As a result, the reconstruction of the 345 GHz extended jet emission is much more accurate at high dynamic range in the multi-frequency reconstruction." ((cite: ChaelM87) model); "However, the multi-frequency reconstruction accurately resolves the inner shadow feature at 86 GHz by propagating structural information from the higher-resolution datasets at 230 and 345 GHz." ((cite: ChaelM87) model)
- Simultaneous multi-frequency RML imaging accurately recovers resolved spectral index maps across a narrow 18 GHz band around 230 GHz where independent single-frequency reconstructions fail.  
  > "As a result, the spectral index maps recovered from the independent images do not accurately reproduce any physically useful information from the ground truth spectral index distribution at 1.3 mm." (ngEHT Case Study: 230 GHz spectral index maps across the band); "the simultaneous multi-frequency fit of all four datasets is able to accurately recover a spectral index map similar to the ground truth distribution," (ngEHT Case Study: 230 GHz spectral index maps across the band)
- Multi-frequency RML imaging of ALMA HL Tau data reproduces the concentric ring structure and local spectral index maxima in the gaps, producing sharper spectral features in the intermediate dark rings than the original CLEAN reconstruction.  
  > "We obtain a clear concentric ring structure with distinct gaps between adjacent rings." (ALMA imaging of HL Tau); "Compared to the original CLEAN reconstruction, the eht-imaging reconstruction produces sharper spectral features corresponding to the intermediate dark rings (cite: ALMA_HlTau)." (ALMA imaging of HL Tau)

## Claim tuples

- H: Simultaneous RML multi-frequency image reconstruction produces higher-fidelity total intensity images and spectral index/curvature maps than combining independent single-frequency reconstructions. | E: Generate synthetic ngEHT observations of GRMHD models of M87* across 86-345 GHz and across four sub-bands near 230 GHz, and compare simultaneous multi-frequency RML reconstructions against independent single-frequency RML reconstructions using NRMSE and visual inspection. | R: Multi-frequency reconstructions achieve lower NRMSE across all frequencies and blurring kernels, recover the extended 345 GHz jet, super-resolve the 86 GHz inner shadow, and recover accurate 230-345 GHz and intra-band 230 GHz spectral index maps that independent reconstructions fail to recover. | F: Simultaneous RML multi-frequency imaging significantly outperforms independent single-frequency reconstructions in both total intensity fidelity and spectral map recovery. | **supported**
- H: The RML multi-frequency imaging method can be successfully applied to real VLBI and connected-element interferometer (ALMA) datasets to recover spatial and spectral structure consistent with CLEAN reconstructions. | E: Apply the multi-frequency RML algorithm in eht-imaging to archival MOJAVE VLBA datasets (S5 0212+73 and NRAO 530) and ALMA Science Verification Band 6+7 observations of HL Tau. | R: The reconstructions fit the data with reduced chi-squared near unity, reproduce the core-to-jet spectral index decline in MOJAVE sources, and recover the concentric rings and high-spectral-index gaps in HL Tau with sharper spectral features in the dark rings. | F: RML multi-frequency synthesis successfully reconstructs images and spectral index maps from real VLBA and ALMA observations, reproducing primary features of prior CLEAN reconstructions. | **supported**

## Reasoning

- Why this data: Synthetic ngEHT datasets test horizon-scale spectral imaging capabilities at 86-345 GHz; MOJAVE VLBA datasets test real VLBI spectral index imaging; ALMA HL Tau observations test applicability to larger datasets from connected-element interferometers.  
  > "In 5.1 we consider two examples of VLBI spectral index imaging using MOJAVE data from $8-12$ GHz (cite: Hovatta_2014; Lister2018)." (Example Reconstructions: Real VLBA and ALMA data); "In 5.2 we demonstrate the applicability of the method to larger datasets from connected-element interferometers with a reconstruction of the spectral index structure of the protoplanetary disk in HL Tau from 2014 ALMA observations between $224-350$ GHz (cite: ALMA_HlTau)." (Example Reconstructions: Real VLBA and ALMA data)
- Why this method: RML forward-modeling can fit directly to closure phases and closure amplitudes, avoiding initial calibration errors on high-frequency VLBI baselines, while simultaneously regularizing the spectral index map and naturally enforcing image alignment across frequencies.  
  > "critically, it allows us to maintain the flexibility of the RML approach in fitting directly to interferometric ‘closure quantities’, which are robust to systematic calibration uncertainties that affect all millimeter-VLBI datasets." (Introduction); "RML multifrequency synthesis effectively enforces image alignment by the spectral index regularization terms, which favor spectral index maps without large gradients" (Discussion)
- Alternative: Independent single-frequency RML imaging followed by cross-correlation alignment and pixel-by-pixel spectral fitting  
  > "We compare the simultaneously-recovered maps of the reference frequency $\mathbf{I}_0$, spectral index $\boldsymbol\alpha$, and spectral curvature $\boldsymbol\beta$ from multifrequency imaging to those we compute after-the-fact from independently-reconstructed images." (ngEHT Case Study: Simultaneous imaging from 86-345 GHz)
- Alternative: Multi-frequency CLEAN algorithms (e.g., CASA tclean)  
  > "Several CLEAN-based algorithms that simultaneously use observations at multiple frequencies to solve for an image and spectral index map have been developed (cite: Sault_1994; Rau_2011; Offringa_2021) and are implemented in standard interferometric software." (Introduction)
- Alternative: Fitting closure quantities for ALMA HL Tau (rejected in favor of complex visibilities due to large data volume)  
  > "Because the data volume remains much larger than the VLBI datasets we typically reconstruct with" (ALMA imaging of HL Tau)
- How they decided it was enough: _not stated_
- Limitation (authors): Forward-modeling likelihood and gradient computation is computationally slow for large datasets from connected-element interferometers like ALMA, requiring heavy time and frequency averaging.  
  > "For observations from connected-element interferometers like ALMA, the large size of the data vector $\mathbf{d}$ slows down the likelihood and gradient computation; when imaging ALMA data in eht-imaging, we need to significantly average the data in time and frequency to enable image reconstruction in a reasonable time." (Discussion)
- Limitation (authors): The method uses a fixed pixel grid rather than multi-scale image bases, requiring a large number of pixels to simultaneously capture large-scale low-frequency and fine-scale high-frequency structures.  
  > "Another disadvantage of our current RML approach is that we fit images on a grid with a fixed pixel size; in contrast, existing CLEAN-based multi-frequency methods (cite: Rau_2011; Offringa_2021) currently employ multi-scale image bases (cite: Cornwell_08)." (Discussion)
- Limitation (authors): The RML optimization finds a single maximum and does not provide robust uncertainty estimates or posterior distributions for the reference image or spectral index map.  
  > "Finally, another key disadvantage of our RML multi-frequency synthesis technique is that we do not provide any robust measurement of the uncertainty in the reference frequency image or in the spectral index map." (Discussion)
- Limitation (authors): Position offsets/misalignment between frequencies can still occur for poorly-resolved images lacking common features across bands, and steep brightness gradients can cause spectral index artifacts.  
  > "This error in the spectral index reconstruction occurs at the jet edge where the brightness gradient is very steep." ((cite: ChaelM87) model); "position offsets may be a particular problem for poorly-resolved images where there are few common features between frequency bands for the imager to ‘lock on’ to during image reconstruction." (Discussion)
- Caveat (inferred, ours): Hyperparameter selection (such as total variation weight on the spectral index map) involves a subjective trade-off between suppressing boundary artifacts and over-smoothing real spectral variations.
- Caveat (inferred, ours): Reduced chi-squared metrics cannot distinguish between single-frequency and multi-frequency reconstruction quality because both achieve chi-squared near unity.

## Reproducibility

- Data public (paper): Yes; ALMA HL Tau data and MOJAVE datasets are publicly available, and synthetic data, reduced real data, ground truth images, and imaging scripts are released on GitHub.  
  > "We reconstructed multifrequency images from the publicly available ALMA datasets across the four spectral windows in both ALMA Band 6 (centered on 241 GHz) and Band 7 (centered at 324 GHz)." (ALMA imaging of HL Tau); "The synthetic data, ground truth simulation images, and eht-imaging scripts used to produce the reconstructed images in the following sections can be found at https://github.com/achael/multifrequency_scripts/." (Footnotes); "The reduced data and eht-imaging scripts used to produce the reconstructed images in the following sections can be found at https://github.com/achael/multifrequency_scripts/." (Footnotes)
- Products in archive: _not stated_
- Code: eht-imaging library (https://github.com/achael/eht-imaging, Zenodo v1.2.4) and paper reproduction scripts/data (https://github.com/achael/multifrequency_scripts/)  
  > "https://github.com/achael/eht-imaging" (Footnotes); "The synthetic data, ground truth simulation images, and eht-imaging scripts used to produce the reconstructed images in the following sections can be found at https://github.com/achael/multifrequency_scripts/." (Footnotes)
- Missing: Exact hyperparameter values and pixel grid settings are not tabulated in the paper text, though they are available in the linked GitHub repository.
- Data volume (inferred): Small to moderate (<10 GB for the time/frequency-averaged visibilities, synthetic UVFITS files, and ground-truth images in the repository; raw ALMA SV data is tens of GB).
- Score (inferred): 95/5, The open-source software (eht-imaging v1.2.4) and the exact imaging scripts, synthetic datasets, ground-truth models, and reduced archival datasets are publicly released in a dedicated GitHub repository.
- Rediscovery candidate: yes, Publicly available ALMA SV data for HL Tau, public MOJAVE data, open-source software, and complete reproduction scripts with quantitative chi-squared and spectral index benchmarks.

## Links

- Method: (cite: Chael_16; Chael18_Closure) (Foundational single-frequency RML imaging framework, closure likelihoods, regularizers, and analytical gradients in eht-imaging)
- Method: (cite: PaperIV) (EHT M87* RML imaging procedures and regularizer definitions)
- Method: (cite: Raymond_2021; Issaoun_2022) (ngEHT reference array site selection and time-dependent SEFD modeling)
- Related: Event Horizon Telescope (EHT)
- Related: next-generation Event Horizon Telescope (ngEHT)
- Related: MOJAVE
- Related: ALMA Science Verification

## Checks

```json
{
 "quotes": 100,
 "quotes_ok": 100,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.000015.SV"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00015.SV"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 99,
  "stated": 55,
  "rate": 0.556
 },
 "evidence_ok": true
}
```
