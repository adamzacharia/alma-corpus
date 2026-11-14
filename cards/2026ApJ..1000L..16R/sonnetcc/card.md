# exoALMA. XXIII. Estimating Disk and Planet Properties from Dust Morphologies with DBNets 2.0

`2026ApJ..1000L..16R` | The Astrophysical Journal Letters 2026 | first author: Ruzza, Alessandro | arXiv: 2603.13149 | DOI: 10.3847/2041-8213/ae434c

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: protoplanetary_disks
- Question: What disk properties (alpha-viscosity, scale height, dust Stokes number) and planet masses would reproduce the dust substructures of the exoALMA disks if each were carved by an embedded planet  
  > "We estimate the putative planet mass, the disk $\alpha$-viscosity, scale-height, and dust Stokes number that would reproduce 19 substructures in 13 of the 15 exoALMA disks." (abstract); "we aim to investigate what population of planets would be consistent with these substructures, assuming that each is the result of the disk interaction with an embedded young planet." (1 Introduction)
- Target **AA Tau**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **CQ Tau**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **DM Tau**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **HD 135344B**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **HD 143006**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **HD 34282**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **J1604**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **J1615**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **J1842**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **J1852**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **LkCa 15**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **MWC 758**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **SY Cha**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **V4046 Sgr**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **PDS 66**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2021.1.01123.L
- bands: Band 7 (0.8-1.1 mm) continuum  
  > "exoALMA Band 7 ($\lambda=0.8–1.1$ mm)" (5.2 Comparison with DBNets2.0 estimates); "we considered all fiducial Band 7 continuum observations of the exoALMA Large Program" (3 Sample selection and methodology)
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
- pi or archival as stated: exoALMA Large Program images released by the exoALMA collaboration  
  > "which were CLEANed, calibrated, and made publicly available by the exoALMA collaboration" (3 Sample selection and methodology)
- External data: Substructure (gap/cavity) locations and azimuthally symmetric frank radial profile fits for the exoALMA disks  
  > "we consider as viable planet locations those of gaps and cavities identified by (cite: Curone2025ExoALMA.Emission)" (3 Sample selection and methodology) [from (cite: Curone2025ExoALMA.Emission)]
- External data: Disk geometry (deprojection parameters) fitted for each disk  
  > "We do that by linearly interpolating the observation and using the geometrical properties fitted by (cite: Curone2025ExoALMA.Emission)." (7 Appendix, Deprojection and preprocessing) [from (cite: Curone2025ExoALMA.Emission)]
- External data: Dynamical stellar masses used to convert Mp/Mstar to Mp  
  > "The conversion from $M_p/M_\star$ to $M_p$ is done using dynamical stellar masses derived by (cite: Izquierdo2025ExoALMA.Disks)." (3 Sample selection and methodology) [from (cite: Izquierdo2025ExoALMA.Disks)]
- External data: Disk dynamical masses and accretion timescales from rotation-curve modelling, used for the alpha h^2 comparison  
  > "(cite: Longarini2025ExoALMA.Modelling) modelled the rotation curves of a subsample of exoALMA targets, fitting the stellar mass, disk mass, and scale radius" (5.3 Accretion timescales) [from (cite: Longarini2025ExoALMA.Modelling)]
- External data: Midplane temperature profiles from emission surfaces, compared with inferred aspect ratios  
  > "using (cite: Galloway-Sprietsma2025ExoALMA.Structures) estimates of the midplane temperature profile to compute the expected aspect ratio" (4.3 Aspect ratios and Stokes numbers) [from (cite: Galloway-Sprietsma2025ExoALMA.Structures)]
- External data: Literature planet-mass limits and estimates (HCI/SAM upper limits, kinematic, gap-width and simulation estimates) for comparison  
  > "Non-detections in high-contrast imaging (HCI) and sparse aperture masking (SAM) observations are translated into upper limits on the planet masses." (4.1 Planet masses) [from (cite: Willson2016SparseDiscs; Reggiani2018Discovery758; Pinte2025ExoALMA.Planetsb; Stadler2025ExoALMA.Variations) and others]
