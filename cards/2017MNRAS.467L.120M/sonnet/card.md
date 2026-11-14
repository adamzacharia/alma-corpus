# The ALMA view of W33A: a spiral filament feeding the candidate disc in MM1-Main

`2017MNRAS.467L.120M` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Maud, L. T. | arXiv: 1701.06958 | DOI: 10.1093/mnrasl/slx010

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Is there a Keplerian disc around the O-type MYSO W33A MM1-Main at ~500 au resolution, and what is the structure of the surrounding MM1 region?  
  > "to search for a sub$-$1000 au disc around the central O-type massive young stellar object (MYSO) W33A MM1-Main" (abstract)
- Target **W33A MM1 (MM1-Main)**: coordinates MM1-Main 18:14:39.512 -17:52:00.13 (J2000)  
  > "W33A (G12.91-0.26), a relatively nearby archetypal massive star formation site (2.4 kpc, (cite: Immer2013))" (Introduction); "| Main | 18:14:39.512 | $-$17:52:00.13 |" (Table 1); z/distance 2.4 kpc  
  > "W33A (G12.91-0.26), a relatively nearby archetypal massive star formation site (2.4 kpc, (cite: Immer2013))" (Introduction); "| Main | 18:14:39.512 | $-$17:52:00.13 |" (Table 1); distance from Immer et al. 2013  
  > "W33A (G12.91-0.26), a relatively nearby archetypal massive star formation site (2.4 kpc, (cite: Immer2013))" (Introduction); "| Main | 18:14:39.512 | $-$17:52:00.13 |" (Table 1)

## Data provenance

- ALMA projects: 2012.1.00784.S
- bands: Band 6 (230 GHz) and Band 7 (345 GHz)  
  > "in band 6 (230 GHz) and 7 (345 GHz)" (abstract)
- frequencies and spectral setup: 4 spectral windows per band, 937.5 MHz bandwidth each, 488 kHz resolution  
  > "Both bands had 4 spectral windows, each with a 937.5 MHz bandwidth and 488 kHz frequency resolution" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 30.8 m to 1300 m in band 6, out to 1600 m in band 7  
  > "The array configurations had baseline lengths from 30.8 m to 1300 m in band 6 and out to 1600 m in band 7." (2 Observations)
- angular resolution: 0.32"x0.26" band 6; 0.21"x0.14" band 7 (robust=0.5)  
  > "The resulting images have a beam size of 0.32$''\times$0.26$''$ in band 6 and 0.21$''\times$0.14$''$ at band 7 using a robust=0.5 weighting" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: June 24, 25 and 26, 2015  
  > "taken on June 24, 25 and 26, 2015" (2 Observations)
- pi or archival as stated: PI: M. G. Hoare  
  > "(2012.1.00784.S $-$ PI: M. G. Hoare)" (2 Observations)
- Line: CH3CN J=12-11 and 13-12, K=0-9 (band 6) (not stated)
- Line: CH3CN J=19-18, K=0-8 (band 7) (not stated)
- Line: SiO 8-7 (not stated)
- External data: Radio free-free detections at 8.4, 15.0 and 43.3 GHz used to extrapolate free-free flux  
  > "after extrapolating from the radio detections at 8.4, 15.0 and 43.3 GHz (cite: vandertak2005; Rengarajan1996)" (3.1 The Continuum Emission) [from (cite: vandertak2005; Rengarajan1996)]
- External data: Free-free spectral index 1.03±0.08  
  > "$\alpha_{\rm ff}$=1.03$\pm$0.08 (cite: GalvanMadrid2010)" (3.1 The Continuum Emission) [from (cite: GalvanMadrid2010)]
- External data: Inclination ~50 deg  
  > "inclination angle of $\sim$50$^{\circ}$ (cite: dewit2010)" (3.5 W33A MM1-Main as a disc candidate?) [from (cite: dewit2010)]

## Processing

### Calibration

- pipeline or manual: Manual reduction in CASA  
  > "The data were manually reduced using casa (cite: McMullin2007) version 4.5.1." (2 Observations)
