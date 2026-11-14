# ALMA Observations of the IRDC Clump G34.43+00.24 MM3: Complex Organic and Deuterated Molecules

`2018ApJ...857...35S` | The Astrophysical Journal 2018 | first author: Sakai, Takeshi | arXiv: 1803.11357 | DOI: 10.3847/1538-4357/aaadfd

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What is the chemical composition (COMs and deuterated molecules) of the hot core/corino in G34.43+00.24 MM3, and does it resemble high-mass hot cores or low-mass hot corinos?  
  > "In this paper, we investigate the nature of the hot core/corino in G34.43+00.24 MM3 from its chemical composition." (1 Introduction)
- Target **G34.43+00.24 MM3 (hot core/corino)**: coordinates phase center RA 18h53m20.4s, Dec +1d28m23.0s (J2000)  
  > "The phase center was (R.A.(J2000), Dec.(J2000)) = (18$^{\rm h}$53$^{\rm m}$20.4$^{\rm s}$, 1$^{\circ}$28$^{\prime}$23.0$^{\prime\prime}$)." (2 OBSERVATIONS); "Kurayama et al. (2011) derived the distance to be 1.56 kpc from VLBI parallax observations." (1 Introduction); "In this paper, we consider both possibilities." (1 Introduction); z/distance 1.56 kpc (near case) or 3.9 kpc (far case); 3.7 kpc for mass  
  > "The phase center was (R.A.(J2000), Dec.(J2000)) = (18$^{\rm h}$53$^{\rm m}$20.4$^{\rm s}$, 1$^{\circ}$28$^{\prime}$23.0$^{\prime\prime}$)." (2 OBSERVATIONS); "Kurayama et al. (2011) derived the distance to be 1.56 kpc from VLBI parallax observations." (1 Introduction); "In this paper, we consider both possibilities." (1 Introduction); distance from 1.56 kpc from VLBI parallax (Kurayama et al. 2011); 3.5-3.9 kpc kinematic/near-IR extinction (Sakai 2008; Sanhueza 2012; Foster 2012)  
  > "The phase center was (R.A.(J2000), Dec.(J2000)) = (18$^{\rm h}$53$^{\rm m}$20.4$^{\rm s}$, 1$^{\circ}$28$^{\prime}$23.0$^{\prime\prime}$)." (2 OBSERVATIONS); "Kurayama et al. (2011) derived the distance to be 1.56 kpc from VLBI parallax observations." (1 Introduction); "In this paper, we consider both possibilities." (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00656.S
- bands: Band 6 and Band 7  
  > "We observed G34.43+00.24 MM3 with ALMA Band 6 and Band 7 in 2012." (2 OBSERVATIONS)
- frequencies and spectral setup: 9 spectral windows (1-7 Band 6, 8-9 Band 7), 234 MHz mode with 61 kHz channels, averaged to 2.44 MHz or 1.464 MHz; 228.8-279.6 GHz  
  > "Although the spectrometers were used with the 234 MHz mode with a 61 kHz channel width, we averaged channels in order to reduce the noise level" (2 OBSERVATIONS); "Frequency ranges for the 9 spectral windows" (Table 1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.8" x 0.6" (0.73-0.89" major axis)  
  > "at the present resolution ($\sim$0$^{\prime\prime}$.8$\times$0$^{\prime\prime}$.6)" (3.1 Spectra & Integrated Intensity Maps)
- max recoverable scale: _not stated_
- sensitivity: rms 1.7-4.3 mJy/beam per 1.464 MHz channel  
  > "The rms noise level is derived from the channels free of emission in the cube with the channel width of 1.464 MHz." (Table 1)
- time on source: _not stated_
- observing dates: 2012  
  > "We observed G34.43+00.24 MM3 with ALMA Band 6 and Band 7 in 2012." (2 OBSERVATIONS)
- pi or archival as stated: _not stated_
- Line: CH3OH 10_2-9_3 A- (231.28110 GHz)
- Line: D2CO 4(0,4)-3(0,3) (231.41023 GHz)
- Line: DNC 3-2 (228.91049 GHz)
- Line: NH2CHO 12(1,11)-11(1,10) (261.32745 GHz)
- External data: Average COM/CH3OH abundances for hot corinos and high-mass hot cores  
  > "Taquet et al. (2015) derived the averaged values of the abundances of several COMs relative to CH$_3$OH for hot corinos" (4.1.1 Comparison with the Other Sources) [from Taquet et al. 2015 (ref: Taq15)]
- External data: COM abundances in G34.26+0.15 SE  
  > "are comparable to those of G34.26+0.15 SE (Mookerjea et al. 2007) within the 1 sigma error" (4.1.1 Comparison with the Other Sources) [from Mookerjea et al. 2007 (ref: moo07)]
- External data: D2CO/CH3OH in IRAS 16293-2422 B (8e-4); CH3OH data from Jørgensen et al. 2016  
  > "the D$_2$CO/CH$_3$OH ratio is found to be 8$_{-2.5}^{+2}$$\times$10$^{-4}$ (the CH$_3$OH data is taken from Jørgensen et al. 2016)" (4.2.1 Comparison with the Other Sources) [from Persson et al. 2018 (ref: per18)]
- External data: Partition functions from JPL/CDMS; line parameters from CDMS/JPL  
  > "The partition function $Q$ is evaluated from the data in JPL or CDMS." (Derivation of Column density) [from CDMS, JPL catalogs]

## Processing

### Calibration

- pipeline or manual: Data reduced with CASA; no further detail  
  > "The data were reduced by the CASA software package." (2 OBSERVATIONS)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: not applied  
  > "Self-calibration is not applied." (2 OBSERVATIONS)

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
- smoothing: Channels averaged: 40 channels (2.44 MHz, 3.2 km/s) for Figure 2; 24 channels (1.464 MHz, 1.92 km/s) for Figure 3  
  > "40 channels (channel width of 2.44 MHz, corresponding to 3.2 km s$^{-1}$ at 230 GHz) for the data presented in Figure 2" (2 OBSERVATIONS)
- final beam: 0.73-0.89" x 0.49-0.64" depending on window (Table 1)  
  > "| 1 | 228.793–289.025 | 0.85$^{\prime\prime}$$\times$0.64$^{\prime\prime}$ | -72 | 1.7 |" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Observations and part of the data were previously presented; details of observations given there  
  > "The data used in this paper are a part of the same observations presented in Sakai et al. (2013), Yanagida et al. (2014), and Sakai et al. (2015)." (2 OBSERVATIONS) [from Sakai et al. (2013), Yanagida et al. (2014), Sakai et al. (2015)]
- Rotation diagram method  
  > "we apply the rotation diagram method (Turner 1991; Goldsmith & Langer 1999)" (3.3 Column Densities) [from Turner 1991; Goldsmith & Langer 1999]

### Not stated but needed to reproduce (our reading)

- Calibrators, CASA version, and imaging parameters (weighting/robust, cell, deconvolver, masks) not given
- Continuum subtraction method and line-free channels not stated
- Array configuration, baselines, time on source, max recoverable scale not stated
- Which brightest line per molecule was used for column density and spectra extraction aperture (single pixel vs beam)
- Rotation diagram fit details (weights, treatment of blended lines, beam dilution)
- RADEX collision partner data and kinetic temperature
- Flux calibration uncertainty not included

## Analysis recipe

1. **Image cubes and integrated intensity maps**: Average channels, integrate over ±5 km/s about 59.7 km/s (wider for blended lines)  
  > "the velocity range for the integration is $\pm$5 km s$^{-1}$ centered at the LSR velocity of 59.7 km s$^{-1}$" (3.1 Spectra & Integrated Intensity Maps)
   - software: CASA
   - parameter: Blended lines: -5 km/s of lowest to +5 km/s of highest velocity line  
  > "the velocity range for the integration is set from -5 km s$^{-1}$ of the lowest velocity line to +5 km s$^{-1}$ of the highest velocity line." (3.1 Spectra & Integrated Intensity Maps)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure emission sizes**: 2D Gaussian fit to integrated intensity maps, with deconvolution  
  > "We fit a 2D Gaussian to the integrated intensity maps of the COMs emission near G34.43 MM3 HC in Figure 1" (3.1 Spectra & Integrated Intensity Maps)
   - software: CASA imview
   - fitting: Gaussian fitting task in imview  
  > "using the Gaussian fitting task in $imview$ of the CASA software package" (3.1 Spectra & Integrated Intensity Maps)
   - validation: _not stated_
3. **Rotation temperature from CH3OH rotation diagram**: Rotation diagram of CH3OH lines; exclude optically thick lines (tau>1 from RADEX) and the maser line  
  > "Hence, we exclude those lines (black circles in Figure 5) for the temperature estimate using the rotation diagram method." (3.3 Column Densities)
   - software: RADEX
   - parameter: RADEX: density 1e7 cm-3, column density 1e17 cm-2, velocity width 5 km/s  
  > "When we set the density of 10$^7$ cm$^{-3}$, the column density of 10$^{17}$ cm$^{-2}$ and the velocity width of 5 km s$^{-1}$" (3.3 Column Densities)
   - assumption: LTE  
  > "assuming the local thermodynamic equilibrium (LTE) condition" (3.3 Column Densities)
   - fitting: Linear fit of rotation diagram  
  > "we fit the data to the following equation;" (3.3 Column Densities)
   - validation: _not stated_
4. **Column densities of all molecules**: LTE optically thin column density from brightest line integrated intensity at T=110 K; Q(T)=a T^b fitted to JPL/CDMS  
  > "We use this temperature for the derivation of the column density of all the observed molecules, including CH$_3$OH." (3.3 Column Densities)
   - assumption: LTE, optically thin  
  > "We derive the column density assuming LTE and optically thin emission." (Derivation of Column density)
   - fitting: _not stated_
   - validation: Errors include Trot uncertainty and 1 sigma rms of integrated intensity  
  > "The errors in Table 4 include the uncertainty of the excitation temperature and the 1 sigma rms noise level of the integrated intensity." (3.3 Column Densities)
5. **Compare abundances relative to CH3OH with other sources**: Compare X(CH3OH) ratios with hot corinos and high-mass hot cores from literature  
  > "we use the abundances relative to CH$_3$OH, because CH$_3$OH is thought to be the parent species" (4.1.1 Comparison with the Other Sources)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data reduction and 2D Gaussian fitting (imview)  
  > "The data were reduced by the CASA software package." (2 OBSERVATIONS)
- **RADEX** : Estimating line optical depths  
  > "We estimate the optical depth of each line by using the RADEX code (van der Tak et al. 2007)." (3.3 Column Densities)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3OH rotation temperature | 110 | +30/-20 | K | 3 | the rotation temperature is derived to be 110$_{-20}^{+30}$ K |
| CH3OH column density | 3.9e16 | +3.6/-1.8 e16 | cm-2 | 4 | / CH$_3$OH / 3.9$_{-1.8}^{+3.6}\times 10^{16}$ / — / |
| CH3CH2CN/CH3OH | 0.0094 | +0.011/-0.0051 | dimensionless | 4 | / CH$_3$CH$_2$CN / 3.7$_{-0.5}^{+0.8}\times 10^{14}$ / 0.0094$_{-0.0051}^{+0.011}$ / |
| D2CO/CH3OH | 1.5e-3 | +3.1/-1.0 e-3 | dimensionless | 4 | The D$_2$CO/CH$_3$OH ratio of G34.43 MM3 HC is evaluated to be 1.5$_{-1.0}^{+3.1}$$\times$10$^{-3}$ |
| Keplerian stellar mass upper estimate | 11 (1.56 kpc), 27 (3.9 kpc) | not stated | Msun | 0 | the stellar mass is roughly estimated to be about 11 $M_{\odot}$ and 27 $M_{\odot}$ for the distance of 1.56 kpc and 3.9 kpc |

## Qualitative findings

- Only CH3OH detected toward shocked regions; COMs not shock-originated  
  > "None of these lines, except for CH$_3$OH, are detected toward the shocked regions in our data, which suggests that COMs do not originate in shocks." (abstract)
- DNC emission is offset from the hot core, likely tracing the envelope  
  > "the DNC emission is likely to trace the envelope." (3.2 Velocity Structures)

## Claim tuples

- H: Is the COM chemistry of G34.43 MM3 HC like high-mass hot cores or low-mass hot corinos? | E: Derive COM column densities relative to CH3OH and compare with Taquet et al. (2015) averages | R: CH3CH2CN, HCOOCH3, CH3OCH3 relative to CH3OH similar to high-mass hot cores; CH3CH2CN/CH3OH ~10x higher than low-mass | F: Warm-up phase conditions similar to high-mass sources | **supported**
- H: Is the D2CO abundance anomalous? | E: Compare D2CO/CH3OH with other hot cores and hot corinos | R: 1.5e-3, higher than NGC7129 FIR 2 and comparable to hot corino IRAS 16293 B | F: Implies young core and possibly long cold starless phase | **partially**
- H: Do COMs originate in shocks? | E: Check COM line detections toward shocked outflow-interaction region | R: No COM lines except CH3OH detected there | F: COMs do not originate in shocks | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Abundances relative to CH3OH used because CH3OH is the parent species of COMs  
  > "we use the abundances relative to CH$_3$OH, because CH$_3$OH is thought to be the parent species in the synthesis of more complex organic molecules" (4.1.1 Comparison with the Other Sources)
- How they decided it was enough: _not stated_
- Limitation (authors): Distance is uncertain; resolution too low to resolve internal structure or confirm rotation  
  > "Thus, the distance to this object is not well defined." (1 Introduction); "In order to fully confirm the rotation motion, we need higher angular resolution observations." (3.2 Velocity Structures)
- Caveat (inferred, ours): Single-temperature LTE at 110 K applied to all molecules; large errors
- Caveat (inferred, ours): Blended lines and unresolved source size (beam dilution) not corrected
- Caveat (inferred, ours): Scatter in rotation diagram; distance ambiguity affects interpretations
- Caveat (inferred, ours): D2CO/CH3OH comparisons mix single-dish and interferometric data at different resolutions

## Reproducibility

- Data public (paper): ALMA data from project 2011.0.00656.S acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00656.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters and CASA version
- Missing: Continuum subtraction details
- Missing: Exact line integrated intensities extraction apertures
- Missing: Array configuration details
- Data volume (inferred): ~20-50 GB (Cycle 0 Band 6/7 raw data)
- Score (inferred): 3/5, Data public and equations given, but imaging/calibration parameters are largely not stated and the data are Cycle 0.
- Rediscovery candidate: no, Imaging and extraction recipe incomplete; the results rely on prior-paper details.

## Links

- Method: Sakai et al. 2013, ApJL 775, L31 (Original observations and processing of the same data)
- Companion: Yanagida et al. 2014, ApJL 794, L10 (Same data: CH3OH masers and outflow)
- Companion: Sakai et al. 2015, ApJ 803, 70 (Same data: DNC/N2H+ and chemical modeling)

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 38,
  "rate": 0.521
 },
 "evidence_ok": true
}
```
