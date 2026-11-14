# Chemistry across dust and gas gaps in protoplanetary disks. Modelling the co-spatial molecular rings in the HD 100546 disk

`2024A&A...687A.299L` | Astronomy and Astrophysics 2024 | first author: Leemker, M. | arXiv: 2405.10361 | DOI: 10.1051/0004-6361/202349072

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Where and how bright are molecular line rings expected in gapped disks across a range of physical conditions, and can thermochemical DALI models explain the molecular rings co-spatial with the dust rings in HD 100546  
  > "The aim of this work is to identify the expected location and intensity of rings seen in molecular line emission in gapped disks while exploring a range of physical conditions across the gap." (abstract)
- Target **HD 100546**: coordinates _not stated_; z/distance 108.1 +/- 0.4 pc  
  > "This star is located in a relatively isolated region at a distance of $108.1\pm 0.4$ pc (cite: Gaia2016; GaiaDR3)." (2.1 Source: HD 100546); distance from Gaia (cite: Gaia2016; GaiaDR3)  
  > "This star is located in a relatively isolated region at a distance of $108.1\pm 0.4$ pc (cite: Gaia2016; GaiaDR3)." (2.1 Source: HD 100546)

## Data provenance

- ALMA projects: 2011.0.00863.S, 2015.1.00806.S, 2016.1.00344.S, 2018.1.00141.S, 2021.1.00738.S
- bands: Band 10 (for the new [C I] data)  
  > "taken in Cycle 6 with ALMA in Band 10 (2018.1.00141.S; PI: B. Dent), using 43 antennas with baselines of 15-783 m." (2.2 ALMA data covering [C I])
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 43 antennas  
  > "taken in Cycle 6 with ALMA in Band 10 (2018.1.00141.S; PI: B. Dent), using 43 antennas with baselines of 15-783 m." (2.2 ALMA data covering [C I])
- configurations: _not stated_
- baselines: 15-783 m  
  > "taken in Cycle 6 with ALMA in Band 10 (2018.1.00141.S; PI: B. Dent), using 43 antennas with baselines of 15-783 m." (2.2 ALMA data covering [C I])
- angular resolution: 0.21'' x 0.16'' (28 deg) for [C I]  
  > "This resulted in an image with a spatial resolution of $0.21\ensuremath{''} \times 0.16\ensuremath{''}\ (28\degree)$ and a maximum recoverable scale of 2" in diameter (108 au in radius)." (2.2 ALMA data covering [C I])
- max recoverable scale: 2" in diameter (108 au in radius) for [C I]  
  > "and a maximum recoverable scale of 2" in diameter (108 au in radius)." (2.2 ALMA data covering [C I])
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival pipeline-calibrated data (2018.1.00141.S, PI: B. Dent); other ALMA data from earlier papers  
  > "Starting from the archival pipeline-calibrated data we performed further data reduction using CASA (cite: McMullin2007)." (2.2 ALMA data covering [C I]); "References: 1. (cite: Pineda2019), 2. (cite: Boothinprep), 3. (cite: Perez2020) and Wölfer et al. subm., 4. Wölfer et al. subm., 5. This work." (Table of observed lines)
- Line: C I 3P2-3P1 (not stated)
- Line: HCN J=4-3 (not stated)
- Line: CN N=3-2 fine-structure components (not stated)
- Other facility **Gaia**: Distance to HD 100546 (108.1 +/- 0.4 pc)  
  > "This star is located in a relatively isolated region at a distance of $108.1\pm 0.4$ pc (cite: Gaia2016; GaiaDR3)." (2.1 Source: HD 100546)
- Other facility **FUSE and IUE**: Stellar UV spectrum of HD 100546 used as the model radiation field (as presented in Bruderer2012)  
  > "The stellar spectrum of HD 100546 observed by the Far Ultraviolet Spectroscopic Explorer (FUSE) and the the International Ultraviolet Explorer (IUE) and presented in (cite: Bruderer2012) is used." (2.3.3 Stellar spectrum)
- Other facility **Herschel (PACS, HIFI)**: Literature constraints on disk gas mass and gas-phase water (not newly analysed)  
  > "PACS and HIFI observations of the CO rotational ladder up to $J=38$" (2.1 Source: HD 100546)
