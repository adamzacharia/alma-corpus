# Ring Asymmetry and Spin in M87*

`2026ApJ..1000..231B` | The Astrophysical Journal 2026 | first author: Bernshteyn, Vadim | arXiv: 2601.00394 | DOI: 10.3847/1538-4357/ae34af

Card schema 1.0 | model gpt-6.1-sol | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: agn_and_quasars
- Question: How ring brightness asymmetry constrains dimensionless black hole spin in M87*.  
  > "In this paper, we study how ring brightness asymmetry constrains dimensionless black hole spin:" (Introduction)
- Target **M87***: coordinates _not stated_; z/distance 16.8 Mpc  
  > "The ring diameter is consistent with a black hole of mass $M = 6.5 \times 10^9 M_\odot$ located at a distance $D = 16.8$ Mpc from Earth (cite: EHTC_2019_6)" (Introduction); distance from (cite: EHTC_2019_6)  
  > "The ring diameter is consistent with a black hole of mass $M = 6.5 \times 10^9 M_\odot$ located at a distance $D = 16.8$ Mpc from Earth (cite: EHTC_2019_6)" (Introduction)

## Data provenance

- ALMA projects: 2017.1.00841.V, 2019.1.01797.V
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: Event Horizon Telescope (EHT); VLBI  
  > "Very-long-baseline interferometry (VLBI) arrays such as the EHT sample the $(u,v)$, or Fourier, domain." (EHT observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2017, 2018, and 2021 observing campaigns  
  > "The observational data were obtained by the EHT Collaboration during the 2017, 2018, and 2021 observing campaigns" (Introduction)
- pi or archival as stated: _not stated_
- Other facility **Event Horizon Telescope (EHT)**: 2017, 2018, and 2021 observational data  
  > "The observational data were obtained by the EHT Collaboration during the 2017, 2018, and 2021 observing campaigns" (Introduction)
- Other facility **Argonne Leadership Computing Facility**: Storage space on the Eagle system  
  > "We are particularly grateful to the Argonne Leadership Computing Facility for providing storage space on the Eagle system that was critical for enabling this work." (Acknowledgments)
- External data: EHT observations from the 2017, 2018, and 2021 campaigns  
  > "The observational data were obtained by the EHT Collaboration during the 2017, 2018, and 2021 observing campaigns" (Introduction); "hereafter EHTC M87 I–VI for (cite: EHTC_2019_1; EHTC_2019_2; EHTC_2019_3; EHTC_2019_4; EHTC_2019_5; EHTC_2019_6); EHTC M87 2018 I–II for (cite: EHTC_2024_1; EHTC_2025_1); and EHTC M87 2021 for (cite: EHTC_2025_1_M87_21)" (Introduction) [from EHTC M87 I–VI (cite: EHTC_2019_1; EHTC_2019_2; EHTC_2019_3; EHTC_2019_4; EHTC_2019_5; EHTC_2019_6); EHTC M87 2018 I–II (cite: EHTC_2024_1; EHTC_2025_1); EHTC M87 2021 (cite: EHTC_2025_1_M87_21)]
- External data: M87* mass 6.5 × 10^9 M_sun and distance 16.8 Mpc  
  > "The ring diameter is consistent with a black hole of mass $M = 6.5 \times 10^9 M_\odot$ located at a distance $D = 16.8$ Mpc from Earth (cite: EHTC_2019_6)" (Introduction) [from (cite: EHTC_2019_6)]
- External data: Approaching jet inclination 17°  
  > "We assume that the black hole spin vector, the accretion flow orbital angular momentum vector, and the large scale jet are coaxial, and that the approaching jet inclination is $17^\circ$ (cite: walker_jet_2018)." (Models) [from (cite: walker_jet_2018)]
- External data: v5 Illinois GRMHD library  
  > "For this study, we use the “v5” version of the Illinois GRMHD library (Bowden et al., in preparation)." (Models) [from Bowden et al., in preparation]
- External data: v3 library for comparison  
  > "Results from the v3 library (cite: Dhruv_grmhd_survey_2024), which were produced with an outdated adiabatic index among other differences, used the `iharm `code (cite: prather_iharm_2021)" (Models) [from (cite: Dhruv_grmhd_survey_2024)]
- External data: Earlier 2017 April 11 asymmetry A ∼ 0.22  
  > "The analysis of 2017 data reported an asymmetry $A\sim 0.22$ on April 11, which is smaller than reported here ($a_{1}=0.41$) due to a difference in definition." (Comparison to Earlier Work) [from not stated]
- External data: Earlier 2018 April 21 asymmetry A ≈ 0.31  
  > "The EHT analysis of 2018 April 21 data used Comrade and VIDA to measure an asymmetry and found $A\approx 0.31$" (Comparison to Earlier Work) [from not stated]
- External data: Earlier 2021 April 18 asymmetry A ≈ 0.22 to 0.25  
  > "The EHT analysis of 2021 April 18 used Comrade to measure an asymmetry of $A\approx 0.22$ to $0.25$, again following the convention where values of $A$ are a factor of 2 smaller than $a_{1}$." (Comparison to Earlier Work) [from not stated]
- External data: 2017 M87* FA = 0.20–0.24, compared with the present a1 measurement  
  > "For 2017 M87\* data they find $FA = 0.20-0.24$, implying $a_{1}\approx 0.38 - 0.46$, consistent with the $a_{1}=0.41$ value we find by fitting all visibility amplitudes and closure phases using Comrade." (Comparison to Earlier Work) [from (cite: faggert_asym_2024)]
- Simulation/model as data: Illinois v5: 13 MAD GRMHD fluid simulations spanning spin −0.97 to 0.97  
  > "For v5, we densely sample the dimensionless spin $a_{*}$ in 13 steps, ranging from $-0.97$ to $0.97$ (Bowden et al., in preparation)." (Models); "Our analysis therefore uses 13 MAD GRMHD fluid simulations." (Models)
- Simulation/model as data: 104 PATOKA models; 6000 images each; 5 t_g cadence from 20,000 to 50,000 t_g  
  > "Each of 104 `PATOKA `models contains 6000 images, produced at $5 \, t_g$ cadence (for gravitational time $t_g\equiv GMc^{-3}$) in the interval from time $20,000 \, t_g$ to $50,000 \, t_g$ after the start of the simulation." (Models)
- Simulation/model as data: v3 and v5 MAD and SANE models used for comparison  
  > "A comparison of MAD and SANE models in our main v5 library and in the v3 library, which is run with different physical assumptions and a different GRMHD code, are discussed in Appendix" (Models)

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

- task: CLEAN imaging with Difmap  
  > "We thank Martin Shepherd for the addition of extra features in the Difmap software that were used for the CLEAN imaging results presented in this paper." (Acknowledgments)
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

- PATOKA pipeline for GRMHD simulations and ray-traced synthetic images  
  > "The library was produced using the `PATOKA `pipeline (cite: wong_patoka_2022), which models the accretion flow using ideal general relativistic magnetohydrodynamics (GRMHD) simulations and then ray-traces GRMHD snapshots to produce synthetic images." (Models) [from (cite: wong_patoka_2022)]
- v5 Illinois GRMHD library and dense spin sampling  
  > "For this study, we use the “v5” version of the Illinois GRMHD library (Bowden et al., in preparation)." (Models); "For v5, we densely sample the dimensionless spin $a_{*}$ in 13 steps, ranging from $-0.97$ to $0.97$ (Bowden et al., in preparation)." (Models) [from Bowden et al., in preparation]
- Approaching jet inclination 17°, with coaxial spin, accretion flow, and jet  
  > "We assume that the black hole spin vector, the accretion flow orbital angular momentum vector, and the large scale jet are coaxial, and that the approaching jet inclination is $17^\circ$ (cite: walker_jet_2018)." (Models) [from (cite: walker_jet_2018)]
- R_high–R_low prescription for Ti/Te as a function of plasma beta  
  > "We use a model with parameters $R_{\text{high}}$ and $R_{\text{low}}$ to assign a distribution function to the electrons." (Models); "Then, following (cite: moscibrodzca16)" (Models) [from (cite: moscibrodzca16)]
- Detailed validation of the parameter optimization method  
  > "Detailed validation of the parameter optimization method is described in (cite: tiede_vida_2022)." (EHT observations) [from (cite: tiede_vida_2022)]
- Synthetic visibility amplitudes and closure phases with realistic observational noise  
  > "We generate $(u,v)$ data by Fourier transforming our synthetic images, then sampling the resulting visibility amplitudes and closure phases using EHT $(u,v)$ coverage, with realistic observational noise (cite: Chael_2018)." (Simulated images) [from (cite: Chael_2018)]
- Magnetized torus initial conditions of limited radial extent  
  > "The models are initialized with a magnetized torus of limited radial extent (cite: Fishbone_moncrief_torus; wong_patoka_2022)." (Model Uncertainty) [from (cite: Fishbone_moncrief_torus; wong_patoka_2022)]

### Not stated but needed to reproduce (our reading)

- Exact EHT data products, observing scans, frequency selections, and flags used for each annual fit.
- ALMA station calibration and phasing products, flux scale, and their propagation into the EHT observables.
- Comrade version, optimizer or sampler, initialization, priors, complete parameter bounds, likelihood, and treatment of correlated closure phases.
- Procedure used to obtain the quoted observational a1 uncertainties.
- Actual jet position angle used to rotate synthetic images.
- Noise model parameters and implementation used to generate synthetic EHT data.
- v5 snapshot and image access, simulation grid and boundary settings, ray-tracing resolution, field of view, and emission normalization.
- Weights used when marginalizing over R_high and R_low.
- Truncated-Gaussian fitting implementation and KS-test implementation.
- Monte Carlo repetition counts and random seeds for the forecasts.
- Identification and parameters of the fast-light versus slow-light test model.

## Analysis recipe

1. **Measure observed ring asymmetry**: Fit EHT visibility amplitudes and closure phases with a Gaussian background plus an m=4 m-ring; use normalized m=1 amplitude a1.  
  > "Our parameterized Comrade model has two components: a ring with intensity $I_{ring}$ and a Gaussian background component with intensity $I_{bg}$." (EHT observations); "The model parameters are adjusted by the Comrade optimizers to fit EHT visibility amplitude and closure phase data." (EHT observations); "We use $a_{1}$, the normalized amplitude of the $m = 1$ Fourier component, as our measure of ring brightness asymmetry." (EHT observations)
   - software: Comrade
   - parameter: m=4; a_m ∈ [0,1); zero ring ellipticity; single nuisance Gaussian  
  > "For the bulk of this analysis, we used an $m$-ring model that was truncated at $m=4$, bound by asymmetry $a_m\in[0,1)$, and fit in the $(u,v)$ domain assuming 2018 $(u,v)$ coverage." ($m$-ring Truncation, Asymmetry Bounds, and $(u,v)$ Coverage); "Our $m=4$ $m$-ring had zero ellipticity and was allowed a single nuisance Gaussian, which models diffuse off-ring emission." ($m$-ring Truncation, Asymmetry Bounds, and $(u,v)$ Coverage)
   - parameter: Ring: radius r0, thickness sigma, amplitudes and position angles for m=1 through 4  
  > "Our $m=4$ $m$-ring has 10 parameters: ring radius $r_0$, ring thickness $\sigma$, amplitudes $a_m$, and position angles $\textrm{PA}_m$ for $m=1$ through $4$." (EHT observations)
   - assumption: a1=0 denotes symmetry; a1=1 denotes amplitude as large as the ring mean  
  > "In our convention, notice that a ring with $a_{1}=0$ is symmetric, while a ring with $a_{1}=1$ has an amplitude as large as its mean." (EHT observations)
   - fitting: Comrade optimizers fit visibility amplitudes and closure phases.  
  > "The model parameters are adjusted by the Comrade optimizers to fit EHT visibility amplitude and closure phase data." (EHT observations)
   - validation: Mean squared standardized residual chi2, normalized by number of data points; 1.9, 0.9, and 2.6 for 2017, 2018, and 2021.  
  > "The quality of fit can be assessed using the mean squared standardized residual $\chi^2$, normalized by the number of data points." (EHT observations); "The normalized $\chi^2$ is $1.9$, $0.9$, and $2.6$ in 2017, 2018, and 2021 respectively (note these are not reduced $\chi^2$ values)." (EHT observations)
2. **Construct the synthetic image library**: Evolve ideal GRMHD with KHARMA and ray-trace snapshots with ipole using PATOKA; use Illinois v5.  
  > "The library was produced using the `PATOKA `pipeline (cite: wong_patoka_2022), which models the accretion flow using ideal general relativistic magnetohydrodynamics (GRMHD) simulations and then ray-traces GRMHD snapshots to produce synthetic images." (Models); "The GRMHD simulations are integrated with the KHARMA code (cite: Prather_kharma_2024), and the synthetic images are produced using `ipole `(cite: ipole18)." (Models); "For this study, we use the “v5” version of the Illinois GRMHD library (Bowden et al., in preparation)." (Models)
   - software: PATOKA, KHARMA, ipole
   - parameter: MAD; spins 0, ±0.25, ±0.5, ±0.75, ±0.85, ±0.9375, ±0.97  
  > "Our analysis therefore uses 13 MAD GRMHD fluid simulations." (Models); "$0$, $\pm 0.25$, $\pm 0.5$, $\pm 0.75$, $\pm 0.85$, $\pm 0.9375$, $\pm 0.97$" (Table 1)
   - parameter: R_high = 10, 40, 80, 160; R_low = 1, 10  
  > "We consider models with $R_{\text{high}} = 10, 40, 80, 160$ and $R_{\text{low}}= 1, 10$" (Models)
   - parameter: 104 models; 6000 images per model; 5 t_g cadence; t=20,000–50,000 t_g  
  > "Each of 104 `PATOKA `models contains 6000 images, produced at $5 \, t_g$ cadence (for gravitational time $t_g\equiv GMc^{-3}$) in the interval from time $20,000 \, t_g$ to $50,000 \, t_g$ after the start of the simulation." (Models)
   - assumption: Coaxial spin, flow angular momentum, and jet; approaching jet inclination 17°  
  > "We assume that the black hole spin vector, the accretion flow orbital angular momentum vector, and the large scale jet are coaxial, and that the approaching jet inclination is $17^\circ$ (cite: walker_jet_2018)." (Models)
   - assumption: i=17° for a*<0; i=163° for a*≥0  
  > "Adopting this constraint, we set $i = 17^\circ$ for $a_{*}< 0$ and $i = 163^\circ$ for $a_{*}\ge 0$." (Models)
   - assumption: Thermal electrons and ions; Ti from the simulation; Ti/Te depends only on local instantaneous plasma beta  
  > "The model assumes that (1) the electrons are thermal at temperature $T_e$; (2) the ions are thermal at temperature $T_i$; (3) $T_i$ can be deduced directly from the simulation;" (Models); "and (4) $T_i/T_e$ depends only on the local, instantaneous value of the plasma $\beta \equiv P_{gas}/P_{mag}$ for gas pressure $P_{gas}$ and magnetic pressure $P_{mag}$." (Models)
   - assumption: beta_crit=1  
  > "for $\tilde{\beta}=\beta/\beta_{\text{crit}}$ and $\beta_{\text{crit}}=1$." (Models)
   - assumption: v5 adiabatic index gamma=5/3  
  > "The most notable physical difference is that in v5, the plasma adiabatic index is $\gamma = \frac{5}{3}$, compared to $\gamma = \frac{4}{3}$ in v3." (v3 Illinois GRMHD Library)
   - assumption: Fast-light radiative transfer on a single time slice  
  > "The fast light approximation used here performs the radiative transfer calculation for a snapshot on a single time slice." (Model Uncertainty)
   - fitting: _not stated_
   - validation: Compare v3 and v5, MAD and SANE models; compare fast-light and slow-light asymmetry in a test model.  
  > "A comparison of MAD and SANE models in our main v5 library and in the v3 library, which is run with different physical assumptions and a different GRMHD code, are discussed in Appendix" (Models); "We have compared the asymmetry distribution in fast light and slow light versions of a test model and find that they are nearly identical." (Model Uncertainty)
3. **Measure asymmetry in synthetic EHT observations**: Rotate images to the jet axis; Fourier transform, sample EHT coverage with noise, and fit the same m-ring with Comrade.  
  > "We first rotate the ground truth images to match the large-scale jet axis expected from observations" (Simulated images); "We generate $(u,v)$ data by Fourier transforming our synthetic images, then sampling the resulting visibility amplitudes and closure phases using EHT $(u,v)$ coverage, with realistic observational noise (cite: Chael_2018)." (Simulated images); "Finally, we fit the $m$-ring model parameters to the resulting synthetic data using Comrade," (Simulated images)
   - software: Comrade, VIDA
   - parameter: Downsample to 125 t_g; 240 images per spin/R_high/R_low combination and 1920 per spin  
  > "so we downsample to a cadence of $125 \, t_g$" (Simulated images); "This leaves $240$ images per unique combination of spin, $R_{\text{high}}$, and $R_{\text{low}}$, and $1920$ unique images per unique spin." (Simulated images)
   - parameter: 2018 EHT (u,v) coverage and conditions  
  > "For simplicity, we assume 2018 EHT $(u,v)$ coverage and conditions." (Simulated images)
   - assumption: 125 t_g cadence provides independent synthetic observations  
  > "to obtain independent synthetic observations." (Simulated images); "The images are correlated on timescales $\sim 100 \, t_g$, so we downsample to a cadence of $125 \, t_g$" (Simulated images)
   - fitting: Fit the m-ring parameters to synthetic data using Comrade, as for the observations.  
  > "Finally, we fit the $m$-ring model parameters to the resulting synthetic data using Comrade," (Simulated images); "We apply the same analysis technique to our synthetic data as we did to the real data." (Simulated images)
   - validation: Compare (u,v)-domain and image-domain asymmetries; 68% differ by less than 0.13 and 90% by less than 0.22; check other annual coverage.  
  > "About $68\%$ of snapshots have $|a_{1, UV} - a_{1,I}|$ less than $0.13$, and $90\%$ have difference less than $0.22$." (Simulated images); "The results are consistent if we use 2017 or 2021 $(u,v)$ coverage and observational noise instead" (Simulated images); "We demonstrate consistency with asymmetry fits in the image domain using variational image domain analysis (cite: tiede_vida_2022)" (EHT observations)
4. **Build spin-dependent asymmetry distributions**: Marginalize MAD asymmetries over all parameters except spin and fit truncated Gaussian distributions.  
  > "Figure [5](#fig:spin_distr) shows the asymmetry distributions for MAD models, marginalizing over all parameters except spin." (Results); "Mode ($\mu$) and standard deviation ($\sigma$) for truncated Gaussian fits to asymmetry distributions for MAD models." (Table 2)
   - parameter: Filter a1>0.99 before fitting; truncated-Gaussian bounds a1 ∈ [0,1)  
  > "We filter out all images with $a_{1}> 0.99$ before fitting to improve accuracy." (Results); "The fits are bounded by $a_{1}\in [0, 1)$; we exclude $a_{1}= 1$ cases prior to fitting." (Table 2)
   - fitting: Truncated Gaussian fits summarized by mode mu and standard deviation sigma.  
  > "Mode ($\mu$) and standard deviation ($\sigma$) for truncated Gaussian fits to asymmetry distributions for MAD models." (Table 2)
   - validation: Compare with a clipped Gaussian fit; recovered mu changes little.  
  > "We tried fitting a clipped Gaussian and found this had little effect on the recovered $\mu$ for each model." ($m$-ring Truncation, Asymmetry Bounds, and $(u,v)$ Coverage)
5. **Test spins against observed asymmetries**: Use one-sample KS tests against truncated Gaussian distributions and two-sample KS tests against individual synthetic-image asymmetries.  
  > "To assess the significance of the inconsistency between the data and the models, we use the Kolmogorov–Smirnov (KS) test." (Results); "one for the truncated Gaussian fit to the GRMHD asymmetry distribution (the “one-sample” KS test), and one using measured asymmetries of individual images drawn from each model (the “two-sample” KS test)." (Results)
   - parameter: Marginalize over R_high and R_low at each spin; also inspect zero-spin models separately by these parameters.  
  > "In the discussion above, we marginalize over all radiative transfer parameters $R_{\text{high}}$ and $R_{\text{low}}$ at each spin." (Results); "Figure [7](#fig:p_value_spin_0) shows KS test probabilities for $a_{*}= 0$ models broken out for different $R_{\text{high}}$ and $R_{\text{low}}$." (Results)
   - assumption: MAD model library represents M87*; only three independent observations  
  > "a restriction of the model library to magnetically arrested disk (MAD) models, which are nevertheless preferred by EHT data; and (3) only three independent observations." (Conclusion); "the relevance of the model library itself, which is known to have missing physical ingredients and internal inconsistencies" (Conclusion)
   - fitting: _not stated_
   - validation: One-sample and two-sample KS results are very close.  
  > "Evidently the two are very close." (Results)
6. **Forecast constraints from additional epochs**: Repeatedly draw N mock observations, perform KS comparisons, and report median p; test a present-data distribution and distributions at fixed true spin.  
  > "We draw $N$ random samples (mock observations) from the truncated normal distribution, and perform a KS test comparing the mock observations to all spin zero models." (Future EHT Observations); "We fix the “true” spin of M87\*, draw samples from the distribution for that spin" (Future EHT Observations); "We again repeat this procedure many times and take the median $p$." (Future EHT Observations)
   - parameter: First forecast: truncated normal with mu ∼0.55 and standard deviation ≃0.2  
  > "For the first case, we assume the asymmetry is a (truncated) normal distribution with $\mu$ equal to the average of the three existing measurements, $\sim 0.55$, and the standard deviation $\simeq 0.2$" (Future EHT Observations)
   - assumption: Second forecast assumes the correct model is in the library.  
  > "For the second case, we assume the correct model is in our library and ask how well future observations can measure the spin." (Future EHT Observations)
   - assumption: Mean-asymmetry uncertainty scales as sigma/sqrt(N) for independent samples.  
  > "The uncertainty in the measurement of the average asymmetry scales with the number of independent samples $N$ as $\sim \sigma/\sqrt{N}$" (Future EHT Observations)
   - fitting: Median zero-spin p scales as e^(−N/1.6).  
  > "We find the median $p$ for spin zero drops off as $p \sim e^{-N/1.6}$: the constraint improves exponentially as new observations are added." (Future EHT Observations)
   - validation: _not stated_
7. **Check geometric and inclination sensitivity**: Repeat KS tests with different annual coverage, asymmetry bounds, and m-ring order; perturb inclination in a small MAD model sample.  
  > "while varying assumed $(u,v)$ coverage from 2017 to 2021, the assumed parameter bounds from $a_{1 \,\textrm{max}}=1$ to $1.5$, and the geometric model template from an $m=4$ $m$-ring to an $m=3$ one." ($m$-ring Truncation, Asymmetry Bounds, and $(u,v)$ Coverage); "We assess the uncertainty introduced by inclination error in a small sample of models, changing the inclination by $\pm 5^\circ$ from the inclination used in our standard model series." (Degeneracy with Inclination)
   - software: Comrade
   - parameter: Geometric checks: 500 t_g cadence; 60 samples per model and 480 per spin  
  > "This analysis was performed at a reduced cadence of one frame every $500 \, t_g$, leaving 60 samples for each unique model, and 480 for each unique spin." ($m$-ring Truncation, Asymmetry Bounds, and $(u,v)$ Coverage)
   - parameter: Inclination checks: R_high=40, R_low=1, a*=±0.5; 30 images per model separated by >50 t_g  
  > "We consider four MAD models, with $R_{\text{high}}=40$, $R_{\textrm{low}}=1$, and $a_{*}=\pm 0.5$." (Degeneracy with Inclination); "We sample 30 images from each model separated by $> 50\, t_g$." (Degeneracy with Inclination)
   - fitting: Repeat m-ring fitting and two-sample KS tests.  
  > "Finally, we tried fitting an $m=3$ ring to observations and compared to the distribution found in models at each spin and again found largely consistent results." ($m$-ring Truncation, Asymmetry Bounds, and $(u,v)$ Coverage); "Figure [10](#fig:other_modeling) shows two-sample KS test as done in Figure [6](#fig:p_values)" ($m$-ring Truncation, Asymmetry Bounds, and $(u,v)$ Coverage)
   - validation: Coverage and bounds have negligible effect on p-values; geometric-template results largely agree.  
  > "The changes in asymmetry bounds or assumed $(u,v)$ coverage have a negligible effect on $p$-values." ($m$-ring Truncation, Asymmetry Bounds, and $(u,v)$ Coverage); "We conclude that our spin constraints are relatively insensitive to details of the geometric model." ($m$-ring Truncation, Asymmetry Bounds, and $(u,v)$ Coverage)

## Software

- **PATOKA** : GRMHD simulation and ray-traced synthetic-image pipeline  
  > "The library was produced using the `PATOKA `pipeline (cite: wong_patoka_2022), which models the accretion flow using ideal general relativistic magnetohydrodynamics (GRMHD) simulations and then ray-traces GRMHD snapshots to produce synthetic images." (Models)
- **KHARMA** : Integrate the v5 GRMHD simulations  
  > "The GRMHD simulations are integrated with the KHARMA code (cite: Prather_kharma_2024), and the synthetic images are produced using `ipole `(cite: ipole18)." (Models); "compared to the newer KHARMA code used in v5." (v3 Illinois GRMHD Library)
- **ipole** : Produce synthetic images  
  > "The GRMHD simulations are integrated with the KHARMA code (cite: Prather_kharma_2024), and the synthetic images are produced using `ipole `(cite: ipole18)." (Models)
- **iharm** : Evolve the fluid in the comparison v3 library  
  > "In addition, v3 utilized an older `iharm `code (cite: prather_iharm_2021) to evolve the fluid," (v3 Illinois GRMHD Library)
- **Comrade** : Bayesian VLBI modeling; fit m-ring parameters to observed and synthetic data  
  > "we fit a parameterized $m$-ring model using the Comrade package for Bayesian modeling of VLBI observations (cite: tiede_comrade_2022)." (EHT observations); "Finally, we fit the $m$-ring model parameters to the resulting synthetic data using Comrade," (Simulated images)
- **VIDA** : Image-domain asymmetry fitting and comparison  
  > "We demonstrate consistency with asymmetry fits in the image domain using variational image domain analysis (cite: tiede_vida_2022)" (EHT observations); "The EHT analysis of 2018 April 21 data used Comrade and VIDA to measure an asymmetry" (Comparison to Earlier Work)
- **DiFX** : EHT-specific use acknowledged  
  > "We would like to thank A. Deller and W. Brisken for EHT-specific support with the use of DiFX." (Acknowledgments)
- **Difmap** : CLEAN imaging results  
  > "We thank Martin Shepherd for the addition of extra features in the Difmap software that were used for the CLEAN imaging results presented in this paper." (Acknowledgments)
- **Extreme Science and Engineering Discovery Environment (XSEDE)** : Computing resources used by the work  
  > "This work used the Extreme Science and Engineering Discovery Environment (XSEDE), supported by NSF grant ACI-1548562, and CyVerse, supported by NSF grants DBI-0735191, DBI-1265383, and DBI-1743442." (Acknowledgments); "XSEDE Stampede2 resource at TACC was allocated through TG-AST170024 and TG-AST080026N." (Acknowledgments)
- **CyVerse** : Used by the work  
  > "This work used the Extreme Science and Engineering Discovery Environment (XSEDE), supported by NSF grant ACI-1548562, and CyVerse, supported by NSF grants DBI-0735191, DBI-1265383, and DBI-1743442." (Acknowledgments)
- **OSG Consortium** : Services used by the research  
  > "This research was done using services provided by the OSG Consortium," (Acknowledgments)
- **NASA’s Astrophysics Data System** : Used by the research  
  > "This research has made use of NASA’s Astrophysics Data System." (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 2017 observed a1 | 0.41 | ± 0.04 | dimensionless | 1 | Using this procedure to model EHT 2017, 2018, and 2021 observations yields $a_{1}= 0.41 \pm 0.04$, $a_{1}= 0.69 \pm 0.10$, and $a_{1}= 0.53 \pm 0.04$ respectively. |
| 2018 observed a1 | 0.69 | ± 0.10 | dimensionless | 1 | Using this procedure to model EHT 2017, 2018, and 2021 observations yields $a_{1}= 0.41 \pm 0.04$, $a_{1}= 0.69 \pm 0.10$, and $a_{1}= 0.53 \pm 0.04$ respectively. |
| 2021 observed a1 | 0.53 | ± 0.04 | dimensionless | 1 | Using this procedure to model EHT 2017, 2018, and 2021 observations yields $a_{1}= 0.41 \pm 0.04$, $a_{1}= 0.69 \pm 0.10$, and $a_{1}= 0.53 \pm 0.04$ respectively. |
| Normalized chi2 for 2017, 2018, 2021, respectively; not reduced chi2 | 1.9, 0.9, 2.6 | not stated | dimensionless | 1 | The normalized $\chi^2$ is $1.9$, $0.9$, and $2.6$ in 2017, 2018, and 2021 respectively (note these are not reduced $\chi^2$ values). |
| 68th-percentile bound on |a1,UV − a1,I| | less than 0.13 | not stated | dimensionless | 3 | About $68\%$ of snapshots have $/a_{1, UV} - a_{1,I}/$ less than $0.13$, and $90\%$ have difference less than $0.22$. |
| 90th-percentile bound on |a1,UV − a1,I| | less than 0.22 | not stated | dimensionless | 3 | About $68\%$ of snapshots have $/a_{1, UV} - a_{1,I}/$ less than $0.13$, and $90\%$ have difference less than $0.22$. |
| Mean a1 correlation timescale in SANE models | ≈ 70 | not stated | t_g | 3 | Across the v5 model library, we find a mean correlation timescale for $a_{1}$ of $\tau_{corr}\approx 70\,t_g$ for SANEs and $\tau_{corr}\approx 115\,t_g$ for MADs. |
| Mean a1 correlation timescale in MAD models | ≈ 115 | not stated | t_g | 3 | Across the v5 model library, we find a mean correlation timescale for $a_{1}$ of $\tau_{corr}\approx 70\,t_g$ for SANEs and $\tau_{corr}\approx 115\,t_g$ for MADs. |
| MAD truncated-Gaussian mu at spins −0.97, −0.9375, −0.85, −0.75, −0.5, −0.25, 0.0, 0.25, 0.5, 0.75, 0.85, 0.9375, 0.97 | 0.653, 0.609, 0.567, 0.485, 0.382, 0.324, 0.278, 0.378, 0.525, 0.573, 0.630, 0.645, 0.675 | not stated | dimensionless | 4 | / Spin / $-0.97$ / $-0.9375$ / $-0.85$ / $-0.75$ / $-0.5$ / $-0.25$ / $0.0$ / $0.25$ / $0.5$ / $0.75$ / $0.85$ / $0.9375$ / $0.97$ /; / $\mu$ / $0.653$ / $0.609$ / $0.567$ / $0.485$ / $0.382$ / $0.324$ / $0.278$ / $0.378$ / $0.525$ / $0.573$ / $0.630$ / $0.645$ / $0.675$ / |
| MAD truncated-Gaussian sigma at spins −0.97, −0.9375, −0.85, −0.75, −0.5, −0.25, 0.0, 0.25, 0.5, 0.75, 0.85, 0.9375, 0.97 | 0.203, 0.178, 0.193, 0.210, 0.188, 0.168, 0.181, 0.172, 0.201, 0.209, 0.213, 0.220, 0.198 | not stated | dimensionless | 4 | / Spin / $-0.97$ / $-0.9375$ / $-0.85$ / $-0.75$ / $-0.5$ / $-0.25$ / $0.0$ / $0.25$ / $0.5$ / $0.75$ / $0.85$ / $0.9375$ / $0.97$ /; / $\sigma$ / $0.203$ / $0.178$ / $0.193$ / $0.210$ / $0.188$ / $0.168$ / $0.181$ / $0.172$ / $0.201$ / $0.209$ / $0.213$ / $0.220$ / $0.198$ / |
| Two-sample KS p for a*=0 | 0.026 | not stated | dimensionless | 5 | $a_{*}=0$ models have $p=0.026$ and $a_{*}=-0.25$ models have $p=0.049$ in the two-sample KS test. |
| Two-sample KS p for a*=−0.25 | 0.049 | not stated | dimensionless | 5 | $a_{*}=0$ models have $p=0.026$ and $a_{*}=-0.25$ models have $p=0.049$ in the two-sample KS test. |
| KS p for a*=0.25 | ≈ 0.14 | not stated | dimensionless | 5 | Models with $a_{*}= 0.25$ are currently still plausible at $p \approx 0.14$. |
| Tentative spin-magnitude constraint | |a*| ≳ 0.2 | not stated | dimensionless | 5 | Our analysis, based on image asymmetry alone, suggests that M87\* may have $/a_{*}/ \gtrsim 0.2$ |
| Forecast median zero-spin KS p as a function of N | p ∼ e^(−N/1.6) | not stated | dimensionless | 6 | We find the median $p$ for spin zero drops off as $p \sim e^{-N/1.6}$: the constraint improves exponentially as new observations are added. |
| Prograde asymmetry shift for inclination shift ±5° | ± 0.1 | not stated | dimensionless | 7 | In the prograde model, we find a shift of $i\pm5^\circ$ corresponds to a shift in asymmetry of $a_{1}\pm 0.1$. |
| Retrograde asymmetry shift for inclination shift ±5° | ± 0.04 | not stated | dimensionless | 7 | In the retrograde model, we find a shift of $i\pm5^\circ$ corresponds to a shift in asymmetry of $a_{1}\pm 0.04$. |
| Reported N threshold for inclination uncertainty to dominate in retrograde models | ≳ 4 | not stated | dimensionless | 7 | This occurs when $N \gtrsim 4$ for the retrograde models, and $N \gtrsim 25$ for the prograde models. |
| Reported N threshold for inclination uncertainty to dominate in prograde models | ≳ 25 | not stated | dimensionless | 7 | This occurs when $N \gtrsim 4$ for the retrograde models, and $N \gtrsim 25$ for the prograde models. |
| Fast-light test-model asymmetry mean | 0.70 | not stated | dimensionless | 2 | The asymmetry had a mean and standard deviation of $0.70\pm0.18$ in the fast light model, while it was $0.70\pm0.19$ in the slow light model. |
| Fast-light test-model asymmetry standard deviation | 0.18 | not stated | dimensionless | 2 | The asymmetry had a mean and standard deviation of $0.70\pm0.18$ in the fast light model, while it was $0.70\pm0.19$ in the slow light model. |
| Slow-light test-model asymmetry mean | 0.70 | not stated | dimensionless | 2 | The asymmetry had a mean and standard deviation of $0.70\pm0.18$ in the fast light model, while it was $0.70\pm0.19$ in the slow light model. |
| Slow-light test-model asymmetry standard deviation | 0.19 | not stated | dimensionless | 2 | The asymmetry had a mean and standard deviation of $0.70\pm0.18$ in the fast light model, while it was $0.70\pm0.19$ in the slow light model. |

## Qualitative findings

- MAD asymmetry is minimized at zero spin and grows with spin magnitude.  
  > "Models with zero spin show minimum asymmetry, while models with maximum spin magnitude have mean asymmetry that is over twice as large." (Results)
- Current data do not significantly distinguish the higher-spin models.  
  > "However, the relative difference in $p$ between these highly spinning models is insignificant; all are consistent with the data at present." (Results)
- MAD asymmetry depends weakly on R_high and R_low; R_low=10 is mildly favored.  
  > "The asymmetry is only weakly dependent on $R_{\text{high}}$ and $R_{\text{low}}$ in MAD models." (Results); "While our asymmetry does not exclude $R_{\text{high}}=10$, it does mildly favor $R_{\text{low}}=10$." (Results)
- Spin–asymmetry correlation is clearer for MAD than SANE models.  
  > "The spin-ring asymmetry correlation is clearer for MAD models than for SANE models" (Conclusion)
- The asymmetry argument is independent of jet-power estimates.  
  > "Our argument here is independent of the jet power argument, and does not rely on highly uncertain jet power estimates." (Conclusion)

## Claim tuples

- H: Ring brightness asymmetry depends on black hole spin. | E: Measure synthetic asymmetry distributions across the MAD spin library. | R: Zero-spin models have minimum asymmetry; maximum-spin mean asymmetry is over twice as large. | F: MAD ring asymmetry correlates with spin magnitude. | **supported**
- H: The three observed M87* asymmetries are consistent with zero spin. | E: Compare observed and MAD synthetic asymmetry distributions with KS tests. | R: Two-sample p=0.026 for a*=0 and p=0.049 for a*=−0.25. | F: Low-spin models are marginally disfavored; evidence for spinning M87* is tentative. | **partially**
- H: Limited EHT Fourier coverage permits accurate ring-asymmetry measurement. | E: Compare fits to synthetic EHT data with image-domain asymmetry fits. | R: 68% of differences are below 0.13; 90% are below 0.22. | F: Fourier-domain asymmetry provides a nearly unbiased estimate of image-domain asymmetry. | **supported**
- H: The spin constraint depends strongly on geometric-template choices or annual coverage. | E: Vary m=4 to m=3, the upper asymmetry bound from 1 to 1.5, and coverage from 2017 to 2021. | R: Coverage and bounds have negligible effects on p-values; m=3 results largely agree. | F: The tested methodological changes do not materially alter the spin constraint. | **refuted**
- H: Additional independent observations can substantially improve spin constraints. | E: Repeated mock-observation sampling and KS comparisons under assumed asymmetry distributions. | R: Median zero-spin p scales approximately as e^(−N/1.6). | F: Spin constraints can improve rapidly if the assumed distributions describe M87*. | **partially**
- H: The M87* spin inference is consistent with Blandford–Znajek jet launching. | E: Compare the asymmetry-based spin inference with the mechanism's spinning-black-hole requirement. | R: Asymmetry suggests a spinning black hole. | F: The result is consistent with BZ; future observations could test continued spin–jet-power consistency. | **partially**

## Reasoning

- Why this data: Use near-horizon total intensity as a complementary spin constraint given polarization-interpretation uncertainties.  
  > "However, uncertainties in interpreting polarization data (due to, e.g., Faraday rotation and year-to-year variability) motivate complementary constraints using near-horizon total intensity data." (Introduction)
- Why this method: a1 captures large-scale brightness asymmetry; a simpler template permits straightforward interpretation at reduced computational cost.  
  > "Here, $a_{1}$ captures the large-scale brightness asymmetry, while $a_2$ through $a_4$ capture smaller scale turbulent structure." (EHT observations); "The more complex template from 2018 analysis allows for better fits to the 2018 data, while ours allows for more straightforward interpretation at reduced computational cost." (Comparison to Earlier Work)
- Alternative: Focus on MAD models because they are more likely to pass jet-power and polarization constraints.  
  > "In the main text, we focus on MAD models." (Models); "This is motivated by evidence that MAD models are favored by M87\* data, as they are more likely to pass jet power and polarization constraints" (Models)
- Alternative: Reject R_high=1 as disfavored by the data.  
  > "We do not consider $R_{\text{high}}=1$ because it is disfavored by the data" (Models)
- Alternative: Prefer v5 over v3 for higher resolution, longer runs, denser spin sampling, and gamma=5/3.  
  > "We prefer v5 models because (1) they are run at higher resolution; (2) they are run longer and therefore provide better sampling of the asymmetry distribution;" (Models); "(3) they sample spin more densely (13 spins in v5 vs 5 spins in v3); and (4) v5 uses adiabatic index $\gamma = 5/3$, while v3 uses $\gamma = 4/3$." (Models)
- Alternative: Clipped Gaussian fits have little effect on recovered mu.  
  > "We tried fitting a clipped Gaussian and found this had little effect on the recovered $\mu$ for each model." ($m$-ring Truncation, Asymmetry Bounds, and $(u,v)$ Coverage)
- Alternative: Fast-light and slow-light test-model asymmetry distributions are nearly identical.  
  > "We have compared the asymmetry distribution in fast light and slow light versions of a test model and find that they are nearly identical." (Model Uncertainty)
- How they decided it was enough: Downsample synthetic images beyond their approximate correlation timescale to obtain independent observations.  
  > "The images are correlated on timescales $\sim 100 \, t_g$, so we downsample to a cadence of $125 \, t_g$" (Simulated images); "to obtain independent synthetic observations." (Simulated images)
- Limitation (authors): Evidence is tentative because the model library has missing physics and internal inconsistencies, the main analysis is restricted to MAD, and only three observations are independent.  
  > "the relevance of the model library itself, which is known to have missing physical ingredients and internal inconsistencies" (Conclusion); "a restriction of the model library to magnetically arrested disk (MAD) models, which are nevertheless preferred by EHT data; and (3) only three independent observations." (Conclusion)
- Limitation (authors): Tilted disks are not considered.  
  > "The spin and accretion disk angular momentum vector are assumed to be coaxial: we do not consider tilted disks." (Models)
- Limitation (authors): Asymmetry distributions depend on the model.  
  > "Our asymmetry distributions are model-dependent." (Model Uncertainty)
- Limitation (authors): Electron distribution is assumed thermal and isotropic, with Te much less than Ti.  
  > "Our models assume the electron distribution function is thermal with $T_e(\beta, T_i; R_{\text{high}}, R_{\text{low}})$, $T_e \ll T_i$, and with an isotropic $T_e$ relative to the local magnetic field." (Model Uncertainty)
- Limitation (authors): Accuracy of the ideal-fluid approximation for a Coulomb-collisionless plasma is not understood.  
  > "Our models treat the accreting plasma as an ideal fluid, but the plasma is known to be Coulomb-collisionless." (Model Uncertainty); "The accuracy of this approximation is not yet understood." (Model Uncertainty)
- Limitation (authors): Sensitivity to initial and boundary conditions has not been fully assessed.  
  > "The variation of model outcomes with respect to changes in this initial condition and boundary conditions have not yet been fully assessed." (Model Uncertainty)
- Limitation (authors): Some high-spin SANE distributions are poorly fit because the asymmetry boundary truncates much of the distribution.  
  > "A small fraction of high-spin SANEs are poorly fit, as the asymmetry boundary truncates a significant portion of the asymmetry distribution." (Asymmetry Fits from GRMHD Library)
- Limitation (authors): High-spin v5 SANE comparisons use shorter duration, higher cadence, and reduced image resolution.  
  > "asymmetry measurements for v5 SANEs at $a_{*}=0.85$ and $0.97$ were calculated over a shorter duration ($t=20,000$ to $30,000 \, t_g$ rather than $20,000$ to $50,000 \, t_g$)" (Other Model Sets); "with a slightly higher cadence (every $100\,t_g$ rather than every $125\,t_g$), using a reduced image resolution." (Other Model Sets)
- Caveat (inferred, ours): KS p-values are not posterior probabilities for spin; the tentative spin threshold depends on the selected model family.
- Caveat (inferred, ours): The reported inclination-dominance thresholds appear reversed relative to the reported prograde and retrograde asymmetry shifts; verify before reusing them.
- Caveat (inferred, ours): The 125 t_g synthetic cadence is only slightly longer than the reported 115 t_g MAD correlation timescale; residual dependence merits checking.
- Caveat (inferred, ours): Marginalization weights and propagation of observational asymmetry uncertainties into the KS tests are unspecified.
- Caveat (inferred, ours): The ALMA contribution is acknowledged through project codes, but its station-level processing cannot be reconstructed from this text.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Public-access statements and exact locations for the EHT fit inputs and v5 synthetic images or snapshots.
- Missing: Analysis scripts, package versions, and complete Comrade fitting configuration.
- Missing: Synthetic-observation noise configuration and jet-axis rotation angle.
- Missing: Radiative-parameter marginalization weights and observational-error treatment.
- Missing: Simulation and ray-tracing configuration sufficient to regenerate the library.
- Missing: Forecast repetition counts and random seeds.
- Missing: Complete machine-readable per-model fit table, which is referenced but only partially supplied here.
- Data volume (inferred): Bytes cannot be estimated: image dimensions and visibility counts are absent. The main library contains 104 × 6000 images before downsampling.
- Score (inferred): 4/5, The statistical recipe, parameter grid, observed asymmetries, and aggregate fit table are explicit. Exact inputs, public availability, software configuration, and simulation-generation settings are insufficient for an independent end-to-end reproduction.
- Rediscovery candidate: no, Main results are numeric, but public data availability is not stated and the EHT fitting inputs and v5 library are not sufficiently specified or located.

## Links

- Method: (cite: wong_patoka_2022) (PATOKA simulation and ray-tracing pipeline; additional model details.)
- Method: (cite: Prather_kharma_2024) (KHARMA GRMHD integration code.)
- Method: (cite: ipole18) (ipole synthetic-image generation.)
- Method: (cite: prather_iharm_2021) (iharm code used in the v3 comparison library.)
- Method: (cite: moscibrodzca16) (Electron-to-ion temperature prescription.)
- Method: (cite: tiede_comrade_2022) (Comrade Bayesian modeling of VLBI observations.)
- Method: (cite: tiede_vida_2022) (Image-domain analysis, m-ring modeling, and detailed optimization validation.)
- Method: (cite: johnson_photon_2020) (m-ring Fourier representation and near-horizon lensing discussion.)
- Method: (cite: Chael_2018) (Synthetic EHT sampling and realistic observational noise.)
- Method: (cite: Fishbone_moncrief_torus; wong_patoka_2022) (Magnetized torus initial conditions.)
- Method: (cite: grete_2023) (Implicit Large Eddy Simulation and numerical dissipation discussion.)
- Companion: Bowden et al., in preparation (v5 Illinois GRMHD library used for the main analysis.)
- Companion: (cite: Dhruv_grmhd_survey_2024) (v3 GRMHD library used for model comparisons.)
- Companion: EHTC M87 I–VI (cite: EHTC_2019_1; EHTC_2019_2; EHTC_2019_3; EHTC_2019_4; EHTC_2019_5; EHTC_2019_6) (2017 EHT observational campaign papers.)
- Companion: EHTC M87 2018 I–II (cite: EHTC_2024_1; EHTC_2025_1) (2018 EHT observational campaign papers.)
- Companion: EHTC M87 2021 (cite: EHTC_2025_1_M87_21) (2021 EHT observational campaign paper.)
- Related: Event Horizon Telescope (EHT)
- Related: Illinois v5 KHARMA library
- Related: v3 Illinois GRMHD Library

## Checks

```json
{
 "quotes": 186,
 "quotes_ok": 186,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 23,
 "numeric_problems": 0,
 "fill": {
  "facts": 138,
  "stated": 101,
  "rate": 0.732
 },
 "evidence_ok": true
}
```
