# Isotopic Ratios of Carbon and Oxygen in Titan’s CO using ALMA

`2016ApJ...821L...8S` | The Astrophysical Journal Letters 2016 | first author: Serigano, Joseph | arXiv: 1602.07707 | DOI: 10.3847/2041-8205/821/1/L8

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: solar_system
- Question: What are the CO abundance and the 12C/13C, 16O/18O and 16O/17O isotopic ratios in Titan's atmosphere, derived from ALMA CO isotopologue lines?  
  > "Molecular abundances and the vertical atmospheric temperature profile were derived by modeling the observed emission line profiles using NEMESIS, a line-by-line radiative transfer code." (abstract)
- Target **Titan**: coordinates not stated (ephemeris tracking)  
  > "Titan’s diameter ranged from 0.67$^{\prime\prime}$ to 0.78$^{\prime\prime}$ on the sky throughout the observation dates." (Observations); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00772.S, 2011.0.00319.S, 2012.1.00261.S, 2011.0.00419.S, 2011.0.00724.S, 2011.0.00465.S, 2011.0.00277.S, 2012.1.00564.S, 2012.1.00496.S, 2011.0.00318.S, 2012.1.00453.S
- bands: Bands 3, 6, 7, 9  
  > "Data from ALMA Bands 3, 6, 7, and 9 were used for this study." (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Beams from 0.35''x0.28'' (CO 6-5) to 1.87''x1.30'' (CO 1-0)  
  > "CO (6–5) | 691.473 | 2012 Jun 05 | 230 | 21 | 1953 | $0.35''\times0.28''$ | 420 - 550 | 2011.0.00724.S" (Table 2)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2012 and 2014 (Cycle 0 and Cycle 1)  
  > "Data sets from 2012 were a part of ALMA Early Science Cycle 0 observations, when the full array was not yet completed." (Observations)
- pi or archival as stated: Archival data, often Titan flux calibration observations  
  > "ALMA often uses Titan to calibrate the absolute flux scale for the science target, resulting in numerous short observations of Titan spanning the lifetime of ALMA." (Observations)
- Line: CO J=1-0 (115.271 GHz)
- Line: CO J=2-1 (230.538 GHz)
- Line: CO J=3-2 (345.796 GHz)
- Line: CO J=6-5 (691.473 GHz)
- Line: 13CO J=2-1, 3-2, 6-5 (220.399, 330.588, 661.067 GHz)
- Line: C18O J=2-1, 3-2 (219.560, 329.331 GHz)
- Line: C17O J=3-2 (337.061 GHz)
- External data: Initial temperature profile from Cassini CIRS and Huygens HASI  
  > "We adopted an initial atmospheric temperature profile derived from a combination of Cassini CIRS and Huygens Atmospheric Structure Instrument (HASI) measurements" (Modeling and Results) [from (cite: flasar05; fulchignoni05)]
- External data: Abundances of nitrogen and methane isotopes and aerosols  
  > "Abundances of nitrogen and methane isotopes and aerosols were adopted from Teanby et al. (2013)" (Modeling and Results) [from (cite: teanby13)]
- External data: Line parameters from HITRAN 2012  
  > "line parameters were extracted from the HITRAN 2012 database" (Modeling and Results) [from (cite: rothman13)]
- External data: Gas vertical profiles for N2, CH4, H2  
  > "Gas vertical profiles for these molecules were based on (cite: niemann10)." (Modeling and Results) [from (cite: niemann10)]
- External data: Terrestrial isotopic ratios 89.3, 498.8, 2680.6 used as a priori  
  > "we assumed terrestrial isotopic ratios of 89.3 for $^{12}$C/$^{13}$C, 498.8 for $^{16}$O/$^{18}$O, and 2680.6 for $^{16}$O/$^{17}$O" (Modeling and Results) [from (cite: lodders03)]
- Simulation/model as data: Butler-JPL-Horizons 2012 flux model for Titan used for the flux scale  
  > "The initial flux scale was established by matching the continuum level from a relatively line free region in the spectrum to that of the Butler-JPL-Horizons 2012 flux model for Titan" (Observations)

## Processing

### Calibration

- pipeline or manual: Revised JAO calibration scripts, with emission lines unflagged and updated Titan flux model  
  > "The data were flagged and calibrated using revised versions of the calibration scripts provided by the Joint ALMA Observatory." (Observations)
- casa version: CASA 4.3.1  
  > "using version 4.3.1 of the Common Astronomy Software Applications package (CASA)" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Butler-JPL-Horizons 2012 Titan model; bandpass with bright quasars (e.g., 3C279)  
  > "Bright quasars (e.g., 3C279) were used for bandpass calibration." (Observations)
- flux scale uncertainty: within 15%  
  > "which is expected to be accurate to within 15%." (Observations)
- self calibration: Phase self-calibration possible using Titan's continuum  
  > "Self-calibration of the phases was possible due to Titan’s strong and compact continuum emission." (Observations)

### Imaging

- task: _not stated_
- deconvolver: Högbom clean  
  > "Image deconvolution was performed using the Högbom clean algorithm with natural visibility weighting and a threshold flux level of twice the expected RMS noise." (Observations)
- weighting robust: natural weighting  
  > "Image deconvolution was performed using the Högbom clean algorithm with natural visibility weighting and a threshold flux level of twice the expected RMS noise." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: C18O and C17O data combined per transition with fixplanets and cvel  
  > "Measurements of C$^{18}$O and C$^{17}$O were combined for each transition using the CASA *fixplanets* and *cvel* tasks" (Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Data reduction method  
  > "Data reduction used a similar method to (cite: cordiner15) using version 4.3.1" (Observations) [from (cite: cordiner15)]
- NEMESIS modeling approach  
  > "In a similar manner to (cite: cordiner15), individual spectra were modeled using the NEMESIS line-by-line radiative transfer code" (Modeling and Results) [from (cite: cordiner15)]
- Flux to radiance conversion procedure  
  > "fluxes were converted to spectral radiance units (W/cm$^{2}$/sr/cm$^{-1}$) following the procedure outlined in (cite: teanby13)." (Modeling and Results) [from (cite: teanby13)]
- Combination of line results  
  > "results for all five emission lines were combined using the technique provided in (cite: nixon08a) Section 4." (Modeling and Results) [from (cite: nixon08a)]

### Not stated but needed to reproduce (our reading)

- Titan flux model details/updates beyond reference to ALMA Memo 594
- Exact spectrum extraction regions and channel selection
- Line-free channels and continuum subtraction method
- Which detections were combined and how many were used per line
- NEMESIS a priori covariance/error settings
- Aerosol profile specifics

## Analysis recipe

1. **Calibrate and image Titan data**: Revised JAO scripts, phase self-cal, Högbom clean with natural weighting in CASA, Titan rest-frame correction  
  > "spectral coordinates were corrected into Titan’s rest frame using JPL Horizons On-Line Ephemeris System" (Observations)
   - software: CASA
   - parameter: clean threshold 2x expected RMS  
  > "a threshold flux level of twice the expected RMS noise" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract disc-averaged spectra and convert to radiance**: Integrate over Titan disc plus atmosphere to 850 km plus 3 sigma_PSF; convert Jy to radiance  
  > "We obtained spectra by integrating over a region of the ALMA data cube that includes the flux from Titan’s solid disc and atmosphere out to 850 km plus 3$\sigma$$_{PSF}$" (Modeling and Results)
   - fitting: _not stated_
   - validation: Spectra rescaled to NEMESIS continuum, differing ~10% from Horizons flux model  
  > "which typically differed from the Butler-JPL-Horizons 2012 flux model by about 10%." (Modeling and Results)
3. **Retrieve CO abundance and temperature profile**: Simultaneous retrieval of constant CO VMR and temperature profile with a priori 50 ppm; limb-brightening via disc-averaged reference spectra  
  > "We began with an a priori mixing ratio of 50 ppm and simultaneously retrieved a constant vertical abundance and temperature profile." (Modeling and Results)
   - software: NEMESIS
   - parameter: 24 to 27 field-of-view averaging points out to 3425 km radius  
  > "The number of averaging points for this study ranged from 24 to 27" (Modeling and Results)
   - assumption: CO mixing ratio constant with altitude up to 850 km  
  > "we modeled the CO emission lines under the assumption that the mixing ratio remains constant with altitude up to 850 km" (Modeling and Results)
   - fitting: Iterative chi^2 minimization with a priori regularization; 2% line intensity systematic added  
  > "NEMESIS uses an iterative $\chi^2$ minimization technique that relies on both the quality of the fit to the data and the level of deviation from the a priori setup." (Modeling and Results)
   - validation: Correlation coefficients; fixed CO 40-60 ppm test with temperature-only retrieval  
  > "We also tested the uniqueness of fit by holding the CO gas abundance at constant values between 40 and 60 ppm" (Modeling and Results)
4. **Retrieve isotopologue abundances and isotopic ratios**: Fixed nearest-in-time CO-retrieved temperature profile; a priori terrestrial ratios; fit each line and combine  
  > "the retrieved temperature profile which was closest in time to that observation was used as the fixed temperature profile" (Modeling and Results)
   - software: NEMESIS
   - assumption: A priori terrestrial isotopic ratios  
  > "we assumed terrestrial isotopic ratios of 89.3 for $^{12}$C/$^{13}$C, 498.8 for $^{16}$O/$^{18}$O, and 2680.6 for $^{16}$O/$^{17}$O" (Modeling and Results)
   - fitting: Same procedure as CO  
  > "Best-fitting models of CO isotopologues were found using the same modeling procedures as CO (aside from the fixed temperature profile)" (Modeling and Results)
   - validation: C18O 3-2 and 2-1 abundances consistent within errors  
  > "The mixing ratios for C$^{18}$O, derived independently from the J = 3–2 and J = 2–1 transitions, are consistent within the observational errors." (Modeling and Results)

## Software

- **CASA** 4.3.1: Calibration, imaging, fixplanets/cvel combination  
  > "using version 4.3.1 of the Common Astronomy Software Applications package (CASA)" (Observations)
- **NEMESIS** : Line-by-line radiative transfer retrieval  
  > "individual spectra were modeled using the NEMESIS line-by-line radiative transfer code" (Modeling and Results)
- **Splatalogue** : Assigning rest frequencies  
  > "The Splatalogue database for astronomical spectroscopy was used to assign rest frequencies to the observed emission lines" (Observations)
- **JPL Horizons** : Titan rest-frame correction  
  > "spectral coordinates were corrected into Titan’s rest frame using JPL Horizons On-Line Ephemeris System" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO abundance | 49.6 | 1.8 | ppm | 3 | The abundance of CO was determined to be 49.6 ${\pm}$ 1.8 ppm |
| 12C/13C | 89.9 | 3.4 | dimensionless | 4 | $^{12}$C/$^{13}$C = 89.9 ${\pm}$ 3.4 |
| 16O/18O | 486 | 22 | dimensionless | 4 | $^{16}$O/$^{18}$O = 486 ${\pm}$ 22 |
| 16O/17O | 2917 | 359 | dimensionless | 4 | $^{16}$O/$^{17}$O = 2917 ${\pm}$ 359 |
| Temperature profile error | 8 K above 500 km; 4 K at 200 km | not stated | K | 3 | Errors for the globally averaged retrieved temperature profile are of the order of 8 K at the top of the atmosphere (above 500 km) and 4 K at 200 km. |

## Qualitative findings

- First spectroscopic detection of 17O in the outer solar system via C17O at >8 sigma  
  > "We present the first spectroscopic detection of $^{17}$O in the outer solar system with C$^{17}$O detected at \>8$\sigma$ confidence." (abstract)

## Claim tuples

- H: Titan's CO isotopic ratios deviate from terrestrial values | E: NEMESIS retrieval of ALMA CO isotopologue lines | R: 12C/13C=89.9±3.4, 16O/18O=486±22, 16O/17O=2917±359 | F: No significant deviation from terrestrial ratios | **supported**
- H: CO is uniformly mixed in Titan's atmosphere | E: Fit lines probing 140-550 km with a constant VMR | R: Consistent abundances across transitions; CO 49.6±1.8 ppm | F: Constant-with-altitude assumption appears validated | **supported**

## Reasoning

- Why this data: Archival Titan flux-calibration observations give many CO lines; dates chosen close in time to limit seasonal effects  
  > "We selected observation dates within a short period of time to minimize possible effects of seasonal variations in Titan’s thermal structure." (Observations)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Unquantified systematic errors (disc-averaged temperature, Voigt profile, line-broadening coefficients)  
  > "Additional systematic errors that have not been quantified in the final error estimate could exist." (Modeling and Results)
- Caveat (inferred, ours): Which detections go into each combined ratio is unclear
- Caveat (inferred, ours): Flux scale uncertainty of 15% and 10% rescaling not propagated clearly
- Caveat (inferred, ours): Constant CO profile assumed

## Reproducibility

- Data public (paper): Data obtained from the ALMA Science Archive  
  > "Interferometric observations of Titan (obtained from the ALMA Science Archive" (Observations)
- Products in archive: _not stated_
- Missing: Revised calibration scripts and Titan flux model details
- Missing: Extraction apertures and a priori error settings for NEMESIS
- Missing: Per-line retrieved values before combination
- Data volume (inferred): ~100-300 GB raw across 11 projects
- Score (inferred): 5/5, Public data and named tools, but retrieval setup and calibration revisions are only partly specified.
- Rediscovery candidate: no, Requires NEMESIS retrieval with unspecified settings and custom calibration revisions.

## Links

- Method: (cite: cordiner15) (Data reduction and modeling approach followed)
- Method: (cite: teanby13) (Radiance conversion and disc-averaging procedure)
- Method: (cite: irw08) (NEMESIS code)
- Companion: (cite: cordiner14a) (Previous ALMA Titan study of HNC and HC3N)

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 11,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 45,
  "rate": 0.6
 },
 "evidence_ok": true
}
```
