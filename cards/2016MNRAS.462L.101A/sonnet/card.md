# Dipper discs not inclined towards edge-on orbits

`2016MNRAS.462L.101A` | Monthly Notices of the Royal Astronomical Society 2016 | first author: Ansdell, M. | arXiv: 1607.03115 | DOI: 10.1093/mnrasl/slw140

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, stellar_physics
- Question: Are dipper stars' disks all viewed nearly edge-on, as assumed by the proposed dip mechanisms?  
  > "Most of the proposed mechanisms explaining the dips—i.e., occulting disk warps, vortices, and forming planetesimals—assume nearly edge-on viewing geometries." (abstract)
- Target **EPIC 204638512 (J1604-2130)**: coordinates 16:04:21.655 -21:30:28.50  
  > "| 204638512 | 16042165-2130284 | 16:04:21.655 | -21:30:28.50 | USc | K2 | 4900 | 0.7 | TD | 5.00 | 0.57 | A |" (Table 1); z/distance _not stated_; distance from _not stated_
- Target **EPIC 205151387**: coordinates 16:09:00.762 -19:08:52.70  
  > "| 205151387 | 16090075-1908526 | 16:09:00.762 | -19:08:52.70 | USc | M1 | 4000 | 0.8 | Full | 9.55 | 0.31 | Q |" (Table 1); z/distance _not stated_; distance from _not stated_
- Target **EPIC 203850058 (rho Oph 102)**: coordinates 16:27:06.596 -24:41:48.84  
  > "| 203850058 | 16270659-2441488 | 16:27:06.596 | -24:41:48.84 | Oph | M6 | 2700 | 3.0 | Full | 2.88 | 0.18 | Q |" (Table 1); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00526.S, 2012.1.00046.S
