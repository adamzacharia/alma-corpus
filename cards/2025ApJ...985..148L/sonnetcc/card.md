# L1448 IRS3B: Dust Polarization Aligned with Spiral Features, Tracing Gas Flows

`2025ApJ...985..148L` | The Astrophysical Journal 2025 | first author: Looney, Leslie W. | arXiv: 2503.07787 | DOI: 10.3847/1538-4357/adcb9f

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: Which dust polarization mechanisms (magnetic alignment, self-scattering, mechanical alignment) operate in the envelope, circum-multiple disk, spirals and compact sources of the protostellar multiple L1448 IRS3B  
  > "Circum-multiple dust structures in protostellar systems provide a unique environment to probe different polarization alignment mechanisms." (abstract); "We use the dust polarization to infer possible polarization mechanisms in the circum-multiple disk and inner envelope of L1448 IRS3B, finding evidence of three polarization mechanisms." (Introduction)
- Target **L1448 IRS3B**: coordinates _not stated_; z/distance 288 pc  
  > "The L1448 IRS3 system is at a distance of 288 pc based on recent constraints (cite: Ortiz2018; Zucker2019)." (Introduction); distance from (cite: Ortiz2018; Zucker2019)  
  > "The L1448 IRS3 system is at a distance of 288 pc based on recent constraints (cite: Ortiz2018; Zucker2019)." (Introduction)
- Target **L1448 IRS3A**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **L1448 IRS3C (L1448 NW)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **L1448 IRS3-ALMA (likely background galaxy)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2021.1.00276.S
- bands: Band 4 and Band 7, full polarization continuum  
  > "We present ALMA Band 4 and Band 7 polarization observations toward the multiple young system L1448 IRS3B." (abstract); "observations in full polarization at continuum Band 4 and Band 7" (Observations and Data Reduction)
