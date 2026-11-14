# On the Origin of the Spiral Morphology in the Elias 2-27 Circumstellar Disk

`2017ApJ...839L..24M` | The Astrophysical Journal Letters 2017 | first author: Meru, Farzana | arXiv: 1703.05338 | DOI: 10.3847/2041-8213/aa6837

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: What causes the two large-scale spiral arms and inner structures in the Elias 2-27 disc: an internal companion, an external companion, or gravitational instability?  
  > "With such a large disc-to-star mass ratio, could the disc be self-gravitating? Or, could an as-yet-undetected companion be causing these features via dynamical interactions?" (Introduction)
- Target **Elias 2-27**: coordinates _not stated_; z/distance 139 pc  
  > "Assuming all objects lie at the same distance as Elias 2-27 (139 pc)" (2.3.2); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00498.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthesised beam of real data 0.27'' x 0.25'', PA = 86 deg  
  > "which results in a very similar synthesised beam to that of the real data: 0.27$''$$\times$0.25$''$ with PA = $86\ensuremath{^\circ}$" (2.2 Radiative Transfer & Synthetic Imaging)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **UKIDSS**: K-band source catalogue used to limit companion mass  
  > "the area around Elias 2-27 has been targeted by the UKIRT Infrared Deep Sky Survey" (2.3.2)
- External data: ALMA observations, disc parameters (Sigma_c=5 g cm-2, Rc=200 au, q=0.45, p=0.7), CO kinematic enclosed mass 0.5±0.2 Msun, unsharp-masked image and intensity profile  
  > "using the parameters determined by (cite: Elias227_Science), namely $\Sigma_{\rm c} = 5$ g cm$^{-2}$, R$_{\rm c} = 200$ au, $q = 0.45$ and $p=0.7$" (2.1 Hydrodynamics) [from (cite: Elias227_Science)]
- External data: K-band contrast upper limit of 2.5 mag between 0.13-6.4'' (multiplicity survey)  
  > "Elias 2-27 was found to be a single star with an upper limit on the K-band contrast of 2.5 mag between 0.13–$6.4\ensuremath{''}$." (2.3.2) [from (cite: ratzka_2005)]
- Simulation/model as data: 72 3D SPH radiation-hydrodynamic simulations, 250,000 particles each, post-processed with RADMC-3D  
  > "We perform 72 hydrodynamical simulations varying a number of disc properties as well as orbit properties for the companion simulations." (2.1 Hydrodynamics)

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

- task: CASA simobserve for visibilities, clean for imaging (synthetic)  
  > "Visibilities are calculated with the `simobserve` task while imaging is performed with the `clean` task." (2.2 Radiative Transfer & Synthetic Imaging)
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

- Unsharp masking applied in similar manner to the observational paper  
  > "We then apply an unsharp masking filter to the images in a similar manner to (cite: Elias227_Science)." (2.2 Radiative Transfer & Synthetic Imaging) [from (cite: Elias227_Science)]
- SPH code description  
  > "A detailed description of the code can be found in (cite: Triggered)" (2.1 Hydrodynamics) [from (cite: Triggered)]

### Not stated but needed to reproduce (our reading)

- Scaling factor of the unsharp mask subtraction
- clean parameters (weighting, cell, image size, niter, threshold)
- Dust inclination/position angle and distance used for ray tracing
- Which of the 72 simulations are shown and full parameter table
- Time/snapshot selected for imaging
- Inward extrapolation power-law exponent

## Analysis recipe

1. **Run SPH simulations**: 3D SPH with flux-limited diffusion, 250,000 particles; 0.5 Msun star, disc 10-400 au; internal/external companion or self-gravitating setups  
  > "Each disc is modelled using 250,000 sph gas particles." (2.1 Hydrodynamics)
   - software: sph code
   - parameter: alpha_SPH 0.1-1.0, beta_SPH = 2 alpha_SPH  
  > "with the sph parameter, $\alpha_{\rm SPH}$, varying between 0.1 – 1.0 and $\beta_{\rm SPH} = 2 \alpha_{\rm SPH}$" (2.1 Hydrodynamics)
   - assumption: gas and dust well mixed; surface temperature held at T(R)=13.4 K (R/200 au)^-q  
  > "We assume that the gas and dust are well mixed." (2.1 Hydrodynamics)
   - fitting: _not stated_
   - validation: _not stated_
