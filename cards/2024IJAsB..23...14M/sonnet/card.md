# Detection and prebiotic chemistry of possible glycine precursor molecule methylenimine towards the hot molecular core G10.47+0.03

`2024IJAsB..23...14M` | International Journal of Astrobiology 2024 | first author: Manna, Arijit | arXiv: 2404.12212 | DOI: 10.1017/S1473550424000107

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: astrochemistry, star_formation
- Question: Can the possible glycine precursor methylenimine (CH2NH) be detected towards the hot core G10.47+0.03 with ACA, and what are its column density, temperature and abundance, and likely formation route?  
  > "we successfully identified the rotational emission lines of CH$_{2}$NH towards the hot molecular core G10.47+0.03 using the Atacama Compact Array (ACA)." (abstract)
- Target **G10.47+0.03**: coordinates 18:08:38.232, –19:51:50.400 (J2000)  
  > "The observed phase centre of the hot molecular core G10.47+0.03 is ($\alpha,\delta$)$_{\rm J2000}$ = 18:08:38.232, –19:51:50.400." (2. Observation and data reductions); "which is located at a distance of 8.6 kpc with a luminosity of 5$\times$10$^{5}$ L$_{\odot}$ (cite: cer10; san14)" (1. Introduction); z/distance 8.6 kpc  
  > "The observed phase centre of the hot molecular core G10.47+0.03 is ($\alpha,\delta$)$_{\rm J2000}$ = 18:08:38.232, –19:51:50.400." (2. Observation and data reductions); "which is located at a distance of 8.6 kpc with a luminosity of 5$\times$10$^{5}$ L$_{\odot}$ (cite: cer10; san14)" (1. Introduction); distance from (cite: cer10; san14)  
  > "The observed phase centre of the hot molecular core G10.47+0.03 is ($\alpha,\delta$)$_{\rm J2000}$ = 18:08:38.232, –19:51:50.400." (2. Observation and data reductions); "which is located at a distance of 8.6 kpc with a luminosity of 5$\times$10$^{5}$ L$_{\odot}$ (cite: cer10; san14)" (1. Introduction)

## Data provenance

- ALMA projects: 2016.2.00005.S
- bands: ACA Band 4  
  > "The observations were made with ACA band 4 with spectral ranges of 127.47–128.47 GHz, 129.74–130.74 GHz, 139.07–140.07 GHz, and 140.44–141.44 GHz" (2. Observation and data reductions)
- frequencies and spectral setup: 127.47–128.47, 129.74–130.74, 139.07–140.07, 140.44–141.44 GHz; 488 kHz resolution  
  > "spectral ranges of 127.47–128.47 GHz, 129.74–130.74 GHz, 139.07–140.07 GHz, and 140.44–141.44 GHz and a corresponding spectral resolution of 488 kHz" (2. Observation and data reductions)
- continuum bandwidth: _not stated_
- arrays: ACA 7-m array, 11 antennas  
  > "The observation was carried out on September 16, 2017, using 11 antennas." (2. Observation and data reductions)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 10.48″×6.28″ to 12.08″×6.90″ (cube beams)  
  > "The final spatial resolution of the spectral data cubes was 10.48$^{\prime\prime}\times$6.28$^{\prime\prime}$, 10.82$^{\prime\prime}\times$6.39$^{\prime\prime}$" (2. Observation and data reductions)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: September 16, 2017  
  > "The observation was carried out on September 16, 2017, using 11 antennas." (2. Observation and data reductions)
- pi or archival as stated: Archival, PI Rivilla, Cycle 4  
  > "We used the archival data of G10.47+0.03 in cycle 4" (2. Observation and data reductions)
- Line: CH2NH 2(0,2)–1(0,1) (127.856 GHz)
- Line: CH2NH 6(2,4)–7(1,7) (129.904 GHz)
- Line: CH2NH 10(3,7)–11(2,10) (140.810 GHz)
- External data: H2 column density of 1.30e23 cm^-2 used for abundance  
  > "the column density of H$_{2}$ towards G10.47+0.03 was 1.30$\times$10$^{23}$ cm$^{-2}$ (cite: suz16)" (3.3 Rotational diagram analysis of CH$_{2}$NH) [from (cite: suz16)]
