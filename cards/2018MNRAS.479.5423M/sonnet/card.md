# A gap in the planetesimal disc around HD 107146 and asymmetric warm dust emission revealed by ALMA

`2018MNRAS.479.5423M` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Marino, S. | arXiv: 1805.01915 | DOI: 10.1093/mnras/sty1790

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks
- Question: What is the radial structure of the HD 107146 debris disc (gap, inner warm emission), and can planets explain the gap?  
  > "These observations resolve the broad debris disc around this system at higher sensitivity and resolution than the data presented by (cite: Ricci2015), which showed tentative evidence of a gap as commented above." (Introduction)
- Target **HD 107146**: coordinates _not stated_; z/distance 27.5±0.3 pc  
  > "an $\sim80-200$ Myr old G2V star (cite: Williams2004) at a distance of $27.5\pm0.3$ pc (cite: Gaiamission; Gaiadr1)" (Introduction); distance from Gaia (Gaiamission; Gaiadr1)  
  > "an $\sim80-200$ Myr old G2V star (cite: Williams2004) at a distance of $27.5\pm0.3$ pc (cite: Gaiamission; Gaiadr1)" (Introduction)

## Data provenance

- ALMA projects: 2016.1.00104.S, 2016.1.00195.S
- bands: Band 7 (0.86 mm) 12m+ACA; Band 6 (1.1 mm) 12m  
  > "Band 7 observations were carried out between October and December 2016 (see Table [\[tab:obs\]](#tab:obs)) both using the 12m array and the Atacama Compact Array (ACA)" (2 Observations)
- frequencies and spectral setup: Band 6: four 2 GHz SPWs at 253.60, 255.60, 269.61, 271.61 GHz; Band 7: SPWs at 343.13, 357.04 (2 GHz), 345.03, 355.14 GHz (1.875 GHz, 0.976 MHz resolution)  
  > "The correlator was set up with four spectral windows centered at 253.60, 255.60, 269.61 and 271.61 GHz with 2 GHz bandwidths and 15.625 MHz spectral resolution." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Band 6 12m 41-312 m; Band 7 12m 48-410 m; ACA 9-44 m (5th-95th percentiles)  
  > "with baselines ranging from 41 to 312 m (5th and 95th percentiles)" (2 Observations)
- angular resolution: Natural-weight beams 0.80"x0.79" (B6), 0.58"x0.47" (B7); ~22 au and 15 au  
  > "The band 6 and band 7 synthesised beams have dimensions of $0.80\ensuremath{''}\times0.79\ensuremath{''}$ and $0.58\ensuremath{''}\times0.47\ensuremath{''}$" (2.1 Continuum)
- max recoverable scale: _not stated_
- sensitivity: rms 6.3 (B6) and 27 (B7) uJy/beam at centre  
  > "These maps have a rms of 6.3 and 27 $\mu$Jy beam$^{-1}$ at the center" (2.1 Continuum)
- time on source: Band 6 236 min; Band 7 184 min (49 12m, 135 ACA)  
  > "The total time on source for band 6 was 236 min, and 184 min for band 7 (49 and 135 min for the 12m array and ACA, respectively)." (2 Observations)
- observing dates: Band 7: Oct-Dec 2016 (12m 11 Dec 2016), ACA also Mar/Apr 2017; Band 6: April 2017  
  > "Band 6 observations were carried out in April 2017" (2 Observations)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (not stated)
- Line: HCN J=4-3 (not stated)
- External data: Previous ALMA band 6 total flux and CO J=2-1 upper limit 40 mJy km/s, gap/disc model  
  > "including also the 40 mJy km s$^{-1}$ upper limit for CO J=2-1 from (cite: Ricci2015)" (4.5 Gas non detections) [from (cite: Ricci2015)]
- External data: Warm dust ~120 K at 5-15 au from Spitzer/22 um excess  
  > "at a temperature of $\sim$120 K and thus inferred to be located between 5-15 au from the star (cite: Morales2011; Kennedy2014)" (Introduction) [from (cite: Morales2011; Kennedy2014)]
- Simulation/model as data: REBOUND/MERCURIUS N-body simulations of planet(s) in a planetesimal disc, compared with visibilities  
  > "we use the N-body software package REBOUND (cite: rebound), using the hybrid integrator MERCURIUS" (3.2 N-body simulations)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "Calibrations were applied using the pipeline provided by ALMA and CASA 4.7." (2 Observations)
