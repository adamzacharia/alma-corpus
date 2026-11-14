# Rotation of the asymptotic giant branch star R Doradus

`2018A&A...613L...4V` | Astronomy and Astrophysics 2018 | first author: Vlemmings, W. H. T. | arXiv: 1804.04709 | DOI: 10.1051/0004-6361/201832929

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, stellar_physics
- Question: Does the extended atmosphere of the AGB star R Dor rotate, and what is its angular rotation velocity and origin?  
  > "Here we present the first direct detection of rotation of the extended atmosphere of an AGB star, R Dor." (Introduction)
- Target **R Dor**: coordinates _not stated_; z/distance 59 pc  
  > "reaches the measured temperature ($\sim2100$ K) and radius ($\approx 400$ $R_\odot$ at 59 pc)" (Discussion); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00004.S
- bands: Band 6 mainly; Band 4 confirms  
  > "Here we mainly focus on observations in Band 6, although Band 4 observations" (2 Observations and data reduction)
- frequencies and spectral setup: four spws of 1920 channels, centred 213.97, 215.97, 226.29, 228.21 GHz; ~1.4 km/s resolution  
  > "were performed using four spectral windows (spws) of 1920 channels each. The velocity resolution was $\sim1.4$ km s$^{-1}$ and the spws were centered on 213.97, 215.97, 226.29, and 228.21 GHz." (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: one of the longest baseline configurations  
  > "Since the data were taken in one of the longest baseline configurations" (2 Observations and data reduction)
- baselines: _not stated_
- angular resolution: typical beam 30x42 mas  
  > "This resulted in a typical beam size of $30\times42~{\rm mas}$" (2 Observations and data reduction)
- max recoverable scale: ~0.35 arcsec  
  > "the maximum recoverable scale is $\sim0.35\ensuremath{''}$" (2 Observations and data reduction)
- sensitivity: ~2.5 mJy/beam per channel  
  > "a typical channel rms noise" (2 Observations and data reduction)
- time on source: _not stated_
- observing dates: 25 September 2017  
  > "The observations took place on 25 September 2017," (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: SiO v=3, J=5-4 (212.5826 GHz)
- Line: SO2 16(3,13)-16(2,14) (214.68939 GHz)
- Line: 29SiO v=1, J=5-4 (212.90515 GHz)
- External data: Stellar evolution model of 1.5 Msun star with 50 km/s initial rotation, used for comparison  
  > "which use the same code and physics as explained in (cite: GS2014)" (5.1 The origin of the rotation) [from (cite: GS2014)]

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
- weighting robust: Briggs robust weighting (value not given)  
  > "The line image products were created using Briggs robust weighting." (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum subtracted before line imaging  
  > "The continuum emission was subtracted before the subsequent line imaging." (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Calibration and self-calibration details deferred  
  > "Further details of the calibration and self-calibration will be presented in a forthcoming paper (Vlemmings et al., in prep.)." (2 Observations and data reduction) [from Vlemmings et al., in prep.]
- uv-fitting procedure for continuum size  
  > "Using the uv-fitting procedure decribed in (cite: Vlemmings2017)" (2 Observations and data reduction) [from (cite: Vlemmings2017)]
- Solid-body rotation shell velocity model  
  > "The rotation velocity for solid-body rotation including possible expansion is given by (cite: Kervella2018)" (3 Results) [from (cite: Kervella2018)]

### Not stated but needed to reproduce (our reading)

- Briggs robust value, cell and image size
- CASA version and calibration details
- Line-free channels for continuum subtraction
- Aperture used for spectra
- Stellar centre position and method for shell fit initialisation

## Analysis recipe

1. **Measure continuum size**: uv-fitting of stellar continuum  
  > "we have determined the size of R Dor at 214 GHz to be $(62.4\pm0.1)\times(61.8\pm0.1)~{\rm mas}$" (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit line profiles per pixel**: specfit per pixel; single Lorentzian, two Gaussians for 29SiO v=1  
  > "we fit the spectra from each image pixel using the CASA task *specfit*." (3 Results)
   - software: CASA specfit
   - fitting: Lorentzian profile  
  > "a single Lorentzian profile accurately describes the majority of the spectral lines" (3 Results)
   - validation: residual spectra and maps inspected  
  > "we present the line spectra, for the SiO $v=3$, SO$_2$, and $^{29}$SiO $v=1$ lines, taken in an aperture covering the dominant part of the line emission region, and the resulting fit and residual spectra." (Results)
3. **Determine shell radius**: fit shell of emission to each channel; weighted average of four central channels  
  > "We then take $R_{\rm shell}$ to be the weighted average of the four central emission channels." (3 Results)
   - software: immultifit
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit solid-body rotation to velocity field**: chi2 fit of rotating shell model to central-velocity maps  
  > "The velocity field was fit, using a $\chi^2-$analysis, to the velocity field produced by the rotation of a shell with solid-body rotation." (3 Results)
   - parameter: pixels with fitted amplitude at least 3x fit error  
  > "We limit the pixels included to those where the fitted amplitudes are at least three times the associated fit error." (3 Results)
   - assumption: solid-body rotation per line  
  > "Although the approximation of solid-body rotation for each individual molecular line might not be fully correct" (3 Results)
   - fitting: chi2 minimisation  
  > "The velocity field was fit, using a $\chi^2-$analysis, to the velocity field produced by the rotation of a shell with solid-body rotation." (Results)
   - validation: SiO v=3 and SO2 angular velocities consistent within <1.5 sigma  
  > "yield results for the angular rotation velocity that are consistent within $<1.5\sigma$" (3 Results)

## Software

- **CASA** : specfit line fitting  
  > "using the CASA task *specfit*" (3 Results)
- **immultifit** : shell radius fits per channel  
  > "using *immultifit* (cite: MartiVidal2014) by fitting a shell of emission to each individual channel" (3 Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Angular rotation velocity w sin i | 3.5 | 0.3 | 1e-9 rad/s | 4 | $\omega_R\sin{i}=(3.5 \pm 0.3) \times10^{-9}$ rad s$^{-1}$ |
| Rotation period P/sin i | 57 | 5 | yr | 4 | $P/\sin{i}
= 57\pm5$ yr |
| Position angle of rotation axis | 7 | 6 | deg | 4 | The weighted average position angle of the rotation axis $\Phi=7\pm6^\circ$. |
| Continuum size at 214 GHz | 62.4x61.8 | 0.1 | mas | 1 | $(62.4\pm0.1)\times(61.8\pm0.1)~{\rm mas}$ |

## Qualitative findings

- Velocity gradients across SiO and SO2 lines indicate rotation of the star and envelope; an anomalous fast-rotating feature extends beyond 10 R*  
  > "Consequently we conclude that only rotation of the star and its envelope can explain the velocity field observed." (3 Results)

## Claim tuples

- H: R Dor's atmosphere rotates | E: Per-pixel line velocity fits and solid-body rotation chi2 fit | R: omega sin i = 3.5±0.3e-9 rad/s, P/sin i = 57±5 yr | F: Solid-body rotation out to at least 2 R* | **supported**
- H: Single-star evolution can explain the rotation | E: Compared with a 1.5 Msun rotating stellar model | R: Model surface rotation ~0.01 km/s, two orders lower than observed | F: A low-mass companion is the likely cause | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Convective cells, edge-on disc, tilted disc and bipolar outflow rejected as origin of velocity gradient  
  > "we can rule out a chance alignment of convective cells." (3 Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Angular resolution limits fitting to solid-body rotation; sin i unknown  
  > "our angular resolution does not allow us to fit the extra parameters needed for a more detailed description of the rotation." (3 Results)
- Caveat (inferred, ours): Inclination unknown so rotation velocity is a lower limit
- Caveat (inferred, ours): Strong vsys-vexp degeneracy and few resolution elements
- Caveat (inferred, ours): Lines affected by pulsation and possible maser action
- Caveat (inferred, ours): Companion not detected

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration details deferred to a paper in prep
- Missing: Imaging parameters
- Missing: Aperture and mask definitions
- Data volume (inferred): ~100 GB
- Score (inferred): 4/5, Data public project, but calibration and imaging details missing; fits are simple.
- Rediscovery candidate: no, Calibration and imaging recipe incomplete.

## Links

- Method: (cite: Kervella2018) (rotating shell velocity model)
- Method: (cite: MartiVidal2014) (immultifit)
- Method: (cite: Vlemmings2017) (uv-fitting of stellar size)
- Companion: (cite: Homan2018) (lower resolution detection of velocity gradient)

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2016.1.0004.S"
 ],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 30,
  "rate": 0.455
 },
 "evidence_ok": true
}
```
