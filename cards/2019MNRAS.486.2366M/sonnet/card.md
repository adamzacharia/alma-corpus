# The molecular gas properties in the gravitationally lensed merger HATLAS J142935.3-002836

`2019MNRAS.486.2366M` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Messias, Hugo | arXiv: 1904.00307 | DOI: 10.1093/mnras/stz945

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: What are the molecular gas properties (temperature, density, mass, alpha_CO) of the lensed merger H1429-0028, using new APEX CO(3-2) and CO(6-5) data plus earlier ALMA lines?  
  > "The modelling of the observed spectral line energy distribution of CO J$_{\rm up}$=2 to 6 and \[CI\] $^3P_1-^3P_0$ assumes a large velocity gradient scenario" (abstract)
- Target **HATLAS J142935.3-002836 (H1429-0028)**: coordinates _not stated_; z/distance z_lens=0.218, z_bkg=1.027  
  > "$z_{lens}=0.218$, $z_{bkg}=1.027$" (abstract); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00476.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: APEX SEPIA Band 5: 5.1 h; SHeFI APEX2: 4 h  
  > "The total time on source was 5.1 h." (2.1.1 SEPIA Band 5); "The total time on source was 4 h." (2.1.2 SHeFI APEX2)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 3-2 (not stated)
- Line: CO 6-5 (not stated)
- Other facility **APEX (SEPIA Band 5, SHeFI APEX2, Z-SPEC)**: New CO(3-2) and CO(6-5) spectra; earlier Z-SPEC CO(4-3), (5-4)  
  > "Here, we proceed to describe the more recent SEPIA Band 5 and SHeFI APEX2 observations." (2.1 APEX)
- Other facility **HST/WFC3**: Grism data revisited for the arc-like feature  
  > "we revisited the HST grism data assessing any possible emission from the arc-like feature external to the Einstein-ring" (3.1 Properties of targeted lines)
- External data: ALMA CO(2-1), CO(4-3), [CI] lines and 1.28 mm continuum from M14  
  > "together with the lines reported in M14" (3.2 Spectral Line decomposition) [from messias14]
- External data: Revised lens model and dust magnification (~24)  
  > "which resulted in a revised magnification factor of 24$\pm$1" (3.3 Differential magnification) [from dye18]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: [CI] data re-self-calibrated (phase only) versus M14  
  > "We revisited the data-set to improve the self-calibration step (only in phase)" (Footnote 4)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA data reduction and imaging, and Z-SPEC observations, from M14  
  > "The Z-SPEC observations targeting the CO transitions J=4-3 and 5-4 were already described in detail in M14." (2.1 APEX) [from messias14]
- Lens model from Dye et al.  
  > "using the same lens model from (cite: dye18)" (3.3 Differential magnification) [from dye18]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, imaging and cube parameters (all in M14)
- Absolute flux scale/calibrators for ALMA
- Line-free channels and baseline fitting for APEX spectra
- MCMC walkers/steps for spectral fit and LVG MCMC
- Gaussian priors/bounds for the line fits
- Spatial-decomposition details

## Analysis recipe

1. **Reduce APEX spectra**: Reduction with CLASS; Jy/K conversion factors applied  
  > "The data was reduced with class (a gildas[^2] task)." (2.1.1 SEPIA Band 5)
   - software: CLASS/GILDAS
   - parameter: 38.4 Jy/K (Band 5), 40.8 Jy/K (APEX2)  
  > "The adopted Kelvin to Jansky conversion factor is 38.4 Jy/K" (2.1.1 SEPIA Band 5)
   - fitting: _not stated_
   - validation: _not stated_
2. **Decompose line profiles into three velocity components**: Three-Gaussian MCMC fit to CO(4-3) as training; centroids fixed for other transitions; priors on component fractions vs J  
  > "The training-derived values of the three centroid-velocities were kept fixed while fitting the remainder of the spectrally resolved CO transition spectra." (3.2 Spectral Line decomposition)
   - software: emcee
   - fitting: emcee affine-invariant sampler; monotonic priors on component flux fractions with J  
  > "had to comply with the following priors" (3.2 Spectral Line decomposition)
   - validation: _not stated_
3. **Source reconstruction and magnification of components**: Reconstruct moment-0 maps of each component with the Dye et al. lens model; AutoLens as independent check  
  > "AutoLens (cite: nightingale18) was used as an independent check of the lens parameters." (3.3 Differential magnification)
   - software: AutoLens
   - fitting: _not stated_
   - validation: AutoLens check  
  > "AutoLens (cite: nightingale18) was used as an independent check of the lens parameters." (3.3 Differential magnification)
