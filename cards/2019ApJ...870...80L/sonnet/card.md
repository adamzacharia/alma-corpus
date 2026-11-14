# Spatially Resolved [C II] Emission in SPT0346-52: A Hyper-starburst Galaxy Merger at z ∼ 5.7

`2019ApJ...870...80L` | The Astrophysical Journal 2019 | first author: Litke, Katrina C. | arXiv: 1811.07800 | DOI: 10.3847/1538-4357/aaf057

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What is the source-plane structure and kinematics of the lensed DSFG SPT0346-52 in [CII] and dust continuum, and does the [CII] deficit hold on sub-kpc scales?  
  > "We discuss the \[CII\] deficit with a pixellated study of the $\rm{L_{[C{\scriptsize II}]}/L_{FIR}}$ ratio in the source plane." (abstract)
- Target **SPT0346-52 (SPT-S J034640-5204.9)**: coordinates _not stated_; z/distance z=5.6559; 1'' = 6.035 kpc  
  > "SPT0346-52 is a gravitationally lensed galaxy at $z=5.6559$ (cite: weiss2013), with lensing magnification $\mu = 5.6\pm 0.1$ (cite: spilker2016)." (1 Introduction); distance from Weiss et al. 2013 (redshift); Planck cosmology with Wright 2006 calculator  
  > "SPT0346-52 is a gravitationally lensed galaxy at $z=5.6559$ (cite: weiss2013), with lensing magnification $\mu = 5.6\pm 0.1$ (cite: spilker2016)." (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.01231.S
- bands: Band 7  
  > "ALMA Band 7 observations of SPT0346-52 were carried out on 2014 September 02 and 2015 June 28 (project ID: 2013.1.01231, PI: Marrone)." (2 ALMA Observations)
- frequencies and spectral setup: reference (first LO) frequency 291.53 GHz  
  > "The reference frequency (first local oscillator frequency) was 291.53GHz." (2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: up to 1.1 km (34 antennae) and up to 1.6 km (41 antennae)  
  > "The 2014 September 02 observation used 34 antennae with baselines up to 1.1km. For the 2015 June 28 observation, 41 antennae were used with baselines up to 1.6km" (2 ALMA Observations)
- angular resolution: 0.26x0.23 arcsec and 0.19x0.17 arcsec  
  > "| 2015-Jun-28 | $41$ | $0.19\times 0.17$ | $1.315$ | $5.2$ | $0.54$ |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.44 and 0.54 mJy/beam  
  > "| 2014-Sep-02 | $34$ | $0.26\times 0.23$ | $0.944$ | $5.3$ | $0.44$ |" (Table 1)
- time on source: ~5 min in each observation  
  > "SPT0346-52 was observed twice at different resolutions, with $\sim 5$ minutes on source in both observations." (2 ALMA Observations)
- observing dates: 2014 September 02 and 2015 June 28  
  > "ALMA Band 7 observations of SPT0346-52 were carried out on 2014 September 02 and 2015 June 28" (2 ALMA Observations)
- pi or archival as stated: PI Marrone  
  > "(project ID: 2013.1.01231, PI: Marrone)" (2 ALMA Observations)
- Line: [CII] 158 um fine structure (not stated)
- External data: Total L_FIR used to scale pixel continuum to luminosity  
  > "using $\rm{L_{FIR}}$ from (cite: gullberg2015) and corrected for lensing using the magnification from (cite: spilker2016)" (4.1 [CII] Deficit) [from (cite: gullberg2015)]
- External data: Total gas mass 1.5e11 Msun  
  > "The total gas mass, $M_g = 1.5\times 10^{11}\ \rm{M_{\odot}}$, taken from (cite: spilker2015)" (5.2 Stability of Components) [from (cite: spilker2015)]
- External data: Lensing magnification 5.6  
  > "corrected for lensing using the magnification from (cite: spilker2016)" (4.1 [CII] Deficit) [from (cite: spilker2016)]
- External data: SFR used for depletion time  
  > "dividing the gas mass from (cite: spilker2015) by the star formation rate from (cite: ma2015)" (5.1 Merging Galaxies) [from (cite: ma2015)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline plus some additional flagging beforehand  
  > "Some additional flagging was carried out before processing the data with the pipeline." (2 ALMA Observations)
- casa version: pipeline version 4.2.2  
  > "pipeline version 4.2.2" (2 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0334-4008 (also phase calibrator)  
  > "J0334-4008 was used as both the flux calibrator and the phase calibrator on both days." (2 ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA  
  > "Images were made using the CLEAN algorithm within CASA, with Briggs weighting (robust=0.5)." (2 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust=0.5  
  > "with Briggs weighting (robust=0.5)" (2 ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: UVCONTSUB, fitorder=1  
  > "The continuum was subtracted from the line cube using UVCONTSUB (fitorder=1)." (2 ALMA Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: binned to 50 km/s channels  
  > "The \[CII\] data were binned to $50\ \rm{km\ s^{-1}}$ channels." (2 ALMA Observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Pixellated lensing code RIPPLES framework  
  > "This code is described in detail in (cite: hezaveh2016), with the general framework of using pixellated sources described in (cite: warren2003) and (cite: suyu2006)." (3.1) [from (cite: hezaveh2016)]
- Initial lens parameters  
  > "The initial parameters are taken from previous lensing reconstructions of SPT0346-52 by (cite: hezaveh2013) and (cite: spilker2015)." (3.2) [from (cite: hezaveh2013); (cite: spilker2015)]
- epicyclic factor a=sqrt(3)  
  > "(cite: swinbank2015) and (cite: oteo2016) used an intermediary value of $a=\sqrt{3}$; we use the same substitution here." (5.2) [from (cite: swinbank2015); (cite: oteo2016)]

### Not stated but needed to reproduce (our reading)

- Image size, cell size, clean masks/threshold and number of iterations
- Line-free channels for UVCONTSUB and continuum bandwidth
- RIPPLES source pixel grid size, priors and MCMC settings
- Value of regularization lambda for the [CII] cube
- Spectral windows and which data were combined for the reconstruction
- Dust-continuum frequency/flux scale and amplitude calibration uncertainty
- Rest frequency of [CII] and velocity zero point
- 3D-Barolo settings
- Whether RIPPLES code is publicly available

## Analysis recipe

1. **Calibrate and image ALMA data**: CASA pipeline, extra flagging, CLEAN with Briggs weighting, UVCONTSUB, 50 km/s channels  
  > "The continuum was subtracted from the line cube using UVCONTSUB (fitorder=1)." (2 ALMA Observations)
   - software: CASA
   - parameter: robust=0.5; fitorder=1  
  > "with Briggs weighting (robust=0.5)" (2 ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit lens model to continuum**: Pixellated visibility-plane reconstruction with SIE (z=0.9) plus external shear; lens parameters from MCMC, regularization lambda iterated  
  > "We model the lensing galaxy as a singular isothermal ellipsoid at $z=0.9$ with an external shear component." (3.2)
   - software: RIPPLES
   - parameter: lambda fitted for fixed lens model, alternating with MCMC until convergence  
  > "We fit for $\lambda$, then run the MCMC with RIPPLES. These two steps are repeated until the chains have converged" (3.1)
   - assumption: Lens at z=0.9  
  > "singular isothermal ellipsoid at $z=0.9$" (3.2)
   - fitting: chi^2 against visibilities, MCMC; priors not stated  
  > "The model visibilities are compared to the observed visibilities via a $\chi^2$ goodness-of-fit test." (3.1)
   - validation: Mock point-source visibilities reconstructed to give effective source-plane resolution  
  > "we created a set of mock visibilities for a point source in the source plane that was lensed by the best-fit lens model." (3.3 Source Plane Resolution)
3. **Reconstruct [CII] per channel and build maps/spectra**: Apply best-fit lens model to each 50 km/s channel with fixed lambda; sum channels into moment maps; sum pixels for source spectrum and fit two Gaussians  
  > "The best-fit model was then applied to the \[CII\] line in each $50\ \rm{km\ s^{-1}}$ channel." (3.2)
   - software: RIPPLES
   - fitting: two-component Gaussian fit to source-plane spectrum  
  > "A two-component Gaussian was fit to the spectrum" (3.2)
   - validation: _not stated_
4. **Resolved [CII]/FIR ratio**: Scale pixel continuum to total L_FIR (Gullberg+15), lensing-corrected; compare L_CII/L_FIR vs Sigma_FIR  
  > "The measured continuum flux in each pixel, $\rm{F_{cont,i}}$, is scaled proportional to the total $\rm{L_{FIR}}$" (4.1)
   - assumption: constant flux-to-luminosity ratio, i.e. constant dust temperature  
  > "This method assumes a constant flux density-to-luminosity ratio, and thus a constant dust temperature." (4.1)
   - fitting: _not stated_
   - validation: Modified blackbody SEDs for 22<Td<57 integrated over 42.5-122.5 um give L_FIR within factor ~2  
  > "Resulting $\rm{L_{FIR}}$ values were within a factor of $\sim 2$ of the luminosity measured by (cite: gullberg2015)" (4.1)
5. **Kinematic decomposition**: Moment maps, PV diagrams, two-Gaussian fit per pixel, elliptical Gaussian fit to each component  
  > "we fit the spectrum of each pixel with two Gaussian components." (4.2)
   - fitting: _not stated_
   - validation: _not stated_
6. **Toomre Q**: Q = sigma_r * sqrt(3) v_r/r / (pi G Sigma_gas); v_r from 3D-Barolo tilted-ring fits of velocity fields; Sigma_gas from M_g split by [CII] flux  
  > "These velocity fields were then fit using the 2D tilted ring modeling in 3D-Barolo (cite: bbarolo)." (5.2)
   - software: 3D-Barolo
   - assumption: [CII] traces gas; M_g=1.5e11 Msun; a=sqrt(3); sigma_r used as upper limit on turbulent dispersion  
  > "To calculate the gas surface density, $\Sigma_{\rm gas}$, we assume the \[CII\] emission traces the gas." (5.2)
   - fitting: _not stated_
   - validation: Using sigma_r gives upper limit on Q so Q<<1 is robust  
  > "Thus, the result that $Q\ll 1$ everywhere and the disks are gravitationally unstable does not depend on this substitution." (5.2)

## Software

- **CASA** pipeline 4.2.2: calibration and imaging  
  > "pipeline version 4.2.2" (2 ALMA Observations)
- **RIPPLES** : pixellated lensing reconstruction  
  > "we use the pixellated lensing reconstruction code RIPPLES." (3.1)
- **3D-Barolo** : tilted-ring fits to velocity fields  
  > "fit using the 2D tilted ring modeling in 3D-Barolo" (5.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Blue component velocity | -287 | 22 | km/s | 3 | The blue component is centered at $-287\pm 22\ \rm{km\ s^{-1}}$ and has a FWHM of $337\pm 22\ \rm{km\ s^{-1}}$. |
| Red component velocity | +158 | 22 | km/s | 3 | The red component is centered at $+158 \pm 22\ \rm{km\ s^{-1}}$ with a FWHM of $319 \pm 15\ \rm{km\ s^{-1}}$. |
| Effective source-plane resolution | 0.13x0.15 arcsec (0.12x0.12 near caustic) | not stated | arcsec | 2 | the effective resolution is $0.13\ensuremath{''} \times 0.15\ensuremath{''}$ |
| Central L_CII/L_FIR | ~1e-4 | not stated | dimensionless | 4 | Typical values of the $\rm{L_{[C{\scriptsize II}]}/L_{FIR}}$ ratio in the center of SPT0346-52 are around $\sim 1 \times 10^{-4}$. |
| Mean Toomre Q blue component | 0.03 (max 0.13) | not stated | dimensionless | 6 | $\bar{Q}=0.03$ and a maximum value of $Q_{\rm max}=0.13$ |
| Mean Toomre Q red component | 0.02 (max 0.06) | not stated | dimensionless | 6 | $\bar{Q}=0.02$ and $Q_{\rm max}=0.06$ |
| Gas depletion timescale | 31 | 10 | Myr | 0 | we calculate a gas depletion timescale of $31 \pm 10\ \rm{Myr}$ |
| f_[CII] | 0.21 | not stated | dimensionless | 4 | we find that $\rm f_{[C{\scriptsize II}]} = 0.21$ |
| Lens mass log | 11.43 | 0.02 | log Msun | 2 | $\rm{\log{Mass[M_{\odot}]}}$ / $11.43 \pm 0.02$ |

## Qualitative findings

- Two spatially/kinematically separated components joined by a gas bridge; dust continuum is more compact and smoother than [CII].  
  > "The lensing reconstruction reveals two spatially and kinematically separated components" (abstract)

## Claim tuples

- H: Does the [CII] deficit hold at sub-kpc scales? | E: Pixel-by-pixel L_CII/L_FIR vs Sigma_FIR in source plane | R: Pixels follow the unresolved-galaxy trend | F: Deficit arises on scales <~700 pc | **supported**
- H: Is SPT0346-52 a merger or a rotating disk? | E: Kinematic analysis of reconstructed [CII] cube | R: Two components ~1 kpc and ~500 km/s apart with bridge | F: Major merger likely driving star formation | **supported**
- H: Are components gravitationally stable? | E: Resolved Toomre Q | R: Q<<1 everywhere | F: Globally unstable | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Pixellated source does not assume a specific source structure and uses all interferometric data  
  > "it does not assume a specific source structure" (3.1)
- Alternative: Clumpy rotating disk considered; merger favored given higher S/N  
  > "allowing a more confident classification of this system as a merger rather than a clumpy, rotating disk." (5.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Constant dust temperature assumed, uncertainty within factor ~2  
  > "the variation caused by variable dust temperatures in the galaxy is within a factor of $\sim 2$." (4.1)
- Caveat (inferred, ours): Q depends on assumed global gas mass distributed by [CII] flux and a=sqrt(3)
- Caveat (inferred, ours): Lens model fit on continuum only and applied to line; no lens uncertainty propagation into maps
- Caveat (inferred, ours): Merger interpretation rests on two-Gaussian decomposition without independent tests

## Reproducibility

- Data public (paper): ALMA project 2013.1.01231.S cited  
  > "ADS/JAO.ALMA#2013.1.01231.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: RIPPLES setup and priors
- Missing: imaging parameters
- Missing: regularization value
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Public data and clear workflow, but lensing code settings and imaging details are missing.
- Rediscovery candidate: no, Key results depend on RIPPLES setup and unstated parameters.

## Links

- Method: (cite: hezaveh2016) (RIPPLES lensing code)
- Method: (cite: bbarolo) (3D-Barolo)
- Companion: (cite: spilker2015) (CO(2-1) reconstruction, gas mass)
- Companion: (cite: spilker2016) (magnification, continuum reconstructions)
- Related: South Pole Telescope survey

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
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 49,
  "rate": 0.62
 },
 "evidence_ok": true
}
```
