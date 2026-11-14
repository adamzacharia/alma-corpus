# Circumstellar CO in metal-poor stellar winds: the highly irradiated globular cluster star 47 Tucanae V3

`2019MNRAS.484L..85M` | Monthly Notices of the Royal Astronomical Society 2019 | first author: McDonald, I. | arXiv: 1901.05416 | DOI: 10.1093/mnrasl/slZ009

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, stellar_physics
- Question: Is circumstellar CO detectable around a metal-poor globular cluster AGB star (47 Tuc V3), and what do its wind velocity and CO strength say about the wind-driving mechanism and the ISRF?  
  > "We report the first detection of circumstellar CO in a globular cluster." (abstract)
- Target **47 Tucanae V3**: coordinates 00h25m16.023s -72d03m54.70s  
  > "It is populous, and close ($\sim$4.5 kpc; (cite: Harris96))." (Introduction); "V3 is recovered as a point source at $00^h 25^m 16.^{\!s}023$ $-72^\circ 03^\prime 54.70\ensuremath{''}$" (Observations & Results); z/distance ~4.5 kpc  
  > "It is populous, and close ($\sim$4.5 kpc; (cite: Harris96))." (Introduction); "V3 is recovered as a point source at $00^h 25^m 16.^{\!s}023$ $-72^\circ 03^\prime 54.70\ensuremath{''}$" (Observations & Results); distance from Harris96 (cite)  
  > "It is populous, and close ($\sim$4.5 kpc; (cite: Harris96))." (Introduction); "V3 is recovered as a point source at $00^h 25^m 16.^{\!s}023$ $-72^\circ 03^\prime 54.70\ensuremath{''}$" (Observations & Results)

## Data provenance

- ALMA projects: 2016.1.00078.S
- bands: Band 7  
  > "observed 47 Tuc V3 in Band 7 on 2018 May 12, 13 and 15" (Observations & Results)
- frequencies and spectral setup: 4 spectral windows, 331.74–348.73 GHz; CO window at 488 kHz (0.42 km/s); others 15.625 MHz  
  > "The remaining windows were observed at a resolution of 15.625 MHz ($\sim$13.5 km s$^{-1}$)" (Observations & Results)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: uv-coverage sensitive to 1.14–5.51 arcsec  
  > "The $uv$-coverage of the array is sensitive to angular resolutions between 1.14 and 5.51$^{\prime\prime}$." (Observations & Results)
- max recoverable scale: _not stated_
- sensitivity: 0.62 mJy/channel/beam line; 21 uJy/beam continuum  
  > "attaining a total continuum sensitivity of 21 $\mu$Jy beam$^{-1}$" (Observations & Results)
- time on source: 5.2 hours  
  > "totalling 5.2 hours of on-source observation over four spectral windows" (Observations & Results)
- observing dates: 2018 May 12, 13 and 15  
  > "observed 47 Tuc V3 in Band 7 on 2018 May 12, 13 and 15" (Observations & Results)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (345.796 GHz)
- Line: SiO v=1 J=8-7 (344.917 GHz)
- Other facility **Gaia DR2**: expected position and proper motion of V3  
  > "its expected position ($00^h 25^m 16.^{\!s}003$ $-72^\circ 03^\prime 54.68\ensuremath{''}$; (cite: GaiaDR2))" (Observations & Results)
- External data: Previous mass-loss rate constraint for V3 ~1.2–3.5e-7 Msun/yr and ISRF ~9x solar neighbourhood  
  > "(cite: MZL+15) estimated that the ISRF at V3 was $\sim$9$\times$ stronger than in the Solar Neighbourhood, with a factor $\sim$3 uncertainty" (Discussion & Conclusions) [from MZL+15]
- External data: Galactic comparison star parameters and CO 3-2 intensities  
  > "Table [\[StarsTable\]](#StarsTable), data from (cite: SRO+13)" (Discussion & Conclusions) [from SRO+13]
- External data: Dust model of V3 with v_inf 3.2 km/s and mass-loss 9.4e-7 Msun/yr  
  > "The modelled mass-loss rate (9.4 $\times$ 10$^{-7}$ M$_\odot$ yr$^{-1}$) is higher than the constraint from evolutionary arguments" (Discussion & Conclusions) [from MBvLZ11]

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
- continuum subtraction: CO and SiO lines masked from continuum image construction  
  > "V3 is recovered in the frequency-averaged continuum image (the CO and SiO lines were masked from its construction)" (Observations & Results)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- CO dissociation model and ISRF estimate for V1 scaled to V3  
  > "The same paper presented a model of CO dissociation around V1, which is expected to have an ISRF $\sim$5$\times$ stronger than V3." (Discussion & Conclusions) [from MZL+15]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the pipeline or archive products were used
- Flux, bandpass and phase calibrators
- Imaging task, weighting, robust, cell and image size
- Synthesised beam and line rms in final cubes
- Exact continuum channels and masks used
- Line-free channels for the continuum
- Spectral resolution handling (smoothing/binning) of the extracted spectra
- Photospheric model details for SED scaling

## Analysis recipe

1. **Extract line spectra and integrated fluxes**: Spectra extracted in 1 arcsec radius circle around V3; line flux integrated over –46 to –36 km/s  
  > "computed over the 1$^{\prime\prime}$ aperture and the velocity range –46 to –36 km s$^{-1}$" (Observations & Results)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit line profiles for velocity and expansion speed**: Parabolic line function fit by chi^2 minimisation; v_inf taken as half HWZP  
  > "were each fit by a parabolic line function using $\chi^2$ minimisation" (Observations & Results)
   - assumption: CO profile well represented by a paraboloid  
  > "As the CO line profile is well-represented by a paraboloid, $v_\infty$ can be taken directly as half the model’s HWZP" (Discussion & Conclusions)
   - fitting: chi^2 minimisation; reduced chi^2 2.2 (CO), 5.3 (SiO)  
  > "and reduced $\chi^2$ of 2.2 and 5.3" (Observations & Results)
   - validation: _not stated_
