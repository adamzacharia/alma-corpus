# An ALMA+ACA measurement of the shock in the Bullet Cluster

`2019A&A...628A.100D` | Astronomy and Astrophysics 2019 | first author: Di Mascolo, Luca | arXiv: 1907.07680 | DOI: 10.1051/0004-6361/201936184

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: galaxy_clusters_and_sz
- Question: What are the Mach number and electron-ion equilibration behaviour of the western shock in the Bullet Cluster, measured from the thermal SZ pressure jump with ALMA+ACA plus X-ray priors?  
  > "We aim to characterize the shock properties using deep, high-resolution interferometric SZ effect observations in combination with priors from an independent X-ray analysis." (abstract)
- Target **Bullet Cluster (1E0657-56)**: coordinates _not stated_; z/distance z = 0.296  
  > "At the redshift of the Bullet Cluster ($z = 0.296$), $1\ensuremath{''}$ corresponds to a physical scale of $4.41~\mathrm{kpc}$." (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00760.S
- bands: Band 3  
  > "in Band 3 (project code 2013.1.00760.S)" (2.1 ALMA/ACA observations)
- frequencies and spectral setup: 84-100 GHz, four 2 GHz-wide spectral windows centered near 85, 87, 97, 99 GHz  
  > "These wideband observations span the frequency range $84-100~\mathrm{GHz}$ in four $2~\mathrm{GHz}$-wide spectral windows, centered at approximately $85$, $87$, $97$, and $99~\mathrm{GHz}$." (2.1 ALMA/ACA observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m array and ACA 7-m array  
  > "These observations include data from both the 12-meter array (hereafter “ALMA”) and 7-meter Atacama Compact (Morita) Array (ACA)." (Introduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 4.01" x 3.07" FWHM, P.A. 81 deg  
  > "a synthesized beam with a main lobe of $4.01\ensuremath{''}\times3.07\ensuremath{''}$ FWHM (P.A. $81\ensuremath{^\circ}$)" (2.1 ALMA/ACA observations)
- max recoverable scale: ~40" (ALMA), ~55" (ACA)  
  > "the largest recoverable scales are respectively $\sim40\ensuremath{''}$ and $\sim55\ensuremath{''}$" (2.1 ALMA/ACA observations)
- sensitivity: ~5 uJy (ALMA), ~45 uJy (ACA), natural weighting  
  > "obtaining root-mean-square noise levels of approximately $5~\mu\mathrm{Jy}$ and $45~\mu\mathrm{Jy}$ respectively (as measured in naturally-weighted imaging)" (2.1 ALMA/ACA observations)
- time on source: 3.1 h (ALMA), 5.9 h (ACA)  
  > "ALMA and the ACA observed the Bullet Cluster for a total of 3.1 and 5.9 hours integration time respectively" (2.1 ALMA/ACA observations)
- observing dates: 2014; 4 ALMA and 11 ACA executions  
  > "The ALMA and ACA observations were respectively performed in 4 and 11 separate executions spanning 2014" (2.1 ALMA/ACA observations)
- pi or archival as stated: _not stated_
- Other facility **Chandra**: X-ray priors on shock geometry, upstream pressure and temperature; independent Mach number  
  > "we find the best-matching shock geometry by minimizing the variance of the X-ray image within a defined region." (2.2.1 Shock front)
- External data: Upstream electron pressure and temperature from Chandra modelling in a narrow sector at the shock nose  
  > "set the upstream electron pressure $P_{\mathrm{e,us}}$ to the value derived by modelling the *Chandra* data in a narrow sector centered on the shock nose" (2.2.1 Shock front) [from (cite: Markevitch2006)]
- External data: X-ray density jump xn=2.86±0.16 and MX=2.74±0.25 (instantaneous), MX=2.57±0.23 (adiabatic)  
  > "provides an electron density jump $x_{\mathrm{n}}=2.86\pm0.16$" (3.1 Instantaneous equilibration) [from Markevitch (in prep.)]
- External data: gNFW universal pressure profile parameters  
  > "are fixed to the values reported in (cite: Arnaud2010) for the universal pressure profile" (2.2.2 Bulk pressure distribution) [from (cite: Arnaud2010)]
- External data: gNFW centroid at main lensing kappa-map peak  
  > "to the position of main lensing $\kappa$-map peak inferred by (cite: Clowe2006)" (2.2.2 Bulk pressure distribution) [from (cite: Clowe2006)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline re-reduction with manual cross-check of flux and phase calibrators  
  > "we performed a manual cross-check of the values for the designated flux calibrators as well as the phase calibrators, finding they were consistent" (2.1 ALMA/ACA observations)
- casa version: CASA 4.7  
  > "We re-reduced the data using the ALMA pipeline (cite: ALMA2015; ALMA2016) in CASA 4.7 (cite: McMullin2007)" (2.1 ALMA/ACA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: nominal ≤5%; modelled with kappa hyperparameters (normal, sigma=0.05)  
  > "which has nominal uncertainty $\leq 5\%$" (2.1 ALMA/ACA observations)
- self calibration: _not stated_

### Imaging

- task: No CLEAN; visibility-space forward modelling; dirty images only for illustration  
  > "to avoid known deconvolution biases intrinsic to the CLEAN algorithm (cite: Hogbom1974; Thompson2015), we perform our analysis directly in visibility ($uv$) space." (2.1 ALMA/ACA observations)
- deconvolver: _not stated_
- weighting robust: natural weighting (for noise estimate); analysis done in uv space  
  > "(as measured in naturally-weighted imaging)" (2.1 ALMA/ACA observations)
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

- Interferometric SZ forward-modelling technique in uv space  
  > "We extend the interferometric SZ analysis techniques presented in the Appendix of (cite: DiMascolo2019) to allow fitting pressure discontinuities due to shocks." (2.1 ALMA/ACA observations) [from (cite: DiMascolo2019)]
- Optimal visibility binning scheme  
  > "binning the data in each spectral window following the optimal averaging scheme described in (cite: Hobson1995)" (2.1 ALMA/ACA observations) [from (cite: Hobson1995)]
- X-ray-informed SZ analysis  
  > "we therefore employ an X-ray-informed analysis of the ALMA+ACA SZ observations as in Section 3.3 of (cite: Basu2016)" (2.2.1 Shock front) [from (cite: Basu2016)]
- Shock geometry fitting by minimizing X-ray image variance  
  > "Analogous to (cite: Ueda2017), we find the best-matching shock geometry by minimizing the variance of the X-ray image within a defined region." (2.2.1 Shock front) [from (cite: Ueda2017)]
- Relativistic SZ corrections  
  > "relativistic corrections to the SZ spectrum (cite: Itoh2004) are included in our modelling" (2.2.2 Bulk pressure distribution) [from (cite: Itoh2004)]

### Not stated but needed to reproduce (our reading)

- Exact binning parameters for visibilities
- dynesty settings (live points, stopping criterion)
- Likelihood form and noise treatment details
- Hyperbola shock-geometry best-fit values and X-ray image/region selection
- Which ALMA/ACA execution blocks, calibrators and flagging were used
- Gridding pixel scale and galario settings
- Chandra X-ray values for prior derivation (Markevitch in prep. unpublished)

## Analysis recipe

1. **Re-calibrate and bin visibilities**: ALMA pipeline in CASA 4.7, then optimal binning of visibilities per spectral window  
  > "binning the data in each spectral window following the optimal averaging scheme described in (cite: Hobson1995)" (2.1 ALMA/ACA observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Cross-checked against delivered calibration  
  > "producing results consistent with the previous calibration using the script provided on data delivery" (2.1 ALMA/ACA observations)
2. **Determine shock front geometry from Chandra**: Fit hyperbolic step-function model to X-ray image by minimizing variance in angular sectors; MAP model adopted  
  > "The model is assumed to be simply given by a step function in which the discontinuity has a hyperbolic shape." (2.2.1 Shock front)
   - assumption: Axially-symmetric front, merger axis in plane of sky, symmetric curvature in LoS and PoS  
  > "we consider the curvature of the front to be symmetric with respect to the line-of-sight and the plane-of-sky direction." (2.2.1 Shock front)
   - fitting: _not stated_
   - validation: _not stated_
3. **Forward-model SZ signal and fit visibilities**: Integrate 3D pressure model (power-law downstream, gNFW upstream) along LoS, apply SZ spectrum with relativistic correction, FFT and sample at uv points, fit jointly ALMA+ACA  
  > "The SZ model image is then Fourier transformed and sampled to the position of the sparse interferometric data." (2.1 ALMA/ACA observations)
   - software: galario, dynesty
   - parameter: Priors in Table 1: P_e,us and T_e,us split-normal from X-ray; shock nose and angle split-normal; M uniform 1-10; alpha uniform -10 to 0; kappa normal(1,0.05)  
  > "$\mathcal{M}$ | uniform | $\mathrm{min}=1$, $\mathrm{max}=10$" (Table 1)
   - assumption: gamma=5/3; flat LCDM Om=0.30, H0=70; kSZ neglected  
  > "we then decide to not include the kinetic SZ effect in our model" (2.2.2 Bulk pressure distribution)
   - fitting: Dynamic nested sampling with dynesty; posterior medians and 16/84 percentiles  
  > "we improved the posterior sampling algorithm by adopting the dynamic nested sampling by (cite: Higson2017)." (2.3 Implementation details)
   - validation: Prior-only run; robustness tests varying gNFW slopes and centroid; residual dirty images  
  > "We test for biases in the parameter reconstruction arising from our specific choice for the distribution of priors by performing a *prior-only* run" (2.2 Sunyaev-Zeldovich model)
4. **Convert pressure jump to Mach number for two heating scenarios**: Instantaneous: Rankine-Hugoniot relation with gamma=5/3. Collisional: electrons heated adiabatically then equilibrate via Coulomb collisions; xp from density and temperature ratios  
  > "we assume that electrons are first heated adiabatically (cite: Vink2015), so that the electron temperature immediately inside the shock front equals $x_{\mathrm{n}}^{\gamma-1} T_{\mathrm{e,us}}$." (3.2 Collisional equilibration)
   - assumption: Azimuthal decline of Mach number from X-ray density jump  
  > "We further allow for the azimuthal variation of $\mathcal{M}$ along the shock front" (3.1 Instantaneous equilibration)
   - fitting: _not stated_
   - validation: Compared with Chandra MX; Bayesian evidence difference between models  
  > "$\Delta\log{\mathcal{Z}}=1.30\substack{+0.71\\-1.48}$" (3.2 Collisional equilibration)

## Software

- **CASA** 4.7: ALMA pipeline re-reduction  
  > "We re-reduced the data using the ALMA pipeline (cite: ALMA2015; ALMA2016) in CASA 4.7" (2.1 ALMA/ACA observations)
- **dynesty** : Dynamic nested sampling of posterior  
  > "we employ the pure-Python implementation provided by `dynesty` (cite: Speagle2019)." (2.3 Implementation details)
- **galario** : Listed among software used (visibility sampling of model)  
  > "`galario` (cite: Tazzari2018)" (Acknowledgements)
- **AstroPy** : General astronomy Python package  
  > "`AstroPy`, a community-developed core Python package for Astronomy (cite: Astropy2018)" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mach number, instantaneous equilibration | 2.08 | +0.12/-0.12 | dimensionless | 4 | We obtain $\mathcal{M}=2.08\substack{{+0.12}\\{-0.12}}$ |
| Mach number, collisional equilibration | 2.53 | +0.33/-0.25 | dimensionless | 4 | we find $\mathcal{M}=2.53\substack{+0.33\\-0.25}$ |
| Delta log evidence (instantaneous vs adiabatic) | 1.30 | +0.71/-1.48 | dimensionless | 3 | $\Delta\log{\mathcal{Z}}=1.30\substack{+0.71\\-1.48}$ |
| X-ray Mach number (instantaneous) | 2.74 | 0.25 | dimensionless | 0 | This corresponds to $\mathcal{M}_{\mathrm{X}}=2.74\pm0.25$. |

## Qualitative findings

- ALMA+ACA data are sensitive mainly to the pressure difference across the shock; large-scale gNFW profile is filtered out  
  > "This confirms that the ALMA+ACA data are only sensitive to the properties of the pressure distributions near the shock edge" (3.2 Collisional equilibration)
- No significant residuals after model subtraction  
  > "it is not possible to identify residuals that differ at a significant level from noise-like features." (3.2 Collisional equilibration)

## Claim tuples

- H: Does the SZ-derived Mach number agree with X-ray under instantaneous electron-ion equilibration? | E: Joint uv-space ALMA+ACA fit with X-ray priors, Rankine-Hugoniot conversion | R: M=2.08±0.12 vs MX=2.74±0.25 | F: ~2.4 sigma tension | **supported**
- H: Can adiabatic electron heating with collisional equilibration reconcile SZ and X-ray? | E: Collisional model of electron temperature | R: M=2.53 (+0.33/-0.25) vs MX=2.57±0.23 | F: Consistent, but neither model unambiguously preferred | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Fit in uv space to avoid CLEAN deconvolution biases and missing flux issues  
  > "to avoid known deconvolution biases intrinsic to the CLEAN algorithm (cite: Hogbom1974; Thompson2015), we perform our analysis directly in visibility ($uv$) space." (2.1 ALMA/ACA observations)
- Alternative: SZ-only shock geometry and Mach number were unconstrained, so X-ray priors were adopted  
  > "the parameters defining its geometry are heavily degenerate, and the small extent of the ALMA+ACA field of view does not allow for meaningful constraints." (2.2.1 Shock front)
- How they decided it was enough: _not stated_
- Limitation (authors): Systematics from cluster geometry and complex post-shock gas distribution; model does not capture X-ray morphology  
  > "Our analysis is however limited by systematics related to the overall cluster geometry and the complexity of the post-shock gas distribution." (abstract)
- Caveat (inferred, ours): Mach number depends on unpublished X-ray priors (Markevitch in prep.)
- Caveat (inferred, ours): Cylindrical symmetry assumption may bias the pressure jump
- Caveat (inferred, ours): Single power-law downstream profile ignores the cold front
- Caveat (inferred, ours): Only ~2 sigma discrimination between heating models

## Reproducibility

- Data public (paper): Data cited by project code 2013.1.00760.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00760.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Chandra-derived priors partly from unpublished work
- Missing: Binning and sampler configuration
- Missing: Hyperbolic geometry best-fit values
- Data volume (inferred): ~50-100 GB raw ALMA+ACA Band 3 data
- Score (inferred): 4/5, Data public and method described, but key X-ray priors are in prep. and numerical settings are missing.
- Rediscovery candidate: no, Requires custom uv-space modelling and unpublished Chandra priors.

## Links

- Method: (cite: DiMascolo2019) (Interferometric SZ modelling algorithm)
- Method: (cite: Basu2016) (X-ray-informed ALMA+ACA shock analysis)

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 47,
  "rate": 0.61
 },
 "evidence_ok": true
}
```
