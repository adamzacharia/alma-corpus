# ALMA detects a radial disk wind in DG Tauri

`2018A&A...620L...1G` | Astronomy and Astrophysics 2018 | first author: Güdel, M. | arXiv: 1810.12251 | DOI: 10.1051/0004-6361/201834271

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Map the flow pattern of molecular gas near DG Tau and its disk to find outflows/winds related to the disk and jet.  
  > "We aim to use the high spatial resolution of the Atacama Large Millimeter/submillimeter Array (ALMA) to map the flow pattern of molecular gas near DG Tau and its disk" (abstract)
- Target **DG Tau**: coordinates _not stated_; z/distance 121.2 (119.1-123.4) pc  
  > "We use a distance to DG Tau of 121.2 (119.1-123.4) pc measured by GAIA" (2 The target: DG Tau); distance from Gaia (Gaia Collaboration 2016, 2018)  
  > "We use a distance to DG Tau of 121.2 (119.1-123.4) pc measured by GAIA" (2 The target: DG Tau)

## Data provenance

- ALMA projects: 2015.1.00722.S
- bands: Band 6  
  > "The observations in band 6 comprise the transitions of $^{12}$CO $J = 2-1$ (230.538 GHz)" (3 Observations)
- frequencies and spectral setup: 117 MHz bandwidth per sideband, 0.122 MHz resolution (~0.159-0.167 km/s)  
  > "The spectral bandwidth was 117 MHz (corresponding to a velocity range of $\sim$152–162 km s$^{-1}$ per sideband), and the spectral resolution was 0.122 MHz" (3 Observations)
