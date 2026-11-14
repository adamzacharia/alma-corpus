# Dust Polarization toward Embedded Protostars in Ophiuchus with ALMA. III. Survey Overview

`2019ApJS..245....2S` | The Astrophysical Journal Supplement Series 2019 | first author: Sadavoy, Sarah I. | arXiv: 1909.02591 | DOI: 10.3847/1538-4365/ab4257

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: star_formation, protoplanetary_disks
- Question: What are the dust polarization morphologies and likely mechanisms (self-scattering vs magnetic fields) on disk scales for all embedded protostars in Ophiuchus?  
  > "The goal of this study is to study dust polarization morphologies down to disk scales." (abstract)
- Target **Ophiuchus embedded protostars (28 fields, 37 YSOs)**: coordinates phase centers per field in Table 1 (e.g. c2d_811 16:26:21.35 -24:23:04.3 ICRS)  
  > "We selected 26 protostellar systems (Class 0 and Class I) from the surveys of (cite: Enoch09), (cite: Evans09), and (cite: ConnelleyGreene10)." (2.1 Source Selection); "assuming a distance of 140 pc" (2.3 ALMA Imaging); z/distance 140 pc  
  > "We selected 26 protostellar systems (Class 0 and Class I) from the surveys of (cite: Enoch09), (cite: Evans09), and (cite: ConnelleyGreene10)." (2.1 Source Selection); "assuming a distance of 140 pc" (2.3 ALMA Imaging); distance from not stated explicitly beyond citing Ortiz-León18 for Ophiuchus distance  
  > "We selected 26 protostellar systems (Class 0 and Class I) from the surveys of (cite: Enoch09), (cite: Evans09), and (cite: ConnelleyGreene10)." (2.1 Source Selection); "assuming a distance of 140 pc" (2.3 ALMA Imaging)

## Data provenance

- ALMA projects: 2015.1.01112.S
- bands: Band 6 (1.3 mm), full polarization  
  > "The 28 pointings were observed at 1.3 mm in full polarization on 2017 May 20, July 11, and July 14" (2.2 ALMA Observations)
