# ALMA Resolves the Stellar Birth Explosion in Distant Quasar 3C298

`2018ApJ...866L...3B` | The Astrophysical Journal Letters 2018 | first author: Barthel, P. D. | arXiv: 1809.08432 | DOI: 10.3847/2041-8213/aae3e2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: Is the cool (~40 K) dust emission in the z=1.439 quasar 3C298 host a localized circumnuclear starburst, once synchrotron emission is subtracted?  
  > "We here present strong evidence for an extreme circumnuclear starburst in the z=1.439 quasar 3C298." (abstract)
- Target **3C298 (B1416+067)**: coordinates 14h19m08.1835s +06d28m34.819s (J2000), Gaia position of the optical QSO  
  > "using its Gaia position 14 [h] 19 [m] 08 [s] .1835, +06°28´34.819´´ (J2000)" (2. Observations and results); "using its Gaia position 14 [h] 19 [m] 08 [s] .1835, +06°28´34.819´´ (J2000)" (2. Observations and results); z/distance z=1.439; 8.6 kpc/arcsec  
  > "using its Gaia position 14 [h] 19 [m] 08 [s] .1835, +06°28´34.819´´ (J2000)" (2. Observations and results); "cosmology, which implies a scale of 8.6 kpc/arcsec" (1. Introduction, footnote 3); distance from cosmology of Bennett et al. 2014  
  > "using its Gaia position 14 [h] 19 [m] 08 [s] .1835, +06°28´34.819´´ (J2000)" (2. Observations and results); "We follow Bennett et al. (2014), using a H 0 = 69.6 km s -1 Mpc -1" (1. Introduction, footnote 3)

## Data provenance

- ALMA projects: 2015.1.00754.S
- bands: Band 7 (1 mm)  
  > "ALMA band 7 (1 mm) observations of 3C298 took place on August 15, 2016" (2. Observations and results)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: up to 1.6 km  
  > "with baselines of up to" (2. Observations and results)
- angular resolution: 0.18 x 0.16 arcsec, p.a. -5 deg  
  > "The resulting beam is 0.18 x 0.16 arcsec in p.a. -5º" (2. Observations and results)
- max recoverable scale: _not stated_
- sensitivity: 1σ = 37 µJy/beam  
  > "reaches a 1σ noise level of 37 μJy/beam" (2. Observations and results)
- time on source: 15 minutes  
  > "an on-source integration time of 15minutes" (2. Observations and results)
- observing dates: August 15, 2016  
  > "took place on August 15, 2016" (2. Observations and results)
- pi or archival as stated: _not stated_
- Other facility **VLA (archive, project BREUGL)**: 15 GHz (2 cm) A-array image used to subtract synchrotron  
  > "We started by analysing VLA Archive data (project BREUGL) at U-band (2cm, 15GHz) of 3C298, taken in October 1983." (2. Observations and results)
- Other facility **Gaia**: optical QSO position for image alignment  
  > "using its Gaia position 14 [h] 19 [m] 08 [s] .1835, +06°28´34.819´´ (J2000)" (2. Observations and results)
- External data: Herschel SED, cool dust temperature 37.9 K and SFR 940 Msun/yr  
  > "Podigachoski et al. (2015) find 37.9K, implying more thermal radiation at 1mm." (2. Observations and results) [from Podigachoski et al. 2015]
- External data: Earlier thermal 1mm estimate of 2.1 mJy from T=50K grey body  
  > "most likely larger than the 2.1mJy earlier estimated using a simple T = 50K grey body" (2. Observations and results) [from Haas et al. 2006]

## Processing

### Calibration

- pipeline or manual: Standard CASA pipeline at the ALMA European ARC node in Leiden  
  > "Standard CASA pipeline calibration was employed at the ALMA European Regional Centre Node in Leiden," (2. Observations and results)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 5% ALMA absolute flux density uncertainty  
  > "formally" (2. Observations and results)
- self calibration: phase-only and phase+amplitude self-calibration  
  > "including phase-only and" (2. Observations and results)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.025 arcsec pixels (re-gridded)  
  > "Both images, 1a and 1b, were re-gridded to" (2. Observations and results)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.18 x 0.16 arcsec, p.a. -5 deg  
  > "The resulting beam is 0.18 x 0.16 arcsec in p.a. -5º" (2. Observations and results)
- final rms: 37 µJy/beam  
  > "The ALMA image 1σ noise is 37 µJy/beam" (Figures 1a – 1b)

