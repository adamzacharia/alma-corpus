# Discovery and Physical Characterization of a Large Scattered Disk Object at 92 au

`2017ApJ...839L..15G` | The Astrophysical Journal Letters 2017 | first author: Gerdes, D. W. | arXiv: 1702.00731 | DOI: 10.3847/2041-8213/aa64d8

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: solar_system
- Question: What are the orbit, size and albedo of the newly discovered distant TNO 2014 UZ224, using DES discovery data and ALMA thermal emission?  
  > "from which we determine a $V$-band albedo of $13.1^{+3.3}_{-2.4}\mathrm{(stat)}^{+2.0}_{-1.4}\mathrm{(sys)}$ percent" (abstract)
- Target **2014 UZ224 (DeeDee)**: coordinates _not stated_; z/distance 92.5 AU heliocentric at discovery  
  > "2014 UZ$_{224}$ was originally detected at a heliocentric distance of 92.5 AU in 7 linked observations on 4 nights between 2014/9/27 and 2014/10/28" (2 Optical Data and Analysis); distance from orbit fit to DES observations (B&K fitter)  
  > "2014 UZ$_{224}$ was originally detected at a heliocentric distance of 92.5 AU in 7 linked observations on 4 nights between 2014/9/27 and 2014/10/28" (2 Optical Data and Analysis)

## Data provenance

- ALMA projects: 2015.A.00023.S
- bands: 1.3 mm (233 GHz band)  
  > "such as the 1.3mm wavelength corresponding to ALMA’s 233 GHz band used in our measurement" (Measurement of Thermal Emission, Size, and Albedo)
- frequencies and spectral setup: four continuum spectral windows centered on 224, 226, 240, 242 GHz  
  > "The correlator was configured to observe four continuum spectral windows centered on 224, 226, 240, and 242 GHz, respectively, resulting in a total bandwidth of 7.5GHz." (Measurement of Thermal Emission, Size, and Albedo)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15-1462 m, 41 antennae  
  > "The observations were carried out with 41 antennae and baselines between 15-1462 meters." (Measurement of Thermal Emission, Size, and Albedo)
- angular resolution: 0.30"x0.25", PA -84 deg  
  > "The resulting synthesized beam is $0.30^{\prime\prime}\times0.25^{\prime\prime}$, with a position angle of $-84^{\circ}$." (Measurement of Thermal Emission, Size, and Albedo)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 176 minutes  
  > "The total on-source integration time was 176 minutes." (Measurement of Thermal Emission, Size, and Albedo)
- observing dates: 2016 August 19 and 20  
  > "on the Atacama Large Millimeter/submillimeter Array (ALMA) on 2016 August 19 and 20." (Measurement of Thermal Emission, Size, and Albedo)
- pi or archival as stated: director's discretionary time  
  > "We observed 2014 UZ$_{224}$ with director’s discretionary time" (Measurement of Thermal Emission, Size, and Albedo)
- Other facility **Dark Energy Survey / DECam (Blanco 4m)**: Discovery and optical photometry, orbit  
  > "we report the discovery of a large scattered disk object at 92 AU using data from the Dark Energy Survey" (Introduction)
- External data: Emissivity 0.68 at 1.3 mm, average for four TNOs with ALMA  
  > "We adopt a value of $\epsilon_{\lambda}=0.68$ at 1.3mm, the average value measured by (cite: BrownButler2017) with ALMA at 233 GHz" (Measurement of Thermal Emission, Size, and Albedo) [from (cite: BrownButler2017)]
- External data: Phase integral q=0.8  
  > "we assume that the phase integral $q=0.8$ as derived in (cite: Stansberry2008) for large, bright TNOs" (Measurement of Thermal Emission, Size, and Albedo) [from (cite: Stansberry2008)]
- External data: Beaming factor range 0.6 to 2.6  
  > "we must allow $\eta$ to explore its full range of 0.6 to 2.6 (cite: Mommert2012)" (Measurement of Thermal Emission, Size, and Albedo) [from (cite: Mommert2012)]

## Processing

### Calibration

- pipeline or manual: manual calibration by NRAO staff  
  > "The raw data were calibrated by NRAO staff manually using the CASA package version 4.6." (Measurement of Thermal Emission, Size, and Albedo)
- casa version: CASA 4.6  
  > "The raw data were calibrated by NRAO staff manually using the CASA package version 4.6." (Measurement of Thermal Emission, Size, and Albedo)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-0120  
  > "J0423-0120 was used for absolute flux calibration." (Measurement of Thermal Emission, Size, and Albedo)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN, continuum  
  > "We generated a synthesized continuum image with the CLEAN algorithm and a natural weighting in CASA." (Measurement of Thermal Emission, Size, and Albedo)
- deconvolver: _not stated_
- weighting robust: natural  
  > "We generated a synthesized continuum image with the CLEAN algorithm and a natural weighting in CASA." (Measurement of Thermal Emission, Size, and Albedo)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.30"x0.25", PA -84 deg  
  > "The resulting synthesized beam is $0.30^{\prime\prime}\times0.25^{\prime\prime}$, with a position angle of $-84^{\circ}$." (Measurement of Thermal Emission, Size, and Albedo)
- final rms: _not stated_

### Inherited from earlier work

- Monte Carlo uncertainty procedure for diameter and albedo  
  > "Estimation of the uncertainties in the calculated diameter and albedo were performed following the procedure outlined in (cite: Mommert2012)." (Measurement of Thermal Emission, Size, and Albedo) [from (cite: Mommert2012)]

