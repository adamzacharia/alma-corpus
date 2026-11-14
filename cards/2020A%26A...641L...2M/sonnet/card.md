# All good things come in threes: the third image of the lensed quasar PKS 1830-211

`2020A&A...641L...2M` | Astronomy and Astrophysics 2020 | first author: Muller, S. | arXiv: 2008.08395 | DOI: 10.1051/0004-6361/202038978

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, cosmology
- Question: Can ALMA high-resolution, high-dynamic-range continuum imaging unambiguously identify the faint third (central) lensed image of PKS 1830-211 and thereby refine the lens model?  
  > "allowed us to unambiguously identify the third image of PKS 1830$-$211 and refine the lens model of the system." (1 Introduction)
- Target **PKS 1830-211**: coordinates _not stated_; z/distance quasar z=2.5 (z_S=2.507); lens z=0.89 (z_L=0.88582)  
  > "It consists of a radio-loud quasar at $z=2.5$ ((cite: lid99)), a foreground lens in the form of a nearly face-on $z=0.89$ spiral galaxy" (1 Introduction); distance from Lidman et al. 1999 (source); Wiklind & Combes 1996 (lens)  
  > "It consists of a radio-loud quasar at $z=2.5$ ((cite: lid99)), a foreground lens in the form of a nearly face-on $z=0.89$ spiral galaxy" (1 Introduction)

## Data provenance

- ALMA projects: 2018.1.00051.S
- bands: Bands 4, 5, 6, 7  
  > "in bands 4 ($\sim 150$ GHz) and 6 ($\sim 230$ GHz), and on 2019 July 28 in bands 5 ($\sim 180$ GHz) and 7 ($\sim 280$ GHz)." (2 Observations)
- frequencies and spectral setup: 4 spectral windows of 1.875 GHz each, resolution ~0.5-1 MHz  
  > "The correlator was configured to cover four independent spectral windows, each of 1.875 GHz in width, with a spectral resolution $\sim 0.5$–1 MHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Extended configuration, longest baselines 8-14 km  
  > "The array was in an extended configuration, with longest baselines up to 8–14 km depending on the date." (2 Observations)
- baselines: _not stated_
- angular resolution: Synthesized beam 60 to 20 mas  
  > "This resulted in a synthesized beam of between 60 mas and 20 mas." (2 Observations)
- max recoverable scale: LRAS 1.2-1.8 arcsec, larger than the Einstein ring  
  > "LRAS: largest recoverable angular scale, calculated as $c/(2\nu B_{\rm min})$." (Table 1)
- sensitivity: _not stated_
- time on source: B4 7:36, B5 17:14, B6 24:52, B7 18:49 min  
  > "| B6 | 230.89 | 2019 Jul 11 | 44 | 111 | 12.6 | 1.2 | 24:52 | $37.5 \times 23.2$ / 70.0 | 1.2 |" (Table 1)
- observing dates: 2019 July 10, 11 and 28  
  > "Our ALMA observations of PKS 1830$-$211 were carried out on 2019 July 10 and 11" (2 Observations)
- pi or archival as stated: _not stated_
- External data: VLA 15 GHz image used as visual guide for the extended source model  
  > "using the VLA-15 GHz image of (cite: sub90) (see Fig. [3](#fig:finalmodels)c) as a visual guide" (3 Revising the lens model) [from Subrahmanyan et al. 1990 (cite: sub90)]
- External data: H0 values 67.4 (Planck) and 73.3 (lens modeling)  
  > "(1) $H_0$ measurements from (cite: Planck18) and (cite: won20), respectively." (Table 3 notes) [from Planck18; Wong et al. 2020]
- External data: Source redshift 2.507 and lens redshift 0.88582  
  > "(2) (cite: lid99). (3) (cite: wik96)." (Table 3 notes) [from Lidman et al. 1999; Wiklind & Combes 1996]

## Processing

### Calibration

- pipeline or manual: Standard CASA calibration procedure  
  > "The data calibration was done within the CASA[^1] package, following a standard procedure." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1924-292, also bandpass calibrator  
  > "observations of the bright quasar J 1924$-$292 (3.8 to 2.5 Jy with increasing frequency), which was also used for the absolute flux calibration." (2 Observations)
- flux scale uncertainty: better than 5% bands 4,5,6; better than 10% band 7  
  > "the flux accuracy is better than 5% at bands 4, 5, and 6, and better than 10% at band 7" (2 Observations)
- self calibration: Phase-only self-cal on continuum with 6 s solint; dynamic range improved 2-3x to >~1000  
  > "applying phase-only gain corrections at each 6 s integration." (2 Observations)

### Imaging

