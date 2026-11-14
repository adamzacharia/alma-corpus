# Formation and Atmosphere of Complex Organic Molecules of the HH 212 Protostellar Disk

`2017ApJ...843...27L` | The Astrophysical Journal 2017 | first author: Lee, Chin-Fei | arXiv: 1706.06041 | DOI: 10.3847/1538-4357/aa7757

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Where does a Keplerian disk form inside the infalling-rotating envelope of HH 212, and do the complex organic molecules trace the disk atmosphere (formed in the disk) or a rapidly infalling warm inner envelope?  
  > "Without detailed kinematic study of the envelope and disk, we can not determine the radius at which the Keplerian disk has formed." (1 Introduction); "Our spatially resolved observations of COMs favor their formation in the disk rather than a rapidly infalling (warm) inner envelope." (abstract)
- Target **HH 212 (IRAS 05413-0104)**: coordinates _not stated_; z/distance 400 pc  
  > "It is deeply embedded in a compact molecular cloud core in the L1630 cloud of Orion, which is at a distance of about 400 pc (cite: Kounkel2017)." (1 Introduction); distance from Kounkel et al. 2017  
  > "It is deeply embedded in a compact molecular cloud core in the L1630 cloud of Orion, which is at a distance of about 400 pc (cite: Kounkel2017)." (1 Introduction)

## Data provenance

- ALMA projects: 2012.1.00122.S, 2015.1.00024.S
- bands: Band 7 (~350 GHz), Cycles 1 and 3  
  > "Observations of the HH 212 protostellar system were carried out with ALMA in Band 7 at $\sim$ 350 GHz in Cycles 1 and 3, with 32-45 antennas" (2 Observations)
- frequencies and spectral setup: Cycle 1: 4 spws (CO, SiO, HCO+, continuum at 358 GHz); Cycle 3: 6 spws adding SO and H13CO+; 0.212 km/s per channel in line windows  
  > "For the Cycle 3 project, the correlator was more flexible and thus was set up to include 2 more spectral windows" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C32-6 (Cycle 1), C36-7/8 (Cycle 3)  
  > "| 3 | 2015-11-05 | C36-7/8 | 45 | 44 | 78$-$16196 |" (Table 1)
- baselines: 15-1466 m (Cycle 1); 17-16196 m (Cycle 3)  
  > "The projected baselines are 17-16196 m." (2 Observations)
- angular resolution: ~0.16'' (Cycle 1), ~0.02'' (Cycle 3); maps at 0.04'', 0.06'', 0.1''  
  > "The resulting resolutions are $\sim$ $0^{\prime\prime}_{^\textrm{.}}04$." (2 Observations)
- max recoverable scale: ~2.5'' (Cycle 1); ~0.4'' (Cycle 3)  
  > "The maximum recoverable size scale is $\sim$ $0^{\prime\prime}_{^\textrm{.}}4$." (2 Observations)
- sensitivity: HCO+: 3.1 mJy/beam (0.06'') and 3.9 mJy/beam (0.1''); COMs: 1.7 mJy/beam (0.848 km/s), 3.0 mJy/beam (0.212 km/s)  
  > "The noise levels are found to be $\sim$ 1.7 mJy beam$^{-1}$ (or $\sim$ 11 K) for 0.848 km s$^{-1}$ and 3.0 mJy beam$^{-1}$ (or $\sim$ 20 K) for 0.212 km s$^{-1}$." (2 Observations)
- time on source: ~148 minutes  
  > "The total time on the HH 212 system is $\sim$ 148 minutes." (2 Observations)
- observing dates: 2015-08-29, 2015-11-05, 2015-12-03  
  > "| 1 | 2015-08-29 | C32-6 | 37 | 30 | 15$-$1466 |" (Table 1)
