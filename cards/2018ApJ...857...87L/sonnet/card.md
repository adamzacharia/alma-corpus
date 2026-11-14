# New Constraints on Turbulence and Embedded Planet Mass in the HD 163296 Disk from Planet-Disk Hydrodynamic Simulations

`2018ApJ...857...87L` | The Astrophysical Journal 2018 | first author: Liu, Shang-Fei | arXiv: 1803.05437 | DOI: 10.3847/1538-4357/aab718

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: Can planet-disk interaction with a radially varying alpha viscosity explain the dust gaps and CO depletion pattern in the HD 163296 disk, and what planet masses and turbulence levels are required?  
  > "Here we explore the possibility that all three gaps are formed through planet–disk interaction." (Introduction)
- Target **HD 163296**: coordinates _not stated_; z/distance 122 +17/-13 pc  
  > "At a distance of only $122 ^{+ 17} _{- 13} \;{\rm pc}$ from the Earth (cite: 1997A&A...324L..33V)" (Introduction); distance from van den Ancker et al. 1997  
  > "At a distance of only $122 ^{+ 17} _{- 13} \;{\rm pc}$ from the Earth (cite: 1997A&A...324L..33V)" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00601.S
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
- Line: 12CO, 13CO, C18O J=2-1 (not stated)
- External data: ALMA 1.3 mm continuum and CO J=2-1 observations, plus fiducial parametric disk model (surface densities, temperature structure, dust opacity 3.95 cm2/g, inclination 42 deg, PA 132 deg)  
  > "We adopt an initial disk dust and gas surface density profile presented in I16" (2 Method); "We adopt a dust opacity at 1.3 mm of 3.95 $\textrm{cm}^2\textrm{g}^{-1}$ same as I16" (2.2 Radiative transfer) [from Isella et al. 2016 (cite: 2016PhRvL.117y1101I)]
- External data: Stellar mass 2.3 Msun and effective temperature 9500 K  
  > "with a stellar mass of 2.3 $\rm{M}_\odot$  and an effective temperature of $9500\,{\rm K}$ (cite: 2004A&A...416..179N)" (Introduction) [from Natta et al. 2004 (cite: 2004A&A...416..179N)]
- Simulation/model as data: Hydrodynamic simulations of three embedded planets (LA-COMPASS) post-processed with RADMC-3D to synthetic continuum and CO images compared to ALMA data  
  > "by combining the planet–disk interaction simulations with the *LA-COMPASS* code" (2 Method)

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

- Modeling procedure combining hydro simulations and RADMC-3D radiative transfer  
  > "We follow the procedure of the HL Tau disk modeling in J16" (2 Method) [from J16 (Jin et al. 2016) (cite: 2016ApJ...818...76J)]
- Detailed RADMC-3D procedure for dust and CO emission  
  > "The reader interested in the detailed procedure of calculating dust and CO emission using *RADMC-3D* is referred to I16 supplementary material." (2.2 Radiative transfer) [from I16 (Isella et al. 2016) (cite: 2016PhRvL.117y1101I)]

### Not stated but needed to reproduce (our reading)

- Public ALMA data processing/imaging details (beam, rms, calibration) not given; taken from I16
- LA-COMPASS code version and dust-gas coupling/boundary condition details
- CO abundance and isotope ratios, and the radially varying CO/H2 profile
- RADMC-3D photon numbers and beam convolution parameters
- Quantitative goodness-of-fit metric; fits judged by eye

## Analysis recipe

1. **Run 2D two-fluid hydrodynamic simulations**: LA-COMPASS gas+dust simulations with three fixed planets at 59, 105, 160 au for 1000 orbits, scanning constant and radially varying alpha and planet masses  
  > "We assume that planets do not migrate for 1000 orbits ($\sim 3\times 10^5$ yr), so the gaps can be fully developed." (2.1 Hydrodynamic simulation)
   - software: LA-COMPASS
   - parameter: Grid 1024x768, disk 10-500 au, dust grain size 0.15 mm, h=0.05(r/r0)^0.25  
  > "The disk extends from 10 to 500 au, and is simulated with a resolution of $1024\times768$ grids along the radial and azimuthal direction." (2.1 Hydrodynamic simulation)
   - assumption: Isothermal T(r)=24.1(r/r0)^-0.5; viscosity nu=alpha c_s h  
  > "we assume the turbulent viscosity has the form $\nu = \alpha c_{\textrm{s}} h$" (2.1 Hydrodynamic simulation)
   - fitting: Manual exploration of more than 100 simulations compared with I16 fiducial surface densities; no MCMC  
  > "We have performed more than one hundred simulations in total with various initial conditions of planet mass, disk mass and effective viscosity." (3 Results)
   - validation: Compare simulated gas/dust surface densities with I16 parametric model  
  > "we improve our fitting by comparing our hydrodynamic simulations to the I16 fiducial model." (3 Results)
2. **Radiative transfer of dust continuum and CO lines**: Convert 2D densities to 3D with dust scale height 0.1 h_gas; RADMC-3D with Dartois-type temperature structure; CO freeze-out and photodissociation by reducing CO density by 1e8  
  > "We reduce the CO density by a factor of $10^8$ when the temperature is below 19 K" (2.2 Radiative transfer)
   - software: RADMC-3D, radmc3dPy
   - parameter: Dust opacity 3.95 cm2/g at 1.3 mm; inclination 42 deg; rotation 132 deg; Keplerian around 2.3 Msun  
  > "The generated disk image is inclined by $42^\circ$ and rotated by $132^\circ$ to match the observation." (2.2 Radiative transfer)
   - fitting: _not stated_
   - validation: Azimuthally averaged radial profiles and images compared with ALMA 1.3 mm continuum and CO J=2-1 data  
  > "We also compare the synthetic dust continuum and continuum-subtracted CO J=2-1 emission of the nominal model to the ALMA images of HD 163296 disk" (3.2 Varying alpha)
