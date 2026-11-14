# Witnessing the Birth of the Red Sequence: ALMA High-resolution Imaging of [C II] and Dust in Two Interacting Ultra-red Starbursts at z = 4.425

`2016ApJ...827...34O` | The Astrophysical Journal 2016 | first author: Oteo, I. | arXiv: 1601.07549 | DOI: 10.3847/0004-637X/827/1/34

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the morphology, physical scale and dynamics of the gas ([CII]) and dust in the interacting starburst pair SGP38326 at z = 4.425, and are they consistent with dissipative mergers?  
  > "Our observations support a scenario where at least a subset of the most distant extreme starbursts are highly dissipative mergers of gas-rich galaxies." (abstract)
- Target **SGP38326 (HATLAS J000307-330250)**: coordinates _not stated_; z/distance z = 4.425  
  > "HATLAS J000307$-$330250, also known as SGP38326, one of our ultra-red starbursts confirmed to be at $z =
4.425$ via multi-CO line detection." (1 Introduction); distance from multi-CO line detection from ALMA 3mm spectral scan  
  > "HATLAS J000307$-$330250, also known as SGP38326, one of our ultra-red starbursts confirmed to be at $z =
4.425$ via multi-CO line detection." (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.00449.S, 2013.1.00001.S
- bands: 3mm spectral scan and 870 um (Band 7) continuum setup  
  > "spectral scans in the ALMA 3mm window" (2 ALMA data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 870um beam 0.16'' x 0.12''; CO(4-3) 1.5''x1.2''; CO(5-4) 1.1''x1.0''  
  > "The beam size of the 870$\mu$m observations is $0.16''
\times 0.12''$" (2 ALMA data)
- max recoverable scale: _not stated_
- sensitivity: 870um continuum rms 0.11 mJy/beam; [CII] 0.66 mJy/beam in 100 km/s channels; CO(4-3) 0.54 and CO(5-4) 0.64 mJy/beam in 50 km/s channels  
  > "The r.m.s. of the 870$\mu$m continuum map is $0.11 \, {\rm mJy \, beam^{-1}}$" (2 ALMA data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PIs A. Conley (2013.1.00449.S) and R.J. Ivison (2013.1.00001.S)  
  > "Project 2013.1.00001.S was a high-spatial resolution study of the dust continuum morphology at 870$\mu$m of a subsample of our ultra-red starbursts (PI. R.J. Ivison)" (2 ALMA data)
- Line: 12CO 4-3 (not stated)
- Line: 12CO 5-4 (not stated)
- Line: [CII] 158 um fine structure (not stated)
- Line: OH 2Pi1/2 J=3/2-1/2 doublet (163 um) (1834.74735 GHz)
- Other facility **Herschel-ATLAS (SPIRE)**: 250/350/500 um flux densities used for selection and SED  
  > "$S_{\rm 250 \mu
  m} = 28.6 \pm 5.2 \, {\rm mJy}$, $S_{\rm 350 \mu m} = 28.6 \pm 5.8
\, {\rm mJy}$, $S_{\rm 500 \mu m} = 46.2 \pm 6.8 \, {\rm mJy}$" (3 SGP38326)
- Other facility **SCUBA-2**: 870 um flux density 32.5 +/- 4.1 mJy  
  > "SGP38326 was subsequently observed with SCUBA-2 at 870 $\mu$m ($S_{\rm 870 \mu m} = 32.5 \pm 4.1 \, {\rm
  mJy}$)" (3 SGP38326)
- Other facility **VIKING**: near-IR non-detection used to argue against lensing  
  > "SGP38326 has no near-IR counterpart in the VIKING survey" (3 SGP38326)
- External data: Average CO line ratio L'CO(5-4)/L'CO(1-0) = 0.39 for SMGs  
  > "the average CO line ratio for SMGs (cite: Carilli2013ARA&A..51..105C), $L'_{\rm CO(5-4)} / L'_{\rm
  CO(1-0)} = 0.39$" (3.1 A massive molecular gas reservoir) [from (cite: Carilli2013ARA&A..51..105C)]
- External data: alpha_CO = 0.8  
  > "$\alpha_{\rm CO} = 0.8 M_\odot \, ({\rm K \, km \,
  s^{-1} \, pc^2})$, a value typically assumed for high-$z$ starbursts and local ULIRGs (cite: Downes1998ApJ...507..615D)" (3.1 A massive molecular gas reservoir) [from (cite: Downes1998ApJ...507..615D)]
- External data: Dust mass absorption coefficient kappa_850 = 0.077 m^2/kg  
  > "using a value of $\beta=2$ and $\kappa_{850}=0.077\,{\rm m}^2/{\rm kg}^{-1}$ (cite: Dunne2001MNRAS.327..697D)" (3.3 Dust properties and SED fitting) [from (cite: Dunne2001MNRAS.327..697D)]
