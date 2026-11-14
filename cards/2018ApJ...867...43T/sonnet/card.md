# The VLA/ALMA Nascent Disk and Multiplicity (VANDAM) Survey of Perseus Protostars. VI. Characterizing the Formation Mechanism for Close Multiple Systems

`2018ApJ...867...43T` | The Astrophysical Journal 2018 | first author: Tobin, John J. | arXiv: 1809.06434 | DOI: 10.3847/1538-4357/aae1f7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Are close (<600 AU) protostellar multiple systems in Perseus formed by disk fragmentation or turbulent fragmentation, judged from circum-multiple dust and gas kinematics?  
  > "definitive evidence in favor of disk fragmentation would be finding
them embedded within a common, circumbinary/multiple structure that has Keplerian rotation." (1. INTRODUCTION)
- Target **17 close multiple protostar systems in Perseus (VANDAM sample)**: coordinates _not stated_; z/distance 300 pc  
  > "We adopt a distance of 300 pc as an average
distance for the Perseus molecular cloud (Ortiz-Le´on et al. 2018)." (1. INTRODUCTION); distance from Ortiz-Leon et al. 2018 (Gaia-based), adopted as average  
  > "We adopt a distance of 300 pc as an average
distance for the Perseus molecular cloud (Ortiz-Le´on et al. 2018)." (1. INTRODUCTION)

## Data provenance

- ALMA projects: 2013.1.00031.S
- bands: 1.3 mm continuum plus five lines  
  > "We observed 17 close ( _<_ 600 AU separation)
multiple systems at 1.3 mm in continuum and five molecular lines" (abstract)
- frequencies and spectral setup: 2 GHz continuum band centered at 232.5 GHz (TDM, 128 channels); three 60 MHz windows with 1960 channels (0.083 km/s)  
  > "The correlator was configured to observe
a 2 GHz continuum band centered at 232.5 GHz and observed in TDM mode with 128 channels." (2. OBSERVATIONS AND DATA REDUCTION)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 32 - 2000 meters, 33 antennas  
  > "with 33 antennas operating and sampling baselines between 32 - 2000 meters" (2. OBSERVATIONS AND DATA REDUCTION)
- angular resolution: continuum 0.27x0.16 arcsec (81x48 AU); lines 0.35x0.25 arcsec  
  > "The typical beam sizes of the continuum and molecular line images
are 0 _[′′]_ _._ 27 _×_ 0 _[′′]_ _._ 16 (81 AU _×_ 48 AU) and 0 _[′′]_ _._ 35 _×_ 0 _[′′]_ _._ 25 (108 AU _×_ 76 AU), respectively." (2. OBSERVATIONS AND DATA REDUCTION)
- max recoverable scale: _not stated_
- sensitivity: ~0.14 mJy/beam continuum; ~15 mJy/beam in 0.25 km/s channels  
  > "The resultant noise in the 1.3 mm continuum was
_∼_ 0.14 mJy beam _[−]_ [1] and _∼_ 15 mJy beam _[−]_ [1] in 0.25 km s _[−]_ [1] channels for the spectral line observations." (2. OBSERVATIONS AND DATA REDUCTION)
- time on source: ~2.9 minutes per source in a 1.8 hour block  
  > "the total time spent on each source was _∼_ 2.9 minutes" (2. OBSERVATIONS AND DATA REDUCTION)
- observing dates: 27 September 2015 (Cycle 2)  
  > "observed with the ALMA during Cycle 2 on 27 September 2015" (2. OBSERVATIONS AND DATA REDUCTION)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- Line: SO JN=6_5-5_4 (not stated)
- Line: H2CO J=3_03-2_02 (not stated)
- Other facility **VLA (VANDAM survey)**: Prior continuum detections of the multiple systems, positions, 9 mm flux densities, separations  
  > "This
survey conducted with the NSF’s Karl G. Jansky Very Large Array (VLA) observed all known Class 0
and Class I protostars in the Perseus star forming region" (1. INTRODUCTION)
- External data: 9.1 mm flux densities (with and without free-free correction) used for spectral indices  
  > "We use the 9.1 mm flux densities from Tychoniec et al. (2018b) to
calculate _α_ with respect to the flux densities at 1.3 mm." (3.3 Spectral Indices) [from Tychoniec et al. 2018b]
- External data: Outflow position angles  
  > "The larger-scale outflows have previous

