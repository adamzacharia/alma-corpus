# No Evidence for Millimeter Continuum Source Overdensities in the Environments of z ≳ 6 Quasars

`2018ApJ...867..153C` | The Astrophysical Journal 2018 | first author: Champagne, Jaclyn B. | arXiv: 1809.10178 | DOI: 10.3847/1538-4357/aae396

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Do 1.2 mm continuum source counts in ALMA Band 6 fields around 35 z>6 quasars show an overdensity relative to blank-field number counts, as expected for early protoclusters?  
  > "We compare the detection rates of continuum sources at $\geq5\sigma$ significance in the fields surrounding the quasars (A$_{\rm eff}$ = 4.3 arcmin$^2$) with millimeter number counts in blank field surveys." (abstract)
- Target **35 quasars at 5.95<z<6.90 (Table 1; e.g. PJ007+04, J0305-3150, PJ231-20)**: coordinates Listed per quasar in Table 1 (RA/Dec J2000)  
  > "| VIK J0305–3150 | J0305–3150 | 03:05:16.92 | –31:50:56.0 | 44.0 | 6.6145$\pm$0.0001 | \[CII\] | 15 |" (Table 1); z/distance z = 5.95-6.90 (per quasar, Table 1)  
  > "| VIK J0305–3150 | J0305–3150 | 03:05:16.92 | –31:50:56.0 | 44.0 | 6.6145$\pm$0.0001 | \[CII\] | 15 |" (Table 1); distance from [CII], MgII, Lyα or CO redshifts from literature (Table 1 references)  
  > "| VIK J0305–3150 | J0305–3150 | 03:05:16.92 | –31:50:56.0 | 44.0 | 6.6145$\pm$0.0001 | \[CII\] | 15 |" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00206.S, 2011.0.00243.S, 2012.1.00882.S, 2013.1.00273.S, 2015.1.00997.S
