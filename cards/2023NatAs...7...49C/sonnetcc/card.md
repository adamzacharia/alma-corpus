# UV-driven chemistry as a signpost of late-stage planet formation

`2023NatAs...7...49C` | Nature Astronomy 2023 | first author: Calahan, Jenny K. | arXiv: 2212.05539 | DOI: 10.1038/s41550-022-01831-8

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: How does the chemistry of a planet-forming disk evolve from a cosmic-ray/X-ray-dominated regime to a UV-dominated equilibrium that explains bright CH3CN and HC3N emission from cold gas  
  > "We explain how the chemistry of a planet-forming disk evolves from a cosmic-ray/X-ray-dominated regime to a ultraviolet-dominated chemical equilibrium." (abstract)
- Target **HD 163296**: coordinates _not stated_; z/distance 101 pc  
  > "is nearby at 101 pc(cite: Gaia18)" (Main); distance from Gaia18 (cite: Gaia18)  
  > "is nearby at 101 pc(cite: Gaia18)" (Main)
- Target **TW Hya**: coordinates _not stated_; z/distance 59.9 pc  
  > "hosts the closest Class II disk at 59.9 pc(cite: Gaia18)" (Supplementary Information: TW Hya); distance from Gaia18 (cite: Gaia18)  
  > "hosts the closest Class II disk at 59.9 pc(cite: Gaia18)" (Supplementary Information: TW Hya)

## Data provenance

- ALMA projects: 2018.1.01055.L, 2016.1.01046.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: HD 163296: beam-circularized, uv-tapered images with synthesised beam 0.3 arcsec; TW Hya: beams matched with small uv-tapers (1.05 x 0.83 arcsec as printed)  
  > "For all lines, we used the beam-circularized and uv-tapered images, which had synthesised beam sizes of 0."3." (Methods: Observations); "matched using small uv-tapers to 1$.\!\!^{\prime\prime}$05 x 0$.\!\!^{\prime\prime}$83" (Methods: Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: HD 163296 from the MAPS large program, publicly available; TW Hya from ALMA project 2016.1.01046.S  
  > "The data that support the findings of this study can be obtained as part of the MAPS program and are publicly available via alma-maps.info." (Data Availability)
- Line: CH3CN not stated (not stated)
- Line: HC3N not stated (not stated)
- Line: HCN not stated (not stated)
- Other facility **Gaia**: Distances to HD 163296 (101 pc) and TW Hya (59.9 pc)  
  > "is nearby at 101 pc(cite: Gaia18)" (Main); "hosts the closest Class II disk at 59.9 pc(cite: Gaia18)" (Supplementary Information: TW Hya)
- Other facility **Herschel PACS**: HD J=1-0 observation used to constrain the TW Hya disk model (from earlier work)  
  > "an HD J=1-0 observation from the *Hershel* PACS instrument" (Supplementary Information: TW Hya)
- External data: CLEANed HD 163296 image cubes and radial profiles of CH3CN, HCN and HC3N from the MAPS program  
  > "see Czekala et al. 2021(cite: Czekala21), Law et al. 2021(cite: Law21rad), and Öberg et al. 2021(cite: Oberg21)" (Methods: Observations) [from Czekala et al. 2021 (cite: Czekala21); Law et al. 2021 (cite: Law21rad); Oberg et al. 2021 (cite: Oberg21)]
- External data: CH3CN observations and imaging of TW Hya (details deferred to earlier paper)  
  > "See Loomis et al. 2018a(cite: Loomis18) for more details." (Methods: Observations) [from Loomis et al. 2018a (cite: Loomis18)]
- External data: Initial HD 163296 gas-to-small-dust ratio of 500 from the earlier thermo-chemical model  
  > "The model of HD 163296 started with a gas-to-small dust ratio of the disk equal to 500(cite: Zhang21)" (Main) [from Zhang et al. 2021 (cite: Zhang21)]
- External data: Gas-phase chemical network (UMIST RATE12 derived)  
  > "Our chemical network is derived from Bosman et al. 2018(cite: Bosman18)" (Methods: Modeling) [from Bosman et al. 2018 (cite: Bosman18); McElroy et al. 2013 (cite: McElroy13)]
