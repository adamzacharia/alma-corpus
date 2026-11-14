# The Atacama Large Millimeter/submillimeter Array Spectroscopic Survey in the Hubble Ultra Deep Field: CO Emission Lines and 3 mm Continuum Sources

`2019ApJ...882..139G` | The Astrophysical Journal 2019 | first author: González-López, Jorge | arXiv: 1903.09161 | DOI: 10.3847/1538-4357/ab3105

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: How to reliably search for emission lines and continuum sources in the ASPECS-LP 3 mm cube, and what are the resulting CO line and 3 mm continuum samples and 3 mm number counts  
  > "We here present our search strategy for emission lines and continuum sources in the HUDF. We compare several line search algorithms used in the literature" (abstract)
- Target **Hubble Ultra Deep Field (ASPECS-LP footprint)**: coordinates _not stated_; z/distance CO redshifts z=1.037-3.601 (Table 6); continuum sources median z~2.5  
  > "was mapped with 17 Nyquist-spaced pointings in band 3 cover an area of 4.6 arcmin$^2$" (2.1 Survey design); distance from NIR spectroscopic/photometric counterpart redshifts, CO line  
  > "was mapped with 17 Nyquist-spaced pointings in band 3 cover an area of 4.6 arcmin$^2$" (2.1 Survey design)

## Data provenance

- ALMA projects: 2016.1.00324.L
- bands: Band 3 (3 mm), 84.176-114.928 GHz  
  > "Emission lines rest-frequency and corresponding redshift ranges for the band 3 line scan (84.176–114.928 GHz)." (Table 1)
- frequencies and spectral setup: five tunings, FDM, 1875 MHz per spw, final channel 7.813 MHz (~23.5 km/s at 99.5 GHz)  
  > "with five tunings that cover most of the ALMA band 3" (2.1 Survey design); "result in a final channel resolution of 7.813 MHz" (2.2 Data reduction, calibration and imaging)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-3  
  > "The ASPECS-LP observations in band 3 were made in antenna configuration C40-3." (2.1 Survey design)
- baselines: _not stated_
- angular resolution: 1.5''x1.31'' (high freq) to 2.05''x1.68'' (low freq)  
  > "synthesized beam sizes between $1.5\ensuremath{''}\times1.31\ensuremath{''}$ at the high frequencies and $2.05\ensuremath{''}\times1.68\ensuremath{''}$ at low frequencies" (2.2 Data reduction, calibration and imaging)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 3.8 uJy/beam in deepest region  
  > "The deepest region of the continuum image has an rms value of $3.8\thinspace{\rm \mu Jy\thinspace beam^{-1}}$" (2.2 Data reduction, calibration and imaging)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=1-0 to 7-6 (115.271-806.652 GHz)
- Line: [CI] 1-0, 2-1 (492.161, 809.342 GHz)
- Other facility **ALMA 1.2 mm map (ASPECS-Pilot + Dunlop2017)**: 1.2 mm continuum flux densities for the 3 mm sources  
  > "created by combining the observations from ASPECS-Pilot at 1.2 mm and from 1.3 mm ALMA map in the UDF (cite: Dunlop2017)" (4.2 Detected continuum sources)
- Other facility **NIR/optical spectroscopy and photometry**: counterpart redshifts to identify lines  
  > "Eleven of the candidates have NIR counterpart galaxies with spectroscopic redshifts, allowing for a secure identification of the detected emission lines." (4.1 Detected emission lines)
- External data: ASPECS-Pilot band 3 data and source list for comparison  
  > "The details about the ASPECS-Pilot observations were presented in (cite: Walter2016)" (2.1 Survey design) [from (cite: Walter2016)]
- External data: 1.1 mm number counts compiled for extrapolation to 3 mm  
  > "We make use of the results obtained by (cite: Franco2018), which takes the number counts of several published studies" (5.3 3 mm number counts) [from (cite: Franco2018)]
- External data: 3 mm number counts from ALMA archive for comparison  
  > "We also compare our number counts with the observed 3 mm number counts presented by (cite: Zavala2018)." (5.3 3 mm number counts) [from (cite: Zavala2018)]
- Simulation/model as data: Simulated cubes via simobserve with injected Gaussian lines for method comparison  
  > "The data cubes were created using the CASA task simobserve with a similar setup to the ASPECS-LP band 3 observations." (3.2.1 Lines detected from Simulations)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline and own scripts similar to manual calibration; own cube used  
  > "The data was processed using both the CASA ALMA calibration pipeline (cite: McMullin2007) and our own scripts (cite: Aravena2016a)" (2.2 Data reduction, calibration and imaging)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "We imaged the 3 mm cube with natural weighting using the task tclean" (2.2 Data reduction, calibration and imaging)
