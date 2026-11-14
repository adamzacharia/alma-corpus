# Anatomy of the internal bow shocks in the IRAS 04166+2706 protostellar jet

`2017A&A...597A.119T` | Astronomy and Astrophysics 2017 | first author: Tafalla, M. | arXiv: 1610.01614 | DOI: 10.1051/0004-6361/201629493

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: How are the jet and the wide-angle outflow related in IRAS 04166+2706; do the jet emission peaks represent internal bow shocks that eject gas laterally?  
  > "We study the relation between the jet and the outflow in the IRAS 04166+2706 protostar." (abstract)
- Target **IRAS 04166+2706 jet (B6 and R6 EHV peaks)**: coordinates IRAS 04166 at RA(J2000)=4h19m42.5s, Dec=+27d13'36''; fields offset (26.5'',46.5'') and (-28.8'',-48.9'')  
  > "These fields are located at offsets ($26.5\ensuremath{''}$, $46.5\ensuremath{''}$) and ($-28.8\ensuremath{''}$, $-48.9\ensuremath{''}$) with respect to the position of IRAS 04166" (2 Observations); "in the Taurus molecular cloud at an estimated distance of 140 pc (cite: eli78; tor07)" (1 Introduction); z/distance 140 pc  
  > "These fields are located at offsets ($26.5\ensuremath{''}$, $46.5\ensuremath{''}$) and ($-28.8\ensuremath{''}$, $-48.9\ensuremath{''}$) with respect to the position of IRAS 04166" (2 Observations); "in the Taurus molecular cloud at an estimated distance of 140 pc (cite: eli78; tor07)" (1 Introduction); distance from Elias 1978; Torres et al. 2007  
  > "These fields are located at offsets ($26.5\ensuremath{''}$, $46.5\ensuremath{''}$) and ($-28.8\ensuremath{''}$, $-48.9\ensuremath{''}$) with respect to the position of IRAS 04166" (2 Observations); "in the Taurus molecular cloud at an estimated distance of 140 pc (cite: eli78; tor07)" (1 Introduction)

## Data provenance

- ALMA projects: 2012.1.00304.S
- bands: Band 6, tuned to 230.5 GHz  
  > "The Band 6 receivers were tuned to a frequency of 230.5 GHz, to observe simultaneously CO(J=2–1), SiO(J=5–4), and SO(J$_{\mathrm N}$=6$_5$–5$_4$)." (2 Observations)
- frequencies and spectral setup: velocity resolution ~0.32 km/s  
  > "The correlator was configured to provide a velocity resolution of approximately 0.32 km s$^{-1}$." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C32-2, 12 m only, no Morita Array  
  > "The telescope array was in its C32-2 configuration" (2 Observations)
- baselines: ~15 to 330 m  
  > "the baselines between its 12 m antennas ranged approximately between 15 and 330 m" (2 Observations)
- angular resolution: 1.5''x1.1'' (CO 2-1); 1.6''x1.2'' (SiO 5-4)  
  > "resulted in a synthesized beam of $1.5\ensuremath{''} \times 1.1\ensuremath{''}$ for the higher frequency CO(2–1) line" (2 Observations)
- max recoverable scale: Not given; missing flux at large scales as no compact array; primary beam 25'' FWHM  
  > "they may be missing flux from the largest spatial scales" (3 Results)
- sensitivity: 2.5 mJy/beam (35 mK) per 0.5 km/s channel  
  > "The typical rms noise level in the maps is 2.5 mJ beam$^{-1}$ (= 35 mK) per 0.5 km s$^{-1}$ channel." (2 Observations)
- time on source: two 1.3-hour scheduling blocks  
  > "They were observed jointly during two 1.3-hour ALMA scheduling blocks in December 2014" (2 Observations)
- observing dates: December 2014  
  > "two 1.3-hour ALMA scheduling blocks in December 2014" (2 Observations)
- pi or archival as stated: Cycle 1 project, PI Yu-Nung Su  
  > "Early Science Cycle 1 project 2012.1.00304.S (PI Yu-Nung Su)" (2 Observations)
- Line: CO J=2-1 (230.5 GHz)
- Line: SiO J=5-4 (217.1 GHz)
- Line: SO J_N=6_5-5_4 (not stated)
- Other facility **IRAM 30 m**: single-dish CO(2-1) spectra from Tafalla et al. 2004 to check missing flux  
  > "we use the spectra from (cite: taf04) (T04 hereafter), who mapped the CO(2–1) emission of the IRAS 04166 outflow with the IRAM 30 m single-dish telescope" (3 Results)
