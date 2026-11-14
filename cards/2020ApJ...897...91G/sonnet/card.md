# The ALMA Spectroscopic Survey in the HUDF: Deep 1.2 mm Continuum Number Counts

`2020ApJ...897...91G` | The Astrophysical Journal 2020 | first author: González-López, Jorge | arXiv: 2002.07199 | DOI: 10.3847/1538-4357/ab765b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies, cosmology
- Question: What are the deep 1.2 mm continuum number counts in the HUDF, do they flatten at faint flux densities, and what fraction of the 1.2 mm extragalactic background light do the detected sources recover?  
  > "We estimate the 1.2 mm number counts to flux levels of <30 \mu Jy in two different ways" (abstract)
- Target **Hubble Ultra Deep Field (ASPECS-LP band 6 mosaic)**: coordinates _not stated_; z/distance counterpart redshifts z=0-4  
  > "The mosaic consists of 85 pointings separated by $11\ensuremath{''}$" (2.1 Survey design); distance from spectroscopic redshifts of NIR counterparts (MUSE and ALMA CO)  
  > "The mosaic consists of 85 pointings separated by $11\ensuremath{''}$" (2.1 Survey design)

## Data provenance

- ALMA projects: 2016.1.00324.L
- bands: Band 6 (1.2 mm), ASPECS-LP, ALMA cycle 4 large program  
  > "The data used in this work correspond to the band 6 observations from ASPECS-LP." (2.1 Survey design)
- frequencies and spectral setup: eight spectral tunings covering 212-272 GHz  
  > "We used eight spectral tunings that cover most of the ALMA band 6 (212–272 GHz, $\approx94\%$ of band 6)." (2.1 Survey design)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.53"x1.08" natural; 2.37"x2.05" tapered  
  > "a tapered image with a rms value of $11.3\thinspace{\rm \mu Jy\thinspace beam^{-1}}$ with a beam size of $2.37\ensuremath{''}\times2.05\ensuremath{''}$" (2.2 Data reduction, calibration and imaging)
- max recoverable scale: _not stated_
- sensitivity: rms 9.3 uJy/beam (deepest region)  
  > "The deepest region of the continuum image has a rms value of $9.3\thinspace{\rm \mu Jy\thinspace beam^{-1}}$ with a beam size of $1.53\ensuremath{''}\times1.08\ensuremath{''}$." (2.2 Data reduction, calibration and imaging)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **HST**: NIR counterparts (F160W) and priors  
  > "We define a counterpart as any bright NIR galaxy ($m_{\rm F160W}\leq27$) that is located within the synthesized beam of the natural or tapered image." (4 Results)
- Other facility **Spitzer-MIPS and Herschel-PACS**: mid-IR priors for faint sample  
  > "We select all the *Spitzer*-MIPS and *Herschel*-PACS detected sources that show 1.2 mm emission with ${\rm S/N}\geq3.0$." (5.4 1.2 mm extragalactic background light)
- External data: Galaxy properties (stellar mass, dust mass, SFR, redshifts) of counterparts from MAGPHYS SED fits  
  > "using the best SED parameters from the associated optical/NIR counterparts (cite: Aravena2019b)" (5.2 Number Counts for different populations) [from (cite: Aravena2019b)]
- External data: Literature number counts at 870um-1.3mm used for comparison  
  > "The studies at 1.1-1.3 millimeters correspond to deep fields and large mosaics in blank and lensing fields" (5.1 Number Counts) [from (cite: Aravena2016; Fujimoto2016; MunozArancibia2018; Franco2018)]
- Simulation/model as data: Model predicted number counts compared  
  > "Figure [5] also presents the 1.2 mm number counts as predicted by different galaxy evolution models (cite: Bethermin2017; Schreiber2017; Lagos2019; Popping2019b)." (5.1 Number Counts)

## Processing

### Calibration

- pipeline or manual: CASA ALMA calibration pipeline with ALMA-provided calibration and flagging  
  > "We processed the data with the CASA ALMA calibration pipeline (cite: McMullin2007), using the calibration and flagging input provided by ALMA." (2.2 Data reduction, calibration and imaging)
