# Properties of the molecular gas in the fast outflow in the Seyfert galaxy IC 5063

`2017A&A...608A..38O` | Astronomy and Astrophysics 2017 | first author: Oosterloo, Tom | arXiv: 1710.01570 | DOI: 10.1051/0004-6361/201731781

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What are the excitation, optical depth, mass, density, temperature and pressure of the molecular gas in the jet-driven fast outflow of IC 5063, from multiple CO and HCO+ transitions?  
  > "This larger range of molecular tracers allows more extensive characterisation of the physical conditions of the different kinematical components of the molecular gas." (Introduction)
- Target **IC 5063**: coordinates _not stated_; z/distance z = 0.1134 (V_hel = 3400 km/s); 47.9 Mpc angular size distance; 1 arcsec = 232 pc  
  > "IC 5063 is an early-type galaxy ($z = 0.1134$[^1])" (Introduction); "implies an angular size distance of 47.9 Mpc and a scale of 1 arcsec = 232 pc." (footnote 1); distance from Hubble constant H0 = 70 km/s/Mpc, OmegaL = 0.7, OmegaM = 0.3  
  > "IC 5063 is an early-type galaxy ($z = 0.1134$[^1])" (Introduction); "implies an angular size distance of 47.9 Mpc and a scale of 1 arcsec = 232 pc." (footnote 1)

## Data provenance

- ALMA projects: 2012.1.00435.S, 2015.1.00467.S
- bands: Band 3 (CO 1-0), Band 6 (13CO 2-1), Band 7 (CO 3-2, HCO+ 4-3); CO(2-1) from earlier data  
  > "The CO(3-2) and HCO$^+$(4-3) data were taken with Band 7 on March 22, 2016, using 37 antennas." (2 Observations and data reduction); "we used ALMA in Band 6 on May 19 and 23, 2016" (2 Observations and data reduction)
