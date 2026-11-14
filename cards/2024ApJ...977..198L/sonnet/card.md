# The SUPERCOLD-CGM Survey. II. [C I](1─0) Emission and the Physical Conditions of Cold Gas in Enormous Lyα Nebulae at z ∼ 2

`2024ApJ...977..198L` | The Astrophysical Journal 2024 | first author: Li, Jianan | arXiv: 2502.05805 | DOI: 10.3847/1538-4357/ad8637

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars, milky_way_ism
- Question: What are the physical conditions and molecular gas content of QSOs, companions and the cold CGM in ELANe at z~2, from [C I](1-0), CO(4-3) and dust continuum?  
  > "In this work, we present the [C I]$(1-0)$ results." (1 Introduction)
- Target **10 Type-I QSO fields (Q0050+0051, Q0052+0140, Q0101+0201, Q0107+0314, Q1227+2848, Q1228+3128, Q1230+3320, Q1416+2649, Q2121+0052, Q2123-0050)**: coordinates e.g. Q0050+0051 00:50:21.22 +00:51:35.0 (all in Table 1)  
  > "Q0050+0051 | 2.2432 | QSO | 00:50:21.22 | +00:51:35.0" (Table 1); z/distance z = 2.2218-2.4503 (from CO(4-3))  
  > "Q0050+0051 | 2.2432 | QSO | 00:50:21.22 | +00:51:35.0" (Table 1); distance from CO(4-3) redshifts, Paper I  
  > "Q0050+0051 | 2.2432 | QSO | 00:50:21.22 | +00:51:35.0" (Table 1)

## Data provenance

