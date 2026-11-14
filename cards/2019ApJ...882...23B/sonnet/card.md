# EHT-HOPS Pipeline for Millimeter VLBI Data Reduction

`2019ApJ...882...23B` | The Astrophysical Journal 2019 | first author: Blackburn, Lindy | arXiv: 1903.08832 | DOI: 10.3847/1538-4357/ab328d

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type technical_calibration_or_instrument

## Science

- Fields: instrumentation
- Question: How can an automated HOPS-based pipeline calibrate mm-wavelength VLBI data (GMVA+ALMA, EHT), and how does it compare with a classical AIPS reduction?  
  > "demonstrate the benefits from the specialized processing of high-frequency VLBI data with respect to classical analysis techniques." (abstract)
- Target **Sgr A***: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **NRAO 530**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: 86 GHz; 512 MHz total (256 MHz per polarization); four channels of 116 subchannels per polarization  
  > "A total bandwidth of 512 MHz (256 MHz per polarization) was recorded at each station except YS" (5.1 Data Set); "At correlation, the bandwidth per polarization was divided into four channels of 116 subchannels each." (5.1 Data Set)
- continuum bandwidth: _not stated_
- arrays: GMVA (8 VLBA, GBT, Yebes, IRAM 30m, Effelsberg) plus phased ALMA (37 antennas)  
  > "the Robert C. Byrd Green Bank Telescope (GBT), the Yebes 40m telescope (YS), the IRAM 30m telescope (PV), the Effelsberg 100 m telescope (EB), and the ALMA phased array of 37 antennas" (5.1 Data Set)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2017 April 3  
  > "observations of Sgr A$^{\ast}$ on 2017 April 3 (project code MB007)" (5.1 Data Set)
- pi or archival as stated: _not stated_
- Other facility **GMVA / VLBA / GBT / Effelsberg / IRAM 30m / Yebes**: VLBI stations of the 86 GHz GMVA+ALMA data set  
  > "composed of the eight VLBA antennas operating at 86 GHz, the Robert C. Byrd Green Bank Telescope (GBT)" (5.1 Data Set)
- External data: Simultaneous ALMA interferometric total flux of NRAO 530 used to constrain imaging  
  > "constraining the total flux of the source from simultaneous ALMA interferometric measurements (cite: Goddi_2019)" (5.2 Pipeline Comparison) [from (cite: Goddi_2019)]

## Processing

### Calibration

- pipeline or manual: EHT-HOPS pipeline (HOPS fourfit + eat + eht-imaging), compared with manual AIPS reduction  
  > "We have performed a comparative analysis of the GMVA+ALMA data set processed by the EHT-HOPS pipeline and a classic AIPS reduction." (Pipeline Comparison)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: eht-imaging closure-only imaging of NRAO 530  
  > "We image NRAO 530 using the `eht-imaging` library (cite: chael2016), following the closure imaging method of (cite: Chael2018)." (5.2 Pipeline Comparison)
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

- Observation details of the MB007 GMVA+ALMA data set  
  > "See (cite: Issaoun_2019) for further details on the observations." (5.1 Data Set) [from (cite: Issaoun_2019)]
- Network calibration extends earlier techniques  
  > "the EHT-HOPS implementation of network calibration is an extension of techniques developed in (cite: Johnson2015)" (3.3 Network Amplitude Calibration) [from (cite: Johnson2015)]
- Global fringe least-squares approach  
  > "Following (cite: alef1986), we take the estimated baseline and polarization-dependent delay and delay rate solutions" (2.5 Global Fringe Solution) [from (cite: alef1986)]

### Not stated but needed to reproduce (our reading)

- Flagging intervals and notches used for MB007
- Savitzky-Golay polynomial degree actually used
- Polarization-gain polynomial orders for stations other than GBT
- eht-imaging imaging parameters and regularizers
- Software versions and Docker image tags
- Whether the MB007 correlated data are publicly retrievable

## Analysis recipe

1. **Fringe fit with iterative phase calibration**: Five fourfit stages: bandpass, ad hoc atmospheric phase, RCP-LCP delay, global fringe solution  
  > "The first five stages of the pipeline run several iterations of `fourfit` (cite: fourfitmanual), while solving for nonlinear phase corrections and a global fringe solution." (2 EHT-HOPS Pipeline)
   - software: HOPS fourfit, eat
   - parameter: S/N threshold ~7 for reliable detections  
  > "sets a threshold $\rho_\text{thr} \sim 7$ above which detections are considered reliable" (2.5 Global Fringe Solution)
   - fitting: Least-squares station-based delays/rates with soft_l1 loss at scale 8 sigma (Scipy)  
  > "The least-squares minimization is performed in Scipy with an additional `soft_l1` loss function" (2.5 Global Fringe Solution)
   - validation: _not stated_
2. **A priori amplitude, polarization calibration and network calibration**: Convert to UVFITS; apply SEFD from ANTAB tables, field rotation, RCP/LCP gain ratios, network calibration  
  > "The post-processing stages 7–9 that follow read and write `UVFITS` formatted data directly and apply amplitude calibration and polarization- and time-dependent phase corrections" (3 Post-processing)
   - software: eat, eht-imaging
   - fitting: _not stated_
   - validation: _not stated_
