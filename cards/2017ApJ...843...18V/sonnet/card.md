# Quasar Feedback in the Ultraluminous Infrared Galaxy F11119+3257: Connecting the Accretion Disk Wind with the Large-scale Molecular Outflow

`2017ApJ...843...18V` | The Astrophysical Journal 2017 | first author: Veilleux, S. | arXiv: 1706.00443 | DOI: 10.3847/1538-4357/aa767d

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: Does the CO(1-0) emission of the ULIRG F11119+3257 show broad wings confirming the molecular outflow, and what are its energetics compared with the OH-based estimates?  
  > "Here, we independently confirm the presence of the molecular outflow in F11119$+$3257, based on the detection of broad wings in the CO(1$-$0) profile derived from ALMA observations." (abstract)
- Target **IRAS F11119+3257**: coordinates _not stated_; z/distance z = 0.190; D_L = 933 Mpc; 3.19 kpc/arcsec  
  > "a nearby ($z$ = 0.190; 1$^{\prime\prime}$ = 3.19 kpc) optically classified type 1 ULIRG" (Introduction); "we adopt a redshift $z = 0.190$ (Rupke et al. 2005b, 2017 in prep.; Xia et al. 2012), a luminosity distance of 933 Mpc" (Introduction); distance from Rupke et al. 2005b; Xia et al. 2012; cosmology of Bennett et al. 2014  
  > "a nearby ($z$ = 0.190; 1$^{\prime\prime}$ = 3.19 kpc) optically classified type 1 ULIRG" (Introduction); "we adopt a redshift $z = 0.190$ (Rupke et al. 2005b, 2017 in prep.; Xia et al. 2012), a luminosity distance of 933 Mpc" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00305.S
- bands: Band 3, CO(1-0) at 96.9 GHz  
  > "CO$(1$-$0)$ line emission at 96.9 GHz (Band 3)" (2 ALMA Observations and Data Reduction)
