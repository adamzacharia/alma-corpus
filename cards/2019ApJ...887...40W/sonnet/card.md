# Resolving the Interstellar Medium in the Nuclear Region of Two z = 5.78 Quasar Host Galaxies with ALMA

`2019ApJ...887...40W` | The Astrophysical Journal 2019 | first author: Wang, Ran | arXiv: 1904.07749 | DOI: 10.3847/1538-4357/ab4d4b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: How are [CII] and dust emission distributed and how does the gas move on kpc scales in two z=5.78 quasar hosts, and what do they imply for [CII]-FIR deficit and host dynamical mass?  
  > "The ALMA observations at 0.2$''$ resolution map the dust and gas on kpc scales." (abstract)
- Target **SDSS J0129-0035**: coordinates [CII] centre 01h29m58.513s -00d35'39.83'' (J2000)  
  > "We adopt the [C II] redshift of $\rm z_{[CII]}=5.7787$ as the zero velocity (cite: wang13)." (3 Results); z/distance z_[CII]=5.7787  
  > "We adopt the [C II] redshift of $\rm z_{[CII]}=5.7787$ as the zero velocity (cite: wang13)." (3 Results); distance from Wang et al. 2013 [CII] redshift  
  > "We adopt the [C II] redshift of $\rm z_{[CII]}=5.7787$ as the zero velocity (cite: wang13)." (3 Results)
- Target **SDSS J1044-0125**: coordinates [CII] centre 10h44m33.042s -01d25'02.08'' (J2000)  
  > "we adopt the [C II] redshift of $\rm z_{[CII]}=5.7847$ from the single Gaussian fitting as the zero velocity" (3 Results); z/distance z_[CII]=5.7847  
  > "we adopt the [C II] redshift of $\rm z_{[CII]}=5.7847$ from the single Gaussian fitting as the zero velocity" (3 Results); distance from single-Gaussian [CII] fit (Wang et al. 2013)  
  > "we adopt the [C II] redshift of $\rm z_{[CII]}=5.7847$ from the single Gaussian fitting as the zero velocity" (3 Results)

## Data provenance

- ALMA projects: 2012.1.00240.S, 2011.0.00206.S
- bands: Band 7  
  > "using the Band 7 receiver on ALMA in Cycle 1" (2 Observations)
- frequencies and spectral setup: four 1.785 GHz spectral windows, one on [CII], three continuum; 15.625 MHz channels (~17 km/s)  
  > "We tuned the four 1.785 GHz spectral windows with one window centered on the redshifted [CII] line frequencies of the two targets and the other three windows observing the continuum." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C34-6, 32 12-m antennas  
  > "in the C34-6 configuration with 32 12-m diameter antennas and a maximum baseline of 1.6 km" (2 Observations)
- baselines: maximum 1.6 km  
  > "a maximum baseline of 1.6 km" (2 Observations)
- angular resolution: ~0.2'' (1.2 kpc)  
  > "synthesized beam size of $\sim$0.2$''$ using robust weighting, which corresponds to 1.2 kpc at z$\sim$5.8" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: Cube rms 0.20 (J0129) and 0.36 (J1044) mJy/beam per 17 km/s; continuum rms 21 and 40 uJy/beam  
  > "The rms noise of the continuum is 21$\rm \mu Jy\,beam^{-1}$ for SDSS J0129$-$0035, and 40$\rm \mu Jy\,beam^{-1}$ for SDSS J1044$-$0125." (2 Observations)
- time on source: ~80 min (J0129), 75 min (J1044)  
  > "The total on-source time is about 80 min for SDSS J0129-0035 and 75 min for SDSS J1044-0125." (2 Observations)
- observing dates: 2015 July and August  
  > "The data was taken in 2015 July and August" (2 Observations)
- pi or archival as stated: _not stated_
- Line: [CII] 158 um fine structure (not stated)
- Other facility **Gaia**: Optical quasar astrometry  
  > "We checked the coordinates of the optical quasars using the astrometric data from the Gaia mission (cite: lindegren18)." (3 Results)
