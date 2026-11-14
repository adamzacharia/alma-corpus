# ALMA Observations of the Outflow from Source I in the Orion-KL Region

`2012ApJ...754L..17Z` | The Astrophysical Journal Letters 2012 | first author: Zapata, Luis A. | arXiv: 1206.3600 | DOI: 10.1088/2041-8205/754/1/L17

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: What are the morphology and velocity structure of the large-scale SiO outflow from Orion Source I, and how do they compare with the small-scale maser kinematics?  
  > "contrary to what is found in the SiO and H$_2$O maser observations at scales of tens of AU, the blueshifted radial velocities of the moving gas are found to the northwest, while the redshifted velocities are in the southeast." (abstract)
- Target **Orion Source I (Orion BN/KL)**: coordinates ALMA phase center RA(J2000) 05h35m14.35s, Dec -05d22'35.00"  
  > "The phase reference center for the observations was at $\alpha_{J2000.0}$ = $05^{\rm h}35^{\rm m}14\mbox{$^{\rm s}\mskip-7.6mu.\,$}35$, $\delta_{J2000.0}$ = $-05^{\circ}22'35\mbox{$''\mskip-7.6mu.\,$}00$." (2.1 ALMA); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00009.SV
- bands: _not stated_
- frequencies and spectral setup: 4 spectral windows of 1875 MHz, 3840 channels, 0.488 MHz (~0.7 km/s) per channel; SiO window centered at 217.225 GHz; 5 tunings  
  > "The ALMA digital correlator was configured in 4 spectral windows of 1875 MHz and 3840 channels each." (2.1 ALMA); "has a central frequency of 217.225 GHz." (2.1 ALMA)
- continuum bandwidth: _not stated_
- arrays: 16 12-m antennas, ALMA science verification  
  > "The observations were made with sixteen antennas of ALMA on January 2012, during the ALMA science verification data program." (2.1 ALMA)
- configurations: _not stated_
- baselines: 18 to 253 kλ (120 baselines)  
  > "The 120 independent baselines ranged in projected length from 18 to 253 k$\lambda$." (2.1 ALMA)
