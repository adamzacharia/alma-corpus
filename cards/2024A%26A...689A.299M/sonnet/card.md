# Prospects of directly using closure traces for imaging in very long baseline interferometry

`2024A&A...689A.299M` | Astronomy and Astrophysics 2024 | first author: Müller, Hendrik | arXiv: 2407.20190 | DOI: 10.1051/0004-6361/202450437

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars, instrumentation
- Question: Can closure traces (gain- and leakage-independent polarimetric closure quantities) be fitted directly to create polarimetric images in VLBI (EHT, ngEHT) and in a denser array such as ALMA?  
  > "Here we explore, how closure traces could be directly fitted to create an image and point out an imaging pipeline that succeeds in the direct imaging from closure traces." (abstract)
- Target **M87 (ALMA observation during EHT 2017 campaign)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01154.V
- bands: Band 6  
  > "The observations were performed in ALMA Band 6, with an array of 33 antennas covering baseline lengths between 15.1 meter and 160.7 meter." (Real Data Application)
- frequencies and spectral setup: four spectral windows studied by Albentosa2023 at 213.1, 215.1, 227.1, 229.1 GHz; this work uses 227.1 GHz  
  > "For this work, we reproduce the image at the third spectral window (227.1 GHz), matching the lower band of the EHT observations." (Real Data Application)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15.1 m to 160.7 m, 33 antennas  
  > "with an array of 33 antennas covering baseline lengths between 15.1 meter and 160.7 meter." (Real Data Application)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: April 6 (2017)  
  > "during the EHT campaign in 2017 (cite: eht2019a), at April 6." (Real Data Application)
- pi or archival as stated: _not stated_
- Other facility **EHT (2017 array, public M87 data of April 11 2017)**: Real calibrated M87 polarimetric data and uv-coverage/noise for synthetic observations  
  > "We apply our algorithms to the public calibrated M87 observations of the EHT at April 11th in 2017" (Real Data Application)
- Other facility **ngEHT analysis challenge**: EHT+ngEHT configuration synthetic data set for M87  
  > "with a proposed configuration of the ngEHT taken from the ngEHT Analysis challenge (cite: ngehtchallenge)." (Synthetic Data)
- External data: Reference model-fitting results of ALMA M87 polarization (the experiment reproduced)  
  > "we aim to reproduce the numerical experiment performed in (cite: Albentosa2023) which represents the pioneering work that directly fitted closure traces." (Real Data Application) [from Albentosa-Ruiz & Marti-Vidal 2023 (cite: Albentosa2023)]
- External data: EHT-estimated leakage terms used for calibrated-data comparison reconstruction  
  > "were corrected by the detailed and vetted estimates obtained by the EHT (cite: eht2021a)." (Real Data Application) [from (cite: eht2021a)]
- Simulation/model as data: Synthetic ground truths: geometric ring model (42 uas diameter, 0.6 Jy compact flux), GRMHD SgrA* model from ehtim, 3C279-inspired six-Gaussian double source  
  > "It consists of a ring with a diameter of $42\,\mu\mathrm{as}$, and a compact flux of $0.6\,\mathrm{Jy}$." (Synthetic Data)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline script on archive data  
  > "The data were downloaded from the ALMA archive and calibrated with the ALMA pipeline script." (Real Data Application)
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
- smoothing: time-averaged by 10 seconds after export to uvfits  
  > "We exported the measurement sets to the uvfits format and time-averaged the data by 10 seconds" (Real Data Application)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Closure trace definition and degeneracies  
  > "It can be shown now that $Tr_{i,j,k,l}$ is independent of $\mathbf{J}^{i},\mathbf{J}^{j},\mathbf{J}^{k},\mathbf{J}^{l}$, i.e. independent of gains and leakage terms (cite: Broderick2020b)." (Theory) [from (cite: Broderick2020b)]
- MOEA/D objective set for polarimetric imaging  
  > "The set-up of MOEA/D for the reconstruction with respect to closure traces consists of solving a multi-objective problem with the following objective functionals (cite: Mus2023b)" (Imaging Procedure) [from (cite: Mus2023b)]
- MO-PSO algorithm details  
  > "For more details, we refer to (cite: Mus2023c)." (Description of the imaging algorithms) [from (cite: Mus2023c)]

### Not stated but needed to reproduce (our reading)

- ALMA pipeline/CASA version
- Which of the archive execution blocks/scans of 2016.1.01154.V were used and flagging
- Number of pixels, field of view, and regularization/weight settings for the ALMA reconstruction
- MO-PSO swarm size, iterations, and EVPA alignment details for the real-data run
- Total intensity initial guess details for ALMA (pipeline image used)
- Quantitative metric comparing with Albentosa2023

## Analysis recipe

1. **Prepare ALMA data**: Download archive data, calibrate with ALMA pipeline, export to uvfits, time-average 10 s  
  > "The data were downloaded from the ALMA archive and calibrated with the ALMA pipeline script." (Real Data Application)
   - software: MrBeam
   - parameter: 10 s averaging; spectral window 227.1 GHz  
  > "time-averaged the data by 10 seconds" (Real Data Application)
   - assumption: Negligible circular polarization  
  > "We therefore restrict ourselves in this work to situations with negligibly small circular polarization at first instance." (Imaging Procedure)
   - fitting: _not stated_
   - validation: _not stated_
