# A Radial Decrease in Kinetic Temperature Measured with H<SUB>2</SUB>CO in 30 Doradus

`2024ApJ...969..143I` | The Astrophysical Journal 2024 | first author: Indebetouw, Rémy | arXiv: 2405.07931 | DOI: 10.3847/1538-4357/ad47bf

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, nearby_galaxies, astrochemistry
- Question: Does H2CO-derived gas kinetic temperature in 30 Doradus vary with distance from R136, and which heating mechanisms (mechanical, cosmic ray, X-ray, radiative/photoelectric) explain it?  
  > "H$_2$CO provides a direct measure of gas kinetic temperature, and we find a trend of decreasing temperature with projected distance from R136 that may be indicative of gas heating by the stars." (abstract)
- Target **30 Doradus (R136 region, 30Dor-10 cloud), LMC**: coordinates _not stated_; z/distance not stated (1.75'' = 0.4 pc implied)  
  > "An approximately 60$\;$pc$\times$90pc region of 30$\;$Doradus was observed by ALMA project 2019.1.00843.S between September and December 2019." (2.1 ALMA data); "The center of the 30Dor-10 cloud (cite: johansson), $\sim$20pc north-east of R136, was observed at much higher resolution by project 2013.1.00346.S" (2.1 ALMA data); distance from _not stated_

## Data provenance

