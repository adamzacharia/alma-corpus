# Resolved ALMA Continuum Image of the Circumbinary Ring and Circumstellar Disks in the L1551 IRS 5 System

`2019ApJ...882L...4C` | The Astrophysical Journal Letters 2019 | first author: Cruz-Sáenz de Miera, Fernando | arXiv: 1908.04649 | DOI: 10.3847/2041-8213/ab39ea

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: What are the geometry and masses of the circumstellar disks and the structure of the circumbinary ring in the FUor-like binary L1551 IRS 5 at 1.3 mm?  
  > "We determined the geometry and estimated lower mass limits for the circumstellar disks using simple models." (abstract)
- Target **L1551 IRS 5**: coordinates _not stated_; z/distance 147 ± 5 pc  
  > "L1551 IRS 5 is a deeply embedded very young ($\sim$10$^5$ yr) system at a distance of 147 $\pm$ 5 pc" (2 Our target); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00209.S
- bands: Band 6 (1.3 mm)  
  > "Data were taken in Band 6, with three spectral windows" (3 Observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: two continuum spws of 1875 MHz each, centered at 216.9 and 232.2 GHz  
  > "two continuum spectral windows of 1875 MHz bandwidth each, centered at 216.9 GHz and 232.2 GHz" (3 Observations and data reduction)
- arrays: 7 m array (11 antennas), 12 m compact (44 antennas), 12 m extended (44 antennas)  
  > "with the 7 m array using 11 antennas with projected baselines between 8.9 and 45 m on 2016 November 14" (3 Observations and data reduction)
- configurations: _not stated_
- baselines: 7 m: 8.9-45 m; compact: 15-500 m; extended: 30.5 m-3.6 km  
  > "in extended configuration using 44 antennas with projected baselines between 30.5 m and 3.6 km on 2017 July 24" (3 Observations and data reduction)
- angular resolution: 0.144x0.102 arcsec (uniform); 0.198x0.183 arcsec (natural)  
  > "For the uniform image the resulting synthesized beam size is 0$\ensuremath{''}$144 $\times$ 0$\ensuremath{''}$102 (21 au $\times$ 15 au)" (3 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 0.33 mJy/beam (uniform); 0.76 mJy/beam (natural)  
  > "while the rms noise is 0.33 mJy beam$^{-1}$" (3 Observations and data reduction)
- time on source: _not stated_
- observing dates: 2016-11-14 (7 m), 2018-04-24 (compact), 2017-07-24 (extended)  
  > "in compact configuration using 44 antennas with projected baselines between 15 and 500 m on 2018 April 24" (3 Observations and data reduction)
- pi or archival as stated: Cycle 4, PI Takami  
  > "We observed L1551 IRS 5 in ALMA Cycle 4 (ID: 2016.1.00209.S; PI: Takami)" (3 Observations and data reduction)
- Line: 12CO, 13CO, C18O J=2-1 (not analysed here) (not stated)
- External data: 7 mm VLA fluxes of the N and S disks used for the alpha index  
  > "we calculated the $\alpha$ index using the 7 mm ($\sim$43 GHz) VLA observations from (cite: Lim2016ApJ...826..153L)" (5.1 Photometry and in-band spectral indices) [from (cite: Lim2016ApJ...826..153L)]
- External data: Distance 147 ± 5 pc and stellar masses/binary separation used as context  
  > "L1551 IRS 5 is a deeply embedded very young ($\sim$10$^5$ yr) system at a distance of 147 $\pm$ 5 pc" (2 Our target) [from (cite: Connelley2018ApJ...861..145C)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA v.5.1.1  
  > "The data sets were calibrated using CASA v.5.1.1" (3 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: phase and amplitude self-calibration applied  
  > "We applied self-calibration for both the visibility phases and amplitudes to improve signal-to-noise ratio." (3 Observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: uniform and natural weighting  
  > "we created continuum images by cleaning using uniform and natural weighting." (3 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: line channels excluded before continuum imaging  
  > "After excluding the channels with line emission from the combined data set" (3 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: three configurations concatenated into a single data set  
  > "we concatenated them into a single data set which recovers the emission in all spatial scales." (3 Observations and data reduction)
- smoothing: _not stated_
- final beam: 0.144x0.102 arcsec uniform; 0.198x0.183 arcsec natural  
  > "In the case of the natural image the resulting synthesized beam size is 0$\ensuremath{''}$198 $\times$ 0$\ensuremath{''}$183" (3 Observations and data reduction)
- final rms: 0.33 (uniform) and 0.76 (natural) mJy/beam  
  > "while the rms noise is 0.76 mJy beam$^{-1}$" (3 Observations and data reduction)

### Inherited from earlier work

- Procedure of fitting two 2D Gaussians per CS disk  
  > "We followed a procedure similar to (cite: Lim2016ApJ...826..153L) and used two 2D Gaussians to describe each circumstellar disk" (4 Structures in the continuum map) [from (cite: Lim2016ApJ...826..153L)]
- Disk/ring surface-density parametrization for RADMC-3D models  
  > "Each model was constructed using the parametrization presented in (cite: Andrews2009ApJ...700.1502A)" (5.3 Structure of the circumbinary ring) [from (cite: Andrews2009ApJ...700.1502A)]

### Not stated but needed to reproduce (our reading)

- tclean parameters: cell size, image size, robust/weighting details, masks, threshold, niter
- line-free channel selection
- self-calibration solution intervals and number of rounds
- MCMC free parameters, priors, walkers, steps, likelihood form and noise treatment
- RADMC-3D dust opacity, grid, photon count and inclination handling for the model
- relative flux/position alignment between the three configurations
- exact aperture and elliptical-fit procedure details for the ring

## Analysis recipe

1. **Fit CS disks with 2D Gaussians**: Simultaneous single 2D Gaussian per disk fit; radii from HWHM, inclination from axis ratio, PA from deconvolved parameters  
  > "We used CASA’s IMFIT tool to fit both CS disks simultaneously using a single 2D Gaussian for each disk." (4 Structures in the continuum map)
   - software: CASA imfit
   - assumption: Distance 147 ± 5 pc  
  > "We estimated the disks radii from the half-width half-maximum assuming a distance to the system of 147 $\pm$ 5 pc." (4 Structures in the continuum map)
   - fitting: _not stated_
   - validation: _not stated_
2. **Subtract disks and characterise CB ring**: Subtract four fitted Gaussians (two per disk), fit an ellipse to pixels above 12 sigma in the residuals  
  > "We estimated the radius, inclination and position angle of the extended emission by fitting an ellipse to all pixels above 12$\sigma$ in the residual images." (4 Structures in the continuum map)
   - software: CASA
   - parameter: 12 sigma threshold  
  > "fitting an ellipse to all pixels above 12$\sigma$ in the residual images" (4 Structures in the continuum map)
   - fitting: _not stated_
   - validation: _not stated_
3. **Radial profile and ring width**: Deproject the residuals, azimuthally average, fit a 1D Gaussian to the peak, deconvolve by the beam  
  > "We estimated the width of the ring by fitting a 1D Gaussian to the peak of the radial profiles and deconvolved them by their respective beams." (4 Structures in the continuum map)
   - fitting: _not stated_
   - validation: _not stated_
4. **Photometry and spectral index**: Integrate flux in Gaussians (CS disks) and in an elliptical annulus on residuals (ring, 46-285 au); alpha from visibility amplitudes of the two continuum spws  
  > "an elliptical annulus aperture with inner radius of 46 au and outer radius of 285 au with an inclination angle of 45$^\circ$ and a position angle of 161$^\circ$" (5.1 Photometry and in-band spectral indices)
   - fitting: _not stated_
   - validation: Noted large uncertainties as the two spws are close in frequency  
  > "because the continuum spectral window frequencies are too close together there are large uncertainties in the estimation of the spectral index" (5.1 Photometry and in-band spectral indices)
5. **Dust and disk masses**: M_dust = f d^2 / (kappa B_nu(T_dust)); gas-to-dust 100:1  
  > "Assuming a 100:1 gas-to-dust mass ratio, we calculated the total disk mass for each component" (5.2 Mass estimates for the components)
   - parameter: kappa = 0.22 m^2 kg^-1; T_dust N=160 K, S=100 K, ring 80 K  
  > "$T_{\rm dust, N}$ = 160 K and $T_{\rm dust, S}$ = 100 K." (5.2 Mass estimates for the components)
   - assumption: Optically thick disks so masses are lower limits; may rise by up to 3 from beam dilution  
  > "These mass lower limits could increase by a factor of up to 3 due to beam dilution effects." (5.2 Mass estimates for the components)
   - fitting: _not stated_
   - validation: _not stated_
6. **Radiative transfer model of CB ring**: RADMC-3D models with Andrews et al. 2009 parametrization, two heating sources, compared to natural-weighted residuals  
  > "The models were generated using two heating sources with T$_*$ = 10,000 K and R$_*$ = 2 R$_\odot$" (5.3 Structure of the circumbinary ring)
   - software: RADMC-3D, emcee
   - assumption: Heating sources and ring coplanar; sources fixed at CS disk peaks; inclination and PA fixed to best fit  
  > "assumed the heating sources and the circumbinary ring to be in the same plane" (5.3 Structure of the circumbinary ring)
   - fitting: MCMC with emcee maximizing the likelihood  
  > "running a Markov chain Monte Carlo (MCMC) using the EMCEE Python module (cite: ForemanMackey2013PASP..125..306F) to explore the parameter space and maximize the likelihood function" (5.3 Structure of the circumbinary ring)
   - validation: _not stated_

## Software

- **CASA** 5.1.1: Calibration, imaging, imfit  
  > "The data sets were calibrated using CASA v.5.1.1" (3 Observations and data reduction)
- **RADMC-3D** : Radiative transfer models of the CB ring  
  > "building radiative transfer models using RADMC-3D" (5.3 Structure of the circumbinary ring)
- **emcee** : MCMC fitting  
  > "running a Markov chain Monte Carlo (MCMC) using the EMCEE Python module" (5.3 Structure of the circumbinary ring)
- **astropy** : Listed in software section; use not described  
  > "astropy (cite: astropy), CASA" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Binary separation | 365 | ±4 | mas | 1 | we estimated the separation between the two protostars to be 365 $\pm$ 4 mas (51 $\pm$ 0.6 au) |
| CB ring peak radius | 100 | ±1 | au | 3 | We found that the ring peaks at 100 $\pm$ 1 au and has a width of 38 $\pm$ 0.6 au. |
| CB ring width | 38 | ±0.6 | au | 3 | has a width of 38 $\pm$ 0.6 au |
| N disk radius (uniform) | 10.3 | ±1.8 | au | 1 | Uniform   / 10.3 $\pm$ 1.8  / 40 $\pm$ 9     / 156 $\pm$ 16 |
| N disk mass (uniform) | >4.68e-3 | not stated | Msun | 5 | $>$4.68 $\times$ 10$^{-3}$ |
| CB ring mass (uniform) | 1.95e-2 | not stated | Msun | 5 | 1.95 $\times$ 10$^{-2}$ |
| Spectral index N and S disks (7 mm to 1.3 mm) | 2.32 and 2.26 | ±0.03, ±0.04 | dimensionless | 4 | We obtained values of 2.32 $\pm$ 0.03 and 2.26 $\pm$ 0.04 for the North and South disks, respectively. |
| Model characteristic ring radius R_c | 110.9 | +0.12/-0.18 | au | 6 | $R_c = 110.9^{+0.12}_{-0.18}\,$au |

## Qualitative findings

- First resolved circumbinary ring; northern disk is the likely eruptive star  
  > "However, the present ones are the first resolved observations of the circumbinary material." (4 Structures in the continuum map)

## Claim tuples

- H: Are the CS disks resolved and how massive? | E: 2D Gaussian fits and dust mass formula | R: Disks are marginally resolved with radii ~9-14 au and mass lower limits ~4-6e-3 Msun | F: Disks are compact and probably optically thick, so masses are lower limits | **supported**
- H: Do geometric effects explain the CB ring brightness asymmetries? | E: RADMC-3D model plus MCMC compared to residuals | R: Model reproduces much of the structure; some residuals remain | F: The ring is mostly axisymmetric with small dust density enhancements | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): CS disks unresolved internally; jets and disk emission cannot be separated; spectral index uncertain  
  > "due to the beam size of our observations we are not able to clearly disentangle the emission from the CS disks and possible contribution from the jets" (4 Structures in the continuum map)
- Caveat (inferred, ours): Mass lower limits depend on brightness temperature as T_dust and on an opacity of unstated origin
- Caveat (inferred, ours): Radiative transfer fit has unstated parameter list, priors and uncertainties that look unrealistically small
- Caveat (inferred, ours): Gaussian subtraction of CS disks may bias the ring residuals

## Reproducibility

- Data public (paper): Data cited by project ID 2016.1.00209.S, archive status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00209.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: tclean settings
- Missing: self-calibration parameters
- Missing: MCMC setup and priors
- Missing: RADMC-3D opacity and grid details
- Data volume (inferred): ~100-300 GB raw for three configurations
- Score (inferred): 5/5, Basic data and key formulae given but imaging and model fitting settings are largely missing.
- Rediscovery candidate: no, Imaging and RT fitting recipes are incomplete, though the Gaussian fits and mass formula are redoable.

## Links

- Method: (cite: Andrews2009ApJ...700.1502A) (Surface density parametrization)
- Method: (cite: Lim2016ApJ...826..153L) (Two-Gaussian disk fit procedure)
- Companion: (cite: Cieza2018MNRAS.474.4347C) (FUor disk sample for comparison)
- Companion: (cite: Takakuwa2017ApJ...837...86T) (L1551 NE comparison)
- Related: ALMA 2016.1.00209.S

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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 41,
  "rate": 0.539
 },
 "evidence_ok": true
}
```
