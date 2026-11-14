# Hints of a Population of Solar System Analog Planets from ALMA

`2020ApJ...895L..46L` | The Astrophysical Journal Letters 2020 | first author: Long, Deryl E. | arXiv: 2005.09730 | DOI: 10.3847/2041-8213/ab94a8

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Does the compact disk around GQ Lup A show DSHARP-like substructures (gaps/rings), and what planet masses would they imply?  
  > "Here we explore the presence and characteristics of features in a compact disk around GQ Lup A, the effective radius of which is 1.5 to 10 times smaller than those of DSHARP disks." (abstract)
- Target **GQ Lup A**: coordinates _not stated_; z/distance 152 pc  
  > "The data are deprojected using an inclination angle $i = 60\degree$ and a position angle $\phi = 346\degree$ (cite: MacGregor_2017)." (Deriving the surface brightness profile of the 1.3 mm continuum); "A source distance of 152 pc (cite: gaia_2018) is used for conversions between angular distance and au." (Deriving the surface brightness profile of the 1.3 mm continuum); distance from Gaia (Brown et al. 2018)  
  > "The data are deprojected using an inclination angle $i = 60\degree$ and a position angle $\phi = 346\degree$ (cite: MacGregor_2017)." (Deriving the surface brightness profile of the 1.3 mm continuum); "A source distance of 152 pc (cite: gaia_2018) is used for conversions between angular distance and au." (Deriving the surface brightness profile of the 1.3 mm continuum)

## Data provenance

- ALMA projects: 2015.1.00773.S
- bands: Band 6 (1.3 mm)  
  > "These observations were taken on UT 2015, November 1 in Cycle 3 with the Band 6 receiver." (Observations and Data Reduction)
- frequencies and spectral setup: three continuum basebands centered at 233.0, 246.0, 248.0 GHz  
  > "The three basebands configured for continuum observations are centered at 233.0, 246.0, and 248.0 GHz respectively" (Observations and Data Reduction)
- continuum bandwidth: 2 GHz total  
  > "provide a total continuum bandwidth of 2 GHz" (Observations and Data Reduction)
- arrays: 41 12-m antennas  
  > "The observations utilized 41 12-m antennas for a total on-source time of 11 minutes." (Observations and Data Reduction)
- configurations: _not stated_
- baselines: baseline coverage 84.7 meters  
  > "The baseline coverage was 84.7 meters." (Observations and Data Reduction)
