# ALMA View of G0.253+0.016: Can Cloud-Cloud Collision form the Cloud?

`2014AJ....147..141H` | The Astronomical Journal 2014 | first author: Higuchi, Aya E. | arXiv: 1403.4734 | DOI: 10.1088/0004-6256/147/6/141

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, milky_way_ism
- Question: What are the spatial and velocity structures of the dense, massive cloud G0.253+0.016 in SO emission, and can a cloud-cloud collision explain its formation?  
  > "In attempt to explore the formation scenario of the dense cloud, we compared our results with numerical simulations, thus, we propose that G0.253+0.016 may have formed due to a cloud-cloud collision process." (abstract)
- Target **G0.253+0.016 (G0.25)**: coordinates _not stated_; z/distance 8.5 kpc  
  > "G0.25 forms part of 100 pc circum-nuclear ring of clouds (Molinari et al. 2011) at 8.5$\,$kpc distance (Longmore et al. 2012)." (INTRODUCTION); distance from Longmore et al. 2012  
  > "G0.25 forms part of 100 pc circum-nuclear ring of clouds (Molinari et al. 2011) at 8.5$\,$kpc distance (Longmore et al. 2012)." (INTRODUCTION)

## Data provenance

- ALMA projects: 2011.0.00217.S
- bands: Band 3 (90 GHz)  
  > "G0.25 was observed with ALMA (Hills et al. 2010) during Early Science Cycle 0 with extended configuration, using the Band 3 receivers." (OBSERVATIONS)
- frequencies and spectral setup: 4 spectral windows centered at 89.1, 87.2, 99.1, 101.1 GHz; 1875 MHz each; 2.9-3.4 km/s resolution after Hanning smoothing  
  > "The correlator was set up to four spectral windows in dual polarization mode, centered at 89.10000 GHz, 87.20000 GHz, 99.10000 GHz, and 101.10000 GHz." (OBSERVATIONS)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: ~36.1 to ~452.8 m projected  
  > "The array was in a configuration with projected baselines length between $\sim$ 36.1 to $\sim$ 452.8 m" (OBSERVATIONS)