- bands: 880 um continuum (Cycle 0), 870 um continuum (Cycle 1)  
  > "EPIC 203850058 was imaged at high resolution in the 870 $\mu$m continuum during ALMA Cycle 1" (2.2 Resolved Sub-mm Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.67"x0.42" (EPIC 204638512), 0.64"x0.45" (EPIC 205151387), 0.28"x0.19" (EPIC 203850058)  
  > "giving a beam size of 0.28$^{\prime\prime}$$\times$0.19$^{\prime\prime}$ ($\sim$35$\times$25 AU)." (2.2 Resolved Sub-mm Data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO 3-2 (not stated)
- Other facility **K2 (MAST)**: K2SFF optical light curves of the dippers  
  > "we use the K2SFF light curves made publicly available by the Mikulski Archive for Space Telescopes (MAST)." (2.1 K2 Optical Light Curves)
- External data: Inclination of EPIC 204638512, 6±1.5 deg, from 12CO first-moment map  
  > "we adopt the disk inclination of $i=6$$^\circ$$\pm$1.5$^\circ$ derived by (cite: 2012ApJ...753...59M)" (3.1 Disk Inclinations) [from (cite: 2012ApJ...753...59M)]
- External data: Stellar properties (SpT, Teff, AV, disk type)  
  > "Stellar properties are from the literature (cite: 2002A&A...393..597N; 2014ApJ...787...42C; 2016ApJ...816...69A)." (Sample) [from (cite: 2002A&A...393..597N; 2014ApJ...787...42C; 2016ApJ...816...69A)]

## Processing

### Calibration

- pipeline or manual: For EPIC 203850058, raw data downloaded and pipeline calibration script run; others used archive images  
  > "we downloaded the raw visibilities and executed the pipeline calibration script" (2.2 Resolved Sub-mm Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust = +0.5 (EPIC 203850058)  
  > "interactively cleaning with a Briggs robust weighting parameter of $+0.5$" (2.2 Resolved Sub-mm Data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: interactive cleaning (EPIC 203850058)  
  > "extracted the continuum image by averaging over the continuum channels and interactively cleaning" (2.2 Resolved Sub-mm Data)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Dip depth, periodicity and rotation period measurement method  
  > "see Section 2.2 in (cite: 2016ApJ...816...69A)" (2.1 K2 Optical Light Curves) [from (cite: 2016ApJ...816...69A)]
- Use of K2SFF light curves  
  > "As in (cite: 2016ApJ...816...69A), we use the K2SFF light curves" (2.1 K2 Optical Light Curves) [from (cite: 2016ApJ...816...69A)]

### Not stated but needed to reproduce (our reading)

- Which ALMA calibrated products/images were used for EPIC 204638512 and 205151387 and their processing
- CASA version and pipeline version
- Image size, cell size, clean threshold for the images
- uvmodelfit initial guesses and region/fit settings for EPIC 205151387
- How inclination and its error were derived from aspect ratio r
- Distances adopted

## Analysis recipe

1. **Fit visibilities for EPIC 205151387 inclination**: uvmodelfit elliptical Gaussian to visibilities; inclination from aspect ratio assuming circular disk; checked against CO first-moment map  
  > "We assumed an elliptical Gaussian model, which has six free parameters" (3.1 Disk Inclinations)
   - software: CASA, uvmodelfit
   - assumption: circular disk structure, Keplerian rotation for moment-map check  
  > "then derived the inclination from $r$ assuming circular disk structure, finding $i=53$$^\circ$$\pm$2$^\circ$." (3.1 Disk Inclinations)
   - fitting: _not stated_
   - validation: First-moment 12CO map gives PA≈-30 deg, i≈50 deg  
  > "finding a similar position angle (${\rm PA}\approx-30$$^\circ$) and inclination ($i\approx50$$^\circ$) when assuming Keplerian rotation." (3.1 Disk Inclinations)
2. **Fit EPIC 203850058 inclination**: uvmodelfit elliptical Gaussian with initial PA≈20 deg, then imfit image-plane check  
  > "We therefore checked our results with the CASA routine `imfit`, which fits an elliptical Gaussian to the source in its image plane" (3.1 Disk Inclinations)
   - software: CASA, uvmodelfit, imfit
   - assumption: circular disk, Gaussian representation  
  > "we assume the observed disks of EPIC 205151387 and EPIC 203850058 are adequately represented by elliptical Gaussians" (3.1 Disk Inclinations)
   - fitting: _not stated_
   - validation: imfit compared with uvmodelfit  
  > "We therefore checked our results with the CASA routine `imfit`, which fits an elliptical Gaussian to the source in its image plane, then uses the clean beam to return de-convolved fit results" (Discussion, Disk Inclinations)

## Software

- **CASA** : uvmodelfit, imfit, pipeline calibration, cleaning  
  > "using standard routines from the *Common Astronomy Software Applications* (CASA) package" (3.1 Disk Inclinations)
- **KepPCA** : custom-aperture K2 light curve extraction  
  > "used the KepPCA pipeline to apply custom photometric apertures" (2.1 K2 Optical Light Curves)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| EPIC 205151387 inclination | 53 | 2 | deg | 1 | finding $i=53$$^\circ$$\pm$2$^\circ$ |
| EPIC 205151387 flux density | 49.5 | 0.4 | mJy | 1 | We found $F=49.5\pm0.4$ mJy and PA$=-22$$^\circ$$\pm$3$^\circ$ |
| EPIC 203850058 inclination (imfit) | 73 | 23 | deg | 2 | we found a nearly edge-on disk with $i=73$$^\circ$$\pm$23$^\circ$, $F=4.2\pm0.1$ mJy |
| EPIC 203850058 flux density (uvmodelfit) | 4.0 | 0.1 | mJy | 2 | We found $F=4.0\pm0.1$ mJy and PA$=15$$^\circ$$\pm$1$^\circ$ |

## Qualitative findings

- Dipper disks show a range of inclinations, including the face-on J1604-2130  
  > "reveals disks with a range of inclinations, most notably the face-on transition disk J1604-2130" (abstract)

## Claim tuples

- H: Dippers are viewed nearly edge-on | E: Inclinations of three dippers from resolved sub-mm data | R: i≈6, 53 and ~73-90 deg | F: Nearly edge-on geometry is not a defining characteristic of dippers | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Inclinations reflect bulk geometry; uncertainties exclude systematics; small sample  
  > "the uncertainties do not include systematic errors" (3.1 Disk Inclinations)
- Caveat (inferred, ours): Only three objects, so no statistical conclusion
- Caveat (inferred, ours): Gaussian fits to marginally resolved disks give poor inclination constraints
- Caveat (inferred, ours): Face-on case relies on literature SMA value

## Reproducibility

- Data public (paper): Archival ALMA data publicly available  
  > "Our sample consists of the three dippers with publicly available high-resolution sub-mm data" (Sample)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: fit starting values
- Missing: exact data selections
- Data volume (inferred): ~10-50 GB raw
- Score (inferred): 3/5, Public data and simple CASA fits, but few settings are given.
- Rediscovery candidate: yes, Public data, simple fits, numeric results.

## Links

- Companion: (cite: 2016ApJ...816...69A) (Original K2 dipper sample)
- Companion: (cite: 2012ApJ...753...59M) (SMA discovery and inclination of J1604-2130)
- Related: K2

## Checks

```json
{
 "quotes": 34,
 "quotes_ok": 34,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 25,
  "rate": 0.379
 },
 "evidence_ok": true
}
```
