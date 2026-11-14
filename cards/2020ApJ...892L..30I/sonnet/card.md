# Time Variations in the Flux Density of Sgr A* at 230 GHz Detected with ALMA

`2020ApJ...892L..30I` | The Astrophysical Journal Letters 2020 | first author: Iwata, Yuhei | arXiv: 2003.08601 | DOI: 10.3847/2041-8213/ab800d

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, agn_and_quasars
- Question: Does Sgr A* show short-timescale (tens of minutes) variability at 230 GHz, and are there time lags between frequencies or a flux dependence of the spectral index?  
  > "The main objective of this study is confirming the short-timescale variability in the light curves." (Introduction)
- Target **Sgr A***: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00503.S
- bands: Band 6  
  > "The Band 6 observations of the Sgr A region were carried out as a part of the ALMA Cycle 5" (Observations and Data Reduction)
- frequencies and spectral setup: 4 SPWs at 217.5, 219.5, 234.0, 231.9 GHz; 2.0 GHz bandwidth, 15.625 MHz resolution  
  > "The central frequencies of the four spectral windows (SPWs) were 217.5, 219.5, 234.0, and 231.9 GHz." (Observations and Data Reduction); "The bandwidth and frequency resolution of the SPWs were 2.0 GHz and 15.625 MHz, respectively." (Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.04" x 0.02" (natural weighting)  
  > "The synthesized beam sizes with natural weighting were $\sim 0.04\ensuremath{''} \times 0.02\ensuremath{''}$." (Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: ten days, 2017 Oct 5 to Oct 20  
  > "over ten days between 2017 October 5 and 2017 October 20" (Observations and Data Reduction)
- pi or archival as stated: PI: M. Tsuboi; same data as Tsuboi et al. 2019  
  > "Detailed description of the analysis and the results of the IRS 13E complex from the same data have already been published by (cite: Tsuboi19)." (Observations and Data Reduction)
- External data: Time lag of 30 min between 43 and 22 GHz used to predict expected lag  
  > "Using the time lag $\Delta T_{\rm 2-1}$ between $\nu_2 = 43$ GHz and $\nu_1 = 22$ GHz of 30 min (cite: Yusef-Zadeh06; Yusef-Zadeh08)" (Discussion) [from (cite: Yusef-Zadeh06; Yusef-Zadeh08)]

## Processing

### Calibration

- pipeline or manual: standard flux, gain, bandpass calibration, then iterative phase self-calibration  
  > "After performing the standard procedures for flux, gain, and bandpass calibrations, we applied the phase self-calibration method iteratively." (Observations and Data Reduction)
- casa version: CASA 5.5.0  
  > "CASA (version 5.5.0)." (Software)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1924-2914 (flux and bandpass); phase: J1744-3116, J1752-2956  
  > "J1924–2914 was observed as a flux and bandpass calibrator, while phase calibration was performed with J1744–3116 and J1752–2956." (Observations and Data Reduction)
- flux scale uncertainty: <10% absolute; fitting uncertainties <~0.1%  
  > "the accuracy of the absolute amplitude calibration is better than $10\%$ for the Band 6 observations" (Observations and Data Reduction)
- self calibration: iterative phase self-calibration  
  > "we applied the phase self-calibration method iteratively" (Observations and Data Reduction)

### Imaging

- task: snapshot images per SPW, 16-56 s integration; flux via imfit  
  > "snapshot images of each SPW were produced with integration times in the range of 16 to 56 sec." (Observations and Data Reduction); "Flux densities and their uncertainties were measured by fitting them to the snapshot images with the CASA task “imfit”." (Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The synthesized beam sizes with natural weighting were $\sim 0.04\ensuremath{''} \times 0.02\ensuremath{''}$." (Observations and Data Reduction)
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
- final beam: ~0.04" x 0.02"  
  > "The synthesized beam sizes with natural weighting were $\sim 0.04\ensuremath{''} \times 0.02\ensuremath{''}$." (Observations and Data Reduction)
- final rms: _not stated_

### Inherited from earlier work

- Analysis of the IRS 13E complex from the same data published separately  
  > "Detailed description of the analysis and the results of the IRS 13E complex from the same data have already been published by (cite: Tsuboi19)." (Observations and Data Reduction) [from (cite: Tsuboi19)]
- Expected time-lag calculation follows van der Laan model and Yusef-Zadeh06/Miyazaki13 analyses  
  > "based on the model of (cite: vanderLaan66) and the following analyses of (cite: Yusef-Zadeh06) and (cite: Miyazaki13)" (Discussion) [from (cite: vanderLaan66); (cite: Yusef-Zadeh06); (cite: Miyazaki13)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (cell size, image size, imaging task, uv range)
- Self-calibration solution intervals and number of iterations
- Which scans were flagged
- Fitting model/component used in imfit
- Structure function and Lomb-Scargle details such as frequency grid
- ZDCF binning parameters
- Number of SPW-combination choices for spectral index and the flux-scale correction between epochs

## Analysis recipe

1. **Calibrate and self-calibrate**: standard calibration then iterative phase self-calibration  
  > "we applied the phase self-calibration method iteratively" (Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: Scans not between two phase calibrator scans were flagged  
  > "Several on-source scans that were not interposed between two adjacent phase calibrator scans were flagged" (Observations and Data Reduction)
2. **Build light curves**: snapshot images per SPW and imfit flux measurement  
  > "Flux densities and their uncertainties were measured by fitting them to the snapshot images with the CASA task “imfit”." (Observations and Data Reduction)
   - software: CASA
   - parameter: integration 16-56 s; 44 or 45 snapshots per 70 min epoch  
  > "We obtained 44 or 45 snapshot images ($N_{\rm obs}$ in Table [1](#tab:obs)) with a 70 min duration for each epoch." (Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Variability timescale**: first-order structure function (15 log bins to 60 min) and Lomb-Scargle periodogram  
  > "We divided the variances into 15 bins equally spaced in logarithmic time lags up to 60 min." (Discussion); "we computed the Lomb-Scargle periodogram" (Discussion)
   - fitting: _not stated_
   - validation: 3 sigma false-alarm probability (Baluev08)  
  > "The heights of the peaks well exceed the $3\,\sigma$ level of the false-alarm probability (cite: Baluev08)." (Discussion)
4. **Time lag between 217.5 and 234.0 GHz**: ZDCF per epoch, quadratic fit to peaks  
  > "We estimated the time lags by fitting a quadratic function to the peaks of the ZDCFs." (Discussion)
   - assumption: p=2 for expected lag  
  > "$p=2$, $\Delta T_{\rm 4-3}$ becomes 1.4 min" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_
5. **Spectral index vs flux**: spectral index between 217.5 and 234.0 GHz at all data points vs 217.5 GHz flux  
  > "We derived spectral indices between the flux densities at 217.5 and 234.0 GHz at all data points." (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.5.0: calibration, self-calibration, imaging, imfit  
  > "Data reduction was performed using the Common Astronomy Software Applications package (CASA)." (Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean flux density at 234.0 GHz | 2.939 | 0.348 | Jy | 2 | The average flux densities of 217.5, 219.5, and 234.0 GHz were $2.912\pm0.331$, $2.914\pm0.331$, and $2.939\pm0.348$ Jy, respectively. |
| Mean spectral index 217.5-234.0 GHz | 0.12 | 0.10 | dimensionless | 5 | The mean spectral index of all the data is $0.12\pm0.10$. |
| Time lag epoch 6 (234.0 delayed) | 2.6 | 0.3 | min | 4 | The variation during epoch 6 at 234.0 GHz is delayed by $2.6\pm0.3$ min from that at 217.5 GHz. |
| Time lag epoch 10 (234.0 precedes) | 1.4 | 0.4 | min | 4 | precedes that at 217.5 GHz by $1.4\pm0.4$ min |
| Largest flux amplitude (epoch 8) | 14% | not stated | percent | 2 | The largest amplitude of flux variation (14%) can be seen during epoch 8 |

## Qualitative findings

- No coherent time lag between 217.5 and 234.0 GHz  
  > "we conclude that there is no coherent time lag between fluxes across the different observed frequencies." (Discussion)

## Claim tuples

- H: Sgr A* shows short-timescale variability at 230 GHz | E: 70 min light curves in ten epochs; structure function and Lomb-Scargle | R: Characteristic timescale of a few tens of minutes and >60 min | F: Short timescale likely from orbital motion near ISCO | **supported**
- H: Lower frequencies lag higher frequencies | E: ZDCF between 217.5 and 234.0 GHz | R: Lags <1 min in 8 epochs; two outliers of opposite sign | F: No coherent time lag | **supported**
- H: Spectral index depends on flux | E: indices vs 217.5 GHz flux | R: higher flux gives higher index | F: Dependence confirmed | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Structure functions may be unreliable for quantitative timescales; observations only 70 min long  
  > "structure functions may not be reliable for quantitative determination of timescales" (Discussion)
- Caveat (inferred, ours): Quasi-periodicity based on few peaks per 70 min epoch; significance of periodograms limited
- Caveat (inferred, ours): Absolute flux scale 10% uncertainty vs per-point fit errors of 0.1% may overstate spectral-index precision
- Caveat (inferred, ours): Self-calibration could affect variability

## Reproducibility

- Data public (paper): ALMA Cycle 5 data cited with project code; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00503.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Self-calibration parameters
- Missing: Imaging parameters
- Missing: Flagging list
- Data volume (inferred): ~100s of GB to 1 TB (ten epochs of Band 6)
- Score (inferred): 3/5, Data identified and workflow simple, but key imaging and self-cal settings missing.
- Rediscovery candidate: yes, Archive data with a simple recipe and numeric results (flux, lags, indices).

## Links

- Method: (cite: Alexander97) (ZDCF method)
- Method: (cite: VanderPlas18) (Lomb-Scargle periodogram)
- Companion: (cite: Tsuboi19) (Same data, IRS 13E analysis)

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 30,
  "rate": 0.455
 },
 "evidence_ok": true
}
```
