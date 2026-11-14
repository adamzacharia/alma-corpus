# 1000 au exterior arcs connected to the protoplanetary disk around HL Tauri

`2017A&A...608A.134Y` | Astronomy and Astrophysics 2017 | first author: Yen, Hsi-Wei | arXiv: 1708.02384 | DOI: 10.1051/0004-6361/201730894

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What are the gas kinematics in the protostellar envelope around the HL Tau disk and how might the envelope influence the embedded disk?  
  > "In this work, we study the gas kinematics in the envelope and its possible influence on the embedded disk." (abstract)
- Target **HL Tau**: coordinates J2000 04h31m38.43s +18d13m57.2s  
  > "is located in the Taurus star-forming region at a distance of 140 pc" (Introduction); "(J2000 04$^{\rm h}$31$^{\rm m}$38$.\!\!^{\rm s}$43 +18$^{\rm d}$13$^{\rm m}$57$.\!\!^{\rm s}$2; (cite: ALMA15))" (Introduction); z/distance 140 pc  
  > "is located in the Taurus star-forming region at a distance of 140 pc" (Introduction); "(J2000 04$^{\rm h}$31$^{\rm m}$38$.\!\!^{\rm s}$43 +18$^{\rm d}$13$^{\rm m}$57$.\!\!^{\rm s}$2; (cite: ALMA15))" (Introduction); distance from Kenyon94; Loinard13  
  > "is located in the Taurus star-forming region at a distance of 140 pc" (Introduction); "(J2000 04$^{\rm h}$31$^{\rm m}$38$.\!\!^{\rm s}$43 +18$^{\rm d}$13$^{\rm m}$57$.\!\!^{\rm s}$2; (cite: ALMA15))" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00551.S
- bands: 1.3 mm (Cycle 3, 13CO and C18O 2-1)  
  > "Two spectral windows, each with a bandwidth of 2 GHz, were assigned to the 1.3 mm continuum." (2 Observations)
- frequencies and spectral setup: Five spws: two 2 GHz continuum; 13CO (468.8 MHz, 122 kHz channel); C18O (234.4 MHz, 244 kHz); SO (234.4 MHz, 488 kHz)  
  > "One spectral window with a bandwidth of 468.8 MHz and a channel width of 122 kHz was set to the $^{13}$CO (2–1) line" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 14 m to 384 m  
  > "The baseline length ranges from 14 m to 384 m" (2 Observations)
- angular resolution: 0.77'' x 0.75'' (13CO), 0.77'' x 0.74'' (C18O)  
  > "The angular resolution and the noise level are 0.77$''$ $\times$ 0.75$''$ and 7 mJy Beam$^{-1}$ per channel in the $^{13}$CO image" (2 Observations)
- max recoverable scale: 12'' (1700 au)  
  > "so the maximum recoverable scale of our observations is 12$\ensuremath{''}$ (1700 au)" (2 Observations)
- sensitivity: 7 mJy/beam per channel (13CO); 6.7 mJy/beam per channel (C18O)  
  > "0.77$''$ $\times$ 0.74$''$ and 6.7 mJy Beam$^{-1}$ per channel in the C$^{18}$O image" (2 Observations)
- time on source: 30 min, 7 pointing mosaic  
  > "was observed with 7 pointing mosaic, and the total integration time on is 30 min." (2 Observations)
- observing dates: 22 March 2016, 40 antennas  
  > "ALMA cycle-3 observations toward were conducted on 22 March, 2016 with 40 antennas." (2 Observations)
- pi or archival as stated: _not stated_
- Line: 13CO 2-1 (220.398684 GHz)
- Line: C18O 2-1 (219.560358 GHz)
- Line: SO 5_6-4_5 (not stated)
- External data: Disk inclination 47 deg and PA 138 deg  
  > "has an inclination angle of 47$\ensuremath{^\circ}$ from the plane of the sky and a position angle (PA) of 138$\ensuremath{^\circ}$ (cite: ALMA15)" (Introduction) [from (cite: ALMA15)]
- External data: Disk gas temperature ~60 K at 60-100 au  
  > "was estimated to be 60 K at the outer radii of 60–100 au from the ALMA observations in the CO (1–0) emission (cite: Yen16)" (4.1 Keplerian Disk) [from (cite: Yen16)]
