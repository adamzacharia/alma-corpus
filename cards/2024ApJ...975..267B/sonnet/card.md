# Magnetic Field Alignment Relative to Multiple Tracers in the High-mass Star-forming Region RCW 36

`2024ApJ...975..267B` | The Astrophysical Journal 2024 | first author: Bij, Akanksha | arXiv: 2409.03558 | DOI: 10.3847/1538-4357/ad77c7

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, milky_way_ism
- Question: How do magnetic fields (SOFIA HAWC+) and stellar feedback shape gas structure in the bipolar HII region RCW 36, via HRO alignment of many tracers relative to the field?  
  > "we apply the Histogram of Relative Orientations (HRO) method to quantify the relative alignment between the inferred magnetic field and elongated structures observed in several datasets" (abstract)
- Target **RCW 36 (Vela C)**: coordinates _not stated_; z/distance ~900 pc  
  > "using a distance estimate of $\sim 900$ pc for Vela C from (cite: 2020A&A...633A..51Z)" (2.2.1 ALMA); distance from Zucker et al. 2020  
  > "using a distance estimate of $\sim 900$ pc for Vela C from (cite: 2020A&A...633A..51Z)" (2.2.1 ALMA)

## Data provenance

- ALMA projects: 2018.1.01003.S, 2021.1.01365.S
- bands: Band 6 (1.1 mm)  
  > "observations of dust continuum and line emission in Band 6 (1.1 mm) using the ACA with 7-m dishes" (2.2.1 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ACA 7-m and 12-m (C43-1)  
  > "The second ALMA program used the 12-m array in the C43-1 configuration" (2.2.1 ALMA)
- configurations: _not stated_
- baselines: ACA 9-48 m; 12-m 14.6-284 m  
  > "The configuration resulted in a minimum baseline of 14.6 m and a maximum baseline of 284 m." (2.2.1 ALMA)
- angular resolution: ACA ~4.9''; 12-m ~1.2''  
  > "The angular resolution is approximately 1.2$''$ and the maximum recoverable scale is 11.2$''$" (2.2.1 ALMA)
- max recoverable scale: ACA 28''; 12-m 11.2''  
  > "The angular resolution is approximately 4.9$''$ and the maximum recoverable scale is 28$''$" (2.2.1 ALMA)
- sensitivity: ACA 2.15 mJy/beam; 12-m 0.2 mJy/beam (continuum)  
  > "with a continuum sensitivity of 0.2 mJy beam$^{-1}$" (2.2.1 ALMA)
- time on source: ACA 20 min per pointing (87 pointings); 12-m 9.5 min per pointing (26 pointings)  
  > "The average integration time was 9.5 minutes per mosaic pointing." (2.2.1 ALMA)
- observing dates: ACA 22 Apr-14 Jul 2019; 12-m 19 Mar 2022  
  > "The spectroscopic and continuum observations took place on 19 March 2022" (2.2.1 ALMA)
- pi or archival as stated: _not stated_
- Other facility **SOFIA HAWC+**: 89 and 214 micron dust polarization (magnetic field orientation)  
  > "The RCW 36 region was observed by SOFIA/HAWC+ on 6 and 14 June 2018" (2.1.1 SOFIA HAWC+)
- Other facility **Herschel PACS/SPIRE**: dust emission, column density and temperature maps  
  > "we use publicly available archival maps from the *Herschel* Space Observatory" (2.2.2 Herschel)
- Other facility **Spitzer IRAC**: 3.6 and 4.5 micron maps  
  > "we only use data from 3.6 $\mu$m (channel 1) and 4.5 $\mu$m (channel 2) for our HRO analysis" (2.2.3 Spitzer IRAC)
- Other facility **SOFIA upGREAT FEEDBACK, APEX LAsMA, Mopra**: [CII], [OI], CO, HNC, N2H+, C18O line cubes  
  > "we use a myriad of archival spectroscopic line data to probe different chemical, thermal and density conditions" (2.3 Atomic and Molecular Line Maps)
- External data: [CII]/CO line data reduced and smoothed by Bonne et al.  
  > "we use the data reduced by (cite: 2022ApJ...935..171B) who smoothed the \[ C II \] map to 20$''$ and \[ O I \] map to 30$''$ to reduce noise." (2.3.1 SOFIA upGREAT) [from (cite: 2022ApJ...935..171B)]
- External data: Mopra C18O, HNC, N2H+ maps  
  > "which were originally presented in (cite: 2019ApJ...878..110F)" (2.3.4 Mopra) [from (cite: 2019ApJ...878..110F)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: ALMA continuum maps as delivered by QA2, no further reduction  
  > "as delivered by the QA2 (Quality Assurance 2) process, with no further data reduction performed" (2.2.1 ALMA)
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
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- HRO method  
  > "the Histogram of Relative Orientation (HRO) method (cite: 2013ApJ...774..128S; 2017A&A...607A...2S)" (4.1 Histogram of Relative Orientations) [from (cite: 2013ApJ...774..128S; 2017A&A...607A...2S)]
- Oversampling correction of PRS with white-noise maps  
  > "we follow the methodology in (cite: 2019ApJ...878..110F) and correct for oversampling" (4.5 Projected Rayleigh Statistic) [from (cite: 2019ApJ...878..110F)]

### Not stated but needed to reproduce (our reading)

- Continuum frequency/bandwidth of ALMA maps and whether QA2 products are mosaic-corrected
- Exact ALMA product file names
- Spectral line setup of ALMA data
- Coordinates of the field

## Analysis recipe

1. **Build structure maps and B-field orientation**: B-field from HAWC+ Q,U rotated by 90 deg; structure maps from dust, column density, temperature, integrated line intensity; projected to finer grid with 3-sigma cut  
  > "Next, a 3-$\sigma$ signal-to-noise cut is applied to the data points in the structure map $M(x,y)$." (4.3 Projection and Masking)
   - fitting: _not stated_
   - validation: _not stated_
2. **Compute relative orientation angles**: Gaussian derivative kernel gradient, kernel = beam/3 (min 3 pixels), phi histogram in 20 bins  
  > "The size of the Gaussian kernels in angular units $\theta_{G}$ is chosen to be one third of the FWHM angular resolution" (4.4 Calculating the Relative Orientation Angle)
   - fitting: _not stated_
   - validation: _not stated_
3. **Quantify alignment significance**: Projected Rayleigh Statistic corrected by sigma from 1000 white-noise maps; |Zx|>3 significant  
  > "a magnitude of $\lvert Z_{x} \rvert > 3$ is considered statistically significant" (4.5 Projected Rayleigh Statistic)
   - fitting: _not stated_
   - validation: Monte Carlo of measurement errors gives sigma Zx ~0.2-0.3  
  > "In all cases, $Z_{x}$  $Z^{\prime}_{x}$, and $\Tilde{Z}^{\prime}_{x}$ have standard deviations less than 1." (Uncertainty Estimation for the PRS)
4. **Velocity-dependent HRO**: 1 km/s slabs stepped by 0.5 km/s, PRS per slab  
  > "into narrower velocity slabs with a width of 1 km/s. We increment the center velocities $v_{i}$ of each slab by 0.5 km/s" (4.2.2 Velocity Dependent HRO)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **Astropy** : listed software  
  > "Astropy (cite: astropy:2013; astropy:2018; astropy:2022)" (Software)
- **Spectral-Cube** : line cube handling  
  > "Spectral-Cube (cite: 2019zndo...2573901G)" (Software)
- **APLpy** : plotting  
  > "APLpy (cite: 2012ascl.soft08017R)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band C vs Band E mean relative angle | 6.6 | not stated | deg | 2 | This gives a mean relative angle of $\langle\phi\rangle = 6.6^{\circ}$ |
| Zx, Herschel N(H2) vs HAWC+ Band C | -11.0 | 1 | dimensionless | 3 | / *Herschel* / N(H$_2$) / -11.0 / 3.9 / -42.7 / -0.30 / 10447 / |
| Zx, Spitzer 3.6 um | +7.7 | 1 | dimensionless | 3 | / IRAC / 3.6 $\mu$m / +7.7 / 4.1 / +31.1 / +0.08 / 85010 / |
| Zx, ALMA 12m | -1.0 | 1 | dimensionless | 3 | / ALMA 12m / 1.4 mm / -1.0 / 3.8 / -3.8 / -0.01 / 32739 / |
| Zx, [CII] | +0.5 | 1 | dimensionless | 3 | / upGREAT / \[ C II \]  / +0.5 / 4.4 / +2.2 / +0.02 / 9071 / |

## Qualitative findings

- ALMA continuum shows no significant alignment preference, likely due to resolved-out large scales and few points above 3 sigma  
  > "The ALMA continuum maps show no significant preference for either parallel or perpendicular alignment." (5.2 Single Map HRO Results)

## Claim tuples

- H: Do dense-gas and PDR structures align differently relative to the field? | E: HRO with HAWC+ field vs 20 tracers | R: Dense tracers negative Zx; Spitzer and [CII] positive or ~0 | F: Bimodal alignment: dense gas perpendicular, PDR parallel | **supported**
- H: Is the alignment bimodality also kinematic? | E: Velocity-dependent HRO of line cubes | R: Perpendicular at 4-7 km/s, parallel at 8-11 km/s | F: Dense and PDR structures are kinematically distinct | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA continuum resolves out large structures and HAWC+ may not probe the dense cores  
  > "The HAWC+ Band C data is also likely not probing the magnetic field within the dense cores detected by ALMA" (Single Map HRO)
- Caveat (inferred, ours): ALMA plays a minor role and its HRO result is null
- Caveat (inferred, ours): Interpretation relies on plane-of-sky field only

## Reproducibility

- Data public (paper): HAWC+ archival and ALMA project IDs given  
  > "using publicly available archival data from HAWC+" (2.1.1 SOFIA HAWC+)
- Products in archive: _not stated_
- Missing: ALMA continuum maps were QA2 products; details not given
- Missing: No code released
- Data volume (inferred): ~10-50 GB for ALMA; other data small
- Score (inferred): 3/5, HRO method is well specified with equations, but ALMA part is minor and code not released.
- Rediscovery candidate: no, Main results depend on many multi-facility archival maps and reduced data from other papers; ALMA is minor.

## Links

- Method: (cite: 2013ApJ...774..128S) (HRO method)
- Method: (cite: 2018MNRAS.474.1018J) (Projected Rayleigh Statistic)
- Companion: (cite: 2022ApJ...935..171B) ([CII] and CO data reduction and kinematics of RCW 36)
- Related: SOFIA FEEDBACK
- Related: HOBYS
- Related: BLASTPol

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 31,
  "rate": 0.456
 },
 "evidence_ok": true
}
```
