# A candidate circumbinary Keplerian disk in G35.20-0.74 N: A study with ALMA

`2013A&A...552L..10S` | Astronomy and Astrophysics 2013 | first author: Sánchez-Monge, Á. | arXiv: 1303.4242 | DOI: 10.1051/0004-6361/201321134

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Do ALMA Cycle 0 350 GHz observations of the high-mass star-forming region G35.20-0.74 N reveal a Keplerian disk around the YSO(s) in core B, and what is the stellar content?  
  > "we consider the alternative possibility that the velocity gradient is tracing a disk." (3 The nature of core B: A Keplerian rotating disk?)
- Target **G35.20-0.74 N**: coordinates not stated (fitted center of core B: 18h58m13.027s, +01d40m35.94s)  
  > "G35.20–0.74 N is a well known star forming region located at a distance of $2.19_{-0.20}^{+0.24}$ kpc (Zhang et al. (cite: zhang2009))" (1 Introduction); z/distance 2.19 (+0.24/-0.20) kpc  
  > "G35.20–0.74 N is a well known star forming region located at a distance of $2.19_{-0.20}^{+0.24}$ kpc (Zhang et al. (cite: zhang2009))" (1 Introduction); distance from Zhang et al. 2009  
  > "G35.20–0.74 N is a well known star forming region located at a distance of $2.19_{-0.20}^{+0.24}$ kpc (Zhang et al. (cite: zhang2009))" (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00275.S
- bands: 350 GHz (Cycle 0)  
  > "G35.20–0.74 N was observed with ALMA Cycle 0 at 350 GHz in May and June 2012" (2 Observations and results)
- frequencies and spectral setup: 4 spectral windows of 1875 MHz, 3840 channels each, covering 334.85–338.85 and 346.85–350.85 GHz; ~0.4 km/s resolution  
  > "covering the ranges 334.85–338.85 GHz and 346.85–350.85 GHz), providing a resolution of $\sim$0.4 km s$^{-1}$" (2 Observations and results)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 36–400 m  
  > "with baselines in the range 36–400 m, providing sensitivity to structures $\le$2 $''$" (2 Observations and results)
- angular resolution: 0.51'' x 0.46'', PA=48 deg  
  > "The synthesized beam is $0.51\ensuremath{''}\times0.46\ensuremath{''}$, P.A.=48$^\circ$." (2 Observations and results)
- max recoverable scale: _not stated_
- sensitivity: ~6 mJy/beam per line channel; ~1.8 mJy/beam continuum  
  > "The rms noise is $\sim$6 mJy beam$^{-1}$ for individual line channels, while in the continuum image it is $\sim$1.8 mJy beam$^{-1}$" (2 Observations and results)
- time on source: _not stated_
- observing dates: May and June 2012  
  > "observed with ALMA Cycle 0 at 350 GHz in May and June 2012" (2 Observations and results)
- pi or archival as stated: _not stated_
- Line: CH3CN 19–18, K=2,3,4 (not stated)
- Line: CH3OH 7(1,6)–6(1,5) vt=1; 14(1,13)–14(0,14) (not stated)
- Line: HC3N 37–36 (not stated)
- Other facility **Spitzer/IRAC (GLIMPSE)**: 4.5 micron enhanced-resolution image for overlay  
  > "overlaid on an enhanced resolution Spitzer/IRAC image at 4.5 $\mu$m extracted from the GLIMPSE survey" (2 Observations and results)
- External data: Free-free continuum fluxes of core B at 6 and 3.6 cm (and 0.5 mJy at 3.6 cm)  
  > "Extrapolation of the 3.6 cm flux density (0.5 mJy) to 1.3 cm gives $>$1.9 mJy" (4 The stellar content of core B: A binary system?) [from Gibb et al. 2003 (GHLW); Codella et al. 2010]
- External data: Dust absorption coefficient 0.5 cm2/g (nu/230.6 GHz)  
  > "Assuming a dust absorption coefficient 0.5 cm$^2$ g$^{-1}~(\nu/230.6~{\rm GHz})$ (Kramer et al. (cite: kramer2003))" (3 The nature of core B: A Keplerian rotating disk?) [from Kramer et al. 2003]
- External data: Luminosity ~3e4 Lsun from RMS database  
  > "Estimate taken from the RMS database" (1 Introduction) [from RMS database]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune (flux), J1751+096 (gain, bandpass)  
  > "Flux, gain, and bandpass calibrations were obtained through observations of Neptune and J1751$+$096." (2 Observations and results)
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
- continuum subtraction: Continuum from line-free channels, subtracted from data  
  > "A continuum map was obtained from line-free channels and subtracted from the data." (2 Observations and results)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.51'' x 0.46'', PA 48 deg  
  > "The synthesized beam is $0.51\ensuremath{''}\times0.46\ensuremath{''}$, P.A.=48$^\circ$." (2 Observations and results)
- final rms: ~6 mJy/beam line; ~1.8 mJy/beam continuum  
  > "The rms noise is $\sim$6 mJy beam$^{-1}$ for individual line channels" (2 Observations and results)

### Not stated but needed to reproduce (our reading)

- CASA version and calibration procedure
- Weighting/robust, cell and image size, deconvolver
- Line-free channels used for continuum
- Parameter ranges and minimization algorithm for the Keplerian fit
- Peak selection criteria in each channel and uncertainty derivation
- Rest frequencies and moment-map velocity range

## Analysis recipe

1. **Image continuum and line cubes**: Calibrate and image in CASA; continuum from line-free channels subtracted  
  > "The data were calibrated and imaged using CASA." (2 Observations and results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Map velocity field**: First moment of CH3CN(19-18) K=2 line  
  > "computing the first moment of a CH$_3$CN line" (2 Observations and results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive per-channel emission peaks**: 2-D Gaussian fit of emission in each 0.4 km/s channel  
  > "we fitted the CH$_3$CN emission in each 0.4 km s$^{-1}$ velocity channel with a 2-D Gaussian." (3 The nature of core B: A Keplerian rotating disk?)
   - fitting: _not stated_
   - validation: Same pattern seen in several lines and species  
  > "All of these lines reveal a kinematical pattern very similar to that in Fig. [4](#fkepfit)a" (3 The nature of core B: A Keplerian rotating disk?)
4. **Fit Keplerian rotation**: Purely kinematical Keplerian model about a point source fitted to peak velocities  
  > "we have fitted the observed velocity pattern assuming Keplerian rotation about a point-like source." (3 The nature of core B: A Keplerian rotating disk?)
   - parameter: Free: Vsys, M*, x0, y0, inclination, position angle  
  > "the LSR velocity of the system ($V_{\rm sys}$), the central point mass ($M_\ast$) and its position ($x_0$,$y_0$)" (3 The nature of core B: A Keplerian rotating disk?)
   - fitting: Least squares: minimize sum of (Vobs - Vmodel)^2 over peaks  
  > "minimizing the expression" (3 The nature of core B: A Keplerian rotating disk?)
   - validation: Comparison of model velocity map with observed peaks; no uniqueness test  
  > "no attempt is made to demonstrate the uniqueness of the model proposed" (3 The nature of core B: A Keplerian rotating disk?)
5. **Estimate core B mass**: Mass from 350 GHz continuum flux of 0.32 Jy  
  > "The integrated flux density from core B at 350 GHz is 0.32 Jy." (3 The nature of core B: A Keplerian rotating disk?)
   - assumption: kappa=0.5 cm2/g (nu/230.6 GHz), gas-to-dust 100, Td=100 K, d=2.19 kpc  
  > "a gas-to-dust mass ratio of 100, we obtain $\sim$3 $M_\odot$ for a dust temperature of 100 K" (3 The nature of core B: A Keplerian rotating disk?)
   - fitting: _not stated_
   - validation: Compared with central mass for Keplerian condition  
  > "we believe that the mass of core B is significantly less than the central mass ($\sim$18 $M_\odot$), which satisfies the condition for Keplerian rotation." (The nature of core B: A Keplerian rotating disk?)

## Software

- **CASA** : calibration and imaging  
  > "The data were calibrated and imaged using CASA." (2 Observations and results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Vsys | 30.0 | 0.3 | km/s | 4 | $V_{\rm sys}$=30.0$\pm$0.3 km s$^{-1}$ |
| Central mass M* | 18 | 3 | Msun | 4 | $M_\ast$=18$\pm$3 $M_\odot$ |
| Inclination | 19 | 1 | deg | 4 | $\theta$=19$\pm$1$^\circ$ |
| Position angle | 157 | 4 | deg | 4 | $\psi$=157$\pm$4$^\circ$ |
| Disk radius lower limit | 2500 | not stated | AU | 4 | A lower limit for the disk radius is $R_{\rm disk}\simeq2500$ AU |
| Core B flux density at 350 GHz | 0.32 | not stated | Jy | 5 | The integrated flux density from core B at 350 GHz is 0.32 Jy. |
| Core B mass | ~3 | not stated | Msun | 5 | we obtain $\sim$3 $M_\odot$ for a dust temperature of 100 K |

## Qualitative findings

- At least 5 cores in a chain, supporting a fragmented structure rather than a smooth disk/toroid  
  > "Along the elongated structure a chain of at least 5 cores is seen" (2 Observations and results)

## Claim tuples

- H: Does core B host a Keplerian disk rather than an outflow base? | E: Per-channel Gaussian peaks of CH3CN and other lines fitted with a Keplerian point-mass model | R: M*=18±3 Msun, inclination 19°, PA 157°, R>=2500 AU; core mass ~3 Msun | F: Candidate Keplerian disk in core B | **supported**
- H: Is core B a binary? | E: Compare 18 Msun mass with the bolometric luminosity and Lyman continuum | R: A single 18 Msun star would dominate the luminosity; a binary lowers it | F: Possibly an HII region ionized by a binary at the disk center | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Bipolar outflow root rejected because velocity gradient orientation differs from the radio jet on the same scale  
  > "the orientation of the CH$_3$CN velocity gradient differs from that of the radio jet *on the same scale*" (3 The nature of core B: A Keplerian rotating disk?)
- How they decided it was enough: _not stated_
- Limitation (authors): Kinematic fit only, uniqueness not demonstrated  
  > "no attempt is made to demonstrate the uniqueness of the model proposed" (3 The nature of core B: A Keplerian rotating disk?)
- Caveat (inferred, ours): Gradient could be infall/outflow rather than Keplerian; no intensity modeling
- Caveat (inferred, ours): Fit uncertainties are not described; peak selection ad hoc
- Caveat (inferred, ours): Mass estimate depends on assumed opacity and 100 K
- Caveat (inferred, ours): Binary hypothesis is speculative

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Fit code and parameter ranges
- Missing: CASA version and imaging parameters
- Data volume (inferred): ~50-150 GB raw Cycle 0 data
- Score (inferred): 3/5, Public data and simple method, but imaging and fit details are missing.
- Rediscovery candidate: no, Imaging and fitting details are insufficient for a faithful redo.

## Links

- Companion: Gibb et al. 2003 (GHLW) (Earlier millimeter study of the same region)
- Companion: Ilee et al. 2013 (CO bandhead Keplerian disk fit giving 17.7 Msun)
- Related: GLIMPSE
- Related: RMS survey

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
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
  "facts": 68,
  "stated": 33,
  "rate": 0.485
 },
 "evidence_ok": true
}
```
