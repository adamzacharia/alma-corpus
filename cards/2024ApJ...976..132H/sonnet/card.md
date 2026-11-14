# High-resolution ALMA Observations of Richly Structured Protoplanetary Disks in σ Orionis

`2024ApJ...976..132H` | The Astrophysical Journal 2024 | first author: Huang, Jane | arXiv: 2410.03823 | DOI: 10.3847/1538-4357/ad84df

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Do millimeter continuum substructures (gaps, rings) form and survive in disks exposed to intermediate external UV radiation in sigma Orionis, and how do disk sizes compare to nearby regions?  
  > "The diminished masses and sizes of disks close to massive stars in Orion raise the question of whether they still commonly harbor the kinds of millimeter continuum disk substructures" (Introduction)
- Target **SO 662, SO 844, SO 897, SO 984, SO 1036, SO 1152, SO 1153, SO 1274 (sigma Orionis disks)**: coordinates 2MASS designations given in Table 1 (e.g. SO 662: J05384027-0230185)  
  > "the median Gaia distance to members of $\sigma$ Orionis is 402 pc" (Sample overview); "SO 662 | J05384027-0230185 | K7 | 0.64 | 0.68 | $394.9\pm3.1$ | 0.68 | 3.41" (Table 1); z/distance ~375-408 pc individual Gaia distances; cluster median 402 pc  
  > "the median Gaia distance to members of $\sigma$ Orionis is 402 pc" (Sample overview); "SO 662 | J05384027-0230185 | K7 | 0.64 | 0.68 | $394.9\pm3.1$ | 0.68 | 3.41" (Table 1); distance from Gaia; median cluster distance from Zerjal et al. 2024  
  > "the median Gaia distance to members of $\sigma$ Orionis is 402 pc" (Sample overview); "SO 662 | J05384027-0230185 | K7 | 0.64 | 0.68 | $394.9\pm3.1$ | 0.68 | 3.41" (Table 1)

## Data provenance

- ALMA projects: 2022.1.00728.S, 2016.1.00447.S
- bands: 1.3 mm continuum  
  > "Long-baseline 1.3 mm continuum observations of the eight disks were obtained by ALMA program 2022.1.00728.S (PI: J. Huang)." (3 Observations and Data Reduction)
