# First high-resolution look at the quiet Sun with ALMA at 3mm

`2018A&A...619L...6N` | Astronomy and Astrophysics 2018 | first author: Nindos, A. | arXiv: 1810.05223 | DOI: 10.1051/0004-6361/201834113

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: sun
- Question: What do high-resolution ALMA 3 mm images show of the quiet Sun chromosphere: network/intranetwork brightness, center-to-limb variation, and spicules?  
  > "In this article we present high-resolution quiet-Sun observations that we obtained in March 2017; we present CLV measurements for the network and the intranetwork and discuss the properties of spicules beyond the limb." (Introduction)
- Target **Seven quiet-Sun regions from limb to disk center**: coordinates Table 1 solar coordinates, e.g. Target 1 (x,y)=(-680",-680"), Target 7 (50",0")  
  > "Seven regions (targets) were observed at 100 GHz on March 16, 2017, from the limb to the center of the disk, along a line at a position angle of 135$^\circ$" (Observations and data reduction); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00572.S
- bands: 100 GHz (3 mm)  
  > "Seven regions (targets) were observed at 100 GHz on March 16, 2017" (Observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: most compact configuration, 40 twelve-meter and 8 seven-meter antennas  
  > "the observations were performed in the most compact ALMA configuration which included 40 twelve-meter antennas and 8 seven-meter antennas." (Observations and data reduction)
- baselines: _not stated_
- angular resolution: nominal 3.7" x 2.5"; clean beams 2.3-2.6" x 4.5-8.1" (Table 1)  
  > "The resolution we achieved is close to the nominal resolution for the configuration we used which was $3.7\ensuremath{''} \times 2.5\ensuremath{''}$." (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 10 min per target, 2 s cadence  
  > "each target was observed for 10 min with a cadence of 2 s." (Observations and data reduction)
- observing dates: March 16, 2017  
  > "Seven regions (targets) were observed at 100 GHz on March 16, 2017" (Observations and data reduction)
- pi or archival as stated: _not stated_
- Other facility **SDO/AIA**: 1600 and 304 Å images for comparison and pointing cross-correlation  
  > "Therefore the actual pointing was computed by cross-correlation of the ALMA with the AIA 1600 Å images." (Observations and data reduction)
- Other facility **ALMA total power antennas**: 22 full-disk images used for feathering  
  > "Twenty-two FD images were obtained from two 12-m “total power” (TP) antennas" (Observations and data reduction)
- Other facility **GONG**: Hα images to identify spicules  
  > "as evidenced from the comparison of ALMA with H$\alpha$ images from the GONG network" (Results)
- Other facility **IRIS**: slit-jaw images compared with ALMA  
  > "There is also a very strong similarity between the ALMA images and the Interface Region Imaging Spectrograph (IRIS) slit-jaw images" (Results)
- External data: Disk-center quiet Sun Tb of 7250 K used to scale the FD image; 14% flux excess correction  
  > "we scaled the FD image to match the quiet Sun brightness temperature at disk center reported in Paper I which was 7250 K." (Full-disk images) [from Alissandrakis et al. 2017 (Paper I) (cite: 2017A&A...605A..78A)]

## Processing

### Calibration

- pipeline or manual: visibilities calibrated following Shimojo et al. (2017), provided by JAO  
  > "The visibilities were calibrated following the method described by Shimojo et al. (2017) and were provided to us by the Joint ALMA Observatory" (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: four rounds of phase self-cal (20 min, 1 min, 2 s, 2 s) and one amplitude round (2 s)  
  > "four rounds of phase self-calibration, with solution intervals of 20 min, 1 min, 2 s, and 2 s, and one round of amplitude self-calibration with a solution interval of 2 s." (Observations and data reduction)

### Imaging

- task: AIPS CLEAN for average and 2 s snapshot images; CASA feather for combination  
  > "We imported the visibilities into the Astronomical Image Processing System (AIPS) and for each target we re-calculated CLEAN images synthesized from the entire observing period." (Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied as last step  
  > "The last step in the data reduction was the correction of all images for the primary beam response." (Observations and data reduction)
- array combination: feather with full-disk TP image, interferometric flux scaled down for 14% excess  
  > "The combination was done using CASA’s task `feather` and correcting for the fact that the flux of the derived images was higher than that of the FD image by 14%" (Observations and data reduction)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Visibility calibration method  
  > "The visibilities were calibrated following the method described by Shimojo et al. (2017)" (Observations and data reduction) [from Shimojo et al. 2017]
- 14% flux excess correction relative to FD image  
  > "higher than that of the FD image by 14%, as noted in Paper I" (Observations and data reduction) [from Paper I (Alissandrakis et al. 2017)]
- FD ellipticity correction  
  > "We also corrected the FD image for the slight ellipticity of the solar disk, also reported in Paper I." (Full-disk images) [from Paper I]

### Not stated but needed to reproduce (our reading)

- AIPS CLEAN parameters (weighting, robust, cell, image size, iterations)
- Self-calibration reference model and calibrator details
- Details of single-dish processing (Appendix A mostly not given)
- Exact alignment/cross-correlation procedure for pointing
- Polynomial fit and masking details beyond second degree
- Azimuthal averaging bin widths

## Analysis recipe

1. **Re-image with self-calibration**: AIPS CLEAN of average and 2 s snapshot images after phase and amplitude self-calibration  
  > "Both our average and snapshot CLEAN images were produced after four rounds of phase self-calibration" (Observations and data reduction)
   - software: AIPS
   - fitting: _not stated_
   - validation: Self-cal removed jitter in snapshot movies  
  > "removed the jitter that was apparent in the movies of snapshot images" (Observations and data reduction)
2. **Fix pointing and combine with full-disk image**: Cross-correlate with AIA 1600 Å; feather with processed FD image; primary beam correction  
  > "Therefore the actual pointing was computed by cross-correlation of the ALMA with the AIA 1600 Å images." (Observations and data reduction)
   - software: CASA
   - assumption: FD disk-center Tb scaled to 7250 K  
  > "we scaled the FD image to match the quiet Sun brightness temperature at disk center reported in Paper I which was 7250 K." (Full-disk images)
   - fitting: _not stated_
   - validation: Compared to AIA 1600/304 and IRIS  
  > "There is also a very strong similarity between the ALMA images and the Interface Region Imaging Spectrograph (IRIS) slit-jaw images in three bands" (Results)
3. **Measure CLV and network/intranetwork Tb**: Fit Tb(x,y) in 80" FOV with second-degree polynomial; mean above fit = network, below = intranetwork; azimuthal averaging for CLV  
  > "We next fitted $T_b(x,y)$ with a second-degree polynomial to avoid large-scale structure and we considered the average of the values above the fit as representative of the network and the others as representative of the intranetwork." (Results)
   - fitting: second-degree polynomial  
  > "We next fitted $T_b(x,y)$ with a second-degree polynomial to avoid large-scale structure" (Results)
   - validation: Convolved AIA 1600 Å with ALMA beam for Target 5: 3.3% cell increase, 3.7% network drop  
  > "a check using AIA 1600 Å data for Target 5 gave a 3.3% increase of the cell intensity and a 3.7% drop of the network intensity" (Results)

## Software

- **AIPS** : self-calibration and CLEAN imaging  
  > "We imported the visibilities into the Astronomical Image Processing System (AIPS)" (Observations and data reduction)
- **CASA** : feather combination with FD image  
  > "The combination was done using CASA’s task `feather`" (Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Network excess over average Tb | 305 | 35 | K | 3 | On average, the network is $305 \pm 35$ K above the average $T_b$ and the intranetwork $285 \pm 30$ K below. |
| Intranetwork deficit below average Tb | 285 | 30 | K | 3 | On average, the network is $305 \pm 35$ K above the average $T_b$ and the intranetwork $285 \pm 30$ K below. |
| Network/cell ratio | 1.08 | not stated | dimensionless | 3 | The network/cell ratio has an average value of 1.08 and decreases slightly towards the limb. |
| Spicule Tb at 8.5" above limb | 2560 (1800 above background) | not stated | K | 3 | is most prominent at 8.5$''$, with $T_b=2560$ K, 1800 K above the local background and a width of 4$''$. |

## Qualitative findings

- No spicules on the disk in emission or absorption; 3 mm structures are larger than at 1600 Å  
  > "we found no evidence of spicules on the disk, either in emission or in absorption." (Results)

## Claim tuples

- H: Can ALMA 3 mm resolve the chromospheric network and its CLV? | E: Self-calibrated and feathered images of seven targets, azimuthal and polynomial analysis | R: Network 305 K above and intranetwork 285 K below average, ratio 1.08 decreasing slightly toward limb | F: Network is clearly seen and similar to 1600 Å but larger | **supported**
- H: Are spicules detectable at 3 mm? | E: Limb images compared to GONG Hα | R: Structures up to 15" above limb, 1800 K above background | F: First detection of spicules in ALMA mm data; none on the disk | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Unexplained excess emission beyond the limb up to 1000 K; segregation method not unique  
  > "we got emission beyond the limb of up to 1000 K (14% of the disk center value), the origin of which we could not identify." (Summary and discussion)
- Caveat (inferred, ours): Single day, poor weather
- Caveat (inferred, ours): Network segregation via polynomial fit is arbitrary
- Caveat (inferred, ours): Pointing relies on AIA cross-correlation

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: AIPS imaging parameters
- Missing: Self-cal details
- Missing: Full-disk processing details
- Data volume (inferred): tens to hundreds of GB (2 s cadence solar visibilities)
- Score (inferred): 3/5, Data identified by project code and main steps described, but imaging parameters missing and calibrated data came from JAO.
- Rediscovery candidate: no, Recipe lacks imaging parameters and requires JAO-supplied calibrated solar data.

## Links

- Method: Shimojo et al. 2017 (solar visibility calibration)
- Companion: Alissandrakis et al. 2017 (Paper I) (low-resolution full-disk ALMA quiet Sun)

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
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 32,
  "rate": 0.492
 },
 "evidence_ok": true
}
```
