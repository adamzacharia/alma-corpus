# ALMA and VLA observations of the outflows in IRAS 16293-2422.

`2013MNRAS.430L..10L` | Monthly Notices of the Royal Astronomical Society 2013 | first author: Loinard, L. | arXiv: 1211.4744 | DOI: 10.1093/mnrasl/sls038

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Which embedded sources in IRAS 16293-2422 drive the NE-SW, EW and any other outflows, and what is the nature of the outflow from source B?  
  > "These data clarify the origins of the protostellar outflows from the deeply embedded sources in this complex region." (abstract)
- Target **IRAS 16293-2422**: coordinates _not stated_; z/distance 120 pc  
  > "IRAS 16293–2422 (Ceccarelli et al. 2000; Crimier et al. 2010) is located at a distance of 120 pc (Loinard et al. 2008) in the eastern part of the Ophiuchus complex." (Introduction); distance from Loinard et al. 2008  
  > "IRAS 16293–2422 (Ceccarelli et al. 2000; Crimier et al. 2010) is located at a distance of 120 pc (Loinard et al. 2008) in the eastern part of the Ophiuchus complex." (Introduction)

## Data provenance

- ALMA projects: 2011.0.00007.SV
- bands: 0.45 mm (ALMA); VLA 7 mm and 4 cm  
  > "IRAS 16293–2422 was observed at $\lambda$ = 0.45 mm with fifteen 12-m antennas of ALMA on April 2012, during the science verification data program." (2.1 ALMA data)