ALMA Perseus Multiplicity 9


characterization of their orientations, when possible, from Stephens et al. (2017)" (3.4 Molecular Line Kinematics) [from Stephens et al. 2017]
- External data: VLA positions and multiplicity/separations from VANDAM  
  > "the most precisely measured positions for
the observed protostars in Perseus are those listed in Tobin et al. (2016b) from the VLA" (2. OBSERVATIONS AND DATA REDUCTION) [from Tobin et al. 2016b]

## Processing

### Calibration

- pipeline or manual: Manually reduced by North American ARC staff  
  > "The raw visibility data were manually reduced by the North American ARC staff using CASA
version 4.5.0" (2. OBSERVATIONS AND DATA REDUCTION)
- casa version: CASA 4.5.0 (reduction, clean); CASA 4.7.2 (imfit)  
  > "The data were imaged using the _clean_ task within CASA 4.5.0" (2. OBSERVATIONS AND DATA REDUCTION)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0238+166; phase J0319+4130, bandpass J0237+2848  
  > "the amplitude and absolute
flux calibrator was the monitored quasar J0238+166" (2. OBSERVATIONS AND DATA REDUCTION)
- flux scale uncertainty: better than 10%, not included in uncertainties  
  > "The absolute flux calibration accuracy is
expected to be better than 10%; however, we do not include this uncertainty in our calculations" (2. OBSERVATIONS AND DATA REDUCTION)
- self calibration: 2 rounds phase self-cal (scan-length, then 12.1 or 6.05 s) then amplitude self-cal with normalization; 16 of 17 fields; applied to line bands  
  > "When possible, we performed 2 rounds of phase self-calibration, first with
solution intervals that encompassed the length of an entire on-source scan, then the second round
utilized either 12.1 or 6.05 second solution intervals." (2. OBSERVATIONS AND DATA REDUCTION)

### Imaging

- task: CASA clean  
  > "The data were imaged using the _clean_ task within CASA 4.5.0" (2. OBSERVATIONS AND DATA REDUCTION)
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.5 (continuum); Natural for 13CO and C18O  
  > "generated using Briggs weighting with a robust parameter of 0.5." (2. OBSERVATIONS AND DATA REDUCTION)
- uv taper: 500 kλ taper for 13CO and C18O; uv-distances >50 kλ used  
  > "images were generated with Natural weighting,
tapering at 500 k _λ_, and also only using the data having _uv_ -distances _>_ 50 k _λ_ ." (2. OBSERVATIONS AND DATA REDUCTION)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Spectral index uncertainty formula  
  > "following Chiang et al. (2012)" (3.3 Spectral Indices) [from Chiang et al. 2012]
- Dust opacity kappa=0.899 from Ossenkopf & Henning table  
  > "taken from Ossenkopf & Henning (1994), Table 1 column 5" (3.2 Mass Estimates from Dust Continuum) [from Ossenkopf & Henning (1994)]

### Not stated but needed to reproduce (our reading)

- Cell size, image size, clean masks, iteration threshold and number of iterations
- Line-free channels and continuum subtraction method for line cubes
- Channel ranges for moment maps (only in Table 3, not in text)
- Exact spectral windows/rest frequencies
- Self-calibration reference and S/N thresholds per field
- Units of kappa=0.899 (cm2/g of gas or dust)
- Procedure for choosing polygon regions and extended flux
- Outflow PA values used

## Analysis recipe

1. **Self-calibrate and image continuum and lines**: Phase and amplitude self-cal on continuum, applied to lines; clean with Briggs 0.5 (13CO/C18O natural, 500 kλ taper)  
  > "Following the completion of self-calibration on the continuum, the solutions were also applied to the
spectral line bands." (2. OBSERVATIONS AND DATA REDUCTION)
   - software: CASA
   - parameter: uv-distance >50 kλ  
  > "we only include data at _uv_ -distances _>_ 50 k _λ_ to mitigate striping in the
images" (2. OBSERVATIONS AND DATA REDUCTION)
   - fitting: _not stated_
   - validation: Noise improved from ~1 to ~0.14 mJy/beam after self-cal  
  > "The non-self-calibrated continuum images had a noise level of _∼_ 1 mJy beam _[−]_ [1] ." (2. OBSERVATIONS AND DATA REDUCTION)
