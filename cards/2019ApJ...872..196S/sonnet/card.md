# Implications of a Hot Atmosphere/Corino from ALMA Observations toward NGC 1333 IRAS 4A1

`2019ApJ...872..196S` | The Astrophysical Journal 2019 | first author: Sahu, Dipen | arXiv: 1901.05424 | DOI: 10.3847/1538-4357/aaffda

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Do the protostellar binary cores IRAS 4A1 and 4A2 host complex organic molecules, and what do the continuum opacity and COM absorption/emission imply for the nature of A1?  
  > "we report, for the first time, the solid evidence of complex organic molecules (COMs), including CH$_3$OH, $^{13}$CH$_3$OH, CH$_2$DOH, CH$_3$CHO associated with the A1 core seen in absorption." (abstract)
- Target **NGC 1333 IRAS 4A (A1 and A2)**: coordinates 03 29 10.50 +31 13 31.5 (J2000 phase centre)  
  > "The phase centre of the observations was set at R.A.(J2000) = 03$^d$ 29$^m$ 10.50$^s$ , Dec.(J2000) =+31$^\circ$13$'$ 31.5$''$" (Observations); "A recent result from GAIA measured the distance of Perseus molecular cloud to be 293$\pm$22 pc (cite: ortiz18; zucker18), we adopt this updated distance ($\sim$293 pc) throughout the paper." (Introduction); z/distance 293 pc  
  > "The phase centre of the observations was set at R.A.(J2000) = 03$^d$ 29$^m$ 10.50$^s$ , Dec.(J2000) =+31$^\circ$13$'$ 31.5$''$" (Observations); "A recent result from GAIA measured the distance of Perseus molecular cloud to be 293$\pm$22 pc (cite: ortiz18; zucker18), we adopt this updated distance ($\sim$293 pc) throughout the paper." (Introduction); distance from Gaia distance to Perseus (Ortiz-Leon et al. 2018; Zucker et al. 2018)  
  > "The phase centre of the observations was set at R.A.(J2000) = 03$^d$ 29$^m$ 10.50$^s$ , Dec.(J2000) =+31$^\circ$13$'$ 31.5$''$" (Observations); "A recent result from GAIA measured the distance of Perseus molecular cloud to be 293$\pm$22 pc (cite: ortiz18; zucker18), we adopt this updated distance ($\sim$293 pc) throughout the paper." (Introduction)

## Data provenance

- ALMA projects: 2015.1.00147.S
- bands: Band 7 (0.84 mm)  
  > "Three Execution Blocks (EBs) were conducted with ALMA Band 7 receiver on 2016 Jul. 23 and 24 and 2016 Dec. 14." (Observations)
