# A Hunt for Massive Starless Cores

`2017ApJ...834..193K` | The Astrophysical Journal 2017 | first author: Kong, Shuo | arXiv: 1609.06008 | DOI: 10.3847/1538-4357/834/2/193

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: Are there massive starless/early-stage cores in IRDCs, identified via strong N2D+(3-2) emission, and are their dynamics consistent with virial equilibrium of pressure-confined cores?  
  > "with the aim of finding massive starless cores, which may be the initial conditions for the formation of massive stars." (abstract)
- Target **32 IRDC clumps in IRDCs A, B, C, D, E, F, H (30 pointings)**: coordinates Table 1 lists RA/Dec and l,b per clump (e.g., A1 18h26m15.14s -12d41m43.4s)  
  > "we observed 32 more clumps from the BT12 sample (listed in Table [1](#tab:obs)), focusing on IRDCs A, B, C, D, E, F and H." (Sample Selection and ALMA Observations); "| A1 | $\rm 18^h26^m15.14s$ | $\rm -12\ensuremath{^\circ}41\ensuremath{'}43.4\ensuremath{''}$ | 18.78675 | -0.28592 | 66 | 4.8 |" (Table 1); z/distance 2.4-5.7 kpc (per IRDC, Table 1)  
  > "we observed 32 more clumps from the BT12 sample (listed in Table [1](#tab:obs)), focusing on IRDCs A, B, C, D, E, F and H." (Sample Selection and ALMA Observations); "| A1 | $\rm 18^h26^m15.14s$ | $\rm -12\ensuremath{^\circ}41\ensuremath{'}43.4\ensuremath{''}$ | 18.78675 | -0.28592 | 66 | 4.8 |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00806.S
- bands: Band 6  
  > "Dual polarization mode was adopted for the Band 6 spectral setup." (Sample Selection and ALMA Observations)
- frequencies and spectral setup: Seven spectral windows: N2D+(3-2) 231.32 GHz (0.05 km/s), continuum at 231.00 GHz, C18O(2-1) 219.56 GHz (0.05 km/s), DCO+ 216.11, CH3OH 216.95, SiO 217.10, DCN 217.24 GHz (0.2 km/s)  
  > "A Baseband 1 single spectral window was centered on $\rm N_2D^+$(3-2) (rest frequency 231.32 GHz), with a velocity resolution of 0.05 $\rm km\:s^{-1}$." (Sample Selection and ALMA Observations)
- continuum bandwidth: about 2 GHz  
  > "The total bandwidth for this baseband is about 2 GHz." (Sample Selection and ALMA Observations)
- arrays: 12m array only, no ACA  
  > "No ACA observations were performed." (Sample Selection and ALMA Observations)
- configurations: most compact configuration  
  > "with the 12m array in the most compact configuration." (Sample Selection and ALMA Observations)
- baselines: 12 m to 330 m (9-254 klambda)  
  > "The baselines were from 12 m to 330 m (9-254 k$\lambda$)" (Sample Selection and ALMA Observations)
- angular resolution: 1.5'' x 1.0''  
  > "resulting in a synthesized beam size of 1.5$''$ $\times$ 1.0$''$" (Sample Selection and ALMA Observations)
- max recoverable scale: ~20''  
  > "a maximum detectable scale of $\sim$20$''$" (Sample Selection and ALMA Observations)
- sensitivity: Line: 22 (Track 1) and 30 (Track 2) mJy/beam per 0.1 km/s; continuum 0.22 mJy/beam  
  > "In the end, Track 1 has sensitivity of 22 mJy beam$^{-1}$ per 0.1 $\rm km\:s^{-1}$." (Sample Selection and ALMA Observations); "The continuum sensitivity we achieve now is 0.22 mJy beam$^{-1}$" (Sample Selection and ALMA Observations)
- time on source: _not stated_
- observing dates: April 2015  
  > "The observations were carried out during April 2015" (Sample Selection and ALMA Observations)