- frequencies and spectral setup: 4 basebands, 1.875 GHz bandwidth, 64 channels each, centered at 224, 226, 240, 252 GHz  
  > "each baseband set to 1.875 GHz bandwidth and 64 channels, centered at 224 GHz, 226 GHz, 240 GHz, and 252 GHz." (2.2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15.1-1124.3 m (May); 16.7-2647.3 m (July)  
  > "The baselines ranged from 15.1 m to 1124.3 m for the May observations and 16.7 m to 2647.3 m for the July observations." (2.2 ALMA Observations)
- angular resolution: typically 0.27" x 0.21"  
  > "The map resolution for each field is typically $0.27\ensuremath{''} \times 0.21\ensuremath{''}$" (2.3 ALMA Imaging)
- max recoverable scale: ~2.6"  
  > "the maximum recoverable scale is $\sim 2.6\ensuremath{''}$" (2.3 ALMA Imaging)
- sensitivity: typical 27 uJy/beam  
  > "The typical map sensitivity is 27 $\mu$Jy beam$^{-1}$" (2.3 ALMA Imaging)
- time on source: ≈7 minutes per field  
  > "The total time spent on each target field is $\approx 7$ minutes." (2.2 ALMA Observations)
- observing dates: 2017 May 20, July 11, July 14  
  > "on 2017 May 20, July 11, and July 14 on shared tracks" (2.2 ALMA Observations)
- pi or archival as stated: Cycle 3 program 2015.1.01112.S (authors' program)  
  > "as part of the Cycle 3 program 2015.1.01112.S" (2.2 ALMA Observations)
- Other facility **SCUBA-2 (JCMT)**: 850 um background map for field figure  
  > "on a SCUBA-2 850 $\mu$m from (cite: Pattle15)" (2.1 Source Selection)
- External data: Multi-wavelength literature fluxes for spectral index/beta  
  > "We measure $\beta$ by combining our 233 GHz fluxes with complementary fluxes in the literature." (Disk Optical Depth) [from ArturV19, vanderMarel19, Brinch16, Hsieh19oph1, Cox17, Harris18, P. Sheehan private communication]
- External data: Galaxy number counts Schechter function at 1.3 mm  
  > "we use the 1.3 mm results of (cite: Carniani15) based on ALMA observations." (5.5 Galaxy Contamination) [from (cite: Carniani15)]
- External data: Outflow position angles  
  > "Estimated outflow position angle in the literature with reference if applicable" (Table disk_scatter) [from Friesen18, Kamazaki03, Bussmann07, vanderMarel13, Yen17, Visser02, vanderWiel19, Santangelo15]

## Processing

### Calibration

- pipeline or manual: manual calibration by observatory  
  > "The observations were manually calibrated using CASA 4.7.2 by the observatory." (2.2 ALMA Observations)
- casa version: CASA 4.7.2  
  > "The observations were manually calibrated using CASA 4.7.2 by the observatory." (2.2 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1517-2422 (20 May, 14 July); J1733-1304 (11 July)  
  > "J1517-2422 was also used for absolute flux calibration on the 20 May and 14 July executions, with J1733-1304 as the absolute flux calibration on 11 July." (2.2 ALMA Observations)
- flux scale uncertainty: ~10%  
  > "The expected flux uncertainty for the final observations is $\sim 10$%." (2.2 ALMA Observations)
- self calibration: phase-only on Stokes I for S/N>20, 1-3 rounds (scan length, 30.25 s, 15 s); amp+phase for c2d_1008a/b  
  > "We tested phase-only self calibration to the Stokes I data for all the observations with S/N $>20$ and only applied the ones with good gain solutions based on a visual inspection." (2.3 ALMA Imaging); "The first round of self calibration used solution intervals equivalent to the entire scan length and the second round used solution intervals of 30.25 s" (2.3 ALMA Imaging)

### Imaging

- task: CASA clean, interactive for Stokes I, non-interactive for Q and U  
  > "We used interactive `clean` for all the Stokes I maps and non-interactive `clean` for Stokes Q and U." (2.3 ALMA Imaging)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "we applied `clean` with Briggs weighting and a robust parameter of 0.5 and a UVtaper of 0.1$''$." (2.3 ALMA Imaging)
- uv taper: 0.1"  
  > "a robust parameter of 0.5 and a UVtaper of 0.1$''$." (2.3 ALMA Imaging)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: multi-scale used for sources with extended emission (scales not stated)  
  > "We also used the multi-scale option during the Stokes I `clean` for those sources with substantial extended emission." (2.3 ALMA Imaging)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: c2d_1008a and b mosaicked in final clean  
  > "we performed a final deep `clean` on the self-calibrated data with both fields to produce a mosaic." (2.3 ALMA Imaging)
- smoothing: _not stated_
- final beam: typically 0.27"x0.21"  
  > "The map resolution for each field is typically $0.27\ensuremath{''} \times 0.21\ensuremath{''}$" (2.3 ALMA Imaging)
- final rms: typical 27 uJy/beam; Table 1 per field  
  > "The typical map sensitivity is 27 $\mu$Jy beam$^{-1}$" (2.3 ALMA Imaging)

### Inherited from earlier work

- Polarization debiasing via PDF method  
  > "We follow (cite: HullPlambeck15) and calculate the debiased polarization intensities using a probability density function (PDF)." (2.4 Debias Correction) [from (cite: HullPlambeck15)]
- Multiplicity fraction and companion star fraction definitions  
  > "Following (cite: Tobin16), we calculate MF = (B + T + Q)/(S + B + T + Q) and CSF = (B + 2T + 3Q)/(S + B + T + Q)" (5.6 Class 0 and Class I Multiplicity) [from (cite: Tobin16)]
- Optically thin disk mass formula, kappa and temperature scaling  
  > "We estimate the mass assuming the thermal dust emission is optically thin (cite: Kauffmann08)" (Individual Sources) [from (cite: Kauffmann08); Andrews09; Andrews13]

### Not stated but needed to reproduce (our reading)

- Multiscale scales and clean thresholds/masks per field
- Self-calibration reference/solint per field beyond Table 1 and applied-solution criteria
- Exact polarization calibration steps and flux model
- Stokes I region used for imfit per source
- Weighting scheme and binning for weighted-average polarization angles
- Number of clean iterations / cell and image size
- Procedure for fitting mass-size relation (weights, data)

## Analysis recipe

1. **Calibrate and self-calibrate**: Manual observatory calibration in CASA 4.7.2; phase-only (and some amp+phase) self-cal on Stokes I  
  > "The observations were manually calibrated using CASA 4.7.2 by the observatory." (2.2 ALMA Observations)
   - software: CASA
   - parameter: self-cal for S/N>20, solints scan length, 30.25 s, 15 s  
  > "The first round of self calibration used solution intervals equivalent to the entire scan length and the second round used solution intervals of 30.25 s" (2.3 ALMA Imaging)
   - fitting: _not stated_
   - validation: visual inspection of noise decrease each round  
  > "we visually inspected the data after applying the solutions to ensure the noise was dropping with each iteration." (2.3 ALMA Imaging)
2. **Image Stokes I, Q, U**: clean with Briggs robust 0.5, 0.1" uvtaper  
  > "we applied `clean` with Briggs weighting and a robust parameter of 0.5 and a UVtaper of 0.1$''$." (2.3 ALMA Imaging)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive debiased polarization products**: PDF-based debiasing (tnmin in IDL) for S/N<9, sqrt(Q²+U²-σ²) above; compute angle and fraction  
  > "we measured $\mathcal{P}_I$ by taking the minimum of $-\mbox{PDF}(\mbox{$\mathcal{P}_I$}|\mbox{$\mathcal{P}_{obs}$},\mbox{$\sigma_{\mathcal{P}I}$})$ using the routine `tnmin`" (2.4 Debias Correction)
   - software: IDL tnmin
   - parameter: detection: I/σI>3, PI/σPI>3, σθ<10°  
  > "$\sigma_{\theta} < 10\degree$." (3.2 Polarization Overview)
   - fitting: _not stated_
   - validation: on/off-axis comparison of overlapping fields  
  > "The on-axis and off-axis polarization are well matched for offsets $\lesssim 5$$''$ from the phase center" (Conclusions)
4. **Measure continuum source properties and disk masses**: Gaussian fits with imfit; optically thin mass formula; inclination from cos i = b/a  
  > "simple Gaussian fits to the sources in the image plane using `imfit` in CASA." (3.1 Stokes I Overview)
   - software: CASA
   - assumption: d=140 pc, kappa=2.4 cm2/g at 233 GHz, gas-to-dust 100, T=20 K  
  > "we assume a distance of 140 pc, $\kappa_d = 2.4$ cm$^2$ g$^{-1}$ at 233 GHz" (Individual Sources)
   - fitting: _not stated_
   - validation: compared with literature masses and inclinations  
  > "Nevertheless, higher resolution observations of WL 17, Oph-emb-1, and VLA 1623B (cite: SheehanEisner17; Harris18; Hsieh19oph1) give consistent inclinations within 5 of our estimate, which suggest that our inclinations are broadly reliable." (Non-detected Polarization)
5. **Classify polarization morphology and mechanism**: Uniform/azimuthal/complex classification; compare with inclination and beta=alpha-2 as optical-depth proxy  
  > "We therefore define azimuthal polarization when at least half of the e-vectors have an angular deviation of $< 25\degree$ with the idealized elliptical pattern." (Polarization morphology definitions (Section 4.1))
   - parameter: optically thick if beta<0.5  
  > "We consider a source to be optically thick if $\beta < 0.5$, not thick if $\beta > 0.5$." (Table disk_scatter_sum)
   - assumption: geometrically thin disks; beta→0 when optically thick  
  > "We note, however, that disk inclinations as measured from $\cos{i} = b/a$ are only robust if the disk is well resolved (e.g., over two beams along the minor axis) and geometrically thin." (Non-detected Polarization)
   - fitting: _not stated_
   - validation: _not stated_
6. **Estimate galaxy contamination probability**: Carniani15 Schechter counts integrated over annuli across primary beam for 5/10/20σ thresholds  
  > "we calculate the probability of detecting a galaxy at each threshold in annuli separated by $\sim 0.3$$''$" (5.5 Galaxy Contamination)
   - assumption: galaxies randomly distributed in primary beam  
  > "our probabilities assume galaxies are distributed randomly in the primary beam" (5.5 Galaxy Contamination)
   - fitting: _not stated_
   - validation: compare expected ~6 fields to observed number  
  > "we estimate that an extragalactic source should be detected at 10$\sigma$ in roughly 6 fields, which is comparable to the observed number." (Galaxy Contamination)

## Software

- **CASA** 4.7.2: calibration, clean imaging, imfit  
  > "manually calibrated using CASA 4.7.2 by the observatory" (2.2 ALMA Observations)
- **IDL tnmin** : minimizing PDF for debiasing  
  > "using the routine `tnmin`[^3] in IDL" (2.4 Debias Correction)
- **getALMAflux (analysis utilities)** : check calibrator fluxes  
  > "using analysis utilities task `getALMAflux` in CASA" (2.2 ALMA Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| fraction detected in polarization | 14/37 (38%) | not stated | dimensionless | 3 | We find that 14/37 (38%) of the observed YSOs are detected in polarization at our sensitivity. |
| compact continuum sources detected | 41 | not stated | sources | 4 | we identify 41 distinct compact sources in the 27 fields. |
| Multiplicity fraction (35-1800 au) | 0.29 | 0.11 | dimensionless | 0 | we measure MF = 0.29$\pm$0.11 and CSF = 0.41$\pm$0.12 |
| Companion star fraction | 0.41 | 0.12 | dimensionless | 0 | we measure MF = 0.29$\pm$0.11 and CSF = 0.41$\pm$0.12 |
| weighted mass-size slope | 1.13 | 0.01 | dimensionless | 4 | The slope of this relation is 1.13 $\pm$ 0.01. |
| galaxy detection probability within primary beam (5σ/10σ/20σ) | 66% / 31% / 10% | not stated | percent | 6 | the probability of detecting a galaxy within the primary beam is 66% for the $5\sigma$ threshold, 31% at $10\sigma$, and 10% at $20\sigma$. |

## Qualitative findings

- Nine sources show polarization consistent with dust self-scattering; remaining sources show mostly poloidal/hourglass inferred fields, no toroidal component  
  > "We find no evidence of a strong toroidal field component toward any of our disks." (abstract)

## Claim tuples

- H: Does disk-scale dust polarization trace magnetic fields? | E: 1.3 mm full-polarization survey of 28 fields with morphology/inclination/beta analysis | R: 9/14 detected sources consistent with self-scattering | F: Polarization mostly reflects self-scattering in optically thick disks, not magnetic fields | **supported**
- H: Inclination controls polarization morphology and detectability | E: Compare inclinations of detected vs undetected sources (Anderson-Darling) | R: Uniform sources i>60°, azimuthal <60° | F: High-inclination disks are best targets | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: k-RAT, aerodynamic alignment, mechanical torques not favoured for uniform sources  
  > "we do not favour any of these alternative polarization mechanisms for our sources with uniform polarization angles." (4.3 Polarization From Other Mechanisms)
- How they decided it was enough: _not stated_
- Limitation (authors): Gaussian fits and masses are approximate; inclinations biased for compact disks; dust scattering effects on beta ignored  
  > "We caution, however, that both the Gaussian fits and the mass measurements should be considered approximations" (5.3 Disk Properties)
- Caveat (inferred, ours): beta as optical depth proxy is weak and mixes with grain properties
- Caveat (inferred, ours): Instrumental polarization (0.03-0.1%) not included in errors
- Caveat (inferred, ours): Gaussian-fit inclinations for unresolved disks
- Caveat (inferred, ours): Class reclassification relies on heterogeneous literature

## Reproducibility

- Data public (paper): Released maps on Dataverse; ALMA data from public program  
  > "The data products are available at Dataverse[^4] for individual fields or for the entire sample." (3.3 Deliverables)
- Products in archive: _not stated_
- Missing: clean masks/scales
- Missing: per-field self-cal details
- Missing: IDL debiasing code
- Missing: literature fluxes (private communication)
- Data volume (inferred): ~100s of GB for 3 EBs raw; ~tens of GB calibrated
- Score (inferred): 3/5, Data public and many parameters given, but clean masks, multiscale scales and some inputs are unstated.
- Rediscovery candidate: yes, Public data, recipe largely specified, numeric detection stats and fluxes.

## Links

- Method: (cite: HullPlambeck15) (polarization debiasing method)
- Method: (cite: Kauffmann08) (disk mass formula)
- Companion: (cite: Sadavoy18b) (first VLA 1623 results)
- Companion: (cite: Sadavoy18c) (first IRAS 16293 results)
- Related: Cieza19 ODISEA
- Related: Tobin16 Perseus VANDAM

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
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
  "facts": 80,
  "stated": 55,
  "rate": 0.688
 },
 "evidence_ok": true
}
```
