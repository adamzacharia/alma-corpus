# CO and Dust Properties in the TW Hya Disk from High-resolution ALMA Observations

`2018ApJ...852..122H` | The Astrophysical Journal 2018 | first author: Huang, Jane | arXiv: 1801.03948 | DOI: 10.3847/1538-4357/aaa1e7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What are the CO and dust properties (CO column density structure, spectral index/grain sizes) in the TW Hya disk at high angular resolution?  
  > "We analyze high angular resolution ALMA observations of the TW Hya disk to place constraints on the CO and dust properties." (abstract)
- Target **TW Hya**: coordinates J2000 R.A. 11h01m51.905s, Decl. -34d42m17.03s  
  > "the TW Hya disk (J2000 R.A. 11h01m51.905s, Decl. -34d42m17.03s)" (Introduction); "TW Hya is a 10 Myr old K6 star in the TW Hydrae association lying 59.5 pc away from Earth" (Introduction); z/distance 59.5 pc  
  > "the TW Hya disk (J2000 R.A. 11h01m51.905s, Decl. -34d42m17.03s)" (Introduction); "TW Hya is a 10 Myr old K6 star in the TW Hydrae association lying 59.5 pc away from Earth" (Introduction); distance from Gaia (Gaia Collaboration 2016)  
  > "the TW Hya disk (J2000 R.A. 11h01m51.905s, Decl. -34d42m17.03s)" (Introduction); "TW Hya is a 10 Myr old K6 star in the TW Hydrae association lying 59.5 pc away from Earth" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00114.S, 2013.1.00198.S, 2015.1.00686.S, 2013.1.00387.S, 2015.A.00005.S, 2013.1.01397.S, 2016.1.00629.S, 2012.1.00422.S, 2013.1.00196.S