- deconvolver: none; analysis on dirty cube  
  > "The lack of very bright sources in our cubes allows us to perform our analysis on the ‘dirty’ cube" (2.2 Data reduction, calibration and imaging)
- weighting robust: natural weighting  
  > "We imaged the 3 mm cube with natural weighting using the task tclean" (2.2 Data reduction, calibration and imaging)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: mosaic PB correction; area with PB>=0.5 is 4.6 arcmin2, search area PB>=0.2  
  > "which is of 7 arcmin$^2$ within mosaic primary beam correction $\geq0.2$" (3.3 Fidelity)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: continuum beam 2.08''x1.71''; per-channel beams in cube  
  > "a beam size of $2.08\ensuremath{''}\times1.71\ensuremath{''}$" (2.2 Data reduction, calibration and imaging)
- final rms: 3.8 uJy/beam continuum (deepest)  
  > "The deepest region of the continuum image has an rms value of $3.8\thinspace{\rm \mu Jy\thinspace beam^{-1}}$" (2.2 Data reduction, calibration and imaging)

### Inherited from earlier work

- Own calibration scripts  
  > "our own scripts (cite: Aravena2016a), which follow a similar scheme to the ALMA manual calibration scripts" (2.2 Data reduction, calibration and imaging) [from (cite: Aravena2016a)]
- Spectral setup same as ASPECS-Pilot  
  > "The spectral setup of the ASPECS-LP is the same as the one used in the ASPECS-Pilot" (2.1 Survey design) [from (cite: Walter2016)]
- LineSeeker method  
  > "LineSeeker is the method used in the search for emission lines in the ALMA Frontier Fields survey (cite: GL2017c)." (3.1.1 LineSeeker) [from (cite: GL2017c)]
- Independent elements = twice number of beams  
  > "A good estimate of the number of independent elements is twice the number of beams contained in the map (cite: Condon1997; Condon1998; Dunlop2017)." (3.3 Fidelity) [from (cite: Condon1997; Condon1998; Dunlop2017)]

### Not stated but needed to reproduce (our reading)

- Number and settings of LineSeeker S/N thresholds and DBSCAN parameters
- tclean cell size, image size and mask details
- Flux calibrators and flux scale uncertainty
- MCMC sampler, priors and likelihood for Gaussian line fits
- Which channels removed for continuum image
- Details of mosaic PB correction (Decarli2019)
- Dust SED extrapolation code and details for number counts

## Analysis recipe

1. **Calibrate and image 3 mm cube and continuum**: Pipeline plus own scripts; tclean natural weighting, per-channel beams, 7.813 MHz channels; continuum by collapsing all channels  
  > "Finally, the continuum image was created by collapsing all the spectral windows and channels." (2.2 Data reduction, calibration and imaging)
   - software: CASA, tclean
   - fitting: _not stated_
   - validation: Compared rms of own cube with pipeline cube  
  > "the final rms appears consistent with the one computed from the cube provided by the ALMA pipeline" (2.2 Data reduction, calibration and imaging)
2. **Compare line search algorithms**: Run LineSeeker, FindClump, MF3D on simulated cubes with injected lines and on real cube; compare S/N  
  > "The simulations were repeated until 5000 simulated lines were produced." (3.2.1 Lines detected from Simulations)
   - software: LineSeeker, FindClump, MF3D, simobserve, SExtractor, scikit-learn
   - parameter: Gaussian kernel sigma_GK 0-19 (LineSeeker); top-hat N=1-9 (FindClump); spatial kernels FWHM 0-4'' (MF3D)  
  > "which ranges from 0 up to 19" (3.1.1 LineSeeker)
   - fitting: _not stated_
   - validation: S/N ratios of methods agree; ~99% recovery in simulation  
  > "Both methods performed similarly in the detection of the injected emission lines, recovering around $\approx99\%$ of the lines." (3.2.1 Lines detected from Simulations)
3. **Estimate fidelity**: Fidelity = 1 - N_neg/N_pos using negative lines per kernel; erf function fit to negative S/N histogram; select Fidelity>=0.9  
  > "we fit a function of the form $N(1 - \mathop{\mathrm{erf}}(\rm SN / \sqrt{2}\sigma))$ to the S/N histogram of negative lines" (3.3 Fidelity)
   - software: LineSeeker
   - parameter: Fidelity >= 0.9  
  > "We select as reliable all the emission lines that have ${\rm Fidelity}\geq0.9$." (3.3 Fidelity)
   - assumption: Negative lines are produced by noise only; noise symmetric around 0  
  > "We use the negative lines as reference to estimate the fidelity, assuming noise around 0, typical of interferometric data." (3.3 Fidelity)
   - fitting: N and sigma free in erf function  
  > "with $\mathop{\mathrm{erf}}$ being the error function and $N$ and $\sigma$ free parameters" (3.3 Fidelity)
   - validation: All 6 continuum sources detected at 1.2 mm; ASPECS-Pilot S/N>=6 confirmed by counterparts  
  > "The six candidates are detected in the 1.2 mm map, fully supporting the fidelity estimates and the reliability of the sample." (4.2 Detected continuum sources)
