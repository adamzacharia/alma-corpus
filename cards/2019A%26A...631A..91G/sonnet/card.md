# Towards sub-kpc scale kinematics of molecular and ionized gas of star-forming galaxies at z ∼ 1

`2019A&A...631A..91G` | Astronomy and Astrophysics 2019 | first author: Girard, M. | arXiv: 1909.07400 | DOI: 10.1051/0004-6361/201935896

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Do molecular (CO) and ionized ([O II]) gas rotation curves and velocity dispersions differ in two lensed z~1 galaxies, and can disk geometry (radius, thickness) explain it?  
  > "we investigate if the difference observed between the rotation curves and velocity dispersion values of the molecular and ionized gas can be explained by geometrical effects in the Cosmic Snake and A521." (7 Analysis of two lensed z~1 galaxies)
- Target **Cosmic Snake**: coordinates 12:06:11 -08:48:05 (J2000)  
  > "| Cosmic Snake | 12:06:11 | -08:48:05 | 0.51 | $0.22\times0.18$ | 1.03620 |" (Table 1); "located behind the clusters MACSJ1206.2-0847 and Abell 0521, respectively." (1 Introduction); z/distance z = 1.03620  
  > "| Cosmic Snake | 12:06:11 | -08:48:05 | 0.51 | $0.22\times0.18$ | 1.03620 |" (Table 1); "located behind the clusters MACSJ1206.2-0847 and Abell 0521, respectively." (1 Introduction); distance from _not stated_
- Target **A521**: coordinates 04:54:06 -10:13:23 (J2000)  
  > "| A521 | 04:54:06 | -10:13:23 | 0.57 | $0.20\times0.17$ | 1.04356 |" (Table 1); z/distance z = 1.04356  
  > "| A521 | 04:54:06 | -10:13:23 | 0.57 | $0.20\times0.17$ | 1.04356 |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.01330.S, 2016.1.00643.S
- bands: Band 6  
  > "The total on-source integration time was of 52.3 minutes in band 6." (3.2 CO observations with ALMA)
