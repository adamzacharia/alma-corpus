# A Very Compact Extremely High Velocity Flow toward MMS 5/OMC-3 Revealed with ALMA

`2019ApJ...871..221M` | The Astrophysical Journal 2019 | first author: Matsushita, Yuko | arXiv: 1811.08060 | DOI: 10.3847/1538-4357/aaf1b6

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Do the low-velocity outflow and extremely high-velocity (EHV) jet of the Class 0 protostar MMS 5 follow the nested disk wind or jet entrainment scenario?  
  > "In order to specify the driving mechanism of protostellar outflows, we choose a unique EHV flow associated with MMS 5, which is located in the Orion Molecular Cloud 3 (OMC-3)" (INTRODUCTION)
- Target **MMS 5 / OMC-3 (HOPS 88)**: coordinates RA 05h35m22.464s, Dec -05d01m14.304s (J2000)  
  > "toward MMS 5 (R.A. = $05^{h}35^{m}22^{s}.464$, Dec = $-05^{\circ}01'14''.304$)" (2 ALMA OBSERVATIONS AND DATA REDUCTION); "as our sample distance of $d \sim 388$ pc (Kounkel et al. 2017)" (INTRODUCTION); z/distance d ~ 388 pc  
  > "toward MMS 5 (R.A. = $05^{h}35^{m}22^{s}.464$, Dec = $-05^{\circ}01'14''.304$)" (2 ALMA OBSERVATIONS AND DATA REDUCTION); "as our sample distance of $d \sim 388$ pc (Kounkel et al. 2017)" (INTRODUCTION); distance from Kounkel et al. 2017  
  > "toward MMS 5 (R.A. = $05^{h}35^{m}22^{s}.464$, Dec = $-05^{\circ}01'14''.304$)" (2 ALMA OBSERVATIONS AND DATA REDUCTION); "as our sample distance of $d \sim 388$ pc (Kounkel et al. 2017)" (INTRODUCTION)

## Data provenance

- ALMA projects: 2015.1.00341.S
- bands: _not stated_
- frequencies and spectral setup: Four spectral windows: CO 2-1 and SiO 5-4 with 468.75 MHz bandwidth; C18O and N2D+ with 58.594 MHz; Frequency Division Mode  
  > "Spectral windows allocated for CO $J$=2–1 and SiO $J$=5–4 have a bandwidth of 468.75 MHz" (2 ALMA OBSERVATIONS AND DATA REDUCTION)
- continuum bandwidth: ~1.1 GHz effective after line subtraction  
  > "After subtraction of line emissions, the effective bandwidth for the continuum emissions is approximately 1.1 GHz." (2 ALMA OBSERVATIONS AND DATA REDUCTION)
- arrays: ALMA 12-m array (compact and extended) and ACA 7-m array  
  > "Our ALMA 12-m array and ACA 7-m array (Morita-array) observations were performed between 2016 January 29 and September 18" (2 ALMA OBSERVATIONS AND DATA REDUCTION)
- configurations: _not stated_
- baselines: 7–47 m (ACA), 10–310 m (12-m LAR), 10–3130 m (12-m HAR)  
  > "Projected baseline coverage (m) | 7–47 | 10–310 | 10–3130" (Table 1)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 16 min ACA, 4 min 12-m compact, 8 min 12-m extended  
  > "The total on source time was 16 minutes for the ACA 7-m array, 4 minutes for the ALMA 12-m array compact configuration" (2 ALMA OBSERVATIONS AND DATA REDUCTION)
- observing dates: 2016 January 29 to September 18, 7 executions  
  > "with 7 separate executions" (2 ALMA OBSERVATIONS AND DATA REDUCTION)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230.538 GHz)
- Line: SiO J=5-4 (217.105 GHz)
- Line: C18O J=2-1 (219.560 GHz)
- Line: N2D+ J=3-2 (231.322 GHz)
- External data: Dust temperature T_dust = 21.5 K  
  > "Here, $T_{\rm{dust}}$ = 21.5 K is adopted (Sadavoy et al. 2016)." (3.1 1.3 mm Continuum Emission) [from Sadavoy et al. 2016]
- External data: 3.6 cm flux density 0.12 mJy (3 sigma upper limit)  
  > "based on the 3.6 cm flux density of 0.12 mJy with 3$\sigma$ upper limit (Reipurth et al. 1999)" (3.1 1.3 mm Continuum Emission) [from Reipurth et al. 1999]
- External data: Dust opacity kappa_1.3mm = 0.009 cm^2/g  
  > "We adopt $\kappa_{1.3\rm{mm}} = 0.009\ \rm{cm^2\ g^{-1}}$" (3.1 1.3 mm Continuum Emission) [from Ossenkopf & Henning (1994)]

## Processing

### Calibration

