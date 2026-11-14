# Unveiling Two Deeply Embedded Young Protostars in the S68N Class 0 Protostellar Core with JWST/NIRSpec

`2025ApJ...985..225L` | The Astrophysical Journal 2025 | first author: Le Gouellec, Valentin J. M. | arXiv: 2410.11095 | DOI: 10.3847/1538-4357/adcac4

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation
- Question: What are the near-infrared photospheric, disk, jet and molecular-gas properties of the two embedded Class 0 protostars (NC and SC) in S68N, as seen with JWST NIRSpec?  
  > "In the present study, we aim to investigate further the nature of the driving sources within the S68N protostellar core." (Introduction)
- Target **S68N protostellar core (NC and SC sources)**: coordinates NC: 18:29:48.13 +01:16:44.69; SC: 18:29:48.06 +01:16:43.98 (IR positions, J2000)  
  > "S68N[^1] is a bona fide protostellar core located in the Serpens Main star forming region, for which we adopt a distance of 445 pc" (Introduction); z/distance 445 pc  
  > "S68N[^1] is a bona fide protostellar core located in the Serpens Main star forming region, for which we adopt a distance of 445 pc" (Introduction); distance from OrtizLeon2017b; Zucker2019; Herczeg2019; Zucker2020  
  > "S68N[^1] is a bona fide protostellar core located in the Serpens Main star forming region, for which we adopt a distance of 445 pc" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00726.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 170 AU (CO) and 240 AU (dust continuum)  
  > "The ALMA CO and dust continuum data have a spatial resolutions of 170 and 240 AU, respectively." (3.4 ALMA molecular emission)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival ALMA program 2013.1.00726.S (PI: C. L. H. Hull); CO(2-1) and 870 um continuum from earlier papers  
  > "(ALMA program 2013.1.00726.S, PI: C. L. H. Hull)" (3.4 ALMA molecular emission)
- Line: CO J=2-1 (not stated)
- Other facility **JWST NIRSpec IFU (GTO 1186)**: 1.7-5.3 um IFU spectroscopy of NC and SC sources; main data set  
  > "Our JWST spectroscopic observations of S68N were executed on 2023 April 16 UT under GTO Program 1186 (P.I Thomas Greene)." (2.2 JWST NIRSpec)
- Other facility **JWST NIRCam (GO 1611)**: Three-colour context image of the core  
  > "The JWST NIRCam data are from the Cycle 1 GO program 1611 (PI: Klaus M. Pontoppidan) and are presented by (cite: Green2024)." (2.1)
- External data: ALMA 870 um dust continuum and CO(2-1) data of S68N, and outflow mass ejection rate and force  
  > "the ALMA 870 $\mu$m dust continuum observations from (cite: LeGouellec2019a) and (cite: Tychoniec2019)" (3.4 ALMA molecular emission) [from LeGouellec2019a; Tychoniec2019]
- External data: Shock model grid (Paris-Durham, ~14000 models)  
  > "We explore the recent shock model grid by (cite: Kristensen2023), that uses the Paris-Durham shock code over an extensive grid of $\sim$ 14 000 plane-parallel stationary shock models." (4.2.1 The shock model grid) [from Kristensen2023]

## Processing

### Calibration

- pipeline or manual: Standard JWST pipeline with custom modifications (nsclean, bad-pixel flagging) for NIRSpec; ALMA calibration not described  
  > "The data reduction was performed by following the standard JWST data reduction pipeline of version 1.13.0 and a reference file version of pmap 1174 with modifications as described below." (2.2 JWST NIRSpec)
- casa version: _not stated_
- pipeline version: JWST pipeline 1.13.0, pmap 1174  
  > "standard JWST data reduction pipeline of version 1.13.0 and a reference file version of pmap 1174" (2.2 JWST NIRSpec)
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

- ALMA 870 um continuum and CO(2-1) data products taken from earlier papers  
  > "the ALMA 870 $\mu$m dust continuum observations from (cite: LeGouellec2019a) and (cite: Tychoniec2019)" (3.4 ALMA molecular emission) [from LeGouellec2019a; Tychoniec2019]