- angular resolution: 1.78" x 1.23", PA -4.4 deg  
  > "The resulting r.m.s. noise for the line images was about 100 mJy beam$^{-1}$ at an angular resolution of $1\rlap.{''}78$ $\times$ $1\rlap.{''}23$ with a P.A. = $-4.4^\circ$." (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: rms ~100 mJy/beam per line image  
  > "The resulting r.m.s. noise for the line images was about 100 mJy beam$^{-1}$" (2.1 ALMA)
- time on source: about 100 min total, split over 5 tunings  
  > "The total on-source integration time was about 100 min." (2.1 ALMA)
- observing dates: January 2012  
  > "The observations were made with sixteen antennas of ALMA on January 2012" (2.1 ALMA)
- pi or archival as stated: _not stated_
- Line: SiO J=5-4; v=0 (217.10498 GHz)
- Other facility **SMA**: SiO J=8-7 v=0 maps at similar resolution, compact configuration, Dec 2009  
  > "The observations were obtained from the SMA, and were collected on December 2009, when the array was in its compact configuration." (2.2 SMA)

## Processing

### Calibration

- pipeline or manual: calibrated in CASA (details not given)  
  > "The data were calibrated, imaged, and analyzed using the Common Astronomy Software Applications (CASA)." (2.1 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto (ALMA); gain calibrator J0607-085  
  > "Observations of Callisto provided the absolute scale for the flux density calibration" (2.1 ALMA)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: uniform weighting (ALMA)  
  > "We used uniform weighting to obtain a slightly better angular resolution." (2.1 ALMA)
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
- final beam: 1.78" x 1.23", PA -4.4 deg  
  > "angular resolution of $1\rlap.{''}78$ $\times$ $1\rlap.{''}23$ with a P.A. = $-4.4^\circ$" (2.1 ALMA)
- final rms: ~100 mJy/beam  
  > "The resulting r.m.s. noise for the line images was about 100 mJy beam$^{-1}$" (2.1 ALMA)

### Not stated but needed to reproduce (our reading)

- CASA version and calibration procedure/scripts
- Cell size, image size, deconvolver, clean threshold and masks
- Continuum subtraction and line-free channels
- Channel width used for channel maps
- Primary beam correction treatment
- Whether SV reference calibrated data were used

## Analysis recipe

1. **Calibrate and image SiO J=5-4 cube**: Calibration and imaging in CASA with uniform weighting  
  > "The data were calibrated, imaged, and analyzed using the Common Astronomy Software Applications (CASA)." (2.1 ALMA)
   - software: CASA, KARMA
   - parameter: uniform weighting  
  > "We used uniform weighting to obtain a slightly better angular resolution." (2.1 ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Make moment-0 maps of blue/red wings**: Integrate over velocity ranges: blue -15 to -5, red +15 to +25, very high +26 to +30 km/s  
  > "The blueshifted gas emission was integrated over LSR velocities ranging from $-$15 km s$^{-1}$ to $-$5 km s$^{-1}$." (3 Results)
   - software: KARMA
   - fitting: _not stated_
   - validation: Compared with SMA SiO 8-7 maps and prior CARMA results  
  > "is in good agreement with the one obtained by (cite: plam2009) shown in their Figure 1." (3 Results)

## Software

- **CASA** : ALMA calibration, imaging, analysis  
  > "The data were calibrated, imaged, and analyzed using the Common Astronomy Software Applications (CASA)." (2.1 ALMA)
- **KARMA** : data analysis/visualization  
  > "To analyze the data, we also used the KARMA software (cite: goo96)." (2.1 ALMA)
- **MIRIAD** : SMA imaging (INVERT, robust=0)  
  > "We set the ROBUST parameter of the task INVERT to 0 to obtain an optimal compromise between resolution and sensitivity." (2.2 SMA)
- **MIR (IDL)** : SMA calibration  
  > "The data were calibrated using the IDL superset MIR" (2.2 SMA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA line image rms | 100 | not stated | mJy/beam | 1 | The resulting r.m.s. noise for the line images was about 100 mJy beam$^{-1}$ |
| Radial velocity of Source I | +6 | not stated | km/s | 2 | We estimated that the radial velocity of the Orion Source I is about $+$6 |
| SMA channel rms | 170 | not stated | mJy/beam | 0 | was about 170 mJy beam$^{-1}$ at an angular resolution of $2\rlap.{''}9$ $\times$ $1\rlap.{''}9$ |

## Qualitative findings

- Outflow has a butterfly morphology along NE-SW axis with blueshifted gas to the NW and redshifted to the SE, opposite to the maser sense  
  > "with the blueshifted radial velocities found to the northwest, while the redshifted velocities are toward the southeast." (3 Results)

## Claim tuples

- H: Does the large-scale SiO outflow share the velocity orientation of the small-scale masers? | E: ALMA SiO 5-4 and SMA SiO 8-7 moment maps | R: Blue to NW, red to SE, opposite to the masers | F: Velocity sense flips between small and large scales | **supported**
- H: Ballistic ejecta from a rotating disk explain the pattern | E: Qualitative comparison with Figure 4 expectation | R: Predicted largest velocities overlapping at center, not observed | F: Ruled out | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Ballistic ejection from a rotating disk rejected  
  > "This is not what is observed and we rule out this possibility." (4.2 Ballistic ejecta from a rotating disk)
- How they decided it was enough: _not stated_
- Limitation (authors): All hypotheses need further high-resolution sensitive observations  
  > "any of these hypotheses requires further sensitive, and high spatial resolution observations." (Conclusions)
- Caveat (inferred, ours): Purely qualitative interpretation; no quantitative kinematic modeling
- Caveat (inferred, ours): Imaging parameters and calibration not documented
- Caveat (inferred, ours): Contamination of the high-velocity gas by other BN/KL objects not quantified

## Reproducibility

- Data public (paper): ALMA Science Verification data  
  > "This paper makes use of the following ALMA Science Verification data: ADS/JAO.ALMA#2011.0.00009.SV" (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Channel/moment mask details
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public SV data and clear velocity ranges, but imaging details are missing and results are mostly qualitative.
- Rediscovery candidate: no, Results are mainly qualitative morphology and few numeric answers.

## Links

- Companion: Plambeck et al. 2009 (cite: plam2009) (CARMA SiO 2-1 imaging of the same outflow)
- Companion: Matthews et al. 2010 (cite: matt2010) (SiO maser kinematics at small scales)
- Related: ALMA Science Verification

## Checks

```json
{
 "quotes": 36,
 "quotes_ok": 36,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 58,
  "stated": 27,
  "rate": 0.466
 },
 "evidence_ok": true
}
```
