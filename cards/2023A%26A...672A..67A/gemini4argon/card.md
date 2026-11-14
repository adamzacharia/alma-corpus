# Robust analysis of differential Faraday rotation based on interferometric closure observables

`2023A&A...672A..67A` | Astronomy and Astrophysics 2023 | first author: Albentosa-Ruiz, E. | arXiv: 2303.04052 | DOI: 10.1051/0004-6361/202244573

Card schema 1.0 | model gemini-4-argon | depth full | type technical_calibration_or_instrument

## Science

- Fields: agn_and_quasars, instrumentation
- Question: Can newly-introduced complex interferometric closure observables (closure traces) be used to extract robust, calibration-independent information on source polarization structure and differential Faraday Rotation across frequency?  
  > "In this paper, we apply the newly-introduced closure traces to extract robust information on the polarization structure of the sources and their possible dependence on the observation frequency." (Introduction); "Finally, we show in Section 4 the results of our test and discuss the possibility of using closure traces to determine Faraday Rotation (FR) from broadband interferometric observations." (Introduction)
- Target **M87**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01154.V
- bands: Band 6 (212 GHz to 230 GHz)  
  > "The observations were performed in the ALMA Band 6 (ranging from $212$ GHz to $230$ GHz)." (Observations and simulated data)
- frequencies and spectral setup: 2 sidebands, 4 spectral windows of 2 GHz each centered at 213.1 GHz, 215.1 GHz, 227.1 GHz, and 229.1 GHz  
  > "Each of these sidebands has two spectral windows (spws) of $2$ GHz each." (Observations and simulated data); "The measurements were taken in four different spws ($0$, $1$, $2$ and $3$, corresponding to frequencies centered at $213.1$ GHz, $215.1$ GHz, $227.1$ GHz and $229.1$ GHz, respectively) for all epochs of the EHT campaign (cite: Goddi2019)." (Observations and simulated data)
- continuum bandwidth: _not stated_
- arrays: 12-m array (33 antennas)  
  > "To observe this source, ALMA used an array of 33 antennas, with 12-meter diameters each, with unprojected baseline lengths ranging from $15.1$ m to $160.7$ m." (Observations and simulated data)
- configurations: _not stated_
- baselines: 15.1 m to 160.7 m (unprojected)  
  > "To observe this source, ALMA used an array of 33 antennas, with 12-meter diameters each, with unprojected baseline lengths ranging from $15.1$ m to $160.7$ m." (Observations and simulated data)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2017 April 6, between 00:52 and 08:02 UT  
  > "In this paper, we focus on the M87* track observed on 2017 April 6, between 00:52 and 08:02 UT (cite: Goddi2021complete)." (Observations and simulated data)
- pi or archival as stated: _not stated_
- External data: Polarization structure image of M87 AGN and jet and Rotation Measure (~1.5 x 10^5 rad/m^2) from ALMA EHT observations  
  > "Figure 1 shows the polarization structure of the AGN and the jet of M87, obtained from the ALMA data (cite: Goddi2021complete)." (Observations and simulated data); "compared to the value of $\sim 1.5 \times 10^5$ rad/m$^{2}$ for M87*, obtained from the ALMA EHT data (cite: Goddi2021complete; TFM)." (Simulations and model parameters) [from Goddi et al. 2021 (cite: Goddi2021complete)]
- External data: RM map of M87  
  > "In Fig. 2, we show the RM map of M87, obtained from the results presented in (cite: TFG)." (Observations and simulated data) [from Albentosa-Ruiz 2020 (cite: TFG)]
