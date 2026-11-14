# VLT/SPHERE- and ALMA-based shape reconstruction of asteroid (3) Juno

`2015A&A...581L...3V` | Astronomy and Astrophysics 2015 | first author: Viikinkoski, M. | arXiv: - | DOI: 10.1051/0004-6361/201526626

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: solar_system
- Question: Can the 3D shape and spin of asteroid (3) Juno be reconstructed from ALMA visibilities combined with AO images and lightcurves, and what does the shape imply about non-gravitational features?  
  > "allows us, for the first time, to explore the viability of the shape reconstruction of asteroids from disk-resolved thermal infrared observations." (1. Introduction)
- Target **(3) Juno**: coordinates _not stated_; z/distance Range to observer 1.12-2.41 au for the AO epochs (Table 1); ALMA resolution 0.021'' ~ 30 km projected  
  > "despite its large diameter of about 250 km" (1. Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00013.SV
- bands: _not stated_
- frequencies and spectral setup: 224, 226, 240, 242 GHz  
  > "At the observed frequencies of 224, 226, 240, and 242 GHz" (2.1 Submillimeter interferometry)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 26 m to 13 km  
  > "thereby providing projected baselines between 26 m and 13 km." (2.1 Submillimeter interferometry)
- angular resolution: as high as 0.021''  
  > "angular resolutions as high as 0.021 ′′, or about 30 km projected at the distance of Juno." (2.1 Submillimeter interferometry)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ten epochs over 4.4 h; each epoch 18 min  
  > "A total of ten different epochs spread over 4.4 h were acquired" (2.1 Submillimeter interferometry); "each epoch on Juno lasted for 18 min, during which time Juno rotated 15 ◦." (2.1 Submillimeter interferometry)
- observing dates: 2014 Oct. 19  
  > "Juno was observed with ALMA on 2014 Oct. 19 using between 27 and 33 antennas" (2.1 Submillimeter interferometry)
- pi or archival as stated: ALMA science verification data, publicly released  
  > "The release of the ALMA science
verification data [1] of Juno (ALMA Partnership et al. 2015) allows us, for the first time, to explore the viability of the shape
reconstruction" (Introduction)
- Other facility **VLT/SPHERE (IRDIS)**: Science verification AO images of Juno  
  > "We used the classical imaging mode of SPHERE (IRDIS, Dohlen et al. 2008) to image the apparent disk of Juno." (2.2 Adaptive-optics images)
- Other facility **Keck NIRC2, VLT NACO, Mt. Wilson ADOPT**: Earlier AO disk-resolved images (1996, 2001, 2010)  
  > "2001-12-26 15h NIRC2 1.59 248 −34 4b" (Table 1)
- Other facility **Pic-du-Midi 1 m telescope and archival lightcurves**: 37 old lightcurves plus a new April 2015 lightcurve  
  > "we acquired a lightcurve in April 2015 at the 1 m telescope of the Pic-du-Midi Observatory, France." (2.3 Optical lightcurves)
- Other facility **Stellar occultation 1979**: 16 chords, used as consistency check  
  > "only the occultation from 1979 with 16 full chords can be used for recovering an almost complete silhouette" (2.4 Stellar occultation)
- External data: Mt. Wilson ADOPT AO images taken directly from the paper  
  > "The original data were no longer available in a usable format, so we used the images directly from the paper." (2.2 Adaptive-optics images) [from Baliunas et al. 2003]
- External data: 11 diameter and 23 mass estimates of Juno  
  > "There are 11 diameter and 23 mass estimates for (3) Juno in the literature (see Appendix)" (4. Results) [from see Appendix references]
- External data: Thermal inertia of Juno 5 J m-2 s-0.5 K-1  
  > "owing to the very low thermal inertia of Juno of 5 J m −2 s −0.5 K −1 (Mueller & Lagerros 1998)" (3. Methods) [from Mueller & Lagerros 1998]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated visibility data used directly (not CLEAN images)  
  > "We used the calibrated visibility data instead of the ALMA deconvolved images" (4. Results)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Self-calibrated images tested; gave no additional detail  
  > "The model reconstructed from the self-calibrated, deconvolved images instead of the raw data revealed no additional detail" (4. Results)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ADAM shape/spin reconstruction algorithm  
  > "We used the ADAM algorithm (Viikinkoski & Kaasalainen 2014; Viikinkoski et al. 2015) for the shape and spin reconstruction." (3. Methods) [from Viikinkoski & Kaasalainen 2014; Viikinkoski et al. 2015]
- ALMA data reduction and self-calibration of the SV data  
  > "As stated by ALMA Partnership et al. (2015), each epoch on Juno lasted for 18 min" (2.1 Submillimeter interferometry) [from ALMA Partnership et al. 2015]
- Averaging of literature diameters by sigma rejection  
  > "following the method by Carry et al. (2012)" (Appendix A) [from Carry et al. 2012]

### Not stated but needed to reproduce (our reading)

- ALMA calibration details and CASA version for the SV visibilities
- Data weighting between ALMA, AO and lightcurve terms and regularization weights in ADAM
- Starting shape and spin and optimization settings
- Subdivision/octantoid resolution and harmonic degree
- Whether antenna phase errors were corrected
- Deconvolution parameters for AO images (Mistral)

## Analysis recipe

1. **Assemble multi-data inputs**: Calibrated ALMA visibilities, deconvolved AO images, lightcurves; occultation used only as check  
  > "the ALMA visibility data were combined with disk-integrated photometry and with the adaptive-optics images, and checked against the occultation data." (3. Methods)
   - software: ADAM
   - parameter: Mt. Wilson image scale a free parameter  
  > "we included it in the optimization as a free parameter." (2.2 Adaptive-optics images)
   - fitting: _not stated_
   - validation: _not stated_
2. **Reconstruct shape and spin**: ADAM with octantoid and subdivision-surface shape supports; semi-analytical FFT-based thermal model  
  > "We used both subdivision surfaces and octantoid parametrization for shape representations" (3. Methods); "we used a simple, semi-analytical FFT-based approach" (3. Methods)
   - software: ADAM
   - assumption: Low thermal inertia of 5 J m-2 s-0.5 K-1  
  > "owing to the very low thermal inertia of Juno of 5 J m −2 s −0.5 K −1" (3. Methods)
   - fitting: _not stated_
   - validation: Compared different shape supports and data subsets; occultation consistency check; self-calibration test  
  > "we checked the effect of data sources by observing the model variations under varying data subset combinations." (3. Methods)
3. **Derive diameter, density and porosity**: Compare diameter with literature mass average to get density and porosity versus L chondrite grain density  
  > "Using this estimate, we find a density of 3.32 ± 0.40 g cm −3." (4. Results)
   - assumption: L ordinary chondrite grain density  
  > "Compared with the grain density of L ordinary chondrites (Consolmagno et al. 2008)" (4. Results)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **ADAM** : All-data asteroid modelling of shape and spin  
  > "model the 3D shape and spin of the large asteroid (3) Juno with the all-data asteroid modelling (ADAM) procedure" (abstract)
- **Mistral** : Deconvolution of NACO, NIRC2 and SPHERE images  
  > "unlike Mistral (Mugnier et al. 2004), the algorithm we used to deconvolve the images from NACO, NIRC2, and SPHERE" (3. Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Volume-equivalent diameter | 249 | ±5 | km | 2 | Our determination of 249 ± 5 km corresponds exactly to this average diameter. |
| Density | 3.32 | ±0.40 | g cm-3 | 3 | we find a density of 3.32 ± 0.40 g cm −3. |
| Porosity | 7 | ±1 | % | 3 | this implies a porosity of 7 ± 1% |
| Spin pole ECJ2000 (λ, β) | 103°, +22° | ±4°, ±4° | deg | 2 | λ ( ◦) 103 ± 4 118 ± 13 103 ± 5 |
| Ellipsoid axes a, b, c | 282, 249, 220 | ±5 each | km | 2 | _a_ (km) 282 ± 5 298 ± 6 304 ± 29 |
| Literature mean mass | 2.68e19 | ±0.24e19 | kg | 0 | an average mass of 2.68 ± 0.24 × 10 19 kg |

## Qualitative findings

- Juno has sizable unrounded features likely from impacts, in the transition between dwarf planets and medium asteroids  
  > "Its global shape features are apparently molded by other than gravitational processes (likely impacts)." (5. Conclusions)

## Claim tuples

- H: Shapes of asteroids can be reconstructed from raw ALMA visibilities combined with other data | E: ADAM fit to ALMA visibilities, lightcurves and AO images | R: Model with D = 249 ± 5 km, consistent with occultation | F: Reconstruction is viable and shape is robust to variations | **supported**
- H: Juno is not fully rounded despite its size | E: Compared shapes from two supports and data subsets | R: Lopsided/lozenge-like shape with a/b = 1.13, b/c = 1.13 | F: Non-equilibrium features from impacts | **supported**
- H: ALMA self-calibration matters for the shape | E: Reconstruction from self-calibrated images | R: No additional detail | F: Not a major concern at this resolution | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Raw visibilities avoid information loss and distortion from CLEAN and self-calibration  
  > "The “clean” ALMA images obtained by various deconvolution and self-calibration processes inevitably lose and distort some of the original information." (2.1 Submillimeter interferometry)
- Alternative: Mt. Wilson features not fully accommodated; occultation data used only as check  
  > "The last did not improve the reliability of the solution or provide more information" (3. Methods)
- How they decided it was enough: _not stated_
- Limitation (authors): Northern hemisphere less constrained due to southern-only viewing geometry  
  > "so the northern parts of the model are less constrained." (4. Results)
- Limitation (authors): Residual antenna phase errors may exist in raw ALMA data  
  > "there usually are residual antennabased phase errors in the raw ALMA data (Hezaveh et al. 2013)." (2.1 Submillimeter interferometry)
- Caveat (inferred, ours): No formal fit statistics or chi-square given for the ALMA data
- Caveat (inferred, ours): Weights between data types not given
- Caveat (inferred, ours): Uncertainties on shape not derived transparently
- Caveat (inferred, ours): Density depends on literature mass

## Reproducibility

- Data public (paper): ALMA SV data publicly released; model on DAMIT  
  > "This model can be downloaded at the DAMIT web site." (4. Results)
- Products in archive: _not stated_
- Missing: ADAM code availability and settings
- Missing: Data weights and regularization
- Missing: Reduced AO images
- Data volume (inferred): tens of GB (SV visibilities, 10 epochs)
- Score (inferred): 3/5, Public data and a published model exist, but the ADAM settings and weights are not given.
- Rediscovery candidate: no, The recipe depends on ADAM and unstated parameters.

## Links

- Method: Viikinkoski et al. 2015 (ADAM algorithm)
- Method: Viikinkoski & Kaasalainen 2014 (ADAM and thermal modeling)
- Companion: ALMA Partnership et al. 2015 (ALMA SV data release of Juno)
- Related: ALMA science verification
- Related: SPHERE science verification
- Related: DAMIT

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
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
  "facts": 71,
  "stated": 35,
  "rate": 0.493
 },
 "evidence_ok": true
}
```