- Photosphere+disk model form adopted from earlier work  
  > "we model the observed flux between 1.9 and 2.45 $\mu$m with the following model (adopted from (cite: Greene2018))" (5.1 Modeling setup) [from Greene2018]
- Likelihood construction for the shock grid follows earlier work  
  > "We adopted the same technique as (cite: Poorta2023) to build likelihood distributions for each modeled parameter of the non-uniformly sampled shock model grid" (Appendix shock models) [from Poorta2023]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, imaging parameters and CASA version for the CO and continuum maps (taken from earlier papers)
- Custom JWST pipeline modules (bad-pixel flagging) are only described, not released
- Exact H2 line list and aperture positions used for each jet location in the shock fits
- MCMC walker initialisation and Starfish settings in detail

## Analysis recipe

1. **Reduce NIRSpec IFU cubes**: JWST pipeline with nsclean, custom DO_NOT_USE flagging, outlier_detection and emsm cube_build  
  > "build the spectral cube in the "cube_build" step with the "emsm" weighting method" (2.2 JWST NIRSpec)
   - software: JWST pipeline, nsclean
   - parameter: outlier_detection threshold_percent = 99.8, kernel_size = 33  
  > "with threshold_percent = 99.8 and a kernel_size = 33" (2.2 JWST NIRSpec)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract 1D spectra and fit emission lines**: 0.4 arcsec aperture; Gaussian line fits with scipy curve_fit; detection requires S/N >= 10  
  > "we require the signal-to-noise ratio (S/N) of the line emission peak" (3.3 NIRSpec emission line maps)
   - software: scipy
   - parameter: Fixed aperture radius 0.4 arcsec  
  > "We use a fixed aperture radius of $0.4\ensuremath{''}$ to extract the 1D spectra" (3.2)
   - fitting: 1D Gaussians with pipeline uncertainties propagated  
  > "We propagate the uncertainty values from the pipeline into the `curve_fit` routine of the `scipy` python package to derive the uncertainty of the fitted line profile parameters" (3.3 NIRSpec emission line maps)
   - validation: _not stated_
3. **H2 extinction, o/p ratio and excitation**: Line-pair extinction with Pontoppidan2024a law; Boltzmann single-temperature fit of level populations  
  > "We fit a single temperature component and extract the total column density of molecules $N_{\textrm{tot}}$" (4.1.3 H2 excitation)
   - assumption: Optically thin H2 lines; single temperature  
  > "As the H$_2$ lines are optically thin, their line flux is proportional to the column density" (4.1.3)
   - fitting: _not stated_
   - validation: Other extinction laws give values within 0.1 mag  
  > "Using other extinction laws such as (cite: Indebetouw2005; Hensley2021) typically yields extinction values within 0.1 mag" (4.1.1)
4. **Fit shock model grid to H2 jet**: chi2 on log flux ratios against Kristensen2023 grid; likelihood 1/chi2, marginalised per parameter  
  > "We convert all $\chi^2$ values to a likelihood taking $1/\chi^2$." (Appendix shock models)
   - software: Paris-Durham shock code
   - assumption: Stationary plane-parallel shocks, perpendicular B field  
  > "the magnetic field orientation is assumed to be perpendicular to the direction of shock propagation (no oblique shocks), which is purely 1D" (4.2.1 The shock model grid)
   - fitting: Grid likelihood, no sampler  
  > "We convert all $\chi^2$ values to a likelihood taking $1/\chi^2$." (Appendix: shock models)
   - validation: Compared model o/p ratio and column densities with data  
  > "We note that our estimates of H$_2$ column densities along the jet (see Figure [8](#fig:H2_param_jet)) overestimate the column density of the best models by a factor $\sim$2." (4.2.1)
