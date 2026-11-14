# JWST/NIRCam Imaging of the Bipolar Planetary Nebula NGC 6537: The (Infra)red Spider, Revealed

`2025ApJ...993...79K` | The Astrophysical Journal 2025 | first author: Kastner, Joel H. | arXiv: 2509.11042 | DOI: 10.3847/1538-4357/ae0706

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: evolved_stars
- Question: What is the structure and mass-loss history of the bipolar PN NGC 6537, and is there evidence for a binary central star, from JWST/NIRCam, ALMA, HST and Chandra imaging?  
  > "The resulting multiwavelength view of the Red Spider establishes the detailed lobe/torus structure of the nebula and the mass-loss history of its progenitor star." (abstract)
- Target **NGC 6537 (Red Spider Nebula)**: coordinates _not stated_; z/distance D = 1.8 ± 0.5 kpc  
  > "in this paper, we adopt the estimate $D=1.8\pm0.5$ kpc (cite: Frew2016)." (1 Introduction); distance from Frew et al. 2016 (cite: Frew2016)  
  > "in this paper, we adopt the estimate $D=1.8\pm0.5$ kpc (cite: Frew2016)." (1 Introduction)

## Data provenance

- ALMA projects: 2018.1.00424.S
- bands: Band 3 (3 mm)  
  > "The ALMA data were obtained in the 3 mm region (ALMA Band 3) as part of a molecular line survey of high-mass star-forming regions (cite: Gieser2023)" (2.3 Archival HST and ALMA data)
