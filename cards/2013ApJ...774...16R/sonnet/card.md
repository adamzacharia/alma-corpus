# A Spatially Resolved Vertical Temperature Gradient in the HD 163296 Disk

`2013ApJ...774...16R` | The Astrophysical Journal 2013 | first author: Rosenfeld, Katherine A. | arXiv: 1306.6475 | DOI: 10.1088/0004-637X/774/1/16

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Can the spatial asymmetry of CO lines in the HD 163296 disk be explained by a vertical temperature gradient, and are the data sensitive to sub-Keplerian gas velocities?  
  > "We associate this behavior as the direct signature of a vertical temperature gradient and layered molecular structure in the disk." (abstract)
- Target **HD 163296**: coordinates RA 17h56m21.287s, Dec -21d57m22.39s (J2000)  
  > "HD 163296 ($\alpha = 17^{\rm h} 56^{\rm m} 21.287s$, $\delta = -21\ensuremath{^\circ}57\ensuremath{'}22.39\ensuremath{''}$, J2000)" (2 Observations and Data Reduction); "its *Hipparcos* parallax indicates it is nearby (cite: vandenancker98)" (Introduction); z/distance _not stated_; distance from Hipparcos parallax (cite: vandenancker98)  
  > "HD 163296 ($\alpha = 17^{\rm h} 56^{\rm m} 21.287s$, $\delta = -21\ensuremath{^\circ}57\ensuremath{'}22.39\ensuremath{''}$, J2000)" (2 Observations and Data Reduction); "its *Hipparcos* parallax indicates it is nearby (cite: vandenancker98)" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00010.SV
- bands: Band 6 and Band 7  
  > "was observed by ALMA in Band 6 and Band 7 as part of its commissioning and science verification (SV) program." (2 Observations and Data Reduction)