3. **Compare with AIPS reduction and image NRAO 530**: Compare detections, correlation amplitudes, closure quantities, and closure-only images between HOPS and AIPS  
  > "We have performed a comparative analysis of the GMVA+ALMA data set processed by the EHT-HOPS pipeline and a classic AIPS reduction." (5.2 Pipeline Comparison)
   - software: AIPS, eht-imaging
   - fitting: _not stated_
   - validation: Normalized closure differences smaller than a standard normal; images consistent  
  > "indicates that differences between the pipelines are of subthermal magnitude, even after full scan averaging." (5.2 Pipeline Comparison)

## Software

- **HOPS** : fringe fitting (fourfit) and fringe summary (alist, aedit)  
  > "HOPS (cite: Whitney_2004)" (Software)
- **eat** : Python interface to HOPS, global fringe solution, UVFITS conversion, post-calibration  
  > "we have extended the basic HOPS framework with Python-based packages, included within the EHT Analysis Toolkit" (2 EHT-HOPS Pipeline)
- **eht-imaging** : network calibration and closure imaging  
  > "We implemented this procedure for network calibration within the `eht-imaging` library" (3.3.2 Network Calibration Procedure)
- **AIPS** : classical reduction for comparison  
  > "The AIPS reduction followed a classical procedure for low-frequency VLBI" (5.1 Data Set)
- **Scipy** : savgol filter and least-squares fits  
  > "The least-squares minimization is performed in Scipy" (2.5 Global Fringe Solution)
- **Docker** : freezing the software environment  
  > "we use Docker, an operating-system-level virtualization software, to freeze the entire software environment" (4 Computing workflow)
- **GNU parallel** : parallel fourfit tasks per scan  
  > "we use GNU parallel to start multiple `fourfit` tasks, with one scan mapped per task" (4 Computing workflow)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total Stokes I detections, AIPS | 1040 | not stated | detections | 3 | / Total           / 1040 / 1331 / |
| Total Stokes I detections, HOPS | 1331 | not stated | detections | 3 | / Total           / 1040 / 1331 / |
| Sgr A* detections AIPS vs HOPS | 196 vs 461 | not stated | detections | 3 | / Sgr A$^{\ast}$  / 196  / 461  / |

## Qualitative findings

- HOPS and AIPS give consistent high-S/N amplitudes, closure quantities and images; HOPS closure phases are smoother  
  > "The HOPS and AIPS closure phases are generally consistent, but the HOPS data set indicates smoother trends." (5.2 Pipeline Comparison)

## Claim tuples

- H: Specialized mm-VLBI processing recovers more detections than classical AIPS | E: Reduce MB007 GMVA+ALMA data with both pipelines and count detections | R: 1331 vs 1040 total; Sgr A* 461 vs 196 | F: EHT-HOPS is more efficient, especially for Sgr A* | **supported**
- H: HOPS output is consistent with AIPS | E: Compare correlation amplitudes, closure quantities and NRAO 530 images | R: High consistency at high S/N; images similar | F: HOPS products are reliable | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Phase variations on seconds timescales require on-source atmospheric phase correction beyond classical fringe fitting  
  > "atmospheric turbulence causes nonlinear, stochastic phase evolution on timescales of seconds" (2.3 Atmospheric Phase)
- How they decided it was enough: _not stated_
- Limitation (authors): No automated flagging; leakage calibration not implemented  
  > "The EHT-HOPS pipeline does not currently implement automated flagging in either time or frequency" (2.1 Data Flagging); "the calibration of which is not yet a standard part of the EHT-HOPS data calibration pipeline" (3.2)
- Caveat (inferred, ours): AIPS reduction used a fixed 10 s solution interval, so comparison may be unfair
- Caveat (inferred, ours): Single dataset validation
- Caveat (inferred, ours): No ground truth for detections; comparison relative only

## Reproducibility

- Data public (paper): Software on GitHub; data availability not stated  
  > "are version controlled by `git` and publicly available on GitHub" (4 Computing workflow)
- Products in archive: _not stated_
- Code: eat library public on GitHub  
  > "EHT Analysis Toolkit[^5] (`eat` library)" (2 EHT-HOPS Pipeline)
- Missing: Control files and flagging for MB007
- Missing: Software versions
- Missing: Correlated VLBI data access
- Data volume (inferred): ~100 GB to TB of correlated VLBI data
- Score (inferred): 3/5, Methods are described with equations and code is public, but exact parameters, versions, and data access are lacking.
- Rediscovery candidate: no, Pipeline paper; data access and full recipe unclear.

## Links

- Method: (cite: fourfitmanual) (fourfit fringe fitter)
- Method: (cite: Johnson2015) (basis for phase stabilization and network calibration)
- Companion: (cite: Issaoun_2019) (Science results from the same GMVA+ALMA Sgr A* data)
- Companion: (cite: PaperIII) (EHT M87 calibration using this pipeline)
- Related: Event Horizon Telescope
- Related: Global Millimeter VLBI Array

## Checks

```json
{
 "quotes": 37,
 "quotes_ok": 37,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2016.1.00413.V"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 29,
  "rate": 0.408
 },
 "evidence_ok": true
}
```
