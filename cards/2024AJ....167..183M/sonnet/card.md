# JWST/NIRCam Imaging of Young Stellar Objects. III. Detailed Imaging of the Nebular Environment around the HL Tau Disk

`2024AJ....167..183M` | The Astronomical Journal 2024 | first author: Mullin, Camryn | arXiv: 2403.00908 | DOI: 10.3847/1538-3881/ad2de9

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What is the nebular environment of HL Tau in JWST/NIRCam imaging, and what planet detection limits can be set inside and outside the disk?  
  > "we use JWST NIRCam’s direct imaging mode in F187N, F200W, F405N, and F410M to perform high contrast observations of the circumstellar structures surrounding the protostar HL Tau." (abstract)
- Target **HL Tau**: coordinates RA 04:31:38.425, Dec +18:13:57.242 (J2000)  
  > "| RA (J2000)              |  04:31:38.425   |     1     |" (Table 1); "| Distance \[pc\]         |      $140$      |     2     |" (Table 1); z/distance 140 pc  
  > "| RA (J2000)              |  04:31:38.425   |     1     |" (Table 1); "| Distance \[pc\]         |      $140$      |     2     |" (Table 1); distance from Table 1 reference 2 (not resolved in text)  
  > "| RA (J2000)              |  04:31:38.425   |     1     |" (Table 1); "| Distance \[pc\]         |      $140$      |     2     |" (Table 1)

## Data provenance

- ALMA projects: 2011.0.01234.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: HCO+ not stated (not stated)
- Other facility **JWST/NIRCam**: Direct imaging in F187N, F200W, F405N, F410M (program 1179), main data  
  > "Our observations of HL Tau were taken on UT 2022-09-29 with JWST/NIRCam in direct imaging (non-coronagraphic) mode as part of GTO program 1179" (Observation and Data Reduction)
- Other facility **HST**: 2004 archival images (GO 9862) at 0.6 micron for comparison  
  > "compare to 2004 HST observations from GO program 9862" (Outflow Cavity)
- External data: ALMA HCO+ moment 0 map of HL Tau, provided by the author, used for comparison  
  > "We would like to thank Yen Hsi-Wei for providing us with moment 0 ALMA $\textrm{HCO}^+$ data from (cite: Yen2019)." (Acknowledgements) [from (cite: Yen2019)]
- Simulation/model as data: BEX and AMES-COND evolutionary tracks at 1 Myr used to convert flux limits to planet mass  
  > "we used BEX (cite: Linder2019) evolutionary tracks for planets with $M_{\rm p} < 2 M_{\rm J}$ and AMES-COND models (cite: Chabrier2000) for more massive companions." (Sensitivity Limits)

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

### Not stated but needed to reproduce (our reading)

- ALMA HCO+ observational and imaging details (this paper only overlays Yen et al. 2019 moment 0 map)
- Which ALMA project code is actually used (2011.0.01234.S in the paper vs 2011.0.00015.SV in the archive link)

## Analysis recipe


## Software

- **jwst pipeline** 1.8.2 (crds 11.16.15): stage 1 and 2 calibration to calints  
  > "We reduced the data using the standard `jwst` pipeline (version 1.8.2 with crds version 11.16.15)" (Observation and Data Reduction)
- **PynPoint** : bad pixels, centering, PSF subtraction with PCA, synthetic planet injection  
  > "This pipeline managed bad pixel correction, centering, point-spread-function (PSF) generation, PSF subtraction, and synthetic planet injection." (Customized PynPoint Pipeline)
- **webbpsf** : model PSF for centering  
  > "we generated a perfectly centered model PSF using `webbpsf` (cite: Perrin2014)" (Centering)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Deepest mass limit, F410M at 3.75 arcsec (525 AU) | 0.75 | not stated | M_J | 0 | Our deepest limits are $\sim0.75~M_{\rm J}$ at 3.75$''$ (525 AU) separation in the F410M filter. |
| Mass sensitivity at 0.2-0.8 arcsec in disk region | >8.6 | not stated | M_J | 0 | At these separations, we are sensitive to companions with $M_{\rm p}>8.6~M_{\rm J}$. |

## Qualitative findings

- A SW spiral streamer seen in ALMA HCO+ is detected in scattered light at 4 micron; no planet candidates found.  
  > "The position of our spiral aligns with the $\textrm{HCO}^+$ spiral, though the shape is somewhat different at IR wavelengths." (Streamers)

## Claim tuples

- H: Is the ALMA HCO+ spiral streamer detected in NIRCam scattered light? | E: PSF-subtracted NIRCam images compared with Yen et al. HCO+ moment 0 map | R: Part of the spiral is seen at 4 micron, mainly in F405N, aligned with HCO+ spiral | F: The IR feature traces dust scattering along the streamer | **supported**
- H: Can NIRCam detect protoplanets in HL Tau | E: Synthetic planet injection with PSF subtraction | R: No candidates; limits 5.2 MJ in disk region, 0.75 MJ outside | F: Envelope prevents detecting gap-opening planets | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Roll-angle ADI rejected because of self-subtraction from the extended envelope; MWC 758 used as PSF reference.  
  > "The stellar envelope is bright at near-IR wavelengths, and azimuthally extended, which causes severe self-subtraction between the two roll angles." (PSF Subtraction)
- How they decided it was enough: _not stated_
- Limitation (authors): Over-subtraction from using MWC 758 as PSF reference hinders contrast at <1 arcsec.  
  > "This over-subtraction likely hinders our contrast performance (especially at $<1\ensuremath{''}$ separation)" (PSF Subtraction)
- Caveat (inferred, ours): ALMA is only used as a comparison map; no independent ALMA analysis
- Caveat (inferred, ours): Mass limits assume 1 Myr age and no extinction

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Exact ALMA data and moment map reproduction (provided privately by the author)
- Missing: PynPoint customizations not released
- Data volume (inferred): JWST data only; ALMA HCO+ map not reprocessed (small)
- Score (inferred): 2/5, ALMA role is a supporting comparison map obtained from another author; the main JWST analysis is not an ALMA reduction.
- Rediscovery candidate: no, ALMA data are not processed in this paper; the main results rely on JWST data.

## Links

- Method: (cite: Cugno2024) (JWST/NIRCam reduction and injection method followed)
- Companion: (cite: Wagner2024) (MWC 758 from the same GTO program)
- Related: JWST GTO 1179 Direct Imaging of YSOs

## Checks

```json
{
 "quotes": 25,
 "quotes_ok": 25,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.01234.S"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00015.SV"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 53,
  "stated": 14,
  "rate": 0.264
 },
 "evidence_ok": true
}
```
