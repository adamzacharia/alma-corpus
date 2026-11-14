# Constraining the magnetic field strength of a flaring radio core in the compact steep spectrum source 3C 138

`2026A&A...710A..63L` | Astronomy and Astrophysics 2026 | first author: Li, Shan | arXiv: 2605.18283 | DOI: 10.1051/0004-6361/202659759

Card schema 1.0 | model gemini-4-argon | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars
- Question: Estimate the synchrotron self-absorption (SSA) magnetic field ($B_{\rm SSA}$) in the SSA core of the compact steep spectrum quasar 3C 138 during its high state and compare it with the equipartition magnetic field ($B_{\rm eq}$) to assess the core field environment.  
  > "We estimated the synchrotron self-absorption (SSA) magnetic field ($B_{\rm SSA}$) in the SSA core of 3C 138 during its high state and compared it with the equipartition magnetic field ($B_{\rm eq}$) to assess the core field environment." (abstract)
- Target **3C 138**: coordinates _not stated_; z/distance z = 0.759  
  > "The CSS quasar 3C 138 ($z=0.759$; (cite: hewitt1989first)) is one such case, showing both radio variability and detected high-energy activity." (Introduction); "At $z = 0.759$, 1 mas corresponds to 7.58 pc, and $1~{\rm mas~yr^{-1}} = 43.5~c$." (Introduction); distance from (cite: hewitt1989first)  
  > "The CSS quasar 3C 138 ($z=0.759$; (cite: hewitt1989first)) is one such case, showing both radio variability and detected high-energy activity." (Introduction); "At $z = 0.759$, 1 mas corresponds to 7.58 pc, and $1~{\rm mas~yr^{-1}} = 43.5~c$." (Introduction)

## Data provenance

