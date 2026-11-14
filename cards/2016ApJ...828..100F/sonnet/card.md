# Outflow Detection in a 70 μm Dark High-Mass Core

`2016ApJ...828..100F` | The Astrophysical Journal 2016 | first author: Feng, Siyi | arXiv: 1605.01736 | DOI: 10.3847/0004-637X/828/2/100

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, milky_way_ism
- Question: Does the 70 um dark high-mass core G28.34 S-A host a protostellar SiO outflow, and what does it imply for its evolutionary stage and accretion history?  
  > "Therefore, the line profile of SiO on the core-scale (0.1 pc) is crucial to judge whether protostellar object(s) are already in the $\rm 70\,\mu m$ dark G 28.34 S." (1 Introduction)
- Target **G28.34 S-A**: coordinates 18h42m46.597s, -04d04m11.940s (J2000), phase center  
  > "For all observations a common phase center was used, at $\rm 18^h42^m46^s.597$, $\rm -04^{\circ}04^{'}11^{''}.940$ (J2000)." (2.1 NOEMA); "was discovered around the southern edge of the filamentary IRDC G28.34+0.06 ($\sim$4.7 kpc," (1 Introduction); z/distance ~4.7 kpc  
  > "For all observations a common phase center was used, at $\rm 18^h42^m46^s.597$, $\rm -04^{\circ}04^{'}11^{''}.940$ (J2000)." (2.1 NOEMA); "was discovered around the southern edge of the filamentary IRDC G28.34+0.06 ($\sim$4.7 kpc," (1 Introduction); distance from Carey et al. 1998, 2000 (IRDC G28.34+0.06)  
  > "For all observations a common phase center was used, at $\rm 18^h42^m46^s.597$, $\rm -04^{\circ}04^{'}11^{''}.940$ (J2000)." (2.1 NOEMA); "was discovered around the southern edge of the filamentary IRDC G28.34+0.06 ($\sim$4.7 kpc," (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00236.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA compact configuration, Cycle 0 (archival)  
  > "was carried out with the compact configuration in ALMA Cycle-0." (2.4 ALMA archival data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 2.35'' x 1.98'' (PA=-66 deg)  
  > "The derived angular resolution is $\rm 2.35\ensuremath{''}\times1.98\ensuremath{''}$ ($\rm PA=-66^{\circ}$), and the maximum detectable scale is $\sim 9''$." (2.4 ALMA archival data)
- max recoverable scale: ~9''  
  > "the maximum detectable scale is $\sim 9''$" (2.4 ALMA archival data)
- sensitivity: ~7.4 mJy per 0.08 km/s channel after continuum subtraction  
  > "The rms noise level is $\sim 7.4$ mJy per 0.08 km$\rm s^{-1}$ channel after continuum subtraction." (2.4 ALMA archival data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival data; observation details in Tan et al. 2013  
  > "The details of the observations can be found in (cite: tan13)." (2.4 ALMA archival data)
- Line: SiO J=5-4 (not stated)
- Line: SiO J=2-1 (NOEMA+30m) (not stated)
- Other facility **NOEMA**: 3.4 mm continuum and SiO J=2-1 interferometric data  
  > "in its B (with 6-7 working antennae on different days), C (5 antennae), and D (5-6 antennae) configurations during March 21 to May 23, 2015." (2.1 NOEMA)
- Other facility **IRAM 30 m**: single-dish SiO J=2-1 to recover missing flux  
  > "To compensate the missing flux, we use data from an imaging line survey on G28.34 S with the IRAM 30 m telescope at 3 mm" (2.2 IRAM 30 m telescope)
- Other facility **SMA**: 1.1 mm continuum  
  > "We made continuum images using data from the combined COMP+EXT data" (2.3 SMA)
- External data: NH3 gas kinetic temperature (VLA+Effelsberg) used to fit T_kin ~15 K  
  > "Using the combined VLA+Effelsberg $\rm NH_3$ lines (resolution of 5$''$, (cite: wangy08))" (4.1 Core mass) [from (cite: wangy08)]
- External data: Bolometric luminosity ~10 Lsun (private communication)  
  > "The entire G 28.34 S region has a low bolometric luminosity $\rm L_{bol}\sim 10\,L_{\odot}$ (priv. communication with S. Ragan)." (4.2 Physical properties of the W-E oriented outflow) [from S. Ragan, priv. comm.; (cite: ragan13)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated ALMA data downloaded from archive  
  > "We download the calibrated data from the ALMA archive and cleaned it with natural weighting in CASA (cite: mcuullin07)." (2.4 ALMA archival data)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "cleaned it with natural weighting in CASA" (2.4 ALMA archival data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: performed (method not given)  
  > "after continuum subtraction" (2.4 ALMA archival data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: ALMA J=5-4 convolved to NOEMA J=2-1 resolution for PV  
  > "we convolve the $J$=5$\rightarrow$4 data obtained with ALMA to the same angular resolution as the $J$=2$\rightarrow$1 data obtained with NOEMA" (3.2 Position-velocity (PV) diagram)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA observation details  
  > "The details of the observations can be found in (cite: tan13)." (2.4 ALMA archival data) [from (cite: tan13)]
- SMA and 30 m observation details and calibration  
  > "More details of the observations and data calibration are given in (cite: feng16)." (2.3 SMA) [from (cite: feng16)]
- NH3 temperature fitting procedure  
  > "the procedure outlined in (cite: wangk14), we fit a gas kinetic temperature of $T_{\rm kin} \approx 15$ K for S-A." (4.1 Core mass) [from (cite: wangk14)]

### Not stated but needed to reproduce (our reading)

- CASA version and tclean parameters (cell, image size, mask, threshold) for ALMA SiO 5-4
- Line-free channels and continuum subtraction method for ALMA data
- Velocity integration ranges for lobe maps and Gaussian fits
- SiO 5-4 spectral window and rest frequency
- PV slice position angle and center
- Details of the 30m+NOEMA combination in GILDAS
- Calibration details for the archival ALMA data (archive version)

## Analysis recipe

1. **Image archival ALMA SiO 5-4**: Downloaded calibrated data, cleaned with natural weighting in CASA  
  > "We download the calibrated data from the ALMA archive and cleaned it with natural weighting in CASA (cite: mcuullin07)." (2.4 ALMA archival data)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Position-velocity diagrams of SiO lines**: 5'' wide slice along W-E, ALMA convolved to NOEMA resolution, extracted with pvextractor  
  > "we take a 5$''$-width slice along the W-E orientation and extract a PV diagram from both lines (Figure [2](#pv) left panel), using the “pvextractor" code" (3.2 Position-velocity (PV) diagram)
   - software: pvextractor
   - fitting: _not stated_
   - validation: _not stated_
3. **Core mass from dust continuum**: Mass from 3.4 mm and 1.1 mm continuum with T=15 K, opacities, gas-to-dust 150  
  > "Adopting a gas to dust mass ratio of 150 (cite: draine11), a dust opacity of $\rm \kappa_{1.1mm}=1.0\,cm^2g^{-1}$ and $\rm \kappa_{3.4mm}=0.17\,cm^2g^{-1}$" (4.1 Core mass)
   - assumption: Dust temperature equals gas kinetic temperature, 15 K; thermal dust emission dominates  
  > "it is safe to assume that dust and gas are thermalized, such that dust temperature is equal to gas kinetic temperature" (4.1 Core mass)
   - fitting: _not stated_
   - validation: Compared with 870 um single-dish; >60% missing flux so mass is a lower limit  
  > "more than 60% of the missing flux leads to the above core mass being a lower limit" (4.1 Core mass)
4. **Outflow mass, momentum, timescale, energetics**: 2-D Gaussian fits to lobes for SiO flux; mass scaled by SiO abundance; momentum from Vmax; dynamical time from L/|V-Vlsr|  
  > "Using 2-D Gaussian fits to the gas lobes in Figure [1](#source)d, we measure the SiO $J=2\rightarrow1$ total flux of the red-shifted lobe as 4.02 Jy and of the blue-shifted lobe as 2.06 Jy." (4.2 Physical properties of the W-E oriented outflow)
   - assumption: SiO 2-1 optically thin; outflow temperature >= 15 K; wind speed 300 km/s; mass loading 0.1-0.3  
  > "(1) the shocked gas in the outflow is warmer than or at least has the same temperature as the core centre (15 K); (2) $\rm SiO$ $J=\rm 2\rightarrow1$ is optically thin." (4.2 Physical properties of the W-E oriented outflow)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Cleaning archival ALMA data  
  > "cleaned it with natural weighting in CASA (cite: mcuullin07)" (2.4 ALMA archival data)
- **GILDAS** : NOEMA calibration and combining NOEMA with 30 m data  
  > "We combined the large-scale $\rm SiO$ $J=\rm 2\rightarrow1$ obtained from the IRAM 30 m with the high resolution data from NOEMA using GILDAS." (2.2 IRAM 30 m telescope)
- **pvextractor** : PV diagrams  
  > "using the “pvextractor" code" (3.2 Position-velocity (PV) diagram)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA SiO 5-4 blue lobe deconvolved size | 2.9'' x 2.2'' (PA=108 deg) | not stated | arcsec | 1 | appears more compact ($\rm 2.9\ensuremath{''}\times2.2\ensuremath{''}$, PA=108$\rm ^\circ$ after 2-D Gaussian deconvolution) |
| Core mass (3.4 mm; 1.1 mm) | ~40 (~53) | not stated | Msun | 3 | we estimate a core mass of $\rm \sim40\,M_{\odot}$ ($\rm \sim53\,M_{\odot}$) |
| SiO 2-1 flux red/blue lobe | 4.02 / 2.06 | not stated | Jy | 4 | we measure the SiO $J=2\rightarrow1$ total flux of the red-shifted lobe as 4.02 Jy and of the blue-shifted lobe as 2.06 Jy. |
| Outflow dynamical timescale | ~10^4 | not stated | yr | 4 | we derive the maximum as the outflow dynamic timescale $\rm t_{dyn}\sim10^4$ years |
| Outflow momentum | 6.1e-10/chi_SiO | not stated | Msun km/s | 4 | ${6.1\times10^{-10}}/{\chi_{SiO}}\,M_{\odot}km\,s^{-1}$ |

## Qualitative findings

- SiO 2-1 shows W-E red/blue lobes around the continuum peak, indicating a bipolar outflow; ALMA SiO 5-4 blue lobe is more compact and closer to the continuum  
  > "Our SiO detection is consistent with ALMA archival data of $\rm SiO$ $J=\rm 5\rightarrow4$, whose high-velocity blue-shifted gas reveals a more compact lobe spatially closer to the dust center." (abstract)

## Claim tuples

- H: Is the 70 um dark core S-A starless? | E: NOEMA+30m SiO 2-1 mapping, with ALMA SiO 5-4 archival comparison | R: High-velocity red/blue SiO lobes up to 40 km/s | F: A protostellar outflow exists; the core is in an early stage of high-mass protostar formation | **supported**
- H: Is the outflow consistent with a low-luminosity source? | E: Outflow energetics and accretion scenarios | R: t_dyn ~1e4 yr, outflow weaker than in more evolved regions | F: Episodic accretion may explain the low luminosity | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Cloud-cloud collision or grain-grain collisions as SiO sources not supported by observations  
  > "However, previous and our observations do not provide evidences for these mechanisms." (3.3 SiO Line profiles: towards/away from the dust core)
- How they decided it was enough: _not stated_
- Limitation (authors): SiO abundance unknown, so outflow properties uncertain; ALMA bandpass covers only part of blueshifted range  
  > "The exact physical properties of the SiO outflows is yet uncertain, due to the unknown SiO abundance with respect to $\rm H_2$ ($\rm \chi_{SiO}$)." (4.2 Physical properties of the W-E oriented outflow)
- Caveat (inferred, ours): Outflow parameters scale with unknown SiO abundance
- Caveat (inferred, ours): Single-temperature 15 K assumption
- Caveat (inferred, ours): ALMA 5-4 analysis is minimal with missing processing details

## Reproducibility

- Data public (paper): ALMA data from the public archive  
  > "We download the calibrated data from the ALMA archive" (2.4 ALMA archival data)
- Products in archive: _not stated_
- Missing: NOEMA and 30 m data are not stated to be public
- Missing: CASA imaging parameters
- Missing: Combination procedure details
- Data volume (inferred): ~10-50 GB for the ALMA Cycle 0 project
- Score (inferred): 3/5, ALMA part is simple, but the key results rely on NOEMA/IRAM data and few imaging parameters are given.
- Rediscovery candidate: no, Main results depend on non-ALMA NOEMA/30m data and the ALMA recipe is incomplete.

## Links

- Method: (cite: tan13) (ALMA observation details)
- Method: (cite: feng16) (SMA and 30 m observations and calibration)
- Companion: (cite: feng16) (Earlier line survey of G28.34 S)

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 35,
  "rate": 0.493
 },
 "evidence_ok": true
}
```
