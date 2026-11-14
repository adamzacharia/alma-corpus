# Compact Disks in a High-resolution ALMA Survey of Dust Structures in the Taurus Molecular Cloud

`2019ApJ...882...49L` | The Astrophysical Journal 2019 | first author: Long, Feng | arXiv: 1906.10809 | DOI: 10.3847/1538-4357/ab2d2d

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the dust substructures and sizes of a representative, unbiased sample of Taurus disks at ~0.12" resolution, and how do compact smooth disks compare to ring disks?  
  > "This survey was designed with sufficient resolution and depth to provide a snapshot of substructures of mm-sized grains in a large number of disks." (1 Introduction)
- Target **32 Taurus protoplanetary disks (e.g. CI Tau, DL Tau, MWC 480, RY Tau, BP Tau, HQ Tau)**: coordinates per-source 2MASS IDs and fitted centers in Tables 1 and 3  
  > "The distance for individual star is adopted from the Gaia DR2 parallax (cite: gaia2018)." (Table 1); z/distance ~127-197 pc (individual Gaia DR2 distances)  
  > "The distance for individual star is adopted from the Gaia DR2 parallax (cite: gaia2018)." (Table 1); distance from Gaia DR2 (RY Tau: 128±4 pc from Taurus neighbors)  
  > "The distance for individual star is adopted from the Gaia DR2 parallax (cite: gaia2018)." (Table 1)

## Data provenance

