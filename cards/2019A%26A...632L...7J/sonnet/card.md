# Detection of a high-redshift molecular outflow in a primeval hyperstarburst galaxy

`2019A&A...632L...7J` | Astronomy and Astrophysics 2019 | first author: Jones, G. C. | arXiv: 1911.09967 | DOI: 10.1051/0004-6361/201936989

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Is there a dense, warm molecular outflow in the lensed hyperstarburst SPT 0346-52 at z=5.656, traced by high-excitation H2O absorption, and what are its mass outflow rate and loading factor?  
  > "In order to explore the dense and warm molecular outflow in the starburst galaxy SPT 0346-52 at $z=5.656$, we used band 7 of the Atacama Large Millimeter/submillimeter Array (ALMA)" (Introduction)
- Target **SPT 0346-52 (SPT-S J034640-5204.9)**: coordinates _not stated_; z/distance z = 5.656; 1 arcsec = 6.033 proper kpc  
  > "Detailed lens modelling shows that the galaxy is magnified by $\mu=5.6\pm0.1$ (cite: spil16)" (Introduction); distance from CO redshift (Aravena et al. 2016); Planck cosmology  
  > "Detailed lens modelling shows that the galaxy is magnified by $\mu=5.6\pm0.1$ (cite: spil16)" (Introduction)

## Data provenance

- ALMA projects: 2016.1.01313.S, 2013.1.00722.S, 2015.1.00117.S
- bands: Band 7  
  > "Our ALMA band 7 observations were taken between 4 and 11 October, 2016, using 40-43 antennas in configuration C40-7." (Observations and data reduction)
