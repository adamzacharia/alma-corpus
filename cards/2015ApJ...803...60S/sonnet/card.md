# ALMA Multi-line Observations of the IR-bright Merger VV 114

`2015ApJ...803...60S` | The Astrophysical Journal 2015 | first author: Saito, Toshiki | arXiv: 1501.07373 | DOI: 10.1088/0004-637X/803/2/60

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, astrochemistry
- Question: Distribution and kinematics of diffuse and dense molecular gas in the merger VV 114, and spatial variation of excitation conditions across the two merging disks  
  > "The main aim of this study is to investigate the distribution and kinematics of the diffuse and dense molecular gas and to quantify the spatial variation of the excitation conditions across the two merging disks." (INTRODUCTION)
- Target **VV 114**: coordinates _not stated_; z/distance D = 82 Mpc (86 Mpc also quoted in Results)  
  > "VV 114 is a gas-rich (cite: yun94) nearby (D = 82 Mpc; 1.0$''$ = 400 pc) interacting system" (INTRODUCTION); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00467.S
- bands: Band 3 and Band 7  
  > "The band 3 and band 7 receivers were tuned to the $^{12}$CO (1–0), $^{13}$ CO (1–0), $^{12}$CO (3–2), HCN (4–3), and HCO$^+$ (4–3) line emissions in the upper side band" (2 OBSERVATIONS AND DATA REDUCTION)
- frequencies and spectral setup: Four 1.875 GHz spws with 3840 channels, ~7.5 GHz total coverage; 0.488 MHz per channel  
  > "Each spectral window had a bandwidth of 1.875 GHz with 3840 channels, and two spectral windows were set to each sideband to achieve a total frequency coverage of $\sim$ 7.5 GHz in these observations." (2 OBSERVATIONS AND DATA REDUCTION)
- continuum bandwidth: _not stated_
- arrays: 14-20 12 m antennas, compact and extended configurations  
  > "using fourteen – twenty 12 m antennas" (2 OBSERVATIONS AND DATA REDUCTION)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.97''x1.35'' (CO 1-0), 1.64''x1.17'' (CO 3-2), 0.46''x0.38'' (HCN 4-3)  
  > "1.97$''$ $\times$ 1.35$''$ (P.A. = 82.3 deg.), 1.77$''$ $\times$ 1.20$''$ (P.A. = 85.8 deg.), 1.64$''$ $\times$ 1.17$''$ (P.A. = 112.6 deg.), and 0.46$''$ $\times$ 0.38$''$ (P.A. = 51.5 deg.)" (2 OBSERVATIONS AND DATA REDUCTION)
- max recoverable scale: ~8'' (Band 3), ~7'' (Band 7)  
  > "The MRS of our observations are $\sim$ 8$''$ and $\sim$ 7$''$ in band 3 and band 7, respectively" (2 OBSERVATIONS AND DATA REDUCTION)
- sensitivity: 30 km/s channel rms 1.0 mJy/beam (B3), 0.8 mJy/beam (B7); continuum 0.05, 0.11, 0.07 mJy/beam  
  > "the rms noise levels of the channel maps with 30 km s$^{-1}$ resolution are 1.0 mJy beam$^{-1}$ and 0.8 mJy beam$^{-1}$, respectively." (2 OBSERVATIONS AND DATA REDUCTION)
- time on source: ~40 min (Band 3), ~80 min (Band 7)  
  > "The on-source times of band 3 and band 7 were about 40 minutes and 80 minutes" (2 OBSERVATIONS AND DATA REDUCTION)
- observing dates: Nov 2011 - Jul 2012  
  > "The $^{12}$CO (1–0) data were obtained on November 6, 2011 and May 4, 2012 in the compact and extended configurations, respectively." (2 OBSERVATIONS AND DATA REDUCTION)
- pi or archival as stated: Cycle 0 program, PI D. Iono  
  > "ALMA cycle 0 program (ID = 2011.0.00467.S; PI = D. Iono)" (2 OBSERVATIONS AND DATA REDUCTION)
