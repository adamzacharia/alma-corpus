# ALMA reveals a pseudo-disc in a proto-brown dwarf

`2019MNRAS.486.4114R` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Riaz, B. | arXiv: 1904.06418 | DOI: 10.1093/mnras/stz1032

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Does the proto-brown dwarf Mayrit 1701117 host a pseudo-disc, and which formation model (core collapse, disc fragmentation, circum-binary disc) reproduces its CO kinematics?  
  > "We present the observational evidence of a pseudo-disc around the proto-brown dwarf Mayrit 1701117, the driving source of the large-scale HH 1165 jet." (abstract)
- Target **Mayrit 1701117 (M1701117), driving source of HH 1165**: coordinates RA 05:40:25.80, Dec -02:48:55.49 (J2000)  
  > "located in the vicinity of the $\sigma$ Orionis cluster (410$\pm$60 pc; Gaia DR2; Gaia Collaboration 2018)" (1 Introduction); "The peak position of the source is RA (J2000) = 05:40:25.80; Dec (J2000) = -02:48:55.49" (3.1 Continuum Map); z/distance 410±60 pc  
  > "located in the vicinity of the $\sigma$ Orionis cluster (410$\pm$60 pc; Gaia DR2; Gaia Collaboration 2018)" (1 Introduction); "The peak position of the source is RA (J2000) = 05:40:25.80; Dec (J2000) = -02:48:55.49" (3.1 Continuum Map); distance from Gaia DR2 (Gaia Collaboration 2018)  
  > "located in the vicinity of the $\sigma$ Orionis cluster (410$\pm$60 pc; Gaia DR2; Gaia Collaboration 2018)" (1 Introduction); "The peak position of the source is RA (J2000) = 05:40:25.80; Dec (J2000) = -02:48:55.49" (3.1 Continuum Map)

## Data provenance

- ALMA projects: 2016.1.01453.S
- bands: Band 6 (211-275 GHz), six pointings along the HH 1165 jet  
  > "We obtained molecular line and continuum observations in Band 6 (211-275 GHz) at six positions along the HH 1165 jet" (2 Observations)
- frequencies and spectral setup: Line basebands 117.18 MHz wide, 244.14 kHz channels (~0.3 km/s smoothed); one continuum baseband 976 kHz resolution, 1875 MHz bandwidth  
  > "The bandwidth was set to 117.18 MHz, which provides a resolution of 244.14 kHz, or a smoothed resolution of $\sim$0.3 km s$^{-1}$ at 230.5 GHz." (2 Observations)