- External data: Gas-to-dust mass ratios, non-axisymmetry indexes, dust and dynamical masses used in correlation tests  
  > "(cite: Curone2025ExoALMA.Emission; Longarini2025ExoALMA.Modelling; Izquierdo2025ExoALMA.Disks)" (5.5 Correlations with other disk properties) [from (cite: Curone2025ExoALMA.Emission; Longarini2025ExoALMA.Modelling; Izquierdo2025ExoALMA.Disks)]
- Simulation/model as data: DBNets2.0 training set: synthetic dust continuum observations from 2D FARGO3D hydrodynamical simulations with one embedded planet, postprocessed with the Birnstiel et al. 2018 opacity model  
  > "Hydrodynamical simulations are run with the mesh code FARGO3D" (7 Appendix, hydrodynamical simulations); "The opacity ($\kappa$) is computed using (cite: Birnstiel2018TheModel) model." (7 Appendix, Radiative transfer)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Used exoALMA-collaboration CLEANed, calibrated Band 7 continuum images  
  > "which were CLEANed, calibrated, and made publicly available by the exoALMA collaboration" (3 Sample selection and methodology)
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

- Further details of DBNets2.0 and its training data  
  > "Further details are provided in (cite: Ruzza2024DBNets:Discs; Ruzza2025DBNets2.0:Discs)." (3 Sample selection and methodology) [from (cite: Ruzza2024DBNets:Discs; Ruzza2025DBNets2.0:Discs)]
- Calibration, CLEANing and imaging of the exoALMA continuum data  
  > "which were CLEANed, calibrated, and made publicly available by the exoALMA collaboration (cite: Teague2025ExoALMA.Products; Loomis2025ExoALMA.Pipeline; Curone2025ExoALMA.Emission)" (3 Sample selection and methodology) [from (cite: Teague2025ExoALMA.Products; Loomis2025ExoALMA.Pipeline; Curone2025ExoALMA.Emission)]
- Gap versus cavity classification of substructures  
  > "We also follow (cite: Curone2025ExoALMA.Emission) characterization when distinguishing between gaps and cavities." (3 Sample selection and methodology) [from (cite: Curone2025ExoALMA.Emission)]
- Confidence-score rejection threshold of 0.6 for input data inside the training distribution  
  > "It was advised to treat with additional caution (or reject), any result with a CS less than this threshold." (2 DBNets2.0) [from Ruzza et al. DBNets2.0 paper (cite: Ruzza2025DBNets2.0:Discs)]

### Not stated but needed to reproduce (our reading)

- Trained DBNets2.0 weights and inference code (paper does not say whether or where they are released)
- Exact exoALMA Band 7 image products used (file names, robust weighting, beam, rms, pixel size) and the CASA/pipeline versions
- Per-disk inclination, position angle and distance values fed to the deprojection (taken from Curone et al. 2025 but not listed here)
- Exact input image size, pixel scale after deprojection and rescaling, and how the beam size is supplied to the network
- CNN and normalizing-flow architecture, training hyperparameters and training-set size (deferred to the earlier DBNets papers)
- How the quoted best values and uncertainties are summarized from the 10^6 posterior samples (median and which percentiles)
- Aspect-ratio profile exponent beta and surface-density slope assumed per disk (marginalized, not reported)
- Gap/cavity radii for each proposed planet (only the final R_p values are tabulated)

## Analysis recipe

1. **select images and proposed planet locations**: Use exoALMA fiducial Band 7 continuum images; choose gap and cavity locations from frank profiles of Curone et al. and the literature, excluding substructures not visible in the CLEAN radial profiles  
  > "we exclude substructures that are not visible in the azimuthally averaged radial profiles obtained from the CLEANed images" (3 Sample selection and methodology); "we consider as viable planet locations those of gaps and cavities identified by (cite: Curone2025ExoALMA.Emission)" (3 Sample selection and methodology)
   - software: frank
   - parameter: Cavity planets placed only where previous studies proposed planet signatures; J1842 cavity excluded from main results  
  > "We select the putative planet’s location based on previous studies that proposed detections of planet signatures such as direct thermal emission or kinematic perturbations" (3 Sample selection and methodology)
   - assumption: Each substructure is due to an embedded planet at the chosen fixed location  
  > "assuming these are due to embedded planets at fixed locations" (abstract)
   - fitting: _not stated_
   - validation: _not stated_
