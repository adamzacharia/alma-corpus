# ALMA uncovers the [C II] emission and warm dust continuum in a z = 8.31 Lyman break galaxy

`2020MNRAS.493.4294B` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Bakx, Tom J. L. C. | arXiv: 2001.02812 | DOI: 10.1093/mnras/staa509

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Is [C II] detected in the z=8.31 LBG MACS0416_Y1, and what does the 1.5 mm continuum non-detection imply for its dust temperature and emissivity index?  
  > "This paper reports the detection of [C ii] and the stringent upper limit on the dust continuum emission at 1.5 mm of the Lyman-break galaxy MACS0416_Y1 at redshift 8.312." (Introduction)
- Target **MACS0416_Y1**: coordinates RA 04h16m09.4010s, Dec -24d16'35.470" (phase centre, as printed)  
  > "The [O iii] emission confirmed the spectroscopic redshift at $z = 8.3118 \pm 0.0003$." (2.1 Target and previous observations); "The phase-tracking center was set to the UV continuum position ($\alpha_{\rm{ICRS}}$, $\delta_{\rm{ICRS}}$) = (04$^{\rm{h}}$16$^{\rm{m}}$09.4010s, $-24^{\circ}$16$^{{\rm{'}}}$35.470$''$)." (2.2 ALMA observations); z/distance z = 8.3118 ± 0.0003 ([O III]); [C II] z = 8.31132 ± 0.00037  
  > "The [O iii] emission confirmed the spectroscopic redshift at $z = 8.3118 \pm 0.0003$." (2.1 Target and previous observations); "The phase-tracking center was set to the UV continuum position ($\alpha_{\rm{ICRS}}$, $\delta_{\rm{ICRS}}$) = (04$^{\rm{h}}$16$^{\rm{m}}$09.4010s, $-24^{\circ}$16$^{{\rm{'}}}$35.470$''$)." (2.2 ALMA observations); distance from [O III] redshift from Tamura et al. 2019; [C II] this work  
  > "The [O iii] emission confirmed the spectroscopic redshift at $z = 8.3118 \pm 0.0003$." (2.1 Target and previous observations); "The phase-tracking center was set to the UV continuum position ($\alpha_{\rm{ICRS}}$, $\delta_{\rm{ICRS}}$) = (04$^{\rm{h}}$16$^{\rm{m}}$09.4010s, $-24^{\circ}$16$^{{\rm{'}}}$35.470$''$)." (2.2 ALMA observations)

## Data provenance

