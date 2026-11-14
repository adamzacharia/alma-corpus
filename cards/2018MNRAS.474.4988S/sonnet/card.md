# A disrupted molecular torus around Eta Carinae as seen in <SUP>12</SUP>CO with ALMA

`2018MNRAS.474.4988S` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Smith, Nathan | arXiv: 1712.01362 | DOI: 10.1093/mnras/stx3050

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, stellar_physics
- Question: What is the structure, kinematics and mass of the cool molecular equatorial torus around Eta Carinae seen in 12CO 2-1, and how does it relate to the IR torus, H2 emission and the binary orbit?  
  > "These observations reveal new structural details about the cool equatorial torus located $\sim$4000 au from the star." (abstract)
- Target **Eta Carinae**: coordinates _not stated_; z/distance 2.3 kpc  
  > "0.056 pc$^2$ at the 2.3 kpc distance of $\eta$ Car; (cite: smith06)" (4 Mass estimate from CO data); distance from (cite: smith06)  
  > "0.056 pc$^2$ at the 2.3 kpc distance of $\eta$ Car; (cite: smith06)" (4 Mass estimate from CO data)

## Data provenance

- ALMA projects: 2013.1.00661.S
- bands: Band 6 (1.3 mm)  
  > "ALMA observations of $\eta$ Carinae in Band 6 (1.3 mm) were taken as part of program 2013.1.00661.S." (OBSERVATIONS)
- frequencies and spectral setup: 4 basebands: 215.7-217.6, 217.6-219.5, 229.6-231.5, 231.6-233.5 GHz; 1.3 km/s (976 kHz) resolution  
  > "The observations covered 4 basebands: 215.7$-$217.6 GHz, 217.6$-$219.5 GHz, 229.6$-$231.5 GHz, and 231.6$-$233.5 GHz." (OBSERVATIONS)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: roughly 1 arcsec; beam 1.3x0.99 arcsec, PA 67 deg  
  > "in a 1$\ensuremath{''}$3$\times$0$\ensuremath{''}$99  (P.A. = 67$^{\circ}$) beam" (OBSERVATIONS)
- max recoverable scale: _not stated_
- sensitivity: RMS 7.2 mJy per 3 km/s channel  
  > "the RMS achieved was 7.2 mJy per 3 km s$^{-1}$ channel" (OBSERVATIONS)
- time on source: _not stated_
- observing dates: 2015 January 29 and 2015 April 3 (two scheduling blocks)  
  > "Two scheduling blocks were executed on 2015 January 29 and 2015 April 3." (OBSERVATIONS)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.5 GHz)
- Other facility **HST**: near-UV image of the Homunculus for comparison  
  > "superposed on a near-UV *HST* image of the Homunculus, for reference" (OBSERVATIONS)
- External data: 8.8 and 18 micron mid-IR optical depth maps  
  > "8.8 $\mu$m and 18 $\mu$m optical depth maps" (OBSERVATIONS) [from (cite: smith03)]
- External data: High-resolution near-IR H2 2.122 micron spectra  
  > "compares it to high-resolution near-IR spectra of near-IR H$_2$ emission (cite: smith04; smith06)" (OBSERVATIONS) [from (cite: smith04; smith06)]
