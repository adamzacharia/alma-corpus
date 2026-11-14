# Resolved Millimeter Observations of the HR 8799 Debris Disk

`2018ApJ...855...56W` | The Astrophysical Journal 2018 | first author: Wilner, David J. | arXiv: 1803.00054 | DOI: 10.3847/1538-4357/aaacd7

Card schema 1.0 | model gemini-3.8-flash | depth full | type archival_reuse

## Science

- Fields: debris_disks, exoplanets
- Question: What are the structural properties (geometry, radial extent, flux) of the HR 8799 debris disk when combining SMA and archival ALMA observations, and what constraints does the inner edge place on the mass of planet b?  
  > "To better determine the properties of the cold belt of planetesimals in the HR 8799 system, we used the SMA to obtain new observations at 1.3 millimeters wavelength that are sensitive to larger angular scales than the previous millimeter interferometer studies" (1 Introduction)
- Target **HR 8799**: coordinates 23h07m28.72s, +21d08m03.3s  
  > "The phase center was set at $\alpha=23^\text{h}07^\text{m}28.72$, $\delta=+21\ensuremath{^\circ}08\ensuremath{'}03.3\ensuremath{''}$ (J2000), i.e. the J2000 star position uncorrected for interim proper motion." (2.1 Submillimeter Array); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00482.S
- bands: Band 6  
  > "We retrieved observations of HR 8799 from the ALMA archive that were made in Band 6 in 2015 January." (2.2 Atacama Large Millimeter/submillimeter Array)
- frequencies and spectral setup: four spectral windows with width 2 GHz and channel spacing 16 MHz, centered at 216, 218, 231 and 233 GHz  
  > "In brief, the correlator setup consisted of four spectral windows with width 2 GHz and channel spacing 16 MHz, centered at 216, 218, 231 and 233 GHz, respectively." (2.2 Atacama Large Millimeter/submillimeter Array)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 to 349 meters  
  > "The observations included baseline lengths from 15 to 349 meters." (2.2 Atacama Large Millimeter/submillimeter Array)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2015 January (including 2015 January 03)  
  > "We retrieved observations of HR 8799 from the ALMA archive that were made in Band 6 in 2015 January." (2.2 Atacama Large Millimeter/submillimeter Array); "the execution on 2015 January 03 obtained in the best weather conditions dominates the sensitivity budget." (2.2 Atacama Large Millimeter/submillimeter Array)
- pi or archival as stated: archival  
  > "We retrieved observations of HR 8799 from the ALMA archive that were made in Band 6 in 2015 January." (2.2 Atacama Large Millimeter/submillimeter Array)
- Line: CO not stated (not stated)
- Other facility **Submillimeter Array (SMA)**: 1.3 mm observations in subcompact configuration (baselines 6-69 m) providing short-baseline continuum and 12CO / 13CO J=2-1 line data  
  > "We observed the HR 8799 system with the SMA on Mauna Kea, Hawaii, at a wavelength near 1.3 millimeters in the subcompact configuration that provides projected baselines as short as 6 meters." (2.1 Submillimeter Array)
- Other facility **Very Large Array (VLA)**: 9 mm continuum observations in D configuration (baselines 0.04 to 1.03 km)  
  > "We observed the HR 8799 system with the VLA at 9 mm wavelength in the most compact D configuration." (2.3 Very Large Array)
- External data: Details of ALMA Band 6 observations  
  > "Details of these observations are described in (cite: booth16)." (2.2 Atacama Large Millimeter/submillimeter Array) [from (cite: booth16)]
- External data: Semi-major axis of planet b (68 AU) and stellar mass (1.56 M_sun)  
  > "For this calculation, we adopt the planet semi-major axis $a_\text{pl}=68$ AU and stellar mass $M_* = 1.56$ M$_{\odot}$ from dynamical analysis (cite: soummer11), consistent with optical photometry and spectral synthesis (cite: gray99)." (4.2 Dynamical Constraints on the Mass of Planet b) [from (cite: soummer11); (cite: gray99)]

