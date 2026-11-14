# GATOS: missing molecular gas in the outflow of NGC 5728 revealed by JWST

`2024A&A...689A.263D` | Astronomy and Astrophysics 2024 | first author: Davies, R. | arXiv: 2406.17072 | DOI: 10.1051/0004-6361/202449875

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Is molecular gas present in the ionisation cone/outflow of NGC 5728, where CO(2-1) is not detected, and how is it excited and kinematically behaving, as seen with JWST MIRI MRS pure rotational H2 lines?  
  > "It is therefore expedient to look at the pure rotational H$_2$ lines present at mid-infrared wavelengths" (1 Introduction); "It is remarkable, however, that CO emission is not detected in the ionisation cone." (1 Introduction)
- Target **NGC 5728**: coordinates _not stated_; z/distance 39 Mpc  
  > "which is a strongly barred disk galaxy at a distance of 39 Mpc" (1 Introduction); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.3 mm continuum position measured with a 0.5'' beam using ALMA  
  > "the 1.3 mm continuum position measured with a 0.5$''$ beam using ALMA (cite: shi19)" (4.1 Data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230.5 GHz)
- Other facility **JWST MIRI MRS**: 5-28 micron integral field spectroscopy with rotational H2 lines, program 1670  
  > "Observations of NGC 5728 were performed on 13–14 March 2023 using the Medium Resolution Spectrometer (MRS; (cite: wel15; arg23))" (4 Observations, data processing, map extraction)
- Other facility **VLT/SINFONI**: near-infrared ro-vibrational H2 and Brgamma fluxes in the nucleus  
  > "These were measured from the reduced cubes analysed by (cite: shi19), who only included the 1-0 S(1) line in their work." (5.3 Non-LTE model of the nuclear region)
- External data: ALMA CO(2-1) data, maps and disk model fitted to CO kinematics  
  > "the residual velocity after subtracting the velocity field of the disk model fitted to the CO (2-1) kinematics in (cite: shi19)" (4.3 Flux and kinematics maps) [from Shimizu et al. 2019 (cite: shi19)]
- Simulation/model as data: Shock model library of Kristensen et al. 2023  
  > "we use the library of models calculated by (cite: kri23), which are based on models of (cite: flo85) and (cite: god19)" (5.4 Shock models of the nuclear region)

## Processing

### Calibration

