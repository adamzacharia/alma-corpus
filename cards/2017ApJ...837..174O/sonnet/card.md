# L483: Warm Carbon-chain Chemistry Source Harboring Hot Corino Activity

`2017ApJ...837..174O` | The Astrophysical Journal 2017 | first author: Oya, Yoko | arXiv: 1703.03653 | DOI: 10.3847/1538-4357/aa6300

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What are the chemical composition and physical (kinematic) structure around the Class 0 protostar L483 at 100 au scale, and is this WCCC candidate also showing hot corino chemistry?  
  > "In the present study, we investigate the physical and chemical structures around the protostar at a 100 au scale with ALMA." (Introduction)
- Target **L483 (IRAS 18148-0440)**: coordinates 18h17m29.910s, -04d39m39.60s (J2000, field center)  
  > "The L483 dark cloud is located in the Aquila Rift ($d$ = 200 pc; Jørgensen et al. 2002; Rice et al. 2006)" (Introduction); "The field center of the observations was ($\alpha_{2000}$, $\delta_{2000}$) = ($18^{\rm h} 17^{\rm m} 29.910s$, $-04\ensuremath{^\circ} 39\ensuremath{'} 39.60\ensuremath{''}$)." (Observation); z/distance 200 pc  
  > "The L483 dark cloud is located in the Aquila Rift ($d$ = 200 pc; Jørgensen et al. 2002; Rice et al. 2006)" (Introduction); "The field center of the observations was ($\alpha_{2000}$, $\delta_{2000}$) = ($18^{\rm h} 17^{\rm m} 29.910s$, $-04\ensuremath{^\circ} 39\ensuremath{'} 39.60\ensuremath{''}$)." (Observation); distance from Jørgensen et al. 2002; Rice et al. 2006  
  > "The L483 dark cloud is located in the Aquila Rift ($d$ = 200 pc; Jørgensen et al. 2002; Rice et al. 2006)" (Introduction); "The field center of the observations was ($\alpha_{2000}$, $\delta_{2000}$) = ($18^{\rm h} 17^{\rm m} 29.910s$, $-04\ensuremath{^\circ} 39\ensuremath{'} 39.60\ensuremath{''}$)." (Observation)

## Data provenance

- ALMA projects: 2013.1.01102.S
- bands: Band 6, 244-264 GHz  
  > "were observed with the Band 6 receiver in the frequency range from 244 to 264 GHz" (Observation)
- frequencies and spectral setup: 61.030 kHz resolution (0.073 km/s at 250 GHz), 58.5892 MHz per chunk  
  > "A backend correlator was tuned to a resolution of 61.030 kHz and a bandwidth of each chunk of 58.5892 MHz." (Observation)
- continuum bandwidth: _not stated_
- arrays: 34 antennas  
  > "Thirty-four antennas were used in the observation" (Observation)
- configurations: _not stated_
- baselines: 18.5 to 644 m  
  > "the baseline length ranged from 18.5 to 644 m" (Observation)
- angular resolution: ~0.5'' (continuum 0.46''x0.42'')  
  > "the synthesized beam size is $0.46\ensuremath{''} \times 0.42\ensuremath{''}$ (P.A. 11.$^\circ$76)" (Distribution)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.13 mJy/beam; line rms 3.5-8.2 mJy/beam per 61.03 kHz channel  
  > "An rms noise level for the continuum is 0.13 mJy beam$^{-1}$" (Observation)
- time on source: 25.85 minutes  
  > "The total on-source time was 25.85 minutes" (Observation)
- observing dates: 12 June 2014 (Cycle 2)  
  > "The ALMA observation of L483 was carried out in the Cycle 2 operation on 12 June 2014." (Observation)
- pi or archival as stated: Part of project 2013.1.01102.S, P.I. N. Sakai  
  > "(#2013.1.01102.S; P.I. N. Sakai)" (Distribution)
