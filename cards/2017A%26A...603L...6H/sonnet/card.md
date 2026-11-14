# Direct evidence of multiple reservoirs of volatile nitrogen in a protosolar nebula analogue

`2017A&A...603L...6H` | Astronomy and Astrophysics 2017 | first author: Hily-Blant, P. | arXiv: 1706.10095 | DOI: 10.1051/0004-6361/201730524

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry, solar_system
- Question: What is the 14N/15N ratio in CN in the TW Hya disk, does it differ from HCN in other disks (multiple N reservoirs), and what does it imply for the present-day local ISM ratio and the origin of nitrogen in the solar system?  
  > "A first step in addressing this issue would be to demonstrate the existence of multiple reservoirs in protoplanetary disks, which serve as analogues for the PSN." (Introduction)
- Target **TW Hya**: coordinates _not stated_; z/distance d=59.5(9) pc  
  > "a nearby (d=59.5(9) pc[^1]), nearly pole-on T Tauri star and disk system" (Observations); distance from not stated (Gaia acknowledged)  
  > "a nearby (d=59.5(9) pc[^1]), nearly pole-on T Tauri star and disk system" (Observations)
- Target **MWC 480 (archival H13CN/HC15N)**: coordinates _not stated_; z/distance d=140 pc  
  > "in the nearby ($d$=140 pc) protoplanetary disk orbiting MWC 480" (Two isotopic reservoirs of nitrogen in disks); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00196.S
- bands: CN(3-2) at 340 GHz and C15N(3-2) at 330 GHz  
  > "C$^{14}$N(3-2) and C$^{15}$N(3-2) rotational emission at 340 and 330 GHz respectively" (Observations)
- frequencies and spectral setup: channel spacing 61 kHz (0.107 km/s at 340 GHz), CN and C15N observed simultaneously  
  > "channel spacing of 61 kHz (or 0.107 km/s effective velocity resolution at 340 GHz)" (Observations)
- continuum bandwidth: _not stated_
- arrays: 47 antennas  
  > "The Fourier plane was sampled by 47 antennas, covering baselines from 15 to 343 m." (Observations)
- configurations: _not stated_
- baselines: 15 to 343 m  
  > "covering baselines from 15 to 343 m" (Observations)
- angular resolution: CN clean beam 0.90"x0.53", PA 86 deg; C15N synthesized beamwidth 2.3"  
  > "The clean beam at 340 GHz was 0.90”$\times$0.53” and with a position angle of 86$^\circ$" (Observations); "The synthesized beamwidth is 2.3$''$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: CN 1.8-3.6 mJy/beam/channel; C15N 5.3-6.4 mJy/beam/channel  
  > "the final sensitivity is between 1.8 and 3.6 mJy/beam/channel" (Observations); "the sensitivity was between 5.3 to 6.4 mJy/beam/channel" (Observations)
- time on source: _not stated_
- observing dates: December 2014 and April 2015  
  > "Observations of TW Hya were performed in December 2014 and April 2015" (Observations)
- pi or archival as stated: _not stated_
- Line: CN N=3-2 hyperfine groups (~340.0 and ~340.25 GHz (e.g. 340019.63 MHz))
- Line: C15N N=3-2 hyperfine (329837.13 MHz (and others near 329.62-329.84 GHz))
- External data: Archival ALMA H13CN and HC15N data for MWC 480  
  > "archival H$^{13}$CN and HC$^{15}$N data for MWC 480 (cite: guzman2015)" (Two isotopic reservoirs of nitrogen in disks) [from (cite: guzman2015)]
- External data: Rest frequencies of C15N and CN hyperfine lines from CDMS  
  > "were taken from the CDMS spectroscopic catalogue (cite: muller2005)" (Observations) [from (cite: muller2005)]
- External data: 12C/13C = 68(15)  
  > "adopting 68(15) for the latter (cite: milam2005)" (Two isotopic reservoirs of nitrogen in disks) [from (cite: milam2005)]
- External data: TW Hya disk physical structure model for density limits  
  > "Based on a model of the physical structure of the TW Hya disk (cite: qi2013)" (Excitation of CN and C15N) [from (cite: qi2013)]
- External data: Collision rate coefficients for CN and C15N at hyperfine level  
  > "collision rates coefficients, for CN and C$^{15}$N, at the hyperfine level (cite: hilyblant2013b)" (Excitation of CN and C15N) [from (cite: hilyblant2013b)]
