# ALMA observations of the circumstellar envelope around EP Aqr

`2019RAA....19...43N` | Research in Astronomy and Astrophysics 2019 | first author: Tuyet Nhung, Pham Thi | arXiv: 1810.04423 | DOI: 10.1088/1674-4527/19/3/43

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: What are the morphology and kinematics of the EP Aqr circumstellar envelope (bipolar vs spherical vs equatorial wind, axi-symmetry, orientation), inferred directly from CO(1-0) and CO(2-1) data without a physical model?  
  > "The aim of the present article is limited to a presentation of the morphology and kinematics of the circumstellar envelope of EP Aqr inferred directly from the observational data without invoking a physical model." (Observations and data reduction)
- Target **EP Aqr**: coordinates RA=21h 46m 31.848 s, DEC=-02d12'45.93'' (J2000 epoch)  
  > "EP Aqr is an oxygen-rich M type semi-regular variable AGB star at a distance of only 114 $\pm$ 8 pc from the solar system (van Leeuwen 2007)" (Introduction); "The origin of coordinates at RA=21h 46m 31.848 s and DEC=$-$02$^\circ$12$'$ 45.93$''$ corresponds to year 2000." (Observations and data reduction); z/distance 114 ± 8 pc  
  > "EP Aqr is an oxygen-rich M type semi-regular variable AGB star at a distance of only 114 $\pm$ 8 pc from the solar system (van Leeuwen 2007)" (Introduction); "The origin of coordinates at RA=21h 46m 31.848 s and DEC=$-$02$^\circ$12$'$ 45.93$''$ corresponds to year 2000." (Observations and data reduction); distance from van Leeuwen 2007 (Hipparcos)  
  > "EP Aqr is an oxygen-rich M type semi-regular variable AGB star at a distance of only 114 $\pm$ 8 pc from the solar system (van Leeuwen 2007)" (Introduction); "The origin of coordinates at RA=21h 46m 31.848 s and DEC=$-$02$^\circ$12$'$ 45.93$''$ corresponds to year 2000." (Observations and data reduction)

## Data provenance

