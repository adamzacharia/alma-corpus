# HCN (1‒0) opacity of outflowing gas in Arp 220W

`2021A&A...649A.125W` | Astronomy and Astrophysics 2021 | first author: Wang, J. Z. | arXiv: 2104.02896 | DOI: 10.1051/0004-6361/202140433

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies
- Question: What is the HCN/H13CN 1-0 line ratio, and hence the HCN 1-0 opacity, in the molecular outflow of Arp 220W?  
  > "Using H$^{13}$CN 1-0, the isotopic line of HCN 1-0, to obtain the line ratio of HCN/H$^{13}$CN 1-0 is an ideal way to derive the optical depth of HCN 1-0 in outflowing gas." (abstract)
- Target **Arp 220W**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00702.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: about 1.9 hours  
  > "The data used in this work were obtained from observations lasting about 1.9 hours on source with ALMA." (4.2 Outflow properties and future prospects)
- observing dates: _not stated_
- pi or archival as stated: Archival, PI L. Barcos-Muñoz  
  > "The data were taken from the ALMA archival system (project number: 2015.1.00702.S, PI: L. Barcos-Muñoz)" (The data)
- Line: HCN 1-0 (88.6318473 GHz)
- Line: H13CN 1-0 (86.3401764 GHz)
- External data: HCN/H13CN 1-0 ratio of about five for whole Arp 220 (IRAM 30m)  
  > "The HCN/H$^{13}$CN 1-0 ratio in the entire system of Arp 220 is about five according to single-dish observations with IRAM 30-meter telescope" (3.2 HCN/H13CN 1-0 line ratio) [from (cite: 2016MNRAS.455.3986W)]
- External data: 12C/13C = 40 in Arp 220  
  > "The $^{12}$C/$^{13}$C ratio in Arp 220 was updated to be 40 with ALMA observations of $^{12}$CO 3-2 and $^{13}$CO 4-3" (4.1 HCN 1-0 opacity in the outflowing gas) [from (cite: 2020ApJ...896...43W)]
- External data: Abundance ratio HCN/H13CN of 100  
  > "namely 100, which was suggested by (cite: 2011A&A...527A..36M)" (4.1 HCN 1-0 opacity in the outflowing gas) [from (cite: 2011A&A...527A..36M)]

## Processing

### Calibration