- Line: 12CO 1-0 (115.27 GHz)
- Line: 13CO 1-0 (110.20 GHz)
- Line: 12CO 3-2 (345.80 GHz)
- Line: HCN 4-3 (354.51 GHz)
- Line: HCO+ 4-3 (356.73 GHz)
- Line: CH3OH 2k-1k (96.74 GHz)
- Line: CS 2-1 (97.98 GHz)
- Line: CN 1(3/2)-0(1/2) (113.49 GHz)
- Line: CS 7-6 (342.88 GHz)
- Other facility **miniTAO/ANIR**: Pa-alpha and Ks-band images (SFR, nuclei positions)  
  > "Column 3: The Pa$\alpha$ flux (cite: tat12)." (Table 10)
- External data: Single-dish/SMA/JCMT fluxes used for missing-flux estimates and dust temperature 39.4 K  
  > "The estimated missing flux in our ALMA observation is 21 $\pm$ 1 % (cite: wil08; sai13)." (3.2 12CO (3-2)) [from (cite: wil08; sai13)]
- External data: 8.44 GHz continuum flux  
  > "Column 2: 8.44 GHz continuum flux (cite: cnd91)." (Table 3) [from (cite: cnd91)]
- External data: Pa-alpha luminosity from miniTAO  
  > "Column 3: The Pa$\alpha$ flux (cite: tat12)." (Table 10) [from (cite: tat12)]