- bands: Band 6 (1.3 mm) and Band 7 (870 um) continuum; 12CO J=3-2 in Band 7  
  > "We reprocessed and combined archival 1.3 mm (Band 6) and 870 $\mu$m (Band 7) continuum data from six ALMA programs." (Continuum Reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 12CO: 139x131 mas (8.3x7.8 AU); combined 290 GHz continuum: 37x26 mas  
  > "The resulting image has a synthesized beam with a FWHM of $139 \times131$ mas ($8.3 \times7.8$ AU) at a position angle of $-74.9\ensuremath{^\circ}$." ($^{12}$CO $J=3-2$ Data Reduction); "The synthesized beam is $37\times26$ mas (2.2 $\times$ 1.5 AU), with a position angle of 73$\ensuremath{^\circ}$7." (Continuum Reduction)
- max recoverable scale: shortest baseline 13.1 m, ~14 arcsec  
  > "The shortest projected baseline is 13.1 m, which corresponds to an angular scale of $\approx14''$" ($^{12}$CO $J=3-2$ Observations)
- sensitivity: 12CO rms ~1.7 mJy/beam per 0.25 km/s channel; continuum rms 20 uJy/beam  
  > "The rms measured in nearby signal-free channels is $\approx$ 1.7 mJy beam$^{-1}$." ($^{12}$CO $J=3-2$ Data Reduction); "The rms measured in a signal-free portion of the image is 20 $\mu$Jy beam$^{-1}$." (Continuum Reduction)
- time on source: _not stated_
- observing dates: 2014 July to 2017 July (see Table 1)  
  > "2017 July 21" (Table 1)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (not stated)
- Line: 13CO J=3-2 (not stated)
- External data: Gaia distance of 59.5 pc  
  > "adjusted for the new *Gaia* distance of 59.5 pc" (Observational results) [from (cite: 2016AA...595A...2G)]
- External data: C18O column density/temperature model (T_mid,10=40 K, q=0.47, Tfrz=27 K) motivating fiducial model  
  > "We set $T_{\textup{mid},10} = 40$ K and $q = 0.47$ based on the midplane temperature derived in (cite: 2017NatAs...1E.130Z)." (The Fiducial Model) [from (cite: 2017NatAs...1E.130Z)]
- External data: Stellar mass 0.88 Msun from SED modeling  
  > "We favor the higher stellar mass value of 0.88 $M_\odot$ derived in (cite: 2012ApJ...744..162A) based on SED modeling." (The Spectral Index Between 1.3 mm and 870 $\mu$m) [from (cite: 2012ApJ...744..162A)]
- External data: Dust opacity 3.3 cm2/g at 290 GHz from Mie calculations  
  > "We adopt a dust opacity at 290 GHz of $\kappa = 3.3$ cm$^2$ g$^{-1}$, based on the Mie scattering calculations reported in (cite: 2009ApJ...700.1502A)" (Radial Variation in Grain Sizes) [from (cite: 2009ApJ...700.1502A)]

## Processing

### Calibration

- pipeline or manual: Some data calibrated by NRAO staff; others calibrated in CASA with archive reduction scripts  
  > "the raw data from programs 2013.1.00387.S, 2015.A.00005.S, and 2013.1.01397.S were downloaded from the ALMA archive and calibrated in `CASA` (cite: 2007ASPC..376..127M) using the accompanying reduction scripts." (Continuum Reduction)
- casa version: CASA 4.5.3 (continuum); CASA 5.0 (line imaging)  
  > "Additional calibration and imaging were performed with `CASA 4.5.3`." (Continuum Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Solar system objects (Butler-JPL-Horizons 2012) or bright quasars; see Table 3  
  > "either a solar system object (using the Butler-JPL-Horizons 2012 model) or a bright quasar was used for amplitude calibration." (Continuum Reduction)
- flux scale uncertainty: 10% systematic  
  > "which is compatible with the estimated 10% systematic flux calibration uncertainty of ALMA in these bands." (Continuum Reduction)
- self calibration: Phase self-calibration of continuum per band; 12CO from 2015.1.00686.S used continuum solutions; 2016.1.00629.S self-calibrated on line-free channels  
  > "The $^{12}$CO observations from 2016.1.00629.S were phase self-calibrated using a continuum model estimated from the line-free channels in the same spectral window." ($^{12}$CO $J=3-2$ Data Reduction)

### Imaging

- task: clean (continuum, mtmfs nterms=2); tclean in CASA 5.0 (12CO)  
  > "imaged together with the `clean` task’s implementation of multi-term multi-frequency synthesis (cite: 2011AA...532A..71R) with $nterms = 2$" (Continuum Reduction)
- deconvolver: multi-scale CLEAN  
  > "The $^{12}$CO datasets were then imaged together with the multi-scale CLEAN algorithm (as implemented in the `tclean` task in `CASA 5.0`)" ($^{12}$CO $J=3-2$ Data Reduction)
- weighting robust: Band 6 image robust=0.5; combined spectral index image robust=0; 12CO robust=1.0; 13CO robust=0  
  > "Briggs weighting (robust = 1.0)" ($^{12}$CO $J=3-2$ Data Reduction); "Briggs weighting (robust $=0.5$)" (Continuum Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: CLEAN mask tailored to emission in individual channels  
  > "The CLEAN mask was tailored to the emission in individual channels." ($^{12}$CO $J=3-2$ Data Reduction)
- multiscale scales: 12CO: 0, 0.2, 0.4, 0.8, 1.6, 3.2 arcsec; Band 6: 0, 0.06, 0.15, 0.3, 0.6 arcsec  
  > "using scales of 0$''$, 0$\ensuremath{''}$2, 0$\ensuremath{''}$4, 0$\ensuremath{''}$8, 1$\ensuremath{''}$6, and 3$\ensuremath{''}$2" ($^{12}$CO $J=3-2$ Data Reduction)
- continuum subtraction: uvcontsub in visibility plane  
  > "The continuum was then subtracted from the line emission in the visibility plane using the `uvcontsub` task." ($^{12}$CO $J=3-2$ Data Reduction)
- line free channels: _not stated_
- primary beam correction: impbcor  
  > "A primary beam correction was applied to the image cube with the `impbcor` task." ($^{12}$CO $J=3-2$ Data Reduction)
- array combination: Extended and compact datasets imaged together jointly; mstransform regrid to 0.25 km/s channels  
  > "the `mstransform` task in `CASA 5.0` was used to regrid and average the visibilities into channels 0.25 km s$^{-1}$ (288 kHz) wide." ($^{12}$CO $J=3-2$ Data Reduction)
- smoothing: _not stated_
- final beam: 139x131 mas at PA -74.9 deg (12CO)  
  > "The resulting image has a synthesized beam with a FWHM of $139 \times131$ mas ($8.3 \times7.8$ AU) at a position angle of $-74.9\ensuremath{^\circ}$." ($^{12}$CO $J=3-2$ Data Reduction)
- final rms: 1.7 mJy/beam (12CO)  
  > "The rms measured in nearby signal-free channels is $\approx$ 1.7 mJy beam$^{-1}$." ($^{12}$CO $J=3-2$ Data Reduction)

### Inherited from earlier work

- Microturbulence fixed to 0.01 km/s  
  > "As in (cite: 2017NatAs...1E.130Z), we fix the microturbulent line broadening parameter to $a_\text{turb}$ = 0.01 km s$^{-1}$" (12CO Radiative Transfer Modeling) [from (cite: 2017NatAs...1E.130Z)]
- Peak brightness map built from three cubes with offset starting velocities  
  > "we follow the example of (cite: 2014ApJ...785L..12C) and produce three image cubes with the same channel width (0.25 km s$^{-1}$)" (12CO J=3-2 Peak Brightness Temperatures) [from (cite: 2014ApJ...785L..12C)]
- Temperature structure vertical gradient prescription  
  > "The temperature structure is modeled using the vertical gradient prescription presented in (cite: 2003AA...399..773D) and (cite: 2012ApJ...744..162A)" (The Fiducial Model) [from (cite: 2003AA...399..773D; 2012ApJ...744..162A)]
- Intensity/spectral index formalism for dust  
  > "Following (cite: 2016ApJ...829L..35T), we estimate the intensity of the submillimeter dust emission as" (Radial Variation in Grain Sizes) [from (cite: 2016ApJ...829L..35T)]
- Archival flux calibration retained except 2016.1.00629.S 2016 Dec 30 rescaled by 8%  
  > "In all other cases, we retained the original flux calibration specified in the ALMA archive." (Additional Calibrator Details) [from ALMA archive scripts]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals and number of iterations
- Line-free channel ranges for continuum and uvcontsub
- Image size and cell size for clean/tclean
- clean thresholds and number of iterations
- Exact spectral windows used per program
- Procedure for how model parameters were chosen beyond 'some experimentation' (no fit/goodness metric)
- Radial bin and deprojection details for profiles

## Analysis recipe

1. **Reduce and combine archival continuum data**: Calibrate, flag line channels, average line-free channels, phase self-calibrate, align phase centers with fixvis/fixplanets, image Band 6 with MS-MFS  
  > "Because of the relatively large proper motion of TW Hya, the `fixvis` and `fixplanets` tasks in `CASA` were used to shift the datasets to a common phasecenter." (Continuum Reduction)
   - software: CASA
   - parameter: robust=0.5; scales 0, 0.06, 0.15, 0.3, 0.6 arcsec  
  > "Briggs weighting (robust $=0.5$) and scales of $0''$, 0$\ensuremath{''}$06, 0$\ensuremath{''}$15, 0$\ensuremath{''}$3, and 0$\ensuremath{''}$6 were used." (Continuum Reduction)
   - fitting: _not stated_
   - validation: Continuum fluxes of self-calibrated images agree within 5% within each band; compared with published images  
  > "The continuum fluxes from the self-calibrated images were within 5% of one another within each band" (Continuum Reduction)
2. **Make 290 GHz spectral index map**: Joint imaging of Band 6+7 with multi-term MFS (nterms=2), spectral index computed where intensity exceeds 5 sigma  
  > "The spectral index is computed only for pixels where the intensity image exceeds 0.1 mJy beam$^{-1}$ (5 $\times$ the rms noise)." (Continuum Reduction)
   - software: CASA
   - parameter: nterms=2, robust=0, i=5 deg, PA=152 deg  
  > "The adopted position angle and inclination are 152 and 5 degrees, respectively" (The Spectral Index Between 1.3 mm and 870 $\mu$m)
   - assumption: M* = 0.88 Msun, distance 59.5 pc  
  > "We favor the higher stellar mass value of 0.88 $M_\odot$" (The Spectral Index Between 1.3 mm and 870 $\mu$m)
   - fitting: _not stated_
   - validation: Compared with 190 GHz spectral index of Tsukagoshi et al.  
  > "Our 290 GHz spectral index map, which has an angular resolution about a factor of two higher than the map from (cite: 2016ApJ...829L..35T), now confirms the presence of the latter two peaks." (Observational results, The Spectral Index Between 1.3 mm and 870 μm)
3. **Image 12CO J=3-2 cube and derive moment/peak Tb maps**: Self-calibrate, uvcontsub, mstransform to 0.25 km/s, multi-scale tclean, impbcor; integrated intensity above 3 sigma; peak Tb via Planck law, median of three offset cubes  
  > "A peak brightness map is computed by taking the maximum value along the frequency axis for each pixel in the image cube and then converting to a brightness temperature using Planck’s law" (12CO J=3-2 Peak Brightness Temperatures)
   - software: CASA
   - parameter: integration -1.91 to 7.59 km/s; 3 sigma clip  
  > "An integrated intensity map was produced by summing emission above the $3\sigma$ level in the velocity range from $-1.91$ to 7.59 km s$^{-1}$." ($^{12}$CO $J=3-2$ Data Reduction)
   - fitting: _not stated_
   - validation: Imaged without continuum subtraction; integration limits changed flux <0.1%  
  > "truncating or extending the integration range by a few channels changed the integrated flux by less than $0.1\%$" ($^{12}$CO $J=3-2$ Data Reduction)
4. **Parametric LTE radiative transfer modeling of 12CO**: Axisymmetric parametric models with RADMC-3D, sampled with vis_sample, imaged identically to data; compare fiducial, freezeout-only, no-freezeout, perturbed temperature models by eye  
  > "The `vis_sample` package[^3] (cite: 2015ApJ...806..154C; loomis) is used to sample the radiative transfer images at the same spatial frequencies as the data" (12CO Radiative Transfer Modeling)
   - software: RADMC-3D, vis_sample, radmc3dPy
   - parameter: Fiducial: N_CO=3e19 cm-2, R1=15 AU, R2=70 AU, A=3, f=0.025, Tmid10=40 K, Tatm10=125 K, q=0.47, Tfrz=27 K, Rin=0.05, Rout=215 AU  
  > "$N_\text{CO}$ (cm$^{-2}$) | $3\times 10^{19}$" (Table 2)
   - assumption: LTE; thin Keplerian disk; inclination 5 deg, PA 152 deg; mu=2.37; CO freezeout step function p=1e-6 below Tfrz  
  > "Local thermal equilibrium is assumed for calculating the intensity of $^{12}$CO $J = 3-2$ because its critical density" (12CO Radiative Transfer Modeling)
   - fitting: No formal fit; parameters set by experimentation; Tatm10 chosen so systemic-channel flux matches within 5%  
  > "we choose a value of 125 K such that the spatially integrated fluxes of the channels at the systemic velocity for the observations and fiducial model are within 5$\%$ of one another" (The Fiducial Model)
   - validation: Freezeout-only model fails to reproduce features; no-freezeout and perturbed temperature tests  
  > "The failure of the “freezeout-only" model to reproduce the key features of the observations indicates that these features are not artifacts resulting from sparse $uv$ coverage or of the deconvolution algorithm" (A Freezeout-only Model)
5. **Constrain grain size / optical depth from spectral index**: Solve alpha(tau, beta, Td) with emission model, limits on tau from brightness temperature and Td<=30 K; Toomre Q stability check  
  > "The dust temperature is likely no more than 30 K in the gaps and rings beyond a radius of 25 AU" (Radial Variation in Grain Sizes)
   - parameter: kappa=3.3 cm2/g at 290 GHz; gas-to-dust 100; T=15 K for Q  
  > "Assuming an ISM gas-to-dust ratio of 100" (Optical Depth Variations)
   - assumption: Vertically isothermal mm dust; ISM beta upper limit 1.7  
  > "the upper limit on $\beta$ should be the ISM value of $\approx1.7$ (cite: 2006ApJ...636.1114D), when no grain growth has occurred." (Radial Variation in Grain Sizes)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.3 (continuum), 5.0 (line): Calibration, self-calibration, clean/tclean imaging, uvcontsub, mstransform, impbcor, fixvis  
  > "Additional calibration and imaging were performed with `CASA 4.5.3`." (Continuum Reduction)
- **RADMC-3D** : LTE level populations and ray tracing of 12CO model cubes  
  > "The radiative transfer code RADMC-3D[^2] (cite: 2012ascl.soft02015D) is used to compute the $^{12}$CO level populations" (12CO Radiative Transfer Modeling)
- **vis_sample** : Sample model images at data uv points to make model visibilities  
  > "The `vis_sample` package[^3] (cite: 2015ApJ...806..154C; loomis) is used to sample the radiative transfer images" (12CO Radiative Transfer Modeling)
- **radmc3dPy** : listed in software section (use not detailed)  
  > "`radmc3dPy` (<http://www.ast.cam.ac.uk/~juhasz/radmc3dPyDoc/index.html>)" (Software)
- **AstroPy** : listed in software section  
  > "`AstroPy` (cite: 2013AA...558A..33A)" (Software)
- **analysisUtils** : listed in software section  
  > "`analysisUtils`" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 12CO integrated flux (r<4 arcsec) | 42.7 | 0.2 | Jy km/s | 3 | The integrated flux, measured inside a circular mask with a radius of $4''$, is 42.7$\pm0.2$ Jy km s$^{-1}$. |
| 12CO emission extent (3 sigma) | 3.6 arcsec (215 AU) | not stated | arcsec | 3 | $^{12}$CO emission exceeding the $3\sigma$ level extends to a radius of $\approx 3.6\ensuremath{''}$ (215 AU) |
| 12CO/13CO flux ratio in outer annulus (101-214 AU) | ~20 | not stated | dimensionless | 3 | Inside this annulus, the $^{12}$CO/$^{13}$CO flux ratio is $\approx20$ |
| 12CO column density drop radius / bump radius (fiducial) | 15 AU / 70 AU | not stated | AU | 4 | $R_1$ (AU) / 15 / \- / 15 / 15 |
| Spectral index in rings | 1.7-2.2 | scatter | dimensionless | 2 | $\alpha$ values range from 1.7 to 2.2, taking the scatter into account |
| Spectral index peaks at gaps (25, 41, 47 AU) | ~2.6-2.7 | not stated | dimensionless | 2 | $\alpha$ peaking at $\sim2.6-2.7$ near the locations of the continuum emission gaps at 25, 41, and 47 AU |
| Peak 12CO brightness temperature 25-90 AU | ~70 to 35 | not stated | K | 3 | The peak brightness temperatures between radii of 25 and 90 AU range from $\sim$70 to 35 K |
| Lower limit on optical depth in gaps/rings outside 25 AU at 290 GHz | >~0.25 | not stated | dimensionless | 5 | this suggests that $\tau\gtrapprox 0.25$ at 290 GHz in the gaps and rings outside 25 AU |

## Qualitative findings

- 12CO emission has a bright core, shoulder at ~70 AU and break at ~90 AU matching features in 13CO and C18O  
  > "The CO emission exhibits a bright inner core, a shoulder at $r\approx70$ AU, and a prominent break in slope at $r\approx90$ AU." (abstract)

## Claim tuples

- H: Can 12CO emission morphology be explained by CO column density substructure? | E: LTE RADMC-3D models with sharp drop and secondary bump vs smooth freezeout-only | R: Fiducial model reproduces core, deficits, shoulder and 90 AU break; freezeout-only does not | F: Column density drop at ~15 AU and bump at ~70 AU reasonably reproduce emission | **supported**
- H: Do the CO features trace midplane CO freezeout? | E: Peak brightness temperatures and no-freezeout model | R: Tb well above freezeout temperatures within 100 AU; features insensitive to freezeout | F: Features are likely not midplane snowline; arise from X_CO variation or gas density reductions | **supported**
- H: What do spectral index variations imply about dust grains? | E: 290 GHz spectral index map and emission model | R: alpha ~2 at rings, ~2.7 in gaps | F: Grains in gaps no larger than few mm; rings either have cm grains or are marginally optically thick | **partially**
- H: Can temperature variations alone reproduce the CO substructure? | E: Perturbed temperature model with smooth column density | R: Morphology within 150 AU similar with 60% and 15% temperature boosts | F: Degenerate; gas substructure vs depletion cannot be distinguished with current data | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Parametric models chosen for flexibility and low computational cost, aiming at guidance rather than an optimal model  
  > "our aim in this work is not to present an optimal model, but to provide guidance for which physical and chemical mechanisms would plausibly yield the key emission features" (12CO Radiative Transfer Modeling)
- Alternative: Freezeout-only, no-freezeout and perturbed temperature models considered; thermochemical modeling deferred  
  > "An alternative approach is thermochemical disk modeling" (12CO Radiative Transfer Modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): Models are not optimal; dust modeling and multi-line fitting deferred; perturbed temperature model not physically self-consistent  
  > "this model is not physically self-consistent" (A “Perturbed Temperature" Model)
- Limitation (authors): Absolute alpha uncertain by ~0.4 from flux calibration  
  > "A $\sim10\%$ flux uncertainty in each band would correspond to an uncertainty in the overall offset of $\Delta \alpha\sim0.4$" (The Spectral Index Between 1.3 mm and 870 $\mu$m)
- Caveat (inferred, ours): Models were tuned by eye without a quantitative fit or uncertainties on parameters
- Caveat (inferred, ours): Strong degeneracy among temperature, depletion, and gas density with optically thick 12CO
- Caveat (inferred, ours): Self-cal and imaging parameters not fully specified
- Caveat (inferred, ours): Optical depth/grain-size conclusions depend on assumed dust temperature and opacity

## Reproducibility

- Data public (paper): Archival ALMA data downloaded from the ALMA archive  
  > "were downloaded from the ALMA archive and calibrated in `CASA`" (Continuum Reduction)
- Products in archive: _not stated_
- Code: vis_sample version used is available on GitHub  
  > "Version used in this work available at <https://github.com/AstroChem/vis_sample/tree/j>." (footnote 3)
- Missing: Self-calibration solints and line-free channel lists
- Missing: Image/cell sizes and clean thresholds
- Missing: Full RADMC-3D setup details (dust, CO abundance code) beyond table 2
- Missing: Deprojection/radial-profile binning details
- Data volume (inferred): ~hundreds of GB raw across ~9 programs (many Band 6/7 execution blocks); imaged products ~tens of GB
- Score (inferred): 3/5, Public data and many numeric settings given, but self-cal, mask, and model-selection details are missing and models are tuned by eye.
- Rediscovery candidate: no, Main model results are qualitative comparisons without a fitting procedure; reproduction of continuum spectral index and integrated flux is feasible but recipe incomplete.

## Links

- Method: (cite: 2011AA...532A..71R) (Multi-term multi-frequency synthesis)
- Method: (cite: 2008ISTSP...2..793C) (Multi-scale CLEAN)
- Method: (cite: 2015ApJ...806..154C) (vis_sample)
- Companion: (cite: 2017NatAs...1E.130Z) (C18O model that motivates the fiducial 12CO model)
- Companion: (cite: 2016ApJ...829L..35T) (190 GHz spectral index of TW Hya)
- Companion: (cite: 2016ApJ...820L..40A) (870 um continuum rings and gaps in TW Hya)

## Checks

```json
{
 "quotes": 94,
 "quotes_ok": 94,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 9,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 64,
  "rate": 0.744
 },
 "evidence_ok": true
}
```
