# An 80 au cavity in the disk around HD 34282

`2017A&A...607A..55V` | Astronomy and Astrophysics 2017 | first author: van der Plas, G. | arXiv: 1707.01688 | DOI: 10.1051/0004-6361/201731392

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Does the HD 34282 disk have a large cavity, as predicted from SED modeling, and what is the dust and gas structure and its origin?  
  > "We aim to resolve the large cavity in the disk around HD 34282, such as has been predicted by previous studies modeling the spectral energy distribution" (abstract)
- Target **HD 34282**: coordinates _not stated_; z/distance 325 (+29/-47) pc  
  > "For source distance we use the value of 325$^{+29}_{-47}$ pc from the Gaia DR1" (Introduction); distance from Gaia DR1  
  > "For source distance we use the value of 325$^{+29}_{-47}$ pc from the Gaia DR1" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00658.S
- bands: Band 7 (345 GHz)  
  > "Using ALMA band 7 observations we study HD 34282" (abstract)
- frequencies and spectral setup: Two TDM continuum windows at 345.8 and 356.7 GHz; two FDM windows for 12CO J=3-2 and HCO+ J=4-3, 0.23 GHz bandwidth  
  > "These two TDM spectral windows were centred at 345.8 GHz and 356.7 GHz." (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-2 (compact) and C34-7 (extended)  
  > "ALMA Early Science Cycle 2 observations were conducted in the compact C43-2 configuration" (2 Observations and data reduction)
- baselines: 15.1-348.5 m and 15.1-1466.2 m  
  > "between respectively 15.1 and 348.5 meters, and between 15.1 and 1466.2 meters" (2 Observations and data reduction)
- angular resolution: 0.25x0.19 arcsec (briggs); 0.17x0.10 arcsec (superuniform)  
  > "0.17" $\times$ 0.10" at PA = 77.0 degrees (superuniform)" (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: RMS 0.11 mJy/beam (superuniform continuum)  
  > "resulting in a final RMS of 0.11 mJy/beam for the images created using superuniform weighting" (2 Observations and data reduction)
- time on source: 684 s (compact), 342 s (extended)  
  > "with 684 seconds of total time on source" (2 Observations and data reduction)
- observing dates: 2014 Dec 12 and 2015 Aug 31  
  > "2014 Dec 12" (Table 1)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (not stated)
- Line: HCO+ J=4-3 (not stated)
- Other facility **Gaia DR1**: Distance and stellar position  
  > "For source distance we use the value of 325$^{+29}_{-47}$ pc from the Gaia DR1" (Introduction)
- External data: Stellar parameters (A3 V, 6.4 Myr, 13.64 Lsun, 1.59 Msun)  
  > "We use the values derived by (cite: 2004A&A...419..301M) that are based on detailed modeling of the stellar spectrum" (Introduction) [from (cite: 2004A&A...419..301M)]
- External data: Dust temperature-luminosity relation  
  > "$\langle T_{dust} \rangle \approx 25 (L_{*} /L_{\odot})^{1/4} K$ (cite: andrews2013)" (4.1 Mass limits) [from (cite: andrews2013)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "The data were calibrated and combined using the *Common Astronomy Software Applications* pipeline" (2 Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-013  
  > "J0423-013" (Table 1)
- flux scale uncertainty: ~20%  
  > "we estimate the absolute flux calibration to be accurate within $\sim$20%" (2 Observations and data reduction)
- self calibration: Phase and amplitude self-calibration on continuum, applied to lines  
  > "we perform self-calibration on both phase and amplitude" (2 Observations and data reduction)

### Imaging

- task: CLEAN in CASA  
  > "We image the disks with the CLEAN task in CASA" (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: briggs and superuniform (robust not given)  
  > "using briggs and superuniform weighting" (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CASA uvcontsub  
  > "subtracted the continuum emission using the CASA task *uvcontsub*" (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.25x0.19 at PA 88.3 (briggs); 0.17x0.10 at PA 77.0 (superuniform)  
  > "0.25" $\times$ 0.19" at PA = 88.3 degrees (briggs)" (2 Observations and data reduction)
- final rms: 0.11 mJy/beam (superuniform)  
  > "final RMS of 0.11 mJy/beam" (2 Observations and data reduction)

### Not stated but needed to reproduce (our reading)

- Briggs robust value
- Cell and image size, clean masks, threshold
- Self-calibration solution intervals and number of iterations
- Line-free channels for uvcontsub
- How the amplitude scaling between configurations was applied
- Initial uvmultifit parameter values
- Details of the polar deprojection and radial/azimuthal profile extraction

## Analysis recipe

1. **Calibrate, combine, self-calibrate and image**: CASA pipeline calibration, extended-array amplitudes scaled to compact-array, phase and amplitude self-cal, CLEAN imaging  
  > "we scale the amplitudes of the visibilities for the extended array configuration observations to those of the compact array configuration observations" (2 Observations and data reduction)
   - software: CASA
   - assumption: Midplane emission constant over the 8 month period  
  > "assuming that the emission from the midplane is constant in the 8 month period spanning the observations" (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit continuum visibilities with geometric models**: Fit combinations of disk, ring and 2D Gaussian components to visibilities in each continuum window  
  > "We fit the continuum visibilities to a combination of the following geometries" (3.1 continuum)
   - software: uvmultifit
   - parameter: Two disks sharing center, inclination and PA, plus offset Gaussian  
  > "We achieve the best fit with a combination of two disk components and a Gaussian that is offset from the disk center" (3.1 continuum)
   - fitting: chi2 minimization; uncertainties from post-fit covariance scaled to reduced chi2 of 1  
  > "Quoted parameter uncertainties are estimated from the post-fit covariance matrix which is scaled so that its $\chi^{2}_{r}$ has a value of 1." (3.1 continuum)
   - validation: Residuals of calibrated visibilities and imaged residuals compared with model  
  > "as judged by minimizing the residuals of the calibrated visibilities of the data and our models" (3.1 continuum)
3. **Radial and azimuthal profiles**: Deproject to polar coordinates with fitted geometry, collapse radially and azimuthally, subtract median radial Gaussian, fit 2D Gaussian to remaining structure  
  > "we remap the disk to polar coordinates after deprojecting it using the previously derived geometry" (3.1.1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Line moments, fluxes and gas extent**: Moment 0/1/8 maps; inner radius from highest 3 sigma velocity assuming Keplerian rotation; outer extent from 3 sigma emission  
  > "We calculate an upper limit on the inner radius of the gas disk assuming Keplerian rotation for the highest velocity at which we detect the line above 3$\sigma$" (3.2 CO and HCO+ emission)
   - software: CASA
   - assumption: Keplerian rotation, inclination 59.3 deg, 1.59 Msun star  
  > "assuming the gas is in Keplerian rotation in a disk inclined with 59.3$^\circ$ around a 1.59 M$_\odot$ star" (Table 2)
   - fitting: _not stated_
   - validation: PV diagrams compared with Keplerian curves for distance and mass choices  
  > "We verify our choice for distance (325 au) and stellar mass (1.59 M$_\odot$) by using the kinematics of the CO emission." (4.3)
5. **Dust mass**: Optically thin single-temperature dust mass equation  
  > "assuming the emitting dust is optically thin and of a single (average) temperature" (4.1 Mass limits)
   - parameter: kappa = 2.7 cm2/g at 0.867 mm; T_dust = 48 K  
  > "We adopt a dust opacity of 2.7 $cm^{2}~g^{-1}$ at 0.867 mm" (4.1 Mass limits)
   - assumption: Dust-to-gas ratio 1:100; distance 325 pc  
  > "With a dust-to-gas ratio of 1:100" (4.1 Mass limits)
   - fitting: _not stated_
   - validation: _not stated_
6. **Interpret asymmetry via companion**: Interpolate azimuthal contrast ratio against SPH simulation results to infer companion mass  
  > "a naive interpolation would put the companion mass at $\approx$ 0.05 M$_\odot$ (50 M$_{\mathrm{jup}}$)" (4.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration, CLEAN imaging, uvcontsub, moment maps  
  > "We image the disks with the CLEAN task in CASA" (2 Observations and data reduction)
- **uvmultifit** : Fitting geometric models to continuum visibilities  
  > "We use the fitting library *uvmultifit*" (3.1 continuum)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total flux at 345.8 GHz (best fit) | 323.9 | 3.0 | mJy | 2 | 323.9 (3.0) |
| Dust ring extent | 0.24 to 1.15 | not stated | arcsec | 3 | We resolve the disk around HD 34282 into a ring between 0.24 and 1.15$''$ |
| Inclination | 59.3 | 0.4 | deg | 2 | 59.3 (0.4) |
| Spectral slope | -3.0 | 0.7 | dimensionless | 2 | a spectral slope of -3.0 $\pm$ 0.7 |
| CO J=3-2 line flux | 21.2 | 0.3 | Jy km/s | 4 | is 21.2 $\pm$ 0.3 Jy km s$^{-1}$ |
| Systemic velocity | -2.35 | 0.10 | km/s | 4 | v$_{LSR}$ = -2.35 $\pm$ 0.10 km s$^{-1}$ |
| Dust mass of disk | 0.41 | not stated | Mjup | 5 | we calculate a dust mass of 0.41 M$_{\mathrm{jup}}$ for the disk |
| Azimuthal asymmetry FWHM | 52 | not stated | deg | 3 | with a FWHM of 0.15$''$ in radius and 52$^\circ$ in azimuth |
| CO gas inner radius limit | 23 | not stated | au | 4 | / CO J = 3-2 / 21.2 / 0.3 / 200 / 9.4 / 6.2 / 23 / |

## Qualitative findings

- CO emission is detected inside the dust cavity and out to 2.7 times the dust radial extent  
  > "We detect CO emission both inside the disk cavity and as far out as 2.7 times the radial extent of the dust emission." (abstract)

## Claim tuples

- H: The disk has a large dust cavity | E: Visibility model fitting of 345 GHz continuum | R: Ring between 0.24 and 1.15 arcsec (78 to 374 au) | F: Large cavity resolved | **supported**
- H: Cavity and azimuthal asymmetry are due to a companion rather than photoevaporation | E: Compare asymmetry contrast to SPH simulations and consider CO and SED constraints | R: Contrast ~1.25 implies ~0.05 Msun companion at ~0.1 arcsec | F: A ~50 Mjup brown dwarf companion explains the structure | **partially**
- H: Gas extends differently than dust | E: CO J=3-2 moment maps and channel maps | R: Gas traced to 3.1 arcsec (1000 au), factor ~2.7 beyond dust | F: Outer dust edge consistent with radial drift | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Photoevaporation deemed unlikely to have shaped the cavity  
  > "we deem photo evaporation unlikely to have shaped the cavity" (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust temperature is likely overestimated so dust mass is a lower limit  
  > "the resulting dust mass should thus be interpreted as a lower limit" (4.1)
- Caveat (inferred, ours): Companion mass from naive interpolation of one simulation set
- Caveat (inferred, ours): Sharp-edged geometric models leave radial residuals
- Caveat (inferred, ours): No direct companion detection
- Caveat (inferred, ours): Flux rescaling between configurations assumes constant emission

## Reproducibility

- Data public (paper): ALMA programme 2013.1.00658.S cited; public status not stated  
  > "This paper makes use of data from ALMA programme 2013.1.00658.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging and self-calibration parameters
- Missing: Exact flux scaling factor applied
- Missing: Initial uvmultifit setups
- Data volume (inferred): ~20-50 GB raw for two short Band 7 executions
- Score (inferred): 3/5, Data identified and the fitting approach is clear, but many imaging and self-calibration settings are missing.
- Rediscovery candidate: no, Key imaging and self-calibration settings are not given, and the data's public status is not stated in the paper.

## Links

- Method: (cite: 2014A&A...563A.136M) (uvmultifit visibility fitting)
- Companion: (cite: 2017A&A...597A..32V) (HD 97048 disk, a similar ALMA study)

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 43,
  "rate": 0.581
 },
 "evidence_ok": true
}
```
