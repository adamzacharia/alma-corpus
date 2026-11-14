# ALMA reveals the feeding of the Seyfert 1 nucleus in NGC 1566

`2014A&A...565A..97C` | Astronomy and Astrophysics 2014 | first author: Combes, F. | arXiv: 1401.4120 | DOI: 10.1051/0004-6361/201423433

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: How is the Seyfert 1 nucleus of NGC 1566 fueled, and is there molecular outflow feedback, as probed by CO(3-2) at ~25 pc resolution and gravity torques?  
  > "make NGC 1566 an ideal target to test and refine scenarios of AGN feeding and feedback" (1 Introduction)
- Target **NGC 1566**: coordinates RA 04h20m00.42s, Dec -54d56m16.1s (J2000, phase center)  
  > "In the present work, we adopt the median value given by NED, i.e. D=10 Mpc, for which 1$''$ = 48 pc." (1.1 NGC 1566); "04$^h$20$^m$00.42$^s$" (Table 1); z/distance 10 Mpc (V_hel 1504 km/s)  
  > "In the present work, we adopt the median value given by NED, i.e. D=10 Mpc, for which 1$''$ = 48 pc." (1.1 NGC 1566); "04$^h$20$^m$00.42$^s$" (Table 1); distance from median value given by NED  
  > "In the present work, we adopt the median value given by NED, i.e. D=10 Mpc, for which 1$''$ = 48 pc." (1.1 NGC 1566); "04$^h$20$^m$00.42$^s$" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00208.S
- bands: Band 7  
  > "NGC 1566 was observed with Band 7 simultaneously in CO(3-2), HCO$^+$(4-3), HCN(4-3), and continuum." (2 Observations)
- frequencies and spectral setup: sky frequencies 344.09 (CO 3-2), 354.98 (HCO+), 352.76 (HCN), 342.80 GHz (continuum); 0.49 MHz resolution smoothed to 11.7 MHz (10.15 km/s)  
  > "The corresponding sky frequencies were 344.09 GHz, 354.98 GHz, 352.76 GHz, and 342.80 GHz, respectively." (2 Observations); "The spectra were then smoothed to 11.7 MHz (10.15 km/s) to build channel maps." (2 Observations)
- continuum bandwidth: 6500 MHz (four sub-bands, lines subtracted)  
  > "The bandwidth available then amounts to 6500 MHz, yielding an rms noise level of 0.055 mJy." (3.2 Continuum emission)
