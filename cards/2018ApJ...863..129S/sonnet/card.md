# Spatially Resolved Dense Molecular Gas Excitation in the Nearby LIRG VV 114

`2018ApJ...863..129S` | The Astrophysical Journal 2018 | first author: Saito, Toshiki | arXiv: 1807.03345 | DOI: 10.3847/1538-4357/aad23b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation, astrochemistry
- Question: How does dense molecular gas excitation, star formation efficiency and chemistry vary across the AGN, starburst and shocked Overlap regions of the merging LIRG VV 114?  
  > "VV 114 has three distinctive regions that are expected to show different dense gas excitation and/or chemistry, i.e., the X-ray-bright AGN, starburst regions, and the shocked Overlap" (1 INTRODUCTION)
- Target **VV 114**: coordinates E0 (AGN) at 01h07m47.60s, -17°30'24.52'' (J2000)  
  > "We have adopted H$_0$ = 70 km s$^{-1}$ Mpc$^{-1}$, $\Omega_{m}$ = 0.3, and $\Omega_{\Lambda}$ = 0.7 throughout this Paper." (1 INTRODUCTION); "(01$^{\rm{h}}$07$^{\rm{m}}$47.60, -17$^\circ$30$'$24.52$''$)" (3.2 The Eastern Nucleus); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.01057.S, 2015.1.00973.S, 2013.1.00740.S, 2011.0.00467.S
- bands: Band 3, Band 6, Band 7  
  > "toward the nearby luminous infrared galaxy VV 114 with ALMA bands 3, 6, and 7" (conclusion)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: B3-1: 18–780 m; B3-2: 19–650 m; Band 6: 16.7–641.5 m; B7-1: 43.3 m–1.6 km; B7-2: 15.1 m–1.6 km  
  > "with a projected baseline length ($L_{\rm baseline}$) of 18–780 m (19–650 m)" (2.1 Cycle 2 ALMA: J = 1–0); "$L_{\rm baseline}$ of 16.7–641.5 m (MRS $\sim$ 9$''$)" (2.2 Cycle 3 ALMA: J = 3–2)
- angular resolution: 0.2''–1.5''; beams 1.45x1.06'' (B3), 0.60x0.47'' (B6), 0.19x0.15'' (B7)  
  > "| 4–3 | 354.50548 | 42.53 | 7 | natural | 0.19 $\times$ 0.15 | 30 | 0.3 |" (Table 1)
- max recoverable scale: ~22'' (Band 3), ~9'' (Band 6), 7'' (Band 7)  
  > "| HCN | 1–0 | 88.63160 | 4.25 | 22 | briggs |" (Table 1)
- sensitivity: _not stated_
- time on source: B3-1 47.4 min, B3-2 23.7 min; Band 6 30.4 min; Band 7 ~41.2 min each  
  > "The total on-source time of B3–1 (B3–2) was 47.4 minutes (23.7 minutes)." (2.1 Cycle 2 ALMA: J = 1–0); "The total on-source time was 30.4 minutes." (2.2 Cycle 3 ALMA: J = 3–2)
- observing dates: B3: 2014 Jun 17, Jul 2, 2015 Jun 4, 5 (B3-1), 2014 Jul 3 (B3-2); B6: 2016 May 23; B7: 2015 Jun 28 and Jul 18  
  > "The data were obtained on 2015 June 28 (B7–1) and July 18 (B7–2)" (2.3 Cycle 2 ALMA: J = 4–3)
- pi or archival as stated: PI: T. Saito for new data; cycle 0 HCN/HCO+ (4–3) data from earlier papers  
  > "We use HCN (4–3) and HCO$^+$ (4–3) data taken in ALMA cycle 0 (cite: Iono13; Saito15)" (2.4 Data Reduction)
- Line: HCN J=1–0, 3–2, 4–3 (88.63160, 265.88643, 354.50548 GHz)
- Line: HCO+ J=1–0, 3–2, 4–3 (89.18852, 267.55763, 356.73422 GHz)
- Line: HNC J=1–0 (90.66357 GHz)
- Line: CS J=7–6 (342.88285 GHz)
- External data: 110 GHz free-free based SFR surface densities, 880 um dust continuum / H2 column densities and aperture definitions  
  > "we use the SFR surface density ($\Sigma_{\rm SFR}$) based on 110 GHz continuum emission (cite: Saito16b)" (5.1) [from (cite: Saito16b)]
- External data: Single-dish HCN/HCO+/HNC fluxes for recovered-flux estimate  
  > "Column 12: Reference of the single-dish flux. (1) (cite: Privon15); (2) (cite: Zhang14)" (Table 1) [from (cite: Privon15); (cite: Zhang14)]
