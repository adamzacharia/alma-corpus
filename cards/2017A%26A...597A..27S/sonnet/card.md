# ALMA high spatial resolution observations of the dense molecular region of NGC 6302

`2017A&A...597A..27S` | Astronomy and Astrophysics 2017 | first author: Santander-García, M. | arXiv: 1609.06455 | DOI: 10.1051/0004-6361/201629288

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: What are the physical conditions, structure and velocity field of the dense molecular region of NGC 6302, as seen in high-resolution ALMA 12CO and 13CO J=3-2 maps?  
  > "We investigate the physical conditions, structure and velocity field of the dense molecular region of the planetary nebula NGC 6302 by means of ALMA band 7 interferometric maps." (abstract)
- Target **NGC 6302 (PN G349.5+01.0)**: coordinates phase centre RA 17h13m44.21s, Dec -37d06m15.941s  
  > "NGC 6302 is a large, butterfly-like young PNe located 1.17 kpc away ((cite: meaburn08))" (Introduction); "R.A. 17$^h$13$^m$44.21$^s$, Dec. -37$^{\circ}$06$^\prime$15.941$^{\prime\prime}$." (Flux loss); z/distance 1.17 kpc  
  > "NGC 6302 is a large, butterfly-like young PNe located 1.17 kpc away ((cite: meaburn08))" (Introduction); "R.A. 17$^h$13$^m$44.21$^s$, Dec. -37$^{\circ}$06$^\prime$15.941$^{\prime\prime}$." (Flux loss); distance from Meaburn et al. 2008  
  > "NGC 6302 is a large, butterfly-like young PNe located 1.17 kpc away ((cite: meaburn08))" (Introduction); "R.A. 17$^h$13$^m$44.21$^s$, Dec. -37$^{\circ}$06$^\prime$15.941$^{\prime\prime}$." (Flux loss)

## Data provenance

- ALMA projects: 2013.1.00331.S
- bands: Band 7  
  > "We mapped the rotational transitions $^{12}$CO and $^{13}$CO $J$=3$-$2 in band 7, 345.796 and 330.588 GHz" (Observations)
- frequencies and spectral setup: Two line windows with 0.2 km/s resolution (345.736-345.854 and 330.529-330.647 GHz); two continuum windows with 1.7 km/s resolution  
  > "The backends were set to achieve a spectral resolution of 0.2 km s$^{-1}$ in the lines" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 35 antennas, extended configuration, dual polarisation  
  > "with 35 antennas in an extended configuration and dual polarisation" (Observations)
- baselines: _not stated_
- angular resolution: 12CO beam 0.38x0.33 arcsec PA 87 deg; 13CO beam 0.43x0.36 arcsec PA 97 deg  
  > "The synthetic beam of the $^{12}$CO $J$=3$-$2 map is a 2D Gaussian with a half power beam width (HPBW) of 0$''$38$\times$0$''$33" (Observations)
- max recoverable scale: _not stated_
- sensitivity: rms ~6 mJy/beam in lines, ~1.7 mJy/beam in continuum  
  > "The resulting brightness rms is $\sim$6 mJy beam$^{-1}$ in maps from both $^{12}$CO and $^{13}$CO $J$=3$-$2 emissions, and $\sim$1.7 mJy beam$^{-1}$ in the continuum." (Observations)
- time on source: 20 min correlation time on NGC 6302  
  > "We obtained a total of 20 min of correlation time on NGC 6302." (Observations)
