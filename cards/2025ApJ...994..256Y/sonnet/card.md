# A Face-on Accretion Disk Geometry Revealed by Millimeter-wave Periodicity in Sgr A<SUP>∗</SUP>

`2025ApJ...994..256Y` | The Astrophysical Journal 2025 | first author: Yanagisawa, Kazuki | arXiv: 2511.02186 | DOI: 10.3847/1538-4357/ae1a80

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: milky_way_ism, agn_and_quasars
- Question: Does 230 GHz ALMA flux variability of Sgr A* show coherent periodicity, and what accretion-flow geometry (orbital radius, inclination) does it imply under a hotspot model?  
  > "Modeling with a Doppler-boosted hotspot scenario yields an orbital radius of $\sim$4 Schwarzschild radii and a disk inclination of 8$^\circ$ (or 172$^\circ$)" (abstract)
- Target **Sgr A***: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00111.S, 2013.1.00764.S, 2015.1.00311.S, 2015.1.00859.S, 2015.A.00021.S, 2016.1.00870.S, 2016.A.00037.T, 2017.1.00503.S, 2017.1.00820.S, 2018.1.01124.S, 2019.1.01559.S, 2021.1.00798.S
- bands: 230 GHz  
  > "(2) 230 GHz frequency band, (3) angular resolution below $1\ensuremath{''}$, and (4) integration time exceeding 1 hour." (Observations and Data Reduction)
