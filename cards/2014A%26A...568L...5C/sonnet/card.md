# The ALMA view of the protostellar system HH212. The wind, the cavity, and the disk

`2014A&A...568L...5C` | Astronomy and Astrophysics 2014 | first author: Codella, C. | arXiv: 1407.6229 | DOI: 10.1051/0004-6361/201424103

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: What is the kinematics of the innermost envelope, cavity, wind and possible Keplerian disk of the Class 0 protostar HH212?  
  > "We wish to exploit the unmatched combination of high angular resolution, high sensitivity, high-imaging fidelity, and spectral coverage provided by ALMA to shed light on the complex kinematics of the innermost central regions of HH212." (abstract)
- Target **HH212 (MM1 protostar)**: coordinates RA(J2000)=05h43m51.41s, Dec=-01d02m53.17s  
  > "Positions are given with respect to the MM1 protostar, located at $\alpha({\rm J2000})$ = 05$^h$ 43$^m$ 51$s$41, $\delta({\rm J2000})$ = –01$\ensuremath{^\circ}$ 02$\ensuremath{'}$ 53$\ensuremath{''}$17" (Observations); "HH212 is a strikingly bright and symmetric bipolar jet from a Class 0 source in Orion (at 450 pc)" (Introduction); z/distance 450 pc  
  > "Positions are given with respect to the MM1 protostar, located at $\alpha({\rm J2000})$ = 05$^h$ 43$^m$ 51$s$41, $\delta({\rm J2000})$ = –01$\ensuremath{^\circ}$ 02$\ensuremath{'}$ 53$\ensuremath{''}$17" (Observations); "HH212 is a strikingly bright and symmetric bipolar jet from a Class 0 source in Orion (at 450 pc)" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.000647.S
- bands: Band 7 (850 um)  
  > "using the ALMA interferometer in band 7 in the extended configuration of the Early Science Cycle 0 operations" (abstract)
- frequencies and spectral setup: 488 kHz (0.43 km/s) spectral units; C17O, SiO, C34S in one set-up  
  > "were observed using spectral units of 488 kHz (0.43 km s$^{-1}$) resolution." (Observations)
- continuum bandwidth: _not stated_
- arrays: 24 12-m antennas  
  > "HH212 was observed with ALMA using 24 12-m antennas on 2012 December 1 during the Early Science Cycle 0 phase." (Observations)
- configurations: _not stated_
- baselines: about 20 m to 360 m  
  > "The shortest and longest baselines were about 20 m and 360 m" (Observations)
- angular resolution: 0.65"x0.47" (PA=35 deg)  
  > "Images have a typical clean-beam FWHM of $0.65\ensuremath{''}\times0.47\ensuremath{''}$ (PA = 35$\ensuremath{^\circ}$)" (Observations)
- max recoverable scale: 3 arcsec at 850 um  
  > "we obtained a maximum unfiltred scale of 3$\ensuremath{''}$ at 850 $\mu$m" (Observations)
- sensitivity: ~1 mJy/beam continuum; 3-4 mJy/beam in 0.44 km/s channels  
  > "an rms noise of $\sim$ 1 mJy beam$^{-1}$ for continuum, and 3–4 mJy beam$^{-1}$ in the 0.44 km s$^{-1}$ channels" (Observations)
- time on source: _not stated_
- observing dates: 2012 December 1  
  > "HH212 was observed with ALMA using 24 12-m antennas on 2012 December 1" (Observations)
- pi or archival as stated: PI: C. Codella  
  > "(PI: C. Codella)" (Acknowledgements)
- Line: C17O 3-2 (337061.13 MHz)
- Line: SiO 8-7 (347330.63 MHz)
- Line: C34S 7-6 (337396.69 MHz)
- External data: Spectroscopic parameters from JPL and CDMS databases  
  > "Spectroscopic parameters were extracted from the Jet Propulsion Laboratory molecular database (Pickett et al. 1998) and the Cologne Database for Molecular Spectroscopy (Müller et al. 2005)." (footnote 1) [from Pickett et al. 1998; Müller et al. 2005]
- External data: C34S collisional rates used for critical density  
  > "according to the collisional rates of Lique et al. (2006)" (C34S: warped cavity and wide-angle flow) [from Lique et al. (2006)]

## Processing

### Calibration

