# Kuiper Belt-like Hot and Cold Populations of Planetesimal Inclinations in the β Pictoris Belt Revealed by ALMA

`2019AJ....157..135M` | The Astronomical Journal 2019 | first author: Matrà, L. | arXiv: 1902.04081 | DOI: 10.3847/1538-3881/ab06c0

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks
- Question: Is the vertical distribution (and hence inclination distribution) of mm grains in the beta Pic planetesimal belt a single Gaussian or a sum of hot and cold populations, and what stirs it?  
  > "finding that the vertical distribution is significantly better described by the sum of two Gaussians compared to a single Gaussian." (abstract)
- Target **beta Pictoris**: coordinates _not stated_; z/distance 19.44 pc  
  > "At only 19.44 pc (cite: vanLeeuwen2007), the disk’s brightness and on-sky extent have made this system extremely suitable for resolved imaging." (Introduction); distance from van Leeuwen 2007  
  > "At only 19.44 pc (cite: vanLeeuwen2007), the disk’s brightness and on-sky extent have made this system extremely suitable for resolved imaging." (Introduction)

## Data provenance

- ALMA projects: 2012.1.00142.S
- bands: Band 6 (1.33 mm, 224.58 GHz effective)  
  > "The dataset covers $\sim$6.8 GHz of total bandwidth at an effective wavelength (frequency) of 1.33 mm (224.58 GHz)." (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m extended, 12-m compact (two pointings), and ACA  
  > "Data was taken with the 12-m array in extended (one pointing centered on the star) and compact configuration (two pointings centered $\pm5\ensuremath{''}$ from the star along the belt midplane)" (Observations)
- configurations: _not stated_
- baselines: 9 to 1574 m; sensitive to ~0.3'' to 27''  
  > "Baselines covered a range between 9 and 1574 m, enabling us to be sensitive to structure between about 0$\ensuremath{''}$3 and 27$\ensuremath{''}$." (Observations)
- angular resolution: 0.32'' x 0.27'' (6.1 x 5.3 au), natural weighting  
  > "synthesized beam of size $0.32\ensuremath{''}\times0.27\ensuremath{''}$ and PA of -82.01$^\circ$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: RMS 12 uJy/beam  
  > "for the RMS noise level of 12 $\mu$Jy/beam measured in an emission-free region of the continuum map" (3.1 New 1.33 mm dust continuum dataset)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230.538 GHz)
- External data: 885 um ALMA archival dataset (Band 7, mosaic) re-reduced for comparison  
  > "we independently re-reduced the dataset as described in §2.2 of (cite: Matra2017a)." (4.5) [from Dent2014; Matra2017a]
- External data: beta Pic b orbit: a 8.8 au, inclination 89.3 deg, PA 32.1 deg  
  > "best-fit semimajor axis of 8.8 au, an inclination to the line of sight $I_{\rm p}$ of 89.3$^{\circ}$ and a position angle $\Omega_{\rm p}$ of 32.1$^{\circ}$ (cite: Lagrange2018b)" (5.2.1) [from Lagrange2018b]
- External data: Stellar luminosity 8.7 Lsun  
  > "around a star of 8.7 L$_{\odot}$ (cite: KennedyWyatt2014)" (4.1 Method) [from KennedyWyatt2014]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: relative flux calibration systematics of ±10% between compact and extended datasets tested  
  > "relative flux calibration systematics of $\pm10\%$ between the datasets with compact and extended baselines" (3.3)
- self calibration: _not stated_

### Imaging

