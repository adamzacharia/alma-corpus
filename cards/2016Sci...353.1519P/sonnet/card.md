# Spiral density waves in a young protoplanetary disk

`2016Sci...353.1519P` | Science 2016 | first author: Pérez, Laura M. | arXiv: 1610.05139 | DOI: 10.1126/science.aaf8296

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Does the Elias 2-27 disk show spiral density waves in the midplane, traced by optically thin 1.3 mm dust emission, and what drives them?  
  > "The arms extend to the disk outer regions and can be traced down to the midplane." (abstract)
- Target **Elias 2-27**: coordinates RA 16h26m45.024s, Dec -24d23m08.250s (J2000)  
  > "Right Ascension (J2000) = 16h 26m 45.024s, Declination (J2000) = –24d 23m 08.250s and coincidental with the position of the star Elias 2-27." (Figure 1 caption); "is a member of the $\rho$-Ophiuchus star-forming complex at a distance of 139 pc (*19*)" (main text); z/distance 139 pc  
  > "Right Ascension (J2000) = 16h 26m 45.024s, Declination (J2000) = –24d 23m 08.250s and coincidental with the position of the star Elias 2-27." (Figure 1 caption); "is a member of the $\rho$-Ophiuchus star-forming complex at a distance of 139 pc (*19*)" (main text); distance from Mamajek 2008 (cite 19)  
  > "Right Ascension (J2000) = 16h 26m 45.024s, Declination (J2000) = –24d 23m 08.250s and coincidental with the position of the star Elias 2-27." (Figure 1 caption); "is a member of the $\rho$-Ophiuchus star-forming complex at a distance of 139 pc (*19*)" (main text)

## Data provenance

- ALMA projects: 2013.1.00498.S
- bands: 1.3 mm continuum plus CO J=2-1 lines  
  > "to observe the protoplanetary disk around the young star Elias 2-27 at a wavelength of 1.3 mm." (main text)
- frequencies and spectral setup: two 2 GHz and three 468.75 MHz continuum windows; three 468.75 MHz line windows at 220.183, 219.715, 230.714 GHz  
  > "The spectral setup consisted of two 2 GHz and three 468.75 MHz windows for continuum observations" (Materials and Methods)
- continuum bandwidth: 6.8 GHz  
  > "with a total continuum bandwidth of 6.8 GHz" (Materials and Methods)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15.1 m to 1.6 km, 44 antennas  
  > "ALMA observations were obtained with 44 antennas whose baseline lengths ranged between 15.1 m to 1.6 km." (Materials and Methods)
- angular resolution: 0.26'' x 0.22'' (36 x 31 AU)  
  > "reaching an angular resolution of $0.26''\times0.22''$" (Figure 1 caption)
- max recoverable scale: _not stated_
- sensitivity: 58.6 uJy/beam continuum rms  
  > "reaching an image RMS noise level (hereafter referred to as $\sigma$) of $\sigma = 58.6$ $\mu$Jy/beam" (ALMA Continuum Imaging)
- time on source: 12.5 min  
  > "The total time on source was 12.5 min" (Materials and Methods)
- observing dates: _not stated_
- pi or archival as stated: Cycle 2 program, P.I. L. Pérez  
  > "Elias 2-27 was observed as part of the ALMA Cycle 2 program 2013.1.00498.S (P.I. L. Pérez)." (Materials and Methods)
- Line: C18O J=2-1 (centered 220.183 GHz window)
- Line: 13CO J=2-1 (centered 219.715 GHz window)
- Line: 12CO J=2-1 (centered 230.714 GHz window)
- Other facility **VLA (Disks@EVLA, AC982)**: 9 mm continuum to test grain growth in the 70 AU gap  
  > "Elias 2-27 was observed as part of our Disks@EVLA program (project code AC982, P.I. C. Chandler) at 9 mm" (Materials and Methods)
- External data: Surface density constraint (Sigma_c=0.05 g cm-2, R_c=200 AU, gamma=0.7, kappa=2.4 cm2/g) used in radiative transfer model  
  > "The parameters adopted, based on the previous constraint on this disk (*20*), are: $\Sigma_c = 0.05$ g cm$^{-2}$, $R_c = 200$ AU, $\gamma = 0.7$" (Radiative Transfer Model) [from Andrews et al. 2009 (cite: 20)]
