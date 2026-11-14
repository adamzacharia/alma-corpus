# Continuum and molecular emission from the inner regions of the symbiotic system R Aquarii

`2024A&A...689A.317G` | Astronomy and Astrophysics 2024 | first author: Gómez-Garrido, M. | arXiv: 2408.06033 | DOI: 10.1051/0004-6361/202348283

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, astrochemistry, stellar_physics
- Question: What do ALMA continuum, H30alpha and molecular line maps reveal about the inner regions of the symbiotic system R Aqr, and how are weak molecules distributed there?  
  > "Our aim is to study the inner regions of R Aqr based on ALMA observations of the continuum and line emission." (abstract)
- Target **R Aqr**: coordinates Band 7 centre RA 23:43:49.4962, Dec -15:17:04.720 (ICRS J2000)  
  > "In this work, we assumed a distance of 265$\pm$20 pc for our calculations, which is derived from the luminosity-period relation (cite: alcolea23)." (1 Introduction); "The ICRS coordinates for the maps at 0.9 mm are R.A.: 23:43:49.4962, Dec.: –15:17:04.720." (2 Observations); z/distance 265±20 pc  
  > "In this work, we assumed a distance of 265$\pm$20 pc for our calculations, which is derived from the luminosity-period relation (cite: alcolea23)." (1 Introduction); "The ICRS coordinates for the maps at 0.9 mm are R.A.: 23:43:49.4962, Dec.: –15:17:04.720." (2 Observations); distance from luminosity-period relation (Alcolea et al. 2023)  
  > "In this work, we assumed a distance of 265$\pm$20 pc for our calculations, which is derived from the luminosity-period relation (cite: alcolea23)." (1 Introduction); "The ICRS coordinates for the maps at 0.9 mm are R.A.: 23:43:49.4962, Dec.: –15:17:04.720." (2 Observations)

## Data provenance

- ALMA projects: 2018.1.00638.S, 2017.1.00363.S
- bands: Band 6 (1.3 mm), Band 7 (0.9 mm), Band 9 (0.45 mm)  
  > "We explored the emission of this object in the ALMA Bands 6, 7, and  9, corresponding to 1.3, 0.9, and 0.45 mm wavelengths" (2 Observations)
- frequencies and spectral setup: 0.282 MHz/channel at 1.3 and 0.9 mm (0.38 and 0.25 km/s), 0.564 MHz/channel at 0.45 mm; spectral windows 25, 27, 29, 31 per band  
  > "we reached a spectral resolution of 0.282 MHz per channel at 1.3 and 0.9 mm  and 0.564 MHz per channel at 0.45 mm" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Band 6 C43-6 (low res) and C43-10 (high res); Band 7 C43-8; Band 9 C43-7  
  > "Band 6 - Low resolution  | June 2019      | 200                    | 23:43:49.5004 | -15:17:04.782 | C43-6" (Table 2)
- baselines: _not stated_
- angular resolution: 20-250 mas depending on band, configuration and weighting  
  > "Angular resolutions between 20 and 250 mas were attained depending on the observed frequency, array configuration, and mapping weighting." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: noise ~0.1, 2, 10 mJy in Bands 6, 7, 9 clean maps  
  > "Noise levels of $\sim$0.1, 2, and 10 mJy were found in the clean maps on Bands 6, 7, and 9, respectively." (2 Observations)
- time on source: _not stated_
- observing dates: Band 6 June and September 2019; Band 7 November 2017; Band 9 August 2019  
  > "The observations of Band 6 were carried out in June and September 2019 with high- and low-spatial resolution, and Bands 7 and 9 were observed in November 2017 and August 2019, respectively." (2 Observations)
- pi or archival as stated: _not stated_
- Line: CO v=0 J=2-1 (230.538 GHz)
- Line: H30alpha RRL (231900.928 MHz)
- Line: SiO v=0 J=16-15 (694294.114 MHz)
- External data: Orbital parameters (period 42.4 yr, PA 95 deg, semi-major axis 57±8 mas) and predicted WD position  
  > "The derived orbital period is 42.4 yr, which is slightly shorter than previous estimations (cite: gromadzki09)." (1 Introduction) [from (cite: alcolea23)]
- External data: Photosphere extent and temperature used in model  
  > "has the extent and temperature described in (cite: bujarrabal18)" (5 Modeling) [from (cite: bujarrabal18)]
