# A High Cluster Formation Efficiency in the Sagittarius B2 Complex

`2018ApJ...864L..17G` | The Astrophysical Journal Letters 2018 | first author: Ginsburg, Adam | arXiv: 1808.06616 | DOI: 10.3847/2041-8213/aada89

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type archival_reuse

## Science

- Fields: milky_way_ism, star_formation
- Question: What fraction of stars in Sgr B2 form in bound clusters (the CFE), and is it consistent with environmentally dependent CFE models?  
  > "We report a measurement of the CFE in the highest-density region in the Galaxy, Sgr B2, based on ALMA observations of high-mass young stellar objects." (abstract)
- Target **Sgr B2 (M, N clusters)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00269.S
- bands: 3 mm band, 0.5 arcsec resolution (data from Ginsburg et al. 2018)  
  > "obtaining a resolution of $0.5\arcsec$ in the 3 mm band." (Census of the Stellar Population)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: H recombination line H41alpha (not stated)
- Other facility **VLA/JVLA**: 1.3 cm and 7 mm catalogs of H II regions (Gaume 1995; De Pree 2015)  
  > "They detected 49 continuum sources. These are exclusively H II regions and components of H II regions." (Census of the Stellar Population)
- External data: Catalog of 271 ALMA 3 mm sources, 31 H II regions, and cluster census counts  
  > "They reported a total of 271 sources spread throughout the cloud, of which 31 are confirmed H II regions" (Census of the Stellar Population) [from (cite: Ginsburg2018a)]
- External data: Gas masses and instantaneous SFE of Sgr B2 M and N  
  > "give a gas mass of $M=9.6\ensuremath{\times 10^{3}}$ $\mathrm{M}_{\odot}$ in the Sgr B2 M cluster in their Table 2" (Mass of the clusters) [from (cite: Schmiedeke2016a)]
- External data: Literature H II region velocities  
  > "Of the 32 unique H II regions within the field identified in the (cite: Gaume1995a) 1.3 cm data, 15 had measurements in (cite: De-Pree2011a)." (Velocity Dispersion Measurements - boundedness) [from (cite: De-Pree2011a)]
- External data: CFE of 7 (+7/-3)% for the local neighborhood  
  > "(cite: Lada2003a) reported a CFE of $\Gamma=7^{+7}_{-3}\%$ for the local neighborhood" (The cluster formation efficiency) [from (cite: Lada2003a)]
- Simulation/model as data: Kruijssen (2012) CFE model, global and local versions, with Monte Carlo error propagation  
  > "We obtain uncertainty contours on the model predictions by carrying out a Monte Carlo error propagation of the uncertainties on the observed parameters used as the input values." (Comparison of observations to predictions)

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

- Kroupa IMF extrapolation of the total stellar mass from observed objects  
  > "We follow (cite: Ginsburg2018a) in extrapolating the total stellar mass implied by the observed objects using a (cite: Kroupa2001a) initial mass function." (Census of the Stellar Population) [from (cite: Ginsburg2018a)]
