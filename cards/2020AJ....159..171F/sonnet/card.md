# A Ringed Pole-on Outflow from DO Tauri Revealed by ALMA

`2020AJ....159..171F` | The Astronomical Journal 2020 | first author: Fernández-López, Manuel | arXiv: 2003.01148 | DOI: 10.3847/1538-3881/ab7a10

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, protoplanetary_disks
- Question: What is the nature of the nested elliptical CO (2-1) rings around DO Tauri, and do they trace a pole-on outflow with measurable ages, mass and energetics?  
  > "We discuss the data under the hypothesis that the rings represent velocity cuts through three outflowing shells that are possibly driven by a wide-angle wind" (abstract)
- Target **DO Tauri**: coordinates RA 04h38m28.600s, Dec -26d10m49.20s (J2000, pointing)  
  > "located at 139.4$^{+1.0}_{-0.9}$ pc from Earth (cite: 2018Gaia)" (Introduction); "The array was pointed at $\alpha_{J2000.0}$ = $04^{\rm h}38^{\rm m}28\mbox{$^{\rm s}\mskip-7.6mu.\,$}600$" (2.1 ALMA observations); z/distance 139.4 +1.0/-0.9 pc  
  > "located at 139.4$^{+1.0}_{-0.9}$ pc from Earth (cite: 2018Gaia)" (Introduction); "The array was pointed at $\alpha_{J2000.0}$ = $04^{\rm h}38^{\rm m}28\mbox{$^{\rm s}\mskip-7.6mu.\,$}600$" (2.1 ALMA observations); distance from Gaia (2018Gaia)  
  > "located at 139.4$^{+1.0}_{-0.9}$ pc from Earth (cite: 2018Gaia)" (Introduction); "The array was pointed at $\alpha_{J2000.0}$ = $04^{\rm h}38^{\rm m}28\mbox{$^{\rm s}\mskip-7.6mu.\,$}600$" (2.1 ALMA observations)

## Data provenance

- ALMA projects: 2016.1.01042.S
- bands: Band 6 (1.3 mm)  
  > "We present new ALMA Band 6 observations including the CO (2-1) line and 1.3 mm continuum emission" (abstract)
