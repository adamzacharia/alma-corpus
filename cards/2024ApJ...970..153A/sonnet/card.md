# On Kinematic Measurements of Self-gravity in Protoplanetary Disks

`2024ApJ...970..153A` | The Astrophysical Journal 2024 | first author: Andrews, Sean M. | arXiv: 2405.19574 | DOI: 10.3847/1538-4357/ad5285

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: How accurately and precisely can disk gas masses be measured from the kinematic (self-gravity) signature in resolved CO line data, tested by injection/recovery on synthetic data and demonstrated on MWC 480  
  > "we devised an analysis prescription to assess the quality of dynamical measurements of protoplanetary disk gas masses based on resolved (CO) spectral line data" (abstract)
- Target **MWC 480**: coordinates _not stated_; z/distance d = 162 pc  
  > "$v_{\rm sys} = 5100\pm10$ m s$^{-1}$ (assuming $d = 162$ pc; (cite: gaia_dr3))" (6.3 Demonstration with ALMA Data: MWC 480); distance from Gaia DR3  
  > "$v_{\rm sys} = 5100\pm10$ m s$^{-1}$ (assuming $d = 162$ pc; (cite: gaia_dr3))" (6.3 Demonstration with ALMA Data: MWC 480)

## Data provenance

- ALMA projects: 2018.1.01055.L
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: MWC 480 cubes: beam 0.17'' x 0.12'' (PA = 6 deg), 200 m/s channels  
  > "created with FWHM synthesized beam dimensions $0.17\ensuremath{''}\times0.12\ensuremath{''}$ (PA = 6$^\circ$) and a channel spacing of 200 m s$^{-1}$" (6.3 Demonstration with ALMA Data: MWC 480)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival MAPS large program data  
  > "we selected the ALMA observations from the MAPS project (cite: maps1) of the MWC 480 disk" (6.3 Demonstration with ALMA Data: MWC 480)
- Line: 12CO J=2-1 (230.538 GHz)
- Line: 13CO J=2-1 (not stated)
- Other facility **Gaia DR3**: distance to MWC 480 (162 pc)  
  > "(assuming $d = 162$ pc; (cite: gaia_dr3))" (6.3 Demonstration with ALMA Data: MWC 480)
- External data: MWC 480 midplane temperature profile adopted in Layer 3  
  > "adopted the midplane temperature profile derived by (cite: zhang21) (as approximated with uncertainties by (cite: sierra21))" (6.3 Demonstration with ALMA Data: MWC 480) [from Zhang et al. 2021 (cite: zhang21); Sierra et al. 2021 (cite: sierra21)]
- External data: MAPS 12CO and 13CO J=2-1 cubes (robust=+0.5, primary-beam corrected)  
  > "these are the `robust` = $+0.5$, primary beam-corrected cubes" (6.3 Demonstration with ALMA Data: MWC 480) [from Öberg et al. 2021 (cite: maps1)]
- Simulation/model as data: Synthetic CO J=2-1 cubes from RADMC-3D for three fiducial models (A, B, C), Md=0.1 Msun, M*=1 Msun, d=150 pc, with ALMA C-4/C-7 sampling and noise  
  > "we relied on the (local thermodynamic equilibrium) excitation and raytracing capabilities of `RADMC-3D` (cite: dullemond12) to compute synthetic spectral line cubes." (3.1)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: MAPS-provided imaged cubes used  
  > "We considered the cubes for the $^{12}$CO and $^{13}$CO $J$=2$-$1 transitions provided by MAPS" (6.3 Demonstration with ALMA Data: MWC 480)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA/tclean for synthetic data  
  > "standard imaging process using the `CASA/tclean` task (cite: CASA22; cornwell08)" (3.1)
- deconvolver: _not stated_
- weighting robust: Briggs robust = +1 (simulated data)  
  > "used Briggs weighting with `robust` = +1" (3.1)
- uv taper: _not stated_
- cell size: 0.02'' pixels, 80 m/s channels (simulated)  
  > "We set 0.02$''$ pixels and a channel spacing of 80 m s$^{-1}$" (3.1)
- image size: _not stated_
- masking: Keplerian mask convolved with 0.15'' Gaussian  
  > "using a Keplerian mask (cite: teague20_kepmask) that was convolved with a FWHM = 0.15$''$ Gaussian" (3.1)
