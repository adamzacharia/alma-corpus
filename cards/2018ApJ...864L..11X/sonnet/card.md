# Flat Rotation Curves Found in Merging Dusty Starbursts at z = 2.3 through Tilted-ring Modeling

`2018ApJ...864L..11X` | The Astrophysical Journal Letters 2018 | first author: Xue, Rui | arXiv: 1807.04291 | DOI: 10.3847/2041-8213/aad9a9

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the resolved gas kinematics, rotation curves and dynamical masses of the merging starburst HXMM01, and what upper limits do they place on alpha_CO?  
  > "we present 0.2$''$-resolution gas kinematics of HXMM01 traced by two molecular lines and one atomic line from observations with the Atacama Large Millimeter/submillimeter Array (ALMA)." (Introduction)
- Target **HXMM01 (HerMES J022016.5-060143)**: coordinates alpha_J2000=02h20m16.613s, delta_J2000=-06d01m43.15s (pointing center)  
  > "The observations consisted of a single pointing towards the approximate center of HXMM01" (2.1 ALMA Band-6 Observations); "the bright *Herschel* source ($S_{\rm500\mu m}=132$ mJy) at $z = 2.308$" (Introduction); z/distance z = 2.308  
  > "The observations consisted of a single pointing towards the approximate center of HXMM01" (2.1 ALMA Band-6 Observations); "the bright *Herschel* source ($S_{\rm500\mu m}=132$ mJy) at $z = 2.308$" (Introduction); distance from previous observations (Fu et al. 2013), not explicitly cited at this point  
  > "The observations consisted of a single pointing towards the approximate center of HXMM01" (2.1 ALMA Band-6 Observations); "the bright *Herschel* source ($S_{\rm500\mu m}=132$ mJy) at $z = 2.308$" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00723.S, 2011.0.00539.S
- bands: Band 6, 226-245 GHz  
  > "ALMA band-6 observations of HXMM01 were carried out on 2016 August 2, 14, 15, and 17" (2.1 ALMA Band-6 Observations)
