# Evidence for Multiple Pathways to Deuterium Enhancements in Protoplanetary Disks

`2012ApJ...749..162O` | The Astrophysical Journal 2012 | first author: Öberg, Karin I. | arXiv: 1202.3992 | DOI: 10.1088/0004-637X/749/2/162

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Do DCN and DCO+ have different radial distributions in the TW Hya disk, implying different deuterium fractionation pathways?  
  > "we use these new data to compare the DCN and DCO$^+$ distributions, and to test if these data suggest different pathways to deuterium enhancements in these species" (Introduction)
- Target **TW Hya**: coordinates _not stated_; z/distance 51 pc  
  > "TW Hydrae is the most well-studied protoplanetary disk because of its proximity (51 pc)" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00001.SV
- bands: Band 6  
  > "TW Hya was observed on April 20th and 23rd, 2011 in ALMA band 6 as a part of ALMA Science Verification." (Spatially Resolved Observations of DCN and DCO$^+$ towards TW Hya)
- frequencies and spectral setup: DCN 3-2 at 217.238 GHz; channel spacing 0.16 km/s resampled to 0.2 km/s  
  > "channel spacing of 0.16 km s$^{-1}$ (resampled to 0.2 km s$^{-1}$)" (Spatially Resolved Observations of DCN and DCO$^+$ towards TW Hya)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 2.8'' x 2.3'' synthesized beam  
  > "synthesized beam size $2.8\ensuremath{''}\times2.3\ensuremath{''}$" (Spatially Resolved Observations of DCN and DCO$^+$ towards TW Hya)
- max recoverable scale: _not stated_
- sensitivity: rms 12 mJy/beam in line-free channels  
  > "with an rms of 12 mJy beam$^{-1}$ in the line-free channels" (Spatially Resolved Observations of DCN and DCO$^+$ towards TW Hya)
- time on source: _not stated_
- observing dates: April 20th and 23rd, 2011  
  > "TW Hya was observed on April 20th and 23rd, 2011 in ALMA band 6" (Spatially Resolved Observations of DCN and DCO$^+$ towards TW Hya)
- pi or archival as stated: _not stated_
- Line: DCN J=3-2 (217.238 GHz)
- Other facility **SMA**: DCO+ 3-2 and HCN data from Qi et al. 2008  
  > "together with comparable DCO$^+$ observations from the Submillimeter Array" (abstract)
- External data: Disk density and temperature structure  
  > "we adopt a physical structure of the TW Hya disk with density and temperature distributions from (cite: Qi04; Qi06)" (The DCN radial profile) [from (cite: Qi04; Qi06)]
- External data: HCN best-fit vertical boundaries and radial profile (alpha~-1)  
  > "we assume DCN exists in a disk layer with vertical boundaries given by the best-fit values for HCN in (cite: Qi08)" (The DCN radial profile) [from (cite: Qi08)]
