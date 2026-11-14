# Geometric and Kinematic Structure of the Outflow/Envelope System of L1527 Revealed by Subarcsecond-resolution Observation of CS

`2015ApJ...812...59O` | The Astrophysical Journal 2015 | first author: Oya, Yoko | arXiv: 1604.08005 | DOI: 10.1088/0004-637X/812/1/59

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: star_formation
- Question: What are the inclination direction and outflow cavity structure of the L1527 outflow/envelope system, from CS (J=5-4) kinematics?  
  > "In this paper, we report the determination of the inclination angle and morphological properties of the outflow." (Introduction)
- Target **L1527 (IRAS 04368+2557)**: coordinates _not stated_; z/distance 137 pc  
  > "IRAS 04368+2557 in L1527 ($d$=137 pc) is a representative Class 0 low-mass protostar" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00604.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.8" x 0.7" (P.A. = -6 deg) for CS J=5-4 and c-C3H2  
  > "The synthesized beam size is $0.8\ensuremath{''} \times 0.7\ensuremath{''}$ (P.A. = $-6\ensuremath{^\circ}$) for the CS ($J$=5–4) and c-C$_3$H$_2$ ($5_{2, 3}$–$4_{3, 2}$) lines." (2 Results)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA Cycle 0 data reported by Sakai et al. (2014b)  
  > "We used the ALMA Cycle 0 data ($\#$2011.0.00604S) reported by Sakai et al. (2014b)." (2 Results)
- Line: CS J=5-4 (244.9355565 GHz)
- Line: c-C3H2 5(2,3)-4(3,2) (249.0543680 GHz)
- Other facility **JCMT, Gemini North, Spitzer IRAC**: Previously published 12CO(3-2), L' band and 3.6 um images used for comparison  
  > "Tobin et al. (2008, 2010) conducted $L^\prime$ band imaging of this source with the Gemini North telescope" (Introduction)
- External data: Dynamical timescales and outflow parameters of comparison sources (Table 2)  
  > "The dynamical timescales in Table [2](#tb:params) are taken from Yıldız et al. (2015)." (4.3 Comparison with other sources) [from Yıldız et al. (2015); Lee et al. (2000); Hirano et al. (2010); Arce et al. (2013)]
- External data: Protostellar mass 0.18 Msun and centrifugal barrier radius 100 AU  
  > "the protostellar mass and the radius of the centrifugal barrier are assumed to be 0.18 $M_\odot$ and 100 AU, respectively, which are derived by Sakai et al. (2014b)." (Appendix) [from Sakai et al. (2014b)]
- External data: Outflow origin offset 0.62" (~85 AU)  
  > "We therefore adopt the offset ($0.62\ensuremath{''} \sim 85$ AU) of the outflow origin reported by Tobin et al. (2010) in the model." (2.3 Outflow) [from Tobin et al. (2010)]

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

- Infalling rotating envelope ballistic model details  
  > "Details of this model are described in the paper investigating another low-mass protostellar source: IRAS 15398–3359 (Oya et al. 2014)." (2.2 Envelope) [from Oya et al. 2014]
- Parabolic outflow cavity model  
  > "We employ a standard model of the outflow structure for the analysis (Lee et al. 2000; Oya et al. 2014)." (2.3 Outflow) [from Lee et al. 2000; Oya et al. 2014]
- ALMA data calibration/imaging from earlier paper  
  > "We used the ALMA Cycle 0 data ($\#$2011.0.00604S) reported by Sakai et al. (2014b)." (2 Results) [from Sakai et al. (2014b)]

### Not stated but needed to reproduce (our reading)

- Calibration and imaging details (CASA version, weighting, cleaning, continuum subtraction)
- Spectral resolution and channel width of the cubes
- PV extraction widths and line position angles
- Model grid and procedure for the by-eye fits
- Procedure for the exponential fits in Figs. 10-11

## Analysis recipe