- frequencies and spectral setup: CO(4-3) at 226.44 GHz (Snake) and 225.66 GHz (A521); channel 7.8125 MHz (~10.3 km/s)  
  > "The spectral resolution was tuned to 7.8125 MHz ($\rm \sim 10.3\, km \, s^{-1}$) for both galaxies." (3.2 CO observations with ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Snake: C38-5 (max baseline 1.6 km, 38 antennae); A521: C40-6 (max baseline 3.1 km, 41 antennae)  
  > "performed in the extended C38-5 configuration with the maximum baseline of 1.6 km and 38 of the 12 meters antennae" (3.2 CO observations with ALMA)
- baselines: _not stated_
- angular resolution: 0.22"x0.18" (Snake), 0.20"x0.17" (A521)  
  > "The final synthesized beam size is $0.22'' \times 0.18''$ with a position angle of +85$^\circ$ for the Cosmic Snake and $0.20'' \times 0.17''$ at $-71^\circ$ for A521." (3.2 CO observations with ALMA)
- max recoverable scale: _not stated_
- sensitivity: rms 0.29 mJy/beam (Snake), 0.34 mJy/beam (A521) per 7.8125 MHz channel  
  > "We reach an rms of 0.29 mJy beam$^{-1}$ and 0.34 mJy beam$^{-1}$ per 7.8125 MHz channel" (3.2 CO observations with ALMA)
- time on source: 52.3 min (Snake); 89.0 min (A521)  
  > "with an on-source time of 89.0 minutes" (3.2 CO observations with ALMA)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 4-3 (not stated)
- Other facility **MUSE/VLT**: [O II] velocity and dispersion maps (from Patricio2018)  
  > "The observations, data reduction and emission line measurements are described in (cite: Patricio2018)." (3.1)
- Other facility **HST/WFC3**: F160W images and lens model constraints  
  > "with the HST/WFC3 F160W images (program #15435)" (4)
- External data: MUSE [O II] velocity and dispersion maps  
  > "They derived the velocity field and velocity dispersion maps of the Cosmic Snake and A521 by fitting the $[$O II$]$$\lambda3726,3729 \AA$ emission lines" (3.1) [from (cite: Patricio2018)]
- External data: Lens models  
  > "We use the lensing models that were presented in detail in (cite: Cava2018) and (cite: Richard2010) for the Cosmic Snake and A521, respectively" (3.3) [from (cite: Cava2018); (cite: Richard2010)]
- External data: Snake gas fraction f_gas=0.20±0.03  
  > "the gas fraction of $f_{gas}=0.20\pm0.03$ obtained in Dessauges-Zavadsky et al. (accepted)" (6.1) [from Dessauges-Zavadsky et al. (accepted)]
- External data: Inclinations 70 and 72 deg, v_rot=225 km/s for Snake  
  > "the rotation velocity corrected for the inclination is $\upsilon_{rot}=225\pm1$ $\rm km \, s^{-1}$ (cite: Patricio2018)" (6.1) [from (cite: Patricio2018)]
- Simulation/model as data: Particle simulations (~1e6 particles) of Miyamoto-Nagai stellar and gas disks in equilibrium  
  > "we typically distribute one million particles according to the analytical distributions of the gas disk components" (5.1 Model)

## Processing

### Calibration

- pipeline or manual: Standard automated CASA pipeline  
  > "The data reduction was performed with the standard automated reduction procedure from the pipeline of the Common Astronomy Software Application (CASA) package" (3.2)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean, interactive  
  > "We cleaned all channels interactively, with the *clean* routine in CASA, until convergence." (3.2)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "we used the Briggs weighting and the robust factor of 0.5" (3.2)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Custom mask including CO emission in all channels  
  > "we used a custom mask for which we made sure to include the CO emission of all the channels" (3.2)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Applied after cleaning  
  > "We then applied the primary beam correction." (3.2)
- array combination: _not stated_
- smoothing: imsmooth to 0.51" (Snake) and 0.69" (A521) to match MUSE  
  > "smoothed with the *imsmooth* routine in CASA to a spatial resolution of $0.51''$ and $0.69''$, respectively" (3.2)
- final beam: 0.22"x0.18" PA +85 (Snake); 0.20"x0.17" PA -71 (A521)  
  > "The final synthesized beam size is $0.22'' \times 0.18''$ with a position angle of +85$^\circ$" (3.2)
- final rms: _not stated_

### Inherited from earlier work

- MUSE observations, reduction and [O II] fitting  
  > "The observations, data reduction and emission line measurements are described in (cite: Patricio2018)." (3.1) [from (cite: Patricio2018)]
- Lens models  
  > "We use the lensing models that were presented in detail in (cite: Cava2018) and (cite: Richard2010)" (3.3) [from (cite: Cava2018); (cite: Richard2010)]
- Intrinsic dispersion measured in outer regions where curve is flat  
  > "where the rotation curve is flat and beam-smearing is negligible (cite: ForsterSchreiber2009; Girard2018a)" (4) [from (cite: ForsterSchreiber2009; Girard2018a)]

### Not stated but needed to reproduce (our reading)

- Line-free channels / continuum subtraction and clean thresholds
- Exact CASA version and pipeline version
- Cell and image size
- Velocity-axis reference used for moment maps and moment masking details
- Annulus widths, aperture definitions, and Toomre-based velocity dispersion setup of the simulation code (code not named)
- Instrumental broadening values sigma_instr for ALMA and MUSE
- Dessauges-Zavadsky et al. gas masses/fractions
- Flux calibrators and flux scale uncertainty

## Analysis recipe

1. **Image CO(4-3) cubes**: CASA clean with Briggs weighting, custom mask, primary beam correction  
  > "we used the Briggs weighting and the robust factor of 0.5" (3.2)
   - software: CASA
   - parameter: robust 0.5  
  > "the robust factor of 0.5" (3.2)
   - fitting: _not stated_
   - validation: _not stated_
2. **Match resolution and make moment maps**: Smooth to MUSE PSF with imsmooth, then immoments for velocity and dispersion with 3 sigma threshold  
  > "with a 3$\sigma$ threshold parameter above the noise level applied when producing the first (velocity) and second (velocity dispersion) moment maps" (3.2)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Extract rotation curves and dispersion profiles**: Source-plane annuli projected to image plane; major axis from steepest gradient; apertures of PSF size along major axis; average positive sides of two counter-images  
  > "The rotation curves and velocity dispersion profiles have been measured directly from the velocity and velocity dispersion maps in the image plane by taking an aperture corresponding to the PSF along the major axis." (4)
   - software: Lenstool
   - fitting: _not stated_
   - validation: Verified with simulated galaxy in source plane projected to image plane; kinematics recovered within 10%  
  > "We accurately recovered the kinematics (with an error less than 10%)." (4)
4. **Measure intrinsic velocity dispersion**: Measure dispersion along major axis at radii larger than R_e where curve is flat; correct for instrumental broadening in quadrature  
  > "We determine the intrinsic velocity dispersion by directly measuring the velocity dispersion maps along the major axis in the outer regions" (4)
   - fitting: _not stated_
   - validation: Compared with Patricio2018 values from a different method  
  > "(cite: Patricio2018) used a different method to estimate the intrinsic velocity dispersion" (4)
5. **Model rotation curves with particle disks**: Stellar and gas Miyamoto-Nagai disks of particles in equilibrium; project at inclination, average LOS velocities, smooth to observed resolution, extract along major axis; vary R_gas, H_gas and resolution H*tan(i)  
  > "we assume an inclination and then produce a 2D velocity map by taking the average velocity of the particles along the line of sight in each spatial element." (5.1 Model)
   - parameter: Snake: M*=4.0e10, R*=3.8 kpc, H*=0.5 kpc, f_mol=0.20, R_mol=0.75 kpc, H_mol=0.1 kpc, R_ion=6.1 kpc, H_ion=1-3 kpc, Q=0.6, i=70 deg  
  > "| $H_{mol}$ \[kpc\]    |             0.1             |" (Table 2)
   - assumption: Dark matter and bulge neglected; Toomre Q=sqrt2 sigma0/(vrot fgas)  
  > "Given that we are observing only the baryon-dominated central parts of a relatively massive galaxy, the contribution from the dark matter is negligible." (6.1)
   - fitting: No formal fit; parameters set from observations and compared with data  
  > "The simulations are in very good agreement with the observed rotation curves." (Analysis of two lensed z~1 galaxies / The Cosmic Snake)
   - validation: Simulated curves compared to observed CO and [O II] curves  
  > "The simulations are in very good agreement with the observed rotation curves." (6.1)

## Software

- **CASA** : pipeline reduction, clean, imsmooth, immoments  
  > "We finally use the *immoments* routine in CASA to obtain the CO(4-3) moment maps" (3.2)
- **Lenstool** : lens mass models  
  > "Lenstool was used to constrain the mass distribution and to optimize the models" (3.3)
- **CAMEL** : Gaussian fitting of [O II] in MUSE (Patricio2018)  
  > "using the CAMEL code (cite: Epinat2010)" (3.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Intrinsic sigma, molecular, Cosmic Snake | 18.5 | 7 | km/s | 4 | We obtain a similar intrinsic velocity dispersion of $18.5 \pm 7 \,$ $\rm km \, s^{-1}$ and $19.5 \pm 6$ $\rm km \, s^{-1}$ |
| Intrinsic sigma, ionized, Cosmic Snake | 19.5 | 6 | km/s | 4 | $19.5 \pm 6$ $\rm km \, s^{-1}$ for the molecular and ionized gas, respectively, for the Cosmic Snake |
| Intrinsic sigma, molecular, A521 | 11 | 8 | km/s | 4 | For A521, we find different values of $11 \pm 8$ $\rm km \, s^{-1}$ and $54 \pm 11$ $\rm km \, s^{-1}$ |
| Intrinsic sigma, ionized, A521 | 54 | 11 | km/s | 4 | $54 \pm 11$ $\rm km \, s^{-1}$ |
| Molecular effective radius, Snake | 0.75 | +0.26/-0.07 | kpc | 5 | we measure the molecular effective radius to be $R_{mol}=0.75^{+0.26}_{-0.07}$ kpc |
| Ionized effective radius, Snake | 6.1 | +1.4/-1.0 | kpc | 5 | $R_{ion}=6.1^{+1.4}_{-1.0}$ kpc for the ionized gas disk |
| Stellar effective radius, Snake | 3.8 | 0.7 | kpc | 5 | We measure a stellar effective radius of $R_\star=3.8\pm0.7$ kpc |
| Toomre Q, Snake | ~0.6 | not stated | dimensionless | 5 | We, therefore, get $Q\sim0.6$ for both the molecular and ionized gas disks |
| R_mol and R_ion, A521 | 5.8 and 6.5 | 1.0 and 1.2 | kpc | 5 | ($R_{mol} = 5.8\pm 1.0$ kpc) with respect to $[$O II$]$  ($R_{ion} = 6.5\pm 1.2$ kpc) |
| Ionized gas mass, Snake | 2.0e7 | 0.2e7 | Msun | 5 | We estimate the ionized gas mass to be $(2.0\pm0.2)\times10^7 M_\odot$ |

## Qualitative findings

- Snake CO rotation curve is steeper than [O II]; A521 curves agree at ~2-3 kpc resolution  
  > "The molecular gas curve is steeper and reaches the maximum rotation velocity at a smaller radius from the center than the ionized gas curve." (4)

## Claim tuples

- H: Molecular and ionized gas rotation curves differ at sub-kpc resolution | E: Compare CO(4-3) ALMA and [O II] MUSE rotation curves of the lensed Snake and A521 | R: Snake CO curve steeper in inner 0-2 kpc; A521 curves agree at few-kpc resolution | F: Differences appear when resolution is sufficient | **supported**
- H: Disk geometry explains the differences | E: Particle simulations of stellar plus two gas disks | R: Different radii and heights reproduce the Snake curves; H_ion~1 kpc | F: Molecular disk is more concentrated and thinner than the ionized disk | **supported**
- H: Velocity dispersions differ between tracers | E: Measure outer-disk dispersion | R: Snake similar; A521 11 vs 54 km/s | F: A521 ionized gas may be a thick turbulent disk | **partially**

## Reasoning

- Why this data: Lensing gives a few hundred pc resolution for comparing tracers  
  > "we can compare the molecular and ionized gas kinematics of these two galaxies at high spatial resolution (a few hundred parsecs on average)." (1 Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): A521 lacks resolution along the major axis, so differences may be hidden  
  > "The lack of spatial resolution can easily prevent to see a difference between two rotation curves." (3.1)
- Caveat (inferred, ours): Only two galaxies; no formal fit or uncertainties for the simulation comparison
- Caveat (inferred, ours): Only positive-velocity sides used
- Caveat (inferred, ours): Beam-smearing not corrected in profiles
- Caveat (inferred, ours): Model parameters partly tuned (H_ion), not fitted
- Caveat (inferred, ours): Lens model uncertainty propagates to radii

## Reproducibility

- Data public (paper): Project codes are given, but public status is not stated  
  > "Observations of the Cosmic Snake were carried out in Cycle 3 (project 2013.1.01330.S)" (CO observations with ALMA)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Simulation code
- Missing: Dessauges-Zavadsky gas fractions
- Missing: Lens models
- Missing: MUSE maps from Patricio2018
- Missing: Clean parameters
- Data volume (inferred): ~50-100 GB raw for two ALMA Band 6 datasets
- Score (inferred): 4/5, Imaging recipe is partly given but the simulation code, inputs and lens models are external or unstated.
- Rediscovery candidate: no, Key inputs (MUSE maps, lens models, simulation code) are not available in the paper.

## Links

- Method: (cite: Epinat2010) (CAMEL code for line fitting)
- Method: (cite: Miyamoto1975) (Disk density-potential model)
- Companion: (cite: Patricio2018) (MUSE [O II] kinematics)
- Companion: Dessauges-Zavadsky et al. accepted (ALMA molecular clouds and gas fraction)
- Companion: (cite: Cava2018) (HST clumps and lens model)
- Related: MUSE

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 47,
  "rate": 0.588
 },
 "evidence_ok": true
}
```