### Not stated but needed to reproduce (our reading)

- Cell size, image size, number of iterations and clean threshold
- Ephemeris used and how the five data sets were stacked (fixplanet parameters)
- Image rms
- Number of Monte Carlo draws' flux input values (optical flux uncertainty) and solar V magnitude
- Self-calibration status

## Analysis recipe

1. **Stack and image ALMA continuum**: Stack five calibrated data sets with fixplanet, CLEAN with natural weighting  
  > "The calibrated visibilities of five data sets were then stacked to align the position using the `fixplanet` command." (Measurement of Thermal Emission, Size, and Albedo)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure source flux and size**: 2D Gaussian fit with imfit; compared single point and binary models  
  > "We used the `imfit` task in CASA to fit the central source with a 2D Gaussian" (Measurement of Thermal Emission, Size, and Albedo)
   - software: CASA imfit
   - fitting: 2D Gaussian  
  > "We used the `imfit` task in CASA to fit the central source with a 2D Gaussian and found the source had a major-axis FWHM of $0.33\pm0.05^{\prime\prime}$" (Measurement of Thermal Emission, Size, and Albedo)
   - validation: Residuals of point-source and binary models within 1 sigma of background noise  
  > "The residuals after subtracting either model are very similar, and both were within 1$\sigma$ of the distribution of noise measured in the background regions" (Measurement of Thermal Emission, Size, and Albedo)
3. **Derive diameter and albedo with STM**: Solve visible and thermal flux equations with Standard Thermal Model, eta free over 0.6-2.6  
  > "For the remainder of this work we use the STM as our base thermal model, but we allow $\eta$ to take any value within its allowed range." (Measurement of Thermal Emission, Size, and Albedo)
   - parameter: epsilon=0.9±0.1 bolometric; epsilon_lambda=0.68; q=0.8; phase angle 0  
  > "We keep $\epsilon=0.9\pm0.1$ as our bolometric emissivity in the surface temperature distribution." (Measurement of Thermal Emission, Size, and Albedo)
   - assumption: Spherical body, uniform surface properties  
  > "assuming a spherical body with uniform surface properties" (abstract)
   - fitting: Monte Carlo with 1000 clones; normal draws, eta uniform 0.6-2.6  
  > "We employed a Monte Carlo simulation using 1000 clones" (Measurement of Thermal Emission, Size, and Albedo)
   - validation: _not stated_

## Software

- **CASA** 4.6: calibration, fixplanet stacking, CLEAN imaging, imfit  
  > "The raw data were calibrated by NRAO staff manually using the CASA package version 4.6." (Measurement of Thermal Emission, Size, and Albedo)
- **Mercury6** : orbit integration  
  > "built into `Mercury6` (cite: Chambers1999)" (Orbital Dynamics)
- **DiffImg** : difference imaging transient detection  
  > "a variant of the DES supernova difference-imaging pipeline, `DiffImg` (cite: Kessler2015)" (Optical Data and Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA peak flux | 47 | not stated | uJy/beam | 2 | with a peak flux of $47~\mu$Jy/beam and a signal-to-noise ratio of $\sim 7$ |
| ALMA total flux | 53 | 10 | uJy | 2 | The total flux measured from a 2D Gaussian fit is $53\pm10~\mu$Jy. |
| V-band geometric albedo | 13.1 | +3.3/-2.4 (stat), +2.0/-1.4 (sys) | percent | 3 | $V$-band albedo of $13.1^{+3.3}_{-2.4}\mathrm{(stat)}^{+2.0}_{-1.4}\mathrm{(sys)}$ percent |
| Diameter | 635 | +57/-61 (stat), +32/-39 (sys) | km | 3 | a diameter of $635^{+57}_{-61}\mathrm{(stat)}^{+32}_{-39}\mathrm{(sys)}$ km |

## Qualitative findings

- Orbit is dynamically stable over Gyr; detached TNO  
  > "this object remains dynamically stable and satisfies the formal criteria of (cite: Gladman2008) as a detached TNO" (Orbital Dynamics)

## Claim tuples

- H: Can ALMA measure the size and albedo of a ~92 AU TNO? | E: 3 h ALMA band 6 continuum plus DES optical photometry, STM | R: 7 sigma detection; D=635 km, pV=13.1% | F: Object is a candidate dwarf planet with mixed ice-rock composition | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Binary model tested for N-S elongation; consistent with single point source  
  > "We conclude that the observations are consistent with a single point source." (Measurement of Thermal Emission, Size, and Albedo)
- How they decided it was enough: _not stated_
- Limitation (authors): Single-wavelength measurement prevents fitting eta  
  > "However this is not possible with a single-wavelength measurement" (Measurement of Thermal Emission, Size, and Albedo)
- Caveat (inferred, ours): STM with free eta gives large systematics; 7 sigma detection only
- Caveat (inferred, ours): Emissivity 0.68 taken from other TNOs

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Ephemeris and stacking details
- Missing: Optical flux inputs for Monte Carlo
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Data identified and recipe outlined, but imaging details and thermal-model inputs are incomplete.
- Rediscovery candidate: no, Imaging and Monte Carlo inputs not fully specified; archive public status not stated.

## Links

- Method: (cite: Mommert2012) (Monte Carlo uncertainty procedure and eta range)
- Related: Dark Energy Survey

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 35,
  "rate": 0.538
 },
 "evidence_ok": true
}
```
