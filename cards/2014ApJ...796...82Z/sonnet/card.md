# Spectral and Morphological Analysis of the Remnant of Supernova 1987A with ALMA and ATCA

`2014ApJ...796...82Z` | The Astrophysical Journal 2014 | first author: Zanardo, Giovanna | arXiv: 1409.7811 | DOI: 10.1088/0004-637X/796/2/82

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What are the thermal and non-thermal components of SNR 1987A's emission from radio to FIR, how are they distributed, and is there evidence for a pulsar wind nebula?  
  > "The non-thermal and thermal components of the radio emission are investigated in images from 94 to 672 GHz" (abstract)
- Target **SNR 1987A**: coordinates RA 05h35m27.968s, Dec -69d16m11.09s (J2000), VLBI SN position (Reynolds et al. 1995)  
  > "RA $05^{\rm h}\;35^{\rm m}\;27\hbox{$.\!\!^{\rm s}$}968$, Dec $-69^{\circ}\;16'\;11\hbox{$.\!\!^{\prime\prime}$}09$ (J2000)" (3.1 Subtracted Images); z/distance Large Magellanic Cloud; no value stated  
  > "RA $05^{\rm h}\;35^{\rm m}\;27\hbox{$.\!\!^{\rm s}$}968$, Dec $-69^{\circ}\;16'\;11\hbox{$.\!\!^{\prime\prime}$}09$ (J2000)" (3.1 Subtracted Images); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00273.S
- bands: Band 3, 6, 7, 9 (Cycle 0)  
  > "ALMA observations were made in 2012 (Cycle 0) from April to November, over four frequency bands" (2 Observations and Analysis)
