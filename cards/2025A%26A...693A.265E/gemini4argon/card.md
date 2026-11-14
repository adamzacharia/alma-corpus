# The persistent shadow of the supermassive black hole of M87: II. Model comparisons and theoretical interpretations

`2025A&A...693A.265E` | Astronomy and Astrophysics 2025 | first author: Event Horizon Telescope Collaboration | arXiv: - | DOI: 10.1051/0004-6361/202451296

Card schema 1.0 | model gemini-4-argon | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: agn_and_quasars
- Question: What are the theoretical interpretations and physical constraints on the M87* black hole and its surrounding accreting plasma from comparing an extended library of GRMHD simulations with the 2017 and 2018 EHT observations?  
  > "we provide theoretical interpretations for the multi-epoch EHT observations for M87" (abstract); "we focus on the theoretical interpretation of the observed total intensity of M87" (Sect. 1)
- Target **M87***: coordinates _not stated_; z/distance 16.8 Mpc (fiducial models), 16.2 Mpc (radiative models)  
  > "into units of solar masses at a distance of 16.8 Mpc" (Sect. 5.3); "at a distance of D = 16.2 Mpc, and an observational frequency of 230 GHz" (Sect. 3, footnote 3); distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00841.V, 2016.1.01154.V
- bands: _not stated_
- frequencies and spectral setup: centered at 229 GHz (high-band in 2017 and band 4 in 2018)  
  > "We focused our comparisons on the EHT observations centered at 229 GHz (high-band in 2017 and band 4 in 2018)." (4.1. Overview of the data selection and comparison)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: April 6, 2017, and April 21, 2018  
  > "To obtain uncorrelated constraints, we focused our comparisons on two selected days from each campaign: April 6, 2017, and April 21, 2018." (4.1. Overview of the data selection and comparison)
- pi or archival as stated: _not stated_
- Other facility **Event Horizon Telescope (EHT)**: VLBI observations of M87* at 1.3 mm (229 GHz) in April 2017 and April 2018  
  > "The EHT collected multiple epochs of M87 data in two frequency bands in 2017 and four frequency bands in 2018. We focused our comparisons on the EHT observations centered at 229 GHz" (Sect. 4.1); "We focused our comparisons on the EHT observations centered at 229 GHz (high-band in 2017 and band 4 in 2018)." (4.1. Overview of the data selection and comparison)
- External data: 2018 EHT observations and compact flux density (roughly 0.5 Jy at 228 GHz)  
  > "determined by the averaged compact flux density of roughly 0.5 Jy at 228 GHz" (Sect. 3) [from Paper I; M87* 2018 I]
- External data: Milliarcsecond-scale jet position angle PA = 288 deg +/- 10 deg and inclination angle 17 deg  
  > "This is true for the 2017 and 2018 scores, but compared to 2017, the 2018 preferred PA distributions are overall significantly better aligned with the large-scale jet." (4.2. Snapshot scoring constraints); "_PA_ = 288 [◦] ± 10 [◦] of the milliarcsecond-scale jet (Walker et al. 2018; Cui et al. 2023)" (Figure 5 caption); "When the angle between the approaching jet and the line of sight is 17" (Sect. 3) [from Walker et al. 2018; Cui et al. 2023]
- External data: Multiwavelength radio and X-ray observations of M87* collected during the 2018 EHT campaign  
  > "In Fig. 8 we present the SEDs for three best-bet models along with radio and X-ray observations collected in 2018 (EHT MWL Science Working Group 2024)." (5.2. Multiwavelength spectra of the selected best-bet models) [from EHT MWL Science Working Group 2024]
- External data: Observational jet power lower limit of 10^42 erg s^-1  
  > "Previous studies of M87 estimated its jet power to be P_jet = 10^42-10^45 erg s^-1 (Reynolds et al. 1996; Li et al. 2009; de Gasperin et al. 2012; Broderick & Tchekhovskoy 2015; Prieto et al. 2016)." (4.5. Jet-power constraint); "Finally, in addition to the EHT constraints of the three aforementioned scoring schemes, the M87 jet power in the models was required to exceed a lower limit of 10^42 erg s^-1." (4.1. Overview of the data selection and comparison) [from Reynolds et al. 1996; Li et al. 2009; de Gasperin et al. 2012; Broderick & Tchekhovskoy 2015; Prieto et al. 2016]