- ALMA projects: 2019.1.01251.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA 12 m and ACA/Morita 7 m  
  > "using both the main (12 m) and Morita (ACA 7 m) arrays of the Atacama Large Millimeter/submillimeter Array (ALMA)" (1 Introduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 12 m: 1.6-2.7'' x 1.2-1.8''; tapered 7+12 m: 5.2-5.4'' x 4.9-5.1''  
  > "5.2$''$$-$5.4$''$ $\times$ 4.9$''$$-$5.1$''$ with PA = $-90^{\circ}$—$84^{\circ}$ for the 7 m + 12 m array data after uv-tapering" (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 0.12-0.17 mJy/beam per 60 km/s channel (12 m); 0.21-0.30 (tapered)  
  > "the resulting rms was between 0.12 $\rm mJy\ beam^{-1}$ and 0.17 $\rm mJy\ beam^{-1}$ per binned channel for the 12 m array data" (2 Observations and data reduction)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [C I] 3P1-3P0 (1-0) (not stated)
- Line: CO 4-3 (not stated)
- Other facility **FIRST and VLASS**: Radio flux densities at 1.44 and 3.00 GHz for Q1228+3128 and Q1416+2649  
  > "observed with the FIRST and VLASS survey, respectively" (3.1 Individual QSOs)
- Other facility **2MASS**: Optical/NIR detections used for radio loudness  
  > "Utilizing detections of 2MASS (cite: 2mass) and VLASS" (3.1 Individual QSOs)
- External data: Ly-alpha extents R_Lya of the nebulae  
  > "Column 13: projected Ly$_{\alpha}$ extent (cite: cai19)." (Table 1) [from (cite: cai19)]
- External data: CO(4-3) fluxes, luminosities, line widths and companion identifications  
  > "In Paper I, We have measured the CO(4$-$3) luminosities for the QSOs and companion galaxies in our sample" (4.3.1) [from Paper I (cite: li23)]
- Simulation/model as data: PDR Toolbox model grids used to compare line ratios  
  > "photo-dissociation region (PDR) model PhotoDissociation Region Toolbox" (4.2)

## Processing

### Calibration

- pipeline or manual: ALMA calibration pipeline with the standard script included with archival data  
  > "We calibrated the data using the ALMA calibration pipeline (cite: hunter23) version 2022.2.0.68 by running the standard pipeline calibration script that was included with the archival ALMA data." (2 Observations and data reduction)
- casa version: CASA 6.4.1  
  > "Common Astronomy Software Applications package (CASA) version 6.4.1" (2 Observations and data reduction)
- pipeline version: 2022.2.0.68  
  > "ALMA calibration pipeline (cite: hunter23) version 2022.2.0.68" (2 Observations and data reduction)
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean in CASA  
  > "we imaged the 12 m array data using the TCLEAN task in CASA with natural weighting" (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "with natural weighting to maximize the signal-to-noise ratio (SNR)" (2 Observations and data reduction)
- uv taper: downweight baselines longer than 18.75 kλ (Gaussian FWHM 4.8'')  
  > "manually downweight baselines with lengths longer than 18.75 k$\lambda$" (2 Observations and data reduction)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, first-order polynomial, line-free channels  
  > "subtract the continuum emission using the UVCONTSUB task in CASA assuming a first-order polynomial for the continuum using line-free channels" (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 7 m + 12 m combined for tapered images  
  > "we combined the data from the 7 m and 12 m arrays" (2 Observations and data reduction)
- smoothing: binned to 60 km/s channels  
  > "We binned the [C I]$(1-0)$ line in all of our targets to 60 $\rm km\ s^{-1}$ channel width" (2 Observations and data reduction)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observation details, sample and CO(4-3) data  
  > "Detailed descriptions of the observations are presented in Paper I, in which we published the CO(4$-$3) data." (2 Observations and data reduction) [from Paper I (cite: li23)]
- [C I] line widths fixed to CO(4-3) values for upper limits and partial spectra  
  > "Width values with no errors correspond to QSOs and companion galaxies for which the [C I]$(1-0)$ width was fixed to that of CO(4$-$3) (see Table 2 in Paper I)." (Table 1) [from Paper I (cite: li23)]
- Mass formula for [C I]  
  > "We follow the formula presented in (cite: dunne21) to estimate the molecular gas mass from the [C I]$(1-0)$ luminosity." (4.3.2) [from (cite: dunne21)]

### Not stated but needed to reproduce (our reading)

- Number of clean iterations, threshold and masks in tclean
- Cell and image size
- Line-free channel ranges per target
- Gaussian-fit procedure and peak-pixel selection details
- Exact PDR model grid and fitting method for n and G0
- Comparison sample compilation for Figures 6-7
- Observing dates, times on source and configurations (only in Paper I)

## Analysis recipe

1. **Calibrate and image**: Pipeline calibration, uvcontsub, natural-weighted tclean of 12 m data, and 7+12 m uv-tapered cubes at 60 km/s  
  > "we combined the data from the 7 m and 12 m arrays and used the “uv-tapering" technique" (2 Observations and data reduction)
   - software: CASA
   - parameter: taper 18.75 kλ  
  > "longer than 18.75 k$\lambda$" (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure [C I] fluxes and widths**: Extract spectra at peak pixel, fit Gaussian; 3 sigma upper limits = 3×RMS×sqrt(δν×FWHM)  
  > "We derive the 3$\sigma$ [C I]$(1-0)$ flux upper limits for the companion galaxies where the [C I]$(1-0)$ line is undetected using $\rm 3\times RMS_{channel} \times \sqrt{\rm \delta \nu \times FWHM}$." (3 Results)
   - assumption: Line center and width fixed to CO(4-3) where [C I] is partially covered  
  > "We adopt a Gaussian profile with the line center and width fixed to the values derived from the CO(4$-$3) line" (3 Results)
   - fitting: Gaussian profile fit  
  > "we use a Gaussian profile to fit the spectrum for each of the QSOs and companions where a full \[C I\]$(1-0)$ spectrum is obtained." (Results)
   - validation: Source sizes from 2D Gaussian fit show emission is unresolved  
  > "we consider the [C I]$(1-0)$ emission from the cold ISM of the QSOs to be spatially unresolved" (Appendix)
3. **Estimate CGM [C I] flux**: CGM flux = tapered 7+12 m flux minus 12 m flux; uncertainty is quadrature sum  
  > "The uncertainty of the [C I]$(1-0)$ flux for the CGM is calculated through $\sqrt{\sigma_{12m}^{2} + \sigma_{7m+12m}^{2}}$" (3.2)
   - assumption: CGM defined as emission on scales ≳16 kpc  
  > "we adopt the definition ‘CGM’ for all the [C I]$(1-0)$ emission on scales $\gtrsim$ 16 kpc" (3.2)
   - fitting: _not stated_
   - validation: Checked contamination from companion C1 in Q0050+0051 and from undetected companions  
  > "To check if there is any contamination from the companion galaxy C1 in the tapered data to the CGM, we use the fact that the QSO is more luminous in \[C I\]$(1-0)$ than companion C1" (Extended [C I](1-0) emission)
4. **Derive luminosities, FIR luminosity, SFR and dust mass**: Line luminosities from Carilli & Walter formulae; MBB SED normalised to continuum; SFR = 2.1e-10 L_FIR  
  > "SFR  =  2.1 \times 10^{-10}\ L_{\rm FIR(SF)}\ [\rm M_{\ensuremath{\odot}}\ yr^{-1} ]" (3.3)
   - assumption: T_dust = 47 K, beta = 1.6, optically thin; L_FIR over 42.5-122.5 µm  
  > "We adopt a dust temperature of 47 K and emissivity index of 1.6" (3.3)
   - fitting: _not stated_
   - validation: Radio synchrotron subtracted for Q1416+2649 via power-law from FIRST/VLASS; not possible for Q1228+3128  
  > "We follow a similar procedure as for Q1228+3128 to subtract the radio synchrotron contribution from the observed ALMA continuum emission." (Individual QSOs)
5. **Constrain gas density and radiation field**: Compare L[CI]/L_CO(4-3) and L[CI]/L_FIR ratios with PDR Toolbox models  
  > "comparing the observed ratios with those predicted in the photo-dissociation region (PDR) model PhotoDissociation Region Toolbox" (4.2)
   - software: PhotoDissociation Region Toolbox
   - fitting: _not stated_
   - validation: _not stated_
6. **Derive molecular gas masses and CGM mass/baryon fraction**: CO(4-3), [C I] and dust based masses; compare to infer alpha_CO  
  > "This suggests that the QSOs and companions are likely starbursts, and both have a low conversion factor" (4.3.4)
   - assumption: QSOs: alpha_CO=0.8, R41=0.87, X_CI=8.4e-5, Tex=29.1 K (Q10=0.457); companions R41=0.85; dust: DGR 1/50 with 47 K  
  > "For the QSOs, we adopt $\alpha_{\rm CO}$ = 0.8 $\rm M_{\ensuremath{\odot}}$${[\rm K\ km/s\ pc^2]}^{-1}$, $R_{\rm 41}$ = 0.87" (Table 2)
   - assumption: CGM X_CI range (3.0-8.4)e-5; halo mass 10^12.5 Msun; baryon fraction 15.6%  
  > "adopting a typical halo mass for QSOs of $10^{12.5}$ $\rm M_{\ensuremath{\odot}}$" (4.3.5)
   - fitting: _not stated_
   - validation: Cross-comparison of three mass tracers  
  > "We here use the \[C I\]$(1-0)$ and CO(4$-$3) lines, as well as the dust continuum emission, as three independent tracers for the molecular gas mass" (Molecular gas mass)

## Software

- **CASA** 6.4.1: calibration, uvcontsub, tclean, 2D Gaussian size fitting  
  > "Common Astronomy Software Applications package (CASA) version 6.4.1" (2 Observations and data reduction)
- **ALMA pipeline** 2022.2.0.68: calibration  
  > "ALMA calibration pipeline (cite: hunter23) version 2022.2.0.68" (2 Observations and data reduction)
- **numpy polyfit** : linear fits of line vs FIR luminosity  
  > "using the polyfit function in the python numpy package" (4.1)
- **PhotoDissociation Region Toolbox** : PDR model line-ratio comparison  
  > "photo-dissociation region (PDR) model PhotoDissociation Region Toolbox" (4.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CGM [C I](1-0) flux in Q0050+0051 | 0.22 (2.7σ) | not stated | Jy km/s | 3 | we detect a [C I]$(1-0)$ flux (luminosity) of 0.22 $\rm Jy\ km\ s^{-1}$ ((2.5 $\pm$ 0.9) $\times 10^{7}$ $\rm L_{\ensuremath{\odot}}$) at an SNR of 2.7 |
| CGM molecular mass Q0050+0051 | (1.0-2.8)e10 | not stated | Msun | 6 | This leads to a molecular gas mass of ($1.0 - 2.8$)$\times 10^{10}$ $\rm M_{\ensuremath{\odot}}$ based on the [C I]$(1-0)$ line. |
| CGM mass 3σ limits other QSOs | <(0.2-1.4)e10 | not stated | Msun | 6 | the resulting range in limits for the molecular gas mass in the CGM is $<$($0.2 - 1.4$)$\times 10^{10}$ $\rm M_{\ensuremath{\odot}}$ |
| Baryon fraction in molecular CGM | <0.4-3 | not stated | % | 6 | represents $<$0.4-3$\%$ of the baryons |
| Gas density of QSOs | 10^4.4-10^4.8 | not stated | cm^-3 | 5 | we estimate a gas density in the range of $10^{4.4}-10^{4.8}\,{\rm cm^{ -3}}$ and radiation field of $10^{3.3}-10^{3.7}$ |
| [C I] flux Q0050+0051 QSO (12 m) | 0.89 | 0.04 | Jy km/s | 2 | 0.89$\pm$0.04 / 382 / 1.11$\pm$0.07 |
| r[CI]/CO Q0050+0051 QSO | 0.36 | 0.03 | dimensionless | 4 | The $r_{[\rm C\ I]/CO}$ values in the QSO and C1 are 0.36 $\pm$ 0.03 and 0.75 $\pm$ 0.18 |
| [CI]/FIR ratio Q1416+2649 | 1.1e-6 | not stated | dimensionless | 4 | extremely low $L_{\rm [C\ I](1-0)}$/$L_{\rm FIR(SF)}$ ratio of $1.1 \times 10^{-6}$ |

## Qualitative findings

- QSOs and companions have a similar low alpha_CO ~0.8, indicating starbursts  
  > "the QSOs and companions display a similar low CO conversion factor of $\alpha_{\rm CO}$ $\sim$ 0.8" (abstract)

## Claim tuples

- H: Do QSOs and companions have denser gas and stronger radiation fields than LIRGs and MS galaxies? | E: Compare L[CI]/L_CO(4-3) and L[CI]/L_FIR with PDR models and comparison samples | R: Ratios similar to SMGs/QSOs, lower than MS galaxies | F: Higher density and radiation fields, highest in QSOs | **supported**
- H: Is there [C I] in the CGM on 16-40 kpc scales? | E: Compare tapered 7+12 m with 12 m fluxes | R: Nine QSOs show flux increase; only Q0050+0051 at 2.7σ | F: Hint of CGM but not confirmed individually | **partially**
- H: What alpha_CO fits QSOs and companions? | E: Compare gas masses from CO(4-3), [C I] and dust | R: Starburst-like parameters give agreement | F: alpha_CO ~0.8 | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Tapering to enhance surface brightness sensitivity for faint extended CGM emission  
  > "This will lower the spatial resolution but enhance the surface brightness sensitivity" (2 Observations and data reduction)
- Alternative: Extended emission from undetected companions considered; judged likely not significant but not excluded  
  > "argue that the contribution from companion galaxies to the extended emission is likely not significant, but cannot be completely excluded" (3.2)
- How they decided it was enough: _not stated_
- Limitation (authors): CGM significance too low for individual targets; mass comparisons depend on uncertain parameters  
  > "any comparison between the various tracers will be hampered by large uncertainties" (4.3.4)
- Caveat (inferred, ours): CGM flux difference between two datasets is not independent and the CGM X_CI is a crude assumption
- Caveat (inferred, ours): Peak-pixel spectra with different beams may bias the flux comparison
- Caveat (inferred, ours): Q1228+3128 continuum contaminated by synchrotron, so no FIR/dust estimate
- Caveat (inferred, ours): Partial line coverage for three QSOs relies on CO-fixed Gaussians

## Reproducibility

- Data public (paper): Pipeline script included with archival ALMA data; project 2019.1.01251.S  
  > "the standard pipeline calibration script that was included with the archival ALMA data" (2 Observations and data reduction)
- Products in archive: _not stated_
- Missing: tclean parameters beyond weighting/taper
- Missing: Paper I observing details
- Missing: Comparison-sample data and PDR fitting details
- Data volume (inferred): ~50-100 GB raw for 10 fields (12 m + 7 m)
- Score (inferred): 3/5, Public data and a clear taper/difference recipe, but imaging parameters and PDR fitting are underspecified and CO data live in Paper I.
- Rediscovery candidate: yes, Public data, a clear recipe and numeric tabulated results exist, though some settings are missing.

## Links

- Method: (cite: dunne21) ([C I] gas mass formula)
- Method: (cite: carrili13) (line luminosity definitions and R41)
- Companion: Paper I (cite: li23) (sample, observations and CO(4-3) results)
- Related: SUPERCOLD-CGM
- Related: FIRST
- Related: VLASS

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
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
  "facts": 82,
  "stated": 50,
  "rate": 0.61
 },
 "evidence_ok": true
}
```
