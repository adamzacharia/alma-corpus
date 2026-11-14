# ALMA Observations and Modeling of the Rotating Outflow in Orion Source I

`2020ApJ...904..158L` | The Astrophysical Journal 2020 | first author: López-Vázquez, J. A. | arXiv: 2010.00132 | DOI: 10.3847/1538-4357/abbe24

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation
- Question: Does the rotating molecular outflow of Orion Src I show rotation, mass and kinematics consistent with a thin-shell model of an anisotropic stellar wind interacting with an Ulrich accretion flow, or with a disk wind?  
  > "We compare the observations with a model of a shell produced by the interaction between an anisotropic stellar wind and an Ulrich accretion flow that corresponds to a rotating molecular envelope in collapse." (abstract)
- Target **Orion Source I**: coordinates _not stated_; z/distance 418±6 pc  
  > "Located at the center of the Kleinmann-Low Nebula in Orion, at a distance $\sim$ 418$\pm$ 6 pc ((cite: Kim_2008))" (Introduction); distance from Kim et al. 2008  
  > "Located at the center of the Kleinmann-Low Nebula in Orion, at a distance $\sim$ 418$\pm$ 6 pc ((cite: Kim_2008))" (Introduction)

## Data provenance

- ALMA projects: 2016.1.00165.S, 2012.1.00123.S
- bands: Band 7  
  > "carried out with the Atacama Large Millimeter/Submillimeter Array (ALMA) in band 7 in 2016 October 31st and 2014 July 26th" (2 Observations)
- frequencies and spectral setup: 2014: 4 spws, 3840 channels, 488 kHz (~0.4 km/s), 29SiO in spw2; 2016: 4 spws, 1920 channels, 976.6 kHz (~0.8 km/s), SiO and SiS in spw0  
  > "The spectral lines reported on this study were found in the spw2 ($^{29}$SiO) of the 2014 observations and the spw0 (SiO and SiS) of the 2016 observations" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 33–820 m (2014); 18–1100 m (2016)  
  > "yielding baselines with projected lengths from 33 to 820 m (41 – 1025 k$\lambda$) and 18 to 1100 m (22 – 1375 k$\lambda$), respectively." (2 Observations)
- angular resolution: 0.19"x0.14" PA -63 deg (SiO, SiS); 0.30"x0.24" PA +58 deg (29SiO)  
  > "at a angular resolution of 0.19$''$ $\times$ 0.14$''$ with a PA of $-$63$^\circ$ and about 20 mJy Beam$^{-1}$ ($^{29}$SiO) at an angular resolution of 0.30$''$ $\times$ 0.24$''$ with a PA of $+$58$^\circ$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: rms ~10 mJy/beam (SiO, SiS); ~20 mJy/beam (29SiO)  
  > "The resulting image rms noises for the spectral lines were about 10 mJy Beam$^{-1}$ (SiO and SiS)" (2 Observations)
- time on source: about 25 min (2014); about 13 min (2016)  
  > "The integration time on-source was about 25 min., and 32 min. was used for calibration for the 2014 observations, while for the 2016 observations was about 13 min. on-source" (2 Observations)
- observing dates: 2014 July 26 and 2016 October 31  
  > "in band 7 in 2016 October 31st and 2014 July 26th" (2 Observations)
- pi or archival as stated: Archival; PIs John Bally (2016.1.00165.S) and Richard Plambeck (2012.1.00123.S)  
  > "The archive observations of Orion Src I were carried out with the Atacama Large Millimeter/Submillimeter Array (ALMA)" (2 Observations)
- Line: 29SiO J=8-7 v=0 (342.9808 GHz)
- Line: SiS J=19-18 v=0 (344.7794 GHz)
- Line: 28SiO J=8-7 v=1 (344.9162 GHz)
- External data: 28SiO abundance relative to H2 of 1.2-2.4e-7 in OMC1 (IRc2)  
  > "we assumed a relative abundance of $^{28}$SiO with respect to H$_2$ of $1.2 -2.4  \times 10^{-7}$, obtained by (cite: Ziurys_1987) in OMC1 (IRc2)" (3.2 Mass of the outflow) [from (cite: Ziurys_1987)]
- External data: 29SiO/28SiO abundance ratio 5e-2 toward evolved stars  
  > "a relative abundance of $^{29}$SiO with respect to $^{28}$SiO of 5$\times$10$^{-2}$, obtained by (cite: Soria_2005) toward evolved stars" (3.2 Mass of the outflow) [from (cite: Soria_2005)]
- External data: Stellar mass 15 Msun  
  > "For our comparison we assume a stellar mass M$_*=15$ M$_\odot$ ((cite: Ginsburg_2018))" (3.3 Comparison with the outflow model) [from (cite: Ginsburg_2018)]
- External data: Expansion velocity ~18 km/s used for kinematic time  
  > "for an expansion velocity $v \sim 18\  {\rm km \ s^{-1}}$ (cite: Greenhill_2013)" (3.2 Mass of the outflow) [from (cite: Greenhill_2013)]
