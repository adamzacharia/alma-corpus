# First Spectral Analysis of a Solar Plasma Eruption Using ALMA

`2019ApJ...875..163R` | The Astrophysical Journal 2019 | first author: Rodger, Andrew S. | arXiv: 1902.01319 | DOI: 10.3847/1538-4357/aafdfb

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: sun
- Question: Can the logarithmic millimetre continuum gradient across ALMA Band 3 sub-bands be used to estimate optical thickness (and hence temperature/emission measure) of a solar plasmoid and an X-ray bright point enhancement?  
  > "The aim of this study is to demonstrate how the logarithmic millimeter continuum gradient observed using the Atacama Large Millimeter/submillimeter Array (ALMA) may be used to estimate optical thickness in the solar atmosphere." (abstract)
- Target **Active region NOAA12470 region: XBP-coincident enhancement (box 1) and plasmoid ejection (box 2)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00020.SV
- bands: Band 3 (84–116 GHz), four spectral windows  
  > "The observation was conducted using ALMA Band 3 which has a central frequency of 100 GHz in the bandwidth of 84 – 116 GHz." (3 Observation)
- frequencies and spectral setup: spw0 93, spw1 95, spw2 105, spw3 107 GHz  
  > "four constituent spectral windows of Band 3; 93, 95, 105 and 107 GHz" (3.1 Noise level calculation)
- continuum bandwidth: _not stated_
- arrays: 22x12 m and 9x7 m antennae  
  > "This observation was conducted with a reduced interferometer setup of 22x12 m and 9x7 m antennae" (3 Observation)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: elliptical beam, 6.2'' x 2.3''  
  > "The observing beam for this observation was elliptical with a semi-major axis of 6.2$''$ and semi-minor axis of 2.3$''$" (3 Observation)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 17 December 2015  
  > "On the 17th of December 2015 ALMA observed a region near the large leading sunspot of active region NOAA12470" (3 Observation)
- pi or archival as stated: Publicly released science verification data  
  > "This dataset, along with other SV data sets, has been publicly released by the joint ALMA observatory" (3 Observation)
- Other facility **SDO/AIA**: 304 Å context image  
  > "An SDO/AIA 304 Å image shows the context for the observation in Figure [2]" (3 Observation)
- External data: Free-free Gaunt factor tables  
  > "free-free Gaunt factor interpolated from the table of numerically calculated values given by (cite: 2014MNRAS.444..420V)" (2.1 Isothermal plasma) [from van Hoof et al. 2014 (cite: 2014MNRAS.444..420V)]
- External data: Quiet-Sun model C7 atmosphere for background spectrum gradient  
  > "we have adopted the quiet-Sun model C7 from (cite: 2008ApJS..175..229A) to give an example continuum spectrum for Band 3" (4.1) [from Avrett & Loeser 2008 (cite: 2008ApJS..175..229A)]
- External data: Typical Band 3 quiet Sun background brightness temperature 7300±100 K  
  > "typical value of $\approx7300\pm100$ K (cite: 2017SoPh..292...88W)" (4.1) [from White et al. 2017 (cite: 2017SoPh..292...88W)]
- External data: Flux scale accuracy of 5% for Band 3  
  > "This accuracy limit is said to increase with frequency and is quoted for ALMA Band 3 to be 5%." (3.2 Flux scale accuracy) [from ALMA Cycle 6 Technical Handbook (cite: ALMA_handbook)]

## Processing

### Calibration

- pipeline or manual: Reference scripts provided with SV data; no self-calibration  
  > "We used the scripts provided with the test data[^2] to calibrate the data" (3 Observation); "we have only used the calibration methods presented in the reference scripts for the SV data which does not contain further corrections such as self-calibration." (3.1 Noise level calculation)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 5% (3σ), Gaussian  
  > "we have assumed a normally-distributed random uncertainty where the mean is zero and $3\sigma$ is equal to the 5% limit." (3.2 Flux scale accuracy)
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
- smoothing: Interferometric only, not feathered with total power  
  > "in agreement with (cite: 2017ApJ...841L...5S) we have decided to focus on interferometric results solely." (3 Observation)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Box definitions and replication of plasmoid analysis  
  > "following (cite: 2017ApJ...841L...5S), we define two boxes within the field of view" (3 Observation) [from Shimojo et al. 2017a (cite: 2017ApJ...841L...5S)]
- Noise estimation from XX minus YY difference  
  > "calculating the difference image between XX and YY cross-correlations of the two orthogonal linear polarisation measurements, X and Y (cite: 2017SoPh..292...87S)" (3.1 Noise level calculation) [from Shimojo et al. 2017b (cite: 2017SoPh..292...87S)]
- Optical thickness vs logarithmic spectral gradient relation and alpha bounds  
  > "the minimum and maximum values for $\alpha$ are 1.04 and 1.09, respectively (cite: Rodger&Labrosse2018)." (4.1) [from Rodger & Labrosse 2018 (cite: Rodger&Labrosse2018)]

### Not stated but needed to reproduce (our reading)

- Exact box 1 and box 2 pixel/coordinate extents
- Exact time ranges of background and enhanced phases
- Synthesis (tclean) parameters: weighting, cell, imaging software and CASA version
- MCMC burn-in and exact prior widths
- Exact SV scan/execution block used

## Analysis recipe

1. **Calibrate and image**: Calibrate with SV reference scripts; synthesise images at 2 s cadence for full band and each of four spectral windows  
  > "synthesise each image using the full bandwidth of Band 3 at a cadence of 2 s" (3 Observation)
   - fitting: _not stated_
   - validation: Replicated Shimojo et al. noise level of 11 K  
  > "We replicate the 11 K noise level value presented by (cite: 2017ApJ...841L...5S)" (3.1 Noise level calculation)
