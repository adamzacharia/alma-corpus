# Homogeneous Analysis of the Dust Morphology of Transition Disks Observed with ALMA: Investigating Dust Trapping and the Origin of the Cavities

`2018ApJ...859...32P` | The Astrophysical Journal 2018 | first author: Pinilla, P. | arXiv: 1804.07301 | DOI: 10.3847/1538-4357/aabf94

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: What are the cavity sizes, ring shapes and dust masses of 29 transition disks analysed homogeneously in the visibility plane, and what do they imply for dust trapping and the origin of the cavities?  
  > "We perform the analysis in the visibility plane to characterize the total flux, cavity size, and shape of the ring-like structure." (abstract)
- Target **29 transition disks (Lupus, Upper Sco, Cha I, Taurus, Oph and isolated), e.g. HD 135344B, SR 21, DoAr 44, V892 Tau**: coordinates given per target in Table 1  
  > "HD 135344B | 156 | 346.3 | 62.73" (Table 2); z/distance assumed distances 108-325 pc (Table 2)  
  > "HD 135344B | 156 | 346.3 | 62.73" (Table 2); distance from Gaia where observed, otherwise literature (not detailed)  
  > "HD 135344B | 156 | 346.3 | 62.73" (Table 2)

## Data provenance

- ALMA projects: 2013.1.00498.S, 2012.1.00182.S, 2013.1.00220.S, 2013.1.00395.S, 2013.1.00437.S, 2012.1.00158.S, 2011.0.00724.S, 2013.1.00091.S, 2013.1.00663.S, 2013.1.00658.S, 2015.1.00934.S, 2013.1.00157.S, 2011.1.00863.S
- bands: Band 7 (~0.87 mm) or Band 6 (~1.3 mm); Band 9 for LkCa 15 and RXJ1615  
  > "we analyze all disks in a similar wavelength (Band 7, i.e. $\sim0.87$ mm; or Band 6, i.e. $\sim1.3$ mm), to trace similar grain size." (3 Observations and Sample of TDs)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~20-40 au average; beams 0.12-1.0 arcsec (Table 1)  
  > "observed from Cycle 0 to Cycle 3 (i.e. from 2012 to 2016) with an average resolution of $\sim20-40$ au" (1 Introduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Mostly data from PIs/co-Is after self-calibration; T Cha as delivered from archive  
  > "Otherwise, the data is taken as delivered from the ALMA archive, and there is no additional self-calibration performed (only one disk, T Cha)." (3 Observations and Sample of TDs)
- Other facility **Gaia**: Updated distances for targets observed with Gaia  
  > "We update the distance of the targets that have been observed with Gaia" (3 Observations and Sample of TDs)
- External data: Stellar masses via evolutionary tracks method  
  > "employing the method described in (cite: pascucci2016), which uses the evolutionary tracks from (cite: baraffe2015) and (cite: feiden2016)" (3 Observations and Sample of TDs) [from (cite: pascucci2016)]
- External data: Accretion rates from literature (last column Table 1)  
  > "the corresponding citations for the accretion rates are in the last column of Table" (3 Observations and Sample of TDs) [from (cite: alcala2017); (cite: alcala2014); (cite: manara2014); (cite: fairlamb2015)]
- External data: Comparison M_dust-M_star fits in other regions  
  > "with the values reported in (cite: pascucci2016), who performed the fit assuming for all the cases a constant temperature of 20 K" (5.1) [from (cite: pascucci2016); (cite: ansdell2017)]
- Simulation/model as data: Dust evolution models with 1 MJup planet (1 Msun, 0.01 Msun disk, planet at 20 au, alpha=1e-3, ~1 Myr)  
  > "The standard model assumes a disk around one Solar mass, with a disk mass of 0.01 $M_\odot$, and one Jupiter planet at 20 au." (5.2)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% flux calibration uncertainty adopted  
  > "we include 10% of uncertainty from flux calibration for every source" (5.1)
- self calibration: Self-calibrated data from PIs; no extra self-cal for T Cha  
  > "the final measurement sets after self calibration were obtained from the principle investigator or co-investigators" (3 Observations and Sample of TDs)

### Imaging

- task: CASA clean; uvmodelfit and fixvis for center/PA/inclination  
  > "The center reported in Table 1 is used to fix the visibilities using `fixvis` in CASA" (3 Observations and Sample of TDs)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We used natural weighting for imaging (cite: pinilla2018), to obtain as high sensitivity as possible." (3 Observations and Sample of TDs)
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

- Asymmetric Gaussian ring profile and MCMC procedure  
  > "The fitting is performed using the Markov chain Monte Carlo (MCMC) method, and we used *emcee* (cite: foreman2013), and follow the same procedure as in (cite: pinilla2017)." (4) [from (cite: pinilla2017)]
- Dust opacity kappa and mass formula  
  > "which we assume to be $\kappa_\nu=2.3\,$cm$^{2}$ g$^{-1}\times(\nu/230\,\rm{GHz})^{0.4}$ (cite: andrews2013)" (5.1) [from (cite: andrews2013)]
- Opacities via Mie theory with silicate mix  
  > "calculated for each grain size as in (cite: pinilla2015c)-that is, assuming Mie theory" (5.2) [from (cite: pinilla2015c)]

### Not stated but needed to reproduce (our reading)

- Which archival datasets were obtained privately from PIs (self-calibrated MS not public)
- CASA version and uvmodelfit settings per target
- Visibility binning and uv-range used in fits
- Likelihood form and weighting of visibilities
- Which targets use only short baselines for centre fit
- Spectral windows/continuum channels used

## Analysis recipe

1. **Determine centre, PA, inclination**: uvmodelfit with Gaussian or disk model; fixvis; deproject visibilities  
  > "found by fitting the data using `uvmodelfit` in CASA, assuming a Gaussian and a disk model." (3)
   - software: CASA
   - fitting: _not stated_
   - validation: Tests with free centre/PA/inclination gave similar results  
  > "These tests provided similar results as using a priori `uvmodelfit` and `fixvis`." (3)
2. **Fit ring model to real visibilities**: Asymmetric Gaussian ring Hankel-transformed with J0; fit r_peak, sigma_int, sigma_ext, F_total  
  > "We explored four free parameters ($r_{\rm{peak}}$, $\sigma_{\rm{int}}$, $\sigma_{\rm{ext}}$, and $F_{\rm{total}}$) with 200 walkers and 1000 steps in each case" (4)
   - software: emcee, GALARIO
   - parameter: radial grid 0-500 au in 0.5 au steps; last 700 steps used  
  > "we take the last 700 steps to obtain the posterior distributions" (4)
   - fitting: emcee, uniform priors: r_peak 1-150 au, sigma 1-100 au, F 0-2 Jy  
  > "We adopted a set of uniform prior probability distributions for the free parameters explored by the Markov chain" (4)
   - validation: GALARIO fits for three targets agree; residuals around zero  
  > "These tests gave similar results in all three cases, providing confidence about the accuracy of our procedure." (4)
3. **Dust masses and M_dust-M_star fit**: Optically thin mass with T=20 K; linear fit in log-log with MCMC  
  > "for which we assume 20 K in all cases" (5.1)
   - assumption: kappa=2.3 cm2/g (nu/230GHz)^0.4, T=20 K  
  > "for which we assume 20 K in all cases" (5.1)
   - fitting: MCMC linear fit including 10% flux uncertainty  
  > "using an MCMC fit that takes into account the uncertainties of the data" (5.1)
   - validation: Checked temperature scaling with L*; trends similar  
  > "we found that in general the trends remain similar" (5.1)
4. **Optical depth at ring peak**: tau=-ln[1-Tb/Tphys] with Tphys=20 K  
  > "assuming a physical temperature of 20 K for all targets" (5.1)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare with dust-trapping models and correlations**: Dust evolution models with planet gap, intensity profiles at 870 micron convolved with 20 au beam; correlate r_peak, widths with stellar/disk parameters  
  > "We also convolved the intensity profile with a 20 au Gaussian beam" (5.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : imaging, uvmodelfit, fixvis  
  > "CASA (cite: mcmullin2007), GALARIO (cite: tazzari2018), emcee (cite: foreman2013)" (Software)
- **emcee** : MCMC visibility fits  
  > "we used *emcee* (cite: foreman2013)" (4)
- **GALARIO** : cross-check fits with free geometry  
  > "using the publicly available code GALARIO (cite: tazzari2018)" (4)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| M_dust-M_star slope beta | 0.72 | +0.08/-0.08 | dimensionless | 3 | we obtained $\beta=0.72^{+0.08}_{-0.08}$ and $\alpha=1.85^{+0.03}_{-0.03}$ |
| M_dust-M_star intercept alpha | 1.85 | +0.03/-0.03 | log10 Earth masses | 3 | we obtained $\beta=0.72^{+0.08}_{-0.08}$ and $\alpha=1.85^{+0.03}_{-0.03}$ |
| HD 135344B r_peak | 62.73 | +0.10/-0.10 | au | 2 | HD 135344B / 156 / 346.3 / 62.73$^{+0.10}_{-0.10}$ |
| tau_peak range | ~0.2-1.0 in most cases; >1 for four targets | not stated | dimensionless | 4 | ($\tau_{\rm{peak}}\sim$ 0.2-1.0) in most cases and optically thick $\tau_{\rm{peak}}>1$ for four targets |

## Qualitative findings

- No TDs with large cavities (>~45 au) around stars <~0.4 Msun  
  > "there are not TDs with large cavities ($\gtrsim$45 au) around low mass stars ($\lesssim$0.4 $M_\odot$)" (5.3)

## Claim tuples

- H: Are TDs a more evolved disk set (steeper Mdust-Mstar)? | E: Fit Mdust-Mstar for 26 TDs vs other regions | R: beta=0.72, flatter than other regions | F: Cavities open in high-mass disks; flat relation due to optical thickness and/or trapping | **supported**
- H: Photoevaporation is leading cavity mechanism | E: Compare cavity size vs accretion rate with photoevaporation predictions | R: No small cavities with low accretion rates | F: Photoevaporation excluded as leading mechanism | **supported**
- H: Model correlations of cavity/ring shape with stellar/disk parameters are detectable | E: Convolved model intensity with 20 au beam; compare observed correlations | R: Models indistinguishable; no clear correlations | F: Higher resolution needed | **supported**

## Reasoning

- Why this data: Use previously published medium-resolution data for a homogeneous sample  
  > "we prefer to use the data that has already been published to create a homogeneous sample at medium resolution" (3)
- Why this method: _not stated_
- Alternative: Disks with multiple rings or strong asymmetries excluded; ρOph 38, RXJ1615, DM Tau not fitted  
  > "we only keep TDs with a cavity and a single ring of emission" (4)
- How they decided it was enough: _not stated_
- Limitation (authors): Resolution biased toward large cavities; only real part fitted assuming axisymmetry  
  > "the resolution of the observations in our sample is bias toward resolving large cavities" (Conclusions)
- Caveat (inferred, ours): Single 20 K temperature for all disks biases masses
- Caveat (inferred, ours): Gaussian ring shape and r_peak as cavity size model-dependent
- Caveat (inferred, ours): Heterogeneous distances and stellar masses affect correlations
- Caveat (inferred, ours): Small sample, no significance tests for correlations

## Reproducibility

- Data public (paper): Data from ALMA project codes; many from PIs after self-cal  
  > "the final measurement sets after self calibration were obtained from the principle investigator or co-investigators" (3)
- Products in archive: _not stated_
- Missing: Self-calibrated measurement sets from PIs
- Missing: CASA version
- Missing: Exact visibility binning/likelihood
- Data volume (inferred): ~100-500 GB for ~15 projects
- Score (inferred): 3/5, Method well described (emcee, priors, model) but self-calibrated inputs and several details missing.
- Rediscovery candidate: no, Self-calibrated inputs not all public and details unstated, though results are numeric.

## Links

- Method: (cite: pinilla2017) (Asymmetric Gaussian ring model and MCMC procedure)
- Method: (cite: tazzari2018) (GALARIO visibility fitting)
- Companion: (cite: pascucci2016) (Mdust-Mstar comparison and stellar mass method)
- Related: Lupus ALMA survey
- Related: Upper Sco ALMA survey
- Related: Chamaeleon I survey

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 13,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.1.00863.S"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00526.S",
  "2011.0.00863.S",
  "2013.1.01020.S"
 ],
 "codes_printed_but_missing": [
  "2011.0.00966.S"
 ],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 39,
  "rate": 0.527
 },
 "evidence_ok": true
}
```