3. **Measure continuum and constrain dust**: Frequency-averaged continuum flux compared with scaled dustless photospheric model, molecular line and synchrotron contributions  
  > "meaning the continuum flux density from dust is $\lesssim$20 $\pm$ 16 $\mu$Jy" (Observations & Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare with Galactic stars and ISRF model, test metallicity scaling**: CO intensity compared with Galactic stars scaled to 4.5 kpc and with the MZL+15 photodissociation model; v_inf compared with sqrt(Z) scaling  
  > "this is closely in keeping with a $v_\infty \propto \sqrt{Z}$ law, meaning the wind is likely to be driven by radiation pressure on dust" (Discussion & Conclusions)
   - assumption: Distance 4.5 kpc; [Fe/H] = –0.72, ~0.2 Zsun  
  > "As the metallicity of 47 Tuc is approximately 0.2 $Z_\odot$" (Discussion & Conclusions)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO 3-2 integrated line flux | 35.8 | 5.1 | mJy km/s | 1 | integrated line strength of 35.8 $\pm$ 5.1 mJy km s$^{-1}$ (7$\sigma$) |
| SiO v=1 J=8-7 integrated line flux | 48.9 | 4.4 | mJy km/s | 1 | 48.9 $\pm$ 4.4 mJy km s$^{-1}$ (11$\sigma$) |
| CO central velocity (fit) | –40.6 | 0.3 | km/s | 2 | central velocities of –40.6 $\pm$ 0.3 and –40.4 $\pm$ 0.4 km s$^{-1}$ |
| CO terminal expansion velocity | 3.2 | 0.4 | km/s | 2 | $v_\infty$ can be taken directly as half the model’s HWZP: 3.2 $\pm$ 0.4 km s$^{-1}$ |
| 345 GHz continuum flux density of V3 | 58 | 16 | uJy | 3 | with a 345-GHz flux density of $F = 58 \pm 16$ $\mu$Jy ($\sim$3.5$\sigma$) |
| Dust continuum flux density at 345 GHz | ≲20 | 16 | uJy | 3 | meaning the continuum flux density from dust is $\lesssim$20 $\pm$ 16 $\mu$Jy |
| Unrelated 345 GHz point source flux | 556 | 56 | uJy | 3 | with a flux density at 345 GHz of $F = 556 \pm 56$ $\mu$Jy |

## Qualitative findings

- CO line is about an order of magnitude weaker than for Galactic stars with similar mass loss, consistent with ISRF photodissociation  
  > "We retrieve a CO line intensity an order of magnitude lower than this." (Discussion & Conclusions)
- SiO line is asymmetric and brighter, likely a maser  
  > "suggesting the line is more likely masing" (Discussion & Conclusions)

## Claim tuples

- H: Circumstellar CO can be detected in CO J=3-2 around a globular cluster AGB star | E: ALMA Band 7 observations of 47 Tuc V3 | R: CO detected at 7 sigma, v_LSR –40.6 km/s | F: First detection of circumstellar CO in a globular cluster | **supported**
- H: The wind terminal velocity is set by radiation pressure on dust | E: Compared v_inf with Galactic stars and the sqrt(Z) law | R: v_inf is 2–3x slower than Galactic stars, matching 0.2 Zsun | F: Pulsation-enhanced dust-driven wind | **partially**
- H: Strong ISRF photodissociates CO in globular clusters | E: Compared CO intensity with Galactic stars and the MZL+15 model | R: CO an order of magnitude weaker; matches model prediction | F: Supports photodissociation model | **supported**

## Reasoning

- Why this data: V3 chosen as farthest from cluster centre, hence least subject to ionising radiation; higher CO transitions excited closer to the star  
  > "We selected the third-brightest AGB star, V3, for re-observation, as it is the furthest from the cluster centre" (Introduction)
- Why this method: _not stated_
- Alternative: Magnetic fields cannot be completely ruled out as the wind driver  
  > "Magnetic fields cannot be completely ruled out either" (Discussion & Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): Single object; possible geometric asymmetries or time dependence  
  > "it is difficult to ascertain with certainty the wind-driving mechanism in metal-poor stars from observations of a single object" (Discussion & Conclusions)
- Caveat (inferred, ours): Only a 3.8 sigma peak and one star; the metallicity scaling rests on one object
- Caveat (inferred, ours): Galactic comparison stars are poorly matched in type and properties
- Caveat (inferred, ours): Parabolic fit has reduced chi^2 of 2.2 and the 1.5 sigma redshifted wing is unresolved
- Caveat (inferred, ours): SiO maser interpretation is not tested

## Reproducibility

- Data public (paper): ALMA project code given and data acknowledged via ADS/JAO.ALMA  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00078.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibration and imaging details
- Missing: Photospheric SED model parameters
- Missing: Exact aperture/continuum procedures
- Data volume (inferred): ~10-50 GB raw for 5.2 h in Band 7
- Score (inferred): 3/5, Data are public and the measurements are simple, but calibration and imaging settings are not given.
- Rediscovery candidate: no, Imaging and calibration recipe is largely unstated, so the line fluxes are only approximately reproducible.

## Links

- Companion: MZL+15 (Previous ALMA CO J=2-1 non-detection and ISRF/CO dissociation model)
- Companion: MBvLZ11 (Dust modelling of V3)

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
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
  "facts": 66,
  "stated": 29,
  "rate": 0.439
 },
 "evidence_ok": true
}
```
