# An Ordered Bipolar Outflow from a Massive Early-stage Core

`2016ApJ...821L...3T` | The Astrophysical Journal Letters 2016 | first author: Tan, Jonathan C. | arXiv: 1601.07043 | DOI: 10.3847/2041-8205/821/1/L3

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Do the massive early-stage cores C1-N and C1-S host protostars driving ordered outflows, as traced by 12CO(2-1) and dense gas tracers?  
  > "Here we search for potential protostars and outflow activity via $^{12}$CO(2-1) and other tracers using an *ALMA* Cycle 2 observation." (Introduction)
- Target **C1-S (and C1-N), IRDC G028.37+00.07**: coordinates field center RA=18:42:46.5856, Dec=-04:04:12.361 (J2000); l=28.3230, b=+0.06750  
  > "The position of the field center was R.A.=18:42:46.5856, Dec.=-04:04:12.361 (FK5 J2000 system)" (2 Observations); "distance ($5\pm1\:$kpc)" (Introduction); z/distance 5±1 kpc  
  > "The position of the field center was R.A.=18:42:46.5856, Dec.=-04:04:12.361 (FK5 J2000 system)" (2 Observations); "distance ($5\pm1\:$kpc)" (Introduction); distance from kinematic distance  
  > "The position of the field center was R.A.=18:42:46.5856, Dec.=-04:04:12.361 (FK5 J2000 system)" (2 Observations); "distance ($5\pm1\:$kpc)" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00248.S, 2011.0.00236.S
- bands: _not stated_
- frequencies and spectral setup: channel width 1.129 MHz, 1.465 km/s; other basebands tuned to N2D+, C18O, DCN, DCO+, SiO, CH3OH  
  > "each channel has width $1.129\:$MHz, i.e., velocity resolution $1.465\:$$\rm{km\:s}^{-1}$" (2 Observations)
- continuum bandwidth: 1.875 GHz centered at 231 GHz (230.0625-231.9375 GHz)  
  > "a continuum band centered at $231\:$GHz with width $1.875\:$GHz" (2 Observations)
- arrays: _not stated_
- configurations: compact configuration  
  > "which observed the C1 region in a compact configuration on 05-Apr-2015" (2 Observations)
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: sensitive to scales ~10'' to ~1''  
  > "yielding sensitivity to scales from $\sim10\ensuremath{''}$ to $\sim1\ensuremath{''}$)" (2 Observations)
- sensitivity: 0.045 mJy per 1.51''x0.84'' beam  
  > "The achieved sensitivity was $0.045\:$mJy per $1.51\ensuremath{''}\times0.84\ensuremath{''}$ beam." (2 Observations)
