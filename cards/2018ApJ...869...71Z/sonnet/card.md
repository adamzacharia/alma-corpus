# Constraining the Volume Density of Dusty Star-forming Galaxies through the First 3 mm Number Counts from ALMA

`2018ApJ...869...71Z` | The Astrophysical Journal 2018 | first author: Zavala, J. A. | arXiv: 1810.12300 | DOI: 10.3847/1538-4357/aaecd2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies
- Question: What are the 3 mm galaxy number counts from archival ALMA Band 3 data, and what do they imply for the volume density of DSFGs and their contribution to the CSFRD at z>4?  
  > "These number counts are then used to place constraints on the volume density of DSFGs with an empirical backward evolution model." (abstract)
- Target **COSMOS, CDF-S and UDS legacy fields (archival Band 3 pointings)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00092.S, 2015.1.00853.S, 2016.1.00171.S, 2016.1.00324.L, 2016.1.00698.S, 2015.1.01528.S
- bands: Band 3 (84-116 GHz, 2.59-3.57 mm)  
  > "we search for public ALMA Band 3 observations, which cover a frequency range of $\nu=84-116$ GHz or $\lambda=2.59-3.57$ mm" (2.1 ALMA Band 3 archival data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: total 8 GHz  
  > "the typical achieved continuum depth across the total 8 GHz bandwidth, in the case of ALMA" (2 Data retrieval)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: theta >= 1.0 arcsec  
  > "A restriction on the angular resolution of the images, $\theta\ge1.0$ arcsec, was also imposed" (2.1 ALMA Band 3 archival data)
- max recoverable scale: _not stated_
- sensitivity: continuum rms < 0.2 mJy/beam  
  > "observations were restricted to have a continuum sensitivity of $\sigma_{\rm rms}<0.2\rm\,mJy\,beam^{-1}$" (2.1 ALMA Band 3 archival data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- External data: Backward evolution model of the submm sky (IRLF evolution, SED assignment) used for predictions  
  > "we use the estimated galaxy number counts and the predictions from the backward evolution model presented by (cite: Casey2018a; Casey2018b)" (4 Constraining the infrared galaxy luminosity function) [from (cite: Casey2018a; Casey2018b)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Archive continuum maps used for the blind search; maps with detections re-reduced with CASA  
  > "we individually re-reduce the raw data using casa ((cite: McMullin2007a)) following the standard procedure, with a natural weighting of the visibilites" (2.1 ALMA Band 3 archival data)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting for re-reduced maps; archive maps usually Briggs  
  > "the signal-to-noise ratio (SNR) is typically lower in the retrieved images since a Briggs weighting is usually adopted" (2.1 ALMA Band 3 archival data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Extraction on uncorrected PB maps; fluxes measured on PB-corrected maps  
  > "the associated flux density of each candidate is measured from the primary-beam corrected image at the same position" (2.2 Source extraction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Number-count method follows previous ALMA blind surveys  
  > "In this paper, we follow the typical method used previously in those works." (3 Number Counts) [from (cite: Hatsukade2013a; Carniani2015a; Fujimoto2016a; Oteo2016a; Franco2018a; Hatsukade2018a)]
- Poisson uncertainties  
  > "Poisson uncertainties are also added in quadrature following (cite: Gehrels1986a)" (3 Number Counts) [from (cite: Gehrels1986a)]

### Not stated but needed to reproduce (our reading)

- Exact per-map list of 135 maps and their rms
- SNR threshold used for candidate pixels beyond 5 sigma, mask handling details
- Casa version
- Flux deboosting prescription details
- Model code/grid for psi2 and z_cutoff fit
- Redshift info for the sources used

## Analysis recipe

1. **Select archival maps**: Query ALMA archive for Band 3 data in UDS, CDF-S, COSMOS with resolution and sensitivity cuts  
  > "a total of 135 maps were retrieved from almost 20 different projects" (2.1 ALMA Band 3 archival data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Blind source extraction**: SNR maps from uncorrected PB maps, noise = 68th percentile of pixels, 5 sigma threshold, iterative masking  
  > "The noise is assumed to be the $68^{th}$ percentile of the distribution of pixel values of the map" (2.2 Source extraction)
   - software: CASA
   - parameter: threshold 5 sigma; radius 1.3 x primary beam FWHM  
  > "here we adopt a conservative threshold of $5\sigma$ to minimize the contamination fraction" (2.2 Source extraction)
   - assumption: Fluxes scaled to 3 mm with S proportional to nu^(2+beta), beta=1.8  
  > "assuming $S_\nu\propto\nu^{2+\beta}$, with $\beta=1.8$" (Footnote 1)
   - fitting: _not stated_
   - validation: Compared re-reduced fluxes with archive maps  
  > "are in very good agreement with the values measured on the maps available through the archive" (2.1 ALMA Band 3 archival data)
3. **Contamination, completeness, flux boosting**: Inverted maps for false detections; Monte Carlo source injection (100 realizations per SNR bin)  
  > "After 100 realizations per SNR bin, ranging from 3.0 to 7.0 in steps of 0.1" (2.3 Completeness)
   - fitting: _not stated_
   - validation: Recovered within a synthesized beam  
  > "A source is considered recovered if it is detected within a synthesized beam of the input random position." (2.3 Completeness)
4. **Cumulative number counts and fit**: N_i=(1-f_cont)/(zeta A_eff) summed; Monte Carlo and Poisson errors; double power law fit  
  > "were inferred using a minimum $\chi^2$ method through a Levenberg-Marquardt algorithm" (3 Number Counts)
   - fitting: chi-square Levenberg-Marquardt  
  > "were inferred using a minimum $\chi^2$ method through a Levenberg-Marquardt algorithm" (3 Number Counts)
   - validation: Schechter function also tried and rejected  
  > "it reproduce neither the behavior of the data at the brightest flux densities" (3 Number Counts)
5. **Constrain IRLF evolution**: Fit model number counts for psi2 (-6.5 to -2.0) and z_cutoff (9 to 5) by maximum likelihood with flat priors  
  > "through a maximum likelihood approach, using flat prior distributions for both $\psi_2$ and $z_{\rm cutoff}$" (4 Constraining the infrared galaxy luminosity function)
   - assumption: Optically thick SEDs at rest-frame lambda<100 um  
  > "The constraints described above assume optically thick SEDs at rest-frame $\lambda<100\,\rm\mu m$" (4 Constraining the infrared galaxy luminosity function)
   - fitting: maximum likelihood, flat priors  
  > "using flat prior distributions for both $\psi_2$ and $z_{\rm cutoff}$" (4 Constraining the infrared galaxy luminosity function)
   - validation: _not stated_

## Software

- **CASA** : Re-reduction of raw data with natural weighting  
  > "we individually re-reduce the raw data using casa ((cite: McMullin2007a))" (2.1 ALMA Band 3 archival data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Sources detected >5 sigma | 16 | not stated | sources | 2 | The 16 serendipitously-detected 3 mm sources at $>5\sigma$ |
| Effective survey area | 198 | not stated | arcmin^2 | 1 | This compilation covers an effective area of $198\,\rm arcmin^2$ |
| Double power-law alpha | 1.4 | 0.5 | dimensionless | 4 | $\alpha=1.4\pm0.5$ and $\beta=3.4\pm0.5$ |
| Double power-law S0 | 0.11 | +0.22/-0.03 | mJy | 4 | $S_0=0.11^{+0.22}_{-0.03}\rm\,mJy$ |
| psi2 best fit | -4.2 | +1.6/-0.8 | dimensionless | 5 | best-fit value of $\Psi_2=-4.2^{+1.6}_{-0.8}$ |
| DSFG share of CSFRD at z~4-5 | 35-85 | 68% confidence interval | percent | 5 | DSFGs contribute $\approx35-85\%$ of the total CSFRD at $z\approx4-5$ |
| False detection rate at 5 sigma | <=5 | not stated | percent | 3 | a false detection rate of $\lesssim5\%$ is expected at our adopted threshold |

## Qualitative findings


## Claim tuples

- H: Do DSFGs contribute negligibly to the CSFRD at z>4? | E: Compare 3 mm number counts with backward evolution model | R: psi2<-5.3 (dust-poor) not favoured; DSFGs give ~35-85% at z~4-5 | F: DSFG contribution at z>4 is non-negligible | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Schechter-like fit rejected  
  > "The number counts were also fitted with a Schechter-like function" (3 Number Counts)
- How they decided it was enough: _not stated_
- Limitation (authors): Counts likely biased low by cosmic variance; small sample  
  > "These estimations are likely to be low biased by cosmic variance" (3 Number Counts)
- Caveat (inferred, ours): Only 13 sources; Poisson-dominated
- Caveat (inferred, ours): Heterogeneous archival targets may bias blindness
- Caveat (inferred, ours): Model dependent on optically thick assumption
- Caveat (inferred, ours): Most sources lack redshifts

## Reproducibility

- Data public (paper): Public archival data up to May 2018  
  > "up to a public release date of May 2018" (2.1 ALMA Band 3 archival data)
- Products in archive: _not stated_
- Missing: Code for extraction and model
- Missing: Exact map list
- Missing: Model grid
- Data volume (inferred): ~100s GB to ~1 TB for archive continuum maps and raw data
- Score (inferred): 3/5, Public data and clear recipe, but the model code and details are missing.
- Rediscovery candidate: yes, Public archival data and numeric catalog and counts, though the model step is hard.

## Links

- Method: (cite: Casey2018a; Casey2018b) (Backward evolution model)
- Companion: (cite: Wardlow2018a) (Earlier 3 mm detections in ALESS fields)
- Related: ASPECS
- Related: ALESS

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 6,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.00228.S",
  "2015.1.00752.S",
  "2015.1.00861.S",
  "2015.1.00862.S",
  "2015.1.01151.S",
  "2015.1.01222.S",
  "2016.1.00564.S",
  "2016.1.00567.S",
  "2016.1.00754.S",
  "2016.1.00798.S",
  "2016.1.00932.S",
  "2016.1.00967.S",
  "2016.1.01149.S",
  "2016.1.01546.S"
 ],
 "codes_printed_but_missing": [
  "2015.1.00228.S",
  "2015.1.00752.S",
  "2015.1.00861.S",
  "2015.1.00862.S",
  "2015.1.01151.S",
  "2015.1.01222.S",
  "2016.1.00564.S",
  "2016.1.00567.S",
  "2016.1.00754.S",
  "2016.1.00798.S",
  "2016.1.00932.S",
  "2016.1.00967.S",
  "2016.1.01149.S",
  "2016.1.01546.S"
 ],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 28,
  "rate": 0.418
 },
 "evidence_ok": true
}
```