- External data: 28SiO relative abundance 6.6e-6  
  > "we assumed a relative abundance of 6.6$\cdot10^{-6}$, which is compatible with the values found in O-rich Mira-type variables (cite: massalkhi20)" (5 Modeling) [from (cite: massalkhi20)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA pipeline in CASA  
  > "The calibration of the visibilities was performed using the standard ALMA pipeline in the CASA software." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0006-0623; ~1.45 Jy (Jun 2019) and ~1.32 Jy (Sep 2019) Band 6; ~0.9 Jy Band 7; ~4.3 Jy Band 9  
  > "For the absolute flux scaling, J0006-0623 was used as a calibrator." (2 Observations)
- flux scale uncertainty: 5-8% Bands 6 and 7; ~15% Band 9  
  > "Flux uncertainties in Bands 6 and 7 are estimated to be between about 5% and 8%, while it is $\sim$15 % for Band 9." (2 Observations)
- self calibration: Continuum self-calibration in GILDAS; Band 6 SPW 31 self-calibrated on SiO v=1 J=5-4 maser  
  > "Self-calibration of the *uv* data using the continuum emission was performed by means of GILDAS." (2 Observations)

### Imaging

- task: GILDAS MAPPING  
  > "Map cleaning was performed in GILDAS using the Hogbom algorithm implemented in MAPPING." (2 Observations)
- deconvolver: Hogbom; ~4000 components first pass, 5000 final; stop at sigma_p/2  
  > "Final clean maps were obtained imposing a maximum amplitude of the absolute value of the residual map of $\sigma_{p}$/2" (2 Observations)
- weighting robust: robust weighting (value not given); natural weighting for SPW 27 and 29 in Band 6 and low-res maps  
  > "we worked to reach our best angular resolution using robust weighting." (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Line-free channels averaged and subtracted in uv data  
  > "The continuum is subtracted from the *uv* data affecting the visibilities directly." (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Band 6 high and low resolution merged  
  > "we merged both the high- and low-resolution Band 6 data to increase the S/N" (2 Observations)
- smoothing: 1.6 km/s channels for lines; 4.8 km/s for H30alpha  
  > "we resampled the *uv* tables to obtain a spectral resolution of 4.8 km s$^{-1}$, increasing the S/N." (2 Observations)
- final beam: about 25x18, 35x25, 33x28 mas (Bands 6,7,9); circular 15 and 20 mas continuum beams; 264x163 mas low-res  
  > "Beam sizes of about 25$\times$18, 35$\times$25, and 33$\times$28 mas and PAs of around 129, 56, and 83 deg were achieved for the ALMA Bands 6, 7, and  9." (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Calibration of 2017.1.00363.S data, and similar for 2018.1.00638.S  
  > "The calibration of the 2017.1.00363.S data has been described in (cite: bujarrabal18), and that of 2018.1.00638.S data was very similar, including in the choice of calibrators." (2 Observations) [from (cite: bujarrabal18)]
- 0.9 mm continuum already studied in detail, so not reanalysed  
  > "Because the high- and low-resolution continuum maps at 0.9 mm were already studied by (cite: bujarrabal18) in detail, we focused on the analysis of the observations at 1.3 and 0.45 mm." (2 Observations) [from (cite: bujarrabal18)]
- Model code similar to earlier radiative transfer codes  
  > "Our code is similar to those extensively used and described previously to model emission of gas in rotation and expansion in evolved objects (cite: gallardo21; bujarrabal17; bujarrabal21)." (5 Modeling) [from (cite: gallardo21; bujarrabal17; bujarrabal21)]

### Not stated but needed to reproduce (our reading)

- Robust parameter values
- Line-free channel ranges per spectral window
- Self-calibration solution intervals and reference components
- Cell and image sizes
- CASA and GILDAS versions
- Model code and fitting figure of merit; dust Gaussian parameters
- Band 7 flux date inconsistency (November 2018 vs 2017)

## Analysis recipe

1. **Recentre and self-calibrate uv data**: Fit continuum centroid with uv_fit and recentre all uv tables on it  
  > "The coordinates of these centroids were derived from a preliminary analysis of the *uv* tables of the continuum data using the routine *uv_fit* of the GILDAS packages" (2 Observations)
   - software: GILDAS
   - assumption: Continuum centroid approximates the Mira position  
  > "which approximately gives the position of the Mira component" (2 Observations)
   - fitting: _not stated_
   - validation: Centroid differences compared with beam size  
  > "These differences are comparable to the position accuracy and much smaller than the beam size of the low-resolution data" (2 Observations)
2. **Subtract continuum and clean maps**: uv-plane continuum subtraction then Hogbom CLEAN with two-pass stopping criteria  
  > "We completed a first cleaning using a maximum number of clean components of $\sim$4000." (2 Observations)
   - software: GILDAS
   - assumption: Continuum constant within each spectral window (spectral index 2, <1% variation)  
  > "assuming a spectral index of  two, differences in the intensity of the continuum emission smaller than 1 % are expected" (2 Observations)
   - fitting: _not stated_
   - validation: Checked line-free channels for residuals and no overcleaning  
  > "We checked that the final clean maps do not show overcleaned regions." (2 Observations)
3. **Measure continuum fluxes and spectral index**: Compare central compact component intensities at 1.3 and 0.45 mm  
  > "By comparing the intensities measured for the compact central component of the high-resolution continuum maps at 1.3 and 0.45 mm, we estimated a spectral index of 1.88." (4.1 Continuum maps)
   - fitting: _not stated_
   - validation: _not stated_
4. **Model compact molecular emission (SiO v=0 J=16-15 example)**: LTE ray-tracing model of expanding oblate shell plus in-falling spherical shell with dust and photosphere continuum, continuum subtracted, convolved with beam  
  > "Our model nebula consists of an oblate ellipsoidal shell in radial expansion for the emission and an in-falling spherical shell for the absorption" (5 Modeling)
   - parameter: Power-law density and temperature; constant velocity  
  > "we assumed a constant radial velocity to simplify our calculations." (5 Modeling)
   - assumption: LTE; optically thin Gaussian dust; SiO abundance 6.6e-6; distance 265 pc  
  > "We assumed local thermodynamic equilibrium (LTE) to obtain the coefficients of absorption and emission in each point of the circumstellar shells." (5 Modeling)
   - fitting: Best fit found by manual variation of parameters  
  > "We found the best-fit model by manually varying the parameters to adjust the synthetic maps to the observations." (5 Modeling)
   - validation: Qualitative comparison with channel maps of other lines; size uncertainty <20% (expanding), ~50% (in-falling)  
  > "We estimated that the uncertainty in the determination of the sizes of the expanding shell and in-falling component is smaller than 20% and $\sim$50%, respectively." (5 Modeling)

## Software

- **CASA** : Standard ALMA pipeline calibration  
  > "The calibration of the visibilities was performed using the standard ALMA pipeline in the CASA software." (2 Observations)
- **GILDAS (MAPPING, uv_fit)** : Self-calibration, centroid fitting, cleaning and imaging  
  > "Map cleaning was performed in GILDAS using the Hogbom algorithm implemented in MAPPING." (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum spectral index of central component (1.3-0.45 mm) | 1.88 | not stated | dimensionless | 3 | we estimated a spectral index of 1.88 |
| Central compact continuum flux at 1.3 and 0.45 mm | 30 and 220 | not stated | mJy | 3 | The flux of this central component is 30 and 220 mJy at 1.3 and 0.45 mm, respectively. |
| H30alpha velocity range | -80.6 to 29.8 | not stated | km/s | 0 | This atomic line spans a velocity range between –80.6 and 29.8 km s$^{-1}$ |
| Expanding shell outer radius (equatorial) and expansion velocity | 1.6e14 cm; 9.0 km/s | <20% | cm; km/s | 4 | R$_{o.equ}$ (cm)         / 1.6$\times$10$^{14}$ / 6$\times$10$^{13}$ |
| In-falling component velocity | -17 | not stated | km/s | 4 | we accurately derived velocities of 9 and $-$17 km s$^{-1}$ for the expanding and in-falling components, respectively. |
| Position angle of expanding shell projection | 105 | not stated | deg | 4 | the projection of the expanding shell is inclined at a PA of 105° |

## Qualitative findings

- H30alpha is displaced west of the 1.3 mm continuum peak, tracing the jet and WD surroundings  
  > "the emission of H30$\alpha$ is slightly displaced to the west of the continuum emission" (4.2 H30alpha maps)

## Claim tuples

- H: Does the high-resolution 1.3 mm continuum trace the innermost jet near the WD? | E: Compare 1.3 mm high-res continuum with predicted WD position | R: Emission extends toward predicted WD position | F: Extension is ionized gas around the WD and jet base; cannot be firmly confirmed | **partially**
- H: Do weak molecules survive only close to the AGB star? | E: Map many lines and model SiO with shell model | R: Best-fit shell outer radius ~1e14 cm | F: Weak species confined to intra-orbital regions | **supported**
- H: What causes the central absorption at positive velocities? | E: Model with cool in-falling shell | R: Reproduces absorption | F: Consistent with in-falling gas but photospheric motion cannot be excluded | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): In-falling component size is not conclusive  
  > "Therefore, the obtained result concerning the size of the in-falling component is not conclusive." (5 Modeling)
- Caveat (inferred, ours): Model fit is manual with no goodness-of-fit metric
- Caveat (inferred, ours): Distance uncertain (parallax discrepant)
- Caveat (inferred, ours): Continuum subtraction affects optically thick line centres

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Model code not released
- Missing: Imaging parameters incomplete
- Missing: Self-calibration details
- Data volume (inferred): Several hundred GB raw across three bands
- Score (inferred): 4/5, Data archival but GILDAS imaging parameters and custom model not specified.
- Rediscovery candidate: no, Recipe incomplete and model is custom and manually tuned.

## Links

- Method: (cite: bujarrabal18) (Calibration and continuum analysis)
- Method: (cite: bujarrabal21) (CO modelling and chemistry)
- Companion: (cite: bujarrabal21) (Same ALMA data, CO emission)

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 43,
  "rate": 0.623
 },
 "evidence_ok": true
}
```
