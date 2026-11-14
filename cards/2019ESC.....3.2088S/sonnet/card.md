# Complex Organic Molecules in Star-Forming Regions of the Magellanic Clouds

`2019ESC.....3.2088S` | ACS Earth and Space Chemistry 2019 | first author: Sewiło, Marta | arXiv: 1909.06843 | DOI: 10.1021/acsearthspacechem.9b00065

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: astrochemistry, star_formation
- Question: What is known about complex organic molecules in Magellanic Cloud star-forming regions, and how do observations compare with chemical models?  
  > "In this article, we summarize the current state of knowledge concerning the organic chemistry in the Magellanic Clouds." (Introduction)
- Target **N159W-South (LMC)**: coordinates RA 05h39m41s, Dec 69d46m11s (phase center)  
  > "The phase center was set to RA (J2000) = 05$^{\rm h}$39$^{\rm m}$41$^{\rm s}$, Dec (J2000) = 69$^{\circ}$46$'$11$''$." (8 Technical Details on Unpublished Observations Reported in this Paper); z/distance LMC: 50.0 +/- 1.1 kpc  
  > "The phase center was set to RA (J2000) = 05$^{\rm h}$39$^{\rm m}$41$^{\rm s}$, Dec (J2000) = 69$^{\circ}$46$'$11$''$." (8 Technical Details on Unpublished Observations Reported in this Paper); distance from pietrzynski2013  
  > "The phase center was set to RA (J2000) = 05$^{\rm h}$39$^{\rm m}$41$^{\rm s}$, Dec (J2000) = 69$^{\circ}$46$'$11$''$." (8 Technical Details on Unpublished Observations Reported in this Paper)

## Data provenance

- ALMA projects: 2016.1.00308.S
- bands: Band 6  
  > "The ALMA correlator was configured to cover specific frequency ranges within the Band 6 of ALMA." (8 Technical Details on Unpublished Observations Reported in this Paper)
- frequencies and spectral setup: Four spectral windows, 1875 MHz each, centered at 242.4, 244.8, 257.85 and 259.7 GHz  
  > "Four broad spectral windows (with a bandwidth of 1875 MHz each) centered at frequencies 242.4, 244.8, 257.85 and 259.7 GHz" (8 Technical Details on Unpublished Observations Reported in this Paper)
- continuum bandwidth: _not stated_
- arrays: 12m main array, 40 antennas  
  > "We used the main array (i.e.,12m antennas) consisting of 40 antennas." (8 Technical Details on Unpublished Observations Reported in this Paper)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: 1.4 mJy/beam in line cube  
  > "Sensitivity of 1.4 mJy beam$^{-1}$ was achieved in the data cube covering the lines." (8 Technical Details on Unpublished Observations Reported in this Paper)
- time on source: _not stated_
- observing dates: Cycle 4, October 2016  
  > "during its Cycle 4 in October 2016" (8 Technical Details on Unpublished Observations Reported in this Paper)
- pi or archival as stated: PI P. Schilke  
  > "PI P. Schilke" (Table 3)
- Line: CH3OH 5(0,5)-4(0,4) E etc. (241.700-241.905 GHz)
- Other facility **VLT/KMOS**: K-band continuum, Brgamma and H2 images of N159W-S  
  > "N159W–S was observed with *VLT*/KMOS (*Very Large Telescope*/$K-$band Multi-Object Spectrograph) under program 0101.C-0856(A)" (8 Technical Details on Unpublished Observations Reported in this Paper)
- External data: N113 A1/B3 hot core LTE results (Trot, column densities, abundances)  
  > "($134\pm6~{\rm K}, 1.6\pm0.1\times10^{16}~{\rm cm}^{-2}$) and ($131\pm15~{\rm K}, 6.4\pm0.8\times10^{15}~{\rm cm}^{-2}$) for A1 and B3, respectively" (4.3) [from (cite: sewilo2018)]

## Processing

### Calibration

- pipeline or manual: ALMA calibration pipeline  
  > "The ALMA data were calibrated using the ALMA calibration pipeline available in CASA version 5.5.1." (8 Technical Details on Unpublished Observations Reported in this Paper)
- casa version: CASA 5.5.1  
  > "The ALMA data were calibrated using the ALMA calibration pipeline available in CASA version 5.5.1." (8 Technical Details on Unpublished Observations Reported in this Paper)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0519-4546  
  > "Flux calibration was obtained through observations of the bright quasar J0519–4546." (8 Technical Details on Unpublished Observations Reported in this Paper)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: TCLEAN  
  > "The CLEANing process was done with the task TCLEAN" (8 Technical Details on Unpublished Observations Reported in this Paper)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "setting the robust parameter of Briggs equal to 0.5 as compromise between resolution and sensitivity" (8 Technical Details on Unpublished Observations Reported in this Paper)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: line-free channels identified and used for continuum images (ranges not given)  
  > "the line-free channels of the broad spectral windows were identified and used to create the continuum images" (8 Technical Details on Unpublished Observations Reported in this Paper)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.22" x 0.12"  
  > "The resulting images were restored with a synthesized beam of 0$\rlap.{''}$22$\times$0$\rlap.{''}$12." (8 Technical Details on Unpublished Observations Reported in this Paper)
- final rms: _not stated_

### Inherited from earlier work

- N113 ALMA analysis (LTE fitting, H2 columns) taken from earlier work  
  > "The LTE analysis of six transitions resulted in rotational temperatures and total column densities" (4.3) [from (cite: sewilo2018)]
- Hot core model code and network  
  > "The chemical network is as discussed in (cite: taquet2016)." (5.2.2) [from (cite: taquet2016)]

