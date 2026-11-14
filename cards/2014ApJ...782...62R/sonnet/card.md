# Fast Radial Flows in Transition Disk Holes

`2014ApJ...782...62R` | The Astrophysical Journal 2014 | first author: Rosenfeld, Katherine A. | arXiv: 1312.3817 | DOI: 10.1088/0004-637X/782/2/62

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: Can fast (near free-fall) radial inflow inside transition disk cavities be detected through channel-map signatures, and does HD 142527 show it?  
  > "we ask here whether we can test observationally the idea that transition disk cavities have fast (nearly free-fall) radial flows." (INTRODUCTION)
- Target **HD 142527**: coordinates _not stated_; z/distance 145 ± 15 pc  
  > "At a distance of $d=145 \pm 15$ pc (cite: verhoeff11)" (3 A CASE STUDY: HD 142527); distance from Verhoeff et al. 2011  
  > "At a distance of $d=145 \pm 15$ pc (cite: verhoeff11)" (3 A CASE STUDY: HD 142527)

## Data provenance

- ALMA projects: 2011.0.00465.S
- bands: Band 7 (345 GHz)  
  > "ALMA Band 7 (345 GHz) observations presented by (cite: casassus13)" (3 A CASE STUDY: HD 142527)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthesized beam 0.64'' x 0.41'', PA = 75.5 deg  
  > "The large synthesized beam size (0.64$''$$\times$0.41$''$, PA = 75.5$^\circ$)" (3 A CASE STUDY: HD 142527)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival ALMA data, originally presented by Casassus et al. 2013  
  > "We apply the tools developed in §2 to the archival ALMA data on CO and HCO$^+$ line emission." (3 A CASE STUDY: HD 142527)
- Line: 12CO J=3-2 (not stated)
- Line: HCO+ J=4-3 (not stated)
- External data: Stellar mass of HD 142527  
  > "We also adopt literature values for the stellar mass (cite: casassus13) and viewing geometry for the outer disk (cite: fujiwara06; verhoeff11)." (3 A CASE STUDY: HD 142527) [from Casassus et al. 2013 (cite: casassus13)]
- External data: Outer disk viewing geometry (inclination, PA)  
  > "We also adopt literature values for the stellar mass (cite: casassus13) and viewing geometry for the outer disk (cite: fujiwara06; verhoeff11)." (3 A CASE STUDY: HD 142527) [from (cite: fujiwara06; verhoeff11)]
- Simulation/model as data: 3D LIME model disks with radial inflow parameter chi and inclination i, mock-imaged with CASA  
  > "We use the modeling capabilities of `LIME` (cite: brinch10) to simulate high-resolution channel maps assuming LTE conditions" (2 OBSERVATIONAL SIGNATURES OF RADIAL INFLOW)

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

- ALMA data reduction and imaging taken from Casassus et al. 2013 observations  
  > "our first-cut analysis of the (cite: casassus13) ALMA observations of the HD 142527 disk" (3 A CASE STUDY: HD 142527) [from (cite: casassus13)]

### Not stated but needed to reproduce (our reading)

- Calibration and imaging details (CASA version, weighting, continuum subtraction) for the archival data
- Which data products/images were used and the channel width
- Disk-mass-independent model details for the HD 142527 LIME model (abundance, scale height, turbulence)
- Outer disk inclination and PA values numerically (only i=160 deg appears) and stellar mass
- How centroids were measured on the real data

## Analysis recipe

1. **Build razor-thin and 3D LIME disk models with inflow**: Velocity field with inward radial component chi*vK inside R_cav; LIME channel maps, sampled and deconvolved in CASA  
  > "Both models treat the gas velocities within the cavity ($R<R_{\rm cav}$) as having an inward radial component that is some constant fraction $\chi$ of the local circular Keplerian velocity." (2 OBSERVATIONAL SIGNATURES OF RADIAL INFLOW)
   - software: LIME, CASA
   - parameter: 0.212 km/s spectral resolution, 0.1'' spatial resolution for mock data  
  > "spectral resolution of 0.212 km s$^{-1}$ and a spatial resolution of 0.1$''$" (2 OBSERVATIONAL SIGNATURES OF RADIAL INFLOW)
   - assumption: Axisymmetric inflow; LTE; no surface density reduction in cavity  
  > "Nevertheless we assume axisymmetry to gain a foothold on the problem." (2 OBSERVATIONAL SIGNATURES OF RADIAL INFLOW)
   - fitting: _not stated_
   - validation: Razor-thin predictions compared with 3D model  
  > "Note how $\max
