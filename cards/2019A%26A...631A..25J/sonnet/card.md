# ALMA observations of water deuteration: a physical diagnostic of the formation of protostars

`2019A&A...631A..25J` | Astronomy and Astrophysics 2019 | first author: Jensen, S. S. | arXiv: 1909.10533 | DOI: 10.1051/0004-6361/201936012

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, star_formation
- Question: What is the HDO/H2O ratio in the inner warm gas of three isolated Class 0 protostars, and does it differ from clustered protostars?  
  > "The aim is to determine the HDO/H$_2$O ratio in the inner warm gas toward three low-mass Class 0 protostars selected to be in isolated cores" (abstract)
- Target **L483**: coordinates 18:17:29.9 -04:39:39.6 (J2000)  
  > "For L483 the observations were centered on $\alpha_{\mathrm{J}2000}$=18:17:29.9, $\delta_{\mathrm{J}2000}$=–04:39:39.6" (2 Observations); "We assume a distance of $200$ pc in this paper." (Introduction); z/distance 200 pc  
  > "For L483 the observations were centered on $\alpha_{\mathrm{J}2000}$=18:17:29.9, $\delta_{\mathrm{J}2000}$=–04:39:39.6" (2 Observations); "We assume a distance of $200$ pc in this paper." (Introduction); distance from assumed; Jacobsen et al. 2019 (200-250 pc)  
  > "For L483 the observations were centered on $\alpha_{\mathrm{J}2000}$=18:17:29.9, $\delta_{\mathrm{J}2000}$=–04:39:39.6" (2 Observations); "We assume a distance of $200$ pc in this paper." (Introduction)
- Target **BHR71–IRS1**: coordinates 12:01:36.5 -65:08:49.3 (J2000)  
  > "for BHR71–IRS1 $\alpha_{\mathrm{J}2000}$=12:01:36.5, $\delta_{\mathrm{J}2000}$=–65:08:49.3" (2 Observations); "It is part of a wide binary system, with the companion located at 3200 au at a distance $d\approx200$ pc." (Introduction); z/distance ~200 pc  
  > "for BHR71–IRS1 $\alpha_{\mathrm{J}2000}$=12:01:36.5, $\delta_{\mathrm{J}2000}$=–65:08:49.3" (2 Observations); "It is part of a wide binary system, with the companion located at 3200 au at a distance $d\approx200$ pc." (Introduction); distance from _not stated_
- Target **B335**: coordinates 19:37:00.9 +07:34:09.6 (J2000)  
  > "for B335 $\alpha_{\mathrm{J}2000}$=19:37:00.9, $\delta_{\mathrm{J}2000}$=07:34:09.6" (2 Observations); "B335 is a Bok globule located at $d\approx100$ pc (cite: olofsson2009)" (Introduction); z/distance ~100 pc  
  > "for B335 $\alpha_{\mathrm{J}2000}$=19:37:00.9, $\delta_{\mathrm{J}2000}$=07:34:09.6" (2 Observations); "B335 is a Bok globule located at $d\approx100$ pc (cite: olofsson2009)" (Introduction); distance from Olofsson & Olofsson 2009  
  > "for B335 $\alpha_{\mathrm{J}2000}$=19:37:00.9, $\delta_{\mathrm{J}2000}$=07:34:09.6" (2 Observations); "B335 is a Bok globule located at $d\approx100$ pc (cite: olofsson2009)" (Introduction)

## Data provenance

- ALMA projects: 2017.1.00693.S
- bands: Band 6 (HDO) and Band 5 (H2 18O)  
  > "Another spectral setup targeted the H$_{2}^{18}$O $3_{1,3}$–$2_{2,0}$ transition at 203.4075 GHz in Band 5." (2 Observations)
- frequencies and spectral setup: 1920 channels per spectral window, 122 kHz (0.11 km/s) width  
  > "Each spectral window contains 1920 channels with a width of 122 kHz (0.11 km s$^{-1}$)." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: max baselines 677-1797 m  
  > "| BHR71–IRS1 | 2017 January 15 | J1147$-$6753 | J0904$-$5735 | 1797 | 46 | 6 |" (Table 1)
- angular resolution: HDO beams 0.4"x0.3" to 0.7"x0.5"; H2 18O 0.8"x0.5" to 1.2"x1.0"  
  > "The synthesized beam size range from $0.4\ensuremath{''}\times0.3\ensuremath{''}$ to $0.7\ensuremath{''}\times0.5\ensuremath{''}$ for the HDO spectral windows" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2017 Jan-Sep (Table 1)  
  > "| L483 | 2017 March 11 | J1743$-$0350 | J1751+0939 | 1100 | 42 | 6 |" (Table 1)
