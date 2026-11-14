# First M87 Event Horizon Telescope Results. VI. The Shadow and Mass of the Central Black Hole

`2019ApJ...875L...6E` | The Astrophysical Journal Letters 2019 | first author: Event Horizon Telescope Collaboration | arXiv: 1906.11243 | DOI: 10.3847/2041-8213/ab1141

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars
- Question: What are the size, structure and mass implied by the horizon-scale 1.3 mm emission of M87's central black hole, from geometric crescent fits, GRMHD fits and image-domain features of EHT 2017 data?  
  > "We present measurements of the properties of the central radio source in M87 using Event Horizon Telescope data obtained during the 2017 campaign." (abstract)
- Target **M87**: coordinates _not stated_; z/distance D = 16.8 (+0.8/-0.7) Mpc  
  > "we adopt a distance of _D_ = 16.8 -+ 0.70.8 Mpc to M87." (8. Prior Mass and Distance Estimates); distance from Combined TRGB (Bird et al. 2010) and two SBF measurements (Blakeslee et al. 2009; Cantiello et al. 2018a)  
  > "We combine one TRGB measurement (Bird et al. 2010) with two SBF measurements (Blakeslee et al. 2009; Cantiello et al. 2018a) to arrive at a combined distance measurement." (8. Prior Mass and Distance Estimates)

## Data provenance

