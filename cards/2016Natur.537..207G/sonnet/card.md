# Compression and ablation of the photo-irradiated molecular cloud the Orion Bar

`2016Natur.537..207G` | Nature 2016 | first author: Goicoechea, Javier R. | arXiv: 1608.06173 | DOI: 10.1038/nature18957

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, star_formation, astrochemistry
- Question: Is the H/H2 transition at the Orion Bar edge spatially separated from the C+/C/CO transition as static PDR models predict, and what do 1-arcsec images reveal about the cloud structure and dynamics?  
  > "Here we report one-arcsecond-resolution millimetre-wave images that allow us to resolve the molecular cloud surface." (abstract)
- Target **Orion Bar**: coordinates RA(2000)=05h35m20.6s, Dec(2000)=-05d25m20s (mosaic centre)  
  > "The observations consisted of a 27-pointing mosaic centred at $\alpha$(2000) = 5$^h$35$^m$20.6$^s$; $\delta$(2000) = -05$^o$25$'$20$''$." (Methods); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00352.S
- bands: Band 7  
  > "ALMA Cycle-1 observations of the Bar were carried out using twenty-seven 12 m antennae in band 7 at 345.796 GHz (CO $J$=3-2) and 356.734 GHz (HCO$^+$ $J$=4-3)." (Methods)
- frequencies and spectral setup: CO 3-2 345.796 GHz, HCO+ 4-3 356.734 GHz; ~500 kHz resolution (0.4 km/s) over 937.5 MHz bandwidth  
  > "Lines were observed with correlators providing $\sim$500 kHz resolution ($\delta$v$\approx$0.4 km s$^{-1}$) over a 937.5 MHz bandwidth." (Methods)
- continuum bandwidth: _not stated_
- arrays: 27 12 m antennae  
  > "ALMA Cycle-1 observations of the Bar were carried out using twenty-seven 12 m antennae in band 7" (Methods)
- configurations: _not stated_
- baselines: ~12 to ~444 m (C32-3)  
  > "Baseline configurations from $\sim$12 to $\sim$444 m were used (C32-3 antennae configuration)." (Methods)
- angular resolution: ~1 arcsec synthesized beam  
  > "using the synthesized beam size of $\sim$1$''$" (Methods)
- max recoverable scale: _not stated_
- sensitivity: rms ~0.4 K per 0.4 km/s channel  
  > "The achieved rms noise is $\sim$0.4 K per 0.4 km s$^{-1}$ channel, with an absolute flux accuracy of $\sim$10%." (Methods)
- time on source: ~2 h total  
  > "The ALMA 12 m array total observation time was $\sim$2h." (Methods)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (345.796 GHz)
- Line: HCO+ J=4-3 (356.734 GHz)
- Other facility **IRAM-30m**: OTF single-dish maps (EMIR) used as zero/short spacings; HERA HCO+ 3-2 map  
  > "we used fully sampled single-dish maps as “zero-” and “short-spacings”." (Methods)
- External data: H2 v=1-0 S(1) near-IR image  
  > "M. Walmsley for sharing his H$_2$ $v$=1-0 $S$(1) and O i 1.3 $\mu$m infrared images." (Acknowledgements) [from Walmsley et al. 2000 (cite: Walmsley00)]
- External data: Column densities from IRAM-30m line survey towards dissociation front  
  > "were estimated utilizing information from our IRAM-30m telescope line-survey towards the dissociation front\[38\]." (Methods) [from Cuadrado et al. 2015 [38]]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.2.0  
  > "ALMA executing blocks were first calibrated in the CASA software (version 4.2.0) and then exported to GILDAS." (Methods)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10%  
  > "with an absolute flux accuracy of $\sim$10%" (Methods)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: Högbom CLEAN  
  > "The dirty image was deconvolved using the standard Högbom CLEAN algorithm" (Methods)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: IRAM-30m short-spacing visibilities created with GILDAS/MAPPING and merged  
  > "These visibilities were merged with the interferometric observations." (Methods)
- smoothing: _not stated_
- final beam: ~1 arcsec  
  > "using the synthesized beam size of $\sim$1$''$" (Methods)
- final rms: ~0.4 K per 0.4 km/s channel  
  > "The achieved rms noise is $\sim$0.4 K per 0.4 km s$^{-1}$ channel" (Methods)

