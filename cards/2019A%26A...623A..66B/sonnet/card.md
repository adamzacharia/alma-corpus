# ALMA CO(2-1) observations in the XUV disk of M83

`2019A&A...623A..66B` | Astronomy and Astrophysics 2019 | first author: Bicalho, Isadora C. | arXiv: 1807.01373 | DOI: 10.1051/0004-6361/201732352

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation, milky_way_ism
- Question: Is there molecular gas (CO(2-1), GMCs) in the XUV disk of M83 where UV emission and HI are present, and how does this constrain star formation efficiency?  
  > "It offers the opportunity to search for the molecular gas and characterise the star formation in outer disk regions, traced by the UV emission." (abstract)
- Target **M83 outer (XUV) disk**: coordinates 13h 37m 03.6s -29d 59' 47.6" (field center)  
  > "The selected region is located at $13h 37m 03.6s ~ -29d 59' 47.6''$ enclosed in a $3'\times1.5'$ ($4kpc\times 2 kpc$) rectangle located at $r_{gal} = 7.85' = 11kpc$ from M83 center." (2 Observations); "Distance (Mpc)   |          4.8" (Table 1); z/distance 4.8 Mpc  
  > "The selected region is located at $13h 37m 03.6s ~ -29d 59' 47.6''$ enclosed in a $3'\times1.5'$ ($4kpc\times 2 kpc$) rectangle located at $r_{gal} = 7.85' = 11kpc$ from M83 center." (2 Observations); "Distance (Mpc)   |          4.8" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00861.S
