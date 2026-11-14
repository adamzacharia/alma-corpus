# The 492 GHz emission of Sgr A* constrained by ALMA

`2016A&A...593A..44L` | Astronomy and Astrophysics 2016 | first author: Liu, Hauyu Baobab | arXiv: 1604.00599 | DOI: 10.1051/0004-6361/201628176

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, agn_and_quasars
- Question: Characterize the polarized continuum emission of Sgr A* at ~492 GHz (intensity, polarization position angle, polarization percentage) and compare with lower-frequency observations.  
  > "Our aim is to characterize the polarized continuum emission properties including intensity, polarization position angle, and polarization percentage of Sgr A* at $\sim$492 GHz." (abstract)
- Target **Sgr A***: coordinates RA 17h45m40.036s, Dec -29d00m28.17s (J2000), central field  
  > "The pointing and phase referencing center of the central field was R.A. (J2000) =17$^{\mbox{\scriptsize{h}}}$45$^{\mbox{\scriptsize{m}}}$40$^{\mbox{\scriptsize{s}}}$.036" (2 Observations and Data Reduction); z/distance _not stated_; distance from _not stated_
- Target **J1744-3116 (gain calibrator quasar)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00071.S
- bands: Band 8 (479-482 GHz; 489-493 GHz)  
  > "We have performed Band 8 (479-482 GHz; 489-493 GHz) mosaic observations towards the Galactic center, using the ALMA 12m-Array and the ACA." (5 Conclusions)
