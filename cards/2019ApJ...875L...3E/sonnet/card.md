# First M87 Event Horizon Telescope Results. III. Data Processing and Calibration

`2019ApJ...875L...3E` | The Astrophysical Journal Letters 2019 | first author: Event Horizon Telescope Collaboration | arXiv: 1906.11240 | DOI: 10.3847/2041-8213/ab0c57

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type technical_calibration_or_instrument

## Science

- Fields: agn_and_quasars, instrumentation
- Question: How are EHT 2017 1.3 mm VLBI data (including phased ALMA) correlated, phase- and amplitude-calibrated, and validated to produce science-ready M87 and 3C 279 visibilities?  
  > "We present the calibration and reduction of Event Horizon Telescope (EHT) 1.3 mm radio wavelength observations of the supermassive black hole candidate at the center of the radio galaxy M87 and the quasar 3C 279" (abstract)
- Target **M87**: coordinates α J2000 = 12h30m49.42s, δ J2000 = +12°23′28.04″ (as printed, decimal points lost)  
  > "M87 (α J2000 = 12 [h] 30 [m] 49 42, δ J2000 = 12°23′28 04) was observed as a target source on three nights" (2. Observations); z/distance _not stated_; distance from Blakeslee et al. 2009; Gebhardt et al. 2011; Cantiello et al. 2018 cited  
  > "M87 (α J2000 = 12 [h] 30 [m] 49 42, δ J2000 = 12°23′28 04) was observed as a target source on three nights" (2. Observations)
- Target **3C 279**: coordinates α J2000 = 12h56m11.17s, δ J2000 = −05°47′21.52″ (as printed)  
  > "3C 279 (α J2000 = 12 [h] 56 [m] 11 17, δ J2000 = −05°47′21 52)" (2. Observations); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01154.V
