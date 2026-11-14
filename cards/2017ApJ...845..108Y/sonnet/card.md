# Blind Millimeter Line Emitter Search using ALMA Data Toward Gravitational Lensing Clusters

`2017ApJ...845..108Y` | The Astrophysical Journal 2017 | first author: Yamaguchi, Yuki | arXiv: 1707.05547 | DOI: 10.3847/1538-4357/aa80e0

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: high_z_galaxies, nearby_galaxies, cosmology
- Question: Constrain CO and [CII] luminosity functions via a blind line emitter search in ALMA Band 6 single-tuning data toward gravitational lensing clusters  
  > "We present the results of a blind millimeter line emitter search using ALMA Band 6 data with a single frequency tuning toward four gravitational lensing clusters" (abstract)
- Target **RXJ1347.5-1145**: coordinates _not stated_; z/distance z_cluster = 0.451  
  > "RXJ1347.5$-$1145 | 0.451 | 4.75 | 265 | 155" (Table 1); distance from _not stated_
- Target **Abell S0592**: coordinates _not stated_; z/distance z_cluster = 0.222  
  > "Abell S0592 | 0.222 | 3.63 | 265 | 150" (Table 1); distance from _not stated_
- Target **MACS J0416.1-2403**: coordinates _not stated_; z/distance z_cluster = 0.397  
  > "MACS J0416.1$-$2403 | 0.397 | 4.45 | 263 | 73" (Table 1); distance from _not stated_
- Target **Abell 2744**: coordinates _not stated_; z/distance z_cluster = 0.308  
  > "Abell 2744 | 0.308 | 4.26 | 263 | 91" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00724.S, 2013.1.00999.S, 2013.1.00718.S