- Simulation/model as data: 3D GRMHD simulation library (~184,000 image snapshots) generated using BHAC, H-AMR, KHARMA, and koral codes, covering SANE and MAD states, thermal and nonthermal synchrotron emission, tilted disks, and radiative models  
  > "A total of four GRMHD codes contributed to our model libray: BHAC (Porth et al. 2017), H-AMR (Liska et al. 2022), KHARMA (Prather 2022), and koral (Sadowski et al. 2013; Sadowski et al. 2017)." (3. Image library of the extended GRMHD simulations); "Our extended image library consists of ∼184 000 snapshots, and it is three times larger than the library assembled in" (Sect. 3.3)

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

- Choice of April 6, 2017 dataset, snapshot scoring, average image scoring (AIS), and jet power criterion  
  > "based on the highest number of scans in the 2017 datasets and because of the four days of observations in 2017, April 5/6 differ most from the 2018 image." (Sect. 4.1); "we first compared the models to the observations using two previously developed algorithms: the snapshot scoring, and the average imaging scoring (hereafter, AIS)" (Sect. 4.1); "we computed the powers of outflows in our GRMHD simulations and compared them with observations" (Sect. 4.5) [from M87* 2017 V; M87* 2017 VI]
- Tilted disk GRMHD models  
  > "The tilted models were adopted from Chatterjee et al. (2020, see also Liska et al. 2018) and evolved using H-AMR code for a considerably longer time than the fiducial simulations." (3.2. Exploratory models) [from Chatterjee et al. (2020); Liska et al. (2018)]
- Radiative two-temperature GRMHD models  
  > "Our library also includes radiative two-temperature models from Chael et al. (2019a) that were simulated using the KORAL-grtrans pipeline." (3.2. Exploratory models) [from Chael et al. (2019a)]
- Julia-based scoring driver  
  > "Third, the scoring was performed with an efficient Julia-based driver developed following Tiede (2022)." (4.1. Overview of the data selection and comparison) [from Tiede (2022)]

### Not stated but needed to reproduce (our reading)

- VLBI calibration and phasing details for the ALMA array and the rest of the EHT stations (deferred to companion/earlier EHT papers)
- Exact initialization parameters (e.g., torus inner radius and pressure maximum radius) for the new KHARMA, BHAC, and H-AMR fiducial simulations

## Analysis recipe

1. **Generate 3D GRMHD simulation library**: Run 3D GRMHD simulations of magnetized plasma tori accreting onto a black hole in SANE and MAD states, plus exploratory tilted and radiative models  
  > "Our numerical model library consists of a number of 3D GRMHD simulations of gas from a magnetized torus accreting onto a black hole and producing a jet." (3. Image library of the extended GRMHD simulations)
   - software: BHAC, H-AMR, KHARMA, koral
   - parameter: a_* = 0, +/-0.5, +/-0.94; t_final = 16000 to 105000 GM/c^3; Gamma_ad = 4/3, 13/9, 5/3  
  > "0, ±0.5, ±0.94 MAD 139 35 000 1000 348 × 192 × 192" (Table 1)
   - assumption: Hydrodynamic torus initial condition (Fishbone & Moncrief 1976 or Penna et al. 2013) seeded with poloidal magnetic fields  
  > "All GRMHD simulations in this work began with a hydrodynamic torus of gas (Fishbone & Moncrief 1976) with a constant adiabatic index Γ ad seeded with a loop of poloidal magnetic fields, except for the radiative model." (Sect. 3)
   - fitting: _not stated_
   - validation: _not stated_