- bands: Band 6, CO(2-1) at 229.67 GHz  
  > "We observe CO(2-1) emission at 229.67 GHz (band 6) in M83 with ALMA during Cycle 2 (PI: Monica Rubio)." (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m array, 34 antennas  
  > "The 12m array was used with 34 antennas and a maximum baseline of 558.2 m." (2 Observations)
- configurations: _not stated_
- baselines: maximum baseline 558.2 m  
  > "The 12m array was used with 34 antennas and a maximum baseline of 558.2 m." (2 Observations)
- angular resolution: 0.75"x0.56" = 17x13 pc  
  > "Synthetized Beam | 0.75"x0.56" = 17x13pc" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: 10.3 mJy per 2.5 km/s channel; 4 mJy in 15 km/s channels per beam; continuum rms 0.19 mJy  
  > "a channel spacing of 2.5 km/s and an rms of 10.3 mJy per channel" (2 Observations); "The rms noise level is 4mJy in 15km/s channels for each beam of 0.75"x0.56"." (2 Observations)
- time on source: 1 hour; 10.8 s per pointing; mosaic of 121 pointings spaced 12.9"  
  > "The map was done with a mosaic of 121 pointings separated by 12.9" (figure [2](#fig:mosaic_point)), and with an integration time of 10.8 sec per pointing." (2 Observations)
- observing dates: March 2014  
  > "The selected region of M83 was observed during  1hour in March 2014, in very good weather conditions (pwv 1.3mm)." (2 Observations)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (229.67 GHz (as stated))
- Other facility **GALEX**: FUV/NUV images used to select UV peaks  
  > "We used the selection criteria corresponding to FUV/NUV GALEX images (cite: GP07), using the peaks of UV emission" (2 Observations)
- Other facility **THINGS (VLA HI)**: HI emission and velocity for selection and stacking  
  > "as well as the correlation with the HI emission from the THINGS survey (cite: things)" (2 Observations)
- Other facility **Subaru**: Halpha observations to locate 13 star-forming regions  
  > "Using the observations from the Subaru telescope (cite: koda12) we found 13 regions of star formation" (3 Results)
- External data: Halpha map used to select star-forming regions  
  > "Using the observations from the Subaru telescope (cite: koda12) we found 13 regions of star formation" (3 Results) [from (cite: koda12)]
- External data: Comparison sample of nearby galaxies for Kennicutt-Schmidt diagram  
  > "with the large sample of nearby galaxies from (cite: Bigiel08)" (4.1 Star formation diagram) [from (cite: Bigiel08)]
- External data: Mean HII-region metallicity 12+log(O/H)=8.4  
  > "the average metallicity of the H$_{II}$ regions is $12+log(O/H)=8.4$ (cite: bresolin09)" (4.2 The dearth of CO emission in the outer disc of M83) [from (cite: bresolin09)]

## Processing

### Calibration

- pipeline or manual: calibrated with CASA; ~36% of data flagged  
  > "The data were calibrated using the CASA reduction package." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: cleaning and cube analysis in GILDAS from 121 exported uv-tables  
  > "The calibrated 121 uv-tables were subsequently exported to GILDAS where the cleaning and the cube analysis were performed." (2 Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We produced a CO(2-1) data cube for each pointing with natural weighting" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: CO map smoothed to 1.5" for stacking  
  > "We smoothed the CO(2-1) map at the 1.5$\ensuremath{''}$ resolution" (3.2 Stacking)
- final beam: line 0.75"x0.56"; continuum 0.78"x0.60"  
  > "Using natural weighting, the synthesized beamsize of the continuum map was 0.78"x0.60", with rms$=$0.19 mJy." (2 Observations)
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- CASA version and calibrators (flux, bandpass, phase)
- Clean threshold, masks, cell and image size in GILDAS
- Primary beam correction and mosaic handling
- Continuum subtraction and line-free channels
- Exact detection-assessment parameters in GILDAS
- Stacking details: noise estimation, number of stacked spectra, how 'when properly reduced' flux was obtained
- Source of the 4.8 Mpc distance

## Analysis recipe

1. **Image cubes and derive per-beam upper limits**: Natural-weighted cubes per pointing cleaned in GILDAS; 3 sigma limit assuming 15 km/s FWHM, converted to H2 mass  
  > "The 3$\sigma$ upper limit of the integrated emission is therefore 0.180 Jy km/s." (2 Observations)
   - software: CASA, GILDAS
   - parameter: channel 2.5 km/s, 15-1015 km/s  
  > "for a velocity range from 15 to 1015 km/s, a channel spacing of 2.5 km/s" (2 Observations)
   - assumption: I21/I10 = 0.7; alpha = 4.36 Msun/(K km/s pc^2)  
  > "Assuming an intensity ratio of $I_{21}$/$I_{10}$ 0.7 (e.g. (cite: BraineCombes)), and a standard CO-to-H$_2$ conversion factor $\alpha = 4.36 M_\odot/(K km/s pc^2)$" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Blind and Halpha-guided search for CO**: GILDAS detection assessment at >5 sigma in 121 cubes; spectra extracted at 13 Halpha regions  
  > "We searched in an automatic way for CO (2-1) emission with an SNR of more than 5 $\sigma$ in each of the 121 cubes" (3 Results)
   - software: GILDAS
   - fitting: _not stated_
   - validation: compared hints with other tracers; Gaussian noise check via moment 0 pixel histogram  
  > "The plot shows no obvious irregularity or departure from a Gaussian, revealing no problem with the cleaning or reduction." (3.1 Matched Filter Technique)
3. **Stack CO spectra by HI velocity**: Shift each 1.5" spectrum by HI first-moment velocity and average where HI integrated intensity >50 mJy/beam km/s; same on HI cube  
  > "Then we averaged all spectra, where the HI integrated intensity was above a certain threshold, which was 50 mJy/beam $\times$ km/s." (3.2 Stacking)
   - software: GILDAS
   - assumption: same conversion factor as in Observations  
  > "Adopting the conversion factor described in section [2](#sec:obs)" (3.2 Stacking)
   - fitting: _not stated_
   - validation: _not stated_
4. **Place limits on Kennicutt-Schmidt diagram**: SFR from FUV+24um (Leroy08) and Halpha (Kennicutt & Evans 2012) over 200 pc apertures; Sigma_H2 upper limits averaged over 200 pc  
  > "Over an aperture of 200 pc size around the two strongest HII regions, we find an SFR of 3 $\times$ 10$^{-4}$ and 3.6 $\times$ 10$^{-4}$ M$_{\odot}$yr$^{-1}$." (4.1 Star formation diagram)
   - assumption: R21=0.7; X_CO = 2e20 cm^-2/(K km/s) with helium; Sigma_H2 = 4.2 I_1-0  
  > "The standard CO-to-H$_2$ conversion ratio of $X_{CO}$ = 2 10$^{20}$ cm$^{-2}$ /(K km s$^{-1}$) is adopted" (4.1 Star formation diagram)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration  
  > "The data were calibrated using the CASA reduction package." (2 Observations)
- **GILDAS** : cleaning, cube analysis, detection assessment, stacking  
  > "The calibrated 121 uv-tables were subsequently exported to GILDAS where the cleaning and the cube analysis were performed." (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 3 sigma integrated-flux upper limit per beam (15 km/s width) | 0.180 | not stated | Jy km/s | 1 | The 3$\sigma$ upper limit of the integrated emission is therefore 0.180 Jy km/s. |
| H2 mass upper limit per beam | 1.5e4 | not stated | Msun | 1 | this corresponds to $M(H_2) = 1.5  10^4 M_\odot$ |
| Stacked CO(2-1) mean integrated flux | 0.85 | not stated | mJy km/s | 3 | When properly reduced, the average integrated flux is 0.85 mJy km/s. |
| Total H2 mass from stack over 4x2 kpc | 2e6 | not stated | Msun | 3 | therefore would represent a total mass of 2 x 10$^6$ M$_\odot$ over the whole mapped region |
| Total HI mass over region | 7.0e7 | not stated | Msun | 3 | this gives a total HI mass of 7.0 x 10$^7$ M$_\odot$ over the same region. |
| M(H2)/M(HI) | <3e-2 | not stated | dimensionless | 3 | The mass ratio between the molecular and atomic gas is then M(H$_2$) /M(HI) = 3 $\times$ 10$^{-2}$ or below. |
| Molecular depletion time upper limit | <3e8 | not stated | yr | 4 | t$_{dep} <$ 3 10$^8$ yr |

## Qualitative findings

- No significant CO(2-1) detected in the XUV disk; 14 >5 sigma hints have no counterparts and are considered false; only a tentative 3.5 sigma stacked detection.  
  > "They are therefore considered as false detections." (Conclusions)

## Claim tuples

- H: GMCs are detectable in the M83 XUV disk where UV and HI are present | E: ALMA CO(2-1) mosaic, blind and Halpha-guided searches | R: No detections above 3 sigma at Halpha regions; blind hints are spurious | F: Dearth of CO emission; GMC-mass limits ~1e4 Msun versus expected ~1e6 | **supported**
- H: Stacking on HI velocity reveals faint molecular gas | E: Velocity-aligned stack | R: 3.5 sigma hint, FWHM 14 km/s, H2/HI < 3e-2 | F: Tentative low molecular fraction | **partially**
- H: Low metallicity explains missing CO | E: Compare half-solar metallicity with X_CO scaling | R: Slightly higher X_CO would still give >8 sigma detection | F: Metallicity alone insufficient; strong FUV and small clouds (CO-dark gas) likely | **partially**

## Reasoning

- Why this data: Regions chosen at UV and HI peaks beyond r25, as for M63 where CO was detected  
  > "These selection criteria were used for the M63 XUV disk (NGC 5055), and led to a CO detection" (2 Observations)
- Why this method: _not stated_
- Alternative: Averaging all pixels gave no signal, attributed to velocity dilution by HI velocity gradient  
  > "Averaging all pixels of the map has not given any signal" (3.2 Stacking)
- How they decided it was enough: _not stated_
- Limitation (authors): FUV resolution of 100 pc prevents knowing radiation field per cloud  
  > "so we cannot know exactly the radiation felt by each cloud" (4.2 The dearth of CO emission in the outer disc of M83)
- Caveat (inferred, ours): Stacked detection is only 3.5 sigma with no baseline subtraction and a poorly defined 'properly reduced' flux
- Caveat (inferred, ours): Very short integration (10.8 s per pointing); mass conversions assume standard alpha and R21
- Caveat (inferred, ours): Dark-CO interpretation is untested without C+ or dust data

## Reproducibility

- Data public (paper): Data cited by ALMA project code in acknowledgements; Cycle 2 data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00861.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and calibration details
- Missing: GILDAS scripts and clean parameters
- Missing: THINGS HI cube and Subaru Halpha data must be obtained separately
- Missing: Stacking parameters
- Data volume (inferred): ~10-50 GB raw for a single 1-hour 121-pointing mosaic
- Score (inferred): 3/5, Data public and the approach is simple, but GILDAS parameters, calibration and stacking details are missing.
- Rediscovery candidate: no, Results are mostly upper limits and the recipe lacks detail on imaging and stacking.

## Links

- Method: (cite: Vio16) (Matched filter technique and false detection probability)
- Companion: (cite: Dessauges) (CO in M63 XUV disk with the same selection criteria)
- Related: THINGS
- Related: GALEX

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
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
  "facts": 70,
  "stated": 37,
  "rate": 0.529
 },
 "evidence_ok": true
}
```