- Simulation/model as data: Synthetic full-polarization visibility dataset of an M87-like source consisting of three compact (delta) components (core, knot A, knot B) on the exact ALMA baseline coordinates, with simulated core RM of ~0.35 x 10^7 rad/m^2 and 0.5 mJy Gaussian visibility noise  
  > "we generate synthetic data of a source with the more relevant components of M87 (i.e. a core and two peaks of polarization intensity) based on the exact baseline coordinates of the observations described in the previous section." (Simulations and model parameters); "increasing the RM of our simulated source to $\sim 0.35 \times 10^7$ rad/m$^{2}$, compared to the value of $\sim 1.5 \times 10^5$ rad/m$^{2}$ for M87*, obtained from the ALMA EHT data (cite: Goddi2021complete; TFM)." (Simulations and model parameters); "we introduce, at each integration time, an uncorrelated Gaussian noise contribution to the real and imaginary parts of the visibilities, with zero average and a standard deviation of 0.5 mJy" (Simulations and model parameters)
- Simulation/model as data: 1D synthetic double Dirac-delta source observed with 4 stations at positions {0, 1, 4, 6} wavelengths for analytical and numerical exploration of closure trace amplitudes and phases  
  > "Limiting the problem to a 1-spatial dimension, the polarized structure of the double source, given by the Stokes parameters distribution $(I,Q,U,V)$, can be expressed as a sum of Dirac deltas" (The case of the double source); "Hence, for a configuration of antennas at positions $\{A;B;C;D\} \rightarrow \{0; 1; 4; 6\}$, in units of wavelength $\lambda$, we fix the Stokes parameters of component $1$, $(I_1;Q_1;U_1; V_1) = (1;0.3;0.15;0)$" (The case of the double source)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated ALMA data from the April 2017 EHT campaign used directly  
  > "We use the ALMA data obtained from the observations of the M87 AGN conducted on April 2017, and properly calibrated by the ALMA observatory." (Observations and simulated data)
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

- Definition and formalism of complex closure traces  
  > "Recently, a new set of complex closure quantities, dubbed closure traces, has been reported (cite: Broderick&Pesce2020)." (Introduction) [from Broderick & Pesce 2020 (cite: Broderick&Pesce2020)]
- Calibrated ALMA observations and full-polarization images of M87 from the April 2017 EHT campaign  
  > "In this paper, we focus on the M87* track observed on 2017 April 6, between 00:52 and 08:02 UT (cite: Goddi2021complete)." (Observations and simulated data); "Figure 1 shows the polarization structure of the AGN and the jet of M87, obtained from the ALMA data (cite: Goddi2021complete)." (Observations and simulated data) [from Goddi et al. 2021 (cite: Goddi2021complete)]
- Analytical expression of the closure trace for a double source  
  > "we obtain the analytical expression of the closure trace for the interferometric observation of a double source presented in (cite: TFM)." (Analytical Study of the Closure Traces, The case of the double source) [from Albentosa-Ruiz 2021 (cite: TFM)]

### Not stated but needed to reproduce (our reading)

- List of the exact 13 ALMA antenna names selected for the closure-trace subset analysis
- MCMC setup details for emcee (number of walkers, number of steps, burn-in length, and parameter priors)
- Grid resolution and parameter range bounds used in the 2D grid-search exploration
- Visibility time-averaging and frequency channel-averaging intervals used before computing closure traces

## Analysis recipe

