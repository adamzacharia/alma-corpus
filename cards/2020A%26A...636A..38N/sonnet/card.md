# Episodic accretion constrained by a rich cluster of outflows

`2020A&A...636A..38N` | Astronomy and Astrophysics 2020 | first author: Nony, T. | arXiv: 2002.05720 | DOI: 10.1051/0004-6361/201937046

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: How many protostellar outflows does W43-MM1 host, how does the environment affect them, and what do PV diagrams of knots say about episodic ejection and accretion?  
  > "to search for protostellar outflows, evaluate the influence that the environment has on these outflows’ characteristics and put constraints on outflow variability in W43-MM1." (abstract)
- Target **W43-MM1**: coordinates _not stated_; z/distance 5.5 kpc  
  > "It is located at 5.5 kpc from the Sun (cite: zhang14) at the tip of the Galactic bar (cite: nguyen11b)." (Introduction); distance from zhang14 (Zhang et al. 2014)  
  > "It is located at 5.5 kpc from the Sun (cite: zhang14) at the tip of the Galactic bar (cite: nguyen11b)." (Introduction)

## Data provenance

- ALMA projects: 2013.1.01365.S
- bands: _not stated_
- frequencies and spectral setup: four line SPWs: SiO(5-4) 217.033 GHz, O13CS(18-17) 218.125, CO(2-1) 230.462, 13CS(5-4) 231.144 GHz; 0.25-1.3 km/s resolution  
  > "| CO(2-1)           | 230.462         | 469       | 0.46                          | 1.3                           | 2.3    |   |" (Table 1)
- continuum bandwidth: _not stated_
- arrays: ALMA 12 m and 7 m (ACA)  
  > "with ALMA 12 m and 7 m (ACA) arrays and baselines ranging from 7.6 m to 1045 m" (2 Observations)
- configurations: _not stated_
- baselines: 7.6 m to 1045 m  
  > "baselines ranging from 7.6 m to 1045 m" (2 Observations)
- angular resolution: CO cube ~0.46''; continuum 0.44'' (12 m) and 5.3'' (7 m)  
  > "The 1.3 mm continuum images themselves have $0.44\ensuremath{''}$ and $5.3\ensuremath{''}$ angular resolutions" (2 Observations)
- max recoverable scale: ~12'' (12 m), ~21'' (ACA)  
  > "the maximum detectable scale is of $\sim 12\ensuremath{''}$ ($\sim 21\ensuremath{''}$ with ACA)" (2 Observations)
- sensitivity: continuum rms ~0.13 mJy/beam (12 m), ~9.1 mJy/beam (7 m)  
  > "$1\sigma$ rms noise levels of $\sim$0.13 mJy beam$^{-1}$ and $\sim$9.1 mJy beam$^{-1}$" (2 Observations)
- time on source: _not stated_
- observing dates: July 2014 to June 2015 (Cycle 2)  
  > "Observations were carried out in Cycle 2 between July 2014 and June 2015" (2 Observations)
- pi or archival as stated: _not stated_
- Line: CO 2-1 (not stated)
- Line: SiO 5-4 (not stated)
- Line: 13CS 5-4 (not stated)
- Line: O13CS 18-17 (not stated)
- Other facility **Herschel**: Column density image (25'' resolution) giving the Av=130 mag background level (from Nguyen Luong 2013)  
  > "we added a Av=130 mag level measured at the outskirt of the W43-MM1 cloud ridge on the *Herschel* column density image, with $25\ensuremath{''}$ resolution" (3.4 Cloud environment crossed by outflow lobes)
- External data: Core catalogue, core masses (1.4-102 Msun) and 1.3 mm continuum at 0.44''  
  > "cores that have been detected at $0.44\ensuremath{''}$ angular resolution (or 2400 AU at 5.5 kpc) in the 1.3 mm continuum image by (cite: motte18b)" (3 Results and analysis) [from (cite: motte18b)]
