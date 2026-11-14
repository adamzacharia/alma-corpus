# Salt, Hot Water, and Silicon Compounds Tracing Massive Twin Disks

`2020ApJ...900L...2T` | The Astrophysical Journal Letters 2020 | first author: Tanaka, Kei E. I. | arXiv: 2007.02962 | DOI: 10.3847/2041-8213/abadfc

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Which molecular lines trace the individual circumstellar disks of the massive proto-binary IRAS 16547-4247 at ~100 au scale, and what are the disk kinematics and chemistry?  
  > "This work will provide a tip for the disk-tracing line selection based on new ALMA observations." (Introduction)
- Target **IRAS 16547-4247**: coordinates _not stated_; z/distance 2.9 kpc; systemic velocity about -31 km/s  
  > "at the distance of $2.9{\rm\:kpc}$ (cite: gar03)" (Introduction); distance from Garay et al. 2003 (cite: gar03)  
  > "at the distance of $2.9{\rm\:kpc}$ (cite: gar03)" (Introduction)

## Data provenance

- ALMA projects: 2018.1.01656.S, 2016.1.00992.S
- bands: Band 3 (3 mm), Band 6 (1.3 mm), Band 7 (0.85 mm)  
  > "The 3 mm and 1.3 mm observations were carried out with ALMA in Band 3 and 6" (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 45, 42, 44 antennas for Bands 3, 6, 7  
  > "| 6 | July 15, 2019 (78 min) | 42 |" (Table 1)
- configurations: _not stated_
- baselines: Band 3: 83.1 m-16.2 km; Band 6: 138.5 m-8.5 km; Band 7: 21.0 m-3.7 km  
  > "| 6 | July 15, 2019 (78 min) | 42 | 138.5 m $-$ 8.5 km |" (Table 1)
- angular resolution: ~0.05'' at all bands (Band 3 0.048x0.046'', Band 6 0.055x0.038'', Band 7 0.056x0.046'')  
  > "The resultant synthesized beams of the continuum images are as high as $0.05\ensuremath{''}$ for all wavelengths (Table [1](#tab:obs))." (Observations)
- max recoverable scale: 0.73'' (B3), 0.75'' (B6), 0.84'' (B7)  
  > "| 7 | August 21 $-$22, 2019 (100 min) | 44 | 21.0 m $-$ 3.7 km | J1636-4102 | J1617-5848/J1427-4206 | $0.056\ensuremath{''}\times0.046\ensuremath{''}$ | $0.84\ensuremath{''}$ |" (Table 1)
- sensitivity: _not stated_
- time on source: Total time 90 min (B3), 78 min (B6), 100 min (B7)  
  > "| 3 | June 9, 2019 (90 min) | 45 |" (Table 1)
- observing dates: Band 3 June 9, 2019; Band 6 July 15, 2019; Band 7 August 21-22, 2019  
  > "| 3 | June 9, 2019 (90 min) | 45 | 83.1 m $-$ 16.2 km |" (Table 1)
- pi or archival as stated: _not stated_
- Line: H2O 5(5,0)-6(4,3) (v2=1) (232.6867000 GHz)
- Line: SiO 5-4 (v=0) (217.10498 GHz)
- Line: NaCl 18-17 (v=0) (234.2519153 GHz)
- Line: SiS 12-11 (v=0) (217.817663 GHz)
- Line: SO2 26(3,23)-26(2,24) (v2=1) (216.7585584 GHz)
- Line: CH3CN 12_K-11_K (220.4758-220.6793 GHz (K=4, 8))
- External data: Band 7 (0.85 mm) ALMA data and earlier continuum/CS results for IRAS 16547  
  > "We also utilize the ALMA archived Band 7 (0.85 mm) data in project 2016.1.00992.S (cite: zap19)." (Observations) [from Zapata et al. 2019 (cite: zap19)]
- External data: Dust opacity 0.097 cm2/g (coagulated, no ice mantle, 1e8 cm-3)  
  > "we apply the dust opacity of $\kappa_{\nu, d}=0.097{\rm\:cm^2\:g^{-1}}$ for the coagulated dust model in the high density of $10^8{\rm\:cm^{-3}}$ without the ice mantle (cite: oss94)" (Estimations of Protostellar Properties) [from Ossenkopf & Henning 1994 (cite: oss94)]
- External data: Systemic velocity about -31 km/s  
  > "The systemic velocity of IRAS 16547 is about $-31{\rm\:km\:s^{-1}}$ (cite: gar03)." (Results) [from Garay et al. 2003 (cite: gar03)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline calibration  
  > "The data were calibrated using CASA (cite: McMullin07) pipeline v5.6.1." (Observations)
- casa version: _not stated_
- pipeline version: v5.6.1  
  > "The data were calibrated using CASA (cite: McMullin07) pipeline v5.6.1." (Observations)
- archive products used as is: _not stated_
- flux calibrator: J1617-5848 (B3), J1427-4206 (B6), J1617-5848/J1427-4206 (B7)  
  > "| 3 | June 9, 2019 (90 min) | 45 | 83.1 m $-$ 16.2 km | J1706-4600 | J1617-5848 |" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: Phase self-cal on line-free continuum of all spws, applied to line data, all three bands  
  > "we performed phase self-calibration for all the three bands using the continuum data combining line-free channels of all the spectral windows, and applied the self-calibration solutions to the line data." (Observations)

### Imaging

- task: CASA tclean  
  > "Images are made with CASA task tclean using the Briggs weighting" (Observations)
- deconvolver: _not stated_
- weighting robust: robust 0.5 (Bands 3, 6), -0.5 (Band 7); robust -0.5 for Band 6 line maps in Fig. 4 (~0.035'')  
  > "Briggs weighting with the robustness parameter of 0.5 for Band 3 and 6 data, and $-0.5$ for Band 7 data." (Observations); "we further improve the resolution to $\sim0.035\ensuremath{''}$ ($\sim100{\rm\:au}$), by emphasizing data with longer baselines using a robust parameter of $-0.5$." (Results)
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
- final beam: 0.048x0.046'' (B3), 0.055x0.038'' (B6), 0.056x0.046'' (B7)  
  > "| 6 | July 15, 2019 (78 min) | 42 | 138.5 m $-$ 8.5 km | J1706-4600 | J1427-4206 | $0.055\ensuremath{''}\times0.038\ensuremath{''}$ |" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- PV diagrams along circumbinary disk major axis (P.A.=50 deg) following earlier work  
  > "Following (cite: zap15; zap19), we plot the position-velocity (PV) diagrams along the major axis of the circumbinary disk (P.A.=$50\ensuremath{^\circ}$)" (Results) [from (cite: zap15; zap19)]
- Ionizing photon rate formula and stellar radii estimate  
  > "we can evaluate the ionizing-photon rates of the protostars (cite: sch16)" (Estimations of Protostellar Properties) [from Schmiedeke et al. 2016 (cite: sch16); Tanaka et al. 2016 (cite: KT16)]
- Recombination line to free-free ratio formula  
  > "we can estimate the the ratio of hydrogen recombination lines to the free-free continuum (cite: ang18)" (Estimations of Protostellar Properties) [from (cite: ang18)]

### Not stated but needed to reproduce (our reading)

- Spectral window setup, channel widths and spectral resolution
- Image size, cell size, masking, number of clean iterations and thresholds
- Line-free channel selection and continuum subtraction method
- Self-calibration solution intervals
- Line rms and continuum rms per band
- Method for PV extraction, Gaussian fitting and moment/channel ranges for Fig. 4
- Aperture used for flux measurement and primary beam correction

## Analysis recipe

1. **Calibrate and self-calibrate**: CASA pipeline calibration, then phase self-calibration on combined line-free continuum, applied to line data  
  > "After pipeline calibration, we performed phase self-calibration for all the three bands" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Image continuum and lines**: tclean with Briggs weighting  
  > "Images are made with CASA task tclean using the Briggs weighting" (Observations)
   - software: CASA
   - parameter: robust 0.5 (B3, B6), -0.5 (B7); -0.5 for high-resolution B6 line maps  
  > "A robust weighting parameter of 0.5 is used for Band 3 and 6 data, and a robust weighting parameter of -0.5 is used for Band 7 data." (Table 1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Disk kinematics from moment maps, PV diagrams and blue/red channel maps**: Moment 0/1 maps, PV cuts along P.A.=50 and -65 deg, blue/redshifted emission maps; Gaussian fits to spectra at continuum peaks  
  > "Figure [3](#fig:outer-disk)c shows the PV diagrams of the SO$_2$ $v_2=1$ and SiO emissions along a slit passing through sources A and B (P.A.$=-65\ensuremath{^\circ}$)." (Results)
   - fitting: Gaussian fits to line profiles  
  > "The fitted Gaussian functions of each profile are also presented, except for the SiO (5–4) emission, which has strong absorption." (Information of the Presented Molecular Lines)
   - validation: _not stated_
4. **Estimate disk masses**: Isothermal dust emission equation using 0.85 mm fluxes within 0.05''  
  > "We utilize the 0.85 mm fluxes of $S_{\nu,d}=84$ and $60{\rm\:mJy}$ within $0.05\ensuremath{''}$ for sources A and B" (Estimations of Protostellar Properties)
   - assumption: Td=350-500 K, kappa=0.097 cm2/g, gas-to-dust 100, D=2.9 kpc  
  > "Here we assume the dust temperature range of $T_d=350$–$500{\rm\:K}$." (Estimations of Protostellar Properties)
   - fitting: _not stated_
   - validation: _not stated_
5. **Estimate ionizing photon rates and recombination line width limit**: Optically thin free-free relation using 3 mm fluxes; HRL/free-free ratio for non-detection  
  > "Under the assumption of the optically thin free-free emission, we can evaluate the ionizing-photon rates of the protostars (cite: sch16)" (Estimations of Protostellar Properties)
   - assumption: Te=8000 K, Y+=0.08; 3 mm flux treated as free-free (upper limit)  
  > "where $T_e$ is the electron temperature, which we use the typical values of $8000{\rm\:K}$ (cite: ket08)" (Estimations of Protostellar Properties)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** pipeline v5.6.1: Calibration, self-calibration and tclean imaging  
  > "The data were calibrated using CASA (cite: McMullin07) pipeline v5.6.1." (Observations)
- **IDL Astronomy User's Library** : Listed in software section; use not described  
  > "CASA (cite: McMullin07), the IDL Astronomy User’s Library (cite: lan95)." (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk mass source A (Td=350-500 K) | 0.033-0.19 | not stated | Msun | 4 | We evaluate the disks masses as $0.033$–$0.19\:M_\odot$ and $0.019$–$0.035\:M_\odot$ for sources A and B |
| Disk mass source B (Td=350-500 K) | 0.019-0.035 | not stated | Msun | 4 | We evaluate the disks masses as $0.033$–$0.19\:M_\odot$ and $0.019$–$0.035\:M_\odot$ for sources A and B |
| Ionizing photon rate source A | 9.7e45 (9.6e45 in main text) | upper limit | s-1 | 5 | we evaluate the ionizing-photon rates of $9.7\times10^{45}{\rm\:s^{-1}}$ and $4.3\times10^{45}{\rm\:s^{-1}}$ for sources A and B |
| Ionizing photon rate source B | 4.3e45 | upper limit | s-1 | 5 | we evaluate the ionizing-photon rates of $9.7\times10^{45}{\rm\:s^{-1}}$ and $4.3\times10^{45}{\rm\:s^{-1}}$ for sources A and B |
| Stellar radii A, B | 16 and 17 | not stated | Rsun | 5 | we estimate the stellar radii of $16\:R_\odot$ and $17\:R_\odot$ for sources A and B, respectively (cite: KT16) |
| Recombination line width lower limit | >=100 | 5 sigma limit | km/s | 5 | we estimated that the line width would be $\Delta V\ensuremath{\gtrsim}100~\mbox{km s}^{-1}$ for the non-detection with $5\sigma$ level |
| Systemic velocity difference between A and B | <=2 | not stated | km/s | 3 | We find the velocity difference is as small as $\Delta v_{\rm lsr}\ensuremath{\lesssim}2{\rm\:km\:s^{-1}}$ |
| Line FWHM of disk-tracing lines | 18-26 | not stated | km/s | 3 | These lines have quasi-Gaussian shapes with the FMHWs of $18$–$26{\rm km~s}^{-1}$. |

## Qualitative findings

- NaCl, SiO, SiS and vibrationally excited H2O trace the individual disks at ~100 au, while CH3CN and SO2 trace the circumbinary structure at ~1000 au  
  > "These are complementary to typical hot-core molecules tracing the circumbinary structures on a 1000 au scale." (abstract)
- Disk B appears to rotate opposite to disk A (tentative)  
  > "We also tentatively find that the twin disks are counter-rotating" (abstract)

## Claim tuples

- H: Do NaCl, Si compounds and hot water trace the individual protostellar disks? | E: Moment maps and PV diagrams of many lines at 0.05'' resolution | R: These lines are concentrated near sources A and B, while CH3CN/SO2 are extended | F: They are good inner-disk probes | **supported**
- H: Are the twin disks counter-rotating? | E: Blue/redshifted maps at ~0.035'' | R: Velocity gradient of B opposite to A | F: Tentative counter-rotation, suggesting turbulent fragmentation | **partially**
- H: Are the sources at protostellar stage? | E: Ionizing photon rates from 3 mm flux | R: Rates orders lower than ZAMS | F: Protostars with large radii | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Disk fragmentation origin disfavoured relative to turbulent fragmentation given counter-rotation  
  > "A puzzling finding, however, is the tentative detection of the counter-rotating disks (Figure [4](#fig:disk)), which are difficult to form by disk fragmentation." (Discussions)
- How they decided it was enough: _not stated_
- Limitation (authors): Counter-rotation tentative; contaminating unidentified lines; 3 mm flux is an upper limit for free-free  
  > "We have not been able to identify these contamination lines." (Results)
- Caveat (inferred, ours): Disk masses depend strongly on assumed Td and opacity
- Caveat (inferred, ours): Counter-rotation inferred from velocity gradients affected by absorption and outflow
- Caveat (inferred, ours): No excitation or abundance analysis of NaCl, SiO, SiS

## Reproducibility

- Data public (paper): Archival project codes cited; Band 7 explicitly archived  
  > "We also utilize the ALMA archived Band 7 (0.85 mm) data in project 2016.1.00992.S (cite: zap19)." (Observations)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, mask, niter)
- Missing: Spectral window and channel details
- Missing: Self-cal solints
- Missing: PV and moment extraction details
- Data volume (inferred): ~1-2 TB raw for three long-baseline multi-band datasets
- Score (inferred): 4/5, Data and main settings (robust, CASA version) given, but many imaging details are missing and results are mostly qualitative.
- Rediscovery candidate: no, Main results are largely qualitative (line morphology and kinematics) and imaging details are incomplete.

## Links

- Companion: Zapata et al. 2019 (cite: zap19) (Earlier Band 7 ALMA study of the circumbinary disk)

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
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
  "facts": 73,
  "stated": 39,
  "rate": 0.534
 },
 "evidence_ok": true
}
```