- Line: CS J=5-4 (244.9355565 GHz)
- Line: NH2CHO 12(0,12)-11(0,11) (247.390719 GHz)
- Line: HCOOCH3 20(5,16,0)-19(5,15,0) (249.0474280 GHz)
- Line: SiO J=6-5 (260.5180090 GHz)
- Line: SO J_N=6_7-5_6 (261.8437210 GHz)
- Line: CCH N=3-2, J=7/2-5/2, F=4-3 and 3-2 (262.0042600 / 262.0064820 GHz)
- Line: HNCO 12(0,12)-11(0,11) (263.7486250 GHz)
- External data: Systemic velocity 5.5 km/s from single-dish observations  
  > "We here adopt the systemic velocity of 5.5 km s$^{-1}$ for this source based on previous single-dish observations (Hirota et al. 2009)." (Introduction) [from Hirota et al. 2009]
- External data: Outflow position angle 105 deg  
  > "we employ the position angle of the outflow axis of 105$^\circ$ reported by Chapman et al. (2013)" (4.1 Geometrical Configuration) [from Chapman et al. 2013]
- External data: Dust opacity kappa=0.008 cm2/g at 1.2 mm with beta=1.8  
  > "$\kappa_\nu$ is evaluated to be 0.008 cm$^2$ g$^{-1}$ at 1.2 mm with $\beta$ = 1.8 (Shirley et al. 2011)" (Chemical Composition) [from Shirley et al. 2011; Beckwith et al. 1990]
- External data: Bolometric luminosity 13 Lsun  
  > "Its bolometric luminosity is 13 $L_\odot$ (Shirley et al. 2000)." (Introduction) [from Shirley et al. 2000]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan; J1733-1304 for bandpass and phase  
  > "An absolute flux density scale was derived from Titan." (Observation)
- flux scale uncertainty: less than 9%  
  > "uncertainties are less than 9%" (Observation)
- self calibration: applied (details not given)  
  > "We applied self-calibration for better imaging." (Observation)

### Imaging

- task: CLEAN algorithm  
  > "Images were obtained by using the CLEAN algorithm" (Observation)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "the Brigg’s weighting with the robustness parameter of 0.5 was employed" (Observation)
- uv taper: outertaper of 1'' for CCH  
  > "the outertaper of 1$''$ is applied to improve a signal-to-noise ratio of the image" (Distribution)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum from line-free channels, subtracted in visibilities  
  > "the line maps were obtained after subtracting the continuum component directly from the visibilities" (Observation)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Infalling-rotating envelope ballistic model  
  > "The infalling-rotating envelope model employed in this study is essentially the same as that reported by Oya et al. (2014)." (5 Analysis) [from Oya et al. (2014)]
- Inclination of 80 deg from outflow analysis  
  > "we roughly assume an inclination angle respect to the plane of the sky ($i$) of 80$^\circ$ (0$^\circ$ for a face-on configuration) (Y. Oya et al. in preparation)" (5 Analysis) [from Y. Oya et al. in preparation]
- H2 column density relation  
  > "by using the following relation (Ward-Thompson et al. 2000)" (Chemical Composition) [from Ward-Thompson et al. 2000]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline/manual calibration details
- Self-calibration solint and reference
- Line-free channels
- Image size, cell size, masks, CLEAN threshold
- Spectroscopy catalog and partition function details
- LTE column density method and linewidth and source size assumptions
- Model code and any PV model grid details beyond parameter values

## Analysis recipe

1. **Image continuum and line maps**: CLEAN imaging with Briggs weighting, self-calibration, continuum subtraction in uv  
  > "A continuum image was prepared by averaging line-free channels" (Observation)
   - parameter: robust 0.5; CCH 1'' outertaper  
  > "the robustness parameter of 0.5 was employed" (Observation)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure sizes and positions**: two-dimensional Gaussian fit and deconvolution by beam  
  > "Its peak position is determined by the two dimensional Gaussian fit" (Distribution)
   - fitting: _not stated_
   - validation: _not stated_
