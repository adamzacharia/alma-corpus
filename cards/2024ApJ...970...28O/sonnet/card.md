# CH<SUB>3</SUB>OH and Its Deuterated Species in the Disk/Envelope System of the Low-mass Protostellar Source B335

`2024ApJ...970...28O` | The Astrophysical Journal 2024 | first author: Okoda, Yuki | arXiv: 2405.16744 | DOI: 10.3847/1538-4357/ad4d88

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry
- Question: What are the abundance ratios of CH3OH and its deuterated species, and the infall-rotation kinematics, in the disk/envelope system of the protostar B335 at 5 au resolution?  
  > "We derive the column densities and abundance ratios of the above species at 6 positions in the disk/envelope system as well as the continuum peak." (abstract)
- Target **B335 (IRAS 19347+0727)**: coordinates _not stated_; z/distance 165 pc  
  > "The distance to B335 is reported to be 165 pc, based on the Gaia DR2 parallax data (cite: Watson(2020))." (2 Target: B335); distance from Gaia DR2 parallax (Watson 2020)  
  > "The distance to B335 is reported to be 165 pc, based on the Gaia DR2 parallax data (cite: Watson(2020))." (2 Target: B335)

## Data provenance

- ALMA projects: 2018.1.01311.S
- bands: Band 6  
  > "Single-point ALMA observations toward B335 were carried out with the Band 6 receiver in the four execution blocks of the Cycle 6 operation" (3 Observation)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.03'' (5 au); beams 0.032-0.033'' x 0.026-0.028''  
  > "at a resolution of 0.03$''$ (5 au)" (abstract)
- max recoverable scale: 0.3''  
  > "Since the maximum recoverable scale is 0.3$''$ for these observations" (3 Observation)
- sensitivity: 1.0 mJy/beam/channel; spectral resolution 0.544-0.691 km/s  
  > "The spectral resolution is 0.544-0.691 km s$^{-1}$, and the root-mean-square noise is 1.0 mJy beam$^{-1}$channel$^{-1}$." (3 Observation)
- time on source: _not stated_
- observing dates: June 10, 12, 13, 23, 2019  
  > "on June 10, 12, 13, and 23 in 2019" (3 Observation)
- pi or archival as stated: PI Muneaki Imai; data originally observed by Okoda et al. 2022  
  > "(PI: Muneaki Imai)" (Acknowledgments)
- Line: CH3OH 18(3,15)-18(2,16), A (247.610918 GHz)
- Line: CH2DOH 4(2,2)-4(1,3), e0 (244.8411349 GHz)
- Line: CHD2OH 4(1,2)-4(0,1), o1-e0 (247.2524160 GHz)
- Line: CH3OD 5_1-4_0, E (245.142988 GHz)
- Line: HCOOH 12(0,12)-11(0,11) (262.1034810 GHz)
- External data: CH2DOH Sμ² measured experimentally (SUMIRE)  
  > "Since the $S\mu^2$ values of CH$_2$DOH were recently measured with the laboratory experiment (cite: Oyama et al.(2023))" (2 Target: B335) [from Oyama et al.(2023)]
- External data: CHD2OH Sμ² and spectroscopy from theory/CDMS  
  > "those of CHD$_2$OH with the theoretical calculation (cite: Coudert et al.(2021))" (2 Target: B335) [from Coudert et al.(2021)]
- External data: CH3OD Sμ²  
  > "For CH$_3$OD, we employ the $S\mu^2$ value calculated by (cite: Anderson et al.(1988))." (4.1 Column Densities) [from Anderson et al.(1988)]
- External data: H2 column density 5.66e23 cm^-2  
  > "the H$_2$ column density of 5.66$\times$10$^{23}$ cm$^{-2}$ reported by (cite: Imai et al.(2016))" (4.1 Column Densities) [from Imai et al.(2016)]
- External data: Systemic velocity 8.34 km/s  
  > "the systemic velocity is 8.34 km s$^{-1}$(cite: Yen et al.(2015b))" (6 Distributions and Velocity Maps) [from Yen et al.(2015b)]

## Processing

### Calibration

- pipeline or manual: CASA with a modified version of the ALMA calibration pipeline  
  > "as well as a modified version of the ALMA calibration pipeline" (3 Observation)
- casa version: CASA 5.8.0  
  > "Common Astronomy Software Applications package (CASA) 5.8.0" (3 Observation)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: phase self-cal on continuum, solutions applied to line data; four EBs combined in uv plane  
  > "We combined four visibility data in the $uv$ plane after phase self-calibration using each continuum data and the application of their solution to the spectral line data." (3 Observation)

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
- final beam: 0.030''x0.023'' for moment maps; per-line beams in Table 1  
  > "with the synthesized beam size (0.030$''$$\times$0.023$''$: Table [1](#observation))" (4 Deuterated CH3OH)
