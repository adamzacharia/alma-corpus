# Science development study for the Atacama Large Aperture Submillimeter Telescope (AtLAST): Solar and stellar observations

`2024ORE.....4..140W` | Open Research Europe 2024 | first author: Wedemeyer, Sven | arXiv: 2403.00920 | DOI: 10.12688/openreseurope.17453.1

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: sun, stellar_physics, instrumentation
- Question: What solar and stellar science cases and technical requirements would a 50 m single-dish telescope (AtLAST) need to meet?  
  > "In this article, key science cases and observing strategies for solar observations with AtLAST are described." (Introduction)
- Target **Sun (chromosphere, flares, prominences, activity cycle)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00009.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- External data: ALMA Band 3 and 6 solar brightness temperatures from 3000 K to above 13 000 K  
  > "ALMA observations in Band 3 and 6 show a wide range of brightness temperatures from as low as 3000 K to above 13 000 K" (3.1.3 Sensitivity, integration time, dynamic range) [from (cite: 2022A&A...659A..31H)]
- External data: ALMA Band 3 science verification data indicating circular polarization degree of at least 1%  
  > "indicate that the circular polarization degree is at least 1% ." (3.1.4 Polarisation) [from (cite: 2024arXiv240106343S)]
- Simulation/model as data: Synthetic flare sub-mm/IR spectra from radiative-hydrodynamic modelling (Figure 2)  
  > "In Figure 2, we provide an example of the temporal evolution of a synthetic flare spectrum from RHD modelling." (2.2 Solar flares)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
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
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- The ALMA data are only used for illustrations; no processing details given
- Origin of RHD flare model parameters

## Analysis recipe


## Software

- **AtLAST sensitivity calculator** : Deriving integration times  
  > "The calculations used to derive integration times for this paper were done using the AtLAST sensitivity calculator" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| AtLAST angular resolution at 1.3 mm (230 GHz) | 6.5 | not stated | arcsec | 0 | the achievable angular resolution would be 6.5” at a wavelength of 1.3 mm |
| AtLAST angular resolution at 0.3 mm (950 GHz) | 1.5 | not stated | arcsec | 0 | down to just 1.5” at 0.3 mm ($\sim$950 GHz, ALMA Band 10) |
| Estimated full-disk scan time with AtLAST single beam | ~3 hours | not stated | hours | 0 | (on the order of ($(\frac{50\,\mathrm{m}}{12\,\mathrm{m}})^2 \approx 17$ times, i.e. $\sim$3 hours) |

## Qualitative findings

- Multi-pixel, multi-chroic continuum camera with fast on-the-fly scanning is the best approach for solar observations  
  > "Consequently, the best approach combines a multi-pixel detector with fast on-the-fly scanning." (4 Summary of telescope requirements)

## Claim tuples

- H: Can AtLAST provide capabilities for solar science that ALMA cannot? | E: Scaling arguments and requirement discussion | R: Wide simultaneous frequency coverage and large instantaneous FOV with multi-pixel detectors | F: AtLAST would enable 3D atmospheric mapping, flare detection and synoptic full-disk maps | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Instrument details remain open; spectral lines not yet known to be detectable on the Sun  
  > "While it has yet to be seen if spectral lines, mostly hydrogen recombination lines and potentially CO, can be detected at millimeter wavelengths" (3.1.2)
- Caveat (inferred, ours): Requirements are based on scaling estimates, not simulated AtLAST data
- Caveat (inferred, ours): ALMA data serve only as illustration

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: AtLAST sensitivity calculator on GitHub  
  > "available from [this link](https://github.com/ukatc/AtLAST_sensitivity_calculator)" (Software)
- Missing: No ALMA data analysis to reproduce
- Data volume (inferred): negligible
- Score (inferred): 1/5, White paper with no ALMA data analysis recipe.
- Rediscovery candidate: no, No ALMA data analysis; mostly scaling arguments.

## Links

- Companion: (cite: Mroczkowski2024) (AtLAST telescope concept design)
- Related: AtLAST
- Related: Solar ALMA Science Archive

## Checks

```json
{
 "quotes": 14,
 "quotes_ok": 14,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2011.0.00011.E"
 ],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 50,
  "stated": 8,
  "rate": 0.16
 },
 "evidence_ok": true
}
```
