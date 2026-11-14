# ALMA Reveals an Eccentricity Gradient in the Fomalhaut Debris Disk

`2025ApJ...990..145L` | The Astrophysical Journal 2025 | first author: Lovell, Joshua B. | arXiv: 2509.02884 | DOI: 10.3847/1538-4357/adfadc

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: debris_disks
- Question: Does the Fomalhaut debris disk host a forced eccentricity gradient with semi-major axis, and what planetary and formation scenarios are consistent with it?  
  > "We present evidence of a negative eccentricity gradient in the debris disk of the nearby A-type main sequence star, Fomalhaut." (abstract)
- Target **Fomalhaut (HD 216956)**: coordinates _not stated_; z/distance 7.66 pc  
  > "the 7.66 pc-distant, 440 Myr old, A-type main sequence star, Fomalhaut" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00486.S, 2015.1.00966.S, 2017.1.01043.S
- bands: Band 6 (1.32 mm)  
  > "the three *ALMA* band 6 data sets included" (2.1 ALMA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.76 x 0.55 arcsec (6x4 au), beam PA -87.4 deg  
  > "a synthesised clean beam with $0.76 \times 0.55''$, and beam position angle $-87.4^\circ$" (2.1 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: 8.0 uJy/beam rms in disk-free regions  
  > "$\delta I_{\rm{data}}=8.0\,\mu$Jy beam$^{-1}$ based on the root-mean-square of pixel intensities in disk-free regions" (3.3 Model fitting)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival data from three programs (PIs Boley, Kalas, MacGregor)  
  > "archival *ALMA* 1.32 mm continuum data for Fomalhaut" (abstract)
- Other facility **JWST MIRI/NIRCam**: Published intermediate-belt edges and eccentricities (MIRI) and planet mass limits (NIRCam) used to constrain planet scenarios  
  > "the first evidence of an ‘intermediate belt’ is presented, which has inner and outer edges of 83 au and 104 au respectively" (4.1 Planet properties)
- External data: Calibrated, aligned, combined ALMA band 6 image of Fomalhaut  
  > "For this study we fit to the images of Fomalhaut from (cite: Chittidi_rev)." (2.1 ALMA observations) [from (cite: Chittidi_rev)]
- External data: Stellar parameters T=8500 K, R=1.8 Rsun, M=1.9 Msun  
  > "the effective temperature ($T_\star=8500\,$K), stellar radius ($R_\star=1.8R_\odot$) and stellar mass ($M_\star=1.9M_\odot$)" (2.2 Model setup) [from (cite: Mamajek2012)]
- External data: Intermediate belt edges 83 and 104 au with eccentricities 0.31 and 0.265  
  > "which has inner and outer edges of 83 au and 104 au respectively, with large corresponding eccentricities of 0.31 and 0.265" (4.1 Planet properties) [from (cite: Gaspar+2023)]
- External data: NIRCam planet mass limit <~200 Mearth beyond 5 arcsec  
  > "place constraints on planet masses of $M_{\rm{pl}}{\lesssim}200\,M_\oplus$ beyond $5''$ (38.3 au)" (4.1 Planet properties) [from (cite: Ygouf+2024)]

## Processing

### Calibration

- pipeline or manual: Standard CASA ALMA reduction pipelines, done in Chittidi et al.  
  > "utilizes standard `CASA` ALMA reduction pipelines" (2.1 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% ALMA flux calibration uncertainty  
  > "accounting for a 10% *ALMA* flux calibration uncertainty in quadrature with our fitting error" (3.4.1 Fitting an EVD disk model)
- self calibration: _not stated_

### Imaging

- task: tclean, same parameters as Chittidi et al.  
  > "We use the same `tclean` parameters for imaging as (cite: Chittidi_rev)" (2.1 ALMA observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust 0.5  
  > "a briggs-weighting scheme and robust parameter of 0.5" (2.1 ALMA observations)
- uv taper: _not stated_
- cell size: 0.075 arcsec  
  > "with a pixel size of $0.075''$" (2.1 ALMA observations)
- image size: _not stated_
- masking: Fit mask: primary beam response >0.66 and projected radius <200 au  
  > "only fitting emission where the primary beam response exceeds $0.66$" (3.3 Model fitting)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Fit to primary-beam corrected image, CASA primary beam form  
  > "We fit to the primary-beam corrected image" (3.3 Model fitting)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.76 x 0.55 arcsec, PA -87.4 deg  
  > "$0.76 \times 0.55''$, and beam position angle $-87.4^\circ$" (2.1 ALMA observations)
- final rms: _not stated_

### Inherited from earlier work

- Calibration, data alignment and imaging parameters  
  > "We use the same `tclean` parameters for imaging as (cite: Chittidi_rev)" (2.1 ALMA observations) [from (cite: Chittidi_rev)]
- Model fitting approach, here in image domain rather than visibilities  
  > "Our fitting approach is consistent with the procedures of (cite: Lovell21c; Lovell22)" (3.3 Model fitting) [from (cite: Lovell21c; Lovell22)]
- Free eccentricity modelling via summed families of orbits  
  > "we adopt the same approach as (cite: LovellLynch2023)" (3.4.2 Sensitivity to free eccentricity) [from (cite: LovellLynch2023)]

### Not stated but needed to reproduce (our reading)

- emcee priors and bounds for each parameter
- initial walker positions
- Chittidi et al. pipeline/CASA version and the image file itself
- RADMC-3D settings such as photon count, grid and dust composition
- how the mask and primary-beam response were computed numerically
- REBOUND random seed and particle output details

## Analysis recipe

1. **Fit stellar flux and position**: Fit the star separately with a 10x10 pixel box mask  
  > "masking all but a $10\times10$ pixel box" (3.4.1 Fitting an EVD disk model)
   - software: emcee, RADMC-3D
   - fitting: _not stated_
   - validation: Offsets consistent with zero  
  > "the star is best-fitted with offsets consistent with 0.0 in both axes" (3.4.1 Fitting an EVD disk model)
2. **Fit eccentric-gradient disk model in image domain**: RADMC-3D parametric optically thin disk with Gaussian semi-major axis profile and power-law forced eccentricity, convolved with the clean beam and fit to the primary-beam corrected image  
  > "by imaging 3-dimensional dust distributions within the `RADMC-3D` framework" (2.2 Model setup)
   - software: RADMC-3D, emcee
   - parameter: 9 free parameters: M_disk, a0, w_r, e_f0, omega_f, n_pow, i, PA, h; 40 walkers, 6000 steps, first half removed  
  > "fitted only for the disk mass ($M_{\rm{disk}}$), semi-major axis ($a_0$), disk width ($w_r$)" (3.4.1 Fitting an EVD disk model)
   - assumption: Dust sizes 0.9 um–1 cm, -3.5 power law, 3.5 g/cm3, optically thin, Kurucz stellar spectrum  
  > "fixed size distribution between $0.9\,\mu$m–$1.0\,$cm with a $-3.5$ power-law index" (2.2 Model setup)
   - fitting: emcee affine-invariant ensemble sampler, Gaussian likelihood exp(-chi2/2) with pixel-correlation reweighting by l_pix^2/Omega_beam; priors not stated  
  > "a Gaussian likelihood function ($\propto \exp({- \chi^2/2})$)" (3.3 Model fitting)
   - validation: Residual mean and std checked; autocorrelation time ~120, steps >50 tau; Verify fit to cycle 3-only data  
  > "convergence is achieved when the number of steps exceeds ${>}50\times \tau$" (Model convergence)
3. **Compare to free-eccentricity models**: Fit Proper 1 (n_pow=0) and Proper 2 (n_pow=-1) models with free eccentricity e_p, compare delta chi2 converted to sigma via incomplete gamma function  
  > "the General model returns a lower $\chi^2$ than the Proper 1 and 2 models by 70 and 22 respectively" (3.5 Which model is preferred?)
   - software: emcee
   - fitting: emcee 3000 steps (Proper 1), 5000 (Proper 2) in main text  
  > "(for 5000 steps to ensure convergence)" (3.4.2 Sensitivity to free eccentricity)
   - validation: Visibility-domain chi2 check on Cycle 5 apocenter pointing agrees  
  > "has the lowest $\chi^2$ by 350 (versus Proper 1) and 245 (versus Proper 2)" (3.5 Which model is preferred?)
4. **Derive single-planet scenarios**: Analytic relations from Mustill & Wyatt 2012, 2009 and Morrison & Malhotra 2015 using disk inner edge ~125 au and e~0.16  
  > "using equation 10 of (cite: Mustill12), i.e., $(a_{\rm{inner}}-a_{\rm{pl}})/a_{\rm{pl}} {=}1.8\times(e_{\rm{inner}}\mu)^{1/5}$" (4.1.1 A gap-carving planet?)
   - assumption: Single co-planar planet; Fomalhaut mass 2 Msun  
  > "On the assumption that a single, co-planar planet is responsible for carving the observed disk structure" (4.1 Planet properties)
   - fitting: _not stated_
   - validation: Compared with JWST NIRCam limits and Fomalhaut b orbit  
  > "Recent observations of Fomalhaut with the *JWST NIRCam* instrument place constraints on planet masses of $M_{\rm{pl}}{\lesssim}200\,M_\oplus$ beyond $5''$ (38.3 au) from the stellar center" (Planet properties consistent with ALMA and JWST observations)
5. **N-body stability test**: REBOUND WHFast, 2e5 test particles, circular vs eccentric (e∝a^-1) initial disks, three planets, up to 440 Myr  
  > "We adopt the `WHFAST` symplectic integrator (cite: Rein+2015) with a fixed timestep set to 1 per cent of the initially innermost particles orbital period" (5.1.1 REBOUND setup)
   - software: REBOUND
   - parameter: softening b=1e-6 a_pl  
  > "gravitational softening parameter set to $b = 10^{-6} [a_{\rm pl}]$" (5.1.1 REBOUND setup)
   - assumption: Massless test particles, single planet  
  > "we consider the interaction of this star-planet system with a population of test particles" (5.1 N-body modelling)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration/imaging (in prior work), statwt and visibility checks  
  > "after applying the `CASA statwt` function to the data" (3.5 Which model is preferred?)
- **RADMC-3D** : Imaging 3D dust models  
  > "by imaging 3-dimensional dust distributions within the `RADMC-3D` framework" (2.2 Model setup)
- **emcee** : MCMC fitting  
  > "We fit our model to the *ALMA* data with `emcee`" (3.3 Model fitting)
- **REBOUND** : N-body stability simulations  
  > "To investigate the stability of orbits in the Fomalhaut system, we use `REBOUND`" (5.1.1 REBOUND setup)
- **DS9** : Listed in software section  
  > "`CASA` (cite: CASA07) `DS9` (cite: ds9)." (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Forced eccentricity gradient index n_pow (General) | -1.75 | 0.16 | dimensionless | 2 | $n_{\rm{pow}}$ / – / $-1.75{\pm}0.16$ |
| Semi-major axis a0 | 138.79 | 0.12 | au | 2 | $a_0$ / au / $138.79{\pm}0.12$ |
| Gaussian width w_r | 13.51 | 0.29 | au | 2 | $w_r$ / au / $13.51{\pm}0.29$ |
| Forced eccentricity e_f0 | 12.56 | 0.12 | % | 2 | $e_{f,0}$ / \% / $12.56{\pm}0.12$ |
| Dust mass | 18.70e-2 | 0.20e-2 | Earth masses | 2 | $18.70{\pm}0.20$ |
| Inclination | 66.44 | 0.09 | deg | 2 | $i$ / deg / $66.44{\pm}0.09$ |
| Stellar flux at 1.32 mm | 0.74 | 0.08 | mJy | 1 | $F_{\rm{\star}}{=}0.74{\pm}0.08\,$mJy |
| Delta chi2 Proper 1 / Proper 2 vs General | 70.0 / 21.5 (6.7 sigma / 2.6 sigma) | not stated | dimensionless | 3 | the General model is favored over the Proper 1 and 2 models by $6.7\sigma$ and $2.6\sigma$ respectively |
| Free eccentricity e_p (Proper 1) | 3.85 | 0.17 | % | 3 | $e_p{=}3.85{\pm}0.17\%$ |
| n_pow from cycle-3-only Verify fit | -1.16 | 0.16 | dimensionless | 2 | $n_{\rm{pow}}{=}-1.16{\pm}0.16$ |

## Qualitative findings

- N-body runs: initially circular disks are disrupted, while initially eccentric disks survive 440 Myr, suggesting the ring was born eccentric  
  > "scenarios initialised with eccentric disks (E1, E2 and E3) survive the full 440 Myr simulation timescale" (5.1.2 REBOUND results)

## Claim tuples

- H: Fomalhaut's disk has a negative forced eccentricity gradient | E: Image-domain MCMC fit of a power-law e_f(a) model to the ALMA 1.32 mm mosaic | R: n_pow = -1.75±0.16 | F: Evidence of an eccentricity gradient, first in a debris disk | **supported**
- H: Gradient model is preferred over constant forced plus free eccentricity models | E: Compare chi2 of General with Proper 1 and 2 | R: Delta chi2 = 70 and 22; 6.7 and 2.6 sigma | F: Gradient model statistically preferred | **supported**
- H: Single planet can explain the disk structure | E: Analytic planet constraints and REBOUND simulations | R: Gap planet 109–120 au; Resonant planet 70–75 au; only eccentric initial disks stay eccentric | F: Planets sculpt edges but eccentricity likely formed in the protoplanetary disk stage | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Image-domain fitting is far cheaper than visibility-domain fitting, allowing many model setups  
  > "model convergence can be achieved with this image-based setup in a modest 1–2 days, whereas in the visibility domain a much more intensive 1–2 weeks per model is required" (Footnote 2)
- Alternative: Constant-eccentricity models with free eccentricity (Proper 1, 2) disfavoured  
  > "the strong preference of the General and Proper 2 models over the Proper 1 model" (3.5 Which model is preferred?)
- How they decided it was enough: _not stated_
- Limitation (authors): Massless-disk N-body ignores self-gravity; noise non-Gaussian near minor axis; residuals suggest width at apocenter not quite right  
  > "We have thus far explored the possible origin of Fomalhaut’s disk eccentricity assuming a stationary planet perturbing a *massless* debris disk." (5.2 Additional physics)
- Caveat (inferred, ours): Fit masks out the minor axes, so the gradient depends on the ansae
- Caveat (inferred, ours): Gaussian radial profile assumed; residuals hint at non-Gaussian edges
- Caveat (inferred, ours): Gradient is -1.75 vs classical -1 at 4.6 sigma, and cycle 3-only data give -1.16
- Caveat (inferred, ours): Priors and fixed grain properties may bias the results
- Caveat (inferred, ours): Combined mosaic has non-Gaussian noise but a Gaussian likelihood is used

## Reproducibility

- Data public (paper): Archival ALMA data and model code on GitHub/Zenodo  
  > "is available publicly on [ https://github.com/astroJLovell/eccentricDiskModels]" (Conclusions)
- Products in archive: _not stated_
- Code: Surface density model code at github.com/astroJLovell/eccentricDiskModels (Zenodo 10.5281/zenodo.16758671)  
  > "available via DOI: <https://doi.org/10.5281/zenodo.16758671> and at <https://github.com/astroJLovell/eccentricDiskModels>" (Footnote 1)
- Missing: Final combined image from Chittidi et al. must be rebuilt or obtained
- Missing: emcee priors
- Missing: RADMC-3D run settings
- Data volume (inferred): Three ALMA Band 6 datasets, likely tens to a few hundred GB raw; the image product is small
- Score (inferred): 3/5, Public data and released code, but depends on a companion paper for the image and omits priors.
- Rediscovery candidate: no, Requires the Chittidi et al. combined image and unstated priors, so full reproduction from the paper alone is not possible.

## Links

- Method: (cite: LynchLovell21) (Eccentric disk surface density model with power-law gradients)
- Method: (cite: Lovell21c; Lovell22) (Fitting approach)
- Companion: (cite: Chittidi_rev) (ALMA calibration, alignment and imaging of the data used)
- Companion: (cite: MacGregor17) (Earlier ALMA cycle 3 study of Fomalhaut)
- Companion: (cite: Kennedy20) (Previous eccentric disk modelling)

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 49,
  "rate": 0.613
 },
 "evidence_ok": true
}
```
