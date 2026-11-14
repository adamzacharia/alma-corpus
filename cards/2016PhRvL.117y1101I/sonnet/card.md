# Ringed Structures of the HD 163296 Protoplanetary Disk Revealed by ALMA

`2016PhRvL.117y1101I` | Physical Review Letters 2016 | first author: Isella, Andrea | arXiv: - | DOI: 10.1103/PhysRevLett.117.251101

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Does the HD 163296 disk show ringed structures in dust and CO gas, and what do the dust and gas densities across the rings imply about their origin (planets, MRI dead zone, CO frost line)?  
  > "Observations of the dust emission at higher angular resolution and of molecules that probe dense gas are required to establish more precisely the origins of the dark rings" (abstract)
- Target **HD 163296**: coordinates _not stated_; z/distance 122 pc (+17/-13)  
  > "HD 163296 is a young (5 Myr) intermediate mass (2.3M ⊙ )" (Introduction); distance from van den Ancker et al. 1997 [21]  
  > "HD 163296 is a young (5 Myr) intermediate mass (2.3M ⊙ )" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00601.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.22'' x 0.14'' (about 25 AU)  
  > "The angular resolution of the observations, 0.22 [00] × 0.14 [00], is indicated" (Figure 1 caption)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- External data: Cosmic CO abundance n(12CO/H2)=5e-5 used to convert CO to H2  
  > "adopting a cosmic molecular abundance nð [12] CO=H 2 Þ ¼
5 × 10 [−][5] [28]" (Data analysis) [from Wilson 1999 [28]]
- Simulation/model as data: Hydrodynamic planet-disk simulations with three planets (0.1, 0.3, 0.3 MJ at 62, 105, 160 AU) compared to derived surface densities  
  > "The red line in Fig. 2 shows
the dust and gas surface density for a disk perturbed
by three planets with masses of 0.1M J, 0.3M J, and 0.3M J" (Discussion)

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

- Parametric surface density and temperature model of the disk  
  > "Following the methodology described in" (Data analysis) [from de Gregorio-Monsalvo et al. 2013 [23] and Rosenfeld et al. 2013 [27]]
- Data acquisition, calibration, modeling procedure and simulation setup are in the Supplemental Material  
  > "The acquisition and calibration
of the data are described in the Supplemental Material [26]." (Observations) [from Supplemental Material [26]]

### Not stated but needed to reproduce (our reading)

- Calibration and imaging details (CASA version, weighting, robust, cleaning, continuum-subtraction channels) are only in the Supplemental Material
- Observing setup, spectral windows, array configurations, dates
- Model-fitting procedure for gap parameters (grid, likelihood, radiative-transfer or ray-tracing code)
- Stellar and disk parameters (stellar mass luminosity inputs) for the temperature model
- Hydrodynamic code and setup

## Analysis recipe

1. **azimuthally averaged radial profiles**: Average over elliptical annuli to correct for inclination  
  > "averaging on elliptical annuli with a position angle of 132°, an eccentricity of 0.7, and a width equal to 1=4 of the angular resolution" (Figure 1 caption)
   - fitting: _not stated_
   - validation: _not stated_
2. **parametric Gaussian fit to continuum profile**: Gaussian minus three Gaussian gap components fitted to the continuum profile  
  > "A nonlinear least-squares
Marquardt-Levenberg fit of the observations returns" (Observations)
   - fitting: Marquardt-Levenberg least squares, reduced chi2 ~2  
  > "with a reduced
χ [2] ∼ 2" (Observations)
   - validation: _not stated_
3. **model dust and CO emission to derive surface densities and gap parameters**: Synthetic images from parametric surface density and temperature models with circular gaps (R, W, Delta) compared to observations  
  > "We calculate synthetic
images for the dust continuum, [12] CO, [13] CO, and C [18] O
J ¼ 2 − 1 emission for different values of the gap parameters ðR; W; ΔÞ" (Data analysis)
   - assumption: Gaps in dust and CO have same width and radius; CO abundance 5e-5  
  > "we assume that the gaps in
the dust and CO have the same width and radius" (Data analysis)
   - fitting: _not stated_
   - validation: _not stated_
4. **infer planet masses, viscosity and compare to hydrodynamics**: Combine gap width and depth relations with derived aspect ratios; compare to hydrodynamic simulations  
  > "By combining Eqs. (3) and (4) we estimate the