- Other facility **IRAM PdBI**: EHV CO(2-1) image used as the context map (SG09)  
  > "colored image of the EHV CO(2–1) emission obtained with the IRAM PdBI" (3 Results)
- External data: IRAM 30 m CO(2-1) spectra, ambient velocity 6.7 km/s, gas temperatures 7-20 K, kinematic age 3000 yr  
  > "we use the spectra from (cite: taf04) (T04 hereafter)" (3 Results) [from Tafalla et al. 2004 (cite: taf04)]
- External data: Jet direction 30.4±0.2 deg, B6/R6 ages ~900 yr, masses 8.8e-5 and 5.9e-5 Msun  
  > "which was determined as $30.4\ensuremath{^\circ} \pm 0.2\ensuremath{^\circ}$ by SG09" (3.2) [from Santiago-García et al. 2009 (cite: san09)]
- External data: CO abundance 8.5e-5  
  > "We also assume a standard CO abundance of $8.5 \times 10^{-5}$ (cite: fre82)." (4) [from Frerking et al. 1982 (cite: fre82)]
- External data: Core mass 1.0-1.5 Msun  
  > "Since (cite: shi00) and T04 estimated the mass of the core at between 1.0 and 1.5 M$_\ensuremath{\odot}$" (5) [from Shirley et al. 2000 (cite: shi00)]

## Processing

### Calibration

- pipeline or manual: observatory pipeline in CASA  
  > "The resulting visibility data were reduced using the observatory pipeline in CASA version 4.3.1" (2 Observations)
- casa version: CASA 4.3.1  
  > "observatory pipeline in CASA version 4.3.1 (cite: mac07)" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800 (also phase calibrator); bandpass J0423-0120  
  > "The same continuum source was used for flux calibration, and J0423-0120 was used to calibrate the bandpass." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA for synthesis and preliminary cleaning; final cleaning with GILDAS MAPPING  
  > "Final cleaning of the maps was carried out using the MAPPING program of the GILDAS software" (2 Observations)
- deconvolver: _not stated_
- weighting robust: briggs, robust = 0.5  
  > "Imaging was carried out using briggs weighting with a robust parameter of 0.5" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: not applied to the maps shown  
  > "Since we have not corrected the maps in Fig. 3 for the attenuation of the primary beam of the antennas" (3.1)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.5''x1.1'' CO; 1.6''x1.2'' SiO  
  > "synthesized beam of $1.5\ensuremath{''} \times 1.1\ensuremath{''}$ for the higher frequency CO(2–1) line" (2 Observations)
- final rms: 2.5 mJy/beam per 0.5 km/s channel  
  > "The typical rms noise level in the maps is 2.5 mJ beam$^{-1}$ (= 35 mK) per 0.5 km s$^{-1}$ channel." (2 Observations)

### Inherited from earlier work

- Jet axis direction, field positions, B6/R6 labelling and ages  
  > "The fields were chosen to cover a pair of emission peaks labeled B6 and R6 in the SG09 notation" (3 Results) [from SG09 (cite: san09)]
- Ray-tracing LTE radiative transfer program (modified version)  
  > "using a modified version of the ray-tracing program presented in (cite: taf97)" (4) [from (cite: taf97)]

### Not stated but needed to reproduce (our reading)

- Whether CASA cleaning masks and thresholds were used, and the CLEAN parameters in MAPPING
- Line-free channels and continuum subtraction
- Image size and cell size
- Exact moment-map clipping thresholds
- Modified ray-tracing code is not available; model grid and fitting procedure (trial and error) not defined
- How the ellipse size/PA was measured (by eye)

## Analysis recipe

1. **Check missing flux against single-dish**: Synthesize ALMA spectra at 11'' resolution and compare to IRAM 30 m CO(2-1) at the two nearest positions  
  > "we compared these positions with spectra synthesized from the ALMA data assuming the same position and angular resolution as the 30 m observations ($11''$ FWHM)" (3 Results)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: Intensity agreement within about 30% at line peak in the EHV regime  
  > "the intensity agreement between the two spectra is within about 30% at the line peak" (3 Results)
2. **Integrated and channel maps of EHV gas**: Integrate over 20 km/s EHV range centred at |V0±37.5| km/s; six 3.33 km/s channels after correcting for the 37.5 km/s offset  
  > "The EHV regime is defined as the 20 km s$^{-1}$-wide velocity range that is centered on $|V_0\pm 37.5\mathrm{~km~s}^{-1}|$" (3.1)
   - parameter: V0 = 6.7 km/s  
  > "where $V_0$ is the LSR velocity of the ambient cloud (6.7 km s$^{-1}$, T04)" (3.1)
   - fitting: Gaussian fit to spectra for the 37.5 km/s offset  
  > "We estimated the value of this offset using a a Gaussian fit to the spectra, deriving a velocity of 37.5 km s$^{-1}$" (3.2)
   - validation: _not stated_