- casa version: CASA v.5.4.0-70 (imaging)  
  > "We created the continuum images as well as the data cubes with CASA v.5.4.0-70." (2.2 Data reduction, calibration and imaging)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean, mfs mode  
  > "We obtained the continuum images using the task tclean with natural weighting and multi-frequency synthesis (mfs) mode." (2.2 Data reduction, calibration and imaging)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We obtained the continuum images using the task tclean with natural weighting and multi-frequency synthesis (mfs) mode." (2.2 Data reduction, calibration and imaging)
- uv taper: tapered image to 2.37"x2.05" beam, rms 11.3 uJy/beam  
  > "We chose this tapered beam size because it offers extra sensitivity to slightly extended emission without a significant loss of depth." (2.2 Data reduction, calibration and imaging)
- cell size: _not stated_
- image size: _not stated_
- masking: cleaning boxes on sources with S/N>=5, clean to 20 uJy/beam  
  > "We created the cleaned images by putting cleaning boxes on all the sources with $\rm{S/N}\geq5$ and cleaning down to $20\thinspace{\rm \mu Jy\thinspace beam^{-1}}$." (2.2 Data reduction, calibration and imaging)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: channels with strong emission lines flagged; rms 10.0 uJy/beam  
  > "we proceeded to create a line-free continuum image by flagging all the frequency channels with strong emission lines" (2.2 Data reduction, calibration and imaging)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Source extraction with LineSeeker as for 3 mm continuum  
  > "We performed 2D source extraction using LineSeeker in the same manner as was done for the ASPECS-LP 3 mm continuum image (cite: GL2019)." (3.1 Source search) [from (cite: GL2019)]
- Direct number count recipe  
  > "We followed the same recipe used by (cite: Aravena2016) and (cite: GL2019)" (3.2 Direct number counts) [from (cite: Aravena2016); (cite: GL2019)]
- Flux density measurement method  
  > "We measured the flux densities in the same way as for the ASPECS-LP 3 mm continuum image in (cite: GL2019)." (4 Results) [from (cite: GL2019)]
- Observational setups  
  > "The observational setups used in ASPECS-LP are the same as the ones used in ASPECS-Pilot observations presented in (cite: Walter2016)." (2.1 Survey design) [from (cite: Walter2016)]

### Not stated but needed to reproduce (our reading)

- Image size and cell size for tclean
- Which channels were flagged as line-contaminated
- Exact observation dates, configurations and time on source
- LineSeeker parameters (DBSCAN eps/min samples)
- Grid spacing and sampling for P(D) parameter grid
- Flux density measurement aperture details (deferred to GL2019)
- MAGPHYS settings and galaxy properties (in Aravena2019b)
- Details of the triple power-law fit procedure

## Analysis recipe

1. **Image continuum**: tclean natural weighting mfs, plus tapered and line-free versions  
  > "We used the same procedure to obtain a tapered image with a rms value of $11.3\thinspace{\rm \mu Jy\thinspace beam^{-1}}$" (2.2 Data reduction, calibration and imaging)
   - software: CASA, tclean
   - parameter: clean threshold 20 uJy/beam  
  > "cleaning down to $20\thinspace{\rm \mu Jy\thinspace beam^{-1}}$" (2.2 Data reduction, calibration and imaging)
   - fitting: _not stated_
   - validation: _not stated_
2. **Source extraction, fidelity, completeness**: LineSeeker with DBSCAN on S/N>=2 pixels; fidelity from negative/positive counts; completeness by injecting 20,000 point sources into uv jackknife noise image  
  > "We selected all the pixels with new $\rm{S/N}\geq2$ and grouped them together using Density-Based Spatial Clustering of Applications with Noise (DBSCAN) algorithm" (3.1 Source search)
   - software: LineSeeker
   - parameter: fidelity 50% at S/N=4.3 (natural), 3.3 (tapered)  
  > "($\rm S/N=4.3$ for the natural image and $\rm S/N=3.3$ for the tapered image)" (3.1 Source search)
   - fitting: _not stated_
   - validation: flux boosting ~11% at fidelity 50%, <=3% at S/N~5  
  > "We estimate an excess of $\approx11\%$ in the measured flux density for the sources detected with fidelity equal to $50\%$." (3.1 Source search)