- External data: High resolution ALMA continuum and CO isotopologue data (Pineda2019; Perez2020; Wolfer et al. subm.) and intermediate resolution continuum and line data (Booth et al.) used for comparison with the models  
  > "References: 1. (cite: Pineda2019), 2. (cite: Boothinprep), 3. (cite: Perez2020) and Wölfer et al. subm., 4. Wölfer et al. subm., 5. This work." (Table of observed lines) [from (cite: Pineda2019); (cite: Boothinprep); (cite: Perez2020); Wölfer et al. subm.]
- External data: X-ray luminosity 7.9e28 erg/s with temperature 7e7 K  
  > "Additionally, an X-ray luminosity of $7.9\times 10^{28}$ erg s$^{-1}$ (cite: Stelzer2006) with a temperature of $7\times 10^7$ K is included to account for more energetic radiation." (2.3.3 Stellar spectrum) [from (cite: Stelzer2006)]
- External data: Stellar UV spectrum of HD 100546 (FUSE, IUE) extended with a B9V template  
  > "These observations have been dereddend and extended to longer wavelengths using a B9V template (cite: Pickles1998)." (2.3.3 Stellar spectrum) [from (cite: Bruderer2012); (cite: Pickles1998)]
- External data: Cosmic ray ionisation rate of 1e-18 s^-1  
  > "a cosmic ray ionisation rate consistent with that found in other protoplanetary disks of $10^{-18}$ s$^{-1}$ is adopted (cite: Aikawa2021)." (Appendix DALI model setup) [from (cite: Aikawa2021)]
- External data: Isotope ratios used in the CO isotopologue network  
  > "with their ratios taken as / = 77, / = 560, and / = 1792 (cite: Wilson1994)" (2.3.4 Chemistry) [from (cite: Wilson1994)]
- External data: Collisional rate coefficients from the LAMDA database  
  > "The level populations are calculated without assuming local thermodynamical equilibrium (LTE)" (2.3.5 Raytracing) [from (cite: Schoier2005) and others listed in the Raytracing section]
- External data: Stellar age of 5 Myr  
  > "All chemical networks are evaluated at 5 Myr, the approximate age of the HD 100546 star (cite: Arun2019; Pineda2019)." (2.3.4 Chemistry) [from (cite: Arun2019; Pineda2019)]
- Simulation/model as data: Fiducial DALI thermochemical model: gas cavity 0-15 au, dust cavity 0-20 au, gas and dust gap 40-175 au, compared with ALMA continuum, CO isotopologues and other lines  
  > "The fiducial model of a gapped disk with a gas cavity at $0-15$ au, a dust cavity at $0-20$ au, and a gas and dust gap at $40-175$ au provides a good fit to the continuum and the CO isotopologues in the HD 100546 disk." (abstract)

## Processing

### Calibration

- pipeline or manual: Archival pipeline-calibrated data, then further reduction in CASA  
  > "Starting from the archival pipeline-calibrated data we performed further data reduction using CASA (cite: McMullin2007)." (2.2 ALMA data covering [C I])
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: none applied (low signal-to-noise ratio)  
  > "Due to a low signal-to-noise ratio, no self-calibration was applied." (2.2 ALMA data covering [C I])

### Imaging

- task: tclean (written `tCLEAN`) on continuum-subtracted and non-subtracted data  
  > "We first subtracted the continuum using the `uvcontsub` task, flagging channels containing line emission, and then imaged the lines with `tCLEAN` for both the continuum-subtracted and non-subtracted data sets." (2.2 ALMA data covering [C I])
- deconvolver: multi-scale  
  > "We further used the multi-scale deconvolver (scales 0,5,10,20)" (2.2 ALMA data covering [C I])
- weighting robust: Briggs robust = 0.5  
  > "adopted a Briggs robust weighting of 0.5, which gave the best trade off between spatial resolution and sensitivity." (2.2 ALMA data covering [C I])
- uv taper: 0.05'' x 0.05'', 0 deg  
  > "and a slight `uv-taper` ($0.05\ensuremath{''}\times 0.05\ensuremath{''},0\,\degree$) to improve the signal-to-noise ratio in the images." (2.2 ALMA data covering [C I])
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian mask: inclination 42, position angle 140, distance 110 pc, stellar mass 2.13 Msun, systemic velocity 5.7 km/s  
  > "using an inclination of 42 , position angle of 140 , distance of 110 pc, stellar mass of 2.13 M$_{\odot}$, and systemic velocity of 5.7 km s$^{-1}$" (2.2 ALMA data covering [C I])