- frequencies and spectral setup: three 2 GHz windows on CO 7-6, [CI] 2-1, H2O lines plus one continuum window at 230 GHz; 1875 MHz effective bandwidth, 15.625 MHz channels  
  > "Each window had an effective bandwidth of 1875 MHz and a channel spacing of 15.625 MHz." (2.1 ALMA Band-6 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-5, 38-45 antennas  
  > "with thirty-eight to forty-five antennas online in the C40-5 configuration" (2.1 ALMA Band-6 Observations)
- baselines: _not stated_
- angular resolution: 0.24'' x 0.18'' at CO 7-6, P.A.=84 deg  
  > "is 0.24$''$$\times$0.18$''$ with P.A.=84$^\circ$" (2.1 ALMA Band-6 Observations)
- max recoverable scale: _not stated_
- sensitivity: ~0.02 mJy/beam 1 sigma at center of 230 GHz continuum  
  > "The $1\sigma$ noise at the center of the 230 GHz continuum map reaches $\sim0.02$ mJy beam$^{-1}$" (2.1 ALMA Band-6 Observations)
- time on source: 2.6 hr  
  > "The total on-source integration time was 2.6 hr" (2.1 ALMA Band-6 Observations)
- observing dates: 2016 August 2, 14, 15, 17  
  > "carried out on 2016 August 2, 14, 15, and 17" (2.1 ALMA Band-6 Observations)
- pi or archival as stated: _not stated_
- Line: p-H2O 2_11-2_02 (752.03314 GHz)
- Line: CO J=7-6 (806.65181 GHz)
- Line: CI 3P2-3P1 (809.34197 GHz)
- Line: CO J=1-0 (VLA archival) (115.27120 GHz)
- Other facility **VLA**: archival CO J=1-0 data (DnC, C, B configs), reprocessed in CASA  
  > "were obtained with the Karl G. Jansky Very Large Array (VLA) in the DnC, C, and B configurations in 2012" (2.2 Archival CO J=1-0 Data)
- Other facility **Chandra**: X-ray non-detection (77 ks ACIS-S)  
  > "Our 77 ks Chandra ACIS-S observations (Obs-ID: 14972) did not detect any significant X-ray emission" (Introduction)
- External data: Lensing magnification mu~1.6 used for correction estimate  
  > "Taking an average magnification factor of $\mu\approx1.6$ from , a lensing correction may increase our $\alpha_{\rm CO}$ upper limits by up to 30%." (3.3 Rotation Curve, Dynamical Mass, and alpha_CO) [from previous HXMM01 paper (Fu et al. 2013; citation not printed in text)]
- External data: Line collisional coefficients for critical densities  
  > "using the coefficients from the Leiden Atomic and Molecular Database (cite: Schoier:2005wx)" (Table 1) [from (cite: Schoier:2005wx)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline in CASA  
  > "The raw data were calibrated using the ALMA pipeline in the Common Astronomy Software Application" (2.1 ALMA Band-6 Observations)
- casa version: CASA 5.1.2 (for continuum subtraction and imaging)  
  > "data imaging in CASA ver. 5.1.2" (2.1 ALMA Band-6 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0006-0623 (flux); J0238+1636 (bandpass); J0241-0815 (phase)  
  > "The bandpass and flux density calibrators are J0238$+$1636 and J0006$-$0623, respectively." (2.1 ALMA Band-6 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: mstransform (uv continuum subtraction) and tclean  
  > "using the `mstransform` and `tclean` tasks, respectively" (2.1 ALMA Band-6 Observations)
- deconvolver: multi-scale clean  
  > "we adopted the multi-scale clean algorithm implemented in `tclean`" (2.1 ALMA Band-6 Observations)
- weighting robust: Briggs, robust = 0  
  > "We used the Briggs image weighting scheme with `robust = 0` to suppress sidelobes." (2.1 ALMA Band-6 Observations)
- uv taper: _not stated_
- cell size: 0.03''  
  > "so we set a pixel size of 0.03$''$ to oversample the beam" (2.1 ALMA Band-6 Observations)
- image size: _not stated_
- masking: circular CLEAN mask radius 10'' centered on HXMM01  
  > "applied a circular CLEAN mask with a radius of 10$''$ centered at HXMM01" (2.1 ALMA Band-6 Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: data maps corrected for 12 m primary beam; separate uncertainty map  
  > "a “data” map which is corrected for the primary beam response of ALMA 12 m antenna" (2.1 ALMA Band-6 Observations)
- array combination: _not stated_
- smoothing: channel width 40 km/s  
  > "We thus set a channel width of 40 $\rm km\,s^{-1}$ for spectral line imaging" (2.1 ALMA Band-6 Observations)
- final beam: 0.24'' x 0.18'' P.A.=84 deg (CO 7-6)  
  > "is 0.24$''$$\times$0.18$''$ with P.A.=84$^\circ$" (2.1 ALMA Band-6 Observations)
- final rms: ~0.02 mJy/beam (continuum)  
  > "reaches $\sim0.02$ mJy beam$^{-1}$" (2.1 ALMA Band-6 Observations)

### Inherited from earlier work

- Earlier data product of the same VLA CO 1-0 observations reduced in AIPS with different 3C48 flux scale; here reprocessed in CASA  
  > "presented the earlier data product of the same observations, in which the reduction was performed in `AIPS` with a slightly different flux scaling for 3C 48" (2.2 Archival CO J=1-0 Data) [from previous HXMM01 paper (Fu et al. 2013)]
- VLA CO 1-0 imaged with tclean as for ALMA  
  > "We performed imaging with `tclean` as in § [2.1](#sec:alma)." (2.2 Archival CO J=1-0 Data) [from Section 2.1]

### Not stated but needed to reproduce (our reading)

- Multi-scale clean scales and cleaning threshold/niter
- Line-free channels used for continuum subtraction and polynomial order
- Mask details: smoothing kernel for the 3D detection masks and the 4 sigma/2 sigma noise reference
- emcee settings: number of walkers, steps, burn-in, convergence criterion
- Free-parameter bounds (flat priors), SB distortion amplitude details and node angle value
- Number of rings per component and outer radius used
- Aperture coordinates for spectral extraction
- How the r_s,mass-based alpha_CO is computed (luminosity weighting details, CO 1-0 to luminosity conversion)
- Version numbers for TiRiFiC, emcee, Astropy and the pipeline
- Spectral windows used for combined CO 7-6 + [CI] cube

## Analysis recipe

1. **Calibrate and image ALMA Band 6 cubes**: ALMA pipeline calibration; uv continuum subtraction with mstransform; tclean multi-scale imaging with Briggs weighting  
  > "We performed the $uv$-plane continuum subtraction and data imaging in CASA ver. 5.1.2, using the `mstransform` and `tclean` tasks, respectively." (2.1 ALMA Band-6 Observations)
   - software: CASA, mstransform, tclean
   - parameter: robust = 0, pixel 0.03'', channel 40 km/s  
  > "We used the Briggs image weighting scheme with `robust = 0` to suppress sidelobes." (2.1 ALMA Band-6 Observations)
   - fitting: _not stated_
   - validation: continuum noise consistent with expectation  
  > "reaches $\sim0.02$ mJy beam$^{-1}$, consistent with expectation." (2.1 ALMA Band-6 Observations)
2. **Make masked moment maps, PV plot and integrated line fluxes**: 3D detection masks (>=4 sigma regions in smoothed cube, expanded to 2 sigma, padded 2 pixels); spectra from rectangular apertures  
  > "The masking algorithm first searches for $\geqslant4\sigma$ continuous regions in 3D smoothed datacubes, then expands each of them to the surrounding 2$\sigma$ contour" (3.1 Detection of CO, [C I], and H2O)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit 3D tilted-ring models to CO 7-6 + [CI] cube**: TiRiFiC forward-modeled disks per component (shared center, inclination, P.A.; ring step 0.1''; exponential SB with first-order sinusoidal distortion; constant dispersion per line; same rotation curve for all lines), likelihood on independent beam elements via hexagon resampling  
  > "We adopt a step size of 0.1$''$, which is roughly half of the beam FWHM." (3.2 Kinematic Modeling with Tilted-Ring Models); "we only consider independent beam elements when evaluating the likelihood function" (3.2 Kinematic Modeling with Tilted-Ring Models)
   - software: TiRiFiC, emcee
   - parameter: ring step 0.1'' (0.84 kpc)  
  > "Due to the relatively large step size (0.1$''$ = 0.84 kpc)" (3.2 Kinematic Modeling with Tilted-Ring Models)
   - assumption: constant velocity dispersion across each disk; same rotation curve for all lines; H2O excluded due to low S/N  
  > "for simplicity we assume constant velocity dispersion across each disk but allow it to vary among different lines" (3.2 Kinematic Modeling with Tilted-Ring Models)
   - fitting: emcee affine-invariant sampler, Gaussian likelihood with error scaling factor eta, bounded flat priors  
  > "Starting from bounded “flat” priors for all free parameters, we iterate with `emcee` until the posterior distribution of model parameters are sampled adequately." (3.2 Kinematic Modeling with Tilted-Ring Models)
   - validation: compared PV maps of data and best-fit models; tested fixed outer-ring dispersion  
  > "we compare the PV maps from the \[C I\]$\,{{^3P_2}\to{^3P_1}}$ and ${\rm CO\,{\it J}=7\to 6}$ data cube and the best-fit `TiRiFiC` models in Figure [3](#fig:pvmom0)" (3.2 Kinematic Modeling with Tilted-Ring Models)
4. **Model VLA CO 1-0 surface brightness**: Fit CO 1-0 cube with same 3D approach using best-fit ALMA kinematic models  
  > "using our reprocessed VLA ${\rm CO\,{\it J}=1\to 0}$ datacube and the best-fit kinematic models from the high-resolution ALMA data" (3.3 Rotation Curve, Dynamical Mass, and alpha_CO)
   - software: TiRiFiC, emcee
   - fitting: _not stated_
   - validation: scale lengths agree with [CI] within errors  
  > "the values do agree with those of \[C I\]$\,{{^3P_2}\to{^3P_1}}$ within the error margins" (3.3 Rotation Curve, Dynamical Mass, and alpha_CO)
5. **Derive dynamical mass and alpha_CO upper limit**: Enclosed mass of thin exponential disk from rotation curve; divide by CO 1-0 flux within radius; median over 3-5 kpc  
  > "The ratio between the dynamic mass and the corresponding integrated ${\rm CO\,{\it J}=1\to 0}$ line flux provides strict upper limit of the CO$\to$H$_2$ conversion factor" (3.3 Rotation Curve, Dynamical Mass, and alpha_CO)
   - assumption: disk mass and CO 1-0 scale lengths equal that of [CI]; entire support by rotation; no lensing correction  
  > "Assuming that the scale-lengths of the disk mass and ${\rm CO\,{\it J}=1\to 0}$ brightness distribution" (3.3 Rotation Curve, Dynamical Mass, and alpha_CO)
   - fitting: _not stated_
   - validation: spherical case +10-30%; CO 1-0 own scale length gives 2.2; lensing up to +30%  
  > "a lensing correction may increase our $\alpha_{\rm CO}$ upper limits by up to 30%" (3.3 Rotation Curve, Dynamical Mass, and alpha_CO)

## Software

- **CASA** 5.1.2: pipeline calibration, mstransform, tclean imaging  
  > "data imaging in CASA ver. 5.1.2" (2.1 ALMA Band-6 Observations)
- **TiRiFiC** : tilted-ring simulated spectral cubes  
  > "We use the tilted-ring modeling code `TiRiFiC`" (3.2 Kinematic Modeling with Tilted-Ring Models)
- **emcee** : MCMC fitting  
  > "we use the Python Affine Invariant MCMC Ensemble sampler `emcee`" (3.2 Kinematic Modeling with Tilted-Ring Models)
- **RADEX** : non-LTE modeling of CO SLED  
  > "A non-LTE radiative transfer modeling analysis using `RADEX`" (3.1 Detection of CO, [C I], and H2O)
- **AIPS** : earlier VLA reduction in prior paper  
  > "the reduction was performed in `AIPS`" (2.2 Archival CO J=1-0 Data)
- **Astropy** : listed in software section  
  > "CASA (cite: McMullin:2007ta), Astropy (cite: AstropyCollaboration:2013cd)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Vmax component a | 542 | +105/-108 | km/s | 3 | $V_{{\rm max}}$ / $\rm km\,s^{-1}$ / $542_{-108}^{+105}$ |
| Vmax component b | 486 | +54/-81 | km/s | 3 | $486_{-81}^{+54}$ |
| Inclination a / b / c | 79 / 60 / 69 | 2 / 5 / 4 | degree | 3 | $79\pm2$ / $60\pm5$ / $69\pm4$ |
| Dynamical mass within 5 kpc, comp a | 2.3 | +0.3/-0.5 | 1e11 Msun | 5 | $2.3_{-0.5}^{+0.3}$ |
| Dynamical mass within 5 kpc, comp b | 1.8 | +0.6/-0.5 | 1e11 Msun | 5 | $1.8_{-0.5}^{+0.6}$ |
| alpha_CO limit a / b | 1.4 / 2.0 | not stated | Msun (K km/s pc^2)^-1 | 5 | The median $\alpha_{\rm CO}$ limits estimated from this radius range equal 1.4 and 2.0 |
| CO 7-6 flux a / b / c | 6.2 / 3.5 / 0.9 | 0.2 / 0.1 / 0.1 | Jy km/s | 2 | $6.2\pm0.2$ / $3.5\pm0.1$ / $0.9\pm0.1$ |
| 230 GHz continuum a / b / c | 4.3 / 3.6 / 0.5 | 0.1 / 0.1 / 0.1 | mJy | 2 | $4.3\pm0.1$ / $3.6\pm0.1$ / $0.5\pm0.1$ |
| alpha_CO with CO 1-0 scale length | 2.2 | not stated | Msun (K km/s pc^2)^-1 | 5 | the $\alpha_{\rm CO,limit}$ values will increase to 2.2 |

## Qualitative findings

- HXMM01 resolves into three components within 20 kpc and 2000 km/s; two major components have flat rotation curves ~500 km/s; CO 7-6 more asymmetric than [CI]  
  > "the source is resolved into three distinct components, which are spatially and dynamically associated within a projected radius of 20$\,$kpc" (abstract)

## Claim tuples

- H: Do the major components have declining or flat rotation curves? | E: 3D tilted-ring MCMC modeling of CO 7-6 and [CI] cubes | R: Vmax ~540 and ~490 km/s, plateau out to ~5 kpc | F: Flat rotation curves, no sign of decline out to 4-5 kpc | **supported**
- H: Is alpha_CO in HXMM01 Galactic-like? | E: Dynamical mass divided by CO 1-0 luminosity | R: alpha_CO limits 1.4-2.0 | F: Lower than Galactic 4.3, consistent with local starbursts; short depletion time unchanged | **supported**
- H: Are the disks rotation supported? | E: Vmax/sigma from models | R: Vmax/sigma >~3 with sigma as upper limits | F: Mainly rotationally supported but highly turbulent | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: 3D forward modeling avoids beam-smearing biases of velocity-field fitting and handles blended components  
  > "Secondly, we can generate synthetic cubes that include multiple spatial and kinematic components." (3.2 Kinematic Modeling with Tilted-Ring Models)
- Alternative: Fixing dispersion to outer-ring values degraded fit to inner disks  
  > "However, the goodness of fit degrades for inner disks." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): No lensing correction; possible merger non-equilibrium motions; sigma only an upper limit  
  > "We caution that we do *not* include any lensing correction in the analysis of dynamical mass and $\alpha_{\rm CO}$" (3.3 Rotation Curve, Dynamical Mass, and alpha_CO)
- Caveat (inferred, ours): Disk assumption for merging clumpy systems may not hold
- Caveat (inferred, ours): alpha_CO limit depends on [CI] scale length standing in for CO 1-0 and on thin exponential disk
- Caveat (inferred, ours): Constant dispersion and shared rotation curve across lines are simplifying choices

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code; VLA described as archival  
  > "The ${\rm CO\,{\it J}=1\to 0}$ data of HXMM01 were obtained with the Karl G. Jansky Very Large Array" (2.2 Archival CO J=1-0 Data)
- Products in archive: _not stated_
- Missing: emcee configuration and priors
- Missing: multi-scale clean scales and thresholds
- Missing: aperture definitions and TiRiFiC parameter setup
- Data volume (inferred): ~50-150 GB raw ALMA plus VLA
- Score (inferred): 3/5, Public data and clear method outline, but many modeling and imaging parameters are unstated.
- Rediscovery candidate: no, Key MCMC/TiRiFiC setup details are missing, so redoing the recipe is not feasible from the text alone.

## Links

- Method: (cite: Jozsa:2007ey) (TiRiFiC tilted-ring code)
- Method: (cite: Goodman:2010et) (emcee sampler)
- Companion: Fu et al. 2013 (cite: Fu:2013hz) (previous HXMM01 observations and discovery)
- Related: Herschel HerMES
- Related: VLA 11B-044 and 12A-201

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 54,
  "rate": 0.701
 },
 "evidence_ok": true
}
```