- continuum bandwidth: _not stated_
- arrays: 12m antennas, 42 used, Cycle 3  
  > "in Cycle 3 on 24/26 September 2016 using 42 of the 12m antennas" (3 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.21'' x 0.12'' (25 au x 15 au)  
  > "providing an angular resolution (beam size) of $\sim$0$\ensuremath{''} 21\times 0.12\ensuremath{''}$ (25 au $\times$ 15 au)" (3 Observations)
- max recoverable scale: _not stated_
- sensitivity: 3.8, 4.3, 3.1 mJy/beam for 12CO, 13CO, C18O  
  > "Typical background noise levels were 3.8, 4.3, and 3.1 mJy/beam for $^{12}$CO, $^{13}$CO, and C$^{18}$O, respectively." (3 Observations)
- time on source: 1.95 h  
  > "The on-source time amounted to 1.95 h." (3 Observations)
- observing dates: 24/26 September 2016  
  > "in Cycle 3 on 24/26 September 2016" (3 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- Line: 13CO J=2-1 (220.399 GHz)
- Line: C18O J=2-1 (219.560 GHz)
- Line: SiO J=5-4 (217.105 GHz)
- Other facility **Gaia**: Distance to DG Tau  
  > "We use a distance to DG Tau of 121.2 (119.1-123.4) pc measured by GAIA" (2 The target: DG Tau)
- External data: Disk inclination of 38 deg  
  > "adopting a disk inclination of $i = 38^{\circ}$ against the line of sight (cite: eisloeffel98)" (5 Discussion) [from (cite: eisloeffel98)]
- External data: Thermochemical disk model temperature structure of DG Tau  
  > "We used the resulting temperature structure from a thermochemical disk model of DG Tau published by (cite: podio13)" (5 Discussion) [from (cite: podio13)]
- External data: Jet position angle ~222 deg  
  > "the approaching jet points toward a position angle of $\sim$222 deg, that is, to the southwest (SW), (cite: lavalley97)" (4 Results) [from (cite: lavalley97)]

## Processing

### Calibration

- pipeline or manual: standard CASA procedures  
  > "We applied standard procedures provided by the CASA software version 4.7.0-1 for data reduction, calibration, and data extraction." (3 Observations)
- casa version: CASA 4.7.0-1  
  > "We applied standard procedures provided by the CASA software version 4.7.0-1 for data reduction, calibration, and data extraction." (3 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: line data continuum-subtracted and cleaned per CASA Cookbook prescriptions  
  > "The line data presented here were continuum-subtracted and cleaned following prescriptions in the CASA User Reference & Cookbook, public release 2017." (3 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Continuum subtraction and cleaning following CASA Cookbook  
  > "continuum-subtracted and cleaned following prescriptions in the CASA User Reference & Cookbook, public release 2017." (3 Observations) [from CASA User Reference & Cookbook, public release 2017]
- Inclination of 38 deg adopted from earlier work  
  > "a symmetric disk compatible with an inclination of $\sim 38^{\circ}$ (cite: eisloeffel98)" (4 Results) [from (cite: eisloeffel98)]

### Not stated but needed to reproduce (our reading)

- Weighting/robust, cell and image size, clean threshold and masks
- Line-free channels for continuum subtraction
- Flux calibrator choice and flux scale uncertainty
- Moment-map thresholds and clipping
- Continuum image used for contours
- Procedure for estimating r'_proj and radial velocities from maps (done by eye)

## Analysis recipe

1. **Calibrate and image CO line cubes**: Standard CASA calibration, continuum subtraction and cleaning  
  > "The line data presented here were continuum-subtracted and cleaned following prescriptions in the CASA User Reference & Cookbook, public release 2017." (3 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Moment and PV maps of disk kinematics**: First-moment maps and PV diagram along major axis compared to Kepler rotation  
  > "agrees with a Kepler rotation profile for a star of 0.5 solar masses" (4 Results)
   - parameter: v_sys ≈ 5.5 km/s  
  > "These figures indicate a systemic velocity relative to lsr of $v_{\rm sys}\approx 5.5$ km s$^{-1}$" (4 Results)
   - assumption: Inclination 38 deg  
  > "adopting a disk inclination of $i = 38^{\circ}$ against the line of sight (cite: eisloeffel98)" (5 Discussion)
   - fitting: _not stated_
   - validation: _not stated_
3. **Geometric estimate of wind height, angle and velocity**: Projection geometry using arc radius and radial velocity ratio at two azimuths to solve for flow angle phi and velocity v  
  > "the ratio $v_{\rm rad}(\alpha_2)/v_{\rm rad}(\alpha_1) = 2/3$ determines, through Eq. [\[proj\]](#proj) for the numerator and denominator, the value of $\varphi$." (5 Discussion)
   - fitting: _not stated_
   - validation: _not stated_
4. **Test photoevaporation origin**: Compare escape-temperature layer with thermochemical model temperature structure  
  > "We then determined the layer at which the escape temperature is reached using DG Tau’s high-energy luminosity" (5 Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0-1: Data reduction, calibration, continuum subtraction, cleaning  
  > "We applied standard procedures provided by the CASA software version 4.7.0-1 for data reduction, calibration, and data extraction." (3 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Wind flow angle from vertical | ≈25 | not stated | deg | 3 | We obtain $\varphi \approx 25^{\circ}$. |
| Wind full velocity | -3.1 | not stated | km/s | 3 | $v = v_{\rm rad}(\alpha_1)/\cos(\varphi-i) \approx  -3/\cos(-13^{\circ}) = -3.1$ km s$^{-1}$ |
| Height ratio z/r | 0.03-0.15 | not stated | dimensionless | 3 | we find $z/r = 0.03-0.15$ |
| Distance of fast flow from center along major axis | 0.45 | 0.12 | arcsec | 3 | is $\approx$$0.45\ensuremath{''}\pm 0.12\ensuremath{''}$ |
| Systemic velocity (lsr) | ≈5.5 | not stated | km/s | 2 | $v_{\rm sys}\approx 5.5$ km s$^{-1}$ |

## Qualitative findings

- Keplerian disk emission in 12CO is asymmetric, absent in the NE half, attributed to absorption  
  > "The emission is almost completely absent in the NE half of the disk (which is closer to the observer)." (5 Discussion)
- Strongly redshifted arc SW of disk possibly an accretion flow from the envelope  
  > "We speculate that this is an accretion flow from the remnant envelope in front of the disk" (5 Discussion)

## Claim tuples

- H: Is there a disk-related molecular wind component beyond the Keplerian disk and the jet-related flows? | E: 12CO, 13CO, C18O 2-1 first-moment maps and geometric projection analysis | R: Blueshifted arc at v≈-3 km/s, z/r 0.03-0.15, flow angle ≈25 deg, v≈3.1 km/s | F: A new radial wind component exists close to the disk surface, extending the onion-like velocity structure | **supported**
- H: Is the wind photoevaporative? | E: Compare escape-temperature layer with a thermochemical model | R: Escape predicted at r=60-70 au, significantly above the molecular layer | F: Possibly related to photoevaporation but a dedicated model is needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Flaring index of the relevant layer is unknown, making quantitative estimates challenging  
  > "The flaring index of the relevant layer (CO and/or dust) is not known, making a quantitative estimate challenging" (5 Discussion)
- Caveat (inferred, ours): Geometry values read by eye from maps without uncertainties
- Caveat (inferred, ours): Absorption by foreground gas confuses the interpretation
- Caveat (inferred, ours): Single-epoch observation, simple model with a single flow angle

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Uncertainties on geometric estimates
- Missing: Moment map settings
- Data volume (inferred): ~50-100 GB raw for one 12m EB set
- Score (inferred): 3/5, Public data and simple geometry, but imaging parameters and readings from maps are not specified.
- Rediscovery candidate: no, Imaging recipe is incomplete and key results rely on by-eye readings of maps.

## Links


## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
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
  "stated": 29,
  "rate": 0.433
 },
 "evidence_ok": true
}
```