- final rms: 1.0 mJy/beam/channel  
  > "the root-mean-square noise is 1.0 mJy beam$^{-1}$channel$^{-1}$" (3 Observation)

### Inherited from earlier work

- Further observation parameters (calibrators, primary beam, correlator setups)  
  > "Further observation parameters (calibrators, primary beamwidth, and correlator setups etc.) are described elsewhere (cite: Okoda et al.(2022))." (3 Observation) [from Okoda et al.(2022)]
- LTE column density equations including dust opacity  
  > "we use the same equations as those reported by (cite: Okoda et al.(2022)), assuming the local thermodynamic equilibrium (LTE) condition" (4.1 Column Densities) [from Okoda et al.(2022)]
- FERIA infalling-rotating envelope model code  
  > "a general-purpose computer code FERIA (Flat Envelope model with Rotation and Infall under Angular momentum conservation) developed by (cite: Oya et al.(2022))" (7 Kinematics) [from Oya et al.(2022)]

### Not stated but needed to reproduce (our reading)

- Imaging task, weighting/robust, cell and image size, deconvolver settings
- Continuum subtraction method and line-free channels
- Self-calibration solution intervals
- Exact pipeline version and flux calibrator
- Dust continuum intensity values and T_dust derivation used in tau_dust
- FERIA grid step sizes and the detailed chi2 definition
- Partition functions used
- Sμ² SUMIRE for CHD2OH is unpublished (Oyama et al. in prep)

## Analysis recipe

1. **Extract line spectra and fit Gaussians**: Spectra from 7 rectangular areas (0.03''x0.05'') along P.A. 5 deg; Gaussian fits for peak intensity and width  
  > "towards 7 rectangle areas (0.03$''$$\times$0.05$''$) along the disk/envelope direction (P.A. 5$^\circ$) including the continuum peak position" (4.1 Column Densities)
   - software: CASA
   - fitting: Gaussian fitting  
  > "The observed intensities and the velocity widths are obtained by Gaussian fitting." (Gaussian fitting)
   - validation: _not stated_
2. **Derive T and N by LTE with dust opacity**: LTE fit with line and dust optical depth, chi2 minimisation for CH3OH and CH2DOH; CHD2OH and CH3OD use CH3OH temperature  
  > "in the calculation of the column densities of CHD$_2$OH and CH$_3$OD, we assume the CH$_3$OH temperature obtained for each position" (4.1 Column Densities)
   - assumption: gas and dust well mixed, T_gas = T_dust; LTE  
  > "assuming that the gas and dust are well mixed and the gas temperature is equal to the dust temperature" (4.1 Column Densities)
   - fitting: chi2; 1 sigma errors; ±15 K temperature range for CHD2OH and CH3OD  
  > "we estimate the errors of their column densities, based on the assumed temperature range of $\pm$15 K from the CH$_3$OH temperature" (4.1 Column Densities)
   - validation: Compared Sμ² JPL/CDMS vs SUMIRE  
  > "we here note the effects on the results for the different $S\mu^2$ values for the CH$_2$DOH ($S\mu^2_{\rm \ SUMIRE}$ vs. $S\mu^2_{\rm \ JPL}$) and CHD$_2$OH ($S\mu^2_{\rm \ SUMIRE}$vs. $S\mu^2_{\rm \ CDMS}$) lines" (An Effect of $S\mu^2$ on the Column Densities)