3. **Kinematics from PV diagrams and infalling-rotating envelope plus Keplerian models**: Compare CS and SO PV diagrams with ballistic infall-rotation model and Keplerian disk by eye over parameter grid  
  > "we calculate the models with various parameters to find the reasonable set of the parameters by eye" (5 Analysis)
   - parameter: envelope thickness 30 au, density r^-1.5; M, r_CB, i free  
  > "we assume the flattened envelope with a constant thickness (30 au), which has the radial density distribution of $r^{-1.5}$" (5 Analysis)
   - assumption: inclination 80 deg, PA 15 deg for disk/envelope  
  > "assume that the disk/envelope system is extended along the position angle of 15$^\circ$" (4.1 Geometrical Configuration)
   - fitting: No formal fit; by-eye  
  > "we calculate the models with various parameters to find the reasonable set of the parameters by eye" (5 Analysis)
   - validation: Parameter variations of r_CB and M shown (Figs 12, 13)  
  > "for the case of no rotation ($r_{\rm CB}$ = 0 au), the positions of the most blue-shifted component and the most red-shifted component coincide in the model" (5 Analysis)
4. **Column densities and fractional abundances**: LTE column densities at 70, 100, 130 K; H2 column from dust continuum  
  > "evaluated by assuming local thermodynamic equilibrium at 70, 100, and 130 K" (Chemical Composition)
   - parameter: kappa = 0.008 cm2/g at 1.2 mm, beta = 1.8; mean particle mass 3.83e-24 g  
  > "$\kappa_\nu$ is evaluated to be 0.008 cm$^2$ g$^{-1}$ at 1.2 mm with $\beta$ = 1.8" (Chemical Composition)
   - assumption: Dust temperature 100 K (70-130 K), gas temp equals dust temp  
  > "assuming that the gas temperature is the same as the dust temperature" (Chemical Composition)
   - fitting: _not stated_
   - validation: Compared with hot corinos IRAS 16293-2422 and B335  
  > "These fractional abundances of NH$_2$CHO and HCOOCH$_3$ are comparable with those reported for the hot corinos" (Chemical Composition)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.2 mm continuum total flux | 28 | not stated | mJy | 2 | The total flux of the continuum is 28 mJy. |
| Continuum deconvolved size | 0.23'' x 0.16'' (PA 158 deg) | not stated | arcsec | 2 | The deconvolved size of the continuum emission is $0.23\ensuremath{''} \times 0.16\ensuremath{''}$ (P.A. 158$^\circ$) |
| Protostellar mass (representative) | 0.15 (range 0.1-0.2) | loosely constrained | Msun | 3 | the protostellar mass ($M$) of 0.15 $M_\odot$, the radius of the centrifugal barrier ($r_{\rm CB}$) of 100 au |
| Centrifugal barrier radius (representative) | 100 (range 30-200) | loosely constrained | au | 3 | for the range of $r_{\rm CB}$ from 30 au to 200 au |
| NH2CHO column density at 100 K | 1.5e14 | 0.7e14 | cm^-2 | 4 | $(1.5 \pm 0.7) \times 10^{14}$ cm$^{-2}$ and $(7 \pm 4) \times 10^{15}$ cm$^{-2}$ |
| HCOOCH3 column density at 100 K | 7e15 | 4e15 | cm^-2 | 4 | $(1.5 \pm 0.7) \times 10^{14}$ cm$^{-2}$ and $(7 \pm 4) \times 10^{15}$ cm$^{-2}$ |
| Beam-averaged N(H2) at 100 K | 6.5e23 | not stated | cm^-2 | 4 | derived from the dust continuum to be $6.5 \times 10^{23}$ cm$^{-2}$ |
| Fractional abundance NH2CHO relative to H2 | (1.3-3.9)e-10 | not stated | dimensionless | 4 | $(1.3-3.9) \times 10^{-10}$ and $(7.3-16.2) \times 10^{-9}$ for NH$_2$CHO and HCOOCH$_3$ |
| Fractional abundance HCOOCH3 relative to H2 | (7.3-16.2)e-9 | not stated | dimensionless | 4 | $(1.3-3.9) \times 10^{-10}$ and $(7.3-16.2) \times 10^{-9}$ for NH$_2$CHO and HCOOCH$_3$ |
| Emitting radius of 6 km/s component in Keplerian disk | 4 | not stated | au | 3 | A radius of the emitting region of the maximum velocity component ($\sim$6 km s$^{-1}$) in the disk is estimated to be as small as 4 au. |

