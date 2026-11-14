# A Study of HH 270 with the James Webb Space Telescope

`2026ApJ..1003...65O` | The Astrophysical Journal 2026 | first author: Ortiz Capeles, A. N. | arXiv: 2604.09897 | DOI: 10.3847/1538-4357/ae5e55

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: star_formation
- Question: What do JWST NIRCam, ALMA CO and Subaru Halpha reveal about the jet, knots, cavity and molecular outflow of HH 270?  
  > "This paper aims to build upon those studies by providing new high-resolution observations of HH 270 with the NIRCam instrument" (Introduction)
- Target **HH 270 / HH270VLA1**: coordinates VLA1-A 5:51:34.587 +2:56:46.010; VLA1-B 5:51:34.600 +2:56:45.880  
  > "located within the Orion B complex at a distance of $\sim$430 pc from the Sun" (Introduction); "we assume a distance of 430.1 pc to HH270VLA1" (Table 1); z/distance 430.1 pc  
  > "located within the Orion B complex at a distance of $\sim$430 pc from the Sun" (Introduction); "we assume a distance of 430.1 pc to HH270VLA1" (Table 1); distance from Tobin et al. 2022 (2022ApJ...925...39T)  
  > "located within the Orion B complex at a distance of $\sim$430 pc from the Sun" (Introduction); "we assume a distance of 430.1 pc to HH270VLA1" (Table 1)

## Data provenance

