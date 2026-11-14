# ALMA Reveals a Collision between Protostellar Outflows in BHR 71

`2018AJ....156..239Z` | The Astronomical Journal 2018 | first author: Zapata, Luis A. | arXiv: 1804.00625 | DOI: 10.3847/1538-3881/aae51e

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation
- Question: Are the two protostellar outflows from IRS 1 and IRS 2 in BHR 71 colliding, and what does this imply for the 3D geometry?  
  > "These images reveal for the first time solid evidence that their flows are partially colliding" (abstract)
- Target **BHR 71 (IRS 1 and IRS 2)**: coordinates _not stated_; z/distance 200 pc (assumed)  
  > "powered by two young stars separated by 15$''$ or 3500 AU (at an assumed distance of 200 pc) called IRS 1 and IRS 2" (Introduction); distance from assumed; cited to Bourke et al. 1997  
  > "powered by two young stars separated by 15$''$ or 3500 AU (at an assumed distance of 200 pc) called IRS 1 and IRS 2" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00518.S
- bands: Band 6 (1.3 mm)  
  > "carried out with ALMA at Band 6 in 2015 Jan 17" (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 4.236 GHz total from six spws  
  > "which covers a total bandwidth of 4.236 GHz" (Observations)
- arrays: 35 antennas of 12 m  
  > "The observations used 35 antennas with a diameter of 12 m" (Observations)
- configurations: _not stated_
- baselines: 15 to 348.5 m (11-268 klambda)  
  > "yielding baselines with projected lengths from 15 to 348.5 m (11–268 k$\lambda$)" (Observations)
- angular resolution: continuum 1.2"x1.1" (PA -63.6 deg); line 1.6"x1.4" (PA -77.2 deg)  
  > "at an angular resolution of $1\rlap.{''}6 \times 1\rlap.{''}4$ with a PA = $-$77.2$^\circ$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.4 mJy/beam; line rms 50 mJy/beam km/s  
  > "The resulting image *rms* noise for the continuum was 0.4 mJy beam$^{-1}$" (Observations)
- time on source: 14.1 minutes, 14-pointing mosaic  
  > "The integration time on-source was 14.1 minutes, approximately 1 min. for each pointing in the mosaic." (Observations)
- observing dates: 2015 Jan 17  
  > "carried out with ALMA at Band 6 in 2015 Jan 17" (Observations)
- pi or archival as stated: archival  
  > "The archive observations of the BHR 71 protostellar binary system" (Observations)
- Line: 12CO J=2-1 (230.548 GHz (spw3 center))
- External data: Envelope masses and luminosities of IRS 1 and IRS 2, used for comparison  
  > "a mass of the dusty envelope of 2.1$\pm$0.4M$_\odot$" (Introduction) [from (cite: che2008)]
- External data: Dust mass opacity 0.015 cm2/g at 1.3 mm  
  > "Assuming a dust mass opacity ($\kappa_\nu$) of 0.015 cm$^2$ g$^{-1}$" (Results) [from (cite: Oss1994)]

## Processing

### Calibration

- pipeline or manual: CASA used for calibration, imaging and analysis; pipeline vs manual not stated  
  > "The data were calibrated, imaged, and analyzed using the Common Astronomy Software Applications CASA" (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymedes  
  > "Ganymedes was used for the flux amplitude." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: phase and amplitude, using the continuum image as model; applied to spectra  
  > "We did self-calibration in phase and amplitude using the resulting mm continuum image as model." (Observations)

### Imaging

- task: CLEAN in CASA  
  > "Imaging of the calibrated visibilities was done using the task CLEAN." (Observations)
- deconvolver: _not stated_
- weighting robust: robust = 0  
  > "We used the ROBUST parameter of CLEAN in CASA set to 0." (Observations)
- uv taper: outer taper 140 klambda (line image)  
  > "A mild outer taper (140 k$\lambda$) was applied to avoid the sparsity of the longest baselines." (Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: line 1.6"x1.4" PA -77.2; continuum 1.2"x1.1" PA -63.6  
  > "at an angular resolution of $1\rlap.{''}2 \times 1\rlap.{''}1$ with a PA = $-$63.6$^\circ$" (Observations)
- final rms: continuum 0.4 mJy/beam; line 50 mJy/beam km/s  
  > "the resulting image *rms* noise was 50 mJy beam$^{-1}$ km s$^{-1}$" (Observations)

### Not stated but needed to reproduce (our reading)

- CASA version
- Continuum-subtraction method and line-free channels
- Clean threshold, masks, image size and cell size
- Self-calibration solution intervals
- Channel width/velocity resolution used for moment maps and any clipping threshold for moments
- Flux-scale uncertainty
- Which quasar was bandpass versus gain calibrator (text repeats J1229-6003)
- Method used to fit the deconvolved source sizes
- Method for outflow opening angles

## Analysis recipe

1. **Calibrate and image continuum and CO(2-1)**: CASA calibration, self-calibration, CLEAN imaging of the mosaic  
  > "Imaging of the calibrated visibilities was done using the task CLEAN." (Observations)
   - software: CASA
   - parameter: robust = 0; 140 klambda taper for line  
  > "A mild outer taper (140 k$\lambda$) was applied to avoid the sparsity of the longest baselines." (Observations)
   - fitting: _not stated_
   - validation: Image rms compared with theoretical rms (0.3 mJy/beam continuum, 40 mJy/beam km/s line)  
  > "which is very close to the value we obtain in the continuum images" (Observations)
2. **Measure continuum sizes and flux densities and derive dust masses**: Deconvolved sizes and flux densities; optically thin isothermal dust mass formula  
  > "Assuming that the dust emission is optically thin and isothermal, the dust mass (M$_d$) is directly proportional to the flux density" (Results)
   - parameter: kappa = 0.015 cm2/g, beta = 1.5, Td = 25 K  
  > "a characteristic dust temperature (T$_d$) of 25 K" (Results)
   - assumption: Distance 200 pc, dust-to-gas 100, optically thin emission (so masses are lower limits)  
  > "we estimated a lower limit (provided that the emission is not optically thin)" (Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Map outflow morphology and kinematics (moments 0,1,2)**: Moment maps of CO(2-1); moment 1 integrated -25 to +20 km/s; redshifted map 0 to +20 km/s  
  > "The range of velocities where we integrated to construct this image is from $-$25 to $+$20 km s$^{-1}$." (Results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
4. **Estimate collision probability for capsule-shaped flows**: Monte Carlo of random orientations of two capsules, 10^5 realizations per separation; overlap if s<2r  
  > "For each separation we run a realization with $10^5$ sets of $a_1, b_1, c_1, a_2, b_2, c_2$ values" (The probability of Colliding Flows)
   - parameter: BHR 71: r = 10", h = 20", d = 15"  
  > "we adopt as values $r = 10"$, $h=20"$, and $d=15"$" (The probability of Colliding Flows)
   - assumption: Sky-plane dimensions represent true dimensions  
  > "Here we are making the assumption that the dimensions in the plane of the sky represent the true dimensions." (The probability of Colliding Flows)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration, imaging (CLEAN), analysis  
  > "The data were calibrated, imaged, and analyzed using the Common Astronomy Software Applications CASA" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| IRS 1 continuum flux density | 547 | 10 | mJy | 2 | a flux density of 547 $\pm$ 10 mJy |
| IRS 2 continuum flux density | 44 | 5 | mJy | 2 | a flux density of 44 $\pm$ 5 mJy |
| IRS 1 dust mass (lower limit) | 0.215 | 0.004 | Msun | 2 | about 0.215$\pm$0.004 M$_\odot$ |
| IRS 2 dust mass (lower limit) | 0.017 | 0.002 | Msun | 2 | 0.017$\pm$0.002 M$_\odot$ |
| Outflow opening angle IRS 1 | 44 | not stated | deg | 3 | open angle of about $44\ensuremath{^\circ}$, versus $29\ensuremath{^\circ}$ for the outflow of IRS 2 |
| Outflow opening angle IRS 2 | 29 | not stated | deg | 3 | open angle of about $44\ensuremath{^\circ}$, versus $29\ensuremath{^\circ}$ for the outflow of IRS 2 |
| Max line width in colliding zone | 7.5 | not stated | km/s | 3 | very broad-lines (up to 7.5 km s$^{-1}$ wide) |
| CO enhancement in colliding zone | factor of two or three | not stated | dimensionless | 3 | strong and abrupt increase of CO flux of about a factor of two or three |

## Qualitative findings

- IRS 2 outflow is partially colliding with and deflected by the IRS 1 outflow; IRS 2 is probably closer to the observer  
  > "derive that IRS 2 should be closer to us than IRS 1" (Conclusions)

## Claim tuples

- H: Are the BHR 71 outflows colliding? | E: CO(2-1) moment 0/1/2 maps with ALMA | R: CO brightening, broad lines (up to 7.5 km/s) and redirected stream at the overlap zone | F: The outflows are probably partially colliding | **supported**
- H: Collision likelihood for close wide binary flows | E: Monte Carlo capsule overlap model | R: Probability near 1 for BHR 71; 0.2 and 0.5 for IC 1396N and G028.37 | F: Collisions may be more common than observed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: 12CO(2-1) is a good outflow tracer  
  > "which is well known to be an excellent outflow tracer" (Observations)
- Alternative: Redshifted emission from IRS 1 outflow exiting its cloud; rejected as unable to explain all facts; projection overlap also noted  
  > "this hypothesis cannot explain some of the observational facts" (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust masses are lower limits with up to factor of two or three uncertainty  
  > "The actual uncertainty could be very large (a factor of two or three)" (Results)
- Limitation (authors): Collision may be projection overlap  
  > "These results may suggest that both outflows are colliding or just overlapping in projection." (Results)
- Caveat (inferred, ours): Evidence is morphological and kinematic; the collision is not quantified (no momentum or energy analysis).
- Caveat (inferred, ours): Projection overlap is not rigorously excluded.
- Caveat (inferred, ours): The probability model assumes sky-plane sizes are true sizes and ignores the outflow's actual shape.

## Reproducibility

- Data public (paper): Archival ALMA data  
  > "The archive observations of the BHR 71 protostellar binary system" (Observations)
- Products in archive: _not stated_
- Missing: CASA version and calibration scripts
- Missing: Cleaning parameters and masks
- Missing: Moment clipping thresholds
- Missing: Monte Carlo code
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Data are public and the pipeline is simple, but many imaging parameters are unstated and the results are mostly qualitative.
- Rediscovery candidate: no, Main results are qualitative morphology and kinematics, and the recipe is incomplete.

## Links

- Companion: (cite: par2006) (APEX CO(4-3) of the IRS 2 outflow)

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 39,
  "rate": 0.582
 },
 "evidence_ok": true
}
```
