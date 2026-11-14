# Survey of Orion Disks with ALMA (SODA): III. Disks in wide binary systems in L1641 and L1647

`2025A&A...695A.257R` | Astronomy and Astrophysics 2025 | first author: Ricciardi, G. | arXiv: 2409.11485 | DOI: 10.1051/0004-6361/202452287

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: star_formation, protoplanetary_disks
- Question: How does stellar multiplicity at wide separations (>=1000 AU) affect dust masses of Class II disks in L1641 and L1647, and is there a separation threshold in the flux-separation correlation?  
  > "The goal of this work is to comprehensively characterize the impact of stellar multiplicity on Class II disks in the L1641 and L1647 regions of Orion A ($\sim$ 1-3 Myr), part of the Survey of Orion Disks with ALMA (SODA)." (abstract)
- Target **Class II disks in multiple systems in L1641 and L1647 (Orion A)**: coordinates _not stated_; z/distance 380-455 pc (per-disk distances from Paper I)  
  > "Given the average distance of Orion A between 388 pc and 414 pc (cite: Grosschedl18_3D)" (Sample characterization); distance from Paper I (van Terwisga et al. 2022)  
  > "Given the average distance of Orion A between 388 pc and 414 pc (cite: Grosschedl18_3D)" (Sample characterization)

## Data provenance

- ALMA projects: 2019.1.01813.S
- bands: _not stated_
- frequencies and spectral setup: 225 GHz continuum  
  > "The sample of 873 protoplanetary disks was observed with ALMA at 225 GHz, with a median rms of 1.5 M$_{\oplus}$" (Sample characterization)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1.1"  
  > "a typical synthesized beam FWHM of $\sim$1.1$^{''}$" (Sample characterization)
- max recoverable scale: _not stated_
- sensitivity: median rms 1.5 M_earth (0.08 mJy/beam)  
  > "with a median rms of 1.5 M$_{\oplus}$ (or 0.08 mJy beam$^{-1}$)" (Sample characterization)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **ESO-VISTA (VISION)**: NIR catalog used to identify multiple systems  
  > "we search in the VISION catalog (cite: VisionCatalogue19) for the nearest Class II neighbor to each Class II source" (Multiple systems association)
- Other facility **Hubble Space Telescope (Kounkel16)**: 7 closer binaries (100-1000 AU)  
  > "our analyses include 7 new closer binaries, with separations between 100 and 1000 AU, resolved by (cite: Kounkel16)" (Disk dust mass)
- Other facility **Spitzer**: YSO classification (Megeath catalogs)  
  > "3479 sources have been classified as Class II objects (dusty YSOs)" (Sample characterization)
- External data: Lupus, Taurus multiple system fluxes and separations  
  > "considering the multiple sample in Lupus (cite: Zurlo21; Ansdell18), Taurus (cite: Akeson19; Manara19; Akeson14; Harris_2012)" (4.1 Flux-Separation correlation) [from Zurlo21; Ansdell18; Akeson19; Manara19; Akeson14; Harris_2012]
- External data: Stellar masses from IN-SYNC  
  > "from the Sloan Digital Sky Survey (SDSS) APOGEE INfrared Spectroscopy of Young Nebulous Clusters program (IN-SYNC) of the Orion A molecular cloud (cite: DaRio)" (4.3) [from DaRio]

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

- Disk dust mass procedure, kappa=2.3 cm2/g, T_dust=20 K, distances  
  > "We estimate the disk masses based on their ALMA continuum using the same procedure presented in paper I (cite: van_Terwisga_2022)." (3.1 Disk dust mass) [from van Terwisga et al. 2022 (cite: van_Terwisga_2022)]
- Inside-out multiplicity search and Bayesian association probability  
  > "we employ the iterative inside-out search method presented by (cite: Tobin_2022)." (2.2) [from Tobin et al. 2022 (cite: Tobin_2022)]

### Not stated but needed to reproduce (our reading)

- ALMA reduction and imaging details and flux measurements (from SODA Paper I)
- Per-disk fluxes and upper limits table
- UltraNest priors, likelihood and settings
- How fluxes of the systems were summed for fits
- Constant subtracted for log-rank test

## Analysis recipe

