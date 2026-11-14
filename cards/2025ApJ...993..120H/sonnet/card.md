# Early Planet Formation in Embedded Disks (eDisk). XVII. A Compact but Structured Keplerian Disk and Large-scale Streamers Revealed in the Class I Protostellar System IRAS 04169+2702

`2025ApJ...993..120H` | The Astrophysical Journal 2025 | first author: Han, Ilseung | arXiv: 2506.16569 | DOI: 10.3847/1538-4357/ade684

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: star_formation, protoplanetary_disks
- Question: Does the Class I protostar IRAS 04169+2702 host a Keplerian disk with substructure, and what is the nature of the large-scale spiral structures around it (streamers vs outflow)?  
  > "The position-velocity diagrams of these lines unveil a Keplerian-rotating disk with a radius of $\sim$21 au around a 1.3 $M_{\odot}$ protostar" (abstract)
- Target **IRAS 04169+2702 (I04169)**: coordinates ICRS 04h19m58.475s, +27d09m56.81s (Gaussian center of LB-only image)  
  > "In this paper, we adopt 156 pc as the distance to I04169" (Introduction); "The Gaussian center of this image is at $\alpha_{\rm ICRS}$ $=$ 04$^{\rm h}$19$^{\rm m}$58.475s" (3.1.1 ALMA); z/distance 156 pc  
  > "In this paper, we adopt 156 pc as the distance to I04169" (Introduction); "The Gaussian center of this image is at $\alpha_{\rm ICRS}$ $=$ 04$^{\rm h}$19$^{\rm m}$58.475s" (3.1.1 ALMA); distance from mean distance to Taurus B213 from Gaia EDR3 (Krolikowski et al. 2021)  
  > "In this paper, we adopt 156 pc as the distance to I04169" (Introduction); "The Gaussian center of this image is at $\alpha_{\rm ICRS}$ $=$ 04$^{\rm h}$19$^{\rm m}$58.475s" (3.1.1 ALMA)

## Data provenance

