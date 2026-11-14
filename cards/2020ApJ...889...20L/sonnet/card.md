# The Circumstellar Environment around the Embedded Protostar EC 53

`2020ApJ...889...20L` | The Astrophysical Journal 2020 | first author: Lee, Seokho | arXiv: 1911.10318 | DOI: 10.3847/1538-4357/ab5a7e

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry, protoplanetary_disks
- Question: What are the disk, envelope kinematics and chemistry (snow lines) of the episodically accreting embedded protostar EC 53, and do they show traces of past outbursts?  
  > "To better describe the kinematics and chemical properties of this environment, we have obtained high-resolution Atacama Large Millimeter/submillimeter Array (ALMA) imaging of gas and dust." (Introduction)
- Target **EC 53**: coordinates RA 18h29m51.17685s, Dec +01d16m40.3892s (J2000)  
  > "The peak of the continuum emission is located at $\alpha$(J2000)= 18$^h$29$^m$51.17685$^s$ and $\delta$(J2000)= +01$^d$16$^m$40.3892$''$." (3.1 Dust continuum images); "(93 AU at the distance of 436 pc)" (3.1 Dust continuum images); z/distance 436 pc  
  > "The peak of the continuum emission is located at $\alpha$(J2000)= 18$^h$29$^m$51.17685$^s$ and $\delta$(J2000)= +01$^d$16$^m$40.3892$''$." (3.1 Dust continuum images); "(93 AU at the distance of 436 pc)" (3.1 Dust continuum images); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01304.T
- bands: _not stated_
- frequencies and spectral setup: 4 spectral windows: 336.995–337.229, 338.345–338.579, 346.945–347.180, 349.396–349.630 GHz; 244.141 kHz resolution (~0.2 km/s)  
  > "The four spectral windows were set for 336.995 – 337.229 GHz, 338.345 – 338.579 GHz, 346.945 – 347.180 GHz, and 349.396 – 349.630 GHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-5, 41 12-m antennas  
  > "Forty-one 12-m antennas were used in the C40-5 configuration, with baselines in the range from 15.1 m to 1.1 km." (2 Observations)
- baselines: 15.1 m to 1.1 km  
  > "with baselines in the range from 15.1 m to 1.1 km" (2 Observations)
- angular resolution: 0.3'' (natural+taper lines); 0.2'' (robust 0.5 lines); 0.15''x0.11'' (uniform continuum)  
  > "natural weighting with a UV-taper of 0.2$''$  was used to obtain images with a higher signal-to-noise ratio and a resolution of 0.3$''$." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: ~4 mJy/beam (strong lines); continuum 0.21 and 0.38 mJy/beam  
  > "The RMS noise levels of the two images are 0.21 and 0.38 mJy beam$^{-1}$, respectively." (2 Observations)
- time on source: 48.1 minutes  
  > "The total observing time on EC 53 was 48.1 minutes." (2 Observations)
- observing dates: 2017 May 21  
  > "on 2017 May 21" (2 Observations)
- pi or archival as stated: PI Jeong-Eun Lee, Cycle 4  
  > "ALMA during Cycle 4 (2016.1.01304.T, PI: Jeong-Eun Lee)" (2 Observations)
- Line: C17O J=3-2 (337.060988 GHz)
- Line: H13CO+ J=4-3 (346.998344 GHz)
- Line: CH3OH 7k-6k (338.34-338.72 GHz)
- Line: CCH N=4-3, J=7/2-5/2 (349.3992756 GHz)
- Line: C34S J=7-6 (337.396459 GHz)
- Other facility **JCMT/SCUBA-2**: 850 um flux of 960 mJy at quiescent phase, used for envelope mass  
  > "The 850 $\mu$m flux (in the beam of 14.6$''$) of EC 53 with the JCMT/SCUBA-2 is 960 mJy at the quiescent phase" (3.1 Dust continuum images)
- Other facility **CARMA**: N2H+ 1-0 data for source velocity and snow line comparison  
  > "N$_2$H$^+$ 1–0 line emission measured with the CARMA" (3.2 Molecular lines)