- External data: C18O abundance 1.5e-7 and 13CO abundance 1.5e-6 relative to H2; 13CO/C18O = 10  
  > "a C$^{18}$O abundance of 1.5 $\times$ 10$^{-7}$ relative to H$_2$ (cite: Brittain05; Smith15)" (4.1 Keplerian Disk) [from (cite: Brittain05; Smith15)]
- External data: Bolometric luminosity 3.5-15 Lsun  
  > "With $L_{\rm bol} = 3.5\mbox{--}15$ $L_\ensuremath{\odot}$ (cite: Robitaille07)" (5 Discussion) [from (cite: Robitaille07)]

## Processing

### Calibration

- pipeline or manual: Standard cycle-3 reduction script, no self-calibration; manual flag of one 13CO time range  
  > "The raw visibility data were calibrated using the standard reduction script for the cycle-3 data" (2 Observations)
- casa version: CASA 4.6  
  > "(CASA; (cite: McMullin07)) of version 4.6, and without self-calibration" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800 (2.38 Jy at 225.7 GHz), bandpass and flux  
  > "J0510+1800 with a flux of 2.38 Jy at 225.7 GHz was observed as bandpass and flux calibrators" (2 Observations)
- flux scale uncertainty: 10%  
  > "The typical absolute flux uncertainty of ALMA observations at 1 mm wavelength is 10%." (2 Observations)
- self calibration: none  
  > "and without self-calibration" (2 Observations)

### Imaging

- task: CASA clean, 0.34 km/s velocity resolution  
  > "cleaned with the CASA task “clean” at a velocity resolution of 0.34 km s$^{-1}$" (2 Observations)
