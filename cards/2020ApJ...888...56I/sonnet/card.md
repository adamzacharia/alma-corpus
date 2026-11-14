# Structural and Dynamical Analysis of 0.1 pc Cores and Filaments in the 30 Doradus-10 Giant Molecular Cloud

`2020ApJ...888...56I` | The Astrophysical Journal 2020 | first author: Indebetouw, Rémy | arXiv: 1912.11515 | DOI: 10.3847/1538-4357/ab5db7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, nearby_galaxies
- Question: Do 0.1 pc cores and filaments in the 30Dor-10 cloud in the LMC resemble those in other clouds in structure, dynamics, stability and mass function, given strong external feedback from R136?  
  > "To develop any universal understanding of star formation it is important to determine whether the same core and filament structures exist in a wider range of molecular clouds than exist in the solar neighborhood." (Introduction)
- Target **30Dor-10 molecular cloud (LMC)**: coordinates _not stated_; z/distance 50 kpc  
  > "The 30Dor-10 molecular cloud (cite: johansson98) is located 15pc to the NE of the rich star cluster R136 in the LMC." (Introduction); "at the adopted distance of 50 kpc (cite: distance)" (Introduction); distance from de Grijs et al. 2014 (cite: distance)  
  > "The 30Dor-10 molecular cloud (cite: johansson98) is located 15pc to the NE of the rich star cluster R136 in the LMC." (Introduction); "at the adopted distance of 50 kpc (cite: distance)" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00471.S
