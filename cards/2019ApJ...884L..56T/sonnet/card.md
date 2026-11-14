# Spiral Structure in the Gas Disk of TW Hya

`2019ApJ...884L..56T` | The Astrophysical Journal Letters 2019 | first author: Teague, Richard | arXiv: 1910.01532 | DOI: 10.3847/2041-8213/ab4a83

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Is there spiral substructure in the gas velocity and temperature structure of the TW Hya disk, and what could launch it?  
  > "In this Letter we search for comparable azimuthal structure in the gas physical structure, both in terms of gas velocity and temperature." (1 Introduction)
- Target **TW Hya**: coordinates _not stated_; z/distance 60.1 ± 0.1 pc  
  > "the closest protoplanetary disk at $60.1~\pm0.1$ pc (cite: Bailer-Jones_ea_2018)" (1 Introduction); distance from Bailer-Jones et al. 2018 (Gaia)  
  > "the closest protoplanetary disk at $60.1~\pm0.1$ pc (cite: Bailer-Jones_ea_2018)" (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.00686.S, 2016.1.00629.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 139 mas x 131 mas, PA 105 deg; channel spacing 250 m/s  
  > "The final image has a beam size of $139~{\rm mas} \times 131~{\rm mas}$ with a position angle of $105\ensuremath{^\circ}$ and a channel spacing of $250~{\rm m\,s^{-1}}$." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Data from Huang et al. 2018; projects PI Andrews and PI Cleeves  
  > "We use the $^{12}$CO $J = 3-2$ observations presented in (cite: Huang_ea_2018)" (2 Observations)
- Line: 12CO J=3-2 (not stated)
- External data: Reduced and imaged 12CO 3-2 data cubes  
  > "We refer the reader to the aforementioned publication for full details of the data reduction and subsequent imaging." (2 Observations) [from Huang et al. 2018 (cite: Huang_ea_2018)]
- External data: Perturber location 94 au, polar angle ~10 deg  
  > "we adopt the location used in (cite: Mentiplay_ea_2019) at an orbital radius of 94 au and a polar angle of $\phi \approx 10\ensuremath{^\circ}$" (3.1 An Embedded Planet) [from Mentiplay et al. 2019]
- Simulation/model as data: Spiral wake parameterization of Bae & Zhu (2018) used to compare spiral morphology  
  > "we attempt to fit the structures using a parameterization of a spiral wake from an embedded companion (cite: Bae_Zhu_2018a; Bae_Zhu_2018b)" (3.1 An Embedded Planet)

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
- final beam: 139 x 131 mas, PA 105 deg  
  > "The final image has a beam size of $139~{\rm mas} \times 131~{\rm mas}$ with a position angle of $105\ensuremath{^\circ}$" (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Data reduction and imaging  
  > "We refer the reader to the aforementioned publication for full details of the data reduction and subsequent imaging." (2 Observations) [from Huang et al. 2018 (cite: Huang_ea_2018)]
- Imaging at velocity offsets of ±100 m/s to mitigate spectral response  
  > "we follow the approach described in (cite: Christiaens_ea_2014) and image the data at two additional velocity offsets, $\pm$$100~{\rm m\,s^{-1}}$." (2.1 Velocity Structure) [from Christiaens et al. 2014]

### Not stated but needed to reproduce (our reading)

- Calibration, CASA version, weighting and imaging parameters (only in Huang et al. 2018)
- bettermoments settings beyond the quadratic method (e.g. masking)
- emcee/eddy uncertainty handling and the radial binning for the Tb profile
- Exact procedure for the by-eye spiral fits and the pitch-angle uncertainties
- Coordinates of the target

## Analysis recipe

1. **Measure line centres and peak Tb**: Quadratic fit to peak pixel and two neighbours, averaged over images at 0 and ±100 m/s offsets  
  > "This approach fits a quadratic curve to the pixel of peak intensity and the two neighbouring pixels." (2.1 Velocity Structure)
   - software: bettermoments
   - fitting: _not stated_
   - validation: Uncertainty below 10% of the channel width  
  > "we achieve a precision of less than 10% of the channel width" (2.1 Velocity Structure)
2. **Fit Keplerian rotation model and make residual map**: Fit Keplerian v0 map with eddy, average 250 posterior samples, subtract from data  
  > "We take the average of 250 random samples of the posterior distributions to create a model rotation map, $v_{\rm mod}$." (2.1 Velocity Structure)
   - software: eddy, emcee, scipy.optimize
   - parameter: 256 walkers, 500 burn-in steps, 10,000 sampling steps; fit region 0.26'' to 3.75''  
  > "utilises 256 walkers which take 500 steps to burn in, then an additional 10, 000 steps to sample the posterior distribution function" (Rotation Map Fitting)
   - parameter: Inclination fixed at 5.8 deg  
  > "we fix it at $5.8\ensuremath{^\circ}$ based on trial runs" (2.1 Velocity Structure)
   - assumption: Keplerian, razor-thin disk; flat priors (M* 0.1-2 Msun)  
  > "This approach makes the implicit assumption that the rotation profile of Keplerian" (Rotation Map Fitting)
   - fitting: MCMC with emcee after scipy.optimize start; flat priors  
  > "The fitting starts with an optimisation of the free parameters of using `scipy.optimize` which is then used as the starting positions for an MCMC exploration" (Rotation Map Fitting)
   - validation: Four runs, including elevated emission surface; model scatter ~1%  
  > "all four runs found PDFs for the free parameters which resulted in an average standard deviation in $v_{\rm mod}$ of $\sim 1\%$" (Rotation Map Fitting)
3. **Temperature residuals**: Convert peak intensity to Tb via Planck law, subtract deprojected azimuthally averaged radial profile  
  > "we convert from flux density units to units of Kelvin assuming the Planck law" (2.2 Temperature Structure)
   - software: bettermoments
   - assumption: 12CO optically thick so Tb traces gas temperature  
  > "we can use the brightness temperature as a probe of the gas temperature" (2.2 Temperature Structure)
   - fitting: _not stated_
   - validation: Radial profile compared to Huang et al. 2018  
  > "The recovered radial profile is again consistent with that presented in (cite: Huang_ea_2018)" (2.2 Temperature Structure)
4. **Fit Archimedean spirals and pitch angles**: Linear spiral r = a + b phi fitted by eye; pitch angle tan beta = -(dr/dphi)/r  
  > "Due to the relatively low significance of the spirals in any given pixel, the fits were performed by eye." (2.3 Spiral Structure)
   - parameter: {a,b} = {1.51,0.17} velocity; {1.43,0.16} and {2.03,0.18} temperature  
  > "The velocity spiral was well fit with $\{a,\,b\} = \{1.51,\, 0.17\}$" (2.3 Spiral Structure)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare with planet spiral wake model**: Bae & Zhu Lindblad wake with m=1000, planet at 94 au, M*=0.81 Msun, cs from Tb profile  
  > "We use $m = 10^3$ in order to recover spirals with the smallest pitch angles" (3.1 An Embedded Planet)
   - fitting: _not stated_
   - validation: Model fails to reproduce observed morphology  
  > "which fails to reproduce the observed morphology" (3.1 An Embedded Planet)

## Software

- **bettermoments** : line centre and peak Tb maps  
  > "we, use the `bettermoments`[^1] package using the quadratic method" (2.1 Velocity Structure)
- **eddy** : Keplerian fit to v0 map  
  > "we use the Python package `eddy`[^2] (cite: eddy) to fit a Keplerian rotation profile" (2.1 Velocity Structure)
- **emcee** : MCMC sampling  
  > "The MCMC is performed using `emcee`" (Rotation Map Fitting)
- **scipy.optimize** : initial optimisation  
  > "an optimisation of the free parameters of using `scipy.optimize`" (Rotation Map Fitting)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stellar mass | 0.81 | +0.16/-0.17 | Msun | 2 | $M_{\rm star} = 0.81_{-0.17}^{+0.16}~M_{\ensuremath{\odot}}$ |
| Position angle | 151.6 | 5.8 | deg | 2 | ${\rm PA} = 151.6 \pm 5.8~\ensuremath{^\circ}$ |
| Systemic velocity | 2839 | 18 | m/s | 2 | $v_{\rm LSR} = 2839 \pm 18~{\rm m\,s^{-1}}$ |
| Pitch angle range of spirals | 9 deg at 70 au to 3 deg at 200 au | not stated | deg | 4 | ranging from 9$^\circ$ at 70 au, dropping to 3$^\circ$ at 200 au |
| Temperature deviation | ±4 K, ΔT/T ~0.05 | not stated | K | 3 | Deviations in the gas temperature are $\pm 4$ K about the azimuthally averaged profile |
| Velocity deviation | Δvφ/vkep ~0.1 or Δvz/vkep ~0.01 (30 m/s in v0) | not stated | dimensionless | 2 | $\Delta v_{\phi} \, / \, v_{\rm kep} \sim 0.1$ or $\Delta v_{z} \, / \, v_{\rm kep} \sim 0.01$ |

## Qualitative findings

- Radial velocity perturbations ruled out since the spiral crosses the major axis  
  > "we can rule out significant $v_{\rm r}$ motions" (3.1 An Embedded Planet)

## Claim tuples

- H: Spiral structure exists in the gas velocity and temperature of TW Hya | E: Subtract azimuthally symmetric models from 12CO 3-2 maps | R: One velocity spiral and two temperature spirals found, ~5 sigma per pixel but coherent | F: Real spiral substructure in gas | **supported**
- H: A Lindblad-resonance wake from the 94 au planet explains the spirals | E: Compare Bae & Zhu wake model to the observed spirals | R: Model fails; tighter spiral needs (h/r)_p ~0.02 | F: Spirals not readily explained by Lindblad wake; other mechanism (e.g. buoyancy) possible | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Subtracting one side of the rotation map from the other gave no improvement over a 2D model  
  > "we do not find any improvement over the subtraction of a full 2D model" (2.1 Velocity Structure)
- How they decided it was enough: _not stated_
- Limitation (authors): Cannot fully break degeneracy between velocity components  
  > "we will never be able to fully break the degeneracy between which velocity components are dominating the observed perturbations" (3.1 An Embedded Planet)
- Limitation (authors): Low per-pixel significance; by-eye spiral fits  
  > "Due to the relatively low significance of the spirals in any given pixel, the fits were performed by eye." (2.3 Spiral Structure)
- Caveat (inferred, ours): Spiral fits by eye with no uncertainties
- Caveat (inferred, ours): Residual features may be affected by imperfect Keplerian/emission-surface model and spectral response
- Caveat (inferred, ours): Pitch-angle interpretation depends on assumed emission height

## Reproducibility

- Data public (paper): ALMA projects listed; processing in Huang et al. 2018  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00686.S and 2016.1.00629.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: bettermoments and eddy on GitHub  
  > "<https://github.com/richteague/eddy>" (footnote)
- Missing: Huang et al. 2018 imaging parameters
- Missing: By-eye spiral fit procedure
- Data volume (inferred): ~10-50 GB (two archival Band 7 projects)
- Score (inferred): 3/5, Public data and named tools with MCMC details, but imaging is deferred to earlier work and spiral fits are by eye.
- Rediscovery candidate: no, Imaging recipe is not given and key spiral measurements are by eye.

## Links

- Method: Teague & Foreman-Mackey 2018 (bettermoments quadratic method)
- Method: Christiaens et al. 2014 (velocity-offset imaging for spectral response)
- Companion: Huang et al. 2018 (source of data reduction and imaging)

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 36,
  "rate": 0.468
 },
 "evidence_ok": true
}
```
