# ALMA and Herschel observations of the prototype dusty and polluted white dwarf G29-38

`2014MNRAS.444.1821F` | Monthly Notices of the Royal Astronomical Society 2014 | first author: Farihi, J. | arXiv: 1407.7976 | DOI: 10.1093/mnras/stu1545

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: stellar_physics, debris_disks, exoplanets
- Question: Is there an outlying, cold parent planetesimal population at 1-100 AU around the dusty, polluted white dwarf G29-38 that can be detected with ALMA and Herschel?  
  > "These long wavelength programs attempted to detect an outlying, parent population of bodies at $1-100$ AU, from which originates the disrupted planetesimal debris" (abstract)
- Target **G29-38 (ZZ Psc, WD 2326+049)**: coordinates _not stated_; z/distance 13.6 pc  
  > "At 13.6 pc, G29-38 is the nearest example of a disk-polluted white dwarf and also the brightest by an order of magnitude" (INTRODUCTION); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00851.S
- bands: Band 6 (230 GHz, 1305 um) and Band 7 (345 GHz, 870 um)  
  > "two 17 min observations on 18 and 26 November in band 6 (230 GHz, 1305 $\mu$m), and five 23 minutes observations on 6, 14, and 16 November in band 7 (345 GHz, 870 $\mu$m)" (2 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 10 to 150 m  
  > "The spatial configuration of the array provided baselines covering a range from 10 to 150 m." (2 ALMA)
- angular resolution: Band 7 beam 1.5" x 1.8", PA 1.63 deg  
  > "overplotted with the band 7 beam size ($1.5\ensuremath{''}\times1.8\ensuremath{''}$ at position angle 1.63$^\circ$)" (2 ALMA)
- max recoverable scale: _not stated_
- sensitivity: RMS 0.071 mJy/beam (band 6), 0.056 mJy/beam (band 7)  
  > "the achieved RMS values were 0.071 mJy/beam in band 6 and 0.056 mJy/beam in band 7" (2 ALMA)
- time on source: Band 6: two 17 min observations; Band 7: five 23 min observations  
  > "two 17 min observations on 18 and 26 November in band 6" (2 ALMA)
- observing dates: 2011 November (Cycle 0 Early Science)  
  > "as part of Early Science operations at the beginning of Cycle 0 in 2011 November" (2 ALMA)
- pi or archival as stated: _not stated_
- Other facility **Herschel PACS**: 100 and 160 um photometry upper limits  
  > "G29-38 was targeted by the *Herschel Space Observatory* on 2012 June 6 with the Photodetector Array Camera and Spectrometer" (2 Herschel)
- External data: Dusty A-star debris disk model parameters from Su et al. 2006, extrapolated to white dwarf  
  > "plotted model extrapolations for dusty A-type stars from (cite: su06)" (3.2 Projections of Dusty A-type Stars) [from (cite: su06)]
- External data: Dust opacity kappa=1.7 cm2/g at 870 um (range 0.2-4.0)  
  > "$\kappa=1.7$ cm$^2$ g$^{-1}$ at 870 $\mu$m, noting that the actual opacity may be anywhere in the range $0.2-4.0$ cm$^2$ g$^{-1}$ (cite: dra06)" (3.3 Dust Mass Limits) [from (cite: dra06)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "The data were processed by the ALMA pipeline" (2 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune (absolute flux)  
  > "Neptune was used for absolute flux calibration" (2 ALMA)
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
- array combination: Band 6 and 7 combined image made with CASA  
  > "Using the Common Astronomy Software Applications package, a band 6 and 7, beam-combined image was created" (2 ALMA)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Fractional luminosity limits computed following Wyatt (2008) formalism  
  > "Following (cite: wya08), all the available infrared and submillimeter upper limit $F_{\nu}$ at G29-38 were transformed into limiting fractional disk luminosities" (3.1 Sensitivity to Dust Emission) [from (cite: wya08)]
- Fractional luminosity evolution of grains following Bonsor & Wyatt 2010  
  > "Following (cite: bon10), considering the realistic emission properties of small grains illuminated by the faint white dwarf" (3.2 Projections of Dusty A-type Stars) [from (cite: bon10)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- Imaging parameters (weighting, cell, image size, cleaning) for ALMA images
- Combination method for band 6 and 7 data and spectral index assumed
- Dust temperature-radius relation details (grain properties, X_lambda)
- Stellar parameters used for the temperature calculation

## Analysis recipe

1. **Reduce Herschel PACS data and measure aperture photometry**: Standard PACS photometer processing in HIPE, photProject maps, high-pass filtering, point-source aperture photometry; upper limit = flux + 3 sigma  
  > "The derived upper limits for G29-38 are the flux measured in the source apertures $+3\sigma$" (2 Herschel)
   - software: HIPE
   - parameter: Aperture radii 5" and 8"; filter widths 66" and 102"; aperture corrections 1.94 and 1.90  
  > "aperture corrections applied; 1.94 and 1.90 for the 100 and 160 $\mu$m bands respectively" (2 Herschel)
   - assumption: Source assumed point-like  
  > "The source was assumed to be point-like and photometry was performed using apertures." (2 Herschel)
   - fitting: _not stated_
   - validation: _not stated_
2. **ALMA upper limits**: Pipeline-processed images; RMS adopted as 1 sigma, 3 sigma upper limits; combined band 6+7 image  
  > "upper limits for unresolved emission from the science target were taken to be $3\sigma$" (2 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Convert limits to fractional dust luminosity vs radius**: f = 3.4e9 F_nu d^2 X_lambda / (r^2 B_nu(lambda,T)); ALMA limits divided by number of beams per ring circumference when resolved  
  > "The plotted ALMA sensitivities were corrected for such resolved cases by assuming a face on disk and dividing by the number of beams per ring circumference." (3.1 Sensitivity to Dust Emission)
   - assumption: Blackbody grains, face-on disk, distance 13.6 pc  
  > "by assuming a face on disk" (3.1 Sensitivity to Dust Emission)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive dust mass limits**: m(T)=F_nu d^2/(kappa B_nu(T)) using 870 um limit of 0.17 mJy/beam, ring radii up to 60 AU  
  > "the adopted upper limit flux of $F_\nu=0.17$ mJy/beam is converted to the dust mass using" (3.3 Dust Mass Limits)
   - parameter: kappa = 1.7 cm2/g at 870 um  
  > "the average value of dust opacity is adopted here, $\kappa=1.7$ cm$^2$ g$^{-1}$ at 870 $\mu$m" (3.3 Dust Mass Limits)
   - assumption: Optically thin, circular face-on thin ring  
  > "the calculations assume a simple, circular, and face-on ring of radial thickness much less than the beam size" (3.3 Dust Mass Limits)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Beam-combined band 6 and 7 image  
  > "Using the Common Astronomy Software Applications package, a band 6 and 7, beam-combined image was created" (2 ALMA)
- **HIPE** 7.0: Herschel PACS data reduction  
  > "The PACS data were reduced using the *Herschel* Interactive Processing Environment (HIPE) version 7.0." (2 Herschel)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 3 sigma upper limit, 870 um | 0.17 | not stated | mJy | 2 | ALMA /         870         / $<$ 0.17 |
| ALMA 3 sigma upper limit, 1305 um | 0.21 | not stated | mJy | 2 | ALMA /        1305         / $<$ 0.21 |
| PACS 100 um upper limit | 1.6 | not stated | mJy | 1 | PACS    /         100         /  $<$ 1.6 |
| PACS 160 um upper limit | 4.4 | not stated | mJy | 1 | PACS    /         160         /  $<$ 4.4 |
| Detectable fractional luminosity limit | ~1e-4 | not stated | dimensionless | 3 | No associated emission sources were detected in any of the data down to $L_{\rm IR}/L_*\sim10^{-4}$ |
| Cold dust mass ruled out | > 1e24-1e25 | not stated | g | 4 | generally ruling out cold dust masses greater than $10^{24}-10^{25}$ g |

## Qualitative findings

- Several projected A-star debris disks would have been detectable with ALMA but not Herschel or Spitzer, suggesting such disks are depleted by the white dwarf phase.  
  > "several of the brightest A-star debris disk projections were readily detectable in the ALMA (but not *Herschel* or *Spitzer*) observations" (3.2 Projections of Dusty A-type Stars)

## Claim tuples

- H: Cold outer planetesimal belts around G29-38 are detectable with Herschel/ALMA | E: Herschel PACS 100/160 um and ALMA Band 6/7 continuum observations | R: No detections; L_IR/L* < ~1e-4 | F: No bright cold disk; consistent with collisional depletion models | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Early, shallow ALMA data with limited antennas; projections assume no further collisional evolution  
  > "ALMA in early and relatively shallow observations at 870 and 1305 $\mu$m" (OUTLOOK)
- Caveat (inferred, ours): Dust mass limits depend strongly on assumed opacity and ring geometry
- Caveat (inferred, ours): Imaging details not given

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA/pipeline versions
- Missing: imaging parameters
- Missing: temperature-radius relation details
- Data volume (inferred): ~ few GB (Cycle 0 continuum TDM)
- Score (inferred): 3/5, Simple non-detection analysis with formulas but sparse processing details.
- Rediscovery candidate: no, Main results are upper limits and imaging settings are not stated.

## Links

- Method: (cite: wya08) (Fractional luminosity formalism)

## Checks

```json
{
 "quotes": 38,
 "quotes_ok": 38,
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
  "facts": 69,
  "stated": 29,
  "rate": 0.42
 },
 "evidence_ok": true
}
```
