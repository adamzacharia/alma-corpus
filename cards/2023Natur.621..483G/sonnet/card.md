# Polarized thermal emission from dust in a galaxy at redshift 2.6

`2023Natur.621..483G` | Nature 2023 | first author: Geach, J. E. | arXiv: 2309.02034 | DOI: 10.1038/s41586-023-06346-4

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Is there a large-scale ordered magnetic field in a z=2.6 lensed starburst galaxy, as traced by polarized dust emission?  
  > "it is not known how early in the Universe such structures form" (abstract)
- Target **9io9**: coordinates RA 02h09m41.3s, Dec +00d15m58.5s (J2000)  
  > "9io9 at celestial coordinates $\alpha=02^{\rm hr}$09$^{\rm m}$41.3$^{\rm s}$, $\delta = +00^\circ$15$'$58.5$''$ (J2000)" (Methods); z/distance z=2.6  
  > "9io9 at celestial coordinates $\alpha=02^{\rm hr}$09$^{\rm m}$41.3$^{\rm s}$, $\delta = +00^\circ$15$'$58.5$''$ (J2000)" (Methods); distance from _not stated_

## Data provenance

- ALMA projects: 2021.1.01461.S
- bands: _not stated_
- frequencies and spectral setup: 242 GHz representative frequency, full polarization  
  > "at a representative frequency of 242 GHz (equivalent to a wavelength of approximately 350 $\mu$m in the rest-frame of the galaxy)" (main text)
- continuum bandwidth: 7.5 GHz total  
  > "averaged over a total bandwidth of 7.5 GHz" (main text)
- arrays: ALMA 12 m array  
  > "was observed by the ALMA 12 m array in project 2021.1.01461.S" (Methods)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.2'' x 0.9'' at PA 68 deg  
  > "the final beam shape has a full width half maximum of $1.2''\times 0.9''$ at position angle 68 degrees" (Methods)
- max recoverable scale: _not stated_
- sensitivity: sigma_I = 47 uJy/beam; sigma_Q ~ sigma_U = 9 uJy/beam  
  > "$\sigma_{I} = 47\,\mu\text{Jy}\,\text{beam}^{-1}$ and $\sigma_{Q} \sim \sigma_{U} = 9\,\mu\text{Jy}\,\text{beam}^{-1}$" (main text)
- time on source: _not stated_
- observing dates: 12 April 2022 (two EBs) and 14 April 2022 (one EB)  
  > "The first session, comprising two Execution Blocks, was executed on 12 April 2022, and the second, comprising one Execution Block, was executed on 14 April 2022." (Methods)
- pi or archival as stated: _not stated_
- External data: Lens model parameters (SIE+shear) and CO(4-3) disk model (Rmax, Vmax, tilt, inclination)  
  > "Extended Data Table 1 summarises the best-fit lens model parameters from$^5$." (Methods) [from Geach2018]
- External data: Molecular gas mass, velocity dispersion and disk height from CO  
  > "The total molecular mass is estimated from the CO luminosity$^5$ as $M_{\rm{H_{2}}} = (7.5\pm0.1)\times10^{10}$ M$_{\odot}$" (Energy equipartition) [from Geach2018]
- Simulation/model as data: Simulated ALMA observations of lensed source-plane model B-field via lenstronomy and CASA simobserve  
  > "To mimic the observed data, we use the *simobserve* task of CASA" (Lens modelling)

## Processing

### Calibration

- pipeline or manual: Standard ALMA pipeline plus additional polarization calibration script  
  > "using both the standard ALMA calibration pipeline and an additional polarization calibration script" (Observations and data reduction)
