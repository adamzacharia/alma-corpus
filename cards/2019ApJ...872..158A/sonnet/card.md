# Resolved Young Binary Systems and Their Disks

`2019ApJ...872..158A` | The Astrophysical Journal 2019 | first author: Akeson, Rachel L. | arXiv: 1901.05029 | DOI: 10.3847/1538-4357/aaff6a

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: How do stellar mass and stellar multiplicity affect the 1.3 mm flux and mass of circumstellar disks in Class II Taurus systems?  
  > "to explore two of the factors affecting these disks: the influence of stellar mass, and the influence of stellar companions." (Introduction)
- Target **Taurus Class II single and multiple systems (45 systems, 65 stars observed)**: coordinates _not stated_; z/distance ~140 pc; per-source Gaia DR2 distances, fallback median 138.8±18.8 pc  
  > "We selected targets from a single star forming region, Taurus (distance $\sim$ 140 pc)" (2.1 Sample); "we took distances and uncertainties from (cite: BailerJones2018)." (3.1 Continuum emission); distance from Gaia DR2 via Bailer-Jones et al. 2018  
  > "We selected targets from a single star forming region, Taurus (distance $\sim$ 140 pc)" (2.1 Sample); "we took distances and uncertainties from (cite: BailerJones2018)." (3.1 Continuum emission)

## Data provenance

- ALMA projects: 2013.1.00105.S, 2015.1.00392.S
- bands: Band 6 (1.3 mm)  
  > "We selected Band 6 (1.3 mm) for these ALMA observations." (2.2 ALMA Data Reduction)
- frequencies and spectral setup: Three correlator sections for continuum, fourth set to CO(2-1) at 230.5 GHz  
  > "Three of the correlator sections were set for continuum emission sensitivity, with the fourth set to the transition for CO(2–1) at 230.5 GHz." (2.2 ALMA Data Reduction)
- continuum bandwidth: 7.5 GHz  
  > "The total continuum bandwidth was 7.5 GHz." (2.2 ALMA Data Reduction)
- arrays: 34-41 antennas  
  > "2015.1.00392.S | 2016 July 1$^{b}$ | 41       | 0.75 x 0.42" (Table 1)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.2 arcsec; beams 0.18x0.16 to 0.87x0.43 arcsec  
  > "resolvable in a snapshot survey at moderate (i.e. $\sim$0.2$''$) resolution" (Introduction)
- max recoverable scale: _not stated_
- sensitivity: average 3 sigma ~0.35 mJy  
  > "have an average 3$\sigma$ detection level of 0.35 mJy" (abstract)
- time on source: _not stated_
- observing dates: 2015 May 3, 2015 Sept 18, 2015 Sept 19, 2016 July 1  
  > "2013.1.00105.S | 2015 Sept 18      | 34       | 0.24 x 0.13" (Table 1)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230.5 GHz)
- Other facility **Gaia DR2**: parallax distances and positions for comparison  
  > "Gaia DR2 (cite: gaia18) contains parallax measurements for most of our sources" (3.1 Continuum emission)
- External data: Taurus millimeter fluxes compilation  
  > "The flux values come primarily from this work and from the compilation of (cite: and13)" (4.1 Defining a sample) [from (cite: and13)]
- External data: Stellar spectral types from the literature  
  > "we compiled spectral types from the literature, trying wherever possible to go to the original references" (3.3 Stellar properties) [from references listed in Table 8]
- External data: Literature binary separations and PAs  
  > "FO Tau AB | 0.124$\pm$0.012 | 253.2$\pm$3.7 | 0.150$\pm$0.007 | 193.7$\pm$1.0 | White and Ghez (2001)" (Table 3) [from (cite: whi01)]
- External data: Companion detection limits for single-star sample  
  > "We drew limits on companions primarily from (cite: kra11; kra12)" (4.2.1 Single star sample) [from (cite: kra11; kra12)]
