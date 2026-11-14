# ALMA Observations of the Terahertz Spectrum of Sagittarius A*

`2019ApJ...881L...2B` | The Astrophysical Journal Letters 2019 | first author: Bower, Geoffrey C. | arXiv: 1907.08319 | DOI: 10.3847/2041-8213/ab3397

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, milky_way_ism
- Question: What is the submm/THz spectrum of Sgr A* and what do the flat spectrum and one-zone thermal synchrotron model imply for the emitting plasma and its optical depth?  
  > "We model the submm and far infrared spectrum with a one zone synchrotron model of thermal electrons." (abstract)
- Target **Sagittarius A***: coordinates _not stated_; z/distance D = 8.2 kpc  
  > "We use a black hole mass of $M = 4.1\times10^6 M_{\odot}$ and a distance of $D = 8.2$ kpc (cite: 2018A&A...615L..15G)." (Discussion and Conclusions); distance from Gravity Collaboration 2018b (cite: 2018A&A...615L..15G)  
  > "We use a black hole mass of $M = 4.1\times10^6 M_{\odot}$ and a distance of $D = 8.2$ kpc (cite: 2018A&A...615L..15G)." (Discussion and Conclusions)

## Data provenance

- ALMA projects: 2016.1.00901.S
- bands: Band 6 (233 GHz), Band 9 (678 GHz), Band 10 (868 GHz)  
  > "On 22 March 2017, observations were obtained in Bands 6 and 9 (233 and 678 GHz, respectively) within 45 minutes of each other." (Observations, Data Reduction, and Results)
- frequencies and spectral setup: four SPWs per band, each 2 GHz bandwidth, 128 channels; parallel hands only  
  > "Observations in each band were obtained in standard correlator configurations with four spectral windows (SPWs) each with 2 GHz bandwidth and 128 channels." (Observations, Data Reduction, and Results)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: compact configuration, maximum baseline 2.4 km  
  > "The array was in a compact configuration with maximum baseline of 2.4 km." (Observations, Data Reduction, and Results)
- angular resolution: ~1.5 arcsec Band 6, ~0.5 arcsec Band 9, ~0.4 arcsec Band 10 (natural weighting)  
  > "This produced a naturally-weighted synthesized beam of $\sim 1.5$ arcsec in Band 6, $\sim 0.5$ arcsec in Band 9, and $\sim 0.4$ arcsec in Band 10." (Observations, Data Reduction, and Results)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 2 minutes on Sgr A* in each band  
  > "For all three bands, integrations on Sgr A\* were 2 minutes in each band; calibrator integrations were of comparable duration." (Observations, Data Reduction, and Results)
- observing dates: 18 March 2017 (Band 10); 22 March 2017 (Bands 6 and 9)  
  > "On 18 March 2017, observations were obtained in Band 10 (868 GHz)." (Observations, Data Reduction, and Results)
- pi or archival as stated: _not stated_
- Other facility **Herschel SPIRE/PACS**: Variable flux detections used to set lower/upper limits on median flux density in the fit  
  > "We further follow (cite: stone2016) and take the detected variable flux densities as lower limits to the median value." (Discussion and Conclusions)
- External data: Herschel SPIRE/PACS variable flux densities used as limits  
  > "Following (cite: vonfellenberg2018), we further derive upper limits on the median flux density by assuming a minimum variability amplitude of $25\%$ during the observations" (Discussion and Conclusions) [from (cite: stone2016; vonfellenberg2018)]
- External data: Black hole mass 4.1e6 Msun and distance 8.2 kpc  
  > "We use a black hole mass of $M = 4.1\times10^6 M_{\odot}$ and a distance of $D = 8.2$ kpc (cite: 2018A&A...615L..15G)." (Discussion and Conclusions) [from (cite: 2018A&A...615L..15G)]
- External data: X-ray upper limit L_X < 2e33 erg/s  
  > "Imposing an upper limit $L_X < 2\times10^{33} \,\rm erg \,\rm s^{-1}$ (cite: baganoff2003)" (Discussion and Conclusions) [from (cite: baganoff2003)]

## Processing

### Calibration

- pipeline or manual: CASA, standard procedures for flux, gain, bandpass, plus phase self-calibration on short timescales  
  > "Data reduction was performed using CASA, following standard procedures for flux, gain, and bandpass calibration, including phase self-calibration on short time scales for Sgr A\* and each calibrator." (Observations, Data Reduction, and Results)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1924-2914, observed in Bands 3 and 7 and extrapolated  
  > "Flux calibration is based on estimates of the flux density of the ALMA gain calibrator J1924-2914" (Observations, Data Reduction, and Results)
