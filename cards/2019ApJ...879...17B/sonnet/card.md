# Extreme CO Isotopologue Line Ratios in ULIRGS: Evidence for a Top-heavy IMF

`2019ApJ...879...17B` | The Astrophysical Journal 2019 | first author: Brown, Toby | arXiv: 1905.06950 | DOI: 10.3847/1538-4357/ab2246

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, astrochemistry, star_formation
- Question: Why are 13CO/C18O J=1-0 ratios extremely low in ULIRGs and a post-merger galaxy, and do they indicate a top-heavy IMF?  
  > "this paper aims to investigate the prevalence, robustness, and physical cause of unusual CO isotopologue intensity ratios in systems that span the merger sequence." (Introduction)
- Target **Arp 220**: coordinates _not stated_; z/distance D_L = 79 Mpc  
  > "| D$_L$ \[Mpc\] | 79 | 135 | 189 | 80 |" (Table 1); distance from _not stated_
- Target **IRAS 13120-5453**: coordinates _not stated_; z/distance D_L = 135 Mpc  
  > "| D$_L$ \[Mpc\] | 79 | 135 | 189 | 80 |" (Table 1); distance from _not stated_
- Target **IRAS 17208-0014**: coordinates _not stated_; z/distance D_L = 189 Mpc  
  > "| D$_L$ \[Mpc\] | 79 | 135 | 189 | 80 |" (Table 1); distance from _not stated_
- Target **NGC 2623**: coordinates _not stated_; z/distance D_L = 80 Mpc  
  > "| D$_L$ \[Mpc\] | 79 | 135 | 189 | 80 |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00379.S, 2015.1.00167.S, 2015.1.01191.S, 2016.1.00140.S, 2017.1.01306.S
- bands: Band 6 calibration uncertainties quoted (as stated in table caption)  
  > "ALMA band 6 calibration uncertainties are provided in brackets" (Table 1)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA 12m array  
  > "This paper combines new and archival ALMA 12m-array observations" (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.86x0.51, 0.73x0.52, 0.47x0.40, 1.37x1.04 arcsec (matched across lines)  
  > "| Resolution \["\] | 0.86 $\times$ 0.51 | 0.73 $\times$ 0.52 | 0.47 $\times$ 0.40 | 1.37 $\times$ 1.04 |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: ALMA cycles 2-5  
  > "our targets were observed across ALMA cycles 2-5" (Observations)
- pi or archival as stated: _not stated_
- External data: Infrared luminosity of NGC 2623 (and ULIRG IR luminosities)  
  > "NGC 2623 is a post-merger galaxy with L$_{\rm IR}$ = 10$^{11.6}$ L$_{\odot}$ (cite: Armus2009)" (Observations) [from (cite: Armus2009)]

## Processing

### Calibration