1. **Simulate full-polarization visibilities for an M87-like three-component model**: Discrete Fourier transform of Stokes parameters (I, Q, U, V) for three point-source (delta) components (core, knot A, knot B) on the exact ALMA baseline coordinates across 4 spectral windows, adding 0.5 mJy uncorrelated Gaussian noise per integration time  
  > "For the simulation of closure traces related to a simplified model of M87 at ALMA scales, we parameterize the polarization intensity as a set of compact (delta) components" (Simulations and model parameters); "The simulated data are obtained by computing the discrete Fourier transform of the Stokes parameters ($(\tilde{I},\tilde{Q},\tilde{U},\tilde{V})$), for each $(u,v)$ coordinate and observed frequency $\nu$" (Simulations and model parameters); "we introduce, at each integration time, an uncorrelated Gaussian noise contribution to the real and imaginary parts of the visibilities, with zero average and a standard deviation of 0.5 mJy" (Simulations and model parameters)
   - software: Python
   - parameter: Core position (l, m) = (0, 0), I = 1.2 Jy; Knot A position (l, m) = (-11.28, 4.35), I = 0.1 Jy; Knot B position (l, m) = (-13.92, 4.95), I = 0.05 Jy  
  > "The component positions and Stokes values are given in Table" (Simulations and model parameters)
   - parameter: Simulated core RM ~ 0.35 x 10^7 rad/m^2; Gaussian visibility noise std = 0.5 mJy  
  > "thus increasing the RM of our simulated source to $\sim 0.35 \times 10^7$ rad/m$^{2}$" (Simulations and model parameters); "with zero average and a standard deviation of 0.5 mJy (similar to the average noise levels per integration time seen in the real data)." (Simulations and model parameters)
   - assumption: Source polarization structure represented by three compact (delta) components with Stokes V = 0  
  > "Regarding the rest of Stokes parameters (i.e., $Q$, $U$ and $V$), the model consists of three point sources, located at the positions marked in Fig. 2 (which correspond to the jet core and the two knots, $A$ and $B$)." (Simulations and model parameters)
   - fitting: _not stated_
   - validation: Assess structure factor contribution to spectral variation by comparing Stokes I model visibilities between spw 0 (213.1 GHz) and spw 3 (229.1 GHz)  
  > "we compare the *model* visibilities, computed from the Stokes $I$ deconvolved model obtained from the real ALMA data," (Prior discussion on the behaviour of the closure traces)
2. **Compute complex closure traces on a 13-antenna subset**: Select a subset of 13 ALMA antennas preserving Fourier space coverage and compute complex closure traces T_ABCD from visibility matrices on all 4-antenna quadrangles using a custom Python module  
  > "First, we develop a Python module to compute the closure traces of both simulated and model data." (Methodology); "Therefore, in this work we have decided to use a selection of 13 antennas, distributed in such a way that there is not a significant loss of information in the Fourier space (see Fig. 4)." (Methodology)
   - software: Python
   - parameter: 13 antennas selected out of 33 ALMA antennas  
  > "Therefore, in this work we have decided to use a selection of 13 antennas, distributed in such a way that there is not a significant loss of information in the Fourier space (see Fig. 4)." (Methodology)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit core-only polarization per spectral window via 2D grid search and linear RM fit**: Perform a 2D grid search minimizing the squared differences of closure traces for each spectral window independently (fixing RM parameter p_2 = 0 and jet knots A and B to image values), followed by a linear fit of core EVPA versus wavelength squared to recover RM  
  > "Since this core-only model only has two fitting parameters, we have opted to perform a grid search method (i.e. the 2-dimensional exploration of $\chi^2$) focusing on two parameters, the EVPA and the fractional polarization of the core." (Modelling the core-only polarization.); "To retrieve the RM, we need to perform a linear fitting of the polarization angle $\phi = \phi_0 + RM \lambda^2$ as a function of the observation wavelength $\lambda$ (i.e. for each spw)." (Modelling the core-only polarization.)
   - software: Python
   - parameter: Free parameters per spw: core EVPA (p_0) and core polarized flux density (p_1 = m * I_core); fixed parameters: p_2 = 0, knot A and knot B Stokes parameters  
  > "where all the Stokes parameters of the jet components are fixed to the measured values in the ALMA image" (Modelling the core-only polarization); "with the parameter $p_2$ fixed to 0 (i.e. there is no RM) as we analyse each spectral window separately." (Modelling the core-only polarization)
   - assumption: Equal weights for all visibilities; chi^2 temperature T estimated from the standard deviation of closure trace residuals at the minimum  
  > "where $T$ is the standard deviation of the closure trace residuals (evaluated for each dataset and spectral window) at the $\chi^2$ minimum, and assuming the same weights for all visibilities." (Modelling the core-only polarization.)
   - fitting: 2D grid search minimizing chi^2 = sum |T_ABCD^model - T_ABCD^data|^2 with probability density P proportional to exp(-chi^2 / 2T), then linear regression of phi(lambda^2)  
  > "The error function used in the least-squares minimization is simply given by the squared differences between the data closure traces and those from the parameterized model" (Methodology); "The probability density is then recovered as $\mathcal{P}_{\chi^2}(m,\phi) \propto \exp{\left( -\frac{\chi^2}{2T} \right)}$, where $T$ is the standard deviation of the closure trace residuals" (Modelling the core-only polarization.)
   - validation: Compare fitted EVPA, polarized flux, and core RM against ground-truth simulated values  
  > "From these results, we retrieve the differential FR along the core-jet structure of the simulation by fitting the polarization angle as a function of the observation wavelength $\phi(\lambda)$." (Grid Search)
