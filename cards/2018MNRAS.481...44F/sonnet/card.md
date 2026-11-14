# Is there really a debris disc around ζ<SUP>2</SUP> Reticuli?

`2018MNRAS.481...44F` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Faramaz, V. | arXiv: 1809.00645 | DOI: 10.1093/mnras/sty2304

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks
- Question: Is the double-lobed Herschel/PACS feature around zeta2 Reticuli a real eccentric edge-on debris disc, or background contamination?  
  > "Follow-up observations with *Herschel*/PACS revealed a double-lobed feature, that displayed asymmetries both in brightness and position." (abstract)
- Target **zeta2 Reticuli (HR 1010, HIP 15371, HD 20807)**: coordinates _not stated_; z/distance 12 pc  
  > "is a 3 Gyr-old G1V solar-type star (cite: 2013A&A...555A..11E; 2014ApJ...785...33S), located at 12 pc" (1 Introduction); distance from Hipparcos/Gaia (cite: 2007A&A...474..653V; 2016A&A...595A...1G; 2018arXiv180409365G)  
  > "is a 3 Gyr-old G1V solar-type star (cite: 2013A&A...555A..11E; 2014ApJ...785...33S), located at 12 pc" (1 Introduction)

## Data provenance

- ALMA projects: 2017.1.00786.S
- bands: Band 6 (230 GHz, 1.3 mm) and Band 7 (345 GHz, 870 microns)  
  > "in Band 6 (230 GHz, 1.3mm), that were carried out from Nov 4th to Nov 18th 2017, and in Band 7 (345 GHz, 870 microns)" (2 Observations)
- frequencies and spectral setup: Band 7: three 2 GHz SPWs at 334, 336, 348 GHz (15.625 MHz channels) plus 1 GHz SPW at 346 GHz for CO 3-2; Band 6: SPWs at 232.5, 245.5, 247.5 GHz plus 230.5 GHz for CO 2-1  
  > "The spectral setup in Band 7 consisted of three 2 GHz-wide spectral windows, centred on 334, 336, and 348 GHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: ALMA/ACA  
  > "Here we present ALMA/ACA observations in Band 6 and 7" (abstract)
- configurations: _not stated_
- baselines: 8.9 to 48.9 m  
  > "These were both taken using baselines ranging from 8.9 to 48.9 m." (2 Observations)
- angular resolution: Band 7 4.77x3.2 arcsec; Band 6 6.62x4.60 arcsec  
  > "The resulting synthesized beam has dimensions $4".77 \times 3".2$, with position angle $88^{\circ}$." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 150 uJy/beam (Band 7); 66 uJy/beam (Band 6)  
  > "was found to be $\sigma=150\,\mu\mathrm{Jy/beam}$" (2 Observations)
- time on source: 6 h Band 7; 6.8 h Band 6  
  > "The total on-source time was 6 h in Band 7." (2 Observations); "The total on-source time was 6.8 h in Band 6." (2 Observations)
- observing dates: Band 7 27 Oct-22 Nov 2017; Band 6 4-18 Nov 2017  
  > "Band 7 (345 GHz, 870 microns), that were carried out from Oct 27th to Nov 22th 2017" (2 Observations)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (not stated)
- Line: CO J=2-1 (not stated)
- Other facility **Herschel/PACS and SPIRE**: Earlier double-lobed detection at 70/100 um and 250 um photometry for extrapolation  
  > "allowed the resolution of a double-lobed structure at these wavelengths" (1 Introduction)
- Other facility **Gaia**: Proper motion and distance  
  > "This work has made use of data from the European Space Agency (ESA) mission *Gaia*" (Acknowledgements)
- External data: Proper motion 1331.15 mas/yr in RA and 648.52 mas/yr in Dec  
  > "$1331.15 \pm 0.36\,\mathrm{mas/year}$ in Right Ascension and $648.52 \pm 0.43\,\mathrm{mas/year}$ in Declination" (3 Results) [from (cite: 2016A&A...595A...1G; 2018arXiv180409365G)]
