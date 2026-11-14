# Fast molecular outflow from a dusty star-forming galaxy in the early Universe

`2018Sci...361.1016S` | Science 2018 | first author: Spilker, J. S. | arXiv: 1809.01676 | DOI: 10.1126/science.aap8900

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: Is there a molecular (OH) outflow from the lensed dusty star-forming galaxy SPT2319-55 at z=5.3, and how large is its mass outflow rate relative to the SFR?  
  > "We present observational evidence of a massive molecular wind being launched from SPT$-$S J231921$-$5557.9 (SPT2319$-$55 hereafter)" (main text)
- Target **SPT2319-55 (SPT-S J231921-5557.9)**: coordinates RA 23h 19m 21.67s, Dec -55d 57m 57.8s  
  > "| Right Ascension | 23h 19m 21.67s |" (Table 1); "| $z_{\rm{source}}$ | 5.2943 |" (Table 1); z/distance z_source = 5.2943; z_lens = 0.91  
  > "| Right Ascension | 23h 19m 21.67s |" (Table 1); "| $z_{\rm{source}}$ | 5.2943 |" (Table 1); distance from ALMA CO and [CI] redshift (Strandet et al. 2016)  
  > "| Right Ascension | 23h 19m 21.67s |" (Table 1); "| $z_{\rm{source}}$ | 5.2943 |" (Table 1)

## Data provenance

- ALMA projects: 2016.1.00089.S, 2016.1.01499.S
- bands: Band 8  
  > "ALMA observed SPT2319$-$55 on 2016 November 18 using the Band 8 receivers" (ALMA Observations and Data Analysis)