1. **Identify multiple systems**: Iterative inside-out KNN search from 1000 to 10^4 AU in VISION catalog, around SODA Class II sources  
  > "we iteratively search for companions with an increasing separation up to 10$^4$ AU." (2.2)
   - parameter: probability threshold P>0.9; 10 neighbors for surface density  
  > "including in our final catalog only the ones that pass the threshold value of 0.9" (2.3)
   - assumption: NIR catalog complete for Class II sources, P(D|C,I)=1  
  > "We assume the NIR catalog is complete for Class II sources and thus $P(D|C,I)$ = 1." (2.3)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive disk dust masses**: Optically thin M=F d^2/(k B(T))  
  > "We assume that the continuum millimeter flux is optically thin." (3.1)
   - parameter: kappa=2.3 cm2/g, T=20 K  
  > "we consider the constant values of $k_{\nu}$=2.3 $cm^2~g^{-1}$ and $T_{dust,eff}$=20 $K$" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit flux-separation relation**: Linear and broken (linear+constant) fits with nested sampling, compared by Bayes factor  
  > "we perform an additional fit to the combined observations, including a separation threshold beyond which we assume a constant system dust mass." (4.1)
   - software: UltraNest
   - fitting: UltraNest nested sampling; upper limits as constraints on parameter space  
  > "Specifically for our case upper limits are treated as constraints on the parameter space." (4.1)
   - validation: Bayes factor from log Z  
  > "Therefore, $BF=exp(log~Z_2 - log~Z_1)~>~1$" (4.1)
4. **Compare mass distributions**: Kaplan-Meier estimator and log-rank tests; bootstrap with J-band matched single disks (10^4 times)  
  > "We repeated this procedure 10$^4$ times to generate a bootstrap distribution of p-values." (4.3)
   - software: lifelines
   - fitting: _not stated_
   - validation: bootstrap p-value distribution  
  > "We repeated this procedure 10$^4$ times to generate a bootstrap distribution of p-values." (4.3 Mass distribution in Orion A: separate system components)

## Software

- **UltraNest** : nested sampling fits of flux-separation  
  > "The plots are obtained using the `UltraNest`[^3] package by (cite: Buchner16)" (4.1)
- **lifelines** v0.23.9: Kaplan-Meier estimator and log-rank test  
  > "This work uses the implementation of this estimator in the `lifelines` package" (4.2)
- **Linmix** : Zagaria21 regression shown for reference  
  > "performed using the hierarchical Bayes model `Linmix`" (4.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Sample size | 61 binaries, 3 triples, 1 quadruple | not stated | systems | 1 | Our final catalog counts 61 binary systems, 3 triple systems, and 1 quadruple system |
| Separation threshold | 127 | 4 | AU | 3 | we identify a threshold separation x$_{edge}$ = 127 $\pm$ 4 AU |
| log Z linear vs broken fit | -20.831 vs -18.333 | 0.101 / 0.109 | dimensionless | 3 | -18.333$^{+0.109}_{-0.109}$ |
| Median dust mass primary / secondary disks | 3.23 / 3.88 | +0.6/-0.4 ; +-0.3 | M_earth | 4 | median mass of 3.23$^{+0.6}_{-0.4}$ M$_{\oplus}$ for primary disks and 3.88$^{+0.3}_{-0.3}$ M$_{\oplus}$ for secondary disks |

## Qualitative findings

- Disk mass distributions of Lupus, Taurus and Orion A multiples are indistinguishable; Upper Sco differs  
  > "the cumulative distributions for Lupus, Taurus, and Orion A are not statistically distinguishable." (4.2)

## Claim tuples

- H: A separation threshold exists beyond which flux-separation correlation is lost | E: Linear vs broken fits to Lupus+Taurus+Orion multiples | R: x_edge=127±4 AU, broken model favored | F: Systems before and after threshold form via different processes | **supported**
- H: Disks in wide binaries differ from single disks | E: Bootstrap log-rank tests with J-matched singles | R: median p ~0.07 (primary), 0.16 (secondary) | F: No significant difference at 10^3-10^4 AU | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Optically thin and constant opacity assumptions give unquantifiable uncertainty; dust masses may be underestimated  
  > "the assumptions of optically thin emission and constant opacity introduce an unquantifiable source of uncertainty." (3.1)
- Caveat (inferred, ours): Threshold sensitive to heterogeneous samples and wavelengths across regions
- Caveat (inferred, ours): Chance alignment contamination not testable without kinematics
- Caveat (inferred, ours): Primary defined by NIR brightness, not mass

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Fit priors and likelihood
- Missing: Per-disk fluxes table
- Missing: Compilation of Lupus/Taurus data
- Data volume (inferred): small (published SODA catalog; ~tens of GB if reimaging)
- Score (inferred): 5/5, Catalogs and methods mostly specified, but fit details and ALMA fluxes come from other papers.
- Rediscovery candidate: no, Depends on external catalogs and unspecified fit priors.

## Links

- Method: Tobin et al. 2022 (cite: Tobin_2022) (inside-out search and association probability)
- Companion: van Terwisga et al. 2022 (cite: vanTerwisga22) (SODA Paper I, ALMA data and dust masses)
- Related: SODA
- Related: VISION
- Related: IN-SYNC

## Checks

```json
{
 "quotes": 36,
 "quotes_ok": 36,
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
  "facts": 70,
  "stated": 28,
  "rate": 0.4
 },
 "evidence_ok": true
}
```