5. **Jet energetics**: Mdot = mu*mH*N*A/t_dyn; force = Mdot*v_jet  
  > "We compute the mass-loss rate from the driving protostar of the SC outflow as follows" (4.2.2)
   - assumption: mu_H2 = 2.8; inclination 64 deg from |dv|/vs  
  > "we use a value of 2.8; (cite: Kauffmann2008)" (4.2.2)
   - fitting: _not stated_
   - validation: Compared with ALMA CO outflow rates of Tychoniec2019  
  > "We also compare these values with the outflow mass ejection rate and force computed by (cite: Tychoniec2019) using ALMA CO ($J$ = 2 $\rightarrow\,$1) data" (4.2.3 Energetics of the molecular jet)
6. **CO ro-vibrational excitation and 12C/13C**: Multi-Gaussian line fits with HITEMP list, population diagrams with two rotational temperatures, vibrational temperatures, slab models  
  > "We use the HITEMP CO line list from the HITRAN database (cite: Rothman2010; Gordon2022) to retrieve the line transition data tables of the first five rotational ladders of $^{12}$CO" (4.3 CO molecular wind)
   - assumption: CO only in emission; H2-derived extinction used to de-redden  
  > "In this Section, we treat this SC source spectrum as having CO only in emission." (4.3 CO molecular wind)
   - fitting: chi2 minimisation for slab models  
  > "We find the $N_{^{13}\textrm{CO}}$ value that minimizes the reduced $\chi^2$ for the two spectral regions" (4.3.3 CO isotope ratio)
   - validation: _not stated_
7. **Fit NC photosphere plus disk**: Starfish with BT-Settl grid, emcee MCMC, 1.9-2.45 um  
  > "We use the emcee python package (cite: ForemanMackey2013) to perform the MCMC using this Starfish likelihood estimation." (Appendix MCMC)
   - software: Starfish, emcee
   - parameter: alpha fixed to 1.54; R_max fixed to 10 AU; Teff prior 2600-5550 K, log g 0.5-5  
  > "We fix $\alpha$ to $1.54$ to match the extinction law from (cite: Pontoppidan2024a) used throughout this paper. We fix $R_{\textrm{max}}$ to 10 AU" (5.1 Modeling setup)
   - assumption: Solar metallicity; distance 445 pc  
  > "metallicity $[{\textrm{Fe/H}}]$ (that we restrict to the solar value)" (5.1 Modeling setup)
   - fitting: MCMC, converged within 5000 steps, 2000 additional  
  > "Starfish converged within the first 5,000 steps and was run for 2,000 additional steps after convergence." (Appendix MCMC)
   - validation: Tested log g sensitivity to continuum level and shape  
  > "We tested the sensitivity of log $g$ to continuum level and shape, and found we retrieve the same log $g$ (and $T_{\star,\textrm{eff}}$) within 1 sigma." (5.2)

## Software

- **Starfish** : Photospheric spectral fitting  
  > "We use the Starfish modeling framework from (cite: Czekala2015) and (cite: GullySantiago2017)" (5.1)
- **emcee** : MCMC sampling  
  > "We use the emcee python package (cite: ForemanMackey2013)" (Appendix MCMC)
- **JWST pipeline** 1.13.0: NIRSpec reduction  
  > "standard JWST data reduction pipeline of version 1.13.0" (2.2)
- **nsclean** : Correlated noise removal  
  > "We then applied the `nsclean` algorithm (cite: Rauscher2024)" (2.2)
- **scipy** : curve_fit Gaussian line fitting  
  > "`curve_fit` routine of the `scipy` python package" (3.3)
- **Paris-Durham shock code** : Shock grid models of H2  
  > "We explore the recent shock model grid by (cite: Kristensen2023), that uses the Paris-Durham shock code over an extensive grid of $\sim$ 14 000 plane-parallel stationary shock models." (4.2.1 The shock model grid)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| NC Teff | 3113 | +23/-26 | K | 7 | $3113^{+23}_{-26}$ |
