# Magnetically aligned dust and SiO maser polarisation in the envelope of the red supergiant VY Canis Majoris

`2017A&A...603A..92V` | Astronomy and Astrophysics 2017 | first author: Vlemmings, W. H. T. | arXiv: 1703.02084 | DOI: 10.1051/0004-6361/201730735

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: evolved_stars, stellar_physics
- Question: What do the linear and circular polarization of SiO lines and of the dust continuum from VY CMa reveal about the magnetic field and dust alignment in its envelope?  
  > "We analyse both linear and circular polarization and derive the magnetic field strength and structure, assuming the polarization of the lines originates from the Zeeman effect, and that of the dust originates from aligned dust grains." (abstract)
- Target **VY CMa**: coordinates _not stated_; z/distance 1.2 kpc  
  > "It is one of the largest red supergiant stars, located at a distance of 1.2 kpc (cite: Zhang2012)." (Introduction); distance from Zhang et al. 2012  
  > "It is one of the largest red supergiant stars, located at a distance of 1.2 kpc (cite: Zhang2012)." (Introduction)

## Data provenance

- ALMA projects: 2011.0.00011.S
- bands: Band 5 (163-211 GHz)  
  > "These observations are part of the ALMA Band 5 ($163-211$ GHz) Science Verification (SV) campaign." (Observations and data reduction)
- frequencies and spectral setup: five spws; spw 0 183.310 GHz, spw 1 183.884, spw 2 170.999, spw 3 172.481, spw 4 173.668 GHz  
  > "| 2 | 170.999 | 1.953 | 3.42 | 960 | 1.8750 | $^{28}$SiO $(J=4-3, v=2)$ |" (Table 1); "The observations were performed using five spectral windows (spws)." (Observations and data reduction)
- continuum bandwidth: 2.25 GHz aggregate line-free bandwidth, centered ~178 GHz  
  > "The resulting aggregate bandwidth was 2.25 GHz." (Results)
