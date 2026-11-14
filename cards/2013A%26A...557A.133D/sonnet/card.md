# Unveiling the gas-and-dust disk structure in HD 163296 using ALMA observations

`2013A&A...557A.133D` | Astronomy and Astrophysics 2013 | first author: de Gregorio-Monsalvo, I. | arXiv: 1307.1357 | DOI: 10.1051/0004-6361/201321603

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What is the structure (dust and gas, radial and vertical) of the protoplanetary disk around the Herbig Ae star HD 163296?  
  > "The aim of this work is to study the structure of the protoplanetary disk surrounding the Herbig Ae star HD 163296." (abstract)
- Target **HD 163296**: coordinates RA(J2000) 17h56m21.285s, Dec -21d57m22.368s  
  > "At a distance of $122\,{\rm pc}$, is an isolated A2Ve star of estimated ${\rm age}\approx5\,{\rm Myr}$ (cite: Mon09)." (Introduction); "Continuum emission at $850\,\mu{\rm m}$ is detected centered at the position R.A.(J2000) = 17$^{h}$56$^{m}$21$s$285, Dec(J2000) =$-$21$\ensuremath{^\circ}$57$\ensuremath{'}$22$\ensuremath{''}$368." (3.1 Continuum emission at $850\,\mu{\rm m}$); z/distance 122 pc  
  > "At a distance of $122\,{\rm pc}$, is an isolated A2Ve star of estimated ${\rm age}\approx5\,{\rm Myr}$ (cite: Mon09)." (Introduction); "Continuum emission at $850\,\mu{\rm m}$ is detected centered at the position R.A.(J2000) = 17$^{h}$56$^{m}$21$s$285, Dec(J2000) =$-$21$\ensuremath{^\circ}$57$\ensuremath{'}$22$\ensuremath{''}$368." (3.1 Continuum emission at $850\,\mu{\rm m}$); distance from van den Ancker et al. 1998 (cite: vda98)  
  > "At a distance of $122\,{\rm pc}$, is an isolated A2Ve star of estimated ${\rm age}\approx5\,{\rm Myr}$ (cite: Mon09)." (Introduction); "Continuum emission at $850\,\mu{\rm m}$ is detected centered at the position R.A.(J2000) = 17$^{h}$56$^{m}$21$s$285, Dec(J2000) =$-$21$\ensuremath{^\circ}$57$\ensuremath{'}$22$\ensuremath{''}$368." (3.1 Continuum emission at $850\,\mu{\rm m}$)

## Data provenance

- ALMA projects: 2011.0.000010.SV
- bands: Band 7  
  > "Observations were performed on 2012 June 9, 11, 22, and July 6 at Band 7" (Observations description)
- frequencies and spectral setup: 4 spectral windows centered at 345.796 (CO 3-2), 346.998 (H13CO+ 4-3), 356.734 (HCO+ 4-3), 360.170 GHz (DCO+ 5-4); bandwidths 468.75, 937.50, 468.75, 117.19 MHz; velocity resolution ~0.21, 0.42, 0.21, 0.05 km/s after Hanning smoothing  
  > "The effective bandwidths used were $468.75$, $937.50$, $468.75$, and $117.19\,{\rm MHz}$, respectively" (Observations description)
- continuum bandwidth: _not stated_
- arrays: 16-19 12 m antennas, five data sets  
  > "A total of five data sets were collected, using between 16 and 19 antennas of $12\,{\rm m}$ diameter" (Observations description)
- configurations: _not stated_
- baselines: ~16 to ~400 m  
  > "projected baselines length between $\sim$16 to $\sim$400 m" (Observations description)
- angular resolution: 0.52'' x 0.38'' at PA ~82 deg  
  > "providing a synthesized beam of $0.52\ensuremath{''} \times 0.38\ensuremath{''}$ at ${\rm P.A.}\!\sim\!\!82^\circ$" (Observations description)
- max recoverable scale: ~7''  
  > "sensitive to maximum angular scales of $\sim\!\!7''$" (Observations description)
- sensitivity: rms 0.5 mJy/beam continuum; 14 mJy/beam per CO channel  
  > "The achieved rms was 0.5 mJy beam$^{-1}$ for the continuum and 14 mJy beam$^{-1}$ for each CO channel map." (Observations description)
- time on source: 3.9 h total, 2.3 h on HD 163296  
  > "accounting for 3.9 hours of total integration time including overheads and calibration (2.3 hours on HD 163296)" (Observations description)
- observing dates: 2012 June 9, 11, 22, and July 6  
  > "Observations were performed on 2012 June 9, 11, 22, and July 6 at Band 7" (Observations description)