- External data: Dust temperature 23 K and kappa_1.3mm = 0.01 cm g^-1  
  > "we assumed $T_{\rm dust}=23$ K and $\kappa_{\rm 1.3mm}=0.01\,\rm cm\,g^{-1}$ (cite: motte18b)" (3.4 Cloud environment crossed by outflow lobes) [from (cite: motte18b)]

## Processing

### Calibration

- pipeline or manual: Manual and self-calibration scripts, CASA 4.7  
  > "Data were reduced in CASA 4.7, applying manual and selfcalibration scripts." (2 Observations)
- casa version: CASA 4.7 (reduction)  
  > "Data were reduced in CASA 4.7" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: CLEAN, multiscale with 0, 1, 3, 9, 17 beams (CASA 5.4)  
  > "We ran the CLEAN algorithm with CASA 5.4 using a robust weight of 0.5 and the *multiscale* (with 0, 1, 3, 9 and 17 beams) option" (2 Observations)
- weighting robust: robust = 0.5  
  > "using a robust weight of 0.5" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Lines imaged with merged 12 m + 7 m; continuum imaged with 12 m and 7 m separately  
  > "Line data were imaged using the merged (12 m + 7 m) configurations while the continuum was imaged with the 12 m and 7 m arrays separately." (2 Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Core catalogue and 12 m continuum imaging for core identification  
  > "The 12 m-only data provide the best sensitivity image chosen to identify compact cores (cite: motte18b)" (2 Observations) [from (cite: motte18b)]
- SiO as secondary outflow tracer  
  > "SiO(5-4) was used as a secondary outflow tracer, as in (cite: Nony18)" (3.2 Association with dust cores) [from (cite: Nony18)]

### Not stated but needed to reproduce (our reading)

- Line-free channels / continuum subtraction method for the line cubes
- Cell size, image size, masks and clean thresholds
- Flux calibrators and flux scale uncertainty
- Exact PV extraction axes and widths per jet; knot identification is by eye
- Core coordinates and masses, taken from Motte et al. 2018
- Regression method for L_max vs A_V

## Analysis recipe

1. **Image line cubes and find outflow lobes**: Integrate blue/red wings of CO(2-1) and SiO(5-4), check in velocity cubes, associate lobes with cores  
  > "we discovered several tens of outflow lobes, whose existence was confirmed by investigating the velocity cubes of both CO(2-1) and SiO(5-4) lines" (3.1 Discovery of a rich cluster of outflows)
   - software: CASA
   - parameter: CO integration ranges 42-85 and 111-154 km/s; SiO 43-93 and 103-153 km/s  
  > "$42-85~\ensuremath{\rm km\,s^{-1}}$ and $111-154~\ensuremath{\rm km\,s^{-1}}$ for CO(2-1); $43-93~\ensuremath{\rm km\,s^{-1}}$ and $103-153~\ensuremath{\rm km\,s^{-1}}$ for SiO(5-4)" (3.1 Discovery of a rich cluster of outflows)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure core velocities**: Gaussian fit to 13CS(5-4) (O13CS(18-17) for cores #1, #2, #4) integrated over each core  
  > "We used the velocities of a Gaussian fitted to the $^{13}$CS(5-4) line integrated over the core" (3.2 Association with dust cores)
   - assumption: Undetected cores assigned 95 km/s (SW) and 96 km/s (core #31)  
  > "used $95~\ensuremath{\rm km\,s^{-1}}$ for undetected cores in the south-westernmost part and $96~\ensuremath{\rm km\,s^{-1}}$ for core #31" (3.2 Association with dust cores)
   - fitting: _not stated_
   - validation: V_LSR uncertain by up to 1 km/s  
  > "their velocities at rest, $V_{\rm LSR}$, are estimated to be uncertain by up to 1 km s$^{-1}$" (3.2 Association with dust cores)
3. **Measure lobe lengths and maximum velocities**: Inspect CO(2-1) channel maps at 5 sigma threshold  
  > "we investigated the channel maps of CO(2-1) using a $5\sigma=12.5$ mJy beam$^{-1}$ threshold" (3.3 Main characteristics of outflow lobes)
   - fitting: _not stated_
   - validation: uncertainties up to 2 km/s and 0.2''  
  > "uncertain by up to $2~\ensuremath{\rm km\,s^{-1}}$ (twice the precision of our velocity measurements) and 0.2$\ensuremath{''}$" (3.3 Main characteristics of outflow lobes)
4. **Derive background visual extinction around lobes**: Convert 7 m 1.3 mm continuum to N_H2 and add 130 mag Herschel large-scale level: A_V ≈ 130 mag + 940 mag × I_7m (Jy/beam)  
  > "A_{\rm V} = \left(\frac {N_{\rm H_2}}{10^{21}\,\rm cm^{-2}}\right) \approx 130~\rm mag + 940~mag \times  \left(\frac {I_{\rm 7m}}{\rm Jy\,beam^{-1}}\right)." (Cloud environment crossed by outflow lobes)
   - assumption: T_dust=23 K, kappa_1.3mm=0.01 cm g^-1, mu=2.8  
  > "$\mu = 2.8$ is the mean molecular weight" (3.4 Cloud environment crossed by outflow lobes)
   - fitting: _not stated_
   - validation: relative uncertainty ~30%; absolute up to factor of two  
  > "As for the absolute values of the visual extinction, they could be uncertain by up to a factor of two" (3.4 Cloud environment crossed by outflow lobes)
5. **Identify knots in PV diagrams**: PV diagrams along each jet axis averaged over 0.6''; knot velocity and position measured on the high-velocity vertical segments  
  > "we averaged the PV diagrams over $0.6\ensuremath{''}$, about half of the mean width of molecular jets detected in W43-MM1" (3.5 Knots in jets)
   - fitting: _not stated_
   - validation: knot velocity ~3 km/s and position ~0.2'' uncertainty  
  > "estimated to be $\sim$3 $\ensuremath{\rm km\,s^{-1}}$ and $\sim$0.2$\ensuremath{''}$ ($\sim$0.005 pc), respectively" (3.5 Knots in jets)
6. **Dynamical timescales and inter-knot timescales**: t_dyn = L_max/ΔV_max; t_knot = r_knot/ΔV_lobe; Δt between consecutive knots; deprojected by 1/tan(57.3°)  
  > "$t_{\rm knot}=r_{\rm knot}/\Delta V_{\rm lobe}$" (4.2.1 Dynamical timescales)
   - assumption: Mean inclination 57.3° for all lobes (random orientation)  
  > "we chose not to individually correct outflow characteristics but to keep the most probable angle, $57.3\degree$, for homogeneously deprojecting timescales." (4.2.3 Time span between consecutive ejection events and projection effects)
   - fitting: _not stated_
   - validation: Two extreme projection configurations tested; completeness limit assessed  
  > "We evaluated the projection effects of $\Delta t$ measurements by considering two extreme configurations" (4.2.3 Time span between consecutive ejection events and projection effects)

## Software

- **CASA** 4.7 (reduction), 5.4 (CLEAN): Calibration and imaging  
  > "Data were reduced in CASA 4.7, applying manual and selfcalibration scripts. We ran the CLEAN algorithm with CASA 5.4" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of outflow lobes | 46 | not stated | lobes | 1 | We discovered a rich cluster of 46 outflow lobes, driven by 27 protostars |
| Number of knots | 86 | not stated | knots | 5 | we discovered 86 knots in the integrated maps and PV diagrams of CO(2-1) |
| Exponent of L_max vs A_V | -0.5 | ±0.1 | dimensionless | 4 | $L_{\rm max}\propto A_{\rm V}^\alpha$ with $\alpha= -0.5 \pm 0.1$, with a Pearson correlation coefficient of -0.70 |
| Median dynamical timescale (uncorrected) | ~1500 | not stated | yr | 6 | range from 400 yr to $10^4$ yr, with a median value of $\sim$1500 yr |
| Median Δt between knots (uncorrected) | ~780 | not stated | yr | 6 | varies from 290 yr to 4300 yr, with a median of $\sim$780 yr |
| Typical ejection timescale (deprojected) | ~500 | +300/-100 | yr | 6 | $\overline{\Delta \rm t_{\rm corr}} \sim 500\pm^{300}_{100}$ yr |
| Fraction of lobes detected in both CO and SiO | 42 of 46 (91%) | not stated | lobes | 1 | In total 42 out of the 46 outflow lobes (i.e. 91%) are detected both in CO(2-1) and SiO(5-4) |

## Qualitative findings

- Outflow length anti-correlates with background extinction; no correlation with core mass  
  > "a clear anti-correlation of the length of outflow lobes projected on the plane of the sky with the visual extinction appears" (4.1.1 Outflow maximum length and velocity)
- PV diagrams show Hubble-law fingers and knots, signs of episodic ejection  
  > "This probably is the signature of episodic ejection, with variation of the velocity and/or of the mass of the gas ejected" (4.2.2 PV diagrams as open books on ejection variability)

## Claim tuples

- H: Does W43-MM1 host a rich outflow cluster? | E: CO(2-1) and SiO(5-4) mosaic search | R: 46 lobes from 27 protostars | F: Richest outflow cluster known per area, twice NGC 1333 | **supported**
- H: Does the environment limit outflow properties? | E: Compare L_max with A_V and core mass | R: alpha=-0.5±0.1, Pearson -0.70 | F: Dense dynamical environment limits outflow length, so t_dyn is a poor ejection proxy | **supported**
- H: Is ejection, and hence accretion, episodic? | E: PV diagrams of 72 knots, Δt between knots | R: Typical Δt_corr ~500 yr | F: Episodic ejection is common, consistent with nearby protostars | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Interferometric mosaics give a large homogeneous sample of outflows in one cloud  
  > "Interferometric mosaics at (sub)millimeter wavelengths currently are the best way to image a large and homogeneous sample of outflows" (Introduction)
- Alternative: Individual inclination corrections rejected; uniform 57.3° kept because three indirect methods disagree  
  > "Since the three indirect methods (statistical, morphology, and PV diagrams arguments) do not converge toward the same objects" (4.2.3 Time span between consecutive ejection events and projection effects)
- How they decided it was enough: _not stated_
- Limitation (authors): Missing short spacings and self-absorption prevent detection of low-velocity outflows (|ΔV|<10 km/s)  
  > "our observation limitations (effect of self-absorption and missing short spacings) preclude the detection of the outflow cavities developing close to the systemic velocity" (3.3 Main characteristics of outflow lobes)
- Limitation (authors): Unknown inclinations introduce scatter; dynamical timescales are rough  
  > "outflow dynamical timescales should only be considered as rough estimates of the protostellar lifetimes" (4.2.1 Dynamical timescales)
- Caveat (inferred, ours): Knot identification is by eye with no objective criterion or completeness test
- Caveat (inferred, ours): Uniform 57.3° inclination is a strong assumption
- Caveat (inferred, ours): Knot Δt may reflect propagation instabilities rather than accretion variability
- Caveat (inferred, ours): Entrained-gas velocities are used as jet velocities

## Reproducibility

- Data public (paper): Project 2013.1.01365.S cited; public status not stated  
  > "This paper makes use of the following ALMA data: #2013.1.01365.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust and scales
- Missing: Core positions and masses (from Motte+2018)
- Missing: Knot lists are by eye; PV axes and widths per jet
- Data volume (inferred): Large (mosaic of 33 12m + 11 ACA fields); hundreds of GB raw
- Score (inferred): 3/5, Data are identifiable and the analysis is clear, but imaging and line-free details are missing and the knot selection is subjective.
- Rediscovery candidate: no, Knot identification is manual and the core catalogue comes from another paper; the data may be public but the recipe is incomplete.

## Links

- Method: (cite: motte18b) (Core catalogue and continuum imaging)
- Companion: Pouteau et al. in prep. (Inflow and O13CS velocities in W43-MM1)
- Related: W43-MM1 ALMA mosaic (Motte et al. 2018)

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 43,
  "rate": 0.566
 },
 "evidence_ok": true
}
```
