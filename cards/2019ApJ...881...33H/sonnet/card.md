# Constraining the Radio Emission of TRAPPIST-1

`2019ApJ...881...33H` | The Astrophysical Journal 2019 | first author: Hughes, A. G. | arXiv: 1907.02112 | DOI: 10.3847/1538-4357/ab2be7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: exoplanets, stellar_physics
- Question: Does TRAPPIST-1 emit gyrosynchrotron radio emission at 44 and 97.5 GHz, and what do upper limits imply for magnetic properties and energetic proton flux at its planets?  
  > "The aim of these observations was to determine whether TRAPPIST-1 has comparable radio emission." (Introduction)
- Target **TRAPPIST-1**: coordinates RA = 23h 06m 29.37s, Dec = -05d 02' 29.03'' (J2000)  
  > "TRAPPIST-1 (or 2MASS J23062928-0502285) is a nearby M8 star located $12.45 \pm 0.02$ pc away from the Sun (cite: kane)." (Introduction); z/distance 12.45 ± 0.02 pc  
  > "TRAPPIST-1 (or 2MASS J23062928-0502285) is a nearby M8 star located $12.45 \pm 0.02$ pc away from the Sun (cite: kane)." (Introduction); distance from Kane 2018  
  > "TRAPPIST-1 (or 2MASS J23062928-0502285) is a nearby M8 star located $12.45 \pm 0.02$ pc away from the Sun (cite: kane)." (Introduction)

## Data provenance

- ALMA projects: 2017.1.00986.S
- bands: Band 3, 97.5 GHz  
  > "Observations were in Band 3 with a total bandwidth of 8 GHz split among 4 spectral windows (SPW)." (ALMA Observations)