4. **LVG modelling of CO+[CI] SLED**: myRadex LVG on a grid; chi2 minimum, maximum likelihood, bootstrap (1000 iterations), MCMC  
  > "The best-fit value was obtained by finding the minimum $\chi^2$-value in a grid of line-intensity values" (3.4 Large Velocity Gradient analysis)
   - software: myRadex
   - parameter: 10<T<1000 K, 1e2<n<1e6 cm-3, 1e2<dv<1e6 m/s/pc, 0.1 dex steps  
  > "with $\log$-steps of 0.1 dex" (3.4 Large Velocity Gradient analysis)
   - assumption: x_CO and x_C ~1e-4; MH2 < Mdyn; virial K_vir>=1  
  > "The CO and C abundances relative to H$_2$ (small $x_{\rm CO}$ and $x_{\rm C}$) are both assumed to be $\sim10^{-4}$" (3.4 Large Velocity Gradient analysis)
   - fitting: chi2 grid with flux errors plus 5% (CO 2-1) and 10% (others) calibration error  
  > "a 5 and 10 per cent error in flux added in quadrature to the instrumental error" (3.4 Large Velocity Gradient analysis)
   - validation: Predicted [CI] flux compared with observed  
  > "which comprises the observed value of $0.77\pm0.09$" (3.4 Large Velocity Gradient analysis)

## Software

- **CLASS/GILDAS** : APEX data reduction  
  > "The data was reduced with class (a gildas[^2] task)." (2.1.1 SEPIA Band 5)
- **emcee** : Spectral line decomposition  
  > "emcee (cite: foremanmackey13)" (3.2 Spectral Line decomposition)
- **myRadex** : LVG modelling  
  > "by making use of *myRadex*[^5]" (3.4 Large Velocity Gradient analysis)
- **AutoLens** : Independent lens parameter check  
  > "AutoLens (cite: nightingale18) was used as an independent check of the lens parameters." (3.3 Differential magnification)
- **mbb_emcee** : SED fit to predict 850 um flux  
  > "We also consider the mbb_emcee[^9] SED fit" (4.3.2 Comparison with the L850-L'CO relation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Combined H2 mass (NS) | 4e9 | +3/-2 e9 | Msun | 4 | ${\rm M_{H_2}=4_{-2}^{+3} \times 10^9~M_\odot}$ |
| alpha_CO | 0.4 | +0.3/-0.2 | Msun/(K km/s pc2) | 4 | $\alpha_{\rm CO}=0.4_{-0.2}^{+0.3}~$M$_\odot$/(K km/s pc$^2)$ |
| Magnifications mu I, II, III | 15.1, 15.6, 12 | 0.7, 0.4, 1 | dimensionless | 3 | $\mu^{\sc I}=15.1\pm0.7$, $\mu^{\sc II}=15.6\pm0.4$, and $\mu^{\sc III}=12\pm1$ |
| Dynamical mass NS | 5e10 | +3/-2 e10 | Msun | 3 | M$_{\rm DYN}=5_{-2}^{+3}\times10^{10} \,$M$_\odot$ |
| EW/NS gas fraction upper limit | <9 | +9 | per cent | 0 | the EW gas and dust content is $<9^{+9}$ per cent |

## Qualitative findings

- Line profiles comprise three velocity components; the high-velocity one is less magnified and more compact.  
  > "the fainter high-velocity one is less magnified and more compact" (abstract)

## Claim tuples

- H: What are the NS gas conditions and mass? | E: LVG analysis of CO J=2-6 and [CI] | R: T~70 K, log n~3.7, MH2=4e9 Msun | F: Gas is ~8% of dynamical mass | **supported**
- H: Is alpha_CO Milky-Way-like? | E: Compare SLED-derived alpha_CO with metallicity relations | R: 0.4 vs 4-7 predicted | F: Low alpha_CO; high values would exceed the dynamical mass | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: CS as density tracer gave poor results  
  > "but this retrieved poor results" (3.4 Large Velocity Gradient analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Temperature, velocity gradient and density poorly constrained and correlated  
  > "temperature, velocity gradient, and gas density are poorly constrained and correlated" (4.1 Gas conditions)
- Caveat (inferred, ours): Gas mass scales linearly with the assumed x_C
- Caveat (inferred, ours): No differential magnification between lines is tested beyond CO(4-3) and [CI]
- Caveat (inferred, ours): Few data points for many LVG parameters

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA reduction details in M14
- Missing: Lens model from Dye et al.
- Missing: Priors and sampler settings
- Data volume (inferred): small (ALMA project 2011.0.00476.S cubes plus APEX spectra)
- Score (inferred): 2/5, ALMA part is inherited from M14 and many fit details are missing.
- Rediscovery candidate: no, Recipe depends on earlier papers and APEX data, and key settings are unstated.

## Links

- Method: messias14 (ALMA data, earlier analysis)
- Method: dye18 (Lens model)
- Related: H-ATLAS

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 29,
  "rate": 0.403
 },
 "evidence_ok": true
}
```
