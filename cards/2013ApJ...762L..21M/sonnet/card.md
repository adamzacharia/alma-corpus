# Millimeter Emission Structure in the First ALMA Image of the AU Mic Debris Disk

`2013ApJ...762L..21M` | The Astrophysical Journal Letters 2013 | first author: MacGregor, Meredith A. | arXiv: 1211.5148 | DOI: 10.1088/2041-8205/762/2/L21

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks
- Question: What is the millimeter emission structure of the AU Mic debris disk at 0.6" resolution, including the outer belt profile and a newly seen central peak?  
  > "The ALMA data provide substantially improved constraints on the locations of colliding planetesimals in the AU Mic disk" (Introduction)
- Target **AU Mic**: coordinates pointing center RA 20h45m09.34s, Dec -31d20m24.09s (J2000)  
  > "At a distance of $9.91\pm0.10$ pc (cite: van07), the M1 star AU Mic hosts one of the closest and best studied debris disks." (Introduction); "pointing center $\alpha=20^{\rm 
h}45^{\rm m}09.34s$, $\delta=-31\ensuremath{^\circ}20\ensuremath{'}24.09\ensuremath{''}$, J2000" (Observations); z/distance 9.91±0.10 pc  
  > "At a distance of $9.91\pm0.10$ pc (cite: van07), the M1 star AU Mic hosts one of the closest and best studied debris disks." (Introduction); "pointing center $\alpha=20^{\rm 
h}45^{\rm m}09.34s$, $\delta=-31\ensuremath{^\circ}20\ensuremath{'}24.09\ensuremath{''}$, J2000" (Observations); distance from van Leeuwen 2007 (cite: van07)  
  > "At a distance of $9.91\pm0.10$ pc (cite: van07), the M1 star AU Mic hosts one of the closest and best studied debris disks." (Introduction); "pointing center $\alpha=20^{\rm 
h}45^{\rm m}09.34s$, $\delta=-31\ensuremath{^\circ}20\ensuremath{'}24.09\ensuremath{''}$, J2000" (Observations)

## Data provenance

- ALMA projects: 2011.0.00142.S
- bands: Band 6 (1.3 mm), Cycle 0  
  > "AU Mic was observed by ALMA with its Band 6 receivers over four 2 hour-long “scheduling blocks" (SBs) in 2012 Apr and Jun." (Observations)
- frequencies and spectral setup: four 2 GHz basebands, 128 channels each, centered at 226, 228, 242, 244 GHz; two polarizations  
  > "processing two polarizations in four 2 GHz-wide basebands, each with 128 spectral channels, centered at 226, 228, 242, and 244 GHz." (Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m antennas, 16-20 per SB  
  > "The 16-20 operational 12-m antennas were arranged to span baseline lengths of 21–402 m" (Observations)
- configurations: _not stated_
- baselines: 21–402 m  
  > "The 16-20 operational 12-m antennas were arranged to span baseline lengths of 21–402 m" (Observations)
- angular resolution: synthesized beam 0.80" x 0.69" (8x7 AU), p.a. 49 deg for SB-4  
  > "with synthesized beam $0.80\ensuremath{''} \times 0.69\ensuremath{''}$ ($8\times7$ AU), p.a. 49$^\circ$" (3.1 Image of 1.3 mm Dust Continuum Emission)
- max recoverable scale: _not stated_
- sensitivity: rms 30 uJy/beam (SB-4)  
  > "and rms of 30 $\mu$Jy beam$^{-1}$" (3.1 Image of 1.3 mm Dust Continuum Emission)
- time on source: _not stated_
- observing dates: 2012 Apr 23, Apr 24, Jun 16 (four SBs)  
  > "SB-4 | 2012 Jun 16 05:48 – 08:02 |    20    |   0.7" (Table 1)
- pi or archival as stated: _not stated_
- External data: NextGen stellar model photosphere (Teff=3720 K, L=0.11 Lsun) giving F*=52 uJy at 1.3 mm, fitted to 0.4–25 um photometry  
  > "A NextGen stellar model (cite: hau99) with $T_{\rm eff} = 
3720$ K, $L_{\ast} = 0.11$ L$_{\odot}$, and $M_{\ast} = 0.6$ M$_{\odot}$ (cite: met05; che05)" (4.1 The Central Emission Peak) [from Hauschildt et al. 1999 (cite: hau99); Metchev 2005; Chen 2005]
- External data: Astrosilicate opacity composition used for dust  
  > "We calculated various $\kappa_{\nu}$ for dust with the (cite: wei01) “astrosilicate” composition" (4.1 The Central Emission Peak) [from Weingartner & Draine 2001 (cite: wei01)]

## Processing

### Calibration

- pipeline or manual: Calibrated independently per SB in CASA (Tsys, WVR, flagging, averaging to 6.048 s)  
  > "The data from each SB were calibrated independently within the `CASA` software package." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune  
  > "The absolute flux calibration was derived from observations of Neptune" (Observations)
- flux scale uncertainty: ~10%  
  > "with a systematic uncertainty of $\sim$10% (see §3.3)" (Observations)
- self calibration: _not stated_

### Imaging

- task: CLEAN with multi-frequency synthesis at 235 GHz  
  > "performed a multi-frequency synthesis deconvolution with the `CLEAN` algorithm" (Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "we Fourier inverted the calibrated visibilities with natural weighting" (Observations)
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
- final beam: 0.80" x 0.69", PA 49 deg  
  > "with synthesized beam $0.80\ensuremath{''} \times 0.69\ensuremath{''}$ ($8\times7$ AU), p.a. 49$^\circ$" (3.1 Image of 1.3 mm Dust Continuum Emission)
- final rms: 30 uJy/beam  
  > "and rms of 30 $\mu$Jy beam$^{-1}$" (3.1 Image of 1.3 mm Dust Continuum Emission)

### Inherited from earlier work

- Parametric modeling approach for resolved mm debris disk emission  
  > "Building on the phenomenological methodology of (cite: wil11; wil12) to analyze resolved millimeter emission from debris disks" (3.2 Modeling Formalism) [from Wilner et al. 2011, 2012 (cite: wil11; wil12)]
- MCMC affine-invariant ensemble sampler, parallel implementation  
  > "We used the affine-invariant ensemble sampler proposed by (cite: goo10), in a locally-modified version of the parallelized implementation described by (cite: for12)" (3.2 Modeling Formalism) [from Goodman & Weare 2010; Foreman-Mackey et al. 2012]

### Not stated but needed to reproduce (our reading)

- Flagging details and line/edge channels excluded beyond 'central 112 channels'
- Cell size, image size, CLEAN mask and threshold
- Neptune flux model used
- Number of walkers and burn-in/convergence criteria
- Model code (visibility generation) not released
- Reweighting procedure details
- Dust temperature adopted when computing belt mass from the 7.14 mJy flux in detail

## Analysis recipe

1. **Calibrate and image continuum**: Calibrate each SB in CASA; natural-weighted MFS CLEAN image at 235 GHz; average central 112 channels per baseband and reweight  
  > "The visibilities were further reduced by spectrally averaging over the central 112 channels in each baseband and re-weighted by the observed scatter." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Image from all 4 SBs consistent but noisier than SB-4  
  > "An image constructed from all 4 SBs is consistent but noisier" (3.1 Image of 1.3 mm Dust Continuum Emission)
2. **Fit parametric belt + central Gaussian model to visibilities**: Edge-on thin axisymmetric belt with power-law intensity plus circular Gaussian central source, fitted directly in visibilities for four basebands  
  > "For a given parameter set, we compute four synthetic visibility sets sampled at the same spatial frequencies observed by ALMA" (3.2 Modeling Formalism)
   - software: MCMC (affine-invariant ensemble sampler)
   - parameter: ~10^6 MCMC trials; 12 free parameters  
  > "(905,920 independent datapoints, 12 free parameters)" (3.3 Results of Model Fits)
   - assumption: Inclination 89.5 deg  
  > "We assume the belt is viewed at an inclination of 89.5$^\circ$." (3.2 Modeling Formalism)
   - fitting: ln L = -chi^2/2; uniform priors with bounds F_belt, F_cen, sigma^2_cen >= 0 and 0 <= r_i < r_o  
  > "Uniform priors were assumed for all parameters, with bounds imposed to ensure that the model was well-defined" (3.2 Modeling Formalism)
   - validation: Reduced chi^2 = 1.37; no significant residuals; fits to each SB individually consistent  
  > "The results were entirely consistent, although the parameter uncertainties were notably smaller from the superior SB-4 dataset alone" (3.3 Results of Model Fits)
3. **Estimate dust mass and temperature of central peak and outer belt**: Optically thin dust emission F = kappa B(T) M / d^2 with astrosilicate opacity, n(a)∝a^-3.5, amin=0.2 um, amax 1 um–1 cm; max T constrained by IR SED  
  > "we computed the maximum $T$ (and minimum $M_{\rm dust}$) consistent with both the observed millimeter flux density and the infrared SED." (4.1 The Central Emission Peak)
   - parameter: kappa = 2.7 cm^2/g; outer belt T ≈ 25 K  
  > "Adopting the opacity used in §4.1 ($\kappa_{\nu}$ = 2.7 cm$^2$ g$^{-1}$), and assuming $T \approx 25$ K (for 35-45 AU)" (4.2 The Outer Dust Belt)
   - assumption: d = 9.91 pc; central peak is star plus dust  
  > "We assume the central peak represents the combined emission from the star and dust, such that $F_{\rm dust} = F_{\rm cen} - F_{\ast} \approx 0.25$ mJy at 1.3 mm." (4.1 The Central Emission Peak)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration and imaging  
  > "The data from each SB were calibrated independently within the `CASA` software package." (Observations)
- **CLEAN** : multi-frequency synthesis deconvolution  
  > "performed a multi-frequency synthesis deconvolution with the `CLEAN` algorithm" (Observations)
- **affine-invariant ensemble MCMC sampler (Goodman & Weare; Foreman-Mackey et al.)** : posterior sampling of model parameters  
  > "in a locally-modified version of the parallelized implementation described by (cite: for12), to compute likelihood values for $\sim$10$^6$ MCMC trials" (3.2 Modeling Formalism)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Outer belt radial index x | 2.32 | +0.21/-0.31 | dimensionless | 2 | $x$ / belt radial power law index / 2.32 / +0.21, -0.31 |
| Belt outer radius r_o | 40.3 | ±0.4 | AU | 2 | $r_o$ / belt outer radius (AU) / 40.3 / +0.4, -0.4 |
| Belt flux density | 7.14 | +0.12/-0.25 | mJy | 2 | $F_{\rm belt}$ / belt flux density (mJy) / 7.14 / +0.12, -0.25 |
| Belt position angle | 128.41 | +0.12/-0.13 | deg | 2 | PA / belt position angle ($^\circ$) / 128.41 / +0.12, -0.13 |
| Central peak flux density | 0.32 | ±0.06 | mJy | 2 | $F_{\rm cen}$ / Gaussian flux density (mJy) / 0.32 / +0.06, -0.06 |
| Central peak HWHM | <=3.0 (3 sigma) | not stated | AU | 2 | It is unresolved, with $\mathcal{R_{\rm cen}} \le 3.0$ AU (3 $\sigma$) |
| Inner belt dust mass | ~9e23 g (~1% lunar mass) | not stated | g | 3 | The corresponding minimum $M_{\rm dust}$ is $\sim$$9 \times 10^{23}$ g, about 1% of the lunar mass. |
| Outer belt dust mass | 7e25 g | not stated | g | 3 | the dust mass of this outer belt is $7 \times 10^{25}$ g (cite: liu04b) |
| Reduced chi^2 of best fit | 1.37 | not stated | dimensionless | 2 | The best-fit model has a reduced $\chi^2 = 1.37$ |

## Qualitative findings

- No significant asymmetries or substructure in the outer belt; no centroid offset between belt and central peak  
  > "The ALMA data show no clear evidence for asymmetries or substructure that would signal planet-disk interactions." (4.2 The Outer Dust Belt)

## Claim tuples

- H: Does the mm emission show a rising profile in the outer belt rather than a narrow ring? | E: Visibility-domain MCMC fit of a power-law belt | R: x = 2.32 (+0.21/-0.31); x<0 models leave residuals | F: Belt emission rises out to 40 AU, with a sharp outer edge at the birth ring | **supported**
- H: Is there an additional central emission component? | E: Added central Gaussian to model | R: F_cen = 0.32 mJy, unresolved, ~6x photosphere | F: Central peak exists; possibly an inner planetesimal belt, though stellar emission not excluded | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Stellar corona/flare emission for the central peak considered unlikely because it persists at consistent intensity across all four observations  
  > "the mm-wave peak persists at a consistent intensity in all four ALMA observations" (4.1 The Central Emission Peak)
- How they decided it was enough: _not stated_
- Limitation (authors): Spectral index of central peak poorly constrained; inner belt interpretation needs higher resolution  
  > "Unfortunately, the spectral index ($\alpha_{\rm cen}$) constraints are not good enough to be diagnostic." (4.1 The Central Emission Peak)
- Caveat (inferred, ours): Central peak origin (stellar vs dust) degenerate
- Caveat (inferred, ours): Inner belt mass depends on assumed opacity/size distribution
- Caveat (inferred, ours): Edge-on fixed inclination and thin-belt assumption
- Caveat (inferred, ours): Earlier SBs have worse calibration; only SB-4 used

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Fitting code
- Missing: Walker count and convergence details
- Missing: Imaging parameters
- Data volume (inferred): ~10-30 GB raw for four Cycle 0 SBs
- Score (inferred): 3/5, Public Cycle 0 data and a clear model description with a table of results, but no code, and imaging and MCMC details are missing.
- Rediscovery candidate: yes, Data are an ALMA Cycle 0 project (public per archive link), the model is described, and results are numeric, though public status is not stated in the paper.

## Links

- Method: Wilner et al. 2012 (cite: wil12) (Prior parametric mm modeling of AU Mic)

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 38,
  "rate": 0.576
 },
 "evidence_ok": true
}
```
