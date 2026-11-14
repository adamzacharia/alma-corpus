# Imaging the Jet of MWC 349A with Resolved Radio Recombination Line Emission from ALMA

`2024ApJ...971L...7M` | The Astrophysical Journal Letters 2024 | first author: Martínez-Henares, Antonio | arXiv: 2407.13681 | DOI: 10.3847/2041-8213/ad638d

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: star_formation, stellar_physics
- Question: What are the resolved structure and kinematics of the ionized disk, wind and jet of MWC 349A in H26alpha RRL and 341 GHz continuum, and does a MORELI model reproduce them?  
  > "The maser RRL emission is resolved for the first time and clearly delineates the ionized disk, wind and jet." (abstract); "we report new ALMA observations that resolve for the first time the structure of the sub-mm continuum and H26$\alpha$ RRL emission toward MWC$\,$349A" (Introduction)
- Target **MWC 349A**: coordinates phase center RA(J2000)=20h32m45.528s, Dec(J2000)=+40d39m36.623s  
  > "located at $\sim$1.2$\,$kpc (cite: cohen1985)" (Introduction); "$\alpha$(J2000)$=20^h32^m45^s.528$" (Observations and data reduction); "$\delta$(J2000)$=40^{\circ}39'36".623$" (Observations and data reduction); z/distance ~1.2 kpc  
  > "located at $\sim$1.2$\,$kpc (cite: cohen1985)" (Introduction); "$\alpha$(J2000)$=20^h32^m45^s.528$" (Observations and data reduction); "$\delta$(J2000)$=40^{\circ}39'36".623$" (Observations and data reduction); distance from Cohen et al. 1985 (cite: cohen1985)  
  > "located at $\sim$1.2$\,$kpc (cite: cohen1985)" (Introduction); "$\alpha$(J2000)$=20^h32^m45^s.528$" (Observations and data reduction); "$\delta$(J2000)$=40^{\circ}39'36".623$" (Observations and data reduction)

## Data provenance

- ALMA projects: 2019.1.01069.S
- bands: _not stated_
- frequencies and spectral setup: 2 continuum SPWs at 340.610 and 342.506 GHz (1.875 GHz each); 2 line SPWs on H26alpha (353.623 GHz): wide 1.875 GHz, 0.98 MHz (~0.82 km/s) channels; narrow 0.469 GHz, 0.24 MHz (~0.21 km/s)  
  > "two spectral windows for the continuum centered at 340.610 and 342.506$\,$GHz of 1.875$\,$GHz bandwidth" (Observations and data reduction); "two spectral windows centered on the H26$\alpha$ RRL (353.623$\,$GHz) to obtain the line emission" (Observations and data reduction)
- continuum bandwidth: two continuum SPWs of 1.875 GHz bandwidth each  
  > "two spectral windows for the continuum centered at 340.610 and 342.506$\,$GHz of 1.875$\,$GHz bandwidth" (Observations and data reduction)
- arrays: _not stated_
- configurations: C43-9/10  
  > "on 2021 September 5 and 10 in the array configuration C43-9/10" (Observations and data reduction)
- baselines: longest baseline 16200 m  
  > "(longest baseline of 16200$\,$m)" (Observations and data reduction)