- bands: _not stated_
- frequencies and spectral setup: C18O and H2CO at 122 kHz = 168 m/s; 12CO and 13CO 2-1 at 61 kHz ~ 80 m/s  
  > "(C$^{18}$O$\;$2-1 and the H$_2$CO lines were observed at 122 kHz=168 m/s resolution, $^{12}$CO$\;$2-1 and $^{13}$CO$\;$2-1 at 61 kHz$\simeq$80 m/s resolution.)" (2 Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Cycle 0: 2.3'' x 1.5'' (0.56 x 0.36 pc); Cycle 2 12CO/13CO: 0.31'' x 0.22'' (0.08 x 0.05 pc); C18O: 0.44'' x 0.28''  
  > "achieving a beam of" (2 Observations and Data Reduction); "The C$^{18}$O$\;$2-1 data were imaged at 0.4 km s$^{-1}$ resolution with natural weighting, achieving a beam of 0.44 $\ensuremath{''}\times$0.28 $\ensuremath{''}$ and rms = 1.6 mJy bm$^{-1}$" (2 Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 2.3 mJy/beam (12CO, 13CO, line-free channels); 6 mJy/beam after feathering 12CO; 1.6 mJy/beam C18O  
  > "rms noise in line-free channels of 2.3mJy$\;$bm$^{-1}$" (2 Observations and Data Reduction); "the combined image used for subsequent analysis has an rms of 6mJy bm$^{-1}$" (2 Observations and Data Reduction)
- time on source: _not stated_
- observing dates: 7 executions between 2015/06/27 and 2015/09/24 (project 2013.1.00346)  
  > "The observation was executed 7 times between 2015/06/27 and 2015/09/24." (2 Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: 12CO 2-1 (not stated)
- Line: 13CO 2-1 (not stated)
- Line: C18O 2-1 (not stated)
- Line: H2CO 3_0,3-2_0,2, 3_2,2-2_2,1, 3_2,1-2_2,0 (218.22219, 218.47563, 218.76007 GHz)
- Other facility **APEX**: Single-dish 12CO 2-1 data used to feather with ALMA  
  > "The $^{12}$CO$\;$2-1 image was feathered with APEX single dish data" (2 Observations and Data Reduction)
- Other facility **HST (HTTP)**: Optical/near-IR images for comparison  
  > "relative to optical and near-infrared emission imaged with HST for the HTTP project (cite: sabbi)" (3 CO morphology and associated star formation)
- External data: Size-linewidth data for N159 and other clouds; Galactic SRBY relation, Perseus A structures  
  > "Also shown in Figure [10](#sizelinefig) are the relation fit to Galactic molecular clouds $\delta v$=0.72$\;$R$^{0.5}$ (cite: heyer09; srby)" (4.5 size-linewidth-flux relations) [from heyer09; srby; ridge06; saigo17; tokuda18; fukui15; fukui18]
- External data: Interclump pressure estimate 3e6 cm^-3 K  
  > "In Paper I we used the formula of (cite: bertoldi92) to estimate that interclump pressure to be 3$\times$10$^6$cm$^{-3}$K" (4.5 size-linewidth-flux relations) [from Indebetouw et al. 2013 (cite: ri13)]
- Simulation/model as data: Radex non-LTE grid used to test LTE column density recovery  
  > "we ran a grid of non-LTE excitation models with Radex (cite: radex)" (4.2 Mass calculation)

## Processing

### Calibration

- pipeline or manual: ALMA Calibration pipeline Cycle3R1 in CASA 4.3.1  
  > "Data were calibrated using the ALMA Calibration pipeline version Cycle3R1 included in Common Astronomy Software Applications (CASA; <http://casa.nrao.edu>) v. 4.3.1 (cite: casa)." (2 Observations and Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0519-454 (amplitude calibrator)  
  > "The amplitude calibrator was J0519-454 (0.66-1.0 Jy at 230.5 GHz)." (2 Observations and Data Reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean in CASA 4.5 with prototype auto-multithresh  
  > "deconvolved using `clean`, `tclean` in CASA 4.5, and a prototype version of the auto-multithresh automasking routine now included in CASA (cite: kepley20)" (2 Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: 12CO/13CO: Briggs robust=0.5; C18O: natural  
  > "imaged at 0.4 km s$^{-1}$ resolution with Briggs weighting, robust=0.5" (2 Observations and Data Reduction)
- uv taper: _not stated_
- cell size: 0.032 arcsec  
  > "multi-scale deconvolution at 0,5, and 9 times the 0.032$\;$arcsec pixel" (2 Observations and Data Reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: 0, 5, 9 times the 0.032 arcsec pixel  
  > "multi-scale deconvolution at 0,5, and 9 times the 0.032$\;$arcsec pixel" (2 Observations and Data Reduction)
- continuum subtraction: in the uv domain  
  > "Calibrated visibilities were subsequently continuum-subtracted in the uv domain" (2 Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Visibilities from both projects jointly deconvolved; 12CO feathered with APEX  
  > "Visibilities from both projects were included in the deconvolution." (2 Observations and Data Reduction)
- smoothing: _not stated_
- final beam: 0.31'' x 0.22'' (12CO, 13CO); 0.44'' x 0.28'' (C18O)  
  > "The C$^{18}$O$\;$2-1 data were imaged at 0.4 km s$^{-1}$ resolution with natural weighting, achieving a beam of 0.44 $\ensuremath{''}\times$0.28 $\ensuremath{''}$ and rms = 1.6 mJy bm$^{-1}$" (2 Observations and Data Reduction)
- final rms: _not stated_

### Inherited from earlier work

- LTE mass method follows Bourke 1997 and Paper I  
  > "using what is sometimes referred to as the LTE or “standard” method (cite: bourke97; ri13)" (4.2 Mass calculation) [from (cite: bourke97; ri13)]
- Filament finding via filfinder; filament pruning parameters per its documentation  
  > "(see `filfinder` documentation for parameter descriptions)" (4.1 Methods) [from filfinder (cite: filfinder)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum subtraction and rms
- Exact feathering procedure and APEX data details
- Rest frequencies for CO lines and exact velocity range used
- Moment-masking / noise cutoffs for LTE mass cubes
- quickclump/cprops parameters (dT, Tmin, Iminpk) for the final core catalogue
- Dendrogram parameters (min_value, min_delta, min_npix)
- Details of the 12CO/13CO abundance and 13CO/H2 assumption (text gives both 5e5 and 5e6)
- Executions' array configurations and baselines
- Cycle 0 data processing details

## Analysis recipe

1. **Calibrate and image ALMA data**: Pipeline calibration, uv continuum subtraction, tclean multiscale with auto-multithresh; feather 12CO with APEX  
  > "deconvolved using `clean`, `tclean` in CASA 4.5, and a prototype version of the auto-multithresh automasking routine now included in CASA (cite: kepley20)" (2 Observations and Data Reduction)
   - software: CASA
   - parameter: 0.4 km/s channels, robust=0.5, scales 0,5,9 pixels  
  > "imaged at 0.4 km s$^{-1}$ resolution with Briggs weighting, robust=0.5" (2 Observations and Data Reduction)
   - fitting: _not stated_
   - validation: 13CO ALMA vs APEX comparison shows all emission recovered  
  > "Comparison of the ALMA and APEX data for $^{13}$CO$\;$2-1 indicates that the interferometer recovered all emission to within uncertainties" (2 Observations and Data Reduction)
2. **Compute LTE column density and mass**: Tex from 12CO 2-1 brightness, 13CO optical depth and column density, assuming Tex(13CO)=Tex(12CO)  
  > "The $^{13}$CO excitation temperature is assumed to be the same as $^{12}$CO$\;$2-1, to calculate the $^{13}$CO optical depth and column density." (4.2 Mass calculation)
   - software: Radex
   - assumption: H2/13CO = 5e5 (grid test); N(12CO)=75 N(13CO)  
  > "corresponding to line-of-sight pathlength $<$1pc for an abundance H$_2$/$^{13}$CO=5$\times$10$^5$" (4.2 Mass calculation)
   - fitting: _not stated_
   - validation: Radex grid shows LTE method works fairly well; bright structures overestimated up to factor 2  
  > "There is a modest effect that the calculated column density (and mass) of bright structures may be overestimated by up to a factor of 2 relative to faint structures." (4.2 Mass calculation)
3. **Segment emission into cores, hierarchical structures and filaments**: quickclump (clumpfind-type), astrodendro, filfinder on the peak intensity image; filaments matched to elongated dendrogram structures  
  > "we match filament branches to elongated dendrogram entities." (4.1 Methods)
   - software: quickclump, cpropstoo, astrodendro, filfinder
   - parameter: filfinder global threshold 0.17 (12CO) and 0.07 (13CO) of peak; flatten at 90%; smooth 3 beamwidths; size threshold 24 beam areas; adaptive threshold 14 beamwidths; prune 5 beams and 10 pixels; aspect ratio >2.5:1, area 0.2-0.5 pc^2  
  > "Filaments are found using a global threshold of 0.17 and 0.07 times the peak intensity for $^{12}$CO and $^{13}$CO, respectively." (4.1 Methods)
   - fitting: _not stated_
   - validation: Visual check; 3D vs 2D pruning gives only minor differences  
  > "Our trials found that the final filament skeletons differ only in minor ways between the default 3D pruning and pruning based on 3D lengths" (4.1 Methods)
4. **Filament velocity gradients, line mass, stability and width**: Moment-1 gradient vs filament direction; line mass from Gaussian fit to perpendicular profile or integrated N, compared with critical line mass 2sigma^2/G with thermal and nonthermal support  
  > "Unmagnetized isothermal filaments with line mass i.e. mass per unit length $M_l > 2\sigma^2/G$ are unstable to gravitational collapse" (4.4 Structure analysis result: filament stability)
   - software: filfinder
   - parameter: mu = 2.36 m_H; sigma_v over cube within 5 km/s of filament peak velocity  
  > "where $\mu$ is the mean molecular mass 2.36$m_H$" (4.4 Structure analysis result: filament stability)
   - assumption: abundance n(H2)/n(13CO) = 5e6 used here  
  > "5$\times$10$^6$ was used here" (4.4 Structure analysis result: filament stability)
   - fitting: Gaussian fits to perpendicular profiles  
  > "We fit a Gaussian of width $\sigma_r$ to the profile of $^{12}$CO$\;$2-1 intensity" (4.4 Structure analysis result: filament stability)
   - validation: _not stated_
5. **Size-linewidth-surface density and boundedness**: Power-law fit of size-linewidth for dendrogram and clumpfind structures; Sigma_LTE vs Sigma_vir with virial mass 5 sigma_v^2 R/G and external pressure curves  
  > "$\Sigma_{LTE}$ is calculated from the LTE mass, and $\Sigma_{vir}$ from the virial mass 5$\sigma_v^2$R/G." (4.5 size-linewidth-flux relations)
   - software: Kapteyn
   - parameter: radius = 1.91 x second moment, deconvolved for resolution  
  > "The “radius” plotted is the historical value of 1.91 times the second moment in the plane of the sky" (4.5 size-linewidth-flux relations)
   - fitting: Levenberg-Marquardt least squares (Kapteyn)  
  > "The relation is fit to a power-law with the Levenberg-Marquardt least-squares fitter in the Kapteyn package (cite: kapteyn)." (4.5 size-linewidth-flux relations)
   - validation: _not stated_
6. **Core mass/luminosity function**: clumpfind cores; Hill maximum-likelihood power-law fit and weighted linear fit to cumulative/differential distributions  
  > "we show both the Hill maximum likelihood estimator with its statistical uncertainty (dashed lines), as well as a simple linear fit to the log number $n$, weighted by $n^{-0.3}$" (4.6 Core mass function)
   - software: cprops, clumpfind
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3.1 (calibration); 4.5 (imaging): Calibration and imaging  
  > "deconvolved using `clean`, `tclean` in CASA 4.5" (2 Observations and Data Reduction)
- **quickclump** : Clump segmentation, with added Iminpk parameter  
  > "we use the `quickclump` python implementation" (4.1 Methods)
- **astrodendro** : Dendrogram structures  
  > "For dendrograms we use the python implementation at <https://github.com/dendrograms/astrodendro>." (4.1 Methods)
- **filfinder** : Filament identification  
  > "We use `filfinder` (cite: filfinder)" (4.1 Methods)
- **Radex** : Non-LTE grid to test LTE column density  
  > "we ran a grid of non-LTE excitation models with Radex (cite: radex)" (4.2 Mass calculation)
- **Kapteyn** 2.3: Power-law fitting of size-linewidth  
  > "Levenberg-Marquardt least-squares fitter in the Kapteyn package (cite: kapteyn)" (4.5 size-linewidth-flux relations)
- **cpropstoo** : Moments calculation of clump properties  
  > "Properties (moments, fitted sizes, etc) of clumps are calculated with a python translation of the moments calculations in `cpropstoo`" (4.1 Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median filament width | 0.09 | standard deviation 0.06 | pc | 4 | The median width is 0.09pc, with standard deviation of 0.06pc |
| Size-linewidth slope (30Dor-10) | 0.75 | 0.05 | dimensionless | 5 | The slope of 0.75$\pm$0.05 is somewhat steeper than the theoretical slope of 0.5 |
| N159 linewidth offset below 30Dor-10 | 0.33 | 0.05 | dex | 5 | the linewidth at a given scale is 0.33$\pm$0.05 dex lower |
| 12CO luminosity function slope | 1.7 | 0.2 | dimensionless | 6 | The bright end is fit with a power law of slope $\alpha$=1.7$\pm$0.2. |
| Differential core mass function slope | -1.3 | 0.15 | dimensionless | 6 | The best estimate slope of -1.3$\pm$0.15 is consistent with the stellar IMF slope -1.35. |
| Mean Sigma_LTE difference dendrogram vs clumpfind | 0.8 (0.5 with clipping) | not stated | dex | 5 | the mean difference of $\Sigma_{LTE}$ between `dendrogram` and `clumpfind` structures is 0.8dex without clipping, and decreases to 0.5dex when clipping is used |

## Qualitative findings

- Filaments are oriented towards R136 and most show no embedded star formation  
  > "a series of parsec-long filaments oriented almost directly towards R136, most of which don’t show signs of embedded star formation" (5 Conclusions)
- Velocity gradients show no strong evidence for accretion along filaments  
  > "accretion along filaments, although it may be present, does not dominate over the stochastic turbulent velocity motions in the cloud" (4.3 Structure analysis result: filament velocity structure)

## Claim tuples

- H: Is kinetic energy elevated in 30Dor-10 relative to other regions? | E: Size-linewidth relation for dendrogram structures compared with N159, Milky Way and Perseus A | R: Slope 0.75±0.05; linewidths higher by 0.33 dex than N159 and 0.65 dex than SRBY relation | F: Elevated kinetic energy consistent with large-scale energy injection | **supported**
- H: Are 30Dor-10 filaments like solar neighborhood filaments? | E: Measured filament widths from perpendicular profiles | R: Median width 0.09 pc | F: Widths consistent with ~0.1 pc | **supported**
- H: Are structures gravitationally bound? | E: Boundedness plots and critical line mass | R: Clumpfind entire objects near virial/free-fall; dendrogram parts and many filament points above equilibrium | F: Inferred balance depends on segmentation method | **supported**
- H: Does the core mass function match the IMF? | E: Power-law fits to the core mass distribution | R: Slope -1.3±0.15 vs IMF -1.35 | F: Upper end consistent with IMF slope | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Segmentation algorithms have different biases, so several (clumpfind, dendrogram, filfinder) are used and compared  
  > "It is important to note the bias of the various algorithms" (4.1 Methods)
- Alternative: 3D pruning in filfinder tested but only the default 2D results presented  
  > "so here we present only the default 2D results using the publicly available code" (4.1 Methods)
- How they decided it was enough: _not stated_
- Limitation (authors): Systematic uncertainty from 13CO abundance could move most points into the stable regime  
  > "There is a systematic uncertainty in $M_l$ depending on the choice of abundance ratio $n(H_2)/n(^{13}CO)$." (4.4 Structure analysis result: filament stability)
- Caveat (inferred, ours): Abundance assumption is stated inconsistently (5e5 vs 5e6)
- Caveat (inferred, ours): Results depend strongly on segmentation parameters, which are largely unlisted
- Caveat (inferred, ours): Spitzer resolution prevents robust association with star formation
- Caveat (inferred, ours): Filament finding on 2D peak intensity image may miss multi-velocity structure

## Reproducibility

- Data public (paper): Project codes given and cited in the acknowledgments  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00471.S, ADS/JAO.ALMA#2013.1.00346" (Software)
- Products in archive: _not stated_
- Code: Modified quickclump and FilFinder released on GitHub (indebetouw forks)  
  > "(<https://github.com/indebetouw/quickclump>)" (4.1 Methods)
- Missing: Prototype auto-multithresh settings
- Missing: Clumpfind/dendrogram parameters for each figure
- Missing: Feathering details
- Missing: Stated abundance inconsistency
- Data volume (inferred): ~100s of GB raw across two projects
- Score (inferred): 3/5, Data are public and many filfinder parameters are given, but key segmentation parameters, feathering and masking are unstated.
- Rediscovery candidate: no, The recipe is incomplete (segmentation parameters, auto-multithresh prototype, feathering) and requires the heavy combined-project imaging.

## Links

- Method: Koch & Rosolowsky 2015 (cite: filfinder) (filfinder algorithm)
- Method: Rosolowsky et al. 2008 (cite: dendro) (dendrograms)
- Method: Rosolowsky & Leroy 2006 (cite: cprops) (cprops/clumpfind property calculations)
- Method: Kepley et al. 2020 (cite: kepley20) (auto-multithresh masking)
- Companion: Indebetouw et al. 2013 (cite: ri13) (Paper I: Cycle 0 ALMA observations of 30Dor-10)
- Related: HTTP (Hubble Tarantula Treasury Project)
- Related: SAGE Spitzer survey

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00346.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 54,
  "rate": 0.628
 },
 "evidence_ok": true
}
```