- pipeline or manual: Standard calibration performed by the ALMA observatory with CASA  
  > "Calibration of the raw visibility data was performed by the ALMA observatory with the standard calibration method using the Common Astronomy Software Application" (2 ALMA OBSERVATIONS AND DATA REDUCTION)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0522-3627 (ACA, 12-m LAR); J0510+1800 (12-m HAR)  
  > "Flux calibrator | J0522-3627 | J0522-3627 | J0510+1800" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "robust weighting with the Briggs parameter = 0.5 was used" (2 ALMA OBSERVATIONS AND DATA REDUCTION)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Line-free channels used for continuum  
  > "The channels that have no detection of the line emission are used to produce the continuum image." (2 ALMA OBSERVATIONS AND DATA REDUCTION)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: ACA + 12-m compact (LAR image); 12-m extended (HAR image)  
  > "Data sets obtained with the three different array configurations are combined in order to produce final images." (2 ALMA OBSERVATIONS AND DATA REDUCTION)
- smoothing: _not stated_
- final beam: Continuum LAR 1.8x1.0 arcsec; HAR 0.20x0.16 arcsec  
  > "1.3mm continuum | 12-m array HAR image | $0.20 \times 0.16$, -22 | 0.9" (Table 2)
- final rms: Continuum 3.3 mJy/beam (LAR), 0.9 mJy/beam (HAR)  
  > "1.3mm continuum | ACA+12-m array LAR image | $1.8 \times 1.0$, -77 | 3.3" (Table 2)

### Inherited from earlier work

- Outflow shell model (wind-driven) and derivation of v0 and inclination follow Lee et al. 2000  
  > "we use a simplified analytical model (wind-driven model) introduced by Lee et al. (2000)" (3.5 Physical Parameters of Outflow and Jet) [from Lee et al. 2000]

### Not stated but needed to reproduce (our reading)

- CASA version
- Channel ranges/line-free channels and continuum subtraction method
- tclean parameters: cell size, image size, masks, threshold, deconvolver
- Velocity ranges integrated for moment maps
- Procedure for fitting shell curvature C and v0 (fit method, uncertainties)
- How knot positions and the sine wiggle were measured and fit
- Relative weighting used when combining ACA and 12-m data

## Analysis recipe

1. **Image continuum and lines**: CLEAN images from calibrated visibilities with combined arrays, Briggs weighting  
  > "The calibrated visibility data were CLEANed to create the continuum and molecular line images." (2 ALMA OBSERVATIONS AND DATA REDUCTION)
   - software: CASA
   - parameter: robust = 0.5; velocity resolution 5.0 km/s for CO and SiO, 0.1 km/s for C18O and N2D+  
  > "CO $J$=2–1 and SiO $J$=5–4 imaging velocity resolution ($\rm{km\ s^{-1}}$) $^{c}$ | 5.0" (Table 1)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit compact continuum source and derive disk mass**: 2D Gaussian fit with IMFIT; mass from optically thin dust emission formula  
  > "two-dimensional Gaussian fitting tool in CASA (task $\lq\lq$IMFIT") was used." (3.1 1.3 mm Continuum Emission)
   - software: CASA imfit
   - assumption: kappa=0.009 cm^2/g, gas-to-dust 100, T_dust=21.5 K, d=388 pc  
  > "We assume a gas-to-dust mass ratio of 100." (3.1 1.3 mm Continuum Emission)
   - fitting: _not stated_
   - validation: Residual less than 10% of peak flux  
  > "The residual after extraction of the two-dimensional Gaussian fit is less than 10 % as compared to the peak flux." (3.1 1.3 mm Continuum Emission)
3. **Derive outflow inclination and curvature**: Fit wind-driven shell model z=CR^2 to CO outflow and PV diagrams  
  > "The curvature parameter is fit to the outflow shells as $C$ = 0.07 $\rm{arcsec^{-1}}$." (3.5 Physical Parameters of Outflow and Jet)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compute sizes, velocities, dynamical timescales**: t_dyn ~ (L_obs/v_obs) tan 50 deg; L_obs measured at 10 sigma contour in channel maps  
  > "The projected maximum size of CO $J$=2–1 and SiO $J$=5–4 emission, $L_{\rm obs}$, was measured at the 10 $\sigma$ contour in their channel maps" (3.5 Physical Parameters of Outflow and Jet)
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: _not stated_
5. **Analyze jet knots, precession and launching radius**: Knot spacing, sine fit of wiggle, Keplerian relations for precession and launching radius  
  > "The wiggling is fitted by a simple sine curve in Figure [9](#fig:6-2)(c)" (4.2 Episodic Mass Ejection of Jet)
   - assumption: M* = 0.1 Msun  
  > "When the protostellar mass of 0.1 $M_\odot$ is assumed[^2], the precession radius becomes approximately 6 AU." (4.2 Episodic Mass Ejection of Jet)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration, CLEAN imaging, IMFIT Gaussian fitting  
  > "Calibration of the raw visibility data was performed by the ALMA observatory with the standard calibration method using the Common Astronomy Software Application (CASA; McMullin et al. 2007)." (2 ALMA OBSERVATIONS AND DATA REDUCTION)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Compact 1.3 mm continuum total flux (HAR) | 57 | ±3 | mJy | 2 | The total flux, peak flux, and deconvolved size are measured to be $57 \pm 3$ mJy |
