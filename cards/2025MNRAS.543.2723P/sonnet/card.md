# Observational constraints on evolution of dust disc properties in Upper Scorpius

`2025MNRAS.543.2723P` | Monthly Notices of the Royal Astronomical Society 2025 | first author: Pinilla, Paola | arXiv: 2509.19442 | DOI: 10.1093/mnras/staf1624

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: How do dust disc sizes, fluxes and structures of Upper Scorpius discs evolve compared with younger regions, and do dust evolution models with mild external photoevaporation reproduce them?  
  > "We compare the results with state-of-the art gas and dust evolution models that include external photoevaporation, with mild values of the $F_{\rm{UV}}$ of 1-40 $G_0$." (abstract)
- Target **121 dust-detected discs in Upper Scorpius (Carpenter et al. 2025 survey)**: coordinates _not stated_; z/distance average 145 pc  
  > "A total of 121 discs confirmed as members of UpperSco were detected in dust continuum emission with a signal-to-noise-ratio (SNR) $>$ 3" (2 Sample and Visibility Modelling); "($14.5\,$au at an average distance of 145 pc for the discs in UpperSco)" (2 Sample and Visibility Modelling); distance from Gaia DR3 distances (Bailer-Jones) for stellar luminosities; average 145 pc assumed  
  > "A total of 121 discs confirmed as members of UpperSco were detected in dust continuum emission with a signal-to-noise-ratio (SNR) $>$ 3" (2 Sample and Visibility Modelling); "($14.5\,$au at an average distance of 145 pc for the discs in UpperSco)" (2 Sample and Visibility Modelling)

## Data provenance

- ALMA projects: 2011.0.00526.S, 2018.1.00564.S
- bands: Band 7 (0.88 mm), continuum and CO J=3-2  
  > "observations taken with ALMA in Band 7 (0.88mm) to detect the dust continuum and the CO J=3-2" (2 Sample and Visibility Modelling)
- frequencies and spectral setup: spws centred at 334.2, 336.1, 346.2, 348.1 GHz, 1.875 GHz each  
  > "The spectral windows of these observations were centred at 334.2, 336.1, 346.2, and 348.1 GHz, with a bandwidth of 1.875 GHz for each window." (2 Sample and Visibility Modelling)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.1-0.3 arcsec  
  > "The resolution of these observations is between 0.1-0.3$^{\prime \prime}$" (2 Sample and Visibility Modelling)
- max recoverable scale: _not stated_
- sensitivity: 0.15 mJy/beam  
  > "which provides a sensitivity of the dust continuum emission of 0.15 mJy beam$^{-1}$." (2 Sample and Visibility Modelling)
- time on source: typical 2.5 minutes  
  > "with a typical on-source integration time of 2.5 minutes" (2 Sample and Visibility Modelling)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (not stated)
- Other facility **Gaia DR3**: distances for stellar luminosity  
  > "stellar luminosities are derived by scaling the 2MASS J observed photometries to the Gaia DR3 distances" (4.4)
- Other facility **2MASS**: J-band photometry for luminosities  
  > "stellar luminosities are derived by scaling the 2MASS J observed photometries to the Gaia DR3 distances" (4.4)
- External data: ALMA Band 7 UpperSco survey data, fluxes and sizes (used for unresolved disc fluxes and comparison)  
  > "for the unresolved discs we use the values from (cite: carpenter2025), as their typical uncertainties are lower." (4.1) [from (cite: carpenter2025)]
- External data: Gas disc sizes R_CO for 67 discs plus upper limits  
  > "Zagaria et al. (in prep)  measured gas disc sizes for the 78 discs in the sample of UpperSco where emission from $^{12}$CO $J=3-2$ was detected at $>5\sigma$ level." (4.3) [from Zagaria et al. (in prep)]
- External data: Lupus dust disc radii R90 for comparison  
  > "The Lupus values are calculated from (cite: guerra2025)." (Table 2) [from (cite: guerra2025)]
