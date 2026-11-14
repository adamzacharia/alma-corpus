# A tell-tale tracer for externally irradiated protoplanetary disks: Comparing the [C I] 8727 Å line and ALMA observations in proplyds

`2024A&A...692A.137A` | Astronomy and Astrophysics 2024 | first author: Aru, M.-L. | arXiv: 2410.21018 | DOI: 10.1051/0004-6361/202451737

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Whether the [C I] 8727 A line seen with VLT/MUSE-NFM traces externally driven photoevaporative winds, by comparing its location with the ALMA Band 7 dust continuum in 12 ONC proplyds and by checking its detection rate in low-mass star-forming regions  
  > "Here, we report a proxy for unambiguously identifying externally driven winds" (abstract); "To verify whether the" (abstract)
- Target **12 proplyds in the Orion Nebula Cluster (154-346, 167-325, 168-326, 170-249, 170-334, 170-337, 171-340, 173-236, 174-414, 177-341W, 203-504, 244-440); ALMA Band 7 available for 6 of them**: coordinates given per proplyd in Table 1 (RA/Dec, hh:mm:ss.s / dd:mm:ss.s)  
  > "We use data of the 12 proplyds showing prominent ionization fronts firstly presented by (cite: aru2024)." (Data and analysis); "Coordinates and projected separations of the sample of proplyds." (Table 1); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00534.S
- bands: Band 7 (0.86 mm)  
  > "performed in Band 7 (0.86 mm) with an angular resolution of 0.09"" (Data and analysis)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.09"  
  > "performed in Band 7 (0.86 mm) with an angular resolution of 0.09"" (Data and analysis)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Band 7 data described in Eisner et al. 2018 (cite: eisner2018); acknowledgement cites ADS/JAO.ALMA #2015.1.00534.S  
  > "The ALMA Band 7 data trace thermal dust emission from the disk, and they are described in (cite: eisner2018)." (Data and analysis)
- Line: [O I] (MUSE-NFM, not ALMA) forbidden line (5577 A and 6300 A (wavelength; frequency not stated))
- Line: [C I] (MUSE-NFM, not ALMA) 2p^2 1D2 forbidden line (8727 A (wavelength; frequency not stated))
- Other facility **VLT/MUSE-NFM**: Integral-field spectroscopy of the [O I] 5577, 6300 and [C I] 8727 line emission and stellar continuum of the 12 proplyds, the primary dataset compared with ALMA  
  > "These objects were observed with the VLT/MUSE integral-field spectrograph (cite: Bacon2010)." (Data and analysis); "MUSE was operated in NFM, which covers the wavelength range" (Data and analysis)
- Other facility **VLT/X-Shooter**: Spectra of young stars in low-mass SFRs (PENELLOPE) and sigma-Orionis used to measure [C I] 8727 detection rates  
  > "we use the publicly available spectra taken with VLT/X-Shooter for the PENELLOPE Large Program (cite: manara2021)" (Data and analysis)
- External data: Deconvolved FWHM major and minor axes of the ALMA disks, used to derive disk inclinations and position angles  
  > "calculated from their deconvolved FWHM major and minor axes listed by (cite: ballering2023)" (Data analysis) [from (cite: ballering2023)]
- External data: MUSE-NFM observations and data reduction of the 12 proplyds, and the continuum-subtracted emission line maps  
  > "Details regarding the observation and the data reduction process are described in (cite: haworth2023) for proplyd 203-504, and in (cite: aru2024) for the remainder of the sample." (Data and analysis) [from (cite: haworth2023); (cite: aru2024)]
- External data: VLT/X-Shooter spectra of low-mass SFR targets (PENELLOPE) and of sigma-Orionis  
  > "we examined 74 VLT/X-Shooter spectra from the PENELLOPE Large Program (cite: manara2021)" (Results and discussion) [from (cite: manara2021); (cite: mauco2023)]