2. **Measure continuum flux densities**: Gaussian fits to compact components with imfit; polygon region for extended flux  
  > "The Gaussians were fit using the _imfit_ task of CASA 4.7.2." (2.1 Data Analysis)
   - software: CASA imfit, casaviewer
   - fitting: Gaussian fits; two Gaussians (inner/outer disk) for Per-emb-8 and L1448 IRS3A  
  > "so we fit two Gaussians to these sources and list the inner and outer Gaussian fits separately" (3.1 Dust Continuum Imaging)
   - validation: _not stated_
3. **Derive dust+gas masses**: Optically thin isothermal M = D^2 F / (kappa B(T)), times 100  
  > "Under the assumption that the dust emission is optically thin and isothermal, the dust mass can be" (3.2 Mass Estimates from Dust Continuum)
   - parameter: D~300 pc, Tdust=30 K, kappa=0.899  
  > "T _dust_ is assumed to
be 30 K, consistent with temperature estimates on _∼_ 100 AU scales (Whitney et al. 2003)" (3.2 Mass Estimates from Dust Continuum)
   - assumption: Gas-to-dust 100:1  
  > "assuming the canonical dust to gas mass ratio of 1:100" (3.2 Mass Estimates from Dust Continuum)
   - fitting: _not stated_
   - validation: Compared with CARMA masses of Tobin 2015a: ~20% higher  
  > "The mass calculations presented here tend to be about 20% higher than the
masses reported for some of the same sources in Tobin et al. (2015a)" (3.2 Mass Estimates from Dust Continuum)
4. **Spectral indices 1.3-9.1 mm**: alpha from ln flux ratio over ln frequency ratio, with ALMA and VLA 9.1 mm fluxes  
  > "we calculated _α_
with respect to both the corrected and uncorrected 9.1 mm flux densities." (3.3 Spectral Indices)
   - parameter: 10% flux calibration uncertainty added in quadrature  
  > "We do assume a 10% uncertainty in the
flux calibration for each flux density and add this in quadrature" (3.3 Spectral Indices)
   - fitting: _not stated_
   - validation: _not stated_
5. **Classify kinematics relative to outflows**: Red/blue integrated-intensity moment maps; measure PA of velocity gradient vs outflow; within 30 deg of orthogonal = disk rotation  
  > "that is within 30 _[◦]_ of orthogonal to the outflow direction, we classify it as being consistent with disk rotation." (3.4. Molecular Line Kinematics)
   - parameter: PA uncertainty ±10 deg  
  > "The position angles do have uncertainty and we estimate that this is _±_ 10 _[◦]_ ." (3.4. Molecular Line Kinematics)
   - fitting: _not stated_
   - validation: Consistency across multiple tracers (e.g. Per-emb-18)  
  > "The fact that all molecules have gradients in the same direction lends confidence
to interpreting the kinematics as rotation." (4.1.1 Class 0 and 0/I Systems)

## Software

- **CASA** 4.5.0 (clean); 4.7.2 (imfit): Calibration, self-calibration, imaging, Gaussian fitting  
  > "The Gaussians were fit using the _imfit_ task of CASA 4.7.2." (2.1 Data Analysis)
- **casaviewer** : Polygon regions for extended flux  
  > "we
used _casaviewer_ to draw a polygon region" (2.1 Data Analysis)
- **APLpy** : Plotting  
  > "This research made
use of APLpy, an open-source plotting package for Python" (Acknowledgements)
- **Astropy** : Python analysis  
  > "This research made
use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Class 0 systems with circum-multiple dust | 8 of 9 | not stated | systems | 2 | We also detect circum-multiple dust emission toward 8 out of 9 Class 0 multiples. |
| Systems with velocity gradient orthogonal to outflow | 8 of 12 | PA ±10 deg | systems | 5 | The velocity gradients in the circum-multiple gas are clearly orthogonal to the outflow directions in 8
out of the 12 systems |
| Companions detected among resolvable systems | 12 of 15 | not stated | systems | 2 | we detect the companions in 12 out
of 15 multiple systems that we were able to resolve. |
| Fraction disk fragmentation (<600 AU) | ~67% | small-number statistics | percent | 5 | The
raw numbers indicate that for multiples on scales _<_ 600 AU, _∼_ 67% form via disk fragmentation and
_∼_ 33% form via turbulent fragmentation. |
| Continuum noise after self-cal | 0.14 | not stated | mJy/beam | 1 | The resultant noise in the 1.3 mm continuum was
_∼_ 0.14 mJy beam _[−]_ [1] |
| Per-emb-12 total extended mass | 3.9 | 0.2 | Msun | 3 | Per-emb-12 2.3 _±_ 0.04 3.9 _±_ 0.2 |