- Simulation/model as data: Thin-shell model of LV19: anisotropic stellar wind (A=1, B=35, n=5) colliding with Ulrich infall, M*=15 Msun, Rcen=40 au, alpha=0.1, beta~4  
  > "a shell formed by a very anisotropic stellar wind, with $A=1$, $B=35$, and $n=5$." (3.3 Comparison with the outflow model)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.1  
  > "The data were calibrated, imaged, and analyzed using the Common Astronomy Software Applications (CASA Version 5.1)." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Attempted on continuum, no good improvement in line maps  
  > "Self-calibration was attempted on the continuum, however, we did not obtain a relatively good improvement in the line maps." (2 Observations)

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

- Outflow thin-shell model and its equations (e.g. non-dimensional mass flux p_m, eq. 47)  
  > "where $p_m$ is the non dimensional mass flux (eq. \[47\] of LV19)" (3.3 Comparison with the outflow model) [from (cite: JALV2019)]
- Excitation temperature and optical depth formulae  
  > "the excitation temperature is (e.g.," (3.2 Mass of the outflow) [from (cite: Estalella_1994)]
- Inclination 10 deg and V_LSR 5 km/s adopted from literature  
  > "Here, we assume an inclination for the outflow of $i=$10$^\circ$, which is similar to the value reported by (cite: Plambeck_2016), (cite: Hirota_2017), and (cite: Baez_2018)." (3.1 Results from the observations) [from (cite: Plambeck_2016); (cite: Hirota_2017); (cite: Baez_2018)]

### Not stated but needed to reproduce (our reading)

- Calibration details (pipeline vs manual, flux calibrator, flux scale uncertainty)
- Imaging parameters: weighting/robust, cell and image size, deconvolver, masks, clean threshold
- Continuum subtraction and line-free channels
- How the observed antenna temperatures (19 K, 14 K) were extracted (position, beam)
- Velocity width and solid angle derivation for the mass
- Positions and ranges of Gaussian fits per height and treatment of the multiple Gaussians
- Whether the two datasets were regridded or smoothed to a common resolution
- Phase center coordinates

## Analysis recipe

