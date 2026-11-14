# CO envelope of the symbiotic star R Aquarii seen by ALMA

`2018A&A...616A..61R` | Astronomy and Astrophysics 2018 | first author: Ramstedt, S. | arXiv: 1806.04979 | DOI: 10.1051/0004-6361/201833394

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, stellar_physics
- Question: What is the spatial and kinematic distribution of CO gas in the envelope of the symbiotic star R Aqr, and what does it imply for the average mass-loss rate and dynamics?  
  > "In this paper we present the first resolved CO line observations of the circumstellar envelope (CSE) around R Aqr." (Introduction)
- Target **R Aqr**: coordinates 23:43:49.491 -15:17:04.648 (J2000)  
  > "| R Aqr  | 23:43:49.491 | -15:17:04.648 | 95.3$\pm$0.6 mJy |" (Table 1); "At 218 pc (cite: minetal14), R Aqr is the closest symbiotic star" (Introduction); z/distance 218 pc  
  > "| R Aqr  | 23:43:49.491 | -15:17:04.648 | 95.3$\pm$0.6 mJy |" (Table 1); "At 218 pc (cite: minetal14), R Aqr is the closest symbiotic star" (Introduction); distance from Min et al. 2014 (cite: minetal14)  
  > "| R Aqr  | 23:43:49.491 | -15:17:04.648 | 95.3$\pm$0.6 mJy |" (Table 1); "At 218 pc (cite: minetal14), R Aqr is the closest symbiotic star" (Introduction)

## Data provenance