2. **deproject and preprocess the continuum images**: Deproject by linear interpolation with geometry from Curone et al., rescale to the training convention R_p = 1, crop to 0.3 R_p to 4 R_p, standardize pixel values  
  > "We do that by linearly interpolating the observation and using the geometrical properties fitted by (cite: Curone2025ExoALMA.Emission)." (7 Appendix, Deprojection and preprocessing); "is required as an additional input to rescale the observation to the training convention" (7 Appendix, Treatment of multiple substructures); "Input observations are also standardized by subtracting the mean value of their pixels and dividing by their standard deviation" (7 Appendix, Deprojection and preprocessing)
   - software: DBNets2.0
   - parameter: Input covers 0.3 R_p to 4 R_p  
  > "Each DBNets2.0 output considers, in principle, the entire observed morphology within $0.3R_p$ and $4R_p$, corresponding to the portion of the disk provided as input." (7 Appendix, Treatment of multiple substructures)
   - assumption: Results unaffected by deprojection up to 60 degrees inclination, shown on synthetic data in earlier work  
  > "results remain unaffected by deprojection effects up to a disk inclination of 60°" (7 Appendix, Deprojection and preprocessing)
   - fitting: _not stated_
   - validation: _not stated_
3. **infer posteriors with DBNets2.0**: Neural posterior estimation with CNNs and normalizing flows gives the joint posterior of alpha, h, St and Mp/Mstar for each proposed planet, treated as an independent single-planet scenario  
  > "DBNets2.0 uses convolutional neural networks (CNNs) and normalizing flows" (2 DBNets2.0); "the full joint posterior for these properties is inferred, revealing degeneracies and enabling uncertainty quantification." (1 Introduction); "we separately consider each gap as a viable planet location and independently fit our single-planet model." (7 Appendix, Treatment of multiple substructures)
   - software: DBNets2.0
   - parameter: 10^6 samples drawn from each posterior  
  > "All analyses and results presented here are based on $10^6$ samples drawn from each inferred posterior distribution." (3 Sample selection and methodology)
   - parameter: Training range (uniform priors): 1e-4<=alpha<=1e-2, 0.03<=h<=0.1, 1e-3<=St<=1e-1, 1e-5<=Mp/Mstar<=1e-2  
  > "The training set covers the parameter space region where $10^{-4}\leq\alpha\leq10^{-2}, 0.03\leq h \leq0.1, 10^{-3} \leq \text{St} \leq 10^{-1}, 10^{-5} \leq M_p/M_\star \leq 10^{-2}$." (7 Appendix, Training set parameter space); "This effectively sets uniform priors for each of these inferred properties in the respective range of values." (7 Appendix, Training set parameter space)
   - assumption: Training model: 2D locally isothermal FARGO3D simulations, one non-accreting planet on a fixed orbit, constant alpha, dust as pressureless fluid with Sc=1 and fixed Stokes number, no dust back reaction  
  > "One, non-accreting, planet is embedded in the disk and maintained on a fixed orbit." (7 Appendix, hydrodynamical simulations); "Back reaction of the dust on the gas is neglected." (7 Appendix, hydrodynamical simulations)
   - assumption: Training images use Birnstiel et al. 2018 opacity; Gaussian noise and varying Gaussian beams added during training  
  > "During training, Gaussian noise with random variance is added, and the images are convolved with Gaussian beams of varying sizes" (7 Appendix, Radiative transfer)
   - fitting: Neural posterior estimation (CNN plus normalizing flow); the posterior is conditional on the training model  
  > "all the inferred posteriors are to be understood as conditional upon it." (2 DBNets2.0)
   - validation: Confidence score between 0 and 1 compares the input image with synthetic training images at samples from the posterior; CS below 0.6 flagged as uncertain, and posteriors whose 2.5 and 97.5 percentiles leave the prior support flagged as unconstrained  
  > "that quantifies, with a value between 0 and 1, the similarity between the input continuum observation and the synthetic data within DBNets2.0 training sample" (2 DBNets2.0); "we adopt a conservative approach, considering estimates with CS $< 0.6$ as uncertain." (2 DBNets2.0); "We identify as such all estimates whose 2.5 and 97.5 percentiles (corresponding to $2\sigma$ for a Gaussian) fall outside of the respective prior support." (2 DBNets2.0)
