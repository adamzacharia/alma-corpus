# Annular substructures in the transition disks around LkCa 15 and J1610

`2020A&A...639A.121F` | Astronomy and Astrophysics 2020 | first author: Facchini, S. | arXiv: 2005.02712 | DOI: 10.1051/0004-6361/202038027

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Do the transition disks LkCa 15 and J1610 show multiple annular substructures at ~40-60 mas resolution in 1.3 mm continuum, and can planet-disk interaction explain them?  
  > "the continuum emission resolves into multiple rings at a resolution of $\sim$60$\times$40 mas" (abstract)
- Target **LkCa 15**: coordinates _not stated_; z/distance 158.9±1.2 pc  
  > "Located at a distance of $158.9\pm1.2\,$pc (cite: gaia), LkCa 15 is a $1.25\pm0.10\,M_\odot$ star" (1 Introduction); distance from Gaia  
  > "Located at a distance of $158.9\pm1.2\,$pc (cite: gaia), LkCa 15 is a $1.25\pm0.10\,M_\odot$ star" (1 Introduction)
- Target **J1610 (2MASS J16100501-2132318)**: coordinates _not stated_; z/distance 144.7±2.7 pc  
  > "It is located at a distance of $144.7\pm2.7\,$pc (cite: gaia)" (1 Introduction); distance from Gaia  
  > "It is located at a distance of $144.7\pm2.7\,$pc (cite: gaia)" (1 Introduction)

## Data provenance

- ALMA projects: 2018.1.01255.S
- bands: Band 6 (220 GHz)  
  > "we present new ALMA Band 6 220 GHz continuum observations of LkCa 15" (1 Introduction)
