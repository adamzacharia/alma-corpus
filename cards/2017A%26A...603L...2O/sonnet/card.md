# First detection of methanol towards a post-AGB object, HD 101584

`2017A&A...603L...2O` | Astronomy and Astrophysics 2017 | first author: Olofsson, H. | arXiv: 1706.08254 | DOI: 10.1051/0004-6361/201731170

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, astrochemistry
- Question: Is methanol present in the post-AGB object HD 101584, where does it originate, and do isotope ratios support its post-AGB nature?  
  > "Here we provide further evidence, based on circumstellar isotopolog ratios, for the post-AGB nature of HD 101584." (Introduction)
- Target **HD 101584**: coordinates _not stated_; z/distance 0.7 kpc (0.9-1.8 kpc from Gaia)  
  > "The distance is estimated to be 0.7 kpc, but recent Gaia data suggests a somewhat larger distance, 0.9 – 1.8 kpc." (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00248.S, 2015.1.00078.S
- bands: Band 6; 12CO(2-1) and 13CO(2-1) settings  
  > "in two frequency settings in Band 6, one for the $^{12}$CO($J$ = 2–1) line and one for the $^{13}$CO($J$ = 2–1) line (only Cycle 1)" (Observations)
- frequencies and spectral setup: four 1.875 GHz spectral windows with 3840 channels each  
  > "the data set contains four 1.875 GHz spectral windows with 3840 channels each" (Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m main array, 35 to 43 antennas, Cycles 1 and 3  
  > "during Cycles 1 and 3 with 35 to 43 antennas of the 12 m main array" (Observations)
- configurations: three configurations combined for 12CO(2-1)  
  > "data obtained in three different configurations were combined" (Observations)
- baselines: 13 to 12934 m  
  > "The baselines range from 13 to 12934 m." (Observations)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CH3OH 4_2-3_1 (218.440 GHz)
- Line: CH3OH 8_-1-7_0 (229.759 GHz)
- Other facility **APEX**: 12CO 3-2 and 4-3, C17O and C18O 2-1 line data  
  > "Complementary $^{12}$CO $J$ = 3–2 and 4–3, and C$^{17}$O and C$^{18}$O $J$ = 2–1 line data were obtained using APEX." (Observations)
- External data: 12CO and 13CO J=1-0 data  
  > "we make use of the $^{12}$CO and $^{13}$CO $J$ = 1–0 data published by (cite: olofnyma99)" (Observations) [from (cite: olofnyma99)]
- External data: CH3OH collisional coefficients  
  > "Collisional coefficients for CH$_3$OH were taken from (cite: pottetal04)." (Molecular abundances) [from (cite: pottetal04)]

## Processing

### Calibration

- pipeline or manual: CASA reduction with Tsys, WVR, bandpass and gain calibration  
  > "bandpass and gain calibration were done" (Observations)
- casa version: CASA 4.5.2  
  > "The data were reduced using CASA 4.5.2." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres and Titan  
  > "Flux calibration was done using Ceres and Titan." (Observations)
- flux scale uncertainty: within 5%  
  > "we estimate the absolute flux calibration to be accurate to within 5%" (Observations)
- self calibration: on the strong continuum, per tuning  
  > "for each individual tuning, self-calibration was performed on the strong continuum" (Observations)

### Imaging

- task: CASA clean  
  > "Imaging was done using the CASA clean algorithm" (Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The final line images were created using natural weighting." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: performed on the line data before imaging  
  > "after a continuum subtraction was performed on the emission line data" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Very little flux lost in 12CO(2-1) data  
  > "concluded that very little flux is lost even in the $^{12}$CO(2–1) ALMA data" (Observations) [from (cite: olofetal15)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction order
- Clean threshold, mask, cell and image size
- Final beam and rms per line
- Radiative transfer code name and version
- Region used for extreme-velocity spot fluxes
- Which CASA step and ALMA products correspond to each project code

## Analysis recipe

1. **Isotopologue ratios from CO lines**: Gaussian line decomposition of APEX data and ALMA central 0.5'' emission to get integrated intensity ratios  
  > "We have determined the intensities of the emission coming from the very central region, within 0.5$''$ of HD 101584 in the ALMA data" (The evolutionary nature of HD 101584)
   - fitting: Gaussian fits  
  > "The values within parentheses give the uncertainties in the Gaussian fits used to determine the line parameters." (Table 2)
   - validation: _not stated_
2. **Radiative transfer abundances of extreme velocity spot**: Accelerated-Lambda-Iteration code with two-zone spherical clump model, fitted to 4'' E EVS line intensities  
  > "we solve the radiative transfer using an Accelerated-Lambda-Iteration code, taking into account excitation through collisions with H$_2$" (Molecular abundances)
   - parameter: Inner n=5e6 cm-3, T=200 K, R=0.15''; outer n=5e5 cm-3, T=60 K, R=1''  
  > "Inner: | $n_{\rm H_2}$ = 5$\times$10$^6$ cm$^{-3}$, | $T_{\rm k}$ = 200 K | $R$ = 0$''$15 |" (Table 1)
   - assumption: Spherical clump; torsionally excited CH3OH states not included (abundance may be underestimated by up to factor of two)  
  > "We have not included the torsionally excited states of methanol, which may lead to an underestimate of its abundance by up to a factor of two." (Molecular abundances)
   - fitting: _not stated_
   - validation: Inner size set so 28SiO/29SiO = 20 (solar)  
  > "The size of the higher-density region is constrained by requiring that the $^{28}$SiO/$^{29}$SiO abundance ratio equals 20 (the solar value)" (Molecular abundances)

## Software

- **CASA** 4.5.2: ALMA data reduction and imaging (clean)  
  > "The data were reduced using CASA 4.5.2." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Integrated line intensity ratio 12C17O/13C17O | 13 | ±6 | dimensionless | 1 | The integrated line intensity ratio is 13$\pm$6 |
| C17O/C18O (2-1) intensity ratio | 0.20 | ±0.08 | dimensionless | 1 | 0.20$\pm$0.08 |
| Gas mass of 4'' E EVS | 4e-3 | not stated | Msun | 2 | The estimated gas mass of the 4$''$ E EVS is 4$\times$10$^{-3}$ M$_\odot$. |
| CH3OH abundance (inner) | 3e-6 | not stated | relative to H2 | 2 | CH$_3$OH has an estimated abundance of 3$\times$10$^{-6}$ (assuming an $E$-to-$A$ ratio of 1) |
| H2CO/H2 13CO line intensity ratio | 12 | +12/-6 | dimensionless | 2 | 12$^{+12}_{-6}$ |

## Qualitative findings

- CH3OH emission comes exclusively from the extreme velocity spots  
  > "the CH$_3$OH line emission comes exclusively from the EVSs" (The detection of methanol)

## Claim tuples

- H: Is methanol present in an AGB-related object? | E: ALMA Band 6 spectra of HD 101584 | R: CH3OH 4_2-3_1 and 8_-1-7_0 detected in the EVSs | F: First detection of methanol in an AGB-related object | **supported**
- H: HD 101584 is a post-AGB low-mass M-type star | E: CO isotopologue intensity ratios from APEX and ALMA | R: 12C/13C low, 17O/18O low | F: Remnant of a solar-mass M-type AGB star | **supported**
- H: Origin of molecules in EVSs | E: Comparison of abundances with YSO outflows | R: Similar detections but differing abundances | F: Post-shock chemistry involving circumstellar grains proposed; details unclear | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Evaporation of planetary system objects rejected because CH3OH/H2CO ratio differs from comets  
  > "the observed CH$_3$OH/H$_2$CO abundance ratio is very different, for example, $\approx$ 10 in comets" (Chemistry)
- How they decided it was enough: _not stated_
- Limitation (authors): Geometry uncertain; simple model gives only order-of-magnitude abundances  
  > "In order to get at least order-of-magnitude estimates we assume a spherical clump" (Molecular abundances)
- Caveat (inferred, ours): Single-clump model with unconstrained geometry; no uncertainties on abundances
- Caveat (inferred, ours): Distance uncertain (0.7 vs 0.9-1.8 kpc) affects physical scales
- Caveat (inferred, ours): Methanol detection in two lines only, no rotation diagram

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Radiative transfer code identity
- Missing: Clean parameters
- Missing: EVS extraction regions
- Data volume (inferred): ~100-500 GB for two projects
- Score (inferred): 3/5, Data are archival-linked and calibration is described, but imaging and modelling details are sparse.
- Rediscovery candidate: no, Imaging recipe and radiative transfer code are not specified enough.

## Links

- Companion: (cite: olofetal15) (Earlier ALMA 12CO(2-1) study of HD 101584)

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 59,
  "stated": 29,
  "rate": 0.492
 },
 "evidence_ok": true
}
```