- pi or archival as stated: Cycle 2, PI Tan  
  > "With ALMA in Cycle 2 (Project number: 2013.1.00806.S; PI: Tan)" (Sample Selection and ALMA Observations)
- Line: N2D+ 3-2 (231.32 GHz)
- Line: C18O 2-1 (219.56 GHz)
- Line: DCO+ 3-2 (216.11 GHz)
- Line: DCN 3-2 (217.24 GHz)
- Line: SiO 5-4 (217.10 GHz)
- Other facility **Spitzer MIREX maps**: Mid-IR extinction mass surface density maps used for target selection and core mass estimates  
  > "First we use the MIREX map of BT12." (Core Masses)
- Other facility **Herschel 70 micron**: Checked for 70 micron counterparts of cores  
  > "We checked the Herschel 70 $\rm \mu m$ image in this area." (Notes on Individual Cores)
- External data: MIREX mass surface density maps and clump sample  
  > "BT12 characterized 42 high $\Sigma$ clumps selected from 10 IRDCs (A-J)" (Introduction) [from Butler & Tan 2009, 2012 (cite: 2009ApJ...696..484B; 2012ApJ...754....5B)]
- External data: Dust opacity kappa_nu = 5.95e-3 cm^2/g  
  > "adopt $\kappa_\nu = 5.95\times10^{-3}\:{\rm cm^2\:g}^{-1}$ (cite: 1994A&A...291..943O)." (Core Masses) [from (cite: 1994A&A...291..943O)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune (Track 1), Titan (Track 2)  
  > "Neptune was the flux calibrator." (Sample Selection and ALMA Observations); "Titan was the flux calibrator." (Sample Selection and ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: none  
  > "No self-calibration was done to the dataset." (Sample Selection and ALMA Observations)

### Imaging

- task: continuum cleaned; line data not cleaned  
  > "The continuum data were cleaned, while the line data were not cleaned due to their relatively weak detections." (Sample Selection and ALMA Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied before fluxes extracted; core search done before correction  
  > "Primary beam correction was applied before fluxes were extracted." (Sample Selection and ALMA Observations)
- array combination: _not stated_
- smoothing: N2D+ cubes smoothed to 0.15 km/s  
  > "we settle on a choice of a velocity resolution of 0.15 $\rm km\:s^{-1}$" (Core Detection Analysis Methods)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Core mass, virial dynamics (equations 2, 4, 7), 5 km/s moment range, temperature 10±3 K and mu=2.33 mp follow T13  
  > "Following the methods of T13, we measure core masses, $M_c$, within the Case 1 and Case 2 ellipses in two ways." (Core Masses) [from Tan et al. 2013 (cite: 2013ApJ...779...96T)]
- Virialized pressure-confined turbulent core model  
  > "Following T13 and MT03, we consider virialized singular polytropic quasi-spherical cores" (Core Dynamics) [from McKee & Tan 2003 (cite: 2003ApJ...585..850M)]
- MIREX maps  
  > "First we use the MIREX map of BT12." (Core Masses) [from BT12 (cite: 2012ApJ...754....5B)]

### Not stated but needed to reproduce (our reading)

- Calibration pipeline/CASA version and manual vs pipeline
- Continuum imaging parameters (robust, cell, image size, masks, line-free channels)
- Minimum voxel count used in core finding
- Exact equations from T13 (eq 2, 4, 7) not reproduced
- Flux scale uncertainty
- Continuum bandwidth/channels used and noise in each field

## Analysis recipe

1. **Find N2D+ cores**: Connected components of voxels >=3 sigma in PPV cube (NetworkX graph), plus positive-flux neighbors; requires >=2 channels and detection in cube shifted by 0.075 km/s  
  > "We start by identifying cores as connected groups of “voxels” (pixels in 3D position-position-velocity (PPV) space of $l-b-v$) with flux densities of $\geq 3\sigma$" (Core Detection Analysis Methods)
   - software: NetworkX
   - parameter: 0.15 km/s resolution; sigma 0.020 (Track 1) / 0.030 (Track 2) Jy/beam; search within 26'' FOV  
  > "which has $\sigma\simeq0.020\:$$\rm Jy\:bm^{-1}\:$for IRDCs A, B, C, E (Track 1)" (Core Detection Analysis Methods)
   - fitting: _not stated_
   - validation: Compared with yt clumpfind in B1 region; checks with continuum, DCO+, C18O  
  > "then yt finds all B1 cores given by our method." (Core Detection Analysis Methods)
2. **Measure core sizes**: Fit 2D elliptical Gaussians to N2D+ integrated intensity; Case 1 ellipse at 3 sigma, Case 2 larger ellipse  
  > "we fit 2D elliptical Gaussians to the $\rm N_2D^+$(3-2) integrated intensity maps." (Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure line velocity dispersion**: Extract spectrum in Case 1 ellipse, fit hyperfine structure with CLASS HFS assuming optically thin; subtract thermal in quadrature at 10 K and add core sound speed  
  > "utilizing the HFS method of the CLASS software package" (Core Kinematics)
   - software: CLASS
   - assumption: optically thin; T = 10±3 K; mu = 2.33 mp  
  > "assuming a mean particle mass $\mu = 2.33 m_p$ and gas temperature of 10$\pm$3 K, following T13." (Core Kinematics)
   - fitting: CLASS HFS  
  > "We then fit the $\rm N_2D^+$(3-2) line with full blended hyperfine components," (Core Kinematics)
   - validation: _not stated_
4. **Derive core masses**: Mass from 1.3 mm dust continuum (fiducial) and from MIREX (with/without envelope subtraction)  
  > "we prefer the mm continuum based mass estimate as our fiducial method." (Core Masses)
   - assumption: Td = 10±3 K, kappa = 5.95e-3 cm^2/g with 30% uncertainty, distance from Table 1  
  > "assume a dust temperature of $T_d = 10 \pm
  3$ K" (Core Masses)
   - fitting: _not stated_
   - validation: Compared MIREX and mm masses  
  > "because of the difficulties of clump envelope subtraction in the MIREX mass estimates, we prefer the mm continuum based mass estimate as our fiducial method." (Core Masses)
5. **Virial analysis**: Compare observed sigma to predicted virial sigma of MT03 pressure-confined core; derive B-field needed  
  > "The two quantities are calculated following T13 equations (2) and (4), given core mass $M_c$ and clump mass surface density $\Sigma_{\rm cl}$." (Core Dynamics)
   - fitting: _not stated_
   - validation: Compared with T13 ratio 0.83  
  > "This is very similar to the result found by T13 of a ratio of 0.83 for the six cores they analyzed." (Core Dynamics)

## Software

- **NetworkX** : graph connected components for core finding  
  > "using the NetworkX package (cite: hagberg-2008-exploring), we identify all connected components in the graph" (Core Detection Analysis Methods)
- **yt** : clumpfind comparison  
  > "We have thus compared it with the “clumpfind” method in the yt package" (Core Detection Analysis Methods)
- **CLASS (GILDAS)** : hyperfine fit of N2D+ spectra  
  > "utilizing the HFS method of the CLASS software package" (Core Kinematics)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of N2D+ cores | 141 | not stated | cores | 1 | In total 141 $\rm N_2D^+$(3-2) cores are found in the 30 data cubes |
| C9A mass (Case 1, mm) | 69.7 | +76/-38 (31.7 to 146) | Msun | 4 | C9A is the most massive of the six cores suitable for dynamical analysis, with $M_{c,{\rm mm}}\simeq
70\:M_\odot$ in the Case 1 |
| C9A mass (Case 2, mm) | 170 | 77.6 to 357 | Msun | 4 | C9A rises in mass to $M_{c,{\rm mm}}\simeq
170\:M_\odot$. |
| Mean sigma_obs/sigma_vir (mm) | 0.80 | 0.742 to 0.882 | dimensionless | 5 | $\langle \sigma_{\rm N_2D^+}/\sigma_{\rm
  c,vir,mm}\rangle = 0.80$ |
| C9A sigma ratio | 0.71 | 0.588 to 0.890 | dimensionless | 5 | The most massive core, C9A, has a ratio of 0.71, which is modestly subvirial. |
| N2D+ velocity dispersion range | 0.26 to 0.61 | not stated | km/s | 3 | ranging from 0.26 to 0.61 $\rm km\:s^{-1}$ |
| C9A velocity gradient | ~20 | not stated | km/s/pc | 0 | so the velocity gradient is $\sim$20 $\rm km\:s^{-1}~$ pc$^{-1}$ |
| 1 sigma mass sensitivity | 0.51 | not stated | Msun | 4 | the 1$\sigma$ mass sensitivity is 0.51$\:M_\odot$ |

## Qualitative findings

- Cores show dearth of C18O, consistent with CO depletion; some cores (C9A, C9B, D5A, C3A, C5A) have weak DCO+  
  > "there is often a dearth of $\rm C^{18}O$(2-1) emission associated with the $\rm N_2D^+$(3-2) cores" (Identified N2D+ Cores)
- C9A shows complex kinematics, possibly two merging cores; weak SiO counterpart leaves starless nature uncertain  
  > "it is possible that we are seeing two $\rm N_2D^+$(3-2) cores in the process of merging." (Core Kinematics)

## Claim tuples

- H: Massive starless/early-stage cores exist in IRDCs | E: N2D+(3-2) and 1.3 mm survey of 30 pointings with automated PPV core finding | R: 141 candidate cores; C9A ~70 (up to ~170) Msun | F: C9A is a candidate massive early-stage core, but starless nature needs follow-up | **partially**
- H: Core dynamics are consistent with virial equilibrium of pressure-confined cores | E: Hyperfine line fits and mm masses compared with MT03 model | R: mean sigma ratio 0.80 | F: Consistent with virial equilibrium; ~1 mG fields needed for precise virial | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Graph-based PPV connectivity to systematically process many regions  
  > "we have presented a new way to automatically identify $\rm N_2D^+$(3-2) cores as connected structures in PPV space using Graph theory methods." (Discussion and Conclusions)
- Alternative: yt clumpfind gave all B1 cores with 2.5 sigma threshold  
  > "then yt finds all B1 cores given by our method." (Core Detection Analysis Methods)
- How they decided it was enough: _not stated_
- Limitation (authors): Many weakest cores likely noise; sensitivity 3 times worse than T13; core sizes likely underestimated; mass uncertainty factor ~2  
  > "although many of the weakest sources are likely to be noise fluctuations." (Discussion and Conclusions)
- Caveat (inferred, ours): Core definition depends on arbitrary thresholds
- Caveat (inferred, ours): Uncleaned line cubes and no deconvolution
- Caveat (inferred, ours): Fixed 10 K dust temperature drives mass
- Caveat (inferred, ours): No ACA, large-scale flux filtered

## Reproducibility

- Data public (paper): ALMA project cited with acknowledgment of ALMA data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.0.00806.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Core-finding code not released
- Missing: Minimum voxel threshold
- Missing: Imaging parameters
- Missing: T13 equations
- Data volume (inferred): ~100-300 GB raw for two tracks
- Score (inferred): 3/5, Data public and algorithm described, but key thresholds, imaging parameters and code are missing.
- Rediscovery candidate: no, Recipe incomplete for core finding and imaging details.

## Links

- Method: Tan et al. 2013 (cite: 2013ApJ...779...96T) (Mass and dynamics methods)
- Method: Butler & Tan 2012 (cite: 2012ApJ...754....5B) (MIREX maps)
- Companion: Liu et al. (in prep.) (SiO(5-4) outflow analysis)
- Related: ALMA Cycle 0 N2D+ pilot (T13)

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2013.0.00806.S"
 ],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 47,
  "rate": 0.627
 },
 "evidence_ok": true
}
```