- ALMA projects: 2011.0.00001.CAL
- bands: _not stated_
- frequencies and spectral setup: approximately 97.5-343 GHz (ALMA Calibrator Source Catalogue)  
  > "We also used the Atacama Large Millimeter/submillimeter Array (ALMA) Calibrator Source Catalogue (cite: kneissl2023operational), which provides well-calibrated flux estimates for standard ALMA calibrators, thereby extending our spectral coverage to the millimeter/submillimeter regime (approximately $97.5$–$343$ GHz)." (Archive data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival (ALMA Calibrator Source Catalogue)  
  > "We also used the Atacama Large Millimeter/submillimeter Array (ALMA) Calibrator Source Catalogue (cite: kneissl2023operational), which provides well-calibrated flux estimates for standard ALMA calibrators, thereby extending our spectral coverage to the millimeter/submillimeter regime (approximately $97.5$–$343$ GHz)." (Archive data)
- Other facility **Extended Korean VLBI Network (KVN)**: Simultaneous VLBI observations at 22, 43, 86, and 129 GHz on 2024 December 12 and 2025 January 10  
  > "We conducted simultaneous VLBI observations at 22, 43, 86, and 129 GHz on 2024 December 12 and 2025 January 10 with the extended KVN, which comprises the original three 21 m antennas (Yonsei, Ulsan, and Tamna) plus KVN Pyeongchang (KPC)." (KVN observations)
- Other facility **Very Large Array (VLA)**: 1-50 GHz archival data from project TCAL0009 at four epochs (2022 March 20, 2023 July 1, 2024 December 20, and 2025 January 19)  
  > "To capture total flux variations, including large-scale jet emission, we used VLA data (1–50 GHz) from the observing-support test project TCAL0009 (PI: Lorant Sjouwerman)" (Archive data); "We focused on four epochs (2022 March 20, 2023 July 1, 2024 December 20, and 2025 January 19)." (Archive data)
- Other facility **Very Long Baseline Array (VLBA)**: Three epochs at 23.5 GHz (2022 December 14, 2024 June 18, and 2025 June 21) from project UC003  
  > "Complementing our KVN analysis, we used three higher-resolution Very Long Baseline Array (VLBA) epochs at 23.5 GHz (2022 December 14, 2024 June 18, and 2025 June 21) from project UC003 (PI: Phillip Cigan) to trace the flux and structural evolution of the VLBA core and the inner jet." (Archive data)
- External data: ALMA Calibrator Source Catalogue flux estimates (approximately 97.5-343 GHz)  
  > "We also used the Atacama Large Millimeter/submillimeter Array (ALMA) Calibrator Source Catalogue (cite: kneissl2023operational), which provides well-calibrated flux estimates for standard ALMA calibrators, thereby extending our spectral coverage to the millimeter/submillimeter regime (approximately $97.5$–$343$ GHz)." (Archive data) [from (cite: kneissl2023operational)]
- External data: Median jet-opening index epsilon = 0.97  
  > "We adopt $k_{\rm r}=1$ as a commonly used empirical value in core-shift scaling (cite: lobanov1998ultracompact), and the median $\epsilon$ value of 0.97 from (cite: algaba2017resolving)." (Size scaling for the SSA region) [from (cite: algaba2017resolving)]
- External data: Equipartition brightness temperature T_B,eq = 5 x 10^10 K  
  > "Here we adopt $T_{\rm B,eq}=5\times10^{10}$ K (cite: hovatta2009)." (Variability Doppler factor) [from (cite: hovatta2009)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: 6.5.4 (for VLA data)  
  > "To capture total flux variations, including large-scale jet emission, we used VLA data (1–50 GHz) from the observing-support test project TCAL0009 (PI: Lorant Sjouwerman) and processed the data with the Common Astronomy Software Applications pipeline, version 6.5.4 (cite: mcmullin2007casa; 2022PASP..134k4501C)." (Archive data)
- pipeline version: _not stated_
- archive products used as is: ALMA Calibrator Source Catalogue flux estimates used directly; VLA data processed with CASA pipeline 6.5.4  
  > "To capture total flux variations, including large-scale jet emission, we used VLA data (1–50 GHz) from the observing-support test project TCAL0009 (PI: Lorant Sjouwerman) and processed the data with the Common Astronomy Software Applications pipeline, version 6.5.4 (cite: mcmullin2007casa; 2022PASP..134k4501C)." (Archive data); "We also used the Atacama Large Millimeter/submillimeter Array (ALMA) Calibrator Source Catalogue (cite: kneissl2023operational), which provides well-calibrated flux estimates for standard ALMA calibrators, thereby extending our spectral coverage to the millimeter/submillimeter regime (approximately $97.5$–$343$ GHz)." (Archive data)
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

- KVN image total flux density uncertainties (10% at 22/43 GHz, 20% at 86 GHz, 30% at 129 GHz)  
  > "For image total flux density, we used 10% (22/43 GHz), 20% (86 GHz), and 30% (129 GHz) uncertainties (cite: lee2016interferometric)." (KVN observations) [from (cite: lee2016interferometric)]
- Uncertainties of Gaussian model parameters  
  > "Uncertainties of the Gaussian model parameters were estimated following (cite: Fomalont1999) and (cite: lee2008global)." (KVN observations) [from (cite: Fomalont1999) and (cite: lee2008global)]
- Single-zone SSA model for spectral fitting  
  > "We therefore fitted the eastern component with a single power law (PL), $S_\nu \propto \nu^{\alpha}$, where $\alpha$ is the spectral index, and modeled the western component with a single-zone SSA model (cite: turler2000modelling):" (Spectral analysis) [from (cite: turler2000modelling)]
- SSA magnetic field formula  
  > "Given $S_{\rm m}$, $\nu_{\rm m}$, and $\alpha_0$ from the SSA fit (Fig. 2), together with $d_{\rm m}$ and $\delta_{\rm var}$, we compute the SSA magnetic field strength from (cite: marscher1983accurate):" (Magnetic field strength formulae) [from (cite: marscher1983accurate)]
- Equipartition magnetic field formula  
  > "The equipartition magnetic field strength is estimated following (cite: kataoka2005x):" (Magnetic field strength formulae) [from (cite: kataoka2005x)]

### Not stated but needed to reproduce (our reading)

- Exact dates and frequencies of the ALMA Calibrator Source Catalogue measurements used for the Gaussian-process interpolation
- Kernel and hyperparameters used for the Gaussian-process regression of the ALMA light curves
- Exact fixed value of the optically thick spectral index alpha_t in the PL+SSA fits to the VLA+ALMA spectra
- Details of the sampler and priors used to obtain the SSA-fit posterior

## Analysis recipe

1. **Calibrate, image, and model-fit KVN and VLBA visibilities**: Calibrate KVN visibilities with AIPS KVN pipeline; perform interferometric imaging and circular 2D Gaussian model fitting in Difmap for KVN and VLBA epochs.  
  > "The data were correlated with DiFX (December 2024) and a GPU-based correlator (January 2025), then calibrated in the Astronomical Image Processing System (cite: greisen2003aips) with a KVN pipeline (cite: hodgson2016automatic)." (KVN observations); "Interferometric imaging and circular two-dimensional Gaussian model fitting were performed with Difmap (cite: shepherd1997difmap)." (KVN observations)
   - software: DiFX, AIPS, KVN pipeline, Difmap
   - parameter: Two circular Gaussian components (W and E) separated by ~5 mas  
  > "Via Gaussian model fitting, we identified two components separated by about 5 mas, with the fainter eastern component lying to the southeast of the brighter western one at a position angle (PA) of about $105^\circ$ (Table 3)." (Multifrequency flux and morphology)
   - assumption: Flux density uncertainties of 10% (22/43 GHz), 20% (86 GHz), and 30% (129 GHz)  
  > "For image total flux density, we used 10% (22/43 GHz), 20% (86 GHz), and 30% (129 GHz) uncertainties (cite: lee2016interferometric)." (KVN observations)
   - fitting: Circular 2D Gaussian model fitting in Difmap; parameter uncertainties from post-fit rms and SNR following Fomalont (1999) and Lee et al. (2008).  
  > "Uncertainties of the Gaussian model parameters were estimated following (cite: Fomalont1999) and (cite: lee2008global)." (KVN observations)
   - validation: Comparison of fitted sizes against minimum resolvable size (Lobanov 2005) and consistency across two epochs.  
  > "The eastern component is clearly resolved, with fitted sizes larger than the minimum resolvable size, whereas the western component is more compact and is constrained as an upper limit in some bands (cite: lobanov2005resolution)." (Multifrequency flux and morphology)
2. **Fit component spectra and broadband VLA+ALMA spectra**: Fit KVN eastern component with a power law (PL) and western component with a single-zone SSA model. Interpolate ALMA Calibrator Catalogue flux densities with Gaussian-process (GP) regression, pair with four VLA epochs, and fit combined VLA+ALMA spectra with PL and PL+SSA models.  
  > "We therefore fitted the eastern component with a single power law (PL), $S_\nu \propto \nu^{\alpha}$, where $\alpha$ is the spectral index, and modeled the western component with a single-zone SSA model (cite: turler2000modelling):" (Spectral analysis); "To probe the time variability of the broadband spectrum, we interpolated the ALMA flux densities using Gaussian-process (GP) regression, paired them with the four VLA epochs, and fitted the combined VLA+ALMA spectra with both a PL model and a PL+SSA model for each epoch." (Spectral analysis)
   - software: CASA
   - assumption: Single-zone homogeneous synchrotron self-absorption model for the core  
  > "We therefore fitted the eastern component with a single power law (PL), $S_\nu \propto \nu^{\alpha}$, where $\alpha$ is the spectral index, and modeled the western component with a single-zone SSA model (cite: turler2000modelling):" (Spectral analysis)
   - fitting: Model selection between PL and PL+SSA using reduced chi^2 and Bayesian information criterion (BIC).  
  > "We then selected the preferred model by comparing the reduced $\chi^2$ and the Bayesian information criterion." (Spectral analysis)
   - validation: Comparison of reduced chi^2 and BIC between PL and PL+SSA models.  
  > "We then selected the preferred model by comparing the reduced $\chi^2$ and the Bayesian information criterion." (Spectral analysis)
3. **Estimate SSA core size, variability Doppler factor, and magnetic field strengths**: Scale 23.5 GHz VLBA core size to the SSA turnover frequency to get d_m; fit VLBA core light curve in log space to get variability timescale tau_var, T_B^var, and delta_var; compute B_SSA and B_eq and propagate uncertainties via Monte Carlo sampling.  
  > "We estimated the SSA magnetic field strength and the equipartition magnetic field strength of the KVN core for the first epoch (2024 December 12) using the SSA spectral parameters listed in Fig. 2, together with the SSA region size ($d_{\rm m}$) scaled from the bright-state VLBA core size and the Doppler factor ($\delta$) estimated from VLBA core variability (Appendix 6)." (Magnetic field strength); "we propagated uncertainties via Monte Carlo sampling by drawing $S_{\rm m}$, $\nu_{\rm m}$ and $\alpha_0$ from the SSA-fit posterior and $d_{\rm VLBA}$ from its inferred distribution." (Uncertainty propagation and sensitivity tests)
   - parameter: d_VLBA = 0.06 +/- 0.01 mas, k_r = 1, epsilon = 0.97, T_B,eq = 5 x 10^10 K, eta = 1  
  > "We therefore adopt the 2025 June VLBA core size ($d_{\rm VLBA}=0.06\pm0.01$ mas), measured in a bright-state epoch close in time to the KVN observations" (Size scaling for the SSA region); "We adopt $k_{\rm r}=1$ as a commonly used empirical value in core-shift scaling (cite: lobanov1998ultracompact), and the median $\epsilon$ value of 0.97 from (cite: algaba2017resolving)." (Size scaling for the SSA region); "Here we adopt $T_{\rm B,eq}=5\times10^{10}$ K (cite: hovatta2009)." (Variability Doppler factor)
   - assumption: Cosmology: H_0 = 67.8 km s^-1 Mpc^-1, Omega_m = 0.308, Omega_Lambda = 0.692  
  > "The adopted cosmology is $H_{0} = 67.8~{\rm km~s^{-1}~Mpc^{-1}}$, $\Omega_{\rm m} = 0.308$, and $\Omega_{\rm \Lambda} = 0.692$ (cite: wright2006)." (Introduction)
   - assumption: Factor 1.6 converts Gaussian FWHM to uniform disk angular diameter; eta = 1 for ratio of proton+electron to electron energy densities  
  > "where the factor $1.6$ converts the full width at half maximum of a circular Gaussian component to the equivalent angular diameter of a uniform disk (cite: pearson1995)" (Size scaling for the SSA region); "assuming $\eta=1$ (the ratio of proton + electron to electron energy densities)." (Magnetic field strength formulae)
   - fitting: Least-squares fit to VLBA core light curve in log space; Monte Carlo sampling for magnetic field uncertainty propagation.  
  > "we fit the VLBA core light curve in log space with a least-squares method," (Variability Doppler factor); "we propagated uncertainties via Monte Carlo sampling by drawing $S_{\rm m}$, $\nu_{\rm m}$ and $\alpha_0$ from the SSA-fit posterior and $d_{\rm VLBA}$ from its inferred distribution." (Uncertainty propagation and sensitivity tests)
   - validation: Sensitivity tests varying the jet-opening index (epsilon) and core-shift index (k_r) within plausible ranges.  
  > "We propagated uncertainties via Monte Carlo sampling, and we further tested the sensitivity of the result to the assumed geometric and opacity scalings by varying jet-opening index and the core-shift index within plausible ranges." (Magnetic field strength)

## Software

- **DiFX** : Correlating KVN December 2024 observations  
  > "The data were correlated with DiFX (December 2024) and a GPU-based correlator (January 2025), then calibrated in the Astronomical Image Processing System (cite: greisen2003aips) with a KVN pipeline (cite: hodgson2016automatic)." (KVN observations)
- **AIPS** : Calibrating KVN visibility data  
  > "The data were correlated with DiFX (December 2024) and a GPU-based correlator (January 2025), then calibrated in the Astronomical Image Processing System (cite: greisen2003aips) with a KVN pipeline (cite: hodgson2016automatic)." (KVN observations)
- **KVN pipeline** : Automated calibration of KVN data in AIPS  
  > "The data were correlated with DiFX (December 2024) and a GPU-based correlator (January 2025), then calibrated in the Astronomical Image Processing System (cite: greisen2003aips) with a KVN pipeline (cite: hodgson2016automatic)." (KVN observations)
- **Difmap** : Interferometric imaging and circular 2D Gaussian model fitting  
  > "Interferometric imaging and circular two-dimensional Gaussian model fitting were performed with Difmap (cite: shepherd1997difmap)." (KVN observations)
- **CASA** 6.5.4: Pipeline processing of archival VLA data  
  > "To capture total flux variations, including large-scale jet emission, we used VLA data (1–50 GHz) from the observing-support test project TCAL0009 (PI: Lorant Sjouwerman) and processed the data with the Common Astronomy Software Applications pipeline, version 6.5.4 (cite: mcmullin2007casa; 2022PASP..134k4501C)." (Archive data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| KVN SSA core turnover frequency | 33 | not stated | GHz | 2 | The KVN SSA core shows a turnover at about 33 GHz and a peak flux of about 1.45 Jy. |
| KVN SSA core peak flux density | 1.45 | not stated | Jy | 2 | The KVN SSA core shows a turnover at about 33 GHz and a peak flux of about 1.45 Jy. |
| SSA region size (d_m) | 0.07 | 0.01 | mas | 3 | We adopted $d_{\rm m}=0.07\pm0.01$ mas and $\delta_{\rm var}=2.36^{+0.35}_{-0.38}$, noting that $\delta_{\rm var}$ is an approximate constraint and likely a lower limit given the sparse temporal sampling and possible unresolved substructure. |
| Variability Doppler factor (delta_var) | 2.36 | +0.35/-0.38 | dimensionless | 3 | We adopted $d_{\rm m}=0.07\pm0.01$ mas and $\delta_{\rm var}=2.36^{+0.35}_{-0.38}$, noting that $\delta_{\rm var}$ is an approximate constraint and likely a lower limit given the sparse temporal sampling and possible unresolved substructure. |
| SSA magnetic field strength (B_SSA) | 10.12 | +9.59/-5.11 | mG | 3 | Using these parameters, we derived $B_{\rm SSA}=10.12^{+9.59}_{-5.11}$ mG and $B_{\rm eq}=200.77^{+44.08}_{-33.79}$ mG, which yields $B_{\rm SSA}/B_{\rm eq}=0.05^{+0.06}_{-0.03}\ll 1$. |
| Equipartition magnetic field strength (B_eq) | 200.77 | +44.08/-33.79 | mG | 3 | Using these parameters, we derived $B_{\rm SSA}=10.12^{+9.59}_{-5.11}$ mG and $B_{\rm eq}=200.77^{+44.08}_{-33.79}$ mG, which yields $B_{\rm SSA}/B_{\rm eq}=0.05^{+0.06}_{-0.03}\ll 1$. |
| Magnetic field ratio (B_SSA / B_eq) | 0.05 | +0.06/-0.03 | dimensionless | 3 | Using these parameters, we derived $B_{\rm SSA}=10.12^{+9.59}_{-5.11}$ mG and $B_{\rm eq}=200.77^{+44.08}_{-33.79}$ mG, which yields $B_{\rm SSA}/B_{\rm eq}=0.05^{+0.06}_{-0.03}\ll 1$. |
| VLA+ALMA SSA turnover frequency (2024-12-20) | 52.88 | +28.84/-20.19 | GHz | 2 | / 2024-12-20 / $-0.53\pm0.03$ / $0.62_{-0.25}^{+0.30}$ / $52.88_{-20.19}^{+28.84}$ / $-1.00_{-0.43}^{+0.20}$ / |
| VLA+ALMA SSA turnover frequency (2025-01-19) | 70.61 | +29.34/-29.53 | GHz | 2 | / 2025-01-19 / $-0.50\pm0.03$ / $0.63_{-0.24}^{+0.22}$ / $70.61_{-29.53}^{+29.34}$ / $-1.39_{-0.40}^{+0.43}$ / |

## Qualitative findings

- The western KVN component is identified as the SSA core based on its flat-inverted spectrum between 22 and 43 GHz, while the eastern component follows a steep power law consistent with an optically thin inner jet.  
  > "The KVN western component shows a flat–inverted spectrum between 22 and 43 GHz and is well described by an SSA model, supporting its identification as the SSA core. The eastern feature follows a single steep PL, consistent with an optically thin inner jet component (Fig. 2)." (SSA core spectrum and temporal evolution)
- The broadband VLA+ALMA spectrum transitions from a single steep power-law state in 2022-2023 to a PL+SSA state in 2024-2025.  
  > "For the VLA data, as shown in Fig. 7, a spectral inflection is detected only in 2024 and 2025, whereas the 2022–2023 spectra are adequately described by a single steep PL. This indicates a transition from a PL-only state to a PL+SSA state." (SSA core spectrum and temporal evolution)
- The SSA core is strongly particle-dominated (B_SSA / B_eq << 1) and the radio flux variability since 2022 is driven by the compact core rather than the extended jet.  
  > "The multi-year radio brightening is core-dominated and the core magnetic field is below equipartition, implying a particle-dominated emitting region with only mild Doppler boosting." (Conclusion)

## Claim tuples

- H: The multi-year radio brightening of 3C 138 is driven by a compact, particle-dominated SSA core rather than magnetic-field-dominated emission or kiloparsec-scale jet interactions. | E: Simultaneous four-band (22, 43, 86, 129 GHz) KVN VLBI imaging and Gaussian model fitting, combined with archival VLBA, VLA, and ALMA Calibrator Source Catalogue data to fit SSA models and compute B_SSA and B_eq. | R: The western KVN core turns over at ~33 GHz with peak flux ~1.45 Jy, yielding B_SSA = 10.12 (+9.59/-5.11) mG and B_eq = 200.77 (+44.08/-33.79) mG, or B_SSA / B_eq = 0.05 (+0.06/-0.03) << 1, while VLBA/VLA monitoring shows the flux rise is confined to the core. | F: The flaring core of 3C 138 is strongly particle-dominated and drives the observed radio flux variability. | **supported**
- H: The broadband VLA+ALMA radio-to-submillimeter spectrum reflects the emergence of the flaring SSA core component during the 2024-2025 high state. | E: Interpolated ALMA Calibrator Catalogue flux densities with Gaussian-process regression, combined them with four VLA epochs (2022-2025), and compared single PL and PL+SSA spectral fits using reduced chi^2 and BIC. | R: The 2022-2023 broadband spectra are well fit by a single power law, whereas the 2024-2025 spectra require an additional SSA component with turnover frequencies of ~53 GHz and ~71 GHz. | F: The broadband spectrum transitioned from a PL-only state to a PL+SSA state during the flare, with a higher inferred turnover frequency than the KVN core due to resolution blending and/or core inhomogeneity. | **supported**

## Reasoning

- Why this data: Simultaneous four-band KVN VLBI observations resolve the compact core and inner jet without temporal variability ambiguity, while archival VLA, ALMA Calibrator Catalogue, and VLBA data provide broadband spectral constraints, kpc-scale jet monitoring, and higher-resolution core size/variability measurements.  
  > "We also used the Atacama Large Millimeter/submillimeter Array (ALMA) Calibrator Source Catalogue (cite: kneissl2023operational), which provides well-calibrated flux estimates for standard ALMA calibrators, thereby extending our spectral coverage to the millimeter/submillimeter regime (approximately $97.5$–$343$ GHz)." (Archive data); "The simultaneous four-band KVN observations enabled us to determine the spectra of the two components and identify the core." (Spectral analysis)
- Why this method: Gaussian-process regression interpolates non-simultaneous ALMA calibrator measurements to match VLA epochs; Monte Carlo sampling accounts for the strong non-linearity of the magnetic field equations.  
  > "To probe the time variability of the broadband spectrum, we interpolated the ALMA flux densities using Gaussian-process (GP) regression, paired them with the four VLA epochs, and fitted the combined VLA+ALMA spectra with both a PL model and a PL+SSA model for each epoch." (Spectral analysis); "we propagated uncertainties via Monte Carlo sampling by drawing $S_{\rm m}$, $\nu_{\rm m}$ and $\alpha_0$ from the SSA-fit posterior and $d_{\rm VLBA}$ from its inferred distribution." (Uncertainty propagation and sensitivity tests)
- Alternative: Kiloparsec-scale jet-interstellar medium interaction as the driver of the radio brightening (rejected because the flux rise is core-dominated while the extended jet remains nearly constant).  
  > "Multifrequency, multi-scale data show that the flux rise since 2022 is core-dominated (Fig. 6), meaning a kiloparsec-scale jet–interstellar medium interaction is likely not the primary driver of the integrated flux increase." (Core brightening and high-energy emission)
- Alternative: Single power-law (PL) vs. PL+SSA models for the broadband VLA+ALMA spectra (PL preferred in 2022-2023, PL+SSA preferred in 2024-2025).  
  > "For the VLA data, as shown in Fig. 7, a spectral inflection is detected only in 2024 and 2025, whereas the 2022–2023 spectra are adequately described by a single steep PL." (SSA core spectrum and temporal evolution)
- How they decided it was enough: _not stated_
- Limitation (authors): VLA and ALMA observations are not simultaneous and have unmatched angular resolutions.  
  > "As the two arrays are not simultaneous, and have unmatched angular resolutions, these fits should be interpreted with caution." (Spectral analysis)
- Limitation (authors): Sparse temporal sampling of the VLBA core (three epochs) and possible unresolved substructure mean tau_var is an upper limit, delta_var is likely underestimated (a lower limit), and B_SSA, B_eq, and B_SSA/B_eq are upper limits.  
  > "Given the sparse sampling of the VLBA core flux density (three epochs) and the possibility of unresolved substructure within the VLBA core, the derived $\tau_{\rm var}$ should be regarded as an upper limit." (Variability Doppler factor); "Since $\delta_{\rm var}$ is likely underestimated, the derived $B_{\rm SSA}$, $B_{\rm eq}$, and $B_{\rm SSA}/B_{\rm eq}$ should be interpreted as upper limits, subject to a corresponding systematic uncertainty." (Magnetic field strength formulae)
- Limitation (authors): The 129 GHz KVN image is unavailable in the second epoch due to poor weather, and the second-epoch 86 GHz core size is affected by poorer data quality and calibration effects.  
  > "The 129 GHz image is available only for the first epoch due to poor weather." (Multifrequency flux and morphology); "The larger 86 GHz size of the western component in the second epoch is likely influenced mainly by poorer data quality and calibration effects." (Multifrequency flux and morphology)
- Caveat (inferred, ours): The SSA magnetic field scales as the fourth power of the core size (d_m^4), which is not directly resolved at the turnover frequency in KVN data but extrapolated from a single 23.5 GHz VLBA epoch assuming canonical core-shift and jet-opening indices.
- Caveat (inferred, ours): Variability Doppler factor is derived from only three VLBA epochs over 2.5 years, which strongly under-samples rapid flare timescales.
- Caveat (inferred, ours): Combining arcsecond-scale VLA and ALMA total flux densities blends the kpc jet, inner mas jet, and core, making the broadband SSA parameters an effective composite rather than an isolated core measurement.

## Reproducibility

- Data public (paper): ALMA Calibrator Source Catalogue is public via URL; VLA project TCAL0009 and VLBA project UC003 are archival; KVN data public status is not stated.  
  > "We also used the Atacama Large Millimeter/submillimeter Array (ALMA) Calibrator Source Catalogue (cite: kneissl2023operational), which provides well-calibrated flux estimates for standard ALMA calibrators, thereby extending our spectral coverage to the millimeter/submillimeter regime (approximately $97.5$–$343$ GHz)." (Archive data); "This work makes use of ALMA data (ADS/JAO.ALMA#2011.0.00001.CAL)." (Acknowledgements)
- Products in archive: Calibrated flux density estimates from the ALMA Calibrator Source Catalogue  
  > "We also used the Atacama Large Millimeter/submillimeter Array (ALMA) Calibrator Source Catalogue (cite: kneissl2023operational), which provides well-calibrated flux estimates for standard ALMA calibrators, thereby extending our spectral coverage to the millimeter/submillimeter regime (approximately $97.5$–$343$ GHz)." (Archive data)
- Missing: Raw or calibrated KVN visibility data (not stated as publicly archived)
- Missing: Exact ALMA Calibrator Catalogue query table (timestamps, frequencies, and flux values) used for GP interpolation
- Missing: Gaussian-process regression kernel and hyperparameter settings
- Missing: Exact fixed value of alpha_t used in the SSA spectral fits
- Data volume (inferred): < 1 MB for the ALMA Calibrator Catalogue table; ~10-50 GB for the archival VLA and VLBA visibility datasets and KVN visibilities
- Score (inferred): 65/5, The analytic equations, assumptions, and intermediate component flux tables (KVN, VLBA, VLA) are thoroughly reported in the text and appendices, allowing direct reproduction of the magnetic field calculations and KVN spectral fits from the tables. However, the KVN raw visibilities are not stated to be public, and the exact GP interpolation settings and ALMA flux table are not explicitly provided.
- Rediscovery candidate: yes, The broadband VLA+ALMA spectral evolution and VLBA core variability can be fully reproduced from public NRAO archives (TCAL0009, UC003) and the public ALMA Calibrator Source Catalogue, and the magnetic field calculations can be reproduced directly from the published tables and equations.

## Links

- Method: (cite: hodgson2016automatic) (Automated KVN calibration pipeline in AIPS)
- Method: (cite: Fomalont1999) (Estimation of Gaussian model-fit parameter uncertainties)
- Method: (cite: lee2008global) (Estimation of Gaussian model-fit parameter uncertainties in VLBI)
- Method: (cite: turler2000modelling) (Single-zone synchrotron self-absorption (SSA) spectral model)
- Method: (cite: marscher1983accurate) (Formula for SSA magnetic field strength)
- Method: (cite: kataoka2005x) (Formula for equipartition magnetic field strength)
- Method: (cite: kneissl2023operational) (ALMA Calibrator Source Catalogue flux density measurements)
- Related: ALMA Calibrator Source Catalogue (ADS/JAO.ALMA#2011.0.00001.CAL)
- Related: VLA project TCAL0009
- Related: VLBA project UC003

## Checks

```json
{
 "quotes": 82,
 "quotes_ok": 82,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 7,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00001.CAL"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 50,
  "rate": 0.61
 },
 "evidence_ok": true
}
```
