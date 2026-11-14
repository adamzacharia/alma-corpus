# Tracing Embedded Stellar Populations in Clusters and Galaxies Using Molecular Emission: Methanol as a Signature of the Low-mass End of the IMF

`2015ApJ...807L..25K` | The Astrophysical Journal Letters 2015 | first author: Kristensen, Lars E. | arXiv: 1506.04160 | DOI: 10.1088/2041-8205/807/2/L25

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: star_formation, astrochemistry
- Question: Can methanol 338.4 GHz outflow emission from modeled embedded low-mass protostars reproduce the observed extended methanol emission in a high-mass cluster, tracing the low-mass population?  
  > "We here present a model of a forming cluster where methanol emission is assigned to every embedded low-mass protostar." (abstract)
- Target **IRAS16547-4247**: coordinates _not stated_; z/distance 2.9 kpc  
  > "The region is located at a distance of 2.9 kpc and was observed at an angular resolution of $\sim$ 0.5$''$ (1500 AU)." (5.1 Comparison to ALMA observations of IRAS16547–4247); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.5'' (1500 AU)  
  > "was observed at an angular resolution of $\sim$ 0.5$''$ (1500 AU)" (5.1 Comparison to ALMA observations of IRAS16547–4247)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival data downloaded from the Science Archive; originally presented by Higuchi et al.  
  > "The data were downloaded from the Science Archive." (5.1 Comparison to ALMA observations of IRAS16547–4247)
- Line: CH3OH 7_0–6_0 A+ (338.409 GHz)
- Other facility **JCMT HARP**: 338 GHz methanol maps of NGC1333 and Serpens Main used as outflow templates  
  > "both mapped with the James Clerk Maxwell Telescope (JCMT) at 338 GHz" (2.2 Outflow emission characteristics)
- External data: Serpens methanol data and reduction  
  > "The Serpens data are presented in (cite: kristensen10a) where also the data reduction is described in detail." (2.2 Outflow emission characteristics) [from (cite: kristensen10a)]
- External data: Envelope masses and bolometric luminosities of template sources  
  > "From (cite: kristensen12), except for S68N which is from (cite: kristensen10a)." (Table 1) [from (cite: kristensen12)]
- External data: Class fractions from Perseus  
  > "The fraction of protostars in the Class I, II and III stages as well as the “flat-spectrum” stage between Class I and II are taken from (cite: evans09)" (2.1 Cluster characteristics) [from (cite: evans09)]
- Simulation/model as data: Monte Carlo cluster model with 3000 protostars, 1 Myr, at 3 kpc, convolved with 0.5'' beam  
  > "For a cluster with 3000 protostars and an age distribution of the low-mass population corresponding to that of Perseus, i.e. 1 Myr" (3 Results)

## Processing

### Calibration

- pipeline or manual: Pipeline-calibrated visibilities used  
  > "The pipeline-calibrated visibilities were were first continuum-subtracted using line-free channels" (5.1 Comparison to ALMA observations of IRAS16547–4247)
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
- masking: Iterative clean mask starting at peak intensity and expanding  
  > "the clean mask was iteratively placed so that cleaning started at the peak intensity and expanded from there" (5.1 Comparison to ALMA observations of IRAS16547–4247)
- multiscale scales: _not stated_
- continuum subtraction: uv-plane subtraction using line-free channels  
  > "continuum-subtracted using line-free channels in the $uv$ spectrum and then re-imaged" (5.1 Comparison to ALMA observations of IRAS16547–4247)
- line free channels: _not stated_
- primary beam correction: Applied for quantitative analysis; not for display  
  > "For the more quantitative analysis, see below, primary-beam-corrected data are used." (5.1 Comparison to ALMA observations of IRAS16547–4247)
- array combination: _not stated_
- smoothing: Visibilities averaged over –44 to –20 km/s before imaging  
  > "the visibilities were averaged over a spectral region corresponding to velocities from –44 to –20 km s$^{-1}$ prior to imaging" (5.1 Comparison to ALMA observations of IRAS16547–4247)
- final beam: _not stated_
- final rms: 0.07 Jy km/s/beam  
  > "a decrease in noise level of a factor of 2 to 0.07 Jy km s$^{-1}$ beam$^{-1}$" (5.1 Comparison to ALMA observations of IRAS16547–4247)

### Inherited from earlier work

- Baseline pipelined image of the ALMA data  
  > "two changes were made compared to the pipelined image presented in (cite: higuchi14)" (5.1 Comparison to ALMA observations of IRAS16547–4247) [from (cite: higuchi14)]
- Spatial distribution parameters  
  > "The spatial distribution of protostars builds on the model by (cite: adams14)" (2.1 Cluster characteristics) [from (cite: adams14)]
- Chabrier IMF  
  > "The initial mass function (IMF) follows that defined in (cite: chabrier03)" (2.1 Cluster characteristics) [from (cite: chabrier03)]

### Not stated but needed to reproduce (our reading)

- ALMA project code, CASA version, robust/weighting, cell and image size
- Line-free channel selection
- Model random seed and number of realizations
- Radial profile center definition and bin widths
- Primary beam model used in simulated image

## Analysis recipe

1. **Build template cluster**: Sample positions, ages, IMF masses for 3000 stars; scale Class 0/I core masses  
  > "The initial mass function (IMF) follows that defined in (cite: chabrier03) for young clusters and disk stars and is randomly sampled over the mass interval from 0.01–100 $M_\odot$" (2.1 Cluster characteristics)
   - parameter: R0=1 pc, N0=300, alpha=1/3, p=1.5  
  > "This relation works well with $R_0$=1 pc, $N_0$=300 and $\alpha=1/3$" (2.1 Cluster characteristics)
   - fitting: _not stated_
   - validation: _not stated_