## Processing

### Calibration

- pipeline or manual: pipeline_or_manual using associated reduction scripts  
  > "We calibrated the five individual scheduling block executions using the associated CASA 4.3.1 reduction scripts." (2.2 Atacama Large Millimeter/submillimeter Array)
- casa version: CASA 4.3.1  
  > "We calibrated the five individual scheduling block executions using the associated CASA 4.3.1 reduction scripts." (2.2 Atacama Large Millimeter/submillimeter Array)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: clean  
  > "Imaging was carried out with the clean task in CASA (version 4.7.2)." (2.2 Atacama Large Millimeter/submillimeter Array)
- deconvolver: _not stated_
- weighting robust: natural  
  > "These images were obtained with natural weighting, and those including SMA data use a 4'' FWHM Gaussian taper to improve surface brightness sensitivity at the expense of angular resolution." (3.1 Continuum Emission)
- uv taper: 4'' FWHM Gaussian taper (for images including SMA data)  
  > "These images were obtained with natural weighting, and those including SMA data use a 4'' FWHM Gaussian taper to improve surface brightness sensitivity at the expense of angular resolution." (3.1 Continuum Emission)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ~1.5'' for ALMA image; ~3.8'' for SMA+ALMA combined image  
  > "The ALMA image is comparable to Figure 1 of (cite: booth16), with a beam size of $\sim1.5\ensuremath{''}$" (3.1 Continuum Emission); "In the SMA and ALMA combined image shown with a $\sim3.8\ensuremath{''}$ beam, the two peaks visible on either side of the star are the signatures of limb brightening along the major axis of an inclined and optically thin emission belt." (3.1 Continuum Emission)
- final rms: _not stated_

### Inherited from earlier work

- Visibility fitting procedure and radial power-law belt model  
  > "To provide a quantitative characterization of the 1.3 millimeter emission from the HR 8799 disk, we make the simple assumption that the structure can be represented by an axisymmetric and geometrically thin belt, and we model the observations using the visibility fitting procedure described in (cite: macgregor13)." (3.3 SMA/ALMA Disk Model Fits) [from (cite: macgregor13)]
- Chaotic zone inner edge formula relating disk inner radius to planet mass  
  > "The (cite: pearce14) study formulates a convenient expression for the location of the disk inner edge relative to the width of the chaotic zone, $R_\text{in} = a_\text{pl}+5a_\text{pl}(M_\text{pl}/3M_{*})^{1/3}$, taken in the limit of zero eccentricity." (4.2 Dynamical Constraints on the Mass of Planet b) [from (cite: pearce14)]

### Not stated but needed to reproduce (our reading)

- CASA clean cell size, image size, and threshold/niter used for ALMA and combined imaging
- Specific channels flagged for CO emission in ALMA data

## Analysis recipe