4. **Simultaneously fit multi-component polarization and RM across all spectral windows using MCMC**: Combine all 4 spectral windows and fit the polarization (EVPA, polarized flux, and RM) of the core and one jet knot simultaneously while fixing the remaining knot (with V = 0), using circular statistics reparameterization and affine-invariant MCMC sampling on both simulated and real ALMA data  
  > "We use the Python tool `emcee` (cite: ForemanMackeyMCMC2013) for a affine-invariant MCMC approach to model-fitting, estimating the differential FR among the source components." (Model-fitting two M87 components: the MCMC approach); "We can break this ambiguity using circular statistics (cite: Fisher1987Spherical; Jupp2009DirectionalStat), a simple, but effective, change of parameters of the fitting model" (Model-fitting two M87 components: the MCMC approach); "This motivates the last part of our analysis on the use of closure traces on the real ALMA observations of M87 to retrieve the differential FR." (Real ALMA Observations)
   - software: Python, emcee
   - parameter: Reference wavelength lambda_0 = 0; 6 free parameters (q_0, q_1, q_2, q_3, and two component RMs)  
  > "In our model-fitting, we set $\lambda_0 = 0$, and therefore the $p_0$ value to which the MCMC method converges corresponds to the intrinsic polarization angle of the core, $\phi_{0}$, i.e, the EVPA at infinite frequency." (Model-fitting two M87 components: the MCMC approach); "Finally, $p_2$ and $p_5$ are preserved in our parameterization as the RM of the core and the knot $A$." (Model-fitting two M87 components: the MCMC approach)
   - assumption: One component is fixed with Stokes V = 0 to break the latitudinal degeneracy in the Poincare sphere and serve as differential polarization reference  
  > "However, the closure traces are only sensitive to differential polarization (or polarization contrast) across the source structure, which means that we must leave one of the components fixed (and force its Stokes $V$ to zero, in order to break the latitudinal degeneracy in the Poincaré Sphere)" (Model-fitting two M87 components: the MCMC approach)
   - fitting: Affine-invariant MCMC sampler (emcee) minimizing closure-trace least-squares chi^2 across all spectral windows simultaneously  
  > "We use the Python tool `emcee` (cite: ForemanMackeyMCMC2013) for a affine-invariant MCMC approach to model-fitting, estimating the differential FR among the source components." (Model-fitting two M87 components: the MCMC approach)
   - validation: Compare MCMC posterior RM against simulated ground-truth RM (~0.35 x 10^7 rad/m^2) and against the real ALMA image-analysis RM (~1.5 x 10^5 rad/m^2)  
  > "We obtain a RM posterior distribution spread around $RM \sim (0.2-0.4) \times 10^7$ rad/m$^{-2}$, which is close to, albeit a bit lower than, the expected value of $(0.35 \pm 0.04) \times 10^7$ rad/m$^{2}$" (Markov chains); "We now compare our results with the results obtained from the image analysis (cite: Goddi2021complete; TFM). We get a RM posterior distribution peaked around $RM \sim (0.8-1.6) \times 10^5$ rad/m$^{-2}$, being consistent with the values obtained from the image analysis." (Real ALMA Observations)

## Software

