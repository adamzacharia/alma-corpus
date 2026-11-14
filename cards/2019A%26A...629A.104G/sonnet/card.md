# Sunyaev-Zel'dovich detection of the galaxy cluster Cl J1449+0856 at z = 1.99: The pressure profile in uv space

`2019A&A...629A.104G` | Astronomy and Astrophysics 2019 | first author: Gobat, R. | arXiv: 1907.10985 | DOI: 10.1051/0004-6361/201935862

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: galaxy_clusters_and_sz
- Question: Can the thermal SZ decrement of the z=1.99 cluster Cl1449 be detected with ALMA+ACA at 92 GHz after subtracting FIR point sources in uv space, and what do the pressure profile and total mass imply?  
  > "We thus approach the SZ effect in this cluster from two different perspectives: as yielding an independent constraint on its total mass" (Introduction)
- Target **Cl J1449+0856 (Cl1449)**: coordinates RA 14:49:14, Dec +08:56:26 (phase centre)  
  > "Cl J1449+0856 (hereafter Cl1449) is a young galaxy cluster at $z=1.995$ (cite: Gob13)" (Introduction); "a phase centre at R.A. = 14:49:14 and Dec = 8:56:26" (Observations and data reduction); z/distance z = 1.995  
  > "Cl J1449+0856 (hereafter Cl1449) is a young galaxy cluster at $z=1.995$ (cite: Gob13)" (Introduction); "a phase centre at R.A. = 14:49:14 and Dec = 8:56:26" (Observations and data reduction); distance from Gobat et al. 2013  
  > "Cl J1449+0856 (hereafter Cl1449) is a young galaxy cluster at $z=1.995$ (cite: Gob13)" (Introduction); "a phase centre at R.A. = 14:49:14 and Dec = 8:56:26" (Observations and data reduction)

## Data provenance

