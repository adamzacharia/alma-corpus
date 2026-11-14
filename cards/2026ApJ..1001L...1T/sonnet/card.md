# ALMA Band 9 CO(6─5) Reveals a Warm Ring Structure Associated with the Embedded Protostar in the Cold Dense Core MC 27/L1521F

`2026ApJ..1001L...1T` | The Astrophysical Journal Letters 2026 | first author: Tokuda, Kazuki | arXiv: 2602.12661 | DOI: 10.3847/2041-8213/ae47ec

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Does high-J CO(6-5) imaging reveal warm, dense gas structure (a ring) near the Class 0 protostar in MC 27/L1521F that low-J CO misses due to optical depth?  
  > "aiming to reveal warm molecular gas components that may be hidden or severely distorted in low-$J$ CO observations near $V_{\rm sys}$." (Introduction)
- Target **MC 27/L1521F**: coordinates _not stated_; z/distance D ~140 pc  
  > "stands out as one of the densest cores within the Taurus molecular cloud ($D \sim$140 pc; (cite: Galli18))." (Introduction); distance from Galli18  
  > "stands out as one of the densest cores within the Taurus molecular cloud ($D \sim$140 pc; (cite: Galli18))." (Introduction)

## Data provenance

- ALMA projects: 2024.1.00023.S, 2011.0.00611.S, 2015.1.00340.S
- bands: Band 9, ACA 7 m array  
  > "using the Atacama Compact Array (ACA) 7 m array in Band 9." (Observations and Data Reduction)
- frequencies and spectral setup: 4 SPWs: 673.754 and 685.421 GHz (1.875 GHz, 1920 ch), continuum 689.364 GHz (2.000 GHz, 128 ch), CO(6-5) 691.437 GHz (0.117 GHz, 480 ch)  
  > "one high-resolution window covering CO($J{=}6$–5) centered at 691.437 GHz with 0.117 GHz bandwidth and 480 channels." (Observations and Data Reduction)
