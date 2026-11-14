# The morpho-kinematics of the circumstellar envelope around the AGB star EP Aqr

`2019MNRAS.484.1865H` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Hoai, D. T. | arXiv: 1901.00974 | DOI: 10.1093/mnras/stz041

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: What are the morphology, kinematics, temperature, density and mass-loss rate of the EP Aqr circumstellar envelope, from separate analysis of the narrow (equatorial) and broad (bipolar) CO components?  
  > "The present work presents a detailed study of the morphology and kinematics of the circumstellar envelope of EP Aqr" (Introduction)
- Target **EP Aqr**: coordinates RA=21h46m31.848s, Dec=-02d12m45.93s (J2000)  
  > "EP Aqr is an oxygen-rich M type AGB star at a distance of only 119$\pm$6 pc from the solar system" (Introduction); "The origin of coordinates at RA=21h46m31.848s and DEC=$-$02$^\circ$12’45.93” corresponds to year 2000." (Observations and data reduction); z/distance 119±6 pc  
  > "EP Aqr is an oxygen-rich M type AGB star at a distance of only 119$\pm$6 pc from the solar system" (Introduction); "The origin of coordinates at RA=21h46m31.848s and DEC=$-$02$^\circ$12’45.93” corresponds to year 2000." (Observations and data reduction); distance from van Leeuwen 2007; Gaia 2018  
  > "EP Aqr is an oxygen-rich M type AGB star at a distance of only 119$\pm$6 pc from the solar system" (Introduction); "The origin of coordinates at RA=21h46m31.848s and DEC=$-$02$^\circ$12’45.93” corresponds to year 2000." (Observations and data reduction)

## Data provenance

