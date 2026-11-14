# A Radially Broad Collisional Cascade in the Debris Disk of γ Ophiuchi Observed by JWST

`2026ApJ..1004..182H` | The Astrophysical Journal 2026 | first author: Han, Yinuo | arXiv: 2601.15285 | DOI: 10.3847/1538-4357/ae6ef7

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: debris_disks
- Question: Is the radially broad debris disk of gamma Oph a steady-state collisional cascade with one grain size distribution (JWST/MIRI vs ALMA), or shaped by PR drag like Vega and Fomalhaut, and is it asymmetric?  
  > "We recently imaged the debris disk of $\gamma$ Oph with JWST/MIRI to test whether the PR drag scenario in Vega and Fomalhaut applies to $\gamma$ Oph’s radially broad belt." (Introduction)
- Target **gamma Oph (HD 161868)**: coordinates _not stated_; z/distance 29.7 pc  
  > "At a distance of 29.7 pc and an age of $300 \pm 200$ Myr ((cite: Vican2012; Gaspar2016; Trevor2015)), $\gamma$ Oph is of a similar spectral type (A1V)" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2022.1.00338.L
- bands: Band 7 (0.87 mm), ARKS programme  
  > "Here we focus on the latter, which were carried out in Band 7 (0.87  mm) at higher resolution (15 au) than the REASONS observations." (5 Discussion)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 15 au  
  > "Band 7 (0.87  mm) at higher resolution (15 au) than the REASONS observations." (5 Discussion)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **JWST/MIRI**: F1500W and F2550W imaging of gamma Oph, programme 5709, plus zeta Ser PSF star and background observations  
  > "We observed $\gamma$ Oph with the JWST MIRI Imager on 13 Aug 2024 UT (programme ID 5709, (cite: Han2024_JWST_GamOph))." (2 Observations)
- Other facility **Spitzer**: 24 micron imaging showing extended disk (prior, literature)  
  > "*Spitzer* observations at 24 $\mu$m show the disk to be greatly extended, reaching 265 au" (Introduction)
- External data: ARKS ALMA Band 7 observations/images of gamma Oph; Gaussian ring fit (PA 57.6, i 66.1; centre 121 au, sigma 57 au)  
  > "The ALMA position angle is measured to be $57.6 \pm 1.6^\circ$ and the inclination $66.1 \pm 1.5^\circ$ by fitting a Gaussian ring model (cite: Marino2025)." (5.3.1 Collisional cascade) [from (cite: Marino2025)]
- External data: ALMA radial profiles via rave and frank and power-law edge indices (1.0 inner, -3.7 outer)  
  > "the ALMA inner edge under the same parametrisation finds the power law index to be $1.0 \pm 0.1$ for the inner edge and $-3.7 \pm 0.8$ for the outer edge (cite: Han2025b)" (5.3.2 Inner and outer edges) [from (cite: Han2025b)]
