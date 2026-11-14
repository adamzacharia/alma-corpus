# Linearly polarized millimeter and submillimeter continuum emission of Sgr A* constrained by ALMA

`2016A&A...593A.107L` | Astronomy and Astrophysics 2016 | first author: Liu, Hauyu Baobab | arXiv: 1605.05544 | DOI: 10.1051/0004-6361/201628731

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, agn_and_quasars
- Question: What are the polarized continuum properties (Stokes I, polarization position angle, polarization percentage) of Sgr A* at ~100, 230, 345, 500 and 700 GHz?  
  > "Our aim is to characterize the polarized continuum emission properties including intensity, polarization position angle, and polarization percentage of Sgr A*" (abstract)
- Target **Sgr A***: coordinates RA 17h45m40.036s, Dec -29d00m28.17s (J2000; band 9 central field center)  
  > "The pointing and phase referencing center of the central field was R.A. (J2000) =17$^{\mbox{\scriptsize{h}}}$45$^{\mbox{\scriptsize{m}}}$40$^{\mbox{\scriptsize{s}}}$.036, and decl. (J2000) =-29$^{\circ}$00$'$28$''$.17" (Observations and Data Reduction, 12m array observations); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00071.S, 2013.1.00126.S, 2011.0.00887.S
- bands: Bands 3, 6, 7, 8, 9  
  > "We analyzed the ALMA observations at band 3 ($\sim$3 mm), 6 ($\sim$1 mm), 7 ($\sim$0.88 mm), 8 ($\sim$0.6 mm), and 9 ($\sim$0.4 mm)." (2 Observations and Data Reduction)
- frequencies and spectral setup: Band 9: four 1.875 GHz spws, 3906.25 kHz channel spacing  
  > "We configured the correlator to provide four 1.875 GHz wide spectral windows (spws)" (2.2.1 12m array observations)
- continuum bandwidth: ~7.5 GHz simultaneous bandwidth per band (bands 3,6,7,8)  
  > "each frequency band was covered with a $\sim$7.5 GHz simultaneous bandwidth" (2.1)
- arrays: 12m Array and ACA  
  > "based on Atacama Large Millimeter Array (ALMA) 12m-Array and Compact Array (ACA) single pointing and mosaic observations" (1 Introduction)
- configurations: _not stated_
- baselines: 12m: 14-400 m (bands 3,6,7), 15-347 m (band 9); ACA 7.3-89 m  
  > "The projected baseline length sampled by the 12m-Array observations is 15-347 meter." (2.2.1 12m array observations)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2012 May 18; 2014 Jul 26; 2015 Apr 30, May 02, Jul 25-26  
  > "The ACA observations were carried out on 2014 July 26" (2.2.2 ACA observations)
- pi or archival as stated: _not stated_
- External data: Previous polarization measurements (position angles, percentages) for comparison; RM and chi0 from Marrone 2007 and Macquart 2006  
  > "RM=(-5.6$\pm$0.7)$\times$10$^{5}$ rad m$^{-2}$ reported by Marrone et al. (2007)" (4 Discussion) [from Aitken et al. 2000; Bower et al. 2003, 2005; Macquart et al. 2006; Marrone et al. 2006a, 2007]

## Processing

### Calibration

- pipeline or manual: Manual CASA calibration: Tsys, WVR (12m only), passband, gain phase per XX/YY, gain amplitude from XX/YY average, flux scaling  
  > "The gain phase solutions were derived separately for the XX and YY correlations, while the gain amplitude solutions were derived from the average of XX and YY correlations." (2.2.3 Data calibration)
- casa version: CASA 4.5  
  > "using the CASA software package (McMullin et al. 2007) version 4.5" (2.2.3 Data calibration)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (plus Neptune in 2012 data)  
  > "Titan+Neptune/NRAO530/J1924-292" (Table 1 obs)
- flux scale uncertainty: nominal 20% for bands 8 and 9  
  > "For the band 8 and 9 observations, we assumed a nominal 20% flux error" (2.3 Measuring fluxes)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub on line-free channels; continuum from averaged line-free channels per spw  
  > "We fitted the continuum baselines from line-free channels, using the CASA task `uvcontsub`." (2.2.3 Data calibration)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12m antennas omitted from ACA data before measuring Stokes I  
  > "The 12m antennas were omitted from the ACA before measuring Stokes I fluxes" (2.3 Measuring fluxes)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Calibration of band 3, 6, 7 observations  
  > "We refer to Brinkerink et al.(2015) for the calibration of the band 3, 6 and 7 observations." (2.1) [from Brinkerink et al. (2015)]
- Band 8 observation details and results  
  > "We refer the details of the band 8 observations to Liu et al. (2016)." (2.1) [from Liu et al. (2016)]

### Not stated but needed to reproduce (our reading)

- Line-free channel selection for uvcontsub
- Modified Miriad uvamp code
- Flux calibrator model/flux values for Titan
- Exact fitting of chi0/RM weights
- Which archival execution blocks map to each epoch

## Analysis recipe

