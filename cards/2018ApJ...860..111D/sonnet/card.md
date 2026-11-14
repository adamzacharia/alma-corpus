# Similar Scaling Relations for the Gas Content of Galaxies Across Environments to z ∼ 3.5

`2018ApJ...860..111D` | The Astrophysical Journal 2018 | first author: Darvish, Behnam | arXiv: 1805.10291 | DOI: 10.3847/1538-4357/aac836

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: high_z_galaxies, nearby_galaxies
- Question: Given fixed z, M*, and sSFR/sSFR_MS, does the local environment affect the molecular gas content of galaxies in the local universe and at higher redshift?  
  > "Given fixed $z$, $M_{*}$, and sSFR/sSFR$_{MS}$, does the local environment affect the molecular gas content of galaxies in the local universe and at higher redshift?" (Introduction)
- Target **COSMOS field star-forming galaxies from Scoville et al. 2017 (708 galaxies)**: coordinates _not stated_; z/distance z ≈ 0.3-4.5 (used z ≈ 0.5-3.5)  
  > "a sample of 708 galaxies at $z$ $\approx$ 0.3-4.5 in the COSMOS field" (2.1 High Redshift); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00097.S, 2012.1.00076.S, 2012.1.00523.S, 2013.1.00034.S, 2013.1.00111.S, 2015.1.00137.S, 2013.1.00118.S, 2013.1.00151.S
- bands: Band 6 and 7 RJ dust continuum  
  > "rely on the RJ dust-continuum emission in ALMA bands 6 and 7" (2.1 High Redshift)
- frequencies and spectral setup: _not stated_
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
- Other facility **ALFALFA HI survey**: HI masses for local sample, converted to H2  
  > "The local universe sample is from the ALFALFA HI survey (cite: Haynes11) matched with the SDSS DR12" (2.2 Local Universe)
- Other facility **SDSS DR12 / MPA-JHU**: Local stellar masses, SFRs, density  
  > "Stellar masses and SFRs are from the MPA-JHU DR8 catalog (cite: Kauffmann03)." (2.2 Local Universe)
- External data: ALMA-derived M_ISM for 708 COSMOS galaxies  
  > "The parent sample is from (cite: Scoville17), based on ALMA observations of the long-wavelength dust continuum" (2.1 High Redshift) [from (cite: Scoville17)]
- External data: Stellar masses from SED fitting  
  > "Stellar masses are based on spectral energy distribution (SED) template fitting using optical to infrared bands (cite: Laigle16)." (2.1 High Redshift) [from (cite: Laigle16)]
- External data: Stellar mass function for star-forming galaxies  
  > "we use the stellar mass function of (cite: Ilbert13) for star-forming galaxies at $z$=0.2-4.0." (5.5) [from (cite: Ilbert13)]
- External data: High-z density field  
  > "We use the slightly modified density field estimation of (cite: Darvish17) in the COSMOS field." (3.1 High Redshift) [from (cite: Darvish17)]

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

- M_ISM estimation from RJ dust continuum  
  > "(see (cite: Scoville14; Scoville17) for details)" (2.1 High Redshift) [from (cite: Scoville14; Scoville17)]
- Local density estimates  
  > "We use the density measurements of (cite: Darvish18) based on the SDSS DR12" (3.2 Local Universe) [from (cite: Darvish18)]

### Not stated but needed to reproduce (our reading)

- Scoville17 ALMA flux measurements and M_ISM catalog values
- MCMC priors, chain length and likelihood
- K-S test implementation details
- Photo-z slice widths used for density field

## Analysis recipe

1. **assign density quantiles**: Adaptive kernel smoothing density (high-z); 10th nearest neighbor (local); four quantile bins  
  > "We define four density bins using the projected surface density quantiles from the low- to high-density regions" (3.1 High Redshift)
   - fitting: _not stated_
   - validation: _not stated_
2. **build control samples**: Match each δ4 galaxy to lower-density galaxies within ±0.2 dex M*, ±0.2 dex sSFR/sSFR_MS, ±0.2 z (±0.005 local)  
  > "within $\pm$ 0.2 dex of $M_{*}$, $\pm$ 0.2 dex of sSFR/sSFR$_{MS}$, and $\pm$ 0.2 ($\pm$0.005 for the local sample) of redshift" (4 Control Sample Selection)
   - fitting: _not stated_
   - validation: K-S tests p>0.1  
  > "High K-S p-values (p $>$ 0.1) in all cases guarantee a good control sample selection." (4 Control Sample Selection)
