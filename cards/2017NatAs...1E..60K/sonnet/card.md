# The large-scale nebular pattern of a superwind binary in an eccentric orbit

`2017NatAs...1E..60K` | Nature Astronomy 2017 | first author: Kim, Hyosun | arXiv: 1704.00449 | DOI: 10.1038/s41550-017-0060

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: Does the circumstellar spiral-shell pattern of AFGL 3068 seen in ALMA molecular lines (including a bifurcation) require a binary in an eccentric orbit?  
  > "The observations clearly reveal that the dynamics of the mass loss is influenced by the presence of an eccentric-orbit binary." (abstract)
- Target **AFGL 3068 (LL Pegasi)**: coordinates _not stated_; z/distance ~3,400 light years  
  > "targeted at AFGL 3068 (LL Pegasi)" (Methods); "corresponding to 10,000 AU at the distance of AFGL 3068 ($\sim$ 3,400 light years)" (main text); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00179.S
- bands: Band 6  
  > "which fall in the ALMA Band 6 frequency coverage" (Methods)
- frequencies and spectral setup: Four SPWs at ~230.5, 232.0, 220.4, 217.8 GHz; 117.2 MHz SPWs for 12CO and 13CO at 488.281 kHz (~0.7 km/s); two 1875 MHz continuum SPWs at 976.563 kHz (~1.3 km/s)  
  > "The correlator was configured with four spectral windows (SPWs) centered at $\sim$ 230.5, 232.0, 220.4, and 217.8 GHz" (Methods)
- continuum bandwidth: _not stated_
- arrays: 12-m array, 34 antennas on average, 5-field Nyquist mosaic  
  > "The 5-field Nyquist-sampled mosaic observations used the 12-m array with 34 antennas on average." (Methods)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Line images ~0.26x0.23 arcsec; continuum 0.35x0.34 arcsec  
  > "The resulting synthesized beam sizes for all molecular line images are about" (Methods)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~1.8 hours on source; ~3.5 hours total  
  > "The integration time on AFGL 3068 was $\sim1.8$ hours" (Methods)
- observing dates: August 29, August 31, September 29, 2015 (Cycle 2)  
  > "was carried out with ALMA on August 29, August 31, and September 29 of 2015 during its Cycle 2" (Methods)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: HC3N J=24-23 (not stated)
- Other facility **HST**: Dust-scattered light image at 0.6 micron compared with the ALMA maps  
  > "The emission maps integrated over the molecular lines are well correlated with the HST image" (main text)
- Other facility **Keck**: Adaptive-optics NIR imaging showing two point sources, projected separation 109 AU  
  > "revealing a projected binary separation of 109 AU" (main text)
- External data: Stellar masses (3.5 and 3.1 Msun) and mean separation (166 AU) from circular-orbit parameter-space analysis  
  > "we adopt the stellar masses and their mean separation derived from a parameter space analysis under a circular orbit assumption" (Hydrodynamic model) [from (cite: kim12b)]
- Simulation/model as data: FLASH4.3 AMR hydrodynamic model of an eccentric binary (e=0.8, inclination 50 deg) compared with observed channel maps  
  > "The hydrodynamic simulation is performed using the FLASH4.3 code with an adaptive mesh refinement" (Hydrodynamic model)

## Processing

### Calibration

- pipeline or manual: Manual calibration in CASA  
  > "Manual calibration was performed on the data according to the standard procedures of ALMA" (Methods)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres (Aug 29, 31); 3c454.3 (Sep 29)  
  > "3c454.3 was the flux calibrator" (Methods)
- flux scale uncertainty: _not stated_
- self calibration: Two cycles against continuum image, phase then phase-amplitude; noise improved 20%  
  > "Two cycles of self-calibration against the continuum image were then applied to derive new phase and phase-amplitude gains." (Methods)

### Imaging

- task: CLEAN  
  > "We defined individual cleaning boxes on a channel by channel basis in the CLEAN task" (Methods)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "with a robust weighting of 0.5" (Methods)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Manual cleaning boxes per channel  
  > "We defined individual cleaning boxes on a channel by channel basis" (Methods)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 0.2 mJy/beam in the continuum  
  > "obtaining a final r.m.s. noise of 0.2 mJy per beam in the continuum map" (Methods)

### Inherited from earlier work

- Binary parameters (masses, separation) taken from circular-orbit analysis  
  > "we adopt the stellar masses and their mean separation derived from a parameter space analysis under a circular orbit assumption" (Hydrodynamic model) [from (cite: kim12b)]