- multiscale scales: 0, 5, 10, 20  
  > "We further used the multi-scale deconvolver (scales 0,5,10,20)" (2.2 ALMA data covering [C I])
- continuum subtraction: uvcontsub task, flagging channels containing line emission  
  > "We first subtracted the continuum using the `uvcontsub` task, flagging channels containing line emission" (2.2 ALMA data covering [C I])
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.21'' x 0.16'' (28 deg)  
  > "This resulted in an image with a spatial resolution of $0.21\ensuremath{''} \times 0.16\ensuremath{''}\ (28\degree)$ and a maximum recoverable scale of 2" in diameter (108 au in radius)." (2.2 ALMA data covering [C I])
- final rms: _not stated_

### Inherited from earlier work

- DALI model setup is based on earlier DALI models of HD 100546  
  > "The model presented in this work is based on those presented in (cite: Pirovano2022) and (cite: Keyte2023)." (2.3 DALI) [from (cite: Pirovano2022); (cite: Keyte2023)]
- Nitrogen/hydrocarbon chemical network (134 species, 1844 reactions)  
  > "This network was first presented in (cite: Visser2018; Cazzoletti2018); and (cite: Long2021) and includes 134 species and 1844 reactions." (2.3.4 Chemistry) [from (cite: Visser2018; Cazzoletti2018); (cite: Long2021)]
- CO isotopologue network (185 species, 5755 reactions)  
  > "The abundance of the CO isotopologues is predicted with the CO isotopologue network presented in (cite: Miotello2016) consisting of 185 species and 5755 reactions." (2.3.4 Chemistry) [from (cite: Miotello2016)]
- Small ten-reaction chemical network for HCO+  
  > "the chemical network presented in (cite: Leemker2021) is used." (2.3.4 Chemistry) [from (cite: Leemker2021)]
- Emitting heights derived with the ALFAHOR package  
  > "These emitting heights are derived using the ALFAHOR package by masking the individual channels after visually inspecting the data (cite: PanequeCarreno2023)." (Appendix emitting heights) [from (cite: PanequeCarreno2023)]

### Not stated but needed to reproduce (our reading)

- CASA version used for the [C I] reduction
- Which channels were flagged as line-containing for uvcontsub, and the order of the continuum fit
- Channel width / spectral resolution and cell and image size of the [C I] cube
- Final rms of the [C I] image
- Primary-beam correction and flux calibration scale uncertainty for the Band 10 data
- Whether DALI source code and the three chemical networks are available to a reproducer
- Exact input parameter files for the model grid and the raytracing settings (inclination for each model, beam convolution details)
- Stellar mass used in DALI (2.5 Msun in the parameter table) versus 2.13 Msun in the Keplerian mask, and distance 108.1 pc versus 110 pc, are not reconciled in the text
- Reduced datasets from Booth et al. and Wolfer et al. (subm.) that the models are compared with

## Analysis recipe

1. **Reduce and image the Band 10 [C I] data**: Archival pipeline-calibrated data, uvcontsub, tclean with Keplerian mask; no self-calibration  
  > "Starting from the archival pipeline-calibrated data we performed further data reduction using CASA (cite: McMullin2007)." (2.2 ALMA data covering [C I]); "Due to a low signal-to-noise ratio, no self-calibration was applied." (2.2 ALMA data covering [C I])
   - software: CASA, uvcontsub, tclean
   - parameter: Briggs robust 0.5  
  > "adopted a Briggs robust weighting of 0.5, which gave the best trade off between spatial resolution and sensitivity." (2.2 ALMA data covering [C I])
   - parameter: multi-scale scales 0,5,10,20 with a slight uv-taper of 0.05'' x 0.05''  
  > "We further used the multi-scale deconvolver (scales 0,5,10,20)" (2.2 ALMA data covering [C I]); "and a slight `uv-taper` ($0.05\ensuremath{''}\times 0.05\ensuremath{''},0\,\degree$) to improve the signal-to-noise ratio in the images." (2.2 ALMA data covering [C I])
   - assumption: Keplerian mask with inclination 42, PA 140, distance 110 pc, stellar mass 2.13 Msun, systemic velocity 5.7 km/s  
  > "using an inclination of 42 , position angle of 140 , distance of 110 pc, stellar mass of 2.13 M$_{\odot}$, and systemic velocity of 5.7 km s$^{-1}$" (2.2 ALMA data covering [C I])
   - fitting: _not stated_
   - validation: _not stated_