- pi or archival as stated: ALMA science verification data  
  > "as part of the ALMA science verification program 2011.0.000010.SV" (Observations description)
- Line: CO 3-2 (345.796 GHz)
- External data: Initial disk model (favored model 3, Table 6) and photospheric parameters (Teff 9250 K, M*=2.47 Msun, L*=37.7 Lsun, LUV/L*=0.097)  
  > "The initial disk model we use is based on (cite: Til12), in particular their favored model number three (see Table 6 in that paper)." (3.3 Modelling) [from Tilling et al. 2012 (cite: Til12)]
- External data: Dust mass of 7e-4 Msun assumed  
  > "A dust mass of $7\!\times\!10^{-4}M_\odot$ (cite: Til12) was assumed" (4.1.1 The outer disk, outside of Rc) [from Tilling et al. 2012 (cite: Til12)]
- External data: Initial CO freeze-out temperature of 19 K  
  > "Based on the initial value of 19 K adopted by (cite: Qi11), a range of higher and lower values were explored." (4.3 The vertical structure of HD 163296) [from Qi et al. 2011 (cite: Qi11)]

## Processing

### Calibration

- pipeline or manual: CASA data reduction with self-calibration; WVR used for atmospheric phase  
  > "Data reduction was performed using the version 3.4 of the Common Astronomy Software Applications package (CASA)." (Observations description)
- casa version: CASA 3.4  
  > "Data reduction was performed using the version 3.4 of the Common Astronomy Software Applications package (CASA)." (Observations description)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune (amplitude); J1924-292 bandpass; J1733-130 gain  
  > "Amplitude calibration was done using Neptune, and quasars J$1924$$-292$ and J$1733$$-130$ were used to calibrate the bandpass and the complex gain fluctuations respectively." (Observations description)
- flux scale uncertainty: _not stated_
- self calibration: Applied using the continuum  
  > "We applied self-calibration using the continuum and we used the task CLEAN for imaging the self-calibrated visibilities." (Observations description)

### Imaging

- task: CLEAN  
  > "we used the task CLEAN for imaging the self-calibrated visibilities" (Observations description)
- deconvolver: _not stated_
- weighting robust: Briggs weighting (robust not stated)  
  > "Briggs weighting was used in both continuum and line images." (Observations description)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: Continuum from all line-free channels (ranges not given)  
  > "The continuum image was produced by combining all of the line-free channels." (Observations description)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.52'' x 0.38'' PA ~82 deg  
  > "providing a synthesized beam of $0.52\ensuremath{''} \times 0.38\ensuremath{''}$ at ${\rm P.A.}\!\sim\!\!82^\circ$" (Observations description)
- final rms: 0.5 mJy/beam continuum; 14 mJy/beam per channel  
  > "The achieved rms was 0.5 mJy beam$^{-1}$ for the continuum and 14 mJy beam$^{-1}$ for each CO channel map." (Observations description)

### Inherited from earlier work

- Initial MCFOST disk model and parameters  
  > "The initial disk model we use is based on (cite: Til12), in particular their favored model number three (see Table 6 in that paper)." (3.3 Modelling) [from Tilling et al. 2012 (cite: Til12)]
- MCFOST code description  
  > "(see (cite: Pin06; Pin09) for a more detailed description)" (3.3 Modelling) [from Pinte et al. 2006, 2009 (cite: Pin06; Pin09)]
- Tapered-edge surface density prescription  
  > "we consider a tapered-edge model for the surface density distribution (see (cite: And09))" (4.1 Dust and gas surface brightness distributions) [from Andrews et al. 2009 (cite: And09)]

### Not stated but needed to reproduce (our reading)

- Briggs robust value, cell size, image size, CLEAN masks/threshold
- Line-free channels used for continuum
- Self-calibration solution intervals and number of rounds
- Flux scale uncertainty and Neptune model used
- Fixed MCFOST parameters (disk mass, inner radius, flux of grids, stellar/disk inclination handling, number of photon packets)
- Velocity/channel width of the CO cube used for the models
- Exact procedure for matching model channel maps to data (no metric used)
- Whether data products are retrievable as calibrated measurement sets

## Analysis recipe

1. **Measure continuum disk size, geometry, flux**: Continuum image measured at 3 sigma; inclination from isophote shape; flux integrated above 3 sigma  
  > "The inclination angle is $i=45^\circ$, derived from the shape of the isophote contours" (3.1 Continuum emission)
   - software: CASA
   - assumption: distance 122 pc  
  > "at the adopted distance of $122\,{\rm pc}$ (cite: vda98)" (3.1 Continuum emission)
   - fitting: _not stated_
   - validation: Compared with Isella et al. 2007 and Qi et al. 2011 values  
  > "similar to the values reported by (cite: Ise07) and (cite: Qi11) using Submillimeter Array (SMA) observations at similar wavelengths" (3.1 Continuum emission)
