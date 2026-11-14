# ALMA view of the circumstellar environment of the post-common-envelope-evolution binary system HD 101584

`2015A&A...576L..15O` | Astronomy and Astrophysics 2015 | first author: Olofsson, H. | arXiv: 1503.08609 | DOI: 10.1051/0004-6361/201526026

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: What are the morphology, kinematics, masses and energetics of the circumstellar environment of the post-AGB binary HD 101584, and does it match common-envelope scenarios?  
  > "We study the circumstellar evolution of the binary HD101584, consisting of a post-AGB star and a low-mass companion, which is most likely a post-common-envelope-evolution system." (abstract)
- Target **HD 101584 (V885 Cen, IRAS 11385-5517)**: coordinates _not stated_; z/distance ≈ 0.7 kpc  
  > "they estimated a (present-day) mass of ≈ 0.6 _M_ ⊙, a luminosity of ≈ 4000 _L_ ⊙, and a distance of ≈ 0.7 kpc." (1. Introduction); distance from Bakker et al. (1996b)  
  > "they estimated a (present-day) mass of ≈ 0.6 _M_ ⊙, a luminosity of ≈ 4000 _L_ ⊙, and a distance of ≈ 0.7 kpc." (1. Introduction)

## Data provenance

- ALMA projects: 2012.1.00248.S
- bands: Band 6 (cycle 1)  
  > "in two frequency settings in band 6 (cycle 1)" (2. Observations)
- frequencies and spectral setup: Two tunings (230.53 and 220.06 GHz); four spws of 1.875 GHz with 3840 channels each  
  > "the data contain four spectral windows (spw) of 1.875 GHz width and with 3840 channels." (2. Observations)
- continuum bandwidth: line-free equivalent bandwidth of 10.2 GHz  
  > "We produced a single continuum map combining both tunings with a line-free equivalent bandwidth of 10.2 GHz." (2. Observations)
- arrays: ALMA 12 m array, 35 antennas  
  > "obtained on 29 April 2014 with 35 antennas of the ALMA 12 m array" (2. Observations)
- configurations: _not stated_
- baselines: 16 to 497 m  
  > "The baselines range from 16 to 497 m." (2. Observations)
- angular resolution: 0.65×0.57 arcsec (12CO), 0.65×0.54 arcsec (13CO, C18O); continuum 0.56×0.49 arcsec  
  > "13 CO, C 18 O 220.06 26 0.67 0.8 0.65 × 0.54, 46.1" (Table 1)
- max recoverable scale: ≈ 10 arcsec  
  > "This means a maximum recoverable scale of ≈ 10 [′′] ." (2. Observations)
- sensitivity: _not stated_
- time on source: 8 min (12CO tuning), 26 min (13CO/C18O tuning)  
  > "12 CO 230.53 8 0.64 1.8 0.65 × 0.57, 8.2" (Table 1)
- observing dates: 29 April 2014  
  > "obtained on 29 April 2014" (2. Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.53 GHz (tuning))
- Line: 13CO, C18O J=2-1 (220.06 GHz (tuning))
- Other facility **SEST**: single-dish 12CO(2-1) profile for comparison of missing flux  
  > "SEST [12] CO (black, offset +5 Jy)" (Figure 2 caption)
- External data: Single-dish 12CO(2-1) flux 850 Jy km/s  
  > "The single-dish 12 CO(2–1) flux is 850 Jy km s [−][1] (Olofsson & Nyman 1999)" (3.1 Global characteristics) [from Olofsson & Nyman 1999]
- External data: SED model and dust temperature 45 K, mass 0.6 Msun, distance 0.7 kpc  
  > "an adopted dust temperature of 45 K [from the SED in Bakker et al. (1996b)]" (3.3 Mass, energy, and momentum estimates) [from Bakker et al. (1996b)]
- External data: Dust opacity kappa_230 = 0.5 cm2/g  
  > "the dust opacity κ 230 = 0.5 cm [2] g [−][1] (Liseau et al. 2015)" (3.3 Mass, energy, and momentum estimates) [from Liseau et al. 2015]
- External data: Orbital period 218 d and K1 = 3 km/s  
  > "Adopting the orbital parameters (period _P_ = 218 days and velocity semi-amplitude _K_ 1 = 3 km s [−][1] )" (3.4 A scenario) [from Bakker et al. 1996a,b]