- casa version: CASA 6.2.1  
  > "Common Analysis Software Applications (CASA) version 6.2.1" (Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J2253+1608 (bandpass and flux); J0006-0623 polarization calibrator  
  > "The ALMA grid source J2253+1608 was observed as a bandpass and flux calibrator, J0006$-$0623 was used as the polarization calibrator" (Observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean, IQUV Stokes images  
  > "The procedure *tclean* is used to produce the *IQUV* Stokes images" (Observations and data reduction)
- deconvolver: clarkstokes  
  > "with the ‘*clarkstokes*’ deconvolver, natural weighting of the visibilities and a common restoring beam" (Observations and data reduction)
- weighting robust: natural weighting  
  > "natural weighting of the visibilities and a common restoring beam" (Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied; negligible for compact target  
  > "All images are primary beam corrected to account for fall-off in sensitivity away from the phase centre" (Observations and data reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.2'' x 0.9'' PA 68 deg common beam  
  > "the final beam shape has a full width half maximum of $1.2''\times 0.9''$ at position angle 68 degrees" (Observations and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- Lens model and CO(4-3) disk kinematic model  
  > "The morphology of the continuum thermal emission in the source plane is assumed to match that of the CO(4–3) molecular gas emission$^5$." (Lens modelling) [from Geach2018]

### Not stated but needed to reproduce (our reading)

- Image size and cell size for tclean
- Polarization calibration script details and polarization calibrator model
- Self-calibration, if any
- Pipeline version
- Masking used in cleaning
- Exact sensitivity-weighted selection of pixels for averages
- Total on-source time

## Analysis recipe

1. **Calibrate and image Stokes IQU**: ALMA pipeline plus polarization calibration; tclean on all Stokes with common beam  
  > "The polarization calibration script derives and applies additional corrections for instrument-related polarization effects" (Observations and data reduction)
   - software: CASA
   - parameter: clean threshold 10 uJy  
  > "Dirty images are cleaned to a stopping threshold of 10 $\mu$Jy" (Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure polarization fraction and B-field angle**: Debiased P from mean Q,U,I for pixels with P/sigma_P>=3; chi_B = 0.5 arctan(U/Q)+pi/2; mean from independent beams  
  > "for measurements with a polarized intensity signal to noise ratio $P/\sigma_{P} \ge 3$" (Measuring polarization)
   - fitting: _not stated_
   - validation: MDP of 0.1 per cent added in quadrature to uncertainties  
  > "all quoted uncertainties in this work have the minimum detectable polarization of 0.1 per cent added in quadrature" (Observations and data reduction)
3. **Constrain source-plane B-field orientation via lens simulation**: Lens source-plane Gaussian disk with constant chi_B and P=1%, lensed with SIE+shear, simulated with simobserve, cleaned like data; compare Stokes U detection  
  > "We can constrain the orientation by rotating the *B*-field until the corresponding Stokes $U$ image shows a $3\sigma$ detection in the synthetic polarimetric observations." (Constraining the B-field orientation)
   - software: lenstronomy, CASA simobserve
   - parameter: 801x801 grid, 0.01'' pixel; pwv 0.6 mm; antenna configuration 2 (Cycle 8)  
  > "Using a grid of $801\times801$ pixels$^{2}$ with a scale of $0.01\mbox{$^{\prime\prime}$}$ pixel$^{-1}$" (Lens modelling)
   - assumption: Constant polarization fraction of unity/1% and constant B orientation in source plane; continuum matches CO morphology  
  > "The *B*-field orientation in the source plane is assumed to be constant, $\chi_{B,{\rm sp}}$, with a constant polarization fraction of unity" (Lens modelling)
   - fitting: Grid of chi_B values, no sampler  
  > "With a polarization fraction of 1% we set a range of constant $\chi_{B,{\rm sp}}$ orientations in the source plane." (Methods, Constraining the B-field orientation)
   - validation: Lens and convolution do not rotate or change P; noise adds ~10 deg uncertainty  
  > "We conclude that the lens model and convolution do not produce rotation or change in the polarization fraction from the source plane to the image plane." (Constraining the B-field orientation)
4. **Equipartition B-field strength**: B_eq = sqrt(4 pi rho) sigma_v with rho from H2 mass over disk volume  
  > "Then, assuming equipartition, $U_{K} = U_{B}$, the field strength is" (Energy equipartition)
   - parameter: r=2647 pc, h<=600 pc, M_H2=7.5e10 Msun, sigma_v=73 km/s  
  > "the velocity dispersion of the gas is $\sigma_{\rm{v}} = 73\pm4$ km s$^{-1}$" (Energy equipartition)
   - assumption: Equipartition of turbulent kinetic and magnetic energy  
  > "assuming equipartition between the turbulent kinetic energy and the turbulent magnetic energy" (Energy equipartition)
   - fitting: _not stated_
   - validation: _not stated_
5. **Mean-field dynamo ordering timescale**: Ordering timescale and dynamo number following Arshakian et al.  
  > "The ordering timescale can be estimated as(cite: Arshakian2009)" (Ordering timescale)
   - parameter: h=300 pc, l_c=0.5-2 kpc, l=1-10 pc  
  > "We assume a large-scale coherence length in the range $l_{\rm{c}} = 0.5-2.0$ kpc" (Ordering timescale)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.2.1: calibration, tclean imaging, simobserve  
  > "Common Analysis Software Applications (CASA) version 6.2.1" (Observations and data reduction)
- **lenstronomy** : computing SIE+shear lens model  
  > "using LENSTRONOMY(cite: Birrer2018)" (Lens modelling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Integrated flux density | 62 | not stated | mJy | 1 | We measure an image plane integrated flux density of $I=62$ mJy |
| Integrated polarization fraction | 0.6 | 0.1 | % | 2 | integrated polarization fraction of $P=0.6\pm 0.1$% |
| Mean polarization fraction | 0.6 | 0.3 | % | 2 | $\langle P \rangle = 0.6\pm0.3$% |
| Source-plane B-field orientation | 5 | +5/-10 | deg east of north | 3 | orientated $\chi_{\rm B} =5^{+5}_{-10}$ degrees east of north |
| Equipartition B-field upper limit | 514 | not stated | uG | 4 | $B_{\rm{eq}} \le514~\mu$G |
| Dynamo number | 3.2 | 0.4 | dimensionless | 5 | We estimate a dynamo number $D_{\rm{d}} = 3.2\pm0.4$ |
| Ordering timescale | 0.4-18 | not stated | Gyr | 5 | the ordering timescale is estimated to be in the range of $\tilde{t} \approx 0.4$–$18$ Gyr |

## Qualitative findings

- Polarization level similar to local star-forming disks and starbursts  
  > "We therefore conclude that 9io9 has a polarization level similar to local star-forming disks and starburst galaxies" (main text)

## Claim tuples

- H: A kpc-scale ordered B-field exists in 9io9 at z=2.6 | E: Polarized 242 GHz continuum plus lensed source-plane simulations | R: chi_B = 5 (+5/-10) deg, parallel to the CO disk; P ~0.6% | F: A 5 kpc-scale ordered field aligned with the disk is present | **supported**
- H: The mean-field dynamo has had time to order the field | E: Ordering timescale and dynamo number estimate | R: D_d=3.2 below critical ~7; timescale 0.4-18 Gyr | F: Mean-field dynamo has not yet had time to amplify; starburst turbulence dominant | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Lack sensitivity and resolution to map B-field at ~100 pc scales; field strength cannot be reliably estimated from dust polarization  
  > "We currently lack the sensitivity and resolution to map the configuration of the *B*-field strength at scales $\sim$100 pc" (main text)
- Caveat (inferred, ours): Source-plane model assumes uniform B and CO-like Gaussian morphology
- Caveat (inferred, ours): Equipartition strength is only an upper limit with unresolved disk height
- Caveat (inferred, ours): Low S/N polarization detection

## Reproducibility

- Data public (paper): Data to be available via ALMA archive under 2021.1.01461.S  
  > "The ALMA data used in this work will be available via the ALMA Science Archive (https://almascience.nrao.edu/aq) with reference to the project code 2021.1.01461.S." (Methods)
- Products in archive: _not stated_
- Missing: Image/cell size
- Missing: Polarization calibration script
- Missing: Pixel selection details
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 3/5, Data public and main steps described, but several imaging settings and the polarization script are missing.
- Rediscovery candidate: yes, Public data, numeric results (P, chi_B) are reproducible via CASA polarization imaging.

## Links

- Method: Birrer2018 (lenstronomy lens modelling)
- Companion: Geach2018 (lens model and CO kinematics)
- Companion: Geach2015 (discovery of 9io9)

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
