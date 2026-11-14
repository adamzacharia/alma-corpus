# An ALMA survey for disks orbiting low-mass stars in the TW Hya Association

`2015A&A...582L...5R` | Astronomy and Astrophysics 2015 | first author: Rodriguez, David R. | arXiv: 1509.04589 | DOI: 10.1051/0004-6361/201527031

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Do low-mass (M-type) members of the ~8 Myr TW Hya Association retain cold dust and molecular gas disks?  
  > "with the goal of detecting molecular gas in the form of CO emission, as well as providing constraints on continuum emission due to cold dust." (abstract)
- Target **TWA 34**: coordinates 10:28:45 -28:30:37  
  > "| TWA 34 | 10:28:45 | -28:30:37 | M5 | 1.35 | 2.75 | Y | $47.0\pm5.6$ | $0.54\pm0.06$ | 2.5 | 4 |" (Table 1); z/distance 47.0±5.6 pc  
  > "At a distance of $47.0\pm5.6$ pc and using the proper motions listed in PPMXL" (TWA 34: System Velocity); distance from _not stated_
- Target **TWA 30B, TWA 32, TWA 33 and 11 other low-mass TWA members/candidates**: coordinates see Table of targets (RA/Dec per target)  
  > "We carried out an ALMA survey of 15 members or proposed members of the TWA" (Observations); z/distance 33-92 pc per target (Table)  
  > "We carried out an ALMA survey of 15 members or proposed members of the TWA" (Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00457.S
- bands: _not stated_
- frequencies and spectral setup: continuum at 230 GHz; 12CO(2-1) and 13CO(2-1) with 488 kHz resolution (0.6 km/s)  
  > "observations of the $^{12}$CO(2–1) and $^{13}$CO(2–1) emission lines with a resolution of 488 kHz, corresponding to a velocity resolution of 0.6 km/s" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: average 1.5x0.8 arcsec beam, 40-80 AU  
  > "The final restored beam was, on average, $1.5\times0.8$$''$ and corresponds to a scale of 40–80 AU" (Observations)
- max recoverable scale: _not stated_
- sensitivity: 0.05 mJy/beam continuum; 5 mJy/beam per 0.6 km/s channel in CO  
  > "We reached a sensitivity of 0.05 mJy/beam in the continuum and 5 mJy/beam per 0.6 km/s channel in $^{12}$CO and $^{13}$CO." (Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Other facility **WISE and Herschel**: infrared excess information for the targets  
  > "most are known to host dusty circumstellar disks as inferred via WISE and Herschel infrared excesses" (Observations)
- External data: Stellar mass of TWA 34, 0.08 Msun  
  > "where $M_*$ is the mass of the star, 0.08 $M_\odot$ (cite: Baraffe:2015)" (3.1 TWA 34: CO Detection) [from (cite: Baraffe:2015)]
- External data: Dust opacity kappa = 1.15 cm2/g  
  > "where we adopt $\kappa_\nu = 1.15$ cm$^2$/g (see (cite: Rodriguez:2010) and references therein)" (Results) [from (cite: Rodriguez:2010)]
- External data: Proper motions of TWA 34 from PPMXL  
  > "using the proper motions listed in PPMXL (cite: Roeser:2010)" (3.2 TWA 34: System Velocity) [from (cite: Roeser:2010)]
- External data: Average UVW velocity of the TWA  
  > "average velocity of the TWA ($-9.87$, $-18.06$, $-4.52$ km/s; (cite: Malo:2013))" (3.2 TWA 34: System Velocity) [from (cite: Malo:2013)]

## Processing

### Calibration

- pipeline or manual: calibration done by ALMA staff  
  > "Calibration and cleaning was performed by the ALMA staff with CASA version 4.2.2." (Observations)
- casa version: CASA 4.2.2  
  > "Calibration and cleaning was performed by the ALMA staff with CASA version 4.2.2." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust=0.5  
  > "Briggs weighting was used with robust=0.5." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: fluxes measured from primary-beam-corrected images  
  > "along with the measured flux from the primary beam corrected images" (Results)
- array combination: _not stated_
- smoothing: Hanning smoothing, 3-channel kernel (CO spectrum)  
  > "Hanning smoothed with a kernel size of 3 channels" (3.1 TWA 34: CO Detection)
- final beam: 1.5x0.8 arcsec on average  
  > "The final restored beam was, on average, $1.5\times0.8$$''$" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Parametric Keplerian line profile fit  
  > "we fit a parametrized Keplerian model as described in (cite: Kastner:2008a)" (3.1 TWA 34: CO Detection) [from (cite: Kastner:2008a)]
- Gas mass prescription  
  > "We estimate a gas mass of $\sim$0.2 $M_E$ following the prescriptions of (cite: Zuckerman:2008), (cite: Kastner:2008a), (cite: Rodriguez:2010)" (3.1 TWA 34: CO Detection) [from (cite: Zuckerman:2008), (cite: Kastner:2008a), (cite: Rodriguez:2010)]

### Not stated but needed to reproduce (our reading)

- CASA clean parameters (cell, image size, masks, threshold, deconvolver)
- Line-free channels and continuum subtraction method
- Gaussian-fit procedure and fitting region
- SED photometry and blackbody fitting details
- Fitting method/uncertainty treatment for the line profile
- Moment-map construction parameters
- Array configurations and observing dates

## Analysis recipe

1. **Measure continuum fluxes and limits**: Gaussian fit to cleaned primary-beam-corrected images; 3-sigma limits from 3x RMS  
  > "Fluxes were measured by fitting a Gaussian to the cleaned image." (Results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive dust masses**: Optically thin M_dust = F D^2 / (kappa B(T))  
  > "Assuming optically thin dust, we can estimate the dust mass from:" (Results)
   - assumption: kappa=1.15 cm2/g, T_dust=40 K  
  > "where we adopt $\kappa_\nu = 1.15$ cm$^2$/g (see (cite: Rodriguez:2010) and references therein) and $T_{dust}=40$ K." (Results)
   - fitting: _not stated_
   - validation: SED blackbody fits consistent with ~40 K  
  > "The measured fluxes are consistent with emission from T$\sim$40 K dust grains as determined by modeling the spectral energy distribution (SED)." (Results)
3. **Fit TWA 34 CO line profile**: Parametric Keplerian profile fit to integrated spectrum; outer radius from v_d^2=GM/R_d  
  > "We fix $q$=0.5 and $p_d$=0.1 for simplicity." (3.1 TWA 34: CO Detection)
   - parameter: q=0.5, p_d=0.1 fixed  
  > "We fix $q$=0.5 and $p_d$=0.1 for simplicity." (3.1 TWA 34: CO Detection)
   - fitting: _not stated_
   - validation: _not stated_
4. **Estimate gas mass**: Optically thin 13CO upper limit prescription  
  > "We assume optically thin $^{13}$CO, a $^{12}$C:$^{13}$C ratio of 89, a CO:H$_2$ ratio of 10$^{-4}$, temperature of $\sim$40 K" (3.1 TWA 34: CO Detection)
   - assumption: 12C:13C=89, CO:H2=1e-4, T~40 K  
  > "a $^{12}$C:$^{13}$C ratio of 89, a CO:H$_2$ ratio of 10$^{-4}$, temperature of $\sim$40 K" (3.1 TWA 34: CO Detection)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.2: calibration and cleaning by ALMA staff  
  > "Calibration and cleaning was performed by the ALMA staff with CASA version 4.2.2." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| TWA 34 continuum flux | 0.54 | 0.06 | mJy | 1 | / TWA 34 / 10:28:45 / -28:30:37 / M5 / 1.35 / 2.75 / Y / $47.0\pm5.6$ / $0.54\pm0.06$ / 2.5 / 4 / |
| TWA 32 continuum flux | 2.10 | 0.05 | mJy | 1 | $2.10\pm0.05$ / 15.8 / 3, 5 / |
| 12CO integrated intensity TWA 34 | 0.34 | 0.03 | Jy km/s | 3 | an integrated intensity of $0.34\pm0.03$ Jy km/s |
| Systemic velocity (LSR) | 2.3 | 0.1 | km/s | 3 | a systemic velocity of $2.3\pm0.1$ km/s in the LSR frame |
| v_d | 2.49 | 0.09 | km/s | 3 | $v_d$ of $2.49\pm0.09$km/s |
| CO disk outer radius | ~11 | not stated | AU | 3 | We thereby estimate the CO disk orbiting TWA 34 is $\sim$11 AU in radius. |
| Gas mass TWA 34 | ~0.2 | not stated | Earth masses | 4 | We estimate a gas mass of $\sim$0.2 $M_E$ |
| Barycentric systemic velocity TWA 34 | 13.3 | 0.1 | km/s | 3 | this velocity corresponds to $13.3\pm0.1$ km/s |

## Qualitative findings

- Warm dust does not necessarily imply cold dust is present  
  > "the presence of warm circumstellar dust does not necessarily imply cold dust is also present in the system" (Discussion)

## Claim tuples

- H: Low-mass TWA members host cold dust disks | E: 1.3 mm continuum survey of 15 targets | R: 4 detections, all unresolved; dust masses ~1-16% Earth mass | F: Cold dust is present in only a minority despite warm excesses | **supported**
- H: Low-mass TWA members retain molecular gas | E: 12CO(2-1) and 13CO observations | R: Only TWA 34 detected, double-peaked Keplerian profile | F: TWA 34 is the lowest-mass star known with a cold gas disk at ~7-10 Myr | **supported**
- H: TWA 34 is a TWA member | E: Systemic velocity and UVW from CO | R: UVW consistent with TWA average | F: Supports membership | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Dust temperature from Andrews 2013 relation (~8 K) would give 5x higher dust masses; not adopted  
  > "This is 5 times lower than the temperatures assumed in the SED model and, under the same assumptions, implies dust masses that are 5 times higher." (Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas mass uncertain; CO radius estimates discrepant; higher resolution needed  
  > "Higher resolution CO imaging will allow an independent measurement of the disk size" (3.1 TWA 34: CO Detection)
- Caveat (inferred, ours): Dust masses depend strongly on assumed T=40 K
- Caveat (inferred, ours): Unresolved data; CO radius of 11 AU vs 20-40 AU discrepancy
- Caveat (inferred, ours): Gas mass relies on 13CO upper limit and assumed abundances
- Caveat (inferred, ours): Table coordinates for TWA 34 Dec are inconsistent

## Reproducibility

- Data public (paper): ALMA Cycle 2 data cited by project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00457.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Line-free channels
- Missing: SED data and fitting details
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Simple recipe with few imaging details but numeric tables given.
- Rediscovery candidate: yes, Data are from a Cycle 2 project and flux/dust-mass/CO results are numeric and simple to redo.

## Links

- Method: (cite: Kastner:2008a) (Keplerian line profile fit and gas mass prescription)
- Related: BANYAN II

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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 34,
  "rate": 0.472
 },
 "evidence_ok": true
}
```