- External data: Effective temperatures from spectral types  
  > "the effective temperatures are obtained from spectral types from (cite: manara2020) if available, otherwise from (cite: luhman2022)" (4.4) [from (cite: manara2020); (cite: luhman2022)]
- External data: FUV fluxes F_UV per disc  
  > "We sampled from this probability to compute the distribution of the FUV flux (cite: anania2025b)." (4.3) [from (cite: anania2025b)]
- Simulation/model as data: DustPy 1.0.5 gas and dust evolution models with external photoevaporation, 0.3 and 1.0 Msun stars, F_UV = 1,10,20,40 G0, pressure bumps A = 0,1,4,50  
  > "we use the 1D code `Dustpy` (cite: stammler2022), version 1.0.5." (3.1)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Uses data from the Carpenter et al. survey; calibration not described  
  > "correspond to observations taken with ALMA in Band 7 (0.88mm) to detect the dust continuum and the CO J=3-2 (cite: carpenter2025)." (2 Sample and Visibility Modelling)
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

- Observations, calibration and imaging from the Upper Sco ALMA survey  
  > "(cite: carpenter2025)" (2 Sample and Visibility Modelling) [from (cite: carpenter2025)]
- Gas disc size method (unconvolved best-fit image-plane models)  
  > "used the method introduced in (cite: trapman2025_size), where the gas disc size is measured from unconvolved best fit models to the image." (4.3) [from (cite: trapman2025_size)]
- External photoevaporation prescription in DustPy  
  > "we follow the prescription implemented by (cite: garate2024) in `Dustpy`." (3.1) [from (cite: garate2024)]
- R_CO prescription from thermochemical models  
  > "we assume the analytical prescriptions in (cite: trapman2023)." (3.2) [from (cite: trapman2023)]

### Not stated but needed to reproduce (our reading)

- Calibration and imaging details of the visibility data (taken from Carpenter et al. 2025)
- Which measurement sets and whether continuum-only averaged visibilities were used
- uv binning and Galario setup (priors ranges, initial positions, weighting)
- Criterion for choosing point source vs Gaussian fit
- linmix settings and handling of upper limits
- Exact F_UV values per disc and the disc-star separation procedure
- Gas disc sizes from Zagaria et al. (in prep) not available

## Analysis recipe

1. **Visibility modelling of dust continuum**: Fit axisymmetric Gaussian ring/disc intensity model to visibilities with Galario; point source for unresolved discs  
  > "We assume axisymmetric discs, and an intensity radial profile described by a Gaussian function." (2 Sample and Visibility Modelling)
   - software: Galario, emcee
   - parameter: 7 free parameters (f0, sigma_r, R_peak, inc, PA, dRA, dDec); 8 walkers per parameter; 30,000 steps then final 10,000; uniform priors; 256x256 pixels of 0.02 arcsec  
  > "The number of walkers per free parameter is set to 8." (2 Sample and Visibility Modelling); "The number of steps is set to 30,000, which was found to be sufficient for parameter convergence." (2 Sample and Visibility Modelling)
   - assumption: Structured if R_peak > 0.05 arcsec, smooth otherwise; unresolved size upper limit 0.1 arcsec (14.5 au)  
  > "The former are defined as those in which the peak of the best-fitting Gaussian function is resolved ($R_{\rm peak} > 0.05^{\prime \prime}$)" (2 Sample and Visibility Modelling)
   - fitting: MCMC with emcee, uniform priors  
  > "The prior for each parameter follows a uniform distribution." (2 Sample and Visibility Modelling)
   - validation: Compared fluxes, sizes, inclinations with Carpenter et al. and Zagaria et al.  
  > "showing in general good agreements" (4.1)
2. **Disc size distributions and Lupus comparison**: Kaplan-Meier CDFs including upper limits, logrank test vs Lupus; K-S test for smooth vs structured  
  > "using the Kaplan-Meier estimator (cite: Davidson-Pilon2019). The $p-$value obtained from the `logrank` test from `lifelines`" (4.1)
   - software: lifelines
   - fitting: _not stated_
   - validation: _not stated_