- frequencies and spectral setup: two sidebands, each two SPWs of 128 channels of 15.625 MHz; lines at 340.167 and 329.980 GHz  
  > "Our frequency range was covered by two sidebands, each composed of two spectral windows (SPWs) made of 128 channels, each of them 15.625 MHz wide." (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-7, 40-43 antennas  
  > "using 40-43 antennas in configuration C40-7" (Observations and data reduction)
- baselines: _not stated_
- angular resolution: 0.14'' x 0.12'' continuum beam  
  > "resulting in a restoring beam of $0.14''\times0.12''$ at a position angle of $\sim-50^{\circ}$" (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: 0.2-0.5 mJy/beam per channel; continuum 0.25 mJy/beam  
  > "the RMS noise level per channel ranged from $0.2$ to $0.5$ mJy beam$^{-1}$." (Observations and data reduction)
- time on source: 1.95 h on source of 3.23 h total  
  > "Out of 3.23 hours of total observation time, 1.95 hours were on-source." (Observations and data reduction)
- observing dates: 4-11 October 2016  
  > "Our ALMA band 7 observations were taken between 4 and 11 October, 2016" (Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: H2O 4(2,3)-4(1,4) (2264.14965 GHz)
- Line: H2O 3(3,0)-3(2,1) (2196.345756 GHz)
- External data: Lensing magnification mu=5.6±0.1  
  > "Detailed lens modelling shows that the galaxy is magnified by $\mu=5.6\pm0.1$ (cite: spil16)" (Introduction) [from (cite: spil16)]
- External data: SFR = 3600±300 Msun/yr from SED fit  
  > "Spectral energy distribution (SED) modelling yields a massive star formation rate (SFR$=3600\pm300$ $M_{\odot}$ year$^{-1}$; (cite: ma16))" (Introduction) [from (cite: ma16)]
- External data: CO, [CII] and lower-energy H2O emission profiles used for systemic velocity  
  > "centroid of the emission transitions of CO ((cite: arav16; dong19)), \[CII\] ((cite: litk19)), and water emission lines" (Results and evidence for molecular outflow) [from (cite: arav16; dong19; litk19)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA pipeline by ALMA staff  
  > "These data were calibrated by ALMA staff following the standard pipeline." (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "Using the CASA task tclean, the continuum-subtracted data in each sideband were used to create spectral data cubes" (Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "natural weighting in order to balance the RMS noise level and resolution" (Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: continuum cleaned interactively  
  > "the image was cleaned interactively" (Observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in uv-space, flat continuum  
  > "Continuum subtraction was performed in *uv*-space (CASA uvcontsub) using all line-free channels" (Observations and data reduction)
- line free channels: excluding ±750 km/s from expected line frequency at z=5.656  
  > "excluding $\pm750$ km s$^{-1}$ from the expected frequency, assuming $z=5.656$" (Observations and data reduction)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.14'' x 0.12'', PA ~ -50 deg  
  > "restoring beam of $0.14''\times0.12''$ at a position angle of $\sim-50^{\circ}$" (Observations and data reduction)
- final rms: 0.25 mJy/beam continuum  
  > "an RMS noise level of $0.25$ mJy beam$^{-1}$" (Observations and data reduction)

### Inherited from earlier work

- Redshift z=5.656 for line-free channel selection and systemic frame  
  > "assuming $z=5.656$; (cite: arav16)" (Observations and data reduction) [from (cite: arav16)]
- Shell width dR/R_CONT values 3, 19, 10 taken from local ULIRG modelling  
  > "$dR/R_{CONT}=3$, 19, and 10, following the geometries obtained by (cite: gonz10; gonz12; gonz17)" (Outflow model) [from (cite: gonz10; gonz12; gonz17)]

### Not stated but needed to reproduce (our reading)

- Cell size and image size for cubes and continuum
- Primary beam correction details
- Spectral-line extraction aperture for the northern image absorption spectrum
- Number of clean iterations/threshold
- Partition function value and excitation temperature used in the mass outflow rate
- MultiNest settings (live points, tolerance) and likelihood form
- Exact CASA version

## Analysis recipe

1. **Continuum subtraction and cube/continuum imaging**: uvcontsub with flat continuum, tclean cubes of 15.6 MHz channels, natural weighting; MFS continuum from line-free channels  
  > "A continuum image was created using the line-free channels that were used for continuum estimation, multifrequency synthesis, and natural weighting." (Observations and data reduction)
   - software: CASA
   - parameter: exclude ±750 km/s around lines  
  > "excluding $\pm750$ km s$^{-1}$ from the expected frequency" (Observations and data reduction)
   - assumption: flat continuum despite 1-2% change over sideband  
  > "we still assume a flat continuum" (Observations and data reduction)
   - fitting: _not stated_
   - validation: absorption detected regardless of continuum subtraction method  
  > "the water absorption lines in both the northern and southeastern components are detected clearly regardless of the continuum subtraction method" (Observations and data reduction)
2. **Measure continuum size and SFR surface density**: Beam-deconvolved size of northern image, delivered to source plane with mu; SFR from SED fit times 0.5 for FWHM fraction  
  > "including a factor of 0.5 to scale the total SFR to the fraction of FIR flux contained within the full width at half max (FWHM)" (4.1 Hyperstarburst nature of SPT 0346-52)
   - assumption: mu = 5.6±0.1; SFR = 3.6e3 Msun/yr  
  > "Taking the velocity-independent continuum magnification factor (cite: spil16) of $\mu=5.6\pm0.1$ into account" (4.1 Hyperstarburst nature of SPT 0346-52)
   - fitting: _not stated_
   - validation: compared to Eddington-limited starburst Sigma_SFR~1e3  
  > "a factor of five times higher than that of ‘maximum’ (i.e. Eddington-limited) starbursts" (4.1 Hyperstarburst nature of SPT 0346-52)
3. **Fit spherical outflow model to H2O 3(3,0)-3(2,1) absorption and derive mass outflow rate**: Spherical shell with constant mass outflow rate, Sobolev optical depth, convolved with Gaussian; mdot from fitted v0, tau0 with assumed water abundance  
  > "a spherical continuum emitter is surrounded by a shell of outflowing gas which we assume to feature a constant mass outflow rate" (Outflow model)
   - software: MultiNest, PyMultiNest
   - parameter: gamma=-1; dR/R_CONT=3,19,10; R_IN=0.07 kpc; chi_H2O~1e-6  
  > "we adopt the same abundance inferred for local ULIRGS ($\chi_{H_2O}\sim10^{-6}$)" (Spherical outflow model)
   - assumption: emission negligible; aperture and R_CONT/R_IN ratios unity; CO redshift as rest frame  
  > "Because of this, we assume that the emission is negligible." (Spherical outflow model)
   - fitting: MultiNest; free v0, tau0, sigma_v; log-uniform priors 10^0-10^3.5 km/s for v0 and sigma_v, 10^-8-10^0 for tau0  
  > "We adopt log-uniform distributions for $v_{\circ}$ and $\sigma_v$ ($10^0-10^{3.5}$ km s$^{-1}$), and a log-uniform for $\tau_o$ in the range $10^{-8}-10^0$." (Spherical outflow model)
   - validation: _not stated_
4. **Mass loading factor**: eta = Mdot/SFR using SFR 3.6e3 (and 4.5e3 alternative)  
  > "then we find a mass loading factor of $\rm \eta\sim0.03-0.28$" (Outflow model)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : uvcontsub and tclean  
  > "Using the CASA task tclean, the continuum-subtracted data in each sideband were used to create spectral data cubes" (Observations and data reduction)
- **MultiNest** : Bayesian fit of outflow model  
  > "a Bayesian inference code (MultiNest; (cite: fero08)) was used to explore a wide parameter space" (Outflow model)
- **PyMultiNest** : python wrapper for MultiNest  
  > "Using the Bayesian inference code MultiNest (cite: fero08) and its python wrapper (PyMultiNest; (cite: buch14))" (Spherical outflow model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Beam-deconvolved FIR continuum size, northern image | (0.34±0.03)'' x (0.19±0.02)'' | ±0.03/±0.02 | arcsec | 2 | has a beam-deconvolved size of $(0.34\pm0.03)''\times(0.19\pm0.02)''$ |
| Source-plane HWHM | 0.32 | 0.02 | kpc | 2 | source-plane half width at half max (HWHM) of $0.32\pm0.02$ kpc |
| SFR surface density | 5.5e3 | 0.9e3 | Msun/yr/kpc^2 | 2 | we find a SFR density of $\Sigma_{SFR}=(5.5\pm0.9)\times10^3$ M$_{\odot}$ year$^{-1}$ kpc$^{-2}$ |
| Mass outflow rate | 100-900 (average ~500) | not stated | Msun/yr | 3 | total mass outflow rates in the range $\dot{M}\sim100-900\,$M$_{\odot}\,$year$^{-1}$, with an average value of $\dot{M}\sim500\,$M$_{\odot}\,$year$^{-1}$ |
| Mass loading factor | 0.03-0.28 | not stated | dimensionless | 4 | then we find a mass loading factor of $\rm \eta\sim0.03-0.28$ |
| Absorption blueshift of dip relative to CO centroid | ~170 | not stated | km/s | 0 | The bottom of the absorption feature is blueshifted by $\sim170$ km s$^{-1}$ |

## Qualitative findings

- Asymmetric blueshifted H2O absorption indicates a dense molecular outflow with velocities up to 500 km/s; merger interpretation disfavoured in favour of a single compact starburst core  
  > "Finally, our results show that the previous interpretation of a major merger for the kinematics of this source is untenable." (Conclusions)

## Claim tuples

- H: SPT 0346-52 hosts a molecular outflow | E: Band 7 observations of two high-excitation H2O lines | R: Blueshifted asymmetric absorption seen in northern and southeastern images | F: A dense molecular outflow along the line of sight is present | **supported**
- H: The starburst exceeds the Eddington-limited SFR surface density | E: Measure continuum size at 0.14'' resolution and combine with SED SFR | R: Sigma_SFR = (5.5±0.9)e3 Msun/yr/kpc^2 | F: Hyper-Eddington starburst, ~5x the maximum | **supported**
- H: The outflow regulates star formation | E: Spherical outflow model fit | R: Mdot ~100-900 Msun/yr, eta 0.03-0.28 | F: Outflow is massive but eta well below unity, so star formation runs away | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Major merger interpretation rejected; considered biconic outflow and water dip as systemic velocity  
  > "our results show that the previous interpretation of a major merger for the kinematics of this source is untenable" (Conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): Outflow loading factor poorly constrained; shell thickness unconstrained  
  > "The outflow loading factor in SPT0346-52 is not well constrained" (4.3 Outflow model)
- Caveat (inferred, ours): Mdot depends strongly on assumed water abundance, shell width and excitation temperature
- Caveat (inferred, ours): Fit to a single spectrum with simple spherical geometry
- Caveat (inferred, ours): Outflow rate depends on choice of systemic redshift (drops >10x if absorption dip used)
- Caveat (inferred, ours): Upper-limit size R_IN set by beam

## Reproducibility

- Data public (paper): Calibrated cubes at CDS; model code on GitHub  
  > "Calibrated data cubes are available in electronic form at the CDS via anonymous ftp" (Acknowledgements)
- Products in archive: _not stated_
- Code: https://github.com/gcjones2/SphOut  
  > "The spherical outflow model used to fit the observed spectrum is available at https://github.com/gcjones2/SphOut." (Footnote 3)
- Missing: Imaging grid parameters
- Missing: Spectrum extraction region
- Missing: Excitation temperature and partition function
- Missing: MultiNest run settings
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Public data and code, but imaging and fit details are sparse and results depend on assumptions.
- Rediscovery candidate: no, Recipe lacks several settings and the outflow rate depends on unstated assumptions.

## Links

- Method: (cite: fero08) (MultiNest sampler)
- Method: (cite: gonz17) (shell geometries for outflow model)
- Companion: (cite: dong19) (CO(8-7) and differential lensing)
- Companion: (cite: litk19) ([CII] kinematics)
- Companion: (cite: apos19) (H2O emission lines)
- Related: South Pole Telescope survey

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2013.1.00722.S",
  "2015.1.00117.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 43,
  "rate": 0.597
 },
 "evidence_ok": true
}
```
