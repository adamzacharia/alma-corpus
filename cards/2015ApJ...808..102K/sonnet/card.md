# Resolving Protoplanetary Disks at Millimeter Wavelengths with CARMA

`2015ApJ...808..102K` | The Astrophysical Journal 2015 | first author: Kwon, Woojin | arXiv: 1506.03679 | DOI: 10.1088/0004-637X/808/1/102

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the physical properties of six Taurus protoplanetary disks from CARMA 1.3 and 2.7 mm visibilities, and does a flared power-law or flared viscous accretion disk model fit better?  
  > "We constrain physical properties of the disks with Bayesian inference using two disk models; flared power-law disk model and flared accretion disk model." (abstract)
- Target **CI Tau**: coordinates 04 33 52.000 +22 50 30.20 (J2000, phase center)  
  > "CI Tau | 04 33 52.000 | +22 50 30.20" (Table 1); z/distance 140 pc  
  > "CI Tau | 04 33 52.000 | +22 50 30.20" (Table 1); distance from adopted Taurus distance, from Bertout et al. 1999 Hipparcos ranges  
  > "CI Tau | 04 33 52.000 | +22 50 30.20" (Table 1)
- Target **DL Tau**: coordinates 04 33 39.076 +25 20 38.14 (J2000)  
  > "DL Tau | 04 33 39.076 | +25 20 38.14" (Table 1); z/distance 140 pc  
  > "DL Tau | 04 33 39.076 | +25 20 38.14" (Table 1); distance from adopted Taurus distance  
  > "DL Tau | 04 33 39.076 | +25 20 38.14" (Table 1)
- Target **DO Tau**: coordinates 04 38 28.583 +26 10 49.85 (J2000)  
  > "DO Tau | 04 38 28.583 | +26 10 49.85" (Table 1); z/distance 140 pc  
  > "DO Tau | 04 38 28.583 | +26 10 49.85" (Table 1); distance from adopted Taurus distance  
  > "DO Tau | 04 38 28.583 | +26 10 49.85" (Table 1)
- Target **FT Tau**: coordinates 04 23 39.178 +24 56 14.30 (J2000)  
  > "FT Tau | 04 23 39.178 | +24 56 14.30" (Table 1); z/distance 140 pc  
  > "FT Tau | 04 23 39.178 | +24 56 14.30" (Table 1); distance from adopted Taurus distance  
  > "FT Tau | 04 23 39.178 | +24 56 14.30" (Table 1)
- Target **Haro 6-13**: coordinates 04 32 15.410 +24 28 59.97 (J2000)  
  > "Haro 6-13 | 04 32 15.410 | +24 28 59.97" (Table 1); z/distance 140 pc  
  > "Haro 6-13 | 04 32 15.410 | +24 28 59.97" (Table 1); distance from adopted Taurus distance  
  > "Haro 6-13 | 04 32 15.410 | +24 28 59.97" (Table 1)
- Target **HL Tau**: coordinates 04 31 38.471 +18 13 58.11 (J2000)  
  > "HL Tau | 04 31 38.471 | +18 13 58.11" (Table 1); "However, 140 pc is within uncertainties of most of the ranges, so it is adopted for all 6 targets in this study." (3 Observations and Data); z/distance 140 pc  
  > "HL Tau | 04 31 38.471 | +18 13 58.11" (Table 1); "However, 140 pc is within uncertainties of most of the ranges, so it is adopted for all 6 targets in this study." (3 Observations and Data); distance from adopted Taurus distance  
  > "HL Tau | 04 31 38.471 | +18 13 58.11" (Table 1); "However, 140 pc is within uncertainties of most of the ranges, so it is adopted for all 6 targets in this study." (3 Observations and Data)

## Data provenance

- ALMA projects: 2011.0.00015.SV
- bands: 1.3 mm and 2.7 mm continuum  
  > "continuum observations at $\lambda=1.3$ mm and 2.7 mm" (abstract)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: individual windows ~500 MHz wide  
  > "Individual wide bandwidth windows ($\Delta\nu \sim 500$ MHz) are averaged and considered a visibility point." (4.4 Model Fitting Procedures)