- ALMA projects: 2018.1.01038.S
- bands: Band 6 (1.3 mm)  
  > "Band 6, 1.3 mm observations toward HH270VLA1 were conducted in the C-5 configuration" (3.2 ALMA and Subaru Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C-5, 43 to 50 antennas  
  > "conducted in the C-5 configuration with 43 to 50 operating antennas" (3.2 ALMA and Subaru Observations)
- baselines: _not stated_
- angular resolution: ~0.3 arcsec  
  > "enabled an angular resolution of $\sim0.3 \ensuremath{''}$" (3.2 ALMA and Subaru Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~32 min  
  > "The total time on source was $\sim$32 min." (3.2 ALMA and Subaru Observations)
- observing dates: 8 executions, Oct-02-2018 to Nov-23-2018  
  > "The observations were carried out with 8 executions between Oct-02-2018 and Nov-23-2018." (3.2 ALMA and Subaru Observations)
- pi or archival as stated: _not stated_
- Line: C18O J=2-1 (219.560 GHz)
- Line: 13CO J=2-1 (220.399 GHz)
- Line: 12CO J=2-1 (230.538 GHz)
- Other facility **JWST NIRCam**: F212N and F460M images (GTO 1293)  
  > "Observations were carried out using the F460M and F212N filters" (3.1 JWST NIRCam Observations)
- Other facility **Subaru Telescope**: Halpha image from 2006  
  > "H$\alpha$ observations of the HH 270/110 system were taken with the Subaru Telescope on January 4, 2006" (3.2 ALMA and Subaru Observations)
- External data: Subaru Halpha image of HH 270/110  
  > "which were published in (cite: 2012AJ....143..106K)" (3.2 ALMA and Subaru Observations) [from (cite: 2012AJ....143..106K)]
- External data: VLA1-A and VLA1-B positions, distance 430.1 pc  
  > "located at $\alpha = 5:51:34.587$, $\delta=+2:56:46.010$ and $\alpha=5:51:34.600$, $\delta=+2:56:45.880$, respectively ((cite: 2022ApJ...925...39T))" (4 Results) [from (cite: 2022ApJ...925...39T)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "The data were calibrated by the pipeline integrated within `CASA 5.4.0-70`" (3.2 ALMA and Subaru Observations)
- casa version: CASA 5.4.0-70  
  > "The data were calibrated by the pipeline integrated within `CASA 5.4.0-70`" (3.2 ALMA and Subaru Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800 (flux and bandpass); J0532+0732 phase  
  > "The monitored quasar J0510+1800 was used as the flux density and bandpass calibrator" (3.2 ALMA and Subaru Observations)
- flux scale uncertainty: _not stated_
- self calibration: Phase-only then amplitude self-cal on continuum, applied to line data  
  > "First, phase-only self-calibration was performed on the continuum data, and amplitude self-calibration was then performed" (3.2 ALMA and Subaru Observations)

### Imaging

- task: tclean  
  > "final images of the spectral line data were made using `tclean`" (3.2 ALMA and Subaru Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.048 arcsec (C18O, 13CO); 0.045 arcsec (12CO)  
  > "with 960$\times$960 0.048$\ensuremath{''}$ pixels" (3.2 ALMA and Subaru Observations)
- image size: 960x960 pixels  
  > "with 960$\times$960 0.045$\ensuremath{''}$ pixels" (3.2 ALMA and Subaru Observations)
- masking: usemask='auto-multithresh'  
  > "the automated masking in `tclean` was used via the `usemask=‘auto-multithresh’` option" (3.2 ALMA and Subaru Observations)
- multiscale scales: _not stated_
- continuum subtraction: hif_findcont, hif_uvcontfit, hif_uvcontsub  
  > "subtracted from the spectral line visibilities using the pipeline tasks `hif_uvcontfit` and `hif_uvcontsub`" (3.2 ALMA and Subaru Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.29x0.26 arcsec (C18O, 13CO); 0.28x0.24 arcsec (12CO)  
  > "and a $0.28\ensuremath{''} \times 0.24\ensuremath{''}$ beam size" (3.2 ALMA and Subaru Observations)
- final rms: _not stated_

### Inherited from earlier work

- Subaru Halpha data reduction and image creation  
  > "See (cite: 2012AJ....143..106K) for details on the data reduction and image creation procedures." (3.2 ALMA and Subaru Observations) [from (cite: 2012AJ....143..106K)]
- NIRCam observation design  
  > "As outlined in (cite: 2025ApJ...981...95R), the NIRCam data of the HH 270/110 system were obtained" (3.1 JWST NIRCam Observations) [from (cite: 2025ApJ...981...95R)]
- Processed ALMA data products provided by J. Tobin  
  > "We thank John J. Tobin for providing processed ALMA data products that contributed part of our analysis." (Acknowledgments) [from John J. Tobin]

### Not stated but needed to reproduce (our reading)

- tclean weighting/robust value, deconvolver and threshold
- line-free channels and continuum selection
- self-calibration solution intervals
- final image rms per channel
- knot detection thresholds and Ricker wavelet sigma
- moment-map clipping thresholds
- how Tobin-provided ALMA products differ from archive products

## Analysis recipe

1. **Process ALMA CO cubes**: Pipeline calibration, continuum subtraction, self-cal, tclean with auto-multithresh  
  > "Following continuum subtraction and self-calibration, final images of the spectral line data were made using `tclean`." (3.2 ALMA and Subaru Observations)
   - software: CASA, tclean
   - parameter: C18O/13CO: 120 channels of 0.25 km/s; 12CO: 200 channels of 1 km/s  
  > "The $^{12}$CO data was imaged with 200, 1 km s$^{-1}$ channels" (3.2 ALMA and Subaru Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Align and background-subtract NIRCam images**: Background2D subtraction; astroalign alignment; F212N vs F460M offsets checked  
  > "The aligned F212N image showed deviations of $<0.05\ensuremath{''}$ relative to the F460M image" (3.1 JWST NIRCam Observations)
   - software: photutils, astroalign
   - fitting: _not stated_
   - validation: Star coordinate offset statistics  
  > "a script was developed to compute the average, minimum, median, and maximum distance differences between the two sets of stellar coordinates" (3.1 JWST NIRCam Observations)
3. **Identify and centroid jet knots**: Visual identification, Ricker-wavelet filtering, centroid_sources/centroid_com refinement; ALMA 12CO knots identified manually  
  > "These positions were refined using the `centroid_sources` and `centroid_com` routines from the `photutils.centroids` module." (4 Results)
   - software: photutils
   - assumption: Distance 430.1 pc  
  > "we assume a distance of 430.1 pc to HH270VLA1" (Table 1)
   - fitting: _not stated_
   - validation: Mean/median shifts between initial and refined positions were minimal  
  > "the refinement of the initial estimates was, in fact, minimal" (4 Results)
4. **Knot photometry and pairing**: Circular aperture flux with nearby background region; pair knots across lobes within 0.13 arcsec  
  > "The flux of each identified knot was measured using a circular region which encompasses the full extent of each knot." (4 Results)
   - fitting: _not stated_
   - validation: _not stated_
5. **Moment maps and multiwavelength comparison**: CARTA moment-0 maps in velocity ranges; overlay with F460M and Halpha  
  > "ALMA moment-0 (integrated intensity) maps were generated for the $^{12}$CO, $^{13}$CO and C$^{18}$O lines" (4 Results)
   - software: CARTA
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4.0-70: Pipeline calibration and imaging  
  > "The data were calibrated by the pipeline integrated within `CASA 5.4.0-70`" (3.2 ALMA and Subaru Observations)
- **tclean** : Spectral line imaging  
  > "final images of the spectral line data were made using `tclean`" (3.2 ALMA and Subaru Observations)
- **CARTA** : Moment-0 maps  
  > "using the Cube Analysis and Rendering Tool for Astronomy (CARTA)" (4 Results)
- **photutils** : Background2D and centroiding  
  > "Background correction was applied using the `Background2D` function from the `photutils.background` module." (3.1 JWST NIRCam Observations)
- **astroalign** : Image alignment  
  > "The `astroalign` package was then used for the alignment of the NIRCam images." (3.1 JWST NIRCam Observations)
- **jwst pipeline** 1.12.5 (CRDS 11.17.6): Level 3 NIRCam mosaics  
  > "the calibration software version used was `1.12.5`, with the Calibration Reference Data System (CRDS) software version `11.17.6`" (3.1 JWST NIRCam Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of knots in F460M | 47 (33 redshifted, 14 blueshifted) | not stated | count | 3 | / R33   / 5:51:35.3792 / +2:57:01.722 / 19.68    / 8466.09  / —             / |
| Closest blueshifted knot B01 distance | ~230 au (0.54 arcsec) | not stated | au | 3 | The first knot in the blueshifted lobe (B01) lies at $\sim$230 au from the central source. |
| Fraction of blueshifted knots with redshifted counterpart within 0.13 arcsec | 70% (F460M), 75% (F212N) | not stated | percent | 4 | most (70% and 75%, respectively) of the blueshifted knots have a redshifted counterpart within a distance of 0.13$''$ |
| Redshifted knots brighter than blueshifted in F460M | 71% | not stated | percent | 4 | most (71%) of the redshifted knots are brighter than the blueshifted knots |
| Rotation angle for knot plot | ~43 | not stated | degrees | 3 | all knots’ positions were rotated clockwise by $\sim$43 degrees |
| Cloud velocity near HH 270 | ~8-9 | not stated | km/s | 5 | The molecular cloud velocity near HH 270 is estimated at $\sim$8-9 km s$^{-1}$ |

## Qualitative findings

- Redshifted 12CO jet is an extension of the NIR jet and curves beyond ~4000 au.  
  > "the redshifted $^{12}$CO jet can be seen as an extension of the NIR jet" (4 Results)
- 13CO and C18O trace compact dense slow gas near the source rather than the jet.  
  > "These tracers highlight dense, slow-moving gas likely associated with the envelope or cavity walls, rather than the high-velocity jet." (4 Results)

## Claim tuples

- H: Does JWST resolve the inner jet and its knots in both lobes? | E: NIRCam F460M and F212N knot identification | R: Many new knots, the closest ~230 au from the source | F: A collimated inner jet is revealed with a bipolar cavity | **supported**
- H: Is the jet curvature due to precession or deflection? | E: Knot positions and ALMA 12CO morphology | R: L-shaped curvature in the NIR and 12CO | F: Consistent with precession or deflection; not distinguished | **partially**
- H: Do optical, IR and mm tracers show the same outflow? | E: Overlay of ALMA 12CO, F460M and Halpha | R: Morphological continuity in the redshifted lobe | F: The same outflow is seen in different tracers | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: 12CO knots identified manually since the lower resolution and extended emission made centroid fitting unreliable  
  > "made the use of the centroid fitting routines less reliable" (4 Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Contributions of each protostar to the outflow are uncertain.  
  > "the exact contribution of each protostar to the outflow remains uncertain given the current data" (6 Discussion)
- Caveat (inferred, ours): Knot identification is partly visual and not reproducible without thresholds
- Caveat (inferred, ours): No uncertainties on knot fluxes or positions
- Caveat (inferred, ours): ALMA is only moment-0 maps, with no quantitative outflow mass or momentum
- Caveat (inferred, ours): Precession vs deflection not discriminated

## Reproducibility

- Data public (paper): NIRCam data in MAST; ALMA project cited  
  > "The NIRCam data used in this paper can be found in MAST" (3.1 JWST NIRCam Observations)
- Products in archive: _not stated_
- Missing: Knot detection parameters
- Missing: Tclean weighting and thresholds
- Missing: Tobin-processed ALMA products
- Missing: Moment velocity ranges beyond those listed are given, but clipping not
- Data volume (inferred): ~50-100 GB raw ALMA plus ~1 GB JWST
- Score (inferred): 3/5, Public data and software named, but key imaging and detection parameters missing and the results are mostly qualitative.
- Rediscovery candidate: no, Main results are knot catalogs and morphology, with incomplete parameters.

## Links

- Method: (cite: 2020PASP..132b4505K) (auto-multithresh masking)
- Companion: (cite: 2025ApJ...981...95R) (Earlier JWST NIRCam study of HH 270)
- Companion: (cite: 2022ApJ...925...39T) (VANDAM ALMA survey source properties and distance)
- Related: VANDAM
- Related: JWST GTO 1293

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
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
  "facts": 76,
  "stated": 46,
  "rate": 0.605
 },
 "evidence_ok": true
}
```
