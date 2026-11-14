# An ALMA/HST Study of Millimeter Dust Emission and Star Clusters

`2019ApJ...884..112T` | The Astrophysical Journal 2019 | first author: Turner, J. A. | arXiv: 1909.04629 | DOI: 10.3847/1538-4357/ab3faa

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: Does the millimeter dust continuum slope (0.87/2.1 mm) in NGC 628 vary with the ages and masses of nearby HST LEGUS star clusters, indicating dust processing by the local radiation field?  
  > "allows us to constrain the spatial variations in the slope of the millimeter dust continuum as a function of the ages and masses of the nearby stellar clusters." (abstract)
- Target **NGC 628 (M74)**: coordinates _not stated_; z/distance 9.9 Mpc  
  > "NGC 628 is nearly face-on ($i \sim 25$$^\circ$), located at a distance of 9.9 Mpc (cite: Calzetti2015)" (Introduction); distance from Calzetti et al. 2015 (LEGUS)  
  > "NGC 628 is nearly face-on ($i \sim 25$$^\circ$), located at a distance of 9.9 Mpc (cite: Calzetti2015)" (Introduction)

## Data provenance

- ALMA projects: 2016.1.01435.S, 2012.1.00650.S, 2013.1.00532.S
- bands: Band 7 (343 GHz, 0.87 mm) and Band 4 (145 GHz, 2.1 mm)  
  > "The *ALMA* Cycle 4 observations in band 7 (343 GHz, 0.87 mm) and band 4 (145 GHz, 2.1 mm)" (2 ALMA Observations)