- External data: Systemic velocity 68.50 km/s  
  > "The systematic velocity ($V_{LSR}$) of G10.47+0.03 is 68.50 km s$^{-1}$ (cite: rof11)." (3.2 Identification of the CH$_{2}$NH in the G10.47+0.03) [from (cite: rof11)]
- External data: Partition functions of CH2NH from CDMS  
  > "The rotational partition function of CH$_{2}$NH at 75 K is 740.457, that at 150 K is 2084.970, and that at 300 K is 5892.504 (cite: mu05)." (3.3 Rotational diagram analysis of CH$_{2}$NH) [from (cite: mu05)]
- Simulation/model as data: Two-phase warm-up NAUTILUS model abundance of CH2NH (~1e-9–1e-8 gas phase) from Suzuki et al. 2016  
  > "the modelled abundance of CH$_{2}$NH varied between $\sim$10$^{-9}$–10$^{-8}$ in the gas phase." (4.2. Comparison with modelled and observed abundance of CH$_{2}$NH)

## Processing

### Calibration

- pipeline or manual: CASA ALMA pipeline  
  > "we used the Common Astronomy Software Application (CASA 5.4.1) with an ALMA data reduction pipeline (cite: mc07)" (2. Observation and data reductions)
- casa version: CASA 5.4.1  
  > "Common Astronomy Software Application (CASA 5.4.1)" (2. Observation and data reductions)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1924–2914; Perley-Butler 2017 model  
  > "the flux calibrator and bandpass calibrator were J1924–2914, and the phase calibrator was J1833–210B." (2. Observation and data reductions); "we used the Perley-Butler 2017 flux calibrator model" (2. Observation and data reductions)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean, specmode=cube  
  > "To produce spectral images, we used the SPECMODE = CUBE parameter in the TCLEAN task." (2. Observation and data reductions)
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.5  
  > "We used the CASA task TCLEAN with a Briggs weighting robust value of 0.5" (2. Observation and data reductions)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in uv plane  
  > "For continuum and background subtraction, we used task UVCONTSUB in the UV plane of the separated calibrated data." (2. Observation and data reductions)
- line free channels: _not stated_
- primary beam correction: impbcor  
  > "we used the CASA task IMPBCOR to correct the primary beam pattern in continuum images and spectral data cubes." (2. Observation and data reductions)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 10.48″×6.28″, 10.82″×6.39″, 12.08″×6.90″, 12.08″×6.79″  
  > "12.08$^{\prime\prime}\times$6.90$^{\prime\prime}$, and 12.08$^{\prime\prime}\times$6.79$^{\prime\prime}$" (2. Observation and data reductions)
- final rms: _not stated_

### Inherited from earlier work

- Data analysis flow chart  
  > "The data analysis flow chart is shown in (cite: man24c)." (2. Observation and data reductions) [from (cite: man24c)]
- Emitting-region size equation  
  > "$\theta_{50} = 2\sqrt{A/\pi}$ indicates the diameter of the circle whose area ($A$) corresponds to the 50% line peak of CH$_{2}$NH" (3.4 Spatial distribution of CH$_{2}$NH in the G10.47+0.03) [from (cite: riv17; man22c; man23c)]

### Not stated but needed to reproduce (our reading)

- Image size, cell size, cleaning threshold, niter, masks
- Line-free channels for uvcontsub
- Spectral window / channel width after imaging and velocity frame
- CASSIS MCMC priors and fit ranges
- Spectral extraction region centre
- Source size and partition function used for the CH2NH rotational-diagram fit
- Details of the glycine upper limits (line frequencies, assumed Tex, linewidth)

## Analysis recipe

1. **Calibrate and image**: CASA pipeline calibration, mstransform, uvcontsub, tclean cubes, impbcor  
  > "We used the CASA task TCLEAN with a Briggs weighting robust value of 0.5, to create continuum and spectral images of the G10.47+0.03." (2. Observation and data reductions)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum**: 2D Gaussian fit to continuum images  
  > "we fitted the 2D Gaussian over the continuum emission images using the CASA task IMFIT" (3.1 Continuum emission towards the G10.47+0.03)
   - software: CASA imfit
   - fitting: _not stated_
   - validation: _not stated_