- angular resolution: synthesized beam 2.30" x 1.53" (quoted as 1.7")  
  > "providing a synthesized beam of 2.30$''$ $\times$ 1.53$''$" (OBSERVATIONS)
- max recoverable scale: 9.1"  
  > "sensitive to maximum angular scales of 9.1$''$" (OBSERVATIONS)
- sensitivity: rms 1.1 to 1.4 mJy/beam per 3.4 km/s channel  
  > "for an rms noise in line-free channels of 1.1 to 1.4 mJy beam$^{-1}$ per 3.4 km s$^{-1}$ channel" (OBSERVATIONS)
- time on source: 4 hours, six data sets, 24 antennas  
  > "A total of six data sets were collected, using 24 antennas of 12$\,$m diameter and accounting for 4 hours of total integration time on target." (OBSERVATIONS)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: SO 3(2)-2(1) (99.29987 GHz)
- Other facility **SCUBA 450 um (Longmore et al. 2012)**: Dust continuum map compared with SO shell  
  > "Comparing our SO map with the dust continuum map traced by SCUBA 450 $\ensuremath{\mu}m$ in Longmore et al. (2012)" (Spatial distributions of the SO emission)
- Other facility **WISE**: Image showing filaments in dust extinction  
  > "Comparing Figure [1](#map1) with the $\it{WISE}$ image of G0.25, we see that the SO emissions trace the network of pc-long filaments seen in dust extinction." (Spatial distributions of the SO emission)
- External data: Cloud mass ~2e5 Msun, radius 2.8 pc  
  > "G0.253+0.016 (hereafter G0.25) is very massive ($\sim$2$\times$10$^{5}M_\odot$, radius of 2.8 pc; Longmore et al. 2012)" (INTRODUCTION) [from Longmore et al. 2012]
- External data: Velocity gradient vs size relation  
  > "We compared our result with the previous studies of velocity gradients of clouds in Larson (1983) and Goodmann et al. (1993)" (Kinematic structures of the cloud) [from Larson 1983; Goodman et al. 1993]
- Simulation/model as data: Habe & Ohta (1992) head-on non-identical cloud collision simulation compared qualitatively  
  > "Habe $\&$ Ohta (1992) simulated head-on collision between non-identical clouds with supersonic relative velocities" (Comparison with the simulation)

## Processing

### Calibration

- pipeline or manual: CASA data reduction (details not given)  
  > "Data reduction was performed using the version 3.4 of the Common Astronomy Software Applications (CASA) package" (OBSERVATIONS)
- casa version: CASA 3.4  
  > "Data reduction was performed using the version 3.4 of the Common Astronomy Software Applications (CASA) package" (OBSERVATIONS)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune (amplitude); J1717-337, J2225-049 bandpass; NRAO 530 gain  
  > "Amplitude calibration was done using Neptune, and quasars J1717-337 and J2225-049, and NRAO$\,$530 were used to calibrate the bandpass and the complex gain fluctuations, respectively." (OBSERVATIONS)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN, 3.4 km/s channels  
  > "We used the task CLEAN to image the visibilities." (OBSERVATIONS)
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
- array combination: Interferometer only, no short-spacing; larger scales resolved out  
  > "We made the map using only interferometric dataset, which implies that we are only seeing features of the shell-like structure within the size of 9.1$''$." (Spatial distributions of the SO emission)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- CLEAN weighting/robust, threshold, masking, cell and image size
- Continuum subtraction and line-free channels
- Mosaic pointings and phase center
- Integration velocity range and clipping for moment maps
- How core boundaries (30 sigma contours) and the velocity gradient were measured
- Temperature/mass inputs of the virial analysis beyond quoted values
- Position-velocity slice definitions
- Inconsistency between 2.30x1.53 beam and quoted 1.7 arcsec resolution
- Flux scale uncertainty

## Analysis recipe

1. **Image SO cube**: CLEAN imaging of SO(3-2-2-1) visibilities at 3.4 km/s channels  
  > "visibilities imaged and deconvolved with 3.4 km s$^{-1}$ channels" (OBSERVATIONS)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared SO shell with SCUBA dust continuum to argue it is not an interferometric artifact  
  > "we interpreted that the shell structure traced by SO emission is not an artifact of the interferomtric observations" (Spatial distributions of the SO emission)
2. **Identify SO cores**: SO emission within 30 sigma contours of integrated intensity map defined as cores A-N  
  > "We defined the SO emission enclosed in the 30$\,$$\sigma$ contours of the integrated intensity map as SO cores." (Spatial distributions of the SO emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Moment maps and velocity gradient**: 1st and 2nd moment maps; gradient = v_diff/2R  
  > "We estimated the velocity gradient ($\sigma_{\rm{grad}}$), $v_{\rm{diff}}$/$2R$, where $v_{\rm{diff}}$ is the velocity difference of $\sim$100 km$\,$s$^{-1}$" (1st and 2nd moment maps)
   - fitting: _not stated_
   - validation: _not stated_
4. **P-V diagrams**: Cube collapsed along each spatial axis; slices at different position angles  
  > "i.e., the data cube collapsed along each spatial axis" (Position-Velocity diagram)
   - fitting: _not stated_
   - validation: _not stated_
5. **Virial balance**: K/|W| and U/|W| scaling relations from Stahler & Palla (2005), magnetic field ignored  
  > "Here, we ignore the effect of the magnetic field." (Kinematic structures of the cloud)
   - parameter: sigma_v ~4 km/s (mean 2nd moment), M=2e5 Msun, R=2.8 pc, T=20 K  
  > "We used mean value of the velocity dispersion of SO (${\sigma_{v}}$$\sim$4 km s$^{-1}$) in the 2nd moment map." (Kinematic structures of the cloud)
   - fitting: _not stated_
   - validation: _not stated_
6. **Compare with collision simulations**: Qualitative comparison with Habe & Ohta (1992), Takahira et al., Inoue & Fukui (2013)  
  > "The filamentary structures and cores of SO in G0.25 cloud are very similar to results of cloud cloud collision simulations." (Comparison with the simulation)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 3.4: Data reduction and CLEAN imaging  
  > "Data reduction was performed using the version 3.4 of the Common Astronomy Software Applications (CASA) package" (OBSERVATIONS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Shell radius | 1.3 | not stated | pc | 2 | shell structure of radius 1.3 pc |
| Velocity gradient | 20 | not stated | km/s/pc | 3 | to be $\sim$20 km s$^{-1}$ pc$^{-1}$ within the whole cloud |
| Velocity dispersion of large-sigma cores | 30-40 | not stated | km/s | 3 | ${\sigma}_{v}$$\sim$ 30 to 40 km$\,$s$^{-1}$ |
| Overall velocity difference | ~100 | not stated | km/s | 3 | The overall velocity structure of the cloud has a velocity difference of $\sim$100 km$\,$s$^{-1}$. |
| K/|W| | 0.1 | not stated | dimensionless | 5 | = 0.1\,\left(\frac{\sigma_{v}}{4~\rm{km~s}^{-1}}\right)^{2} |
| U/|W| | 2e-2 | not stated | dimensionless | 5 | = 2\times10^{-2}\,\left(\frac{M}{2\times10^{5}~M_\odot}\right)^{-1} |

## Qualitative findings

- SO traces a network of pc-long filaments and hub-filament cores connected to the shell.  
  > "we see that the SO emissions trace the network of pc-long filaments seen in dust extinction." (Spatial distributions of the SO emission)

## Claim tuples

- H: G0.25 has a shell structure and large velocity structure in SO | E: SO(3-2) mosaic with ALMA, moment and P-V analysis | R: 1.3 pc shell, ~20 km/s/pc gradient, cores with sigma 30-40 km/s | F: Unusual kinematics, large-sigma cores may form high-mass stars | **supported**
- H: Cloud-cloud collision formed G0.25 | E: Qualitative comparison with collision simulations | R: Observed filaments, shells and velocities resemble simulations; velocity gradient is an order of magnitude above literature relation | F: G0.25 may have formed through cloud-cloud collision | **partially**

## Reasoning

- Why this data: G0.25 is massive and dense but shows no obvious cluster formation, so is a site to study initial conditions of super-star cluster formation  
  > "G0.25 presents an interesting site for the study of the initial condition of super-star cluster formation" (INTRODUCTION)
- Why this method: _not stated_
- Alternative: Winds or supernova shells as shell origin disfavoured due to no evidence of external effects  
  > "However, there are no evidence of such an external effects in G0.25 cloud" (Comparison with the simulation)
- How they decided it was enough: _not stated_
- Limitation (authors): Interferometer-only data resolves out structure larger than 9.1"  
  > "All components above this scale were resolved out." (Spatial distributions of the SO emission)
- Caveat (inferred, ours): Collision interpretation is qualitative, with no quantitative model comparison
- Caveat (inferred, ours): No short-spacing data; resolved-out flux affects moments and virial estimates
- Caveat (inferred, ours): Large velocity dispersions could reflect line blending or multiple components, not single cores
- Caveat (inferred, ours): Virial estimate uses scaled formulae with a 4 km/s mean sigma while cores show 30-40 km/s
- Caveat (inferred, ours): Conclusion 4 mentions rotation in virial ratios not shown in the text

## Reproducibility

- Data public (paper): Cycle 0 archival ALMA data, project 2011.0.00217.S  
  > "based on ALMA archive data of G0.25 obtained with an extended configuration" (INTRODUCTION)
- Products in archive: _not stated_
- Missing: CLEAN parameters
- Missing: Moment-map thresholds
- Missing: Core definition details
- Missing: Pointing and mosaic details
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and basic setup given, but imaging and analysis parameters are mostly missing.
- Rediscovery candidate: no, Imaging and moment parameters are not given and the comparison with simulations is qualitative.

## Links

- Companion: Kauffmann et al. 2013 (Earlier N2H+ study of G0.25)
- Companion: Longmore et al. 2012 (Cloud properties and SCUBA map)

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 34,
  "rate": 0.479
 },
 "evidence_ok": true
}
```
