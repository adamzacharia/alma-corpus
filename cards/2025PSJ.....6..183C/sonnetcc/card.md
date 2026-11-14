# A Multifrequency Global View of Callisto's Thermal Properties from ALMA

`2025PSJ.....6..183C` | The Planetary Science Journal 2025 | first author: Camarca, Maria | arXiv: 2507.12671 | DOI: 10.3847/PSJ/ade7ee

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: What are the global thermophysical properties (thermal inertia, emissivity, electrical skin depth) and local thermal anomalies of Callisto's leading and trailing hemispheres, from multi-frequency ALMA maps?  
  > "In this work, we present the first global set of high-resolution thermal observations of Callisto using ALMA by mapping the leading and trailing hemispheres at 3 mm (97 GHz), 1.3 mm (233 GHz), and 0.87 mm (343 GHz)." (Introduction)
- Target **Callisto (leading and trailing hemispheres)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00691.S
- bands: Band 3 (97 GHz, 3 mm), Band 6 (233 GHz, 1.3 mm), Band 7 (343 GHz, 0.87 mm)  
  > "Each hemisphere has spectral coverage in three receiver bands with central frequencies of 97 GHz" (Observations)
- frequencies and spectral setup: four spectral windows per band  
  > "Within each receiver band, spectral coverage spanned four spectral windows with collective bandwidth of" (Observations)
- continuum bandwidth: entire 8 GHz of bandwidth per band, multi-frequency synthesis  
  > "In each band, we integrated the signal over the entire 8 GHz of bandwidth using multi-frequency synthesis" (Data Analysis)
