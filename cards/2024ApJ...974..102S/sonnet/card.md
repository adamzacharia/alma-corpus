# Hints of Planet Formation Signatures in a Large-cavity Disk Studied in the AGE-PRO ALMA Large Program

`2024ApJ...974..102S` | The Astrophysical Journal 2024 | first author: Sierra, Anibal | arXiv: 2407.16651 | DOI: 10.3847/1538-4357/ad6e73

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Does the large-cavity disk around J16120 show dust and gas (CO kinematic) signatures of planet formation?  
  > "In this paper, we unveil hints of planet formation signatures in the large-cavity disk around 2MASS J16120668-3010270 (J16120 hereafter)." (Introduction)
- Target **2MASS J16120668-3010270 (J16120)**: coordinates J2000 16h12m06.664505s -30d10m27.61789s (common phase center)  
  > "This star is localized in the Upper Scorpius star forming region, at a distance of 132.1 pc (cite: Gaia_2023)." (Introduction); z/distance 132.1 pc  
  > "This star is localized in the Upper Scorpius star forming region, at a distance of 132.1 pc (cite: Gaia_2023)." (Introduction); distance from Gaia (Gaia_2023)  
  > "This star is localized in the Upper Scorpius star forming region, at a distance of 132.1 pc (cite: Gaia_2023)." (Introduction)

## Data provenance

- ALMA projects: 2021.1.00128.L, 2023.1.01100.S
- bands: Band 6 (1.3 mm)  
  > "The disk was imaged with the Atacama Large Millimeter/submillimeter Array (ALMA) at Band 6 (1.3 mm)" (abstract)
- frequencies and spectral setup: 6 spectral windows per setup: one continuum (1.4 km/s), five line (0.09 km/s)  
  > "Each correlator setup consists of 6 spectral windows: one for continuum observations with a velocity resolution of 1.4 km s$^{-1}$, and five for molecular line emission, with a velocity resolution of 0.09 km s$^{-1}$." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: three short baseline (SB) and five long baseline (LB) executions  
  > "The observations of J16120 consist in three short baseline (SB) executions and five long baseline (LB) executions." (Observations)