- frequencies and spectral setup: 8 spectral windows (~6800 MHz total); spw3 centered 230.703 GHz contains CO(2-1) at 0.488 MHz (0.63 km/s) resolution  
  > "For our study we are particularly interested in the spectral window 3, which contains the CO (2-1) emission at a spectral resolution of 0.488 MHz" (2.1 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 16-626 m (28 Nov 2016); 32-2620 m (2 Aug 2017)  
  > "47 antennas (with baselines from 16 m to 626 m) were on duty" (2.1 ALMA observations); "with baselines from 32 m to 2620 m" (2.1 ALMA observations)
- angular resolution: CO cube from combined configs: 0.21"x0.16"; continuum 0.17"x0.12"  
  > "which yields a synthesized beam of $0.21\ensuremath{''}\times0.16\ensuremath{''}$ (PA$=7\ensuremath{^\circ}$)" (2.1 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 1.22 min (compact track); 3.7 min (extended track)  
  > "Time on source was 1.22 minutes." (2.1 ALMA observations); "The time spent on DO Tauri was 3.7 minutes" (2.1 ALMA observations)
- observing dates: 28 November 2016 and 2 August 2017  
  > "taken on 2 August 2017 with the array in a more extended configuration" (2.1 ALMA observations)
- pi or archival as stated: Archival, PI Claire Chandler  
  > "ALMA Cycle 4 archive observations (Project 2016.1.01042.S; P.I. Claire Chandler)" (2.1 ALMA observations)
- Line: CO J=2-1 (230.538 GHz)
- Other facility **HST (Legacy Archive, proposal 8215)**: [SII] and continuum images of the optical jet; jet PA measurement  
  > "we downloaded the available images of this source in the HST Legacy Archive (P.I. C. Dougados; HST proposal ID 8215" (2.2 HST archive observations)
- External data: Disk inclination 28 deg and PA 170 deg  
  > "reporting a low inclination of $28\ensuremath{^\circ}\pm0.3\ensuremath{^\circ}$ and a position angle (PA) of $170\ensuremath{^\circ}\pm1\ensuremath{^\circ}$" (Introduction) [from (cite: 2019Long)]
- External data: Optical jet blue lobe PA 250+-10 deg; blue-shifted jet velocity 95 km/s  
  > "The PA of its blue-shifted lobe is 250$\ensuremath{^\circ}\pm10\ensuremath{^\circ}$ (cite: 1997Hirth)" (Introduction) [from (cite: 1997Hirth); (cite: 1994Hirth)]
- External data: Accretion rates 1.4e-7 and 3.0e-8 Msun/yr  
  > "$\dot{M}_{acc}$ has been estimated as $1.4\times 10^{-7}$ M$_{\ensuremath{\odot}}$ yr$^{-1}$ and $3.0\times10^{-8}$ M$_{\ensuremath{\odot}}$ yr$^{-1}$" (4.3 CO masses, momentum and energy of the rings) [from (cite: 1998Gullbring; 2017AlonsoMartinez)]

## Processing

### Calibration

- pipeline or manual: ALMA-provided data reduction scripts in CASA  
  > "The ALMA data were calibrated using the data reduction scripts provided by ALMA for the Common Astronomy Software Applications (CASA) package" (2.1 ALMA observations)
- casa version: CASA 4.7.0 for calibration; 5.4.0 for imaging  
  > "which we use in its version 4.7.0" (2.1 ALMA observations); "the continuum data was imaged using CASA version 5.4.0" (2.1 ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800 (2.139 Jy at 232.366 GHz, alpha=-0.393) first track; J0423-0120 (0.835 Jy at 223.670 GHz) second track  
  > "The quasar J0510+1800 was used as bandpass and absolute flux calibrator, assuming a model with a flux density of 2.139 Jy at 232.366 GHz" (2.1 ALMA observations)
- flux scale uncertainty: ~10% for Band 6  
  > "Typically, the uncertainty in the ALMA flux measurements is estimated to be of order of $\sim10$% for Band 6." (2.1 ALMA observations)
- self calibration: Three iterations on continuum, applied to CO spw; rms 0.2 to 0.07 mJy/beam  
  > "We made three iterations of self-calibration reducing the final rms of the image by 60% (from 0.2 mJy beam$^{-1}$ to 0.07 mJy beam$^{-1}$)" (2.1 ALMA observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "We set the robust parameter to 0.5 and obtain a synthesized beam of $0.71\ensuremath{''}\times0.47\ensuremath{''}$" (2.1 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum from spws after removing line channels  
  > "which we used to generate a continuum image after removing the emission from the line channels" (2.1 ALMA observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Compact and extended tracks combined for the CO cube  
  > "For imaging and analyzing the molecular gas emission we prepared a dataset combining both configurations" (2.1 ALMA observations)
- smoothing: _not stated_
- final beam: CO cube combined: 0.21"x0.16" (PA 7 deg); continuum 0.17"x0.12" (PA 14 deg)  
  > "The synthesized beam of the resulting image is $0.17\ensuremath{''}\times0.12\ensuremath{''}$ (PA$=14\ensuremath{^\circ}$) when using robust 0.5" (2.1 ALMA observations)
- final rms: CO combined cube 4.6 mJy/beam per channel; continuum 0.06 mJy/beam  
  > "an rms noise level of 4.6 mJy beam$^{-1}$(or 3.1 K) as measured in the empty channels of the velocity cube" (2.1 ALMA observations)

### Inherited from earlier work

- Disk inclination/PA uncertainty estimated from difference with Long et al.  
  > "we estimate the uncertainty of the disk PA and inclination as the difference with the same quantities derived by (cite: 2019Long)" (3.1 The disk) [from (cite: 2019Long)]
- Column density/mass procedure analogous to earlier works  
  > "using an analogue procedure to that in (cite: 2008Pineda) and (cite: 2016Zhang), with expressions adapted to the CO (2-1) transition following (cite: 2015Mangum)" (4.3 CO masses, momentum and energy of the rings) [from (cite: 2008Pineda); (cite: 2016Zhang); (cite: 2015Mangum)]
- Wide-angle wind model for dynamical ages  
  > "adopting the wide-angle wind model of (cite: 2000Lee), we could derive the dynamical ages" (5 Conclusions) [from (cite: 2000Lee)]
- Launching region constraint method  
  > "Following (cite: 2019Zhang) we constrain the dimensions of the launching area of the outbursts" (4.4 Launching region) [from (cite: 2019Zhang)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum spw selection
- Self-calibration solution intervals and imaging parameters (cell, image size, masks, deconvolver, niter, threshold)
- How the two tracks were combined (weights, phase centers) and the cube velocity grid
- Channel-by-channel image/rms values used to define ring emission for the Minuit merit function
- Per-ring area Omega and integration velocity ranges for mass calculation
- Selection of points for power-law mass-velocity fits
- Primary beam correction details

## Analysis recipe

1. **Calibrate, self-calibrate and image continuum and CO**: ALMA scripts in CASA, continuum self-calibration applied to CO spw; separate continuum from high-res track, CO cube from combined tracks  
  > "The final solutions found during the continuum self-calibration stage were applied to the CO (2-1) spectral window and a velocity cube was constructed using robust$=0.5$." (2.1 ALMA observations)
   - software: CASA
   - parameter: robust 0.5; 0.63 km/s channels  
  > "at the native velocity resolution of 0.63 km s$^{-1}$" (2.1 ALMA observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit disk continuum**: 2D Gaussian in uv-plane with uvmodelfit; inclination from axis ratio for circular disk; image-plane Gaussian for comparison  
  > "We have fit DO Tauri's disk emission in the uv-plane after using a 2D-Gaussian model implemented in the task uvmodelfit in CASA." (3.1 The disk)
   - software: CASA uvmodelfit
   - assumption: Disk intrinsically circular  
  > "For a circular disk, this fit implies an inclination of $19\ensuremath{^\circ}\pm9\ensuremath{^\circ}$ with respect to the plane of the sky." (3.1 The disk)
   - fitting: _not stated_
   - validation: Compared with image-plane fit and Long et al. 2019  
  > "an independent 2D-Gaussian fit to the continuum emission in the image plane, gives a similar result but with a different PA" (3.1 The disk)
3. **Fit ellipses to CO rings channel by channel**: Automatic Minuit fit of an infinitely thin elliptical ring maximizing product with channel image; manual fits for blended rings  
  > "For the automatic fits we used a Perl-PDL script with the Minuit tool (cite: 1975James) which maximizes the product between the channel image and the equation of an elliptical ring" (3.3.2 Ring fitting procedure)
   - software: Perl-PDL, Minuit
   - parameter: Errors: +-0.3" manual centers/axes, +-15 deg PA, plus 0.1" and 5 deg added; PA not quoted if eccentricity < 0.35  
  > "we decided not to quote the PA of the rings when their eccentricity $\sqrt{1-(Bmin/Bmaj)^2}$ is less than 0.35" (3.3.2 Ring fitting procedure)
   - fitting: Minuit errors at 1 sigma of merit function evaluated in noise regions  
  > "Minuit derives an error for each parameter (coordinates center, major and minor axis of the ring and position angle)" (3.3.2 Ring fitting procedure)
   - validation: One ring fitted both automatically and manually for comparison  
  > "This ring is fitted automatically and manually for comparison of the results." (Table 2)
4. **Deproject outflow geometry and dynamical ages**: Rotate ring centers to outflow axis (PA 253.6 deg), deproject with i=19 deg, t_dyn=R/V with V=V_radial/cos i  
  > "We take $V\sim V_{radial}/\cos{i}$ ($i=19\ensuremath{^\circ}$ is the inclination of the outflow)" (4.2 Velocity gradients and dynamical ages)
   - assumption: Outflow perpendicular to disk; wide-angle wind model  
  > "if the jet and outflow are launched perpendicular to the circumstellar disk plane, the inclination of the jet with respect to the line of sight would be the same as that of the disk" (4.1 An outflow from DO Tauri)
   - fitting: _not stated_
   - validation: _not stated_
5. **Derive CO mass, momentum, energy**: LTE optically thin column density, M = mu m_H Omega N/X_CO, velocity corrected by inclination  
  > "we estimate the mass by doing $M=\mu m_h \Omega N_{tot}/X_{CO}$, using a mean molecular weight $\mu=2.8$ times the atomic hydrogen mass and a CO abundance of $X_{CO}=10^{-4}$" (4.3 CO masses, momentum and energy of the rings)
   - assumption: Tex = 25 K, LTE, optically thin; yields lower limits  
  > "we assume an excitation temperature of 25 K as a proxy for the mass, momentum and energy estimates" (4.3 CO masses, momentum and energy of the rings)
   - fitting: Power-law fits to mass-velocity spectra per shell  
  > "We make individual fits to each of the three shells, using only masses corresponding to larger outflow velocities that show a clear power-law behavior." (4.3 CO masses, momentum and energy of the rings)
   - validation: _not stated_
6. **Constrain launching region size**: c_s * Delta t_outburst, outburst 0.2-0.3 of shell interval, T=100 K  
  > "we obtain an upper limit for the size of the wind/jet outburst launching region of $<10-15$ au." (4.4 Launching region)
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0 (calibration); 5.4.0 (imaging): Calibration, imaging, uvmodelfit  
  > "which we use in its version 4.7.0" (2.1 ALMA observations)
- **Perl-PDL with Minuit** : Automatic ellipse fits to rings  
  > "we used a Perl-PDL script with the Minuit" (3.3.2 Ring fitting procedure)
- **DS9, IRAF, Astropy, Karma** : Listed in software section; specific use not stated  
  > "DS9 (cite: 2003Joye), CASA (cite: 2007McMullin), IRAF (cite: 1986Tody), Astropy (cite: 2013Astropy), Karma (cite: 1995Gooch), PDL (cite: 1997Glazebrook)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk continuum flux density | 116.8 | 0.1 | mJy | 2 | a flux density of 116.8$\pm0.1$ mJy |
| Disk inclination | 19 | 9 | deg | 2 | this fit implies an inclination of $19\ensuremath{^\circ}\pm9\ensuremath{^\circ}$ |
| Disk PA (uv fit) | 150 | 20 | deg | 2 | its derived PA is $150\ensuremath{^\circ}\pm20\ensuremath{^\circ}$ |
| Ring-center alignment PA | 253.6 | 0.1 | deg | 3 | gives a position angle of $253.6\ensuremath{^\circ}\pm0.1$ |
| Optical jet PA (HST) | 260 | 1 | deg | 0 | The maximum of the emission of the jet has a PA of $260\ensuremath{^\circ}\pm1\ensuremath{^\circ}$ |
| Dynamical age of outflow (LB shell) | 1090 | 90 | yr | 4 | T$_{dyn}$ (yr) / 460$\pm70$ / 700$\pm$100 / 1090$\pm$90 / 1090$\pm$90 |
| Total blue-lobe mass (lower limit) | 1.3e-4 | not stated | Msun | 5 | $1.3\times10^{-4}$ M$_{\ensuremath{\odot}}$, $1.1\times10^{-3}$ M$_{\ensuremath{\odot}}$ km s$^{-1}$ and $1.1\times10^{41}$ erg |
| Mass-velocity slope gamma (SB, M, LB) | 3.2, 2.2, 3.9 | 0.3, 0.4, 0.7 | dimensionless | 5 | $\gamma$ / 3.2$\pm$0.3 / 2.2$\pm$0.4 / 3.9$\pm$0.7 |
| Launching region size upper limit | <10-15 | not stated | au | 6 | we obtain an upper limit for the size of the wind/jet outburst launching region of $<10-15$ au |
| Outflow opening angle | 27 | not stated | deg | 4 | This implies an opening angle of $27\ensuremath{^\circ}$ |

## Qualitative findings

- CO emission shows three sets of nested elliptical rings (SB, M, LB) whose centers align with the optical jet and whose velocity increases with distance from the star.  
  > "we notice that the velocity of these structures increases with the separation from the young star" (abstract)

## Claim tuples

- H: Are the CO rings cavity-wall velocity cuts of a nearly pole-on outflow? | E: Ellipse fitting of channel maps and comparison with jet PA and disk inclination | R: Ring centers lie on a line at PA 253.6 deg, matching the jet; velocity rises with distance | F: Rings trace three outflow shells seen close to line of sight | **supported**
- H: Is the energetics consistent with other outflows? | E: LTE CO mass, momentum, energy | R: Lower limits M=1.3e-4 Msun, 1.1e41 erg, agree with Class II HH 30 | F: Consistent with outflow interpretation | **supported**
- H: Can the launching region size be constrained? | E: Shell time intervals with sound speed | R: <10-15 au | F: Narrow launching zone | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Mass estimate limited by lack of optically thick tracer, so assume Tex=25 K and optically thin  
  > "Since we do not have at hand observations of any optically thick tracer we assume an excitation temperature of 25 K" (4.3 CO masses, momentum and energy of the rings)
- Alternative: Jet-driven bowshock scenario cannot be discarded; interaction of moving DO Tau with cloud underweighted  
  > "a jet-driven bowshock scenario can not be discarded" (5 Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): Masses are lower limits; ALMA may filter extended outflow emission  
  > "it is also possible that the ALMA observations are filtering out part of the extended material of the outflow" (4.3 CO masses, momentum and energy of the rings)
- Caveat (inferred, ours): Short on-source time (1.22 min) limits sensitivity and uv coverage
- Caveat (inferred, ours): Disk inclination from a marginally resolved Gaussian fit drives all deprojection
- Caveat (inferred, ours): Ring fit uncertainties partly empirical; Tex fixed at 25 K
- Caveat (inferred, ours): Alternative origins (infall, envelope) not ruled out

## Reproducibility

- Data public (paper): Archival ALMA project and HST archive data  
  > "We present ALMA Cycle 4 archive observations (Project 2016.1.01042.S; P.I. Claire Chandler)" (2.1 ALMA observations)
- Products in archive: _not stated_
- Missing: Perl-PDL fitting script not released
- Missing: Imaging parameters beyond robust
- Missing: Ring masks/areas for mass sums
- Data volume (inferred): ~10-30 GB for two short tracks
- Score (inferred): 3/5, Public data and clear recipe with tables of ring fits, but imaging details and fitting code are missing.
- Rediscovery candidate: yes, Public archival data, ring-fit table and numeric results; recipe mostly complete though some details missing.

## Links

- Method: (cite: 2019Zhang) (launching region and outflow-shell methodology)
- Method: (cite: 2000Lee) (wide-angle wind model for dynamical ages)
- Companion: (cite: 2019Long) (earlier resolved disk of DO Tau)

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
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
  "facts": 81,
  "stated": 52,
  "rate": 0.642
 },
 "evidence_ok": true
}
```
