# Deep ALMA imaging of the merger NGC 1614. Is CO tracing a massive inflow of non-starforming gas?

`2016A&A...594A..70K` | Astronomy and Astrophysics 2016 | first author: König, S. | arXiv: 1603.05405 | DOI: 10.1051/0004-6361/201628535

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: How do the large-scale molecular gas in the dust lane and the circumnuclear ring of the merger NGC 1614 differ in excitation and isotopic abundances, as probed by 12CO, 13CO, C18O, CN and CS?  
  > "were used to assess the properties of the large-scale molecular gas reservoir and its connection to the circumnuclear molecular ring in the merger NGC 1614." (abstract)
- Target **NGC 1614**: coordinates 04:34:00.02688, -08:34:44.5692 (J2000, phase center)  
  > "The phase center of the observations was located at $\alpha$=04:34:00.02688 and $\delta$=$-$08.34.44.5692 (J2000)." (2 Observations, data reduction and analysis); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00991.S
- bands: Band 3 (3 mm)  
  > "in band 3 (3 mm) as part of Cycle 2 observations" (2 Observations, data reduction and analysis)
- frequencies and spectral setup: Two tunings centered on 113.5 and 108.5 GHz; four spectral windows of 1.875 GHz, ~5 km/s resolution after Hanning smoothing  
  > "We used four spectral windows of 1.875 GHz bandwidth ($\sim$5000 km s$^{\rm -1}$) each, with a velocity resolution of $\sim$5 km s$^{\rm -1}$, after Hanning smoothing." (2 Observations, data reduction and analysis)
- continuum bandwidth: _not stated_
- arrays: ACA and ALMA main array compact configuration  
  > "Here we focus on the data obtained with the ALMA Compact Array (ACA) and the ALMA main array in compact configuration." (2 Observations, data reduction and analysis)
- configurations: _not stated_
- baselines: ACA 8.8-49.0 m; main array 15.0-390 m  
  > "With baseline lengths of between 8.8 m and 49.0 m, the ACA data are sensitive to scales smaller than $\sim$38$^{\prime\prime}$." (2 Observations, data reduction and analysis)
- angular resolution: _not stated_
- max recoverable scale: ~38" (ACA); ~22" (main array compact)  
  > "The compact configuration main array ALMA data are sensitive to scales smaller than $\sim$22$^{\prime\prime}$ (baselines: 15.0 m $-$ 390 m)." (2 Observations, data reduction and analysis)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: ACA 2014 June 16 and 30; compact configuration 2014 December 4 and 5  
  > "The ACA observations took place on 2014 June 16 and 30, the ALMA compact configuration observations on 2014 December 4 and 5." (2 Observations, data reduction and analysis)
- pi or archival as stated: PI: S. König  
  > "project 2013.1.00991.S (PI: S. König)" (2 Observations, data reduction and analysis)
- Line: 12CO 1-0 (not stated)
- Line: 13CO 1-0 (not stated)
- Line: C18O 1-0 (not stated)
- Line: CN 1-0 (not stated)
- Line: CS 2-1 (not stated)
- Other facility **HST**: Optical image compared with 13CO and CS maps  
  > "A comparison with an *Hubble Space Telescope (HST)* image (Fig. [3](#fig:overlay_13co_false_color)b)" (3.3 13CO 1-0)
- External data: Single-dish CO fluxes used to check flux recovery  
  > "A comparison to single-dish observations shows that we recover approximately 115$\%$ of the flux that has recently been detected by (cite: cos11)." (3.2 12CO 1-0) [from (cite: cos11)]
- External data: Previous interferometric 12CO/13CO 1-0 results compared with ratio map  
  > "(cite: sli14) reported $\mathcal{R_{\rm 10}}$ similar to our findings." (3.5 12CO-to-13CO 1-0 line ratio) [from (cite: sli14)]

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

- task: CASA clean on combined ACA + main-array visibilities  
  > "The combined data set was then deconvolved using the “clean” task in CASA, and individual data cubes were created for each observable" (2 Observations, data reduction and analysis)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum reconstructed from line-free channels  
  > "The 3 mm continuum was reconstructed using line-free channels." (2 Observations, data reduction and analysis)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Visibilities combined by weighting data sets in the uv plane for continuous amplitude vs uv-distance  
  > "sets of visibilities from ACA and the compact configuration observations were combined by weighting the individual data sets in the uv plane" (2 Observations, data reduction and analysis)
- smoothing: Maps smoothed to common 5"x5" beam for ratio map  
  > "The resulting maps were smoothed to a common beam at 5$^{\prime\prime}$ $\times$ 5$^{\prime\prime}$" (2 Observations, data reduction and analysis)
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- clean weighting/robust, uniform used for continuum only mentioned
- cell and image size
- clean masks, thresholds, and iterations
- line-free channels and velocity integration ranges for moment maps
- CASA version
- calibrator names and flux scale uncertainty
- relative weighting of ACA vs main array
- rest frequencies
- distance and adopted cosmology

## Analysis recipe