### Inherited from earlier work

- Short-spacing/wide-field mosaic synthesis theory  
  > "The GILDAS/MAPPING software was used to create the short-spacing visibilities\[31\] not sampled by ALMA." (Methods) [from Pety & Rodríguez-Fernández 2010 [31]]
- Radiative transfer code details  
  > "(see the Appendix in ref.\[36\] for code details and benchmarking tests)" (Methods) [from Goicoechea et al. 2006 [36]]

### Not stated but needed to reproduce (our reading)

- CLEAN masks, thresholds and weighting
- Cell and image size
- Line-free channels and continuum treatment
- Details of the 30m–ALMA merging (scaling factors)
- Rotation angle and definition of the cut geometry for δx
- Grid ranges and collisional rate references for the radiative transfer models
- Distance to Orion adopted explicitly

## Analysis recipe

1. **Calibrate, merge with single-dish and image**: CASA calibration, export to GILDAS, add IRAM-30m short spacings, mosaic imaging with Högbom CLEAN, convert to K  
  > "The dirty image was deconvolved using the standard Högbom CLEAN algorithm and the resulting cubes were scaled from Jy/beam to brightness temperature scale" (Methods)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive physical conditions via non-LTE radiative transfer**: Grid of non-local non-LTE Monte Carlo models compared to CO 3-2 peak and HCO+ 4-3 integrated intensity  
  > "we run a grid of non-local, non-LTE excitation and radiative transfer (Monte Carlo) models." (Methods)
   - parameter: N(HCO+)=5e13, N(CO)=1e18, N_H~2e22 cm^-2  
  > "Radiative transfer models were run for $N$(HCO$^+$)=5$\times$10$^{13}$ cm$^{-2}$, $N$(CO)=1.0$\times$10$^{18}$ cm$^{-2}$" (Methods)
   - assumption: molecular fraction f=0.8, x_e 0–1e-4, T_dust=55 K, CMB 2.7 K  
  > "We adopted $f$=0.8 and varied $x_e$ between 0 and 10$^{-4}$." (Methods)
   - fitting: _not stated_
   - validation: Column densities consistent with previous observations; HCO+/H13CO+ ratio indicates moderate opacity  
  > "They are consistent with previous observations in the region" (Methods)
3. **Density PDF of HCO+ emission**: Log-normal fit to PDF of z=ln(W/<W>) for pixels >5 sigma in compressed layers  
  > "We obtain $z_0$=0.165 and $\sigma$=0.31 from a fit (green curve)." (Methods)
   - assumption: W(HCO+ 4-3) proportional to n_H  
  > "This reasoning justifies the use of $W_{4-3}^{{\rm HCO^+}}$ as a proxy for $n_{\rm H}$ in the region." (Methods)
   - fitting: Gaussian in z  
  > "is very close to a log-normal distribution with $p(z)=N exp(-(z-z_0)^2/2\sigma^2)$, where $z_0$ is the peak value and $\sigma$ the standard deviation." (Emission Probability Distribution Functions (PDF))
   - validation: _not stated_
4. **Pressure budget and magnetic field**: Compare thermal, turbulent and magnetic pressures assuming equipartition (beta=1)  
  > "for $\beta$=$P_B$/$P_{\rm th}$=1 we estimate magnetic fields strengths of $B$$\approx$200 $\mu$G and $\approx$800 $\mu$G" (Methods)
   - assumption: equipartition of thermal, turbulent and magnetic energies  
  > "it is reasonable to assume equipartition of thermal, turbulent and magnetic energies" (Methods)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.0: calibration  
  > "ALMA executing blocks were first calibrated in the CASA software (version 4.2.0)" (Methods)
- **GILDAS/MAPPING** : short-spacing visibilities, merging and imaging  
  > "The GILDAS/MAPPING software was used to create the short-spacing visibilities" (Methods)
