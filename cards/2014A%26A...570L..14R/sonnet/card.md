# The wonderful complexity of the Mira AB system

`2014A&A...570L..14R` | Astronomy and Astrophysics 2014 | first author: Ramstedt, S. | arXiv: 1410.1529 | DOI: 10.1051/0004-6361/201425029

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: What is the morphology of the circumstellar CO(3-2) gas around the Mira AB binary, and how has it been shaped by the binary interaction?  
  > "We have mapped the CO(3-2) line emission around the system with considerably higher spatial resolution than previous observations ($\sim$0.5$''$)." (Introduction)
- Target **Mira AB**: coordinates Mira A 02:19:20.784 -02:58:42.818 (J2000)  
  > "The Mira AB system is well-studied and nearby (cite: vlee07)." (Introduction); "| Mira A | 02:19:20.784 | -02:58:42.818 | 252.3$\pm$0.3 mJy |" (Table 1); z/distance 100 pc (assumed in discussion)  
  > "The Mira AB system is well-studied and nearby (cite: vlee07)." (Introduction); "| Mira A | 02:19:20.784 | -02:58:42.818 | 252.3$\pm$0.3 mJy |" (Table 1); distance from van Leeuwen 2007 (nearby); 100 pc used in modelling estimate  
  > "The Mira AB system is well-studied and nearby (cite: vlee07)." (Introduction); "| Mira A | 02:19:20.784 | -02:58:42.818 | 252.3$\pm$0.3 mJy |" (Table 1)

## Data provenance

