# The close circumstellar environment of Betelgeuse. V. Rotation velocity and molecular envelope properties from ALMA

`2018A&A...609A..67K` | Astronomy and Astrophysics 2018 | first author: Kervella, Pierre | arXiv: 1711.07983 | DOI: 10.1051/0004-6361/201731761

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, stellar_physics
- Question: What is the rotation velocity of Betelgeuse and what are the properties of its close molecular envelope, as measured from high-resolution ALMA band 7 line emission?  
  > "We present here new spatially resolved observations of the close-in molecular envelope of Betelgeuse in the submillimeter domain using the most extended configuration of the ALMA array" (Introduction)
- Target **Betelgeuse**: coordinates _not stated_; z/distance parallax 4.51 ± 0.80 mas  
  > "the parallax $\pi = 4.51 \pm 0.80$ mas by" (3.3 Radial rotation velocity profile); distance from parallax from a cited work (citation not shown in text)  
  > "the parallax $\pi = 4.51 \pm 0.80$ mas by" (3.3 Radial rotation velocity profile)

## Data provenance

- ALMA projects: 2015.1.00206.S
- bands: Band 7 (275–373 GHz)  
  > "during cycle 3 in band 7 (275–373 GHz)" (2 Observations)
- frequencies and spectral setup: 5 spws centered 330.65, 332.55, 343.19, 345.15, 345.80 GHz; channel widths 0.85–1.69 km/s  
  > "| 2 | 343.19 | 1.88 | 0.85 |" (Table 1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: TE extended (0.056–16 km) and TC compact (0.013–1.2 km)  
  > "Observations were made in the extended configuration (hereafter TE, baseline lengths of 0.056 to 16 km)" (2 Observations)
- baselines: _not stated_
- angular resolution: 18 mas (TE), 190 mas (TC), 22 mas (TE+TC)  
  > "18 mas and 1.3 mJy, 190 mas and 1.7 mJy, 22 mas and 1 mJy, for the TE, TC, and TE+TC combined data, respectively" (2 Observations)
- max recoverable scale: 2 arcsec (TE); 8 arcsec (TC and combined)  
  > "The TE-only cubes are sensitive to emission on angular scales up to 2 arcseconds; the TC and combined cubes up to 8 arcseconds." (2 Observations)
- sensitivity: noise 1.3 mJy (TE), 1.7 mJy (TC), 1 mJy (TE+TC)  
  > "18 mas and 1.3 mJy, 190 mas and 1.7 mJy, 22 mas and 1 mJy, for the TE, TC, and TE+TC combined data, respectively" (2 Observations)
- time on source: TE 112 min; TC 38 min  
  > "on 16 Aug 2016, using 42 good antennas, for 38 min on target" (2 Observations)
- observing dates: TE: 6, 7, 9 Nov 2015; TC: 16 Aug 2016  
  > "on 6, 7, and 9 Nov 2015, using 47 good antennas, for a total of 112 minutes on target." (2 Observations)
- pi or archival as stated: _not stated_
- Line: 28SiO v=2 J=8-7 (342.50438 GHz)
- Line: 12CO v=0 J=3-2 (345.79599 GHz)
- Line: 28SiO v=1 J=8-7 (344.91633 GHz)
- Line: 29SiO v=0 J=8-7 (342.98085 GHz)
- Other facility **AAVSO**: visible light curve of Betelgeuse  
  > "We acknowledge with thanks the variable star observations from the AAVSO International Database contributed by observers worldwide and used in this research." (Acknowledgements)
- External data: Parallax 4.51 ± 0.80 mas used for radius, Keplerian velocity and rotation period  
  > "the parallax $\pi = 4.51 \pm 0.80$ mas by" (3.3 Radial rotation velocity profile) [from not shown in text (citation key stripped)]
- External data: Rest frequencies of lines  
  > "The rest frequencies are taken from the CDMS database ." (Table 2) [from CDMS database]

## Processing

### Calibration

- pipeline or manual: Standard ALMA procedures; self-calibration on continuum  
  > "Standard ALMA procedures were used for instrumentally derived calibration (system temperature measurements, water vapor radiometry, etc.), bandpass, flux scale, and phase reference calibration." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Continuum images from line-free channels used for self-calibration; solutions applied to all data in same configuration; 9 Nov 2015 TE data used as starting model for other TE epochs  
  > "We identified the line-free channels and used these to make continuum images for self-calibration, applying the solutions to all data in the same configuration." (2 Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: line-free continuum subtracted from full-resolution calibrated data  
  > "We subtracted the line-free continuum from the full-spectral-resolution, fully calibrated data and made image cubes of all spectral windows" (2 Observations)
- line free channels: _not stated_
- primary beam correction: applied to TC images (~16 arcsec FWHM)  
  > "we made TC images of comparable size, applying the primary beam correction." (2 Observations)
- array combination: TE, TC and combined cubes made  
  > "made image cubes of all spectral windows for the TE, TC, and combined data" (2 Observations)
- smoothing: _not stated_
- final beam: 18 mas (TE)  
  > "18 mas and 1.3 mJy" (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Continuum analysis and further observational details of the 9 Nov data, and astrometric analysis, given in earlier papers  
  > "were used for detailed continuum analysis (; also see that paper for more observational details) and astrometric analysis ." (2 Observations) [from earlier Betelgeuse ALMA papers (citations stripped)]
- Spherical thin molecular shell model  
  > "we model our ALMA observations using a spherical thin molecular shell of angular radius $R_\mathrm{shell}$ located above the spherical stellar photosphere" (3.2 Shell model) [from Following earlier works (citations stripped)]

### Not stated but needed to reproduce (our reading)

- Task, weighting, robust, cell and image size, deconvolver and masking for tclean
- CASA version
- Line-free channel ranges and self-cal solution intervals
- Flux calibrator and phase calibrator names (stripped)
- Exact procedure for velocity-map fitting and absorption compensation
- Fit region/radius range for the radial profile fit

## Analysis recipe

1. **Measure stellar continuum radius and brightness**: Measure I_star at disk center and equivalent uniform-disk R_star from integrated continuum flux in spw2 continuum image  
  > "we estimate $R_\mathrm{star}$ from the integrated continuum flux $I(r,\theta)$ and the surface brightness measured at the center of the disk $I_\mathrm{star}$" (3.3.1 Stellar radius)
   - fitting: _not stated_
   - validation: _not stated_
2. **Determine line profile and systemic velocity**: Gaussian profile from absorption at disk center and emission ring; emission velocity adopted as systemic  
  > "We adopted the emission line velocity as the systemic velocity $\varv_\mathrm{sys}$" (3.3.2 Line profile)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit thin shell model to radial profile**: R_shell from peak of azimuthally averaged radial profile; fit I_shell*tau_shell and tau_cool with beam-convolved model  
  > "The model profile is adjusted to the ALMA radial intensity profile $I(r)$ (Fig. [7](#radprofiles)), using as variables $I_\mathrm{shell}\,\tau_\mathrm{shell}$ and the optical depth of the cooler absorbing layer" (3.3.3 Shell radius)
   - software: SciPy
   - parameter: optically thin shell assumed (tau_shell << 1)  
  > "We make the assumption here that the light-emitting layer is optically thin ($\tau_\mathrm{shell} \ll 1$)" (3.2 Shell model)
   - fitting: Levenberg–Marquardt chi2 minimization with scipy.optimize.leastsq  
  > "we used a classical Levenberg–Marquardt algorithm based on the SciPy routine `scipy.optimize.leastsq`" (3.3.3 Shell radius)
   - validation: A thick-shell fit was attempted but was unstable  
  > "We attempted to fit a thick shell model, adding one parameter in the model (the shell thickness), but the results are unstable" (3.3.3 Shell radius)
4. **Build emission velocity map**: Compensate absorption in the cube, then fit Gaussian (amplitude, width, velocity) per position  
  > "At each position of the absorption compensated data cube, we fit a Gaussian profile on the emission line with three parameters" (3.4 Molecular emission velocity map)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit solid body rotation model**: Fit solid body rotation (v_sys, v_eq sin i, PA), with and without expansion term, to velocity map within stellar disk  
  > "The three model parameters are the systemic velocity $\varv_\mathrm{sys}$ in the local standard of rest (LSR), the projected rotation velocity $\varv_\mathrm{eq}\,\sin i$, and the position angle of the polar axis $PA$." (3.5 Rotation velocity)
   - parameter: v_sys fixed to emission ring value; fit radius varied by ±15% for systematics  
  > "we chose the approach to modulate the radius over which the fit is computed by $\pm 15\%$ around the continuum radius of the star" (3.5 Rotation velocity)
   - assumption: angular velocity independent of latitude  
  > "This simple model assumes that the angular rotation velocity is independent of latitude." (3.5 Rotation velocity)
   - fitting: chi2 fit; uncertainties scaled by sqrt(chi2_red)  
  > "The listed uncertainties of the model parameters have been scaled by $(\chi^2_\mathrm{red})^{1/2}$" (3.5 Rotation velocity)
   - validation: Compared four lines; differential rotation fit gave no significant improvement  
  > "the adjustment of this model does not bring a significant improvement of the $\chi^2$ or residuals of the fit" (4.4 Inclination)
6. **Derive rotation period, Keplerian comparison**: Combine parallax, R_star and v_eq sin i; compare with Keplerian velocity  
  > "we obtain a rotation period of $P / \sin i = 36\pm 8$ years" (4.4 Inclination)
   - assumption: mass 15 ± 5 Msun  
  > "Assuming a mass of $m_\mathrm{Bet} = 15 \pm 5\ M_\odot$" (3.3 Radial rotation velocity profile)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **SciPy** : Levenberg–Marquardt least squares fit (scipy.optimize.leastsq)  
  > "a classical Levenberg–Marquardt algorithm based on the SciPy routine `scipy.optimize.leastsq`" (3.3.3 Shell radius)
- **Astropy** : general analysis  
  > "This research made use of Astropy[^1], a community-developed core Python package for Astronomy ." (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| v_eq sin i | 5.47 | 0.25 | km/s | 5 | $\varv_\mathrm{eq}\sin i = 5.47\pm 0.25$ km s$^{-1}$ |
| R_star (ALMA continuum) | 29.50 | 0.14 | mas | 1 | $R_\mathrm{star} = 29.50\pm 0.14$ mas |
| Position angle of north pole | 48.0 | 3.5 | deg | 5 | $PA = 48.0\pm 3.5^\circ$ |
| omega sin i | 5.6e-9 | 1.3e-9 | rad/s | 6 | $\omega\,\sin i = (5.6\pm 1.3) \times 10^{-9}$ rad s$^{-1}$ |
| P / sin i | 36 | 8 | years | 6 | $P / \sin i = 36\pm 8$ years |
| R_shell (SiO v=2) | 37.8 | 2.5 | mas | 3 | $R_\mathrm{shell} = 37.8 \pm 2.5$ mas |
| Systemic LSR velocity (SiO v=2 emission) | +4.52 | 0.09 | km/s | 2 | $\varv_\mathrm{sys\,LSR} = +4.52 \pm 0.09$ km s$^{-1}$ |
| Expansion velocity (SiO v=2) | +0.69 | 0.08 | km/s | 5 | $\varv_\mathrm{exp} = +0.69\pm 0.08$ km s$^{-1}$ |
| Keplerian velocity at stellar surface | 45 | 28 | km/s | 6 | the Keplerian rotation velocity at the surface of Betelgeuse is $\varv_K = 45 \pm 28$ km s$^{-1}$ |

## Qualitative findings

- Molecular shell co-rotates with star; no significant global outflow at 40 mas; hot spot, plume and dust arc aligned with polar axis, suggesting focused mass loss from a rogue convection cell  
  > "suggests that focused mass loss is currently taking place in the polar region of the star." (abstract)

## Claim tuples

- H: Betelgeuse's rotation can be measured from ALMA SiO velocity map | E: Solid body rotation fit to SiO v=2 J=8-7 emission velocity map | R: v_eq sin i = 5.47 ± 0.25 km/s, PA = 48.0 ± 3.5 deg | F: Betelgeuse rotates slowly with P/sin i = 36 ± 8 yr | **supported**
- H: The chromosphere co-rotates with the star | E: Compare ALMA velocity with UV measurements at larger radii | R: Linear velocities similar, angular velocity lower at larger radii | F: Co-rotation up to ≈10 au | **supported**
- H: Hot spot, plume and dust shell reveal focused mass loss from rogue convection cells | E: Compare PA of pole, ALMA hot spot, molecular plume, and dust arc | R: Position angles coincide | F: Focused mass loss from rogue cell; scenario not directly confirmed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: SiO v=2 line chosen as best match to thin shell model and likely traces regions closest to star  
  > "We chose this line as its intensity profile is the best match to our thin shell model" (3.3 Static shell model parameters)
- Alternative: Thick shell model unstable; differential rotation model gave no significant improvement  
  > "We attempted to fit a thick shell model, adding one parameter in the model (the shell thickness), but the results are unstable" (3.3.3 Shell radius)
- How they decided it was enough: _not stated_
- Limitation (authors): Inclination cannot be determined; resolution insufficient for differential rotation  
  > "For this reason, we cannot conclude firmly on the inclination of the polar axis on the line of sight." (4.4 Inclination)
- Caveat (inferred, ours): Rotation signal could be mimicked by non-radial pulsation or turbulence; only ~4 resolution elements across disk
- Caveat (inferred, ours): Simple thin-shell model with fixed parameters; no joint fit or MCMC
- Caveat (inferred, ours): Systematic errors estimated ad hoc
- Caveat (inferred, ours): Single epoch, unknown masing effects

## Reproducibility

- Data public (paper): Project code given; ALMA data acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00206.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters (weighting, cell, mask)
- Missing: CASA version and calibrator names
- Missing: Analysis code not released
- Missing: Exact fitting procedure for velocity maps
- Data volume (inferred): ~100s of GB raw for extended-config multi-epoch band 7 (estimate)
- Score (inferred): 4/5, Data public and models clearly defined with explicit equations, but imaging and calibration settings and code are missing.
- Rediscovery candidate: no, Imaging recipe and fitting details are incomplete, and the extended-configuration data are large.

## Links

- Companion: earlier papers in the Close circumstellar environment of Betelgeuse series (citations stripped) (continuum hot spot and astrometry from 9 Nov 2015 data)

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
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
  "facts": 75,
  "stated": 43,
  "rate": 0.573
 },
 "evidence_ok": true
}
```