- bands: Band 6 (211-275 GHz)  
  > "ALMA observations in Band 6 (211-275 GHz, corresponding to rest-frame FIR $\sim150-200\mu$m)" (Observations and Data Reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12 m antennas, compact configuration  
  > "with a compact configuration using 38-49 12 m antennas" (Observations and Data Reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthesized beam FWHM 0.5" to 1.0"  
  > "The typical FWHM of the synthesized beam at these frequencies ranges from $0.5\ensuremath{''}$ to $1.0\ensuremath{''}$." (Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: mean RMS 58.6±19.0 µJy/beam (range 21.0-98.4)  
  > "The average RMS noise in the images is 58.6$\pm$19.0 $\mu$Jy beam$^{-1}$, spanning a range of 21.0$-$98.4 $\mu$Jy beam$^{-1}$" (Observations and Data Reduction)
- time on source: _not stated_
- observing dates: 27 Decarli sample observations 2016 January-July; 8 archival from Cycles 0-1  
  > "they were carried out between 2016 January and July, with a compact configuration using 38-49 12 m antennas." (Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: [CII] 158 µm (spectral windows cover expected observed frequency; continuum analysis) (not stated)
- External data: Blank-field 1.2 mm number counts Schechter fit (phi*, alpha, S*) used for injected sources and expected counts  
  > "The Schechter model we choose is based on the most recent blank field 1.2 mm number counts compilation of (cite: Fujimoto2016a) valid for flux densities of 0.1-1.5 mJy" (Data Analysis) [from (cite: Fujimoto2016a)]
- External data: Quasar redshifts (Table 1)  
  > "1- (cite: Banados2016a); 2- Venemans et al. (in prep); 3- (cite: Carnall2015a)" (Table 1) [from (cite: Banados2016a) and others in Table 1 notes]
- External data: [CII] companion sources from earlier ALMA work shown for comparison  
  > "three \[CII\] sources found in (cite: Decarli2017a) and (cite: Willott2017a) which are not found in continuum here" (Results) [from (cite: Decarli2017a); (cite: Willott2017a)]
- External data: Protocluster overdensity profile model used to predict expected delta_gal  
  > "(cite: Chiang2013a) uses semi-analytical models of protocluster evolution to predict their overdensity profiles out to $z=5$ in cubes of (15 cMpc)$^3$." (Discussion) [from (cite: Chiang2013a)]
- Simulation/model as data: 1000 simulated Gaussian-noise maps with injected Schechter-distributed unresolved sources for completeness/contamination  
  > "we generate 1000 simulated maps with area equivalent to the 35 primary beams in this study." (Data Analysis)

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "The data have been reduced using the pipeline developed for the Common Astronomy Software Applications (cite: McMullin2007a)" (Observations and Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN  
  > "deconvolved using the CLEAN task" (Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Each data set is imaged using natural weighting and is cleaned down to the 3$\rm \sigma$ noise level." (Observations and Data Reduction)
- uv taper: _not stated_
- cell size: 0.1" (Cycle 4), 0.15" (earlier cycles)  
  > "The pixel size is $0.1\ensuremath{''}\times0.1\ensuremath{''}$ for the Cycle 4 data and $0.15\ensuremath{''}\times0.15\ensuremath{''}$ for the earlier cycles." (Observations and Data Reduction)
- image size: _not stated_
- masking: 4"x4" mask on quasar (modified for J1152+0055 and PJ231-20)  
  > "We exclude the region of the field containing most of the quasar’s flux by applying a conservative $4\ensuremath{''} \times 4\ensuremath{''}$ mask centered on the known quasar coordinates." (Data Analysis)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: search only where PB response >50% (~12" radius); detection on uncorrected maps, fluxes corrected afterwards  
  > "We search for sources only where the primary beam response is greater than 50% so the final images have been trimmed to this area (approximately $12\ensuremath{''}$ in radius)." (Observations and Data Reduction)
- array combination: _not stated_
- smoothing: none; original resolution of each map kept  
  > "We utilize the original resolution of each map, since homogenizing the resolution across the maps would cause an overall loss of depth." (Observations and Data Reduction)
- final beam: _not stated_
- final rms: 58.6±19.0 µJy/beam average before PB correction  
  > "this is the uncorrected RMS calculated from the image after the quasar has been masked out but before we make the primary beam correction." (Observations and Data Reduction)

### Inherited from earlier work

- Number counts constructed as in previous ALMA surveys  
  > "we construct the number counts as in previous ALMA surveys (cite: Fujimoto2016a)." (Results) [from (cite: Fujimoto2016a)]
- 27 of the datasets are those of the [CII] search  
  > "the remaining 27 objects constitute the sample used in the \[CII\] search by (cite: Decarli2017a; Decarli2018a)." (Observations and Data Reduction) [from (cite: Decarli2017a; Decarli2018a)]

### Not stated but needed to reproduce (our reading)

- Which CASA version and pipeline version were used
- Exact observing setups/execution blocks per project and which project covers which quasar
- Specific region-growing source-finder implementation and code
- Details of the fidelity/completeness evaluation as function of flux (values beyond 5σ)
- Whether archival Cycle 0-1 data were pipeline- or manually-calibrated; flux calibrators and scale uncertainties
- Line-free channel selection/continuum bandwidth used for collapsing to continuum maps
- CLEAN mask/iteration settings, image size
- Method used for the Monte Carlo 16th-84th percentile Fujimoto curve

## Analysis recipe

1. **Reduce and image continuum maps**: Pipeline calibration, CLEAN with natural weighting to 3σ, original resolution  
  > "Each data set is imaged using natural weighting and is cleaned down to the 3$\rm \sigma$ noise level." (Observations and Data Reduction)
   - software: CASA
   - parameter: pixel 0.1" (Cycle 4) / 0.15" (earlier)  
  > "The pixel size is $0.1\ensuremath{''}\times0.1\ensuremath{''}$ for the Cycle 4 data" (Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Mask quasar and build SNR maps**: Mask 4"x4" around quasar; divide by continuum RMS (no primary beam correction); trim to PB>50%  
  > "We create signal-to-noise ratio maps to identify potential candidates in the field by dividing by the continuum RMS (not corrected for the primary beam)." (Data Analysis)
   - fitting: _not stated_
   - validation: Compared pixel SNR histogram with inverted negative side as pure noise  
  > "since negative flux is guaranteed to be noise, we invert this distribution to show what a pure noise distribution would look like" (Data Analysis)
3. **Choose detection threshold via mock observations**: 1000 simulated noise maps with Schechter-injected unresolved sources, convolved with 0.8"x0.5" beam; region-growing source finder; completeness and contamination vs SNR  
  > "Figure [3](#fig:completeness) indicates that we reach a satisfactory completeness of 91.6% and contamination of 4.3% at a $5\sigma$ detection threshold." (Data Analysis)
   - parameter: source = two or more adjacent pixels above 5σ  
  > "A grouping is declared a source if there are two or more adjacent pixels above the SNR threshold." (Data Analysis)
   - assumption: Injected sources unresolved and unclustered; blank-field Fujimoto2016 Schechter counts  
  > "We assume the injected sources are unresolved and unclustered." (Data Analysis)
   - fitting: _not stated_
   - validation: Completeness/contamination from mocks  
  > "Figure [3](#fig:completeness) indicates that we reach a satisfactory completeness of 91.6% and contamination of 4.3% at a $5\sigma$ detection threshold." (Data Analysis)
4. **Construct number counts**: Per-source weight xi=(1-f)/(C A_eff), summed in 6 log bins of 0.25 dex; Poisson errors plus completeness/contamination uncertainty  
  > "The uncertainty is calculated based on Poisson statistics propagated with the 1$\sigma$ uncertainty in the completeness and contamination as from our simulations." (Results)
   - fitting: _not stated_
   - validation: Compared with Scott2010 and Fujimoto2016 counts  
  > "We compare the distribution of our sources in Figure [6](#fig:nc) with several blank field number counts at 1.1 and 1.2 mm, with fits from (cite: Scott2010a) and (cite: Fujimoto2016a)." (Results)
5. **Compute overdensity**: delta_gal=(N_gal-N_exp)/N_exp using Fujimoto2016 expected counts over effective area; also radial dependence test  
  > "Correcting for fidelity and completeness, our measured number of sources $N_{\rm gal}$ is 15.1$\pm$5.7." (Results)
   - fitting: _not stated_
   - validation: N_gal recomputed with fields cut at various radii; consistent with uniform  
  > "The sources are consistent with a uniform distribution at 50% of the primary beam, and this remains true at any area cut" (Results)

## Software

- **CASA** : pipeline data reduction and CLEAN imaging  
  > "The data have been reduced using the pipeline developed for the Common Astronomy Software Applications (cite: McMullin2007a)" (Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of continuum sources detected at ≥5σ | 15 | not stated | sources | 3 | The results from the source-finding algorithm reveal a total of 15 candidate detections in the 35 fields |
| Completeness at 5σ | 91.6 | not stated | percent | 3 | completeness of 91.6% and contamination of 4.3% at a $5\sigma$ detection threshold |
| Contamination at 5σ | 4.3 | not stated | percent | 3 | completeness of 91.6% and contamination of 4.3% at a $5\sigma$ detection threshold |
| Expected sources N_exp (0.1-10 mJy) | 16.1 | +3.3/-6.8 | sources | 5 | we would expect $N_{\rm exp} = 16.1^{+3.3}_{-6.8}$ sources between 0.1-10 mJy in these fields without an overdensity |
| Measured N_gal (corrected) | 15.1 | ±5.7 | sources | 5 | our measured number of sources $N_{\rm gal}$ is 15.1$\pm$5.7 |
| Overdensity delta_gal | -0.07 | ±0.56 | dimensionless | 5 | this implies a value of $\delta_{\rm gal} = -0.07\pm0.56$ |
| Maximum effective area | 4.3 | not stated | arcmin^2 | 2 | The deepest data have a flux limit of 0.15 mJy beam$^{-1}$ and the maximum effective area is 4.3 arcmin$^2$. |
| Predicted 2D delta_gal if quasars sit at protocluster peak | ≈0.3 | not stated | dimensionless | 0 | or a 2D $\delta_{\rm gal} \approx 0.3$ when including the expected millimeter foreground sources |

## Qualitative findings

- Continuum counts around quasars are consistent with blank fields; the lack of overdensity does not exclude protoclusters because of small field of view, cosmic variance and foreground contamination along the line of sight.  
  > "it is most likely that the large line of sight volume probed by a continuum survey will wash out a true overdensity signal." (abstract)

## Claim tuples

- H: A high number of mm dust emitters near z>6 quasars relative to blank fields indicates protoclusters | E: Count ≥5σ 1.2 mm sources in 35 quasar fields and compare with Fujimoto2016 blank-field counts | R: N_gal=15.1±5.7 vs N_exp=16.1; delta_gal=-0.07±0.56 | F: No continuum overdensity detected within ~140 pkpc | **supported**
- H: Continuum should trace the [CII] overdensities seen by Decarli et al. | E: Compare continuum counts to the [CII] result | R: No continuum excess | F: Discrepancy likely due to large line-of-sight volume of continuum selection | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Millimeter continuum probes a larger redshift range than [CII] and number counts are better constrained than high-z luminosity functions  
  > "the number counts for 1.1 mm and 1.2 mm sources are more certain than high-redshift UV, IR, and \[CII\] luminosity functions" (Introduction)
- Alternative: Statistical flux excess rather than discrete sources was considered; discrete source search chosen  
  > "our argument for searching for formally detected discrete sources rather than statistical flux excess is sound." (Data Analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Sample is not formally complete; no redshifts for the continuum sources  
  > "this study includes every $z\sim6$ quasar with available Band 6 observations but is not formally complete in any physical quantity" (Observations and Data Reduction)
- Limitation (authors): Small field of view, cosmic variance, and foreground sources limit the test  
  > "our current data do not achieve high enough contrast against the foreground population." (Discussion)
- Caveat (inferred, ours): Large uncertainty on delta_gal (±0.56) gives little power to detect modest overdensities
- Caveat (inferred, ours): Blank-field model uncertainty and cosmic variance dominate
- Caveat (inferred, ours): Sources without redshifts cannot be associated with the quasars
- Caveat (inferred, ours): Heterogeneous archival data of varied depth

## Reproducibility

- Data public (paper): ALMA data identified by project code in acknowledgments (archival)  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA: 2011.0.00206.S (PI: R. Wang)" (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA/pipeline versions
- Missing: Source-finder code
- Missing: Continuum channel selection
- Missing: Mapping of projects to targets
- Data volume (inferred): ~100-300 GB raw for 35 fields
- Score (inferred): 3/5, Public data and clear counting methodology, but source-finder, CASA version and calibration details are absent.
- Rediscovery candidate: yes, Public archival data, simple recipe (image, 5σ source finding, number-count comparison), numeric result delta_gal.

## Links

- Method: (cite: Fujimoto2016a) (Blank-field 1.2 mm number counts and counting method)
- Companion: (cite: Decarli2017a) ([CII] companion overdensity in the same quasar sample)
- Companion: (cite: Decarli2018a) (Source of the 27 ALMA observations)
- Related: Decarli et al. ALMA [CII] quasar survey

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 43,
  "rate": 0.589
 },
 "evidence_ok": true
}
```
