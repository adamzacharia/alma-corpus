# Circumstellar Disks around Binary Stars in Taurus

`2014ApJ...784...62A` | The Astrophysical Journal 2014 | first author: Akeson, R. L. | arXiv: 1402.5363 | DOI: 10.1088/0004-637X/784/1/62

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What are the circumstellar disk masses of wide young binary components in Taurus, and how do primary and secondary disks compare with each other and with single stars?  
  > "The observations were designed to measure the masses of circumstellar disks in these systems as an aid to understanding the role of multiplicity in star and planet formation." (abstract)
- Target **17 wide Taurus binaries (e.g. FV Tau, UY Aur, HK Tau, DK Tau, IRAS 04113+2758)**: coordinates per-source positions in Table 3 (e.g. FV Tau A 4:26:53.550 +26:06:53.903 J2000)  
  > "We selected targets from a single star formation region, Taurus (distance $\sim$ 140 pc)" (2 Sample); "| FV Tau | 4:26:53.550 $\pm$ 0.019 | 26:06:53.903 $\pm$ 0.025 |" (Table 3); z/distance ~140 pc (Taurus)  
  > "We selected targets from a single star formation region, Taurus (distance $\sim$ 140 pc)" (2 Sample); "| FV Tau | 4:26:53.550 $\pm$ 0.019 | 26:06:53.903 $\pm$ 0.025 |" (Table 3); distance from adopted Taurus distance; d = 140 pc used to compare with Andrews et al. 2013  
  > "We selected targets from a single star formation region, Taurus (distance $\sim$ 140 pc)" (2 Sample); "| FV Tau | 4:26:53.550 $\pm$ 0.019 | 26:06:53.903 $\pm$ 0.025 |" (Table 3)

## Data provenance

- ALMA projects: 2011.0.00150.S
- bands: Band 6 (1.3 mm) and Band 7 (850 um), ALMA Cycle 0  
  > "we have obtained ALMA Cycle 0 observations of 17 young binary systems in Taurus for which the components can be resolved." (1 Introduction); "At 1.3 mm (Band 6), one of the correlator basebands was set to cover the CO(2-1) transition at 230.5 GHz" (3 Observations)
- frequencies and spectral setup: 4 basebands, each 1.875 GHz total bandwidth, 488 kHz channels; one baseband on CO(2-1) in Band 6 and CO(3-2) in Band 7  
  > "The correlator was configured with each of the four basebands covering a total bandwidth of 1.875 GHz with a channel spacing of 488 kHz." (3 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Beams ~1.1x0.74 arcsec at 1.3 mm; ~0.7-0.9x0.5 arcsec at 850 um  
  > "| FV Tau A | 7.0       | 0.15     | 1.12x0.74 |" (Table 2)
- max recoverable scale: 3.0 arcsec at 850 um and 4.4 arcsec at 1.3 mm  
  > "the maximum scale for extended emission to be detected was 3.0$''$ at 850 $\mu$m and 4.4$''$ at 1.3 mm." (4.3 Binary comparisons)
- sensitivity: rms 0.15-0.20 mJy/beam at 1.3 mm; 0.35-0.40 mJy/beam at 850 um  
  > "The typical rms values achieved are 0.15-0.20 mJy/beam at 1.3 mm and 0.35-0.40 mJy/beam at 850 $\mu$m" (3 Observations)
- time on source: 60 s at 1.3 mm and 90 s at 850 um per source  
  > "Given the short time on source (60 sec at 1.3 mm and 90 sec at 850 $\mu$m)" (3 Observations)
- observing dates: Table 1 lists data sets 2012-12-05 to 2013-01-26 (Dec 2012 - Jan 2013; April 2012 for one set)  
  > "2011.0.00150.S_2012-12-05" (Table 1)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230.5 GHz)
- Line: CO J=3-2 (345.8 GHz)
- External data: Stellar luminosities and masses (Siess et al. 2000 grid) for sources  
  > "We adopt the stellar luminosities and masses from (cite: and13) for our sources" (4.2 Stellar properties and disk mass) [from (cite: and13)]
- External data: Single-dish 850 um fluxes for sample (Table 1)  
  > "Millimeter fluxes are single-dish fluxes at 850 $\mu$m taken from (cite: and05)" (Table 1) [from (cite: and05)]
- External data: Comparison sample of single Taurus stars, with known multiples removed  
  > "we used the sample in (cite: and13), and removed all known multiple sources using the list in (cite: kra11)" (4.2 Stellar properties and disk mass) [from (cite: and13); (cite: kra11)]

## Processing

### Calibration