- continuum bandwidth: 5.75 GHz total, centre 682.5 GHz  
  > "yielding a total bandwidth of 5.75 GHz with an effective central frequency of 682.5 GHz." (Observations and Data Reduction)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~2'' (~300 au); beam 1.8'' x 1.3'', PA -6.1 deg  
  > "The restoring beam is $1.8\ensuremath{''} \times 1.3\ensuremath{''}$ at a position angle of $-6.1\ensuremath{^\circ}$." (Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: cube rms 0.14 K; continuum rms 3.7 mJy/beam  
  > "The achieved rms noise in the final cube is 0.14 K." (Observations and Data Reduction); "The continuum image reaches an rms sensitivity of 3.7 mJy beam$^{-1}$" (Observations and Data Reduction)
- time on source: _not stated_
- observing dates: five execution blocks, 2025 September 11-23  
  > "The observations were executed in five execution blocks between 2025 September 11 and 23." (Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: CO J=6-5 (691.437 GHz (window centre))
- Other facility **CSO**: Single-dish CO(6-5) spectrum (Shinnaga 2009) for consistency check of missing flux  
  > "single-dish CO($J$=6–5) observations toward MC 27 have been reported with the Caltech Submillimeter Observatory (CSO) by (cite: Shinnaga_2009)" (Observations and Data Reduction)
- Other facility **ALMA 12 m / ACA TP (earlier projects)**: CO(3-2) and HCO+(3-2), H13CO+ data from earlier papers for comparison  
  > "the CO($J$=3–2) data from (cite: Tokuda_2018) and the HCO$^{+}$($J$=3–2) data from (cite: Tokuda_2014)" (Results)
- External data: CSO CO(6-5) spectrum, Tmb ~5 K, rms 0.6-1.4 K in 10'' beam  
  > "the spectrum toward the protostellar position reaches a main-beam brightness temperature of $\sim$5 K with an rms of $\sim$0.6–1.4 K." (Observations and Data Reduction) [from (cite: Shinnaga_2009)]
- External data: CO(3-2) data  
  > "the CO($J$=3–2) data from (cite: Tokuda_2018)" (Results) [from (cite: Tokuda_2018)]
- External data: HCO+(3-2) and H13CO+(3-2) data; density estimates for MMS-2  
  > "the HCO$^{+}$($J$=3–2) data from (cite: Tokuda_2014)" (Results) [from (cite: Tokuda_2014)]
- External data: Alfven-speed field strength B~1e-3 G from simulations  
  > "the magnetic field strength at radii of a few hundred au can reach $B\sim$10$^{-3}$ G (see their Figure 5)" (4.2 Velocity structure of the ring and its kinematic implications) [from (cite: Machida_2025)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline-calibrated visibilities (QA2 PASS)  
  > "We started from the pipeline-calibrated visibilities delivered by ALMA (QA2 PASS)." (Observations and Data Reduction)
- casa version: CASA 6.7.2 (imaging)  
  > "using CASA version 6.7.2" (Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: Calibrated MS used, re-imaged by user  
  > "We re-imaged the calibrated measurement sets on the user side using CASA version 6.7.2." (Observations and Data Reduction)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean, interactive (iclean)  
  > "Imaging was performed with `tclean` in interactive mode (`iclean`)" (Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We adopted natural weighting to maximize surface-brightness sensitivity" (Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: manual mask; threshold ~0.5x rms of dirty cube emission-free channels  
  > "the cleaning mask was selected manually, and the cleaning threshold was set to $\sim$0.5 times the rms noise measured in emission-free channels of the dirty cube." (Observations and Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: cube 1.8''x1.3'' PA -6.1 deg; continuum 1.7''x1.2'' PA -5.2 deg  
  > "with a synthesized beam of $1.7\ensuremath{''} \times 1.2\ensuremath{''}$ at a position angle of $-5.2\ensuremath{^\circ}$." (Observations and Data Reduction)
- final rms: 0.14 K (cube); 3.7 mJy/beam (continuum)  
  > "The achieved rms noise in the final cube is 0.14 K." (Observations and Data Reduction)

### Inherited from earlier work

- Systemic velocity V_sys = 6.5 km/s  
  > "$V_{\rm sys}=6.5~{\rm km~s^{-1}}$ (cite: Onishi99; Tatematsu04)" (Observations and Data Reduction) [from (cite: Onishi99; Tatematsu04)]
- Disk inclination i~70 deg  
  > "the compact dust disk is highly inclined ($i\sim70^\circ$; (cite: Terebey09; Tokuda_2017; Tokuda_2024))" (4.2 Velocity structure of the ring and its kinematic implications) [from (cite: Terebey09; Tokuda_2017; Tokuda_2024)]
- Interchange-instability scenario for ring interpretation  
  > "These eliminative arguments motivate us to revisit the scenario proposed by (cite: Tokuda_2024)" (4.2 Velocity structure of the ring and its kinematic implications) [from (cite: Tokuda_2024)]

### Not stated but needed to reproduce (our reading)

- Which ALMA pipeline version and which of the ACA calibrators were used
- Mask regions and number of clean iterations
- Cell size and image size
- Line-free channels and continuum subtraction method
- Flux scale uncertainty
- Primary-beam correction details
- Conversion to brightness temperature (Jy/beam to K) details
- Ring diameter measurement method
- Details of the CO(3-2) and HCO+ comparison data (projects 2011.0.00611.S, 2015.1.00340.S processing)
- Moment map velocity ranges clipping thresholds

## Analysis recipe

1. **Re-image ACA Band 9 CO(6-5) cube and continuum**: tclean interactive cleaning on pipeline-calibrated MS with natural weighting; 0.12 km/s channels; continuum from 3 SPWs  
  > "imaged the CO($J{=}6$–5) cube with a velocity resolution of 0.12 km s$^{-1}$." (Observations and Data Reduction)
   - software: CASA
   - parameter: threshold ~0.5x rms of dirty cube  
  > "the cleaning threshold was set to $\sim$0.5 times the rms noise measured in emission-free channels of the dirty cube." (Observations and Data Reduction)
   - fitting: _not stated_
   - validation: Compared ACA spectrum in 10'' beam with CSO spectrum; missing flux likely at most a few tens of percent  
  > "the overall agreement suggests that any missing flux in the ACA data is likely at most a few tens of percent when integrated over the full velocity range." (Observations and Data Reduction)
2. **Map morphology and kinematics (channel maps, moment 0/1)**: Channel maps and moment maps over broad (3-9 km/s) and narrow (6.3-6.7 km/s) ranges; compare with CO(3-2), HCO+, H13CO+  
  > "the ring becomes significantly sharper, with a central cavity of diameter $\sim$1000 au." (Results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Constrain temperature and density of the ring**: Excitation argument: observed TB ~ few K vs. LTE optically thick limit of 1.2 K at 10 K; density from MMS-2 values and CO(6-5) critical density  
  > "the maximum line brightness would be limited to the Rayleigh–Jeans-equivalent temperature of a 10 K blackbody at this frequency, $T_{\rm B}\simeq1.2$ K." (4.1 Physical properties of the ring near the systemic velocity)
   - assumption: Ring density between compact condensations and cold envelope; CO freeze-out below ~20 K  
  > "if the ring component were colder than $\sim$20 K, CO freeze-out would likely reduce the observable CO emission" (4.1 Physical properties of the ring near the systemic velocity)
   - fitting: _not stated_
   - validation: _not stated_
4. **Estimate ring expansion velocity and compare with Alfven speed**: Geometric correction with tilt phi<=45 deg to maximum offset ~3 km/s gives v_exp>~4.2 km/s; compare to vA=4.5 km/s (B/1e-3 G)(n/1e5)^-1/2  
  > "Assuming that the ring is not strongly tilted relative to the plane of the sky ($\phi\le45^\circ$), we obtain $v_{\rm exp}\gtrsim$4.2 km s$^{-1}$" (4.2 Velocity structure of the ring and its kinematic implications)
   - assumption: B~1e-3 G, n(H2)<~1e5 cm^-3 in ring interior  
  > "If the lower-density interior of the ring has $n({\rm H_2})\lesssim10^{5}~{\rm cm^{-3}}$" (4.2 Velocity structure of the ring and its kinematic implications)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.7.2: Re-imaging with tclean/iclean  
  > "We re-imaged the calibrated measurement sets on the user side using CASA version 6.7.2." (Observations and Data Reduction)
- **astropy** : listed in Software section; specific use not stated  
  > "astropy (cite: Astropy22), CASA (cite: CASAteam_2022)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Ring diameter / central cavity | ~1000 | not stated | au | 2 | the ring becomes significantly sharper, with a central cavity of diameter $\sim$1000 au. |
| Ring peak brightness temperature | ~3 | not stated | K | 2 | The typical peak brightness temperature at these velocity components is $\sim$3 K. |
| ACA spectrum peak Tb in 10'' beam | ~4 | not stated | K | 1 | the peak brightness temperature is $\sim$4 K |
| Ring kinetic temperature | >~20 | not stated | K | 3 | plausibly $T_{\rm kin}\gtrsim20$ K |
| Ring density | 1e5-1e6 | not stated | cm^-3 | 3 | the characteristic density of the CO($J$=6–5) ring is likely $n({\rm H_2})\sim10^{5}$–$10^{6}~{\rm cm^{-3}}$ |
| Minimum expansion velocity | >~4.2 | not stated | km/s | 4 | we obtain $v_{\rm exp}\gtrsim$4.2 km s$^{-1}$ |
| Continuum 3-sigma level | 11 | not stated | mJy/beam | 2 | $\gtrsim$3$\sigma$(= 11 mJy beam$^{-1}$) |

## Qualitative findings

- Off-centered ring seen near systemic velocity, not identifiable in low-J CO; emission concentrated to the northeast; ring plus eastern arc resembles numeral 9  
  > "the combination of the ring and the eastern arc yields a pattern that, as an aside, resembles the Arabic numeral “9”." (Results)

## Claim tuples

- H: High-J CO reveals warm gas structure hidden in low-J CO near systemic velocity | E: ACA Band 9 CO(6-5) imaging compared with CO(3-2) and HCO+ | R: Ring ~1000 au in diameter detected at 6-7 km/s | F: Ring is a coherent structure newly revealed by CO(6-5) | **supported**
- H: The ring is warm and dense | E: Brightness-temperature and excitation arguments | R: Tb ~3 K exceeds the 1.2 K limit for 10 K gas | F: T>~20 K and n~1e5-1e6 cm^-3 | **partially**
- H: Ring arises from magnetic-flux redistribution by interchange instability with shock heating | E: Kinematic and geometric comparison with scenario of Tokuda 2024 and Machida 2025 | R: Expansion velocity ~4 km/s consistent with Alfven speed; outflow face-on interpretation disfavored | F: Interpretation favored over outflow-only scenarios | **partially**

## Reasoning

- Why this data: Band 9 CO(6-5) traces warm/dense gas and avoids low-J optical depth problems  
  > "High-excitation CO transitions at submillimeter wavelengths provide a complementary probe because they preferentially trace warmer and/or denser gas" (Introduction)
- Why this method: _not stated_
- Alternative: Ring as face-on outflow structure disfavored (no connection to outflow wings; highly inclined disk)  
  > "However, this interpretation is disfavored for MC 27." (4.2 Velocity structure of the ring and its kinematic implications)
- How they decided it was enough: _not stated_
- Limitation (authors): No zero spacings in Band 9, so missing flux cannot be quantified precisely  
  > "our ACA 7 m array data therefore lack zero spacings." (Observations and Data Reduction)
- Limitation (authors): No multi-transition line ratios available  
  > "direct multi-transition line ratios are not yet available to tighten physical constraints." (4.1 Physical properties of the ring near the systemic velocity)
- Caveat (inferred, ours): Temperature and density limits are order-of-magnitude arguments without radiative transfer modelling
- Caveat (inferred, ours): Magnetic interpretation is not tested with direct field measurements
- Caveat (inferred, ours): Missing flux and filtering may alter ring morphology
- Caveat (inferred, ours): Single-pointing, low resolution (~2'')

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO, ALMA#2011.0.00611.S, 2015.1.00340.S and 2024.1.00023.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Cell/image size
- Missing: Mask definitions
- Missing: Exact moment-map thresholds
- Missing: Ring measurement procedure
- Missing: Comparison datasets from earlier projects
- Data volume (inferred): ~20-50 GB (five ACA EBs, Band 9)
- Score (inferred): 55/5, Imaging steps are described and data from one cycle-11 project are central, but many tclean parameters are missing and the interpretation is largely qualitative.
- Rediscovery candidate: no, Main results are morphological and order-of-magnitude, data public status is uncertain (proprietary period for 2025 data may apply).

## Links

- Companion: (cite: Tokuda_2024) (Interchange-instability scenario and disk/spike structures in MC 27)
- Companion: (cite: Tokuda_2018) (CO(3-2) data and warm shocked gas in MC 27)
- Companion: (cite: Tokuda_2014) (HCO+ and H13CO+ data, MMS-1/2/3 identification)

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 42,
  "rate": 0.575
 },
 "evidence_ok": true
}
```