- continuum bandwidth: 1875 MHz  
  > "one baseband was used for continuum observations where the spectral resolution was set to 976 kHz and the total bandwidth was 1875 MHz" (2 Observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.4 arcsec  
  > "Our chosen configuration was a maximum recoverable scale of $\sim$4$\ensuremath{''}$, and an angular resolution of $\sim$0.4$\ensuremath{''}$." (2 Observations)
- max recoverable scale: ~4 arcsec  
  > "Our chosen configuration was a maximum recoverable scale of $\sim$4$\ensuremath{''}$, and an angular resolution of $\sim$0.4$\ensuremath{''}$." (2 Observations)
- sensitivity: CO 1-sigma rms ~3-4 mJy; other lines ~5-6 mJy; continuum 0.8 mJy  
  > "The 1-$\sigma$ rms in the 1.37 mm continuum image is 0.8 mJy." (2 Observations)
- time on source: _not stated_
- observing dates: May 2016  
  > "Observations with ALMA were carried out in May, 2016" (2 Observations)
- pi or archival as stated: PI Riaz  
  > "(PID: 2016.1.01453.S; PI: Riaz)" (2 Observations)
- Line: 12CO 2-1 (not stated)
- Line: para-H2CO 3(0,3)-2(0,2) (not stated)
- Line: N2D+ 3-2 (not stated)
- Line: C18O 2-1 (not stated)
- Other facility **UKIDSS**: J, K photometry for colour-magnitude diagram  
  > "Figure [10](#ukidss-cmd) shows the UKIDSS ($J-K, J$) colour-magnitude diagram (cmd)." (4.1 Source Properties)
- Other facility **SCUBA-2**: single-dish 850 um continuum mass from earlier paper  
  > "derived from the single-dish SCUBA-2 850$\mu$m continuum flux (Riaz et al. 2015)" (3.1 Continuum Map)
- External data: Core-collapse MHD simulation structure of brown dwarf formation (density, temperature, velocity)  
  > "We consider the physical structure from the core collapse model (hereafter; CC model) of brown dwarf formation presented in Machida et al. (2009)." (4.2.1 Core Collapse Model) [from Machida et al. (2009) (cite: mach09)]
- External data: Baraffe isochrones used for stellar mass estimate  
  > "we have used the infrared photometry for this object and the evolutionary models by Baraffe et al. (2003)" (4.1 Source Properties) [from Baraffe et al. (2003)]
- External data: SCUBA-2 850um mass ~36 MJup and SED model ratio Mdisc/Menv ~0.002  
  > "In Riaz et al. (2015), we estimated the ratio $M_{disc}$/$M_{env} \sim$0.002 from the best model fit to the SED." (4.1 Source Properties) [from Riaz et al. (2015)]
- Simulation/model as data: SPH (Seren) disc-fragmentation simulation of a 42 MJup brown dwarf with a 20 MJup disc, from Stamatellos & Whitworth (2009)  
  > "We simulate a brown dwarf of 42 ${\rm M_{Jup}}$ attended by a 20 ${\rm M_{Jup}}$ disc." (4.2.2 Disc Fragmentation)
- Simulation/model as data: Seren SPH simulations of a 350 MJup single star and a binary with a 20 MJup disc  
  > "a 350 ${\rm M_{Jup}}$ M dwarf attended by a 20 ${\rm M_{Jup}}$ disc, with an initial radius of 90 AU (hereafter, SK350MJ model)" (4.2.3 Single and Circum-binary Keplerian Discs)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Used calibrated data delivered by the EU-ARC  
  > "We employed the calibrated data delivered by the EU-ARC." (2 Observations)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: uniform weighting  
  > "Data analysis was performed on the uniform-weighted synthesized images using the CASA software." (2 Observations)
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Continuum radiative transfer SED modelling and degeneracies  
  > "We refer to Riaz et al. (2015) for a detailed discussion on the continuum radiative transfer modeling and the related degeneracies in the model fit." (4.1 Source Properties) [from Riaz et al. (2015)]
- CC model setup and numerics  
  > "The initial setup of the model, the numerical method and numerical settings are the same as those described in Machida et al. (2008; 2009; 2014)." (4.2.1 Core Collapse Model) [from Machida et al. (2008; 2009; 2014)]
- DF simulation details  
  > "The details of the simulations are described in Stamatellos & Whitworth (2009)." (4.2.2 Disc Fragmentation) [from Stamatellos & Whitworth (2009)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- Flux, bandpass and phase calibrators and flux scale uncertainty
- Cell size, image size, masks, clean threshold
- Continuum subtraction and line-free channels
- Rest frequencies and velocity resolution of the final cubes
- Final synthesized beam
- PVD cut width and extraction details
- MOLLIE grid, abundance profile parameterisation and line width choice
- Machida CC simulation snapshots (data access)
- Pixel/aperture choices for CO spectrum extraction

## Analysis recipe

1. **Measure continuum source size, position and flux**: Fit elliptical Gaussians to the 1.37 mm continuum image  
  > "We have used the CASA tasks *uvmodelfit* and *imfit* to measure the source size, peak position and the continuum flux by fitting one or more elliptical Gaussian components on the image." (3.1 Continuum Map)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive dust and total mass from the continuum**: Optically thin dust mass with Planck function at Tdust  
  > "Assuming that the dust emission at 1.37 mm is optically thin, the dust continuum mass can be calculated from the millimeter flux density as" (3.1 Continuum Map)
   - assumption: kappa = 0.1 (nu/1e12)^beta cm2/g, beta = 1, Tdust = 10 K, gas-to-dust 100, d = 410 pc  
  > "Assuming the dust and gas temperature of 10 K, M$_{dust}$ = 0.21$\pm$0.1 M$_{Jup}$." (3.1 Continuum Map)
   - fitting: _not stated_
   - validation: Compared with SCUBA-2 mass; difference attributed to beam contamination  
  > "The much larger beam size can result in severe contamination from the surrounding medium and enhance the observed emission." (3.1 Continuum Map)
3. **Channel, moment maps and PVDs of CO and other lines**: Moment 0/1/2 maps and image-space PVDs along disc axis (PA 55 deg) and jet axis  
  > "Figure [6](#pvd-co) shows the CO line PVDs created by making a cut along the disc axis (left panel) and the jet axis (right panel)." (3.3.1 12CO line)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit CO spectrum and PVD with physical models**: Input density, temperature, velocity structure from each model into MOLLIE non-LTE radiative transfer; vary abundance profile and line width; convolve with 0.4 arcsec beam; compare spectrum and PVD offsets  
  > "is used as an input to the 3D non-LTE radiative transfer code MOLLIE (Keto et al. 2004). We generate synthetic CO spectra for different radial profiles of the molecular abundance." (4.2 CO Line Modeling)
   - software: MOLLIE
   - parameter: inclination varied; best CC fit 60-70 deg  
  > "The best-fit was obtained for a close to edge-on inclination of 60$\ensuremath{^\circ}$-70$\ensuremath{^\circ}$." (4.2.1 Core Collapse Model)
   - assumption: Dust-to-gas ratio fixed at 0.01 in simulations  
  > "In these simulations, the dust-to-gas ratio is fixed to 0.01" (5 Discussion)
   - fitting: Reduced chi-squared minimisation over synthetic spectra  
  > "For each synthetic spectrum, a reduced-$\chi^{2}$ value is computed to determine the goodness of fit." (4.2 CO Line Modeling)
   - validation: Compare model PVD peak positions and velocities with observed PVD  
  > "we produced a PVD for a cut along the disc axis (55$\ensuremath{^\circ}$), and compared the position and velocity offsets in the model and observed PVDs." (4.2 CO Line Modeling)
5. **Constrain age and CO depletion**: Match velocity offset in CC snapshots at different ages; compare H2 column density from CO modelling and continuum  
  > "We checked for a match with the observed velocity offset using the CC simulation data at different evolutionary stages." (4.2.1 Core Collapse Model)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Analysis of uniform-weighted images; uvmodelfit and imfit  
  > "Data analysis was performed on the uniform-weighted synthesized images using the CASA software." (2 Observations)
- **MOLLIE** : 3D non-LTE radiative transfer for synthetic CO spectra  
  > "3D non-LTE radiative transfer code MOLLIE (Keto et al. 2004)" (4.2 CO Line Modeling)
- **Seren** : SPH simulations for DF, single and circum-binary disc models  
  > "The simulations were performed using the Smoothed Particle Hydrodynamics code (SPH) Seren (Hubber et al. 2011ab)." (4.2.2 Disc Fragmentation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1.37 mm integrated flux | 6.94 | 0.41 | mJy | 1 | The integrated flux is 6.94$\pm$0.41 mJy. |
| Continuum FWHM major x minor, PA | 0.53 x 0.45 arcsec, PA 55.0 deg | 0.02 arcsec; 5.6 deg | arcsec, deg | 1 | The source size has a FWHM of 0.53$\ensuremath{''}$ along the major axis and 0.45$\ensuremath{''}$ along the minor axis |
| Total (dust+gas) mass at 10 K | 20.98 | 1.24 | MJup | 2 | the total (dust+gas) mass M$_{d+g}$ = 20.98 $\pm$ 1.24 M$_{Jup}$ for M1701117 |
| Source VLSR | 12.5 | 0.5 | km/s | 3 | a source V$_{LSR}\sim$ 12.5$\pm$0.5 km s$^{-1}$ for M1701117 |
| Reduced chi2 of best CC fit | 1.1 | not stated | dimensionless | 4 | The reduced-$\chi^{2}$ value of the best-fit is 1.1. |
| Reduced chi2 DF fit | 2.2 | not stated | dimensionless | 4 | The reduced-$\chi^{2}$ value of the best-fit is 2.2. |
| CO abundance N(CO)/N(H2) from CC fit | 5e-6 | 2e-6 | dimensionless | 4 | obtained from the CC line fit is (5$\pm$2)$\times$10$^{-6}$ |
| System age from CC model | 30,000-40,000 | not stated | yr | 5 | we can constrain the age of the M1701117 system to be approximately 30,000-40,000 yr |
| CO depletion fraction | ~2 | not stated | % | 5 | indicates that only $\sim$2% of the CO is depleted from the gas phase |
| Pseudo-disc size, continuum and CO | 165±7 AU (0.43±0.02 arcsec); 192±19 AU (0.5±0.05 arcsec) | as given | AU | 3 | The deconvolved size of the pseudo-disc measured from the dust continuum image is 0.43$\pm$0.02$\ensuremath{''}$ or 165$\pm$7 AU. |

## Qualitative findings

- Keplerian-only discs of 0.35 Msun single or binary fit CO spectrum and PVD poorly  
  > "a purely Keplerian disc model cannot re-produce the observed morphology" (4.2.3 Single and Circum-binary Keplerian Discs)
- No continuum or line emission detected from the shocked knots  
  > "No continuum or line emission is detected at a $\geq$2-$\sigma$ level for any of the shocked regions." (2 Observations)

## Claim tuples

- H: M1701117 hosts a pseudo-disc consistent with core-collapse brown dwarf formation | E: CO PVD and spectrum modelled with MOLLIE using CC simulation | R: Reduced chi2 1.1; reproduces ±2 km/s spread and size | F: Pseudo-disc plus unresolved Keplerian disc explain the kinematics; age 30,000-40,000 yr | **supported**
- H: Disc fragmentation or Keplerian circum-binary disc could explain the observations | E: Same fitting with DF and SK350/CB SPH models | R: Reduced chi2 2.2 (DF), 2.3-2.5 (Keplerian); PVD shapes mismatched | F: These models fit worse than CC | **partially**
- H: CO is depleted in the pseudo-disc | E: Compare H2 column from CO modelling and from continuum | R: 4.2e22 vs 4.1e22 cm-2 | F: Only ~2% of CO depleted | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Disc fragmentation and single/circum-binary Keplerian disc models rejected or disfavoured by poorer fits  
  > "The poor model fits in Fig. [19](#SK350-CB-fit) show that the structure of a 20 M$_{Jup}$ disc around a 0.35 M$_{\ensuremath{\odot}}$ single/binary star is inconsistent" (4.2.3 Single and Circum-binary Keplerian Discs)
- How they decided it was enough: _not stated_
- Limitation (authors): H2CO and N2D+ detections are weak (~2-3 sigma), so interpretation is speculative  
  > "the H$_{2}$CO and N$_{2}$D$^{+}$ detection is quite weak ($\sim$2-3$\sigma$) in M1701117, therefore we can only speculate" (5 Discussion)
- Limitation (authors): Independent gas mass cannot be derived from the CC fit  
  > "we are unable to obtain an independent estimate on the gas mass derived from the CC model fit." (5 Discussion)
- Caveat (inferred, ours): Only one DF simulation was tested, so the comparison between formation scenarios is not a fair test
- Caveat (inferred, ours): Model comparison rests on one spectrum with ~8-9 sigma peak and few PVD peak positions; degeneracies and parameter uncertainties are not explored
- Caveat (inferred, ours): Model fit uncertainty on age and inclination are not quantified
- Caveat (inferred, ours): Binary scenario not excluded at <0.1 arcsec

## Reproducibility

- Data public (paper): Data from ALMA project 2016.1.01453.S, EU-ARC calibrated products  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.01453.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: Machida CC simulation outputs and MOLLIE input setup
- Missing: Seren simulation outputs for DF and Keplerian models
- Data volume (inferred): ~10-50 GB (six pointings, Band 6)
- Score (inferred): 3/5, Observational measurements are reproducible from archive data, but imaging parameters are missing and the model comparison needs proprietary simulations.
- Rediscovery candidate: no, Main results rely on external MHD/SPH simulations and unspecified imaging settings.

## Links

- Method: Machida et al. (2009) (Core collapse brown dwarf simulation used as model)
- Method: Stamatellos & Whitworth (2009) (Disc fragmentation simulation details)
- Method: Keto et al. 2004 (MOLLIE radiative transfer code)
- Companion: Riaz et al. 2017 (Discovery of HH 1165 jet)
- Companion: Riaz et al. 2015 (SCUBA-2 and SED modelling of M1701117)
- Related: sigma Orionis cluster
- Related: UKIDSS

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
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
  "facts": 79,
  "stated": 44,
  "rate": 0.557
 },
 "evidence_ok": true
}
```
