# High-resolution observations of the outer disk around T Chamaeleontis: the view from ALMA

`2015A&A...575L...5H` | Astronomy and Astrophysics 2015 | first author: Huélamo, N. | arXiv: 1501.06483 | DOI: 10.1051/0004-6361/201424404

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the size, geometry, kinematics and gas/dust structure of the outer disk around the transitional-disk star T Cha?  
  > "The aim of this work is to study the outer disk around T Cha and to derive its main properties." (abstract)
- Target **T Cha**: coordinates RA(J2000) 11h57m13.42s, Dec -79d21m31.696s (continuum centre)  
  > "is a young ($\sim$7$\pm$5 Myr) nearby (108 pc) T Tauri star in the $\epsilon$-Cha association" (Introduction); "R.A.(J2000) = 11$^{h}$57$^{m}$13$s$42, Dec(J2000) =$-$79$\ensuremath{^\circ}$21$\ensuremath{'}$31$\ensuremath{''}$696" (3.2 Continuum emission at 850 um); z/distance 108 pc  
  > "is a young ($\sim$7$\pm$5 Myr) nearby (108 pc) T Tauri star in the $\epsilon$-Cha association" (Introduction); "R.A.(J2000) = 11$^{h}$57$^{m}$13$s$42, Dec(J2000) =$-$79$\ensuremath{^\circ}$21$\ensuremath{'}$31$\ensuremath{''}$696" (3.2 Continuum emission at 850 um); distance from Torres2008; Schisano2009  
  > "is a young ($\sim$7$\pm$5 Myr) nearby (108 pc) T Tauri star in the $\epsilon$-Cha association" (Introduction); "R.A.(J2000) = 11$^{h}$57$^{m}$13$s$42, Dec(J2000) =$-$79$\ensuremath{^\circ}$21$\ensuremath{'}$31$\ensuremath{''}$696" (3.2 Continuum emission at 850 um)

## Data provenance

- ALMA projects: 2011.0.00921.S
- bands: Band 7  
  > "The observations were performed on 2012 July 01, 26 and November 03 at Band 7" (2 Observations)