3. **Direct number counts**: sum of fidelity/completeness over bins divided by area; errors Poisson plus 1000 Gaussian resamplings  
  > "We repeated this process 1000 times and measured the scatter per bin." (3.2 Direct number counts)
   - parameter: bins log S = 0.25 differential, 0.1 cumulative; area 1.16e-3 deg^2 (PB>=0.1)  
  > "The size of the bins is $\log{S_{\nu}}=0.25$ for the differential number counts and $\log{S_{\nu}}=0.1$ for the cumulative number counts." (3.2 Direct number counts)
   - fitting: _not stated_
   - validation: repeated with PB>=0.5 and PB>=0.9; faint end unchanged  
  > "the number counts in the faint end remained the same" (3.2 Direct number counts)
4. **Noise reference images via jackknife**: invert every second visibility (uv plane); randomly invert half of channels in dirty cube 100 times  
  > "we randomly inverted (multiply by $-1$) half of the channels in the dirty cube created for the band 6 ASPECS-LP data." (3.3.2 Noise reference images)
   - software: CASA
   - parameter: channel weights w=1/sigma_i^2  
  > "We calculated the weights by channels as $w=1/\sigma^2_i$" (3.3.2 Noise reference images)
   - fitting: _not stated_
   - validation: two methods agree: 9.21 vs 9.03 uJy/beam  
  > "Both independent jackknife processes return very similar distributions." (3.3.2 Noise reference images)
5. **P(D) forward modeling**: inject sources following double power law into blank image, convolve with dirty beam, add noise image, compare pixel histogram to dirty image; 1000 iterations per parameter set  
  > "This process was repeated 1000 times to obtain the pixel distribution of noise plus injected sources for a given combination of parameters." (3.3.3 P(D) analysis)
   - software: tclean
   - parameter: N0=1-100e3 mJy^-1 deg^-2, S0=0.05-1.0 mJy, alpha=1.5-5, beta -2 to 2; fluxes 0.03-2 mJy; histogram bins 4.3 uJy/beam  
  > "$\alpha=1.5\text{--}5$ and $\beta$ between $-2$ and $+2$" (3.3.3 P(D) analysis)
   - assumption: double power-law number counts  
  > "we assumed that the differential number counts can be well described by a double power-law function" (3.3.3 P(D) analysis)
   - fitting: grid search minimizing Cash statistic C=-2lnL with Poisson likelihood  
  > "we minimize the associated quantity given by" (3.3.3 P(D) analysis)
   - validation: compared to direct counts  
  > "the results from the two independent method show excellent agreement" (5.1 Number Counts)
6. **EBL recovery**: triple power-law fit to counts, integrated from 35 uJy and from zero; compare to summed source flux  
  > "We integrated from $35{\rm \thinspace\mu Jy}$ to infinity and obtained an intensity of $6.3\pm0.2{\rm \thinspace Jy\thinspace deg^{-2}}$." (5.4 1.2 mm extragalactic background light)
   - fitting: TPL with F1 parameters within 1 sigma P(D) range  
  > "we obtained a best-fit of $S_{1}=1.7\pm0.2\thinspace{\rm mJy}$" (5.4 1.2 mm extragalactic background light)
   - validation: _not stated_

## Software

- **CASA** 5.4.0-70: calibration pipeline, tclean imaging  
  > "We created the continuum images as well as the data cubes with CASA v.5.4.0-70." (2.2 Data reduction, calibration and imaging)
- **LineSeeker** : source extraction and fidelity  
  > "We performed 2D source extraction using LineSeeker" (3.1 Source search)
- **DBSCAN** : pixel clustering  
  > "grouped them together using Density-Based Spatial Clustering of Applications with Noise (DBSCAN) algorithm" (3.1 Source search)
- **MAGPHYS** : stellar mass, dust mass, SFR  
  > "We used the Multi-wavelength Analysis of Galaxy Physical Properties (cite: daCunha2008; daCunha2015) to estimate galaxy properties" (4 Results)
- **Astropy** : listed in software  
  > "Astropy (cite: Astropy)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum image rms | 9.3 | not stated | uJy/beam | 1 | a rms value of $9.3\thinspace{\rm\mu Jy\thinspace beam^{-1}}$ |
