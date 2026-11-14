# Molecular line study of the S-type AGB star W Aquilae. ALMA observations of CS, SiS, SiO and HCN

`2018A&A...617A..23B` | Astronomy and Astrophysics 2018 | first author: Brunner, M. | arXiv: 1806.01622 | DOI: 10.1051/0004-6361/201832724

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, astrochemistry
- Question: What are the spatial distribution, abundances and radial extent of CS, SiS, 29SiO and H13CN in the circumstellar envelope of the S-type AGB star W Aql, resolved with ALMA?  
  > "Section [5](#sec:radtransfer) describes the radiative transfer modeling based on the work of (cite: Danilovich2014), which is improved by the incorporation of the new ALMA data." (Introduction)
- Target **W Aql**: coordinates RA 19:15:23.379 DEC -07:02:50.38 (J2000)  
  > "current stellar position of RA 19:15:23.379 and DEC –07:02:50.38 J2000.0 (cite: Ramstedt2017)" (4.3 uv fitting); "Its distance is 395 pc, derived from the period-magnitude relation (cite: Whitelock2008) and 2MASS $K$ band magnitude (cite: Cutri2003)." (2 W Aql); z/distance 395 pc  
  > "current stellar position of RA 19:15:23.379 and DEC –07:02:50.38 J2000.0 (cite: Ramstedt2017)" (4.3 uv fitting); "Its distance is 395 pc, derived from the period-magnitude relation (cite: Whitelock2008) and 2MASS $K$ band magnitude (cite: Cutri2003)." (2 W Aql); distance from period-magnitude relation (Whitelock2008) and 2MASS K magnitude (Cutri2003)  
  > "current stellar position of RA 19:15:23.379 and DEC –07:02:50.38 J2000.0 (cite: Ramstedt2017)" (4.3 uv fitting); "Its distance is 395 pc, derived from the period-magnitude relation (cite: Whitelock2008) and 2MASS $K$ band magnitude (cite: Cutri2003)." (2 W Aql)

## Data provenance