2. **Set up the DALI gas and dust density structure**: Parametrised flared disk with tapered power-law gas surface density, multiplicative drops for cavity and gap, and small and large dust populations  
  > "follow the standard DALI setup for a flared disk with an exponentially tapered power law in the radial direction and a Gaussian distribution of the gas in the vertical direction" (2.3.1 Gas density structure)
   - software: DALI
   - parameter: flaring index psi = 0, scale height h_c = 0.1 at the characteristic radius  
  > "Therefore, the fiducial model has a low flaring index of $\psi = 0$ and a low scale height of $h_c = 0.1$ at the characteristic radius." (3.1 The fiducial model)
   - parameter: gas density lowered by 1e-5 inside the 15 au gas cavity and by 1e-2 between 15 and 20 au  
  > "To match these data, the gas density inside the gas cavity is lowered by a factor of $10^{-5}$ and between the gas (15 au) and dust cavity (20 au) by a factor of $10^{-2}$." (3.1 The fiducial model)
   - parameter: grain sizes 5 nm to 1 um (small) and to 1 mm (large), MRN index -3.5  
  > "Both populations have a minimum grain size of 5 nm but the small grains have a maximum size of 1 $\mu$m, whereas the large grains go up to 1 mm." (Appendix DALI model setup); "An MRN distribution with an index of -3.5 is used to set the grain sizes $a$ within these populations (cite: Mathis1977)." (Appendix DALI model setup)
   - assumption: global gas-to-dust mass ratio 100  
  > "$\Delta_{\mathrm{gas/ dust}}$ & 100 & Gas-to-dust mass ratio" (Table of model parameters)
   - assumption: disk inclination 41 deg  
  > "$i$ & 41$\degree$ & Disk inclination ($0\degree$ is face-on)" (Table of model parameters)
   - assumption: distance 108.1 pc  
  > "$d$ & 108.1 pc & Distance to the star" (Table of model parameters)
   - fitting: No formal fit, no sampler or likelihood; parameters adjusted by hand to roughly match continuum and CO isotopologues  
  > "Therefore, the aim of the fiducial model is not to fit the CO isotopologues perfectly." (3.1 The fiducial model); "Instead, the aim of the fiducial model is to provide a basis that roughly fits the continuum and the CO isotopologues" (3.1 The fiducial model)
   - validation: Compared model continuum and CO isotopologue emission with ALMA profiles; gas gap depth explored with CO isotopologues  
  > "we find that CO isotopologue emission is consistent with a shallow gas gap where the gas is depleted by at most one order of magnitude" (3.1 The fiducial model)
3. **Run the chemical networks**: Three networks (nitrogen/hydrocarbon, CO isotopologue, HCO+) evolved on the DALI density and temperature structure with molecular initial conditions  
  > "Both chemical networks are started with molecular initial conditions and a fiducial total (gas $+$ ice) C/O ratio of 0.4" (2.3.4 Chemistry); "All chemical networks are evaluated at 5 Myr, the approximate age of the HD 100546 star (cite: Arun2019; Pineda2019)." (2.3.4 Chemistry)
   - software: DALI
   - parameter: non-thermal desorption rates updated to 5e-4 and 1.4e-3 molecules per grain per UV photon  
  > "The non-thermal desorption rates of and CO are updated from $1.3\times 10^{-3}$ and $2.7\times 10^{-3}$ molecules desorbed per grain per incident UV photon to $5\times 10^{-4}$ and $1.4\times 10^{-3}$ molecules desorbed per grain per incident UV photon respectively" (2.3.4 Chemistry)
   - parameter: cosmic ray ionisation rate 1e-18 s^-1  
  > "a cosmic ray ionisation rate consistent with that found in other protoplanetary disks of $10^{-18}$ s$^{-1}$ is adopted (cite: Aikawa2021)." (Appendix DALI model setup)
   - assumption: chemistry evolved to 5 Myr; fiducial total C/O of 0.4  
  > "All chemical networks are evaluated at 5 Myr, the approximate age of the HD 100546 star (cite: Arun2019; Pineda2019)." (2.3.4 Chemistry)
   - fitting: _not stated_
   - validation: The network reproduces CN, HCN and related emission in other disks within a factor of a few, per the paper  
  > "The chemical network used to calculate these abundances reproduces the CN, HCN, HNC, and emission in other protoplanetary disks within a factor of a few in general" (3.3 Integrated intensity maps)
