# Polarized emission by aligned grains in the Mie regime: Application to protoplanetary disks observed by ALMA

`2020A&A...634L..15G` | Astronomy and Astrophysics 2020 | first author: Guillet, V. | arXiv: 2001.08400 | DOI: 10.1051/0004-6361/201937314

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: Can polarized emission by aligned grains in the Mie regime become negative (parallel to B-field) at mm wavelengths and explain azimuthal polarization patterns in ALMA disk observations?  
  > "We study the dust polarization properties of aligned grains in emission in the Mie regime, *i.e.* when the mean grain size approches the wavelength." (abstract)
- Target **[BHB2007] 11**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01186.S, 2013.1.000291.S
- bands: Bands 7, 6 and 3 (0.87, 1.3, 3.1 mm) for [BHB2007] 11  
  > "The averaged polarization fraction is 7.5$\pm$1.3%, 5.7$\pm$1.1% and 4.3$\pm$0.6% at 3.1, 1.3 and 0.87 mm, respectively." (3.2 [BHB2007] 11)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: common synthesized beam 0.20''x0.15'', PA -80 deg  
  > "producing a common synthesized beam of $0.20''\times0.15''$ with a position angle of $-80^{\circ}$ for the three bands" (3.2 [BHB2007] 11)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- External data: ALMA multiwavelength polarization observations of [BHB2007] 11  
  > "ALMA multi-wavelength polarization observations shows polarization within circumbinary disk (cite: Alves18)." (3.2 [BHB2007] 11) [from Alves et al. 2018 (cite: Alves18)]
- External data: Optical constants of astronomical silicates  
  > "We use the so-called "astronomical silicates" (cite: DL84) characterized by a constant spectral index $\beta=2$" (2.1 Dust model) [from (cite: DL84)]
- Simulation/model as data: DustEM + T-MATRIX polarized emission models for oblate (b/a=1.1) and prolate (b/a=0.9) astrosilicate grains, log-normal and MRN-like size distributions, a_peak 10 um-1 mm, ISRF G0=100  
  > "calculations were done for 400 grain sizes between $0.3\,\mu$m and 3 mm." (2.1 Dust model)

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
- weighting robust: smaller robust than Alves et al. 2018 (value not given), same visibility range  
  > "using the same visibility range as in (cite: Alves18) but with a smaller robust weighting" (3.2 [BHB2007] 11)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: beam-matched maps in three bands  
  > "We built beam-matching maps obtained in the three bands" (3.2 [BHB2007] 11)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Visibility range and data of [BHB2007] 11 observations  
  > "using the same visibility range as in (cite: Alves18)" (3.2 [BHB2007] 11) [from (cite: Alves18)]
- Filament definition for polarization measurement  
  > "along the two main filaments detected by (cite: Alves19)" (3.2 [BHB2007] 11) [from (cite: Alves19)]

### Not stated but needed to reproduce (our reading)

- Robust value used for beam-matched maps
- Pixel/region selection along filaments
- Polarization debiasing method
- Exact DustEM/T-MATRIX versions and input files
- Source distance

## Analysis recipe

1. **Model polarization fraction vs wavelength**: T-MATRIX cross-sections fed to DustEM for size distributions of aligned spheroids  
  > "The grain absorption and scattering cross-sections were computed with the `T-MATRIX` code" (2.1 Dust model)
   - software: T-MATRIX, DustEM
   - parameter: log-normal sigma=0.1; MRN-like a^-3.5; b/a=1.1 or 0.9; G0=100  
  > "with $\sigma=0.1$, for different mean size $a_{\rm peak}$ ranging from $10\,\mu$m to 1 mm." (2.2 Effect of the size distribution with a magnetic field in the plane of the sky)
   - assumption: Perfect alignment, homogeneous compact astrosilicate grains  
  > "We restrict our analysis to homogeneous and compact grains." (2.1 Dust model)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure polarization fraction in BHB2007 11 and compare to models**: Average polarization fraction along two filaments in beam-matched maps in three bands  
  > "We measured the polarization fraction in the three bands along the two main filaments detected by (cite: Alves19)" (3.2 [BHB2007] 11)
   - fitting: _not stated_
   - validation: Qualitative comparison with model curves  
  > "is in rough agreement with the negative regime of large, almost single-sized, grains" (3.2 [BHB2007] 11)

## Software

- **DustEM** : Dust emission and polarization of size distributions  
  > "We use the `DustEM` tool (cite: Compiegne2011; Guillet2018) to predict the polarized emission of a size distribution of grains." (2.1 Dust model)
- **T-MATRIX** : Grain cross-sections for spheroids  
  > "The grain absorption and scattering cross-sections were computed with the `T-MATRIX` code" (2.1 Dust model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean polarization fraction at 3.1 mm | 7.5 | 1.3 | % | 2 | The averaged polarization fraction is 7.5$\pm$1.3%, 5.7$\pm$1.1% and 4.3$\pm$0.6% at 3.1, 1.3 and 0.87 mm, respectively. |
| Mean polarization fraction at 1.3 mm | 5.7 | 1.1 | % | 2 | The averaged polarization fraction is 7.5$\pm$1.3%, 5.7$\pm$1.1% and 4.3$\pm$0.6% at 3.1, 1.3 and 0.87 mm, respectively. |
| Mean polarization fraction at 0.87 mm | 4.3 | 0.6 | % | 2 | The averaged polarization fraction is 7.5$\pm$1.3%, 5.7$\pm$1.1% and 4.3$\pm$0.6% at 3.1, 1.3 and 0.87 mm, respectively. |

## Qualitative findings

- Polarization becomes negative for grains larger than ~250 um, with transition near lambda ~1 mm  
  > "The transition from the positive to the negative polarization occurs at a wavelength $\lambda \sim 1$ mm." (abstract)

## Claim tuples

- H: Aligned grains in Mie regime can produce polarization parallel to B | E: DustEM/T-MATRIX calculations for spheroidal astrosilicate grains | R: Negative polarization for grains larger than ~250 um; transition at ~1 mm | F: Azimuthal patterns in some disks may still trace toroidal B-fields | **supported**
- H: BHB2007 11 multi-band polarization is explained by Mie negative polarization | E: Compared measured fractions in three bands with models | R: Frequency dependence incompatible with positive regime; roughly matches negative regime | F: Large (>~500 um) near single-size grains suggested | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Only homogeneous compact weakly elongated grains; no fluffy aggregates or self-scattering  
  > "Our modeling was restricted to homogeneous, compact, weakly elongated grains." (Why a negative polarization ?)
- Caveat (inferred, ours): Comparison to data is qualitative, no fit
- Caveat (inferred, ours): Self-scattering not included
- Caveat (inferred, ours): Only silicate composition tested

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Reduced ALMA maps and robust value
- Missing: Model grids/inputs
- Data volume (inferred): tens of GB for ALMA data (three bands polarization)
- Score (inferred): 3/5, Models reproducible in principle with public codes, but ALMA part is brief and inherited.
- Rediscovery candidate: no, ALMA analysis is minor and details are inherited or unstated.

## Links

- Method: Guillet et al. 2018 (cite: Guillet2018) (Dust polarization model basis)
- Companion: Alves et al. 2018 (cite: Alves18) (Original BHB2007 11 ALMA polarization data)

## Checks

```json
{
 "quotes": 27,
 "quotes_ok": 27,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2013.1.000291.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 60,
  "stated": 19,
  "rate": 0.317
 },
 "evidence_ok": true
}
```
