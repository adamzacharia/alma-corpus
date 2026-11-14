# ALMA view of a massive spheroid progenitor: a compact rotating core of molecular gas in an AGN host at z = 2.226

`2018MNRAS.476.3956T` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Talia, M. | arXiv: 1802.06083 | DOI: 10.1093/mnras/sty481

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What are the size, gas content, ISM conditions and kinematics of the dust and molecular gas in GMASS 0953, a proposed progenitor of compact quiescent galaxies?  
  > "we present ALMA spatially resolved observations of the dust continuum and CO lines emission of GMASS 0953, a heavily obscured AGN host selected from the GMASS sample" (Introduction)
- Target **GMASS 0953**: coordinates R.A. 03:32:31.48, Dec. -27:46:23.40  
  > "GMASS 0953[^2] (R.A. 03:32:31.48, Dec. -27:46:23.40) is a SFG at z$_{CO}$=2.2256." (2 GMASS 0953); z/distance z_CO=2.2256  
  > "GMASS 0953[^2] (R.A. 03:32:31.48, Dec. -27:46:23.40) is a SFG at z$_{CO}$=2.2256." (2 GMASS 0953); distance from CO redshift measured in this work  
  > "GMASS 0953[^2] (R.A. 03:32:31.48, Dec. -27:46:23.40) is a SFG at z$_{CO}$=2.2256." (2 GMASS 0953)

## Data provenance

- ALMA projects: 2015.1.01379.S, 2015.1.00228.S
- bands: Band 3 and Band 6  
  > "ALMA observations were carried out in band 3 and 6" (3 ALMA observations)