4. **Raytrace synthetic observations and compare with ALMA**: DALI raytracer, non-LTE level populations, continuum subtraction and convolution to the observed beam of each species  
  > "The synthetic ALMA observations are produced using the raytracer in DALI." (2.3.5 Raytracing); "Finally, all synthetic image cubes are continuum subtracted and convolved to a beam matching that of the observations of that particular species" (2.3.5 Raytracing)
   - software: DALI
   - parameter: blended components raytraced separately and summed  
  > "Therefore, these two and three transitions were raytraced and added assuming the emission is optically thin." (2.3.5 Raytracing)
   - assumption: emission of blended components optically thin; level populations without LTE  
  > "The level populations are calculated without assuming local thermodynamical equilibrium (LTE)" (2.3.5 Raytracing)
   - fitting: No fitting; agreement judged by eye and by factors on moment-0 maps and radial profiles  
  > "Instead of matching the observed line intensities within the uncertainty of the data, we look for trends in the abundances and line intensities for a range of key parameters such as gap depth and chemical composition." (3 Results)
   - validation: A model is considered successful if it reproduces the data within a factor of about 2-3  
  > "Therefore, a model is expected to reproduce the data within a factor of $\sim 2-3$ in general (cite: Kama2016; Sturm2023)." (3 Results)
5. **Explore gas gap depth, C/O, background UV, flaring and X-ray luminosity**: Grid of DALI models varying one parameter at a time around the fiducial model; compare column densities, radial profiles and line ratios  
  > "The thermochemical models spanning a range of gas gap depth ($\delta_{\rm gas\ gap} = 1-10^{-5}$)" (4.1 Radial structures); "In this section, the effect of an increased C/O ratio is explored in the fiducial model with a gas gap of $\delta_{\rm gas\ gap} = 10^{-1}$." (3.5 Different C/O ratios)
   - software: DALI, scipy
   - parameter: background UV 1 G0 in the fiducial model, lowered by a factor of ten in variations  
  > "The models assume that the external UV field is 1 $G_0$, the mean UV field in the interstellar medium." (3.6 Background UV); "Lowering the background UV field by a factor of ten decreases the CN and column densities by that same factor at $300-400$ au." (3.6 Background UV)
   - parameter: X-ray luminosity increased by factors of 4 and 6  
  > "the mean and maximum X-ray luminosities reported in (cite: Skinner2020) that are a factor of 4 and 6 higher than that in the fiducial model." (Appendix X-ray luminosity)
   - parameter: column densities smoothed with a savgol filter over 10 points, 3rd order polynomial  
  > "the column densities inside 250 au are smoothed in log space with a savgol filter in scipy over 10 points and a 3rd order polynomial" (3.4.1 Column densities)
   - assumption: small dust follows the drop in gas density in the gap  
  > "The small dust is assumed to follow the drop in the gas density." (3.4 The effect of a gas gap)
   - fitting: No fitting; trends and comparisons only  
  > "Instead of matching the observed line intensities within the uncertainty of the data, we look for trends in the abundances and line intensities for a range of key parameters such as gap depth and chemical composition." (3 Results)
   - validation: _not stated_
6. **Test a combined model with radially varying C/O and lowered background UV**: Two models with background UV reduced by 10 and C/O raised to 1.01 across the dust rings or only in two 10 au wide rings  
  > "two models with a background UV field attenuated by a factor of 10 and where the C/O ratio is increased to 1.01 in two rings." (4.2.4 C/O ratio / summary); "In this model, the C/O ratio is only increased in two 10 au wide rings from 35 to 45 au and from 215 to 225 au to match the location of the observed emission ring." (4.2.4 C/O ratio / summary)
   - software: DALI
   - parameter: C/O = 1.01 in rings at 35-45 au and 215-225 au; fiducial C/O 0.4 elsewhere  
  > "and the fiducial C/O ratio of 0.4 in the other disk regions reproduces the double ringed morphology seen in the HCN, CN, and emission and it roughly reproduces the morphology of the NO." (5 Conclusions)
   - fitting: _not stated_
   - validation: Model intensities compared with observations within about a factor of 5  
  > "this model does reproduce the intensity of these molecules within a factor of $\sim 5$" (4.2.4 C/O ratio / summary)