1. **Calibrate and image the archival data**: Calibrated, imaged and analysed with CASA; first moment maps and PV diagrams made  
  > "The data were calibrated, imaged, and analyzed using the Common Astronomy Software Applications (CASA Version 5.1)." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Make PV diagrams across the outflow**: Parallel cuts from z=480 au to -480 au at 80 au intervals  
  > "these cuts were made from $z$=480 au to $z$=$-$480 au with intervals of 80 au" (3.1 Results from the observations)
   - software: CASA
   - assumption: Inclination 10 deg, V_LSR = 5 km/s  
  > "Here, we assume an inclination for the outflow of $i=$10$^\circ$" (3.1 Results from the observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure radius, expansion, axial and rotation velocities vs height**: Gaussian fits to intensity profiles: radius from the width at V_LSR=5; v_exp=(v+ - v-)/2, v_z=(v+ + v-)/2; rotation from the difference between outer edges at ±varpi_obs  
  > "The expansion velocity is calculated at the outflow axis as $v_{\rm exp} = (v_+ - v_-)/2$, where $v_\pm$ are the radial velocities corresponding to the width of the Gaussian profile." (5 Measurement procedure)
   - fitting: Gaussian fits; errors from the fit; some require 2 Gaussians  
  > "The red solid lines show the Gaussian fits, some of which require 2 Gaussians." (5 Measurement procedure)
   - validation: _not stated_
4. **Estimate outflow mass and mass loss rate**: Tex from optically thick 28SiO (Ta=19 K); tau of 29SiO from Ta=14 K; LTE mass with X(29SiO/H2)=6-12e-9, dv~30 km/s, solid angle 1.33e-9 sr; kinematic time 130 yr  
  > "we calculate the mass of the outflow as a function of the $^{29}$SiO optical depth as" (3.2 Mass of the outflow)
   - assumption: LTE; 28SiO v=1 optically thick; same Tex for 28SiO and 29SiO  
  > "Assuming that the $^{28}$SiO and $^{29}$SiO molecules coexist" (3.2 Mass of the outflow)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare with thin-shell stellar wind plus Ulrich model**: Choose wind anisotropy parameters minimizing chi^2 of cylindrical radius; integrate shell model in time to 65 yr; compare opening angle, v_exp, v_z, v_rot  
  > "We choose the parameters that minimize $\chi^2$, defined as" (3.3 Comparison with the outflow model)
   - parameter: M*=15 Msun, Rcen=40 au, alpha=0.1, v_w~800 km/s, beta~4  
  > "Assuming a stellar wind velocity $\sim 800$ km s$^{-1}$" (3.3 Comparison with the outflow model)
   - fitting: chi^2 minimization of cylindrical radii  
  > "where $\varpi_{\rm obs}$ is the observed cylindrical radius" (3.3 Comparison with the outflow model)
   - validation: Model compared with data in cylindrical radius, opening angle and velocities  
  > "The comparison between both outflow models with the observational data is shown in Figures [9](#fig:graphicsr) and [10](#fig:graphicsv)." (3.3 Comparison with the outflow model)

## Software

- **CASA** 5.1: calibration, imaging and analysis  
  > "The data were calibrated, imaged, and analyzed using the Common Astronomy Software Applications (CASA Version 5.1)." (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Excitation temperature of 28SiO | 26 | not stated | K | 4 | we obtain $T_{\rm ex}(^{28}{\rm SiO})  =  26$ K |
| 29SiO optical depth | 1.3 | not stated | dimensionless | 4 | we obtain $\tau_0(^{29}{\rm SiO})=1.3$ |
| Outflow mass | 0.66-1.3 | lower limit | Msun | 4 | M}_{\rm outflow}\gtrsim 0.66 - 1.3$ M$_\odot$ |
| Kinematic time | 130 | not stated | yr | 4 | the kinematic time is $t_{kin} \sim 130$ yr |
| Outflow mass loss rate | 5.1-10e-3 | lower limit | Msun/yr | 4 | \gtrsim 5.1 - 10  \times10^{-3}$ M$_\odot$ yr$^{-1}$ |
| Observed rotation velocity | ~4-8 | not stated | km/s | 3 | We find that the rotation velocity ($\sim$4–8 km s$^{-1}$) |
| Model dynamical time | 65 | not stated | yr | 5 | which happens at $t = 65$ yr |
| Required envelope accretion rate | 1.1-2.2e-2 | not stated | Msun/yr | 5 | $\dot{\mathrm{M}}_a = 1.1 - 2.2 \times10^{-2}$ M$_\odot$ yr$^{-1}$ |
| Observed/model rotation velocity ratio | 3-10 | not stated | dimensionless | 5 | The observed rotation velocity is a factor of 3$-$10 larger than those of the anisotropic stellar wind model. |

## Qualitative findings

- Rotation velocity and opening angle decrease with height; cylindrical radius, expansion and axial velocity increase.  
  > "We find that the opening angle (in a range of $\sim$20–60$^\circ$) and the rotation velocity (in a range of $\sim$4–8 km s$^{-1}$) decrease with the height to the disk." (5 Conclusions)

## Claim tuples

- H: Is the outflow massive enough to constrain disk wind models? | E: LTE mass from 28SiO/29SiO, divided by kinematic time | R: M~0.66-1.3 Msun; Mdot~5.1-10e-3 Msun/yr | F: Massive outflow poses constraints on disk wind accretion luminosity and disk lifetime | **supported**
- H: Can a stellar wind and Ulrich envelope shell model reproduce the outflow? | E: Compare LV19 anisotropic wind model with measured radius and velocities | R: Radius, opening angle, v_exp and v_z match; v_rot is 3-10 times too low | F: The Ulrich flow alone cannot explain the rotation | **partially**

## Reasoning

- Why this data: Archival lines trace the outer outflow, easing comparison with the thin shell model  
  > "the archive observations used in this work trace the outer part of the molecular outflow, the latter, because this improves an easily comparison with the thin shell model of LV19." (3 Results and Discussion)
- Why this method: _not stated_
- Alternative: Isotropic wind model does not reproduce observations  
  > "Since the isotropic wind model (dotted lines) does not reproduce the observations" (3.3 Comparison with the outflow model)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass is a lower limit because 28SiO abundance could be lower by up to two orders of magnitude  
  > "This mass is a lower limit because the $^{28}$SiO abundance could be lower by up to two orders of magnitude" (3.2 Mass of the outflow)
- Limitation (authors): Ulrich envelope assumption questionable given the source's proper motion  
  > "Its envelope will not be a gravitational collapsing envelope of the Ulrich type" (3.3 Comparison with the outflow model)
- Caveat (inferred, ours): Mass depends on abundances taken from other sources (OMC1, evolved stars)
- Caveat (inferred, ours): Only one inclination (10 deg) assumed
- Caveat (inferred, ours): Single-pixel antenna temperatures used for Tex and tau
- Caveat (inferred, ours): The model rotation mismatch is not explored with a disk wind model
- Caveat (inferred, ours): Imaging details are missing

## Reproducibility

- Data public (paper): Archival observations from ALMA programs  
  > "The archive observations of Orion Src I were carried out with the Atacama Large Millimeter/Submillimeter Array (ALMA)" (2 Observations)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Calibration details
- Missing: Exact Gaussian fitting setup
- Missing: Shell model code (LV19)
- Data volume (inferred): ~50-100 GB raw for two Band 7 datasets
- Score (inferred): 3/5, Public data and clear analytic formulas, but imaging and fitting details are missing and the shell model code is not provided.
- Rediscovery candidate: no, The recipe lacks imaging details and relies on an external model code.

## Links

- Method: López-Vázquez, Cantó & Lizano 2019 (cite: JALV2019) (Thin shell outflow model used for comparison)
- Companion: (cite: Hirota_2017) (Earlier ALMA observations of Orion Src I outflow rotation)

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 39,
  "rate": 0.527
 },
 "evidence_ok": true
}
```
