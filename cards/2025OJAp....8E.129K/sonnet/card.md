# Observing the Sun with the Atacama Large Aperture Submillimeter Telescope (AtLAST): Forecasting Full-disk Observations

`2025OJAp....8E.129K` | The Open Journal of Astrophysics 2025 | first author: Kirkaune, Mats | arXiv: 2505.13145 | DOI: 10.33232/001c.144106

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: sun, instrumentation
- Question: What FOVs, detector counts and scan strategies let AtLAST scan the full solar disk in under 1 minute, enabling regular observations of dynamic phenomena such as flares?  
  > "We aim to explore what FOVs, detector counts, and scan strategies are suitable for AtLAST to realistically push the required full-disk scan times below 1 minute" (abstract)
- Target **Full solar disk (ALMA Band 3 TP map of 11.03.2023 used as base)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2022.1.01544.S
- bands: Full-disk ALMA TP maps in Band 3, 6, 7 (84-116, 211-275, 275-373 GHz)  
  > "Full-disk ALMA TP maps are available in ALMA Band 3, Band 6 and Band 7, in the frequency bands 84-116, 211-275 and 275-373 GHz respectively" (3.2 Realistic high-resolution input maps)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Band 3 TP map on 11.03.2023  
  > "ALMA Band 3 taken on 11.03.2023" (3.2 Realistic high-resolution input maps)
- pi or archival as stated: _not stated_
- Other facility **SDO/AIA**: 304 and 1600 Å full-disk maps at the epoch of ALMA TP observations, used to build input maps  
  > "querying SDO AIA (cite: 2012SoPh..275...17L; 2012SoPh..275....3P) maps from the 304 and 1600 Å channels at the same epoch of existing full-disk ALMA TP observations" (3.2 Realistic high-resolution input maps)
- External data: Instrument parameter ranges for AtLAST multi-chroic cameras (pixel counts, spacings)  
  > "(cite: AtLAST_memo_4) has gathered estimates for the ranges of instrumental parameters for different types of instruments at AtLAST." (3.3 maria-simulated solar observations) [from (cite: AtLAST_memo_4)]
- External data: AtLAST acceleration and velocity limits (1 deg/s^2, 3 deg/s)  
  > "With a acceleration limit of 1 $^\circ$/s$^2$ and a velocity limit of 3 $^\circ$/s (cite: 2024arXiv240218645M)" (4.3 Cadence of observations) [from (cite: 2024arXiv240218645M)]
- External data: Wavelength vs brightness temperature relation of the Sun  
  > "This was done by utilising the relation between wavelength and brightness temperature from (cite: 2004A&A...419..747L)" (3.2 Realistic high-resolution input maps) [from (cite: 2004A&A...419..747L)]
- Simulation/model as data: maria-simulated AtLAST time-ordered data and maps of a constructed solar input map  
  > "The scan itself then creates time ordered data (TODs) for each detector" (3.3 maria-simulated solar observations)

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
- smoothing: Gaussian with standard deviation of 1 pixel to fill gaps in 100 and 250 GHz maps  
  > "These are done with a Gaussian of standard deviation of 1 pixel for each of these two cases" (4.2.1)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Double-circle scan pattern and sampling length definition  
  > "At ALMA, full-disk maps of the Sun are created by scanning with a singular 12-m antenna in a double-circle pattern (cite: 2017SoPh..292...88W)." (4.1.2 Scan pattern) [from (cite: 2017SoPh..292...88W)]
- Process of creating synthetic observations in maria  
  > "The process of creating synthetic observations in `maria` is thoroughly explained in (cite: 2024OJAp....7E.118V)." (3.3 maria-simulated solar observations) [from (cite: 2024OJAp....7E.118V)]

### Not stated but needed to reproduce (our reading)

- maria version and configuration files (site, weather, sampling rate, beam model)
- AIA map dates, intensity mask threshold and 1600 Å scaling factor
- Exact brightness temperature scaling applied per frequency
- Atmosphere model parameters (PWV, seed)
- Power spectrum computation details
- Calibrated ALMA TP map processing

## Analysis recipe

1. **Construct millimetre full-disk input map**: Combine AIA 304 (quiet Sun) with scaled AIA 1600 (active regions) via intensity mask, scale to ALMA TP brightness temperature distribution  
  > "We therefore construct the required millimetre full-disk maps by taking AIA 304 map, keeping the QS regions, but replacing the active regions with those in AIA 1600 Å multiplied with a scaling factor." (3.2 Realistic high-resolution input maps)
   - fitting: _not stated_
   - validation: Visual comparison with ALMA TP maps convolved to TP beam  
  > "The threshold of which had to be adjusted slightly at different epochs to achieve the visually best reference map." (3.2 Realistic high-resolution input maps)
