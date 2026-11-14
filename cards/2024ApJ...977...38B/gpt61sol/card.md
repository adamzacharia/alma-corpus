# Neural Network Constraints on the Cosmic-Ray Ionization Rate and Other Physical Conditions in NGC 253 with ALCHEMI Measurements of HCN and HNC

`2024ApJ...977...38B` | The Astrophysical Journal 2024 | first author: Behrens, Erica | arXiv: 2409.13821 | DOI: 10.3847/1538-4357/ad85db

Card schema 1.0 | model gpt-6.1-sol | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, astrochemistry, star_formation
- Question: Constrain spatially varying CRIR and molecular gas conditions across the NGC 253 CMZ using HCN, HNC, and a neural-network chemical emulator.  
  > "We use a neural network model and ALMA observations of HCN and HNC to constrain the physical conditions, most notably the cosmic-ray ionization rate (CRIR, $\zeta$), in the Central Molecular Zone (CMZ) of the starburst galaxy NGC 253." (abstract)
- Target **NGC 253 CMZ**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00161.L, 2018.1.00162.S
- bands: Bands 3–7  
  > "which imaged the NGC 253 CMZ in ALMA Bands 3–7 (84–373 GHz)" (ALCHEMI Observations)
- frequencies and spectral setup: 84–373 GHz; HCN and HNC J=1-0, 2-1, 3-2, 4-3  
  > "which imaged the NGC 253 CMZ in ALMA Bands 3–7 (84–373 GHz)" (ALCHEMI Observations); "we extract the HCN and HNC $J=1-0$, $2-1$, $3-2$, and $4-3$ transition integrated intensities" (ALCHEMI Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.6 arcsec (∼28 pc)  
  > "at 1.$^{\prime\prime}6$ ($\sim28$ pc) resolution" (ALCHEMI Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: ALMA Cycles 5 and 6  
  > "during ALMA Cycles 5 (2017.1.00161.L) and 6 (2018.1.00162.S)." (ALCHEMI Observations)
- pi or archival as stated: Data from ALMA Large Program ALCHEMI  
  > "We use data from the ALMA Large Program ALCHEMI: the ALMA Comprehensive High-resolution Extragalactic Molecular Inventory (cite: ALCHEMI-ACA)" (ALCHEMI Observations)
- Line: HCN J=1-0 (88.6316 GHz)
- Line: HCN J=2-1 (177.2611 GHz)
- Line: HCN J=3-2 (265.8864 GHz)
- Line: HCN J=4-3 (354.5055 GHz)
- Line: HNC J=1-0 (90.6636 GHz)
- Line: HNC J=2-1 (181.3248 GHz)
- Line: HNC J=3-2 (271.9811 GHz)
- Line: HNC J=4-3 (362.6303 GHz)
- Other facility **Fermi-LAT and H.E.S.S.**: Non-thermal emission constraints used by Phan2024 for the theoretical CRIR comparison.  
  > "Using this model and parameters derived from fits to non-thermal emission from Fermi-LAT (cite: Abdo2010) and H.E.S.S. (cite: H.E.S.S.Collaboration2018), they model cosmic-ray spectra" (Comparison of Cosmic-Ray Ionization Rate to Theoretical Predictions)
- Other facility **Leiden Atomic and Molecular Database**: Availability of the older He-based excitation rates discussed in the rate comparison.  
  > "The (cite: Dumouchel2010) rates are available in the Leiden Atomic and Molecular Database" (New Collisional Rates Analysis)
- External data: ALCHEMI observations and data reduction.  
  > "Details of the observations and data reduction can be found in (cite: ALCHEMI-ACA) and (cite: Behrens2022)." (ALCHEMI Observations) [from (cite: ALCHEMI-ACA); (cite: Behrens2022)]
- External data: Typical GMC size of 50 pc and GMC identifications used for comparisons.  
  > "We choose a common region size of 50 pc, which is the typical size of a GMC structure in the NGC 253 CMZ (cite: leroy15)." (Region Selection and Moment-0 Maps); "Giant Molecular Cloud (GMC) regions in the CMZ that were identified by (cite: leroy15) based on peaks in the dense gas emission." (Introduction) [from (cite: leroy15)]
- External data: HCN and HNC collisional excitation rates for ortho- and para-H2.  
  > "We use collisional excitation rates from (cite: HernandezVera2017), who calculated rates for HCN and HNC collisions with ortho- and para-H$_2$ (cite: Behrens2022)." (Implementation with Bayesian Nested Sampling) [from (cite: HernandezVera2017)]
- External data: Older He-based HCN and HNC collisional rates used for comparison.  
  > "To provide comparison of the commonly-used He excitation rates (cite: Dumouchel2010) to the H$_2$-based excitation rates (cite: HernandezVera2017) used in the present analysis" (New Collisional Rates Analysis) [from (cite: Dumouchel2010)]
- External data: Prior volume density, column density, and CRIR estimates for NGC 253.  
  > "Estimates for volume and column density from this work and other ALCHEMI studies are shown in Table" (Column Density, Volume Density, Filling Factor, and Kinetic Temperature); "We compare our CRIR results to those predicted using similar methods in (cite: Holdship2022) and (cite: Behrens2022)." (Comparison of Cosmic-Ray Ionization Rate to Other Measurements) [from (cite: Holdship2022); (cite: Behrens2022); (cite: Tanaka2024)]
- External data: Evidence that HCN sources are smaller than the ∼28 pc ALCHEMI beam.  
  > "Recent work by (cite: Butterworth2024) suggests that HCN emission in NGC 253 originates from sources significantly smaller than the $\sim28$ pc ALCHEMI beam" (Comparison of Cosmic-Ray Ionization Rate to Other Measurements) [from (cite: Butterworth2024)]
- External data: Radio sources labeled in Figure 8; unclassified sources expected to include supernova remnants and H II regions.  
  > "Note that of the ‘Unclassified Radio’ sources labeled in Figure [8](#fig:zeta_hatchMap) (cite: ua97), half are expected to be supernova remnants, and half are likely H II regions." (Apparent High-$\zeta$ Regions) [from (cite: ua97)]
- External data: Theoretical cosmic-ray transport model and CRIR predictions informed by non-thermal emission.  
  > "we consider CRIRs derived from theoretical calculations and fits to non-thermal radio, X-ray, and gamma-ray emission data from (cite: Phan2024)." (Comparison of Cosmic-Ray Ionization Rate to Theoretical Predictions) [from (cite: Phan2024)]
- External data: Simulations varying cosmic-ray diffusion in star-forming regions.  
  > "(cite: Semenov2021) use simulations to test the effect of varying the cosmic-ray diffusion coefficient $\kappa_{\text{CR}}$ in star-forming regions." (Cosmic Ray Enhancement in Star-forming Regions) [from (cite: Semenov2021)]
- External data: Starburst evolution models using FIREbox.  
  > "(cite: Cenci2024MNRAS) have modeled starburst galaxy evolution using the `FIREbox` simulation (cite: Feldmann2023MNRAS)." (Column Density, Volume Density, Filling Factor, and Kinetic Temperature) [from (cite: Cenci2024MNRAS); (cite: Feldmann2023MNRAS)]
- External data: Far-UV enhancement of HCN and the HCN/HNC ratio.  
  > "(cite: Santa-Maria2023) found that HCN was enhanced by far-UV radiation, increasing the HCN/HNC ratio as the incident radiation field increased." (High $X_\text{HCN}/X_\text{HNC}$) [from (cite: Santa-Maria2023)]
- External data: Shock mechanical heating enhances the HCN/HNC ratio.  
  > "(cite: meijerink11) discussed the influence of mechanical heating from shocks on the HCN/HNC ratio, showing that it is enhanced by shock activity." (High $X_\text{HCN}/X_\text{HNC}$) [from (cite: meijerink11)]
- External data: Four high-temperature outskirts regions used to assess possible shock contamination.  
  > "(cite: Tanaka2024) constrained the kinetic temperature in NGC 253 and noted four high-temperature regions around the outskirts of the CMZ (approximately regions 34, 49, 51, and 71 from this work)." (High $X_\text{HCN}/X_\text{HNC}$) [from (cite: Tanaka2024)]
- External data: Region 86 proximity to an expanding dense-gas shell and evidence for shocks.  
  > "(cite: Gorski2017) showed that this region is close to an expanding shell of dense gas, and (cite: Huang2023) also found evidence indicative of shocks here." (High $X_\text{HCN}/X_\text{HNC}$) [from (cite: Gorski2017); (cite: Huang2023)]
- External data: Super star cluster ages and central-to-outer age gradient.  
  > "Recent analyses have identified 14 super star clusters in NGC 253 with a likely age range of 0.01 to 3 Myr" (Cosmic Ray Enhancement in Star-forming Regions); "an age gradient whereby the older SSCs are located in the center of the NGC 253 CMZ (cite: leroy18; Mills2021ApJ; Levy2022ApJ; Butterworth2024)." (Cosmic Ray Enhancement in Star-forming Regions) [from (cite: leroy18; Mills2021ApJ; Levy2022ApJ; Butterworth2024)]
- Simulation/model as data: Two-phase UCLCHEM grid supplying HCN and HNC training abundances.  
  > "We derive our training dataset from a grid of `UCLCHEM` models for HCN and HNC using input parameters that span our parameter space" (Training Dataset); "The output from phase 2 makes up the training data for our neural network." (Training Dataset)
- Simulation/model as data: Phan2024 cosmic-ray transport predictions for comparison with inferred CRIRs.  
  > "This study considers a theoretical transport model for cosmic rays from which they derive cosmic-ray spectra" (Comparison of Cosmic-Ray Ionization Rate to Theoretical Predictions)
- Simulation/model as data: Semenov2021 simulations used to interpret possible diffusion suppression.  
  > "(cite: Semenov2021) use simulations to test the effect of varying the cosmic-ray diffusion coefficient $\kappa_{\text{CR}}$ in star-forming regions." (Cosmic Ray Enhancement in Star-forming Regions)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 15% of the measured flux  
  > "where $\sigma_\text{fluxcal}$ is equal to 15% of the measured flux." (Region Selection and Moment-0 Maps)
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

- Observations and data reduction details.  
  > "Details of the observations and data reduction can be found in (cite: ALCHEMI-ACA) and (cite: Behrens2022)." (ALCHEMI Observations) [from (cite: ALCHEMI-ACA); (cite: Behrens2022)]
- HCN/HNC integrated-intensity extraction using CubeLineMoment.  
  > "As noted in (cite: Behrens2022), we extract the HCN and HNC $J=1-0$, $2-1$, $3-2$, and $4-3$ transition integrated intensities using the `CubeLineMoment`" (ALCHEMI Observations) [from (cite: Behrens2022)]
- Bayesian chemical and radiative-transfer inference framework.  
  > "Further details regarding our Bayesian inference analysis are described in (cite: Holdship2022) and (cite: Behrens2022)." (Bayesian Inference with Neural Networks) [from (cite: Holdship2022); (cite: Behrens2022)]
- 50 pc region size based on typical GMC size.  
  > "We choose a common region size of 50 pc, which is the typical size of a GMC structure in the NGC 253 CMZ (cite: leroy15)." (Region Selection and Moment-0 Maps) [from (cite: leroy15)]
- Joint HCN/HNC neural network motivated by similar spatial distributions.  
  > "We train one neural network model to predict the abundance of both HCN and HNC since previous ALCHEMI studies have shown that these molecules have similar spatial distributions (cite: Behrens2022)." (Training Dataset) [from (cite: Behrens2022)]
- Collisional excitation rates for HCN/HNC with ortho- and para-H2.  
  > "We use collisional excitation rates from (cite: HernandezVera2017), who calculated rates for HCN and HNC collisions with ortho- and para-H$_2$ (cite: Behrens2022)." (Implementation with Bayesian Nested Sampling) [from (cite: HernandezVera2017)]
- Low-abundance numerical-error warning motivating training-grid filtering.  
  > "Any parameter combinations that result in very low abundances are likely to be dominated by numerical error rather than chemistry (cite: heyl2023)." (Training Dataset) [from (cite: heyl2023)]
- Beam-filling factor motivated by sub-beam HCN sources.  
  > "Recent work by (cite: Butterworth2024) suggests that HCN emission in NGC 253 originates from sources significantly smaller than the $\sim28$ pc ALCHEMI beam" (Comparison of Cosmic-Ray Ionization Rate to Other Measurements) [from (cite: Butterworth2024)]

### Not stated but needed to reproduce (our reading)

- Exact calibrated cube products, spectral channel widths, velocity integration windows, and CubeLineMoment masking settings.
- Calibration and imaging versions, visibility weighting, array combination, primary-beam treatment, and final beam matching across transitions.
- Adopted distance and hexagonal-grid sky origin, orientation, boundaries, and region masks.
- Random linewidth distribution and seed for replacing masked pixels, including how flux-calibration uncertainty is evaluated in a masked pixel.
- UCLCHEM version, reaction network, elemental abundances, grain parameters, and exact phase-2 abundance output time.
- Neural-network optimizer, learning rate, input scaling beyond the stated logarithms, random seeds, and corrected train/validation/test allocation.
- SpectralRadex linewidth, background radiation, geometry, convergence settings, and exact collisional-rate input files.
- UltraNest live-point, accuracy, and stopping settings; treatment of correlated flux errors and substituted upper limits.
- Complete posterior summaries and a machine-readable list of regions rejected for low abundances or UV/shock chemistry.

## Analysis recipe

1. **Extract transition integrated intensities**: Extract HCN and HNC J=1-0 through 4-3 integrated intensities from ALCHEMI.  
  > "we extract the HCN and HNC $J=1-0$, $2-1$, $3-2$, and $4-3$ transition integrated intensities using the `CubeLineMoment`" (ALCHEMI Observations)
   - software: CubeLineMoment
   - parameter: ALCHEMI resolution 1.6 arcsec (∼28 pc)  
  > "at 1.$^{\prime\prime}6$ ($\sim28$ pc) resolution" (ALCHEMI Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Construct regional measurements and replace masked pixels**: Use HERA to average emission and noise over 50 pc adjoining hexagons; replace low-S/N pixels with 3σ integrated-intensity limits.  
  > "we divide the CMZ into adjoining hexagonal regions 50 pc in height using the integrated emission averaging code `HERA`" (Region Selection and Moment-0 Maps); "we fill in low S/N image pixels with $3\sigma$ upper-limit integrated intensities." (Region Selection and Moment-0 Maps); "Using these upper-limit values in place of masked pixels, we then obtain a unique average integrated intensity and RMS for each hexagonal region" (Region Selection and Moment-0 Maps)
   - software: HERA
   - parameter: 94 regions; S/N ≥3 in at least one transition  
  > "shows the final 94 regions we selected to study, where each of the hexagonal regions has S/N $\geq 3$ in at least one transition of interest." (Region Selection and Moment-0 Maps)
   - parameter: Random Δv between 20 and 100 km s−1 per low-S/N pixel  
  > "we assume a random $\Delta v$ between 20 and 100 km s$^{-1}$ for each low S/N image pixel." (Region Selection and Moment-0 Maps)
   - parameter: Gaussian width Δv/√(8 ln 2); peak 3√(σ_noise²+σ_fluxcal²)  
  > "We integrate over a Gaussian with width $\Delta v / \sqrt{8 \ln 2}$ and a peak value equal to 3 times the noise value, or $3 \times \sqrt{\sigma_\text{noise}^2 + \sigma_\text{fluxcal}^2}$" (Region Selection and Moment-0 Maps)
   - parameter: σ_fluxcal = 15% of measured flux  
  > "where $\sigma_\text{fluxcal}$ is equal to 15% of the measured flux." (Region Selection and Moment-0 Maps)
   - assumption: The substituted limits allow eight transitions to constrain every region.  
  > "These limits allow us to constrain our models with an equal number of transitions per region while also testing the efficacy of this algorithm in regions with low levels of emission." (Region Selection and Moment-0 Maps)
   - fitting: _not stated_
   - validation: Linewidth range chosen by inspecting HCN/HNC linewidths near the S/N threshold.  
  > "Based on an inspection of the range of linewidths seen in the CMZ for HCN and HNC near the edge of our S/N threshold" (Region Selection and Moment-0 Maps)
3. **Generate chemical training abundances**: Run two-phase UCLCHEM models: free-fall collapse followed by 6 Myr cloud chemistry; retain both molecular abundances above 10−12.  
  > "models the free-fall collapse of a gas cloud with an initial density of 100 cm$^{-3}$ down to the specified density at a fixed temperature of 10 K" (Training Dataset); "to chemically model the cloud itself over a timescale of 6 Myr." (Training Dataset); "Hence we retain only parameter combinations that result in abundances for both HCN and HNC above $10^{-12}$" (Training Dataset)
   - software: UCLCHEM
   - parameter: Temperature: 50–300 K; 15 linear points  
  > "| $T_\text{K}$ | Temperature (K) | 50–300 | Linear | 15 |" (Table 2)
   - parameter: H2 volume density: 10^3–10^7 cm−3; 20 logarithmic points; buffer 10^2.6–10^7.4 with 24 points  
  > "| $n_{\text{H}_2}$ | Volume Density (cm$^{-3}$) | 10$^3$–10$^7$ $(10^{2.6}$–$10^{7.4})$ | Log | 20 (24) |" (Table 2)
   - parameter: CRIR: 10–10^7 ζ0; 25 logarithmic points; ζ0 = 1.36×10−17 s−1  
  > "| $\zeta$ | Cosmic Ray Ionization Rate ($\zeta_{0}$$^{a}$) | 10–10$^7$ | Log | 25 |" (Table 2); "$\zeta_0$ = $1.36\times10^{-17}$ s$^{-1}$" (Table 2)
   - parameter: H2 column density: 10^22–10^25 cm−2; 15 logarithmic points; buffer 10^21.6–10^25.4 with 19 points  
  > "| $N_{\text{H}_2}$ | H$_{2}$ Column Density (cm$^{-2}$) | 10$^{22}$–$10^{25}$ $(10^{21.6}$–$10^{25.4})$ | Log | 15 (19) |" (Table 2)
   - parameter: ∼170,000 initial combinations; ∼115,000 after filtering  
  > "Including buffer points, which will be discussed later, each initial dataset contains $\sim$170,000 parameter combinations." (Training Dataset); "leaving $\sim$115,000 data points." (Training Dataset)
   - assumption: Phase 2 inherits phase-1 abundances.  
  > "phase 2, which uses the calculated abundances inherited from phase 1" (Training Dataset)
   - assumption: Shielded cloud interior: Av = 10 mag; UV = 1 Habing in both phases; UV negligible  
  > "Here we assume that we are probing the inner, shielded part of the cloud (visual extinction $A_v$ of 10 mag) such that UV radiation (set to 1 Habing in both `UCLCHEM phases`) is negligible." (Training Dataset)
   - assumption: X-ray ionization excluded.  
  > "X-ray ionization is not included in `UCLCHEM`" (Training Dataset)
   - fitting: _not stated_
   - validation: Filter low-abundance combinations considered dominated by numerical error.  
  > "Any parameter combinations that result in very low abundances are likely to be dominated by numerical error rather than chemistry (cite: heyl2023)." (Training Dataset)
4. **Train the HCN/HNC emulator**: Train one fully connected TensorFlow network to predict log HCN and HNC fractional abundances from four physical inputs.  
  > "We use the python package `TensorFlow`" (Neural Network Architecture); "We start with an input layer of four nodes, where each node corresponds to one of our chemical model parameters" (Neural Network Architecture); "We use the log of the `UCLCHEM` fractional abundance values when training the neural network in order to increase the magnitude of differences between abundances." (Training Dataset)
   - software: TensorFlow
   - parameter: 4 layers of 2000 nodes; 12,020,002 trainable parameters  
  > "we found a neural network with 4 layers each containing 2000 nodes produced results that aligned best with chemical model calculations." (Neural Network Architecture); "a neural network with fully connected layers and 12,020,002 trainable parameters" (Neural Network Architecture)
   - parameter: ReLU activation  
  > "Activation functions, such as the rectified linear unit (ReLU) that we employ, allow neural networks to consider non-linear solutions." (Neural Network Architecture)
   - parameter: Log inputs for n_H2, ζ, and N_H2  
  > "using the log of the parameter value for $n_{\text{H}_2}$, $\zeta$, and $N_{\text{H}_2}$" (Training Dataset)
   - parameter: Reported split: training 60% (∼69,000), validation 50% (∼17,000), test 25% (∼28,000)  
  > "a training set (60% of data, $\sim$69,000 points), validation set (50% of data, $\sim$17,000 points), and a test set (25% of data, $\sim$28,000 points)." (Training Dataset)
   - parameter: Validation mini-batch size 64  
  > "We calculate the validation loss using mini batches with a batch size of 64." (Neural Network Architecture)
   - parameter: Train with density buffer points; exclude buffer ranges from Bayesian inference.  
  > "we include additional column and volume density buffer points outside of our desired parameter ranges" (Training Results); "though values outside of this original range will not be considered later in our Bayesian analysis." (Training Results)
   - assumption: Joint HCN/HNC model based on their similar spatial distributions.  
  > "We train one neural network model to predict the abundance of both HCN and HNC since previous ALCHEMI studies have shown that these molecules have similar spatial distributions (cite: Behrens2022)." (Training Dataset)
   - fitting: Mean squared error; stop after 20 epochs without loss improvement; restore lowest-validation-loss weights.  
  > "We use a mean squared error loss function" (Neural Network Architecture); "we cease neural network training once the calculated loss has not improved over 20 consecutive epochs" (Neural Network Architecture); "the neural network then reverts back to using the weights from the epoch with the lowest validation loss." (Neural Network Architecture)
   - validation: Evaluate validation loss each epoch and compare predictions against held-out UCLCHEM test abundances.  
  > "we calculate the validation loss, or loss derived from the validation data, only once at the end of each epoch" (Training Dataset); "we test the newly-trained neural network model on the test set, a subset of the `UCLCHEM` grid that was not included in the training process." (Training Dataset)
5. **Benchmark emulator accuracy and inference speed**: Compare held-out chemical abundances and compare neural-network versus UCLCHEM inference in regions 26 and 53.  
  > "We compare the neural network model-predicted values against those calculated with `UCLCHEM`" (Training Results); "compares the inference algorithm results using `UCLCHEM` and the HCN/HNC neural network for regions 26 and 53" (Neural Network vs. Chemical Model)
   - software: UCLCHEM, UltraNest, TensorFlow
   - parameter: Regions 26 and 53 represent outer and inner CMZ.  
  > "which were chosen to represent regions in the outer and inner CMZ, respectively." (Neural Network vs. Chemical Model)
   - fitting: Compare inferred parameters, uncertainties, and 1D/2D posterior distributions.  
  > "The final inferred parameter values and their uncertainties derived from `UCLCHEM` and our neural network are nearly identical." (Neural Network vs. Chemical Model); "both the 1D and 2D posterior distributions for the two methods feature very similar shapes and characteristics" (Neural Network vs. Chemical Model)
   - validation: Mean abundance recovery within 3%; inferred parameters within UCLCHEM uncertainties.  
  > "on average, the neural network model is able to recover molecular abundances within 3% of the chemical model’s values." (Training Results); "the parameter values inferred by our neural network algorithm are well within the uncertainties obtained from the same analysis with `UCLCHEM`." (Neural Network vs. Chemical Model)
6. **Infer regional gas parameters**: UltraNest samples gas parameters; the neural network predicts abundances; SpectralRadex predicts optical-depth-aware intensities; apply a free beam-filling factor and compare with regional measurements.  
  > "The HCN and HNC model predicts abundances that we then feed into our radiative transfer code, `SpectralRadex`, in order to obtain integrated intensities for these molecular species." (Implementation with Bayesian Nested Sampling); "Note that `SpectralRadex` does a radiative transfer calculation which accounts for optical depth." (Implementation with Bayesian Nested Sampling); "After the integrated intensities are calculated, we apply a beam-filling factor, which is a free parameter in our algorithm ranging from 0–1." (Implementation with Bayesian Nested Sampling)
   - software: UltraNest, SpectralRadex, TensorFlow
   - parameter: TK = 50–300 K, linear prior; n_H2 = 10^3–10^7 cm−3, logarithmic prior  
  > "| $T_\text{K}$ | Temperature (K) | 50–300 | Linear | 15 |" (Table 2); "| $n_{\text{H}_2}$ | Volume Density (cm$^{-3}$) | 10$^3$–10$^7$ $(10^{2.6}$–$10^{7.4})$ | Log | 20 (24) |" (Table 2)
   - parameter: ζ = 10–10^7 ζ0 and N_H2 = 10^22–10^25 cm−2, logarithmic priors  
  > "| $\zeta$ | Cosmic Ray Ionization Rate ($\zeta_{0}$$^{a}$) | 10–10$^7$ | Log | 25 |" (Table 2); "| $N_{\text{H}_2}$ | H$_{2}$ Column Density (cm$^{-2}$) | 10$^{22}$–$10^{25}$ $(10^{21.6}$–$10^{25.4})$ | Log | 15 (19) |" (Table 2)
   - parameter: Beam-filling factor 0–1, linear prior  
  > "| $\eta_{ff}$ | Beam-filling factor | 0–1 | Linear | N/A$^{b}$ |" (Table 2)
   - assumption: HernandezVera2017 HCN/HNC collisional rates; ortho:para hydrogen = 3:1  
  > "We use collisional excitation rates from (cite: HernandezVera2017), who calculated rates for HCN and HNC collisions with ortho- and para-H$_2$ (cite: Behrens2022)." (Implementation with Bayesian Nested Sampling); "We adopt a 3:1 ortho:para hydrogen ratio." (Implementation with Bayesian Nested Sampling)
   - fitting: Likelihood exp[-(1/2) Σ_i (Fd,i−Ft,i)^2/σF,i²]; sum over transitions; stop when UltraNest has sampled the majority of probability density.  
  > "P(\mathbf{F_d}|\boldsymbol{\theta}) = \exp\left(-\frac{\displaystyle 1}{\displaystyle 2} \sum\limits_{i}^{N} \frac{(F_{d,i} - F_{t,i})^2}{\sigma^2_{F,i}}\right)" (Implementation with Bayesian Nested Sampling); "where we sum the values for each transition $i$." (Implementation with Bayesian Nested Sampling); "This process concludes when `UltraNest` has sampled the majority of the probability density." (Implementation with Bayesian Nested Sampling)
   - validation: Test phase-1 inclusion, old/new collision rates, and beam-filling-factor inclusion against posterior results.  
  > "demonstrates the differences in the posterior distributions with and without phase 1 modeling for sample regions 26 and 53." (Comparison of Cosmic-Ray Ionization Rate to Other Measurements); "These new rates did not result in significant changes in our posterior distributions for the majority of tested regions." (Comparison of Cosmic-Ray Ionization Rate to Other Measurements); "including a beam-filling factor did slightly widen the posterior distributions derived for each parameter." (Comparison of Cosmic-Ray Ionization Rate to Other Measurements)
7. **Identify unreliable regional solutions**: Inspect HCN/HNC abundance ratios, individual abundances, temperature-boundary behavior, and detected excitation ladders to flag UV/shock or low-abundance failures.  
  > "The unphysical combination of high $\zeta$ and very low $T_\text{K}$, in addition to anomalously high $X_{\text{HCN}}/X_{\text{HNC}}$ values, indicate that the chemistry included in our model is not well suited to the conditions in these regions." (High $X_\text{HCN}/X_\text{HNC}$); "we then look beyond abundance ratios and consider the individual values of $X_{\text{HCN}}$ and $X_{\text{HNC}}$." (Low $X_\text{HCN}$ and $X_\text{HNC}$)
   - software: UCLCHEM
   - parameter: 24 regions with X_HCN/X_HNC >4 also have ζ >5×10−13 s−1  
  > "all 24 regions with $X_{\text{HCN}}/X_{\text{HNC}} > 4$ also feature $\zeta > 5\times10^{-13}$ s$^{-1}$." (High $X_\text{HCN}/X_\text{HNC}$)
   - parameter: Abundances below 10−12 indicate unreliable chemical solutions.  
  > "the most likely range of parameters yields $X_\text{HCN}$ and $X_\text{HNC}$ values below $10^{-12}$" (Low $X_\text{HCN}$ and $X_\text{HNC}$); "we determine that parameter results for any regions that correspond to such low abundances are unreliable." (Low $X_\text{HCN}$ and $X_\text{HNC}$)
   - assumption: Shielded, cosmic-ray-dominated chemistry may fail in diffuse UV-affected or shocked gas.  
  > "Since the chemistry in shocked regions is likely not dominated by cosmic-ray ionization, the model presented here may struggle to constrain the parameters in those areas." (High $X_\text{HCN}/X_\text{HNC}$); "UV radiation is likely impacting the HCN and HNC chemistry." (High $X_\text{HCN}/X_\text{HNC}$)
   - fitting: _not stated_
   - validation: Region 1 UCLCHEM/emulator comparison reproduces the low-abundance failure; affected regions lack higher-J detections.  
  > "shows the posterior distributions achieved for region 1 using `UCLCHEM` and the neural network model, demonstrating nearly identical results in this low-abundance region." (Low $X_\text{HCN}$ and $X_\text{HNC}$); "all low-abundance regions feature four or fewer combined HCN and HNC transitions that meet our S/N criteria" (Low $X_\text{HCN}$ and $X_\text{HNC}$); "no higher energy transitions detected above $J=2-1$." (Low $X_\text{HCN}$ and $X_\text{HNC}$)
8. **Compare spatial trends with earlier measurements and theory**: Map inferred parameters and uncertainties; associate previous GMCs with the most-overlapping hexagon; compare CRIRs with molecular-emission studies and non-thermal transport predictions.  
  > "We show maps of the inferred parameter values derived from our combined Bayesian nested sampling and neural network algorithm" (Parameter Maps); "we associate each GMC with the hexagonal region with which it shares the most overlap" (Comparison of Cosmic-Ray Ionization Rate to Other Measurements); "we consider CRIRs derived from theoretical calculations and fits to non-thermal radio, X-ray, and gamma-ray emission data from (cite: Phan2024)." (Comparison of Cosmic-Ray Ionization Rate to Theoretical Predictions)
   - parameter: Inner versus outer CMZ divided near r = 100 pc  
  > "for the inner ($r\lesssim100$ pc) and outer ($r\gtrsim100$ pc) CMZ." (Column Density, Volume Density, Filling Factor, and Kinetic Temperature)
   - assumption: Non-thermal CRIR estimates average over the entire CMZ.  
  > "any CRIR values derived from Fermi-LAT and H. E. S. S. measurements must be treated as an average over the entire CMZ." (Comparison of Cosmic-Ray Ionization Rate to Theoretical Predictions)
   - fitting: _not stated_
   - validation: Most GMC CRIR uncertainties overlap earlier studies; outer-CMZ values agree within ∼0.2 dex with theoretical predictions.  
  > "With the exceptions of GMCs 1 (discussed above) and 5, all CRIR uncertainties overlap with those from both (cite: Holdship2022) and (cite: Behrens2022)." (Comparison of Cosmic-Ray Ionization Rate to Other Measurements); "The CRIR estimates in the outer CMZ are consistent within $\sim0.2$ dex with theoretical predictions of the CRIR (cite: Phan2024) derived from CMZ-averaged non-thermal emission." (Conclusions)
9. **Assess sensitivity to collisional excitation rates**: Compare modeled HCN/HNC intensities using He-scaled versus ortho+para-H2 rates, then compare inference in regions 26 and 53.  
  > "These modeled intensities were calculated using both the “old" (He-based) and “new" (ortho+para-H$_2$-based) rates" (New Collisional Rates Analysis); "The `UltraNest` inference results using the old and new rates are shown" (New Collisional Rates Analysis)
   - software: SpectralRadex, UltraNest
   - parameter: 10−12 ≤ X_mol ≤ 10−6; N_mol = 2 × N_H2 × X_mol  
  > "values in the range of $10^{-12} \leq X_\text{mol} \leq 10^{-6}$" (New Collisional Rates Analysis); "using $N_\text{mol} = 2 \times N_{\text{H}_2} \times X_\text{mol}$." (New Collisional Rates Analysis)
   - parameter: He-to-H2 rate scaling factor 1.363  
  > "In this comparison we have applied the standard scaling factor of 1.363 to convert He excitation rates to para-H$_2$" (New Collisional Rates Analysis)
   - assumption: Intensity-grid comparison excludes CRIR and beam filling; inference comparison includes CRIR but no beam-filling factor.  
  > "Note that the CRIR was not involved in these calculations, and no beam-filling factor was applied." (New Collisional Rates Analysis); "Here we include CRIR as a free parameter using the prior distribution provided in Table [2](#tab:priors)." (New Collisional Rates Analysis); "Note that no beam-filling fator is applied in these tests." (New Collisional Rates Analysis)
   - fitting: UltraNest comparison with the Table 2 CRIR prior.  
  > "Here we include CRIR as a free parameter using the prior distribution provided in Table [2](#tab:priors)." (New Collisional Rates Analysis); "The `UltraNest` inference results using the old and new rates" (New Collisional Rates Analysis)
   - validation: New rates change intensities by up to a factor of 2 but produce nearly identical median inferred parameters in tested regions.  
  > "Use of the new ortho+para-H$_2$ excitation rates result in higher (by up to a factor of 2) predicted HCN and HNC integrated transition intensities." (New Collisional Rates Analysis); "the median predicted values for these parameters are nearly identical using the new and old rates." (New Collisional Rates Analysis)

## Software

- **CubeLineMoment** : Extract HCN and HNC transition integrated intensities.  
  > "we extract the HCN and HNC $J=1-0$, $2-1$, $3-2$, and $4-3$ transition integrated intensities using the `CubeLineMoment`" (ALCHEMI Observations)
- **HERA** : Divide integrated-intensity maps into regions, average emission, and calculate noise statistics.  
  > "This code divides integrated intensity maps for each transition of interest into either adjacent circular or adjoining hexagonal regions of a user-specified size, averages the integrated emission over the region, and calculates noise statistics associated with the averaged emission." (Region Selection and Moment-0 Maps)
- **UCLCHEM** : Generate chemical abundances for training and direct inference comparisons.  
  > "We derive our training dataset from a grid of `UCLCHEM` models for HCN and HNC" (Training Dataset); "We compare the nested sampling results using our neural network model to those obtained with `UCLCHEM`" (Neural Network vs. Chemical Model)
- **TensorFlow** : Build and train the neural network.  
  > "to build and train our neural network model." (Neural Network Architecture); "We use the python package `TensorFlow`" (Neural Network Architecture)
- **SpectralRadex** : Radiative transfer from predicted abundances to integrated intensities, including optical depth.  
  > "The HCN and HNC model predicts abundances that we then feed into our radiative transfer code, `SpectralRadex`, in order to obtain integrated intensities for these molecular species." (Implementation with Bayesian Nested Sampling); "Note that `SpectralRadex` does a radiative transfer calculation which accounts for optical depth." (Implementation with Bayesian Nested Sampling)
- **UltraNest** : Bayesian nested sampling of physical parameters.  
  > "`UltraNest` uses the results from each log-likelihood comparison to choose additional parameter combinations to sample within our designated parameter space" (Implementation with Bayesian Nested Sampling)
- **CASA** : _not stated_
- **Astropy** : _not stated_
- **MLFriends** : _not stated_
- **SciPy** : _not stated_
- **FIREbox** : Starburst evolution simulations in cited work used for interpretation.  
  > "(cite: Cenci2024MNRAS) have modeled starburst galaxy evolution using the `FIREbox` simulation (cite: Feldmann2023MNRAS)." (Column Density, Volume Density, Filling Factor, and Kinetic Temperature)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean neural-network abundance recovery error | 3 | not stated | % | 5 | on average, the neural network model is able to recover molecular abundances within 3% of the chemical model’s values. |
| Neural-network inference time relative to UCLCHEM, region 26 | ∼7 | not stated | % | 5 | The neural network$+$`UltraNest` algorithm completed its explorations of the parameter space in $\sim7$% and $\sim15$% of the time it took for `UCLCHEM`$+$`UltraNest` to do the same for regions 26 and 53, respectively. |
| Neural-network inference time relative to UCLCHEM, region 53 | ∼15 | not stated | % | 5 | The neural network$+$`UltraNest` algorithm completed its explorations of the parameter space in $\sim7$% and $\sim15$% of the time it took for `UCLCHEM`$+$`UltraNest` to do the same for regions 26 and 53, respectively. |
| Maximum nuclear H2 volume density reported in Parameter Maps | 8×10^4 | not stated | cm−3 | 6 | with values reaching as high as 8$\times 10^{4}$ cm$^{-3}$ and 5$\times10^{24}$ cm$^{-2}$, respectively |
| Maximum nuclear H2 column density reported in Parameter Maps | 5×10^24 | not stated | cm−2 | 6 | with values reaching as high as 8$\times 10^{4}$ cm$^{-3}$ and 5$\times10^{24}$ cm$^{-2}$, respectively |
| Outer-CMZ H2 volume density | ∼5-6×10^3 | not stated | cm−3 | 6 | compared to outer CMZ values of $\sim$5-6$\times10^{3}$ cm$^{-3}$ and $\sim$3-4$\times10^{22}$ cm$^{-2}$. |
| Outer-CMZ H2 column density | ∼3-4×10^22 | not stated | cm−2 | 6 | compared to outer CMZ values of $\sim$5-6$\times10^{3}$ cm$^{-3}$ and $\sim$3-4$\times10^{22}$ cm$^{-2}$. |
| Nuclear CRIR | ∼4×10−13 | not stated | s−1 | 6 | We estimate CRIR values of $\zeta \sim 4 \times 10^{-13}$ s$^{-1}$ in the nucleus of the NGC 253 CMZ |
| Outer-CMZ CRIR | ∼2×10−14 | not stated | s−1 | 6 | $\zeta \sim 2 \times 10^{-14}$ s$^{-1}$ in its outer regions. |
| Inner-CMZ beam-filling factor | ≲0.1 | not stated | dimensionless | 6 | In the inner CMZ ($r\lesssim100$ pc), $\eta_{ff} \lesssim 0.1$ |
| Outer-CMZ beam-filling factor | ≳0.3 | not stated | dimensionless | 6 | in the outer CMZ ($r \gtrsim 100$ pc), $\eta_{ff} \gtrsim 0.3$. |
| Regions with X_HCN/X_HNC >4 and ζ >5×10−13 s−1 | 24 | not stated | regions | 7 | all 24 regions with $X_{\text{HCN}}/X_{\text{HNC}} > 4$ also feature $\zeta > 5\times10^{-13}$ s$^{-1}$. |
| Reported CRIR range for this work | 5×10−15–10−12 | not stated | s−1 | 6 | suggesting a CRIR range of $5\times10^{-15}-10^{-12}$ s$^{-1}$ |
| Outer-CMZ agreement with theoretical CRIR predictions | ∼0.2 | not stated | dex | 8 | The CRIR estimates in the outer CMZ are consistent within $\sim0.2$ dex with theoretical predictions of the CRIR (cite: Phan2024) derived from CMZ-averaged non-thermal emission. |
| Nuclear H2 volume density stated in Conclusions | ∼5×10^5 | not stated | cm−3 | 6 | $n_{\text{H}_2}\sim5\times10^{5}$ cm$^{-3}$ |
| Nuclear H2 column density stated in Conclusions | ∼10^24 | not stated | cm−2 | 6 | $N_{\text{H}_2}\sim10^{24}$ cm$^{-2}$ |
| Increase in predicted intensities using new collisional rates | up to a factor of 2 | not stated | dimensionless | 9 | Use of the new ortho+para-H$_2$ excitation rates result in higher (by up to a factor of 2) predicted HCN and HNC integrated transition intensities. |

## Qualitative findings

- Density increases and beam-filling factor decreases toward the nucleus, consistent with smaller, denser emitting components.  
  > "The gradients in $n_{\text{H}_2}$, $N_{\text{H}_2}$, and $\eta_{ff}$ are consistent with gas originating from smaller, higher-density and column density regions as one moves from the outer portions of the CMZ toward the nucleus of NGC 253." (Column Density, Volume Density, Filling Factor, and Kinetic Temperature)
- HCN/HNC measurements poorly constrain kinetic temperature and reveal no systematic spatial temperature trend.  
  > "Kinetic temperature, on the other hand, is poorly constrained by our models, exposing no systematic changes as a function of position in the CMZ." (Column Density, Volume Density, Filling Factor, and Kinetic Temperature)
- Some apparent high-CRIR outskirts solutions reflect inappropriate chemistry or a low-abundance numerical regime.  
  > "We are unable to derive CRIR estimates for regions with low HCN and HNC abundance as well as regions likely featuring UV-dominated or shock chemistry" (Conclusions); "our high-$\zeta$ result is not a product of the neural network, but of the chemical model’s inefficacy at such low abundances." (Low $X_\text{HCN}$ and $X_\text{HNC}$)
- Central cosmic-ray sources and possible suppressed diffusion may explain enhanced nuclear CRIR.  
  > "The high CRIR estimates in the inner CMZ are likely a result of their proximity to supernova remnants and other cosmic-ray-producing sources, as well as potential cosmic-ray diffusion suppression" (Conclusions)

## Claim tuples

- H: A neural network can replace UCLCHEM in gas-parameter inference. | E: Train on UCLCHEM abundances, test held-out abundances, and compare inference in regions 26 and 53. | R: Mean abundance recovery within 3%; nearly identical inferred parameters; runtimes ∼7% and ∼15% of direct UCLCHEM inference. | F: The emulator reproduces chemical-model inference much faster. | **supported**
- H: Dense-gas structure varies between the nucleus and outer CMZ. | E: Fit regional HCN/HNC intensities and map density, column density, and beam-filling factor. | R: Densities are enhanced centrally; inner beam filling ≲0.1 versus outer ≳0.3. | F: Nuclear emission originates from smaller, denser gas components. | **supported**
- H: CRIR is spatially enhanced in the nucleus. | E: Infer CRIR from regional HCN/HNC measurements with chemical and radiative-transfer models. | R: Nuclear ζ ∼4×10−13 s−1; outer ζ ∼2×10−14 s−1. | F: CRIR increases toward the nucleus. | **supported**
- H: The shielded-cloud chemical framework can recover conditions throughout all selected regions. | E: Inspect high-CRIR outskirts solutions using abundance ratios, absolute abundances, temperatures, and UCLCHEM comparisons. | R: 24 high-ratio regions also have high CRIR; low-abundance solutions are unreliable. | F: UV/shock chemistry and low-abundance regions prevent reliable CRIR recovery across the entire selected field. | **refuted**
- H: Molecular-emission CRIR estimates agree with non-thermal emission predictions. | E: Compare inferred CRIRs with Phan2024 CMZ-averaged transport predictions. | R: Outer-CMZ CRIR estimates agree within ∼0.2 dex. | F: The theoretical prediction is consistent with the lowest, outer-CMZ inferred CRIRs. | **supported**
- H: Local cosmic-ray sources and suppressed diffusion explain enhanced nuclear CRIR. | E: Compare spatial CRIR patterns with cosmic-ray sources and published diffusion simulations. | R: Central regions contain cosmic-ray-producing sources where CRIR is enhanced. | F: Source proximity and potential diffusion suppression are plausible explanations. | **partially**

## Reasoning

- Why this data: HCN/HNC chemistry is sensitive to cosmic rays in shielded NGC 253 gas.  
  > "(cite: Behrens2022) found that the abundances of HCN and HNC are greatly influenced by cosmic-ray chemistry in the UV-shielded environments of NGC 253." (Introduction)
- Why this method: Chemical-model computation prevented full spatial sampling; a neural-network replacement makes larger regional inference feasible.  
  > "the use of a chemical modeling code significantly prolongs this process" (Bayesian Inference with Neural Networks); "We address this issue by developing a neural network model that can replace and fulfill the role of a chemical model in our Bayesian inference algorithm" (Bayesian Inference with Neural Networks)
- Alternative: Use 3σ replacements rather than discard incomplete regions or fit fewer than eight transitions.  
  > "Rather than removing regions which do not feature a full set of 8 detected transitions for HCN and HNC or, alternatively, constraining models of those regions with fewer than 8 transitions" (Region Selection and Moment-0 Maps); "we fill in low S/N image pixels with $3\sigma$ upper-limit integrated intensities." (Region Selection and Moment-0 Maps)
- Alternative: Add density buffer points rather than retain poorly learned parameter-space edges.  
  > "we include additional column and volume density buffer points outside of our desired parameter ranges" (Training Results)
- Alternative: Compare two-phase chemistry with phase-2-only modeling.  
  > "demonstrates the differences in the posterior distributions with and without phase 1 modeling for sample regions 26 and 53." (Comparison of Cosmic-Ray Ionization Rate to Other Measurements)
- Alternative: Compare older He-scaled collisional rates with newer H2 rates.  
  > "These modeled intensities were calculated using both the “old" (He-based) and “new" (ortho+para-H$_2$-based) rates" (New Collisional Rates Analysis)
- Alternative: Test inclusion of a free beam-filling factor.  
  > "The addition of this parameter did not greatly change the median CRIR values inferred for any of our test regions" (Comparison of Cosmic-Ray Ionization Rate to Other Measurements)
- Alternative: Consider UV radiation, shocks, and low-abundance chemical-model failures as explanations for apparent high-CRIR outskirts.  
  > "one explanation for the high CRIR values outside of the inner 5$^{\prime\prime}$ is that they are not shielded against UV radiation" (High $X_\text{HCN}/X_\text{HNC}$); "Another possibility is that some of these regions are affected by shocks." (High $X_\text{HCN}/X_\text{HNC}$); "our high-$\zeta$ result is not a product of the neural network, but of the chemical model’s inefficacy at such low abundances." (Low $X_\text{HCN}$ and $X_\text{HNC}$)
- How they decided it was enough: Training stops after 20 non-improving epochs; inference stops after sampling the majority of probability density.  
  > "we cease neural network training once the calculated loss has not improved over 20 consecutive epochs" (Neural Network Architecture); "This process concludes when `UltraNest` has sampled the majority of the probability density." (Implementation with Bayesian Nested Sampling)
- Limitation (authors): Initial chemical conditions may affect phase-2 starting abundances; varying them requires rebuilding the training set.  
  > "the abundances used at the beginning of stage 2 may be sensitive to the initial conditions (e.g. UV field, elemental abundances, mode of collapse)" (Training Dataset); "varying these parameters would require reconstructing the training datset, which is not a case considered here." (Training Dataset)
- Limitation (authors): The emulator may smooth posterior structure; finer-grid testing remains necessary.  
  > "the 2D posteriors generated when including the neural network model are somewhat smoother than those produced when our algorithm includes `UCLCHEM`." (Neural Network vs. Chemical Model); "Further testing is required to determine whether a more finely-spaced grid would more closely resemble the structure seen in the 2D `UCLCHEM` posterior distributions." (Neural Network vs. Chemical Model)
- Limitation (authors): Kinetic temperature is poorly constrained.  
  > "In general, we do not constrain the kinetic temperature well with our HCN and HNC measurements" (Parameter Maps)
- Limitation (authors): The chemical framework is unsuitable for UV-dominated or shocked regions.  
  > "We are unable to derive CRIR estimates for regions with low HCN and HNC abundance as well as regions likely featuring UV-dominated or shock chemistry" (Conclusions)
- Limitation (authors): The emulator can extrapolate below the chemical grid's reliable abundance threshold.  
  > "it can still extrapolate and produce abundances below the $10^{-12}$ threshold if provided with the relevant parameter values by our nested sampling algorithm." (Low $X_\text{HCN}$ and $X_\text{HNC}$)
- Limitation (authors): Larger regions mix diffuse and dense gas and complicate comparison with previous GMC measurements.  
  > "the regions we study here are nearly twice as large in diameter and contain $\sim3.5$ times the area as those investigated in the aforementioned studies." (Comparison of Cosmic-Ray Ionization Rate to Other Measurements); "the gas parameters being averaged over a larger area, thus likely including both diffuse and dense components" (Comparison of Cosmic-Ray Ionization Rate to Other Measurements)
- Limitation (authors): SpectralRadex performs poorly at unrealistically high molecular column densities.  
  > "At very high HCN and HNC column densities ($\gtrsim 10^{18}$ cm$^{-2}$), the predicted HCN and HNC transition intensities and opacities become so large that the `SpectralRadex` models do a poor job of predicting integrated intensities." (New Collisional Rates Analysis)
- Limitation (authors): The timing of observable cosmic-ray suppression of star formation is uncertain.  
  > "It is unclear, though, at exactly what point from the beginning of a starburst phase cosmic-ray feedback is expected to noticeably affect star formation." (Cosmic Ray Enhancement in Star-forming Regions)
- Caveat (inferred, ours): The reported training/validation/test percentages sum to 135%; the validation percentage also conflicts with its point count.
- Caveat (inferred, ours): The Conclusions give nuclear n_H2 ∼5×10^5 cm−3, inconsistent with the Parameter Maps maximum of 8×10^4 cm−3 and Table 3's central log-density range.
- Caveat (inferred, ours): The likelihood compares substituted upper-limit intensities as flux measurements; no censored-data likelihood is described.
- Caveat (inferred, ours): Random linewidth replacements introduce stochastic measurement changes without a stated seed or sensitivity test.
- Caveat (inferred, ours): The 15% flux uncertainty is not accompanied by a stated covariance treatment across transitions.
- Caveat (inferred, ours): Agreement with UCLCHEM validates the emulator against its parent model, rather than independently validating the chemical assumptions.
- Caveat (inferred, ours): Diffusion suppression is an interpretation supported by comparisons, rather than a directly fitted or measured diffusion coefficient.
- Caveat (inferred, ours): The supplied text lacks figure captions and numerical posterior tables needed to resolve source-level uncertainties and exclusions.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: HERA GitHub link provided  
  > "https://github.com/ebehrens97/HERA" (Region Selection and Moment-0 Maps)
- Missing: Observation/reduction details explicitly delegated to ALCHEMI-ACA and Behrens2022.
- Missing: Exact input cubes and region definitions.
- Missing: Machine-readable regional measurements mentioned by the paper but absent from the supplied text.
- Missing: Full chemical model configuration and precise abundance extraction time.
- Missing: Trained neural-network weights, training/inference scripts, software versions, and corrected dataset split.
- Missing: Radiative-transfer linewidth and background/geometry settings.
- Missing: Numerical UltraNest stopping and sampling configuration.
- Missing: Full posterior summaries, numerical uncertainties, and final region rejection list.
- Missing: Resolution of the conflicting nuclear volume-density numbers.
- Data volume (inferred): not stated
- Score (inferred): 5/5, On a 0–10 scale: project codes, transitions, main model grid, neural-network architecture, priors, likelihood, and several validation tests are specified. Reduction is inherited, key executable settings and trained weights are absent, and numerical inconsistencies remain.
- Rediscovery candidate: no, The main results are numeric, but public data availability is not stated and the supplied recipe lacks essential reduction, model, and inference settings.

## Links

- Method: (cite: ALCHEMI-ACA) (ALCHEMI observations and data reduction.)
- Method: (cite: Behrens2022) (Integrated-intensity extraction and earlier Bayesian chemical/radiative-transfer inference.)
- Method: (cite: Holdship2022) (Earlier Bayesian inference framework and two-phase chemical modeling comparison.)
- Method: (cite: Holdship2017) (UCLCHEM chemical modeling code.)
- Method: (cite: HernandezVera2017) (Adopted HCN/HNC ortho- and para-H2 collisional excitation rates.)
- Method: (cite: Dumouchel2010) (Older He-based collisional rates used in sensitivity comparisons.)
- Method: (cite: ultranest14; ultranest19; ultranest21) (Nested sampling and UltraNest implementation.)
- Method: (cite: heyl2023) (Numerical unreliability of very low chemical abundances.)
- Companion: (cite: ALCHEMI-ACA) (Parent ALCHEMI survey and reduction reference.)
- Companion: (cite: Behrens2022) (Earlier HCN/HNC inference study directly extended and compared here.)
- Companion: (cite: Holdship2022) (Related ALCHEMI CRIR inference using H3O+ and SO.)
- Companion: (cite: Tanaka2024) (Related ALCHEMI density and temperature comparisons.)
- Companion: (cite: Butterworth2024) (Related source-size evidence motivating beam filling.)
- Related: ALCHEMI: ALMA Comprehensive High-resolution Extragalactic Molecular Inventory

## Checks

```json
{
 "quotes": 225,
 "quotes_ok": 225,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 162,
  "stated": 119,
  "rate": 0.735
 },
 "evidence_ok": true
}
```
