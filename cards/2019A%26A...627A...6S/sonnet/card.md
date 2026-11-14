# Physical conditions in Centaurus A's northern filaments. I. APEX mid-J CO observations of CO-bright regions

`2019A&A...627A...6S` | Astronomy and Astrophysics 2019 | first author: Salomé, Q. | arXiv: 1901.11148 | DOI: 10.1051/0004-6361/201833866

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars, astrochemistry
- Question: What are the physical conditions (temperature, density) and shock characteristics of the molecular gas in the Horseshoe complex of Centaurus A's northern filaments, from mid-J CO lines  
  > "we investigate the physical conditions of gas (temperature, density) and the characteristics of shocks within the Horseshoe complex." (Introduction)
- Target **Centaurus A (NGC 5128) Horseshoe complex, position 16**: coordinates J2000 13:26:27.47, -42:48:50.9  
  > "at a distance of 3.8 Mpc ((cite: Harris_2010); scaling conversion of $18.3\: pc/''$)" (Introduction); "so-called position 16; J2000 $\alpha=$13:26:27.47, $\delta=-$42:48:50.9" (2.1 APEX mid-J CO); z/distance 3.8 Mpc  
  > "at a distance of 3.8 Mpc ((cite: Harris_2010); scaling conversion of $18.3\: pc/''$)" (Introduction); "so-called position 16; J2000 $\alpha=$13:26:27.47, $\delta=-$42:48:50.9" (2.1 APEX mid-J CO); distance from Harris et al. 2010  
  > "at a distance of 3.8 Mpc ((cite: Harris_2010); scaling conversion of $18.3\: pc/''$)" (Introduction); "so-called position 16; J2000 $\alpha=$13:26:27.47, $\delta=-$42:48:50.9" (2.1 APEX mid-J CO)

## Data provenance