- frequencies and spectral setup: 2021 data: four SpWs centered at 229.5, 231.2, 231.9, 232.9 GHz; 231.2 GHz excluded  
  > "The four spectral windows (SpWs) were centered at 229.5, 231.2, 231.9, and 232.9 GHz, each with a bandwidth of 2 GHz." (Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 77 light curves of 30-70 min, ~90 hours total  
  > "covering a total of 90 hours (Figure [1](#light)a)" (Variability analysis)
- observing dates: Projects executed July 2015 to May 2022; 2019.1.01559.S on 2021 July 20 and 22  
  > "we identified data from 12 projects executed between July 2015 and May 2022 that met our requirements." (Observations and Data Reduction)
- pi or archival as stated: _not stated_
- External data: Sgr A* black hole mass 4.297e6 Msun  
  > "black hole mass of $4.297\!\times\! 10^6\, M_{\ensuremath{\odot}}$ (cite: abuter2022mass)" (Modeling) [from (cite: abuter2022mass)]
- External data: Red-noise PSD spectral index alpha=2.20  
  > "spectral density index of $\alpha=2.20$ ($\mathrm{PSD}\propto f^{-2.20}$; (cite: weldon2023near))" (Period Analysis) [from (cite: weldon2023near)]

## Processing

### Calibration

- pipeline or manual: Standard scriptForPI.py, then iterative phase self-calibration  
  > "The raw ALMA visibility data were calibrated using the standard scriptForPI.py provided by the observatory" (Observations and Data Reduction)
- casa version: 4.2.2, 4.4.0, 4.5.3, 4.6.0, 4.7.0, 4.7.2, 5.1.1, 5.4.0, 5.7.2, 6.2.1-7  
  > "CASA (version 4.2.2, 4.4.0 4.5.3 4.6.0, 4.7.0, 4.7.2, 5.1.1, 5.4.0, 5.7.2, 6.2.1-7)" (Software)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Iterative phase self-cal with gaincal/applycal; solint inf then int  
  > "We started with a solution interval of `inf` (per scan), and subsequently shortened it to int (per integration), improving the coherence of the data." (Observations and Data Reduction)

### Imaging

- task: tclean, snapshot images; flux via imfit  
  > "The flux density and its associated uncertainty were obtained by performing fits to the snapshot images with the CASA task `imfit`." (Observations and Data Reduction)
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
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Iterative phase self-calibration method  
  > "we performed iterative phase self-calibration on Sgr A\*, following the method described in I20+." (Observations and Data Reduction) [from I20+ (Iwata et al. 2020; cite: iwata2020time)]

### Not stated but needed to reproduce (our reading)

- tclean parameters (weighting, robust, cell, image size, niter, threshold, masks)
- snapshot integration length and binning details
- which of the 12 projects/epochs yielded each light curve and the list of 77
- Self-calibration number of iterations and reference model
- Priors' widths and MCMC sampler/software, chains
- Reference flux calibrator and flux scale handling
- Linear-trend removal and imfit details

## Analysis recipe

1. **Select and calibrate archival data**: Archive search with criteria; scriptForPI calibration; phase self-cal  
  > "The selection criteria required (1) focusing on Sgr A$^*$’s field of view, (2) 230 GHz frequency band, (3) angular resolution below $1\ensuremath{''}$" (Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Build light curves**: tclean snapshot images, imfit flux densities, ~1 min bins  
  > "each with a duration of $30\mbox{--}70$ minutes and the data are binned to $\sim$1 min" (Variability analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Periodicity search**: GLS periodogram after linear detrending; FAP from 1e5 red-noise simulations; threshold FAP<2.9e-7 (5 sigma)  
  > "We considered a signal significant if $\mathrm{FAP}\!<\!2.9\!\times\!10^{-7}$, corresponding to $>\!5\sigma$ significance for Gaussian noise." (Period Analysis)
   - parameter: PSD index 2.20, 1e5 realizations  
  > "estimated from $10^{5}$ Monte Carlo realizations of red-noise light curves with a spectral density index of $\alpha=2.20$" (Period Analysis)
   - fitting: _not stated_
   - validation: Red-noise Monte Carlo FAP  
  > "The false-alarm probability (FAP) of each periodogram peak was estimated from $10^{5}$ Monte Carlo realizations of red-noise light curves with a spectral density index of $\alpha=2.20$" (Variability analysis, Period Analysis)
4. **Fit Doppler-boosted hotspot model**: Least-squares fit of F(t)=A/(1-beta sin i cos(2pi t/T-phi))^3+B+Ct, then Kepler's third law for r, v_rot and i for a*=0, +1, -1  
  > "A least-squares fit of Eq.([\[eq:doppler_1\]](#eq:doppler_1)) to the observed sinusoidal light curve yielded well-constrained best-fit values" (Modeling)
   - assumption: Circular orbit, BH mass 4.297e6 Msun, spin a* from -1 to 1  
  > "we adopted a circular-orbit hotspot plus accretion disk model." (Modeling)
   - fitting: Least squares; chi2 contours in T and beta sin i  
  > "A least-squares fit of Eq.([\[eq:doppler_1\]](#eq:doppler_1)) to the observed sinusoidal light curve yielded well-constrained best-fit values for the parameters" (Modeling)
   - validation: _not stated_
5. **MCMC joint fit**: MCMC on combined Doppler+Kepler form, with r and a* free; uniform priors on a* and phi, Gaussian priors on others  
  > "a_* and phi were assigned uniform priors, while the remaining parameters used Gaussian priors centered on the best-fit values from our initial analysis" (Modeling)
   - fitting: MCMC; spin posterior flat  
  > "While the posterior distribution of the spin parameter remains flat, the other parameters are consistent with the results obtained from the analysis using" (Modeling)
   - validation: _not stated_
6. **Assess GR systematics**: GRRT light curves with CARTOON for a*=0, 0.998 and hotspot radius 0.5, 1.0 rg compared to Doppler model  
  > "the simulated light curves differed from those predicted by the Doppler-beaming model (Eq.[\[eq:doppler_1\]](#eq:doppler_1)) by less than 2% of this amplitude." (Impact of General Relativistic Effects)
   - software: CARTOON
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.2 to 6.2.1-7: calibration, self-cal, tclean, imfit  
  > "We applied the self-calibration and CLEAN algorithm to these data using the Common Astronomy Software Applications (CASA) package" (Observations and Data Reduction)
- **CARTOON** : GRRT light curves  
  > "we performed general relativistic radiative transfer (GRRT) calculations using the code `CARTOON`" (Impact of General Relativistic Effects)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Orbital period T | 52.28 | +1.46/-1.54 | min | 4 | $T\! =\! 52.28^{+1.46}_{-1.54}\,\mbox{min}$ |
| beta_rot sin i | 4.7e-2 | 0.5e-2 | dimensionless | 4 | $\beta_{\rm rot}\sin{i}\! =\!(4.7\!\pm\!0.5)\!\times\!10^{-2}$ |
| Orbital radius (a*=0) | 4.1 | 0.1 | r_s | 4 | an orbital radius of $r\! =\! (4.1\!\pm\! 0.1)\, r_{\text{s}}$ |
| Inclination (a*=0) | 7.7 (or 172.3) | 0.8 | deg | 4 | $i\! =\! 7.7\ensuremath{^\circ}\!\pm\! 0.8\ensuremath{^\circ}$ or $172.3\ensuremath{^\circ}\!\pm\! 0.8\ensuremath{^\circ}$ |
| Hotspot velocity (a*=0) | 0.348 | 0.003 | c | 4 | $0$ / $4.1\pm0.1$ / $0.348\pm0.003$ |
| Modulation amplitude | ~14% | not stated | percent | 2 | The amplitude of the observed sinusoidal variation is approximately 14% |
| FAP of main peak | <1.8e-7 | not stated | dimensionless | 3 | $\mathrm{FAP}\!<\!1.8\times10^{-7}$ |

## Qualitative findings

- Only 3 of 77 light curves show significant periodicity; two were already reported by Iwata et al. 2020  
  > "Periodic variability was detected in three epochs, two of which occurred in 2017 and were already reported by I20+." (Period Analysis)

## Claim tuples

- H: A coherent periodic millimeter modulation exists in Sgr A* | E: GLS periodogram with red-noise FAP on 77 light curves | R: ~52 min sinusoid on 2021 July 22, FAP<1.8e-7 | F: Rare transient coherent periodicity detected at >5 sigma | **supported**
- H: The modulation traces an orbiting hotspot in a near face-on disk | E: Doppler-boosted hotspot fit plus Kepler's law | R: r~4 r_s, i~7.7 deg (or 172 deg) | F: Consistent with GRAVITY and EHT inclinations | **supported**
- H: GR effects and hotspot size do not bias the result | E: GRRT with CARTOON | R: Light curves differ by <2% of amplitude | F: Systematics small | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Model neglects GR effects and finite hotspot size in the fit; uncertainties are statistical only; hotspot temporal changes not modelled; spin unconstrained  
  > "the reported parameter uncertainties represent only statistical errors." (Modeling)
- Caveat (inferred, ours): Single epoch detection; post hoc selection among 77 light curves (look-elsewhere effect) not accounted for in the significance
- Caveat (inferred, ours): Sinusoid could arise from red noise or other non-hotspot variability; inclination degeneracy with a single beaming model
- Caveat (inferred, ours): Uncertainties are formal and exclude hotspot model systematics

## Reproducibility

- Data public (paper): Archival ALMA data  
  > "We analyzed 77 epochs of Atacama Large Millimeter/submillimeter Array (ALMA) archival data" (abstract)
- Products in archive: _not stated_
- Missing: Imaging parameters and light-curve construction details
- Missing: Exact list of epochs/data selection
- Missing: MCMC sampler and prior widths
- Data volume (inferred): Large: 12 projects of long 230 GHz Sgr A* tracks, likely hundreds of GB to ~1 TB raw
- Score (inferred): 3/5, Public data and a simple model, but imaging/self-cal and MCMC details are omitted.
- Rediscovery candidate: no, Heavy multi-project processing with underspecified imaging steps, although the 2021 epoch alone is public and numeric.

## Links

- Method: Zechmeister & Kürster 2009 (cite: zechmeister2009generalised) (Generalized Lomb-Scargle periodogram)
- Method: Takahashi et al. 2022 (cite: takahashi20223d) (CARTOON GRRT code)
- Companion: Iwata et al. 2020 (cite: iwata2020time) (Earlier ALMA periodicity in Sgr A*, source of self-cal method)
- Related: GRAVITY
- Related: EHT

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 12,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 28,
  "rate": 0.4
 },
 "evidence_ok": true
}
```