- ALMA projects: 2019.1.00261.L
- bands: Band 6 (1.3 mm); VLA Q, K, C  
  > "We observed I04169 using ALMA in Band 6" (2.1 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-8 (LB, four executions) and C43-5 (SB, two executions)  
  > "the observations were made in the C43-8 and C43-5 configurations, from 2021 September 30 to October 24 and on 2022 July 3, respectively" (2.1 ALMA)
- baselines: _not stated_
- angular resolution: ~0.05'' (8 au) in SBLB continuum; LB-only 0.044''x0.034''  
  > "We present high-resolution ($\sim$0.05$''$; 8 au) dust continuum" (abstract)
- max recoverable scale: 2.30-3.50'' (LB), 10.73'' (SB)  
  > "C43-5 & 41 & 15–1301 & 10.73 & 20.16" (Table 1)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2021 Sep 30 to Oct 24 (LB); 2022 Jul 3 (SB); VLA 2020 Dec 10, 24, 30  
  > "from 2021 September 30 to October 24 and on 2022 July 3, respectively" (2.1 ALMA); "on 2020 December 10, 24, and 30" (2.2 VLA)
- pi or archival as stated: eDisk Large Program, PI Nagayoshi Ohashi; VLA Program 20B-322  
  > "(Program 20B-322)" (2.2 VLA)
- Line: 12CO 2-1 (230.538000 GHz)
- Line: 13CO 2-1 (220.398684 GHz)
- Line: C18O 2-1 (219.560354 GHz)
- Line: SO 6_5-5_4 (219.949442 GHz)
- Line: H2CO 3_0,3-2_0,2 (218.222192 GHz)
- Other facility **VLA**: A-configuration Q, K, C-band continuum for free-free/spectral index  
  > "observed with the Karl G. Jansky Very Large Array (VLA) in the A configuration at the Q- (0.7 cm), K- (1.4 cm), and C-bands (5.0 cm)" (2.2 VLA)
- Other facility **Gaia**: distance to B213  
  > "reported the mean distance to B213 as 155.94 pc, using the early third data release of *Gaia*" (Introduction)
- External data: Bolometric luminosity 1.4 Lsun and Tbol 161 K  
  > "re-calculated its bolometric luminosity and temperature to be 1.4 $L_{\odot}$ and 161 K, respectively" (Introduction) [from (cite: 2023ApJ...951....8O)]
- External data: Dust temperature scaling relation T=43 K (L/Lsun)^0.25 (R/50 au)^-0.5  
  > "$T_{\rm dust}$ $=$ 43 K ($L_{\rm bol}$/$L_{\odot}$)$^{0.25}$" (3.1.1 ALMA) [from (cite: 2020ApJ...890..130T; 2022ApJ...929...76S)]

## Processing

### Calibration

- pipeline or manual: ALMA calibration pipeline in CASA  
  > "The standard calibration was carried out using the ALMA calibration pipeline included in the Common Astronomy Software Application" (2.1 ALMA)
- casa version: CASA 6.2.1  
  > "version 6.2.1, and subsequent imaging and self-calibration were also carried out with the same CASA version" (2.1 ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0238+1636 and J0510+1800  
  > "J0510$+$1800 & J0438$+$3004" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: SB: 6 phase-only + 2 phase&amp; amp iterations; SBLB: 5 phase-only + 2 phase&amp; amp after SB step  
  > "For the SB-only data, we did six iterations of phase-only self-calibration and two iterations of phase and amplitude self-calibration." (2.1 ALMA)

### Imaging

- task: CASA tclean  
  > "using the CASA task *tclean*" (2.1 ALMA)
- deconvolver: _not stated_
- weighting robust: Continuum: SB 2.0, SBLB 0.5, LB 0.0; lines: 2.0; VLA Q 1.0, K 0.0, Chigh 1.0, Clow 0.0  
  > "SB-only (robust = 2.0), SBLB (0.5), and LB-only (0.0)" (2.1 ALMA)
- uv taper: 2000 kλ circular Gaussian for line SBLB and LB images  
  > "uv-tapered by a circular Gaussian with a full width at half maximum (FWHM) of 2000 $k\lambda$" (2.1 ALMA)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied  
  > "All the images were corrected for the primary beam attenuation." (2.1 ALMA)
- array combination: SB self-calibrated then combined with LB (SBLB)  
  > "the self-calibrated SB data were combined with the LB data to self-calibrate the combined data set (hereafter SBLB)" (2.1 ALMA)
- smoothing: _not stated_
- final beam: Continuum LB 0.044''x0.034''; SBLB 0.071''x0.052''; SB 0.463''x0.331''  
  > "LB & & & 0.0 & 0.044 $\times$ 0.034 & (19.1)" (Table 2)
- final rms: Continuum: 30.0 (SB), 13.1 (SBLB), 18.8 (LB) µJy/beam  
  > "SBLB & & & 0.5 & 0.071 $\times$ 0.052 & (28.0) & 13.1" (Table 2)

### Inherited from earlier work

- Correlator setup and visibility calibration details  
  > "Further details of the observations, such as the correlator setup and visibility calibration, should be referred to (cite: 2023ApJ...951....8O)." (2.1 ALMA) [from (cite: 2023ApJ...951....8O)]
- Overall data reduction procedures and imaging scripts  
  > "Details of the overall procedures are explained in (cite: 2023ApJ...951....8O)." (2.1 ALMA) [from (cite: 2023ApJ...951....8O); scripts (cite: 2023zndo...7986682T)]
- VLA observations, reduction and imaging  
  > "Details of the observations, data reduction, and imaging procedures are described in (cite: 2022ApJ...934...95S)" (2.2 VLA) [from (cite: 2022ApJ...934...95S)]
- SLAM ridge/edge PV fitting procedure  
  > "The overall fitting procedure is further described in (cite: 2023ApJ...951....8O) and (cite: 2024PKAS...39...2A)." (4.2 Kinematics) [from (cite: 2023ApJ...951....8O); (cite: 2024PKAS...39...2A)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction method for line cubes
- Self-calibration solution intervals and masks
- tclean cell size, image size, deconvolver, masks and thresholds
- SLAM fitting settings (PV cut width, thresholds for ridge/edge, outer radius range)
- Details of the two-component SED fit (fitting code, initial values, fixed alpha_free)
- Which VLA flux scale and region definitions were used for central vs entire disk
- Exact velocity channels used for moment maps

## Analysis recipe

1. **Self-calibrate and image ALMA data**: Pipeline calibration, iterative phase and amplitude self-calibration on SB then SBLB, tclean imaging of SB, SBLB, LB-only  
  > "The self-calibration was performed on the SB-only data, and then the self-calibrated SB data were combined with the LB data" (2.1 ALMA)
   - software: CASA
   - parameter: robust 2.0/0.5/0.0 for continuum SB/SBLB/LB  
  > "SB-only (robust = 2.0), SBLB (0.5), and LB-only (0.0)" (2.1 ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum disk size, inclination, peaks**: Elliptical Gaussian fitting; inclination from axis ratio cos^-1(min/maj); separate Gaussian fits of two peaks  
  > "estimate the disk inclination angle to be 43$\ensuremath{^\circ}$ by assuming that the disk is geometrically thin" (3.1.1 ALMA)
   - software: CASA
   - assumption: geometrically thin disk  
  > "by assuming that the disk is geometrically thin" (3.1.1 ALMA)
   - fitting: elliptical Gaussian  
  > "The compact component, when fitted with an elliptical Gaussian" (3.1.1 ALMA)
   - validation: compared three radial intensity cuts  
  > "we compare three radial intensity cuts, which are along the major and minor axes and along the two peaks" (3.1.1 ALMA)
3. **Derive dust and disk mass**: Optically thin isothermal dust mass formula with kappa=2.25 cm2/g at 225 GHz, T=20 K and 61 K, gas-to-dust 100  
  > "Adopting the two temperatures of 20 and 61 K, the dust masses of the protostellar disk are derived to be 67 and 18 $M_{\ensuremath{\oplus}}$" (3.1.1 ALMA)
   - parameter: kappa = (nu/100 GHz)^beta, beta=1 giving 2.25 cm2/g  
  > "The dust opacity adopted at this frequency is 2.25 cm$^{2}$ g$^{-1}$" (3.1.1 ALMA)
   - assumption: gas-to-dust ratio 100; d=156 pc; optically thin  
  > "Assuming a typical gas-to-dust mass ratio of 100" (3.1.1 ALMA)
   - fitting: _not stated_
   - validation: lower limits if optically thick  
  > "Note that our mass estimates would be lower limits if the 1.3-mm continuum emission is optically thick." (3.1.1 ALMA)
4. **Proper-motion correct VLA vs ALMA and fit radio SED**: Proper motion from I04166 imfit centers applied to I04169; two power-law (dust + free-free) fit of 1.3 mm to 6 cm fluxes  
  > "We simultaneously fit each spectrum with two single power-law functions: one corresponds to free-free emission and the other thermal dust emission." (4.1 Disk Substructure)
   - software: CASA
   - fitting: two power laws, statistical uncertainties only; sampler/priors not stated  
  > "Note that we only consider statistical uncertainty here." (4.1 Disk Substructure)
   - validation: _not stated_
5. **Measure kinematics with PV fitting**: SLAM ridge and edge methods on LB-only PV diagrams of 12CO, 13CO, C18O along major axis, high-velocity ranges only, single power-law rotation curve  
  > "The fitting is performed using two independent methods: the ridge method and the edge method." (4.2 Kinematics)
   - software: SLAM
   - parameter: Vsys 6.9 km/s, inclination 43 deg; thresholds 5σ (12CO, C18O), 6σ (13CO)  
  > "We then use the emission above the 5$\sigma_{\rm ^{12}CO}$ level for the fitting" (4.2 Kinematics)
   - assumption: p fixed to 0.5 for 12CO mass; final mass is mean of ridge and edge  
  > "we performed the fitting again to $^{12}$CO by assuming the rotation curve index $p$ of 0.5" (4.2 Kinematics)
   - fitting: single power-law V ∝ R^-p  
  > "we adopted a single power-law rotation curve ($V_{\rm rot}$ $\propto$ $R^{-p}$)" (4.2 Kinematics)
   - validation: Keplerian radius from ridge-method intersections of 12CO with 13CO/C18O profiles; edge radii rejected  
  > "we only rely on the two pairs derived from the ridge method" (4.2 Kinematics)
6. **Characterize streamers vs outflow**: Moment 0/1/2/8/9 maps and channel maps; compare velocity dispersion of 12CO, 13CO, C18O  
  > "Figure [9](#fig:mom2) shows the velocity dispersion (moment 2) maps of the SBLB $^{12}$CO, $^{13}$CO, and C$^{18}$O emission." (4.3.1 Nature of Streamers)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.2.1: calibration pipeline, self-calibration, tclean imaging, imfit  
  > "version 6.2.1, and subsequent imaging and self-calibration were also carried out with the same CASA version" (2.1 ALMA)
- **SLAM** : ridge and edge PV diagram fitting for rotation curves and dynamical mass  
  > "We employ the public Python package, Spectral Line Analysis/Modeling (SLAM)" (4.2 Kinematics)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Deconvolved continuum disk FWHM (LB-only) | 0.22'' x 0.16'' (34 x 25 au), PA 140 deg | not stated | arcsec | 2 | for the LB-only image, they are 0.22$''$ $\times$ 0.16$''$ (34 au $\times$ 25 au) and 140$\ensuremath{^\circ}$, respectively |
| Disk inclination | 43 | not stated | deg | 2 | estimate the disk inclination angle to be 43$\ensuremath{^\circ}$ |
| Flux density within 3σ, LB-only | 91.71 | 2.02 | mJy | 2 | 92.19 $\pm$ 1.64 and 91.71 $\pm$ 2.02 mJy, respectively |
| Projected separation of two continuum peaks | 0.11 (17 au) | not stated | arcsec | 2 | The projected separation of the two peaks is 0.11$''$ (17 au). |
| Dust mass (T=20 K / 61 K) | 67 / 18 | not stated | Earth masses | 3 | the dust masses of the protostellar disk are derived to be 67 and 18 $M_{\ensuremath{\oplus}}$, respectively |
| Dust temperature from Tobin/Sheehan relation | 61 | not stated | K | 3 | the dust temperature of I04169 is derived to be 61 K |
| Dust spectral index, entire disk | 2.848 | 0.040 | dimensionless | 4 | the spectral index is $\alpha_{\rm dust}$ $=$ 2.848 $\pm$ 0.040 |
| Dust spectral index, central region | 2.323 | 0.332 | dimensionless | 4 | $\alpha_{\rm dust}$ $=$ 2.323 $\pm$ 0.332 |
| Free-free spectral index, entire disk | 0.166 | 0.094 | dimensionless | 4 | $\alpha_{\rm free}$ $=$ 0.166 $\pm$ 0.094 |
| Dynamical mass, ridge method | 0.766 | 0.059 | Msun | 5 | 0.766 $\pm$ 0.059 $M_{\odot}$ in the ridge method and 2.007 $\pm$ 0.071 $M_{\odot}$ in the edge method |
| Dynamical mass, edge method | 2.007 | 0.071 | Msun | 5 | 0.766 $\pm$ 0.059 $M_{\odot}$ in the ridge method and 2.007 $\pm$ 0.071 $M_{\odot}$ in the edge method |
| Adopted protostellar mass (mean) | 1.312 | 0.044 | Msun | 5 | which is 1.312 $\pm$ 0.044 $M_{\odot}$ |
| Rotation index p, 13CO (ridge / edge) | 1.012 / 0.933 | 0.058 / 0.074 | dimensionless | 5 | The index $p$ is derived as 1.012 $\pm$ 0.058 in the ridge method and 0.933 $\pm$ 0.074 in the edge method. |
| Keplerian radius range | 18-24 | not stated | au | 5 | The Keplerian radius is expected to be somewhere between 18 and 24 au. |
| Systemic velocity | 6.9 | not stated | km/s | 5 | we use 6.9 km s$^{-1}$ as the systemic velocity in this paper |

## Qualitative findings

- Q-band VLA emission is centrally peaked between the two ALMA peaks and dominated by free-free emission at the center, coinciding with the 1.3-mm depression  
  > "Our VLA observations of the same target reveal a single central peak dominated by the free-free emission" (abstract)
- C18O, SO and H2CO S-shaped spirals are infalling streamers extending to ~1400 au, distinct from the outflow  
  > "large-scale infalling spiral structures extending up to approximately 1400 au, streamers, are discovered" (abstract)

## Claim tuples

- H: Does the disk host a Keplerian rotator and what is the central mass? | E: SLAM ridge/edge PV fits of LB-only 12CO, 13CO, C18O | R: 12CO p~0.5-0.73; 13CO and C18O p~1; mass 1.312 Msun; Keplerian radius 18-24 au | F: Compact Keplerian disk around ~1.3 Msun protostar with infalling rotating envelope | **supported**
- H: Are the two continuum peaks a binary, and what causes the central depression? | E: Compare ALMA LB with VLA Q/K/C and fit dust+free-free SED | R: VLA single peak between ALMA peaks; free-free dominates the center | F: Peaks are not two distinct protostars; depression is a dust deficit; a closer binary cannot be excluded | **partially**
- H: Are the spiral features outflow or infalling streamers? | E: Morphology, moment 2 velocity dispersion, velocity gradients | R: C18O dispersion <0.5 km/s, velocity increases toward center along arms | F: Spirals are infalling streamers | **supported**
- H: Have grains grown in the disk? | E: Dust spectral index from 1.3 mm to 1.4 cm | R: alpha_dust = 2.848 ± 0.040 | F: Suggests grains grown to mm/cm sizes | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: LB-only data used for kinematics because they include the least non-disk components; ridge and edge methods used as they may under/overestimate mass  
  > "Our fitting was performed using the LB-only data since they include the least non-disk components" (4.2 Kinematics)
- Alternative: Edge-method Keplerian radii (3 and 7 au) rejected as inconsistent with data points  
  > "This does not make sense because a rotation velocity curve generally exhibits a break at a point where infalling motion is changed into Keplerian motion." (4.2 Kinematics)
- Alternative: Streamer origin: cloudlet capture considered less likely than magnetic misalignment or multiple-system interactions  
  > "It is thus less likely that multiple cloudlets were captured by this system simultaneously." (4.3.2 Origins of Streamers)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust mass may be a lower limit if emission is optically thick  
  > "Note that our mass estimates would be lower limits if the 1.3-mm continuum emission is optically thick." (3.1.1 ALMA)
- Limitation (authors): A closer unresolved binary cannot be ruled out  
  > "we cannot entirely rule out a possibility of a closer binary" (4.1 Disk Substructure)
- Caveat (inferred, ours): Ridge and edge masses differ by factor ~2.6; averaging is ad hoc
- Caveat (inferred, ours): 12CO not resolving the compact disk makes the mass and Keplerian radius uncertain
- Caveat (inferred, ours): Only statistical uncertainties in SED fits and fluxes
- Caveat (inferred, ours): Streamer origin is not discriminated quantitatively; no modeling
- Caveat (inferred, ours): VLA free-free/dust decomposition with five points is weakly constrained

## Reproducibility

- Data public (paper): Large Program data; reduction scripts on GitHub/Zenodo; SLAM public  
  > "the imaging scripts for this target can be found in (cite: 2023zndo...7986682T)" (2.1 ALMA)
- Products in archive: _not stated_
- Code: eDisk reduction scripts (Zenodo) and SLAM on GitHub  
  > "<https://github.com/jinshisai/SLAM>" (Footnote 2)
- Missing: Line-free channels / continuum subtraction
- Missing: SLAM parameter settings
- Missing: SED fit details
- Missing: tclean image parameters (cell, size, masks)
- Data volume (inferred): ~100-300 GB raw ALMA (6 EBs, 2 configs) plus VLA data
- Score (inferred): 3/5, Public ALMA data and scripts with clear numeric results, but key imaging, SLAM and SED fit settings are deferred to companion papers or unstated.
- Rediscovery candidate: yes, Public eDisk data, public scripts, SLAM public, and numeric results (mass, spectral index, dust mass) available.

## Links

- Method: (cite: 2023ApJ...951....8O) (eDisk overview: correlator setup, calibration, SLAM fitting procedure)
- Method: (cite: 2024PKAS...39...2A) (SLAM code)
- Method: (cite: 2022ApJ...934...95S) (VLA observations and reduction)
- Method: (cite: 2023zndo...7986682T) (eDisk imaging scripts)
- Companion: (cite: 2023ApJ...951....8O) (eDisk survey overview)
- Related: eDisk (2019.1.00261.L)
- Related: VLA program 20B-322

## Checks

```json
{
 "quotes": 88,
 "quotes_ok": 88,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 58,
  "rate": 0.69
 },
 "evidence_ok": true
}
```