3. **Ellipse geometry and jet inclination**: Estimate ellipse sizes and PA from extreme-velocity maps; aspect ratio gives inclination of circular disk, deprojects jet velocity  
  > "the aspect ratio of the ellipse is an indicator of the inclination angle of the disk with respect to the plane of the sky" (3.2)
   - assumption: Gas lies in circular disks perpendicular to the jet axis  
  > "the true distribution of the gas is in circular disks that are perpendicular to the jet axis" (3.2)
   - fitting: by-eye estimates  
  > "These values are very similar, especially considering our simple fitting method, so we average them as $52\ensuremath{^\circ}$, and assume a probable uncertainty of less than 10%." (Velocity structure: Evidence of expanding gas disks)
   - validation: the two fields give similar inclinations (53.1 and 50.5 deg)  
  > "these ratios correspond to jet inclination angles of $53.1\ensuremath{^\circ}$ and $50.5\ensuremath{^\circ}$" (3.2)
4. **First-moment maps and curvature**: CO(2-1) moment-1 maps to show iso-velocity contour curvature  
  > "maps of the first moment (velocity centroid) of the CO(2–1) emission" (3.3)
   - fitting: _not stated_
   - validation: _not stated_
5. **Geometrical radiative-transfer model**: Parabolic shell z=0.02 r^2 truncated at r=11'', thickness 1.5'', LTE ray tracing with linear expansion velocity 0-13 km/s  
  > "the curvature of the parabola must be very mild (described as $z = 0.02 r^2$), and the shell must be truncated when its outer cylindrical radius $r$ reaches a size of $11''$" (4)
   - software: modified ray-tracing program of Tafalla et al. 1997, Shape
   - parameter: inner half constant density 0.8e4 cm^-3, outer half inverse square-root density  
  > "we assumed that the inner half of the shell has a constant density of a $0.8\times 10^4$ cm$^{-3}$" (4)
   - assumption: isothermal 10 K; CO abundance 8.5e-5; optically thin; same structure in both fields  
  > "we assume that the gas in the shells has a constant temperature of 10 K" (4)
   - fitting: trial and error  
  > "After some trial and error, we found a best fit using a linear velocity field" (4)
   - validation: Comparison with channel, integrated and moment-1 maps; constant-velocity model (11 km/s) rejected  
  > "Since the ALMA data are inconsistent with this pattern, we can safely exclude a constant velocity of expansion." (8)
6. **Mass and momentum budget**: Integrate model density to get shell mass; forward and sideways momentum; total lateral momentum over outflow lifetime vs impulse to open cavity  
  > "we integrate the model density profile of the shell to estimate the amount of mass in each EHV peak" (5)
   - assumption: Flat disk; 150 yr between ejections; age 3000 yr; 20 ejections; cavity opening angle 40 deg = 3% of core volume; sound speed 0.2 km/s  
  > "we estimate that there have been a total of 20 EHV ejections (in each direction) over the history of the IRAS 04166 outflow" (5)
   - fitting: _not stated_
   - validation: Shell mass consistent with SG09 direct CO estimates  
  > "This value is in good agreement with the mass estimates for the B6 and R6 peaks made by SG09" (5)

## Software

- **CASA** 4.3.1: pipeline calibration, image synthesis, preliminary cleaning  
  > "which was used for calibration, image synthesis, and preliminary cleaning" (2 Observations)
- **GILDAS MAPPING** : final cleaning of maps  
  > "Final cleaning of the maps was carried out using the MAPPING program of the GILDAS software" (2 Observations)
- **Shape / Shapemol** : initial modeling and two figures  
  > "which were used for the initial modeling of the data and in two figures" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| EHV radial velocity offset | 37.5 | not stated | km/s | 2 | deriving a velocity of 37.5 km s$^{-1}$ for both the blue and red EHV components |