- frequencies and spectral setup: four SPWs at 224, 226, 240, 242 GHz, 2 GHz bandwidth each, 128 channels  
  > "the correlator was configured with four spectral windows (SPWs) centered at 224, 226, 240, and 242 GHz, respectively. Each SPW had a bandwidth of 2 GHz divided into 128 channels." (3 Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: long baseline 230 m - 16.2 km; archival ~15 m to 2.6 km  
  > "230 m - 16.2 km" (Table 2); "each target was observed with baselines ranging from $\sim15$ m to 2.6 km over the course of eight EBs" (3 Observations and Data Reduction)
- angular resolution: ~0.02" (~8 au); beams 22-24 x 19-21 mas  
  > "we used ALMA to observe a sample of eight disks at a resolution of $0.02\ensuremath{''}$ ($\sim8$ au)" (Introduction)
- max recoverable scale: _not stated_
- sensitivity: image rms 9-12 uJy/beam  
  > "SO 1036 | $24\times 19$ ($-60.8$) | 12 | 0.46" (Table 3)
- time on source: 29 min 40 s per long-baseline EB; 2 EBs per target (3 for SO 1274); archival ~9 min  
  > "The time on target for each execution block (EB) was 29 minutes 40 seconds. Three EBs were used to observe SO 1274, while other targets were observed for two EBs each." (3 Observations and Data Reduction)
- observing dates: 2023 July 19 - August 7  
  > "SO 1274 |  2023 July 19  | 230 m - 15.2 km  |         46" (Table 2)
- pi or archival as stated: New program (PI J. Huang) plus archival program (PI J. Williams)  
  > "program 2016.1.00447.S (PI: J. Williams) through the ALMA archive" (3 Observations and Data Reduction)
- External data: Host star spectral type, mass, luminosity and external FUV field values  
  > "Spectral type, stellar mass, stellar luminosity, and external FUV radiation field values come from (cite: 2023AA...679A..82M)." (Table 1 notes) [from (cite: 2023AA...679A..82M)]
- External data: Cluster median Gaia distance 402 pc  
  > "the median *Gaia* distance to members of $\sigma$ Orionis is 402 pc" (Sample overview) [from (cite: 2024AA...686A.161Z)]
- External data: Planet-mass fitting relations and hydrodynamical grid  
  > "We use the fitting relations introduced in (cite: 2018ApJ...869L..47Z), which are implemented in code presented in (cite: 2022MNRAS.510.4473Z)." (Planet mass estimates) [from (cite: 2018ApJ...869L..47Z); (cite: 2022MNRAS.510.4473Z)]

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline by ALMA staff (long baseline); CASA 4.7.2 pipeline for archival data  
  > "Calibrated measurement sets were produced by ALMA staff with the standard ALMA pipeline in `CASA 6.4.1`" (3 Observations and Data Reduction); "The raw data were calibrated with the `CASA` 4.7.2 pipeline." (3 Observations and Data Reduction)
- casa version: CASA 6.4.1 (pipeline), CASA 6.5 (subsequent processing)  
  > "Subsequent processing of the new and archival data was performed with `CASA` 6.5." (3 Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: quasars J0423-0120, J0532-0307, J0529-0519 as calibrators  
  > "The quasars J0423-0120, J0532-0307, and J0529-0519 were used as calibrators for all observations." (3 Observations and Data Reduction)
- flux scale uncertainty: ~10% systematic  
  > "Error bars do not include $\sim10\%$ systematic flux calibration uncertainty" (Table 5)
- self calibration: Phase (and amplitude for some) self-cal on short-baseline data; long-baseline phase self-cal only SO 1153; none for SO 897  
  > "Phase self-calibration was performed on the individual EBs for SO 1153, the brightest disk in the sample. Self-calibration was tested on the other sources, but did not improve the images." (3 Observations and Data Reduction)

### Imaging

- task: tclean; Högbom CLEAN for short-baseline per-EB images  
  > "Images of each EB were produced with the Högbom CLEAN algorithm (cite: 1974AAS...15..417H) as implemented in the `tclean` task." (3 Observations and Data Reduction)
- deconvolver: multi-scale CLEAN for long-baseline and combined data  
  > "The short-baseline and long-baseline observations were then combined and imaged together with multi-scale CLEAN and a robust value of 0.5." (3 Observations and Data Reduction)
- weighting robust: robust = 0.5  
  > "combined and imaged together with multi-scale CLEAN and a robust value of 0.5" (3 Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: channels with possible CO emission flagged in archival data and averaged to pseudo-continuum (channels not listed)  
  > "we flagged channels where CO line emission might be present in the archival short-baseline data and averaged the channels to create pseudo-continuum visibilities" (3 Observations and Data Reduction)
- primary beam correction: applied to all disk images  
  > "Finally, all of the disk images were primary-beam-corrected." (3 Observations and Data Reduction)
- array combination: short- and long-baseline visibilities combined and imaged together  
  > "The short-baseline and long-baseline observations were then combined and imaged together" (3 Observations and Data Reduction)
- smoothing: _not stated_
- final beam: 22-24 x 19-21 mas  
  > "SO 662 | $22\times 20$ ($72.8$) | 10 | 0.42" (Table 3)
- final rms: 9-12 uJy/beam  
  > "SO 1152 | $23\times 21$ ($-82.1$) | 9 | 0.27" (Table 3)

### Inherited from earlier work

- Disk centers determined by 2D Gaussian fit with imfit  
  > "As in (cite: 2018ApJ...869L..41A), the disk centers were determined by fitting each image with a two-dimensional Gaussian using the `imfit` task." (3 Observations and Data Reduction) [from (cite: 2018ApJ...869L..41A)]
- Weight rescaling procedure  
  > "we used the procedure described in (cite: 2023PASP..135f4503Z) and implemented in the `visread` package" (2 Analysis) [from (cite: 2023PASP..135f4503Z)]
- Dust temperature prescription  
  > "Following (cite: 2018ApJ...869L..46D), we approximate $T_d$ with" (Optical Depths) [from (cite: 2018ApJ...869L..46D)]
- Substructure nomenclature  
  > "We follow the nomenclature of (cite: 2018ApJ...869L..42H)" (Locations, widths, and depths) [from (cite: 2018ApJ...869L..42H)]
- Effective radius definitions R68, R90  
  > "We then measured the effective radii using the metrics from (cite: 2017ApJ...845...44T)." (Disk fluxes and sizes) [from (cite: 2017ApJ...845...44T)]

### Not stated but needed to reproduce (our reading)

- Exact line-free/flagged channel ranges in archival data
- Self-calibration solution intervals and which EBs/ cleaning parameters (niter, thresholds, masks, scales, cell, image size) were used
- Prior means and standard deviations for the parametric model
- Initial guesses for N rings and hyperparameters of the pyro guide beyond learning rate
- Zenodo products must be downloaded to reproduce; CLEAN model used for weight rescaling not given
- Distance values adopted for each target in the modeling (Table 1 values assumed)

## Analysis recipe

1. **Combine and image visibilities**: Flag CO channels in archival short-baseline data, self-calibrate, align EBs, combine with long-baseline data, image with multi-scale CLEAN and primary-beam correct  
  > "The short-baseline and long-baseline observations were then combined and imaged together with multi-scale CLEAN and a robust value of 0.5." (3 Observations and Data Reduction)
   - software: CASA, tclean, imfit, phaseshift, fixplanets
   - parameter: robust = 0.5  
  > "a robust value of 0.5" (3 Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit parametric radial intensity profiles in uv plane**: Sum of central Gaussian plus N Gaussian rings, thin disk (flared surface for SO 897), model visibilities compared with weight-rescaled data  
  > "We thus fit the observations with parametric intensity models in order to infer the radial intensity profiles of our targets." (Analysis, Parametric intensity profile modeling)
   - software: mpol, eddy, visread, pyro, pytorch
   - parameter: Adam optimizer, learning rate 0.02, 15,000 iterations; 2000 posterior samples  
  > "Using the Adam optimizer (cite: kingma2017) with a learning rate of 0.02, we found that 15,000 iterations were sufficient for the ELBO values to converge" (Parametric intensity profile modeling)
   - assumption: Geometrically thin disk (flared surface for SO 897); posterior approximated as multivariate normal  
  > "We assumed that the posterior can be approximated as a multivariate normal distribution (a “guide” in the parlance of `pyro`)." (Parametric intensity profile modeling)
   - fitting: Stochastic variational inference (pyro), Gaussian priors on log A, log sigma, r_i, i, z0, phi, PA, offsets; chi-square-like likelihood with rescaled weights  
  > "Gaussian priors were specified for $\log A_0$, $\log \sigma_0$, $\log A_i$, $\log \sigma_i$, $r_i$, $i$, $z_0$, $\phi$, P.A., $\Delta x$, $\Delta y$." (Parametric intensity profile modeling)
   - validation: BIC model selection; model images compared to data (residuals ~4 sigma); frank non-parametric comparison  
  > "The models reproduce the data well, with maximum residual levels at $\sim4\sigma$." (Parametric intensity profile modeling)
3. **Identify substructures and measure location, width, depth**: Rings = local maxima, gaps = local minima, shoulders = three consecutive inflection points, in model profiles from 2000 posterior samples  
  > "A ring is defined to be a local maximum in the radial intensity profile (other than at the disk center)" (Locations, widths, and depths)
   - fitting: _not stated_
   - validation: Compared with frank non-parametric profiles  
  > "we also modelled the visibilities with the non-parametric modeling code `frank`" (Locations, widths, and depths)
4. **Estimate optical depths and dust temperature**: tau = -ln(1 - I/B(Td)) with irradiated-disk temperature Td  
  > "where $\varphi = 0.02$ is the chosen flaring angle." (Optical Depths)
   - assumption: Scattering neglected; flaring angle 0.02; stellar heating only  
  > "This expression neglects scattering, which may lead to underestimates of the optical depth." (Optical Depths)
   - fitting: _not stated_
   - validation: _not stated_
5. **Measure fluxes and effective radii**: Integrate model intensity profile with cos i / d^2; R68 and R90 enclosing 68% and 90% flux  
  > "$R_\text{68}$ is defined as the radius that encloses $68\%$ of the total flux, while $R_\text{90}$ is the radius that encloses $90\%$." (Disk fluxes and sizes)
   - fitting: _not stated_
   - validation: _not stated_
6. **Fit size-luminosity relation**: linmix regression of log R68 vs log Lmm (flux scaled to 140 pc), with flux, 10% calibration, and distance uncertainties sampled  
  > "The data are fit using a Python port of `linmix`, a Bayesian linear fitting code by (cite: 2007ApJ...665.1489K)" (Size-luminosity relationship)
   - software: linmix, Interactive Distance Estimation
   - assumption: Gaussian scatter in log R68  
  > "The scatter of $\log R_\text{68}$ about the regression line is assumed to be Gaussian with standard deviation $\sigma$." (Size-luminosity relationship)
   - fitting: linmix Bayesian linear fit  
  > "a Bayesian linear fitting code by (cite: 2007ApJ...665.1489K) that accounts for uncertainties in both the independent and dependent variables" (Size-luminosity relationship)
   - validation: _not stated_
7. **Assess dust trapping via ring width to scale height**: Compute w_d/h_p for high-contrast rings (depth <0.5) with w_d = sigma_i  
  > "We set $w_d$ equal to the value of $\sigma_i$ inferred for the corresponding ring in the parametric model" (Dust trapping analysis)
   - assumption: mu = 2.37; h_p uncertainty ~25%  
  > "Thus, we estimate an uncertainty on $h_p$ of $\sim25\%$." (Dust trapping analysis)
   - fitting: _not stated_
   - validation: _not stated_
8. **Estimate planet masses from gaps**: Zhang et al. 2018 scaling relations with gap width, Sigma_dust, St_max, h/r  
  > "In brief, we assume that each observed gap corresponds to one protoplanet." (Planet mass estimates)
   - parameter: kappa_abs = 0.43 cm^2/g, amax=0.1 mm, n(a)∝a^-3.5, alpha = 1e-3  
  > "We assume that $\alpha=10^{-3}$." (Planet mass estimates)
   - assumption: One planet per gap; DSHARP dust composition  
  > "the dust absorption opacity is set to 0.43 cm$^{2}$ g$^{-1}$" (Planet mass estimates)
   - fitting: _not stated_
   - validation: Comparison with DSHARP planet masses  
  > "The overall ranges of inferred planet masses and semi-major axes are similar" (Planet mass estimates)

## Software

- **CASA** 6.4.1 (pipeline), 6.5 (processing), 4.7.2 (archival pipeline): calibration, imaging  
  > "Subsequent processing of the new and archival data was performed with `CASA` 6.5." (3 Observations and Data Reduction)
- **mpol** v0.2.0: generating model images and visibilities  
  > "we then used the `mpol` package (cite: 2023PASP..135f4503Z; mpol) to generate a model disk image" (Parametric intensity profile modeling)
- **eddy** : transform disk to sky coordinates for SO 897 flared surface  
  > "We then used the `eddy` package (cite: 2019JOSS....4.1220T) to transform disk coordinates to sky coordinates" (Parametric intensity profile modeling)
- **visread** v0.0.1: rescaling visibility weights  
  > "implemented in the `visread` package (cite: ian_czekala_2021_4432520) to correct the scaling" (Parametric intensity profile modeling)
- **pyro** : stochastic variational inference  
  > "The posterior distributions were estimated with the `pyro` (cite: JMLR:v20:18-403) implementation of the stochastic variational inference (SVI) algorithm" (Parametric intensity profile modeling)
- **frank** : non-parametric visibility modeling check  
  > "we also modelled the visibilities with the non-parametric modeling code `frank` (cite: 2020MNRAS.495.3209J)" (Locations, widths, and depths)
- **linmix** : size-luminosity regression  
  > "The data are fit using a Python port[^3] of `linmix`" (Size-luminosity relationship)
- **Interactive Distance Estimation** : distance posterior samples from Gaia  
  > "we generated posterior samples for the distances using the Interactive Distance Estimation tool" (Size-luminosity relationship)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SO 1274 disk flux | 15.5 | ±0.2 | mJy | 5 | SO 1274 / $15.5\pm0.2$ / $113.2\substack{+0.7 \\ -0.8}$ / $126.7\substack{+0.7 \\ -0.6}$ |
| SO 1274 R90 | 126.7 | +0.7/-0.6 | au | 5 | SO 1274 / $15.5\pm0.2$ / $113.2\substack{+0.7 \\ -0.8}$ / $126.7\substack{+0.7 \\ -0.6}$ |
| SO 662 R68 | 14.2 | ±0.2 | au | 5 | SO 662 / $2.09\pm0.03$ / $14.2\pm0.2$ / $17.7\pm0.3$ |
| Size-luminosity intercept alpha | 2.6 | ±0.3 | dimensionless | 6 | $\alpha$ / $2.6\pm0.3$ |
| Size-luminosity slope beta | 0.8 | ±0.2 | dimensionless | 6 | $\beta$ / $0.8\pm0.2$ |
| Size-luminosity correlation coefficient | 0.91 | +0.06/-0.15 | dimensionless | 6 | $0.91\substack{+0.06\\-0.15}$ |
| SO 1274 gap D27 location | 26.9 | ±0.2 | au | 3 | D27 / $26.9\pm0.2$ / $9.1\pm0.2$ / $0.21\pm0.02$ |
| SO 1274 inner three gap period ratio | 3.08:1.95:1 | not stated | dimensionless | 3 | close to a 3:2:1 period ratio (more precisely, 3.08:1.95:1) |
| SO 1274 ring B119 w_d/h_p | 0.2 | not stated | dimensionless | 7 | B119   /   10.3          /  2.3  / 10.4  /    0.2 |
| SO 844 D10 planet mass | 7.9 | +0.13/-0.16 (log Mp) | M_Jup | 8 | SO 844 / D10 / 0.74 / 0.53 / 0.06 / 736 / 0.3 / 7.9 |
| Weight rescaling factor f | ~2 | not stated | dimensionless | 2 | The value of $f$ was typically $\sim2$. |

## Qualitative findings

- Gaps/rings resolved in five disks; gap or shoulders inferred in the other three; disks largely axisymmetric  
  > "Gaps and rings are resolved in the images of five disks." (abstract)
- Outer narrow rings in SO 1274 are likely dust traps  
  > "Taking into account our rough estimate for the uncertainty of $h_p$, we consider these rings likely to be dust traps." (Dust trapping analysis)

## Claim tuples

- H: Do substructures exist in disks exposed to intermediate external UV fields? | E: ALMA 1.3 mm imaging at ~8 au of eight sigma Ori disks plus visibility modeling | R: Gaps/rings/cavity in five disks; gap or shoulders inferred in others | F: Substructures robustly form and survive at tens of au in sigma Orionis and in compact disks | **supported**
- H: Are SO 1274 gaps arranged in a resonant chain? | E: Period ratios of gap and ring locations | R: Ratios near 3:2 and 3:2:1 | F: Five gaps appear nearly in resonant chain | **partially**
- H: Do sigma Ori disks follow a size-luminosity relation and are large disks with gaps rare? | E: linmix fit of R68 vs Lmm | R: beta=0.8±0.2, correlation 0.91; predicted 9 mJy for 50 au | F: Most disks are small; gaps beyond 50 au rare, due to photoevaporation or age | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: uv-plane modeling can reveal substructures not visible in CLEAN images; SVI faster than MCMC for high-dimensional models  
  > "Modeling disk emission in the $uv$ plane is often an effective technique for inferring the presence of substructures that are not readily visible in CLEAN images" (Parametric intensity profile modeling)
- Alternative: frank non-parametric models used to check parametric substructure; N=2 for SO 1152 rejected since it does not reproduce rings despite lower BIC  
  > "for SO 1152, we selected the model with $N=4$ over the model with $N=2$ because the latter does not reproduce the rings" (Model selection)
- How they decided it was enough: _not stated_
- Limitation (authors): FUV fields are upper bounds from projected separations; temperature uncertainty dominates dust-trap and planet-mass estimates; SVI is approximate  
  > "The FUV field estimates from (cite: 2023AA...679A..82M) are based on projected separations, so they should be considered upper bounds." (2 Sample overview); "SVI is an approximate method" (Parametric intensity profile modeling)
- Caveat (inferred, ours): Posterior uncertainties from a Gaussian variational guide are likely underestimated
- Caveat (inferred, ours): Sample of 8 disks is biased by flux cutoff, limiting the size-luminosity inference
- Caveat (inferred, ours): Optical depth and planet masses rely on assumed temperature and opacity
- Caveat (inferred, ours): Parametric Gaussian model may impose structures; shoulders inferred model-dependently

## Reproducibility

- Data public (paper): Archival ALMA data and reduced continuum visibilities/images on Zenodo  
  > "The continuum visibilities and images can be downloaded from <https://zenodo.org/records/13821034>." (3 Observations and Data Reduction)
- Products in archive: _not stated_
- Missing: Priors, CLEAN masks/thresholds and cell/image sizes
- Missing: Self-calibration details per disk
- Missing: Analysis code not stated as released
- Data volume (inferred): ~100-300 GB raw for both programs; Zenodo continuum products are small (<few GB)
- Score (inferred): 3/5, Public data and Zenodo products with clear model equations and tables, but priors, imaging parameters and code are not specified.
- Rediscovery candidate: yes, Data are public (and reduced visibilities are released), model form is explicit, results are numeric tables.

## Links

- Method: (cite: 2023PASP..135f4503Z) (MPoL package and weight-rescaling procedure)
- Method: (cite: 2018ApJ...869L..47Z) (planet mass from gap width relations)
- Method: (cite: 2018ApJ...869L..46D) (dust temperature and ring width analysis)
- Companion: (cite: 2023AA...679A..82M) (Analysis of the archival 2016.1.00447.S data and stellar properties)
- Companion: (cite: 2017AJ....153..240A) (Original sigma Orionis ALMA survey from which targets were selected)
- Related: DSHARP
- Related: ALMA sigma Orionis survey (Ansdell 2017)

## Checks

```json
{
 "quotes": 91,
 "quotes_ok": 91,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 95,
  "stated": 68,
  "rate": 0.716
 },
 "evidence_ok": true
}
```
