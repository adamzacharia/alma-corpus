# SiO maser astrometry of the red transient V838 Monocerotis

`2020A&A...638A..17O` | Astronomy and Astrophysics 2020 | first author: Ortiz-León, Gisela N. | arXiv: 2004.01488 | DOI: 10.1051/0004-6361/202037712

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: stellar_physics, milky_way_ism
- Question: What is the trigonometric parallax, distance and proper motion of the red transient V838 Mon from VLBA SiO maser astrometry, and what does ALMA show of its surroundings?  
  > "In this paper, we report new VLBA observations of the 43 GHz SiO maser transitions toward V838 Mon. The phase-referencing technique was used to provide accurate astrometry." (Introduction)
- Target **V838 Mon**: coordinates ALMA continuum peak RA=07:04:04.821535, Dec=–03:50:50.629426 (ICRS)  
  > "Based on the geometry of the light echo seen in polarimetric images taken with the HST, (cite: Sparks2008) derived a distance of $6.1\pm0.6$ kpc." (Introduction); z/distance 5.9±0.4 kpc (this work, combined PDF)  
  > "Based on the geometry of the light echo seen in polarimetric images taken with the HST, (cite: Sparks2008) derived a distance of $6.1\pm0.6$ kpc." (Introduction); distance from VLBA parallax combined with Reid distance estimator, light echo and Gaia  
  > "Based on the geometry of the light echo seen in polarimetric images taken with the HST, (cite: Sparks2008) derived a distance of $6.1\pm0.6$ kpc." (Introduction)

## Data provenance

