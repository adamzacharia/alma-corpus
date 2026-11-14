# An Introduction to Dust Evolution and Vertical Transport in Protoplanetary Disks

`2025PASP..137j3001V` | Publications of the Astronomical Society of the Pacific 2025 | first author: Villenave, Marion | arXiv: 2509.10614 | DOI: 10.1088/1538-3873/ae05cb

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: Tutorial review of how multi-wavelength, spatially resolved observations constrain dust grain sizes, dust settling and vertical extent in protoplanetary disks  
  > "Spatially resolved observations of disks at multiple wavelengths can allow to infer the distribution of various dust grains and gas species." (abstract); "by better characterizing the disk vertical structure, observations help to constrain the level of vertical settling and identify regions of high dust density" (abstract)

## Data provenance

- ALMA projects: 2017.1.00712.S, 2019.1.00261.L, 2017.1.01701.S
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
- External data: Dust opacity tables for astronomical silicates (Laor & Draine) used for the opacity figures  
  > "We used the dust opacities for astronomical silicates from the tables published by (cite: Laor_Draine_1993)" (Dust opacities) [from (cite: Laor_Draine_1993)]
- Simulation/model as data: mcfost radiative transfer models of an edge-on disk at 0.89 mm (not beam-convolved), varying dust scale height, dust mass and inclination, used to illustrate edge-on disk appearance  
  > "we produced models with the radiative transfer code `mcfost` (cite: Pinte_2006; Pinte_2009)" (Dust at millimeter wavelengths); "generated images at 0.89 mm for models viewed at an inclination of 90$^\circ$ and 85$^\circ$" (Dust at millimeter wavelengths)

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

- Focus on integrated major and minor axis profiles of the edge-on models, following previous works  
  > "We focus on the size and shape of the integrated major and minor axis profiles, as in previous works (cite: Villenave_2020; Tazaki_2024)." (Dust at millimeter wavelengths) [from (cite: Villenave_2020; Tazaki_2024)]

### Not stated but needed to reproduce (our reading)

- Which figures (if any) display the three listed ALMA projects, and the calibration, imaging, self-calibration and beam parameters of those images
- mcfost version, stellar parameters, dust composition and opacity law, temperature/radiative transfer settings, and photon numbers for the Figure 7 models
- How the Figure 9 emission-height and scattered-light-height curves were extracted or adapted from the cited work
- Dust composition and size-grid settings behind Figures 1-3 beyond the Laor and Draine silicate tables

## Analysis recipe

1. **Model edge-on disk appearance at 0.89 mm with radiative transfer**: mcfost models of an edge-on disk around a young sun-like star at 140 pc, varying dust scale height, dust mass and inclination, imaged at 0.89 mm without beam convolution; major and minor axis profiles compared  
  > "We consider a disk around a young sun like star located at 140 pc with material located between 1 au and 100 au." (Dust at millimeter wavelengths); "We focus on the size and shape of the integrated major and minor axis profiles, as in previous works (cite: Villenave_2020; Tazaki_2024)." (Dust at millimeter wavelengths)
   - software: mcfost
   - parameter: Surface density Sigma ~ r^-1; H_d = H_0 (r/100 au)^1.125; H_0 = 10, 3, 1 au at 100 au  
  > "The surface density of the disk follows $\Sigma\propto r^{-1}$, while its vertical extent is characterized by $H_d=H_0(r/100\text{ au})^{1.125}$." (Dust at millimeter wavelengths); "We produced models with a dust and gas scale height of $H_0=10$ au, 3 au, and 1 au at the reference radius of 100 au." (Dust at millimeter wavelengths)
   - parameter: Dust mass 1e-5, 1e-4, 1e-3 Msun (Light, Moderate mass, Massive models)  
  > "The dust mass is also varied between $10^{-5}$ M$_\odot$, $10^{-4}$ M$_\odot$, and $10^{-3}$ M$_\odot$, respectively for the Light, Moderate mass, and Massive models." (Dust at millimeter wavelengths)
   - parameter: Inclinations 90 and 85 deg; images at 0.89 mm  
  > "generated images at 0.89 mm for models viewed at an inclination of 90$^\circ$ and 85$^\circ$" (Dust at millimeter wavelengths)
   - assumption: Well mixed dust and gas; grain sizes 0.03 micron to 1 mm with size exponent p = 3.5  
  > "We assumed a well mixed dust and gas distribution, with particules between 0.03 $\mu$m and 1 mm following a typical exponent of $p=3.5$" (Dust at millimeter wavelengths)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **mcfost** : Radiative transfer models of edge-on disks at 0.89 mm  
  > "we produced models with the radiative transfer code `mcfost` (cite: Pinte_2006; Pinte_2009)" (Dust at millimeter wavelengths)
- **disksurf** : Public implementation of the molecular emission height method (mentioned, not used by this paper)  
  > "Numerical implementations of this method are publicly available in softwares such as `disksurf` (cite: Teague_2019), `DISCMINER` (cite: Izquierdo_2021; Izquierdo_2023), or `ALFAHOR` (cite: PanequeCarreno_2023)." (Molecular gas emission)
- **DISCMINER** : Public implementation of the molecular emission height method (mentioned, not used by this paper)  
  > "Numerical implementations of this method are publicly available in softwares such as `disksurf` (cite: Teague_2019), `DISCMINER` (cite: Izquierdo_2021; Izquierdo_2023), or `ALFAHOR` (cite: PanequeCarreno_2023)." (Molecular gas emission)