- multiscale scales: point source and Gaussians at 10, 30, 50 pixel FWHM  
  > "`multiscale` parameters that included point source and Gaussian scales at 10, 30, and 50 pixel FWHMs" (3.1)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.13'' x 0.11'' at PA = 95 deg (simulated)  
  > "They have synthesized beams with FWHM = $0.13\ensuremath{''}\times0.11\ensuremath{''}$ (at P.A. = 95$^\circ$)." (3.1)
- final rms: _not stated_

### Inherited from earlier work

- Geometry derivation from continuum visibilities (deprojection, frank fit, residual minimization)  
  > "We followed the procedure outlined by (cite: andrews21)." (MWC 480 Geometric Parameters) [from Andrews et al. 2021 (cite: andrews21)]
- Simplified kinematic mass approach of forward-modeling v_phi(r)  
  > "we further developed a simplified approach (cite: veronesi21; lodato22; martire24) that forward-models a distilled measurement of $v_\phi(r)$" (4) [from Veronesi 2021; Lodato 2022; Martire 2024]
- Emission surface model parameterization  
  > "A resulting set of {$r$, $z$, $\delta z$} was used to infer the parameters of a surface model (cite: law20)" (4.2) [from Law et al. 2020 (cite: law20)]

### Not stated but needed to reproduce (our reading)

- Exact MAPS data product versions/URLs for MWC 480 cubes
- MWC 480 priors for Layer 2/3 beyond statement of same procedure; priors for stellar luminosity etc.
- Details of the exponentially tapered temperature fits and bilinear interpolation
- csalt package is in preparation; mock-cube settings partly unspecified
- Gap parameters were manually tuned without a fitting procedure
- Number of posterior draws N2/N3 for MWC 480 Layer 4 beyond 1000 draws

## Analysis recipe

1. **Layer 1 geometry**: Fit deprojected MAPS 225 GHz continuum visibilities with frank over a grid of geometries; draw from priors  
  > "we deprojected the continuum visibilities and modeled them assuming axisymmetry with the `frank` package (cite: jennings20)" (MWC 480 Geometric Parameters)
   - software: frank
   - parameter: Adopted dx=5±7 mas, dy=1±7 mas, i=-36.3±0.5 deg, PA=327.7±0.7 deg, vsys=5100±10 m/s  
  > "$i = -36.3\ensuremath{^\circ}\pm0.5\ensuremath{^\circ}$, $\vartheta = 327.7\ensuremath{^\circ}\pm0.7\ensuremath{^\circ}$" (6.3 Demonstration with ALMA Data: MWC 480)
   - fitting: _not stated_
   - validation: Imaged residuals for parameter variations  
  > "That process was iterated for different geometries until we reached a satisfactory map that minimized the imaged residual visibilities." (MWC 480 Geometric Parameters)
2. **Layer 2 emission surface**: Extract surface from isovelocity loops in cubes, fit exponentially tapered power-law z(r) with emcee  
  > "using the `disksurf` package (cite: disksurf)" (4.2)
   - software: disksurf, emcee
   - parameter: 64 walkers, 10,000 steps; uniform priors on z0, phi, r_z, psi, ln f_surf; N1=500 geometry draws (simulations)  
  > "using 64 walkers for 10,000 steps" (5.2)
   - fitting: Gaussian likelihood with nuisance scatter f_surf, emcee  
  > "using the `emcee` Monte Carlo Markov Chain sampler" (4.2)
   - validation: Compared with true tau=2/3 surfaces (offset dz/r ~ -0.05); MWC 480 surfaces compared with Law et al. 2021  
  > "the inferred emission surfaces are comparable to those found by (cite: law21)" (6.3 Demonstration with ALMA Data: MWC 480)
3. **Layer 3 thermal structure**: Peak intensity (moment 8) brightness temperature along surface; fit T(r,z) model; for MWC 480 use tapered power-law fits per line plus Zhang+21 midplane with bilinear interpolation  
  > "computing the peak intensity (moment-8) map from the cube with the `bettermoments` package" (4.3)
   - software: bettermoments, gofish, emcee
   - assumption: Line emission optically thick and thermalized  
  > "The idea is to assume the line emission is optically thick and thermalized." (4.3)
   - fitting: Gaussian likelihood with nuisance f_temp; emcee 64 walkers, 10,000 steps  
  > "sampled the $\theta_{\tt 3}$ posteriors for 64 walkers and 10,000 steps" (5.3)
   - validation: Not validated for MWC 480; no 2D prescription fit satisfactorily  
  > "We were unable to find a two-dimensional temperature prescription that satisfactorily accounts for these profiles." (6.3 Demonstration with ALMA Data: MWC 480)