3. **Test sensitivity to alpha, inner planet mass and scale height**: Additional runs VaVis1, VaVis2, ShallowT, LargeH0  
  > "In model VaVis1 we use the same disk as in the nominal model except that we choose $\alpha_\textrm{in} = 5 \times 10^{-5}$." (3.3)
   - software: LA-COMPASS
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **LA-COMPASS** : planet-disk hydrodynamic simulations  
  > "*Software:* LA-COMPASS" (Acknowledgments)
- **RADMC-3D** : dust continuum and CO radiative transfer  
  > "Then we generate the dust continuum emission using the radiative transfer code *RADMC-3D*" (2.2 Radiative transfer)
- **radmc3dPy** : listed as software used (with RADMC-3D)  
  > "radmc3dPy" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Nominal planet masses at 59, 105, 160 au | 0.46, 0.46, 0.58 | not stated | M_J | 1 | three half-Jovian-mass planets (0.46, 0.46 and 0.58 $M_\textrm{J}$) at 59, 105 and 160 au |
| Nominal alpha_in and alpha_out | 1e-5 and 7.5e-3 | not stated | dimensionless | 1 | we choose $\alpha_\textrm{in} = 10^{-5}$ and $\alpha_\textrm{out} = 7.5 \times 10^{-3}$ |
| Inner planet mass range | 0.46 to 0.69 | not stated | M_J | 3 | the inner gap can be created by a sub-Jovian mass planet with a mass in the range of 0.46 to 0.69 $M_\textrm{J}$ |
| Extrapolated mass accretion rate at 0.1 au | 3e-11 | not stated | Msun/yr | 0 | we estimate a mass accretion rate $\dot{M} \simeq  3 \times 10^{-11} \;\textrm{M}_\odot\;\textrm{yr}^{-1}$ at 0.1 au |

## Qualitative findings

- No constant-alpha model reproduces all gaps; a radially increasing alpha is required, consistent with a dead zone transitioning to an MRI-active outer disk  
  > "we find it is difficult to reproduce all the features suggested by the observation with a constant $\alpha$-viscosity disk." (3.1)

## Claim tuples

- H: Three planets can carve all three dust gaps while the inner gap shows no CO depletion | E: Hydro + RADMC-3D models compared with ALMA profiles | R: Nominal model with 0.46/0.46/0.58 MJ reproduces dust rings and lacks CO rings in synthetic maps | F: Planet-disk interaction is consistent with observations | **supported**
- H: Constant alpha can explain the disk | E: Models HiVis, InVis, LoVis | R: Each fits only part of the features | F: A varying alpha is needed (low inner, ~7.5e-3 outer) | **supported**
- H: Outer-disk turbulence is weak (Flaherty et al.) | E: Compare modeling with literature | R: alpha>~7.5e-3 outer vs alpha<~3e-3 from lines | F: Discrepancy attributed to assumptions and temperature, not significant | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: MCMC prohibitively expensive, so fits made manually against I16 fiducial model  
  > "Practically, such a method is prohibited because it requires a huge amount of computation." (3 Results)
- Alternative: Constant alpha disks (HiVis, InVis, LoVis) rejected  
  > "To conclude, we find it is difficult to reproduce all the features suggested by the observation with a constant $\alpha$-viscosity disk." (3.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Degeneracy among acceptable alpha values not fully characterized  
  > "our simulations also show there is some degeneracy of acceptable $\alpha$ values, which is not fully characterized in this study." (4.2)
- Caveat (inferred, ours): No formal fit statistic or uncertainties on planet masses or alpha
- Caveat (inferred, ours): Fixed planet positions and 2D isothermal assumption
- Caveat (inferred, ours): Single dust grain size 0.15 mm
- Caveat (inferred, ours): Results depend on I16 temperature and CO abundance assumptions

## Reproducibility

- Data public (paper): Uses ALMA project 2013.1.00601.S, cited from I16  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00601.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: LA-COMPASS setup details
- Missing: I16 supplementary RADMC-3D CO abundance recipe
- Missing: reduced ALMA radial profiles
- Data volume (inferred): ~tens of GB if the ALMA data are re-imaged; simulation outputs only needed otherwise
- Score (inferred): 3/5, Parameters are tabulated, but the work depends on I16 for the data, the CO recipe and the code, with manual by-eye fitting.
- Rediscovery candidate: no, The main results come from simulations that rely on a specific code and external I16 inputs, not from a recoverable ALMA data analysis.

## Links

- Method: Jin et al. 2016 (cite: 2016ApJ...818...76J) (Procedure for hydro plus radiative transfer modeling)
- Method: Isella et al. 2016 (cite: 2016PhRvL.117y1101I) (ALMA data, fiducial parametric model and RADMC-3D CO recipe)
- Companion: Flaherty et al. 2017 (cite: 2017ApJ...843..150F) (Independent turbulence constraints compared)

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
  "facts": 66,
  "stated": 25,
  "rate": 0.379
 },
 "evidence_ok": true
}
```