| NC log g | 1.95 | +0.16/-0.15 | cm s^-2 | 7 | $1.95^{+0.16}_{-0.15}$ |
| NC A_K (photosphere fit) | 4.74 | +/-0.15 | mag | 7 | $4.74^{+0.15}_{-0.15}$ |
| K-band veiling r_K | 1.25 | not stated | dimensionless | 7 | we obtain $r_K = 1.25$ |
| H2 excitation temperature SC | 2745 | 64 | K | 3 | $2745 \pm 64$ K and $2579 \pm 130$ K for the SC and NC sources |
| H2 o/p ratio SC | 2.6 | 0.3 | dimensionless | 3 | 2.6 $\pm$ 0.3 and 2.7 $\pm$ 0.3 for the SC and the NC source |
| SC A_K from H2 | 7.5 | 1.0 | mag | 3 | $A_K\,=\,4.8\,\pm\,1.4$ and $7.5\,\pm\,1.0$ mag |
| Jet inclination | 64 | not stated | deg from line of sight | 5 | obtain a value of $64^{\circ}$ (with respect to the line-of-sight) |
| 12CO/13CO from column densities | 42 | 22 | dimensionless | 6 | $N_{^{13}\textrm{CO}_{v\,=\,1\rightarrow0}}\,=\,42\pm$22 |
| NC mass accretion rate | 3e-6 to 4e-5 | not stated | Msun/yr | 0 | $\dot{M} \sim$ $3\times10^{-6}$—$4\times10^{-5} M_\odot \textrm{yr}^{-1}$ |

## Qualitative findings

- SC drives a collimated hot molecular jet best matched by fast C-type shocks; no [Fe II] detected  
  > "fast $C$-type shocks ($\geq$ 30 km s$^{-1}$), with high pre-shock density ($\geq$ $10^7$ cm$^{-3}$)" (abstract)

## Claim tuples

- H: NC source shows a young photosphere plus hot disk | E: Starfish MCMC fit of 1.9-2.45 um spectrum | R: Teff 3113 K, log g 1.95, r_K 1.25 | F: Young low-mass photosphere with hot disk, though H I accretion lines are absent | **supported**
- H: H2 emission in SC jet is shock excited | E: Compare H2 excitation along jet to Kristensen2023 grid | R: Best models are fast, strongly magnetised C-type shocks | F: Fast dense C-type shocks with b~3-10 | **supported**
- H: CO excitation is purely collisional | E: CO population and vibrational temperature analysis | R: Higher vibrational levels less populated, high Tvib | F: Non-LTE effects such as UV/IR pumping | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: J- and CJ-type shocks rejected because they differ from observed H2 level populations  
  > "J- and CJ-type shock models significantly differ from observed H$_2$ level population." (4.2.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Scattered light dominates NIR continuum so stellar parameters and radii are underestimated  
  > "This causes the measured photospheric and circumstellar disk emitting radii to be underestimated." (5.3)
- Caveat (inferred, ours): Shock grid lacks self-irradiated J-type shocks
- Caveat (inferred, ours): Extinction uncertainties not propagated
- Caveat (inferred, ours): Viscous disk accretion estimate is highly model-dependent

## Reproducibility

- Data public (paper): JWST data from MAST; ALMA project 2013.1.00726  
  > "The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Custom pipeline module code
- Missing: Details of H2 line selection per aperture
- Data volume (inferred): JWST NIRSpec IFU cubes, a few GB; ALMA used only as published maps
- Score (inferred): 3/5, JWST recipe is mostly described and public, but ALMA is only secondary and custom code is unreleased.
- Rediscovery candidate: no, ALMA plays a minor role and the main results come from JWST analysis with custom steps.

## Links

- Method: Kristensen2023 (Shock model grid)
- Method: Czekala2015 (Starfish framework)
- Companion: LeGouellec2019a (ALMA data of S68N)
- Companion: Greene2018 (Earlier Keck NC photosphere model)
- Related: JOYS
- Related: CALYPSO

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 48,
  "rate": 0.545
 },
 "evidence_ok": true
}
```
