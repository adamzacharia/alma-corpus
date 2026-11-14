# The ALMA-PILS survey: first detection of methyl isocyanide (CH<SUB>3</SUB>NC) in a solar-type protostar

`2018A&A...617A..95C` | Astronomy and Astrophysics 2018 | first author: Calcutt, H. | arXiv: 1807.02909 | DOI: 10.1051/0004-6361/201833140

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: astrochemistry, star_formation
- Question: What is the abundance of CH3NC in the protostellar binary IRAS 16293-2422 compared with CH3CN, and what do chemical models imply about CH3NC formation and destruction?  
  > "The aims of this work are to determine the abundances of methyl isocyanide in the solar-type protostellar binary IRAS 16293–2422 and understand the stark abundance differences observed between methyl isocyanide and methyl cyanide in the ISM." (abstract)
- Target **IRAS 16293-2422 B**: coordinates 16h32m22.58s, -24d28m32.8s (offset position)  
  > "The first position at $\alpha_{J2000}$=16$^{\rm h}$32$^{\rm m}$22s58, $\delta_{J2000}$=$-$24$^{\circ}$28$'$32.8$''$, is offset from the continuum peak position of IRAS 16293B in the south west direction by one beam diameter (0.5$''$, 70 AU)." (2 Observations); "located only 141 pc away (cite: Dzib2018)" (1 Introduction); z/distance 141 pc  
  > "The first position at $\alpha_{J2000}$=16$^{\rm h}$32$^{\rm m}$22s58, $\delta_{J2000}$=$-$24$^{\circ}$28$'$32.8$''$, is offset from the continuum peak position of IRAS 16293B in the south west direction by one beam diameter (0.5$''$, 70 AU)." (2 Observations); "located only 141 pc away (cite: Dzib2018)" (1 Introduction); distance from Dzib et al. 2018  
  > "The first position at $\alpha_{J2000}$=16$^{\rm h}$32$^{\rm m}$22s58, $\delta_{J2000}$=$-$24$^{\circ}$28$'$32.8$''$, is offset from the continuum peak position of IRAS 16293B in the south west direction by one beam diameter (0.5$''$, 70 AU)." (2 Observations); "located only 141 pc away (cite: Dzib2018)" (1 Introduction)
- Target **IRAS 16293-2422 A**: coordinates 16h32m22.90s, -24d28m36.2s (offset position)  
  > "that is 0.6$''$ (85 AU) north east from the peak continuum position of IRAS 16293A." (2 Observations); z/distance 141 pc  
  > "that is 0.6$''$ (85 AU) north east from the peak continuum position of IRAS 16293A." (2 Observations); distance from Dzib et al. 2018  
  > "that is 0.6$''$ (85 AU) north east from the peak continuum position of IRAS 16293A." (2 Observations)

## Data provenance

