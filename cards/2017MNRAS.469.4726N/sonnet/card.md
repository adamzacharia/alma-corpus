# High-resolution ALMA observation of the <SUP>12</SUP>CO(3-2) and 350 GHz continuum emissions of the debris disc of 49 Ceti

`2017MNRAS.469.4726N` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Nhung, P. T. | arXiv: 1701.02131 | DOI: 10.1093/mnras/stx1125

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: debris_disks
- Question: What are the morphology and kinematics of the CO(3-2) gas and 350 GHz dust emission of the 49 Ceti debris disc, and how do they compare with current models?  
  > "We present high resolution ALMA observations of the CO(3-2) and 350 GHz continuum emissions of the debris disc of 49 Ceti, known to be particularly rich in molecular gas in spite of its age." (abstract)
- Target **49 Ceti**: coordinates _not stated_; z/distance 59±1 pc  
  > "surrounding a single A1V star at a distance of 59$\pm$1 pc from the Sun (cite: vanLeuwen2007)" (Introduction); distance from van Leeuwen 2007  
  > "surrounding a single A1V star at a distance of 59$\pm$1 pc from the Sun (cite: vanLeuwen2007)" (Introduction)

## Data provenance

- ALMA projects: 2012.1.00195.S
- bands: 350 GHz continuum and 12CO(3-2)  
  > "CO(3-2) and 350 GHz continuum emissions" (abstract)
- frequencies and spectral setup: 650 velocity bins of 0.053 km/s, -14.6 to 19.8 km/s; spectral resolution 0.1 km/s  
  > "Data cube elements are given in 650 bins of velocity, each 0.053 km s$^{-1}$ wide, covering between $-$14.6 and 19.8 km s$^{-1}$" (Observations and data reduction)
- continuum bandwidth: width of 15.016 MHz, from 342.994 to 358.010 GHz  
  > "continuum (width of 15.016 MHz, from 342.994 to 358.010 GHz)" (Observations and data reduction)
- arrays: 28 antennas  
  > "It used 28 antennas with maximal baseline of 1284.3 m and minimal baseline of 17.3 m." (Observations and data reduction)
- configurations: _not stated_
- baselines: 17.3 m to 1284.3 m  
  > "maximal baseline of 1284.3 m and minimal baseline of 17.3 m" (Observations and data reduction)
- angular resolution: Continuum beam 0.56x0.43 arcsec PA 88.6 deg; CO beam 0.50x0.38 arcsec PA 83.7 deg  
  > "The beam is 0.50$\times$0.38 arcsec$^2$ FWHM with a position angle of 83.7$^\circ$." (Observations and data reduction)
- max recoverable scale: 6.2 arcsec  
  > "the maximal recoverable scale is evaluated to be 6.2 arcsec" (Observations and data reduction)
- sensitivity: continuum rms 0.055 mJy/beam; CO rms 8.8 mJy/beam  
  > "an rms value of 8.8 mJy beam$^{-1}$" (Observations and data reduction)
- time on source: 39 minutes  
  > "during 39 minutes" (Observations and data reduction)
- observing dates: 14 November 2013  
  > "observed by ALMA on 14$^\textrm{th}$ November 2013" (Observations and data reduction)
- pi or archival as stated: PI M. Hughes; data retrieved from JVO portal  
  > "The data are retrieved from the JVO portal (http://jvo.nao.ac.jp/portal) operated by the NAOJ." (Acknowledgements)
- Line: 12CO J=3-2 (345 GHz)
- External data: Distance 59±1 pc  
  > "at a distance of 59$\pm$1 pc from the Sun (cite: vanLeuwen2007)" (Introduction) [from (cite: vanLeuwen2007)]
- External data: CO column density upper limit ~5e12 cm-2 from HST FUV  
  > "the upper limit obtained by (cite: Roberge2014) from FUV HST observations, $\sim$5$\times$10$^{12}$ cm$^{-2}$" (Absorption from a foreground cold cloud) [from (cite: Roberge2014)]
- External data: JCMT CO(3-2) single dish flux 9.5±1.9 Jy km/s  
  > "single dish value of 9.5$\pm$1.9 Jy km s$^{-1}$ obtained by (cite: Dent2005)" (Integrated intensity of the CO(3-2) emission) [from (cite: Dent2005)]
- External data: 0.85 mm flux 8.2±1.9 mJy  
  > "8.2$\pm$1.9 mJy measured by (cite: Song2004) at 0.85 mm wavelength" (Flux density and morphology of the dust emission) [from (cite: Song2004)]

## Processing

### Calibration