- ALMA projects: 2012.1.00524.S
- bands: _not stated_
- frequencies and spectral setup: Four spectral windows centred at 331, 333, 343 and 345 GHz; 1875 MHz (main array) and 1992.187 MHz (ACA) bandwidth each; 488.281 kHz resolution  
  > "Four spectral windows, with a bandwidth of 1875 MHz (main array) and 1992.187 MHz (ACA) each, were observed, centered at 331, 333, 343 and 345 GHz, respectively." (3 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 12 m main array, ACA (7 m) and total power  
  > "combining ALMA main array observations (12 m diameter, long baselines), Atacama Compact Array (ACA) observations (7 m diameter, short baselines) and total power (TP) observations" (3 Observations and data reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.55" x 0.48" (PA 86.35 deg)  
  > "resulting in a beam of 0.55$^{\prime\prime\,} \times$ 0.48$^{\prime\prime\,}$ (PA 86.35$^\circ$)" (3 Observations and data reduction)
- max recoverable scale: 19 arcsec (main array + ACA)  
  > "the maximum recoverable scale for the used 12 m main array and ACA configuration is 19$^{\prime\prime\,}$" (4.3 uv fitting)
- sensitivity: rms 10 mJy/beam from line-free channels  
  > "The rms noise measured from line-free channels is 10 mJy/beam." (Table 1 notes)
- time on source: _not stated_
- observing dates: Cycle 1, March and April 2014  
  > "observed in March and April 2014, PI: Sofia Ramstedt" (3 Observations and data reduction)
- pi or archival as stated: PI Sofia Ramstedt, Cycle 1 binary star sample  
  > "W Aql was observed as part of a sample of binary stars with ALMA in Cycle 1 (observed in March and April 2014, PI: Sofia Ramstedt)" (3 Observations and data reduction)
- Line: CS 7-6 (342.8829 GHz)
- Line: H13CN 4-3 (345.3398 GHz)
- Line: SiS 19-18 (344.7795 GHz)
- Line: 29SiO 8-7 (342.9808 GHz)
- Line: SiO v=1 8-7 (344.9162 GHz)
- Line: SiS v=1 19-18 (343.1010 GHz)
- Line: 30SiS 19-18 (332.5503 GHz)
- Line: SiO v=2 8-7 (342.5044 GHz)
- Other facility **APEX, IRAM 30m, Herschel/HIFI (archival single-dish)**: Archival single-dish line intensities used to discriminate between equally good fits to ALMA data  
  > "with the integrated flux of the archival single-dish data being used – in most cases – to discriminate between two equally good fits to the ALMA data" (5.1 Modeling procedure)
- External data: Stellar parameters for radiative transfer modelling (distance, Teff, mass-loss rate, dust/gas ratio, luminosity, mass, expansion velocity, stellar velocity)  
  > "All parameters are adopted from (cite: Danilovich2014)." (Table 2 notes) [from (cite: Danilovich2014)]
- External data: CO modelling results and mass-loss rate  
  > "Our model uses the CO modeling results obtained by (cite: Danilovich2014) and refined by (cite: Ramstedt2017)." (5.1 Modeling procedure) [from (cite: Danilovich2014); (cite: Ramstedt2017)]
- External data: Archival single-dish line intensities (CS, SiS, 29SiO, H13CN)  
  > "| CS | $3 \to 2$ | 146.969 | IRAM | 17 | 6.96 | (cite: Danilovich2018) |  |" (List of archival spectral line observations) [from (cite: Danilovich2018); (cite: Danilovich2014); APEX Archive]
- External data: Molecular energy levels, frequencies and collisional rates  
  > "The energy levels, transition frequencies and Einstein A coefficients were taken from CDMS (cite: Muller2001; Muller2005)" (5.2.2 SiS) [from CDMS (Muller2001; Muller2005); JPL (Pickett1998); Yang2010; Dayou2006; Dumouchel2010]

## Processing

### Calibration

- pipeline or manual: Standard calibration with CASA; Ceres flux, J1924-2914 bandpass, J1911-2006 phase  
  > "Standard calibration was performed with the Common Astronomy Software Application (CASA), using Ceres as flux calibrator and the quasars J1924-2914 and J1911-2006 as bandpass calibrator and phase calibrator, respectively." (3 Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres  
  > "using Ceres as flux calibrator" (3 Observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN  
  > "Imaging of all spectral lines was carried out with CASA using the CLEAN algorithm with natural weighting" (3 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using the CLEAN algorithm with natural weighting" (3 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Iterative masking per channel and line  
  > "Iterative masking for each spectral channel and molecular line was used to optimize the imaging process with CLEAN." (3 Observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Main array + ACA combined in visibility plane with antenna-specific weighting; TP feathered in image plane  
  > "The combination of the main array and ACA data is conducted in the visibility plane with antenna-specific weighting, whereas the TP data is combined with the rest of the data via feathering in the image plane." (3 Observations and data reduction)
- smoothing: Channels binned to 1 km/s (strong lines) and 2 km/s (weak lines)  
  > "The spectral channels were binned to a velocity resolution of 1 km s$^{-1}$ and 2 km s$^{-1}$ for strong and weak spectral lines, respectively." (3 Observations and data reduction)
- final beam: 0.55" x 0.48" (PA 86.35 deg)  
  > "resulting in a beam of 0.55$^{\prime\prime\,} \times$ 0.48$^{\prime\prime\,}$ (PA 86.35$^\circ$)" (3 Observations and data reduction)
- final rms: 10 mJy/beam  
  > "The rms noise measured from line-free channels is 10 mJy/beam." (Table 1 notes)

### Inherited from earlier work

- Radiative transfer procedure (ALI code) and stellar parameters  
  > "following the same procedure as described in (cite: Danilovich2014)" (5.1 Modeling procedure) [from (cite: Danilovich2014)]
- Stellar position  
  > "current stellar position of RA 19:15:23.379 and DEC –07:02:50.38 J2000.0 (cite: Ramstedt2017)" (4.3 uv fitting) [from (cite: Ramstedt2017)]
- Velocity profile of the wind  
  > "and the velocity profile defined by (cite: Danilovich2014)" (5.2 Modeling results) [from (cite: Danilovich2014)]

### Not stated but needed to reproduce (our reading)

- CASA version used for calibration and imaging
- CLEAN threshold, mask criteria, cell size and image size
- Line-free channels and continuum subtraction method
- Flux calibration uncertainty and whether archive products were used as is
- uvmultifit settings (initial guesses, channel handling)
- Exact ALI model grid, fitting criterion and how best fit was judged beyond by-eye
- Wind velocity profile parameters; overdensity region choice justification
- Exact feathering procedure and TP scaling

## Analysis recipe

1. **Image and extract line properties**: CLEAN imaging of combined 12m+ACA+TP data, moment maps and spectra extracted with apertures  
  > "Imaging of all spectral lines was carried out with CASA using the CLEAN algorithm with natural weighting" (3 Observations and data reduction)
   - software: CASA
   - parameter: natural weighting; 1 or 2 km/s channels  
  > "The spectral channels were binned to a velocity resolution of 1 km s$^{-1}$ and 2 km s$^{-1}$ for strong and weak spectral lines, respectively." (3 Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit emission size in uv plane**: Fit circular Gaussian, then Gaussian plus delta function, to visibilities per channel (main array + ACA only)  
  > "we use the CASA tool *uvmultifit* (cite: Marti-Vidal2014), to fit geometric flux models to the bright emission regions of all spectral lines." (4.3 uv fitting)
   - software: uvmultifit, CASA
   - parameter: Gaussian position, flux density, FWHM; delta component at same position  
  > "described by its position (relative to the current stellar position of RA 19:15:23.379 and DEC –07:02:50.38 J2000.0 (cite: Ramstedt2017)), flux density, and FWHM size" (4.3 uv fitting)
   - assumption: Gaussian intensity distribution; uncertainties assume reduced chi2 of 1  
  > "meaning that the reduced $\chi^2$ can be assumed to be similar to its expected value of unity" (Appendix uv-fitting)
   - fitting: chi2 minimisation; uncertainties from post-fit covariance matrix  
  > "estimates the uncertainties of the fitted parameters from the curvature of the $\chi^2$ distribution at its minimum via the diagonal elements of the post-fit covariance matrix" (Appendix uv-fitting)
   - validation: Residual images imaged and checked as Gaussian noise; Monte Carlo exploration of chi2 PDFs  
  > "we have performed a Monte Carlo analysis of our Gaussian source model plus additional delta component across the full parameter space" (Appendix uv-fitting)
3. **Radiative transfer modelling of abundance and e-folding radius**: ALI non-LTE models with Gaussian abundance profile fitted to ALMA azimuthally averaged radial profiles (0.6" beam) and 4" line profiles, using single-dish data to discriminate  
  > "we used the azimuthally averaged radial profile from the ALMA observations (convolved with a 0.6$^{\prime\prime\,}$ beam) and the ALMA line profiles convolved with a 4$^{\prime\prime\,}$ beam" (5.1 Modeling procedure)
   - software: ALI
   - parameter: Free parameters f0 and Re per molecule; radial points 0.05" to 0.75" in 0.1" steps  
  > "The Gaussian models have two free parameters per molecular species: $f_0$, the central fractional abundance, and $R_e$, the $e$-folding radius." (5.1 Modeling procedure)
   - assumption: Distance 395 pc, Mdot 3e-6 Msun/yr, L 7500 Lsun, expansion velocity 16.5 km/s, spherical symmetry  
  > "| Gas mass-loss rate         | $3\times 10^{-6}$  M$_{\odot}$/yr $^{b}$ |" (Table 2)
   - fitting: Manual best-fit selection; no sampler stated  
  > "To adjust the H$_2$ number density, we multiplied a section of the smooth-wind radial profile (given by the mass-loss rate determined by (cite: Ramstedt2017), listed in Table [1]" (Modeling results)
   - validation: Compared with archival single-dish line profiles  
  > "In general, the ALMA observations are reasonably well described by the models when looking at the radial intensity profiles, as are the single-dish observations." (5.2 Modeling results)
4. **Add wind overdensity to reproduce radial tail**: Multiply H2 density in a radial section by integer factors up to 10; pick the one not over-predicting the tail for any molecule  
  > "we multiplied a section of the smooth-wind radial profile (given by the mass-loss rate determined by (cite: Ramstedt2017), listed in Table [1](#tab:stellarparameters), and the velocity profile defined by (cite: Danilovich2014)) by integer factors up to 10." (5.2 Modeling results)
   - software: ALI
   - parameter: factor of five between 8e15 and 1.5e16 cm  
  > "The best fit for all molecules was found for an overdensity of a factor of five between $8\times 10^{15}$ cm and $1.5\times 10^{16}$ cm." (5.2 Modeling results)
   - fitting: _not stated_
   - validation: _not stated_
5. **Derive isotopic ratios**: Ratios of modelled abundances (28SiO/29SiO, 28SiS/30SiS, H12CN/H13CN), using Danilovich2014 abundances for main isotopologues  
  > "Previous models by (cite: Danilovich2014) estimate a $^{28}$SiO abundance of $2.9 \times 10^{-6}$, which we can use to derive the $^{28}$SiO/$^{29}$SiO ratio, resulting in a value of 11.6." (6.4.1 Silicon)
   - assumption: SiO and SiS ratios trace the Si isotope ratios; HCN ratio traces 12C/13C  
  > "By assuming that both SiO and SiS ratios are good tracers for the Si ratios" (6.4.1 Silicon)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration and CLEAN imaging  
  > "Standard calibration was performed with the Common Astronomy Software Application (CASA)" (3 Observations and data reduction)
- **uvmultifit** : uv-plane fitting of Gaussian and delta components  
  > "we use the CASA tool *uvmultifit* (cite: Marti-Vidal2014)" (4.3 uv fitting)
- **ALI** : Accelerated lambda iteration radiative transfer modelling  
  > "we used ALI, an accelerated lambda iteration code (cite: Rybicki1991; Maercker2008)" (5.1 Modeling procedure)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CS f0 | 1.20e-6 | 0.05e-6 | relative to H2 | 3 | / CS         / $(1.20 \pm 0.05) \times 10^{-6}$ / $7.0\times 10^{15}$ / $\times2$    / |
| CS Re | 7.0e15 | not stated | cm | 3 | / CS         / $(1.20 \pm 0.05) \times 10^{-6}$ / $7.0\times 10^{15}$ / $\times2$    / |
| SiS f0 | 1.50e-6 | 0.05e-6 | relative to H2 | 3 | / SiS        / $(1.50 \pm 0.05)\times 10^{-6}$  / $6.0\times 10^{15}$ / $\times3$    / |
| SiS Re | 6.0e15 | not stated | cm | 3 | / SiS        / $(1.50 \pm 0.05)\times 10^{-6}$  / $6.0\times 10^{15}$ / $\times3$    / |
| 30SiS f0 | 1.15e-7 | 0.05e-7 | relative to H2 | 3 | $^{30}$SiS / $(1.15 \pm 0.05)\times 10^{-7}$  / $3.5\times 10^{15}$ |
| 29SiO f0 | 2.50e-7 | 0.10e-7 | relative to H2 | 3 | $^{29}$SiO / $(2.50 \pm 0.10)\times 10^{-7}$  / $1.4\times 10^{16}$ |
| 29SiO Re | 1.4e16 | not stated | cm | 3 | $^{29}$SiO / $(2.50 \pm 0.10)\times 10^{-7}$  / $1.4\times 10^{16}$ |
| H13CN f0 | 1.75e-7 | 0.05e-7 | relative to H2 | 3 | H$^{13}$CN / $(1.75 \pm 0.05)\times 10^{-7}$  / $4.7\times 10^{16}$ |
| H13CN Re | 4.7e16 (text and table differ: 4.7e15 in modelling section) | not stated | cm | 3 | For H$^{13}$CN, we get a radius of $4.7 \times 10^{16}$ cm |
| 28SiO/29SiO ratio | 11.6 | not stated | dimensionless | 5 | resulting in a value of 11.6 |
| 28SiS/30SiS ratio | 13.0 | not stated | dimensionless | 5 | we find the abundance ratio of $^{28}$SiS/$^{30}$SiS =13.0 |
| 29Si/30Si ratio | 1.1 | not stated | dimensionless | 5 | which results in a value of 1.1 |
| H12CN/H13CN ratio | 17 | 6 | dimensionless | 5 | we derive a H$^{12}$CN/H$^{13}$CN ratio of $17 \pm 6$ |
| Wind overdensity factor | 5 between 8e15 and 1.5e16 cm | not stated | dimensionless | 4 | The best fit for all molecules was found for an overdensity of a factor of five between $8\times 10^{15}$ cm and $1.5\times 10^{16}$ cm. |

## Qualitative findings

- Line emission is resolved, with a compact component and fainter elongation along NE/SW, the binary orbit direction, matching CO clumps.  
  > "The elongation is oriented in the north-east and south-west (NE/SW) directions, which is also the direction of the binary orbit." (4.1 Morphology of spectral line emission)
- SiS line shows a strong red-shifted asymmetry near -21 km/s.  
  > "Additionally, the SiS line shows a strong asymmetry with an excess in red shifted emission relative to the stellar rest frame at around -21 km s$^{-1}$." (4.2 Spectral features)

## Claim tuples

- H: Does a Gaussian alone describe the compact emission? | E: uv fits with Gaussian vs Gaussian plus delta | R: Adding a delta component yields significantly better residuals and recovers more flux | F: Compact central component needed in addition to Gaussian | **supported**
- H: Can smooth-wind Gaussian abundance models explain the ALMA radial profiles? | E: Radiative transfer with and without overdensity | R: A tail beyond ~1" needs an overdensity (factor 5) | F: Overdense, binary-induced region improves fits | **supported**
- H: Do 29SiO and H13CN share the radial extent of main isotopologues? | E: Compare ALMA-derived Re to assumed values | R: Rarer isotopologues have larger radii (H13CN about 3x) | F: Assumed identical distributions are not valid | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: uv fitting avoids deconvolution artefacts  
  > "image artefacts are inevitably introduced during deconvolution, it is reasonable to analyze the observations already in the uv plane" (4.3 uv fitting)
- Alternative: Non-Gaussian abundance profile rejected as unphysical (increasing abundance with radius)  
  > "such models that fit the observations well were not physically realistic, with increasing abundances with radius" (5.2 Modeling results)
- How they decided it was enough: _not stated_
- Limitation (authors): Spherical symmetry assumed despite asymmetric emission  
  > "The most obvious limitation of the radiative transfer models is that they assume spherical symmetry" (6.2 Limitations of radiative transfer models)
- Limitation (authors): Weak lines too low S/N for uv fitting  
  > "the signal-to-noise ratio (S/N) for all weak lines is too low for confident fitting" (4.3 uv fitting)
- Caveat (inferred, ours): Best-fit selection appears manual with no formal uncertainty on Re
- Caveat (inferred, ours): Overdensity abundance scaling for CS and SiS is ad hoc
- Caveat (inferred, ours): Quoted H13CN Re inconsistent between text and table
- Caveat (inferred, ours): Single-dish data taken at different epochs

## Reproducibility

- Data public (paper): ALMA project code given in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2012.1.00524.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and CLEAN parameters
- Missing: ALI input files and fit procedure
- Missing: uvmultifit configuration
- Data volume (inferred): Likely tens to hundreds of GB (12m+ACA+TP, 4 spectral windows, mosaic)
- Score (inferred): 3/5, Public data and clear modelling approach, but imaging/ALI details and versions missing.
- Rediscovery candidate: no, Modelling relies on a custom ALI code and inherited setups; imaging parameters are incomplete.

## Links

- Method: (cite: Marti-Vidal2014) (uvmultifit)
- Method: (cite: Danilovich2014) (radiative transfer procedure and parameters)
- Companion: (cite: Ramstedt2017) (CO observations from the same ALMA project)
- Related: ALMA Cycle 1 binary AGB star sample (PI Ramstedt)

## Checks

```json
{
 "quotes": 84,
 "quotes_ok": 84,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 54,
  "rate": 0.667
 },
 "evidence_ok": true
}
```