- ALMA projects: 2016.1.00026.S
- bands: Band 3 (2.6 mm) CO(1-0) and Band 6 (1.3 mm) CO(2-1)  
  > "we have also observed the continuum emission in the same frequency bands (2.6 mm and 1.3 mm)" (Observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-2 and C40-5, merged in the uv plane  
  > "Both lines were observed in two different configurations, C40-2 and C40-5 and the data were then merged in the *uv* plane." (Observations and data reduction)
- baselines: 19-1124 m (CO 1-0), 15-1400 m (CO 2-1)  
  > "Maximum baseline (m)         |        1124        |        1400" (Table 1)
- angular resolution: Beam 0.78x0.70 arcsec (CO 1-0), 0.33x0.30 arcsec (CO 2-1)  
  > "Beam FWHM (arcsec$^2$)        |  0.78$\times$0.70  |  0.33$\times$0.30" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 98.3 min (CO 1-0), 52.4 min (CO 2-1)  
  > "Time on source (min)         |        98.3        |        52.4" (Table 1)
- observing dates: 30 Oct 2016 to 5 Apr 2017  
  > "between October 30$^{\rm th}$ 2016 and April 5$^{\rm th}$ 2017" (Observations and data reduction)
- pi or archival as stated: Data presented in Nhung et al. 2018a  
  > "were presented in detail in (cite: Nhung2018a)" (Observations and data reduction)
- Line: CO J=1-0 (not stated)
- Line: CO J=2-1 (not stated)
- Other facility **IRAM 30-m**: CO(1-0) short-spacing data merged with ALMA 12-m data  
  > "We also included IRAM 30-m observations of CO(1-0) emission that have been reported in (cite: Winters2007)." (Observations and data reduction)
- External data: IRAM 30-m CO(1-0) map  
  > "We also included IRAM 30-m observations of CO(1-0) emission that have been reported in (cite: Winters2007)." (Observations and data reduction) [from Winters2007]
- External data: Proper motion (24.98, 19.54) mas/yr  
  > "proper motion of (24.98, 19.54) mas/year (cite: vanLeeuwen2007)" (Observations and data reduction) [from vanLeeuwen2007]

## Processing

### Calibration

- pipeline or manual: Calibrated with CASA; no details  
  > "The CO(1-0) and CO(2-1) data have been calibrated using CASA" (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: Mapping with GILDAS  
  > "the mapping was done with GILDAS" (Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: IRAM pseudo-visibilities merged with ALMA 12-m data (CO 1-0 only); ACA/zero spacing absent for CO 2-1  
  > "We then produced a list of pseudo visibilities containing short-spacing information and merged these with the 12-m ALMA data." (Observations and data reduction)
- smoothing: Channels smoothed to 0.2 km/s; regridded to common 0.3x0.3 arcsec pixels in the image plane  
  > "The spectral resolution (channel) has been smoothed to 0.2 km s$^{-1}$" (Observations and data reduction); "we normally use a common pixel size, $0.3\times0.3$ arcsec$^2$" (3.1 General properties)
- final beam: _not stated_
- final rms: Effective noise 6.7 mJy/beam (CO 1-0), 5.8 mJy/beam (CO 2-1)  
  > "effective noise level ($1\sigma$) of 6.7 mJy beam$^{-1}$ for CO(1-0) and 5.8 mJy beam$^{-1}$ for CO(2-1)" (3.1 General properties)

### Inherited from earlier work

- Observations and detailed data description  
  > "were presented in detail in (cite: Nhung2018a)" (Observations and data reduction) [from Nhung2018a]
- De-projection method  
  > "to de-project the effective emissivity following the method developed in (cite: Nhung2018a; Nhung2018b)" (5 The broad component) [from Nhung2018a; Nhung2018b]

### Not stated but needed to reproduce (our reading)

- CASA version and calibrator details
- Cleaning parameters (weighting, robust, threshold, masks) in GILDAS
- Merging weights between IRAM and ALMA
- Code for the narrow/broad separation and de-projection
- Parameters F_J in the absorption model
- Whether archive products were used

## Analysis recipe

1. **Split cube into narrow and broad components**: Per pixel, two 2 km/s control regions 2-4 km/s either side of the peak; linear interpolation gives broad, subtraction gives narrow  
  > "We then interpolate linearly between the two control-regions what we attribute to the broad component, the narrow component being obtained by subtraction." (3.2 Splitting the data cubes)
   - fitting: _not stated_
   - validation: Distributions of interpolated slope and peak velocity offset are well-behaved Gaussians  
  > "We have checked thoroughly that the results are very robust and that the algorithm being used does not produce any significant bias." (3.2 Splitting the data cubes)
2. **Fit velocity vs position angle and radial profiles**: Fit <Vz>=a+b cos(psi-psi0); fit I0 10^(-R/R0) for R>2.5 arcsec  
  > "Fits of the form $<\!\!V_z\!\!>=a+b\cos(\psi-\psi_0)$ are illustrated on the figure" (3.3 Dependence of the Doppler velocity on position angle)
   - assumption: Axis inclination phi=10 deg to line of sight  
  > "The inclination of the star axis with respect to the line of sight is fixed as $\varphi$=10$^\circ$." (5 The broad component)
   - fitting: _not stated_
   - validation: _not stated_
3. **Temperature from CO(2-1)/CO(1-0) ratio**: T = -11.1/ln(R_T/16) per cube element, then fit T(r,alpha)  
  > "$T[{\rm K}] =-11.1/\ln(R_T/16)$ in each data cube element separately" (6.2 Temperature)
   - assumption: Absorption ignored at this stage  
  > "Ignoring absorption, the CO(2-1) and CO(1-0) brightnesses are expected to be in a ratio" (6.2 Temperature)
   - fitting: _not stated_
   - validation: _not stated_
4. **De-project to density, flux of matter and mass-loss rate**: De-project temperature-corrected cubes with V=Veq+(Vpole-Veq)sin^2(alpha); compute dM/dOmega; CO/H~2.5e-4  
  > "Assuming a solar-like abundance ratio, $\rm{CO/H}\sim 2.5\,10^{-4}$, the total mass-loss rate is measured this way to be $0.9\,10^{-7}$ M$_{\odot}$yr$^{-1}$" (6.3 Flux of matter and mass-loss rate)
   - parameter: Veq=1.9 km/s; Vpole=10.3 (blue)/10.7 (red) km/s  
  > "$V_{eq}=1.9$ km s$^{-1}$ and $V_{pole}= 10.3 (10.7)$ km s$^{-1}$ for the blue(red)-shifted part of the spectrum" (6.2 Temperature)
   - fitting: _not stated_
   - validation: Alternative Veq = escape velocity gives very small difference  
  > "The difference with the $V_{eq}$ result is indeed very small" (6.3 Flux of matter and mass-loss rate)
5. **Absorption correction**: Line-of-sight scan in dz=0.004 arcsec steps with attenuation factor; correct f*=f/A; recompute T*, d*  
  > "scanning along the line of sight in small $z$ steps of width $\Delta{z}=0.004$ arcsec" (6.4 Absorption)
   - fitting: _not stated_
   - validation: Radiative transfer with T*, d* reproduces the data cubes  
  > "we reproduce the measured data cubes to excellent precision" (6.5 Results)

## Software

- **CASA** : Calibration  
  > "The CO(1-0) and CO(2-1) data have been calibrated using CASA" (Observations and data reduction)
- **GILDAS** : Mapping, re-centring/resampling IRAM data, merging short spacings  
  > "We used GILDAS to re-centre the map and re-sample velocities" (Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mass-loss rate (absorption corrected) | 1.6e-7 | ±0.4e-7 | Msun/yr | 5 | becomes ($1.6\pm0.4$) $10^{-7}$ M$_\odot$ yr$^{-1}$ |
| Mass-loss rate without absorption | 0.9e-7 | not stated | Msun/yr | 4 | the total mass-loss rate is measured this way to be $0.9\,10^{-7}$ M$_{\odot}$yr$^{-1}$ |
| Equatorial expansion velocity | 1.9 | ±0.2 | km/s | 2 | $1.9\pm0.2$ km s$^{-1}$ |
| Rotation limit |Vrot|/V | <~0.38 | 0.12±0.26 measured | dimensionless | 2 | $V_{rot}/V=0.12\pm0.26$ or, conservatively, in an upper limit of $\sim$0.38 |
| Temperature profile | T*~109 exp(-r/3.1) K | ~25% | K (r in arcsec) | 5 | $T^*\sim109\exp(-r/3.1)$ with $T^*$ in Kelvins and $r$ in arcsec |
| Continuum flux 2.6 mm / 1.3 mm | 4.9 / 17.8 | 0.1 / 0.2 | mJy | 0 | 4.9$\pm$0.1 mJy at 2.6 mm and 17.8$\pm$0.2 mJy at 1.3 mm |
| Velocity modulation amplitude and period | 0.16 km/s, 3.8 arcsec | not stated | km/s; arcsec | 2 | sine wave fit having amplitude of $\pm0.16$ km s$^{-1}$, a period of 3.8 arcsec |

## Qualitative findings

- Broad component emissivity peaks at intermediate latitudes with a polar depression  
  > "causing it to reach maximum at intermediate latitudes of the order of $\sim45$$^\circ$ to 60$^\circ$." (5.4 Summary)

## Claim tuples

- H: Is the spiral enhancement in the equatorial outflow robust? | E: Spiral and circular models fit to intensity and velocity maps of narrow component | R: Spiral fits intensity but not velocity; circles fit velocity not intensity; spiral pitch 4.0 arcsec vs 2.8 arcsec for Homan et al. | F: Spiral evidence is weak and near sensitivity limit | **partially**
- H: What is the mass-loss rate? | E: De-projection, temperature and absorption correction | R: (1.6±0.4)e-7 Msun/yr | F: Roughly constant over past ~2500 yr | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): De-projection is under-determined; models of mass loss cannot be chosen among  
  > "cannot choose among them with confidence" (abstract)
- Caveat (inferred, ours): Assumed inclination 10 deg and velocity law drive the density and mass-loss values
- Caveat (inferred, ours): Absorption/temperature treatment is not a full radiative transfer
- Caveat (inferred, ours): Narrow/broad separation is ad hoc and merges within 2 arcsec

## Reproducibility

- Data public (paper): ALMA project code given  
  > "This paper makes use of the following ALMA data: 2016.1.00026.S." (ACKNOWLEDGEMENTS)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Analysis code
- Missing: Absorption model constants
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Public data and a described method, but imaging details and code are missing, and the de-projection is intricate.
- Rediscovery candidate: no, Recipe incomplete for imaging and de-projection code.

## Links

- Method: Nhung2018a; Nhung2018b (De-projection method)
- Companion: Homan2018 (Independent ALMA analysis with spiral claim)

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 37,
  "rate": 0.529
 },
 "evidence_ok": true
}
```
