# A Detailed Characterization of HR 8799's Debris Disk with ALMA in Band 7

`2021AJ....161..271F` | The Astronomical Journal 2021 | first author: Faramaz, Virginie | arXiv: 2104.02088 | DOI: 10.3847/1538-3881/abf4e0

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks, exoplanets
- Question: Where is the inner edge of HR 8799's cold debris disk and what is its radial profile shape (sharp vs smooth), and is an extra planet implied?  
  > "It was therefore unclear whether the outermost planet HR 8799 b was dynamically sculpting it or not." (abstract)
- Target **HR 8799**: coordinates 23h07m28.86s +21d08m02.39s (Gaia-expected at 12m epoch)  
  > "Situated at a distance of $41.3\,$pc[^1]" (Introduction); z/distance 41.3 pc  
  > "Situated at a distance of $41.3\,$pc[^1]" (Introduction); distance from Gaia DR2 / Bailer-Jones 2018  
  > "Situated at a distance of $41.3\,$pc[^1]" (Introduction)

## Data provenance

- ALMA projects: 2016.1.00907.S, 2012.1.00482.S
- bands: Band 7 (340 GHz, 880 um); Band 6 (1.3 mm) archival  
  > "ALMA observations of the debris disk of HR 8799 in Band 7 (340 GHz, 880 microns)" (2 ALMA Observations)