3. **Identify CH2NH lines via LTE modelling**: Extract spectrum in 23.75″ circle, subtract 2nd-order polynomial baseline, fit LTE model with CDMS in CASSIS using MCMC  
  > "To fit the LTE model spectra of CH$_{2}$NH over the millimeter wavelength spectra of G10.47+0.03, we applied the Markov Chain Monte Carlo (MCMC) algorithm in CASSIS." (3.2 Identification of the CH$_{2}$NH in the G10.47+0.03)
   - software: CASSIS, CDMS
   - parameter: V_LSR = 68.50 km/s  
  > "The systematic velocity ($V_{LSR}$) of G10.47+0.03 is 68.50 km s$^{-1}$ (cite: rof11)." (3.2 Identification of the CH$_{2}$NH in the G10.47+0.03)
   - assumption: LTE valid given gas density 7e7 cm^-3  
  > "the gas density of the warm inner region of the hot core was 7$\times$10$^{7}$ cm$^{-3}$ (cite: rof11)" (3.2 Identification of the CH$_{2}$NH in the G10.47+0.03)
   - fitting: MCMC in CASSIS  
  > "we applied the Markov Chain Monte Carlo (MCMC) algorithm in CASSIS" (3.2 Identification of the CH$_{2}$NH in the G10.47+0.03)
   - validation: Lines checked non-blended with CDMS and Splatalogue  
  > "we find that all the detected transitions of are not blended with other nearby molecular transitions." (3.2 Identification of the CH$_{2}$NH in the G10.47+0.03)
4. **Rotational diagram**: Gaussian fits (Levenberg-Marquardt) to lines, optically thin rotational diagram in CASSIS  
  > "fitting the Gaussian model over the observed spectra of CH$_{2}$NH using the Levenberg-Marquardt algorithm in CASSIS" (3.3 Rotational diagram analysis of CH$_{2}$NH)
   - software: CASSIS
   - assumption: Optically thin, LTE; N(H2)=1.30e23 cm^-2 for abundance  
  > "Initially, we assumed that the detected CH$_{2}$NH emission lines were optically thin and populated under the LTE conditions." (3.3 Rotational diagram analysis of CH$_{2}$NH)
   - fitting: Linear fit of ln(Nu/gu) vs Eu  
  > "Equation 3 indicates a linear relationship between the upper state energy ($E_{u}$) and $\ln(N_{u}/g_{u})$ of CH$_{2}$NH." (3.3 Rotational diagram analysis of CH$_{2}$NH)
   - validation: Compared with LTE-fit values (3.21e15 cm^-2, 210.5 K)  
  > "which are nearly similar to the estimated column density and rotational temperature of using the rotational diagram model." (3.3 Rotational diagram analysis of CH$_{2}$NH)
5. **Moment maps and emitting size**: immoments over line velocity ranges, imfit 2D Gaussian, deconvolve via theta_S  
  > "We created integrated emission maps of CH$_{2}$NH towards G10.47+0.03, using the CASA task IMMOMENTS." (3.4 Spatial distribution of CH$_{2}$NH in the G10.47+0.03)
   - software: CASA immoments, CASA imfit
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4.1: Calibration, imaging, imfit, immoments, impbcor  
  > "Common Astronomy Software Application (CASA 5.4.1)" (2. Observation and data reductions)
- **CASSIS** : LTE modelling with MCMC, Gaussian fits, rotational diagram  
  > "For LTE modelling, we used CASSIS (cite: vas15)." (3.2 Identification of the CH$_{2}$NH in the G10.47+0.03)
- **CDMS** : Spectroscopic database  
  > "with the Cologne Database for Molecular Spectroscopy (CDMS) database (cite: mu05)" (3.2 Identification of the CH$_{2}$NH in the G10.47+0.03)