### Not stated but needed to reproduce (our reading)

- CASA version
- tclean parameters (weighting, robust, deconvolver, masks)
- self-calibration solution intervals
- flux and bandpass calibrators
- frequency setup and bandwidth
- VLA calibration and AIPS convolution details
- exact method for peak alignment shifts

## Analysis recipe

1. **Image ALMA and VLA to matched resolution**: CASA imaging with self-cal of ALMA; AIPS imaging of archival VLA 2 cm with final convolution to the ALMA beam; regrid to 0.025 arcsec pixels  
  > "Standard AIPS routines including a small final convolution were" (2. Observations and results)
   - software: CASA, AIPS
   - fitting: _not stated_
   - validation: Peak values coincide to within a pixel  
  > "Their peak values (core and hot spots) coincide to within a pixel" (2. Observations and results)
2. **Subtract scaled synchrotron (2 cm) from 1 mm image**: Align peaks to the Gaia QSO position, clip at 3σ, subtract the 2 cm image scaled with a range of spectral indices  
  > "we subtracted the 2cm image from the 1mm image using a range of spectral indices" (2. Observations and results)
   - parameter: alpha(2cm-1mm) = -0.9 (pure synchrotron) and -1.0  
  > "Choice of a synchrotron spectral index α 2cm [1mm] = -1.0 yields a more luminous" (2. Observations and results)
   - assumption: Free-free emission negligible; the central structure has a flatter spectral index than the lobes (-1.6/-1.5)  
  > "The central structure is expected to have a flatter spectral index." (2. Observations and results)
   - fitting: _not stated_
   - validation: Steeper indices than -1.0 leave residual at the QSO position, presumed non-thermal  
  > "Image subtraction with spectral indices steeper than -1.0 yields pronounced" (2. Observations and results)

## Software

- **CASA** : pipeline calibration, imaging, self-calibration  
  > "Standard CASA pipeline calibration was employed at the ALMA European Regional Centre Node in Leiden," (2. Observations and results)
- **AIPS** : VLA 2 cm imaging  
  > "Standard AIPS routines including a small final convolution were" (2. Observations and results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Central component flux density at 1 mm | 18.9 | 0.04 | mJy | 1 | central component of 18.9±0.04 mJy |
| Thermal residual flux, alpha=-0.9 | 0.70 | 0.07 | mJy | 2 | marginally resolved clump of strength 0.70 |
| Thermal flux, alpha=-1.0 | 3.1 | 0.06 | mJy | 2 | more luminous (3.1 |
| Extended plateau size | ~0.5 (~4.5 kpc) | not stated | arcsec | 2 | size |

## Qualitative findings

- Cool dust is in an asymmetric, kpc-sized circumnuclear structure, extended to the West and with a clump to the SE.  
  > "the ~40K dust in its host galaxy resides in an asymmetric" (abstract)

## Claim tuples

- H: Cool dust emission in 3C298 originates in a circumnuclear starburst | E: Subtract scaled VLA 2 cm image from ALMA 1 mm image at matched 0.18 arcsec resolution | R: Extended thermal residual of 0.7 to 3.1 mJy over ~4.5 kpc, ~16% of the core flux | F: Starburst origin, with a symbiotic relation to the radio source | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Precise morphology is undetermined; the thermal flux depends on the assumed spectral index.  
  > "although its precise morphology remains to be determined" (2. Observations and results)
- Caveat (inferred, ours): Thermal residual depends strongly on the assumed synchrotron spectral index
- Caveat (inferred, ours): VLA data from 1983 vs ALMA 2016: variability of the compact core is ignored
- Caveat (inferred, ours): No uncertainty from spectral index gradients
- Caveat (inferred, ours): Single-band ALMA, with no spectral information

## Reproducibility

- Data public (paper): ALMA project cited, VLA archive data used  
  > "This paper makes use of the following ALMA data:" (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA imaging parameters
- Missing: VLA calibration details
- Missing: alignment shifts
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and a simple recipe, but imaging and subtraction details are missing.
- Rediscovery candidate: no, Key imaging and subtraction parameters are not given, so results are sensitive to unstated choices.

## Links

- Companion: Podigachoski et al. 2015 (Herschel SED, dust temperature and SFR)

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 59,
  "stated": 31,
  "rate": 0.525
 },
 "evidence_ok": true
}
```