- frequencies and spectral setup: 4 spws of 2 GHz; three at 334, 336, 348 GHz with 128 channels of 15.625 MHz; fourth at 346 GHz for CO 3-2 with 0.5 MHz channels  
  > "The spectral setup consisted of four spectral windows, each 2 GHz wide." (2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: 12m array and ACA  
  > "They comprise 12m-array observations carried out from 2018 May 13 to 2018 June 1 (6 separate observations)" (2 ALMA Observations)
- configurations: _not stated_
- baselines: ACA 8.9-48.9 m; 12m 15-314 m  
  > "ACA data were taken using baselines ranging from 8.9 to 48.9 m" (2 ALMA Observations)
- angular resolution: 1.13" x 0.97", PA 22 deg (natural weighting)  
  > "resulting in a beam size of $1.13\ensuremath{''} \times 0.97\ensuremath{''}$" (Results)
- max recoverable scale: 12" (12m), 20" (ACA)  
  > "(12$''$ for the 12m-array and 20$''$ for the ACA)" (4.3 The disk flux)
- sensitivity: 9.8 uJy/beam  
  > "sensitivity of $9.8\,\mu\mathrm{Jy\,beam^{-1}}$" (abstract)
- time on source: 19.6 h ACA, 4.5 h 12m  
  > "The total time on source was 19.6 hours with the ACA and 4.5 hours with the 12m array." (2 ALMA Observations)
- observing dates: _not stated_
- pi or archival as stated: Band 7 PI V. Faramaz; Band 6 Cycle 1 data from archive (Booth2016)  
  > "The calibrated dataset for this was retrieved from the ALMA archive" (3.1 Model Description)
- Line: CO J=3-2 (not stated)
- Other facility **Gaia**: Astrometry, distance, proper motion  
  > "we take advantage of the Gaia EDR3 astrometry" (Stellar parameters)
- External data: ALMA Band 6 12m Cycle 1 calibrated visibilities  
  > "along with the 12m Band 6 observations from Cycle 1 (cite: Booth2016)" (3.1 Model Description) [from (cite: Booth2016)]
- External data: Planet orbital inclination and PA used as disk priors  
  > "using Table 4 of (cite: WangJason2018), leads to $i \sim \mathcal{N} (26.8^{\circ}, 2.3^{\circ})$" (3.1 Model Description) [from (cite: WangJason2018)]
- External data: JCMT/SCUBA-2 disk flux 17.4 +/- 1.5 mJy at 850 um  
  > "reported a disk total flux of $17.4 \pm 1.5$ mJy at 850 $\mu$m (cite: Holland2017)" (4.3 The disk flux) [from (cite: Holland2017)]

## Processing

### Calibration

- pipeline or manual: Recalibrated with ALMA-provided pipeline and calibration script  
  > "We recalibrated the raw data using the pipeline and calibration script provided by ALMA." (2.1 Results)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J2148+0657 / Titan (12m); Uranus, Neptune, Mars (ACA)  
  > "J2148+0657" (Table 1)
- flux scale uncertainty: 10% absolute flux calibration  
  > "including a 10% absolute flux calibration uncertainty" (3.2 Best-Fit Model Results)
- self calibration: _not stated_

### Imaging

- task: tclean in CASA 5.1.1  
  > "We used the *TCLEAN* algorithm and task in CASA version 5.1.1" (2.1 Results)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We used a natural weighting scheme" (2.1 Results)
- uv taper: _not stated_
- cell size: 0.4" for CO cube  
  > "a pixel size of $0.4\ensuremath{''}$" (7 The gas content)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CO channels excluded; four spws combined  
  > "Note that we excluded the channels spanning the CO emission." (2.1 Results)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 9.8 uJy/beam, measured in dirty image 90" away  
  > "we measure the RMS in a dirty image pointing $90\ensuremath{''}$ away from the target in Declination." (Footnote 2)

### Inherited from earlier work

- Modelling method: RADMC-3D plus MCMC visibility fitting and dust composition  
  > "We follow the method used in (cite: Marino2018; Marino2019; Marino2020)" (3.1 Model Description) [from (cite: Marino2018; Marino2019; Marino2020)]
- RMS measured in a dirty image offset from target  
  > "as in (cite: Booth2016), we measure the RMS in a dirty image" (Footnote 2) [from (cite: Booth2016)]
- Dataset weights renormalised to reduced chi2 about unity  
  > "ensure the reduced $\chi^2$ of each data set is about unity (cite: Booth2021)" (3.1 Model Description) [from (cite: Booth2021)]

### Not stated but needed to reproduce (our reading)

- MCMC settings (walkers, steps, burn-in, convergence)
- Uniform prior bounds for free parameters
- Image size, cell size and clean threshold/masking for continuum
- uv-range and weights used in the visibility fit
- Pipeline version
- Exact CO channels excluded
- Disk scale height/aspect ratio and stellar parameters for RADMC-3D

## Analysis recipe

1. **Recalibrate and image continuum**: Pipeline recalibration; tclean with natural weights, all four spws, CO channels excluded  
  > "To recover the maximum SNR, we combined the four spectral windows." (2.1 Results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure central point source**: Gaussian fit with imfit over 2.5" aperture, compare to Gaia position  
  > "using the `imfit` task over an aperture 2.5$''$ in diameter" (2.1 Results)
   - software: CASA imfit
   - fitting: _not stated_
   - validation: Position consistent with Gaia-expected stellar position  
  > "the position of the central emission as returned by ALMA is consistent with the expected position of the star" (2.1 Results)
3. **Fit radial profile models in visibility space**: RADMC-3D model images x primary beam, sampled at uv points, chi2 summed over Band 7 12m, ACA, Band 6 12m; three surface-density models; extra Gaussian source for bright background source; central point source  
  > "the radiative transfer code is used to produce model images which are multiplied by the primary beam" (3.1 Model Description)
   - software: RADMC-3D, emcee
   - parameter: 22 free parameters (Model 1), 24 (Models 2, 3)  
  > "This gives us a total of 22 free parameters for Model 1, and 24 for Models 2 and 3." (3.1 Model Description)
   - parameter: Surface density zero inside 70 au and beyond 600 au for Models 2 and 3  
  > "we set the surface density to zero interior to 70 au for both Model 2 and Model 3" (3.1 Model Description)
   - assumption: Dust: 70% astrosilicate, 15% amorphous carbon, 15% water ice; size power law -3.5, 1 um to 1 cm; Band 7 opacity 1.9 cm2/g  
  > "with a size distribution following a power law of index $-$3.5 over sizes from 1 micron to 1 centimeter" (3.1 Model Description)
   - assumption: Band 6 emission scaled from Band 7 via free alpha_mm  
  > "it is scaled to band 6 via a spectral index, $(\alpha_\mathrm{mm})$, which is left as free parameter" (3.1 Model Description)
   - fitting: MCMC; uniform priors except Gaussian priors on i (26.8+/-2.3 deg) and PA (68.25+/-5.55 deg)  
  > "We assume uniform priors except for the disk inclination and position angle" (3.1 Model Description)
   - validation: Likelihood ratio exp(-dchi2/2) between models, BIC, residual maps; rerun with unconstrained orientation  
  > "Even after considering the lower number of free parameters of Model 1, e.g. through the Bayesian Information Criterion" (3.2 Best-Fit Model Results)
4. **Mutual inclination of disk and planets**: Combine disk i, PA posteriors with literature planet orbit values approximated as Gaussians  
  > "we use the values quoted in the literature for the best fit planet inclination and position angle, and approximate their posterior distribution by a Gaussian distributions." (4.2 The disk orientation)
   - fitting: _not stated_
   - validation: _not stated_
5. **Map CO 3-2 in ACA data**: tclean cube, natural weights, compared to Keplerian toy model  
  > "we map the CO $J$=3-2 line emission, using the TCLEAN algorithm to create a full-spectral-resolution cube" (7 The gas content)
   - software: CASA
   - assumption: Toy model inclination 33 deg, stellar mass 1.56 Msun  
  > "assumed inclination = 33$^{\circ}$, stellar mass = 1.56 $M_{\odot}$" (7 The gas content)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.1: calibration, tclean imaging, imfit  
  > "task in CASA version 5.1.1" (2.1 Results)
- **RADMC-3D** : radiative transfer model images  
  > "fed into radiative transfer calculations with RADMC3D" (3.1 Model Description)
- **emcee** : MCMC sampling (cited Foreman-Mackey2013)  
  > "Markov chain Monte Carlo (MCMC) procedure (cite: Foreman-Mackey2013)" (3.1 Model Description)
- **BANYAN Sigma** : kinematic membership probabilities of HR 8799  
  > "We use the BANYAN $\Sigma$ (Bayesian Analysis for Nearby Young AssociatioNs $\Sigma$) tool" (Kinematics and Group Membership)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Model 1 inner edge radius | 135 | 4 | au | 3 | $r_{\min}$                 / Inner Radius (au)          / $135 \pm 4$ |
| Model 3 inner-edge Gaussian peak radius r1 | 172 | +26/-40 | au | 3 | Peak Radius Inner Edge (au)                / $172_{-40}^{+26}$ |
| Model 3 inner edge sigma | 37 | +14/-21 | au | 3 | Standard Deviation Inner edge (au)         / $37_{-21}^{+14}$ |
| Spectral index alpha_mm (Model 3) | 2.5 | 0.2 | dimensionless | 3 | which in our preferred model (Model 3) was found to be $2.5\pm0.2$ |
| Disk flux Band 7 (Model 3) | 8.1 | 1.0 | mJy | 3 | $3.1 \pm 0.5\,$mJy and $8.1\pm 1.0\,$mJy in Band 6 and Band 7, respectively |
| Disk dust mass (Model 3) | 1.3e-1 | 0.1e-1 | Earth masses | 3 | $(1.3 \pm 0.1)\times10^{-1}$ |
| Central emission integrated flux (imfit) | 73 | 13 | uJy | 2 | $73\pm 13$ $\mu\mathrm{Jy}$, respectively |
| Bright source flux Band 7 (Model 3) | 316 | +20/-19 | uJy | 3 | Its total flux is found to be $316^{+20}_{-19}$ $\mu\mathrm{Jy}$ at 880 microns |
| Median mutual inclination disk-planets | 9 | 3sigma 1 to 19 | deg | 4 | We find a median mutual inclination of $9^{\circ}$, with a $3\sigma$ lower and upper limit of $1^{\circ}$ and $19^{\circ}$ |
| Disk inclination with unconstrained prior | 30.8 | +2.8/-3.2 | deg | 3 | we recover a disk inclination of $30.8^{\circ\,+2.8}_{-3.2}$ |

## Qualitative findings

- Bright source is likely a background submillimeter galaxy based on steep spectral slope  
  > "This bright source is thus likely to be a background submillimeter galaxy." (4.4 The bright source)
- CO emission originates from the background cloud HLCG 92-35, not the disk  
  > "all confirm that the $^{12}$CO emission originates from the background cloud HLCG 92-35" (7 The gas content)

## Claim tuples

- H: Is the disk adequately described by a single power law with sharp edges? | E: Fit three surface-density models to Band 7 12m, ACA and Band 6 visibilities | R: Model 1 is about 1e10 times less likely than Model 3 | F: Disk has smooth inner and outer edges with a peak in between; step-function inner edge does not apply | **supported**
- H: Is the disk coplanar with the planets? | E: Fit with and without orientation priors and compute mutual inclination | R: Median 9 deg, 3sigma 1-19 deg | F: No evidence of misalignment; ~10 deg not excluded | **supported**
- H: Is the bright source in the disk a background galaxy? | E: Fit fluxes in Band 6 and 7 for the spectral slope | R: Slope 3.98 (+0.96/-0.80) | F: Likely background submillimeter galaxy | **supported**
- H: Is the central emission a stellar photosphere or warm dust? | E: Compare 73 uJy to photosphere model 36 uJy | R: Excess 37+/-13 uJy | F: Excess may be warm dust or chromospheric emission; unresolved | **partially**

## Reasoning

- Why this data: Band 7 gives higher resolution and sensitivity to settle disagreement over inner edge  
  > "By observing the debris disk at higher resolution and sensitivity in Band 7 than in Band 6, our primary goal was to settle the dispute over the inner edge location" (4.1 The disk geometry)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Model-dependent total flux; ALMA flux about half of SCUBA-2 flux  
  > "On the other hand, one factor that could cause the ALMA flux to be too low is that it is model dependent." (4.3 The disk flux)
- Caveat (inferred, ours): Disk orientation priors from planet orbits may bias the fit
- Caveat (inferred, ours): Delta chi2 interpretation on ~1e6 data points is ad hoc
- Caveat (inferred, ours): Parametric profiles are ad hoc, not physically motivated
- Caveat (inferred, ours): Low SNR per beam (up to 6)

## Reproducibility

- Data public (paper): Calibrated Band 6 data retrieved from ALMA archive; projects listed in acknowledgments  
  > "The calibrated dataset for this was retrieved from the ALMA archive" (3.1 Model Description)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: MCMC configuration and prior ranges
- Missing: Full posteriors only available on request
- Missing: Imaging mask/size details
- Data volume (inferred): ~100-300 GB raw (28 ACA + 6 12m executions with a high-resolution CO spw)
- Score (inferred): 3/5, Public data and clear model definitions with a tabulated parameter set, but MCMC setup and priors are incomplete and requires own RADMC-3D pipeline.
- Rediscovery candidate: no, Fit requires custom radiative-transfer MCMC with unspecified settings.

## Links

- Method: (cite: Marino2018) (Visibility-space RADMC-3D+MCMC method and dust model)
- Companion: (cite: Booth2016) (Band 6 ALMA observations)
- Companion: (cite: Wilner2018) (Reanalysis of Band 6 with SMA)

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 50,
  "rate": 0.641
 },
 "evidence_ok": true
}
```