- Simulation/model as data: Baraffe2015 models (Teff<=4210 K) and MIST (Choi2016) for stellar mass and luminosity at assumed age 1 Myr  
  > "from the models of (cite: Baraffe2015) for $T_{\rm eff} \le 4210$ K and the MIST models from (cite: Choi2016) for $T_{\rm eff} > 4210$ K." (3.3 Stellar properties)

## Processing

### Calibration

- pipeline or manual: 2015 data: ALMA-provided calibration; 2016 data reprocessed from raw with CASA pipeline scripts  
  > "For the datasets from 2015, we used the calibration provided by ALMA and created images using the *CASA* package (cite: mcm07)." (2.2 ALMA Data Reduction); "so we processed the raw data using the pipeline scripts in *CASA*." (2.2 ALMA Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 5% absolute flux calibration (ALMA memo 594)  
  > "a 5% absolute flux calibration uncertainty (ALMA memo 594)" (3.1 Continuum emission)
- self calibration: Performed for sources with sufficient continuum flux  
  > "For sources with sufficient continuum flux, we also performed self-calibration." (2.2 ALMA Data Reduction)

### Imaging

- task: CASA clean; imfit for 2D Gaussian integrated flux  
  > "For each target, the *CASA* routine *clean* was used to produce an image." (2.2 ALMA Data Reduction)
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
- final rms: rms measured in cleaned region without known sources; typical 3 sigma limit ~0.35 mJy  
  > "The flux uncertainty was measured as the rms in the cleaned portion of the image without known sources." (2.2 ALMA Data Reduction)

### Inherited from earlier work

- Disk mass constants: dust-to-gas 0.01, kappa=2.3 cm2/g at 1.3 mm, Td=25 (L/Lsun)^-1/4 K  
  > "we use the same constants of dust-to-gas ratio $X_g$ = 0.01 and dust opacity $\kappa_{\nu}$ = 2.3 cm$^2$ g$^{-1}$ at 1.3 mm." (3.1 Continuum emission) [from (cite: and13)]
- Stellar mass and luminosity determination approach  
  > "we followed the approach of (cite: wd18) to determine stellar masses and luminosities." (3.3 Stellar properties) [from (cite: wd18)]
- Linear regression procedure with linmix  
  > "We followed the same procedure as (cite: and13), using the *LINMIX_ERR* MCMC algorithm of (cite: Kelly2007)" (4.4 Accounting for stellar mass) [from (cite: and13); (cite: Kelly2007)]
- Gaia astrometric quality via RUWE  
  > "we followed the procedure recommended in Gaia Technical Note GAIA-C3-TN-LU-LL-124-01 (cite: Lindegren2018)." (3.1 Continuum emission) [from (cite: Lindegren2018)]
- 30 arcsec outer separation cutoff  
  > "The outer cutoff was set at a projected separation of 30$''$ (4200 AU) following (cite: kra09)" (4.2.2 Binary sample) [from (cite: kra09)]
- Paper 1 binary survey data (fluxes)  
  > "9) Paper 1" (Table 8 notes) [from Paper 1 (cite: ake14)]

### Not stated but needed to reproduce (our reading)

- tclean/clean parameters: weighting, robust, cell size, image size, masks, threshold
- CASA version for imaging and pipeline
- Self-calibration solution intervals and which sources were self-calibrated
- Continuum channel selection and CO line-free channels
- Flux calibrator and gain calibrators
- Exact imfit regions
- Whether the CO moment maps were made with what velocity range
- Table 8 fluxes from older data used as-is for non-ALMA-new sources

## Analysis recipe

1. **Image continuum and measure fluxes**: clean images; detection >3 sigma peak at known position; imfit 2D Gaussian for integrated flux  
  > "detections were defined as a $>3\sigma$ peak at the known location." (2.2 ALMA Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: positions compared to Gaia DR2 (agree within few tens of mas)  
  > "comparison of our measured positions with those from Gaia DR2 (cite: gaia18) typically agree to within a few tens of milliarcseconds" (3.1 Continuum emission)
2. **Determine distances**: Bailer-Jones Gaia DR2 distances with RUWE<=1.6; else weighted mean within 30'; else median 138.8 pc  
  > "retaining only those with RUWE $\le 1.6$." (3.1 Continuum emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive stellar masses and luminosities**: spectral type to Teff (Herczeg & Hillenbrand 2014), then Baraffe2015/MIST at 1 Myr with cubic spline  
  > "In all cases, we used cubic spline interpolation between tabulated values" (3.3 Stellar properties)
   - parameter: spectral type uncertainty ±1 subclass  
  > "we adopted an assumed spectral type uncertainty of $\pm1$ spectral subclass" (3.3 Stellar properties)
   - assumption: age 1 Myr  
  > "We then adopted an assumed age of 1 Myr for Taurus" (3.3 Stellar properties)
   - fitting: _not stated_
   - validation: _not stated_
4. **Convert flux to disk mass**: optically thin Md = F d^2/(kappa Xg B(Td))  
  > "Assuming the dust is optically thin, the conversion from flux ($F_{\nu}$) to disk mass ($M_d$) is" (3.1 Continuum emission)
   - assumption: Xg=0.01, kappa=2.3 cm2/g, Td=25 L^-1/4 K  
  > "we also adopt the (cite: and13) scaling of $T_d = 25 (L_{\ast}/L_{\odot})^{-1/4}$ K." (3.1 Continuum emission)
   - fitting: _not stated_
   - validation: _not stated_
5. **Statistical comparison of singles, primaries, secondaries**: censored-data log-rank tests, Kaplan-Meier, Kendall tau (cenken), linmix regression  
  > "we used the R statistical package, in all cases using routines for censored data to account for the upper limits in millimeter flux." (4.3 Statistical Calculations)
   - software: R survival, cenken, linmix
   - parameter: stellar mass cutoff 0.06 Msun (M6); wide/close split at 1 arcsec (~140 AU)  
  > "this stellar mass cutoff is 0.06 M$_{\odot}$ or a spectral type of M6." (4.2 Stellar Mass)
   - fitting: LINMIX_ERR MCMC (Kelly 2007); priors not stated  
  > "using the *LINMIX_ERR* MCMC algorithm of (cite: Kelly2007), as implemented in the Python package *linmix* by Josh Myers." (4.4 Accounting for stellar mass)
   - validation: slopes compared with Andrews et al. 2013 and Pascucci et al. 2016  
  > "broadly consistent with those found by (cite: and13) and (cite: pas16)" (4.4 Accounting for stellar mass)

## Software

- **CASA** : imaging, imfit, pipeline reprocessing of 2016 data  
  > "created images using the *CASA* package (cite: mcm07)" (2.2 ALMA Data Reduction)
- **R (survival: survdiff, survfit; cenken)** : censored statistical tests  
  > "From the *survival* package we used the log rank test from the *survdiff* function" (4.3 Statistical Calculations)
- **linmix** : Bayesian linear regression with censored data  
  > "as implemented in the Python package *linmix* by Josh Myers" (4.4 Accounting for stellar mass)
- **Astropy** : general analysis  
  > "CASA (cite: mcm07), R, Astropy (cite: Astropy2018), matplotlib (cite: Hunter2007)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| New millimeter detections | 21 (6 singles, 4 primaries, 11 companions) | not stated | count | 1 | These observations resulted in 21 new detections: 6 single stars, 4 primary stars, and 11 companion stars. |
| Disk mass limit for M3 star at 3 sigma 0.35 mJy | 4e-5 | not stated | Msun | 4 | total disk mass limit of $4 \times 10^{-5}$ M$_{\odot}$ |
| Flux-stellar mass intercept, singles | 1.80 | +0.17/-0.18 | log mJy | 5 | $1.80^{+0.17}_{-0.18}$ for the single stars |
| Flux-stellar mass intercept, binaries | 1.26 | +0.17/-0.18 | log mJy | 5 | $1.26^{+0.17}_{-0.18}$ for the individual stars in binary systems |
| Flux-mass slope singles | 1.73 | +0.27/-0.27 | dimensionless | 5 | 1.73$^{+0.27}_{-0.27}$ for single stars |
| Flux-mass slope binaries | 1.93 | +0.42/-0.39 | dimensionless | 5 | 1.93$^{+0.42}_{-0.39}$ for binary stars |
| Secondary vs single flux p-value | 0.027 | not stated | dimensionless | 5 | the secondary fluxes arise from a different sample than the singles ($p=0.027$) |
| Primary share of total disk mass | 62% | not stated | percent | 5 | The disk mass from the primary star accounts for 62% of the total mass on average |
| Median total flux close vs wide binaries | 4.7 mJy vs 22.4 mJy | not stated | mJy | 5 | the median flux for the close (15 to 140 AU) binaries is 4.7 mJy, while the median flux for the 140 to 4200 AU binaries is 22.4 mJy. |
| Class II detection fraction | 72% (151/211) | not stated | percent | 0 | All Class II      / 211   / 151           / $72\%$ |

## Qualitative findings

- No new circumbinary disks detected  
  > "Even at this sensitivity level, we have detected no new circumbinary disks" (3.1 Continuum emission)
- Close binaries show correlated Mdisk/Mstar between primary and secondary; wide binaries anticorrelated  
  > "In close ($< 140$ AU) binaries the values of $M_{\rm disk}/M_{\star}$ for the primary and secondary stars are correlated, but in wide binaries, they are anti-correlated." (Conclusion)

## Claim tuples

- H: Do stars in binaries have lower mm flux at a given stellar mass than singles? | E: linmix regression of flux vs stellar mass for singles and binary components | R: Intercepts 1.80 vs 1.26, slopes consistent | F: Binary components have lower flux at given stellar mass | **supported**
- H: Do primaries have brighter disks than secondaries beyond stellar mass effect? | E: compare Mdisk/Mstar distributions | R: p=0.60 for primaries vs secondaries | F: Primary-secondary difference is largely due to stellar mass | **supported**
- H: Does separation affect disk properties? | E: compare wide and close binaries to singles | R: wide binaries resemble singles; close binaries fainter | F: Close binaries have less massive disks but are mostly detected | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Censored-data statistics used to handle upper limits  
  > "using routines for censored data to account for the upper limits in millimeter flux." (4.3 Statistical Calculations)
- How they decided it was enough: _not stated_
- Limitation (authors): Possible undetected companions in single sample; limited disk size information for singles and wide binaries  
  > "While it is possible that there remain a small number of undetected companions in our single star sample" (4.2.1 Single star sample)
- Limitation (authors): CO exposure too short for statistical analysis  
  > "so we are unable to do any meaningful statistical analysis on the CO emission." (3.2 CO emission)
- Caveat (inferred, ours): Disk mass relies on fixed kappa, Td scaling and optically thin assumption; Td scaling for binaries uncertain
- Caveat (inferred, ours): Mixed beam sizes and a reprocessed non-QA-passed dataset
- Caveat (inferred, ours): Single-star sample completeness for companions depends on external limits
- Caveat (inferred, ours): Fixed 1 Myr age for all stars

## Reproducibility

- Data public (paper): ALMA projects acknowledged with ADS/JAO.ALMA codes  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00105.S and\ ADS/JAO.ALMA#2015.1.00392.S." (Conclusion)
- Products in archive: _not stated_
- Missing: clean parameters
- Missing: self-calibration details
- Missing: CASA version
- Missing: linmix priors
- Data volume (inferred): ~100-300 GB raw for two projects (45 systems)
- Score (inferred): 3/5, Data public and statistical analysis described, but imaging and calibration settings are largely unstated.
- Rediscovery candidate: yes, Data are public, tabulated fluxes and stellar properties given, and numeric statistics can be redone, though imaging details are missing.

## Links

- Method: (cite: and13) (disk mass conversion and regression procedure)
- Method: (cite: wd18) (stellar mass and luminosity approach)
- Companion: Paper 1 (cite: ake14) (Cycle 0 ALMA survey of Taurus binaries)
- Related: Harris et al. 2012 SMA Taurus multiples
- Related: Andrews et al. 2013 Taurus survey

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 49,
  "rate": 0.598
 },
 "evidence_ok": true
}
```
