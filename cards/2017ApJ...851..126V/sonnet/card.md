# Galactic-scale Feedback Observed in the 3C 298 Quasar Host Galaxy

`2017ApJ...851..126V` | The Astrophysical Journal 2017 | first author: Vayner, Andrey | arXiv: 1709.03510 | DOI: 10.3847/1538-4357/aa9c42

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: How do quasar and jet-driven outflows in the 3C 298 host galaxy affect its ionized and molecular gas, star formation and bulge/black-hole mass relation?  
  > "A key missing result is one that connects quasar and jet driven outflows with the observed galactic scale winds, star formation activity, and molecular gas properties." (Introduction)
- Target **3C 298**: coordinates RA 14:19:08.181, Dec +06:28:34.79  
  > "14:19:08.181" (Table 3); "individual z=1.439 (look-back time 9.3 Gyr) radio loud quasar 3C 298" (Introduction); z/distance z=1.439  
  > "14:19:08.181" (Table 3); "individual z=1.439 (look-back time 9.3 Gyr) radio loud quasar 3C 298" (Introduction); distance from broad-line region redshift from H$\beta$  
  > "14:19:08.181" (Table 3); "individual z=1.439 (look-back time 9.3 Gyr) radio loud quasar 3C 298" (Introduction)

## Data provenance

- ALMA projects: 2013.1.01359.S, 2015.1.01090.S
- bands: Band 4 and Band 6  
  > "Early ALMA science (cycle 2, 3) band 4 and 6 observations" (2.2 ALMA: Band 4 and 6)
- frequencies and spectral setup: One 1.8745 GHz spw on CO(3-2) (141.87 GHz) and CO(5-4) (236.43 GHz), three additional continuum spws per band  
  > "One 1.8745 GHz spectral window was centered on CO (J=3-2) (141.87 GHz) and CO (J=5-4) (236.43 GHz) while three additional spectral windows set up to map the continuum in each band." (2.2 ALMA: Band 4 and 6)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.4'' (band 4), ~0.3'' (band 6)  
  > "approximate angular resolution of $\sim$0.4$''$ and $\sim0.3$$''$ for band 4 and 6, respectively" (2.2 ALMA: Band 4 and 6)
- max recoverable scale: _not stated_
- sensitivity: Line rms 0.5, 0.22, 0.37 mJy/beam per 34 km/s channel; continuum rms 48, 46, 44 uJy/beam  
  > "| 2016 Sep 9 | 4 | 141.85, 140.00, 129.97, 128.01 | 24.19 | 2.5 | 37 | 0.39$''$$\times$0.30$''$ | 0.22 | 46 |" (Table 1)
- time on source: 27.84, 24.19, 19.65 min  
  > "| 2015 Aug 6 | 4 | 141.86 | 27.84 | 4.5 | 39 | 0.44$''$$\times$0.41$''$ | 0.5 | 48 |" (Table 1)
- observing dates: 2015 Aug 6, 2016 Sep 9, 2016 Sep 17  
  > "| 2016 Sep 17 | 6 | 236.42, 234.5, 220.99, 219.11 | 19.65 | 0.7 | 38 | 0.28$''$$\times$0.18$''$ | 0.37 | 44 |" (Table 1)
- pi or archival as stated: PI: Vayner (own program)  
  > "(2013.1.01359.S, 2015.1.01090.S, PI: Vayner)" (2.2 ALMA: Band 4 and 6)
- Line: CO J=3-2 (141.87 GHz (observed))
- Line: CO J=5-4 (236.43 GHz (observed))
- Other facility **Keck OSIRIS LGS-AO**: Rest-frame optical nebular line IFS (Hb, [OIII], Ha, [NII], [SII])  
  > "We used the Hn3 (May 19) and Jn1 (May 20) filters with a plate scale of 100 milli-arcseconds (mas) per lenslet" (2.1 Keck: OSIRIS)
- Other facility **HST WFC3**: Archival F606W and F140W imaging for stellar populations  
  > "observations were taken in the F606W ($\lambda_{p}$=588.7 nm, width = 218.2 nm) and F140W" (3.8 HST WFC3: PSF Subtraction)
- Other facility **VLA**: Archival 8485.1 MHz radio map of jets/lobes  
  > "We downloaded fully reduced clean map of 3C 298 at 8485.100 MHz" (3.3 OSIRIS: Kinematics)
- External data: VLA 8.485 GHz reduced map of 3C 298  
  > "The radio VLA observations are taken from (cite: mantovani13) (Project code: AJ206)." (3.3 OSIRIS: Kinematics) [from (cite: mantovani13)]
- External data: Single-epoch black hole masses for 3C 298  
  > "(cite: Shen11) determined a single epoch black hole mass for 3C 298 using three calibration methods" (3.7 ALMA: Analysis) [from (cite: Shen11)]