- External data: HCN(4-3)/HCN(1-0) = 0.63  
  > "HCN (4–3)/HCN (1–0) = 0.63 (cite: ima07)" (5.1 Molecular Gas Mass Derivation) [from (cite: ima07)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Delivered calibrated data used  
  > "We used the delivered calibrated data and mapping was accomplished using the `clean` task in `CASA`" (2 OBSERVATIONS AND DATA REDUCTION)
- flux calibrator: Uranus (Neptune for band 3); J1924-292 bandpass, J0132-169 phase  
  > "J1924-292, J0132-169, Uranus (Neptune for band 3 observations) were used for bandpass, phase, and flux calibrations." (2 OBSERVATIONS AND DATA REDUCTION)
- flux scale uncertainty: ~5% Band 3, ~10% Band 7  
  > "The systematic error on the absolute flux is estimated to be $\sim$ 5% and $\sim$ 10% for both sidebands in band 3 and band 7, respectively." (2 OBSERVATIONS AND DATA REDUCTION)
- self calibration: _not stated_

### Imaging

- task: CASA clean; maps analyzed with MIRIAD and AIPS  
  > "All maps in this paper, except for $^{12}$CO (3–2), are reconstructed with a Briggs weighting (cite: b&c92) and analyzed with `MIRIAD` and `AIPS`." (2 OBSERVATIONS AND DATA REDUCTION)
- deconvolver: _not stated_
- weighting robust: Briggs (robust not stated); uniform for CO(3-2)  
  > "The $^{12}$CO (3–2) images are created with uniform weighting (see §[3.2](#co32))." (2 OBSERVATIONS AND DATA REDUCTION)
- uv taper: _not stated_
- cell size: 0.3''/pixel Band 3; 0.08''/pixel Band 7  
  > "the pixel scales of the band 3 and the band 7 images are set to 0.3$''$/pixel and 0.08$''$/pixel, respectively" (2 OBSERVATIONS AND DATA REDUCTION)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane subtraction; continuum from line-free channels  
  > "The continuum emission was subtracted in the $uv$-plane before making the line images." (2 OBSERVATIONS AND DATA REDUCTION)
- line free channels: _not stated_
- primary beam correction: Applied  
  > "All images which we constructed are corrected for primary beam attenuation." (2 OBSERVATIONS AND DATA REDUCTION)
- array combination: Compact+extended combined for 340 GHz low-res continuum  
  > "using the combined data (compact + extended) and the extended configuration data, respectively" (3.3 Continuum Emission)
- smoothing: uv ranges matched (13.5 and 40.0 kλ min) and convolved to 2.0''x1.5'' (B3) and 1.2''x1.0'' (B7)  
  > "The shortest baseline lengths are set to 13.5 k$\lambda$ and 40.0 k$\lambda$ for the molecular lines in the band 3 and the band 7, respectively" (4 Spatially resolved line ratios)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Earlier HCN/HCO+ (4-3) analysis, AGN identification and 200 pc resolution results  
  > "We concluded in from their source size, line widths, and the relative strengths of HCN (4–3) and HCO$^+$ (4–3) that the unresolved eastern nucleus harbors an obscured AGN" (3.2 HCN (4-3) and HCO+ (4-3)) [from Iono et al. 2013 (cite: ion13)]
- Dust mass formula, kappa and Td  
  > "We assumed a dust emissivity, $\kappa_{340} = 0.9~\rm{cm^2~g^{-1}}$, and the dust temperature $T_{\rm{d}}$ of 39.4 K (cite: wil08)." (5.4 Dust Mass) [from (cite: wil08)]
- alpha_CO for U/LIRGs  
  > "We use the conversion factor known to be appropriate for U/LIRGs (cite: d&s98)." (5.1 Molecular Gas Mass Derivation) [from (cite: d&s98)]

### Not stated but needed to reproduce (our reading)

- Briggs robust value for each cube
- Line-free channels used for continuum
- CASA version and clean parameters (threshold, masks, iterations)
- How multi-configuration data were combined
- Exact box positions and Gaussian fit details
- RADEX script details (line widths, chi2 error budget)
- Pa-alpha extinction correction and SFR calibration choices
- Whether pipeline products were re-calibrated

## Analysis recipe

1. **Image line cubes and continuum**: CASA clean with Briggs (uniform for CO 3-2), uv continuum subtraction, primary beam correction, 5 or 30 km/s channels  
  > "We made the data cubes with a velocity width of 5 km s$^{-1}$ for the $^{12}$CO line and 30 km s$^{-1}$ for the other lines." (2 OBSERVATIONS AND DATA REDUCTION)
   - software: CASA, MIRIAD, AIPS
   - fitting: _not stated_
   - validation: Missing flux compared with single-dish/SMA/JCMT  
  > "The estimated missing flux in our ALMA observation is 21 $\pm$ 1 % (cite: wil08; sai13)." (3.2 12CO (3-2))
2. **Measure box-summed line ratios**: Match uv range and beam, convolve, convert to K km/s, sum in 2.0'' R boxes and 1.2'' S boxes, ratio where both >3 sigma; multi-Gaussian fits to spectra  
  > "We carried out a multi Gaussian fit (one - three components) to reproduce the box-summed spectra" (4 Spatially resolved line ratios)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive H2 and dense gas masses**: M = alpha L'  
  > "We also calculate the dense gas mass $M_{\rm{dense}}$ using $\alpha_{\rm{HCN}}$ = 10 M$_{\odot}~\rm{(K~km~s^{-1}~pc^2)^{-1}}$ (cite: g&s04)" (5.1 Molecular Gas Mass Derivation)
   - assumption: alpha_CO = 0.8; alpha_HCN = 10; uncertainty up to factor of two  
  > "bearing in mind that the uncertainties could be as large as a factor of two" (5.1 Molecular Gas Mass Derivation)
   - fitting: _not stated_
   - validation: alpha_CO consistent with Sliwa et al. 2013 value  
  > "This is consistent with the value derived by (cite: slw13) in VV 114" (5.1 Molecular Gas Mass Derivation)
4. **Non-LTE radiative transfer modeling**: RADEX grid in Tkin, nH2, N(H2) (case 1) or [HCN]/[HCO+] (case 2); chi2 minimization  
  > "varied the parameters until the residuals between the observed line fluxes and the modeled line fluxes are minimized in a $\chi^2$ sense" (5.2 Radiative Transfer Analysis using RADEX)
   - software: RADEX
   - parameter: Case 1: Tkin 5-300 K step 5, n 10^2-10^5; case 2: Tkin 5-400 K, n 10^3-10^7  
  > "$T_{\rm{kin}}$ = 5 – 400 K using steps of d$T_{\rm{kin}}$ = 5 K, $n_{\rm{H_2}}$ = $10^3$ – $10^7~\rm{cm^{-3}}$" (5.2 Radiative Transfer Analysis using RADEX)
   - assumption: [13CO]/[H2]=1.4e-6, [CO]/[13CO]=70, [CO]/[H2]=1e-4, [HCO+]/[H2]=1e-9; uniform sphere  
  > "we fixed \[$^{13}$CO\]/\[H$_2$\] = 1.4 $\times$ 10$^{-6}$ (cite: dav13) and \[CO\]/\[$^{13}\rm{CO}$\] = 70" (5.2 Radiative Transfer Analysis using RADEX)
   - fitting: chi2 grid; 95% confidence region chi2<7.81 (3 dof)  
  > "We list the results that are within the 95 % confidence level with 3-degree of freedom ($\chi^2 < 7.81$)" (5.2 Radiative Transfer Analysis using RADEX)
   - validation: _not stated_
5. **LTE filling factor, Tex, column density, abundances**: Tex from CO(1-0) with Phi=Tb/Tkin; optical depth and column density equations  
  > "Using $T_{\rm{kin}}$ estimated from the RADEX calculation (§[5.2](#chi)), we estimate the beam filling factor $\Phi_{\rm{A}}$" (5.3 Filling factor and Column Density under LTE)
   - assumption: 13CO and CO from same cloud; 12CO(1-0) optically thick  
  > "Assuming that the $^{13}$CO and CO arise from the same molecular cloud, and that the $^{12}$CO (1–0) is optically thick" (5.3 Filling factor and Column Density under LTE)
   - fitting: _not stated_
   - validation: _not stated_
6. **Dust and ISM mass from 340 GHz continuum**: Dust mass equation (wil08) and Scoville et al. 2014 RJ-tail ISM mass; compare with M_H2  
  > "we calculated the total ISM mass from the 340 GHz continuum emission (cite: scv14)" (5.4 Dust Mass)
   - assumption: kappa340 = 0.9 cm2/g (Draine & Lee), Td = 39.4 K  
  > "We assumed a dust emissivity, $\kappa_{340} = 0.9~\rm{cm^2~g^{-1}}$, and the dust temperature $T_{\rm{d}}$ of 39.4 K (cite: wil08)." (5.4 Dust Mass)
   - fitting: _not stated_
   - validation: M_ISM/M_H2 close to unity for resolved regions  
  > "the average $M_{\rm{ISM}}$/$M_{\rm{H_2}}$ = 0.9 $\pm$ 0.1" (5.4 Dust Mass)

## Software

- **CASA** : clean imaging  
  > "mapping was accomplished using the `clean` task in `CASA`" (2 OBSERVATIONS AND DATA REDUCTION)
- **MIRIAD** : map analysis  
  > "analyzed with `MIRIAD` and `AIPS`" (2 OBSERVATIONS AND DATA REDUCTION)
- **AIPS** : map analysis  
  > "analyzed with `MIRIAD` and `AIPS`" (2 OBSERVATIONS AND DATA REDUCTION)
- **RADEX** : non-LTE radiative transfer  
  > "We used the non-LTE radiative transfer code RADEX (cite: vdt07)" (5.2 Radiative Transfer Analysis using RADEX)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total 12CO(1-0) integrated intensity | 594.6 | 1.6 | Jy km/s | 1 | The total $^{12}$CO (1–0) integrated intensity of VV 114 is 594.6 $\pm$ 1.6 Jy km s$^{-1}$ |
| HCN(4-3)/HCO+(4-3) at S0 (eastern nucleus) | 1.34 | 0.09 | dimensionless | 2 | S0 has a high $R_{\rm{HCN/HCO^+}}$ (1.34 $\pm$ 0.09) |
| R_3-2/1-0 range | 0.2 to 0.8 | not stated | dimensionless | 2 | The $R_{3-2/1-0}$ of VV 114 varies from 0.2 to 0.8 |
| Molecular gas mass at R38 (tidal arm tip) | 3.8e7 (alpha_CO/0.8) | 0.7e7 | Msun | 3 | R38 / 3.8 $\pm$ 0.7 |
| Gas-to-dust ratio at eastern nucleus (R18) | 128 | 16 | dimensionless | 6 | The smallest value of (128 $\pm$ 16) |
| Tkin at R21a (eastern nucleus), best fit | 50 (range 25-90) | not stated | K | 4 | constrained to within 25 – 90 K (the best fit is 50 K) |
| nH2 at E0 (AGN) | 10^5.0-10^5.4 | not stated | cm^-3 | 4 | $n_{\rm{H_2}}$ = 10$^{5.0}$ – 10$^{5.4}$ cm$^{-3}$ |
| Missing flux 340 GHz continuum vs JCMT | 75 | 4 | % | 1 | The estimated missing flux relative to the JCMT 340 GHz observation (cite: wil08) is 75 $\pm$ 4 % |

## Qualitative findings

- First detection of extranuclear CH3OH emission in interacting galaxies, concentrated in the overlap region  
  > "including the first detection of extranuclear CH$_3$OH emission in interacting galaxies" (abstract)

## Claim tuples

- H: Eastern nucleus hosts an obscured AGN | E: HCN/HCO+ (4-3) ratio at 200 pc | R: R=1.34±0.09 at unresolved nucleus vs <0.5 elsewhere in filament | F: HCN-rich AGN surrounded by HCO+-rich starburst clumps | **supported**
- H: CO excitation varies across the merger | E: Resolved CO 3-2/1-0 and 12CO/13CO ratios | R: 0.2-0.8 and 5-50 | F: Central filament highly excited, enhanced [CO]/[13CO] | **supported**
- H: Overlap region chemistry is shock dominated | E: CS, CH3OH, CN abundances vs M82, NGC 253 | R: High CH3OH abundance, similar to NGC 253 | F: Overlap region dominated by large-scale shocks | **partially**
- H: A tidal dwarf galaxy is forming at the southern arm tip | E: Gas mass, SFR, tgas and RADEX at R38 | R: MH2 ~3.8e7, SFR 0.10, tgas 0.40 Gyr | F: R38 is a candidate forming TDG | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Two RADEX line sets because band 7 lines have higher critical densities than band 3  
  > "Since the molecular lines in the band 7 have significantly higher critical densities than that in the band 3, we used two sets of molecular lines" (5.2)
- How they decided it was enough: _not stated_
- Limitation (authors): alpha_CO very uncertain and held constant  
  > "such a study is beyond the scope of this present paper" (5.1)
- Limitation (authors): Missing flux for some lines  
  > "there are significant negative sidelobes at the north and south of the image which is likely the cause of missing flux" (3.2 12CO (3-2))
- Caveat (inferred, ours): Assumed fixed abundances and uniform single-zone RADEX make Tkin/density poorly constrained
- Caveat (inferred, ours): Single alpha_CO and Td across regions
- Caveat (inferred, ours): Pa-alpha SFR may be affected by extinction
- Caveat (inferred, ours): Box sizes comparable to beam; filling factor degeneracy

## Reproducibility

- Data public (paper): ALMA Cycle 0 data, project cited  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00467.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Briggs robust, clean parameters, line-free channels
- Missing: Box coordinates
- Missing: RADEX script details
- Missing: Pa-alpha maps from miniTAO
- Data volume (inferred): ~50-100 GB raw (Cycle 0, multiple EBs)
- Score (inferred): 3/5, Public data and many numeric tables, but imaging parameters and RADEX setup partly unstated.
- Rediscovery candidate: yes, Public Cycle 0 data, tabulated numeric results (line ratios, masses), mostly standard recipe.

## Links

- Method: van der Tak et al. 2007 (cite: vdt07) (RADEX code)
- Method: Scoville et al. 2014 (cite: scv14) (ISM mass from dust continuum)
- Companion: Iono et al. 2013 (cite: ion13) (Earlier Cycle 0 HCN/HCO+ (4-3) study of VV 114)

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
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
  "facts": 81,
  "stated": 53,
  "rate": 0.654
 },
 "evidence_ok": true
}
```