2. **Synthesize mock 228/230 GHz images via relativistic ray-tracing**: Post-process GRMHD snapshots with relativistic radiative transfer codes assuming synchrotron emission and self-absorption under the fast-light approximation  
  > "The GRMHD simulations were post-processed with three ray-tracing codes BHOSS (Younsi et al. 2012, 2020), grtrans (Dexter 2016), and ipole (Moscibrodzka & Gammie 2018 and see Wong et al. 2022 for pipeline description) that integrate the radiative transfer equations assuming synchrotron emission and self-absorption." (3. Image library of the extended GRMHD simulations); "For the sake of the computational efficiency, all images were computed using the so-called fast-light approximation, which assumes that the light has infinite speed." (3. Image library of the extended GRMHD simulations)
   - software: BHOSS, grtrans, ipole
   - parameter: R_high = 1, 10, 20, 40, 80, 160; R_low = 1, 10; sigma_cut = 1, 3; inclination = 17 deg, 163 deg; FOV = 200 uas x 200 uas (400 x 400 pixels)  
  > "1,10,20,40,80,160 1 1 17 [◦],163 [◦] 25–30" (Table 2); "The field of view and resolution of the mock images usually were 200 µas × 200 µas and 400 × 400 pixels" (Sect. 3)
   - assumption: M_BH = 6.5 x 10^9 M_odot, D = 16.8 Mpc, compact flux density ~ 0.5 Jy at 228 GHz (for fiducial models); R_high - R_low electron temperature prescription or nonthermal kappa distribution  
  > "were constructed by the ray-tracing techniques assuming a black hole mass _M_ BH = 6.5 × 10 [9] _M_ ⊙, a distance _D_ = 16.8 Mpc" (Sect. 3); "determined by the averaged compact flux density of roughly 0.5 Jy at 228 GHz" (Sect. 3)
   - fitting: _not stated_
   - validation: _not stated_
3. **Perform snapshot scoring, Average Image Scoring (AIS), and multi-epoch scoring**: Fit rotated and resized model snapshots and time-averaged images to 2017 and 2018 EHT VLBI closure quantities, then combine single-year AIS evidence and snapshot posteriors via Bayesian multi-epoch scoring  
  > "Second, we fit the closure quantities of the VLBI data, such as the closure phases and the closure amplitudes." (4.1. Overview of the data selection and comparison); "In this procedure, we fit a given model with the EHT data by rotating and resizing every image in the model to find the best-fit values of the image orientation and the implied mass-to-distance ratio, M/D." (4.2. Snapshot scoring constraints); "the multi-epoch scoring post-processes the snapshot scoring and AIS scoring results following a Bayesian approach in which AIS results are treated as approximations for Bayesian evidence, and the snapshot scoring results are used as approximations of the ensemble-based posteriors" (Sect. 4.4)
   - software: Julia-based driver
   - parameter: Top 10% best-fit snapshots by chi^2; AIS probability thresholds 15% or 10%; multi-epoch normalized odds ratio threshold >= 1%  
  > "For posterior estimations for each model, we considered the best 10% images according the snapshot scoring results." (4.4. Multi-epoch scoring constraints); "We selected 1% of the normalized odds ratio as the arbitrary threshold for the passing models." (4.4. Multi-epoch scoring constraints)
   - assumption: 2017 and 2018 datasets are independent; total flux is independent from year to year; PA and mass M are fixed across years  
  > "We assume that the total flux is independent from year to year, and that the PA and mass are fixed." (Appendix C.3); "We assume that the total flux is independent from year to year, and that the PA and mass are fixed." (C.1. Overview: a Bayesian view)
   - fitting: Optimization approach fitting VLBI closure phases and closure amplitudes, followed by kernel density estimation (KDE) for ensemble-based posteriors  
  > "First, we applied an optimization approach instead of the MCMC method with gain fitting (Broderick et al. 2020)" (Sect. 4.1); "Continuous posteriors are generated from kernal density estimations (KDEs) of the sampled values after applying desired" (Appendix C)
   - validation: Validated using synthetic datasets drawn from simulation images on 2017 data  
  > "Validation requires additional iterations using synthetic data sets drawn from simulation images. This procedure was already validated on the 2017 data." (C.2. Ensemble-based posterior construction)
