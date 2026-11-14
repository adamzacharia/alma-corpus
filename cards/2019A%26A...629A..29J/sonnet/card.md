# Organic chemistry in the innermost, infalling envelope of the Class 0 protostar L483

`2019A&A...629A..29J` | Astronomy and Astrophysics 2019 | first author: Jacobsen, Steffen K. | arXiv: 1809.00390 | DOI: 10.1051/0004-6361/201833214

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Does the innermost envelope of the Class 0 protostar L483 contain a Keplerian disk or an infalling-rotating collapse, and are complex organic molecules in a hot corino or a disk?  
  > "We wish to observe and constrain the velocity profile of the gas kinematics near the central protostar and determine whether Keplerian motion or an infalling-rotating collapse under angular momentum conservation best explains the observations." (abstract)
- Target **L483 (IRAS 18148-0440)**: coordinates 18h17m29.90s, -04d39m39.50s (J2000)  
  > "Both observations were centered on $\alpha_{2000}$=18$^{\mathrm{h}}$17$^{\mathrm{m}}$29.90$^{\mathrm{s}}$, $\delta_{2000}$=-04$^{\circ}$39$^{\prime}$39.50$^{\prime\prime}$" (2 Observations); "We therefore adopt the previous distance estimate of 200 pc in this paper." (Introduction); z/distance 200 pc  
  > "Both observations were centered on $\alpha_{2000}$=18$^{\mathrm{h}}$17$^{\mathrm{m}}$29.90$^{\mathrm{s}}$, $\delta_{2000}$=-04$^{\circ}$39$^{\prime}$39.50$^{\prime\prime}$" (2 Observations); "We therefore adopt the previous distance estimate of 200 pc in this paper." (Introduction); distance from Dame & Thaddeus 1985; Gaia-DR2 extinction/parallaxes (Appendix) suggest 200-250 pc  
  > "Both observations were centered on $\alpha_{2000}$=18$^{\mathrm{h}}$17$^{\mathrm{m}}$29.90$^{\mathrm{s}}$, $\delta_{2000}$=-04$^{\circ}$39$^{\prime}$39.50$^{\prime\prime}$" (2 Observations); "We therefore adopt the previous distance estimate of 200 pc in this paper." (Introduction)

## Data provenance

- ALMA projects: 2012.1.00346.S, 2015.1.00377.S
- bands: Band 7, Cycles 1 and 3  
  > "in ALMA Band $7$ as part of Cycle $1$ observations" (2 Observations)
- frequencies and spectral setup: Four spectral windows ~342.8-357.0 GHz, 0.244 MHz channels  
  > "| 3 | 356.490 – 356.958 | 4 | 0.244 |" (Table 1)
- continuum bandwidth: _not stated_
- arrays: 12-m antennas: 44 (Cycle 1), 38 or 39 (Cycle 3)  
  > "The Cycle 1 observations used 44 12-m antennas" (2 Observations)
- configurations: _not stated_
- baselines: 20-600 klambda (Cycle 1); 15-1800 klambda (Cycle 3)  
  > "with baselines in the range of $15$–$1800$ k$\lambda$." (2 Observations)
- angular resolution: Cycle 3 beams ~0.13"; combined 0.28-0.36" x 0.20-0.26"  
  > "0.13$^{\prime\prime}\times0.11^{\prime\prime}$" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 1.8 h (Cycle 1), 3.6 h (Cycle 3) total integration  
  > "with total integration times of 1.8 hours and 3.6 hours for Cycle 1 and Cycle 3, respectively." (2 Observations)
- observing dates: 2013 Jun 1, Jun 19, Nov 2, Nov 3; 2016 Aug 31, Sep 7, Sep 9  
  > "on the nights of $2013$ June $1$, $2013$ June $19$, $2013$ November $2$, and $2013$ November $3$" (2 Observations)
- pi or archival as stated: _not stated_
- Line: HCN 4-3 (354.5055 GHz)
- Line: HCO+ 4-3 (356.7342 GHz)
- Line: CS 7-6 (342.8829 GHz)
- Line: H13CN 4-3 (345.3398 GHz)
- Other facility **2MASS, WISE, AKARI, IRAS, SCUBA, SMA etc. (SED)**: Photometry used to integrate SED for bolometric luminosity  
  > "we integrated the SED and estimate the bolometric luminosity to be 10.5" (Analysis: Dust temperature profile and the distribution of COMs)
