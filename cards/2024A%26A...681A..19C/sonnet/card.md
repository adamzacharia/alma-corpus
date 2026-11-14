# Disk Evolution Study Through Imaging of Nearby Young Stars (DESTINYS): HD 34700 A unveils an inner ring

`2024A&A...681A..19C` | Astronomy and Astrophysics 2024 | first author: Columba, G. | arXiv: 2310.16873 | DOI: 10.1051/0004-6361/202347109

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks
- Question: What is the multi-wavelength morphology and dust scattering properties of the HD 34700 A circumbinary disk (inner ring, outer ring, spirals), and what physical mechanisms could explain them?  
  > "We study the rings and spiral arms morphology and the scattering properties of the dust. We discuss the possible causes of all the observed features." (abstract)
- Target **HD 34700 A (and B)**: coordinates RA 05:19:41.41, Dec +05:38:42.80 (J2000)  
  > "| Distance | $350.5\ (\pm 2.5)$ pc | 1 |" (Table 1); "| R.A. (J2000) | 05:19:41.41 | 1 |" (Table 1); z/distance 350.5 (±2.5) pc  
  > "| Distance | $350.5\ (\pm 2.5)$ pc | 1 |" (Table 1); "| R.A. (J2000) | 05:19:41.41 | 1 |" (Table 1); distance from Gaia DR3 (reference 1 in Table 1)  
  > "| Distance | $350.5\ (\pm 2.5)$ pc | 1 |" (Table 1); "| R.A. (J2000) | 05:19:41.41 | 1 |" (Table 1)

## Data provenance

- ALMA projects: 2021.1.01705.S
- bands: Band 6 (240 GHz, 1.25 mm)  
  > "The ALMA observations were taken in ALMA Band 6 (240 GHz, 1.25 mm) on 21 August 2022" (2.3 ALMA observations)
