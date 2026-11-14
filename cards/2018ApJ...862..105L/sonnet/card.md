# The Core Mass Function across Galactic Environments. II. Infrared Dark Cloud Clumps

`2018ApJ...862..105L` | The Astrophysical Journal 2018 | first author: Liu, Mengyao | arXiv: 1806.02213 | DOI: 10.3847/1538-4357/aacb7c

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: What is the core mass function in IRDC clumps, and does it differ from the Salpeter IMF and from the more evolved G286 protocluster?  
  > "We also make a direct comparison of these IRDC clump CMF results to those measured in the more evolved protocluster G286 derived with similar methods" (abstract)
- Target **32 IRDC clumps in seven IRDCs (A-H)**: coordinates Galactic l,b per core in Table 1 (l~18.8-35.5 deg)  
  > "The distances to the sources, based on near kinematic distance estimates, range from 2.4 kpc to 5.7 kpc." (1 Introduction); z/distance 2.4 to 5.7 kpc  
  > "The distances to the sources, based on near kinematic distance estimates, range from 2.4 kpc to 5.7 kpc." (1 Introduction); distance from near kinematic distance estimates  
  > "The distances to the sources, based on near kinematic distance estimates, range from 2.4 kpc to 5.7 kpc." (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.00806.S
- bands: 1.3 mm continuum, continuum band centred at 231.55 GHz  
  > "The spectral set-up included a continuum band centered at 231.55 GHz (LSRK frame) with width 1.875 GHz" (2.1 Observational Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12 m array only, 29 antennas; no ACA  
  > "No ACA observations were performed." (2.1 Observational Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: ~11 arcsec  
  > "the largest recoverable scale for the array is $\sim 11\ensuremath{''}$" (2.1 Observational Data)
- sensitivity: 1 sigma ~0.2 mJy in ~1.36x0.82 arcsec beam  
  > "The continuum image reaches a 1$\sigma$ rms noise of $\sim$0.2 mJy in a synthesized beam of $\sim$ 1.36$\ensuremath{''}$ $\times$ 0.82$\ensuremath{''}$." (2.1 Observational Data)
- time on source: ~2-3 min per pointing, 30 pointings; total 2.4 hr incl. calibration  
  > "The actual on-source time is $\sim$2-3 min for each pointing (30 pointings in total)." (2.1 Observational Data)
- observing dates: 04-Jan-2015, 10-Apr-2015, 23-Apr-2015  
  > "which observed 32 IRDC clumps on 04-Jan-2015, 10-Apr-2015 and 23-Apr-2015" (2.1 Observational Data)
- pi or archival as stated: Project PI Tan; data mostly presented by Kong et al. (2017)  
  > "These data have mostly been presented by Kong et al. (2017)" (2.1 Observational Data)
- Other facility **BGPS**: Single-dish 1.1 mm data used to estimate ALMA flux recovery  
  > "we use the archival data from the Bolocam Galactic Plane Survey (BGPS) (Aguirre et al. 2011; Ginsburg et al. 2013)" (2.1 Observational Data)
- External data: Dust opacity 0.899 cm2/g (moderately coagulated thin ice mantle model)  
  > "moderately coagulated thin ice mantle model of Ossenkopf & Henning 1994" (2.3 Core Mass Estimation) [from Ossenkopf & Henning 1994]
- External data: Gas-to-refractory-dust ratio of 141  
  > "using a gas-to-refractory-component-dust ratio of 141 (Draine 2011)" (2.3 Core Mass Estimation) [from Draine 2011]
- External data: G286 CMF results for comparison  
  > "Paper I also presented results for 1.0$''$ resolution and with a noise level of 0.45 mJy beam$^{-1}$" (3.3 Comparison to G286) [from Cheng et al. 2018 (Paper I)]

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
- final beam: ~1.36'' x 0.82''  
  > "synthesized beam of $\sim$ 1.36$\ensuremath{''}$ $\times$ 0.82$\ensuremath{''}$" (2.1 Observational Data)
- final rms: ~0.2 mJy/beam (0.6 for C9)  
  > "except for C9 where $\sigma = 0.6\:{\rm mJy \ beam}^{-1}$ due to its large dynamic range" (2.2 Core Identification)

### Inherited from earlier work

- Dendrogram parameters (4 sigma trunk, +1 sigma branch, min area half beam)  
  > "The parameters associated with these three choices are the same as the fiducial choices of Paper I." (2.2 Core Identification) [from Cheng et al. 2018 (Paper I)]
- Mass estimation assumptions  
  > "following the same assumptions adopted in Paper I" (2.3 Core Mass Estimation) [from Paper I]
- Flux and number completeness correction method and mass binning  
  > "Following Paper I, we estimate two correction factors needed to estimate a “true” CMF from a “raw” observed CMF." (2.4 Core Flux Recovery and Completeness Corrections) [from Paper I]

### Not stated but needed to reproduce (our reading)

- Calibration and imaging details (CASA version, weighting, robust, tclean settings, cell and image size) not given
- Dust temperature adopted is implied 20 K fiducial but only via the formula
- How 4 sigma threshold images were produced from the archive products
- Exact binning and fitting code for CMF power law
- Mass-dependent f_flux and f_num curves are only shown in figures

## Analysis recipe

1. **Measure flux recovery vs BGPS**: Compare ALMA flux above 3 sigma and BGPS flux in 27'' aperture, scaling BGPS to 231.6 GHz  
  > "then convert the BGPS flux density measurements at 267.8 GHz to the mean ALMA frequency of 231.6 GHz via $S_{\nu} \propto \nu ^{\alpha_\nu}$ assuming $\alpha_\nu = 3.5 \pm 0.5$" (2.1 Observational Data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify cores**: astrodendro on images before primary-beam correction; leaves are cores; within primary beam FWHM; clumpfind as alternative  
  > "we will adopt the dendrogram (Rosolowsky et al. 2008) method as implemented in the astrodendro python package" (2.2 Core Identification)
   - software: astrodendro, clumpfind
   - parameter: trunk 4 sigma, branch +1 sigma, min leaf area 0.5 beam  
  > "Finally, we set a minimum area of half the synthesized beam size for a leaf structure to be identified." (2.2 Core Identification)
   - fitting: _not stated_
   - validation: Compared with clumpfind  
  > "we find 120 cores with masses from 0.150 to $286\:M_{\odot}$" (3.2 Core Mass Function)
3. **Estimate core masses**: Optically thin dust emission, Sigma_mm formula  
  > "We estimate core masses by assuming optically thin thermal emission from dust" (2.3 Core Mass Estimation)
   - assumption: Td=20 K, kappa_1.3mm,d=0.899 cm2/g, gas-to-dust 141  
  > "If temperatures of 15 K or 30 K were to be adopted, then the mass estimates would differ by factors of 1.48 and 0.604, respectively." (2.3 Core Mass Estimation)
   - fitting: _not stated_
   - validation: Temperature sensitivity factors given  
  > "If temperatures of 15 K or 30 K were to be adopted, then the mass estimates would differ by factors of 1.48 and 0.604, respectively." (2.3 Core Mass Estimation)
4. **Derive completeness corrections**: Insert artificial Gaussian cores (3 at a time, 50 repeats, 150 experiments per mass) over 10^-1 to 10^1.2 Msun, rerun dendrogram  
  > "with three sources being inserted at a given time at random locations within the primary beam and this exercise repeated 50 times" (2.4 Core Flux Recovery and Completeness Corrections)
   - software: astrodendro
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit CMF power law and compare**: Least-squares in log dN/dlogM with Poisson errors, and MLE (Newman 2005), five bins per dex; KS tests vs Salpeter and G286  
  > "We also apply a maximum likelihood estimation (MLE) method to estimate the power law index (Newman et al. 2005)." (3.2 Core Mass Function)
   - fitting: Synthetic core populations drawn uniformly in bins, 50 repeats, median alpha  
  > "We repeat this for 50 times and then derive the median $\alpha$ and confidence interval $\sigma$." (3.2 Core Mass Function)
   - validation: KS tests; clumpfind comparison  
  > "We find that the median $p$ value, which indicates the probability that these distributions are consistent with the same parent distribution, is $\lesssim 10^{-4}$." (3.2 Core Mass Function)

## Software

- **astrodendro** : core identification  
  > "as implemented in the astrodendro[^1] python package" (2.2 Core Identification)
- **clumpfind** : alternative core identification  
  > "we will also consider the effects of using the clumpfind algorithm (Williams et al. 1994)" (2.2 Core Identification)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of cores | 107 | not stated | cores | 2 | Overall we have identified 107 cores in these images. |
| Median flux recovery fraction vs BGPS | 0.19 | 0.02 | dimensionless | 1 | we derive a median flux recovery fraction of 0.19 $\pm$ 0.02 |
| Combined true CMF alpha, M>=0.79 Msun (simple) | 0.86 | 0.11 | dimensionless | 5 | power law indices for $M>0.79\:M_\odot$ of $\alpha=0.50\pm0.10$, $0.49\pm0.09$ and $0.86\pm0.11$, respectively |
| Combined true CMF alpha, M>=1.26 Msun (simple) | 0.70 | 0.13 | dimensionless | 5 | then we derive $\alpha=0.70\pm0.13$ for the true CMF |
| MLE alpha, M>=1.26 Msun | 0.83 | 0.09 | dimensionless | 5 | The MLE analysis yields $\alpha=0.83\pm0.09$. |
| KS p-value IRDC vs G286 (M>=0.79 / >=1.26) | 0.42 / 0.23 | not stated | dimensionless | 5 | the KS test yields $p=0.23$ |
| Core mass range | 0.261 to 178 | not stated | Msun | 3 | The masses range from $0.261 M_{\odot}$ to $178\:M_{\odot}$ |

## Qualitative findings

- Most large-scale emission is resolved out, so dendrogram and clumpfind give similar results  
  > "the resulting core properties are not that sensitive to whether dendrogram or clumpfind is used as the identification algorithm" (3.2 Core Mass Function)

## Claim tuples

- H: IRDC clump CMF is consistent with Salpeter | E: Power-law fits and KS test vs Salpeter | R: alpha 0.70-0.86; KS p<~1e-4 | F: CMF is top-heavy relative to Salpeter | **supported**
- H: IRDC clump CMF differs from G286 CMF | E: Compare dendrogram CMFs, KS test with 12m-only G286 | R: alpha 0.70 vs 1.08 (M>=1.26); p=0.23 | F: Only a hint of variation; larger samples needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Same methods as Paper I for direct comparison  
  > "Most importantly, we use the same methods as our previous study of the more evolved protocluster G286.21+0.17" (1 Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Errors on number-corrected CMF likely underestimate true uncertainties; no 7m data; temperature/opacity uncertainties  
  > "they likely underestimate the true uncertainties" (3.2 Core Mass Function)
- Caveat (inferred, ours): Single fixed 20 K temperature for all cores
- Caveat (inferred, ours): Sample small and mix of distances
- Caveat (inferred, ours): Completeness for lowest bin uncertain, driven by cloud D

## Reproducibility

- Data public (paper): ALMA data cited by project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00806.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Calibration/imaging parameters
- Missing: Core catalog is in Table 1 but completeness curves only in figures
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Public data and clear analysis recipe with a core table, but imaging steps and some parameters are inherited or unstated.
- Rediscovery candidate: yes, Public data, explicit dendrogram parameters, numeric CMF indices.

## Links

- Method: Rosolowsky et al. 2008 (dendrogram algorithm)
- Companion: Cheng et al. 2018 (Paper I) (G286 CMF with same methods)
- Companion: Kong et al. 2017 (presents same ALMA data (N2D+ etc.))
- Related: BGPS

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
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
  "facts": 71,
  "stated": 37,
  "rate": 0.521
 },
 "evidence_ok": true
}
```
