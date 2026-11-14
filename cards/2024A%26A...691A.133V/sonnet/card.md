# The ALMA-CRISTAL survey: Dust temperature and physical conditions of the interstellar medium in a typical galaxy at z = 5.66

`2024A&A...691A.133V` | Astronomy and Astrophysics 2024 | first author: Villanueva, V. | arXiv: 2407.09681 | DOI: 10.1051/0004-6361/202451490

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, milky_way_ism
- Question: What are the dust temperature and ISM physical conditions (dust SED, [CII]/FIR, IRX-beta_UV) of the main-sequence galaxy HZ10 at z=5.66 on kpc scales, using new ALMA Band 9 data?  
  > "This allows us to obtain $T_{\rm SED}$ measurements for HZ10 at kpc-scales, significantly improving the accuracy from the previous studies (derivations)." (1 Introduction)
- Target **HZ10 (CRISTAL-22)**: coordinates _not stated_; z/distance z = 5.659  
  > "Row (1): Ly$\alpha$ redshift." (Table 1); "Rows (1), (5) and (6) are taken from (cite: Capak2015)." (Table 1); distance from Lyα redshift from Capak et al. 2015  
  > "Row (1): Ly$\alpha$ redshift." (Table 1); "Rows (1), (5) and (6) are taken from (cite: Capak2015)." (Table 1)

## Data provenance