- baselines: _not stated_
- angular resolution: continuum ~150 mas (20 au); 12CO ~200 mas (30 au)  
  > "angular resolution of $\sim 150$ mas, 20 au" (abstract)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: March and July 2022  
  > "(ALMA Project ID: 2021.1.00128.L), during March and July 2022." (Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- Line: H2CO 3(0,3)-2(0,2) (not stated)
- Other facility **ALMA Band 7 (Carpenter et al. in prep.)**: Band 7 integrated flux density (65.5 mJy) used for spectral index  
  > "The integrated flux density at Bands 6 and 7 is 16.6 and 65.5 mJy, respectively." (4.1)
- External data: Stellar properties: M0, age 5-10 Myr, L=0.25 Lsun, R=1.2 Rsun, accretion rate 4e-10 Msun/yr  
  > "J16120 is a M0 star with an estimated age between 5-10 Myrs, a luminosity of $0.25 \ L_{\odot}$" (Introduction) [from Fang et al. 2023 (cite: Fang_2023)]
- External data: Dust mass 8.5 Mearth (optically thin, kappa 2.3 cm2/g, 20 K)  
  > "the total dust mass (M$_{\rm dust} = 8.5$ M$_{\oplus}$) estimated in Trapman et al. in prep." (4.1) [from Trapman et al. in prep.]
- External data: DSHARP opacities  
  > "based on the DSHARP opacities (cite: Birnstiel_2018)" (4.1) [from (cite: Birnstiel_2018)]

## Processing

### Calibration

- pipeline or manual: SB and LB executions self-calibrated; LB flux rescaled to SB  
  > "Therefore, the LB visibilities were re-scaled to match the SB flux." (Observations)
- casa version: CASA 6.4.3.27  
  > "The SB and LB executions were self-calibrated using CASA version 6.4.3.27." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: LB total flux 14% higher than SB  
  > "found that the total flux in LB executions was 14% higher than that in the self-calibrated SB." (Observations)
- self calibration: Phase-only; first SB only with combine='spws,scans', solint='inf', SNR improved 47%; then repeated after concatenation; no amplitude self-cal  
  > "The SNR improved by 47% after the initial self-calibration step." (Observations); "We did not apply amplitude self-calibration since we did not observe significant SNR improvement in this case." (Observations)

### Imaging

- task: CASA tclean  
  > "We use the `tclean` task in CASA, with a multi-scale algorithm" (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.0 (continuum, 12CO), 0.5 (13CO), 1.0 (C18O, H2CO)  
  > "we choose a robust of 0.0, 0.5, 1.0, and 1.0 for imaging the $^{12}$CO, $^{13}$CO, C$^{18}$O, and H$_2$CO molecular emission, respectively, and 0.0 for the dust continuum map." (Observations)
- uv taper: _not stated_
- cell size: 20 mas  
  > "20 mas cellsize of the clean image" (More on dust continuum modeling)
- image size: _not stated_
- masking: clean threshold 1 sigma continuum, 4 sigma lines  
  > "We adopted a clean threshold of 1$\sigma$ and 4$\sigma$ for the dust continuum and molecular lines, respectively." (Observations)
- multiscale scales: point sources and 0.5, 1, 2, 3 times beam FWHM  
  > "scales of half, one, two, and three times the beam Full Width at Half Maximum (FWHM)" (Observations)
- continuum subtraction: uvcontsub  
  > "Then, we used the task `uvcontsub` to extract the continuum emission from the dataset" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Continuum 171x142 mas PA 71.9; 12CO 217x188; 13CO 297x241; C18O 407x324; H2CO 347x319  
  > "| Continuum                       | 0.0    | 171 $\times$ 142; 71.9  | 0.021             | \-             |   |" (Table 1)
- final rms: continuum 0.021 mJy/beam; per-channel 2.51, 1.22, 0.56, 0.14 mJy/beam  
  > "| $^{12}$CO (J=2-1)               | 0.0    | 217 $\times$ 188; 71.2  | 2.51              | 0.1            |   |" (Table 1)

### Inherited from earlier work

- 4 sigma clean threshold and JvM correction following MAPS imaging strategy  
  > "The 4$\sigma$ criteria was chosen following the same imaging strategies in the MAPS ALMA Large Program (cite: Oberg_2021; Czekala_2021)." (Observations) [from (cite: Oberg_2021; Czekala_2021)]
- Full observational setup and self-calibration details  
  > "Full comprehensive details regarding the observational setup and self-calibration process for all the disks in the Upper Scorpius star-forming region will be provided in Agurto-Gangas et al. in prep." (Observations) [from Agurto-Gangas et al. in prep.]
- CPD injection-recovery procedure  
  > "we follow the procedure described in (cite: Andrews_2021)" (More on dust continuum modeling) [from (cite: Andrews_2021)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solint values beyond 'inf' for LB, and reference antenna/refant
- Line-free channels and velocity ranges used for uvcontsub
- Image sizes and channel widths for line cubes
- Exact EDDY priors, bounds and initial guesses
- DISKSURF extraction parameters
- Which Frankenstein version and fit radial grid settings (Rmax, N)
- Rest frequencies used
- Mask definition for the faint extra source and compact source photometry details

## Analysis recipe

1. **Calibration, alignment and self-calibration**: Align executions via 2D Gaussian disk centers, self-calibrate SB then concatenated SB+rescaled LB (phase only)  
  > "we created low angular resolution continuum images of each dataset and fit a 2D gaussian to identify the disk center of each execution." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Checked flux-scale alignment of deprojected visibilities  
  > "we checked for flux-scale alignment using the deprojected visibilities of each SB execution" (Observations)
2. **Image continuum and lines**: tclean multiscale with per-line robust, JvM correction  
  > "we applied the JvM correction to the molecular emission maps" (Observations)
   - software: CASA, bettermoments
   - parameter: JvM epsilon = 0.71, 0.47, 0.33, 0.31 for 12CO, 13CO, C18O, H2CO  
  > "We obtain a residual correcting factor of $\epsilon = 0.71, 0.47, 0.33$, and 0.31" (Observations)
   - fitting: _not stated_
   - validation: Repeated without JvM correction; structures unchanged  
  > "we confirm that the final results do not depend on this correction" (Observations)
3. **Fit disk geometry and continuum radial profile**: MCMC on visibilities for offset/inclination/PA (minimizing imaginary part and real-part spread); Frankenstein non-parametric radial profile  
  > "We model the visibilities of the dust continuum emission of J16120[^3] with FRANKENSTEIN (cite: Jennings_2020)" (3.2)
   - software: Frankenstein, uvplot, emcee
   - parameter: alpha = 1.05, w_smooth = 1e-4  
  > "we fix them to $\alpha = 1.05$ and $w_{\rm smooth} = 10^{-4}$." (3.2)
   - assumption: Same geometry assumed for whole disk, azimuthal symmetry  
  > "we assume the same geometry in all the disk." (3.2)
   - fitting: MCMC (Foreman-Mackey 2013), uniform priors  
  > "uniform priors were included for all parameter." (3.2)
   - validation: Hyperparameter grid tested; no important differences  
  > "found no important differences in the reconstructed brightness radial profile." (3.2)
4. **Residual map and spiral fit**: Subtract axisymmetric model in visibility space, image residuals, fit logarithmic spiral r=R0 exp(b theta) to residual knots  
  > "The deprojected coordinates are then fitted using the logarithmic spiral arm prescription outlined in (cite: Perez_2016)" (3.2)
   - software: CASA
   - fitting: Posterior sampling; 1000 random chains shown  
  > "1000 random chains from the posterior distribution" (3.2)
   - validation: Varied offset and geometry within errors; CPD injection tests (50 datasets)  
  > "We created 50 different data set models where we injected the visibilities of a CPD with different fluxes at random coordinates within the gap." (More on dust continuum modeling)
5. **12CO emission surface and stellar mass**: DISKSURF extraction from channels plus EDDY Keplerian fit of quadratic velocity map with parametrized surface  
  > "We use both methodologies and compare the results." (3.3)
   - software: disksurf, eddy, bettermoments
   - parameter: fit radii 0.33 to 1.4 arcsec; inc and PA fixed from continuum  
  > "We fit the emission within a deprojected radius of $0.33^{\prime \prime}$ (1.5 times the beam major axis) and $1.4^{\prime \prime}$" (3.3)
   - fitting: MCMC, 64 walkers, 3000 steps burn-in then last 3000 steps  
  > "the 64 walkers used to explore the parameters of the $^{12}$CO emission surface" (More on kinematics modeling)
   - validation: Compared methods and alternative velocity maps (First moment, Gaussian, GaussThick)  
  > "we also computed velocity maps using additional methodologies (including moment 1 maps), and similar constraints to the emission surface were found" (3.3)
6. **Velocity components and azimuthal deviation**: EDDY deprojected v_r, v_phi, v_z from 12CO channels; compare with Keplerian and pressure-bump expectation  
  > "We also use EDDY and the $^{12}$CO channel maps to compute the deprojected velocity along the disk radius ($v_r$), azimuth ($v_\phi$), and vertical disk axis ($v_z$)." (3.3)
   - software: eddy
   - assumption: gas temperature 20 K, c_s ~0.3 km/s  
  > "$c_s \sim 0.3$ km s$^{-1}$ for a gas with a temperature of 20K" (3.3)
   - fitting: _not stated_
   - validation: _not stated_
7. **Spectral index, grain size and dust mass**: alpha from Band 6/7 integrated fluxes, beta=alpha-2, a_max from DSHARP opacities; dust mass from deconvolved profile with scattering solution  
  > "the opacity spectral index $\beta$ can be estimated as $\beta = \alpha - 2 = 1.3 \pm 0.3$" (4.1)
   - parameter: zeta = 0.02, L* = 0.25 Lsun, T_d=[zeta L/(4 pi sigma r^2)]^(1/4)  
  > "where $\zeta = 0.02$ is the flaring angle (cite: Huang_2018)" (4.1)
   - assumption: optically thin emission; p = 2.5 or 3.5  
  > "for particle size distribution $n(a)da\propto a^{-p}da$" (4.1)
   - fitting: _not stated_
   - validation: _not stated_
8. **Compact source dust mass and kink planet mass**: Optically thin dust mass from 63 uJy peak at 21 K; planet mass M~v_peak^2 r_extent/G  
  > "$M_{\rm planet} \sim v_{\rm peak}^2 r_{\rm extent} /G \approx 0.8 \ M_{\rm Jupiter}$" (4.3)
   - assumption: kappa 0.42 and 1.9 cm2/g for 100 um and 1 mm grains; T=21 K; p=3.5  
  > "a temperature of 21 K (estimated from the stellar irradiation at the compact emission radius)" (4.2)
   - fitting: _not stated_
   - validation: Injection-recovery test: ~20% recovery at 63 uJy; gap rms 35 uJy/beam  
  > "the recovery fraction of a CPD with a flux similar to that of the compact emission is $\sim 20\%$" (4.2)

## Software

- **CASA** 6.4.3.27: Self-calibration, tclean imaging, uvcontsub  
  > "The SB and LB executions were self-calibrated using CASA version 6.4.3.27." (Observations)
- **bettermoments** : Moment maps and line-of-sight velocity maps (Quadratic, Gaussian, GaussThick)  
  > "The moment maps were computed using the BETTERMOMENTS tools" (3.1)
- **Frankenstein** : Non-parametric radial brightness profile from visibilities  
  > "a PYTHON library that fits the visibilities using a non-parametric radial brightness profile" (3.2)
- **eddy** : Keplerian fit of velocity maps, emission surface, velocity components  
  > "We use EDDY (cite: eddy) to explore the posterior probability distribution of the stellar parameters and emission surface." (3.3)
- **disksurf** : Extract CO emission surface from channels  
  > "we use the Python package DISKSURF (cite: Pinte_disksurf_2018; disksurf) to extract the surface in different channels." (3.3)
- **GALARIO** : Compute visibilities of compact emission and bridge for injection tests  
  > "The visibilities of the compact emission and the bridge are computed with GALARIO (cite: Tazzari_2018)" (More on dust continuum modeling)
- **uvplot** : Visibility extraction (modified export_uvtable)  
  > "using a modified version of the *export_uvtable* function in (cite: uvplot_tazzari)" (3.2)
- **emcee** : MCMC sampling (cited Foreman-Mackey 2013)  
  > "We used a Markov chain Monte Carlo (MCMC) method (cite: Foreman_2013)" (3.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum ring peak radius | 0.57 (75) | not stated | arcsec (au) | 3 | a ring-like structure with a peak at $0.57 ^{\prime \prime}$ (75 au) |
| Disk inclination | 37.0 | +0.1/-0.2 | deg | 3 | $\rm inc= 37.0 ^{+0.1}_{-0.2}$ deg |
| Disk position angle | 45.1 | +0.2/-0.9 | deg | 3 | $\rm PA = 45.1^{+0.2}_{-0.9}$ deg |
| Spiral R0 | 0.42 | 0.01 | arcsec | 4 | $R_0 = 0.42^{\prime \prime}\pm 0.01 ^{\prime \prime}$ |
| Spiral b | 2.4e-3 | 0.2e-3 | deg^-1 | 4 | $b = (2.4 \pm 0.2) \times 10^{-3} \ \rm deg^{-1}$ |
| Stellar mass (12CO, EDDY) | 0.70 | +/-0.1 | Msun | 5 | / $M_*$ $[M_{\odot}]$                  / 0.70$^{*}$             / 0.70$^{+0.1}_{-0.1}$   / |
| Emission surface z0 | 0.17 | +/-0.01 | arcsec | 5 | / $z_0$ \[arcsec\]                     / 0.58$^{+0.91}_{-0.30}$ / 0.17$^{+0.01}_{-0.01}$ / |
| Spectral index Band 6-7 | 3.3 | 0.3 | dimensionless | 7 | the average spectral index is $\alpha = 3.3 \pm 0.3$ |
| Maximum grain size | 1.6 mm (p=2.5), 4.0 mm (p=3.5) | not stated | mm | 7 | maximum grain sizes of 1.6 mm and 4.0 mm |
| Compact source dust mass | 12.9 (100 um) to 2.7 (1 mm) | not stated | Lunar masses | 8 | this flux corresponds to a dust mass of 12.9 and 2.7 Lunar masses for grain sizes of 100 $\mu$m and 1 mm, respectively |
| Compact source peak flux | 63 | not stated | uJy | 8 | The peak flux within one beam centered at the compact source is $\sim 63 \ \mu$Jy. |
| Planet mass upper limit from kink | 0.8 | not stated | Mjup | 8 | $M_{\rm planet} \sim v_{\rm peak}^2 r_{\rm extent} /G \approx 0.8 \ M_{\rm Jupiter}$ |
| Injection 50% recovery flux | 93 | not stated | uJy | 4 | The interpolated 50% fraction corresponds to 93 $\mu$Jy. |

## Qualitative findings

- Azimuthal velocity consistent with Keplerian within errors, so dust trap origin of ring not confirmed or ruled out  
  > "Thus, it is not clear if the origin of the dust continuum ring is a dust trap created by a pressure bump." (Conclusions)

## Claim tuples

- H: Dust continuum shows planet-formation hints in the gap | E: Visibility modeling, residual imaging, spiral fit, injection tests | R: Compact 3 sigma source in gap, bridge and spiral arm; recovery fraction ~20% | F: Compact source is a tentative CPD candidate; not distinguishable from noise | **partially**
- H: 12CO kinematics show a planet-induced kink | E: Channel maps and Keplerian modeling residuals | R: Kink at ~0.85 arcsec in channels 4.0-4.3 km/s; rotating-like residual with ~0.17 km/s peak | F: Speculative CPD/planet candidate <~0.8 Mjup | **partially**
- H: Ring is a dust trap | E: Azimuthal velocity vs Keplerian and spectral index | R: v_phi matches Keplerian within errors; alpha = 3.3 | F: Cannot confirm or rule out | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Smaller robust used to increase resolution for substructure  
  > "we re-image the data by adopting a smaller Briggs robust parameter, aiming for higher resolution" (Observations)
- Alternative: Alternative velocity-map methods (First moment, Gaussian, GaussThick) compared; residual structure appears only in Quadratic  
  > "Note the residual structure observed within the green circle of the `Quadratic` method does not appear in the other cases" (Line of sight velocity maps and modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): Compact source gap rms is enhanced, low effective SNR  
  > "which reduces the effective SNR of the compact source detection" (4.2)
- Limitation (authors): Kink structure only marginally resolved; error bars large  
  > "Note that this is not the actual size, but an upper limit, as it is only marginally resolved." (4.3)
- Caveat (inferred, ours): Residual rotating structure is within noise-level residuals elsewhere; no significance estimate
- Caveat (inferred, ours): Spiral arm residuals depend strongly on offset
- Caveat (inferred, ours): Stellar mass differs across isotopologues, affecting v_phi deviation
- Caveat (inferred, ours): Single-band data cannot constrain grain size radially

## Reproducibility

- Data public (paper): Data from ALMA Large Program 2021.1.00128.L (acknowledged); public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2021.1.00128.L" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Self-calibrated measurement sets and calibration scripts (in Agurto-Gangas et al. in prep.)
- Missing: Band 7 flux and Trapman dust mass from in-prep papers
- Missing: Line-free channel and EDDY prior details
- Data volume (inferred): ~100-300 GB raw for 8 executions
- Score (inferred): 3/5, Methods mostly described with named packages, but key calibration and priors are deferred to in-prep papers.
- Rediscovery candidate: no, Self-calibration details and some inputs rely on unpublished companion papers.

## Links

- Method: Jennings et al. 2020 (cite: Jennings_2020) (Frankenstein visibility fitting)
- Method: Teague & Foreman-Mackey 2018 (cite: Teague_2018b) (bettermoments velocity maps)
- Method: Andrews et al. 2021 (cite: Andrews_2021) (CPD injection-recovery procedure)
- Companion: Zhang et al. in prep. (AGE-PRO overview)
- Companion: Agurto-Gangas et al. in prep. (Upper Sco observations and self-calibration)
- Companion: Vioque et al. in prep. (AGE-PRO visibility analysis)
- Related: AGE-PRO
- Related: MAPS
- Related: eDisks
- Related: DSHARP

## Checks

```json
{
 "quotes": 91,
 "quotes_ok": 91,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2023.1.01100.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 94,
  "stated": 67,
  "rate": 0.713
 },
 "evidence_ok": true
}
```