- External data: Compilation of 14N/15N ratios in diffuse clouds and prestellar cores (Table of ratios)  
  > "| NH$_3$ | Prestellar | Barnard 1 | 159.2, -20.1 | 235 | 334(17) | (cite: lis2010) |" (Table 2) [from lis2010, daniel2013, daniel2016, bizzocchi2013, lucas1998, ritchey2015]

## Processing

### Calibration

- pipeline or manual: CASA calibration followed by continuum-based self-calibration  
  > "After a first round of calibration using the CASA software (version 4.2.2), the phase calibration was improved using a self-calibration procedure based on the continuum" (Observations)
- casa version: CASA 4.2.2  
  > "CASA software (version 4.2.2)" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto; bandpass J1256-0547; phase J1037-2934  
  > "Flux calibration was performed using Callisto as an absolute reference, while bandpass and phase calibrations were obtained by observing the J1256-0547 and J1037-2934 QSOs respectively." (Observations)
- flux scale uncertainty: 3%  
  > "The quoted uncertainty does not include the calibration uncertainty (3%)." (Table 3 notes)
- self calibration: Phase self-cal from line-free continuum of parallel wide-bandwidth observations, applied to both CN and C15N  
  > "The self-calibrated output was then applied to both CN and C$^{15}$N." (Observations)

### Imaging

- task: GILDAS/MAPPING  
  > "deconvolution was performed using the Högbom algorithm as implemented in the GILDAS/MAPPING software" (Observations)
- deconvolver: Högbom  
  > "deconvolution was performed using the Högbom algorithm" (Observations)
- weighting robust: robust weighting for C15N (value not given)  
  > "To increase the S/N of the C$^{15}$N, robust weighting was applied" (Observations)
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
- final beam: 0.90"x0.53" PA 86 deg (CN)  
  > "The clean beam at 340 GHz was 0.90”$\times$0.53”" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Hyperfine HFS fitting procedure  
  > "using the `HFS` fitting procedure (cite: hilyblant2013a) of the GILDAS/CLASS software" (Excitation of CN and C15N) [from (cite: hilyblant2013a)]
- Same uv-plane analysis applied to MWC 480 archival data  
  > "We have applied the same $uv$ plane analysis described above to archival H$^{13}$CN and HC$^{15}$N data for MWC 480" (Two isotopic reservoirs of nitrogen in disks) [from (cite: guzman2015)]

### Not stated but needed to reproduce (our reading)

- Robust parameter and uv-taper values for imaging
- Which channels/line-free ranges used for continuum subtraction
- Exact self-calibration solution intervals
- Execution blocks and number of observations per date
- Partition function table values and exact Tex used for the prefactor ratio
- Procedure for propagating the 12C/13C uncertainty into R_HCN
- Integration of MWC 480 visibilities (velocity range, uv cutoff) not given

## Analysis recipe

1. **Calibrate and image**: CASA calibration with continuum self-calibration, then export to GILDAS; Högbom clean in MAPPING  
  > "The calibrated data were then exported to the GILDAS[^2] package format for imaging and analysis." (Observations)
   - software: CASA, GILDAS/MAPPING
   - fitting: _not stated_
   - validation: Simultaneous observation of both isotopologues mitigates cross-calibration uncertainty  
  > "Cross-calibration uncertainties were mitigated by the simultaneous observation of the two isotopologues" (Observations)
2. **Measure hyperfine opacity and excitation**: Fit hyperfine groups a and b of CN spectra at several disk positions with HFS  
  > "each group of hf lines was fitted simultaneously, using the `HFS` fitting procedure" (Excitation of CN and C15N)
   - software: GILDAS/CLASS
   - parameter: 44 mJy/K flux-to-temperature conversion  
  > "the fluxes were brought into the specific-intensity scale by applying a 44 mJy/K conversion factor" (Excitation of CN and C15N)
   - assumption: Equal excitation temperature for all hf lines within each group  
  > "The fitting algorithm assumes that the excitation temperature is equal for all hf lines within each group" (Excitation of CN and C15N)
   - fitting: _not stated_
   - validation: Comparison of the profiles of the four weakest hf lines scaled by intensity  
  > "The very good match of the spectral profiles indicates that they are all optically thin" (Excitation of CN and C15N)