- External data: Flux-density to LIR conversion at z=4.425 from average ALESS SMG FIR SED  
  > "derived from the average FIR SED of SMGs in ALESS (cite: Swinbank2014MNRAS.438.1267S)" (3.7 The spatially resolved L[CII]/LIR ratio) [from (cite: Swinbank2014MNRAS.438.1267S)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline plus ALMA calibration scripts depending on release date; minor extra flagging  
  > "calibrated by using the ALMA pipeline and by executing different ALMA calibration scripts depending on the date when the data were released" (2 ALMA data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA imaging, natural weighting  
  > "The calibrated visibilities of the science target were then imaged in CASA by using a natural weighting scheme to maximize sensitivity." (2 ALMA data)
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

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- Flux, bandpass and phase calibrators
- Cell size, image size, cleaning threshold, masks
- Continuum subtraction and line-free channels
- Velocity-field fitting code and disk+halo model details
- Deblending details for dust and CO components
- Rest frequency for [CII] and moment-map clipping
- SED fitting code and priors

## Analysis recipe

1. **calibrate and image ALMA data**: ALMA pipeline/scripts calibration, CASA imaging with natural weighting  
  > "The calibrated visibilities of the science target were then imaged in CASA by using a natural weighting scheme to maximize sensitivity." (2 ALMA data)
   - software: CASA
   - fitting: _not stated_
   - validation: Visual inspection of calibrated visibilities  
  > "The calibrated visibilities for the calibrators and science target were visually inspected and only very minor further flagging was required." (2 ALMA data)
2. **measure dust and [CII] sizes**: 2D elliptical gaussian fits, A = pi R1 R2 with R=FWHM/2  
  > "the areas are calculated by carrying out 2D elliptical gaussian fits and using $A = \pi \times R_1 \times R_2$" (1 Introduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **derive molecular gas masses**: CO(5-4) luminosity converted with fixed line ratio and alpha_CO  
  > "The molecular gas masses are then calculated using $\alpha_{\rm CO} = 0.8 M_\odot \, ({\rm K \, km \,
  s^{-1} \, pc^2})$" (3.1 A massive molecular gas reservoir)
   - assumption: L'CO(5-4)/L'CO(1-0)=0.39; alpha_CO=0.8  
  > "we need to assume that the average CO line ratio for SMGs (cite: Carilli2013ARA&A..51..105C), $L'_{\rm CO(5-4)} / L'_{\rm
  CO(1-0)} = 0.39$, is valid for SGP38326" (3.1 A massive molecular gas reservoir)
   - fitting: _not stated_
   - validation: _not stated_
4. **SED fit for dust temperature, mass, LIR**: Modified blackbody fits (optically thin and thick) to global SED; split by 870um flux ratio between components  
  > "we fit the global SED of both sources using both optically thin and optically thick modified black bodies to derive the dust temperatures and dust masses" (3.3 Dust properties and SED fitting)
   - parameter: beta=2, kappa_850=0.077 m^2/kg  
  > "using a value of $\beta=2$ and $\kappa_{850}=0.077\,{\rm m}^2/{\rm kg}^{-1}$" (3.3 Dust properties and SED fitting)
   - assumption: Both sources have the same SED shape  
  > "we have assumed they have the same SED shape and split the IR luminosity and dust mass in the ratio of the 870$\mu$m fluxes" (3.3 Dust properties and SED fitting)
   - fitting: _not stated_
   - validation: Both optically thin and thick models give acceptable fits with comparable LIR  
  > "both produce acceptable fits with comparable $\rm{L_{IR}}$" (3.3 Dust properties and SED fitting)
5. **[CII] kinematics, dynamical masses and Toomre Q**: Velocity field fitted with disk plus dark matter halo model; isotropic virial estimator; Toomre Q following Swinbank et al. 2015  
  > "We have fitted the observed velocity field using a disk plus dark matter halo model." (3.6 Dynamics)
   - fitting: _not stated_
   - validation: Disk+halo model is degenerate as rotation curve does not turn over  
  > "since the rotation curve does not turn over, the disk+halo model is degenerate" (3.6 Dynamics)
