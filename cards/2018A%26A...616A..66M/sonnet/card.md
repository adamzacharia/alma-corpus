# The feedback of an HC HII region on its parental molecular core. The case of core A1 in the star-forming region G24.78+0.08

`2018A&A...616A..66M` | Astronomy and Astrophysics 2018 | first author: Moscadelli, L. | arXiv: - | DOI: 10.1051/0004-6361/201832680

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: What are the physical conditions and kinematics of core A1 in G24.78+0.08, and how does the HC HII region interact with its parental molecular core?  
  > "Our aim is to determine the physical conditions and the kinematics of core A1, and study the interaction of the H II region with the parental molecular core." (abstract)
- Target **G24.78+0.08 core A1**: coordinates RA(J2000)=18h36m12.55s, Dec=-07d12m10.9s (EVN tracking center)  
  > "with bolometric luminosity of ∼2 × 10 [5] _L_ ⊙ at a distance of 7.2 ± 1.4 [1] kpc" (1. Introduction); "tracking center: RA (J2000) = 18 [h] 36 [m] 12. [s] 55 and Dec (J2000) = −07 [◦] 12 [′] 10. [′′] 9" (2.2 EVN: 6.7 GHz CH3OH masers); z/distance 7.2 ± 1.4 kpc  
  > "with bolometric luminosity of ∼2 × 10 [5] _L_ ⊙ at a distance of 7.2 ± 1.4 [1] kpc" (1. Introduction); "tracking center: RA (J2000) = 18 [h] 36 [m] 12. [s] 55 and Dec (J2000) = −07 [◦] 12 [′] 10. [′′] 9" (2.2 EVN: 6.7 GHz CH3OH masers); distance from trigonometric parallax of 6.7 GHz methanol masers (Moscadelli et al., in prep.)  
  > "with bolometric luminosity of ∼2 × 10 [5] _L_ ⊙ at a distance of 7.2 ± 1.4 [1] kpc" (1. Introduction); "tracking center: RA (J2000) = 18 [h] 36 [m] 12. [s] 55 and Dec (J2000) = −07 [◦] 12 [′] 10. [′′] 9" (2.2 EVN: 6.7 GHz CH3OH masers)

## Data provenance

- ALMA projects: 2013.1.00489.S
- bands: 1.4 mm  
  > "We combine ALMA 1.4 mm high-angular resolution (≈0 [′′] . 2) observations" (abstract)