1. **Compare observed CS PV diagrams with ballistic envelope model at +5 and -5 deg**: PV diagrams along six lines through protostar compared with infalling-rotating envelope model; inclination sign decided by eye, with rms of difference along 270 deg  
  > "the rms of the difference for the PV diagram along the “$270\ensuremath{^\circ}$" line is 0.022 Jy beam$^{-1}$ for the inclination angle of $-5\ensuremath{^\circ}$" (2.2 Envelope)
   - parameter: M=0.18 Msun, r_CB=100 AU, outer radius 1000 AU, density ∝ r^-1.5, line width 0.5 km/s, beam 0.5"x0.5"  
  > "The outer radius of the envelope is fixed to be 1000 AU, which well reproduces the PV diagram of CCH (Sakai et al. 2014a)." (Appendix)
   - assumption: Optically thin line, Gaussian profile  
  > "The spectral line is assumed to be optically thin, and to have a Gaussian profile with the line width of 0.5 km s$^{-1}$." (Appendix)
   - fitting: _not stated_
   - validation: Rms of difference judged not statistically meaningful given model simplicity  
  > "the statistical argument based on the rms of the difference is almost meaningless, as mentioned above." (2.2 Envelope)
2. **Fit parabolic outflow cavity model**: Parabolic cavity wall with linear velocity field, inclination fixed to +5 deg, offset origin 0.62", C and v0 fitted by eye to PV diagrams  
  > "The parameters are: $C = 0.05\ {\rm arcsec}^{-1}$ and $v_0 = 0.10\ {\rm km\ s}^{-1}$." (2.3 Outflow)
   - parameter: R0 = z0 = 1"  
  > "$R_0$ and $z_0$ are normalization constants, and both are set to be $1^{\prime \prime}$ (Oya et al. 2014)." (2.3 Outflow)
   - assumption: Outflow axis perpendicular to envelope mid-plane  
  > "assuming that the outflow axis is perpendicular to the mid-plane of the infalling rotating envelope." (2.3 Outflow)
   - fitting: best fit by eye  
  > "The blue lines shown in Figure [3](#fig:PV_PA270) represent the best-fit result by eye" (2.3 Outflow)
   - validation: Compared with larger-scale 12CO velocities  
  > "In the above model, the maximum velocity shift for the two lobes is $8.2$ km s$^{-1}$ at the distance of $200^{\prime \prime}$ from the protostar." (2.3 Outflow)
3. **Estimate extinction from CS column density**: RADEX CS column density, then N(H2) with CS abundance 1e-9, then L' extinction  
  > "This value was derived using the RADEX code (van der Tak et al. 2007)" (4.1 Direction of the outflow)
   - software: RADEX
   - parameter: n(H2)=1e6-1e7 cm^-3, Tkin=30 K, X(CS)=1e-9  
  > "the H$_2$ density and the kinetic temperature were assumed to be $10^6$–$10^7$ cm$^{-3}$ and 30 K, respectively" (4.1 Direction of the outflow)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare outflow parameters across sources**: Convert C and v0 to AU units and plot against dynamical time with exponential fit, equal weights  
  > "The green dotted line in Figure [10](#fig:CDt) represents the best-fit result, where an equal weight is assumed for all the sources." (4.3 Comparison with other sources)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **RADEX** : CS column density  
  > "This value was derived using the RADEX code (van der Tak et al. 2007)" (4.1 Direction of the outflow)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Envelope inclination angle | +5 (reasonable +5 to +10; <+15) | 5 ± 10 (Table 2) | deg | 1 | we found that the inclination angle from $+5\ensuremath{^\circ}$ to $+10\ensuremath{^\circ}$ reasonably reproduces the observation. |
