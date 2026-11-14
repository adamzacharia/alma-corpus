# Dual-wavelength ALMA Observations of Dust Rings in Protoplanetary Disks

`2020ApJ...898...36L` | The Astrophysical Journal 2020 | first author: Long, Feng | arXiv: 2006.03120 | DOI: 10.3847/1538-4357/ab9a54

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Do dust rings in three Taurus disks appear at the same locations and widths at 1.3 and 2.9 mm, and what do disk sizes, ring widths, spectral index and optical depth imply for dust trapping and grain growth?  
  > "This comparison aims to test the presence of dust traps and also provide insights for grain property changes, to better understand the role of dust substructures in planet formation process." (1 Introduction)
- Target **DS Tau**: coordinates 2MASS 04474859+2925112  
  > "| DS Tau | 04474859+2925112 | 159 | M0.4 | 3792 | 0.25 | 0.58$^{+0.17}_{-0.13}$" (Table 1); z/distance 159 pc  
  > "| DS Tau | 04474859+2925112 | 159 | M0.4 | 3792 | 0.25 | 0.58$^{+0.17}_{-0.13}$" (Table 1); distance from Gaia DR2 parallax  
  > "| DS Tau | 04474859+2925112 | 159 | M0.4 | 3792 | 0.25 | 0.58$^{+0.17}_{-0.13}$" (Table 1)
- Target **GO Tau**: coordinates 2MASS 04430309+2520187  
  > "| GO Tau | 04430309+2520187 | 144 | M2.3 | 3516 | 0.21 | 0.36$^{+0.13}_{-0.09}$" (Table 1); z/distance 144 pc  
  > "| GO Tau | 04430309+2520187 | 144 | M2.3 | 3516 | 0.21 | 0.36$^{+0.13}_{-0.09}$" (Table 1); distance from Gaia DR2 parallax  
  > "| GO Tau | 04430309+2520187 | 144 | M2.3 | 3516 | 0.21 | 0.36$^{+0.13}_{-0.09}$" (Table 1)
- Target **DL Tau**: coordinates 2MASS 04333906+2520382  
  > "| DL Tau | 04333906+2520382 | 159 | K5.5 | 4277 | 0.65 | 0.98$^{+0.84}_{-0.15}$" (Table 1); z/distance 159 pc  
  > "| DL Tau | 04333906+2520382 | 159 | K5.5 | 4277 | 0.65 | 0.98$^{+0.84}_{-0.15}$" (Table 1); distance from Gaia DR2 parallax  
  > "| DL Tau | 04333906+2520382 | 159 | K5.5 | 4277 | 0.65 | 0.98$^{+0.84}_{-0.15}$" (Table 1)

## Data provenance

- ALMA projects: 2018.1.00614.S, 2016.1.01164.S
- bands: Band 3 (2.9 mm, new) and Band 6 (1.3 mm, previous)  
  > "| 225.5 (B6) | 82.5 | 0.13$\times$0.09 |" (Table 1)
