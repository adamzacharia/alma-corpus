# HCN and HNC in the Disk of an Outbursting Young Star, V883 Ori

`2024JKAS...57..163L` | Journal of Korean Astronomical Society 2024 | first author: Lee, Seonjae | arXiv: 2410.15445 | DOI: 10.5303/JKAS.2024.57.2.163

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Can a one-point chemical model of the disk midplane reproduce the observed HCN/HNC abundance ratio in the inner and outer rings of V883 Ori, and what controls it?  
  > "the objective of this paper is to reproduce the observed HCN/HNC abundance ratio in V883 Ori using a chemical model based on the representative physical conditions of V883 Ori" (1 Introduction)
- Target **V883 Ori**: coordinates _not stated_; z/distance 388 pc  
  > "when they are adjusted to a distance of 388 pc (cite: jelee2019)" (2 Previous observations of V883 Ori); distance from (cite: jelee2019)  
  > "when they are adjusted to a distance of 388 pc (cite: jelee2019)" (2 Previous observations of V883 Ori)

## Data provenance

- ALMA projects: 2019.1.00377.S
- bands: Band 6  
  > "project on ALMA Band 6 in Cycle 7" (2 Previous observations of V883 Ori)
- frequencies and spectral setup: spectral resolution 488.281 kHz (~0.55 km/s)  
  > "All spectral windows had spectral resolution of 488.281 kHz ($\sim$0.55 km s$^{-1}$)." (2 Previous observations of V883 Ori)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.14"x0.12" beam  
  > "Both line data had a similar beam size of $\sim$0.14"$\times$0.12"" (2 Previous observations of V883 Ori)
- max recoverable scale: _not stated_
- sensitivity: rms ~2.2 mJy/beam  
  > "the rms noise level of $\sim$2.2 mJy beam$^{-1}$" (2 Previous observations of V883 Ori)
- time on source: _not stated_
- observing dates: November 15, 2021 (HCN and HNC spectral windows)  
  > "The observation of the spectral windows containing HCN and HNC lines was performed on November 15, 2021." (2 Previous observations of V883 Ori)
- pi or archival as stated: ASSAY project, PI Jeong-Eun Lee  
  > "(2019.1.00377.S, PI: Jeong-Eun Lee)" (2 Previous observations of V883 Ori)
- Line: HCN J=3-2 (265.886 GHz)
- Line: HNC J=3-2 (271.981 GHz)
- Line: H13CN J=3-2 (259.011 GHz)
- Line: HN13C J=3-2 (261.263 GHz)
- External data: Disk density model parameters Rc=75 au, Sigma_c=35 g cm-2, gamma=1, hc=0.1, psi=0.25  
  > "from the model of V883 Ori by (cite: Leemker2021)" (3.2 Physical conditions) [from (cite: Leemker2021)]
- External data: Inclination 38.3 deg  
  > "inclination of 38.3° (cite: Cieza2016)" (2 Previous observations of V883 Ori) [from (cite: Cieza2016)]
- External data: Bolometric luminosity ~285 Lsun (current) and ~6 Lsun (pre-burst)  
  > "When we adapt the bolometric luminosity in the current burst phase to be about 285 L$_\odot$ (cite: Strom1993)" (3.2 Physical conditions) [from (cite: Strom1993); (cite: Cieza2016)]
- External data: Reaction barrier energies 200 K (HNC+H) and 20 K (HNC+O) as fiducial  
  > "we adopt the barrier energies of (200K, 20K) as fiducial values, following (cite: Hacar2020)" (3.1 Chemistry) [from (cite: Hacar2020)]
- Simulation/model as data: One-point chemical model using PURE-C subroutine, two phases (0.5 Myr quiescent, 500 yr burst)  
  > "The model consists of two distinct phases, the quiescent phase and the burst phase, with respective timescales of 0.5 million years and 500 years." (3.2 Physical conditions)

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
  > "We used natural weighting to clean the images for a better resolution." (2 Previous observations of V883 Ori)
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
- final beam: ~0.14"x0.12"  
  > "Both line data had a similar beam size of $\sim$0.14"$\times$0.12"" (2 Previous observations of V883 Ori)
