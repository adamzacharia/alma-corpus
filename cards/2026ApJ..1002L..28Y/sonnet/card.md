# A Close Quasar Pair in a Massive Galaxy Merger at z = 5.7

`2026ApJ..1002L..28Y` | The Astrophysical Journal Letters 2026 | first author: Yue, Minghao | arXiv: 2604.06504 | DOI: 10.3847/2041-8213/ae5e5b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: Is J2037–4537 a physical close quasar pair in a galaxy merger at z=5.7 rather than a doubly-imaged lensed quasar, and what are the host galaxy properties and implied pair fraction?  
  > "The ALMA observation reveals the quasar host galaxy emission in rest-frame far-infrared (FIR) wavelengths, allowing us to conclusively determine the nature of J2037–4537." (Introduction)
- Target **J2037–4537**: coordinates A: 20:37:21.27 -45:37:48.8; B: 20:37:21.26 -45:37:47.5  
  > "These previous observations show that J2037–4537 consists of two point sources separated by $1.24''$, both exhibiting the spectrum of a type-I quasar at redshift $z=5.7$." (2.1 The Target); "| R.A. | 20:37:21.27 | 20:37:21.26 |" (Table 1); z/distance z_[CII] = 5.6947 (A), 5.6948 (B)  
  > "These previous observations show that J2037–4537 consists of two point sources separated by $1.24''$, both exhibiting the spectrum of a type-I quasar at redshift $z=5.7$." (2.1 The Target); "| R.A. | 20:37:21.27 | 20:37:21.26 |" (Table 1); distance from [C II] line fit in this paper  
  > "These previous observations show that J2037–4537 consists of two point sources separated by $1.24''$, both exhibiting the spectrum of a type-I quasar at redshift $z=5.7$." (2.1 The Target); "| R.A. | 20:37:21.27 | 20:37:21.26 |" (Table 1)

## Data provenance

- ALMA projects: 2021.1.01052.S
- bands: Band 7  
  > "J2037–4537 was observed by ALMA in Band 7 under configuration C43-5 in August 2022" (2.2 ALMA Observations)