2. **Simulate AtLAST scans for Cases A-C**: maria simulations of circular detector arrays with double-circle or single-circle scans in four bands (100, 250, 670, 950 GHz)  
  > "Three different instrumental setups with different scan strategies are discussed in detail." (4.2)
   - software: maria
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive scan time vs FOV and pixel count relations**: Compute minor circles needed and scan time under AtLAST limits; fit power laws  
  > "A wide range of instrument FOVs were then set-up, and the required number of minor circles per pattern computed" (4.3 Cadence of observations)
   - software: maria
   - fitting: Power-law (log-log) fits  
  > "To make this easier, the area between first-order log-log fits to the two different sampling lengths has been shaded to the appropriate colour associated with the pixel spacing." (Results, Cadence of observations)
   - validation: _not stated_
4. **Quantify map quality with power spectra with and without atmosphere**: Compare spatial power spectra of synthetic maps to input map; rerun with 2D maria atmosphere  
  > "we utilise spatial power spectra, as comparing these spectra to that of the input map will give insight" (5.4)
   - software: maria
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **maria** : Single-dish telescope simulator for synthetic AtLAST solar observations  
  > "the all-purpose single-dish telescope simulator `maria`[^1] (cite: 2024OJAp....7E.118V) is used." (1 Introduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Case A scan time (1000 pixels, 36 minor circles) | 89 | not stated | s | 2 | It was found that the required time needed to complete such a scan was $~89$ seconds. |
| Case B scan time | 11.4 | not stated | s | 2 | the shortest time AtLAST could complete such a scan is $\sim 11.4$ seconds |
| Case C scan time | 2.7 | not stated | s | 2 | which it completes in about 2.7 seconds |
| Pixels for 1-min cadence at 950 GHz, 1.0 fλ spacing | 24,464 | not stated | pixels | 3 | / 1.0 f$\lambda$ /   280   /  1708   / 12,165  / 24,464  / |

## Qualitative findings

- Double-circle scan is acceptable for small to intermediate FOV; large FOV (≳0.25°) favours a simple circular scan with second-scale cadence  
  > "Using instruments with larger FOVs ($\gtrapprox 0.25^\circ$, equivalent to $\gtrapprox$ 1 R$_\odot$), we find a simple circular scan to be more efficient" (abstract)

## Claim tuples

- H: AtLAST can scan the full solar disk in under 1 minute with realistic instruments | E: maria simulations of three instrument cases with different scan patterns | R: 89 s (A), 11.4 s (B), 2.7 s (C); 50,000 pixels give sub-minute cadence in most bands | F: Sub-minute full-disk cadence is feasible with first-generation instruments, seconds with larger ones | **supported**
- H: Larger FOV reduces atmospheric impact via shorter scans | E: Power spectra with and without atmosphere | R: Noise dominates at ~3.5'' for Case A and ~2'' for Case C at 950 GHz | F: Large FOV, short scan preferable | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Lissajous daisy, raster and Lissajous box compared with double-circle; daisy slowest (250 s)  
  > "89 s for the double-circle, 102 s for the back-and-forth raster, 142 s for the Lissajous box, and 250 s for the Lissajous daisy pattern" (5.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Input map is UV-based, not true millimetre; one map used for all frequencies; time-evolving atmosphere not studied  
  > "full-disk maps in the ultraviolet are not perfect representations of the millimetre Sun, as slightly different heights in the atmosphere are probed." (3.2 Realistic high-resolution input maps)
- Caveat (inferred, ours): Single static input map; no temporal evolution or flare dynamics simulated
- Caveat (inferred, ours): Noise-free simulations for cadence; atmosphere only 2D and briefly treated
- Caveat (inferred, ours): Detector sensitivity and noise not modelled

## Reproducibility

- Data public (paper): SDO AIA maps are public and the ALMA TP data come from project 2022.1.01544.S; maria is public  
  > "initially constructed from publicly available full disk maps from the Solar Dynamics Observatory (SDO)" (abstract)
- Products in archive: _not stated_
- Missing: maria version/configs
- Missing: Input map construction parameters
- Missing: Exact epoch of AIA maps
- Data volume (inferred): small (<10 GB)
- Score (inferred): 3/5, maria and the data are public, but configs and input-map construction parameters are missing.
- Rediscovery candidate: no, Mostly simulation-based with incompletely specified inputs, and ALMA data play a minor role.

## Links

- Method: (cite: 2024OJAp....7E.118V) (maria simulator)
- Method: (cite: 2017SoPh..292...88W) (ALMA double-circle TP scan)
- Companion: (cite: 2024ORE.....4..140W) (AtLAST solar science cases)
- Related: AtLAST
- Related: SDO/AIA

## Checks

```json
{
 "quotes": 30,
 "quotes_ok": 30,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 22,
  "rate": 0.333
 },
 "evidence_ok": true
}
```