4. **convert planet-to-star mass ratio to planet mass**: Multiply Mp/Mstar by dynamical stellar masses from Izquierdo et al.  
  > "The conversion from $M_p/M_\star$ to $M_p$ is done using dynamical stellar masses derived by (cite: Izquierdo2025ExoALMA.Disks)." (3 Sample selection and methodology)
   - fitting: _not stated_
   - validation: _not stated_
5. **compare with literature planet, viscosity, aspect ratio and Stokes estimates**: Compare Mp with HCI and SAM upper limits, kinematic and gap-width estimates; compare alpha with line-broadening turbulence; compare h with temperature-derived aspect ratios under vertical hydrostatic equilibrium; compare with the earlier DBNets2.0 sample  
  > "Figure [2](#fig:litmp) presents a comparison of our planet mass estimates with the literature." (4.1 Planet masses); "can be compared to our estimates of the disks’ aspect ratios by converting them under the assumption of vertical hydrostatic equilibrium." (4.3 Aspect ratios and Stokes numbers)
   - fitting: _not stated_
   - validation: Estimates are mostly consistent with HCI upper limits except J1604 and LkCa 15; Band 7 results agree within uncertainties with the earlier Band 6 and Band 3 DBNets2.0 results  
  > "We found our estimates to be mostly consistent with these constraints, with the only two exceptions of J1604 and LkCa15 for which we estimate higher planet masses." (4.1 Planet masses); "estimates are compatible within uncertainties, proving little dependence of these results on the Band of the observations." (5.2 Comparison with DBNets2.0 estimates)
6. **derive implications for accretion, migration, stability and correlations**: Compute local alpha h^2 and compare with accretion timescales; compute Kanagawa K and K' against migration thresholds; check Hill stability of the six two-planet systems; compute Pearson correlations with other disk properties  
  > "Conversely, with DBNets2.0, we can provide local estimates of $\alpha h^2$ obtained by modelling substructures due to planet-disk interaction" (5.3 Accretion timescales); "This is required to be greater than $2\sqrt{3}$ for the system to be stable." (5.5 Configurations of proposed multiple systems); "we computed the Pearson correlation coefficient ($\rho$)" (8 Appendix, Correlations)
   - parameter: Significance threshold p < 0.05; uncertain and unconstrained estimates removed from the correlation analysis  
  > "A p-value lower than 0.05 indicates statistical significant evidence for correlation between the two properties." (8 Appendix, Correlations); "For this analysis, we remove all estimates that we considered either unreliable or unconstrained." (8 Appendix, Correlations)
   - assumption: Self-similar disk evolution assumed for the accretion timescale relation  
  > "assuming the self-similar solution to the disk evolution" (5.3 Accretion timescales)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **DBNets2.0** : Simulation-based inference of planet mass, alpha, h and St from dust continuum images  
  > "DBNets2.0 is a simulation-based inference pipeline for rapidly fitting dust substructures, such as gaps, rings and cavities, observed in disks’ dust continuum emission." (2 DBNets2.0)
- **FARGO3D** : Hydrodynamical simulations that generate the DBNets2.0 training set  
  > "Hydrodynamical simulations are run with the mesh code FARGO3D" (7 Appendix, hydrodynamical simulations)
- **frank** : Azimuthally symmetric radial profile fits of the continuum, used (via Curone et al.) to locate gaps and cavities  
  > "through the characterization of the azimuthally symmetric `frank` (cite: Jennings2020Frankenstein:Process) fits of the disks’ continuum emission" (3 Sample selection and methodology)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of putative planets and disks with DBNets2.0 estimates | 19 planets in 13 of the 15 disks | not stated | dimensionless | 3 | we propose a population of 19 planets possibly embedded in 13 of the 15 disks targeted by the exoALMA program |