- frequencies and spectral setup: Band 6: four SpWs (13CO+C18O in SpW1, 12CO 2-1 in SpW2, continuum at 217 and 234 GHz); Band 7: continuum at 360 and 347 GHz, HCO+ 4-3 in SpW1, 12CO 3-2 in SpW2  
  > "SpWIDs #0 and #3 were centered at 360 and 347 GHz for continuum, HCO$^+$ $J$=4$-$3 at 356.734 GHz was detected in SpWID #1" (2 Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: 24 12 m antennas (Band 6)  
  > "The Band 6 observations were taken using 24 of the ALMA 12 m antennas on 2012 June 9, June 23, and July 7" (2 Observations and Data Reduction)
- configurations: _not stated_
- baselines: 20 to 400 m  
  > "The baselines spanned a range of 20 to 400 m." (2 Observations and Data Reduction)
- angular resolution: Beams 0.65x0.42 arcsec (12CO 3-2), 0.81x0.66 (12CO 2-1), 0.87x0.70 (13CO, C18O)  
  > "| Beam | $0.65\ensuremath{''}\times0.42\ensuremath{''}$ | $0.81\ensuremath{''}\times0.66\ensuremath{''}$" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: RMS 0.022, 0.016, 0.009, 0.008 Jy/beam per channel (12CO 3-2, 12CO 2-1, 13CO, C18O)  
  > "| RMS \[Jy beam$^{-1}$\] | 0.022 | 0.016 | 0.009 | 0.008 |" (Table 1)
- time on source: Band 6: 84 min; Band 7: 140 min  
  > "for a total on-source time of 84 minutes (including latency)" (2 Observations and Data Reduction); "The total on-source time was 140 minutes." (2 Observations and Data Reduction)
- observing dates: Band 6: 2012 June 9, June 23, July 7; Band 7: 2012 June 9, 11, 22, July 6  
  > "HD 163296 was observed in Band 7 on 2012 June 9, Jun 11, June 22, and July 6 with the same antenna configuration." (2 Observations and Data Reduction)
- pi or archival as stated: ALMA Science Verification data, publicly released  
  > "The raw and calibrated visibility data were publicly released through the science portal" (2 Observations and Data Reduction)
- Line: 12CO J=3-2 (345.796 GHz)
- Line: 12CO J=2-1 (230.538 GHz)
- Line: 13CO J=2-1 (220.399 GHz)
- Line: C18O J=2-1 (219.560 GHz)
- External data: ISM isotopologue ratios 12CO/13CO=69±6 and 12CO/C18O=557±30  
  > "$^{12}$CO/$^{13}$CO$=69\pm6$ and $^{12}$CO/C$^{18}$O$=557\pm30$" (4.2.2 A Hydrostatic Model Structure) [from Wilson 1999 (cite: wilson99)]
- External data: Stellar mass fixed from literature  
  > "the stellar mass (cite: natta04), source distance (cite: vandenancker98)" (4.2 Physical Model Analysis) [from (cite: natta04)]
- External data: Molecular data for CO from LAMDA  
  > "molecular data from the LAMDA database (cite: schoier05; yang10)" (4.2 Physical Model Analysis) [from (cite: schoier05; yang10)]
- External data: Previous SMA line intensities used for comparison  
  > "The reported line intensities agree with previous measurements by the SMA (cite: qi11)" (3 Results) [from (cite: qi11)]

## Processing

### Calibration

- pipeline or manual: Started from SV-team calibrated measurement set; self-calibrated and continuum subtracted in CASA  
  > "We started with the calibrated measurement set and used the CASA software package (cite: mcmullin07) to produce self-calibrated and continuum subtracted spectral visibilities" (2 Observations and Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated SV measurement set used as starting point  
  > "We started with the calibrated measurement set" (2 Observations and Data Reduction)
- flux calibrator: Band 6: Juno, Neptune, Mars; Band 7: Juno (June 9) and Neptune; bandpass J1924-292; phase J1733-130  
  > "The flux calibrator for each of the nights was Juno, Neptune, and Mars, respectively, and the bandpass solution was generated from observations of the quasar J1924-292." (2 Observations and Data Reduction)
- flux scale uncertainty: 10% systematic  
  > "within the 10% systematic uncertainty estimated for the absolute calibration of the visibility amplitudes" (3 Results)
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN (Hogbom)  
  > "We generated these synthesized images using the CASA implementation of the CLEAN algorithm (cite: hogbom74) with natural weighting." (3 Results)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "with natural weighting" (3 Results)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Per-channel mask from Keplerian pattern convolved with Gaussian sigma=0.7 arcsec; extra iterations unmasked  
  > "This region was then convolved with a fixed Gaussian kernel ($\sigma = 0.7\ensuremath{''}$) to broaden the mask" (3 Results)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Visibilities regridded to 0.34 km/s channels for comparison; data Hanning smoothed  
  > "the visibilities have been regridded onto the same 0.34 km s$^{-1}$ wide channels" (3 Results)
- final beam: see Table 1  
  > "| P.A. | $-87.3\ensuremath{^\circ}$ | $75.8\ensuremath{^\circ}$ | $76.8\ensuremath{^\circ}$ | $76.8\ensuremath{^\circ}$ |" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Calibration and imaging scripts/reference maps from ALMA SV team  
  > "accompanied by a set of detailed calibration and imaging scripts provided by the ALMA SV team" (2 Observations and Data Reduction) [from ALMA SV team]
- Disk density/temperature formalism  
  > "Following the formalism explained by (cite: andrews12), axisymmetric density and temperature structures are defined" (4.2 Physical Model Analysis) [from (cite: andrews12)]
- Temperature parameterization modified from Dartois et al.  
  > "a slightly modified version of the parameterization introduced by (cite: dartois03)" (4.2.2 A Hydrostatic Model Structure) [from (cite: dartois03)]
- Hanning smoothing to mimic ALMA pipeline  
  > "smooth using the Hanning algorithm in the spectral dimension with a three channel kernel to mimic the ALMA pipeline (cite: lundgren12)" (4.2 Physical Model Analysis) [from (cite: lundgren12)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Self-calibration solution intervals and reference antenna
- Number of CLEAN iterations/threshold, cell and image size
- Line-free channels for continuum subtraction
- Stellar mass and distance values adopted
- Exact model grid and LIME settings (photons, grid points)
- Model visibility sampling and chi2 values
- How the 'central 49 channels' and mask parameters (phase offset, systemic velocity) were chosen

## Analysis recipe

1. **Image line cubes**: CLEAN with natural weighting and per-channel Keplerian-pattern masks  
  > "we developed a CLEAN mask based on the emission pattern expected from a disk in Keplerian rotation" (3 Results)
   - software: CASA
   - parameter: mask smoothing sigma = 0.7 arcsec  
  > "convolved with a fixed Gaussian kernel ($\sigma = 0.7\ensuremath{''}$)" (3 Results)
   - fitting: _not stated_
   - validation: SNR per channel improves by ~2-3 vs SV reference maps; intensities agree with SMA within 10%  
  > "the signal-to-noise ratio per channel improves by a factor of $\sim$2–3" (3 Results)
2. **Toy double-cone model of emitting surface**: Rotating double cone with opening angle psi; compare isovelocity contours with channel maps  
  > "The toy model that we propose is a differentially rotating double cone, oriented along the $z$ axis with an opening angle $\psi \in (0,\pi/2)$" (4.1 A Toy Model)
   - parameter: psi ~15 deg  
  > "double cone structure with $\psi \sim 15^\circ$" (4.1 A Toy Model)
   - assumption: Keplerian rotation, no v_z  
  > "if this near cone is in circular, Keplerian rotation" (4.1 A Toy Model)
   - fitting: qualitative comparison  
  > "Qualitatively, this model does an excellent job of producing both the morphological and brightness asymmetries noted in §[3](#sec:results)." (4.2.1 A Pedagogical Structure)
   - validation: visual overlay on channel maps  
  > "Figure [\[fig:cone_chmaps\]](#fig:cone_chmaps) shows the velocity pattern of this toy model overlaid on the regridded channel maps" (4.1 A Toy Model)
3. **Non-LTE disk models (pedagogical and hydrostatic)**: Parametric temperature structure, hydrostatic density, LIME non-LTE radiative transfer, Hanning smoothing, model visibilities  
  > "we calculate the CO level populations using the non-LTE molecular excitation and radiative transfer package LIME (cite: brinch10)" (4.2 Physical Model Analysis)
   - software: LIME, CASA
   - parameter: Mgas=0.09 Msun, gamma=0.8, rc=150 AU, Tfrz=19 K, sigma_s=9e20 cm^-2, Tm=19K (r/155AU)^-0.3  
  > "We normalize the density so that the total mass of the gas disk is $M_{\rm gas} = 0.09$ M$_\odot$, and assume $\gamma = 0.8$ and $r_c=150$ AU." (4.2.2 A Hydrostatic Model Structure)
   - parameter: xi=0.01 km/s, i=224 deg, PA=312 deg  
  > "We assume a constant turbulent velocity width, $\xi=0.01$ km s$^{-1}$, and disk inclination, $i=224^\circ$." (4.2 Physical Model Analysis)
   - assumption: 80% of gas is H2; constant CO:H2 abundance; CO depleted by 1e8 below freezeout; ISM isotopologue ratios  
  > "we assume that 80% of the gas (by number; $\mu = 2.37$) is composed of molecular hydrogen" (4.2 Physical Model Analysis)
   - fitting: Hand-tuned, not an optimized fit; chi2 of complex visibilities and inspection of CLEANed maps  
  > "We evaluate the model fit through a $\chi^2$ statistic of the complex visibilities and also by inspection of CLEANed channel maps" (4.2 Physical Model Analysis)
   - validation: Residual channel maps and integrated line profiles; admits models are degenerate  
  > "the exact structures we present are neither unique nor necessarily optimal" (4.2 Physical Model Analysis)
4. **Test sensitivity to gas velocity field**: Models with velocity from vertical geometry, pressure gradient, self-gravity separately and combined; compare to Keplerian  
  > "In order to disambiguate these three effects, we will consider separately the three force terms in Equation [\[eq:fullF\]](#eq:fullF) that determine $v$" (4.3 A Closer Look at the Gas Velocities)
   - software: LIME
   - parameter: LIME only for level populations; images by own ray tracing on interpolated 2D grid; Poisson equation on fixed grid  
  > "for these models we only used LIME to calculate the non-LTE level populations." (4.3 A Closer Look at the Gas Velocities)
   - assumption: circular orbits; self-gravity omitted from hydrostatic density  
  > "throughout our analysis we have only considered circular orbits" (4.3 A Closer Look at the Gas Velocities)
   - fitting: _not stated_
   - validation: Differences significant at >=3 sigma across many channels  
  > "The impact of these changes to the velocity field are significant at the $\gtrsim 3 \sigma$ level across many channels." (4.3 A Closer Look at the Gas Velocities)

## Software

- **CASA** : self-calibration, continuum subtraction, CLEAN imaging  
  > "used the CASA software package (cite: mcmullin07) to produce self-calibrated and continuum subtracted spectral visibilities" (2 Observations and Data Reduction)
- **LIME** : non-LTE level populations and channel maps  
  > "non-LTE molecular excitation and radiative transfer package LIME (cite: brinch10)" (4.2 Physical Model Analysis)
- **LAMDA database** : molecular data for CO  
  > "molecular data from the LAMDA database (cite: schoier05; yang10)" (4.2 Physical Model Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 12CO 3-2 integrated intensity | 109 | ±11 | Jy km/s | 1 | / Integrated intensity \[Jy km s$^{-1}$\] / $109\pm11$ / $46\pm5$ / $18\pm2$ / $5.8\pm 0.6$ / |
| 12CO 2-1 integrated intensity | 46 | ±5 | Jy km/s | 1 | / Integrated intensity \[Jy km s$^{-1}$\] / $109\pm11$ / $46\pm5$ / $18\pm2$ / $5.8\pm 0.6$ / |
| 13CO 2-1 integrated intensity | 18 | ±2 | Jy km/s | 1 | / Integrated intensity \[Jy km s$^{-1}$\] / $109\pm11$ / $46\pm5$ / $18\pm2$ / $5.8\pm 0.6$ / |
| C18O 2-1 integrated intensity | 5.8 | ±0.6 | Jy km/s | 1 | / Integrated intensity \[Jy km s$^{-1}$\] / $109\pm11$ / $46\pm5$ / $18\pm2$ / $5.8\pm 0.6$ / |
| Cone angle of tau=1 surface | ~15 | not stated | deg | 2 | make an angle of $\sim 15^\circ$ with respect to the disk midplane |
| Systemic velocity of 12CO 3-2 (LSRK, incorrect frame in SV Band 7) | 6.99 | not stated | km/s | 0 | is $6.99$ km s$^{-1}$ |
| Velocity-field difference distinguishable by data | >~5 | not stated | percent | 4 | a fractional difference in the bulk gas velocity field of $\gtrsim 5$% |

## Qualitative findings

- 12CO 3-2 emission is asymmetric across the major axis; 12CO 2-1 less so; 13CO and C18O symmetric  
  > "No asymmetries are observed for the rarer $^{13}$CO and C$^{18}$O isotopologues." (Summary)
- Coarse spectral resolution of Band 6 mutes the 12CO 2-1 asymmetry  
  > "The muted asymmetry of the $^{12}$CO $J$=2$-$1 emission can be attributed to the larger beam size and coarser spectral resolution of the Band 6 observations" (5 Discussion)

## Claim tuples

- H: The 12CO 3-2 asymmetry reflects a vertical temperature gradient | E: Toy double cone and non-LTE hydrostatic disk models compared to channel maps | R: Models with cold midplane and warm atmosphere reproduce morphology; isothermal model does not | F: Asymmetry is a resolved signature of a vertical temperature gradient | **supported**
- H: Data are sensitive to sub-Keplerian velocity corrections | E: Models with only the velocity field varied | R: Vertical geometry and pressure gradient effects significant at >=3 sigma | F: Data distinguish models differing by >~5% in velocity; self-gravity is less important | **supported**
- H: Disk absolute orientation can be determined | E: Use asymmetry sense and compare to jet | R: Inclination and PA differ by 180 deg from earlier work, consistent with jet | F: Absolute orientation resolved | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Non-LTE models with physically self-consistent structure needed for sensitive data  
  > "These observations demonstrate the necessity of more sophisticated, physically self-consistent approaches" (5 Discussion)
- Alternative: Vertically isothermal disk fails to reproduce asymmetry  
  > "the morphology of the line is essentially symmetric across the major axis" (4.2.1 A Pedagogical Structure)
- How they decided it was enough: _not stated_
- Limitation (authors): Models are degenerate, not unique or optimal; systematic residuals at large radii  
  > "the exact structures we present are neither unique nor necessarily optimal" (4.2 Physical Model Analysis)
- Limitation (authors): Band 7 sky frequency in SV measurement set incorrect  
  > "The transformation to the absolute sky frequency in the Band 7 measurement set provided by the SV team is incorrect." (Footnote 2)
- Caveat (inferred, ours): Models hand-tuned with no parameter uncertainties
- Caveat (inferred, ours): Disk models may not be unique; no quantitative chi2 reported
- Caveat (inferred, ours): Inclination/PA flip relies on subtle asymmetry
- Caveat (inferred, ours): Stellar mass fixed from literature affects velocity tests

## Reproducibility

- Data public (paper): Raw and calibrated SV data publicly released  
  > "The raw and calibrated visibility data were publicly released through the science portal" (2 Observations and Data Reduction)
- Products in archive: _not stated_
- Missing: Model code (custom ray tracer, Poisson solver) not released
- Missing: Adopted stellar mass and distance values
- Missing: CASA version and imaging parameters
- Missing: Self-calibration details
- Data volume (inferred): ~10-50 GB (SV datasets, multiple EBs, Bands 6 and 7)
- Score (inferred): 3/5, Public data and detailed model parameterization, but custom code unreleased, many imaging/selfcal settings unstated, and fits are qualitative.
- Rediscovery candidate: no, Main results are qualitative morphology and hand-tuned models; few numeric answer keys beyond line fluxes.

## Links

- Method: Andrews et al. 2012 (cite: andrews12) (disk structure formalism)
- Method: Dartois et al. 2003 (cite: dartois03) (temperature parameterization)
- Method: Brinch & Hogerheijde 2010 (cite: brinch10) (LIME)
- Companion: Qi et al. 2011 (cite: qi11) (prior SMA model of the HD 163296 disk)
- Companion: Qi et al. 2013 (cite: qi13) (ALMA SV Band 6 continuum/molecular spectrum of HD 163296)
- Related: ALMA Science Verification

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
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
  "facts": 79,
  "stated": 57,
  "rate": 0.722
 },
 "evidence_ok": true
}
```