- ALMA projects: 2018.1.00336.S
- bands: Band 6  
  > "V838 Mon was observed by ALMA in band 6 with four spectral ranges: 215.56–217.44, 219.06–220.94, 230.11–231.99, and 232.06–233.94 GHz (PI: T. Kamiński)." (2.2 ALMA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: longest baseline 15.3 km  
  > "with the longest ALMA baselines of 15.3 km, which resulted in an angular resolution of 22 mas" (2.2 ALMA observations)
- angular resolution: 22 mas (Briggs, robust 0.5)  
  > "resulted in an angular resolution of 22 mas (when imaged with Briggs weighting and with the robust parameter of 0.5)" (2.2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 20 June 2019  
  > "The observations took place on 20 June 2019" (2.2 ALMA observations)
- pi or archival as stated: PI: T. Kamiński  
  > "(PI: T. Kamiński)" (2.2 ALMA observations)
- Line: SiO v=0, J=5-4 (217 GHz)
- Other facility **VLBA**: Multi-epoch 43 GHz SiO maser astrometry (7 epochs)  
  > "V838 Mon was observed with the VLBA for a total of 7 epochs between 2017 October and 2019 March" (2.1 VLBA observations)
- Other facility **Gaia DR2**: Parallax and proper motions for comparison  
  > "This star has a DR2 parallax of $-0.001\pm0.105$ mas." (Astrometry)
- External data: Light-echo distance 6.1±0.6 kpc used as a PDF in combination  
  > "(cite: Sparks2008) derived a distance of $6.1\pm0.6$ kpc." (Introduction) [from (cite: Sparks2008)]

## Processing

### Calibration

- pipeline or manual: Default observatory calibration scripts  
  > "Visibilities were calibrated with the default calibration scripts delivered by the observatory and were imaged in CASA (cite: casa)." (2.2 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "when imaged with Briggs weighting and with the robust parameter of 0.5" (2.2 ALMA observations)
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

### Not stated but needed to reproduce (our reading)

- CASA version
- ALMA continuum and line-free channel selection
- cell size, image size, masking, deconvolver
- continuum subtraction method
- moment-map velocity range
- final beam and rms of ALMA maps

## Analysis recipe

1. **Image ALMA continuum and SiO v=0 J=5-4**: Default-pipeline calibrated visibilities imaged in CASA; continuum and velocity-integrated SiO maps  
  > "Here, we present only maps of dust continuum emission and the SiO $v=0$, $J$=5–4 line in both of which the source is clearly resolved." (2.2 ALMA observations)
   - software: CASA
   - fitting: Gaussian fits for peak positions and size  
  > "Gaussian fits yield the continuum peak at RA=07:04:04.821535 ($\pm$0.17 mas)" (5.3 Extended emission detected with ALMA)
   - validation: _not stated_

## Software

- **CASA** : ALMA imaging  
  > "were imaged in CASA (cite: casa)" (2.2 ALMA observations)
- **AIPS** : VLBA calibration and imaging  
  > "Data calibration was performed using the Astronomical Imaging System (AIPS) (cite: Greisen2003)" (2.1 VLBA observations)
- **ParselTongue** : AIPS scripting interface  
  > "using a ParselTongue scripting interface (cite: Kettenis2006)" (2.1 VLBA observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SiO v=0 J=5-4 FWHM line width | 225 | not stated | km/s | 1 | which shows a very broad profile with a FWHM of 225 km s$^{-1}$ for the entire emission region |
| Beam-deconvolved SiO size | 148×125 | ±30 | mas | 1 | beam-deconvolved size of $148\times125~(\pm30)$ mas |
| SiO major axis position angle | 61 | ±7 | deg | 1 | at a position angle of $61\pm7^{\rm o}$ |
| 225 GHz continuum peak flux density | 0.43 | not stated | mJy/beam | 1 | The continuum has a peak flux density of 0.43 mJy beam$^{-1}$ |
| VLBA parallax | 0.166 | 0.060 | mas | 0 | \varpi & = & 0.166  \pm 0.060~{\rm mas} |
| Combined distance | 5.9 | 0.4 | kpc | 0 | while the combination of all PDFs yields $d=5.9\pm0.4$ kpc |

## Qualitative findings

- ALMA continuum is elongated roughly perpendicular to the extended SiO thermal emission; the strongest maser spot agrees within 2σ with the continuum and SiO peaks.  
  > "The position of the strongest SiO maser spot agrees within $2\sigma$ with the peaks of continuum and thermal SiO emission" (5.3 Extended emission detected with ALMA)

## Claim tuples

- H: V838 Mon distance can be improved by VLBA parallax | E: Multi-epoch VLBA phase-referenced astrometry combined with the distance estimator, light echo and Gaia | R: parallax 0.166±0.060 mas; d=5.9±0.4 kpc | F: V838 Mon lies beyond 5 kpc, favouring the Outer arm | **supported**
- H: ALMA reveals the structure of the merger ejecta | E: Map SiO v=0 J=5-4 and 225 GHz continuum | R: SiO outflow 148×125 mas, perpendicular to elongated continuum | F: Extended outflow with elongated, complex continuum | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA data are only briefly presented; a dedicated paper will give the full analysis.  
  > "The ALMA data will be presented and analyzed in depth in a dedicated paper." (2.2 ALMA observations)
- Caveat (inferred, ours): ALMA astrometric accuracy of about 3 mas limits comparison with maser positions
- Caveat (inferred, ours): ALMA processing details too sparse to reproduce maps

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA imaging parameters and line-free channels
- Missing: CASA version
- Data volume (inferred): ALMA Band 6 long-baseline dataset, likely tens to hundreds of GB
- Score (inferred): 2/5, ALMA is minor and its processing is sparsely described.
- Rediscovery candidate: no, ALMA recipe is incomplete; main numeric results come from VLBA.

## Links

- Companion: (cite: Kaminski2018) (SMA study of V838 Mon merger ejecta)
- Related: BeSSeL

## Checks

```json
{
 "quotes": 32,
 "quotes_ok": 32,
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
  "facts": 54,
  "stated": 21,
  "rate": 0.389
 },
 "evidence_ok": true
}
```