3. **Size-luminosity and stellar-mass scaling relations**: Bayesian linear regression in log space with upper limits  
  > "we perform a Bayesian linear regression using `linmix` (cite: kelly2007), such that $\log(R_{90}) = \alpha + \beta \log(F_{340\rm{GHz}})$" (4.2)
   - software: linmix
   - assumption: Dust mass: optically thin, kappa=2.3 cm2/g (nu/230GHz)^0.4, T=20 K  
  > "we assume $\kappa_\nu=2.3\,$cm$^{2}$ g$^{-1}(\nu/230\,\rm{GHz})^{0.4}$ (cite: andrews2013)" (4.4)
   - fitting: linmix  
  > "we perform a Bayesian linear regression using `linmix` (cite: kelly2007), such that $\log(R_{90}) = \alpha + \beta \log(F_{340\rm{GHz}})$" (4.2 Dust disc size vs. millimetre flux)
   - validation: _not stated_
4. **Stellar masses**: Teff and L compared with Baraffe 2015 tracks; 10% error on L and Teff  
  > "the stellar luminosities and effective temperatures are then compared to an interpolated grid of (cite: baraffe2015) pre-main sequence evolutionary tracks." (4.4)
   - fitting: _not stated_
   - validation: _not stated_
5. **Gas and dust evolution models with synthetic observables**: DustPy simulations with pressure bumps and external photoevaporation; compute 340 GHz flux, R90, R_CO  
  > "The dust disc radius is defined as the location that encloses 90% of the flux ($R_{90}$)." (3.2)
   - software: DustPy
   - parameter: rc=80 au, gamma=1, Mdisc=0.05 Mstar, alpha0=1e-3, vfrag=10 m/s, 150 radial cells 1-300 au, F_UV 1,10,20,40 G0 switched on at 1 Myr  
  > "We turn-on the effect of external photoevaporation at 1 Myr of evolution" (3.1)
   - assumption: inclination 45 deg, background temperature 20 K, beam 0.1 arcsec, distance 145 pc, detection threshold 3x0.15 mJy/beam  
  > "The disc inclination is assumed to be $i=45^{\circ}$." (3.2)
   - fitting: _not stated_
   - validation: Resolution test with double the cells gave no differences  
  > "we perform resolution tests with a double number of cells, resulting in no differences on the final disc properties and evolution." (3.1)

## Software

- **Galario** : visibility modelling  
  > "We use `Galario` (cite: tazarri2018) to model the dust continuum visibilities of 121 discs" (2)
- **emcee** : MCMC sampling  
  > "as implemented in the `Python` library `emcee`" (2)
- **DustPy** 1.0.5: gas and dust evolution models  
  > "version 1.0.5" (3.1)
- **linmix** : Bayesian linear regression  
  > "using `linmix` (cite: kelly2007)" (4.2)
- **lifelines** : Kaplan-Meier and logrank tests  
  > "`logrank` test from `lifelines`" (4.1)
- **CASA** : listed in software  
  > "CASA (cite: McMullin_2007)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Structured resolved discs | 24 (~20%) | not stated | discs | 1 | we find that 24 discs ($\sim$20%) are resolved and structured |
| Smooth resolved discs | 28 (~23%) | not stated | discs | 1 | 28 ($\sim23$%) are resolved and remain smooth |
| Unresolved discs | 69 (~57%) | not stated | discs | 1 | 69 ($\sim$57%) are unresolved |
| Median R90 total | 25.4 | +10.2/-7.7 (95%) | au | 2 | Total      / $25.4^{+10.2}_{-7.7}$ |
| Median R90 smooth | 17.4 | +5.2/-4.1 | au | 2 | Smooth     / $17.4^{+5.2}_{-4.1}$ |
| Median R90 structured | 46.3 | +16.9/-15.9 | au | 2 | Structured / $46.3^{+16.9}_{-15.9}$ |
| R90-F340 slope beta | 0.72 | +0.08/-0.07 | dimensionless | 3 | $0.44^{+0.09}_{-0.10}$ / $0.72^{+0.08}_{-0.07}$ |
| Mdust-Mstar slope | 1.83 | +0.22/-0.22 | dimensionless | 3 | $1.14^{+0.15}_{-0.15}$ / $1.83^{+0.22}_{-0.22}$ |
| R90-Mstar slope | 1.69 | +0.28/-0.24 | dimensionless | 3 | $1.91^{+0.14}_{-0.13}$ / $1.69^{+0.28}_{-0.24}$ |
| Median R_CO/R90 all resolved | 2.7 | +0.3/-0.4 | dimensionless | 3 | The median value of the $R_{\rm{CO}}$/$R_{90}$ ratio for all the resolved discs is $2.7^{+0.3}_{-0.4}$. |