- ALMA projects: 2012.1.00524.S
- bands: Band 7 (CO(3-2); spectral windows at 331-345 GHz)  
  > "The observations have four spectral windows with a width of $1.875$ GHz (main array) and $2$ GHz (ACA) centered on 331, 333, 343 and 345 GHz." (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m main array (27 and 30 antennas) plus ACA 7m (seven antennas)  
  > "Mira was observed on 25 February 2014 and 3 May 2014, with 27 and 30 of the main array 12m antennas, respectively." (2 Observations)
- configurations: _not stated_
- baselines: Main array 13-450 m; ACA 9-45 m  
  > "The baseline length of the main array ranges from 13 to 450 m" (2 Observations)
- angular resolution: beam 0.576'' x 0.403''  
  > "The images have a beam full width half maximum (FWHM) of 0.576$''$$\times$0.403$''$" (2 Observations)
- max recoverable scale: ~6'' (main array), ~9'' (ACA)  
  > "we find a maximum recoverable scale (MRS) of $\sim$6$''$. The ACA covers 9 to 45 m baselines and the MRS is $\sim$9$''$." (2 Observations)
- sensitivity: rms 23 mJy/beam in emission-free channels  
  > "reach an rms noise of 23 mJy/beam in the emission free channels." (2 Observations)
- time on source: 6.25 min main array; 6 min ACA  
  > "The total time on source is 6.25 minutes with the main array and 6 minutes with the ACA." (2 Observations)
- observing dates: 25 Feb 2014, 3 May 2014 (main); 8 Oct 2013 (ACA)  
  > "It was also observed with seven Atacama Compact Array (ACA) 7m antennas on 8 October 2013." (2 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (not stated)
- External data: Orbit of Mira AB: inclination 112 deg, period ~500 yr, expected separation ~0.5'' at PA ~100 deg  
  > "The latest calculation of the orbit (cite: prieetal02), gives an inclination of 112$^{\circ}$, an orbital period of $\sim$500 yrs" (Introduction) [from (cite: prieetal02)]
- External data: Single-dish CO spectrum used to estimate recovered flux  
  > "Comparison of our spectrum with previous single dish observations (cite: youn95) indicates that even with the ACA only 50% of the extended flux is recovered." (3.2 Circumstellar morphology) [from (cite: youn95)]
- External data: VLA radio continuum spectral index S ∝ nu^1.5 for Mira A  
  > "In order for the $S_{\nu}$ $\propto$ $\nu^{1.5}$ relation determined by (cite: mattkaro06) for Mira A to hold to submm wavelengths" (3.1 Continuum emission and current positions) [from (cite: mattkaro06)]

## Processing

### Calibration

- pipeline or manual: CASA, standard procedures, each data set separately  
  > "Calibration on the separate data sets was carried out using CASA, following standard procedures" (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede, Uranus and J0334-401  
  > "Ganymede, Uranus and the quasar J0334-401 as flux calibrators." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration using the continuum image  
  > "As the continuum emission is sufficiently strong, this image was used for self-calibration." (2 Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum from emission-free channels of all spectral windows, subtracted before line imaging  
  > "A continuum image was made using the emission free channels from all spectral windows." (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Main array and ACA combined, ACA weighted down by factor 0.3  
  > "The data were subsequently combined, weighing the ACA data down by a factor of $0.3$ to account for the lower sensitivity of the 7m antennas." (2 Observations)
- smoothing: Averaged over 2 channels to ~0.85 km/s  
  > "averaging over 2 channels to $\sim$0.85 km s$^{-1}$ spectral resolution" (2 Observations)
- final beam: 0.576'' x 0.403''  
  > "The images have a beam full width half maximum (FWHM) of 0.576$''$$\times$0.403$''$" (2 Observations)
- final rms: 23 mJy/beam (emission-free channels); 30-160 mJy in line channels  
  > "the rms varies between 30 and 160 mJy in the different velocity channels." (Appendix A)

### Inherited from earlier work

- Continuum positions and fluxes determined by uv fitting  
  > "The current positions determined by uv fitting (cite: martetal14) are given in Table [1](#contdata)" (3.1 Continuum emission and current positions) [from (cite: martetal14)]

### Not stated but needed to reproduce (our reading)

- tclean parameters: weighting/robust, deconvolver, cell and image size, masks
- CASA version
- Line-free channels used for continuum
- Self-calibration solution intervals
- Flux scale uncertainty
- How the uv fit was performed (model, software)
- How the position-velocity cut was extracted
- Spectral setup details beyond window centres

## Analysis recipe

1. **Combine and image data**: Calibrate separately, combine 12m and ACA with ACA weight 0.3, self-calibrate on continuum, subtract continuum, image line  
  > "After applying the self-calibration, final imaging was done after subtracting the continuum, and averaging over 2 channels to $\sim$0.85 km s$^{-1}$ spectral resolution." (2 Observations)
   - software: CASA
   - parameter: ACA weight factor 0.3  
  > "weighing the ACA data down by a factor of $0.3$" (2 Observations)
   - fitting: _not stated_
   - validation: Tests indicate the exact ACA weight does not affect results  
  > "Tests indicate that the exact weight does not affect our results." (2 Observations)
2. **Measure binary positions and continuum flux**: uv fitting of continuum data for Mira A and B  
  > "The current positions determined by uv fitting (cite: martetal14) are given in Table [1](#contdata)" (3.1 Continuum emission and current positions)
   - fitting: uv fitting  
  > "The current positions determined by uv fitting (cite: martetal14) are given in Table [1](#contdata) together with the measured flux density at 338 GHz of the two sources." (Results, Continuum emission and current positions)
   - validation: Compared with predicted orbit position  
  > "This agrees with predictions from the orbit by (cite: prieetal02)." (4.1 Comparison to previous observations)
3. **Characterise CO morphology**: Inspect channel maps and a position-velocity diagram along bubble major axis (PA 38 deg)  
  > "position-velocity diagram created along the major axis (position angle 38$^{\circ}$) of the south-east bubble." (3.2 Circumstellar morphology)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration, combination, imaging  
  > "Calibration on the separate data sets was carried out using CASA, following standard procedures" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Binary separation | 0.487 | 0.006 | arcsec | 2 | This gives a total separation of 0.487$''$$\pm$0.006$''$. |
| Mira A flux density at 338 GHz | 252.3 | 0.3 | mJy | 2 | / Mira A / 02:19:20.784 / -02:58:42.818 / 252.3$\pm$0.3 mJy / |
| Mira B flux density at 338 GHz | 15.3 | 0.3 | mJy | 2 | / Mira B / 02:19:20.816 / -02:58:42.887 / 15.3$\pm$0.3 mJy / |
| Bubble radial expansion velocity (lower limit) | ~5 | not stated | km/s | 3 | this gives a lower limit of the radial expansion velocity of $\sim$5 km s$^{-1}$. |
| Bubble size | ~800 | not stated | AU | 3 | The bubble found on the south-east side of Mira A is $\sim$800 AU across |
| Position angle of Mira B | 98 | not stated | deg | 2 | the current position of Mira B is $\approx$0.5$''$ east of Mira A at a position angle of 98$^{\circ}$. |

## Qualitative findings

- Spiral arcs around Mira A are flat and oriented in the orbital plane, with an accretion wake behind the companion  
  > "The spiral appears to be relatively flat and oriented in the orbital plane." (abstract)

## Claim tuples

- H: Is the CO gas shaped by binary interaction producing a flat spiral? | E: ALMA+ACA CO(3-2) channel maps | R: Spiral arcs seen from 45 to 54 km/s with accretion wake; projected separation 3-5'' | F: Slow AGB wind fills Roche lobe and flows onto companion in orbital plane | **supported**
- H: Does Mira B's wind blow a bubble in Mira A's envelope? | E: Blue-wing channel maps and PV diagram, order-of-magnitude timescale | R: ~800 AU bubble, expansion >=5 km/s, timescale ~380 yr | F: Tentative explanation; timescale somewhat longer than orbital half-period | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Interaction with the ISM cannot explain inner structures, since the bow shock lies much further out  
  > "The presence of the bow shock much further out means that the inner structures cannot be explained by (hydrodynamic) interaction with the ISM." (4.1 Comparison to previous observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Only ~50% of extended flux recovered even with ACA; dynamic range limited to ~50  
  > "even with the ACA only 50% of the extended flux is recovered." (3.2 Circumstellar morphology)
- Caveat (inferred, ours): Bubble interpretation is qualitative; no modelling
- Caveat (inferred, ours): Missing short-spacing flux affects bubble interior interpretation
- Caveat (inferred, ours): Imaging parameters unspecified

## Reproducibility

- Data public (paper): Project code given; ALMA data acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00524.S ." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: uv-fit details
- Missing: Self-cal settings
- Data volume (inferred): ~50-100 GB (Cycle 1 12m mosaic plus ACA, 4 spws)
- Score (inferred): 3/5, Data identified and calibration outlined, but imaging parameters missing and results mostly morphological.
- Rediscovery candidate: no, Main results are largely qualitative morphology; imaging recipe incomplete.

## Links

- Method: Martí-Vidal et al. 2014 (cite: martetal14) (uv fitting of positions)
- Companion: Maercker et al. 2012 (cite: maeretal12) (R Scl spiral comparison)

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 61,
  "stated": 36,
  "rate": 0.59
 },
 "evidence_ok": true
}
```
