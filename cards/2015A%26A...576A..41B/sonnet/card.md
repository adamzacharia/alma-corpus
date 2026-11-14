# ALMA and VLA measurements of frequency-dependent time lags in Sagittarius A*: evidence for a relativistic outflow

`2015A&A...576A..41B` | Astronomy and Astrophysics 2015 | first author: Brinkerink, Christiaan D. | arXiv: 1502.03423 | DOI: 10.1051/0004-6361/201424783

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, milky_way_ism
- Question: Do Sgr A* light curves at 19-100 GHz show frequency-dependent time lags indicating an expanding, relativistic outflow/jet?  
  > "Presence of a jet implies that specific correlations should be detected between light curves at different frequencies." (Introduction)
- Target **Sagittarius A***: coordinates _not stated_; z/distance 8.3 ± 0.4 kpc  
  > "Located at a distance of 8.3$\pm 0.4$ kpc from the solar system, its mass is calculated to be $4.3\pm 0.4\cdot 10^6$ $M_{\odot}$" (Introduction); distance from Eisenhauer2003; Reid04; Ghez08; Gillessen09; Genzel2010  
  > "Located at a distance of 8.3$\pm 0.4$ kpc from the solar system, its mass is calculated to be $4.3\pm 0.4\cdot 10^6$ $M_{\odot}$" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00887.S
- bands: ALMA bands 3, 6, 7 observed; only ~100 GHz (Band 3) used here  
  > "In this paper we limit discussion to the 100 GHz ALMA data" (2 Observations and data reduction)