- External data: Cycle 0 HCN(4–3) and HCO+(4–3) ALMA data  
  > "We use HCN (4–3) and HCO$^+$ (4–3) data taken in ALMA cycle 0 (cite: Iono13; Saito15)" (2.4 Data Reduction) [from (cite: Iono13; Saito15)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.2.2 (Band 3), 4.5.3 (Band 6), 4.2.2 (Band 7)  
  > "was done using `CASA` version 4.2.2, 4.5.3, and 4.2.2, respectively" (2.4 Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune/Uranus (B3); bandpass calibrator J0006–0623 used for flux scale in Band 6 (Pallas model unreliable); J2258-279 (B7)  
  > "we estimate the absolute flux scaling factor using the bandpass calibrator, because the visibility model of asteroids in `CASA` is not reliable currently" (2.2 Cycle 3 ALMA: J = 3–2)
- flux scale uncertainty: 5% Band 3, 8% Band 6, 15% Band 7  
  > "we adopt a flux uncertainty of the Band 6 data as 8% throughout this Paper." (2.4 Data Reduction); "we adopt the flux uncertainty of 15% for the Band 7 data." (2.4 Data Reduction)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural (robust = 2.0) or briggs (robust = 0.5)  
  > "Images were reconstructed with the natural (robust = 2.0) or briggs (robust = 0.5) weighting." (2.4 Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane first-order polynomial fit to line-free channels in USB and LSB  
  > "Continuum emission was subtracted in the $uv$-plane by fitting the line free channels in both USB and LSB with a first order polynomial function." (2.4 Data Reduction)
- line free channels: _not stated_
- primary beam correction: images not corrected, except line ratios  
  > "All images shown in this Paper, except for line ratios, are not corrected for primary beam attenuation." (2.4 Data Reduction)
- array combination: _not stated_
- smoothing: uv-clip inside 18 klambda then convolve to 1.5'' for line ratios  
  > "we clipped all visibility data inside 18 $k\lambda$ in order to achieve a similar MRS" (2.4 Data Reduction)
- final beam: _not stated_
- final rms: 0.3–0.6 mJy/beam at 20–50 km/s channels  
  > "| HNC | 1–0 | 90.66357 | 4.35 | 22 | natural | 1.43 $\times$ 1.29 | 50 | 0.6 |" (Table 1)

### Inherited from earlier work

- Eleven 3.0'' apertures, Sigma_SFR and Sigma_H2 (880 um, Scoville16 formulation)  
  > "We use eleven 3.0$''$ ($\sim$1.2 kpc in diameter) apertures along the filament of VV 114 as in (cite: Saito16b)" (3 Results) [from (cite: Saito16b)]
- alpha_HCN(1-0)=10 Msun (K km/s pc2)^-1  
  > "We adopted 10 $M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$ for $\alpha_{\rm HCN(1-0)}$ as in (cite: Gao&Solomon04b)." (5.2) [from (cite: Gao&Solomon04b)]
- n_dense = 2.8e5 cm^-3 and eps_SF = 0.28%  
  > "we assume $n_{\rm dense}$ = 2.8 $\times$ 10$^5$ cm$^{-3}$ and $\epsilon_{\rm SF}$ = 0.28%, which are the same values as those used in (cite: Usero15)" (5.3) [from (cite: Usero15)]
- Free-free to SFR conversion  
  > "used the free-free continuum to SFR conversion prescription described in (cite: Yun&Carilli02)" (5.1) [from (cite: Yun&Carilli02)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum subtraction per spw
- Which dataset uses natural vs briggs beyond Table 1, and image/cell sizes
- Clean thresholds, masks, deconvolver
- Flux-integration method for apertures and uncertainty treatment
- Fitting method for slopes and rotation diagrams (regression, error weighting)
- Mach number/density grid ranges for turbulence model
- Details of Sigma_SFR and Sigma_H2 values taken from Saito16b
- Whether pipeline or manual calibration was used

## Analysis recipe

1. **Calibrate and image ALMA cubes and continuum**: CASA calibration, uv-plane continuum subtraction, imaging with natural/briggs weighting; cycle 0 data flux-rescaled by 1.03 and combined with cycle 2  
  > "we multiplied the flux densities of the cycle 0 data by 1.03 before combination." (2.4 Data Reduction)
   - software: CASA
   - parameter: velocity resolution 20, 30 or 50 km/s  
  > "We made the data cubes with a velocity resolution of 20, 30, or 50 km s$^{-1}$" (2.4 Data Reduction)
   - fitting: _not stated_
   - validation: Checked calibrator fluxes against catalogue; recovered flux relative to single dish  
  > "We roughly recovered half of the total fluxes measured by single dish telescopes." (2.4 Data Reduction)
2. **Build matched line ratio images**: uv-clip inside 18 klambda and convolve to 1.5'' for excitation ratios; mask at 3 sigma  
  > "masked to the region delimited by the HCN (1–0) (HCO$^+$ (1–0)) integrated intensity level at 0.095 (0.153) Jy beam$^{-1}$ km s$^{-1}$" (4.1 Excitation Ratios)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure aperture fluxes and Sigma_dense, SFE, f_dense**: Fluxes in eleven 3'' apertures; M_dense = alpha_HCN L'_HCN(1-0)  
  > "$\Sigma_{\rm dense}$ is calculated by dividing the dense gas mass ($M_{\rm dense}$) by the aperture area." (5.2)
   - assumption: alpha_HCN(1-0)=10; constant T_dust = 25 K for Sigma_H2  
  > "assuming a constant $T_{\rm dust}$ of 25 K" (5.3)
   - fitting: _not stated_
   - validation: Tested alternate SFR tracer (8.4 GHz) and conversion factors  
  > "since the general trend does not change regardless of the employed SFR tracer or adopted conversion factor" (5.3)
4. **Fit Sigma_SFR vs flux slopes and compare turbulence-regulated model**: Log-log slope fits excluding Region 1; Krumholz & McKee turbulence-regulated model grid in Mach number and mean density over SFE_H2 vs f_dense  
  > "We estimate the slope by fitting all the data points except Region 1" (5.1)
   - assumption: n_dense=2.8e5 cm^-3, eps_SF=0.28%  
  > "we assume $n_{\rm dense}$ = 2.8 $\times$ 10$^5$ cm$^{-3}$ and $\epsilon_{\rm SF}$ = 0.28%" (5.3)
   - fitting: _not stated_
   - validation: Density threshold model rejected via correlation coefficient -0.55  
  > "VV 114 data do not show such a positive linear correlation (the correlation coefficient is -0.55)" (5.3)
5. **LTE rotation diagram analysis**: Single-component optically thin LTE rotation diagram fit for T_rot and N_tot per aperture; averaged T_rot of Regions 3 and 9 used where multiple J not detected  
  > "For regions without multiple $J$ detections, we used an averaged $T_{\rm rot}$ between Region 3 and 9" (5.5.1)
   - software: Splatalogue, CDMS
   - parameter: T_bg = 2.73 K  
  > "$T_{\rm bg}$ is the cosmic microwave background temperature (= 2.73 K)" (5.5.1)
   - assumption: optically thin, LTE, single component  
  > "assuming optically-thin gas and LTE conditions" (5.5)
   - fitting: _not stated_
   - validation: Optical depth check using Goldsmith & Langer formalism gives tau_max ~1.3; consistent with Krips08 non-LTE  
  > "which corresponds to $\tau_{\rm max}$ $\sim$ 1.3" (5.5.2)

## Software

- **CASA** 4.2.2, 4.5.3: calibration, imaging, statwt, continuum subtraction  
  > "Processing the new Band 3, Band 6, and Band 7 data, including calibration and imaging, was done using `CASA` version 4.2.2, 4.5.3, and 4.2.2" (2.4 Data Reduction)
- **Splatalogue** : transition parameters  
  > "The molecular line database Splatalogue[^4] and the Cologne Database for Molecular Spectroscopy (cite: Muller01; Muller05) were used" (5.5.1)
- **CDMS** : transition parameters for rotation diagram  
  > "the Cologne Database for Molecular Spectroscopy (cite: Muller01; Muller05) were used to get the transition parameters" (5.5.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum total flux at 260 GHz | 17.4 | 1.4 | mJy | 1 | The total flux of VV 114 at 260 GHz and 350 GHz are 17.4 $\pm$ 1.4 mJy and 44.7 $\pm$ 6.7 mJy |
| Continuum total flux at 350 GHz | 44.7 | 6.7 | mJy | 1 | 17.4 $\pm$ 1.4 mJy and 44.7 $\pm$ 6.7 mJy, respectively |
| HNC(1–0)/HCN(1–0) at E0 | 0.85 | 0.23 | dimensionless | 3 | The HNC (1–0)/HCN (1–0) line ratio at E0 is 0.85 $\pm$ 0.23 |
| HCN(4–3)/CS(7–6) at E0 | 4.9 | 1.3 | dimensionless | 3 | The HCN (4–3)/CS (7–6) ratio is 4.9 $\pm$ 1.3 at the AGN position of VV 114 (E0). |
| Slope Sigma_SFR vs HCN(1–0) flux | 2.03 | 0.18 | dimensionless | 4 | are 2.03 $\pm$ 0.18, 0.83 $\pm$ 0.07, 0.65 $\pm$ 0.04, 1.69 $\pm$ 0.67, 1.30 $\pm$ 0.16, and 0.84 $\pm$ 0.14 |
| Slope vs HCN(4–3) flux | 0.65 | 0.04 | dimensionless | 4 | 2.03 $\pm$ 0.18, 0.83 $\pm$ 0.07, 0.65 $\pm$ 0.04 |
| M_dense Region 6 | 1.8e8 | 0.2e8 | Msun | 3 | $M_{\rm dense}$ = (1.8 $\pm$ 0.2) $\times$ 10$^8$ $M_{\odot}$ (Region 6) |
| Mean X_HCN | 3.5e-9 | 0.7e-9 | dimensionless | 5 | (3.5 $\pm$ 0.7) $\times$ 10$^{-9}$ and (8.9 $\pm$ 1.4) $\times$ 10$^{-9}$, respectively |
| Mean X_HCO+ | 8.9e-9 | 1.4e-9 | dimensionless | 5 | (8.9 $\pm$ 1.4) $\times$ 10$^{-9}$ |
| T_HCN at Region 1 | 10.2 | 2.5 | K | 5 | (10.2 $\pm$ 2.5 K and 12.3 $\pm$ 2.8 K, respectively) |
| T_HCN at E0 | 9.8 | 1.6 | K | 5 | $T_{\rm HCN}$ = 9.8 $\pm$ 1.6 K |
| Mach number Overlap vs eastern nucleus | ~5 vs ~2 | not stated | dimensionless | 4 | (${\mathcal M}$ $\sim$ 5 and $\bar{n}$ $\sim$ 10$^{4.0}$ cm$^{-3}$) relative to the eastern nucleus (${\mathcal M}$ $\sim$ 2 |
| Dynamical mass E0 | 9.3e7 | not stated | Msun | 3 | $M_{\rm dyn}$ of 9.3 $\times$ 10$^7$ $M_{\odot}$ assuming the inclination of 90$^\circ$ |

## Qualitative findings

- Overlap region has higher f_dense but lower SFE than eastern nucleus; HCN/HCO+ high only at AGN position  
  > "In contrast to the SFEs, $f_{\rm dense}$ peaks at Region 8." (5.2)

## Claim tuples

- H: Does dense gas fraction control star formation efficiency (density threshold model)? | E: Compare SFE_H2 vs f_dense across 11 apertures | R: Correlation coefficient -0.55 | F: Density threshold model not appropriate for VV 114 | **supported**
- H: Is the Overlap region more turbulent and diffuse than the nucleus? | E: Turbulence-regulated SF model grid | R: Overlap M~5, n~10^4.0 vs nucleus M~2, n~10^4.5 | F: Overlap has more turbulent diffuse gas, possibly shock-induced | **partially**
- H: What drives dense gas excitation and HCN abundance along the filament? | E: LTE rotation diagrams in apertures | R: T_rot correlates with Sigma_SFR except Region 1; X_HCN flat at (3.5±0.7)e-9 | F: Star formation drives excitation except at AGN; HCN abundance insensitive to environment | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Optically thin LTE assumed since HCN/HCO+ 1–10x weaker than CO  
  > "it is reasonable to assume optically-thin HCN (1–0) and HCO$^+$ (1–0) lines in VV 114" (5.5)
- Alternative: Density threshold model rejected  
  > "showing that the density threshold model is not appropriate for the VV 114 data" (5.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Possible synchrotron contamination of 110 GHz SFR (~25%); absolute values uncertain due to conversion factors  
  > "The absolute values are uncertain because of the assumed conversion factors to derive the surface densities and the assigned SFR tracer." (5.3)
- Caveat (inferred, ours): Single-component optically thin LTE with 3 transitions gives large uncertainties
- Caveat (inferred, ours): Only ~half of the flux recovered; apertures affected by missing flux
- Caveat (inferred, ours): Small number of data points for slope fits
- Caveat (inferred, ours): Constant conversion factors across environments

## Reproducibility

- Data public (paper): ALMA data identified by project codes in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00467.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Saito16b-derived Sigma_SFR and Sigma_H2 tables
- Missing: Fit procedures
- Missing: Line-free channels and clean parameters
- Data volume (inferred): ~100–300 GB raw across four projects
- Score (inferred): 3/5, Public data and clear aperture-based analysis, but key inputs inherited from Saito16b and fitting details missing.
- Rediscovery candidate: no, Key inputs (SFR, H2) from earlier paper and fitting recipes incomplete.

## Links

- Method: (cite: Saito16b) (Apertures, Sigma_SFR, Sigma_H2)
- Method: (cite: Krumholz&McKee05) (Turbulence-regulated star formation model)
- Companion: (cite: Iono13) (Earlier HCN/HCO+ (4–3) cycle 0 data)
- Companion: (cite: Saito15) (Earlier VV 114 ALMA observations)

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 46,
  "rate": 0.605
 },
 "evidence_ok": true
}
```
