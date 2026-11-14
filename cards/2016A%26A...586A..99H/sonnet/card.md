# Steepening of the 820 μm continuum surface brightness profile signals dust evolution in TW Hydrae's disk

`2016A&A...586A..99H` | Astronomy and Astrophysics 2016 | first author: Hogerheijde, Michiel R. | arXiv: 1512.05553 | DOI: 10.1051/0004-6361/201527754

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: What is the radial surface-brightness profile and dust surface density of the 820 um continuum in TW Hya's disk, and does it show signatures of grain growth and drift?  
  > "We determine the surface-brightness profile of the continuum emission using resolved observations at millimeter wavelengths of the disk around TW Hya, and infer the signature of dust evolution on the surface density and dust opacity." (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance 53.7±6.2 pc  
  > "At a distance of $53.7\pm6.2$ pc (cite: vanleeuwen2007), TW Hya is the closest gas- and dust-rich planet-forming disk" (Introduction); distance from van Leeuwen 2007  
  > "At a distance of $53.7\pm6.2$ pc (cite: vanleeuwen2007), TW Hya is the closest gas- and dust-rich planet-forming disk" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00340.S, 2011.0.00399.S
- bands: 340.S: 804–837 um (348–373 GHz); 399.S: 867–898 um (334–346 GHz)  
  > "covering wavelengths of 804–837 $\mu$m (frequencies of 348–373 GHz), a total bandwidth of 0.94 GHz" (2 Observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 0.94 GHz (340.S); 0.24 GHz (399.S)  
  > "a total bandwidth of 0.24 GHz" (2 Observations and data reduction)
- arrays: _not stated_
- configurations: _not stated_
- baselines: up to 370 m (460 kλ) for 340.S; 345 m (430 kλ) for 399.S  
  > "baselines up to 370 m (460 k$\lambda$)" (2 Observations and data reduction)
- angular resolution: 0.45"x0.37" (340.S), uniform weighting  
  > "Uniformly weighted synthesized beams are $0{\ensuremath{''}}45\times 0{\ensuremath{''}}37$ (340.S)" (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: 0.50 mJy/beam (340.S); 0.59 mJy/beam (399.S)  
  > "We reach noise levels of 0.50 mJy beam$^{-1}$ (340.S) and 0.59 mJy beam$^{-1}$ (399.S)." (2 Observations and data reduction)
- time on source: 5449 s (340.S); 4615 s (399.S)  
  > "a total on-source integration time of 5449 s" (2 Observations and data reduction)
- observing dates: _not stated_
- pi or archival as stated: Archival Cycle 0 data; 340.S previously presented by Qi et al. 2013  
  > "The 340.S data were previously presented by (cite: qi2013), who do not analyse the continuum emission in detail." (2 Observations and data reduction)
- Other facility **SMA**: 870 um data and model pC of Andrews et al. 2012 used for comparison  
  > "traced by 870 $\mu$m SMA observations, extend out only to $\sim 60$ au" (Introduction)
- External data: Midplane temperature profile (q0=2.6, q1=0.26, R0=7 au)  
  > "We follow the midplane temperature as calculated by Andrews et al. (2012), which reproduces the observed SED." (3 Model fitting) [from (cite: andrews2012)]
- External data: Dust opacity 3.4 cm2/g at 365.5 GHz and Sigma_10au = 0.39 g/cm2  
  > "we adopt the same value as employed by Andrews et al. (2012), $\kappa_{365.5}=3.4$ cm$^2$ g$^{-1}$ (dust)." (3 Model fitting) [from (cite: andrews2012)]
- External data: Position angle 155 deg and inclination 6 deg  
  > "Adopting a position angle for the (projected) disk’s major axis of $155^\circ$ (east of north) and an inclination of $+6^\circ$ (cite: qi2013; rosenfeld2012)" (2 Observations and data reduction) [from (cite: qi2013; rosenfeld2012)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.2.1  
  > "We use CASA 4.2.1 for the calibration." (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres, and Titan for some of 399.S  
  > "Ceres, and for some of data set 399.S, Titan, as flux calibrators" (2 Observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: Iterative self-calibration on continuum down to 60 s solution intervals  
  > "we iteratively performed self-calibration on the continuum down to solution intervals of 60 s" (2 Observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: uniform weighting  
  > "Uniformly weighted synthesized beams are $0{\ensuremath{''}}45\times 0{\ensuremath{''}}37$ (340.S)" (2 Observations and data reduction)
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
- final rms: 0.50 mJy/beam (340.S)  
  > "We reach noise levels of 0.50 mJy beam$^{-1}$ (340.S)" (2 Observations and data reduction)

### Inherited from earlier work

- Disk geometry (PA, inclination)  
  > "an inclination of $+6^\circ$ (cite: qi2013; rosenfeld2012)" (2 Observations and data reduction) [from (cite: qi2013; rosenfeld2012)]
- Deprojection equations  
  > "We use the equations of (cite: berger2007) (cite: walsh2014) to carry out the deprojection." (2 Observations and data reduction) [from (cite: berger2007) (cite: walsh2014)]
- Temperature profile, opacity and Sigma_0 from model pC  
  > "We follow the midplane temperature as calculated by Andrews et al. (2012), which reproduces the observed SED." (3 Model fitting) [from (cite: andrews2012)]

### Not stated but needed to reproduce (our reading)

- Imaging/cleaning parameters (cell, image size, masking) for Fig. 1
- Line-free channel selection and spectral windows used for continuum
- Self-calibration intermediate solints and reference antenna
- MCMC settings: number of walkers, steps, burn-in, priors
- Weighting of visibility averaging and bin centers
- Flux scale uncertainty and handling of the two datasets' flux calibration
- Details of gap-model grid (widths, depths)

## Analysis recipe

1. **Calibrate and self-calibrate continuum**: Verify calibration, iterative self-calibration down to 60 s  
  > "we iteratively performed self-calibration on the continuum down to solution intervals of 60 s" (2 Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: Second dataset 399.S used to independently confirm results  
  > "we instead prefer to use data set 399.S to independently confirm our results (as is indeed the case)" (2 Observations and data reduction)
2. **Deproject and bin visibilities**: Average real and imaginary visibilities in 41 radial bins of deprojected baseline length  
  > "we derive average continuum visibilities (real and imaginary part) in 41 10-k$\lambda$ wide radial bins of deprojected baseline length" (2 Observations and data reduction)
   - parameter: PA 155 deg, i = 6 deg  
  > "Adopting a position angle for the (projected) disk’s major axis of $155^\circ$ (east of north)" (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: Imaginary parts zero, indicating symmetric emission  
  > "The imaginary parts are all zero to within the accuracy, indicating that the emission is symmetric around the source center" (2 Observations and data reduction)
3. **Fit parametrized disk models to binned real visibilities**: Model intensity I=B(T)(1-exp(-tau)), Hankel transform by summation with 0.1 au step; single and broken power-law Sigma(R)  
  > "We solve the integral in equation ([\[e:vis\]](#e:vis)) by summation using a step size of 0.1 au, which was found to be sufficiently small." (3 Model fitting)
   - software: emcee
   - parameter: 4 or 6 free parameters; fixed Sigma_10au=0.39, kappa=3.4, q0=2.6, q1=0.26, R0=7 au  
  > "Table [1](#t:parameters) lists the fixed and 4 or 6 (depending on the model) free parameters of our model." (3 Model fitting)
   - assumption: Constant dust opacity 3.4 cm2/g; geometrically thin, vertically isothermal; cos i ~ 1  
  > "We choose to describe the optical depth $\tau(R)$ as the product of a constant dust opacity $\kappa_{365.5}$ and a radially varying dust surface density distribution $\Sigma(R)$." (3 Model fitting)
   - fitting: MCMC with emcee affine-invariant ensemble sampler, minimizing chi2 over 41 bins; sigma_i from dispersion in bins  
  > "We use the `emcee`[^1] implementation of the (MCMC) method, which uses affine invariant ensemble sampling" (3 Model fitting)
   - validation: chi2 1437 (single) vs 283 (broken); likelihood-ratio test; 399.S confirms  
  > "A likelihood-ratio test indicates that the broken power law model describes the data better than the single power law model with a probability lager than 0.999." (3 Model fitting)
4. **Constrain gaps in the disk**: Add Gaussian gap at 20 au to the two-slope model; scan widths and depths, reoptimize other parameters; exclude models with chi2 increase by factor two  
  > "We find that we can exclude, as defined by an increase of the $\chi^2$ value by a factor of two or more, models with gaps that are entirely empty with FWHM widths of more than 6.6 au" (4.2 The presence of unseen gaps)
   - parameter: Gap centered at 20 au  
  > "we include a gap centered on 20 au characterized by a Gaussian width and a depth" (4.2 The presence of unseen gaps)
   - assumption: Gap width of 5 Hill radii for planet mass conversion  
  > "Assuming a gap width of 5 Hill radii, such gaps correspond to planet masses of 0.7–10 M$_{\rm Jup}$" (4.2 The presence of unseen gaps)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.2.1: calibration and self-calibration  
  > "We use CASA 4.2.1 for the calibration." (2 Observations and data reduction)
- **emcee** : MCMC model fitting  
  > "We use the `emcee`[^1] implementation of the (MCMC) method" (3 Model fitting)
- **PyAstronomy** : made use of in the work (specific use not stated)  
  > "This work made use of PyAstronomy." (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Inner slope p0 (broken power law) | 0.53 | 0.01 | dimensionless | 3 | $p_0$ / $0.70 \pm 0.01$ / $0.53 \pm 0.01$ |
| Outer slope p1 | 8.0 | 0.1 | dimensionless | 3 | $p_1$ / / $8.0 \pm 0.1$ |
| Break radius | 47.1 | 0.2 | au | 3 | $R_{\rm break}$ (au) / / $47.1 \pm 0.2$ |
| Inner radius (broken) | 4.07 | 0.03 | au | 3 | $R_{\rm in}$ (au) / $4.44\pm 0.02$ / $4.07 \pm 0.03$ |
| Single power law p0 and Rout | p0=0.70, Rout=55.7 | 0.01, 0.1 | dimensionless, au | 3 | ($p_0=0.70\pm 0.01$ vs 0.75) and outer radius ($R_{\rm out}=55.7\pm 0.1$ au vs 60 au |
| chi2 single vs broken | 1437 vs 283 | not stated | dimensionless | 3 | with respective $\chi^2$ values of 1437 and 283 |
| T0 (broken) | 26.7 | 0.2 | K | 3 | $T_0$ (K) / $28.4\pm 0.2$ / $26.7 \pm 0.2$ |
| Optical depth | 2.1 at 4.1 au; 0.57 at 47 au | not stated | dimensionless | 3 | The optical depth drops from 2.1 at 4.1 au to 0.57 at 47 au |
| Excluded empty-gap FWHM at 20 au | >6.6 | not stated | au | 4 | models with gaps that are entirely empty with FWHM widths of more than 6.6 au |
| Integrated flux 340.S | 1.7 | not stated | Jy | 1 | Integrated fluxes of 1.7 Jy (340.S) and 1.3 Jy (399.S) are found. |

## Qualitative findings

- Broken power-law shape resembles grain growth and drift predictions, but total dust content and turn-over radius are too large for 8–10 Myr age  
  > "its total dust content and its turn-over radius are too large for TW Hya’s age of 8–10 Myr" (abstract)

## Claim tuples

- H: A single power-law surface density describes the 820 um visibilities | E: MCMC fit of single power law to 41 binned visibilities | R: Fits to 290 kλ but chi2=1437; underpredicts 300–400 kλ | F: Single power law inadequate | **refuted**
- H: A broken power law describes the surface density better | E: MCMC fit of broken power law | R: p0=0.53, p1=8.0, Rbreak=47.1 au; chi2=283 | F: Broken power law best describes data, resembling grain-drift models | **supported**
- H: Unseen gaps could be present in the disk | E: Gap models at 20 au tested against visibilities | R: Empty gaps wider than 6.6 au excluded; HL Tau-like gaps allowed | F: Planet-induced gaps may exist and trap grains | **partially**

## Reasoning

- Why this data: 820 um chosen for direct comparison to 870 um SMA data, avoiding dust emissivity degeneracy; other ALMA bands not used  
  > "because we aim to make a direct comparison to the 870 $\mu$m SMA data without the added degeneracy between dust surface density and dust emissivity as function of wavelength" (Introduction)
- Why this method: Fit binned real visibilities rather than full set to speed up calculations; no residual imaging  
  > "We fit to the 41 data points plotted in Fig. [2](#f:visplot) rather than the full set of (complex) visibilities to speed up calculations." (3 Model fitting)
- Alternative: Exponentially tapered surface density cannot fit the profile  
  > "(cite: andrews2012) already show that exponentially tapered models do not fit the millimeter continuum visibilities of TW Hya" (3 Model fitting)
- How they decided it was enough: _not stated_
- Limitation (authors): Cannot infer both surface density and opacity from single wavelength; errors are formal only  
  > "From observations at a single wavelength, we cannot infer both the dust surface density and the dust opacity as function of radius." (4.1 Dust drift)
- Caveat (inferred, ours): Fitting binned real visibilities ignores covariance and total flux; uncertainties are formal only
- Caveat (inferred, ours): Temperature profile fixed from earlier work and degenerate with optical depth
- Caveat (inferred, ours): Constant opacity assumption drives surface-density interpretation
- Caveat (inferred, ours): Summary quotes p1 uncertainty 0.2 vs 0.1 in table

## Reproducibility

- Data public (paper): Archival ALMA Cycle 0 data  
  > "The ALMA archive contains two Cycle 0 data sets with continuum observations of TW Hya near 870 $\mu$m." (2 Observations and data reduction)
- Products in archive: _not stated_
- Missing: MCMC configuration and priors
- Missing: Imaging and self-cal details
- Missing: Exact binning weights/errors
- Data volume (inferred): ~10–30 GB raw for the two Cycle 0 datasets
- Score (inferred): 3/5, Public data and a clear model with a table of parameters, but MCMC settings and calibration details are missing.
- Rediscovery candidate: yes, Data are public, model is explicit and results are numeric (slopes, break radius).

## Links

- Method: (cite: andrews2012) (Model pC, temperature profile and opacity adopted)
- Method: (cite: foreman-mackey2013) (emcee sampler)
- Companion: (cite: qi2013) (Earlier presentation of 340.S data, CO snow line)

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
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
  "facts": 73,
  "stated": 44,
  "rate": 0.603
 },
 "evidence_ok": true
}
```