- frequencies and spectral setup: 13 SPWs over 216.0–237 GHz: one broad (1.9 GHz) and twelve narrow (0.23 GHz), 0.33–0.66 km/s resolution  
  > "Thirteen spectral windows (SPW) were observed over the frequency range 216.0–237 GHz, one broad (bandwidth of 1.9 GHz) SPW, for sensitive continuum measurement" (2.1 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: about 0.2 arcsec  
  > "The full width at half maximum (FWHM) clean beam of the resulting images is about 0 [′′] . 2." (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: continuum 1σ 1.0 mJy/beam; channel 1–2 mJy/beam  
  > "The continuum image of G24.78+0.08 has a 1σ rms noise level of 1.0 mJy beam [−][1], limited by the dynamic range." (2.1 ALMA)
- time on source: _not stated_
- observing dates: July and September 2015 (Cycle 2)  
  > "observed by ALMA during Cycle 2 in July and September 2015" (2.1 ALMA)
- pi or archival as stated: _not stated_
- Line: H30α recombination line (231900.928 MHz)
- Line: SO2 16(1,15)–15(2,14) (236216.687 MHz)
- Line: CH3OCHO nine unblended lines (218280.900–236365.574 MHz)
- Line: CH3CN v8=1 JK=12–11 (221299.495–221422.342 MHz)
- Line: 13CH3CN JK=13–12 (232125.130–232234.188 MHz)
- Other facility **EVN**: Three-epoch 6.7 GHz methanol maser VLBI (positions, proper motions)  
  > "Data were taken at three epochs: 2007, March 20 (program code: EM064B), 2009, March 12 (EM064F), and 2012, November 3 (EM099B)." (2.2 EVN: 6.7 GHz CH3OH masers)
- Other facility **JVLA**: A-array 1.3 cm continuum, 0.093x0.079 arcsec beam, rms 14 µJy/beam  
  > "Using “Briggs” weighting with robust 0, the restoring beam is 0. [′′] 093 × 0. [′′] 079 at PA = 19.6 [◦] ." (2.3 Jansky Very Large Array)
- External data: 22 GHz water maser proper motions  
  > "The water maser proper motions have already been presented in Moscadelli et al. (2007)." (4.4 Three-dimensional motion of the methanol and water masers) [from Moscadelli et al. 2007]
- External data: SMA 225 GHz peak flux 86 mJy/beam and core flux 187 mJy; PdBI/SMA fluxes in spectrum  
  > "The 1.4 mm ALMA flux integrated over core A1, 160 mJy, is in reasonable agreement with the corresponding flux, 187 mJy, derived from previous SMA observations (Beltrán et al. 2011)." (5.1 Molecular mass distribution inside core A1) [from Beltrán et al. 2011]
- External data: VLA 7 mm continuum image  
  > "Gray-scale image: VLA A-Array 7 mm continuum observed by Beltrán et al. (2007)." (Figure 9 caption) [from Beltrán et al. 2007]
- External data: Dust opacity 1 cm2/g at 1.4 mm  
  > "Assuming a dust opacity of 1 cm [2] g [−][1] at 1.4 mm (Ossenkopf & Henning 1994)" (5.1 Molecular mass distribution inside core A1) [from Ossenkopf & Henning 1994]

## Processing

### Calibration

- pipeline or manual: ALMA CASA pipeline  
  > "Data calibration was performed using the pipeline for ALMA data analysis in the Common Astronomy Software Applications (CASA, McMullin et al. 2007) package, version 4.4." (2.1 ALMA)
- casa version: CASA 4.4  
  > "Data calibration was performed using the pipeline for ALMA data analysis in the Common Astronomy Software Applications (CASA, McMullin et al. 2007) package, version 4.4." (2.1 ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN, manual  
  > "The images for the continuum and line emissions were produced manually using the CLEAN task" (2.1 ALMA)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "with the robust parameter of Briggs (1995) set to 0.5, as a compromise between resolution and sensitivity to extended emission." (2.1 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: STATCONT statistical continuum estimate per pixel  
  > "For each SPW, we use STATCONT [2] (Sanchez-Monge et al. 2017), a statistical method to estimate the continuum level at each position of the map" (2.1 ALMA)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: about 0.2 arcsec FWHM  
  > "The full width at half maximum (FWHM) clean beam of the resulting images is about 0 [′′] . 2." (2.1 ALMA)
- final rms: continuum 1.0 mJy/beam; channel 1–2 mJy/beam  
  > "The 1σ rms noise in a single spectral channel varies in the interval 1–2 mJy beam [−][1], depending on the considered SPW." (2.1 ALMA)

### Inherited from earlier work

- Full ALMA observation, correlator setup, calibration and imaging description  
  > "A full description of the ALMA observations, correlator setup, data calibration and imaging is given in Cesaroni et al. (2017)." (2.1 ALMA) [from Cesaroni et al. (2017)]
- STATCONT method validity  
  > "The validity of our procedure is described in detail and tested with numerical simulations by Sanchez-Monge et al. (2017)." (2.1 ALMA) [from Sanchez-Monge et al. (2017)]
- VLBI data calibration and analysis in AIPS  
  > "Data were reduced with AIPS following the VLBI spectral line procedures (see, for instance, Sanna et al. (2010a) for a detailed description of the data calibration and analysis)." (2.2 EVN: 6.7 GHz CH3OH masers) [from Sanna et al. (2010a)]

### Not stated but needed to reproduce (our reading)

- Line-free channel/STATCONT parameters (sigma clipping, thresholds) per SPW
- Clean threshold, masks, image size, cell size, deconvolver
- ALMA array configuration, baselines, time on source, calibrators (only in Cesaroni et al. 2017)
- XCLASS initial conditions, optimizer and fit algorithm, source size assumption, line-blending handling
- Pixel region selection and S/N cutoff for XCLASS fits
- MADCUBA fit settings and version
- Treatment of ALMA flux scale uncertainty

## Analysis recipe

1. **Continuum subtraction**: STATCONT per-pixel continuum estimate in each SPW, subtracted from spectra  
  > "For each SPW, we use STATCONT [2] (Sanchez-Monge et al. 2017), a statistical method to estimate the continuum level at each position of the map" (2.1 ALMA)
   - software: STATCONT
   - fitting: _not stated_
   - validation: Tested with numerical simulations by Sanchez-Monge et al. (2017)  
  > "The validity of our procedure is described in detail and tested with numerical simulations by Sanchez-Monge et al. (2017)." (2.1 ALMA)
2. **Pixel-by-pixel LTE line fitting for N, Trot, VLSR, FWHM maps**: Simultaneous fit of all unblended lines of a molecular species per pixel with XCLASS (isothermal LTE, 1D radiative transfer)  
  > "by extracting spectra pixel-by-pixel from the images of the SPWs and fitting all the unblended lines of a given molecular species simultaneously." (3. Data analysis)
   - software: XCLASS
   - parameter: Ntot 1e13–1e19 cm-2; |VLSR-Vsys| ≤ 8 km/s; FWHM 0–12 km/s; Trot 50–400 K (low-energy species), 100–700 K (CH3CN v8=1)  
  > "10 [13] cm [−][2] ≤ _N_ tot ≤ 10 [19] cm [−][2] for the column density" (3. Data analysis)
   - assumption: Isothermal homogeneous source in LTE; low optical depth molecules selected  
  > "This tool models the data by solving the radiative transfer equation for an isothermal homogeneous object in local thermodynamic equilibrium (LTE) in one dimension." (3. Data analysis)
   - fitting: _not stated_
   - validation: Compared maps between molecules; CH3OCHO maps best quality; 13CH3OH and CH3CH2CN rejected as unreliable  
  > "Instead, the maps produced by fitting the 13 CH 3 OH and CH 3 CH 2 CN emission are more irregular and appear to be unreliable in large portions of the fitted area." (3. Data analysis)
3. **H30α velocity gradient**: 2D Gaussian fit to channel maps for peak positions versus velocity; linear fit; position errors from Reid et al. 1988  
  > "This is obtained by fitting the emission in the channel maps with a two-dimensional (2D) Gaussian." (4.3 The VLSR pattern in the H30α line)
   - fitting: linear fit to channel VLSR vs projected position  
  > "The dashed line is a linear fit to the data." (Figure 8 caption)
   - validation: _not stated_
4. **Dust and molecular gas mass**: Subtract free-free (extrapolated from 44 GHz) from 1.4 mm flux; convert dust flux to mass; scale to regions using CH3OCHO Ntot map  
  > "Assuming a dust opacity of 1 cm [2] g [−][1] at 1.4 mm (Ossenkopf & Henning 1994), a gas-to-dust mass ratio of 100, and a dust temperature equal to the average _T_ rot ≈ 200 K" (5.1 Molecular mass distribution inside core A1)
   - assumption: kappa=1 cm2/g at 1.4 mm, gas-to-dust 100, Td≈200 K, constant abundance  
  > "a gas-to-dust mass ratio of 100, and a dust temperature equal to the average _T_ rot ≈ 200 K" (5.1 Molecular mass distribution inside core A1)
   - fitting: _not stated_
   - validation: Ntot integral ratio compared with continuum flux ratio 23/74 = 0.31  
  > "This is in excellent agreement with the ratio of the 1.4 mm continuum fluxes 23/74 = 0.31" (5.1 Molecular mass distribution inside core A1)
5. **Dynamical mass and rigid rotation model**: Mdyn = ΔV²R/(4 sin²i G); inclination from rigid-rotation model using maser 3D relative motion of A1SW wrt A1N  
  > "a dynamical mass can be calculated using the expression _M_ dyn = (∆ _V_ [2] _R_ )/(4 (sin _i_ ) [2] _G_ )" (5.2 Velocity distribution inside core A1 and dynamical equilibrium)
   - assumption: Rigid rotation, Wy=0, rotation plane intersects sky along S–N  
  > "since _V_ LSR in core A1 increase regularly from S to N and are almost constant along E–W, for simplicity we take _W_ y = 0." (Appendix A)
   - fitting: _not stated_
   - validation: _not stated_
6. **Vibrational temperature of CH3CN**: Simultaneous fit of CH3CN v=0 and v8=1 transitions at selected positions  
  > "we have used the tool MADCUBA [9] to fit simultaneously vibrational ground (v = 0) and vibrationally excited (v 8 = 1) levels of CH 3 CN." (5.6. Excitation conditions throughout core A1)
   - software: MADCUBA
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.4: ALMA pipeline calibration, CLEAN imaging; JVLA calibration  
  > "package, version 4.4. The images for the continuum and line emissions were produced manually using the CLEAN task" (2.1 ALMA)
- **STATCONT** : continuum level estimation and subtraction  
  > "For each SPW, we use STATCONT [2] (Sanchez-Monge et al. 2017)" (2.1 ALMA)
- **XCLASS** : LTE multi-transition fitting to produce maps  
  > "we use the XCLASS (eXtended CASA Line Analysis Software Suite) tool (Möller et al. 2017)." (3. Data analysis)
- **MADCUBA** : CH3CN vibrational temperature fits  
  > "we have used the tool MADCUBA [9] to fit simultaneously vibrational ground (v = 0) and vibrationally excited (v 8 = 1) levels of CH 3 CN." (5.6 Excitation conditions throughout core A1)
- **AIPS** : EVN data reduction  
  > "Data were reduced with AIPS following the VLBI spectral line procedures" (2.2 EVN: 6.7 GHz CH3OH masers)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H30α VLSR gradient | 22 | not stated | km/s/mpc | 3 | The velocity gradient, 22 km s [−][1] mpc [−][1] (see Fig. 8, lower panel), is one of the highest so far observed towards HC H II regions. |
| Total molecular gas mass of core A1 | 4–7 (adopted ≈7) | not stated | Msun | 4 | we derive a total mass of molecular gas in core A1 of 4–7 _M_ ⊙ . |
| 1.4 mm flux integrated over core A1 | 160 | not stated | mJy | 4 | The 1.4 mm ALMA flux integrated over core A1, 160 mJy |
| 1.4 mm ALMA flux over HC HII region | 109 | not stated | mJy | 4 | we derive a flux of 109 mJy |
| Inclination of rotation axis | 53 | ±8 | deg | 5 | / _**W**_ / = 18 ± 3 km s [−][1] arcsec [−][1] and _i_ = 53 [◦] ± 8 [◦] |
| Dynamical mass of core A1 | 94 | ±20 | Msun | 5 | we obtain _M_ dyn = 94 ± 20 _M_ ⊙ . |
| Vibrational temperature CH3CN at A1N, A1M, A1SW | 939, 643, 296 | ±73, ±49, ±19 | K | 6 | we find values of _T_ vib equal to 939±73 K, 643±49 K, and 296±19 K, respectively. |
| CH3OCHO abundance | ≈2e-7 | not stated | dimensionless | 4 | The estimated abundance of CH 3 OCHO is ≈2 × 10 [−][7] |
| Ionized gas velocity required | ≥200 | not stated | km/s | 3 | the ionized gas must reach velocities ≥200 km s [−][1] close to the plane of the sky. |

## Qualitative findings

- 1.4 mm continuum dominated by free-free emission from the HC HII region  
  > "The 1.4 mm continuum is dominated by free-free emission from the intense HC H II region (size ≈1000 au) observed to the North of core A1 (region A1N)." (abstract)
- Vibrationally excited CH3CN is radiatively pumped, with Trot differing from kinetic temperature  
  > "are likely radiatively pumped, and their rotational temperature can significantly differ from the kinetic temperature of the gas." (abstract)

## Claim tuples

- H: The ionized gas in the HC HII region is in a fast flow. | E: Gaussian peak positions of H30α channel maps vs velocity, with maser 3D motions. | R: Gradient of 22 km/s/mpc over ≈60 km/s; implied ionized gas speed ≥200 km/s. | F: A fast bipolar ionized outflow expands into the molecular gas. | **supported**
- H: Temperature distribution in core A1 reflects shock heating by the HII region. | E: XCLASS Trot maps compared with SO2 emission. | R: Trot 100–400 K, peak toward A1N-W coincident with SO2 peak. | F: Shocks from the ionized flow heat the gas. | **supported**
- H: The S–N VLSR gradient in core A1 is gravitationally supported rotation of a toroid. | E: Compare Mdyn from VLSR gradient and maser inclination with total mass; compare with H30α kinematics. | R: Mdyn=94±20 Msun vs molecular mass ≈7 Msun plus ≥20 Msun stars; H30α gradient inconsistent with rotation. | F: Gradient interpreted as slow expansion of core A1, not rotation. | **partially**
- H: High-energy CH3CN v8=1 transitions are radiatively pumped. | E: MADCUBA Tvib fits vs CH3OCHO Trot. | R: Tvib 939, 643, 296 K at A1N, A1M, A1SW, exceeding Trot. | F: IR pumping dominates over collisions toward A1N and A1M. | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Multi-transition simultaneous fits used for robust molecular identification amid line forest  
  > "a robust way of molecular identification is through the simultaneous fit of multiple transitions of a given molecular species." (3. Data analysis)
- Alternative: Champagne flow interpretation rejected for H30α gradient  
  > "seems to be inconsistent with a champagne flow interpretation (Tenorio-Tagle 1979)" (5.3 A fast bipolar outflow through the HC HII region)
- How they decided it was enough: _not stated_
- Limitation (authors): H30α emission not spatially resolved; higher resolution needed  
  > "The present ALMA data do not spatially resolve the H30α emission" (5.3 A fast bipolar outflow through the HC HII region)
- Limitation (authors): Outflow tracers SiO and 13CO too noisy and patchy to use  
  > "the obtained images are too noisy and patchy to be used for" (5.4. Signature of expansion of core A1)
- Caveat (inferred, ours): LTE single-component assumption with optically thin lines may bias Trot and N
- Caveat (inferred, ours): Dust temperature of 200 K and kappa assumed; mass uncertain by factor of a few
- Caveat (inferred, ours): Free-free subtraction relies on extrapolation from non-contemporaneous 44 GHz flux
- Caveat (inferred, ours): Rigid rotation model with Wy=0 is simplistic
- Caveat (inferred, ours): Expansion interpretation rests on indirect arguments

## Reproducibility

- Data public (paper): ALMA project code printed; ALMA data not explicitly stated as public  
  > "G24.78+0.08 is one of the six targets of the program “2013.1.00489.S” to search for disks around O-type YSOs" (2.1 ALMA)
- Products in archive: _not stated_
- Missing: Detailed ALMA observing/calibration info only in Cesaroni et al. 2017
- Missing: STATCONT and XCLASS fit settings
- Missing: Unpublished VLA low-frequency fluxes (private communication)
- Missing: EVN and JVLA data reduction details
- Data volume (inferred): ~50–100 GB for the ALMA measurement sets (13 SPWs, Cycle 2)
- Score (inferred): 4/5, ALMA data are identified by project code and main steps are described, but imaging and fitting details are deferred to other papers or omitted, and several inputs need EVN/VLA data.
- Rediscovery candidate: no, Key analysis relies on EVN and unpublished VLA data and unspecified XCLASS settings, so the ALMA-only recipe is incomplete.

## Links

- Method: Cesaroni et al. (2017) (Full ALMA observation, setup, calibration and imaging description)
- Method: Sanchez-Monge et al. (2017) (STATCONT continuum estimation method)
- Method: Möller et al. (2017) (XCLASS tool)
- Companion: Moscadelli et al. (2007) (Earlier water maser VLBI proper motions)
- Companion: Beltrán et al. (2011) (Earlier PdBI/SMA observations of G24.78+0.08)
- Related: ALMA Cycle 2 program 2013.1.00489.S search for disks around O-type YSOs

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
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 51,
  "rate": 0.607
 },
 "evidence_ok": true
}
```