1. **Calibrate and prepare ALMA and SMA visibilities**: Calibrate ALMA SB executions with CASA 4.3.1 reduction scripts, re-weight visibilities with statwt, flag CO line channels, average to 30 s and 2 GHz, and clean in CASA 4.7.2.  
  > "We calibrated the five individual scheduling block executions using the associated CASA 4.3.1 reduction scripts." (2.2 Atacama Large Millimeter/submillimeter Array); "We used the CASA task statwt to homogenize the visibility weights among scheduling blocks and note that the execution on 2015 January 03 obtained in the best weather conditions dominates the sensitivity budget." (2.2 Atacama Large Millimeter/submillimeter Array); "Continuum visibilities were output for analysis after flagging the channels with CO line emission, averaging in time to 30 seconds, and averaging in frequency to 2 GHz bandwidth." (2.2 Atacama Large Millimeter/submillimeter Array)
   - software: CASA
   - parameter: Time averaging: 30 s; frequency averaging: 2 GHz bandwidth  
  > "averaging in time to 30 seconds, and averaging in frequency to 2 GHz bandwidth." (2.2 Atacama Large Millimeter/submillimeter Array)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit parametric belt model to interferometric visibilities**: MCMC sampling of posterior probability distribution using synthetic visibilities generated with vissample from an axisymmetric radial power-law belt model plus an offset point source.  
  > "The surface brightness of the belt is assumed to be a radial power law, $I_\nu \propto r^x$, between an inner and outer radius, $R_\text{in}$ and $R_\text{out}$, respectively." (3.3 SMA/ALMA Disk Model Fits); "For each model image, we calculate synthetic visibilities using vissample... and determine a $\chi^2$ likelihood function, $\text{ln}\mathcal{L} = -\chi^2/2$, that incorporates the statistical weights of the visibilities. We make use of the emcee package" (3.3 SMA/ALMA Disk Model Fits)
   - software: vissample, emcee
   - parameter: 100 walkers, 5,000 steps each (50,000 iterations)  
  > "We explore the posterior with 50,000 iterations ($100$ walkers and $5,000$ steps each) and check that the Gelman-Rubin statistic (cite: gelman14) is $\hat{R}<1.1$ for all parameters to ensure convergence." (3.3 SMA/ALMA Disk Model Fits)
   - assumption: Axisymmetric, geometrically thin, optically thin belt  
  > "we make the simple assumption that the structure can be represented by an axisymmetric and geometrically thin belt" (3.3 SMA/ALMA Disk Model Fits)
   - fitting: MCMC with emcee, log-likelihood ln L = -chi^2 / 2  
  > "determine a $\chi^2$ likelihood function, $\text{ln}\mathcal{L} = -\chi^2/2$, that incorporates the statistical weights of the visibilities. We make use of the emcee package (cite: foreman13) to sample the posterior probability distribution" (3.3 SMA/ALMA Disk Model Fits)
   - validation: Gelman-Rubin convergence check R_hat < 1.1 and inspecting residual images after subtracting model visibilities  
  > "check that the Gelman-Rubin statistic (cite: gelman14) is $\hat{R}<1.1$ for all parameters to ensure convergence." (3.3 SMA/ALMA Disk Model Fits); "The goodness-of-fit is demonstrated by the noise-like residual image." (3.3 SMA/ALMA Disk Model Fits)
3. **Constrain mass of planet b from belt inner edge**: Translate inner edge posterior distribution into planet b mass using Pearce & Wyatt (2014) chaotic zone truncation formula.  
  > "If we adopt the (cite: pearce14) formula, then we can translate the radial location of the inner edge of the millimeter belt, $R_\text{in}= 104_{-12}^{+8}$ AU, directly into a constraint on the mass of the outermost planet b." (4.2 Dynamical Constraints on the Mass of Planet b)
   - parameter: a_pl = 68 AU, M_* = 1.56 M_sun  
  > "For this calculation, we adopt the planet semi-major axis $a_\text{pl}=68$ AU and stellar mass $M_* = 1.56$ M$_{\odot}$ from dynamical analysis (cite: soummer11)" (4.2 Dynamical Constraints on the Mass of Planet b)
   - assumption: Chaotic zone of planet b truncates the planetesimal distribution in the limit of zero eccentricity  
  > "The (cite: pearce14) study formulates a convenient expression for the location of the disk inner edge relative to the width of the chaotic zone, $R_\text{in} = a_\text{pl}+5a_\text{pl}(M_\text{pl}/3M_{*})^{1/3}$, taken in the limit of zero eccentricity." (4.2 Dynamical Constraints on the Mass of Planet b)
   - fitting: _not stated_
   - validation: Comparison with hot-start and warm-start planetary evolutionary models  
  > "This procedure gives $M_\text{pl} = 5.8_{-3.1}^{+7.9}$ M$_{\rm Jup}$ for the planet b mass, compatible with standard planet cooling models" (4.2 Dynamical Constraints on the Mass of Planet b)
