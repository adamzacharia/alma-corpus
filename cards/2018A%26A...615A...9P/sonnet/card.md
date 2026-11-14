# Distribution of Serpens South protostars revealed with ALMA

`2018A&A...615A...9P` | Astronomy and Astrophysics 2018 | first author: Plunkett, Adele L. | arXiv: 1804.02405 | DOI: 10.1051/0004-6361/201732372

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Are the protostars in the young Serpens South cluster mass segregated, and is any segregation primordial rather than dynamical?  
  > "Due to its young age, this is a feasible region to test whether the distribution of protostars is primordial, or whether enough time has passed for significant dynamical evolution or disruption." (Introduction)
- Target **Serpens South central cluster**: coordinates not stated (sources near 18:30:03, -02:02)  
  > "multi-epoch Very Long Baseline Array (VLBA) observations by (cite: Ort17) provided the distance to Serpens/Aquila molecular complex of $436.0\pm9.2$ pc, which we adopt for Serpens South in our study." (Introduction); z/distance 436 pc  
  > "multi-epoch Very Long Baseline Array (VLBA) observations by (cite: Ort17) provided the distance to Serpens/Aquila molecular complex of $436.0\pm9.2$ pc, which we adopt for Serpens South in our study." (Introduction); distance from Ortiz-León et al. 2017 VLBA parallax of Serpens/Aquila  
  > "multi-epoch Very Long Baseline Array (VLBA) observations by (cite: Ort17) provided the distance to Serpens/Aquila molecular complex of $436.0\pm9.2$ pc, which we adopt for Serpens South in our study." (Introduction)

## Data provenance