- frequencies and spectral setup: 4 spectral windows of 1875 MHz, 3840 channels each; 0.488 MHz channels, 0.4 km/s resolution after Hanning smoothing  
  > "The digital correlator was configured in 4 spectral windows of 1875 MHz and 3840 channels each." (2.1 ALMA data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: VLA A configuration  
  > "IRAS 16293–2422 was observed with the VLA in its most extended (A) configuration on 2011, June 5 and 8 at $\lambda$ = 7 mm" (2.2 VLA data)
- baselines: 105 baselines, 26 to 403 m  
  > "The 105 independent baselines ranged in projected length from 26 to 403 m." (2.1 ALMA data)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: line channels ~50 mJy/beam; continuum 20 mJy/beam  
  > "The r.m.s. noise, measured in line-free channels on either side of the CO line, is about 50 mJy beam$^{-1}$" (2.1 ALMA data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA science verification data  
  > "during the science verification data program" (2.1 ALMA data)
- Line: CO J=6-5, v=0 (691.47308 GHz)
- Other facility **VLA**: 7 mm and 4 cm continuum imaging of ionized gas/jets  
  > "at $\lambda$ = 7 mm, and on 2011, August 12 at $\lambda$ = 4 cm." (2.2 VLA data)
- External data: Source Ab flux 0.5 Jy at 305 GHz  
  > "0.5 Jy at 305 GHz (Chandler et al. 2005)" (3.1 Continuum emission and the NE-SW flow) [from Chandler et al. 2005]
- External data: Systemic velocity of source B about 3 km/s  
  > "the systemic velocity of source B is about 3 km s$^{-1}$ (Jørgensen et al. 2011)" (3.3 A compact outflow from source B) [from Jørgensen et al. 2011]

## Processing

### Calibration

- pipeline or manual: VLA manually inspected, flagged and calibrated in CASA  
  > "The data were manually inspected and flagged, and calibrated following standard procedures." (2.2 VLA data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: ALMA: Juno; VLA: 3C286  
  > "Observations of Juno provided the absolute scale for the flux density calibration" (2.1 ALMA data); "the absolute flux calibrator was 3C286 (J1331$+$3030)" (2.2 VLA data)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: VLA 4 cm robust = -2; 7 mm robust = +2 and 0  
  > "(Robust parameter set to $-$2 in CASA)" (2.2 VLA data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: channels around 4 km/s ignored to filter ambient emission  
  > "we filtered it out by ignoring the velocity channels around 4 km s$^{-1}$" (3.3 A compact outflow from source B)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ALMA 0.32" x 0.18", PA -69°  
  > "at an angular resolution of $0\mbox{$''\mskip-7.6mu.\,$}32$ $\times$ $0\mbox{$''\mskip-7.6mu.\,$}18$; $-69^\circ$" (2.1 ALMA data)
- final rms: ALMA continuum 20 mJy/beam; VLA 4 cm 16 uJy/beam; 7 mm 19 and 31 uJy/beam  
  > "the r.m.s. noise of the continuum image is only moderately better (20 mJy beam$^{-1}$)" (2.1 ALMA data)

### Inherited from earlier work

- Other spectral lines in these ALMA data described elsewhere  
  > "The continuum emission as well as many spectral lines were detected in these ALMA data (see Jørgensen et al. 2012)." (2.1 ALMA data) [from Jørgensen et al. 2012]

### Not stated but needed to reproduce (our reading)

- ALMA and CASA versions
- Robust/weighting and deconvolver for ALMA imaging
- Line-free channels used for continuum
- ALMA pipeline vs manual calibration
- Moment-map clipping and velocity ranges
- Source coordinates

## Analysis recipe

1. **Calibrate and image ALMA and VLA data**: Calibration and imaging in CASA, with KARMA for analysis  
  > "The data were calibrated, imaged, and analyzed using the Common Astronomy Software Applications (CASA) and KARMA software (Gooch 1996)." (2.1 ALMA data)
   - software: CASA, KARMA
   - fitting: _not stated_
   - validation: _not stated_
2. **Map CO(6-5) outflow and compute dynamical age**: First moment map of CO(6-5) with ambient channels removed; expansion velocity ~10 km/s over 3" gives age ~200 yr  
  > "the dynamical age of the flow is of order 200 years" (3.3 A compact outflow from source B)
   - software: CASA
   - assumption: Distance of Ophiuchus (120 pc); nearly face-on so velocity mostly radial  
  > "In this configuration, the flow driven by source B ought to be oriented nearly along the line of sight" (3.3 A compact outflow from source B)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration, imaging, analysis of ALMA and VLA data  
  > "The data calibration was performed using the CASA software." (2.2 VLA data)
- **KARMA** : Analysis of ALMA data  
  > "Common Astronomy Software Applications (CASA) and KARMA software (Gooch 1996)" (2.1 ALMA data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total ALMA 0.45 mm flux of source B | ~12.2 | not stated | Jy | 1 | The total flux measured here with ALMA ($\sim$ 12.2 Jy) |
| Spectral index of Ab extension | 2.7 | 0.5 | dimensionless | 1 | This yields a spectral index of 2.7 $\pm$ 0.5 |
| Dynamical age of source B outflow | ~200 | not stated | yr | 2 | the dynamical age of the flow is of order 200 years |
| Bubble extent | 5.4e15 (360 AU) | not stated | cm | 2 | corresponds to 5.4 $\times$ 10$^{15}$ cm (360 AU) |
| Expansion velocity of bubble | ~10 | not stated | km/s | 2 | the (radial) expansion velocity of the bubble relative to source B is about 10 km s$^{-1}$ |

## Qualitative findings

- A2 drives the NE-SW flow and shows a new ejection (A2delta), implying an episodic, precessing jet  
  > "demonstrating that it drives an episodic jet" (abstract)

## Claim tuples

- H: Does source B drive its own outflow? | E: CO(6-5) first moment map from ALMA | R: 3" bubble-like blueshifted structure with B at the NW apex, ~10 km/s expansion, ~200 yr age | F: Source B drives a young, slow, moderately collimated outflow; it may be one of the youngest protostars | **supported**
- H: Does A2 drive an episodic jet? | E: VLA 7 mm and 4 cm continuum imaging | R: New compact source NE of A2 | F: New ejection from A2 | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: NE extension of A argued to be circumbinary envelope emission rather than a new protostar  
  > "rather than a new protostellar source in the system" (3.1 Continuum emission and the NE-SW flow)
- How they decided it was enough: _not stated_
- Limitation (authors): Ambient CO emission poorly recovered, so fluxes are underestimated  
  > "our fluxes (as given, for instance, in Figure [4](#fig:outflowB)) are clearly underestimated since they do not include the ambient gas" (3.3 A compact outflow from source B)
- Caveat (inferred, ours): Dynamical age is crude, with inclination and distance uncertainties
- Caveat (inferred, ours): No uncertainties on velocities or ages
- Caveat (inferred, ours): Missing short spacings

## Reproducibility

- Data public (paper): ALMA science verification data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00007.SV." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA versions and imaging parameters for ALMA
- Missing: VLA project codes
- Missing: Moment map velocity ranges and clipping
- Data volume (inferred): ~50-100 GB for ALMA SV plus VLA
- Score (inferred): 3/5, Data are public but imaging and moment-map details are sparse.
- Rediscovery candidate: no, The recipe is incomplete and the results are mostly morphological.

## Links

- Companion: Jørgensen et al. 2012 (Other lines in same ALMA data)
- Companion: Pineda et al. 2012 (ALMA infall/rotation toward B)
- Related: ALMA Science Verification

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
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
  "facts": 59,
  "stated": 28,
  "rate": 0.475
 },
 "evidence_ok": true
}
```