- frequencies and spectral setup: four 1.875 GHz-wide SPWs at 284.451, 286.263, 296.450, 298.263 GHz  
  > "We tuned the four 1.875 GHz-wide spectral windows (SPWs) at 284.451 GHz, 286.263 GHz, 296.450 GHz, and 298.263 GHz." (2.2 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-5  
  > "J2037–4537 was observed by ALMA in Band 7 under configuration C43-5 in August 2022" (2.2 ALMA Observations)
- baselines: _not stated_
- angular resolution: 0.44'' x 0.26'' clean beam (continuum)  
  > "the clean beam size is $0.44\ensuremath{''}\times0.26\ensuremath{''}$." (2.2 ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 5,564 seconds  
  > "The on-source exposure time is 5,564 seconds." (2.2 ALMA Observations)
- observing dates: August 2022  
  > "J2037–4537 was observed by ALMA in Band 7 under configuration C43-5 in August 2022" (2.2 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: [C II] 158 um fine-structure line (not stated)
- Other facility **HST ACS/WFC F850LP, Magellan LDSS and FIRE, DES**: Discovery, imaging and optical-NIR spectra of the quasar pair (from earlier work)  
  > "(cite: yue21) presented the Hubble Space Telescope Advanced Camera for Surveys Wide Field Camera F850LP band image" (2.1 The Target)
- External data: Quasar bolometric luminosities (log Lbol=47.1, 46.9) and SMBH masses (3.9e8, 2.8e8 Msun)  
  > "(cite: yue21) measured the bolometric luminosities of the two quasars to be $\log L_\text{bol}[\text{erg s}^{-1}]=47.1$ and $46.9$" (2.1 The Target) [from (cite: yue21)]
- External data: Quasar luminosity function used to estimate N_qso=83 at 5.5<z<6 in DES  
  > "Using the quasar luminosity function in (cite: mat18) and the template quasar spectrum in (cite: vb01)" (4.1 Quasar Pair Fraction) [from (cite: mat18); (cite: vb01)]
- External data: Dust temperature 47 K and beta=1.6  
  > "We adopt a canonical dust temperature of $T_\text{dust}=47$K and emissivity of $\beta=1.6$ (cite: beelen06)." (3.2 Quasar Host Galaxy Properties) [from (cite: beelen06)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 6.5.4.9  
  > "We reduce the ALMA data using the Common Astronomy Software Applications (cite: casa) version 6.5.4.9." (2.2 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean, interactive  
  > "we run task `tclean` interactively using natural weighting, until the residual shows no significant patterns beyond the background noise level." (2.2 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "we run task `tclean` interactively using natural weighting" (2.2 ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub linear fit to line-free channels  
  > "we use CASA task `uvcontsub` to fit a linear model to the line-free channels and subtract the linear model from the total visibility" (2.2 ALMA Observations)
- line free channels: nu_obs > 284.5 GHz  
  > "splitting out the line-free channels (i.e., with $\nu_\text{obs}>284.5$ GHz)" (2.2 ALMA Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.44'' x 0.26'' (continuum)  
  > "the clean beam size is $0.44\ensuremath{''}\times0.26\ensuremath{''}$." (2.2 ALMA Observations)
- final rms: _not stated_

### Inherited from earlier work

- Dynamical mass relation for dispersion-dominated systems and [C II] luminosity relation  
  > "we estimate the dynamical masses of the quasar hosts using the relation in (cite: decarli18), which is suitable for dispersion-dominated systems" (3.2 Quasar Host Galaxy Properties) [from (cite: decarli18); (cite: wang24)]
- SFR-L_TIR relation  
  > "we estimate the star formation rates following the relation in (cite: kennicutt12)" (3.2 Quasar Host Galaxy Properties) [from (cite: kennicutt12)]
- Dynamical friction timescale expressions  
  > "We follow the expression in (cite: chen23)" (4.2 Merger Timescale Estimate) [from (cite: chen23)]

### Not stated but needed to reproduce (our reading)

- Number of channels/channel width and velocity resolution of the [C II] cube
- Cell size, image size, masks and clean thresholds
- Calibrators and whether the pipeline or manual calibration was used
- MCMC sampler, priors and likelihood for Gaussian line fits
- PyAutoLens model setup, priors and settings
- Which line-free channels were used given the line at the spectrum edge
- Procedure for sigma used in M_dyn (conversion from FWHM, size inputs)
- Inclination or random-orientation assumption details for M_dyn

## Analysis recipe

1. **Continuum imaging**: Split line-free channels, run tclean interactively with natural weighting  
  > "we obtain the continuum visibility by splitting out the line-free channels" (2.2 ALMA Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Cleaned until residual shows no significant patterns  
  > "until the residual shows no significant patterns beyond the background noise level" (2.2 ALMA Observations)
2. **[C II] cube, spectra and redshifts**: uvcontsub then tclean; extract spectra in 0.8'' circular apertures; fit Gaussian plus constant with MCMC  
  > "we fit the spectrum around the \[C ii\] lines as a Gaussian profile plus a constant using the Markov Chain Monte Carlo (MCMC) method." (2.2 ALMA Observations)
   - software: CASA
   - parameter: aperture diameter 0.8''  
  > "The diameter of the apertures is $0.8\ensuremath{''}$" (2.2 ALMA Observations)
   - fitting: Gaussian plus constant, MCMC  
  > "Gaussian profile plus a constant using the Markov Chain Monte Carlo (MCMC) method" (2.2 ALMA Observations)
   - validation: _not stated_
3. **Moment maps**: immoments for moment 0 over 283.534-284.301 GHz; per-pixel Gaussian fits for velocity and dispersion  
  > "We produce the \[C ii\] moment 0 map using task `immoments` with a frequency range $283.534\leq\nu_\text{obs}[\text{GHz}]\leq284.301$" (2.2 ALMA Observations)
   - software: CASA
   - fitting: Per-pixel Gaussian plus constant  
  > "we fit each pixel in the cleaned \[C ii\] cube as a Gaussian profile plus a constant" (2.2 ALMA Observations)
   - validation: Example pixel fits shown in Appendix  
  > "For individual pixels, a Gaussian profile describes the spectra well." (Appendix)
4. **Lens modeling test**: Fit continuum and [C II] with singular isothermal ellipsoid plus external shear lens and Sersic sources  
  > "We assume a singular isothermal elliptical density profile for the potential lensing galaxy, and add an external shear component" (3.1 Confirming the Close Quasar Pair Hypothesis)
   - software: PyAutoLens
   - fitting: _not stated_
   - validation: Compared continuum and [C II] best-fit lens models, sizes and axis ratio  
  > "The best-fit lensing models for the continuum and the \[C ii\] line have significantly different deflector galaxy positions and Einstein radii" (3.1 Confirming the Close Quasar Pair Hypothesis)
5. **Fluxes and sizes**: imstat in apertures, error from annulus 6''-12''; imfit 2D Gaussians  
  > "We estimate the flux error using an annulus with an inner radius of $6''$ and an outer radius of $12''$, centered at the phase center." (3.2 Quasar Host Galaxy Properties)
   - software: CASA
   - fitting: imfit 2D Gaussian  
  > "which fits the emission as 2D Gaussian profiles" (3.2 Quasar Host Galaxy Properties)
   - validation: _not stated_
6. **Derive L_FIR, L_TIR, SFR, L_[CII], M_dyn**: Modified blackbody SED with CMB correction; SFR from L_TIR; L_[CII] relation; M_dyn=1.5 R_maj sigma^2/G  
  > "Using the continuum flux, we model the FIR spectral energy distribution (SED) as a modified black body" (Properties of J2037–4537 / Quasar Host Galaxy Properties)
   - assumption: T_dust=47 K, beta=1.6, kappa=0.077 (nu/352 GHz)^beta  
  > "We adopt a canonical dust temperature of $T_\text{dust}=47$K and emissivity of $\beta=1.6$ (cite: beelen06)." (3.2 Quasar Host Galaxy Properties)
   - assumption: Flat LCDM, Om=0.3, H0=70  
  > "we assume a flat $\Lambda$CDM cosmology with $\Omega_m=0.3$ and $H_0=70 \text{ km s}^{-1}\text{Mpc}^{-1}$" (Introduction)
   - fitting: _not stated_
   - validation: Discussion of systematic uncertainty from T_dust and beta  
  > "the the assumptions of $T_\text{dust}=47$K and $\beta=1.6$ introduce systematic uncertainties in $L_\text{TIR}$ and $\text{SFR}_\text{TIR}$" (3.2 Quasar Host Galaxy Properties)
7. **Quasar pair fraction lower limit**: N_qso=83 from luminosity function in DES area; F_pair>1/83; Poisson-Gamma posterior with flat prior  
  > "We thus infer a pair fraction of $F_\text{pair}>1/83=1.2\%$." (4.1 Quasar Pair Fraction)
   - assumption: J2037–4537 is the only z>5.5 pair in DES field  
  > "By assuming that J2037–4537 is the only $z>5.5$ close quasar pair in the DES field" (4.1 Quasar Pair Fraction)
   - fitting: Gamma posterior, alpha=1, beta=0  
  > "We take $\alpha=1$ and $\beta=0$, which corresponds to a flat prior." (4.1 Quasar Pair Fraction)
   - validation: _not stated_
8. **Merger timescale**: Chandrasekhar dynamical friction for galaxies then SMBHs  
  > "The total timescale for J2037–4537 to form a gravitationally-bound binary SMBH is $t_\text{total}=t^\text{gal}_\text{fric}+t^\text{BH}_\text{fric}\approx2.1$ Gyrs." (4.2 Merger Timescale Estimate)
   - assumption: SIS profiles, circular orbits, ln Lambda=0.93 (galaxies) and ~6 (BHs)  
  > "Assuming singular isothermal sphere (SIS) density profiles for the quasar host galaxy density profiles and circular orbits" (4.2 Merger Timescale Estimate)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.5.4.9: Calibration data reduction, tclean, uvcontsub, immoments, imstat, imfit  
  > "We reduce the ALMA data using the Common Astronomy Software Applications (cite: casa) version 6.5.4.9." (2.2 ALMA Observations)
- **PyAutoLens** : Lens modeling of continuum and [C II]  
  > "We use `PyAutoLens` [^1] (cite: pyautolens; Nightingale2015; Nightingale2018) to perform lens modeling." (3.1 Confirming the Close Quasar Pair Hypothesis)
- **astropy** : Listed in software section  
  > "astropy (cite: 2013A&A...558A..33A; 2018AJ....156..123A; 2022ApJ...935..167A), CASA, PyAutoLens" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [C II] redshift quasar A | 5.6947 | 0.0004 | dimensionless | 2 | $z_{\rm A}=5.6947 \pm 0.0004$ and $z_{\rm B}=5.6948 \pm 0.0005$ |
| [C II] redshift quasar B | 5.6948 | 0.0005 | dimensionless | 2 | $z_{\rm A}=5.6947 \pm 0.0004$ and $z_{\rm B}=5.6948 \pm 0.0005$ |
| 287 GHz continuum flux A / B | 0.807 / 0.828 | 0.008 / 0.007 | mJy | 5 | / $F_\text{287GHz}$ (mJy) / $0.807\pm0.008$ / $0.828\pm0.007$ / |
| [C II] line flux A / B | 1.95 / 1.30 | 0.26 / 0.18 | Jy km/s | 5 | $1.95\pm0.26$ / $1.30\pm0.18$ |
| L_TIR A / B | 4.52e12 / 3.66e12 | 0.19e12 / 0.13e12 | Lsun | 6 | $(4.52\pm0.19)\times10^{12}$ / $(3.66\pm0.13)\times10^{12}$ |
| SFR_TIR A / B | 672 / 543 | 29 / 19 | Msun/yr | 6 | / $672\pm29$ / $543\pm19$ / |
| M_dyn A / B | 2.2e10 / 4.6e10 | 0.7e10 / 1.7e10 | Msun | 6 | $(2.2\pm0.7)\times10^{10}$ / $(4.6\pm1.7)\times10^{10}$ |
| [C II] FWHM A / B | 549 / 479 | 79 / 75 | km/s | 2 | $549\pm79$ / $479\pm75$ |
| Pair fraction lower limit | 1.2% | not stated | percent | 7 | We thus infer a pair fraction of $F_\text{pair}>1/83=1.2\%$. |
| F_pair at 95% probability | >4.28e-3 | not stated | dimensionless | 7 | the probability of having $F_\text{pair}>4.28\times10^{-3}$ is $95\%$ |
| Total binary formation timescale | 2.1 | not stated | Gyr | 8 | $t_\text{total}=t^\text{gal}_\text{fric}+t^\text{BH}_\text{fric}\approx2.1$ Gyrs |

## Qualitative findings

- Continuum shows tidal bridge between the two quasars; quasar B irregular in [C II] moment 0  
  > "The tidal bridge in the dust continuum map and the irregular structures of quasar B in the \[C ii\] moment 0 map indicate that J2037–4537 is an on-going galaxy merger." (3.1 Confirming the Close Quasar Pair Hypothesis)

## Claim tuples

- H: J2037–4537 is a lensed quasar rather than a physical pair | E: Examined ALMA continuum and [C II] morphology and fit lens models | R: Tidal bridge, no arcs; continuum and [C II] lens models inconsistent, tiny sizes, q=0.17 | F: J2037–4537 is a physical close quasar pair | **supported**
- H: Host galaxies are massive and star-forming | E: Continuum SED and [C II] measurements | R: M_dyn 2.2e10 and 4.6e10 Msun; SFR 672 and 543 Msun/yr | F: Massive, actively star-forming hosts | **supported**
- H: Quasar pair fraction at z>5.5 is elevated | E: Compared 1 pair to estimated 83 quasars in DES | R: F_pair>1.2% | F: Pair fraction much higher than at z<~4 | **supported**
- H: The pair will form a bound SMBH binary | E: Dynamical friction timescale estimate | R: ~2.1 Gyr | F: Binary formation at z~2, relevant to PTA background | **partially**

## Reasoning

- Why this data: Rest-frame FIR emission of quasars is dominated by host galaxies, so ALMA can reveal tidal features  
  > "ALMA is the ideal facility for this experiment, as the rest-frame FIR emission of quasars is dominated by their host galaxies." (2.1 The Target)
- Why this method: _not stated_
- Alternative: Doubly-imaged lensed quasar rejected via lens modeling  
  > "We show that the dust continuum and \[C ii\] line cannot be described by the same lensing model, ruling out the strong lensing hypothesis." (Summary)
- How they decided it was enough: _not stated_
- Limitation (authors): T_dust and beta assumed; multi-band FIR needed  
  > "Future multi-band FIR photometry is needed to directly constrain $T_\text{dust}$ and $\beta$ for J2037–4537." (3.2 Quasar Host Galaxy Properties)
- Limitation (authors): Pair fraction is a lower limit because the survey is incomplete  
  > "This value is a lower limit because the survey of (cite: yue21) is incomplete." (4.1 Quasar Pair Fraction)
- Caveat (inferred, ours): Single system gives pair fraction with large Poisson uncertainty
- Caveat (inferred, ours): Assumed T_dust/beta drive L_TIR and SFR
- Caveat (inferred, ours): Dynamical masses from dispersion-dominated assumption with a line at the spectral edge
- Caveat (inferred, ours): Lens modeling details not given, so rejection is hard to verify
- Caveat (inferred, ours): N_qso depends on extrapolated luminosity function

## Reproducibility

- Data public (paper): Raw ALMA data downloadable from the ALMA Science Archive  
  > "The raw ALMA data can be downloaded via the ALMA Science Archive" (Summary)
- Products in archive: _not stated_
- Code: Code and figure data at Zenodo 10.5281/zenodo.19211007  
  > "The code used in this work and the data for making the figures can be found at [10.5281/zenodo.19211007](10.5281/zenodo.19211007)." (Summary)
- Missing: Imaging parameters (cell, size, channel width, masks)
- Missing: Calibration details
- Missing: MCMC and lens-model settings
- Data volume (inferred): A few GB (single Band 7 execution, ~1.5 h on source)
- Score (inferred): 4/5, Public single-project data, code released on Zenodo, compact recipe, but imaging and fitting settings are sparse.
- Rediscovery candidate: yes, Public data, simple recipe, and numeric results in Table 1 can be rederived.

## Links

- Method: (cite: decarli18) ([C II] and dynamical mass relations)
- Method: (cite: chen23) (dynamical friction timescales and pair confirmation approach)
- Companion: (cite: yue21) (discovery and optical/NIR data of J2037–4537)
- Related: Dark Energy Survey
- Related: HSC Subaru Strategic Program
- Related: J1215–0148 (z=6.05 quasar pair)

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 54,
  "rate": 0.621
 },
 "evidence_ok": true
}
```