- frequencies and spectral setup: 98.3 GHz continuum; 13CO(1-0) cube with 0.664 km/s velocity resolution  
  > "The $^{13}$CO emission-line map was obtained with velocity resolution of 0.664 km s$^{-1}$" (2.3 Archival HST and ALMA data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1 arcsec  
  > "obtained at spatial resolution of $\sim$1$''$ (cite: Gieser2023)" (2.3 Archival HST and ALMA data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival data from a high-mass star-forming region survey (Gieser et al. 2023); subject of forthcoming Moraga Baez et al. paper  
  > "are the subject of a forthcoming paper (Moraga Baez et al. 2025b, in preparation)" (2.3 Archival HST and ALMA data)
- Line: 13CO J=1-0 (110.20135 GHz)
- Other facility **JWST/NIRCam**: F164N, F212N, F356W, F405N images  
  > "Images were obtained with NIRCam through filters F164N, F212N, F356W, and F405N" (2.1 JWST)
- Other facility **Chandra HRC-I**: 76.13 ks X-ray imaging, nondetection  
  > "The total Chandra/HRC-I exposure time was 76.13 ks." (2.2 Chandra X-ray Observatory)
- Other facility **HST/WFPC2**: Archival 1998 optical images  
  > "the HST data, obtained in 1998 with WFPC2 (PID: 6502; PI: B. Balick)" (2.3 Archival HST and ALMA data)
- External data: Polar lobe deprojected speeds ~300-400 km/s and inclination 30-40 deg  
  > "revealed (deprojected) expansion speeds of $\sim$300–400 km s$^{-1}$ along the nebula’s polar axis" (1 Introduction) [from Corradi & Schwarz 1993 (cite: CorradiSchwarz1993)]
- External data: Extinction A_V=3.7 and central star HST photometry  
  > "corresponding to the extinction toward the central star and nebular core region, $A_V=3.7$ (cite: Matsuura2005N6537)" (3.3.3) [from Matsuura et al. 2005 (cite: Matsuura2005N6537)]
- External data: Central star luminosity 8500 Lsun  
  > "assuming a stellar luminosity of 8500 $L_\odot$ (cite: Casassus2000)" (4.3) [from Casassus et al. 2000 (cite: Casassus2000)]
- Simulation/model as data: 2D hydrodynamic simulation from Balick et al. 2019 compared to NE lobe image  
  > "is selected as representative of a “family” of simulations included in (cite: Balick2019) that appears to match the overall radial and azimuthal appearance of the polar lobes of NGC 6537." (4.2 Hydrodynamic modeling)

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

- ALMA data reduction and imaging (maps at ~1 arcsec) from the survey paper  
  > "Here, we utilize maps of 98.3 GHz continuum emission and the $J=1\rightarrow 0$ (110.20135 GHz) rotational transition of $^{13}$CO, obtained at spatial resolution of $\sim$1$''$ (cite: Gieser2023)." (2.3 Archival HST and ALMA data) [from Gieser et al. 2023 (cite: Gieser2023)]
- Hydrodynamic simulation details  
  > "The reader is directed to those papers for details of the simulations." (4.2 Hydrodynamic modeling) [from Balick et al. 2019, 2020 (cite: Balick2019; Balick2020)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, CASA version, imaging parameters (robust, beam, rms) not given
- Velocity ranges for moment-0 maps and how the torus radius of ~9 arcsec was measured
- Systemic velocity handling and moment clipping thresholds
- Continuum and line synthesized beam and sensitivity

## Analysis recipe

1. **Make 13CO moment maps**: Velocity-integrated (moment 0) images over various velocity ranges and intensity-weighted mean velocity (moment 1) image from the cube  
  > "we have extracted velocity-integrated (“moment 0”) images over various velocity ranges of interest as well as an intensity-weighted mean velocity (“moment 1”) image." (2.3 Archival HST and ALMA data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive torus size, velocity and age**: Projected radius ~9 arcsec read from map; deprojected using the lobe-axis inclination; age = radius/velocity  
  > "we deduce a projected angular radius of $\sim$9$''$ for the outer edge of the molecular torus, leading to a deprojected linear radius of $\sim$0.13 pc assuming $D=1.8$ kpc." (3.3.2 The molecular torus)
   - assumption: Torus axis inclination equals polar axis inclination (38 deg to plane of sky); D = 1.8 kpc  
  > "if we assume the inclination of the molecular torus axis of symmetry with respect to the plane of the sky is identical that of NGC 6537’s polar axis" (3.3.2 The molecular torus)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **webPIMMS** : Convert Chandra count-rate limits to flux limits (APEC model)  
  > "we used the webPIMMS[^2] spectral modeling tool. We adopt the APEC thermal plasma model" (3.3.3)
- **JWST Science Calibration Pipeline** 1.14.0 and 1.15.1: NIRCam calibration and mosaics  
  > "Version 1.14.0 of the JWST Science Calibration Pipeline was used to generate fully calibrated exposures and final mosaiced images" (2.1 JWST)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 13CO projected expansion velocity | ~10 | not stated | km/s | 2 | characterized by a projected expansion velocity of $V_{exp} \sim 10$ km s$^{-1}$ |
| Deprojected torus expansion velocity | ~13 | not stated | km/s | 2 | the deprojected expansion velocity of the torus we obtain from the $^{13}$CO(1–0) data is $\sim$13 km s$^{-1}$ |
| Deprojected torus radius | ~0.13 | not stated | pc | 2 | leading to a deprojected linear radius of $\sim$0.13 pc assuming $D=1.8$ kpc |
| Torus dynamical age | ~10000 | not stated | yr | 2 | The implied torus dynamical age — or, more accurately, the time since onset of copious equatorial mass loss — is then $\sim$10000 yr. |
| Diffuse X-ray luminosity upper limit | 1.5e31 | not stated | erg/s | 0 | $L_{X,d} \lesssim 1.5\times10^{31}$ erg s$^{-1}$ |

## Qualitative findings

- 13CO traces a point-symmetric equatorial torus whose symmetry axis (PA~155 deg) is rotated ~20 deg from the expected equatorial plane  
  > "the projected orientation of peak $^{13}$CO emission (PA $\sim$155$^\circ$) is evidently rotated by $\sim$20$^\circ$" (3.3.2 The molecular torus)

## Claim tuples

- H: Is the molecular gas a slowly expanding equatorial torus older than the polar lobes? | E: ALMA 13CO(1-0) moment maps compared with JWST imaging | R: Torus ~10 km/s, 0.13 pc, ~10000 yr vs lobes ~3700 yr | F: Slow equatorial mass loss preceded fast polar outflows | **supported**
- H: Does the central star host hot circumstellar dust? | E: Aperture photometry on HST and JWST images, blackbody fit | R: IR excess matched by ~1000 K blackbody | F: Likely circumbinary dust disk implying a binary | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): X-ray limits depend on assumed plasma temperatures  
  > "the limits on both $L_{X,d}$ and $L_{X,p}$ derived here are dependent on the aforementioned choices of parameters" (3.3.3)
- Caveat (inferred, ours): ALMA data analysis is qualitative, with no uncertainties on torus radius or velocity
- Caveat (inferred, ours): Distance uncertainty (±0.5 kpc) propagates to ages but is not quantified
- Caveat (inferred, ours): Inclination of torus assumed equal to lobes despite the observed misalignment

## Reproducibility

- Data public (paper): ALMA data cited by project code; archival  
  > "This paper makes use of ALMA data ADS/JAO.ALMA#2018.1.00424.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: ALMA imaging recipe and moment-map parameters
- Missing: Exact measurement of torus radius
- Data volume (inferred): ~10-50 GB for the ALMA Band 3 data
- Score (inferred): 3/5, ALMA role is minor and processing is not described; JWST data are public but the ALMA analysis is qualitative.
- Rediscovery candidate: no, ALMA processing is unspecified and results are mostly rough estimates.

## Links

- Method: Gieser et al. 2023 (cite: Gieser2023) (Source of the ALMA survey data and processing)
- Companion: Moraga Baez et al. 2025 (cite: MoragaBaez2025) (Forthcoming ALMA study of NGC 6537/NGC 6302 molecular tori)
- Related: JWST PID 4571
- Related: Chandra ChanPlaNS

## Checks

```json
{
 "quotes": 34,
 "quotes_ok": 34,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 63,
  "stated": 24,
  "rate": 0.381
 },
 "evidence_ok": true
}
```