- deconvolver: _not stated_
- weighting robust: uniform weighting  
  > "were generated with the uniform weighting" (2 Observations)
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
- final beam: 0.77'' x 0.75'' (13CO); 0.77'' x 0.74'' (C18O)  
  > "The angular resolution and the noise level are 0.77$''$ $\times$ 0.75$''$" (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- P-V peak-position method for rotation curves  
  > "we followed the method in (cite: Yen13)" (4.1 Keplerian Disk) [from (cite: Yen13)]
- Systematic error 10-20% of method  
  > "As discussed in (cite: Yen13) and (cite: Aso15), the method has a systematic error of 10%–20%" (4.1 Keplerian Disk) [from (cite: Yen13); (cite: Aso15)]
- 3D infall velocity profiles  
  > "we adopted the velocity profiles of three-dimensional infalling and rotational motions from (cite: Ulrich76) and (cite: Mendoza04)" (4.3 Three-Dimensional Infall and Rotation Model) [from (cite: Ulrich76); (cite: Mendoza04)]

### Not stated but needed to reproduce (our reading)

- clean threshold, masks, image size and cell size
- continuum subtraction method and line-free channels
- spw/rest-frame velocity settings and primary beam correction
- how P-V peak positions were measured (cut width, thresholds)
- exact moment-map thresholds
- initial 3D model grid and sampling
- Comparison of flagged data details beyond one time range

## Analysis recipe

1. **Image cubes and moment maps**: Calibrate with standard script, clean uniform-weighted cubes, make moment 0/1 maps  
  > "The image cubes of the $^{13}$CO (2–1) and C$^{18}$O (2–1) lines were generated with the uniform weighting" (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit Keplerian rotation curve and protostellar mass**: P-V diagrams along the major axis, peak positions fitted with power law, mass from Keplerian profile  
  > "We then fitted a power-law function to these data points" (4.1 Keplerian Disk)
   - parameter: R0 = 1'' (140 au); free parameters V_rot(R0), f, V_sys; high-velocity ranges only  
  > "Thus, there are three free parameters in the fitting, $V_{\rm rot}(R_0)$, $f$, and $V_{\rm sys}$." (4.1 Keplerian Disk)
   - assumption: Disk inclination 47 deg  
  > "on the assumption that the inclination angle of the protoplanetary disk is 47$\ensuremath{^\circ}$" (4.1 Keplerian Disk)
   - fitting: Power-law fit; sampler/likelihood not stated  
  > "We then fitted a power-law function to these data points" (Analysis, Keplerian Disk)
   - validation: Compared with Pinte16 1.7 Msun; tested removing 3 outlier 13CO points  
  > "Our measured protostellar mass is consistent with 1.7 $M_\ensuremath{\odot}$ estimated from the P–V diagrams" (4.1 Keplerian Disk)
3. **Disk gas mass from C18O**: 2D Gaussian fit to C18O moment 0; LTE optically thin mass  
  > "we fitted a two-dimensional Gaussian function to the central C$^{18}$O emission in the moment 0 map" (4.1 Keplerian Disk)
   - parameter: Tex = 60 K (100 K alternative)  
  > "with an excitation temperature of 60 K and a C$^{18}$O abundance of 1.5 $\times$ 10$^{-7}$ relative to H$_2$" (4.1 Keplerian Disk)
   - assumption: LTE, optically thin C18O, abundance 1.5e-7  
  > "On the assumption of an LTE condition and optically thin C$^{18}$O emission" (4.1 Keplerian Disk)
   - fitting: 2D Gaussian  
  > "we fitted a two-dimensional Gaussian function to the central C$^{18}$O emission in the moment 0 map" (Analysis, Keplerian Disk)
   - validation: _not stated_
4. **Arc temperature, optical depth and mass**: 13CO/C18O brightness temperature ratio gives Tex, tau; interpolated power-law temperature; pixel-by-pixel tau-corrected 13CO mass  
  > "we estimated the gas kinematic temperature and column density by comparing the C$^{18}$O and $^{13}$CO brightness temperatures" (4.2 Temperature, Column Density, and Mass of arc Structures)
   - assumption: 13CO/C18O = 10; 13CO abundance 1.5e-6; LTE; T = 15 K at 1000 au, 60 K at 100 au  
  > "the $^{13}$CO/C$^{18}$O abundance ratio was adopted to be 10" (4.2 Temperature, Column Density, and Mass of arc Structures)
   - fitting: _not stated_
   - validation: Tested ratio 5.5 giving Tex 38 K  
  > "If a lower $^{13}$CO/C$^{18}$O abundance ratio of 5.5 is adopted" (4.2 Temperature, Column Density, and Mass of arc Structures)
5. **Compare observed arc velocity with kinematic models**: Model moment 1 maps for Keplerian, infall+rotation, infall+counter-rotation, and 3D Ulrich infall, compared with observed moment 1  
  > "we computed model moment 1 maps of different kinds of gas motions and compared them with the observations" (4.3 Kinematics of arc Structures)
   - parameter: M*=1.8 Msun, i=47 deg, PA=138 deg, Vsys=7.04 km/s  
  > "In our calculation, $V_{\rm sys}$ is adopted to be 7.04 km s$^{-1}$" (Appendix 8.3)
   - assumption: Arcs in disk plane for thin models; particles anywhere along line of sight for 3D  
  > "each particle can be located anywhere along the line of sight" (4.3 Kinematics of arc Structures)
   - fitting: Best matching model V_LSR per pixel; no statistical fit  
  > "If there is a particle having its $V_{\rm los}+V_{\rm sys}$ ($=V_{\rm LSR}$) that matches the observed velocity at the same position, its $V_{\rm los}+V_{\rm sys}$ is assigned to that pixel" (Kinematical Models for the Arc Structures, Three-Dimensional Infall and Rotation Model)
   - validation: Residual map and missing-flux test against IRAM 30m  
  > "We convolved our $^{13}$CO image with the angular resolution of the IRAM 30m observations" (4.3.5 Effects of Missing Flux)

## Software

- **CASA** 4.6: Calibration and imaging with clean  
  > "(CASA; (cite: McMullin07)) of version 4.6" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| C18O rotation profile amplitude | 2.44 | 0.07 | km/s at 1'' | 2 | $(2.44\pm0.07) \times (R_{\rm rot}/R_0)^{-0.52\pm0.04}$ km s$^{-1}$ with $V_{\rm sys} = 7.04\pm0.04$ km s$^{-1}$ |
| C18O power-law index f | -0.52 | 0.04 | dimensionless | 2 | $(2.44\pm0.07) \times (R_{\rm rot}/R_0)^{-0.52\pm0.04}$ km s$^{-1}$ |
| Systemic velocity | 7.04 | 0.04 | km/s | 2 | with $V_{\rm sys} = 7.04\pm0.04$ km s$^{-1}$ |
| Protostellar mass | 1.8 | 0.3 | Msun | 2 | the protostellar mass of is estimated to be 1.8$\pm$0.3 $M_\ensuremath{\odot}$ |
| Disk gas mass from C18O | 3.5e-3 | not stated | Msun | 3 | is estimated to be 3.5 $\times$ 10$^{-3}$ $M_\ensuremath{\odot}$ with an excitation temperature of 60 K |
| Excitation temperature at NW arc peak | 15 | not stated | K | 4 | $T_{\rm ex}$ is derived to be 15 K, $\tau_{\rm C^{18}O}$ to be 0.18, and $\tau_{\rm ^{13}CO}$ to be 1.78 |
| Arc masses (blue, red) | 2.9e-3 and 2.8e-3 | not stated | Msun | 4 | The masses of the blue- and redshifted arc structures are estimated to be 2.9 $\times$ 10$^{-3}$ $M_\ensuremath{\odot}$ and 2.8 $\times$ 10$^{-3}$ $M_\ensuremath{\odot}$ |
| Velocity excess in NW blue arc | 0.8 (60-70% of free-fall) | not stated | km/s | 5 | The blueshifted velocity excess is as large as 0.8 km s$^{-1}$ |
| Mass infall rate | 2.2e-6 | not stated | Msun/yr | 5 | $5.7 \times 10^{-3}/2600 = 2.2 \times 10^{-6}$ $M_\ensuremath{\odot}$ yr$^{-1}$ |

## Qualitative findings

- Central C18O/13CO component shows Keplerian rotation; arcs are not explained by thin infall or counter-rotation but better by 3D infall/outflow  
  > "The gas kinematics of the arc structures can be better explained with three-dimensional infalling or outflowing motions." (abstract)

## Claim tuples

- H: Central compact emission traces a Keplerian disk | E: P-V peak fitting in high-velocity channels | R: f = -0.52±0.04 (C18O) | F: Consistent with Keplerian; M*=1.8±0.3 Msun | **supported**
- H: Arcs are simple infalling/rotating flattened envelopes | E: Compare model moment 1 maps | R: Thin models fail to reproduce NW blueshift or eastern blueshift | F: Not fully explained; 3D infall better | **refuted**
- H: Arc velocities obey free fall | E: 3D Ulrich model residuals | R: NW blue arc ~60-70% higher than free-fall | F: Needs external compression or outflow of clumps | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Keplerian, infall+rotation and infall+counter-rotation thin models rejected as full explanations  
  > "the motion of the arc structures is not pure rotation around" (4.3.1 Keplerian Rotation Model)
- How they decided it was enough: _not stated_
- Limitation (authors): Missing flux from lack of short spacings may bias blueshifted arc velocity  
  > "Nevertheless, adding short-spacing data to fully recover the structures at the low velocities with a high angular resolution is essential" (4.3.5 Effects of Missing Flux)
- Limitation (authors): Disk gas mass is a lower limit  
  > "our estimated disk gas mass should be considered as a lower limit" (4.1 Keplerian Disk)
- Caveat (inferred, ours): Model comparison is qualitative moment-1 matching with no chi-square or uncertainties
- Caveat (inferred, ours): Mass depends on assumed abundances and interpolated temperature
- Caveat (inferred, ours): Missing flux and ambient cloud blending complicate arc velocities

## Reproducibility

- Data public (paper): Project code given in acknowledgements; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00551.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: clean parameters and masks
- Missing: continuum subtraction details
- Missing: P-V fitting details
- Missing: model code
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 3/5, Data identified and recipe mostly described, but imaging and fitting details and model code missing.
- Rediscovery candidate: no, Key results need unspecified imaging and model implementation choices.

## Links

- Method: Yen13 (P-V rotation curve method)
- Method: Ulrich76; Mendoza04 (3D infall velocity field)
- Companion: ALMA15 (HL Tau long-baseline continuum, disk geometry)
- Companion: Pinte16 (HL Tau disk modeling)

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
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
  "facts": 77,
  "stated": 51,
  "rate": 0.662
 },
 "evidence_ok": true
}
```
