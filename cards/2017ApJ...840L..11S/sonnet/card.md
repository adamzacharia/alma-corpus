# Extreme CO Isotopic Abundances in the ULIRG IRAS 13120-5453: An Extremely Young Starburst or Top-heavy Initial Mass Function

`2017ApJ...840L..11S` | The Astrophysical Journal Letters 2017 | first author: Sliwa, Kazimierz | arXiv: 1704.06671 | DOI: 10.3847/2041-8213/aa6ea4

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, astrochemistry
- Question: What causes the extreme 12CO/13CO and 13CO/C18O line ratios in the ULIRG IRAS 13120-5453, and what do the isotopic abundances imply for starburst age or the IMF?  
  > "The abundances within the central 500 pc are consistent with enrichment of the ISM via a young starburst ($<$7Myr), a top-heavy initial mass function or a combination of both." (abstract)
- Target **IRAS 13120-5453**: coordinates _not stated_; z/distance D_L = 144 Mpc  
  > "is a nearby ULIRG (D$_{\rm{L}}$ = 144 Mpc)" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00306.S, 2013.1.00379.S
- bands: Bands 3, 7 and 9, Cycle 2  
  > "ALMA was used to observe IRAS 13120-5453 in Cycle 2 using Bands 3, 7 and 9" (Observations and Line Ratios)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.58x0.35 (12CO 1-0), 0.39x0.29 (3-2), 0.25x0.16 (6-5), 0.55x0.41 arcsec (13CO, C18O)  
  > "| Resolution (arcsec) | 0.58 $\times$ 0.35 | 0.39 $\times$ 0.29 | 0.25$\times$ 0.16 | 0.55 $\times$ 0.41 | 0.55 $\times$ 0.41 |" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: rms 1.5, 1.1, 16 mJy/beam (20 km/s) for 12CO 1-0, 3-2, 6-5; 0.3 mJy/beam (35 km/s) for 13CO and C18O  
  > "| rms (mJy beam$^{-1}$) | 1.5 (20 km s$^{-1}$) | 1.1 (20 km s$^{-1}$) | 16 (20 km s$^{-1}$) | 0.3 (35 km s$^{-1}$) | 0.3 (35 km s$^{-1}$) |" (Table 1)
- time on source: Integration time 652, 867, 1567, 3117, 3117 s  
  > "| Integration Time (s) | 652 | 867 | 1567 | 3117 | 3117 |" (Table 1)
- observing dates: 2015 June 7 to July 22  
  > "| Obs Data | 2015 July 03 | 2015 June 07 | 2015 June 09 | 2015 July 22 | 2015 July 22 |" (Table 1)
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (not stated)
- Line: 12CO J=3-2 (not stated)
- Line: 12CO J=6-5 (not stated)
- Line: 13CO J=1-0 (not stated)
- Line: C18O J=1-0 (not stated)
- External data: Nucleosynthesis yields for core-collapse supernovae  
  > "Using the nucleosynthesis yield calculations for core-collapse supernovae (CCSNe) of (cite: Nomoto2006)" (Root of the Extreme Abundances) [from (cite: Nomoto2006)]
- External data: Starburst region size of 0.5 kpc  
  > "The region lacking emission is within the starburst region (0.5 kpc) measured by (cite: Privon2017)." (Observations and Line Ratios) [from (cite: Privon2017)]

## Processing

### Calibration

- pipeline or manual: Manual calibration in CASA with standard steps  
  > "We calibrated all datasets manually in CASA v4.5.3 (cite: McMullin2007) using standard calibration steps." (Observations and Line Ratios)
- casa version: CASA v4.5.3  
  > "We calibrated all datasets manually in CASA v4.5.3" (Observations and Line Ratios)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Two iterations of phase-only self-calibration on 12CO datasets  
  > "We implemented two iterations of phase-only self calibration on the $^{12}$CO datasets" (Observations and Line Ratios)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.5  
  > "We CLEAN the datacubes using a Briggs robust weighting of 0.5 down to 1$\sigma$ level" (Observations and Line Ratios)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: CPROPS masking routine; channels with masked emission included down to 1.5 sigma  
  > "Integrated intensity maps were created using the CPROPs (cite: Rosolowsky2006) masking routine" (Observations and Line Ratios)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: All maps primary beam corrected  
  > "All maps were primary beam corrected" (Observations and Line Ratios)