- ALMA data reduction and source catalog  
  > "We note several ways the survey may be incomplete, which were described in detail in (cite: Ginsburg2018a)" (Effects of completeness) [from (cite: Ginsburg2018a)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging details (all deferred to Ginsburg et al. 2018)
- H41alpha line fitting setup (line model, initial guesses, baseline handling)
- Distance to Sgr B2
- Exact Monte Carlo setup for the model prediction

## Analysis recipe

1. **Census of stellar population**: Combine VLA and ALMA catalogs of H II regions and cores, extrapolate to total stellar mass with Kroupa IMF  
  > "each H II region implies the presence of a total of 326 $\mathrm{M}_{\odot}$ of stars, while each 8-20 $\mathrm{M}_{\odot}$ core represents 135 $\mathrm{M}_{\odot}$" (Census of the Stellar Population)
   - assumption: Upper stellar mass limit of 200 Msun; each VLA source is an H II region with a star of at least 20 Msun  
  > "assuming an upper stellar mass limit of 200 $\mathrm{M}_{\odot}$" (Census of the Stellar Population)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure H II region velocities and velocity dispersion**: Fit H41alpha lines, take standard deviation of V_LSR and compare with escape speed  
  > "We measure the 1D velocity dispersion in Sgr B2 M by taking the standard deviation of the measured V$_{\rm LSR}$ values." (Velocity Dispersion Measurements - boundedness)
   - software: pyspeckit
   - assumption: H II regions trace stellar motions  
  > "they closely follow the motions of their stars and serve as probes of the underlying stellar kinematics." (Velocity Dispersion Measurements - boundedness)
   - fitting: _not stated_
   - validation: Compared with De Pree et al. 2011 velocities (agree within 5 km/s except F10.37)  
  > "Our measurements agree to within 5 km s$^{-1}$ with those of (cite: De-Pree2011a) for all sources we both measured except F10.37" (Velocity Dispersion Measurements - boundedness)
3. **Compute CFE**: Gamma = M_clustered / M_total from clusters M and N  
  > "These values imply a CFE of $\Gamma=M_{\rm *,clustered}/M_{\rm *,total}\times100\% = 37\%$." (The cluster formation efficiency)
   - fitting: _not stated_
   - validation: Varied cluster membership and completeness; lower limit from source counts  
  > "With 78 clustered out of a total of 297 sources, we obtain a CFE of $\Gamma>26\%$." (Effects of completeness)
4. **Compare with the Kruijssen 2012 model**: Predict f_bound from observed gas parameters, ignoring the cruel cradle effect, with Monte Carlo errors  
  > "we only consider the bound fraction of star formation and omit the ‘cruel cradle effect’ (CCE)" (Comparison of observations to predictions)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **pyspeckit** : line fitting  
  > "Pyspeckit (cite: Ginsburg2011c) was used for the line fitting." (Software)
- **matplotlib** : plots  
  > "Plots were made with matplotlib (cite: Hunter2007a)." (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Cluster formation efficiency | 37 | 7 | % | 3 | we adopt $\Gamma=37\pm7\%$ |
| 1D velocity dispersion of Sgr B2 M, full data set | 12 | not stated | km/s | 2 | Using the full data set, we obtain a higher $\sigma_{\rm 1D}\approx12~\textrm{km~s}\ensuremath{^{-1}}$. |
| Lower limit on CFE from source counts | >26 | not stated | % | 3 | we obtain a CFE of $\Gamma>26\%$ |
| Predicted f_bound (global model) | 44.8 | 13.1 | % | 4 | $f_{\rm bound,global}$ / \[%\] / 44.8 / 13.1 |

## Qualitative findings

- The Sgr B2 M cluster is gravitationally bound, since sigma_1D is below the escape speed of 14 km/s.  
  > "implies that the Sgr B2 M cluster is presently bound" (Velocity Dispersion Measurements - boundedness)

## Claim tuples

- H: The CFE is constant in the Galaxy | E: Measure the CFE in Sgr B2 from ALMA and VLA source counts and compare with the solar neighborhood | R: Gamma = 37±7% versus 7% locally | F: The CFE varies within the Milky Way | **supported**
- H: Environmentally dependent CFE models predict the observed CFE | E: Compare with the Kruijssen 2012 model | R: Predictions of 45–49% are slightly above the observed value but consistent within the errors | F: The model is consistent with Sgr B2 | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Excluding NE and S from the clusters; larger M cluster radius of 1.4 pc  
  > "We therefore exclude them from the analysis" (Mass of the clusters)
- How they decided it was enough: _not stated_
- Limitation (authors): Completeness of the core catalog is hard to evaluate and depends on the models used  
  > "For the less massive ‘cores’, the completeness is much more difficult to evaluate" (Effects of completeness)
- Caveat (inferred, ours): The CFE depends on the IMF extrapolation and on the assumed cluster boundaries
- Caveat (inferred, ours): The error of 7% is a judgement of systematic effects, not a statistical error

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: Code is on GitHub: keflavich/SgrB2_ALMA_3mm_Mosaic and keflavich/SgrB2_CFE  
  > "<https://github.com/keflavich/SgrB2_ALMA_3mm_Mosaic/> and <https://github.com/keflavich/SgrB2_CFE>" (Software)
- Missing: ALMA calibration and imaging details, available only in Ginsburg et al. 2018
- Missing: Exact line-fitting setup
- Data volume (inferred): Tens of GB (3 mm ALMA mosaic), if reprocessing from scratch
- Score (inferred): 3/5, The code is public and the numbers are simple, but the catalog and processing come from the earlier paper.
- Rediscovery candidate: no, The main result depends on the catalogs of the earlier paper and on judgement about membership.

## Links

- Method: (cite: Ginsburg2018a) (Source catalog and ALMA data processing)
- Method: (cite: Kruijssen2012a) (CFE model)

## Checks

```json
{
 "quotes": 34,
 "quotes_ok": 34,
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
  "facts": 71,
  "stated": 24,
  "rate": 0.338
 },
 "evidence_ok": true
}
```
