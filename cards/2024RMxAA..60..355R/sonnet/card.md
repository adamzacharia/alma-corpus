# The Radio Continuum Source Projected Near HR 8799

`2024RMxAA..60..355R` | Revista Mexicana de Astronomia y Astrofisica 2024 | first author: Rodríguez, L. F. | arXiv: 2407.05479 | DOI: 10.22201/ia.01851101p.2024.60.02.12

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: debris_disks, exoplanets
- Question: Is the radio continuum source seen near HR 8799 (VLA 3 GHz and ALMA 340 GHz) physically associated with the star/exoplanets, or is it a background galaxy?  
  > "In this paper we present sensitive VLA observations of the HR 8799 region obtained with the purpose of searching for emission from the star or from one of its four exoplanets." (Introduction)
- Target **HR 8799**: coordinates _not stated_; z/distance 40.85 pc  
  > "Four exoplanets were found within $\sim$80 au ($\sim 2''$ at the distance of 40.85 pc) in the plane of the sky from the star" (Introduction); distance from Gaia DR3 parallax  
  > "Four exoplanets were found within $\sim$80 au ($\sim 2''$ at the distance of 40.85 pc) in the plane of the sky from the star" (Introduction)

## Data provenance

- ALMA projects: 2016.1.00907.S
- bands: 340 GHz continuum (0.8 mm)  
  > "The sub-millimeter continuum data (at 340 GHz) were obtained from the ALMA data archive." (2.2 ALMA)
- frequencies and spectral setup: Four 2 GHz SPWs; three continuum, one for CO(3-2)  
  > "Three of these SPWs were used for the continuum, and one for the detection of the CO(3$-$2) molecular line" (2.2 ALMA)
- continuum bandwidth: _not stated_
- arrays: 12 m array only  
  > "we only used the 12 m array observations carried out from 2018 May 13 to June 1." (2.2 ALMA)
- configurations: _not stated_
- baselines: 15 to 314 m (18 to 392 kλ)  
  > "The data were taken using baselines ranging from 15 to 314 m (18 to 392 k$\lambda$)." (2.2 ALMA)
- angular resolution: 0.88" x 0.76"; PA 14 deg  
  > "at an angular resolution of $0\rlap.{''}88 \times 0\rlap.{''}76$; 14$^{\circ}$" (2.2 ALMA)
- max recoverable scale: _not stated_
- sensitivity: 10 μJy/beam rms at 0.8 mm  
  > "We obtained an image rms noise for the continuum at 0.8 mm of 10 $\mu$Jy beam$^{-1}$" (2.2 ALMA)
- time on source: 4.5 hrs  
  > "The total time on-source was 4.5 hrs." (2.2 ALMA)
- observing dates: 2018 May 13 to June 1  
  > "we only used the 12 m array observations carried out from 2018 May 13 to June 1." (2.2 ALMA)
- pi or archival as stated: Archival; PI V. Faramaz  
  > "The project was made under the program 2016.1.00907.S (PI: V. Faramaz)." (2.2 ALMA)
- Line: CO J=3-2 (345.79598990 GHz)
- Other facility **VLA**: Archival 3 GHz (S-band) A-configuration data, project 12B-188, six epochs in 2012  
  > "These observations were made in the highest angular resolution A configuration during six epochs between 2012 October 31 and 2012 November 26." (2.1 VLA)
- Other facility **Gaia DR3**: Proper motion and parallax of HR 8799  
  > "HR 8799 has large proper motions, of order $0\rlap.{''}1$ per year" (3.3 Comparison between the VLA and the ALMA data)
- External data: 3 GHz source counts and spectral index distribution  
  > "we have used the 3.0 GHz source catalog of Smolčić et al. (2017) to produce a plot of the expected number of background sources" (3.1 VLA data) [from Smolčić et al. 2017]
- External data: 850 μm background source counts  
  > "From the results of Zavala et al. (2017) we estimate that the number of background sources with a flux density of 0.49 mJy or higher at 850 $\mu$m is about 4.9 per square arcmin." (3.2 ALMA data) [from Zavala et al. 2017]
- External data: Exoplanet orbital motions  
  > "an interpolation of the orbital motions of the exoplanets with respect to the star taken from Konopacky et al. (2016)" (3.1 VLA data) [from Konopacky et al. 2016]
- External data: ALMA+ACA fluxes at 340 and 230 GHz and disk inner radius  
  > "the data points of Faramaz et al. (2021) have flux densities of 316$\pm$20 and 58$\pm$18 $\mu$Jy, at 340 and 230 GHz, respectively." (3.3 Comparison between the VLA and the ALMA data) [from Faramaz et al. 2021]

## Processing

### Calibration

- pipeline or manual: ALMA: raw data calibrated (method not detailed); VLA: pipeline provided for VLA  
  > "the pipeline provided for VLA[^2] observations" (2.1 VLA)