| PV rms difference along 270 deg, +5 deg model | 0.018 | not stated | Jy/beam | 1 | larger than that for the inclination angle of $+5\ensuremath{^\circ}$ (0.018 Jy beam$^{-1}$) |
| Outflow C | 0.05 | not stated | arcsec^-1 | 2 | $C = 0.05\ {\rm arcsec}^{-1}$ and $v_0 = 0.10\ {\rm km\ s}^{-1}$ |
| Outflow v0 | 0.10 | not stated | km/s | 2 | $C = 0.05\ {\rm arcsec}^{-1}$ and $v_0 = 0.10\ {\rm km\ s}^{-1}$ |
| c_AU = C/D | 3.6 | 2.2 | 1e-4 AU^-1 | 4 | / 3.6 $\pm$ 2.2 / 7.3 $\pm$ 1.5 / |
| CS column density at 0.7" west | (1-2)e13 | not stated | cm^-2 | 3 | We evaluated the CS column density to be (1–2) $\times 10^{13}$ cm$^{-2}$ |
| L' band extinction | (0.5-1) | not stated | mag | 3 | This H$_2$ column density corresponds to an $L^\prime$ band extinction of about (0.5–1) mag. |
| Correlation coefficient C/D vs t_dyn | -0.94 | not stated | dimensionless | 4 | The correlation coefficient for this plot is $-0.94$. |
| Correlation coefficient v0/DR0 vs t_dyn | -0.80 | not stated | dimensionless | 4 | Although the correlation coefficient of $-0.80$ |

## Qualitative findings

- The western outflow lobe points toward us, opposite to previous reports; the envelope's eastern side is in front.  
  > "the outflow axis in the western side of the protostar points to us" (2.2 Envelope)
- No clear rotation of the outflow cavity wall is detected.  
  > "A rotating motion is hardly seen in the outflow cavity wall." (4.2 Angular momentum)

## Claim tuples

- H: Is the envelope inclination positive (west lobe toward us)? | E: Compare CS and c-C3H2 PV diagrams along six lines with ballistic models at +5 and -5 deg | R: +5 deg reproduces all PV diagrams; -5 deg does not | F: Inclination is positive, opposite to earlier assumption | **supported**
- H: Does the outflow near the protostar follow a parabolic model? | E: By-eye fit of parabolic cavity model with offset origin | R: C=0.05 arcsec^-1, v0=0.10 km/s explain PV diagrams | F: Outflow parameters can be derived from a narrow central region | **partially**
- H: Does the outflow cavity opening (C/D) decrease with age? | E: Plot C/D vs dynamical timescale for six sources | R: Correlation coefficient -0.94 | F: C/D appears to decrease exponentially with t_dyn | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Extinction of L' light by dense gas, or non-perpendicular outflow axis/precession, as explanations for the conflict with infrared asymmetry  
  > "The contradiction can originate from the following two reasons." (4.1 Direction of the outflow)
- How they decided it was enough: _not stated_
- Limitation (authors): Simple model with many assumptions; rms statistics not meaningful; outflow emission faint and resolved out  
  > "the outflow components are faint and heavily resolved out" (2.1 Overall Distribution)
- Caveat (inferred, ours): Fits by eye without uncertainties or sampling
- Caveat (inferred, ours): Only six sources in the trend fit
- Caveat (inferred, ours): Outflow axis assumed perpendicular to envelope
- Caveat (inferred, ours): Heavily resolved-out outflow emission
- Caveat (inferred, ours): Offset of outflow origin taken from literature

## Reproducibility

- Data public (paper): Cycle 0 data cited by project code; public status not explicitly stated  
  > "This paper makes use of the following ALMA data set ADS/JAO.ALMA$\#$2011.0.00604.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Calibration and imaging recipe
- Missing: Model code
- Missing: PV extraction details
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Data are identified and the model is described, but the fits are by eye and the processing details are inherited from earlier papers.
- Rediscovery candidate: no, The main results are by-eye model comparisons and the recipe is incomplete.

## Links

- Method: Oya et al. 2014 (Envelope and outflow model)
- Method: Lee et al. 2000 (Parabolic outflow model)
- Companion: Sakai et al. (2014a) (Centrifugal barrier and chemistry in L1527)
- Companion: Sakai et al. (2014b) (Source of the ALMA data)

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
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 29,
  "rate": 0.403
 },
 "evidence_ok": true
}
```