- ALMA projects: 2012.1.00885.S, 2015.1.01355.S
- bands: Band 3, central frequency 92 GHz  
  > "The data were taken in Band 3, with a central frequency of 92 GHz" (Observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA (most compact configuration) and ACA  
  > "we chose the most compact ALMA configuration to minimise signal loss due to over-resolution" (Observations and data reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ACA 16.86"x13"; ALMA 4.23"x3.58"  
  > "| ALMA |      9.7       |           4           | $4.23\times3.58$ |" (Table 1)
- max recoverable scale: 29" in cycle 4  
  > "the maximum recoverable scale being 29” in cycle 4" (Observations and data reduction)
- sensitivity: ~22 (ACA) and ~4 (ALMA) uJy/beam point-source rms  
  > "with a r.m.s. (root mean square) point-source sensitivity of $\sim$22 and $\sim$4 $\mu$Jy/beam, respectively" (Observations and data reduction)
- time on source: 49 h ACA, 9.7 h ALMA  
  > "total observing times of 49h for ACA and 9.7h for ALMA" (Observations and data reduction)
- observing dates: November 2016 to March 2017  
  > "were carried out between November 2016 and March 2017 as single pointings" (Observations and data reduction)
- pi or archival as stated: PI Gobat (2016.1.01107)  
  > "under program 2016.1.01107 (PI Gobat)" (Observations and data reduction)
- Other facility **CARMA 31 GHz**: 31 GHz data, 31.4 h, rms 90 uJy/beam, used for an SZ upper limit  
  > "We find a continuum r.m.s. noise limit of 90 $\mu$Jy/beam across the full 8 GHz bandwidth." (31 GHz observations)
- Other facility **Chandra**: X-ray mass constraint and X-ray peak position  
  > "consistent with the *Chandra* constraint of $M_{200}\sim6\times10^{13}$ M$_{\odot}$ (cite: Val16)" (Results and discussion)
- Other facility **ALMA 870 um and CO(4-3) (C18)**: positions and fluxes of FIR sources  
  > "we use higher-resolution ALMA 870 $\mu$m and CO(4–3) observations of Cl1449 (described in C18)" (Observations and data reduction)
- External data: Positions/fluxes of FIR emitters from 870um and CO(4-3) data  
  > "To determine the positions and fluxes of the sources, we use higher-resolution ALMA 870 $\mu$m and CO(4–3) observations of Cl1449 (described in C18)." (Observations and data reduction) [from C18 (Coogan et al. 2018) (cite: Coo18)]
- External data: SED templates for 92 GHz flux expectations  
  > "we also compare the recovered fluxes to the 92 GHz expectations from (cite: Mag12) spectral energy distribution (SED) templates" (Observations and data reduction) [from (cite: Mag12)]
- External data: Chandra M200 ~6e13 Msun  
  > "consistent with the *Chandra* constraint of $M_{200}\sim6\times10^{13}$ M$_{\odot}$ (cite: Val16)" (Results and discussion) [from (cite: Val16)]
- External data: 3 mm number counts  
  > "we use the 3 mm number counts distribution of (cite: Zav18), extrapolating it to arbitrarily low fluxes" (Lensed background) [from (cite: Zav18)]
- Simulation/model as data: GNFW pressure models (LeB15 REF/AGN 8.0/AGN 8.5, A10, S16, McD14) projected and passed through simalma  
  > "We use the 2D models as inputs for noise-free simulations of ACA and ALMA observations using the `simalma` task in CASA" (Modelling)

## Processing

### Calibration

- pipeline or manual: Raw data reduced with CASA and ALMA-provided script to generate measurement sets  
  > "We reduce the raw data using the CASA software suite (cite: CASA) and the script provided by ALMA to generate measurement sets" (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting throughout  
  > "We use natural weighting for imaging throughout the paper." (Observations and data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: ALMA and ACA visibilities merged in uv; maps merged for display  
  > "A merged ALMA+ACA map of the resulting data is shown in Fig. [2](#fig:image) (C)" (Observations and data reduction)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Source positions and fluxes priors from higher-resolution ALMA data  
  > "we use higher-resolution ALMA 870 $\mu$m and CO(4–3) observations of Cl1449 (described in C18)" (Observations and data reduction) [from C18 (cite: Coo18)]
- Gas fraction and temperature model A for beta-model  
  > "assume the gas fraction and temperature model A from (cite: DR15)" (beta-model fit) [from (cite: DR15)]

### Not stated but needed to reproduce (our reading)

- CASA version
- Fit method/statistic and uncertainty treatment for model amplitude and mass (chi2 minimisation details)
- How M200 was extrapolated from M500 numerically
- simalma setup details (configurations, antenna lists)
- Point-source subtraction details for source grouping
- Details of how ALMA and ACA were weighted when merged
- Whether 2012.1.00885.S and 2015.1.01355.S data were used directly (C18 data)

## Analysis recipe

1. **Subtract FIR point sources in uv space**: Measure fluxes of 9 known sources in ALMA data with uv>30 m, then subtract point-source models from ALMA and ACA visibilities over all uv, in groups of 4 from brightest to faintest  
  > "Where possible we model and subtract the sources by groups of 4, iteratively from brightest to faintest, to minimise contamination." (Observations and data reduction)
   - software: GILDAS
   - parameter: uv>30 m for flux measurement (50 m tested)  
  > "using only visibilities with *uv*-distance ($\sqrt{u^2+v^2}$; hereafter *uv*) of $uv>30$ m" (Observations and data reduction)
   - assumption: Sources are point-like given the large beams  
  > "In both cases we model them as point sources, since the beams are large compared to the sizes found in C18." (Observations and data reduction)
   - fitting: _not stated_
   - validation: Compared recovered fluxes with Magdis+12 SED template expectations  
  > "As a sanity check, we also compare the recovered fluxes to the 92 GHz expectations from (cite: Mag12) spectral energy distribution (SED) templates, finding consistency" (Observations and data reduction)
2. **Extract uv-amplitude profile**: Fit complex visibilities with a point source in uv bins using UV_FIT; fixed position; errors from rms of fits at randomised offsets  
  > "then extract fluxes at fixed position in *uv* bins of 6–13.5 m, 13.5–18.75 m, 18.75–25.5 m, 25.5–50 m, 50–100 m, and 100–300 m" (Analysis)
   - software: GILDAS UV_FIT
   - parameter: initial free-position fit in uv=6-25 m  
  > "We first perform the fit in a large bin of $uv=6-25$ m, leaving the offset $(x,y)$ free" (Analysis)
   - fitting: Point-source model V = const x exp(-2 pi i (ux+vy))  
  > "We choose the point-source model for simplicity" (Analysis)
   - validation: Noise from point-source fits at randomised large offsets  
  > "instead use the r.m.s. noise as measured in each bin with a point-source fit at randomised large offset positions" (Analysis)
3. **Fit pressure models and derive mass**: Project GNFW profiles (LeB15, A10, S16, McD14) with fixed shapes, simulate with simalma, compare to uv profile with free mass; chi2 ranking  
  > "While we keep the GNFW parameters fixed to the various models’ values, we let the mass vary freely." (Modelling)
   - software: CASA simalma
   - parameter: Compton-y background 1.6e-6  
  > "including an average Compton-*y* background of $1.6\times10^{-6}$" (Modelling)
   - assumption: Spherical models; M200 extrapolated from M500 assuming GNFW mass distribution  
  > "We here therefore extrapolate $M_{200}$ from $M_{500}$, assuming that the mass distribution follows the GNFW profile." (Modelling)
   - fitting: _not stated_
   - validation: FFT approximation vs simalma differs at most ~4%  
  > "We find a relative difference between both of at most $\sim$4% (Fig. [10](#fig:fft))" (uv plane modelling)
4. **Fit beta-model**: Forward Fourier transform of deprojected beta-model sampled at data uv, free r_c and beta over a grid  
  > "We use an expanding parameter grid with $(r_c>0.1,\beta>0.1)$ and steps of $(\Delta r_c,\Delta\beta)=(0.01,0.01)$." (beta-model fit)
   - assumption: Primordial abundances; gas fraction and temperature model A of DR15  
  > "We then assume primordial abundances and assume the gas fraction and temperature model A from (cite: DR15)." (beta-model fit)
   - fitting: _not stated_
   - validation: _not stated_
5. **Test SZ-X-ray peak offset significance**: Monte Carlo of simulated A10 decrement with noise from visibility weights, point-source fit with free position  
  > "We then perform a point-source extraction with free position, as described in Section [\[cooking\]](#cooking), which we compare to the observed offsets." (Peak offset significance)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : data reduction and simalma simulations  
  > "We reduce the raw data using the CASA software suite (cite: CASA)" (Observations and data reduction)
- **GILDAS** : point-source subtraction and UV_FIT visibility fitting  
  > "using the `UV_FIT` task GILDAS" (Analysis)
- **Miriad** : CARMA data reduction  
  > "The data were then reduced using the `Miriad` (cite: Sau95) software package." (31 GHz observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total SZ signal (ALMA+ACA, after point-source subtraction) | -190 | 36 | uJy | 2 | the total signal over all angular scales is $-190\pm36$ $\mu$Jy, with a significance of 5.3$\sigma$ |
| Signal when removing only interlopers/unconfirmed sources | -123 | 40 | uJy | 2 | a signal is marginally detected at $-123\pm40$ $\mu$Jy |
| Offset of SZ peak from phase centre | (4.4, 4.3) | not stated | arcsec | 2 | offset from the phase centre by $\Delta(RA,DEC)=(4.4,4.3)$” |
| 31 GHz signal at fixed positions | 0 | 120 | uJy | 0 | We find $0\pm120$ $\mu$Jy, which implies a 3$\sigma$ “upper” limit to the 31  GHz signal of $\sim$-360 $\mu$Jy |
| AGN 8.5 model mass | ~1.8e14 | not stated | Msun | 3 | only AGN 8.5 yields a higher mass of $\sim$$1.8\times10^{14}$ M$_{\odot}$ |

## Qualitative findings

- Point-source subtraction was essential; confirmed cluster members fill ~35% of the decrement  
  > "The filling of the decrement by confirmed cluster members thus amounts to $\sim$35% of the signal" (Analysis)

## Claim tuples

- H: The SZ decrement of Cl1449 is detectable with ALMA+ACA | E: Subtract 9 FIR sources in uv space and fit uv-amplitude profile | R: -190±36 uJy, 5.3 sigma | F: Secure ~5 sigma SZ detection | **supported**
- H: SZ-derived mass agrees with Chandra | E: Fit pressure models with free mass | R: Most models consistent with M200~6e13; AGN 8.5 gives 1.8e14 | F: Chandra mass confirmed, with ~factor 2 model spread | **supported**
- H: Pressure profile follows local calibrated models | E: Compare uv profile with GNFW models and beta-model | R: McD14 fits best; other models show a small tension at uv~30 m | F: Data limited; flat inner profile possibly due to residual sources or pressure deficit | **partially**

## Reasoning

- Why this data: 92 GHz chosen as compromise between integration time and dust contamination; compact config to avoid resolving out signal  
  > "this frequency was chosen as a compromise to both optimise the total integration time and minimise positive contamination" (Observations and data reduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Residual positive signal from undetected sources means significance is conservative; S/N too low to strongly constrain pressure models  
  > "The final S/N of the data, conservatively estimated, is not quite high enough to strongly constrain ICM pressure models." (Conclusions)
- Caveat (inferred, ours): Results depend on point-source flux subtraction with sources from other datasets
- Caveat (inferred, ours): Mild ALMA/ACA tension attributed to noise
- Caveat (inferred, ours): Fit statistics and covariance between uv bins not described

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version and calibration details
- Missing: Fit procedure details and error treatment for models
- Missing: Access to C18 source catalogue
- Data volume (inferred): ~100-300 GB raw for ALMA+ACA Band 3
- Score (inferred): 3/5, Data are in the archive and methods are described in outline, but key fitting and simulation settings are not given.
- Rediscovery candidate: no, Recipe lacks fitting and simulation details, and depends on external source catalogue.

## Links

- Method: Coogan et al. 2018 (cite: Coo18) (source positions/fluxes)
- Companion: Valentino et al. 2016 (cite: Val16) (Chandra mass and Lya nebula)
- Related: CARMA c0865

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2015.1.01355.S"
 ],
 "obscore_codes_not_in_card": [
  "2016.1.01107.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 46,
  "rate": 0.582
 },
 "evidence_ok": true
}
```
