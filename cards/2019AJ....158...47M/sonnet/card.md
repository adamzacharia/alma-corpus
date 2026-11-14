# Thermal Emission from the Uranian Ring System

`2019AJ....158...47M` | The Astronomical Journal 2019 | first author: Molter, Edward M. | arXiv: 1905.12566 | DOI: 10.3847/1538-3881/ab258c

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: What are the thermal emission properties (particle temperature, filling factor, azimuthal structure) of the Uranian main rings, and is micron-sized dust present?  
  > "we observed the thermal component of the Uranian ring system for the first time." (abstract)
- Target **Uranian ring system (epsilon ring and other main rings)**: coordinates _not stated_; z/distance d = 19.2, 19.6, 19.1 AU at 3.1, 2.1, 1.3 mm (Table 2)  
  > "The ring geometry at the time of observation in each band, taken from JPL Horizons[^1] and the Planetary Ring Node,[^2] are given in Table [2](#table_geom)." (2.1 ALMA Data); distance from JPL Horizons and Planetary Ring Node  
  > "The ring geometry at the time of observation in each band, taken from JPL Horizons[^1] and the Planetary Ring Node,[^2] are given in Table [2](#table_geom)." (2.1 ALMA Data)

## Data provenance

- ALMA projects: 2017.1.00855.S
- bands: Band 3 (3.1 mm), Band 4 (2.1 mm), Band 6 (1.3 mm)  
  > "with ALMA at three wavelengths (Band 3; 3.1 mm, Band 4: 2.1 mm, Band 6: 1.3 mm)" (Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Min/max baseline 41.4-5200 m (3.1 mm), 15.1-2500 m (2.1 mm), 15.1-1200 m (1.3 mm)  
  > "| 2.1 mm | 2017-12-27 22:56 | 22 | 15.1 | 2500 | J0238+1636 | J0121+1149 |" (Table 1)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 42 min x2 (3.1 mm), 22 min (2.1 mm), 24 min (1.3 mm)  
  > "| 1.3 mm | 2018-09-13 07:02 | 24 | 15.1 | 1200 | J0237+2848 | J0211+1051 |" (Table 1)
- observing dates: 2017-12-03, 2017-12-06 (3.1 mm); 2017-12-27 (2.1 mm); 2018-09-13 (1.3 mm)  
  > "| 3.1 mm | 2017-12-06 23:42 | 42 | 41.4 | 3600 | J0238+1636 | J0121+1149 |" (Table 1)
- pi or archival as stated: _not stated_
- Other facility **VLT VISIR (Q2 filter, 18.72 um)**: Mid-infrared thermal imaging of the rings, three nights Sept-Oct 2018  
  > "The 18.72 $\mu$m (Q2 filter) VISIR image combined observations from three nights in September and October 2018" (2.2 VLT Data)
- External data: Visible-wavelength equivalent widths of rings used to set relative ring contributions within groups  
  > "the relative contribution from each ring within a group was set according to its visible-wavelength equivalent width (cite: french86)." (3 Radial Profiles) [from (cite: french86)]
- External data: Gaussian prior on Bond albedo, mean 0.061, sd 0.006  
  > "a Gaussian prior on $A_B$ with mean value $0.061$ and standard deviation $0.006$ (cite: karkoschka97)" (4 Thermal Modeling) [from (cite: karkoschka97)]
- External data: Ring widths at periapsis and apoapsis; fractional visible area model  
  > "Let the measured width of the ring at periapsis and apoapsis be denoted $w_p$ and $w_a$ (cite: karkoschka01b)." (4 Thermal Modeling) [from (cite: karkoschka01b)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline run by North American ALMA Science Center, then phase-only self-calibration  
  > "The data in each of the three bands were flagged and calibrated by the North American ALMA Science Center using the standard data reduction procedures contained in the NRAO’s CASA software version 5.1.1." (2.1 ALMA Data)
- casa version: CASA 5.1.1  
  > "NRAO’s CASA software version 5.1.1" (2.1 ALMA Data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0238+1636 (3.1, 2.1 mm); J0237+2848 (1.3 mm)  
  > "| 1.3 mm | 2018-09-13 07:02 | 24 | 15.1 | 1200 | J0237+2848 | J0211+1051 |" (Table 1)
- flux scale uncertainty: 5.0%, 5.4%, 5.3% at 3.1, 2.1, 1.3 mm  
  > "The CASA pipeline retrieved flux calibration errors of 5.0%, 5.4%, and 5.3% at 3.1 mm, 2.1 mm, and 1.3 mm, respectively." (2.1 ALMA Data)
- self calibration: Iterative phase-only, solution intervals 20, 10, 5, 1 min  
  > "iterative phase-only self-calibration was performed using a procedure similar to that outlined in (cite: brogan18) using solution intervals of 20, 10, 5, and 1 minutes in that order." (2.1 ALMA Data)

### Imaging

- task: tclean after subtracting a uniform limb-darkened Uranus disk model in the uv plane  
  > "a uniform limb-darkened disk model of Uranus was subtracted from the data in the UV plane" (2.1 ALMA Data); "The disk-subtracted data were inverted into the image plane and deconvolved using CASA’s `tclean` function." (2.1 ALMA Data)
- deconvolver: _not stated_
- weighting robust: _not stated_
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
- final rms: _not stated_

### Inherited from earlier work

- Self-calibration procedure similar to Brogan et al.  
  > "using a procedure similar to that outlined in (cite: brogan18)" (2.1 ALMA Data) [from (cite: brogan18)]
- Uranus disk subtraction in uv plane  
  > "as done in e.g. (cite: depater14; depater16)" (2.1 ALMA Data) [from (cite: depater14; depater16)]
- CMB correction prescription for Uranus brightness  
  > "corrected to account for the blocked CMB photons according to the prescription in (cite: depater14)" (3 Radial Profiles) [from (cite: depater14)]

### Not stated but needed to reproduce (our reading)

- tclean parameters (weighting/robust, cell size, image size, niter, threshold, masks)
- Final beam sizes and image rms values per band
- Uranus disk model parameters (brightness temperature, limb darkening)
- Which self-cal iterations/spws were applied per dataset
- MCMC settings (walkers, steps, burn-in) and initial values
- Equivalent-width ratios used for within-group ring weights
- Eccentricity/width values adopted for epsilon ring area
- Beam-width mask details and VISIR pipeline version and IDL routines

## Analysis recipe

1. **Calibrate and image ALMA data**: CASA pipeline calibration, phase self-cal, uv-plane Uranus disk subtraction, tclean  
  > "The disk-subtracted data were inverted into the image plane and deconvolved using CASA’s `tclean` function." (2.1 ALMA Data)
   - software: CASA
   - fitting: _not stated_
   - validation: Uranus total flux compared to previous millimeter observations  
  > "The flux calibration was sanity-checked by comparing the measured total flux of Uranus to previous millimeter-wavelength observations" (2.1 ALMA Data)
2. **Azimuthally integrated radial profile and ring-group fluxes**: Elliptical annuli of 500 km ring-plane width from 35000 to 64500 km; model profiles of rings projected, beam-convolved; MCMC fit of four ring-group fluxes  
  > "Each annulus was given a ring-plane width of 500 km, and the ring-plane radius of the annulus inner edge was varied in steps of 500 km from 35000 km to 64500 km." (3 Radial Profiles)
   - software: photutils, PyAstronomy, emcee
   - parameter: Uranus masked to mean radius plus three times the beam FWHM  
  > "The planet Uranus was masked out to a distance equal to its mean radius plus three times the ALMA full beam width at half power in each observing band." (3 Radial Profiles)
   - assumption: Relative ring fluxes within a group follow visible equivalent widths  
  > "the relative contribution from each ring within a group was set according to its visible-wavelength equivalent width (cite: french86)." (3 Radial Profiles)
   - fitting: emcee MCMC, Gaussian likelihood with free fluxes F654, Falphabeta, Fetagammadelta, Fepsilon  
  > "the fluxes $F_{654}$, $F_{\alpha \beta}$, $F_{\eta \gamma \delta}$, and $F_\epsilon$ of the four ring groups were allowed to vary freely" (3 Radial Profiles)
   - validation: _not stated_
3. **Fit NEATM-like thermal model to epsilon ring fluxes**: Convert flux to brightness using projected ring area; fit Planck brightness with free eta, emissivity, Bond albedo, and fractional visible area via emcee  
  > "We allowed four parameters to vary: $\eta$, $\epsilon$, and $A_B$ in Equation [\[equation_neatm\]](#equation_neatm), and $f(B)$" (4 Thermal Modeling)
   - software: emcee
   - assumption: Gaussian prior on A_B = 0.061 +/- 0.006; eta, emissivity, f(B) unconstrained priors  
  > "We treated $\eta$, $\epsilon$, and $f(B)$ as completely unknown" (4 Thermal Modeling)
   - fitting: emcee MCMC, likelihood similar to Eq. for radial profile  
  > "compared with the measured ring group brightness using a likelihood function similar in form to Equation [\[lnlike\]](#lnlike)" (4 Thermal Modeling)
   - validation: Compared f(B) with Karkoschka model and T with STM/FRM toy particle model  
  > "Our derived fractional visible area is consistent with the (cite: karkoschka01b) model" (4 Thermal Modeling)
4. **Azimuthal structure of epsilon ring**: 30 azimuth bins of 12 deg, width 2x PSF FWHM, brightness vs angle from periapsis  
  > "breaking the ring into 30 bins, each subtending 12$^\circ$ of azimuth and having a width equal to two times the FWHM of the ALMA point-spread function" (5 Azimuthal Structure)
   - fitting: _not stated_
   - validation: Compared with occultation and reflected light results  
  > "in good agreement with stellar occultation measurements (cite: french86)" (5 Azimuthal Structure)

## Software

- **CASA** 5.1.1: Pipeline calibration, self-cal, tclean imaging  
  > "NRAO’s CASA software version 5.1.1" (2.1 ALMA Data)
- **photutils** v0.6: Elliptical annulus radial profiles  
  > "using the `astropy`-affiliated `photutils` Python package (cite: bradley19)" (3 Radial Profiles)
- **PyAstronomy** : Projecting model rings onto 2-D grid  
  > "using the `PyAstronomy` package in `Python`[^4]" (3 Radial Profiles)
- **emcee** : MCMC for ring flux and thermal model fits  
  > "implemented using the Python `emcee` package[^5] (cite: dfm13)" (3 Radial Profiles)
- **IDL** : VISIR flux calibration with standard stars  
  > "flux calibrated via comparison to observed standard stars using custom-written `IDL` routines" (2.2 VLT Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Epsilon ring particle temperature | 77.3 | 1.8 | K | 3 | the particle temperature to $T = 77.3 \pm 1.8$ K |
| Fractional visible area f(B) | 0.491 | 0.022 | dimensionless | 3 | $f(B) = 0.491 \pm 0.022$ |
| eta-bar times emissivity | 1.62 | 0.17 | dimensionless | 3 | $\bar{\eta} \epsilon = 1.62 \pm 0.17$ |
| Epsilon ring flux 3.1 mm | 13.73 | 0.73 | mJy | 2 | / 3.1        / 2017-12-03 / 36.8      / $1.29 \pm 0.15$ / $1.91 \pm 0.19$  / $2.77 \pm 0.22$          / $13.73 \pm 0.73$ / |
| Epsilon ring flux 2.1 mm | 36.0 | 2.2 | mJy | 2 | $8.15 \pm 0.89$ / $36.0 \pm 2.2$ |
| Epsilon ring flux 1.3 mm | 112.2 | 6.3 | mJy | 2 | $44.4 \pm 3.2$ / $112.2 \pm 6.3$ |
| Projected angular area of epsilon ring | 1.57e-12 | not stated | sr | 3 | $\Omega_{r,obs} = A_{r} \sin B / d^2 = 1.57\times10^{-12}$ steradians |

## Qualitative findings

- Epsilon ring is 2-3 times brighter at apoapsis than periapsis at 3.1 and 2.1 mm; no clear asymmetry at 1.3 mm or 18.7 um  
  > "We find the $\epsilon$ ring to be a factor of 2-3 brighter at apoapsis than at periapsis at 3.1 and 2.1 mm" (5 Azimuthal Structure)

## Claim tuples

- H: Ring particle temperature versus thermal inertia and rotation | E: NEATM-like MCMC fit to four-wavelength epsilon ring fluxes | R: T = 77.3 +/- 1.8 K, between STM (79.5 K) and FRM (71.5 K) | F: Particles have low thermal inertia and/or slow rotation | **partially**
- H: Micron-sized dust is absent in the main rings | E: Compare mm and mid-IR thermal emission with visible properties | R: Epsilon ring consistent with optical/NIR observations; scattered light negligible | F: No micron dust in the rings | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Surface roughness not modeled, so beaming cannot be separated from thermal inertia  
  > "Surface roughness is not included in our model, so we cannot disentangle the effects of beaming from the effects of thermal inertia." (4 Thermal Modeling)
- Caveat (inferred, ours): Parameters eta and emissivity are degenerate and albedo set by prior
- Caveat (inferred, ours): Only four flux points constrain a multi-parameter model
- Caveat (inferred, ours): Inner ring fluxes at 1.3 mm possibly affected by planet subtraction residuals

## Reproducibility

- Data public (paper): ALMA project 2017.1.00855.S cited; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00855.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: tclean imaging parameters
- Missing: Uranus disk model details
- Missing: MCMC configuration
- Data volume (inferred): ~50-200 GB raw for three ALMA bands
- Score (inferred): 3/5, Recipe is outlined, data are identified, but imaging and fitting settings are missing.
- Rediscovery candidate: no, Imaging parameters and disk model are unspecified, so exact redo is difficult.

## Links

- Method: (cite: harris98) (NEATM thermal model basis)
- Method: (cite: karkoschka01b) (Fractional visible area model)

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 40,
  "rate": 0.556
 },
 "evidence_ok": true
}
```