4. **Extract v_phi(r) and correct for resolution bias**: eddy annulus-wise velocity extraction (dV method) along emission surface, then multiply by correction factors from csalt mock cubes  
  > "`fit‘_method=‘dV’`" (4.4)
   - software: eddy, csalt
   - parameter: 0.05'' radial bins  
  > "We set the annular spacing of these extractions to 0.05$''$" (6.3 Demonstration with ALMA Data: MWC 480)
   - assumption: Bias from beam smearing only; mock with Keplerian field, power-law Tb  
  > "Assuming the bias is produced solely by these beam-smearing effects" (5.1)
   - fitting: _not stated_
   - validation: Correction factors indistinguishable across models and insensitive to inputs (<1% std)  
  > "relatively insensitive to uncertainties in the input parameters (within $<$1% standard deviations)" (5.1)
5. **Layer 4 inference of Md, M*, Sigma parameters**: Fit v_phi model (stellar + pressure + self-gravity) to extracted profiles with emcee; joint 12CO+13CO for MWC 480  
  > "we then performed the `Layer  4` inference for *both lines* jointly" (6.3 Demonstration with ALMA Data: MWC 480)
   - software: emcee
   - parameter: 64 walkers, 25,000 steps; priors p~U(0,2), gamma~U(0,6), rt logistic soft bound (600 au for MWC 480), min Q prior  
  > "again using `emcee` and 64 walkers for 25,000 steps" (5.3)
   - assumption: Axisymmetry, no radial/vertical flows, gravitationally stable disk (min Q prior)  
  > "This framework assumes the disk structure and kinematics are axisymmetric, and that no external contributions" (4)
   - fitting: Gaussian likelihood with nuisance f_vphi; emcee  
  > "where $f_{\tt vphi}$ is a nuisance parameter to account for any under-estimated scatter" (4.4 Layer 4: Kinematics)
   - validation: Injection/recovery on fiducial models; MWC 480 compared with Zhang+21 and Martire+24 Sigma profiles  
  > "The general agreement between these independent techniques is striking" (6.3 Demonstration with ALMA Data: MWC 480)

## Software

- **CASA** : tclean imaging of synthetic data  
  > "standard imaging process using the `CASA/tclean` task" (3.1)
- **RADMC-3D** : synthetic line cubes and tausurf  
  > "we relied on the (local thermodynamic equilibrium) excitation and raytracing capabilities of `RADMC-3D`" (3.1)
- **vis_sample** : sampling model cubes to visibilities  
  > "sampled onto the template ($u$, $v$) spatial frequencies using the `vis‘_sample` package" (3.1)
- **csalt** : simulations and mock cubes for bias correction  
  > "The simulations and post-processing steps were computed with the `csalt` package" (3.1)
- **disksurf** : emission surface extraction  
  > "using the `disksurf` package (cite: disksurf)" (4.2)
- **emcee** : posterior sampling in all layers  
  > "using the `emcee` Monte Carlo Markov Chain sampler" (4.2)
- **bettermoments** : peak intensity maps  
  > "computing the peak intensity (moment-8) map from the cube with the `bettermoments` package" (4.3)
- **gofish** : azimuthally averaged Tb profiles  
  > "the `gofish` package (cite: gofish) was used on that peak intensity map" (4.3)
- **eddy** : velocity profile extraction  
  > "using the `eddy` package (cite: eddy)" (4.4)
- **frank** : continuum visibility fit for geometry  
  > "modeled them assuming axisymmetry with the `frank` package" (MWC 480 Geometric Parameters)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| MWC 480 disk mass Md | 0.13 | +0.04/-0.01 | Msun | 5 | 0.13 $^{+0.04}_{-0.01}$ |
