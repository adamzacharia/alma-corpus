# Thermal Physics of the Inner Coma: ALMA Studies of the Methanol Distribution and Excitation in Comet C/2012 K1 (PanSTARRS)

`2017ApJ...837..177C` | The Astrophysical Journal 2017 | first author: Cordiner, M. A. | arXiv: 1701.08258 | DOI: 10.3847/1538-4357/aa6211

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: How do the CH3OH distribution, rotational temperature and excitation vary with distance from the nucleus in the inner coma of comet C/2012 K1 (PanSTARRS)?  
  > "Two-dimensional maps of the line-of-sight average rotational temperature ($T_{rot}$) were derived, covering spatial scales $0.3''-1.8''$" (abstract)
- Target **C/2012 K1 (PanSTARRS)**: coordinates _not stated_; z/distance geocentric distance 1.96-1.97 AU  
  > "while the comet was at a heliocentric distance $r_H=1.42$-1.43 AU and geocentric distance $\Delta=1.96$-1.97 AU" (2 ALMA CH$_3$OH observations); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.01061.S
- bands: Band 6 (K=3-2 near 251.9 GHz) on June 28; Band 7 (J=7-6 near 338.5 GHz) on June 29  
  > "The CH$_3$OH $K=3-2$ rotational band near 251.9 GHz (in ALMA receiver band 6) was observed on June 28 and the $J=7-6$ band near 338.5 GHz (in band 7) was observed on June 29." (2 ALMA CH$_3$OH observations)