4. **Derive millimeter spectral index and grain size distribution power-law index**: Calculate spectral index alpha_mm between 1.3 mm and 9 mm, then calculate q = (alpha_mm - alpha_Pl)/beta_s + 3.  
  > "For HR 8799, we use the best-fit total flux density from the combined SMA and ALMA models at 1.3 millimeters and the VLA flux density measured at 9 millimeters to obtain a millimeter spectral index of $\alpha_\text{mm} = 2.41\pm0.17$." (4.4 Grain Size Distribution); "power-law index $q = (\alpha_\text{mm}-\alpha_\text{Pl})/\beta_s +3$. In this expression, valid for $3<q<4$, $\beta_s$ is the dust opacity power law index in the small grain limit, $1.8\pm0.2$ for interstellar grain materials (cite: draine06), and $\alpha_\text{Pl}$ is the spectral index of the Planck function, $1.92\pm0.10$" (4.4 Grain Size Distribution)
   - parameter: beta_s = 1.8 +/- 0.2, alpha_Pl = 1.92 +/- 0.10, T_dust = 39.7 K  
  > "$\beta_s$ is the dust opacity power law index in the small grain limit, $1.8\pm0.2$ for interstellar grain materials (cite: draine06), and $\alpha_\text{Pl}$ is the spectral index of the Planck function, $1.92\pm0.10$ (the Rayleigh-Jeans limit modified by a small correction factor from the 39.7 K dust temperature assumed for HR 8799)." (4.4 Grain Size Distribution)
   - assumption: Valid for 3 < q < 4  
  > "In this expression, valid for $3<q<4$" (4.4 Grain Size Distribution)
   - fitting: _not stated_
   - validation: Comparison with mean value for 15 debris disks from MacGregor et al. (2016)  
  > "This result is consistent with the weighted mean value of $q = 3.36\pm0.02$ determined by (cite: macgregor16) for a sample of 15 debris disks observed over a similar wavelength range." (4.4 Grain Size Distribution)

## Software

- **CASA** 4.3.1 and 4.7.2: Data calibration scripts (4.3.1), statwt, clean deconvolution, and aperture flux measurement (4.7.2)  
  > "We calibrated the five individual scheduling block executions using the associated CASA 4.3.1 reduction scripts." (2.2 Atacama Large Millimeter/submillimeter Array); "Imaging was carried out with the clean task in CASA (version 4.7.2)." (2.2 Atacama Large Millimeter/submillimeter Array)
- **MIR** : SMA calibration  
  > "All of the basic calibration was performed using standard procedures in the MIR software package." (2.1 Submillimeter Array)
- **vissample** : Generating synthetic visibilities from model images  
  > "For each model image, we calculate synthetic visibilities using vissample, a python package for visibility sampling that improves on the sampling and interpolation of the uvmodel task in the Miriad software package" (3.3 SMA/ALMA Disk Model Fits)
- **emcee** : MCMC sampling of model posterior probability distributions  
  > "We make use of the emcee package (cite: foreman13) to sample the posterior probability distribution of the data conditioned on the model" (3.3 SMA/ALMA Disk Model Fits)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SMA+ALMA Belt inner edge R_in | 104 | +8, -12 | AU | 2 | 104. (+8., -12.) |
| SMA+ALMA Belt outer edge R_out | 361 | +16, -18 | AU | 2 | 361. (+16., -18.) |
| SMA+ALMA Total belt flux density F_belt | 3.44 | +0.31, -0.56 | mJy | 2 | 3.44 (+0.31, - 0.56) |
| SMA+ALMA Surface brightness power law index x | -0.38 | +0.47, -0.47 | dimensionless | 2 | -0.38 (+0.47, -0.47) |
| SMA+ALMA Disk inclination i | 32.8 | +5.6, -9.6 | deg | 2 | 32.8 (+5.6, -9.6) |
| SMA+ALMA Disk position angle PA | 35.6 | +9.4, -10.1 | deg | 2 | 35.6 (+9.4, -10.1) |
| Planet b dynamical mass M_pl | 5.8 | +7.9, -3.1 | M_Jup | 3 | This procedure gives $M_\text{pl} = 5.8_{-3.1}^{+7.9}$ M$_{\rm Jup}$ for the planet b mass |
| VLA 9 mm disk flux density F_9mm | 32.6 | 9.9 | uJy | 0 | The measured total flux density of the disk from our VLA observations is $F_\text{9mm} = 32.6\pm9.9$ $\mu$Jy |
| Millimeter spectral index alpha_mm | 2.41 | 0.17 | dimensionless | 4 | obtain a millimeter spectral index of $\alpha_\text{mm} = 2.41\pm0.17$. |
| Grain size distribution power-law index q | 3.27 | 0.10 | dimensionless | 4 | the resulting grain size distribution power-law index is $q = 3.27\pm0.10$. |

