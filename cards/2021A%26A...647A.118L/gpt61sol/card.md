# Exploring HNC and HCN line emission as probes of the protoplanetary disk temperature

`2021A&A...647A.118L` | Astronomy and Astrophysics 2021 | first author: Long, Feng | arXiv: 2102.06338 | DOI: 10.1051/0004-6361/202039336

Card schema 1.0 | model gpt-6.1-sol | depth full | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Can HNC and HCN emission, especially their line ratio, probe disk temperature and other physical and chemical conditions?  
  > "Our goal is to investigate the HNC and HCN emission in protoplanetary disks based on our knowledge of cyanide chemistry and to explore the potential usability of HNC and HCN as tracers" (Introduction); "We investigate the HNC and HCN line emission in disks at (sub-)millimeter wavelengths and explore their potential utility for probing disk temperature and other disk properties." (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance 59.5 pc  
  > "We adopt the Gaia distance of 59.5 pc (cite: Gaia2018) and the HD-based gas disk mass of 0.06 $\rm M_{\odot}$ (cite: Bergin2013) for TW Hya." (Comparisons to literature studies); distance from Gaia (cite: Gaia2018)  
  > "We adopt the Gaia distance of 59.5 pc (cite: Gaia2018) and the HD-based gas disk mass of 0.06 $\rm M_{\odot}$ (cite: Bergin2013) for TW Hya." (Comparisons to literature studies)
- Target **HD 163296**: coordinates _not stated_; z/distance 101 pc  
  > "For HD 163296, we take a range of gas disk masses (0.048–0.31 $\rm M_{\odot}$) from CO isotopolog and HD observations (cite: Williams2014; Booth2019; Kama2020) with a distance of 101 pc (cite: Gaia2018)." (Comparisons to literature studies); distance from (cite: Gaia2018)  
  > "For HD 163296, we take a range of gas disk masses (0.048–0.31 $\rm M_{\odot}$) from CO isotopolog and HD observations (cite: Williams2014; Booth2019; Kama2020) with a distance of 101 pc (cite: Gaia2018)." (Comparisons to literature studies)
- Target **J160830.7-382827**: coordinates _not stated_; z/distance 155 pc  
  > "The transition disk J160830.7-382827 (cite: vanderMarel2018) is the brightest HNC emission source, with a peak S/N of 4.5$\sigma$." (Constraints from new HNC observations of Lupus disks); "where we take a source distance of 155 pc (cite: Gaia2018) and disk gas masses from CO observations ((cite: Ansdell2016; Miotello2017))." (Constraints from new HNC observations of Lupus disks); distance from (cite: Gaia2018)  
  > "The transition disk J160830.7-382827 (cite: vanderMarel2018) is the brightest HNC emission source, with a peak S/N of 4.5$\sigma$." (Constraints from new HNC observations of Lupus disks); "where we take a source distance of 155 pc (cite: Gaia2018) and disk gas masses from CO observations ((cite: Ansdell2016; Miotello2017))." (Constraints from new HNC observations of Lupus disks)
- Target **29 disks in Lupus**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.0156.S, 2016.1.00571.S, 2017.1.01056.S
- bands: TW Hya: Band 6; Lupus: Band 3 (3 mm)  
  > "The HNC $J=3-2$ line in the disk of TW Hya was observed with ALMA Band 6 receivers" (Comparisons to new HNC observations of TW Hya); "The ALMA Lupus disk survey at Band 3 (PI: M. Tazzari, 2016.1.00571.S) recorded the 3 mm continuum in frequency-division mode (FDM) with 3840 channels, designed for serendipitous line detections." (Constraints from new HNC observations of Lupus disks)
- frequencies and spectral setup: TW Hya HNC J=3-2: 0.15 km s^-1 channels; Lupus HNC 1-0: FDM, 3840 channels, ~3.5 km s^-1 velocity resolution  
  > "The HNC line data cube with channel widths of 0.15 km s$^{-1}$ was produced with `tclean` using Briggs weighting of robust=0.5." (Comparisons to new HNC observations of TW Hya); "recorded the 3 mm continuum in frequency-division mode (FDM) with 3840 channels, designed for serendipitous line detections." (Constraints from new HNC observations of Lupus disks); "The HNC line data cubes are created with `tclean` using natural weighting, resulting in a typical beam size of $0.48\ensuremath{''}\times0.40\ensuremath{''}$ with a velocity resolution of $\sim\rm 3.5\,km\,s^{-1}$." (Constraints from new HNC observations of Lupus disks)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: TW Hya: 15–1996 m  
  > "with a baseline range of 15–1996 m" (Comparisons to new HNC observations of TW Hya)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Lupus: 2–3 min  
  > "With 2–3 min on-source time, we reach a 1$\sigma$ noise level of 2–3 mJy beam$^{-1}$ per $\rm 3.5\,km\,s^{-1}$ channel." (Constraints from new HNC observations of Lupus disks)
- observing dates: TW Hya: September 30, 2018  
  > "on September 30, 2018" (Comparisons to new HNC observations of TW Hya)
- pi or archival as stated: TW Hya PI: V. Guzman; Lupus PI: M. Tazzari  
  > "(PI: V. Guzman, 2017.1.0156.S)" (Comparisons to new HNC observations of TW Hya); "(PI: M. Tazzari, 2016.1.00571.S)" (Constraints from new HNC observations of Lupus disks)
- Line: HNC J=3-2 (not stated)
- Line: HNC J=1-0 (not stated)
- Line: HCN J=1-0 and J=3-2 (models) (not stated)
- Line: HNC J=2-1 and J=4-3 (models) (not stated)
- Other facility **SMA**: Spatially resolved HNC 3-2 observations of TW Hya and HD 163296; disk-integrated fluxes and ring-like morphology  
  > "The first spatially resolved observations of HNC $3-2$ lines were performed toward TW Hya and HD 163296 with the SMA (cite: Graninger2015)." (Comparisons to literature studies); "The SMA observations with arcsec resolution also indicate ring-like emission for the HNC $3-2$ lines for both disks (cite: Graninger2015)." (Comparisons to literature studies)
- Other facility **IRAM 30m**: Literature disk-averaged HNC-to-HCN line ratios, together with SMA observations  
  > "Available SMA and IRAM 30m observations provide the disk-averaged HNC-to-HCN line ratio of 0.1–0.2" (Comparisons to literature studies); "an upper limit of 0.3 for the $1-0$ transition in HD 163296 (cite: Graninger2015)." (Comparisons to literature studies)
- Other facility **Gaia**: Adopted source distances  
  > "We adopt the Gaia distance of 59.5 pc (cite: Gaia2018)" (Comparisons to literature studies); "with a distance of 101 pc (cite: Gaia2018)." (Comparisons to literature studies); "where we take a source distance of 155 pc (cite: Gaia2018)" (Constraints from new HNC observations of Lupus disks)
- External data: HCN disk-averaged column densities: (1–10)×10^12 cm^-2  
  > "Low- to medium-resolution observations found the disk-averaged column densities for HCN lines to be in the range of (1–10)$\times10^{12}\,\rm cm^{-2}$ for a sample of disks around T Tauri and Herbig Ae stars (cite: Chapillon2012; Bergner2019)." (Comparisons to literature studies) [from (cite: Chapillon2012; Bergner2019)]
- External data: MAPS HCN column densities up to 10^15 cm^-2 in the inner 100 au; optical depths >10  
  > "the HCN column densities can reach 10$^{15}\,\rm cm^{-2}$ in the inner 100 au of disks" (Comparisons to literature studies); "the ALMA Large Program (MAPS, V. Guzman, J. Bergner, and G. Cataldi, private communication), which leads to high optical depths of $>$10." (Comparisons to literature studies) [from MAPS, V. Guzman, J. Bergner, and G. Cataldi, private communication]
- External data: SMA HNC 3-2 observations, integrated fluxes and ring-like emission of TW Hya and HD 163296  
  > "The first spatially resolved observations of HNC $3-2$ lines were performed toward TW Hya and HD 163296 with the SMA (cite: Graninger2015)." (Comparisons to literature studies); "the distance-scaled disk-integrated line fluxes are consistent with our model predictions for both disks." (Comparisons to literature studies) [from (cite: Graninger2015)]
- External data: HNC-to-HCN ratios: 0.1–0.2 for 3-2 in TW Hya and HD 163296; 1-0 upper limit 0.3 in HD 163296  
  > "Available SMA and IRAM 30m observations provide the disk-averaged HNC-to-HCN line ratio of 0.1–0.2 for the $3-2$ transition in TW Hya and HD 163296" (Comparisons to literature studies); "an upper limit of 0.3 for the $1-0$ transition in HD 163296 (cite: Graninger2015)." (Comparisons to literature studies) [from (cite: Graninger2015)]
- External data: Distances: TW Hya 59.5 pc; HD 163296 101 pc; J160830.7-382827 155 pc  
  > "We adopt the Gaia distance of 59.5 pc (cite: Gaia2018)" (Comparisons to literature studies); "with a distance of 101 pc (cite: Gaia2018)." (Comparisons to literature studies); "where we take a source distance of 155 pc (cite: Gaia2018)" (Constraints from new HNC observations of Lupus disks) [from (cite: Gaia2018)]
- External data: TW Hya HD-based gas disk mass: 0.06 M_sun  
  > "the HD-based gas disk mass of 0.06 $\rm M_{\odot}$ (cite: Bergin2013) for TW Hya." (Comparisons to literature studies) [from (cite: Bergin2013)]
- External data: HD 163296 gas disk masses: 0.048–0.31 M_sun, from CO isotopolog and HD observations  
  > "For HD 163296, we take a range of gas disk masses (0.048–0.31 $\rm M_{\odot}$) from CO isotopolog and HD observations (cite: Williams2014; Booth2019; Kama2020)" (Comparisons to literature studies) [from (cite: Williams2014; Booth2019; Kama2020)]
- External data: J160830.7-382827 and Lupus CO-based gas disk masses  
  > "where we take a source distance of 155 pc (cite: Gaia2018) and disk gas masses from CO observations ((cite: Ansdell2016; Miotello2017))." (Constraints from new HNC observations of Lupus disks); "the typical gas disk mass range in the Lupus sample (cite: Ansdell2016)." (Constraints from new HNC observations of Lupus disks) [from (cite: Ansdell2016; Miotello2017)]
- External data: Lupus CO gas disk sizes: 70 to ~500 au, mostly smaller than 300 au  
  > "The measured CO gas disk sizes for a sample of Lupus disks span from 70 to $\sim$500 au and are mostly smaller than 300 au (cite: Ansdell2018)." (Constraints from new HNC observations of Lupus disks) [from (cite: Ansdell2018)]
- External data: Lupus CN observations: J160830.7-382827 brightest; a fraction of disks compact, consistent with R_c=15 au models  
  > "This is incidentally also the brightest CN emission source in the sample (cite: vanTerwisga2019)." (Constraints from new HNC observations of Lupus disks); "The CN observations also reveal that a fraction of Lupus disks are compact, consistent with models with a characteristic radius $R_c$=15 au (cite: vanTerwisga2019)." (Constraints from new HNC observations of Lupus disks) [from (cite: vanTerwisga2019)]
- External data: TW Hya inner disk cavity within 1 au; bright C2H indicating strong UV and high C/O  
  > "However, TW Hya is known to host an inner disk cavity within 1 au (cite: Andrews2016)." (Comparisons to new HNC observations of TW Hya); "Its bright C$_{2}$H emission also suggests a strong UV field and a high C/O in the disk (cite: Bergin2016)." (Comparisons to new HNC observations of TW Hya) [from (cite: Andrews2016); (cite: Bergin2016)]
- External data: J160830.7-382827 transition-disk classification  
  > "The transition disk J160830.7-382827 (cite: vanderMarel2018)" (Constraints from new HNC observations of Lupus disks) [from (cite: vanderMarel2018)]
- External data: Binding energies: CN 1600 K; HNC and HCN 2050 K  
  > "We used binding energies to grains of 1600 K for CN and 2050 K for HNC and HCN, based on the values from the Kinetic Database for Astrochemistry (KIDA; (cite: Wakelam2012))." (Chemical network) [from Kinetic Database for Astrochemistry (KIDA; (cite: Wakelam2012))]
- External data: Reduced CNO chemical network  
  > "Our models used the new reduced network presented in (cite: Visser2018) for CNO chemistry, which is based on the network of (cite: Bruderer2012) and includes the reactions for cyanides discussed in (cite: Loison2014)." (Chemical network) [from (cite: Visser2018); (cite: Bruderer2012); (cite: Loison2014)]
- External data: Empirical ISM HNC-to-HCN ratio–gas kinetic temperature relation used for comparison  
  > "(cite: Hacar2020) carried out a dedicated investigation of the HNC-to-HCN ratio in the integral shape filament of Orion and established a strong correlation between the HNC-to-HCN line ratio and the gas kinetic temperature" (HNC-to-HCN intensity ratio as a disk thermometer?) [from (cite: Hacar2020)]
- Simulation/model as data: DALI 2D thermochemical disk models: radiative transfer, chemistry, thermal balance and ray-tracing  
  > "we employed the 2D thermochemical code DALI ((cite: Bruderer2012; Bruderer2013))" (Physical and chemical models); "This code includes calculations of radiative transfer, chemistry, thermal balance, and ray-tracing." (Physical and chemical models)
- Simulation/model as data: Grid varying disk mass, vertical height and flaring for T Tauri and Herbig stars  
  > "A small grid of models was performed by varying disk mass, disk vertical height, and flaring for the T Tauri and Herbig models to represent a wide range of physical and chemical conditions." (Physical framework)
- Simulation/model as data: Additional models varying accretion rate, C and O abundances, C/O and characteristic radius  
  > "we ran a set of additional models with different accretion rates ($10^{-7}, 10^{-9},$ and $10^{-10}\,\rm M_{\odot}\,yr^{-1}$" (Dependence of line fluxes on disk parameters); "we performed three additional carbon- and oxygen-depleted models" (Dependence on varying the C and O elemental abundances); "we ran additional models with $R_{c}=$15 and 30 au, keeping the inner disk surface density profile identical" (Emission dependence on varying disk parameters)

## Processing

### Calibration

- pipeline or manual: TW Hya: raw visibilities pipeline-calibrated; Lupus calibration details in (cite: Tazzari2020)  
  > "The raw visibilities were first pipeline-calibrated with the required `CASA` version 5.1.1" (Comparisons to new HNC observations of TW Hya); "The observation and data calibration details are described in (cite: Tazzari2020)." (Constraints from new HNC observations of Lupus disks)
- casa version: TW Hya: 5.1.1  
  > "The raw visibilities were first pipeline-calibrated with the required `CASA` version 5.1.1" (Comparisons to new HNC observations of TW Hya)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean for TW Hya and Lupus HNC line cubes  
  > "The HNC line data cube with channel widths of 0.15 km s$^{-1}$ was produced with `tclean` using Briggs weighting of robust=0.5." (Comparisons to new HNC observations of TW Hya); "The HNC line data cubes are created with `tclean` using natural weighting" (Constraints from new HNC observations of Lupus disks)
- deconvolver: _not stated_
- weighting robust: TW Hya: Briggs, robust=0.5; Lupus: natural  
  > "using Briggs weighting of robust=0.5." (Comparisons to new HNC observations of TW Hya); "The HNC line data cubes are created with `tclean` using natural weighting" (Constraints from new HNC observations of Lupus disks)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: TW Hya: CASA uvcontsub  
  > "then continuum-subtracted with `CASA` task `uvcontsub`." (Comparisons to new HNC observations of TW Hya)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: TW Hya: 0.25''×0.20''; Lupus typical: 0.48''×0.40''  
  > "This returned a beam size of $0.25\ensuremath{''}\times0.20\ensuremath{''}$" (Comparisons to new HNC observations of TW Hya); "resulting in a typical beam size of $0.48\ensuremath{''}\times0.40\ensuremath{''}$" (Constraints from new HNC observations of Lupus disks)
- final rms: TW Hya: 3.5 mJy beam^-1 per 0.15 km s^-1 channel; Lupus: 2–3 mJy beam^-1 per 3.5 km s^-1 channel, 1σ  
  > "a 1$\sigma$ noise level of 3.5 mJy beam$^{-1}$ per velocity channel." (Comparisons to new HNC observations of TW Hya); "The HNC line data cube with channel widths of 0.15 km s$^{-1}$" (Comparisons to new HNC observations of TW Hya); "With 2–3 min on-source time, we reach a 1$\sigma$ noise level of 2–3 mJy beam$^{-1}$ per $\rm 3.5\,km\,s^{-1}$ channel." (Constraints from new HNC observations of Lupus disks)

### Inherited from earlier work

- Viscous evolving accretion-disk gas surface density profile  
  > "We adopt the gas surface density profile as for a viscous evolving accretion disk (viscosity $\nu \propto R^{\gamma}$, (cite: Lynden-Bell1974; Hartmann1998))" (Physical framework) [from (cite: Lynden-Bell1974; Hartmann1998)]
- Surface-density power-law index γ=1, constant with time  
  > "The power-law index $\gamma$ is taken as 1 (cite: Hughes2008; Andrews2011) and assumed to not change with time." (Physical framework) [from (cite: Hughes2008; Andrews2011)]
- Two dust-grain populations  
  > "we consider two populations of grains, following (cite: DAlessio2006)" (Physical framework) [from (cite: DAlessio2006)]
- Default T Tauri accretion rate: 10^-8 M_sun yr^-1  
  > "We took the typical accretion rate for young T Tauri stars of $10^{-8}\,\rm M_{\odot}\,yr^{-1}$ (cite: Hartmann2016; Manara2016) as the default in our model" (Physical framework) [from (cite: Hartmann2016; Manara2016)]
- Interstellar UV field G_0 definition  
  > "We set an interstellar UV flux of $G_0$, as defined in (cite: Draine1978)" (Physical framework) [from (cite: Draine1978)]
- Reduced CNO network based on Bruderer2012, including Loison2014 cyanide reactions  
  > "Our models used the new reduced network presented in (cite: Visser2018) for CNO chemistry, which is based on the network of (cite: Bruderer2012) and includes the reactions for cyanides discussed in (cite: Loison2014)." (Chemical network) [from (cite: Visser2018); (cite: Bruderer2012); (cite: Loison2014)]
- CN disk chemical model, with two HNC-destruction changes  
  > "The entire chemical model is the same as was used for the investigation of CN emission in disks (cite: Cazzoletti2018), except for two changes made relating to the destruction of HNC" (Chemical network) [from (cite: Cazzoletti2018)]
- Updated HNC+H reaction rate coefficient; 200 K energy barrier  
  > "we used an updated reaction rate coefficient of HNC+H based on (cite: Graninger2014) with an energy barrier of 200 K" (Chemical network) [from (cite: Graninger2014)]
- HNC+O destruction reaction; 20 K energy barrier  
  > "we included the reaction of HNC+O with an energy barrier of 20 K based on the recent study of the HNC-to-HCN ratio in molecular clouds by (cite: Hacar2020)." (Chemical network) [from (cite: Hacar2020)]
- Detailed gas-phase and grain-surface chemical processes  
  > "The details of these processes are elaborated in (cite: Bruderer2012) and (cite: Visser2018)." (Chemical network) [from (cite: Bruderer2012); (cite: Visser2018)]
- CN, HNC and HCN grain binding energies from KIDA  
  > "We used binding energies to grains of 1600 K for CN and 2050 K for HNC and HCN, based on the values from the Kinetic Database for Astrochemistry (KIDA; (cite: Wakelam2012))." (Chemical network) [from KIDA; (cite: Wakelam2012)]
- Lupus observation and data-calibration details  
  > "The observation and data calibration details are described in (cite: Tazzari2020)." (Constraints from new HNC observations of Lupus disks) [from (cite: Tazzari2020)]
- Smaller-R_c models keep the inner disk surface density profile identical  
  > "we ran additional models with $R_{c}=$15 and 30 au, keeping the inner disk surface density profile identical (see Figure B.1 in (cite: Cazzoletti2018))." (Emission dependence on varying disk parameters) [from (cite: Cazzoletti2018)]

### Not stated but needed to reproduce (our reading)

- Resolve the TW Hya project-code discrepancy: 2017.1.0156.S in the observation section versus 2017.1.01056.S in the acknowledgements.
- TW Hya uvcontsub line-free channels, fit order and spectral-window selections.
- tclean cell size, image size, deconvolver, cleaning mask, threshold and iteration limits for both datasets.
- Whether primary-beam correction or self-calibration was applied.
- TW Hya deprojection inclination, position angle, disk center, radial bins and profile uncertainty calculation.
- Lupus sample identities, integration apertures and individual cube alignment details.
- Stacking weights, spatial and velocity registration, beam handling and upper-limit calculation for the 28 disks.
- DALI version, executable inputs, spatial grid, disk boundaries, dust opacity inputs and convergence tolerances.
- Complete numerical chemical network, reaction-rate coefficients and molecular excitation data.
- Exact disk-integrated model-flux extraction and distance-scaling procedure.

## Analysis recipe

1. **Measure TW Hya HNC morphology**: Create a moment-zero map and deprojected azimuthally averaged radial profile from the HNC cube  
  > "The moment-zero map of the HNC emission and the deprojected azimuthally averaged radial profile, which are created including only pixels above 3$\sigma$ from the velocity range of 1.9–4 km s$^{-1}$" (Comparisons to new HNC observations of TW Hya)
   - parameter: Pixels above 3σ; velocity range 1.9–4 km s^-1  
  > "including only pixels above 3$\sigma$ from the velocity range of 1.9–4 km s$^{-1}$" (Comparisons to new HNC observations of TW Hya)
   - fitting: _not stated_
   - validation: Compare morphology and radial profile with model predictions; short-spacing limitation requires future confirmation of the central component  
  > "This double-ring morphology with the brighter ring at closer radius is consistent with our model predictions" (Comparisons to new HNC observations of TW Hya); "The data presented here lack the short-spacing baselines that might affect the radial profile, thus future observations are needed to confirm the presence of this central component." (Comparisons to new HNC observations of TW Hya)
2. **Search for HNC in individual Lupus disks**: Integrate HNC 1-0 channels into moment-zero maps and estimate noise in signal-free zones  
  > "To attempt to detect the HNC $1-0$ line, we generated moment-zero maps by integrating over 1–8 $\rm km\,s^{-1}$ channels and estimated the noise level from the signal-free zones." (Constraints from new HNC observations of Lupus disks)
   - parameter: Velocity integration: 1–8 km s^-1  
  > "integrating over 1–8 $\rm km\,s^{-1}$ channels" (Constraints from new HNC observations of Lupus disks)
   - fitting: _not stated_
   - validation: Noise estimated from signal-free zones; brightest source peak S/N 4.5σ  
  > "estimated the noise level from the signal-free zones." (Constraints from new HNC observations of Lupus disks); "The transition disk J160830.7-382827 (cite: vanderMarel2018) is the brightest HNC emission source, with a peak S/N of 4.5$\sigma$." (Constraints from new HNC observations of Lupus disks)
3. **Constrain the remaining Lupus disks**: Stack images of the remaining 28 disks and obtain a disk-integrated upper limit  
  > "We created the stacked image for the remaining 28 disks and obtained a disk-integrated 3$\sigma$ upper limit of $\sim$10 mJy km s$^{-1}$" (Constraints from new HNC observations of Lupus disks)
   - parameter: 28 disks; 3σ disk-integrated upper limit  
  > "We created the stacked image for the remaining 28 disks and obtained a disk-integrated 3$\sigma$ upper limit" (Constraints from new HNC observations of Lupus disks)
   - fitting: _not stated_
   - validation: Compare with model predictions in the typical Lupus gas disk mass range  
  > "which agrees with our models in the typical gas disk mass range in the Lupus sample (cite: Ansdell2016)." (Constraints from new HNC observations of Lupus disks)
4. **Construct physical disk models**: Specify viscous gas surface density, Gaussian vertical density, two dust populations and stellar radiation; vary mass, vertical height and flaring  
  > "We adopt the gas surface density profile as for a viscous evolving accretion disk" (Physical framework); "The gas density in the vertical direction follows a Gaussian distribution, with a scale-height angle of $h=h_{c}(R/R_{c})^{\psi}$." (Physical framework); "A small grid of models was performed by varying disk mass, disk vertical height, and flaring for the T Tauri and Herbig models" (Physical framework)
   - software: DALI
   - parameter: γ=1; ψ=0.1, 0.2, 0.3; h_c=0.1, 0.2 rad; R_c=60 au  
  > "| $\gamma$ | 1 |
| $\psi$ | 0.1, 0.2, 0.3 |
| $h_{\rm c}$ | 0.1, 0.2 rad |
| $R_{\rm c}$ | 60 au |" (Table 1)
   - parameter: M_gas=10^-5, 10^-4, 10^-3, 10^-2, 10^-1 M_sun  
  > "| $M_{\rm gas}$ | $10^{-5} , 10^{-4} , 10^{-3}, 10^{-2}, 10^{-1} M_\odot$ |" (Table 1)
   - parameter: T Tauri: T_eff=4000 K, L_*=1 L_sun; Herbig Ae: T_eff=10000 K, L_*=10 L_sun  
  > "a T Tauri star with $T_{\rm eff}$=4000 K and $L_\ast$=1 $L_\odot$, and a Herbig Ae star with $T_{\rm eff}$=10000 K and $L_\ast$=10 $L_\odot$" (Physical framework)
   - parameter: Accretion UV: 10000 K blackbody onto a 1 M_sun, 1.5 R_sun star; default accretion rate 10^-8 M_sun yr^-1  
  > "modeled as a blackbody emitting at 10000 K on to a 1$M_{\odot}$ and 1.5$R_{\odot}$ star" (Physical framework); "We took the typical accretion rate for young T Tauri stars of $10^{-8}\,\rm M_{\odot}\,yr^{-1}$ (cite: Hartmann2016; Manara2016) as the default in our model" (Physical framework)
   - parameter: Fiducial: 10^-2 M_sun, ψ=0.2, h_c=0.1, T Tauri star  
  > "the fiducial model, which is a $10^{-2}\,\rm M_{\ensuremath{\odot}}$ disk with $\psi$=0.2, $h_c$=0.1 orbiting a T Tauri star." (Results)
   - assumption: Gas-to-dust ratio 100  
  > "The dust surface density is scaled from the gas surface density assuming a typical gas-to-dust ratio of 100." (Physical framework)
   - assumption: Small grains 0.005–1 μm at gas scale height; large grains 1–1000 μm at χh, χ=0.2; f_large=0.99  
  > "a small-grain population (0.005-1 $\mu$m) with the same scale height $h$ as the gas" (Physical framework); "a large-grain population (1-1000 $\mu$m) with a reduced scale height of ${\chi}h$, where ${\chi}=0.2$." (Physical framework); "We took $f_{\rm large}=0.99$ in our models because large grains dominate the dust mass budget." (Physical framework)
   - assumption: External UV G_0≈2.7×10^-3 erg s^-1 cm^-2 between 6 and 13.6 eV; cosmic-ray ionization 5×10^-17 s^-1 per H2  
  > "of $\rm \sim2.7\times10^{-3}\,erg\,s^{-1}\,cm^{-2}$ between 6 and 13.6 eV range, and a cosmic-ray ionization rate of $\rm 5\times10^{-17}\,s^{-1}$ per $\rm H_2$." (Physical framework)
   - assumption: X-rays: thermal radiation at 7×10^7 K, 1–100 keV, luminosity 10^30 erg s^-1; same prescription for T Tauri and Herbig models  
  > "The X-ray spectrum was taken as thermal radiation at $7\times10^7$ K between 1 and 100 keV, with the X-ray luminosity of 10$^{30}$ erg s$^{-1}$." (Physical framework); "The same prescription was used for the T Tauri and Herbig models." (Physical framework)
   - fitting: _not stated_
   - validation: Varying f_large between 0.9 and 0.99 produced no significant cyanide line-emission differences  
  > "We have tested models in which we varied the $f_{\rm large}$ parameter between 0.9 and 0.99, but found no significant differences in line emission of cyanides (cite: Cazzoletti2018)." (Physical framework)
5. **Solve chemistry and thermal structure**: Monte Carlo dust radiative transfer; chemical abundances and non-LTE excitation; iterate heating–cooling balance to self-consistent gas temperature  
  > "DALI first solves the dust continuum radiative transfer based on a Monte Carlo method to obtain the local UV flux and dust temperature" (Physical and chemical models); "the abundances for chemical species are calculated with a chemical network simulation and are then fed into the non-LTE excitation calculation" (Physical and chemical models); "the final $T_{\rm gas}$ is obtained by iterating the above steps until a self-consistent solution is reached." (Physical and chemical models)
   - software: DALI, KIDA
   - parameter: Initial [C]/[H]=1×10^-4; [O]/[H]=3.5×10^-4; [N]/[H]=1.6×10^-5  
  > "| $\rm [C]/[H]$ | 1$\times 10^{-4}$ |
| $\rm [O]/[H]$ | 3.5$\times 10^{-4}$ |
| $\rm [N]/[H]$ | 1.6$\times 10^{-5}$ |" (Table 1)
   - parameter: HNC+H barrier 200 K; HNC+O barrier 20 K  
  > "we used an updated reaction rate coefficient of HNC+H based on (cite: Graninger2014) with an energy barrier of 200 K" (Chemical network); "we included the reaction of HNC+O with an energy barrier of 20 K" (Chemical network)
   - parameter: Grain binding energies: CN 1600 K; HNC and HCN 2050 K  
  > "We used binding energies to grains of 1600 K for CN and 2050 K for HNC and HCN" (Chemical network)
   - assumption: Steady-state chemistry with initial ISM CNO abundances and ISM C/O  
  > "The chemistry was run in steady-state mode with initial ISM abundances for CNO" (Chemical network); "thus with the ISM C/O." (Chemical network)
   - assumption: No isotopolog reactions; identical HCN and HNC photodissociation rates  
  > "Reactions involving isotopologs were not considered." (Chemical network); "The same photodissociation rate was used for HCN and HNC" (Chemical network)
   - assumption: Chemical model inherited from Cazzoletti2018 except the two HNC-destruction changes  
  > "The entire chemical model is the same as was used for the investigation of CN emission in disks (cite: Cazzoletti2018), except for two changes made relating to the destruction of HNC" (Chemical network)
   - fitting: _not stated_
   - validation: Iterate to self-consistency; updated network has negligible effects on CN emission  
  > "the final $T_{\rm gas}$ is obtained by iterating the above steps until a self-consistent solution is reached." (Physical and chemical models); "The updated network has negligible effects on the CN emission." (Chemical network)
6. **Generate synthetic line observables**: Ray-trace spectral line emission; convolve integrated maps; extract intensity profiles, HNC-to-HCN ratios and integrated fluxes  
  > "For a given temperature structure and abundance profile, spectral line emission is obtained through ray-tracing." (Emission morphology); "the velocity-integrated intensity maps for HNC and HCN at the two transitions from our fiducial model, convolved with a $0.2\ensuremath{''}$ Gaussian beam." (Emission morphology); "the predicted radial profiles of HNC-to-HCN line ratio using the intensity profile cuts from the model images." (Emission morphology)
   - software: DALI
   - parameter: HNC and HCN J=1-0 and J=3-2; 0.2'' Gaussian beam  
  > "In this work, we focus on rotational transitions of $J=1-0$ and $J=3-2$ for HNC and HCN" (Emission morphology); "convolved with a $0.2\ensuremath{''}$ Gaussian beam." (Emission morphology)
   - assumption: Face-on disk, inclination 0°, distance 150 pc  
  > "The disk is set to be face-on (inclination of 0$\ensuremath{^\circ}$) and placed at a distance of 150 pc." (Emission morphology)
   - fitting: _not stated_
   - validation: Compare intensity rings with column-density peaks and emitting-region density and excitation  
  > "The predicted ring-like emission patterns, seen clearly in radial intensity profiles, are consistent with the column density profiles in which peaks of column densities are located off-center" (Emission morphology); "We find that the excitation temperature for the $1-0$ line in our model is $\sim50\%$ of the gas temperature." (Excitation and column density)
7. **Test sensitivity to disk conditions**: Compare model line fluxes, profiles, column densities and ratios across physical, radiation and elemental-abundance variations  
  > "explore the dependences of line fluxes on key disk properties." (Dependence of line fluxes on disk parameters); "we performed three additional carbon- and oxygen-depleted models" (Dependence on varying the C and O elemental abundances); "We investigated how the HNC line emission varies with different disk sizes, characterized by $R_{c}$ in our models." (Emission dependence on varying disk parameters)
   - software: DALI
   - parameter: Additional accretion rates: 10^-7, 10^-9, 10^-10 M_sun yr^-1  
  > "we ran a set of additional models with different accretion rates ($10^{-7}, 10^{-9},$ and $10^{-10}\,\rm M_{\odot}\,yr^{-1}$" (Dependence of line fluxes on disk parameters)
   - parameter: C and O depleted by factors 10 and 100; third model adds oxygen depletion to C/O=1.5  
  > "The initial overall abundances of carbon and oxygen were depleted by a factor of 10" (Dependence on varying the C and O elemental abundances); "abundances of carbon and oxygen were depleted by a factor of 100" (Dependence on varying the C and O elemental abundances); "under the condition of model (2), oxygen was further depleted to reach a C/O=1.5, all with respect to the fiducial model." (Dependence on varying the C and O elemental abundances)
   - parameter: Additional characteristic radii R_c=15 and 30 au  
  > "we ran additional models with $R_{c}=$15 and 30 au, keeping the inner disk surface density profile identical" (Emission dependence on varying disk parameters)
   - assumption: Nitrogen abundance unchanged in depletion models  
  > "The nitrogen abundance was kept the same as in the original model." (Dependence on varying the C and O elemental abundances)
   - assumption: Inner disk surface density profile unchanged in smaller-R_c models  
  > "keeping the inner disk surface density profile identical" (Emission dependence on varying disk parameters)
   - fitting: _not stated_
   - validation: Check whether outward-increasing line ratios persist with high C/O and elemental depletion  
  > "The simulated HNC-to-HCN line ratio generally increases outward, which is consistent with the preferential destruction of HNC in warmer regions." (Summary); "This conclusion is robust even for high C and O depletions and C/O$>$1." (Summary)
8. **Compare models with observed disks**: Compare distance-scaled literature fluxes, ratios and column densities, TW Hya radial morphology and Lupus detection and stacked upper limit with models  
  > "the distance-scaled disk-integrated line fluxes are consistent with our model predictions for both disks." (Comparisons to literature studies); "we overplot the radial profile from a model with a smaller characteristic radius $R_{c}=30$ au (with an otherwise identical parameter setup as the fiducial model) to guide the comparison." (Comparisons to new HNC observations of TW Hya); "The line fluxes and line ratios from literature HNC observations and the upper limit from new ALMA observations for Lupus disks are consistent with our model predictions." (Summary)
   - parameter: TW Hya profile comparison: R_c=30 au, otherwise fiducial parameters  
  > "a model with a smaller characteristic radius $R_{c}=30$ au (with an otherwise identical parameter setup as the fiducial model)" (Comparisons to new HNC observations of TW Hya)
   - assumption: Literature distances and gas disk masses adopted for observational comparisons  
  > "We adopt the Gaia distance of 59.5 pc (cite: Gaia2018) and the HD-based gas disk mass of 0.06 $\rm M_{\odot}$ (cite: Bergin2013) for TW Hya." (Comparisons to literature studies); "For HD 163296, we take a range of gas disk masses (0.048–0.31 $\rm M_{\odot}$) from CO isotopolog and HD observations (cite: Williams2014; Booth2019; Kama2020) with a distance of 101 pc (cite: Gaia2018)." (Comparisons to literature studies); "where we take a source distance of 155 pc (cite: Gaia2018) and disk gas masses from CO observations ((cite: Ansdell2016; Miotello2017))." (Constraints from new HNC observations of Lupus disks)
   - fitting: _not stated_
   - validation: Broad agreement for literature fluxes, TW Hya rings and Lupus stack; J160830.7-382827 is brighter than the full-disk prediction  
  > "This double-ring morphology with the brighter ring at closer radius is consistent with our model predictions" (Comparisons to new HNC observations of TW Hya); "Its HNC $1-0$ flux is one order of magnitude above our model prediction" (Constraints from new HNC observations of Lupus disks); "which agrees with our models in the typical gas disk mass range in the Lupus sample (cite: Ansdell2016)." (Constraints from new HNC observations of Lupus disks)
9. **Assess the temperature diagnostic**: Compare local abundance ratios with gas temperature and inspect vertical chemical abundance cuts to identify non-temperature controls  
  > "the extracted HNC-to-HCN abundance ratio and gas temperature at each position of the disk for all disk models with the mass of 0.01 M$_{\odot}$." (Emission morphology); "we examined the abundance vertical cuts at 300 au for species involved in HNC/HCN formation and destruction" (HNC-to-HCN intensity ratio as a disk thermometer?)
   - parameter: Temperature–ratio comparison: 0.01 M_sun disk models; radii outside 10 au; vertical diagnostic at 300 au  
  > "for all disk models with the mass of 0.01 M$_{\odot}$." (Emission morphology); "We focus on disk radii outside of 10 au where most of HNC and HCN millimeter emission originates." (Emission morphology); "we examined the abundance vertical cuts at 300 au" (HNC-to-HCN intensity ratio as a disk thermometer?)
   - assumption: Similar HNC and HCN photodissociation cross sections  
  > "Because similar photodissociation cross sections are assumed in the model for the two molecules" (HNC-to-HCN intensity ratio as a disk thermometer?)
   - fitting: _not stated_
   - validation: Examine UV penetration and C/O-depletion models; compare with the empirical ISM temperature relation  
  > "the ratio also strongly depends on other parameters, including UV penetration and initial C and O abundances." (HNC-to-HCN intensity ratio as a disk thermometer?); "(cite: Hacar2020) carried out a dedicated investigation of the HNC-to-HCN ratio in the integral shape filament of Orion and established a strong correlation between the HNC-to-HCN line ratio and the gas kinetic temperature" (HNC-to-HCN intensity ratio as a disk thermometer?)

## Software

- **DALI** : 2D thermochemical disk modeling: radiative transfer, chemistry, thermal balance, non-LTE excitation and ray-tracing  
  > "we employed the 2D thermochemical code DALI ((cite: Bruderer2012; Bruderer2013))" (Physical and chemical models); "This code includes calculations of radiative transfer, chemistry, thermal balance, and ray-tracing." (Physical and chemical models); "the abundances for chemical species are calculated with a chemical network simulation and are then fed into the non-LTE excitation calculation" (Physical and chemical models)
- **CASA** 5.1.1: TW Hya pipeline calibration and continuum subtraction  
  > "The raw visibilities were first pipeline-calibrated with the required `CASA` version 5.1.1 and then continuum-subtracted with `CASA` task `uvcontsub`." (Comparisons to new HNC observations of TW Hya)
- **uvcontsub** : TW Hya continuum subtraction  
  > "then continuum-subtracted with `CASA` task `uvcontsub`." (Comparisons to new HNC observations of TW Hya)
- **tclean** : TW Hya and Lupus HNC line-cube imaging  
  > "The HNC line data cube with channel widths of 0.15 km s$^{-1}$ was produced with `tclean` using Briggs weighting of robust=0.5." (Comparisons to new HNC observations of TW Hya); "The HNC line data cubes are created with `tclean` using natural weighting" (Constraints from new HNC observations of Lupus disks)
- **Kinetic Database for Astrochemistry (KIDA)** : Source of CN, HNC and HCN grain binding energies  
  > "We used binding energies to grains of 1600 K for CN and 2050 K for HNC and HCN, based on the values from the Kinetic Database for Astrochemistry (KIDA; (cite: Wakelam2012))." (Chemical network)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| TW Hya bright HNC 3-2 ring radius | 0.3 | not stated | arcsec | 1 | The line emission in TW Hya exhibits a central component, a bright ring around 0.3$''$, and a weaker bump around 1.0$''$. |
| TW Hya weaker HNC 3-2 bump radius | 1.0 | not stated | arcsec | 1 | The line emission in TW Hya exhibits a central component, a bright ring around 0.3$''$, and a weaker bump around 1.0$''$. |
| J160830.7-382827 HNC 1-0 peak S/N | 4.5 | not stated | dimensionless | 2 | The transition disk J160830.7-382827 (cite: vanderMarel2018) is the brightest HNC emission source, with a peak S/N of 4.5$\sigma$. |
| Stacked HNC 1-0 disk-integrated flux upper limit, remaining 28 Lupus disks | ~10 | 3σ upper limit | mJy km s^-1 | 3 | We created the stacked image for the remaining 28 disks and obtained a disk-integrated 3$\sigma$ upper limit of $\sim$10 mJy km s$^{-1}$ |
| Fiducial-model HNC 3-2 emission peak radius | 100 | not stated | au | 6 | For HNC lines, emission peaks at 100 au for the $3-2$ transition and at $\sim$300 au for $1-0$ transition |
| Fiducial-model HNC 1-0 emission peak radius | ~300 | not stated | au | 6 | For HNC lines, emission peaks at 100 au for the $3-2$ transition and at $\sim$300 au for $1-0$ transition |
| Fiducial-model prominent HCN ring radius, both transitions | 100 | not stated | au | 6 | For HCN, our model predicts a prominent ring around 100 au for both transitions |
| Fiducial-model fainter HCN 1-0 second ring radius | 300 | not stated | au | 6 | a fainter second ring around 300 au also emerges in the $1-0$ transition. |
| Fiducial-model radial HNC-to-HCN line-ratio range over 50–350 au | 0.1 to 0.6 | not stated | dimensionless | 6 | The HNC-to-HCN line ratio generally increases outward, varying from 0.1 to 0.6 in regions where most line emission originates (50 to 350 au in the fiducial model). |
| Modeled disk-integrated HNC-to-HCN 1-0 line ratio | 0.2~0.3 | not stated | dimensionless | 7 | Disk-integrated HNC-to-HCN line ratios are rather constant in our models with varying stellar and disk conditions, with 0.2$\sim$0.3 for the $1-0$ transition and 0.1$\sim$0.2 for the $3-2$ transition |
| Modeled disk-integrated HNC-to-HCN 3-2 line ratio | 0.1~0.2 | not stated | dimensionless | 7 | Disk-integrated HNC-to-HCN line ratios are rather constant in our models with varying stellar and disk conditions, with 0.2$\sim$0.3 for the $1-0$ transition and 0.1$\sim$0.2 for the $3-2$ transition |
| Model 1-0 excitation temperature relative to gas temperature | ~50% | not stated | dimensionless | 6 | We find that the excitation temperature for the $1-0$ line in our model is $\sim50\%$ of the gas temperature. |
| J160830.7-382827 HNC 1-0 flux excess over model prediction | one order of magnitude | not stated | dimensionless | 8 | Its HNC $1-0$ flux is one order of magnitude above our model prediction |
| Fiducial-model HCN 3-2 optical depth at column densities of order 10^12 cm^-2 | ~0.2 | not stated | dimensionless | 8 | In disk regions in which the observed HCN column density is on the order of 10$^{12}\,\rm cm^{-2}$, the line emission of $J=3-2$ transition is optically thin.; Our fiducial model also predicts optically thin line emission of $\tau\sim0.2$ at comparable column densities. |
| Predicted temperature regime for HNC-to-HCN abundance ratios above ~0.4 | <50 | not stated | K | 9 | However, observed abundance ratios above $\sim$0.4 would very likely probe cold or lukewarm ($<$50 K) disk material. |

## Qualitative findings

- Chemical HNC and HCN rings arise naturally in full disks and need not correspond to dust rings  
  > "HNC and HCN show ring-shaped emission morphology in our full-disk models because these molecules are predicted to be mostly abundant in the warm surface layer and outer disk midplane regions." (Summary); "These chemical rings are not related to observed dust rings, but probe physical conditions that are relevant to their formation and destruction." (Summary)
- Higher UV radiation and flaring brighten HNC 3-2; HNC 1-0 is much less affected  
  > "increasing the disk flaring angle results in higher line fluxes of HNC $3-2$." (Dependence of line fluxes on disk parameters); "the simulated line fluxes of the HNC $3-2$ transition increase with higher accretion rates, while the fluxes of the HNC $1-0$ lines stay constant" (Dependence of line fluxes on disk parameters)
- C and O depletion increases cyanide column densities; higher C/O can produce more centrally peaked emission  
  > "Our model indicates higher column densities with an increasing level of C and O depletion, especially in the inner disks" (Dependence on varying the C and O elemental abundances); "With a supersolar C/O=1.5, line emission is brighter and tends to peak at the disk center." (Summary)
- The HNC-to-HCN ratio increases outward but has no unique temperature mapping  
  > "There is no one-to-one relation between temperature and HNC-to-HCN ratio, however." (Emission morphology); "The precise relation of the line ratio – gas temperature depends on other parameters such as C and O abundances and UV penetration." (Summary)
- Non-LTE excitation must be considered for precise physical constraints  
  > "Analysis with HNC and HCN lines should therefore take the non-LTE excitation effects into account for more precise constraints of the disk physical conditions." (Excitation and column density)

## Claim tuples

- H: HNC and HCN chemical structure can produce rings without dust rings. | E: Ray-trace full-disk thermochemical models and compare with TW Hya HNC 3-2 morphology. | R: Models produce rings; TW Hya shows a bright ring around 0.3'' and a weaker bump around 1.0''. | F: Chemical rings trace formation and destruction conditions; the TW Hya ring morphology agrees with model predictions. | **supported**
- H: Cyanide line emission responds to disk UV exposure. | E: Vary flaring and accretion-driven UV radiation in the model grid. | R: HNC 3-2 flux increases with flaring and accretion rate; HNC 1-0 remains nearly unchanged. | F: Higher-J lines can probe the UV environment, whereas 1-0 mainly traces the outer cold midplane. | **supported**
- H: Elemental C and O abundances affect cyanide emission and morphology. | E: Deplete C and O and test a model with C/O=1.5. | R: Column densities increase with depletion; supersolar C/O gives brighter, more centrally peaked emission. | F: Radial cyanide emission profiles might constrain disk C/O. | **supported**
- H: The HNC-to-HCN ratio can serve as a disk thermometer. | E: Compare radial line ratios, local abundance ratios and gas temperatures across model conditions. | R: The line ratio increases outward, but UV penetration and elemental abundances also affect the temperature relation. | F: Temperature sensitivity is supported; a unique thermometer calibration is difficult. | **partially**
- H: The full-disk models reproduce observed HNC emission strengths. | E: Compare literature fluxes and ratios, individual Lupus maps and the 28-disk stack with predictions. | R: The stacked 3σ limit is ~10 mJy km s^-1; J160830.7-382827 is one order of magnitude brighter than predicted. | F: Broad agreement holds for existing observations and the stack, but the transition disk requires a cavity model. | **partially**

## Reasoning

- Why this data: Compare modeled cyanide emission with new TW Hya HNC 3-2 and Lupus HNC 1-0 observations  
  > "we compare the results with currently available disk observations, including new ALMA observations of HNC $J=3-2$ in TW Hya disk and HNC $J=1-0$ for a sample of Lupus disks." (Introduction)
- Why this method: Use thermochemical modeling and non-LTE excitation because abundances, excitation and gas temperature are coupled  
  > "Because both the abundance and excitation calculations depend on $T_{\rm gas}$, the final $T_{\rm gas}$ is obtained by iterating the above steps until a self-consistent solution is reached." (Physical and chemical models); "Analysis with HNC and HCN lines should therefore take the non-LTE excitation effects into account for more precise constraints of the disk physical conditions." (Excitation and column density)
- Alternative: Dust large-grain fractions 0.9–0.99 tested; adopted 0.99 because large grains dominate dust mass  
  > "We have tested models in which we varied the $f_{\rm large}$ parameter between 0.9 and 0.99, but found no significant differences in line emission of cyanides (cite: Cazzoletti2018)." (Physical framework); "We took $f_{\rm large}=0.99$ in our models because large grains dominate the dust mass budget." (Physical framework)
- Alternative: Temperature-dependent destruction alone cannot explain the vertical double peak in abundance ratio  
  > "presents a vertical double-peak pattern that cannot simply be explained by temperature-dependent HNC destruction because the gas temperature increases monotonically toward the surface along the vertical direction." (HNC-to-HCN intensity ratio as a disk thermometer?)
- Alternative: Photodissociation and oxygen abundance considered as additional controls on the vertical HNC-to-HCN ratio  
  > "The sudden decrease in HNC abundance (and HNC/HCN) could be explained by the steep increase in O atom abundance around 20 au" (HNC-to-HCN intensity ratio as a disk thermometer?); "we expect a HNC-to-HCN ratio that gradually approaches unity in photodissociation-dominated regions." (HNC-to-HCN intensity ratio as a disk thermometer?)
- Alternative: Full-disk models are inappropriate for J160830.7-382827; a central-cavity chemical model is needed  
  > "The models we present here are not appropriate for transition disks, which would have a very different UV environment than full disks." (Constraints from new HNC observations of Lupus disks); "Disk chemical models that include a central cavity are needed to explore the origin of the observed morphology." (Constraints from new HNC observations of Lupus disks)
- Alternative: Proposed moderate-to-high-inclination observations to separate cold-midplane emission from elevated photodissociation-dominated emission  
  > "observe disks with moderate to high inclinations for which the midplane and elevated emitting region could be separated spatially and spectrally." (HNC-to-HCN intensity ratio as a disk thermometer?)
- How they decided it was enough: Thermochemical iterations stop at a self-consistent solution  
  > "the final $T_{\rm gas}$ is obtained by iterating the above steps until a self-consistent solution is reached." (Physical and chemical models)
- Limitation (authors): Model abundances and column densities uncertain by at least a factor of a few  
  > "Given the uncertainties in individual rate coefficients and physical structure, our model abundances and column densities have uncertainties of at least a factor of a few." (Chemical network)
- Limitation (authors): Equal HNC and HCN photodissociation rates assumed; actual HNC rate may be twice as high  
  > "The same photodissociation rate was used for HCN and HNC; the actural HNC photodissociation rate may be a factor of 2 higher than that of HCN (cite: Aguado2017)." (Chemical network)
- Limitation (authors): TW Hya short-spacing coverage may affect its radial profile and apparent central component  
  > "The data presented here lack the short-spacing baselines that might affect the radial profile, thus future observations are needed to confirm the presence of this central component." (Comparisons to new HNC observations of TW Hya)
- Limitation (authors): No optimized TW Hya model; improved agreement in components, ring positions and amplitudes is beyond scope  
  > "A detailed model optimized for TW Hya is required to provide an improved match in emission components, ring locations, and structure amplitudes." (Comparisons to new HNC observations of TW Hya); "This is beyond the scope of this work, however." (Comparisons to new HNC observations of TW Hya)
- Limitation (authors): Full-disk models do not represent transition-disk UV environments  
  > "The models we present here are not appropriate for transition disks, which would have a very different UV environment than full disks." (Constraints from new HNC observations of Lupus disks)
- Limitation (authors): Lupus HNC 1-0 may originate at different radii across the stacked sample  
  > "The HNC $1-0$ emission could therefore originate from different radii in the sample." (Constraints from new HNC observations of Lupus disks)
- Limitation (authors): UV penetration and initial C and O abundances complicate a unique temperature diagnostic  
  > "using this ratio as a thermometer in disks will be difficult because the ratio also strongly depends on other parameters, including UV penetration and initial C and O abundances." (HNC-to-HCN intensity ratio as a disk thermometer?)
- Limitation (authors): Outer-disk lines can be subthermal; LTE inference is insufficient  
  > "While the $1-0$ line may be slightly subthermal, the $3-2$ line at this emitting region would be substantially subthermal because this transition has an even higher critical density." (Excitation and column density)
- Caveat (inferred, ours): The TW Hya project identifier is inconsistent between the observation section and acknowledgements.
- Caveat (inferred, ours): The 3σ pixel selection can bias faint radial emission and requires exact replication for a fair morphology comparison.
- Caveat (inferred, ours): The sole Lupus detection has peak S/N 4.5σ; significance assessment and flux uncertainty are insufficiently detailed.
- Caveat (inferred, ours): The stack lacks registration, weighting and aperture specifications.
- Caveat (inferred, ours): Model–observation agreement is qualitative; no likelihood or quantitative goodness-of-fit criterion is supplied.
- Caveat (inferred, ours): Temperature, UV field, elemental abundances and non-LTE excitation remain coupled in the proposed diagnostic.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Verified mapping of TW Hya observations to the conflicting printed project codes.
- Missing: Lupus observation and calibration details inherited from (cite: Tazzari2020).
- Missing: Continuum-subtraction selections and complete imaging scripts.
- Missing: TW Hya deprojection geometry and radial-profile extraction settings.
- Missing: Lupus source list, apertures and stacking implementation.
- Missing: DALI version, complete input files, numerical grids and convergence criteria.
- Missing: Inherited chemical model and complete updated reaction network.
- Missing: Molecular excitation inputs and dust opacity prescription.
- Missing: Exact literature comparison values and flux-scaling implementation.
- Missing: Public data availability statement and released analysis or model products.
- Data volume (inferred): Cannot estimate from the supplied spectral setup and integration times alone.
- Score (inferred): 5/5, Moderate reproducibility: project identifiers, principal imaging settings and substantial model parameters are given, but calibration inheritance, extraction and stacking details, complete model inputs and public availability are unresolved.
- Rediscovery candidate: no, Numeric observational and model targets exist, but public availability is not established by the supplied text and the extraction, stacking and model recipes are incomplete.

## Links

- Method: (cite: Bruderer2012; Bruderer2013) (DALI thermochemical modeling framework.)
- Method: (cite: Visser2018) (Reduced CNO network and chemical-process details.)
- Method: (cite: Cazzoletti2018) (Inherited disk chemical model and smaller-radius model construction.)
- Method: (cite: Loison2014) (Cyanide chemical reactions included in the network.)
- Method: (cite: Graninger2014) (Updated HNC+H destruction rate and 200 K barrier.)
- Method: (cite: Hacar2020) (HNC+O destruction barrier and empirical ISM temperature comparison.)
- Method: (cite: Wakelam2012) (KIDA grain binding energies.)
- Method: (cite: Lynden-Bell1974; Hartmann1998) (Viscous accretion-disk surface-density prescription.)
- Method: (cite: Hughes2008; Andrews2011) (Adopted surface-density index γ=1.)
- Method: (cite: DAlessio2006) (Two-population dust prescription.)
- Method: (cite: Draine1978) (Definition of the external UV field G_0.)
- Companion: (cite: Tazzari2020) (Observation and calibration details for the reused Lupus Band 3 survey.)
- Related: ALMA Lupus disk survey at Band 3
- Related: ALMA Large Program MAPS
- Related: Lupus CN observations (cite: vanTerwisga2019)

## Checks

```json
{
 "quotes": 240,
 "quotes_ok": 240,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2017.1.0156.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 165,
  "stated": 127,
  "rate": 0.77
 },
 "evidence_ok": true
}
```
