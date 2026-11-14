# A Keplerian Disk around Orion SrCI, a ∼ 15 M <SUB>☉</SUB> YSO

`2018ApJ...860..119G` | The Astrophysical Journal 2018 | first author: Ginsburg, Adam | arXiv: 1804.10622 | DOI: 10.3847/1538-4357/aac205

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What is the mass of the massive protostar Orion SrcI, as measured from the Keplerian rotation of its disk, and is it high enough to support the dynamical decay scenario?  
  > "We present new measurements of SrcI’s mass, finding it has $M_I \sim 15$ $M_{\odot}$." (Introduction)
- Target **Orion Source I (SrcI)**: coordinates offsets from ICRS 5h35m14s -5d22m30s  
  > "despite its relative proximity at a mere $\approx415$ pc from the sun (cite: Menten2007a; Kim2008a)" (Introduction); "The pointlike source position is given as RA seconds and Dec arcseconds offset from ICRS 5h35m14s -5d22m30s." (Table 4); z/distance ≈415 pc  
  > "despite its relative proximity at a mere $\approx415$ pc from the sun (cite: Menten2007a; Kim2008a)" (Introduction); "The pointlike source position is given as RA seconds and Dec arcseconds offset from ICRS 5h35m14s -5d22m30s." (Table 4); distance from Menten2007a; Kim2008a  
  > "despite its relative proximity at a mere $\approx415$ pc from the sun (cite: Menten2007a; Kim2008a)" (Introduction); "The pointlike source position is given as RA seconds and Dec arcseconds offset from ICRS 5h35m14s -5d22m30s." (Table 4)

## Data provenance

- ALMA projects: 2016.1.00165.S
- bands: Band 3, 6 (Band 7 not discussed)  
  > "Band 7 data are not discussed in this work because the data for the long-baseline observations were not delivered by the time of submission" (Observations)
- frequencies and spectral setup: 4 SPWs per band, 1.8 GHz wide (B3 85.5-101.2 GHz; B6 214.3-233.7 GHz)  
  > "| B6 | 0 | 229.168-231.042 | -2 | 0.026 | 0.022 | 64.0 | 2.8 | 115.9 | 1.3 |" (Table 3)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: long-baseline B6 up to 12147 m; B3 up to 14854 m  
  > "| 25-Sep-2017 | 3 | 12m | 5180 | 41-14854 | 42 | J0423-0120 | J0541-0541 |" (Table 1)
- angular resolution: 0.03-0.06 arcsec (12-24 AU) at 1.3 and 3.2 mm  
  > "with resolution 0.03-0.06(12-24 AU) at 1.3 and 3.2 mm" (abstract)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.087 mJy/beam (B6), 0.038 mJy/beam (B3), robust -2  
  > "| B6 | -2 | 0.037 | 0.022 | 67.0 | 30.3 | 0.087 | 19.638 | 220 |" (Table 2)
- time on source: _not stated_
- observing dates: 8 Oct 2016 to 25 Sep 2017  
  > "| 19-Sep-2017 | 6 | 12m | 5556 | 41-12147 | 42 | J0522-3627 | J0541-0541 |" (Table 1)
