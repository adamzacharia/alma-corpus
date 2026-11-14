# Sequential planet formation in the HD 100546 protoplanetary disk?

`2015A&A...580A.105P` | Astronomy and Astrophysics 2015 | first author: Pinilla, P. | arXiv: 1506.02383 | DOI: 10.1051/0004-6361/201425539

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: What do dust evolution models with one or two massive planets imply for the age and sequential formation of planets in HD 100546, given the ALMA/ATCA continuum visibilities?  
  > "Our aims are to provide constraints on the age of the planets in HD 100546 and to explore the potential evidence for sequential planet formation in transition disks such as HD 100546." (abstract)
- Target **HD 100546**: coordinates _not stated_; z/distance 103 pc  
  > "the disk is taken to be at a distance of 103 pc with an inclination ($i$) of $45^\circ$ (cite: vandenAncker1997), and a position angle (P.A.) of $146^\circ$ (east from north)." (2.4 Set-up); distance from van den Ancker et al. 1997  
  > "the disk is taken to be at a distance of 103 pc with an inclination ($i$) of $45^\circ$ (cite: vandenAncker1997), and a position angle (P.A.) of $146^\circ$ (east from north)." (2.4 Set-up)

## Data provenance

- ALMA projects: 2011.0.00863.S
- bands: ALMA Cycle 0 870 micron continuum (data from Walsh et al. 2014)  
  > "Moreover, ALMA Cycle 0 data at this wavelength are also plotted for comparison." (3.1 No planets in the disk)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **ATCA**: 3 and 7 mm visibilities from Wright et al. 2015 for comparison  
  > "ALMA Cycle 0 data from (cite: walsh2014) and ATCA data from (cite: wright2015) are over-plotted for comparison." (3.2 A planet is embedded in the inner disk)
- External data: ALMA Cycle 0 870 micron visibilities and CO J=3-2 disk extent  
  > "ALMA Cycle 0 data from (cite: walsh2014) and ATCA data from (cite: wright2015) are over-plotted for comparison." (3.2 A planet is embedded in the inner disk) [from Walsh et al. 2014 (cite: walsh2014)]
- External data: Disk temperature profile (T20AU~100 K, T400AU~25 K)  
  > "We use a temperature profile specific for HD 100546 and derived by (cite: bruderer2012)" (2.4 Set-up) [from Bruderer et al. 2012 (cite: bruderer2012)]
- External data: ATCA 3 and 7 mm visibilities  
  > "ATCA data from (cite: wright2015) are over-plotted for comparison." (3.2 A planet is embedded in the inner disk) [from Wright et al. 2015 (cite: wright2015)]
- Simulation/model as data: FARGO hydrodynamical simulations used to benchmark analytical gap shapes  
  > "Fig. 1 displays the comparison of the gas surface density between hydrodynamical simulations done with `FARGO` (cite: masset2000)" (2.1 Carved gaps)

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

- Dust evolution model formulation  
  > "To model the dust evolution, we use the formulation of (cite: birnstiel2010)." (2.2 Dust evolution and radial gas velocity) [from Birnstiel et al. 2010 (cite: birnstiel2010)]
- Viscosity alpha values  
  > "with $\alpha=[2\times10^{-3}, 5\times10^{-3}]$ as in (cite: mulders2013)" (2.4 Set-up) [from Mulders et al. 2013 (cite: mulders2013)]

### Not stated but needed to reproduce (our reading)

- Dust evolution code and its numerical grid not released
- uv coverage and visibility binning used for the ALMA comparison
- Stellar luminosity or other quantities beyond the temperature profile
- Exact injection prescription for later planets

## Analysis recipe

1. **Model planet gaps**: Analytical gap profile (Crida width, Fung depth), benchmarked against FARGO  
  > "We imitate the gas gaps carved by massive planets by solving Eq ([\[crida_solution\]](#crida_solution)) and correcting the depth of the gap with the empirical scalings (cite: fung2014), between $-2r_H<r-r_p<2r_H$." (2.1 Carved gaps)
   - software: FARGO
   - fitting: _not stated_
   - validation: Compared with FARGO  
  > "this approximation for the shape of the gaps is very good for the case of $q=1\times10^{-3}$." (2.1 Carved gaps)
2. **Evolve dust**: Dust growth, fragmentation and drift with 180 grain sizes  
  > "We investigate the evolution of 180 species of dust grains, defined by size from 1 $\mu$m to 200 cm." (2.2 Dust evolution and radial gas velocity)
   - parameter: vf=10 m/s, rho_s=1.2 g/cm3, disk mass 0.05 Msun  
  > "the so-called fragmentation velocity, is $\varv_f=10~\rm{m~s}^{-1}$." (2.4 Set-up)
   - fitting: _not stated_
   - validation: _not stated_
3. **Compute and compare visibilities**: Real part of visibilities from Mie opacities, compared by eye with ALMA and ATCA data  
  > "we calculate the real part of the visibilities in the $uv$-plane" (2.3 Visibilities at mm-wavelenghts)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **FARGO** : Hydrodynamical benchmark of gap shapes  
  > "hydrodynamical simulations done with `FARGO` (cite: masset2000)" (2.1 Carved gaps)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Best single inner planet mass | ~20 | not stated | MJup | 3 | very massive planet ($\sim20~M_{\rm{Jup}}$), which formed early in the inner disk ($r\sim$10 AU) |
| Age of disk for single-planet case | ~5-10 | not stated | Myr | 3 | the disk is likely to be old, comparable to the stellar age ($\sim$5-10 Myr). |

## Qualitative findings


## Claim tuples

- H: Can radial drift alone explain the HD 100546 mm emission? | E: No-planet dust evolution models vs ALMA visibilities | R: Mm flux drops after 1 Myr | F: A pressure bump is needed | **supported**
- H: Is the outer planet younger than the inner one? | E: Two-planet models with simultaneous vs later outer injection | R: A massive outer planet needs later injection | F: The outer planet is at least ~2-3 Myr younger | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Analytical gaps underestimate the gap width for very massive planets, so the outer ring is not as extended as observed  
  > "The latter scenario reproduces a more extended emission than with a single planet, but it is not as extended as observed." (4 Discussion)
- Caveat (inferred, ours): Fits are qualitative with no formal fitting
- Caveat (inferred, ours): Degeneracy with disk mass, temperature and dust composition
- Caveat (inferred, ours): Free-free at 7 mm neglected

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Dust evolution code not provided
- Missing: No numeric fit metrics
- Data volume (inferred): small; only published visibility profiles needed
- Score (inferred): 2/5, Theory paper; ALMA data only used as a comparison and the models are not reproducible from the text
- Rediscovery candidate: no, Results come from custom simulations compared by eye and are not numeric ALMA measurements.

## Links

- Method: Birnstiel et al. 2010 (dust evolution model)
- Method: Crida et al. 2006; Fung et al. 2014 (gap shape prescriptions)
- Companion: Walsh et al. 2014 (ALMA Cycle 0 data of HD 100546)

## Checks

```json
{
 "quotes": 24,
 "quotes_ok": 24,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 62,
  "stated": 18,
  "rate": 0.29
 },
 "evidence_ok": true
}
```
