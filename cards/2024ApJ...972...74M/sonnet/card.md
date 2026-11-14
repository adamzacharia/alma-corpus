# Observations of Low and Intermediate Spectral Peak Blazars with the Imaging X-Ray Polarimetry Explorer

`2024ApJ...972...74M` | The Astrophysical Journal 2024 | first author: Marshall, Herman L. | arXiv: 2310.11510 | DOI: 10.3847/1538-4357/ad5671

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars
- Question: Do IXPE X-ray polarization observations of LSP/ISP blazars detect polarization, and what do limits imply for X-ray emission models (Compton vs hadronic)?  
  > "For none of these objects was IXPE able to detect X-ray polarization at the 3$\sigma$ level." (abstract)
- Target **3C 273**: coordinates _not stated_; z/distance z=0.158339  
  > "3C273 ($z=0.158339$) is one of the brightest X-ray emitting LSP blazars." (3C 273); distance from _not stated_
- Target **3C 279**: coordinates _not stated_; z/distance z=0.538  
  > "3C 279 ($z=0.538$) is one of the most rapidly varying blazars" (3C 279); distance from _not stated_
- Target **3C 454.3**: coordinates _not stated_; z/distance z=0.859  
  > "3C 454.3 ($z=0.859$) has had several well-studied outbursts" (3C 454.3); distance from _not stated_
- Target **S5 0716+714**: coordinates _not stated_; z/distance z=0.3  
  > "S5 0716$+$714 ($z=0.3$) is a highly variable source" (S5 0716+714); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
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
- Other facility **IXPE**: 2–8 keV X-ray polarimetry of four blazars (main data)  
  > "Event data were selected over the full bandpass from 2 to 8 keV, from a circular region 60$^{\prime\prime}$ radius about each source" (2.1 Full-Band Analyses)
- Other facility **IRAM-30m (POLAMI)**: mm-radio polarization at 3.5 mm and 1.3 mm  
  > "at 3.5 mm (86.24 GHz) and 1.3 mm (228.93 GHz)" (Multiwavelength polarization observations)
- Other facility **Optical/IR polarimeters (Palomar, Kanata, Perkins, NOT, Skinakas, etc.)**: contemporaneous optical/IR polarization  
  > "In the optical, all the sources we observed in B, V, R, I bands by the AZT-8 & LX-200 telescopes (St. Petersburg University)" (Multiwavelength polarization observations)

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

- EVPA rotation test method  
  > "We tested for rotations using the method described in (cite: DiGesu2023)" (2.1 Full-Band Analyses) [from (cite: DiGesu2023)]
- Unbinned event-based likelihood polarization analysis with unpolarized background  
  > "Results from an unbinned event-based likelihood analysis (cite: marshall20) that accounts for an unpolarized background (cite: Marshall2023)" (2.1 Full-Band Analyses) [from (cite: marshall20); (cite: Marshall2023)]

### Not stated but needed to reproduce (our reading)

- No ALMA data are used; the paper contains no ALMA project code
- Energy binning and likelihood details of the Marshall method are not given
- Fit priors and statistics settings in 3ML not given
- Multiwavelength data reduction details are deferred to references

## Analysis recipe

1. **Full-band polarimetry**: Unbinned event-based likelihood on 2–8 keV events, source region 60" and background annulus 200–300"  
  > "with background selected from an annulus from 200$^{\prime\prime}$ to 300$^{\prime\prime}$ from the target" (2.1 Full-Band Analyses)
   - software: ixpeobssim, ftools
   - fitting: _not stated_
   - validation: _not stated_
2. **EVPA rotation search**: Event tracks rotated with uniform EVPA rate omega; delta log-likelihood chi2 with 1 dof  
  > "$\Delta S$ is distributed as $\chi^2$ with one degree of freedom because $q$ and $u$ are uninteresting parameters for this test." (2.1 Full-Band Analyses)
   - fitting: _not stated_
   - validation: _not stated_
3. **Spectropolarimetric fit**: Absorbed power law in 2–8 keV, NH fixed to Galactic, polarization constant and energy-independent  
  > "The absorption column densities were fixed to the nominal Galactic values,[^2] and the polarization parameters are assumed to be constant through each observation and independent of energy." (2.2 Spectropolarimetry)
   - software: 3ML
   - fitting: _not stated_
   - validation: Analysis with xspec gave similar results  
  > "An analysis using `xspec` gave similar results." (2.2 Spectropolarimetry)

## Software

- **ixpeobssim** : IXPE data processing  
  > "Data were processed using `ixpeobssim` (cite: 2022SoftX..1901194B)" (2.1 Full-Band Analyses)
- **3ML** : spectropolarimetric fits  
  > "Spectropolarimetric fits were performed with the Multi-Mission Maximum Likelihood (`3ML`) framework" (2.2 Spectropolarimetry)
- **HEASoft** 6.30.1: ftools processing  
  > "HEASoft 6.30.1[^3] (cite: heasoft)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Pi_X 99% upper limit, 3C 273 | <9.0 | not stated | % | 1 | / 3C 273 / IXPE / 01005901 / 59732.37 - 59734.45 / 95.28 / $< 9.0$% / |
| Pi_X 99% upper limit, 3C 279 | <12.7 | not stated | % | 1 | / 3C 279 / IXPE / 01005701 / 59743.02 - 59748.85 / 264.42 / $< 12.7$% / |
| Pi_X 99% upper limit, 3C 454.3 | <28 | not stated | % | 1 | / 3C 454.3 / IXPE / 01005401 / 59730.19 - 59732.34 / 98.12 / $< 28$% / |
| Pi_X 99% upper limit, S5 0716+714 | <26 | not stated | % | 1 | / S5 0716+714 / IXPE / 01005301 / 59669.43 - 59674.80 / 358.68 / $< 26$% / |

## Qualitative findings

- No EVPA rotations found in any source  
  > "We do not find evidence for EVPA rotations during our observations in any of the four sources." (2.1 Full-Band Analyses)

## Claim tuples

- H: Is X-ray polarization of LSP/ISP blazars detectable and which emission models does it favor? | E: IXPE 2–8 keV polarimetry with contemporaneous radio/optical polarization | R: No detections; upper limits ~9–28% | F: Favors Compton-dominated X-rays; hadronic models not fully eliminated; proton synchrotron strongly disfavored in 3C 279 | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Unpolarized optical emission in 3C 273 and 3C 454.3 prevents definitive conclusions  
  > "however the unpolarized optical/IR emission during the IXPE observations is preventing us from coming to definitive conclusions." (Summary)
- Caveat (inferred, ours): Not an ALMA paper; no ALMA data used
- Caveat (inferred, ours): Upper limits are method-dependent (full-band vs spectropolarimetric)

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Marshall 2023 method paper is only 'submitted'
- Missing: Multiwavelength data processing details
- Data volume (inferred): small (IXPE event files, a few GB)
- Score (inferred): 2/5, Not ALMA; X-ray analysis partly reproducible from public IXPE data but methods are cited rather than detailed.
- Rediscovery candidate: no, No ALMA data are used in the paper.

## Links

- Method: (cite: marshall20) (Unbinned event-based likelihood polarization method)
- Method: (cite: DiGesu2023) (EVPA rotation search method)
- Companion: (cite: Middei2023) (IXPE BL Lac observations)
- Related: POLAMI

## Checks

```json
{
 "quotes": 25,
 "quotes_ok": 25,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2021.A.00016.T"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 19,
  "rate": 0.268
 },
 "evidence_ok": true
}
```
