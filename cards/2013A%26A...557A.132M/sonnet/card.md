# ALMA imaging of the CO snowline of the HD 163296 disk with DCO<SUP>+</SUP>

`2013A&A...557A.132M` | Astronomy and Astrophysics 2013 | first author: Mathews, G. S. | arXiv: 1307.3420 | DOI: 10.1051/0004-6361/201321600

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Can DCO+ J=5-4 emission resolve the CO snowline in the HD 163296 disk and constrain the temperature range and abundance of DCO+ (and HCO+) relative to a disk physical model?  
  > "We aim to use line emission from DCO$^+$ to directly resolve the CO ‘snowline’ – the region at which the gas-phase CO abundance drops due to freezeout" (abstract)
- Target **HD 163296**: coordinates _not stated_; z/distance not stated (1.4'' corresponds to 170 AU)  
  > "The disk is observed at an inclination of 44$^\circ$, and position angle of $\sim$133$^\circ$  East-of-North." (Introduction); distance from Hipparcos parallax cited (Perryman et al. 1997), value not given  
  > "The disk is observed at an inclination of 44$^\circ$, and position angle of $\sim$133$^\circ$  East-of-North." (Introduction)

## Data provenance

- ALMA projects: 2011.0.00010.SV
- bands: Band 7  
  > "Band 7 observations of HD 163296 were carried out on June 9, 11, 22, and July 6, 2012" (Observations)
- frequencies and spectral setup: Four correlator bands at 345.796, 356.734, 346.998, 360.170 GHz; channel widths 122.1, 122.1, 244.1, 30.5 kHz; bandwidths 468.8, 468.8, 937.5, 117.2 MHz  
  > "with channel widths of 122.1, 122.1, 244.1, and 30.5 kHz, and total bandwidths of 468.8, 468.8, 937.5, and 117.2 MHz, respectively." (Observations)
- continuum bandwidth: _not stated_
- arrays: 17-20 12m antennas  
  > "The ALMA array included between 17 and 20 12m diameter antennas and baselines from 13m to 402m." (Observations)
- configurations: _not stated_
- baselines: 13 m to 402 m  
  > "The ALMA array included between 17 and 20 12m diameter antennas and baselines from 13m to 402m." (Observations)
