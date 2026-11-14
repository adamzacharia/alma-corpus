# A flux-ratio anomaly in the CO spectral line emission from gravitationally lensed quasar MG J0414+0534

`2018MNRAS.481L..40S` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Stacey, H. R. | arXiv: 1808.05571 | DOI: 10.1093/mnrasl/sly153

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: Does the flux-ratio anomaly of lensed quasar MG J0414+0534 persist in sub-mm continuum and in CO (11-10) line emission, and is the candidate dusty dwarf galaxy (object Y) real?  
  > "Here, we re-analyse the ALMA observations of MG J0414+0534 to investigate the flux-ratio anomaly in the continuum and, for the first time, also in the molecular gas emission from a lensed quasar at mm-wavelengths." (Introduction)
- Target **MG J0414+0534**: coordinates _not stated_; z/distance z=2.64 (quasar); lens z=0.96  
  > "MG J0414+0534 is a radio-loud quasar at $z=2.64$ that is gravitationally-lensed into four images by a foreground galaxy at $z=0.96$." (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.01110.S
- bands: Band 7, central frequency 342 GHz  
  > "MG J0414+0534 was observed with ALMA at a central frequency of 342 GHz (Band 7) on 2015 June 13 and 2015 August 14" (2 Observations and data reduction)
- frequencies and spectral setup: four spectral windows centred on 335.0, 336.9, 347.0 and 349 GHz, 2 GHz bandwidth each, 128 channels per spw, 2 s integration  
  > "over four spectral windows centred on 335.0, 336.9, 347.0 and 349 GHz with 2 GHz bandwidth each." (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 12-m array; 35 antennas (epoch 1), 42 antennas (epoch 2)  
  > "In total, 35 antennas from the 12-m array were used, with baselines ranging from 21 to 687 m." (2 Observations and data reduction)
- configurations: _not stated_
- baselines: 21-687 m (first set); 15-1575 m (second)  
  > "Here, 42 antennas from the 12 m array were used with baselines between 15 and 1575 m." (2 Observations and data reduction)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: 19 uJy/beam rms in naturally weighted continuum image after self-cal  
  > "is $19~\upmu$Jy beam$^{-1}$, in comparison to the $65~\upmu$Jy beam$^{-1}$ from the analysis by (cite: Inoue:2017)" (3.1 Continuum)
- time on source: about 100 min (first set); about 50 min (second)  
  > "with a combined on-source integration time of about 100 mins" (2 Observations and data reduction)
- observing dates: 2015 June 13 and 2015 August 14  
  > "on 2015 June 13 and 2015 August 14" (2 Observations and data reduction)
- pi or archival as stated: archival data, PI Inoue  
  > "We present an analysis of archival observations" (abstract)
- Line: CO J=11-10 (1267.014 GHz)
- External data: Flux ratios at radio, mid-infrared and near-infrared wavelengths for comparison (Fig. 2)  
  > "The flux ratios from the radio to near-infrared are shown in Fig. [2](#fig:all_ratios)." (3.1 Continuum) [from not specified in the text (e.g. Minezaki:2009; Macleod:2013; Katz:1997)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline in CASA, modified to not flag edge channels; bad antenna flagged  
  > "we modified the pipeline to prevent flagging of the edge channels and allow a bandpass solution to be derived for the whole spectral window." (2 Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0238+166  
  > "The flux-density calibration was carried out using J0238+166" (2 Observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: Phase-only, several timescales starting from scan length down to 240 s; applied to line channels  
  > "Phase-only self-calibration over several time-scales, starting with each scan length, was used to progressively build the model for the source surface brightness distribution, down to a solution interval of 240 s." (2 Observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: super-uniform to natural weighting for self-cal model; natural for the Einstein ring image; super-uniform for compact components  
  > "With super-uniform weighting of the visibility data, we detect four compact components" (3.1 Continuum)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: model fit to line-free continuum, subtracted from visibilities  
  > "The spectral line data was prepared by fitting a model to the line-free continuum and subtracting this model from the visibilities." (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- Line-free channel ranges for continuum subtraction and order of the fit
- Robust or super-uniform weighting parameters, cell and image size, clean thresholds and masks
- Self-calibration solution intervals between scan length and 240 s and the initial model
- Channel width for line cube and moment-map settings
- Flux-ratio measurement velocity range is inconsistent between text (-350 to 0) and table (-300 to 0 km/s)
- UVMultiFit settings (positions fixed or free)

## Analysis recipe

1. **Calibrate and self-calibrate continuum**: ALMA pipeline, then phase-only self-calibration with iteratively built source model; apply solutions to line channels  
  > "The self-calibrated phase corrections that were derived for the continuum as a function of time were then applied to the spectral line channels." (2 Observations and data reduction)
   - software: CASA
   - parameter: shortest solution interval 240 s  
  > "down to a solution interval of 240 s" (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: Also tried initial model including object Y; calibration did not converge to a solution where Y remains  
  > "However, the calibration does not converge to a solution were object Y remains after the process." (3.1 Continuum)
2. **Measure image flux densities of continuum and CO(11-10)**: Fit delta-function models to each image in the visibility plane; continuum uses epoch 2 only; line uses channels -350 to 0 km/s  
  > "The flux densities of the compact components (continuum and spectral line) were measured by fitting models of delta functions to each image directly in the visibility plane using UVMultiFit" (2 Observations and data reduction)
   - software: UVMultiFit
   - assumption: Compact emission approximated by delta functions; Gaussians gave unstable results  
  > "the fitting did not produce stable results" (3.1 Continuum)
   - fitting: _not stated_
   - validation: _not stated_
3. **Characterise CO line profile and kinematics**: Extract 1D spectrum over A1+A2, single Gaussian fit for FWHM; moment maps  
  > "A single Gaussian fit to the line profile from images A1 and A2, gives a line FWHM of $1080\pm20$ km s$^{-1}$." (3.2 CO (11–10))
   - fitting: single Gaussian  
  > "A single Gaussian fit to the line profile from images A1 and A2" (3.2 CO (11–10))
   - validation: _not stated_

## Software

- **CASA** : ALMA pipeline calibration, imaging and self-calibration  
  > "processed using the ALMA pipeline within the Common Astronomy Software Applications () package" (2 Observations and data reduction)
- **UVMultiFit** : visibility-plane fitting of delta functions for flux densities  
  > "using UVMultiFit (cite: Marti-Vidal:2014)" (2 Observations and data reduction)
- **Astropy** : acknowledged as used in the research  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total 340 GHz continuum flux density | 24.3 | 1.2 | mJy | 1 | $S_{\rm 340~GHz} = 24.3\pm1.2$ mJy |
| Continuum flux ratio A2/A1 | 0.86 | 0.01 | dimensionless | 2 | A2/A1  / $0.86\pm0.01$  / $0.83\pm0.05$ |
| CO(11-10) flux ratio A2/A1 | 0.83 | 0.05 | dimensionless | 2 | $S_{\rm A2}/S_{\rm A1} = 0.83\pm0.05$ |
| CO(11-10) line FWHM | 1080 | 20 | km/s | 3 | gives a line FWHM of $1080\pm20$ km s$^{-1}$ |
| Velocity dispersion at black hole position | 300 | not stated | km/s | 3 | high velocity dispersion of 300 km s$^{-1}$ at the position of the black hole |
| Naturally-weighted continuum rms | 19 | not stated | uJy/beam | 1 | is $19~\upmu$Jy beam$^{-1}$ |

## Qualitative findings

- Object Y is a noise artefact from residual phase errors, not a genuine source  
  > "we conclude that object Y is a noise artefact resulting from residual phase errors rather than a genuine astronomical source." (3.1 Continuum)

## Claim tuples

- H: Does the flux-ratio anomaly persist in sub-mm continuum? | E: Visibility-plane delta-function fits to super-uniform-weighted epoch 2 continuum | R: A2/A1 = 0.86±0.01 | F: Anomaly persists at 340 GHz | **supported**
- H: Is a flux-ratio anomaly present in CO(11-10)? | E: Visibility fits to channels in blue-shifted velocity range | R: A2/A1 = 0.83±0.05 | F: First detection of a mm-line flux-ratio anomaly in a lensed quasar | **supported**
- H: Is object Y a real dusty dwarf galaxy? | E: Re-reduction with self-calibration | R: 4 sigma peak in pipeline data disappears after self-cal | F: Object Y is a noise artefact | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gaussian models for the lensed images tried but unstable  
  > "We also attempted to fit Gaussian models, however, as the images are only marginally resolved" (3.1 Continuum)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass models not tested; deferred to follow-up paper  
  > "we have not tested the possible mass models that are consistent with the data, which we defer to a follow-up paper." (Discussion and Conclusions)
- Caveat (inferred, ours): Line flux ratios use a blue-shifted channel range that may be offset from the nucleus, mixing differential magnification with substructure
- Caveat (inferred, ours): Self-calibration model choice could affect faint features, yet the processing details are sparse
- Caveat (inferred, ours): Velocity range inconsistent between text and table captions

## Reproducibility

- Data public (paper): Archival ALMA data, project 2013.1.01110.S  
  > "We present an analysis of archival observations" (abstract)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: Imaging parameters and self-cal intervals
- Missing: Line-free channels
- Missing: UVMultiFit setup
- Data volume (inferred): ~50-150 GB raw (two epochs, 4 spws x 128 channels, 2 s integration)
- Score (inferred): 3/5, Public data and a clear outline, but imaging and self-calibration parameters are largely unstated.
- Rediscovery candidate: no, Key processing parameters missing, so it is hard to redo exactly even though results are numeric.

## Links

- Method: Marti-Vidal:2014 (UVMultiFit visibility fitting)
- Companion: Inoue:2017 (Original analysis of the same data reporting object Y)
- Companion: Stacey:2018 (FIR-radio SED of MG J0414+0534 and fraction of FIR-bright lensed quasars)
- Related: Dark Energy Survey
- Related: Euclid

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
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
  "facts": 61,
  "stated": 30,
  "rate": 0.492
 },
 "evidence_ok": true
}
```