- pipeline or manual: JWST Calibration pipeline (JWST data, not ALMA) with extra bad pixel steps  
  > "We followed the standard MRS pipeline procedure adding some extra steps to correct for bad pixels." (4.1 Data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
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

- JWST data reduction described in detail elsewhere  
  > "The data reduction is described in detail in (cite: gber22), (cite: gber24), and (cite: mps22)." (4.1 Data reduction) [from (cite: gber22), (cite: gber24), (cite: mps22)]
- Non-LTE model with RADEX adopted from earlier work  
  > "The model we adopt here is described in (cite: per14) which makes use of RADEX (cite: van07)." (5.3 Non-LTE model of the nuclear region) [from Pereira-Santaella et al. 2014 (cite: per14)]

### Not stated but needed to reproduce (our reading)

- ALMA project code, calibration and imaging of the CO(2-1) cube (only via Shimizu et al. 2019)
- CO(2-1) flux, beam and noise values for the hotspot and nucleus apertures used for column density
- Fit method, priors and uncertainties for power-law and non-LTE fits
- How the shock model chi2 was computed
- Aperture definitions in machine-readable form

## Analysis recipe

1. **Reduce MRS cubes and fix astrometry**: JWST pipeline, median background subtraction, astrometry corrected with background galaxies  
  > "we corrected the astrometry of the 12 individual MIRI MRS datacubes using background galaxies detected in the parallel imaging." (4.1 Data reduction)
   - software: JWST Calibration pipeline
   - parameter: pipeline 1.11.4, context 1130  
  > "JWST Calibration pipeline (version 1.11.4) with the calibration context 1130" (4.1 Data reduction)
   - fitting: _not stated_
   - validation: relative centering precision about 0.02'' rms  
  > "we found that the relative centering precision was about 0.02$''$ rms" (4.1 Data reduction)
2. **Extract line flux and kinematics maps**: Single Gaussian plus linear continuum per line; quadrature correction for instrumental resolution  
  > "Flux and kinematics maps for each line were extracted using a single Gaussian fit to the line profile and a linear continuum to match the local continuum." (4.3 Flux and kinematics maps)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit H2 excitation with power-law temperature LTE models**: Aperture fluxes in five regions; power-law dN=T^-beta dT  
  > "a more physical approach is to adopt a power-law temperature distribution d$N = T^{-\beta}$d$T$" (5.1 Thermal equilibrium models)
   - parameter: pixel grid 0.13'', apertures minimum width 0.8''  
  > "we extracted line fluxes in apertures with a minimum width of 0.8$''$ and mostly $>$1$''$" (5 Molecular gas excitation and temperature distribution)
   - assumption: LTE; no PSF correction  
  > "We note that it would be incorrect to apply a PSF correction because of the extended nature of the spatial distributions of the lines." (5 Molecular gas excitation and temperature distribution)
   - fitting: _not stated_
   - validation: PSF effects tested to be at most 20% on fluxes  
  > "Tests indicate that in this case PSF effects have no more than a 20% impact on extracted fluxes from S(1) to S(8)." (5 Molecular gas excitation and temperature distribution)
4. **Non-LTE and shock model fits for nucleus**: RADEX-based grid with power-law T; extinction from Brgamma/Pfalpha; compare shock library by chi2  
  > "The grids considered cover kinetic temperatures $T_{kin} = 10$–2800 K, H$_2$ density n$_{H_2} = 10^2$–10$^9$ cm$^{-3}$" (5.3 Non-LTE model of the nuclear region)
   - software: RADEX
   - assumption: Fritz et al. 2011 extinction curve  
  > "so for the discussion here we simply adopt that of (cite: fri11)" (5.3 Non-LTE model of the nuclear region)
   - fitting: _not stated_
   - validation: three extinction curves give consistent fits  
  > "Trying these different curves yields consistent fits to the extinction corrected data" (5.3 Non-LTE model of the nuclear region)
5. **Compare H2 column with CO(2-1)-derived column**: Convert CO(2-1) to column with alpha_CO and compare to H2 columns  
  > "integrating over the hotspot aperture provides a marginal detection that would yield a column density similar to that above if one adopts $\alpha_{CO}\sim0.3$" (5.5 Gas Column Density)
   - assumption: alpha_CO=1.1 in Shimizu et al.; ~0.3 in hotspot  
  > "Those authors adopted a CO-to-H$_2$ ratio of $\alpha_{CO}=1.1$ typical for the central regions of nearby galaxies." (5.5 Gas Column Density)
   - fitting: _not stated_
   - validation: _not stated_
6. **Model molecular outflow kinematics**: Add planar radial velocity profile to CO disk model and compare PV diagrams  
  > "This can be matched very well if one adds a planar radial component $v_{rad}$ to the disk model" (6.1 Planar molecular flow)
   - parameter: v_max=400 km/s at r0=50 pc, r_out=750 pc  
  > "the radial velocity $v_{rad}$ reaches its maximum $v_{max} = 400$ km s$^{-1}$ at $r_0=50$ pc" (6.1 Planar molecular flow)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **JWST Calibration pipeline** 1.11.4: MIRI MRS reduction  
  > "JWST Calibration pipeline (version 1.11.4)" (4.1 Data reduction)
- **RADEX** : non-LTE H2 excitation grid  
  > "which makes use of RADEX (cite: van07)" (5.3 Non-LTE model of the nuclear region)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Power-law index beta, nucleus and hotspot | 4.4-4.5 | not stated | dimensionless | 3 | while the nucleus and hotspot have significantly shallower indices of $\beta =$4.4–4.5 |
| Power-law index beta, other apertures | 5.5-6.0 | not stated | dimensionless | 3 | have power-law indices in the range $\beta =$5.5–6.0 |
| Non-LTE beta, nucleus | 3.6 | not stated | dimensionless | 4 | In this case we find $\beta = 3.6$ |
| A_Brgamma | 0.78 | not stated | mag | 4 | we find $A_{Br\gamma} = 0.78$ mag |
| Peak radial velocity of molecular outflow | 400 | not stated | km/s | 6 | $v_{max} = 400$ km s$^{-1}$ at $r_0=50$ pc |
| log N_H from CO(2-1) in nucleus with alpha_CO=0.3 | 22.3 | not stated | log cm^-2 | 5 | using the same value of $\alpha_{CO}$ yields $\log N_H = 22.3$ |

## Qualitative findings

- H2 rotational lines are detected in the ionisation cone where CO(2-1) is not.  
  > "while CO is not detected in the ionisation cones, the rotational H$_2$ lines are detected." (4.3 Flux and kinematics maps)

## Claim tuples

- H: Molecular gas survives in the ionisation cone but is missed by CO(2-1) | E: MRS H2 line mapping compared to ALMA CO(2-1) | R: H2 detected in the cone; hotspot CO column consistent with H2 only for alpha_CO~0.3 | F: Gas in outflow is shock heated so CO is a poor tracer | **supported**
- H: The molecular outflow is planar and terminates | E: PV diagrams with disk plus radial velocity model | R: v_max 400 km/s at 50 pc falling to zero at 750 pc | F: Molecular outflow decelerates within 1 kpc in the disk plane | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Only qualitative arguments for the jet versus disk interaction  
  > "while we can only use qualitative arguments" (5.2 Excitation distribution: jet or disk interaction?)
- Caveat (inferred, ours): alpha_CO of 0.3 is tuned to match H2 columns, making the argument somewhat circular
- Caveat (inferred, ours): Toy deceleration model is non-unique

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA CO(2-1) cube details
- Missing: Fitting code and aperture masks
- Data volume (inferred): JWST cubes plus one ALMA cube, tens of GB
- Score (inferred): 2/5, ALMA role minor; JWST analysis lacks fit details and ALMA processing is in a previous paper.
- Rediscovery candidate: no, ALMA data are secondary and the recipe is incomplete.

## Links

- Method: Shimizu et al. 2019 (cite: shi19) (ALMA CO(2-1) data and disk model)
- Method: Pereira-Santaella et al. 2014 (cite: per14) (non-LTE power-law H2 model)
- Companion: García-Bernete et al. 2024 (cite: gber24) (first JWST GATOS analysis)
- Related: GATOS
- Related: LLAMA
- Related: JWST program 1670

## Checks

```json
{
 "quotes": 40,
 "quotes_ok": 40,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.00086.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 29,
  "rate": 0.377
 },
 "evidence_ok": true
}
```