- bands: Band 6, single frequency tuning (~8 GHz)  
  > "using ALMA Band 6 data with only a single frequency tuning (i.e., observed frequency range $\simeq$ 8 GHz)" (Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15.1-348.5 m (35-38 antennas) for RXJ1347 and Abell S0592  
  > "The minimum and maximum baselines were 15.1 and 348.5 m, respectively." (2.1 ALMA data)
- angular resolution: approx. 1''-1.5'' for cubes  
  > "The achieved angular resolutions of the 3D data cubes are approximately 1$''$–1.$''$5." (2.1 ALMA data)
- max recoverable scale: _not stated_
- sensitivity: 60 MHz cube: 1.4, 1.2, 0.73, 0.95 mJy/beam; 100 MHz: 1.2, 1.0, 0.56, 0.77 mJy/beam  
  > "$\sigma\simeq$ 1.4, 1.2, 0.73, and 0.95 mJy beam$^{-1}$ with 60 MHz binning" (3 Results)
- time on source: 2.26, 1.91, 8.50, 7.89 hrs total observation time  
  > "(10) Total observation time." (Table 1)
- observing dates: April 9 and 10, 2015 (RXJ1347, Abell S0592)  
  > "on April 9 and 10, 2015" (2.1 ALMA data)
- pi or archival as stated: _not stated_
- Line: CO 3-2, 4-3, 5-4 (not stated)
- Line: [CII] 158 um (not stated)
- Other facility **HST**: Optical/NIR images of the clusters; counterpart check for the candidate  
  > "images of these gravitational lensing clusters obtained by the *Hubble Space Telescope* (*HST*) are displayed in Figure" (Introduction)
- External data: GLAFIC lens models v3.0 and MCMC chains for MACS J0416 and Abell 2744  
  > "we use public `GLAFIC` mass models (version 3.0) that are available at Space Telescope Science Institute (STScI) website" (4 CO and [CII] luminosity functions) [from (cite: kawamata2016)]
- External data: Semi-analytical model predictions of CO and [CII] luminosity functions  
  > "we also show the predictions based on semi-analytical cosmological models by (cite: obreschkow2009a; obreschkow2009b), (cite: lagos2012), and (cite: popping2016)" (4.1 CO luminosity functions) [from (cite: obreschkow2009a; obreschkow2009b; lagos2012; popping2016)]
- External data: ASPECS luminosity function results and [CII] LF from Herschel for comparison  
  > "observational results of ASPECS (cite: aravena2016) and (cite: hayatsu2017)" (4.2 [CII] luminosity function) [from (cite: aravena2016; hayatsu2017; hemmati2017)]
- Simulation/model as data: Lens mass models for RXJ1347 (Kitayama et al. in prep.) and Abell S0592 (Oguri et al. in prep.)  
  > "we use mass models obtained by Kitayama et al. in preparation (for RXJ1347.5$-$1145) and Oguri et al. in preparation (for Abell S0592)" (4 CO and [CII] luminosity functions)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Started from calibrated measurement sets  
  > "From the calibrated measurement sets of clusters, we create three-dimensional (3D) data cubes" (2.1 ALMA data)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN, dirty cubes, 60 and 100 MHz channels  
  > "The calibrated visibilities are Fourier transformed using the task CLEAN in the Common Astronomy Software Application" (2.1 ALMA data)
- deconvolver: None (dirty cubes, no CLEAN deconvolution)  
  > "we use cubes without beam deconvolution employing the CLEAN algorithm" (2.1 ALMA data)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Noise computed on cubes before primary beam correction  
  > "we use the data cubes before the correction of the primary beam attenuation pattern to calculate the standard deviations" (2.2 Methods of line emitter search)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- MCMC lens-model uncertainty approach  
  > "We use Markov Chain Monte Carlo (MCMC) methods to estimate model uncertainties as with the case of (cite: kawamata2016)." (4 CO and [CII] luminosity functions) [from (cite: kawamata2016)]
- Assumed line width of 200 km/s for CO  
  > "we assume $\Delta V=$ 200 km s$^{-1}$, as presumed in (cite: decarli2016)" (3 Results) [from (cite: decarli2016)]
- Assumed line width of 300 km/s for [CII]  
  > "we assume $\Delta V$ = 300 km s$^{-1}$ as explained in (cite: aravena2016)" (3 Results) [from (cite: aravena2016)]

### Not stated but needed to reproduce (our reading)

- CASA version and CLEAN parameters (cell size, image size, weighting/robust, spectral window handling)
- Whether the calibration was archive-delivered or re-done
- Exact per-channel noise estimation method (region, clipping)
- Lens models for RXJ1347 and Abell S0592 are unpublished
- Details of the volume computation (S/N limit per pixel, magnification map handling)
- Spectral setup details for 2013.1.00999.S and 2013.1.00718.S
- Recipe for reanalysis of ASPECS data beyond 'following our procedure'

## Analysis recipe

1. **Make dirty 3D cubes**: Fourier transform calibrated visibilities with CLEAN without deconvolution at 60 and 100 MHz binning for each spectral window  
  > "we create three-dimensional (3D) data cubes against each spectral window with two different frequency resolutions, i.e., 60 and 100 MHz" (2.1 ALMA data)
   - software: CASA
   - fitting: _not stated_
   - validation: No strong emission above 6 sigma in dirty cubes  
  > "no strong emission above 6$\sigma$ is found in these cubes" (2.1 ALMA data)
2. **Build S/N cubes and find candidates**: Divide each channel by its standard deviation, run CLUMPFIND for peak S/N > 5, remove spurious candidates by eye (not S/N>3 in adjacent channel)  
  > "we deem line emitter candidates that were not detected with a S/N $>$ 3 in any channel adjacent to their peak channel as spurious and exclude them." (2.2 Methods of line emitter search)
   - software: CLUMPFIND
   - parameter: Delta S = 2 sigma, S_start = 4 sigma  
  > "$\Delta S = 2\sigma$ and $S_\mathrm{start} = 4\sigma$" (2.2 Methods of line emitter search)
   - fitting: S/N distributions fitted with Gaussians  
  > "The S/N distributions are well fitted by Gaussian functions, which also support non-detections" (3 Results)
   - validation: Noise histograms symmetric; negative tail compared with candidate  
  > "the negative tail of the noise distribution of the 60 MHz-binning data cubes also extends to S/N = $-4.5$" (3 Results)
3. **Compute co-moving survey volumes using lens models**: Use GLAFIC lens models with 100 random MCMC parameter sets to get volume as function of intrinsic sensitivity; uncertainty is max-min range  
  > "From the MCMC chain we randomly pick 100 parameter sets to estimate the error in our volume estimate from the mass model uncertainty." (4 CO and [CII] luminosity functions)
   - software: GLAFIC
   - parameter: Luminosity bins from 3 sigma limiting apparent luminosity to 0.5 dex higher  
  > "We define luminosity bins to range from our 3$\sigma$ limiting apparent luminosity (see Section [3](#sec:results)) to a 0.5-dex higher luminosity." (4 CO and [CII] luminosity functions)
   - assumption: Lambda CDM: Omega_M=0.3, Omega_Lambda=0.7, H0=70  
  > "$\Omega_M = 0.3$, $\Omega_\Lambda = 0.7$, and $H_0 =$ 70 km s$^{-1}$ Mpc$^{-1}$" (Introduction)
   - fitting: _not stated_
   - validation: Cross-check of volume at mu~5 for CO(4-3) against table value  
  > "is estimated to be $V_\mathrm{com}\simeq$ 14 Mpc$^3$, which is comparable with Table" (4 CO and [CII] luminosity functions)
4. **Derive upper limits on luminosity function densities**: 1 sigma Poisson upper limits (Gehrels 1986) divided by volume; compare with models and ASPECS reanalysed with same procedure  
  > "The 1$\sigma$ confidence upper limits on the densities of line emitters, which are calculated by using the Poisson statistics by (cite: gehrels1986)." (Table 2)
   - assumption: No CO excitation conversion to CO(1-0)  
  > "we do not convert $L^{\prime}_{\mathrm{CO(3\mathchar`-2)}}$, $L^{\prime}_{\mathrm{CO(4\mathchar`-3)}}$, and $L^{\prime}_{\mathrm{CO(5\mathchar`-4)}}$ into $L^{\prime}_{\mathrm{CO(1\mathchar`-0)}}$" (4.1 CO luminosity functions)
   - fitting: _not stated_
   - validation: Reanalysis of ASPECS recovers its two known lines  
  > "In our procedure, we detect two emission lines, which are detected in ASPECS as 1mm.1 and 1mm.2" (4.1 CO luminosity functions)

## Software

- **CASA** : CLEAN to make dirty cubes  
  > "using the task CLEAN in the Common Astronomy Software Application" (2.1 ALMA data)
- **CLUMPFIND** : 3D S/N cube line emitter search  
  > "we apply `CLUMPFIND` software (cite: williams1994) to the 3D S/N cubes" (2.2 Methods of line emitter search)
- **GLAFIC** 3.0 (public models): Lens mass models and magnification/volume  
  > "we used gravitational lensing models constructed with the `GLAFIC` software" (4 CO and [CII] luminosity functions)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 3 sigma limiting apparent L'CO(3-2) at z~0.3 | 5.5e8 | not stated | K km/s pc^2 | 2 | $\mu L^{\prime}_{\mathrm{CO}}$ $\simeq$ $5.5\times10^8$, $1.8\times10^{9}$, and $2.9\times10^{9}$ K km s$^{-1}$ pc$^2$ |
| Peak S/N of candidate RXJ1347-emitter1 (60 MHz) | 4.5 | not stated | dimensionless | 2 | RXJ1347-emitter1 is detected with 4.5$\sigma$ at the peak channel in the 60 MHz-binning data cube |
| CO(4-3) density upper limit, logL' 9.3-9.8 | <2.4e-3 | +0.1/-0.1 (x1e-3) | Mpc^-3 | 4 | 9.3–9.8 / 768.5$^{+51.0}_{-39.9}$ / $<(2.4^{+0.1}_{-0.1}) \times 10^{-3}$ |
| [CII] density upper limit, L 9.2-9.7 | <7.3e-4 | +1.1/-1.1 (x1e-4) | Mpc^-3 | 4 | 9.2–9.7$^{c}$ / 2532$^{+444}_{-331}$ / $<(7.3^{+1.1}_{-1.1}) \times 10^{-4}$ |

## Qualitative findings

- No line emitters with peak S/N>5; one candidate at S/N 4.5 likely [CII] at z=5.95 if real  
  > "RXJ1347-emitter1 can be a \[CII\] 158 $\mu$m emitter at $z=$ 5.95 rather than a CO emitter at $z\sim$ 1, if it is a real line emitter." (Line emitter candidate)

## Claim tuples

- H: Single-tuning ALMA Band 6 data toward lensing clusters can constrain CO and [CII] luminosity functions at low luminosity | E: Blind search in dirty S/N cubes of four clusters with CLUMPFIND; lens-model volumes; Poisson upper limits | R: No S/N>5 detections; upper limits down to ~1e-3 Mpc^-3 dex^-1 | F: Wide single-tuning cluster observations give useful constraints, comparable to ASPECS time | **supported**
- H: Observed LFs agree with semi-analytical model predictions | E: Compare upper limits with models and ASPECS | R: Limits lie above model predictions but consistent | F: Consistent with models, though constraints not stringent | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Dirty cubes used because no strong emission above 6 sigma in them  
  > "because no strong emission above 6$\sigma$ is found in these cubes" (2.1 ALMA data)
- How they decided it was enough: _not stated_
- Limitation (authors): Volume errors may be underestimated because systematic differences between lens models are not included  
  > "Note that our estimated errors can be underestimated because we do not include systematic errors between different lens models." (4 CO and [CII] luminosity functions)
- Caveat (inferred, ours): Conservative S/N>5 criterion differs from other works finding detections in the same data
- Caveat (inferred, ours): Unpublished lens models for two clusters
- Caveat (inferred, ours): Completeness/purity not simulated by injection
- Caveat (inferred, ours): Dirty-beam sidelobes and non-Gaussian noise not assessed

## Reproducibility

- Data public (paper): All data sets public in ALMA archive  
  > "All data sets are public in the ALMA science archive." (2.1 ALMA data)
- Products in archive: _not stated_
- Missing: CASA version and CLEAN settings
- Missing: Lens models for RXJ1347 and Abell S0592
- Missing: Volume calculation details
- Data volume (inferred): ~100-300 GB raw for 3 projects
- Score (inferred): 3/5, Public data and a simple method, but imaging parameters and two lens models are not given.
- Rediscovery candidate: no, Unpublished lens models and unspecified imaging details prevent a full redo, and the main results are upper limits.

## Links

- Method: (cite: williams1994) (CLUMPFIND algorithm)
- Method: (cite: kawamata2016) (GLAFIC lens models and MCMC uncertainties)
- Companion: (cite: decarli2016) (ASPECS line search whose data were reanalysed)
- Companion: (cite: gonzaez2017) (Independent line search in MACS J0416 and Abell 2744)
- Related: ASPECS

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 43,
  "rate": 0.531
 },
 "evidence_ok": true
}
```