- **Python** : Developing a custom module to compute closure traces and run model-fitting  
  > "First, we develop a Python module to compute the closure traces of both simulated and model data." (Methodology)
- **emcee** : Affine-invariant Markov chain Monte Carlo (MCMC) model-fitting of closure traces  
  > "We use the Python tool `emcee` (cite: ForemanMackeyMCMC2013) for a affine-invariant MCMC approach to model-fitting, estimating the differential FR among the source components." (Model-fitting two M87 components: the MCMC approach)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Average deviation of Stokes I model visibilities between spw 0 and spw 3 | 1.2 | 0.7 | % | 1 | We retrieve an average deviation of the model visibilities at spws $0$ and $3$ of $(1.2\pm0.7)\%$, much lower than the average deviation computed directly from the visibilities, of $(10\pm20)\%$. |
| Average deviation of observed visibilities between spw 0 and spw 3 | 10 | 20 | % | 1 | We retrieve an average deviation of the model visibilities at spws $0$ and $3$ of $(1.2\pm0.7)\%$, much lower than the average deviation computed directly from the visibilities, of $(10\pm20)\%$. |
| Simulated core polarization angle phi (grid-search, spw 0) | 30.11 | 0.05 | deg | 3 | 0 / 30.11 $\pm$ 0.05 / 30 / 0.200 $\pm$ 0.001 / 0.200 |
| Simulated core polarized flux m*I (grid-search, spw 0) | 0.200 | 0.001 | Jy | 3 | 0 / 30.11 $\pm$ 0.05 / 30 / 0.200 $\pm$ 0.001 / 0.200 |
| Simulated core polarization angle phi (grid-search, spw 1) | 14.37 | 0.05 | deg | 3 | 1 / 14.37 $\pm$ 0.05 / 15 / 0.347 $\pm$ 0.001 / 0.346 |
| Simulated core polarized flux m*I (grid-search, spw 1) | 0.347 | 0.001 | Jy | 3 | 1 / 14.37 $\pm$ 0.05 / 15 / 0.347 $\pm$ 0.001 / 0.346 |
| Simulated core polarization angle phi (grid-search, spw 2) | -13.66 | 0.11 | deg | 3 | 2 / -13.66 $\pm$ 0.11 / -15 / 0.348 $\pm$ 0.002 / 0.346 |
| Simulated core polarized flux m*I (grid-search, spw 2) | 0.348 | 0.002 | Jy | 3 | 2 / -13.66 $\pm$ 0.11 / -15 / 0.348 $\pm$ 0.002 / 0.346 |
| Simulated core polarization angle phi (grid-search, spw 3) | -25.2 | 0.3 | deg | 3 | 3 / -25.2 $\pm$ 0.3 / -30 / 0.203 $\pm$ 0.005 / 0.200 |
| Simulated core polarized flux m*I (grid-search, spw 3) | 0.203 | 0.005 | Jy | 3 | 3 / -25.2 $\pm$ 0.3 / -30 / 0.203 $\pm$ 0.005 / 0.200 |
| Simulated M87 core Rotation Measure (grid-search + linear fit) | 0.32e7 | 0.04e7 | rad/m^2 | 3 | By doing so, we obtain a value of the RM of the core component, $RM = (0.32 \pm 0.04) \times 10^7$ rad/m$^{2}$, as shown in Fig. 6, which is compatible with the expected value of $(0.35 \pm 0.04) \times 10^7$ rad/m$^{2}$. |
| Simulated M87 core Rotation Measure (MCMC) | (0.2-0.4)e7 | not stated | rad/m^2 | 4 | We obtain a RM posterior distribution spread around $RM \sim (0.2-0.4) \times 10^7$ rad/m$^{-2}$, which is close to, albeit a bit lower than, the expected value of $(0.35 \pm 0.04) \times 10^7$ rad/m$^{2}$ (see Fig. 6). |
| Real ALMA M87 core Rotation Measure (MCMC) | (0.8-1.6)e5 | not stated | rad/m^2 | 4 | We get a RM posterior distribution peaked around $RM \sim (0.8-1.6) \times 10^5$ rad/m$^{-2}$, being consistent with the values obtained from the image analysis. |