| MWC 480 stellar mass | 2.09 | +0.06/-0.04 | Msun | 5 | 2.09 $^{+0.06}_{-0.04}$ |
| MWC 480 Md/M* | 7 | ±1 | percent | 5 | we inferred a mass ratio $M_{\rm d} / M_\ast = 7\pm1$% |
| MWC 480 taper radius rt | 124 | +99/-21 | au | 5 | 124 $^{+99}_{-21}$ |
| MWC 480 gamma | 1.1 | +0.3/-0.1 | dimensionless | 5 | 1.1 $^{+0.3}_{-0.1}$ |
| Md bias in simulations (full inference) | <~20% | not stated | percent | 5 | biases for these parameters are $\lesssim$ 2% and $\lesssim$ 20%, respectively |
| Md bias from ignoring resolution bias (model B) | ~170% high | not stated | percent | 4 | higher $M_{\rm d}$ ($\sim$170%) |

## Qualitative findings

- Gaps at ~65 and 135 au with a pressure maximum near 100 au can explain kinematic oscillations in MWC 480  
  > "conspicuous kinematics features could be explained with localized density depletions at 65 and 135 au" (7 Summary)

## Claim tuples

- H: Can kinematics recover Md for massive disks? | E: Injection/recovery with three fiducial models (Md/M*=0.1) | R: Md biases <~20%, 90% intervals ±0.04–0.08 Msun | F: Method recovers Md and Sigma(r) within factor two for massive disks | **supported**
- H: Does beam smearing bias v_phi extraction? | E: Compare corrected vs uncorrected inference for model B | R: Uncorrected gives M* ~10% low and Md ~170% high | F: Resolution bias must be corrected | **supported**
- H: Lower limit of sensitivity in Md/M* | E: Variants of model B with Md=0.04–0.12 Msun | R: Posteriors broaden as ratio decreases | F: Good inference down to Md/M*~5% | **supported**
- H: Method works on real data | E: MWC 480 12CO+13CO MAPS cubes | R: Md=0.13 Msun, Md/M*=7±1% | F: Consistent with Zhang+21 thermo-chemical Sigma(r) | **supported**

## Reasoning

- Why this data: MWC 480 has geometry and CO surface similar to fiducial models, appears axisymmetric, no contamination  
  > "appears to be axisymmetric (cite: teague21), and does not suffer foreground or environmental contamination" (6.3 Demonstration with ALMA Data: MWC 480)
- Why this method: _not stated_
- Alternative: Full forward modeling of visibilities with radiative transfer rejected as too expensive  
  > "But that is an expensive task, since each likelihood computation is slow" (4)
- How they decided it was enough: _not stated_
- Limitation (authors): Non-axisymmetric substructure, flows, warps, magnetic pressure and 2D temperature uncertainty could bias results  
  > "the azimuthal averaging used in this analysis framework *will* generate artificial $v_\phi(r)$ structures that can bias the $M_{\rm d}$ inference" (6.2 Caveats and Potential)
- Caveat (inferred, ours): Synthetic tests use the same parametric model as the fit, so model mis-specification is only weakly tested
- Caveat (inferred, ours): MWC 480 temperature structure ad hoc; gap model manually tuned
- Caveat (inferred, ours): Single real-disk demonstration; geometry offsets differ from literature

## Reproducibility

- Data public (paper): MAPS archival data  
  > "We illustrated this approach using archival ALMA observations of the MWC 480 disk" (7 Summary)
- Products in archive: _not stated_
- Code: csalt on GitHub (github.com/seanandrews/csalt)  
  > "`csalt` (Andrews et al., *in preparation*)[^2]" (Software)
- Missing: Full MWC 480 priors and temperature-interpolation details
- Missing: Gap model manual tuning procedure
- Missing: Exact random seeds and draw counts for MWC 480
- Data volume (inferred): ~tens of GB (MAPS MWC 480 12CO/13CO cubes); synthetic data computed locally
- Score (inferred): 3/5, Public MAPS data and many parameters stated, but csalt unpublished and MWC 480 temperature and geometry steps partly ad hoc.
- Rediscovery candidate: no, Complex hierarchical pipeline with partly unstated MWC 480 settings and tools in preparation.

## Links

- Method: Veronesi et al. 2021 (cite: veronesi21) (first dynamical disk mass measurement)
- Method: Martire et al. 2024 (cite: martire24) (kinematic mass analysis of MAPS disks)
- Method: Andrews et al. 2021 (cite: andrews21) (geometry procedure)
- Companion: Öberg et al. 2021 (cite: maps1) (MAPS data source)
- Companion: Zhang et al. 2021 (cite: zhang21) (comparison thermo-chemical Sigma(r))
- Related: MAPS

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
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
  "facts": 86,
  "stated": 55,
  "rate": 0.64
 },
 "evidence_ok": true
}
```
