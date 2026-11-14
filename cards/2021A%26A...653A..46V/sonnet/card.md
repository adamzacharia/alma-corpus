# Probing protoplanetary disk evolution in the Chamaeleon II region

`2021A&A...653A..46V` | Astronomy and Astrophysics 2021 | first author: Villenave, M. | arXiv: 2106.13847 | DOI: 10.1051/0004-6361/202140496

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: How do disk dust masses in Cha II compare with other 1-10 Myr star-forming regions, as a probe of disk evolution?  
  > "We aim to compare the disk dust masses in the Chamaeleon II (Cha II) star-forming region with other regions with ages between 1 and 10 Myr." (abstract)
- Target **Cha II Class II disks (29 sources)**: coordinates per-source in Table 1 (e.g. CM Cha 13 02 13.4 -76 37 57.9)  
  > "Cha II is a close-by region, located at an average distance of 198 pc (cite: Dzib_2018; Galli_2020b)." (Introduction); z/distance ~198 pc average; individual Gaia distances  
  > "Cha II is a close-by region, located at an average distance of 198 pc (cite: Dzib_2018; Galli_2020b)." (Introduction); distance from Gaia DR2/EDR3, Galli_2020b, Dzib_2018  
  > "Cha II is a close-by region, located at an average distance of 198 pc (cite: Dzib_2018; Galli_2020b)." (Introduction)

## Data provenance