4. **Apply jet-power constraint and evaluate multiwavelength SEDs**: Compute time-averaged outward energy flux P_out over polar regions and require P_out >= 10^42 erg s^-1; compute broadband SEDs for selected best-bet models using Monte Carlo radiative transfer  
  > "as in previous EHT publications for the failing models with an insufficient jet power, that is, a model fails when its outward energy flux (outflow power;" (Sect. 4.5); "The SEDs were generated using the Monte Carlo relativistic radiative transfer code grmonty (Dolence et al. 2009), which includes synchrotron (emission and self-absorption), inverse-Compton scattering, and bremsstrahlung emission." (5.2. Multiwavelength spectra of the selected best-bet models)
   - software: grmonty
   - parameter: Polar angle integration of 1 radian about north and south poles; P_out >= 10^42 erg s^-1  
  > "Here, the polar angle integration includes 1 radian about the north or south poles and only those regions whose energy flux is directed outward." (4.5. Jet-power constraint)
   - assumption: Observed X-ray luminosity treated as an upper limit for the horizon-scale models  
  > "When we treat the observed X-ray luminosity as an upper limit for the models, the best-bet models shown in Fig. 8 are all acceptable." (5.2. Multiwavelength spectra of the selected best-bet models)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **BHAC** : 3D GRMHD simulations of MAD accretion flows  
  > "A total of four GRMHD codes contributed to our model libray: BHAC (Porth et al. 2017), H-AMR (Liska et al. 2022), KHARMA (Prather 2022), and koral (Sadowski et al. 2013; Sadowski et al. 2017)." (3. Image library of the extended GRMHD simulations)
- **H-AMR** : 3D GRMHD simulations of aligned MAD/SANE and tilted SANE accretion flows  
  > "A total of four GRMHD codes contributed to our model libray: BHAC (Porth et al. 2017), H-AMR (Liska et al. 2022), KHARMA (Prather 2022), and koral (Sadowski et al. 2013; Sadowski et al. 2017)." (3. Image library of the extended GRMHD simulations); "The tilted models were adopted from Chatterjee et al. (2020, see also Liska et al. 2018) and evolved using H-AMR code for a considerably longer time than the fiducial simulations." (3.2. Exploratory models)
- **KHARMA** : 3D GRMHD simulations of MAD and SANE accretion flows  
  > "A total of four GRMHD codes contributed to our model libray: BHAC (Porth et al. 2017), H-AMR (Liska et al. 2022), KHARMA (Prather 2022), and koral (Sadowski et al. 2013; Sadowski et al. 2017)." (3. Image library of the extended GRMHD simulations)
- **koral** : Radiative two-temperature 3D GRMHD (GRRMHD) simulations  
  > "Our library also includes radiative two-temperature models from Chael et al. (2019a) that were simulated using the KORAL-grtrans pipeline." (3.2. Exploratory models)
- **BHOSS** : Relativistic ray-tracing radiative transfer for H-AMR and BHAC simulations  
  > "The GRMHD simulations were post-processed with three ray-tracing codes BHOSS (Younsi et al. 2012, 2020), grtrans (Dexter 2016), and ipole (Moscibrodzka & Gammie 2018 and see Wong et al. 2022 for pipeline description) that integrate the radiative transfer equations assuming synchrotron emission and self-absorption." (3. Image library of the extended GRMHD simulations)
- **grtrans** : Relativistic ray-tracing radiative transfer for koral radiative simulations  
  > "The GRMHD simulations were post-processed with three ray-tracing codes BHOSS (Younsi et al. 2012, 2020), grtrans (Dexter 2016), and ipole (Moscibrodzka & Gammie 2018 and see Wong et al. 2022 for pipeline description) that integrate the radiative transfer equations assuming synchrotron emission and self-absorption." (3. Image library of the extended GRMHD simulations)
- **ipole** : Relativistic ray-tracing radiative transfer for KHARMA simulations  
  > "The GRMHD simulations were post-processed with three ray-tracing codes BHOSS (Younsi et al. 2012, 2020), grtrans (Dexter 2016), and ipole (Moscibrodzka & Gammie 2018 and see Wong et al. 2022 for pipeline description) that integrate the radiative transfer equations assuming synchrotron emission and self-absorption." (3. Image library of the extended GRMHD simulations)
- **Julia-based driver** : Snapshot and AIS scoring of model images against VLBI closure quantities  
  > "Third, the scoring was performed with an efficient Julia-based driver developed following Tiede (2022)." (4.1. Overview of the data selection and comparison)
- **grmonty** : Monte Carlo relativistic radiative transfer to generate broadband SEDs  
  > "The SEDs were generated using the Monte Carlo relativistic radiative transfer code grmonty (Dolence et al. 2009), which includes synchrotron (emission and self-absorption), inverse-Compton scattering, and bremsstrahlung emission." (5.2. Multiwavelength spectra of the selected best-bet models)