- pipeline or manual: Standard bandpass, phase and flux calibration using archive scripts in CASA  
  > "Standard bandpass, phase, and flux calibrations using scripts from the archive system were done in CASA" (The data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "imaging and deconvolution using natural weighting with a pixel size of 0.02$''$ and frequency resolution of 3.906 MHz in the task ‘tclean’" (The data)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "imaging and deconvolution using natural weighting with a pixel size of 0.02$''$" (The data)
- uv taper: _not stated_
- cell size: 0.02"  
  > "natural weighting with a pixel size of 0.02$''$" (The data)
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

- Same ALMA data set as earlier outflow detection  
  > "the same data set used in (cite: 2018ApJ...853L..28B)" (The data) [from (cite: 2018ApJ...853L..28B)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Line-free channels for continuum
- Cleaning threshold, masks and iterations
- Exact coordinates and distance of Arp 220W
- Box coordinates for spectral extraction
- Beam size and rms of the cubes
- Brightness temperature conversion details

## Analysis recipe

1. **Image cubes and maps**: tclean cube with natural weighting; continuum from line-free channels; velocity-integrated maps of HCN and H13CN wings  
  > "The continuum image obtained from line-free channels, the velocity-integrated maps of HCN 1-0 at the rest frequency of 88.6318473 GHz for both red and blue wings" (The data)
   - software: CASA
   - fitting: _not stated_
   - validation: Fluxes consistent with IRAM 30m  
  > "HCN and H$^{13}$CN 1-0 fluxes measured from ALMA data are consistent with those obtained with the IRAM 30-meter telescope" (3.2 HCN/H13CN 1-0 line ratio)
2. **Measure wing fluxes and line ratio limits**: Integrate spectra over red 5620-5800 and blue 4860-5040 km/s; 3 sigma upper limits for H13CN; ratio in brightness temperature  
  > "The red wing displayed in Figure 1 shown with red contours is integrated from 5620 to 5800 km s$^{-1}$ as radio-defined velocity, while the blue wing shown with blue contours is integrated from 4860 to 5040 km s$^{-1}$." (3.1 Spatial distribution of outflow traced by HCN)
   - parameter: uncertainty = sigma_rms x sqrt(dv DeltaV), dv ~13.2 km/s, DeltaV=180 km/s  
  > "The uncertainties are estimated with ${\sigma}_{rms}\times\sqrt{{\delta}v{\Delta}V}$" (3.2 HCN/H13CN 1-0 line ratio)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive HCN opacity**: Ratio of line intensities with tau(H13CN)/tau(HCN) set by 13C/12C abundance ratio  
  > "is assumed to be the same as the abundance ratio of $^{13}$C/$^{12}$C" (4.1 HCN 1-0 opacity in the outflowing gas)
   - assumption: HCN/H13CN abundance ratio 100 (or 40 from updated 12C/13C)  
  > "Assuming an $X_{HCN}$/$X_{H^{13}CN}$ abundance ratio of 100" (4.1 HCN 1-0 opacity in the outflowing gas)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration, imaging with tclean  
  > "were done in CASA, as well as imaging and deconvolution" (The data)
- **RADEX** : HCN 2-1 vs 1-0 opacity ratio for future prospects  
  > "Using the RADEX online calculator (cite: 2007A&A...468..627V)" (4.2 Outflow properties and future prospects)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HCN 1-0 flux, red wing | 631.1 | 22.5 | mJy km/s | 2 | is 631.1$\pm$22.5 mJy km s$^{-1}$ |
| HCN 1-0 flux, blue wing | 794.1 | 27.7 | mJy km/s | 2 | 794.1$\pm$27.7 mJy km s$^{-1}$ for the blue wing |
| HCN/H13CN 1-0 ratio lower limit, red and blue wings | >9.5 and >9.7 | 3 sigma | dimensionless | 2 | line ratios of HCN/H$^{13}$CN 1-0 greater than 9.5 and 9.7 in the red and blue wings |
| HCN/H13CN ratio lower limit, combined wings | >13.3 | 3 sigma | dimensionless | 2 | which gives a ratio of greater than 13.3 |
| HCN 1-0 opacity upper limit (12C/13C=40) | <4.4 | not stated | dimensionless | 3 | HCN 1-0 (blue)   /   794.1$\pm$27.7    /    $<$4.4 |

## Qualitative findings

- Whether HCN 1-0 is optically thick or thin in the outflow remains uncertain  
  > "whether HCN 1-0 is optically thick or thin remains uncertain" (4.1 HCN 1-0 opacity in the outflowing gas)

## Claim tuples

- H: HCN 1-0 opacity in the Arp 220W outflow is lower than in the whole galaxy | E: Measure HCN and H13CN 1-0 in outflow wings from archival ALMA data | R: H13CN undetected; HCN/H13CN > 9.5-13.3 vs about 5 for the whole galaxy | F: Opacity in the outflow is at least about three times lower than the galaxy average | **supported**
- H: A smaller conversion factor is needed for the outflow | E: Compare opacities | R: Low opacity upper limit | F: A lower conversion factor than for the host galaxy should be used | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Sensitivity too limited to determine accurate opacity  
  > "the accurate opacity of HCN 1-0 of the outflowing gas in Arp 220W cannot be determined because of the limited sensitivity of the observations" (4.2 Outflow properties and future prospects)
- Caveat (inferred, ours): Absorption and SO/HC15N contamination affect ratios
- Caveat (inferred, ours): Abundance ratio assumed equal to 12C/13C
- Caveat (inferred, ours): Inconsistent limits quoted (9.5/9.7 vs 9.6; Table 1 limits differ from text)
- Caveat (inferred, ours): Ratio taken in flux versus brightness temperature not detailed

## Reproducibility

- Data public (paper): Data from ALMA archive  
  > "The data were taken from the ALMA archival system" (The data)
- Products in archive: _not stated_
- Missing: CASA version and clean parameters
- Missing: Extraction box positions
- Missing: Line-free channels
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and simple recipe, but imaging and extraction details are missing.
- Rediscovery candidate: yes, Public data, simple flux and ratio calculation with numeric limits, though extraction regions are not given.

## Links

- Companion: (cite: 2018ApJ...853L..28B) (Original outflow detection with the same data)

## Checks

```json
{
 "quotes": 33,
 "quotes_ok": 33,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 62,
  "stated": 22,
  "rate": 0.355
 },
 "evidence_ok": true
}
```