4. **Compute completeness**: Inject 5000 Gaussian point-source lines (50 per iteration) into real cube; recovered if Fidelity>=0.9; for continuum inject 10,000 point sources, recovered at S/N>=4.6  
  > "We repeated this process until 5000 emission lines were injected." (3.4 Completeness)
   - software: LineSeeker
   - parameter: peaks 0-2 mJy/beam, FWHM 0-~1000 km/s, 84.2-114.2 GHz  
  > "The line peaks range between 0 and 2 mJy beam$^{-1}$" (3.4 Completeness)
   - fitting: _not stated_
   - validation: _not stated_
5. **Characterise detected lines and identify transitions**: Gaussian profile fit with MCMC to PB-corrected spectra; resolved if voxel S/N>=2 flux >=10% above central; identify via NIR counterpart redshifts  
  > "we present the results from fitting a Gaussian profile to the observed spectra using a Markov chain Monte Carlo (MCMC) sampling algorithm." (4.1 Detected emission lines)
   - fitting: _not stated_
   - validation: NIR spectroscopic redshifts agree with CO redshifts  
  > "In all cases the NIR spectroscopic redshift agrees very well with that obtain from the CO emission line." (4.1 Detected emission lines)
6. **Derive 3 mm number counts and compare with extrapolations**: N(S_i)=(1/A) sum P_i/C_i with bins of 0.25 dex in logS, fidelity and PB-corrected completeness; compare with synchrotron extrapolations and 1.1 mm counts scaled to 3 mm  
  > "The size of the bins is $\log{S_{\nu}}=0.25$ and we use all the source candidates with ${\rm Fidelity}\geq0.9$ listed in Tab. [7]" (5.3 3 mm number counts)
   - parameter: Area A = 1.46e-3 deg2  
  > "$A$ is the total area of the observations ($1.46\times10^{-3}\thinspace{\rm deg^{2}}$)" (5.3 3 mm number counts)
   - assumption: Modified blackbody, beta=1.5-2.0, T=25-40 K, z=2.5, CMB effects  
  > "For the dust emissivity index we use a range of $\beta=1.5-2.0$" (5.3 3 mm number counts)
   - fitting: _not stated_
   - validation: Compared with Sadler2008, Tucci2011, SPT and Zavala2018 counts  
  > "We find that our number counts are $\sim3\times$ lower than the best-fit function" (5.3 3 mm number counts)

## Software

- **CASA** : Pipeline calibration, tclean imaging, simobserve  
  > "We imaged the 3 mm cube with natural weighting using the task tclean" (2.2 Data reduction, calibration and imaging)
- **LineSeeker** : Emission line and continuum search, fidelity, completeness  
  > "We have made available online LineSeeker, the code used to search for emission lines in this work." (Acknowledgments)
- **FindClump** : Alternative line search  
  > "FindClump uses a top-hat convolution of the data cubes in the spectral axis." (3.1.2 FindClump)
- **MF3D** : Alternative line search with spatial kernels  
  > "it also implements convolutions in the spatial axis to look for spatially resolved emission lines" (3.1.3 MF3D)
- **SExtractor** : Searching for features in FindClump  
  > "FindClump searches for high significance features in channel by channel basis using SExtractor (cite: Bertin1996)." (3.1.2 FindClump)
- **scikit-learn (DBSCAN)** : Grouping voxels into line candidates  
  > "available in the Python package Scikit-learn (cite: scikit-learn)" (3.1.1 LineSeeker)
- **astropy** : listed in software section  
  > "astropy (cite: Astropy), SExtractor (cite: Bertin1996)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of emission lines with Fidelity>=0.9 | 16 | not stated | dimensionless | 3 | We present all the 16 emission–line candidates for which the condition of ${\rm Fidelity}\geq0.9$ is fulfilled. |