- **DiFX** : VLBI correlation (mentioned in acknowledgements)  
  > "We would like to thank A. Deller and W. Brisken for EHT-specific support with the use of DiFX." (Appendix A: Acknowledgements)
- **Difmap** : CLEAN imaging (mentioned in acknowledgements)  
  > "We thank Martin Shepherd for the addition of extra features in the Difmap software that were used for the CLEAN imaging results presented in this paper." (Appendix A: Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| M87* mass-to-distance ratio (M/D) from 2017 data | 3.70 | +0.51/-0.59 | uas | 3 | 2017 3.70 |
| M87* mass (M) from 2017 data | 6.30e9 | +0.87e9/-1.01e9 | M_odot | 3 | 2017 3.70 [+] − [0] 0 [.] . [51] 59 6.30 [+] − [0] 1 [.] . [87] 01 |
| M87* mass-to-distance ratio (M/D) from 2018 data | 4.17 | +0.41/-0.66 | uas | 3 | 2018 4.17 |
| M87* mass (M) from 2018 data | 7.09e9 | +0.69e9/-1.11e9 | M_odot | 3 | 2018 4.17 [+] − [0] 0 [.] . [41] 66 7.09 [+] − [0] 1 [.] . [69] 11 |
| M87* combined (2017 + 2018) mass-to-distance ratio (M/D) | 3.62 | +0.41/-0.34 | uas | 3 | 2017 + 2018 3.62 |
| M87* combined (2017 + 2018) mass (M) | 6.16e9 | +0.71e9/-0.57e9 | M_odot | 3 | 2017 + 2018 3.62 [+] − [0] 0 [.] . [41] 34 6.16 [+] − [0] 0 [.] . [71] 57 |
| Number of best-bet fiducial models passing both multi-epoch and jet-power constraints | 68 | not stated | dimensionless | 4 | The 68 best-bet models of the 194 fiducial models are shown in Table 3. |

## Qualitative findings

- The 2018 EHT observation confirms that the spin vector of the M87* supermassive black hole is pointed away from Earth.  
  > "The 2018 observation again shows that the spin vector of the M87 [∗] supermassive black hole is pointed away from Earth." (abstract)
- The ~30 deg shift of the brightest part of the ring between 2017 and 2018 is naturally explained by accretion turbulence, and more turbulent retrograde models have a higher survival rate than prograde models in multi-epoch scoring.  
  > "A shift of the brightest part of the ring during the multi-epoch observations can naturally be explained by the turbulent nature of black hole accretion, which is supported by the fact that the more turbulent retrograde models can explain the multi-epoch observations better than the prograde models." (abstract); "Among all the best-bet models, retrograde models have a relatively higher survival rate than all other cases." (5.1. Summary of the model constraints and best-bet models)
- MAD models achieve higher survival rates and multi-epoch scores overall than SANE models, and a_* = 0 MAD models generally fail the jet-power constraint.  
  > "Figure 7 shows models from all three pipelines with high relative scores, and MAD models reach higher scores overall than SANE models." (4.4. Multi-epoch scoring constraints); "MAD models fail the power constraint most often (16 out of 20 fail)." (Sect. 4.5)
- Exploratory tilted-disk models with tilt angles of 30 deg and 60 deg are inconsistent with the EHT data due to their crescent-like rather than ring-like morphology.  
  > "The EHT data are inconsistent with the tilted models in our model image library." (abstract); "due to the more crescent-like, instead of ring-like, morphology of the tilted images (compare Fig. 3 with Fig. B.1)." (Sect. 4.2)

## Claim tuples

- H: The spin axis of the M87* black hole is pointed away from Earth, and future observations after 2017 should show the brightest part of the ring shifted counterclockwise toward ~90 deg clockwise from the forward jet. | E: Compare ~184,000 GRMHD simulation snapshots (with spin pointing toward and away from Earth) to the 2017 and 2018 EHT VLBI closure data via snapshot scoring and compare fitted jet position angles with the observed large-scale jet PA (288 +/- 10 deg). | R: Models with the black hole spin axis pointing away from Earth align with the large-scale jet PA = 288 +/- 10 deg, and the 2018 preferred PA distributions are even better aligned with the large-scale jet than in 2017. | F: The spin vector of M87* points away from Earth, and the brightest part of the ring is expected to be most commonly observed 90 deg clockwise from the forward jet. | **supported**
- H: The observed shift in the position angle of the brightest part of the M87* ring between 2017 and 2018 arises from turbulent fluctuations in the accretion flow. | E: Apply Bayesian multi-epoch scoring combining 2017 and 2018 snapshot and AIS scores requiring consistent M/D and jet PA across both epochs. | R: 68 of 194 fiducial models pass both multi-epoch and jet-power constraints, with retrograde models (which exhibit broader PA distributions due to stronger turbulence) showing a higher survival rate than prograde models. | F: Accretion turbulence naturally explains the shift in ring brightness asymmetry, and more turbulent retrograde models match the two-epoch observations better than prograde models. | **supported**
- H: Tilted accretion disk models can explain the horizon-scale EHT structure of M87*. | E: Score exploratory H-AMR tilted-disk GRMHD models (tilt angles 30 deg and 60 deg, a_* = +0.94) against the 2017 and 2018 EHT data. | R: Tilted-disk models with tilt angles of 30 deg and 60 deg yield much higher reduced chi^2 values and fail the multi-epoch scoring cutoff. | F: The EHT data are inconsistent with the tilted models in the current model image library. | **refuted**
- H: The mass-to-distance ratio M/D of M87* is persistent across epochs as required by a stationary general relativistic spacetime. | E: Derive M/D posterior distributions from the top 10% best-fitting snapshots in 2017, 2018, and combined 2017+2018 multi-epoch scoring. | R: M/D = 3.70 +0.51/-0.59 uas (2017), 4.17 +0.41/-0.66 uas (2018), and 3.62 +0.41/-0.34 uas (2017+2018 combined), corresponding to M = 6.16 +0.71/-0.57 x 10^9 M_odot at 16.8 Mpc. | F: The new single-year and combined M/D and mass estimates are statistically consistent with each other and with the 2019 EHT result (6.50 +/- 0.7 x 10^9 M_odot). | **supported**

## Reasoning

- Why this data: April 6, 2017 was chosen for having the highest number of scans in 2017 and differing most from 2018; April 21, 2018 was chosen for having the best (u,v)-coverage in 2018; the 1-year separation ensures uncorrelated turbulent realizations.  
  > "based on the highest number of scans in the 2017 datasets and because of the four days of observations in 2017, April 5/6 differ most from the 2018 image." (Sect. 4.1)
- Why this method: Optimization on VLBI closure quantities with a Julia-based driver was used to reduce computational cost across ~184,000 images; AIS overcomes individual turbulent snapshot fluctuations; multi-epoch Bayesian scoring enforces consistent M/D and PA across years.  
  > "To effectively perform the scoring procedures on a significant number of model images, a few improvements were made to reduce the computational cost of the calculations." (4.1. Overview of the data selection and comparison); "To effectively perform the scoring procedures on a significant number of model images, a few improvements were made to reduce the computational cost of the calculations." (Sect. 4.1)
- Alternative: Slow-light radiative transfer was rejected in favor of the fast-light approximation for computational efficiency.  
  > "For the sake of the computational efficiency, all images were computed using the so-called fast-light approximation, which assumes that the light has infinite speed." (3. Image library of the extended GRMHD simulations)
- Alternative: MCMC with gain fitting was replaced by an optimization approach on closure quantities to reduce computational cost.  
  > "First, we applied an optimization approach instead of the MCMC method with gain fitting (Broderick et al. 2020)" (Sect. 4.1)
- Alternative: Running new radiative GRMHD simulations with updated flux normalization (0.5 Jy instead of 0.98 Jy) was rejected due to computational cost being an order of magnitude higher.  
  > "but since the computational cost can be higher by an order of magnitude than a typical fiducial model, we chose not to produce new radiative simulations for this analysis and instead used what was already available." (Sect. 3.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Differences in adiabatic index Gamma_ad, sigma_cut, grid resolution, and radiative transfer implementations across simulation pipelines introduce systematic variations in model images.  
  > "The effects of changing the equation of state, σ cut, and other parameters in model-data comparisons have yet to be fully investigated" (Sect. 3.3)
- Limitation (authors): Multi-epoch analysis is based on only two epochs (2017 and 2018), making conclusions subject to small-number statistics and finite sampling of correlation times.  
  > "We note that the identification of good models that passed the AIS scoring was based on only two observations, so caution should be taken when interpreting these results." (4.3. Average imaging scoring constraints); "The current multi-epoch analysis was performed on just two years of data, so that any differences between the years may be subject to concerns about small-number statistics." (6. Conclusions)
- Limitation (authors): Exploratory models (tilted and radiative) sample a much smaller parameter space (only a_* = +0.94) than the fiducial models.  
  > "Our exploratory models are sampled more sparsely than the fiducial models. There is a larger parameter space left to be explored for these models in the future" (Sect. 5.1)
- Limitation (authors): Retrograde models produce less compact images, which biases snapshot scoring toward shrinking simulated images and yielding slightly lower M/D estimates.  
  > "The retrograde models generally produce less compact images, so that the snapshot scoring procedure tends to shrink the simulated images to match the size of the emission region in the real data, leading to lower mass estimates." (5.3. Mass-to-distance ratios and implications for gravitational physics)
- Limitation (authors): AIS score is not a true Bayesian evidence and EBPC is not a true posterior because turbulence is not fully parameterized or sampled.  
  > "The AIS score is not, however, exactly a Bayesian evidence, despite being used as such." (C.4.2. Approximate integration); "Similarly, the EBPC is not, exactly, a true posterior; it is typically broader." (C.4.2. Approximate integration)
- Caveat (inferred, ours): Fitting only closure quantities discards absolute flux density and baseline amplitude calibration information during the scoring step.
- Caveat (inferred, ours): The preference for retrograde models may be sensitive to the arbitrary 1% odds ratio cutoff and the 10% snapshot selection threshold.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Public release or archive location of the ~184,000 GRMHD synthetic image library
- Missing: Exact version and scripts of the Julia-based scoring driver used for snapshot, AIS, and multi-epoch scoring
- Missing: Calibrated 2017 and 2018 EHT UVFITS data files for April 6, 2017 and April 21, 2018
- Data volume (inferred): Several TB for the 3D GRMHD simulation outputs and ~100-500 GB for the ~184,000 ray-traced image snapshots; a few MB for the EHT VLBI closure datasets.
- Score (inferred): 45/5, The mathematical formulation of the scoring (snapshot, AIS, and multi-epoch Bayesian combination) and the simulation grid parameters are well documented, but reproducing the results requires a massive proprietary library of ~184,000 GRMHD snapshots and custom scoring scripts not released with the paper.
- Rediscovery candidate: no, This is a theoretical interpretation paper relying on a massive (~184,000 snapshot) GRMHD simulation library and EHT VLBI data rather than standalone ALMA archival data products.

## Links

- Method: Porth et al. 2017 (BHAC 3D GRMHD code)
- Method: Liska et al. 2022 (H-AMR 3D GRMHD code)
- Method: Prather 2022 (KHARMA 3D GRMHD code)
- Method: Sadowski et al. 2013; Sadowski et al. 2017 (koral radiative GRMHD code)
- Method: Younsi et al. 2012, 2020 (BHOSS relativistic ray-tracing code)
- Method: Dexter 2016 (grtrans relativistic ray-tracing code)
- Method: Moscibrodzka & Gammie 2018; Wong et al. 2022 (ipole relativistic ray-tracing code and pipeline)
- Method: Dolence et al. 2009 (grmonty Monte Carlo radiative transfer code)
- Method: Tiede 2022 (Julia-based VLBI model scoring framework)
- Method: M87* 2017 V; M87* 2017 VI (Snapshot scoring, Average Image Scoring (AIS), and Ensemble-based Posterior Construction (EBPC) methods)
- Companion: Event Horizon Telescope Collaboration (Akiyama, K., et al.) 2024, A&A, 681, A79 (M87* 2018 I) (Paper I of the series presenting the 2018 EHT observations, calibration, and image reconstructions of M87*)
- Companion: EHT MWL Science Working Group (Algaba, J. C., et al.) 2024, A&A, 692, A140 (Simultaneous 2018 broadband multiwavelength observations of M87)
- Related: Event Horizon Telescope (EHT)

## Checks

```json
{
 "quotes": 98,
 "quotes_ok": 98,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 7,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 96,
  "stated": 53,
  "rate": 0.552
 },
 "evidence_ok": true
}
```