- frequencies and spectral setup: CO(1-0) plus adjacent continuum; baseband-4 covers CN(1-0) and SiO(3-2); smoothing by 4 giving ~6 km/s resolution  
  > "Spectral smoothing by a factor of 4 was used to reduce the data rate while maintaining a reasonable velocity resolution of $\sim$ 6 km s$^{-1}$." (2 ALMA Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: 36 antennas, 12-m array  
  > "The observations were carried out with 36 antennas in the compact C36-1 12-m array configuration" (2 ALMA Observations and Data Reduction)
- configurations: _not stated_
- baselines: 15-312 m  
  > "with baselines 15 – 312 m" (2 ALMA Observations and Data Reduction)
- angular resolution: ~2.8 arcsec (~9 kpc)  
  > "resulting in an angular resolution of $\sim$2$\ensuremath{''}$8 $\sim$ 9 kpc" (2 ALMA Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: target 140 uJy per 100 km/s channel; achieved 0.28 mJy per 20 km/s channel  
  > "A RMS (1-sigma) sensitivity of 140 $\mu$Jy in each 100 km s$^{-1}$ channel was targeted" (2 ALMA Observations and Data Reduction); "The cube has a noise of 0.28 mJy in the 20 km s$^{-1}$ channels." (3 Results)
- time on source: 1.9 hours on-source (3.2 hours total)  
  > "observed for 1.9 hours (on-source, 3.2 hours in total)" (2 ALMA Observations and Data Reduction)
- observing dates: 2016 January 3 and 10  
  > "on 2016 January 3 and 10" (2 ALMA Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: CO 1-0 (~115.27 GHz (observed 96.9 GHz))
- Line: CN 1-0 hyperfine (113.15 and 113.50 GHz)
- Other facility **Herschel**: OH 119 um profile used for earlier outflow energetics  
  > "the energetics of the outflowing molecular gas were estimated from the optically thick OH 119 $\mu$m transition profile observed with *Herschel*" (abstract)
- Other facility **Suzaku**: X-ray accretion disk wind data (T15)  
  > "Quantities derived from the *Suzaku* data of T15." (Table 4)
- Other facility **IRAM 30m**: Earlier CO(1-0) single-dish measurement  
  > "IRAM 30-m observations by Xia et al. 2012 have already shown that the CO(1$-$0) emission in F11119$+$3257 is broad" (Introduction)
- External data: OH-based outflow energetics, Herschel OH 119 um profile and X-ray wind properties  
  > "Local (“instantaneous”) quantities derived by T15 from the *Herschel* OH 119 $\mu$m presented in V13." (Table 4) [from Tombesi et al. 2015 (T15); Veilleux et al. 2013 (V13)]
- External data: L_AGN = 1.5e46 erg/s from 15-to-30 um color  
  > "$L_{\rm AGN}$ = 1.5 $\times$ 10$^{46}$ ergs s$^{-1}$, derived from the infrared 15-to-30 $\mu$m color and the prescription of Veilleux et al. (2009)" (4.1 Energetics of the CO Outflow) [from Veilleux et al. 2009]
- External data: alpha_CO values (Galactic 4.3, ULIRG 0.8, optically thin 0.34)  
  > "adopt a ULIRG-like $\alpha_{\rm CO}$ of 0.8 $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ as done by Cicone et al. (2014)" (4.1 Energetics of the CO Outflow) [from Cicone et al. 2014; Bolatto et al. 2013]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline-calibrated visibilities  
  > "The pipeline-calibrated interferometric visibilities delivered by ALMA were continuum-subtracted" (2 ALMA Observations and Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: pipeline-calibrated visibilities delivered by ALMA  
  > "The pipeline-calibrated interferometric visibilities delivered by ALMA" (2 ALMA Observations and Data Reduction)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5, 20 km/s channels  
  > "imaged at 20 km s$^{-1}$ resolution using Briggs weighting with a robust parameter of 0.5" (2 ALMA Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: tight box around the source  
  > "cleaned using a tight box around the source" (2 ALMA Observations and Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: uv-plane, first-order polynomial  
  > "continuum-subtracted in the *uv*-plane using a first-order polynomial" (2 ALMA Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Hanning smoothing to ~40 km/s resolution for the spectrum  
  > "Hanning velocity smoothing was carried out to result in a spectral resolution of $\sim$40 km s$^{-1}$" (3 Results)
- final beam: 3.46 x 2.21 arcsec FWHM, PA = 12 deg  
  > "The restoring beam is 3$\ensuremath{''}$46 $\times$ 2$\ensuremath{''}$21 FWHM with PA = 12$^\circ$." (2 ALMA Observations and Data Reduction)
- final rms: 0.28 mJy per 20 km/s channel  
  > "The cube has a noise of 0.28 mJy in the 20 km s$^{-1}$ channels." (3 Results)

### Inherited from earlier work

- Energetics formalism: time-averaged thin shell values  
  > "These correspond to the “time-averaged thin shell” values of Rupke et al. (2005a)" (4.1 Energetics of the CO Outflow) [from Rupke et al. 2005a (cite: Rupke et al. 2005a)]
- Mass from CO flux using equation 3  
  > "using equation 3 from Bolatto, Wolfire, & Leroy (2013a)" (4.1 Energetics of the CO Outflow) [from Bolatto, Wolfire, & Leroy 2013a]
- ULIRG-like alpha_CO = 0.8  
  > "adopt a ULIRG-like $\alpha_{\rm CO}$ of 0.8 $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ as done by Cicone et al. (2014)" (4.1 Energetics of the CO Outflow) [from Cicone et al. 2014]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for the continuum fit
- Number of clean iterations, threshold, cell and image size
- Exact velocity range used for the two-Gaussian fits and the bootstrap setup
- Flux calibrator and CASA/pipeline version
- Source coordinates and phase center
- How the rotation model velocity-gradient fit was parametrized in detail
- How R_out and V_out nominal values map to the quoted mass ranges (aperture flux choices)

## Analysis recipe

1. **Image the cube**: Continuum subtraction in uv plane, Briggs imaging at 20 km/s  
  > "imaged at 20 km s$^{-1}$ resolution using Briggs weighting with a robust parameter of 0.5" (2 ALMA Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Two-Gaussian fit to integrated spectrum**: Simultaneous narrow plus broad Gaussian fit to 3 and 5 arcsec aperture spectra  
  > "we carry out a simultaneous fit for two Gaussians (one narrow, one broad) to these data." (3 Results)
   - fitting: Bootstrap Monte Carlo for uncertainties  
  > "The uncertainties on these quantities were estimated using a bootstrap Monte Carlo method." (3 Results)
   - validation: Broad-to-narrow peak ratio compared with the ~5% assumed  
  > "the broad-to-narrow peak flux ratios ($\sim$3$-$4%) listed in that table are similar to those assumed for the requested ALMA time" (3 Results)
3. **Remove rotating disk and isolate high-velocity gas**: Fit 2D Gaussian per channel; build smooth source model with linearly changing position, Gaussian intensity, constant size and orientation; subtract to obtain residual cube  
  > "a smooth source model with linearly changing position as a function of velocity (to account for a possible velocity gradient; see below), Gaussian changing intensity, but constant size and orientation" (3 Results)
   - assumption: Velocity gradient represents galaxy rotation  
  > "Assuming that this represents the rotation of the gas in the host galaxy" (3 Results)
   - fitting: _not stated_
   - validation: Gradient compared with unpublished Keck OSIRIS Pa-alpha cube  
  > "This compares well with the direction and amplitude of the velocity gradient measured in an unpublished Keck laser guide star adaptive optics Pa$\alpha$ data cube" (3 Results)
4. **Measure size and flux of the outflow**: Gaussian fit to high-velocity map and aperture photometry growth curve  
  > "Aperture photometry on the high-velocity gas confirms that it is indeed extended." (3 Results)
   - fitting: _not stated_
   - validation: uv-plane fits with uvmodelfit and uvmultifit  
  > "we also derived the sizes and fluxes of the wing emission by fitting the data directly in the *uv* plane." (3 Results)
5. **Derive outflow mass and energetics**: Mass from integrated flux with alpha_CO; Mdot = M V/R, Pdot = Mdot V, Edot = 1/2 Mdot V^2  
  > "$$\dot{M}_{\rm out,CO} & = & \frac{M_{\rm out,CO}~V_{\rm out,CO}}{R_{\rm out,CO}}\\" (4.1 Energetics of the CO Outflow)
   - parameter: R_out = 7 kpc, V_out = 1000 km/s  
  > "we adopt a conservatively low value for the radius, $R_{\rm out,CO}$ = 7 kpc, and $V_{\rm out,CO}$ = 1000 km s$^{-1}$" (4.1 Energetics of the CO Outflow)
   - assumption: ULIRG-like alpha_CO = 0.8; luminosity distance 933 Mpc  
  > "ULIRG-like CO$-$to$-$H$_2$ conversion factor of $\alpha_{\rm CO}$ = 0.8 $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$" (4.3 Comparisons with Published Models)
   - fitting: _not stated_
   - validation: Compared with OH-based local and time-averaged values (Table 4)  
  > "Table 4 compares the mass, momentum, and kinetic energy outflow rates derived from the new ALMA CO(1$-$0) data cube" (4.2 Comparisons with the Herschel OH Outflow)

## Software

- **CASA uvmodelfit** : uv-plane model fitting of wing emission  
  > "we used both the CASA *uv*-Plane Model Fitting routine *uvmodelfit* and *uvmultifit*" (3 Results)
- **uvmultifit** : uv-plane fitting of blue and red wings separately  
  > "*uvmultifit* could not deal with the sum of the red and blue wings, so they were fit separately" (3 Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Broad Gaussian integrated flux, 3 arcsec aperture | 0.66 | 0.07 | Jy km/s | 2 | Broad Gaussian  / $-$11 $\pm$ 53    / 1113 $\pm$ 171 / 0.66 $\pm$ 0.07 |
| Broad Gaussian FWHM, 3 arcsec aperture | 1113 | 171 | km/s | 2 | Broad Gaussian  / $-$11 $\pm$ 53    / 1113 $\pm$ 171 |
| High-velocity integrated flux | 0.40 | 0.10 | Jy km/s | 4 | Blue + red wings / \[$-$820, $-$400\], \[+280, +800\] / 0.40 $\pm$ 0.10 |
| Maximum outflow radius | 15 (+5/-8) | +5/-8 | kpc | 4 | 4$\ensuremath{''}$8$^{+1.5}_{-2.7}$ = 15$^{+5}_{-8}$ kpc, is our best estimate of the maximum extent of the CO outflow. |
| Outflowing molecular mass (ULIRG-like alpha_CO) | (0.6-1.4)e9 | not stated | Msun | 5 | This results in an outflowing molecular gas mass of $\sim$ (0.6 $-$ 1.4) $\times$ 10$^9$ $M_\odot$ |
| Mass outflow rate | 80-200 | not stated | Msun/yr | 5 | $\dot{M}_{\rm out,CO}$ = (80 $-$ 200) $M_\odot$ yr$^{-1}$ |
| Momentum flux | (6-13)e35 dyne = 1.5-3.0 L_AGN/c | not stated | dyne | 5 | $\dot{P}_{\rm out,CO}$ = (6 $-$ 13) $\times$ 10$^{35}$ dyne = (1.5 $-$ 3.0) $L_{\rm AGN}/c$ |
| Mechanical power | (3-6)e43 erg/s = 0.15-0.40% L_AGN | not stated | erg/s | 5 | (3 $-$ 6) $\times$ 10$^{43}$ ergs s$^{-1}$ = (0.15 $-$ 0.40)% $L_{\rm AGN}$ |
| Dynamical mass within ~1 kpc | ~5e9 | not stated | Msun | 3 | a dynamical mass of $\sim$5 $\times$ 10$^9$ $M_\odot$ within $\sim$1 kpc from the center is derived |
| Efficiency f_CO | 0.02-0.03 | not stated | dimensionless | 5 | we derive $f_{\rm CO}$ = 0.02 – 0.03 |

## Qualitative findings

- Broad CO(1-0) wings out to ~±1000 km/s confirm the molecular outflow, extended over at least ~7 kpc, the largest in a local ULIRG  
  > "This is the largest molecular outflow found so far in a local ULIRG." (5 Conclusions)

## Claim tuples

- H: Is the molecular outflow in F11119+3257 confirmed independently of OH? | E: Fit CO(1-0) spectrum from ALMA cube for broad wings | R: Broad wings to ~±1000 km/s detected, similar to OH outflow velocity | F: Molecular outflow independently confirmed | **supported**
- H: Is the CO outflow spatially extended? | E: Residual map after disk removal, aperture photometry and uv fits | R: High-velocity gas FWHM 5.1x2.8 arcsec versus 3.46x2.21 beam; radius ~15 kpc max | F: Outflow extends at least ~7 kpc | **supported**
- H: Are CO energetics consistent with OH-based and energy-conserving expectations? | E: Time-averaged thin-shell energetics with ULIRG-like alpha_CO | R: Rates similar to time-averaged OH values, ~4x below local OH values | F: Quasar efficiency stable over few 1e6 yr; momentum-conserving radiation driving not ruled out | **partially**

## Reasoning

- Why this data: CO(1-0) wings provide independent mass tracer, less uncertain than optically thick OH  
  > "we take a complementary approach to constrain the energetics of the molecular outflow in F11119$+$3257, using line emission from low-level transitions of CO" (Introduction)
- Why this method: _not stated_
- Alternative: Galactic and optically thin alpha_CO considered as extremes; ULIRG-like favored  
  > "using a ULIRG-like $\alpha_{\rm CO}$ is the most realistic value for the outflowing molecular gas" (4.3 Comparisons with Published Models)
- How they decided it was enough: _not stated_
- Limitation (authors): Modest angular resolution is a major limitation  
  > "The modest angular resolution of the ALMA data set is a major limitation of our analysis." (5 Conclusions)
- Caveat (inferred, ours): Outflow radius poorly constrained; R = 7 kpc is a chosen nominal value
- Caveat (inferred, ours): alpha_CO uncertain by factor of ~10
- Caveat (inferred, ours): Broad wing could include low-velocity non-outflow gas
- Caveat (inferred, ours): Rotating-disk subtraction model is simple

## Reproducibility

- Data public (paper): ALMA data cited with project code; archive public presumably  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2015.1.00305.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Line-free channel selection
- Missing: Clean parameters and image size
- Missing: Source model fitting details
- Missing: Aperture centers and exact flux ranges behind mass ranges
- Data volume (inferred): ~10-30 GB
- Score (inferred): 6/5, Single dataset with reasonably clear steps, but several imaging and fitting details are missing.
- Rediscovery candidate: yes, Single-project data, mainly numeric results (fluxes, rates), recipe mostly reproducible.

## Links

- Method: Martí-Vidal et al. 2014 (uvmultifit library)
- Companion: Tombesi et al. 2015 (T15) (X-ray wind and OH outflow detection in the same target)
- Companion: Veilleux et al. 2013 (V13) (Herschel OH outflow survey)
- Related: Herschel OH outflow survey of ULIRGs

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
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
  "facts": 75,
  "stated": 48,
  "rate": 0.64
 },
 "evidence_ok": true
}
```