- ALMA projects: 2019.1.00843.S, 2013.1.00346.S, 2011.0.00471.S
- bands: H2CO 3-2 lines near 218 GHz plus 232 GHz continuum  
  > "Both datasets include the H$_2$CO transitions listed in Table [1](#tab:transitions), as well as 232$\;$GHz continuum." (2.1 ALMA data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m (used); 7m compared for 2019.1.00843.S  
  > "Only the 12m visibilities were used for the analysis presented here" (2.1 ALMA data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.75'' (0.4 pc) wide-field; 0.46''x0.39'' (0.12 x 0.098 pc) high-res; smoothed to 0.6'' = 0.15 pc  
  > "covers a small central region at 0.46$''$$\times$0.39$''$ = 0.12$\;$pc$\times$0.098$\;$pc resolution." (2.1 ALMA data)
- max recoverable scale: ~2'' = 0.5 pc for high-res data  
  > "the emitting structures are smaller than the $\sim$2$''$=0.5pc largest recoverable scale of the higher resolution data." (2.1 ALMA data)
- sensitivity: 1.75'' cubes: 12 mJy/beam = 0.1 K per channel; 0.6'' cubes: 2.5 mJy/beam = 0.18 K per 0.4 km/s channel  
  > "The resulting images have sensitivity per channel of $\sigma\simeq$12$\;$mJy$\;$bm$^{-1}$=0.1K." (2.1 ALMA data); "rms noise of 2.5$\;$mJy$\;$bm$^{-1}$ = 0.18K per 0.4$\;$km$\;$s$^{-1}$ channel" (2.1 ALMA data)
- time on source: _not stated_
- observing dates: 2019.1.00843.S Sep-Dec 2019; 2013.1.00346.S Jun-Sep 2015  
  > "was observed at much higher resolution by project 2013.1.00346.S between June and Sept 2015" (Data Analysis: ALMA data)
- pi or archival as stated: _not stated_
- Line: H2CO 3_03-2_02 (218.22219 GHz)
- Line: H2CO 3_22-2_21 (218.47532 GHz)
- Line: H2CO 3_21-2_20 (218.76007 GHz)
- Line: 13CO 2-1 (not stated)
- Other facility **SIMBA 1.2mm total power**: Total power continuum to recover diffuse emission  
  > "We used total power SIMBA 1.2mm observations (cite: ferreira) to recover that emission" (2.2 Clump Segmentation)
- External data: 12CO/13CO 2-1 data, 13CO column densities, 12CO excitation temperature, clump properties  
  > "The second panel shows those fitted column densities and the $^{13}$CO column densities determined in (cite: wong22)" (4) [from (cite: wong22)]
- External data: X-ray luminosity of 30 Dor, ~5e36 erg/s  
  > "The overall X-ray luminosity of 30$\;$Doradus of about 5$\times$10$^{36}$erg$\;$s$^{-1}$ (cite: townsley06)" (5) [from (cite: townsley06)]
- External data: gamma-ray energy flux of 30 Dor 4e-11 erg/s/cm2 from Fermi  
  > "to which they attribute a $\gamma$-ray energy flux F$_\gamma$ of 4$\times 10.^{-11}\;$erg$\;s^{-1}\;$cm$^{-2}$" (5) [from (cite: abdo10)]
- External data: Tang et al. LMC H2CO temperatures for N113, N159 and 30Dor pointing  
  > "They found a range of temperatures in N113 of 28-105K (median 49K), and in N159 a range of 29-68K (median 49K)." (4) [from (cite: tang21); (cite: tang17)]
- Simulation/model as data: RADEX non-LTE model grids for H2CO; spubsmi MYSO radiative transfer model grid  
  > "We fit the three H$_2$CO lines using grids of non-LTE models calculated with RADEX (cite: radex)" (3)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline for 2019.1.00843.S; Cycle3R1 pipeline for 2013.1.00346.S  
  > "The data were calibrated with the ALMA data processing pipeline Pipeline-CASA56-P1-B (cite: hunter)" (2.1 ALMA data)
- casa version: CASA 5.6.1-8 (calibration 2019); 4.3.1 (2013 calibration); 6.6.1 and 6.5.4.9 for imaging  
  > "Visibilities were calibrated with the Cycle3R1 ALMA pipeline included in CASA 4.3.1." (2.1 ALMA data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean with auto-multithresh  
  > "using tclean with auto-multithresh auto-masking parameters as used by the ALMA imaging pipeline for 12m data" (2.1 ALMA data)
- deconvolver: _not stated_
- weighting robust: Briggs robust=2 for high-res combination  
  > "imaged in CASA 6.6.1 with Briggs weighting robust=2 (nearly the same as natural weighting)" (2.1 ALMA data)
- uv taper: Gaussian taper 0.37''  
  > "a Gaussian uv taper of" (2.1 ALMA data)
- cell size: 0.5''  
  > "(1 pixel = 0.5$''$)" (2.1 ALMA data)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: continuum: 0, 5, 11, 21 x 0.5'' pixel  
  > "with multi-scale deconvolution at scales of 0,5,11, and 21$\times$ the 0.5$''$ pixel size" (2.2 Clump Segmentation)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 5 tiles imaged separately and mosaicked weighted by sensitivity; continuum feathered with SIMBA  
  > "The region was observed in 5 tiles, each calibrated and imaged separately, and then the 5 images were mosaiced together" (2.1 ALMA data)
- smoothing: _not stated_
- final beam: 0.6'' = 0.15 pc (high-res); 1.75'' (wide)  
  > "the smoothed (slightly) to a 0.6$''$ = 0.15$\;$pc beam" (2.1 ALMA data)
- final rms: _not stated_

### Inherited from earlier work

- Calibration and imaging of 2019.1.00843.S  
  > "The data and their calibration are described in detail in (cite: wong22)." (2.1 ALMA data) [from (cite: wong22)]
- Details and calibration of 2013.1.00346.S  
  > "The details of those data and their calibration are described in (cite: indebetouw20)." (2.1 ALMA data) [from (cite: indebetouw20)]
- Simple line-ratio to TK conversion  
  > "we use the (cite: tang21) "simple" method of converting from line ratio to T at fixed N(H2CO) and n(H2)" (3) [from (cite: tang21)]
- H2/13CO=1e6 abundance  
  > "An assumed abundance ratio of and $H_2$/$^{13}$CO=10$^6$ (cite: indebetouw20)" (4) [from (cite: indebetouw20)]

### Not stated but needed to reproduce (our reading)

- RADEX grid ranges and spacing for n, N, TK, filling factor
- RADEX background and line width settings
- Which filling-factor prior was adopted for final TK values
- Line-free channels and continuum subtraction method for cubes
- Distance to LMC/30 Dor and R136 position used for projected distances
- Fitting range used in the radial trend and the fitted slope and R values
- Stated auto-multithresh parameter values and cleaning thresholds
- Self-calibration status
- Flux calibrator and flux scale uncertainty

## Analysis recipe

1. **Image H2CO cubes and make moment maps**: tclean imaging of 12m visibilities at 1.75'' x 0.5 km/s; integrated intensity with threshold mask I(3_03-2_02)>30 mJy/beam, binary-dilated by 3 pixels  
  > "Integrated intensities were calculated using a threshold mask I(3$_{03}$-2$_{02}$)$>$30mJy$\;$bm$^{-1}$ = 0.25K $\simeq$ 2.5$\sigma$, binary-dilated with a 3-pixel radius" (2.1 ALMA data)
   - software: CASA, tclean
   - fitting: _not stated_
   - validation: 12m flux compared with 7m: 95-100% recovered  
  > "95–100% of the 7m flux is recovered by the higher resolution image" (2.1 ALMA data)
2. **Segment clumps**: astrodendro on 3_03-2_02; boundaries applied to the other two lines  
  > "the H$_2$CO 3$_{03}$-2$_{02}$ emission is segmented into clumps using `astrodendro`, min_value = 3$\sigma$ = 0.3K, min_delta = 2.5$\sigma$ = 0.25K" (2.2 Clump Segmentation)
   - software: astrodendro
   - parameter: min_npix = 1 beam area = 14 square pixels  
  > "min_npix = 1$\;$beam area = 14 square pixels" (2.2 Clump Segmentation)
   - fitting: _not stated_
   - validation: Parameters matter little as only two clumps split into substructure  
  > "The parameters matter very little for subsequent analysis since only two of the clumps break into substructure" (2.2 Clump Segmentation)
3. **Fit non-LTE kinetic temperature per clump**: chi2 over RADEX grids in n, N, TK and filling factor; peak/expectation values of marginalized posteriors  
  > "For each clump of emission, we calculated $\chi^2$ as a function of $H_2$ volume density $n$, H$_2$CO column density $N$, kinetic temperature $T_K$, and beam areal filling factor *ff*." (3)
   - software: RADEX
   - parameter: filling factor restricted to <1  
  > "If fitting a filling factor, it is important to restrict the filling factor to be less than 1." (3)
   - assumption: Para-H2CO only, so no ortho-to-para ratio needed  
  > "the three observed H$_2$CO lines are all para-H$_2$CO, so physical conditions can be constrained without assuming an ortho-to-para ratio." (3)
   - fitting: Grid chi2; flat log priors on physical variables; flat linear or log prior on filling factor  
  > "Flat priors in log space were used for the physical variables, and either a flat prior in linear or in log space for the filling factor." (3)
   - validation: Marginalization methods (4D to 1D) give consistent TK; compared with simple and LTE conversions (~20% differences)  
  > "All of those methods result in consistent $T_K$ within uncertainties" (3)
4. **Map TK in high-resolution data**: Ratio of averaged 3_21 and 3_22 to 3_03 at 0.6'' for pixels >3 sigma, converted with Tang simple prescription  
  > "Temperature was calculated from that ratio using the "simple" prescription of (cite: tang21) at n(H$_2$)=2$\times$10$^5\;$cm$^{-3}$ and N(H$_2$CO)=10$^{13}\;$cm$^{-2}$." (4)
   - assumption: n(H2)=2e5 cm-3, N(H2CO)=1e13 cm-2  
  > "at fixed N(H$_2$CO)=10$^{13}\;$cm$^{-2}$ and n($H_2$)=2$\times$10$^5\;$cm$^{-3}$" (3)
   - fitting: _not stated_
   - validation: Different masking thresholds tested; morphology robust  
  > "the morphology is robust, as are the indications of internal and external heating" (4)
5. **Radial trend and heating mechanism tests**: Linear fit of TK vs projected distance to R136 maximizing Pearson R over distance range; comparison with continuum, nonthermal linewidth, X-ray and cosmic-ray estimates  
  > "The minimum and maximum projected distance were allowed to vary to maximize the significance of the linear fit as quantified by the Pearson’s correlation coefficient $R$." (4)
   - assumption: Hadronic gamma-ray origin for cosmic-ray ionization estimate  
  > "under the hadronic assumption, that $\gamma$-ray emission is primarily due to $\pi^0$ decay from p-p collisions" (5)
   - fitting: _not stated_
   - validation: Slope uncertainty from range choice ±0.5 K/pc  
  > "resulting in an uncertainty of $\pm$0.5$\;$K$\;$pc$^{-1}$." (4)

## Software

- **CASA** 5.6.1-8 (calibration), 4.3.1, 6.6.1, 6.5.4.9 (imaging): Calibration and imaging  
  > "imaged in CASA 6.6.1 with Briggs weighting robust=2" (2.1 ALMA data)
- **tclean** : Imaging with auto-multithresh  
  > "using tclean with auto-multithresh auto-masking parameters" (2.1 ALMA data)
- **astrodendro** : Clump segmentation  
  > "segmented into clumps using `astrodendro`" (2.2 Clump Segmentation)
- **RADEX** : Non-LTE model grids for H2CO  
  > "grids of non-LTE models calculated with RADEX (cite: radex)" (3)
- **sedfitter** : SED fit of MYSO with spubsmi model grid  
  > "We fit the spectral energy distribution of this MYSO with the (cite: rob07) fitter (cite: zenfitter)" (4)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of H2CO clumps in 3_03-2_02 | 53 | not stated | dimensionless | 2 | Fifty-three structures are found in 3$_{03}$-2$_{02}$, and 29 have signal-to-noise greater than 3 |
| TK median of 30Dor clumps | 43 (range 20-100; mean 48) | ±3 K (standard error of mean) | K | 3 | 20-100K, median 43K, mean 48$\pm$3K (standard error of the mean) |
| TK at Tang 2017 pointing | 50 | +17/-13 | K | 3 | we calculate $T_K$=50$^{+17}_{-13}$K |
| Radial TK gradient | decrease from ~60 K to ~20 K over 10-30 pc | slope ±0.5 K/pc | K | 5 | A trend of temperature decreasing from $\sim$60K down to $\sim$20K is found over the projected distance range of 10 to 30pc from R136. |
| MYSO luminosity | log L = 4.7 | ±0.3 | log(Lsun) | 0 | calculate a source luminosity of log(L)=4.7$\pm$0.3$\;$log(L$_\odot$) |
| Cosmic-ray ionization rate | ~2e-15 | order of magnitude | s-1 | 5 | this method derives an estimated $\zeta_I\sim$2$\times$10$^{-15}\;$s$^{-1}$ for the r=60pc 30$\;$Doradus region. |

## Qualitative findings

- No correlation between TK and continuum or nonthermal linewidth; edges of clumps near R136 hotter, consistent with external heating  
  > "Figure [10](#fig:continuum) shows no such correlation, supporting the hypothesis that external heating dominates in this region." (4)

## Claim tuples

- H: Gas kinetic temperature decreases with distance from R136 | E: Non-LTE fits of H2CO line ratios for clumps vs projected distance | R: TK decreases from ~60 to ~20 K over 10-30 pc, no trend beyond 30 pc | F: Consistent with heating by R136 | **supported**
- H: Mechanical heating drives H2CO temperatures | E: Compare TK with nonthermal linewidth and distance | R: No clear correlation | F: Mechanical heating not dominant | **supported**
- H: Heating is external rather than internal to clumps | E: 0.6'' temperature maps and TK vs continuum | R: Higher ratios on edges of clumps near R136; no TK-continuum correlation | F: External heating favored | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: H2CO K-ladder ratios are sensitive to kinetic temperature and weakly to density and column  
  > "should be strongly sensitive to the kinetic temperature, and only weakly to the collider volume density and H$_2$CO column density" (Introduction)
- Alternative: X-ray heating rejected (would raise TK only ≲10K)  
  > "X-ray heating probably does not dominate, and would only raise the temperature to $\lesssim$10K" (5)
- How they decided it was enough: _not stated_
- Limitation (authors): Cosmic ray ionization estimate uncertain by order of magnitude; N(H2CO) poorly constrained  
  > "the conversion of $\gamma$-ray flux to ionization rate is uncertain by an order of magnitude" (5)
- Caveat (inferred, ours): Clumps only marginally resolved at 1.75''; projected not 3D distances
- Caveat (inferred, ours): Radial range chosen to maximize correlation introduces selection bias
- Caveat (inferred, ours): Many TK uncertainties large, some fits unconstrained
- Caveat (inferred, ours): Optical depth, density and filling factor degeneracy

## Reproducibility

- Data public (paper): ALMA projects cited with archive data acknowledgement  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.00843.S and ADS/JAO/ALMA#2013.1.00346.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: RADEX grid definitions
- Missing: Distance and R136 coordinates
- Missing: Details of auto-multithresh and continuum subtraction
- Missing: SIMBA data processing
- Data volume (inferred): ~100-300 GB for the mosaic of 5 tiles plus high-res data
- Score (inferred): 3/5, Public data and a clear analysis chain, but key fitting grid, imaging and distance details are missing, and calibration is delegated to earlier papers.
- Rediscovery candidate: no, Recipe is incomplete for the RADEX fit and imaging; results are numeric but depend on unstated choices.

## Links

- Method: (cite: tang21) (Simple H2CO line-ratio temperature method)
- Method: (cite: wong22) (Calibration and 12CO/13CO analysis of 2019.1.00843.S)
- Companion: (cite: indebetouw20) (Describes 2013.1.00346.S data)
- Related: ALMA 30 Doradus 2019.1.00843.S
- Related: 2011.0.00471.S

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00471.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 53,
  "rate": 0.654
 },
 "evidence_ok": true
}
```