2. **Radial surface brightness profiles of continuum and CO**: Azimuthal averaging in concentric elliptical annuli; two-component power law fit  
  > "The continuum surface brightness profile was calculated by azimuthally averaging the emission from concentric elliptical annuli from the central star." (3.1 Continuum emission)
   - fitting: Minimized chi^2 fit of power-law slopes  
  > "A minimized $\chi$$^{2}$ fitting was used to determine the best value of the power-law slopes." (3.1 Continuum emission)
   - validation: _not stated_
3. **Model radial profiles with MCFOST tapered-edge disk**: Explore R_c and gamma grid separately for continuum and CO, compare profiles, total flux, and SED  
  > "A range of $\gamma$ values from 0 to 2 were then explored to reproduce the steep decline in continuum and the shallower ${\rm CO}(3$–$2)$ surface brightness profile" (4.1.1 The outer disk, outside of Rc)
   - software: MCFOST
   - parameter: Rc 110-140 AU step 5; gamma 0-2 step 0.1  
  > "| $R_{c}$ \[AU\] | Critical Radius | $110-140$ | 5 | 125 |" (Table 1)
   - assumption: Astronomical silicates, size slope -3.5, max radius 1 mm; gas-to-dust 100; CO/H2 1e-4; LTE with Tgas=Tdust; Keplerian rotation  
  > "MCFOST assumes a constant gas-to-dust mass ratio of 100 throughout the disk (both radially and vertically)." (3.3 Modelling)
   - fitting: No minimisation scheme; grid explored by eye  
  > "No minimisation scheme was used, but we note that the continuum model and the line model (outside of $R_{\rm c}$ ) match all the data point within the error bars" (4.1.1 The outer disk, outside of Rc)
   - validation: Model total flux within 5% (continuum) and 1% (CO) of observed  
  > "reproducing the total integrated continuum flux well (5$\%$ larger than the observed integrated flux)" (4.1.1 The outer disk, outside of Rc)
4. **Explain central CO excess**: Tgas = 1.5 Tdust for R<80 AU, Tgas=Tdust elsewhere  
  > "the model CO surface brightness profile is a good match to the data when using $T_{\rm gas}=1.5T_{\rm dust}$ for a radius $<\!80\,{\rm AU}$" (4.1.2 The central region of the disk, inside of Rc)
   - software: MCFOST
   - fitting: _not stated_
   - validation: Convolved profile matches observed profile  
  > "This is the model shown in Fig. [2](#rad), where the resulting change in the brightness profile, after convolution by the synthesized beam, is shown to match the observed profile." (Discussion, The central region of the disk, inside of R_c)
5. **Constrain vertical structure with CO channel maps**: Vary CO freeze-out T, turbulent width, scale height H0 and flaring index; compare channel maps visually  
  > "we fine-tuned the CO model slightly by exploring a set of values of CO freeze-out temperature, non-thermal turbulence velocity, scale height and flaring power." (4.3 The vertical structure of HD 163296)
   - software: MCFOST
   - parameter: Tfreeze 10-40 K; dVturb 0-0.3 km/s; H0 0.03-0.1; beta 1.0-1.21  
  > "| $\beta$ | Flaring angle index | $1.0-1.21$ | 0.06 | 1.12 |" (Table 1)
   - fitting: not stated (qualitative best match)  
  > "In order to improve the match between modeled and observed channel maps, we fine-tuned the CO model slightly by exploring a set of values of CO freeze-out temperature, non-thermal turbulence velocity, scale height and flaring power." (Discussion, The vertical structure of HD 163296)
   - validation: Refined model checked against CO radial profile and SED; SED degraded in mid/far-IR  
  > "The final model keeps matching also the CO radial surface brightness profiles adequately." (4.3 The vertical structure of HD 163296)

## Software

- **CASA** 3.4: Data reduction, self-calibration, imaging  
  > "Data reduction was performed using the version 3.4 of the Common Astronomy Software Applications package (CASA)." (Observations description)
