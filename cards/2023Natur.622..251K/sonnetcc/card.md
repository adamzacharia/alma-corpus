# A planetary collision afterglow and transit of the resultant debris cloud

`2023Natur.622..251K` | Nature 2023 | first author: Kenworthy, Matthew | arXiv: 2310.08360 | DOI: 10.1038/s41586-023-06573-9

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: debris_disks, exoplanets, stellar_physics
- Question: What caused the infrared brightening and later optical dimming of ASASSN-21qj; the authors propose a single giant impact between super-Earths or mini Neptunes, with the ALMA Band 7 observation used to set a limit on cool dust  
  > "Here, we combine both optical (from the Las Cumbres Observatory Global Telescope, LCOGT) and infrared (from the WISE satellite) observations of ASASSN-21qj for the years before and after this dimming event" (Main Article); "Instead, we hypothesize that are we are observing the aftermath of a single collision between super-Earths or mini Neptunes" (Main Article)
- Target **ASASSN-21qj (Gaia DR3 5539970601632026752 = 2MASS J08152329-3859234)**: coordinates 08:15:23.30 -38:59:23.3 (ICRS, Extended Data Table 1)  
  > "08:15:23.30" (Extended Data Table 1); "-38:59:23.3" (Extended Data Table 1); "567.2" (Extended Data Table 1); "at 600 pc thousands of square au of 100 K dust is needed for a thermal detection with ALMA" (Dust mass estimates); z/distance 567.2 (+6.7/-5.9) pc (Extended Data Table 1); text also says 600 pc  
  > "08:15:23.30" (Extended Data Table 1); "-38:59:23.3" (Extended Data Table 1); "567.2" (Extended Data Table 1); "at 600 pc thousands of square au of 100 K dust is needed for a thermal detection with ALMA" (Dust mass estimates); distance from not stated explicitly; Extended Data Table 1 lists the Gaia DR3 parallax and a distance  
  > "08:15:23.30" (Extended Data Table 1); "-38:59:23.3" (Extended Data Table 1); "567.2" (Extended Data Table 1); "at 600 pc thousands of square au of 100 K dust is needed for a thermal detection with ALMA" (Dust mass estimates)

## Data provenance