- frequencies and spectral setup: continuum; wavelengths 2.1 mm (Band 4) and 873 um (Band 7); spectral windows not stated  
  > "(i.e. $\lambda$ = 2.1 mm and 873 $\mu$m, respectively)" (Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Band 4 has shorter baselines than Band 7 (values are in the observation table, not in the text)  
  > "Band 4 is more sensitive to larger structures due to its shorter baselines" (Results)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **VLA (VANDAM survey, Ka band)**: Non-detection of L1448 IRS3-ALMA at 8 mm and 1 cm (RMS 0.012 and 0.01 mJy/beam)  
  > "is undetected in the Perseus VANDAM survey of (cite: Tobin2016) in the VLA Ka Band" (Other sources in the Field)
- Other facility **ALMA VANDAM Band 6**: Non-detection of L1448 IRS3-ALMA at 1.3 mm, RMS 0.33 mJy/beam  
  > "is also not detected in the VANDAM ALMA Band 6 observations" (Other sources in the Field)
- External data: Distance to L1448 IRS3 of 288 pc  
  > "The L1448 IRS3 system is at a distance of 288 pc based on recent constraints (cite: Ortiz2018; Zucker2019)." (Introduction) [from (cite: Ortiz2018; Zucker2019)]
- External data: C17O (3-2) velocity field at 0.2 arcsec: Keplerian motion near source a, no clear perturbation by spirals  
  > "reveals Keplerian motion around a location near source $a$ without any clear perturbations caused by the spiral structures" (Results) [from (cite: Nick2021)]
- External data: Protostellar mass of source c, upper limit 0.2 Msun (sources a+b ~1.2 Msun)  
  > "with an upper limit on the protostellar mass of 0.2 M$_\odot$" (Introduction) [from (cite: Nick2021)]
- External data: Source c Gaussian fit in Band 6: 0.2 x 0.175 arcsec, PA 25 deg  
  > "find an extended source of 0.2$''$ $\times$ 0.175$''$ with a PA of 25$^\circ$" (Polarization from Self-Scattering) [from (cite: Reynolds2023)]
- External data: Dust ring around source d with estimated PA of 45 deg  
  > "they note a dust ring around source $d$ with an estimated PA of 45$^\circ$ PA" (Polarization from Self-Scattering) [from (cite: Reynolds2023)]
- External data: Earlier SMA 870 um polarization: ~3% at angle -67 deg (east of north)  
  > "a dust polarization fraction of $\sim$3% with a polarization angle of -67$^\circ$ (east of north) has been observed" (Introduction) [from (cite: Galametz2018)]
- External data: Combined bolometric temperature of IRS3A and B of 25.6 K (eHOPS)  
  > "gives a combined bolometeric temperature for L1448 IRS3A and B of 25.6 K" (Introduction) [from (cite: Pokhrel2023)]
- External data: Three compact sources a, b, c in IRS3B  
  > "We detect at both wavelengths the arcs or spiral structures and the three compact sources defined by (cite: John2016)" (Results) [from (cite: John2016)]

## Processing

### Calibration

- pipeline or manual: Calibrated by NRAO staff within CASA; pipeline vs manual not stated  
  > "The observations were calibrated by the National Radio Astronomy Observatory staff (since polarization is a non-standard observing mode)" (Observations and Data Reduction)
- casa version: CASA 6.4.1.12  
  > "within CASA, Common Astronomy Software Applications (cite: casa2022), version 6.4.1.12." (Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10%  
  > "As suggested in the ALMA handbook, the absolute flux calibration accuracy is adopted to be" (Observations and Data Reduction)
- self calibration: auto_selfcal script; Band 4 phase-only intervals inf-EB, inf, 26.21s, 8.06s, 4.03s, int, then amp+phase at 300s; Band 7 phase-only inf-EB, inf, 48.38s, then amp+phase at inf  
  > "The Band 4 observations were iteratively self-calibrated, phase only, with intervals of" (Observations and Data Reduction); "Afterwards, a round of amplitude and phase self-calibration was performed with an interval of 300s to further improve the calibration." (Observations and Data Reduction); "The Band 7 observations were self-calibrated, phase only, with intervals of" (Observations and Data Reduction)

### Imaging

- task: tclean, Stokes I, Q, U maps  
  > "The Stokes I, Q, and U maps were then created using the CASA task" (Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5 (Band 4 and 7); robust = 1.0 for a Band 4 low-resolution map  
  > "weighting of 0.5, which is a good compromise between resolution and sensitivity" (Observations and Data Reduction); "We used Robust weighting of 1.0 as a compromise between sensitivity and larger spatial scale sensitivity." (Other sources in the Field)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Band 7 and Band 4 smoothed to the same spatial resolution to compare angles and brightness temperatures  
  > "the difference between the two Bands when smoothed to the same spatial resolution" (Results)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Polarization debiasing of low S/N (<3 sigma_P) data via a probability density function  
  > "Following (cite: Wardle1974; Vaillancourt2006; Hull2015), the linear polarization at low S/N ($<$ 3$\sigma_P$) was debiased using the probability density function (PDF)" (Observations and Data Reduction) [from (cite: Wardle1974; Vaillancourt2006; Hull2015)]
- Robust weighting choice  
  > "which is a good compromise between resolution and sensitivity (cite: Briggs1995)" (Observations and Data Reduction) [from (cite: Briggs1995)]
- Compact source labels a, b, c  
  > "the three compact sources defined by (cite: John2016)" (Results) [from (cite: John2016)]

### Not stated but needed to reproduce (our reading)

- Observation table (arrays, baselines, dates, time on source, max recoverable scale) is referenced but its contents are not in the text
- Spectral window setup and bandwidth for Band 4 and Band 7
- Flux, bandpass, gain and polarization calibrators and calibration pipeline/manual details
- tclean image size, cell size, deconvolver, niter, threshold, masks and uv range/taper for the main maps
- Method used to smooth Band 4/7 to a common beam
- Exact auto_selfcal version and settings beyond the listed solution intervals
- Mask and thresholds used to define the spiral spine for the spline fit, and the 4 segment definitions
- Definition (polygons) of the tan and cyan polarization regions in Figure 5
- How mean fractional polarization is computed (S/N cut, per-beam sampling, uncertainty meaning)
- Brightness temperature formula inputs and beam handling
- Primary-beam correction details

## Analysis recipe

1. **Self-calibrate and image Stokes I, Q, U**: Phase-only then amplitude+phase self-calibration with auto_selfcal on NRAO-calibrated data, then tclean Stokes I, Q, U maps with Briggs robust 0.5  
  > "After the data were calibrated, we further performed self-calibration using the" (Observations and Data Reduction); "The Stokes I, Q, and U maps were then created using the CASA task" (Observations and Data Reduction)
   - software: CASA, tclean, auto_selfcal
   - parameter: Band 4 phase-only intervals inf-EB, inf, 26.21s, 8.06s, 4.03s, int; amp+phase 300s  
  > "Afterwards, a round of amplitude and phase self-calibration was performed with an interval of 300s to further improve the calibration." (Observations and Data Reduction)
   - parameter: Band 7 phase-only inf-EB, inf, 48.38s; amp+phase inf  
  > "The Band 7 observations were self-calibrated, phase only, with intervals of" (Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive debiased polarized intensity, angle and noise**: P_m = sqrt(Q^2+U^2); sigma_P from sigma_Q and sigma_U; debias with Rice-type PDF at S/N<3 and with P = sqrt(Q^2+U^2-sigma_P^2) at higher S/N; chi = 0.5 arctan(U/Q)  
  > "The measured linear polarization intensity map is created using" (Observations and Data Reduction); "was used to debias the linear polarization." (Observations and Data Reduction)
   - parameter: Low S/N threshold 3 sigma_P for PDF debiasing  
  > "the linear polarization at low S/N ($<$ 3$\sigma_P$) was debiased using the probability density function (PDF)" (Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Make brightness temperature maps and constrain spectral index/optical depth**: Brightness temperature maps without Rayleigh-Jeans approximation; spectral index lower limits tested with mtmfs and a restricted uv range of 50-1000 klambda with uv taper to match beam areas  
  > "brightness temperature maps (made without using the Rayleigh-Jeans approximation)" (Results); "between 50 and 1000 k$\lambda$ coupled with a" (Discussion); "that resulted in beams whose areas were within a few percent of each other." (Discussion)
   - software: tclean
   - parameter: uv range 50-1000 klambda with taper (beam areas within a few percent)  
  > "between 50 and 1000 k$\lambda$ coupled with a" (Discussion)
   - assumption: Brightness temperature is the temperature required for a blackbody to match the observed intensity  
  > "The brightness temperature is the temperature required for a blackbody to match the observed intensity." (Results)
   - fitting: _not stated_
   - validation: Band 4 remained more sensitive to envelope in both tests, so indices are only lower limits  
  > "However, due to the contamination, these are only lower limits to the spectral index." (Discussion)
4. **Identify polarization regions by morphology and fraction**: Regions classed as magnetic, scattering or mechanical using polarization fraction, location and angle relative to disk minor axis and spirals  
  > "The region was chosen using a combination of polarization fraction and location (off the circum-multiple disk)." (Magnetic Field Alignment)
   - fitting: _not stated_
   - validation: _not stated_
5. **Model polarization angles from the continuum spiral spine and compare with observations**: Mask spirals in Stokes I, fit cubic splines (UnivariateSpline, smoothing factor 5, 4 segments in Band 7), take spline slope per pixel as the model vector, compare with observed angles  
  > "We use a simple mask to define the spiral structures in the Stokes I maps, then fit cubic splines to the emission using" (Simple Model of Polarization Morphology); "with a smoothing factor = 5." (Simple Model of Polarization Morphology); "which is essentially the arctangent of the instantaneous slope of the spline fit." (Simple Model of Polarization Morphology)
   - software: SciPy
   - parameter: smoothing factor = 5  
  > "with a smoothing factor = 5." (Simple Model of Polarization Morphology)
   - assumption: Spiral arms create a drift velocity of dust relative to gas, traced by the continuum  
  > "Under the assumption that the spiral arms are creating a drift velocity of the dust relative to the gas (and traced by the dust continuum)" (Simple Model of Polarization Morphology)
   - fitting: Cubic spline fit (UnivariateSpline); no sampler  
  > "We use a simple mask to define the spiral structures in the Stokes I maps, then fit cubic splines to the emission using" (Simple Model of Polarization Morphology)
   - validation: Histogram of model-minus-observed angle differences: standard deviation 18.5 deg, centred near 0 deg  
  > "the standard deviation of the distribution is 18.5$^\circ$ with the distribution centered around 0$^\circ$, both of which are good for such a simple model." (Simple Model of Polarization Morphology)
6. **Measure mean fractional polarization along spirals and in inner regions**: Mean P/I per beam along the spiral feature and in the high-resolution inner region, per band  
  > "1.5$\pm$0.7% and 2.5$\pm$1.3%, for Band 4 and Band 7, respectively" (Simple Model of Polarization Morphology)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.4.1.12: Calibration (by NRAO staff) and imaging with tclean  
  > "within CASA, Common Astronomy Software Applications (cite: casa2022), version 6.4.1.12." (Observations and Data Reduction)
- **tclean** : Stokes I, Q, U imaging with Briggs weighting  
  > "The Stokes I, Q, and U maps were then created using the CASA task" (Observations and Data Reduction)
- **auto_selfcal** : Iterative self-calibration with refantmode strict  
  > "After the data were calibrated, we further performed self-calibration using the" (Observations and Data Reduction)
- **SciPy** : UnivariateSpline cubic spline fits to the spiral structures  
  > "We use a simple mask to define the spiral structures in the Stokes I maps, then fit cubic splines to the emission using" (Simple Model of Polarization Morphology)
- **astropy** : Listed as software used; specific use not stated  
  > "astropy (cite: 2013A&A...558A..33A; 2018AJ....156..123A; Astropy2022) and SciPy (cite: SciPy)." (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean polarization fraction in inner regions, Band 4 | 1.2 | 0.6 | % | 6 | the mean polarization fraction drops to 1.2$\pm$0.6% and 2.4$\pm$1.1% in Band 4 and Band 7, respectively |
| Mean polarization fraction in inner regions, Band 7 | 2.4 | 1.1 | % | 6 | the mean polarization fraction drops to 1.2$\pm$0.6% and 2.4$\pm$1.1% in Band 4 and Band 7, respectively |
| Mean fractional polarization along spiral arms, Band 4 | 1.5 | 0.7 | % | 6 | 1.5$\pm$0.7% and 2.5$\pm$1.3%, for Band 4 and Band 7, respectively |
| Mean fractional polarization along spiral arms, Band 7 | 2.5 | 1.3 | % | 6 | 1.5$\pm$0.7% and 2.5$\pm$1.3%, for Band 4 and Band 7, respectively |
| Standard deviation of model-minus-observed polarization angle, Band 7 | 18.5 | not stated | deg | 5 | the standard deviation of the distribution is 18.5$^\circ$ with the distribution centered around 0$^\circ$ |
| Inner envelope polarization fraction (high-resolution maps) | 8 | not stated | % | 6 | at 8% in Band 4 and Band 7 |
| Lower-limit spectral index, bright compact sources | 2 | lower limit | dimensionless | 3 | The bright compact emission had lower-limit spectral indices of $\alpha$ = 2 with the spiral arms being 1.5. |
| Lower-limit spectral index, spiral arms | 1.5 | lower limit | dimensionless | 3 | The bright compact emission had lower-limit spectral indices of $\alpha$ = 2 with the spiral arms being 1.5. |
| Band 7 to Band 4 brightness temperature ratio | 1.25 (central region), 1.5 (compact sources and outer spiral edge) | not stated | dimensionless | 3 | typically by factors of 1.25 for the central region and 1.5 near the compact sources |
| Mean Band 7 polarization angle around source c | 126 | not stated | deg | 4 | has an angle of 126$^\circ$, which is comparable to being along the minor axis |
| Mean Band 7 polarization angle around source a | 220 | not stated | deg | 4 | has an angle of 220$^\circ$, which is comparable to being along the minor axis of the ring emission |
| Rotation of Band 7 polarization holes around source c | ~20 | not stated | deg east of north | 4 | appear rotated by $\sim 20^{\circ}$ east-of-north |
| Total flux of L1448 IRS3-ALMA in Band 4 (primary beam corrected) | 221 | 25 | uJy/beam | 0 | the total flux is 221 $\pm$25 $\mu$Jy/beam (primary beam corrected) |

## Qualitative findings

- Polarization in the two Bands has consistent orientation in most locations  
  > "The polarization in the two Bands is consistent with each other, presenting multiple polarization morphologies." (abstract)
- Polarized emission generally follows the continuum spiral structures  
  > "The most striking is that the polarized emission generally follows along the spiral structures" (Results)
- First resolution of the spiral structures in Band 4  
  > "This is the first time that the spiral structures have been resolved in Band 4." (Conclusions)
- Polarization alignment with the continuum spiral has not been shown before  
  > "This polarization alignment with the dust continuum spiral structure in L1448 IRS3B has not been shown before." (Model Implications)

## Claim tuples

- H: Is polarization in the inner envelope due to magnetic grain alignment? | E: Compare Band 4/7 polarization angles and fractions in outer regions with earlier lower-resolution polarization | R: Outer-region angles are consistent with earlier envelope angles and trend radially, implying a toroidal-like field | F: Envelope polarization is likely magnetically aligned | **partially**
- H: Is polarization around compact sources a and c due to self-scattering? | E: Compare mean Band 7 angles near sources c and a with the minor axes of their Band 6 structures | R: Angles of 126 and 220 deg are comparable to being along the minor axes | F: Scattering around a and c, which are likely the most optically thick | **partially**
- H: Does the polarization along the spirals trace mechanical alignment by gas-dust drift? | E: Spline model of the spiral spine compared with the Band 7 polarization angle map | R: Difference distribution centred near 0 deg with standard deviation 18.5 deg | F: Polarization consistent with mechanical alignment tracing relative gas flow along the spiral arms | **partially**
- H: Is radiative alignment important in IRS3B? | E: Compare polarization morphology around source c and along spirals with circular k-RAT pattern | R: Pattern is elongated or elliptical, not circular | F: No strong evidence for radiative alignment | **supported**

## Reasoning

- Why this data: Circum-multiple disk systems are among the few with posited combined magnetic and scattering mechanisms  
  > "In order to explore the polarization of disks, we use the young multiple protostellar system L1448 IRS3, as circumbinary disks to date are among the few sources with posited combinations of magnetic field and scattering polarization mechanisms." (Introduction)
- Why this method: Robust 0.5 chosen as a resolution/sensitivity compromise  
  > "which is a good compromise between resolution and sensitivity (cite: Briggs1995)" (Observations and Data Reduction)
- Alternative: Magnetic alignment in the spirals (Guillet et al. style large-grain model) judged less favorable than mechanical alignment  
  > "we posit that the magnetic alignment of dust grains in the spiral structures is less favorable than mechanical alignment (see discussion below)." (Magnetic Field Alignment)
- Alternative: Radiative alignment rejected because morphology is elliptical, not circular  
  > "However, that polarization morphology is not circular (as expected for radiative dust alignment) either; it is very elongated or elliptical, which is inconsistent with radiative dust alignment." (Radiative Alignment)
- How they decided it was enough: _not stated_
- Limitation (authors): Spectral index values are only lower limits because Band 4 is more sensitive to envelope emission  
  > "However, due to the contamination, these are only lower limits to the spectral index." (Discussion)
- Limitation (authors): Optical depth poorly constrained, making polarization mechanism harder to determine  
  > "With only weak constraints on the spectral index, we have very little knowledge of the optical depth in the source, which will make it more difficult to determine the polarization mechanisms." (Discussion)
- Caveat (inferred, ours): Mechanical-alignment claim rests on a morphological match with a spline model (18.5 deg scatter) and no competing quantitative model
- Caveat (inferred, ours): Region classification (tan/cyan) is qualitative and depends on chosen polygons
- Caveat (inferred, ours): Band 4 versus Band 7 comparison limited by different uv coverage and envelope filtering
- Caveat (inferred, ours): Debiased high polarization fractions at disk edges may be biased by resolved-out Stokes I

## Reproducibility

- Data public (paper): ALMA data and reduction scripts available from the ALMA archive  
  > "The ALMA data and reduction scripts are available from the ALMA archive." (Acknowledgments)
- Products in archive: _not stated_
- Code: Final maps, scripts used to make them and the selfcal script are in the Illinois Data Bank  
  > "The final maps and the scripts used to make them (as well as the selfcal script) are available in the Illinois Data Bank (cite: illinoisdatabankIDB-5442905)." (Acknowledgments)
- Missing: Observation table contents not in the text
- Missing: tclean imaging parameters beyond robust
- Missing: Region polygons and spline mask definitions
- Data volume (inferred): Likely tens of GB of raw data for two full-polarization bands of one project; exact size not stated
- Score (inferred): 4/5, Public ALMA data, NRAO calibration, released scripts, selfcal script and final maps on Illinois Data Bank, and numeric summary statistics; some imaging parameters are unstated in the text.
- Rediscovery candidate: yes, Data are public, scripts are released and main results include numeric polarization fractions and angle scatter.

## Links

- Method: (cite: Briggs1995) (Briggs weighting used in tclean)
- Companion: (cite: Nick2021) (Earlier Band 7 continuum and C17O kinematics of IRS3B)
- Companion: (cite: Reynolds2023) (Higher resolution Band 6 observations revealing source d and the ring)
- Related: Perseus VANDAM survey (VLA and ALMA Band 6)
- Related: eHOPS

## Checks

```json
{
 "quotes": 89,
 "quotes_ok": 89,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 104,
  "stated": 59,
  "rate": 0.567
 },
 "evidence_ok": true
}
```