- frequencies and spectral setup: Band 7: 1.875 GHz windows (480 ch) at 341.97 and 353.05 GHz plus 2 GHz continuum windows at 340.1 and 352.0 GHz; Band 6: line window at 217.8 GHz (960 ch), continuum at 230.0 and 232.5 GHz; Band 3: 1.875 GHz window at 114.0 GHz (960 ch), continuum at 100.1 and 101.9 GHz  
  > "High spectral resolution data were taken using a 1.875 GHz wide band (960 channels) centred on 114.0 GHz." (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 12-m array only  
  > "Since only the 12-m array was used and observations at very different frequencies are involved" (2 Observations and data reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.62" (143 pc) for main CO cubes; 1.52" (~350 pc) for HCO+ and 13CO; continuum 0.60"  
  > "This resulted in data cubes having a resolution of 0.62$''$." (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: CO(1-0) 0.30, CO(2-1) 0.23, CO(3-2) 0.55 mJy/beam; HCO+ 0.90, 13CO 0.18 mJy/beam (low-res); continuum 50 uJy/beam  
  > "The noise level of the CO(1-0) data cube is 0.30 mJy beam$^{-1}$ (corresponding to 73.0 mK)" (2 Observations and data reduction)
- time on source: Band 7 ~0.5 hr; Band 6 2.5 hr; Band 3 1.9 hr  
  > "The total on-source observing time was about 0.5 hr." (2 Observations and data reduction); "The total on-source observing time is 2.5 hr." (2 Observations and data reduction); "The total on-source time was 1.9 hr." (2 Observations and data reduction)
- observing dates: 22 Mar 2016 (Band 7); 19 and 23 May 2016 (Band 6); 25 and 26 Jul 2016 (Band 3)  
  > "observed with ALMA in Band 3 on July 25 and 26, 2016 using 45 antennas." (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: 12CO 1-0 (not stated)
- Line: 12CO 3-2 (not stated)
- Line: 13CO 2-1 (not stated)
- Line: HCO+ 4-3 (not stated)
- External data: ALMA CO(2-1) data reused  
  > "we also re-use our earlier ALMA observations of the CO(2-1) emission of IC 5063 published in (cite: Morganti2015)" (2 Observations and data reduction) [from (cite: Morganti2015)]
- External data: Atomic outflow mass 3.6e6 Msun  
  > "the atomic outflow ($3.6\times 10^6$ $M_\odot$, (cite: Morganti2007))" (5.2 Mass estimates) [from (cite: Morganti2007)]
- External data: alpha_CO = 0.25 K km/s pc^2 for Tex = 29 K optically thin  
  > "For $T_{\rm ex} = 29$ K the conversion factor $\alpha_{\rm CO}= 0.25$ K $\,$km$\,$s$^{-1}$ pc$^2$ (cite: Bolatto2013)" (5.2 Mass estimates) [from (cite: Bolatto2013)]
- External data: Collision rates from LAMBDA database  
  > "use the collision rates from the LAMBDA database (cite: Schoier2005)" (5.3 Kinetic temperature, density and pressure) [from (cite: Schoier2005)]

## Processing

### Calibration

- pipeline or manual: Initial calibration in CASA with ESO-provided scripts and calibration data; phase-only self-calibration on continuum applied to line data  
  > "the initial calibration of the data was done in CASA[^3] (cite: McMullin2007)) using the calibration scripts and calibration data provided by ESO." (2 Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (Band 7); Pallas (Bands 6 and 3 per text)  
  > "involving Titan, J2056$-$4714 and J2141$-$6411 as flux, bandpass and phase calibrators respectively." (2 Observations and data reduction); "except that Pallas was used as a flux calibrator." (2 Observations and data reduction)
- flux scale uncertainty: minimum 5% error assigned  
  > "we have assigned a minimum error of 5% in the flux estimates used (cite: vanKempen2014)." (5.3 Kinetic temperature, density and pressure)
- self calibration: phase only, on continuum images, applied to line data; offsets ~0.1 arcsec corrected using continuum  
  > "additional self calibration (phase only) of the continuum images of IC 5063 and apply these calibrations also to the line data." (2 Observations and data reduction)

### Imaging

- task: MIRIAD plus self-made Python scripts  
  > "all subsequent imaging and data reduction were done using the MIRIAD[^4] software (cite: Sault1995) as well as self-made PYTHON scripts." (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "From all three observations, data cubes were made using natural weighting." (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: 0.1" pixels  
  > "the same spatial (0.1$''$ pixels) and velocity gridding" (2 Observations and data reduction)
- image size: _not stated_
- masking: iterative masking using lower-resolution version of previous cube; moment images masked with 2-sigma clipped low-res cube  
  > "All cubes were cleaned using an iterative masking technique using a lower resolution version of a cube of a previous iteration to mask emission regions" (2 Observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Hanning smoothing, 10 km/s channels giving 20 km/s resolution; smoothed to common 0.62" resolution; HCO+ and 13CO tapered to 1.52" and 100 km/s  
  > "10 $\,$km$\,$s$^{-1}$ channels, but Hanning smoothing was applied to the data cubes so that the velocity resolution is 20 $\,$km$\,$s$^{-1}$" (2 Observations and data reduction)
- final beam: 0.62" (main CO); 1.52" (HCO+, 13CO); continuum 0.60"  
  > "The HCO$^+$(4-3) and $^{13}$CO(2-1) cubes we discuss have a spatial resolution of 1.52$''$" (2 Observations and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- CO(2-1) data and its reduction  
  > "we also re-use our earlier ALMA observations of the CO(2-1) emission of IC 5063 published in (cite: Morganti2015)" (2 Observations and data reduction) [from (cite: Morganti2015)]
- Rotation curve for expected regular rotation from HST photometry, as in earlier paper  
  > "as we did in (cite: Morganti2015), indicated a rotation curve based on the HST photometry of IC 5063 of (cite: Kulkarni1998)" (3.2 Kinematics of the main CO lines) [from (cite: Morganti2015); (cite: Kulkarni1998)]
- Mass outflow rate formula Mdot = 3vM/R  
  > "The mass outflow rate can be estimated using $\dot{M} = 3 v M/R$ (cite: Maiolino2012)" (5.2 Mass estimates) [from (cite: Maiolino2012)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals and number of iterations
- Number of CLEAN iterations and cleaning thresholds
- Taper parameters for the low-resolution HCO+ and 13CO cubes
- Exact definition of regions FO, O, L, D (polygons in position-velocity space) and how line ratios and errors were extracted
- Rest frequencies used and continuum subtraction/line-free channels
- Method of chi-square or matching of RADEX grid to line ratios
- Which calibrator was used for Band 3 and 6 beyond Pallas, and flux-scale details

## Analysis recipe

1. **Calibrate, self-calibrate, image and homogenise cubes**: CASA calibration with ESO scripts; phase-only self-calibration on continuum; MIRIAD imaging with natural weighting, common resolution smoothing, offset correction  
  > "We indeed found that the self calibration had introduced offsets of the order of 0.1 arcsec. All images and data cubes we present are corrected for these offsets." (2 Observations and data reduction)
   - software: CASA, MIRIAD, Python
   - parameter: common resolution 0.62"; low-res 1.52", 100 km/s  
  > "This resulted in data cubes having a resolution of 0.62$''$." (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: No signatures of missing large-scale flux present  
  > "No signatures of missing large-scale flux (’negative bowl’) were present in any of the observations." (2 Observations and data reduction)
2. **Compute line ratio maps and pv diagrams**: Integrated intensity images and ratios R31, R32 in K km/s; pv diagrams averaged over 1.5" perpendicular to jet at PA -65 deg; pixel-by-pixel R32 from cubes  
  > "averaging the CO data cubes over a width of 1.5$''$ (corresponding to 350 pc) in the direction perpendicular to the jet axis" (3.2 Kinematics of the main CO lines)
   - software: MIRIAD, Python
   - fitting: _not stated_
   - validation: _not stated_
3. **Excitation temperature and outflow mass**: LTE optically thin Tex from R32; sum flux of pixels with R32 > 1.0; convert with alpha_CO; Mdot = 3vM/R  
  > "adding the flux from all 3-D pixels in the CO(2-1) cube, and similarly in the CO(3-2) cube, for which $R_{32}$ $> 1.0$" (5.2 Mass estimates)
   - parameter: R = 0.5 kpc, v = 300 km/s  
  > "Using $R \sim 0.5$ kpc and $v = 300$$\,$km$\,$s$^{-1}$" (5.2 Mass estimates)
   - assumption: optically thin, LTE, alpha_CO = 0.25 at Tex 29 K, spherical outflow  
  > "This assumes that the outflow has a spherical geometry." (5.2 Mass estimates)
   - fitting: _not stated_
   - validation: Compared flux integral with earlier papers' 10.0 and 12.3 Jy km/s  
  > "compares well with the values of 10.0 Jy $\,$km$\,$s$^{-1}$ and 12.3 Jy $\,$km$\,$s$^{-1}$" (5.2 Mass estimates)
4. **Non-LTE RADEX modelling of Tkin, density, pressure**: Single-slab RADEX grids in Tkin and nH2 compared to line ratios for four regions, for a range of CO column densities  
  > "we modelled the data using a single slab (1-D) model with constant kinetic temperature and density" (5.3 Kinetic temperature, density and pressure)
   - software: RADEX
   - parameter: Tkin 10-200 K (log steps 0.043); nH2 1e2-1e7 cm-3 (log steps 0.167); N(12CO) 5e15-1e20 cm-2 (log step 0.5); line width 100 km/s; Tbg 2.73 K  
  > "We set the background temperature to 2.73 K and the line width to 100 $\,$km$\,$s$^{-1}$." (5.3 Kinetic temperature, density and pressure)
   - assumption: 12CO/13CO = 100; HCO+/12CO = 1.3e-4  
  > "For the ratio $^{12}$CO/$^{13}$CO we have assumed 100." (5.3 Kinetic temperature, density and pressure)
   - fitting: Graphical comparison of tracks of line ratios in Tkin-n plane; no formal fit  
  > "The quality of models can be assessed by to what extent the different lines in the panels of Fig. [12](#fig:f_radex) intersect in a common region." (5.3 Kinetic temperature, density and pressure)
   - validation: Varied 12CO/13CO between 50 and 200 and HCO+ abundance; similar results  
  > "varying this ratio between 50 and 200 gives similar results, within the errors." (5.3 Kinetic temperature, density and pressure)

## Software

- **CASA** : initial calibration  
  > "the initial calibration of the data was done in CASA[^3] (cite: McMullin2007))" (2 Observations and data reduction)
- **MIRIAD** : self-calibration, imaging and data reduction  
  > "This self calibration and all subsequent imaging and data reduction were done using the MIRIAD[^4] software" (2 Observations and data reduction)
- **RADEX** : non-LTE radiative transfer modelling  
  > "derived using the RADEX non-LTE radiative transfer code[^2] (cite: Tak2007)" (Introduction)
- **Python** : self-made scripts  
  > "as well as self-made PYTHON scripts" (2 Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean R32 for most extreme outflow gas | 1.25 | 0.09 | dimensionless | 2 | / fast outflow / 52.6        / 2.6         / 1.79 / 0.51 / 2.08 / 0.61 / 1.25 / 0.09 / |
| Excitation temperature from mean R32 (LTE, thin) | 29 | not stated | K | 3 | indicates an excitation temperature of $T_{\rm ex}$ = 29 K |
| Highest pixel R32 and corresponding Tex | R32 ~1.65; Tex = 54 K | not stated | K | 3 | Such values correspond to $T_{\rm ex}$ = 54 K assuming optically thin emission and LTE. |
| Outflow flux integrals (R32>1.0) | CO(2-1) 9.5; CO(3-2) 25.3 | not stated | Jy km/s | 3 | The flux integrals we find are 9.5 Jy $\,$km$\,$s$^{-1}$ for the CO(2-1) line and 25.3 Jy $\,$km$\,$s$^{-1}$ for the CO(3-2) line. |
| Molecular outflow mass | 1.3e6 (CO 2-1), 1.1e6 (CO 3-2) | likely lower limit, factor of a few larger | Msun | 3 | $1.3 \cdot  10^6$ $M_\odot$ based on the CO(2-1) flux integral and $1.1 \cdot  10^6$ $M_\odot$ from the CO(3-2) data |
| Mass outflow rate | ~12 | or somewhat higher | Msun/yr | 3 | gives a gas mass outflow rate of the about $\sim$12 $M_\odot$ yr$^{-1}$ or somewhat higher |
| 13CO(2-1)/12CO(2-1) in outer disk | 0.13 | 0.01 | dimensionless | 2 | / disk         / 67.7        / 3.4         / 0.40 / 0.03 / 0.17 / 0.01 / 0.39 / 0.03 / 0.13     / 0.01     / |
| Pressure in jet-affected regions | 10^6 - 10^7.5 | not stated | K cm^-3 | 4 | The resulting pressures are in the range $10^6$–$10^{7.5}$ K cm$^{-3}$. |
| Continuum noise at 346 GHz | 50 | not stated | uJy/beam | 1 | The noise level of this continuum image is 50 $\mu$Jy beam$^{-1}$ and the spatial resolution is 0.60$''$. |

## Qualitative findings

- Inner jet-affected region has much higher CO line ratios than outer disk; outflow gas is optically thin with high excitation  
  > "The $^{13}$CO(2-1) data confirm that the outflow is optically thin." (Conclusions)
- HCO+(4-3) relatively bright in fastest outflow, implying high density  
  > "This implies that the densities in the outflowing gas are high." (Conclusions)

## Claim tuples

- H: Does the radio jet change the excitation of molecular gas? | E: Compared CO line ratio images and pv diagrams | R: R31 well above 1 in inner region, below 0.5 in outer disk; R32 1.0-1.5 for outflowing gas | F: Outflow has high excitation coincident with jet | **supported**
- H: Is outflowing gas optically thin? | E: 13CO/12CO and CO line ratios | R: 13CO(2-1)/12CO(2-1) below 0.015 in fastest outflow; ratios above 1 | F: Fast outflow is optically thin | **supported**
- H: What is the mass of the molecular outflow? | E: Sum flux where R32>1, apply optically thin alpha_CO | R: ~1e6 Msun, 12 Msun/yr | F: Cold outflow comparable to atomic outflow, small compared with ISM | **supported**
- H: What are the density, temperature and pressure in the outflow? | E: RADEX modelling of line ratios | R: Tkin 20-100 K, n 1e5-1e6 cm-3, P 1e6-1e7.5 K cm-3 | F: Pressure two orders of magnitude above disk, suggests shock compression; clumpy gas | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Tapered to low resolution to improve S/N of faint HCO+ and 13CO  
  > "in order to improve the signal-to-noise of the emission, we tapered the data to much lower spatial and velocity resolution" (2 Observations and data reduction)
- Alternative: Jets hitting unusually dense molecular material rejected as less likely  
  > "The alternative would be that the jets have hit unusually dens molecular material" (5.3 Kinetic temperature, density and pressure)
- How they decided it was enough: _not stated_
- Limitation (authors): Separation of outflowing and regular gas is uncertain, so masses are likely lower limits  
  > "the main uncertainty in the mass estimate comes from the uncertainties in the separation of regular and anomalous gas" (5.2 Mass estimates)
- Limitation (authors): Single-component model not appropriate for mixed gas; Tkin-n degeneracy  
  > "there is a degeneracy between them in the models" (5.3 Kinetic temperature, density and pressure)
- Caveat (inferred, ours): Mass depends strongly on the R32>1 threshold (factor 2 change at 0.9) and assumed alpha_CO
- Caveat (inferred, ours): RADEX grid comparison is graphical without formal likelihood or uncertainties
- Caveat (inferred, ours): Solutions rely on assumed HCO+/CO abundance and 12CO/13CO ratio

## Reproducibility

- Data public (paper): ALMA data cited by project codes in acknowledgements; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00435.S and ADS/JAO.ALMA#2015.1.00467.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Region definitions for FO, O, L, D
- Missing: Self-calibration and CLEAN parameters
- Missing: Taper settings
- Missing: Details of RADEX fitting procedure
- Data volume (inferred): ~100-300 GB raw across the projects
- Score (inferred): 3/5, Data identified and main steps described, but region definitions, self-cal and taper parameters are missing.
- Rediscovery candidate: no, Region definitions and processing parameters are incomplete, so exact numeric reproduction is hard.

## Links

- Method: (cite: Tak2007) (RADEX code)
- Method: (cite: Schoier2005) (LAMBDA collision rates)
- Companion: (cite: Morganti2015) (Earlier ALMA CO(2-1) data and outflow discovery)
- Companion: (cite: Dasyra2016) (ALMA CO(4-3) results on same object)
- Companion: (cite: Mukherjee2017) (Numerical model comparison in following paper)

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
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
  "facts": 76,
  "stated": 51,
  "rate": 0.671
 },
 "evidence_ok": true
}
```