## Qualitative findings

- Frequency-dependent variations in observed ALMA closure traces of M87 cannot be explained solely by the spatial structure factor (uv-scaling with frequency) and indicate differential Faraday Rotation across the source.  
  > "We retrieve an average deviation of the model visibilities at spws $0$ and $3$ of $(1.2\pm0.7)\%$, much lower than the average deviation computed directly from the visibilities, of $(10\pm20)\%$. Therefore, the frequency dependence seen in the observed closure traces of M87 may be related to FR." (Prior discussion on the behaviour of the closure traces)
- Fitting closure traces independently per spectral window exhibits multiple local minima (degeneracies in EVPA and fractional polarization), whereas combining all spectral windows in a joint MCMC fit breaks these degeneracies.  
  > "even though the $\chi^2$ parametric space presents several minima when model-fitting for each spw individually, as reported in Fig. 7, due to the degeneracies of the closure traces with the EVPA and the fractional polarization, combining all the spw seems to help breaking the degeneracies" (Markov chains)
- Analytical exploration of a double point-source shows closure trace amplitude peaks when component EVPAs are aligned and maximum phase sensitivity to polarized intensity variations when EVPAs point in the same direction.  
  > "First, a closure trace amplitude peak (maximum or minimum) is obtained when the EVPAs of the two components are equal. Second, the closure trace phases are more sensitive to polarization intensity variations when the EVPAs of both components point in the same direction." (The case of the double source)

## Claim tuples

- H: Frequency variations in the observed closure traces of M87 in ALMA Band 6 are driven by differential Faraday Rotation rather than baseline re-projection (structure factor) across frequency. | E: Compare the fractional variation between spw 0 (213.1 GHz) and spw 3 (229.1 GHz) for Stokes I model visibilities (structure factor only) versus the directly observed visibilities. | R: Model visibilities deviate by (1.2 +/- 0.7)% between spw 0 and spw 3, much smaller than the (10 +/- 20)% deviation seen in the observed visibilities. | F: The observed frequency dependence of M87 closure traces is dominated by differential Faraday Rotation rather than source structure re-projection. | **supported**
- H: Parametric model-fitting to complex closure traces alone can recover source polarization parameters (EVPA, fractional polarization) and differential Faraday Rotation independent of instrumental polarization calibration. | E: Fit a 3-component point-source polarization model to simulated ALMA closure traces using both a per-spw 2D grid search with linear EVPA(lambda^2) fitting and a multi-spw MCMC sampler with circular statistics parameterization. | R: Grid search recovers RM = (0.32 +/- 0.04) x 10^7 rad/m^2 and MCMC recovers RM ~ (0.2-0.4) x 10^7 rad/m^2, both compatible with the simulated input RM of (0.35 +/- 0.04) x 10^7 rad/m^2, while multi-spw MCMC breaks single-spw degeneracies. | F: Closure-trace model fitting reliably extracts differential polarization and Faraday Rotation without requiring instrumental polarization calibration. | **supported**
- H: Applying the MCMC closure-trace fitting method to real ALMA Band 6 observations of M87 can recover the differential Faraday Rotation of the M87 core directly from closure observables. | E: Run the 2-component circular-statistics MCMC closure-trace fit on the 2017 April 6 ALMA Band 6 track of M87 using a subset of 13 antennas and compare with full-array calibrated image RM synthesis. | R: The MCMC posterior peaks around RM ~ (0.8-1.6) x 10^5 rad/m^2, consistent with the ~1.5 x 10^5 rad/m^2 obtained from calibrated image analysis, though with a wide posterior distribution. | F: Differential Faraday Rotation in the M87 core-jet structure can be recovered directly from real ALMA closure traces, though precision is limited by the small (~2 deg) EVPA rotation across Band 6 and the use of 13 of 33 antennas. | **supported**