- Other facility **Gaia-DR2**: Parallaxes and extinctions for distance check  
  > "we extracted the extinctions and parallaxes for all stars within 1 degree of L483 from the Gaia-DR2 catalog" (Appendix)
- External data: PILS IRAS16293B spectra and column densities used to assign lines  
  > "we compared our L483 data directly to those from the ALMA Protostellar Interferometric Line Survey (PILS) of the low-mass Class 0 protostellar binary IRAS 16293-2422" (3.1 Other lines) [from (cite: 2016A&A...595A.117J)]
- External data: Dust opacities (bare grain and thin ice mantle, coagulated at 10^6 cm-3)  
  > "We used bare-grain and thin ice-mantle opacities from (cite: 1994A&A...291..943O)" (4.2 Dust temperature profile) [from (cite: 1994A&A...291..943O)]
- External data: Outflow inclination 75-90 deg  
  > "Using an inclination between 75–90$^{\circ}$ (cite: 2018ApJ...863...72O)" (4.1 Kinematics) [from (cite: 2018ApJ...863...72O)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA v. 4.7  
  > "Both Cycle 1 and 3 data were calibrated using `CASA` v. 4.7." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1733-1304 or J1924-2914 (Cycle 1); J1924-2914 or J1733-1304 (Cycle 3), depending on date  
  > "For $2013$ November $2$ and $3$, J$1733$–$1304$ was the phase calibrator and J$1924$–$2914$ was the flux and bandpass calibrator." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: Phase self-calibration on continuum channels of each dataset before combination  
  > "Phase self-calibration was also performed on the continuum channels in each dataset before combination." (2 Observations)

### Imaging

- task: clean algorithm  
  > "were created with the `clean` algorithm using Briggs weighting with a robust parameter of 0.5" (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "using Briggs weighting with a robust parameter of 0.5, to get a good trade-off between sensitivity and angular resolution." (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum from line-free channels subtracted after concatenation  
  > "the continuum was constructed using line-free channels and subtracted from the line emission cubes." (2 Observations)
- line free channels: _not stated_
- primary beam correction: Applied before imaging  
  > "After primary beam correction, both line emission channel images and the 857 $\upmu$m continuum image were created" (2 Observations)
- array combination: Cycle 1 binned by 4 channels to match Cycle 3; Cycle 3 trimmed to Cycle 1 bandwidth; concatenated  
  > "the Cycle 1 data were binned down with 4 channels in each bin to match the Cycle 3 channel width" (2 Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Infall velocity profile v_phi ∝ r^-1 approach used previously for Class 0/I kinematics  
  > "a velocity profile previously used to estimate the kinematics of a disk or disk-like structure around Class 0/I objects (cite: 2014A&A...566A..74L)." (4.1 Kinematics) [from (cite: 2014A&A...566A..74L)]
- Density solution for infalling-rotating collapse with centrifugal radius 60 au  
  > "we used the density solution to an infalling-rotating collapse (cite: 1984ApJ...286..529T), with an example centrifugal radius of $60$ au (cite: 2017ApJ...837..174O)." (4.2 Dust temperature profile) [from (cite: 1984ApJ...286..529T); (cite: 2017ApJ...837..174O)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum
- clean masks, thresholds, cell and image size
- Self-calibration solution intervals
- Details of LTE synthetic spectra fits (source size, linewidth, Vlsr)
- Initial dust density model parameters and RADMC-3D setup
- imfit box definitions and uncertainties on peak positions
- Pipeline vs manual calibration

## Analysis recipe

1. **Calibrate, combine and image**: Calibrate Cycles 1 and 3, self-calibrate, concatenate, subtract continuum, clean with Briggs 0.5  
  > "After concatenation of the Cycles 1 and 3 data, the continuum was constructed using line-free channels and subtracted from the line emission cubes." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify COM lines**: LTE synthetic spectra compared to PILS IRAS16293B data; column densities as sanity check  
  > "for a given molecule the spectra are predicted under the assumption of local thermodynamic equilibrium given assumptions of the column density, excitation temperature, systemic velocity, line width and source size." (3.1 Other lines)
   - parameter: Tex 100 K for most species; CH3OCHO slightly better at 300 K  
  > "an excitation temperature of $100\pm 25$ K reproduces the relative line strengths, while the lines of CH$_3$OCHO are slightly better fitted with a higher excitation temperature of 300 K." (3.1 Other lines)
   - fitting: _not stated_
   - validation: Comparison with PILS identifications  
  > "The general agreement with the identifications in the IRAS16293B data strengthens this case, however." (3.1 Other lines)
3. **Channel-peak positions and kinematic fits**: imfit peak position per channel in H13CN and CS; reduced chi2 fit of Keplerian vs infall (angular momentum conserving) profiles  
  > "we fit the position of the peak emission in each spectral cube channel, using the 2D Gaussian fit routine, CASA `imfit`." (4.1 Kinematics)
   - software: CASA imfit
   - parameter: Keplerian mass 0.01-1.5 Msun; specific angular momentum 1e4-1.5e5 m2/s; 2.8e5 uniform steps; rest velocity 6.0 km/s  
  > "we used a central mass range of 0.01-1.5 M$_{\odot}$ and $2.8\times10^5$ uniform steps in the specific angular momentum range for the infall velocity profile of 10$^4$ – 1.5$\times10^5$ m$^2$ s$^{-1}$" (4.1 Kinematics)
   - assumption: Inclination 75-90 deg; optically thin emission for rest velocity  
  > "This is done under the assumption of optically thin emission." (4.1 Kinematics)
   - fitting: Grid reduced chi2 minimisation  
  > "used in a reduced $\chi^2$ fit of two different velocity profiles" (4.1 Kinematics)
   - validation: Repeated with Cycle 3 only, combined, and H13CN only; same conclusion  
  > "The conclusion remain the same, with infall favored for both the combined dataset and Cycle 3-only data." (4.1 Kinematics)
4. **Dust temperature and sublimation radius**: Mass from continuum flux with Ossenkopf & Henning opacities, iterated with RADMC-3D on TSC infall-rotation density  
  > "we used `RADMC-3D`, a 3D Monte Carlo radiative transfer code (cite: 2012ascl.soft02015D), to determine the dust temperature" (4.2 Dust temperature profile)
   - software: RADMC-3D
   - parameter: Initial Tav=100 K, icy/bare ratio 0.5, radius 56 au, gas-to-dust 100  
  > "We used initial guesses of $T_\mathrm{av}$ = 100 K" (4.2 Dust temperature profile)
   - assumption: gas-to-dust 100; bare-grain opacities; distance 200 pc  
  > "using a gas-to-dust mass ratio of 100" (4.2 Dust temperature profile)
   - fitting: Iteration to stable parameters  
  > "After a few iterations, we had a stable estimate of all parameters" (4.2 Dust temperature profile)
   - validation: Repeated with opacities for 1e7 and 1e8 cm-3  
  > "The 44-52 au sublimation radius of the $10^6$ cm$^{-3}$ gas density model is decreased to a 41-49 au sublimation radius in the $10^8$ cm$^{-3}$ gas density model." (4.2 Dust temperature profile)
5. **COM spatial extents**: 2D Gaussian fits to moment 0 maps integrated over ±7 km/s; compare to sublimation radius  
  > "integrating all emission within $\pm$ 7 km s$^{-1}$ based on Fig. [12]" (3.1 Other lines)
   - fitting: 2D Gaussian  
  > "we fit the position of the peak emission in each spectral cube channel, using the 2D Gaussian fit routine" (Analysis: Kinematics)
   - validation: _not stated_

## Software

- **CASA** 4.7: Calibration, clean imaging, imfit  
  > "Both Cycle 1 and 3 data were calibrated using `CASA` v. 4.7." (2 Observations)
- **PVEXTRACTOR** : PV diagrams, path width 0.05"  
  > "Each was produced along the velocity vector using `PVEXTRACTOR`, with a path width of 0.05$^{\prime\prime}$" (3 Results)
- **RADMC-3D** : Dust temperature  
  > "we used `RADMC-3D`, a 3D Monte Carlo radiative transfer code" (4.2 Dust temperature profile)
- **Astropy** : Acknowledged as used  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Combined 857 um continuum flux | 68.6 | 4.4 | mJy | 1 | to be 68.6 $\pm$ 4.4 mJy |
| Cycle 3 continuum flux | 53.7 | 3.5 | mJy | 1 | an integrated flux density of $53.7$ $\pm$ $3.5$ mJy |
| Reduced chi2 infall (Cycle 3) | 0.84 | not stated | dimensionless | 3 | with $\chi^2_{\mathrm{red}}$ = 0.84, while the Keplerian fit has $\chi^2_{\mathrm{red}}=11.6$ |
| Reduced chi2 Keplerian (Cycle 3) | 11.6 | not stated | dimensionless | 3 | with $\chi^2_{\mathrm{red}}$ = 0.84, while the Keplerian fit has $\chi^2_{\mathrm{red}}=11.6$ |
| Rest velocity | 6.0 | not stated | km/s | 3 | The rest velocity for L483 was estimated to be 6.0 km s$^{-1}$ |
| Bolometric luminosity | 10.5 | not stated | Lsun | 4 | estimate the bolometric luminosity to be 10.5 L$_{\odot}$ |
| Inner-region total mass | 8.8e-4 | not stated | Msun | 4 | we estimate the total mass (dust + gas) in the inner region to be $8.8\times10^{-4}$ M$_{\odot}$ |
| Sublimation radius (1e6 cm-3 opacities) | 44-52 | not stated | au | 4 | The 44-52 au sublimation radius of the $10^6$ cm$^{-3}$ gas density model |
| COM deconvolved size | 0.2-0.3 (40-60 au) | not stated | arcsec | 5 | deconvolved sizes of approximately 0.2–0.3$''$ (40–60 au) |

## Qualitative findings

- No Keplerian disk down to ~15 au radius; infalling-rotating collapse  
  > "We find that L483 does not harbor a Keplerian disk down to at least $15$ au in radius." (abstract)

## Claim tuples

- H: Is gas kinematics Keplerian or infall with angular momentum conservation? | E: Reduced chi2 fits of channel-peak positions of H13CN and CS | R: Infall chi2red 0.84 vs Keplerian 11.6 (Cycle 3) | F: Infall profile favored; no Keplerian disk beyond ~15 au | **supported**
- H: Are COMs in the hot corino? | E: Compare COM Gaussian sizes with RADMC-3D sublimation radius | R: COM extent 40-60 au vs ~50 au sublimation | F: COMs reside in the hot corino | **supported**
- H: COM kinematics follow infall | E: imfit of CH3OCHO channel peaks | R: Consistent with infall profile | F: Only CH3OCHO yields usable profile; consistent | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Aim to distinguish the two profiles rather than get a precise stellar mass  
  > "the paramount goal is to distinguish between the two velocity profiles, not to obtain a precise measure of the stellar mass." (4.1 Kinematics)
- Alternative: Keplerian disk >15 au rejected; tentative Keplerian fit above 5.8 km/s not conclusive  
  > "we cannot conclude the presence of a Keplerian disk with a radius of $15$ au, since the data is too noisy and sparse" (4.1 Kinematics)
- How they decided it was enough: _not stated_
- Limitation (authors): Peak-position method valid only for single-position components; COM line assignments tentative  
  > "is only exactly valid when each emission component comes from a single position." (4.1 Kinematics)
- Caveat (inferred, ours): Channel-peak fitting is sensitive to beam and outflow contamination
- Caveat (inferred, ours): Uncertainties on fits not given
- Caveat (inferred, ours): Distance 200 pc versus 436 pc affects physical scales
- Caveat (inferred, ours): Dust model is simple and spherical

## Reproducibility

- Data public (paper): Project codes given in acknowledgements  
  > "This paper makes use of the following ALMA data: 2012.1.00346.S and 2015.1.00377.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Clean masks and line-free channels
- Missing: Self-cal parameters
- Missing: Full dust model parameters
- Missing: Fit uncertainties
- Data volume (inferred): ~100-300 GB raw for two Band 7 projects
- Score (inferred): 3/5, Public data and clear main fit approach, but many imaging and modeling settings are unstated.
- Rediscovery candidate: no, Key imaging and model details missing, though results are numeric.

## Links

- Method: (cite: 2016A&A...595A.117J) (PILS line identification reference)
- Companion: (cite: 2017ApJ...837..174O) (Earlier ALMA study of L483 chemistry/kinematics)
- Related: PILS

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 51,
  "rate": 0.662
 },
 "evidence_ok": true
}
```