## Qualitative findings

- The 1.3 mm emission morphology is consistent with a broad, axisymmetric, inclined belt without significant azimuthal brightness asymmetries.  
  > "The 1.3 mm emission morphology imaged at $3.8\ensuremath{''}$ (150 AU) resolution is consistent with a broad ($\Delta R/R\gtrsim 1$), axisymmetric, inclined belt centered on the star. These data provide no evidence for the presence of clumps or other azimuthal asymmetries" (5 Conclusions)
- Belt inclination and position angle are consistent with coplanarity and alignment with the planetary orbits.  
  > "These values overlap with estimates of the orbital inclination and angle of ascending node of the planet orbits determined by astrometric observations, and they are consistent with a coplanar configuration of the disk and planetary orbits within the (still large) mutual uncertainties." (5 Conclusions)
- Inner edge location indicates planet b truncates the disk, removing the need to hypothesize an unseen planet beyond planet b.  
  > "Given this result, there is no need to posit the presence of an additional unseen planet orbiting beyond planet b, or variations in the orbit of planet b, to account for the disk truncation." (4.2 Dynamical Constraints on the Mass of Planet b)

## Claim tuples

- H: Does the inner edge of the cold planetesimal belt in HR 8799 truncate near the chaotic zone of planet b without requiring an additional unseen planet? | E: Fit an axisymmetric power-law belt model to combined SMA and archival ALMA 1.3 mm visibilities using MCMC, determine R_in, and apply chaotic zone truncation formula. | R: R_in is measured to be 104 (+8, -12) AU, translating to a planet b mass of 5.8 (+7.9, -3.1) M_Jup. | F: The inner edge is consistent with truncation by planet b, requiring no additional unseen planet. | **supported**
- H: Is the debris disk coplanar and aligned with the orbits of the four directly imaged planets? | E: Compare the disk inclination and position angle from visibility fitting to astrometric orbital determinations. | R: Disk inclination is 32.8 (+5.6, -9.6) deg and PA is 35.6 (+9.4, -10.1) deg, overlapping with orbital inclination 38 +/- 7 deg and ascending node 40 to 70 deg. | F: Disk geometry is consistent with coplanarity and alignment within mutual uncertainties. | **supported**
- H: Does the millimeter spectral index of HR 8799 conform to expectations for a steady-state classical collisional cascade? | E: Measure flux density at 9 mm with VLA, combine with 1.3 mm flux density from SMA+ALMA model, derive alpha_mm and grain size distribution index q. | R: alpha_mm = 2.41 +/- 0.17 and q = 3.27 +/- 0.10. | F: The grain size distribution power-law index is close to classical collisional cascade predictions (q ~ 3.5 or weighted mean 3.36). | **supported**

## Reasoning

- Why this data: ALMA observations spatially filtered the bulk of extended emission due to lack of short baselines, requiring SMA observations to recover larger angular scales.  
  > "We present 1.3 millimeter observations of the debris disk surrounding the HR 8799 multi-planet system from the Submillimeter Array to complement archival ALMA observations that spatially filtered away the bulk of the emission." (abstract)