- External data: DCO+/HCO+ abundance ratio 0.035  
  > "previously measured DCO$^+$/HCO$^+$ abundance ratio of 0.035 in the TW Hya disk (cite: vanDishoeck03)" (The DCN radial profile) [from (cite: vanDishoeck03)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Released calibrated visibilities used  
  > "The calibrated visibilities and CLEANed reference images were released and made available to the public in August 2011" (Spatially Resolved Observations of DCN and DCO$^+$ towards TW Hya)
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

- Disk modeling method and chi2 visibility fitting  
  > "we use the same methods as (cite: Qi08) to model observations of DCO$^+$, HCO$^+$ and HCN emission from TW Hya" (The DCN radial profile) [from (cite: Qi08)]
- Disk physical structure  
  > "density and temperature distributions from (cite: Qi04; Qi06)" (The DCN radial profile) [from (cite: Qi04; Qi06)]

### Not stated but needed to reproduce (our reading)

- Exact vertical layer boundaries and HCN profile values from Qi08
- Fixed disk inclination, position angle, systemic velocity and turbulent linewidth
- Best-fit N10 values
- Collisional rate data and molecular data file used in RATRAN
- Number of fitted visibilities and degrees of freedom (chi2 values are huge)
- Integration range for the moment map
- SMA DCO+ data reduction

## Analysis recipe

1. **Model DCN column density as power law**: Parametric power-law column density N10*(r/10)^alpha in a layer of the adopted TW Hya disk structure, cut off at 100 AU; alpha=-1, 0, 2 tested  
  > "we model the DCN column density in this layer as a power law, $N_{\rm 10}\times(r/10)^{\rm \alpha}$" (The DCN radial profile)
   - software: RATRAN
   - parameter: alpha = -1, 0, 2; cutoff 100 AU  
  > "We therefore tested models of DCN column density with three different values of power-law index, $\alpha=-1$, 0, and 2" (The DCN radial profile)
   - assumption: Hyperfine levels in LTE; DCN vertical layer same as HCN  
  > "The relative population of the hyperfine levels are assumed to be in LTE" (The DCN radial profile)
   - fitting: Optimize N10 by minimizing chi2 of complex visibilities  
  > "we optimize $N_{\rm 10}$ by minimizing the $\chi^2$ value, the weighted differences between the observed and modeled complex visibilities" (The DCN radial profile)
   - validation: Compared channel maps and chi2 among models  
  > "The model with $\alpha=-1$ clearly provides the best fit to the data" (The DCN radial profile)
2. **Derive DCN/HCN abundance ratio**: Ratio from best model (alpha=-1) and Qi08 HCN profile; robustness tested by varying indices by ±2  
  > "Using Model 1 and the HCN profile reported by (cite: Qi08), we calculate the DCN/HCN abundance ratio to be $\sim0.017$" (The DCN radial profile)
   - fitting: _not stated_
   - validation: Varying power-law indices by ±2 changes ratio by <30%  
  > "varying the power-law indices by $\pm2$ changes the ratio by less than 30%" (The DCN radial profile)

## Software

- **RATRAN** : Monte Carlo radiative transfer with DCN hyperfine structure to produce model visibilities  
  > "We use the Monte Carlo radiative transfer code RATRAN (cite: Hogerheijde00), taking into account the DCN hyperfine structure" (The DCN radial profile)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| chi2 Model 1 (alpha=-1) | 2296194 | not stated | dimensionless | 1 | which increase from 2296194 for Model 1, to 2298334 for Model 2, and to 2300603 for Model 3 |
| chi2 Model 2 (alpha=0) | 2298334 | not stated | dimensionless | 1 | to 2298334 for Model 2 |
| chi2 Model 3 (alpha=2) | 2300603 | not stated | dimensionless | 1 | and to 2300603 for Model 3 |
| DCN/HCN abundance ratio | ~0.017 | <30% for index variation ±2 | dimensionless | 2 | We estimate a DCN/HCN abundance ratio of $\sim0.017$ |

## Qualitative findings

- DCN is centrally peaked and compact, whereas DCO+ is more extended  
  > "The DCN emission is peaked on the TW Hya stellar position and spatially compact, barely resolved with the ALMA beam." (Spatially Resolved Observations of DCN and DCO$^+$ towards TW Hya)

## Claim tuples

- H: DCN and DCO+ have different radial distributions, implying different formation pathways | E: Fit power-law column density models (alpha=-1,0,2) to ALMA DCN visibilities | R: alpha=-1 gives the lowest chi2; alpha=0 and 2 underestimate line wings | F: DCN is centrally peaked unlike DCO+, so it forms at smaller radii and higher temperature, consistent with CH2D+ pathways | **supported**
- H: Deuterium fractionation is efficient in the disk at a range of temperatures | E: Compare DCN/HCN with DCO+/HCO+ | R: 0.017 vs 0.035 | F: Similar ratios; fractionation efficient at a range of temperatures | **supported**

## Reasoning

- Why this data: New ALMA SV DCN data have higher signal-to-noise than SMA data  
  > "newly released ALMA science verification data on DCN 3-2 towards TW Hydrae have higher signal-to-noise and allow for significant constraints" (Introduction)
- Why this method: _not stated_
- Alternative: Dynamics, photochemistry, freeze-out and ice photodesorption judged unlikely to dominate  
  > "Having dismissed dynamics, photochemistry, and mechanisms requiring grains, as plausible routes to significant deuterium fractionation in the outer disk" (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution too low to characterize profile shape; more centrally peaked profiles not excluded  
  > "A more detailed characterization of the shape of the DCN radial profile requires higher spatial resolution than currently available." (The DCN radial profile)
- Caveat (inferred, ours): Only three power-law indices tested; no uncertainties on N10 or alpha
- Caveat (inferred, ours): Beam ~3'' (~150 AU) barely resolves DCN, so radial inference is model dependent
- Caveat (inferred, ours): Disk structure and vertical layer fixed from earlier work
- Caveat (inferred, ours): Chemical pathway inference is qualitative

## Reproducibility

- Data public (paper): Public SV data  
  > "released and made available to the public in August 2011" (Spatially Resolved Observations of DCN and DCO$^+$ towards TW Hya)
- Products in archive: _not stated_
- Missing: Disk model parameters from Qi08/Qi04/Qi06
- Missing: Best-fit N10 values
- Missing: Fitting code (Qi08 pipeline) not provided
- Data volume (inferred): ~1-5 GB (SV calibrated visibilities)
- Score (inferred): 4/5, Public data and simple model, but the fitting depends on unreleased code and earlier-paper disk model details.
- Rediscovery candidate: no, Recipe depends on inherited disk model and fitting code not fully specified.

## Links

- Method: (cite: Qi08) (Disk modeling and visibility fitting method)
- Method: (cite: Hogerheijde00) (RATRAN radiative transfer code)
- Companion: (cite: Qi08) (SMA DCO+ and HCN observations of TW Hya)
- Related: ALMA Science Verification TW Hya Band 6

## Checks

```json
{
 "quotes": 36,
 "quotes_ok": 36,
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
  "facts": 61,
  "stated": 27,
  "rate": 0.443
 },
 "evidence_ok": true
}
```