- task: _not stated_
- deconvolver: Högbom CLEAN, multi-frequency synthesis, per band  
  > "produced for each band separately, from a Högbom-Clean multi-frequency synthesis deconvolution of the interferometric visibilities, with a pixel size of 5 mas." (2 Observations)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 5 mas  
  > "with a pixel size of 5 mas." (2 Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Absorption features flagged to image continuum  
  > "All the absorption features were flagged to image the continuum emission." (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: B4 46.9x37.7, B5 56.4x51.6, B6 37.5x23.2, B7 34.3x32.9 mas  
  > "| B4 | 154.89 | 2019 Jul 10 | 45 | 138 | 13.9 | 2.1 | 7:36 | $46.9 \times 37.7$ / 61.5 | 1.4 |" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Softened isothermal ellipsoidal lens mass model  
  > "A softened isothermal ellipsoidal model was adopted for the lens mass distribution (e.g., (cite: kor94) and see App. [7.1](#app:lens))." (3 Revising the lens model) [from Kormann et al. 1994 (cite: kor94)]
- Chi-square minimization in source and image plane  
  > "The best-fit model was obtained by minimizing the $\chi$-square in the source and image plane, successively (see (cite: kee01))." (3 Revising the lens model) [from Keeton 2001 (cite: kee01)]

### Not stated but needed to reproduce (our reading)

- Robust/weighting and clean threshold/masks for each band
- CASA version
- Self-calibration reference model and image used
- Method and software for measuring image positions/fluxes (point-source fits in uv or image plane)
- Details of global spectral-index fit
- MCMC settings (sampler, priors, chains) for the corner plots
- Flagging details and which channels were flagged

## Analysis recipe

1. **Calibrate and self-calibrate**: Standard CASA calibration then phase-only self-calibration on continuum at 6 s  
  > "the visibility phases were furthermore self-calibrated on the continuum of PKS 1830$-$211, applying phase-only gain corrections at each 6 s integration." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Dynamic range improved by factor 2-3 to >~1000  
  > "the dynamic range (i.e., the ratio of peak flux to rms noise level in the image) improved by a factor of two to three after self-calibration" (2 Observations)
2. **Image continuum per band**: Högbom CLEAN MFS, 5 mas pixels  
  > "from a Högbom-Clean multi-frequency synthesis deconvolution of the interferometric visibilities" (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure positions, fluxes and spectral indices of A, B, C**: Global fit of F = F0 (nu/nu0)^alpha across bands  
  > "The spectral index is defined as $F = F_0 \times (\nu / \nu_0)^{\alpha}$." (Table 2 notes)
   - fitting: _not stated_
   - validation: Similar spectral index and flux ratio of C vs A and B; position consistent with VLA feature E  
  > "its flux ratio relative to images A and B, and its similar spectral index point toward its identification as the expected third, de-magnified lensed image" (3 Results)
4. **Fit point-source lens model**: Softened isothermal ellipsoid fit to three image positions and flux ratios; image C position as initial lens center  
  > "We took the position of the third image as an initial guess for the center of the lens, because both are expected to be very close." (4 Revising the lens model)
   - software: GravLens
   - parameter: Eight free parameters: source position, lens position, mass scale, softening length, ellipticity, position angle  
  > "the lens model has therefore eight free parameters" (4 Revising the lens model)
   - assumption: Flat universe Omega_m=0.3, Omega_L=0.7; H0 = 67.4 or 73.3; second absorber at z=0.19 neglected  
  > "with a flat Universe defined by $\Omega_m=0.3$ and $\Omega_{\Lambda}=0.7$" (Appendix A.1)
   - fitting: Chi-square minimization in source and image plane; Monte Carlo degeneracy corner plots  
  > "The outcome of the fit is shown in the form of Monte-Carlo degeneracy parameter plots ("corner plots")" (4 Revising the lens model)
   - validation: _not stated_
5. **Model extensions and Einstein ring with extended source**: Add second point source at extension positions; then Sérsic n=1 profile with half-light radius 55 mas, compared visually to VLA 15 GHz  
  > "a 1D Sérsic profile with Sérsic index $n=1$ (i.e., an exponential intensity distribution profile), centered at the same position as the second point-like source above, and with a half-light radius of 55 mas" (4 Revising the lens model)
   - software: GravLens
   - fitting: Manual trials, no formal fit  
  > "After several trials varying its positions, size, and Sérsic index" (4 Revising the lens model)
   - validation: Visual match to VLA image  
  > "a remarkable match between the VLA and GravLens model images" (4 Revising the lens model)

## Software

- **CASA** : Calibration and imaging  
  > "The data calibration was done within the CASA[^1] package" (2 Observations)
- **GravLens** : Lens modeling  
  > "we used the GravLens code[^3] ((cite: kee01)) in successive steps" (4 Revising the lens model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Flux density of image C at 300 GHz | 12.6 | 1.6 | mJy | 3 | / C / $-500.1 \pm 2.1$ / $-459.6 \pm 1.6$ / $12.6 \pm 1.6$ / $0.0071 \pm 0.0009$ / $-0.53 \pm 0.28$ / |
| Flux ratio C/A | 0.0071 | 0.0009 | dimensionless | 3 | / C / $-500.1 \pm 2.1$ / $-459.6 \pm 1.6$ / $12.6 \pm 1.6$ / $0.0071 \pm 0.0009$ / $-0.53 \pm 0.28$ / |
| Image C offset from A (RA, Dec) | -500.1, -459.6 | 2.1, 1.6 | mas | 3 | / C / $-500.1 \pm 2.1$ / $-459.6 \pm 1.6$ / $12.6 \pm 1.6$ / $0.0071 \pm 0.0009$ / $-0.53 \pm 0.28$ / |
| Spectral index of image A | -0.698 | 0.045 | dimensionless | 3 | / A / 0.0 / 0.0 / $1776 \pm 36$ / 1.0 / $-0.698 \pm 0.045$ / |
| Spectral index of A extension | -1.28 | 0.15 | dimensionless | 3 | we estimate spectral indices $\alpha = -1.28 \pm 0.15$ and $-1.18 \pm 0.15$ toward A and B extensions, respectively |
| Spectral index of B extension | -1.18 | 0.15 | dimensionless | 3 | we estimate spectral indices $\alpha = -1.28 \pm 0.15$ and $-1.18 \pm 0.15$ toward A and B extensions, respectively |
| Lens ellipticity e | 0.19 | 0.02 | dimensionless | 4 | / / Ellipticity $e$ / $0.19 \pm 0.02$ / \[0.0; 0.3\] / / |
| Time delay t_AB | 28.6 (H0=67.4); 26.3 (H0=73.3) | not stated | days | 4 | / Time delay / $t_{\rm AB}$ (d) / 28.6; 26.3 / / \(11\) / |
| Time delay t_AC | 33.7; 31.0 | not stated | days | 4 | / / $t_{\rm AC}$ (d) / 33.7; 31.0 / / \(11\) / |
| Magnifications A, B, C | 3.1, -2.9, 0.022 | not stated | dimensionless | 4 | / / $\mu_{\rm C}$ / $0.022$ / / / |
| Core-jet separation | 55 (PA 107 deg) | not stated | mas | 5 | a separation of 55 mas ($\sim 0.5$ kpc at the redshift of the quasar) and a position angle ${PA}=107^\circ$ |
| Enclosed mass within 1 arcsec diameter | ~4e11 | not stated | Msun | 4 | which we find to be $\sim 4 \times 10^{11}$ M$_\odot$ within a region of $1\ensuremath{''}$ in diameter |

## Qualitative findings

- Extensions have steeper spectral indices than A, B, C, indicating a different (jet) component.  
  > "These spectral indices are significantly steeper than those of the point-like images A, B, and C" (3 Results)

## Claim tuples

- H: Is the faint component near image B the third lensed image of the quasar? | E: Multi-band ALMA continuum imaging at 20-60 mas resolution | R: Faint point source C ~0.3 arcsec from B, flux ratio ~0.7% of A, spectral index similar to A and B | F: C is the third de-magnified image; lens center coincides with it | **supported**
- H: Can a simple core-jet source reproduce ALMA and VLA images? | E: GravLens modeling with point core plus Sérsic n=1 jet | R: Model reproduces three images, extensions, Einstein ring and bridge feature | F: Core-jet morphology with ~55 mas separation | **supported**
- H: Can the lens model constrain time delays and H0? | E: Modeling with two H0 values | R: t_AB ~26-29 d, t_AC ~31-34 d | F: Precise delay measurement could constrain H0 to a few percent; no H0 constraint attempted | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Second absorber at z=0.19 neglected as its lensing effect is negligible (kappa'<1).  
  > "We find that its lensing effect is negligible at the location of both images A and B" (Appendix A.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Goal was a plausible model, not ultimate modeling; no H0 constraint because time delay is uncertain.  
  > "Our goal was not to achieve the ultimate modeling of the system, but to build one plausible model" (4 Revising the lens model)
- Caveat (inferred, ours): Quasar variability and time delays between epochs/bands affect flux ratios and joint spectral index fit
- Caveat (inferred, ours): Extended source model tuned by eye with no goodness-of-fit
- Caveat (inferred, ours): Single isothermal ellipsoid with no external shear or line-of-sight structure
- Caveat (inferred, ours): Lens parameter uncertainties may be underestimated given only three image positions

## Reproducibility

- Data public (paper): ALMA project data acknowledged; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00051.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters (weighting, masks, thresholds)
- Missing: Method for extracting image positions and fluxes
- Missing: MCMC details
- Missing: Source model fitting for the extended jet is manual
- Data volume (inferred): ~100-500 GB raw for four long-baseline execution blocks
- Score (inferred): 3/5, Data identified and calibration outline given, but imaging and fitting details are sparse.
- Rediscovery candidate: no, Imaging and measurement settings are underspecified and the lens model includes manual tuning.

## Links

- Method: Keeton 2001 (cite: kee01) (GravLens code)
- Method: Kormann et al. 1994 (cite: kor94) (Softened isothermal ellipsoid)
- Companion: Subrahmanyan et al. 1990 (cite: sub90) (VLA 15 GHz image of the Einstein ring)

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
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
  "facts": 70,
  "stated": 41,
  "rate": 0.586
 },
 "evidence_ok": true
}
```