- ALMA projects: 2016.1.00026.S
- bands: _not stated_
- frequencies and spectral setup: Channel spacings 30 and 60 kHz with 3840 and 1920 channels for CO(1-0) and CO(2-1); ~80 m/s velocity resolution  
  > "The correlator was set up with channel spacings of 30 and 60 kHz with widths of 3840 and 1920 channels for CO(1-0) and CO(2-1) respectively" (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-2 and C40-5, merged in the uv plane  
  > "Both lines were observed in two different configurations, C40-2 and C40-5 and the data were then merged in the uv plane." (Observations and data reduction)
- baselines: CO(1-0): 19-1124 m; CO(2-1): 15-1400 m  
  > "Max. baseline | 1124 m | 1400 m" (Table 1)
- angular resolution: CO(1-0) 0.78''x0.70'' PA -56 deg; CO(2-1) 0.33''x0.30'' PA -80 deg  
  > "Beam FWHM | $0.78''\times0.70''$ | $0.33''\times0.30''$ |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: 7 and 6 mJy/beam per 0.2 km/s bin (CO(1-0), CO(2-1))  
  > "(mJy beam$^{-1}$/0.2 km s$^{-1}$ bin) | 7 | 6 |" (Table 1)
- time on source: 98.3 min (CO(1-0)); 52.4 min (CO(2-1))  
  > "Time on source | 98.3 min | 52.4 min |" (Table 1)
- observing dates: 30 Oct 2016 to 5 Apr 2017 (Cycle 4)  
  > "between October 30th 2016 and April 5th 2017" (Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (not stated)
- Line: 12CO J=2-1 (not stated)
- External data: Distance 114 ± 8 pc and proper motion [24.98, 19.54] mas/yr  
  > "proper motion of \[24.98, 19.54\] mas/yr taken from van Leeuwen 2007" (Observations and data reduction) [from van Leeuwen 2007 (cite: van Leeuwen 2007)]

## Processing

### Calibration

- pipeline or manual: ALMA-provided calibration scripts  
  > "We used the calibration scripts provided by ALMA and the CASA 4.7.2 software package to obtain the calibrated data." (Observations and data reduction)
- casa version: CASA 4.7.2  
  > "We used the calibration scripts provided by ALMA and the CASA 4.7.2 software package to obtain the calibrated data." (Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Quasar J2148+0657 and Neptune  
  > "Flux calibrators were quasar J2148+0657 and Neptune." (Observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: Imaging in GILDAS after UVFITS export  
  > "exported through UVFITS format to the GILDAS package for imaging" (Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We use natural weighting resulting in beam sizes which are given in Table [1]" (Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: C40-2 and C40-5 merged in uv plane; no zero spacing  
  > "Zero spacing | No | No |" (Table 1)
- smoothing: Channels smoothed to 0.2 km/s; velocity range -20 to 20 km/s  
  > "The spectral resolution (channel) has been smoothed to 0.2 km s$^{-1}$" (Observations and data reduction)
- final beam: 0.78''x0.70'' (CO 1-0); 0.33''x0.30'' (CO 2-1)  
  > "Beam FWHM | $0.78''\times0.70''$ | $0.33''\times0.30''$ |" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- De-projection method and effective emissivity concept  
  > "This feature was discussed in some detail in Nhung et al. (2015a) and Diep et al. (2016) and is again extensively exploited in the present article" (Introduction) [from Nhung et al. (2015a); Diep et al. (2016)]
- Temperature-corrected emissivity with LTE; quantitative physical modelling deferred  
  > "A detailed analysis of these observations in terms of density and temperature, rather than effective emissivity as in the present article, is the subject of another publication (Hoai et al., in preparation)" (Summary and conclusions) [from Hoai et al., in preparation]

### Not stated but needed to reproduce (our reading)

- Imaging pixel size, image size, deconvolution/cleaning parameters in GILDAS
- Continuum subtraction and line-free channels
- Primary beam correction details
- Rest frequencies and exact velocity frame handling
- Interpolation and binning details of the de-projection code (code not released)
- Details of the preliminary radiative transfer giving T=32/r^0.65
- Flux scale uncertainty

## Analysis recipe

1. **Calibrate and image the data**: ALMA calibration scripts in CASA, UVFITS export, natural-weight imaging in GILDAS; proper motion correction; smoothing to 0.2 km/s  
  > "The CO(1-0) and CO(2-1) data have been calibrated using CASA[^1] and the mapping was done with GILDAS[^2]." (Observations and data reduction)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **De-project data cube to effective emissivity**: Assume radial wind velocity field and relation z/r=Vz/V; rho=f dVz/dz  
  > "The relation between $z$ and $V_z$ becomes particularly simple in the case of pure radial expansion, the velocity becoming a simple scalar $V$: $$\begin{equation}   z/r=V_z/V \end{equation}$$" (3.1 The method)
   - parameter: Wind V=Veq+(Vpole-Veq)(sin^2 alpha)^n with n=0.5,1,2.4; larger velocity adjusted to cover whole spectrum  
  > "we always adjust the larger of $V_{pole}$ and $V_{eq}$ in such a way as to account for the whole observed Doppler velocity spectrum, but not larger than necessary" (3.4 Dependence of the flux of matter on r and alpha)
   - assumption: Radial wind, axi-symmetry, velocity independent of r (or with a gradient to 12.5 km/s at 9 arcsec); distance 114 pc  
  > "The wind configuration used for de-projection is spherical but assumes a constant positive radial velocity gradient, the wind velocity increasing from 0 at $r=0$ to 12.5 km s$^{-1}$ at $r=9$ arcsec" (3.2 Orientation of the star axis)
   - fitting: _not stated_
   - validation: CO(1-0) and CO(2-1) compared after temperature correction  
  > "one obtains a very good agreement between CO(1-0) and CO(2-1) results after correction for temperature" (3.4 Dependence of the flux of matter on r and alpha)
3. **Determine star axis orientation via chi2_axi**: Minimise chi2_axi = <D^2> over axis tilt phi and position angle theta  
  > "we define $\chi^2_{axi} = <D^2(R',z',\omega)>$ as a figure of merit measuring the deviation from axi-symmetry" (3.2 Orientation of the star axis)
   - parameter: Error on phi from 10% increase in chi2_axi  
  > "where the error corresponds to a 10% increase in $\chi^2_{axi}$" (3.5 Deviations from axi-symmetry and disc rotation)
   - fitting: _not stated_
   - validation: Consistency between CO(1-0) and CO(2-1)  
  > "with excellent agreement between the CO(1-0) and CO(2-1) lines" (3.5 Deviations from axi-symmetry and disc rotation)
4. **Temperature-corrected emissivity and flux of matter**: rho*=rho/Q under LTE with T=32/r^0.65 K; Mdot=rho* V r^2; UV dissociation factor  
  > "As radial dependence of the temperature we assume a form $T=32/r^{0.65}$ K with $r$ measured in arcsec" (3.4 Dependence of the flux of matter on r and alpha)
   - assumption: LTE; T=32/r^0.65 K from a preliminary radiative transfer calculation  
  > "As radial dependence of the temperature we assume a form $T=32/r^{0.65}$ K with $r$ measured in arcsec (one of possible forms obtained in a preliminary radiative transfer calculation)." (3.4 Dependence of the flux of matter on r and alpha)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2: Calibration  
  > "We used the calibration scripts provided by ALMA and the CASA 4.7.2 software package to obtain the calibrated data." (Observations and data reduction)
- **GILDAS** : Imaging/mapping  
  > "the mapping was done with GILDAS" (Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Tilt angle phi where chi2_axi doubles (spherical, constant velocity) | 5 | not stated | deg | 3 | The value of $\varphi$ for which $\chi^2_{axi}$ reaches twice its minimal value is 5$^\circ$ for both emissions |
| Tilt angle phi (equatorial disc region) | 3.8 | ±2.0 | deg | 3 | the former displays a clear minimum at $\varphi = 3.8 \pm 2.0^\circ$ |
| Position angle theta at minimum | 35 | ±35 | deg | 3 | The value of $\theta$ at minimum is less well defined and of the order of 35 $\pm$ 35$^\circ$. |
| Radius of flux-of-matter maximum | 3 to 6 (~500 AU) | not stated | arcsec | 4 | the radial dependence of the flux of matter is always found to display a maximum at distances between 3 and 6 arcsec, namely $\sim$ 500 AU, from the star |

## Qualitative findings

- De-projected emissivity shows polar depression and equatorial enhancement (flared disc or ring)  
  > "strong polar depression and equatorial enhancement, remain qualitatively present for other wind models" (3.3 Bipolar, spherical and equatorial winds)

## Claim tuples

- H: Is the EP Aqr envelope intrinsically non-spherical axi-symmetric about an axis near the line of sight? | E: chi2_axi versus phi, theta using spherical de-projection | R: Steep minimum near phi=0; doubling at 5 deg (13-15 deg with gradient) | F: Intrinsic non-spherical axi-symmetry with small tilt | **supported**
- H: Bipolar vs equatorial wind | E: Compare de-projected models with different Vpole/Veq and n | R: Equatorial winds need higher velocities and give steeper flux decrease | F: Bipolar winds preferred, with equatorial enhancement | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Equatorial wind models require very high equatorial velocities; spherical symmetry disfavoured by chi2_axi dependence on phi  
  > "In case of spherical symmetry, one would find instead that $\chi^2_{axi}$ is independent of $\varphi$." (3.2 Orientation of the star axis)
- How they decided it was enough: _not stated_
- Limitation (authors): Rotation vs expansion cannot be distinguished; absorption/optical depth ignored  
  > "would probably require data of better spatial resolution and signal-to-noise ratio and is beyond the scope of the present article" (3.5 Deviations from axi-symmetry and disc rotation)
- Caveat (inferred, ours): Any velocity field reproduces data by construction; model preference is weakly constrained
- Caveat (inferred, ours): Ad hoc temperature law and no optical depth treatment
- Caveat (inferred, ours): No uncertainties on most results

## Reproducibility

- Data public (paper): ALMA project code given; acknowledges use of ALMA data  
  > "This paper makes use of the following ALMA data: 2016.1.00026.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: De-projection code
- Missing: GILDAS imaging scripts and parameters
- Data volume (inferred): ~50-200 GB raw
- Score (inferred): 3/5, Data identified and formulas given, but imaging parameters and code are missing.
- Rediscovery candidate: no, Custom unreleased de-projection code and few numerical results.

## Links

- Method: Diep et al. 2016 (cite: Diep et al. 2016) (De-projection method)
- Companion: Nhung et al. 2015a (IRAM/PdBI analysis of EP Aqr)

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 38,
  "rate": 0.567
 },
 "evidence_ok": true
}
```