- arrays: ALMA cycle 0, 23 antennae  
  > "with the ALMA array in cycle 0, using 23 antennae" (2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.64'' x 0.43'', PA 123 deg  
  > "the extended configuration provided in Band 7 a beam of 0.64$''$ x 0.43$''$, with a PA of 123$^\circ$" (2 Observations)
- max recoverable scale: ~3'' filtered in each channel map  
  > "extended emission was filtered out at scales larger than $\sim$3$''$  in each channel map" (2 Observations)
- sensitivity: 0.05 mJy/beam continuum; ~1.3 mJy/beam in line cubes at 10 km/s  
  > "an rms of 0.05 mJy/beam in the continuum, and $\sim$1.3 mJy/beam in the line cubes at 10 km/s resolution" (2 Observations)
- time on source: 28 min per block, 2 blocks, 2 h total duration  
  > "The observations were done in 2 blocks, with a total duration of 2 hours. For each period, NGC 1566 was observed for 28 minutes" (2 Observations)
- observing dates: October 22, 2012  
  > "The observations were carried out on October 22, 2012" (2 Observations)
- pi or archival as stated: PI Combes, own cycle 0 program  
  > "under the project ID 2011.0.00208.S (PI: Combes)" (2 Observations)
- Line: CO J=3-2 (not stated)
- Line: HCO+ J=4-3 (not stated)
- Line: HCN J=4-3 (not stated)
- Other facility **HST**: U,B,V,I images (F275W, F450W, F606W, F814W) for comparison; F814W used for stellar potential  
  > "We superposed the CO map onto HST images in the U, B, V and I filters (F275W, F450W, F606W, F814W)." (3.1 Molecular gas distribution and morphology)
- Other facility **SEST**: CO(2-1) single-dish spectrum for missing flux comparison (Bajaja et al. 1995)  
  > "These single dish observations were obtained with the SEST in CO(2-1) with a 22$''$  beam." (3.1 Molecular gas distribution and morphology)
- External data: Central CO(2-1) SEST spectrum and masses  
  > "Bajaja etal. (1995) found a CO(2-1) spectrum peaking at T$_A^*$= 120mK with FWHM=200 km/s" (3.4 H2 mass) [from Bajaja et al. 1995]
- External data: Black hole mass 8.3e6 Msun  
  > "The mass of the NGC 1566 black hole has been estimated to be 8.3 $\times$ 10$^6$ M$_{\odot}$ by the M-$\sigma$ relation" (1.1 NGC 1566) [from Woo & Urry (2002)]
- External data: Inclination 35 deg and PA 44 deg  
  > "Inclination | 35.0$^\circ$ | \(3\) |" (Table 1) [from Agüero et al. (2004)]

## Processing

### Calibration

- pipeline or manual: CASA used for calibration  
  > "The data were calibrated with the CASA software (v4.1; McMullin etal. 2007)" (2 Observations)
- casa version: CASA v4.1  
  > "The data were calibrated with the CASA software (v4.1; McMullin etal. 2007)" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune (line contribution subtracted); bandpass J1924-292; phase J0455-462  
  > "Flux calibration was done on Neptune, after subtracting the line contribution from its spectrum; band-pass calibration used J1924-292, and the phase calibrations the nearby radio source J0455-462." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: cleaning and imaging finalised with GILDAS  
  > "the cleaning and imaging were then finalised with the GILDAS software (Guilloteau & Lucas 2000)" (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust 0.5  
  > "The maps were made with Briggs weighting and a robustness parameter of 0.5" (2 Observations)
- uv taper: _not stated_
- cell size: 0.11 arcsec  
  > "256x256 pixels of 0.11$''$ per pixel" (2 Observations)
- image size: 256x256 pixels, 50 channels of ~10 km/s  
  > "The final cubes are 256x256 pixels of 0.11$''$ per pixel in the plane of the sky, and 50 channels of $\sim$10 km/s width." (2 Observations)
- masking: mask made from integrated CO(3-2) map  
  > "The data were cleaned using a mask made from the integrated CO(3-2) map." (2 Observations)
- multiscale scales: _not stated_
- continuum subtraction: continuum subtracted from all line maps  
  > "The continuum was subtracted from all line maps." (2 Observations)
- line free channels: _not stated_
- primary beam correction: maps not corrected; spectra and masses corrected  
  > "The maps and images shown in the figures of the present paper are not corrected for primary beam attenuation." (2 Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.64'' x 0.43''  
  > "a beam of 0.64$''$ x 0.43$''$, with a PA of 123$^\circ$" (2 Observations)
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- Line-free channels for continuum subtraction
- Clean threshold and iterations
- Rest frequencies used
- Exact rotation-curve model fitting procedure and uncertainties
- Gas density map construction for torque weighting
- Flux calibration uncertainty

## Analysis recipe

1. **Moment maps and flux measurement**: clipped cube with pixels <2 sigma (2.6 mJy/beam) set to zero; Gaussian fits to integrated spectra  
  > "To measure fluxes we used a clipped cube where all pixel values $<$2$\sigma$ (2.6 mJy/beam) were set to zero." (3.1 Molecular gas distribution and morphology)
   - software: GILDAS
   - fitting: _not stated_
   - validation: compared with SEST CO(2-1) to estimate missing flux  
  > "telling us that we are certainly missing some flux, by a factor up to $\sim$ 2" (3.4 H2 mass)
2. **Derive H2 mass**: convert CO(3-2) flux assuming thermalized gas and Galactic X_CO  
  > "assuming thermally excited gas, and a Milky-Way like CO-to-H$_2$ conversion factor, of 2.3 10$^{20}$cm$^{-2}$/(Kkm/s)" (3.4 H2 mass)
   - assumption: D=10 Mpc; X_CO=2.3e20  
  > "we adopt the median value given by NED, i.e. D=10 Mpc" (1.1 NGC 1566)
   - fitting: _not stated_
   - validation: comparison with SEST mass  
  > "In the 22$''$ beam, the SEST CO(2-1) spectrum, together with the CO(2-1)/CO(1-0) ratio of 1, yields a mass 1.7 $\times$ 10$^8$ M$_\odot$, while we find 0.7 $\times$ 10$^8$ M$_\odot$ in our FoV" (H$_2$ mass)
3. **Stellar potential and gravity torques**: HST F814W deprojected, Fourier transformed to potential; torque t=xFy-yFx weighted by CO gas density, azimuthally averaged  
  > "The image has been rotated and deprojected according to PA=44$^\circ$ and i=35$^\circ$, and then Fourier transformed to compute the gravitational potential and forces." (4 Torques and AGN fueling)
   - parameter: M/L=0.5 in I band, h_r=3.8 kpc, h_z=317 pc, pixel 0.079''  
  > "constant mass-to-light ratio of M/L = 0.5 M$_{\odot}$/L$_{\odot}$ in the I-band" (4 Torques and AGN fueling)
   - assumption: bulge not separated; dark matter neglected  
  > "Dark matter can be safely neglected inside the central kpc." (4 Torques and AGN fueling)
   - fitting: M/L fit to reproduce CO rotation curve  
  > "The stellar M/L value was fit to reproduce the observed CO rotation curve." (4 Torques and AGN fueling)
   - validation: i and PA varied by ±5 deg  
  > "We have checked that the results are not significantly changed when the geometrical parameters (i and PA) are varied by $\pm$5$^\circ$" (4 Torques and AGN fueling)

## Software

- **CASA** 4.1: calibration  
  > "The data were calibrated with the CASA software (v4.1; McMullin etal. 2007)" (2 Observations)
- **GILDAS** : cleaning and imaging  
  > "the cleaning and imaging were then finalised with the GILDAS software (Guilloteau & Lucas 2000)" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(3-2) integrated flux | 596 | 2 | Jy km/s | 1 | CO(3-2) / 596$\pm$ 2 |
| Continuum peak at 0.87 mm | ~3 | 50 sigma | mJy | 1 | The $\sim$ 3mJy peak emission is detected at 50$\sigma$ significance. |
| Total continuum in FoV | 12.5 | not stated | mJy | 1 | The total continuum emission integrated over our FoV amounts to 12.5 mJy |
| H2 mass in 18'' FoV | 0.7e8 | not stated | Msun | 2 | we find 0.7 $\times$ 10$^8$ M$_\odot$ in our FoV of 18 $''$ |
| Gas angular momentum loss between 200-300 pc | half in one rotation (~7 Myr) | not stated | Myr | 3 | Between 200 and 300 pc, the gas loses half of its angular momentum in one rotation, which is $\sim$ 7 Myr. |
| Peak residual velocity | ~30 | not stated | km/s | 0 | peak at $\sim$ 30 km/s S-SE of the nucleus |

## Qualitative findings

- CO nuclear disk of ~150 pc radius with a 2-arm trailing spiral inside the ILR ring, coincident with dust lanes; no symmetric molecular outflow  
  > "it is remarkable that no symmetric molecular outflow, indicating a possible AGN feedback, is observed" (Summary)

## Claim tuples

- H: Is there molecular outflow in NGC 1566? | E: Residual velocity field after rotation model subtraction and PV diagrams | R: residuals ≤30 km/s, spiral-following | F: No outflow; streaming motions | **supported**
- H: Do gravity torques drive gas inward within the ILR? | E: Torque computed from HST potential weighted by CO | R: negative torques 50-300 pc | F: Efficient fueling; BH influences spiral to trailing | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Distance 17.8 Mpc rejected as gas-to-dynamical mass ratio unrealistically high  
  > "For the higher distance, the gas to dynamical mass ratio is unrealistically high, favoring lower values." (1.1 NGC 1566)
- How they decided it was enough: _not stated_
- Limitation (authors): Missing flux up to a factor ~2 due to missing short spacings and primary beam  
  > "we are certainly missing some flux, by a factor up to $\sim$ 2" (3.4 H2 mass)
- Caveat (inferred, ours): Distance uncertain (6.5-17.8 Mpc) affects all physical scales
- Caveat (inferred, ours): Torques use CO with large missing flux
- Caveat (inferred, ours): BH mass from M-sigma only

## Reproducibility

- Data public (paper): project ID given; Cycle 0 data  
  > "ADS/JAO.ALMA#2011.0.00208.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Torque code and gas map details
- Missing: clean parameters
- Missing: line-free channels
- Data volume (inferred): ~10-20 GB raw
- Score (inferred): 3/5, Public data and basic imaging stated, but torque analysis and clean settings underspecified.
- Rediscovery candidate: no, Torque analysis recipe is incomplete.

## Links

- Method: Garcı́a-Burillo et al. 2005 (torque computation method)
- Companion: Combes et al. 2013 (NGC 1433 ALMA cycle 0 study)
- Related: NUGA

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 46,
  "rate": 0.708
 },
 "evidence_ok": true
}
```