- **Splatalogue** : Blending check and Sμ² values  
  > "As per the CDMS and online molecular database Splatalogue" (3.2 Identification of the CH$_{2}$NH in the G10.47+0.03)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH2NH column density (rotational diagram) | 3.40e15 | 0.2e15 | cm^-2 | 4 | (3.40$\pm$0.2)$\times$10$^{15}$ cm$^{-2}$ with a rotational temperature of 218.70$\pm$20 K |
| Rotational temperature | 218.70 | 20 | K | 4 | rotational temperature of 218.70$\pm$20 K |
| CH2NH fractional abundance wrt H2 | 2.61e-8 | not stated | dimensionless | 4 | The fractional abundance of CH$_{2}$NH with respect to H$_{2}$ towards G10.47+0.03 is 2.61$\times$10$^{-8}$. |
| LTE-fit column density | 3.21e15 | 1.5e15 | cm^-2 | 3 | the best-fit column density of CH$_{2}$NH was (3.21$\pm$1.5)$\times$10$^{15}$ cm$^{-2}$ with an excitation temperature of 210.50$\pm$32.82 K |
| Glycine conformer I upper limit | ≤1.02e15 | not stated | cm^-2 | 3 | $\leq$1.02$\times$10$^{15}$ cm$^{-2}$ and $\leq$2.36$\times$10$^{13}$ cm$^{-2}$ respectively |
| Emitting region size | 10.520″ to 10.781″ (0.43–0.45 pc) | not stated | arcsec | 5 | The emitting region of CH$_{2}$NH varied between 10.520$^{\prime\prime}$ and 10.781$^{\prime\prime}$. |

## Qualitative findings

- CH2NH emission is unresolved and peaks at the continuum position; no morphology conclusions possible  
  > "Therefore, we cannot draw any conclusions about the morphology of the integrated emission maps of CH$_{2}$NH towards G10.47+0.03." (3.4)

## Claim tuples

- H: CH2NH is detectable in G10.47+0.03 with ACA | E: LTE modelling of ACA Band 4 spectra | R: Three non-blended transitions identified | F: First interferometric detection of CH2NH in G10.47+0.03 | **supported**
- H: CH2NH arises from the warm inner hot core | E: Rotational diagram | R: Trot=218.7±20 K | F: Emission from warm region, unlike the 84 K of Suzuki et al. | **supported**
- H: Observed abundance matches the chemical model, indicating the formation route | E: Compare 2.61e-8 with the model of Suzuki et al. 2016 | R: Similar to modelled gas-phase abundance | F: CH2NH likely formed by gas-phase CH3 + NH | **partially**
- H: Glycine conformers can be detected | E: LTE search | R: Not detected; upper limits | F: Emission may be below the confusion limit | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Hyperfine lines unresolved and source not spatially resolved  
  > "the current spectral resolution is insufficient to resolve the hyperfine lines." (3.2)
- Caveat (inferred, ours): Three lines with a coarse ~10″ beam, large envelope contamination, and a single-temperature LTE model
- Caveat (inferred, ours): Abundance uses an H2 column from a single-dish study with different beam
- Caveat (inferred, ours): Model comparison is loose, with a ~1 dex range; conclusion on formation route is weak
- Caveat (inferred, ours): Source size set to the beam so beam dilution is uncertain; strong continuum optical depth ignored

## Reproducibility

- Data public (paper): Archival ALMA data, project 2016.2.00005.S  
  > "We used the archival data of G10.47+0.03 in cycle 4" (2. Observation and data reductions)
- Products in archive: _not stated_
- Missing: tclean image parameters and masks
- Missing: CASSIS fit priors and inputs
- Missing: Line-free channels
- Data volume (inferred): ~5-20 GB
- Score (inferred): 3/5, Public data and software named, but imaging and fit details are sparse.
- Rediscovery candidate: yes, Public ACA data, simple rotational-diagram recipe, numeric results.

## Links

- Method: (cite: man24c) (Data analysis flow chart)
- Method: (cite: vas15) (CASSIS)
- Companion: (cite: man22a) (Aminoacetonitrile in G10.47+0.03)
- Companion: (cite: suz16) (Earlier NRO CH2NH survey and chemical model)

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
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
  "stated": 43,
  "rate": 0.589
 },
 "evidence_ok": true
}
```
