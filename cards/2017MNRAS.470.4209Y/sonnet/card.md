# ALMA and VLA observations of emission from the environment of Sgr A*

`2017MNRAS.470.4209Y` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Yusef-Zadeh, F. | arXiv: 1706.02750 | DOI: 10.1093/mnras/stx1439

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, agn_and_quasars
- Question: What mm/radio emission (stars, magnetar, halo, outflow features) surrounds Sgr A*, and is there a positional shift of Sgr A* between 44 and 226 GHz?  
  > "identify a new 2.5 ′′ × 1.5 ′′ halo of mm emission centered on Sgr A*." (abstract); "we determine the peak position of Sgr A* at 226 GHz by registering the accurate positions of near-IR identified stars detected at 44 and 226 GHz" (1 INTRODUCTION)
- Target **Sgr A* and inner 20 arcsec of the Galactic center**: coordinates 17h45m40.040s, -29d00m28.2s (ALMA pointing center)  
  > "The pointing center of ALMA observations was set at α, δ( J2000) = 17 h 45 m 40 s .040, −29 ◦ 00 ′ 28 ′′ .2." (3.5 Near-IR and Millimeter Astrometry); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2015.A.00021.S
- bands: _not stated_
- frequencies and spectral setup: four spectral windows centered at roughly 216.2, 218.0, 231.9, 233.7 GHz  
  > "The spectral windows were centered at roughly: 216.2 GHz, 218.0 GHz, 231.9 GHz, and 233.7 GHz." (2.1 Radio and Millimeter Data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 226 GHz combined image 0.38″ × 0.27″ (PA=−79°)  
  > "A 226 GHz image of the mini-spiral with spatial resolution of 0.38 ′′ × 0.27 ′′ and PA=−79 ◦ ." (Figure 1 caption)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2016 July 12 and 18  
  > "Observations were made on July 12 and 18, 2016" (2.1 Radio and Millimeter Data)
- pi or archival as stated: Director's discretionary time  
  > "radio and mm observations were obtained as part of the director’s discretionary time given to us to join the observing campaign." (2.1 Radio and Millimeter Data)
- Other facility **VLA (program 16A-419)**: B-array Q-band 44 GHz continuum, simultaneous  
  > "We carried out VLA B-array observations (program 16A-419) in the Q (7mm) and Ka (9mm) bands" (2.1 Radio and Millimeter Data)
- Other facility **VLT NACO**: H-band AO imaging 2016 July 12  
  > "It consists of observations in the H −band with the S27 camera." (2.2 VLT Data)
- Other facility **Chandra**: 1.5-7 keV X-ray image (private communication) for comparison  
  > "an X-ray 1.5-7 keV image in red taken with Chandra (D. Haggard, private communication)" (Figure 1 caption)
- External data: Near-IR extinction map from star counts  
  > "We also present the extinction map of the inner 30 ′′ derived from star counts in the near-IR" (2.2 VLT Data) [from Schödel et al. (2010)]
- External data: S-star orbital parameters used to predict positions  
  > "by using orbital parameters derived from near-IR observations (Gillessen et al. 2016)" (3.3 Search for Radio and mm Emission from the S stars) [from Gillessen et al. 2016]

## Processing

### Calibration

- pipeline or manual: Editing and calibration with OBIT  
  > "Editing and calibration of the data were carried out with OBIT (Cotton 2008)" (2.1 Radio and Millimeter Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (flux); NRAO 530 for phase/amplitude  
  > "Titan was initially used in ALMA observations (project code 2015.A.00021.S.) as the flux calibrator and NRAO 530 was observed periodically" (2.1 Radio and Millimeter Data)
- flux scale uncertainty: _not stated_
- self calibration: Phase and amplitude self-cal on Sgr A* (VLA); self-calibration gains applied to ALMA  
  > "A phase and amplitude self-calibration procedure was applied to all data using the bright radio source Sgr A*." (2.1 Radio and Millimeter Data)

### Imaging

- task: OBIT and CASA used to construct images; spectral windows averaged  
  > "We used OBIT (Cotton 2008) and CASA to construct radio and mm images." (2.1 Radio and Millimeter Data)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: 44 GHz image with uv range >100 kλ  
  > "constructed by limiting the uv range to greater than 100 kλ" (Figure 3 caption)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Two epochs combined after scaling variable Sgr A* flux  
  > "the images were combined after scaling the variable flux of Sgr A* during the two epochs of observations." (2.1 Radio and Millimeter Data)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- _not stated_ [from Schödel et al. (2010)]

### Not stated but needed to reproduce (our reading)

- Weighting/robust, cell size, image size, deconvolver and masking for ALMA imaging
- CASA/OBIT versions
- ALMA array configuration, baselines, on-source time
- Flux scale uncertainty and Sgr A* flux scaling factors between epochs
- Mechanism for fibril significance and noise levels
- Distance to Galactic center and parameters for synchrotron/equipartition estimates

## Analysis recipe

1. **Calibrate and image ALMA/VLA data**: OBIT calibration, self-calibration, imaging with OBIT/CASA, epochs combined  
  > "We used OBIT (Cotton 2008) and CASA to construct radio and mm images." (2.1 Radio and Millimeter Data)
   - software: OBIT, CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure source positions, fluxes and spectral indices**: Background-subtracted 2D Gaussian fits; spectral index between 44 and 226 GHz using second ALMA epoch and first VLA epoch  
  > "The positions and the sizes of radio sources are determined from background-subtracted Gaussian fit to the individual radio sources." (3.2 Compact Stellar Sources at 226 GHz)
   - software: AIPS
   - fitting: 2D Gaussian; positional accuracy from quadrature sum of RA and Dec errors  
  > "The positional accuracy is determined from quadrature sum of errors of the right ascension and declination values from 2D Gaussian fits" (3.2 Compact Stellar Sources at 226 GHz)
   - validation: _not stated_
3. **Register radio, mm and near-IR frames and measure Sgr A* shift**: Linear-term astrometric solution using common sources with IDL solve-astro; VLT image shifted  
  > "The astrometry was solved with the IDL solve-astro routine from ASTROLIB." (3.5 Near-IR and Millimeter Astrometry)
   - software: IDL ASTROLIB, StarFinder
   - assumption: Ionized-wind sources symmetric at 44 and 226 GHz (no optical depth effect)  
  > "This positional shift estimate assumes that the sources of ionized winds are symmetrical at 44 and 226 GHz" (3.5 Near-IR and Millimeter Astrometry)
   - fitting: _not stated_
   - validation: _not stated_
4. **Interpret halo as synchrotron emission**: Order-of-magnitude estimates of bremsstrahlung, equipartition field, luminosity and cooling time vs X-ray  
  > "The millimeter emission could, however, be produced by synchrotron emission from relativistic electrons in equipartition with a ∼ 1.5 mG magnetic field." (4.1 Low Extinction Millimeter Halo)
   - assumption: X-ray gas n_e ~150 cm^-3, T ~3e7 K  
  > "n e ∼ 150 cm −3 and T ∼ 3 × 10 7 K" (4.1 Low Extinction Millimeter Halo)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **OBIT** : Editing, calibration and imaging  
  > "Editing and calibration of the data were carried out with OBIT (Cotton 2008)" (2.1 Radio and Millimeter Data)
- **CASA** : Imaging and calibration of data  
  > "After calibrating the data using CASA and applying self-calibration gains" (3.5 Near-IR and Millimeter Astrometry)
- **StarFinder** : Stellar positions and fluxes in NACO images  
  > "Stellar positions and fluxes were extracted with the StarFinder package (Diolaiti et al. 2000)." (2.2 VLT Data)
- **AIPS** : Gaussian fitting of near-IR positions  
  > "The positions in the near-IR images were measured via Gaussian fitting in AIPS." (3.5 Near-IR and Millimeter Astrometry)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Halo integrated flux at 226 GHz | 81 | not stated | mJy | 2 | The integrated flux is 81 mJy over an area of 9.7 square arcsecond. |
| Sgr A* spectral index 44-226 GHz | 0.56 | 0.00004 | dimensionless | 2 | 1 Sgr A* 40.0383 28.0690 0.00 0.00 3 × 0 (31) 1536.400 ± 0.052 0.56 ± 0.00004 |
| Magnetar spectral index | -0.21 | 0.10 | dimensionless | 2 | -0.21±0.10 |
| Magnetar 226 GHz flux | 5.8 (abstract); integrated 4.699 ± 1.290 in Table 2 | 1.290 | mJy | 2 | We also detect a 5.8 mJy source at 226 GHz coincident with the magnetar SGR J1745-29 |
| Sgr A* 226 GHz shift from 44 GHz position | 11.53 mas NE (3.37 mas E, 11.03 mas N) | 0.23 mas | mas | 3 | thus the centroid of Sgr A* at 226 GHz is shifted by 11.53 ± 0.23 mas NE of the radio position at 44 GHz. |
| Equipartition magnetic field | ~1.5 | not stated | mG | 4 | equipartition with a ∼ 1.5 mG magnetic field |
| mm luminosity of halo | 1.4e33 | not stated | erg/s | 4 | The luminosity in the mm is 4π d 2 ν S ν ∼ 1.4 × 10 33 erg s −1 |

## Qualitative findings

- Eight near-IR identified stars detected at 226 GHz; six have ionized-wind spectra, IRS 3 and IRS 7SW have steep spectra  
  > "The remaining eight sources are stellar, six of which have spectra consistent with ionized winds." (3.2)
- Tentative radial fibrils of mm emission seen  
  > "Figure 7a points to seven fibrils that are tentatively detected" (3.6)

## Claim tuples

- H: Is there extended mm emission near Sgr A* coinciding with X-ray gas and an extinction minimum? | E: Compared 226 GHz images with Chandra X-ray and near-IR extinction map | R: 2.5″×1.5″ halo, 81 mJy, coincident with diffuse X-ray and low extinction | F: Halo is synchrotron emission, with an outflow creating a dust cavity | **supported**
- H: Does Sgr A* peak shift between 44 and 226 GHz? | E: Registered ALMA and VLA images using stars detected at both | R: 11.53 ± 0.23 mas NE shift | F: Shift detected; origin unclear, possibly contamination by a jet-like ridge | **partially**
- H: Are the stellar radio/mm sources winds or photospheres? | E: Spectral indices between 44 and 226 GHz | R: Most consistent with ionized winds; IRS 3 and IRS 7SW steep | F: Mixed populations | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Thermal dust and bremsstrahlung ruled out for the halo emission  
  > "Thermal continuum from dust can also be ruled out because of the halo’s extinction deficit of 0.5 magnitudes at H-band" (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Fibril detection is tentative and needs sensitive confirmation  
  > "sensitive measurements are clearly needed to confirm the tentative detection of fibrils described here." (3.6)
- Caveat (inferred, ours): Halo and fibrils could be imaging artifacts of bright Sgr A* and mini-spiral deconvolution; no robustness tests shown
- Caveat (inferred, ours): Positional shift uncertainty ignores absolute astrometric and scattering systematics
- Caveat (inferred, ours): Energetics are rough estimates without error analysis

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Calibration scripts and OBIT settings
- Missing: Epoch flux scaling factors
- Missing: Chandra image is private communication
- Data volume (inferred): tens of GB (two ALMA band 6 epochs)
- Score (inferred): 3/5, ALMA project code given, but calibration/imaging parameters largely missing.
- Rediscovery candidate: no, Imaging recipe incomplete and results depend on non-public VLA/VLT/Chandra data and OBIT workflows.

## Links

- Method: Cotton 2008 (OBIT software)
- Method: Schödel et al. (2010) (extinction map)
- Companion: Yusef-Zadeh et al. 2016 (radio stars in inner 30″ of Sgr A*)

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
  "facts": 71,
  "stated": 32,
  "rate": 0.451
 },
 "evidence_ok": true
}
```