- frequencies and spectral setup: Pairs of spectral windows centered at 95, 105, 247, 260, 338, 348 GHz; 3.75 GHz bandwidth per pair, 7.5 GHz per band  
  > "Each pair of spectral windows covered 3.75 GHz bandwidth for a total of 7.5 GHz bandwidth per ALMA band." (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 19 antennas available  
  > "At that time, ALMA had 19 antennas available." (2 Observations and data reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: Scan lengths chosen for 0.5 mJy  
  > "Scan lengths were chosen to yield a sensitivity of 0.5 mJy." (2 Observations and data reduction)
- time on source: _not stated_
- observing dates: 2012 May 18, 03:30:47-10:52:16 UT  
  > "observations were made in ALMA cycle 0 on May 18, 2012 from 03:30:47 UT to 10:52:16 UT" (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Other facility **VLA**: Light curves at 19, 25.5, 27.48, 37.99, 39.55, 48.5 GHz, CnB config, project 12A-339  
  > "The VLA data (project code: 12A-339) were initially reduced using the VLA pipeline version 1.2.0 (rev. 9744) on CASA 4.1.0." (2 Observations and data reduction)
- External data: Size-frequency relation of Sgr A*: 0.52 mas x (lambda/cm)^1.3  
  > "we can use the size-frequency relation of Sgr A* as presented in (cite: Falcke09) as additional information" (Discussion and conclusion) [from (cite: Falcke09)]
- External data: Miyazaki 102-90 GHz time delay of -2.56 ± 0.9 min  
  > "they reported the time delay between 102 GHz and 90 GHz as being $-2.56 \pm 0.9$ min" (Discussion and conclusion) [from (cite: Miyazaki2013)]

## Processing

### Calibration

- pipeline or manual: ALMA: custom script based on Cycle 0 QA2 procedure; VLA: VLA pipeline 1.2.0 plus self-cal  
  > "The ALMA data were calibrated using a custom script based on the calibration procedure for the QA2 process of Cycle 0 data" (2 Observations and data reduction)
- casa version: CASA 4.1.0 (VLA reduction)  
  > "VLA pipeline version 1.2.0 (rev. 9744) on CASA 4.1.0" (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: ALMA: Titan and Neptune; gain calibrator NRAO530  
  > "while flux density calibration was made on Titan and Neptune" (2 Observations and data reduction)
- flux scale uncertainty: ~5% for ALMA and VLA  
  > "For the ALMA data, the uncertainty in flux density is approximately 5% as well" (2 Observations and data reduction)
- self calibration: Phase self-cal on Sgr A* using baselines >150 klambda  
  > "with subsequent phase self-calibration on Sgr A* (which has a very strong unresolved component of around 2.5 Jy at 100 GHz) using baselines longer than 150 k$\lambda$." (2 Observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: No imaging; uniform weighting of selected visibilities, baselines >150 klambda averaged per scan  
  > "averaging all unflagged UV visibilities per scan from all baselines longer than $150\hspace{3pt}\textrm{k}\lambda$, using uniform weighting for the selected baselines" (2 Observations and data reduction)
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

- FRED function for light-curve fitting  
  > "’fast rise, exponential decay’ (FRED) functions as fitting functions (cite: Bhat1994)" (3 Analysis and results) [from (cite: Bhat1994)]
- Adiabatically expanding plasma cloud model, initial radius 3 Schwarzschild radii  
  > "If we adopt the initial radius of the cloud as being $\sim$3 Schwarzschild radii, as was done by (cite: YZ2008)" (Discussion and conclusion) [from (cite: YZ2008)]

### Not stated but needed to reproduce (our reading)

- ALMA CASA version and exact QA2 script
- Flagging details for ALMA
- FRED fit initial guesses and weighting
- Exact ZDCF settings
- Line-free/continuum channel selection for ALMA
- Numerical time lag versus wavelength fit coefficients

## Analysis recipe

1. **Build light curves**: Average unflagged visibilities per scan over baselines >150 klambda; errors from visibility amplitude spread  
  > "The errors on the flux density levels were estimated using the spread in amplitude of the calibrated visibilities over each scan." (2 Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: Check-source variability sets ~5% uncertainty  
  > "The final uncertainties in flux density are dominated by the calibration uncertainty coming from the variability that was exhibited by the check-source" (2 Observations and data reduction)
2. **Cross-correlate light curves**: ZDCF; zero-lag spikes dominate so no lags derived  
  > "the zero-lag peaks preclude any meaningful time lag estimates to be made this way" (3 Analysis and results)
   - software: ZDCF
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit time of maximum**: FRED fit to bump (7-11h UT VLA, 6:50-8:50 UT ALMA); Monte Carlo dropping half of VLA points, 500 iterations  
  > "at random, half of the data points (20 out of 40) for a given VLA light curve were dropped before attempting a fit with the FRED function. For each light curve, this was iterated 500 times." (3 Analysis and results)
   - assumption: ALMA bump is same event as VLA maxima  
  > "Acting on the assumption that this feature in the ALMA light curve can be attributed to the same event in the source" (3 Analysis and results)
   - fitting: 4-parameter FRED least-squares; priors not stated  
  > "These functions consist of the product of two exponentials, involving four free parameters:" (Analysis and results)
   - validation: VLA-only fit gives practically identical lag relation; ALMA peak coincides with extrapolation  
  > "The time lag expected for the ALMA peak based on the VLA time lag/frequency fit coincides with the measured value" (3 Analysis and results)
4. **Infer outflow velocity**: Combine linear lag vs wavelength fit with size-frequency relation and light-travel-time lag formula for inclination  
  > "Taking into account the influence of light travel time with different inclination angles yields the following expression for the expected time lag between observing frequencies" (Discussion and conclusion)
   - assumption: Distance 8.3 kpc; one-sided jet at i=90 deg or two-sided jet  
  > "When we assume a source inclination of 90$^\circ$ and a one-sided outflow interpretation" (Discussion and conclusion)
   - fitting: _not stated_
   - validation: Compared with Yusef-Zadeh et al. lag  
  > "Yusef-Zadeh et al. reported a time lag between 43 GHz and 22 GHz of 20 to 40 minutes, while we detect a time lag of 28 $\pm$ 9 minutes between these two frequencies" (Discussion and conclusion)

## Software

- **CASA** 4.1.0: VLA pipeline reduction  
  > "VLA pipeline version 1.2.0 (rev. 9744) on CASA 4.1.0" (2 Observations and data reduction)
- **ZDCF** : Cross-correlation of unevenly sampled light curves  
  > "The z-transform discrete correlation function (ZDCF) algorithm (cite: Alexander1997) provides a way to cross-correlate light curves" (3 Analysis and results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spectral index, VLA+ALMA | 0.41 | 0.03 | dimensionless | 0 | has a spectral index of $\alpha = 0.41 \pm 0.03$ |
| Spectral index, VLA only | 0.50 | 0.07 | dimensionless | 0 | we obtain $\alpha = 0.50 \pm 0.07$ when only the VLA data are used |
| Time of maximum at 100 GHz | 7.65 | 0.19 | hrs UT | 3 | 100 GHz / $7.65\pm0.19$ |
| Time of maximum at 19 GHz (all data) | 8.78 | 0.29 | hrs UT | 3 | 19 GHz / $8.78\pm0.29$ |
| Time lag 43-22 GHz | 28 | 9 | minutes | 3 | we detect a time lag of 28 $\pm$ 9 minutes between these two frequencies |
| Predicted lag 102-90 GHz | 1.7 | 0.6 | min | 4 | predicts a time lag between these frequencies of $1.7 \pm 0.6$ min |
| Outflow velocity, one-sided, i=90deg | 0.77c (gamma beta 1.2) | not stated | c | 4 | our data suggest an outflow velocity of $\sim$0.77$c$ ($\gamma\beta\approx1.2$) |
| Minimum flow velocity, two-sided, i=60deg | 0.5c (gamma beta 0.58) | not stated | c | 4 | indicates a minimum flow velocity of $v_f = 0.5$c ($\gamma\beta=0.58$) for an inclination of 60$^\circ$ |

## Qualitative findings

- Higher-frequency light curves peak earlier than lower-frequency ones (25 GHz an exception)  
  > "With the 25 GHz data as notable exception, the maxima occur at later times for the lower observing frequencies" (3 Analysis and results)

## Claim tuples

- H: Sgr A* light curves show frequency-dependent time lags consistent with an outflow | E: FRED fits to VLA and ALMA 100 GHz light curves from one track | R: Maxima shift later with decreasing frequency from 100 to 19 GHz | F: Time lags exist, with a moderately relativistic directed outflow | **supported**
- H: Lags are consistent with earlier reports | E: Compare linear lag/wavelength fit with Yusef-Zadeh et al. | R: 28 ± 9 min at 43-22 GHz | F: Compatible | **supported**
- H: Short-term fluctuations share the lag of the long-term trend | E: Cross-correlation of detrended light curves | R: Peak at zero lag | F: Short-term variations are likely calibration residuals | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: FRED fitting chosen because ZDCF is dominated by zero-lag spikes  
  > "we chose the simple and robust approach of fitting the longer-term flux density evolution in all light curves" (3 Analysis and results)
- Alternative: ZDCF rejected for lag estimates due to zero-lag peaks  
  > "the zero-lag peaks preclude any meaningful time lag estimates to be made this way" (3 Analysis and results)
- How they decided it was enough: _not stated_
- Limitation (authors): Results from a single track; ALMA cadence coarse  
  > "As these results are based upon measurements of a light-curve feature from a single track" (Discussion and conclusion)
- Caveat (inferred, ours): Single ALMA peak with 15-min cadence may not be causally linked to VLA maxima
- Caveat (inferred, ours): 25 GHz outlier and coherence loss at low elevation weaken the lag trend
- Caveat (inferred, ours): Velocity depends on assumed quiescent size-frequency relation and geometry

## Reproducibility

- Data public (paper): ALMA project code given; VLA project 12A-339  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00887.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Custom ALMA calibration script
- Missing: FRED fitting details and starting values
- Missing: Fitted lag-wavelength coefficients
- Data volume (inferred): ~10-50 GB (Cycle 0 ALMA plus VLA)
- Score (inferred): 3/5, Public data and simple method, but custom calibration and fit details are missing.
- Rediscovery candidate: yes, Public data, simple visibility-based light curves and FRED fits with numeric results in Table 1.

## Links

- Method: (cite: Bhat1994) (FRED function)
- Method: (cite: Alexander1997) (ZDCF)
- Companion: (cite: YZ2006) (previous time lag measurement)
- Related: Chandra XVP

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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 36,
  "rate": 0.537
 },
 "evidence_ok": true
}
```