- pipeline or manual: Reduced by ALMA staff; authors checked and made no changes  
  > "We have checked the quality of data reduction and found it unnecessary to make changes." (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Yes, products from JVO portal  
  > "The data were reduced by the ALMA staff in 2015 and published on JVO portal" (Observations and data reduction)
- flux calibrator: _not stated_
- flux scale uncertainty: ~10%  
  > "a normalization uncertainty of $\sim$10% associated with the calibration of the absolute flux must be taken in account" (Integrated intensity of the CO(3-2) emission)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.1x0.1 arcsec  
  > "The continuum data are presented in a grid of 360$\times$360 pixels, each 0.1$\times$0.1 arcsec$^2$." (Observations and data reduction)
- image size: 360x360 pixels  
  > "grid of 360$\times$360 pixels" (Observations and data reduction)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CO data are continuum subtracted  
  > "The $^{12}$CO(3-2) data are continuum subtracted" (Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: Primary beam loss ~5% at 2 arcsec; loss approximated by Gaussian FWHM 5.7 arcsec for crude corrections  
  > "The acceptance loss associated with the primary beam is only $\sim$5% at a distance of 2 arcsec from the star" (Observations and data reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Continuum 0.56x0.43 arcsec; CO 0.50x0.38 arcsec  
  > "The beam is 0.56$\times$0.43 arcsec$^2$ FWHM with a position angle of 88.6$^\circ$." (Observations and data reduction)
- final rms: 0.055 mJy/beam continuum; 8.8 mJy/beam CO  
  > "an rms value of 0.055 mJy beam$^{-1}$" (Observations and data reduction)

### Inherited from earlier work

- Gaussian vertical profile choice  
  > "The choice of a Gaussian form follows (cite: Hughes2008) and is not critical" (A simple model of CO(3-2) emission) [from (cite: Hughes2008)]
- Effective emissivity definition  
  > "We define (cite: Diep2016) the effective emissivity $\rho(x,y,z)$ as" (Evidence for central attenuation of the CO(3-2) emission) [from (cite: Diep2016)]
- CO mass from integrated intensity with T=50 K  
  > "assuming a temperature of 50$\pm$10 K as suggested by (cite: Hughes2008)" (Properties of the CO(3-2) emission) [from (cite: Hughes2008)]

### Not stated but needed to reproduce (our reading)

- Exact CASA/pipeline version used by ALMA staff
- Procedure and flux threshold for the clean map and mask
- How the position angle of 17.5 deg was optimized
- Coordinates of the target and phase centre
- Details of the short-spacing correction estimate
- Coefficients used for the CO mass relation

## Analysis recipe

1. **Measure intensity maps and noise**: Gaussian fit of noise; integrated intensity map with 1-sigma cut; rotate frame by 17.5 deg  
  > "we use a frame of reference shifted west by 0.02 arcsec (where the dip in the gas intensity distribution peaks) and rotated clockwise by 17.5$^\circ$" (Morphology)
   - fitting: _not stated_
   - validation: Checked 2- and 3-sigma cuts do not change conclusions  
  > "We have checked that using stronger cuts, such as 2-$\sigma$ and 3-$\sigma$, does not significantly affect any of the conclusions" (Morphology)
2. **Fit Keplerian rotation**: Power-law fit of maximal Doppler velocity vs x along y=0  
  > "Very good fits to the distributions observed for $x$\>0 and $x$\<0 are obtained assuming a power law dependence of the velocity on radius" (Gas kinematics)
   - assumption: Circular orbits  
  > "Assuming circular orbits with velocities independent from azimuth" (Gas kinematics)
   - fitting: _not stated_
   - validation: _not stated_
3. **Solve effective emissivity radial profile**: Integral equation solved stepwise inward from large |x|, assuming optically thin, rotation invariance  
  > "This integral equation is easily solved by steps from large $\lvert x \rvert$ values inward" (Evidence for central attenuation of the CO(3-2) emission)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit phenomenological disc models to CO and continuum**: Model of flared disc with central attenuation (V_z or x dependent), convolved with beam, chi2 jointly on intensity map, mean-velocity map and spectrum  
  > "In practice we minimize $\chi^2 = \chi^2_1+\chi^2_2+\chi^2_3$" (A simple model of CO(3-2) emission)
   - software: MINUIT
   - parameter: Uncertainties: 0.22 km/s on mean velocity; 14.6 mJy/beam km/s plus 10% on intensity  
  > "We use an uncertainty of 0.22 km s$^{-1}$ on the mean Doppler velocities" (A simple model of CO(3-2) emission)
   - fitting: chi2 minimization with MINUIT; uncertainties from 10% increase of chi2  
  > "uncertainties are defined by a 10% increase of $\chi^2$" (Flux density and morphology of the dust emission)
   - validation: Checked uncertainty choices negligible; position-velocity diagrams reproduced  
  > "We checked that these choices have negligible influence on the results." (A simple model of CO(3-2) emission)
5. **Derive intrinsic line width limits**: Subtract Keplerian-shear width from model in quadrature from observed Gaussian widths in |x| intervals  
  > "we subtract in quadrature these Gaussian line widths, meant to account for the Keplerian shear, from the observed line widths" (Optical thickness and line width effects)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **MINUIT** : chi2 minimization (FORTRAN code)  
  > "The minimization of $\chi^2$ is straightforward and uses FORTRAN code MINUIT (cite: James1975)." (A simple model of CO(3-2) emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(3-2) integrated intensity | 7.1 | 0.4 | Jy km/s | 0 | giving 7.1$\pm$0.4 Jy km s$^{-1}$ |
| 350 GHz continuum flux | 11.4 | 0.5 | mJy | 0 | giving 11.4$\pm$0.5 mJy |
| Gas disc inclination | 11.1 | 0.9 | deg | 4 | $11.1\pm0.9$ |
| Dust disc inclination | 11.1 | 1.4 | deg | 4 | $i$=11.1$^\circ\pm$1.4$^\circ$ |
| Rotation velocity at 1 arcsec | 5.1 | 0.1 | km/s | 4 | $5.1\pm0.1$ |
| Power index n | -0.46 | +0.05/-0.02 | dimensionless | 4 | $-0.46^{+0.05}_{-0.02}$ |
| Stellar mass | 1.73 | 0.10 | solar masses | 4 | gives a star mass of 1.73$\pm$0.10 solar masses |
| Gas flaring parameter eta_h | 0.041 | +0.028/-0.019 | rad | 4 | $0.041^{+0.028}_{-0.019}$ |
| Dust flaring parameter eta_h | 0.10 | 0.06 | dimensionless | 4 | $\eta_h$=0.10$\pm$0.06 |
| Intrinsic line width upper limits | 1.4, 1.2, 0.8 | 0.3, 0.2, 0.1 | km/s FWHM | 5 | upper limits to the intrinsic line widths of 1.4$\pm$0.3, 1.2$\pm$0.2 and 0.8$\pm$0.1 km s$^{-1}$ FWHM |
| CO mass | 2.2e-4 | not stated | Earth masses | 0 | translates into a CO mass of 2.2$\times$10$^{-4}$ Earth masses |

## Qualitative findings

- Gas disc is more central, thinner and more homogeneous than the dust disc; CO shows a deficit of emission near systemic velocity.  
  > "the gas disc is more homogeneous, more central and thinner than the dust disc" (abstract)

## Claim tuples

- H: Are gas and dust co-spatial? | E: Compared deprojected morphology of CO and continuum | R: Same PA and inclination (~11 deg); gas FWHM 0.53 vs dust 0.79 arcsec; gas radii 20-210 au, dust 40-280 au | F: Gas and dust discs differ in extent and thickness | **supported**
- H: Is the gas Keplerian? | E: Power-law fit of velocity vs radius, and model fits | R: n=-0.46, V0=5.1 km/s at 1 arcsec | F: Keplerian over ~20-200 au | **supported**
- H: Is there a central CO deficit and is it due to a foreground cold cloud? | E: Emissivity inversion, attenuation models, column density estimate vs HST | R: Required attenuation ~2/3; implied N_CO 8e15 vs HST limit 5e12 | F: Deficit is real, but foreground cloud interpretation rejected | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Image-plane phenomenological modelling with effective emissivity preferred to uv-plane physical modelling  
  > "Such a pragmatic approach favours working in the image plane rather than in the uv plane" (A simple model of CO(3-2) emission)
- Alternative: Foreground cold cloud absorption rejected due to conflict with HST CO column limit  
  > "the interpretation in terms of an absorbing cloud in the foreground cannot be retained as a sensible picture of the observed attenuation" (Absorption from a foreground cold cloud)
- How they decided it was enough: _not stated_
- Limitation (authors): Short-spacing correction crude and unreliable  
  > "The correction for the loss of short spacing cannot be reliably evaluated" (Integrated intensity of the CO(3-2) emission)
- Caveat (inferred, ours): Image-plane fits on moment maps rather than uv or full cube modelling
- Caveat (inferred, ours): Ad hoc attenuation with no physical explanation
- Caveat (inferred, ours): No self-consistent short-spacing treatment
- Caveat (inferred, ours): Error definition via 10% chi2 increase is nonstandard

## Reproducibility

- Data public (paper): Public data from JVO portal  
  > "who are making their data available to the public after a one year period of exclusive property" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Model code not released
- Missing: Exact clean maps and masks
- Missing: Short-spacing correction details
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and simple models, but code and several settings are unstated.
- Rediscovery candidate: no, Model details and ad hoc procedures are insufficiently specified for a reliable redo, though data are public.

## Links

- Method: (cite: Diep2016) (Effective emissivity definition)
- Method: (cite: Hughes2008) (Prior SMA analysis and models)
- Companion: (cite: Hughes2017) (Parallel analysis of the same ALMA data focused on temperature, density and chemistry)

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 46,
  "rate": 0.648
 },
 "evidence_ok": true
}
```
