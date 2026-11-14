# The Physical and Chemical Properties of the ρ Ophiuchi A Dense Core

`2018ApJ...868...80C` | The Astrophysical Journal 2018 | first author: Chen, Yu-Ching | arXiv: 1810.08226 | DOI: 10.3847/1538-4357/aae9e4

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, astrochemistry
- Question: What are the physical and chemical properties (small-scale condensations, heating, CO and N2H+ depletion, kinematics) of the rho-Oph A dense core, using SMA data combined with single-dish data?  
  > "In this paper, we present the 1.3 mm continuum and C$^{18}$O (2–1) images obtained with the combination of the SMA and the single-dish data." (Introduction)
- Target **rho-Oph A core (SM1, SM1N, VLA1623)**: coordinates _not stated_; z/distance 137.3±1.2 pc  
  > "The $\rho$ Ophiuchus cloud complex at a distance of 137.3$\pm$1.2 pc (cite: Ortiz-Leon2017)" (Introduction); distance from Ortiz-Leon2017  
  > "The $\rho$ Ophiuchus cloud complex at a distance of 137.3$\pm$1.2 pc (cite: Ortiz-Leon2017)" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00187.S, 2016.1.01468.S
- bands: ALMA Band 3 (3 mm) archival, used only in an appendix  
  > "The first Band 3 observations from project 2013.1.00187.S were made during cycle 2 on January 31, 2015." (Appendix A)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: ALMA: compact (37 antennas) and C40-4  
  > "The array was in C40-4 configuration." (Appendix A)
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: ALMA 3 mm image rms 0.18 mJy/beam  
  > "The rms noise level of the 3 mm continuum image is 0.18 mJy beam$^{-1}$." (Appendix A)
- time on source: ALMA: 60.48 s and 241.92 s total integration  
  > "The total integration time is 241.92 seconds" (Appendix A)
- observing dates: _not stated_
- pi or archival as stated: ALMA data obtained from the ALMA Science Archive; SMA data from the SMA archive (2005) plus new 2016 SMA observations  
  > "The ALMA datasets were obtained from ALMA Science Archive." (Appendix A)
- Line: C18O 2-1 (not stated)
- Line: C17O 2-1 (224.714 GHz)
- Other facility **SMA**: 1.3 mm continuum and C18O, C17O, CH3OH, H2CO lines (main data)  
  > "observed with the Submillimeter Array (SMA)" (abstract)
- Other facility **IRAM 30m**: 1.3 mm single-dish continuum for short spacings  
  > "The 1.3 mm continuum data of the $\rho$-Oph A region were taken with the IRAM 30m telescope by (cite: Motte1998)." (2.2)
- Other facility **JCMT**: C18O (2-1) single-dish cube  
  > "The single-dish data of the C$^{18}$O (2–1) line were obtained through the JCMT science archive." (2.2)
- External data: N2H+ (1-0) data cube from IRAM 30m and BIMA  
  > "We thank James Di Francesco for providing the N$_2$H$^+$ data cube obtained with the IRAM 30 m telescope and the BIMA interferometer" (Acknowledgments) [from DiFrancesco2004]
- External data: JCMT C17O (2-1) data for optical depth  
  > "estimated using the C$^{18}$O (2–1) and C$^{17}$O (2–1) data observed with the JCMT (cite: Gurney2008)" (3.3) [from Gurney2008]

## Processing

### Calibration

- pipeline or manual: SMA data calibrated with MIR in IDL; ALMA calibrated with CASA (version not stated)  
  > "The visibility data were calibrated using the MIR package in IDL." (2.1)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: SMA: MIRIAD; ALMA 3 mm: tclean in mfs mode  
  > "used "tclean" in the mfs (multi-frequency synthesis) mode" (Appendix A)
- deconvolver: MOSSDI (CLEAN-based) for combined maps  
  > "The combined maps were deconvolved using the CLEAN-based algorithm, MOSSDI (cite: Sault1996)." (2.3)
- weighting robust: robust = 0.5 (ALMA 3 mm)  
  > "The robust weighting of 0.5 was adopted" (Appendix A)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: SMA + single-dish via MIRIAD following Takakuwa2003  
  > "We used the MIRIAD package and followed the procedure described in (cite: Takakuwa2003)" (2.3)
- smoothing: _not stated_
- final beam: 1.3 mm continuum 5.2"x3.1"; C18O 4.9"x3.4"; ALMA 3 mm 1.1"x1.0"  
  > "The synthesized beam is 5.2$''$$\times$3.1$''$ (P.A. = 6.1$\ensuremath{^\circ}$) for the continuum map" (2.3)
- final rms: _not stated_

### Inherited from earlier work

- Combination procedure for single-dish and interferometer data  
  > "followed the procedure described in (cite: Takakuwa2003)" (2.3) [from Takakuwa2003]
