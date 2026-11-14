# ALMAGAL: V. Relations between the core populations and the parent clump physical properties

`2026A&A...705A.100E` | Astronomy and Astrophysics 2026 | first author: Elia, D. | arXiv: 2511.10825 | DOI: 10.1051/0004-6361/202554764

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: star_formation, milky_way_ism
- Question: How do the number, mass and formation efficiency of cores in ALMAGAL clumps correlate with the clump physical parameters and evolutionary indicators, and which star formation scenario (core-fed or clump-fed) do they favour?  
  > "This study aims at correlating the fragmentation properties of massive clumps, obtained from ALMA observations, with their global physical parameters" (abstract)
- Target **1007 ALMAGAL clumps in the Galactic plane (Hi-GAL and RMS selected)**: coordinates _not stated_; z/distance heliocentric distances, mostly ~2-8 kpc; near d <= 4.66 kpc and far d > 4.66 kpc  
  > "Of the 1017 targets initially present in the ALMAGAL observing plan, 1007 are analyzed in this work." (2.1 Clump physical parameters); distance from Megeath/Mege et al. (cite: meg21), updated by Benedettini et al. (in prep.) using ALMAGAL line radial velocities  
  > "Of the 1017 targets initially present in the ALMAGAL observing plan, 1007 are analyzed in this work." (2.1 Clump physical parameters)

## Data provenance

- ALMA projects: _none stated_
- bands: 1.3-1.4 mm continuum  
  > "as observed in continuum maps at 1.4 mm of the ALMAGAL survey" (Summary and conclusions)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 7M (ACA) + TM2 (C-2, C-3) + TM1 (C-5, C-6)  
  > "the compact configurations C-2 and C-3 (collectively referred to as TM2), and the extended configurations C-5 and C-6 (summarized as TM1) were combined with data from the 7m array" (2.2 Core physical parameters)
- configurations: near (d<=4.66 kpc): C2+C5, 476 targets; far (d>4.66 kpc): C3+C6, 531 targets  
  > "the “near” distance for $d \leq 4.66$ kpc (C2+C5 configurations, 476 targets observed), and the “far” distance for $d > 4.66$ kpc (C3+C6 configurations, 531 targets observed)" (2.2 Core physical parameters)
- baselines: _not stated_
- angular resolution: 0.15-0.3 arcsec  
  > "0.15 - 0.3" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: 90% flux completeness 0.95 mJy (0.13 and 0.37 Msun at d=3.5 and 6 kpc)  
  > "The 90% flux completeness in the catalog is 0.95 mJy, which translates into 0.13 and 0.37 M$_\odot$ at $d=3.5$ and 6 kpc, respectively." (2.2 Core physical parameters)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Herschel Hi-GAL**: 70-500 micron clump photometry, SED fits, masses, temperatures, luminosities  
  > "For these 1007 objects, physical properties are calculated from Hi-GAL photometry" (2.1 Clump physical parameters)
- Other facility **CORNISH and CORNISH South**: radio counterparts to identify UCHII regions  
  > "we searched for possible compact or ultra-compact HII (UCHII) region counterparts in the source catalogs of the radio surveys CORNISH (cite: pur13) and CORNISH South (cite: ira23)" (2.1 Clump physical parameters)
- External data: Core catalog (positions, flux densities, masses) extracted from ALMAGAL 7M+TM2+TM1 continuum maps  
  > "The morphologic, photometric, and physical properties of fragments detected in ALMAGAL continuum observations were determined by (cite: col25)." (2.2 Core physical parameters) [from (cite: col25)]
- External data: Clump physical parameters (mass, T, L, Tbol) from Hi-GAL catalogs  
  > "For the subsample of sources selected directly from the Hi-GAL catalog, data are taken from (cite: eli21)." (2.1 Clump physical parameters) [from (cite: eli17; eli21)]
- External data: Updated rescaled distance-dependent clump quantities and RMS-target recovery  
  > "Hence, re-scaled distance-dependent quantities were listed by (cite: mol25)." (2.1 Clump physical parameters) [from (cite: mol25)]
- External data: Sink particle number and mass vs L/M from Rosetta Stone simulations  
  > "We use recent numerical simulations produced by the Rosetta Stone project (cite: leb25)" (6.2.2 Comparison with simulations) [from (cite: leb25)]