- External data: Rotational temperature 30 K; proto-PN energy and momentum ranges  
  > "and _T_ rot =30 K (Bujarrabal et al. 2001)" (3.3 Mass, energy, and momentum estimates) [from Bujarrabal et al. 2001]

## Processing

### Calibration

- pipeline or manual: Manual CASA reduction with WVR and Tsys corrections, bandpass and gain calibration  
  > "After corrections for the time and frequency dependence of the system temperatures and rapid atmospheric variations at each antenna using WVR data, bandpass and gain calibration were made." (2. Observations)
- casa version: CASA 4.2.2  
  > "The data were reduced using CASA 4.2.2." (2. Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres and Titan (Butler-JPL-Horizons 2012)  
  > "Flux calibration was made using Ceres and Titan for the different tunings (Butler-JPL-Horizons 2012, ALMA Memo 594)." (2. Observations)
- flux scale uncertainty: within 5%  
  > "we estimate the absolute flux calibration to be accurate to within 5%." (2. Observations)
- self calibration: Self-calibration on strong continuum, per tuning  
  > "for each individual tuning, self-calibration was performed on the strong continuum." (2. Observations)

### Imaging

- task: CASA clean  
  > "Imaging was made using the CASA clean algorithm" (2. Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Our final line images were created using natural weighting and the restoring beam given in Table 1." (2. Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: performed on the emission line data before imaging  
  > "after a continuum subtraction was performed on the emission line data" (2. Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: Line channel rms 1.8 mJy/beam (12CO), 0.8 (13CO/C18O); continuum 0.14 mJy/beam  
  > "The dynamic-range-limited rms is 0.14 mJy beam [−][1]" (Figure 1 caption)

### Inherited from earlier work

- Flux calibrator models  
  > "(Butler-JPL-Horizons 2012, ALMA Memo 594)" (2. Observations) [from Butler-JPL-Horizons 2012, ALMA Memo 594]
- Rotational temperature and abundance assumptions for mass and energy  
  > "and _T_ rot =30 K (Bujarrabal et al. 2001)" (3.3 Mass, energy, and momentum estimates) [from Bujarrabal et al. 2001]

### Not stated but needed to reproduce (our reading)

- clean threshold, number of iterations and masks
- image size and cell size
- line-free channels for continuum subtraction
- self-calibration solution intervals
- flagging details beyond the antennas mentioned
- how the global line profiles were extracted (aperture)
- details of the kinetic energy and momentum calculation
- spectral resolution/velocity binning for the channel maps

## Analysis recipe

1. **Measure continuum and global line fluxes**: Continuum map from line-free bandwidth; line fluxes integrated over global profiles; compared with SED and SEST  
  > "The ALMA total fluxes, integrated over the global line profiles, are 690, 150, and 18 Jy km s [−][1] for the [12] CO, [13] CO, and C [18] O _J_ = 2–1 lines, respectively." (3.1 Global characteristics)
   - software: CASA
   - fitting: _not stated_
   - validation: Comparison with SEST single-dish profile to estimate missing flux  
  > "based on a detailed comparison of the ALMA global and the single-dish line profiles, no flux is missed in the central 20 km s [−][1]" (3.1 Global characteristics)
2. **Morphology and kinematics from channel maps and PV diagram**: Velocity-channel maps and PV diagram along PA=90 deg; age from projected length and velocity with tilt 10 deg  
  > "adopting a tilt angle of 10 [◦], a projected expansion length of 1 [′′] . 5, and an expansion velocity of 60 km s [−][1], the age is estimated to be ≈ 500 yr." (3.2 A jet, an hour-glass structure, and the central region)
   - assumption: Inclination about half the hour-glass opening angle, ≈ 10 deg  
  > "We estimate the inclination angle, _i_, to be about half of the opening angle of the hour-glass structure, ≈ 10 [◦]." (3.2 A jet, an hour-glass structure, and the central region)
   - fitting: _not stated_
   - validation: _not stated_
3. **Dust and gas mass**: Dust mass from the 1.3 mm flux (Eq. 1); gas mass from C18O(2-1) (Eq. 2)  
  > "A simple estimate of the gas mass is obtained using" (3.3 Mass, energy, and momentum estimates)
   - assumption: D = 0.7 kpc, kappa230 = 0.5 cm2/g, Td = 45 K, dust-to-gas 200  
  > "assuming a dustto-gas ratio of 200" (3.3 Mass, energy, and momentum estimates)
   - assumption: f_C18O = 4e-7, f_CO = 2e-4, Trot = 30 K  
  > "_f_ C 18 O =4 ×10 [−][7]" (3.3 Mass, energy, and momentum estimates)
   - fitting: _not stated_
   - validation: _not stated_
4. **Energetics and comparison with orbital energy**: Kinetic energy and momentum of gas at ≥10 km/s from C18O; orbital mass function and released orbital energy for the capture scenario  
  > "The amount of orbital energy released is" (3.4 A scenario)
   - assumption: circular orbit, i=10 deg, M1=0.6 Msun, M1,i=1.6 Msun, a2,i=4 AU  
  > "assuming _a_ 2,i = 4 AU (sufficiently near to be captured)." (3.4 A scenario)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.2: data reduction, self-calibration, continuum subtraction and clean imaging  
  > "The data were reduced using CASA 4.2.2." (2. Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux density at 230 GHz | 112 | not stated | mJy | 1 | The total flux density, _S_ 230 = 112 mJy |
| Systemic velocity | 42 | 1 | km/s (LSR) | 1 | estimated to be 42 ± 1 km s [−][1] (LSR) |
| Dust mass | 0.007 | at least a factor of four | Msun | 3 | gives _M_ d ≈ 0.007 _M_ ⊙ |
| Gas mass from C18O | 0.3 | considerable | Msun | 3 | we obtain _M_ g ≈ 0.3 _M_ ⊙ |
| Kinetic energy of accelerated gas | 4e45 | lower limit | erg | 4 | is ≈ 4 × 10 [45] erg (a lower limit since extended flux from accelerated gas is missed) |
| Released orbital energy | 2e45 | not stated | erg | 4 | ≈ 2 × 10 [45] erg, (4) |
| Age of complex structure | ≈500 | not stated | yr | 2 | the age is estimated to be ≈ 500 yr. |
| Companion mass | ≈0.6 | not stated | Msun | 4 | we estimate that _M_ 2 ≈ 0.6 _M_ ⊙ at a distance of _a_ ≈ 0.7 AU |

## Qualitative findings

- Bipolar hour-glass structure seen almost pole-on, formed by a jet with peak velocity ≈150 km/s  
  > "The circumstellar medium has a bipolar hour-glass structure, seen almost pole-on, formed by an energetic jet, ≈ 150 km s [−][1] ." (abstract)

## Claim tuples

- H: The circumstellar medium was shaped by a binary interaction event | E: CO channel maps and PV diagram | R: Jet and complex structure both have ages ≈ 500 yr and ≈ 520 yr | F: A common origin, such as companion infall, is possible | **supported**
- H: Current common-envelope scenarios can explain the ejection energy | E: Compare kinetic energy of accelerated gas with released orbital energy | R: Kinetic energy ≈4e45 erg exceeds released ≈2e45 erg | F: Another process must augment or dominate the ejection | **supported**
- H: Substantial mass resides in the central region | E: C18O line as mass indicator | R: About 55% of integrated flux within ±10 km/s; ≈0.3 Msun gas | F: Much material is in an unresolved equatorial region | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Flux lost to missing short spacings; large uncertainties in masses and orbital estimates  
  > "suggesting a significant loss of flux originating from a region larger than 10 [′′] ." (3.1 Global characteristics)
- Caveat (inferred, ours): Mass estimates rely on assumed Trot, abundances and opacity with factor-of-several uncertainties
- Caveat (inferred, ours): Inclination of 10 deg is poorly constrained and drives ages and orbital results
- Caveat (inferred, ours): No uncertainties on most derived quantities

## Reproducibility

- Data public (paper): Project code given; public status not stated  
  > "ADS/JAO.ALMA#2012.1.00248.S" (1. Introduction (footnote))
- Products in archive: _not stated_
- Missing: clean parameters and masks
- Missing: aperture for global profiles
- Missing: precise energy/momentum calculation details
- Data volume (inferred): ~20-50 GB
- Score (inferred): 3/5, Single project and simple estimates with given equations, but imaging and extraction details are missing.
- Rediscovery candidate: yes, A single archival project; the main results are numeric and the analysis is simple, although some details are missing.

## Links

- Companion: Olofsson & Nyman 1999 (earlier single-dish CO maps of HD 101584)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
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
  "facts": 70,
  "stated": 42,
  "rate": 0.6
 },
 "evidence_ok": true
}
```
