# The ALMA-ATOMS survey: Vibrationally excited HC<SUB>3</SUB>N lines in hot cores

`2025A&A...694A.166C` | Astronomy and Astrophysics 2025 | first author: Chen, Li | arXiv: 2412.12546 | DOI: 10.1051/0004-6361/202452598

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: How do the physical conditions in hot cores affect the excitation of vibrationally excited HC3N lines (HC3N*), observed at 3 mm in 60 hot cores?  
  > "We present the Atacama Large Millimeter/submillimeter Array (ALMA) 3 mm observations of HC$_3$N\* lines in 60 hot cores and investigate how the physical conditions affect the excitation of HC$_3$N\* transitions." (abstract)
- Target **60 hot cores from the ATOMS survey (e.g. IRAS 16348-4654, IRAS 18056-1952)**: coordinates _not stated_; z/distance Distances 1.34 to 12.09 kpc (Tables 1-4)  
  > "identified 60 hot cores, which were selected as the sample for our study." (2.2 Data calibration and imaging); distance from _not stated_

## Data provenance

- ALMA projects: 2019.1.00685.S
- bands: Band 3 (3 mm)  
  > "is an ALMA band 3 survey" (2.1 ALMA observations)
- frequencies and spectral setup: SPW 7 and 8 in the upper sideband, 1875 MHz bandwidth, ~1.6 km/s resolution, centers ~98,505 and 100,454 MHz  
  > "with center frequencies of $\sim$ 98,505 MHz and 100,454 MHz, respectively" (2.1 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: ACA 7 m and 12 m array; only 12 m used for line identification  
  > "we exclusively rely on 12 m array data to identify molecular lines and hot cores." (2.1 ALMA observations)
- configurations: 12 m C43-2 or C43-3  
  > "the 12 m array (C43-2 or C43-3 configuration)" (2.1 ALMA observations)
- baselines: _not stated_
- angular resolution: about 1.2-1.9 arcsec  
  > "approximately 1.2-1.9 arcsec" (2.2 Data calibration and imaging)
- max recoverable scale: about 60 arcsec  
  > "the maximum recoverable angular scales were approximately 60 arcsec" (2.2 Data calibration and imaging)
- sensitivity: about 0.4 mJy/beam continuum; better than 10 mJy/beam per channel for lines  
  > "mean sensitivity of approximately 0.4 mJy beam$^{-1}$ for the continuum and better than 10 mJy beam$^{-1}$ per channel for the lines" (2.2 Data calibration and imaging)
- time on source: _not stated_
- observing dates: September to mid-November 2019  
  > "The observations were conducted from September to mid-November 2019" (2.1 ALMA observations)
- pi or archival as stated: ATOMS survey, PI Tie Liu  
  > "Project ID: 2019.1.00685.S; PI: Tie Liu" (2.1 ALMA observations)
- Line: HC3N v7=1, v7=2, v7=3, v6=1, v6=v7=1, v5=1, v4=1 J=11-10 (99938-101170 MHz (SPW 8))
- Line: H40alpha H40alpha (99,023 MHz)
- External data: Dust temperature from COM (CH3OCHO, C2H5CN, CH3OH) rotation temperatures  
  > "The dust temperature is adopted from the temperature of COMs (CH$_3$OCHO, C$_2$H$_5$CN, and CH$_3$OH) calculated by (cite: 2022MNRAS.511.3463Q)." (Table 1) [from (cite: 2022MNRAS.511.3463Q)]
- External data: Hot core sample, and source distances/systemic velocities/R_GC  
  > "the R$\rm_{GC}$ of the cores was taken from (cite: 2020MNRAS.496.2790L)" (3.2.2 Parameter calculation) [from (cite: 2020MNRAS.496.2790L)]
- External data: Dust absorption coefficient 0.24 cm2/g at 99 GHz  
  > "interpolated to be 0.24 cm$^2$ g$^{-1}$ at 99,000 MHz (cite: 1994A&A...291..943O)" (3.2.2 Parameter calculation) [from (cite: 1994A&A...291..943O)]
- External data: Gas-to-dust ratio vs galactocentric distance  
  > "which increases with galactocentric distance R$\rm_{GC}$ , which was described by (cite: 2017A&A...606L..12G; 2023ApJ...950...57T)" (3.2.2 Parameter calculation) [from (cite: 2017A&A...606L..12G; 2023ApJ...950...57T)]
- External data: Critical densities for collisional excitation of vibrational levels at 300 K  
  > "the critical densities (n$\rm _{crit}$) for collisional excitation of the v$_7$=1, v$_6$=1, v$_5$=1, and v$_4$=1 levels at 300 K are 4$\times$10$^8$, 3$\times$10$^{11}$, 7$\times$10$^{12}$, and 2$\times$10$^{10}$ cm$^{-3}$, respectively (cite: 1999A&A...341..882W)" (1 Introduction) [from (cite: 1999A&A...341..882W)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.6  
  > "Data reduction and image processing were conducted using version 5.6 of the Common Astronomy Software Applications" (2.2 Data calibration and imaging)
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
- line free channels: Line-free channels selected in SPW 7 and 8 for continuum, central frequency ~99,404 MHz  
  > "line-free channels were selected in SPW 7 and SPW 8, with a central frequency of approximately 99,404 MHz" (2.2 Data calibration and imaging)
- primary beam correction: All images primary-beam corrected  
  > "All images were corrected for primary beam." (2.2 Data calibration and imaging)
- array combination: _not stated_
- smoothing: Line cubes at native spectral resolution  
  > "Line cubes were produced for each SPW with their native spectral resolution" (2.2 Data calibration and imaging)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ATOMS observations, calibration and imaging; source velocities  
  > "see (cite: 2020MNRAS.496.2790L) for specific values" (3.1 HC3N* line identification) [from (cite: 2020MNRAS.496.2790L)]
- Hot core identification using COMs  
  > "(cite: 2022MNRAS.511.3463Q) successfully identified 60 hot cores" (2.2 Data calibration and imaging) [from (cite: 2022MNRAS.511.3463Q)]

### Not stated but needed to reproduce (our reading)

- tclean parameters (robust, cell, image size, deconvolver, masks)
- Exact line-free channel ranges for continuum
- Pipeline vs manual calibration and flux calibrator
- XCLASS fit priors and parameter bounds, optimizer
- Spectral extraction aperture at each hot core peak
- Continuum core coordinates
- Line-width and velocity ranges for moment-0 maps

## Analysis recipe

1. **Identify HC3N* lines and fit LTE model**: Spectra at hot-core peak; XCLASS LTE fit with CDMS/JPL line data; free parameters: source size, Trot, N, line width, velocity offset; same abundance for all states  
  > "by setting the deconvolved size of the continuum core, rotation temperature, source-averaged column density, line width, and velocity offset as free parameters in the fitting process" (3.1 HC3N* line identification)
   - software: XCLASS, CDMS, JPL
   - parameter: Detection requires 3 sigma and velocity near systemic; need at least three lines per state to fit  
  > "with a line intensity above the 3$\sigma$ detection level." (3.1 HC3N* line identification)
   - assumption: LTE  
  > "assuming local thermodynamic equilibrium (LTE)" (3.1 HC3N* line identification)
   - fitting: _not stated_
   - validation: Rotational temperature diagram consistent with XCLASS within errors  
  > "The rotation temperatures obtained via RTD are consistent with those derived from XCLASS within the errors." (3.2.2 Parameter calculation)
2. **Measure continuum core size and flux**: 2D Gaussian fit in CASA; subtract free-free emission estimated from H40alpha for UC HII cores  
  > "We used the 2D Gaussian fitting in CASA to determine the deconvolved core size" (3.2.1 Continuum flux)
   - software: CASA
   - parameter: Te = 6000 K, N(He+)/N(H+) = 0.08  
  > "N(He$^+$)/N(H$^+$) $\approx$ 0.08 is the typical ratio" (3.2.1 Continuum flux)
   - assumption: Free-free optically thin at 99,023 MHz  
  > "We assumed that the free-free continuum is optically thin at 99,023 MHz." (3.2.1 Continuum flux)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive core mass, N(H2), n(H2), abundance**: Optically thin dust emission formulae with Td from COMs; n(H2)=M/((4/3)pi mu mH R^3)  
  > "M$\rm _{\text{core}} = \frac{D^2 S_\nu^{int} \eta}{\kappa_\nu B_\nu (T_d)}$" (3.2.2 Parameter calculation)
   - assumption: mu=2.8; kappa=0.24 cm2/g; gas-to-dust ratio from R_GC relation  
  > "where $\mu\approx2.8$ is the mean particle weight per $\rm H_2$ molecule" (3.2.2 Parameter calculation)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare excitation types with physical properties**: Classify cores by number of HC3N* states; compare Trot, N, flux ratios, n(H2) with n_crit; moment-0 maps and peak offsets vs H40alpha  
  > "We categorized the types of hot cores based on the number of HC$_3$N\* states and refer to each category as a different excitation type" (4.1 The role of UC Hii regions)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.6: Data reduction, imaging, 2D Gaussian fitting  
  > "version 5.6 of the Common Astronomy Software Applications" (2.2 Data calibration and imaging)
- **XCLASS** : Line identification and LTE fitting  
  > "Precise line identification was performed using the eXtended CASA Line Analysis Software Suite (XCLASS" (3.1 HC3N* line identification)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Hot cores with HC3N* detected | 52 of 60 | not stated | count | 1 | We have detected HC$_3$N\* lines in 52 hot cores, 29 of which show more than one vibrationally excited state. |
| Rotation temperature range | 160 to 335 K, mean 235 K | (160±18) to (335±22) K; mean ±21 | K | 1 | the rotation temperature ranges from (160$\pm$18) to (335$\pm$22) K, with a mean value of (235$\pm$21) K |
| HC3N* column density range | 6.9e15 to 1.7e18 | ±0.3e15 and ±0.1e18 | cm^-2 | 1 | ranges from (6.9$\pm$0.3)$\times$10$^{15}$ to (1.7$\pm$0.1)$\times$10$^{18}$ cm$^{-2}$ |
| n(H2) of cores with HC3N* | 1.3e5 to 5.0e8, mean 3.2e7 | ±0.2e5, ±0.5e8 | cm^-3 | 3 | ranges from (1.3$\pm$0.2)$\times$10${^5}$ to (5.0$\pm$0.5)$\times$10$^{8}$ cm$^{-3}$, with a mean value of 3.2$\times$10$^{7}$ cm$^{-3}$ |
| Detection rate of v7=1 | 87% | not stated | percent | 1 | The detection rates for v$_7$=1, v$_7$=2, v$_6$=1, v$_5$=1, v$_7$=3, v$_6$=v$_7$=1, and v$_4$=1 are 87%, 48%, 45%, 27%, 27%, 25%, and 3%, respectively. |
| HC3N* abundance range | 6.9e-10 to 2.3e-7 | ±1.5e-10, ±0.2e-7 | dimensionless | 3 | ranges from (6.9$\pm$1.5)$\times$10$^{-10}$ to (2.3$\pm$0.2)$\times$10$^{-7}$ |

## Qualitative findings

- HC3N* spatial distribution is affected by UC HII regions; excitation requires dense environments  
  > "The excitation of HC$_3$N\* requires dense environments, and its spatial distribution is affected by the presence of UC Hii regions." (abstract)

## Claim tuples

- H: Does gas temperature relate to the number of detected HC3N* states? | E: Detection and LTE fitting across 60 hot cores | R: Hotter cores show more vibrational states | F: Higher gas temperature gives more detections | **supported**
- H: Is HC3N* excited by mid-IR pumping or collisions? | E: Compare n(H2) with critical densities | R: All but one core (I18507+0110) have n(H2) apparently inconsistent with collisional dominance | F: Mid-IR pumping dominates | **supported**
- H: Does column density determine the number of excited states? | E: Compare N by excitation type | R: Thresholds 1.9e16 and 7.6e16 cm^-2 | F: More states with higher column density | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): 3 mm data cannot resolve the emission distribution in distant sources  
  > "since these two sources are located at very large distances, we were unable to resolve the emission distribution with 3 mm data." (3.3 Spatial distributions)
- Caveat (inferred, ours): Only the J=11-10 transition per state, so pumping vs collisions is inferred indirectly from n(H2) at core scale
- Caveat (inferred, ours): LTE and a single Td from COMs assumed for the dust
- Caveat (inferred, ours): Distances and Td inherited from other papers
- Caveat (inferred, ours): n_crit comparison is at 300 K

## Reproducibility

- Data public (paper): Derived data on Zenodo; ALMA project ID given  
  > "The derived data underlying this article are available in the article and in its online supplementary material on" (Data availability)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: XCLASS fit setup and bounds
- Missing: Hot core peak positions
- Missing: COM temperatures and distances from companion papers
- Data volume (inferred): Large: about 60 fields of 12 m band-3 data, tens to hundreds of GB
- Score (inferred): 3/5, Public data and clear formulae, but imaging and fitting setup are missing and key inputs are inherited.
- Rediscovery candidate: no, Fit and imaging settings are incomplete and the sample inputs come from companion papers.

## Links

- Method: (cite: 2017A&A...598A...7M) (XCLASS)
- Companion: (cite: 2020MNRAS.496.2790L) (ATOMS survey overview)
- Companion: (cite: 2022MNRAS.511.3463Q) (Hot core sample and COM temperatures)
- Companion: (cite: 2021MNRAS.505.2801L) (H40alpha UC HII identification)
- Related: ATOMS

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 37,
  "rate": 0.521
 },
 "evidence_ok": true
}
```
