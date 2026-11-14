# Spatio-kinematical model of the collimated molecular outflow in the water-fountain nebula IRAS 16342-3814

`2019A&A...629A...8T` | Astronomy and Astrophysics 2019 | first author: Tafoya, D. | arXiv: 1906.06328 | DOI: 10.1051/0004-6361/201834632

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: evolved_stars
- Question: To describe the three-dimensional morphology and kinematics of the molecular gas of the water-fountain nebula IRAS 16342$-$3814.  
  > "To describe the three-dimensional morphology and kinematics of the molecular gas of the water-fountain nebula IRAS 16342$-$3814." (abstract)
- Target **IRAS 16342-3814**: coordinates RA 16:37:39.935, Dec -38:20:17.15 (J2000, continuum peak)  
  > "(J2000) R.A.=16:37:39.935, Dec.=$-$38:20:17.15" (2 CO ALMA data of IRAS 16342-3814); "In this work we adopt a distance to IRAS 16342$-$3814 $D$=2 kpc (cite: Sahai1999)." (3 Spatio-kinematical model of the molecular gas); z/distance D = 2 kpc  
  > "(J2000) R.A.=16:37:39.935, Dec.=$-$38:20:17.15" (2 CO ALMA data of IRAS 16342-3814); "In this work we adopt a distance to IRAS 16342$-$3814 $D$=2 kpc (cite: Sahai1999)." (3 Spatio-kinematical model of the molecular gas); distance from Sahai et al. 1999  
  > "(J2000) R.A.=16:37:39.935, Dec.=$-$38:20:17.15" (2 CO ALMA data of IRAS 16342-3814); "In this work we adopt a distance to IRAS 16342$-$3814 $D$=2 kpc (cite: Sahai1999)." (3 Spatio-kinematical model of the molecular gas)

## Data provenance

- ALMA projects: 2012.1.00678.S, 2018.1.00250.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 43 12-m antennas (CO 1-0)  
  > "using 43-12m antennas with a maximum and minimum baselines of 740 m and 15 m, respectively" (2 CO ALMA data of IRAS 16342-3814)
- configurations: _not stated_
- baselines: 15 m to 740 m (CO 1-0)  
  > "maximum and minimum baselines of 740 m and 15 m, respectively" (2 CO ALMA data of IRAS 16342-3814)
- angular resolution: ~1 arcsec (CO 1-0)  
  > "The resulting angular resolution was around 1$^{\prime\prime}$" (2 CO ALMA data of IRAS 16342-3814)
- max recoverable scale: 11.8 arcsec (CO 1-0)  
  > "the maximum recoverable scale was 11$\rlap{.}^{\prime\prime}$8" (2 CO ALMA data of IRAS 16342-3814)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: CO(1-0): December 9 2018  
  > "were carried out on December 9 2018 using 43-12m antennas" (2 CO ALMA data of IRAS 16342-3814)
- pi or archival as stated: CO 3-2: archival, PI R. Sahai; CO 1-0: PI D. Tafoya  
  > "project 2012.1.00678.S (PI: R. Sahai)" (2 CO ALMA data of IRAS 16342-3814)
- Line: CO J=3-2 (not stated)
- Line: CO J=1-0 (not stated)
- External data: Systemic velocity v_sys,LSR = 45 km/s  
  > "assumed to be v$_{\rm sys, LSR}$=45 km s$^{-1}$ (cite: Sahai2017)" (2 CO ALMA data of IRAS 16342-3814) [from (cite: Sahai2017)]
- External data: Inclination 45 deg from H2O maser 3D velocities  
  > "which (cite: Claussen2009) obtained by measuring the inclination angle of the three-dimensional velocity vectors of the H$_{2}$O masers" (3 Spatio-kinematical model of the molecular gas) [from (cite: Claussen2009)]