- frequencies and spectral setup: four 1.875 GHz spws: 491.3-493.2, 489.3-491.2, 479.2-481.1, 481.0-482.9 GHz; channel spacing 1953.125 kHz (~1.2 km/s); XX and YY correlations only  
  > "We configured the correlator to provide four 1.875 GHz wide spectral windows (spws)" (2 Observations and Data Reduction); "The frequency channel spacing was 1953.125 kHz ($\sim$1.2 km s$^{-1}$)." (2 Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: ALMA 12m Array (39 antennas) and ACA (10 antennas)  
  > "carried out on 2015 April 30 (UTC 06:48:32.4–08:04:38.4), with 39 antennas." (2 Observations and Data Reduction)
- configurations: _not stated_
- baselines: 12m: 25-570 klambda; ACA: 14-80 klambda  
  > "The range of *uv* spatial frequencies sampled by the 12m-Array observations is 25-570 k$\lambda$." (2 Observations and Data Reduction)
- angular resolution: 12m: 0.70"x0.42" (PA -88); ACA: 3.4"x2.2" (PA 78), natural weighting  
  > "$\theta_{\mbox{\scriptsize{maj}}}$$\times$$\theta_{\mbox{\scriptsize{min}}}$ = $3.4\ensuremath{''}$$\times$$2.2\ensuremath{''}$ (P.A.=78$^{\circ}$)" (2 Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 12m: 12.08 s per field x149 fields; ACA: 60.6 s (SE half) or 30.3 s (NW half) per field  
  > "with an on-source integration time of 12.08 seconds for each of the 149 mosaic fields" (2 Observations and Data Reduction)
- observing dates: 2015 April 30  
  > "mosaic observations of 149 fields were carried out on 2015 April 30" (2 Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: CI 3P2-3P1 (492.16065 GHz)
- Line: CS 10-9 (489.75093 GHz)
- External data: Intrinsic PA chi0=167±7 deg and RM=(-5.6±0.7)e5 rad/m2 used to predict 155 deg PA at 492 GHz  
  > "Marrone et al. (2007) reported the fitted intrinsic polarization position angle $\chi_{0}$=167$^{\circ}$$\pm$7$^{\circ}$" (4 Discussion) [from Marrone et al. 2007 (cite: 2007ApJ...654L..57M)]
- External data: Earlier polarization PA records at 230/340 GHz combined with the new point in an RM fit  
  > "together with the records provided by Bower et al. (2003, 2005), Macquart et al. (2006), and Marrone (2006a, 2007)" (4 Discussion) [from Bower et al. 2003, 2005; Macquart et al. 2006; Marrone et al. 2006a, 2007]

## Processing

### Calibration

- pipeline or manual: Manual a priori calibration in CASA (Tsys, WVR, passband, gain, flux scaling)  
  > "were carried out using the CASA software package (McMullin et al. 2007) version 4.3.1." (2 Observations and Data Reduction)
- casa version: CASA 4.3.1  
  > "were carried out using the CASA software package (McMullin et al. 2007) version 4.3.1." (2 Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (absolute flux); J1744-3116 (gain); J1833-2103 (12m passband), J1517-2422 (ACA passband)  
  > "We observed Titan and J1833-2103 for absolute flux and passband calibrations, respectively." (2 Observations and Data Reduction)
- flux scale uncertainty: ~20% (empirical)  
  > "is subject to a large uncertainty (e.g. $\sim$20 %, empirically)." (2 Observations and Data Reduction)
- self calibration: Miriad selfcal options=mosaic, 0.01 min solution interval, on central 7 fields with model from demos  
  > "using the Miriad task `selfcal options=mosaic`, with a 0.01 minute solution interval." (3.1 Continuum data)

### Imaging

- task: Miriad dirty images (no clean)  
  > "For all of these images we do not make deconvolved CI line (i.e. `clean`ed) maps" (2 Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "of the continuum using naturally weighed data for the 12m-Array and ACA" (2 Observations and Data Reduction)
- uv taper: Gaussian taper FWHM = 1.5" for CI line on 12m data  
  > "we tapered the 12m-Array data using a Gaussian weighting function of FWHM = $1.5\ensuremath{''}$" (2 Observations and Data Reduction)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CASA uvcontsub from line-free channels  
  > "We fitted the continuum baselines from line-free channels, using the CASA task `uvcontsub`." (2 Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12m and ACA treated separately  
  > "However, we were not able to obtain a meaningful constraint of $F_{XX}^{CI}(\nu)$ / $F_{YY}^{CI}(\nu)$ from the ACA observations" (3.2 Spectral line data)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges used for uvcontsub
- Polynomial order of uvcontsub fit
- Flagging details
- Model flux/shape used in demos for self-calibration
- How the bootstrap errors in the XX/YY fits were computed
- Image size and cell size
- Titan flux model used for flux scaling

## Analysis recipe

1. **Calibrate and prepare continuum and line data**: CASA a priori calibration; inter-spw phase offsets from passband scans; XX/YY phase solutions separately, amplitude from XX+YY average; uvcontsub; export to Miriad  
  > "The gain phase solutions were derived separately for the XX and YY correlations, while the gain amplitude solutions were derived from the average of XX and YY correlations." (2 Observations and Data Reduction)
   - software: CASA, Miriad
   - parameter: gain phase solved on all spws averaged together; WVR applied to 12m data  
  > "we chose to apply the wvr solutions to the 12m data" (2 Observations and Data Reduction)
   - fitting: _not stated_
   - validation: Titan XX/YY ratios ~1 from <100 m baselines  
  > "the XX/YY flux ratios of Titan measured from spw 0, 1, 2, and 3, are 0.99, 0.98, 1.0, and 1.0, respectively." (3.1 Continuum data)
2. **Self-calibrate phases and measure Sgr A* XX/YY fluxes**: fixvis to shift phase centers; Miriad demos model and selfcal for central 7 fields; uvflux to fit amplitudes per field/correlation  
  > "Then, we used the Miriad task `uvflux` to fit the observed amplitudes from the visibility data." (3.1 Continuum data)
   - software: CASA fixvis, Miriad demos, Miriad selfcal, Miriad uvflux
   - parameter: selfcal solution interval 0.01 min; nominal ALMA primary beam  
  > "assuming the nominal ALMA primary beam shape, to generate models of Sgr A* for the central 7 mosaic fields" (3.1 Continuum data)
   - fitting: _not stated_
   - validation: Self-cal did not significantly change XX/YY ratios  
  > "The application of phase self-calibration solutions does not significantly change the observed amplitude (or flux) ratios between the XX and the YY correlations." (3.1 Continuum data)
3. **Fit polarization percentage and position angle**: Least-squares fit of XX/YY ratio vs parallactic angle with Q/I - delta = P cos(2(Psi - eta - phi)); Evector 0 deg  
  > "Evector of ALMA is 0$^{\circ}$ for the frequency band we observed." (3 Results)
   - parameter: constant polarization PA assumed; Q offset delta fitted  
  > "From a least square fit to constant polarization position angle" (3.1 Continuum data)
   - assumption: Non-variable source; Stokes U not determined (no XY/YX)  
  > "we are not able to determine Stokes U." (4 Discussion)
   - fitting: Least-squares (bootstrap shown in figures); priors not stated  
  > "From a least square fit to constant polarization position angle, the measured XX to YY intensity ratios for Sgr A\* are consistent with the polarization percentage of $\sim$14%$\pm$1.2%" (Results, Continuum data)
   - validation: Checked DA-only, DV-only, DA-DV subsets and with/without PM antennas; consistent across spws  
  > "We obtained identical measurements from these three subsets." (3.1 Continuum data)
4. **Gauge spurious polarization using CI line and Titan**: Miriad imdiff to find XX/YY multiplicative factor in CI images over a box region, per scan and per 2.5 km/s channel; compare with continuum ratio and absorption  
  > "We used the Miriad task `imdiff` to systematically estimate the multiplicative factor that minimizes the difference between the XX and YY synthesized images of CI" (3.2 Spectral line data)
   - software: Miriad imdiff
   - parameter: 2.5 km/s velocity channels; CI 12m data tapered at 1.5"  
  > "for every 2.5 km s$^{-1}$ wide velocity channels" (3.2 Spectral line data)
   - assumption: Foreground CI absorber has negligible Tex and identical tau for X and Y  
  > "it is safe to assume that $T_{ex}$ is negligible, and the gas optical depth $\tau$ is identical for the orthogonal linear polarizations X and Y." (3.2 Spectral line data)
   - fitting: Maximum likelihood factor minimizing XX-YY image difference  
  > "estimate the multiplicative factor that minimizes the difference between the XX and YY synthesized images of CI in a maximum likelihood sense" (Results, Spectral line data)
   - validation: Residuals consistent with thermal noise; CI emission XX/YY ~1 away from absorption  
  > "we found that $R(\nu, t)$, and its time integration, are consistent with thermal noise." (3.2 Spectral line data)
5. **Compare PA with lower-frequency measurements**: Extrapolate Marrone et al. 2007 chi0 and RM to 492 GHz; refit chi0 and RM including the new point with literature data  
  > "Least square fitting of our measured polarization position angle at 492 GHz, together with the records provided by Bower et al. (2003, 2005), Macquart et al. (2006), and Marrone (2006a, 2007)" (4 Discussion)
   - fitting: Least squares for chi0 and RM  
  > "Least square fitting of our measured polarization position angle at 492 GHz, together with the records provided by Bower et al. (2003, 2005), Macquart et al. (2006), and Marrone (2006a, 2007), yield" (Discussion)
   - validation: _not stated_

## Software

- **CASA** 4.3.1: A priori calibration, uvcontsub, exportfits, fixvis  
  > "We then exported the calibrated continuum data and the continuum-subtracted line data in standard fits format files, using the CASA task `exportfits`." (2 Observations and Data Reduction)
- **Miriad** 4.3.8: Format conversion, imaging, selfcal, uvflux, imdiff  
  > "Finally, we used the Miriad 4.3.8 (Sault et al. 1995) task `fits` to convert the fits format data into the Miriad data format" (2 Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Sgr A* Stokes I flux at 492 GHz | 3.6 | 0.72 | Jy | 2 | After self-calibration, the averaged flux of Sgr A* at 492 GHz is 3.6$\pm$0.72 Jy. |
| Sgr A* polarization percentage (lower limit) | 14 | 1.2 | % | 3 | consistent with the polarization percentage of $\sim$14%$\pm$1.2% and a position angle of $\sim$158$^{\circ}$$\pm$3$^{\circ}$ |
| Sgr A* polarization position angle | 158 | 3 | deg | 3 | a position angle of $\sim$158$^{\circ}$$\pm$3$^{\circ}$ |
| J1744-3116 Stokes I | 252 | not stated | mJy | 3 | can be fitted to Stokes I = 252 mJy |
| J1744-3116 polarization percentage | 7.9 | 0.9 | % | 3 | with 7.9%$\pm$0.9% polarization in position angle P.A. = 14.1$^{\circ}$$\pm$4.2$^{\circ}$ |
| J1744-3116 polarization PA | 14.1 | 4.2 | deg | 3 | P.A. = 14.1$^{\circ}$$\pm$4.2$^{\circ}$ |
| J1744-3116 normalized Q offset delta | -0.02 | 0.02 | dimensionless | 3 | $\delta$=$-$0.02$\pm$0.02 |
| Peak CI absorption XX/YY ratio near vlsr~20 km/s | ~1.3 | not stated | dimensionless | 4 | The local peak value of $F_{XX}^{CI}(\nu)$ / $F_{YY}^{CI}(\nu)$ is $\sim$1.3 (or 0.11 in logarithm). |
| Std of CI XX/YY away from 20 km/s | 0.043 | not stated | dimensionless | 4 | is 0.043. |
| Predicted PA at 492 GHz from Marrone 2007 | 155 (+9/-8) | +9/-8 | deg | 5 | which inplies a 155$^{+9}_{-8}$$^{\circ}$ polarization position angle at 492 GHz. |
| Refit RM including 492 GHz point | -4.9e5 | 1.2e5 | rad m^-2 | 5 | RM of ($-$4.9$\pm$1.2)$\times$10$^{5}$ rad m$^{-2}$ |
| Titan XX/YY continuum difference | ~3 | not stated | % | 4 | The continuum emission from Titan shows a $\sim$3% intensity difference between the XX and the YY correlations. |

## Qualitative findings

- Sgr A* continuum shows large XX/YY differences not seen in CI line emission or Titan, attributed to linearly polarized synchrotron emission.  
  > "Therefore, we attribute the observed intensity differences to linearly polarized synchrotron emission from hot ionized gas immediately surrounding Sgr A*." (5 Conclusions)

## Claim tuples

- H: Sgr A* at 492 GHz is linearly polarized, and the XX/YY difference is not instrumental. | E: Fit XX/YY vs parallactic angle; compare with Titan, CI line emission, antenna subsets and spws. | R: Polarization ~14±1.2% (lower limit), PA ~158±3 deg; CI emission and Titan show ~1 or ~3% ratios. | F: Polarized synchrotron emission is the most probable explanation. | **supported**
- H: The 492 GHz polarization PA is consistent with extrapolation from 1999-2005 lower-frequency data. | E: Compare measured PA with the PA predicted from chi0 and RM of Marrone et al. 2007; refit RM. | R: Predicted 155 (+9/-8) deg vs measured 158±3 deg; RM -4.9±1.2e5 rad/m2. | F: Consistent within 1 sigma; no evidence for large change in accretion rate or field configuration. | **supported**
- H: The 90 deg PA flip expected at higher frequencies may appear at 492 GHz. | E: Compare measured PA with lower-frequency values. | R: No flip detected. | F: Frequency may be too low; whether emission is optically thin is uncertain. | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Instrumental causes (beam squint, gain drift, phase decoherence, primary beam polarization, DA/DV heterogeneity) were considered and judged unable to explain the XX/YY difference.  
  > "or instrumental effects including (1) beam squint, (2) relative drifts of instrumental gain amplitude between the XX and YY correlations, (3) phase decoherence for a certain polarization, and (4) primary beam polarization." (4 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): No XY/YX cross-correlations, so Stokes U is undetermined and the polarization percentage is a lower limit.  
  > "lacking the cross-correlations XY and YX which were not sampled in these observations, we are not able to determine Stokes U." (4 Discussion)
- Limitation (authors): Absolute flux uncertain (~20%) because Titan scans were largely flagged; single epoch only.  
  > "The scans on Titan were largely flagged due to interference from spectral lines." (2 Observations and Data Reduction)
- Caveat (inferred, ours): Polarization inferred from XX/YY alone with no cross-hand data is vulnerable to uncalibrated gain/leakage differences
- Caveat (inferred, ours): Fit quality is imperfect, and time variability can mimic the parallactic-angle dependence
- Caveat (inferred, ours): Errors on the 14% and 158 deg values may be underestimated given the 20% flux uncertainty
- Caveat (inferred, ours): Self-calibration with a point-source model on a mosaic with large pointing errors may bias amplitudes

## Reproducibility

- Data public (paper): ALMA data cited by project code 2013.1.00071.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA 2013.1.00071.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Line-free channel selection
- Missing: Self-calibration model details
- Missing: Flagging
- Missing: Fit uncertainty/bootstrap procedure details
- Missing: Titan flux model
- Data volume (inferred): ~50-200 GB raw for 12m plus ACA mosaic of 149 fields
- Score (inferred): 3/5, Data public and software named, but several processing details (line-free channels, flagging, fit procedure) are missing and the result depends on custom analysis.
- Rediscovery candidate: no, The recipe lacks key details and the XX/YY fit relies on unspecified procedures, although results are numeric.

## Links

- Method: Marti-Vidal et al. 2016 (cite: 2016arXiv160306072M) (Similar technique used to estimate rotation measure of PKS 1830-211)
- Companion: Liu et al. in prep. (Detailed CI emission analysis)

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 46,
  "rate": 0.613
 },
 "evidence_ok": true
}
```
