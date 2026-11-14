# High-resolution observations of the symbiotic system R Aqr. Direct imaging of the gravitational effects of the secondary on the stellar wind

`2018A&A...616L...3B` | Astronomy and Astrophysics 2018 | first author: Bujarrabal, V. | arXiv: 1807.07272 | DOI: 10.1051/0004-6361/201833633

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, stellar_physics
- Question: How does the WD secondary gravitationally affect the AGB wind in the symbiotic system R Aqr, as seen in high-resolution continuum and CO maps?  
  > "there is no direct observational information on how the gravitational effects of the secondary on the stellar wind take place." (1 Introduction)
- Target **R Aqr**: coordinates ICRS 23:43:49.4962, -15:17:04.72 (continuum centroid)  
  > "Parallax measurements from SiO Very Long Baseline Interferometry (VLBI) data indicate a distance of 218 pc (cite: min14), although the distance from the GAIA parallax is 320 pc" (1 Introduction); "ICRS coordinates R.A.: 23:43:49.4962, dec.: –15:17:04.72" (3.1 Summary of observational results); z/distance 218 pc (VLBI) or 320 pc (GAIA); discrepancy unexplained  
  > "Parallax measurements from SiO Very Long Baseline Interferometry (VLBI) data indicate a distance of 218 pc (cite: min14), although the distance from the GAIA parallax is 320 pc" (1 Introduction); "ICRS coordinates R.A.: 23:43:49.4962, dec.: –15:17:04.72" (3.1 Summary of observational results); distance from Min et al. 2014 (VLBI parallax); GAIA parallax  
  > "Parallax measurements from SiO Very Long Baseline Interferometry (VLBI) data indicate a distance of 218 pc (cite: min14), although the distance from the GAIA parallax is 320 pc" (1 Introduction); "ICRS coordinates R.A.: 23:43:49.4962, dec.: –15:17:04.72" (3.1 Summary of observational results)

## Data provenance

- ALMA projects: 2017.1.00363.S
- bands: _not stated_
- frequencies and spectral setup: four spectral windows at 330583, 331295, 343495, 345791 MHz; resolutions 0.24, 0.98, 0.98, 0.12 MHz  
  > "The correlator was set to observe with four spectral windows, centered at frequencies 330583, 331295, 343495, and 345791 MHz, and with spectral resolutions 0.24, 0.98, 0.98 and 0.12 MHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 92 m to 8.5 km, 47-48 antennas  
  > "Data were obtained with 47-48 antennas, with baselines ranging from 92 m to 8.5 km." (2 Observations)
- angular resolution: HPBW ~40x35 mas (robust 1); 17x27 mas for long baselines  
  > "resulting in maps with half-power beam width (HPBW) $\sim$ 40$\times$35 mas" (2 Observations)
- max recoverable scale: ~2'' (field of view ~18'')  
  > "The half-power field of view and the maximum recoverable scales are $\sim$18$''$ and $\sim$2$''$, respectively." (2 Observations)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2017 Nov 21 and 23, three tracks of 1.3 h each  
  > "Observations were performed with ALMA on November 21 and 23, 2017, for three tracks of 1.3 h each." (2 Observations)
- pi or archival as stated: _not stated_
- Line: H2O nu2=2 3(2,1)-4(1,4) (331.123730 GHz)
- Line: 12CO v=1 J=3-2 (342.647636 GHz)
- Line: 29SiO v=0 J=8-7 (342.980847 GHz)
- Line: Si17O v=1 J=8-7 (332.021994 GHz)
- Other facility **VLT**: Resolved both stars, ~45 mas separation (Schmid et al. 2017)  
  > "Recent Very Large Telescope (VLT) imaging by (cite: schmid17) resolved both stars" (1 Introduction)