- External data: Spectral index 2.6 for debris discs from SED modelling  
  > "the majority of debris discs have a spectral index of 2.6 or smaller (cite: 2017MNRAS.470.3606H)" (3 Results) [from (cite: 2017MNRAS.470.3606H)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "The data were calibrated using the pipeline provided by ALMA." (2 Observations)
- casa version: CASA 5.1.1  
  > "in CASA version 5.1.1" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean in CASA 5.1.1, four SPWs combined  
  > "In both cases, we combined the four spectral windows in order to recover the maximum signal-to-noise (S/N) ratio" (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "used a Briggs weighting scheme with robustness parameter set to 0.5" (2 Observations)
- uv taper: _not stated_
- cell size: 0.2 arcsec (B7), 0.3 arcsec (B6)  
  > "For our Band 7 image, we used a cell size of 0".2" (2 Observations)
- image size: 286x286 (B7), 210x210 (B6) pixels  
  > "an image size of $286\times 286$ pixels in order to cover the primary beam" (2 Observations)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied  
  > "We further corrected the images for the primary beam" (2 Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 150 uJy/beam (B7), 66 uJy/beam (B6)  
  > "while the rms was found to be $\sigma=66\,\mu\mathrm{Jy/beam}$" (2 Observations)

### Not stated but needed to reproduce (our reading)

- Deconvolver, masking and clean threshold
- Method of combining the multiple execution blocks
- Mosaic phase centres for Band 7
- Details of Gaussian fits for lobes
- How surface brightness limits were converted from sigma
- Herschel/SPIRE 250 um flux used for extrapolation

## Analysis recipe

1. **Image continuum**: tclean of combined SPWs, Briggs weighting, primary beam correction  
  > "We used the *TCLEAN* algorithm and task in CASA version 5.1.1" (2 Observations)
   - software: CASA
   - parameter: robust 0.5; cell 0.2"/0.3"  
  > "Briggs weighting scheme with robustness parameter set to 0.5" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Test common proper motion of lobes**: Compute stellar displacement since Herschel (7.75 yr) from Gaia proper motion and compare with lobe positions  
  > "it is expected to have displaced by 11".5 in the North-East direction (position angle of $64^{\circ}$) since it was observed with *Herschel* in February 2010" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure lobe fluxes and sizes**: Gaussian ellipse fits deconvolved from beam  
  > "We modeled it with a Gaussian ellipse, which once deconvolved from the beam" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Test hypothetical faint disc detectability**: Extrapolate SPIRE 250 um flux with spectral index 2.6 assuming uniform surface brightness over 4 (B6) or 6 (B7) beams  
  > "extrapolating the flux of such a disc from *Herschel*/SPIRE photometric measurements at 250 microns, adopting a spectral index of 2.6" (3 Results)
   - assumption: uniform surface brightness; spectral index 2.6  
  > "Assuming that the disc surface brightness is uniform" (3 Results)
   - fitting: _not stated_
   - validation: Expected SNR is a conservative lower limit since pericentre/apocentre brighter  
  > "Hence the SNR quoted above are very conservative lower limits" (3 Results)

## Software

- **CASA** 5.1.1: tclean image reconstruction of continuum  
  > "We used the *TCLEAN* algorithm and task in CASA version 5.1.1" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band 6 3-sigma surface brightness upper limit | 5.7 | not stated | uJy/arcsec^2 | 4 | $5.7\,\mathrm{\mu Jy/arcsec^2}$ at 1.3 mm |
| Band 7 3-sigma surface brightness upper limit | 26 | not stated | uJy/arcsec^2 | 4 | $26\,\mathrm{\mu Jy/arcsec^2}$ at 870 microns |
| A1 integrated flux at 1.3 mm | 794 | 106 | uJy | 3 | with an integrated flux of $794 \pm 106\,\mu\mathrm{Jy}$ |
| A2 integrated flux at 870 um | 1.20 | 0.19 | mJy | 3 | with an integrated flux of $1.20\pm 0.19 \,\mathrm{mJy}$ |
| A2 integrated flux at 1.3 mm | 511 | 50 | uJy | 3 | with an integrated flux of $511\pm50\,\mu\mathrm{Jy}$ |
| Stellar displacement since Herschel | 11.5 | not stated | arcsec | 2 | it is expected to have displaced by 11".5 in the North-East direction |

## Qualitative findings

- No CO line emission detected in Band 6 or Band 7  
  > "Finally, no CO line emission was detected in Band 6, nor in Band 7." (3 Results)

## Claim tuples

- H: The Herschel double-lobe is an eccentric edge-on debris disc around zeta2 Ret | E: ACA Band 6/7 imaging and proper motion comparison | R: Lobes do not move with the star; no disc flux above 3 sigma | F: The feature is background confusion, not a debris disc | **supported**
- H: A faint real disc could hide below ALMA sensitivity | E: Extrapolate SPIRE flux with spectral index 2.6 | R: Disc would be detected at SNR >=2.5 (B7) and >=3 (B6) | F: This scenario is excluded | **supported**

## Reasoning

- Why this data: ACA resolution is similar to Herschel/PACS and observations 8 yr later allow a proper motion test  
  > "As the ALMA/Atacama Compact Array (ACA) performs (sub)mm observations with resolutions similar to that of *Herschel*/PACS" (1 Introduction)
- Why this method: _not stated_
- Alternative: A1/H1 and A2/H2 may be the same or unrelated sources; undecidable  
  > "does not allow us to tell for certainty whether the A1 and H1, and A2 and H2 emissions are related or not" (3 Results)
- How they decided it was enough: _not stated_
- Limitation (authors): A1 measurements at 870 um uncertain because far from phase centre  
  > "A1 is far from the phasecentre of the ALMA image at this wavelength, where uncertainties are very large and fitting difficult" (3 Results)
- Caveat (inferred, ours): Upper limits depend on the assumed spectral index and uniform brightness
- Caveat (inferred, ours): Source nature of A1/A2 unresolved
- Caveat (inferred, ours): No uv-based or flux-calibration uncertainty discussion

## Reproducibility

- Data public (paper): Project code given; archive public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00786.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Clean parameters beyond robust and cell
- Missing: Surface brightness upper limit conversion
- Data volume (inferred): ~10-30 GB raw (17 ACA execution blocks)
- Score (inferred): 6/5, Simple imaging with key parameters given; detection analysis and limit derivation lack detail.
- Rediscovery candidate: yes, Data are from a PI project whose proprietary period has likely expired; imaging recipe and numeric flux/limit results are given.

## Links

- Companion: (cite: 2018MNRAS.475.3046S) (Independently suggested lobes are background objects)
- Companion: (cite: 2010A&A...518L.131E) (Original Herschel/PACS detection of the lobes)
- Related: Herschel DUNES

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
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 36,
  "rate": 0.554
 },
 "evidence_ok": true
}
```