- bands: 1.3 mm (~230 GHz), two 2 GHz bands at 227.1 and 229.1 GHz  
  > "The 2017 observing run recorded two 2 GHz bands, low and high, centered at sky frequencies of 227.1 and 229.1 GHz" (2. Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA as phased array of usually 37 antennas, plus APEX, LMT, SPT, PV, SMT, SMA, JCMT  
  > "ALMA observed as a phased array of usually 37 dual linear polarization antennas" (2. Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 25 μas  
  > "reaching an angular resolution of 25 μas" (abstract)
- max recoverable scale: _not stated_
- sensitivity: ~1 mJy on baselines to ALMA, ~10 mJy on other baselines  
  > "characteristic sensitivity limits of ∼1 mJy on baselines to ALMA and ∼10 mJy on other baselines" (abstract)
- time on source: _not stated_
- observing dates: 2017 April 5, 6, 7, 10, 11 triggered; M87 on April 5, 6, 11 (plus 7 scans on April 10)  
  > "Observations were triggered on 2017 April 5, 6, 7, 10, and 11." (2. Observations)
- pi or archival as stated: _not stated_
- Other facility **APEX, LMT, SPT, IRAM 30m, SMT, SMA, JCMT**: Other EHT VLBI stations  
  > "the ALMA and the Atacama Pathfinder Experiment (APEX) in the Atacama Desert in Chile, the Large Millimeter Telescope Alfonso Serrano (LMT)" (2. Observations)
- External data: ALMA QA2 total flux densities of M87 and 3C 279 used for network calibration  
  > "The flux density values used for network calibration in SR1 come from the initial ALMA QA2 data release (2017 October), with a quoted uncertainty of 10%." (Table 4) [from Goddi et al. 2019]

## Processing

### Calibration

- pipeline or manual: Three independent pipelines: EHT-HOPS, CASA rPICARD, AIPS (ParselTongue); common post-processing for flux calibration  
  > "data reduction is carried out with three independent phase calibration (fringe-fitting) and reduction pipelines." (1. Introduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% for ALMA (lower limit)  
  > "the uncertainty of 10% for the derived SEFD of the ALMA phased array is considered a lower limit." (6.1.4 Phased-array Calibration)
- self calibration: Network calibration via chi-squared minimization with 10 s solution intervals  
  > "network calibration is performed on frequency-averaged visibility UVFITS data coherently time-averaged over 10 s solution intervals." (6.2 Network Calibration)

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

- ALMA QA2 reduction and PolConvert calibration input  
  > "PolConvert takes auxiliary calibration input from the quality assurance stage 2 (QA2) ALMA interferometric reduction of data (Goddi et al. 2019)." (4. Correlation) [from Goddi et al. 2019]
- EHT-HOPS pipeline details  
  > "Details for all steps can be found in Blackburn et al. (2019)." (5.1 HOPS Pipeline) [from Blackburn et al. 2019]

### Not stated but needed to reproduce (our reading)

- Raw correlated data (petabyte-scale voltages; 665/713 GB correlated) are not in ALMA archive form
- Exact flagging lists and per-pipeline solution intervals
- rPICARD configuration and CASA fringefit version

## Analysis recipe

1. **Correlate and convert polarization**: DiFX correlation (AP 0.4 s, 0.5 MHz channels); PolConvert linear-to-circular for ALMA  
  > "Data were correlated with an accumulation period (AP) of 0.4 s and a frequency resolution of 0.5 MHz" (4. Correlation)
   - software: DiFX, PolConvert
   - fitting: _not stated_
   - validation: Baseband data exchanged between correlators to verify output  
  > "Baseband data on a few high-S/N scans with good coverage were exchanged between the two sites to verify the output of each correlator against the other." (4. Correlation)
2. **Fringe fitting**: Phase calibration with HOPS fourfit, CASA fringefit (rPICARD), and AIPS KRING  
  > "we describe three independent fringe-fitting pipelines for phase calibration, based on three different software packages for VLBI data processing" (5. Fringe Detection)
   - software: HOPS, CASA, AIPS
   - parameter: Global fringe solution from baselines with S/N > 7 (HOPS)  
  > "These are derived from a least-squares solution (as proposed by Alef & Porcas 1986) to relative delays and delay-rates from confident baseline detections with S/N > 7" (5.1 HOPS Pipeline)
   - fitting: least-squares global delays and rates  
  > "These are derived from a least-squares solution (as proposed by Alef & Porcas 1986) to relative delays" (5.1. HOPS Pipeline)
   - validation: Fringe consistency tests of RR vs LL delays  
  > "Delay calibration assumes a constant RCP versus LCP delay offset per night at each station" (8.1 Fringe Validation)
3. **A priori and network amplitude calibration**: SEFD from Tsys, DPFU, gain curve; network calibration using ALMA-APEX and SMA-JCMT redundancy  
  > "The flux density calibration for the EHT is done in two steps and is a common post-processing procedure for all three phase calibration pipelines" (6. Flux Density Calibration)
   - software: eht-imaging, eat
   - assumption: Co-located sites act as zero-baseline interferometer; ALMA total flux from QA2  
  > "The second is that co-located sites provide a zero-baseline interferometer (e.g., ALMA–APEX), with a corresponding visibility that is a positive real number equal to the total flux density V 0 ." (6.2 Network Calibration)
   - fitting: chi-squared minimization over station gains and model visibilities  
  > "by minimizing an associated χ [2]" (6. Flux density calibration (network calibration))
   - validation: _not stated_
4. **Validate data and estimate systematics**: Thermal error tests, coherence tests, closure-quantity consistency (RR-LL, bands, trivial closures), inter-pipeline comparison  
  > "In this section, we summarize data set validation tests, performed using diagnostic tools developed in the eat library framework" (8. Data Validation and Systematics)
   - software: eat
   - parameter: S/N<7 excluded; mad0 = 1.4826 med|Y| statistic  
  > "We exclude low S/N data (S/N < 7), for which the normal distribution approximation does not hold well." (8.4.1 Quantifying Residual Errors)
   - fitting: systematic error s solved so that normalized mad0 = 1  
  > "The results of the SR1 errors estimation by normalizing mad 0 are summarized in Table 7." (8.4.2. RR-LL Consistency)
   - validation: _not stated_

## Software

- **DiFX** : Correlation  
  > "Each correlator is a networked computer cluster running a standard installation of the DiFX software package (Deller et al. 2011)." (4. Correlation)
- **HOPS** : Fringe fitting (primary data set)  
  > "For EHT 2017 observations, HOPS was augmented with a collection of auxiliary calibration scripts, and packaged into an EHT-HOPS pipeline" (5.1. HOPS Pipeline)
- **CASA** : rPICARD fringe-fitting pipeline  
  > "The modular, general-purpose rPICARD VLBI data reduction pipeline (Janssen et al. 2019a) is used for the calibration of EHT data." (5.2 CASA Pipeline)
- **AIPS** : Fringe fitting with KRING via ParselTongue  
  > "The custom AIPS pipeline is an automated Python-based script using functions implemented in the eat package." (5.3 AIPS Pipeline)
- **PolConvert** : Linear-to-circular conversion of ALMA data  
  > "The software routine PolConvert (Martí-Vidal et al. 2016; Matthews et al. 2018) was created to convert visibilities" (4. Correlation)
- **eht-imaging** : Network calibration  
  > "We implemented network calibration via this minimization procedure within the eht-imaging library (Chael et al. 2016, 2018)." (6.2 Network Calibration)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| M87 first visibility null | ~3.4 | not stated | Gλ | 3 | two nulls in correlated flux density at ∼3.4 and ∼8.3 Gλ |
| M87 second visibility null | ~8.3 | not stated | Gλ | 3 | two nulls in correlated flux density at ∼3.4 and ∼8.3 Gλ |
| Baseline systematic errors | 2% amplitude, 1° phase | not stated | % / deg | 4 | set limits on baseline systematic errors of 2% in amplitude and 1° in phase |
| Median HOPS–CASA visibility difference (M87) | 3.8 | 0.7 thermal units | % | 4 | Median visibility error (%) 3.8(0.7) 7.9(1.5) 9.4(1.5) |

## Qualitative findings

- M87 closure phases evolve between April 5/6 and April 10/11, indicating intrinsic source variability on timescales of days  
  > "We observe clear indications of modest source evolution between the two pairs of nights, and broad consistency within each pair." (7.3. Data Features)

## Claim tuples

- H: Can three independent pipelines produce consistent calibrated EHT data? | E: Compared HOPS, CASA and AIPS outputs | R: Median HOPS–CASA amplitude difference 3.8%; closure quantities consistent within thermal errors | F: Pipelines are largely consistent; HOPS chosen as primary | **supported**
- H: Are residual non-closing errors small enough for imaging and modeling? | E: Closure-quantity consistency tests | R: Non-closing errors no larger than 2° in closure phase and 4% in closure amplitude for M87 | F: Systematics are below thermal uncertainty for M87 | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Polarimetric leakage not calibrated; LMT and SPT amplitude errors are lower limits; ALMA 10% uncertainty is a lower limit  
  > "In this first science release, the issue of polarimetric leakage calibration and correction is not addressed." (7.1 Data Release Specification)
- Caveat (inferred, ours): Network calibration assumes point-like co-located baselines, questionable for extended M87
- Caveat (inferred, ours): Flux scale uses early QA2 values later revised ~10% higher

## Reproducibility

- Data public (paper): SR1 data and software available via EHT data portal  
  > "Information about accessing SR1 data and the software used for analysis can be found on the Event Horizon Telescope website’s data portal." (7.1 Data Release Specification)
- Products in archive: _not stated_
- Code: eat available on GitHub  
  > "109 [http://github.com/sao-eht/eat](http://github.com/sao-eht/eat)" (5.1 HOPS Pipeline)
- Missing: Raw VLBI voltage data and correlator configuration are not generally available
- Missing: Details deferred to Blackburn et al. 2019, Janssen et al. 2019a, Goddi et al. 2019
- Data volume (inferred): ~1.4 TB correlated data; ~16 GB phase-calibrated; ~0.24 GB network-calibrated
- Score (inferred): 3/5, Pipeline described and products released, but many details deferred to companion papers and raw data are inaccessible.
- Rediscovery candidate: no, Requires VLBI correlation and specialized pipelines; ALMA role is phased-array station data.

## Links

- Method: Blackburn et al. 2019 (EHT-HOPS pipeline)
- Method: Janssen et al. 2019a (rPICARD CASA VLBI pipeline)
- Method: Goddi et al. 2019 (ALMA QA2 for VLBI)
- Companion: EHT Collaboration et al. 2019a (Paper I) (M87 results overview)
- Companion: EHT Collaboration et al. 2019b (Paper II) (Array and instrumentation)
- Companion: EHT Collaboration et al. 2019c (Paper IV) (Imaging)
- Related: Event Horizon Telescope
- Related: ALMA Phasing Project

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 38,
  "rate": 0.514
 },
 "evidence_ok": true
}
```
