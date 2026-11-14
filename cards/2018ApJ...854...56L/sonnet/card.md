# ALMA Dust Polarization Observations of Two Young Edge-on Protostellar Disks

`2018ApJ...854...56L` | The Astrophysical Journal 2018 | first author: Lee, Chin-Fei | arXiv: 1801.03802 | DOI: 10.3847/1538-4357/aaa769

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: Is poloidal magnetic field (versus scattering or radiation-flux alignment) responsible for dust polarization in two young edge-on protostellar disks, HH 212 and HH 111 VLA 1?  
  > "Specifically, we seek to determine whether some of the core magnetic flux is dragged into the disk or not." (1 Introduction)
- Target **HH 212 disk**: coordinates _not stated_; z/distance ~400 pc  
  > "These criteria are satisfied by two bright nearby disks in Orion at a distance of $\sim$ 400 pc, one in HH 212 (Class 0) and one in HH 111 (early Class I)." (1 Introduction); distance from _not stated_
- Target **HH 111 VLA 1 and VLA 2**: coordinates _not stated_; z/distance ~400 pc  
  > "These criteria are satisfied by two bright nearby disks in Orion at a distance of $\sim$ 400 pc, one in HH 212 (Class 0) and one in HH 111 (early Class I)." (1 Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00037.S
- bands: Band 7 (~343 GHz), Cycle 3  
  > "carried out together with ALMA in Band 7 at $\sim$ 343 GHz in Cycle 3" (2 Observations)
- frequencies and spectral setup: 4 continuum windows at 336.5, 338.5, 348.5, 350.5 GHz  
  > "4 continuum windows (with one at 336.5 GHz, one at 338.5 GHz, one at 348.5 GHz, and one at 350.5 GHz)" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C36-6, 38-40 antennas  
  > "with 38-40 antennas in the Configuration C36-6" (2 Observations)
- baselines: 14-2483 m  
  > "The projected baselines are 14-2483 m." (2 Observations)
- angular resolution: ~0.12 arcsec  
  > "This generates a synthesized beam (resolution) of $\sim$ $0^{\prime\prime}_{^\textrm{.}}12$." (2 Observations)
- max recoverable scale: ~1.4 arcsec  
  > "The maximum recoverable size (MRS) scale is $\sim$ $1^{\prime\prime}_{^\textrm{.}}4$" (2 Observations)
- sensitivity: _not stated_
- time on source: ~40 minutes on each HH system  
  > "The total time is $\sim$ 40 minutes on each HH system." (2 Observations)
- observing dates: 2016 Aug 30 and Sep 3  
  > "Two executions were carried out in 2016, one on August 30 and the other on September 3." (2 Observations)
- pi or archival as stated: _not stated_
- External data: HH 212 disk properties (inclination ~86 deg, flared) from 350 GHz ~0.02 arcsec ALMA data  
  > "the disk is nearly edge-on, with an inclination of $\sim$ 86$^\circ$ and the nearside tilted slightly to the south." (3.1 HH 212) [from (cite: Lee2017disk)]
- External data: HH 111 disk inclination ~80 deg and Keplerian rotation from C18O  
  > "with a smaller inclination angle of $\sim$ 80$^\circ$ and the near side tilted to the east (cite: Lee2016)" (3.2 HH 111) [from (cite: Lee2016)]

## Processing

### Calibration

- pipeline or manual: CASA calibration; bandpass J5010+1800, gain J0552+0313, polarization J0522-3627  
  > "with quasars J5010+1800, J0552+0313 (0.31 Jy), and J0522-3627 (3.04 Jy) as bandpass, gain, and polarization calibrators, respectively." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: super-uniform weighting, robust 0.5  
  > "A super-uniform weighting with a robust factor of 0.5 was used for the $uv$ data" (2 Observations)
- uv taper: uv distances <50 m excluded  
  > "the $uv$ data with a distance $<$ 50 m are not well sampled and thus excluded in our map generation." (2 Observations)
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
- final rms: Stokes I 0.44 (HH 212), 0.34 (HH 111) mJy/beam; Q,U ~0.03 mJy/beam  
  > "the noise level is $\sim$ 0.44 mJy beam$^{-1}$ in HH 212 and $\sim$ 0.34 mJy beam$^{-1}$ in HH 111." (2 Observations)

### Inherited from earlier work

- Flared disk model and radiative transfer code for dust continuum  
  > "We used our radiative transfer code (cite: Lee2017disk) to obtain dust continuum emission map from the model disk." (4 A Disk Model for HH 111) [from (cite: Lee2017disk)]
- beta ~0.6 adopted as found in HH 212 disk  
  > "we assume $\beta \sim$ 0.6, as that found in the disk of HH 212 (cite: Lee2008)" (4 A Disk Model for HH 111) [from (cite: Lee2008)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Polarization calibration procedure and leakage handling
- Whether self-calibration was applied
- Image size and cell size, deconvolver and masking
- Polarization debiasing and threshold for plotting vectors
- Model fit details (eye-fitting criteria)
- Source coordinates

## Analysis recipe

1. **Make Stokes I, Q, U continuum maps and polarization**: Super-uniform weighting, robust 0.5, uv>50 m; P = sqrt(Q^2+U^2)/I; E-vector orientations  
  > "(Linear) Polarization fraction (degree) is defined as $P=\sqrt{Q^2+U^2}/I$." (2 Observations)
   - software: CASA
   - parameter: robust 0.5, beam ~0.12 arcsec  
  > "A super-uniform weighting with a robust factor of 0.5 was used" (2 Observations)
   - fitting: _not stated_
   - validation: Instrumental P error <=0.2% (0.3% for VLA 2) per ALMA Technical Handbook  
  > "the instrumental error on $P$ is expected to be $\lesssim$ 0.2% for the disks of HH 212 and HH 111 VLA 1 at the phase center" (2 Observations)
2. **Model HH 111 VLA 1 disk continuum**: Parametrized flared disk with radiative transfer, convolved with beam, eye-fit to the map  
  > "We also assume $p= 1$ and use an eye-fitting for the rough determination of the disk properties." (4 A Disk Model for HH 111)
   - parameter: q=0.5, p=1, inclination 80 deg  
  > "we assume $q=0.5$, as that found for the disk in the later stage (cite: Andrews2009)" (4 A Disk Model for HH 111)
   - assumption: kappa = 0.1 (nu/1e12 Hz)^beta cm2/g, beta~0.6; Keplerian rotation; vertical hydrostatic equilibrium  
  > "Thus, the dust opacity is $\kappa_\nu\sim 0.053$ cm$^2$ g$^{-1}$ at 343 GHz." (4 A Disk Model for HH 111)
   - fitting: Eye-fitting, 20% assumed uncertainties  
  > "Note that the best-fit parameters are assumed to have 20% uncertainties." (4 A Disk Model for HH 111)
   - validation: Residual map reasonably small  
  > "The residual is reasonably small, indicating that the disk model is acceptable." (4 A Disk Model for HH 111)

## Software

- **CASA** : uv data calibration and imaging  
  > "The $uv$ data were calibrated with the Common Astronomy Software Applications (CASA) package" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HH 212 total flux density at 343 GHz | ~150 | 25 | mJy | 1 | The total flux density is $\sim$ 150$\pm$25 mJy. |
| HH 111 VLA 1 total flux density | ~535 | 80 | mJy | 1 | It has a total flux density of $\sim$ 535$\pm$80 mJy. |
| HH 111 VLA 2 total flux density | ~18.2 | 3.6 | mJy | 1 | It has a total flux density of $\sim$ 18.2$\pm$3.6 mJy. |
| HH 111 VLA 1 disk outer radius Ro | 0.55 arcsec (220 AU) | 0.11 arcsec (44 AU) | arcsec | 2 | $R_\mathrm{o}\sim$ $0^{\prime\prime}_{^\textrm{.}}55$$\pm$$0^{\prime\prime}_{^\textrm{.}}11$ (220$\pm$44 AU) |
| HH 111 disk temperature at Rt | 87 | 17 | K | 2 | $T_\mathrm{t}\sim$ 87$\pm$17 K |
| HH 111 VLA 1 disk mass | ~0.04 | not stated | Msun | 2 | \sim 0.04 \,M_\odot |
| Polarization fraction | ~1% | not stated | percent | 1 | Polarization fraction is $\sim$ 1%. |

## Qualitative findings

- HH 212 polarization is perpendicular to disk major axis with near-side asymmetry; HH 111 VLA 1 shows perpendicular pattern in nearside and along-major-axis in farside.  
  > "The polarization orientations are almost perpendicular to the disk major axis in the nearside, but more along the major axis in the farside" (abstract)

## Claim tuples

- H: Resolved young edge-on disks show polarization from poloidal magnetic fields | E: 343 GHz ALMA polarization imaging of HH 212 and HH 111 | R: ~1% polarization, perpendicular to major axis in HH 212; two patterns in HH 111 VLA 1 | F: HH 212 consistent with scattering or poloidal-field-aligned grains; cannot be distinguished | **partially**
- H: Polarization in HH 111 VLA 1 traces magnetic field | E: Compare pattern with disk model and mechanisms | R: Toroidal-like in nearside, poloidal-like or elliptical in farside | F: Toroidal plus poloidal field may explain it, but scattering or radiation-flux alignment are possible | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Radiation-flux alignment unlikely for HH 212 since orientations are perpendicular, not parallel, to major axis  
  > "The observed dust polarization is unlikely be due to the alignment of dust grains by the radiation flux" (6.1 HH 212)
- How they decided it was enough: _not stated_
- Limitation (authors): Disk model is illustrative only, from single frequency  
  > "Thus, the model here is really for illustrative purposes only." (4 A Disk Model for HH 111)
- Caveat (inferred, ours): Single-frequency data cannot separate polarization mechanisms
- Caveat (inferred, ours): Eye-fit model without formal uncertainties
- Caveat (inferred, ours): No scattering modeling performed

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Polarization calibration details
- Missing: Model code not released
- Missing: Imaging parameters
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 3/5, Public data and basic imaging parameters given, but polarization calibration and model details are missing.
- Rediscovery candidate: no, Polarization calibration and imaging details are incomplete, and the model is an eye-fit using unreleased code.

## Links

- Method: (cite: Lee2017disk) (Disk model and radiative transfer code)
- Companion: (cite: Lee2016) (HH 111 kinematics)

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 63,
  "stated": 31,
  "rate": 0.492
 },
 "evidence_ok": true
}
```