- Simulation/model as data: Rosetta Stone RAMSES magnetized collapse of a 500 Msun clump (Mach 7, mu=10, T=10 K, ~0.38 pc), sink particles above 1e9 cm-3, ~400 au resolution  
  > "initial clump size $\sim 0.38$ pc (total size of the cube $\sim 1.5$ pc), mass $M=500~M_\odot$, turbulent Mach number $\mathcal{M}=7$" (6.2.2 Comparison with simulations)

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
- array combination: 7M+TM2+TM1 maps  
  > "the final products considered by (cite: col25) are called 7M+TM2+TM1 maps." (2.2 Core physical parameters)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Core detection and photometry with CuTEx adapted to ALMAGAL maps  
  > "The fragment[^2] detection and photometry in the ALMAGAL fields were carried out with the CuTEx algorithm (cite: mol11), specifically adapted to the ALMAGAL maps, as detailed in (cite: col25)." (2.2 Core physical parameters) [from (cite: col25)]
- Core flux to mass conversion with kappa=0.9 cm2/g at 1.3 mm and temperature scheme by clump L/M  
  > "assuming an opacity of 0.9 cm$^2$ g$^{-1}$ at 1.3 mm, suitable for dense environments (cite: oss94; san19), a gas-to-dust ratio of 100" (2.2 Core physical parameters) [from (cite: col25)]
- Clump SED fitting and bolometric temperature estimate  
  > "estimated as described in (cite: eli17)" (2.1 Clump physical parameters) [from (cite: eli17)]

### Not stated but needed to reproduce (our reading)

- Exact formula and normalization of Tcore ∝ (L/M)^0.22 for L/M>10
- Binning scheme (bin edges) for the median trends
- Fitting procedure details for power laws (weights, log space, data selection)
- Final ALMAGAL core catalog contents and version needed (from Coletta et al.)
- Exact clump catalog values after distance update (Benedettini et al. in prep.)
- Simulation sink curve data used in the figures

## Analysis recipe

1. **Assemble clump and core parameters**: Combine Hi-GAL clump parameters with ALMAGAL core catalog; classify as quiescent, star-forming, UCHII (CORNISH match within 10 arcsec)  
  > "Adopting a searching radius of 10$''$, 24 and 50 matches with ALMAGAL were found in the former and the latter, respectively." (2.1 Clump physical parameters)
   - assumption: Clump kappa300=10 cm2/g, beta=2, gas-to-dust 100; non-deconvolved sizes for surface density  
  > "A modified black body (cite: eli16) with a mass opacity coefficient (hereafter opacity) of $\kappa_{300}=10$ cm$^2$ g$^{-1}$ at 300 $\mu$m" (2.1 Clump physical parameters)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive fragmentation descriptors**: Compute Ncore, mass of most massive core MMC, fMMC and CFE = total core mass / clump mass  
  > "defined as the total mass of the cores identified in a clump divided by the clump’s total mass" (5 Core formation efficiency)
   - fitting: _not stated_
   - validation: Checked distance bias; restricted to 2<d<6 kpc; free-free-free subsample in Appendix  
  > "we recalculated all median trends of the other clump parameters shown in panels $b$ to $f$ of Figure [7](#massmaxvsall) by considering only targets located at $2~\mathrm{kpc} < d < 6~\mathrm{kpc}$." (4.1)
3. **Statistical correlations and trends**: Medians in bins, Spearman matrix, two-sample K-S test between classes, power-law least-squares fits  
  > "we obtain coefficients $\rho_\mathrm{S}$ by considering the $n=840$ ALMAGAL targets with all clump properties defined and $N_\mathrm{core} \geq 1$." (6.1)
   - fitting: Power laws by least squares; uncertainties from the fit  
  > "(parameter uncertainties are simply derived from least squares fitting to data)" (5.3)
   - validation: Resampling of 100 subsamples of 30 points; critical Spearman values from Student t  
  > "we performed a resampling test by extracting 100 random subsamples of 30 data points (out of 840) for each pair of variables" (6.1)
4. **Compare with simulations and scenarios**: Overplot Rosetta Stone sink count, sink efficiency and max sink mass vs L/M and compare with core-fed and clump-fed predictions  
  > "The predicted number of sink particles (gray line in Figure [17](#ncoremultiplot), and orange in Figure [4](#ncoresvsall) (panel $d$)) exceeds most ALMAGAL values by a factor $\gtrsim 2$" (6.2.2 Comparison with simulations)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CuTEx** : core detection and photometry in ALMAGAL maps (done in Coletta et al.)  
  > "carried out with the CuTEx algorithm (cite: mol11)" (2.2 Core physical parameters)