- arrays: 13 antennas used  
  > "A total of 13 antennas were used in the calibration and imaging." (Observations and data reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: lines ~0.8x0.3 arcsec; continuum ~0.5x0.2 arcsec  
  > "The continuum was imaged using a robust gridding weighting parameter of $-0.5$ resulting in a beam of $\sim0.5\times0.2\ensuremath{''}$." (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.1 mJy/beam; line rms ~3.8 mJy/beam (spw 3,4), ~1.4 mJy/beam (spw 2)  
  > "We achieved an rms noise of $0.1$ mJy beam$^{-1}$." (Observations and data reduction)
- time on source: _not stated_
- observing dates: 16 October 2016, ~6.4 hours  
  > "The VY CMa observations took place on 16 October 2016, starting at 05:45 UT and lasting for about 6.4 hours." (Observations and data reduction)
- pi or archival as stated: ALMA Band 5 Science Verification data  
  > "These observations are part of the ALMA Band 5 ($163-211$ GHz) Science Verification (SV) campaign." (Observations and data reduction)
- Line: 28SiO J=4-3, v=0 (173.688 GHz)
- Line: 28SiO J=4-3, v=1 (172.481 GHz)
- Line: 28SiO J=4-3, v=2 (171.275 GHz)
- Line: 29SiO J=4-3, v=0 (171.512 GHz)
- Line: 29SiO J=4-3, v=1 (170.328 GHz)
- Other facility **ALMA Band 7 and 9 (O'Gorman et al. 2015)**: continuum maps and spectral index used to compare with Band 5  
  > "In Fig. [1](#cont)(left) we show the Band 5 continuum overplotted on the ALMA Band 9 observations around 658 GHz." (Results)
- External data: Band 7/9 continuum structure and clump C size, dust analysis  
  > "Taking the dust mass derived from our measured fluxes, the size of clump C from OG+15, and assuming a gas-to-dust ratio of $100$" (Dust polarization of clump C) [from O'Gorman et al. 2015 (cite: OGorman2015)]
- External data: SiO Einstein A coefficients and energies  
  > "along with their transition energy and Einstein $A$ coefficients (cite: Muller2001)" (SiO emission) [from (cite: Muller2001)]

## Processing

### Calibration

- pipeline or manual: standard ALMA procedures with improvements for polarization, per Band 5 polarization memo  
  > "The polarization calibration was also performed following standard ALMA procedures, although with some improvements that we summarize here." (Observations and data reduction)
- casa version: CASA 4.7.0  
  > "The full calibration and imaging was performed in CASA 4.7.0" (Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: four iterations on a strong SiO maser channel in spw 3, applied to all spws  
  > "we performed four iterations of self-calibration on a strong channel of the SiO maser in spw 3. These solutions were applied to all the other spw." (Observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: lines: Briggs robust 0.5; continuum: robust -0.5  
  > "The imaging of the spectral lines was performed using Briggs weighting with a robustness parameter of $0.5$" (Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: line-free channels far from the 183 GHz water line, 2.25 GHz total  
  > "we only used line-free channels sufficiently far from the atmospheric H$_2$O line." (Dust continuum)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: lines ~0.8x0.3 arcsec; continuum ~0.5x0.2 arcsec  
  > "which resulted in a synthesized beam of $\sim0.8\times0.3\ensuremath{''}$" (Observations and data reduction)
- final rms: continuum 0.1 mJy/beam  
  > "We achieved an rms noise of $0.1$ mJy beam$^{-1}$." (Observations and data reduction)

### Inherited from earlier work

- Full calibration and imaging, polarization calibration details  
  > "is described in the Band 5 polarization calibration memo (cite: IMV2016) that was released with the data." (Observations and data reduction) [from Martí-Vidal et al. 2016 (cite: IMV2016)]
- Dust mass and temperature analysis for clump C  
  > "following the analysis from OG+15, the dust mass to $>1.2\times10^{-3}$ M$_\odot$ and decreases the dust temperature to $\sim100$ K." (Dust continuum) [from O'Gorman et al. 2015 (OG+15)]
- Maser polarization parameters for Zeeman vs non-Zeeman regime  
  > "Using the parameters from (cite: PerezSanchez2013), $g\Omega\sim150$ s$^{-1}$" (SiO maser polarization) [from (cite: PerezSanchez2013)]

### Not stated but needed to reproduce (our reading)

- Exact CASA tasks and parameters for imaging (cell size, image size, masks, deconvolver, niter)
- Line-free channel ranges for continuum
- Reference antenna and self-calibration solution intervals
- Method of two-component deconvolution for clump C and star fluxes
- Aperture used for the extended SiO v=0 spectra
- Debiasing of polarized intensity and thresholds

## Analysis recipe

1. **Calibrate and image full-Stokes data**: Standard ALMA calibration plus polarization calibration, self-cal on SiO maser, imaging in Stokes I,Q,U,V  
  > "We then reimaged all the spws at full spectral resolution and both the continuum and lines at full polarization, producing data cubes in Stokes I, Q, U, and V." (Observations and data reduction)
   - software: CASA
   - parameter: line robust 0.5; continuum robust -0.5  
  > "The continuum was imaged using a robust gridding weighting parameter of $-0.5$" (Observations and data reduction)
   - fitting: _not stated_
   - validation: Monte Carlo test of D-term and X-Y phase errors on Stokes V  
  > "we have generated one thousand sets of random D-terms for all the ALMA antennas, together with random X-Y phases for the reference antenna." (Appendix)
2. **Measure continuum fluxes and polarization**: Deconvolve star and clump C; derive fractional polarization and EVPA  
  > "Deconvolving the two components, we measure a total flux of $36\pm3$ mJy for the star and $94\pm9$ mJy for clump C." (Dust continuum)
   - fitting: _not stated_
   - validation: Compared with Band 7/9 convolved to Band 5 beam and spectral index  
  > "the distribution appears identical when the ALMA Band 7 and Band 9 observations (OG+15) are convolved with the Band 5 beam." (Dust continuum)
3. **Extract SiO spectra and polarization**: Spectra of Stokes I, linear fraction, EVPA and V at the peak intensity  
  > "Their spectra, in Stokes I, linear polarization fraction, EVPA, and Stokes V, are shown in Figs." (SiO emission)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive maser magnetic field from circular polarization**: Zeeman: B ≈1.3 Pc cosθ, and fit V = z B cosθ dI/dν  
  > "Our fit shown in Fig. [2](#line1)(right) then yields a magnetic field strength of $B\cos{\theta}\sim2.4$ G." (SiO maser polarization)
   - parameter: maser linewidth ~1 km/s; z≈1500 s^-1 G^-1  
  > "Here, the proportionality term $z=g\Omega\approx1500$ s$^{-1}$ \[Gauss\]$^{-1}$." (SiO maser polarization)
   - assumption: Zeeman origin of circular polarization; field reversals at Vlsr~15 and 30 km/s  
  > "if one assumes a magnetic field reversal at $V_{\rm lsr}\sim15$ and $30$ km s$^{-1}$" (SiO maser polarization)
   - fitting: V proportional to dI/dν fit  
  > "Assuming a general Zeeman splitting origin, the circular polarization spectrum $V$ is expected to be proportional to the derivative of the total intensity $I$, with a proportionality coefficient that depends on the magnetic field strength." (Discussion, SiO maser polarization)
   - validation: _not stated_
5. **Lower limit of field for grain alignment**: Compare Larmor timescale with gas-dust timescale (Hoang & Lazarian 2009)  
  > "For the dust alignment to be efficient, we find $B>13$ mG (or less if clump C is indeed severely depleted in gas)." (Dust polarization of clump C)
   - parameter: a=0.1 micron, s=0.5, Td=Tg=100 K, n_g≈9e9 cm^-3  
  > "we find $n_g\approx 9\times10^9$ cm$^{-3}$." (Dust polarization of clump C)
   - assumption: gas-to-dust ratio 100  
  > "assuming a gas-to-dust ratio of $100$" (Dust polarization of clump C)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0: calibration and imaging  
  > "The full calibration and imaging was performed in CASA 4.7.0" (Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Clump C flux at 178 GHz | 94 | 9 | mJy | 2 | $94\pm9$ mJy for clump C |
| Star flux at 178 GHz | 36 | 3 | mJy | 2 | we measure a total flux of $36\pm3$ mJy for the star |
| Continuum EVPA | 8 | 4 | deg | 2 | The average (non-rotated) electric vector position angle (EVPA) is $8\pm4^\circ$ (East of North) |
| Maximum continuum fractional polarization | ~3 | not stated | % | 2 | The maximum fractional polarization is $\sim3\%$. |
| Max linear polarization 29SiO v=1 | 28.6 | not stated | % | 3 | / 170.328$^{b}$  / $J=4-3, v=1$ / 1779    / $2.484\times          / 7.4       / 28.6              / 0.9                 / |
| Magnetic field from circular polarization, B/cosθ | 0.85 | not stated | G | 4 | We thus find $B/\cos{\theta} \approx 0.85$ G. |
| B cosθ from dI/dν fit | ~2.4 | not stated | G | 4 | $B\cos{\theta}\sim2.4$ G |
| Minimum field for dust alignment in clump C | >13 | not stated | mG | 5 | we find $B>13$ mG |
| Clump C dust mass | >1.2e-3 | not stated | Msun | 2 | the estimated clump C dust mass is $>1.2\times10^{-3}$ M$_\odot$ |

## Qualitative findings

- First detection of mm-wavelength dust polarization in the inner CSE of an evolved star, associated with clump C  
  > "This is the first detection of dust polarization at millimeter wavelengths in the inner circumstellar environment of an evolved star." (Conclusions)

## Claim tuples

- H: Is the continuum polarization from clump C due to magnetically aligned grains? | E: Compared scattering and aligned-grain emission scenarios and the RAT timescale | R: B>13 mG needed, far below masers fields (>100 mG) | F: Emission from aligned grains is the most likely origin, though self-scattering is not fully excluded | **partially**
- H: Does SiO maser linear polarization trace the magnetic field? | E: Evaluated gΩ vs R and Γ and EVPA rotation with velocity | R: gΩ>R, polarization mostly <15% | F: Magnetic field determines polarization; consistent with toroidal field | **supported**
- H: Is the circular polarization real and Zeeman? | E: Monte Carlo calibration-error simulation; V vs dI/dν | R: Spurious V <0.1%, smooth; observed V much more variable | F: Not caused by standard calibration errors; implies ~1-3 G | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Resonant scattering for maser circular polarization disfavoured since 29SiO and 28SiO show similar fractions  
  > "it appears that the resonant scattering does not contribute significantly to the maser transitions presented here." (SiO maser polarization)
- Alternative: Self-scattering of dust disfavoured but not ruled out  
  > "Although we show it to be unlikely, we cannot yet completely rule out a self-scattering origin of the polarization." (Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): Unknown instrumental effects in Stokes V cannot be ruled out; first ALMA circular polarization results  
  > "as these are the first reported ALMA circular polarization results, there is still the chance that they are affected by unkown instrumental issues." (Observations and data reduction)
- Limitation (authors): Higher resolution needed to map field structure  
  > "it is not possible to produce a more detailed map of the magnetic field with the current data." (Magnetic field morphology)
- Caveat (inferred, ours): Single epoch, low-resolution beam elongated along clump C direction
- Caveat (inferred, ours): Grain-alignment lower limit depends strongly on assumed grain size, density, gas-to-dust ratio
- Caveat (inferred, ours): Zeeman field estimates depend on unknown angle θ and saturation
- Caveat (inferred, ours): Thermal SiO circular polarization origin is unresolved

## Reproducibility

- Data public (paper): Data released as ALMA Band 5 SV with a calibration memo  
  > "described in the Band 5 polarization calibration memo (cite: IMV2016) that was released with the data." (Observations and data reduction)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masks)
- Missing: Details of two-component fit
- Missing: Calibration memo contents
- Missing: Aperture definitions for extended SiO emission
- Data volume (inferred): ~50-100 GB (5 spws, 6.4 h, full polarization)
- Score (inferred): 6/5, Public SV data and clear analytic formulas, but imaging and extraction details are largely deferred to a memo or unstated.
- Rediscovery candidate: yes, Public SV data, numeric results (fluxes, EVPA, polarization fractions, B estimates) with described recipe.

## Links

- Method: Martí-Vidal et al. 2016 (cite: IMV2016) (Band 5 polarization calibration of these data)
- Method: Hoang & Lazarian 2009 (cite: Hoang2009) (grain alignment lower limit on B)
- Companion: O'Gorman et al. 2015 (cite: OGorman2015) (ALMA Band 7 and 9 observations of VY CMa continuum)
- Companion: Humphreys et al. 2017 (cite: Humphreys2017) (APEX SiO polarization comparison)
- Related: ALMA Band 5 Science Verification

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00011.S"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00011.SV"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 44,
  "rate": 0.587
 },
 "evidence_ok": true
}
```