| Number of continuum sources with Fidelity>=0.9 | 6 | not stated | dimensionless | 3 | We identified six continuum source candidates with a ${\rm Fidelity}\geq0.9$. |
| S/N ratio FindClump/LineSeeker | 1.00 | +0.06/-0.04 | dimensionless | 2 | the ratio between the S/N obtained with FindClump and LineSeeker is of $1.00^{+0.06}_{-0.04}$ |
| Median FWHM of secure lines | 331 | not stated | km/s | 5 | the secure positive lines have a flat FWHM distribution and a median value of $\approx331{{\rm \thinspace km\thinspace s}^{-1}}$ |
| Cumulative 3 mm counts, 17.78-31.62 uJy bin | 5940 | +2579/-1995 | deg^-2 | 6 | / 17.78–31.62 / -1.625 / 3 / 5940 / 1995 / 2579 / |
| Mean beta of continuum sources (T=35 K) | 1.6 | 0.2 | dimensionless | 6 | average value $\beta=1.6\pm0.2$ obtained for our continuum sources when assuming a dust temperature of 35 K |
| 3 mm flux of ASPECS-LP-3mm.C01 | 32.5 | 3.8 | uJy | 5 | $32.5 \pm 3.8$ |

## Qualitative findings

- All 16 line sources have optical/IR counterparts; 3 mm continuum sources all detected at 1.2 mm  
  > "Comparing these sources to multi-wavelength data we find that all sources have optical/infrared counterparts." (abstract)

## Claim tuples

- H: Different line search algorithms give equivalent significance | E: Compared LineSeeker, FindClump, MF3D on simulations and real cube | R: S/N ratios agree within scatter; FindClump slightly higher at low S/N | F: Three methods effectively equivalent | **supported**
- H: Line width must be accounted for in significance | E: Fidelity from negative lines per kernel width | R: 16 lines with fidelity>=0.9; four unconfirmed Pilot sources mostly narrow | F: Width-aware fidelity gives reliable sample | **supported**
- H: 3 mm sub-mJy counts are dominated by dust rather than synchrotron | E: Number counts from six sources, compared with extrapolations | R: Counts order of magnitude above synchrotron extrapolation; match 1.1 mm counts with beta=1.5, T=35 K, z=2.5 | F: Dust-dominated population | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Matched filtering over varying widths with negative-detection fidelity for unbiased line search  
  > "Without any priori knowledge of positions and frequencies for the lines, we need to use some unbiased method to search for emission lines." (3.1 Methods)
- Alternative: Combining Pilot and LP data rejected due to artifacts  
  > "We chose to work with both datasets separately because the combination injected artifacts in the data cubes" (2.1 Survey design)
- Alternative: MF3D.18 excluded as only found by one method  
  > "we leave it out of the list of selected line candidates" (3.2.2 Lines detected from observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Possible missed extended 3 mm sources beyond the beam  
  > "We could be missing a large population of sources at 3 mm if their emission is extended beyond our already coarse beam size." (5.3 3 mm number counts)
- Caveat (inferred, ours): Small continuum sample (six sources) gives large Poisson uncertainties
- Caveat (inferred, ours): Fidelity depends on Gaussian-noise assumption and negative-peak symmetry
- Caveat (inferred, ours): Number-count discrepancy with Zavala2018 only partly explained

## Reproducibility

- Data public (paper): ALMA data ADS/JAO.ALMA#2016.1.00324.L; LineSeeker code public on GitHub  
  > "This Paper makes use of the ALMA data\
ADS/JAO.ALMA#2016.1.00324.L." (Acknowledgments)
- Products in archive: _not stated_
- Code: LineSeeker released at github.com/jigonzal/LineSeeker  
  > "[LineSeeker](https://github.com/jigonzal/LineSeeker)" (Software)
- Missing: Detailed imaging parameters
- Missing: Decarli2019 mosaic and PB details
- Missing: MCMC fit setup
- Missing: FindClump and MF3D code availability
- Data volume (inferred): Several hundred GB raw; cubes tens of GB
- Score (inferred): 3/5, Public data and public LineSeeker code with detailed method, but imaging and calibration details are sparse and rely on companion papers.
- Rediscovery candidate: yes, Data are public, the search recipe is described and the results (line and continuum source lists, counts) are numeric.

## Links

- Method: (cite: GL2017c) (LineSeeker method)
- Method: (cite: Walter2016) (ASPECS-Pilot and FindClump)
- Method: (cite: Pavesi2018) (MF3D method)
- Companion: (cite: Decarli2019) (ASPECS-LP overview, CO luminosity function)
- Companion: (cite: Boogaard2019) (Properties of line galaxies with MUSE)
- Companion: (cite: Aravena2019) (Molecular gas content of line galaxies)
- Companion: (cite: Popping2019) (Cosmic molecular gas density implications)
- Related: ASPECS-Pilot
- Related: ALMA Frontier Fields
- Related: COLDZ

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
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
  "facts": 89,
  "stated": 57,
  "rate": 0.64
 },
 "evidence_ok": true
}
```