- pipeline or manual: standard procedures  
  > "Calibration was carried out following standard procedures, using quasars J0538–440, J0607–085, as well as Callisto and Ganymede." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto and Ganymede (quasars J0538-440, J0607-085 also used)  
  > "using quasars J0538–440, J0607–085, as well as Callisto and Ganymede" (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA for spectral line imaging  
  > "Spectral line imaging was achieved with the CASA package." (Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
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
- final beam: 0.65"x0.47", PA 35 deg  
  > "Images have a typical clean-beam FWHM of $0.65\ensuremath{''}\times0.47\ensuremath{''}$ (PA = 35$\ensuremath{^\circ}$)" (Observations)
- final rms: ~1 mJy/beam continuum; 3-4 mJy/beam per 0.44 km/s channel  
  > "an rms noise of $\sim$ 1 mJy beam$^{-1}$ for continuum, and 3–4 mJy beam$^{-1}$ in the 0.44 km s$^{-1}$ channels" (Observations)

### Inherited from earlier work

- Centroid-from-elliptical-Gaussian-fit-in-uv approach as in other Class 0 disk studies  
  > "Similarly to other Class 0 disk studies (see e.g. Murillo et al. 2013, and references therein), the emission centroid positions in each channel were obtained from elliptical Gaussian fits in the $uv$ domain" (C17O(3-2): rotating envelope cavities and inner disk) [from Murillo et al. 2013]

### Not stated but needed to reproduce (our reading)

- Calibration pipeline/manual choice and CASA version
- Weighting/robust, cell and image size, deconvolver, masks
- Continuum subtraction line-free channels
- Fitting details of Keplerian curve (how 0.3±0.1 Msun and uncertainties derived), inclination assumed
- Channel ranges used for LV/HV centroids
- Flux calibration scale and uncertainty
- GILDAS version

## Analysis recipe

1. **Determine systemic velocity**: Channel maps for most extended emission and symmetry, plus PV diagram perpendicular to jet (PA=112 deg)  
  > "the position-velocity (PV) diagram of the C$^{17}$O(3–2) emission perpendicular to the jet axis (PA = 112$\ensuremath{^\circ}$), see Fig. 2ab, which shows that the emission is most extended and most symmetric" (Line results and analysis, Systemic velocity)
   - software: GILDAS
   - fitting: _not stated_
   - validation: Compared with NH3 value of +1.6 km/s from Wiseman et al. 2001  
  > "This value is slightly different from the +1.6 km s$^{-1}$ measured using NH$_3$(1,1) VLA emission by Wiseman et al. (2001)." (Systemic velocity)
2. **Measure channel centroids of C17O LV and HV emission**: Elliptical Gaussian fits in the uv domain per channel with GILDAS uv-fit  
  > "We used the GILDAS $uv-fit$ task" (footnote 3)
   - software: GILDAS
   - fitting: elliptical Gaussian uv-fit  
  > "the emission centroid positions in each channel were obtained from elliptical Gaussian fits in the $uv$ domain" (C17O(3-2): rotating envelope cavities and inner disk)
   - validation: Centroid errors much smaller than beam  
  > "is typically much smaller than the beam size" (footnote 3)
3. **Compare equatorial centroid velocity gradient with rotation curves to estimate central mass**: Compare with Keplerian and r^-1 (angular momentum conserving) rotation curves  
  > "We compare in Fig. [3](#fig:disk) the centroid measurements along the disk plane with Keplerian rotation curves and, as a reference, with a $\sim$ $r^{-1}$ rotation curve" (C17O(3-2): rotating envelope cavities and inner disk)
   - assumption: Distance 450 pc  
  > "a Class 0 source in Orion (at 450 pc)" (Introduction)
   - fitting: _not stated_
   - validation: Agrees with 0.2 Msun from Lee et al.; r^-1 not ruled out  
  > "Although a $\sim$ $r^{-1}$ trend is not ruled out" (C17O(3-2): rotating envelope cavities and inner disk)

## Software

- **CASA** : Spectral line imaging  
  > "Spectral line imaging was achieved with the CASA package." (Observations)
- **GILDAS** : Data analysis incl. uv-fit  
  > "Data analysis was performed using the GILDAS[^2] package." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Systemic velocity | +1.3 | 0.2 | km/s | 1 | has to be close to $\simeq +1.3\pm0.2$ km s$^{-1}$ |
| Protostar mass | 0.3 | 0.1 | Msun | 3 | keplerian rotation out to $\simeq 0.2\ensuremath{''}$ = 90 AU around a 0.3$\pm$0.1 $M_{\rm \odot}$ protostar |
| Disk radius | 0.2 arcsec = 90 AU | not stated | arcsec / AU | 2 | an inner rotating equatorial disk of radius $\simeq 0.2\ensuremath{''}$ (90 AU) |
| C17O envelope FWHM | 460 | not stated | AU | 0 | protostellar envelope of FWHM $\simeq$ 460 AU |

## Qualitative findings

- C34S shows an S-shaped warp despite straight jet and traces a rotating wide-angle flow, suggesting disk winds  
  > "A surprising finding is the S-shaped warp seen in C$^{34}$S, despite the very straight axial jet." (C34S: warped cavity and wide-angle flow)

## Claim tuples

- H: Does HH212 host a rotating, possibly Keplerian disk? | E: uv-plane centroid fits of high-velocity C17O channels compared with rotation curves | R: Centroids lie on equatorial plane, consistent with Keplerian rotation to 0.2" (90 AU) around 0.3±0.1 Msun | F: Possible Keplerian disk of ~90 AU radius | **partially**
- H: Is there a wide-angle wind around the jet? | E: C34S(7-6) channel maps | R: Nested, rotating biconical structure becoming more collimated at higher velocity, with S-shaped warp | F: Wide-angle flow suggests disk winds; warp may indicate misaligned B and rotation axes | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: r^-1 rotation curve (angular momentum conservation) not ruled out  
  > "Although a $\sim$ $r^{-1}$ trend is not ruled out" (C17O(3-2): rotating envelope cavities and inner disk)
- How they decided it was enough: _not stated_
- Limitation (authors): Higher spatial and spectral resolution needed to confirm disk size and Keplerian nature  
  > "The present results calls for more observations at high spatial and spectral resolutions of disk tracers to confirm the disk size and verify its keplerian nature." (Conclusions)
- Caveat (inferred, ours): Keplerian claim rests on few centroid points at ~0.5" beam; r^-1 not excluded
- Caveat (inferred, ours): Inclination and fit method not given
- Caveat (inferred, ours): Warp interpretation speculative

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Rotation curve fitting details
- Missing: Calibration details
- Data volume (inferred): ~10-20 GB
- Score (inferred): 3/5, Public Cycle 0 data and simple analysis, but imaging and fit parameters are not given.
- Rediscovery candidate: no, Recipe incomplete: imaging and Keplerian fit settings are missing.

## Links

- Method: Murillo et al. 2013 (uv-plane centroid approach for Class 0 disks)
- Companion: Lee et al. 2014 (Earlier ALMA observations of HH212 (HCO+, continuum))

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.000647.S"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00647.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 61,
  "stated": 33,
  "rate": 0.541
 },
 "evidence_ok": true
}
```