- observing dates: 14 June 2014  
  > "in June 14, 2014 (programme ID 2013.1.00331.S)" (Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (345.796 GHz)
- Line: 13CO J=3-2 (330.588 GHz)
- Line: SO N_J 8_8-7_7 (344.311 GHz)
- Line: NS not stated (345.823 GHz)
- Other facility **JCMT**: 12CO and 13CO J=3-2 single-dish spectra used to estimate flux recovery and constrain the model  
  > "the JCMT $^{12}$CO  and $^{13}$CO  $J$=3$-$2 observations by (cite: peretto07)" (Observational results and data modelling)
- Other facility **Herschel/HIFI**: High-J CO transitions used to fit the model  
  > "These include Herschel/HIFI high-$J$ transitions observed by (cite: bujarrabal11)" (Observational results and data modelling)
- Other facility **HST**: F673N archive image compared with the CO data; F658N image used for the optical lobes model  
  > "we used an optical image in the F673N filter from the Hubble Space Telescope (HST) archive" (Observational results and data modelling)
- External data: JCMT 12CO and 13CO J=3-2 spectra  
  > "comparison of the spectral profiles in JCMT observations by (cite: peretto07)" (Flux loss) [from Peretto et al. 2007 (cite: peretto07)]
- External data: Herschel/HIFI high-J CO observations  
  > "These include Herschel/HIFI high-$J$ transitions observed by (cite: bujarrabal11)" (Observational results and data modelling) [from (cite: bujarrabal11)]
- External data: Distance 1.17 kpc  
  > "located 1.17 kpc away ((cite: meaburn08))" (Introduction) [from (cite: meaburn08)]

## Processing

### Calibration

- pipeline or manual: Delivered CASA-calibrated data recalibrated by the authors  
  > "We improved the delivered `CASA`[^1]-calibrated data by recalibrating them according to our specific needs." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (flux); J1709-3525 (phase and amplitude); J1427-4206 (bandpass)  
  > "Titan was observed as flux calibrator, while the phase and amplitude of the observations were calibrated with J1709-3525." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: Cleaning in GILDAS with support polygons around extended emission  
  > "We performed the cleaning in `GILDAS`[^2] with the aid of support polygons enclosing the extended emission." (Observations)
- deconvolver: _not stated_
- weighting robust: robust weighting, 0.5  
  > "performed image deconvolution by robust weighting (with a value of 0.5)" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Two spectral windows used for continuum subtraction of the lines  
  > "a spectral resolution of 1.7 km s$^{-1}$ in the two spectral windows used for continuum subtraction of the lines" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: channels averaged to 0.42 km/s  
  > "we averaged the initial velocity channels, obtaining velocity resolutions of 0.42 km s$^{-1}$ in the lines" (Observations)
- final beam: 12CO 0.38x0.33 arcsec; 13CO 0.43x0.36 arcsec  
  > "has a HPBW of 0$''$43$\times$0$''$36, with its major axis oriented along a PA of 97$^\circ$" (Observations)
- final rms: ~6 mJy/beam lines; ~1.7 mJy/beam continuum  
  > "The resulting brightness rms is $\sim$6 mJy beam$^{-1}$" (Observations)

### Inherited from earlier work

- Starting morphology, velocity field, densities, temperatures and abundances taken from earlier models  
  > "uses the morphology, velocity field, densities, temperatures, and abundances found by the latter as a starting point" (Observational results and data modelling) [from Santander-García et al. 2015 (cite: santander15a); Dinh-V-Trung et al. 2008 (cite: dinhvtrung08)]
- shapemol code description and limitations  
  > "See (cite: santander15a) for a detailed description of the code, its capabilities and limitations." (Observational results and data modelling) [from (cite: santander15a)]
- 20% calibration uncertainty for single-dish (HIFI) data  
  > "to account for the characteristic 20% uncertainty of the calibration of this instrument (see (cite: santander12))" (Model uncertainties and reliability of the fit) [from (cite: santander12)]

### Not stated but needed to reproduce (our reading)

- Exact recalibration changes made to the CASA-delivered data
- CASA version
- GILDAS clean parameters (iterations, threshold, polygons)
- Line-free channels used for continuum subtraction
- Model grid size, resolution and full lobe-fragment geometry (only in the online SHAPE file)
- Quantitative goodness-of-fit metric (fit is by eye)
- Scale factors for the single-dish profiles per transition

## Analysis recipe

1. **Measure interferometric flux loss**: Compare JCMT spectra with ALMA maps convolved to the JCMT beam at the JCMT position, channel by channel  
  > "We estimated the recovered flux by comparison of the spectral profiles in JCMT observations by (cite: peretto07) with the profiles of the $^{12}$CO  and $^{13}$CO  $J$=3$-$2 maps convolved" (Flux loss)
   - software: GILDAS
   - fitting: _not stated_
   - validation: _not stated_
2. **Reconstruct 3D geometry from the maps**: Assume Hubble-like flow, place pixels above 3 sigma in 3D, inspect in SHAPE, and tune the kinematic age until rings look circular  
  > "The $x$ and $y$ position of every point in every channel above an emission threshold (defined at a 3$\sigma$ level) was registered in a text file along with a $z$ position" (Observational results and data modelling)
   - software: SHAPE
   - parameter: emission threshold 3 sigma  
  > "above an emission threshold (defined at a 3$\sigma$ level)" (Observational results and data modelling)
   - assumption: Hubble-like velocity law  
  > "by assuming a Hubble-like flow with different slopes (kinematic ages)" (Observational results and data modelling)
   - fitting: _not stated_
   - validation: Constant velocity laws rejected as they gave irregular shapes without axial symmetry  
  > "the structures generated in that manner showed very irregular shapes without any degree of axial symmetry" (Observational results and data modelling)
3. **Fit spatio-kinematical and non-LTE radiative transfer model**: SHAPE+shapemol model with LVG radiative transfer; fit to ALMA maps and to JCMT and HIFI single-dish profiles, compromising between maps and profiles  
  > "We therefore opted to model the structures reaching a compromise between the somewhat overestimated maps and the slightly underestimated single-dish profiles." (Observational results and data modelling)
   - software: SHAPE, shapemol
   - parameter: 12CO/13CO abundance ratio 8; 12CO abundance 1e-4, 13CO 1.25e-5  
  > "The best-fit $^{12}$CO and $^{13}$CO abundances are 1$\times$10$^{-4}$ and 1.25$\times$10$^{-5}$, respectively" (Modelling results)
   - assumption: Constant temperature per structure; density falls as 1/r except for constant density in the inner ring and inner main-ring rim; radial Hubble-like velocity  
  > "Each of the structures of the model is characterised by a constant value of the temperature, and a density that drops with the inverse of the distance to the central star" (Modelling results)
   - fitting: Visual inspection, one parameter changed at a time, several series from different starting parameters; no sampler or likelihood  
  > "the fitting procedure is performed by visual inspection on a series of iterations, modifying one parameter at a time" (Observations and data modelling)
   - validation: Simulated ALMA observations of the model in GILDAS give flux loss similar to the real data, though not near the systemic velocity  
  > "we used `GILDAS` to estimate the flux lost in simulated ALMA observations of the model in conditions as similar as possible to those of the actual data" (Model uncertainties and reliability of the fit)
4. **Estimate uncertainties**: Vary one parameter at a time, others fixed, until the fit is no longer reasonable; velocities by eye  
  > "these are computed by fixing all parameters but one, which is varied until the synthetic maps or single-dish profiles no longer provide a reasonable fit" (Model uncertainties and reliability of the fit)
   - software: SHAPE
   - fitting: _not stated_
   - validation: _not stated_
5. **Estimate kinematic age of the optical lobes**: SHAPE spatio-kinematical model fitted simultaneously to the HST F658N image and an echelle spectrum  
  > "We simultaneously fitted the F658N HST image and the echelle spectrum analysed by (cite: meaburn05)." (Lifetime estimate of the optical lobes)
   - software: SHAPE
   - assumption: distance 1.17 kpc  
  > "at the adopted distance of 1.17 kpc" (Lifetime estimate of the optical lobes)
   - fitting: _not stated_
   - validation: Described as a rough estimate  
  > "we stress that these figures should be taken as a rough estimate" (Lifetime estimate of the optical lobes)

## Software

- **CASA** : Delivered calibration, which the authors recalibrated  
  > "We improved the delivered `CASA`[^1]-calibrated data by recalibrating them" (Observations)
- **GILDAS** : Cleaning and imaging; simulating ALMA observations of the model for flux loss  
  > "We performed the cleaning in `GILDAS`[^2]" (Observations)
- **SHAPE** : Interactive 3D spatio-kinematical modelling  
  > "`SHAPE` is an interactive 3D software for modelling complex gaseous nebulae." (Observational results and data modelling)
- **shapemol** : LVG non-LTE radiative transfer plug-in for SHAPE  
  > "`shapemol` works as a plugin for `SHAPE`, enabling full radiative transfer in $^{12}$CO  and $^{13}$CO  lines" (Observational results and data modelling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Inner ring mass | 2.7e-3 | not stated | Msun | 3 | 2.7$\times$10$^{-3}$ |
| Inner ring characteristic radius | 7.5e16 | not stated | cm | 3 | showing a characteristic radius of 7.5$\times$10$^{16}$ cm |
| Inner ring expansion velocity | 11 | +/-0.5 | km/s | 3 | 11$^{+0.5}_{-0.5}$ |
| Inner ring kinematic age | 2200 | not stated | yr | 3 | The latter implies a kinematical age for this ring of just $\sim$2200 years |
| Systemic velocity | -30.4 | not stated | km/s (LSR) | 3 | The systemic velocity of the nebula deduced from our modelling is V$_\mathrm{LSR}$= -30.4 km s$^{-1}$ |
| Main ring symmetry-axis inclination to the line of sight | 75 | not stated | deg | 3 | whose symmetry axis is inclined 75$^\circ$ to the line of sight |
| Inner ring inclination to the line of sight | 52 | not stated | deg | 3 | inclined 52$^\circ$ to the line of sight |
| Total molecular mass | 0.1 | factor 2 (13CO abundance) | Msun | 3 | a similar total molecular mass of 0.1 M$_{\odot}$ |
| 12CO abundance | 1e-4 | not stated | dimensionless | 3 | The best-fit $^{12}$CO and $^{13}$CO abundances are 1$\times$10$^{-4}$ and 1.25$\times$10$^{-5}$ |
| 13CO abundance | 1.25e-5 | factor 2 | dimensionless | 3 | the uncertainty of the $^{13}$CO  abundance, which we estimate at a factor 2 |
| Fraction of flux recovered by ALMA | ~70% red side, 40-50% blue side, ~30% near systemic velocity | not stated | percent | 1 | being $\sim$70% in the redwards regions, between 40 and 50% in the blueward regions, and $\sim$30% near the systemic velocity |
| Kinematic age of the optical wide-open lobes | 3600-4700 | not stated | yr | 5 | to constrain its kinematic age between 3,600 and 4,700 years |
| Upper limit on Keplerian disk diameter | <~100 | not stated | AU | 0 | its diameter must be $\lesssim$100 UA, or 1.5$\times$10$^{15}$ cm |

## Qualitative findings

- The molecular region is a massive broken ring from which lobe-wall fragments emerge, enclosing the base of the optical lobes  
  > "We find that the molecular region consists of a massive ring out of which a system of fragments of lobe walls emerge and enclose the base of the lobes visible in the optical." (abstract)
- No sign of a Keplerian disk around the central star  
  > "show no signature of a circumstellar or circumbinary flat disk in Keplerian rotation" (Discussion)

## Claim tuples

- H: Is there a previously undetected inner ring in NGC 6302? | E: 3D reconstruction and SHAPE+shapemol modelling of the ALMA CO J=3-2 maps | R: Inner ring with R=7.5e16 cm, inclined ~60 deg to the main ring, M=2.7e-3 Msun, expanding at 11 km/s | F: A younger inner ring (~2200 yr) exists, with a counterpart in the HST image, ejected about when the NW optical lobe was | **supported**
- H: Is the total molecular mass consistent with previous estimates? | E: Model fit to ALMA maps plus JCMT and HIFI profiles | R: Total mass ~0.1 Msun | F: Confirms the 0.1 Msun molecular mass | **supported**
- H: Does a compact Keplerian disk exist around the central star? | E: Search the ALMA maps for central low-velocity emission | R: No emission at ALMA sensitivity | F: Any shielded CO disk must have a diameter <~100 AU | **supported**
- H: Is the gap in the southern ring caused by low density or by CO destruction? | E: Abundance contrast test on the optically thin 13CO map | R: Density would have to be 150 times lower | F: Ring broken by photodissociation or shocks | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Simple model chosen because the data are too complex for a perfect fit to give solid conclusions  
  > "since a perfect fit to the data would require dealing with a parameter space that is too large to draw any solid conclusions" (Model uncertainties and reliability of the fit)
- Alternative: Constant velocity laws rejected, except for the inner main ring  
  > "so we discarded such a velocity law except for the inner regions of the main ring" (Observational results and data modelling)
- Alternative: Hourglass structure for the main ring not modelled; thick cylindrical ring used for simplicity  
  > "We chose, however, to model the main ring as a thick cylindrical ring" (Model uncertainties and reliability of the fit)
- How they decided it was enough: _not stated_
- Limitation (authors): Severe flux loss, no short-spacing data; ~30% recovered near systemic velocity, so structures there are excluded  
  > "Unfortunately we did not have short-spacing data to image and analyse the smooth extended structures." (Observational results and data modelling)
- Limitation (authors): Geometry uncertainties are not quantified; fit is only fair  
  > "Owing to their nature, their uncertainties are not quantified in Table 1." (Model uncertainties and reliability of the fit)
- Caveat (inferred, ours): Model fitting is by eye with no objective metric, so parameters are not reproducible to a stated tolerance
- Caveat (inferred, ours): Flux loss biases the model and abundances
- Caveat (inferred, ours): Single-dish and interferometer intensity scales are reconciled by ad hoc scale factors
- Caveat (inferred, ours): Inner ring planetary-ejection origin is speculative

## Reproducibility

- Data public (paper): ALMA programme ID given; archive data acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00331.S." (Acknowledgements)
- Products in archive: _not stated_
- Code: SHAPE-format model file provided as online supporting data  
  > "a file provided in electronic form with the model of the dense molecular region of NGC 6302 in `SHAPE` format is available as on-line supporting data" (Modelling results)
- Missing: Custom recalibration steps
- Missing: GILDAS imaging scripts
- Missing: Per-profile scale factors
- Missing: JCMT and HIFI data from the literature
- Missing: Full lobe fragment geometry (only in SHAPE file)
- Data volume (inferred): ~10-50 GB raw for one 20-min Band 7 execution block
- Score (inferred): 4/5, Public data and clear observational setup, but modelling by eye in SHAPE with custom recalibration and imaging details missing makes exact reproduction hard.
- Rediscovery candidate: no, The main results depend on interactive visual modelling in SHAPE and on external single-dish data, so the recipe is not mechanically repeatable.

## Links

- Method: Santander-García et al. 2015 (cite: santander15a) (Describes shapemol and the earlier model used as the starting point)
- Method: Steffen et al. 2011 (cite: steffen11) (SHAPE software)
- Companion: Dinh-V-Trung et al. 2008 (cite: dinhvtrung08) (Earlier SMA CO J=2-1 maps and model of the molecular torus)
- Companion: Peretto et al. 2007 (cite: peretto07) (JCMT data used for flux recovery and model fitting)

## Checks

```json
{
 "quotes": 81,
 "quotes_ok": 81,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 55,
  "rate": 0.663
 },
 "evidence_ok": true
}
```