- External data: Molecular properties of CH3CN, HC3N and HCN from LAMDA, with some parameters updated from CDMS  
  > "were taken from the Leiden Atomic and Molecular Database" (Methods: Modeling) [from Schoier05 (cite: Schoier05); Muller01, Muller05 (CDMS)]
- External data: Dust opacities  
  > "Opacity values for the dust are calculated based on Birnstiel et al. 2018(cite: Birnstiel18)." (Methods: Modeling) [from Birnstiel et al. 2018 (cite: Birnstiel18)]
- Simulation/model as data: RAC2D thermo-chemical models of the HD 163296 and TW Hya disks, ray-traced with RADMC-3D and compared with observed azimuthally-averaged radial profiles  
  > "The 2D temperature, density, and molecular abundance results were used to simulate observations of each disk with a raytracing code: RADMC-3D" (Methods: Modeling)

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

- task: tclean in CASA 6.1.0 for HD 163296 cubes; CLEAN for TW Hya lines  
  > "The image cubes were produced using the `tclean` task in the Common Astronomy Software Applications (CASA) package, version 6.1.0" (Methods: Observations); "Each emission line was individually imaged using `CLEAN`" (Methods: Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: uv-tapered images used for HD 163296; small uv-tapers for TW Hya (values not given)  
  > "For all lines, we used the beam-circularized and uv-tapered images" (Methods: Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian masks based on disk geometric parameters (HD 163296); Keplerian mask (TW Hya)  
  > "Keplerian masks based on the disk geometric parameters were used in the CLEANing process" (Methods: Observations); "A Keplerian mask was used to extract the flux for each transition." (Methods: Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Beam-circularized (HD 163296); beams matched across transitions with small uv-tapers (TW Hya)  
  > "the synthesised beam for each transition were matched using small uv-tapers" (Methods: Observations)
- final beam: 0.3 arcsec (HD 163296); 1.05 x 0.83 arcsec (TW Hya)  
  > "which had synthesised beam sizes of 0."3." (Methods: Observations)
- final rms: _not stated_

### Inherited from earlier work

- Observations and CLEANing/radial-profile techniques for HD 163296  
  > "For a thorough description of the observations and the techniques used to obtain the CLEAN-ed images and radial profiles" (Methods: Observations) [from Czekala et al. 2021 (cite: Czekala21), Law et al. 2021 (cite: Law21rad), Oberg et al. 2021 (cite: Oberg21)]
- TW Hya CH3CN observations and imaging  
  > "A description of the observations of $\textrm{CH}_{3}\textrm{CN}$ towards TW Hya can be found in Loomis et al. 2018a(cite: Loomis18)." (Methods: Observations) [from Loomis et al. 2018a (cite: Loomis18)]
- HD 163296 thermo-chemical model set-up (reproducing continuum, SED, CO isotopologues)  
  > "Our modeling efforts follow that of Zhang et al. 2021(cite: Zhang21), and Calahan et al. 2021b(cite: Calahan21b)" (Main) [from Zhang et al. 2021 (cite: Zhang21); Calahan et al. 2021b (cite: Calahan21b)]
- TW Hya thermo-chemical model set-up  
  > "Our modeling efforts of TW Hya follow that of Calahan et al. 2021a(cite: Calahan21a)" (Supplementary Information: TW Hya) [from Calahan et al. 2021a (cite: Calahan21a)]
- Detailed description of RAC2D physical code  
  > "a detailed description of the code can be found in Calahan et al 2021a(cite: Calahan21a)" (Methods: Modeling) [from Calahan et al 2021a (cite: Calahan21a)]

### Not stated but needed to reproduce (our reading)

- tclean parameters for HD 163296 and TW Hya cubes (robust, cell, image size, niter, threshold, channel width) and the uv-taper values for HD 163296
- Which CH3CN, HC3N and HCN transitions and rest frequencies were imaged
- Implementation of the Jorsater & van Moorsel correction
- RAC2D input files, stellar parameters and initial abundances for HD 163296 and TW Hya (largely deferred to Zhang21, Calahan21a, Calahan21b)
- Exact initial carbon abundance values and carrier (C, CH4 or C2H) of the final model, and the UV/X-ray/cosmic-ray field settings
- RADMC-3D settings (inclination, position angle, photon counts, velocity resolution) and GoFish deprojection parameters
- Single-point model grid (ranges of gas-to-dust ratio and carbon abundance)

## Analysis recipe

1. **Obtain HD 163296 and TW Hya line images and radial intensity profiles**: CLEAN images with Keplerian masks, JvM correction, beam circularisation/uv-taper; zeroth moment maps deprojected and azimuthally averaged  
  > "All radial intensity profiles were generated by deprojecting and azimuthally-averaging zeroth moment maps using the GoFish python package." (Methods: Observations)
   - software: CASA, tclean, GoFish
   - parameter: HD 163296 synthesised beam 0.3 arcsec  
  > "which had synthesised beam sizes of 0."3." (Methods: Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Explore single-point midplane chemistry models**: Single-point models of the cold, dense midplane with a reduced gas-phase network, varying gas-to-dust ratio, carbon abundance and other variables  
  > "We varied the gas-to-dust mass ratio and initial carbon abundance among other physical and chemical variables including the nitrogen abundance, dust extinction, and ionization rate." (Main)
   - parameter: Network from Bosman18/UMIST RATE12, most grain-surface reactions disregarded  
  > "for this study we disregarded most grain-surface chemical reactions in order to isolate gas-phase formation of $\textrm{CH}_{3}\textrm{CN}$" (Methods: Modeling)
   - fitting: _not stated_
   - validation: _not stated_
3. **Build RAC2D thermo-chemical disk models**: Three components (gas, small dust, large dust) with Lynden-Bell & Pringle surface density and power-law scale height; parameters in Table 1  
  > "Our model consists of three mass components: gas, small dust, and large dust grains." (Methods: Modeling); "The modeling parameters used for TW Hya and HD 163296 are shown in Table 1." (Methods: Modeling)
   - software: RAC2D
   - parameter: Small grains 5e-3 to 1 micron; large grains 5e-3 to 1e3 micron  
  > "The small dust grains have radii between $5 \times 10^{-3}$ - $1 \mu$m, and the large grains have radii between $5 \times 10^{-3}$ - $10^{3} \mu$m." (Methods: Modeling)
   - assumption: MRN grain size distribution n(a) ~ a^-3.5 for each dust population  
  > "each dust population follows an Mathis, Rumpl, and Nordsieck (MRN) grain distribution" (Methods: Modeling)
   - assumption: Small grains 50% silicates and 50% refractory organics  
  > "Small dust grains consist of 50% silicates and 50% refractory organics." (Methods: Modeling)
   - fitting: _not stated_
   - validation: Earlier model reproduces mm continuum, SED and CO isotopologue lines  
  > "reproducing the mm dust-continuum observations, the spectral-energy distribution (SED), the full line intensity and morphology of six CO isotopologue transitions" (Main)
4. **Deplete small dust and enhance gas-phase carbon, run to equilibrium**: Small dust mass depleted by a factor of 10 and initial gas-phase carbon raised so C/O exceeds unity; model run for 1 Myr  
  > "we deplete the small dust mass by a factor of 10 throughout the disk of HD 163296 making the new gas-to-dust mass ratio above the pebble disk midplane equal to 5,000." (Results); "Our thermo-chemical model is run for a full megayear (Myr), after which the chemistry reaches an equilibrium." (Results)
   - software: RAC2D
   - parameter: C/O = 1-2 with small dust depleted by a factor of 10  
  > "using a C/O = 1-2 and a factor of 10 depletion of small dust roughly reproduces line ratios and fluxes of the radial intensity profiles" (Results)
   - assumption: Network of 6,302 gas-phase reactions and twelve grain-surface reactions  
  > "In our network there are 6,302 gas phase reactions and we have limited the grain-surface reactions to twelve." (Methods: Chemical Reactions)
   - fitting: _not stated_
   - validation: Run time chosen because chemistry reaches equilibrium  
  > "We run our thermo-chemical model for 1 Myr as the $\textrm{CH}_{3}\textrm{CN}$ and $\textrm{HC}_{3}\textrm{N}$ chemistry reaches an equilibrium after this time period" (Methods: Chemical Reactions)
5. **Ray-trace models and compare radial profiles with ALMA**: RADMC-3D ray tracing of model abundances into 3D cubes, compressed with GoFish into moment maps and radial profiles compared with azimuthally-averaged observations  
  > "to compress these 3D images into zeroth moment maps and radial profiles which were then directly compared to the azimuthally-averaged observations" (Methods: Modeling)
   - software: RADMC-3D, GoFish
   - fitting: _not stated_
   - validation: Comparison of modelled and observed radial intensity profiles  
  > "using a C/O = 1-2 and a factor of 10 depletion of small dust roughly reproduces line ratios and fluxes of the radial intensity profiles" (Results)
6. **Adjust inner-disk C/O to match observed inner emission**: C-to-O set to the ISM value inside about 20 au  
  > "we set the C-to-O ratio = 0.47, or the ISM ratio, inside of ($\sim$20 au)" (Results)
   - software: RAC2D
   - fitting: _not stated_
   - validation: _not stated_
7. **Compute MRI-active regions from model ionisation**: Magnetic Reynolds number and ambipolar diffusion term evaluated for early-stage and late-stage models  
  > "In our work, we assume a combined $Am >$100 and $Re >$ 3,000 to signify an MRI-active zone." (Supplementary Information: MRI Instability)
   - software: RAC2D
   - parameter: Am > 100 and Re > 3,000 for MRI-active zone  
  > "In our work, we assume a combined $Am >$100 and $Re >$ 3,000 to signify an MRI-active zone." (Supplementary Information: MRI Instability)
   - fitting: _not stated_
   - validation: _not stated_
8. **Test SED degeneracy of small-dust depletion**: Monte Carlo radiative transfer SED models varying minimum grain radius or power-law index  
  > "We find that by varying the minimum dust grain radius or the power law index, we can account for a factor of 10 in UV attenuation." (Supplementary Information: SED Degeneracy)
   - software: TORUS
   - fitting: _not stated_
   - validation: Depleted model argued to remain consistent with the SED  
  > "Thus our depletion of small dust continues to reproduce all previous observables including the SED." (Supplementary Information: SED Degeneracy)

## Software

- **CASA** 6.1.0: tclean imaging of HD 163296 cubes  
  > "The image cubes were produced using the `tclean` task in the Common Astronomy Software Applications (CASA) package, version 6.1.0" (Methods: Observations)
- **GoFish** : Deprojected, azimuthally averaged radial profiles from moment maps of observations and models  
  > "All radial intensity profiles were generated by deprojecting and azimuthally-averaging zeroth moment maps using the GoFish python package." (Methods: Observations)
- **RAC2D** : Thermo-chemical models of HD 163296 and TW Hya disks  
  > "was used to create models of the disks around TW Hya and HD 163296" (Methods: Modeling)
- **RADMC-3D** : Ray tracing model abundances into 3D emission cubes  
  > "These were used as inputs for the raytracing code RADMC-3D(cite: radmc3d)." (Methods: Modeling)
- **TORUS** : Monte Carlo radiative transfer SED models for the degeneracy test  
  > "We modeled protoplanetary disk SEDs using the code TORUS" (Supplementary Information: SED Degeneracy)
- **LAMDA** : Molecular properties of CH3CN, HC3N and HCN for ray tracing  
  > "were taken from the Leiden Atomic and Molecular Database" (Methods: Modeling)
- **CDMS** : Updated molecular parameters  
  > "with some molecular parameters updated according to data from the Cologne Database for Molecular Spectroscopy" (Methods: Modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Fraction of CH3CN mass frozen on grains in the proposed scenario | ~96 | not stated | percent | 4 | $\sim$96% of the total mass of $\textrm{CH}_{3}\textrm{CN}$ continues to reside frozen out onto grains |
| Gas-to-small-dust mass ratio above the midplane after depletion | 5,000 | not stated | dimensionless | 4 | making the new gas-to-dust mass ratio above the pebble disk midplane equal to 5,000 |
| UV field increase in the atmosphere | 3-5 | not stated | dimensionless (factor) | 4 | the UV field increases by a factor of 3-5 in the atmosphere and between 1-2 near the midplane |
| UV field increase near the midplane | 1-2 | not stated | dimensionless (factor) | 4 | the UV field increases by a factor of 3-5 in the atmosphere and between 1-2 near the midplane |
| Increase in MRI-active gas mass | 13 | not stated | dimensionless (factor) | 7 | As a result, thirteen times more mass within the disk becomes MRI-active including within the midplane. |
| Midplane MRI-active extent, base (early-stage) model | 4 | not stated | au | 7 | In the base model representing early stages of disk chemistry, the MRI activity at the midplane extends to 4 au. |
| Midplane MRI-active extent, small-dust-depleted model | ~10 | not stated | au | 7 | the MRI activity at the midplane then extends out to $\sim$10 au |
| Change in CO abundance from late-stage chemistry | <1 | not stated | percent of total CO abundance | 4 | However this accounts for less than 1% of the total abundance of CO |

## Qualitative findings

- Bright CH3CN and C2H emission from the cold midplane is proposed as a signpost of an evolved dust population and late-stage planet formation  
  > "Thus bright hydrocarbon and nitrile (i.e. C$_{2}$H, CH$_{3}$CN) emission from the cold midplane acts as a signpost for an evolved dust population" (Main)
- Models with C/O above one and depleted small dust reproduce observed CH3CN, HC3N and HCN profiles in HD 163296, and TW Hya CH3CN lines with C/O = 1.0 and slight small-dust depletion  
  > "given a C/O ratio equal to 1.0" (Supplementary Information: TW Hya)

## Claim tuples

- H: Gas-phase CH3CN abundance in cold midplane gas depends on gas-to-dust ratio and carbon abundance | E: Single-point midplane models varying gas-to-dust ratio, initial carbon and other variables | R: CH3CN abundance was most sensitive to gas-to-dust ratio and initial gas-phase carbon abundance | F: A higher gas-to-dust ratio and carbon-rich gas favour gas-phase CH3CN | **supported**
- H: UV-driven photochemistry with enhanced C/O and depleted small dust explains bright CH3CN, HC3N and HCN from cold gas in HD 163296 | E: RAC2D thermo-chemical model with small dust depleted by 10 and C/O 1-2, ray-traced and compared to MAPS radial profiles | R: Roughly reproduces line ratios and fluxes of the radial intensity profiles; inner emission slightly too bright | F: Late-stage UV-dominated chemistry accounts for the observations | **supported**
- H: The same mechanism applies to a second evolved disk | E: TW Hya model with slight small-dust depletion and C/O = 1.0 compared to CH3CN lines | R: Reproduces the available CH3CN lines | F: TW Hya is additional evidence for the evolved chemistry proposal | **supported**
- H: Small-dust depletion increases ionisation and MRI activity | E: Re and Am evaluated for early-stage and late-stage HD 163296 models | R: Thirteen times more MRI-active mass; midplane activity extends from 4 au to about 10 au | F: Late-stage chemistry could promote accretion in older disks | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Single-point models suggested a higher gas/dust ratio and carbon content, so full-disk thermo-chemical codes were used  
  > "After our results from the modeling suggested a higher gas/dust ratio and carbon content, we turned to more comprehensive thermo-chemical codes which model the thermal physics and chemical evolution throughout the whole disk." (Methods: Modeling)
- Alternative: Grain-surface chemistry with efficient photodesorption disfavoured by laboratory efficiencies orders of magnitude lower  
  > "Laboratory experiments find an intact photodesorption efficiency of $\textrm{CH}_{3}\textrm{CN}$ to be orders of magnitude less efficient" (Main)
- Alternative: Carbon excess from CO destruction disfavoured because it supplies equal carbon and oxygen  
  > "Additionally, CO destruction would supply equal amounts of carbon and oxygen, while we seek to enhance carbon over oxygen." (Results)
- How they decided it was enough: Models run to 1 Myr, when CH3CN and HC3N chemistry reaches equilibrium  
  > "We run our thermo-chemical model for 1 Myr as the $\textrm{CH}_{3}\textrm{CN}$ and $\textrm{HC}_{3}\textrm{N}$ chemistry reaches an equilibrium after this time period" (Methods: Chemical Reactions)
- Limitation (authors): Inner-disk HCN and CH3CN emission remains slightly brighter than observed  
  > "The inner disk emission remains slightly brighter than observed in HCN and" (Results)
- Limitation (authors): Dust mass, grain size and size distribution are degenerate, giving dust-mass uncertainty of at least a factor of 10  
  > "The total population mass, grain size, and how the grain sizes are distributed are strongly degenerate and can result in uncertainties of the dust mass by a factor of at least 10." (Supplementary Information: SED Degeneracy)
- Limitation (authors): MRI prediction not yet compared against low observed turbulence  
  > "It is not yet clear whether our MRI prediction is in tension with the observational evidence of low turbulence in HD 163296" (Supplementary Information: MRI Instability)
- Caveat (inferred, ours): Small-dust depletion factor and C/O were tuned to match profiles and are not fitted with uncertainties or a stated goodness-of-fit
- Caveat (inferred, ours): Model is mostly compared by eye ('roughly reproduces') to radial profiles of two disks
- Caveat (inferred, ours): Herbig versus T Tauri stellar UV differences are confounded with disk age
- Caveat (inferred, ours): Alternative explanations (e.g. grain-surface chemistry parameters) were not quantitatively explored

## Reproducibility

- Data public (paper): MAPS data public via alma-maps.info; TW Hya data via data-rich figures in earlier paper  
  > "The data that support the findings of this study can be obtained as part of the MAPS program and are publicly available via alma-maps.info." (Data Availability)
- Products in archive: _not stated_
- Code: RAC2D, RADMC-3D and GoFish are public; TORUS is private  
  > "This study relied on the following publicly available coding packages: rac2d: https://github.com/fjdu/rac-2d, RADMC-3D: https://www.ita.uni-heidelberg.de/ dullemond/software/radmc-3d/, and GoFish: https://github.com/richteague/gofish." (Code availability); "TORUS is a private code developed by Tim Harries and collaborators." (Code availability)
- Missing: RAC2D model input files and full parameter set for the final depleted model
- Missing: Exact carbon abundances and transitions modelled
- Missing: tclean and RADMC-3D settings
- Missing: Model output radial profiles as numeric tables
- Data volume (inferred): Public MAPS HD 163296 cubes for three molecules (several GB) plus TW Hya Band 6 data; modelling is the main cost, not data volume
- Score (inferred): 2/5, Observational data are public, but the paper is model-driven with key set-up deferred to earlier papers, no full model parameters for the final run and no numeric goodness-of-fit.
- Rediscovery candidate: no, Main results come from thermo-chemical modelling with unstated inputs and qualitative comparison, not a numeric recipe redoable from ALMA data.

## Links

- Method: Czekala et al. 2021 (cite: Czekala21) (MAPS observations and imaging for HD 163296)
- Method: Law et al. 2021 (cite: Law21rad) (Radial profiles)
- Method: Oberg et al. 2021 (cite: Oberg21) (MAPS large program overview)
- Method: Loomis et al. 2018a (cite: Loomis18) (TW Hya CH3CN observations and imaging)
- Method: Calahan et al 2021a (cite: Calahan21a) (RAC2D description and TW Hya model)
- Method: Calahan et al. 2021b (cite: Calahan21b) (HD 163296 thermo-chemical model)
- Method: Zhang et al. 2021 (cite: Zhang21) (HD 163296 disk structure model)
- Method: Bosman et al. 2018 (cite: Bosman18) (Chemical network)
- Companion: Ilee et al. 2021 (cite: Ilee21) (MAPS CH3CN and HC3N analysis)
- Companion: Bosman et al. 2021 (cite: Bosman21a) (C2H and carbon-rich gas in MAPS disks)
- Related: MAPS (Molecules with ALMA at Planet-forming Scales) large program

## Checks

```json
{
 "quotes": 90,
 "quotes_ok": 90,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 107,
  "stated": 64,
  "rate": 0.598
 },
 "evidence_ok": true
}
```
