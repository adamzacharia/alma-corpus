# Sub-arcsecond Kinematic Structure of the Outflow in the Vicinity of the Protostar in L483

`2018ApJ...863...72O` | The Astrophysical Journal 2018 | first author: Oya, Yoko | arXiv: 1806.10298 | DOI: 10.3847/1538-4357/aacf42

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: What are the geometry, kinematics and possible rotation of the outflow cavity wall in the Class 0 protostar L483, and how do its parabolic-model parameters compare with those of other outflow sources?  
  > "Structures and kinematics of the outflow cavity wall are investigated in the CS line, and are analyzed by using a parabolic model of an outflow." (abstract)
- Target **L483 (IRAS 18148-0440)**: coordinates continuum peak (J2000) 18h17m29.947s, -04d39m39.55s  
  > "L483 is a dark cloud in Aquila Rift, whose distance from the Sun is 200 pc (Jørgensen et al. 2002; Rice et al. 2006)." (1.2 Target Source: L483); "We determined the peak position of the continuum emission to be ( α 2000, δ 2000 ) = (18 h 17 m 29 s . 947, -04 ◦ 39 ′ 39 ′′ . 55)" (3. Distribution); z/distance 200 pc  
  > "L483 is a dark cloud in Aquila Rift, whose distance from the Sun is 200 pc (Jørgensen et al. 2002; Rice et al. 2006)." (1.2 Target Source: L483); "We determined the peak position of the continuum emission to be ( α 2000, δ 2000 ) = (18 h 17 m 29 s . 947, -04 ◦ 39 ′ 39 ′′ . 55)" (3. Distribution); distance from Jørgensen et al. 2002; Rice et al. 2006  
  > "L483 is a dark cloud in Aquila Rift, whose distance from the Sun is 200 pc (Jørgensen et al. 2002; Rice et al. 2006)." (1.2 Target Source: L483); "We determined the peak position of the continuum emission to be ( α 2000, δ 2000 ) = (18 h 17 m 29 s . 947, -04 ◦ 39 ′ 39 ′′ . 55)" (3. Distribution)

## Data provenance

- ALMA projects: 2013.1.01102.S
- bands: Band 6 (1.2 mm)  
  > "were observed (ALMA Band 6)." (2. Observations)