- ALMA projects: _none stated_
- bands: two 2 GHz bands centered on 227.1 GHz (LO) and 229.1 GHz (HI), 1.3 mm  
  > "the EHT observed M87 in two 2 GHz frequency bands centered on 227.1 GHz (low-band; LO) and 229.1 GHz (high-band; HI)" (2. Observations and Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: April 5, 6, 10, 11 2017  
  > "The EHT observed M87 on four days (April 5, 6, 10, and 11) at 1.3 mm" (1. Introduction)
- pi or archival as stated: _not stated_
- Other facility **EHT (VLBI array incl. ALMA, APEX, JCMT, SMA, LMT, SMT)**: 2017 1.3 mm VLBI visibilities, HOPS-reduced  
  > "We use Stokes I visibility data reduced via the EHT-Haystack Observatory Processing System (HOPS) pipeline (Blackburn et al. 2019), coherently averaged in time by scan." (2. Observations and Data)
- External data: Distance to M87, 16.8 Mpc, from TRGB and SBF measurements  
  > "We combine one TRGB measurement (Bird et al. 2010) with two SBF measurements (Blakeslee et al. 2009; Cantiello et al. 2018a) to arrive at a combined distance measurement." (8.1 Distance) [from Bird et al. 2010; Blakeslee et al. 2009; Cantiello et al. 2018a]
- External data: Stellar and gas dynamical black hole masses  
  > "we focus on the two latest dynamical measurements of the kinematic properties of surrounding stars and gas (Gebhardt et al. 2011; Walsh et al. 2013)" (8.2 Mass-to-distance Ratio) [from Gebhardt et al. 2011; Walsh et al. 2013]
- Simulation/model as data: GRMHD image library from Paper V, used for calibration and direct fitting  
  > "we have constructed a large image library of horizon-scale synchrotron emission images at 230 GHz computed from GRMHD simulations." (6.1 Summary of Simulations)

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

- Correlation, calibration and validation of EHT 2017 data  
  > "The 2017 EHT observations of M87 and their subsequent correlation, calibration, and validation are described in detail in Paper III." (2. Observations and Data) [from EHT Collaboration et al. 2019b (Paper III)]
- Image reconstructions (eht-imaging, SMILI, DIFMAP) and synthetic data generation  
  > "A detailed description of the synthetic data generation pipeline is provided in Paper IV." (Appendix D.1) [from EHT Collaboration et al. 2019c (Paper IV)]

### Not stated but needed to reproduce (our reading)

- Exact random seeds and sampler settings (live points, chain lengths) for THEMIS runs; details deferred to Broderick et al. 2019 in preparation
- The specific 100 GRMHD snapshots chosen for calibration

## Analysis recipe

1. **Prepare closure quantities**: Scan-average visibilities, add 1% systematic error, construct non-redundant closure phases and log closure amplitudes  
  > "by adding a 1% systematic uncertainty component in quadrature to the thermal noise" (2.2 Data Selection and Preparation)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit geometric crescent models**: Fit xs-ring (dynesty, closure quantities) and xs-ringauss (THEMIS, visibility amplitudes and closure phases) with nuisance Gaussians  
  > "Throughout this Letter we fit the xs‐ring model using the dynesty sampling code, while the xs‐ringauss model is implemented as part of THEMIS ." (5.1 Generalized Crescent Models)
   - software: THEMIS, dynesty
   - parameter: dynesty runs until less than 1% of the evidence is unaccounted for  
  > "We permit dynesty to run until it estimates that less than 1% of the evidence is left unaccounted for." (4.2.2 dynesty)
   - fitting: Gaussian likelihoods; differential evolution MCMC with parallel tempering (THEMIS); nested sampling (dynesty); priors in Table 8  
  > "THEMIS implements a differential evolution MCMC algorithm, and it utilizes parallel tempering" (4.2.1 THEMIS)
   - validation: Reduced chi-square values; comparison between the two codes  
  > "In general we find joint reduced-χ [2] values for the fits of ∼0.9–1.5." (5.2 M87 Fit Results)
3. **Calibrate crescent diameter to gravitational radius**: Fit GC models to synthetic data from 103 GRMHD snapshots to derive scaling factor alpha (d = alpha theta_g) and uncertainties via generalized lambda distributions  
  > "From the GRMHD simulation library we selected 103 separate snapshot images with which to generate synthetic data sets." (Appendix D.1)
   - software: eht-imaging, GLDEX
   - assumption: GRMHD library provides ground-truth images  
  > "we take the GRMHD simulation library described in Paper V to provide our “ground truth” images." (Appendix D)
   - fitting: _not stated_
   - validation: Part I synthetic data tests observational uncertainty; Part II tests theoretical scatter  
  > "The goal of the Part I data sets is to assess the impact of such observational corruptions on the recovered model parameters" (Appendix D)
4. **Direct GRMHD snapshot fitting**: Fit single snapshot models (flux, scale, rotation) with THEMIS and GENA; select models with average image scoring; marginalize over acceptable models  
  > "The full posteriors are then obtained by marginalizing over all GRMHD models that are found to be acceptable via the THEMIS AIS procedure." (6.5. Ensemble-based Parameter Estimation)
   - software: THEMIS, GENA
   - fitting: Uniform priors on CF, theta_g, PA  
  > "We adopt a uniform prior on the total compact flux density between 0.1 and 10 Jy for THEMIS and between 0.1 Jy and 4 Jy for GENA" (6.3. Fitting Single Snapshots to EHT Data)
   - validation: Mock analyses showed no significant biases  
  > "no significant biases were found" (6.5 Ensemble-based Parameter Estimation)
5. **Image-domain feature extraction and mass**: Measure ring diameter in reconstructed images, calibrate with alpha, convert theta_g to mass with distance  
  > "After applying the calibrated scaling factor to the image domain diameter measurements, we find consistent results across all observing days and reconstruction methods" (7.3. From Image Diameter to Angular Gravitational Radius)
   - software: eht-imaging, SMILI, DIFMAP
   - assumption: D = 16.8 Mpc  
  > "we adopt a distance of _D_ = 16.8 -+ 0.70.8 Mpc to M87." (8.1 Distance)
   - fitting: _not stated_
   - validation: Variants A, B, C of the method give differences smaller than the pixel size  
  > "The typical differences between the parameters measured with the three variants are smaller than the pixel size." (Figure 30 caption)

## Software

- **THEMIS** : MCMC fitting of geometric and GRMHD models  
  > "THEMIS is written in C++ and parallelized via the Message Passing Interface (MPI) standard." (4.2.1 THEMIS)
- **dynesty** : nested sampling of xs-ring model  
  > "We use the Python code dynesty (Speagle & Barbary 2018) as a sampler for the NS analyses presented in this Letter." (4.2.2 dynesty)
- **GENA** : genetic algorithm fit of GRMHD snapshots  
  > "GENA (Fromm et al. 2019), is a genetic algorithm written in Python and parallelized using MPI." (4.2.3 GENA)
- **eht-imaging** v1.1.0: synthetic data and RML imaging  
  > "generating synthetic observational data with ehtimaging" (Appendix D.1)
- **GLDEX** : generalized lambda distribution fits to uncertainty components  
  > "The fits were performed using the GLDEX package in R (Su 2007a, 2007b)." (Appendix D.3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| crescent diameter | 42 | ±3 | μas | 2 | The average diameter of the crescent is well constrained by multiple methods with a combined range of 42 ± 3 μas. |
| GC model calibration factor alpha (xs-ring / xs-ringauss) | 11.55 / 11.50 | not stated | dimensionless | 3 | For the xs‐ring model we find a mean value of _a_ = 11.55, while for the xs‐ringauss model we find a nearly identical _a_ = 11.50 |

## Qualitative findings

- Crescent models strongly preferred; central brightness depression of factor >10; asymmetry brightest in the south  
  > "a persistent asymmetry with the brightest region to the South (PA of 150°–200°)." (9.1 Lensed Emission Around the Black Hole Shadow)

## Claim tuples

- H: Is the M87 image a lensed ring around a black hole shadow? | E: Fit geometric and GRMHD models and extract image features | R: Crescent diameter 42±3 μas, fractional width <0.5, contrast >10 | F: Consistent with lensed emission around the shadow | **supported**
- H: What is the black hole mass? | E: Calibrate size with GRMHD, combine with distance | R: M = 6.5±0.2±0.7 ×10^9 Msun | F: Consistent with stellar but not gas dynamics | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Disks, rings and double Gaussians fit worse than crescents  
  > "We find that the data overwhelmingly prefer crescent models over, e.g., symmetric disk and ring models" (5. Geometric Modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): Results rely on GRMHD simulations and a small subset of the library  
  > "The measurements rely on images generated from GRMHD simulations and should be understood within that" (9.2 The Black Hole Mass)
- Caveat (inferred, ours): Systematic uncertainty dominated by GRMHD calibration choice
- Caveat (inferred, ours): ALMA is only one station of a VLBI array; no ALMA-only analysis

## Reproducibility

- Data public (paper): Data and software available on EHT data portal  
  > "software used for analysis can be found on the Event Horizon Telescope website’s data portal." (2.2. Data Selection and Preparation)
- Products in archive: _not stated_
- Missing: Full THEMIS validation details (in preparation paper)
- Missing: Paper IV/V products
- Data volume (inferred): Small (scan-averaged visibilities), but GRMHD library is large
- Score (inferred): 3/5, Public data and detailed modeling, but depends on companion papers and heavy computation.
- Rediscovery candidate: no, Requires GRMHD library and unpublished THEMIS details; ALMA is minor.

## Links

- Method: EHT Collaboration et al. 2019b (Paper III) (data calibration)
- Method: EHT Collaboration et al. 2019c (Paper IV) (imaging)
- Companion: EHT Collaboration et al. 2019d (Paper V) (GRMHD library)
- Related: Event Horizon Telescope 2017 campaign

## Checks

```json
{
 "quotes": 40,
 "quotes_ok": 40,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2016.1.01154.V"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 34,
  "rate": 0.453
 },
 "evidence_ok": true
}
```