- frequencies and spectral setup: single 976 kHz spectral window per band, 488 kHz resolution (0.58 km/s Band 6, 0.43 km/s Band 7)  
  > "in a single 976 kHz spectral window, using a spectral resolution of 488 kHz (0.58 km s$^{-1}$ in band 6 and 0.43 km s$^{-1}$ in band 7)" (2 ALMA CH$_3$OH observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 20-650 m, thirty 12-m antennae  
  > "Thirty 12-m antennae, with baseline lengths 20-650 m" (2 ALMA CH$_3$OH observations)
- angular resolution: 0.80''x0.43'' at 252 GHz; 0.71''x0.33'' at 338 GHz  
  > "resulted in an angular resolution of $0.80''\times0.43''$ at 252 GHz and $0.71''\times0.33''$ at 338 GHz" (2 ALMA CH$_3$OH observations)
- max recoverable scale: ≈7.4'' (≈10^4 km)  
  > "the largest angular scale detectable in our observations is $\approx7.4''$ (or $\approx10^4$ km)" (4.1 Spectra and maps)
- sensitivity: RMS per channel 1.8 mJy/beam (252 GHz), 3.0 mJy/beam (338 GHz)  
  > "the measured RMS noise levels per channel were 1.8 mJy bm$^{-1}$ and 3.0 mJy bm$^{-1}$" (2 ALMA CH$_3$OH observations)
- time on source: 46 min at 252 GHz; 38 min at 338 GHz  
  > "for a total of 46 min on-source at 252 GHz and 38 min on-source at 338 GHz" (2 ALMA CH$_3$OH observations)
- observing dates: 2014-06-28 19:07-20:05 and 2014-06-29 17:37-18:26  
  > "during 2014-06-28 19:07-20:05 and 2014-06-29 17:37-18:26" (2 ALMA CH$_3$OH observations)
- pi or archival as stated: _not stated_
- Line: CH3OH K=3-2 band (14 lines detected) (near 251.9 GHz)
- Line: CH3OH J=7-6 band (16 lines detected) (near 338.5 GHz)
- Other facility **Nançay radio telescope**: OH 18 cm lines giving Q(OH) and water production rate  
  > "The strengths of the 18 cm OH lines (at 1667 and 1665 MHz) in comet C/2012 K1 (PanSTARRS) were monitored using the Nançay radio telescope" (3 Nançay OH observations)
- External data: OH photolysis branching ratio 0.86 and CH3OH photodissociation rate 1e-5 s-1  
  > "adopting a branching ratio of 0.86 for the H$_2$O + $h\nu$ $\longrightarrow$ OH + H photolysis channel (cite: hue92)" (3 Nançay OH observations) [from (cite: hue92)]
- External data: Radiative transfer model for CH3OH level populations  
  > "Using the radiative transfer model of (cite: biv99; biv15), which computes the CH$_3$OH level populations" (5 Discussion) [from (cite: biv99; biv15)]

## Processing

### Calibration

- pipeline or manual: standard CASA routines  
  > "The data were flagged, calibrated and cleaned using standard CASA routines (cite: cor14)" (2 ALMA CH$_3$OH observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede  
  > "The data were flagged, calibrated and cleaned using standard CASA routines (cite: cor14), with Ganymede as the flux calibrator." (2 ALMA CH$_3$OH observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.05''  
  > "Imaging was performed using a grid size of $768\times768$ pixels, with $0.05''$ pixel scale." (2 ALMA CH$_3$OH observations)
- image size: 768x768 pixels  
  > "Imaging was performed using a grid size of $768\times768$ pixels" (2 ALMA CH$_3$OH observations)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied to cubes  
  > "The resulting data cubes were corrected for the response of the ALMA primary beam" (2 ALMA CH$_3$OH observations)
- array combination: _not stated_
- smoothing: spectra convolved with 3 km/s FWHM Gaussian kernel before fitting  
  > "each extracted spectrum was first convolved with a Gaussian broadening kernel of FWHM 3 km s$^{-1}$" (4.3 Line modeling)
- final beam: 0.80''x0.43'' (252 GHz), 0.71''x0.33'' (338 GHz)  
  > "angular resolution of $0.80''\times0.43''$ at 252 GHz and $0.71''\times0.33''$ at 338 GHz" (2 ALMA CH$_3$OH observations)
- final rms: _not stated_

### Inherited from earlier work

- Flagging, calibration and cleaning with standard CASA routines  
  > "The data were flagged, calibrated and cleaned using standard CASA routines (cite: cor14)" (2 ALMA CH$_3$OH observations) [from (cite: cor14)]
- Spectral line modeling algorithm (modified)  
  > "Using a modified version of the spectral line modeling algorithm previously applied to interstellar rotational emission lines by (cite: cor13)" (4.3 Line modeling) [from (cite: cor13)]
- OH observation procedure and analysis  
  > "The observational procedure and data analysis were described previously by (cite: cro02)" (3 Nançay OH observations) [from (cite: cro02)]

### Not stated but needed to reproduce (our reading)

- CASA version and tclean parameters (weighting, robust, deconvolver, threshold, masks)
- Bandpass and phase calibrator names and flux scale uncertainty
- Continuum subtraction (comet continuum undetected, so procedure unclear)
- Details of the modified line-fitting code, which is not released
- Comet ephemeris file and ALMA simulator settings for Haser model
- Details of the non-LTE model inputs (electron density, collision rates)

## Analysis recipe

1. **Extract spectra and moment maps**: Average over 1.5'' circular aperture at the emission peak; integrate line ranges for maps  
  > "These spectra were extracted by averaging the data over a circular aperture $1.5''$ in diameter, centered on the peak of the CH$_3$OH emission." (4.1 Spectra and maps)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Rotational diagram analysis**: Rotational diagram at column density peak; integration limits ±1.5 km/s  
  > "for our data, we used integration limits of $\pm1.5$ km s$^{-1}$ for all lines" (4.2 Rotational diagrams)
   - assumption: Equal A and E abundances  
  > "Thus, we assumed equal abundances of $A$ and $E$ CH$_3$OH in our analysis from here on." (4.2 Rotational diagrams)
   - fitting: Linear fit to the diagram; errors from gradient and intercept  
  > "Errors on $T_{rot}$ and $N$ were obtained from the errors on the gradient and intercept" (4.2 Rotational diagrams)
   - validation: Compared with line-modeling results  
  > "are in good agreement with those obtained using the rotational diagram method" (4.3 Line modeling)
3. **Spectral line fitting for Trot and N**: Nonlinear least-squares fit of Gaussian optical depth curves per pixel, parameters Trot, N, FWHM  
  > "fitting Gaussian optical depth curves to each emission line (as a function of frequency), parameterised by $T_{rot}$, $N$ and the line FWHM" (4.3 Line modeling)
   - parameter: Spectra smoothed by 3 km/s kernel; FWHM and Doppler shift held fixed  
  > "allowing these values to be held fixed during the fitting" (4.3 Line modeling)
   - fitting: chi2 minimization; 300 Monte Carlo noise realizations, 1-sigma from ±68% percentiles  
  > "300 synthetic, Gaussian, random noise spectra were generated" (4.3 Line modeling)
   - validation: Reduced chi2 1.0-1.3  
  > "with reduced $\chi^2$ values in the range 1.0-1.3" (4.3 Line modeling)
4. **Maps and radial profiles**: Pixel-by-pixel fit in 2''x2'' area; azimuthal averaging in 0.1'' annuli around column density peak; maps masked at >50% uncertainty  
  > "our data were binned into a series of $0.1''$-wide annuli" (4.5 Radial profiles)
   - fitting: same as step 3  
  > "These $\bar{S_{\nu}}(\rho)$ were subject to the same fitting procedure outlined in Section [4.3](#sec:modeling) to derive radial \[$T_{rot}$, $N$\] profiles" (Radial profiles)
   - validation: _not stated_
5. **Haser model of column density and production rates**: Haser outflow model run through CASA ALMA simulator and compared with N(rho)  
  > "the model column density maps were run through the ALMA simulator in CASA with array configuration, imaging and cleaning parameters matching those of our observationions" (4.5 Radial profiles)
   - software: CASA
   - assumption: Constant outflow velocity 0.5 km/s, photodissociation rate 1e-5 s-1  
  > "constant velocity of 0.5 km s$^{-1}$" (4.5 Radial profiles)
   - fitting: _not stated_
   - validation: Visual fit to observed N(rho)  
  > "provide an excellent fit to the observations on June 28, and a reasonably good fit on June 29" (4.5 Radial profiles)
6. **Non-LTE excitation modelling of Trot vs Tkin**: Radiative transfer model of Biver et al. with collisions with H2O and electrons and solar pumping; trial Tkin(r) profiles  
  > "A variety of different kinetic temperature profiles were tested in our radiative transfer model" (5 Discussion)
   - parameter: Q(H2O)=1e29 s-1, v=0.5 km/s, cross section 5e-14 cm-2  
  > "The H$_2$O production rate was taken to be $10^{29}$ s$^{-1}$ and outflow velocity 0.5 km s$^{-1}$" (5 Discussion)
   - fitting: Manual trial of Tkin(r) profiles  
  > "A variety of different kinetic temperature profiles were tested in our radiative transfer model, with the aim of reproducing the general behaviour of the observed $T_{rot}(r)$ profiles." (Discussion)
   - validation: _not stated_

## Software

- **CASA** : calibration, cleaning, ALMA simulator  
  > "calibrated and cleaned using standard CASA routines (cite: cor14)" (2 ALMA CH$_3$OH observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Trot at peak, June 28 (line modeling) | 62.3 | ±5.3 | K | 3 | $T_{rot}=62.3\pm5.3$ K, $N=(2.8\pm0.1)\times10^{14}$ cm$^{-2}$ on June 28 |
| Trot at peak, June 29 (line modeling) | 116 | ±18 | K | 3 | $T_{rot}=116\pm18$ K, $N=(2.7\pm0.4)\times10^{14}$ cm$^{-2}$ on June 29 |
| Trot at peak, June 28 (rotational diagram) | 63.0 | ±6.8 | K | 2 | $T_{rot}=63.0\pm6.8$ K, $N=(2.8\pm0.7)\times10^{14}$ cm$^{-2}$ on June 28 |
| Water production rate | 1.05e29 | ±0.20e29 | s-1 | 0 | we obtain a water production rate of $(1.05\pm0.20)\times10^{29}$ s$^{-1}$ |
| CH3OH production rate | 1.9e27 (June 28), 1.4e27 (June 29) | not stated | s-1 | 5 | CH$_3$OH production rates of $1.9\times10^{27}$ s$^{-1}$ on June 28 and $1.4\times10^{27}$ s$^{-1}$ on June 29 |
| CH3OH mixing ratio | 1.1-2.2 | not stated | % relative to H2O | 5 | with mixing ratios of 1.1-2.2% |
| Trot at rho=1000 km, June 29 | 42 | ±4 | K | 4 | decreased sharply from $116\pm18$ K to $42\pm4$ K between $\rho=0$-1000 km |
| Trot at rho=2500 km, June 28 | 22 | ±9 | K | 4 | followed by a relatively slow, steady decrease to $22\pm9$ K at $\rho=2500$ km |

## Qualitative findings

- CH3OH column density profile consistent with isotropic uniform outflow from nucleus; no extended source  
  > "no evidence is found for significant production of CH$_3$OH in the coma, either from icy grain sublimation or photochemistry" (6 Conclusion)

## Claim tuples

- H: Does coma Trot fall with distance beyond sub-thermal excitation? | E: Line fitting of azimuthal spectra plus non-LTE modelling | R: Observed Trot falls faster than for constant Tkin | F: Falling coma kinetic temperature required | **supported**
- H: Is CH3OH released directly from the nucleus? | E: Haser model fit to N(rho) | R: Good fits with isotropic outflow | F: Nuclear source, mixing ratio 1.1-2.2% | **supported**
- H: Do standard coma models explain the temperature drop? | E: Compare with DSMC and multi-fluid models | R: Observed drop less steep than models | F: Additional heating source needed | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Elliptical beam and filtering limit interpretation; June 29 Trot profile hard to fit  
  > "The elliptical shape of the telescope beam introduces some additional uncertainty into our radial temperature and column density profiles" (4.5 Radial profiles)
- Caveat (inferred, ours): Tkin profiles chosen by eye without uncertainties
- Caveat (inferred, ours): Line-of-sight averaging biases Trot
- Caveat (inferred, ours): Two epochs only, different bands, so temporal comparison confounded by band excitation differences
- Caveat (inferred, ours): Haser velocity assumed constant

## Reproducibility

- Data public (paper): ALMA project 2013.1.01061.S cited  
  > "It makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.01061.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Fitting code not released
- Missing: Non-LTE model details and CASA imaging parameters
- Data volume (inferred): ~20-50 GB
- Score (inferred): 3/5, Public data and clear fitting approach, but imaging parameters, versions and model code are missing.
- Rediscovery candidate: no, Imaging settings and the bespoke fitting and non-LTE codes are not specified well enough to redo the main results.

## Links

- Method: (cite: cor13) (Spectral line modeling algorithm)
- Method: (cite: boc94) (Rotational diagram method)
- Method: (cite: biv99; biv15) (Non-LTE excitation model)
- Companion: (cite: cor14) (Earlier ALMA comet observations and CASA procedure)
- Companion: (cite: cor16) (Preliminary analysis of the same data)

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
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
  "facts": 74,
  "stated": 44,
  "rate": 0.595
 },
 "evidence_ok": true
}
```