- time on source: _not stated_
- observing dates: 05-Apr-2015  
  > "which observed the C1 region in a compact configuration on 05-Apr-2015" (2 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO 2-1 (230.538 GHz)
- Line: C18O 2-1 (not stated)
- Line: DCN 3-2 (not stated)
- Other facility **Spitzer-IRAC**: 8 um extinction (MIREX) mass surface density map  
  > "mid-infrared, i.e., $8\:\rm{\mu}\rm{m}$ *Spitzer-IRAC*, extinction (MIREX) mapping" (Introduction)
- Other facility **Herschel-PACS**: 70 um darkness check  
  > "$70\:\rm{\mu}\rm{m}$ (*Herschel-PACS*) images" (Introduction)
- External data: N2D+(3-2) ALMA Cycle 0 core definitions and velocities  
  > "$v_{\rm{LSR}}$ of C1-N and C1-S estimated from $\rm{N_2D}^+$(3-2) (T13)." (Results) [from Tan et al. 2013 (T13)]
- External data: MIREX Sigma map  
  > "Figure 1a presents the MIREX $\Sigma$ map (Butler et al. 2014) of the C1 region" (Results) [from Butler et al. 2014]
- External data: Protostellar model predictions of momentum flux  
  > "Models of massive protostar formation (Zhang et al. 2014) based on the Turbulent Core Model (MT03)" (Discussion) [from Zhang et al. 2014]

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
- weighting robust: natural weighting  
  > "which has been cleaned with natural weighting and had a primary beam correction applied" (Results)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: 12CO(2-1) integrated intensities continuum subtracted  
  > "integrated intensities of (continuum subtracted) $^{12}$CO(2-1)" (Results)
- line free channels: _not stated_
- primary beam correction: applied to continuum image  
  > "which has been cleaned with natural weighting and had a primary beam correction applied" (Results)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- N2D+(3-2) core velocities and boundaries from Cycle 0 data  
  > "contours of $\rm{N_2D}^+$(3-2) integrated intensity (T13), which define C1-S and C1-N" (Results) [from Tan et al. 2013 (T13)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration procedure
- Line-free channels and continuum subtraction method
- Image size, cell size, deconvolver, masks, and clean threshold
- CO(2-1) column density/mass conversion details (abundance, opacity)
- Peak-finding method for continuum sources
- Cycle 0 project processing for SiO check

## Analysis recipe

1. **Image continuum and identify protostars**: 1.3 mm continuum cleaned with natural weighting, primary beam corrected; protostars defined by continuum peaks  
  > "potential protostars defined by $1.3\:$mm dust continuum peaks detected in the *ALMA* Cycle 2 image" (Results)
   - fitting: _not stated_
   - validation: _not stated_
2. **Map outflows and ambient gas**: 12CO(2-1) integrated intensity in red/blue velocity ranges, channel maps, PV diagrams along outflow axes in 3'' wide rectangles  
  > "These are defined by rectangular regions 3$''$ wide running length-wise along the P.A. of each outflow or the filament." (Results)
   - fitting: _not stated_
   - validation: PV diagram used to distinguish ambient filament from outflow  
  > "The ambient nature of the filament is readily apparent in these figures." (Results)
3. **Determine protostar radial velocity**: Peaks of C18O(2-1) and DCN(3-2) spectra toward continuum peak  
  > "We estimate the radial velocity of the C1-Sa protostar from the $\rm{C^{18}O}$(2-1) and DCN(3-2) spectra towards the continuum peak." (Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive outflow mass, momentum, timescale and rates**: Integrate 12CO(2-1) mass and momentum over velocity ranges; dynamical time from 12'' length; inclination corrections  
  > "Assuming the length of all the outflows lobes are $\simeq12\ensuremath{''}\:(60,000\:$AU), the dynamical times" (Results)
   - parameter: Tex = 17 K; i = 60 deg  
  > "assuming $T_{\rm{ex}}=17\:$K, the blue/red lobes have masses" (Results)
   - assumption: Tex=17 K minimizes mass; mass underestimation factor of 3; inclination 60 deg  
  > "Allowing for a mass underestimation factor of 3" (Results)
   - fitting: _not stated_
   - validation: compared with Zhang et al. 2014 Turbulent Core Model predictions  
  > "It is interesting that these estimates are comparable with the observed values of $\dot{p}_w$ from C1-Sa and C1-Sb." (Discussion)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| C1-Sa outflow mass blue/red | 0.50/0.32 | not stated | Msun | 4 | the blue/red lobes have masses $m_w=0.50/0.32\:M_\odot$ |
| C1-Sa outflow momentum blue/red | 3.6/6.6 | not stated | Msun km/s | 4 | $p_w=3.6/6.6\:M_\odot\:$$\rm{km\:s}^{-1}$ |
| C1-Sb outflow mass blue/red | 0.73/0.38 | not stated | Msun | 4 | the blue/red lobes have masses $0.73/0.38\:M_\odot$ |
| C1-Sa total momentum flux (corrected) | ~5.9e-3 | not stated | Msun km/s /yr | 4 | totals for C1-Sa of $\dot{p}_w\sim5.9\times10^{-3}\:M_\odot\:$ |
| C1-Sa 1.3 mm flux | 19.5 | 0.1 | mJy | 1 | / C1-Sa / 28.322093 / 0.067698664 / $19.5\pm0.1$ / |
| C1-Sa vLSR from C18O | 79.01 | 0.12 | km/s | 3 | The $\rm{C^{18}O}$(2-1) spectrum shows a main peak at $+79.01\pm0.12\:$$\rm{km\:s}^{-1}$ |

## Qualitative findings

- C1-Sa drives a narrow, highly collimated, symmetric bipolar outflow extending ~12'' (0.3 pc)  
  > "The outflow is highly-collimated and is seen to extend $\sim12\ensuremath{''}$ ($60,000\:$AU,$\:0.3\:$pc), and is quite symmetric" (Results)

## Claim tuples

- H: C1-S hosts an early-stage massive protostar with ordered outflow | E: ALMA 12CO(2-1), C18O, DCN and 1.3 mm continuum | R: Collimated outflow from continuum peak C1-Sa near the C1-S center with matching velocity; momentum flux ~6e-3 Msun km/s/yr | F: C1-Sa is a good candidate early-stage massive protostar with ordered outflow/accretion | **supported**
- H: C1-Sb is associated with the C1-S core | E: C18O velocity and CO channel maps | R: vLSR 81.36 km/s differs from the core's 79.4 | F: Association uncertain | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Elongated CO filament interpreted as ambient gas rather than a collimated outflow, based on narrow velocity dispersion and lack of gradient  
  > "The ambient nature of the filament is readily apparent in these figures." (Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Outflow properties are lower limits (Tex, inclination, optical depth); blue lobes affected by source overlap  
  > "the absolute values of the above estimates should be viewed as lower limits" (Results)
- Caveat (inferred, ours): Single inclination assumed (60 deg) with a large uncertain correction
- Caveat (inferred, ours): Outflow length assumed 12'' for all lobes
- Caveat (inferred, ours): Sidelobe contamination possible for fainter sources

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration and imaging parameters
- Missing: Mass calculation details
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Project code stated but processing and imaging details are largely absent.
- Rediscovery candidate: no, Imaging and analysis recipe lacks detail.

## Links

- Companion: Tan et al. 2013 (Cycle 0 N2D+ detection of the cores)
- Companion: Kong et al. 2016 (Deuteration of the cores)

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 30,
  "rate": 0.455
 },
 "evidence_ok": true
}
```