- pipeline or manual: Each calibrated measurement set reduced with the CASA version recommended by ALMA pipeline documentation  
  > "Each calibrated measurement set was reduced using the appropriate *Common Astronomy Software Applications* (cite: McMullin2007) version recommended by ALMA’s" (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: Band 6 calibration uncertainties given in brackets in Table 1  
  > "ALMA band 6 calibration uncertainties are provided in brackets" (Table 1)
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "We image all data using CASA’s `TCLEAN` command with a *Briggs* weighting" (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "robust parameter of 0.5, and rms threshold of 2$\sigma$" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Measurement sets continuum subtracted; CASA v5.1.1  
  > "The calibrated measurement sets are continuum subtracted and reduced using CASA v5.1.1." (Observations)
- line free channels: _not stated_
- primary beam correction: CASA impbcor  
  > "are primary beam corrected using the CASA routine `IMPBCOR`" (Observations)
- array combination: _not stated_
- smoothing: Final beam matching with imsmooth; cell, uvtaper, uvrange in tclean to match pixel, beam, minimum baseline  
  > "with the final beam matching achieved using `IMSMOOTH`." (Observations)
- final beam: _not stated_
- final rms: C18O/13CO 0.3-0.7 mJy/beam (35 km/s); 12CO 1.1-4.2 mJy/beam (20 km/s)  
  > "| $^{12}$CO $J$=1-0 rms \[mJy beam$^{-1}$\] (20 km s$^{-1}$) | 4.2 | 1.1 | 1.4 | 1.9 |" (Table 1)

### Not stated but needed to reproduce (our reading)

- Which ALMA project maps to which galaxy
- Cell size, image size, uvtaper and uvrange values used for matching
- Clean mask/threshold details
- Line-free channels for continuum subtraction
- Final common beam per galaxy and primary beam details
- Aperture definition for fluxes
- Conversion to brightness temperature details and S/N cut for ratio maps
- Meaning of the 3-sigma moment-map threshold (per channel or integrated)

## Analysis recipe

1. **Image the lines**: tclean with Briggs weighting robust 0.5, channel widths 20 km/s (12CO) and 35 km/s (C18O, 13CO), matched cell/uvtaper/uvrange, smoothed to a common beam  
  > "We set the image channel width to 20 km s$^{-1}$ for $^{12}$CO and 35 km s$^{-1}$ for C$^{18}$O and $^{13}$CO." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Make moment maps and integrated fluxes**: Integrated intensity maps with 3 sigma threshold, primary beam corrected; fluxes from an aperture covering all detected C18O and 13CO emission  
  > "All moment maps have a 3$\sigma$ threshold and are primary beam corrected using the CASA routine `IMPBCOR`." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Compute line ratio maps**: Convert moment maps from Jy/beam km/s to K km/s then ratio with immath  
  > "we convert each moment map in Figure [1](#fig:momentMaps) from Jy beam$^{-1}$ km s$^{-1}$ to K km s$^{-1}$ before computing the ratio using CASA’s `IMMATH` routine." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with previous values (Sliwa2017 etc.)  
  > "the values of $^{12}$CO/C$^{18}$O $J$=1-0 are consistent with those reported previously for Mrk 231, IRAS 13120-5453, and Arp 220" (Observations)

## Software

- **CASA** v5.1.1: calibration, imaging, continuum subtraction, ratio maps  
  > "The calibrated measurement sets are continuum subtracted and reduced using CASA v5.1.1." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean 13CO/C18O J=1-0, Arp 220 | 0.9 | 0.05 | dimensionless | 3 | / Mean $^{13}$CO/C$^{18}$O $J$=1-0 / 0.9 $\pm$ 0.05 / 2 $\pm$ 0.2 / 2 $\pm$ 0.2 / 0.5 $\pm$ 0.1 / |
| Mean 13CO/C18O J=1-0, NGC 2623 | 0.5 | 0.1 | dimensionless | 3 | / Mean $^{13}$CO/C$^{18}$O $J$=1-0 / 0.9 $\pm$ 0.05 / 2 $\pm$ 0.2 / 2 $\pm$ 0.2 / 0.5 $\pm$ 0.1 / |
| Mean 12CO/13CO J=1-0, NGC 2623 | 92 | 10 | dimensionless | 3 | / Mean $^{12}$CO/$^{13}$CO $J$=1-0 / 48 $\pm$ 2 \[$\pm$ 0.1\] / 36 $\pm$ 0.8 \[$\pm$ 0.1\] / 45 $\pm$ 2 \[$\pm$ 0.1\] / 92 $\pm$ 10 \[$\pm$ 0.5\] / |
| Mean 12CO/C18O J=1-0, IRAS 17208-0014 | 81 | 6 | dimensionless | 3 | / Mean $^{12}$CO/C$^{18}$O $J$=1-0 / 39 $\pm$ 2 \[$\pm$ 0.1\] / 63 $\pm$ 4 \[$\pm$ 0.2\] / 81 $\pm$ 6 \[$\pm$ 0.2\] / 40 $\pm$ 2 \[$\pm$ 0.1\] / |

## Qualitative findings

- C18O is stronger than 13CO over large areas in each system (inverted ratio)  
  > "there are large areas in each system where the line ratio is actually inverted and C$^{18}$O line emission is stronger than $^{13}$CO." (Observations)

## Claim tuples

- H: Are 13CO/C18O ratios unusually low in ULIRGs and a post-merger? | E: Resolved ALMA J=1-0 ratio maps of 4 galaxies | R: 13CO/C18O ≲1 across central regions | F: Low ratios confirmed and extended to more systems | **supported**
- H: Is a top-heavy IMF the cause of the ratios? | E: Qualitative assessment of six explanations | R: Other mechanisms judged unlikely; top-heavy IMF plausible | F: Consistent with top-heavy IMF; optical depth and recent starburst not fully excluded | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Radial flows, optical depth, photodissociation, fractionation and recent starburst considered; optical depth and recent star formation not fully excluded  
  > "although we cannot completely exclude optical depth effects, especially in Arp 220" (3.2 Optical Depth Effects)
- How they decided it was enough: _not stated_
- Limitation (authors): Optical depths not measured; multiple transitions needed  
  > "to properly test this assumption, observations of multiple line transitions are required to measure excitation conditions and derive the optical depths." (3.2 Optical Depth Effects)
- Caveat (inferred, ours): Interpretation is qualitative, with no abundance or radiative transfer modeling
- Caveat (inferred, ours): Differing uv coverage between lines and archival datasets may bias ratios
- Caveat (inferred, ours): Optically thick 13CO or C18O in Arp 220 could mimic the ratios

## Reproducibility

- Data public (paper): Archival ALMA data cited by project codes  
  > "This paper makes use of the following ALMA data:" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Mapping of projects to targets
- Missing: Cell, image size, uvtaper/uvrange values
- Missing: Clean masks
- Missing: Aperture and S/N cuts
- Data volume (inferred): ~100-300 GB across six projects
- Score (inferred): 3/5, Data public and CASA recipe partly given, but many imaging parameters and the project-target mapping are missing.
- Rediscovery candidate: yes, Public data, a simple imaging recipe, and numeric line ratios, though some settings are missing.

## Links

- Companion: Sliwa2017 (Previous ALMA study of IRAS 13120-5453 with low 13CO/C18O; its data is combined here)

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.00287.S"
 ],
 "codes_printed_but_missing": [
  "2015.1.00287.S"
 ],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 27,
  "rate": 0.409
 },
 "evidence_ok": true
}
```