## Qualitative findings

- Class I systems show no circum-multiple dust; most Class I have little gas emission  
  > "Most of the less-embedded Class I systems in our sample do not show circumbinary dust or
gas emission." (5. CONCLUSIONS)
- L1448 IRS3A and Per-emb-8 identified as strong disk candidates  
  > "We identified two additional strong disk candidates, L1448 IRS3A and Per-emb-8." (5. CONCLUSIONS)

## Claim tuples

- H: Close multiples form via disk fragmentation in rotating circum-multiple structures | E: ALMA 1.3 mm continuum and five lines toward 17 VANDAM close multiples; compare velocity gradients with outflow PAs | R: 8 of 12 systems have gradients orthogonal to outflow; 8 of 9 Class 0 have circum-multiple dust | F: Disk fragmentation is an important mechanism, but fractions are upper limits and statistics are small | **supported**
- H: VLA-detected companions are real | E: Detect companions with ALMA | R: 12 of 15 resolvable detected, 2 tentative | F: VANDAM detections are highly reliable | **supported**
- H: Keplerian rotation in circum-multiple gas | E: Moment maps only | R: S/N insufficient to fit rotation curves | F: Keplerian nature not confirmed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: ALMA provides simultaneous dust continuum and molecular lines to test circum-multiple structure and rotation  
  > "ALMA enables simultaneous observation of both dust continuum to look for circummultiple structure and molecular lines to search for rotation signatures" (1. INTRODUCTION)
- Alternative: Inward migration of initially wide turbulent-fragmentation companions could mimic disk fragmentation; so 66% is an upper limit  
  > "could be rephrased to say that 66% is an upper
limit on the frequency disk fragmentation for the production of close multiples." (4.2.3 Which is the Most Common Mechanism?)
- How they decided it was enough: _not stated_
- Limitation (authors): Short observations give low S/N per channel; phase unstable giving ~0.1 arcsec position offsets  
  > "there are
systematic position offsets in each field up to _∼_ 0 _[′′]_ _._ 1." (2. OBSERVATIONS AND DATA REDUCTION)
- Limitation (authors): Mass uncertainties from opacity, isothermal assumption, dust-to-gas ratio  
  > "We caution that the masses calculated may have systematic uncertainty" (3.2 Mass Estimates from Dust Continuum)
- Caveat (inferred, ours): Orthogonality criterion (30 deg) with no statistical test; subjective moment-map PA measurements
- Caveat (inferred, ours): Rotation vs infall/outflow/filtering not distinguished without PV or Keplerian fits
- Caveat (inferred, ours): Single 3-minute snapshot per source; spatial filtering affects extended emission
- Caveat (inferred, ours): Flux uncertainty excluded from masses

## Reproducibility

- Data public (paper): Project code given; ALMA archival data  
  > "This paper
makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00031.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust/taper
- Missing: Moment channel ranges are in Table 3 (not in text)
- Missing: Outflow PAs from Stephens et al. 2017
- Missing: Extended-flux polygon definitions
- Data volume (inferred): ~20-50 GB (one 1.8 h execution, 4 spectral windows, 17 fields)
- Score (inferred): 3/5, Public data and basic recipe stated, but subjective moment-map classification and missing imaging details limit exact reproduction.
- Rediscovery candidate: no, Main conclusions depend on subjective visual classification of kinematics; imaging details incomplete.

## Links

- Method: Chiang et al. 2012 (spectral index uncertainty formula)
- Companion: Tobin et al. 2016b (VANDAM VLA survey of Perseus)
- Companion: Tobin et al. 2016a (ALMA L1448 IRS3B spiral/disk fragmentation)
- Companion: Tychoniec et al. 2018b (9 mm VLA flux densities)
- Related: VANDAM survey

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 49,
  "rate": 0.628
 },
 "evidence_ok": true
}
```