- array combination: _not stated_
- smoothing: J=1-0 maps matched to 0.60x0.45 arcsec  
  > "We match the $^{12}$CO, $^{13}$CO and C$^{18}$O $J$=1$-$0 maps to an angular resolution of 0.60$''$ $\times$ 0.45$''$." (Observations and Line Ratios)
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- Rest frequencies and spectral setups
- Self-calibration solution intervals
- Image sizes and cell sizes
- Continuum subtraction and line-free channels
- Flux calibrator choice per dataset
- Exact CPROPS parameters
- RADEX grid and priors for the Bayesian fit
- Number of channels for the integrated maps

## Analysis recipe

1. **Image cubes and integrated intensity maps**: CLEAN cubes, CPROPS-masked moment maps, primary beam correction  
  > "Integrated intensity maps were created using the CPROPs (cite: Rosolowsky2006) masking routine" (Observations and Line Ratios)
   - software: CASA, CPROPS
   - parameter: Briggs robust 0.5; channel widths 20 or 35 km/s  
  > "with channels widths of 20 or 35 km s$^{-1}$" (Observations and Line Ratios)
   - fitting: _not stated_
   - validation: Band 3 observations have similar uv-coverage, supporting the morphological differences  
  > "The Band 3 observations, observed 19 days apart, have similar $uv$-coverage adding confidence" (Observations and Line Ratios)
2. **Line ratio maps**: Match J=1-0 maps to common resolution, cut below 2 sigma, convert to K km/s, form R10, Y10, Z10  
  > "We then create line ratio maps by cutting emission below 2$\sigma$ in each map" (Observations and Line Ratios)
   - fitting: _not stated_
   - validation: _not stated_
3. **Constrain molecular gas conditions**: Non-LTE RADEX with Bayesian likelihood on 12CO lines in central ~400 pc  
  > "We use the non-LTE code RADEX (cite: vanderTak2007) and a Bayesian likelihood code (cite: Kamenetzky2012)" (Root of the Extreme Abundances)
   - software: RADEX
   - parameter: 12CO J=1-0 Gaussian FWHM = 375 km/s  
  > "We fit the $^{12}$CO $J$=1$-$0 line with a Gaussian profile of FWHM=375 km s$^{-1}$." (Root of the Extreme Abundances)
   - fitting: Bayesian likelihood (Kamenetzky et al. 2012 code); priors not stated  
  > "We use the non-LTE code RADEX (cite: vanderTak2007) and a Bayesian likelihood code (cite: Kamenetzky2012) to constrain the molecular gas physical conditions" (Root of the Extreme Abundances)
   - validation: _not stated_
4. **Test mechanisms and enrichment**: Compare ratios with photodissociation, fractionation, infall and CCSN yield (Nomoto 2006) with Kroupa vs flat IMF  
  > "Using the nucleosynthesis yield calculations for core-collapse supernovae (CCSNe) of (cite: Nomoto2006)" (Root of the Extreme Abundances)
   - assumption: LTE, 13CO and C18O optically thin, total star-forming molecular mass 10^9 Msun, Z=0.02  
  > "assuming a total star-forming molecular mass of 10$^{9}$$M_{\odot}$ and an initial metallicity of Z=0.02" (Root of the Extreme Abundances)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.3: Calibration and imaging  
  > "We calibrated all datasets manually in CASA v4.5.3" (Observations and Line Ratios)
- **CPROPS** : Masking for integrated intensity maps  
  > "Integrated intensity maps were created using the CPROPs (cite: Rosolowsky2006) masking routine" (Observations and Line Ratios)