- External data: Stellar mass 0.5 +/- 0.2 Msun used for Keplerian profile  
  > "We compute the corresponding Keplerian profile for a stellar mass of $0.5 \pm 0.2\; M_{\odot}$" (Materials and Methods) [from (cite: 20,22)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline and CASA  
  > "The ALMA pipeline (*36*) and the CASA software (*37*) were used for calibration" (Materials and Methods)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (bandpass PKS J1517-2422, gain PMN J1626-2426)  
  > "PKS J1517-2422 for bandpass, Titan for absolute flux density calibration, and PMN J1626-2426 for gain calibration" (Materials and Methods)
- flux scale uncertainty: _not stated_
- self calibration: Amplitude and phase self-calibration; SNR improved from 340 to 547  
  > "This procedure improved the dynamic range of the dust continuum image from a signal-to-noise ratio (SNR) of 340 to 547." (ALMA Continuum Imaging)

### Imaging

- task: CASA multiscale clean  
  > "using the multiscale cleaning algorithm (*38*) in CASA" (ALMA Continuum Imaging)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 1.0 (continuum); natural, robust 2.0 for lines  
  > "Briggs weighting with a robust parameter of 1.0" (ALMA Continuum Imaging)
- uv taper: uv-tapering for 13CO and C18O, giving 0.42''x0.38''  
  > "we applied uv-tapering of the visibilities to down-weight long baselines" (ALMA Spectral Line Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.26''x0.22'' continuum  
  > "($0.26''\times0.22''$)" (ALMA Continuum Imaging)
- final rms: 58.6 uJy/beam  
  > "$\sigma = 58.6$ $\mu$Jy/beam" (ALMA Continuum Imaging)

### Inherited from earlier work

- Surface density/temperature structure from earlier SED+visibility modeling adopted  
  > "we adopt a previous surface density constraint found for this object (*20*), which assumes axial symmetry" (Radiative Transfer Model) [from Andrews et al. 2009 (cite: 20)]
- VLA calibration and imaging details  
  > "Further details on calibration and imaging are presented in our group’s publications (*34,35,47,48*)" (VLA Observations) [from (cite: 34,35,47,48)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals and number of iterations
- Clean mask, threshold, cell and image size, multiscale scales
- CASA version
- Initial model for self-cal and flux scale uncertainty
- Settings of the unsharp-mask/background profile functional form and MCMC priors, walkers, steps
- Line-free channels and continuum subtraction for CO
- RADMC-3D setup (grid, stellar parameters, dust composition)

## Analysis recipe

1. **Self-calibrate and image continuum**: Amplitude and phase self-calibration then multiscale clean, Briggs robust 1.0  
  > "Amplitude and phase self-calibration was performed on the continuum observations of Elias 2-27 using the multiscale cleaning algorithm (*38*) in CASA" (ALMA Continuum Imaging)
   - software: CASA
   - fitting: _not stated_
   - validation: SNR improved from 340 to 547  
  > "improved the dynamic range of the dust continuum image from a signal-to-noise ratio (SNR) of 340 to 547" (ALMA Continuum Imaging)
2. **Enhance spirals with unsharp masking**: Subtract scaled Gaussian-smoothed image  
  > "The original image was smoothed with a 2-D Gaussian of $0.33''$ FWHM and the smoothed image was scaled by a factor of 0.87 before subtracting it from the original." (Unsharp Masking Filtering)
   - fitting: _not stated_
   - validation: _not stated_
3. **Estimate optical depth and Toomre Q**: Radiative transfer of azimuthally averaged profile with adopted surface density  
  > "We performed radiative transfer calculations using RADMC3D (*26*) in order to compute the dust temperature and surface density, as well as the optical depth" (Radiative Transfer Model)
   - software: RADMC-3D
   - assumption: gas-to-dust ratio 100; kappa 2.4 cm2/g (RT), 2.3 cm2/g (Toomre Q)  
  > "For a dust mass opacity of $\kappa_{1.3mm} = 2.3$ cm$^2$ g$^{-1}$, commonly used in the literature (*41*)" (Estimation of Toomre Q)
   - fitting: _not stated_
   - validation: Model reproduces azimuthally averaged radial profile  
  > "This model reproduces the azimuthally averaged radial profile of the observed ALMA 1.3 mm continuum emission" (main text)
4. **Fit spirals and dark ring geometry**: Subtract best-fit radial profile, find local maxima/minima every 12 deg, fit ring and two log spirals with MCMC  
  > "we find the position of local maxima and minima of the emission, at evenly spaced azimuthal angles (spaced every $12^{\circ}$)" (Fitting of Dark Ring)
   - software: emcee
   - assumption: Ring and spirals share single i and PA  
  > "The geometry of the spiral arms and dark ring can all be described with a single inclination angle" (main text)
   - fitting: MCMC (emcee); priors not stated  
  > "we employed a Markov Chain Monte Carlo method (*44*)" (Fitting of Dark Ring)
   - validation: Compared with Gaussian fit to visibilities on baselines <150 m  
  > "We find excellent agreement between the orientation on the sky of the large-scale disk" (Fitting of Dark Ring)
5. **Measure spiral contrast**: Ratio of spiral peak to minimum surface brightness at each deprojected radius  
  > "is the background surface brightness on the disk, defined as the minimum flux density at radius $R$" (Calculation of Spiral Arms Contrast)
   - fitting: _not stated_
   - validation: _not stated_
6. **Determine rotation sense and trailing nature from CO**: CO channel maps, PV diagram vs Keplerian curve, near/far side asymmetry  
  > "we infer that the SW side of the disk is tilted towards Earth" (Absolute Geometry)
   - software: CASA
   - fitting: _not stated_
   - validation: No significant deviation from Keplerian  
  > "find no significant deviations from a Keplerian velocity pattern in the Elias 2-27 disk" (Spectral Line Observations)

## Software

- **CASA** : calibration, self-calibration, multiscale clean imaging  
  > "The ALMA pipeline (*36*) and the CASA software (*37*) were used for calibration" (Materials and Methods)
- **RADMC-3D** : radiative transfer for dust temperature and optical depth  
  > "We performed radiative transfer calculations using RADMC3D (*26*)" (Radiative Transfer Model)
- **emcee** : MCMC fit of spirals and ring  
  > "we employed a Markov Chain Monte Carlo method (*44*)" (Fitting of Dark Ring)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spiral R0 | 84 | ±4 | AU | 4 | $R_0 = 84 \pm 4$ AU and $b = 0.138 \pm 0.007$ |
| Spiral b | 0.138 | ±0.007 | dimensionless | 4 | $R_0 = 84 \pm 4$ AU and $b = 0.138 \pm 0.007$ |
| Spiral pitch angle | 7.9 | ±0.4 | deg | 4 | a pitch angle of $\phi = 7.9^{\circ} \pm 0.4^{\circ}$ |
| Dark ring radius | 71 | ±2 | AU | 4 | has a radius of $a_0 = 71 \pm 2$ AU |
| Inclination | 55.8 | ±0.9 | deg | 4 | $i = 55.8^{\circ} \pm 0.9^{\circ}$ and position angle $PA = 117.3^{\circ} \pm 0.9^{\circ}$ |
| Position angle | 117.3 | ±0.9 | deg | 4 | $i = 55.8^{\circ} \pm 0.9^{\circ}$ and position angle $PA = 117.3^{\circ} \pm 0.9^{\circ}$ |
| Spiral contrast range | 1.3 to 2.5 | not stated | dimensionless | 5 | We find both arms have similar contrasts ranging between values of 1.3 and 2.5. |
| Optical depth at 100 AU | 0.1 (0.02 at 300 AU) | not stated | dimensionless | 3 | $\tau=0.1$ at $R=100$ AU, decreasing to $\tau=0.02$ at $R=300$ AU |
| Large-scale disk inclination | 54.4 | ±1.4 | deg | 4 | $i_{disk} = 54.4^{\circ} \pm 1.4^{\circ}$, $PA_{disk} = 118.8^{\circ} \pm 1.5^{\circ}$ |

## Qualitative findings

- Two symmetric trailing spiral arms with low optical depth trace midplane density/temperature enhancements; a low-contrast gap lies at ~70 AU.  
  > "these results imply that NW and SE are tracing density and/or temperature enhancements at the disk midplane" (main text)

## Claim tuples

- H: Spiral arms in the Elias 2-27 disk trace midplane spiral density waves | E: 1.3 mm ALMA imaging, polar projection, ring/spiral fitting, optical depth modeling | R: Two symmetric arms with contrast 1.3-2.5, optically thin (tau 0.02-0.1) | F: Arms trace spiral density waves in the midplane | **supported**
- H: Spirals are driven by gravitational instability alone | E: Toomre Q and disk-to-star mass ratio comparison | R: Q well in stable regime; Mdisk/Mstar at most ~0.3 | F: GI alone is unlikely | **supported**
- H: The 70 AU gap results from grain growth | E: VLA 9 mm imaging | R: No 9 mm emission beyond ~50 AU | F: Gap likely a density decrement | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Planet-disk interaction alone rejected as it struggles to produce symmetric arms of equal contrast; GI alone and PDI+GI also disfavored  
  > "Those models often struggle to produce the symmetric spiral pattern observed in the Elias 2-27 disk" (main text)
- How they decided it was enough: _not stated_
- Limitation (authors): Contrast values are lower limits because of possible beam dilution and higher optical depth.  
  > "Thus, the contrast values measured for NW and SE are lower limits." (main text)
- Caveat (inferred, ours): Optical depth relies on an axisymmetric prior model, not fit to this data
- Caveat (inferred, ours): Short 12.5 min observation; spiral significance and unsharp-mask artefacts not quantified
- Caveat (inferred, ours): Driving mechanism not uniquely identified

## Reproducibility

- Data public (paper): Raw data from ALMA archive and calibrated FITS at a NRAO site  
  > "it can be obtained from the ALMA Science Data Archive, <https://almascience.nrao.edu/alma-data/> (raw format) and in the calibrated fits format used for analysis here" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Self-calibration parameters
- Missing: CASA version
- Missing: Clean masks and image grid
- Missing: MCMC priors and the smooth background profile form
- Data volume (inferred): ~10-20 GB raw (single short EB, Band 6)
- Score (inferred): 3/5, Public data and clear geometric fitting results, but self-cal and clean settings are missing.
- Rediscovery candidate: yes, Public data, numeric geometry results, moderately complete recipe.

## Links

- Method: Rau & Cornwell 2011 (cite: 38) (multiscale clean)
- Method: Foreman-Mackey et al. 2013 (cite: 44) (emcee MCMC)
- Companion: Andrews et al. 2009 (cite: 20) (previous disk structure model)
- Related: Disks@EVLA

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
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 45,
  "rate": 0.608
 },
 "evidence_ok": true
}
```