- frequencies and spectral setup: Seven spectral windows; analysed broadband window centred at 350.714 GHz, 1.875 GHz bandwidth, 976 kHz channels (0.84 km/s, Hanning-smoothed)  
  > "including one broadband window centered at 350.714 GHz whose bandwidth and spectral channel width are 1.875 GHz and 976 kHz, respectively." (Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m array, 39, 42 and 43 antennas in the three EBs  
  > "The number of antennas in the 12 M array for the three EBs were respectively 39, 42, and 43." (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.30'' x 0.20'' continuum; 0.31'' x 0.20'' cubes  
  > "The resulting synthesized beam size is 0.30$''$ $\times$ 0.20$''$ (PA=-6.45$^\circ$) for the continuum map" (Observations)
- max recoverable scale: _not stated_
- sensitivity: rms ~8 mJy/beam continuum, 3 mJy/beam cubes  
  > "The resulting rms level is $\sim$ 8 mJy beam$^{-1}$ and 3 mJy beam$^{-1}$ in the continuum image and spectral cubes, respectively" (Observations)
- time on source: about 84 min  
  > "the total integration time on-source was approximately 84 mins." (Observations)
- observing dates: 2016 Jul 23, 24 and Dec 14  
  > "Three Execution Blocks (EBs) were conducted with ALMA Band 7 receiver on 2016 Jul. 23 and 24 and 2016 Dec. 14." (Observations)
- pi or archival as stated: _not stated_
- Line: CH3OH vt=0 1(1,1)-0(0,0)++ and others (350905.12 MHz (this line))
- Line: 13CH3OH vt=0 1(1,0)-0(0,0)++, 8(1,7)-7(2,5) (350103.12, 350421.58 MHz)
- Line: CH2DOH several e1 transitions (349862-350632 MHz)
- Line: CH3CHO 18-17 transitions (350133-351119 MHz)
- External data: Single-dish 0.85 mm peak flux densities (10.3 and 9.05 Jy/beam)  
  > "reported a peak flux density of 10.3 Jy beam$^{-1}$ within a 16${''}$ beam toward IRAS 4A." (3.1 Dust continuum emission) [from Smith et al. 2000 (cite: smith00); Sandell & Knee 2001 (cite: sand01)]
- External data: ALMA 1.2 mm peak flux of 542 mJy toward A1  
  > "detected with ALMA a peak continuum flux of 542 mJy towards the A1 centroid" (4.1 Continuum Opacity) [from (cite: lopez17)]
- External data: VLA 8.1 and 10.3 mm peak fluxes of 4.151 and 2.759 mJy toward A1  
  > "measured peak continuum fluxes of 4.151 mJy and 2.759 mJy at 8.1 mm and 10.3 mm, respectively, towards A1" (4.1 Continuum Opacity) [from (cite: cox15)]
- External data: Line catalogs JPL and CDMS for synthetic spectra  
  > "employing the JPL (cite: pick98) and CDMS (cite: muller01; muller05) databases" (3.2 Detected molecules) [from (cite: pick98); (cite: muller01; muller05)]

## Processing

### Calibration

- pipeline or manual: ALMA observatory pipeline  
  > "The data were first calibrated by the ALMA observatory through the data reduction pipeline" (Observations)
- casa version: CASA 4.7  
  > "Common Astronomy Software Application package (CASA, version 4.7 (cite: mcmullin07))" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: calibration error ~10%  
  > "there are calibration error $\sim 10\%$, we have not included it here." (Table 3)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "We used Briggs weighting with a robustness parameter of 0.5 for forming the images." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: fit and subtract continuum in visibility domain  
  > "by fitting and subtracting continuum emission in the visibility domain" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.30'' x 0.20'' (PA -6.45 deg) continuum; 0.31'' x 0.20'' (PA -24 deg) cubes  
  > "0.31$''$ $\times$ 0.20$''$ (P.A= -24$^\circ$) for the spectral data cubes" (Observations)
- final rms: ~8 mJy/beam continuum; 3 mJy/beam cubes  
  > "The resulting rms level is $\sim$ 8 mJy beam$^{-1}$ and 3 mJy beam$^{-1}$" (Observations)

### Inherited from earlier work

- Full observational setup described in a forthcoming paper  
  > "more details about the full observational setup can be found in our forthcoming paper (Su et al. 2019)" (Observations) [from Su et al. 2019]
- Dust opacity law  
  > "a dust opacity $\kappa_{\nu}$ = 0.006 ($\nu$/245 GHz) $^\beta$ cm$^2$ g$^{-1}$ (Kramer et al. 1998; Shepherd & Watson 2002)" (3.1 Dust continuum emission) [from Kramer et al. 1998; Shepherd & Watson 2002]
- Rotation diagram method  
  > "we may estimate the gas temperature using the rotation diagram method ((cite: turner91; herbst09) and references therein)" (3.3 Gas temperatures) [from (cite: turner91; herbst09)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum fitting/subtraction
- Image size, cell size, deconvolver, masks and clean thresholds
- Flux, bandpass and phase calibrators
- Integration velocity ranges for moment maps
- Partition functions and line strengths used in rotation diagrams
- Details of how 2D Gaussian fits and stacking were done
- Whether self-calibration was applied

## Analysis recipe

1. **Image continuum and cubes**: Pipeline calibration, visibility-domain continuum subtraction, Briggs imaging  
  > "We then generated both the 0.84 mm continuum and spectral visibilities by fitting and subtracting continuum emission in the visibility domain." (Observations)
   - software: CASA, MIRIAD
   - parameter: robust = 0.5  
  > "We used Briggs weighting with a robustness parameter of 0.5 for forming the images." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit continuum components and derive masses**: Two-component 2D Gaussian fit to each source; optically thin dust mass  
  > "We applied a two-component 2D Gaussian fitting to the two sources and summarize the fitting results in Table [1](#tb-cont-fit)." (3.1 Dust continuum emission)
   - assumption: gas-to-dust 100, Tdust 60 K, beta 1.5, d = 293 pc, optically thin  
  > "Assuming a gas-to-dust ratio of 100, a (uniform) dust temperature of 60 K" (3.1 Dust continuum emission)
   - fitting: _not stated_
   - validation: Compared with single-dish 0.85 mm fluxes; missing flux judged not severe  
  > "we conclude that the missing flux issue, though may result from the most extended envelope, is not severe" (3.1 Dust continuum emission)
3. **Identify lines**: Synthetic spectra from JPL/CDMS in CASSIS compared with observed spectra  
  > "we generated synthetic spectra within CASSIS." (3.2 Detected molecules)
   - software: CASSIS
   - parameter: vsys = 6.96 km/s; match at 3 sigma for Aij >= 1e-5  
  > "Essentially all isolated transitions from these molecules with their Einstein co-efficient $A_{ij} \geq 10^{-5}$ are well matched (at a level of 3$\sigma$ and above)" (3.2 Detected molecules)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit line profiles**: Gaussian profile fitting giving intensity, Vlsr, width  
  > "We applied Gaussian profile fitting for extracting the spectral parameters of the identified features." (3.2 Detected molecules)
   - software: CASSIS
   - fitting: _not stated_
   - validation: Velocities of transitions of one molecule consistent  
  > "The fitting results of spectral profiles from different transitions of a molecule have peak around a common LSR velocity" (3.2 Detected molecules)
5. **Derive Trot and column densities**: Rotation diagram, LTE; for A1 absorption (Scenario I) optically thin foreground layer against continuum background  
  > "we assume that most, if not all, of the observed transitions in A1 are optically thin and there is no saturation in absorption." (3.3 Gas temperatures)
   - parameter: Trot assumed 200 K where no diagram fit  
  > "for molecules where do not have any estimation of rotational temperature, we choose the temperature to be 200 K" (3.3 Gas temperatures)
   - assumption: LTE, single Trot  
  > "characterized by a single (rotation) temperature T$_{ex} =$ T$_{rot}$, if its excitation is assumed in local thermodynamic equilibrium (LTE)" (3.3 Gas temperatures)
   - fitting: _not stated_
   - validation: _not stated_
6. **Compare continuum brightness temperatures across wavelengths and deuteration**: Brightness temperatures from ALMA, JVLA, VLA; smooth ALMA to JVLA beam; 13CH3OH/CH2DOH ratios with 12C/13C ~ 70  
  > "We, for example, smooth our ALMA 0.84 mm continuum to have the same beam size as that of the JVLA 6.9 mm observations" (4.1 Continuum Opacity)
   - assumption: 12C/13C ~ 70  
  > "If we consider $^{12}$C/$^{13}$C $\sim$ 70 (cite: sheffer07)" (4.4 Deuterium Fractionation)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7: Pipeline calibration  
  > "Common Astronomy Software Application package (CASA, version 4.7 (cite: mcmullin07))" (Observations)
- **MIRIAD** : Image inspection and spectral line analysis  
  > "We subsequently used MIRIAD (cite: sault95) and CASSIS" (Observations)
- **CASSIS** : Line identification, synthetic spectra and analysis  
  > "We visualized the spectral data in CASSIS for initial line identifications." (3.2 Detected molecules)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total recovered continuum flux density | 7.24 | not stated | Jy | 2 | Overall we recovered within the region a flux density of 7.24 Jy. |
| A1-A2 separation | 1.8 | not stated | arcsec | 2 | is 1.8$''$, in agreement with previous measurements |
| Peak brightness temperature A1 / A2 | 57 / 42 | not stated | K | 2 | The brightness temperatures derived from the observed peak continuum are 57 K and 42 K towards A1 and A2, respectively. |
| Masses A1 compact, A1 extended, A2 compact, A2 extended | 0.15, 0.49, 0.07, 0.50 | not stated | Msun | 2 | / 4A1    / compact   / 03 29 10.538 / +31 13 30.93 / 923       / 0.397                / 0.354                / 64.1         / 0.15        / |
| H2 column density toward A1 centroid | >= 1.3e26 | not stated | cm^-2 | 2 | the H$_2$ column density toward the 4A1 centroid is estimated to be at least 1.3 $\times$ 10$^{26}$ cm$^{-2}$ |
| Trot 13CH3OH in A2 / CH3CHO in A2 | 375.13 / 261.31 | 270.02 / 10.79 | K | 5 | we obtained rotation temperatures of 375.13$\pm$270.02 K and 261.31$\pm$10.79 K for $^{13}$CH$_3$OH and the CH$_3$CHO, respectively. |
| Trot CH3OH / 13CH3OH in A1 | 140.39 / 58.94 | 6.63 / 3.74 | K | 5 | rotation temperatures for CH$_3$OH and $^{13}$CH$_3$OH are 140.39$\pm$6.63 K and 58.94$\pm$ 3.74 K, respectively. |
| CH3OH column density in A1 | >= 1.14e17 | 0.17e17 | cm^-2 | 5 | $\leq 140.39 \pm 6.63$ K  / $\geq (1.14 \pm 0.17)\times 10^{17}$ |
| 13CH3OH/CH2DOH ratio A2 and A1 | 2.47 and 0.29 | not stated | dimensionless | 6 | The $^{13}$CH$_3$OH/CH$_2$DOH ratio for A2 and A1 is 2.47 and 0.29 (considering the average value) respectively. |
| CH2DOH/CH3OH lower limit A2 and A1 | 0.6e-2 and 4.9e-2 | not stated | dimensionless | 6 | then the lower limit of CH$_2$DOH/CH$_3$OH ratio in A2 and A1 becomes the 0.6$\times 10^{-2}$ and 4.9$\times 10^{-2}$ respectively. |
| A1 peak brightness smoothed to JVLA 6.9 mm beam | 39 | not stated | K | 6 | find the resulting A1 peak brightness be 39 K |

## Qualitative findings

- COMs (CH3OH, 13CH3OH, CH2DOH, CH3CHO) seen in absorption toward A1 against optically thick continuum; A2 shows emission from a hot corino  
  > "A forest of spectral line emissions is observed towards A2, while spectral transitions towards A1 are detected in absorption." (Conclusion)

## Claim tuples

- H: Is the A1 continuum optically thick while A2 is optically thin? | E: Compare brightness temperatures from 0.84 mm to 10 mm and line absorption | R: Comparable brightness (~40-80 K) from 10 mm to 0.84 mm for A1; A2 much weaker at 6.9 mm | F: A1 continuum likely optically thick, A2 predominantly optically thin | **supported**
- H: Does A1 host COMs? | E: Line identification in the 350 GHz band | R: Absorption by CH3OH, 13CH3OH, CH2DOH, CH3CHO toward A1 | F: COMs are associated with A1, in a compact region | **supported**
- H: Origin of A1 absorption | E: Rotation diagrams under optically thin (Scenario I) vs saturated (Scenario II) absorption | R: Trot ~100 K, compact <~73 AU absorbing layer; no infall signature | F: Either hot-corino-like atmosphere over an optically thick disk, or temperature-stratified envelope; not distinguished | **partially**
- H: Does the methanol deuteration indicate a hot-corino environment in A1? | E: Estimate CH2DOH/CH3OH from 13CH3OH and CH2DOH columns | R: Ratios of order 1e-2 in both sources | F: Low deuteration suggests hot gas (~100 K) in both | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Common foreground origin and outflow-shock origin of COM features were ruled out  
  > "strongly ruling out a common (foreground) origin of the observed COM absorption and emission." (4.2 COM Features)
- How they decided it was enough: _not stated_
- Limitation (authors): Rotation temperatures are upper limits and column densities lower limits because low-Eu lines may be optically thick; large uncertainty in 13CH3OH columns; assumed 200 K  
  > "These temperatures should be taken as upper limits though, as their corresponding lower E$_u$ lines are possibly optically thick." (3.3 Gas temperatures)
- Caveat (inferred, ours): Rotation-diagram temperatures rest on few lines, some blended, with huge uncertainty for 13CH3OH in A2
- Caveat (inferred, ours): Assumed 200 K Trot and 12C/13C=70 drive the deuteration ratios
- Caveat (inferred, ours): Beam filling factor and absorption saturation are unconstrained
- Caveat (inferred, ours): Scenarios for A1 are not discriminated
- Caveat (inferred, ours): Single dust temperature of 60 K for masses

## Reproducibility

- Data public (paper): Archival ALMA project cited, public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00147.S." (Acknowledgment)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masks, line-free channels)
- Missing: Calibrator information
- Missing: Integration ranges and fitting windows for lines
- Missing: Partition function and spectroscopic constants used
- Data volume (inferred): ~50-100 GB raw for three EBs; ~10 GB for the broadband spw products
- Score (inferred): 3/5, Data identified by project code and key steps described, but imaging and fitting details are sparse.
- Rediscovery candidate: no, Recipe lacks imaging and line-fit details, and the results rely on interpretive scenarios and assumptions.

## Links

- Method: Turner 1991 (cite: turner91) (Rotation diagram equations)
- Method: Goldsmith & Langer 1999 (cite: goldsmith99) (Opacity correction to column density)
- Companion: Su et al. 2019 (Forthcoming paper with full observational setup)
- Companion: López-Sepulcre et al. 2017 (cite: lopez17) (Previous ALMA/PdBI study of COMs in IRAS 4A)
- Related: VANDAM survey
- Related: PROSAC survey

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
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 46,
  "rate": 0.575
 },
 "evidence_ok": true
}
```