| Circumstellar mass from 1.3 mm | 1.8e-2 | not stated | Msun | 2 | the mass is estimated to be $M_{1.3\rm{mm}} \sim$ 1.8 $\times\ 10^{-2} M_{\odot}$. |
| Outflow inclination to plane of sky | 50 | not stated | deg | 3 | the inclination angle of the outflow axis with respect to the plane of the sky was $i=50^{\circ}$ |
| CO outflow dynamical time | 1,300 | not stated | yr | 4 | outflow (CO $J$=2–1)…… / 9,300 / 14,000 / 30 / 40 / 1,300 |
| CO jet dynamical time | 470 | not stated | yr | 4 | jet (CO $J$=2–1)……… / 7,000 / 11,000 / 70 / 90 / 470 |
| SiO jet dynamical time | 110 | not stated | yr | 4 | jet (SiO $J$=5–4)……… / 1,600 / 2,500 / 70 / 90 / 110 |
| Precession period | ~50 | not stated | yr | 5 | the period of the cycle can be estimated to be $P \sim 50$ yr |
| Precession radius | ~6 | not stated | AU | 5 | the precession radius becomes approximately 6 AU |
| Mean knot spacing | 0.46 (median 0.36) | not stated | arcsec | 5 | The average and median spacings are measured to be $\Delta \theta \simeq$ 0.46 and 0.36 arcsec |
| Jet launching radius | ~1 | not stated | Rsun | 5 | our result indicates that the jet appears near the surface of the protostar |

## Qualitative findings

- SiO 5-4 traces only the EHV jet, located at the root of the V-shaped CO outflow  
  > "On the other hand, SiO $J$=5–4 emission only traces the EHV flow." (abstract)

## Claim tuples

- H: Is the jet younger and shorter than the outflow, as the nested disk wind predicts? | E: Measured sizes and dynamical times of CO outflow and CO/SiO jet from channel maps and PV diagrams with inclination 50 deg | R: Jet 11,000 AU vs outflow 14,000 AU; t_dyn ratio ~3 | F: Consistent with nested disk wind, entrainment not fully excluded | **supported**
- H: Are the jet and outflow axes aligned? | E: Compared position angles of CO outflow and CO/SiO jet | R: Axis difference ~17-18 deg | F: Different launching radii/epochs | **supported**
- H: Does the jet show episodic ejection and precession? | E: Identified six knots and fit sine curve to wiggle | R: Ejection every ~9–12 yr, precession ~50 yr at ~6 AU | F: Episodic ejection and possible precession | **partially**

## Reasoning

- Why this data: MMS 5 hosts one of the most compact EHV flows, best for studying driving just after protostar formation  
  > "the MMS 5 is the best object to clarify the driving mechanisms of respective velocity flows immediately after protostar formation." (INTRODUCTION)
- Why this method: _not stated_
- Alternative: Jet entrainment scenario not completely ruled out  
  > "although the jet entrainment scenario could not completely be ruled out" (4.1 Driving Mechanism of Outflow and Jet)
- How they decided it was enough: _not stated_
- Limitation (authors): Launching points not resolved; further high-resolution observations needed for precession mechanism  
  > "Although we are not able to spatially resolve the outflow and jet launching points (or radii) due to the limited angular resolution" (4.1 Driving Mechanism of Outflow and Jet)
- Caveat (inferred, ours): Inclination of 50 deg is derived from a simple shell model and strongly affects timescales, with no uncertainty given
- Caveat (inferred, ours): Stellar mass of 0.1 Msun assumed
- Caveat (inferred, ours): Sine fit to six knots with one outlier is weak evidence for precession
- Caveat (inferred, ours): Dynamical age ratio is not a unique discriminator between scenarios

## Reproducibility

- Data public (paper): Data cited by project code 2015.1.00341.S in acknowledgment  
  > "This paper uses the following ALMA data: ADS/JAO.ALMA #2015.1.00341.S." (ACKNOWLEDGMENT)
- Products in archive: _not stated_
- Missing: CASA version and tclean settings
- Missing: Moment integration ranges
- Missing: Shell model fitting details
- Missing: Knot identification procedure
- Data volume (inferred): ~50-150 GB raw for 7 executions (ACA + 12-m)
- Score (inferred): 3/5, Public data and standard imaging, but many imaging and fitting details are unstated.
- Rediscovery candidate: no, Key results rely on unstated imaging parameters and manual measurements of size, velocity and knots.

## Links

- Method: Lee et al. 2000 (Wind-driven shell model used for inclination)
- Companion: Gomez-Ruiz et al., submitted (APEX detection of EHV flow from MMS 5)

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
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
  "facts": 70,
  "stated": 36,
  "rate": 0.514
 },
 "evidence_ok": true
}
```
