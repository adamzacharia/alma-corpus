# Inspiraling streams of enriched gas observed around a massive galaxy 11 billion years ago

`2023Sci...380..494Z` | Science 2023 | first author: Zhang, Shiwu | arXiv: 2305.02344 | DOI: 10.1126/science.abj9192

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Does the circumgalactic gas around the z~2.3 MAMMOTH-1 nebula trace metal-enriched inspiraling streams (recycled inflow) rather than an AGN outflow?  
  > "The kinematics of this circumgalactic gas is consistent with an inspiraling stream." (abstract); "We interpret the results as evidence of gas recycling during high-redshift galaxy assembly." (abstract)
- Target **MAMMOTH-1 nebula (quasar host G-2)**: coordinates J2000 14h41m24.42s, +40d03'09.7"  
  > "One such Ly$\alpha$ nebula is the MAMMOTH-1 (J2000 $14^{\rm h}41^{\rm m}24.42^{\rm s}$, $+40^{\circ}03'09.7''$) nebula at $z\approx2.31$" (Observations of MAMMOTH-1); "we measure the systemic redshift of MAMMOTH-1 to be $2.3116\pm 0.0004$ and $2.3120\pm 0.0006$ from the two CO lines, respectively." (Materials and Methods); z/distance z = 2.3116 ± 0.0004  
  > "One such Ly$\alpha$ nebula is the MAMMOTH-1 (J2000 $14^{\rm h}41^{\rm m}24.42^{\rm s}$, $+40^{\circ}03'09.7''$) nebula at $z\approx2.31$" (Observations of MAMMOTH-1); "we measure the systemic redshift of MAMMOTH-1 to be $2.3116\pm 0.0004$ and $2.3120\pm 0.0006$ from the two CO lines, respectively." (Materials and Methods); distance from CO (J=1→0) from archival radio data (Emonts2019)  
  > "One such Ly$\alpha$ nebula is the MAMMOTH-1 (J2000 $14^{\rm h}41^{\rm m}24.42^{\rm s}$, $+40^{\circ}03'09.7''$) nebula at $z\approx2.31$" (Observations of MAMMOTH-1); "we measure the systemic redshift of MAMMOTH-1 to be $2.3116\pm 0.0004$ and $2.3120\pm 0.0006$ from the two CO lines, respectively." (Materials and Methods)

## Data provenance

- ALMA projects: 2018.1.00859.S
- bands: _not stated_
- frequencies and spectral setup: CO (J=3→2) data (Li2021) used for redshifts, FWHM and luminosities of G-1 to G-6; no ALMA setup details given  
  > "Redshift is the spectroscopic redshifts from the CO (J=3→2)." (Table S3)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=3→2 (not stated)
- Other facility **Keck/KCWI**: IFU spectroscopy of Lyα, C IV, He II (primary data)  
  > "Our team observed MAMMOTH-1 with the Keck Cosmic Web Imager (KCWI) on the 10-m Keck II telescope" (Observations of MAMMOTH-1)
- Other facility **Subaru/MOIRCS**: Hα narrowband imaging  
  > "We also performed narrowband imaging of redshifted H$\alpha$" (Observations of MAMMOTH-1)
- Other facility **Chandra/ACIS-I**: 2-8 keV X-ray detection of G-2  
  > "We also proposed the X-ray observations for MAMMOTH-1 for this work (Fig. S1B)." (Materials and Methods)
- Other facility **VLA**: CO (J=1→0) systemic redshift (Emonts2019)  
  > "From the archival CO (J=1→0) radio observations (cite: Emonts2019)," (Observations of MAMMOTH-1)
- Other facility **HST**: F160W image of the galaxy group  
  > "Hubble Space Telescope image of the galaxy group, using the rest-frame optical filter, F160W." (Figure 1 caption)
- External data: CO (J=3→2) luminosity, H2 masses and FIR luminosity L_FIR = 2.0±0.4e45 erg/s  
  > "which is $L_{\rm FIR}=2.0\pm0.4 \times10^{45}$ erg s$^{-1}$ (cite: Li2021)" (Materials and Methods) [from Li2021]
- External data: CO (J=1→0) systemic redshift and FWHM of G-2  
  > "the radio observations show that the FWHM of the CO (J=1→0) emission of G-2 is 85 km s$^{-1}$ (cite: Emonts2019)." (Systemic Redshift) [from Emonts2019]
- Simulation/model as data: IllustrisTNG TNG-100 at z=2 used for halo selection and stream geometry  
  > "We focus on the TNG-100 simulation box because it has a sufficient number of massive halos to statistically assess the kinematics and physical properties of the CGM." (Materials and Methods)

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

- ALMA CO (J=3→2) data reduction and measurements taken from earlier paper  
  > "The H$_{\rm 2}$ gas mass converted from the CO (J=3→2) emissions (cite: Li2021)." (Table S3) [from (cite: Li2021)]
- CLOUDY parameter choices follow previous work  
  > "We follow previous work (cite: Cai2017a; Arrigoni2015a) in setting the parameters of CLOUDY." (Line ratio diagnostics) [from (cite: Cai2017a; Arrigoni2015a)]

### Not stated but needed to reproduce (our reading)

- ALMA observing setup, array configuration, calibration and imaging of the CO(3-2) data (all in Li2021)
- How G-1 to G-6 spectra and FWHM were extracted from the ALMA cube
- MCMC priors and likelihood for the stream model