- frequencies and spectral setup: 3 continuum TDM windows at 214, 216.2, 229 GHz (plus one 12CO window not used)  
  > "which have central rest frequency of 214, 216.2 and 229 GHz" (2 ALMA observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-5, C43-8, C43-9 for LkCa 15; C43-6, C43-8 for J1610  
  > "using nominal C43-5, C43-8 and C43-9 configurations for LkCa 15, and C43-6 and C43-8 for J1610" (2 ALMA observations and data reduction)
- baselines: _not stated_
- angular resolution: 68x47 mas (LkCa 15), 55x43 mas (J1610)  
  > "For J1610, the synthesized beam is $55\times43\,$mas with a P.A. of $50.3^\circ$" (2 ALMA observations and data reduction)
- max recoverable scale: 3.7'' (LkCa 15), 1.8'' (J1610)  
  > "The maximum recoverable scale for LkCa 15 and J1610 is $3.7\ensuremath{''}$ and $1.8\ensuremath{''}$, respectively." (2 ALMA observations and data reduction)
- sensitivity: rms ~6.9 uJy/beam (LkCa 15), ~7.2 uJy/beam (J1610)  
  > "The rms noise level is $\sim6.9\,\mu$Jy beam$^{-1}$" (2 ALMA observations and data reduction)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- External data: VLA 7 mm point-source flux of LkCa 15, 16.6±3.6 uJy  
  > "with a flux density of $16.6\pm3.6\,\mu$Jy" (3.1 Images) [from (cite: isella2014)]
- External data: Gas surface density profile parameters from 12CO(3-2) of LkCa 15  
  > "We adopt a parameterized initial gas surface density profile based on the analysis of low-resolution $^{12}$CO ($J$=3-2) observations of LkCa 15 by (cite: jin2019)" (4.1 Set-up) [from (cite: jin2019)]
- External data: N2H+ abundant between 58 and 88 au in LkCa 15  
  > "showing that this ion is particularly abundant between $58^{+6}_{-10}$ and $88^{+6}_{-4}\,$au" (5 Discussion) [from (cite: qi2019)]
- Simulation/model as data: 2D Dusty FARGO-ADSG simulations with 60 Earth-mass planet at 70 au, isothermal, beta=1, beta=100, post-processed with RADMC-3D  
  > "We insert a 60 Earth-mass planet at 70 au, at the radial location of the middle continuum ring in the LkCa 15 disk" (4.2 Hydrodynamical simulations)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.6  
  > "The data were calibrated using the `CASA` package, version 5.6" (2 ALMA observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800 (LkCa 15); J1517-2422 / J1427-4206 (J1610)  
  > "J1610 & 03.09.2019 & 46 & 38 m & 3143 m & 19 min & J1517-2422 & J1551-1755 & J1517-2422" (Table 1)
- flux scale uncertainty: 10%  
  > "within the 10% calibration uncertainties" (2 ALMA observations and data reduction)
- self calibration: Performed on all data sets  
  > "Self-calibration was performed on all data-sets, leading to a good improvement in the signal-to-noise (S/N) ratio." (2 ALMA observations and data reduction)

### Imaging

- task: tclean  
  > "Images in the sky plane were produced using the `tclean` task, with the `multiscale` cleaning algorithm allowing for point source emission." (2 ALMA observations and data reduction)
- deconvolver: multiscale  
  > "with the `multiscale` cleaning algorithm allowing for point source emission" (2 ALMA observations and data reduction)
- weighting robust: Briggs robust 0 (LkCa 15), 0.3 (J1610)  
  > "The best compromise between angular resolution and S/N for LkCa 15 is with a Briggs robust weighting of 0, whereas for J1610 we opted for a Briggs robust weighting of 0.3." (2 ALMA observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Elliptical masks, semi-major axis 1.7'' (LkCa 15) and 1'' (J1610), PA/inclination from uv fits  
  > "a semi-major axis of $1.7\ensuremath{''}$ and $1\ensuremath{''}$ for LkCa 15 and J1610, respectively" (2 ALMA observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Visibilities spectrally re-binned to 250 MHz channels  
  > "spectrally re-binned on $250\,$MHz channels to avoid bandwidth smearing" (2 ALMA observations and data reduction)
- final beam: 68x47 mas PA 347.4 deg (LkCa 15); 55x43 mas PA 50.3 deg (J1610)  
  > "The resulting synthesized beam for LkCa 15 is $68\times47\,$mas, with a position angle (P.A.) of $347.4^\circ$." (2 ALMA observations and data reduction)
- final rms: 6.9 uJy/beam (LkCa 15); 7.2 uJy/beam (J1610)  
  > "the rms noise level is $\sim7.2\,\mu$Jy beam$^{-1}$" (2 ALMA observations and data reduction)

### Inherited from earlier work

- JvM residual rescaling of the clean image  
  > "The residuals in the final images were rescaled by the ratio of the clean beam and dirty beam (cite: JvM1995)" (2 ALMA observations and data reduction) [from (cite: JvM1995)]
- Iterative MCRT temperature method  
  > "following the method described in Appendix A of (cite: bae2019)" (4.1 Set-up) [from (cite: bae2019)]
- Flaring angle 0.02 and DSHARP temperature prescription  
  > "which we set equal to $0.02$ as in (cite: huang2018b)" (5 Discussion) [from (cite: huang2018b)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals, number of rounds and reference antennas
- Cell size and image size
- Multiscale scales list
- Pipeline vs manual calibration and flux model details
- Initial uv-fit parameter bounds apart from the sigma constraint
- Which calibrator flux values were used
- uv-plot binning for visibilities

## Analysis recipe

1. **Calibrate, self-calibrate, concatenate and image**: CASA calibration, self-cal, concat, tclean multiscale with JvM correction  
  > "The visibilities were merged using the `concat` task in `CASA`" (2 ALMA observations and data reduction)
   - software: CASA
   - parameter: Briggs robust 0 (LkCa 15), 0.3 (J1610); clean threshold 1 sigma  
  > "The de-convolution was performed down to a cleaning threshold of $1\sigma$, which maximises the flux in the clean model." (2 ALMA observations and data reduction)
   - fitting: _not stated_
   - validation: Fluxes compared with PdBI, CARMA, SMA within 10%  
  > "the integrated flux densities are in agreement with previous observations at the same wavelength with different interferometers" (2 ALMA observations and data reduction)
2. **Fit axisymmetric Gaussian-ring model to visibilities**: Sum of radial Gaussian rings, Fourier transformed and sampled at uv points  
  > "fitting the visibility points using an axisymmetric parametric model that consists in a set of radially Gaussian rings" (3.2 Modelling of the continuum emission)
   - software: GALARIO, emcee
   - parameter: 16 free parameters (LkCa 15), 13 (J1610)  
  > "is described with 16 and 13 free parameters, respectively" (3.2 Modelling of the continuum emission)
   - fitting: emcee, 160 walkers, 10000 steps after 2000 burn-in; flat priors with one ring sigma>0.15''  
  > "We sample the posterior distribution of our parameters with the `emcee` package (cite: emcee) with 160 walkers over 10000 steps after 2000 steps of burn-in." (3.2 Modelling of the continuum emission)
   - validation: Residual images and visibility comparison  
  > "Figure [4](#fig:map_mod_res_lkca15) provides the images of the data, model and residuals for the best-fit model" (3.2 Modelling of the continuum emission)
3. **Azimuthally averaged radial profiles**: Re-center, deproject, average in 9 mas bins using fitted geometry  
  > "Radial bins of $9\,$mas are used" (3.1 Images)
   - fitting: _not stated_
   - validation: _not stated_
4. **Optical depth, dust mass and Sigma_g/Sigma_d**: Invert I=B(1-exp(-tau)); Sigma_d=tau/kappa; Toomre Q>2 gives gas upper limit  
  > "we compute optical depth profiles under the assumptions of a uniform opacity across the disks, and that the albedo of the dust grains is negligible" (5 Discussion)
   - parameter: kappa = 2.6 cm2/g at 1.3 mm  
  > "we have an absorption opacity of 2.6 cm$^{2}$ g$^{-1}$ at 1.3 mm" (5 Discussion)
   - assumption: Negligible albedo; temperature from MCRT model or phi=0.02 irradiation formula  
  > "where $\sigma_{\rm SB}$ in the Stefan-Boltzmann constant, and $\varphi$ is the flaring angle" (5 Discussion)
   - fitting: _not stated_
   - validation: _not stated_
5. **Hydrodynamical simulations and synthetic images**: Dusty FARGO-ADSG with 60 Earth-mass planet, three cooling prescriptions; RADMC-3D imaging convolved with observed beam  
  > "We carry out two-dimensional hydrodynamical simulations using the Dusty FARGO-ADSG code (cite: baruteau2019)." (4.2 Hydrodynamical simulations)
   - software: Dusty FARGO-ADSG, RADMC-3D
   - parameter: alpha=1e-4; 672x1556 cells; 1000 orbits then 300 with 3e5 particles  
  > "The disk viscosity $\nu$ is characterized by a uniform viscosity parameter $\alpha=10^{-4}$" (4.2 Hydrodynamical simulations)
   - assumption: Gas disk mass 0.1 Msun within 600 au; Rc=65 au  
  > "so that the total gas disk mass inside of 600 au is $0.1~M_\odot$" (4.1 Set-up)
   - fitting: _not stated_
   - validation: Qualitative comparison with observed rings  
  > "our goal is not to reproduce a perfect match with the observations" (4 Comparison with hydrodynamical simulations)

## Software

- **CASA** 5.6: Calibration, concat, tclean imaging  
  > "The data were calibrated using the `CASA` package, version 5.6" (2 ALMA observations and data reduction)
- **GALARIO** : Fourier transform and sampling of model at uv points  
  > "sampled in the $(u,v)$ points of the dataset using `GALARIO`" (3.2 Modelling of the continuum emission)
- **emcee** : Posterior sampling  
  > "We sample the posterior distribution of our parameters with the `emcee` package" (3.2 Modelling of the continuum emission)
- **RADMC-3D** : MCRT temperature and synthetic continuum images  
  > "The raw continuum emission is obtained with RADMC-3D" (4.3 Model results)
- **Dusty FARGO-ADSG** : 2D hydrodynamical simulations with dust particles  
  > "We carry out two-dimensional hydrodynamical simulations using the Dusty FARGO-ADSG code" (4.2 Hydrodynamical simulations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| LkCa 15 ring radii B47/B69/B100 | 47.33 / 68.99 / 100.11 | +1.53/-1.20, +0.17/-0.15, ±0.19 | au | 2 | $R_i$ & (au) & $47.33^{+1.53}_{-1.20}$ & $68.99^{+0.17}_{-0.15}$ & $100.11^{+0.19}_{-0.19}$ |
| LkCa 15 inclination | 50.16 | ±0.03 | deg | 2 | $i$ & $(^{\circ})$ & $50.16\pm0.03$ |
| J1610 ring radii B29/B41 | 28.79 / 41.11 | ±0.10 / +0.13,-0.15 | au | 2 | $R_i$ & (au) & $28.79^{+0.10}_{-0.10}$ & $41.11^{+0.13}_{-0.15}$ |
| J1610 inclination | 37.80 | ±0.20 | deg | 2 | $i$ & $(^{\circ})$ & $37.80\pm0.20$ |
| Recovered flux density LkCa 15 | 136.4 | ±0.1 | mJy | 1 | $136.4\pm0.1\,$mJy and $30.8\pm0.1\,$mJy for LkCa 15 and J1610 |
| Recovered flux density J1610 | 30.8 | ±0.1 | mJy | 1 | $136.4\pm0.1\,$mJy and $30.8\pm0.1\,$mJy for LkCa 15 and J1610 |
| LkCa 15 central unresolved emission peak | 73.7 | ±6.9 | uJy/beam | 1 | with a peak intensity of $73.7\pm6.9\,\mu$Jy beam$^{-1}$ |
| Spectral index 1.35-7 mm of LkCa 15 center | 0.9 | ±0.2 | dimensionless | 0 | we obtain a spectral index of $0.9\pm0.2$ between 1.35 and 7 mm |
| Dust mass B100 (LkCa 15), MCRT temperature | 182 | not stated | Earth masses | 4 | we obtain dust masses of 51 and $182\,M_\oplus$ for B47+B69 and B100, respectively |
| Sigma_g/Sigma_d upper limits B69, B100 | <68, <62 | not stated | dimensionless | 4 | $\Sigma_{\rm g}/\Sigma_{\rm d}<[68,62]$ at their intensity peaks |
| Beta at 70 au in LkCa 15 | 0.07-4.3 | not stated | dimensionless | 0 | the cooling parameter $\beta$ at 70 au in the LkCa 15 disk is $\sim0.07 - 4.3$ |
| J1610 stellar luminosity | 0.46 | ±0.03 | Lsun | 0 | Our final value is $L_*=0.46\pm0.03L_\odot$ |

## Qualitative findings

- Both disks have multiple narrow rings plus a broad component; rings marginally optically thick  
  > "The rings look marginally optically thick, with peak optical depths of $\sim0.5$ (neglecting scattering)" (abstract)
- Point-like emission at 35 au in LkCa 15 is likely an imaging artefact  
  > "This suggests that the feature is likely an imaging artefact" (3.1 Images)

## Claim tuples

- H: Do the broad rings of transition disks resolve into multiple rings at high resolution? | E: Band 6 imaging and uv-plane Gaussian ring fits | R: 3 narrow rings in LkCa 15 and 2 in J1610 plus a broad component | F: Both disks host multi-ringed substructure | **supported**
- H: Can a low-mass embedded planet explain the rings? | E: Hydro simulations with a 60 Earth-mass planet and three cooling prescriptions | R: Number of rings and gaps varies with cooling time | F: Qualitatively explained but outcome strongly depends on cooling | **partially**
- H: Are the rings favourable to planetesimal formation? | E: Optical-depth dust surface density vs Toomre-limited gas density | R: Sigma_g/Sigma_d upper limits ~62-68 in LkCa 15 rings | F: Rings plausible sites of streaming instability | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Gaussian ring uv fit inspired by image analysis  
  > "Inspired by the image analysis (Sec. [3.1](#sec:images)), the model consists in a broad ring and 3 or 2 narrow rings" (3.2 Modelling of the continuum emission)
- Alternative: Snowline-induced rings and dead-zone edges cannot be excluded  
  > "The present observations cannot distinguish between these different models." (5 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): J1610 rings likely unresolved, so only limits on alpha/St  
  > "Given that the rings in J1610 are likely unresolved even in the $(u,v)$-plane analysis" (5 Discussion)
- Caveat (inferred, ours): Optical depths neglect scattering, so dust masses are lower limits
- Caveat (inferred, ours): Simulations are not fitted and a single planet mass/position is tried
- Caveat (inferred, ours): Rc chosen differently from CO fit to match ring position
- Caveat (inferred, ours): Residual rms in cavity may be underestimated

## Reproducibility

- Data public (paper): ALMA data acknowledged under project 2018.1.01255.S; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.01255.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Self-calibration parameters
- Missing: Image size and cell size
- Missing: Multiscale scales
- Missing: Hydro code initial setup scripts
- Data volume (inferred): ~100-300 GB raw for six execution blocks
- Score (inferred): 3/5, Imaging and fitting approach described with key numbers, but self-cal and several clean parameters are missing; hydro part requires specialised codes.
- Rediscovery candidate: yes, Data likely public after the proprietary period, with numeric ring parameters from a uv fit; moderate recipe completeness.

## Links

- Method: (cite: galario) (uv-plane modelling tool)
- Method: (cite: dullemond2018) (ring confinement framework alpha/St)
- Method: (cite: JvM1995) (residual rescaling)
- Companion: (cite: huang2020) (high-resolution GM Aur comparison)
- Companion: (cite: jin2019) (CO gas model of LkCa 15)
- Related: DSHARP

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 55,
  "rate": 0.663
 },
 "evidence_ok": true
}
```