- angular resolution: 0.025 x 0.012 arcsec (30 au x 14 au at 1.2 kpc), PA -7.1 deg (continuum)  
  > "The resulting synthesized beam size was of 0.025 $\times$ 0.012$\,$arcsec (30$\,$au $\times$ 14$\,$au, assuming a distance of 1.2$\,$kpc)" (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2021 September 5 and 10  
  > "on 2021 September 5 and 10 in the array configuration C43-9/10" (Observations and data reduction)
- pi or archival as stated: Project 2019.1.01069.S, PI Qizhou Zhang  
  > "(Project code 2019.1.01069.S: PI Qizhou Zhang)" (Observations and data reduction)
- Line: H (hydrogen RRL) H26alpha (353.623 GHz)
- Line: C (carbon RRL), tentative identification of additional line C26alpha (not stated)
- External data: Spectral index of the continuum, 0.64+/-0.02 (fit up to 340 GHz), used for comparison  
  > "consistent with the spectral index of 0.64$\pm$0.02 recently obtained by (cite: prasad2023)" (3.1 Continuum emission at 341 GHz) [from (cite: prasad2023)]
- External data: Electron density structure of the model (r^-2.14 dependence, double cone) taken from earlier modeling  
  > "This electron density structure is the same as the one used by (cite: baezrubio2013)" (3.4 Comparison with the non-LTE radiative transfer model) [from (cite: baezrubio2013)]
- External data: Disk opening angle and electron temperature of the ionized disk constrained from unsaturated H30alpha modeling  
  > "these parameters were previously constrained by modeling the unsaturated H30$\alpha$ RRL in (cite: baezrubio2013) and (cite: martinezhenares2023)" (3.4 Comparison with the non-LTE radiative transfer model) [from (cite: baezrubio2013); (cite: martinezhenares2023)]
- External data: Solid angle of the maser beam, 4pi/Omega = 60  
  > "with a value of $4\pi/\Omega$ = 60 (cite: thum1994)" (A.2 Saturation of the maser) [from (cite: thum1994)]
- Simulation/model as data: MORELI 3D non-LTE radiative transfer model (disk, wind, jet in a double cone) used to model the continuum and H26alpha cubes  
  > "We employed the 3D non-LTE radiative transfer code MORELI (cite: baezrubio2013) to model the continuum and H26$\alpha$ observations." (3.4 Comparison with the non-LTE radiative transfer model)

## Processing

### Calibration

- pipeline or manual: initial calibration from the ALMA pipeline  
  > "The initial calibration of the data was obtained from the ALMA pipeline." (Observations and data reduction)
- casa version: CASA 6.6.3  
  > "Common Astronomy Software Application (CASA) 6.6.3 (cite: casa)" (Software)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: nominal 10% assumed  
  > "We assume the nominal 10% uncertainty in the flux density measurement." (3.1 Continuum emission at 341 GHz)
- self calibration: continuum: five phase iterations + one amplitude, 16 s solint; line: same solint, five phase rounds + one amplitude, derived on brightest channel  
  > "The continuum self-calibration tables were obtained after five iterations of the phase calibration and one amplitude calibration, with a solution time interval of 16 seconds." (Observations and data reduction); "We used the same solution interval to obtain the line self-calibration tables after five rounds of phase and one round of amplitude calibration." (Observations and data reduction)

### Imaging

- task: CASA tclean  
  > "we imaged the data with CASA’s routine *tclean* using Briggs weighting with a *robust* parameter of 0.0" (Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.0  
  > "using Briggs weighting with a *robust* parameter of 0.0" (Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: done in the line spectral windows using line-free channels of the wide spectral window  
  > "The continuum subtraction of the line spectral windows was done with the line-free channels of the wide spectral window." (Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.025 x 0.012 arcsec, PA -7.1 deg (continuum); same size with PA -3.3 deg (narrow) and -11.7 deg (wide) line cubes  
  > "The resulting synthesized beam size was of 0.025 $\times$ 0.012$\,$arcsec" (Observations and data reduction); "same beam size with a PA of $-$3$^{\circ}$.3 and $-$11$^{\circ}$.7 for the narrow and wide spectral window line cubes, respectively" (Observations and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- MORELI model version and most parameters (disk, wind, jet) taken from the previous unresolved-RRL model; only disk inclination and jet tilts updated  
  > "using the most recent version based on previous unresolved RRL observations (cite: martinezhenares2023)" (Summary) [from (cite: martinezhenares2023)]
- Maser saturation degree parameter kept unchanged from the previous model  
  > "is the one used in the previous model (cite: martinezhenares2023) and has remained unchanged since it roughly reproduces the intensity of the line." (A.2 Saturation of the maser) [from (cite: martinezhenares2023)]
- Electron density structure of the ionized gas same as in earlier modeling of radio continuum observations  
  > "This electron density structure is the same as the one used by (cite: baezrubio2013)" (3.4 Comparison with the non-LTE radiative transfer model) [from (cite: baezrubio2013)]
- Tilt of each jet cone fitted individually, following the earlier method  
  > "hence the tilt of each cone had to be fitted individually (cite: martinezhenares2023)" (3.4 Comparison with the non-LTE radiative transfer model) [from (cite: martinezhenares2023)]

### Not stated but needed to reproduce (our reading)

- Which ALMA SPW/EBs and pipeline version were used, and which flux calibrator was used
- Self-calibration reference model/solint beyond 16 s, and the exact line-free channel ranges
- tclean parameters: cell size, image size, deconvolver, masks, threshold, niter, channel width of the line cubes, and final rms
- Exact velocity convention/rest frequency used for the C26alpha and He26alpha velocities
- How the 2.4 Jy continuum flux was measured (aperture or fit)
- Full MORELI input files/code and the exact model grid (cube sizes dx,dy,dz), plus the viewing azimuth and the model-to-observation convolution
- Quantitative criterion for choosing the disk inclination and jet tilt (the choice was made by visual inspection)

## Analysis recipe

1. **self-calibrate, continuum-subtract and image the data**: Phase+amplitude self-calibration on averaged continuum and brightest line channel, continuum subtraction using line-free channels of wide SPW, tclean imaging  
  > "We performed self-calibration with CASA on the calibrated continuum and line data with the averaged continuum and the brightest channel of the line, respectively." (Observations and data reduction)
   - software: CASA, tclean
   - parameter: solution interval 16 s; Briggs robust = 0.0  
  > "with a solution time interval of 16 seconds" (Observations and data reduction); "using Briggs weighting with a *robust* parameter of 0.0" (Observations and data reduction)
   - assumption: distance of 1.2 kpc  
  > "assuming a distance of 1.2$\,$kpc" (Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **measure the 341 GHz continuum flux and morphology**: Integrated flux compared to SMA and ALMA fluxes of Prasad et al. 2023; morphology compared to VLA and ALMA 217 GHz images  
  > "The total integrated flux measured is 2.4$\pm$0.2$\,$Jy, in agreement with the SMA and ALMA fluxes reported in (cite: prasad2023)." (3.1 Continuum emission at 341 GHz)
   - assumption: nominal 10% flux density uncertainty  
  > "We assume the nominal 10% uncertainty in the flux density measurement." (3.1 Continuum emission at 341 GHz)
   - fitting: _not stated_
   - validation: Agreement with SMA/ALMA fluxes from Prasad et al. 2023  
  > "in agreement with the SMA and ALMA fluxes reported in (cite: prasad2023)" (3.1 Continuum emission at 341 GHz)
3. **extract the H26alpha spectral profile and systemic velocity**: Spectrum integrated over an aperture matching the model integration limits; systemic velocity as central velocity between the two line peaks  
  > "The spatial aperture over which the spectra is integrated is 0.18$\times$0.17$\,$arcsec, which corresponds to the integration limits of the model" (3.2 Resolved H26alpha line emission); "as the central velocity between the peaks of the H26$\alpha$ line" (3.2 Resolved H26alpha line emission)
   - parameter: aperture 0.18 x 0.17 arcsec  
  > "The spatial aperture over which the spectra is integrated is 0.18$\times$0.17$\,$arcsec" (3.2 Resolved H26alpha line emission)
   - fitting: _not stated_
   - validation: _not stated_
4. **make velocity-binned integrated intensity maps and measure jet opening angle**: Integrated intensity maps in 13.09 km/s bins; opening angle from 2D Gaussian fit axes in the image plane  
  > "integrated intensity maps in bins of 13.09$\,$km s$^{-1}$ for the blueshifted and redshifted emission, respectively" (3.2 Resolved H26alpha line emission); "The opening angle is obtained from the major and minor axes of a 2D Gaussian fit in the image plane" (3.2 Resolved H26alpha line emission)
   - software: CASA imview
   - parameter: velocity bin width 13.09 km/s  
  > "integrated intensity maps in bins of 13.09$\,$km s$^{-1}$" (3.2 Resolved H26alpha line emission)
   - fitting: 2D Gaussian fit in image plane (no sampler or priors stated)  
  > "a 2D Gaussian fit in the image plane to the integrated intensity maps reported in Figures" (3.2 Resolved H26alpha line emission)
   - validation: _not stated_
5. **characterize the additional line near H26alpha**: Subtract H26alpha contribution pixel by pixel, integrate 353.74-353.90 GHz, identify the line from velocities and absorption  
  > "After removing the contribution from H26$\alpha$ pixel by pixel, we generated an integrated intensity map between 353.74 and 353.90$\,$GHz" (3.3 Additional line emission)
   - parameter: integration range 353.74-353.90 GHz  
  > "an integrated intensity map between 353.74 and 353.90$\,$GHz" (3.3 Additional line emission)
   - fitting: _not stated_
   - validation: Tentative identification as C26alpha from velocity match with H26alpha peaks and absorption; He26alpha not excluded  
  > "Given the absorption component and the closer radial velocity to the H26$\alpha$ line, we tentatively identify this new line as C26$\alpha$" (3.3 Additional line emission)
6. **model the continuum and H26alpha cubes with MORELI and update disk and jet orientation**: Adopt previous MORELI model; change disk inclination in 1 deg steps, then update jet tilts of each cone; choose by visual comparison with the integrated intensity maps  
  > "we changed the disk orientation in steps of 1$^{\circ}$, which also modifies the wind and jet orientation" (3.4 Comparison with the non-LTE radiative transfer model); "By visual examination of the results, we adopted a final" (3.4 Comparison with the non-LTE radiative transfer model); "As a second step, we updated the tilt of the jet following the same method." (3.4 Comparison with the non-LTE radiative transfer model)
   - software: MORELI
   - parameter: previous disk inclination 8 deg (south facing observer), updated -4 deg; jet tilts previously 16-22 deg, updated 2-6 deg  
  > "In the previous model, the disk was tilted 8$^{\circ}$ from the edge-on orientation with the southern side facing the observer." (3.4 Comparison with the non-LTE radiative transfer model); "The new model requires a tilt of 2-6$^{\circ}$, much closer to the rotation axis than before" (3.4 Comparison with the non-LTE radiative transfer model)
   - assumption: maser saturation treated with an approximation (photons from the same line of sight only); maser beam solid angle 4pi/Omega = 60  
  > "MORELI accounts for the saturation of the maser considering only photons coming from the same line of sight (cite: baezrubio2013)." (A.2 Saturation of the maser); "with a value of $4\pi/\Omega$ = 60 (cite: thum1994)" (A.2 Saturation of the maser)
   - fitting: Manual visual parameter adjustment, not a statistical fit (no sampler, priors or likelihood stated)  
  > "By visual examination of the results, we adopted a final" (3.4 Comparison with the non-LTE radiative transfer model)
   - validation: Modeled continuum flux 2.5 Jy vs observed 2.4 Jy; model integrated maps compared to observed maps at all velocities  
  > "The model reproduces very well the observed line emission across all velocities." (3.4 Comparison with the non-LTE radiative transfer model)

## Software

- **CASA** 6.6.3: self-calibration, continuum subtraction, imaging  
  > "We performed self-calibration with CASA on the calibrated continuum and line data" (Observations and data reduction)
- **tclean** : imaging  
  > "we imaged the data with CASA’s routine *tclean*" (Observations and data reduction)
- **imview** : 2D Gaussian fits to integrated intensity maps for the jet opening angle  
  > "using CASA’s *imview*" (3.2 Resolved H26alpha line emission)
- **MORELI** : 3D non-LTE radiative transfer modeling of continuum and H26alpha RRL emission  
  > "We employed the 3D non-LTE radiative transfer code MORELI (cite: baezrubio2013) to model the continuum and H26$\alpha$ observations." (3.4 Comparison with the non-LTE radiative transfer model)
- **astropy** : _not stated_
- **matplotlib** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total integrated 341 GHz continuum flux | 2.4 | 0.2 | Jy | 2 | The total integrated flux measured is 2.4$\pm$0.2$\,$Jy |
| Modeled total continuum flux | 2.5 | not stated | Jy | 6 | The total integrated flux from the model is 2.5$\,$Jy |
| Systemic velocity | 8.72 | not stated | km/s | 3 | We calculate a systemic velocity of the source of 8.72 |
| H26alpha peak radial velocities | 32.69 and -15.25 | not stated | km/s | 3 | the peaks of H26$\alpha$ are found at radial velocities of 32.69 and $-$15.25 |
| Separation between brightest pixels of the two H26alpha peaks | 0.040 | 0.012 (beam size in east-west direction) | arcsec | 5 | The separation between the brightest pixels of the H26$\alpha$ line peaks is 0.040$\pm$0.012 |
| Separation between brightest pixels of peaks 1 and 3 of the additional line | 0.031 | 0.012 (beam size in east-west direction) | arcsec | 5 | The separation between the brightest pixels for peaks 1 and 3 is 0.031$\pm$0.012 |
| Updated disk inclination angle | -4 | not stated | deg | 6 | we adopted a final $\theta_i$ value of $-$4$^{\circ}$ |
| Updated jet tilt angle (both cones) | 2-6 (northern -2, southern 6 per parameter table) | not stated | deg | 6 | The new model requires a tilt of 2-6$^{\circ}$, much closer to the rotation axis than before |
| Synthesized beam (continuum) | 0.025 x 0.012, PA -7.1 deg | not stated | arcsec | 1 | The resulting synthesized beam size was of 0.025 $\times$ 0.012$\,$arcsec |
| Model overestimate of central H26alpha line intensity | ~2 | not stated | dimensionless | 6 | whose intensity is overestimated by a factor of $\sim2$ |

## Qualitative findings

- Resolved H26alpha emission shows the ionized disk, X-shaped wind and a bipolar north-south jet; opening angle of the high-velocity lobes decreases with increasing velocity  
  > "where the opening angle of the high velocity emission decreases for increasing velocities" (3.2 Resolved H26alpha line emission)
- Continuum shows X-shaped morphology consistent with free-free emission from an expanding outflow rather than thermal dust  
  > "free-free radiation from a constant velocity expanding outflow (cite: olnon1975; panagiafelli1975) and not by thermal dust emission" (3.1 Continuum emission at 341 GHz)
- Jet axis is closer to the system rotation axis than found from unresolved data  
  > "We found that the jet orientation is closer to the rotation axis of the system than derived from spatially unresolved data." (abstract)

## Claim tuples

- H: Do ALMA longest baselines resolve the ionized disk, wind and jet of MWC 349A in RRL emission? | E: H26alpha cubes imaged at ~0.02 arcsec beam and inspected as velocity-binned integrated intensity maps | R: Disk, wind and jet components appear in resolved maps | F: The maser RRL emission clearly delineates the ionized disk, wind and jet | **supported**
- H: Is the jet poorly collimated and does collimation increase with velocity? | E: 2D Gaussian opening angles from integrated intensity maps compared with MORELI predictions | R: Opening angle decreases with increasing velocity, reproduced by the model | F: Consistent with a collimated high-velocity jet inside a wide wind | **supported**
- H: Does the resolved data require a different jet and disk orientation than the unresolved-data model? | E: Vary disk inclination in 1 deg steps and jet tilts, compare model maps with observed maps by eye | R: Disk inclination changes from 8 to -4 deg and jet tilt from 16-22 deg to 2-6 deg | F: Jet axis is much closer to the rotation axis than previously derived | **supported**
- H: Is the 341 GHz continuum dominated by free-free emission? | E: Compared X-shaped morphology to lower-frequency VLA and ALMA images and flux to earlier results | R: X-shaped continuum, flux 2.4 Jy matched by the model flux of 2.5 Jy | F: Free-free emission from a constant velocity outflow dominates, not thermal dust | **supported**
- H: What is the extra line blueward of H26alpha? | E: Pixel-by-pixel removal of H26alpha, velocity and absorption comparison for He26alpha vs C26alpha | R: Velocities of peaks closer to C26alpha; absorption component present | F: Tentatively C26alpha, with possible He26alpha contribution | **partially**

## Reasoning

- Why this data: Highest angular resolution ever used toward this source, allowing the RRL emission to be resolved  
  > "obtained with the highest angular resolution ever used toward this source" (abstract)
- Why this method: _not stated_
- Alternative: Emission from thermal dust rejected in favor of free-free emission for the continuum  
  > "free-free radiation from a constant velocity expanding outflow (cite: olnon1975; panagiafelli1975) and not by thermal dust emission" (3.1 Continuum emission at 341 GHz)
- Alternative: Helium He26alpha identification of the additional line not adopted; tentatively carbon C26alpha  
  > "we tentatively identify this new line as C26$\alpha$, although we cannot discard some contribution from He26$\alpha$." (3.3 Additional line emission)
- How they decided it was enough: Disk inclination chosen by visual examination of model results  
  > "By visual examination of the results, we adopted a final" (3.4 Comparison with the non-LTE radiative transfer model)
- Limitation (authors): Model predicts a symmetric line profile while the observed profile is asymmetric  
  > "the model predicts a symmetric line profile while the observed one is clearly asymmetric" (3.4 Comparison with the non-LTE radiative transfer model)
- Limitation (authors): Maser saturation is only approximated and the model overestimates the central line intensity  
  > "A more realistic treatment accounts for photons coming from every direction to evaluate the population in the atomic levels, such as in the model of (cite: tran2021)." (A.2 Saturation of the maser)
- Limitation (authors): Discrepancies remain between observed and modeled line emission at high velocities  
  > "We note that some discrepancies do exist between the observed and modeled line emission at these high velocities." (3.4 Comparison with the non-LTE radiative transfer model)
- Caveat (inferred, ours): Model parameters were tuned by eye in 1 deg steps with no goodness-of-fit metric or uncertainties on inclination and tilt angles
- Caveat (inferred, ours): Most MORELI parameters are fixed from earlier unresolved data, so degeneracies with the updated angles are not explored
- Caveat (inferred, ours): Line cube rms, image size and cell size are not reported, so detection significance of the faint C26alpha line cannot be judged
- Caveat (inferred, ours): Maser saturation approximation overestimates line flux by about a factor of 2

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: MORELI code or input files (not stated as released)
- Missing: Exact tclean parameters (cell, image size, masks, niter, threshold) and line cube channelization
- Missing: Flux calibrator and EB-level calibration details
- Missing: Numerical criterion or uncertainty for the model orientation angles
- Data volume (inferred): Large: two EBs of C43-9/10 with 4 spectral windows each (one 1.875 GHz line window at 0.98 MHz channels); likely several tens to hundreds of GB raw
- Score (inferred): 2/5, Project code and key imaging settings are given, but cell size, image size, masks and rms are missing, the model was tuned visually, and MORELI code availability is not stated.
- Rediscovery candidate: no, Public availability of the data and code is not stated, and the model comparison relies on visual tuning of an unreleased code, so the main results are not redoable from the paper alone.

## Links

- Method: Baez-Rubio et al. 2013 (cite: baezrubio2013) (Describes the MORELI non-LTE radiative transfer code)
- Method: Martinez-Henares et al. 2023 (cite: martinezhenares2023) (Most recent MORELI version with a jet and the previous parameter set used here)
- Companion: Prasad et al. 2023 (cite: prasad2023) (Earlier ALMA continuum and RRL observations of MWC 349A with comparison fluxes and spectral index)
- Companion: Zhang et al. 2017 (cite: zhang2017) (SMA observations showing the ionized wind rotating and expanding)
- Related: 2019.1.01069.S

## Checks

```json
{
 "quotes": 99,
 "quotes_ok": 99,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 92,
  "stated": 61,
  "rate": 0.663
 },
 "evidence_ok": true
}
```