- External data: Dust opacity 3.4 cm2/g at 343.4 GHz  
  > "a dust opacity" (3.1 Dust continuum images) [from (cite: Beckwith1990)]
- External data: Average dust temperature of 20 K  
  > "Adopting an average dust temperature of 20 K (cite: Andrews2005)" (3.1 Dust continuum images) [from (cite: Andrews2005)]
- External data: SCUBA-2 850 um quiescent flux 960 mJy  
  > "is 960 mJy at the quiescent phase (cite: Yoo2017)" (3.1 Dust continuum images) [from (cite: Yoo2017)]
- External data: Molecular line data from CDMS  
  > "The molecular information is adopted from CDMS database (cite: CDMS2001)." (Table 1) [from (cite: CDMS2001)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "The data were initially calibrated using the CASA 4.7.2 pipeline (cite: McMullin2007)." (2 Observations)
- casa version: CASA 4.7.2  
  > "CASA 4.7.2 pipeline" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1751+0939 (bandpass and amplitude); J1830+0619 phase  
  > "The quasar J1751+0939 was used as a bandpass and amplitude calibrator" (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: applied, details not given  
  > "Self-calibration was applied for better imaging." (2 Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Lines: natural + 0.2'' taper; strong lines also Briggs robust 0.5; continuum: natural+taper and uniform (uv>500 klambda)  
  > "produced by Briggs weighting with a robust factor of 0.5 to obtain higher resolution (0.2$''$)." (2 Observations)
- uv taper: 0.2''  
  > "natural weighting with a UV-taper of 0.2$''$" (2 Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: continuum from line-free channels (not listed)  
  > "A dust continuum image was produced using line-free channels" (2 Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 0.25 km/s channels for strong lines, 0.5 km/s for weak lines  
  > "A spectral resolution of 0.25 km s$^{-1}$  was used for *strong* C$^{17}$O, H$^{13}$CO$^{+}$, and CCH lines" (2 Observations)
- final beam: 0.15''x0.11'' PA -88.4 deg (uniform continuum)  
  > "with a beam size of 0.15$''$  $\times$ 0.11$''$  oriented at position angle of -88.4$^\circ$" (2 Observations)
- final rms: 0.21 and 0.38 mJy/beam continuum; ~4 mJy/beam strong lines  
  > "The RMS noise level for the strong molecular lines is $\sim$4 mJy beam$^{-1}$  near the continuum peak." (2 Observations)

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals and number of rounds
- Line-free channel ranges for continuum
- Image size, cell size, clean threshold and masks
- Deconvolver used in tclean
- Procedure for position-velocity extraction and power-law fit of the rotation profile
- Details of stacking weak CH3OH and CCH lines
- Thin-disk model fitting procedure and uncertainties on tau and T
- LTE model fitting details for methanol
- Flux scale uncertainty

## Analysis recipe

1. **Measure continuum disk size, orientation, flux**: Gaussian fit in the image plane  
  > "The properties of the continuum emission are derived by fitting a Gaussian profile using the task ‘imfit’ in CASA." (3.1 Dust continuum images)
   - software: CASA imfit
   - fitting: _not stated_
   - validation: Compared with previous position angle and inclination measurements  
  > "This position angle and inclination are both consistent with previous observations." (3.1 Dust continuum images)
2. **Derive disk mass**: Optically thin dust mass formula M = F d^2/(kappa B(T))  
  > "The disk mass may be estimated from the continuum flux by" (3.1 Dust continuum images)
   - assumption: T_dust 20 K, kappa 3.4 cm2/g, gas-to-dust 100, d=436 pc  
  > "a gas-to-dust ratio of 100 leads to a disk mass of 0.075 $\pm$ 0.003 M$_\odot$." (3.1 Dust continuum images)
   - fitting: _not stated_
   - validation: Caveat that estimate depends on uncertain opacity and optical depth  
  > "depends on highly uncertain assumptions, including the dust opacities and optical depths" (3.1 Dust continuum images)
3. **Spectral index and grain growth**: Spectral index between uniform-weighted images at 348.38 and 337.86 GHz, related to tau and beta  
  > "between two continuum images produced with the uniform weighting at frequencies of $\nu_1$ = 348.38 GHz and $\nu_2$ = 337.86 GHz" (3.1 Dust continuum images)
   - assumption: isothermal dust  
  > "in the isothermal condition" (4.1 Dust grain growth)
   - fitting: _not stated_
   - validation: _not stated_
4. **C17O rotation profile and protostellar mass**: PV diagram along disk PA 60 deg within 0.5'', power-law fit to velocity profile, Keplerian mass at i=35 deg  
  > "In the following analysis, we fit the rotation profile only within 0.5$''$." (3.2.1 Kinematics)
   - assumption: source velocity 8.5 km/s  
  > "A source velocity of 8.5 km s$^{-1}$  is adopted throughout this analysis" (3.2 Molecular lines)
   - fitting: _not stated_
   - validation: Tested position angles 30-60 deg  
  > "the models with different position angles from 30$^\circ$  to 60$^\circ$  do not show significant variation in the rotation profile." (3.2.1 Kinematics)
5. **Thin disk model of continuum optical depth from C17O hole**: Power-law tau_c(r) and T(r) thin inclined disk, LTE C17O intensity I ∝ tau n_u exp(-tau), convolved with beam, psi=1.0,1.5,2.0  
  > "We test three power-law indices of optical depth: $\psi$= 1.0, 1.5, and 2.0." (4.1 Dust grain growth)
   - parameter: inclination 35 deg; model reproduces 69.3 mJy/beam peak and 139.7 mJy flux  
  > "The emission from the inclined thin disk (inclination= 35$^\circ$) are convolved with the observed beam." (4.1 Dust grain growth)
   - assumption: constant C17O/dust column ratio, LTE, gas and dust same temperature  
  > "the column density ratio of C$^{17}$O  and dust is spatially constant, and the C$^{17}$O  molecules are in the local thermal equilibrium (LTE) condition" (4.1 Dust grain growth)
   - fitting: _not stated_
   - validation: Disk mass compared with 0.075 Msun estimate  
  > "which is similar to the disk mass of 0.075 M$_\odot$" (4.1 Dust grain growth)
6. **Methanol abundance**: LTE model of CH3OH spectrum from 0.6'' aperture with CDMS data, line width 2 km/s, H2 column from dust continuum  
  > "We then reproduced this spectrum with a simple LTE model using molecular data from the Cologne Database for Molecular Spectroscopy" (4.2 Water and CO snowlines)
   - assumption: kappa 3.4 cm2/g, gas-to-dust 100, T 30/50/70 K  
  > "gas-to-dust ratio of 100, and the dust temperatures of 30, 50, and 70 K are adopted" (4.2 Water and CO snowlines)
   - fitting: _not stated_
   - validation: Compared with V883 Ori  
  > "two orders of magnitude lower than the CH$_3$OH  abundance of $\sim$10$^{-8}$ for V883 Ori" (4.2 Water and CO snowlines)

## Software

- **CASA** 4.7.2: pipeline calibration and imfit Gaussian fitting  
  > "CASA 4.7.2 pipeline" (2 Observations)
- **CDMS** : molecular data for LTE methanol model  
  > "Cologne Database for Molecular Spectroscopy" (4.2 Water and CO snowlines)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk mass | 0.075 | 0.003 | Msun | 2 | leads to a disk mass of 0.075 $\pm$ 0.003 M$_\odot$ |
| Disk total flux | 139.7 | 1.2 | mJy | 1 | 69.3 $\pm$ 0.4 mJy beam$^{-1}$  and 139.7 $\pm$ 1.2 mJy, respectively |
| Disk peak intensity | 69.3 | 0.4 | mJy/beam | 1 | 69.3 $\pm$ 0.4 mJy beam$^{-1}$ |
| Disk inclination | 34.8 | 2.1 | deg | 1 | disk inclination of 34.8 $\pm$ 2.1$^\circ$ |
| Disk position angle | 60.0 | 4.2 | deg | 1 | position angle of 60.0 $\pm$ 4.2$^\circ$ |
| Spectral index at continuum peak | 1.9 | 0.3 | dimensionless | 3 | The spectral index at the continuum peak is 1.9 $\pm$ 0.3 |
| Disk radius (95% flux) | 214 mas (93 AU) | not stated | mas | 1 | the disk radius that encircles 95% of the disk flux is 214 mas (93 AU at the distance of 436 pc) |
| Envelope mass | 0.86–1.25 | not stated | Msun | 0 | implies the envelope mass is 0.86 – 1.25 M$_\odot$ |
| Protostellar mass (Keplerian lower limit) | 0.3 | 0.1 | Msun | 4 | the lower limit of the protostellar mass can be calculated as 0.3 $\pm$ 0.1 M$_\odot$ |
| Rotation power-law index | -2.1 | 2.2 | dimensionless | 4 | The power-law index that fits the velocity profile is -2.1 $\pm$ 2.2. |
| Dust opacity index beta | <0.2 | 0.6 | dimensionless | 5 | must be lower than 0.2 $\pm$ 0.6 |
| Methanol column density | ~1e15 | not stated | cm-2 | 6 | The derived methanol column density and abundance are $\sim$10$^{15}$ cm$^{-2}$ and $\sim$10$^{-10}$ |
| Methanol abundance | ~1e-10 | not stated | dimensionless | 6 | $\sim$10$^{-10}$, respectively |

## Qualitative findings

- Molecular lines trace outflow cavity walls, infalling/rotating envelope; H13CO+ anti-correlated with CH3OH  
  > "Molecular lines trace the outflow cavity walls, infalling and rotating envelope, and/or the Keplerian disk." (abstract)

## Claim tuples

- H: Is the disk massive with grown grains? | E: Continuum flux, spectral index and thin disk model | R: Mass 0.075 Msun, alpha=1.9±0.3, beta<0.2±0.6 | F: Massive disk with cm-sized grains | **supported**
- H: Is C17O rotation Keplerian? | E: PV rotation profile within 0.5'' | R: Index -2.1±2.2 (-1.1±0.7 excluding one point) | F: Cannot distinguish Keplerian from infalling envelope; M*~0.3 if Keplerian | **partially**
- H: Do snow lines retain past outbursts? | E: CH3OH extent vs current-luminosity snow line; CO extent | R: CH3OH to ~0.35'' vs 0.03'' expected; CH3OH abundance ~1e-10 | F: Snow lines more extended than expected, implying past bursts | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Large scatter and low S/N in rotation profile  
  > "our current observation with large scatter and a low signal-to-noise ratio cannot rule out a rotational profile produced by the Keplerian disk" (3.2.1 Kinematics)
- Caveat (inferred, ours): Disk mass depends strongly on assumed T, opacity and optical depth
- Caveat (inferred, ours): Kinematic mass poorly constrained
- Caveat (inferred, ours): Snow-line interpretation is qualitative with no chemical modelling
- Caveat (inferred, ours): Methanol abundance may be underestimated by an order of magnitude

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Self-calibration parameters
- Missing: Imaging parameters (cell, image size, masks)
- Missing: Rotation fit procedure
- Missing: Thin-disk model code
- Data volume (inferred): ~10-50 GB
- Score (inferred): 5/5, Project code and imaging weights given, but self-cal, masks and model fit details missing.
- Rediscovery candidate: no, Data are likely public after proprietary period but not stated, and several recipe details are missing.

## Links

- Method: (cite: Lee2019) (Similar thin disk and methanol analysis for V883 Ori)
- Companion: (cite: Yoo2017) (JCMT sub-mm variability of EC 53)
- Related: JCMT-Transient monitoring survey

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 48,
  "rate": 0.623
 },
 "evidence_ok": true
}
```