6. **resolved L[CII]/LIR map**: Divide L[CII] map (from moment-0) by LIR map (from 870um continuum via ALESS SED conversion); rebin by 5 pixels  
  > "We have obtained the $L_{\rm [CII]}/L_{\rm IR}$ ratio map by simply dividing the $L_{\rm [CII]}$ and $L_{\rm IR}$ maps." (3.7 The spatially resolved L[CII]/LIR ratio)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : imaging of calibrated visibilities  
  > "The calibrated visibilities of the science target were then imaged in CASA" (2 ALMA data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [CII] size SMG1 | 3.8 x 2.9 | ±0.1 x ±0.1 | kpc | 2 | The size of the \[CII\] emission is $3.8 \pm 0.1 \, {\rm kpc}
\times 2.9 \pm 0.1 \, {\rm kpc}$ in SMG1 |
| dust size SMG1 | 2.2 x 2.0 | ±0.2 x ±0.2 | kpc | 2 | $2.2 \pm 0.2 \,{\rm kpc} \times 2.0 \pm 0.2 \,{\rm kpc}$ in SMG1 |
| Toomre Q SMG1 | ~0.22 | not stated | dimensionless | 5 | We obtain $Q^{\rm SMG1} \sim 0.22$ and $Q^{\rm SMG2} \sim 0.35$ |
| dynamical mass SMG1 from disk model | ~5e10 | factor ~2 | Msun | 5 | This suggests a dynamical mass $M_{\rm dyn,\, SMG1} \sim 5
\times 10^{10} \, M_\odot$ |
| molecular gas mass SMG1 | ~1.9e11 | not stated | Msun | 3 | $M_{\rm H_2} \, [M_\odot]$ / $\sim 1.9 \times 10^{11}$ |
| SFR surface density SMG1 | ~840 | not stated | Msun/yr/kpc^2 | 2 | $\Sigma_{\rm SFR} \sim 840\, {\rm
  M_\odot \, yr^{-1} \, kpc^{-2}}$ |
| dust temperature (optically thin) | 33 | ±2 | K | 4 | The optically thin model gives a best fit temperature of $33\pm 2$ K |
| [CII] redshifts | SMG1 4.4237, SMG2 4.4289 | ±0.0004 | dimensionless | 0 | $z_{\rm SMG1} = 4.4237 \pm 0.0004$ and $z_{\rm SMG2} = 4.4289 \pm
0.0004$ |

## Qualitative findings

- Dust is smooth while [CII] is more irregular and more extended  
  > "the smooth distribution of the continuum emission from cool dust grains contrasts with the more irregular morphology of the gas" (abstract)
- L[CII]/LIR is lower in centres and higher in outskirts  
  > "the $L_{\rm [CII]} / L_{\rm IR}$ ratio is lower in the center of the galaxies and higher in the outer parts" (4 Conclusions)

## Claim tuples

- H: Does gas ([CII]) trace a different morphology and scale than dust? | E: 2D gaussian fits to 0.1'' [CII] and 870um maps | R: [CII] 3.8x2.9 kpc vs dust 2.2x2.0 kpc in SMG1 | F: Gas is more extended and irregular than dust | **supported**
- H: Are the components ordered rotating disks and stable? | E: [CII] velocity field analysis and Toomre Q | R: Ordered rotation, Q ~0.22 and ~0.35 | F: Disk-like rotation but turbulent and unstable | **supported**
- H: Is SGP38326 a highly dissipative merger of gas-rich galaxies? | E: Combined morphology, kinematics, velocity offset vs escape velocity | R: Offset ~300 km/s far below escape velocity | F: Supports dissipative gas-rich merger scenario | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Lensing considered and rejected from lack of VIKING counterpart and no lensing signature in dust morphology  
  > "Therefore, neither of the two merging components is lensed" (3 SGP38326)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas mass from a single mid-J CO line is highly uncertain; low-J CO needed  
  > "the calculation of the molecular gas mass from a single mid-$J$ transition might be highly uncertain" (3.1 A massive molecular gas reservoir)
- Caveat (inferred, ours): Dynamical mass is degenerate and 5x below gas mass
- Caveat (inferred, ours): Toomre Q depends on assumed CO ratio and alpha_CO
- Caveat (inferred, ours): Dust and gas masses depend on assumed temperature/opacity
- Caveat (inferred, ours): No kinematic fitting code or uncertainties described

## Reproducibility

- Data public (paper): Cited as ALMA data from two projects; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00001.S and ADS/JAO.ALMA#2013.1.00449.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Kinematic modelling details
- Missing: SED fitting code and data
- Missing: Component flux extraction details
- Data volume (inferred): ~50-200 GB raw for two ALMA projects
- Score (inferred): 4/5, ALMA codes given but imaging and modelling details are sparse.
- Rediscovery candidate: no, Recipe incomplete, especially kinematic modelling and imaging parameters.

## Links

- Method: (cite: Swinbank2015ApJ...806L..17S) (Toomre Q calculation)
- Method: (cite: Swinbank2014MNRAS.438.1267S) (ALESS SED for flux to LIR conversion)
- Related: H-ATLAS
- Related: HerMES
- Related: ALESS

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 34,
  "rate": 0.447
 },
 "evidence_ok": true
}
```
