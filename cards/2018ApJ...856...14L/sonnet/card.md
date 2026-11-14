# A 100 au Wide Bipolar Rotating Shell Emanating from the HH 212 Protostellar Disk: A Disk Wind?

`2018ApJ...856...14L` | The Astrophysical Journal 2018 | first author: Lee, Chin-Fei | arXiv: 1802.03668 | DOI: 10.3847/1538-4357/aaae6d

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: Does a disk wind exist in the Class 0 protostellar system HH 212, as traced by a rotating outflow shell in SO and SO2 at 16 au resolution?  
  > "In this paper, we aim to determine whether a disk wind exists in HH 212 as well, using our new high-resolution molecular line data." (Introduction)
- Target **HH 212 (IRAS 05413-0104)**: coordinates _not stated_; z/distance ~400 pc  
  > "HH 212 protostellar system is a well-studied young star-forming system located in Orion at a distance of $\sim$ 400 pc." (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00024.S
- bands: Band 7 (~350 GHz), Cycle 3  
  > "Observations of the HH 212 protostellar system were carried out with ALMA in Band 7 at $\sim$ 350 GHz in Cycle 3, with 32-45 antennas" (Observations)
- frequencies and spectral setup: 6 spectral windows: SO, CO 3-2, H13CO+, SiO 8-7, HCO+ 4-3, and continuum at 358 GHz (1875 MHz bandwidth)  
  > "The correlator was set up to have 6 spectral windows" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C36-7/8  
  > "C36-7/8" (Table 1)
- baselines: 17-16196 m  
  > "The projected baselines are 17-16196 m." (Observations)
- angular resolution: ~0.04 arcsec (~16 au)  
  > "at an angular resolution of $\sim$ $0^{\prime\prime}_{^\textrm{.}}04$" (Observations)
- max recoverable scale: ~0.4 arcsec  
  > "The maximum recoverable size (MRS) scale is $\sim$ $0^{\prime\prime}_{^\textrm{.}}4$" (Observations)
- sensitivity: 1.85 mJy/beam (SO, 0.848 km/s channels); 0.48 mJy/beam (stacked SO2)  
  > "It is $\sim$ 1.85 mJy beam$^{-1}$ (or $\sim$ 12.4 K) for the SO channel maps." (Observations)
- time on source: ~88 minutes  
  > "The total time on the HH 212 system is $\sim$ 88 minutes." (Observations)
- observing dates: 2015-11-05 and 2015-12-03  
  > "Two executions were carried out in 2015, one on November 5 and the other on December 3." (Observations)
- pi or archival as stated: _not stated_
- Line: SO N_J=8_9-7_8 (346.528481 GHz)
- Line: SO2 twelve lines stacked (356.755-358.216 GHz)
- External data: Protostellar mass ~0.25 Msun  
  > "The mass of the protostar is $\sim$ 0.25 $M_\odot$ from the kinematics of the disk and envelope in molecular lines" (3.3.1) [from (cite: Lee2017com)]
- External data: Systemic velocity 1.7+-0.1 km/s LSR  
  > "the systemic velocity is assumed to be $V_\textrm{\scriptsize sys}= 1.7\pm0.1$ km s$^{-1}$ LSR" (Results) [from (cite: Lee2007)]
- External data: SO and SO2 abundances used to derive H2 column density  
  > "The abundances of SO and SO$_2$ have been estimated before at lower resolution by comparing their column density to that derived from the CO J=3-2 emission" (3.4) [from (cite: Podio2015)]
- External data: Jet mass-loss rate ~1e-6 Msun/yr and velocity ~100 km/s  
  > "The jet component was found to have a mass-loss rate of $\sim$ $10^{-6}$ $M_\odot$yr$^{-1}$ and a velocity of $\sim$ 100 km s$^{-1}$" (4.1) [from (cite: Lee2015)]

## Processing

### Calibration

- pipeline or manual: CASA calibration of passband, flux and gain  
  > "The data were calibrated with the CASA package (version 4.5) for the passband, flux, and gain" (Observations)
- casa version: CASA 4.5  
  > "The data were calibrated with the CASA package (version 4.5)" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-0120 (0.55 Jy, 0.67 Jy)  
  > "J0423-0120, 0.67 Jy" (Table 3)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "We used a Briggs weighting with a robust factor of 0.5 for the visibility weighting" (Observations)
- uv taper: outer taper of 0.03 arcsec; uv-distance >12000 m (SO) and >8000 m (SO2) excluded  
  > "Also an outer taper of $0^{\prime\prime}_{^\textrm{.}}03$ was used to obtain a better signal-to-noise ratio." (Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 4 channels binned to 0.848 km/s  
  > "we binned 4 channels to make a bigger channel with a width of $\sim$ 0.848 km s$^{-1}$" (Observations)
- final beam: _not stated_
- final rms: 1.85 mJy/beam (SO); 0.48 mJy/beam (SO2 stack)  
  > "the noise level is $\sim$ 0.48 mJy beam$^{-1}$ (or $\sim$ 3.0 K) for the resulting SO$_2$ channel maps" (Observations)

### Inherited from earlier work

- Disk/envelope kinematic model, Keplerian profile and centrifugal barrier  
  > "well described by the Keplerian rotation velocity profile (magenta curves) due to the central protostar (cite: Lee2017com)" (3.3.1) [from (cite: Lee2017com)]
- Radially expanding shell model velocity law  
  > "If the shell material is radially expanding, then we have $v_R = v_0 R$ and $v_z = v_0 z$ (cite: Lee2000)." (4.1) [from (cite: Lee2000)]
- Launching radius from MHD disk wind relation  
  > "then using Eq. 4 in (cite: Anderson2003), and an outflow velocity of 5-10 km s$^{-1}$, the launching radius is estimated to be 2-3 au" (4.1) [from (cite: Anderson2003)]

### Not stated but needed to reproduce (our reading)

- Image size and cell size
- Deconvolver, masking and clean threshold
- Continuum subtraction method and line-free channels
- Self-calibration, if any
- Exact SO2 stacking procedure and weights
- Flux calibration uncertainty
- Which SO2 lines were used in the population diagram fit and their measured intensities
- Ellipse eye-fit parameters at each z
- Phase center and coordinates

## Analysis recipe

1. **Image SO and SO2 channel maps**: Briggs weighting, taper, uv cut, channel binning; stack twelve SO2 lines  
  > "Twelve SO$_2$ lines are detected (see Table [4](#tab:lines)) and stacked" (Observations)
   - software: CASA
   - parameter: robust 0.5, taper 0.03 arcsec, 0.848 km/s channels  
  > "a velocity resolution of $\Delta v_c = 0.848$ km s$^{-1}$ per channel" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure shell radius, rotation and expansion from PV diagrams**: Eye-fit ellipses to PV cuts across the jet axis at z steps of 0.025 arcsec; radius = max offset, rotation velocity = velocity at max offset, expansion = velocity at zero offset; j = v_rot x R  
  > "we only used an eye-fitting to roughly obtain the green ellipses, which are required to pass through the emission in the shells as much as possible." (3.3.1)
   - assumption: Inclination ~4 deg so no correction needed  
  > "Since the inclination angle of the outflow is small, no correction is needed for the inclination effect." (3.3.1)
   - fitting: Eye fit, no formal fit  
  > "Since the elliptical PV structures are not well defined, we only used an eye-fitting to roughly obtain the green ellipses, which are required to pass through the emission in the shells as much as possible." (Results, Rotation and Expansion in the Shell)
   - validation: Uncertainties described in figure caption  
  > "These physical quantities of the shell are shown in Figure [\[fig:vexprot\]](#fig:vexprot), with their uncertainties described in the caption." (Results, Rotation and Expansion in the Shell)
3. **Population diagram of SO2 and column densities**: Optically thin population diagram fit to lines with Eu>70 K; SO column density assuming Tex  
  > "Fitting the data points with E$_\textrm{u} > 70$ K, we estimate a rotational temperature of 81$\pm$20 K" (3.4)
   - assumption: SO Tex 200-300 K in jet, ~100 K in shell  
  > "The excitation temperature can be assumed to be $\sim$ 100 K" (3.4)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare radially expanding vs along-shell models to observed PV**: Parabolic shell z = C R^2 + 0.02 arcsec, C~14 arcsec^-1; two velocity laws at 4 deg inclination  
  > "Figure [\[fig:pvjetfit\]](#fig:pvjetfit) shows the model PV structures of these two models at an inclination angle of $\sim$ 4$^\circ$" (4.1)
   - parameter: v0 ~42 (radial) and ~45 (along shell) km/s/arcsec  
  > "$v_0 \sim 42$ km s$^{-1}$ arcsec$^{-1}$" (4.1)
   - fitting: _not stated_
   - validation: Visual comparison; both match reasonably  
  > "both model PV structures can match the observed PV structure reasonably well" (4.1)

## Software

- **CASA** 4.5: Calibration (and imaging)  
  > "The data were calibrated with the CASA package (version 4.5)" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Specific angular momentum of shell | ~40 | not stated | au km/s | 2 | The specific angular momentum of the outflow shell is $\sim$ 40 au km s$^{-1}$. |
| SO2 rotational temperature | 81 | 20 | K | 3 | we estimate a rotational temperature of 81$\pm$20 K |
| SO2 column density | 8.2e15 | 2.0e15 | cm^-2 | 3 | a column density of 8.2$\pm2.0\times10^{15}$ cm$^{-2}$ |
| SO column density in shell | ~6e15 | not stated | cm^-2 | 3 | the SO column density is estimated to be $\sim$ 6$\times10^{15}$ cm$^{-2}$ in the outflow shell |
| Shell mass | (0.4-4)e-4 | not stated | Msun | 3 | $M_s = 1.4 m_{\textrm{\scriptsize H}_2}N_{\textrm{\scriptsize H}_2}A \sim$ $(0.4-4)\times10^{-4}$ $M_\odot$ |
| Shell dynamical age | ~45 | not stated | yr | 4 | the shell has a dynamical age of $1/v_0$ or $\sim$ 45 yrs |
| Launching radius if MHD disk wind | 2-3 | not stated | au | 4 | the launching radius is estimated to be 2-3 au |

## Qualitative findings

- Compact outflow resolved into a wide-opening rotating shell (~100 au wide) and a collimated jet aligned with the SiO jet; disk atmosphere Keplerian rotation confirmed.  
  > "We also resolve the disk atmosphere traced by the two S-bearing molecules, confirming the Keplerian rotation there." (Conclusions)

## Claim tuples

- H: The compact SO/SO2 outflow contains a rotating wide-angle shell | E: 0.04 arcsec ALMA SO and SO2 maps and PV diagrams | R: Shell width ~100 au, expanding and rotating with j ~40 au km/s | F: A rotating outflow shell is present around the SiO jet | **supported**
- H: The shell traces a disk wind rather than pushed disk material | E: Compare radial-expansion and along-shell models to PV | R: Both models fit equally | F: Cannot discriminate; either a disk wind or disk material pushed by an unseen inner wind | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: SO/SO2 have higher critical density than CO and CO is complicated by the large-scale outflow and missing flux, so CO deferred  
  > "here in HH 212, CO emission is complicated, arising from both the collimated outflow and the large-scale molecular outflow, and suffering from missing flux around the systemic velocity." (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): PV ellipses are poorly defined and eye-fitted; southern kinematics not fitted; decrease in specific angular momentum is uncertain.  
  > "This decrease in the specific angular momentum is uncertain because the rotation velocity can not be estimated accurately outside the atmosphere" (3.3.1)
- Caveat (inferred, ours): Eye-fitted ellipses without formal uncertainty make j hard to reproduce
- Caveat (inferred, ours): Model comparison is qualitative
- Caveat (inferred, ours): Excitation temperatures for SO assumed
- Caveat (inferred, ours): Abundances taken from lower-resolution work

## Reproducibility

- Data public (paper): Project code given in acknowledgments  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA# 2015.1.00024.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masking, threshold)
- Missing: Continuum subtraction details
- Missing: Ellipse fit values
- Missing: Population diagram line intensities
- Data volume (inferred): ~100-300 GB raw for two Band 7 executions
- Score (inferred): 3/5, Data and key imaging settings are given, but eye-fitting and missing imaging details limit exact reproduction.
- Rediscovery candidate: no, Main kinematic results rely on eye-fitted PV ellipses and unstated imaging details.

## Links

- Method: (cite: Goldsmith1999) (Population diagram method)
- Companion: (cite: Lee2017com) (Disk atmosphere and envelope kinematics)
- Companion: (cite: Tabone2017) (Lower resolution SO/SO2 compact outflow)
- Companion: (cite: Lee2017jet) (SiO jet observations)

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 41,
  "rate": 0.594
 },
 "evidence_ok": true
}
```