- flux scale uncertainty: systematic errors in Bands 9 and 10 <~20%  
  > "We estimate that systematic flux density errors in Bands 9 and 10 are $\stackrel{\scriptstyle <}{\scriptstyle \sim}20\%$." (Observations, Data Reduction, and Results)
- self calibration: phase self-calibration on short time scales for Sgr A* and each calibrator  
  > "including phase self-calibration on short time scales for Sgr A\* and each calibrator." (Observations, Data Reduction, and Results)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "This produced a naturally-weighted synthesized beam" (Observations, Data Reduction, and Results)
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

- One-zone synchrotron fitting approach  
  > "Following (cite: vonfellenberg2018) we estimate the physical properties of the emission region by fitting a one zone synchrotron emission model" (Discussion and Conclusions) [from (cite: vonfellenberg2018)]
- Synchrotron emissivity/absorption fitting functions  
  > "using the fitting function expressions from Appendix A of (cite: dexter2016)" (Discussion and Conclusions) [from (cite: dexter2016)]
- SSC spectrum estimation method  
  > "We use the method described in (cite: chiaberge1999) and (cite: drappeau2013) to estimate the SSC spectrum." (Discussion and Conclusions) [from (cite: chiaberge1999; drappeau2013)]

### Not stated but needed to reproduce (our reading)

- Exact CASA version and whether the pipeline or manual scripts were used
- Calibrator flux model details and extrapolation spectral index for J1924-2914
- Antenna flagging and spectral-window handling
- emcee settings (walkers, steps, burn-in)
- One-zone code is from von Fellenberg and not released
- Exact prior ranges for n and Te
- Uv-fit procedure details

## Analysis recipe

1. **Measure flux densities**: Point source model fit in the visibility domain per source per SPW; band mean with errors from scatter  
  > "Flux densities were fit for each source in each spectral window using a point source model in the visibility domain." (Observations, Data Reduction, and Results)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared J1924-2914 and other calibrators with archival ALMA measurements; differences <~10% in Band 6  
  > "Comparisons to archival ALMA Band 6 measurements for all calibrators show excellent consistency with differences to nearest measurements $\stackrel{\scriptstyle <}{\scriptstyle \sim}10\%$." (Observations, Data Reduction, and Results)