- pi or archival as stated: _not stated_
- Line: HCO+ J=4-3 (356.734288 GHz)
- Line: CH3OH 3 lines (e.g. 4(1,3)-3(0,3)) (345.90392, 358.41465, 358.60580 GHz)
- Line: CH2DOH 18 lines at 13 frequencies (345.7-358.1 GHz)
- Line: CH3SH 14(1)-13(1) E (356.62709 GHz)
- Line: NH2CHO 17(2,16)-16(2,15) (356.71376 GHz)
- Line: D2CO 6(2,4)-5(2,3) (357.87145 GHz)
- External data: Dusty disk density profile, flared structure, temperature (~70 K at ~40 AU), optical depth used for disk mass and geometry  
  > "using the disk density profile derived from modeling the disk continuum emission in (cite: Lee2017)" (4.2 Formation of a Keplerian disk) [from (cite: Lee2017)]
- External data: Peak-abundance temperatures of methanol in warm-up models (~120 K, ~130 K)  
  > "which is estimated to be $\sim 120~K$ (cite: Garrod2013) or $\sim 130~K$ (cite: Muller2016)" (3.4 Physical condition in the disk atmosphere) [from (cite: Garrod2013; Muller2016)]
- External data: CH3SH rotation partition function  
  > "using the rotation partition function in (cite: Xu2012)" (3.4 Physical condition in the disk atmosphere) [from (cite: Xu2012)]

## Processing

### Calibration

- pipeline or manual: CASA calibration of passband, flux, gain (details not given)  
  > "The data were calibrated with the CASA package for the passband, flux, and gain (see Table [4](#tab:calib))." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-013 (Cycle 1); J0423-0120 (Cycle 3)  
  > "| 2015-08-29 | J0607-0834, 1.20 Jy | J0423-013, 1.03 Jy | J0552+0313, 0.25 Jy |" (Table 4)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0.5 for HCO+ and COM maps  
  > "We used a robust factor of 0.5 for the visibility weighting to generate the HCO$^+$ maps" (2 Observations)
