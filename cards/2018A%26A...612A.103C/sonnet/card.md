# Radio outburst from a massive (proto)star. When accretion turns into ejection

`2018A&A...612A.103C` | Astronomy and Astrophysics 2018 | first author: Cesaroni, R. | arXiv: 1802.04228 | DOI: 10.1051/0004-6361/201732238

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation
- Question: Did the accretion burst in the massive YSO S255 NIRS 3 produce a radio (thermal jet) burst, and what are the jet properties?  
  > "Our main goal was to establish whether the accretion burst had boosted the radio thermal jet visible in archival VLA images of S255 NIRS 3" (Introduction)
- Target **S255 NIRS 3**: coordinates RA(J2000)=06h12m54.02s, Dec=+17d59m23.1s (phase centre)  
  > "located at a distance of 1.78$^{+0.12}_{-0.11}$ kpc (Burns et al. (cite: burns))" (Introduction); "$\alpha$(J2000)=$06^{\rm h}\,12^{\rm m}\,54.02s$, $\delta$(J2000)=17$^\circ$ 59$'$ 23.1$''$." (Observations and data analysis); z/distance 1.78 (+0.12/-0.11) kpc  
  > "located at a distance of 1.78$^{+0.12}_{-0.11}$ kpc (Burns et al. (cite: burns))" (Introduction); "$\alpha$(J2000)=$06^{\rm h}\,12^{\rm m}\,54.02s$, $\delta$(J2000)=17$^\circ$ 59$'$ 23.1$''$." (Observations and data analysis); distance from Burns et al. 2016  
  > "located at a distance of 1.78$^{+0.12}_{-0.11}$ kpc (Burns et al. (cite: burns))" (Introduction); "$\alpha$(J2000)=$06^{\rm h}\,12^{\rm m}\,54.02s$, $\delta$(J2000)=17$^\circ$ 59$'$ 23.1$''$." (Observations and data analysis)

## Data provenance

- ALMA projects: 2016.A.00008.T
- bands: Band 3  
  > "S255 NIRS 3 was observed with ALMA at band 3 on December 16, 2016." (2.3 ALMA)
