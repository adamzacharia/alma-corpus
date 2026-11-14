# Hot methanol from the inner region of the HH 212 protostellar system

`2016A&A...595L...4L` | Astronomy and Astrophysics 2016 | first author: Leurini, S. | arXiv: 1610.05322 | DOI: 10.1051/0004-6361/201629460

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry
- Question: What do high-excitation CH3OH lines reveal about the kinematics and nature (disk, jet/outflow, disk wind) of the inner ~100 AU of the Class 0 system HH 212?  
  > "we further exploit ALMA Band 7 data (cite: 2014A&A...568L...5C) to investigate the inner 100 AU of the HH 212 system through a survey of methanol (CH$_3$OH) high-energy lines" (Introduction)
- Target **HH 212-MM1**: coordinates RA(J2000) 05h43m51.41s, Dec -01d02m53.17s (continuum peak)  
  > "$\alpha({\rm J2000})$ = 05$^h$ 43$^m$ 51$s$41, $\delta({\rm J2000})$ = –01$\ensuremath{^\circ}$ 02$\ensuremath{'}$ 53$\ensuremath{''}$17" (Observations); "HH 212 is a strikingly bright and symmetric bipolar jet from a Class 0 source at a distance of 450 pc" (Introduction); z/distance 450 pc  
  > "$\alpha({\rm J2000})$ = 05$^h$ 43$^m$ 51$s$41, $\delta({\rm J2000})$ = –01$\ensuremath{^\circ}$ 02$\ensuremath{'}$ 53$\ensuremath{''}$17" (Observations); "HH 212 is a strikingly bright and symmetric bipolar jet from a Class 0 source at a distance of 450 pc" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.000647.S
- bands: Band 7 (cycle 0)  
  > "HH 212 was observed in Band 7 during the cycle 0 phase of ALMA." (Observations)