2. **Compute spectral index**: Power-law S ∝ ν^α for sources with all three bands  
  > "We also compute the spectral index $\alpha$ (using $S \propto \nu^{\alpha}$) for sources with measurements in all three bands." (Observations, Data Reduction, and Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit one-zone thermal synchrotron model**: Uniform sphere of angular diameter 40 uas with n, Te, B; fit to ALMA data plus Herschel ranges; ν_p, L_bol, n, Te, B derived  
  > "We parameterize the emission region as a sphere of constant particle density $n$, electron temperature $T_e$, and magnetic field strength $B$." (Discussion and Conclusions)
   - software: emcee
   - parameter: Te >= Tb, 1e-3 < beta < 1e3; 20% uncertainty on 868 GHz  
  > "Parameter bounds are $T_e \ge T_b$ the brightness temperature, necessary for obtaining a one zone solution, and $10^{-3} < \beta < 10^{3}$." (Discussion and Conclusions)
   - assumption: Relativistic effects and radiative cooling neglected; thermal electrons; constant ion temperature proportional to virial  
  > "We neglect all relativistic effects in the spatial and velocity distribution of the material and on the photon trajectories." (Discussion and Conclusions)
   - fitting: emcee default sampler with logarithmic priors on n, Te and plasma beta  
  > "We use the default sampler with logarithmic priors $n$, $T_e$, and plasma $\beta = p_g/p_B \propto n/B^2$" (Discussion and Conclusions)
   - validation: Repeated without Herschel data  
  > "We find similar results with somewhat larger ranges when leaving out the Herschel data" (Discussion and Conclusions)
4. **Apply X-ray SSC constraint**: Estimate SSC 2-10 keV luminosity and require L_X<2e33 erg/s  
  > "This constraint removes about half of the models." (Discussion and Conclusions)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data reduction  
  > "Data reduction was performed using CASA" (Observations, Data Reduction, and Results)
- **emcee** : MCMC sampling of one-zone model  
  > "We sample the model parameter space using the `emcee` Markov Chain Monte Carlo code (cite: emcee)." (Discussion and Conclusions)
- **MATLAB** : Listed in software; use not stated  
  > "CASA, MATLAB" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spectral index Sgr A* (all bands) | -0.31 | 0.02 | dimensionless | 2 | / Sgr A\* / $2.886 \pm 0.043$ / $2.183 \pm 0.026$ / $1.864 \pm 0.067$ / $-0.31 \pm  0.02$ / |
| Spectral index Sgr A* (233 and 678 GHz) | -0.26 | 0.02 | dimensionless | 2 | Considering only the simultaneous 233 and 678 GHz Sgr A\* data, $\alpha = -0.26 \pm 0.02$. |
| Sgr A* flux density 233 GHz | 2.886 | 0.043 | mJy | 1 | / Sgr A\* / $2.886 \pm 0.043$ / $2.183 \pm 0.026$ / $1.864 \pm 0.067$ / $-0.31 \pm  0.02$ / |
| SED peak frequency | (1-2)e12 | 68% interval | Hz | 3 | The peak of the SED in $\nu L_\nu$ is well constrained to be at $\nu_p = (1-2) \times 10^{12}$ Hz |
| Bolometric luminosity of submm bump | (4-6)e35 | not stated | erg/s | 3 | The bolometric luminosity of the submm bump is found to be $L_{\rm bol} = (4-6) \times
10^{35}\,\ensuremath{{\rm erg\,s}}^{-1}$. |
| Electron density, temperature, field | n=2-5e6 cm^-3, Te=1-3e11 K, B=10-50 G | not stated | cm^-3, K, G | 3 | $n = 2-5 \times 10^6 \hspace{2pt} \rm cm^{-3}$, $T_e =
  1-3 \times 10^{11}$ K, $B = 10-50$ G. |
| Parameters with X-ray constraint | n=2-3e6, Te=1-2e11 K, B=20-50 G, beta ~1-10 | not stated | cm^-3, K, G | 4 | $n = 2-3 \times 10^6 \hspace{2pt} \rm cm^{-3}$, $T_e =
  1-2 \times 10^{11}$ K, $B = 20-50$ G. |

## Qualitative findings

- Emission is mostly optically thin at 233 GHz (~90% of models tau<1)  
  > "Approximately $90\%$ of the sampled models have $\tau_\nu < 1$ and all have $\tau_\nu < 2$ at that frequency" (Discussion and Conclusions)

## Claim tuples

- H: Sgr A* has a flat spectrum across 233-868 GHz | E: ALMA Band 6, 9, 10 flux measurements | R: alpha = -0.31 +/- 0.02 | F: Flat submm spectrum | **supported**
- H: One-zone thermal synchrotron model constrains plasma properties | E: emcee fit to ALMA plus Herschel limits | R: n, Te, B ranges given | F: High, efficiently heated electron temperature | **supported**
- H: Emission region is transparent at 233 GHz | E: Optical depth of sampled models | R: ~90% have tau<1 | F: EHT should see a transparent region | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Power-law electron distribution gives similar parameters but cannot fit both submm peak and NIR median flux  
  > "Using a power law shape yields similar parameter estimates and spectral shape" (Discussion and Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): 868 GHz measured four days from the others, longer than variability coherence time  
  > "the four-day separation with the 868 GHz measurements is significantly longer than the variability coherence time" (Discussion and Conclusions)
- Caveat (inferred, ours): Single-epoch snapshots of a variable source
- Caveat (inferred, ours): One-zone model neglects relativistic effects
- Caveat (inferred, ours): Herschel limits are derived quantities with assumptions
- Caveat (inferred, ours): Band 9/10 flux scale extrapolated, ~20% systematics

## Reproducibility

- Data public (paper): ALMA project 2016.1.00901.S acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00901.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: One-zone code (provided privately by von Fellenberg)
- Missing: CASA version and calibration scripts
- Missing: MCMC settings
- Data volume (inferred): ~ few GB
- Score (inferred): 5/5, Public data and simple flux measurement, but modeling code and settings not given.
- Rediscovery candidate: no, Flux measurements are reproducible but the model code is not available and settings missing.

## Links

- Method: (cite: vonfellenberg2018) (one-zone fitting approach)
- Method: (cite: dexter2016) (synchrotron fitting functions)
- Companion: (cite: bower2015) (earlier ALMA Sgr A* SED)
- Related: Event Horizon Telescope

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
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
  "facts": 70,
  "stated": 37,
  "rate": 0.529
 },
 "evidence_ok": true
}
```