- casa version: CASA 4.7  
  > "Calibrations were applied using the pipeline provided by ALMA and CASA 4.7." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1229+0203 (12m); Titan (ACA)  
  > "| Band 6 - 12m | 24, 27-30 Apr 2017 | 236.4 | 6.8 | $0.67\ensuremath{''}\times0.66\ensuremath{''}$ ($-2.9\ensuremath{^\circ}$) | 41 and 312 | J1229+0203 | J1229+0203 | J1215+1654 |" (Table 1)
- flux scale uncertainty: 10% absolute  
  > "(including 10% absolute flux uncertainties)" (2.1 Continuum)
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA 4.7; NTERMS=2 for spectral index map  
  > "Continuum maps at band 6 and 7 are created using the CLEAN task in CASA 4.7" (2.1 Continuum)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We adopt natural weighting for band 6 and 7 (12m+ACA combined) for a higher signal to noise." (2.1 Continuum)
- uv taper: 0.8" outer taper for band 7 residual dirty maps  
  > "plus an outer taper of $0.8\ensuremath{''}$ for band 7" (3.1 Parametric model)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: maps primary-beam corrected  
  > "as the maps are corrected by the primary beam" (2.1 Continuum)
- array combination: Band 7 12m+ACA combined  
  > "natural weighting for band 6 and 7 (12m+ACA combined)" (2.1 Continuum)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Radial profile via azimuthal averaging over ellipses  
  > "computed by azimuthally averaging the disc emission over ellipses as in (cite: Marino2016; Marino2017etacorvi; Marino201761vir)" (2.1 Continuum) [from (cite: Marino2016; Marino2017etacorvi; Marino201761vir)]
- Visibility-fitting parametric method  
  > "which we fit directly to the observed visibilities as in (cite: Marino2016; Marino2017etacorvi; Marino201761vir)" (3.1 Parametric model) [from (cite: Marino2016; Marino2017etacorvi; Marino201761vir)]
- Matched filter CO search  
  > "applying a matched filter technique (cite: Matra2015; Marino2016; Marino2017etacorvi; Matra2017fomalhaut)" (2.2 CO J=3-2 and HCN J=4-3) [from (cite: Matra2015; Marino2016; Marino2017etacorvi; Matra2017fomalhaut)]
- Eccentric disc parametrization  
  > "using the same parametrization as in (cite: Marino2017etacorvi)" (3.1.1 Disc global eccentricity) [from (cite: Marino2017etacorvi)]
