# A second post-AGB nebula that contains gas in rotation and in expansion: ALMA maps of IW Carinae

`2017A&A...597L...5B` | Astronomy and Astrophysics 2017 | first author: Bujarrabal, V. | arXiv: 1612.03568 | DOI: 10.1051/0004-6361/201629317

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: Are rotation (Keplerian disk) and expansion (outflow) both present in the post-AGB nebula around IW Car, and what are its mass, central stellar mass and disk lifetime?  
  > "We aim to study the presence of both rotation and expansion in post-AGB nebulae, in particular around IW Car" (abstract)
- Target **IW Car**: coordinates _not stated_; z/distance 1 kpc  
  > "Following those authors we adopt a distance of 1 kpc for this source, but we stress that this value is uncertain." (1 Introduction); distance from adopted from earlier work (uncertain)  
  > "Following those authors we adopt a distance of 1 kpc for this source, but we stress that this value is uncertain." (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.00338.S
- bands: Band 7 (0.8 mm)  
  > "$\lambda$ = 0.8 mm, obtained with ALMA, receiver band 7." (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 12 to 1572 m, 42 antennas  
  > "with an array configuration of 42 antennas providing baselines between 12 and 1572 m." (2 Observations)
- angular resolution: ~0.17x0.17 arcsec (HPBW)  
  > "leading to a resolution (HPBW) of approximately 0$''$17$\times$0$''$ 17." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~110 minutes  
  > "In total, $\sim$ 110 minutes of acquisitions were obtained on source." (2 Observations)
- observing dates: July 26, 2015 (four tracks)  
  > "Four tracks were consecutively observed on July 26, 2015" (2 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (not stated)
- Line: 13CO J=3-2 (not stated)
- Other facility **APEX**: single-dish 12CO J=3-2 profile used to estimate flux loss  
  > "By comparison with the APEX single-dish profile (Bujarrabal et al. 2013b), we conclude that a small fraction of $\sim$ 25% of the flux has been filtered out" (2 Observations)
- External data: APEX single-dish 12CO J=3-2 profile  
  > "By comparison with the APEX single-dish profile (Bujarrabal et al. 2013b)" (2 Observations) [from Bujarrabal et al. 2013b]

## Processing

### Calibration

- pipeline or manual: Calibrated with CASA; then phase self-calibration in GILDAS  
  > "The data were first calibrated with the CASA software package." (2 Observations); "phase self-calibration was later performed using the compact continuum source as a reference with the GILDAS software package" (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0538-440 (0.91 Jy) and J1107-448 (0.43 Jy) at 345.8 GHz  
  > "J0538-440 and J1107-448 were set as absolute flux references (with 0.91 Jy and 0.43 Jy at 345.8 GHz respectively)." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: phase self-cal on compact continuum source, GILDAS  
  > "phase self-calibration was later performed using the compact continuum source as a reference with the GILDAS software package" (2 Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Image deconvolution was performed by using natural weighting" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Spectral resolution degraded from 0.21 to 0.85 km/s (12CO) and 0.66 km/s (13CO)  
  > "to a resolution of 0.85 km s$^{-1}$ for $^{12}$CO $J$=3$-$2 (which shows emission at larger velocities) and of 0.66 km s$^{-1}$ for $^{13}$CO $J$=3$-$2." (2 Observations)
- final beam: ~0.17x0.17 arcsec  
  > "leading to a resolution (HPBW) of approximately 0$''$17$\times$0$''$ 17." (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Model nebula built on properties derived for 89 Her and the Red Rectangle  
  > "we base our modeling on the properties we previously derived for those objects." (3.1 Simple modeling) [from Bujarrabal et al. 2007, 2013b, 2016]
- X(13CO) ~2e-5 adopted to compare with previous results  
  > "We adopt a relative abundance $X$($^{13}$CO) $\sim$ 2 10$^{-5}$, to ease the comparison with previous results on this object (Bujarrabal et al. 2013a)." (3.1 Simple modeling) [from Bujarrabal et al. 2013a]
- LTE justification  
  > "see further discussion in Bujarrabal et al. (2013b, 2016)." (3.1 Simple modeling) [from Bujarrabal et al. 2013b, 2016]

### Not stated but needed to reproduce (our reading)

- Model code and its source are not named or released
- Line-free channels and continuum subtraction method
- Image size, cell size, and final rms
- Rest frequencies and velocity reference
- Fitting procedure and goodness-of-fit metric (apparently by eye)
- Calculation of kinematical age and disk lifetime
- Disk width and shape details

## Analysis recipe

1. **Map the emission and measure morphology**: Channel maps and position-velocity diagrams along the equatorial direction (PA -15 deg)  
  > "Figs. 4 and 5 show position-velocity diagrams along the direction perpendicular to the outflow axis, which corresponds to the equatorial plane, at –15$^\circ$." (3 Results)
   - software: GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit simplified LTE model of CO emission**: Parametric nebula with Keplerian disk plus radial hourglass outflow, power-law density and temperature, compared to maps  
  > "The density and temperature ($n$ and $T$) are assumed to depend solely on the distance to the center and the equator with potential laws." (3.1 Simple modeling)
   - parameter: V(2e15 cm)=2.5 km/s; inclination ~45 deg (±15); X(13CO)~2e-5; X(12CO)~1e-4  
  > "We adopt a value of $\sim$ 45$^\circ$ ($\pm$ 15$^\circ$)." (3.1 Simple modeling)
   - assumption: LTE level populations; distance 1 kpc  
  > "We assume LTE populations for the involved rotational levels." (3.1 Simple modeling)
   - fitting: _not stated_
   - validation: Comparison of synthetic and observed channel maps and p-v diagrams  
  > "The model reproduces most of the observed features, but some problems are still present." (A.3 Comparison)
3. **Derive masses and disk lifetime**: Total mass from fitted model; lifetime from outflow kinematical time and mass-loss rate  
  > "we can derive the typical kinematical time required to form the outflow ($\sim$ 1000 yr) and the average mass-loss rate of the disk." (5 Summary and conclusions)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : initial calibration  
  > "The data were first calibrated with the CASA software package." (2 Observations)
- **GILDAS** : self-calibration and data analysis  
  > "which was also used in the following data analysis." (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Central stellar mass | 1 | +0.6/-0.4 | Msun | 2 | The uncertainty of the deduced central mass is 1$^{+0.6}_{-0.4}$ $M_{\mbox{\ensuremath{\odot}}}$. |
| Total nebular mass | 4e-3 | not stated | Msun | 2 | The total mass derived from our fitting is 4 10$^{-3}$ $M_{\mbox{\ensuremath{\odot}}}$ |
| Outflow axis position angle | ~75 | not stated | deg | 1 | is PA $\sim$ 75$^\circ$. |
| Disk future lifetime | ~8000 | 5000-10000 yr range | yr | 3 | We therefore estimate the disk’s future lifetime to be approximately 8000 yr. |
| Continuum flux | ~0.2 | not stated | Jy | 0 | Dust continuum emission was detected, with total flux $\sim$ 0.2 Jy |

## Qualitative findings

- Hourglass-like expanding outflow with axis perpendicular to a Keplerian rotating equatorial disk  
  > "expansion, which shows an hourglass-like structure with a symmetry axis perpendicular to the rotation plane" (abstract)

## Claim tuples

- H: IW Car hosts both a rotating disk and an expanding outflow | E: ALMA 12CO/13CO J=3-2 maps and p-v diagrams | R: Hourglass lobes and Keplerian pattern detected | F: Both components are present, the outflow likely extracted from the disk | **supported**
- H: Disk and outflow masses and central mass can be estimated | E: Simplified LTE model fit | R: Mtot~4e-3 Msun, outflow ~8x lighter than disk, M*~1 Msun | F: Disk lifetime ~5000-10000 yr | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Data S/N and resolution moderate and only two lines mapped, so a simplified model is used  
  > "Under these conditions, very detailed models, as those developed for the Red Rectangle, are not sensible and we only perform simplified modeling." (3.1 Simple modeling)
- Alternative: Constant velocity modulus, axial expansion and expansion parallel to the equator rejected  
  > "We can exclude some other simple cases, such as constant velocity modulus, expansion in the axial direction, and expansion parallel to the equator" (A.2 Uncertainties)
- How they decided it was enough: _not stated_
- Limitation (authors): ~25% flux filtered out, model overpredicts faint extended emission  
  > "a small fraction of $\sim$ 25% of the flux has been filtered out in the maps of $^{12}$CO $J$=3$-$2." (2 Observations)
- Limitation (authors): Inclination poorly determined  
  > "The axis inclination with respect to the plane of the sky is poorly determined" (3.1 Simple modeling)
- Caveat (inferred, ours): Mass depends mainly on assumed X(13CO) and distance of 1 kpc
- Caveat (inferred, ours): No formal fit or error analysis; uncertainties qualitative
- Caveat (inferred, ours): Lifetime estimate relies on outflow being extracted from disk

## Reproducibility

- Data public (paper): Dataset ADS/JAO.ALMA#2013.1.00338.S cited  
  > "We made use of the ALMA dataset ADS/JAO.ALMA#2013.1.00338.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Model code and exact parameter files
- Missing: Imaging parameters and line-free channels
- Missing: Fit criterion
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 4/5, Data public but model is bespoke, unreleased and fit by eye; short letter with limited processing details.
- Rediscovery candidate: no, Model code unreleased and recipe incomplete.

## Links

- Method: Bujarrabal et al. 2016 (detailed Red Rectangle model on which this model is based)
- Companion: Bujarrabal et al. 2013a (single-dish CO study of IW Car)

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
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 33,
  "rate": 0.508
 },
 "evidence_ok": true
}
```