- frequencies and spectral setup: CCH 262.0 GHz, CS 244.9 GHz, SO 261.8 GHz; channel width 61.030 kHz  
  > "The rotational lines of CCH, CS, and SO at 262.0, 244.9, and 261.8 GHz, respectively, were observed (ALMA Band 6)." (2. Observations); "where the channel width is 61.030 kHz." (2. Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: continuum beam 0.46 x 0.42 arcsec (P.A. 11.76 deg)  
  > "The synthesized beam size for the continuum image is 0 ′′ . 46 × 0 ′′ . 42 (P.A. 11. ◦ 76)." (3. Distribution)
- max recoverable scale: 3.3 arcsec for CCH and CS; 2.0 arcsec for SO  
  > "The maximum recoverable size of these observations is 3 ′′ . 3 for the CCH and CS lines, and 2 ′′ . 0 for the SO line." (2. Observations)
- sensitivity: rms 0.13 mJy/beam continuum; 8.2 (CCH) and 7.6 (CS) mJy/beam per channel  
  > "The rms noise level of the CCH and CS line images is evaluated to be 8.2 and 7.6 mJy beam − 1, respectively" (2. Observations)
- time on source: _not stated_
- observing dates: 12 June 2014 (Cycle 2)  
  > "The ALMA observations of L483 were carried out during its Cycle 2 operation (12 June 2014)." (2. Observations)
- pi or archival as stated: _not stated_
- Line: CCH N=3-2 (262.0 GHz)
- Line: CS J=5-4 (244.9 GHz)
- Line: SO not stated (261.8 GHz)
- External data: Outflow position angle 105 deg adopted  
  > "the position angle (P.A.) of the outflow is assumed to be 105 ◦ (Chapman et al. 2013)" (3. Distribution) [from Chapman et al. 2013]
- External data: Protostellar mass 0.15 Msun and j_IRE = 7.9e-4 km/s pc from the earlier ALMA analysis  
  > "evaluated the protostellar mass ( M ) of 0.15 M ⊙ and the radius of the centrifugal barrier ( r CB ) of 100 au." (Appendix A) [from Oya et al. 2017]
- External data: Outflow mass loss rate (5.4-14)e-6 Msun/yr  
  > "The outflow mass loss rate of L483 was reported to be (5 . 4 − 14) × 10 − 6 M ⊙ yr − 1 by Yıldız et al. (2015)." (8.1 Mass Rates of Outflow and Accretion) [from Yıldız et al. 2015]
- External data: Bolometric luminosity 13 Lsun  
  > "The bolometric luminosity is 13 L ⊙, according to Shirley et al. (2000)." (1.2 Target Source: L483) [from Shirley et al. 2000]
- External data: Parabolic outflow parameters and dynamical times for IRAS 15398-3359, L1527 and other comparison sources (Table 3)  
  > "Oya et al. (2014, 2015) reported the kinematic structure of the outflow near the protostar for IRAS 15398–3359 and L1527 observed with ALMA" (6.1 Comparison with Other Sources) [from Oya et al. 2014, 2015; Lee et al. 2000; Hirano et al. 2010; Arce et al. 2013]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration with the continuum data was applied; details not given  
  > "Self-calibration with the continuum data" (2. Observations)

### Imaging

- task: CLEAN procedure  
  > "We obtained images by employing the CLEAN procedure." (2. Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "The robustness parameter of the Brigg’s weighting was set to be 0.5." (2. Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum subtracted directly from visibilities; continuum from averaging line-free channels  
  > "We subtracted the continuum component directly from the visibilities to prepare the line image." (2. Observations)
- line free channels: _not stated_
- primary beam correction: Not applied  
  > "The primary beam correction is not applied." (2. Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 0.13 mJy/beam continuum; CCH 8.2, CS 7.6 mJy/beam  
  > "We obtained the root-mean-square (rms) noise level of 0.13 mJy beam − 1 for the continuum image." (2. Observations)

### Inherited from earlier work

- Other observational details (calibration, array configuration etc.)  
  > "Other observational details were reported elsewhere (Oya et al. 2017)." (2. Observations) [from Oya et al. 2017]
- Parabolic outflow model  
  > "We employ the standard outflow model reported by Lee et al. (2000)." (4. Outflow Structure Traced by CS) [from Lee et al. 2000]
- Similar model analysis as for IRAS 15398-3359  
  > "We therefore conduct a similar model analysis for L483." (4. Outflow Structure Traced by CS) [from Oya et al. 2014]
- Source age from bolometric temperature relation  
  > "The source age is obtained from the bolometric temperature by using the relation (Ladd et al. 1998)" (Figure 9 caption) [from Ladd et al. 1998]

### Not stated but needed to reproduce (our reading)

- Array configurations, baselines, time on source, calibrators and CASA version (deferred to Oya et al. 2017)
- Self-calibration solution intervals
- Line-free channels used for the continuum
- Image size, cell size, and CLEAN threshold/masks
- Fitting procedure for C and v0 (appears to be by-eye overlay on PV diagrams; no statistic or uncertainties given)
- PV extraction widths
- Values for the other sources in Table 3 (table not in text)

## Analysis recipe

1. **Image continuum and line cubes**: CLEAN with Briggs weighting, continuum subtracted in visibility plane, moment maps of CCH, CS, SO  
  > "We subtracted the continuum component directly from the visibilities to prepare the line image." (2. Observations)
   - parameter: robust = 0.5  
  > "The robustness parameter of the Brigg’s weighting was set to be 0.5." (2. Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract PV diagrams across the outflow**: PV diagrams along P.A. 105 deg and perpendicular cuts at P.A. 15 deg with offsets 0-10 arcsec on both lobes  
  > "which are prepared for the position axes taken along the lines with the position angle of 15 ◦ (Figure 1b) with the offsets (0 ′′ − 10 ′′ )" (5. Model Analysis of the Outflow)
   - parameter: outflow P.A. assumed 105 deg  
  > "the position angle (P.A.) of the outflow is assumed to be 105 ◦ (Chapman et al. 2013)" (3. Distribution)
   - assumption: elliptic PV feature traces the outflow cavity wall  
  > "this elliptic feature likely corresponds to the outflow cavity wall." (4. Outflow Structure Traced by CS)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit parabolic outflow model to PV diagrams**: Parabolic cavity wall z = C R^2 with velocity proportional to distance; fit free parameters C and v0 to PV diagrams and constrain inclination  
  > "We fit this model to the observed PV diagrams, and determine the two free parameters, C and v 0 ." (Appendix B)
   - parameter: i = 80 deg (75-90 allowed), C = 0.0025 au^-1, v0 = 0.0015 km/s; z0 = R0 = 1 au  
  > "The model parameters employed here are as follows; i = 80 ◦, C = 0.0025 au − 1, and v 0 = 0.0015 km s − 1 ." (5. Model Analysis of the Outflow)
   - assumption: velocity on the cavity wall proportional to distance to the protostar  
  > "cavity wall is assumed to be proportional to the distance to the protostar." (5. Model Analysis of the Outflow)
   - fitting: Qualitative comparison of model overlays; no sampler or likelihood stated  
  > "In Figure 2, the outflow model result is overlaid in white lines on the PV diagrams" (5. Model Analysis of the Outflow)
   - validation: Inclination below 75 or above 90 deg cannot reproduce the structure  
  > "With the inclination angle less than 75 ◦ or larger than 90 ◦, the kinematic structure cannot be reproduced by the model." (5. Model Analysis of the Outflow)
4. **Derive dynamical time and opening angle**: t_dyn = z/vz = z0/v0; opening angle tan(theta/2)=1/sqrt(aC)  
  > "t dyn = z/v z = z 0 /v 0, where z 0 is 1 au" (5. Model Analysis of the Outflow)
   - parameter: a = 500, 1000, 2000 au  
  > "is calculated to be 42 ◦, 32 ◦, and 24 ◦, for a of 500, 1000, and 2000 au, respectively." (Appendix B)
   - fitting: _not stated_
   - validation: Compared with literature dynamical times  
  > "Thus, the dynamical time scales are almost consistent with one another" (5. Model Analysis of the Outflow)
5. **Compare with other sources**: Linear fits of log C and log v0 versus t_dyn and T_bol for seven sources, equal weights  
  > "The dashed lines are obtained by linear fitting to the data under the assumption of equal weight." (6.2 Relation to Dynamical Ages)
   - fitting: Linear fit, uniform weights  
  > "where the uniform weights are applied to all the sources." (Figure 7 caption)
   - validation: _not stated_
6. **Test outflow rotation**: Overlay models with angular momentum conservation, j = 0, 1, 2, 4 x j_IRE, on PV diagrams  
  > "The rotation velocity of the outflow cavity wall is simply calculated under assumption of the angular momentum conservation." (7. Rotation Motion in the Outflow)
   - parameter: j_IRE = 7.9e-4 km/s pc  
  > "( j IRE = 7 . 9 × 10 − 4 km s − 1 pc; Oya et al. 2017)" (7. Rotation Motion in the Outflow)
   - assumption: specific angular momentum conserved along the outflow  
  > "The specific angular momentum of the gas is assumed to be conserved in each outflow model." (Figure 5 caption)
   - fitting: by visual comparison  
  > "Comparing the model results with the observations, we find a hint that the first and second models" (7. Rotation Motion in the Outflow)
   - validation: j = 1-2 x j_IRE better than no rotation at small offsets; 4x overestimates  
  > "The rotation motion seems to be overestimated in the third model ( j = 4 × j IRE ; red ellipses)." (7. Rotation Motion in the Outflow)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Outflow inclination angle | 80 (allowed 75-90) | not stated | deg | 3 | We constrain the inclination angle of the outflow to be from 75 ◦ to 90 ◦ |
| Curvature parameter C | 0.0025 | not stated | au^-1 | 3 | C = 0.0025 au − 1, and v 0 = 0.0015 km s − 1 . |
| Velocity parameter v0 | 0.0015 | not stated | km/s | 3 | C = 0.0025 au − 1, and v 0 = 0.0015 km s − 1 . |
| Dynamical timescale | 3e3 | 1e3 | yr | 4 | is evaluated to be (3 ± 1) × 10 3 yr |
| Opening angle at a=500, 1000, 2000 au | 42, 32, 24 | not stated | deg | 4 | is calculated to be 42 ◦, 32 ◦, and 24 ◦, for a of 500, 1000, and 2000 au, respectively. |
| Continuum peak synthesized beam | 0.46 x 0.42 (PA 11.76) | not stated | arcsec | 1 | 0 ′′ . 46 × 0 ′′ . 42 (P.A. 11. ◦ 76) |
| Mass accretion rate from t_dyn | 5e-5 | not stated | Msun/yr | 0 | can be estimated to be 5 × 10 − 5 M ⊙ yr − 1 |
| Mass accretion rate from luminosity | 6.9e-6 | not stated | Msun/yr | 0 | M ˙ acc is calculated to be 6 . 9 × 10 − 6 M ⊙ yr − 1 |
| Correlation coefficient log C vs t_dyn | -0.95 | not stated | dimensionless | 5 | The correlation coefficients are − 0 . 95, − 0 . 85, − 0 . 75, and − 0 . 63 for the four plots. |
| Fit slope log C vs t_dyn(1e3 yr) | -0.18 | 0.03 | dex per 1e3 yr | 5 | log C = ( − 0 . 18 ± 0 . 03) × ( t dyn × 10 − 3 ) + ( − 5 . 6 ± 0 . 3) |

## Qualitative findings

- CCH and CS trace the outflow at about 1000 au scale while SO traces only the compact component  
  > "On the other hand, the SO line, which is often regarded as the outflow tracer, does not trace the outflow components in this source." (9. Summary)

## Claim tuples

- H: Is the L483 outflow close to the plane of the sky? | E: Parabolic model fit to CS PV diagrams | R: i = 80 deg; below 75 or above 90 deg fails | F: The outflow is nearly perpendicular to the line of sight, in contrast to the earlier 50 deg estimate | **supported**
- H: Do outflow opening angle and velocity correlate with dynamical age? | E: Compare C and v0 for seven sources | R: Correlation coefficients -0.95 and -0.75 with t_dyn | F: C and v0 decrease with increasing dynamical time | **supported**
- H: Does the outflow cavity wall rotate? | E: Overlay rotating models on CS PV diagrams | R: Slant distortion favours j of 1-2 x j_IRE | F: Hint of rotation, marginal | **partially**

## Reasoning

- Why this data: CCH hyperfine offset is comparable to outflow velocity range, so CS was chosen  
  > "Therefore, we here focus on the outflow components traced by CS." (3. Distribution)
- Why this method: A similar parabolic model explained the IRAS 15398-3359 outflow with the same geometry  
  > "The kinematic structure of the outflow cavity wall of IRAS 15398–3359 is well explained by a parabolic model of an outflow (Oya et al. 2014)." (4. Outflow Structure Traced by CS)
- Alternative: CCH rejected for modelling because of hyperfine structure  
  > "the hyperfine structure of the CCH line often makes its velocity structure complicated." (3. Distribution)
- How they decided it was enough: _not stated_
- Limitation (authors): Rotation is marginal and angular momentum cannot be accurately evaluated  
  > "it is difficult to evaluate the amount of the specific angular momentum and the total angular momentum extracted by the outflow accurately at the current stage." (7. Rotation Motion in the Outflow)
- Limitation (authors): Extended emission is heavily resolved out  
  > "Thus, CS also traces the outflow in spite of a heavy resolving-out problem." (3. Distribution)
- Caveat (inferred, ours): Model parameters are matched by eye without formal uncertainties or goodness of fit
- Caveat (inferred, ours): Sample for trends is only seven sources with heterogeneous methods
- Caveat (inferred, ours): Heavy resolving-out affects the outflow structure
- Caveat (inferred, ours): Position angle fixed from literature rather than measured

## Reproducibility

- Data public (paper): ALMA dataset cited by project code  
  > "We use the ALMA data set ADS/JAO.ALMA#2013.1.01102.S." (9. Summary)
- Products in archive: _not stated_
- Missing: Calibration and array details in Oya et al. 2017
- Missing: Model fitting procedure
- Missing: Table 3 values for comparison sources
- Data volume (inferred): about 50-100 GB raw (single Cycle 2 Band 6 execution)
- Score (inferred): 3/5, Data are public and model equations given, but imaging details and fitting procedure are incomplete and the fit is by eye.
- Rediscovery candidate: no, The recipe lacks imaging and fitting details, and the model fit is qualitative.

## Links

- Method: Lee et al. 2000 (Standard parabolic outflow model)
- Method: Oya et al. 2014 (Similar model analysis and ballistic infall simulations)
- Companion: Oya et al. 2017 (Same ALMA data: infalling-rotating envelope and disk of L483)
- Companion: Oya et al. 2015 (L1527 outflow analysis and comparison data)

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 52,
  "rate": 0.634
 },
 "evidence_ok": true
}
```