- External data: ALMA Cycle 0 data, [CII] redshifts, FIR luminosities (T=47 K, beta=1.6), Cycle 0 fluxes  
  > "$\rm L_{FIR}$ is the FIR luminosity derived in (cite: wang13) assuming dust temperature of 47 K and emissivity index of $\rm \beta=1.6$" (4.1) [from (cite: wang13)]
- External data: ULAS J1319+0950 [CII] and continuum data for comparison  
  > "We also include ULAS J1319+0950 in the comparison" (4.1) [from (cite: shao17)]
- External data: Comparison samples (GOALS, SMGs, LBGs, quasars) for [CII]-FIR vs surface brightness  
  > "We collect samples of star forming galaxies and quasars at low and high redshifts that have continuum source size measurements from ALMA" (4.1) [from (cite: diazsantos13; diazsantos17; shangguan19; gullberg18; rybak19)]
- External data: CO(6-5) spectra of J0129 and J1044  
  > "compared to the CO (6-5) line spectrum published in Wang et al. (2011)" (3 Results) [from (cite: wang11)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "The data were calibrated using the pipeline of the Common Astronomy Software Application (CASA) Version 4.3.1." (2 Observations)
- casa version: CASA 4.3.1  
  > "CASA) Version 4.3.1" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres and J1058+015  
  > "the flux scale was calibrated on Ceres and J1058+015 with calibration uncertainties less than 10%" (2 Observations)
- flux scale uncertainty: <10%  
  > "calibration uncertainties less than 10%" (2 Observations)
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA  
  > "The images were cleaned using the CLEAN task in CASA using robust=0.5 for weighting." (2 Observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "robust=0.5 for weighting" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Line-free channels averaged into pseudo-continuum, subtracted in uv-domain  
  > "We averaged, in the visibility domain, the emission in line-free channels to form a 'pseudo' continuum dataset which we then subtracted from the uv-data" (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Cycle 1 combined with Cycle 0 data, weights corrected  
  > "we corrected the weights before combining with the Cycle 1 data" (2 Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 0.20 / 0.36 mJy/beam per 17 km/s channel  
  > "The typical rms noise is 0.20 mJy $\rm beam^{-1}$ per 17 $\rm km\,s^{-1}$ channel for the final image cube of SDSS J0129$-$0035" (2 Observations)

### Inherited from earlier work

- Rotating-disk velocity-field fitting method  
  > "following the method used in (cite: shao17) (see also (cite: jones17))" (4.3) [from (cite: shao17)]
- Cycle 0 weight correction/combination procedure  
  > "we corrected the weights before combining with the Cycle 1 data[^2]" (2 Observations) [from CASA guide DataWeightsAndCombination]
- Redshifts used as zero velocity  
  > "We adopt the [C II] redshift of $\rm z_{[CII]}=5.7787$ as the zero velocity (cite: wang13)." (3 Results) [from (cite: wang13)]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters: cell size, image size, masks, thresholds, iterations, deconvolver
- Line-free channel ranges and channels used for line moment maps
- Moment-map thresholds for J0129 (J1044 uses >4 sigma)
- Weight-correction details and exact Cycle 0 calibration state
- Ring/pixel handling and fitting details for exponential disk surface-brightness model
- ROTCUR ring widths, fixed parameters and initial guesses
- Gaussian fit method for J1044 spectra
- Cycle 0 CASA version used

## Analysis recipe

1. **Image continuum and [CII] cubes**: Combine Cycle 0 and Cycle 1 uv-data, subtract pseudo-continuum, clean with robust=0.5  
  > "We made the continuum image with the data from three line-free spectral windows and made the line image cubes with the continuum-subtracted visibility dataset." (2 Observations)
   - software: CASA
   - parameter: robust=0.5; 17 km/s channels  
  > "robust=0.5 for weighting" (2 Observations)
   - fitting: _not stated_
   - validation: Cycle 0 and Cycle 1 visibility amplitudes consistent at overlapping uv-distance  
  > "We checked the amplitudes of visibility data from the two observations at overlapping uv-distance" (2 Observations)
2. **Measure fluxes and sizes**: Integrate within 2 sigma contour; elliptical Gaussian fits in image and uv planes  
  > "We performed elliptical Gaussian fitting to measure the sizes of the [CII] and continuum emission in both the image plane and the uv plane, using *imfit* and *uvmodelfit* tasks in CASA" (3 Results)
   - software: CASA imfit, CASA uvmodelfit
   - parameter: uv bins 50 klambda (J0129), 75 klambda (J1044)  
  > "radially averaged with a bin size of 50 k$\lambda$ for SDSS J0129-0035 and 75 k$\lambda$ for SDSS J1044-0125" (3 Results)
   - fitting: Elliptical Gaussian  
  > "We performed elliptical Gaussian fitting to measure the sizes of the \[C II\] and continuum emission in both the image plane and the uv plane" (Results)
   - validation: Image-plane and uv-plane sizes consistent; compared with Cycle 0  
  > "consistent with that from the uv-models within the fitting uncertainties" (3 Results)
3. **Radial [CII] and FIR surface brightness profiles**: Scale continuum map by L_FIR/S_con; mean in 0.1'' rings; fit beam-convolved exponential disk (n=1)  
  > "We model the surface brightness with an exponential disk in the 2-dimensional image plane with a Sérsic index of n=1." (4.1)
   - parameter: rings at 0 to 0.6'' with width 0.1''  
  > "rings at central radii of 0$''$, 0.1$''$, 0.2$''$, 0.3$''$, 0.4$''$, 0.5$''$, 0.6$''$ and a ring width of 0.1$''$" (4.1)
   - assumption: T_dust=47 K, beta=1.6; FIR 42.5-122.5 um; H0=71, Om=0.27, OL=0.73  
  > "assuming dust temperature of 47 K and emissivity index of $\rm \beta=1.6$ (cite: beelen06)" (4.1)
   - fitting: Fit ring means of convolved model to data  
  > "We then convolve the model with the synthesized beam, calculate the mean surface brightnesses of the model in each ring described above, and fit these mean values to the data." (4.1 Surface brightnesses and ratios of the resolved [C II] and dust emission)
   - validation: _not stated_
4. **Fit disk rotation to J0129 velocity map and derive dynamical mass**: ROTCUR circular rotating disk fit within 0.35''; M_dyn from V_c at 1.8 kpc  
  > "We use the ROTCUR task in the Groningen Image Processing System (GIPSY3; (cite: vanderhulst92)) to fit the observed velocity field." (4.3)
   - software: GIPSY ROTCUR
   - parameter: Disk centre fixed at [CII] Gaussian peak; V_sys=0; radius 0.35''  
  > "We then use the data within a radius of 0.35$''$ to determine $\rm \phi$ and *incl*." (4.3)
   - assumption: Simple circular rotating disk  
  > "We here model the gas velocity map of SDSS J0129-0035 with a simple circular rotating gas disk" (4.3 Constraints on the host galaxy dynamics of SDSS J0129-0035)
   - fitting: ROTCUR least squares; errors are fitting errors  
  > "where the error bars denote the fitting errors" (4.3)
   - validation: M_dyn treated as lower limit given uncertainties  
  > "the $\rm M_{dyn}$ value derived above should be considered as a lower limit of the host galaxy dynamical mass for SDSS J0129-0035." (4.3 Constraints on the host galaxy dynamics of SDSS J0129-0035)

## Software

- **CASA** 4.3.1: Calibration, CLEAN imaging, imfit, uvmodelfit  
  > "The data were calibrated using the pipeline of the Common Astronomy Software Application (CASA) Version 4.3.1." (2 Observations)
- **GIPSY (ROTCUR)** GIPSY3: Velocity-field disk fitting  
  > "We use the ROTCUR task in the Groningen Image Processing System (GIPSY3; (cite: vanderhulst92))" (4.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [CII] line flux, J0129-0035 | 2.11 | 0.09 | Jy km/s | 2 | / \[C II\] line flux ($\rm Jy\,km\,s^{-1}$) / 2.11$\pm$0.09 / 1.52$\pm$0.15 / |
| [CII] line flux, J1044-0125 | 1.52 | 0.15 | Jy km/s | 2 | / \[C II\] line flux ($\rm Jy\,km\,s^{-1}$) / 2.11$\pm$0.09 / 1.52$\pm$0.15 / |
| Continuum flux, J0129 / J1044 | 2.82 / 3.02 | 0.04 / 0.11 | mJy | 2 | / Continuum (mJy) / 2.82$\pm$0.04 / 3.02$\pm$0.11 / |
| Inclination of J0129 disk | 16 | 20 | deg | 4 | $\rm \phi=56\pm1^{\circ}$ and $\rm incl=16\pm20^{\circ}$ |
| Dynamical mass within 1.8 kpc, J0129 | 2.6e10 | lower limit | Msun | 4 | we derive the dynamical mass within a radius of 1.8 kpc to be $\rm M_{dyn}=2.6\times10^{10}\,M_{\odot}$ |
| Circular velocity at 1.8 kpc (incl=16 deg) | 250 | not stated | km/s | 4 | the circular velocity at the largest radius (i.e., 1.8 kpc) is $\rm V_c$=250 $\rm km\,s^{-1}$ |
| SMBH mass of J0129 (Eddington assumed) | 1.7e8 | +1.7/-0.9e8 | Msun | 4 | $\rm M_{BH}=1.7^{+1.7}_{-0.9}\times10^{8}\,M_{\odot}$ |
| M_BH/M_dyn for J0129 (Vc=250) | 0.007 | not stated | dimensionless | 4 | $\rm M_{BH}/M_{dyn}=0.007$ with $\rm V_c=250\, km\,s^{-1}$ |
| [CII]/continuum size ratio, J0129 / J1044 | 1.8 / 2.6 | 0.2 / 0.5 | dimensionless | 2 | 1.8$\pm$0.2 and 2.6$\pm$0.5 times larger than that of the continuum |
| Offset [CII] peak FWHM, J1044 | 750 | 190 | km/s | 2 | yields a FWHM line width of $\rm 750\pm190\,km\,s^{-1}$ |

## Qualitative findings

- J0129 shows velocity gradient with turbulent clumps; J1044 shows no clear rotation and a multi-peaked [CII] spectrum offset from CO(6-5)  
  > "The [C II]-emitting gas in the central region of SDSS J1044-0125 does not show a clear sign of rotation." (Summary)

## Claim tuples

- H: Do resolved [CII]/FIR ratios in quasar hosts follow the [CII]-FIR deficit trend? | E: Ring-averaged [CII] and FIR surface brightnesses compared with other samples | R: Ratios 0.0001-0.001, decreasing with increasing Sigma_FIR up to ~2e12 Lsun/kpc2 | F: Similar to compact starbursts; local conditions drive the deficit | **supported**
- H: Is J0129's host dynamical mass consistent with local M_BH-M_host relation? | E: ROTCUR disk fit, M_dyn and Eddington BH mass | R: M_dyn >= 2.6e10 Msun, M_BH/M_dyn <= 0.007 vs local 0.0043 | F: Ratio not significantly above local relation | **partially**
- H: Is there an offset [CII] companion near J1044? | E: Integrated map over -740 to 400 km/s | R: ~5 sigma peak 4.9 kpc east, 0.52 Jy km/s, no continuum | F: Tentative infalling companion or outflow node | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Face-on geometry makes inclination and Vc poorly constrained; M_dyn is a lower limit  
  > "the model has large uncertainties for face-on system and cannot accurately determine the inclination angle and circular velocity" (4.3)
- Caveat (inferred, ours): Eddington-accretion assumed for BH mass of J0129
- Caveat (inferred, ours): Tentative features at 3-5 sigma
- Caveat (inferred, ours): Single dust temperature used for FIR conversion

## Reproducibility

- Data public (paper): ALMA data acknowledged with project IDs  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00206.S and #2012.1.00240.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: CLEAN parameters and masks
- Missing: ROTCUR setup details
- Missing: Cycle 0 reduction details
- Data volume (inferred): ~20-50 GB raw
- Score (inferred): 3/5, Public data and clear outline, but imaging and fitting parameters are incomplete.
- Rediscovery candidate: yes, Public data, numeric results (fluxes, sizes, inclination, M_dyn) can be redone.

## Links

- Method: (cite: shao17) (Disk modelling method)
- Companion: (cite: wang13) (Cycle 0 observations)
- Companion: (cite: shao17) (Third quasar of Cycle 1 program)
- Related: GOALS

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
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
  "facts": 76,
  "stated": 53,
  "rate": 0.697
 },
 "evidence_ok": true
}
```