- External data: Inclination i=41 deg  
  > "correcting for an inclination of $i$=41$^{\circ}$; (cite: smith06)" (2.2 Near-IR H2 Emission and Kinematic Structure) [from (cite: smith06)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline, QA2 products used  
  > "Data reduction was performed using the CASA pipeline version 4.2.2 r30986, and we used the QA2-produced visibilities and images." (OBSERVATIONS)
- casa version: 4.2.2 r30986  
  > "CASA pipeline version 4.2.2 r30986" (OBSERVATIONS)
- pipeline version: _not stated_
- archive products used as is: QA2-produced visibilities and images  
  > "we used the QA2-produced visibilities and images" (OBSERVATIONS)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust 0.5  
  > "Images were produced with Briggs weighting using robust factor 0.5 and a cell size of 0$\ensuremath{''}$2." (OBSERVATIONS)
- uv taper: _not stated_
- cell size: 0.2 arcsec  
  > "a cell size of 0$\ensuremath{''}$2" (OBSERVATIONS)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum fit and subtracted  
  > "The continuum emission was fit and subtracted." (OBSERVATIONS)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.3x0.99 arcsec, PA 67 deg  
  > "1$\ensuremath{''}$3$\times$0$\ensuremath{''}$99  (P.A. = 67$^{\circ}$) beam" (OBSERVATIONS)
- final rms: 7.2 mJy per 3 km/s channel  
  > "the RMS achieved was 7.2 mJy per 3 km s$^{-1}$ channel" (OBSERVATIONS)

### Inherited from earlier work

- Distance 2.3 kpc and inclination 41 deg  
  > "correcting for an inclination of $i$=41$^{\circ}$; (cite: smith06)" (2.2 Near-IR H2 Emission and Kinematic Structure) [from (cite: smith06)]
- Standard X_CO of 2e20 from Bolatto et al.  
  > "assuming the ‘average’ X-factor from (cite: bolatto13)" (4 Mass estimate from CO data) [from (cite: bolatto13)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum fit order
- Excitation temperature, CO column density details and CNO abundance in the LTE optically thin mass calculation
- How the 450 arcsec^2 area and moment-map clipping thresholds were defined
- Moment map velocity ranges and PV extraction width
- Number of antennas and array configuration, time on source, calibrators

## Analysis recipe

1. **Make CO maps**: Peak and integrated (0th moment) maps of 12CO 2-1 from continuum-subtracted cube  
  > "Figure [1](#fig:IR) shows maps of the peak CO emission (Fig. [1](#fig:IR)a) and the integrated line flux or 0th moment of the CO emission" (OBSERVATIONS)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with mid-IR optical depth maps and HST image  
  > "Panels (c) and (d) show the same contours of line flux from Fig. [1](#fig:IR)b, but superposed on images of the mid-IR 8.8 $\mu$m and 18 $\mu$m optical depth maps" (OBSERVATIONS)
2. **Position-velocity diagram and kinematics**: PV diagram along Homunculus major axis, flux integrated perpendicular to polar axis; compared to H2 2.122 micron spectra; deproject velocity with inclination  
  > "position-velocity diagram with the positional coordinate along the major axis of the Homunculus, and with the flux integrated in the direction perpendicular to the polar axis" (2.2 Near-IR H2 Emission and Kinematic Structure)
   - assumption: inclination 41 deg  
  > "correcting for an inclination of $i$=41$^{\circ}$" (2.2 Near-IR H2 Emission and Kinematic Structure)
   - fitting: _not stated_
   - validation: CO kinematics overlap H2 emission  
  > "the kinematic structure of the CO emission overlaps perfectly with the near-IR $H_2$ emission" (2.2 Near-IR H2 Emission and Kinematic Structure)
3. **Estimate gas mass**: X_CO conversion (2e20 and 0.4e20) and LTE optically thin CO mass with CO/H2 of 1e-4 or AGCar-based ratio  
  > "An LTE optically thin analysis leads to a total CO mass of roughly 5.9$\times$10$^{-4}$ $M_{\odot}$." (4 Mass estimate from CO data)
   - parameter: area 450 arcsec^2 (0.056 pc^2)  
  > "Averaged over a projected area on the sky of 450 arcsec$^2$ (0.056 pc$^2$ at the 2.3 kpc distance" (4 Mass estimate from CO data)
   - assumption: gas/dust temperature 140 K; CO/H2 number ratio 1e-4  
  > "we expect the gas and dust temperature (140 K) to be similar" (4 Mass estimate from CO data)
   - fitting: _not stated_
   - validation: Range of conversions compared; uncertainty dominated by CO-to-H2 conversion  
  > "Clearly the dominant uncertainty here is in the appropriate conversion of CO to H$_2$" (4 Mass estimate from CO data)

## Software

- **CASA** 4.2.2 r30986: pipeline data reduction  
  > "Data reduction was performed using the CASA pipeline version 4.2.2 r30986" (OBSERVATIONS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak redshifted radial velocity of torus | +81 | not stated | km/s | 2 | The redshifted peak of the torus has a radial velocity of about $+$81 km s$^{-1}$ |
| Deprojected expansion speed | 123 | not stated | km/s | 2 | of about 123 km s$^{-1}$ |
| Kinematic age | 170 | ±15 | yr | 2 | a kinematic age of around 170 ($\pm$15) yr |
| Peak CO brightness temperature | 12.4 | not stated | K | 1 | The peak CO brightness temperature we observe is 12.4 K |
| Average integrated surface brightness | 26 | ±0.4 | K km/s | 3 | 26 ($\pm$0.4) K km s$^{-1}$ |
| LTE optically thin CO mass | 5.9e-4 | not stated | Msun | 3 | total CO mass of roughly 5.9$\times$10$^{-4}$ $M_{\odot}$ |
| Total molecular gas mass (rough) | ~1 (range 0.2-5) | order of magnitude | Msun | 3 | we infer $\sim$1 $M_{\odot}$ as a very rough order-of-magnitude estimate |

## Qualitative findings

- CO torus is C-shaped, missing its NW near side, matching apastron direction  
  > "The missing material matches the direction of apastron in the eccentric binary system" (abstract)

## Claim tuples

- H: Is the CO torus a separate disk or part of the Homunculus walls? | E: Compared CO maps and PV diagram with mid-IR dust and H2 | R: CO matches cool dust and H2 spatially and kinematically | F: CO traces the pinched waist of the polar lobes | **supported**
- H: Is the torus azimuthally complete? | E: Mapped CO peak and moment 0 | R: C shape with gap to NW | F: Near side was disrupted, likely by the companion | **partially**
- H: How much gas mass is in the torus? | E: X-factor and LTE estimates | R: 0.2-5 Msun | F: ~1 Msun, highly uncertain | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Older pre-existing disk (Morris et al. 1999) rejected based on kinematic age  
  > "The CO emission is not tracing an older, pre-existing disk as advocated by (cite: morr99)." (2.2 Near-IR H2 Emission and Kinematic Structure)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass conversion highly uncertain; deeper observations needed for polar lobes  
  > "In any case, the correct X-factor to use is highly uncertain." (4 Mass estimate from CO data)
- Caveat (inferred, ours): Only one CO line, so no excitation or optical depth constraints
- Caveat (inferred, ours): Mass estimate relies on unconstrained X_CO and CO/H2
- Caveat (inferred, ours): Interpretation of gap origin is qualitative
- Caveat (inferred, ours): Possible missing flux from interferometric filtering not discussed

## Reproducibility

- Data public (paper): Project code and ALMA data acknowledgment given  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00661.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Moment map thresholds
- Missing: LTE assumptions (Tex, CNO abundance)
- Missing: Mid-IR and H2 data from earlier papers
- Data volume (inferred): tens of GB
- Score (inferred): 4/5, Short paper with basic imaging details, but mass calculation and map thresholds are underspecified.
- Rediscovery candidate: no, Mass analysis lacks full recipe; main results largely qualitative.

## Links

- Companion: (cite: smith03) (Mid-IR optical depth maps)
- Companion: (cite: smith06) (Homunculus geometry, distance, inclination)

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
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
  "facts": 65,
  "stated": 36,
  "rate": 0.554
 },
 "evidence_ok": true
}
```