- ALMA projects: 2015.1.01019.S
- bands: Band 3 (12m and ACA 7m)  
  > "using Band 3 receivers during Cycle 3" (2.2 ALMA 12CO(1-0) short-spacings with ACA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: ACA 8.85 m to 48.95 m  
  > "The baselines of the 7m array range from 8.85m to 48.95m" (2.2 ALMA 12CO(1-0) short-spacings with ACA)
- angular resolution: ACA 13.68''x8.28''; combined 1.40''x1.10''  
  > "with a synthesised beam of $1.40''\times 1.10''\sim 25.6\times 20.1\: pc$ ($PA=82.9$$^{\circ}$)" (2.2 ALMA 12CO(1-0) short-spacings with ACA)
- max recoverable scale: 12m array: 14'' (~260 pc)  
  > "The maximum recovered angular scale by the 12m array was $14''\sim 260\: pc$." (2.2 ALMA 12CO(1-0) short-spacings with ACA)
- sensitivity: noise peaks at 6.2 mJy/beam at 1.47 km/s  
  > "The histogram of the noise level peaks at 6.2 mJy/beam at a spectral resolution of $1.47\: km.s^{-1}$." (2.2 ALMA 12CO(1-0) short-spacings with ACA)
- time on source: ACA: 15 pointings, 11.7-41 min each  
  > "The map consists in a mosaic of 15 pointings, each with an integration time between 11.7 and 41 min" (2.2 ALMA 12CO(1-0) short-spacings with ACA)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO 1-0 (ALMA) (not stated)
- Other facility **APEX**: 12CO(3-2), 12CO(4-3), 12CO(2-1), HCN/HCO+(3-2), [CI] observations  
  > "We looked for the $^{12}$CO(3-2), $^{12}$CO(4-3) and HCN/$HCO^+$(3-2) lines in one pointing" (2.1 APEX mid-J CO)
- External data: ALMA 12m 12CO(1-0) observations  
  > "In (cite: SalomeQ_2017), we presented $^{12}$CO(1-0) observations with the ALMA 12m array." (2.2 ALMA 12CO(1-0) short-spacings with ACA) [from (cite: SalomeQ_2017)]
- External data: 12CO(2-1) APEX data  
  > "the $^{12}$CO(2-1) line comes from (cite: SalomeQ_2016b)" (Table 1) [from (cite: SalomeQ_2016b)]
- External data: HCN/CO ~1e-4 and HCO+/CO ~3e-5 abundances  
  > "we used the relative abundances $HCN/CO\sim 10^{-4}$ and $HCO^+/CO\sim 3\times 10^{-5}$ from (cite: Pety_2017)" (4.1 Low-velocity gradient modelling of the CO emission) [from (cite: Pety_2017)]
- Simulation/model as data: Grid of Paris-Durham C- and J-type shock models, n_H=1e2-1e6 cm^-3, vs 4-20 (C) / 4-30 (J) km/s, G0=0 or 1  
  > "It consists of an ensemble of stationary C-type and J-type shock models with pre-shock densities" (4.2 Paris-Durham shock code)

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "Both sets of data were calibrated using the Common Astronomy Software Applications (CASA) pipeline." (2.2 ALMA 12CO(1-0) short-spacings with ACA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean in CASA  
  > "The imaging and cleaning was made using the *tclean* routine in CASA." (2.2 ALMA 12CO(1-0) short-spacings with ACA)
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
- array combination: uv-plane combination of 12m and ACA within CASA  
  > "We then combined the data in the uv plane within CASA" (2.2 ALMA 12CO(1-0) short-spacings with ACA)
- smoothing: _not stated_
- final beam: 1.40''x1.10'' (PA=82.9°)  
  > "with a synthesised beam of $1.40''\times 1.10''\sim 25.6\times 20.1\: pc$ ($PA=82.9$$^{\circ}$)" (2.2 ALMA 12CO(1-0) short-spacings with ACA)
- final rms: _not stated_

### Inherited from earlier work

- Gaussian decomposition and clustering method to extract 12CO(1-0) signal  
  > "We first recovered the signal using a coherent Gaussian decomposition method, based on the method of (cite: MAMD_2017a)." (3.2 Line ratios) [from (cite: MAMD_2017a)]
- ALMA 12m data and cloud extraction  
  > "In (cite: SalomeQ_2017), we presented $^{12}$CO(1-0) observations with the ALMA 12m array." (2.2 ALMA 12CO(1-0) short-spacings with ACA) [from (cite: SalomeQ_2017)]

### Not stated but needed to reproduce (our reading)

- tclean parameters (weighting, robust, deconvolver, cell, masks, niter, threshold)
- CASA version
- Flux calibrator and flux uncertainty
- Details of the uv combination (weights, scaling)
- Parameters of the Gaussian decomposition/clustering
- Which velocity channels used for the 2.2'' reconstructed cube
- Beam-smoothing method for APEX resolutions

## Analysis recipe

1. **Reduce APEX spectra**: CLASS reduction, baseline subtraction (linear; degree-4 polynomial for CO(4-3)), smoothing to ~3-12 km/s  
  > "The data were reduced using the IRAM package CLASS." (2.1 APEX mid-J CO)
   - software: CLASS
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive 12CO(1-0) emission in each APEX beam**: Gaussian decomposition and clustering of ALMA+ACA cube at 2.2'', K/Jy factor 19.17, smoothing to APEX beams, extract central spectrum, integrate over blue/red velocity ranges  
  > "we smoothed the reconstructed $^{12}$CO(1-0) cube to the different APEX resolutions and extracted the spectrum at the central position of the APEX observations." (3.2 Line ratios)
   - software: CASA
   - parameter: K/Jy 19.17; velocity ranges -360<v<-260 and -260<v<-160 km/s  
  > "we then applied the ALMA K/Jy conversion factor of 19.17 to obtain a cube of the main beam temperature." (3.2 Line ratios)
   - fitting: _not stated_
   - validation: _not stated_
3. **Constrain n, N_CO, T_kin with RADEX**: CO-SLED grid (40x8x40) with LVG, restricted by line ratios, chi2 over coarse grid  
  > "For each triplet {$n_H$, $N_{CO}$, $T_{kin}$}, we built a CO-SLED model ($40\times 8\times 40$)." (4.1 Low-velocity gradient modelling of the CO emission)
   - software: RADEX
   - parameter: linewidth 50 km/s fixed  
  > "We fixed a linewidth $\Delta V=50\: km.s^{-1}$" (4.1 Low-velocity gradient modelling of the CO emission)
   - assumption: same excitation for all clouds in the beam  
  > "We assume that the excitation of the different clouds is the same in this region." (4.1 Low-velocity gradient modelling of the CO emission)
   - fitting: chi2 minimisation between model and observed ratios on a coarse grid  
  > "We thus computed a $\chi^2$ between those model predictions and the observed line ratios." (4.1 Low-velocity gradient modelling of the CO emission)
   - validation: _not stated_
4. **Compare with Paris-Durham shock grid**: Compare total line ratios with C- and J-type shock models coupled to LVG radiative transfer  
  > "In this figure, we compare the observations of the total line integrated intensity ratios (’Total’ lines in Table [2](#table:spec)) with the results of models." (4.2 Paris-Durham shock code)
   - software: Paris-Durham
   - parameter: B_perp (muG) = sqrt(n_H)  
  > "this quantity was set as $B_\bot\, (\mu G)=[n_H\, (cm^{-3})]^{1/2}$" (4.2 Paris-Durham shock code)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration pipeline, uv combination, tclean imaging  
  > "We then combined the data in the uv plane within CASA" (2.2 ALMA 12CO(1-0) short-spacings with ACA)
- **CLASS** : APEX data reduction  
  > "The data were reduced using the IRAM package CLASS." (2.1 APEX mid-J CO)
- **RADEX** : non-LTE LVG modelling of CO SLED  
  > "We used the non-LTE radiative transfer code RADEX (cite: RADEX) based on the low-velocity gradient (LVG) approximation." (4.1 Low-velocity gradient modelling of the CO emission)
- **Paris-Durham shock code** : shock models of CO line ratios  
  > "The shock model is the Paris-Durham code (cite: Flower_2015)." (4.2 Paris-Durham shock code)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(2-1)/CO(1-0) ratio, total | 0.61 | 0.18 | dimensionless | 2 | / Total / $7.61\pm 1.16$ / $12.48\pm 1.88$ / $0.61\pm 0.18$ / |
| CO(3-2)/CO(1-0) ratio, total | 0.21 | 0.07 | dimensionless | 2 | / Total / $3.65\pm 0.64$ / $17.79\pm 2.67$ / $0.21\pm 0.07$ / |
| CO(4-3)/CO(1-0) ratio, total | 0.10 | 0.04 | dimensionless | 2 | / Total / $2.19\pm 0.58$ / $22.46\pm 3.37$ / $0.10\pm 0.04$ / |
| Kinetic temperature | 55-70 | not stated | K | 3 | $N_{CO}=10^{17}-10^{18}\: cm^{-2}$, $n_H=2-6\times 10^2\: cm^{-3}$ and $T_{kin}=55-70\: K$ |
| H2 density | 2-6e2 | not stated | cm^-3 | 3 | $N_{CO}=10^{17}-10^{18}\: cm^{-2}$, $n_H=2-6\times 10^2\: cm^{-3}$ and $T_{kin}=55-70\: K$ |
| ALMA+ACA flux relative to ALMA only | 4.6 | not stated | dimensionless | 0 | recover about 4.6 times the flux from ALMA only |

## Qualitative findings

- CO(3-2) and CO(4-3) detected for the first time in a jet-gas interaction region; HCN, HCO+ and [CI] not detected  
  > "The $^{12}$CO(3-2) and $^{12}$CO(4-3) were detected for the first time in a region of radio jet-gas interaction" (5 Conclusions)

## Claim tuples

- H: Gas in the Horseshoe complex is described by a given temperature and density | E: RADEX LVG grid against CO line ratios relative to ALMA+ACA CO(1-0) | R: T_kin 55-70 K, n_H 2-6e2 cm^-3, degenerate solution | F: Higher-J CO is not strongly excited, SLED peaks at Jup~2-3 | **supported**
- H: Low-velocity shocks can explain the CO emission | E: Compare ratios with Paris-Durham grid | R: Best models n_H=100 cm^-3, G0=0, low velocity, poorly constrained | F: Compatible with low-velocity C-shock, preliminary | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: J-type shocks rejected: absolute intensities too low  
  > "J-type models produce absolute integrated intensities that are too low compared with observed values" (4.2 Paris-Durham shock code)
- How they decided it was enough: _not stated_
- Limitation (authors): Models poorly constrained; degeneracy among n, N, T; single pointing and different beams may bias ratios  
  > "Finally, as we have only one pointing for each transition and the beam size is not the same, we do not cover the same regions." (4.1 Low-velocity gradient modelling of the CO emission)
- Caveat (inferred, ours): Single pointing and beam-matching via modelled CO(1-0) cube introduces uncertain ratios
- Caveat (inferred, ours): Shock grid comparison is qualitative with no formal fit
- Caveat (inferred, ours): Assumes uniform excitation across clouds in beam

## Reproducibility

- Data public (paper): Reduced APEX spectra available at CDS  
  > "The reduced APEX spectra (FITS files) are only available at the CDS via anonymous ftp" (footnote 2)
- Products in archive: _not stated_
- Missing: tclean parameters and combination details
- Missing: Gaussian decomposition/clustering settings
- Missing: Shock grid outputs
- Data volume (inferred): ~10-50 GB (ACA + 12m mosaics, Band 3)
- Score (inferred): 3/5, ALMA data public and APEX spectra at CDS, but imaging and decomposition parameters missing and shock modelling qualitative.
- Rediscovery candidate: no, ALMA part is only a supporting input; key results depend on APEX data and unreleased shock grids.

## Links

- Method: (cite: MAMD_2017a) (Gaussian decomposition and clustering method)
- Method: (cite: Flower_2015) (Paris-Durham shock code)
- Companion: (cite: SalomeQ_2017) (ALMA 12m CO(1-0) of the Horseshoe complex)
- Companion: (cite: SalomeQ_2016b) (APEX CO(2-1) map)
- Related: APEX project 098.B-0004

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
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
  "facts": 73,
  "stated": 38,
  "rate": 0.521
 },
 "evidence_ok": true
}
```