viscosity parameter α." (Discussion)
   - fitting: _not stated_
   - validation: Hydrodynamic simulations of three planets after 2000 orbits  
  > "The surface
density profiles were extracted after 2000 orbits of the
innermost planet" (Discussion)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust gap radii | 60, 100, 160 | not stated | AU | 3 | R 1 ¼ 60 A.U., R 2 ¼ 100 A.U.,
and R 3 ¼ 160 A.U. |
| Disk inclination | 42 | not stated | deg | 1 | an intrinsically
circular disk inclined by 42° with respect to the line of
sight |
| Gaussian gap radii theta1,2,3 | 0.44, 0.81, 1.13 | 0.01, 0.01, 0.02 | arcsec | 2 | θ 1 ¼
ð0.44 � 0.01Þ [00], θ 2 ¼ ð0.81 � 0.01Þ [00], θ 3 ¼ ð1.13 � 0.02Þ [00] |
| Ring intensity ratios B1/D1, B2/D2, B3/D3 | 1.6, 1.3, 1.08 | not stated | dimensionless | 1 | are 1.6 (B1=D1), 1.3
(B2=D2), and 1.08 (B3=D3) |
| Dust surface density parameters | gamma=0.1, rc=90 AU, Sigma_c=0.42 g cm-2 | not stated | mixed | 3 | γ ¼ 0.1, r c ¼ 90 A.U., Σ c ¼ 0.42 g cm [−][2] |
| CO depletion in inner gap | 0 to 2.5 | not stated | dimensionless | 3 | we measure Δ [CO] 1 between 0 and 2.5 |
| Viscosity alpha in inner gap | >~2e-2 | not stated | dimensionless | 4 | We obtain α ≳ 2 × 10 [−][2] in the inner
gap |

## Qualitative findings

- CO maps show no rings but slope changes at ring positions; gas-to-dust ratio rises by at least a factor 5 in the inner gap  
  > "it increases by at least a factor 5 within the inner dust gap compared to adjacent regions of
the disk" (abstract)

## Claim tuples

- H: Are the dust rings accompanied by gas gaps? | E: Modeled continuum and CO isotopologue maps with gap models | R: CO is depleted in middle and outer gaps but not in the inner gap | F: Gas-to-dust ratio varies across the disk | **supported**
- H: Could planets carve the gaps? | E: Compared derived densities with hydrodynamic simulations | R: Saturn-mass planets at 100 and 160 AU fit middle and outer gaps; a single planet fails for the inner gap | F: Middle and outer rings consistent with planets; inner gap origin unclear | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: CO depletion in middle and outer gaps deemed inconsistent with volatile evaporation (frost line) origin  
  > "the depletion of CO molecules measured inside
the middle and outer gaps is inconsistent with the evaporation of volatile elements" (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Large CO optical depth prevents ruling out a shallow gas gap in the inner gap  
  > "due to the large optical depth of
the observed CO lines, we cannot rule out the presence of a
shallow gas gap" (Conclusions)
- Caveat (inferred, ours): Parametric temperature model rather than radiative transfer
- Caveat (inferred, ours): Model degeneracy between gap width and depth
- Caveat (inferred, ours): Optically thick CO lines
- Caveat (inferred, ours): Planet configuration not unique

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Supplemental Material needed for calibration, imaging and modeling
- Missing: No code named or released
- Data volume (inferred): ~100-300 GB raw for Band 6 continuum plus CO lines
- Score (inferred): 2/5, Main text omits calibration, imaging and fit procedures; these are deferred to the Supplemental Material.
- Rediscovery candidate: no, The recipe is incomplete in the main text, and the model fitting is complex and not specified.

## Links

- Method: de Gregorio-Monsalvo et al. 2013 [23] (Disk modeling methodology)
- Method: Rosenfeld et al. 2013 [27] (Disk modeling methodology)
- Companion: Liu et al. [46] (Detailed planet-disk interaction analysis)
- Companion: Guidi et al. 2016 [24] (Previous ALMA observations of HD 163296)

## Checks

```json
{
 "quotes": 32,
 "quotes_ok": 32,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 63,
  "stated": 18,
  "rate": 0.286
 },
 "evidence_ok": true
}
```