| Putative planet mass, J1604 (R_p = 41 au) | 7.91 | +1.52/-1.37 | M_J | 4 | $7.91^{+1.52}_{-1.37}$ |
| Putative planet mass, HD 34282 (R_p = 47 au) | 7.14 | +3.33/-1.76 | M_J | 4 | $7.14^{+3.33}_{-1.76}$ |
| alpha for the 72 au gap in DM Tau | 5.5e-3 | +3.1/-2.0 (x 10^-3) | dimensionless | 3 | The analysis of the gap at 72 au instead returns an estimate $\alpha=5.5^{+3.1}_{-2.0} \times 10^{-3}$ |
| log St for the 86 au gap in LkCa 15 | -1.45 | +0.12/-0.14 | dimensionless | 3 | we estimate $\log \text{St} = -1.45^{+0.12}_{-0.14}$ |
| Estimates with confidence score below 0.6 | 3 (inner gap of MWC 758, cavities of HD 135344 B and LkCa 15) | not stated | dimensionless | 3 | These are three estimates for putative planets in the inner gap of MWC 758 and in the cavities of HD 135344 B and LkCa 15. |
| Putative planets expected to migrate outward | 3 | not stated | dimensionless | 6 | most of our planets would fall into the inward migrating case, with only three objects migrating outwards. |
| Pearson correlation, stellar mass versus inferred aspect ratio | 0.60 | not stated | dimensionless | 6 | Pearson correlation coefficient of 0.60 |

## Qualitative findings

- Inferred alpha distribution has two peaks at the two ends of the prior, with more sources at low viscosity  
  > "with an higher number of sources showing evidence of low viscosity" (4 Results and comparison with literature)
- Cavities suggest more massive companions than gaps  
  > "Cavities are found to suggest the presence of more massive companions" (4 Results and comparison with literature)
- All six proposed two-planet systems would be dynamically stable and not in low-order mean-motion resonances  
  > "all these systems would be dynamically stable and are not close enough to lie in the lower-order mean-motion resonances" (5.5 Configurations of proposed multiple systems)
- Inferred planet mass depends on assumed location inside cavities and decreases as the planet nears the outer ring  
  > "the inferred planet mass decreases as the assumed planet location approaches the ring." (5.1 Dependence on assumed planet location)

## Claim tuples

- H: Do the exoALMA dust substructures, if planet-carved, imply planet masses consistent with other constraints | E: Applied DBNets2.0 to Band 7 continuum images at proposed planet locations and compared with HCI limits, kinematic and empirical estimates | R: Most estimates consistent with HCI upper limits and simulation or empirical estimates; J1604 and LkCa 15 cavity planets are more massive than previous constraints; planets in HD 34282 and J1604 are the best direct-imaging candidates | F: Most proposed planets are super-Jovian (likely selection bias) and cavities require larger masses than gaps | **supported**
- H: Can viscous transport inferred from planet-disk substructures explain observed stellar accretion rates | E: Compared local alpha h^2 from DBNets2.0 with global accretion timescales from rotation-curve modelling | R: Viscous timescales are too long for all Herbig stars; T Tauri stars show larger scatter, mostly roughly consistent | F: Additional accretion mechanisms are needed for the Herbig stars | **supported**
- H: Which migration regime do the proposed planets occupy | E: Computed Kanagawa K and K' from DBNets2.0 estimates and compared with outward-migration thresholds | R: Most planets fall in the inward-migration regime; three objects migrate outward | F: Inward migration is more frequent | **supported**
- H: Do inferred disk and planet properties correlate with other disk properties | E: Pearson correlations with gas-to-dust ratio, non-axisymmetry index, gas, dust and stellar masses | R: Only stellar mass versus aspect ratio is significant (Pearson coefficient 0.60) | F: No other remarkable trend | **supported**
- H: Do DBNets2.0 estimates depend on observing band | E: Compared Band 7 exoALMA estimates with earlier Band 6 and Band 3 DBNets2.0 estimates for overlapping objects | R: Planet masses compatible within uncertainties; alpha for DM Tau differs by more than one order of magnitude at Band 3 | F: alpha and St estimates should not be fully trusted at wavelengths far from Band 6 | **partially**

## Reasoning

