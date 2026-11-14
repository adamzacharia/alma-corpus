# A compact jet at the infrared heart of the prototypical low-luminosity AGN in NGC 1052

`2019MNRAS.485.5377F` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Fernández-Ontiveros, J. A. | arXiv: 1903.05108 | DOI: 10.1093/mnras/stz716

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: What is the nature of the mid-IR nuclear continuum in the LLAGN NGC 1052: thermal torus dust or non-thermal emission from a compact jet?  
  > "The aim of this work is to probe the mid-IR brightness distribution in the nucleus of NGC 1052 using VLTI/MIDI observations and discriminate between the proposed scenarios for the origin of this emission." (Introduction)
- Target **NGC 1052**: coordinates _not stated_; z/distance z = 0.0045; D = 18 Mpc  
  > "a nearby E4 galaxy ($z = 0.0045$; $D = 18\, \rm{Mpc}$, $1\,\ensuremath{''} \sim 87\,\mbox{pc}$, (cite: 2003ApJ...583..712J))" (Introduction); distance from (cite: 2003ApJ...583..712J)  
  > "a nearby E4 galaxy ($z = 0.0045$; $D = 18\, \rm{Mpc}$, $1\,\ensuremath{''} \sim 87\,\mbox{pc}$, (cite: 2003ApJ...583..712J))" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00749.S
- bands: _not stated_
- frequencies and spectral setup: archival continuum in 419–478 GHz range (four continuum bands); also 108–353 GHz from Paper by Pasetto et al.  
  > "archival observations in the $419$–$478\, \rm{GHz}$ range where NGC 1052 was acquired as a calibrator" (2.4 Spectral Flux Distribution)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.12 arcsec synthesised beam; 0.12x0.10 arcsec at 478 GHz  
  > "The synthesised beam has a size of $\sim 0.12\ensuremath{''}$" (2.4 Spectral Flux Distribution)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival; NGC 1052 observed as a calibrator (PI R. Dominik)  
  > "NGC 1052 was acquired as a calibrator (programme: 2013.1.00749.S, PI: R. Dominik)" (2.4 Spectral Flux Distribution)
- Other facility **VLTI/MIDI**: N-band correlated fluxes at baselines up to ~130 m  
  > "Interferometric observations of NGC 1052 were obtained with VLTI/MIDI, a Michelson interferometer" (2.1 Mid-IR interferometry)
- Other facility **WHT/LIRIS and GTC/CanariCam**: Ks- and N-band imaging polarimetry  
  > "we acquired also *Ks*- and *N*-band imaging in polarised light" (Introduction)
- External data: ALMA fluxes in 108–353 GHz range  
  > "ALMA) measurements in the $108$–$353\, \rm{GHz}$ range recently published by (cite: 2019arXiv190102280P)" (2.4 Spectral Flux Distribution) [from (cite: 2019arXiv190102280P)]

## Processing

### Calibration

- pipeline or manual: archival data calibrated with CASA 4.7.2 and ALMA archive scripts  
  > "We calibrated the archival observations using CASA[^7] v4.7.2 and the scripts provided by the ALMA Observatory in the scientific archive." (2.4 Spectral Flux Distribution)
- casa version: CASA 4.7.2 (calibration); CASA 5.4.0 (imaging)  
  > "Four continuum bands were reconstructed using CASA v5.4.0" (2.4 Spectral Flux Distribution)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: briggs, robust = 0.5  
  > "with `briggs` weighting and a robust parameter of $0.5$ for the cleaning process" (2.4 Spectral Flux Distribution)
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

- ALMA band/EBs, dates and array configuration for 2013.1.00749.S
- cell size, image size, masking, niter/threshold, spectral window selection
- flux scale and flux calibrator
- fitting region and fit procedure details for 2D Gaussian

## Analysis recipe

1. **measure ALMA nuclear continuum flux**: image four continuum bands and fit 2D elliptical Gaussian to the nucleus  
  > "The nuclear flux was measured by fitting a 2D elliptical Gaussian profile to the nuclear source, which remain unresolved in all bands." (2.4 Spectral Flux Distribution)
   - software: CASA
   - parameter: briggs, robust 0.5  
  > "with `briggs` weighting and a robust parameter of $0.5$ for the cleaning process" (2.4 Spectral Flux Distribution)
   - fitting: _not stated_
   - validation: ALMA fluxes agree with large-aperture measurements  
  > "the ALMA fluxes included in Table [3](#sed_high) are in good agreement with large aperture measurements" (4.2 A compact jet)

## Software

- **CASA** 4.7.2 (calibration), 5.4.0 (imaging): calibrating and imaging archival ALMA data  
  > "We calibrated the archival observations using CASA[^7] v4.7.2" (2.4 Spectral Flux Distribution)
- **MIDI Interactive Analysis and Expert Work Station** : MIDI reduction  
  > "MIDI observations were processed and reduced using the *MIDI Interactive Analysis and Expert Work Station* software" (2.1 Mid-IR interferometry)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 478 GHz nuclear flux | 201 | 2 | mJy | 1 | $(201 \pm 2) \times 10^{-3}$ |
| ALMA 419 GHz nuclear flux | 283 | 1 | mJy | 1 | $(283 \pm 1) \times 10^{-3}$ |
| IR-to-UV power-law index | 2.58 | 0.02 | dimensionless | 0 | power-law continuum with an index of $\alpha = 2.58 \pm 0.02$ |

## Qualitative findings

- ALMA 478 GHz data show no extended structure indicating extended cold torus dust  
  > "do not show any extended structure in the millimetre/submillimetre range that could be indicative of extended cold dust emission from the torus" (4.2 A compact jet)

## Claim tuples

- H: Is the mid-IR nucleus of NGC 1052 thermal torus dust or a compact jet? | E: MIDI interferometry, IR polarimetry, SED including ALMA fluxes | R: nucleus unresolved <5 mas (0.5 pc); polarisation ~4%; steep IR-UV power law | F: compact jet favoured | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): ALMA role limited to SED points; non-simultaneous multi-epoch fluxes despite variability

## Reproducibility

- Data public (paper): ALMA data are archival  
  > "archival observations in the $419$–$478\, \rm{GHz}$ range" (2.4 Spectral Flux Distribution)
- Products in archive: _not stated_
- Missing: full ALMA imaging parameters
- Data volume (inferred): small (~ few GB)
- Score (inferred): 3/5, ALMA part is small and sparsely described, but data are public
- Rediscovery candidate: no, ALMA recipe incomplete; main results rely on non-ALMA data

## Links

- Companion: (cite: 2019arXiv190102280P) (ALMA/VLA fluxes 108–353 GHz used)
- Related: MIDI AGN Large Programme

## Checks

```json
{
 "quotes": 25,
 "quotes_ok": 25,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00034.S",
  "2013.1.00055.S",
  "2013.1.00221.S",
  "2013.1.01151.S",
  "2013.1.01225.S",
  "2015.1.00591.S",
  "2015.1.00989.S",
  "2016.1.00232.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 53,
  "stated": 19,
  "rate": 0.358
 },
 "evidence_ok": true
}
```