- angular resolution: 0.057" x 0.032"  
  > "giving us a synthesized beam of 0$''$057 $\times$ 0$''$032" (Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 56 uJy/beam  
  > "has an rms of 56 ${\mu}$Jy beam$^{-1}$" (Observations and Data Reduction)
- time on source: 11 minutes  
  > "The observations utilized 41 12-m antennas for a total on-source time of 11 minutes." (Observations and Data Reduction)
- observing dates: UT 2015 November 1  
  > "These observations were taken on UT 2015, November 1 in Cycle 3 with the Band 6 receiver." (Observations and Data Reduction)
- pi or archival as stated: _not stated_
- External data: Total dust mass 5.9 Earth masses, r_in=1.5 au, r_out=23.8 au, gamma=0.1 (Model A)  
  > "we begin with a total dust mass of 5.9$M_{\Earth}$ from Model A in (cite: Wu_2017), one of their best-fit models." (Masses of Hidden Planets) [from (cite: Wu_2017)]
- External data: Lower total gas mass from simple parametric disk model  
  > "We also use a second, lower value of total gas mass that (cite: MacGregor_2017) retrieved using a simple parametric model of disk structure." (Masses of Hidden Planets) [from (cite: MacGregor_2017)]
- External data: Inclination 60 deg, PA 346 deg  
  > "The data are deprojected using an inclination angle $i = 60\degree$ and a position angle $\phi = 346\degree$ (cite: MacGregor_2017)." (Deriving the surface brightness profile of the 1.3 mm continuum) [from (cite: MacGregor_2017)]
- External data: Stellar mass of GQ Lup A 1.05 Msun  
  > "using the mass of GQ Lup A, 1.05$M_{\odot}$ (cite: Wu_2017)" (Masses of Hidden Planets) [from (cite: Wu_2017)]
- External data: Gap width/depth to planet-mass-ratio fitting relations (Tables 1 and 2)  
  > "we select related models from Tables 1 and 2 in (cite: Zhang_2018) to perform our subsequent calculations of planet-star mass ratios." (Masses of Hidden Planets) [from (cite: Zhang_2018)]

## Processing

### Calibration

- pipeline or manual: Followed Wu et al. 2017 reduction steps; three rounds of phase-only self-calibration  
  > "We followed data reduction steps outlined in (cite: Wu_2017), performing three rounds of phase-only self calibration" (Observations and Data Reduction)
- casa version: CASA 5.0.0-218  
  > "Data were reduced using the CASA package (version 5.0.0-218)" (Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: three rounds of phase-only  
  > "performing three rounds of phase-only self calibration with the TCLEAN algorithm with natural weighting" (Observations and Data Reduction)

### Imaging

- task: tclean  
  > "Our continuum map was produced by imaging the calibrated measurement set with the TCLEAN algorithm" (Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "with the TCLEAN algorithm with natural weighting" (Observations and Data Reduction)
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
- final beam: 0.057" x 0.032"  
  > "giving us a synthesized beam of 0$''$057 $\times$ 0$''$032" (Observations and Data Reduction)
- final rms: 56 uJy/beam  
  > "has an rms of 56 ${\mu}$Jy beam$^{-1}$" (Observations and Data Reduction)

### Inherited from earlier work

- Data reduction steps  
  > "We followed data reduction steps outlined in (cite: Wu_2017)" (Observations and Data Reduction) [from (cite: Wu_2017)]
- Parametric Gaussian-sinusoid radial model  
  > "with a parametric function (Equation [\[eq4\]](#eq4)) developed by (cite: Zhang_2016)" (Deriving the surface brightness profile of the 1.3 mm continuum) [from (cite: Zhang_2016)]
- Substructure identification and width definitions  
  > "We employ the same method that (cite: Huang_2018) used to identify substructures in the DSHARP sample" (Characterizing Substructures) [from (cite: Huang_2018)]
- Planet mass inference via gap width/depth relations  
  > "We use fitting relationships outlined by (cite: Zhang_2018) to relate gap width and depth to the planet-star mass ratio, $q$." (Masses of Hidden Planets) [from (cite: Zhang_2018)]

### Not stated but needed to reproduce (our reading)

- Initial guesses for MPFIT parameters
- Cleaning threshold, masks, image size and cell size
- Flux calibrator and calibration details (taken from Wu et al. 2017)
- Visibility binning used for the profile
- Exact fixvis phase center
- Which self-cal solints were used
- Data/model details for the 3-Gaussian fit (parameters not tabulated)
- Depth fitting function form for plateau feature

## Analysis recipe

1. **Calibrate and image continuum**: CASA reduction following Wu et al. 2017, three rounds phase-only self-cal, tclean natural weighting, recentred with fixvis  
  > "We ensure that the image is properly centered by fitting a Gaussian to the continuum source and centering the image using *fixvis* in CASA." (Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: Integrated flux of 26 mJy matches Wu et al. 2017  
  > "we retrieve an integrated flux of 26 mJy for the GQ Lup A disk, well matching results from (cite: Wu_2017)." (Observations and Data Reduction)
2. **Fit radial brightness profile in visibility domain**: Deproject visibilities, fit Gaussians modulated by sinusoids to real visibilities via Hankel transform  
  > "we employ an empirical model-fitting approach in the visibility domain (cite: Pearson)." (Deriving the surface brightness profile of the 1.3 mm continuum)
   - software: MPFIT
   - parameter: i = 60 deg, PA = 346 deg, d = 152 pc; two Gaussians  
  > "We use two Gaussians based on the two peaks seen in the visibility profile" (Deriving the surface brightness profile of the 1.3 mm continuum)
   - assumption: Axisymmetric disk  
  > "For following analysis, we focus only on axisymmetric substructures." (Deriving the surface brightness profile of the 1.3 mm continuum)
   - fitting: Levenberg-Marquardt least squares (MPFIT)  
  > "MPFIT (cite: mpfit), a Levenberg-Marquardt least-squares minimization algorithm" (Deriving the surface brightness profile of the 1.3 mm continuum)
   - validation: Model image compared with observed image; 7 sigma asymmetric residuals  
  > "We find 7$\sigma$ residuals" (Deriving the surface brightness profile of the 1.3 mm continuum)
3. **Identify and measure gaps and rings**: Find local minima/maxima following Huang et al. 2018; plateau via normalized gradient > -0.05; depth by fitting function on either side  
  > "using the condition that $\frac{1}{I_{v}(r)} \frac{dI_{v}(r)}{dr}$ be greater than -0.05 (cite: Huang_2018)" (Characterizing Substructures)
   - fitting: _not stated_
   - validation: _not stated_
4. **Infer hidden planet masses**: Convert disk mass to gas surface density, compute Stokes number, use Zhang et al. 2018 width and depth relations to get q, then planet mass  
  > "We convert from planet-star mass ratios, $q = M_{p}$/$M_{*}$, to planet mass estimates using the mass of GQ Lup A, 1.05$M_{\odot}$" (Masses of Hidden Planets)
   - parameter: h/r = 0.07, alpha = 1e-3 and 1e-4  
  > "We choose the middle values, simulating “average" conditions." (Masses of Hidden Planets)
   - assumption: gas-to-dust ratio 100; gamma = 0.1; max particle size 0.1 mm  
  > "We convert this value to total gas mass using a gas-to-dust ratio of 100." (Masses of Hidden Planets); "assuming a maximum particle size of 0.1 mm (p = 3.5 and s$_{max}$ = 0.1)" (Masses of Hidden Planets)
   - fitting: _not stated_
   - validation: Tested gamma = 1 and 1.5; same choices result  
  > "but proceed with $\gamma$ = 0.1 as all of the distributions lead to the same choices moving forward." (Masses of Hidden Planets)

## Software

- **CASA** 5.0.0-218: Data reduction, self-calibration, tclean imaging, fixvis  
  > "Data were reduced using the CASA package (version 5.0.0-218)" (Observations and Data Reduction)
- **MPFIT** : Fitting parametric model to visibilities  
  > "Model-fitting was performed using MPFIT (cite: mpfit)" (Deriving the surface brightness profile of the 1.3 mm continuum)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Integrated flux of GQ Lup A disk | 26 | not stated | mJy | 1 | we retrieve an integrated flux of 26 mJy for the GQ Lup A disk |
| Gaussian 2 ring location | 1615 | 28 | kλ | 2 | $1615\pm{28}$ |
| Effective radius | 19 | not stated | au | 0 | with an effective radius of 19 au as compared to the average DSHARP size of 50 au |
| D2* gap width | 2.25 | not stated | au | 3 | The gap at 32 au (D2[^1]) has a width of 2.25 au and a depth of 0.957. |
| D1 planet mass range (alpha=1e-4) | 3.07-355 | not stated | Earth masses | 4 | we present a mass range of 3.07-355 $M_{\Earth}$ for D1 |
| D2* planet mass range (alpha=1e-4) | 0.62-2.44 | not stated | Earth masses | 4 | a range of 0.62-2.44 $M_{\Earth}$ for D2\* |

## Qualitative findings

- Compact disk shows substructures (gap near 10 au) similar to DSHARP disks  
  > "The compact disk around GQ Lup exhibits similar substructures to those in the DSHARP sample" (abstract)

## Claim tuples

- H: Compact disks host substructures like large DSHARP disks | E: Visibility-domain fitting of 1.3 mm continuum of GQ Lup A | R: Plateau/gap feature at ~10 au and tentative gap at 32 au | F: Dust trapping mechanisms operate in small disks | **partially**
- H: Gaps may be due to hidden planets | E: Gap width/depth relations of Zhang et al. 2018 | R: Planet masses from ~0.6 to ~724 Earth masses depending on assumptions | F: Possible planet formation at Saturnian distances | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Visibility fitting uses full baselines and recovers smaller scales than CLEAN images  
  > "can recover smaller spatial scale structures than the CLEAN images" (Deriving the surface brightness profile of the 1.3 mm continuum)
- Alternative: Other gap origins (ice condensation fronts, MHD) and tidal interaction with GQ Lup b not excluded  
  > "Other possible origins include changes in dust properties near condensation fronts of dominant ices" (Masses of Hidden Planets)
- How they decided it was enough: _not stated_
- Limitation (authors): Two-Gaussian model underestimates the shortest baselines; D2 is tentative; plateau width poorly measured  
  > "though we note that this model underestimates the uv profile at the shortest baseline" (Deriving the surface brightness profile of the 1.3 mm continuum)
- Caveat (inferred, ours): Single-source, short 11-minute observation
- Caveat (inferred, ours): No formal model comparison between 2 and 3 Gaussian fits
- Caveat (inferred, ours): Planet masses span orders of magnitude and depend on assumed alpha, h/r, dust mass
- Caveat (inferred, ours): Tidal truncation by GQ Lup B not ruled out
- Caveat (inferred, ours): Errors in Table are formal MPFIT errors

## Reproducibility

- Data public (paper): Archival ALMA data cited by project code  
  > "This work makes use of the following ALMA data: ADS/JAO.ALMA $\#$2015.1.00773.S." (Discussion and Conclusions)
- Products in archive: _not stated_
- Missing: Self-calibration solints
- Missing: Clean parameters
- Missing: MPFIT initial guesses
- Missing: 3-Gaussian fit parameters
- Missing: Exact depth-fitting function
- Data volume (inferred): ~10-30 GB
- Score (inferred): 3/5, Public data and simple model, but imaging, self-cal and 3-Gaussian fit details are unspecified.
- Rediscovery candidate: yes, Public archival data, a visibility fit with a published model and numeric table results.

## Links

- Method: (cite: Zhang_2016) (Parametric visibility model)
- Method: (cite: Huang_2018) (Substructure identification method)
- Method: (cite: Zhang_2018) (Planet mass from gap width and depth)
- Companion: (cite: Wu_2017) (Original presentation of the ALMA data and disk model)
- Related: DSHARP

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 47,
  "rate": 0.644
 },
 "evidence_ok": true
}
```