- External data: IR SFR and dust mass  
  > "Value from (cite: Podigachoski15)" (Table 3) [from (cite: Podigachoski15)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.4 and 4.7  
  > "version 4.4 and 4.7" (3.6 ALMA: Data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Phase-only self-cal on synchrotron continuum with gaincal, iterated; rms improved 6-8x  
  > "The final root mean square (rms) improved by a factor of 6-8 in the continuum images." (3.6 ALMA: Data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Continuum: Briggs robust 0.5; line cubes: natural  
  > "Cleaning is performed with Briggs weighting using a robust value of 0.5 with a pixel scale of 0.05$''$." (3.6 ALMA: Data reduction); "natural weighting to improve SNR in diffuse structure" (3.6 ALMA: Data reduction)
- uv taper: Cycle 2 band 4: taper to 0.98''x0.8'' (robust 0.5)  
  > "Applying UV tapering to a resolution of 0.98$''$$\times$0.8$''$ with Briggs weighting (robust = 0.5) improves the SNR to 5" (3.6 ALMA: Data reduction)
- cell size: 0.05''  
  > "plate scale of 0.05$''$ per pixel, spectral channel size of 34 km s$^{-1}$" (3.6 ALMA: Data reduction)
- image size: _not stated_
- masking: Cycle 3 cubes: masks on CO with SNR>5, same mask all channels  
  > "clean masks were placed on CO emission with SNR$>$5 with the same mask applied to all channels" (3.6 ALMA: Data reduction)
- multiscale scales: _not stated_
- continuum subtraction: uv-plane first-order polynomial fit to line-free channels  
  > "We perform continuum subtraction in UV-space by fitting a first order polynomial to channels free of line emission" (3.6 ALMA: Data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- PSF subtraction routine for OSIRIS  
  > "In (cite: Vayner16) we discuss in greater detail our PSF subtraction routine" (3.2 OSIRIS: PSF construction) [from (cite: Vayner16)]
- HST observation details  
  > "Detailed description of the observations are available in (cite: Hilbert16)." (3.8 HST WFC3) [from (cite: Hilbert16)]
- Ionized gas mass from [OIII] following method  
  > "We calculate the ionized gas mass from the [OIII] line using methodology presented in (cite: Cano-Diaz12)." (4.1 Outflow rates) [from (cite: Cano-Diaz12)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum subtraction
- Clean thresholds, niter and mask details for the cycle 2 data
- Self-cal solution intervals
- Flux/phase/bandpass calibrators and flux scale uncertainty
- Whether archive pipeline products were used
- Channel ranges integrated for CO fluxes and the outflow V10 procedure
- Spectral line fit priors
- Extents of spatial regions for integrated spectra

## Analysis recipe

1. **Self-calibrate and image ALMA continuum and cubes**: Phase self-cal on quasar synchrotron, uv continuum subtraction, natural-weighted clean cubes at 34 km/s  
  > "has sufficient SNR to perform self calibrations directly on the science source" (3.6 ALMA: Data reduction)
   - software: CASA
   - parameter: robust 0.5, 0.05'' pixel  
  > "Cleaning is performed with Briggs weighting using a robust value of 0.5 with a pixel scale of 0.05$''$." (3.6 ALMA: Data reduction)
   - fitting: _not stated_
   - validation: Stopped self-cal when no significant SNR improvement  
  > "until we did not see a significant improvement in the SNR on the continuum" (3.6 ALMA: Data reduction)
2. **Map CO flux, velocity and dispersion**: Gaussian fit to spaxels with SNR>=3; flux integrated over +-3 sigma  
  > "Spaxels that showed an emission line with a SNR $\geq$ 3 are fit with a Gaussian profile." (3.7 ALMA: Analysis)
   - fitting: _not stated_
   - validation: _not stated_
3. **Model CO(3-2) velocity field for dynamical mass**: Two-dimensional arctangent disc model fit; alternative inclination from axial ratio (Holmberg)  
  > "we model the molecular disc with a hyperbolic arctangent function" (3.7.1 Molecular gas velocity field modeling)
   - software: Scipy
   - parameter: q0 = 0.13 for edge-on disc  
  > "$\rm q_{0}$ is the axial ratio for an edge on disc taken to be 0.13" (3.7.1 Molecular gas velocity field modeling)
   - fitting: non-linear least squares  
  > "using a non-linear least squares routine" (3.5 OSIRIS: Velocity field modeling)
   - validation: Two methods agree within errors  
  > "The dynamical masses and disc inclination angles obtained with these two methods agree within the error." (3.7.1 Molecular gas velocity field modeling)
4. **Derive molecular gas mass**: L'CO(3-2) converted to CO(1-0) and M_H2  
  > "We convert to CO (1-0) luminosity (L$^{'}_{CO(1-0)}$) using a ratio $L^{'}_{\rm CO(3-2)}/L^{'}_{\rm CO(1-0)}$ of 0.97" (3.7.2 Molecular gas mass)
   - assumption: alpha_CO = 0.8; r32/r10 ratio 0.97  
  > "Using the typical $\alpha_{\rm CO}$ value from nuclear star bursts and quasars (0.8 K km s$^{-1}$ $\rm pc^{2}$)$^{-1}$)" (3.7.2 Molecular gas mass)
   - fitting: _not stated_
   - validation: _not stated_
5. **Molecular outflow rate**: Broad component of double Gaussian fit; Mdot = 3Mv/R for conical outflow  
  > "$$\dot{M}=3\frac{Mv}{R}.$$" (4.1 Outflow rates)
   - parameter: v = 400 km/s (V10), R = 1.6 kpc, M = 3.3e9 Msun  
  > "the total molecular gas mass in the outflow region is 3.3$\times10^{9}$M$_{\odot}$ with an outflow velocity of 400km s$^{-1}$as measured by $V_{10}$ parameter" (4.1 Outflow rates)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.4 and 4.7: ALMA reduction, self-calibration, imaging  
  > "Data reduction was performed using CASA" (3.6 ALMA: Data reduction)
- **PyNeb** : Electron density from [SII] ratio (getTempDen)  
  > "using the *getTempDen* code part of *PyNeb*" (4.1 Outflow rates)
- **FSPS** : Stellar population modelling of HST colours  
  > "flexible stellar population synthesis (FSPS) code" (3.9 HST WFC3: Stellar population)
- **OSIRIS Data Reduction Pipeline** 3.2: OSIRIS reduction  
  > "OSIRIS data reduction pipeline version 3.2" (3.1 OSIRIS: Data reduction)
- **Scipy** : Listed software  
  > "Scipy: (cite: scipy)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Molecular disc gas mass | 6.6 | 0.36 | 1e9 Msun | 4 | The molecular gas disc contains 6.6$\pm0.36\times10^{9}$M$_{\odot}$ |
| Total molecular gas mass | 8.75 | 0.4 | 1e9 Msun | 4 | we derive a total molecular gas mass equal to $8.75\pm0.4\times10^{9}$M$_{\odot}$ |
| Molecular outflow rate | 2300 | not stated | Msun/yr | 5 | This yields a total molecular outflow rate of 2300M$_\odot$ yr$^{-1}$. |
| CO disc dynamical mass (velocity model) | 1.7 | 0.9 | 1e10 Msun | 3 | We derive a dynamical mass 1.7$\pm0.9\times10^{10}$M$_{\odot}$within $r_{dyn}=$2.1 kpc |
| CO disc dynamical mass (axial ratio) | 1.0 | 0.5 | 1e10 Msun | 3 | We derive a dynamical mass of $1.0\pm0.5\times10^{10}$ M$_{\odot}$ |
| Broad CO(3-2) FWHM | 624 | 49 | km/s | 5 | We measure FWHM of 624$\pm$49 km s$^{-1}$ for the broad line emission in CO (3-2) |

## Qualitative findings

- Molecular outflow emanates from the blueshifted side of the molecular disc, on the same side as the ionized outflow.  
  > "Unlike the ionized outflow the molecular outflow emanates in a single direction from the blueshifted side of the molecular disc." (5 Discussion)

## Claim tuples

- H: Is quasar-driven feedback evacuating molecular gas in 3C 298? | E: CO(3-2)/(5-4) ALMA cubes with double-Gaussian fits to the broad component | R: Molecular outflow of 2300 Msun/yr from 3.3e9 Msun gas; depletion time 3 Myr | F: Winds evacuate the molecular reservoir | **supported**
- H: Does 3C 298 lie on the local bulge-BH mass relation? | E: Compared CO dynamical bulge mass with Shen11 BH masses | R: Bulge mass 2-2.5 dex below the relation | F: BH grew before bulge assembly | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Cycle 2 band 4 CO(3-2) data too noisy and unresolved, so cycle 3 data used  
  > "Therefore for the analysis of CO (J=3-2) we defer to cycle 3 data taken under superior weather conditions." (3.6 ALMA: Data reduction)
- Caveat (inferred, ours): alpha_CO=0.8 and r31 assumed; molecular masses uncertain by large factors
- Caveat (inferred, ours): Outflow rate assumes simple conical geometry and V10
- Caveat (inferred, ours): Single-epoch BH masses have systematic spread
- Caveat (inferred, ours): Rotation and outflow separation in CO may be ambiguous

## Reproducibility

- Data public (paper): ALMA data acknowledged via ADS/JAO.ALMA code; HST and VLA archival  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA[2013.1.01359.S]." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Calibrator details
- Missing: Line-free channels
- Missing: CO fit regions and integration limits
- Missing: Self-cal solints
- Data volume (inferred): ~50-100 GB raw for three ALMA execution blocks
- Score (inferred): 3/5, ALMA data is identified and imaging parameters are mostly given, but many calibration, masking and region details are missing.
- Rediscovery candidate: no, Key results depend on custom region selection and multi-instrument data (OSIRIS, HST) not reproducible from ALMA alone.

## Links

- Method: (cite: Vayner16) (OSIRIS PSF subtraction routine)
- Method: (cite: Cano-Diaz12) (Outflow rate and mass formalism)
- Related: QUART survey

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 47,
  "rate": 0.603
 },
 "evidence_ok": true
}
```