- frequencies and spectral setup: One 1.875 GHz SPW with 3840 channels at 107.291 GHz (B3) and 214.532 GHz (B6) for CO(3-2) and CO(6-5); two 1.875 GHz SPWs with 960 channels each per band for continuum  
  > "two spectral windows of bandwidth 1.875 GHz covering 960 channels to target dust continuum" (3 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.6 arcsec  
  > "and an angular resolution of 0.6$\ensuremath{''}$" (3 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 32 min (band 3), 1.3 hr (band 6)  
  > "for a total integration time on source of 32 mins and 1.3 hrs respectively" (3 ALMA observations)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (not stated)
- Line: CO J=6-5 (not stated)
- Other facility **HST (ACS/WFC3)**: High-resolution morphology images  
  > "HST images (Fig. [2](#hst); top: ACS/z-band; bottom: WFC3/H-band)) show a compact morphology" (2 GMASS 0953)
- External data: Archival ALMA band 3 data and CO(3-2), CO(4-3), [CI] results, dust mass/temperature consistency  
  > "We also combined our band 3 continuum data with those from (cite: popping2017) taken from the ALMA archive" (3 ALMA observations) [from (cite: popping2017)]
- External data: Photometric and kinematic Halpha PAs and rotation curve  
  > "This value is consistent with both the photometric and kinematic H$\alpha$ PAs as determined by HST imaging and KMOS data" (4 Kinematics) [from (cite: vanderwel2014; wisnioski2017)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA pipeline  
  > "The data were calibrated, imaged and analysed using the standard ALMA pipeline and software package CASA" (3 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% absolute flux accuracy  
  > "Flux errors account for both measurement error and the 10$\%$ absolute flux accuracy due to the calibrator." (3 ALMA observations)
- self calibration: _not stated_

### Imaging

- task: CASA clean, interactive  
  > "The calibrated data were cleaned interactively using masks at source position and setting a threshold of 3$\times$r.m.s. noise level as measured on the dirty images." (3 ALMA observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.2, 100 km/s channels  
  > "a Briggs weighting scheme (cite: briggs1995) with a *robust* parameter of 0.2 and a channel width of 100 km s$^{-1}$" (3 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in uv plane (band 6)  
  > "In band 6 we first subtracted in the *uv* plane the continuum with the task `uvcontsub`." (3 ALMA observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: B6: 0.6x0.5 arcsec PA 60 deg; B3: 1.0x0.7 arcsec PA 80 deg  
  > "resulting in a clean beam of $FWHM$=0.6$\ensuremath{''}$$\times$0.5$\ensuremath{''}$" (3 ALMA observations)
- final rms: 1.4mm continuum 0.03 mJy/beam; line 0.15 (B3) and 0.10 (B6) mJy/beam  
  > "The rms noise level is $\sigma_{1.4mm}$=0.03 mJy/beam." (3 ALMA observations)

### Inherited from earlier work

- Multi-component SED fitting approach  
  > "Following (cite: delvecchio2014), we performed a multi-component SED fitting to the available broadband photometry" (2 GMASS 0953) [from (cite: delvecchio2014)]
- L'CO derived following Solomon et al.  
  > "From the CO(1-0) flux, following (cite: solomon1997) we derive" (3.1 ISM MODELING) [from (cite: solomon1997)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum
- Image size and cell size
- uvmodelfit starting parameters
- Exact BAROLO settings (mask, normalization, fit mode)
- CLOUDY grid ranges and cosmic-ray scaling
- Which CO SLED templates and flux ratios were used
- CASA version

## Analysis recipe

1. **Image continuum and line cubes**: Interactive clean with Briggs weighting; moment 0 over -1000 to 1000 km/s  
  > "obtained by integrating the line channels over the velocity range between -1000 and 1000 km s$^{-1}$" (3 ALMA observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure sizes and fluxes**: Elliptical Gaussian fit to visibilities  
  > "We derived the source size and fluxes by fitting an elliptical Gaussian to the visibility data (task `uvmodelfit`)" (3 ALMA observations)
   - software: CASA uvmodelfit
   - fitting: _not stated_
   - validation: Monte Carlo with mock galaxy and 100 noise realizations  
  > "We then created 100 realizations of the background noise to match our observations and measured the properties of the simulated sources using `uvmodelfit`." (3 ALMA observations)
3. **Derive gas mass**: Extrapolate CO(1-0) from CO(3-2) using average BzK and ULIRG SLEDs, then L'CO and alpha_CO  
  > "Extrapolating the CO(1-0) transition from our observed CO(3-2) flux, assuming the average flux ratio from the appropriate literature SLEDs" (3.1 ISM MODELING)
   - assumption: alpha_CO=0.8 Msun/(K km/s pc^2)  
  > "Assuming a CO-to-H$_{\rm 2}$ conversion factor $\alpha_{\rm CO}$=0.8 $M_{\odot}$/(K km s$^{-1}$ pc$^{2}$)" (3.1 ISM MODELING)
   - fitting: _not stated_
   - validation: Compared with [CI]-based estimate  
  > "that is in good agreement with the estimate derived from the \[C I\] emission line" (3.1 ISM MODELING)
4. **Constrain ISM density and radiation field**: Grid of 1-D slab PDR models compared to [CI]/CO(6-5) and CO(6-5)/CO(4-3) ratios  
  > "we run a grid of CLOUDY PDR models that span ranges in density and intensity of the UV radiation field" (3.1 ISM MODELING)
   - software: CLOUDY
   - fitting: No robust fit feasible; ratios overlaid  
  > "though a robust fit is not currently feasible because the degrees of freedom outnumber the data" (3.1 ISM MODELING)
   - validation: _not stated_
5. **Fit rotation kinematics**: 3D tilted-ring model, two rings of 0.2 arcsec, PA fixed at 95 deg, free Vrot and sigma, inclination varied  
  > "We assumed a disk model with two rings and a ring width of 0.2$\ensuremath{''}$" (4 Kinematics)
   - software: 3DBarolo
   - assumption: Inclination range 60-90 deg from residual maps  
  > "between 60$\degree$ and 90$\degree$" (4 Kinematics)
   - fitting: _not stated_
   - validation: Residual maps; simulations show insensitivity to sigma  
  > "From our simulations we also conclude that the model is quite insensitive to large variations in $\sigma$" (4 Kinematics)

## Software

- **CASA** : Calibration, imaging, uvcontsub, uvmodelfit  
  > "standard ALMA pipeline and software package CASA" (3 ALMA observations)
- **3DBarolo** : Tilted-ring kinematic fit  
  > "a tool for fitting 3D tilted-ring models to emission-line datacubes" (4 Kinematics)
- **CLOUDY** v17.00: PDR model grid  
  > "We did the same investigation with the code *CLOUDY* v17.00" (3.1 ISM MODELING)
- **SED3FIT** : SED fitting  
  > "with the SED3FIT code (cite: berta2013)" (2 GMASS 0953)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(6-5) deconvolved FWHM | 0.18 | 0.06 | arcsec | 2 | we measure a deconvolved $FWHM$=0.18$\ensuremath{''}$$\pm$0.06$\ensuremath{''}$ |
| 1.4 mm continuum flux | 378 | 65 | uJy | 2 | 1.4 mm continuum flux $S_{\rm 1.4mm}$=378$\pm$65 $\mu$Jy |
| CO(6-5) line flux | 1.21 | 0.13 | Jy km/s | 2 | $I_{\rm CO(6-5)}$=1.21$\pm$0.13 Jy km/s |
| H2 mass | 3.24e10 | 0.6e10 | Msun | 3 | $M_{\rm H_{\rm 2}}$=(3.24$\pm$0.6)$\times$10$^{10}$$M_{\odot}$ |
| Rotation velocity | 320 | +92/-53 | km/s | 5 | a best-fit $V_{rot}$=320$^{+92}_{-53}$ km s$^{-1}$ |
| Gas depletion time | ~150 | not stated | Myr | 0 | $\tau_{\rm depl}$=$M_{\rm H_{\rm2}}$/$SFR$$\sim$150 Myr |

## Qualitative findings

- Dust and molecular gas are extremely compact (~1 kpc), consistent with a compact core about to quench  
  > "We measure for the first time the size of the dust and molecular gas emission of GMASS 0953 that we find to be extremely compact ($\sim$1 kpc)." (abstract)

## Claim tuples

- H: GMASS 0953 is a compact star-forming progenitor of a compact quiescent galaxy | E: Measure sizes, gas mass and depletion time from ALMA | R: r~1 kpc, gas fraction 0.2, tdepl~150 Myr | F: It will rapidly exhaust gas and become a compact QG | **supported**
- H: The molecular gas is in a rotating disk | E: 3DBarolo fit to CO(6-5) cube | R: Vrot=320 km/s | F: Evidence of rapidly rotating gas | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Merger in coalescence rejected as unlikely due to no two nuclei in HST image  
  > "this picture seems unlikely based on the absence of two distinct nuclei in the core of the high-resolution HST/ACS image" (4 Kinematics)
- How they decided it was enough: _not stated_
- Limitation (authors): Single PDR cannot fit; robust multi-component fit not feasible  
  > "a robust fit is not currently feasible because the degrees of freedom outnumber the data" (3.1 ISM MODELING)
- Caveat (inferred, ours): Target only marginally resolved; size errors large
- Caveat (inferred, ours): Only two rings and coarse 100 km/s channels limit kinematics
- Caveat (inferred, ours): alpha_CO and CO SLED extrapolation dominate gas mass uncertainty

## Reproducibility

- Data public (paper): Archival ALMA data acknowledged with project codes  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2015.1.01379.S (PI: Cassata)" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust
- Missing: BAROLO configuration
- Missing: SLED templates
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and main steps described, but many parameters missing.
- Rediscovery candidate: yes, Public data, numeric results (size, flux, Vrot) with a reasonably described recipe.

## Links

- Method: (cite: diteodoro2015) (3DBarolo)
- Companion: (cite: popping2017) (Previous ALMA observations of the same target)
- Related: GMASS
- Related: CDF-S

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 39,
  "rate": 0.542
 },
 "evidence_ok": true
}
```