- External data: Coordinates and projected separations of the sample proplyds  
  > "The information is from (cite: OdellWen1994; Bally2000DisksNebula; Ricci2008THENEBULA; Mann2014ALMAPROPLYDS)." (Table 1) [from (cite: OdellWen1994; Bally2000DisksNebula; Ricci2008THENEBULA; Mann2014ALMAPROPLYDS)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

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

- MUSE observation and data reduction details  
  > "Details regarding the observation and the data reduction process are described in (cite: haworth2023) for proplyd 203-504, and in (cite: aru2024) for the remainder of the sample." (Data and analysis) [from (cite: haworth2023); (cite: aru2024)]
- Continuum subtraction of the MUSE emission-line maps  
  > "compare the location of the continuum-subtracted emission (see (cite: aru2024) for details)" (Data analysis) [from (cite: aru2024)]
- Radial cut procedure on MUSE emission-line images  
  > "The procedure is described in more detail in (cite: aru2024)." (Radial cuts) [from (cite: aru2024)]
- ALMA Band 7 observations and reduction  
  > "The ALMA Band 7 data trace thermal dust emission from the disk, and they are described in (cite: eisner2018)." (Data and analysis) [from (cite: eisner2018)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, CASA version, imaging parameters (weighting, robust, cell, beam) and rms of the Band 7 continuum are not given; only a reference to Eisner et al. 2018
- Which ALMA execution blocks or products of 2015.1.00534.S were used
- imfit settings (region, components) for 168-326 and 171-340; inclinations and PAs for those two come from Ballering et al. in prep.
- Exact definition of how the MUSE stellar position and ALMA disk center were measured for the alignment (fitting method, apertures)
- How the peak offsets were measured from the radial cuts (smoothing, binning, peak finder)
- Detection criteria for [C I] 8727 in the X-Shooter spectra (S/N threshold, line fitting, 'tentative' definition)
- Public availability and archive identifiers of the MUSE-NFM cubes
- FUV field (G0) values per proplyd used in Figure 3

## Analysis recipe

1. **Align MUSE cubes to the ALMA continuum**: Measure reference points in MUSE and ALMA continuum images and shift the ALMA coordinates to match MUSE; for most proplyds the MUSE star position (continuum subcube 674-678 nm) is matched to the ALMA disk center; for 177-341W two background sources seen in both datasets are used  
  > "The alignment was done by measuring relevant references points in the MUSE and ALMA continuum images and shifting the coordinates of the ALMA image to align with MUSE." (Alignment and spatial comparison); "we carried out the matching by using two background sources present in both the ALMA and MUSE data" (Alignment and spatial comparison)
   - parameter: Alignment uncertainty taken as half the MUSE spaxel size (0.0125"), or 0.025" spaxel for 168-326, 174-414 and 203-504  
  > "We considered the uncertainty on this alignment to be half the spatial size of the MUSE spaxels (0.0125")" (Alignment and spatial comparison)
   - fitting: _not stated_
   - validation: _not stated_
2. **Overlay MUSE line contours on ALMA images**: MUSE line emission shown as contours at 50%, 70% and 90% of the peak intensity over the ALMA Band 7 images  
  > "which is shown with contours representing 50%, 70% and 90% of the peak intensity of the line emission" (Alignment and spatial comparison)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive disk inclinations and position angles from ALMA**: Inclinations from deconvolved FWHM major and minor axes listed by Ballering et al. 2023, or from CASA imfit on the ALMA data for 168-326 and 171-340  
  > "We report the inclinations of the disks, calculated from their deconvolved FWHM major and minor axes listed by (cite: ballering2023) and calculated using the CASA task imfit on the ALMA data for proplyds 168-326 and 171-340." (Alignment and spatial comparison)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
4. **Measure line-peak offsets from the star with radial cuts**: Emission along a 6" long line centered on the star (disk center for 177-341W) and oriented toward theta1 Ori C, on the MUSE emission-line images; offset of the line peak from the star, positive toward the UV source  
  > "This was performed by calculating the emission along a 6" long line centered at the coordinates of the central star and oriented towards the ionizing source" (Radial cuts); "The positive sign of the values on y-axis marks a peak located in the direction of the UV source, and the negative sign the opposite." (Results and discussion)
   - fitting: _not stated_
   - validation: Offsets compared with the alignment uncertainty (half spaxel); most are compatible with zero within the uncertainties  
  > "The values are compatible with no displacement within their uncertainties" (Results and discussion)
5. **Compute relative inclination of each disk with respect to the UV source**: Spherical law of cosines using the ALMA disk position angle and inclination and the star-UV source position angle  
  > "we calculate the relative inclination of the disks using the spherical law of cosines" (Results and discussion)
   - assumption: Inclination of the UV source emission in the plane of the sky taken as i2 = 90 deg  
  > "the inclination we assume for the emission coming from the UV source in the plane of the sky" (Results and discussion)
   - fitting: _not stated_
   - validation: _not stated_
6. **Count [C I] 8727 and [O I] detections in X-Shooter spectra of low-mass SFR disks**: Examine 74 PENELLOPE and 45 sigma-Orionis X-Shooter spectra for the lines and compute detection rates  
  > "we examined 74 VLT/X-Shooter spectra from the PENELLOPE Large Program (cite: manara2021)" (Results and discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : imfit task on the ALMA data for proplyds 168-326 and 171-340 to obtain disk sizes and inclinations  
  > "calculated using the CASA task imfit on the ALMA data for proplyds 168-326 and 171-340" (Alignment and spatial comparison)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Offset of [O I] 6300 peak from the star, proplyd 177-341W | 0.0931 | 0.0125 | arcsec | 4 | 0.0931 $\pm$ 0.0125 |
| Offset of [C I] 8727 peak from the star, proplyd 177-341W | 0.101 | 0.0125 | arcsec | 4 | 0.101 $\pm$ 0.0125 |
| Disk inclination of 177-341W | 73.6 | 2.9 | deg | 3 | an inclined disk of $i$=73.6 $\pm$ 2.9 deg |
| Detection rate of [O I] 5577 in PENELLOPE low-mass SFR sample | 68% | not stated | percent of targets | 6 | The [O I] 5577 Å line is detected in 68% of the targets, and the [O I] 6300 Å line in 88% of the targets in the PENELLOPE sample |
| Detection rate of [O I] 6300 in PENELLOPE low-mass SFR sample | 88% | not stated | percent of targets | 6 | The [O I] 5577 Å line is detected in 68% of the targets, and the [O I] 6300 Å line in 88% of the targets in the PENELLOPE sample |
| Detection rate of [C I] 8727 in PENELLOPE sample (1 clear plus 7 tentative of 74) | <<10% | not stated | percent of targets | 6 | with 7 additional tentative detections, for a total of $\ll10\%$ detection rate |
| Detection rate of [C I] 8727 in sigma-Orionis (45 spectra) | ~40% | not stated | percent of targets | 6 | This number increases substantially to a $\sim40\%$ detection rate in |
| Detection rate of [C I] 8727 in the 12 ONC proplyds (MUSE-NFM) | 100% (12 of 12) | not stated | percent of targets | 0 | the detection of this line in all 12 proplyds in our sample |

## Qualitative findings

- [C I] 8727 emission is co-spatial with the ALMA disk emission with no ionization-front contribution, and traces the disk shape more closely than [O I] in inclined disks 173-236 and 177-341W  
  > "No contribution from the ionization front is present, and the line is emitted only from the disk surface and/or base of the externally photoevaporating wind." (Results and discussion)
- [O I] 5577 is bound to the disk region while [O I] 6300 comes from both the disk and the ionization front  
  > "The major difference between the two oxygen emission lines is that" (Results and discussion)
- Only 177-341W (highest relative inclination) shows a clear peak displacement toward the UV source  
  > "The proplyd 177-341W has the highest relative inclination, which could indeed explain that the displacement arises from" (Results and discussion)

## Claim tuples

- H: The [C I] 8727 line arises from the disk surface/base of the external photoevaporative wind in proplyds | E: Aligned MUSE-NFM line maps with ALMA Band 7 continuum for 6 proplyds and with the MUSE stellar continuum for all 12, and compared contours and peak offsets | R: [C I] 8727 contours follow the ALMA disk shape, with peak compatible with the star in all but 177-341W | F: [C I] 8727 is co-spatial with the disk surface and not the ionization front | **supported**
- H: The two [O I] lines trace different regions in proplyds | E: Compared MUSE [O I] 5577 and 6300 contours with the ALMA disk continuum and the stellar continuum | R: [O I] 5577 is co-spatial with the disk; [O I] 6300 comes from both the disk and the ionization front | F: Confirms earlier results that 5577 is a disk tracer and 6300 also traces the ionization front | **supported**
- H: [C I] 8727 is a tell-tale tracer of external photoevaporation, absent in isolated disks | E: Compared detection rates of [C I] 8727 and [O I] in X-Shooter spectra of PENELLOPE (low-mass SFRs) and sigma-Orionis targets with the 12 ONC proplyds | R: One clear plus 7 tentative detections of 74 in PENELLOPE (<<10%), ~40% in sigma-Orionis, 12 of 12 in ONC | F: Detection rate rises with external UV field, supporting the FUV-pumping excitation models | **supported**
- H: The offset of the line peak toward the UV source depends on the disk inclination relative to the UV source | E: Computed relative inclinations with the spherical law of cosines for the six proplyds with ALMA inclinations and compared with peak offsets | R: Only 177-341W (highest relative inclination) has a significant offset | F: Possible explanation, needing a larger sample | **partially**

## Reasoning

- Why this data: ALMA Band 7 traces the thermal dust disk, giving a reference position for the disk against which the MUSE line emission is compared  
  > "The ALMA Band 7 data trace thermal dust emission from the disk" (Data and analysis); "show that the Band 7 data does not trace the ionization front" (Data and analysis)
- Why this method: MUSE-NFM astrometry is uncertain, so the cubes must be aligned to ALMA before comparing positions  
  > "As MUSE-NFM is known to have uncertain astrometric accuracy, it is necessary to align the MUSE cubes with the ALMA data" (Alignment and spatial comparison)
- How they decided it was enough: _not stated_
- Limitation (authors): Disk inclination and position angle are missing for half of the sample (no ALMA data), so the relative-inclination explanation cannot be tested further  
  > "The lack of measurements of the disk inclination and position angle for half of our sample hinders the possibility to further confirm this is due to the relative inclination of the disks and the external UV radiation." (Results and discussion)
- Limitation (authors): The relative-inclination hypothesis needs a larger sample  
  > "This hypothesis needs confirmation on a larger sample of targets." (Results and discussion)
- Caveat (inferred, ours): ALMA is used only as a positional reference; no ALMA reduction or imaging details are given
- Caveat (inferred, ours): Offsets are mostly consistent with zero within half-spaxel uncertainties, so the comparison depends on the alignment assumption that the star sits at the ALMA disk center
- Caveat (inferred, ours): Detection rates in X-Shooter spectra rest on unstated S/N criteria and different spectral resolution and sensitivity from MUSE-NFM
- Caveat (inferred, ours): Inclination and PA are missing for 6 of 12 proplyds and two values rely on a paper in prep.

## Reproducibility

- Data public (paper): X-Shooter PENELLOPE spectra are stated to be publicly available; ALMA and MUSE availability not stated beyond the acknowledgement of ALMA project 2015.1.00534.S  
  > "Lastly, we use the publicly available spectra taken with VLT/X-Shooter for the PENELLOPE Large Program (cite: manara2021)" (Data and analysis)
- Products in archive: _not stated_
- Missing: ALMA calibration and imaging recipe (only a reference to Eisner et al. 2018)
- Missing: MUSE reduction and line-map construction (deferred to Aru et al. 2024 and Haworth et al. 2023)
- Missing: Peak-finding and alignment procedure details
- Missing: Line-detection criteria for the X-Shooter spectra
- Missing: Inclinations for 168-326 and 171-340 from a paper in prep.
- Data volume (inferred): Tens of GB for the six ALMA Band 7 datasets plus MUSE-NFM cubes (not stated in the paper)
- Score (inferred): 2/5, The ALMA part is a positional comparison with no processing recipe, the MUSE inputs are deferred to other papers, and the numeric results are few offsets and detection rates.
- Rediscovery candidate: no, MUSE processing and ALMA reduction are deferred to other papers, and the main conclusions are largely qualitative spatial comparisons.

## Links

- Method: (cite: aru2024) (MUSE-NFM observations, data reduction, continuum subtraction and radial cut procedure for the 12 proplyds)
- Method: (cite: haworth2023) (MUSE data reduction for proplyd 203-504)
- Method: (cite: eisner2018) (Describes the ALMA Band 7 data)
- Method: (cite: ballering2023) (Deconvolved disk sizes used for inclination and position angle)
- Companion: (cite: Goicoechea2024) (FUV-pumping excitation models for the IR carbon lines, which the results support)
- Companion: (cite: manara2021) (PENELLOPE Large Program X-Shooter spectra)
- Companion: (cite: mauco2023) (X-Shooter spectra of sigma-Orionis)
- Related: PENELLOPE Large Program (VLT/X-Shooter)
- Related: ESO programmes 0104.C-0963(A), 106.218X.001, 110.259E.001 (MUSE-NFM)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 33,
  "rate": 0.418
 },
 "evidence_ok": true
}
```