- External data: Orbital parameters and radial velocities  
  > "using the same radial velocity measurements as in (cite: gromik09) and the relative position of the stars in (cite: schmid17)" (Appendix B) [from Gromadzki & Mikołajewska 2009 (cite: gromik09); Schmid et al. 2017 (cite: schmid17)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline delivered with CASA  
  > "The data calibration was performed using the ALMA pipeline delivered with the CASA software." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0006-0623; flux 1.58/1.65 Jy adopted  
  > "J0006-0623 was the bandpass and flux calibrator: a flux reference of 1.58/1.65 Jy (at the lowest/highest frequencies) was adopted" (2 Observations)
- flux scale uncertainty: ~5% between tracks  
  > "Differences in the phase calibrator flux of 5% between consecutive tracks were found, which is a limit to the flux uncertainty." (2 Observations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: Hogbom  
  > "we used the Hogbom method and the Briggs weighting scheme with a robust value of 1" (2 Observations)
- weighting robust: Briggs robust = 1; robust -2 (uniform) for long-baseline map  
  > "adopting a robustness factor of –2 (equivalent to uniform weighting)" (Appendix A)
- uv taper: baselines >2.5 km only  
  > "using only data from baselines longer than 2.5 km and uniform weighting" (2 Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: line-free data from both sidebands combined, using the two widest spws  
  > "Line-free data from the two side-bands were combined and then imaged and cleaned using CASA." (Appendix A)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 17x27 mas (PA 51 deg); 30x40 mas (PA 69 deg) for robust 1; 10 mas circular restoring beam for clean-component map  
  > "The final HPBW is 17$\times$27 mas (at PA 51$^\circ$), with an rms of 220 $\mu$Jy beam$^{-1}$" (Appendix A)
- final rms: 220 uJy/beam (long-baseline map)  
  > "with an rms of 220 $\mu$Jy beam$^{-1}$" (Appendix A)

### Inherited from earlier work

- Orbital parameters adapted from earlier orbit, except i, Omega, a  
  > "The new parameters are the same as in (cite: gromik09), except for $i$" (Appendix B) [from (cite: gromik09)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges
- CASA version
- Image size and cell size
- Clean masks and iteration/threshold
- Procedure for the uv-plane disk fit
- Method for deriving the new orbit (fitting code)
- Line-map velocity resolution and smoothing
- Exact method for the spectral index of components

## Analysis recipe

1. **Image continuum**: Combine line-free data of the two widest spws and clean with Hogbom, robust 1  
  > "Line-free data from the two side-bands were combined and then imaged and cleaned using CASA." (Appendix A)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **High-resolution continuum**: Use baselines >2.5 km with uniform weighting, then re-restore clean components with a 10 mas circular beam  
  > "by imposing a circular restoring beam of 10 mas (red contours in Fig. 2)" (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Checked that emission between the maxima is 10-30 times weaker than the maxima  
  > "is 10-30 times weaker that the maxima themselves" (Appendix A)
3. **Locate the AGB star**: Compare continuum peak, uv-plane disk fit, and centroids of high-excitation lines and 29SiO absorption  
  > "gives the AGB photosphere centroid with an accuracy of $\pm$3 mas" (3.2)
   - fitting: Uniform round disk fitted in the uv plane  
  > "By fitting in the $uv$ plane a disk-like distribution, i.e. uniform and round, we find a 15-mas-wide disk" (3.1)
   - validation: Compatible with GAIA DR2  
  > "We have checked that these coordinates are fully compatible with the GAIA DR2 data." (3.2)
4. **Predict WD position**: Recompute orbit with the Gromadzki & Mikołajewska radial velocities and Schmid et al. relative astrometry  
  > "using the same radial velocity measurements as in (cite: gromik09) and the relative position of the stars in (cite: schmid17)" (Appendix B)
   - fitting: _not stated_
   - validation: _not stated_
5. **Spectral index of continuum components**: Compare fluxes at 331 and 343 GHz separately  
  > "Comparing the fluxes obtained at 331 and 343 GHz separately, we estimated the spectral index of these three emitting spots" (Appendix A)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration pipeline and imaging  
  > "The data calibration was performed using the ALMA pipeline delivered with the CASA software." (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| AGB continuum peak position (ICRS) | RA 23:43:49.49657, Dec -15:17:04.7204 | ±3 mas | ICRS | 3 | ICRS R.A. 23:43:49.49657, dec. –15:17:04.7204, gives the AGB photosphere centroid with an accuracy of $\pm$3 mas |
| Uniform disk width (uv fit) | 15 | not stated | mas | 3 | we find a 15-mas-wide disk |
| Total 0.9 mm continuum flux | ~100 | not stated | mJy | 1 | The total flux is $\sim$ 100 mJy, of which $\sim$ 70 mJy comes from the central condensation |
| Spectral indices of components A, B, C | 1.9, 3.1, 1.0 | not stated | dimensionless | 5 | we found values of about 1.9, 3.1, and 1.0 for components A, B, and C, respectively |
| WD–Mira separation in 2017.9 | 32 (+7/-12) mas at PA -102 (+3/-15) | +7/-12 mas | mas | 4 | is 32$^{+7}_{-12}$ mas, at PA –102$^{+3}_{-15}$ |
| New orbit inclination | 110 | not stated | deg | 4 | which is now 110$^\circ$ (clockwise movement) |
| CO v=1 J=3-2 total flux | 310 | 7 | mJy km/s | 0 | CO $v$=1 $J$=3$-$2  / 310$\pm$7 / 132$\pm$5 |

## Qualitative findings

- 12CO shows two plumes along the E-W orbital direction resembling WRLOF spiral arms  
  > "The shape and velocity of the plumes are similar to those expected for the projection in the plane of the sky of the spiral-like arms." (3.4)

## Claim tuples

- H: High-resolution continuum detects both stars and mass transfer | E: Long-baseline continuum map compared with predicted WD position | R: Three components; C coincides with predicted WD position; B has a dust-like spectral index | F: Components A and C are the Mira and WD, and B is the first detection of mass transfer in a symbiotic system | **supported**
- H: The CO wind is shaped by the secondary as in WRLOF models | E: 12CO J=3-2 maps and PV diagram | R: E-W plumes with velocity shifts of ~10 km/s | F: Strong equatorial confinement and a double spiral beyond the orbit | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Hollis et al. WD position judged to be a jet blob, since it implies a semimajor axis 2.7 times larger than Schmid et al. imply  
  > "The most likely explanation is that the claimed position for the WD in (cite: hollis97) is in fact an emission blow in the north jet." (Appendix B)
- How they decided it was enough: _not stated_
- Limitation (authors): Absolute astrometry ~3 mas; WD position uncertainty ~±7 mas  
  > "we thus expect absolute errors $\sim$ 3 mas" (3.1)
- Caveat (inferred, ours): Letter-length; CO analysis is qualitative with no model comparison
- Caveat (inferred, ours): Orbit recomputation details deferred
- Caveat (inferred, ours): Distance discrepancy unresolved
- Caveat (inferred, ours): Super-resolved 10 mas restoring beam interpretation is model-dependent

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masks, thresholds)
- Missing: Orbit-fit details
- Missing: Line-free channel selection
- Data volume (inferred): ~100-300 GB (three tracks, long baselines, four spws)
- Score (inferred): 4/5, The project code and main settings are given, but many imaging details are missing.
- Rediscovery candidate: no, The recipe is incomplete and the main results are partly qualitative.

## Links

- Companion: Ramstedt et al. 2018 (Lower-resolution ALMA maps of R Aqr)

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
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
  "facts": 65,
  "stated": 33,
  "rate": 0.508
 },
 "evidence_ok": true
}
```
