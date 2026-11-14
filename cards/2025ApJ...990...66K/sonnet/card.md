# Reexamination of the CO Absorption Line in the M87 Nucleus

`2025ApJ...990...66K` | The Astrophysical Journal 2025 | first author: Kawanaka, Norita | arXiv: 2508.03015 | DOI: 10.3847/1538-4357/adf726

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: Is the CO(2–1) absorption line reported toward the M87 nucleus in archival ALMA data real, or an artifact of bandpass calibration and telluric contamination?  
  > "In this study, we have reanalyzed one of the ALMA datasets of the M87 nucleus used in RH24 to test its interpretation." (Introduction)
- Target **M87 nucleus**: coordinates RA 12h30m49.423s, Dec 12d23m28.043s  
  > "M87 is the central galaxy of the Virgo cluster, one of the closest cool-core clusters ($\sim 16.4~{\rm Mpc}$; (cite: 2010A&A...524A..71B))" (Introduction); "centered at R.A.: $12^h30^m49.423$, decl.: $12^d23^m28.043$" (3.1 TC (2015-06-15)); z/distance ~16.4 Mpc  
  > "M87 is the central galaxy of the Virgo cluster, one of the closest cool-core clusters ($\sim 16.4~{\rm Mpc}$; (cite: 2010A&A...524A..71B))" (Introduction); "centered at R.A.: $12^h30^m49.423$, decl.: $12^d23^m28.043$" (3.1 TC (2015-06-15)); distance from Bird et al. 2010  
  > "M87 is the central galaxy of the Virgo cluster, one of the closest cool-core clusters ($\sim 16.4~{\rm Mpc}$; (cite: 2010A&A...524A..71B))" (Introduction); "centered at R.A.: $12^h30^m49.423$, decl.: $12^d23^m28.043$" (3.1 TC (2015-06-15))

## Data provenance

- ALMA projects: 2013.1.00073.S
- bands: Band 6, covering CO(2–1)  
  > "The observations were done in Band 6, covering the CO(2–1) transition." (2 Observational Data and Analysis)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: TC 43.3–1600 m; TE 21.4–783.5 m  
  > "43.3 / 1600" (Table 1)
- angular resolution: TC 0.53x0.44 arcsec; TE 0.28x0.1 arcsec  
  > "0.53 $\times$ 0.44" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: rms ~6 mJy/beam (TC), ~4 mJy/beam (TE) in cubes  
  > "The rms of in the CLEANed cube data TC and TE are $\sim 6~{\rm mJy}~{\rm beam}^{-1}$ and $\sim 4~{\rm mJy}~{\rm beam}^{-1}$, respectively." (2 Observational Data and Analysis)
- time on source: TC 876.96 s; TE 1753.92 s  
  > "| M87_a_06_TC | 876.960 | 2015-06-15" (Table 1)
- observing dates: TC 2015-06-15; TE 2015-08-16  
  > "| M87_a_06_TC | 876.960 | 2015-06-15 | 0.53 $\times$ 0.44 | -41.86 | 1.270 | 43.3 / 1600 | 38 |" (Table 1); "| M87_a_06_TE | 1753.920 | 2015-08-16 | 0.28 $\times$ 0.1 | 12.19 | 1.270 | 21.4 / 783.5 | 34 |" (Table 1)
- pi or archival as stated: Archival  
  > "We utilize the ALMA archival data of the central region of M87" (2 Observational Data and Analysis)
- Line: CO J=2–1 (230.538 GHz)
- External data: CO(1–0) absorption optical depth 0.3±0.02 from RH24 (project 2012.1.00661.S)  
  > "RH24 analyzed CO(1–0) transition line using another dataset, 2012.1.00661.S, and evaluate its optical depth as $0.3\pm 0.02$." (4.2 Revised Constraint on the Molecular Gas) [from Ray & Hwang 2024 (cite: 2024ApJ...974....5R)]