- ALMA projects: 2017.1.00225.S, 2013.1.00999.S
- bands: Band 5  
  > "The local oscillator frequency of the Band 5 receivers (cite: Belitsky2018) was set from 200.5 GHz to 204.85 GHz" (2.2 ALMA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-1, -2, -3 and -4  
  > "These observations were executed in the C43-1, -2, -3 and -4 configurations, with baseline lengths ranging from 15 to 1400 meters." (2.2 ALMA observations)
- baselines: 15 - 1400 m  
  > "with baseline lengths ranging from 15 to 1400 meters" (2.2 ALMA observations)
- angular resolution: [C II] map 0.46" x 0.64"; continuum 0.59" x 0.78"  
  > "For the continuum map, the resulting beam-size is 0.59$''$ $\times$ 0.78$''$ at a position angle of $-$81 degrees" (2.2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: [C II] map rms 9 mJy/beam; continuum rms 6 uJy/beam  
  > "r.m.s. noise is 6 $\mu$Jy/beam" (2.2 ALMA observations)
- time on source: 272.2 minutes  
  > "In total, 272.2 minutes were spent effectively on-source." (2.2 ALMA observations)
- observing dates: August, September and November 2018  
  > "The ALMA observations were initially carried out in August, September and November 2018 as a Cycle 5 program" (2.2 ALMA observations)
- pi or archival as stated: _not stated_
- Line: [C II] 2P3/2 - 2P1/2, 157.7 um (not stated (observed ~204.1 GHz))
- Other facility **Hubble Space Telescope**: RGB image for overlay  
  > "Figure 1 shows the Hubble false-colour RGB image, overplotted with the contours of a naturally-weighted [C ii] map" (3.1 Detection)
- External data: 850 um continuum 137 ± 26 uJy and [O III] 88 um line properties  
  > "The 850 $\mu$m dust continuum is detected at 137 $\pm$ 26 $\mu$Jy" (2.1 Target and previous observations) [from Tamura2019]
- External data: Band 6 1.1 mm upper limit <116 uJy (2 sigma)  
  > "$S_{\rm{1140\mu m}}$$^{\ddagger}$ | $< 116$ (2$\sigma$) $\mu$Jy" (Table 1) [from GL2017 (project 2013.1.00999.S)]
- External data: Magnification mu = 1.43 ± 0.04  
  > "with only a moderate magnification of $\mu$ = 1.43 $\pm$ 0.04 (cite: Kawamata2016)" (2.1 Target and previous observations) [from Kawamata2016]
- External data: Delensed UV luminosity 4.5e10 Lsun  
  > "The delensed UV luminosity of MACS0416_Y1 is 4.5 $\times$ 10$^{10}$ L$_{\odot}$, taken from (cite: Laporte2015)." (4.1) [from Laporte2015]

## Processing

### Calibration

- pipeline or manual: standard pipeline  
  > "The calibration and flagging were done using the standard pipeline running on CASA (cite: McMullin2007) version 5.4.1." (2.2 ALMA observations)
- casa version: CASA 5.4.1  
  > "The calibration and flagging were done using the standard pipeline running on CASA (cite: McMullin2007) version 5.4.1." (2.2 ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "A CASA task `tclean` was used to combine all visibilities into an image, both for the continuum and the [C ii] emission" (2.2 ALMA observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We used the natural weighting on the `tclean` task to maximize the point-source flux significance." (2.2 ALMA observations)
- uv taper: Gaussian 0.27" FWHM (convolution of natural maps), chosen by maximizing S/N over 0.01-0.50"  
  > "We find this FWHM size by maximizing the signal-to-noise of the [C ii] emission for all tapering sizes between 0.01$''$ and 0.50$''$" (3.1 Detection)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: [C II]-containing channels omitted from continuum image  
  > "where the [C ii]-containing channels were omitted in the continuum image" (2.2 ALMA observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: cube sampled at 35 km/s (~23.3 MHz)  
  > "The data cube was sampled at 35 km /s ($\sim$23.3 MHz) to search for the [C ii] line feature." (2.2 ALMA observations)
- final beam: [C II] 0.46" x 0.64" PA -77 deg; continuum 0.59" x 0.78" PA -81 deg  
  > "resulting in a beam-size of 0.46$''$ $\times$ 0.64$''$ at a position angle of $-$77 degrees" (2.2 ALMA observations)
- final rms: 9 mJy/beam (moment 0), 6 uJy/beam (continuum); off-source standard deviation  
  > "Here, we calculate the r.m.s. noise from the off-source standard deviation of the maps." (2.2 ALMA observations)

### Inherited from earlier work

- 850 um continuum, [O III] line data, and SED/stellar-mass modelling taken from earlier paper  
  > "(cite: Tamura2019) report the detection of the [O iii] 88 $\mu$m line emission and 850 $\mu$m dust continuum emission." (2.1 Target and previous observations) [from Tamura2019]
- Upper-limit treatment in chi-squared  
  > "The upper limits are taken into account as discussed in (cite: Sawicki2012)" (3.3.1) [from Sawicki2012]
- CMB corrections for dust  
  > "we use the adjustment equations from (cite: daCunha2013) to include the effects of CMB" (3.3.1) [from daCunha2013]

### Not stated but needed to reproduce (our reading)

- Imaging cell size, image size, masking and clean threshold
- Which spectral windows/channels define the continuum and exact aggregate continuum bandwidth
- Aperture/method for 2D Gaussian fit and tapered spectrum extraction
- Exact measurement of 1.5 mm limit (reference frequency, position used)
- Flux calibrator and flux scale uncertainty
- Whether archive products or re-calibrated data were used
- Details of the grid and step used for the chi-squared temperature scan
- Basis of the 100-120 km/s peak-to-peak velocity gradient measurement

## Analysis recipe

1. **Image cube and continuum**: tclean with natural weighting, all configurations combined; cube at 35 km/s; continuum excludes [C II] channels  
  > "A CASA task `tclean` was used to combine all visibilities into an image, both for the continuum and the [C ii] emission" (2.2 ALMA observations)
   - software: CASA
   - parameter: moment 0 integrated over -140 to +140 km/s  
  > "We integrate the data cube between $-140$ and +140 km/s around the [C ii] frequency to generate the [C ii]-integrated map" (2.2 ALMA observations)
   - fitting: _not stated_
   - validation: velocity range gives highest S/N and agrees with by-eye inspection  
  > "This $-140$ and $+$140 km/s velocity range was chosen because it resulted in the highest signal-to-noise ratio for the [C ii] emission" (2.2 ALMA observations)
2. **Measure [C II] position, size, flux**: 2D Gaussian fit to naturally-weighted integrated intensity image  
  > "We calculate the central position and total apparent flux by fitting a 2D Gaussian to the naturally-weighted integrated intensity image" (3.1)
   - fitting: 2D Gaussian  
  > "We calculate the central position and total apparent flux by fitting a 2D Gaussian to the naturally-weighted integrated intensity image, since it has the best positional accuracy." (Results, Detection of the [C ii] 158 micron emission)
   - validation: _not stated_
3. **Fit line profile and luminosity**: Gaussian fit to spectrum from 0.27" tapered map; L from Solomon et al. 2005 relation with lensing correction  
  > "In order to maximise the signal-to-noise ratio of the spectrum and fitted line-profile, we taper the [C ii] map with a 0.27 arcsecond tapering size." (3.1)
   - assumption: CMB attenuation of [C II] not corrected; mu = 1.43  
  > "We do not account for the effect of the Cosmic Microwave Background (CMB) on the [C ii]-luminosity" (3.1)
   - fitting: Gaussian profile  
  > "The best-fit Gaussian profile finds a central frequency at 204.1105 $\pm$ 0.0082 GHz, indicating a redshift of 8.31132 $\pm$ 0.00037." (Results, Detection of the [C ii] 158 micron emission)
   - validation: compared with [O III] profile  
  > "the bottom panel shows the \[O iii\] 88$\mu$m emission from (cite: Tamura2019) in order to compare the line profiles." (Results, Detection of the [C ii] 158 micron emission)
4. **Constrain dust temperature and beta**: Fit single-temperature modified blackbody (normalization free) to 850 um detection plus 1.1 and 1.5 mm upper limits at fixed T and beta; 90% lower limit from Delta chi2 = 2.7 interpolation  
  > "We fit these modified blackbodies by adjusting the normalization, $A$, such that we minimize the chi-squared, $\chi^2$." (3.3.1)
   - parameter: beta = 1.5, 2.0, 2.5; T from 30 to 130 K  
  > "In Figure [7](#fig:SED), we show the results from fitting a single-temperature modified blackbody with different $\beta$ for a range of possible temperatures." (Discussion, Fitting a spectrum)
   - assumption: kappa_850um = 0.15 m2/kg (Draine 2003), nu0 = 353 GHz; CMB heating and contrast corrected  
  > "$\kappa_{\rm 850 \mu m}$ = 0.15 m$^2$/kg (cite: Draine2003)" (3.3.1)
   - fitting: chi-squared minimization with upper-limit adjustment (Sawicki 2012); temperature and beta not fitted jointly due to degeneracy  
  > "Given the degeneracy between $\beta$ and temperature, we cannot fit these values directly" (3.3.1)
   - validation: agrees with visual inspection of SED figure  
  > "agree with the visual analysis of Figure 7" (3.3.1)
5. **Dust mass**: Equation 1 of Magdis et al. 2011  
  > "We estimate the dust mass according to equation 1 in (cite: Magdis2011)" (3.3.1)
   - fitting: _not stated_
   - validation: _not stated_
6. **Dynamical mass from kinematics**: Virial M_dyn = C r_1/2 sigma^2 / G with C = 3.4; velocity field via immoments  
  > "we take $C$ to be 3.4 from (cite: Erb2006)" (4.2.2)
   - software: CASA immoments
   - parameter: r_1/2 = deconvolved major axis, 1.15 ± 0.35 kpc  
  > "we take the deconvolved major axis as the half-light radius, equalling 1.15 $\pm$ 0.35 kpc" (4.2.2)
   - assumption: rotation-dominated system  
  > "Given that MACS0416_Y1 is rotationally-dominated, we take $C$ to be 3.4 from (cite: Erb2006)" (Discussion, Velocity profile)
   - fitting: _not stated_
   - validation: uncertainty in C not included, could vary by factor of two  
  > "although we note that the uncertainty in $C$ is not accounted for, and could vary by a factor of two" (4.2.2)

## Software

- **CASA** 5.4.1: pipeline calibration, tclean imaging, immoments  
  > "The calibration and flagging were done using the standard pipeline running on CASA (cite: McMullin2007) version 5.4.1." (2.2 ALMA observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [C II] integrated flux (apparent) | 130.2 | 20.4 | mJy km/s | 2 | 130.2 $\pm$ 20.4 mJy km/s |
| [C II] redshift | 8.31132 | 0.00037 | dimensionless | 3 | indicating a redshift of 8.31132 $\pm$ 0.00037 |
| [C II] FWHM | 191 | 29 | km/s | 3 | The [C ii] line width (FWHM) is 191 $\pm$ 29 km/s |
| [C II] luminosity (magnification-corrected) | 1.40e8 | 0.22e8 | Lsun | 3 | We find (1.40 $\pm$ 0.22) $\times$ $10^8$ $L_{\odot}$ |
| 1.5 mm continuum upper limit | <18 | 3 sigma | uJy | 1 | We find a 3$\sigma$ upper limit of 18 $\mu$Jy at 1.5 mm |
| [O III]/[C II] luminosity ratio | 9.3 | 2.6 | dimensionless | 3 | resulting in a [O iii]-to-[C ii] luminosity ratio of 9.3 $\pm$ 2.6 |
| Dynamical mass | 1.2e10 | 0.4e10 | Msun | 6 | We find a dynamical mass of (1.2 $\pm$ 0.4) $\times$ 10$^{10}$ M$_{\odot}$ |
| 90% lower limit dust temperature (beta=2.0) | 80 | 90% confidence | K | 4 | 80 / 15.9 / 2.7 **(90%)** / 0.5 |
| [C II]-[O III] positional offset | 95 | 2 sigma significance | mas | 2 | which is 95 milli-arcseconds offset from the [C ii] emission |

## Qualitative findings

- [C II] is cospatial with 850 um dust emission but offset from [O III] peak  
  > "however the peak [C II] emission does not agree with the peak [O III] emission" (abstract)
- Velocity gradient suggests a rotation-dominated disc, with outflow/inflow/merger alternatives  
  > "suggesting a rotationally-dominated disc" (4.2.2)

## Claim tuples

- H: Is [C II] detectable in MACS0416_Y1 and how does it compare with [O III]? | E: Band 5 imaging and Gaussian fits | R: [C II] detected; L[OIII]/L[CII] = 9.3 ± 2.6 | F: Hard radiation fields and/or low PDR covering fraction | **supported**
- H: Does the 1.5 mm limit imply unusual dust properties? | E: Modified blackbody chi2 fit with 850 um, 1.1 mm and 1.5 mm limits | R: T > 80 K at beta=2 (90% limit) | F: Warm dust and/or steep beta | **supported**
- H: Is the [C II] kinematics rotation dominated? | E: Velocity map, peak-to-peak 100-120 km/s | R: Delta v/2sigma ≈ 0.6-0.7; M_dyn 1.2e10 Msun | F: Likely rotating disc, though outflow/merger cannot be excluded | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Dust temperature and beta cannot be fitted jointly due to degeneracy, so a 90% lower limit from Delta chi2 is used  
  > "Instead, we find the 90% confidence limit from the $\chi^2$ value." (3.3.1)
- Alternative: Extended [C II] halo and inclination effects rejected as explanations for high [OIII]/[CII] ratio  
  > "disqualifying missed [C ii] emission due to a spatially extended [C ii] halo (G) around MACS0416_Y1" (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Uncertainty in C not included in M_dyn; CMB attenuation of [C II] not corrected; resolution does not resolve outflow regions  
  > "Our current beam-width does not allow us to resolve the individual outflowing regions" (4.2.2)
- Caveat (inferred, ours): Dust temperature constraint rests on one detection and two upper limits from different projects, with only a 90% lower limit
- Caveat (inferred, ours): Kinematic claim from a barely resolved source with a 0.5" beam
- Caveat (inferred, ours): Offset between [C II] and [O III] is only 2 sigma

## Reproducibility

- Data public (paper): ALMA project codes cited in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA 2017.1.00225.S, 2016.1.00117 and 2013.1.00999.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Cell/image size, masking, clean thresholds
- Missing: Exact continuum channel selection
- Missing: Flux calibrator and flux uncertainty
- Missing: Chi-squared grid details
- Data volume (inferred): ~100-300 GB (six Band 5 execution blocks, raw)
- Score (inferred): 6/5, Public data and a simple recipe with key numbers; imaging details are sparse.
- Rediscovery candidate: yes, Public data and simple numeric outputs (flux, line width, upper limit, T limit), though imaging parameters are underspecified.

## Links

- Method: Sawicki2012 (treatment of upper limits in chi2)
- Method: daCunha2013 (CMB corrections for dust)
- Method: Magdis2011 (dust mass equation)
- Companion: Tamura2019 (Earlier ALMA [O III] and 850 um detection of the same source)
- Related: Hubble Frontier Fields
- Related: 2013.1.00999.S

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2013.1.00999.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 54,
  "rate": 0.675
 },
 "evidence_ok": true
}
```