- arrays: main ALMA array (12-m antennas)  
  > "The main ALMA array is composed of 50 12-m radio/sub-mm antennas linked via a correlator to function as an interferometer" (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.09-0.24 arcsec, ~420-1100 km at Callisto  
  > "The angular resolution achieved for these observations ranged from 0.09″-0.24″" (abstract)
- max recoverable scale: _not stated_
- sensitivity: final image rms ~0.20-1.7 K  
  > "is reported, with values ranging from about 0.20-1.7 K." (Data Analysis)
- time on source: ~121 s (Bands 6 and 7) to ~300 s (Band 3)  
  > "on-source integration times of 121 s for Bands 6 and 7 to 300 s for the Band 3 observations" (Observations)
- observing dates: seven observations, 2016 October 24 to 2017 October 3  
  > "We present seven observations of Callisto’s leading and trailing hemispheres obtained between 2016 October 24 and 2017 October 3" (Observations)
- pi or archival as stated: Program 2016.1.00691.S, P.I. de Kleer  
  > "(Program 2016.1.00691.S, P.I. de Kleer)" (Observations)
- Other facility **ALMA calibrator catalogue**: time-resolved J1256-0547 flux densities used to check the pipeline flux scale  
  > "were downloaded from the ALMA calibrator catalogue." (ALMA Pipeline Flux Density Calibration Check)
- Other facility **JWST NIRSpec (published results)**: CO2 band depth and gas column maps used for comparison with the cold anomaly  
  > "These data provide context for Callisto JWST results (cite: cartwright_revealing_2024)" (abstract)
- External data: spacecraft-data constrained Bond albedo map used as the upper boundary condition  
  > "based on spatially varying bond albedo (we use the same spacecraft-data constrained albedo map published by (cite: camarca_thermal_2023))" (Thermophysical Model) [from (cite: camarca_thermal_2023)]
- External data: geologic map of Callisto used to interpret residuals  
  > "Based on the (cite: greeley_geology_2001) geologic map, the disk in-view for the 97 GHz trailing hemisphere image does not sample any major geologic units." (Additional local residuals) [from (cite: greeley_geology_2001)]
- External data: earlier 343 GHz leading hemisphere measurement, results and residuals  
  > "Consistent with what was previously reported by (cite: camarca_thermal_2023) for the 0.87 mm leading hemisphere measurement" (Disk-Averaged Brightness Temperature) [from (cite: camarca_thermal_2023)]
- Simulation/model as data: grids of thermophysical models (single-Gamma, two-Gamma, variable electrical skin depth) compared with the data  
  > "We model the data using a thermophysical model previously used for ALMA observations of the Galilean satellites" (Thermophysical Model)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline flux scale kept, no manual flux correction; then self-calibration  
  > "Our inspection of a year-long range of J1256-0547 observations demonstrated consistency with the values adopted by the pipeline, and we did not make any manual corrections to the flux density scale calibration." (ALMA Pipeline Flux Density Calibration Check)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: quasar J1256-0547  
  > "For all of our observations, the quasar J1256-0547 was used for flux density scale calibration." (ALMA Pipeline Flux Density Calibration Check)
- flux scale uncertainty: 5% of total flux density  
  > "which were parameterized by a 5% error of the total flux density, and the visibility fitting errors." (Data Analysis)
- self calibration: phase-only, iterative with tclean, solint from full integration time down to 2 s  
  > "Our phase-only self-calibration using CASA followed as such" (Data Analysis); "This cycle of cleaning and computing gains continued down to an interval of 2 s" (Data Analysis)

### Imaging

- task: tclean with Lambertian disk startmodel  
  > "a Lambertian disk scaled to the size and brightness temperature of Callisto was used as a `startmodel` for the `tclean` task" (Data Analysis)
- deconvolver: Clark  
  > "and used the “Clark" deconvolver" (Data Analysis)
- weighting robust: Briggs, robust = 0.0  
  > "we adopted a Briggs weighting scheme (cite: briggs_high_1995) with a robust parameter of 0.0" (Data Analysis)
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
- final beam: 0.09-0.24 arcsec; per-observation beams in Table 1  
  > "The dimensions of the final clean beams are included in Table" (Data Analysis)
- final rms: ~0.20-1.7 K  
  > "is reported, with values ranging from about 0.20-1.7 K." (Data Analysis)

### Inherited from earlier work

- MS calibration and imaging routines for Solar System interferometric data  
  > "we followed established routines for calibrating and imaging solar system interferometric data (e.g., see (cite: thelen_subsurface_2024; camarca_thermal_2023; de_kleer_ganymedes_2021))" (Data Analysis) [from (cite: thelen_subsurface_2024; camarca_thermal_2023; de_kleer_ganymedes_2021)]
- thermophysical model  
  > "which is described in detail in Section 3 of (cite: de_kleer_ganymedes_2021)" (Thermophysical Model) [from (cite: de_kleer_ganymedes_2021)]
- two-Gamma modelling procedure  
  > "using a procedure identical to that described in Section 3.1 of (cite: camarca_thermal_2023)" (Thermophysical Model) [from (cite: camarca_thermal_2023)]
- albedo map  
  > "we use the same spacecraft-data constrained albedo map published by (cite: camarca_thermal_2023)" (Thermophysical Model) [from (cite: camarca_thermal_2023)]
- cost function applied to ALMA data  
  > "For additional details on applying the cost function to ALMA data, see Section 3.4 of (cite: de_kleer_surface_2021)." (Thermophysical Model) [from (cite: de_kleer_surface_2021)]
- brightness temperature inversion equation  
  > "was calculated by inverting the following equation (see Appendix A in (cite: de_pater_neptunes_2014)):" (Data Analysis) [from (cite: de_pater_neptunes_2014)]
- range of absorptivity scaling factors tested  
  > "for interpreting Europa ALMA data performed by (cite: thelen_subsurface_2024)." (Thermophysical Model) [from (cite: thelen_subsurface_2024)]

### Not stated but needed to reproduce (our reading)

- CASA version used for imaging and self-calibration
- Image size, cell size, clean masks, iteration counts and thresholds for tclean
- Radius, brightness temperature and sampling of the Lambertian startmodel disk
- Intermediate self-calibration solution intervals between the full integration and 2 s, and number of cycles
- Flagging, ephemeris handling and any UV range cuts before imaging and self-calibration
- Starting parameters and fit settings for uvmodelfit
- Grid spacing in Gamma, emissivity and a_scale, and relative-percentage steps for the two-Gamma mixtures
- Thermophysical model code and the bond albedo map files
- Density, heat capacity and conductivity prescriptions in the 1D heat equation
- Beam convolution details and pixel-per-beam values used for N_dat
- Value of sigma in the chi-squared cost function
- Adopted Callisto radius and distance for each observation

## Analysis recipe

1. **self-calibrate and image the visibilities**: iterative cycle of tclean imaging and phase-only gain calibration, continuing until the image SNR stopped improving  
  > "The imaging routine for these datasets consisted of an iterative cycle of imaging and self-calibration." (Data Analysis)
   - software: CASA, tclean, gaincal, applycal
   - parameter: Briggs weighting, robust = 0.0, Clark deconvolver  
  > "we adopted a Briggs weighting scheme (cite: briggs_high_1995) with a robust parameter of 0.0" (Data Analysis)
   - parameter: signal integrated over the entire 8 GHz bandwidth, multi-frequency synthesis  
  > "In each band, we integrated the signal over the entire 8 GHz of bandwidth using multi-frequency synthesis" (Data Analysis)
   - parameter: gain solution interval from the full integration time down to 2 s  
  > "This cycle of cleaning and computing gains continued down to an interval of 2 s" (Data Analysis)
   - assumption: Callisto modelled as a Lambertian disk for the first startmodel  
  > "a Lambertian disk scaled to the size and brightness temperature of Callisto was used as a `startmodel` for the `tclean` task" (Data Analysis)
   - fitting: _not stated_
   - validation: stopped at 2 s because image SNR no longer improved  
  > "at shorter time intervals the image SNR ceased to substantially improve" (Data Analysis)
2. **check the pipeline flux density scale**: compare J1256-0547 calibrator catalogue fluxes with the setjy amplitude scale used by the pipeline on each observation day  
  > "These time-resolved measurements were compared to the `setjy` visibility amplitude scale set by the pipeline scripts for each day of our observations." (ALMA Pipeline Flux Density Calibration Check)
   - software: setjy, ALMA calibrator catalogue
   - fitting: _not stated_
   - validation: consistent with pipeline values, no manual correction needed  
  > "demonstrated consistency with the values adopted by the pipeline" (ALMA Pipeline Flux Density Calibration Check)
3. **measure disk-integrated flux density and disk-averaged brightness temperature**: fit visibilities with a uniform disk using uvmodelfit, then invert the flux-density equation to get Tb  
  > "The visibilities were fit with Bessel functions using the CASA task `uvmodelfit` assuming a uniform disk model, fitting to all spectral windows" (Data Analysis)
   - software: CASA, uvmodelfit
   - parameter: baselines longer than 200 m excluded  
  > "by excluding baselines $>$200 m for an optimal fit" (Data Analysis)
   - parameter: 5% flux scale error included in Tb uncertainty  
  > "which were parameterized by a 5% error of the total flux density, and the visibility fitting errors." (Data Analysis)
   - assumption: uniform disk; CMB temperature 2.7 K  
  > "and $T_{cmb}$ is the cosmic microwave background (2.7 K)" (Data Analysis)
   - fitting: _not stated_
   - validation: agrees with earlier radio measurements of Callisto  
  > "the additional ALMA measurements presented here agree well with past work." (Disk-Averaged Brightness Temperature)
4. **fit single thermal inertia and emissivity models**: 1D heat equation thermophysical model with radiative transfer, fit globally to each frequency and hemisphere independently for Gamma and emissivity  
  > "The model is then compared to the data to determine the best-fit global thermal inertia and emissivity." (Thermophysical Model); "we fit the model parameters of each frequency and hemisphere independently" (Thermophysical Model)
   - software: thermophysical model of de Kleer et al. 2021
   - parameter: model evolved ~15 Callisto days, time step at least 1/500 day  
  > "(1 Callisto day = 16.69 Earth days) in time steps of at least 1/500 of a day to allow for equilibration" (Thermophysical Model)
   - parameter: emissivity capped at 1  
  > "(values exceeding $\epsilon$ = 1 were not permitted)" (Single-Gamma Results)
   - assumption: thermal properties constant across the disk, spatial differences interpreted as time-of-day differences  
  > "under the assumption that the thermal properties are constant across the disk, we can use the fact that the local time at each individual location is different to build a global thermal emission model" (Thermophysical Model)
   - assumption: electrical properties of pure water ice, scaled by a free factor  
  > "In our implementation, the electrical properties are instead set assuming pure water ice, but are allowed to vary via a free scale factor." (Thermophysical Model)
   - assumption: zero heat flow lower boundary, solar insolation with Bond albedo map as upper boundary  
  > "the lower boundary condition is set by the assumption of zero heat flow at depth" (Thermophysical Model)
   - fitting: chi-squared cost function using number of beams on disk as N_dat; models below chi2_min(1 + sqrt(2/(N_dat-N_par))) acceptable  
  > "we divide the total number of pixels on-disk in a given observation by the number of pixels per ALMA beam" (Thermophysical Model); "were considered acceptable (cite: press_numerical_1986; hanus_thermophysical_2015)" (Thermophysical Model)
   - validation: residual maps inspected for large-scale systematics such as warm disk centre and cold limbs  
  > "the models usually failed to simultaneously fit the satellite disk center and the disk limb" (Single-Gamma Results)
5. **fit single Gamma with variable electrical skin depth**: scale the water-ice absorptivity by a_scale, constant in wavelength and temperature, and fit with Gamma  
  > "we tested varying $\delta_{elec}$ by an absorptivity scaling factor $a_{scale}$ that is constant in wavelength and in temperature" (Thermophysical Model)
   - software: thermophysical model of de Kleer et al. 2021
   - parameter: a_scale from 0.25 to 12.5  
  > "where the tested values of $a_{scale}$ ranged from 0.25 to 12.5" (Thermophysical Model)
   - fitting: _not stated_
   - validation: compared residual maps with the single-Gamma fits  
  > "For many models, allowing this parameter to vary provides an improvement over the" (Single-Gamma and Variable delta Results)
6. **fit two-Gamma mixture models**: grid of low-Gamma and high-Gamma models added linearly in Jy at variable relative percentages before beam convolution  
  > "Pairs of low-$\Gamma$ and high-$\Gamma$ models are linearly added at variable relative percentages prior to convolution with the ALMA beam." (Thermophysical Model)
   - software: thermophysical model of de Kleer et al. 2021
   - parameter: low Gamma 15-400 MKS, high Gamma 500-2000 MKS  
  > "“lower" thermal inertia models ($\Gamma$ = 15-400 MKS) and “higher" thermal inertia models ($\Gamma$ = 500-2000 MKS)" (Thermophysical Model)
   - assumption: materials of two thermal inertias mixed spatially below the resolution of the data  
  > "This task produced models that simulate materials at two thermal inertias mixed spatially below the resolution of the data." (Thermophysical Model)
   - fitting: _not stated_
   - validation: compared residual maps with single-Gamma fits  
  > "For some observations, the inclusion of a secondary thermal inertia component provided an improved fit over" (Two-Gamma Results)
7. **identify local thermal anomalies from residuals**: subtract best-fit models from data and compare residual cold and warm spots with geologic maps and JWST CO2 maps  
  > "as well as the residual maps produced by subtracting the corresponding best-fit models from the data to identify spatial variations in thermal properties" (Results & Discussion)
   - fitting: _not stated_
   - validation: cold spot near Valhalla and near Adlinda/Heimdall/Lofn seen at multiple frequencies; limb-proximity features treated with caution  
  > "its proximity to the satellite’s limb necessitates caution" (Cold Spot Near 270 W)

## Software

- **CASA** : imaging and self-calibration  
  > "We conducted our imaging using the Common Astronomy Software Application (CASA) package (cite: the_casa_team_casa_2022)." (Data Analysis)
- **tclean** : imaging with Lambertian disk startmodel  
  > "a Lambertian disk scaled to the size and brightness temperature of Callisto was used as a `startmodel` for the `tclean` task" (Data Analysis)
- **gaincal** : antenna-based complex gain corrections for self-calibration  
  > "Next, the complex antenna-based gain corrections were calculated using the CASA `gaincal` task on an interval spanning the full integration time and then applied using `applycal`." (Data Analysis)
- **applycal** : applying the self-calibration gains  
  > "on an interval spanning the full integration time and then applied using `applycal`." (Data Analysis)
- **uvmodelfit** : fit uniform disk to visibilities for disk-integrated flux density  
  > "The visibilities were fit with Bessel functions using the CASA task `uvmodelfit` assuming a uniform disk model, fitting to all spectral windows" (Data Analysis)
- **setjy** : pipeline visibility amplitude scale compared with calibrator catalogue  
  > "These time-resolved measurements were compared to the `setjy` visibility amplitude scale set by the pipeline scripts for each day of our observations." (ALMA Pipeline Flux Density Calibration Check)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk-integrated flux density range, 3 mm to 0.87 mm | 0.62-8.03 | not stated | Jy | 3 | 0.62-8.03 Jy across the wavelength range of 3 to 0.87 mm |
| Disk-averaged brightness temperature range | 106-116 | not stated | K | 3 | 106-116 K |
| Final image rms range | 0.20-1.7 | not stated | K | 1 | is reported, with values ranging from about 0.20-1.7 K. |
| Millimeter emissivity | 0.85-0.97 | not stated | dimensionless | 4 | We find that Callisto’s millimeter emissivities are high, with representative values of 0.85-0.97 |
| Single-Gamma emissivity range | 0.86 to 1.0 | not stated | dimensionless | 4 | although the range extends from 0.86 to 1.0 depending on the frequency band |
| Single-Gamma thermal inertia at 343, 233, 97 GHz | 600-1900, 100-1300 MKS, unconstrained | not stated | J m^-2 K^-1 s^-1/2 | 4 | = 600-1900 MKS, 100-1300 MKS, and unconstrained, for 343, 233, and 97 GHz respectively. |
| Single Gamma plus variable skin depth, thermal inertia at 343, 233, 97 GHz | 500-2000, 300-500, 50-2000 MKS | not stated | J m^-2 K^-1 s^-1/2 | 5 | = 500-2000, 300-500, and 50-2000 MKS for 343, 233, and 97 GHz respectively |
| Best-fit absorptivity scaling factor a_scale | ~10-12.5 (upper bound of tested range) | not stated | dimensionless | 5 | 10-12.5, which represents the upper bound of |
| Two-Gamma (lower, higher) thermal inertia at 233 GHz | (<100, unconstrained) | not stated | J m^-2 K^-1 s^-1/2 | 6 | (\<100, unconstrained) MKS for 233 GHz |
| Cold anomalies at craters relative to surroundings | 3-5 | not stated | K | 7 | brightness temperatures that are locally 3-5 K colder than surrounding terrain are associated with impact craters |
| 97 GHz trailing hemisphere cold spot near 270 W | 5-6 K colder than nearby terrain | not stated | K | 7 | the cold spot is approximately 5-6 K colder than nearby terrain |
| 97 GHz trailing cold spot near 30 N, 180 W | 1.3 K colder than disk average | not stated | K | 7 | there is a cold spot observed that is about 1.3 K colder than the disk average |

## Qualitative findings

- Brightness temperatures of leading and trailing hemispheres are the same within uncertainties at each frequency  
  > "at a given frequency are the same within uncertainties" (Disk-Averaged Brightness Temperature)
- ALMA data may not bypass Callisto's dark material blanket  
  > "Altogether, the ALMA data may offer a lower bound for the dark material blanket that is not less than" (Summary of Global Results)
- Valhalla cold spot may indicate higher thermal inertia and perhaps lower emissivity than surroundings  
  > "its thermal anomaly may be explained by the presence of a material that is either higher thermal inertia than surrounding terrain" (Conclusions)

## Claim tuples

- H: Can a single thermal inertia model describe Callisto's millimeter thermal emission? | E: Fitted single-Gamma models to each frequency and hemisphere and inspected residuals | R: Single-Gamma models left systematic residuals (warm disk centre, cold limbs) in nearly every observation | F: Single-Gamma models are not sufficient; more complex models fit better | **supported**
- H: Are Callisto's millimeter emissivities high compared to Europa and Ganymede? | E: Derived emissivity from all three model treatments at 97, 233 and 343 GHz | R: Emissivity 0.85-0.97 in all treatments, versus 0.75-0.85 for Europa and Ganymede | F: Callisto has consistently high millimeter emissivity | **supported**
- H: Are local thermal anomalies tied to impact craters? | E: Subtracted best-fit global models and compared residual cold spots with geologic features | R: Cold spots of 3-5 K at Valhalla and the Adlinda/Heimdall/Lofn complex | F: Large impact features appear as cold anomalies | **supported**
- H: Do the ALMA data sense below Callisto's dark material blanket, via frequency or hemisphere differences in thermal properties? | E: Compared best-fit thermal inertias across 97-343 GHz and between hemispheres | R: No clear trend with depth and no consistent leading/trailing difference | F: ALMA may not have bypassed the dark material blanket | **partially**
- H: Is the L-shaped warm anomaly on the leading hemisphere seen earlier at 343 GHz real? | E: Examined 233 and 97 GHz leading hemisphere residual maps | R: Warm region reproduced at 233 GHz and in the same area at 97 GHz | F: Confirmed at additional frequencies, possibly lower thermal inertia from micrometeorite bombardment | **supported**

## Reasoning

- Why this data: first global multi-frequency high-resolution ALMA maps of Callisto  
  > "In this work, we present the first global set of high-resolution thermal observations of Callisto using ALMA" (Introduction)
- Why this method: self-calibration gives higher SNR than the ALMA pipeline for Solar System objects with simple disk shapes  
  > "The use of self-calibration to address phase fluctuations typically yields higher signal-to-noise images for Solar System objects than those generated directly by the ALMA pipeline." (Data Analysis)
- Alternative: joint self-consistent porosity-based fit of all data per frequency gave a poor fit, so each dataset was fit independently with more free parameters  
  > "The motivation for the different implementation was that an approach in which all data within each frequency were jointly fit with a model that requires parameters to be physically self-consistent found a poor fit to the Callisto data." (Thermophysical Model)
- Alternative: Band 6 trailing observation of 2016 Oct 25 excluded from thermal modelling because the beam was too large  
  > "we present the calibrated image and disk-averaged quantities, but do not include it in the thermal model analysis" (Observations)
- Alternative: local property fits not attempted because each location is observed at a single local time  
  > "we refrain from attempting to fit local properties on Callisto because we do not observe individual locations at multiple times of day" (Thermophysical Model)
- How they decided it was enough: self-calibration stopped at 2 s when SNR no longer improved  
  > "at shorter time intervals the image SNR ceased to substantially improve" (Data Analysis)
- Limitation (authors): model cannot fit large-scale trailing hemisphere warm/cold structure; extra physics may be needed  
  > "may require more complex model physics (e.g., roughness) than is used by the present approach" (Local Thermal Residuals)
- Limitation (authors): self-consistent model could not fit the data, indicating missing physics  
  > "The fact that the self-consistent model implementation was not able to fit the data indicates that some physics may be missing in the model" (Thermophysical Model)
- Caveat (inferred, ours): Thermal inertia is poorly constrained at 97 GHz and often unconstrained or bimodal, so cross-frequency comparisons are weak
- Caveat (inferred, ours): a_scale best fits sit at the edge of the tested range, so the true optimum is not bracketed
- Caveat (inferred, ours): Cold spot near 270 W at 97 GHz is near the limb and seen in only one observation
- Caveat (inferred, ours): Fit parameters are degenerate between Gamma, emissivity and skin depth, and acceptance uses an ad hoc chi-squared threshold

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Thermophysical model code and albedo map are not provided with the paper
- Missing: CASA version, tclean image and mask parameters, and self-calibration intermediate solution intervals are not stated
- Missing: Grid steps for Gamma, emissivity, a_scale and two-Gamma mixing fractions are not stated
- Missing: Per-observation distance and radius values used for conversions are not stated
- Data volume (inferred): Seven short (about 2-5 min on-source) execution blocks; raw MS likely a few to tens of GB in total (estimate)
- Score (inferred): 3/5, Calibration and imaging steps are described but key CASA parameters are missing, and the thermophysical model and albedo map depend on prior papers and unreleased code
- Rediscovery candidate: no, Disk-integrated fluxes and brightness temperatures are redoable, but the thermophysical fitting recipe depends on unreleased code and unstated grid settings

## Links

- Method: (cite: de_kleer_ganymedes_2021) (Source of the thermophysical model, described in its Section 3)
- Method: (cite: camarca_thermal_2023) (Two-Gamma procedure (Section 3.1) and albedo map)
- Method: (cite: de_kleer_surface_2021) (Cost function applied to ALMA data (Section 3.4))
- Method: (cite: brogan_advanced_2018) (Detailed explanation of self-calibration)
- Method: (cite: thelen_subsurface_2024) (Processing routines and range of absorptivity scaling for Europa)
- Companion: (cite: camarca_thermal_2023) (Earlier 343 GHz leading hemisphere image of Callisto)
- Companion: (cite: trumbo_alma_2018) (ALMA Europa observations)
- Companion: (cite: de_kleer_ganymedes_2021) (ALMA Ganymede observations)
- Related: ALMA program 2016.1.00691.S (P.I. de Kleer)

## Checks

```json
{
 "quotes": 101,
 "quotes_ok": 101,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 106,
  "stated": 79,
  "rate": 0.745
 },
 "evidence_ok": true
}
```