- External data: Grain composition parameters from Fomalhaut MIRI fits (q_sil=0.4, q_ice=1.0, p=0.7)  
  > "we assumed that the grains are described by $q_\mathrm{sil} = 0.4$, $q_\mathrm{ice} = 1.0$ and $p = 0.7$" (4.2 Parametric modelling) [from (cite: Sommer2025)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
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

- ALMA modelling details (rave, frank profile fits to ARKS data)  
  > "Details of the ALMA modelling are described in (cite: Han2025b)." (5.3 Disk structure across wavelength) [from (cite: Han2025b)]
- Dust optical property code astrodust_optprops and grain composition  
  > "We modelled the optical properties of dust grains using the `astrodust_optprops` code (cite: Sommer2025)" (4.2 Parametric modelling) [from (cite: Sommer2025)]
- Dither-by-dither PSF subtraction approach  
  > "before combining the subtracted disk image at each dither using the Stage 3 pipeline (cite: Su2024)." (3 Data reduction) [from (cite: Su2024)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, imaging parameters and the ARKS image products used (only referenced to other papers)
- Details of the SED data points and stellar models (only in figure legend)
- Emcee priors and burn-in length
- How the ALMA rave fit settings (inclination, PA, annuli) were chosen

## Analysis recipe

1. **Nonparametric radial profile at 25 micron**: rave fit to PSF-subtracted F2550W image over a 4D grid of theta, i, F*, h with 12 annuli; best grid point theta=59.0, i=64.5, h=0.1, F*=240 mJy  
  > "the best combination of parameters are $\theta = 59.0^\circ$, $I = 64.5^\circ$, $F_* = 240$ mJy and $h = 0.1$" (4.1 Nonparametric modelling at 25 micron)
   - software: rave
   - assumption: azimuthally symmetric, optically thin, Gaussian vertical profile with constant aspect ratio  
  > "assuming that the disk is azimuthally symmetric and optically thin" (4.1 Nonparametric modelling at 25 micron)
   - fitting: _not stated_
   - validation: squared residuals; repeated 100 times with randomised annuli boundaries  
  > "The placement of annuli boundaries are randomised to marginalise over their effect on the fitted profile, and the fit is repeated 100 times." (4.1 Nonparametric modelling at 25 micron)
2. **Parametric optical depth fits (Gaussian, two Gaussians, double power law) with and without stellocentric offset**: MCMC fit of PSF-convolved model images to F2550W and F1500W data  
  > "using 64 walkers and running the chain for at least 5,000 steps after burn-in" (4.2.1 Gaussian)
   - software: emcee, astrodust_optprops
   - assumption: gamma=3.5, s_min=15 micron, s_max=1 m, L=24.4 Lsun, M=2.11 Msun  
  > "The minimum grain size (i.e., diameter) was assumed to be $s_\mathrm{min} = 15\,\mu$m" (4.2 Parametric modelling)
   - fitting: emcee, independent Gaussian pixel noise equal to measured rms; 16/50/84 percentiles  
  > "The noise in each pixel was assumed to be independent and Gaussian with a standard deviation equal to the rms noise described in Section 3" (4.2.1 Gaussian)
   - validation: reduced chi-squared comparison  
  > "we base the comparison directly on the reduced $\chi^2$" (4.2.1 Gaussian)
3. **Compare MIRI and ALMA radial profiles**: Convert rave surface brightness profiles between wavelengths using a common steady-state size distribution; compare with ALMA rave and frank profiles; model SED  
  > "We find that a steady-state collisional cascade with $\gamma = 3.5$ (cite: Dohnanyi1969; Wyatt2008; Hughes2018) and a minimum grain size of 15 $\mu$m is consistent with the 25 $\mu$m and 0.87 mm surface brightness profiles that we observe." (5.3.1 Collisional cascade)
   - software: rave, frank
   - fitting: _not stated_
   - validation: no vertical scaling needed between profiles  
  > "No vertical scaling is applied between profiles within each panel." (5.3.1 Collisional cascade)
4. **Planet mass constraints from gaps and secular forcing**: Inject cleared gaps into rave profile to find widest undetectable gap; chaotic zone width, clearing and secular timescales, eccentricity relation  
  > "To test the widest gap that could hide in the disk while remaining undetected, we simulated observations using the `rave` radial profile" (5.2 Planet constraints)
   - software: rave
   - assumption: age 300 Myr, a_disk=50 au, forced eccentricity 0.03  
  > "we set $a_\mathrm{disk} = 50$ au where the surface brightness asymmetry peaks" (5.2 Planet constraints)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **rave** : nonparametric deconvolved radial profile fitting of MIRI and ALMA images  
  > "We nonparametrically fitted the PSF-subtracted (assuming SED stellar flux) F2500W image with the `rave` package" (4.1)
- **emcee** : MCMC sampling of parametric models  
  > "implemented with the `emcee` package (cite: emcee)" (4.2.1 Gaussian)
- **JWST pipeline** 1.18.0: MIRI data reduction, CRDS jwst_1364.pmap  
  > "We processed the MIRI observations with the JWST pipeline version 1.18.0" (3 Data reduction)
- **astrodust_optprops** : dust optical properties, temperatures, beta  
  > "We modelled the optical properties of dust grains using the `astrodust_optprops` code (cite: Sommer2025)" (4.2)
- **frank** : ALMA visibility-based radial profile for comparison  
  > "We also include the ALMA nonparametric profile fitted with the `frank` method" (5.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Best-fit disk offset deprojected | 1.41 | 0.01 | au | 2 | corresponding to a $1.41 \pm 0.01$ au offset along $16.2 \pm 0.8^\circ$ clockwise from the ascending (western) node |
| Disk eccentricity | ~0.03 | not stated | dimensionless | 2 | such an offset corresponds to an eccentricity of $\sim$0.03 |
| MIRI inclination (power-law offset model) | 63.29 | 0.02 | deg | 2 | slightly larger than the inclination of $63.29 \pm 0.02^\circ$ |
| Gaussian optical depth peak (25 micron, offset) | 99.99 | +0.09/-0.10 | au | 2 | $99.99^{+0.09}_{-0.10}$ |
| Power-law edge indices (inner, outer) | 1.472, -0.72 | 0.002, 0.02 | dimensionless | 2 | $1.472^{+0.002}_{-0.002}$ |
| Unresolved inner dust blackbody radius | ~8 | not stated | au | 2 | The corresponding radius with such a blackbody equilibrium temperature is $\sim$8 au. |
| Largest bodies for MMSN erosion to r^(7/3) | ~150 | not stated | m | 3 | predicts the largest bodies in the disk to be approximately 150 m in diameter |

## Qualitative findings

- MIRI disk is smooth and radially broad with no gaps or rings; extends to ~250 au at 25.5 micron and ~150 au at 15 micron  
  > "finding a smooth and radially broad disk with inner emission extending to the star and outer emission detected out to approximately 250 au at 25.5 $\mu$m and 150 au at 15 $\mu$m" (Conclusions)

## Claim tuples

- H: Is gamma Oph's broad disk a single steady-state collisional cascade rather than PR-drag displaced dust? | E: Convert MIRI 25 micron and ALMA 0.87 mm rave profiles assuming the same optical properties and compare | R: gamma=3.5, s_min=15 micron cascade is consistent with both profiles without vertical scaling | F: Disk is populated by a radially broad planetesimal belt with in-situ dust | **supported**
- H: Is the disk asymmetric? | E: Fit axisymmetric models with a star-disk offset | R: Offset of ~1.4 au improves residuals; eccentricity ~0.03 | F: Disk appears asymmetric, consistent with a small forced eccentricity | **supported**
- H: What perturbers could be hidden given no gaps? | E: Hidden-gap, clearing and secular timescale constraints | R: Giant planets up to 10 MJup outside 10 au allowed; larger companions within 10 au | F: Mildly eccentric planet or companion could induce the eccentricity without a gap | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: PR drag inner dust as in Vega/Fomalhaut is not required; may be weakened by shorter collisional timescale  
  > "without the need to invoke PR drag" (5.3.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Aspect ratio poorly constrained; uncertainties large in inner disk and outer edge; small uncertainties exclude PSF-subtraction systematics  
  > "suggesting that the aspect ratio is in practice not tightly constrained" (5.1)
- Caveat (inferred, ours): Offset interpretation degenerate with azimuthal emission asymmetry; not tested
- Caveat (inferred, ours): Fixed dust composition from Fomalhaut and assumed gamma/s_min
- Caveat (inferred, ours): Marginal 6 sigma ALMA asymmetry detectability
- Caveat (inferred, ours): MIRI inclination differs from ALMA

## Reproducibility

- Data public (paper): JWST data available from MAST; ALMA data credited as 2022.1.00338.L  
  > "The data described here may be obtained from the MAST archive" (Acknowledgements)
- Products in archive: _not stated_
- Missing: ALMA ARKS imaging products and settings
- Missing: rave code settings for ALMA
- Missing: SED data points
- Data volume (inferred): ~1-5 GB (JWST MIRI) plus ALMA images
- Score (inferred): 3/5, JWST pipeline and models are well described, but ALMA is reused from companion papers and code is not released.
- Rediscovery candidate: no, Main analysis is JWST-based; ALMA part relies on companion-paper products.

## Links

- Method: (cite: Han2022) (rave radial profile fitting)
- Method: (cite: Sommer2025) (dust optical property code and grain composition)
- Companion: (cite: Marino2025) (ARKS survey ALMA data)
- Companion: (cite: Han2025b) (ALMA radial profile modelling)
- Related: ARKS
- Related: REASONS

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
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
  "facts": 74,
  "stated": 32,
  "rate": 0.432
 },
 "evidence_ok": true
}
```