- frequencies and spectral setup: Continuum from four SPWs (17, 19, 21, 23) in each band  
  > "Continuum maps were generated using all four spectral windows (SPWs 17, 19, 21, 23) in each band" (2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m array; 43 antennas (B7), 44 antennas (B4)  
  > "Our band 7 observations consisted of 137 pointings with 43 12-meter antennas" (2 ALMA Observations)
- configurations: _not stated_
- baselines: B7: 15.1 m to 2.6 km; B4: 18.6 m to 1.1 km  
  > "with a baseline ranging from 15.1 m to 2.6 km" (2 ALMA Observations)
- angular resolution: 1.12"x1.04" (B7), 1.12"x1.08" (B4)  
  > "This gives a restoring beam size of 1.12$''$ $\times$ 1.04$''$ with position angle 39.73$\ensuremath{^\circ}$ for band 7" (2 ALMA Observations)
- max recoverable scale: 7.2" (B7), 13.8" (B4)  
  > "with a maximum recoverable scale of 7.2$''$" (2 ALMA Observations)
- sensitivity: 1 sigma 225 uJy/beam (B7), 31.7 uJy/beam (B4)  
  > "the 1$\sigma$ sensitivity is 225 $\mu$Jy bm$^{-1}$ for band 7 and 31.7 $\mu$Jy bm$^{-1}$ for band 4" (2 ALMA Observations)
- time on source: _not stated_
- observing dates: 2016-2017  
  > "were carried out in 2016–2017" (2 ALMA Observations)
- pi or archival as stated: _not stated_
- Other facility **HST LEGUS**: Star cluster catalog with ages and masses  
  > "The LEGUS dataset provides star clusters’ measured properties including age, mass, and color excess" (Introduction)
- Other facility **Archival ALMA bands 6 and 3, CO(2-1)**: Non-detection checks for the bright unknown source  
  > "archival *ALMA* bands 6 and 3 continuum maps (observed 2013 and 2015), or CO (2–1) emission line maps (observed 2013)" (4.1 Bright Unknown Source)
- External data: LEGUS star cluster catalog (ages, masses; averaged aperture corrections, MW extinction, Padova-AGB tracks)  
  > "We make use of the LEGUS cluster catalog with the averaged aperture corrections, Milky Way extinction, and Padova-AGB stellar evolution track" (Introduction) [from (cite: Calzetti2015; Adamo2017)]
- External data: Star-forming SED templates for photometric redshift and reference dust model  
  > "the star-forming SED templates of (cite: Dale2014)" (4.1 Bright Unknown Source) [from (cite: Dale2014)]

## Processing

### Calibration

- pipeline or manual: not stated beyond CASA reduction  
  > "The data were reduced using the Common Astronomy Software Applications (CASA) package version 5.4.0-68" (2 ALMA Observations)
- casa version: CASA 5.4.0-68  
  > "package version 5.4.0-68" (2 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean, mosaic mode  
  > "Images were constructed and cleaned using the CASA task `TCLEAN` in the mosaic imaging mode." (2 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 2.0  
  > "A Briggs weighting is used with the “robust” parameter set to 2.0" (2 ALMA Observations)
- uv taper: 1.2" (B7), 1.0" (B4)  
  > "A $u$-$v$ taper of 1.2$''$ and 1.0$''$ is applied to the band 7 and band 4 images, respectively." (2 ALMA Observations)
- cell size: 0.06"/pixel  
  > "With the pixel scale of 0.06$''$ per pixel" (3 Analysis)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Applied to continuum maps; sensitivity measured before correction  
  > "which were then corrected for the primary beam attenuation and used for the analysis in this paper." (2 ALMA Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.12"x1.04" PA 39.73 deg (B7); 1.12"x1.08" PA 29.63 deg (B4)  
  > "For band 4, the restoring beam is 1.12$''$$\times$1.08$''$ with position angle 29.63$\ensuremath{^\circ}$" (2 ALMA Observations)
- final rms: 225 uJy/beam (B7), 31.7 uJy/beam (B4)  
  > "the 1$\sigma$ sensitivity is 225 $\mu$Jy bm$^{-1}$ for band 7 and 31.7 $\mu$Jy bm$^{-1}$ for band 4" (2 ALMA Observations)

### Not stated but needed to reproduce (our reading)

- Calibration details (pipeline vs manual, flux calibrator, flux scale uncertainty)
- Clean threshold, niter, masking and image size
- SExtractor configuration beyond 50 pixels at 2 sigma (background mesh, filter)
- Aperture used for photometry and background estimation
- How the three nearest clusters are selected and how ages/masses are averaged
- Details of the stacking and slope uncertainty
- Cluster catalog URL (footnote empty)

## Analysis recipe

1. **Image band 7 and 4 continuum**: tclean mosaic with Briggs robust 2.0 and uv taper, primary beam corrected  
  > "Images were constructed and cleaned using the CASA task `TCLEAN` in the mosaic imaging mode." (2 ALMA Observations)
   - software: CASA
   - parameter: taper 1.2" (B7), 1.0" (B4)  
  > "A $u$-$v$ taper of 1.2$''$ and 1.0$''$ is applied to the band 7 and band 4 images, respectively." (2 ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Detect millimeter sources and measure fluxes**: SExtractor detection requiring 50 contiguous pixels above 2 sigma; keep sources in 80% footprint; noise from randomly placed ellipses; require dual-band centroid match within beam  
  > "with the requirement that each source must have 50 contiguous pixels with flux greater than 2$\sigma$ above the background." (3 Analysis)
   - software: SExtractor
   - fitting: _not stated_
   - validation: Chance alignment test with 10,000 random placements of apertures  
  > "we randomly place our same SExtractor identified source apertures across each image, count how many overlap, and repeat this process 10,000 times." (3 Analysis)
3. **Match sources to LEGUS clusters and compute slope**: Find three nearest LEGUS clusters per source using Gaia-registered positions; compute slope S(0.87/2.1 mm) = dlogF/dlogλ  
  > "We identify the three LEGUS star clusters that are projected to lie closest to each millimeter source." (3 Analysis)
   - assumption: Distance 9.9 Mpc  
  > "assuming a distance of 9.9 Mpc to NGC 628" (2 ALMA Observations)
   - fitting: _not stated_
   - validation: Slope uncertainty from difference between summed and stacked (30" cutouts) slopes  
  > "The uncertainty on this slope is approximated by the difference between $S$(0.87mm/2.1mm)$_{\rm sum}$ and the slope $S$(0.87mm/2.1mm)$_{\rm stack}$" (4 Results & Discussion)
4. **Compare slopes with reference dust SED and cluster age/mass**: Compare slopes with reference slope -4.81 from the Dale2014 alpha=2.5 template (modified blackbody T=23 K, beta=1.8); look for correlation with mean age and mass  
  > "Fitting a modified blackbody to the “$\alpha=2.5$” model yields a blackbody temperature $T=23$ K and $\beta=1.8$." (4.1 Bright Unknown Source)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4.0-68: data reduction and tclean imaging  
  > "The data were reduced using the Common Astronomy Software Applications (CASA) package version 5.4.0-68" (2 ALMA Observations)
- **SExtractor** : millimeter source identification and photometry  
  > "Millimeter sources for each band are identified using SExtractor" (3 Analysis)
- **APLpy** : plotting (listed in Software)  
  > "APLpy (cite: aplpy), Astropy (cite: astropy1; astropy2), CASA (cite: casa2007), NumPy (cite: numpy), SExtractor (cite: sextractor)" (Software)
- **Astropy** : listed in Software  
  > "APLpy (cite: aplpy), Astropy (cite: astropy1; astropy2), CASA (cite: casa2007), NumPy (cite: numpy), SExtractor (cite: sextractor)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of dual-band sources | 16 | not stated | sources | 2 | This yields a final tally of 16 dual-band sources |
| Chance overlapping sources | 15 | 4 (std dev) | sources | 2 | We find an average of 15 uncorrelated sources randomly overlap, with a standard deviation of 4 sources. |
| Slope of summed sources | -3.92 | 0.3 | dimensionless | 3 | the slope of the sum of all 16 sources at $S$(0.87mm/2.1mm)$_{\rm sum}=-3.92\pm0.3$ |
| Reference model slope | -4.81 | not stated | dimensionless | 4 | $S$(0.87mm/2.1mm)$_{\rm ref}=-4.81$ |
| Sources with slope above reference | 13 of 16 | not stated | sources | 4 | Thirteen of the 16 sources exhibit millimeter/submillimeter slopes larger than this reference value. |
| Mean separation to young clusters | 161 | 21 | pc | 3 | $\sim$ 161$\pm$21 pc and $\sim$ 172$\pm$13 pc, respectively, for the younger and older clusters |
| Mean separation to old clusters | 172 | 13 | pc | 3 | $\sim$ 161$\pm$21 pc and $\sim$ 172$\pm$13 pc, respectively, for the younger and older clusters |

## Qualitative findings

- No correlation of the mm slope with star cluster age or mass  
  > "We find no correlation with either star cluster mass or star cluster age" (4 Results & Discussion)
- A bright mm source detected only in bands 4 and 7, possibly a dust-obscured supernova  
  > "We speculate this is possibly a dust obscured supernova." (abstract)

## Claim tuples

- H: Local star cluster radiation (age/mass) flattens the mm dust emissivity slope | E: Compare slopes of 16 dual-band sources with the mean age and mass of the three nearest LEGUS clusters | R: No correlation with age or mass | F: Local ISRF from nearby clusters does not measurably affect the mm slope in this footprint | **supported**
- H: There is a mm excess over a cold dust model | E: Compare measured slopes to the reference slope -4.81 | R: 13 of 16 slopes are flatter; summed slope -3.92 | F: Small but real excess, with caveats from dust composition | **partially**
- H: The brightest source belongs to NGC 628 and its nature | E: SED template fit and archival non-detection checks | R: Best fit is a cool dust template at z=0; not detected in band 6 | F: Likely a dust-obscured supernova, speculative | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Compact cold infrared dark cloud ruled out because expected band 6 flux was not detected  
  > "Therefore, we can rule out the infrared dark cloud explanation." (4.1 Bright Unknown Source)
- How they decided it was enough: _not stated_
- Limitation (authors): A significant fraction of the spatial overlaps may arise by chance  
  > "We note, however, that a significant fraction of these spatial overlaps may arise by chance." (5 Summary)
- Limitation (authors): Small number of sources and solar-metallicity region only  
  > "However, we have detected a relatively small number of millimeter/submillimeter sources" (5 Summary)
- Caveat (inferred, ours): Only 16 sources with chance-overlap expectation of ~15, so statistics are weak
- Caveat (inferred, ours): Slope uncertainty is a crude estimate and flux errors are not propagated
- Caveat (inferred, ours): Band 4 and 7 have different uv coverage and recoverable scales, which may bias slopes
- Caveat (inferred, ours): Free-free and synchrotron contamination at 2.1 mm is not considered

## Reproducibility

- Data public (paper): Data cited by ALMA project ID; archive public status not explicitly stated  
  > "(ID = 2016.1.01435.S3, PI = D. Dale)" (2 ALMA Observations)
- Products in archive: _not stated_
- Missing: SExtractor parameters
- Missing: clean parameters and masks
- Missing: cluster selection details
- Missing: LEGUS catalog URL
- Data volume (inferred): ~100-300 GB raw (137+23 mosaic pointings)
- Score (inferred): 3/5, Data and main imaging parameters are given, but source extraction and photometry details are missing.
- Rediscovery candidate: no, Key SExtractor and photometry settings are unstated, so numeric results cannot be reliably redone.

## Links

- Method: (cite: Adamo2017) (LEGUS cluster catalog)
- Method: (cite: Dale2014) (SED templates)
- Companion: (cite: Grasha2019) (Similar cluster-GMC comparison in M51)
- Related: LEGUS
- Related: KINGFISH

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2012.1.00650.S",
  "2013.1.00532.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 42,
  "rate": 0.6
 },
 "evidence_ok": true
}
```