- Why this method: Fitting in the visibility domain directly avoids dirty image deconvolution biases and incorporates telescope primary beam responses and statistical weights.  
  > "we model the observations using the visibility fitting procedure described in (cite: macgregor13)." (3.3 SMA/ALMA Disk Model Fits); "determine a $\chi^2$ likelihood function, $\text{ln}\mathcal{L} = -\chi^2/2$, that incorporates the statistical weights of the visibilities." (3.3 SMA/ALMA Disk Model Fits)
- Alternative: Fitting ALMA data alone without strong priors was rejected because R_out and F_tot extend freely without informative constraints due to missing short baselines.  
  > "When modeling the ALMA observations alone, informative constraints were not obtained for the outer radius or total flux parameters using these assumptions. In effect, the ALMA data allow the outer radius parameter to extend freely, with ever increasing total flux." (3.3 SMA/ALMA Disk Model Fits)
- Alternative: Fitting VLA visibilities with MCMC was rejected due to low S/N (~3-4 sigma) and difficulty selecting a parameterization for the surface brightness profile; circular aperture flux was used instead.  
  > "In the VLA image, the disk is detected only at the $\sim3\sigma$ per beam level, and we do not apply the same MCMC modeling technique to these data." (3.4 VLA 9 millimeter Flux Estimate); "We adopt this image-based approach instead of fitting to the millimeter visibilities due to the difficulty in selecting a function that adequately reproduces the complex structure of the observed surface brightness profile." (3.4 VLA 9 millimeter Flux Estimate)
- How they decided it was enough: _not stated_
- Limitation (authors): Interferometer imaging of molecular CO line emission suffered from missing flux and pronounced image artifacts.  
  > "Regardless of the choice of visibility weighting scheme and clean deconvolution parameters, all of our attempts at imaging the line emission show pronounced artifacts." (3.2 Line Emission)
- Limitation (authors): The observations still lack sensitivity to detect subtle planet-disk interactions or tightly constrain planet masses to distinguish cooling models.  
  > "However, these observations still lack the sensitivity needed to reveal any details of planet-disk interactions, or to obtain dynamical constraints on planet mass that usefully discriminate between planet evolutionary models." (5 Conclusions)
- Caveat (inferred, ours): Combined SMA and ALMA fitting ignored the 0.20 arcsec proper motion between epochs, justified by SMA's coarse resolution.
- Caveat (inferred, ours): The discrepancy between millimeter and far-infrared disk geometry (inclination and PA) remains unresolved, possibly due to dust dynamics or model simplicity.

## Reproducibility

- Data public (paper): ALMA data are public under project code 2012.1.00482.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00482.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: vissample is publicly available on GitHub and Anaconda Cloud  
  > "vissample is publicly available at https://github.com/AstroChem/vis_sample or in the Anaconda Cloud at https://anaconda.org/rloomis/vis_sample" (3.3 SMA/ALMA Disk Model Fits)
- Missing: Specific CASA clean threshold and mask parameters for ALMA image reconstruction
- Missing: List of exact frequency channels flagged for CO emission in ALMA data
- Data volume (inferred): 20-50 GB (5 ALMA Band 6 scheduling block executions plus SMA and VLA raw data)
- Score (inferred): 8/5, The paper provides an explicit description of the parametric model, likelihood, sampler settings, and software tools (emcee, vissample). The ALMA dataset is identified by project code and calibration scripts are cited. SMA and VLA data must be obtained to reproduce the joint results, but all steps and formulas are clearly laid out.
- Rediscovery candidate: yes, The MCMC model fitting and chaotic zone calculations are cleanly specified with public tools (emcee, vissample) and clear numeric outputs.

## Links

- Method: (cite: macgregor13) (Parametric visibility fitting framework for debris disks)
- Method: (cite: foreman13) (emcee MCMC implementation)
- Method: (cite: pearce14) (Chaotic zone inner edge formula)
- Companion: (cite: booth16) (Primary paper presenting the ALMA Band 6 HR 8799 data)

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 74,
 "quote_pass_rate": 0.987,
 "quotes_too_long": 6,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 49,
  "rate": 0.613
 },
 "evidence_ok": false
}
```