- arrays: CARMA (6 x 10.1 m, 9 x 6.4 m; 3.5 m antennas not used for imaging)  
  > "which is a heterogeneous array consisting of six 10.1-m, nine 6.4-m, and eight 3.5-m antennas. For this project the 3.5-m antennas were not used for imaging." (3 Observations and Data)
- configurations: A, B, C and/or D configurations  
  > "All targets were observed in A and/or B configurations (see Table [\[tab_diskobs\]](#tab_diskobs)) at $\lambda=1.3$ mm and/or 3 mm" (3 Observations and Data)
- baselines: _not stated_
- angular resolution: best ~0.13'' at 1.3 mm (HL Tau); others ~0.3''  
  > "The highest angular resolution (the smallest synthesized beam size) is $\sim$0.13$''$ at $\lambda=1.3$ mm toward HL Tau." (3 Observations and Data)
- max recoverable scale: at least 10 arcsec (min uv distance at most 17 kλ)  
  > "the minimum *uv* distance is at most 17 kilo-wavelengths, which means that our large scale sensitivity is at least 10 arcseconds." (3 Observations and Data)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2007 Sep to 2011 Jan (per track in Table 2)  
  > "CI Tau | 2007 Nov. 25 | B | 1 | MWC349 (1.9)" (Table 2)
- pi or archival as stated: _not stated_
- Other facility **ALMA**: HL Tau long-baseline Science Verification data, used only qualitatively for comparison  
  > "the long baseline science verification (SV) data of ALMA have recently shown unprecedented details of substructures toward HL Tau" (Introduction)
- External data: Stellar Teff, L*, M*, 10 micron EW and n13-31 for targets  
  > "Selected information from the above studies is summarized in Table [\[tab_targets\]](#tab_targets)." (3 Targets) [from Furlan et al. 2009 (cite: 2009ApJ...703.1964F); Kenyon & Hartmann 1995]
- External data: Mass accretion rates from SED fitting  
  > "we use the mass accretion rate estimated by (cite: 2007ApJS..169..328R) using SED fitting" (5.6 Disk Substructures) [from (cite: 2007ApJS..169..328R)]
- External data: Dust opacity kappa0 = 0.01 cm2/g at 230 GHz  
  > "The $\kappa_0$ is based on the case of ice mantle grains following a MRN size distribution (cite: 1977ApJ...217..425M) in (cite: ossenkopf1994)." (4.1 Power-law Disk Model) [from (cite: ossenkopf1994)]

## Processing

### Calibration