## Qualitative findings

- CCH shows a ~0.5'' radius central hole and traces envelope/outflow cavity wall  
  > "The CCH distribution has a hole with a radius of $\sim$0.5$''$ around the continuum peak." (Distribution)
- SiO extends northeast, likely outflow shock near centrifugal barrier  
  > "It may trace the local outflow-shock near the centrifugal barrier." (Summary)

## Claim tuples

- H: Does the WCCC candidate L483 also harbor hot corino chemistry? | E: ALMA Band 6 line survey at ~0.5'' | R: NH2CHO and HCOOCH3 detected concentrated at the protostar, with abundances comparable to hot corinos | F: L483 is a mixed-character source: WCCC at large scale with hot corino activity near the protostar | **supported**
- H: Do envelope and disk kinematics explain the chemical differentiation? | E: Compare CS and SO PV diagrams with infalling-rotating envelope and Keplerian disk models | R: M 0.1-0.2 Msun, r_CB 30-200 au; central high-velocity component fit by Keplerian disk | F: Chemical change occurs around the centrifugal barrier; CS and SO also trace the disk, possibly due to higher luminosity | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Same ballistic model used for L1527, TMC-1A, IRAS 16293-2422 A  
  > "Hence, we apply the same model to the CS data." (5 Analysis)
- Alternative: Single infalling-rotating envelope model cannot reproduce the overall CS velocity structure, so a two-component model was needed  
  > "However, we cannot reproduce the overall velocity structure with the infalling-rotating envelope model." (5 Analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Model parameters only loosely constrained; fit by eye  
  > "Unfortunately, the key parameters can loosely be constrained from these observations" (5 Analysis)
- Limitation (authors): Most species detected in only one line  
  > "although only one line was detected for each of these species except for CCH" (Distribution)
- Caveat (inferred, ours): COM column densities from single lines with assumed LTE temperature and no excitation constraint
- Caveat (inferred, ours): Beam-averaged unresolved emission, optical depth and dust opacity assumptions
- Caveat (inferred, ours): By-eye model fitting without uncertainties
- Caveat (inferred, ours): Possible line blending for COM identification

## Reproducibility

- Data public (paper): Project 2013.1.01102.S, data set acknowledged  
  > "This paper makes use of the ALMA data set ADS/JAO.ALMA#2013.1.01102.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and calibration scripts
- Missing: Imaging parameters (size, cell, masks, self-cal solints)
- Missing: LTE fitting details and linewidths
- Missing: Model code
- Data volume (inferred): ~50-100 GB raw, one execution block
- Score (inferred): 3/5, Public data and clear robust/beam/rms numbers, but processing and modeling details are sparse and model fits are by eye.
- Rediscovery candidate: no, Key results rely on by-eye modeling and unspecified LTE settings.

## Links

- Method: Oya et al. 2014 (Infalling-rotating envelope model)
- Companion: Imai et al. 2016 (B335 observed with same setup)
- Companion: A. López-Sepulcre et al. in preparation (NGC 1333 IRAS 4A same setup)
- Related: ALMA 2013.1.01102.S (P.I. N. Sakai)

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 46,
  "rate": 0.639
 },
 "evidence_ok": true
}
```