- **RAMSES** : simulations compared (by Lebreuilly et al.)  
  > "by using the RAMSES code (cite: tey02; fro06)" (6.2.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Clumps analyzed | 1007 (891 star-forming, 116 quiescent) | not stated | clumps | 1 | The ALMAGAL sample is divided in 891 star-forming and 116 quiescent sources, respectively. |
| Spearman rho Mmmc vs clump mass | 0.34 | not stated | dimensionless | 3 | A large scatter is found, with a Spearman’s rank correlation coefficient $\rho_\mathrm{S}=0.34$. |
| Power-law exponent Mmmc vs Sigma | 0.75 | 0.06 | dimensionless | 3 | the best-fit exponent is found to be $0.75\pm 0.06$ for the entire population |
| CFE vs L/M power-law exponent | 0.36 | 0.02 | dimensionless | 3 | \mathrm{CFE}=10^{-2.54\pm 0.02}\;\left[\frac{L/M}{\mathrm{L}_\odot/\mathrm{M}_\odot}\right]^{0.36\pm 0.02} |
| CFE vs T power-law exponent | 2.5 | 0.1 | dimensionless | 3 | \mathrm{CFE}=10^{-5.42\pm 0.13}\;\left[\frac{T}{\mathrm{K}}\right]^{2.5\pm 0.1} |
| CFE median and range | median 0.4%, range 0.01% to 15% | not stated | percent | 2 | the derived CFEs range from 0.01% to 15%, with a median of 0.4% |
| Clumps with MMC > 24 Msun | 31 (30 with L/M>1, 24 with L/M>10) | not stated | clumps | 2 | Looking in particular at the 31 clumps with $M_\mathrm{MMC} > 24~\mathrm{M}_\odot$ |
| K-S statistic Ncore quiescent vs star-forming | D=0.31 (critical 0.19 at 99%) | not stated | dimensionless | 3 | In this case, the K-S statistic is $D=0.31$ |

## Qualitative findings

- Ncore correlates preferentially with clump surface density, not with total clump mass  
  > "The fragmentation level correlates preferentially with clump surface density, supporting a scenario of density-driven fragmentation" (abstract)
- Cores above 24 Msun are absent in quiescent clumps and found only in clumps with Sigma > 0.3 g cm-2  
  > "Cores with masses of at least 24 M$_\odot$ (i.e., three times the 8 M$_\odot$ threshold for defining a massive star) are exclusively found in clumps with a surface density exceeding 0.3 g cm$^{-2}$" (4.2)

## Claim tuples

- H: Fragmentation level depends on clump mass or surface density | E: Ncore vs M and Sigma, medians and Spearman | R: No clear dependence on M; clearer increase with Sigma | F: Density-driven fragmentation | **supported**
- H: Core growth continues during clump evolution | E: MMC and CFE vs T, L/M | R: Both increase on average by an order of magnitude with large scatter | F: Favours clump-fed over core-fed scenarios | **supported**
- H: Simulations reproduce the observed fragmentation | E: Compare Rosetta Stone 500 Msun mu=10 sinks with Ncore and CFE | R: Similar trends but simulations exceed observations by factor >=2 | F: Stellar feedback, sensitivity and resolution may explain the discrepancy | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Core-fed model rejected because core masses and CFE increase with time and no isolated massive cores are seen  
  > "multiple arguments emerge against a core-fed scenario" (6.2.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Continuum data cannot quantify magnetic fields, turbulence or feedback; Ncore values may be lower limits due to sensitivity  
  > "the $N_\mathrm{core}$ values plotted in various figures might be intended as lower limits for this quantity." (6.2.1)
- Caveat (inferred, ours): Core masses assume temperatures from clump L/M, so trends with L/M may be partly built in
- Caveat (inferred, ours): Clump and core opacities differ by a factor 1.7, affecting CFE
- Caveat (inferred, ours): Spearman significance is ambiguous at n=840
- Caveat (inferred, ours): Ncore is sensitivity limited and distance dependent

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Core catalog of Coletta et al. and the clump table of Molinari et al. are needed as inputs
- Missing: Simulation outputs from Lebreuilly et al.
- Missing: Binning details
- Data volume (inferred): Catalog-level analysis; raw ALMAGAL data are very large (TB scale) but not needed if catalogs are available
- Score (inferred): 3/5, Analysis relies on catalogs from companion papers and is statistical, with partial recipe detail.
- Rediscovery candidate: no, Depends on unreleased or companion catalogs and unspecified binning; project code not printed.

## Links

- Method: (cite: col25) (core extraction and mass catalog)
- Method: (cite: mol25) (ALMAGAL survey and clump parameters)
- Method: (cite: san25) (ALMAGAL data processing)
- Companion: (cite: sch25) (spatial arrangement of cores)
- Companion: (cite: leb25) (Rosetta Stone simulations)
- Related: ALMAGAL
- Related: Hi-GAL
- Related: Rosetta Stone project
- Related: ASHES
- Related: ALMA-IMF
- Related: CORNISH

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2019.1.00195.L"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 33,
  "rate": 0.458
 },
 "evidence_ok": true
}
```
