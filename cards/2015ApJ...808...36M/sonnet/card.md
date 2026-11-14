# New Measurements of the Radio Photosphere of Mira Based on Data from the JVLA and ALMA

`2015ApJ...808...36M` | The Astrophysical Journal 2015 | first author: Matthews, L. D. | arXiv: 1506.03075 | DOI: 10.1088/0004-637X/808/1/36

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: Do JVLA and ALMA continuum data at 46, 96 and 229 GHz match the radio photosphere model of Mira A (size, shape, flux, brightness structure), and what are the properties of Mira B?  
  > "The measured millimeter flux densities are consistent with a radio photosphere model derived from previous observations, where flux density $S_{\nu}\propto\nu^{1.86}$." (abstract)
- Target **Mira AB (o Ceti)**: coordinates _not stated_; z/distance 110±9 pc  
  > "Throughout the paper we adopt a distance of 110$\pm$9 pc (Haniff et al. 1995), based on the period-luminosity relation of Feast et al. 1989." (1 Introduction (footnote 1)); distance from Haniff et al. 1995, from period-luminosity relation of Feast et al. 1989  
  > "Throughout the paper we adopt a distance of 110$\pm$9 pc (Haniff et al. 1995), based on the period-luminosity relation of Feast et al. 1989." (1 Introduction (footnote 1))

## Data provenance

- ALMA projects: 2011.0.00014.SV
- bands: ALMA Band 3 (94 GHz) and Band 6 (229 GHz); JVLA Q band 46 GHz  
  > "ALMA observations of Mira were performed in Band 3 (94 GHz) on 2014 October 17 and 25 and in Band 6 (229 GHz)" (2.2 ALMA Data)