3. **Compute abundance ratios**: Ratios of column densities at each offset; D/H = CH2DOH/CH3OH divided by 3  
  > "The $\lbrack$CH$_2$DOH$\rbrack$/$\lbrack$CH$_3$OH$\rbrack$ ratio can be converted to the D/H ratio by dividing by 3" (8.1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit infall-rotation kinematics**: FERIA IRE/Keplerian/combined models fit to the data cube by reduced chi2 for CH3OH 18(3,15) and HCOOH  
  > "We perform the $\chi^2$ test to obtain the best-fit model parameters on the molecular-line data cube, where the intensities are higher than 3$\sigma$ noise level" (7 Kinematics)
   - software: FERIA
   - parameter: Disk/envelope height 20 au, R_out 24 au (CH3OH) and 10 au (HCOOH), P.A. 5 deg, i 70-90 deg, Mstar 0.02-0.08 Msun, r_CB 2-9 au  
  > "IRE | CH$_3$OH  | 0.02-0.08 | 2-9 | 70-90 | $r_{\rm CB}$ | 24" (Table 3)
   - fitting: reduced chi2 grid  
  > "We perform the $\chi^2$ test to obtain the best-fit model parameters on the molecular-line data cube, where the intensities are higher than 3$\sigma$ noise level" (Kinematics of the Disk/Envelope System with FERIA)
   - validation: PV diagrams compared with best-fit model; consistency with Imai+2019, Oya+2022, Bjerkeli+2019  
  > "Thus, the small $M_{\rm star}$ and $r_{\rm CB}$ values obtained in this study are consistent with those reported in the previous works." (7.1)

## Software

- **CASA** 5.8.0: data reduction  
  > "The data reduction was performed with Common Astronomy Software Applications package (CASA) 5.8.0" (3 Observation)
- **FERIA** : infalling-rotating envelope kinematic modelling  
  > "a general-purpose computer code FERIA" (7 Kinematics)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [CH2DOH]/[CH3OH] in envelope | 0.09-0.38 | not stated | dimensionless | 3 | in the envelope are in the range of \[0.09-0.38\] |
| [CH2DOH]/[CH3OD] | 4.9-15 | not stated | dimensionless | 3 | are in the range of \[4.9-15\] and \[0.14-0.29\] |
| [CHD2OH]/[CH2DOH] | 0.14-0.29 | not stated | dimensionless | 3 | are in the range of \[4.9-15\] and \[0.14-0.29\] |
| CH3OH best-fit Mstar, r_CB, i | 0.07 Msun, 3 au, 70 deg (reduced chi2 0.88) | not stated | Msun, au, deg | 4 | where $M_{\rm star}$, $r_{\rm CB}$($=R_{\rm in}$), and $i$ are 0.07$M_\odot$, 3 au, and 70$^\circ$, respectively |
| HCOOH IRE best-fit Mstar | 0.04 Msun (r_CB 7 au, i 90 deg, chi2 0.81) | not stated | Msun | 4 | The best-fit value of $M_{\rm star}$ is 0.04 $M_\odot$, where the reduced $\chi^2$ value is 0.81. |
| CH2DOH column density at -0.03'' (SUMIRE) | 3.6e18 cm^-2 at 161 K | +1.1/-0.6 | cm^-2 | 2 | 161$^{+8}_{-6}$ K and 3.6$^{+1.1}_{-0.6}\times$10$^{18}$ cm$^{-2}$ |

## Qualitative findings

- CH3OH and its deuterated species have ring distributions within 24 au with a central depression due to dust opacity.  
  > "They have a ring distribution within the radius of 24 au with the intensity depression at the continuum peak." (abstract)

## Claim tuples

- H: Does B335 show high CH2DOH/CH3OH compared with other low-mass sources? | E: LTE column densities at 6 envelope positions | R: [CH2DOH]/[CH3OH] 0.09-0.38 (D/H 0.03-0.13) | F: Relatively high, possibly related to protostellar youth; caveat from optically thick CH3OH | **partially**
- H: Is [CH2DOH]/[CH3OD] above the statistical 3 despite high temperature? | E: Column density ratios | R: 4.9-15 | F: Ratio does not depend only on temperature but on physical environment history | **supported**
- H: Protostellar mass and disk size from kinematics | E: FERIA fits to CH3OH and HCOOH cubes | R: Mstar 0.03-0.07 Msun, r_CB <7 au | F: Young protostar with tiny disk; Keplerian disk not confirmed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Experimental Sμ² values for CH2DOH became available, enabling reliable column densities.  
  > "reliable derivations of their column densities are now possible by making use of them" (2 Target: B335)
- Alternative: HCOOH tested as IRE (case 1) versus Keplerian disk (case 2); cannot discriminate.  
  > "our observation is not able to determine which of Case 1 and Case 2 is more appropriate for the HCOOH distribution" (7.2.2)
- How they decided it was enough: _not stated_
- Limitation (authors): CH3OH column density may be underestimated due to high optical depth; optically thin isotopologue needed.  
  > "the derived D/H ratio could be due to underestimating the column density of CH$_3$OH" (8.1)
- Caveat (inferred, ours): LTE with T_gas=T_dust under high dust opacity and optically thick CH3OH is uncertain
- Caveat (inferred, ours): CHD2OH and CH3OD temperatures assumed from CH3OH
- Caveat (inferred, ours): Sμ² SUMIRE for CHD2OH unpublished
- Caveat (inferred, ours): Single data set; no formal model comparison

## Reproducibility

- Data public (paper): Archival project 2018.1.01311.S cited  
  > "ADS/JAO.ALMA# 2018.1.01311.S (PI: Muneaki Imai)" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: line-free channels
- Missing: self-cal details
- Missing: Okoda+2022 setup details
- Missing: Unpublished CHD2OH Sμ²
- Data volume (inferred): ~50-150 GB (four Band 6 EBs)
- Score (inferred): 5/5, Public data and equations given, but imaging and processing details are deferred to Okoda+2022.
- Rediscovery candidate: no, Imaging recipe is incomplete and key Sμ² values are unpublished.

## Links

- Method: Okoda et al.(2022) (observation setup and LTE equations)
- Method: Oya et al.(2022) (FERIA code)
- Companion: Imai et al.(2019) (previous kinematic analysis of B335)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
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
  "facts": 70,
  "stated": 40,
  "rate": 0.571
 },
 "evidence_ok": true
}
```