- ALMA projects: 2013.1.00278.S
- bands: Band 7  
  > "an ALMA observing program to study IRAS 16293 in Band 7, between 329.147 GHz and 362.896 GHz" (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12 m array plus ACA  
  > "The data are a combination of the main 12 m array and Atacama Compact Array (ACA) observations" (2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.5 arcsec restoring beam, 0.2 km/s spectral resolution  
  > "which have been combined to have a restoring beam of 0.5$''$ at a spectral resolution of 0.2 km s$^{-1}$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: 7–10 mJy/beam/channel, ~5 mJy/beam km/s  
  > "They reach a sensitivity of about 7–10 mJy beam$^{-1}$ channel$^{-1}$, i.e., approximately $\sim$5 mJy beam$^{-1}$ km s$^{-1}$ across the entire frequency range." (2 Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CH3NC J=17-16 and 18-17, K=0-7, v=0 (341.33–341.71 GHz and 361.40–361.79 GHz)
- Line: CH3CN 18(±4)-17(∓4) v8=1 (not stated)
- External data: CH3CN column densities in IRAS 16293A and B  
  > "$^{c}$Determined using CH$_{3}$CN column densities from (cite: Calcutt2017)." (Table 2) [from (cite: Calcutt2017)]
- External data: CH3CN/CH3NC ratios in other sources  
  > "| Sgr B2(N) molecular cloud |         50          |     HM      | \[1\] |" (Table 3) [from Table 3 refs [1]-[6]]
- External data: JPL catalog entry for CH3NC used initially  
  > "The initial modelling of the methyl isocyanide emission lines was performed using the JPL catalog (cite: Pickett1998) entry." (3.2 Column densities) [from (cite: Pickett1998)]
- Simulation/model as data: MAGICKAL chemical models at final nH = 1.6e7 and 6e10 cm^-3  
  > "we run two models, using two different final densities for the collapse phase" (3.3 Chemical modelling)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: better than 5%  
  > "The flux calibration accuracy of these data are better than 5% (cite: Jorgensen2016)." (3.2 Column densities)
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
- continuum subtraction: described in Jorgensen2016  
  > "Further details of the data reduction and continuum subtraction procedure can be found in (cite: Jorgensen2016)." (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.5 arcsec  
  > "a restoring beam of 0.5$''$" (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Data reduction and continuum subtraction  
  > "Further details of the data reduction and continuum subtraction procedure can be found in (cite: Jorgensen2016)." (2 Observations) [from (cite: Jorgensen2016)]
- VINE map method  
  > "More details of how a VINE map is created and the caveats with this method can be found in (cite: Calcutt2017)." (3.1 Spatial extent) [from (cite: Calcutt2017)]
- Two final densities for models  
  > "Following (cite: Coutens2018), we run two models, using two different final densities for the collapse phase" (3.3 Chemical modelling) [from (cite: Coutens2018)]
- Network and two-stage physical model  
  > "The chemical network is based on that of (cite: Belloche2017)" (3.3 Chemical modelling) [from (cite: Belloche2017)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (weighting, robust, cleaning) are only in Jorgensen2016
- CASA version and calibration details
- Exact spectral windows and channel selection used for chi2
- Which lines counted as 'most optically thin' for fitting
- RMS value used for upper limits
- Chemical network files and reaction rate details of the new CH3NC reactions
- Details of the CDMS CH3NC catalog (not yet public at publication)

## Analysis recipe

1. **Extract spectra at offset positions**: Spectra extracted from positions offset from continuum peaks of B and A  
  > "In this work we analyse spectra extracted from two positions, where a large number of complex organic molecules have been previously detected and the line emission is not obscured by dust." (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit LTE models for CH3NC column density and Tex**: Grid of LTE synthetic spectra compared to optically thin lines, minimum chi2  
  > "The results of these models were compared to the spectra of the most optically thin lines to determine the best-fit model by computing the minimum $\chi^2$." (3.2 Column densities)
   - software: CASSIS
   - parameter: N 1e13–9e14 cm^-2; Tex 80–300 K; FWHM 0.8–1.2 km/s; peak velocity 2.5–2.9 km/s  
  > "A large grid of models was run with column densities between 1$\times$10$^{13}$ – 9$\times$10$^{14}$ cm$^{-2}$ and excitation temperatures between 80 – 300 K." (3.2 Column densities)
   - assumption: LTE, source size 0.5 arcsec, continuum background correction factor 1.1 at 150 K  
  > "The correction factor is 1.1 at 150 K towards IRAS 16293B." (3.2 Column densities)
   - fitting: chi2 grid minimisation  
  > "The results of these models were compared to the spectra of the most optically thin lines to determine the best-fit model by computing the minimum $\chi^2$." (Results and analysis, Column densities and excitation temperatures)
   - validation: Errors from minimum change in each quantity producing significant change in goodness of fit  
  > "We therefore determine the errors by determining the minimum change to each quantity which produces a significant difference to the goodness of fit." (3.2 Column densities)
3. **Upper limits for source A**: 3 sigma limit on brightest line 17_3-16_3 at 341.637 GHz  
  > "We use $1.05{\times}3{\times}RMS{\times}\sqrt{{\Delta}V{\times}FWHM}$ to compute the 3$\sigma$ limit" (3.2 Column densities)
   - software: CASSIS
   - parameter: FWHM 2.2 km/s, Tex 150 K  
  > "We assume a line width of 2.2 km s$^{-1}$ based on the line width found for nitriles towards this source by (cite: Calcutt2017), and an excitation temperature of 150 K." (3.2 Column densities)
   - fitting: _not stated_
   - validation: _not stated_
4. **Chemical modelling of CH3CN/CH3NC**: Three-phase MAGICKAL cold collapse then warm-up to 400 K, two final densities  
  > "The two-stage physical model used is also similar to that of (cite: Belloche2017), in which a cold collapse is followed by a static warm-up to 400 K." (3.3 Chemical modelling)
   - software: MAGICKAL
   - parameter: Gas 10 K; dust 16 to 8 K; warm-up reaches 400 K at 2.8e5 yr  
  > "reaches a final temperature of 400 K at $2.8\times10^{5}$ years" (3.3 Chemical modelling)
   - parameter: 15% isomerisation; H+CH3NC barrier 1200 K  
  > "This reaction is assumed to have a barrier of 1200 K, based on recent calculations of the barrier for H + HNC (cite: Graninger2014)." (3.3 Chemical modelling)
   - assumption: Single-point uniform-density model  
  > "The chemical model is a single-point model, thus it has a uniform density." (3.3 Chemical modelling)
   - fitting: _not stated_
   - validation: Compared model ratio at 150 K with observed ratios  
  > "In the low-density case, the ratio at 150 K is $\sim$450, which is the same order as the observed ratio in IRAS 16293B." (Results and analysis, Chemical modelling)

## Software

- **CASSIS** : LTE synthetic spectra and fits  
  > "the spectral modelling software CASSIS[^1] was used to calculate synthetic spectra and determine best-fit spectral models" (3.2 Column densities)
- **MAGICKAL** : three-phase chemical kinetics modelling  
  > "we use an updated version of the three-phase chemical kinetics model *MAGICKAL* (cite: Garrod2013)" (3.3 Chemical modelling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Tex CH3NC IRAS 16293B | 150 | ±20 | K | 2 | / IRAS 16293B / 150$\pm$20 / 2.0$\pm$0.2$\times$10$^{14}$ / 200 / |
| N(CH3NC) IRAS 16293B | 2.0e14 | ±0.2e14 | cm^-2 | 2 | / IRAS 16293B / 150$\pm$20 / 2.0$\pm$0.2$\times$10$^{14}$ / 200 / |
| N(CH3NC) IRAS 16293A upper limit | <1.45e13 | not stated | cm^-2 | 3 | $<$1.45$\times$10$^{13}$$^{b}$ |
| CH3CN/CH3NC ratio in B | 200 | not stated | dimensionless | 2 | The CH$_3$CN/CH$_3$NC abundance ratio in IRAS 16293B is 200 |
| Model ratio at 150 K, low density | ~450 | not stated | dimensionless | 4 | In the low-density case, the ratio at 150 K is $\sim$450 |
| Model ratio at 150 K, high density | ~2.5e6 | not stated | dimensionless | 4 | The ratio at the same point in the high-density model is $\sim$2.5$\times$10$^{6}$ |

## Qualitative findings

- CH3NC emission traces the disk component of B with similar extent to CH3CN  
  > "The emission traces the disk component of IRAS 16293B and shows a similar morphology and extent to methyl cyanide emission." (3.1 Spatial extent)

## Claim tuples

- H: CH3NC is detectable in a solar-type protostar | E: Search PILS spectra at offset positions of A and B | R: 10 unblended and 6 blended lines above 3 sigma in B; none in A | F: First detection of CH3NC in a solar-type protostar, B | **supported**
- H: Chemical models reproduce the observed ratios | E: MAGICKAL models at two final densities | R: Low density gives ~450, high density ~2.5e6 | F: Models fail to match B at representative density but are consistent with A limits; an extra gas-phase CH3NC destruction is needed | **partially**

## Reasoning

- Why this data: High sensitivity needed because CH3NC emission is very weak  
  > "high sensitivity observations are needed as it has shown very weak emission in the objects it has been detected in so far" (1 Introduction)
- Why this method: _not stated_
- Alternative: Adding CH3+ + HNC association had little effect on CH3CN and CH3NC  
  > "it was observed that the inclusion of this process did not affect the abundance of CH$_{3}$CN in any significant way" (3.3 Chemical modelling)
- How they decided it was enough: _not stated_
- Limitation (authors): H+CH3NC reaction is speculative with very uncertain barrier  
  > "In particular, the reaction of H+CH$_3$NC, which is included in both the gas-phase and the grain-surface networks, is quite speculative." (3.3 Chemical modelling)
- Limitation (authors): Blending prevented line identification closer to source A  
  > "no lines could be identified as blending became too severe" (3 Results and analysis)
- Caveat (inferred, ours): Upper-limit ratio is quoted as >5517 in text and >5317 in Table 2
- Caveat (inferred, ours): Single-position LTE analysis with assumed 0.5 arcsec source size
- Caveat (inferred, ours): Single-point models without simultaneous collapse and warm-up
- Caveat (inferred, ours): Evolutionary-stage inference is weak and contradicted by vinyl cyanide

## Reproducibility

- Data public (paper): ALMA PILS data 2013.1.00278.S acknowledged; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00278.S." (Acknowledgements)
- Products in archive: _not stated_
- Code: CH3NC predictions to be made available in CDMS  
  > "The resulting predictions will be made available in the Cologne Database for Molecular Spectroscopy" (3.2 Column densities)
- Missing: Reduced PILS cubes and imaging recipe (Jorgensen2016)
- Missing: MAGICKAL network with new CH3NC reactions
- Missing: Line fit selection details
- Data volume (inferred): Large (tens to hundreds of GB for full PILS cubes)
- Score (inferred): 3/5, Simple LTE fit with stated grid and values, but data processing is inherited and the model code and catalog are not readily available.
- Rediscovery candidate: yes, The data are archival, the LTE fit recipe is mostly given, and the main results are numeric (Tex, N, ratios).

## Links

- Method: Jorgensen2016 (PILS data reduction and continuum subtraction)
- Method: Calcutt2017 (VINE maps, CH3CN column densities, line widths)
- Method: Garrod2013; Willis2017 (MAGICKAL model and back-diffusion correction)
- Companion: Coutens2018 (Chemical modelling at the same two densities)
- Companion: Ligterink2017 (Same offset position used for methyl isocyanate)
- Companion: Manigand2018 (Same offset position used for oxygen-bearing molecules)
- Related: PILS (Protostellar Interferometric Line Survey)

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
  "facts": 79,
  "stated": 44,
  "rate": 0.557
 },
 "evidence_ok": true
}
```