- ALMA projects: 2012.1.00769.S
- bands: Band 6 (1.3 mm)  
  > "The observations were made in Band 6, and continuum maps were made by selecting line-free spectral channels in four basebands" (2.1 ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 858 MHz total line-free; mean frequency 225.758 GHz  
  > "the total bandwidth of the continuum image (line-free channels) sums to 858 MHz." (2.1 ALMA Observations)
- arrays: 12m array (32 antennas) and 7m array (9 antennas)  
  > "The observations where made with the 12m array using 32 antennas (baselines 15-437 m) and the 7m array using 9 antennas (baselines 8-48 m) during 2014 January - June." (2.1 ALMA Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.96" x 0.59" (419 x 256 au)  
  > "Our map has a synthesized beam HPBW of $0.96\ensuremath{''}\times 0.59\ensuremath{''}$" (2.1 ALMA Observations)
- max recoverable scale: ~29"  
  > "The maximum recoverable scale is $\sim29\ensuremath{''}$, or 0.06 pc (for the 7m array in Band 6)." (2.1 ALMA Observations)
- sensitivity: rms 0.3-0.8 mJy/beam  
  > "varying between 0.3 and 0.8 mJy beam$^{-1}$" (2.1 ALMA Observations)
- time on source: 12m: 41 min x2; 7m: 18-34 min x8  
  > "Time on source during each execution block to make the maps were 41 minutes (times two executions) for the 12m array and 18-34 minutes (times 8 executions) for the 7m array." (2.1 ALMA Observations)
- observing dates: 2014 January - June  
  > "during 2014 January - June" (2.1 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: N2H+ J=1-0 (CARMA data, not ALMA) (93.173704 GHz)
- Other facility **CARMA (CLASSy)**: N2H+ (1-0) maps with zero-spacing, ~7" resolution  
  > "giving a $\sim 7\ensuremath{''}$ resolution while including the zero-spacing information" (2.2 Supplementary data to study dense gas)
- External data: YSO catalog with SED classes used to classify sources  
  > "We use especially the catalog of (cite: Dun15) for classifying sources in this work." (Introduction) [from (cite: Dun15)]
- External data: Distance 436.0±9.2 pc  
  > "$436.0\pm9.2$ pc, which we adopt for Serpens South in our study." (Introduction) [from (cite: Ort17)]
- External data: N2H+ CARMA data  
  > "the data were presented in (cite: Fer14)" (2.2 Supplementary data to study dense gas) [from (cite: Fer14)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres, J1751+096, Mars, Neptune, Titan  
  > "Flux calibrators used were: Ceres, J1751+096, Mars, Neptune, Titan." (2.1 ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean, multi-frequency synthesis  
  > "In the CASA tclean task, we used multi-frequency synthesis and a robust weighting parameter of 0.5 to make the continuum image." (2.1 ALMA Observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "a robust weighting parameter of 0.5" (2.1 ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: interactive CLEAN boxes  
  > "We masked interactively, drawing CLEAN boxes around the emission and reviewing residuals before reiterating." (2.1 ALMA Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied  
  > "Finally we corrected for primary beam." (2.1 ALMA Observations)
- array combination: 12m and 7m combined in CLEAN  
  > "We combined observations from the 12m and 7m arrays in the CLEAN process." (Observations and data, ALMA Observations)
- smoothing: _not stated_
- final beam: 0.96" x 0.59"  
  > "synthesized beam HPBW of $0.96\ensuremath{''}\times 0.59\ensuremath{''}$" (2.1 ALMA Observations)
- final rms: _not stated_

### Inherited from earlier work

- Dust opacity and temperatures follow Looney et al. 2000, consistent with earlier Serpens South study  
  > "These values are consistent with our previous study of Serpens South (cite: Plu15a)" (3.3 Source masses) [from (cite: Loo00); (cite: Plu15a)]
- MST mass segregation ratio algorithm  
  > "we adopt the algorithm described in (cite: All09b)" (4.2 Minimum Spanning Tree) [from (cite: All09b)]
- N2H+ velocity dispersion map method  
  > "To obtain the velocity dispersion map (cite: Sto14) the seven N$_{2}$H$^{+}$(1-0) hyperfine components were modeled simultaneously" (2.2 Supplementary data to study dense gas) [from (cite: Sto14)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration (pipeline vs manual) details
- Clean threshold, cell size, image size, and number of iterations
- Exact cluster center coordinates and the N2H+ weighting
- Mass formula treatment of unresolved sources
- Random seed for the 500 MST random sets
- Whether total or peak flux was used for mass

## Analysis recipe

1. **Make 12m+7m continuum mosaic**: tclean with MFS on line-free channels, combining arrays, primary-beam corrected  
  > "We combined observations from the 12m and 7m arrays in the CLEAN process." (2.1 ALMA Observations)
   - software: CASA
   - parameter: robust = 0.5  
  > "a robust weighting parameter of 0.5" (2.1 ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify mm sources and measure fluxes**: 2D Gaussian fits to peaks above local 5 sigma, two-Gaussian fits for two blended pairs  
  > "first we made two-dimensional (2D) Gaussian fits where emission exceeded $5\sigma$ and where a local emission peak was seen by eye; fits were made using the task imfit in MIRIAD" (3.1 Millimeter continuum source identifications)
   - software: MIRIAD imfit
   - parameter: 5 sigma threshold varying with local rms  
  > "we take this variation into account by changing the $5\sigma$ threshold detection limit accordingly throughout the image." (3.1 Millimeter continuum source identifications)
   - fitting: 2D Gaussians  
  > "first we made two-dimensional (2D) Gaussian fits where emission exceeded $5\sigma$ and where a local emission peak was seen by eye" (Results, Millimeter continuum source identifications)
   - validation: Estimated fewer than four extragalactic contaminants from deep ALMA surveys  
  > "we estimate that within our mapped region (where power is greater than 30%) fewer than four extragalactic sources should appear as contaminants" (3.1 Millimeter continuum source identifications)
3. **Derive source masses**: Optically thin dust emission, M = D^2 S/(B(Td) kappa)  
  > "This calculation assumes an optically thin model and a constant temperature for each source." (3.3 Source masses)
   - parameter: kappa = 0.0188 cm2/g at 1.3 mm (beta=1)  
  > "which corresponds to $\kappa_\nu=0.0188$ cm$^2$g$^{-1}$ at $\lambda=1.3$ mm" (3.3 Source masses)
   - parameter: Td = 35 K with IR counterpart, 15 K without  
  > "We assigned $T_d=35$ K for sources with IR counterparts and $T_d=15$ K for deeply embedded sources without IR counterparts" (3.3 Source masses)
   - assumption: distance 436 pc  
  > "equivalent to a linear resolution of $419\times 256$ au at a distance of 436 pc" (2.1 ALMA Observations)
   - fitting: _not stated_
   - validation: Tested single-temperature alternatives; mass uncertainty a factor of a few  
  > "the mass calculation may have an error of a factor of a few" (3.3 Source masses)
4. **Test stability of sources without IR counterpart**: Compare observed density and radius with Bonnor-Ebert critical density and maximum radius  
  > "we compare the core with a Bonnor-Ebert isothermal sphere, inferring the critical density ($n_{crit}$) and maximum radius ($R_{max}$) for stability." (3.4 Pre-stellar source stability)
   - parameter: T = 15 K, mu = 2.73 mH, M_BE = mm mass  
  > "where we used T=15 K as the typical temperature, and we assumed the Bonnor Ebert mass $M_{BE}$ is the mm mass" (3.4 Pre-stellar source stability)
   - fitting: _not stated_
   - validation: ~30% uncertainty on ratios  
  > "Given estimated uncertainty of $\sim30$% for the ratios" (3.4 Pre-stellar source stability)
5. **Mass segregation via MST**: MST length of N most massive sources vs mean over 500 random sets, giving Lambda_MSR  
  > "We take the average over 500 random sets of $N$ sources in the cluster to estimate L$_{norm}$ and its statistical deviation" (4.2 Minimum Spanning Tree)
   - software: scipy csgraph
   - assumption: Analysis limited to sources without IR counterpart, presumed roughly coeval  
  > "we deal with sources in the pre-stellar and earliest Class 0 stages, that we presume are roughly coeval." (4.3 Segregation according to mass or age effects)
   - fitting: _not stated_
   - validation: Accretion mass estimate shows age effects unlikely to change conclusion  
  > "the conclusions of mass segregation according to MST analysis for the youngest sources holds" (4.3 Segregation according to mass or age effects)
6. **Estimate dynamical segregation timescale**: Spitzer 1969 segregation time with crossing time from N2H+ velocity dispersion  
  > "We follow the (cite: 1969ApJ...158L.139S) prescription for the time scale for mass segregation" (4.4 Timescale for mass segregation)
   - parameter: v_disp=0.47 km/s, R_hm=0.14 pc, <m>=0.4 Msun, N~100  
  > "we derive $v_{disp}=0.47$ km s$^{-1}$" (4.4 Timescale for mass segregation)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : tclean imaging  
  > "In the CASA tclean task" (2.1 ALMA Observations)
- **MIRIAD** : imfit Gaussian fitting of sources  
  > "fits were made using the task imfit in MIRIAD" (3.1 Millimeter continuum source identifications)
- **SciPy** : csgraph MST computation  
  > "We compute it by means of the csgraph routine in the Python scipy toolkit" (4.2 Minimum Spanning Tree)
- **Astropy** : general analysis  
  > "This research made use of Astropy" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of mm sources | 52 | not stated | sources | 2 | We identified 52 mm sources in our map |
| Source mass range | 0.002 to 0.9 | factor of a few | Msun | 3 | The masses we measured are in the range of 0.002 to 0.9 $\mbox{M$_\odot$}$ |
| Lambda_MSR plateau for 3<=N<=18 | ~3.7 | not stated | dimensionless | 5 | an approximately flat plateau with a mean value of $\langle\Lambda_{MSR}\rangle \sim3.7$ for $3\leq N_{MST}\leq18$ |
| Lambda_MSR at N=2 | ~43 | not stated | dimensionless | 5 | a very large value of the mass segregation ratio for $N_{MST}=2$ ($\Lambda_{MSR}\sim43$ |
| Crossing time | 0.6 | not stated | Myr | 6 | The resulting crossing time is $t_{crossing}=0.6$ Myr. |
| Median distance of sources from cluster center | 0.06 | not stated | pc | 0 | we measure a median distance from the cluster center of 0.06 pc |
| Fraction of IR-less sources unstable | 70% | not stated | percent | 4 | This corresponds to 70% of the sample of mm sources with no IR counterpart |

## Qualitative findings

- Youngest mm sources are mass segregated, probably primordially; no segregation seen for Class 0/I sources with IR counterparts.  
  > "we present evidence for mass segregation, specifically among the youngest mm sources (those with no IR counterpart)." (Summary)

## Claim tuples

- H: Youngest protostellar candidates are mass segregated | E: MST Lambda_MSR on mm-mass-ranked sources without IR counterpart | R: Lambda_MSR ~3.7 for 3<=N<=18, ~1 beyond N~21 | F: Segregation among most massive pre-stellar candidates | **supported**
- H: The segregation is primordial | E: Compare dynamical segregation time to cluster age | R: 7e5 yr for 1 Msun, longer than source ages | F: Segregation probably primordial | **partially**
- H: Many IR-less cores are collapsing | E: Bonnor-Ebert density and radius criteria | R: 20 sources unstable | F: ~70% likely unstable | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: MST avoids needing a cluster center  
  > "The MST method has the virtue of avoiding problems such as setting the cluster center" (4.2 Minimum Spanning Tree)
- How they decided it was enough: _not stated_
- Limitation (authors): Mm masses are envelope/disk masses, so age effects cannot be entirely ruled out  
  > "in this analysis the data cannot entirely rule out small contributions that might be the result of age segregation." (4.3 Segregation according to mass or age effects)
- Caveat (inferred, ours): Mass depends strongly on assigned Td split by IR counterpart, which correlates with the sample used in MST
- Caveat (inferred, ours): Source mass is not protostar mass
- Caveat (inferred, ours): Possible extragalactic contaminants and incomplete sensitivity near bright central sources
- Caveat (inferred, ours): Statistical significance of Lambda_MSR vs. random not fully quantified

## Reproducibility

- Data public (paper): FITS map available at CDS; ALMA project cited  
  > "FITS data are available at the CDS via anonymous ftp to" (2.1 ALMA Observations)
- Products in archive: _not stated_
- Missing: CASA version and calibration script
- Missing: Imaging parameters beyond robust
- Missing: Cluster center coordinates
- Missing: Random seeds
- Data volume (inferred): ~100-300 GB raw for 12m+7m mosaics
- Score (inferred): 3/5, Data public and recipe mostly described with a source table, but many processing details are missing.
- Rediscovery candidate: yes, Public data, simple recipe, and numeric results (52 sources, masses, Lambda_MSR).

## Links

- Method: (cite: All09b) (MST mass segregation ratio)
- Method: (cite: Loo00) (dust opacity and temperature)
- Companion: (cite: Plu15a) (previous CARMA continuum study)
- Companion: (cite: Plu15b) (outflow from serps45 using same project)
- Related: CLASSy
- Related: Gould Belt survey

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 53,
  "rate": 0.646
 },
 "evidence_ok": true
}
```
