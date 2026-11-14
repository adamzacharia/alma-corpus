# An Explanation of the Very Low Radio Flux of Young Planet-mass Companions

`2017AJ....154..234W` | The Astronomical Journal 2017 | first author: Wu, Ya-Lin | arXiv: 1710.07489 | DOI: 10.3847/1538-3881/aa93db

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, exoplanets
- Question: Why do young wide planetary-mass companions show very low radio flux despite accretion signatures, and can compact optically thick disks explain it?  
  > "we suggest that disks around wide companions might be very compact and optically thick, in order to sustain a few Myr of accretion yet have very weak (sub)millimeter flux" (abstract)
- Target **GQ Lup B**: coordinates _not stated_; z/distance ~150 pc  
  > "$D$ (pc) | $\sim$150 | $\sim$140 | $\sim$150 | $\sim$150 | $\sim$180" (Table 2); distance from Table 2 references (Wu 2017 and references therein)  
  > "$D$ (pc) | $\sim$150 | $\sim$140 | $\sim$150 | $\sim$150 | $\sim$180" (Table 2)
- Target **DH Tau B**: coordinates _not stated_; z/distance ~140 pc  
  > "$D$ (pc) | $\sim$150 | $\sim$140 | $\sim$150 | $\sim$150 | $\sim$180 |" (Table 2); distance from _not stated_
- Target **GSC 6214-210 B**: coordinates _not stated_; z/distance ~150 pc  
  > "$D$ (pc) | $\sim$150 | $\sim$140 | $\sim$150 | $\sim$150 | $\sim$180 |" (Table 2); distance from _not stated_
- Target **1RXS 1609 B**: coordinates _not stated_; z/distance ~150 pc  
  > "$D$ (pc) | $\sim$150 | $\sim$140 | $\sim$150 | $\sim$150 | $\sim$180 |" (Table 2); distance from _not stated_
- Target **CT Cha B**: coordinates _not stated_; z/distance ~180 pc  
  > "$D$ (pc) | $\sim$150 | $\sim$140 | $\sim$150 | $\sim$150 | $\sim$180 |" (Table 2); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00773.S
- bands: Band 6 (1.3 mm) continuum  
  > "We report Atacama Large Millimeter/submillimeter Array (ALMA) 1.3 mm continuum upper limits" (abstract)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15–3247 m (DH Tau, CT Cha); 15–3143 m; 85–14969 m (GQ Lup)  
  > "| DH Tau | 2016 Sep 14 | 36 | 15–3247 | $\sim$13 |" (Table 1)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: rms ~30–50 µJy/beam  
  > "| CT Cha | 2016 Sep 27 | 36 | 15–3247 | $\sim$14 | J1058$-$8003 | J1107$-$4449 | J1107$-$4449 | $0.259\times0.134$ | 16.5 | $\sim$50 |" (Table 1)
- time on source: ~11–14 min per target  
  > "| GSC 6214-210 | 2016 Sep 16 | 36 | 15–3143 | $\sim$12 |" (Table 1)
- observing dates: 2015 Nov 01 to 2016 Sep 27  
  > "| GQ Lup | 2015 Nov 01 | 41 | 85–14969 | $\sim$11 |" (Table 1)
- pi or archival as stated: _not stated_
- External data: Companion properties, accretion rates and literature flux limits (Table 2)  
  > "(1) (cite: W17) and references therein, (2) (cite: M17), (3) (cite: Z14), (4) (cite: K14)" (Table 2) [from (cite: W17); (cite: M17); (cite: Z14); (cite: K14)]