## Software

- **CASA** : Reduction and imaging of the Band 10 [C I] data  
  > "Starting from the archival pipeline-calibrated data we performed further data reduction using CASA (cite: McMullin2007)." (2.2 ALMA data covering [C I])
- **uvcontsub** : Continuum subtraction of the [C I] data  
  > "We first subtracted the continuum using the `uvcontsub` task, flagging channels containing line emission" (2.2 ALMA data covering [C I])
- **tclean** : Imaging the [C I] line data  
  > "and then imaged the lines with `tCLEAN` for both the continuum-subtracted and non-subtracted data sets." (2.2 ALMA data covering [C I])
- **Keplerian mask** : Mask applied when cleaning the [C I] cube  
  > "using an inclination of 42 , position angle of 140 , distance of 110 pc, stellar mass of 2.13 M$_{\odot}$, and systemic velocity of 5.7 km s$^{-1}$" (2.2 ALMA data covering [C I])
- **DALI (Dust And LInes)** : Thermochemical disk modelling and raytracing of synthetic ALMA observations  
  > "we model the dust rings and rings seen in molecular line emission using the thermochemical code Dust And LInes (cite: Bruderer2009; Bruderer2012; Bruderer2013)." (2.3 DALI); "The synthetic ALMA observations are produced using the raytracer in DALI." (2.3.5 Raytracing)
- **scipy (savgol filter)** : Smoothing model column densities  
  > "the column densities inside 250 au are smoothed in log space with a savgol filter in scipy over 10 points and a 3rd order polynomial" (3.4.1 Column densities)
- **ALFAHOR** : Deriving observed CO emitting heights (average of both disk sides)  
  > "These emitting heights are derived using the ALFAHOR package by masking the individual channels after visually inspecting the data (cite: PanequeCarreno2023)." (Appendix emitting heights)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [C I] image spatial resolution | 0.21'' x 0.16'' (28 deg) | not stated | arcsec | 1 | This resulted in an image with a spatial resolution of $0.21\ensuremath{''} \times 0.16\ensuremath{''}\ (28\degree)$ and a maximum recoverable scale of 2" in diameter (108 au in radius). |
| [C I] maximum recoverable scale | 2 (diameter), 108 au radius | not stated | arcsec | 1 | and a maximum recoverable scale of 2" in diameter (108 au in radius). |
| Fiducial gas gap depth between 40 and 175 au | factor of ~10 drop in gas density (delta_gas_gap = 1e-1) | no more than a factor of ~10 | dimensionless | 5 | In particular, the CO isotopologue emission is consistent with a shallow gas gap with no more than a factor of $\sim 10$ drop in gas density at $40-175$ au. |
| Gas cavity, dust cavity and gap radii of the fiducial model | gas cavity 0-15 au, dust cavity 0-20 au, gap 40-175 au | not stated | au | 2 | The fiducial model of a gapped disk with a gas cavity at $0-15$ au, a dust cavity at $0-20$ au, and a gas and dust gap at $40-175$ au |
| Best-fit C/O ratio for [C I], CN and C2H | ~0.8-1.2 | not stated | dimensionless | 5 | and is an elevated C/O of $\sim 0.8-1.2$. |
| C/O in narrow rings of the radially varying C/O model | 1.01 in rings 35-45 au and 215-225 au | not stated | dimensionless | 6 | In this model, the C/O ratio is only increased in two 10 au wide rings from 35 to 45 au and from 215 to 225 au to match the location of the observed emission ring. |
| Fiducial model underprediction of atomic carbon inside ~108 au | an order of magnitude | not stated | dimensionless | 5 | Inside $\sim108$ au, the fiducial model underpredicts the emission of atomic carbon by an order of magnitude. |
| Decrease of CN and C2H column densities for 10x lower background UV at 300-400 au | factor of 10 | not stated | dimensionless | 5 | Lowering the background UV field by a factor of ten decreases the CN and column densities by that same factor at $300-400$ au. |
| Decrease of NO column density for 10x lower background UV at 200-350 au | factor of 5 | not stated | dimensionless | 5 | The NO decreases by a factor of 5 from $200-350$ au. |
| Height of peak CN number density at inner rim of outer dust ring, flattest models (psi = -0.1 and 0) | z = 55-53 au at r = 175 au | not stated | au | 5 | For the two flattest models ($\psi = -0.1$ and 0) the CN at $r=175$ au peaks at $z=55-53$ au |
| Height of peak CN number density, more flared models (psi = 0.1 and 0.2) | 66-68 au at r = 176 au | not stated | au | 5 | for the two more flared models ($\psi = 0.1$ and 0.2), the CN peaks at a height of $66-68$ au at $r=176$ au. |
| Location of the water snowline in the HD 100546 disk (inferred) | inside 15 au (unresolved at 31 au resolution) | not stated | au | 4 | Therefore, the water snowline in the HD 100546 disk is likely unresolved at the 31 au resolution of the observations and thus located inside 15 au. |