- **MCFOST** : 3D radiative transfer modelling of continuum and CO  
  > "the 3-dimensional radiative transfer code MCFOST was used to model the data presented in this work" (3.3 Modelling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust disk outer radius | 240 | not stated | AU | 1 | which corresponds to an outer dust disk radius of $R_{\rm out}\!\simeq240\,{\rm AU}$ |
| Continuum flux density at 850 um | 1.82 | 0.09 | Jy | 1 | $S_{850\mu m}$= 1.82 $\pm$0.09 Jy |
| Continuum characteristic radius | 125 | 5 | AU | 2 | equal to $125\pm5\,{\rm AU}$ from the central star |
| Continuum power-law slopes inner/outer | 1.03 / 4.7 | 0.04 / 0.2 | dimensionless | 2 | changing from a power-law slope of $1.03\pm0.04$ to a very steep decline of $4.7\pm0.2$ |
| CO outer radius | 575 | not stated | AU | 1 | the outer radius extends to $R_{\rm out}\!\simeq575\,{\rm AU}$ |
| CO integrated intensity | 100.30 | 0.13 | Jy km/s | 1 | $100.30\pm0.13$ Jy km s$^{-1}$ |
| Continuum disk inclination / PA | 45 / 137 | not stated | deg | 1 | The major axis position angle is 137$\ensuremath{^\circ}$. |
| Best-fit CO freeze-out temperature | 20 | not stated | K | 5 | The best match is obtained for $20\,{\rm K}$ |
| Best scale height H0 at 1 AU | 0.07 | not stated | AU | 5 | A good match is obtained for a scale height of $0.07\,{\rm AU}$ (at $1\,{\rm AU}$ radius), and a flaring power of 1.12. |
| Best turbulent velocity | 0.1 | not stated | km/s | 5 | The best match is obtained for $0.1\,{\rm km}~{\rm s ^{-1}}$. |

## Qualitative findings

- CO channel maps resolve the front and back surfaces of a flared Keplerian disk  
  > "showing the back- and the front-side of a flared disk" (abstract)
- Gas disk is more than twice the size of the dust disk  
  > "The gaseous disk is more than two times larger than the dust disk" (abstract)

## Claim tuples

- H: Do dust and gas share the same radial structure? | E: Fit surface brightness profiles and tapered-edge MCFOST models | R: Continuum needs gamma<0.1, CO needs 0.8-0.9, same Rc ~125 AU | F: Dust disk has sharper outer edge; tapered-edge prescription must be modified; grain growth and inward migration proposed | **supported**
- H: Is the vertical structure of the CO disk resolved and consistent with earlier models? | E: Compare CO channel maps with MCFOST grid | R: Best H0=0.07 AU, beta=1.12, freeze-out 20 K | F: Gas disk slightly thicker than Tilling et al. model; CO freeze-out in midplane improves fit | **supported**

## Reasoning

- Why this data: High angular resolution and sensitivity of ALMA needed to determine unique disk structure  
  > "Determining unique solutions to the underlying disk structure clearly benefits from having high-angular resolution, good image fidelity and high-sensitivity." (Introduction)
- Why this method: _not stated_
- Alternative: gamma near 1.0 from earlier studies ruled out for continuum by the new data  
  > "Those values are ruled out for the continuum by the higher angular resolution data reported here." (4.1.1 The outer disk, outside of Rc)
- How they decided it was enough: _not stated_
- Limitation (authors): Thicker disk fitting CO degrades SED in mid/far-IR  
  > "it is degraded in the mid- and far-infrared" (4.3 The vertical structure of HD 163296)
- Limitation (authors): No minimisation scheme used for model fits  
  > "No minimisation scheme was used" (4.1.1 The outer disk, outside of Rc)
- Caveat (inferred, ours): Model parameter selection by eye without chi^2 or uncertainties
- Caveat (inferred, ours): Tgas=Tdust and constant gas-to-dust ratio are strong assumptions
- Caveat (inferred, ours): Parameter degeneracies (H0, beta, turbulence, freeze-out) not explored
- Caveat (inferred, ours): Distance and inclination fixed from continuum

## Reproducibility

- Data public (paper): ALMA science verification data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.000010.SV." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CLEAN parameters
- Missing: Self-cal details
- Missing: Full MCFOST input file
- Data volume (inferred): ~tens of GB (SV data, 5 execution blocks, 4 spw)
- Score (inferred): 3/5, Public SV data and clear measurements, but imaging parameters and MCFOST inputs are underspecified and model fitting is manual.
- Rediscovery candidate: no, Imaging recipe incomplete and the modelling is by-eye tuning, though continuum/CO profile measurements are numeric.

## Links

- Method: Pinte et al. 2006, 2009 (cite: Pin06; Pin09) (MCFOST description)
- Method: Tilling et al. 2012 (cite: Til12) (Initial disk model)
- Companion: Mathews et al. 2013 submitted (CO freeze-out in HD 163296)
- Related: ALMA Science Verification
- Related: GASPS

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.000010.SV"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00010.SV"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 54,
  "rate": 0.72
 },
 "evidence_ok": true
}
```