- frequencies and spectral setup: 333.7–337.4 GHz and 345.6–349.3 GHz, 488 kHz resolution (0.42–0.44 km/s)  
  > "The data cover the frequencies 333.7–337.4 GHz and 345.6–349.3 GHz with a spectral resolution of 488 kHz (corresponding to 0.42–0.44 km s$^{-1}$)." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: clean-beam FWHM 0.6"x0.5" (PA ~40 deg)  
  > "The continuum-subtracted images have a typical clean-beam FWHM of $0.6\ensuremath{''}\times0.5\ensuremath{''}$ (PA $\simeq$ 40$\ensuremath{^\circ}$)" (Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 3 mJy/beam per 488 kHz channel  
  > "an rms noise level of 3 mJy beam$^{-1}$ in the 488 kHz channel" (Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CH3OH 7_1-6_1 A, vt=0 (335582.017 MHz)
- Line: CH3OH 12_-1-12_0 A, vt=0 (336865.149 MHz)
- Line: CH3OH 14_-1-14_0 A, vt=0 (349106.997 MHz)
- Line: C17O 2-1 (not stated)
- External data: Spectroscopic parameters of CH3OH from JPL database  
  > "the spectroscopic parameters from the Jet Propulsion Laboratory (JPL) molecular database (cite: pickett_JMolSpectrosc_60_883_1998)" (Results) [from (cite: pickett_JMolSpectrosc_60_883_1998)]
- External data: Bolometric luminosity ~14 Lsun  
  > "The bolometric luminosity of HH 212 is $\sim14$ $L_\odot$ (cite: 1992A&A...265..726Z)." (Results) [from (cite: 1992A&A...265..726Z)]
- External data: Systemic velocity +1.7 km/s  
  > "we assume a systemic velocity, $V_{\rm sys}$, of +1.7 km s$^{-1}$ (cite: 2014ApJ...786..114L)" (CH3OH kinematics) [from (cite: 2014ApJ...786..114L)]
- External data: Inclination ~4 deg to the plane of the sky  
  > "an inclination angle of $\sim4^\circ$ to the plane of the sky (cite: 1998ApJ...507L..79C)" (footnote) [from (cite: 1998ApJ...507L..79C)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
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
- continuum subtraction: continuum-subtracted images used  
  > "The continuum-subtracted images have a typical clean-beam FWHM" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observations, calibration and imaging details  
  > "We refer to these papers for further details and give here a short summary of the observations." (Observations) [from (cite: 2014A&A...568L...5C), (cite: 2015A&A...581A..85P), (cite: 2016A&A...586L...3C)]
- Continuum peak position  
  > "Positions are given with respect to the continuum peak" (Observations) [from (cite: 2014ApJ...786..114L)]
- Dust temperature estimate  
  > "Using Eq. 1 of (cite: 2000A&A...355.1129C), the dust temperature would be about 250 K at a radius of 10 AU" (Results) [from (cite: 2000A&A...355.1129C)]
- Launching radius formula  
  > "we can estimate its launching radius from Eq. 5 of (cite: 2003ApJ...590L.107A)" (Discussion) [from (cite: 2003ApJ...590L.107A)]

### Not stated but needed to reproduce (our reading)

- Calibration pipeline, CASA version, calibrators
- Imaging parameters (weighting, robust, cell, size) and continuum channels
- Priors and parameter ranges for the MCWeeds fit
- Which channels/lines were included in the fit and how blended lines were treated
- MCWeeds is unpublished (in prep.)
- Velocity channel widths and uv-fit details for kinematics

## Analysis recipe

1. **Identify CH3OH lines**: Identified 19 CH3OH lines in the spectrum at the continuum peak using Weeds and JPL parameters  
  > "We identified 19 lines of CH$_3$OH in the 8 GHz bandwidth spectrum towards the 0.9 mm continuum peak" (Results)
   - software: Weeds
   - fitting: _not stated_
   - validation: _not stated_
2. **Size of emitting region**: Elliptical Gaussian uv-fit of visibilities averaged over ±2 km/s around peak of three strong lines  
  > "We averaged the visibilities over the range $\pm2$ km s$^{-1}$ from the peak velocity of the $7_1-6_1$-$A$, $\varv_t=0$, $12_{-1}  - 12_0$-$A$, $\varv_t=0$, and $14_{-1} - 14_0$-$A$, $\varv_t=0$ lines" (High-excitation CH3OH emission)
   - software: GILDAS
   - assumption: Elliptical Gaussian spatial distribution  
  > "assuming an elliptical Gaussian distribution in space using the GILDAS $uv$-fit task" (High-excitation CH3OH emission)
   - fitting: _not stated_
   - validation: Compared with CH3CHO size from same dataset; lines similar peak intensity so S/N bias unlikely  
  > "Since the analysed lines are the strongest of the dataset and have similar peak intensities, we believe that these results are not biased by different signal-to-noise levels." (High-excitation CH3OH emission)
3. **LTE fit of full spectrum**: Simultaneous LTE fit of all CH3OH transitions with MCWeeds (Weeds+PyMC) using MCMC  
  > "We fit all CH$_3$OH transitions using the Markov chain Monte Carlo method." (High-excitation CH3OH emission)
   - software: Weeds, MCWeeds, PyMC
   - parameter: 100000 iterations, burn-in 20000, thinning 50; source size fixed 0.2"  
  > "We used 100 000 iterations following a burn-in period of 20 000 with a thinning factor of 50." (High-excitation CH3OH emission)
   - assumption: LTE  
  > "Weeds generates synthetic spectra of a given molecule assuming local thermodynamic equilibrium (LTE)" (High-excitation CH3OH emission)
   - fitting: MCMC, 95% HPD intervals  
  > "The best fit results and the 95% highest probability density (HPD) interval ranges are given in Table [3](#tab_lte)" (High-excitation CH3OH emission)
   - validation: Synthetic spectrum compared with data; two low-energy lines underestimated  
  > "The fit reproduces all lines except the $2_{-2} - 3_{-1}$-$A$, $\varv_t=0$ and $5_{\pm4} - 6_{\pm3}$-$A$, $\varv_t=0$ transitions which are underestimated by the model." (High-excitation CH3OH emission)
4. **Velocity-channel centroids and kinematics**: uv-fits of elliptical Gaussians per velocity channel for two lines; centroids compared with C17O  
  > "we performed fits of the visibilities for various velocity channels for the $7_1 - 6_1$-$A$, $\varv_t=0$ and $12_{-1}-12_0$-$A$, $\varv_t=0$ lines" (CH3OH kinematics)
   - software: GILDAS
   - assumption: Vsys = +1.7 km/s  
  > "we assume a systemic velocity, $V_{\rm sys}$, of +1.7 km s$^{-1}$" (CH3OH kinematics)
   - fitting: _not stated_
   - validation: _not stated_
5. **Disk-wind launching radius**: Eq. 5 of Anderson et al. 2003 with poloidal 30 km/s and toroidal 1 km/s  
  > "Assuming a poloidal velocity of 30 km s$^{-1}$ and a toroidal velocity of $1$ km s$^{-1}$" (Discussion)
   - assumption: Axisymmetric, steady, magneto-centrifugal disk wind  
  > "If CH$_3$OH is associated with an axisymmetric, steady, magneto-centrifugally accelerated disk wind" (Discussion)
   - fitting: _not stated_
   - validation: Consistent with disk wind models of water in Class 0 YSOs  
  > "consistent with disk wind models of water in Class 0 YSOs (cite: 2016A&A...585A..74Y)" (Discussion)

## Software

- **Weeds** : Line identification and LTE synthetic spectra  
  > "using the Weeds package (cite: 2011A&A...526A..47M)" (Results)
- **MCWeeds** : Interface between Weeds and PyMC for MCMC fitting  
  > "we used MCWeeds (Giannetti et al. in prep.), an external interface between Weeds and PyMC" (High-excitation CH3OH emission)
- **PyMC** : Bayesian models and MCMC  
  > "an external interface between Weeds and PyMC (cite: Patil+10_jstatsoft35_1), to implement Bayesian statistical models and fitting algorithms" (High-excitation CH3OH emission)
- **GILDAS** : uv-fit of visibilities  
  > "using the GILDAS $uv$-fit task" (High-excitation CH3OH emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3OH LTE temperature | 295 | 95% HPD 290–300 | K | 3 | Temperature (K)                      / 295      / 290–300 |
| CH3OH column density | 3.1e17 | 95% HPD 3.0–3.2e17 | cm^-2 | 3 | Column density ($10^{17}$ cm$^{-2}$) / 3.1      / 3.0–3.2 |
| Line width | 4.6 | 95% HPD 4.5–4.7 | km/s | 3 | Line-width (km s$^{-1}$)             / 4.6      / 4.5–4.7 |
| Peak velocity | 2.1 | 95% HPD 2.0–2.1 | km/s | 3 | Peak velocity (km s$^{-1}$)          / 2.1      / 2.0–2.1 |
| Optical depth | ≤0.4 | not stated | dimensionless | 3 | CH$_3$OH is optically thin ($\tau\le0.4$) |
| uv-fit size of 7_1-6_1 A vt=0 | 0.26"x0.19", PA 36 deg | not stated | arcsec | 2 | $7_1    - 6_1$-$A$, $\varv_t=0$ / -12 / +0 / $0.26\ensuremath{''}\times0.19\ensuremath{''}$ / $36^\circ$ |
| uv-fit size of 12_-1-12_0 A vt=0 | 0.23"x0.16", PA 32 deg | not stated | arcsec | 2 | $12_{-1}  - 12_0$-$A$, $\varv_t=0$ / -19 / +0 / $0.23\ensuremath{''}\times0.16\ensuremath{''}$ / $32^\circ$ |
| uv-fit size of 14_-1-14_0 A vt=0 | 0.20"x0.14", PA 16 deg | not stated | arcsec | 2 | $14_{-1} - 14_0$-$A$, $\varv_t=0$ / -7 / +12 / $0.20\ensuremath{''}\times0.14\ensuremath{''}$ / $16^\circ$ |
| Disk-wind launching radius | ~1 | not stated | AU | 5 | the launching radius is $\sim1$ AU |

## Qualitative findings

- CH3OH emission is compact and elongated along the jet axis, more compact than C17O, with velocity increasing away from the protostar, so not associated with a Keplerian disk  
  > "CH$_3$OH is not associated with a Keplerian disk or rotating-infalling cavity, and it is more likely associated with an outflow/jet system." (CH3OH kinematics)

## Claim tuples

- H: Does hot CH3OH trace the Keplerian disk of HH 212-MM1? | E: Compared velocity-channel centroids of CH3OH lines with C17O | R: CH3OH centroids shift symmetrically about the jet axis, rotation velocity increases outward | F: CH3OH is not in a Keplerian disk but in an outflow/jet or disk wind | **supported**
- H: How hot and compact is the CH3OH gas? | E: uv-fits and LTE MCMC fit of 19 lines | R: size 0.2–0.3" (<135 AU diameter), T~295 K, N~3e17 cm^-2 | F: Hot compact gas, likely warmer than dust, suggesting a disk wind base | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Association of CH3OH with outflow cavities traced by C17O is ruled out by its smaller size  
  > "This difference seems to rule out the association of CH$_3$OH with the cavities of the outflow traced by C$^{17}$O." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Source size from three low-energy lines; higher-energy lines likely more compact, affecting column density; higher resolution needed  
  > "We note that a smaller source size would result in a similar temperature and a larger column density in the LTE fit since lines are optically thin." (Results)
- Caveat (inferred, ours): Source size fixed at 0.2" for the LTE fit, so column density is size-dependent
- Caveat (inferred, ours): Beam (~0.5") larger than emitting region; centroid kinematics at sub-beam scales sensitive to S/N
- Caveat (inferred, ours): Disk wind interpretation is speculative
- Caveat (inferred, ours): Uncertainties are statistical only

## Reproducibility

- Data public (paper): Cycle 0 project 2011.0.000647.S cited in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.000647.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: MCWeeds code and priors
- Missing: Calibration/imaging parameters (in earlier papers)
- Missing: Channel-level centroid values
- Data volume (inferred): ~10-30 GB raw Cycle 0 Band 7 data
- Score (inferred): 3/5, Public data and clear approach, but processing is deferred to earlier papers and the fitting tool is unpublished.
- Rediscovery candidate: no, Fitting code unpublished and imaging settings not given.

## Links

- Method: (cite: 2011A&A...526A..47M) (Weeds package)
- Companion: (cite: 2014A&A...568L...5C) (Original Band 7 dataset)
- Companion: (cite: 2016A&A...586L...3C) (HDO and CH3CHO from same data)
- Companion: (cite: 2015A&A...581A..85P) (SiO/SO jet and outflow from same data)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
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
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 38,
  "rate": 0.487
 },
 "evidence_ok": true
}
```
