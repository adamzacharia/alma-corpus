# First analysis of solar structures in 1.21 mm full-disc ALMA image of the Sun

`2018A&A...613A..17B` | Astronomy and Astrophysics 2018 | first author: Brajša, R. | arXiv: 1711.06130 | DOI: 10.1051/0004-6361/201730656

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: sun
- Question: Can different solar structures (quiet Sun, active regions, prominences, inversion lines, coronal holes, coronal bright points) be identified in a 1.21 mm full-disc ALMA image, and what are their brightness temperatures relative to the quiet Sun?  
  > "The second aim is to measure the intensities (brightness temperatures) of those structures and to compare them with the corresponding quiet Sun level." (abstract)
- Target **Full solar disc, 18 December 2015**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00020.SV
- bands: Band 6 (1.21 mm, 248 GHz)  
  > "The measurement frequency/wavelength belongs to Band 6, which is one of the ten ALMA observing bands." (2 Measurements and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: single 12 m total power antenna (PM03), double circle scan  
  > "by scanning the solar disc with a 12 m single dish total power ALMA antenna (PM03) at a frequency of 248 GHz" (2 Measurements and data reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam 26 arcsec  
  > "The beam size amounts to 26 arcsec." (2 Measurements and data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: about 13 minutes  
  > "lasted for about 13 minutes" (2 Measurements and data reduction)
- observing dates: 18 December 2015, start 20:12:21 UT  
  > "The measurement started at 20:12:21 UT on December 18, 2015" (2 Measurements and data reduction)
- pi or archival as stated: CSV campaign data released as science verification data  
  > "A first part of the CSV data was recently released to the scientific community" (2 Measurements and data reduction)
- Other facility **SDO (AIA, HMI)**: EUV/UV filtergrams and magnetogram for comparison  
  > "various SDO images (a composite AIA image at 30.4 nm, 21.1 nm, and 17.1 nm; AIA filtergrams at 170 nm, at 30.4 nm, and at 19.3 nm; and a HMI magnetogram)" (2 Measurements and data reduction)
- Other facility **Cerro Tololo (NISP) Halpha**: Halpha full-disc image  
  > "in H$\alpha$ line (Cerro Tololo Observatory, NISP)" (2 Measurements and data reduction)
- Other facility **NSO SOLIS**: He I 1083 nm full-disc image  
  > "in He I 1083 nm line core (NSO SOLIS)" (2 Measurements and data reduction)

## Processing

### Calibration

- pipeline or manual: two-load method with antenna efficiency factor C = 1.16  
  > "A two-load method was used to calibrate the data" (2 Measurements and data reduction); "a correction (multiplication) factor $C$ was applied to account for the antenna efficiency: $C = 1.16$ for Band 6" (2 Measurements and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: about 5 %  
  > "The final uncertainty in the brightness temperature is about 5 % (cite: White2017)." (2 Measurements and data reduction)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: pixel about 3 arcsec  
  > "The size of a pixel is about 3 arc sec." (3 An analysis of the ALMA image and comparison with other data)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Calibration, imaging and total-power procedure, correction factor C and 5% uncertainty  
  > "More information about the measurements, calibration and imaging of the solar observations with ALMA for the single dish/total power mode can be found in the paper by (cite: White2017)." (2 Measurements and data reduction) [from (cite: White2017)]

### Not stated but needed to reproduce (our reading)

- Calibrated ALMA map file/version and exact CASA version
- Coordinates and pixel positions of the regions of interest
- Alignment procedure of ALMA map with SDO/Halpha images
- Selection of the 56 coronal bright points
- How the prominence region was extracted from Halpha

## Analysis recipe

1. **calibrate full-disc map**: Two-load calibration with efficiency factor, data reduction in CASA  
  > "Data reduction was performed using the Common Astronomy Software Applications (CASA) package" (2 Measurements and data reduction)
   - software: CASA
   - parameter: C = 1.16  
  > "$C = 1.16$ for Band 6" (2 Measurements and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **measure brightness temperatures of regions of interest**: Mean of all pixels in regions of interest; compared with quiet Sun at same radius along the equator east; AR threshold Tb>6900 K, sunspot Tb<6400 K  
  > "Brightness temperatures of various structures are calculated as the mean values of all pixels within regions of interest denoted in Fig. 1a." (3 An analysis of the ALMA image and comparison with other data)
   - parameter: QS circle radius 5 pixels at disc centre, 30 pixels elsewhere  
  > "At the solar disc center radius of the circle is 5 pixels, while for all other quiet Sun measurements it is 30 pixels." (3 An analysis of the ALMA image and comparison with other data)
   - fitting: _not stated_
   - validation: Selection criteria acknowledged as crude and arbitrary  
  > "We note that this selection criteria (for AR1 and SS) are crude and to some extent arbitrary." (3 An analysis of the ALMA image and comparison with other data)
3. **identify coronal bright points across wavelengths**: 56 CBPs identified in AIA 19.3 nm marked with boxes and overlaid on He I 1083 nm and ALMA maps; visual comparison  
  > "56 coronal bright points (only point-like structures and small loops) are identified and denoted with blue boxes." (3.5 Coronal bright points)
   - fitting: _not stated_
   - validation: Correspondence of CBPs used to test overlay/orientation precision at about 5 arcsec  
  > "this spatial precision is in the order of 5 arc sec." (3.5 Coronal bright points)

## Software

- **CASA** : data reduction  
  > "Data reduction was performed using the Common Astronomy Software Applications (CASA) package" (2 Measurements and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Central quiet Sun brightness temperature | 6040 | 70 | K | 2 | / QS / 0 / $6040 \pm  70$ / 78 / $6040 \pm 70$ / 78 / $0$ / |
| Active region AR1 excess over QS | +1010 | not stated | K | 2 | $7250 \pm 210$ / 3048 / $+1010$ |
| Sunspot deficit | -90 | not stated | K | 2 | $6080 \pm 210$ / 136 / $-90$ |
| Magnetic inversion line deficit | -170 | not stated | K | 2 | The average brightness temperature of the measured part of the inversion line has a brightness temperature 170 K below the quiet Sun level. |
| Prominence (FIL1) deficit | -110 | not stated | K | 2 | $6350 \pm 110$ / 154 / $-110$ |
| Coronal hole CH1 deficit | -50 | not stated | K | 2 | $6540 \pm 130$ / 2804 / $-50$ |
| CBPs corresponding to ALMA bright points | 82 | not stated | % | 3 | the great majority (82 %) of all coronal bright points from the EUV image corresponds to the ALMA 1.21 mm bright points |
| CBPs corresponding to He I 1083 nm dark points | 75 | not stated | % | 3 | the great majority (75 %) of all coronal bright points from the EUV image corresponds to He I 1083 nm dark points |
| Limb brightening at 1.21 mm | about 10 | not stated | % | 2 | The amount of this limb brightening is in the order of 10 % in agreement with recent results of (cite: Alissandrakis2017). |

## Qualitative findings

- Active regions are bright, sunspots dark, prominences and coronal holes barely discernible; inversion lines dark; coronal bright points appear as ALMA bright points.  
  > "Magnetic inversion lines appear as large, elongated dark structures and coronal bright points correspond to ALMA bright points." (abstract)

## Claim tuples

- H: Coronal bright points are detectable in the 1.21 mm ALMA image | E: Overlay of 56 EUV-identified CBPs on He I and ALMA maps | R: 82% match ALMA bright points, 75% match He I dark points | F: CBPs correspond almost one-to-one with ALMA bright points; overlay accurate to ~5 arcsec | **supported**
- H: Structures show characteristic brightness temperature contrasts at 1.21 mm | E: Mean Tb in regions of interest versus QS at same radius | R: AR +1010 K, SS -90 K, IL -170 K, PR -110 K, CH -50 K | F: Consistent with sparse earlier measurements | **supported**

## Reasoning

- Why this data: Day chosen for availability of other-wavelength images, especially He I 1083 nm  
  > "The observing day December 18, 2015 was chosen because of availability of images in other wavelength ranges, especially He I 1083 nm" (2 Measurements and data reduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Selection criteria for AR and sunspot are crude and arbitrary; prominence result depends on ~5 arcsec overlay precision  
  > "The reliability of this result depends on the overlying precision (in the order of 5 arc sec)" (3.3 Prominences on the solar disc)
- Caveat (inferred, ours): Single image, single day, single structure per class
- Caveat (inferred, ours): Visual CBP matching is subjective, no statistics or control sample
- Caveat (inferred, ours): Differences of 50-100 K are comparable to the quoted scatter

## Reproducibility

- Data public (paper): CSV data released to the community via ALMA science verification page  
  > "A first part of the CSV data was recently released to the scientific community" (2 Measurements and data reduction)
- Products in archive: _not stated_
- Missing: Region-of-interest coordinates
- Missing: Alignment procedure
- Missing: CBP list
- Data volume (inferred): <1 GB (single-dish map plus public context images)
- Score (inferred): 3/5, Public data and simple averaging, but ROI positions, alignment and CBP selection are not given.
- Rediscovery candidate: no, Key results rely on visual identification and undisclosed region definitions.

## Links

- Method: (cite: White2017) (Calibration and imaging of ALMA solar total-power maps)
- Companion: Paper II (modeling, subsequent paper) (Compares the observational results with theoretical models)
- Related: ALMA solar CSV campaign December 2015

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
 "codes_not_in_obscore": [
  "2011.0.00020.SV"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 61,
  "stated": 26,
  "rate": 0.426
 },
 "evidence_ok": true
}
```
