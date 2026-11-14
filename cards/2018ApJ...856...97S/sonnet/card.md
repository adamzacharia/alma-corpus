# Dense Molecular Gas in the Starburst Nucleus of NGC 1808

`2018ApJ...856...97S` | The Astrophysical Journal 2018 | first author: Salak, Dragan | arXiv: 1802.09108 | DOI: 10.3847/1538-4357/aab2ac

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, astrochemistry, star_formation
- Question: What are the distribution, line ratios and physical conditions (density, temperature) of dense molecular gas in the starburst nucleus, ring and outflow of NGC 1808?  
  > "the next important step is to image other molecular species, especially those that trace the dense molecular gas, which is abundant in star-forming regions." (1 Introduction)
- Target **NGC 1808**: coordinates 05h07m42.331s, -37d30m45.88s (J2000)  
  > "nearby (10.8 Mpc; (cite: Tul88)) galaxy NGC 1808" (1 Introduction); "single pointing toward the galactic center at $(\alpha,\delta)_\mathrm{J2000}=(05^\mathrm{h}07^\mathrm{m}42.331s\pm0.003s,-37\ensuremath{^\circ}30\ensuremath{'}45.88\ensuremath{''}\pm0.05\ensuremath{''})$" (2 Observations); z/distance 10.8 Mpc  
  > "nearby (10.8 Mpc; (cite: Tul88)) galaxy NGC 1808" (1 Introduction); "single pointing toward the galactic center at $(\alpha,\delta)_\mathrm{J2000}=(05^\mathrm{h}07^\mathrm{m}42.331s\pm0.003s,-37\ensuremath{^\circ}30\ensuremath{'}45.88\ensuremath{''}\pm0.05\ensuremath{''})$" (2 Observations); distance from Tully 1988 Nearby Galaxy Catalog  
  > "nearby (10.8 Mpc; (cite: Tul88)) galaxy NGC 1808" (1 Introduction); "single pointing toward the galactic center at $(\alpha,\delta)_\mathrm{J2000}=(05^\mathrm{h}07^\mathrm{m}42.331s\pm0.003s,-37\ensuremath{^\circ}30\ensuremath{'}45.88\ensuremath{''}\pm0.05\ensuremath{''})$" (2 Observations)

## Data provenance

- ALMA projects: 2012.1.01004.S, 2013.1.00911.S
- bands: Band 3 and Band 7  
  > "observations of molecular spectral lines in bands 3 and 7 carried out with ALMA" (1 Introduction)
