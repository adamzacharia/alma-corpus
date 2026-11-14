# Detection of an Optical/UV Jet/Counterjet and Multiple Spectral Components in M84

`2018ApJ...860....9M` | The Astrophysical Journal 2018 | first author: Meyer, Eileen T. | arXiv: 1804.05122 | DOI: 10.3847/1538-4357/aabf39

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: What is the broad-band SED of the inner M84 jet (radio to X-ray), and what emission mechanisms explain its multiple spectral components?  
  > "we investigate the broad-band SED of M84 for the first time, and examine possible theoretical explanations for the unusual three-component SED, including hadronic models." (Introduction)
- Target **M84 jet (knots A-D)**: coordinates _not stated_; z/distance z=0.00339, D=18.5 Mpc (89 pc/arcsec)  
  > "$z$=0.00339, $D$=18.5 Mpc" (Introduction); "an angular distance scale of 89 pc/$''$ for M84" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.01170.S, 2013.1.00828.S
- bands: Band 3 and Band 6  
  > "the brightest knot in the jet (knot B) is detected in the band 3 and 6 imaging we present here." (2.4 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 3 nominal 0.06"; Band 6 nominal 0.34"  
  > "The nominal resolution and largest angular scale is 0.06$''$ and 0.55$''$, respectively." (2.4 ALMA); "The observations have nominal resolution and largest angular scale of 0.34$''$ and 1.74$''$, respectively." (2.4 ALMA)
- max recoverable scale: Band 3 0.55"; Band 6 1.74"  
  > "The nominal resolution and largest angular scale is 0.06$''$ and 0.55$''$, respectively." (2.4 ALMA)
- sensitivity: RMS 9 uJy (Band 3), 40 uJy (Band 6)  
  > "with an RMS of 9 $\mu$Jy and synthesized beam size of 0.06$''\times$0.05$''$." (2.4 ALMA); "with an RMS of 40 $\mu$Jy and synthesized beam size of 0.29$''\times$0.21$''$." (2.4 ALMA)
- time on source: Band 3 72 min; Band 6 49 min  
  > "The observation included 240 scans on M84 for a total time on source of 72 minutes." (2.4 ALMA); "The observation included 12 scans on M84 for a total time on source of 49 minutes." (2.4 ALMA)
- observing dates: _not stated_
- pi or archival as stated: Archival; M84 was a phase calibrator (B3) or one of the targets (B6) in other projects  
  > "We searched through the available ALMA archival data on M84" (2.4 ALMA)
- Other facility **HST**: Archival ACS/WFC3 optical/UV imaging (F850LP, F606W polarization, F475W, F336W, F225W)  
  > "We first noticed the jet in the far-UV (F225W) WFC3 imaging during an archival search for optical counterparts to resolved jets detected by *Chandra*." (2.1 Hubble Space Telescope)
- Other facility **VLA**: Archival L, C, X, Ku band imaging for SED, proper motions, jet/counterjet ratio  
  > "We analyzed archival high-resolution C- and X-band observations of M84 to best match the HST resolution for measuring individual knot fluxes." (2.2 Very Large Array)
- Other facility **Chandra**: Three archival ACIS-S observations (IDs 803, 5908, 6131), re-analyzed  
  > "We analyzed three archival *Chandra* observations of M84 taken with ACIS-S, having IDs 803, 5908, and 6131" (2.6 Chandra)
- Other facility **Fermi/LAT**: Gamma-ray upper limits in five bands  
  > "the upper limits in the five Fermi energy bands of 100 MeV-300 MeV, 300 MeV-1 GeV, 1 GeV-3 GeV, 3 GeV-10 GeV, and 10 GeV-100 GeV were computed" (2.7 Fermi/LAT Limits)
- External data: Black hole mass 8.5e8 Msun  
  > "$M_\mathrm{BH}=8.5^{+0.9}_{-0.8}\times 10^8M_\mathrm{\odot}$ (cite: walsh2010)" (Introduction) [from (cite: walsh2010)]
- External data: Previous Chandra jet fluxes for comparison  
  > "In (cite: harwood2012), the authors find a total jet flux of 2.08 nJy" (2.6 Chandra) [from (cite: harwood2012)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline for initial calibration, then self-calibration  
  > "We used the CASA pipeline version 4.5.1 to produce the initial calibrated measurement set" (2.4 ALMA)
- casa version: Pipeline 4.5.1 (B3), 4.3.1-REL (B6); self-cal and imaging CASA 4.7.1-REL (r39339)  
  > "while CASA version 4.7.1-REL (r39339) was used for self-calibration and imaging with `clean`." (2.4 ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~5% assumed flux calibration error  
  > "as the measured errors are smaller than the $\sim$5% error assumed for the flux calibration." (Table 2)
- self calibration: Several rounds of self-calibration  
  > "After several rounds of self-calibration the final imaged was produced" (2.4 ALMA)

### Imaging

- task: clean in CASA  
  > "while CASA version 4.7.1-REL (r39339) was used for self-calibration and imaging with `clean`." (2.4 ALMA)
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
- final beam: 0.06"x0.05" (B3); 0.29"x0.21" (B6)  
  > "with an RMS of 40 $\mu$Jy and synthesized beam size of 0.29$''\times$0.21$''$." (2.4 ALMA)
- final rms: 9 uJy (B3); 40 uJy (B6)  
  > "with an RMS of 9 $\mu$Jy and synthesized beam size of 0.06$''\times$0.05$''$." (2.4 ALMA)

### Inherited from earlier work

- HST multi-epoch alignment approach follows earlier 3C 273 work  
  > "This was accomplished using an approach very similar to that presented in (cite: meyer2015) to align multi-epoch HST imaging of 3C 273." (2.1 Hubble Space Telescope) [from (cite: meyer2015)]
- Numerical SED code taken from earlier work  
  > "Using the one-zone time-dependent numerical code of (cite: DMPR12), we computed the steady-state photon and particle spectra" (Two-component Synchrotron Model) [from (cite: DMPR12)]

### Not stated but needed to reproduce (our reading)

- ALMA weighting, robust, cell size, image size, clean masks and thresholds
- Self-calibration solution intervals and reference antenna
- Which calibrators and flux scale were used in the ALMA data
- How knot fluxes and upper limits were extracted (regions, aperture, limit definition)
- Whether primary-beam correction was applied
- Spectral windows used for continuum
- Fit procedure and goodness criteria for SED models (parameters tuned by hand)

## Analysis recipe

1. **Image ALMA Band 3 and 6 continuum**: Pipeline calibration, then self-calibration and clean imaging  
  > "After several rounds of self-calibration the final imaged was produced, with an RMS of 9 $\mu$Jy" (2.4 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: Core shows no turnover, ruling out flux scaling problem  
  > "The core shows no sign of a similar turnover, so we can rule out a problem with the flux scaling as the origin of this spectral feature." (3.1 The Unusual SED of M84 knots)
2. **Build knot SEDs from radio to X-ray**: Measure knot fluxes in VLA, ALMA, HST, Chandra; ALMA upper limits for undetected knots from same regions  
  > "The upper limits for the non-detected knots were calculated using the same region we used to measure the fluxes at other wavelengths." (3.1 The Unusual SED of M84 knots)
   - software: CASA, CIAO, sherpa
   - fitting: _not stated_
   - validation: _not stated_
3. **Model SED with two-component synchrotron and leptohadronic models**: One-zone time-dependent code; parameters searched starting from analytical estimates  
  > "We search for the best-fit parameter values by using as a starting point the rough estimates presented in the previous section." (Numerical modeling)
   - software: DMPR12 code
   - parameter: knot B: R=50 pc, B=1 mG, delta=1 (leptohadronic)  
  > "| $R$ \[pc\] | knot size | 50 |" (Table 3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.1 (ALMA imaging); pipeline 4.5.1/4.3.1: ALMA self-calibration and imaging  
  > "while CASA version 4.7.1-REL (r39339) was used for self-calibration and imaging with `clean`." (2.4 ALMA)
- **CIAO** 4.9: Chandra data reduction  
  > "The data were analyzed using CIAO version 4.9." (2.6 Chandra)
- **WISE** : VLA proper motions  
  > "we used the publicly available Wavelet Image Segmentation and Evaluation (WISE) code" (2.4 VLA Proper Motions with WISE)
- **AstroDrizzle** : Stacking HST images  
  > "we used the AstroDrizzle package to stack the two exposures into the final image" (2.1 Hubble Space Telescope)
- **galfit** : Galaxy modelling in F850LP  
  > "We thus modeled the galaxy in the initial F850LP drizzle image using `galfit`" (2.1 Hubble Space Telescope)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA Band 3 flux of knot B (97.5 GHz) | 1.03 | ~5% calibration | mJy | 2 | / $F_{\mathrm{B3}}$ / ALMA / 9.75$\times10^{10}$ / mJy / $<$0.95 / 1.03 / $<$0.95 / … / |
| ALMA Band 6 flux of knot B (236 GHz) | 0.30 | ~5% calibration | mJy | 2 | / $F_{\mathrm{B6}}$ / ALMA / 2.36$\times10^{11}$ / mJy / $<$0.4 / 0.30 / $<$0.66 / $<$0.53 / |
| Jet orientation angle | 74 | +9/-18 | degrees | 0 | yields an orientation angle for the system of 74$^{+9}_{-18}$$^\circ$ |
| Radio jet-to-counterjet ratio | 1.4 | 0.2 | dimensionless | 0 | We thus take the mean value of 1.4$\pm$0.2 as representative of the radio $R$ value. |

## Qualitative findings

- Radio spectrum of knots turns over at ~100 GHz, requiring a second component for optical/UV and a third for X-rays  
  > "the radio spectrum of all four knots in the jet turns over at approximately 100 GHz, which requires a second component for the bright optical/UV emission." (abstract)

## Claim tuples

- H: Does the M84 jet SED require multiple spectral components? | E: Combine VLA, ALMA, HST, Chandra knot fluxes | R: ALMA fluxes imply turnover near 100 GHz; X-rays flat relative to soft optical/UV | F: At least three spectral components | **supported**
- H: Can IC/CMB explain the emission? | E: Compare IC/CMB, equipartition, gamma-ray limits | R: Requires extreme departure from equipartition and unrealistic power | F: Inverse Compton models ruled out | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Star formation, IC/CMB, SSC and thermal bremsstrahlung rejected as origins  
  > "We rule out star formation as the origin of the optical/UV emission based on the low UV luminosity." (Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): Knot D lacks a Band 3 limit due to missing flux from limited largest angular scale  
  > "we do not report a band 3 upper limit because of the limit on the largest angular scale ($0.55''$) being smaller than the size of the knot" (3.1 The Unusual SED of M84 knots)
- Caveat (inferred, ours): Only knot B is detected by ALMA; the turnover for other knots relies on upper limits
- Caveat (inferred, ours): Model fits are by hand with no uncertainty estimates
- Caveat (inferred, ours): ALMA data were calibrator/other-purpose observations with possible flux-scale issues

## Reproducibility

- Data public (paper): All data archival  
  > "With archival VLA, ALMA, and *Chandra* imaging" (abstract)
- Products in archive: _not stated_
- Missing: Imaging parameters for ALMA
- Missing: Region definitions for flux extraction
- Missing: Model fitting procedure
- Data volume (inferred): ~50-100 GB for the two ALMA datasets (plus VLA, HST, Chandra)
- Score (inferred): 3/5, Public data and software named, but ALMA imaging and SED fit details are sparse.
- Rediscovery candidate: no, ALMA imaging recipe incomplete and modeling is not fully specified.

## Links

- Method: (cite: meyer2015) (HST alignment method)
- Method: (cite: mertens2015_wise) (WISE proper-motion code)
- Method: (cite: DMPR12) (leptohadronic SED code)
- Companion: (cite: harris2002) (earlier Chandra analysis of the M84 jet)
- Companion: (cite: breiding2017) (MSC jets with ALMA)

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 37,
  "rate": 0.536
 },
 "evidence_ok": true
}
```
