# Evidence for Multiple Orbiting Hotspots in the 340 GHz Variability of Sgr A*

`2026ApJ..1003L..17Y` | The Astrophysical Journal Letters 2026 | first author: Yanagisawa, Kazuki | arXiv: 2605.11698 | DOI: 10.3847/2041-8213/ae6862

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: milky_way_ism, agn_and_quasars
- Question: Does the 340 GHz light curve of Sgr A* show periodic variability from orbiting hotspots, and can multiple decaying hotspots explain it?  
  > "We find that the variability is well described by a model involving multiple orbiting hotspots with decaying emission." (abstract)
- Target **Sgr A***: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.01080.S, 2016.1.00517.S, 2016.1.01430.S, 2018.A.00050.T, 2019.1.01559.S
- bands: Band 7 (340 GHz)  
  > "(2) frequency band 7, and (3) integration time exceeding 1 hour." (Observations and Data Reduction)
- frequencies and spectral setup: four spectral windows analyzed; detrended light curve at 337.5 GHz  
  > "These features are consistently observed in all four analyzed spectral windows (SpWs)." (Variability analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 11 epochs, 35 to 150 min each, total about 14 hours  
  > "each with observation durations ranging from 35 to 150 minutes" (Variability analysis); "The total observing time amounts to about 14 hours." (Variability analysis)
- observing dates: Main epoch 2016 August 31; projects 2016-2021  
  > "we focus on the light curve obtained on 2016 August 31 during ALMA Cycle 3" (Variability analysis)
- pi or archival as stated: _not stated_
- External data: Magnetic field B = 44 G at orbital radius ~3.1 r_s used for the synchrotron cooling estimate  
  > "adopting a magnetic field strength of $B = 44\,\mathrm{G}$ at an orbital radius of $\sim 3.1\,r_{\rm s}$ (cite: von2025first)" (Discussion) [from (cite: von2025first)]
- External data: Adiabatic expansion timescale ~1 hr for B = 50 G  
  > "reported that, for a magnetic field strength of $50\,\mathrm{G}$, the adiabatic expansion timescale of a hotspot is on the order of $\sim1\,\mathrm{hr}$" (Discussion) [from (cite: michail2024multiwavelength)]

## Processing

### Calibration

- pipeline or manual: Observatory ScriptForPI.py calibration, then iterative phase self-calibration  
  > "standard calibration scripts provided by the observatory (ScriptForPI.py) were applied to perform flux, phase, and bandpass calibration." (Observations and Data Reduction)
- casa version: 4.7, 4.7.2, 5.4.0-68, 5.4.0-70, 6.2.1.7  
  > "CASA (version 4.7, 4.7.2, 5.4.0-68, 5.4.0-70, 6.2.1.7)" (Software)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: iterative phase self-calibration on Sgr A*, following I20+ and Y25+  
  > "we performed iterative phase self-calibration on Sgr A\*, following the procedures described in I20+ and Y25+." (Observations and Data Reduction)

### Imaging

- task: _not stated_
- deconvolver: CLEAN (Högbom)  
  > "We applied self-calibration and the CLEAN algorithm (cite: hogbom1974synthesis) to these data" (Observations and Data Reduction)
- weighting robust: _not stated_
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Iterative phase self-calibration procedure  
  > "following the procedures described in I20+ and Y25+." (Observations and Data Reduction) [from I20+ (cite: iwata2020time); Y25+ (cite: yanagisawa2025face)]
- Sinusoidal approximation of hotspot Doppler beaming for face-on orbits  
  > "this assumption is motivated by the Doppler beaming model proposed by Y25+" (Multiple Hotspot Model) [from Y25+ (cite: yanagisawa2025face)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals and number of iterations
- Imaging parameters (weighting, cell, image size) and how the flux density is measured per time bin
- Which SpWs and which of the 11 epochs belong to which project
- MCMC sampler, priors and chain settings
- GPR implementation and noise amplitude hyperparameters
- Source of the spectral index variation (alpha decreases by ~0.4); method not given
- Flux calibrator and absolute flux scale uncertainty

## Analysis recipe

1. **Build light curves**: Calibrate, self-calibrate and CLEAN archival Band 7 data; light curves binned to ~1 min for 11 epochs  
  > "All data were binned with a time resolution of $\sim$ 1 minute." (Variability analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Detrend long-timescale variation**: Gaussian Process Regression with RBF kernel, correlation length 300 min, measurement errors as white noise  
  > "The correlation length in RBF kernel was fixed to 300 min" (Variability analysis)
   - fitting: _not stated_
   - validation: Matérn kernel gives qualitatively consistent results; detrending other epochs introduces no artificial periodicity  
  > "We verified that applying the same detrending procedure to other epochs does not introduce artificial periodic features." (Variability analysis)
3. **Periodicity search and significance**: Generalized Lomb-Scargle periodogram; FAP from 10^5 simulated light curves with red noise (PSD ∝ f^-2) plus white noise  
  > "estimated using $10^5$ simulated light curves that incorporate both red noise, assuming a power spectral density of PSD$\propto f^{-2}$" (Variability analysis)
   - parameter: 3 sigma criterion, FAP < 1.35e-3  
  > "We adopt a false alarm probability (FAP) of $< 1.35 \times 10^{-3}$" (Variability analysis)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit multiple decaying hotspot model**: Two sinusoids with Gaussian decaying amplitudes and sigmoid emergence of 2nd hotspot, fitted by MCMC  
  > "was fitted to the light curve shown in Fig. [1](#01080) (bottom) using the Markov Chain Monte Carlo (MCMC) method." (Multiple Hotspot Model)
   - assumption: Gaussian decay form is phenomenological and not unique  
  > "We note that this choice is not unique, and the inferred parameters may depend on the assumed functional form." (Multiple Hotspot Model)
   - fitting: MCMC; priors and likelihood not stated  
  > "was fitted to the light curve shown in Fig. [1](#01080) (bottom) using the Markov Chain Monte Carlo (MCMC) method." (Multiple Hotspot Model)
   - validation: _not stated_
5. **Estimate synchrotron cooling timescale**: t_syn = 6π m_e/(σ_T B² γ) with γ from nu_syn = 337.5 GHz  
  > "Assuming $\nu_{\mathrm{syn}} = 337.5\,\mathrm{GHz}$ and $\sin\theta = 1$" (Discussion)
   - assumption: B = 44 G, sinθ = 1  
  > "adopting a magnetic field strength of $B = 44\,\mathrm{G}$" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7, 4.7.2, 5.4.0-68, 5.4.0-70, 6.2.1.7: calibration, self-calibration and CLEAN imaging  
  > "using the Common Astronomy Software Applications (CASA) package" (Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| T1 (1st hotspot period) | 50.4 | ±0.3 | min | 4 | $T_1=50.4\pm0.3\,\mathrm{min}$ and $T_2=30.6\pm0.3\,\mathrm{min}$ |
| T2 (2nd hotspot period) | 30.6 | ±0.3 | min | 4 | $T_1=50.4\pm0.3\,\mathrm{min}$ and $T_2=30.6\pm0.3\,\mathrm{min}$ |
| sigma1 decay timescale | 70.3 | ±2.5 | min | 4 | $\sigma_1=70.3\pm2.5\,\mathrm{min}$ |
| sigma2 decay timescale | 37.7 | +1.6/-1.5 | min | 4 | $37.7^{+1.6}_{-1.5}\,\mathrm{min}$ |
| GLS significance of ~52 and ~34 min peaks, white noise only | ~25.4 and ~12.7 | not stated | sigma | 3 | peaks at $\sim$52 min and $\sim$34 min are obtained with significances of $\sim25.4\,\sigma$ and $\sim12.7\,\sigma$ |
| GLS significance with red+white noise | ~2.9 and ~0.9 | not stated | sigma | 3 | these are reduced to $\sim2.9\,\sigma$ and $\sim0.9\,\sigma$ |
| t_syn | ~150 | not stated | min | 5 | we obtain a synchrotron cooling timescale of $t_{\mathrm{syn}} \sim 150\,\mathrm{min}$ |
| 2nd hotspot emergence time t0 | 50.2 | ±0.3 | min | 4 | $50.2\pm0.3$ |

## Qualitative findings

- Only one of 11 light-curve segments shows variability consistent with orbital motion  
  > "only one out of 11 light-curve segments shows variability consistent with orbital motion" (Discussion)

## Claim tuples

- H: Periodic peaks in the 340 GHz light curve are statistically significant | E: GLS periodogram with FAP from red+white noise simulations | R: Significance falls from 25.4/12.7 sigma to 2.9/0.9 sigma | F: Not significant periodic detections | **supported**
- H: Multiple decaying orbiting hotspots describe the light curve | E: MCMC fit of two decaying sinusoids | R: T1=50.4, T2=30.6 min; sigma1=70.3, sigma2=37.7 min | F: Variability is well described by the model | **partially**
- H: Synchrotron cooling explains amplitude decay | E: Compare t_syn with decay timescales and spectral index change | R: t_syn ~150 min exceeds decay times; alpha decreases ~0.4 | F: Synchrotron cooling alone cannot explain decay | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Matérn kernel tested for detrending; results qualitatively consistent  
  > "we also tested a Matérn kernel with similar characteristic length scales." (Variability analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Fit decay timescales are approximate because of limited light-curve duration  
  > "these values should be regarded as approximate constraints" (Multiple Hotspot Model)
- Caveat (inferred, ours): Periodicities are below 3 sigma with red noise, so the hotspot model is weakly supported
- Caveat (inferred, ours): Single epoch used to fit a many-parameter model; no model comparison against red-noise-only or single-hotspot
- Caveat (inferred, ours): Gaussian decay and sinusoid forms are ad hoc
- Caveat (inferred, ours): GPR correlation length fixed at 300 min may affect detrending of 150 min data

## Reproducibility

- Data public (paper): Archival ALMA data  
  > "We analyzed 11 epochs of archival Atacama Large Millimeter/submillimeter Array (ALMA) data" (abstract)
- Products in archive: _not stated_
- Missing: Self-calibration and imaging parameters
- Missing: MCMC priors, likelihood and sampler
- Missing: Details of the I20+ and Y25+ procedures
- Missing: Spectral index measurement method
- Data volume (inferred): ~100-500 GB for five projects
- Score (inferred): 4/5, Public data and a clear model, but processing and MCMC details are inherited or omitted.
- Rediscovery candidate: no, Self-calibration and photometry details are inherited from other papers, and MCMC settings are missing.

## Links

- Method: (cite: iwata2020time) (self-calibration and light-curve procedures (I20+))
- Method: (cite: yanagisawa2025face) (self-calibration and Doppler beaming hotspot model (Y25+))
- Method: (cite: zechmeister2009generalised) (GLS periodogram)
- Companion: (cite: yanagisawa2025face) (230 GHz ~52 min periodic variability, face-on hotspot)

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 28,
  "rate": 0.406
 },
 "evidence_ok": true
}
```