## Reasoning

- Why this data: ALMA is the most sensitive mm/submm array and recorded full-array visibilities among its 33 phased antennas during the April 2017 EHT campaign on M87, where differential Faraday Rotation between the core and jet knots had already been established by calibrated image analysis.  
  > "This paper concerns, as a test dataset, the ALMA observations conducted on the April 2017 EHT campaign (cite: EHTIcomplete)." (Observations and simulated data); "On the other hand, the RM synthesis performed across the whole source brightness distribution shows a clear differential FR between the core and the two jet knots, $A$ and $B$, being the RM at the core notably larger than those at the knots." (Observations and simulated data)
- Why this method: Closure traces are invariant to antenna-based and direction-independent instrumental polarization (D-terms) and gain errors; MCMC and grid search are used because the chi^2 landscape is highly non-linear with multiple local minima, and circular statistics reparameterization removes the n*pi EVPA ambiguity.  
  > "We notice, though, that the behaviour of this $\chi^2$ is highly non-linear in the parameter space of the chosen model, with many local minima." (Methodology); "We can break this ambiguity using circular statistics (cite: Fisher1987Spherical; Jupp2009DirectionalStat), a simple, but effective, change of parameters of the fitting model" (Model-fitting two M87 components: the MCMC approach)
- Alternative: Gradient-based minimization (e.g., Levenberg-Marquardt) was rejected because the closure-trace chi^2 parameter space is highly non-linear with many local minima.  
  > "Therefore, methods based on the gradient (cite: LevenbergMarquardt1978) may not converge to the global minimum, depending on the initial parameter values" (Methodology)
- Alternative: Using all 33 ALMA antennas was rejected in favor of a 13-antenna subset because the number of 4-antenna combinations scales as n!/(4!(n-4)!), making the full array computationally prohibitive.  
  > "However, for a large number of antennas, which is the case of the ALMA observations analysed here, the computational cost may be prohibitive (for a number of $n$ antennas, there are $n!/\left[4!(n-4)!\right]$ 4-antenna baselines). Therefore, in this work we have decided to use a selection of 13 antennas" (Methodology)
- Alternative: Multi-parameter grid search for simultaneous multi-component RM fitting was rejected in favor of MCMC due to prohibitive computational cost in higher dimensions.  
  > "The MCMC method allows us to test if the closure traces can retrieve the polarization of different components of an observed source, simultaneously, since the grid-search method becomes computationally unfeasible for the extended set of parameters." (Model-fitting two M87 components: the MCMC approach)
- How they decided it was enough: _not stated_
- Limitation (authors): Only a subset of 13 out of 33 ALMA antennas could be used due to computational cost, reducing the SNR and widening the RM posterior distribution compared to full-array imaging.  
  > "In addition to the small EVPA rotation at the core, we are using only a subset of 13 antennas in our closure-based modelling (due to the computational limitations), which has a negative impact on the achievable signal-to-noise ratio (SNR)" (Real ALMA Observations)
- Limitation (authors): The small fractional bandwidth of ALMA Band 6 produces only ~2 degrees of EVPA rotation at the M87 core, resulting in a very wide RM posterior (poor RM precision).  
  > "However, the width of the RM posterior distribution is very wide (i.e., the precision of the RM is poor), likely due to the small EVPA rotation (of the order of 2 deg.) of the core across the ALMA band." (Real ALMA Observations)
- Limitation (authors): Closure traces are only sensitive to differential polarization across the source, requiring at least one component's polarization (and Stokes V = 0) to be held fixed to break global Poincare-sphere rotation degeneracies.  
  > "However, the closure traces are only sensitive to differential polarization (or polarization contrast) across the source structure, which means that we must leave one of the components fixed (and force its Stokes $V$ to zero, in order to break the latitudinal degeneracy in the Poincaré Sphere)" (Model-fitting two M87 components: the MCMC approach)
