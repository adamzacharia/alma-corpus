# Dust and Gas in the Disk of HL Tauri: Surface Density, Dust Settling, and Dust-to-gas Ratio

`2016ApJ...816...25P` | The Astrophysical Journal 2016 | first author: Pinte, C. | arXiv: 1508.00584 | DOI: 10.3847/0004-637X/816/1/25

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the dust surface density, ring/gap masses, grain-size variation, dust settling (alpha) and gas-to-dust ratio in the HL Tau disk, from radiative transfer modelling of the ALMA Band 3, 6 and 7 continuum data?  
  > "We investigate whether a single unified dust model can reproduce both the ALMA images and SED, and compare the dust and gas disk also observed by ALMA." (Introduction)
- Target **HL Tau**: coordinates _not stated_; z/distance 140 pc  
  > "HL Tau is a T Tauri star of spectral energy distribution (SED) Class I–II in the Taurus molecular cloud, at a distance of 140 pc." (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00015.SV
- bands: Bands 3, 6, 7 continuum (0.8-3 mm); Band 3 12CO J=1-0 and HCO+ J=1-0  
  > "The calibrated spectral line data sets in band 3 for $^{12}$CO $J$=1-0 and HCO$^+$ $J$=1-0 were also downloaded and CLEANed." (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: up to ~15 km  
  > "HL Tau was recently observed with ALMA using baselines up to $\sim$ 15 km at wavelengths from 0.8-3 mm" (Introduction)
- angular resolution: down to 3.5 AU; HCO+ 0.25 arcsec, CO 0.2 arcsec (tapered)  
  > "which resulted in spatial resolutions down to 3.5 AU" (Introduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Science verification data from the ALMA Long Baseline Campaign  
  > "HL Tau was observed as a science verification target within the ALMA Long Baseline Campaign" (Observations)
- Line: 12CO J=1-0 (not stated)
- Line: HCO+ J=1-0 (not stated)
- External data: Stellar Teff = 4000 K and L* = 11 Lsun  
  > "We assume passive heating and fix the properties of the central star to $T_\mathrm{eff} = 4\,000\,$K and $L_* = 11\,L_\odot$ (cite: Menshchikov99)." (Radiative transfer model) [from (cite: Menshchikov99)]
- External data: Accretion rate 8.7e-8 Msun/yr from Brgamma luminosity  
  > "The accretion rate of the disk surrounding HL Tau was estimated to $8.7\,10^{-8}\,$M$_\odot$.yr$^{-1}$ from the Br$\gamma$ line luminosity (cite: Beck10)." (Discussion - a coherent model for the HL Tau disk?) [from (cite: Beck10)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated continuum data and CLEANed images downloaded from the ALMA Science portal, with self-calibration tables applied  
  > "together with the tables for self-calibration, which we applied to the data." (Observations)
- flux calibrator: _not stated_
- flux scale uncertainty: 10% calibration uncertainty added in quadrature in chi2  
  > "to which we added quadratically a 10 % calibration uncertainty" (Building a model of the HL Tau disk)
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN; model visibilities from the CASA simulator using ft  
  > "This computes the model visibilities at the exact same ($u$,$v$) coordinates as the observations using the *ft* task." (Building a model of the HL Tau disk)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: HCO+: default CLEAN parameters and uv taper from ALMA LBC paper (0.25 arcsec); CO: taper giving 0.2 arcsec  
  > "CLEANing with a $u$$v$ taper giving a spatial resolution of 0.2 arcsec was found to be a good compromise" (Observations)
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

- Default CLEAN parameters and uv taper for HCO+ taken from the ALMA LBC paper  
  > "The default CLEAN parameters and $u$$v$ taper from were used for HCO$^+$ giving a resolution of 0.25 arcsec." (Observations) [from (cite: ALMA_LBC)]
- Standard disk parameters  
  > "We use standard disk parameters to describe the disk structure (cite: Pinte08; Andrews09)" (Continuum modeling approach) [from (cite: Pinte08; Andrews09)]
- Procedure for combining band surface densities into one model  
  > "we adopt a procedure similar to the one used in (cite: Pinte07) and (cite: Gonzalez12)" (Surface density profile and radial concentration of large grains) [from (cite: Pinte07; Gonzalez12)]
- Ring/gap nomenclature  
  > "We use the same nomenclature as in to name the gaps and rings." (Surface density profile and radial concentration of large grains) [from (cite: ALMA_HLTau)]

### Not stated but needed to reproduce (our reading)

- Exact CLEAN parameters (robust, cell, image size, masks, niter) for continuum
- CASA version
- Ring/gap positions and inclination/PA used
- Line-free channels and continuum subtraction for CO/HCO+
- Exact modified CASA simulator code
- Stopping criteria for the settling alpha search and the grid of alpha values
- Opacity calculation and dust optical constants details beyond those cited
- Central source position/offset conventions

## Analysis recipe

1. **Extract and invert major-axis brightness profile to surface density**: Average both sides of the major-axis profile, deconvolve with a Gaussian beam, convert to surface density with a power-law T (exponent -0.5), then iterate MCFOST models convolved with the beam, correcting surface density by the observed/model ratio  
  > "The surface density at any point in the disk is then corrected by the ratio of the observed profile divided by the model profile." (Building a model of the HL Tau disk)
   - software: MCFOST
   - parameter: Ratio limited to 0.8-1.2; converged when profile changes <1%; ~30 iterations  
  > "this ratio is limited between 0.8 and 1.2. The procedure is iterated until the model brightness profile does not change by more than 1 % at any radius." (Building a model of the HL Tau disk)
   - assumption: 2D axisymmetric disk; h0=10 AU at 100 AU, beta=1.15, outer radius 150 AU, a_min=0.03 um, a_max=3 mm, p=-3.5  
  > "$a_\mathrm{min}$ and $a_\mathrm{max}$ are set to $0.03\,\mu$m and 3 mm and we initially use $p=-3.5$" (Radiative transfer model)
   - fitting: Iterative image-plane inversion, not a sampler  
  > "The procedure is iterated until the model brightness profile does not change by more than 1 % at any radius." (Building a model of the HL Tau disk)
   - validation: Comparison of CLEANed model and observed images  
  > "the observed and modeled images were compared for consistency" (Building a model of the HL Tau disk)
2. **Combine bands into a single multi-grain-size model**: Assign band 3, 6, 7 surface densities to grains of 0.4, 0.18, 0.11 mm; interpolate in log grain size; no extrapolation outside  
  > "the surface densities from bands 3, 6, and 7 were used to define the distribution of the grains of size 0.4, 0.18, and 0.11 mm respectively." (Surface density profile and radial concentration of large grains)
   - software: MCFOST
   - fitting: _not stated_
   - validation: Local grain-size slope compared to -3.5 and -4.5 models  
  > "The grain distribution has a local slope close to -3.5 up to 75 AU, while it approaches -4.5 between 75 and 120 AU" (Surface density profile and radial concentration of large grains)
3. **Simulate visibilities and evaluate chi2**: Average data in 300 s bins, compute model visibilities with the CASA simulator at observed uv points, add noise from median PWV, CLEAN as observations, compute chi2  
  > "we first average the observed data in time (using 300s bins) and in frequency to obtain one single continuum channel per available spectral window." (Building a model of the HL Tau disk)
   - software: CASA
   - parameter: 229910, 420668, 571960 visibilities in bands 3, 6, 7  
  > "After binning, we have 229 910, 420 668 and 571 960 visibilities in bands 3, 6, and 7 respectively." (Building a model of the HL Tau disk)
   - fitting: chi2 with formal weights plus 10% calibration uncertainty; no full Bayesian analysis  
  > "a full Bayesian analysis taking into account the potential correlations between the densities in the various gaps and rings is out of reach with current computing facilities." (Surface density profile and radial concentration of large grains)
   - validation: Unbinned visibilities change chi2 by <2%  
  > "the $\chi^2$ were not affected by more than 2 %" (Building a model of the HL Tau disk)
4. **Ring and gap masses with uncertainties**: Integrate surface density between gaps; vary each gap depth by a constant factor and report range where chi2 <= 1.5 x min chi2  
  > "we report the interval range where the $\chi^2$ remains smaller than 1.5 the minimum $\chi^2$ value." (Surface density profile and radial concentration of large grains)
   - software: MCFOST, CASA
   - fitting: _not stated_
   - validation: Threshold corresponds to visible visibility differences and >3 sigma residuals  
  > "this threshold corresponds to visible differences in the binned visibility curves as well as residuals above 3 $\sigma$ in the CLEAN maps" (Surface density profile and radial concentration of large grains)
5. **Constrain dust settling (alpha)**: Compare 2D models with different alpha (diffusive settling, Fromang & Nelson eq. 19) to the ALMA image gap contrast over azimuth  
  > "produces the best agreement with most of the observed features in the ALMA image, with rings that are well separated at all azimuthal angles." (Degree of dust settling)
   - software: MCFOST
   - parameter: Schmidt number 1.5  
  > "$S_c$ is the Schmidt number, which we fix to 1.5." (Radiative transfer model)
   - assumption: Inclination ~47 deg  
  > "Because the disk is inclined by $\sim$ 47$^\circ$" (Degree of dust settling)
   - fitting: Visual comparison of few alpha values  
  > "A small value of the millimeter dust scale height, $h_{1\,\!\mathrm{mm}}$ = 0.70 AU, equivalent to $\alpha = 3\times 10^{-4}$ produces the best agreement with most of the observed features in the ALMA image" (Degree of dust settling)
   - validation: Compared models with h1mm=0.70 and 2.15 AU and no settling  
  > "The model with $h_{1\,\!\mathrm{mm}}=2.15$ AU reproduces this behavior but does not provide a strong enough contrast in the other rings." (Degree of dust settling)
6. **Gas kinematics from CO and HCO+**: Compare major-axis PV diagrams with Keplerian curves for 1.7 and 1.0 Msun at i=47 deg (not formal fits)  
  > "Although not formal fits, the high gas velocities and shape of these PV diagrams suggest that the stellar mass is closer to $\sim$ 1.7 M$_{\odot}$" (The gas disk: 12CO and HCO+.)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **MCFOST** : Radiative transfer modelling of continuum  
  > "we use the radiative transfer code MCFOST (cite: Pinte06; Pinte09)" (Continuum modeling approach)
- **CASA** : CLEAN imaging, modified simulator and ft for model visibilities  
  > "The final simulated visibilities and images were produced by applying a modified version of the CASA simulator to the model." (Building a model of the HL Tau disk)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total dust mass of best model | 5e-4 | not stated | Msun | 2 | The total dust mass of the best model is 5 10$^{-4}$ M$_\odot$. |
| Total chi2 of final model | 1282 | not stated | dimensionless | 3 | Our final model has a total $\chi^2$ of 1282. |
| Unresolved central source flux (band 3, 6, 7) | 1.57, 1.90, 2.59 | not stated | mJy | 1 | 1.57, 1.90, and 2.59 mJy at band 3, 6 and 7 respectively |
| Mass of ring B7 | 123 | +34/-24 | Mearth | 4 | / B7 / $123_{-24}^{+34}$ / 16 / ... / 4.9 / 1.3 / |
| Missing dust mass in gap D7 | 36 | +11/-20 | Mearth | 4 | / D7 / 91.0 / 21 / $36_{-20}^{+11}$ / 11 / 9.9 / |
| Alpha from settling | 3e-4 | not stated | dimensionless | 5 | $h_{1\,\!\mathrm{mm}}$ = 0.70 AU, equivalent to $\alpha = 3\times 10^{-4}$ |
| Gas-to-dust ratio in midplane at 100 AU (dust to 3 mm) | ~6 | not stated | dimensionless | 5 | the gas-to-dust mass ratio in the disk midplane is $\approx 6$ at a radius of 100 AU |
| Stellar mass from gas kinematics | 1.7 | not stated | Msun | 6 | suggest that the stellar mass is closer to $\sim$ 1.7 M$_{\odot}$ |

## Qualitative findings

- Outer ring is depleted in mm-sized grains relative to central rings  
  > "Our model indicates that the outermost ring is depleted in millimeter grains compared to the central rings." (abstract)
- Mm dust disk is geometrically thin and strongly settled  
  > "indicates that the millimeter dust disk is geometrically thin (scale height $\approx$ 1 AU at 100 AU)" (abstract)

## Claim tuples

- H: Are gaps strongly depleted in mm dust? | E: Radiative transfer inversion of three bands with visibility check | R: Density depleted by >10 in main gaps; missing masses up to ~40 Mearth | F: Gaps consistent with removal of dust possibly into rocky cores | **supported**
- H: Do dust properties vary radially? | E: Compare surface densities from three bands with p=-3.5 and -4.5 | R: Local slope -3.5 to 75 AU, ~-4.5 at 75-120 AU | F: Large grains depleted in outer ring | **supported**
- H: How settled is the mm dust? | E: Compare 2D models with various alpha to image gap contrast | R: alpha ~3e-4, h1mm = 0.70 AU | F: Highly settled; gas/dust ratio ~5 in thin layer | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Full Bayesian analysis not feasible due to computing cost, so gaps explored independently  
  > "Due to the computing cost of the procedure (dominated by the calculations of the visibilities in CASA)" (Surface density profile and radial concentration of large grains)
- Alternative: Steeper p=-4.5 gives matching outer ring but mismatching central regions  
  > "A model with a steeper slope, $p=-4.5$, results in similar surface density profiles at all bands in the outer ring" (Surface density profile and radial concentration of large grains)
- How they decided it was enough: _not stated_
- Limitation (authors): Central peak could not be reproduced; unresolved source added ad hoc  
  > "we could not reproduce the compact and peaked emission at the position of the star" (Building a model of the HL Tau disk)
- Limitation (authors): Opacity values uncertain to a factor of a few  
  > "should be considered with an uncertainty of a factor a few" (Surface density profile and radial concentration of large grains)
- Caveat (inferred, ours): Dust composition, opacity and fixed gas scale height drive masses and gas/dust ratio
- Caveat (inferred, ours): Settling constraint is from visual comparison of few models
- Caveat (inferred, ours): Axisymmetry assumed despite ring offsets
- Caveat (inferred, ours): Uncertainties from one-at-a-time chi2 ranges, no correlations

## Reproducibility

- Data public (paper): Data downloaded from the ALMA Science portal (science verification)  
  > "The band 3, 6, and 7 calibrated continuum data sets and CLEANed images were downloaded from the ALMA Science portal" (Observations)
- Products in archive: _not stated_
- Missing: Modified CASA simulator code
- Missing: Final surface density profiles in numeric form
- Missing: Exact imaging parameters
- Data volume (inferred): ~tens of GB
- Score (inferred): 5/5, Public data and a clear iterative recipe, but MCFOST setup, imaging parameters and simulator modifications are incompletely given.
- Rediscovery candidate: no, Recipe depends on a custom pipeline and a modified simulator; not fully specified.

## Links

- Method: (cite: Pinte06; Pinte09) (MCFOST radiative transfer code)
- Method: (cite: Fromang09) (Dust settling vertical profile)
- Companion: (cite: ALMA_HLTau) (ALMA HL Tau Long Baseline Campaign results)
- Companion: (cite: ALMA_LBC) (Observation details)
- Related: ALMA Long Baseline Campaign

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 44,
  "rate": 0.557
 },
 "evidence_ok": true
}
```