- uv taper: HCO+: uv-distance >3000 m excluded; COMs: uv-distance <8000 m used  
  > "the data with the $uv$-distance greater than 3000 m (with a corresponding angular scale of $\sim$ $0^{\prime\prime}_{^\textrm{.}}06$) are excluded" (2 Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Cycle 1 and Cycle 3 data combined  
  > "Cycle 1 data and Cycle 3 data are combined to make the maps." (2 Observations)
- smoothing: HCO+ maps convolved to 0.1'' for low velocity  
  > "we convolved the maps to $0^{\prime\prime}_{^\textrm{.}}1$ resolution to map the emission at low velocity" (2 Observations)
- final beam: ~0.06'' and 0.1'' (HCO+), ~0.04'' (COMs)  
  > "The resulting resolutions are $\sim$ $0^{\prime\prime}_{^\textrm{.}}04$." (2 Observations)
- final rms: 3.1 and 3.9 mJy/beam (HCO+); 1.7 and 3.0 mJy/beam (COMs)  
  > "The noise levels can be measured from line-free channels and are found to be $\sim$ 3.1 mJy beam$^{-1}$" (2 Observations)

### Inherited from earlier work

- Systemic velocity 1.7±0.1 km/s LSR  
  > "The systemic velocity in HH 212 is assumed to be $V_\textrm{\scriptsize sys}= 1.7\pm0.1$ km s$^{-1}$ LSR, as in (cite: Lee2007)." (3 Results) [from (cite: Lee2007)]
- Toy model for infall/rotation PV structures  
  > "we adopt the toy model developed by (cite: Sakai2014), which has been used to reproduce the similar PV structures of the envelope and disk in L1527." (3.3 Modeling the Kinematics) [from (cite: Sakai2014)]
- Jet inclination ~4 deg and disk near edge-on  
  > "The jet has an inclination of $\sim$ 4$^\circ$ to the plane of the sky, with the northern component tilted toward us (cite: Claussen1998)." (3 Results) [from (cite: Claussen1998; Lee2017)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether archive or manual calibration scripts were used
- Self-calibration details and how Cycle 1 and 3 data were aligned/combined
- Line-free channels and continuum subtraction method
- Cell size, image size, deconvolver, masks, cleaning thresholds
- Beam sizes and position angles for each map
- Details of the line stacking and integration velocity ranges
- How the model PV boundaries were matched (no formal fit or cost function)
- Population diagram fitting method and partition function for CH2DOH
- Flux calibrator scale uncertainty

## Analysis recipe

1. **Calibrate and image Cycle 1 + Cycle 3 data**: CASA calibration; combined visibilities imaged with robust 0.5, uv-range cuts  
  > "Cycle 1 data and Cycle 3 data are combined to make the maps." (2 Observations)
   - software: CASA
   - parameter: robust = 0.5; uv<8000 m for COMs; uv<3000 m for HCO+  
  > "we used a robust factor of 0.5 and the data with the $uv$-distance shorter than 8000 m" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Characterize HCO+ envelope morphology and PV diagrams**: Channel maps at low/high velocity, parabolic boundaries by eye, PV cuts along major and minor axes  
  > "Using a rough eye fitting to the redshifted and blueshifted HCO$^+$ emission of the envelope at both low velocity" (3.1 Flattened Envelope in HCO+)
   - parameter: upper boundary a=0.05, b=0.45; lower a=-0.05, b=-0.6  
  > "we obtained $a=0.05$ and $b=0.45$ for the upper boundary and $a=-0.05$ and $b=-0.6$ for the lower boundary" (3.1 Flattened Envelope in HCO+)
   - assumption: Vsys = 1.7 km/s; maps rotated 23 deg clockwise  
  > "rotate our maps by 23$^\circ$ clockwise to align the jet axis in the north-south direction" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Map COM emission and PV structure in the disk atmosphere**: Stack lines of the same molecule for integrated-intensity maps; PV cuts parallel and perpendicular to the disk plane  
  > "Since the emission morphology is similar, the maps of the same molecule are stacked together to make a map with a higher S/N ratio." (3.2 Tracing Disk Atmosphere with COMs)
   - fitting: Single linear fit to the linear PV structures in methanol and deuterated methanol  
  > "which are obtained from a single linear fit to the linear PV structures seen in both methanol and deuterated methanol" (3.2 Tracing Disk Atmosphere with COMs)
   - validation: _not stated_
4. **Model envelope and disk kinematics**: Toy model with conserved specific angular momentum and energy; model PV outer boundaries matched to observed PV; Keplerian inside centrifugal barrier  
  > "the observed kinematics of the envelope and disk atmosphere can be fitted simultaneously with only two parameters, $l$ and $M$." (3.3 Modeling the Kinematics)
   - parameter: l and M free; r_c = l^2/GM; r_0 = l^2/2GM  
  > "$$\begin{equation} r_0=\frac{l^2}{2GM} \label{eq:CB} \end{equation}$$" (3.3 Modeling the Kinematics)
   - assumption: Flared envelope with parabolic boundaries; fit weighted to blueshifted side because of redshifted self-absorption  
  > "For the envelope, the fit is based more on the blueshifted side, because the redshifted side suffers from self-absorption." (3.3 Modeling the Kinematics)
   - fitting: Visual matching of model PV boundaries to observed PV structures; no sampler or likelihood  
  > "These model PV structures can then be used to fit the outer boundaries of the observed PV structures." (3.3 Modeling the Kinematics)
   - validation: Model broadly reproduces important PV features of envelope and disk  
  > "In summary, this simple toy model can broadly reproduce all the important features in the PV diagrams of the envelope and disk." (3.3 Modeling the Kinematics)
5. **Derive excitation temperature and column densities**: Population diagram of CH2DOH in optically thin limit; methanol scaled to the CH2DOH fit; CH3SH, NH2CHO, D2CO column densities assuming same Tex  
  > "we can construct a population diagram to estimate the mean excitation temperature and the column density of the molecule in the region traced by the COMs." (3.4 Physical condition in the disk atmosphere)
   - parameter: Integrated intensities measured in lower disk atmosphere with 2 sigma cutoff  
  > "The integrated line intensity of each transition can be measured toward the lower disk atmosphere where the emission is better detected, using the total intensity map (integrated over velocity, as shown in Figure [\[fig:methanol\]](#fig:methanol)) with a 2$\sigma$ cutoff." (Physical condition in the disk atmosphere)
   - assumption: Optically thin; same Tex (165 K) for methanol and CH3SH  
  > "we assume the same temperature for the methanol, and then estimate the column density." (3.4 Physical condition in the disk atmosphere)
   - fitting: Fit to CH2DOH population diagram (method not specified)  
  > "Fitting the data points of deuterated methanol, we estimate a mean excitation temperature of 165$\pm$85 K" (3.4 Physical condition in the disk atmosphere)
   - validation: Compared with methanol Tex ~295 K from Leurini et al. 2016  
  > "The excitation temperature of the methanol was estimated to be $\sim$ 295 K." (3.4 Physical condition in the disk atmosphere)

## Software

- **CASA** : Calibration of passband, flux and gain; imaging  
  > "The data were calibrated with the CASA package for the passband, flux, and gain" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Specific angular momentum l | 140 | ±30 | AU km/s | 4 | $l=140\pm30$ AU km s$^{-1}$ and $M=0.25\pm0.05$ $M_\odot$ |
| Central mass (protostar+disk) | 0.25 | ±0.05 | Msun | 4 | $l=140\pm30$ AU km s$^{-1}$ and $M=0.25\pm0.05$ $M_\odot$ |
| Centrifugal barrier radius | 44 | ±9 | AU | 4 | the centrifugal barrier (CB) is at $\sim$ 44$\pm$9 AU |
| Centrifugal radius | 88 | ±18 | AU | 4 | the centrifugal radius (CR) is $\sim$ 88$\pm18$ AU |
| CH2DOH excitation temperature | 165 | ±85 | K | 5 | a mean excitation temperature of 165$\pm$85 K and a mean column density of 9.2$\pm2.0\times10^{16}$ cm$^{-2}$ |
| CH2DOH column density | 9.2e16 | ±2.0e16 | cm^-2 | 5 | a mean excitation temperature of 165$\pm$85 K and a mean column density of 9.2$\pm2.0\times10^{16}$ cm$^{-2}$ |
| CH3OH column density | >=3.4e17 | ±1.0e17 | cm^-2 | 5 | This implies a column density of $\gtrsim$ 3.4$\pm1.0\times10^{17}$ cm$^{-2}$ for methanol |
| [CH2DOH]/[CH3OH] | <=0.27 | not stated | dimensionless | 5 | thus an abundance ratio of \[CH$_2$DOH\]/\[CH$_3$OH\]$\lesssim 0.27$ |
| CH3SH column density | 1.0e17 | not stated | cm^-2 | 5 | the column density is found to be $\sim 1.0\times10^{17}$ cm$^{-2}$ |
| NH2CHO column density | 1.6e15 | not stated | cm^-2 | 5 | the column density is $\sim$ $1.6\times10^{15}$ cm$^{-2}$ for NH$_2$CHO and $\sim$ $3.2\times10^{15}$ cm$^{-2}$ for D$_2$CO |
| D2CO column density | 3.2e15 | not stated | cm^-2 | 5 | the column density is $\sim$ $1.6\times10^{15}$ cm$^{-2}$ for NH$_2$CHO and $\sim$ $3.2\times10^{15}$ cm$^{-2}$ for D$_2$CO |
| Disk mass within ~36 AU | ~0.03 (upper limit) | not stated | Msun | 0 | The disk mass integrating from $r \sim$ 36 AU toward the center is $\sim$ 0.03 $M_\odot$ |

## Qualitative findings

- HCO+ traces an infalling-rotating envelope down to the centrifugal barrier; COMs trace the atmosphere of a Keplerian disk inside it  
  > "This indicates that HCO$^+$ traces the infalling-rotating envelope down to centrifugal barrier and COMs trace the atmosphere of a Keplerian rotating disk within the centrifugal barrier." (abstract)
- Infall velocity in the COM atmosphere has dropped to zero  
  > "It it clear from the PV diagrams that the infall velocity there has dropped to zero." (3.2 Tracing Disk Atmosphere with COMs)

## Claim tuples

- H: Is the ~60 AU dusty disk radius the radius of the centrifugal barrier/Keplerian disk? | E: Fit toy infall-rotation model to HCO+ and COM PV diagrams | R: l=140±30 AU km/s, M=0.25±0.05 Msun, CB ~44±9 AU | F: A Keplerian disk forms inside the centrifugal barrier at ~44 AU | **supported**
- H: Do COMs trace the disk atmosphere rather than a disk wind or infalling envelope? | E: Spatially resolved maps and PV diagrams of CH3OH, CH2DOH, CH3SH, NH2CHO, D2CO | R: Emission 20 AU above and below the midplane, Keplerian rotation, negligible radial velocity | F: COMs trace the atmosphere of a flared Keplerian disk | **supported**
- H: Are COMs formed in the disk or in the warm inner envelope? | E: Compare COM spatial distribution, Tex and deuteration with models | R: Tex 165±85 K, [CH2DOH]/[CH3OH] <~0.27 | F: COMs likely form on grains in the disk and desorb via warming/shock | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: A simple toy model reproduced similar PV structures in L1527 and allows simultaneous fit with two parameters  
  > "which has been used to reproduce the similar PV structures of the envelope and disk in L1527." (3.3 Modeling the Kinematics)
- Alternative: COMs tracing the base of a disk wind was considered but disfavored  
  > "although it is also plausible that they trace the base of a disk wind." (3.2 Tracing Disk Atmosphere with COMs)
- How they decided it was enough: _not stated_
- Limitation (authors): Tex is poorly constrained because data points are scattered at low S/N; may be underestimated by factor ~2  
  > "Since the data points are scattered due to the low S/N ratio, the fitting results have a big uncertainty in excitation temperature." (3.4 Physical condition in the disk atmosphere)
- Limitation (authors): Disk is optically thick in dust so molecules near the midplane cannot be probed  
  > "Whether such molecules exist closer to the disk midplane cannot be determined for the nearly edge-on disk of HH 212 that is optically thick in dust continuum." (Conclusions)
- Caveat (inferred, ours): Model fit is by eye with no formal chi-square or posterior, so uncertainties are loosely defined
- Caveat (inferred, ours): Population-diagram result depends on LTE and optically thin assumptions and a shared Tex across species
- Caveat (inferred, ours): Column densities rely on stacking and a 2 sigma cutoff; blending of CH2DOH lines not discussed
- Caveat (inferred, ours): Conclusions list the mass as 0.25±0.5, inconsistent with ±0.05 in the text

## Reproducibility

- Data public (paper): ALMA data identified by project codes in the acknowledgments  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00122.S and 2015.1.00024.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and calibration scripts
- Missing: Imaging parameters (cell, size, masks, thresholds)
- Missing: Line stacking and integration windows
- Missing: Model fitting procedure and PV extraction details
- Data volume (inferred): Several hundred GB for the long-baseline Cycle 3 plus Cycle 1 raw data; ~tens of GB calibrated
- Score (inferred): 3/5, Public data and simple analytic model with stated parameters, but calibration/imaging details and fitting procedure are largely unstated.
- Rediscovery candidate: no, Fit is by-eye and imaging details are missing, so the recipe is not complete enough to redo precisely.

## Links

- Method: Sakai et al. 2014 (cite: Sakai2014) (Source of the toy infall-rotation model)
- Companion: Lee et al. 2017 (cite: Lee2017) (Dusty disk continuum at 8 AU resolution from the same Cycle 3 data)
- Companion: Lee et al. 2014 (cite: Lee2014) (Previous Cycle 0 HCO+ envelope study of HH 212)

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 51,
  "rate": 0.662
 },
 "evidence_ok": true
}
```