- ALMA projects: 2016.1.01164.S
- bands: Band 6 (1.3 mm), average 225.5 GHz  
  > "The Band 6 receivers were used for all measurements with identical spectral window (SPW) setup." (2.3 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: two SPWs at 218 and 233 GHz, each 1.875 GHz wide  
  > "The continuum emission was recorded in two SPWs, which centered at 218 and 233 GHz, each with a bandwidth of 1.875 GHz." (2.3 Observations)
- arrays: _not stated_
- configurations: C40-7  
  > "We adopted the C40-7 antenna configuration to achieve the desired spatial resolution of $\sim 0.\ensuremath{''}1$." (2.3 Observations)
- baselines: 21-3638 m or 21-3697 m  
  > "| 2017/08/18 | 43 | 21-3638 | 0.5 |" (Table 2)
- angular resolution: typical beam 0.14"x0.11"  
  > "Our final continuum images have a typical beam size of $0.\ensuremath{''}14\times0.\ensuremath{''}11$" (2.3 Observations)
- max recoverable scale: _not stated_
- sensitivity: median continuum rms 50 uJy/beam  
  > "a median continuum rms of 50 $\mu$Jy beam$^{-1}$" (2.3 Observations)
- time on source: ~4 min per source for bright group; ~8-9 min per source for others  
  > "The other three groups, with mostly faint disks ($<50$ mJy, with exceptions for a few bright disks for observing efficiency), were observed for $\sim 8-9$ min per source." (2.3 Observations)
- observing dates: 2017 August 18, 27, 31 and September 2  
  > "| 2017/09/02 | 45 | 21-3697 | 1.3 |" (Table 2)
- pi or archival as stated: PI Herczeg, program 2016.1.01164.S  
  > "Our ALMA observations were conducted as program 2016.1.01164.S (PI: Herczeg) in 2017 August–September." (2.3 Observations)
- Line: 13CO and C18O J=2-1 (not stated)
- Other facility **Gaia DR2**: parallax distances  
  > "The distance for individual star is adopted from the Gaia DR2 parallax (cite: gaia2018)." (Table 1)
- Other facility **ESPaDOnS (CADC archive)**: coadded spectra to derive RY Tau Teff  
  > "we downloaded (from the CADC archive) and coadded 96 high-resolution ESPaDOnS spectra (cite: Donati06) of RY Tau" (8 RY Tau)
- External data: Spectral types and extinctions  
  > "Spectral type is adopted from (cite: herczeg2014)" (Table 1) [from (cite: herczeg2014)]
- External data: Multiple-disk fit results for binary systems  
  > "For multiple stellar systems (see Table [1](#tab:source_prop)), the fitting results are adopted from the companion paper of Manara et al. (submitted)" (3.2 Modeling Results) [from Manara et al. (submitted)]
- External data: Dynamical stellar masses for UZ Tau E, DQ Tau, HN Tau A  
  > "We adopt the stellar dynamical mass measurements from the CO gas rotation for the two spectroscopic binaries (UZ Tau E, (cite: simon00) and DQ Tau, (cite: czekala2016))" (2.2 Host star properties) [from (cite: simon00); (cite: czekala2016); (cite: simon2017)]
- External data: 0.88 mm SMA disk radii for comparison  
  > "For the 11 disks in our sample with $R_{\rm eff,68\%}$ measured by (cite: tripathi2017) with SMA observations at 0.88 mm" (3.3 Fluxes and Sizes) [from (cite: tripathi2017)]

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline with ALMA-staff scripts  
  > "Data reduction started with the standard ALMA pipeline calibration, with scripts provided by ALMA staff." (2.3 Observations)
- casa version: CASA 4.7.2 (first group), 5.1.1 (later three)  
  > "This calibration procedure was performed with CASA v4.7.2 for the first observing group (2017/08/18) and v5.1.1 for the later three groups." (2.3 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Performed except GK Tau and HQ Tau, following Long et al. 2018  
  > "Self-calibration were performed for our targets, except for the faint GK Tau and HQ Tau, with procedures elaborated in (cite: long2018)." (2.3 Observations)

### Imaging

- task: tclean  
  > "We then created continuum image for each target using *tclean* with Briggs weighting and a robust parameter of +0.5." (2.3 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = +0.5  
  > "We then created continuum image for each target using *tclean* with Briggs weighting and a robust parameter of +0.5." (2.3 Observations)
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
- final beam: typical 0.14"x0.11"  
  > "Our final continuum images have a typical beam size of $0.\ensuremath{''}14\times0.\ensuremath{''}11$" (2.3 Observations)
- final rms: median 50 uJy/beam  
  > "a median continuum rms of 50 $\mu$Jy beam$^{-1}$" (2.3 Observations)

### Inherited from earlier work

- Self-calibration procedure  
  > "with procedures elaborated in (cite: long2018)" (2.3 Observations) [from (cite: long2018)]
- Visibility-plane disk modeling procedure  
  > "we follow the similar disk modeling procedure in the visibility plane as presented in (cite: long2018)" (3 Disk Modeling in the visibility plane) [from (cite: long2018)]
- Flux and size derivation from best-fit profiles  
  > "the disk mm flux densities and dust disk sizes are derived as in (cite: long2018)" (3.3 Fluxes and Sizes) [from (cite: long2018)]
- Stellar mass/age from evolutionary tracks  
  > "models of pre-main sequence stellar evolution, as in (cite: pascucci2016)" (2.2 Host star properties) [from (cite: pascucci2016)]

### Not stated but needed to reproduce (our reading)

- MCMC priors and parameter bounds, and the likelihood form
- Self-calibration solution intervals and number of rounds (deferred to Long et al. 2018)
- Image size, cell size, masking and clean threshold
- Which SPWs were used for continuum and any line flagging
- Binary-system fit results from Manara et al. (submitted)
- Flux calibrator names and flux scale uncertainty (only 10% assumed in regression)

## Analysis recipe

1. **Calibrate and self-calibrate**: ALMA pipeline calibration, WVR phase adjustments, check-source phase transfer for one group, then self-calibration  
  > "Following the pipeline, initial phase adjustments were made based on the water vapor radiometer measurements." (2.3 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Image peak SNR increased by ~30% for most disks  
  > "image peak signal-to-noise ratio (SNR) for most disks increased by $\sim 30\%$" (2.3 Observations)
2. **Fit disk model in visibility plane**: Exponentially tapered power law I(R)=A(R/Rc)^-g1 exp[-(R/Rc)^g2], Fourier transformed with Galario, compared to visibilities with MCMC  
  > "We therefore adopt an exponentially tapered power law ($I(R)=A(R/R_{c})^{-\gamma_{1}}\exp[-(R/R_{c})^{\gamma_{2}}]$) as the model intensity profile" (3.1 Modeling Procedure)
   - software: Galario, emcee
   - parameter: 100 walkers, 5000 steps, burn-in <1000, posterior from last 1000 steps  
  > "The parameters are explored with 100 walkers and 5000 steps" (3.1 Modeling Procedure)
   - fitting: emcee MCMC; medians with 16th-84th percentiles scaled by sqrt(reduced chi2)  
  > "The quoted uncertainties are the interval from the 16th to the 84th percentile of the model chains and scaled by the square root of the reduced $\chi^2$ of the fit." (Table 3)
   - validation: Residual images, visibility profiles and radial cuts; separate fits to different SPW sets  
  > "The quality of the best-fit model is checked by inspecting the comparisons of data and model in images, visibility profiles, and radial intensity cuts" (3.2 Modeling Results)
3. **Derive fluxes and effective radii**: Integrate best-fit profile; radius enclosing 68% and 95% of flux  
  > "The dust disk size is defined here as the radius that encircles some fraction of the total flux, calculated for 68% and 95%" (3.3 Fluxes and Sizes)
   - fitting: _not stated_
   - validation: Fluxes consistent with pre-ALMA measurements within 10-15% systematics  
  > "are broadly consistent with pre-ALMA flux measurements (cite: andrews2013), if taking into account a 10–15% systematic uncertainty." (3.3 Fluxes and Sizes)
4. **Compare subsamples**: Two-sample KS tests on stellar mass, luminosity, age  
  > "By performing the two-sample KS test using ks_2samp task in PYTHON SCIPY package" (4.2.1 Comparison of stellar masses)
   - software: scipy
   - assumption: L_mm = F_nu (d/140)^2  
  > "$L_{\rm mm} = F_\nu(d/140)^2$" (4.2.2 Comparison of disk continuum luminosities)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit size-luminosity relation**: Bayesian linear regression with Linmix in log-log plane including both-axis uncertainties and 10% flux uncertainty  
  > "we employ the Bayesian linear regression method of (cite: kelly2007) with its python package *Linmix*" (5.3 Disk size–luminosity relationship)
   - software: Linmix
   - fitting: Linmix (Kelly 2007)  
  > "we employ the Bayesian linear regression method of (cite: kelly2007) with its python package *Linmix*[^1] to determine the correlation, considering uncertainties on both axes" (Disk size–luminosity relationship)
   - validation: _not stated_

## Software

- **CASA** 4.7.2, 5.1.1: calibration and tclean imaging  
  > "CASA (v4.7.2, v5.1.1; (cite: McMullin2007))" (Software)
- **Galario** : Fourier transform of model profile to visibilities  
  > "We then apply the *Galario* code (cite: tazzari2018) to Fourier transform the model intensity profile into visibilities" (3.1 Modeling Procedure)
- **emcee** : MCMC fitting  
  > "The model visibilities are later compared with data visibilities using *emcee* package (cite: Foreman-Mackey2013)." (3.1 Modeling Procedure)
- **Linmix** : Bayesian linear regression  
  > "Bayesian linear regression method of (cite: kelly2007) with its python package *Linmix*" (5.3 Disk size–luminosity relationship)
- **scipy** : ks_2samp KS tests  
  > "using ks_2samp task in PYTHON SCIPY package" (4.2.1 Comparison of stellar masses)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Size-luminosity relation | log R_eff = (2.15±0.15) + (0.42±0.11) log L_mm | ±0.15, ±0.11 | dimensionless | 5 | log$R_{\rm eff}$ = (2.15$\pm$0.15) + (0.42$\pm$0.11)log$L_{\rm mm}$ |
| Slope using R_eff,68% | 0.34 | ±0.11 | dimensionless | 5 | we find a slightly flatter slope (0.34$\pm$0.11) when using $R_{\rm eff,68\%}$ |
| Median gamma1 of smooth disks | 0.56 | std 0.26 | dimensionless | 2 | with the median $\gamma_{1}$ value of 0.56 and a standard deviation of 0.26 |
| KS p-value stellar mass, substructures vs smooth | 94% | not stated | dimensionless | 4 | indistinguishable from that of the smooth disks ($p=94\%$ |
| Disks with substructures | 12 of 32 | not stated | disks | 2 | Our 1.3 mm continuum maps reveal 12 disks with prominent dust gaps and rings |
| Smooth disk R_eff,95% upper limit | ≲50-55 au | not stated | au | 3 | the smooth disk sample all have radii $\lesssim 55$ au |
| Parameter repeatability between SPW fits | incl/PA ~1-2 deg, radii ~3%, fluxes 5% | not stated | mixed | 2 | the inclinations and position angles have a precision of $\sim 1-2$ deg, and the effective radii are precise to $\sim 3$%, fluxes to 5% |

## Qualitative findings

- All disks with R_eff,95% ≥55 au show substructures; compact smooth disks resemble inner cores of ring disks.  
  > "In contrast, all disks with $R_{\rm eff,95\%}$ of at least 55 au in our sample show detectable substructures." (abstract)

## Claim tuples

- H: Do smooth and substructured disks differ in stellar or disk properties? | E: KS tests of stellar mass, age and luminosity across subsamples | R: Mass, age and luminosity are similar to smooth disks in singles; radii differ | F: Dust disk size is the main distinguishing property | **supported**
- H: Inner cores of ring disks resemble compact smooth disks | E: Compare Rc, gamma1, gamma2 and peak brightness | R: Parameters fall within smooth disk ranges | F: The difference is outer rings | **supported**
- H: Size-luminosity relation holds and indicates optically thick compact disks | E: Linmix regression of R_eff,95% vs L_mm | R: slope 0.42±0.11, consistent with L∝R^2 | F: Some compact disks optically thick | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Tapered power law chosen because visibility real part oscillations suggest sharp outer edge  
  > "which likely indicates a disk with a sharp outer edge in millimeter dust grains" (3.1 Modeling Procedure)
- Alternative: Gaussian profile fits worse than tapered power law except for GK Tau  
  > "For all disks, the exponentially tapered power law fits better than the Gaussian profile, except for the faint and compact GK Tau" (3.2 Modeling Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Fit uncertainties are statistical and likely underestimated  
  > "These uncertainties correspond to statistical uncertainties and are likely underestimated." (3.3 Best-fit profile parameters)
- Limitation (authors): Individual stellar ages are unreliable; masses likely underestimated  
  > "the age of any individual star is unreliable." (2.2 Host star properties)
- Caveat (inferred, ours): Substructure classification is resolution-limited (~15 au beam) and binary results depend on an unpublished companion paper
- Caveat (inferred, ours): Stellar masses from tracks are biased low
- Caveat (inferred, ours): Selection excludes already-observed bright disks

## Reproducibility

- Data public (paper): Program code given; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: 2016.1.01164.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Self-calibration parameters (in Long et al. 2018)
- Missing: MCMC priors/likelihood details
- Missing: Binary disk fits from Manara et al.
- Data volume (inferred): ~100-300 GB raw for 4 execution blocks; Band 6 continuum plus line SPWs
- Score (inferred): 3/5, Data and software are identified and fit setup is partly described, but self-calibration, priors and binary fits are deferred to other papers.
- Rediscovery candidate: no, Recipe depends on inherited self-cal and modeling details and companion-paper fits; priors missing.

## Links

- Method: (cite: long2018) (Self-calibration and visibility modeling procedure)
- Method: (cite: tazzari2018) (Galario code)
- Companion: Manara et al. (submitted) (Fits of binary systems)
- Companion: (cite: lodato2019) (Hidden planet population from gaps)
- Companion: (cite: liu2019) (MWC 480 ring)
- Related: DSHARP
- Related: Ophiuchus survey (Cieza 2019)

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
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
  "facts": 79,
  "stated": 53,
  "rate": 0.671
 },
 "evidence_ok": true
}
```