- frequencies and spectral setup: four 2 GHz units centred at 85.2, 87.2, 97.2, 99.2 GHz; 0.49 MHz resolution  
  > "centred at 85.2, 87.2, 97.2, and 99.2 GHz. We chose the maximum possible spectral resolution of 0.49 MHz" (2.3 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: ~20 to ~400 m, 45 antennas  
  > "The array consisted of 45 antennas arranged in a configuration with baselines from $\sim$20 to $\sim$400 m" (2.3 ALMA)
- angular resolution: 2.21x2.12 to 2.61x2.45 arcsec  
  > "ranged respectively from 2.21$''$$\times$2.12$''$ to 2.61$''$$\times$2.45$''$" (2.3 ALMA)
- max recoverable scale: ~30 arcsec  
  > "which provides sensitivity to structures up to $\sim$30$''$" (2.3 ALMA)
- sensitivity: 1 sigma rms 0.34 to 0.61 mJy/beam  
  > "from 0.34 to 0.61 mJy/beam, depending on the frequency" (2.3 ALMA)
- time on source: _not stated_
- observing dates: December 16, 2016  
  > "S255 NIRS 3 was observed with ALMA at band 3 on December 16, 2016." (2.3 ALMA)
- pi or archival as stated: _not stated_
- Other facility **VLA**: 6-45.5 GHz monitoring, 6 epochs in 2016 (16A-424)  
  > "at five epochs during 2016 (project code: 16A-424)" (2.1 Very Large Array)
- Other facility **IRAM/NOEMA**: 3.4 and 2 mm continuum, Jan and Feb 2017  
  > "We observed S255 NIRS 3 with the interferometer on January 23 and February 15, 2017." (2.2 IRAM/NOEMA)
- External data: SMA flux densities at 225-350 GHz at various resolutions  
  > "Flux densities measured at mm wavelengths towards S255 NIRS 3 with the SMA by various authors." (Table 1) [from Zinchenko et al. (cite: zin12); Zinchenko et al. (cite: zin15); Wang et al. (cite: wang)]
- External data: Archival VLA 1990 map (project AM301)  
  > "archival data obtained at the same frequency on August 27, 1990 (project AM301)" (3.1 Centimetre emission) [from archival VLA AM301]

## Processing

### Calibration

- pipeline or manual: ALMA data reduction pipeline in CASA  
  > "Calibration and imaging were performed with the CASA software by employing the ALMA data reduction pipeline." (2.3 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800 and J0750+1231 (flux and bandpass)  
  > "For flux and bandpass calibration we used the strong calibrators J0510$+$1800 and J0750$+$1231" (2.3 ALMA)
- flux scale uncertainty: ~20%  
  > "We estimate a calibration error of $\sim$20%." (2.3 ALMA)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "A data cube was created from each 2 GHz correlator unit with natural weighting." (2.3 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: STATCONT automatic line-free channel identification  
  > "we adopted the STATCONT method by Sánchez-Monge et al. ((cite: statcont)), which automatically identifies line-free channels in the cubes." (2.3 ALMA)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Continuum extraction method (STATCONT)  
  > "we adopted the STATCONT method by Sánchez-Monge et al. ((cite: statcont))" (2.3 ALMA) [from Sánchez-Monge et al. 2017 (cite: statcont)]
- Jet model (standard spherical case)  
  > "we adopt the jet model by Reynolds ((cite: reyn))" (4 Interpretation) [from Reynolds 1986 (cite: reyn)]

### Not stated but needed to reproduce (our reading)

- CASA/pipeline version for ALMA
- cell size, image size, deconvolver and masking for ALMA
- aperture used to integrate the SMA1 flux
- ALMA flux calibrator flux values
- grid ranges for chi2 fit

## Analysis recipe

1. **ALMA continuum flux of NIRS 3**: Continuum maps via STATCONT from four 2 GHz cubes; integrate over SMA1 core; average pairs  
  > "for each continuum image the flux density of S255 NIRS 3 was computed by integrating the emission over the corresponding core" (2.3 ALMA)
   - software: CASA, STATCONT
   - fitting: _not stated_
   - validation: _not stated_
2. **Pre-burst mm spectrum correction from SMA fluxes**: Fit S proportional to beam^alpha at 225 GHz, scale to 3.37 arcsec, fit spectral slope  
  > "we assume that the largest angular scale, $\Theta_{\rm L}$, that can be imaged by the interferometer is proportional to the synthesized beam" (3.2 Millimetre emission)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** ALMA pipeline version not stated; VLA 4.3.1 to 4.5.2: calibration and imaging  
  > "Calibration and imaging were performed with the CASA software by employing the ALMA data reduction pipeline." (2.3 ALMA)
- **STATCONT** : continuum from line-free channels  
  > "we adopted the STATCONT method by Sánchez-Monge et al. ((cite: statcont))" (2.3 ALMA)
- **GILDAS** : NOEMA calibration and imaging  
  > "using the GILDAS package" (2.2 IRAM/NOEMA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA flux density at 86.2 GHz | 73 | ~20% calibration | mJy | 1 | a continuum flux density of $\sim$73 mJy at 86.2 GHz and $\sim$90 mJy at 98.2 GHz |
| ALMA flux density at 98.2 GHz | 90 | ~20% calibration | mJy | 1 | a continuum flux density of $\sim$73 mJy at 86.2 GHz and $\sim$90 mJy at 98.2 GHz |
| SMA spectral slope fit | S = 3.89e-3 nu^2.08 | not stated | mJy, GHz | 2 | S_\nu({\rm mJy}) = 3.89\times10^{-3} \, \left[\nu({\rm GHz})\right]^{2.08}. |

## Qualitative findings

- mm emission constant in time; small excess over pre-burst extrapolation explained by jet free-free emission  
  > "can be entirely due to the free-free emission from the radio jet and not to dust heating by the outburst" (4.2 Origin of the millimetre emission)

## Claim tuples

- H: Accretion burst triggered a radio burst | E: VLA monitoring 6-45 GHz in 2016 | R: Core flux rose exponentially from July 2016, timescale ~77 d | F: First radio burst associated with IR outburst, ~13 month lag | **supported**
- H: mm dust emission brightened with the burst | E: ALMA and NOEMA continuum vs extrapolated SMA fluxes | R: Excess is 20-40% and matches jet free-free | F: No dust heating brightening | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Photoionization rejected as cause of radio burst (timescale ~2.3 h vs 13 months)  
  > "we find a timescale of only $\sim$2.3 hours" (4.3 Time lag)
- How they decided it was enough: _not stated_
- Limitation (authors): Simplified jet model; fully modelling the perturbation propagation too complicated  
  > "modelling the propagation of a similar perturbation across the jet is too complicated for our purposes" (4 Interpretation)
- Caveat (inferred, ours): ALMA used only for one epoch of continuum; mm conclusion depends on empirical SMA flux correction
- Caveat (inferred, ours): Inclination and r0 choices are assumed

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA imaging parameters and aperture
- Missing: pipeline version
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, ALMA part is simple but imaging details are missing.
- Rediscovery candidate: no, ALMA role is minor and settings are incomplete.

## Links

- Method: Sánchez-Monge et al. 2017 (cite: statcont) (STATCONT continuum method)
- Method: Reynolds 1986 (cite: reyn) (thermal jet model)
- Companion: Caratti o Garatti et al. 2017 (cite: cagana) (IR accretion burst)

## Checks

```json
{
 "quotes": 40,
 "quotes_ok": 40,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 61,
  "stated": 30,
  "rate": 0.492
 },
 "evidence_ok": true
}
```