3. **Fit integrated visibilities for fluxes**: Fit 2D Gaussian to CN visibilities integrated over 2 km/s with uv cutoff 60-120 m; fix geometry and fit only flux for C15N  
  > "The geometrical parameters of the CN disk are applied to the C$^{15}$N visibilities thus leaving the flux as the only one free parameter." (uv-plane analysis)
   - software: GILDAS/MAPPING UV_FIT
   - parameter: cutoff uv radius 60 m for the reported results  
  > "The results of the fitting procedure for a cutoff $uv$ radius of 60 m are shown" (uv-plane analysis)
   - assumption: CN and C15N co-spatial  
  > "the co-spatial distribution of CN and C$^{15}$N is likely the most difficult to firmly assess" (uv-plane analysis)
   - fitting: Gaussian disk, 6 free parameters for CN  
  > "The 6 free parameters of the CN fit are the center, major and minor axis, the position angle of the Gaussian disk, and the total flux." (uv-plane analysis)
   - validation: Free C15N fit agrees within 1 sigma; random geometry perturbations change ratio by ~0.1 sigma  
  > "The resulting fluxes and flux ratios vary by typically 0.1$\sigma$" (uv-plane analysis)
4. **Convert flux ratio to column-density ratio**: Optically thin relation with prefactor f(ul,Tex); RADEX excitation to check single Tex  
  > "The non-equilibrium statistical populations of the CN and C$^{15}$N hyperfine levels were calculated under the escape probability formalism using the RADEX code" (Excitation of CN and C15N)
   - software: RADEX
   - parameter: CN column density 1e12-1e15 cm-2; C15N lower by 300 or 441  
  > "a range of CN column densities from 10$^{12}$ to 10$^{15}$ cm$^{-2}$ was explored while that of C$^{15}$N was a factor 300 or 441 lower" (Excitation of CN and C15N)
   - assumption: Single excitation temperature for CN and C15N  
  > "The derived integrated flux ratio was translated into a column density ratio by assuming a single excitation temperature for both isotopologues." (The CN/C15N abundance ratio in TW Hya)
   - fitting: _not stated_
   - validation: Tex of lines equal to better than 3% at Tk<20-25 K  
  > "the excitation temperature of the 340.020 CN line and the 329.837 C$^{15}$N line are equal to better than 3%" (Excitation of CN and C15N)
5. **Compare MWC 480 HCN ratio and derive implications**: Apply same uv analysis to H13CN/HC15N; convert with 12C/13C=68(15) to R_HCN; compare with CN, prestellar cores, comets, GCE models  
  > "Assuming that the abundance ratio HCN/H$^{13}$CN is equal to the elemental $^{12}$C/$^{13}$C isotopic ratio" (Two isotopic reservoirs of nitrogen in disks)
   - software: GILDAS/MAPPING
   - assumption: HCN/H13CN equals elemental 12C/13C  
  > "Assuming that the abundance ratio HCN/H$^{13}$CN is equal to the elemental $^{12}$C/$^{13}$C isotopic ratio" (Two isotopic reservoirs of nitrogen in disks)
   - fitting: _not stated_
   - validation: Agrees with Guzmán 2017 reanalysis  
  > "our ratio for the MWC 480 disk also agrees well with recent re-analysis of the data (cite: guzman2017)" (Two isotopic reservoirs of nitrogen in disks)

## Software

- **CASA** 4.2.2: initial calibration  
  > "After a first round of calibration using the CASA software (version 4.2.2)" (Observations)
- **GILDAS/MAPPING** : imaging, Högbom deconvolution, UV_FIT  
  > "The fitting was performed using the `UV_FIT` task of the GILDAS/MAPPING software." (uv-plane analysis)
- **GILDAS/CLASS** : HFS hyperfine fits  
  > "using the `HFS` fitting procedure (cite: hilyblant2013a) of the GILDAS/CLASS software" (Excitation of CN and C15N)
- **RADEX** : excitation of CN and C15N hyperfine levels  
  > "using the RADEX code (cite: vandertak2007)" (Excitation of CN and C15N)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CN/C15N ratio in TW Hya | 323 | 30 | dimensionless | 4 | \ensuremath{{\cal R}_{\rm CN}} = 323(30) |
| H13CN/HC15N in MWC 480 | 1.88 | 0.34 | dimensionless | 5 | 1.88(34) |
| 14N/15N in HCN in MWC 480 | 128 | 36 | dimensionless | 5 | \ensuremath{{\cal R}_{\rm HCN}} = 128(36) |
| prefactor ratio f14/f15 | 26.5 | 0.8 | dimensionless | 4 | f_{14}/f_{15}=26.5(8). |
| CN integrated flux (hf line) | 2.02 | 0.02 | Jy km/s | 3 | / CN / -0.65(1) / -0.13(1) / 2.55(2) / 2.54(2) / 7.33(8) / 2.02(2) / |
| C15N integrated flux (fixed geometry) | 0.166 | 0.013 | Jy km/s | 3 | / 0.166(13) / |
| Continuum integrated flux at 340.0465 GHz | 1.426 | 0.002 | Jy | 1 | 378.0(3) mJy/beam and 1.426(2) Jy respectively |
| CN total opacity range | 3.4-5.4 (up to 6.1 where lines overlap) | not stated | dimensionless | 2 | The derived total opacity is $\approx 3.4-5.4$ for groups $a$ and $b$ lines |
| Implied outward migration of the Sun | ~2 | not stated | kpc | 5 | would correspond to an outward migration of the Sun by $\sim$2 kpc from its birth location |