## Qualitative findings

- Molecular rings in HCN, CN, C2H and NO are not naturally co-spatial with dust rings in the thermochemical models  
  > "- In general, molecular rings and dust rings do not coincide unless gaps are very deep." (5 Conclusions)
- The best model needs a shallow gas gap, a reduced background UV field and a locally elevated C/O  
  > "The constraints from modelling multiple molecules across a gas gap provides a first step towards a full picture of the chemical makeup of the planet-forming material." (5 Conclusions)

## Claim tuples

- H: Do CO isotopologues constrain the depth of the gas gap between the two dust rings in HD 100546 | E: Varied the gas depletion delta_gas_gap from 1 to 1e-5 in DALI and compared CO isotopologue profiles with ALMA data | R: Models with deeper gaps underpredict CO isotopologue emission in the gap | F: The disk has a shallow gas gap, depleted by at most a factor of ~10 | **supported**
- H: Under what conditions are molecular rings co-spatial with dust rings | E: Gas gap depth, C/O, background UV and flaring were varied in DALI and ring locations compared across HCN, CN, C2H and NO | R: Rings coincide with dust rings only for very deep gaps or a radially varying C/O | F: Molecular rings need not trace gas gaps and can be chemical rather than physical | **supported**
- H: Are the UV tracers CN, C2H and NO good tracers of gas gap depth | E: Computed column densities and line ratios for different gap depths | R: Their column densities are insensitive to gap depth within a factor of a few for shallow to moderately deep gaps | F: CN, C2H and NO are not good tracers of the gas gap depth | **supported**
- H: Does a lower external UV field improve the match in the outer disk | E: Reduced the background UV field by a factor of ten in the models | R: Extended CN emission and the outer C2H ring are removed and the NO ring at 300 au is reduced | F: A reduced background UV field is needed to suppress the outer rings | **supported**
- H: Can a radially varying C/O explain the double rings seen in HD 100546 | E: Set C/O = 1.01 in narrow rings at 40 and 220 au with a shallow gas gap and lowered background UV | R: The double-ring morphology of HCN, CN and C2H is reproduced; [C I] remains underproduced by about an order of magnitude | F: A radially varying C/O above 1 in narrow regions, with a shallow gas gap and reduced UV, is indicated | **partially**

## Reasoning

- Why this data: ALMA data at several resolutions plus new [C I] data used to probe the origin of molecular substructures  
  > "to elucidate the origin of the observed molecular substructures." (2.1 Source: HD 100546)
- Why this method: Thermochemical models cannot match line intensities within data uncertainty, so trends over parameters are explored  
  > "Instead of matching the observed line intensities within the uncertainty of the data, we look for trends in the abundances and line intensities for a range of key parameters such as gap depth and chemical composition." (3 Results)
- Alternative: Second-generation gas from collisions of larger bodies in the outer ring suggested as an alternative to elevated C/O  
  > "Another explanation for the spatial overlap between molecular rings and the outer dust ring could be that the gas in the outer dust ring is second generation gas due to collisions of larger bodies" (4.2.3 C/O ratio across the HD 100546 disk)