- pi or archival as stated: _not stated_
- Line: H2O 5_5,0-6_4,3 (232.68670 GHz)
- Line: SiO v=0,1 J=5-4 and J=2-1 (28SiO, 29SiO) (not stated)
- External data: 7 mm VLA continuum data fitted with the same model  
  > "We also display fits to the (cite: Reid2007a) 7 mm continuum data with the same model" (Continuum) [from (cite: Reid2007a)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: ALMA QA2 calibrated data imaged directly  
  > "The calibrated data delivered from the ALMA QA2 process were imaged directly" (Observations)
- flux calibrator: J0522-3627 (B6), J0423-0120 (B3)  
  > "| 24-Sep-2017 | 3 | 12m | 5146 | 21-12147 | 41 | J0423-0120 | J0541-0541 |" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: not applied; did not improve the image  
  > "we found that self-calibration did not improve the image" (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust -2 (continuum, disk fitting); cubes robust 0.5 and -2  
  > "Cubes were produced centered on SrcI with robust 0.5 and -2 weightings." (Observations)
- uv taper: baselines >150 m (115 kλ) only for robust -2 images used for disk fitting  
  > "we used data only from baselines $>150$ m (115 k$\lambda$, angular scales $<1.8$) in the robust -2 images" (Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: cubes cleaned only in 0.5"x0.5" region around SrcI  
  > "These cubes were only cleaned in the $0.5\arcsec\times0.5$ region immediately surrounding SrcI" (Observations)
- multiscale scales: _not stated_
- continuum subtraction: median across 1.8 GHz bandwidth in each SPW  
  > "Continuum-subtracted cubes were produced by subtracting the median across the 1.8 GHz bandwidth in each spectral window." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: multiconfiguration data combined  
  > "The multiconfiguration data were combined for all images considered here." (Observations)
- smoothing: _not stated_
- final beam: B6 0.037x0.022 arcsec PA 67; B3 0.065x0.041 PA 50.9 (robust -2)  
  > "| B3 | -2 | 0.065 | 0.041 | 50.9 | 53.2 | 0.038 | 14.179 | 370 |" (Table 2)
- final rms: _not stated_

### Inherited from earlier work

- PV outer-envelope method with 5-sigma threshold  
  > "Following (cite: Seifried2016a), we measure the outer edge of the detected emission in a position-velocity (PV) diagram" (3.5 Kinematics) [from (cite: Seifried2016a)]
- edge-on uniform optically thin disk model for centroid fits  
  > "This model approach is the same used by (cite: Plambeck2016a)." (Appendix 10) [from (cite: Plambeck2016a)]

### Not stated but needed to reproduce (our reading)

- CLEAN thresholds, niter, cell and image sizes, tclean parameters
- CASA version used
- Line-free channels / how median continuum was handled
- Pipeline vs manual calibration details and flux scale uncertainty
- Exact PV slice width and position angle for the envelope extraction
- How noise sigma was defined for the 5-sigma envelope threshold
- Initial values and bounds for the lmfit continuum fits
- Rest frequency for U232.511 used in stacking

## Analysis recipe

1. **Image continuum and cubes**: Imaged QA2-calibrated multiconfiguration data at several robust values; cubes continuum-subtracted by median per SPW  
  > "Continuum images were produced with several weighting parameters to emphasize different scales" (Observations)
   - software: CASA, spectral-cube
   - parameter: robust -2 and baselines >150 m for disk fitting  
  > "we used data only from baselines $>150$ m (115 k$\lambda$, angular scales $<1.8$) in the robust -2 images" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit continuum disk and compact source**: Thin edge-on linear disk model plus 2D Gaussian smoothing, plus smeared point source along disk  
  > "We used a linear model (i.e., an infinitely thin perfectly edge-on disk) for the disk, with endpoints and amplitude as free parameters." (Continuum)
   - software: lmfit
   - fitting: Levenberg-Marquardt least squares  
  > "The optimization was performed using a Levenberg-Marquardt fitter (cite: Newville2014a)." (Continuum)
   - validation: residual images shown in appendix  
  > "The models and their residuals are shown in Appendix [6](#appendix:contmodel)." (Continuum)
3. **Measure Keplerian mass from PV outer envelope**: Follow emission outer edge in PV diagram down to 5-sigma and compare with edge-on Keplerian curves  
  > "We use a threshold of 5-$\sigma$, as was done in (cite: Seifried2016a)" (3.5 Kinematics)
   - software: spectral-cube
   - parameter: 5-sigma threshold  
  > "We use a threshold of 5-$\sigma$" (3.5 Kinematics)
   - assumption: edge-on disk, point-like gravitational potential  
  > "We find that a 15 $M_{\odot}$ edge-on Keplerian rotation curve fits" (3.5 Kinematics)
   - fitting: by-eye comparison; no formal best fit  
  > "We do not report best-fit parameters and statistical errors here" (3.5 Kinematics)
   - validation: threshold variation gives ~2 Msun uncertainty; power-law alternatives tested  
  > "These figures suggest that our measurement uncertainty with the PV envelope fitting technique is approximately 2 $M_{\odot}$." (3.5.2)
4. **Centroid-of-velocity mass comparison**: Fit 2D Gaussians to blobs per channel, fit edge-on optically thin ring model with free mass, inner/outer radius, centroid velocity  
  > "The mass, inner and outer radius, and centroid velocity were left as free parameters." (Appendix 10)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **spectral-cube** : cube analysis  
  > "All cube analysis was performed using `spectral-cube`" (Observations)
- **CASA** : listed among tools  
  > "and `CASA` (cite: McMullin2007a)" (Software)
- **lmfit** : continuum model fitting  
  > "The optimization was performed using a Levenberg-Marquardt fitter (cite: Newville2014a)." (Continuum)
- **astroquery** : Splatalogue line searches  
  > "for known lines in the Splatalogue collection of line catalogs using `astroquery`" (Appendix 9)
- **radio-beam** : listed tool  
  > "`radio-beam` (<https://github.com/radio-astro-tools/radio-beam>" (Software)
- **astropy** : listed tool  
  > "`astropy` (cite: Astropy-Collaboration2013a)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SrcI central mass | 15 | ±2 | Msun | 3 | which gives a mass $M_I\approx15\pm2$ $M_{\odot}$ |
| Disk vertical FWHM | about 20 | not stated | AU | 2 | with a vertical FWHM height of about 20 AU and a length of about 100 AU |
| Peak H2O brightness temperature | ~1500 | ±100 | K | 0 | it has a peak brightness temperature $\sim1500\pm100$ K |
| Required luminosity for 500 K surface at 50 AU | 6500 | not stated | Lsun | 0 | the required central source luminosity is 6500 $L_{\odot}$ |
| Compact source spectral index 3.2-1.3 mm | 1.1 | not stated | dimensionless | 2 | ($\alpha\approx1.1$) |
| Compact source offset from disk center | 5.8 | ±1.5 | AU | 2 | slightly offset from the center of the disk by $5.8\pm1.5$ AU in projection |
| Best-fit power-law slope of H2O envelope | ≈0.4 | not stated | dimensionless | 3 | the best-fit profile of $\alpha\approx0.4$ is slightly shallower than the Keplerian $\alpha=0.5$ curve |

## Qualitative findings

- H2O 5_5,0-6_4,3 line is thermal, not masing, and traces disk and inner outflow  
  > "The H$_{2}$O$5_{5,0}-6_{4,3}$ line is not masing and kinematically traces both the upper envelope of the disk and the lower portion of the outflow." (Conclusions)

## Claim tuples

- H: Is SrcI a ~15 Msun object rather than 5-10 Msun? | E: PV outer-envelope fit of H2O line with Keplerian curves | R: 15 Msun edge-on Keplerian fits the envelope; lower masses leave emission outside curve | F: M=15±2 Msun | **supported**
- H: Does the central compact source indicate a hot inner disk/binary? | E: Fit smeared point source to continuum residuals at 1.3 and 3.2 mm | R: Marginally resolved, offset 5.8±1.5 AU, shallow SED | F: Likely hot inner disk region, possibly binary | **partially**
- H: Is the dynamical decay scenario viable? | E: Compare measured mass to required mass | R: M>~15 Msun | F: Scenario remains viable | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Outer-envelope PV fitting resolves disk with high resolution; centroid method used for comparison with earlier works  
  > "to facilitate direct comparison with previous works, we use the centroid-of-velocity-channel approach in Appendix [10]" (3.5 Kinematics)
- Alternative: Power-law alpha=1 rejected; turbulence could lower mass 20-30%  
  > "a power law $\alpha=1$ (cite: Aso2017b) is inconsistent with the data" (3.5.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass error is range of consistent models, not statistical 1-sigma  
  > "the error bar represents the range of consistent models rather than a typical $1-\sigma$ statistical uncertainty" (Conclusions)
- Caveat (inferred, ours): Mass depends on by-eye envelope fit with subjective threshold
- Caveat (inferred, ours): H2O also traces outflow, possible contamination
- Caveat (inferred, ours): No inclination fit; edge-on assumed
- Caveat (inferred, ours): Unidentified lines limit chemistry/excitation constraints

## Reproducibility

- Data public (paper): Cutouts and scripts on Zenodo/GitHub  
  > "Cutouts of the data used for the analysis in this work along with the software and scripts used for the analysis are presented at <https://zenodo.org/record/1213350>." (Observations)
- Products in archive: _not stated_
- Code: GitHub keflavich/Orion_ALMA_2016.1.00165.S, hash 68a49ad  
  > "The software used to make this version of the paper is available from github at <https://github.com/keflavich/Orion_ALMA_2016.1.00165.S>" (Software)
- Missing: tclean parameters and CASA version
- Missing: Exact envelope extraction parameters
- Data volume (inferred): ~100s of GB raw for long-baseline Band 3/6 data; cutouts much smaller
- Score (inferred): 3/5, Code and cutouts released, but main mass is a by-eye envelope fit and imaging details are missing.
- Rediscovery candidate: no, Main mass result is by-eye envelope comparison with incomplete imaging recipe.

## Links

- Method: (cite: Seifried2016a) (PV outer-envelope method)
- Method: (cite: Plambeck2016a) (centroid/edge-on disk model)
- Companion: (cite: Hirota2017b) (Si18O observations of SrcI)

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
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
  "facts": 71,
  "stated": 45,
  "rate": 0.634
 },
 "evidence_ok": true
}
```