## Qualitative findings

- Structured discs are larger than smooth discs; no significant R90 evolution between Lupus and UpperSco; no correlation of dust properties with F_UV  
  > "we observe no significant correlation between dust disc properties and the environmental $F_{\rm{UV}}$" (abstract)

## Claim tuples

- H: Dust disc size evolves between Lupus and UpperSco | E: Compare R90 CDFs with Kaplan-Meier and logrank test | R: p-values above 1% in all cases | F: No significant dust size evolution | **supported**
- H: Size-luminosity relation is steeper than reported and consistent with drift | E: linmix fit of R90 vs F340 | R: slope 0.72 | F: Steep strong correlation, similar to Lupus | **supported**
- H: Environmental F_UV affects dust disc properties | E: Correlate R90, R_CO/R90, flux with F_UV and compare to models | R: no correlation | F: Dust shaped by drift and traps rather than mild F_UV | **supported**
- H: Smooth and structured discs differ in gas-to-dust size ratio | E: logrank on R_CO/R90 | R: 4.1 vs 2.3, p much lower than 1% | F: Significantly different | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Visibility-plane modelling gives better constraints than images at the ~0.1 arcsec resolution  
  > "The analysis is performed in the visibility domain to derive dust disc fluxes, sizes, and inclinations." (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Single Gaussian may miss faint rings, gaps, asymmetries, small cavities  
  > "with this approach we may still miss some structures as faint rings/gaps, azimuthal asymmetries, or small cavities." (2)
- Limitation (authors): Dust shielding by entrained wind not included in models  
  > "This potential shielding is not included in our models" (5.1)
- Caveat (inferred, ours): Point-source fits can wander to noise peaks
- Caveat (inferred, ours): Models use fixed single parameters, not a population synthesis
- Caveat (inferred, ours): Fixed inclination and 20 K temperature assumptions
- Caveat (inferred, ours): Gas sizes from unpublished work

## Reproducibility

- Data public (paper): Non-calibrated ALMA data public; derived tables on Zenodo  
  > "The non-calibrated ALMA data is publicly available at <https://almascience.nrao.edu/aq/>" (Data availability)
- Products in archive: _not stated_
- Code: not stated for analysis code; data and models on request, tables on Zenodo  
  > "The data from observations and models underlying this article will be shared on request to the corresponding author." (Data availability)
- Missing: Calibration/imaging from Carpenter et al. 2025
- Missing: Zagaria et al. gas sizes
- Missing: Galario fit configuration details
- Data volume (inferred): Moderate; ~hundreds of GB raw for three projects, visibilities for 121 sources
- Score (inferred): 3/5, Public data and clear fitting recipe, but calibration inherited and some inputs unpublished.
- Rediscovery candidate: yes, Public archival data, stated visibility fitting recipe and numeric results (R90 medians, slopes).

## Links

- Method: (cite: tazarri2018) (Galario visibility modelling)
- Method: (cite: trapman2025_size) (gas disc size method)
- Companion: (cite: carpenter2025) (source ALMA UpperSco survey)
- Companion: Zagaria et al. (in prep) (gas disc sizes and F_UV)
- Related: AGE-PRO

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00395.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 47,
  "rate": 0.553
 },
 "evidence_ok": true
}
```
