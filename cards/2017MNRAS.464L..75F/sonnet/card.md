# ALMA observations of the supergiant B[e] star Wd1-9

`2017MNRAS.464L..75F` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Fenech, D. M. | arXiv: 1609.03469 | DOI: 10.1093/mnrasl/slw183

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: stellar_physics, star_formation
- Question: What are the millimetre continuum and recombination-line properties of the supergiant B[e] star Wd1-9, what do they imply for its mass loss, and does it resemble MWC349A or eta Carinae?  
  > "In order to place observational constraints on these disparate processes we obtained millimetre continuum observations of the massive Galactic starburst cluster Westerlund 1" (Introduction); "this immediately raises the question of which source (if either) does Wd1-9 resemble." (Discussion)
- Target **Wd1-9 (Westerlund 1 #9)**: coordinates RA 16h47m4.162s, Dec -45d50m31.373s  
  > "(R.A. 16$^{{h}}$47$^{m}$4.162$^{s}$ Dec. -45$^{o}$50$'$31.373$''$ )" (Introduction); "At an assumed distance of 5 kpc to Wd1-9" (Wd1-9 morphology); z/distance 5 kpc (assumed)  
  > "(R.A. 16$^{{h}}$47$^{m}$4.162$^{s}$ Dec. -45$^{o}$50$'$31.373$''$ )" (Introduction); "At an assumed distance of 5 kpc to Wd1-9" (Wd1-9 morphology); distance from adopted; not derived in this paper  
  > "(R.A. 16$^{{h}}$47$^{m}$4.162$^{s}$ Dec. -45$^{o}$50$'$31.373$''$ )" (Introduction); "At an assumed distance of 5 kpc to Wd1-9" (Wd1-9 morphology)

## Data provenance

- ALMA projects: 2013.1.00897.S
- bands: _not stated_
- frequencies and spectral setup: central frequency 100 GHz, four spectral windows, 128 channels each of 15.625 kHz  
  > "Each window contains 128 channels with a frequency width of 15.625 kHz." (2 Observations and image processing)
- continuum bandwidth: 7.5 GHz total  
  > "a total bandwidth of 7.5 GHz over four spectral windows" (2 Observations and image processing)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 40 to 1500 m, 42 antennas  
  > "The array utilised 42 antennas with baselines ranging from 40 to 1500 m" (2 Observations and image processing)
- angular resolution: natural 0.58x0.46 arcsec; Briggs R0 0.51x0.40 arcsec  
  > "natural weighting (beam size: 0.58$\times$ 0.46$''$) and Briggs Robust-0 (R0, beam size: 0.51$\,\times$ 0.40$''$) weighting" (2 Observations and image processing)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 242.3 s per pointing  
  > "a total on-source integration time per pointing of 242.3 secs" (2 Observations and image processing)
- observing dates: 30 June - 1 July 2015  
  > "Observations of Westerlund 1 were performed with ALMA on 30th June - 1st July 2015" (2 Observations and image processing)
- pi or archival as stated: _not stated_
- Line: H41alpha RRL H41alpha (detected at 92.060 GHz)
- Other facility **ATCA**: 8.6 GHz radio observations from literature, used for comparison and extrapolation  
  > "Previous ATCA observations of Westerlund 1 at 8.6 GHz published by (cite: dough10) also showed both compact and extended emission components of Wd1-9." (3.1 Continuum emission)
- External data: ATCA 8.6 GHz radio spectral index +0.68±0.07 and flux density, used to extrapolate to 100 GHz  
  > "They determined a spectral index for the compact source of +0.68$\pm$0.07." (3.1 Continuum emission) [from (cite: dough10)]
- External data: MWC349A flux and v_inf ~50 km/s used to derive its mass-loss rate  
  > "utilising the fluxes and $v_{\infty}$ $\sim$ 50 km s$^{-1}$ from (cite: tafoya04)" (Discussion) [from (cite: tafoya04)]
- External data: system inclination ~50 deg  
  > "which (cite: clark13b) calculate to be $\sim$50$\mathrm{^{o}}$" (3.1 Continuum emission) [from (cite: clark13b)]

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline procedures in CASA  
  > "The data were calibrated using the standard ALMA pipeline procedures in Common Astronomy Software Applications (CASA)" (2 Observations and image processing)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan and Pallas, 228.96 and 82.01 mJy at 91.495 GHz; J1617-5848 for phase and bandpass  
  > "observations of Titan and Pallas were used to amplitude calibrate the data assuming flux densities of 228.96 and 82.01 mJy respectively at 91.495 GHz" (2 Observations and image processing)
- flux scale uncertainty: _not stated_
- self calibration: self-calibration on bright (~150 mJy) compact Wd1-9 emission  
  > "Self-calibration was then carried out using the bright ($\sim$150 mJy) compact source emission from Wd1-9." (2 Observations and image processing)

### Imaging

- task: CLEAN in CASA, Cotton-Schwab  
  > "Imaging of both the continuum and line emission was performed using the CLEAN algorithm in CASA." (2 Observations and image processing)
- deconvolver: _not stated_
- weighting robust: natural and Briggs robust 0  
  > "both natural weighting (beam size: 0.58$\times$ 0.46$''$) and Briggs Robust-0" (2 Observations and image processing)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: line imaging after continuum subtraction; extended emission imaged after subtracting compact source from visibilities  
  > "images of the extended emission were made following subtraction of the strong compact source emission from the visibility data" (2 Observations and image processing)
- line free channels: continuum images exclude line channels (channels not listed)  
  > "images of the continuum emission were produced excluding the channels containing the line emission" (2 Observations and image processing)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: cube velocity resolution 50.90 km/s, LSR frame, natural weighting  
  > "An image cube was also produced in the local standard of rest (LSR) frame using the continuum-subtracted data with natural weighting and a velocity resolution of 50.90 km s$^{-1}$ ." (2 Observations and image processing)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- MFS spectral index and error maps from frequency-dependent modelling during deconvolution  
  > "All spectral indices and errors presented are taken directly from the spectral index and error images shown in Fig. [1](#wd19) (cite: rau11)." (2 Observations and image processing) [from (cite: rau11)]
- centroid position errors: Gaussian-fit error plus formal position error  
  > "the formal position error as outlined in (cite: weintroub08)" (3.2 H41alpha RRL emission) [from (cite: weintroub08)]
- mass-loss rate uses emission model and stellar parameters from Dougherty et al., spherical geometry  
  > "in conjunction with both the continuum mm and radio flux densities and the emission model from (cite: dough10), we calculate a current mass-loss rate" (Discussion) [from (cite: dough10)]

### Not stated but needed to reproduce (our reading)

- Robust weighting details beyond R0, nterms for MFS
- Channel ranges of the line and line-free continuum
- Image size, cell size, clean threshold and masks
- CASA version
- Gaussian fit regions and procedure for compact source subtraction
- Which spectral window held the line (identified only by frequency range)
- Stellar parameters and formulae for the mass-loss rate calculation
- Flux scale uncertainty
- Rms noise of images

## Analysis recipe

1. **calibrate and self-calibrate**: standard ALMA pipeline in CASA, then self-calibration on the compact source  
  > "Self-calibration was then carried out using the bright ($\sim$150 mJy) compact source emission from Wd1-9." (2 Observations and image processing)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **image continuum and spectral index**: CLEAN with natural and R0 weighting, MFS for spectral index and error maps; compact source subtracted to image extended emission  
  > "Imaging was also performed using the multi-frequency synthesis (MFS) capability for both of these weighting schemes to produce spectral index and associated error maps." (2 Observations and image processing)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **measure compact source size and flux**: 2-D Gaussian fit to compact component in R0 image  
  > "A 2-D gaussian fit to the compact source component gives a deconvolved size of 158.3$\pm$1.0 $\times$ 121.9$\pm$1.4 mas" (3.1 Continuum emission)
   - software: CASA
   - fitting: _not stated_
   - validation: compared with extrapolation from ATCA radio flux  
  > "predicts a 100 GHz flux density of $132.1^{+24.7}_{-20.8}$ mJy consistent with the 153 mJy observed" (3.1 Continuum emission)
4. **analyse H41alpha line profile and spectro-astrometry**: Gaussian fit to line profile; 2-D Gaussian fit to peak position in each channel of the cube  
  > "The positions were determined using a 2-D gaussian fit" (3.2 H41alpha RRL emission)
   - software: CASA
   - fitting: Gaussian profile fit  
  > "a gaussian-fitted FWHM of 163$\pm$5 km s$^{-1}$" (3.2 H41alpha RRL emission)
   - validation: peak velocity compared with cluster velocity  
  > "is consistent with the cluster velocity for Westerlund 1" (3.2 H41alpha RRL emission)
5. **derive mass-loss rate**: outflow velocity ~100 km/s from line width, with mm and radio fluxes and the Dougherty et al. emission model  
  > "we calculate a current mass-loss rate of Ṁ$\sim$ 6.4${\times}10^{-5}(d/5kpc)^ {1.5}$" (Discussion)
   - assumption: spherical geometry, distance 5 kpc, stellar parameters from Dougherty et al. 2010  
  > "Stellar parameters are those taken from (cite: dough10) and spherical geometry is assumed." (footnote 3)
   - fitting: _not stated_
   - validation: compared with MWC349A and eta Carinae  
  > "the wind parameters for Wd1-9 are broadly comparable to those of MWC349A" (Discussion)

## Software

- **CASA** : calibration, CLEAN imaging, MFS spectral index maps, cube production  
  > "Imaging of both the continuum and line emission was performed using the CLEAN algorithm in CASA." (2 Observations and image processing)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| compact source integrated flux density at ~100 GHz | 153 | ±8 | mJy | 3 | with an integrated flux density of 153$\pm$8 mJy |
| compact source deconvolved size | 158.3 x 121.9 | ±1.0 x ±1.4 | mas | 3 | deconvolved size of 158.3$\pm$1.0 $\times$ 121.9$\pm$1.4 mas |
| compact source position angle | 0.7 | ±1.2 | deg | 3 | a position angle (P.A.) of 0.7$\pm$1.2 |
| spectral index at compact source peak | 0.000 | ±0.015 | dimensionless | 2 | a value of 0.000$\pm$0.015 at the peak of the compact emission |
| H41alpha FWHM | 163 | ±5 | km/s | 4 | gaussian-fitted FWHM of 163$\pm$5 km s$^{-1}$ |
| H41alpha peak velocity | -59 | ±2 | km/s | 4 | The peak velocity -59$\pm$2 km s$^{-1}$ |
| mass-loss rate | 6.4e-5 (d/5kpc)^1.5 | not stated | Msun/yr | 5 | we calculate a current mass-loss rate of Ṁ$\sim$ 6.4${\times}10^{-5}(d/5kpc)^ {1.5}$ |

## Qualitative findings

- Extended N-S nebula about 1.4 arcsec north and 1.9 arcsec south, ~0.08 pc total, thermal optically thin emission  
  > "extending $\sim$1.4 arcsec to the north and $\sim$1.9 arcsec to the south" (3.1 Continuum emission)

## Claim tuples

- H: Is Wd1-9 an extreme mm stellar source with a dense slow wind? | E: ALMA 3 mm continuum and H41alpha imaging | R: 153 mJy compact source, H41alpha FWHM 163 km/s, mass-loss rate ~6.4e-5 Msun/yr at 5 kpc | F: Wd1-9 has a low velocity ionised wind with extreme mass-loss rate | **supported**
- H: Does Wd1-9 resemble MWC349A? | E: Compare mm flux, line, nebula morphology and spectro-astrometry | R: Comparable wind parameters and similar extended nebula; centroid gradient ~200 km/s perpendicular to nebula | F: Wd1-9 and MWC349A are similar interacting binaries undergoing case-A mass transfer | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Eta Carinae-like shell ejection disfavoured since its mass-loss is over two orders of magnitude greater  
  > "over two orders of magnitude greater than we infer for Wd1-9" (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Bipolar outflow versus rotating disc origin of H41alpha cannot be distinguished; filaments need more sensitive follow-up  
  > "we caution that further observations will be required to unambiguously distinguish between both options." (Discussion)
- Caveat (inferred, ours): Mass-loss rate depends on assumed outflow geometry, distance and clumping; no uncertainty given
- Caveat (inferred, ours): Interpretation of the line as a disc wind is by analogy only
- Caveat (inferred, ours): Single short snapshot; filaments at 2-3 sigma
- Caveat (inferred, ours): Case-A mass transfer conclusion is speculative

## Reproducibility

- Data public (paper): project code given and ALMA data acknowledged; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00897.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Line and continuum channel selections
- Missing: Mass-loss rate calculation details and stellar parameters
- Data volume (inferred): ~10-50 GB for the full MS; small for the single pointing
- Score (inferred): 3/5, Data are identified and the basic steps described, but key imaging parameters and the mass-loss calculation are unspecified.
- Rediscovery candidate: no, The recipe lacks parameters and the mass-loss result depends on an external model.

## Links

- Method: (cite: rau11) (MFS spectral index imaging)
- Method: (cite: dough10) (emission model and radio data for mass-loss rate)
- Companion: (cite: clark13b) (multi-wavelength synthesis of Wd1-9)
- Companion: Fenech et al. in prep. (full Westerlund 1 ALMA study)
- Related: ALMA Westerlund 1 27-pointing survey

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
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
  "facts": 70,
  "stated": 40,
  "rate": 0.571
 },
 "evidence_ok": true
}
```