- ALMA projects: 2022.1.00678.S, 2018.1.00348.S, 2019.1.01075.S, 2015.1.00388.S, 2021.1.00280.L
- bands: Band 9 (77 um rest), Band 8 (110 um), Band 7 (158 um + [CII]), Band 6 (198 um)  
  > "Based on new ALMA Band 9+7 data (77 and 158 $\mu$m dust continuum) and earlier ALMA Band 8+6 (110 and 198 $\mu$m dust continuum) observations" (1 Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 9 0.414x0.293"; Band 8 0.663x0.601"; Band 7 0.252x0.212" (cont), 0.264x0.225" ([CII]); Band 6 1.31x1.03"  
  > "a beamsize of $\sim {0}''.414 \times {0}''.293$" (2.2 The HZ10 data)
- max recoverable scale: _not stated_
- sensitivity: Band 9 ~0.24 mJy/beam; Band 8 ~0.07; Band 7 continuum ~1.6e-2, [CII] ~0.14 mJy/beam at 47 MHz; Band 6 ~0.03  
  > "achieving a sensitivity of $\sim 0.24$ mJy beam$^{-1}$ over $\Delta \nu=13$ GHz" (2.2 The HZ10 data)
- time on source: Band 9 ~77 min; Band 8 ~48 min; Band 7 ~93 min; Band 6 ~54 min  
  > "The integration time was $\sim$77 minutes on-source" (2.2 The HZ10 data); "The integration time was $\sim48$ minutes on-source" (2.2 The HZ10 data)
- observing dates: Band 9 2022-08-19; Band 8 2019-01-09; Band 7 2021-03-26 to 30; Band 6 2015-01-05  
  > "Observations of the rest-frame 77 $\mu$m continuum were taken on August 19th, 2022, during Cycle 8" (2.2 The HZ10 data)
- pi or archival as stated: _not stated_
- Line: [CII] 158 um (not stated)
- Other facility **HST WFC3**: F105W, F125W, F160W images for UV luminosity and beta_UV  
  > "we include HST data for HZ10 as part of the project 13641 (P.I.: Peter Capak)" (2.2 The HZ10 data)
- External data: Previous global quantities (z, SFR_UV, M*) of HZ10  
  > "Rows (1), (5) and (6) are taken from (cite: Capak2015)." (Table 1) [from (cite: Capak2015)]
- External data: SFR_IR and prior global SED results (beta_d, T_SED) for comparison  
  > "Row (4) are drawn from (cite: Faisst2020)." (Table 1) [from (cite: Faisst2020)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean with automasking, cleaned down to 1 sigma  
  > "it runs `tclean` with `automasking` multiple times, producing cubes with different weightings and channel widths. In all cases the data are cleaned down to 1$\sigma$." (2.2 The HZ10 data)
- deconvolver: _not stated_
- weighting robust: Briggs robust=0.5  
  > "we use datacubes with 20 km s$^{-1}$ channel width and Briggs (`robust=0.5`) weighting." (2.2 The HZ10 data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in visibility space (Band 7)  
  > "it starts by subtracting the continuum on the visibility space using using the Common Astronomy Software Application" (2.2 The HZ10 data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: all maps convolved to the 198 um continuum beam for global SED  
  > "we convolve all the maps to the coarsest angular resolution among the continuum maps (i.e., 198 $\mu$m dust-continuum beamsize)." (4.2 SED fitting, $T_{\rm SED}$ and $T_{\rm peak}$)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Band 7 data reduction (self-calibrated, combined MS)  
  > "The details of the data reduction of the Band 7 observations are presented in (cite: Solimano2024)" (2.2 The HZ10 data) [from (cite: Solimano2024)]
- CRISTAL reduction pipeline  
  > "processed with CRISTAL’s reduction pipeline as described in Herrera-Camus et al. (in prep.)" (2.2 The HZ10 data) [from Herrera-Camus et al. in prep.]
- Band 8 and Band 6 observations/imaging, robust=0.5  
  > "The ancillary ALMA Band 8 and Band 6 observations are presented in (cite: Faisst2020)" (2.2 The HZ10 data) [from (cite: Faisst2020)]
- lambda_0 = 100 um in SED fits  
  > "We use $\lambda_0 =100$ $\mu$m for the global and resolved HZ10 SED fittings as adopted in (cite: Faisst2020)." (3.1 Basic equations and assumptions) [from (cite: Faisst2020)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/pipeline details
- Self-calibration parameters
- Image size, cell size, masks, line-free channels for Band 9/8/6
- Primary beam correction details
- emcee settings (walkers, steps, priors on T, beta, N_bb)
- Aperture flux uncertainty treatment and flux calibration uncertainty
- How HST fluxes at 1877 and 2311 A and L_UV were measured (apertures)
- Final continuum rms and beam of convolved maps

## Analysis recipe

1. **Measure fluxes in apertures**: Integrate maps over circular aperture; global aperture = 198 um beam major axis (~1.2"), resolved aperture = 77 um beam major axis (~0.4")  
  > "$A$ is the area of a circular aperture with a diameter equivalent to the major axis of the 198 $\mu$m continuum beamsize" (3.1 Basic equations and assumptions)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Parametric 2D Sérsic morphology**: Fit single Sérsic profiles to HZ10-C and HZ10-W in 77 um, 158 um and [CII] moment 0 maps; Bridge found in residuals  
  > "We model the HZ10-C and HZ10-W morphologies by fitting a single 2D Sérsic profile" (3.2 Parametric 2D fitting)
   - software: PyAutoGalaxy, PyAutoFit, ESSENCE, lmfit
   - parameter: n in [0.1,3], I0 in [0,2 Imax]; 77 um best parameters used as priors for other maps  
  > "we constrain the values of $n$ and $I_0$ within the ranges $[0.1,3]$ and $[0,2I_{\rm max}]$, respectively" (3.2 Parametric 2D fitting)
   - fitting: lmfit minimize: least_squares then emcee; noise map from full covariance matrix  
  > "we adopt the `least_squares` method, followed by the `emcee` method" (3.2 Parametric 2D fitting)
   - validation: Residual maps inspected; Sérsic fit to Bridge residual failed  
  > "we note that the extra component (or the Bridge) cannot be well described by a Sérsic profile" (4.1 The structure of HZ10)
3. **Modified blackbody SED fitting**: Casey (2012) parametrization fit to 77,110,158,198 um fluxes (global) and 77,158 um (components); T_peak from Wien law; CMB correction  
  > "We use the SED parametrization from (cite: Casey2012) to compute the best spectral energy distribution (SED) fitting" (3.1 Basic equations and assumptions)
   - software: lmfit, emcee
   - parameter: alpha=2.0, lambda_0=100 um fixed; beta_d free globally, fixed 2.0 for components  
  > "We finally choose fixed values for $\alpha=2.0$ and $\lambda_{\rm 0}=100$ $\mu$m to perform the fitting" (4.2 SED fitting, $T_{\rm SED}$ and $T_{\rm peak}$)
   - assumption: T_CMB(z=0)=2.73 K, da Cunha 2013 Eq. 12 CMB correction  
  > "Along this paper, we adopt $T^{z=0}_{\rm CMB}=2.73$ K ." (3.1 Basic equations and assumptions)
   - fitting: emcee MCMC via lmfit minimize, maximum likelihood  
  > "We adopt the `emcee` method, which determines for the maximum likelihood of the parameters via a Monte-Carlo Markov Chain." (4.2 SED fitting, $T_{\rm SED}$ and $T_{\rm peak}$)
   - validation: Compared with Faisst et al. 2020 global values  
  > "our estimated global SED dust temperature is statistically identical to the one derived by (cite: Faisst2020)" (4.2 SED fitting, $T_{\rm SED}$ and $T_{\rm peak}$)
4. **Derive luminosities, beta_UV, IRX, molecular index**: L_FIR by integrating SED over 42.5-122.5 um (also stated 125.5), L_IR 8-1000 um, L_[CII] from Solomon & Vanden Bout, beta_UV from HST F125W/F160W, IRX = L_IR/L_UV(1600 A)  
  > "Similarly, we also compute the total IR luminosity ($L_{\rm IR}$) by integrating numerically the best-fitting SED but in the wavelength range between 8 and 1000 $\mu$m." (3.1 Basic equations and assumptions)
   - assumption: LCDM H0=70, OmegaM=0.3, OmegaL=0.7  
  > "we assume a $\Lambda$CDM cosmology, adopting the values $\Omega_{\Lambda}=0.7$, $\Omega_{\rm M}=0.3$ and H$_{\rm o}=70$ km s$^{-1}$ Mpc$^{-1}$" (1 Introduction)
   - fitting: _not stated_
   - validation: Compared with IRX-beta relations and molecular index of Ferrara 2022  
  > "When computing the molecular index for the HZ10 system, we obtain $I_{\rm m} = 1156\pm104$. The latter is consistent with the IRX-$\beta_{\rm UV}$ relation for HZ10 discussed above" (4.4 The IRX-$\beta_{\rm UV}$ relation)

## Software

- **CASA** : uvcontsub, tclean imaging  
  > "it runs `tclean` with `automasking` multiple times" (2.2 The HZ10 data)
- **PyAutoGalaxy** : 2D Sérsic light profile fitting  
  > "we use the 2D light profile modeling code `PYAUTOGALAXY`" (3.2 Parametric 2D fitting)
- **ESSENCE** : noise map with full covariance matrix in likelihood  
  > "we generate the noise-map by feeding the full covariance matrix into the calculation of the likelihood using the code `ESSENCE`" (3.2 Parametric 2D fitting)
- **lmfit** : minimize with least_squares and emcee for morphology and SED fits  
  > "we use the task `minimize` from the `PYTHON` package `lmfit`" (3.2 Parametric 2D fitting)
- **emcee** : MCMC parameter search  
  > "We adopt the `emcee` method" (4.2 SED fitting, $T_{\rm SED}$ and $T_{\rm peak}$)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Global T_SED | 46.7 | ±6.8 | K | 3 | / Global / 3.78$\pm$0.63 / 1.76$\pm$0.51 / 46.7$\pm$6.8 / 35.5$\pm$7.0 / |
| Global beta_d | 2.00 | ±0.14 | dimensionless | 3 | we find a dust emissivity index $\beta_{\rm d}=2.00\pm0.14$ |
| T_SED HZ10-C / HZ10-W / Bridge | 46.4 / 51.2 / 39.2 | ±11.7 / ±13.1 / ±9.8 | K | 3 | / HZ10-W / 1.06$\pm$0.39 / 0.36$\pm$0.13 / 51.2$\pm$13.1 / 37.8$\pm$13.3 / |
| Global log L_FIR | 12.42 | ±0.12 | log Lsun | 4 | 12.42$\pm$0.12 / 12.60$\pm$0.27 |
| Molecular index I_m | 1156 | ±104 | dimensionless | 4 | we obtain $I_{\rm m} = 1156\pm104$ |
| beta_UV HZ10-W | -0.64 | ±0.14 | dimensionless | 4 | -0.64$\pm$0.14 |

## Qualitative findings

- HZ10 consists of two Sérsic components (C and W) plus a dusty Bridge seen in 158 um residuals  
  > "A visual inspection of the residual map of the 158 $\mu$m continuum emission reveals a third component connecting HZ10-C with HZ10-W." (4.1 The structure of HZ10)

## Claim tuples

- H: Band 9 data improve T_dust constraints in HZ10 | E: Global modified blackbody fit with 77,110,158,198 um fluxes | R: T_SED=46.7±6.8 K, beta_d=2.00±0.14 | F: Uncertainty on global T_SED reduced by factor ~2.3 relative to previous work | **supported**
- H: Dust temperature varies among HZ10 components | E: Resolved SED fits with beta_d=2.0 | R: HZ10-W 51.2 K vs 46.4 K (C), 39.2 K (Bridge) | F: Differences are within 1 sigma, not significant | **partially**
- H: HZ10 shows a [CII] deficit | E: [CII]/FIR vs Sigma_FIR | R: Sigma_FIR ~4 times higher than HZ04, similar [CII]/FIR | F: HZ10-W shows signs of a [CII] deficit | **partially**
- H: IRX-beta_UV reveals dust geometry | E: IRX and beta_UV for components | R: HZ10-W and Bridge lie above the Meurer relation | F: Consistent with a dust screen attenuating young stars | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): T_SED and related quantities are sensitive to fixed assumptions and completeness of FIR continuum coverage  
  > "$T_{\rm SED}$ estimations (and related quantities) are very sensitive to the completeness of the integrated FIR continuum fluxes set available to model the dust SED." (5 Summary and conclusions)
- Caveat (inferred, ours): Only two bands for resolved SED with beta fixed, so T is poorly constrained and degenerate
- Caveat (inferred, ours): Differences between components are <1 sigma yet interpreted physically
- Caveat (inferred, ours): Inconsistent FIR integration upper limit (125.5 vs 122.5 um) in text
- Caveat (inferred, ours): Resolved fluxes use 0.4" aperture comparable to beam, with Band 8/6 not resolved

## Reproducibility

- Data public (paper): Archival ALMA projects and HST MAST data used; Band 9 project 2022.1.00678.S listed  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2022.1.00678.S, ADS/JAO.ALMA #2019.1.01075.S, ADS/JAO.ALMA #2018.1.00348.S, ADS/JAO.ALMA #2015.1.00388.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CRISTAL pipeline details (Herrera-Camus et al. in prep.)
- Missing: emcee priors/settings
- Missing: Aperture and HST photometry details
- Data volume (inferred): ~50-150 GB raw for four projects
- Score (inferred): 5/5, Data identified and equations given, but calibration/imaging and fitting priors largely deferred to other papers.
- Rediscovery candidate: no, Key reduction and fitting settings are not given and rely on in-prep papers.

## Links

- Method: (cite: Casey2012) (SED parametrization)
- Method: (cite: Solimano2024) (Band 7 data reduction)
- Method: (cite: daCunha2013) (CMB correction)
- Companion: (cite: Faisst2020) (Previous global SED and Band 8/6 data)
- Companion: (cite: Jones2024) (JWST NIRSpec IFU of HZ10)
- Related: CRISTAL
- Related: ALPINE

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2021.1.00280.L"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2012.1.00523.S",
  "2018.1.01359.S",
  "2018.1.01605.S",
  "2019.1.00226.S"
 ],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 40,
  "rate": 0.548
 },
 "evidence_ok": true
}
```