- External data: Dust opacities 3.4 cm2/g at 880 um and 2.3 cm2/g at 1.3 mm  
  > "adopting dust opacities of 3.4 cm$^2$ g$^{-1}$ at 880 $\mu$m and 2.3 cm$^2$ g$^{-1}$ at 1.3 mm from (cite: B90)" (Table 2) [from (cite: B90)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Data self-calibrated  
  > "Data have been self-calibrated and CLEANed with natural weighting." (1. Introduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Data have been self-calibrated and CLEANed with natural weighting." (1. Introduction)
- uv taper: _not stated_
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

- Observational setup and data reduction  
  > "Details on the observational setup and data reduction can be found in (cite: W17) and (cite: WS17)." (1. Introduction) [from (cite: W17); (cite: WS17)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration procedure
- self-calibration solints
- spectral setup and continuum bandwidth
- image size, cell size, clean threshold
- how 3 sigma limits were derived
- coordinates of targets

## Analysis recipe

1. **Derive dust mass limits**: Optically thin dust mass from flux limits, 20 K disk  
  > "Assuming optically thin dust, one can estimate the dust mass from (cite: H83)" (2. Optically-thin Dust and Timescale Problem)
   - parameter: T = 20 K  
  > "assuming a disk temperature of 20 K for all objects" (Table 2)
   - assumption: Optically thin dust, canonical gas-to-dust 100  
  > "If the actual gas-to-dust ratio is lower than the canonical value of 100" (2. Optically-thin Dust and Timescale Problem)
   - fitting: _not stated_
   - validation: _not stated_
2. **Model flux of compact optically thick disks**: Integrate Planck function over irradiated disk temperature profile T(r) (Pringle 1981) vs outer radius  
  > "we can roughly estimate the brightness of an optically-thick disk following (cite: P81)." (3. Compact Optically-thick Disk)
   - parameter: R*=2.5 RJup, Rmin=2R*, Rmax=10 to 1e4 RJup, D=150 pc, T*=2500 and 1000 K  
  > "We adopt $R_\star=2.5~R_{\rm Jup}$" (3. Compact Optically-thick Disk)
   - assumption: Disk heating dominated by companion irradiation  
  > "Assuming disk heating is dominated by the irradiation from the companion" (3. Compact Optically-thick Disk)
   - fitting: _not stated_
   - validation: Compared with ALMA 3 sigma limits  
  > "We also label the 3$\sigma$ flux upper limits from ALMA observations." (3. Compact Optically-thick Disk)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust mass limits for wide companions | 0.002 to 0.14 Mearth | not stated | Mearth | 1 | These flux upper limits translate to a dust mass of 0.002 to 0.14 $M_\oplus$ |
| GQ Lup B disk depletion time | ~20 | not stated | kyr | 1 | GQ Lup B’s accretion disk could potentially disappear in $\sim$20 kyr |
| Upper limit on compact disk radius | <1000 (~0.5 au) | not stated | RJup | 2 | they are probably smaller than 1000 $R_{\rm Jup}$, or $\sim$0.5 au. |

## Qualitative findings

- No companions detected at 1.3 mm in this survey  
  > "As with other studies, no companions are detected in our survey." (1. Introduction)

## Claim tuples

- H: Compact optically thick disks reconcile low radio flux with long accretion lifetimes | E: Compute optically thick disk fluxes versus radius and compare with ALMA limits | R: Disks smaller than ~1000 RJup are fainter than ~100 uJy | F: Compact optically thick disks can sustain accretion yet remain undetected | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): Order-of-magnitude model with no fit to data
- Caveat (inferred, ours): Disk temperature and distance assumptions drive limits
- Caveat (inferred, ours): Optically thick compact disk is not directly tested

## Reproducibility

- Data public (paper): ALMA project code given  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00773.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Reduction details are in companion papers
- Missing: No CASA version or imaging parameters
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Simple limits and analytic model are easy, but reduction details are deferred to other papers.
- Rediscovery candidate: no, Imaging recipe is not given here; the main results are limits and an analytic estimate.

## Links

- Method: (cite: W17) (Observational setup and data reduction)
- Method: (cite: WS17) (Observational setup and data reduction)
- Companion: (cite: M17) (ALMA GQ Lup B limits)

## Checks

```json
{
 "quotes": 32,
 "quotes_ok": 32,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 26,
  "rate": 0.377
 },
 "evidence_ok": true
}
```