## Analysis recipe

1. **Fit ALMA CO(3-2) line properties of group galaxies**: Gaussian fit to CO(3-2) lines to get redshift and FWHM of G-1 to G-6; used for group redshift gradient and halo mass  
  > "FWHM denotes the line width of the CO (J=3→2) emission yielded by the Gaussian fit." (Table S3)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit inspiraling stream kinematic model to KCWI spectra**: MCMC fit of nine kinematic parameters of three spiral streams to spectra  
  > "To determine the best-fitting values, we minimize the residual between the observed spectra and the simulated spectra from the same aperture (Fig. 4D & E) and apply a Markov Chain Monte Carlo (MCMC) analysis." (Kinematics of Inspiraling Streams)
   - parameter: thirty chains, 100,000 steps, first 1000 discarded  
  > "We initialize this process with thirty Markov chains and iterate each chain over 100,000 steps." (Kinematics of Inspiraling Streams)
   - assumption: edge-on inclination i=90 deg; geometry fixed from TNG  
  > "We assume the inclination to be $i=90^{\rm o}$, that is, that the inspiraling streams are edge-on." (Geometry of Inspiraling Streams)
   - fitting: MCMC; priors not stated  
  > "To determine the best-fitting values, we minimize the residual between the observed spectra and the simulated spectra from the same aperture (Fig. 4D & E) and apply a Markov Chain Monte Carlo (MCMC) analysis." (Materials and Methods, Kinematics of Inspiraling Streams)
   - validation: Alternative geometries give similar profiles (chi_r^2≈0.8)  
  > "the model yields the almost the same line-of-sight velocity profile ($\chi_{\rm r}^{2}\approx 0.8$)" (Robustness of Inspiraling-stream Model)

## Software

- **CLOUDY** V17.02: photoionization line ratio models  
  > "We use the CLOUDY (V17.02) (cite: Ferland2017) to model the line ratios of the extended nebular emission." (Line ratio diagnostics)
- **CIGALE** : SED fitting for AGN luminosity, stellar mass  
  > "From the spectral energy distribution (SED) of G-2 with CIGALE (cite: Boquien2019)" (Materials and Methods)
- **CIAO** : Chandra X-ray source detection  
  > "This X-ray source is detected by the CIAO (cite: CIAO2006)" (Materials and Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| mass inflow rate | 703 | +101/-78 | Msun/yr | 2 | we calculate $\dot{M}_{\rm in}=703^{+101}_{-78} \ M_{\odot}$ yr$^{-1}$ |
| SFR of G-2 | 81 | 18 | Msun/yr | 0 | we estimate SFR to be $81\pm 18 \ M_{\odot}$ yr$^{-1}$ |
| CO(1-0) systemic redshift of G-2 | 2.3116 | 0.0004 | dimensionless | 0 | We choose the redshift determined by the diffuse CO (J=1→0) emission, $z=2.3116\pm0.0004$ |
| CO(3-2) redshift of G-2 | 2.3120 | 0.0006 | dimensionless | 1 | $2.3120\pm0.0006$ |

## Qualitative findings

- He II/Hα requires shock-with-precursor model, CGM metallicity 0.1-1.0 Zsun on ~100 kpc  
  > "Our measurements show that the CGM in MAMMOTH-1 has been enriched to between 0.1 and 1.0$Z_\odot$ on $\approx 100$ kpc scales." (Analysis of line ratios)

## Claim tuples

- H: Is the CGM kinematics an AGN outflow or inspiraling enriched streams? | E: Compared velocity profile and coupling efficiency with outflow expectations and fit a three-stream model | R: Outflow needs f_c=5.82; stream model reproduces spectra with reduced chi2 ~0.9 | F: Metal-enriched inspiraling streams (recycled gas) favored | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: AGN outflow and tidal stripping rejected  
  > "We investigated whether the observed kinematics could be produced by an active galactic nucleus (AGN) outflow" (Interpretation of the kinematics)
- How they decided it was enough: _not stated_
- Limitation (authors): Stream model geometry not unique; quantitative parameters poorly constrained  
  > "its quantitative parameters are not well constrained by the data." (Robustness of Inspiraling-stream Model)
- Caveat (inferred, ours): ALMA data are only a minor input; main results rest on KCWI
- Caveat (inferred, ours): Stream model is degenerate with fixed geometry
- Caveat (inferred, ours): Shock models may not be unique

## Reproducibility

- Data public (paper): All data public, including ALMA 2018.1.00859.S  
  > "The Keck/KCWI, HST, Subaru/MOIRCS, ALMA, VLA, and Chandra/ACIS data used in this work are publicly available." (Data and materials availability)
- Products in archive: _not stated_
- Missing: ALMA processing details
- Missing: MCMC priors and code
- Data volume (inferred): ~10s GB for ALMA; more for KCWI
- Score (inferred): 3/5, Public data and detailed methods, but ALMA is minor and stream-model code is unreleased.
- Rediscovery candidate: no, ALMA role minor; main results depend on non-ALMA data and custom model.

## Links

- Companion: Li2021 (Source of ALMA CO(3-2) data and FIR luminosity)
- Companion: Emonts2019 (CO(1-0) systemic redshift)

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
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 28,
  "rate": 0.418
 },
 "evidence_ok": true
}
```
