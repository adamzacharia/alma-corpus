# Thermal Properties of the Leading Hemisphere of Callisto Inferred from ALMA Observations

`2023PSJ.....4..142C` | The Planetary Science Journal 2023 | first author: Camarca, Maria | arXiv: 2308.13621 | DOI: 10.3847/PSJ/aceb68

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: What are the global thermal properties (thermal inertia, emissivity) and local thermal anomalies of Callisto's leading hemisphere at 0.87 mm?  
  > "Global surface properties were derived from the observation using a thermophysical model (cite: de_kleer_ganymedes_2021) constrained by spacecraft data." (abstract)
- Target **Callisto (leading hemisphere)**: coordinates _not stated_; z/distance angular diameter ~1.05 arcsec; sub-observer longitude 50 W  
  > "The angular diameter of Callisto during data acquisition was $\sim$$1.05^{\prime\prime}$, so $\sim$6 resolution elements across the disk were achieved" (2.1 Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00691.S
- bands: Band 7 (0.87 mm, 343 GHz)  
  > "The data were taken using the Band 7 receiver at a central frequency of 343 GHz (0.87 mm)" (2.1 Observations)
- frequencies and spectral setup: four spectral windows spanning ~8 GHz  
  > "with four spectral windows collectively spanning $\sim$8 GHz and an on-source integration time of 121 s" (2.1 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C-5, 39 12-m antennas  
  > "the array was in configuration C-5 with 39 12-m antennae" (2.1 Observations)
- baselines: 18.6 m to 1.1 km  
  > "The baselines ranged from 18.6 m to 1.1 km, affording an angular resolution of $\sim$$0.16^{\prime\prime}$." (2.1 Observations)
- angular resolution: ~0.16 arcsec  
  > "affording an angular resolution of $\sim$$0.16^{\prime\prime}$" (2.1 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 121 s  
  > "an on-source integration time of 121 s" (2.1 Observations)
- observing dates: 2016 November 01  
  > "We observed the leading hemisphere of Callisto using ALMA on 2016 November 01." (2.1 Observations)
- pi or archival as stated: _not stated_
- Other facility **Voyager and USGS mosaic**: greyscale map and spectral albedos for albedo map  
  > "a high-resolution ($\sim$1 km) USGS greyscale map of Callisto’s surface[^3], with (2) spectral albedos measured at 0.35, 0.41, 0.48, and 0.59 µm obtained at 20 locations by Voyager" (3.2 Albedo Map)
- External data: Voyager spectral albedos at 20 locations  
  > "spectral albedos measured at 0.35, 0.41, 0.48, and 0.59 µm obtained at 20 locations by Voyager (cite: johnson_global_1983)" (3.2 Albedo Map) [from (cite: johnson_global_1983)]
- External data: phase integral of 0.51  
  > "multiplied by a phase integral of 0.51 (cite: buratti_ganymede_1991)" (3.2 Albedo Map) [from (cite: buratti_ganymede_1991)]
- External data: 0.6-2.5 µm disk-integrated reflectance used to extend albedo spectrum  
  > "we extended the spectral coverage by scaling  0.6 – 2.5 µm disk-integrated reflections to our data (cite: clark_galilean_1980)" (3.2 Albedo Map) [from (cite: clark_galilean_1980)]
- Simulation/model as data: 1D thermophysical heat-diffusion model with radiative transfer, from de Kleer et al. 2021  
  > "For full details of the model, including a full description of the radiative transfer, dielectric properties, and other key processes and equations, see Section 3 of (cite: de_kleer_ganymedes_2021)." (3 Thermophysical Model)

## Processing

### Calibration

- pipeline or manual: pipeline-calibrated measurement set; flux calibration checked, no manual correction needed  
  > "the data were provided as a pipeline-calibrated measurement set containing the visibilities" (2.2 Data Analysis); "indicated it is not necessary to correct the pipeline calibration of these data." (2.3 ALMA Flux Density Calibration Check)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1256-0547  
  > "The quasar used for flux calibration was J1256-0547" (2.3 ALMA Flux Density Calibration Check)
- flux scale uncertainty: 5%  
  > "which was parameterized by a 5% error of the total flux density" (2.2 Data Analysis)
- self calibration: iterative phase-only self-cal, solints from full integration (>121 s) down to 2 s  
  > "This cycle of cleaning and computing gains continued down to an interval of 2 s, at which the image SNR ceased to substantially improve." (2.2 Data Analysis)

### Imaging

- task: CASA tclean, multi-frequency synthesis over 8 GHz  
  > "we integrated the signal over the entire 8 GHz of bandwidth using multi-frequency synthesis" (2.2 Data Analysis)
- deconvolver: Clark  
  > "used the "Clark" deconvolver" (2.2 Data Analysis)
- weighting robust: Briggs, robust = 0.0  
  > "we adopted a Briggs weighting scheme with a robust parameter of 0.0" (2.2 Data Analysis)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied to self-calibrated image  
  > "A primary beam correction was applied to the self-calibrated image product." (2.2 Data Analysis)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.16" x 0.19"  
  > "The dimensions of the final clean beam were $0.16^{\prime\prime} \times 0.19^{\prime\prime}$." (2.2 Data Analysis)
- final rms: 0.585 mJy/beam (~0.2 K)  
  > "was 0.585 mJy/beam, or about 0.2 K" (2.2 Data Analysis)

### Inherited from earlier work

- thermophysical model details  
  > "see Section 3 of (cite: de_kleer_ganymedes_2021)" (3 Thermophysical Model) [from (cite: de_kleer_ganymedes_2021)]
- cost function for goodness of fit  
  > "Details for applying the cost function to ALMA data are described in Section 3.4 of (cite: de_kleer_surface_2021)" (3.1 Two-Component Mixtures) [from (cite: de_kleer_surface_2021)]
- albedo map approach  
  > "following (cite: trumbo_alma_2017; trumbo_alma_2018) and (cite: de_kleer_ganymedes_2021)" (3.2 Albedo Map) [from (cite: trumbo_alma_2017; trumbo_alma_2018), (cite: de_kleer_ganymedes_2021)]

### Not stated but needed to reproduce (our reading)

- tclean image size, cell size, niter, threshold and masks
- startmodel Lambertian disk parameters
- intermediate self-cal solints and number of iterations
- CASA version
- emissivity/thermal model input parameters (density, heat capacity, dielectrics, roughness)
- exact cost function and chi-squared cutoff implementation
- thermophysical model code availability
- quasar J1232-0224 role details

## Analysis recipe

1. **self-calibrate and image**: iterative phase-only self-calibration with tclean and gaincal, starting from a Lambertian disk model  
  > "Our phase-only self-calibration using CASA followed as such: for the first round of imaging, a Lambertian disk scaled to the size and brightness temperature of Callisto was used as a startmodel" (2.2 Data Analysis)
   - software: CASA, tclean, gaincal, applycal
   - parameter: Briggs robust 0.0, Clark deconvolver, solint down to 2 s  
  > "we adopted a Briggs weighting scheme with a robust parameter of 0.0, and used the "Clark" deconvolver" (2.2 Data Analysis)
   - fitting: _not stated_
   - validation: dynamic range ~580  
  > "A dynamic range of $\sim$580 (peak flux/rms in units of Jy/beam) was obtained for the final image." (2.2 Data Analysis)
2. **disk-integrated flux and Tb**: fit uniform disk to visibilities with uvmodelfit excluding baselines >200 m; invert Planck equation with CMB subtraction  
  > "fit with Bessel functions using the CASA task `uvmodelfit` assuming a uniform disk model, fitting to all spectral windows, and by excluding baselines $>$200 m" (2.2 Data Analysis)
   - software: CASA uvmodelfit
   - assumption: T_cmb = 2.7 K; 5% flux scale error  
  > "$T_{cmb}$ is the cosmic microwave background (2.7 K)" (2.2 Data Analysis)
   - fitting: uniform-disk visibility fit  
  > "The visibilities were fit with Bessel functions using the CASA task `uvmodelfit` assuming a uniform disk model, fitting to all spectral windows" (Methods, Data Analysis)
   - validation: compared with prior disk-integrated measurements  
  > "Overall, our result agrees well with past work" (4.1 Disk-Integrated Brightness Temperature)
3. **single thermal inertia model fits**: 1D heat diffusion thermophysical model run over Gamma 15-2000, compared with beam-convolved model image  
  > "we performed model runs over a wide range of thermal inertias, ranging from $\Gamma$ = 15 to $\Gamma$ = 2000" (3 Thermophysical Model)
   - parameter: ~15 Callisto days, steps >=1/500 day, bolometric albedo map from spacecraft  
  > "The model was evolved over $\sim$15 Callisto days (1 Callisto day = 16.69 Earth days) in time steps of at least 1/500 of a day" (3 Thermophysical Model)
   - assumption: no heat flow at depth; albedo fixed  
  > "the boundary conditions adopted no heat flow at depth and solar insolation at the distance of Callisto" (3 Thermophysical Model)
   - fitting: least-squares emissivity; cost function accounting for number of beams  
  > "The emissivity for each mixed model was obtained by performing a least-squares analysis, with the off-disk flux masked out for the calculation." (3.1 Two-Component Mixtures)
   - validation: residual maps; tested porosity, refraction, ice/dust ratio  
  > "we tested other model parameters, including the porosity, treatment of refraction, and ice to dust ratio; none of these changes provided a significantly better fit." (4.2 Global Properties: Single Thermal Inertia)
4. **two-component thermal inertia mixtures**: linearly combine low (15-400) and high (500-2000) Gamma models in 10% mixing steps (11 mixtures), convolve with beam, subtract from data  
  > "we created 11 linear mixtures that ranged from 0$\%$ $\Gamma_{lower}$ + 100$\%$ $\Gamma_{higher}$, to 100$\%$ $\Gamma_{lower}$ + 0$\%$ $\Gamma_{higher}$" (3.1 Two-Component Mixtures)
   - parameter: acceptance cutoff 2x minimum chi-squared  
  > "The model parameters that satisfied a cutoff of 2$\times$ the minimum chi-squared ($\chi^2$)" (4.3 Global Properties: Two Thermal Inertias)
   - assumption: horizontal segregation of the two components  
  > "while ours is implemented with horizontal segregation" (4.3 Global Properties: Two Thermal Inertias)
   - fitting: grid search with chi-squared cutoff  
  > "The model parameters that satisfied a cutoff of 2$\times$ the minimum chi-squared ($\chi^2$) allow $\Gamma_{lower}$ = 15-50 and $\Gamma_{higher}$ = 1200-2000" (Results & Discussion, Global Properties: Two Thermal Inertias)
   - validation: max deviations of best two-component models ~2-3 K vs ±6 K for endmembers  
  > "the maximum deviations for the best-fitting two-component models are $\sim$2-3 K" (4.3 Global Properties: Two Thermal Inertias)
5. **local thermal residuals**: inspect data minus model residual maps against geologic units  
  > "we also highlight terrain-specific thermal anomalies that are robust to model parameter changes" (4.4 Local Thermal Residuals)
   - fitting: _not stated_
   - validation: anomaly not aligned with beam elongation  
  > "which is a different direction than the ALMA beam elongation and therefore not an artifact of the non-circular resolution element" (4.4.1 Valhalla Impact Basin)

## Software

- **CASA** : self-calibration, imaging, uvmodelfit  
  > "To conduct this processing, we used the Common Astronomy Software Application (CASA) package" (2.2 Data Analysis)
- **tclean** : imaging  
  > "used as a startmodel for the `tclean` task" (2.2 Data Analysis)
- **uvmodelfit** : disk-integrated flux from visibilities  
  > "using the CASA task `uvmodelfit` assuming a uniform disk model" (2.2 Data Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| disk-integrated flux density | 8.03 | 0.40 | Jy | 2 | is 8.03 $\pm$ 0.40 Jy at 343.5 GHz (0.87 mm), which is equivalent to a brightness temperature of 116 $\pm$ 5 K |
| disk-integrated brightness temperature | 116 | 5 | K | 2 | brightness temperature of 116 $\pm$ 5 K |
| single-Gamma best fit | 600-1800 (emissivity 0.91-0.93) | not stated | J m^-2 K^-1 s^-1/2 | 3 | $\Gamma$ = 600-1800, with emissivities of 0.91-0.93 |
| two-component Gamma_lower and Gamma_higher | 15-50 and 1200-2000 | not stated | J m^-2 K^-1 s^-1/2 | 4 | allow $\Gamma_{lower}$ = 15-50 and $\Gamma_{higher}$ = 1200-2000 |
| emissivity (two-component) | 0.89-0.91 | not stated | dimensionless | 4 | with best-fit global spectral emissivities of 0.89-0.91 |
| mixing ratio Gamma_higher | 50-70% | not stated | % | 4 | with ranges varying from 70-50%, compared to 30-50% for $\Gamma_{lower}$ |
| Valhalla cold residual vs model | 2-3 | not stated | K | 5 | about by $\sim$2-3 K compared to model predictions |
| Adlinda/Heimdall/Lofn cold residual | 3-4 | not stated | K | 5 | diverges from model predictions by about 3-4 K (so SNR $\sim$15-20) |

## Qualitative findings

- Warm L-shaped residual in mid-latitudes of leading hemisphere possibly from micrometeorite texturization  
  > "it is possible the local regolith has been texturized to a less-compact material, perhaps due to micrometeorite bombardment" (4.4.3 Additional Localized Thermal Anomalies)

## Claim tuples

- H: Can a single thermal inertia describe Callisto's 0.87 mm emission? | E: fit single-Gamma and two-Gamma mixture thermophysical models | R: single-Gamma leaves systematic residuals; two-Gamma gives 15-50 and 1200-2000, deviations 2-3 K | F: two-component surface fits better | **supported**
- H: Do large impact basins show thermal anomalies? | E: residual maps vs geology | R: cold ~3 K spots at Valhalla and Adlinda/Heimdall/Lofn | F: higher thermal inertia or lower emissivity material | **supported**
- H: Does exogenic sculpting affect the leading hemisphere? | E: examine warm L-shaped residual | R: warm region at mid-latitudes | F: possibly regolith change from micrometeorite bombardment; difficult to confirm | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: single thermal inertia models, rough/smooth surface treatments, porosity, refraction and ice-to-dust changes did not fit adequately  
  > "no single model could fit both parts, regardless of treatment of the surface emission incidence angle dependence" (3.1 Two-Component Mixtures)
- How they decided it was enough: _not stated_
- Limitation (authors): cost function formally limited to independent data points  
  > "we note that the cost function is formally limited to data sets with independent data points." (3.1 Two-Component Mixtures)
- Limitation (authors): single observation of leading hemisphere only  
  > "However, such a hypothesis is difficult to confirm in the context of a single thermal observation." (5 Conclusion)
- Caveat (inferred, ours): Gamma values degenerate at high inertia
- Caveat (inferred, ours): only ~6 resolution elements so mixing model degenerate
- Caveat (inferred, ours): single frequency cannot test vertical stratification
- Caveat (inferred, ours): no formal parameter uncertainties beyond chi-squared cutoff

## Reproducibility

- Data public (paper): ALMA data cited with project code 2016.1.00691.S  
  > "This paper makes use of the following ALMA data: ADS/ JAO.ALMA#2016.1.00691.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: thermophysical model code and parameters
- Missing: tclean imaging parameters
- Missing: self-cal intermediate solints
- Data volume (inferred): ~5-20 GB
- Score (inferred): 5/5, Data public and imaging steps described, but thermal model code and many parameters are not provided.
- Rediscovery candidate: no, Thermophysical model is external and unreleased in this paper, so full recipe is not reproducible; flux density could be redone.

## Links

- Method: (cite: de_kleer_ganymedes_2021) (thermophysical model and ALMA analysis approach)
- Method: (cite: de_kleer_surface_2021) (cost function)
- Companion: (cite: trumbo_alma_2018) (ALMA Europa thermal study)
- Related: JUICE

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
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
  "facts": 79,
  "stated": 54,
  "rate": 0.684
 },
 "evidence_ok": true
}
```