- frequencies and spectral setup: Center 101.918, 213.146, 345.364, 672.165 GHz; channel widths 4.883, 4.883, 31.25, 15.625 MHz  
  > "Center frequency (GHz) | 101.918 | 213.146 | 345.364 | 672.165" (Table 1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 17 m (B9) minimum to 400 m (B3) maximum  
  > "with minimum baselines of 17 m (B9) to maximum baselines of 400 m (B3)" (2 Observations and Analysis)
- angular resolution: Diffraction-limited beams 1.74x1.25" (102 GHz), 1.16x0.74" (213), 0.65x0.48" (345), 0.34x0.28" (672); super-resolved 0.8, 0.6, 0.3, 0.3"  
  > "| 213 | $19.7\pm1.6$ | $0.6$ | $1.16\times0.74$ | $-68.5$ | $0.034$ | $75$ |" (Table 2)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 0.83, 1.03, 0.62, 3.40 hr total in B3, B6, B7, B9  
  > "Total observing time (hr) | 0.83 | 1.03 | 0.62 | 3.40" (Table 1)
- observing dates: 2012 April to November  
  > "ALMA observations were made in 2012 (Cycle 0) from April to November" (2 Observations and Analysis)
- pi or archival as stated: PI Indebetouw, project 2011.0.00273.S  
  > "ADS/JAO.ALMA #2011.0.00273.S (PI: Indebetouw)" (Acknowledgments)
- Other facility **ATCA**: 44 GHz synchrotron template, 94 GHz image and 1.4-44 GHz flux densities  
  > "ATCA observations at 44 and 94 GHz are detailed in (cite: zan13) and (cite: lak12), respectively." (2 Observations and Analysis)
- Other facility **Herschel**: FIR fluxes used in the dust SED fit  
  > "the best fit of both ALMA fluxes, as reported in this paper, and *Herschel* fluxes, as from (cite: mat11)" (5.3 Dust Emission)
- Other facility **HST**: Optical images for comparison with ALMA  
  > "similar to that seen with *HST* ((cite: lar11; lar13))" (3 Morphology)
- External data: Herschel dust SED fluxes  
  > "*Herschel* fluxes, as from (cite: mat11)" (5.3 Dust Emission) [from (cite: mat11)]
- External data: ATCA 44 GHz synchrotron template image  
  > "the synchrotron component, as resolved with ATCA at 44 GHz (cite: zan13)" (2 Observations and Analysis) [from (cite: zan13)]
- External data: ATCA 94 GHz image  
  > "All other image parameters are as from (cite: lak12)." (Table 2) [from (cite: lak12)]
- External data: Density model of the ejecta  
  > "matches the density model by (cite: bli00) scaled to the current epoch (see Figure 21 in (cite: fra13))" (5.1 Free-Free Emission) [from (cite: bli00; fra13)]

## Processing

### Calibration

- pipeline or manual: calibrated with CASA, exported to MIRIAD for imaging  
  > "Each dataset was calibrated with the casa[^1] package, then exported in miriad[^2] for imaging." (2 Observations and Analysis)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto in B3, B6; Ceres in B7, B9  
  > "Callisto was observed as an absolute flux calibrator in B3 and B6, while Ceres was used in B7 and B9" (2 Observations and Analysis)
- flux scale uncertainty: ~5% at all frequencies  
  > "in Cycle 0 this uncertainty is estimated at $\sim$5% at all frequencies" (2 Observations and Analysis)
- self calibration: Phase and amplitude in B3 (2-min interval); phase only in B6, B7; none in B9  
  > "both phase and amplitude self-calibration were applied in B3 over a 2-minute solution interval, while only phase calibration was applied in B6 and B7. No self-calibration was performed in B9." (2 Observations and Analysis)

### Imaging

- task: MIRIAD uvmodel for subtraction, uvfit for central gaussian  
  > "All subtractions were performed in the Fourier plane, via miriad task `uvmodel`" (2 Observations and Analysis)
- deconvolver: MEM in B3, B6, B7; CLEAN for I44-subtracted residuals  
  > "Deconvolution was carried out via the maximum entropy method (MEM) (cite: gul78) in B3, B6 and B7." (2 Observations and Analysis); "standard CLEANing was applied to the residuals obtained from the $I_{44}$ subtraction" (2 Observations and Analysis)
- weighting robust: robust = 0.5 in all bands  
  > "A weighting parameter of robust = 0.5 (cite: bri95) was used in all bands." (2 Observations and Analysis)
- uv taper: _not stated_
- cell size: 8 mas  
  > "using a pixel size of 8 mas to avoid artefacts when sources are not at pixel centers" (2 Observations and Analysis)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Super-resolved with circular beams 0.8" (B3), 0.6" (B6), 0.3" (B7, B9)  
  > "were then super-resolved with a circular beam of $0\hbox{$.\!\!^{\prime\prime}$}8$ in B3" (2 Observations and Analysis)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Position-shift procedure after self-calibration and 44 GHz alignment with VLBI  
  > "As in (cite: zan13), we note that since the self-calibration technique removes position information" (2 Observations and Analysis) [from (cite: zan13)]
- Flux scaling of ATCA data to day 9280 via exponential fit parameters  
  > "scaled to day 9280 via exponential fitting parameters derived for ATCA flux densities from day 8000" (Table 2) [from Zanardo et al., in preparation]
- B9 dust template and SED  
  > "the dust component, as imaged with ALMA at 672 GHz (B9) ((cite: ind14))" (2 Observations and Analysis) [from (cite: ind14)]

### Not stated but needed to reproduce (our reading)

- Scaling factors for 44 GHz and B9 models
- Exact MEM and CLEAN parameters (iterations, masks)
- Polygons used for flux integration
- Line-free channel selection beyond band edges
- Fitting weights and procedure for SED, beta and T
- Unpublished ATCA exponential scaling parameters
- Distance adopted for SNR 1987A

## Analysis recipe

1. **Image ALMA data**: Calibrate in CASA, image in MIRIAD with MEM, self-cal, super-resolve  
  > "Each dataset was calibrated with the casa[^1] package, then exported in miriad[^2] for imaging." (2 Observations and Analysis)
   - software: CASA, MIRIAD
   - parameter: robust = 0.5; 8 mas pixels  
  > "A weighting parameter of robust = 0.5 (cite: bri95) was used in all bands." (2 Observations and Analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **Subtract synchrotron and dust templates**: Scaled 44 GHz and B9 models subtracted from visibilities with uvmodel  
  > "the model flux density at 44 GHz was scaled to fit the SNR emission over the ER ($I_{44}$)" (2 Observations and Analysis)
   - software: MIRIAD uvmodel, MIRIAD uvfit
   - fitting: Scaling tuned to minimize difference on eastern lobe without over-subtraction  
  > "Scaling of the 44 GHz model was tuned by minimizing the flux density difference on the brighter eastern lobe" (2 Observations and Analysis)
   - validation: Residuals compared with noise levels  
  > "The residual emission at both 102 and 213 GHz is above noise levels and, thus, unlikely to be the result of image artefacts." (3.1 Subtracted Images)
3. **Measure east-west asymmetry**: Ratios Ap, Ai, A90 from images restored with 0.7" beam, linear fits vs frequency  
  > "where all images are restored with a $0\hbox{$.\!\!^{\prime\prime}$}7$ circular beam" (4 Asymmetry)
   - fitting: linear fits to Ap and Ai  
  > "the linear fits derived for both $A_{p}$ and $A_{i}$ ratios show a consistent decrease" (4 Asymmetry)
   - validation: _not stated_
4. **Fit SED components**: Power law fit to scaled 44 GHz fluxes plus ATCA; modified Planck function for dust; free-free and second synchrotron alternatives  
  > "yields $\beta=1.23$ and dust temperature $T=22.2$ K" (5.3 Dust Emission)
   - assumption: 1<=beta<=2; kappa~2.5 cm2/g for amorphous carbon; free-free with Te~1e4 K, sphere radius 0.40"  
  > "$k_{\nu}\sim2.5$ cm$^{2}$ g$^{-1}$ for amorphous carbon" (5.3 Dust Emission)
   - fitting: _not stated_
   - validation: Free-free tested against Halpha flux limits  
  > "the estimated $S_{\rm H\alpha}$ would have to undergo $7.4$ magnitudes of extinction" (5.1 Free-Free Emission)
5. **Spectral index maps and T-T plots**: Per-pixel least-squares power-law maps from 2-5 frequencies; T-T plots in regions for six frequency pairs, four regression types  
  > "The spectral index distribution across the remnant is investigated via multi-frequency spectral index maps and the *T-T* plot method" (6 Spectral Index Variations)
   - parameter: 0.8" circular beam  
  > "restored with a circular beam of $0\hbox{$.\!\!^{\prime\prime}$}8$" (6 Spectral Index Variations)
   - fitting: Minimize squared residuals per pixel  
  > "the maps derived from 3, 4 and 5 frequencies are more accurate, as the solution minimizes the function" (6 Spectral Index Variations)
   - validation: Compared four regression methods  
  > "The given spectral indices are derived from different linear interpolations: least-square fit from vertical squared errors, $\alpha_{y}$; orthogonal distance regression, $\alpha_{ODR}$;" (Table 4 notes)
6. **PWN constraints**: Equipartition B field, magnetic energy, radio luminosity, spin-down power from Chevalier models  
  > "Eq. [\[eq:PWN2\]](#eq:PWN2) leads to $1\lesssim B_{_{\rm{PWN}}}\lesssim 7$ mG" (7 PWN constraints)
   - assumption: K~100, f~0.5, R_PWN 0.05-0.15"  
  > "taking $\mathcal{K}\approx100$ (cite: bec05) while $f\approx0.5$" (7 PWN constraints)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration  
  > "Each dataset was calibrated with the casa[^1] package" (2 Observations and Analysis)
- **MIRIAD** : imaging, self-calibration, uvmodel, uvfit  
  > "then exported in miriad[^2] for imaging" (2 Observations and Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Synchrotron spectral index at day 9280 | -0.727 | 0.020 | dimensionless | 4 | $\alpha_{s}=-0.727\pm0.020$ |
| Dust temperature | 22.2 | not stated | K | 4 | yields $\beta=1.23$ and dust temperature $T=22.2$ K |
| Dust emissivity index beta | 1.23 | not stated | dimensionless | 4 | yields $\beta=1.23$ |
| Second synchrotron index | -0.231 | not stated | dimensionless | 4 | a synchrotron component with spectral index $\alpha_{p}=-0.231$ |
| Flux density at 672 GHz | 52.8 | 14.2 | mJy | 1 | / 672 / $52.8\pm14.2$ / |
| PWN magnetic field | 1-7 | not stated | mG | 6 | $1\lesssim B_{_{\rm{PWN}}}\lesssim 7$ mG |
| Integrated radio luminosity upper limit | 5.4e33 | not stated | erg/s | 6 | $L_{\rm rad}\approx5.4\times10^{33}$ erg s$^{-1}$ |
| Ai asymmetry at 345 GHz | 0.78 | 0.04 | dimensionless | 3 | $0.78\pm0.04$ |

## Qualitative findings

- Residual emission after 44 GHz subtraction lies mainly west of the SN site  
  > "The residual emission is mainly localised west of the SN site" (abstract)

## Claim tuples

- H: Does the east-west asymmetry change with frequency? | E: Asymmetry ratios from 44 to 345 GHz images | R: Ratios decrease with frequency, reversing at 345 GHz in Ai | F: Attributed to shorter synchrotron lifetime at high frequency | **supported**
- H: Is there emission beyond main synchrotron and 22 K dust? | E: SED fit after subtracting templates | R: Excess ~3 mJy at 102-345 GHz | F: Best fit by a second flat-spectrum synchrotron component, implying a possible PWN; free-free and cold dust disfavoured | **partially**
- H: Where is the flat-spectrum emission? | E: Spectral index maps and T-T plots | R: -0.4<alpha<-0.1 in west, alpha~0 near center | F: Pulsar may be offset westward from SN position | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: T-T plot and subtraction used to decouple non-thermal and dust emission  
  > "To decouple the non-thermal emission from that originating from dust" (2 Observations and Analysis)
- Alternative: Free-free emission and very cold dust (T<~5 K, implausible mass ~50 Msun) considered as alternatives  
  > "dust at $T\sim3$ K with $M_{\rm dust}\sim50 \,M_{\ensuremath{\odot}}$" (5.3 Dust Emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Equipartition estimates may be inaccurate for flat spectra; double-subtracted images unusable due to errors  
  > "these $B_{_{\rm PWN}}$ estimates might be inaccurate" (7 PWN constraints)
- Caveat (inferred, ours): Residuals are small relative to subtraction uncertainties and depend on subjective model scaling
- Caveat (inferred, ours): PWN interpretation is not unique; free-free not excluded
- Caveat (inferred, ours): Different resolutions and epochs between ATCA and ALMA data

## Reproducibility

- Data public (paper): ALMA project cited with PI; ATCA data from earlier papers  
  > "ADS/JAO.ALMA #2011.0.00273.S (PI: Indebetouw)" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Model scaling factors
- Missing: ATCA 44 GHz image and unpublished flux scaling
- Missing: Exact flux integration regions
- Missing: MEM and CLEAN settings
- Data volume (inferred): tens of GB for ALMA Cycle 0 raw data in four bands
- Score (inferred): 3/5, ALMA data public and steps described, but scaling choices are subjective and the ATCA templates and unpublished parameters are missing.
- Rediscovery candidate: no, Key results depend on tuned subtraction scalings and external ATCA data not fully specified.

## Links

- Method: (cite: zan13) (ATCA 44 GHz imaging and alignment method)
- Method: (cite: ind14) (ALMA B9 dust template and SED)
- Companion: (cite: kam13) (ALMA Cycle 0 observations of SNR 1987A)
- Companion: (cite: lak12) (ATCA 94 GHz image)

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
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
  "facts": 80,
  "stated": 52,
  "rate": 0.65
 },
 "evidence_ok": true
}
```
