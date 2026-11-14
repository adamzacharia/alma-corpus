# ALMA observations of the multiplanet system 61 Vir: what lies outside super-Earth systems?

`2017MNRAS.469.3518M` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Marino, S. | arXiv: 1705.01944 | DOI: 10.1093/mnras/stx1102

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks, exoplanets
- Question: Where is the planetesimal disc around 61 Vir and what is its mm-grain surface density profile; what does this imply for collisional evolution and for an unseen stirring planet?  
  > "obtained with the aim of studying its debris disc to reveal the location of the parent planetesimals, and place constraints on the presence of planets at large separations" (Introduction)
- Target **61 Vir (HD 115617)**: coordinates _not stated_; z/distance 8.6 pc  
  > "This system located at 8.6 pc (cite: vanLeeuwen2007) is composed of : 1) a G5 $4.6\pm0.9$ Gyr old star" (Introduction); distance from van Leeuwen 2007  
  > "This system located at 8.6 pc (cite: vanLeeuwen2007) is composed of : 1) a G5 $4.6\pm0.9$ Gyr old star" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00359.S
- bands: Band 7 (0.86 mm)  
  > "ALMA band 7 (0.86 mm) observations of 61 Vir were carried out on 2015 April" (3 ALMA Observations)
- frequencies and spectral setup: 3 continuum SPWs at 333.84, 335.78, 347.74 GHz; 1 SPW at 344.85 GHz for CO 3-2 with 3840 channels, 0.42 km/s width  
  > "three spectral windows to image the continuum centered at 333.84, 335.78 and 347.74 GHz" (3 ALMA Observations); "with 3840 channels, a channel width of 0.42 km s$^{-1}$" (3 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 to 349 m, 44 antennas  
  > "The total number of antennas was 44, with baselines ranging from 15 to 349 m" (3 ALMA Observations)
- angular resolution: _not stated_
- max recoverable scale: 6 arcsec  
  > "This allows us to recover angular scales of $0.6\ensuremath{''}$ up to $6\ensuremath{''}$ on the sky." (3 ALMA Observations)
- sensitivity: 16 uJy/beam at centre, 32 at 7.5"  
  > "we achieve a rms noise level of 16 $\mu$Jy beam$^{-1}$, which increases to 32 $\mu$Jy beam$^{-1}$ at $7.5\ensuremath{''}$" (3.1 Continuum emission)
- time on source: 178 min  
  > "The total time on source excluding overheads was 178 min." (3 ALMA Observations)
- observing dates: 2015 April 9 and 22 (4 scheduling blocks)  
  > "split into 4 scheduling blocks (one on April 9 and three on April 22)" (3 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (v=0) (not stated)
- Other facility **SCUBA2/JCMT**: 0.85 mm image, 7.5 h, flux 5.0±1.2 mJy  
  > "61 Vir was observed for 7.5 h" (2 SCUBA2 observations)
- Other facility **Herschel**: Prior disc orientation and inner radius constraints  
  > "The disc was later imaged by Herschel showing that the disc density peaks between 30 and 100 AU" (Introduction)
- External data: Disc PA 65 deg and inclination 77 deg from Herschel, used for deprojection and priors  
  > "assuming a disc PA and inclination of $65\ensuremath{^\circ}$ and $77\ensuremath{^\circ}$, respectively (cite: Wyatt2012)" (3.1 Continuum emission) [from (cite: Wyatt2012)]

## Processing

### Calibration

- pipeline or manual: ALMA-provided pipeline  
  > "Calibrations were applied using the pipeline provided by ALMA." (3 ALMA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (J1337-1257 bandpass and phase)  
  > "J1337-1257 was used as Bandpass and phase calibrator, with Titan as amplitude and flux calibrator." (3 ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA 4.4  
  > "using the task CLEAN in CASA 4.4 (cite: McMullin2007) with natural weights and correcting for the primary beam" (3.1 Continuum emission)
- deconvolver: _not stated_
- weighting robust: natural weights  
  > "with natural weights and correcting for the primary beam" (3.1 Continuum emission)
- uv taper: Gaussian FWHM 1.5" for smoothed image  
  > "tapering the visibilities with the Fourier transform of a Gaussian of FWHM of $1.5\ensuremath{''}$" (3.1 Continuum emission)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.1"x0.7", PA -70 deg (tapered: 1.8"x1.5")  
  > "The beam size is $1.1\ensuremath{''}\times0.7\ensuremath{''}$ with a position angle (PA) of $-70^{\circ}$." (3.1 Continuum emission)
- final rms: 16 uJy/beam at centre  
  > "we achieve a rms noise level of 16 $\mu$Jy beam$^{-1}$" (3.1 Continuum emission)

### Inherited from earlier work

- SCUBA2 SONS data reduction details  
  > "More details on the SCUBA2 data reduction of the SONS survey can be found in (cite: Matthews2015) and (cite: Kennedy2015superearths)." (2 SCUBA2 observations) [from (cite: Matthews2015); (cite: Kennedy2015superearths)]
- Collisional model method  
  > "This method is described in detail in (cite: Wyatt2011) (see Sec. 2.4.2, 2.5 and 2.9 therein)" (5 Steady state collisionally evolved disc model) [from (cite: Wyatt2011)]
- R_min fixed at 30 AU  
  > "We maintain $R_{\min}$ fixed at 30 AU (cite: Wyatt2012)." (4 Disc modelling) [from (cite: Wyatt2012)]

### Not stated but needed to reproduce (our reading)

- CLEAN threshold, mask, niter, cell and image size
- Which CASA version for pipeline calibration
- Number of emcee walkers, steps and burn-in
- Subtraction details and fluxes/positions of point sources in uv
- SCUBA2 map pixel rms values and calibrated map
- Collisional model code not released; numerical grid details
- Exact disc scale height prescription sensitivity

## Analysis recipe

1. **Image ALMA continuum and measure sources**: CLEAN with natural weights, primary beam correction; fluxes of star, B1, B2  
  > "using the task CLEAN in CASA 4.4 (cite: McMullin2007) with natural weights and correcting for the primary beam" (3.1 Continuum emission)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit parametric disc to ALMA visibilities + SCUBA2 image**: RADMC-3D images of power-law disc, 5 free parameters, uvsim-style visibilities, SCUBA2 convolved with 13" beam  
  > "In total there are 5 free parameters that we vary to fit the observations." (4 Disc modelling)
   - software: RADMC-3D, emcee, CASA
   - parameter: R_min=30 AU fixed; H=0.1r; grains 1 um-1 cm, q=-3.5; astrosilicate/amorphous carbon/ice 70/15/15%  
  > "with mass fractions of 70%, 15% and 15%, respectively" (4 Disc modelling)
   - assumption: Star Teff 5500 K, R=1.1 Rsun  
  > "effective temperature of 5500 K[^2] (cite: Kurucz1979) and a radius of 1.1 $R_\odot$" (4 Disc modelling)
   - fitting: emcee affine-invariant MCMC, likelihood exp(-chi2/2), uniform priors: Rmax 30-250 AU, alpha -5 to 5, F>0, PA 0-90, i 45-90  
  > "The prior probabilities of the parameters are assumed to be uniform." (4 Disc modelling)
   - validation: ALMA-only fit compared with Herschel orientation; simulated observations of alternative models  
  > "we find that the disc orientation can still be constrained and matches with the previous estimates from Herschel observations" (4 Disc modelling)
3. **CO upper limit**: Integrate channel maps 30-100 AU, ±5.1 km/s; non-LTE mass limit using Matra 2015 tools  
  > "we derive an integrated noise level of 27 mJy km s$^{-1}$" (3.2 CO)
   - assumption: ionization fraction 0.5, C/CO=100  
  > "a carbon ionization fraction of 0.5 and a C/CO abundance of 100" (3.2 CO)
   - fitting: _not stated_
   - validation: _not stated_
4. **Collisional evolution model of mm-grain surface density**: Quasi steady-state size-bin model in annuli 1-300 AU, MMSN primordial, Dmax 1-100 km, fits to 61 Vir  
  > "Our model is composed of a 1 M$_\odot$ star at the center and a debris disc spanning 1 to 300 AU." (5 Steady state collisionally evolved disc model)
   - software: ACE (cited)
   - parameter: e=0.05, I=1.4 deg, basalt Q_D* (Benz & Asphaug)  
  > "to be 0.05 and 1.4$^{\circ}$ ($e/2$), respectively" (5 Steady state collisionally evolved disc model)
   - fitting: power-law fits to numerical results for Sigma_mm and r_c  
  > "The factor 2 and the exponents of $-0.4$, $-0.1$ and $0.6$ are the results from a fit to the numerical simulations." (5 Steady state collisionally evolved disc model)
   - validation: compared with analytic expression and earlier ACE results  
  > "which matches with our more detailed numerical simulation" (5 Steady state collisionally evolved disc model)
5. **Constrain unseen stirring planet**: Mustill & Wyatt 2009 stirring timescale and forced eccentricity, Hill-radius stability, HARPS limits  
  > "using Eq. 6 from (cite: Mustill2009) (valid for planets with eccentricities $\lesssim 0.3$)" (6.2 Stirring by a yet unseen planet)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.4 (imaging); 4.7 (STATWT): imaging and visibility weights  
  > "using the task CLEAN in CASA 4.4" (3.1 Continuum emission)
- **RADMC-3D** : dust temperature and synthetic images  
  > "the dust equilibrium temperature at different radii is computed using RADMC-3D" (4 Disc modelling)
- **emcee** : MCMC sampling  
  > "sampling the parameter space using the python module EMCEE" (4 Disc modelling)
- **Starlink SMURF / ORAC-DR** : SCUBA2 reduction  
  > "Dynamic Iterative Map-Maker within the Starlink SMURF package" (2 SCUBA2 observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disc flux at 0.86 mm | 3.7 | +1.2/-1.1 | mJy | 2 | $F_\mathrm{disc}$ \[mJy\] / $3.7^{+1.2}_{-1.1}$ |
| R_max | 153 | +39/-26 | AU | 2 | $R_{\max}$ \[AU\] /  $153^{+39}_{-26}$ |
| alpha (i restricted 70-80 deg) | 0.1 | +1.1/-0.8 | dimensionless | 2 | finding $\alpha=0.1^{+1.1}_{-0.8}$ |
| Position angle | 59 | 5 | deg | 2 | PA$=59\pm5$ and $i=82\pm4^{\circ}$ |
| Inclination | 82 | 4 | deg | 2 | PA$=59\pm5$ and $i=82\pm4^{\circ}$ |
| Stellar flux at 0.86 mm | 374 | 16 | uJy | 1 | with a total flux of $374\pm16\ \mu$Jy |
| CO gas mass 3-sigma upper limit | 1.4e-6 | not stated | M_earth | 3 | we derive a CO gas mass upper limit of $1.4\times10^{-6}$ M$_\oplus$ |
| Primordial surface density relative to MMSN | 20-100 times lower | not stated | dimensionless | 4 | a best match with a primordial surface density between 20-100 times less dense than the MMSN and a maximum planetesimal size between $5-20$ km |

## Qualitative findings

- No CO detected; no disc emission above 3 sigma in ALMA CLEAN image due to spatial filtering  
  > "Although there is no disc emission above $3\sigma$ in the ALMA CLEAN image" (3.1 Continuum emission)

## Claim tuples

- H: Is the planetesimal disc broad rather than narrow rings? | E: Joint ALMA+SCUBA2 model fit and simulated observations | R: Rmax~150 AU, alpha=0.1 | F: Planetesimal disc is broad, 30 to >=150 AU | **supported**
- H: Does mm-grain surface density mirror total solids? | E: Numerical collisional model | R: Sigma_mm flatter than Sigma beyond r_c | F: Sigma_mm need not trace total surface density | **supported**
- H: What planet could stir the disc? | E: Stirring timescale and stability constraints | R: M>10 Mearth, a=10-20 AU for e<0.1 | F: Massive planet between 10-20 AU, or lower mass with e>>0.1 | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Scattered disc with r^-3.5 profile rejected as inconsistent with flat observed profile  
  > "we can discard a scattered disc that has an initial characteristic surface density proportional to $r^{-3.5}$" (4 Disc modelling)
- How they decided it was enough: _not stated_
- Limitation (authors): Disc only marginally detected (2.2 sigma) in ALMA alone; flux loss from missing short baselines  
  > "The lower ALMA disc flux could be produced by spatial filtering in the ALMA data due to a lack of short baselines" (3.1 Continuum emission)
- Caveat (inferred, ours): Disc constraints rely heavily on SCUBA2 and prior Herschel orientation
- Caveat (inferred, ours): Table alpha (1.2) differs from quoted alpha (0.1) due to restricted inclination prior
- Caveat (inferred, ours): Collisional model assumptions (pre-stirred, fixed Dmax) are simplified

## Reproducibility

- Data public (paper): Project 2013.1.00359.S cited in acknowledgements  
  > "ADS/JAO.ALMA#2013.1.00359.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Collisional model code
- Missing: SCUBA2 reduced map
- Missing: emcee settings and uvsim tool
- Data volume (inferred): ~10-30 GB raw
- Score (inferred): 5/5, ALMA data public and model clearly described, but key imaging/MCMC settings and SCUBA2 data and codes missing.
- Rediscovery candidate: no, Requires SCUBA2 data and custom modelling tools not provided; main result is a marginal detection.

## Links

- Method: (cite: Wyatt2011) (collisional model method)
- Method: (cite: Matra2015) (non-LTE CO mass tools)
- Companion: (cite: Wyatt2012) (Herschel study of 61 Vir)
- Related: SONS survey

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
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
  "facts": 75,
  "stated": 44,
  "rate": 0.587
 },
 "evidence_ok": true
}
```