2. **Radiative transfer to 1.3 mm images**: RADMC-3D with astronomical silicate Mie opacities, size distribution 0.005-1000 um slope -3.5, gas-to-dust 100, SPH interpolation  
  > "assuming a power-law grain size distribution between 0.005 – 1000 $\mu$m with a power exponent of $-3.5$" (2.2 Radiative Transfer & Synthetic Imaging)
   - software: RADMC-3D
   - parameter: lambda = 1.3 mm  
  > "we calculate images at $\lambda=1.3$ mm using the raytracer in RADMC-3D" (2.2 Radiative Transfer & Synthetic Imaging)
   - assumption: uniform gas-to-dust ratio 100; dust and gas temperatures identical  
  > "The dust and gas temperatures are assumed to be identical." (2.2 Radiative Transfer & Synthetic Imaging)
   - fitting: _not stated_
   - validation: _not stated_
3. **Synthetic ALMA observation and unsharp masking**: CASA simobserve with alma.out13, 6.8 GHz bandwidth, PWV 2.7 mm, 725 s; clean; Gaussian unsharp mask FWHM 0.33''  
  > "we use a bandwidth of 6.8 GHz, assume a precipitable water vapour column of 2.7 mm, and a total integration time of 725 seconds." (2.2 Radiative Transfer & Synthetic Imaging)
   - software: CASA
   - fitting: _not stated_
   - validation: Qualitative morphological comparison with observed unsharp-masked image and radial intensity profile; mass limits from UKIDSS and kinematics  
  > "We require the unsharp masked synthetic observations of the simulated discs to display morphology that is consistent with the observations." (3 Results)

## Software

- **CASA** v4.5: synthetic ALMA observations (simobserve, clean)  
  > "Synthetic observations for ALMA are calculated using the Common Astronomy Software Application v4.5" (2.2 Radiative Transfer & Synthetic Imaging)
- **RADMC-3D** : 3D dust radiative transfer and ray tracing  
  > "we use the 3D radiative transfer code radmc-3d" (2.2 Radiative Transfer & Synthetic Imaging)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Successful external companion mass | ≈10 (limit ≲10-13) | not stated | M_Jup | 3 | includes a $\approx 10 M_{\rm Jup}$ companion at $\approx 425$ au |
| Successful self-gravitating disc mass | 0.24 | not stated | Msun | 3 | The disc mass is 0.24 ${\rm M_{\odot}}$, leading to a disc-to-star mass ratio of 0.49. |

## Qualitative findings

- A steep decline in surface density beyond ~300 au is required to match the unsharp-masked image  
  > "a steep decline in surface mass density beyond $\approx 300$ au is required" (5 Conclusions)

## Claim tuples

- H: An undetected internal companion produces the Elias 2-27 morphology | E: Internal companion SPH models, synthetic ALMA and unsharp mask | R: Produces central ellipse but no dark crescents or two-armed spiral | F: Unlikely | **refuted**
- H: An external companion or gravitational instability reproduces the morphology | E: External companion and self-gravitating disc models | R: Both reproduce spirals, dark crescents and inner ellipse | F: Both are viable; companion ≲10-13 MJup at ~300-700 au | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Exponentially tapered disc from the observational paper does not reproduce the observations well  
  > "i.e. with an exponential surface mass density profile, which does not reproduce the observations well" (4 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Aim is morphological similarity, not exact fit; different uv coverage used  
  > "Since our goal is not to fit the observations exactly, but merely to show the morphological similarities between our models and the observations" (2.2 Radiative Transfer & Synthetic Imaging)
- Caveat (inferred, ours): Comparison is qualitative and by eye
- Caveat (inferred, ours): Degeneracy between scenarios is not broken
- Caveat (inferred, ours): Synthetic uv coverage differs from the real data

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: SPH code and initial conditions not released
- Missing: Full table of the 72 simulations
- Data volume (inferred): small (<10 GB); simulated, with comparison to published images
- Score (inferred): 2/5, Simulation-based with a proprietary SPH code and a qualitative comparison; ALMA data used only for comparison.
- Rediscovery candidate: no, Main results are qualitative and depend on an unreleased SPH code.

## Links

- Method: (cite: Triggered) (SPH code description)
- Companion: (cite: Elias227_Science) (Original ALMA observations of Elias 2-27)
- Companion: (cite: Tomida_Elias227_GI) (Self-gravitating disc simulations of Elias 2-27)
- Related: UKIDSS

## Checks

```json
{
 "quotes": 29,
 "quotes_ok": 29,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 23,
  "rate": 0.343
 },
 "evidence_ok": true
}
```
