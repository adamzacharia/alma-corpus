# Probing the Full CO Spectral Line Energy Distribution (SLED) in the Nuclear Region of a Quasar-starburst System at z = 6.003

`2020ApJ...889..162L` | The Astrophysical Journal 2020 | first author: Li, Jianan | arXiv: 1912.12813 | DOI: 10.3847/1538-4357/ab65fa

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What are the physical conditions and heating mechanisms of the molecular gas in the z=6.003 quasar J2310+1855, as probed by its CO SLED and H2O and OH+ lines?  
  > "aiming to probe the physical conditions of the molecular gas content of this source." (abstract)
- Target **SDSS J231038.88+185519.7 (J2310+1855)**: coordinates _not stated_; z/distance z = 6.0031; D_L = 57763 Mpc  
  > "where 1$''$ corresponds to 5.7 kpc at the J2310 + 1855 redshift ($z=6.0031$), and the luminosity distance to J2310+1855 is 57763 Mpc." (1 Introduction); distance from redshift; flat LCDM H0=70, Om=0.3  
  > "where 1$''$ corresponds to 5.7 kpc at the J2310 + 1855 redshift ($z=6.0031$), and the luminosity distance to J2310+1855 is 57763 Mpc." (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.01265.S
- bands: ALMA Band 4; NOEMA 3 mm and 1 mm  
  > "The CO $(8-7)$, $(9-8)$, $\rm H_{2}O$ and $\rm OH^{+}$ lines were observed in ALMA Band 4 with two separate executions" (2.1 ALMA)
- frequencies and spectral setup: four 1.875 GHz spectral windows of 128 channels per execution; CO(8-7) at 131.6274 GHz, CO(9-8) at 148.0648 GHz  
  > "we used four spectral windows, each with a width of 1.875 GHz consisting of 128 channels, with two of the windows in the lower sideband (LSB) and the other two in the upper sideband (USB)." (2.1 ALMA)
- continuum bandwidth: _not stated_
- arrays: 36 to 44 12-m antennas  
  > "where 36 to 44 12-m diameter antennas were used during observations." (2.1 ALMA)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beams 0.6-0.8 arcsec  
  > "with beam sizes between $0.6\ensuremath{''}$ and $0.8\ensuremath{''}$" (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: rms 0.17 and 0.19 mJy/beam per 36 and 32 km/s channel; continuum 15 uJy/beam  
  > "the corresponding rms sensitivities were 0.17 and 0.19 $\rm mJy\ beam^{-1}$ respectively. The sensitivity of the underlying continuum was 15 $\rm \mu Jy\ beam^{-1}$." (2.1 ALMA)
- time on source: 34.9 and 30.3 min (ALMA); 1.18 h and 6.2 h (NOEMA)  
  > "With a total on source time of 34.9 and 30.3 minutes for CO $(8-7)$($\rm H_{2}O$) and CO $(9-8)$($\rm OH^{+}$)" (2.1 ALMA)
- observing dates: April to November 2016 (ALMA)  
  > "All the observations were executed between April and November in 2016" (2.1 ALMA)
- pi or archival as stated: _not stated_
- Line: CO 8-7 (921.7997 GHz)
- Line: CO 9-8 (1036.9124 GHz)
- Line: H2O 2(0,2)-1(1,1) (987.9268 GHz)
- Line: OH+ 1(1)-0(1) (1033 GHz)
- Other facility **NOEMA (W18EE)**: CO(5-4), (6-5), (12-11), (13-12) and continuum  
  > "and the underlying continuum of this quasar with NOEMA (Project W18EE)." (2.2 NOEMA)
- External data: CO(2-1) flux, source size and dynamical mass (4.3e10 Msun) used in the SED and priors  
  > "The source size and gas dynamical mass are adopted from (cite: shao19), with $M_{\rm dyn} \approx 4.3 \times 10^{10}\ M_{\ensuremath{\odot}}$" (4 Radiative Transfer Analysis) [from (cite: shao19)]
- External data: CO(10-9) flux 1.04 +/- 0.17 Jy km/s  
  > "bright CO $(10-9)$ emission with a line flux of 1.04 $\pm$ 0.17 $\rm Jy \ km\ s^{-1}$ (Riechers et al. in prep)" (1 Introduction) [from Riechers et al. in prep]
- External data: Cold gas component parameters Tkin~50 K, log n=4.2 from J1148+5251  
  > "$T_{\rm kin} \approx$ 50 K and $log (n(\rm H_{2})/ \rm cm^{-3} )=4.2$ that is observed in a "typical" $z\sim 6$ quasar J1148+5251 (cite: riechers09)" (4.3 Fitting Results) [from (cite: riechers09)]
- Simulation/model as data: MOLPOP-CEP slab model grid: Tkin 20-800 K, n(H2) 1e3-1e8, N(CO) 1e14-1e21  
  > "Kinetic Temperature ($T_{\rm kin}$) | 20 - 800 | $\rm \Delta T_{kin} = 13$ | 61 | K" (Table 4)

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline  
  > "using the standard ALMA pipeline" (2.1 ALMA)
- casa version: CASA 4.7.0  
  > "Common Astronomy Software Applications (CASA) software package version 4.7.0" (2.1 ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Pallas (flux); SDSS J2253+1608 phase and bandpass  
  > "The fluxes were calibrated using the standard flux calibrator $Pallas$, while SDSS J2253+1608 was used as both the phase calibrator and the bandpass calibrator." (2.1 ALMA)
- flux scale uncertainty: 15% adopted for ALMA Band 4  
  > "here we use $15\%$ uncertainty that also includes the uncertainties of the old $Pallas$ flux model in early casa versions" (2.1 ALMA)
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN  
  > "The maps were generated using the CLEAN task in CASA" (2.1 ALMA)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 2 (natural)  
  > "we apply the robust weighting algorithm with a Briggs parameter of 2 equivalent to natural weighting" (2.1 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: first order polynomial continuum; line cubes from continuum-subtracted data  
  > "The continuum level was determined using a first order polynomial, and the emission lines were imaged from the continuum subtracted data cube" (2.1 ALMA)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.79x0.75 and 0.77x0.63 arcsec (lines)  
  > "This results in a FWHM synthesized beam size of $0.79\ensuremath{''}$ $\times$ $0.75\ensuremath{''}$" (2.1 ALMA)
- final rms: 0.17 and 0.19 mJy/beam  
  > "the corresponding rms sensitivities were 0.17 and 0.19 $\rm mJy\ beam^{-1}$ respectively." (2.1 ALMA)

### Inherited from earlier work

- Continuum detection published earlier  
  > "The continuum detection were published in (cite: shao19)." (3 Results) [from (cite: shao19)]
- Number of zones (10) for MOLPOP-CEP  
  > "Here we divide the geometry into 10 zones for the model calculation as is suggested by (cite: asensio18)." (4.1 Method) [from (cite: asensio18)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and channel ranges used for continuum fitting
- Image size, cell size, clean threshold and masks
- Priors, walker number, steps and likelihood details for emcee
- How calibration uncertainty enters chi-square
- Normalization parameters in two-component fit
- Absolute coordinates of the target
- Flux extraction aperture details for ALMA line fluxes

## Analysis recipe

1. **Calibrate and image ALMA data**: Standard pipeline calibration in CASA, CLEAN with natural weighting, continuum subtraction, binning to 36/32 km/s  
  > "The observational data were calibrated and reduced with the Common Astronomy Software Applications (CASA) software package version 4.7.0" (2.1 ALMA)
   - software: CASA
   - parameter: robust = 2; first-order polynomial continuum  
  > "we apply the robust weighting algorithm with a Briggs parameter of 2 equivalent to natural weighting" (2.1 ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Reduce NOEMA data**: GILDAS CLIC/MAPPING; UV_AVERAGE, UV_SUBTRACT, HOGBOM clean with natural weighting  
  > "Both the $uv$ table of the continuum and spectral lines were cleaned with the HOGBOM algorithm and NATURAL weighting was used to ensure the maximum S/N." (2.2 NOEMA)
   - software: GILDAS
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure line fluxes, widths, redshifts and sizes**: Gaussian fit to spectra integrated within the 2 sigma contour; 2D Gaussian fit to intensity maps, deconvolved with beam  
  > "We calculate the line widths, redshift, and fluxes of CO $(8-7)$, $(9-8)$ and $\rm H_{2}O$ by fitting a Gaussian profile to the spectra." (3 Results)
   - fitting: single Gaussian; OH+ center fixed to [CII] redshift  
  > "so we fix the center frequency to the \[C II\]$\rm \ 158\mu m$ redshift" (3 Results)
   - validation: Compared to previous CO(6-5) and [CII] measurements  
  > "The new NOEMA observation yield a CO $(6-5)$ flux of 1.05 $\pm$ 0.07 Jy $\rm km \ s^{-1}$, consistent with the results obtained with ALMA" (3 Results)
4. **Fit CO SLED with MOLPOP-CEP slab grid**: Least squares and emcee on grid of uniform slabs (10 zones), one- and two-component models  
  > "we first apply the least square method to find the best fitting results. We also use the Bayesian code emcee" (4.1 Method)
   - software: MOLPOP-CEP, emcee
   - parameter: X_CO=1e-4, local linewidth 1 km/s, CMB 19.12 K, 10 zones  
  > "we fix the molecular abundance of CO to $X_{\rm CO} = 10^{-4}$ (Milky Way, (cite: blake87)), and local linewidth to 1 $\rm km\ s^{-1}$" (4.1 Method)
   - assumption: Tkin>19.12 K; N(CO)Phi<3.2e19 cm-2 from dynamical mass; N(CO)/n(H2)<1.1e18 cm  
  > "The fact that $T_{\rm kin}$ is hotter than the background CMB radiation at redshift 6 is a prior, which sets $T_{\rm kin} >$19.12 K." (4.2 Parameter Constraints)
   - fitting: Cold component fixed at Tkin 50 K, log n 4.2, log N(CO) 18.0 in two-component fit (five free parameters)  
  > "With this assumption, we are fitting only five instead of eight parameters." (4.3 Fitting Results)
   - validation: Results consistent within 1 sigma with/without CO(10-9)  
  > "The resulting parameter ranges are consistent within 1$\sigma$ between including and excluding the CO $(10-9)$ line in the fitting procedure." (4.3 Fitting Results)
5. **Compare with PDR models and other samples**: Fit CO SLED to the PDR grid of Meijerink07; compare SLEDs, L_H2O/L_IR, L_H2O/L_CO and L_OH+/L_H2O with literature  
  > "we fit the CO SLED of J2310+1855 to the PDR grid (cite: meijerink07)" (5.5 Molecular gas heating mechanisms)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0: calibration and imaging of ALMA data  
  > "software package version 4.7.0 (cite: casa07), using the standard ALMA pipeline" (2.1 ALMA)
- **GILDAS (CLIC, MAPPING)** : NOEMA reduction and imaging  
  > "packages CLIC and MAPPING" (2.2 NOEMA)
- **MOLPOP-CEP** : radiative transfer CO SLED modelling  
  > "We here use the radiative transfer model MOLPOP-CEP to investigate the physical conditions of the molecular gas" (4 Radiative Transfer Analysis)
- **emcee** : posterior sampling of model parameters  
  > "We also use the Bayesian code emcee (cite: foreman13) to efficiently explore the parameter space" (4.1 Method)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| One-component best fit Tkin | 228 | not stated | K | 4 | kinetic temperature of $T_{\rm kin} = 228 \ \rm K$ |
| One-component emcee Tkin | 167 | +153/-56 | K | 4 | $T_{\rm kin} \approx 167^{+153}_{-56} \ \rm K$ |
| Two-component warm Tkin (emcee) | 306 | +263/-149 | K | 4 | $T_{\rm kin} \approx 306^{+263}_{-149}\  \rm K$ |
| CO(8-7) line flux | 1.53 | 0.05 | Jy km/s | 3 | CO $(8-7)$ / 6.0028 $\pm$ 0.0001 / 390 $\pm$ 15 / 1.53 $\pm$ 0.05 |
| CO(9-8) line flux | 1.31 | 0.06 | Jy km/s | 3 | CO $(9-8)$ / 6.0031 $\pm$ 0.0002 / 376 $\pm$ 18 / 1.31 $\pm$ 0.06 |
| L_H2O/L_CO(6-5) | 0.97 | 0.09 | dimensionless | 5 | exhibits a $L_{\rm H_{2}O}$/$L_{CO\ (6-5)}$ ratio of 0.97 $\pm$ 0.09 |
| L_OH+/L_H2O | 0.20 | 0.15 | dimensionless | 5 | exhibit a $L_{\rm OH^{+}}$/$L_{\rm H_{2}O}$ ratio of 0.20 $\pm$ 0.15 |

## Qualitative findings

- CO SLED peaks at J=8, higher than local starbursts, SMGs and local AGNs  
  > "while the J2310+1855 CO SLED peaks at much higher $J$ transitions at $J=8$" (5.1)

## Claim tuples

- H: The J>=5 CO emission arises from warm dense gas | E: MOLPOP-CEP grid fit with emcee, one and two components | R: Tkin ~167-306 K, log n ~5.1-5.2 | F: CO SLED dominated by warm dense component | **supported**
- H: Excitation is higher than in starbursts | E: Compare SLEDs with (U)LIRG, SMG, AGN samples | R: Peak at J=8 | F: Higher excitation than comparison samples | **supported**
- H: UV from stars alone does not power the gas | E: H2O/CO and OH+/H2O ratios versus literature | R: High ratios similar to Mrk 231 | F: Shocks, cosmic rays or X-rays likely contribute | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: One-component model underpredicts CO(8-7), motivating a two-component model  
  > "But the current best fit model fail to reproduce the very high CO $(8-7)$ line flux detected." (4.3 Fitting Results)
- How they decided it was enough: _not stated_
- Limitation (authors): OH+ detection tentative (4 sigma); data insufficient to constrain all eight two-component parameters  
  > "Our data are insufficient to constrain all eight parameters." (4.3 Fitting Results)
- Caveat (inferred, ours): Cold component is fixed from another quasar, so the two-component result is assumption-driven
- Caveat (inferred, ours): Single-slab models with 1 km/s linewidth are crude
- Caveat (inferred, ours): Different beams across lines may bias SLED ratios
- Caveat (inferred, ours): Heating mechanism inference is qualitative

## Reproducibility

- Data public (paper): ALMA project ID given; NOEMA project W18EE  
  > "This paper is based on ALMA observations:ADS/JAO.ALMA 2015.1.01265.S." (acknowledgement)
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust
- Missing: emcee priors and setup
- Missing: NOEMA data may be proprietary
- Missing: CO(10-9) flux from unpublished work
- Data volume (inferred): ~10-30 GB for the ALMA Band 4 project
- Score (inferred): 3/5, ALMA data public, recipe partially specified; modelling setup largely described but sampler details and imaging details missing.
- Rediscovery candidate: no, Key results depend on NOEMA data and unpublished CO(10-9), plus incomplete fitting details.

## Links

- Method: (cite: asensio18) (MOLPOP-CEP code)
- Companion: (cite: shao19) (continuum and CO(2-1) of the same quasar)
- Companion: (cite: wang13) ([CII] and CO(6-5) PdBI data)

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 46,
  "rate": 0.613
 },
 "evidence_ok": true
}
```