- External data: Excitation temperature Tex=5 K of Hydra A cloud  
  > "$T_{\rm ex}=5~{\rm K}$ (cite: 2020MNRAS.496..364R)" (3.1 TC (2015-06-15)) [from (cite: 2020MNRAS.496..364R)]
- External data: Einstein A coefficient 7.36e-7 s^-1  
  > "$A_{ul}=7.36\times 10^{-7}~{\rm s}^{-1}$ (cite: 1996A&AS..117..557C)" (3.1 TC (2015-06-15)) [from (cite: 1996A&AS..117..557C)]
- External data: CO-to-H2 abundance 1.1e-4  
  > "Using the CO-to-${\rm H}_2$ conversion factor in the Milky Way, $1.1\times 10^{-4}$ (cite: 2010ApJ...721..686P)" (3.1 TC (2015-06-15)) [from (cite: 2010ApJ...721..686P)]
- External data: Systemic velocity of M87 ≃1284 km/s  
  > "the systemic velocity of M87 is $\simeq 1284~{\rm km}~{\rm s}^{-1}$ (cite: 2011MNRAS.413..813C)" (3.1 TC (2015-06-15)) [from (cite: 2011MNRAS.413..813C)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.4.0 for TC, 4.5.0 for TE  
  > "ver. 4.4.0 for TC, and ver. 4.5.0 for TE" (2 Observational Data and Analysis)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: TC: Titan flux reference, 3C 273 bandpass; TE: 3C 273 for flux, bandpass, phase  
  > "For the data TC, Titan was used as the flux reference." (3.2 TE (2015-08-16)); "For the data TE, the flux, bandpass, and phase calibrator are all the same, that is 3C 273." (3.2 TE (2015-08-16))
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "Image deconvolution was done using CASA task `tclean` with a threshold of $3\sigma$." (2 Observational Data and Analysis)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "We used Briggs weighting with a robust parameter of 0.5." (2 Observational Data and Analysis)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: automasking, niter=100000  
  > "We generated the CLEANed cube data using the automasking method with `niter=100000`." (2 Observational Data and Analysis)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 3 km/s velocity resolution  
  > "We adopted the velocity resolution of $3~{\rm km}~{\rm s}^{-1}$ for both datasets." (2 Observational Data and Analysis)
- final beam: _not stated_
- final rms: ~6 mJy/beam (TC), ~4 mJy/beam (TE)  
  > "The rms of in the CLEANed cube data TC and TE are $\sim 6~{\rm mJy}~{\rm beam}^{-1}$ and $\sim 4~{\rm mJy}~{\rm beam}^{-1}$, respectively." (2 Observational Data and Analysis)

### Inherited from earlier work

- Rigid-rotor approximation for partition function and E_l  
  > "Following (cite: 2019MNRAS.482.2934A), we use the rigid-rotor approximation" (3.1 TC (2015-06-15)) [from (cite: 2019MNRAS.482.2934A)]
- Column density formula  
  > "using the formula (cite: 2015PASP..127..266M)" (3.1 TC (2015-06-15)) [from (cite: 2015PASP..127..266M)]
- Optical depth ratio formula for Tex  
  > "using the formula (cite: 2003ApJ...595..167B)" (4.2 Revised Constraint on the Molecular Gas) [from (cite: 2003ApJ...595..167B)]

### Not stated but needed to reproduce (our reading)

- Exact recipe for re-running bandpass calibration without removing the telluric feature (CASA commands, channels flagged or interpolated)
- Whether the archive calibration scripts or the README were used directly
- Line-free channels and continuum subtraction method
- Image size and cell size
- Spectral window layout and frequency setup
- Details of the Tsys and atmospheric transmission analysis
- Derivation of the 1.3e18 to 3.4e17 cm^-2 column density limits (assumed Tex)

## Analysis recipe

1. **Image archival TC and TE cubes**: CASA tclean cubes with Briggs weighting and automasking  
  > "We used Briggs weighting with a robust parameter of 0.5." (2 Observational Data and Analysis)
   - software: CASA
   - parameter: robust 0.5, 3 km/s channels, threshold 3 sigma, niter=100000  
  > "We generated the CLEANed cube data using the automasking method with `niter=100000`." (2 Observational Data and Analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract nuclear spectra and fit absorption**: Spectrum from central region 0.77x0.59 arcsec; Gaussian fit of absorption; tau = ln(Scont/Sobs)  
  > "From the Gaussian fit, we obtain the continuum flux level, the flux at the line center, the line center velocity, and the line width" (3.1 TC (2015-06-15))
   - software: CARTA
   - fitting: Gaussian fit (details not stated)  
  > "From the Gaussian fit, we obtain the continuum flux level, the flux at the line center, the line center velocity, and the line width as" (Results, TC (2015-06-15))
   - validation: _not stated_
3. **Derive column density**: Column density from optical depth with rigid rotor, Tex=5 K, CO/H2=1.1e-4  
  > "With the approximation of $\int \tau_{ul}dv \simeq \tau_{ul}\delta v$ where $\delta v$ is the line width" (3.1 TC (2015-06-15))
   - assumption: Tex = 5 K from Hydra A; Milky Way CO/H2 abundance  
  > "Here we refer to the excitation temperature obtained for the molecular cloud in the nucleus of Hydra A, $T_{\rm ex}=5~{\rm K}$" (3.1 TC (2015-06-15))
   - fitting: _not stated_
   - validation: Compared with RH24 value; factor of three difference unexplained  
  > "The origin of the difference of a factor of three is not clear." (3.1 TC (2015-06-15))
4. **Check bandpass calibrator spectra and Tsys**: Compare 3C 273 spectra in TC and TE and Tsys spectrum around 230 GHz  
  > "To determine which calibration procedure is valid, we examined the frequency dependence of the system noise temperature ($T_{\rm sys}$) for each dataset." (4.1 Bandpass Calibration)
   - fitting: _not stated_
   - validation: TE bandpass keeps the feature, and Tsys rises near 229.6 GHz, indicating telluric origin  
  > "One can see a slight increase in $T_{\rm sys}$ around the frequency of $229.6~{\rm GHz}$." (4.1 Bandpass Calibration)
5. **Recalibrate TC and derive upper limits**: Reanalyze TC with bandpass spectrum including the absorption; 3 sigma optical depth limit; convert to column density, mass, and Tex limit  
  > "we reanalyzed the TC data using the bandpass calibration spectrum without removing the absorption feature that seems to originate from the telluric contamination." (4.1 Bandpass Calibration)
   - software: CASA
   - fitting: _not stated_
   - validation: Absorption disappears in recalibrated TC  
  > "One can see that the absorption feature that was found in the previous analysis (see the upper panel of Figure 1) has completely disappeared." (4.1 Bandpass Calibration)

## Software

- **CASA** 4.4.0 (TC), 4.5.0 (TE): Calibration and tclean imaging  
  > "ver. 4.4.0 for TC, and ver. 4.5.0 for TE" (2 Observational Data and Analysis)
- **CARTA** 4.1.0: Spectral analysis  
  > "we utilized the Cube Analysis and Rendering Tool for Astronomy (CARTA; version 4.1.0)" (2 Observational Data and Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| TC continuum flux (original calibration) | 1.660 | not stated | Jy | 2 | we obtain the continuum flux level, the flux at the line center, the line center velocity, and the line width as $1.660~{\rm Jy}$ |
| TC optical depth tau_21 (original) | 0.05 | not stated | dimensionless | 2 | In case of TC, we have $\tau_{21,\rm TC}\simeq 0.05$. |
| N_CO from original TC absorption | 1.1e15 | not stated | cm^-2 | 3 | we can estimate the column density of CO molecules as $N_{\rm CO}\sim 1.1\times 10^{15}~{\rm cm}^{-2}$ |
| N_H2 from original TC absorption | 1.0e19 | not stated | cm^-2 | 3 | we have the hydrogen molecule column density as $N_{\rm{H}_2}\sim 1.0\times 10^{19}~{\rm cm}^{-2}$ |
| TE optical depth upper limit | 0.0190 | not stated | dimensionless | 2 | $\tau_{21,{\rm TE}}\lesssim 0.0190$ |
| TC recalibrated tau_21 upper limit | 0.00596 | not stated | dimensionless | 5 | $\tau_{21,{\rm TC}}\lesssim 0.00596$ |
| N_H2 upper limit from recalibrated TC (Sec 4.1) | 1.3e18 | not stated | cm^-2 | 5 | $N_{{\rm H}_2}\lesssim 1.3\times 10^{18}~{\rm cm}^{-2}$ |
| Molecular cloud mass upper limit (r~50 pc) | 50 | not stated | Msun | 5 | the upper limit of the molecular gas cloud can be estimated as $m_{\rm cloud}\lesssim r^2 m_{{\rm H}_2}N_{{\rm H}_2}\sim 50M_{\odot}$ |
| Revised N_H2 upper limit (Sec 4.2/summary) | 3.4e17 | not stated | cm^-2 | 5 | ($\lesssim 3.4\times 10^{17}~{\rm cm}^{-2}$) |
| Excitation temperature upper limit | 1.20 | not stated | K | 5 | $$T_{\rm ex}\lesssim 1.20~{\rm K}.$$ |
| Total molecular mass upper limit (summary) | 13 | not stated | Msun | 5 | that of its total mass is $\lesssim 13M_{\odot}$ |

## Qualitative findings

- The CO(2–1) absorption feature is due to telluric contamination left in the TC data by the bandpass calibration, not M87 gas.  
  > "does not originate from M87 but instead results from telluric contamination" (abstract)

## Claim tuples

- H: Is the CO(2–1) absorption in M87 TC data intrinsic to M87? | E: Compared TC and TE data, bandpass calibrator spectra and Tsys, then recalibrated TC with the atmospheric feature kept | R: Absorption seen in TC disappears after recalibration; TE shows none; tau limit 0.00596 | F: The feature is telluric, and only an upper limit on molecular gas exists | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Fast-moving molecular cloud or multiple moving continuum sources as explanation of variability (not tested)  
  > "one could assume a fast moving molecular cloud in the vicinity of the SMBH or fast moving multiple continuum sources inside the AGN core" (5 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Continuum flux differs by ~45% between epochs; possible unnoticed flux scaling errors  
  > "However, there may be some unnoticed flux scaling errors which could cause such an apparent variability." (3.2 TE (2015-08-16))
- Caveat (inferred, ours): Recalibration details are sparse and rely on the README and archive script
- Caveat (inferred, ours): Tex assumed from Hydra A
- Caveat (inferred, ours): The upper-limit conversions (1.3e18 vs 3.4e17 cm^-2, 50 vs 13 Msun) are not clearly derived
- Caveat (inferred, ours): Mass limit depends on assumed cloud size

## Reproducibility

- Data public (paper): Archival ALMA data  
  > "We utilize the ALMA archival data of the central region of M87" (2 Observational Data and Analysis)
- Products in archive: _not stated_
- Missing: Custom bandpass recalibration script
- Missing: Spectral window and channel details
- Missing: Origin of the 3.4e17 and 13 Msun limits
- Data volume (inferred): ~tens of GB
- Score (inferred): 3/5, Public data and a simple recipe, but the key recalibration step is under-specified.
- Rediscovery candidate: no, The key result depends on a custom recalibration that is not fully specified.

## Links

- Companion: Ray & Hwang 2024 (cite: 2024ApJ...974....5R) (Original claimed detection being re-examined)
- Companion: Li 2022 (cite: Li2022) (Earlier atmospheric modeling of same dataset)
- Companion: Boizelle et al. 2025 (cite: 2025arXiv250303249B) (Concurrent analysis of same dataset)
- Related: 2012.1.00661.S

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2012.1.00661.S"
 ],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 43,
  "rate": 0.589
 },
 "evidence_ok": true
}
```
