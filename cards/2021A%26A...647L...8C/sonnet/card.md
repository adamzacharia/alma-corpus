# First direct measurement of auroral and equatorial jets in the stratosphere of Jupiter

`2021A&A...647L...8C` | Astronomy and Astrophysics 2021 | first author: Cavalié, T. | arXiv: 2103.12208 | DOI: 10.1051/0004-6361/202140330

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: What are the wind speeds in Jupiter's stratosphere as a function of latitude, measured directly from Doppler shifts of HCN lines?  
  > "we bridge the altitude gap between these measurements by directly measuring the wind speeds in Jupiter’s stratosphere." (abstract)
- Target **Jupiter**: coordinates _not stated_; z/distance equatorial diameter 43.8 arcsec at observation  
  > "Jupiter’s equatorial diameter subtended a 43.8$''$ angle, the sub-earth point latitude was -3$^\circ$" (2 Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01235.S
- bands: _not stated_
- frequencies and spectral setup: HCN: 122.070 kHz over 234.375 MHz; CO: 488.242 kHz over 937.5 MHz  
  > "The highest spectral resolution was 122.070 kHz ($\sim$103 m/s) over a bandwidth of 234.375 MHz." (Appendix A)
- continuum bandwidth: _not stated_
- arrays: 42 12-m antennas  
  > "on March 22$^\mathrm{nd}$, 2017, at 5:11-5:36UT with 42 12-m antennas" (2 Observations)
- configurations: _not stated_
- baselines: 15.1 to 160.7 m  
  > "The baselines of the interferometer ranged from 15.1 to 160.7 m" (2 Observations)
- angular resolution: 1.2'' (E-W) x 1'' (N-S) beam  
  > "providing an elliptical synthesized beam of 1.2$''$ (East-West) $\times$ 1$''$ (North-South)" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: 48 mJy/beam per 122 kHz (HCN); 17 mJy/beam per 488 kHz (CO)  
  > "We obtain a sensitivity of 48 mJy/beam per 122 kHz resolution element in the HCN baseband." (Appendix A)
- time on source: 24 minutes  
  > "The accumulated on-source integration time of 24 minutes" (2 Observations)
- observing dates: 22 March 2017, 5:11-5:36 UT  
  > "We observed Jupiter with the ALMA interferometer on March 22$^\mathrm{nd}$, 2017, at 5:11-5:36UT" (2 Observations)
- pi or archival as stated: _not stated_
- Line: HCN 5-4 (354.505 GHz)
- Line: CO 3-2 (345.796 GHz)
- External data: Oval edges used as model input  
  > "We took the inner and outer oval edges as defined by (cite: Bonfond2012)." (5.2) [from (cite: Bonfond2012)]
- External data: Statistical UV aurora brightness  
  > "We thus chose to use the statistical UV aurora brightness model derived from the observations of (cite: Clarke2009)" (Appendix F) [from (cite: Clarke2009)]
- External data: M=30 footprints of magnetic field model  
  > "the M=30 footprints of (cite: Connerney2018)’s model of the magnetic field" (5.2) [from (cite: Connerney2018)]

## Processing

### Calibration

- pipeline or manual: CASA data reduction with pointing, bandpass, amplitude and phase calibrations  
  > "The data reduction process was run under CASA 4.7.2 and included pointing, bandpass, amplitude and phase calibrations." (Appendix A)
- casa version: CASA 4.7.2  
  > "The data reduction process was run under CASA 4.7.2" (Appendix A)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede (amplitude); J1256-0547 bandpass; J1312-0424 phase  
  > "amplitude calibration observations were acquired using Ganymede as a target." (Appendix A)
- flux scale uncertainty: _not stated_
- self calibration: Self-calibrated to center Jupiter on the image  
  > "After self-calibrating the data to center Jupiter at best on the image" (Appendix D)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane subtraction in CASA before imaging, plus 1st order polynomial on spectra  
  > "We proceed with an additional subtraction of a 1st order polynomial from the spectra to flatten their continuum." (Appendix D)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12-m only; extended emission filtered out, only limb imaged  
  > "Because of the limited uv-coverage in the short baselines, the extended emission of Jupiter is mostly filtered out and only the limb of the planet is imaged." (Appendix A)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Wind contribution function definition  
  > "Following (cite: Lellouch2019), we computed the “wind contribution function” of the HCN line" (Appendix B) [from (cite: Lellouch2019)]
- Radiative transfer model  
  > "the radiative transfer model of (cite: Cavalie2019)" (4) [from (cite: Cavalie2019)]

### Not stated but needed to reproduce (our reading)

- tclean parameters (weighting, robust, cell, image size, deconvolver)
- line-free channels for continuum subtraction
- self-calibration solution intervals
- exact spectrum extraction positions
- temperature profile used in radiative transfer
- MCMC priors on nuisance parameters

## Analysis recipe

1. **Extract limb spectra**: Extract ~550 spectra at planet limb (1 bar level) from each cube, oversampling beam by 4-5  
  > "we extracted $\sim$550 spectra located at the planet limb (at the 1 bar level) to oversample the beam by a factor of 4 to 5" (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit line centers with MCMC**: Fit parametrized symmetric line shape; subtract planet rotation to get LOS wind  
  > "We determined the line-of-sight (LOS) wind speeds as a function of latitude by fitting the HCN lines with a Markov Chain Monte Carlo (MCMC) scheme" (5 Wind speed retrieval)
   - software: emcee
   - parameter: 32 walkers, max 2200 iterations, burn-in 540±100  
  > "setting a maximum of 2200 iterations for each of the 32 “walkers”" (Appendix C)
   - assumption: Vertically constant wind in line-forming layers  
  > "We therefore assume a vertically constant wind in the altitude layers where the lines are formed" (Appendix C)
   - fitting: Affine-invariant ensemble MCMC; free: A, nu0, Gamma, gamma, noise  
  > "$A$, $\nu_0$, $\Gamma$ and $\gamma$ are MCMC fitting parameters, as well as the spectrum noise level." (Appendix C)
   - validation: Best fits overplotted on spectra; error budget analysis  
  > "We selected the 30 best-fit obtained from these iterations to demonstrate in Fig. [1](#Map_spectra) the fitting quality obtained with our parametrized line shape." (Retrieval of wind speeds as a function of latitude)
3. **Model auroral oval wind**: Forward model of constant counter-rotation wind within oval, convolved with beam  
  > "we implemented a model in which we assumed a constant wind within the southern oval and no wind outside the oval." (5.2)
   - assumption: HCN 1 ppb below cut-off pressure 5 mbar or 0.1 mbar  
  > "For latitudes lower than 60$^\circ$S and higher than 50$^\circ$N, HCN was set constant to 1 ppb for $p_0$ $<$ 0.1 mbar, and to zero at higher pressures." (Modeling the spectral effect of a constant counter-rotation wind inside the auroral ovals)
   - fitting: _not stated_
   - validation: Compared with measured wind curves  
  > "The LOS projected components of the auroral oval wind at infinite spatial resolution are presented in Fig. [7](#S4) and the comparison with the wind measurements is shown in Fig. [6](#S3)." (Modeling the spectral effect of a constant counter-rotation wind inside the auroral ovals)

## Software

- **CASA** 4.7.2: Data reduction  
  > "The data reduction process was run under CASA 4.7.2" (Appendix A)
- **emcee** : MCMC fitting  
  > "(cite: Goodman2010; Foreman-Mackey2019)" (5 Wind speed retrieval)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak LOS velocity of equatorial prograde jet (eastern limb) at 9-11N | +215 | ±25 | m/s | 2 | peak LOS velocity of +215$\pm$25 m/s on the planet eastern limb |
| Average eastward equatorial wind speed | 165 | ±40 | m/s | 2 | The average eastward wind speed is 165$\pm$40 m/s |
| Peak LOS velocity at 70S eastern limb | -350 | ±20 | m/s | 2 | a peak LOS velocity of -350$\pm$20 m/s |
| Southern auroral oval wind | 370 | not stated | m/s | 3 | a 370 m/s counter-rotation wind inside the auroral oval |
| Northern oval wind | 300 | not stated | m/s | 3 | wind speeds of 300 m/s in the northern oval and 370 m/s in the southern oval |

## Qualitative findings

- Winds are zonal at low-to-mid latitudes and non-zonal at polar latitudes beneath the auroral ovals  
  > "They are zonal at low-to-mid latitudes and non-zonal at polar latitudes." (abstract)

## Claim tuples

- H: Stratospheric winds can be directly measured | E: Fit Doppler shifts of HCN lines on the limb | R: Equatorial jet ~+215 m/s at 1 mbar | F: Direct detection of equatorial stratospheric jets | **supported**
- H: Auroral winds extend to the stratosphere | E: Fit polar limb spectra and oval model | R: 300-400 m/s counter-rotating winds at 0.1 mbar | F: Auroral jets reach sub-mbar level | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Northern oval poorly viewed; northern detection tentative  
  > "our detection in the northern oval remains tentative" (7 Discussion)
- Caveat (inferred, ours): Ad hoc extension of oval edges to fit data
- Caveat (inferred, ours): Empirical line shape with fixed parameters
- Caveat (inferred, ours): Single epoch

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: imaging parameters
- Missing: MCMC code
- Missing: radiative transfer inputs
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Data public, but imaging and fitting details sparse.
- Rediscovery candidate: no, Imaging recipe incomplete.

## Links

- Method: (cite: Lellouch2019) (wind contribution function)
- Method: (cite: Cavalie2019) (radiative transfer model)

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
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
  "facts": 64,
  "stated": 33,
  "rate": 0.516
 },
 "evidence_ok": true
}
```