3. **fit scaling relations of M_ISM and SFR**: Power-law fit in z, sSFR/sSFR_MS, M*, overdensity  
  > "we use both a multidimensional nonlinear Levenberg-Marquardt (LM) least-squares algorithm and a Monte Carlo Markov chain (MCMC) Bayesian approach (Metropolis-Hastings sampling)" (5.1)
   - assumption: alpha_CO=6.5; Chabrier IMF; flat LCDM H0=70, Om=0.3  
  > "a CO-to-H$_{2}$ conversion factor of $\alpha_{CO}$=6.5 $M_{\odot}$ (K kms$^{-1}$pc$^{2}$)$^{-1}$ (cite: Scoville14)" (Introduction)
   - fitting: LM and Metropolis-Hastings MCMC, with observational uncertainties included  
  > "The observational uncertainties of $M_{ISM}$, sSFR/sSFR$_{MS}$, and $M_{*}$ are taken into account." (5.1)
   - validation: LM and MCMC consistent  
  > "The LM and MCMC methods both yield consistent results." (5.1)
4. **molecular mass density per environment**: rho = (1/4)(1/f_V) ∫ M_ISM(z,M*) Φ(M*) dM* over 10^10-10^12 Msun  
  > "The integral is performed at $M_{*}$=10$^{10}$ to 10$^{12}$ $M_{\odot}$" (5.5)
   - assumption: sSFR/sSFR_MS=1, passive galaxies excluded  
  > "we assume (sSFR/sSFR$_{MS}$)=1 in Equation [\[eqn:2\]](#eqn:2) when estimating $\rho$." (5.5)
   - fitting: _not stated_
   - validation: Compared with VIPERS and ORELSE mass functions  
  > "coincide with the midpoint of our measurement (between $\delta{1}$ and $\delta_{4}$)" (5.5)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| M_ISM power-law index on overdensity (MCMC) | 0.03 | +0.01/-0.01 | dimensionless | 3 | $M_{ISM}$ $\propto$ $\Delta^{0.03^{+0.01}_{-0.01}}$ |
| SFR power-law index on overdensity (MCMC) | 0.004 | +0.007/-0.005 | dimensionless | 3 | $\Delta^{0.004^{+0.007}_{-0.005}}$ |
| <M_ISM> densest bin, <z>~1.8 | 1.6 | 0.2 | 1e11 Msun | 2 | $\langle M_{ISM}\rangle$=(1.6$\pm$0.2)$\times$10$^{11}$ $M_{\odot}$ |
| <f_gas> densest bin, <z>~1.8 | 55% | 2% | percent | 2 | $\langle$f$_{gas}\rangle$=55$\pm$2% |
| <tau> densest bin, <z>~1.8 | 0.8 | 0.1 | Gyr | 2 | $\langle \tau \rangle$=0.8$\pm$0.1 Gyr |
| rho in delta4 at z=0.65 | 338.0 | +109.0/-104.2 | 1e6 Msun Mpc^-3 | 4 | 338.0$_{-104.2}^{+109.0} \times$10$^{6}$ $M_{\odot}$Mpc$^{-3}$ |

## Qualitative findings

- No environmental dependence of M_ISM, f_gas, tau to z~3.5; rho peak shifts to lower z in densest bins  
  > "This differential evolution of $\rho$ across environments is likely due to the growth of the large-scale structure with cosmic time." (abstract)

## Claim tuples

- H: Local environment affects molecular gas content at fixed z, M*, sSFR/sSFR_MS | E: Control-matched density quantiles plus multivariable power-law fits | R: M_ISM ∝ Δ^0.03; K-S p>0.1 between bins | F: Gas content is driven by internal processes, not environment | **supported**
- H: Cosmic molecular mass density evolves differently across environments | E: Volume-weighted rho per quantile | R: Peak at z~1-2 in lowest bins, z<1 in densest | F: Due to large-scale structure growth | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Stellar mass distributions differ between density bins, so control-sample results should be treated with caution  
  > "Nonetheless, the presented results using stellar mass controlled samples should be considered with caution." (A)
- Caveat (inferred, ours): Dust-continuum M_ISM assumes fixed alpha_CO and dust-to-gas calibrations, with little sensitivity to environment
- Caveat (inferred, ours): Photo-z density uncertainties blur environments at high z
- Caveat (inferred, ours): Little dynamic range in extreme cluster cores

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Scoville17 M_ISM catalog
- Missing: Density field catalogs of Darvish17/18
- Missing: Fitting priors and MCMC settings
- Data volume (inferred): Small if using catalog products; raw ALMA data not needed.
- Score (inferred): 3/5, Catalog-level analysis with clear matching recipe but dependent on external catalogs and unspecified fit settings.
- Rediscovery candidate: no, Relies on catalogs from other papers; fit details missing.

## Links

- Method: (cite: Scoville14) (RJ dust continuum calibration)
- Method: (cite: Darvish17) (High-z density field)
- Companion: (cite: Scoville17) (Parent ALMA sample and M_ISM)
- Related: COSMOS
- Related: ALFALFA

## Checks

```json
{
 "quotes": 40,
 "quotes_ok": 40,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 8,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 23,
  "rate": 0.343
 },
 "evidence_ok": true
}
```
