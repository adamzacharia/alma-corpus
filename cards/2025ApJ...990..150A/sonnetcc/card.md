# PEACHES. IV. Tracing the Formation and Evolution of C<SUB>2</SUB>H in Perseus Low-mass Protostars

`2025ApJ...990..150A` | The Astrophysical Journal 2025 | first author: Anderson, Jack G. | arXiv: 2508.03918 | DOI: 10.3847/1538-4357/adf199

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What C2H traces in Class 0/I Perseus protostars (outflow cavity walls, O-poor photochemically active gas) and whether its emission morphology evolves from extended outflow-cavity structure to compact disk-like emission  
  > "Our main goals are to (1) disambiguate what C$_2$H is tracing within the protostellar environment" (Introduction); "(2) search for evolutionary trends in the C$_2$H emission morphology, from an extended, outflow cavity structure to a more compact disk-like morphology." (Introduction)
- Target **PEACHES sample of 35 Class 0/I protostars in Perseus**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01501.S, 2017.1.01462.S, 2022.1.00303.S
- bands: _not stated_
- frequencies and spectral setup: ACA C2H spectral window only: F = 3-2, 2-1, 2-2 hyperfine components of N = 3-2, J = 5/2-3/2 at ~262.06 GHz; channel width 61.035 kHz (~0.07 km/s)  
  > "covering the F = 3–2, 2–1 and 2–2 hyperfine components of the N = 3–2, J = $\frac{5}{2}$–$\frac{3}{2}$ C$_2$H transition at $\sim$262.06 GHz, with a channel width of 61.035 kHz ($\sim$0.07 km/s)" (2.1 Observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12m array (PEACHES) plus ALMA ACA (new)  
  > "We used ALMA observations of C$_2$H and SO transitions taken with the 12m array as part of the PEACHES project" (2.1 Observations); "we also used complementary observations taken with the ALMA Atacama Compact Array (ACA; project code 2022.1.00303.S) and combined with the 12m data." (2.1 Observations)
- configurations: _not stated_
- baselines: 12m: 15-1231m; ACA adds 9-50m  
  > "The 15-1231m baselines of the PEACHES ALMA 12m array data (configuration details provided in (cite: PEACHES_I)), with the addition of the 9-50m baselines provided by the ACA observations, cover similar short-baseline distances." (2.1 Observations)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 12m : ACA actual 89:512 minutes (1:5.8)  
  > "from 1:5.8 (actual 89:512 minutes) to an effective ratio of 1:2.4 as recommended by (cite: alma_handbook)" (2.1 Observations)
- observing dates: ACA: August and September 2023  
  > "The ACA observations, taken in August and September of 2023, target the same PEACHES sources and molecular lines as the original 12m survey." (2.1 Observations)
- pi or archival as stated: _not stated_
- Line: C2H N = 3-2, J = 5/2-3/2, F = 3-2 (plus F = 2-1, 2-2 in ACA window) (~262.06 GHz)
- Line: SO N = 7-6, J = 6-5 (not stated)
- Line: CO 2-1 (SMA, from MASSES) (not stated)
- Other facility **SMA (MASSES survey)**: CO (2-1) outflow maps used in the C2H spatial analysis  
  > "The CO images used in our C$_2$H spatial analyses come from SMA observations as part of the MASS Assembly of Stellar Systems and their Evolution with the SMA (MASSES) survey" (2.1 Observations)
- External data: Bolometric temperatures and luminosities (with uncertainties) of the sources  
  > "The bolometric temperature and luminosity values and uncertainties are taken from (cite: tobin2016)" (3.3 C$_2$H Morphology in Conjunction with Protostar Evolution) [from (cite: tobin2016) Tobin et al. 2016, ApJ, 818, 73]
- External data: CO data products (SMA) taken from the MASSES data release  
  > "CO data products were taken directly from the MASSES data release web page through the Harvard data archive ((cite: MASSESData))." (2.1 Observations) [from (cite: MASSES) Stephens et al. 2019; (cite: MASSESData) Stephens 2019]

## Processing

### Calibration

- pipeline or manual: Measurement sets obtained with the ALMA pipeline; self-calibration done manually  
  > "The measurement sets were obtained using the ALMA pipeline." (2.1 Observations); "We performed two to three rounds of manual self-calibration, until minimal gains in SNR were observed." (2.1 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Two to three rounds of manual self-calibration on continuum (line-free channels averaged), only for sources with bright continuum; mean continuum SNR gain 31%; beam axes changed by 0.2% and 1% on average  
  > "Line-free channels were averaged to form continuum measurement sets, on which self-calibration was performed for sources with bright continuum emission to improve signal-to-noise ratio." (2.1 Observations); "The self-calibration process yielded an average improvement in continuum SNR of 31%" (2.1 Observations)

### Imaging

- task: CASA tclean (line and continuum images)  
  > "Line and continuum images were created using the CASA task" (2.1 Observations)
- deconvolver: _not stated_
- weighting robust: 12m-only spatial analysis: Briggs, robust = 1; 12m+ACA: Briggs, robust = 2  
  > "We produced images for our spatial analysis using Briggs weighting and a robust parameter of 1." (2.1 Observations); "The 12m and ACA data were imaged together using the ‘mosaic’ gridding parameter, Briggs weighting and a robust value of 2." (2.1 Observations)
- uv taper: _not stated_
- cell size: 0.05 arcsec  
  > "Images of 600 by 600 pixels were created, with a pixel size of 0.05"" (2.1 Observations)
- image size: 600 x 600 pixels (12m-only images)  
  > "Images of 600 by 600 pixels were created, with a pixel size of 0.05"" (2.1 Observations)
- masking: Cleaned to 2x rms from line-free channels with automasking: 12m low-noise/sidelobe/noise thresholds 1.5, 3.0, 3.75; 12m+ACA 1.5, 2.0, 4.25  
  > "Line images were cleaned to a threshold of twice the rms estimated using line free-channels, using automasking low noise, sidelobe and noise thresholds of 1.5, 3.0 and 3.75, respectively." (2.1 Observations); "using automasking low noise, sidelobe and noise thresholds of 1.5, 2.0 and 4.25, respectively." (2.1 Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: Line-free channels averaged to form continuum MS (channel ranges not given)  
  > "Line-free channels were averaged to form continuum measurement sets" (2.1 Observations)
- primary beam correction: _not stated_
- array combination: 12m + ACA imaged together with mosaic gridding; ACA visibilities downweighted by factor 0.41 (effective 12m:ACA time ratio 1:2.4)  
  > "the ACA visibilities were downweighted by a factor of 0.41 to correct for the time-on-source (ToS) ratio between the 12m and ACA observations" (2.1 Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- List of all detected molecular transitions in the PEACHES data  
  > "See (cite: PEACHES_I) for a list of all detected molecular transitions." (2.1 Observations) [from (cite: PEACHES_I)]
- 12m array configuration details  
  > "configuration details provided in (cite: PEACHES_I)" (2.1 Observations) [from (cite: PEACHES_I)]
- Effective 12m:ACA time-on-source ratio of 1:2.4 used to set the ACA downweighting  
  > "to an effective ratio of 1:2.4 as recommended by (cite: alma_handbook)" (2.1 Observations) [from (cite: alma_handbook)]
- Choice of rotational temperature range (10-50 K) informing the fixed 20 K  
  > "Our choice of rotational temperature is informed by prior studies of molecular outflows in low-mass protostars, from which rotational temperatures of 10–50K are typical" (3.2 ACA Images and Column Density Maps) [from (cite: Parker1991), (cite: Hatchell2007), (cite: Curtis2010), (cite: Dunham2010), (cite: Dunham2014)]

### Not stated but needed to reproduce (our reading)

- CASA version and ALMA pipeline version (and PEACHES_I calibration details) for the 12m and ACA data
- Self-calibration solution intervals, reference antenna, which sources were self-calibrated and the 'bright continuum' criterion
- Line-free channel ranges, continuum subtraction method and velocity ranges used for moment-0 and moment-1 maps
- tclean deconvolver, niter, scales, primary-beam correction and spectral resolution of 12m cubes
- C2H spectroscopic constants (Q(T), E_u, g_u, A_ul, hyperfine velocity offsets and relative intensities) and their source
- Per-source V_lsr, initial guesses, optimiser/likelihood and how column density uncertainties were obtained in the LTE fit
- Definition of the ray length/angular range per source, the 'clearly identified outflow' criterion and the 3 sigma extent measurement
- Velocity ranges for CO moment maps and how SMA and ALMA images were aligned/regridded
- Flux-scale uncertainty and ACA configuration details

## Analysis recipe

1. **Calibrate, self-calibrate and image lines and continuum**: Reprocess pipeline measurement sets in CASA; self-calibrate continuum for bright sources; tclean line cubes; make moment-0 maps (12m-only and 12m+ACA)  
  > "All data reprocessing and imaging was performed using CASA" (2.1 Observations); "Moment 0 maps of the lines were then created from the line data cubes by integrating over the velocities of interest." (2.1 Observations)
   - software: CASA, tclean
   - parameter: Briggs robust 1 (12m), robust 2 (12m+ACA mosaic); 600x600 px at 0.05 arcsec; clean threshold 2x rms  
  > "We produced images for our spatial analysis using Briggs weighting and a robust parameter of 1." (2.1 Observations); "Line images were cleaned to a threshold of twice the rms estimated using line free-channels" (2.1 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Compare C2H and SO spatial intensity profiles along outflow rays**: Sample moment-0 maps along rays from the continuum peak across the outflow region, average rays to get radial intensity profile per molecule, compare C2H vs SO (12m-only images)  
  > "The rays are spaced in 10 degree increments originating at the source continuum peak." (3.1 C$_2$H and SO Emission Morphology); "The emission from each individual ray is then averaged to give a spatial intensity profile" (3.1 C$_2$H and SO Emission Morphology)
   - parameter: Rays at 10 degree increments from the continuum peak; applied to sources with a discernible CO bipolar outflow  
  > "The rays are spaced in 10 degree increments originating at the source continuum peak." (3.1 C$_2$H and SO Emission Morphology)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit LTE hyperfine model to C2H spectra for column density maps**: Fit synthetic LTE spectra with Gaussian hyperfine components to regridded 12m+ACA cubes at pixels above 3 sigma in the F=3-2 moment-0; fixed Tr = 20 K, free N_T  
  > "fitting synthetic spectra to the ACA + 12m images at positions where the F= 3–2 C$_2$H emission in the moment-0 maps is above a 3$\sigma$ threshold" (2.2 C$_2$H Spectral Line Fitting); "The image cubes were first regridded by a factor of 4, i.e. squares of 2-by-2 pixels were averaged" (2.2 C$_2$H Spectral Line Fitting)
   - parameter: Fixed T = 20 K; N bounded between 1e13 and 1e16 cm^-2  
  > "We proceed with fitting column densities assuming a fixed temperature of 20K, and bound our column density values between 10^13^ and 10^16^ cm^-2^" (3.2 ACA Images and Column Density Maps)
   - assumption: Gaussian hyperfine line profiles, one common T_r, LTE  
  > "we assume that the line profiles of each hyperfine component are Gaussian, that each hyperfine component can be described with the same rotational temperature, $T_r$, and that the emission is in local thermodynamic equilibrium (LTE)." (2.2 C$_2$H Spectral Line Fitting)
   - assumption: Background temperature 2.73 K (CMB)  
  > "the cosmic microwave background (2.73 K)" (2.2 C$_2$H Spectral Line Fitting)
   - assumption: 20 K adopted at the low end of 10-50 K because outflow cavities assumed cooler than outflowing gas  
  > "We adopted a value on the low end of this range under the assumption that the outflow cavities are cooler than the outflowing gas itself." (3.2 ACA Images and Column Density Maps)
   - fitting: Per-pixel fit of N_T with T_r fixed; optimiser, priors and likelihood not stated  
  > "The maps resulting from fitting all pixels individually are shown in the top panel on the right." (3.2 ACA Images and Column Density Maps)
   - validation: Varying T_r over 10-50 K changes column densities by <5%  
  > "In any case, varying T$_r$ in our spectral line modeling within the 10–50 K range yields changes in calculated C$_2$H column densities of $<$ 5%." (3.2 ACA Images and Column Density Maps)
4. **Test C2H extent against protostellar evolutionary metrics**: Measure C2H extent as width above 3 sigma of intensity profiles; plot against bolometric temperature, bolometric luminosity and mm continuum deconvolved radius (imfit)  
  > "we estimated the overall spatial extent of the C$_2$H emission from the width above 3$\sigma$ of the intensity profiles obtained in Section" (3.3 C$_2$H Morphology in Conjunction with Protostar Evolution); "while the deconvolved radii are determined via the CASA task" (3.3 C$_2$H Morphology in Conjunction with Protostar Evolution)
   - software: CASA, imfit
   - parameter: Evolutionary proxies: mm continuum deconvolved radius, T_bol, L_bol  
  > "We therefore use the mm continuum deconvolved radius, the bolometric temperature and the bolometric luminosity as our evolutionary proxies." (3.3 C$_2$H Morphology in Conjunction with Protostar Evolution)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare C2H and CO kinematics**: Use fitted C2H F=3-2 velocity shift relative to source velocity and compare with CO moment-1 maps  
  > "From our fitted spectra we calculate the shift in the C$_2$H F=3-2 hyperfine component with respect to the source velocity, and compare that to the intensity-weighted velocities (moment-1) of the CO observations." (3.4 Kinematic Comparison of C~2~H with CO)
   - assumption: Optical depth effects assumed not to drive differences between CO and C2H red/blueshift  
  > "Therefore, we do not expect that optical depth effects are responsible for any differences in red/blueshift between the two species." (3.4 Kinematic Comparison of C~2~H with CO)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data reprocessing, self-calibration, imaging, imfit  
  > "All data reprocessing and imaging was performed using CASA" (2.1 Observations)
- **tclean** : Line and continuum imaging  
  > "Line and continuum images were created using the CASA task" (2.1 Observations)
- **imfit** : Deconvolved continuum radii  
  > "while the deconvolved radii are determined via the CASA task" (3.3 C$_2$H Morphology in Conjunction with Protostar Evolution)
- **ALMA pipeline** : Producing the measurement sets  
  > "The measurement sets were obtained using the ALMA pipeline." (2.1 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| C2H column density range (all sources) | 1e14 - 1e15 | not stated | cm^-2 | 3 | maps of the fitted column density show C$_2$H column densities of  10^14^ - 10^15^ cm^-2^. |
| Average C2H column density across all sources (log10) | 10^14.3 | 0.2 (in log10) | cm^-2 | 3 | an average C$_2$H column density across all sources of 10^14.3 |
| Average per-source column density uncertainty | 10^0.05 - 10^0.5 | not stated | cm^-2 | 3 | The average-per-source uncertainties on our retrieved column densities range from 10^0.05^ - 10^0.5^ cm^-2^. |
| Change in column density when varying T_r over 10-50 K | <5 | not stated | percent | 3 | yields changes in calculated C$_2$H column densities of $<$ 5% |
| Sources with C2H and SO detections (of 35) | 30 and 30 | not stated | sources | 1 | Of the 35 protostars observed, C$_2$H and SO were detected towards 30 and 30, respectively. |
| Sources with clear C2H-SO anti-correlation within the outflow | 12 of 14 | not stated | sources | 2 | Overall, we find that most sources (12 of 14) show a clear anti-correlation between the location of C$_2$H and SO within the outflow. |
| Average continuum SNR improvement from self-calibration | 31 | not stated | percent | 1 | The self-calibration process yielded an average improvement in continuum SNR of 31% |
| ACA visibility downweighting factor | 0.41 | not stated | dimensionless | 1 | the ACA visibilities were downweighted by a factor of 0.41 |
| C2H velocity shift relative to source velocity | ~1 | not stated | km/s | 5 | though with a fairly small magnitude of $\sim$ 1 km/s |

## Qualitative findings

- C2H emission remains spatially extended in most Class 0/I sources, independent of age  
  > "the C$_2$H emission remains spatially extended in most sources, independent of age." (abstract)
- Transition to compact Class II disk C2H must happen rapidly after the embedded stage  
  > "This indicates that the transition to the compact C$_2$H emission observed on the surface of Class II disks must happen rapidly, sometime just after the embedded stage." (abstract)
- C2H velocity shifts are much smaller than CO velocities  
  > "Note that in all cases, the magnitude of the C$_2$H red-or blue-shifting is much lower than the CO velocities." (3.4 Kinematic Comparison of C~2~H with CO)

## Claim tuples

- H: C2H in Class 0/I protostars traces outflow cavity walls | E: Compare C2H moment-0 maps from 12m data with SMA CO outflow maps across 35 Perseus protostars | R: Many sources show X-wing or cone-like C2H along CO outflow edges; where a bipolar CO outflow is clear, C2H is at the base/edges of at least one lobe | F: C2H is associated with outflow cavity walls, consistent with UV-driven photochemistry | **supported**
- H: C2H formation is suppressed in O-rich gas traced by SO | E: Ray-averaged radial intensity profiles of C2H and SO from 12m-only moment-0 maps | R: 12 of 14 sources with identifiable outflows show spatial anti-correlation of C2H and SO | F: C2H traces O-poor gas and is destroyed or not formed where SO traces O-rich gas | **supported**
- H: C2H morphology evolves from extended outflow-cavity to compact disk-like emission during the Class 0/I stage | E: Compare C2H emission extent with continuum deconvolved radius, bolometric temperature and luminosity | R: No clear correlation between C2H extent and the evolutionary metrics | F: No evolution found within Class 0/I, implying the change must occur rapidly after the embedded stage | **partially**
- H: Embedded-protostar C2H column densities are similar to those in Class II disks | E: Fit LTE hyperfine model with fixed T = 20 K to 12m+ACA C2H spectra | R: Column densities 1e14-1e15 cm^-2, average 10^14.3 cm^-2 | F: Column densities are comparable to Class II disks and PDR models, though temperature is unconstrained | **partially**

## Reasoning

- Why this data: Unbiased large sample of protostars of varied ages from PEACHES  
  > "With the aim of obtaining an unbiased view of C$_2$H chemistry in a large sample of protostars of varied ages, we make use of data available as part of the Perseus ALMA Chemical Survey" (Introduction)
- Why this method: 12m-only for small-scale spatial analysis; 12m+ACA to recover full C2H flux for column densities; fixed T because hyperfines share one upper-state energy  
  > "we are interested in the small-scale emission patterns, and therefore use the 12m-only images for our analysis." (3.1 C$_2$H and SO Emission Morphology); "To ensure complete recovery of the C$_2$H flux, we use the combined 12m+ACA images for this analysis." (3.2 ACA Images and Column Density Maps); "Our C~2~H hyperfine transitions span an equal upper state energy, and as a result cannot precisely fit a variable rotational temperature." (3.2 ACA Images and Column Density Maps)
- Alternative: Visual inspection of moment-0 contours judged insufficient to compare C2H and SO overlap, so intensity profiles were used  
  > "comparison of SO and C$_2$H by visual inspection of the moment-zero contours is not sufficient to understand the degree of spatial overlap between the two molecules" (3.1 C$_2$H and SO Emission Morphology)
- How they decided it was enough: _not stated_
- Limitation (authors): Rotational temperature unconstrained; more C2H lines needed for precise column densities  
  > "noting that true constraints on the C$_2$H rotational temperatures, and in turn more precise constraints on the column densities, would require coverage of additional C$_2$H lines" (3.2 ACA Images and Column Density Maps)
- Limitation (authors): Compact C2H on smaller scales than the resolution cannot be excluded  
  > "One caveat is that we cannot rule out whether there is a compact C$_2$H component on even smaller spatial scales than we can access with the spatial resolution of these observations." (4.1 Evolution of C$_2$H chemistry)
- Caveat (inferred, ours): Column densities rest on a single fixed T_r = 20 K and one hyperfine group sharing the same E_u; no temperature constraint
- Caveat (inferred, ours): Spectroscopic constants and fit optimiser/error treatment are not given, so column density uncertainties are hard to verify
- Caveat (inferred, ours): Selection of 14 sources with 'identifiable' outflows for the SO comparison is subjective and the 12 of 14 count has no statistical test
- Caveat (inferred, ours): Extent measure (width above 3 sigma) depends on beam, sensitivity and differing 12m beams across sources
- Caveat (inferred, ours): Evolutionary proxies are noisy and no quantitative correlation statistics are reported
- Caveat (inferred, ours): CO from SMA (different resolution, uv coverage) compared with ALMA C2H

## Reproducibility

- Data public (paper): MASSES CO data public via Harvard Dataverse; public status of ALMA data not stated in text  
  > "CO data products were taken directly from the MASSES data release web page through the Harvard data archive ((cite: MASSESData))." (2.1 Observations)
- Products in archive: Measurement sets obtained using the ALMA pipeline  
  > "The measurement sets were obtained using the ALMA pipeline." (2.1 Observations)
- Code: _not stated_
- Missing: Self-calibration parameters, line-free channels and moment integration ranges
- Missing: C2H spectroscopic constants/hyperfine structure and fitting implementation
- Missing: Ray definition and outflow identification rules for the C2H/SO profiles
- Missing: Source V_lsr values and CO moment map recipe
- Missing: Software versions
- Data volume (inferred): Three ALMA projects (35 sources 12m plus ACA mosaics); roughly tens to ~100 GB of calibrated measurement sets plus SMA CO products
- Score (inferred): 3/5, Data and imaging parameters (robust, pixel size, thresholds) are largely given and column density table is published, but self-cal details, spectroscopic constants, fitting implementation, ray analysis rules and software versions are missing and no code is released.
- Rediscovery candidate: no, Main results are qualitative morphology comparisons that depend on unstated selection rules; the quantitative column densities lack spectroscopic and fitting details and the public status of the ALMA data is not stated in the paper.

## Links

- Method: (cite: PEACHES_I) Yang et al. 2021, ApJ, 910, 20 (PEACHES survey observations, array configurations and detected transitions)
- Companion: (cite: PEACHES_II) Zhang et al. 2023, ApJ, 946, 113 (SO origin by weak-shock sputtering in PEACHES sources)
- Companion: (cite: PEACHES_III) Artur de la Villarmois et al. 2023, A&A, 678, A124 (Images of S-bearing molecules towards PEACHES sources)
- Related: PEACHES (Perseus ALMA Chemical Survey)
- Related: MASSES (SMA survey)

## Checks

```json
{
 "quotes": 88,
 "quotes_ok": 88,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 51,
  "rate": 0.607
 },
 "evidence_ok": true
}
```