- task: CLEAN, multi-frequency synthesis (tclean in CASA v5.1.0 for the 885 um data)  
  > "we imaged the combined dataset using the CLEAN algorithm (cite: Hogbom1974) in multi-frequency synthesis mode." (2 Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We used natural weighting of the visibilities to ensure maximum sensitivity" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: multiscale deconvolution used for 885 um data (scales not stated)  
  > "using natural weights and multiscale deconvolution to best recover faint, extended emission" (4.5)
- continuum subtraction: channels around CO J=2-1 flagged for continuum  
  > "we flagged spectral channels around the frequency of the detected CO J=2-1 line (230.538 GHz)" (2 Observations)
- line free channels: _not stated_
- primary beam correction: flux measured on primary-beam-corrected map  
  > "The spatially integrated 1.33 mm flux measured on the primary-beam-corrected map" (3.1)
- array combination: all configurations and ACA combined with per-dataset visibility weight rescaling  
  > "we applied a constant rescaling factor to the visibility weights of each dataset" (2 Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observation description, calibration, reduction and imaging  
  > "A more complete description of the observations, including calibration, reduction and imaging of CO and other lines can be found in (cite: Matra2017a; Matra2018a)." (Observations) [from Matra2017a; Matra2018a]
- Vertical profile Gaussian fitting procedure  
  > "Following the procedure described in detail in §3.2 and Appendix B of (cite: Matra2017a), we fit Gaussians" (3.3) [from Matra2017a]

### Not stated but needed to reproduce (our reading)

- Dust opacity value fixed in RADMC-3D
- Burn-in length and walker initialisation for MCMC
- Exact CO-flagged channel ranges
- Image size and cell size
- Multiscale scales for 885 um imaging
- Whether the pipeline or manual calibration was used and the CASA version for the 1.33 mm data

## Analysis recipe

1. **Image combined continuum**: CLEAN MFS imaging of combined 12m+ACA data with weight rescaling, natural weighting  
  > "Then, we imaged the combined dataset using the CLEAN algorithm (cite: Hogbom1974) in multi-frequency synthesis mode." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure stellar flux**: Select uv >300 klambda, CLEAN, 2D Gaussian fit at star  
  > "we extract the subset of the dataset containing visibilities at $u-v$ distances $>300 k\lambda$." (3.1)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with ~86 uJy Rayleigh-Jeans extrapolation  
  > "This detection is consistent with the expected stellar flux of $\sim$86 $\mu$Jy" (3.1)
3. **Image-plane radial and vertical profiles**: Vertical profiles every 15 au; Gaussian fits for spine and FWHM; compare single vs double Gaussian on radially integrated profile  
  > "obtained by integrating emission every 15 au along the radial (midplane) direction" (3.3)
   - fitting: _not stated_
   - validation: _not stated_
4. **Visibility-domain model fitting**: Parametric 3D dust models, RADMC-3D images, FT to uv points, MCMC fit with Models 1-5  
  > "we solve the radiative transfer at 1.33mm using RADMC-3D" (4.1)
   - software: RADMC-3D, emcee
   - parameter: walkers = 10x free parameters; 2500 steps  
  > "The MCMC was run for each tested model with a number of walkers equal to 10x the number of free parameters, and over 2500 steps" (4.1)
   - assumption: _not stated_
   - fitting: emcee affine-invariant sampler, uniform priors, likelihood proportional to exp(-chi^2/2)  
  > "assuming uniform priors on all of the probed parameters, and a likelihood function proportional to $e^{-\chi^2/2}$" (4.1)
   - validation: _not stated_
5. **Convert aspect ratio to inclination**: RMS_i = sqrt(2) h, mean i = sqrt(pi/2) h  
  > "$\bar{i}=\sqrt{\frac{\pi}{2}}h\ \ \ \ \mathrm{and}\ \ \ \ \mathrm{RMS}_{i}=\sqrt{2}h.$" (5.1)
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: _not stated_
6. **Dynamical constraints**: _not stated_
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** v5.1.0 (885 um re-reduction): tclean imaging and 2D Gaussian fit  
  > "We imaged the continuum using the *tclean* task (CASA v5.1.0)" (4.5)
- **RADMC-3D** : radiative transfer of model belts  
  > "we solve the radiative transfer at 1.33mm using RADMC-3D" (4.1)
- **emcee** : MCMC fitting of visibilities  
  > "through a Monte Carlo Markov Chain (MCMC) method implemented through the EMCEE package" (4.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| RMS inclination hot population | 8.9 | +0.7/-0.5 | deg | 5 | The hot and cold populations have RMS inclinations of 8.9$^{+0.7}_{-0.5}$ and 1.1$^{+0.5}_{-0.5}$ degrees. |
| RMS inclination cold population | 1.1 | +0.5/-0.5 | deg | 5 | The hot and cold populations have RMS inclinations of 8.9$^{+0.7}_{-0.5}$ and 1.1$^{+0.5}_{-0.5}$ degrees. |
| Integrated 1.33 mm flux | 20 | 2 | mJy | 1 | is 20$\pm$2 mJy |
| Belt PA (Model 2) | 29.7 | +0.1/-0.1 | deg | 4 | $PA$ / $^{\circ}$ / $30.0_{-0.1}^{+0.1}$ / $29.7_{-0.1}^{+0.1}$ |
| Belt inclination (Model 2) | 88.6 | +0.2/-0.3 | deg | 4 | $I$ / $^{\circ}$ / $86.6_{-0.3}^{+0.4}$ / $88.6_{-0.3}^{+0.2}$ |
| Hot-population mass fraction | 80 | +4/-5 | % | 4 | with the hot component containing $80^{+4}_{-5}$% of the observed mass |
| Mass of largest bodies for hot population at 150 au | 0.007 to 54 | not stated | Earth masses | 6 | should be between 0.007 and 54 M$_{\oplus}$ at 150 au |

## Qualitative findings

- No significant SW/NE asymmetry in 1.33 mm or 885 um continuum  
  > "We conclude that we do not detect a significant SW/NE asymmetry in the new 1.33 mm dataset." (4.5)

## Claim tuples

- H: Is the mm vertical distribution a single Gaussian? | E: Image and visibility fitting of single vs double Gaussian models | R: Double Gaussian strongly preferred (>1e8 likelihood ratio) | F: Inclination distribution is bimodal with hot and cold populations like the Kuiper belt | **supported**
- H: Does beta Pic b's secular perturbation explain the vertical structure? | E: Compare disk spine and vertical profile with expected warp | R: No warp above 2.8 deg and centrally peaked emission | F: beta Pic b alone is unlikely to explain it | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Single broad non-Rayleigh vertical profile (p~0.9) fits comparably, but double Gaussian preferred for Kuiper belt comparison  
  > "For later interpretation, we prefer to use the double Gaussian simply to facilitate direct comparison with the Kuiper belt" (4.4)
- How they decided it was enough: _not stated_
- Limitation (authors): Narrow Gaussian component only resolved through forward modelling  
  > "which is similar to the size of our resolution element and only resolved through the forward modelling presented here" (4.3)
- Caveat (inferred, ours): Dust opacity fixed and temperature blackbody; vertical structure may depend on these
- Caveat (inferred, ours): Hot/cold split is parametric; non-Gaussian profile fits similarly
- Caveat (inferred, ours): Dynamical arguments rely on assumed stellar mass and large-body inclination

## Reproducibility

- Data public (paper): ALMA project 2012.1.00142.S acknowledged; archival 885 um data  
  > "This paper makes use of ALMA data ADS/JAO.ALMA#2012.1.00142.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Opacity and RADMC-3D settings
- Missing: Details of calibration in companion papers
- Missing: Priors/bounds and initialisation for MCMC
- Data volume (inferred): ~50-100 GB raw
- Score (inferred): 3/5, Public data and clear model definitions, but calibration is deferred to other papers and some settings are missing.
- Rediscovery candidate: yes, Public data, a fairly complete modelling recipe and numeric results.

## Links

- Method: Matra2017a (calibration and vertical profile fitting procedure)
- Companion: Matra2018a (observations and reduction)

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
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
  "facts": 76,
  "stated": 35,
  "rate": 0.461
 },
 "evidence_ok": true
}
```