- ALMA projects: 2013.1.00708.S
- bands: Band 6 (1.3 mm), mean continuum 225.7 GHz  
  > "giving a mean continuum frequency of 225.7 GHz (1.3 mm)" (2.2 ALMA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 26 to 1170 m, 40 antennas  
  > "with an array configuration made of 40 antennas with baselines ranging from 26 to 1170 m" (2.2 ALMA observations)
- angular resolution: 0.48"x0.25" continuum; 0.51"x0.28" CO  
  > "They achieve an averaged angular resolution of $0.48\ensuremath{''}\times0.25\ensuremath{''}$ ($95\times50$ au)." (2.2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: average continuum RMS 0.17 mJy/beam  
  > "giving an average continuum RMS of 0.17 mJy beam$^{-1}$" (2.2 ALMA observations)
- time on source: 2.5 min per target  
  > "The integration time was 2.5 min on-source per target giving an average continuum RMS of 0.17 mJy beam$^{-1}$." (2.2 ALMA observations)
- observing dates: 2015 August 27  
  > "were obtained on 2015 August 27" (2.2 ALMA observations)
- pi or archival as stated: PI Ménard  
  > "Project 2013.1.00708.S, PI: Ménard" (2.2 ALMA observations)
- Line: 12CO J=2-1 (230.538 GHz)
- Line: 13CO J=2-1 (220.399 GHz)
- Line: C18O J=2-1 (219.56 GHz)
- Other facility **Herschel**: 70 micron fluxes used for sample selection  
  > "selected based on their infrared emission at 70 $\mu$m from *Herschel* observations (cite: Spezzi_2013)" (2.1 Sample)
- Other facility **Gaia DR2/EDR3**: distances and membership  
  > "We checked the membership of each observed target by using distances from *Gaia* data releases" (2.1 Sample)
- External data: Stellar luminosities and temperatures for Cha II  
  > "We used the luminosities determined by (cite: Spezzi_2008), rescaled to the *Gaia* distances." (4.1 Dust masses) [from (cite: Spezzi_2008)]
- External data: Millimeter fluxes of comparison regions (Upper Sco, CrA, IC 348, Cha I, Lupus, Taurus)  
  > "We also recalculated dust masses in a homogeneous way from millimeter or submillimetrer fluxes (cite: Barenfeld_2016; Cazzoletti_2019; Ruiz-Rodriguez_2018; Pascucci_2016; Ansdell_2016; ansdell_2018; Andrews_2013)" (4.2.3 Dust masses) [from (cite: Barenfeld_2016; Cazzoletti_2019; Ruiz-Rodriguez_2018; Pascucci_2016; Ansdell_2016; Andrews_2013)]
- External data: Cha II membership and distances  
  > "we report the individual distances as estimated by (cite: Galli_2020b)" (2.1 Sample) [from (cite: Galli_2020b)]
- Simulation/model as data: Baraffe et al. 2015 pre-main-sequence isochrones used for stellar masses  
  > "using isochrones from (cite: baraffe_2015) in the range 0.5 to 50 Myr" (4.2.2 Stellar masses)

## Processing

### Calibration

- pipeline or manual: Observatory-provided calibration script  
  > "We used the calibration script provided by the observatory, with CASA (cite: McMullin_2007) version 4.3.1, to calibrate the raw data." (2.2 ALMA observations)
- casa version: CASA 4.3.1  
  > "with CASA (cite: McMullin_2007) version 4.3.1" (2.2 ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: typical 10%  
  > "The flux and dust mass uncertainties do not include the typical 10% calibration uncertainty." (Table 2 notes)
- self calibration: Phase-only (inf, spws combined) on 6 sources; DK Cha phase+amp  
  > "we performed a phase-only self-calibration on CM Cha, Hn 22, Hn 23, IRAS12500-7658, Sz 58, and Sz 61." (2.2 ALMA observations)

### Imaging

- task: CASA clean  
  > "by using the CASA `clean` function with a Briggs robust weighting parameter of +0.5" (2.2 ALMA observations)
- deconvolver: _not stated_
- weighting robust: continuum robust +0.5; CO robust 0  
  > "and with a Briggs robust weighting parameter of 0." (2.2 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CASA uvcontsub  
  > "after subtracting the continuum from the spectral windows containing line emission using the `uvcontsub` routine in CASA" (2.2 ALMA observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.48"x0.25" continuum; 0.51"x0.28" CO  
  > "We obtain an average angular resolution of $0.51\ensuremath{''}\times0.28\ensuremath{''}$ ($100\times55$ au) for the CO lines." (2.2 ALMA observations)
- final rms: 0.17 mJy/beam average continuum  
  > "giving an average continuum RMS of 0.17 mJy beam$^{-1}$" (2.2 ALMA observations)

### Inherited from earlier work

- Dust temperature-luminosity relation T=25K(L/Lsun)^1/4  
  > "We also adopted the relationship of $T_\mathrm{dust}$ with $L_\star$ from (cite: Andrews_2013)" (4.1 Dust masses) [from (cite: Andrews_2013)]
- Opacity 2.3 cm2/g at 230 GHz, kappa ∝ nu^0.4  
  > "We assumed a grain opacity $\kappa_\nu$ of $2.3\ \mathrm{cm}^2.\mathrm{g}^{-1}$ at 230 GHz (cite: Beckwith_1990)" (4.1 Dust masses) [from (cite: Beckwith_1990)]
- Stellar mass likelihood method and mass-bin logrank test  
  > "following the methodology of (cite: Andrews_2013)" (4.3 Statistical test) [from (cite: Andrews_2013; Pascucci_2016)]

### Not stated but needed to reproduce (our reading)

- Continuum and line-free channel ranges for continuum imaging and uvcontsub
- Image size, cell size, clean threshold, masks and number of iterations
- Primary beam correction details
- Initial uvmodelfit starting parameters
- Random binning/draw details for 10^4 Monte Carlo logrank test
- Final stellar parameter tables for comparison regions

## Analysis recipe

1. **Measure continuum flux and size**: Elliptical Gaussian fit to visibilities; point source if size/uncertainty<5  
  > "We measured the continuum emission by fitting an elliptical Gaussian model to the visibility data, using the CASA `uvmodelfit` task." (3.1 Continuum emission)
   - software: CASA
   - parameter: 3 sigma detection threshold  
  > "Out of 31 sources, 24 are detected above a 3$\sigma$ significance threshold." (3.1 Continuum emission)
   - assumption: Disks azimuthally symmetric for inclination  
  > "estimated from $r$ assuming that the disks are azimuthally symmetric" (3.1 Continuum emission)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure CO line fluxes**: Integrate line profiles over channels with >3 sigma; upper limits 3 RMS over 6.3 km/s  
  > "They correspond to three times the RMS of the line profile, integrated over a line width of 6.3 km s$^{-1}$." (3.2 CO line emission)
   - software: CASA immoments
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive dust masses**: Optically thin M=F d^2/(kappa B(Tdust))  
  > "Assuming that the continuum emission is optically thin at 1.3 mm, it is possible to infer the disk dust mass" (4.1 Dust masses)
   - parameter: kappa=2.3 cm2/g at 230 GHz; Tdust=25K(L/Lsun)^1/4; 20 K if no luminosity  
  > "we applied a characteristic dust temperature of T$_\mathrm{dust}=20$ K (cite: Andrews_Williams_2005)" (4.1 Dust masses)
   - assumption: Optically thin emission; individual Gaia distances, else 198 pc  
  > "we used the average distance of the well characterized objects: 198 pc" (4.1 Dust masses)
   - fitting: _not stated_
   - validation: Tested T=20 K and kappa ∝ nu opacity alternatives  
  > "We checked that using either opacity law does not significantly affect the results." (4.2.3 Dust masses)
4. **Homogeneous stellar masses for all regions**: Likelihood on Baraffe 2015 isochrone grid, marginalized for median and percentiles  
  > "We then marginalized the distribution to estimate the stellar masses and their uncertainties" (4.2.2 Stellar masses)
   - parameter: sigma log L=0.1, sigma log T=0.02; 0.05-1.4 Msun in 0.01 steps  
  > "assuming that the uncertainties in $\log (\mathrm{L}_\star / \mathrm{L}_\odot )$ and $\log (\mathrm{T}_\star/K)$ are 0.1 and 0.02, respectively" (4.2.2 Stellar masses)
   - fitting: Likelihood grid (Andrews 2013)  
  > "We first evaluated a likelihood function (cite: Andrews_2013) on each grid model, assuming that the uncertainties in $\log (\mathrm{L}_\star / \mathrm{L}_\odot )$ and $\log (\mathrm{T}_\star/K)$ are 0.1 and 0.02" (Disk properties, Comparison with other regions, Methods, Stellar masses)
   - validation: _not stated_
5. **Cumulative distributions with censoring**: Kaplan-Meier estimator for Mdust and Mdust/Mstar  
  > "We used the Kaplan-Meier estimator in the `l`ifelines package in Python" (4.2.5 Cumulative distributions)
   - software: lifelines
   - fitting: _not stated_
   - validation: Repeated with common mass limit 1.52 Mearth  
  > "we performed the analysis considering a common dust mass limit." (Appendix)
6. **Compare regions statistically**: Logrank test on Mdust/Mstar; logrank on Mdust in 5 stellar mass bins with 10^4 resamplings  
  > "This process is repeated $10^4$ times for each compared region." (4.3 Statistical test)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3.1: calibration, clean, uvcontsub, uvmodelfit, immoments  
  > "with CASA (cite: McMullin_2007) version 4.3.1, to calibrate the raw data" (2.2 ALMA observations)
- **lifelines** : Kaplan-Meier estimator  
  > "We used the Kaplan-Meier estimator in the `l`ifelines package in Python" (4.2.5 Cumulative distributions)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum detections | 22 of 29 disks (24 of 31 sources) | not stated | sources | 1 | we detect 22 sources in the continuum, 10 in $^{12}$CO, 3 in $^{13}$CO, and none in C$^{18}$O (J=2-1) |
| Median dust mass Cha II | 4.5 | 1.5 | M_earth | 5 | we derive a median dust mass of $4.5 \pm 1.5$ M$_\oplus$ from survival analysis |
| Median Mdust/Mstar Cha II | 3.1e-5 | 1.5e-5 | dimensionless | 5 | / Cha II / 1 $-$ 2$^{(d)}$, 2 $-$ 6$^{(c)}$ / 198 $\pm$ 6$^{(k)}$ / 225.7 / 0.65 / 18/22 / 4.5 $\pm$ 1.5 / 3.1 $\pm$ 1.5 / |
| Dust mass of IRAS12496-7650 | 337.5 | 0.1 | M_earth | 3 | / IRAS12496-7650 / 708.6 $\pm$ 0.3 / 354 $\pm$ 1 / 25 $\pm$ 1 / 125 $\pm$ 1 / 337.5 $\pm$ 0.1 / |
| Median p-values in mass-bin test vs Cha II | Taurus 0.22, Lupus b6 0.40, Lupus b7 0.31, Cha I 0.47, IC 348 0.54, CrA 0.08, Upper Sco 0.56 | not stated | dimensionless | 6 | We find median $p_\phi$ values of 0.22, 0.40, 0.31, 0.47, 0.54, 0.08, and 0.56 |

## Qualitative findings

- 12CO emission is systematically larger than the continuum  
  > "we find that the $^{12}$CO emission is systematically larger than its continuum counterpart" (3.2 CO line emission)
- Hn 24 B is a new companion candidate  
  > "Hn 24 B is a new companion candidate, since it is not referenced in the literature." (3.1 Continuum emission)

## Claim tuples

- H: Cha II dust-to-stellar mass ratios differ from other regions of different age | E: Kaplan-Meier and logrank tests of Mdust/Mstar across seven regions | R: Cha II differs from Taurus; Upper Sco less massive than all others | F: Consistent with decline of dust mass with time or dust evolution | **partially**
- H: Dust mass distributions in matched stellar mass bins differ between regions | E: Monte Carlo logrank test in 5 mass bins | R: No statistical differences with Cha II | F: Minor differences prevent strong conclusions | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Dust-to-stellar mass ratio reduces the effect of different stellar mass distributions  
  > "Using this ratio allows us to reduce the impact of potentially different M$_\star$ distributions" (4.2 Comparison with other regions)
- Alternative: Serpens SMA survey excluded for incompleteness and low sensitivity  
  > "both because less than half of the known Class II population of this region was observed" (4.2.1 Sample)
- How they decided it was enough: _not stated_
- Limitation (authors): Optically thin assumption may underestimate masses  
  > "they find that the analytical masses are generally underestimated (by a factor of one to five)" (4.4 Possible limitations)
- Limitation (authors): Cloud absorption and filtering affect CO fluxes  
  > "The presence of significant cloud absorption indicates that the CO fluxes presented in Table 1 and the average line width of the profiles can be underestimated." (3.2 CO line emission)
- Caveat (inferred, ours): Cha II age ambiguous (1-2 vs 4 Myr) drives interpretation
- Caveat (inferred, ours): Kaplan-Meier ignores uncertainties on censored values
- Caveat (inferred, ours): Heterogeneous comparison samples and frequencies
- Caveat (inferred, ours): Short snapshot sensitivity with small sample

## Reproducibility

- Data public (paper): ALMA project cited with acknowledgment; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00708.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters (size, cell, thresholds, channels)
- Missing: Comparison-region stellar parameter inputs
- Missing: Random seed and binning for Monte Carlo test
- Data volume (inferred): ~20-50 GB raw for one 2.5 min/target survey
- Score (inferred): 3/5, Single public dataset and clear dust mass recipe, but imaging details and comparison-sample inputs are incomplete.
- Rediscovery candidate: yes, Public data, explicit uvmodelfit and mass formulas, numeric tabulated results.

## Links

- Method: Andrews et al. 2013 (Dust temperature relation, stellar mass method, mass-bin test)
- Companion: Galli et al. 2021 (Cha II membership, distances and age)
- Related: Lupus ALMA survey
- Related: Upper Sco ALMA survey
- Related: Cha I ALMA survey

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 52,
  "rate": 0.634
 },
 "evidence_ok": true
}
```