- C18O optical depth method  
  > "We followed the method described in the appendix B of (cite: Ladd1998)." (3.3) [from Ladd1998]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration details for the ALMA data
- Robust and weighting for SMA imaging
- Line-free channels used for continuum
- Excitation temperature map details for C18O
- SMA archive project codes

## Analysis recipe

1. **Combine SMA and single-dish data**: MIRIAD combination, MOSSDI deconvolution  
  > "The combined maps were deconvolved using the CLEAN-based algorithm, MOSSDI (cite: Sault1996)." (2.3)
   - software: MIRIAD
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit continuum sources**: Single Gaussian fits with IMFIT  
  > "were determined from the single Gaussian component fitting using the MIRIAD task IMFIT." (3.1)
   - software: MIRIAD
   - fitting: single Gaussian  
  > "The coordinates, peak flux density, total flux, size, and position angle of each source were determined from the single Gaussian component fitting using the MIRIAD task IMFIT." (Results and analysis, 1.3 mm continuum)
   - validation: _not stated_
3. **H2 column density, abundances and masses**: Dust continuum column density; LTE column densities of C18O and N2H+ following Mangum & Shirley  
  > "by following (cite: Mangum2015), the C$^{18}$O and N$_2$H$^+$ column densities can be derived from the local thermodynamic equilibrium (LTE) assumptions" (3.3)
   - assumption: kappa = 0.005 cm2/g, Tdust = 27 K, N2H+ Tex = 15 K, 18O/17O = 3.65  
  > "The excitation temperature of N$_2$H$^+$ was assumed to be 15 K" (3.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **MIRIAD** : SMA imaging, data combination, source fitting  
  > "imaged using the MIRIAD package" (2.4)
- **MIR** : SMA calibration  
  > "The visibility data were calibrated using the MIR package" (2.4)
- **CASA** : ALMA 3 mm calibration and tclean imaging  
  > "CASA (cite: Mcmullin2007) was used to calibrate and reduce both datasets." (Appendix A)
- **Starlink ORAC-DR** : JCMT data reduction  
  > "calibrated and gridded to the data cube using the "ORAC-DR" pipeline" (2.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| VLA1623 mass | 0.41 | ~10% | Msun | 3 | / VLA1623 / 16:26:26.44 / -24:24:30.65 / 0.50 / 0.86 / |
| C18O abundance at VLA1623 | 4.3e-8 | not stated | dimensionless | 3 | / VLA1623 / 5.8 / 2.5 / 7.8 / 4.3 / 1.4 / |
| Max C18O optical depth | 5.5 | not stated | dimensionless | 3 | with the highest value of 5.5 at 5$''$ W of SM1 |
| C17O SMA flux recovered vs single dish | ~3 | not stated | % | 0 | the C$^{17}$O flux recovered by the SMA is only $\sim$3$\%$ of the single-dish flux |

## Qualitative findings

- C18O is bright at eastern and western ridge edges, anticorrelated with continuum and N2H+; consistent with external heating  
  > "This supports the picture that the $\rho$-Oph A core is heated externally from the nearby stars Oph S1 and HD147889." (abstract)

## Claim tuples

- H: The ridge is externally heated and its interior is cold with CO depletion | E: Combined SMA+JCMT C18O maps and abundance maps | R: C18O Tb 40-50 K at edges, below 15 K in center; abundance decreases in ridge | F: External heating by Oph S1 and HD147889; interior colder than CO freeze-out | **supported**
- H: Small condensations are gravitationally bound | E: Mass vs Bonnor-Ebert mass | R: All masses exceed Bonnor-Ebert masses | F: Condensations are bound | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): C18O optical depth not derivable in SM1N since C17O covers only 50"x50"  
  > "Therefore, we could not derive the optical depth of the C$^{18}$O in the SM1N region." (3.3)
- Caveat (inferred, ours): ALMA used only for a supporting 3 mm image
- Caveat (inferred, ours): Single assumed dust temperature and opacity
- Caveat (inferred, ours): No uncertainties on abundances

## Reproducibility

- Data public (paper): SMA and JCMT data from public archives; ALMA from ALMA archive  
  > "obtained from the SMA data archive" (2.1)
- Products in archive: _not stated_
- Missing: SMA archive project IDs
- Missing: CASA version
- Missing: Imaging parameters for SMA
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and moderate recipe, but missing parameters and ALMA role minor.
- Rediscovery candidate: no, ALMA part is minor and recipe incomplete.

## Links

- Method: Takakuwa2003 (single-dish and interferometer combination)
- Method: Mangum2015 (LTE column density formulae)
- Companion: Kirk2017 (ALMA 3 mm observations of the same region)
- Companion: Kawabe2018 (ALMA 1.3 mm study of SM1 and VLA1623-N1)

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 33,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