- casa version: VLA: CASA 5.6.2-3; ALMA: CASA 5.1.1  
  > "using the version 5.6.2-3 of the CASA" (2.1 VLA); "imaged using the Common Astronomy Software Applications (CASA) version 5.1.1" (2.2 ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: VLA: J0137+3309 (3C48)  
  > "The amplitude calibrator was J0137+3309 (3C48) and the gain calibrator was J2254+2445." (2.1 VLA)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: TCLEAN (ALMA); source fit with IMFIT  
  > "We used a robust parameter equal to 0.5 in the TCLEAN task" (2.2 ALMA)
- deconvolver: _not stated_
- weighting robust: ALMA robust = 0.5; VLA robust = 2  
  > "We used a robust parameter equal to 0.5 in the TCLEAN task" (2.2 ALMA); "The images were made using a robust weighting of 2 (Briggs 1995)" (2.1 VLA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CO(3-2) line channels excluded from continuum  
  > "The CO(3$-$2) line was the only spectral line excluded during the process of the continuum construction." (2.2 ALMA)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 10 μJy/beam  
  > "image rms noise for the continuum at 0.8 mm of 10 $\mu$Jy beam$^{-1}$" (2.2 ALMA)

### Not stated but needed to reproduce (our reading)

- ALMA calibration procedure (pipeline vs manual) and flux scale
- cell size, image size, masks, clean threshold and iterations
- Spectral window/channel selection details for the CO exclusion
- VLA image rms, cell and size, and clean parameters
- How the 0.49 mJy at 338 GHz flux was derived
- Method for per-epoch flux measurement

## Analysis recipe

1. **Image continuum and fit source**: Calibrate and concatenate VLA epochs; clean ALMA and VLA images; fit source in image plane with IMFIT  
  > "we fitted the data in the image plane with the task IMFIT of CASA" (2.2 ALMA)
   - software: CASA, tclean, imfit
   - parameter: ALMA robust 0.5; VLA robust 2  
  > "The images were made using a robust weighting of 2 (Briggs 1995)" (2.1 VLA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Chance-coincidence probability**: Use background source counts times the solid angle of a 2.2" radius circle  
  > "Since a circle with radius of $2\rlap.{''}2$ has a solid angle of 0.0042 square arcmin, the *a priori probability is 0.0046, or 1 in 215." (3.1 VLA data)
   - fitting: _not stated_
   - validation: _not stated_
3. **Spectral index and variability**: Split the 2-4 GHz band into two 1 GHz halves; compare positions and fluxes in VLA and ALMA and per-epoch  
  > "Dividing the data in two windows of 1 GHz wide each centered at 2.5 and 3.5 GHz, we obtain flux densities of 16.5$\pm$4.1 and 25.3$\pm$2.9 $\mu$Jy" (3.1 VLA data)
   - fitting: _not stated_
   - validation: _not stated_
4. **Proper motion test**: Compare VLA and ALMA positions 5.5 yr apart against expected stellar proper-motion displacement  
  > "In the time interval between the two data sets, we expect a total displacement of $\simeq 0\rlap.{''}6$, twenty times larger than our upper limit." (3.3 Comparison between the VLA and the ALMA data)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.6.2-3 (VLA); 5.1.1 (ALMA): Calibration, imaging, IMFIT source fitting  
  > "we fitted the data in the image plane with the task IMFIT of CASA" (2.2 ALMA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 340 GHz flux density | 207 | 10 | μJy | 1 | 207$\pm$10 $\mu$Jy |
| VLA 3 GHz flux density | 19.1 | 2.7 | μJy | 1 | 19.1$\pm$2.7 $\mu$Jy |
| A priori probability, 3 GHz | 0.0046 | not stated | dimensionless | 2 | the *a priori probability is 0.0046, or 1 in 215. |
| A priori probability, ALMA | 0.021 | not stated | dimensionless | 2 | is 0.021. |
| VLA in-band spectral index | 1.3 | 0.9 | dimensionless | 3 | spectral index of $\alpha$ = 1.3$\pm$0.9 |
| Spectral index 3 to 340 GHz | 0.69 | 0.03 | dimensionless | 3 | The spectral index between the 3.0 and 340.0 GHz flux densities is 0.69$\pm$0.03. |
| Position difference VLA vs ALMA | <= 0.03 | not stated | arcsec | 4 | The two positions coincide within $\leq 0\rlap.{''}03$. |

## Qualitative findings

- No circular polarization detected at upper limit of 19%; no variability across the six epochs  
  > "No circular polarization was detected at an absolute upper limit of 19%." (3.1 VLA data)

## Claim tuples

- H: The radio source near HR 8799 is associated with the star system | E: Compared VLA (2012.88) and ALMA (2018.38) positions against HR 8799 proper motion | R: Positions agree within 0.03" whereas 0.6" of stellar motion is expected | F: Source is a background millimeter galaxy, not associated | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Robust 0.5 chosen as compromise between resolution and sensitivity, and to match VLA resolution  
  > "an adequate compromise between angular resolution and sensitivity" (2.2 ALMA)
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA flux lower than Faramaz et al. because ACA data were not included  
  > "This difference is probably due to the fact that Faramaz et al. (2021) included in their analysis data from the Atacama Compact Array, recovering more extended flux." (2.2 ALMA)
- Caveat (inferred, ours): Positional coincidence accuracy depends on astrometric uncertainties of 0.03-0.05"
- Caveat (inferred, ours): Spectral index from two-point fits with different resolutions and uv coverage
- Caveat (inferred, ours): Gaia proper motions are used, but the offset test is only done at one epoch pair

## Reproducibility

- Data public (paper): Both datasets obtained from public archives (VLA 12B-188; ALMA 2016.1.00907.S)  
  > "The sub-millimeter continuum data (at 340 GHz) were obtained from the ALMA data archive." (2.2 ALMA)
- Products in archive: _not stated_
- Missing: Imaging geometry and cleaning parameters
- Missing: ALMA calibration details
- Data volume (inferred): tens of GB (ALMA 12 m 4.5 h plus six VLA epochs)
- Score (inferred): 6/5, Public data and basic recipe are given, but imaging parameters are incomplete; the analysis is simple.
- Rediscovery candidate: yes, Public data, simple continuum fitting, numeric results.

## Links

- Companion: Faramaz et al. 2021 (Original ALMA+ACA analysis of the HR 8799 disk and the point source)
- Related: VLA 12B-188

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
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
  "facts": 65,
  "stated": 35,
  "rate": 0.538
 },
 "evidence_ok": true
}
```
