# The near-infrared silhouette of the Flying Saucer edge-on disc revealed by the JWST JEDIce program

`2026A&A...705L..14D` | Astronomy and Astrophysics 2026 | first author: Dartois, Emmanuel | arXiv: 2512.13503 | DOI: 10.1051/0004-6361/202557177

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks
- Question: What is the distribution of micron-sized dust grains in the edge-on Flying Saucer disc, and how does its silhouette extent compare with the large-grain disc seen by ALMA?  
  > "This study aims to investigate the distribution of micron-sized dust particles in the Flying Saucer in Rho Ophiuchi" (abstract)
- Target **Flying Saucer (BKLT J162813-243139)**: coordinates _not stated_; z/distance 120 pc (adopted)  
  > "for an adopted distance of 120 pc" (Modelling the Flying Saucer); distance from _not stated_

## Data provenance

- ALMA projects: 2022.1.00742.S
- bands: Band 7 continuum  
  > "We also include ALMA Band 7 continuum data (cycle 9 program #2022.1.00742.S)" (Observations)
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
- Other facility **JWST NIRSpec IFU (GO 5299, JEDIce)**: G235H and G395H IFU cubes used for the 3.29 micron silhouette and scattered light  
  > "The observations were taken with the G235H and G395H filters from 1.66–3.17 $\mu$m and 2.87–5.27 $\mu$m, respectively" (Observations)
- Other facility **HST, JWST MIRI imager and MRS (archival)**: 0.47, 7.7 and 17.035 micron images showing the silhouette  
  > "We retrieved archival data from HST (F475W, 0.47$\mu$m, program #13643), JWST MIRI/Imager (F770W, 7.7$\mu$m, program #4290)" (Observations)
- External data: Large-grain disc size of ~190 au from combined ALMA data sets  
  > "Using a combination of several ALMA data sets, a large-grain disc size of $\sim$190 au was recently measured (cite: Guilloteau2025)." (Constraints on the disc size and dust properties) [from (cite: Guilloteau2025)]
- External data: Ice optical constants  
  > "optical constants are given in (cite: Dartois2022)" (Benchmark disc model) [from (cite: Dartois2022)]

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

### Inherited from earlier work

- Modelling framework and parameter definitions follow the Tau 042021 benchmark model  
  > "uses the same framework and parameter definitions as previously described for the benchmark model of the edge-on disc Tau 042021 in (cite: Dartois2025)" (Modelling the Flying Saucer) [from (cite: Dartois2025)]

### Not stated but needed to reproduce (our reading)

- ALMA Band 7 calibration, imaging and beam details are not given
- Exact NIRSpec cube reduction and narrow-band image construction beyond the stated pipeline version
- Dust opacity details, stellar luminosity and the full set of free model parameters
- Values of the ambient-field scaling

## Analysis recipe

1. **Build narrow-band and optical-depth images from NIRSpec cube**: Stack channels within 3.29±0.01 and 3.2±0.01 micron; T = I3.29/(I3.2+I3.29ambient), tau=-ln(T)  
  > "By dividing $\rm I_{3.29}/(I_{3.2}+I_{3.29}^{ambient})=T$" (Constraints on the disc size and dust properties)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit radiative transfer disc model**: RADMC-3D model with small and settled icy grain populations, ambient PAH field and foreground extinction, fitted to images and cuts  
  > "we describe the Flying Saucer with a radiative transfer model using the RADMC-3D[^1] software" (Modelling the Flying Saucer)
   - software: RADMC-3D
   - assumption: Foreground RV=5.5 extinction curve with AV about 2; distance 120 pc  
  > "we added an $\rm R_V=5.5$ Milky Way extinction curve taken from (cite: Draine2003), adjusted to the expected visual extinction of around A$_V=$ 2." (Benchmark disc model)
   - fitting: Chi2 minimisation with Nelder-Mead downhill simplex from various starting points  
  > "The minimisation was performed using a Nelder-Mead downhill simplex method algorithm, starting from various initial conditions" (Benchmark disc model)
   - validation: Comparison of PSF-convolved model with images and midplane cuts  
  > "The model of the Flying Saucer exhibits a very good overall agreement with the observational spectral imaging" (Constraints on the disc size and dust properties)

## Software

- **RADMC-3D** : Radiative transfer modelling  
  > "using the RADMC-3D[^1] software (cite: Dullemond2012)" (Modelling the Flying Saucer)
- **JWST calibration pipeline** 1.17.1: Reduction of NIRSpec data  
  > "Data were reduced using calibration software version 1.17.1" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Small-grain midplane outer radius (silhouette) | 235 | ±10 | au | 2 | corresponding to a radius of about $235\pm10$ au (for an adopted distance of 120 pc) |
| Model inclination | 87.8 | not stated | deg | 2 | a disc inclination of 87.8$^{\circ}$ |
| Small-grain scale height H0 at 100 au | 7.8 | not stated | au | 2 | $\rm H_{0} = 7.8$ au |

## Qualitative findings

- Grains up to tens of microns are not settled, vertically and radially  
  > "dust settling is inefficient for grains as large as tens of microns, vertically and radially" (abstract)

## Claim tuples

- H: Does the small-grain disc extend beyond the large-grain mm disc? | E: Compare NIRSpec 3.29 micron silhouette and RT model with ALMA Band 7 continuum | R: Silhouette radius about 235 au vs 190 au from mm | F: Small grains extend further than large grains | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Model parameters may be degenerate, e.g. p and h  
  > "some of the parameters in such disc models could be interconnected/degenerate" (Constraints on the disc size and dust properties)
- Caveat (inferred, ours): No parameter uncertainties from the fit
- Caveat (inferred, ours): ALMA data used only qualitatively as an overlay

## Reproducibility

- Data public (paper): JWST/HST data retrieved from MAST archive; ALMA program cited  
  > "The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute" (Acknowledgements)
- Products in archive: _not stated_
- Missing: ALMA processing details
- Missing: Full model parameter file and opacities
- Data volume (inferred): ~10 GB (JWST cubes plus ALMA)
- Score (inferred): 3/5, Model parameters are listed but the data processing is only partly described.
- Rediscovery candidate: no, ALMA plays a minor role and the results come from a bespoke RT fit.

## Links

- Method: (cite: Dartois2025) (Benchmark edge-on disc model framework)
- Companion: (cite: Guilloteau2025) (ALMA large-grain disc size and CO analysis)
- Related: JEDIce (JWST GO 5299)

## Checks

```json
{
 "quotes": 24,
 "quotes_ok": 24,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 59,
  "stated": 18,
  "rate": 0.305
 },
 "evidence_ok": true
}
```