- **ALFAHOR** : Public implementation of the molecular emission height method (mentioned, not used by this paper)  
  > "Numerical implementations of this method are publicly available in softwares such as `disksurf` (cite: Teague_2019), `DISCMINER` (cite: Izquierdo_2021; Izquierdo_2023), or `ALFAHOR` (cite: PanequeCarreno_2023)." (Molecular gas emission)
- **DRAGyS** : Public implementation of the scattered-light height offset method (mentioned, not used by this paper)  
  > "A numerical implementation of this method is publicly available in the `DRAGyS` software (cite: Roumesy_2025)." (Dust in the optical to near infrared)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Grain sizes dominating emission at 1 micron (compact silicate spheres) | 0.1 to 1 | not stated | micron | 0 | we can see directly that emission at 1 $\mu$m is dominated by grains between 0.1 and 1 $\mu$m |
| Grain sizes dominating emission at 1.3 mm (compact silicate spheres) | 100 to 500 | not stated | micron | 0 | while emission at 1.3 mm would instead be dominated by grains between 100 and 500 $\mu$m |

## Qualitative findings

- Millimeter dust is often vertically settled in outer regions of Class II disks, while settling may be less efficient in younger systems  
  > "millimeter dust grains are often found to be affected by vertical settling in the outer regions of Class II protoplanetary disks, while settling might be less efficient in younger systems" (Summary and outlook)
- Maximum grain sizes are not necessarily larger in rings than elsewhere in the disk, depending on the system  
  > "Grains are not necessarily larger in rings than in other regions of the disks, depending on the system." (Summary and outlook)

## Claim tuples

- H: Do edge-on disk morphologies at millimeter wavelengths distinguish vertically thin from thick dust? | E: mcfost models at 0.89 mm varying dust scale height, dust mass and inclination | R: Dust mass and scale height act alike on the minor axis profile but oppositely on the major axis profile | F: A flat topped major axis with a vertically thin minor axis indicates a massive, vertically thin disk | **supported**
- H: Does including scattering change the expected millimeter intensity of disks? | E: Compared intensity with and without scattering as a function of optical depth and albedo (Figure 5) | R: Little change in most of parameter space; scattering lowers intensity for optically thick, high-albedo dust | F: Scattering can explain spectral indices below 2 | **supported**
- H: What do resolved multi-wavelength analyses say about maximum grain size in disks? | E: Review of studies using the scattering-inclusive radial SED analysis | R: Maximum grain sizes from a few centimeters to a few hundreds of microns, assuming compact grains | F: Some rings favor grain growth while others show no increase, possibly fragmentation limited | **partially**
- H: Is the outer disk of Class II systems vertically settled at millimeter wavelengths? | E: Review of gap and outer edge minor-axis versus major-axis analyses | R: Most systems have dust aspect ratio h_mm/r below 0.05, as low as 0.005 | F: Outer regions of Class II disks are significantly affected by vertical settling | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Tutorial aims to explain a technique using radially resolved multi-wavelength millimeter observations to constrain disk and dust properties  
  > "Here, we aim to provide further insights on a technique recently used on high angular resolution, millimeter range, observations of disks to provide radially resolved constraints on disk and dust properties." (Observational constraints on dust sizes)
- How they decided it was enough: _not stated_
- Limitation (authors): The scattering equation is valid only for low inclination systems  
  > "this equation is only valid for low inclination systems." (Considering scattering)
- Limitation (authors): Radial SED analysis depends on multiple parameters rarely studied simultaneously  
  > "The analysis however depends on multiple parameters which have rarely been studied simultaneously." (Considering scattering)
- Caveat (inferred, ours): Tutorial review: ALMA data are only acknowledged, with no stated link between the project codes and specific figures or analyses
- Caveat (inferred, ours): Illustrative mcfost models lack full setup (version, composition, stellar parameters)

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Mapping of ALMA projects to figures and any processing used
- Missing: mcfost parameter file and version for Figure 7
- Missing: Dust composition and size grids for the opacity figures
- Data volume (inferred): Negligible for the illustrative models; ALMA data volume for the three listed projects not stated and not needed for the tutorial's content
- Score (inferred): 2/5, Illustrative mcfost models are described with main parameters, but no ALMA analysis is given and several model settings are missing
- Rediscovery candidate: no, Tutorial with no ALMA data analysis recipe or numeric results to reproduce

## Links

- Method: (cite: Sierra_2019) (Source of the scattering-inclusive intensity equation used for radially resolved multi-wavelength analysis)
- Method: (cite: Pinte_2018) (Geometrical method for molecular emission heights)
- Method: (cite: Birnstiel_2024) (Review of dust evolution theory recommended for details)
- Companion: (cite: Villenave_2020) (Edge-on disk millimeter major and minor axis analysis followed here)
- Companion: (cite: Tazaki_2024) (Vertically resolved HH 30 modeling confirming settling)
- Related: DSHARP
- Related: eDISK
- Related: MAPS
- Related: DiskStrat

## Checks

```json
{
 "quotes": 35,
 "quotes_ok": 35,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 59,
  "stated": 19,
  "rate": 0.322
 },
 "evidence_ok": true
}
```