- pipeline or manual: MIRIAD calibration, tracks calibrated separately  
  > "MIRIAD (cite: sault1995) has been employed to calibrate and map data. Individual tracks have been calibrated and verified separately then combined" (3 Observations and Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus preferred; also Mars, MWC349, 3C84, 3C454.3, 3C273  
  > "a good flux calibrator (e.g., Uranus) was used" (3 Observations and Data)
- flux scale uncertainty: 10% at 1.3 mm and 8% at 2.7 mm (from Kwon 2011; this work presumes lower)  
  > "10% at $\lambda=1.3$ mm and 8% at $\lambda=2.7$ mm (cite: 2011ApJ...741....3K)" (3 Observations and Data)
- self calibration: gain calibrator data self-calibrated, used for visibility noise  
  > "we use the standard deviation of the imaginary components of self-calibrated gain calibrator data" (4.4 Model Fitting Procedures)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0  
  > "the weighting scheme with a robust value of 0 has been applied." (3 Observations and Data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: tracks combined in the invert-Fourier transform step  
  > "Individual tracks have been calibrated and verified separately then combined in the invert-Fourier transform step to make maps." (3 Observations and Data)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- HL Tau data set and proper-motion compensation  
  > "In fact, this paper uses the same data set of HL Tau but we employ two disk models and a better temperature distribution." (3 Targets) [from Kwon, Looney & Mundy 2011 (cite: 2011ApJ...741....3K)]
- Visibility noise from std of imaginary parts of self-calibrated gain calibrator  
  > "which are generally a few times larger than the theoretical estimate (cite: 2011ApJ...741....3K)" (4.4 Model Fitting Procedures) [from (cite: 2011ApJ...741....3K)]
- Accretion disk equations and alpha formula  
  > "the equation derived by (cite: 2009ApJ...700.1502A)" (5.6 Disk Substructures) [from (cite: 2009ApJ...700.1502A)]

### Not stated but needed to reproduce (our reading)

- Fitting code is not named or released; MCMC proposal widths, number of steps, burn-in and annealing schedule not given
- Prior ranges for the free parameters
- Stellar luminosities and masses adopted in RADMC-3D and photon numbers
- Exact flux calibrator fluxes and which tracks were combined per target
- Opacity law at infrared wavelengths used in RADMC-3D
- Details of how inner radius and center offsets entered the fit

## Analysis recipe

1. **calibrate and image CARMA data**: MIRIAD calibration per track with test-calibrator checks and CPACS for some tracks; combine tracks in invert step; robust 0  
  > "MIRIAD (cite: sault1995) has been employed to calibrate and map data." (3 Observations and Data)
   - software: MIRIAD
   - parameter: robust = 0  
  > "the weighting scheme with a robust value of 0 has been applied." (3 Observations and Data)
   - fitting: _not stated_
   - validation: test calibrator point-likeness and flat gain-calibrator uv amplitudes  
  > "All of our data sets have a flat amplitude slope of gain calibrators after calibration" (3 Observations and Data)
2. **compute disk temperature structure**: RADMC 3D Monte Carlo radiative transfer, fit with weighted midplane and surface functional forms  
  > "we make a functional form weighting two functions that fit to the mid-plane ($T_m$) and surface temperature distributions ($T_s$)" (4.1 Power-law Disk Model)
   - software: RADMC-3D
   - assumption: kappa0 = 0.01 cm2/g at 230 GHz, gas-to-dust 100, dust and gas temperature equal, scale height not updated from temperature  
  > "In addition, we assume a gas-to-dust mass ratio of 100." (4.1 Power-law Disk Model)
   - fitting: _not stated_
   - validation: _not stated_
3. **model visibilities for each disk model and vertical structure**: build 2D disk models with radiative transfer along line of sight, multiply by three CARMA primary beams, Fourier transform and sample at observed uv points  
  > "Then, the actual model visibilities are sampled in the *uv* coverage of observational data by bi-linear interpolation of the model visibility maps." (4.4 Model Fitting Procedures)
   - parameter: 25 models per target: b_t = {0.6,0.8,1.0,1.2,1.4}, h = {0.95,1.10,1.25,1.40,1.55}  
  > "we carry out 25 separate models for each target: $b_t = \{0.6, 0.8,
1.0, 1.2, 1.4\}$ and $h = \{0.95, 1.10, 1.25, 1.40, 1.55\}$" (4.3 Model Parameters)
   - parameter: pixel 9 AU, 1024x1024 image  
  > "an image pixel size of 9 AU and an image size of 1024 pixel by 1024 pixel are used" (4.4 Model Fitting Procedures)
   - assumption: distance 140 pc; constant beta; accretion disk cut at 5 Rc  
  > "the modeling disks are cut off at 5 $R_c$ due to limitation in image size and for simplicity in integration" (4.3 Model Parameters)
   - fitting: _not stated_
   - validation: _not stated_
4. **Bayesian parameter fitting**: Metropolis-Hastings MCMC with Gaussian likelihood on real and imaginary visibilities; 8 random starts, annealing, then fresh run per (b_t,h) with proposal tuned to 10-50% acceptance  
  > "Searching distributions of model parameters by the Metropolis Hastings method has two parts." (4.4 Model Fitting Procedures)
   - parameter: 7 free parameters: s, beta, Mdisk, Rin, Rout (or Rc), inclination, PA  
  > "There are 7 free parameters for each disk model: $s$, $\beta$, $M_{disk}$, $R_{in}$, $R_{out}$ (or $R_c$), $\theta_i$, and $PA$." (4.3 Model Parameters)
   - fitting: Metropolis-Hastings; Gaussian likelihood; uniform priors over same ranges for both models; no priors from images except centers and inclination sign  
  > "We set the prior as well as the number of free parameters the same for the two models (uniform priors over the same ranges)" (5.3 Model Comparison)
   - validation: residual maps and annular-averaged visibility plots  
  > "The low levels of the residual indicate excellence of our model fitting." (5.4 Residual Maps)
5. **compare models by evidence**: Bayes factor K from best likelihood times posterior volume; K>3 favors accretion disk  
  > "The likelihood integration can be estimated by the best likelihood times the posterior accessible volume" (5.3 Model Comparison)
   - fitting: _not stated_
   - validation: interpretation scale of Kass & Raftery  
  > "$K > 3$ indicates a considerable preference for the model of the numerator" (5.3 Model Comparison)
6. **correlations, Toomre Q and alpha**: Pearson correlation among fitted properties; Toomre Q profile from midplane temperature and surface density; alpha from accretion rate  
  > "We calculated correlations between the constrained physical properties" (5.5 Correlations among Properties)
   - parameter: Q<~1.5 unstable  
  > "regions of $Q \lesssim 1.5$ are gravitationally unstable" (5.6 Disk Substructures)
   - assumption: Keplerian rotation; Haro 6-13 accretion rate assumed 1.0e-7 Msun/yr  
  > "We assumed the accretion rate of Haro 6-13, which has not been reported, as a typical value of $1.0\times 10^{-7}~\textrm{M}_\ensuremath{\odot}~
\textrm{year}^{-1}$." (5.6 Disk Substructures)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **MIRIAD** : calibration, imaging, IMFIT Gaussian fits  
  > "MIRIAD (cite: sault1995) has been employed to calibrate and map data." (3 Observations and Data)
- **RADMC-3D** : Monte Carlo dust temperature  
  > "we use a temperature distribution calculated in a given disk structure by the RADMC 3D code" (4.1 Power-law Disk Model)
- **Numerical Recipes GASDEV** : Gaussian random numbers for MCMC proposals  
  > "The GASDEV subroutine of the Numerical Recipes using the Box-Muller method is used to produce random numbers in the Gaussian distribution" (4.4 Model Fitting Procedures)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HL Tau accretion-disk beta | 0.6745 | 0.0069 | dimensionless | 4 | HL Tau / 0.7483$\pm$0.0087 / 0.6745$\pm$0.0069 / 0.105$\pm$0.001 |
| HL Tau accretion-disk mass | 0.105 | 0.001 | Msun | 4 | HL Tau / 0.7483$\pm$0.0087 / 0.6745$\pm$0.0069 / 0.105$\pm$0.001 |
| CI Tau accretion-disk Rc | 119.6 | 6.1 | AU | 4 | CI Tau / 1.67$\pm$0.24 / 0.049$\pm$0.027 / 0.018$\pm$0.002 / 4.2$\pm$2.6 / 119.6$\pm$6.1 |
| ln K HL Tau (accretion vs power-law) | 289.6 | not stated | dimensionless | 5 | HL Tau /     -7863636.4     /     -7863346.8     /  289.6  / Accretion |
| ln K DL Tau | -4.7 | not stated | dimensionless | 5 | DL Tau /     -5336360.9     /     -5336365.6     /  -4.7   / Power-law |
| beta range of sample | -0.15 to 0.70 | ~0.25 from flux calibration | dimensionless | 4 | $\beta$ of our sample disks ranges from -0.15 to 0.70 and half of them are around 0 |
| disk masses | 0.01-0.10 | factor ~2 from kappa0 | Msun | 4 | Disk masses are 0.01–0.10 M$_\odot$. |
| beta vs Mdisk correlation | 0.84 | not stated | dimensionless | 6 | $\beta$    /      1.00 /   **0.84** / |

## Qualitative findings

- Extended disks (CI Tau, DL Tau, HL Tau) prefer thinner, less flared models; DO Tau prefers thick, flared  
  > "the three extended disks (CI Tau, DL Tau, and HL Tau) have higher posteriors in thinner and less flared models." (5.7 Disk Vertical Structures)
- Weak non-axisymmetric feature in CI Tau at both wavelengths; no Q<1.5 region found  
  > "the well-resolved map of CI Tau has a weak substructure that is seen at both wavelengths" (5.4 Residual Maps)

## Claim tuples

- H: Does the accretion disk model fit better than the power-law model? | E: Bayes factors from visibility fits of six disks | R: ln K positive for all but DL Tau; large for HL Tau | F: accretion disk model preferred overall, with DL Tau exception | **supported**
- H: Do beta, mass and density gradient correlate, indicating grain growth and drift? | E: correlation coefficients among fitted properties of six disks | R: beta correlates with mass (0.84), anticorrelates with s (-0.77) | F: large grains in less massive disks with steeper midplane gradients | **partially**
- H: Do extended disks show gravitational instability? | E: Toomre Q from accretion-disk models | R: CI Tau and DL Tau have no Q<1.5 region; DL Tau near 1.5 at ~100 AU | F: no strong support for instability | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Bayesian inference provides parameter distributions and model comparison unlike chi-square  
  > "The Bayesian approach provides a basis of probability theory to compare two models as well as to achieve parameter probability distributions, which are not given by the $\chi^2$ method." (Introduction)
- Alternative: Center positions from manual intensity peaks tested; Gaussian-fit offsets chosen for higher posteriors  
  > "The offset values by the simple Gaussian fit have been chosen (Table [\[tab_diskdata\]](#tab_diskdata)), as they give higher posteriors." (5.2 Fitting Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Inner radii unreliable due to resolution and decoherence; constant beta assumed; kappa0 uncertain by factor two  
  > "fitted values can be model-dependent and are likely unreliable due to systematic uncertainties in the observation, primarily the resolution." (4.3 Model Parameters)
- Caveat (inferred, ours): Bayes factor approximated by best likelihood times posterior width rather than true evidence integral
- Caveat (inferred, ours): Only six targets, so correlations are weak statistically
- Caveat (inferred, ours): Results dependent on assumed kappa0 and constant beta
- Caveat (inferred, ours): Disagrees with Guilloteau et al. on model preference and beta radial variation

## Reproducibility

- Data public (paper): HL Tau ALMA SV data cited; CARMA data not stated as public  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00015.SV." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Fitting code
- Missing: Priors and MCMC settings
- Missing: Calibrated CARMA visibilities
- Data volume (inferred): CARMA visibilities ~ a few to tens of GB; the ALMA SV data are only for comparison
- Score (inferred): 3/5, Data and models are well described, but the in-house code, MCMC settings and priors are unstated; CARMA data availability is unclear.
- Rediscovery candidate: no, CARMA data availability is not stated and the fitting code is unreleased.

## Links

- Method: Kwon, Looney & Mundy 2011 (cite: 2011ApJ...741....3K) (earlier HL Tau data and accretion-disk modeling)
- Method: Andrews et al. 2009 (cite: 2009ApJ...700.1502A) (accretion disk formalism and alpha equation)
- Companion: Guilloteau et al. 2011 (cite: 2011A&A...529A.105G) (PdBI modeling of overlapping targets for comparison)
- Related: ALMA HL Tau Science Verification long baseline campaign

## Checks

```json
{
 "quotes": 82,
 "quotes_ok": 82,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 98,
  "stated": 66,
  "rate": 0.673
 },
 "evidence_ok": true
}
```