2. **Reconstruct polarization from closure traces**: MO-PSO multiobjective imaging fitting closure traces, with ALMA pipeline product as initial guess  
  > "The pipeline product of ALMA was used as an initial guess. The reconstruction of the polarized structure from the closure traces, was then performed with the MO-PSO algorithm" (Real Data Application)
   - software: MrBeam, ehtim, pygmo
   - fitting: Particle swarm over regularization weights; objectives chi2 of closure traces plus R_ms, R_hw, R_ptv  
  > "by screening the regularization weights with a particle-swarm optimization algorithm, and solving the related weighted sum problem by fast gradient based minimization techniques." (Description of the imaging algorithms)
   - validation: Qualitative comparison with Albentosa2023 model-fitting results  
  > "The Stokes I reconstruction, as well as the EVPA structure looks very similar to the reconstructions presented in (cite: Albentosa2023), presenting an interesting cross-verification." (Real Data Application)

## Software

- **MrBeam** : Reconstruction software for closure trace imaging  
  > "performed the reconstruction with the software tool MrBeam" (Real Data Application)
- **ehtim** : Synthetic observations and GRMHD model  
  > "The synthetic observations have been performed by the `ehtim` package." (Synthetic Data)
- **DoG-HiT** : Total intensity initial guess and comparison polarimetric imaging  
  > "we use DoG-HiT as an initial guess for the total intensity structure, and as a comparison, imaging algorithm." (Description of the imaging algorithms)
- **pygmo** : Package MrBeam uses (evolutionary algorithms)  
  > "MrBeam makes explicit use of the following packages: ehtim" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Runtime of ALMA MO-PSO reconstruction | roughly 30 minutes | not stated | minutes | 2 | The reconstruction was performed on a common notebook in roughly 30 minutes. |
| Leakage error level at which closure-trace imaging becomes competitive | roughly 2% | not stated | percent | 0 | The MOEA/D reconstruction becomes competitive for d-term inaccuracies of roughly $2\%$. |

## Qualitative findings

- Closure traces are not constraining enough for the 2017 EHT to image directly, but work for EHT+ngEHT and likely the 2021 EHT array.  
  > "Closure traces are not constraining enough for the current EHT configuration to recover an image directly, mainly due to the small number of antennas." (abstract)

## Claim tuples

- H: Can closure traces be used directly for polarimetric imaging with ALMA data? | E: MO-PSO reconstruction of ALMA M87 227.1 GHz data from closure traces | R: Stokes I and EVPA structure similar to Albentosa2023 | F: Closure trace imaging reproduces model-fitting results and scales to dense arrays | **supported**
- H: Is closure trace imaging feasible for EHT arrays? | E: Synthetic tests with EHT 2017, 2021 and EHT+ngEHT | R: 2017 EHT largely unsuccessful; EHT+ngEHT competitive with a few percent residual leakage | F: Feasible for denser future arrays | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Multiobjective evolution samples the multimodal landscape caused by closure trace degeneracies  
  > "leave local search techniques at risk at falling into local minima, opposed to multiobjective imaging algorithms which navigate the objective landscape globally." (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Assumes vanishing circular polarization; MO-PSO does not reproduce multimodality; primary-beam polarization not treated  
  > "As a remaining limitation, we rely on the assumption of vanishing circular polarization" (Conclusions)
- Caveat (inferred, ours): ALMA comparison with Albentosa2023 is purely qualitative
- Caveat (inferred, ours): No uncertainty quantification on reconstructions
- Caveat (inferred, ours): Synthetic data use simplistic noise/gain models

## Reproducibility

- Data public (paper): ALMA data accessible from archive; synthetic data on request  
  > "The data underlying this work are accessible from the ALMA data archive, synthetic data sets will be shared upon reasonable request." (Acknowledgements)
- Products in archive: _not stated_
- Code: MrBeam publicly available on GitHub  
  > "The software used to produce these results is MrBeam, publicly available through github" (Acknowledgements)
- Missing: ALMA run parameters (pixel grid, swarm settings, weights)
- Missing: pipeline version and EB selection
- Data volume (inferred): tens of GB (one ALMA Band 6 EHT-campaign observation, single spw used)
- Score (inferred): 3/5, Code public and data public, but ALMA run parameters and quantitative targets are lacking.
- Rediscovery candidate: no, Main ALMA result is qualitative image comparison; few numeric results.

## Links

- Method: Broderick2020b (defines closure traces)
- Method: Mus2023c (MO-PSO algorithm)
- Method: Mueller2023c (MOEA/D algorithm)
- Companion: Albentosa2023 (ALMA M87 closure trace model fitting reproduced here)
- Related: Event Horizon Telescope
- Related: ngEHT

## Checks

```json
{
 "quotes": 36,
 "quotes_ok": 36,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 2,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 30,
  "rate": 0.455
 },
 "evidence_ok": true
}
```