2. **Brightness temperature enhancement and errors**: Mean Tb in two boxes per time step; enhancement = enhanced minus background phase (N=29 steps each); noise from XX-YY, plus 5% flux-scale error  
  > "As the number of timesteps in both the background and enhanced phases were kept equal at $N=29$" (3.1 Noise level calculation)
   - assumption: Flux scale error normal with 3σ = 5%  
  > "we have assumed a normally-distributed random uncertainty where the mean is zero and $3\sigma$ is equal to the 5% limit." (3.2 Flux scale accuracy)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit spectral gradient**: Bayesian linear regression of log E vs log nu with emcee  
  > "we sampled it using a python implementation of the affine-invariant ensemble sampler for Markov-chain Monte-Carlo (MCMC) method (EMCEE)" (4.1)
   - software: emcee
   - parameter: 100 chains, 1000 steps including tuning  
  > "We sampled using 100 chains, each with 1000 steps including tuning." (4.1)
   - fitting: Normal likelihood in log space; uniform non-informative priors on gradient and intercept; 90% percentile intervals  
  > "The prior distributions for the two desired fitting parameters, i.e spectral gradient and y-intercept, have been set as non-informative uniform distributions." (4.1)
   - validation: _not stated_
4. **Derive optical thickness and plasma parameters**: Intersect gradient confidence interval with diagnostic curve using alpha (1.04–1.09) and beta bounds; then derive T, EM, density  
  > "Through plotting this curve and the confidence intervals of the fitted enhancement gradient it is possible to estimate the optical thickness/optical thickness regime" (4.1)
   - assumption: Isothermal plasma; C7 model background; purely hydrogen plasma; background Tb 7300±100 K  
  > "We assume a purely hydrogen plasma and a solely thermal bremsstrahlung emission mechanism." (4.1)
   - fitting: _not stated_
   - validation: Single-dish images checked to support the assumed background value  
  > "This assumption was checked by viewing the ALMA single-dish images during the observation" (4.1)

## Software

- **emcee** : MCMC sampling of linear fit  
  > "python implementation of the affine-invariant ensemble sampler for Markov-chain Monte-Carlo (MCMC) method (EMCEE)" (4.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Optical thickness, box 1 (90%) | 0.02–2.78 | 90% confidence | dimensionless | 4 | 0.02 $\leq \tau_{90\%\,\mathrm{confidence}} \leq$ 2.78 |
| Optical thickness, box 2 (90%) | 0.11–2.78 | 90% confidence | dimensionless | 4 | the optical thickness of the plasmoid ranges from 0.11 – 2.78 |
| Spectral gradient box 1 | -1.6 to -0.4 | 90% interval | dimensionless | 3 | the spectral gradient ranges between -1.6 and -0.4 |
| Electron temperature box 1 | 7370–15300 | not stated | K | 4 | between $\approx$ 7370 – 15300 K |
| Electron temperature box 2 | 7440–9660 | not stated | K | 4 | electron temperature of the plasmoid of $\sim$7440 – 9660 K |
| Full-band enhancement box 2 | 221 | 9.4 | K | 2 | / Full Band – 100 GHz / 159 $\pm$ 6.8 / 221 $\pm$ 9.4 / |
| Plasmoid electron density | 0.7–3e10 | not stated | cm^-3 | 4 | the electron density of the plasma would be in the range $\approx$ 0.7 – 3$\times 10^{10} \,\mathrm{cm^{-3}}$ |

## Qualitative findings

- Both enhancements lie in the transition between optically thin and thick plasma; plasmoid results favour cool optically thick core model of Shimojo et al.  
  > "where both lie entirely in the transition region between optically thin and optically thick plasma." (Conclusions)

## Claim tuples

- H: Sub-band ALMA spectra can constrain optical thickness of solar features | E: Fit log enhancement spectrum across four Band 3 spws and compare with diagnostic curve | R: tau 0.02–2.78 (box 1), 0.11–2.78 (box 2) | F: Sub-band analysis is a useful diagnostic | **supported**
- H: Is the plasmoid optically thin hot or cool optically thick? | E: Derive tau and temperature and compare with Shimojo et al. | R: tau near transition; T 7440–9660 K | F: Supports cool optically thick core case | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Flux scale accuracy is the largest uncertainty; background gradient uncertainty not included; isothermal assumption  
  > "The largest source of uncertainty in the data is due to the accuracy of the flux scale determination." (5 Discussion)
- Caveat (inferred, ours): Only four closely spaced sub-bands for a linear fit
- Caveat (inferred, ours): Background gradient from model C7 not observed
- Caveat (inferred, ours): No self-calibration; enhancement differs from published 145 K

## Reproducibility

- Data public (paper): Public SV data with reference scripts  
  > "This dataset, along with other SV data sets, has been publicly released by the joint ALMA observatory" (3 Observation)
- Products in archive: _not stated_
- Missing: Box coordinates and phase time ranges
- Missing: Imaging parameters
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, Public data and clear statistical method, but box definitions and imaging parameters missing.
- Rediscovery candidate: yes, Public SV data, numeric results, mostly complete recipe.

## Links

- Method: Rodger & Labrosse 2018 (cite: Rodger&Labrosse2018) (Diagnostic relation between spectral gradient and optical thickness)
- Method: Shimojo et al. 2017b (cite: 2017SoPh..292...87S) (SV calibration and noise estimation)
- Companion: Shimojo et al. 2017a (cite: 2017ApJ...841L...5S) (Earlier analysis of the same plasmoid event)
- Related: ALMA solar science verification

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00020.SV"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 32,
  "rate": 0.464
 },
 "evidence_ok": true
}
```