- pi or archival as stated: _not stated_
- Line: HDO 3(1,2)-2(2,1) (225.8967 GHz)
- Line: HDO 2(1,1)-2(1,2) (241.5616 GHz)
- Line: H2 18O 3(1,3)-2(2,0) (203.4075 GHz)
- External data: HDO/H2O ratios of clustered protostars and comets for comparison  
  > "| NGC1333 IRAS 2A | $7.4\pm2.1$ | HDO, H$_{2}^{18}$O | 14 |" (Table 3) [from Persson et al. 2014 (cite: persson2014)]
- External data: 16O/18O = 560  
  > "assuming the Galactic oxygen isotope ratio of $^{16}$O/$^{18}$O$= 560$ (cite: wilson1994)" (4.1) [from Wilson & Rood 1994 (cite: wilson1994)]

## Processing

### Calibration

- pipeline or manual: pipeline calibration, then phase self-calibration on continuum channels (L483 pipeline product used)  
  > "Each dataset was pipeline-calibrated using casa 5.1 (cite: casa). Phase self-calibration was performed using continuum channels for each dataset with casa 5.4." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% flux calibration uncertainty  
  > "with an additional 10% uncertainty on the flux calibration" (4.1)
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "The images were deconvolved using the tclean algorithm with a robust parameter of $-0.5$." (2 Observations)
- deconvolver: _not stated_
- weighting robust: robust = -0.5  
  > "The images were deconvolved using the tclean algorithm with a robust parameter of $-0.5$." (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: casa uvcontsub for self-calibrated sources  
  > "For the self-calibrated sources we performed continuum subtraction using casa uvcontsub before inversion." (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: HDO cubes convolved with gaussian kernel (imsmooth) to the H2 18O beam  
  > "the image cube is convolved with a gaussian kernel using the imsmooth function in casa" (3 Results)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Optically thin LTE with Tex = 124 K, same method as earlier work  
  > "who determined the water deuteration in the hot corino toward a number of sources using the same method and excitation temperature." (4.1) [from Persson et al. 2014 (cite: persson2014); Coutens et al. 2014 (cite: coutens2014)]

### Not stated but needed to reproduce (our reading)

- Line-free channels for uvcontsub
- Image size, cell size, masking, deconvolution threshold
- Self-calibration solution intervals
- Integration windows and spectral extraction aperture details
- HDO/H2 18O partition functions and spectroscopic constants used
- Final rms values per cube

## Analysis recipe

1. **Calibrate and image**: Pipeline calibration, phase self-cal, uvcontsub, tclean  
  > "Each dataset was pipeline-calibrated using casa 5.1 (cite: casa)." (2 Observations)
   - software: CASA
   - parameter: robust = -0.5  
  > "The images were deconvolved using the tclean algorithm with a robust parameter of $-0.5$." (2 Observations)
   - fitting: _not stated_
   - validation: Continuum compared with Imai et al. 2016 for B335  
  > "we see good agreement: the 10$\sigma$ contours (3 mJy beam$^{-1}$) appear almost identical." (3 Results)
2. **Extract and fit line spectra**: Spectra at continuum peak after beam-matching; Gaussian fits (two for L483); CH3OCH3 blend subtracted for BHR71  
  > "Each spectrum is extracted toward the 202.7 GHz continuum peak of the source" (3 Results)
   - software: CASA
   - fitting: Gaussian profiles  
  > "Toward B335 and BHR71–IRS1 the emission lines are fitted using a single gaussian profile." (3 Results)
   - validation: Moment 1 maps and 2D Gaussian size fits confirm hot corino origin  
  > "This is confirmed by fitting two-dimensional gaussian profiles to the emission maps." (3 Results)
3. **Derive column densities and HDO/H2O**: Optically thin LTE, Tex=124 K; H2O from H2 18O with 16O/18O=560; HDO weighted average of two lines  
  > "We estimated the column densities of HDO and H$_{2}^{18}$O considering optically thin emission and local thermodynamic equilibrium (LTE) with an excitation temperature of 124 K." (4.1)
   - parameter: Tex = 124 K  
  > "with an excitation temperature of 124 K" (4.1)
   - assumption: 16O/18O = 560  
  > "assuming the Galactic oxygen isotope ratio of $^{16}$O/$^{18}$O$= 560$ (cite: wilson1994)" (4.1)
   - fitting: _not stated_
   - validation: Tex varied 30-300 K; Tex from two HDO lines (127, 174, 103 K) consistent with 124 K  
  > "The excitation temperatures are 127$\pm24$ K, 174$\pm59$ K, and 103$\pm$21 K for L483, B335, and BHR71–IRS1" (4.1)

## Software

- **CASA** 5.1 (pipeline), 5.4 (self-cal): calibration, self-calibration, uvcontsub, tclean, imsmooth, moment maps  
  > "Phase self-calibration was performed using continuum channels for each dataset with casa 5.4." (2 Observations)
- **Splatalogue** : line identification via JPL and CDMS  
  > "All querying was done through the Splatalogue interface" (3 Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HDO/H2O L483 | 2.2e-3 | 0.4e-3 | dimensionless | 3 | The estimated HDO/H$_2$O ratios for L483, B335, and BHR71–IRS1 are ($2.2\pm0.4$)$\times 10^{-3}$, ($1.7\pm0.3$)$\times 10^{-3}$, and ($1.8\pm0.4$)$\times 10^{-3}$ |
| HDO/H2O B335 | 1.7e-3 | 0.3e-3 | dimensionless | 3 | ($2.2\pm0.4$)$\times 10^{-3}$, ($1.7\pm0.3$)$\times 10^{-3}$, and ($1.8\pm0.4$)$\times 10^{-3}$, respectively |
| HDO/H2O BHR71-IRS1 | 1.8e-3 | 0.4e-3 | dimensionless | 3 | ($2.2\pm0.4$)$\times 10^{-3}$, ($1.7\pm0.3$)$\times 10^{-3}$, and ($1.8\pm0.4$)$\times 10^{-3}$, respectively |
| HDO excitation temperatures (L483, B335, BHR71-IRS1) | 127, 174, 103 | 24, 59, 21 | K | 3 | The excitation temperatures are 127$\pm24$ K, 174$\pm59$ K, and 103$\pm$21 K for L483, B335, and BHR71–IRS1 |

## Qualitative findings

- Isolated protostars show HDO/H2O a factor of ~2 higher than clustered ones; results favor inheritance of water  
  > "the results presented here favor the inheritance scenario, at least at the earliest protostellar phase" (4.2)

## Claim tuples

- H: Isolated protostars have different water deuteration than clustered ones | E: ALMA HDO and H2 18O observations of three isolated Class 0 sources compared with four clustered ones | R: (1.7-2.2)e-3 vs (5.5-9.2)e-4 | F: Local cloud environment influences water deuteration | **supported**
- H: Result is robust to assumed Tex | E: Varied Tex 30-300 K and computed Tex from two HDO lines | R: Tex<=60-70 K needed to match clustered values, inconsistent with measured Tex | F: Conclusions unaffected | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Same LTE method as earlier work for direct comparison  
  > "Choosing the same methodology, we can directly compare the water deuteration under similar assumptions." (4.1)
- Alternative: Advanced radiative transfer modelling not used because source-parameter uncertainties diminish its advantage  
  > "Attempting more advanced modelling may thus offer little improvement over the LTE approach" (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): LTE may be invalid if inner envelope densities are lower in isolated sources  
  > "then the emission from the water isotopologs could be sub-thermal and the LTE approximation invalid" (4.1)
- Caveat (inferred, ours): Only three isolated sources and four clustered comparison sources
- Caveat (inferred, ours): Optically thin LTE with fixed Tex; no radiative transfer
- Caveat (inferred, ours): Unresolved emission; beam dilution and source size not corrected
- Caveat (inferred, ours): Distances partly uncertain (L483)

## Reproducibility

- Data public (paper): ALMA Cycle 5 project 2017.1.00693.S cited  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00693.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Line-free channels
- Missing: Imaging grid and masks
- Missing: Self-cal parameters
- Missing: Spectroscopic constants/partition functions
- Data volume (inferred): ~100-300 GB raw
- Score (inferred): 3/5, Public data and simple LTE recipe, but imaging and extraction details are sparse.
- Rediscovery candidate: yes, Data public, simple LTE analysis, numeric ratios to compare.

## Links

- Method: Persson et al. 2014 (cite: persson2014) (LTE method and Tex = 124 K)
- Companion: Jacobsen et al. 2019 (cite: jacobsen2018) (L483 hot corino kinematics)

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
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 40,
  "rate": 0.58
 },
 "evidence_ok": true
}
```
