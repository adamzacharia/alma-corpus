# A NIRCam-dark Galaxy Detected with the MIRI/F1000W Filter in the MIDIS/JADES Hubble Ultra Deep Field

`2024ApJ...969L..10P` | The Astrophysical Journal Letters 2024 | first author: Pérez-González, Pablo G. | arXiv: 2402.16942 | DOI: 10.3847/2041-8213/ad517b

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: What is the nature of Cerberus, a NIRCam-dark extremely red source detected in MIRI/F1000W imaging of the HUDF?  
  > "we discuss the possible nature of this red NIRCam-dark source using a battery of codes." (abstract)
- Target **Cerberus**: coordinates 03:32:38.09, -27:47:11.81 (J2000)  
  > "Its coordinates (J2000) are $\alpha =$ 03:32:38.09 (hours), $\delta =$$-$27:47:11.81 (degrees)." (3.1 Selection of NIRCam-dark sources); z/distance photo-z solutions z~0.4, z~4, z~14-15 (also ~17, ~19)  
  > "Its coordinates (J2000) are $\alpha =$ 03:32:38.09 (hours), $\delta =$$-$27:47:11.81 (degrees)." (3.1 Selection of NIRCam-dark sources); distance from SED fitting  
  > "Its coordinates (J2000) are $\alpha =$ 03:32:38.09 (hours), $\delta =$$-$27:47:11.81 (degrees)." (3.1 Selection of NIRCam-dark sources)

## Data provenance

- ALMA projects: _none stated_
- bands: 1.2 mm and 3.0 mm (ASPECS)  
  > "is a Cycle 4 Large Program over a 4.6 arcmin$^{2}$ scan at 1.2 mm" (2.2.3 ALMA data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.5"x1.1" (1.2 mm); 1.8"x1.5" (3.0 mm)  
  > "The 3.0 mm data reaches 1.4 $\mu$Jy/beam, with a $1.8\ensuremath{''}\times1.5\ensuremath{''}$ beam." (2.2.3 ALMA data)
- max recoverable scale: _not stated_
- sensitivity: 1.2 mm: 9.3 uJy/beam rms; 3.0 mm: 1.4 uJy/beam  
  > "The ultra-deep 1.2 mm data reaches an rms sensitivity of 9.3 $\mu$Jy/beam" (2.2.3 ALMA data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **JWST/MIRI (MIDIS)**: F1000W and F560W imaging  
  > "for a total on source exposure time of 30800 s" (2.1 MIRI data)
- Other facility **JWST/NIRCam (JADES DR2)**: 14 bands 0.9-4.8 um  
  > "This dataset provides a total of 14 bands from 0.9 to 4.8 $\mu$m" (2.2.2 NIRCam data)
- Other facility **VLT/MUSE**: spectra, no feature found  
  > "but found no significant spectral feature at the position of the NIRCam-dark candidate." (3.2.2 MUSE measurements)
- External data: ASPECS 1.2 mm and 3.0 mm ALMA data  
  > "(cite: Decarli_2020; gonzalez-lopez2020) and 3.0 mm (cite: Decarli_2019; gonzalez-lopez2019)" (2.2.3 ALMA data) [from Decarli 2019, 2020; González-López 2019, 2020]
- External data: JADES DR2 NIRCam imaging and catalog  
  > "Data Release 2 ((cite: 2023arXiv231012340E))" (2.2.2 NIRCam data) [from Eisenstein 2023b]

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

- MIRI data reduction methodology  
  > "The reduction of the MIRI data followed the methodology described in (cite: 2024arXiv240108782P)" (2.1 MIRI data) [from (cite: 2024arXiv240108782P)]

### Not stated but needed to reproduce (our reading)

- ALMA project/member IDs and how ASPECS products were used
- how the 5-sigma ALMA upper limits were computed (position, beam, primary-beam correction)
- SED fitting priors and parameter grids in detail

## Analysis recipe

1. **ALMA forced upper limits**: Non-detection at source position; 5 sigma upper limits assuming unresolved point source, used as SED constraints  
  > "This finding implies $5\sigma$ upper limits on the flux density at 1.2 mm and 3.0 mm of 47 $\mu$Jy and 7 $\mu$Jy respectively" (3.2.3 ALMA measurements)
   - assumption: unresolved point-like source  
  > "assuming it is effectively an unresolved point-like source." (3.2.3 ALMA measurements)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **eazy** : photometric redshift fitting  
  > "We first used the eazy code (cite: 2008ApJ...686.1503B) to fit the data in 2 ways" (Appendix)
- **prospector** : photo-z and stellar population fitting  
  > "We fitted the extracted photometry of *Cerberus* with prospector" (Appendix)
- **SExtractor** : hot-mode source detection on F1000W  
  > "we executed the SEXTRACTOR software (cite: 1996A&AS..117..393B) directly using the MIRI/F1000W as the detection image" (3.1 Selection of NIRCam-dark sources)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 1.2 mm 5-sigma upper limit | 47 | not stated | uJy | 1 | upper limits on the flux density at 1.2 mm and 3.0 mm of 47 $\mu$Jy and 7 $\mu$Jy respectively |
| ALMA 3.0 mm 5-sigma upper limit | 7 | not stated | uJy | 1 | upper limits on the flux density at 1.2 mm and 3.0 mm of 47 $\mu$Jy and 7 $\mu$Jy respectively |
| F1000W magnitude | 27.13 | 0.17 | AB mag | 0 | F1000W        / 9.968 / 1.795 / $27.13\pm0.17$ |

## Qualitative findings

- Cerberus is real, NIRCam-dark, not a Solar System body, and unlikely a brown dwarf; extragalactic z~0.4, ~4 or ~15 solutions remain  
  > "A sub-stellar Galactic nature is deemed unlikely" (abstract)

## Claim tuples

- H: Cerberus is a real NIRCam-dark source | E: Partial MIRI mosaics and NIRCam stacks | R: Source persists in all 165 skip-3 mosaics; detected in stacks at S/N>5 | F: Source is real | **supported**
- H: Nature of Cerberus | E: SED fitting with multiple codes plus ALMA upper limits | R: Multiple redshift solutions | F: Nature remains uncertain | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Solar System body rejected via 0.016" centroid agreement across one year  
  > "indicates that *Cerberus* cannot be a Solar System body" (4.2.2 Solar System origin)
- How they decided it was enough: _not stated_
- Limitation (authors): SED very noisy, physical properties highly uncertain  
  > "the physical properties of the source are highly uncertain, starting from its redshift" (4.2 Analysis of the SED)
- Caveat (inferred, ours): ALMA plays only a minor role as upper limits
- Caveat (inferred, ours): low S/N photometry
- Caveat (inferred, ours): MIRI and NIRCam epochs differ

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA project IDs
- Missing: full SED fit configurations
- Data volume (inferred): small for ALMA (released ASPECS products); JWST images tens of GB
- Score (inferred): 3/5, ALMA role minimal; JWST data public but recipe partial.
- Rediscovery candidate: no, ALMA part is only upper limits; main results rely on JWST.

## Links

- Method: (cite: 2024arXiv240108782P) (MIRI reduction method)
- Related: ASPECS
- Related: MIDIS
- Related: JADES

## Checks

```json
{
 "quotes": 27,
 "quotes_ok": 27,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2016.1.00324.L"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 59,
  "stated": 21,
  "rate": 0.356
 },
 "evidence_ok": true
}
```