- **GILDAS/GREG** : generating final IRAM-30m images  
  > "The final images were generated using the GILDAS/GREG software." (Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean CO 3-2 peak at δx~15'' | 164 | ±10 | K | 2 | $T_{\rm peak}^{{ \rm CO\,3-2}}$=164$\pm$10 K and $W_{4-3}^{{\rm HCO^+}}$=69$\pm$18 K km s$^{-1}$ |
| Mean HCO+ 4-3 integrated intensity at δx~15'' | 69 | ±18 | K km/s | 2 | $T_{\rm peak}^{{ \rm CO\,3-2}}$=164$\pm$10 K and $W_{4-3}^{{\rm HCO^+}}$=69$\pm$18 K km s$^{-1}$ |
| Density of compressed substructures | (1.0±0.5)e6 | ±0.5e6 | cm^-3 | 2 | $T$=200-300 K and $n_{\rm H}$=(1.0$\pm$0.5)$\times$10$^6$ cm$^{-3}$ |
| Compression factor | 5-30 | not stated | dimensionless | 2 | Hence, the over-dense substructures have compression factors $\sim$5-30 with respect to the ambient molecular gas. |
| Log-normal PDF parameters (z0, sigma) | z0=0.165, sigma=0.31 | not stated | dimensionless | 3 | We obtain $z_0$=0.165 and $\sigma$=0.31 from a fit (green curve). |
| Magnetic field (ambient, substructures) | ~200 and ~800 | not stated | microGauss | 4 | $B$$\approx$200 $\mu$G and $\approx$800 $\mu$G in the ambient and in the high-density substructures respectively |
| Mass of substructures | <~0.005 | not stated | Msun | 2 | is $\lesssim$0.005 $M_{\odot}$ (a mass per unit length of 0.3-1.0 $M_{\odot}$ pc$^{-1}$) |

## Qualitative findings

- No appreciable offset between H2 vibrational emission peaks and the edge of CO and HCO+ emission; H/H2 and C+/C/CO transitions nearly coincide  
  > "there is no appreciable offset between the peak of the H$_2$ vibrational emission (delineating the H/H$_2$ transition) and the edge of the observed CO and HCO$^+$ emission." (abstract)

## Claim tuples

- H: Static equilibrium PDR models correctly describe the Bar edge | E: Compare ALMA CO/HCO+ edge with H2 vibrational emission | R: CO/HCO+ edge coincides with H2* peaks | F: H/H2 and C+/CO zones are very close; dynamical effects matter | **supported**
- H: The cloud edge has been compressed by a high-pressure wave | E: HCO+ crosscuts, excitation models, PDF and pressure budget | R: Dense substructures with compression 5-30, P/k~2e8 K cm^-3, periodic maxima, log-normal PDF | F: A compression wave moves into the cloud | **supported**
- H: Photoablative flows exist in the atomic layer | E: Line profiles and velocity crosscuts of plumes | R: Two velocity components, one identical to Bar gas; dispersion maximum between fronts | F: Consistent with photoablative flows | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Temperature uncertain due to lack of high-J CO lines at high resolution; magnetic fields need observational confirmation  
  > "the $T$ uncertainty is determined by the lack of higher-$J$ CO lines, observed at high-angular resolution, to better constrain $T$ from models." (Methods)
- Caveat (inferred, ours): Density inferred from HCO+ intensity proxy with fixed abundance
- Caveat (inferred, ours): Equipartition magnetic field assumed
- Caveat (inferred, ours): Temperature from a single optically thick CO line
- Caveat (inferred, ours): Near-IR H2 image has saturation and extinction effects

## Reproducibility

- Data public (paper): ALMA project 2012.1.00352.S cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2012.1.00352.S." (Author information)
- Products in archive: _not stated_
- Missing: IRAM-30m maps (not stated as public)
- Missing: Imaging parameters
- Missing: Radiative transfer grid code and rates
- Missing: Near-IR H2 image from Walmsley
- Data volume (inferred): ~20-50 GB (27-pointing mosaic Band 7, ~2 h)
- Score (inferred): 3/5, ALMA data identified and processing outline given, but imaging parameters and single-dish merging are sparse; models use custom code.
- Rediscovery candidate: no, Requires IRAM-30m short spacings and custom radiative transfer models not specified in detail.

## Links

- Method: Pety & Rodríguez-Fernández 2010 (short-spacing/mosaic synthesis)
- Method: Goicoechea et al. 2006 (radiative transfer code)
- Companion: Cuadrado et al. 2015 (IRAM-30m line survey column densities)

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 36,
  "rate": 0.522
 },
 "evidence_ok": true
}
```