- frequencies and spectral setup: Band 3: 87.3–89.0, 97.4–99.1, 99.3–101.0 GHz; Band 6: ~228.7–230.4 GHz; eight 250 MHz channels per spw  
  > "The frequency ranges sampled were 87.3–89.0 GHz, 97.4–99.1 GHz, and 99.3–101.0 GHz." (3.2 ALMA Data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: ALMA baselines up to 15.2 km; JVLA A configuration (0.68 to 36.4 km)  
  > "in its most extended (A) configuration (0.68 km to 36.4 km baselines)" (2.1 JVLA Data)
- baselines: _not stated_
- angular resolution: Dirty beams 79x58 mas (B3), 32x23 mas (B6)  
  > "| 6 (229 GHz) | 32 | 23 | +19 | 27.3 | 34.8 |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: JVLA ~1 h 51 min; ALMA ~1.6 h Band 3, ~1.1 h Band 6  
  > "The total on-source integration times for Mira were approximately 1.6 hours in Band 3 and 1.1 hours in Band 6." (2.2 ALMA Data)
- observing dates: ALMA: 2014 Oct 17, 25 (Band 3), Oct 29, Nov 1 (Band 6); JVLA 2014 Feb 23  
  > "on 2014 October 17 and 25 and in Band 6 (229 GHz) on 2014 October 29 and 2014 November 1" (2.2 ALMA Data)
- pi or archival as stated: ALMA science verification data, public since 2015 February; JVLA program 14A-026  
  > "The data were obtained by ALMA staff for science verification purposes (ALMA Partnership 2015) and were released to the public in 2015 February." (2.2 ALMA Data)
- Line: SiO v=1, J=1-0 maser (JVLA, used for phase self-calibration) (not stated)
- Other facility **JVLA**: 46 GHz continuum data  
  > "Observations of Mira at 46 GHz (7 mm) were carried out with the JVLA" (2.1 JVLA Data)
- External data: Radio photosphere model S=0.50(nu/10GHz)^1.86 (D/100pc)^-2 mJy  
  > "represents the flux density as a function of frequency predicted by the radio photosphere model of RM97" (4.1.1 Mira A) [from Reid & Menten 1997 (RM97)]
- External data: 338 GHz ALMA flux points for Mira A and B  
  > "Additional data points at 338 GHz from Ramstedt et al. (2014) are also included." (4.1.1 Mira A) [from Ramstedt et al. 2014]
- External data: 3C48 flux density scale  
  > "The absolute flux density scale was calculated using the latest time-dependent flux density values for 3C48 from Perley & Butler (2013)." (3.1 JVLA Data) [from Perley & Butler (2013)]

## Processing

### Calibration

- pipeline or manual: ALMA: archive pipeline-calibrated uv data from Science Verification pages, plus self-calibration; JVLA: manual in AIPS  
  > "We retrieved the pipeline calibrated $u$-$v$ data in the form of CASA measurement sets for each of the two ALMA bands" (3.2 ALMA Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: JVLA 3C48; ALMA J0334-4008, J0238+1636, J2258-2758  
  > "For the Band 3 data from 25 October, J0238+1636 and J2258-2758 were used as flux density calibrators" (3.2 ALMA Data)
- flux scale uncertainty: 20% absolute flux calibration assumed  
  > "absolute flux density calibration (assumed to contribute relative errors of 1% and 20%, respectively, at all three observed frequencies)" (Appendix)
- self calibration: ALMA: phase-only at record length (~6 s B3, ~3 s B6) then amp+phase 60 s, gains normalized; JVLA: SiO maser phase self-cal then amp+phase  
  > "additional iterations were performed, solving for both amplitude and phase with a solution interval of 60 seconds." (3.2 ALMA Data)

### Imaging

- task: Imaging and deconvolution in AIPS  
  > "Imaging and deconvolution of the JVLA and the ALMA data were performed using in AIPS." (3.3 Imaging the Data)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0  
  > "we used a Briggs robust value of ${\cal R}$=0, a cell size of 5 mas" (3.3 Imaging the Data)
- uv taper: _not stated_
- cell size: 5 mas  
  > "a cell size of 5 mas" (3.3 Imaging the Data)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Frequency dependence of primary beam corrected using spectral index 1.86  
  > "Corrections were applied during imaging for the frequency dependence of the primary beam and the expected spectral index of Mira A within the JVLA band" (3.3 Imaging the Data)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Circular restoring beams 39.7, 68.7, 27.3 mas  
  > "a circular restoring beam with a FWHM equal to the mean of the dimensions of the dirty beam at the appropriate frequency" (3.3 Imaging the Data)
- final rms: 29.0, 19.7, 34.8 uJy/beam (Q, B3, B6)  
  > "| 3 (96 GHz) | 79 | 58 | +42 | 68.7 | 19.7 |" (Table 1)

### Inherited from earlier work

- Maser-based phase self-calibration method  
  > "We therefore employed the method developed by Reid & Menten (1990) to improve the phase calibration using the stellar maser signal." (3.1 JVLA Data) [from Reid & Menten (1990)]
- Spectral index alpha=1.86 adopted from radio photosphere model  
  > "the expected spectral index of Mira A within the JVLA band ($\alpha$=1.86; RM97)" (3.3 Imaging the Data) [from RM97]

### Not stated but needed to reproduce (our reading)

- Number of clean iterations, clean masks/thresholds in AIPS
- Exact AIPS/CASA versions
- Which flagged channels containing line emission in JVLA data
- Data selection and weighting for uv fits (OMFIT settings)
- Exact target coordinates
- Whether ALMA self-cal reference antenna and models were specified

## Analysis recipe

1. **Calibrate JVLA data**: AIPS calibration with 3C48 flux scale, NRAO150 bandpass, J0215-0222 gains, SiO maser phase self-cal  
  > "Bandpass calibration was performed using NRAO150, assuming a spectral index $\alpha$=0.4 (Trippe et al. 2010)." (3.1 JVLA Data)
   - software: AIPS, Obit
   - fitting: _not stated_
   - validation: amplitude scale change from self-cal <0.5%  
  > "the resulting change in the amplitude scale was measured to be less than 0.5%" (3.1 JVLA Data)
2. **Self-calibrate ALMA pipeline data**: Self-cal on Mira AB continuum, phase then amp+phase  
  > "Using the continuum emission from the Mira AB binary itself, we performed self-calibration on the pipeline data for both ALMA bands." (3.2 ALMA Data)
   - software: CASA
   - fitting: _not stated_
   - validation: amplitude change <0.7%  
  > "were measured to be $<$0.7%" (3.2 ALMA Data)
3. **Image the data**: AIPS imaging, robust 0, 5 mas cells, circular restoring beam  
  > "we used a Briggs robust value of ${\cal R}$=0, a cell size of 5 mas" (3.3 Imaging the Data)
   - software: AIPS
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit size, shape, flux of Mira A and B**: Uniform elliptical disk fits to visibilities and elliptical Gaussian fits to images  
  > "The first was to fit a uniform elliptical disk model to the visibility data at each observed frequency" (4.1.1 Mira A)
   - software: AIPS (OMFIT, JMFIT)
   - assumption: distance 110 pc; Tb=2Sc^2/(k nu^2 pi theta_maj theta_min)  
  > "The brightness temperature was computed as $T_{b}=2S_{\nu}c^2/(k\nu^{2}\pi\theta_{\rm maj}\theta_{\rm min})$" (Table 2)
   - fitting: Least-squares fits; errors per Condon (1997)  
  > "compute uncertainties according to the formalism outlined by Condon (1997)" (Appendix)
   - validation: Monte Carlo and artificial source injection tests for systematic errors  
  > "we introduced into our actual visibility data at each frequency a series of artificial elliptical Gaussians and uniform elliptical disks" (Appendix)
5. **Test brightness non-uniformity**: Compare multi-component visibility models (ring, point, Gaussian) and residual images for 229 GHz  
  > "for the 229 GHz data, two-component models produced a clear improvement in $\chi^{2}$, with the elliptical disk+Gaussian fit providing the best match to the data" (4.2)
   - software: AIPS
   - fitting: chi-square comparison  
  > "none of these three simple models produced a significant improvement in the fit (as assessed by visual inspection of the residuals and the improvement in the $\chi^{2}$ statistic)" (Results, Evidence for Non-uniformities on the Surface of Mira A)
   - validation: Residual image from visibility subtraction compared to image-plane differencing  
  > "the result is virtually indistinguishable, suggesting that the image residuals are not solely artifacts of the deconvolution process" (4.2)

## Software

- **AIPS** : JVLA calibration, imaging, and fitting of all data  
  > "Data processing for the JVLA data was performed using the Astronomical Image Processing System (AIPS; Greisen 2003)" (3.1 JVLA Data)
- **Obit** : load ASDM data into AIPS  
  > "The data were loaded into AIPS directly from archival science data model (ASDM) format files using the Obit software package (Cotton 2008)." (3.1 JVLA Data)
- **CASA** : ALMA pipeline measurement sets provided  
  > "pipeline calibrated $u$-$v$ data in the form of CASA measurement sets" (3.2 ALMA Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mira A 229 GHz flux density (uniform disk) | 150 | ±30 | mJy | 4 | / 6 (229 GHz) / 0.51 / 46.2$\pm$2.3 (0.03) / 41.5$\pm$2.3 (0.02) / 144$\pm$11 (0.1) / 0.90$\pm$0.07 / 150$\pm$30 (0.04) / 2620$\pm$560 / |
| Mira A 46 GHz flux density | 7.4 | ±1.5 | mJy | 4 | / Q (46 GHz) / 0.76 / 60.0$\pm$2.0 (0.7) / 49.3$\pm$1.6 (0.5) / $156\pm$4 (1) / 0.82$\pm$0.04 / 7.4$\pm$1.5 (0.04) / 2110$\pm$440 / |
| Mira A photospheric radius at 46/96/229 GHz | 3.0 / 2.6 / 2.4 AU | not stated | AU | 4 | 4.5$\times10^{13}$ cm (3.0 AU) at 46 GHz, 3.9$\times10^{13}$ cm (2.6 AU) at 96 GHz, and 3.6$\times10^{13}$ cm (2.4 AU) at 229 GHz |
| Mira B radius from 229 GHz | ≈2.0e13 | not stated | cm | 4 | we derive a radius for Mira B of $\approx2.0\times10^{13}$ cm |
| Mira B 229 GHz flux density | 11.5 | ±2.3 | mJy | 4 | / 6 (229 GHz) / 25.4$\pm$0.6 (0.4) / 23.4$\pm$0.6 (0.4) / 69$\pm$7 (7) / 11.5$\pm$2.3 (0.09) / |
| Disk+Gaussian model hot spot fraction at 229 GHz | 39% of 151 mJy in Gaussian FWHM 26 mas | not stated | mixed | 5 | The total flux density in this model was 151 mJy, with 39% in a Gaussian component with FWHM 26 mas |

## Qualitative findings

- Radio photosphere size decreases with increasing frequency, first observational confirmation for an AGB star  
  > "this is the first time that this has been confirmed observationally for an AGB star" (4.1.1 Mira A)

## Claim tuples

- H: Mira A flux densities follow the RM97 radio photosphere model | E: Measure fluxes at 46, 96, 229 GHz and compare to S∝nu^1.86 at 110 pc | R: Excellent match | F: RM97 model supported and extended to higher frequencies | **supported**
- H: Mira A radio photosphere is resolved, with size decreasing at higher frequency and elongated | E: Uniform elliptical disk fits | R: Radii 3.0, 2.6, 2.4 AU; ellipticity 0.8-0.9 | F: Resolved, frequency-dependent size, flattening 10-20% | **supported**
- H: Mira A surface is uniformly bright | E: Visibility fits and residual images | R: Uniform disk inadequate; disk+Gaussian fits best at 229 GHz | F: Evidence for brightness non-uniformities | **supported**
- H: Mira B emission follows simple free-free spectrum | E: Flux measurement at three frequencies | R: Higher frequencies lie above prior relation | F: More complex model needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Tidal distortion by Mira B insufficient to explain ellipticity (~5e-6)  
  > "This implies an ellipticity $\epsilon\sim5\times10^{-6}$, several orders of magnitude smaller than observed." (5 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Mira A size and PA uncertainties dominated by systematics; disagreements with Vlemmings et al. 2015 in Band 3  
  > "the uncertainties on the source size and position angle reported in this work are dominated by systematic uncertainties" (Appendix)
- Caveat (inferred, ours): Band 3 size and PA conflict with an independent analysis, indicating sensitivity to calibration and phase noise
- Caveat (inferred, ours): Stellar variability and non-simultaneous observations complicate the spectrum
- Caveat (inferred, ours): Disk+Gaussian model is non-unique

## Reproducibility

- Data public (paper): ALMA SV data public  
  > "were released to the public in 2015 February" (2.2 ALMA Data)
- Products in archive: _not stated_
- Missing: AIPS clean parameters
- Missing: JVLA data in archive but program details limited
- Missing: Uv-fit starting values
- Data volume (inferred): ~50-200 GB
- Score (inferred): 3/5, Public ALMA data and clear calibration, but AIPS imaging and fitting details are partial.
- Rediscovery candidate: yes, Public SV data, numeric results in tables, fairly complete recipe for ALMA part.

## Links

- Method: Reid & Menten 1990 (maser-based phase self-calibration)
- Method: Pearson 1999 (uniform disk visibility expressions)
- Companion: Vlemmings et al. 2015 (independent analysis of the same ALMA data)
- Companion: Reid & Menten 2007 (earlier 43 GHz resolved images)
- Related: ALMA Science Verification
- Related: NRAO program 14A-026

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
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 45,
  "rate": 0.634
 },
 "evidence_ok": true
}
```