- casa version: 4.5.1  
  > "The data were manually reduced using casa (cite: McMullin2007) version 4.5.1." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Performed, minimum timescale ~30 s  
  > "Self calibration was performed, although a minimal timescale of $\sim$30 s was used" (2 Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "using a robust=0.5 weighting" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum from line-free channels  
  > "had enough ‘line-free’ channels to determine the continuum emission" (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.32"x0.26" band 6; 0.21"x0.14" band 7  
  > "beam size of 0.32$''\times$0.26$''$ in band 6 and 0.21$''\times$0.14$''$ at band 7" (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Dust opacity kappa0 = 0.5 cm2/g at 230 GHz  
  > "$\kappa_0$ = 0.5 cm$^{2}\,$g$^{-1}$ at 230 GHz (cite: GalvanMadrid2010)" (3.1 The Continuum Emission) [from (cite: GalvanMadrid2010)]
- Mass equation  
  > "We use Equation 1 of (cite: Maud2013a)" (3.1 The Continuum Emission) [from (cite: Maud2013a)]
- Rotation temperature diagram analysis  
  > "We follow the rotation temperature diagram (RTD) analysis outlined in (cite: Araya2005)" (3.2 CH$_3$CN Emission) [from (cite: Araya2005)]
- Optical depth equations  
  > "following equations 2 and 3 from (cite: Schuller2009)" (3.1 The Continuum Emission) [from (cite: Schuller2009)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum
- Clean threshold, masks, image size and cell size
- Flux, bandpass and phase calibrators and flux scale uncertainty
- Details of the matched-uv beta imaging and smoothing
- Exact RTD fitting procedure and line selection
- Method of fitting the CH3CN lines for the rough stellar mass
- Continuum rms

## Analysis recipe

1. **Image and measure continuum, derive masses**: Band 7 continuum fluxes; masses assuming optically thin dust  
  > "Masses are estimated from the Band 7 data, assuming optically thin emission" (3.1 The Continuum Emission)
   - software: CASA
   - parameter: Temperature fixed to 80 K where CH3CN too weak  
  > "Where CH$_3$CN is too weak for our temperature estimation technique we fix it to 80 K" (3.1 The Continuum Emission)
   - assumption: Dust to gas ratio 100; kappa = kappa0 (nu/nu0)^beta, kappa0 = 0.5 cm2/g at 230 GHz  
  > "a dust to gas ratio of 100 and a dust opacity $\kappa_\nu$ = $\kappa_0 (\nu/\nu_0)^\beta$" (3.1 The Continuum Emission)
   - fitting: _not stated_
   - validation: Compared with SMA masses  
  > "The masses are consistent with our SMA data (cite: GalvanMadrid2010)" (3.1 The Continuum Emission)
2. **Dust opacity index beta**: Band 6/7 spectral index with matched uv coverage and beams after subtracting free-free; alpha = beta + 2  
  > "where the dust opacity index $\beta$ is related to the spectral index by $\alpha = \beta + 2$" (3.1 The Continuum Emission)
   - parameter: matched uv range 40 to 610 k lambda  
  > "*matched u,v coverage* (40 to 610  K lambda)" (3.1 The Continuum Emission)
   - assumption: Rayleigh-Jeans; free-free modelled as point sources for Main and SE  
  > "We model the free-free emission by point sources for MM1-Main and MM1-SE" (3.1 The Continuum Emission)
   - fitting: _not stated_
   - validation: Optical depth check (tau~0.06) supports optically thin emission  
  > "the calculated maximal optical depth only reaches $\tau \sim$0.06" (3.1 The Continuum Emission)
3. **CH3CN temperature map**: Pixel-by-pixel rotation temperature diagram, single optically thin LTE component, on band 7 J=19-18 K-ladder; cap at 624 K  
  > "on a pixel-by-pixel basis for a single optically thin component in LTE" (3.2 CH$_3$CN Emission)
   - software: RADEX
   - assumption: LTE, optically thin  
  > "for a single optically thin component in LTE" (3.2 CH$_3$CN Emission)
   - fitting: _not stated_
   - validation: RADEX cannot reproduce observed line ratios with a single component, suggesting at least 2 temperature components  
  > "This suggests at least 2 temperature components may be required." (3.2 CH$_3$CN Emission)
4. **Kinematics: moments, SiO outflow, Keplerian mass estimate**: Moment 1 and 2 maps of CH3CN 19-18; SiO clipped at 3 sigma; CH3CN lines fit at blue and red peaks to estimate mass  
  > "we establish a rough stellar mass estimate after fitting the CH$_3$CN lines at the flux peaks of the blue- and red-shifted emission" (3.5 W33A MM1-Main as a disc candidate?)
   - assumption: Keplerian rotation, inclination ~50 deg  
  > "Under a naive assumption that the velocity shift is due to Keplerian rotation" (3.5 W33A MM1-Main as a disc candidate?)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.1: Manual data reduction and self-calibration  
  > "The data were manually reduced using casa (cite: McMullin2007) version 4.5.1." (2 Observations)
- **RADEX** : Reproducing CH3CN K-ladder line fluxes  
  > "With radex (cite: vandertak2007) we can reproduce individual K-ladder line fluxes" (3.2 CH$_3$CN Emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| MM1-Main band 7 peak flux (no free-free correction) | 0.96 | not stated | mJy/beam | 1 | peak flux of 0.96 mJy beam$^{-1}$ at Band 7 without free-free correction |
| MM1-Main mass | 0.15-0.21 | range | Msun | 1 | / 18:14:39.512 / $-$17:52:00.13 / 126.1 / 100.3 / 23.7$-$45.1 / 73.4 / 56.8 / 18.5$-$28.9 / 0.15$-$0.21 / |
| Spectral index alpha of MM1-Main | 2.0-2.5 | range | dimensionless | 2 | The spectral index values $\alpha$ for MM1-Main range from 2.0 to 2.5 and the dust opacity index $\beta$ from 0.0 to 0.5 |
| Maximum optical depth at MM1-Main peak | 0.06 | not stated | dimensionless | 2 | the calculated maximal optical depth only reaches $\tau \sim$0.06 |
| CH3CN temperature cap in MM1-Main | 624 | not stated | K | 3 | we cap the temperature at 624 K |
| Minimum central stellar mass (Keplerian) | 13 | lower limit | Msun | 4 | The central source would be at least 13 M$_{\odot}$ |
| SiO outflow position angle | ~120 | not stated | deg | 4 | The PA of the central flow based on the linear blue-shifted emission is $\sim$120$^{\circ}$ |

## Qualitative findings

- A spiral feeding filament is detected in gas and dust  
  > "the large scale spiral ‘feeding filament’ we detect in both gas and dust emission" (abstract)

## Claim tuples

- H: Is there a Keplerian disc in MM1-Main at ~500 au? | E: CH3CN moment maps and line profiles at 0.2" resolution | R: Kinematics are complex; double-peaked profile with centroids at ~34.8 and ~42.5 km/s | F: No simple Keplerian disc, though a compact disc or unresolved binary cannot be excluded | **partially**
- H: Does a spiral filament feed MM1-Main? | E: Continuum and moment 1 map | R: Velocity gradient from ~37 to ~41 km/s along spiral structure | F: A spiral feeding filament likely supplies material to the core | **supported**
- H: Do dust properties indicate grain growth? | E: Band 6/7 spectral index after free-free removal | R: beta 0.0-0.5 | F: beta ~0.5 suggests larger grains | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Components may be embedded sources, filaments or outflow cavity wall over-densities  
  > "It is unclear whether the components S, NW, E, SE and ridge, are embedded sources" (3.4 Nature of the other continuum sources)
- How they decided it was enough: _not stated_
- Limitation (authors): Possible unresolved binary cannot be excluded  
  > "We cannot however rule out the possibility of an unresolved binary or multiple system." (abstract)
- Caveat (inferred, ours): Mass lower limit relies on a naive Keplerian assumption and assumed inclination
- Caveat (inferred, ours): Free-free extrapolation uncertainty dominates beta
- Caveat (inferred, ours): Single-component LTE temperatures break down in the core
- Caveat (inferred, ours): Few methodological details given (letter format)

## Reproducibility

- Data public (paper): Archival project code given with ALMA acknowledgement  
  > "ADS/JAO.ALMA#2012.1.00784.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibrator and flux scale information
- Missing: Imaging parameters (clean, masks, image size)
- Missing: Detailed RTD and line-fitting procedure
- Data volume (inferred): ~100-300 GB raw for two bands
- Score (inferred): 3/5, Public data and basic recipe stated, but imaging and fitting details are sparse.
- Rediscovery candidate: no, Imaging and analysis recipe is too incomplete and key results are partly qualitative.

## Links

- Method: (cite: Araya2005) (Rotation temperature diagram analysis)
- Method: (cite: Maud2013a) (Mass equation)
- Companion: (cite: GalvanMadrid2010) (Previous SMA observations of W33A)

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
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
  "facts": 73,
  "stated": 42,
  "rate": 0.575
 },
 "evidence_ok": true
}
```