- frequencies and spectral setup: Band 3: four basebands at 86.800, 88.716, 97.981, 100.750 GHz (bandwidths 1.875, 1.875, 0.234, 1.875 GHz); Band 7: HCO+(4-3) baseband at 356.734 GHz, 1.875 GHz  
  > "Four basebands (center rest frequencies at 86.800, 88.716, 97.981, and 100.750 GHz, and effective bandwidths 1.875, 1.875, 0.234, and 1.875 GHz, respectively)" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: Band 3: 12 m array; Band 7: 12 m array plus ACA (7 m)  
  > "The data were acquired with the 12 m array and Atacama Compact Array (7 m antennas) and combined in the imaging (CLEAN) process." (2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 3: 2.20''x1.53'' (SiO natural) to 1.15''x0.75'' (CS, robust 0.5); Band 7 HCO+(4-3): 0.98''x0.52''  
  > "the sizes of the synthesized beams range from $2.20\ensuremath{''}\times1.53\ensuremath{''}$ for SiO (2-1) in natural weighting to $1.15\ensuremath{''}\times0.75\ensuremath{''}$ for CS (2-1) with robust parameter 0.5." (2 Observations)
- max recoverable scale: ~19'' (Band 7, shortest ACA baseline ~9 m)  
  > "The shortest baseline of ACA was about 9 m, yielding a maximum recoverable scale of $\sim19\ensuremath{''}$" (2 Observations)
- sensitivity: Band 3 ~1 mJy/beam (5 km/s); Band 7 HCO+(4-3) ~11 mJy/beam (5 km/s)  
  > "The rms sensitivity of the produced data cubes is $\sim1$ mJy beam$^{-1}$ (channel width $\Delta v=5~\mathrm{km~s}^{-1}$)" (2 Observations)
- time on source: _not stated_
- observing dates: given in Salak et al. 2017, not in this paper  
  > "were presented in (cite: Sal17) together with an observational summary that includes the observation date, on-source time, and calibrator information." (2 Observations)
- pi or archival as stated: _not stated_
- Line: HCN J=1-0 (88.630-88.634 GHz)
- Line: HCO+ J=1-0 (89.18852 GHz)
- Line: HCO+ J=4-3 (356.73422 GHz)
- Line: CS J=2-1 (97.98095 GHz)
- Line: SiO v=0, J=2-1 (86.84696 GHz)
- Other facility **ALMA cycle 1/2 CO(1-0) and CO(3-2) data**: CO(1-0), CO(3-2) cubes and continuum from earlier papers  
  > "The ALMA observations in cycles 1 and 2 have produced the data cubes of two CO lines, $J=1-0$ and $J=3-2$" (3.3 Line intensity ratios)
- External data: CO-to-H2 conversion factor X_CO = 0.8e20 cm-2 (K km/s)-1 and 12C/13C ~20-50  
  > "applying a CO-to-H$_2$ conversion factor of $X_\mathrm{CO}=0.8\times10^{20}~\mathrm{cm}^{-2}(\mathrm{K~km~s}^{-1})^{-1}$ (cite: Sal14)" (4.1) [from (cite: Sal14)]
- External data: R_CO (CO(3-2)/CO(1-0)) maps and 93 GHz/350 GHz continuum  
  > "was presented in (cite: Sal17)." (3.3) [from (cite: Sal17)]
- External data: Molecular data for RADEX from LAMDA  
  > "molecular parameters were acquired from the Leiden Atomic and Molecular Database" (4.2) [from (cite: Sch05)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~5% calibration uncertainty  
  > "the calibration uncertainty of the high signal-to-noise ratio images is of the order of $5\%$" (2 Observations)
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "Two image sets were produced based on the parameters in the task “clean”" (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.5 (5 km/s) and natural (20 km/s); Band 7 uniform  
  > "Briggs algorithm with a robustness parameter of 0.5 (optimum sensitivity and resolution) and a velocity resolution of $\Delta v=5~\mathrm{km~s}^{-1}$" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12 m + ACA combined in CLEAN (Band 7)  
  > "combined in the imaging (CLEAN) process" (2 Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observation dates, on-source time, calibrators, continuum data  
  > "were presented in (cite: Sal17) together with an observational summary that includes the observation date, on-source time, and calibrator information." (2 Observations) [from (cite: Sal17)]
- Major axis PA 316 deg  
  > "position angle $316\ensuremath{^\circ}$ determined in (cite: Sal16)" (3.2) [from (cite: Sal16)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration procedure
- clean mask, threshold, cell and image size
- line-free channels and continuum subtraction method
- uv taper/smoothing to common resolution for ratio maps
- pixel blanking thresholds for ratio maps
- exact RADEX grid settings and line-width handling

## Analysis recipe

1. **image lines**: CASA clean cubes with robust 0.5 and natural weighting  
  > "The visibility data were deconvolved and CLEANed using the Common Astronomy Software Applications (CASA) package" (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **measure line parameters and intensity ratios**: Gaussian fits to spectra from 3'' aperture and 2'' regions; integrated intensity ratios  
  > "spectrum extracted from a circular region of diameter $3\ensuremath{''}$ ($\sim156$ pc) toward the galactic center" (3.1)
   - fitting: Gaussian fitting  
  > "obtained from Gaussian fitting of the spectra within the regions" (3.3)
   - validation: _not stated_
3. **LTE optical depth and column density**: 13C isotopologue ratios give tau; N from LTE formula with Tex=31 K and 10 K  
  > "we use $T_\mathrm{ex}=31$ K, estimated for $^{12}$CO (1-0) (cite: Sal14), and $T_\mathrm{ex}=10$ K." (Appendix)
   - assumption: [HCO+]/[H13CO+] = 50 or 25; same beam filling  
  > "we adopt the values of 50, following (cite: San12), and 25, estimated in section" (Appendix)
   - fitting: _not stated_
   - validation: _not stated_
4. **non-LTE density and temperature**: RADEX with LVG, intersections of line ratio curves in n-T space; four column density setups  
  > "The non-LTE calculations were carried out using the radiative transfer program RADEX (cite: vdT07)" (4.1)
   - software: RADEX
   - parameter: 5-500 K, 1e2-1e7 cm-3, dV=50 km/s, Tbg=2.73 K  
  > "temperature range of $5~\mathrm{K}\leq T_\mathrm{k}\leq500~\mathrm{K}$" (4.2)
   - assumption: [CO]/[H2]=1e-4, [HCO+]/[H2]=1e-8, XCO=0.8e20  
  > "we adopt an abundance ratio of $[\mathrm{HCO^{+}}]/[\mathrm{H_2}]=10^{-8}$ reported in previous works" (4.1)
   - fitting: not a statistical fit; graphical intersection  
  > "The physical conditions (density and temperature) are estimated from the areas where the intensity ratios intersect in the parameter space." (Non-LTE calculation of gas density and kinetic temperature)
   - validation: Setup quality judged by number and closeness of intersections  
  > "the quality of the chosen setup was evaluated based on the number of intersections and how close they appear in the investigated parameter space." (4.2)

## Software

- **CASA** : deconvolution and imaging  
  > "deconvolved and CLEANed using the Common Astronomy Software Applications (CASA) package" (2 Observations)
- **RADEX** : non-LTE radiative transfer  
  > "radiative transfer program RADEX (cite: vdT07)" (4.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| R_HCO+ (4-3/1-0) in CND | 0.420 | 0.022 | dimensionless | 2 | the average value is $R_\mathrm{HCO^{+}}=0.420\pm0.022$ |
| max R_HCO+ within central 50 pc | 0.622 | 0.027 | dimensionless | 2 | $R_\mathrm{HCO^{+}}^\mathrm{max}(r<0.5\ensuremath{''})=0.622\pm0.027$ |
| HCN/HCO+ (1-0) in CND | 1.46 | 0.04 | dimensionless | 2 | C / $1.46\pm0.04$ |
| CND density from setup 4 | 10^4.9 - 10^5.8 | not stated | cm-3 | 4 | $10^{4.9}~\mathrm{cm^{-3}}\lesssim n_\mathrm{H_2}\lesssim 10^{5.8}~\mathrm{cm^{-3}}$ |
| CND kinetic temperature | 20-100 (mean ~40) | not stated | K | 4 | $20~\mathrm{K}\lesssim T_\mathrm{k}\lesssim100~\mathrm{K}$ (on average $T_\mathrm{k}\sim40~\mathrm{K}$) |
| N_HCN/N_HCO+ in CND (LTE) | 2.46 | 0.10 | dimensionless | 3 | $N_\mathrm{HCN}/N_\mathrm{HCO^{+}}=2.46\pm0.10$ |
| HCO+(1-0)/HOC+(1-0) in CND | 19.0 | 3.8 | dimensionless | 2 | is measured to be $19.0\pm3.8$ |

## Qualitative findings

- SiO and HNCO detected toward CND, indicating shocked gas  
  > "SiO (2-1) and HNCO (4-3) are detected toward the circumnuclear disk (CND), indicating the presence of shocked dense gas." (abstract)

## Claim tuples

- H: Is the CND dense and warm? | E: RADEX on HCN/HCO+ isotopologue and HCO+ ratios | R: n~10^5 cm-3, 20-100 K | F: Dense warm gas in CND | **supported**
- H: Is dense gas present in the outflow? | E: PVDs along minor axis, RADEX | R: HCN, HCO+, CS, C2H detected; low density 10^2-10^3 | F: Dense tracers detected in outflow with velocity gradient | **supported**
- H: What drives enhanced HCN/HCO+? | E: Compare R_H with SiO and 93 GHz continuum | R: tentative correlations | F: Possibly shock heating and electron excitation from star formation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Column density uncertain by a factor of a few; beam filling factors may differ among tracers  
  > "The uncertainty of the column density is estimated to be a factor of a few." (4.4)
- Caveat (inferred, ours): Non-LTE solutions are graphical with no formal uncertainties
- Caveat (inferred, ours): Assumed abundances and X_CO dominate results
- Caveat (inferred, ours): HCN enhancement setup chosen post hoc

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: calibration details and CASA version
- Missing: imaging parameters beyond robust
- Missing: exact regions and masks
- Data volume (inferred): ~100-300 GB raw for two projects
- Score (inferred): 3/5, Data are archival with codes given, but calibration and imaging details are sparse and the analysis is partly graphical.
- Rediscovery candidate: no, Calibration and imaging details are missing, and the physical-conditions results rely on graphical intersections and assumed abundances.

## Links

- Method: (cite: vdT07) (RADEX)
- Companion: (cite: Sal17) (earlier ALMA CO and continuum data, observation summary)
- Companion: (cite: Sal16) (earlier ALMA study of NGC 1808)

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 35,
  "rate": 0.515
 },
 "evidence_ok": true
}
```