2. **Calibrate methanol flux vs envelope mass**: Correlate integrated intensity with envelope mass from JCMT maps; t test  
  > "The proportionality is $S$ = (78$\pm$33) $M_{\rm env}$ Jy km s$^{-1}$ $M_\odot^{-1}$ where the uncertainty is 1$\sigma$." (2.2 Outflow emission characteristics)
   - fitting: _not stated_
   - validation: t test at 90% confidence  
  > "at the 90% confidence level there is a direct proportionality between envelope mass and intensity" (2.2 Outflow emission characteristics)
3. **Assign outflow emission and make model image**: Each lobe a 2D Gaussian of 2000 AU radius with flux scaled to envelope mass; Class I reduced by 10; convolve with beam  
  > "scaling down the emission by a factor of ten for each Class I outflow. Finally, the map is convolved with the desired beam." (2.3 Outflow emission assignment)
   - assumption: Optically thin, no radiative transfer  
  > "no radiative transfer is done explicitly, and that all emission is implicitly assumed to be optically thin" (2.3 Outflow emission assignment)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare model with ALMA radial profile**: Radially average both images from cluster center, >3 sigma cut applied to both, primary beam accounted for  
  > "both images are radially averaged from the center of the cluster including only fluxes $>$3$\sigma$" (5.1 Comparison to ALMA observations of IRAS16547–4247)
   - assumption: Emission beyond 2'' dominated by low-mass population  
  > "Assuming that the emission at distances $>$ 2$''$ is dominated by the low-mass population" (5.1 Comparison to ALMA observations of IRAS16547–4247)
   - fitting: No fitting; model not tuned  
  > "Below, the standard model results are compared to these observations without fine-tuning of the input parameters." (Discussion, Comparison to ALMA observations of IRAS16547–4247)
   - validation: Direct comparison, no fine-tuning  
  > "the standard model results are compared to these observations without fine-tuning of the input parameters" (5.1 Comparison to ALMA observations of IRAS16547–4247)

## Software

- **cluster-in-a-box** : Public code for running the cluster model  
  > "The codes for running the model are publicly available" (2 Model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Methanol flux vs envelope mass slope | 78 | ±33 (1σ) | Jy km/s per Msun | 2 | $S$ = (78$\pm$33) $M_{\rm env}$ Jy km s$^{-1}$ $M_\odot^{-1}$ |
| Model peak intensity | 0.4 | not stated | Jy km/s/beam | 3 | The peak intensity is 0.4 Jy km s$^{-1}$ beam$^{-1}$ in the model image. |
| Fraction of cluster flux from low-mass outflows | ~50% | not stated | percent | 4 | approximately 50% of the cluster flux is coming from the low-mass outflows |
| Model profile deficit relative to observations at >2'' | 30–50% weaker | not stated | percent | 4 | at larger distances the model profile is 30–50% weaker than the observed profile |

## Qualitative findings

- Model reproduces observed extended methanol emission within a factor of two without tuning  
  > "the toy model reproduces observations to better than a factor of two" (abstract)

## Claim tuples

- H: Low-mass protostellar outflow methanol emission can account for extended emission in a high-mass cluster | E: Model of 3000-star cluster compared to ALMA IRAS16547–4247 radial profile | R: Model 30–50% weaker than observed beyond 2''; overlaps if no rms cut applied | F: About 50% of cluster flux arises from low-mass outflows | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Outflow emission scales with envelope mass, lowering contrast between low- and high-mass protostars  
  > "low-mass outflow emission scales with envelope mass" (1 Introduction)
- Alternative: Younger age, top-heavy IMF, larger cluster, more concentrated distribution could raise model flux  
  > "To obtain the factor of two increase in the model fluxes, several possibilities exist:" (5.1 Comparison to ALMA observations of IRAS16547–4247)
- How they decided it was enough: _not stated_
- Limitation (authors): Few data points for the flux–mass correlation; hot-core and high-mass outflow contributions not disentangled  
  > "Because of the low number of data points, the proportionality was not tested for higher levels of significance." (2.2 Outflow emission characteristics)
- Caveat (inferred, ours): Single cluster comparison; no quantitative goodness of fit
- Caveat (inferred, ours): Template based on only 7 protostars at 15'' resolution
- Caveat (inferred, ours): High-mass outflow and hot core contributions not modeled, so 50% fraction is rough

## Reproducibility

- Data public (paper): ALMA data from Science Archive; model code public on GitHub/Zenodo  
  > "The data were downloaded from the Science Archive." (5.1 Comparison to ALMA observations of IRAS16547–4247)
- Products in archive: _not stated_
- Code: https://github.com/egstrom/cluster-in-a-box, DOI:10.5281/zenodo.13184  
  > "<https://github.com/egstrom/cluster-in-a-box>,\ DOI:10.5281/zenodo.13184" (Footnote 1)
- Missing: ALMA project code not printed in the paper
- Missing: Exact imaging parameters
- Missing: Random seeds
- Data volume (inferred): A few GB for one ALMA Band 7 dataset
- Score (inferred): 3/5, Code public and model recipe described; ALMA reprocessing details and project code missing.
- Rediscovery candidate: no, Main result is a toy model comparison with loosely specified ALMA processing and no project code in the paper.

## Links

- Method: (cite: kristensen10a) (Methanol maps and reduction of JCMT data)
- Method: (cite: adams14) (Cluster spatial distribution model)
- Companion: (cite: higuchi14) (Original ALMA observations of IRAS16547–4247)

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00419.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 35,
  "rate": 0.493
 },
 "evidence_ok": true
}
```