|\Delta \theta'_{\rm sys}|$ is accurately predicted by the razor-thin model" (2.1 Twisted Isophotes at the Systemic Velocity)
2. **Measure wing rotation in HD 142527 CO channel maps**: Intensity-weighted centroids of channel pairs blue/red-shifted by equal velocity; angle of connecting segment compared with constant-chi, variable-chi and warp models  
  > "Pairs of these positions are constructed from channels blue- and red-shifted by the same velocity relative to the systemic channel." (2.2 Maximum LOS Velocities: Wing Rotation)
   - parameter: variable chi(R<140 AU) = [1+(R/33 AU)^6]^-1; warp i_rel=15 deg, Omega_rel=69 deg, R_w=25 AU  
  > "we ramp up the relative inclination linearly from 0 to its final value $i_{\rm rel} = 15\ensuremath{^\circ}$" (3 A CASE STUDY: HD 142527)
   - assumption: Fixed disk mass 0.1 Msun, R_s=50 AU, T=70(R/50 AU)^-0.7 K, truncation 300 AU; systemic velocity +3.64 km/s LSR  
  > "fixing in advance the disk mass ($0.1\,M_\odot$), scale radius ($R_s = 50$ AU), disk temperature ($T 
= 70 (R/50 \,{\rm AU})^{-0.7}$ K), and outer truncation radius (300 AU)" (3 A CASE STUDY: HD 142527)
   - fitting: No formal fit; models compared by eye  
  > "We aim here only for a first look at the kinematics, and so forego an extensive modeling effort, fixing in advance the disk mass" (A CASE STUDY: HD 142527)
   - validation: _not stated_

## Software

- **LIME** : Simulating high-resolution channel maps of model disks  
  > "We use the modeling capabilities of `LIME` (cite: brinch10) to simulate high-resolution channel maps" (2 OBSERVATIONAL SIGNATURES OF RADIAL INFLOW)
- **CASA** : Sampling and deconvolving model visibilities  
  > "We then use `CASA` to sample and deconvolve the Hanning-smoothed visibilities" (2 OBSERVATIONAL SIGNATURES OF RADIAL INFLOW)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Systemic velocity of HD 142527 (LSR) | +3.64 | not stated | km/s | 2 | the systemic velocity is +3.64 km s$^{-1}$ relative to the local standard of rest |
| Inflow parameter chi inside cavity | ~1 | not stated | dimensionless | 2 | which implies a radial speed comparable to Keplerian ($\chi \sim 1$) |
| Constant offset in wing rotation at low velocities | ~6 | not stated | degrees | 2 | a constant offset in $\Delta \theta'_{\rm
  wing}$ of about 6 degrees |

## Qualitative findings

- Free-fall-like inflow at ~25-50 AU is consistent with data, but a warp reproduces the rotations equally well  
  > "Nevertheless a warped disk at these radii can also reproduce the large, order-unity rotations seen in the CO and HCO$^+$ line wings." (CONCLUSIONS)

## Claim tuples

- H: Fast radial inflow produces detectable twisted isophotes and wing rotation | E: Razor-thin and LIME 3D models with chi variable | R: Rotation angles predicted and measurable for realistic beams and S/N | F: Signatures are detectable with ALMA | **supported**
- H: HD 142527 cavity hosts near-free-fall inflow | E: Compare CO wing rotation with inflow and warp models | R: Variable-chi inflow fits as well as a warp | F: Consistent with inflow but degenerate with a warp | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Warp, outflow, envelope infall, vertical structure and eccentricity considered as contaminants; eccentricity found not degenerate; warp is practically degenerate  
  > "the warp-induced changes in the channel maps are practically identical to those induced by a radial inflow." (2.3.4 A warp)
- How they decided it was enough: _not stated_
- Limitation (authors): Large beam precludes measuring systemic-velocity twist; first-cut analysis without extensive modeling  
  > "We aim here only for a first look at the kinematics, and so forego an extensive modeling effort" (3 A CASE STUDY: HD 142527)
- Caveat (inferred, ours): No quantitative fit or uncertainties for inflow vs warp
- Caveat (inferred, ours): Axisymmetric inflow assumed for strongly non-axisymmetric disk
- Caveat (inferred, ours): Model parameters fixed by hand

## Reproducibility

- Data public (paper): Archival ALMA data, project 2011.0.00465.S  
  > "We apply the tools developed in §2 to the archival ALMA data on CO and HCO$^+$ line emission." (3 A CASE STUDY: HD 142527)
- Products in archive: _not stated_
- Missing: Calibration/imaging parameters
- Missing: Exact model parameters and centroid procedure on data
- Missing: Numeric stellar mass, inclination, PA
- Data volume (inferred): ~10-50 GB
- Score (inferred): 2/5, Data public but recipe is qualitative, with parameters largely unstated and no formal fit.
- Rediscovery candidate: no, Recipe incomplete and results mostly qualitative.

## Links

- Method: Brinch & Hogerheijde 2010 (cite: brinch10) (LIME radiative transfer code)
- Companion: Casassus et al. 2013 (cite: casassus13) (Original presentation of the ALMA HD 142527 data)
- Companion: Fukagawa et al. 2013 (cite: fukagawa13) (Optically thin CO isotopologue observations supporting inflow)

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
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 62,
  "stated": 24,
  "rate": 0.387
 },
 "evidence_ok": true
}
```
