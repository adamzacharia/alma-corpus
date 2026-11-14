# The ALMA Protostellar Interferometric Line Survey (PILS). First results from an unbiased submillimeter wavelength line survey of the Class 0 protostellar binary IRAS 16293-2422 with ALMA

`2016A&A...595A.117J` | Astronomy and Astrophysics 2016 | first author: Jørgensen, J. K. | arXiv: 1607.08733 | DOI: 10.1051/0004-6361/201628648

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, star_formation
- Question: What is the chemical complexity of the Class 0 protostellar binary IRAS 16293-2422 on solar-system scales, and how are glycolaldehyde, its isomers and isotopologues formed?  
  > "The goal is to introduce a systematic survey, “Protostellar Interferometric Line Survey (PILS)”, of the chemical complexity of one of the nearby astrochemical templates" (abstract)
- Target **IRAS 16293-2422 (components A and B)**: coordinates pointing center 16h32m22.72s, -24d28m34.3s (J2000)  
  > "We therefore adopt a distance of 120 pc throughout this paper." (2 An overview of IRAS 16293$-$2422); "$\alpha_{\rm J2000}=$16$^{\text{h}}$32$^{\text{m}}$22.72s; $\delta_{\rm J2000}=-$24$^\circ$28$'$34.3$''$" (3.1 Data, calibration and imaging); z/distance 120 pc  
  > "We therefore adopt a distance of 120 pc throughout this paper." (2 An overview of IRAS 16293$-$2422); "$\alpha_{\rm J2000}=$16$^{\text{h}}$32$^{\text{m}}$22.72s; $\delta_{\rm J2000}=-$24$^\circ$28$'$34.3$''$" (3.1 Data, calibration and imaging); distance from adopted from extinction and VLBI parallax measurements of the rho Oph cloud (Rivera et al. 2015 cited)  
  > "We therefore adopt a distance of 120 pc throughout this paper." (2 An overview of IRAS 16293$-$2422); "$\alpha_{\rm J2000}=$16$^{\text{h}}$32$^{\text{m}}$22.72s; $\delta_{\rm J2000}=-$24$^\circ$28$'$34.3$''$" (3.1 Data, calibration and imaging)

## Data provenance

- ALMA projects: 2013.1.00278.S, 2012.1.00712.S
- bands: Band 7 (329-363 GHz) unbiased survey; Band 6 (~230 GHz) and Band 3 (~100 GHz) selected windows  
  > "selected windows in ALMA’s Bands 3 ($\approx$3 mm, or 100 GHz) and 6 ($\approx$1.3 mm, or 230 GHz) obtained in Cycle 1" (3 Observations)
- frequencies and spectral setup: Band 7: 18 settings of 1875 MHz (four 468.75 MHz windows), 0.244 MHz (~0.2 km/s) resolution, 1920 channels per window  
  > "In total 18 spectral settings were observed: each setting covers a bandwidth of 1875 MHz (over four different spectral windows, 468.75 MHz wide)." (3.1 Data, calibration and imaging)
