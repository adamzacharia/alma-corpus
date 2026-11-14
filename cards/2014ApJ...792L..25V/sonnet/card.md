# Spatially Resolved HCN J = 4-3 and CS J = 7-6 Emission from the Disk around HD 142527

`2014ApJ...792L..25V` | The Astrophysical Journal Letters 2014 | first author: van der Plas, G. | arXiv: 1407.1735 | DOI: 10.1088/2041-8205/792/2/L25

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Do HCN J=4-3 and CS J=7-6 trace the HD 142527 disk, and why is their emission suppressed under the horseshoe-shaped continuum peak?  
  > "Both emission lines are azimuthally asymmetric and are suppressed under the horseshoe-shaped continuum emission peak." (abstract)
- Target **HD 142527**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00465.S
- bands: Band 7 (continuum)  
  > "The band 7 continuum is of similar size of the beam" (Optically thick continuum)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.56'' x 0.35'', PA 67 deg  
  > "with a synthesized beam size of 0.56$\ensuremath{''}$ $\times$ 0.35$\ensuremath{''}$ and a PA of 67$^{\circ}$" (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: 12 mJy/channel RMS  
  > "CLEANed to a RMS noise level of 12 mJy / channel" (Observations and data reduction)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: HCN J=4-3 (354.50547 GHz)
- Line: CS J=7-6 (342.88286 GHz)
- External data: HCN J=3-2 2 sigma upper limit of 0.77 Jy km/s  
  > "report a 2$\sigma$ upper limit of 0.77 Jy km s$^{-1}$) on the HCN J=3–2 emission line" (3.2 HCN J=4-3) [from (cite: 2011ApJ...734...98O)]
- External data: Dust mass 1.0e-3 Msun and max opacity tau=2.76 at 850 um  
  > "a dust mass of 1.0 $\times$ 10$^{-3}$ M$_{\odot}$ is required." (Optically thick continuum) [from (cite: 2011A&A...528A..91V)]

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

- task: CLEAN in CASA  
  > "imaging of the CS and HCN lines was performed using the CLEAN task in `CASA`" (Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Default visibility-domain subtraction left negative residuals near CS; average artifact from channels at -6 to 1 and 6 to 13 km/s subtracted from all CS channels  
  > "We subtract this average from all spectral channels used in our analysis of the CS J=7–6 line." (Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.56'' x 0.35'', PA 67 deg  
  > "with a synthesized beam size of 0.56$\ensuremath{''}$ $\times$ 0.35$\ensuremath{''}$ and a PA of 67$^{\circ}$" (Observations and data reduction)
- final rms: 12 mJy/channel (0.214 km/s channels)  
  > "binned in spectral channels of width 0.214 km s$^{-1}$ and CLEANed to a RMS noise level of 12 mJy / channel" (Observations and data reduction)

### Inherited from earlier work

- Observing strategy and data reduction  
  > "For the observing strategy and data reduction we refer to (cite: 2013Natur.493..191C)." (Observations and data reduction) [from (cite: 2013Natur.493..191C)]
- Disk inclination 28 deg adopted  
  > "For the analysis presented in this manuscript we adopt the latter value of the disk inclination." (Introduction) [from (cite: seba-paper)]

### Not stated but needed to reproduce (our reading)

- Array configurations, observing dates, time on source, calibrators
- CASA version and calibration details
- CLEAN weighting, robust, cell and image size, masks
- Spectral window setup
- Continuum-subtraction line-free channels used by default
- Moment map methods and thresholds
- MCFOST model details beyond parameter ranges
- Distance to HD 142527

## Analysis recipe

1. **Image lines**: CLEAN of CS and HCN lines with continuum subtraction and correction of residual artifact  
  > "imaging of the CS and HCN lines was performed using the CLEAN task in `CASA`" (Observations and data reduction)
   - software: CASA
   - parameter: 0.214 km/s channels  
  > "binned in spectral channels of width 0.214 km s$^{-1}$" (Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure line fluxes, widths and azimuthal variation**: Integrated line profiles, moment maps and azimuthal/radial intensity cuts  
  > "We show the CS J=7–6 and HCN J=4–3 integrated intensity, velocity and peak intensity maps in Figure [1](#fig:momentsCS)" (Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Test inner-rim projection hypothesis with radiative transfer**: MCFOST disk models varying inner-rim dust mass, CS abundance and dust-to-gas ratio  
  > "we vary the dust mass m$_{dust}$, the CS abundance $\epsilon_{\mathrm{CS}}$ and the dust to gas ratio $\delta$." (Optically thick continuum)
   - software: MCFOST
   - parameter: m_dust 6.6e-4 to 4.5e-2 Msun; eps_CS 3.5e-9 to 3.5e-11; delta 1 to 100  
  > "$\epsilon_{\mathrm{CS}}$ between 3.5e-9 and 3.5 e-11, and $\delta$ between 1 and 100" (Optically thick continuum)
   - assumption: Same inclination, PA and mass as HD 142527  
  > "the same disk inclination, PA, and mass, consisting of an inner disk, a disk gap and an outer disk" (Optically thick continuum)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : CLEAN imaging  
  > "using the CLEAN task in `CASA`" (Observations and data reduction)
- **MCFOST** : Radiative transfer test of shadowing by optically thick ring  
  > "we use the radiative transfer model code MCFOST" (Optically thick continuum)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CS J=7-6 integrated flux | 1.67 | 0.08 | Jy km/s | 2 | an integrated flux of 1.67$\pm$0.08 Jy km s$^{-1}$ |
| CS J=7-6 FWHM | 2.71 | 0.21 | km/s | 2 | FWHM of 2.71 $\pm$ 0.21 km s$^{-1}$ |
| HCN J=4-3 integrated flux | 1.73 | 0.05 | Jy km/s | 2 | integrated flux of 1.73 $\pm$ 0.05 Jy km s$^{-1}$ |
| HCN J=4-3 FWHM | 2.52 | 0.21 | km/s | 2 | The line FWHM is 2.52 $\pm$ 0.21 km s$^{-1}$ |
| CS flux increase after artifact removal | 38 | not stated | percent | 1 | increasing the integrated CS J=7–6 line flux by 38% |
| Minimum Tex for HCN 3-2 upper limit consistency | >=30 | not stated | K | 2 | consistent with the HCN J=4–3 detection if the excitation temperature is T$_{ex}~\geq$ 30 K |

## Qualitative findings

- First detection of CS J=7-6 from a protoplanetary disk  
  > "This is the first detection of CS J=7–6 coming from a protoplanetary disk." (abstract)
- No counterpart of CS/HCN emission to the scattered-light and CO spiral structure  
  > "We see no counterpart for the CS and HCN emission with the spiral structure seen in scattered light and CO rotational lines." (Results)

## Claim tuples

- H: Are CS and HCN emission detected and azimuthally asymmetric? | E: ALMA Band 7 line imaging | R: Both detected, strongest to the southwest, suppressed under continuum peak | F: Emission is anticorrelated with the dust trap | **supported**
- H: Is the asymmetry due to line-of-sight projection of the inner rim? | E: Orientation argument plus MCFOST model grid | R: No models gave a brighter near side of the inner edge | F: Projection of the inner rim is discarded | **supported**
- H: Does the dust trap cause the decrement? | E: Qualitative discussion of temperature, freeze-out and continuum opacity | R: Lower dust/gas temperature and optically thick continuum are plausible | F: Two possible mechanisms are suggested, not tested quantitatively | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Inner-rim line-of-sight projection rejected  
  > "rule out emission from the inner rim of the outer disk inclined into the line of sight as source for the brightness asymmetry" (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust-trap effect on gas temperature not modelled  
  > "Modeling the effect of a dust trap on the local gas temperature is beyond the scope of this manuscript." (4.1 Temperature and chemistry)
- Caveat (inferred, ours): Mechanisms are qualitative with no chemical modelling
- Caveat (inferred, ours): Single dataset, no independent line-formation temperature
- Caveat (inferred, ours): Brightness temperature estimate uses a coarse beam

## Reproducibility

- Data public (paper): ALMA project 2011.0.00465.S cited  
  > "This paper makes use of the following ALMA data:\ `ADS/JAO.ALMA#2011.0.00465.S`." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Calibration details
- Missing: MCFOST model files
- Data volume (inferred): tens of GB (Cycle 0 Band 7 dataset)
- Score (inferred): 4/5, Short letter that defers reduction to earlier paper and gives few imaging details; flux numbers are checkable though.
- Rediscovery candidate: no, Recipe incomplete and the main interpretation is qualitative.

## Links

- Method: (cite: 2013Natur.493..191C) (Observing strategy and data reduction)
- Companion: (cite: valentin-paper) (CO spiral arms and channel-averaged visibility discretization)
- Companion: (cite: seba-paper) (Disk inclination and 13CO/C18O results)

## Checks

```json
{
 "quotes": 38,
 "quotes_ok": 38,
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
  "facts": 65,
  "stated": 25,
  "rate": 0.385
 },
 "evidence_ok": true
}
```