- **RADEX** : Non-LTE modelling of 12CO  
  > "We use the non-LTE code RADEX (cite: vanderTak2007)" (Root of the Extreme Abundances)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| R10 range | ~10 to over 250 | not stated | dimensionless | 2 | The R$_{10}$ line ratio shows a wide range of values from $\sim$10 to over 250. |
| Y10 range | 0.2 to over 4 | not stated | dimensionless | 2 | The Y$_{10}$ line ratio ranges from 0.2 to over 4. |
| Z10 range | ~20-140 | not stated | dimensionless | 2 | The Z$_{10}$ values range from $\sim$ 20-140 |
| Tkin | 130 | +400/-77 | K | 3 | $T_{\rm{kin}}$ = 130$^{+400}_{-77}$ K |
| log n(H2) | 4.2 | +2.4/-0.0 | cm^-3 | 3 | log($n_{\rm{H_{2}}}$) = 4.2$^{+2.4}_{-0.0}$ cm$^{-3}$ |
| log M(H2) | 7.8 | +1.0/-0.1 | log Msun | 3 | log(M(H$_{2}$)/$M_{\odot}$) = 7.8$^{+1.0}_{-0.1}$ |
| [12CO]/[13CO] after 6 Myr | ~575 | not stated | dimensionless | 4 | the \[$^{12}$CO\]/\[$^{13}$CO\] value of the ejected material after 6Myr will be $\sim$575 |
| [12CO]/[13CO] flat IMF | 270 | not stated | dimensionless | 4 | a flat, top-heavy IMF ($\phi_{\rm{m}}$$\propto$m$^{0}$) will produce a \[$^{12}$CO\]/\[$^{13}$CO\] abundance of 270 |

## Qualitative findings

- 13CO shows a hole in emission toward the center while C18O is relatively strong there  
  > "*Interestingly, the C$^{18}$O emission is relatively strong where there is no $^{13}$CO emission*." (Observations and Line Ratios)

## Claim tuples

- H: Are 13CO and C18O abundances in the center anomalous? | E: Line ratio maps assuming optically thin isotopologues | R: Y10 < 1 in the center, R10 and Z10 >> 1 | F: C18O is more abundant than 13CO in the central region | **supported**
- H: Which mechanism drives the ratios? | E: Evaluated photodissociation, fractionation, infall and nucleosynthesis | R: Only nucleosynthesis fits | F: Young starburst (<7 Myr), top-heavy IMF or both | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Photodissociation, fractionation and infalling gas ruled out as dominant mechanisms  
  > "we can rule out selective photo-dissociation as the dominant mechanism" (Root of the Extreme Abundances)
- How they decided it was enough: _not stated_
- Limitation (authors): C18O may be contaminated by HNCO up to 30%, not corrected  
  > "the maximum contamination is likely 30$\%$ determined from the peak of the HNCO" (Observations and Line Ratios)
- Limitation (authors): Starburst age and IMF degenerate  
  > "Future work into the star formation history of IRAS 13120-5453 is required to clarify the starburst-age/IMF degeneracy." (Root of the Extreme Abundances)
- Caveat (inferred, ours): Optically thin assumption and LTE untested by radiative transfer for 13CO and C18O
- Caveat (inferred, ours): Flat IMF is arbitrary
- Caveat (inferred, ours): Yields depend on one set of models with assumed mass and metallicity
- Caveat (inferred, ours): HNCO contamination not modelled

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust
- Missing: RADEX grid and priors
- Missing: Details of the yield-IMF integration
- Data volume (inferred): ~50-100 GB raw for five datasets
- Score (inferred): 3/5, Public ALMA data and a short recipe, but key imaging and modelling details are missing.
- Rediscovery candidate: no, Recipe incomplete for the modelling, and some results are modelling-dependent.

## Links

- Method: (cite: Rosolowsky2006) (CPROPS masking)
- Method: (cite: Kamenetzky2012) (Bayesian likelihood code with RADEX)
- Companion: (cite: Privon2017) (ALMA HCN/HCO+ of the same target)

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 32,
  "rate": 0.478
 },
 "evidence_ok": true
}
```
