# The Compact Object and Innermost Ejecta of SN 1987A

`2025ApJ...991..130L` | The Astrophysical Journal 2025 | first author: Larsson, J. | arXiv: 2508.03395 | DOI: 10.3847/1538-4357/adf741

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, other
- Question: What are the properties of the compact object and innermost ejecta of SN 1987A, using second-epoch JWST NIRSpec and MIRI/MRS spectroscopy (with ALMA dust maps used for comparison)?  
  > "Here, we aim to improve our understanding of the innermost ejecta and compact object in SN 1987A by analyzing new JWST Cycle 2 observations with NIRSpec and MIRI/MRS." (Introduction)
- Target **SN 1987A**: coordinates _not stated_; z/distance 49.6 kpc (LMC)  
  > "adopt a distance to the LMC of 49.6 kpc (cite: Pietrzynski2019)" (Analysis and results); distance from Pietrzynski2019  
  > "adopt a distance to the LMC of 49.6 kpc (cite: Pietrzynski2019)" (Analysis and results)

## Data provenance

- ALMA projects: 2015.1.00631.S, 2021.1.00707.S
- bands: _not stated_
- frequencies and spectral setup: 315 GHz and 679 GHz dust images  
  > "Figure 25 shows ALMA images of the ejecta dust at 315 and 679 GHz" (Comparison with ALMA images)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 315 GHz at 12,700 days; 679 GHz at 10,400 days after explosion  
  > "at 12,700 days for the 315 GHz image (cite: Matsuura2024), and 10,400 days for the 679 GHz image (cite: Cigan2019)" (Comparison with ALMA images)
- pi or archival as stated: _not stated_
- Other facility **JWST NIRSpec IFU and MIRI/MRS**: Main data: spatially resolved 1-28 micron spectroscopy of SN 1987A (programs 3131, 1232, 2763)  
  > "JWST Cycle 2 observations with the NIRSpec IFU were carried out on 2024 February 20–21, 13,511–13,512 days after the explosion (PID 3131, PI J. Larsson)." (Observations and data reduction)
- Other facility **HST WFC3/F657N**: Image used for NIRSpec astrometry and comparison (PID 16996)  
  > "The HST image was obtained on 2024 February 27, just a week after the NIRSpec observations, using the WFC3/F657N filter (PID 16996, PI: J. Larsson)." (Observations and data reduction)
- External data: ALMA 679 GHz dust image (observed at 10,400 days) and its 15 mas astrometric uncertainty  
  > "(cite: Cigan2019) report an astrometric uncertainty of 15 mas for the ALMA 679 image" (Comparison with ALMA images) [from (cite: Cigan2019)]
- External data: ALMA 315 GHz dust image (12,700 days)  
  > "at 12,700 days for the 315 GHz image (cite: Matsuura2024)" (Comparison with ALMA images) [from (cite: Matsuura2024)]

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
- cell size: ALMA images resampled to the 10 mas pixel scale of the 315 GHz image (reproject, bilinear)  
  > "All images in Figure 25 were resampled to the 10 mas pixel scale of the 315 GHz image using `astropy/reproject` (cite: reproject2020) with bilinear interpolation." (Comparison with ALMA images)
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

- ALMA images are taken as published, not reprocessed  
  > "at 12,700 days for the 315 GHz image (cite: Matsuura2024), and 10,400 days for the 679 GHz image (cite: Cigan2019)" (Comparison with ALMA images) [from Matsuura2024; Cigan2019]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, imaging and beam parameters (taken from earlier papers)
- How the ALMA images were registered or aligned with the JWST/HST frames
- Which project code corresponds to which ALMA image

## Analysis recipe

1. **Compare ALMA dust maps with JWST line positions**: Resample ALMA 315/679 GHz and HST images to a common 10 mas grid and overlay the [Ar VI] and [Ca IV] positions; assess offsets against astrometric uncertainties; show homologous expansion contours  
  > "The dashed black contours in the middle panel of Figure 25 illustrate this effect, assuming homologous expansion from the center" (Comparison with ALMA images)
   - software: astropy/reproject
   - assumption: Homologous expansion over about 3,100 days between the 679 GHz and JWST epochs (~30%)  
  > "during which time the ejecta would have expanded by nearly 30%" (Comparison with ALMA images)
   - fitting: _not stated_
   - validation: Offset compared with combined astrometric and statistical uncertainties (3 sigma)  
  > "We find that the offset is within the 3$\sigma$ confidence intervals (but outside the 2$\sigma$ intervals)" (Comparison with ALMA images)