- frequencies and spectral setup: broad continuum coverage plus one spectral window on the CO J=2-1 line, imaged at 0.65 km/s  
  > "The spectral window was imaged channel by channel (0.65 km s$^{-1}$)" (2.3 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 1200 m  
  > "The baseline lengths ranged from 15 m to 1200 m." (2.3 ALMA observations)
- angular resolution: continuum beam 0.41"x0.28" PA -64°; CO beam 0.52"x0.48" PA -61°  
  > "The beam size is $0.41\ensuremath{''}\times0.28\ensuremath{''}$ at a PA of -64° and the rms is 0.13 mJy beam$^{-1}$." (2.3 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 1.5 minutes  
  > "The integration time on source was only 1.5 minutes in moderate weather conditions" (2.3 ALMA observations)
- observing dates: 21 August 2022  
  > "The ALMA observations were taken in ALMA Band 6 (240 GHz, 1.25 mm) on 21 August 2022" (2.3 ALMA observations)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230.538 GHz)
- Other facility **VLT/SPHERE (IRDIS, IFS, ZIMPOL)**: Polarimetric and total-intensity scattered-light images in H, K1/K2, YJH and Halpha  
  > "HD 34700 A was observed with SPHERE, the Spectro-Polarimetric High-contrast Exoplanet REsearch facility" (2.1 SPHERE observations)
- Other facility **LBT/LMIRCam**: L' band images, 3.22 h  
  > "with a final scientific exposure time of 3.22 h (0.81 s each frame)" (2.2 LBT observations)
- External data: Distance 350.5 pc  
  > "the latest estimate place HD   34700   A at distance of 350.5 pc" (1 Introduction) [from Gaia Collaboration DR3 (cite: GaiaCollab2022:DR3)]

## Processing

### Calibration

- pipeline or manual: CASA calibration with quasar calibrators, then self-calibration  
  > "to first remove atmospheric and instrumental effects using the quasar calibrators. We then self-calibrated the data to increase the signal-to-noise ratio." (2.3 ALMA observations)
- casa version: CASA 6.2.1  
  > "version 6.2.1, to first remove atmospheric and instrumental effects using the quasar calibrators" (2.3 ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "The continuum image was produced using the *tclean* task on all spectral channels other than the CO window." (2.3 ALMA observations)
- deconvolver: _not stated_
- weighting robust: continuum Briggs robust -0.5; CO cube robust +0.5  
  > "produced with Briggs robust weighting parameter $-0.5$ and corrected for primary beam attenuation" (2.3 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied to continuum  
  > "corrected for primary beam attenuation" (2.3 ALMA observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 0.13 mJy/beam continuum; 4.3 mJy/beam CO channels  
  > "with an rms of 4.3 mJy beam$^{-1}$" (2.3 ALMA observations)

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals and number of rounds
- Flux, bandpass and phase calibrator names
- Cell size, image size, clean threshold and mask
- Channel selection for continuum and the CO window width
- Continuum subtraction for the CO cube
- bettermoments method and clipping parameters for the velocity map
- Number of spectral windows and bandwidth

## Analysis recipe

1. **Image continuum and CO cube**: tclean on non-CO channels for continuum; channel-by-channel CO imaging  
  > "The continuum image was produced using the *tclean* task on all spectral channels other than the CO window." (2.3 ALMA observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure mm-continuum asymmetry and fluxes**: Fluxes of A and B measured; PA of 95% peak intensity from the star  
  > "We measured the mm-continuum integrated fluxes for HD 34700 A and B to be of 9.1 mJy and 4.0 mJy respectively" (3.4 Millimetre-dust asymmetry)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive CO velocity map and gas PA**: Peak-velocity map with bettermoments, masked at 5 sigma; straight-line fit of peak velocity coordinates  
  > "We estimate for the gas disk a position angle of $PA_\mathrm{gas} = \ang{93 \pm 2}$, from a straight line fit of the peak velocity coordinates with `scipy.curve_fit`." (3.5 Gas velocity)
   - software: bettermoments, scipy
   - fitting: scipy.curve_fit line fit  
  > "from a straight line fit of the peak velocity coordinates with `scipy.curve_fit`" (3.5 Gas velocity)
   - validation: _not stated_

## Software

- **CASA** 6.2.1: ALMA calibration, self-calibration and imaging  
  > "version 6.2.1, to first remove atmospheric and instrumental effects using the quasar calibrators" (2.3 ALMA observations)
- **bettermoments** : velocity of peak emission map from CO cube  
  > "using the `bettermoments` package (cite: Teague&Foreman2018) to study the gas kinematics" (3.5 Gas velocity)
- **emcee** : MCMC fits of scattering phase function (scattered-light data)  
  > "We used the `emcee` module (cite: emcee2013) to perform our MCMC runs" (3.6.2 Procedure)
- **IRDAP** : IRDIS polarimetric reduction  
  > "The data were reduced with the IRDAP tool" (2.1.1 IRDIS polarised data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| mm-continuum flux HD 34700 A | 9.1 | 0.13 (rms) | mJy | 2 | 9.1 mJy and 4.0 mJy respectively, with a rms uncertainty of 0.13 mJy |
| mm-continuum flux HD 34700 B | 4.0 | 0.13 (rms) | mJy | 2 | 9.1 mJy and 4.0 mJy respectively, with a rms uncertainty of 0.13 mJy |
| PA of mm peak | -48 | 11 | deg | 2 | we find a $PA_\mathrm{mm} \sim \ang{-48 \pm 11}$ measuring the angle of the 95% peak intensity seen from the central star |
| gas disk PA of A | 93 | 2 | deg | 3 | $PA_\mathrm{gas} = \ang{93 \pm 2}$ |
| inner ring inclination | 39.7 | 2.0 | deg | 0 | / LoS inclination     /  $39.7\pm2.0$ (°)   /     / |
| inner ring asymmetry parameter g | 0.41 | 0.01 | dimensionless | 0 | positive asymmetry parameter of $g_\mathrm{in} = 0.41 \pm 0.01$ |

## Qualitative findings

- Disk around B rotates clockwise, opposite to A, with a very different semi-major axis PA; no gas streamers between A and B  
  > "Interestingly, the disk around B rotates clockwise, opposite to the disk around A, and with a very different semi-major axis PA." (3.5 Gas velocity)

## Claim tuples

- H: Does HD 34700 A host a ring inside the known outer ring? | E: ZIMPOL Halpha polarimetry and ellipse fits | R: Inner ring 65-120 au, PA 87°, inclination ~40° | F: New inner ring with different dust properties from outer ring | **supported**
- H: Do A and B discs share kinematics? | E: ALMA CO J=2-1 velocity maps | R: Opposite rotation senses and misaligned PAs | F: A and B likely formed in different parts of a fragmented cloud | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA CO data have only moderate resolution, so velocity perturbations at the mm-dust peak cannot be excluded  
  > "at least at the moderate resolution of these data" (3.5 Gas velocity)
- Caveat (inferred, ours): ALMA data are a 1.5-minute snapshot with limited sensitivity and resolution
- Caveat (inferred, ours): Scattering-phase-function grain-size inference depends on assumed geometry with zero flaring
- Caveat (inferred, ours): Mm-dust PA error and its link to the ring centre offset are speculative

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Self-calibration and imaging details
- Missing: Custom Python code for fits not released
- Data volume (inferred): ~10-50 GB for the ALMA snapshot MS
- Score (inferred): 3/5, ALMA part is small with several unstated settings; the main results rely on non-ALMA SPHERE data.
- Rediscovery candidate: no, ALMA role is minor and the recipe is incomplete.

## Links

- Method: Teague & Foreman-Mackey 2018 (cite: Teague&Foreman2018) (bettermoments package)
- Companion: Benac+2020 (cite: Benac+2020:HD34700) (previous SMA observations of HD 34700 A and B)
- Companion: Ginski+2020 (cite: Ginski+2020:destinys) (DESTINYS program)
- Related: DESTINYS

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
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
  "stated": 29,
  "rate": 0.475
 },
 "evidence_ok": true
}
```