| Ellipse size north / south | 20''x12'' / 22''x14'' | not stated | arcsec | 3 | we estimate an ellipse size of about $20''\times 12''$ (major times minor axis), while for the southern field we estimate a slightly larger size of $22''\times 14''$ |
| Jet inclination to plane of sky | 52 | <10% | deg | 3 | so we average them as $52\ensuremath{^\circ}$, and assume a probable uncertainty of less than 10% |
| Deprojected jet velocity | 61 | ~10% | km/s | 3 | obtain a true jet velocity of about 61 km s$^{-1}$, again with an uncertainty of about 10% |
| Shell mass per field | 8.6e-5 | not stated | Msun | 6 | we derive a shell mass of $8.6 \times 10^{-5}$ M$_\ensuremath{\odot}$ |
| Forward momentum per shell | 5.2e-3 | not stated | Msun km/s | 6 | the linear momentum of each EHV shell is $5.2 \times 10^{-3}$ M$_\ensuremath{\odot}$ km s$^{-1}$ |
| Sideways momentum per shell | 7.1e-4 | not stated | Msun km/s | 6 | the sideways momentum of the EHV shell is $7.1 \times 10^{-4}$ M$_\ensuremath{\odot}$ km s$^{-1}$ |
| Sideways/forward momentum ratio | 0.14 | not stated | dimensionless | 6 | we find a small ratio of 0.14 |
| Time since single shock event | 550 | not stated | yr | 5 | The result is approximately 550 yr |
| Total lateral momentum per outflow direction | 1.4e-2 | not stated | Msun km/s | 6 | about $1.4 \times 10^{-2}$ M$_\ensuremath{\odot}$ km s$^{-1}$ in each outflow direction |
| Impulse needed to open cavity | 8e-3 | not stated | Msun km/s | 6 | the estimated impulse would be $8 \times 10^{-3}$ M$_\ensuremath{\odot}$ km s$^{-1}$ for each outflow cavity |

## Qualitative findings

- SO(6_5-5_4) not detected inside the elliptical regions; SiO only barely detected  
  > "was not detected inside the elliptical regions of either ALMA field, even when using narrow channel maps" (3.1)

## Claim tuples

- H: EHV peaks are gas ejected laterally in internal bow shocks | E: Channel and moment maps of CO(2-1) in two fields plus geometric model | R: Elliptical regions with minor axis along the jet, SW-to-NE velocity sweep, opposite curvature in the two fields | F: Emitting gas is in expanding, slightly curved disks perpendicular to the jet | **supported**
- H: Expansion velocity is constant vs. increasing with distance from axis | E: Compare constant 11 km/s model against linear 0-13 km/s model | R: Constant model gives wedge patterns inconsistent with the data | F: Velocity must increase linearly away from the axis | **supported**
- H: Lateral ejection can affect the outflow and core | E: Momentum estimates from the model | R: Sideways/forward momentum 0.14; accumulated lateral momentum is almost twice the impulse needed for the cavity | F: Lateral ejection potentially impacts outflow cavity formation | **partially**

## Reasoning

- Why this data: ALMA sensitivity enables 2D velocity structure of weak jet emission  
  > "has now made it possible to study the 2D velocity structure of the relatively weak jet emission in detail" (1 Introduction)
- Why this method: _not stated_
- Alternative: Constant expansion velocity model rejected  
  > "we can safely exclude a constant velocity of expansion" (8)
- How they decided it was enough: _not stated_
- Limitation (authors): No compact-array data; low-velocity outflow emission mostly missing, analysis restricted to the EHV regime  
  > "For this reason, we do not study the slow outflow component and our analysis is restricted to the EHV regime." (3 Results)
- Limitation (authors): Model emission more concentrated than observed; simplified velocity field  
  > "the model emission is significantly more concentrated than observed with ALMA" (4)
- Caveat (inferred, ours): Model parameters tuned by eye with no uncertainties or goodness of fit
- Caveat (inferred, ours): Momentum budget relies on many assumptions (ejection spacing, age, core mass)
- Caveat (inferred, ours): Ellipse parameters estimated by eye
- Caveat (inferred, ours): Primary-beam-uncorrected maps

## Reproducibility

- Data public (paper): ALMA data cite project code; archive ADS/JAO.ALMA#2012.1.00304.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00304.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Ray-tracing code modified version not released
- Missing: Clean parameters, masks, image/cell size
- Missing: Moment-map thresholds
- Data volume (inferred): ~10-30 GB raw (two 1.3 h SBs, Band 6)
- Score (inferred): 3/5, Data public and basic imaging stated, but model fitting is by eye with unreleased code and many unstated imaging details.
- Rediscovery candidate: no, Key results depend on by-eye geometry and a custom modeling code; imaging recipe incomplete.

## Links

- Method: Tafalla et al. 1997 (cite: taf97) (Ray-tracing radiative transfer code)
- Companion: Santiago-García et al. 2009 (cite: san09) (Prior PdBI study defining the EHV peaks)
- Companion: Wang et al. 2014 (cite: wan14) (Prior interferometric study of the jet)
- Companion: Tafalla et al. 2004 (cite: taf04) (IRAM 30 m CO maps of the outflow)

## Checks

```json
{
 "quotes": 79,
 "quotes_ok": 79,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 57,
  "rate": 0.704
 },
 "evidence_ok": true
}
```