| Number of high-fidelity sources | 35 | not stated | sources | 2 | We detect 35 sources at high significance (Fidelity $\geq0.5$), 32 of these have well characterized near-infrared HST counterparts. |
| Intrinsic noise (uv jackknife) | 9.21 | not stated | uJy/beam | 4 | The rms measured in the $uv$-plane noise is $9.21\thinspace{\rm \mu Jy\thinspace beam^{-1}}$ |
| Differential DPL break S0 | 0.10 | ±0.02 | mJy | 5 | $0.10 \pm 0.02$ |
| Differential DPL N0 | 4.4e4 | ±0.6e4 | mJy^-1 deg^-2 | 5 | $(4.4\pm0.6)\times10^4\thinspace{\rm mJy^{-1}deg^{-2}}$ |
| EBL recovered from 35 uJy to infinity | 6.3 | ±0.2 | Jy deg^-2 | 6 | obtained an intensity of $6.3\pm0.2{\rm \thinspace Jy\thinspace deg^{-2}}$ |
| Total EBL (0 to infinity) | 6.8 | ±0.4 | Jy deg^-2 | 6 | obtained an intensity of $6.8\pm0.4{\rm \thinspace Jy\thinspace deg^{-2}}$ |
| TPL break S1 | 1.7 | ±0.2 | mJy | 6 | $S_{1}=1.7\pm0.2\thinspace{\rm mJy}$ |

## Qualitative findings

- Flattening of counts below ~0.1 mJy, attributed to lack of dust emission in galaxies with M*<~1e10 Msun at 1<z<2  
  > "the flattening of the number counts at $S_{\nu}<0.1$ mJy is produced by the lack of continuum emission in galaxies with ${\rm M}_{*}\lesssim10^{10}{{\rm M}_{\odot}}$ at $1<z<2$" (5.3 Causes for the flattening of the number counts)

## Claim tuples

- H: Do 1.2 mm counts flatten below ~0.1 mJy? | E: Direct counts and P(D) analysis | R: Both show a break at S0~0.1 mJy | F: Counts flatten at faint end | **supported**
- H: How much of the 1.2 mm EBL from HUDF galaxies is resolved? | E: Integrate TPL fit and sum detected fluxes | R: 6.3 vs 6.8 Jy/deg^2 | F: ~93% recovered, ~100% with lower-fidelity sample | **supported**
- H: Is the HUDF EBL consistent with Planck estimates? | E: Compare 3 sigma upper limit | R: <8 Jy/deg^2 vs 14-24 | F: In tension with Planck; cosmic variance insufficient | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Jackknife noise needed because tclean residual contaminated by faint sources and confusion  
  > "We could not use the residual map created by tclean as noise reference because it can be contaminated by sources not bright enough to be selected for cleaning boxes" (3.3.1 Input needed for analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Three sources lack NIR counterparts and are likely false detections  
  > "make them good candidates to be false detections" (4 Results)
- Caveat (inferred, ours): Small field; cosmic variance
- Caveat (inferred, ours): Completeness from tapered image applied to all sources
- Caveat (inferred, ours): Counts for populations assume complete HUDF population and depend on MAGPHYS properties from a companion paper
- Caveat (inferred, ours): Image-plane source injection rather than uv-plane

## Reproducibility

- Data public (paper): ALMA large program data cited by project code; public status not explicitly stated  
  > "This Paper makes use of the ALMA data\ ADS/JAO.ALMA#2016.1.00324.L." (Acknowledgments)
- Products in archive: _not stated_
- Code: LineSeeker on GitHub  
  > "[LineSeeker](https://github.com/jigonzal/LineSeeker)" (Software)
- Missing: P(D) code not released
- Missing: Companion paper galaxy properties
- Missing: Image sizes and LineSeeker parameters
- Data volume (inferred): Large: ~85-pointing band 6 mosaic with eight tunings; several hundred GB to TB of raw data
- Score (inferred): 3/5, Public data and main recipe given, but imaging parameters, P(D) code and companion-paper properties are missing.
- Rediscovery candidate: no, Large mosaic and custom P(D) code make full reproduction heavy and underspecified.

## Links

- Method: (cite: GL2019) (ASPECS-LP 3 mm continuum source extraction and flux measurement)
- Method: (cite: Aravena2016) (number counts recipe)
- Companion: (cite: Aravena2019b) (counterpart characterization and galaxy properties)
- Companion: (cite: Popping2019b) (theoretical models and cosmic variance)
- Related: ASPECS-Pilot
- Related: ASPECS-LP
- Related: HUDF/XDF

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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 51,
  "rate": 0.607
 },
 "evidence_ok": true
}
```