- pipeline or manual: CASA with scripts provided by the NRAO ALMA center, standard scripts  
  > "Data for each band were calibrated separately using the CASA package and scripts provided by the NRAO ALMA center." (3 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto, Butler-JPL-Horizons 2012 models; zero-spacing flux 8.54 Jy (1.3 mm), 19.45 Jy (850 um)  
  > "The absolute flux calibration used Callisto and the Butler-JPL-Horizons 2012 flux models" (3 Observations)
- flux scale uncertainty: 5% (ALMA memo 594)  
  > "a 5% absolute flux calibration uncertainty (ALMA memo 594)" (4.2 Stellar properties and disk mass)
- self calibration: Phase-only self-calibration using bright reference sources per data set; continuum time-averaged to a single point  
  > "Each data set had at least one target with sufficient continuum flux to allow phase-only self-calibration, which was applied after the other calibrations." (3 Observations)

### Imaging

- task: CASA clean  
  > "Continuum and CO images at each band were generated using the *clean* task within CASA" (3 Observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "with a robust beam weighting of 0.5" (3 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Interactive clean, 50 iterations per cycle, boxes only on emission in dirty map; stop when residuals in boxes at or below image rms  
  > "images were generated interactively with 50 iterations per cycle and clean boxes placed only around emission visible in the dirty map." (3 Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Applied; entire primary beam mapped  
  > "The primary beam correction was applied and the entire primary beam was mapped for each source" (3 Observations)
- array combination: FV Tau and HBC 387 pointings combined in a mosaic  
  > "we combined the two observations in a mosaic, increasing the sensitivity." (3 Observations)
- smoothing: _not stated_
- final beam: Default restoring beam (Gaussian fit to dirty beam), listed in Table 2  
  > "The images use the default restoring beam, which is a Gaussian fit to the dirty beam." (3 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Disk mass constants: d=140 pc, dust-to-gas 0.01, kappa=2.3 cm2/g at 1.3 mm, Td=25 (L/Lsun)^-1/4 K  
  > "we also adopt the (cite: and13) scaling of $T_d = 25 (L_{\ast}/L_{\odot})^{-1/4}$ K." (4.2 Stellar properties and disk mass) [from (cite: and13)]
- Survival analysis methods via ASURV  
  > "we used the survival analysis methods described in (cite: fei85) and (cite: iso86) as implemented in the ASURV package (cite: lav92)" (4.2 Stellar properties and disk mass) [from (cite: fei85); (cite: iso86); (cite: lav92)]

### Not stated but needed to reproduce (our reading)

- Which CASA version was used
- Exact self-calibration solution intervals and which reference-source models
- Image size, cell size and clean threshold
- Continuum channel selection / line-free channels
- Imfit regions and initial guesses
- Primary/secondary stellar properties for IRAS 04298+2246 B and V710 Tau B details
- Flagging details of the standard scripts

## Analysis recipe

1. **Calibrate and self-calibrate**: Standard CASA calibration scripts, then phase-only self-calibration on bright reference sources  
  > "The system temperature, water vapor phase corrections, and flagging were applied using the standard scripts." (3 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Image continuum and CO**: Interactive clean with robust 0.5, primary-beam corrected  
  > "Continuum and CO images at each band were generated using the *clean* task within CASA, with a robust beam weighting of 0.5." (3 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Checked for no continuum emission away from known source positions  
  > "no continuum emission was detected away from the known source positions." (3 Observations)
3. **Measure flux, size, position**: 2D Gaussian fits in the image plane; point source if major-axis uncertainty exceeds fit size; upper limits 3 sigma  
  > "The clean continuum maps at each band were fit with two-dimensional Gaussians for each source using the CASA routine *imfit*." (4 Results)
   - software: CASA imfit
   - fitting: Gaussian least squares in image plane  
  > "we fit these data in the image plane to determine the total flux and size. The clean continuum maps at each band were fit with two-dimensional Gaussians for each source using the CASA routine *imfit*." (Results)
   - validation: _not stated_
4. **Derive disk masses**: Optically thin isothermal dust: Md = F d^2 /(kappa Xg B(Td)) with 1.3 mm fluxes  
  > "Assuming the dust is optically thin and isothermal, the conversion from flux ($F_{\nu}$) to disk mass ($M_d$) is" (4.2 Stellar properties and disk mass)
   - assumption: d=140 pc, Xg=0.01, kappa=2.3 cm2/g at 1.3 mm, Td=25 L^-1/4 K  
  > "we use the same constants of $d =$ 140 pc, dust-to-gas ratio $X_g$ = 0.01, dust opacity $\kappa_{\nu}$ = 2.3 cm$^2$g$^{-1}$ at 1.3 mm" (4.2 Stellar properties and disk mass)
   - fitting: _not stated_
   - validation: _not stated_
5. **Statistical comparison with singles and between primaries/secondaries**: Survival analysis with upper limits: Gehan, Peto-Peto, Peto-Prentice, EM and Buckley-James regression, Cox and Kendall tau  
  > "we used the univariate two-sample test methods Gehan, Peto and Peto, and Peto and Prentice from ASURV (cite: lav92)." (4.2 Stellar properties and disk mass)
   - software: ASURV
   - fitting: _not stated_
   - validation: Multiple versions of tests run as recommended  
  > "As recommended in (cite: fei85), we ran multiple versions of the relevant tests to compare the measurements." (4.2 Stellar properties and disk mass)
6. **Compute spectral index**: alpha from F850/F1.3mm = (lambda ratio)^alpha  
  > "we calculated the spectral index $\alpha$ between 1.3 mm and 850 $\mu$m" (4.2 Stellar properties and disk mass)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration, clean imaging, imfit  
  > "Data for each band were calibrated separately using the CASA package" (3 Observations)
- **ASURV** Rev 1.2: Survival analysis with upper limits  
  > "This paper makes use of the ASURV package, Rev 1.2 (cite: lav92)." (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Typical rms at 1.3 mm | 0.15-0.20 | not stated | mJy/beam | 2 | The typical rms values achieved are 0.15-0.20 mJy/beam at 1.3 mm |
| Average spectral index 850um-1.3mm | 2.1 | not stated | dimensionless | 6 | The spectral index values calculated for both the primaries and secondaries have an average of 2.1 |
| Probability primaries and secondaries from same flux population | 3-4% | not stated | percent | 5 | which has a probability of only 3-4% |
| Probability stellar-mass-ratio and disk-mass-ratio correlated | 8-65% | not stated | percent | 5 | is 8-65% (for the Cox proportional hazard and Kendall’s tau tests) |
| IRAS 04113+2758 A 1.3 mm total flux | 216.74 | 0.76 | mJy | 3 | / IRAS 04113+2758 A  / 179.0     / 0.54     / 1.15x0.73 / 216.74$\pm$0.76 / |
| HK Tau B disk mass | 7.5e-3 | 1.7e-3 | Msun | 4 | / HK Tau B / $0.027 \pm  0.015$ / $0.37 ^{+ 0.096} _{-  0.07}$ / $7.5\times10^{-3} \pm 1.7\times 10^{-3}$ / |

## Qualitative findings

- No substantial circumbinary emission detected in any system  
  > "there is no evidence for substantial circumbinary emission in any of these systems." (4.3 Binary comparisons)

## Claim tuples

- H: Do binary disks follow the stellar-mass to mm-flux scaling of single Taurus stars? | E: Compare ALMA fluxes and masses with Andrews et al. 2013 singles using survival analysis | R: Primaries consistent with singles (20-60%); secondaries lower (8-17%) | F: Binary sample matches the scaling within the scatter | **supported**
- H: Is the primary disk always more massive than the secondary disk? | E: Compare secondary/primary flux and mass ratios in 15 bona fide binaries | R: Secondary flux higher in two systems; three by disk mass | F: Not always; counter to some theory | **supported**
- H: Are secondary/primary disk mass ratios correlated with stellar mass ratios? | E: Survival-analysis correlation tests | R: Correlation probability 8-65% | F: Not correlated | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Image-plane fitting used since CASA does not allow multi-component uv fitting and goal was overall flux and mass  
  > "because CASA does not currently allow multiple component fitting in the uv-plane, we fit these data in the image plane to determine the total flux and size." (4 Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Primary/secondary comparison may be biased by lower stellar mass of secondaries; observations not designed to characterize disk physical parameters or extended emission  
  > "the comparison of the primaries and secondaries may be significantly biased by the lower stellar mass for the secondaries." (4.2 Stellar properties and disk mass)
- Caveat (inferred, ours): Single-temperature optically thin masses with fixed opacity are uncertain, especially for bright, possibly optically thick disks
- Caveat (inferred, ours): Small sample with short integrations
- Caveat (inferred, ours): Stellar masses inherited from model grids with large uncertainties

## Reproducibility

- Data public (paper): Data set named by project code in Acknowledgments and Table 1; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00150.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: image and cell sizes
- Missing: self-cal parameters
- Missing: exact imfit settings
- Data volume (inferred): ~50-100 GB raw (7 Cycle 0 execution blocks)
- Score (inferred): 3/5, Data are identified and recipe mostly described, but CASA version and several imaging parameters are missing.
- Rediscovery candidate: yes, Cycle 0 data are archival, recipe largely complete, and results are numeric tables of fluxes and masses.

## Links

- Method: (cite: and13) (Source of stellar properties and disk mass constants)
- Method: (cite: lav92) (ASURV survival analysis)
- Companion: (cite: har12) (Comparable binary millimeter survey)

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
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 42,
  "rate": 0.592
 },
 "evidence_ok": true
}
```