### Not stated but needed to reproduce (our reading)

- Image size and cell size
- Line-free channel ranges
- Mask and clean threshold
- Spectral resolution of the cube
- LTE fitting method and software for N159W-S
- Phase and bandpass calibrator details beyond names
- Continuum subtraction method

## Analysis recipe

1. **Calibrate and image N159W-S ALMA data**: Pipeline calibration, tclean imaging with Briggs weighting  
  > "The CLEANing process was done with the task TCLEAN, and setting the robust parameter of Briggs equal to 0.5" (8 Technical Details on Unpublished Observations Reported in this Paper)
   - software: CASA, tclean
   - parameter: robust = 0.5  
  > "setting the robust parameter of Briggs equal to 0.5" (8 Technical Details on Unpublished Observations Reported in this Paper)
   - fitting: _not stated_
   - validation: _not stated_
2. **Preliminary LTE fit of methanol lines**: Preliminary LTE fitting of multiple lines near 241.7-241.9 GHz toward two peaks  
  > "Preliminary Local Thermodynamic Equilibrium (LTE) fitting using multiple lines ($\sim$241.7–241.9 GHz; see Table [\[tbl:transitions\]](#tbl:transitions)) detected toward the two brightest peaks indicate that the gas is cold ($\sim$14 K)." (4.2.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Hot core model calculation for LMC/SMC ices**: Taquet et al. dynamical-chemical model with fixed physical conditions and instant ice injection, ice abundances scaled by elemental depletions  
  > "the physical conditions are fixed in time and the ices are injected instantaneously into the hot gas at $t=0$" (5.2.2)
   - parameter: n_H2 = 5e7 cm-3, T=150 K, zeta = 3e-17 s-1  
  > "$n_{\rm H_2} = 5 \times 10^7$ cm$^{-3}$, $T$=150 K, and a cosmic-ray ionization rate $\zeta = 3\times10^{-17}$ s$^{-1}$" (5.2.2)
   - fitting: _not stated_
   - validation: Compared model CH3OCH3/CH3OH and HCOOCH3/CH3OH ratios with N113 observations  
  > "the observed CH$_3$OCH$_3$/CH$_3$OH ratios in A1 ($\sim$0.1) and B3 ($\sim$0.2) are about an order of magnitude higher than the calculated values ($\sim$0.01)" (5.2.2)

## Software

- **CASA** 5.5.1: ALMA pipeline calibration and tclean imaging  
  > "calibrated using the ALMA calibration pipeline available in CASA version 5.5.1" (8 Technical Details on Unpublished Observations Reported in this Paper)
- **esoreflex** : KMOS data reduction  
  > "The data were reduced with the standard *VLT*/KMOS pipeline using the esoreflex data reduction package." (8 Technical Details on Unpublished Observations Reported in this Paper)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Gas temperature of methanol in N159W-S (preliminary) | ~14 | not stated | K | 2 | indicate that the gas is cold ($\sim$14 K) |
| Synthesized beam N159W-S | 0.22 x 0.12 | not stated | arcsec | 1 | synthesized beam of 0$\rlap.{''}$22$\times$0$\rlap.{''}$12 |
| Model CH3OCH3/CH3OH vs observed in LMC | model ~0.01 vs observed ~0.1 (A1), ~0.2 (B3) | not stated | dimensionless | 3 | the observed CH$_3$OCH$_3$/CH$_3$OH ratios in A1 ($\sim$0.1) and B3 ($\sim$0.2) are about an order of magnitude higher than the calculated values ($\sim$0.01) |

## Qualitative findings

- Only two bona fide COM hot cores (N113 A1, B3) are known in the Magellanic Clouds; cold methanol seen in N159W-S and IRAS 01042-7215  
  > "Only two *bona fide* hot cores with COMs are known in the Magellanic Clouds, both in the N 113 star-forming region in the LMC" (6 Discussion)

## Claim tuples

- H: Does N159W-S host cold methanol rather than hot core methanol? | E: Preliminary LTE fit of methanol lines in new ALMA Band 6 data | R: Gas temperature ~14 K, narrow lines, only methanol detected | F: Methanol in N159W-S is cold, origin unclear | **partially**
- H: Can models reproduce the COM abundances in N113 hot cores? | E: Post-sublimation gas-phase model scaled to LMC/SMC depletions | R: Abundances reproducible but not at times when ratios match; dimethyl ether off by order of magnitude | F: Models broadly but not fully account for observations | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): N159W-S ALMA analysis is preliminary, so no physical parameters given  
  > "Since the analysis of the ALMA data is preliminary, we do not provide physical parameters for N159W–S" (4.2.1)
- Caveat (inferred, ours): Review paper; the new ALMA analysis is preliminary with no uncertainties
- Caveat (inferred, ours): Model comparison uses simplified fixed-condition model

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust
- Missing: LTE fitting details
- Missing: Model code inputs
- Data volume (inferred): ~50-100 GB
- Score (inferred): 2/5, Review paper; the only new ALMA data are briefly described and the analysis is preliminary.
- Rediscovery candidate: no, Recipe incomplete and results are preliminary.

## Links

- Method: (cite: taquet2016) (Chemical model used for the hot core calculations)
- Companion: (cite: sewilo2018) (Detection of COMs in N113 hot cores with ALMA)
- Companion: (cite: shimonishi2018) (SMC IRAS 01042-7215 cold methanol)
- Related: SAGE
- Related: HERITAGE
- Related: MAGMA

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
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 62,
  "stated": 31,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
