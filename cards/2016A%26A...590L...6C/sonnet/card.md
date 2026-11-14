# The ALMA-PILS survey: First detections of deuterated formamide and deuterated isocyanic acid in the interstellar medium

`2016A&A...590L...6C` | Astronomy and Astrophysics 2016 | first author: Coutens, A. | arXiv: 1605.02562 | DOI: 10.1051/0004-6361/201628612

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, star_formation
- Question: Are deuterated formamide and deuterated isocyanic acid present towards the protostar IRAS16293B, and what do their deuteration levels imply about formation pathways?  
  > "In this Letter, we report the first detection of the three singly deuterated forms of formamide, as well as DNCO towards IRAS16293." (Introduction)
- Target **IRAS16293-2422 source B**: coordinates extraction position alpha_J2000=16h32m22.58s, delta_J2000=-24d28m32.8s  
  > "a position offset by $\sim$0.5$\ensuremath{''}$ from the continuum peak of source B in the south west direction" (Analysis and results); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00278.S
- bands: Band 7 (329.15-362.90 GHz); Bands 3 and 6 narrow ranges used for consistency checks  
  > "Additional observations in Bands 3 and 6 cover narrow spectral ranges and, consequently, a very limited number of transitions of formamide isotopologues." (Observations)
- frequencies and spectral setup: 329.15-362.90 GHz, spectral resolution 0.244 MHz (~0.2 km/s)  
  > "The spectral resolution of these observations is 0.244 MHz (i.e. $\sim$0.2 km s$^{-1}$)." (Observations)