- frequencies and spectral setup: 3 continuum SPWs at 98, 100, 112 GHz, 1.875 GHz each; 4th window for 13CO and C18O, ~0.7 km/s channels  
  > "Three spectral windows were set up for continuum observations, centered at 98, 100, and 112 GHz, each with a bandwidth of 1.875 GHz." (2 ALMA Band 3 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Band 3: 90 m to ~8.5 km; Band 6: 21 m to 3.6 km  
  > "The array was configured to span baselines from 90 m to $\sim$8.5 km with 43–45 antennas" (2 ALMA Band 3 Observations)
- angular resolution: ~0.1" (15 au)  
  > "both at an angular resolution of $\sim0.1\ensuremath{''}$ (15 au for the distance of Taurus)" (abstract)
- max recoverable scale: _not stated_
- sensitivity: RMS 12.8-16.5 uJy/beam at Band 3; 58.5-82.5 at Band 6  
  > "| 105 (B3) | 16.5 | 0.13$\times$0.09 |" (Table 1)
- time on source: 66.5, 77.6, 67.3 min for DS Tau, GO Tau, DL Tau  
  > "The total on-source integration time were 66.5 min, 77.6 min, and 67.3 min for DS Tau, GO Tau, and DL Tau, respectively." (2 ALMA Band 3 Observations)
- observing dates: 2019 July 16-28  
  > "were taken between 2019 July 16 and July 28" (2 ALMA Band 3 Observations)
- pi or archival as stated: _not stated_
- Other facility **Gaia DR2**: distances  
  > "The distance for individual stars is adopted from the Gaia DR2 parallax" (Table 1)
- External data: 1.3 mm Band 6 data, ring locations, inclinations/PAs priors  
  > "identified from our previous 1.3 mm survey at 0.1$''$ resolution" (1 Introduction) [from (cite: Long2018)]
- External data: Stellar mass and age  
  > "Stellar mass and age are adopted from (cite: Long2019)." (Table 1) [from (cite: Long2019)]
- External data: Spectral types  
  > "Spectral type is adopted from (cite: herczeg2014)" (Table 1) [from (cite: herczeg2014)]
- Simulation/model as data: Dust evolution model with embedded planet at 33 au, alpha=1e-3, 5.8 MJup disk, 0.58 Msun star, vfrag 10 m/s  
  > "We take an $\alpha$-viscosity parameter of $10^{-3}$ (independent of radius and time)" (4.1.1 Model setup)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "The data were calibrated by ALMA pipeline with the Common Astronomy Software Package (CASA), version 5.4.0." (2 ALMA Band 3 Observations)
- casa version: CASA 5.4.0  
  > "Further calibration and imaging were also performed with this same version." (2 ALMA Band 3 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800  
  > "Bandpass and flux calibrations used observations of the quasar J0510+1800 for all executions." (2 ALMA Band 3 Observations)
- flux scale uncertainty: ~10% assumed at each wavelength  
  > "a $\sim10$% flux calibration uncertainty at each wavelength would introduce a systematic offset of $\sim$0.2 in $\alpha_{\rm mm}$" (3.2 Spectral index)
- self calibration: Two rounds phase-only (120 s, 60 s) for GO Tau and DL Tau; not for DS Tau  
  > "We performed two rounds of phase-only self-calibration with solution intervals of 120s and 60s" (2 ALMA Band 3 Observations)

### Imaging

- task: tclean mtmfs, nterms=2  
  > "The Band 3 continuum images were obtained with the multi-term, multi-frequency synthesis algorithm (`mtmfs`) in `tclean` with *nterms* = 2." (2 ALMA Band 3 Observations)
- deconvolver: _not stated_
- weighting robust: DS Tau robust=-0.5; GO Tau and DL Tau robust=0.0  
  > "For DS Tau, we started with Briggs weighting with robust = -0.5 at both bands" (2 ALMA Band 3 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: imsmooth to common beams  
  > "the final images at both bands were convolved into a common beam size using the `imsmooth` task." (2 ALMA Band 3 Observations)
- final beam: 0.13x0.09" (DS Tau); 0.13x0.10" (GO Tau, DL Tau)  
  > "Both images were then convolved to reach a targeted beam size of $0.13\ensuremath{''}\times0.09\ensuremath{''}$." (2 ALMA Band 3 Observations)
- final rms: 12-16 uJy/beam at Band 3  
  > "The 1$\sigma$ noise levels measured in the signal-free regions are in the range of 12 to 16 $\mu$Jy beam$^{-1}$" (2 ALMA Band 3 Observations)

### Inherited from earlier work

- Parametric intensity profile forms and number of rings from the 1.3 mm analysis  
  > "we adopt the same intensity profiles as (cite: Long2018)" (3.1 Disk Morphology) [from (cite: Long2018)]
- Priors on inclination and PA centered on earlier values  
  > "Priors on disk inclination and position angles are centered at what identified before (cite: Long2018) with a range of $\pm$20$\ensuremath{^\circ}$." (3.1 Disk Morphology) [from (cite: Long2018)]
- Disk size metric of fixed fraction of encircled flux  
  > "we adopt a generic definition of size - the location where a fixed fraction of the total disk flux is encircled, as introduced by (cite: Tripathi2017)." (3.1.1 Disk radius) [from (cite: Tripathi2017)]
- Flaring angle 0.02 as in DSHARP  
  > "The flaring angle is taken to be $\varphi=0.02$, the same as the value used in the DSHARP analysis" (3.2 Spectral index) [from (cite: Huang2018_ring; Dullemond2018)]

### Not stated but needed to reproduce (our reading)

- Band 6 (2016.1.01164.S) calibration, self-calibration and imaging details (reused from Long2018)
- Line-free channel selection for continuum
- Image size, cell size, deconvolver details and masks for tclean
- Exact uv-fit initial values and uv-binning/weighting handling
- Dust model inputs for dust evolution code (code not named)
- Whether spectral index is computed at matched beams or deprojected bins

## Analysis recipe

1. **Image Band 3 continuum and match resolution to Band 6**: tclean mtmfs nterms=2, self-cal for GO/DL Tau, imsmooth to common beams  
  > "The Band 3 continuum images were obtained with the multi-term, multi-frequency synthesis algorithm (`mtmfs`) in `tclean` with *nterms* = 2." (2 ALMA Band 3 Observations)
   - software: CASA
   - parameter: robust -0.5 (DS Tau), 0.0 (GO, DL Tau)  
  > "For GO Tau and DL Tau, the initial images from robust = 0.0" (2 ALMA Band 3 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit uv visibilities with parametric radial profiles**: Galario synthetic visibilities, MCMC with emcee  
  > "we generate synthetic visibilities using the *Galario* code (cite: Tazzari2018), sampled at the observed uv-space." (3.1 Disk Morphology)
   - software: Galario, emcee
   - parameter: 100 walkers, 5000 steps, last 1000 used; grid 0.0001-4" step 0.0005"  
  > "The free parameters are sampled with 100 walkers and 5000 steps for each walker." (3.1 Disk Morphology)
   - assumption: axisymmetric profiles; Gaussian inner disk for DS Tau, tapered power law for GO/DL Tau, Gaussian rings  
  > "The same functional forms, including same numbers of Gaussian rings, are used for the fitting of individual disks at both wavelengths." (3.1 Disk Morphology)
   - fitting: Uniform priors on logF in [6,11] Jy/sr, sigma in [0,0.2"], gamma1 [0,2], gamma2 [0,20], rc [0,0.4"], ring centers +-0.05"; peaks of marginal posteriors, 68% intervals  
  > "The adopted parameters are taken as the peaks of marginal posteriors, with uncertainties given by the 68% confidence intervals" (3.1 Disk Morphology)
   - validation: Residual images (3-5 sigma) and binned visibility comparison  
  > "Our models match the overall structures in the visibility profiles reasonably well." (3.1 Disk Morphology)
3. **Measure disk and inner-disk radii**: radius enclosing 95% (disk) or 68% (inner disk, cut at first local minimum) of model flux  
  > "we measure the effective disk size as 95% of emission encircled in the adopted model intensity profile" (3.1.1 Disk radius)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compute spectral index, optical depth, beta**: alpha from intensity profiles at two bands; tau from full Planck function with irradiated disk temperature  
  > "We estimate optical depth of the dust emission using the expression of" (3.2 Spectral index)
   - parameter: flaring angle 0.02, Td ~15 K at 50 au  
  > "corresponding to T$_{d}\sim$ 15 K and h/r = 0.06–0.08 at 50 au for our sample" (3.2 Spectral index)
   - assumption: Td equals midplane irradiated temperature; absorption-dominated opacity  
  > "The analysis above is based on an assumption that millimeter emission is dominated by absorption." (3.2 Spectral index)
   - fitting: _not stated_
   - validation: Compared model-based and image-based alpha profiles  
  > "Spectral index profiles estimated from the azimuthally averaged brightness profiles (see Figure [5](#fig:alpha)) preserve the overall morphology" (3.2 Spectral index)
5. **Dust evolution modelling with pressure bump**: Dust growth/fragmentation/drift model with planet-carved gap (Crida2006, Fung2014 corrections)  
  > "We use the prescription from (cite: Crida2006) for an analytical shape of the gap carved by a planet" (4.1.1 Model setup)
   - parameter: planet at 33 au, q=0.002, Rc=80 au, gamma=1, alpha=1e-3, vfrag=10 m/s, 180 size cells 1 um-2 m, 300 radial cells 1-300 au  
  > "The grid for particle size has 180 cells logarithmic spaced from 1 $\mu$m to 2 m" (4.1.1 Model setup)
   - assumption: Gas-to-dust 100, 20% dust lost to drift, disk mass 5.8 MJup  
  > "we assume a disk mass of 5.8 $M_{\rm{Jup}}$" (4.1.1 Model setup)
   - fitting: _not stated_
   - validation: Compared model intensity profiles convolved to 0.1" with observations  
  > "which are convolved with a Gaussian profile whose width is 0.1$''$ as our observations." (4.1.2 Dust disk radius)

## Software

- **CASA** 5.4.0: calibration, tclean imaging, imsmooth  
  > "The data were calibrated by ALMA pipeline with the Common Astronomy Software Package (CASA), version 5.4.0." (2 ALMA Band 3 Observations)
- **Galario** : synthetic visibilities  
  > "we generate synthetic visibilities using the *Galario* code (cite: Tazzari2018)" (3.1 Disk Morphology)
- **emcee** v3.0.1: MCMC fitting  
  > "Our fitting is then performed using *emcee v3.0.1*" (3.1 Disk Morphology)
- **SciPy** : curve_fit Gaussian ring fits in image plane  
  > "The fit is performed with $curve\_fit$ in SCIPY package." (Simple Gaussian fit to dust rings)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| DS Tau R95% at 1.3 mm | 70.30 | +0.58/-0.89 | au | 3 | 70.30$_{-0.89}^{+0.58}$ |
| DS Tau R95% at 2.9 mm | 67.29 | +1.07/-1.25 | au | 3 | 67.29$_{-1.25}^{+1.07}$ |
| DS Tau ring width sigma at 1.3 mm | 8.14 | +0.36/-0.52 | au | 2 | 8.14$_{-0.52}^{+0.36}$ |
| DS Tau ring width sigma at 2.9 mm | 7.26 | +0.73/-0.79 | au | 2 | 7.26$_{-0.79}^{+0.73}$ |
| DS Tau 2.9 mm ring width, power-law inner disk model | 5.4 | 0.8 | au | 2 | $\sigma_{uv,\rm 2.9mm}= 5.4\pm0.8$ au |
| Disk-integrated alpha_mm (DS Tau, GO Tau, DL Tau) | 2.66, 2.58, 2.40 | not stated | dimensionless | 4 | 2.66, 2.58, and 2.40 for DS Tau, GO Tau, and DL Tau, respectively |
| Ring optical depth | 0.1-0.2 at 2.9 mm; 0.2-0.4 at 1.3 mm | not stated | dimensionless | 4 | the typical optical depth is about 0.1–0.2 for dust rings at 2.9 mm and 0.2–0.4 for dust rings at 1.3 mm |
| Inner disk radius 2.9 mm vs 1.3 mm (DS Tau) | 11.7 vs 15.5 | ~0.6 typical | au | 3 | The values for $R_{\rm inner,2.9mm}$ and $R_{\rm inner,1.3mm}$ are 11.7 and 15.5 au for DS Tau |
| Model ring width from dust evolution (unconvolved) | 1.09 at 2.9 mm; 1.29 at 1.3 mm | not stated | au | 5 | We therefore determine the ring width to be only 1.09 au at 2.9 mm and 1.29 au at 1.3 mm. |

## Qualitative findings

- Same rings detected at both wavelengths at the same locations; disk outer radii consistent between wavelengths  
  > "the same rings are detected at both wavelengths, with radial locations spanning from 50 to 120 au" (abstract)
- Spectral index increases outward with local minima at high-contrast ring peaks  
  > "The spectral index ($\alpha_{\rm mm}$) increases outward and exhibits local minima that correspond to the peaks of dust rings" (abstract)

## Claim tuples

- H: Dust traps keep disk radii the same at different wavelengths | E: uv-plane fits at 1.3 and 2.9 mm and dust evolution model with/without pressure bump | R: R95% consistent within uncertainties; model with bump gives equal radii, smooth disk gives smaller radii at long wavelength | F: Observations consistent with dust trapping setting disk size | **supported**
- H: Rings are narrower at longer wavelength | E: Visibility fitting of ring widths | R: DS Tau ring tentatively narrower at 2.9 mm; others unresolved | F: Only tentative evidence; depends on function choice | **partially**
- H: Rings are optically thin and host mm-sized grains | E: Spectral index, tau and beta profiles | R: tau 0.1-0.4, beta 0.5-1.5 | F: Grains in rings may have grown to mm sizes | **partially**

## Reasoning

- Why this data: Select disks with optically thin rings from the 1.3 mm survey; longer wavelength has lower optical depth  
  > "we select three disks (DS Tau, GO Tau, and DL Tau) with optically thin rings identified from our previous 1.3 mm survey" (1 Introduction)
- Why this method: _not stated_
- Alternative: Tapered power-law or Nuker inner disk for DS Tau tested; extra Gaussian ring in inner disk failed to converge  
  > "Attempts at fitting with an additional Gaussian ring component in the inner disk failed to converge (after 10000 steps)." (3.1 Disk Morphology)
- How they decided it was enough: _not stated_
- Limitation (authors): Uncertainties of GO Tau and DL Tau ring properties likely underestimated; function choice affects results; resolution washes out alpha variations  
  > "uncertainties in the dust ring properties could be largely underestimated in GO Tau and DL Tau." (3.1.2 Dust rings)
- Caveat (inferred, ours): Optical depth and beta depend on assumed low temperature (phi=0.02) and ignore scattering
- Caveat (inferred, ours): Ring widths below beam size depend on parametric form
- Caveat (inferred, ours): Dust evolution model tuned to only DS Tau with single alpha

## Reproducibility

- Data public (paper): Project codes given; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: 2016.1.01164.S and 2018.1.00614.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Dust evolution code not named or released
- Missing: Imaging parameters (image size, cell, masks)
- Missing: Band 6 processing details
- Data volume (inferred): Tens of GB (two projects, long-baseline, 3 targets)
- Score (inferred): 3/5, uv-fit recipe, priors and MCMC settings are well specified, but imaging details and the dust evolution code are missing and Band 6 processing is inherited.
- Rediscovery candidate: yes, ALMA data are archival projects, the uv-fit recipe is mostly complete, and the main results are numeric tables (R95, ring widths).

## Links

- Method: (cite: Tazzari2018) (Galario visibility modelling)
- Method: (cite: Tripathi2017) (disk size metric)
- Companion: (cite: Long2018) (previous 1.3 mm Taurus ring analysis and profile models)
- Companion: (cite: Veronesi2020) (hydrodynamical modelling of the DS Tau ring)
- Related: DSHARP
- Related: Taurus 1.3 mm survey (Long2019)

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 88,
  "stated": 62,
  "rate": 0.705
 },
 "evidence_ok": true
}
```