1. **Calibrate and export continuum visibilities**: CASA calibration, uvcontsub, exportfits, convert to Miriad  
  > "Finally, we used the Miriad 4.3.8 (Sault et al. 1995) task `fits` to convert the fits format data into the Miriad data format" (2.2.3 Data calibration)
   - software: CASA, Miriad
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure XX and YY point-source fluxes vs parallactic angle**: Modified Miriad uvamp fitting a point source per 5 deg parallactic-angle bin; band 3 uv>30 klambda  
  > "We fit the fluxes of the XX and the YY correlations separately for every 5$^{\circ}$ bin of parallactic angle." (2.3 Measuring fluxes)
   - software: Miriad uvamp
   - assumption: Source spatially compact so missing short spacings not a concern  
  > "the emission source of our interest is spatially very compact (Bower et al. 2014)" (2.2.2 ACA observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit polarization percentage and angle**: Sinusoidal fit of (XX-YY)/2I - delta = P cos(2(Psi - eta - phi)) with bootstrap-like perturbation  
  > "P, $\Psi$, and $\delta$ and their errors are determined by mean and standard deviations of fittings to 1000 independent realizations" (3.2)
   - parameter: 1000 realizations, Gaussian noise sigma^Q from prior-fit residuals  
  > "we disturb each data point of $(XX- YY)/2I$ with a Gaussian random number of which the standard deviation is $\sigma^Q$" (3.2)
   - assumption: P and Psi constant during each track  
  > "If the polarization position angle and the polarization percentage do not vary significantly in a shorter timescale than the durations of our observing tracks" (3.2)
   - fitting: Least-squares sinusoid fit with Q offset delta free  
  > "we perform a prior fitting of $P$, $\delta$ and $\Psi$, based on XX and YY observed at various $\eta$." (Polarization fitting, intrinsic polarization angle, and rotation measure)
   - validation: Means checked to converge to prior fits; calibrators fitted  
  > "We have checked that those means converged to the values close to a priori fittings." (3.2)
4. **Fit intrinsic angle and rotation measure**: Least squares fit of chi0 and RM to band 3, 6, 7 angles  
  > "Least square fitting of the band 3, 6 and 7 observations on 2012 May 18 yield $\chi_{0}$=138$^{\circ}$$\pm$6$^{\circ}$" (4 Discussion)
   - assumption: Constant chi0 and RM; different photospheres ignored  
  > "our analysis here does not consider the effect that the observations at different frequencies may trace the different photospheres" (4 Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5: Calibration, uvcontsub, exportfits  
  > "were carried out using the CASA software package (McMullin et al. 2007) version 4.5" (2.2.3 Data calibration)
- **Miriad** 4.3.8: Data conversion and flux measurement (modified uvamp)  
  > "We modified the Miriad task `uvamp`, to permit fitting fluxes for a point source as a function of the parallactic angle" (2.3 Measuring fluxes)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| chi0 (2012 May 18 fit) | 138 | 6 | deg | 4 | $\chi_{0}$=138$^{\circ}$$\pm$6$^{\circ}$ |
| RM (2012 May 18 fit) | -4.7e5 | 0.2e5 | rad m^-2 | 4 | RM of (-4.7$\pm$0.2)$\times$10$^{5}$ rad m$^{-2}$ |
| P at 486.150 GHz | 14 | 0.4 | % | 3 | / 486.150       /  12m  /  2015Apr30   / 14$\pm$0.4  /  158$\pm$3  / |
| P at 691.537 GHz (12m) | 8.5 | 1.4 | % | 3 | / 691.537       /  12m  /  2015May02   / 8.5$\pm$1.4 / 141$\pm$14  / |
| Stokes I at 691.537 GHz | 2.68 | 0.54 | Jy | 2 | /  691.537  /  12m  /  2015May02   / 2.68$\pm$0.54 / |

## Qualitative findings

- Polarized emission detected in all bands; P increases monotonically with frequency below 500 GHz  
  > "Below 500 GHz, we see a monotonic increase of polarization percentage with frequency." (5 Conclusion)

## Claim tuples

- H: Is emission at >500 GHz optically thin? | E: Compare Stokes I at ~490 and ~690 GHz | R: Lower flux at ~690 GHz | F: Emission at >~500 GHz may be optically thin | **partially**
- H: Is intrinsic polarization angle constant? | E: Fit chi0 and RM from 2012 data and compare with earlier work | R: chi0=138±6 deg vs ~167 deg earlier | F: Intrinsic angle likely varies with time | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Band 9 parallactic angle coverage limited, so P may be overestimated; no polarization calibration  
  > "A better constraint on $P$ requires future observations which incorporate polarization calibration, or cover sufficiently large parallactic angle ranges." (3.2.2)
- Caveat (inferred, ours): No polarization leakage calibration
- Caveat (inferred, ours): Non-simultaneous multi-epoch comparison confounds variability
- Caveat (inferred, ours): 20% flux error assumed, not measured

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Modified uvamp code
- Missing: Exact data selection and flagging
- Missing: Calibrator flux models
- Data volume (inferred): ~50-200 GB
- Score (inferred): 3/5, Public archival data and clear fit formula, but custom code and calibration details missing.
- Rediscovery candidate: no, Custom modified Miriad task and deferred calibration details prevent a complete recipe.

## Links

- Method: Marti-Vidal et al. 2016 (Formalism for polarimetry with ALMA)
- Companion: Brinkerink et al. (2015) (Band 3, 6, 7 calibration)
- Companion: Liu et al. (2016) (Band 8 observations)

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 31,
  "rate": 0.47
 },
 "evidence_ok": true
}
```