- Caveat (inferred, ours): The method requires prior knowledge of the total intensity structure (component positions and Stokes I fluxes) and the exact polarization state of at least one reference component, which were taken from the already-calibrated full-polarization ALMA image, so the demonstration is not strictly independent of prior calibration/imaging.
- Caveat (inferred, ours): An inconsistency exists between Section 3.2 (which states knot B is fixed and core + knot A are varied, with a typo in Eq. 7 using q_2 twice in Q_knotA and q_3 twice in U_knotA) and Section 4.1.2 / Figure 8 (which state core and knot B are varied), complicating exact reproduction of the MCMC parameterization.
- Caveat (inferred, ours): Unweighted least-squares minimization (assuming identical weights for all visibilities/closure traces) does not account for non-Gaussian, correlated noise structure in ratios of visibility matrices.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Calibrated ALMA data from project 2016.1.01154.V were used  
  > "We use the ALMA data obtained from the observations of the M87 AGN conducted on April 2017, and properly calibrated by the ALMA observatory." (Observations and simulated data); "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.01154.V" (Acknowledgements)
- Code: _not stated_
- Missing: Custom Python module for closure trace computation and model fitting is not publicly released
- Missing: Exact list of the 13 ALMA antennas selected (only 4 station names DA50, DA52, DV05, DV12 are mentioned in the text, and positions are plotted in Fig. 4)
- Missing: MCMC hyperparameters (number of walkers, chain length, burn-in, prior distributions)
- Missing: Exact time and spectral averaging applied to the visibility data prior to forming closure traces
- Missing: Resolution of the text/equation discrepancy regarding whether knot A or knot B is varied in the MCMC fit and the typo in Eq. 7
- Data volume (inferred): ~10-50 GB for the single-epoch calibrated ALMA Band 6 full-polarization visibility dataset (reduced significantly if channel-averaged per spectral window and restricted to 13 antennas)
- Score (inferred): 60/5, The mathematical formalism, simulated source table (Table 1/unnumbered table), and ALMA project code/date/time are clearly specified, allowing the simulated experiments to be closely approximated; however, the custom Python code is not released, the exact 13-antenna subset is only shown graphically, MCMC settings/priors are omitted, and there are minor text/equation inconsistencies in the two-component parameterization.
- Rediscovery candidate: yes, The archival ALMA data (2016.1.01154.V) and synthetic model parameters are fully specified in the paper, the mathematical definition of closure traces and the chi^2 objective function are explicit, and the main results are quantitative (recovered EVPA, polarized flux, and RM values).

## Links

- Method: Broderick & Pesce 2020 (cite: Broderick&Pesce2020) (Introduced the complex closure trace observable and proved its invariance to arbitrary Jones matrices)
- Method: Foreman-Mackey et al. 2013 (cite: ForemanMackeyMCMC2013) (Provided the emcee affine-invariant MCMC sampler used for multi-component fitting)
- Method: Fisher et al. 1987 (cite: Fisher1987Spherical); Jupp & Mardia 2009 (cite: Jupp2009DirectionalStat) (Circular statistics formalism used to reparameterize Stokes Q and U and eliminate EVPA n*pi ambiguities)
- Companion: Goddi et al. 2019 (cite: Goddi2019) (Describes the calibration and data processing of the ALMA phased-array observations during the 2017 EHT campaign)
- Companion: Goddi et al. 2021 (cite: Goddi2021complete) (Presents the calibrated full-polarization ALMA images and RM analysis of M87 from the April 2017 campaign used as ground truth and model input)
- Companion: Albentosa-Ruiz 2020 (cite: TFG); Albentosa-Ruiz 2021 (cite: TFM) (Theses by the first author containing the M87 RM map and analytical study of double-source closure traces built upon in this paper)
- Related: Event Horizon Telescope (EHT)

## Checks

```json
{
 "quotes": 87,
 "quotes_ok": 87,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 10,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 45,
  "rate": 0.549
 },
 "evidence_ok": true
}
```