- ALMA projects: 2012.1.00524.S
- bands: ~345 GHz (Band 7), spectral windows at 331, 333, 343, 345 GHz  
  > "The correlator was set up with four $\sim$2 GHz wide spectral windows centered on 331, 333, 343, and 345 GHz." (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: main array, 36 12 m antennas; no ACA or total power  
  > "The R Aqr system was observed on 21 May 2015 with 36 main-array 12 m antennas." (2 Observations)
- configurations: _not stated_
- baselines: 21 m to 539 m  
  > "The longest baseline of the main array was 539 m, and the shortest was 21 m" (2 Observations)
- angular resolution: 0.38"x0.33", PA 77.4 deg  
  > "The full width at half-maximum beam width of the final images is 0.38$''$$\times$0.33$''$ with a position angle of 77.4$^{\circ}$." (2 Observations)
- max recoverable scale: just over 5 arcsec at 345 GHz  
  > "corresponding to a maximum recoverable scale of just over 5$''$ at 345 GHz." (2 Observations)
- sensitivity: rms 4.0 mJy/beam in emission-free channels (2 km/s)  
  > "The rms noise level reaches 4.0 mJy/beam in the emission-free channels." (2 Observations)
- time on source: 48.15 min  
  > "The total on-source observing time was 48.15 mins." (2 Observations)
- observing dates: 21 May 2015  
  > "The R Aqr system was observed on 21 May 2015" (2 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2, v=0 (345.796 GHz)
- Line: 13CO J=3-2 (330.588 GHz)
- Line: 28SiO J=8-7, v=1 (342.504 GHz)
- Other facility **VLT-SPHERE/ZIMPOL**: Halpha image of inner jet and stars, overplotted  
  > "the different molecular features are overplotted on the H$\alpha$ VLT-SPHERE/ZIMPOL image of the inner jet and the two stars (cite: schmetal17)" (5 Molecular emission in context)
- External data: Orbital parameters of the binary (inclination 70 deg, semimajor axis ~6 AU, radial velocities, periastron timing)  
  > "They derived an orbit inclination of 70$^{\circ}$ from the pole and a semimajor axis of the Mira orbit on the order of 6 AU." (3.3 Wind variations along the orbit) [from Gromadzki & Mikolajewska 2009 (cite: grommiko09)]
- External data: Previous CO(2-1) mass-loss rate 9e-6 Msun/yr with size 2e14 cm and CO abundance 5e-4  
  > "they estimated a mass-loss rate of $\dot{M}$=9$\times$10$^{-6}$ M$_{\odot}$ yr$^{-1}$." (3.1 Average mass-loss rate) [from Bujarrabal et al. 2010 (cite: bujaetal10)]
- External data: Distance 218 pc  
  > "At 218 pc (cite: minetal14), R Aqr is the closest symbiotic star" (Introduction) [from Min et al. 2014 (cite: minetal14)]
- Simulation/model as data: Idealized thin optically thin plate with radial or Keplerian velocity field viewed 20 deg below edge-on, for PV and moment-1 illustration  
  > "Figure [4](#pv) shows the expected emission distribution from an infinitesimally thin, uniform, optically thin round plate viewed from an angle of 20$^{\circ}$ below edge-on" (3.4 Can rotation be detected?)

## Processing

### Calibration

- pipeline or manual: Standard calibration in CASA; Ceres flux rescaled relative to pipeline reduction  
  > "Standard calibration and imaging was performed using the Common Astronomy Software Applications package (cite: mcmuetal07)." (2 Observations)
- casa version: CASA 5.1.1 (used to check Ceres fluxes)  
  > "The Ceres fluxes for the observing epoch were checked in CASA 5.1.1 and was found to be 13% lower than adopted in the pipeline reduction." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres (amplitude, bandpass: Ceres and J2348-1631); phase J2348-1631  
  > "Ceres and quasar J2348-1631 were used as amplitude and bandpass calibrators." (2 Observations)
- flux scale uncertainty: could still be of order 20%  
  > "we caution that the absolute flux calibration error using Ceres could still be on the order of 20% ." (2 Observations)
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
- continuum subtraction: continuum subtracted from channels covering 12CO(3-2) before averaging to 2 km/s  
  > "The continuum was subtracted from the channels covering the $^{12}$CO $J$ = 3 $\rightarrow$ 2 (henceforth referred to as CO(3-2)) line emission before spectral averaging to 2 km s$^{-1}$" (2 Observations)
- line free channels: continuum image from emission-free channels across all spectral windows (channels not listed)  
  > "A continuum image was made from the emission-free channels across all spectral windows." (2 Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: cube smoothed to 0.4" with imsmooth for brightness profile  
  > "first smoothing the whole image cube to 0.4$''$ resolution using the CASA task `imsmooth`." (3.1 Average mass-loss rate)
- final beam: 0.38"x0.33", PA 77.4 deg  
  > "The full width at half-maximum beam width of the final images is 0.38$''$$\times$0.33$''$ with a position angle of 77.4$^{\circ}$." (2 Observations)
- final rms: 4.0 mJy/beam  
  > "The rms noise level reaches 4.0 mJy/beam in the emission-free channels." (2 Observations)

### Inherited from earlier work

- Scaling of outer (e-folding) radius to CO(3-2) half-brightness radius (~1.4) and mass-loss rate scaling R_e^-1.82 taken from earlier radiative transfer modeling  
  > "From previous radiative transfer modeling results (cite: ramsetal08), we estimate that the outer radius (defined as the e-folding radius, $R_{\rm{e}}$) will scale as $\sim$1.4 times the CO(3-2) half-brightness radius" (3.1 Average mass-loss rate) [from Ramstedt et al. 2008 (cite: ramsetal08)]
- Flux scale based on solar system flux models  
  > "additional flux uncertainties exist that are based on the accuracy of the solar system flux models[^1]." (2 Observations) [from Butler 2012, ALMA Memo 594]

### Not stated but needed to reproduce (our reading)

- Imaging parameters for tclean (weighting, robust, cell size, image size, deconvolver, masking)
- Line-free channel ranges for continuum and continuum subtraction
- Whether archive or pipeline products were used and the pipeline version
- Exact flux rescaling procedure applied to the cubes
- Details of the e-folding radius to mass-loss conversion (other parameters held fixed, e.g. CO abundance, expansion velocity, luminosity)
- PV slit width and extraction details
- Rest frequencies / velocity reference used for the LSR velocity

## Analysis recipe

1. **measure continuum position and flux**: Image fitting of the continuum image made from emission-free channels  
  > "The position and flux at 338 GHz was determined from image fitting and is given in Table [1](#cont)." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Ceres flux checked, scaled by 13%; calibrator J2348-1631 compared with ALMA calibrator catalog  
  > "Based on an investigation of the fluxes derived for J2348-1631 compared with the monitoring in the ALMA calibrator catalog" (2 Observations)
2. **measure line fluxes and profiles**: Spectra at 2 km/s resolution measured in a 3" aperture centered on continuum peak  
  > "The line is generated at 2 km s$^{-1}$ spectral resolution and measured with an 3$''$ aperture centered on the peak of the continuum emission." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **estimate CO envelope outer radius and average mass-loss rate**: Smooth cube to 0.4", measure brightness every 0.2" N,S,E,W out to 2.0", average, find radius of non-detection; scale to e-folding radius and mass-loss rate  
  > "The line emission was then measured every 0.2$''$ (and integrated) north, south, east, and west from the brightest pixel out to 2.0$''$" (3.1 Average mass-loss rate)
   - software: CASA imsmooth
   - parameter: R_e = 1.4 x half-brightness radius; Mdot scales as R_e^-1.82  
  > "the mass-loss rate will scale as $R_{\rm{e}}^{-1.82}$" (3.1 Average mass-loss rate)
   - assumption: Distance 218 pc; spherical symmetric standard model scaling from earlier work  
  > "The standard model used to estimate mass-loss rates from CO lines (cite: schoolof01; debeetal10) is build for a spherically symmetric, isotropically expanding, homogeneous CSE" (3.1 Average mass-loss rate)
   - fitting: _not stated_
   - validation: Compared with Bujarrabal et al. 2010 estimate  
  > "By assuming that the size of the emitting region is 2$\times$10$^{14}$ cm and a CO fractional abundance of 5$\times$10$^{-4}$, they estimated a mass-loss rate of $\dot{M}$=9$\times$10$^{-6}$ M$_{\odot}$ yr$^{-1}$." (3.1 Average mass-loss rate)
4. **interpret channel maps and orbital wind variations**: Qualitative comparison of channel map components with orbit of Gromadzki & Mikolajewska and a ring-formation scenario; dynamical timescales from sizes and velocities  
  > "A relatively short-term (on the order of tens of years) increase in the mass-loss rate along the equator plane would create an expanding ring around the Mira star." (3.3 Wind variations along the orbit)
   - assumption: Constant expansion velocity (14 km/s); orbit inclination 70 deg  
  > "Assuming a constant expansion velocity, this means that the ring would have been created from approximately 70 to 30 years ago" (3.3 Wind variations along the orbit)
   - fitting: _not stated_
   - validation: _not stated_
5. **test for rotation with PV diagram**: East-west thin-slit PV diagram compared with idealized thin plate model with radial or Keplerian velocity  
  > "The middle panel in Figure [3](#bright) shows a PV diagram of the CO(3-2) emission from R Aqr produced using a thin slit along the east-west direction." (3.4 Can rotation be detected?)
   - assumption: Disk aligned with orbital plane, viewed 20 deg below edge-on  
  > "viewed from an angle of 20$^{\circ}$ below edge-on (the expected viewing angle of a disk aligned with the orbital plane in the R Aqr system)" (3.4 Can rotation be detected?)
   - fitting: _not stated_
   - validation: Authors state rotation cannot be established with the resolution  
  > "However, with the resolution of the data, we cannot with certainty determine whether rotation is present in the molecular gas around R Aqr." (3.4 Can rotation be detected?)

## Software

- **CASA** 5.1.1 (flux check): Calibration, imaging, continuum subtraction, imsmooth  
  > "Standard calibration and imaging was performed using the Common Astronomy Software Applications package (cite: mcmuetal07)." (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux density at 338 GHz | 95.3 | 0.6 (formal fit; ~20% flux scale) | mJy | 1 | / R Aqr  / 23:43:49.491 / -15:17:04.648 / 95.3$\pm$0.6 mJy / |
| 12CO(3-2) v=0 integrated flux | 5.4 | not stated | Jy km/s | 2 | / $^{12}$CO $J$=3-2, $v$=0 /  / 345.796 / 570 / 5.4 / |
| CO(3-2) outer radius | 0.8 arcsec (~170 AU at 218 pc) | not stated | arcsec | 3 | the outer radius (where the CO(3-2) line emission is no longer detected) is 0.8$''$, which corresponds to about 170 AU at 218 pc. |
| Average mass-loss rate | 2e-7 | order of magnitude | Msun/yr | 3 | the mass-loss rate will then be on the order of $\dot{M}$=2$\times$10$^{-7}$ M$_{\odot}$ yr$^{-1}$. |
| Dynamical timescale of CSE | about 40 | not stated | yr | 4 | the dynamical timescale for the creation of the CSE is about 40 yr |
| CO(3-2) peak LSR velocity | -24 | not stated | km/s | 2 | The CO(3-2) line emission peaks at a local standard of rest (LSR) velocity of $v_{\rm{LSR}}$=-24 km s$^{-1}$ |

## Qualitative findings

- Only 12CO(3-2) is spatially resolved; other lines are unresolved and show absorption between -17 and 0 km/s  
  > "Only the $^{12}$CO(3-2) line emission is spatially resolved. All the other detected lines show unresolved emission." (2 Observations)
- A bright spot ~7" south of the continuum peak at -22 km/s relative to system velocity  
  > "We also report the detection of a bright (12$\sigma$) spot some distance ($\sim$7$''$) south of the continuum peak" (Material moving perpendicular to the orbit)

## Claim tuples

- H: What is the extent of the CO envelope and the implied average mass-loss rate? | E: Radial brightness profile of CO(3-2) from smoothed cube, scaled with earlier models | R: Outer radius 0.8" (~170 AU); Mdot ~2e-7 Msun/yr | F: The CO envelope is larger than previously assumed, giving a lower average mass-loss rate than Bujarrabal et al. | **supported**
- H: Can the velocity-resolved structures be linked to orbital-phase mass-loss variations? | E: Compared channel map components with the orbit of Gromadzki & Mikolajewska | R: Ring-like structure consistent with enhanced mass loss ~100-50 yr ago plus central recent CSE | F: A plausible but tentative scenario | **partially**
- H: Is rotation of the molecular gas detected? | E: East-west PV diagram compared with idealized disk models | R: Emission consistent with rotation in orbital sense, but degenerate with expansion at this resolution | F: Rotation cannot be established | **partially**

## Reasoning

- Why this data: Part of a sample of binary AGB stars observed with ALMA to constrain hydrodynamical models  
  > "R Aqr is part of a small sample of binary AGB stars observed with ALMA to provide observational constraints for hydrodynamical models" (Introduction)
- Why this method: _not stated_
- Alternative: Shift and brightness dip could instead be due to arcs shaped by the hot companion  
  > "could also be explained by the hot binary companion shaping arcs (with material flowing along them)" (3.3 Wind variations along the orbit)
- How they decided it was enough: _not stated_
- Limitation (authors): Beam ~0.3" too coarse for firm conclusions on dynamics  
  > "with a beam of about 0.3$''$, it would be bold to try to draw any firm conclusions about the dynamical history of molecular gas of the system" (5 Conclusions)
- Limitation (authors): Flux recovery cannot be evaluated; absolute flux error up to ~20%  
  > "no data exist that can be used to evaluate whether the total flux was recovered by the interferometer" (2 Observations)
- Caveat (inferred, ours): Mass-loss rate rests on scaling from unrelated model grids with a non-spherical, young CSE
- Caveat (inferred, ours): No uncertainty on outer radius or mass-loss rate
- Caveat (inferred, ours): Ring scenario is qualitative with no fitting
- Caveat (inferred, ours): Single short observation, no total power

## Reproducibility

- Data public (paper): Data cited by ALMA project code 2012.1.00524.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00524.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: tclean parameters, weighting
- Missing: Line-free channel selection
- Missing: Exact flux rescaling
- Missing: Mass-loss scaling input parameters
- Data volume (inferred): ~50-100 GB raw, single execution block
- Score (inferred): 3/5, Public data and simple analysis, but imaging parameters and mass-loss derivation details are missing.
- Rediscovery candidate: no, Imaging recipe is incomplete and main results are partly qualitative.

## Links

- Method: Ramstedt et al. 2008 (cite: ramsetal08) (Scaling of outer radius and mass-loss rate)
- Companion: Khouri et al. 2016 (cite: khouetal16) (Analysis of vibrationally excited CO in the same data set)
- Companion: Brunner et al. 2018 (cite: brunetal18) (Other lines in the same data set)
- Related: ALMA binary AGB star sample (Mira, W Aql, pi1 Gru)

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 48,
  "rate": 0.64
 },
 "evidence_ok": true
}
```