1. **Combine and image ACA and main array data**: Weighted uv combination, CASA clean, cubes per line and continuum  
  > "The combined data set was then deconvolved using the “clean” task in CASA, and individual data cubes were created for each observable" (2 Observations, data reduction and analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: Recovered flux compared with single-dish (115% for 12CO, 98% for 13CO)  
  > "The recovered flux corresponds to 98$\%$ of the total flux detected with single-dish observations (cite: cos11)." (3.3 13CO 1-0)
2. **Make moment-0 maps and 12CO/13CO ratio map**: Moment-zero maps in GILDAS/MAPPING; smooth to common beam; pixel-by-pixel ratio, keep S/N>=5  
  > "Only pixels with signal-to-noise ratios equal to or higher than 5 in the ratio map were taken into account and are depicted in the resulting image." (2 Observations, data reduction and analysis)
   - software: GILDAS/MAPPING
   - parameter: common beam 5"x5"; no a-priori clipping  
  > "we used the integrated intensity maps of the two emission line distributions without a-priori clipping." (2 Observations, data reduction and analysis)
   - fitting: _not stated_
   - validation: _not stated_
3. **Convert line ratios to abundance ratios**: Assume 12CO 1-0 optically thick (tau=1), same gas and comparable excitation temperatures for isotopologs; derive [12CO]/[13CO] and [12CO]/[C18O]  
  > "We assume the $^{\rm 12}$CO 1$-$0 line transition to be optically thick ($\tau$ = 1), that the $^{\rm 12}$CO and $^{\rm 13}$CO emission trace the same gas" (4.1.2 Abundance effects)
   - assumption: tau(12CO 1-0)=1, comparable excitation temperatures  
  > "the excitation temperatures for the two are comparable" (4.1.2 Abundance effects)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration, combination and imaging (clean)  
  > "After calibration and imaging within CASA[^1] (cite: mcm07)" (2 Observations, data reduction and analysis)
- **GILDAS/MAPPING** : analysis of FITS cubes, moment maps  
  > "imported in the GILDAS/MAPPING[^2] for further analysis" (2 Observations, data reduction and analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 3 mm continuum integrated flux | 12.9 | 0.8 | mJy | 1 | 12.9$\pm$0.8 mJy |
| 12CO 1-0 integrated intensity | 241 | 1.0 | Jy km/s | 1 | 241$\pm$1.0 Jy km s$^{\rm -1}$ |
| 13CO 1-0 integrated intensity | 6.6 | 1.0 | Jy km/s | 1 | 6.6$\pm$1.0 Jy km s$^{\rm -1}$ |
| C18O 1-0 3sigma upper limit | <0.1 | not stated | Jy km/s | 1 | An upper limit at 3$\sigma$ amounts to $\sim$0.1 Jy km s$^{\rm -1}$ within the central 4$^{\prime\prime}$ $\times$ 4$^{\prime\prime}$. |
| CS 2-1 integrated intensity | 1.3 | 1.0 | Jy km/s | 1 | 1.3$\pm$1.0 Jy km s$^{\rm -1}$ |
| CN 3/2-1/2 to 1/2-1/2 ratio | ~2 | not stated | dimensionless | 1 | amounts to $\sim$2, which indicates that the gas traced by the CN emission in NGC 1614 is optically thin. |
| 12CO/13CO 1-0 ratio near nucleus | ~30 | not stated | dimensionless | 2 | shows an elongated structure of constant value ($\sim$30) |
| 12CO/13CO 1-0 ratio at western dust lane edge | 40-45 | not stated | dimensionless | 2 | increases to its highest values of 40 to 45 at the outer edge of the western dust lane |
| [12CO]/[C18O] abundance ratio | ~900 | lower limit | dimensionless | 3 | The resulting abundance ratio is \[$^{\rm 12}$CO\]/\[C$^{\rm 18}$O\] $\sim$900. |
| [12CO]/[13CO] abundance ratio | ~90 | not stated | dimensionless | 3 | would be roughly 90 |

## Qualitative findings

- 13CO peaks between the dust lane and the ring, unlike 12CO, which follows the dust lane and tidal tails.  
  > "In contrast to $^{\rm 12}$CO, its line emission peaks between the dust lane and the circumnuclear molecular ring." (abstract)

## Claim tuples

- H: Is the dust-lane gas diffuse and unbound while funneled inward? | E: Mapped 12CO/13CO 1-0 ratio across the dust lane and nucleus | R: Ratio >45 in dust lane, ~30 in nucleus | F: Gas in the dust lane is diffuse and unbound, then compressed in the inner 1.5 kpc | **supported**
- H: Does inflow dilute starburst isotopic enrichment? | E: Used C18O upper limit and the line ratio to infer abundance ratios | R: [12CO]/[C18O] ≥900, [12CO]/[13CO] >90 | F: Inflow of unprocessed gas may explain the low 18O enrichment | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Shocks and high gas temperature as the cause of the high ratio considered unlikely  
  > "This most likely excludes the notion of high gas temperatures as the cause of the elevated line ratio." (4.1.1 Excitation effects)
- How they decided it was enough: _not stated_
- Limitation (authors): Beam dilution may affect the C18O deficiency; higher resolution is needed.  
  > "this could also be an effect of the size of the beam in the observations" (4.1.2 Abundance effects)
- Caveat (inferred, ours): Abundance ratios rest on an assumed tau=1 for 12CO
- Caveat (inferred, ours): Ratio uncertainties are not given
- Caveat (inferred, ours): The C18O limit is a lower limit on the abundance ratio only
- Caveat (inferred, ours): Coarse 4"x2" resolution

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: clean parameters and masks
- Missing: calibrator and version details
- Missing: velocity ranges for moments
- Data volume (inferred): ~50-100 GB raw (ACA + 12m, 4 spws)
- Score (inferred): 4/5, Data are identifiable by project code but the imaging and calibration details are sparse.
- Rediscovery candidate: no, Imaging settings and integration ranges are missing; the abundance step relies on assumptions.

## Links

- Companion: (cite: koenig13) (Previous high-resolution CO 2-1 study of NGC 1614)

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 62,
  "stated": 27,
  "rate": 0.435
 },
 "evidence_ok": true
}
```