- angular resolution: ~0.65'' x 0.44'', PA ~90 deg  
  > "The synthesized beam size is $\sim$0.65$''$ $\times$ 0.44$''$, at a position angle of $\sim$90$^\circ$." (Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 11.3, 8.2, 13.1 mJy/beam per 0.4 km/s channel (HCO+, H13CO+, DCO+)  
  > "| DCO$^+$    $J$=5$-$4 | 13.1 |   2.2$\pm$0.4 |   1.7 |" (Table 1)
- time on source: 59.4 minutes  
  > "for a total on-source time of 59.4 minutes" (Observations)
- observing dates: June 9, 11, 22, and July 6, 2012  
  > "carried out on June 9, 11, 22, and July 6, 2012" (Observations)
- pi or archival as stated: ALMA science verification program  
  > "as part of the ALMA science verification program" (Observations)
- Line: HCO+ J=4-3 (356.734 GHz)
- Line: H13CO+ J=4-3 (346.998 GHz)
- Line: DCO+ J=5-4 (360.170 GHz)
- Line: CO J=3-2 (345.796 GHz)
- Other facility **SMA**: Earlier CO/13CO data used by Q11 to locate the CO snowline at 155 AU  
  > "They estimated that the CO snowline of HD 163296 lies at a distance of 155 AU, corresponding to a midplane temperature of 19 K in their physical model." (Introduction)
- External data: Best-fit physical disk model of HD 163296 (mass, radii, gas-to-dust, dust properties, stellar parameters)  
  > "We adopt the overall disk properties derived by Q11 from fitting the broadband spectral energy distribution and spatial extent of their mm data" (Modeling details) [from Qi et al. 2011 (cite: Qi:2011)]
- External data: Observed CO-isotopologue line fluxes used to tune the gas structure  
  > "Table notes: Observed fluxes from Q11." (Table 2) [from Qi et al. 2011 (cite: Qi:2011)]
- External data: Molecular energy levels, frequencies and Einstein A coefficients  
  > "with energy levels, transition frequencies, and Einstein A coefficients taken from the Leiden Atomic and Molecular Database" (Modeling) [from (cite: Schoier:2005)]
- Simulation/model as data: Parametric disk model (RADMC dust temperature; LIME line radiative transfer) with a grid of HCO+, H13CO+, DCO+ abundance models compared to channel maps  
  > "We used this SED-constrained model as the basis for constructing a grid of HCO$^+$, H$^{13}$CO$^+$, and DCO$^+$ models" (Modeling)

## Processing

### Calibration

- pipeline or manual: CASA used for calibration and imaging; version not stated  
  > "We used the Common Astronomy Software Applications package (cite: McMullin:2007) to carry out calibration and imaging of the visibility datasets." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune (gain J1733-130, bandpass J1924-292)  
  > "For gain, bandpass, and flux calibration, we used J1733-130, J1924-292, and Neptune, respectively." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: Phase and amplitude self-calibration using line-free channels  
  > "Self-calibration was carried out for both phases and amplitudes using line free channels." (Observations)

### Imaging

- task: _not stated_
- deconvolver: CLEAN with natural weighting  
  > "We used the CLEAN algorithm with natural weighting and circular clean masks" (Observations)
- weighting robust: natural weighting  
  > "We used the CLEAN algorithm with natural weighting and circular clean masks" (Observations)
- uv taper: _not stated_
- cell size: 0.15''  
  > "The image cubes have a velocity resolution of 0.4 km s$^{-1}$ and pixel size of 0.15$''$ in each data cube." (Observations)
- image size: _not stated_
- masking: Circular clean masks of diameter ~9'', 5'', 5'' for HCO+, H13CO+, DCO+  
  > "circular clean masks with diameters of $\sim$9”, 5”, and 5” to produce channel maps of the HCO$^+$, H$^{13}$CO$^+$, and DCO$^+$ lines, respectively" (Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ~0.65'' x 0.44'', PA ~90 deg  
  > "The synthesized beam size is $\sim$0.65$''$ $\times$ 0.44$''$, at a position angle of $\sim$90$^\circ$." (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Physical disk model structure and parameters adopted from Q11  
  > "We use a parametric disk model to approximate the best-fit model of Q11" (Modeling) [from Qi et al. 2011 (cite: Qi:2011)]
- 12C/13C = 75 for H13CO+/HCO+ abundance ratio  
  > "H$^{13}$CO$^+$ is expected to have an abundance a factor of 75 less than HCO$^+$" (Estimated column densities) [from (cite: Frerking:1982)]
- Surface density profile form  
  > "We define the surface density as (cite: 2009ApJ...700.1502A)" (Modeling details) [from (cite: 2009ApJ...700.1502A)]
- Flaring index psi = 0.066  
  > "We set $\psi$ = 0.066, for consistency with the modeling of (cite: Tilling:2012)." (Modeling details) [from (cite: Tilling:2012)]

### Not stated but needed to reproduce (our reading)

- CASA version and the reduction/calibration scripts (or whether archive SV products were used)
- Line-free channels used for self-calibration and continuum subtraction, and self-cal solution intervals
- Clean threshold and number of iterations
- Goodness-of-fit criterion for the manual model comparison (fit was by eye on channel maps)
- Exact distance adopted for HD 163296
- Simulated-observation (CASA simulation) settings
- Primary beam correction details

## Analysis recipe

1. **Calibrate and image line cubes**: CASA calibration, self-calibration, CLEAN with natural weighting and circular masks to make 0.4 km/s channel maps  
  > "We used the CLEAN algorithm with natural weighting and circular clean masks with diameters of $\sim$9”, 5”, and 5” to produce channel maps" (Observations)
   - software: CASA
   - parameter: 0.4 km/s channels, 0.15'' pixels  
  > "The image cubes have a velocity resolution of 0.4 km s$^{-1}$ and pixel size of 0.15$''$ in each data cube." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure morphology and fluxes**: Fit an ellipse to 3 sigma contour of integrated HCO+ map; ring extents from integrated DCO+ map; integrate line fluxes  
  > "We fit an ellipse to the 3$\sigma$ contour of the integrated emission map, and find that it has major and minor axes of 7.8$''$ and 5.3$''$" (Morphology)
   - assumption: Flat disk for geometry  
  > "Under the assumption of a flat disk these correspond to a disk with an outer radius of 475 AU observed at an inclination of 47$^\circ$" (Morphology)
   - fitting: _not stated_
   - validation: Consistent with previous inclination  
  > "comparable to previous inclination determinations" (Morphology)
3. **Estimate column densities with RADEX**: Adjust HCO+ and H13CO+ columns until RADEX intensity ratio matches median observed ratio of 0.18; also column density sensitivity  
  > "we adjust the HCO$^+$ and H$^{13}$CO$^+$ column densities until the model intensity ratios match the median observed intensity ratio." (Estimated column densities)
   - software: RADEX
   - parameter: TK = 40 K, n(H2) = 1e7 cm^-3, dV = 1 km/s (DCO+ sensitivity: 1e9 cm^-3, 19 K)  
  > "Assuming a kinetic temperature $T_{\rm{K}}$ = 40 K and gas density $n_{\rm{H}_2}$ = 10$^{7}$ cm$^{-3}$" (Estimated column densities)
   - assumption: H13CO+ optically thin, LTE, abundance 1/75 of HCO+  
  > "We assume that the H$^{13}$CO$^+$ $J$=4$-$3 line is optically thin" (Estimated column densities)
   - fitting: _not stated_
   - validation: _not stated_
4. **Build disk physical model**: Parametric Q11-like model; RADMC for dust temperature/SED; LIME for CO lines; adjust scale heights to match SED and CO fluxes within ~50%  
  > "we achieve a match to the observed line fluxes within $\sim$50%." (Modeling details)
   - software: RADMC, LIME
   - parameter: h_small 0.08, h_large 0.06, h_main 0.1, h_tail 0.2, f_tail 0.05  
  > "The gas ‘tail’ has a scale height $h_{\rm{tail}}$ = 0.2 and includes 5% of the gas mass ($f_{\rm{tail}}$)" (Modeling details)
   - assumption: Gas temperature equals mean dust temperature; [CO]/[H] ~1e-4; gas-to-dust 154  
  > "we assume the gas temperature matches the mean dust temperature calculated in this modeling" (Modeling details)
   - fitting: Manual adjustment  
  > "We manually varied the isotopologue abundances, and in the case of DCO$^+$ the region in which it is abundant (discussed below), and compared the resulting channel maps to the observations." (Modeling, Physical structure)
   - validation: SED and CO line fluxes compared with literature  
  > "we adjust parameters to match the SED and CO line fluxes in the literature for HD 163296." (Modeling details)
5. **Fit HCO+ and H13CO+ abundances**: Manual grid of constant abundance between 19 K freezeout and photodissociation layer; compare integrated intensities and channel maps  
  > "We explored HCO$^+$ abundances relative to H$_2$ ranging from 10$^{-11}$ to 10$^{-5}$ in logarithmic steps of 0.5" (Molecular abundances)
   - software: LIME, CASA
   - parameter: H13CO+ = HCO+/75  
  > "setting the H$^{13}$CO$^+$ abundance to 1 / 75 that of HCO$^+$" (Molecular abundances)
   - fitting: Manual fit by comparing models to data; no sampler or likelihood  
  > "We manually varied the isotopologue abundances" (Modeling)
   - validation: Compared model and observed fluxes (Table 1) and channel maps  
  > "provides the best fit to both the total flux and to channel maps. We compare fluxes from our adopted model to the observed fluxes in Table [1](#tab:results)." (Modeling, Molecular abundances)
6. **Fit DCO+ abundance and temperature range**: Manual fit of uniform abundance within T_low to T_high; vary bounds and abundance; compare with 2 km/s channel maps  
  > "We find that a $\chi$$_{\rm{DCO^+}}$ of 1$\times$10$^{-10}$  at temperatures between $T_{\rm{high, DCO^+}}$ = 21 K and $T_{\rm{low, DCO^+}}$ = 19 K provides the best fit" (Molecular abundances)
   - software: LIME, CASA
   - parameter: Explored T_high 19-25 K, T_low 16-21 K, chi 1e-11 to 1e-8  
  > "| $T_{\rm{high, DCO^+}}$     | 21K                   | 19 – 25K               |" (Table 3)
   - fitting: Manual  
  > "We carried out a similar manual fit to the DCO$^+$ $J$=5$-$4 emission." (Modeling, Molecular abundances)
   - validation: Sensitivity tests: bounds shifted -3 K/+4 K, width doubled, abundance x3 up/down; alternative disk model of de Gregorio-Monsalvo et al. gives 16-20 K  
  > "we find that our observations are best described if DCO$^+$ is enhanced between temperatures of 16 and 20 K (compared to 19–21 K found using the Q11 model)" (Dependence on physical models)

## Software

- **CASA** : Calibration, self-calibration, imaging and simulated observations  
  > "Simulated observations of our models, mimicking the $(u,v)$ coverage of the data, were carried out using the built-in simulation tasks of CASA." (Modeling)
- **RADEX** : Initial column densities and column-density sensitivities  
  > "We use the online RADEX 1D non-LTE radiative transfer tool" (Estimated column densities)
- **RADMC** : Continuum radiative transfer: dust temperature and SED  
  > "We carried out continuum radiative transfer modeling using the 2D code RADMC" (Modeling details)
- **LIME** : Line radiative transfer of model emission  
  > "to the line radiative transfer code LIME (cite: Brinch:2010)" (Modeling details)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HCO+ J=4-3 integrated flux | 18.7 | 0.7 | Jy km/s | 2 | / HCO$^+$    $J$=4$-$3 / 11.3 / 18.7$\pm$0.7 / 26.0 / |
| DCO+ J=5-4 integrated flux | 2.2 | 0.4 | Jy km/s | 2 | / DCO$^+$    $J$=5$-$4 / 13.1 /   2.2$\pm$0.4 /   1.7 / |
| H13CO+ J=4-3 integrated flux | 1.0 | 0.2 | Jy km/s | 2 | / H$^{13}$CO$^+$ $J$=4$-$3 /   8.2 /   1.0$\pm$0.2 /   1.4 / |
| HCO+ emission ellipse axes / outer radius | 7.8'' x 5.3'', outer radius 475 AU, inclination 47 deg | not stated | arcsec, AU, deg | 2 | Under the assumption of a flat disk these correspond to a disk with an outer radius of 475 AU observed at an inclination of 47$^\circ$ |
| Median H13CO+/HCO+ intensity ratio | 0.18 | not stated | dimensionless | 3 | has a median value of 0.18, confirming the high optical depth of HCO$^+$ with $\tau\approx16$ under the assumption of LTE. |
| HCO+ line-of-sight column density | 2.1e14 | not stated | cm^-2 | 3 | We find line of sight column densities of 2.1$\times10^{14}$ cm$^{-2}$ and 2.8$\times10^{12}$ cm$^{-2}$ for HCO$^+$ and H$^{13}$CO$^+$, respectively. |
| H13CO+ line-of-sight column density | 2.8e12 | not stated | cm^-2 | 3 | We find line of sight column densities of 2.1$\times10^{14}$ cm$^{-2}$ and 2.8$\times10^{12}$ cm$^{-2}$ for HCO$^+$ and H$^{13}$CO$^+$, respectively. |
| DCO+ ring dimensions (integrated map) | outer axes 3.3'' x 2.2'', inner 1.4'' x 1.0''; central radius ~140 AU, width <110 AU | not stated | arcsec, AU | 2 | DCO$^+$ emission is not detected at the stellar position but is confined to an annulus in the integrated emission map with outer major and minor axes of 3.3$''$ and 2.2$''$ |
| Best-fit HCO+ abundance relative to H2 | 3e-10 | not stated (grid step ~factor 3) | relative to H2 | 5 | with a HCO$^+$ abundance of $3\times10^{-10}$, and a corresponding H$^{13}$CO$^+$ abundance of $4\times10^{-12}$ |
| Best-fit DCO+ abundance and temperature range | 1e-10 between 19 K and 21 K | not stated | relative to H2; K | 6 | We find that a $\chi$$_{\rm{DCO^+}}$ of 1$\times$10$^{-10}$  at temperatures between $T_{\rm{high, DCO^+}}$ = 21 K and $T_{\rm{low, DCO^+}}$ = 19 K provides the best fit |
| Local DCO+/HCO+ abundance ratio | up to 0.3 (enhancement >=1e4 over ISM D/H) | not stated | dimensionless | 6 | the relative abundance of DCO$^+$ to HCO$^+$ is as high as 0.3 within the sub-region which lies near 20 K |
| Disk-averaged DCO+/HCO+ ratio | ~0.02 | not stated | dimensionless | 6 | the disk averaged abundance ratio is approximately 0.02 |
| Minimum midplane ionization fraction | 4e-10 (HCO+ + DCO+) | lower limit | dimensionless | 6 | the minimum ionization fraction would be $4\times10^{-10}$ (HCO$^+$ + DCO$^+$) |

## Qualitative findings

- HCO+ and H13CO+ are centrally peaked; DCO+ forms a resolved ring (~110-160 AU) that matches the CO snowline radius of ~155 AU  
  > "DCO$^+$ emission lies in a resolved ring from $\sim$110 to 160 AU." (abstract)

## Claim tuples

- H: DCO+ emission traces the CO snowline in the HD 163296 disk | E: Image DCO+ J=5-4 with ALMA and compare to a disk model with 19 K midplane isotherm | R: DCO+ ring from ~110 to 160 AU; outer edge near the 155 AU snowline | F: ALMA DCO+ data directly resolve and image the CO snowline | **supported**
- H: DCO+ is abundant only in a narrow temperature range near CO freezeout | E: Manual model grid varying T_low, T_high and abundance, compared with channel maps | R: Best fit 19-21 K, chi = 1e-10, DCO+/HCO+ = 0.3 | F: ~1e4 enhancement of DCO+ in a narrow region | **supported**
- H: HCO+ and DCO+ abundances constrain the midplane ionization fraction | E: Sum of modeled abundances | R: Ionization fraction >= 4e-10 | F: Lower limit far above the dead-zone threshold | **supported**
- H: Results depend on the adopted disk structure | E: Refit using the de Gregorio-Monsalvo et al. model | R: 16-20 K, DCO+ abundance ~7e-11, ratio ~0.3 | F: General characteristics unchanged | **supported**

## Reasoning

- Why this data: High luminosity puts the 20 K region at large radius resolvable with ALMA SV data; massive disk gives high DCO+ column  
  > "Due to its high luminosity ($\sim40$ $L_{\odot}$), the 20 K region is at a large radius which can be resolved with science verification data" (Introduction)
- Why this method: _not stated_
- Alternative: Alternative disk structure (de Gregorio-Monsalvo et al.) with lower temperatures and higher densities tested  
  > "the best-fit disk structure of de Gregorio-Monsalvo et al. (in press) has 1–3 K lower temperatures and factor $\sim1.5$ higher densities in the 100 – 150 AU midplane region" (Dependence on physical models)
- How they decided it was enough: _not stated_
- Limitation (authors): Only large-scale structure modeled; the northwest emission peak not modeled  
  > "However, in this work we address the large scale structure, and do not attempt to model variations within that structure." (Morphology)
- Limitation (authors): Results depend on adopted physical model, since CO constrains mainly surface layers  
  > "it is appropriate to investigate the dependence of our results on the details of the adopted physical model" (Dependence on physical models)
- Caveat (inferred, ours): Manual by-eye model fits with no uncertainties or goodness-of-fit statistics
- Caveat (inferred, ours): Parameter degeneracy between temperature bounds, abundance and gas density
- Caveat (inferred, ours): Model overpredicts HCO+ flux (26.0 vs 18.7 Jy km/s) and CO J=3-2 underpredicted
- Caveat (inferred, ours): Constant-abundance, LTE-like assumptions; gas temperature set to dust temperature
- Caveat (inferred, ours): Low S/N of DCO+ (peak ~6 sigma)

## Reproducibility

- Data public (paper): ALMA science verification data, project 2011.0.00010.SV  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00010.SV." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Disk model details in Q11 and in-press papers
- Missing: Calibration and self-cal scripts and CASA version
- Missing: Line-free channel ranges
- Missing: Model cubes and exact fit criterion
- Data volume (inferred): ~10-50 GB (four execution blocks of Band 7 SV data)
- Score (inferred): 3/5, Public SV data and detailed model parameters, but manual fits, unspecified CASA version and reduction details, and dependence on a prior model limit exact reproduction.
- Rediscovery candidate: no, Main results come from manual, by-eye model fitting with an elaborate custom LIME/RADMC pipeline; not readily redone numerically.

## Links

- Method: Qi et al. 2011 (cite: Qi:2011) (Source of the disk physical model and 19 K snowline)
- Method: van der Tak et al. 2007 (cite: van-der-Tak:2007) (RADEX)
- Method: Brinch & Hogerheijde 2010 (cite: Brinch:2010) (LIME)
- Companion: de Gregorio-Monsalvo et al., in press (CO line emission and alternative disk model)
- Companion: Klaassen et al. 2013 (cite: Klaassen:2013qy) (CO emission associated with disk wind)
- Related: ALMA science verification

## Checks

```json
{
 "quotes": 83,
 "quotes_ok": 83,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2011.0.000010.SV"
 ],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 60,
  "rate": 0.698
 },
 "evidence_ok": true
}
```