## Software

- **astropy/reproject** : Resampling ALMA and HST images to a common pixel grid  
  > "using `astropy/reproject` (cite: reproject2020) with bilinear interpolation" (Comparison with ALMA images)
- **JWST Calibration Pipeline** 1.13.4: Processing NIRSpec data  
  > "processed with version 1.13.4 of the JWST Calibration Pipeline (cite: Bushouse2023)" (Observations and data reduction)
- **photutils DAOStarFinder** 1.9.0: Point-source detection in line images  
  > "We use the `DAOStarFinder` tool from `photutils` (cite: Bradley2023) to carry out the source detection" (Upper limits on narrow lines from the central ejecta)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [Ar VI] source offset from ER center (blue interval) | 30 mas south, 63 mas east (PA=116 deg) | ±10 mas each; PA ±8 deg | mas | 0 | offsets of ($30\pm 10$ mas south, $63\pm 10$ mas east) for \[-400, -100\] $\rm{km\ s^{-1}}$ |
| 3D neutron star kick velocity | 510 | ±55 | km/s | 0 | The offset and blueshift could imply a kick velocity of $510 \pm 55$ $\rm{km\ s^{-1}}$ for the neutron star. |

## Qualitative findings

- The [Ar VI] and [Ca IV] positions lie within the bright 315 GHz dust emission; the 679 GHz dust blob peak is offset NE of [Ar VI] by 2-3 sigma, but the ~10-year expansion prevents firm conclusions.  
  > "Considering these uncertainties, we cannot draw any firm conclusions about the connection between the dust blob and line-emitting region." (Comparison with ALMA images)

## Claim tuples

- H: Is the ALMA 679 GHz dust blob co-located with the JWST [Ar VI] compact-object source? | E: Overlay JWST line positions on ALMA 315 and 679 GHz images accounting for astrometric errors and expansion | R: Blob peak offset NE of [Ar VI] by between 2 and 3 sigma | F: No firm conclusion about a connection | **partially**
- H: Do the innermost ejecta lines imply a neutron star kick? | E: Combine [Ar VI] offset and Doppler shift | R: 3D kick of 510±55 km/s | F: Consistent with a compact object kick, assuming it is near the emitting region | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): The ~3,100 day gap and ~30% ejecta expansion between ALMA 679 GHz and JWST epochs complicate the comparison; ALMA astrometry is 10-15 mas.  
  > "a major complication in this comparison is that the observations were obtained $\sim 3,100$ days apart" (Comparison with ALMA images)
- Caveat (inferred, ours): The ALMA role is a qualitative overlay only; no new ALMA analysis was done
- Caveat (inferred, ours): Kick estimate relies on assuming the center of explosion and neutron star location

## Reproducibility

- Data public (paper): JWST data available from MAST  
  > "The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute" (Summary and conclusions)
- Products in archive: _not stated_
- Missing: ALMA image products and processing details come from earlier papers
- Missing: Photoionization and Monte Carlo codes not released
- Data volume (inferred): ALMA part: small (published images); JWST cubes ~ tens of GB
- Score (inferred): 2/5, ALMA used only as a published-image comparison; main analysis is JWST.
- Rediscovery candidate: no, ALMA data are minor and the main results are JWST-based.

## Links

- Companion: (cite: Fransson2024) (First-epoch JWST detection of the compact object)
- Companion: (cite: Cigan2019) (ALMA 679 GHz dust maps)
- Companion: (cite: Matsuura2024) (ALMA 315 GHz image)
- Related: JWST GTO 1232
- Related: JWST GTO 2763
- Related: JWST GO 3131

## Checks

```json
{
 "quotes": 27,
 "quotes_ok": 27,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2021.1.00707.S"
 ],
 "obscore_codes_not_in_card": [
  "2021.1.00701.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 57,
  "stated": 20,
  "rate": 0.351
 },
 "evidence_ok": true
}
```