- Non-LTE CO code  
  > "we use the code developed by (cite: Matra2018)" (4.5 Gas non detections) [from (cite: Matra2018)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction method for the CO/HCN cubes
- Cell size, image size, clean threshold and masking
- Values of the visibility re-weighting factors
- MCMC walker number, steps and burn-in
- Exact dust-opacity files and RADMC-3D setup
- Stellar SED/photometry used for the SED model
- Channel width used in matched filter

## Analysis recipe

1. **Continuum imaging and fluxes**: CLEAN natural weighting; integrate flux in elliptical mask; radial profile and NTERMS=2 spectral index map  
  > "We compute the total flux by integrating the disc emission inside an elliptical mask with a 180 au semi-major axis" (2.1 Continuum)
   - software: CASA
   - fitting: _not stated_
   - validation: Band 6 flux consistent with Ricci et al. 2015, so no flux loss  
  > "thus proving that our band 6 observations do not suffer from flux loss or miss large scale structure" (2.1 Continuum)
2. **CO and HCN upper limits**: Keplerian matched filter over disc mask  
  > "we assume a stellar mass of 1 $M_{\ensuremath{\odot}}$, inclination of $19\ensuremath{^\circ}$, PA of $153\ensuremath{^\circ}$" (2.2 CO J=3-2 and HCN J=4-3)
   - software: CASA
   - parameter: radii 40-150 au  
  > "deprojected minimum and maximum radii of 40 and 150 au, respectively" (2.2 CO J=3-2 and HCN J=4-3)
   - fitting: _not stated_
   - validation: both rotation directions give similar limits  
  > "Note that we consider the two possible directions of the rotation, obtaining similar limits." (2.2 CO J=3-2 and HCN J=4-3)
3. **Parametric visibility fit**: Triple power law + Gaussian gap disc, RADMC-3D images, FFT to model visibilities at observed uv points  
  > "We then use these images to compute model visibilities at the same *uv* points as the 12m band 6, 12m band 7 and ACA band 7 observations" (3.1 Parametric model)
   - software: RADMC-3D, emcee, CASA
   - parameter: 19 free parameters; h>0.03 prior  
  > "In total, our model has 19 parameters, 10 for the density distribution and 9 for the disc centre, orientation, and spectral index." (3.1 Parametric model)
   - assumption: Dust: 70% astrosilicate, 15% amorphous carbon, 15% water ice; size slope -3.5, 1 um-1 cm; 1.5 cm2/g at 1.1 mm; star 1 Msun, 5750 K, 1 Rsun  
  > "This translates to a dust opacity of 1.5 cm$^2$ g$^{-1}$ at 1.1 mm." (3.1 Parametric model)
   - fitting: emcee affine-invariant ensemble sampler; likelihood exp(-chi2/2), uniform priors, constant reweighting per dataset so reduced chi2~1  
  > "The posterior probability distribution is defined as the product of the likelihood function (proportional to $\exp[-\chi^{2}/2]$) and prior distributions which we assume uniform" (3.1 Parametric model)
   - validation: Binned deprojected visibilities and dirty residual maps  
  > "A more intuitive way to study the goodness of fit of our model is to look at the dirty map of the residuals." (3.1 Parametric model)
4. **Inner component and eccentricity fits**: Add 2D Gaussian polar inner component (5 extra params); fit global eccentricity  
  > "we add an extra inner component by introducing five additional parameters to our reference parametric model" (3.1.2 Inner component)
   - software: emcee, RADMC-3D, CASA
   - fitting: _not stated_
   - validation: Residuals below 3 sigma; UVMODELFIT cross-check of flux  
  > "We also measured the integrated flux of the inner component using the task UVMODELFIT in CASA 4.7" (Footnote 5)
5. **N-body gap modelling**: REBOUND MERCURIUS with 10^4 particles, planet at 80 au, masses 10-100 Mearth, scaled and fit to visibilities with MCMC at 50, 100, 200 Myr  
  > "We run a set of simulations with planet masses varying from 10 to 100 $M_{\ensuremath{\oplus}}$ with a 5 $M_{\ensuremath{\oplus}}$ spacing." (3.2 N-body simulations)
   - software: REBOUND, emcee
   - assumption: Massless particles; flat disc  
  > "we assume particles have zero or a negligible mass" (3.2 N-body simulations)
   - fitting: MCMC over amin, amax, gamma, planet a and mass  
  > "we explore the parameter space using the same MCMC technique as in §[3.1]" (3.2 N-body simulations)
   - validation: Linear scaling tested with 75 au simulations  
  > "These three new simulations show that the linear scaling is a reasonable approximation" (Linear scaling of semi-major axis)
6. **Gas mass limits**: non-LTE CO excitation for upper limit; LTE for HCN  
  > "In the absence of a tool to calculate the population of rotational levels for HCN, we estimate a mass upper limit assuming LTE." (4.5 Gas non detections)
   - software: RADMC-3D
   - assumption: Representative radius 80 au; collisional partners electrons; dust T 30-50 K  
  > "We choose 80 au as the representative radius, which is approximately the middle radius of the disc" (4.5 Gas non detections)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7: Calibration, CLEAN imaging, STATWT, UVMODELFIT  
  > "created using the CLEAN task in CASA 4.7" (2.1 Continuum)
- **RADMC-3D** : Dust temperature and model images  
  > "We solve for the dust equilibrium temperature and compute images at 0.86 and 1.13 mm using RADMC-3D" (3.1 Parametric model)
- **emcee** : MCMC sampling  
  > "we sample the parameter space using the PYTHON module EMCEE" (3.1 Parametric model)
- **REBOUND** : N-body simulations (MERCURIUS integrator)  
  > "we use the N-body software package REBOUND (cite: rebound)" (3.2 N-body simulations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total flux band 6 (1.1 mm) | 16.1 | 1.6 | mJy | 1 | We find a total flux of $16.1\pm1.6$ and $34.4\pm3.5$ mJy at 1.1 and 0.86 mm |
| Total flux band 7 (0.86 mm) | 34.4 | 3.5 | mJy | 1 | We find a total flux of $16.1\pm1.6$ and $34.4\pm3.5$ mJy at 1.1 and 0.86 mm |
| Integrated spectral index | 2.64 | 0.48 | dimensionless | 1 | leading to a spatially unresolved millimetre spectral index of $2.64\pm0.48$ |
| CO J=3-2 3sigma upper limit | 74 | not stated | mJy km/s | 2 | we obtain an integrated line flux $3\sigma$ upper limit of 74 mJy km s$^{-1}$ |
| HCN J=4-3 3sigma upper limit | 91 | not stated | mJy km/s | 2 | we place a $3\sigma$ upper limit of 91 mJy km s$^{-1}$ |
| Disc dust mass | 0.250 | 0.004 | Mearth | 3 | / $M_\mathrm{d}$ \[$M_{\ensuremath{\oplus}}$\]  / $0.250\pm0.004$  |
| Disc inner radius | 46.6 | +1.4/-1.5 | au | 3 | / $r_{\min}$ \[au\]                             / $46.6^{+1.4}_{-1.5}$ |
| Disc outer radius | 135.6 | +1.1/-1.2 | au | 3 | / $r_{\max}$ \[au\]                             / $135.6^{+1.1}_{-1.2}$ |
| Gap radius | 75.5 | +1.1/-1.2 | au | 3 | / $r_\mathrm{g}$ \[au\]                         / $75.5^{+1.1}_{-1.2}$ |
| Gap FWHM | 38.6 | +4.5/-3.6 | au | 3 | / $w_\mathrm{g}$ \[au\]                         / $38.6^{+4.5}_{-3.6}$ |
| Gap fractional depth | 0.52 | +0.03/-0.02 | dimensionless | 3 | / $\delta_\mathrm{g}$                           / $0.52^{+0.03}_{-0.02}$ |
| Disc inclination | 19.3 | 1.0 | deg | 3 | $19.3\pm1.0$ |
| Global eccentricity | <0.03 | 2 sigma upper limit | dimensionless | 4 | with a 2$\sigma$ upper limit of 0.03 for the forced eccentricity |
| Inner component dust mass | 3.0e-3 | +0.9/-0.6 e-3 | Mearth | 4 | $3.0^{+0.9}_{-0.6}\times10^{-3}$ M$_\oplus$ |
| Inner component flux 0.86 mm | 0.82 | 0.14 | mJy | 4 | $0.82\pm0.14$ and $0.31\pm0.04$ mJy at 0.86 and 1.1 mm |
| Best-fit single planet mass | 30 | 5 | Mearth | 5 | We find a best fit mass of $30\pm5$ M$_\oplus$ and semi-major axis of $77\pm1$ au |
| CO gas mass upper limit | 5e-6 | not stated | Mearth | 6 | Overall, the CO gas mass must be lower than $5\times10^{-6}$ M$_\oplus$. |

## Qualitative findings

- Inner emission is asymmetric, offset from star by ~0.5" (15 au), consistent with warm dust  
  > "a peak intensity that is significantly offset from the star by $0.5\ensuremath{''}$ (15 au)" (Conclusions)

## Claim tuples

- H: Does the disc have a broad gap? | E: Parametric visibility fit with Gaussian gap | R: Gap at ~75 au, FWHM ~39 au, depth ~50% | F: Broad shallow gap in planetesimal disc | **supported**
- H: Can a single planet on circular orbit explain the gap? | E: N-body fits to visibilities | R: Best 30 Mearth planet gives too narrow/deep gap | F: Needs multiple low-mass planets or a migrating planet | **supported**
- H: Is there inner warm dust emission? | E: Residual imaging and extra component fit; SED check | R: Offset asymmetric emission peaking ~19 au | F: Likely asymmetric warm belt; background galaxy unlikely | **supported**
- H: Is gas present? | E: Matched filter for CO and HCN | R: Non-detections | F: Gas too little to affect dust | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Pearce et al. scattered-planet secular gap disfavoured by axisymmetry  
  > "The fact that the disc emission is consistent with being axisymmetric disfavours the scenario in which a planet is scattered out from the inner regions" (2.1 Continuum)
- How they decided it was enough: _not stated_
- Limitation (authors): HCN limit assumes LTE and could be much higher  
  > "Note that this HCN upper limit could be much higher due to non-LTE effects" (4.5 Gas non detections)
- Caveat (inferred, ours): Gaussian gap parametrization is simple; deviations beyond 150 kλ
- Caveat (inferred, ours): Dust opacity affects mass
- Caveat (inferred, ours): Planet mass derived assuming massless particles and fixed 80 au scaling

## Reproducibility

- Data public (paper): Project codes given; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00104.S and 2016.1.00195.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Reweighting factors, MCMC settings, imaging parameters, line-free channels
- Data volume (inferred): ~100-300 GB raw for two projects
- Score (inferred): 3/5, Data identified and model well described, but many fitting and imaging settings unstated and heavy modelling.
- Rediscovery candidate: no, Several essential settings are missing and modelling is complex.

## Links

- Method: (cite: Marino2017etacorvi) (Visibility fitting and eccentricity method)
- Method: (cite: Matra2018) (Non-LTE CO code)
- Companion: (cite: Ricci2015) (Earlier ALMA observation of HD 107146)

## Checks

```json
{
 "quotes": 79,
 "quotes_ok": 79,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 53,
  "rate": 0.654
 },
 "evidence_ok": true
}
```