- final rms: ~2.2 mJy/beam  
  > "the rms noise level of $\sim$2.2 mJy beam$^{-1}$" (2 Previous observations of V883 Ori)

### Inherited from earlier work

- Observation and data reduction details  
  > "Further details regarding the observation and data reduction can be found in (cite: jelee2024)." (2 Previous observations of V883 Ori) [from (cite: jelee2024)]
- Chemical network, reduced from original by removing 13C and 15N chemistry  
  > "The chemical network has been reduced from the original network used in (cite: shlee2021; shlee2024)" (3.1 Chemistry) [from (cite: shlee2021; shlee2024)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/imaging details (deferred to Lee et al. 2024a)
- Moment-0 integration velocity range and masking
- Continuum subtraction and line-free channels
- PURE-C code availability and exact reduced network file
- Method for deriving the 1.6±0.6 ratio (aperture, peak pixel, uncertainty)
- Dust/gas temperature and grain parameters in chemical model

## Analysis recipe

1. **Make moment-0 maps and radial profiles**: Integrated intensity maps of HCN, HNC, H13CN, HN13C; azimuthally averaged radial profile corrected for inclination  
  > "azimuthally averaged radial distribution of the emission after correction for the inclination of 38.3°" (2 Previous observations of V883 Ori)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive observed HCN/HNC ratio**: Use H13CN/HN13C intensity ratio at HN13C peak as abundance ratio; lower limit in inner ring from 3 sigma HNC  
  > "we assume that the H$^{13}$CN/HN$^{13}$C line intensity ratio of $1.6 \pm 0.6$ represents the abundance ratio between HCN and HNC at the outer ring" (2 Previous observations of V883 Ori)
   - assumption: Isotopologue ratios similar to main species ratios  
  > "it is known that the abundance ratio of HCN/H$^{13}$CN and HNC/HN$^{13}$C are similar at the final stage of dense molecular clouds" (2 Previous observations of V883 Ori)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive gas temperatures from optically thick HCN peak**: Convert peak intensities (48 and 13 mJy/beam) with Planck function; scale pre-burst by (6/285)^(1/4)  
  > "This corresponds to $76\pm3$ K and $25\pm3$ K, converted using the Planck function." (3.2 Physical conditions)
   - assumption: HCN optically thick, emission from midplane  
  > "We assume that the observed HCN and HNC emission originates from the disk midplane." (3.2 Physical conditions)
   - fitting: _not stated_
   - validation: _not stated_
4. **Run one-point chemical model for inner and outer ring**: Time-dependent chemistry at fixed density, temperature, CR, UV=0, quiescent then burst phase; vary barriers, UV and CR  
  > "The subroutine for chemical calculations can solve the chemical evolution in a specific physical condition of the density and temperature of gas and dust, cosmic ionization rate, and UV flux." (3.1 Chemistry)
   - software: PURE-C
   - parameter: n=2.2e10 (inner), 6.0e7 cm-3 (outer); CR 1e-17 s-1 fiducial  
  > "$2.2\times 10^{10}$ cm$^{-3}$ and $6.0\times 10^7$ cm$^{-3}$, respectively" (3.2 Physical conditions)
   - assumption: UV fully shielded in midplane; CR uniform; burst only affects temperature  
  > "We assume that the accretion burst only affects the disk temperature, without altering the density structure." (3.2 Physical conditions)
   - fitting: No formal fit; compare modeled ratio to observed  
  > "we assume that the H$^{13}$CN/HN$^{13}$C line intensity ratio of $1.6 \pm 0.6$ represents the abundance ratio between HCN and HNC at the outer ring and seek to reproduce this ratio using our chemical model." (Previous observations of V883 Ori)
   - validation: Compared with observed ratios; tested high (KIDA) barriers, UV and CR variations  
  > "The barrier energies from KIDA (cite: Wakelam2012), which are 2000 K for [\[reacH\]](#reacH) and 1130 K for [\[reacO\]](#reacO), were tested." (5.1 Effect of barrier energies in reactions)

## Software

- **PURE-C** : One-point chemical calculation  
  > "we use a subroutine of PURE-C" (3.1 Chemistry)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H13CN/HN13C intensity ratio, outer ring | 1.6 | 0.6 | dimensionless | 2 | The H$^{13}$CN/HN$^{13}$C intensity ratio in that point is $1.6 \pm 0.6$. |
| HCN/HNC intensity ratio lower limit, inner ring | ~10 | not stated | dimensionless | 2 | the lower limit of the HCN/HNC intensity ratio is approximately 10 |
| Post-burst gas temperature inner/outer ring | 76 / 25 | ±3 / ±3 | K | 3 | $76\pm3$ K and $25\pm3$ K |
| Pre-burst temperature inner/outer ring | 29 / 10 | ±2 / ±2 | K | 3 | $29\pm2$ K and $10\pm2$ K, respectively |
| Modeled HCN/HNC ratio, outer ring | ~2 | not stated | dimensionless | 4 | the HCN/HNC abundance ratio remains at the low level of $\sim$2 |

## Qualitative findings

- HCN/HNC in inner ring set by ice sublimation after burst plus HNC conversion by H and O; outer ring ratio unchanged by burst  
  > "The ice abundance ratio between HCN and HNC is intrinsically large, resulting in a high abundance ratio in gas after sublimation." (5 Conclusion)

## Claim tuples

- H: Chemical model with low barrier energies reproduces observed ratios in both rings | E: One-point chemistry for both rings with burst | R: High ratio in inner ring, ~2 in outer ring | F: Ratios reproduced; inner ring ratio from ice sublimation and conversion reactions | **supported**
- H: Theoretical high barrier energies are consistent with non-detection of HNC in inner ring | E: Model with KIDA barriers | R: Gas HNC ~2e-12 vs ~1e-15, so HNC should be detectable | F: Barrier energies must be lower than theoretical values | **supported**
- H: UV and CR affect the ratio | E: Vary UV (0.1 Draine) and CR (1e-16, 1e-18) | R: Ratio largely unchanged | F: Ratio less sensitive to UV and CR than to density or temperature | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: High (KIDA) barrier energies rejected because they predict detectable HNC in the inner ring  
  > "the HNC line emission should be detected, which is not in accordance with our observational results" (5.1 Effect of barrier energies in reactions)
- How they decided it was enough: _not stated_
- Limitation (authors): Simple one-point model; no 2D ring structure or absolute column densities; lines may be optically thick  
  > "We do not intend to reproduce the 2D ring structures observed in the HCN and HNC emission or the absolute column densities of the molecules." (3 Model)
- Caveat (inferred, ours): Observed ratio rests on a single-point isotopologue intensity ratio with assumed equal fractionation
- Caveat (inferred, ours): Midplane assumption for HCN emission is weakly justified
- Caveat (inferred, ours): Temperatures from brightness of possibly non-thermalised lines
- Caveat (inferred, ours): Only fiducial barrier pair tested at low values; no fit or parameter uncertainty

## Reproducibility

- Data public (paper): ALMA project 2019.1.00377.S acknowledged; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.00377.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: PURE-C code and network
- Missing: Reduction scripts and CASA version
- Missing: Moment integration ranges
- Data volume (inferred): ~50-100 GB raw for the project
- Score (inferred): 3/5, Observational part is brief and defers to a prior paper; the model code is not released, though inputs are tabulated.
- Rediscovery candidate: no, Main results depend on unreleased chemical code and deferred data reduction.

## Links

- Method: (cite: jelee2024) (Observation and data reduction details)
- Method: (cite: shlee2021; shlee2024) (PURE-C chemical network)
- Companion: (cite: jelee2024) (ASSAY V883 Ori observations)
- Related: ASSAY (ALMA Spectral Survey of An eruptive Young star, V883 Ori)

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
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
  "facts": 70,
  "stated": 34,
  "rate": 0.486
 },
 "evidence_ok": true
}
```