- continuum bandwidth: _not stated_
- arrays: Band 7: 12 m array plus ACA (7 m); Bands 3 and 6: 12 m only  
  > "Data were obtained from both the array of 12 m dishes (typically 36–41 antennas in the array at the time of observations) and the “Atacama Compact Array (ACA)”" (3.1 Data, calibration and imaging); "For these settings only the 12-m array was utilised" (3.2 Band 3 and Band 6 data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beams ~0.4-0.7'' in Band 7; combined 0.5'' circular-beam dataset  
  > "a combined dataset with a circular restoring beam of 0.5$''$ was produced as well" (3.1 Data, calibration and imaging)
- max recoverable scale: _not stated_
- sensitivity: 7-10 mJy/beam/channel; 4-5 mJy/beam km/s  
  > "noise RMS for the combined datasets of about 7–10 mJy beam$^{-1}$ channel$^{-1}$" (3.1 Data, calibration and imaging)
- time on source: ~13 min per setting for 12 m, double for ACA  
  > "Each setting was observed with approximately 13 minutes integration on source" (3.1 Data, calibration and imaging)
- observing dates: Band 7 12 m: Apr-May 2015; ACA: 2014-2015; Bands 3/6: May-Jul 2014  
  > "three spectral setups were observed in Band 6 and Band 3 between May and July 2014" (3.2 Band 3 and Band 6 data)
- pi or archival as stated: PILS program, PI Jes K. Jørgensen  
  > "(PI: Jes K. Jørgensen)" (3 Observations)
- Line: glycolaldehyde, ethylene glycol (aGg', gGg'), acetic acid, CH3 18OH, isotopologues many (not stated)
- Other facility **JCMT TIMASSS single-dish**: single-dish spectra compared with ALMA  
  > "from JCMT observations taken as part of the larger single-dish TIMASSS survey" (4.2 Line emission)
- External data: Spectroscopy for glycolaldehyde and methyl formate (JPL catalog)  
  > "are provided by the JPL catalog" (5.2 Spectroscopic data) [from (cite: jpl)]
- External data: Ethylene glycol conformer spectroscopy (CDMS)  
  > "is provided by the Cologne Database for Molecular Spectroscopy" (5.2 Spectroscopic data) [from (cite: cdms1; cdms2)]
- External data: SgrB2(N) abundances relative to methanol and Garrod models  
  > "compares the derived column densities for methyl formate, glycolaldehyde, ethylene glycol, acetaldehyde and acetic acid relative to methanol for IRAS16293B, SgrB2(N)" (5.2 Comparison with models) [from (cite: belloche13); (cite: garrod13)]

## Processing

### Calibration

- pipeline or manual: standard CASA recipes with manual and automatic flagging  
  > "The calibration and imaging proceeded according to the standard recipes in CASA." (3.1 Data, calibration and imaging)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (or Ceres); bandpass J1517-2422; phase J1625-2527  
  > "Titan, or in a few instances Ceres, were used as flux calibrators" (3.1 Data, calibration and imaging)
- flux scale uncertainty: better than 5%  
  > "this suggests that the (flux) calibration accuracy is better than 5% for the ALMA observations." (3.1 Data, calibration and imaging)
- self calibration: phase-only self-cal on continuum, applied to cubes before 12m+ACA combination  
  > "A phase-only self-calibration was performed on the continuum datasets and applied to the full data cubes before combining the 12 m array and ACA datasets" (3.1 Data, calibration and imaging)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: statistical per-pixel fit of skewed Gaussian to flux-value distribution  
  > "the continuum subtraction is done in a statistical/iterative manner: for each pixel in a datacube the density distribution of flux-values is created" (3.2 Continuum subtraction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12 m and ACA combined before final imaging  
  > "before combining the 12 m array and ACA datasets and performing the final imaging" (3.1 Data, calibration and imaging)
- smoothing: combined dataset convolved to circular 0.5'' beam  
  > "a combined dataset with a circular restoring beam of 0.5$''$ was produced as well" (3.1 Data, calibration and imaging)
- final beam: _not stated_
- final rms: 4-5 mJy/beam km/s (Band 7)  
  > "uniform sensitivity of approximately 4–5 mJy beam$^{-1}$ km s$^{-1}$" (3.1 Data, calibration and imaging)

### Inherited from earlier work

- excitation temperature 300 K adopted from SV analysis  
  > "we adopt here an excitation temperature of 300 K, which appears to be required from modeling of isotopologues of formamide (NH$_2$CHO) isocyanic acid (HNCO)" (5.1 Excitation analysis) [from (cite: jorgensen12)]
- dust opacities for continuum column density  
  > "assuming typical dust opacities from (cite: ossenkopf94) with $\kappa_\nu=0.0182$ cm$^{2}$ g$^{-1}$ at 850 $\mu$m" (4.1 Continuum emission) [from (cite: ossenkopf94)]

### Not stated but needed to reproduce (our reading)

- CASA version and exact calibration scripts
- tclean weighting/robust, cell and image size, deconvolver, masks
- Reference continuum-subtraction code details
- Synthetic-spectrum code and fitting procedure, uncertainties on column densities
- Details of line width/LSR velocity fixed values used
- Rotation diagram fit details

## Analysis recipe

1. **estimate and subtract continuum**: per-pixel Gaussian then skewed Gaussian fit to flux distribution  
  > "a skewed Gaussian is fitted to the part of the distribution within $F\pm 3\Delta F$" (3.2 Continuum subtraction)
   - software: CASA
   - parameter: fit range F±3ΔF; accuracy within 2σ  
  > "the continuum level can be estimated in this manner to be accurate to within 2$\sigma$" (3.2 Continuum subtraction)
   - fitting: _not stated_
   - validation: experiments with observed cubes and synthetic models  
  > "Experiments with the observed cubes and synthetic models suggest" (3.2 Continuum subtraction)
2. **test LTE with non-LTE methanol excitation**: Radex calculations of Tex vs Tkin for CH3OH, rms deviation over 82 transitions  
  > "we use the escape probability code *Radex* (cite: vandertak07radex) to solve the radiative transfer problem for the largest complex molecule methanol" (5.1 Excitation analysis)
   - software: Radex
   - parameter: Tkin 50, 100, 300 K; n 1e6-1e12 cm-3  
  > "models with $T_{\rm kin}$ of 50, 100 and 300 K, respectively, with densities varying from $10^6-10^{12}$ cm$^{-3}$" (5.1 Excitation analysis)
   - fitting: _not stated_
   - validation: deviations <15% above 3e10 cm-3  
  > "the deviations are less than 15% for these three kinetic temperatures" (5.1 Excitation analysis)
3. **derive column densities by LTE synthetic spectra and rotation diagrams**: compare LTE synthetic spectra to spectra at half beam offset from IRAS16293B; rotation diagrams for Band 3 lines  
  > "the approach taken for this analysis, as well as for other species in Bands 6 and 7, is to calculate synthetic spectra of the targeted molecules and directly compare those to the extracted spectra" (5.1 Excitation analysis)
   - parameter: Tex = 300 K; source size 0.5''; fixed line width and LSR velocity  
  > "We adopt a source size of 0.5$''$" (5.1 Excitation analysis)
   - assumption: LTE, 16O/18O = 560, vibrational corrections (1.47 glycolaldehyde vs JPL; 4.02 ethylene glycol; 1.38 gGg')  
  > "the main species needs to be increased by a factor 1.47 compared to estimates derived using the partition function given in the JPL catalog" (5.2 Spectroscopic data)
   - fitting: by-eye comparison of synthetic and observed spectra; linear fits for rotation diagrams  
  > "The total column density of the molecule and its kinetic temperature can thus be derived from linear fits to plots of $\ln \left(N_u / g_u\right)$ as function of $E_{\rm up}$" (Line identification, temperatures and column densities)
   - validation: no lines predicted where none observed  
  > "A strong test of the assignments is that no lines are predicted to show emission at frequencies where none is seen in the spectra." (5.2 Line identification)
4. **isotopologue ratios**: synthetic spectra of 13C and D isotopologues with vibrational corrections 3.29 (OD) and 2.80  
  > "the column density of the OD isotopologue needs to be increased by 3.29 and those of all other isotopologues by 2.80" (5.3 Isotopologues)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration and imaging  
  > "The calibration and imaging proceeded according to the standard recipes in CASA." (3.1 Data, calibration and imaging)
- **Radex** : test of LTE for methanol  
  > "we use the escape probability code *Radex* (cite: vandertak07radex)" (5.1 Excitation analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| flux calibration accuracy | <5 | not stated | % | 0 | the (flux) calibration accuracy is better than 5% |
| number of lines | ~10,000 | not stated | lines | 0 | approximately 10,000 lines are seen toward the position half a beam away from the continuum peak |
| CH3 18OH column density | 4e16 | not stated | cm-2 | 3 | the derived column density for CH$_3$$^{18}$OH is $4\times 10^{16}$ cm$^{-2}$ |
| glycolaldehyde rotation temperature (Band 3) | 284 | 27 | K | 3 | Glycolaldehyde / $284\pm 27$ K |
| glycolaldehyde column density (Band 7) | 6.8e16 | not stated | cm-2 | 3 | $6.8\times 10^{16}$ cm$^{-2}$ |
| D/H ratio of glycolaldehyde | 4.1-5.2 | not stated | % | 4 | the D/H ratio for glycolaldehyde is 4.1–5.2% |
| 12C/13C ratio | 24-35 (~30) | not stated | dimensionless | 4 | or a $^{12}$C/$^{13}$C ratio of 24–35 |
| lower limit H2 column toward B | >1.2e25 | not stated | cm-2 | 0 | > 1.2 \times 10^{25}~{\rm cm}^{-2} |

## Qualitative findings

- Glycolaldehyde and ethylene glycol are overabundant relative to methanol vs SgrB2(N); gGg' conformer first detected in the ISM  
  > "with the detection of one of these, the $gGg'$ conformer, the first reported detection in the ISM" (6 Summary)

## Claim tuples

- H: Is LTE valid at the scales probed? | E: Radex methanol excitation vs density | R: deviations <15% above 3e10 cm-3 | F: LTE is a good approximation | **supported**
- H: Is glycolaldehyde deuteration uniform across functional groups? | E: fit D isotopologues | R: D/H ~5% for all | F: no difference between groups, in contrast to methanol | **supported**
- H: Is 12C/13C in glycolaldehyde ISM-like? | E: fit 13C isotopologues | R: ~30 | F: lower than local ISM 68 | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: line confusion makes line-free channels and rotation diagrams impractical, so synthetic spectra used  
  > "For this reason it is not practical to identify individual lines and create rotation diagrams based on those." (5.1 Excitation analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Abundances relative to H2 highly uncertain as continuum is optically thick  
  > "even as a limit the abundance with respect to H$_2$ is highly uncertain" (5.1 Excitation analysis)
- Caveat (inferred, ours): Fits by eye without formal uncertainties
- Caveat (inferred, ours): Single Tex = 300 K assumed
- Caveat (inferred, ours): Optically thick continuum and offset position affect column densities

## Reproducibility

- Data public (paper): data available via ALMA archive  
  > "The data are available through the ALMA archive at https://almascience.eso.org/aq." (footnote)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: synthetic spectrum code and fit details
- Missing: uncertainties on column densities
- Data volume (inferred): several hundred GB to TB (18 Band 7 settings with 12m+ACA plus Bands 3 and 6)
- Score (inferred): 4/5, Public data and clear approach but imaging and fitting details missing.
- Rediscovery candidate: no, Data are public but processing and fitting recipe are not complete enough.

## Links

- Method: (cite: coutens16) (PILS formamide analysis)
- Method: (cite: lykke16) (PILS companion analysis)
- Companion: (cite: jorgensen12) (SV glycolaldehyde detection)
- Related: TIMASSS
- Related: PILS

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 44,
  "rate": 0.638
 },
 "evidence_ok": true
}
```
