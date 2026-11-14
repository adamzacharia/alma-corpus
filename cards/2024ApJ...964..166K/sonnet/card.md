# Physical Properties of Molecular Clouds in the Overlap Region of the Merging Antennae Galaxies

`2024ApJ...964..166K` | The Astrophysical Journal 2024 | first author: Krahm, Grace | arXiv: 2401.04835 | DOI: 10.3847/1538-4357/ad2451

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: What are the physical properties of GMCs in the Antennae overlap region, which can form super star clusters, and how do they compare with GMCs in other galaxy environments?  
  > "we present high-resolution ALMA observations of $\mathrm{^{12}CO(2-1)}$, $\mathrm{^{12}CO(3-2)}$, and $\mathrm{^{13}CO(2-1)}$ to characterize the physical conditions of GMCs in the Antennae overlap region" (1 Introduction)
- Target **Antennae overlap region (NGC 4038/39)**: coordinates _not stated_; z/distance 22 Mpc  
  > "At a distance of 22 Mpc (cite: 2008AJ....136.1482S), the merging Antennae galaxies (NGC 4038/39) are of particular interest as the closest major galaxy merger." (1 Introduction); distance from Schweizer et al. 2008 (cite: 2008AJ....136.1482S)  
  > "At a distance of 22 Mpc (cite: 2008AJ....136.1482S), the merging Antennae galaxies (NGC 4038/39) are of particular interest as the closest major galaxy merger." (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.00977.S, 2016.1.00924.S
- bands: Band 6 and 7  
  > "This includes Band 6 and 7 observations of the $\mathrm{^{12}CO(2-1)}$, $\mathrm{^{13}CO(2-1)}$, and $\mathrm{^{12}CO(3-2)}$ emission lines" (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 12CO(2-1) 0.09x0.12"; 12CO(3-2) 0.15x0.16"; 13CO(2-1) 0.17x0.18"; convolved to 0.166" x 0.180"  
  > "Both the $\mathrm{^{12}CO(2-1)}$ and $\mathrm{^{12}CO(3-2)}$ lines were later convolved to the same 0.166" x 0.180" resolution as $\mathrm{^{13}CO(2-1)}$ for analysis." (Table 1)
- max recoverable scale: _not stated_
- sensitivity: rms 1.74 K (12CO 2-1), 0.48 K (12CO 3-2), 1.29 K (13CO 2-1) at 5 km/s channels  
  > "| $\mathrm{^{12}CO(2-1)}$ | 0.09 x 0.12 | 1.74 | 5 |" (Table 1)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: 12CO J=3-2 (not stated)
- Other facility **VLA 3.6 cm (project AN074)**: Archival 8.46 GHz continuum used for ionizing flux  
  > "we also used archival 3.6 cm (8.46 GHz) radio continuum data (project AN074)taken with the Karl G. Jansky Very Large Array (VLA) at X-band in the A configuration" (2 Observations)
- External data: 12CO/13CO=70 (range 40-200) and CO line ratios CO(1-0)/CO(2-1)=0.95, CO(1-0)/13CO(2-1)=22  
  > "Each of the $\mathrm{R_{l}}$ ratios were taken from (cite: Zhu_2003) with typical line intensity for $\mathrm{CO(1-0)/CO(2-1)}$ and $\mathrm{CO(1-0)/^{13}CO(2-1)}$ of 0.95 and 22 respectively." (4.2) [from (cite: Zhu_2003)]
- External data: Comparison GMC catalogs for 9 environments (Table 5)  
  > "(1) (cite: article2); (2) (cite: Rosolowsky_2007); (3) (cite: 10.1093/mnras/stab085); (4) (cite: 2019ApJ...876..141I)" (Table 5) [from Heyer 2009; Rosolowsky 2007; Rosolowsky 2021; Imara & Faesi 2019; Leroy 2006; Miura 2018; Utomo 2015; Oka 2001]
- External data: H2/12CO abundance 1e4-1e5 from Galactic sources  
  > "(cite: 2014A&A...563A..97G) found that the abundance ratio ranges between $10^{4}-10^{5}$ for the earliest stage of massive star formation" (4.2) [from (cite: 2014A&A...563A..97G)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "All calibration and reduction of the observations were done using the CASA 4.7.2 pipeline." (2 Observations)
- casa version: CASA 4.7.2  
  > "All calibration and reduction of the observations were done using the CASA 4.7.2 pipeline." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1256-0547 and J1037-2934  
  > "We used the J1256-0547 and J1037-2934 flux calibrators for flux calibration" (2 Observations)
- flux scale uncertainty: 10%  
  > "estimated a flux uncertainty of 10% due to the source variability" (2 Observations)
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
- primary beam correction: performed with CASA  
  > "A primary beam correction was also performed using CASA." (2 Observations)
- array combination: _not stated_
- smoothing: Cubes convolved to 13CO(2-1) resolution  
  > "we convolved the data cubes to the same resolution as the $\mathrm{^{13}CO(2-1)}$ data cube, which had the lowest resolution." (2 Observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Detailed observation parameters and calibration  
  > "A more in-depth description of the observation parameters and calibration is available in (cite: 2019ApJ...874..120F)." (2 Observations) [from Finn et al. 2019 (cite: 2019ApJ...874..120F)]
- eta = 1.91 effective radius definition  
  > "We adopt $\mathrm{\eta}$ = 1.91 to maintain consistent size definitions with earlier studies" (4.1) [from Solomon 1987; Rosolowsky 2007; Miura 2018; Rosolowsky 2021]
- Pi=0.5 in pressure equation  
  > "where we adopt $\mathrm{\prod=0.5}$ (cite: 2015ApJ...806...35J)" (4.3) [from Johnson et al. 2015]

### Not stated but needed to reproduce (our reading)

- Phase center/coordinates of the overlap field and exact observation dates, arrays and configurations
- Spectral window setup and rest frequencies
- Imaging parameters (tclean weighting, robust, cell size, image size, deconvolver) used for the cubes
- Electron temperature Te used for the ionizing flux
- Details of how the ellipse HWHM fit and the circularity-based radius error were done
- Whether continuum was subtracted and which channels were line-free
- Distribution used for line profile fit and how sigma_v errors were propagated

## Analysis recipe

1. **Convolve and primary-beam correct cubes**: Convolve all cubes to 13CO(2-1) beam; primary beam correction in CASA  
  > "we convolved the data cubes to the same resolution as the $\mathrm{^{13}CO(2-1)}$ data cube, which had the lowest resolution." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify clumps**: quickclump on non-primary-beam-corrected 12CO(2-1) cube; same pixel assignments applied to PB-corrected cubes of all lines  
  > "Both dendrogram and clump-finding algorithms were run on the non-primary beam-corrected data cube for the $\mathrm{^{12}CO(2-1)}$ emission to better identify the boundaries of the structures." (3 Structure Decomposition)
   - software: quickclump
   - parameter: Tcutoff=4.3σ, Iminpk=5.75σ, dTleaf=1.5σ, Npixmin=300, Nlevels=1000  
  > "`Tcutoff`=$4.3\sigma$, `Iminpk`=$5.75\sigma$, `dTleaf`=$1.5\sigma$, `Npixmin`=300, and `Nlevels`=1000" (3.1)
   - fitting: _not stated_
   - validation: Parameters tuned to include maximum emission, exclude clumps absent in other lines, and agree with Firecracker and B1 cloud sizes  
  > "These parameters were optimized to include the maximum amount of emission while still excluding clumps that do not appear in the other emission lines." (3.1)
3. **Dendrogram decomposition**: astrodendro on the 12CO(2-1) cube  
  > "We used the package `astrodendro` (cite: Rosolowsky_2008) to decompose the emission into hierarchical structures" (3.2)
   - software: astrodendro
   - parameter: min_value=3σ, min_delta=1.5σ, min_peak=4.5σ, min_npix=2 beam areas  
  > "`min_value`$=3\sigma$, `min_delta`$=1.5\sigma$, `min_peak`=$4.5\sigma$, and `min_npix`=2 beam areas" (3.2)
   - fitting: _not stated_
   - validation: Trunks align with SGMCs of Wilson et al. 2000  
  > "These large structures generally align with the super giant molecular cloud (SGMC) classifications from (cite: 2000ApJ...542..120W)" (3.2)
4. **Measure radii and velocity dispersions**: Ellipse fit to HWHM gives R=sqrt(maj*min); Gaussian fit (scipy curve_fit) to intensity-weighted line profile; deconvolve beam and channel width; scale by eta  
  > "The velocity dispersion and its error, $\mathrm{\sigma_{v}}$ and $\mathrm{\delta_{v}}$, were found by fitting distributions (`scipyoptimizecurve_fit`, (cite: 2020NatMe..17..261V)) to the intensity-weighted mean line profiles." (4.1)
   - software: SciPy
   - parameter: eta=1.91; channel width 5 km/s  
  > "We adopt $\mathrm{\eta}$ = 1.91 to maintain consistent size definitions with earlier studies" (4.1)
   - fitting: Gaussian least-squares fit  
  > "The velocity dispersion and its error, $\mathrm{\sigma_{v}}$ and $\mathrm{\delta_{v}}$, were found by fitting distributions (`scipyoptimizecurve_fit`, (cite: 2020NatMe..17..261V)) to the intensity-weighted mean line profiles." (4.1 Sizes and Linewidths)
   - validation: Fits with A_exact/A_R >5 standard deviations above average were discarded  
  > "were discarded as poor fits that did not accurately represent the sizes of the clouds." (4.1)
5. **Derive masses (LTE and X_CO)**: LTE from 12CO/13CO(2-1) with Tx, tau, N(13CO), H2/13CO=1.4e6; and M_lum=1.36 m_H2 X_CO L_CO with X_CO=0.5e20  
  > "The luminosity is then converted into mass using the standard $\mathrm{X_{CO}=0.5\times10^{20}\;cm^{-2}(K\:km\:s^{-1})^{-1}}$ for starburst galaxies" (4.2.2)
   - parameter: 12CO/13CO=70, H2/12CO=2e4, R21 CO(1-0)/CO(2-1)=0.95  
  > "We used abundance ratios of $\mathrm{H_{2}/^{13}CO=1.4\times 10^{6}}$ by combining $\mathrm{^{12}CO/^{13}CO}=70$ and $\mathrm{H_{2}/^{12}CO=2\times 10^{4}}$" (4.2.1)
   - assumption: 12CO optically thick, 13CO optically thin, same Tx, LTE  
  > "which we assumed to be optically thick and optically thin respectively" (4.2.1)
   - fitting: _not stated_
   - validation: K-S test between masses: statistic 0.148, p=0.524  
  > "The K-S statistic and p-value between the two mass distributions are 0.148 and 0.524 respectively" (4.2.2)
6. **Compute virial parameter, pressure, surface density, free-fall time**: alpha_vir=5σv²R/GM; Pe=3ΠMσv²k/4πR³; Σ=M/πR²; tff  
  > "$$\alpha_{vir}=\frac{5\sigma_{v}^{2}R}{GM}$$" (4.3)
   - parameter: Π=0.5  
  > "where we adopt $\mathrm{\prod=0.5}$ (cite: 2015ApJ...806...35J)" (4.3)
   - fitting: _not stated_
   - validation: _not stated_
7. **Find pre-SSC candidate clumps**: GESD outlier test on properties (upper bound 20 outliers, 0.05 level); clumps outlying in ≥2 of density, pressure, virial parameter; thresholds M>1e6, R<25 pc, Pe/k>1e7 within uncertainties  
  > "we used the `papanda` implementation of the Generalized Extreme Studentized Deviate (GESD) test (cite: 1983Rosner) to detect outliers in each of the calculated physical properties with an upper bound of 20 outliers." (5.1)
   - software: papanda
   - assumption: 10% flux error and factor of 4 X_CO variation define uncertainties  
  > "assuming 10% errors in observed flux and that $\mathrm{X_{CO}}$ tends to vary by a factor of 4 in starburst galaxies" (5.1)
   - fitting: _not stated_
   - validation: _not stated_
8. **Ionizing flux from 3.6 cm continuum**: N_Lyc from Schmiedeke et al. 2016 Eq. 8; converted to O stars assuming 1e49 s^-1 per O7.5V star  
  > "This was converted to the number of O-type stars assuming that a typical O-type star (O7.5V) produces $\mathrm{N_{Lyc}=10^{49}\:s^{-1}}$" (5.2)
   - parameter: 3σ=0.11 mJy/beam threshold  
  > "detected above the 3$\sigma$ ($\mathrm{0.11\:mJy/beam}$) threshold" (5.2)
   - fitting: _not stated_
   - validation: _not stated_
9. **Compare with other galaxies**: Standardize catalogs (deconvolved R, σv, X_CO 2 or 0.5), fit size-linewidth σv=aR^b, Heyer relation, KDEs (0.25 dex), K-S tests (scipy ks_2samp)  
  > "we re-calculated any physical properties that did not match our definitions described in Section 4" (6)
   - software: SciPy
   - assumption: Galactic X_CO=2e20 for normal, 0.5e20 for starbursts and centers  
  > "standard Galactic and starburst values of $\mathrm{X_{CO}=2\times10^{20}\;cm^{-2}(K\:km\:s^{-1})^{-1}}$ and $\mathrm{X_{CO}=0.5\times10^{20}\;cm^{-2}(K\:km\:s^{-1})^{-1}}$ respectively" (6)
   - fitting: Non-linear least squares, b free or fixed 0.5  
  > "the slope is held constant at 0.5 and the intercept is fit using a non-linear least squares method" (Appendix Spatial and Spectral Resolution)
   - validation: Resolution tests by smoothing Antennae and Henize 2-10: intercepts differ by factor ≤2  
  > "the fitted intercepts are only a factor of 2 difference" (Appendix Spatial and Spectral Resolution)

## Software

- **CASA** 4.7.2: Pipeline calibration, primary beam correction  
  > "All calibration and reduction of the observations were done using the CASA 4.7.2 pipeline." (2 Observations)
- **quickclump** : Clump identification  
  > "we used the `quickclump` (cite: 2017ascl.soft04006S) algorithm" (3.1)
- **astrodendro** : Dendrogram decomposition  
  > "We used the package `astrodendro` (cite: Rosolowsky_2008)" (3.2)
- **papanda** : GESD outlier test  
  > "we used the `papanda` implementation of the Generalized Extreme Studentized Deviate (GESD) test" (5.1)
- **SciPy** : curve_fit line profiles; K-S tests  
  > "two-sample Kolmogorov–Smirnov (K-S) tests were performed on the GMC catalogs using `scipystatsks_2samp`" (Appendix K-S Tests)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of clumps | 72 | not stated | count | 2 | This resulted in a total of 72 individual clumps that contain 91 % of the total cube emission. |
| Dendrogram structures | 206 (124 leaves, 72 branches, 10 trunks) | not stated | count | 3 | This resulted in a total of 206 structures with 124 leaves, 72 branches (no correlation to the 72 identified clumps), and 10 trunks. |
| Possible SSC-forming clumps | 17 (6 outliers + 11) | not stated | count | 7 | In addition to these 6 outlier clumps, there are eleven other clumps that are within uncertainties of having the necessary conditions to form SSCs. |
| Mean virial parameter (Antennae) | 13.77 | ±0.37 | dimensionless | 6 | / Antennae Overlap / S / $13.77\pm0.37$ / 7.78 / supervirial / |
| Mean surface density | 441 (440.64) | σ=452 | Msun pc^-2 | 6 | / $\mathrm{\Sigma_{X_{CO}}}$ ($\mathrm{M_{\odot}\:pc^{-2}}$) / 53.9 / 2650 / 441 / 452 / |
| Mean Pe/k | 2.11e7 | σ=4.74e7 | K cm^-3 | 6 | / $\mathrm{P_{e, X_{CO}}/k}$ ($\mathrm{10^{7}Kcm^{-3}}$) / 0.02 / 28.1 / 2.11 / 4.74 / |
| Mean velocity dispersion | 17.9 | σ=9.04 | km/s | 4 | / $\mathrm{\sigma_{v}}$ ($\mathrm{km\:s^{-1}}$) / 5.24 / 46.6 / 17.9 / 9.04 / |
| Mean X_CO mass per clump | 1.14e6 | σ=1.58e6 | Msun | 5 | / $\mathrm{M_{lum}}$ ($\mathrm{10^{5}\:M_{\odot}}$) / 0.63 / 77 / 11.4 / 15.8 / |
| Size-linewidth fit, Antennae clumps | a=2.98, b=0.55 | ±0.15, ±0.01 | km/s pc^-0.5 (a) | 9 | / Antennae Clumps  / S     / 2.98$\pm$0.15  / 0.55$\pm$0.01  / 3.52$\pm$0.05 /   / |
| K-S between X_CO and LTE masses | statistic 0.148, p 0.524 | not stated | dimensionless | 5 | The K-S statistic and p-value between the two mass distributions are 0.148 and 0.524 respectively |

## Qualitative findings

- Only clump 9 of the 17 candidates has significant ionizing radiation (>5σ), so 16 likely retain intact birth environments  
  > "Clump 9 is of particular note as the only potential SSC-forming clump detected above the 5$\sigma$" (5.2)

## Claim tuples

- H: Do other Antennae overlap GMCs besides the Firecracker have properties to form SSCs? | E: GESD outlier search plus threshold on mass, radius, pressure, with 3.6 cm ionizing flux check | R: 17 of 72 clumps within uncertainties; only one has significant ionizing flux | F: 16 likely pre-SSC clouds with intact birth environments | **supported**
- H: Antennae GMCs differ from GMCs in other environments | E: Size-linewidth, Heyer relation, property KDEs and K-S tests across 10 environments | R: Antennae have highest luminosities, surface densities, pressures, wide linewidths, virial parameters among the highest | F: Antennae resemble galactic centers and some starbursts, unlike normal galaxies | **supported**
- H: LTE and X_CO mass estimates agree | E: K-S test of mass distributions | R: K-S 0.148, p 0.524; agreement within factor 1.34 (best) to 10.1 (worst) | F: X_CO masses consistent with LTE masses for best-fit abundance | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: X_CO masses used for comparability with other GMC catalogs  
  > "In order to be able to directly compare the properties of the Antennae overlap GMCs to other GMC catalogs that use this method, we also calculated cloud mass using a constant" (4.2.2)
- Alternative: Radii from exact area were ~1.5x larger than fitted radii; not adopted  
  > "cloud radii calculated from the exact area are on average 1.5 times larger than those calculated from fitting ellipses to the clouds’ HWHMs" (4.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Comparison depends on assumed X_CO and R21 and on resolution differences; starburst differences are ambiguous  
  > "any conclusions based on this category are heavily dependent on the assumption that these properties are not significantly affected by the resolution of the observations" (6.2)
- Caveat (inferred, ours): Single X_CO and abundance choices drive masses; no uncertainty propagation beyond stated factors
- Caveat (inferred, ours): Heterogeneous comparison catalogs and re-derivation of Henize 2-10 contradict published values
- Caveat (inferred, ours): Radius errors are large for many clumps, so SSC candidate selection depends on neglecting them
- Caveat (inferred, ours): Clump parameters were tuned by hand

## Reproducibility

- Data public (paper): ALMA project codes cited; VLA AN074 archival  
  > "we also used archival 3.6 cm (8.46 GHz) radio continuum data (project AN074)" (2 Observations)
- Products in archive: _not stated_
- Code: quickclump and papanda linked; no authors' own code stated  
  > "(<https://github.com/indebetouw/quickclump>)" (3.1)
- Missing: Imaging parameters for the ALMA cubes (see Finn et al. 2019)
- Missing: Electron temperature for N_Lyc
- Missing: Machine-readable catalogs only referenced, ellipse fitting details
- Data volume (inferred): tens of GB (3 line cubes, Cycle 3/4 high-resolution)
- Score (inferred): 3/5, Parameters for clump finding and equations are given, but calibration/imaging details are deferred to a prior paper and several fitting details are missing.
- Rediscovery candidate: no, Imaging details are not self-contained and the comparison catalogs require external data.

## Links

- Method: Finn et al. 2019 (cite: 2019ApJ...874..120F) (Observation parameters and calibration)
- Method: Mangum & Shirley 2015 (cite: 2015PASP..127..266M) (LTE column density equation)
- Companion: Johnson et al. 2015 (cite: 2015ApJ...806...35J) (Firecracker cloud properties and SSC progenitor criteria)
- Related: VLA AN074

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
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
  "facts": 95,
  "stated": 55,
  "rate": 0.579
 },
 "evidence_ok": true
}
```