- ALMA projects: 2019.A.00040.S
- bands: Band 7, mean wavelength 880 um  
  > "used band 7, with a mean wavelength of 880" (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: archive products RMS 17 uJy; own naturally weighted image RMS 20 uJy; upper limit 60 uJy  
  > "The archive products report an RMS of 17 $\mu$Jy, and we measure an RMS of 20 $\mu$Jy in a naturally weighted image." (Observations); "We therefore consider these results as an upper limit of 60 $\mu$Jy." (Observations)
- time on source: _not stated_
- observing dates: 2021 September 28 (MJD=59485)  
  > "These observations were taken 2021 September 28 (MJD=59485)" (Observations)
- pi or archival as stated: Data downloaded from the ALMA archive (programme 2019.A.00040.S)  
  > "were downloaded and processed through to a measurement set with CASA" (Observations)
- Other facility **LCOGT**: Optical g', r', i' photometry processed with a modified BANZAI pipeline  
  > "the data we collected are in SDSS $g'$, $r'$ and $i'$ bands" (Observations); "All data is automatically processed and calibrated by the BANZAI pipeline." (Observations)
- Other facility **ASAS-SN**: Public V and g' optical light curve; announced the dimming event  
  > "The beginning of the eclipse was announced" (Observations)
- Other facility **NEOWISE / WISE**: W1 and W2 infrared light curve showing the brightening and the blackbody-like excess  
  > "A single data point for each epoch and wavelength is calculated by taking the weighted average of the individual NEOWISE measurements." (Observations)
- Other facility **TESS**: Quick-Look Pipeline light curve from sectors 8, 34 and 35 used for stellar rotation period  
  > "The star was observed in sectors 8, 34 and 35." (Stellar rotation and age)
- Other facility **ATLAS**: Optical c and o band photometry covering the collision time  
  > "Two filters were obtained, the $o$ (orange) and $c$ (cyan) filters respectively." (Observations)
- Other facility **AAVSO (ROAD)**: B, V and I band photometry  
  > "obtains nightly photometry in Astrodon B, V and I bands for a wide range of astronomical projects" (Observations)
- External data: Stellar parameters (Gaia DR3 Teff, parallax, distance etc.) used for the star and for a fit to the SED  
  > "The stellar properties of ASASSN-21qj (Gaia DR3 5539970601632026752 = 2MASS J08152329-3859234) are listed in Extended Data Table" (Methods) [from Gaia DR3 (no (cite:) key given in the text)]
- External data: Silicate absorption efficiency used for the dust spectrum in the dust mass estimate  
  > "based on the absorption efficiency for silicates" (Dust mass estimates) [from (cite: 1993ApJ...402..441L)]
- External data: Interstellar extinction law values compared to the measured A_lambda/A_V  
  > "The values are similar to those seen for interstellar extinction" (Dust properties from optical colors) [from (cite: 1989ApJ...345..245C)]
- External data: Latent heat of vaporization of pure water used in the cooling model  
  > "the latent heat of vaporization of the material (here we have taken the limiting case of pure water" (Post-impact body cooling calculations) [from (cite: Chase1998)]
- Simulation/model as data: SWIFT SPH impact simulation of two 25 Earth-mass planets used to illustrate the extent of the post-impact body  
  > "we performed impact simulations using the SWIFT smoothed particle hydrodynamics (SPH) code" (SPH collision simulations)
- Simulation/model as data: Conceptual post-impact body cooling model with power-law surface density profiles  
  > "we have calculated the evolution of post-impact bodies with different power-law surface density profiles, $\Sigma$, under the limiting case that radiative cooling and condensation of the vapor is the single driver for evolution of the structure." (Post-impact body cooling calculations)

## Processing

### Calibration

- pipeline or manual: Downloaded and processed through to a measurement set with CASA (details not given)  
  > "were downloaded and processed through to a measurement set with CASA" (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Default archive products inspected (no source) and additionally CLEAN images made  
  > "No source is visible in the default archive products, and we also detect no source at the expected location in CLEAN images." (Observations)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "we measure an RMS of 20 $\mu$Jy in a naturally weighted image" (Observations)
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
- final rms: 20 uJy (own image); 17 uJy in archive products  
  > "The archive products report an RMS of 17 $\mu$Jy, and we measure an RMS of 20 $\mu$Jy in a naturally weighted image." (Observations)

### Inherited from earlier work

- Transverse-velocity method: treat linear flux changes as edges of dust clouds and take the largest absorption in a segment as the cloud absorption  
  > "and the largest amount of absorption within any of these segments as an estimate for the absorption of the cloud" (Duration of the eclipse and gradient analysis) [from (cite: Kennedy17)]
- Gyrochronological age calibration from the rotation period  
  > "Using this rotational period the gyrochronological age" (Stellar rotation and age) [from (cite: Bouma23; Kounkel22)]
- SED fitting method for the star  
  > "A fit using the method of" (Methods) [from (cite: 2019MNRAS.488.3588Y)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the pipeline-restored measurement set or a manual calibration was used
- tclean parameters for the ALMA image: cell size, image size, deconvolver, threshold, mask, UV range
- Size of the region used to measure the 20 uJy RMS
- How the 60 uJy upper limit was derived from the RMS (the paper gives only the number; a 3-sigma rule is not stated)
- ALMA array configuration, baselines, spectral setup, bandwidth and time on source
- Which flux and bandpass calibrators and which flux scale were used
- Photometric uncertainty and dust model details behind the SED upper-limit curve in Extended Data Figure 4

## Analysis recipe

1. **measure an ALMA Band 7 upper limit at the stellar position**: Download archive data, process to a measurement set with CASA, make a naturally weighted CLEAN image, measure the RMS and adopt an upper limit  
  > "were downloaded and processed through to a measurement set with CASA" (Observations); "we measure an RMS of 20 $\mu$Jy in a naturally weighted image" (Observations)
   - software: CASA
   - parameter: upper limit of 60 uJy  
  > "We therefore consider these results as an upper limit of 60 $\mu$Jy." (Observations)
   - fitting: _not stated_
   - validation: Compared the own RMS (20 uJy) with the archive-product RMS (17 uJy)  
  > "The archive products report an RMS of 17 $\mu$Jy, and we measure an RMS of 20 $\mu$Jy in a naturally weighted image." (Observations)
2. **fit stellar photosphere and infrared excess**: Fit stellar models to Gaia, APASS, DENIS and WISE photometry; refit including the first five post-brightening NEOWISE points to derive the excess  
  > "The stellar photospheric flux was estimated by fitting stellar models to GAIA, APASS, and DENIS and WISE optical/near-IR photometry" (Methods); "To estimate the IR excess properties we fit the same models, but now including the first five post-brightening NEOWISE data points." (Methods)
   - parameter: Contaminating nearby source corrected using Gaia photometry for the star and the post/pre-brightening difference for the WISE excess  
  > "We correct for the nearby source by using the GAIA photometry for the star, and the post/pre-brightening difference for the WISE excess flux." (Methods)
   - assumption: No reddening needed; stellar mass equal to the Sun where necessary  
  > "We do not find that reddening is needed for these models" (Methods); "Where necessary we assume a stellar mass equal to the Sun." (Methods)
   - fitting: _not stated_
   - validation: Gaia DR3 Teff of 5760 K compared with the fitted value; excess temperature compared with the subtraction-based temperatures  
  > "These fluxes therefore exclude the contaminating flux from the nearby object, and are consistent with the SED-derived dust temperature." (Methods)
3. **derive excess temperature as a function of time**: Subtract median pre-brightening W1/W2 fluxes and use their RMS as uncertainty  
  > "To estimate the dust temperature as a function of time we simply subtract the median pre-brightening W1/2 fluxes, with the RMS of these values as the uncertainty" (Methods)
   - assumption: Blackbody radius may underestimate the true location by a factor of up to five  
  > "Typically the radius derived under the assumption of blackbody emission is an underestimate by a factor of up to five" (Methods)
   - fitting: _not stated_
   - validation: _not stated_
4. **measure stellar rotation period and age**: Lomb-Scargle periodogram of TESS sector 8, then gyrochronological age  
  > "We carry out a Lomb-Scargle periodogram on S08, and obtain a significant detection of $P=4.43\pm 0.33$ days." (Stellar rotation and age)
   - assumption: Modulation attributed to star spots, so the period is the stellar rotation period  
  > "We attribute this modulation due to star spots on the star rotating in and out of our view" (Stellar rotation and age)
   - fitting: _not stated_
   - validation: Similar period seen at lower significance in later TESS sectors and 4.1 days in ASAS-SN data  
  > "Aside from a peak at 1 day, the strongest peak in the ASAS-SN data has a similar period, at 4.1 days." (Stellar rotation and age)
5. **constrain transverse velocity and distance of the occulting dust**: Visually pick turning points in the normalised light curve, fit straight lines and convert flux gradients to a lower limit on velocity  
  > "We visually determine turning points in the linearly increasing or decreasing photometric flux, fit straight lines to the selected points, and determine the flux gradient in units of day$^{-1}$." (Duration of the eclipse and gradient analysis)
   - assumption: Sharp-edged, completely opaque occulter crossing the stellar disk; dust on a circular orbit  
  > "what velocity a sharp edged and completely opaque occulter moving across the disk of the star would need to make the same gradient" (Duration of the eclipse and gradient analysis); "If the dust is on a circular orbit, it therefore has to be within 16 au" (Duration of the eclipse and gradient analysis)
   - fitting: _not stated_
   - validation: _not stated_
6. **constrain dust properties from optical colours**: Compare B-V and V-I colours versus V magnitude with an extinction model plus a scattered-light component of stellar colour  
  > "The solid lines show an extinction model where an underlying scattered light component with the same colour as the star has been added" (Dust properties from optical colors)
   - fitting: _not stated_
   - validation: _not stated_
7. **estimate the dust mass detectable with ALMA**: Blackbody times an emissivity factor for 0.1 um grains at 100 K, scaled to 1% of an Earth mass  
  > "is approximated as a blackbody multiplied by $0.01 \times (10 / \lambda)^{1.5}$ (with $\lambda$ in $\mu$m)" (Dust mass estimates)
   - parameter: Dust temperature 100 K; grain size 0.1 um (1 um gives a similar spectrum)  
  > "is assumed to be converted entirely into 0.1 $\mu$m sized grains" (Dust mass estimates); "Changing the grain size to 1 $\mu$m yields a similar dust spectrum" (Dust mass estimates)
   - assumption: Collision at of order 10 au from the star, so dust at 100 K  
  > "We assume that the collision occurred at of order 10 au from the star, and hence that a dust temperature of 100 K is reasonable." (Dust mass estimates)
   - fitting: _not stated_
   - validation: _not stated_
8. **illustrate the extent of a post-impact body with an SPH simulation**: SWIFT SPH collision of two 25 Earth-mass planets  
  > "we performed impact simulations using the SWIFT smoothed particle hydrodynamics (SPH) code" (SPH collision simulations)
   - software: SWIFT
   - parameter: impact parameter 0.4 (impact angle 23.6 deg); 2.1e6 particles  
  > "at an impact parameter of 0.4 (an impact angle of 23.6$^\circ$)" (SPH collision simulations); "2.1$\times10^6$ particles were used in the simulation." (SPH collision simulations)
   - assumption: Bodies composed of 22.5% rock, 67.5% water and 10% H/He by mass  
  > "The colliding bodies were 22.5% rock" (SPH collision simulations)
   - fitting: _not stated_
   - validation: Authors note SPH likely underestimates the extent of post-impact bodies because of the minimum particle density  
  > "SPH simulations therefore likely underestimate the extent of such post-impact bodies" (SPH collision simulations)

## Software

- **CASA** : Processing the ALMA data to a measurement set and CLEAN imaging  
  > "were downloaded and processed through to a measurement set with CASA" (Observations)
- **BANZAI** : LCOGT image processing and calibration (last two stages modified for this star)  
  > "All data is automatically processed and calibrated by the BANZAI pipeline." (Observations)
- **SWIFT** : SPH giant-impact simulation  
  > "we performed impact simulations using the SWIFT smoothed particle hydrodynamics (SPH) code" (SPH collision simulations)
- **showyourwork** : Reproducible framework for the analysis and figure code  
  > "All the code for the analysis and the generation of all the figures are available in a showyourwork" (Code availability)
- **TESS Quick-Look Pipeline** : TESS light curve of the star  
  > "TESS data from the Quick-Look Pipeline" (Stellar rotation and age)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA Band 7 RMS, own naturally weighted image | 20 | not stated | uJy | 1 | we measure an RMS of 20 $\mu$Jy in a naturally weighted image |
| ALMA Band 7 upper limit | 60 | not stated | uJy | 1 | We therefore consider these results as an upper limit of 60 $\mu$Jy. |
| Blackbody temperature of the IR excess | 1000 | +/-100 | K | 0 | emission at a blackbody temperature of $1000 \pm 100$ K |
| Dust fractional luminosity L_dust/L_star | 0.04 | +/-0.005 | dimensionless | 2 | This fit yields the fractional luminosity $L_{\rm dust}/L_\star = 0.04 \pm 0.005$ and a dust temperature $950 \pm 30$ K. |
| Dust temperature from SED fit | 950 | +/-30 | K | 2 | This fit yields the fractional luminosity $L_{\rm dust}/L_\star = 0.04 \pm 0.005$ and a dust temperature $950 \pm 30$ K. |
| Best-fit stellar effective temperature | 5560 | +/-100 | K | 2 | The best fit stellar effective temperature is $5560 \pm 100$ K. |
| Emitting area and equivalent radius of the IR emitter | 0.01 au^2; 7 R_sun (750 R_Earth) | not stated | au^2; R_sun | 0 | this implies an emitting area of 0.01 au$^2$, equivalent to an object with a radius of 7 $R_\odot$ |
| Stellar rotation period | 4.43 | +/-0.33 | days | 4 | obtain a significant detection of $P=4.43\pm 0.33$ days |
| Gyrochronological age | 300 | +/-92 | Myr | 4 | is calculated to be $300\pm92$ Myr |
| Eclipse duration | approximately 500 | not stated | days | 0 | giving a total eclipse duration of approximately 500 days |
| Lower limit on transverse velocity of the occulting material | 7.5 | not stated | km s^-1 | 5 | we can determine a robust lower limit to the transverse velocity of 7.5 km s$^{-1}$ for the material moving in front of the star |
| Maximum stellocentric distance of the dust if on a circular orbit | 16 | not stated | au | 5 | If the dust is on a circular orbit, it therefore has to be within 16 au |
| Scattered-light fraction | 7.5% | not stated | percent | 6 | The fraction of scattered light is relatively large at 7.5% |
| Mass in small grains detectable with ALMA | about 0.2 | not stated | M_Earth | 7 | the mass in small grains detectable with ALMA is about 0.2 $M_{\rm Earth}$ |

## Qualitative findings

- Optical multiband photometry shows a wavelength-dependent depth consistent with extinction by sub-micron particles  
  > "Optical multiband photometry shows a wavelength dependent depth consistent with extinction by sub-micron particles." (Main Article)
- No infrared excess before the NEOWISE brightening  
  > "Primarily, we conclude that there is no evidence that ASASSN-21qj showed evidence for an IR excess before the brightening seen by NEOWISE." (Methods)
- The ALMA upper limit does not constrain the hot (~1000 K) excess but limits emission from cooler dust  
  > "In terms of the infrared excess visible in the mid-IR with WISE this upper limit is not at all constraining" (Observations)

## Claim tuples

- H: The IR brightening and the optical eclipse are the aftermath of a single giant impact | E: Combined optical and WISE light curves, SED fit, gradient analysis, SPH simulation and cooling model | R: About 1000 K excess, 900 day IR-to-optical delay, dust at 2 to 16 au, post-impact body of order 7 R_sun | F: A single collision between super-Earths or mini Neptunes at 2 to 16 au is proposed as the preferred scenario | **partially**
- H: Cool dust from the collision is detectable with ALMA | E: ALMA Band 7 imaging at the stellar position | R: No detection; 60 uJy upper limit | F: Thermal emission from impact dust is not necessarily easily detected, even in an optimistic case | **supported**
- H: The dimming is caused by small dust grains | E: Multiband optical photometry and colour analysis | R: Deeper absorption at bluer wavelengths with A_lambda/A_V similar to interstellar values | F: The dimming is caused by sub-micron dust | **supported**
- H: The IR brightening and optical dimming are unrelated coincident events | E: Probability argument from the rarity of IR excesses and dimming events | R: Combined chance probability at best 0.01% | F: Coincidence scenario rejected as improbable | **supported**

## Reasoning

- Why this data: The ALMA Band 7 observation was triggered by the announcement of the eclipse  
  > "which triggered several observing campaigns at optical wavelengths and an ALMA observation at Band 7" (Observations)
- Why this method: _not stated_
- Alternative: Two unrelated coincidental phenomena, rejected as improbable  
  > "We consider three possible scenarios to explain the observations: 1) The initial brightening and later eclipse are two unrelated phenomena." (Alternative explanations for the observations)
- Alternative: A single debris disk at about 0.1 au producing both IR and optical features, rejected for geometry and timing issues  
  > "Another possibility is that both the IR and optical features are produced by a single debris disk at about 0.1 au from the star." (Alternative explanations for the observations)
- How they decided it was enough: _not stated_
- Limitation (authors): The ALMA upper limit does not constrain the hot excess  
  > "In terms of the infrared excess visible in the mid-IR with WISE this upper limit is not at all constraining" (Observations)
- Limitation (authors): SPH simulations likely underestimate the extent of post-impact bodies  
  > "SPH simulations therefore likely underestimate the extent of such post-impact bodies" (SPH collision simulations)
- Limitation (authors): Further work needed on structure and evolution of post-impact bodies  
  > "Further work is required to understand the structure and evolution of bodies produced by impacts" (Main Article)
- Caveat (inferred, ours): ALMA upper limit has no stated array, baselines or integration time, so the 60 uJy cannot be checked against the sensitivity expected
- Caveat (inferred, ours): Interpretation of the IR excess as a post-impact body rests on a qualitative cooling model, not a fit to the data
- Caveat (inferred, ours): Dust-mass limit depends on assumed 100 K temperature and 0.1 um grains

## Reproducibility

- Data public (paper): ALMA data downloaded from the archive; analysis data on Zenodo  
  > "were downloaded and processed through to a measurement set with CASA" (Observations); "The data sets generated and analysed during the current study are available in the Zenodo repository" (Data availability)
- Products in archive: Default archive products exist and were inspected  
  > "No source is visible in the default archive products" (Observations)
- Code: Analysis and figure code in a showyourwork framework on GitHub (mkenworthy/ASASSN-21qj-collision); SWIFT is open source at swiftsim.com  
  > "All the code for the analysis and the generation of all the figures are available in a showyourwork" (Code availability); "The source code and documentation for the SWIFT open-source simulation code is available from" (Code availability)
- Missing: CASA version and imaging parameters for the ALMA image
- Missing: ALMA configuration, bandwidth and time on source
- Missing: Definition of the upper limit (60 uJy) relative to the RMS
- Data volume (inferred): Small: one Band 7 execution block, likely a few GB of raw data
- Score (inferred): 2/5, Code and data are released for the whole paper, but the ALMA part (a non-detection) lacks CASA version and imaging settings, and the main results are mostly optical/IR.
- Rediscovery candidate: no, ALMA plays a minor role and gives only a non-detection upper limit; the main results come from optical/IR light curves and a conceptual model.

## Links

- Method: (cite: Kennedy17) (Method for converting light-curve gradients to a transverse velocity lower limit)
- Method: (cite: Lock18) (Post-impact body (synestia) physics and condensation buffering used for the cooling model)
- Companion: (cite: RizzoSmith21) (Announcement of the dimming event)
- Related: ASAS-SN
- Related: NEOWISE
- Related: LCOGT
- Related: TESS
- Related: ATLAS
- Related: AAVSO

## Checks

```json
{
 "quotes": 106,
 "quotes_ok": 106,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 106,
  "stated": 66,
  "rate": 0.623
 },
 "evidence_ok": true
}
```