- Self-calibration procedure  
  > "The dataset was further self-calibrated by employing the following procedure" (Methods) [from (cite: pea84)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Line-free channels used for the continuum
- Self-calibration solution intervals
- Image size, cell size, clean threshold
- Continuum subtraction method for lines
- Model parameter values (wind mass-loss rate, temperature, resolution) for FLASH
- How model density was converted to the velocity channels for comparison
- Quantitative fit criteria for model matching
- Coordinates of the target

## Analysis recipe

1. **Image self-calibrated line cubes**: Self-calibrate on continuum, apply gains to lines, CLEAN with channel-by-channel boxes  
  > "The resulting calibration gains from self-calibration were applied to the line data for further imaging." (Methods)
   - software: CASA
   - parameter: robust = 0.5  
  > "with a robust weighting of 0.5" (Methods)
   - fitting: _not stated_
   - validation: _not stated_
2. **Estimate orbital period from spiral slope**: Archimedean spiral r=A+B*phi, slope measured in angle-radius plot, gives orbital period  
  > "a slope ${\rm d}r/{\rm d}\phi=9\mbox{$^{\prime\prime}$}/8\pi$ characterizes the spiral pattern of AFGL 3068 observed by ALMA to first order" (Orbital period)
   - assumption: Circular orbit approximation; constant wind speed 14 km/s  
  > "Assuming a circular orbit and a constant inherent speed of the wind, it yields an Archimedean spiral" (Orbital period)
   - fitting: _not stated_
   - validation: _not stated_
3. **Compare with eccentric binary hydrodynamic model**: FLASH simulation with e=0.8; density cube oriented by four angles by visual alignment of bifurcations, elongation and undulations  
  > "we orient the modeled density cube with four angular parameters described above" (Hydrodynamic model)
   - software: FLASH4.3
   - parameter: 3.5 and 3.1 Msun, separation 166 AU, e=0.8, inclination 50 deg, periastron PA 40 deg  
  > "a mean orbital separation of 166 AU, and an eccentricity $e=0.8$" (Hydrodynamic model)
   - assumption: Wind accelerated to 14 km/s  
  > "The wind is quickly accelerated to reach 14 km s${}^{-1}$" (Hydrodynamic model)
   - fitting: No formal fit; parameter study deferred  
  > "We defer a parameter study for a thorough modeling to a future investigation." (Hydrodynamic model)
   - validation: Visual match of bifurcations between model and observed systemic-velocity map  
  > "The model of a binary system in an eccentric orbit generates bifurcations that are coincident with those present in the observed images." (main text)

## Software

- **CASA** : Calibration, self-calibration, imaging  
  > "using the Common Astronomy Software Applications (CASA) package" (Methods)
- **FLASH** 4.3: Hydrodynamic simulation of eccentric binary wind  
  > "The hydrodynamic simulation is performed using the FLASH4.3 code" (Hydrodynamic model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spiral radius detected | 10 | not stated | arcsec (~10,000 AU) | 1 | A spiral pattern is definitively detected over a radius ($r$) of 10$^{\prime\prime}$ |
| Orbital period | ~800 years (d/kpc)(Vwind/14 km/s)^-1 | not stated | yr | 2 | $T_{\rm orb}\sim$ 800 years ($d$/kpc) ($V_{\rm wind}$/14 km s${}^{-1}$)$^{-1}$ |
| Eccentricity of model | 0.8 | not stated | dimensionless | 3 | The angle between the two branches indicates that the eccentricity is significantly larger than 0.5 with a good match to the $e\sim0.8$ model. |
| Orbital inclination (model) | 50 | not stated | deg | 3 | the orbit in the model displayed in this paper is inclined by 50$^\circ$ from the plane of the sky |
| Continuum rms | 0.2 | not stated | mJy/beam | 1 | obtaining a final r.m.s. noise of 0.2 mJy per beam in the continuum map |

## Qualitative findings

- Previously unrecognized bifurcation in the spiral pattern, not producible by circular-orbit models  
  > "The most exceptional feature of the images presented here is the previously unrecognized bifurcation in the spiral pattern" (main text)

## Claim tuples

- H: Is the bifurcation explained by an eccentric binary? | E: Compared ALMA systemic-velocity map with FLASH eccentric-orbit model (e=0.8) | R: Model bifurcations coincide with observed ones | F: AFGL 3068 hosts a binary in a highly eccentric orbit | **supported**
- H: Do dust and gas trace the same spiral, and does gas reveal inner windings? | E: Compared ALMA line maps with the HST image | R: Well correlated; innermost winding (r<3 arcsec) seen only in molecular lines | F: Dust and gas trace the same spiral | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Circular-orbit models, spiral-arm width growth, and periodic mass-loss models rejected as explanations for the bifurcation  
  > "However, there is no inclination angle at which a bifurcation is produced." (main text)
- How they decided it was enough: _not stated_
- Limitation (authors): Thorough parameter study deferred  
  > "We defer a parameter study for a thorough modeling to a future investigation." (Hydrodynamic model)
- Caveat (inferred, ours): Model orientation tuned by eye with no goodness-of-fit or uncertainties
- Caveat (inferred, ours): Only one eccentricity (0.8) and one set of masses/separation tested
- Caveat (inferred, ours): Eccentricity range allowed (>0.5) not quantified
- Caveat (inferred, ours): Period depends on assumed distance

## Reproducibility

- Data public (paper): Data available from the corresponding author on request; ALMA data cited by project code  
  > "are available from the corresponding author upon reasonable request." (Data availability)
- Products in archive: _not stated_
- Missing: CASA version and scripts
- Missing: Hydrodynamic model input parameters and outputs
- Missing: Comparison procedure between model and data
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 3/5, Public ALMA data and clear imaging basics, but model comparison is qualitative and the simulation setup is incomplete.
- Rediscovery candidate: no, Main result is a qualitative model comparison, not a numeric recipe.

## Links

- Method: (cite: kim12b) (Circular-orbit binary parameters for AFGL 3068)
- Method: (cite: pea84) (Self-calibration procedure)
- Companion: (cite: kim13) (Spiral-shell models with inclined orbits)

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
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
  "facts": 67,
  "stated": 36,
  "rate": 0.537
 },
 "evidence_ok": true
}
```
