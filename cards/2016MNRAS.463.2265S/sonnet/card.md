# The peculiar dipping events in the disc-bearing young-stellar object EPIC 204278916

`2016MNRAS.463.2265S` | Monthly Notices of the Royal Astronomical Society 2016 | first author: Scaringi, S. | arXiv: 1608.07291 | DOI: 10.1093/mnras/stw2155

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: protoplanetary_disks, stellar_physics
- Question: What causes the irregular large-amplitude dips in the K2 light curve of the disk-bearing young star EPIC 204278916?  
  > "We examine the *K2* light curve in detail and hypothesise that the irregular dimmings are caused by either a warped inner-disk edge or transiting cometary-like objects in either circular or eccentric orbits." (abstract)
- Target **EPIC 204278916 (2MASS J16020757-2257467)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: mean frequency 341.1 GHz (0.88 mm)  
  > "in four spectral windows centred at 334.2, 336.1, 346.2, and 348.1 GHz for a mean frequency of 341.1 GHz (0.88 mm)" (2.2 ALMA observations)
- frequencies and spectral setup: four spectral windows at 334.2, 336.1, 346.2, 348.1 GHz, 1.875 GHz each  
  > "The bandwidth of each window is 1.875 GHz." (2.2 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 16-650 m, 36 antennas  
  > "Thirty six antennas were included in the array, with baselines ranging from 16-650 m for an angular resolution of 0.34 arcseconds." (2.2 ALMA observations)
- angular resolution: 0.34 arcsec  
  > "with baselines ranging from 16-650 m for an angular resolution of 0.34 arcseconds." (2.2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2014 June 30 and 2014 July 7 (Cycle 2)  
  > "ALMA Cycle 2 observations of EPIC 204278916 were obtained on 2014 June 30 and 2014 July 7 (UT)" (2.2 ALMA observations)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (not stated)
- Other facility **K2 (Kepler)**: Long-cadence light curve from MAST, Campaign 2, 78.8 days  
  > "Here we analyse long cadence (LC, 29.4 minutes) data obtained from the Mikulski Archive for Space Telescope (MAST) archive" (2.1 K2 light curve)
- External data: Stellar luminosity log L=0.15, spectral type M1, Halpha EW=-3.2 A  
  > "has a logarithmic bolometric stellar luminosity log$L_\star/L_\odot$ = 0.15 ((cite: preibisch02))" (1 Introduction) [from (cite: preibisch02)]

## Processing

### Calibration

- pipeline or manual: CASA reduction scripts provided by NRAO  
  > "The ALMA data were calibrated using the CASA package. The reduction scripts were kindly provided by NRAO." (2.2 ALMA observations)
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

- ALMA observation details and data reduction  
  > "For further details on the observations and data reduction, see (cite: barenfeld16)." (2.2 ALMA observations) [from (cite: barenfeld16)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Flux calibrator and imaging parameters for continuum image
- Details of elliptical Gaussian visibility fit
- Stellar distance
- Fit settings for the multi-Gaussian light-curve model

## Analysis recipe

1. **Fit continuum disk inclination**: Elliptical Gaussian fit to the continuum visibilities; inclination from axis ratio assuming a circular disk  
  > "An elliptical Gaussian fit of the surface brightness profile to the continuum visibility data results in an axis ratio of 0.55 $\pm$ 0.13" (2.2 ALMA observations)
   - assumption: circular disk  
  > "implying a disk inclination of 57 $\pm$ 9 degrees and assuming a circular disk." (2.2 ALMA observations)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : ALMA calibration  
  > "The ALMA data were calibrated using the CASA package." (2.2 ALMA observations)
- **MATLAB FINDPEAK** : peak finding to identify 53 dips  
  > "Using a local peak finding algorithm (FINDPEAK implemented in MATLAB) we identify 53 dips." (3.3 Transiting circumstellar clumps)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk axis ratio | 0.55 | 0.13 | dimensionless | 1 | results in an axis ratio of 0.55 $\pm$ 0.13 |
| Disk inclination | 57 | 9 | degrees | 1 | implying a disk inclination of 57 $\pm$ 9 degrees |

## Qualitative findings


## Claim tuples

- H: Are the dips due to a warped inner disk edge? | E: Compared maximum co-inclination with ALMA disk inclination | R: i_max=14 deg vs ALMA 57 deg | F: Warped inner disk is disfavoured | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): ALMA is used only for disk inclination, from a simple Gaussian fit, so the result is weakly constrained

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Barenfeld et al. 2016 reduction details
- Data volume (inferred): tens of GB
- Score (inferred): 2/5, ALMA role is minor and most settings are deferred to another paper.
- Rediscovery candidate: no, ALMA analysis is minimal and delegated.

## Links

- Method: (cite: barenfeld16) (ALMA data reduction and observation details)
- Companion: (cite: ansdell16b) (Similar dipper YSOs resolved with ALMA)
- Related: K2 Campaign 2

## Checks

```json
{
 "quotes": 19,
 "quotes_ok": 19,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00395.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 52,
  "stated": 14,
  "rate": 0.269
 },
 "evidence_ok": true
}
```