- frequencies and spectral setup: 4 SPWs at 90.495, 92.432, 102.495, 104.495 GHz; 128 x 15.625 MHz channels each  
  > "The SPWs were centred at 90.495 GHz, 92.432 GHz, 102.495 GHz, and 104.495 GHz, giving an effective continuum frequency of 97.50 GHz." (ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 1397 m, 43 antennas  
  > "There were 43 antennas used with baselines ranging from 15 m to 1397 m." (ALMA Observations)
- angular resolution: 0.835 x 0.738 arcsec, PA -86.4 deg  
  > "The size of the resulting synthesized beam is $0.835  \times 0.738$ arcsec$^{2}$ at a position angle of $-86.4^{ \circ }$" (ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: 3.52 uJy/beam RMS  
  > "These ALMA 97.5 GHz observations achieve a RMS sensitivity of $3.52~ \upmu \textrm{Jy}~\textrm{beam}^{-1}$ as taken from the CLEANed image." (ALMA Observations)
- time on source: 6.41 hr on-source, 8.83 hr total, 8 EBs  
  > "taken in 8 executions blocks (EBs) from 2018 January 22 to 2018 January 28 for a total of 8.83 hr including overhead and 6.41 hr on-source" (ALMA Observations)
- observing dates: 2018 January 22 to 28  
  > "from 2018 January 22 to 2018 January 28" (ALMA Observations)
- pi or archival as stated: Cycle 5, PI Hughes  
  > "The ALMA Cycle 5 observations (ID 017.1.00986.S, PI Hughes)" (ALMA Observations)
- Other facility **VLA**: 44 GHz Q-band observations, D config, 7.20 hr on-source, 5.39 uJy/beam RMS; 3 sigma limit 16.2 uJy  
  > "These VLA 44.0 GHz observations achieve a RMS sensitivity of $5.39 ~ \upmu \textrm{Jy}~\textrm{beam}^{-1}$ as taken from the CLEANed image." (VLA Observations)
- External data: Stellar parameters (mass, radius, Teff, Prot, B field, Lx, age, distance)  
  > "Stellar Parameters of TRAPPIST-1 taken from the literature." (Table 1) [from van_groot, delrez, vida, rein_bas, wheatley, burg_mam, kane]
- External data: 6 GHz upper limit of <8.1 uJy for TRAPPIST-1  
  > "| $6$ | $< 8.1$ | $<1.5\times10^{12}$ | (cite: pineda) |" (Table 2) [from Pineda & Hallinan 2018 (cite: pineda)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "The data from both facilities were reduced using the the Common Astronomy Software Applications (CASA) pipeline (cite: casa_ref)" (Observations)
- casa version: CASA 4.7.2 (ALMA)  
  > "The data were reduced using CASA 4.7.2, which included WVR calibration" (ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: quasar J0006-0623 (flux and bandpass); phase calibrator J2301-0158  
  > "flux and bandpass calibration with quasar J0006-0623; and phase calibration with quasar J2301-0158" (ALMA Observations)
- flux scale uncertainty: _not stated_
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
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.835 x 0.738 arcsec, PA -86.4 deg  
  > "The size of the resulting synthesized beam is $0.835  \times 0.738$ arcsec$^{2}$ at a position angle of $-86.4^{ \circ }$" (ALMA Observations)
- final rms: 3.52 uJy/beam  
  > "RMS sensitivity of $3.52~ \upmu \textrm{Jy}~\textrm{beam}^{-1}$ as taken from the CLEANed image" (ALMA Observations)

### Inherited from earlier work

- Gyrosynchrotron size and electron density formulae follow White et al. 1989 and Osten et al. 2009; brightness temperature from Dulk 1985  
  > "First, following the framework of (cite: white) and (cite: osten2009), we can calculate the size of the emitting region" (Discussion) [from (cite: white); (cite: osten2009); (cite: dulk)]

### Not stated but needed to reproduce (our reading)

- tclean parameters (weighting, robust, cell, image size, deconvolver, threshold)
- How the 3-sigma limit was derived (3 x RMS at target position assumed)
- Whether ALMA archive/pipeline products were used as delivered; flux calibrator flux density and scale uncertainty
- Exact brightness temperature calculation and electron energy distribution details for Dulk equations
- Details of per-scan imaging and noise simulation

## Analysis recipe

1. **Image and derive upper limits**: CLEANed images from pipeline-calibrated data; 3 sigma upper limits from image RMS  
  > "achieve a RMS sensitivity of $3.52~ \upmu \textrm{Jy}~\textrm{beam}^{-1}$ as taken from the CLEANed image" (ALMA Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Confirmed phase centre at expected position including proper motion  
  > "We confirmed that the phase centre is at the expected location of TRAPPIST-1, taking into account proper motion." (Null detections of TRAPPIST-1)
2. **Search for variability per scan**: Analysed individual scans (~7 min ALMA, ~4 min VLA) for flares  
  > "we analyzed each observation’s infividual scans, which are $\sim 4$ minutes for the VLA observations and $\sim 7$ minutes for the ALMA data" (Null detections of TRAPPIST-1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Assess significance of NE source candidates**: 10^4 Gaussian noise images convolved with the beam; count peaks  
  > "The significance of this is tested by producing $10^4$ images of Gaussian noise and convolving those images with the synthesized beam." (Null detections of TRAPPIST-1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Constrain emitting region size and proton flux**: Gyrosynchrotron equations: region size x, electron density N, scaled to outgoing proton flux at TRAPPIST-1e  
  > "Following the gyrosynchrotron equations arranged by (cite: white) for an assumed electron energy index $\delta=2$, the number density of trapped electrons is given by" (Discussion)
   - parameter: B = 600 G, delta = 2, d = 12.45 pc, nu = 97.5 GHz, S = 10.6 uJy  
  > "the $3 \sigma$ flux $S = 10.6 ~\upmu \textrm{Jy}$, size of emitting region $R = 0.02 ~R_J$, magnetic field $B=600~ G$" (Discussion)
   - assumption: Electron-to-proton ratio ~10^3 as in solar flares; flux scaled by R/r^2 with pi sr  
  > "we scale the outgoing rate by $\frac{R}{r^2}$, where R is the size of the emitting region and r is the semi-major axis" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2 (ALMA); 5.1.2 (VLA): Calibration and imaging of ALMA and VLA data  
  > "The data were reduced using CASA 4.7.2" (ALMA Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 97.5 GHz 3 sigma upper limit | 10.6 | not stated | uJy | 1 | we place $3 \sigma$ upper flux limits of 10.6 and 16.2 $\upmu$Jy, respectively |
| VLA 44 GHz 3 sigma upper limit | 16.2 | not stated | uJy | 1 | we place $3 \sigma$ upper flux limits of 10.6 and 16.2 $\upmu$Jy, respectively |
| ALMA per-scan 3 sigma limit | 110 | not stated | uJy | 2 | median $3 \sigma$ upper limits of 110 $\mu$Jy and 190$\mu$Jy per scan for ALMA and the VLA |
| Emitting region size upper limit | <= 0.02 | not stated | R_J | 4 | the emitting region is constrained by our ALMA upper limits to $\leq 0.02~ R_J$ |
| Trapped electron density upper limit | <= 5e8 | not stated | cm^-3 | 4 | The resulting number density of electrons is $N \leq  5 \times 10^8~ cm^{-3}$. |
| Proton flux at TRAPPIST-1e | 1e5 | not stated | pfu | 4 | We find a particle flux incident on the closest habitable planet, TRAPPIST-1e (0.02 au), to be $10^5 pfu$. |

## Qualitative findings

- TRAPPIST-1 is consistent with slow-rotating, X-ray bright UCDs being radio dim  
  > "TRAPPIST-1 conforms to this trend." (Summary)

## Claim tuples

- H: TRAPPIST-1 emits gyrosynchrotron radiation comparable to TVLM 513-46546 | E: ALMA 97.5 GHz and VLA 44 GHz observations | R: No detection; 3 sigma limits 10.6 and 16.2 uJy vs expected 45 and 60 uJy | F: TRAPPIST-1 is radio dim at these frequencies | **supported**
- H: Energetic proton flux from TRAPPIST-1 could make planets uninhabitable | E: Gyrosynchrotron-based scaling of upper limits to proton flux | R: <=1e5 pfu at TRAPPIST-1e, well below 5.9e8 pfu catastrophic value | F: No evidence planets are overtly unsuitable due to proton fluxes | **partially**

## Reasoning

- Why this data: High frequencies probe gyrosynchrotron emission; on-source times chosen for S/N of 10  
  > "The on-source observation times were chosen in order to achieve a signal-to-noise ratio of 10 for each observation." (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Short observations may miss flares; emission mechanism cannot be inferred from non-detections  
  > "While we cannot infer an emission mechanism from only non-detections" (Discussion)
- Caveat (inferred, ours): Proton flux estimate rests on many assumptions (solar electron/proton ratio, R/r^2 scaling, B=600 G)
- Caveat (inferred, ours): Upper limit definition and imaging parameters not given
- Caveat (inferred, ours): Distance quoted as 12.45 vs 12.43 pc inconsistently

## Reproducibility

- Data public (paper): ALMA data from project 2017.1.00986.S acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00986.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Exact upper-limit and brightness temperature procedure
- Data volume (inferred): ~50-100 GB raw for 8 EBs
- Score (inferred): 6/5, Simple non-detection with stated sensitivities and public data, but imaging settings are missing.
- Rediscovery candidate: yes, Public data, simple numeric upper limits, and short recipe.

## Links

- Method: White, Kundu & Jackson 1989 (cite: white) (Gyrosynchrotron equations used)
- Companion: Pineda & Hallinan 2018 (cite: pineda) (6 GHz non-detection of TRAPPIST-1)

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
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 64,
  "stated": 33,
  "rate": 0.516
 },
 "evidence_ok": true
}
```
