# The Faraday Rotation Measure of the M87 Jet at 3.5 mm with ALMA

`2024ApJ...975..103P` | The Astrophysical Journal 2024 | first author: Peng, Sijia | arXiv: 2409.12028 | DOI: 10.3847/1538-4357/ad7c41

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars
- Question: What is the Faraday rotation measure of the M87 core and jet at 3.5 mm, and what does it imply about the origin of the Faraday screen and the magnetic field structure of the jet?  
  > "We present a Faraday rotation measure image of the M87 jet between 85.2 GHz and 101.3 GHz with a resolution of $\sim 2\ensuremath{''}$ with the Atacama Large Millimeter/submillimeter Array (ALMA)." (abstract)
- Target **M87 (core and jet)**: coordinates Core: 12h30m49.423s +12d23m28.05s  
  > "| Core     | 12h30m49.423s | +12d23m28.05s |" (Table 1); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00842.V
- bands: Band 3 (3.5 mm)  
  > "with 32 antennas of 12 meter diameter at Band 3 using the C43-3 configuration." (2 Observation and data reduction)
- frequencies and spectral setup: four full-polarization SPWs centered at 86.3, 88.3, 98.3, 100.3 GHz, 1.875 GHz each  
  > "four full-polarization subbands (spectral windows, SPWs) centered at 86.3, 88.3, 98.3, and 100.3 GHz with a bandwidth of 1.875 GHz each" (2 Observation and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-3  
  > "using the C43-3 configuration" (2 Observation and data reduction)
- baselines: 15 m to 500 m  
  > "The maximum baseline length is 500 m and the minimum length is 15 m." (2 Observation and data reduction)
- angular resolution: ~2 arcsec; SPW0 beam 2.9" x 2.3"  
  > "synthesized beams of $\rm 2.9\ensuremath{''} \times 2.3\ensuremath{''}$" (2 Observation and data reduction)
- max recoverable scale: _not stated_
- sensitivity: Stokes I rms 2.5, 2.2, 2.0, 2.0 mJy/beam; polarized rms 2.0, 2.0, 1.5, 1.5 mJy/beam  
  > "The subband images in Stokes I have rms noise levels of 2.5, 2.2, 2.0, and 2.0 $\rm mJy\ beam^{-1}$" (2 Observation and data reduction)
- time on source: about 1.5 hours on M87 (8.0 hours total)  
  > "The observation lasted about 8.0 hours and the total on-source time for M87 was about 1.5 hours." (2 Observation and data reduction)
- observing dates: April 14-15, 2018  
  > "were performed on April 14–15, 2018" (2 Observation and data reduction)
- pi or archival as stated: _not stated_
- External data: Previous VLA RM ranges (4-18 GHz: |RM| 0-250 rad/m2; 8-43 GHz: 0-500 rad/m2) used in RM-frequency fit  
  > "We adopt the range $\rm |RM| = (0-250)\ rad\ m^{-2}$ (with a median of 150 $\rm rad\ m^{-2}$) in the frequency range $4 -18$ GHz" (4.2 Faraday rotation measure of the jet on arc-second scales) [from (cite: 2021ApJ...923L...5P); (cite: 2016ApJ...823...86A)]
- External data: Previous ALMA 1.3 mm core RM measurements (2016-2018) compared in Fig. 5  
  > "Figure [5](#fig:sign) shows RM measurements by ALMA, including this work and (cite: 2019PASP..131g5003G; 2021ApJ...910L..14G) from 2016 to 2018" (4.1 Faraday rotation measure at the core) [from (cite: 2019PASP..131g5003G); (cite: 2021ApJ...910L..14G)]
- External data: Core shift between 86.3 and 100.3 GHz of (3±12) micro-arcsec  
  > "it is only $\rm (3\pm12)$ micro-arcseconds for M87 core from 86.3 to 100.3 GHz (cite: 2011Natur.477..185H)" (3 Results) [from (cite: 2011Natur.477..185H)]

## Processing

### Calibration

- pipeline or manual: CASA polarization calibration following Goddi et al. 2019 (gaincal XYf+QU, polcal for D-terms)  
  > "calibrated with Common Astronomy Software Applications[^1] (CASA, version: 5.4.0) following the calibration procedures described in (cite: 2019PASP..131g5003G)" (2 Observation and data reduction)
- casa version: CASA 5.4.0  
  > "(CASA, version: 5.4.0)" (2 Observation and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 3C279 polarization calibrator; 3C 273 and 3C 279 calibrators  
  > "3C 273 and 3C 279 were observed in interleaved scans as calibrators." (2 Observation and data reduction)
- flux scale uncertainty: 5% systematic absolute flux scale; 0.03% leakage I to Q/U  
  > "the calculation also incorporates a 5% systematic error caused by the absolute flux-scale calibration, and an additional 0.03% systematic error due to leakage from Stokes I to Stokes Q and U" (Observation and data reduction)
- self calibration: _not stated_

### Imaging

- task: tclean on all Stokes I,Q,U,V per subband  
  > "the CASA `TCLEAN` task was applied to all Stokes parameters (I, Q, U and V) data for each subband" (2 Observation and data reduction)
- deconvolver: nterms=2  
  > "we set `NTERMS=2`, `CELL= 0.2`$\ensuremath{''}$, and a Briggs weighting with `Robust=1`" (2 Observation and data reduction)
- weighting robust: Briggs, robust = 1  
  > "a Briggs weighting with `Robust=1`" (2 Observation and data reduction)
- uv taper: SPWs 1-3 tapered/restored to SPW0 beam 2.9"x2.3" at PA -4.5 deg for RM  
  > "we tapered the visibilities of SPWs 1-3 and restored image to match the lower resolution of SPW 0 that is $\rm 2.9\ensuremath{''} \times 2.3\ensuremath{''}$ at $\rm P.A.= -4.5\ensuremath{^\circ}$" (2 Observation and data reduction)
- cell size: 0.2"  
  > "`CELL= 0.2`$\ensuremath{''}$" (2 Observation and data reduction)
- image size: _not stated_
- masking: manual mask from core to extended inner lobes  
  > "a manual mask that covers the regions from the core to the extended inner lobes of M87" (2 Observation and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied  
  > "We applied a primary beam correction and a manual mask" (2 Observation and data reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Polarization calibration procedure  
  > "Here is a brief description of the polarization calibration procedures (cite: 2019PASP..131g5003G)." (2 Observation and data reduction) [from (cite: 2019PASP..131g5003G)]
- Error treatment: 5% flux scale and 0.03% leakage systematics added in quadrature  
  > "Following (cite: 2021ApJ...910L..14G), the calculation also incorporates a 5% systematic error caused by the absolute flux-scale calibration" (2 Observation and data reduction) [from (cite: 2021ApJ...910L..14G)]
- Phased-array mode observations as part of GMVA imaging experiment  
  > "The ALMA observations were performed in phased-array mode (cite: 2018PASP..130a5002M; 2023PASP..135b5002C) as part of a Global Millimeter VLBI Array (GMVA) imaging experiment (cite: 2023Natur.616..686L)." (2 Observation and data reduction) [from (cite: 2018PASP..130a5002M; 2023PASP..135b5002C; 2023Natur.616..686L)]

### Not stated but needed to reproduce (our reading)

- tclean niter, threshold, image size, spw/channel setup
- Which phased-array/ALMA products were used and how phasing affected calibration
- Details of the orthogonal distance regression (data points, weighting)
- Exact RMFIT settings (e.g. n pi ambiguity handling)
- Distance to M87 / physical scale conversion

## Analysis recipe

1. **Calibrate data including polarization**: Standard CASA calibration plus polarization calibration: gaincal XYf+QU on 3C279, polcal for D-terms  
  > "Finally, we solved for the instrumental polarization determining the leakage terms (or D-terms) for all antennas with the task `polcal`." (2 Observation and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: Calibrator checks show on- and off-axis leakage below 6 mJy/beam  
  > "both on-axis ($\rm \leq 20\ensuremath{''}$) and off-axis ($\rm 20\sim 60\ensuremath{''}$) polarization leakages are below the threshold of our polarization analysis" (2 Observation and data reduction)
2. **Image Stokes I,Q,U,V and make polarization images**: tclean per subband; immath POLI for polarized intensity, POLA for EVPA  
  > "To obtain the image of linear polarized intensity, the CASA task `IMMATH` was used with the `POLI` mode." (2 Observation and data reduction)
   - software: CASA
   - parameter: nterms=2, cell 0.2", robust=1  
  > "we set `NTERMS=2`, `CELL= 0.2`$\ensuremath{''}$, and a Briggs weighting with `Robust=1`" (2 Observation and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure core and knot polarization properties**: IMFIT with elliptical Gaussians; EVPA errors propagated plus systematics  
  > "We used the `IMFIT` task to measure the polarized properties of the M87 core and the jet knots assuming elliptical Gaussian components." (2 Observation and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive RM image**: Match SPW resolutions by taper/restoring beam, then RMFIT on the four SPW images with polarized threshold 6 mJy/beam (3 sigma); linear fit of EVPA vs lambda^2  
  > "we applied the `RMFIT` task to the individual SPW images to make a Faraday RM image and the associated error map with a polarized threshold of $\rm 6\ mJy\ beam^{-1}$" (2 Observation and data reduction)
   - software: CASA
   - parameter: polarized threshold 6 mJy/beam (3 x rms); no systematics in RMFIT  
  > "No systematic errors were included in `RMFIT`." (2 Observation and data reduction)
   - assumption: Single screen, chi = chi0 + RM lambda^2, same opacity at all wavelengths; linear fit due to limited frequency coverage  
  > "We can derive the RM by measuring the observed EVPA of the target at multiple wavelengths assuming that the opacity is the same at these wavelengths." (1 Introduction)
   - fitting: Linear fit of EVPA vs lambda^2  
  > "we adopted a linear fitting to estimate the RM for both the core and the sampled position in the jet knots" (3 Results)
   - validation: RM errors in core radially symmetric; core shift negligible  
  > "because the distribution of RM errors in the core is radially symmetric" (3 Results)
5. **Fit RM-frequency dependence for jet geometry**: Orthogonal distance regression of |RM| vs frequency from 4 to 101 GHz using literature and ALMA RM ranges, following Jorstad et al. |RM| ∝ nu^a  
  > "Using an orthogonal distance regression from 4 to 101 GHz, we obtain $\rm \alpha=2.3\pm0.4$ for the kpc-scale jet from the knot A to knot D." (4.2 Faraday rotation measure of the jet on arc-second scales)
   - parameter: ALMA RM range (1-2.5)e4 rad/m2  
  > "we use our ALMA result range $\rm RM = (1-2.5)\times 10^4\ rad\ m^{-2}$" (4.2 Faraday rotation measure of the jet on arc-second scales)
   - assumption: Helical field, at least mildly relativistic screen, power-law electron density gradient  
  > "Assuming a helical magnetic field, an at least mildly relativistic Faraday screen, and a power-law decreasing gradient in the electron density of the screen" (4.2 Faraday rotation measure of the jet on arc-second scales)
   - fitting: Orthogonal distance regression  
  > "Using an orthogonal distance regression from 4 to 101 GHz" (4.2 Faraday rotation measure of the jet on arc-second scales)
   - validation: _not stated_

## Software

- **CASA** 5.4.0: calibration, tclean imaging, immath, imfit, rmfit  
  > "(CASA, version: 5.4.0)" (2 Observation and data reduction)
- **APLpy** : plotting  
  > "APLpy (cite: 2012ascl.soft08017R), CASA (cite: 2022PASP..134k4501C)." (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Core RM at centroid | 4.5e4 | 0.4e4 | rad m^-2 | 4 | the rotation measure (RM) of the M87 core is $\rm (4.5\pm 0.4)\times10^{4}\ rad\ m^{-2}$ |
| Core fractional polarization | 0.88 | 0.08 | % | 3 | The lowest fractional polarization is found in the core at a level of only $\rm (0.88\pm 0.08)\%$. |
| Average core RM within 1" radius | 4.9e4 | 0.9e4 | rad m^-2 | 4 | is $\rm (4.9\pm0.9)\times10^{4}\ rad\ m^{-2}$ |
| RM at knot B centroid | -0.03e4 | 0.07e4 | rad m^-2 | 4 | $(-0.03\pm 0.07)\times10^4\rm~rad\ m^{-2}$ at the centroid of knot B |
| RM-frequency index alpha (knot A to D) | 2.3 | 0.4 | dimensionless | 5 | we obtain $\rm \alpha=2.3\pm0.4$ for the kpc-scale jet from the knot A to knot D |
| Peak polarized flux density at knot B | 36.7 | 1.8 | mJy/beam | 3 | with a peak flux density of $\rm 36.7\pm1.8 \ mJy\ beam^{-1}$ |
| Stokes I core peak | 1.407 | 0.006 | Jy/beam | 3 | a peak brightness of $\rm 1.407\pm0.006 \ Jy\ beam^{-1}$ |

## Qualitative findings

- RM sign reversals along and across the jet from knot D to B indicate helical magnetic field persisting to kpc scales  
  > "the RM gradient indicates a helical configuration of the magnetic field that persists up to kpc scale" (abstract)
- Core RM sign changed between 2016-2018 and within a week in April 2018 (3 mm positive to 1.3 mm negative)  
  > "The RM sign was found to reverse from negative (in 2016) to positive (in 2018)" (4.1 Faraday rotation measure at the core)

## Claim tuples

- H: Where does the core Faraday rotation originate? | E: Compare 3.5 mm core RM with 1.3 mm ALMA and cm VLBI RM measurements | R: Core RM 4.5e4 rad/m2, sign change within a week vs 1.3 mm | F: Faraday rotation occurs very close to the SMBH; internal screen or external screen with rapidly varying source | **partially**
- H: Is there a helical magnetic field in the kpc-scale jet? | E: Map RM across and along the jet knots D to B | R: RM gradients and sign reversals from about -2e4 to 3e4 rad/m2 | F: Consistent with helical field persisting to kpc scale | **supported**
- H: Does jet RM depend on frequency and what does it imply for jet shape? | E: ODR fit of |RM| vs frequency 4-101 GHz | R: alpha = 2.3±0.4 | F: Trumpet-like expanding jet shape | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): 1.3 mm and 3.5 mm emission may not arise from same location; limited resolution hinders HST-1 vs inner jet attribution  
  > "We caution that the 1.3 mm and 3.5 mm emissions may not arise from the same location" (4.1 Faraday rotation measure at the core)
- Caveat (inferred, ours): RM from only four SPWs with linear fit; possible n-pi ambiguity and opacity effects
- Caveat (inferred, ours): RM-frequency fit uses ranges from non-simultaneous, differently resolved datasets
- Caveat (inferred, ours): Polarization fidelity beyond inner 1/3 of primary beam relies on calibrator checks
- Caveat (inferred, ours): Comparison of RMs at different epochs with variable source

## Reproducibility

- Data public (paper): Data cited by project code 2017.1.00842.V; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00842.V." (Acknowledgments)
- Products in archive: _not stated_
- Missing: tclean niter/threshold/imsize
- Missing: Handling of phased-array data and calibration scripts
- Missing: Exact points used in ODR fit
- Data volume (inferred): ~100-200 GB raw
- Score (inferred): 3/5, Data and main CASA steps given with imaging parameters, but several imaging and fitting details are missing and the data are phased-array VLBI-linked.
- Rediscovery candidate: no, Project code is a VLBI-type (.V) dataset and phased-array calibration is nontrivial; some key details are missing.

## Links

- Method: (cite: 2019PASP..131g5003G) (ALMA polarization calibration procedure)
- Method: (cite: 2007AJ....134..799J) (RM-frequency dependence model)
- Companion: (cite: 2021ApJ...910L..14G) (1.3 mm ALMA polarization of M87)
- Companion: (cite: 2023Natur.616..686L) (GMVA imaging experiment this ALMA run was part of)
- Related: Global Millimeter VLBI Array (GMVA) imaging experiment

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
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
  "facts": 74,
  "stated": 47,
  "rate": 0.635
 },
 "evidence_ok": true
}
```