- continuum bandwidth: _not stated_
- arrays: 12m array and ACA  
  > "both with the 12m array and the Atacama Compact Array (ACA)" (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam sizes 0.4" to 0.7"  
  > "The beam sizes range between 0.4$\ensuremath{''}$ and 0.7$\ensuremath{''}$." (Observations)
- max recoverable scale: _not stated_
- sensitivity: better than 5 mJy/beam km/s  
  > "the final spectral line datacubes show a sensitivity that is better than 5 mJy beam$^{-1}$ km s$^{-1}$" (Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: NH2CDO, cis-NHDCHO, trans-NHDCHO, NH2(13)CHO, DNCO, HN(13)CO many unblended lines (J=16-17/18 type), listed in Table 2 (329-362 GHz)
- External data: Spectroscopic data from CDMS (formamide isotopologues, HNCO) and JPL (DNCO, HN13CO, H15NCO, HNC18O)  
  > "come from the Cologne Database for Molecular Spectroscopy (cite: Muller2001; Muller2005), while the data for DNCO, HN$^{13}$CO, H$^{15}$NCO and HNC$^{18}$O (cite: Hocking1975) are taken from the Jet Propulsion Laboratory (JPL) database" (Spectroscopic data) [from CDMS (cite: Muller2001; Muller2005); JPL (cite: Pickett1998)]
- External data: 12C/13C ratio of 68  
  > "Assuming a $^{12}$C/$^{13}$C ratio of 68 (cite: Milam2005)" (Analysis and results) [from (cite: Milam2005)]
- External data: 16O/18O ratio of 560  
  > "the $^{16}$O/$^{18}$O ratio of 560 in the interstellar medium (cite: Wilson1999)" (Analysis and results) [from (cite: Wilson1999)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
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
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Survey observations and data reduction taken from the PILS survey paper  
  > "A full description of the survey and the data reduction can be found in (cite: Jorgensen2016)." (Observations) [from (cite: Jorgensen2016)]
- Spectrum extraction position  
  > "we use the spectrum extracted at the same position as in (cite: Lykke2016)" (Analysis and results) [from (cite: Lykke2016)]
- Source size 0.5 arcsec  
  > "assuming a linewidth of 1 km s$^{-1}$ and a source size of 0.5$\ensuremath{''}$ (cite: Jorgensen2016; Lykke2016)" (Analysis and results) [from (cite: Jorgensen2016; Lykke2016)]

### Not stated but needed to reproduce (our reading)

- Calibration, CASA version, imaging parameters (all deferred to the PILS paper)
- Line-free channels and baseline subtraction method
- Spectral extraction aperture size
- Vibrational correction details beyond factor 1.5
- Rest-frame velocity (vlsr) of source B used for the models
- Exact CASSIS version and grid step for column densities

## Analysis recipe

1. **Extract spectrum and identify lines**: Spectrum extracted at an offset position from source B continuum peak; unblended lines identified with CASSIS  
  > "Using the CASSIS[^2] software, we identify several unblended lines" (Analysis and results)
   - software: CASSIS
   - fitting: _not stated_
   - validation: Checked consistency with Band 3 and 6 observations  
  > "After the analysis of Band 7, we checked that the results are consistent with these lower frequency observations." (Observations)
2. **Derive column densities with LTE grid**: Grid of LTE synthetic spectra compared to observations by chi2  
  > "We determine the best-fit model using a $\chi$$^2$ method, comparing the observed and synthetic spectra at $\pm$0.5 MHz around the rest frequency of the predicted emission lines." (Analysis and results)
   - software: CASSIS
   - parameter: Tex 100-300 K in 25 K steps; N 1e13-1e17 cm-2  
  > "We predict the spectra for different excitation temperatures between 100 and 300 K with a step of 25 K and for different column densities between 1 $\times$ 10$^{13}$ and 1 $\times$ 10$^{17}$ cm$^{-2}$." (Analysis and results)
   - parameter: Tex = 300 K adopted, linewidth 1 km/s, source size 0.5"  
  > "An excitation temperature of 300 K was consequently adopted for the analysis of the different isotopologues." (Analysis and results)
   - assumption: LTE  
  > "we produce a grid of synthetic spectra, assuming local thermodynamical equilibrium (LTE)" (Analysis and results)
   - fitting: chi2 minimisation on grid; upper limits estimated visually  
  > "The upper limits are estimated visually by a comparison of the synthetic spectra with the observations on the entire spectral range." (Analysis and results)
   - validation: Best-fit model checked not to predict unobserved lines  
  > "We carefully check that the best-fit model does not predict any lines that are not observed in the spectra." (Analysis and results)
3. **Derive main isotopologue columns and D/H**: Scale 13C isotopologue columns by 12C/13C=68 to get NH2CHO and HNCO; compute D/H ratios  
  > "Using the column densities derived for the $^{13}$C isotopologues and a standard $^{12}$C/$^{13}$C ratio, the deuterium fractionation in NH$_2$CHO is about 2% for the three deuterated forms" (Analysis and results)
   - assumption: 12C/13C = 68 (alternative ~30)  
  > "If the $^{12}$C/$^{13}$C ratio is lower ($\sim$30) as reported for glycolaldehyde by (cite: Jorgensen2016)" (Analysis and results)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASSIS** : line identification and LTE synthetic spectra  
  > "Using the CASSIS[^2] software, we identify several unblended lines" (Analysis and results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| N(NH2CDO) | 2.1e14 | within a factor of 2 | cm-2 | 2 | / NH$_2$CDO / 12 / 146 – 366 / 2.1 $\times$ 10$^{14}$ / |
| N(cis-NHDCHO) | 2.1e14 | within a factor of 2 | cm-2 | 2 | / cis-NHDCHO / 11 / 146 – 307 / 2.1 $\times$ 10$^{14}$ / |
| N(trans-NHDCHO) | 1.8e14 | within a factor of 2 | cm-2 | 2 | / trans-NHDCHO / 11 / 151 – 332 / 1.8 $\times$ 10$^{14}$ / |
| N(NH2 13CHO) | 1.5e14 | within a factor of 2 | cm-2 | 2 | / NH$_2$$^{13}$CHO / 10 / 152 – 428 / 1.5 $\times$ 10$^{14}$ / |
| N(DNCO) | 3.0e14 | within a factor of 2 | cm-2 | 2 | / DNCO / 4 / 150 – 751 / 3.0 $\times$ 10$^{14}$ / |
| N(HN13CO) | 4.0e14 | within a factor of 2 | cm-2 | 2 | / HN$^{13}$CO / 8 / 127 – 532 / 4.0 $\times$ 10$^{14}$ / |
| D/H of NH2CHO (each deuterated form) | ~2% | not stated | percent | 3 | the deuterium fractionation in NH$_2$CHO is about 2% for the three deuterated forms and the DNCO/HNCO ratio is similar ($\sim$1%). |
| HNCO/NH2CHO ratio | ~3 | not stated | dimensionless | 3 | Our derived ratio in IRAS16293 for HNCO/NH$_2$CHO, $\sim$3 |

## Qualitative findings

- The deuterated species emit from a similar compact region near source B, and HNCO and NH2CHO are spatially correlated.  
  > "The emission of the different lines clearly arise from a similar compact region in the vicinity of IRAS16293B." (Analysis and results)

## Claim tuples

- H: Deuterated formamide and DNCO can be detected in a low-mass protostar | E: Search PILS Band 7 spectra at source B | R: Several unblended lines of NH2CDO, cis/trans-NHDCHO and DNCO found | F: First ISM detections of these isotopologues | **supported**
- H: HNCO and NH2CHO are chemically related and form on grains | E: Compare deuteration and spatial distributions | R: Similar D/H and similar spatial distributions | F: Favours grain-surface formation, gas-phase routes not ruled out | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Gas-phase route of Barone et al. cannot yet be ruled out; HDCO/H2CO from PILS needed  
  > "Further studies are, however, needed to rule out gas phase routes." (Discussion and conclusion)
- Caveat (inferred, ours): Tex fixed at 300 K with limited constraint from deuterated lines
- Caveat (inferred, ours): Column density uncertainties are a rough factor of 2
- Caveat (inferred, ours): Upper limits and optical depth treated by eye
- Caveat (inferred, ours): Calibration and imaging fully deferred to a then-unpublished paper

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: PILS calibrated data cubes and reduction details
- Missing: Exact extraction aperture and baseline treatment
- Data volume (inferred): Tens to hundreds of GB for Band 7 12m+ACA cubes
- Score (inferred): 3/5, Clear LTE grid recipe and tables of lines, but data reduction and aperture details are external or unstated.
- Rediscovery candidate: no, Reduction is only in a companion paper and parts of the analysis are by-eye.

## Links

- Method: (cite: Jorgensen2016) (PILS survey description and data reduction)
- Companion: (cite: Lykke2016) (Same extraction position and source size)
- Related: PILS (Protostellar Interferometric Line Survey)

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 26,
  "rate": 0.4
 },
 "evidence_ok": true
}
```