- Why this data: exoALMA provides a homogeneous sample of dust continuum observations with substructures in nearly all disks  
  > "represent a rare and valuable case of a homogenous sample" (1 Introduction)
- Why this method: Machine-learning SBI combines the speed of empirical relations with the expressiveness of neural networks and uses the whole observed morphology  
  > "combining the same speed and ease of use of empirical relations with the higher expressiveness of neural networks" (1 Introduction)
- Alternative: J1842 cavity excluded from the main results because no planet-signature constraints exist; results shown as a function of assumed planet location  
  > "exclude from our main discussions the cavity of J1842, which lacks such constraints" (3 Sample selection and methodology)
- Alternative: Estimates with CS below 0.6 or unconstrained posteriors excluded from aggregated results  
  > "We exclude these points from the presentation and discussion of aggregated results" (2 DBNets2.0)
- How they decided it was enough: _not stated_
- Limitation (authors): Posteriors are conditional on the training model and cannot capture scenarios outside it  
  > "The inferred distributions cannot account for scenarios that are not included in this model." (2 DBNets2.0)
- Limitation (authors): Planet migration is not modelled because planets are held on fixed orbits  
  > "does not include planet migration, as planets are held on a fixed orbit." (5.4 Kanagawa coefficients and stalling radius)
- Limitation (authors): exoALMA sample is biased toward brighter and more extended disks  
  > "the exoALMA sample is inherently affected by selection biases, leading to an overrepresentation of brighter and more extended disks" (3 Sample selection and methodology)
- Limitation (authors): Prior upper limit alpha<=1e-2 is too constraining for DM Tau  
  > "DBNets2.0 priors are too constraining in this case" (4.2 Turbulent viscosity)
- Caveat (inferred, ours): Planet locations are chosen by hand and, for cavities, strongly drive the inferred mass; results are scenario-dependent
- Caveat (inferred, ours): Each substructure is fitted independently with a single-planet model, so multi-planet inferences rest on an untested assumption
- Caveat (inferred, ours): Training uses 2D locally isothermal simulations with a single grain size and a fixed Band 6 opacity setup, so alpha and St are model-dependent and band-sensitive
- Caveat (inferred, ours): No test that the data are better described by planets than by non-planetary substructure mechanisms

## Reproducibility

- Data public (paper): exoALMA images publicly available  
  > "made publicly available by the exoALMA collaboration" (3 Sample selection and methodology)
- Products in archive: _not stated_
- Missing: Trained DBNets2.0 model and inference code access
- Missing: Exact exoALMA image files and per-disk deprojection geometry
- Missing: Training-set generation and network details beyond the appendix summary
- Data volume (inferred): Small: 15 Band 7 continuum images (about tens of MB total) from the released exoALMA products; no visibility processing needed
- Score (inferred): 3/5, Public images, planet radii and numeric result tables are given, but the inference depends on the DBNets2.0 trained model from earlier papers and on preprocessing details not listed here.
- Rediscovery candidate: no, Recipe depends on a pretrained external tool and on inputs defined in companion papers, so it cannot be redone from this paper alone.

## Links

- Method: (cite: Ruzza2025DBNets2.0:Discs) (Defines DBNets2.0 and its training data)
- Method: (cite: Ruzza2024DBNets:Discs) (Original DBNets paper, deprojection tests)
- Method: (cite: Curone2025ExoALMA.Emission) (Continuum substructure characterization and disk geometry)
- Method: (cite: Teague2025ExoALMA.Products) (exoALMA data products)
- Companion: (cite: Longarini2025ExoALMA.Modelling) (Rotation-curve dynamical masses and accretion timescales)
- Companion: (cite: Izquierdo2025ExoALMA.Disks) (Dynamical stellar masses)
- Companion: (cite: Pinte2025ExoALMA.Planetsb) (Kinematic planet signatures)
- Companion: (cite: Galloway-Sprietsma2025ExoALMA.Structures) (Emission surfaces and temperature structure)
- Related: exoALMA
- Related: MAPS
- Related: DSHARP

## Checks

```json
{
 "quotes": 85,
 "quotes_ok": 85,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 138,
  "stated": 51,
  "rate": 0.37
 },
 "evidence_ok": true
}
```