## Qualitative findings

- CN ring in TW Hya has deconvolved inner and outer half-maximum radii of roughly 15 and 70 AU  
  > "deconvolved inner and outer half-maximum radii of roughly 15 and 70 AU respectively" (Observations)
- CN emission likely arises from cold, UV-shielded, dense regions rather than the upper warm layer  
  > "CN emission from cold and UV-shielded regions seems to be favoured." (Two isotopic reservoirs of nitrogen in disks)

## Claim tuples

- H: CN and HCN in disks trace different nitrogen reservoirs | E: Compare CN/C15N in TW Hya with HCN/HC15N in MWC 480 via uv-plane analysis | R: R_CN=323(30) vs R_HCN=128(36) | F: At least one disk contains a fractionated 15N-rich reservoir in addition to the elemental one | **supported**
- H: CN/C15N in TW Hya reflects the elemental 14N/15N of the present-day local ISM | E: Compare with prestellar core NH3 and N2H+ and diffuse cloud ratios | R: Prestellar weighted average 336(16) agrees with 323(30) | F: R_0 ~ 323(30), a primary non-fractionated reservoir | **partially**
- H: Solar-system nitrogen reservoirs (Sun/Jupiter vs comets) mirror disk reservoirs | E: Compare ratio of CN- and HCN-derived values with PSN ratio | R: 323:111 (~2.9) vs 441:144 (~3.1) | F: Primary N2 reservoir and secondary atomic N reservoir existed in the PSN | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: CN has optically thin hyperfine lines, enabling a direct isotope ratio without secondary isotopic ratios  
  > "This species hence potentially affords a direct means to infer N isotope ratios in disks, without the need to resort to assumptions" (Introduction)
- Alternative: Selective photodissociation models imply R_0~600, rejected as inconsistent with GCE and core fractionation models  
  > "The elemental ratio in TW Hya, and hence in the LISM, would be $\ensuremath{{\cal R}_0}\approx 600$" (The 14N/15N isotopic ratio in the present-day ISM)
- How they decided it was enough: _not stated_
- Limitation (authors): CN and C15N co-spatiality assumption hard to assess; C15N map not used  
  > "Indeed, the C$^{15}$N map was not used in this work." (uv-plane analysis)
- Limitation (authors): Robust CN column density needs self-consistent modelling; 2D radiative transfer needed  
  > "Yet, 2D radiative transfer calculations are required to demonstrate this claim." (Excitation of CN and C15N)
- Caveat (inferred, ours): HCN ratio from a different disk (MWC 480, different star type) is compared with CN in TW Hya
- Caveat (inferred, ours): Assumes HCN/H13CN equals elemental 12C/13C
- Caveat (inferred, ours): Co-spatial Gaussian assumption ignores the CN central hole and ring
- Caveat (inferred, ours): Interpretation depends on uncertain chemical and GCE models

## Reproducibility

- Data public (paper): Proposal code given; archival MWC 480 data used  
  > "(proposal 2013.1.00196.S)" (Observations)
- Products in archive: _not stated_
- Missing: Imaging weights and taper parameters
- Missing: MWC 480 project code and uv fitting details
- Missing: Full error propagation for R_HCN
- Data volume (inferred): ~50-150 GB raw for TW Hya, plus MWC 480 archival data
- Score (inferred): 3/5, Data and software identified and the method is described, but key imaging and fitting settings are missing and the work relies on GILDAS.
- Rediscovery candidate: no, Results are numeric but several recipe details are missing and heavy interpretation is involved.

## Links

- Method: (cite: hilyblant2013a) (HFS hyperfine fitting procedure)
- Method: (cite: vandertak2007) (RADEX code)
- Companion: (cite: guzman2017) (HCN/HC15N ratios in a sample of disks)
- Companion: (cite: guzman2015) (MWC 480 archival H13CN and HC15N data)

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
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
  "facts": 85,
  "stated": 57,
  "rate": 0.671
 },
 "evidence_ok": true
}
```