- frequencies and spectral setup: LO 405.781 GHz; LSB two 1.875 GHz basebands with 3.9 MHz channels (3.63 GHz continuous); USB two 2 GHz basebands with 15.625 MHz channels  
  > "The ALMA correlator was configured to observe the OH doublet in the lower sideband, delivering two 1.875 GHz basebands with 3.9 MHz channels." (ALMA Observations and Data Analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15-920 m, forty antennas  
  > "Forty antennas were available at the time of observation, with baselines spanning 15–920 m." (ALMA Observations and Data Analysis)
- angular resolution: 0.25'' x 0.4'' (natural weighting)  
  > "The continuum data reach a sensitivity of 105 $\mu\rm{Jy}$ per beam and a beam size of 0.25$\ensuremath{''}\times0.4\ensuremath{''}$ for a naturally-weighted image" (Imaging and Spectral Analysis)
- max recoverable scale: _not stated_
- sensitivity: continuum 105 uJy/beam; cube 45-55 mJy km/s per ~75 km/s channel  
  > "This cube reaches a typical sensitivity of 45–55 mJy km s$^{-1}$" (Imaging and Spectral Analysis)
- time on source: 30 min on-source (75 min total)  
  > "The observations lasted 75 min in total, with 30 min spent on-source." (ALMA Observations and Data Analysis)
- observing dates: 2016 November 18  
  > "ALMA observed SPT2319$-$55 on 2016 November 18" (ALMA Observations and Data Analysis)
- pi or archival as stated: PI J. Spilker program 2016.1.00089.S  
  > "SPT2319$-$55 was observed as part of ongoing ALMA program 2016.1.00089.S (PI: J. Spilker)." (Target Selection)
- Line: OH 2Pi3/2 J=5/2-3/2 Lambda doublet (119 um) (2509.9 and 2514.3 GHz)
- Line: [CII] fine structure (comparison spectrum) (not stated)
- Other facility **ATCA**: CO(2-1) for molecular gas mass  
  > "The molecular gas mass was determined through observations of the CO(2–1) line using the Australia Telescope Compact Array (ATCA)." (Target Selection)
- Other facility **Herschel**: non-detections at 100 and 160 um used in FIR SED  
  > "including non-detections by the *Herschel Space Observatory* at 100 and 160 $\upmu\rm{m}$(cite: strandet16)" (Target Selection)
- External data: Redshift of source from ALMA CO/[CI]  
  > "determined its redshift to be $z_{\rm{source}} = 5.293$ (cite: strandet16)" (main text) [from (cite: strandet16)]
- External data: Low-z OH equivalent width vs mass outflow rate correlation  
  > "Figure [11](#fig:weqmdot) shows the relationship between the outflow rates determined through modeling of multiple OH transitions in local dusty galaxies as a function of the OH 119 $\upmu\rm{m}$ equivalent width (cite: gonzalezalfonso17)" (Mass Outflow Rate Determination) [from (cite: gonzalezalfonso17); CO velocity ranges (cite: cicone14)]
- External data: OH abundance relative to H2 of 5e-6  
  > "We adopt an OH abundance relative to H$_2$ of $5 \times 10^{-6}$ (cite: goicoechea02)" (Mass Outflow Rate Determination) [from (cite: goicoechea02)]
- External data: OH rest frequencies from JPL catalog  
  > "We use the rest frequencies determined with spectroscopic data from the NASA Jet Propulsion Laboratory line catalog (cite: pickett98)." (Target Selection) [from (cite: pickett98)]

## Processing

### Calibration

- pipeline or manual: Standard ALMA Cycle 4 pipeline in CASA  
  > "The data were reduced using the standard ALMA Cycle 4 pipeline in CASA (cite: mcmullin07), and the calibration appears reasonable." (ALMA Observations and Data Analysis)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: PKS J2357-5311 (flux and gains); bandpass PKS J2258-2758  
  > "quasar PKS J2357-5311 was used both to calibrate the absolute flux scale and the time-varying antenna gains" (ALMA Observations and Data Analysis)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "for a naturally-weighted image, which maximizes sensitivity at the expense of spatial resolution" (Imaging and Spectral Analysis)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 25 channels averaged for ~75 km/s resolution  
  > "averaging together 25 channels to create an image cube with a spectral resolution of $\sim$75 km s$^{-1}$" (Imaging and Spectral Analysis)
- final beam: 0.25'' x 0.4''  
  > "a beam size of 0.25$\ensuremath{''}\times0.4\ensuremath{''}$" (Imaging and Spectral Analysis)
- final rms: 105 uJy/beam continuum  
  > "The continuum data reach a sensitivity of 105 $\mu\rm{Jy}$ per beam" (Imaging and Spectral Analysis)

### Inherited from earlier work

- Visibility noise estimated by differencing successive integrations  
  > "we difference visibilities of successive integrations from the same baseline, polarization, and baseband" (ALMA Observations and Data Analysis) [from (cite: hezaveh13; spilker16)]
- Pixellated lens reconstruction code  
  > "We use a pixellated source reconstruction code, described in detail in ref. (cite: hezaveh16)." (Lens Modeling Methodology) [from (cite: hezaveh16)]
- Gas mass conversion assumptions (R21=0.9, alpha_CO=0.8)  
  > "The CO luminosity was converted to a molecular gas mass using the same assumptions as ref. (cite: aravena16)" (Target Selection) [from (cite: aravena16)]
- Thin-shell outflow geometry  
  > "We used the time-averaged thin-shell approximation of (cite: rupke05)" (Mass Outflow Rate Determination) [from (cite: rupke05)]

### Not stated but needed to reproduce (our reading)

- CASA version used by the pipeline
- Imaging task and cleaning parameters (threshold, masks, cell and image size)
- Exact channel ranges used for continuum vs OH in imaging
- Lens model MCMC sampler, priors and parameter values
- Aperture region definition and spectral fit procedure/priors
- Flux calibrator flux density and absolute flux uncertainty
- Lens modelling code is not publicly named/released beyond data files

## Analysis recipe

1. **Reduce and image data**: ALMA Cycle 4 pipeline, natural-weighted continuum and 25-channel-averaged LSB cube  
  > "we imaged the lower sideband data, averaging together 25 channels to create an image cube with a spectral resolution of $\sim$75 km s$^{-1}$" (Imaging and Spectral Analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: Tapered images recover total flux  
  > "We have verified that this procedure accurately recovers the total source flux using additional images created by applying a taper in the $uv$ plane." (Imaging and Spectral Analysis)
2. **Extract and fit OH spectrum**: Aperture photometry over >3 sigma continuum region; fit constant continuum plus two velocity components each of two equal-amplitude Gaussians separated by 520 km/s  
  > "we fit the integrated spectrum with a constant continuum flux density and the sum of two OH velocity components, each consisting of a pair of equal-amplitude Gaussian profiles" (Imaging and Spectral Analysis)
   - parameter: systemic component velocity fixed to systemic; vmax = velocity above which 98% of absorption occurs  
  > "We adopt the velocity above which 98% of the absorption occurs" (Imaging and Spectral Analysis)
   - assumption: Higher-frequency doublet component at systemic velocity  
  > "we assign the higher-frequency component of the doublet to the systemic velocity of the galaxy" (main text)
   - fitting: Gaussian fit; sampler not stated  
  > "we fit the integrated spectrum with a constant continuum flux density and the sum of two OH velocity components, each consisting of a pair of equal-amplitude Gaussian profiles" (Imaging and Spectral Analysis)
   - validation: Spectra from two lensed peaks consistent; [CII] profile compared  
  > "we have also verified that the OH absorption spectra extracted from each peak separately are consistent" (Imaging and Spectral Analysis)
3. **Lens modelling of continuum**: Pixellated source reconstruction fitting visibilities with SIE lens, gradient regularization with strength set by maximizing Bayesian evidence, MCMC for lens parameters on upper-sideband continuum  
  > "We determine the best-fit lens parameters through a Markov Chain Monte Carlo (MCMC) sampling algorithm, fitting to the continuum (upper sideband) data." (Lens Modeling Methodology)
   - software: pixellated lens reconstruction tool (Hezaveh et al. 2016)
   - parameter: time averaging up to 3 min with uv separation <10 m  
  > "we average the data in time in intervals of up to 3 min, unless doing so would cause individual visibilities in the average to have Fourier-plane $uv$ coordinates separated by $>$10 m" (ALMA Observations and Data Analysis)
   - assumption: Singular isothermal ellipsoid lens  
  > "We assume a singular isothermal ellipsoid mass profile (cite: kormann94)" (Lens Modeling Methodology)
   - fitting: MCMC; evidence-maximized regularization  
  > "The strength of the regularization is determined by maximizing the Bayesian evidence of the source-plane reconstruction given a set of fixed lens parameters." (Lens Modeling Methodology)
   - validation: Mock point-source tests, regularization variation, continuum realizations  
  > "To test the resolution of the source-plane reconstructions we derive in this work, we ran a series of reconstructions of mock data." (Lens Model Tests)
4. **Reconstruct wind, systemic absorption and continuum maps**: Reconstruct channels -700 to -200 (wind), +300 to +700 km/s (systemic), and -1500 to -1000 km/s (continuum) with fixed best-fit lens parameters; subtract continuum  
  > "We conservatively define the wind and systemic absorption components to include velocities $-700<v<-200$ km s$^{-1}$ and $+300<v<+700$ km s$^{-1}$ relative to the higher-frequency OH transition" (Lens Modeling Methodology)
   - software: pixellated lens reconstruction tool (Hezaveh et al. 2016)
   - fitting: _not stated_
   - validation: Integrated absorption depths consistent with lens reconstructions  
  > "We have verified that the integrated absorption depths of each component in Figure 1 are consistent with the absorption depths and magnifications implied from our lensing reconstructions." (Lens Modeling Methodology)
5. **Derive mass outflow rate**: Optically thin OH column density from wind equivalent width, converted to H2, then thin-shell Mdot = 4 pi R^2 f_cov mu m_H N_H v/R; also scaled via empirical Weq-Mdot correlation  
  > "We used the time-averaged thin-shell approximation of (cite: rupke05) to calculate the molecular mass outflow rate" (Mass Outflow Rate Determination)
   - parameter: f_cov ~0.8, R ~600 pc, v = 440 km/s  
  > "the wind material is at a typical distance comparable to the galaxy continuum-emitting size, $\sim$600 pc, and use the mean wind velocity 440 km s$^{-1}$" (Mass Outflow Rate Determination)
   - assumption: Tex = Tdust = 100 K; OH/H2 = 5e-6; mu = 1.36  
  > "We assume $T_{\rm{ex}} = \ensuremath{T_{\rm{dust}}}= 100$ K as found for high-velocity OH winds in the literature" (Mass Outflow Rate Determination)
   - fitting: _not stated_
   - validation: Uncertainty at least factor 2, up to 10 acknowledged  
  > "We stress again that both estimates carry large systematic uncertainties of at least a factor of 2, possibly rising to a factor of 10" (Mass Outflow Rate Determination)

## Software

- **CASA** : ALMA Cycle 4 pipeline reduction  
  > "The data were reduced using the standard ALMA Cycle 4 pipeline in CASA (cite: mcmullin07)" (ALMA Observations and Data Analysis)
- **CIGALE** : SED fits yielding AGN fraction limit  
  > "more complex models (using, e.g., CIGALE; (cite: burgarella05; noll09))" (Target Selection)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Systemic OH FWHM | 330 | ±80 | km/s | 2 | / FWHM / $330 \pm 80$ km s$^{-1}$   / |
| Outflow centre velocity | -440 | ±50 | km/s | 2 | / Center velocity      / $-440 \pm 50$ km s$^{-1}$  / |
| Outflow maximum velocity | -800 | ±110 | km/s | 2 | we find $\ensuremath{v_{\rm{max}}}= -800 \pm 110$ km s$^{-1}$ |
| Outflow equivalent width (single line) | 64 | ±14 | km/s | 2 | / Equivalent Width\*   / $64 \pm 14$ km s$^{-1}$    / |
| Continuum level | 52.1 | ±0.5 | mJy | 2 | / Continuum level      / $52.1 \pm 0.5$ mJy         / |
| Magnification | 5.8 | not stated | dimensionless | 3 | with flux density $S_{\mathrm{400GHz}} =$9.0 mJy magnified by a factor $\mu = 5.8$ |
| Minimum mass outflow rate (optically thin) | 60 | not stated | Msun/yr | 5 | we find a minimum mass outflow rate $\ensuremath{\dot M_{\rm{out}}}\gtrsim 60$ $\rm{M}_\odot$ yr$^{-1}$ |
| Likely mass outflow rate | 510 | factor ≥2 systematic | Msun/yr | 5 | is $\ensuremath{\dot M_{\rm{out}}}\sim 510$ $\rm{M}_\odot$ yr$^{-1}$ |
| Wind covering fraction | 80% | not stated | percent | 4 | 80% of pixels with continuum signal-to-noise $>8$ have significant wind absorption |
| Outflow mass | 7e8 | not stated | Msun | 5 | the total outflow mass is $\sim7\times10^8$ $\rm{M}_\odot$ |
| Escape fraction | ~10% | not stated | percent | 5 | $\sim$10% of the outflowing material will escape SPT2319$-$55 |

## Qualitative findings

- Wind resolved into multiple clumps separated by ~2.5 resolution elements; continuum is a single ~1.2 kpc region  
  > "it is clustered into multiple clumps, separated from each other by a few hundred parsecs, corresponding to $\approx$2.5 FWHM resolution elements" (main text)

## Claim tuples

- H: A molecular outflow is present in SPT2319-55 | E: Band 8 OH 119 um doublet spectrum fit | R: Blueshifted absorption at -440±50 km/s with vmax ~ -800 km/s | F: A fast molecular wind is detected | **supported**
- H: The wind is spatially complex and clumpy | E: Pixellated lens reconstruction of wind absorption with mock-data tests | R: Multiple clumps, 80% covering fraction | F: Wind is resolved into clumps, not artifacts | **supported**
- H: Outflow rate is comparable to SFR | E: Optically thin limit and empirical OH equivalent width correlation | R: Mdot ≳60 to ~510 Msun/yr vs SFR 790 | F: Mass loading ~0.7, within factor of two of SFR | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Lens modelling needed for intrinsic structure of lensed source  
  > "we determine its intrinsic structure using a lens modeling technique that represents the galaxy as an array of pixels" (main text)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass outflow rates highly uncertain (optical depth, geometry, OH abundance)  
  > "The mass outflow rates derived in this section should be considered highly uncertain." (Mass Outflow Rate Determination)
- Limitation (authors): Bimodal lens solution  
  > "There is a bimodal solution in the lens parameters" (Lens Model Parameters)
- Caveat (inferred, ours): Outflow rate relies on an empirical low-z correlation with large scatter and assumed geometry
- Caveat (inferred, ours): Wind/systemic separation by velocity is not clean
- Caveat (inferred, ours): Continuum and line were not fit jointly in lens model
- Caveat (inferred, ours): AGN driving cannot be excluded

## Reproducibility

- Data public (paper): ALMA data archived; reduced products and lens files on GitHub  
  > "Reduced data products, lens tool data files, and lensing reconstructions are provided at <https://github.com/jspilker/s18_outflow>." (Data and Materials Availability)
- Products in archive: _not stated_
- Code: Lens tool data files and reconstructions released; tool itself not stated as released  
  > "Pixelated reconstructions were performed using a lens modeling tool developed by a subset of the authors and additional non-authors." (Data and Materials Availability)
- Missing: Lens reconstruction code availability
- Missing: CASA version and imaging parameters
- Missing: Priors and sampler settings
- Data volume (inferred): ~10-50 GB (one Band 8 execution block, plus [CII] data)
- Score (inferred): 3/5, Data public and products released, but lens code and imaging details are not given in text.
- Rediscovery candidate: no, Requires non-public lens tool and the outflow rate depends on external correlation and assumptions.

## Links

- Method: Hezaveh et al. 2016 (cite: hezaveh16) (Pixellated lens reconstruction method)
- Method: Rupke et al. 2005 (cite: rupke05) (Thin-shell outflow rate)
- Companion: Spilker et al. 2016 (cite: spilker16) (Earlier lens model of this source)
- Companion: Strandet et al. 2016 (cite: strandet16) (Redshift measurement)
- Related: South Pole Telescope survey DSFG sample

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 54,
  "rate": 0.675
 },
 "evidence_ok": true
}
```
