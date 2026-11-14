# 1.3-mm ALMA observations of the Fomalhaut debris system

`2017MNRAS.466.4201W` | Monthly Notices of the Royal Astronomical Society 2017 | first author: White, Jacob Aaron | arXiv: 1612.01648 | DOI: 10.1093/mnras/stw3303

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks, stellar_physics
- Question: What is the 1.3 mm morphology of Fomalhaut's debris ring, its mm spectral index and grain size slope, and is there central emission in excess of the stellar photosphere indicating an inner debris component?  
  > "The observations are thus able to address whether there is indeed excess over the stellar emission, constraining the presence of an inner debris disc or ring." (1 Introduction)
- Target **Fomalhaut**: coordinates RA 22h57m39.44s, Dec -29d37m22.64s (J2000)  
  > "Observations were centred on Fomalhaut using J2000 coordinates RA = 22 h 57 min 39.44 s and $\delta = -29^{\circ} 37' 22.64''$." (2 Observations); "Located at a distance of $7.66 \pm 0.04$ pc (cite: hipparcos)" (1 Introduction); z/distance 7.66 +/- 0.04 pc  
  > "Observations were centred on Fomalhaut using J2000 coordinates RA = 22 h 57 min 39.44 s and $\delta = -29^{\circ} 37' 22.64''$." (2 Observations); "Located at a distance of $7.66 \pm 0.04$ pc (cite: hipparcos)" (1 Introduction); distance from Hipparcos (van Leeuwen 2007)  
  > "Observations were centred on Fomalhaut using J2000 coordinates RA = 22 h 57 min 39.44 s and $\delta = -29^{\circ} 37' 22.64''$." (2 Observations); "Located at a distance of $7.66 \pm 0.04$ pc (cite: hipparcos)" (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.00486.S
- bands: Band 6 (~233 GHz, 1.3 mm)  
  > "The observations were taken in band 6 (at $\sim233$ GHz)" (2 Observations)
- frequencies and spectral setup: TDM, dual polarization, 4 spws of 2 GHz at 224, 226, 240, 242 GHz, 128 channels of 15.625 MHz  
  > "Four different spectral windows were used with 2 GHz bandpasses at rest frequency centres of 224, 226, 240, and 242 GHz." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 34 antennas, longest baseline 1.1 km  
  > "A 34-antenna configuration was used; the longest baseline was 1.1 km." (2 Observations)
- baselines: _not stated_
- angular resolution: 0.329 x 0.234 arcsec, PA 83.6 deg  
  > "The size of the synthetic beam is $0.329 \times 0.234$ arcsec at a position angle of 83.6$^{\circ}$." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: 17 uJy  
  > "The observations achieve a sensitivity of 17 $\mu$Jy" (abstract)
- time on source: three EBs, average integration time 1.08 hr  
  > "The average integration time was 1.08 hr." (2 Observations)
- observing dates: 2015 June 11 to 2015 September 21  
  > "Observations were made in three execution blocks (EBs) taking place between 2015 June 11$^{\rm th}$ and 2015 September 21$^{\rm st}$." (2 Observations)
- pi or archival as stated: _not stated_
- External data: Literature disc and stellar flux densities 70 um-6.6 mm and 0.554-24 um used in SED and spectral index fits (Table flux_list)  
  > "with literature values for flux densities at different wavelengths (see Table [\[flux_list\]](#flux_list))." (4 SED Modelling) [from Ricci 2012, Boley 2012, Su 2016, Holland 2003/1998, Acke 2012, Ishihara 2010, Pickles 2010, Boyajian 2013]
- External data: Stellar photosphere temperature 8600 +/- 200 K  
  > "The photosphere temperature of the star is constrained to be T$_{B} = 8600 \pm200$ K from *Herschel* observations (cite: acke)." (4.1) [from (cite: acke)]

## Processing

### Calibration

- pipeline or manual: CASA reduction: WVR, Tsys, bandpass, flux, phase calibration  
  > "The data reduction in CASA included WVR calibration; system temperature corrections; and bandpass, flux, and phase calibrations with Ceres and quasar J2258-2758." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres (flux), J2258-2758 (bandpass)  
  > "Ceres and quasar J2258-2758 were used for absolute flux and bandpass calibration, respectively." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN  
  > "This 233 GHz continuum image was produced by CASA’s *CLEAN* algorithm using threshold of $\frac{1}{2}~ \sigma_{\rm RMS}$ and natural weighting." (2 Observations)
- deconvolver: _not stated_
- weighting robust: natural  
  > "using threshold of $\frac{1}{2}~ \sigma_{\rm RMS}$ and natural weighting" (2 Observations)
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

- Model generation approach for debris ring (particles, thermal equilibrium grains)  
  > "Models are generated using the same approach as in (cite: white) and assume a flat prior distribution." (3 Debris Disc Modelling) [from (cite: white)]
- Image-plane MCMC fitting method  
  > "We carry out the MCMC modelling in the image plane based on the method described in (cite: booth)." (3.1 Image Plane) [from (cite: booth)]
- alpha_pl=1.84 and beta_s=1.8 adopted  
  > "Following (cite: ricci), we adopt $\alpha_{pl} = 1.84 \pm 0.02$ and $\beta_{s} = 1.8 \pm 0.2$." (4 SED Modelling) [from (cite: ricci)]

### Not stated but needed to reproduce (our reading)

- Image size and cell size for CLEAN
- Whether pipeline or manual calibration and CASA version
- Flux scale uncertainty treatment (calibration uncertainty inflating 0.12 vs 0.15 mJy)
- MCMC proposal widths and initial parameter values, prior ranges
- Mapping of image-plane sigma and treatment of primary beam in the fits
- Code for the ring model is not provided

## Analysis recipe

1. **Image continuum**: CASA CLEAN of 233 GHz continuum, natural weighting, threshold 0.5 sigma  
  > "This 233 GHz continuum image was produced by CASA’s *CLEAN* algorithm using threshold of $\frac{1}{2}~ \sigma_{\rm RMS}$ and natural weighting." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Image-plane MCMC ring + point source fit**: Model attenuated by primary beam, convolved with synthetic beam, compared to dirty image with chi^2; Metropolis-Hastings  
  > "The model is attenuated by the primary beam and then convolved with the synthetic beam (the sampling function)." (3.1 Image Plane)
   - software: CASA
   - parameter: 3 chains, 100000 links, thinned by 10, sigma = 374 uJy  
  > "The MCMC routine is run with 3 separate chains for a total of 100000 links (minus about 1000 each for burn-in)." (3.1 Image Plane)
   - assumption: Gaussian radial profile, vertical Gaussian width 1 deg, point source at phase centre  
  > "we assume that the vertical profile of the debris is Gaussian with a width of $1^\circ$" (3 Debris Disc Modelling)
   - fitting: Metropolis-Hastings, flat priors, 95% credible interval  
  > "parameter space is explored using a random walk directed by a Metropolis-Hastings MCMC (cite: ford)" (3 Debris Disc Modelling)
   - validation: ACF negligible for lags <=50; chains converge  
  > "The ACF becomes negligible for lags of 50 or less for all thinned chains." (3.1 Image Plane)
3. **Visibility-plane MCMC fit**: Predict model visibilities with setvp/predict and chi^2 on real and imaginary parts with weights  
  > "used to “predict” the visibilities that the model would have for the actual array configuration and (u,v) coordinates using the tasks *setvp* and *predict*." (3.2 Visibility Plane)
   - software: CASA
   - parameter: 10 chains, 100000 links, acceptance ~26%  
  > "The MCMC routine is run with 10 separate chains for a total of 100000 links (minus about 1000 each for burn-in)." (3.2 Visibility Plane)
   - fitting: Metropolis-Hastings, flat priors, 95% credible intervals  
  > "Uncertainties are given by a $95\%$ credible interval around the most probable value." (3.2 Visibility Plane)
   - validation: Best model and data CLEANed, residuals inspected; compared with image-plane fit  
  > "The data and best fit model are then deconvolved and imaged using the CASA CLEAN algorithm." (3.2 Visibility Plane)
4. **Eccentricity and mass estimates**: e from de-projected offsets over semi-major axis; mass from grain size distribution q=3.5  
  > "the ring’s eccentricity can be calculated from the best fit semi-major axis and the X and Y offsets of the ellipse centre" (3.4)
   - assumption: density 2.5 g/cc for 1.3 mm grains; 1 g/cc, Dmax 50 km for cascade  
  > "Adopting an average density of 2.5$~g~cc^{-1}$, this approach yields a mass of M$_{\rm 1.3\,mm}\sim 0.017~M_{\bigoplus}$." (3.4)
   - fitting: _not stated_
   - validation: _not stated_
5. **Spectral index and grain size slope**: Bayesian MCMC fit of F_nu ∝ nu^alpha to ring fluxes; q=(alpha_mm-alpha_pl)/beta_s+3  
  > "The posterior distribution for the spectral index is determined by performing a Bayesian parameter estimation for $F_\nu$." (4 SED Modelling)
   - assumption: alpha_pl=1.84±0.02 (dust 45±5 K), beta_s=1.8±0.2  
  > "Assuming a dust temperature of $45\pm5$ K yields $\alpha_{pl} = 1.84 \pm 0.02$" (4 SED Modelling)
   - fitting: MCMC, flat prior  
  > "We use an MCMC approach similar to that used for the disc model fitting, incorporating the listed flux uncertainties, and assume a flat prior distribution." (4 SED Modelling)
   - validation: compared with Ricci et al. q and collisional cascade q=3.51  
  > "Both of these results are also consistent with the predicted $q=3.51$" (4 SED Modelling)
6. **Stellar brightness temperature fits**: Bayesian black body fits to subsets of stellar flux data; 10% uncertainty when missing  
  > "For data from literature, when the uncertainty is not given, a 10% uncertainty is used." (Table 3)
   - assumption: Su et al. 870 um flux used rather than Boley  
  > "The $870~\mu$m flux value from (cite: su16) was used in all further analysis." (4.1)
   - fitting: Bayesian black body fit, 95% credible region  
  > "The best fit brightness temperature and 95% credible region are given." (Table 3)
   - validation: _not stated_

## Software

- **CASA** : Calibration, CLEAN imaging, predict visibilities, exportfits  
  > "Data were reduced using the Common Astronomy Software Applications (CASA) package (cite: casa_reference)." (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Ring radius (visibility fit) | 139 | [136,141] 95% | au | 3 | / Centre \[au\]                 / $139$         / $[136, 141]$          / |
| Ring FWHM | 13 | [10,16] 95% | au | 3 | / Width \[au\]                  / $13$          / $[10, 16]$            / |
| Ring flux (visibility) | 30.8 | [27.8,34.2] 95% | mJy | 3 | / Disc Flux \[mJy\]             / $30.8$        / $[27.8, 34.2]$        / |
| Central emission flux | 0.90 | ±0.12 (incl. calibration) | mJy | 3 | with a most probable flux of $0.90\pm 0.12$ mJy (including calibration uncertainties) |
| Inclination | 66.7 | [66.0,67.2] | deg | 3 | / Inclination \[$^{\circ}$\]    / $66.7$        / $[66.0, 67.2]$        / |
| Eccentricity | 0.12 | 0.03 | dimensionless | 4 | which yields an eccentricity of $0.12 \pm0.03$ |
| Spectral index 350-6600 um | -2.73 | 0.13 | dimensionless | 5 | $\alpha_{mm} = -2.73 \pm 0.13$ |
| Grain size slope q (350-6600 um) | 3.50 | 0.14 | dimensionless | 5 | $q = 3.50\pm 0.14$ |
| Stellar brightness temperature from 870-6600 um | 5540 | 3570-7860 | K | 6 | / 870 - 6600            / 5540                  / 3570-7860         / |
| Mass for D<50 km | ~6 | not stated | Earth masses | 4 | we find a total mass of M$(\rm D<50\,km) \sim 6~ M_{\bigoplus}$ |

## Qualitative findings

- No extended structure interior to the ring; central emission is a point source.  
  > "no extended structure is found interior to the main ring" (2 Observations)

## Claim tuples

- H: Is there an inner debris component producing excess central emission? | E: Fit ring + point source; compare central flux with photosphere extrapolation | R: 0.90 mJy, <70% of expected 1.3 mJy | F: No clear evidence for inner debris; stellar mm emission must be understood first | **supported**
- H: Is the mm ring narrow and what is the grain size distribution? | E: Visibility MCMC and SED fit | R: 139 au, FWHM 13 au; q=3.50±0.14 | F: Consistent with steady-state collisional cascade | **supported**
- H: Does image-plane fitting match visibility fitting? | E: Both fits compared | R: Geometry consistent, ring flux differs ~15% | F: Visibility fitting necessary; image-plane for preliminary models | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Power law disc models were not well constrained  
  > "Power law disc models were considered, but were not well constrained in the model fitting." (3.4)
- How they decided it was enough: _not stated_
- Limitation (authors): Ring ansae near primary beam edge, so N/S asymmetries and vertical structure unreliable  
  > "As noted above, the ring ansae are close to the edges of the primary beam. As such, any potential North/South asymmetries are not reliable." (3.4)
- Caveat (inferred, ours): Image-plane chi^2 uses pixel-correlated noise
- Caveat (inferred, ours): Credible intervals for position angle table appear inverted
- Caveat (inferred, ours): Quoted alpha_mm -2.62 vs -2.64 inconsistent
- Caveat (inferred, ours): Stellar contribution at mm depends on assumed photosphere

## Reproducibility

- Data public (paper): ALMA project data acknowledged; archive project given  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA\[2013.1.00486.S\]" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Ring model code
- Missing: CASA version and imaging parameters
- Missing: MCMC step sizes and priors
- Data volume (inferred): ~20-50 GB (3 EBs, 4 TDM spws)
- Score (inferred): 5/5, Public data and clear model description, but custom code and imaging details are missing.
- Rediscovery candidate: yes, Public data, numeric results, model equations given, though code not released.

## Links

- Method: Booth et al. 2016 (cite: booth) (Image-plane MCMC method)
- Method: White et al. 2016 (cite: white) (Ring model and mass method)
- Companion: Boley et al. 2012 (cite: boley) (ALMA 870 um Fomalhaut)
- Companion: Su et al. 2016 (cite: su16) (ALMA 870 um central emission)

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
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
  "facts": 76,
  "stated": 44,
  "rate": 0.579
 },
 "evidence_ok": true
}
```