- External data: CO abundance f(CO)=3e-4  
  > "$f$(CO)=3$\times$10$^{-4}$ (cite: Sahai2017)" (4 Discussion) [from (cite: Sahai2017)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline (CO 1-0 data)  
  > "The data were calibrated with the ALMA pipeline using the CASA version 5.4.0-68." (2 CO ALMA data of IRAS 16342-3814)
- casa version: CASA 5.4.0-68  
  > "using the CASA version 5.4.0-68" (2 CO ALMA data of IRAS 16342-3814)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: phase self-calibration (CO 1-0)  
  > "the data were self-calibrated in phase following the standard self-calibration guidelines for ALMA data" (2 CO ALMA data of IRAS 16342-3814)

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

- Spectral setup, sensitivity, resolution of CO(3-2) data reported in earlier paper  
  > "The spectral setup, sensitivity, angular resolution and results of the observations of the CO($J$=3$\rightarrow$2)" (2 CO ALMA data of IRAS 16342-3814) [from (cite: Sahai2017)]
- Outflow energetics computed following Bujarrabal et al. method  
  > "in the way introduced by (cite: Bujarrabal2001)" (4.3 Kinetic energy and scalar momentum) [from (cite: Bujarrabal2001)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters of the CO(3-2) cube (weighting, cell, channel width, beam, rms)
- Continuum subtraction and line-free channels
- SHAPE model files and exact geometry/density/temperature profiles
- Slit width and length for PV diagrams
- Fit uncertainties/initial guesses for sinusoid fit
- CO(3-2) rest frequency and conversion used for mass spectrum
- Self-calibration solint for CO(1-0)

## Analysis recipe

1. **Extract emission peak positions per channel**: Peak position of brightness in each channel with JMFIT; centroid by unweighted mean used as reference  
  > "we extracted the peak position of the brightness distribution in every channel within the velocity range $-235$\<v$_{\rm LSR}$(km s$^{-1}$)\<+325 using the task JMFIT of AIPS" (2 CO ALMA data of IRAS 16342-3814)
   - software: AIPS
   - assumption: v_sys = 45 km/s  
  > "assumed to be v$_{\rm sys, LSR}$=45 km s$^{-1}$ (cite: Sahai2017)" (2 CO ALMA data of IRAS 16342-3814)
   - fitting: _not stated_
   - validation: _not stated_
2. **Build spatio-kinematical model in SHAPE**: Power-law velocity field, LVC and HVC structures; synthetic images and PV diagrams compared by eye iteratively  
  > "The synthetic P-V diagram obtained with SHAPE and the one from the observations were compared by eye." (3.1 3D modelling with SHAPE)
   - software: SHAPE
   - parameter: HVC: vi=382, vf=212 km/s, eta=4.5; LVC: vi=5, vf=212 km/s, eta=1.6  
  > "v$_{\rm i, HVC}$=382 km s$^{-1}$, v$_{\rm f, HVC}$=212 km s$^{-1}$ and $\eta_{\rm HVC}$=4.5" (3.1 3D modelling with SHAPE)
   - assumption: inclination 45 deg, D=2 kpc, LTE, constant density and Tex for HVC  
  > "the density of the gas and the excitation temperature of the HVC were assumed to be constant throughout the outflow" (3.1 3D modelling with SHAPE)
   - fitting: _not stated_
   - validation: Synthetic PV diagram reproduces main features of observed PV  
  > "The synthetic P-V diagram in Fig. [5](#Fig5)a reproduces very well the main features of the CO($J$=3$\rightarrow$2) emission P-V diagram." (3.1 3D modelling with SHAPE)
3. **Mass spectrum and energetics**: Mass vs velocity from CO(3-2) line profile, optically thin LTE; kinetic energy and momentum summed over channels  
  > "assuming optically thin emission, LTE conditions and an average excitation temperature $T_{\rm ex}$=30 K" (4 Discussion)
   - assumption: Tex=30 K, f(CO)=3e-4, deprojection 1/sin45  
  > "$f$(CO)=3$\times$10$^{-4}$ (cite: Sahai2017)" (4 Discussion)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit precession sinusoid to peak positions**: Fit y(r)=A r sin(2 pi tau(r)/T - phi) to rotated peak positions with constant deceleration  
  > "We fitted the precession model given by Equation [\[Eq:2\]](#Eq:2) to the data points of the pattern seen in Fig. [8](#Fig8)." (4.4 The precessing jet)
   - parameter: theta_rot 23-23.9 deg  
  > "Considering the P.A. of the line connecting the H$_{2}$O masers detected by (cite: Claussen2009), the rotation angle is $\theta_{\rm rot}$=23$\rlap{.}^{\circ}$9" (4.4 The precessing jet)
   - fitting: _not stated_
   - validation: Results depend on rotation angle; not discriminated  
  > "it is difficult to discern which rotation angle gives the best fit" (4.4 The precessing jet)

## Software

- **SHAPE** : 3D spatio-kinematical modelling and synthetic images/PV  
  > "We used the spatio-kinematic modelling tool SHAPE (cite: Steffen2011)" (3.1 3D modelling with SHAPE)
- **AIPS** : JMFIT peak positions  
  > "using the task JMFIT of AIPS" (2 CO ALMA data of IRAS 16342-3814)
- **CASA** 5.4.0-68: Pipeline calibration of CO(1-0)  
  > "The data were calibrated with the ALMA pipeline using the CASA version 5.4.0-68." (2 CO ALMA data of IRAS 16342-3814)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Jet lifetime (constant deceleration) | 70 | not stated | yr | 2 | $\tau_{\rm jet}$=2$\times$$r_{\rm max}/({\rm v}_{\rm i}+{\rm v}_{\rm f})$$\approx$70 years |
| Mass spectrum slope gamma (10-100 km/s) | 0.94 | not stated | dimensionless | 3 | described by a power-law $m$(v)$\propto$v$^{-\gamma}$ with $\gamma$=0.94 |
| Total outflow mass | 1.6e-2 | not stated | Msun | 3 | $M_{\rm outflow}$=1.6$\times$10$^{-2}$ $M_{\odot}$ |
| Jet mass-loss rate | 5e-6 | not stated | Msun/yr | 3 | $\dot{M}_{\rm jet}$=5$\times$10$^{-6}$ $M_{\odot}$ yr$^{-1}$ |
| Precession period (theta_rot=23.5 deg) | 72 | 4 | yr | 4 | $A$=0.014$\pm$0.001, $T$=72$\pm$4 yrs |

## Qualitative findings

- LVC consistent with swept-up gas in jet-driven bow shock; HVC decelerating jet/entrained material  
  > "we conclude that the LVC in IRAS 16342$-$3814 corresponds to material of the CSE that has been swept-up by the jet-driven bow shock." (4 Discussion)

## Claim tuples

- H: Peak-position PV structure arises from real velocity gradients in a narrow outflow, not a wide-angle constant-speed outflow | E: SHAPE model with HVC and LVC power-law velocity fields compared with CO(3-2) PV | R: Synthetic PV reproduces observed S-shape | F: Collimated decelerating HVC inside accelerating LVC | **supported**
- H: The outflow is jet-driven | E: Mass spectrum power laws and morphology | R: Double power law gamma 0.94 and 3.2 | F: Consistent with jet-driven outflow | **supported**
- H: The HVC peak positions trace a precessing jet | E: Sinusoid fit to peak positions | R: T~60-90 yr, opening angle ~2 deg | F: Small-angle precession compatible with IR corkscrew | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Sahai et al. 2017 constant-velocity wide-angle (~90 deg) model rejected  
  > "The constant expansion velocity assumption is most likely not true" (4 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass and slopes are lower limits if CO(3-2) optically thick  
  > "if the CO($J$=3$\rightarrow$2) line is optically thick, the values of these power-law exponents represent just a lower limit" (4 Discussion)
- Caveat (inferred, ours): Model fit by eye with no uncertainties or degeneracy exploration
- Caveat (inferred, ours): Precession parameters depend strongly on the arbitrary rotation angle
- Caveat (inferred, ours): Unresolved HVC width and peak-position scatter limit the sinusoid

## Reproducibility

- Data public (paper): CO(3-2) retrieved from the ALMA archive  
  > "We retrieved archive ALMA data of the project 2012.1.00678.S" (2 CO ALMA data of IRAS 16342-3814)
- Products in archive: _not stated_
- Missing: SHAPE model files
- Missing: Imaging settings for CO(3-2) cube
- Missing: PV slit definition
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and clear model parameters, but by-eye modelling and missing imaging details.
- Rediscovery candidate: no, Main model is fitted by eye in SHAPE and imaging details are missing, although some numbers are reproducible.

## Links

- Method: (cite: Steffen2011) (SHAPE modelling tool)
- Method: (cite: Bujarrabal2001) (Energetics method)
- Companion: (cite: Sahai2017) (Original ALMA analysis of the same CO data)

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
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
  "facts": 71,
  "stated": 36,
  "rate": 0.507
 },
 "evidence_ok": true
}
```