- frequencies and spectral setup: 4 spectral windows at 345.796 (CO 3-2), 342.883 (CS 7-6), 332.505 (SO2), 330.588 GHz (13CO 3-2); 468.75 MHz effective bandwidth; ~0.11 km/s after Hanning smoothing  
  > "The effective bandwidth used was $468.75{\rm MHz}$, providing a velocity resolution of $\sim$ 0.11 km s$^{-1}$ after Hanning smoothing." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 18-23 12 m antennas  
  > "using between 18 and 23 antennas of $12\,{\rm m}$ diameter" (2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: continuum 0.52" x 0.34"; CO 0.64" x 0.48"  
  > "synthesized beam $0.52\ensuremath{''} \times 0.34\ensuremath{''}$, ${\rm P.A.}\!\sim\!\!29^\circ$; rms = 0.7 mJy beam$^{-1}$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.7 mJy/beam; CO 9, 13CO 11, CS/SO2 7 mJy/beam per channel  
  > "an rms per channel of 11 mJy beam$^{-1}$ for the ${\rm ^{13}CO}$ and 7 mJy beam$^{-1}$ for the ${\rm CS}$ and the ${\rm SO_{2}}$" (2 Observations)
- time on source: 6 hours total including overheads and calibration  
  > "accounting for 6 hours of total integration time including overheads and calibration" (2 Observations)
- observing dates: 2012 July 01, 26 and November 03  
  > "The observations were performed on 2012 July 01, 26 and November 03 at Band 7" (2 Observations)
- pi or archival as stated: _not stated_
- Line: CO 3-2 (345.796 GHz)
- Line: CS 7-6 (342.883 GHz)
- Line: 13CO 3-2 (330.588 GHz)
- Line: SO2 4(3,1)-3(2,2) (332.505 GHz)
- External data: SED dataset and MCFOST model grid/parameter ranges  
  > "For the SED, we have fitted the same observational dataset displayed in that work." (4 Comparison with radiative transfer models) [from Cieza2011]
- External data: Inner disk parameters  
  > "We have adopted the inner disk parameters from (cite: Olofsson2013)." (4 Comparison with radiative transfer models) [from Olofsson2013]
- External data: Dust mass 9e-5 Msun for tapered-edge model  
  > "the dust mass to $M_{\rm dust}$= 9$\times$ 10$^{-5}$ M$_{\odot}$ (de Gregorio-Monsalvo et al., in prep.)" (4 Comparison with radiative transfer models) [from de Gregorio-Monsalvo et al., in prep.]
- External data: Stellar parameters Teff=5400 K, Av=1.5, d=108 pc  
  > "The adopted stellar parameters are $T_{\rm eff}$=5400 K, $A_{\rm v}$=1.5, and $d$=108 pc (cite: Torres2008; Schisano2009)." (4 Comparison with radiative transfer models) [from Torres2008; Schisano2009]

## Processing

### Calibration

- pipeline or manual: CASA reduction with WVR phase correction; self-calibration on continuum  
  > "We applied self-calibration using the continuum and we used the task CLEAN for imaging the self-calibrated visibilities." (2 Observations)
- casa version: CASA 4.1  
  > "Data reduction was performed using version 4.1 of the Common Astronomy Software Applications package (CASA)." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Juno and Titan; bandpass J1256-057; gain J1147-6753  
  > "Amplitude calibration was done using Juno and Titan, and quasars J$1256$$-057$ and J$1147$$-6753$ were used to calibrate the bandpass and the complex gain fluctuations respectively." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: applied using the continuum  
  > "We applied self-calibration using the continuum" (2 Observations)

### Imaging

- task: CLEAN  
  > "we used the task CLEAN for imaging the self-calibrated visibilities" (2 Observations)
- deconvolver: _not stated_
- weighting robust: Continuum uniform; CO Briggs (robust not stated); other lines natural  
  > "For the ${\rm CO}(3$–$2)$ line we used Briggs weighting" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum from combining all line-free channels  
  > "The continuum image was produced by combining all of the line-free channels using uniform weighting" (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: continuum 0.7 mJy/beam  
  > "rms = 0.7 mJy beam$^{-1}$" (2 Observations)

### Inherited from earlier work

- MCFOST model parameter ranges and SED data  
  > "using the same parameter range shown in (cite: Cieza2011)" (4 Comparison with radiative transfer models) [from Cieza2011]
- Tapered-edge prescription to reconcile gas and dust extents  
  > "a tapered edge model, in which the surface density falls off gradually, can in principle reconcile the observed profiles." (4 Comparison with radiative transfer models) [from Hughes2008]

### Not stated but needed to reproduce (our reading)

- Briggs robust value, cell size, image size, clean masks and iterations
- Self-calibration solution intervals and number of rounds
- Line-free channel selection for continuum
- Method details of Gaussian fits for i and PA and the deconvolution of radii
- How dynamical mass 1.5±0.2 was derived from the PV diagram
- Full MCFOST grid steps, inner disk values, and Bayesian priors
- Flux calibrator flux scale adopted

## Analysis recipe

1. **Image continuum and lines**: CLEAN on self-calibrated visibilities; continuum from line-free channels  
  > "The continuum image was produced by combining all of the line-free channels using uniform weighting" (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure disk size, flux, inclination and PA**: Moment maps above 3σ; radius deconvolved with beam; Gaussian fit to CO integrated map for i and PA  
  > "have been estimated by fitting a Gaussian to the ${\rm CO}(3$–$2)$ integrated emission map" (3.1 Molecular emission line detections)
   - assumption: distance 108 pc  
  > "adopting a distance of $108\,{\rm pc}$" (3.2 Continuum emission at 850 um)
   - fitting: Gaussian fit  
  > "have been estimated by fitting a Gaussian to the ${\rm CO}(3$–$2)$ integrated emission map, providing values of $i = 67\pm5\degree$ and $PA=113\pm6\degree$." (Results and discussion, Molecular emission line detections)
   - validation: _not stated_
3. **Estimate dynamical mass**: Compare CO position-velocity diagram along major axis with Keplerian profile at i=67 deg  
  > "the emission is compatible with Keplerian rotation around a 1.3 - 1.7 M$_{\odot}$ object in a disk inclined at 67 degrees" (3.1 Molecular emission line detections)
   - fitting: _not stated_
   - validation: Compared with evolutionary-track masses for ~10 Myr  
  > "This mass range is in good agreement with estimations from evolutionary tracks for an age of $\sim$10 Myr" (3.1 Molecular emission line detections)
4. **Power-law SED+ALMA MCFOST modelling**: MCFOST grid with R_out and i fixed from ALMA (80 AU, 68), explore Rin, beta, h0, amax, alpha, Mdust; minimum chi2; Bayesian analysis  
  > "we have fixed two parameters obtained from the ALMA data, $R_{\rm out}$ and $i$" (4 Comparison with radiative transfer models)
   - software: MCFOST
   - assumption: gas-to-dust 100; CO abundance 1e-4 where Tdust>20 K; 12CO/13CO=76; Tgas=Tdust  
  > "we assume a constant gas-to-dust mass ratio of 100 throughout the disk" (4 Comparison with radiative transfer models)
   - fitting: chi2 minimisation and Bayesian probability distributions  
  > "we have performed a Bayesian analysis to estimate the validity range for each of the explored parameters" (4 Comparison with radiative transfer models)
   - validation: Model fails to fit gas and dust simultaneously  
  > "the model fails to fit simultaneously the gas and dust profiles" (4 Comparison with radiative transfer models)
5. **Tapered-edge model**: MCFOST with exponential taper; i=68, Mdust=9e-5 fixed; explore gamma 0-2, Rc 40-100 AU, Rin 12-30 AU, h0 3-6 AU, beta 1.0-1.1  
  > "we have sampled a range of $\gamma$ values between 0 and 2, $R_{\rm c}$ between 40 and 100 AU" (4 Comparison with radiative transfer models)
   - software: MCFOST
   - fitting: _not stated_
   - validation: Compared to radial profiles and SED; CO profiles not perfectly fit  
  > "our best model does not perfectly fit the CO line profiles" (4 Comparison with radiative transfer models)

## Software

- **CASA** 4.1: Data reduction and CLEAN imaging  
  > "Data reduction was performed using version 4.1 of the Common Astronomy Software Applications package (CASA)." (2 Observations)
- **MCFOST** : Radiative transfer modelling of SED, images and line emission  
  > "We have modeled the SED of T Cha with MCFOST" (4 Comparison with radiative transfer models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(3-2) outer radius | 230 | not stated | AU | 2 | corresponds to an outer radius $R_{\rm CO}\!\sim230\,{\rm AU}$ |
| CO(3-2) integrated intensity | 12.46 | 0.11 | Jy km/s | 2 | $12.46$ $\pm$ $0.11$ Jy km s$^{-1}$ |
| Inclination | 67 | 5 | deg | 2 | $i = 67\pm5\degree$ and $PA=113\pm6\degree$ |
| Position angle | 113 | 6 | deg | 2 | $i = 67\pm5\degree$ and $PA=113\pm6\degree$ |
| 13CO radius | 170 | not stated | AU | 2 | $R_{\rm ^{13}CO}\!\sim170\,{\rm AU}$ |
| CS radius | 100 | not stated | AU | 2 | $R_{\rm CS}\!\sim100 {\rm AU}$ |
| Continuum flux density 850 um | 198 | 4 | mJy | 2 | $S_{850\mu m}$ = 198 $\pm$ 4 mJy |
| Dust disk outer radius | 80 | not stated | AU | 2 | $R_{\rm out}\!\sim80\,{\rm AU}$ |
| Systemic velocity | 5.95 | 0.22 | km/s | 3 | The systemic velocity is 5.95$\pm$0.22 km s$^{-1}$. |
| Dynamical stellar mass | 1.5 | 0.2 | Msun | 3 | $M_{*}$ = 1.5$\pm$0.2 M$_{\odot}$ |
| Tapered-edge best model gamma, Rc | gamma=0.5, Rc=50 AU | not stated | dimensionless, AU | 5 | The model shows $\gamma$ = 0.5 and $R_{\rm c}$ = 50 AU for both the gas and the dust. |

## Qualitative findings

- Dust disk is compact (~80 AU) with two emission bumps suggesting a gap, and asymmetric between sides; gas disk is ~3 times larger  
  > "The target is surrounded by a compact dusty disk and a $\sim$3 times larger gaseous disk." (4 Conclusions)

## Claim tuples

- H: Is the outer disk of T Cha resolved, with a compact dust disk and a larger gas disk? | E: ALMA Band 7 continuum and CO, 13CO, CS imaging | R: Dust R~80 AU, CO R~230 AU, two continuum peaks 40 AU apart | F: Compact dust disk and larger gas disk with likely inner gap | **supported**
- H: Can a power-law surface density model explain both gas and dust? | E: MCFOST models with power-law and tapered-edge profiles | R: Only tapered-edge fits both | F: Tapered-edge needed; most disk mass within 50 AU | **supported**
- H: What is the central mass? | E: Keplerian fit to the CO PV diagram | R: 1.5±0.2 Msun | F: Consistent with evolutionary tracks at ~10 Myr | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Power-law surface density models fail to reproduce CO and continuum together  
  > "models with a power-law surface density, like the ones used in these two works, cannot reproduce both the CO and continuum data" (4 Comparison with radiative transfer models)
- How they decided it was enough: _not stated_
- Limitation (authors): Disk barely resolved; best model does not perfectly fit CO profiles  
  > "Given that the disk is barely resolved in our observations" (4 Comparison with radiative transfer models)
- Caveat (inferred, ours): Gaussian-based i/PA and dynamical mass lack described fitting method and error derivation
- Caveat (inferred, ours): Tapered model fit is by eye/grid without stated statistic
- Caveat (inferred, ours): Gap inference rests on peaks separated by about one beam

## Reproducibility

- Data public (paper): Cycle 0 project code given; acknowledges use of ALMA data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00921.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters (robust, cell, mask)
- Missing: Self-cal parameters
- Missing: MCFOST grid and inner-disk parameters
- Missing: Dust mass from in-prep paper
- Data volume (inferred): ~20-50 GB raw for three Cycle 0 execution blocks
- Score (inferred): 3/5, Public Cycle 0 data and clear targets, but imaging and fitting details are sparse (short letter).
- Rediscovery candidate: no, Imaging and model-fitting details too incomplete, though measurements are numeric.

## Links

- Method: Pinte2006; pinte2009 (MCFOST code)
- Method: Cieza2011 (SED model grid)
- Companion: Olofsson2013 (Inner disk parameters)
- Companion: Sacco2014 (Single-dish CO observations)

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
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 43,
  "rate": 0.606
 },
 "evidence_ok": true
}
```