- Alternative: Higher X-ray luminosity creates a ring at 30 au but also adds CN emission not seen in the data  
  > "The largest effect on the emission morphology is seen in the profile, where the increases X-ray flux creates a ring at 30 au, similar to the morphology of the observations." (4.2.3 C/O ratio across the HD 100546 disk)
- How they decided it was enough: A model is accepted if it reproduces the data within a factor of about 2-3  
  > "Therefore, a model is expected to reproduce the data within a factor of $\sim 2-3$ in general (cite: Kama2016; Sturm2023)." (3 Results)
- Limitation (authors): Thermochemical fits are not unique and degeneracies exist  
  > "In addition, a thermochemical model reproducing the observed line intensities within this factor is not unique and degeneracies in the model exist due to e.g., differences in the physical and thus thermal and chemical structure of the model." (3 Results)
- Limitation (authors): Small maximum recoverable scale of the [C I] data filters emission at large radii  
  > "This could partially be due to the small maximum recoverable scale of 2" ($\sim 108$ au in radius), filtering the emission at larger distances." (3.5.1 Column densities and emission profiles)
- Limitation (authors): Water photodesorption is not included in the small HCO+ network, so HCO+ is overpredicted in the gap  
  > "Photodesorption of water ice is not included in the network used to predict the abundance in this work." (4.2.1 tracing a low gas-phase water abundance)
- Caveat (inferred, ours): Fiducial model is tuned by hand with no formal fit, so quoted gap depths and C/O values carry no statistical uncertainty
- Caveat (inferred, ours): Model parameters are degenerate (gap depth, flaring, C/O, UV field) and only a one-at-a-time grid is shown
- Caveat (inferred, ours): Stellar mass and distance inconsistent between the Keplerian mask (2.13 Msun, 110 pc) and the DALI table (2.5 Msun, 108.1 pc)
- Caveat (inferred, ours): Several key observational datasets come from companion papers still in preparation

## Reproducibility

- Data public (paper): [C I] data described as archival ALMA data (project 2018.1.00141.S)  
  > "Starting from the archival pipeline-calibrated data we performed further data reduction using CASA (cite: McMullin2007)." (2.2 ALMA data covering [C I])
- Products in archive: _not stated_
- Missing: DALI code and exact model input files
- Missing: Chemical network files and LAMDA files used for raytracing
- Missing: Reduced ALMA continuum and CO cubes from companion papers
- Missing: CASA version and line-free channel selection for the [C I] data
- Missing: Radial profile extraction details (azimuthal averaging, inclination and position angle used for deprojection)
- Data volume (inferred): Roughly tens of GB for the Band 10 [C I] dataset; the other ALMA datasets are not needed to reproduce the new [C I] image but would be needed for a full comparison
- Score (inferred): 2/5, Main results come from a hand-tuned thermochemical model grid that needs DALI and input files the paper does not give; only the [C I] imaging recipe is reasonably complete.
- Rediscovery candidate: no, Main results are model-based comparisons with qualitative and factor-of-few agreement rather than numeric measurements from the ALMA data, and the model code and inputs are not stated as public.

## Links

- Method: (cite: Bruderer2009; Bruderer2012; Bruderer2013) (DALI thermochemical code)
- Method: (cite: Visser2018; Cazzoletti2018); (cite: Long2021) (Nitrogen and hydrocarbon chemical network)
- Method: (cite: Miotello2016) (CO isotopologue chemical network)
- Method: (cite: Leemker2021) (Small HCO+ chemical network)
- Companion: (cite: Boothinprep) (Intermediate resolution ALMA data of dust, CO, HCN, CN, C2H, NO and HCO+ compared with the models)
- Companion: Wölfer et al. subm. (High resolution CO isotopologue ALMA data compared with the models)
- Companion: (cite: Pineda2019); (cite: Perez2020) (High resolution ALMA continuum and CO isotopologue data)
- Companion: (cite: Pirovano2022); (cite: Keyte2023) (Earlier DALI models of HD 100546 on which this model is based)
- Related: MAPS (Molecules with ALMA at Planet-forming scales)

## Checks

```json
{
 "quotes": 124,
 "quotes_ok": 124,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 110,
  "stated": 85,
  "rate": 0.773
 },
 "evidence_ok": true
}
```
