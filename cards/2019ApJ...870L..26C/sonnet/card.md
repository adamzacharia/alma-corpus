# ALMA Autocorrelation Spectroscopy of Comets: The HCN/H<SUP>13</SUP>CN Ratio in C/2012 S1 (ISON)

`2019ApJ...870L..26C` | The Astrophysical Journal Letters 2019 | first author: Cordiner, M. A. | arXiv: 1901.08676 | DOI: 10.3847/2041-8213/aafb05

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: solar_system, astrochemistry
- Question: Can ALMA main-array autocorrelation spectra recover extended coma emission from comet ISON, and what is the H12CN/H13CN ratio (13C fractionation in cometary HCN)?  
  > "The need for improved constraints on the $^{13}$C fraction in cometary HCN provides motivation for our present study." (Introduction)
- Target **Comet C/2012 S1 (ISON)**: coordinates _not stated_; z/distance heliocentric 0.54 au, geocentric 0.88 au  
  > "We obtained ALMA observations using the Band 7 receiver on 2013 November 17 at a heliocentric distance of 0.54 au and geocentric distance 0.88 au" (2 Observations and Calibration); distance from _not stated_

## Data provenance

- ALMA projects: 2012.A.00033.S, 2013.1.00278.S
- bands: Band 7  
  > "We obtained ALMA observations using the Band 7 receiver on 2013 November 17" (2 Observations and Calibration)
- frequencies and spectral setup: Two settings centered around 350 and 357 GHz; setting 1 HCN and H13CN, setting 2 three CH3OH lines  
  > "The correlator was configured with two frequency settings (centered around 350 and 357 GHz)" (2 Observations and Calibration)
- continuum bandwidth: _not stated_
- arrays: 28 active 12-m antennas of the main array  
  > "Twenty-eight 12-m antennas were active and the minimum antenna spacing was 17.3 m" (2 Observations and Calibration)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: ~5" (interferometric images); primary beam FWHM 16.4" at 354 GHz  
  > "which corresponds to a maximum recoverable angular scale of $\sim$5" in the interferometric images." (2 Observations and Calibration)
- sensitivity: H13CN RMS 1.4 mK; median Tsys 134 K  
  > "The extremely low (1.4 mK) RMS noise level of our H$^{13}$CN spectrum, with only 45 min of observations" (Discussion)
- time on source: _not stated_
- observing dates: 2013 November 17; setting 1 UT 11:31-12:16, setting 2 UT 12:30-13:29  
  > "observed during UT 11:31-12:16 and UT 12:30-13:29, respectively" (2 Observations and Calibration)
- pi or archival as stated: _not stated_
- Line: H13CN J=4-3 (345.340 GHz)
- Line: HCN J=4-3 (354.505 GHz)
- Line: CH3OH 4_0-3_-1 E, 1_1-0_0 A+, 7_2-6_1 E (350.688, 350.905, 363.740 GHz)
- Other facility **APEX**: Archival single-dish HCO+ spectra of IRAS 16293-2422 (13 spectra, 2008-2017) for validating the autocorrelation method  
  > "we averaged 13 archival HCO$^+$ spectra (observed 2008 to 2017) to produce the comparison spectrum" (Results)
- External data: Nucleus position used to extract model spectra  
  > "model spectra were extracted at the nucleus position identified by (cite: cor14)" (Radiative transfer modeling) [from (cite: cor14)]
- External data: Collision rates for HCN and CH3OH from LAMDA  
  > "Molecular collision rates for HCN and CH$_3$OH were taken from the Leiden Atomic and Molecular Database (cite: sch05)" (Radiative transfer modeling) [from (cite: sch05)]
- External data: Photodissociation rates for HCN and CH3OH  
  > "Photodissociation rates for HCN and CH$_3$OH were obtained from (cite: cro94)." (Radiative transfer modeling) [from (cite: cro94)]

## Processing

### Calibration

- pipeline or manual: Standard CASA calibration with JAO-supplied scripts  
  > "The raw ALMA data were initially subject to standard calibration in CASA (cite: jae08), using the scripts supplied by the Joint ALMA Observatory (JAO)." (2 Observations and Calibration)
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
- continuum subtraction: Savitsky-Golay filter on line-free spectrum, 51-channel window, order 3 polynomial  
  > "using a 51 channel window and polynomial of order 3." (2 Observations and Calibration)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Water production rate Q(H2O)=2e29 s-1  
  > "A water production rate $Q({\rm H_2O}) = 2\times10^{29}$ s$^{-1}$ was used, following (cite: cor14)." (Radiative transfer modeling) [from (cite: cor14)]
- Single-dish calibration techniques  
  > "For more details regarding single-dish calibration techniques, see (cite: one02)." (2 Observations and Calibration) [from (cite: one02)]

### Not stated but needed to reproduce (our reading)

- Which scans/antennas were averaged and any flagging or weighting
- Line-free channel ranges for baseline fitting
- Velocity range for line integration
- Opacity tau0 values used
- Model details such as abundance profile and photodissociation scale lengths
- Observation details of the interferometric cross-correlation comparison

## Analysis recipe

1. **Extract and calibrate autocorrelation spectra**: Unflag and extract autocorrelation spectra with plotms; (on-off)/off, times Tsys, opacity correction to TA' scale; average over antennas and scans  
  > "Background-subtracted spectra were produced for each individual antenna by taking the quotient: *(on-off)/off*, then converted to antenna temperatures by multiplying by $T_{sys}$" (2 Observations and Calibration)
   - software: CASA, plotms
   - parameter: opacity correction e^tau0/sin(phi)  
  > "A correction for atmospheric opacity of $e^{\tau_0}/sin(\phi)$ was applied" (2 Observations and Calibration)
   - assumption: 3C 279 scans serve as sky reference  
  > "which we later used as an improvised off-source position for sky subtraction" (2 Observations and Calibration)
   - fitting: _not stated_
   - validation: Compared with APEX HCO+ spectra of IRAS 16293-2422; agrees within one standard deviation  
  > "our ALMA autocorrelation spectrum lies within one standard deviation of the APEX spectra (shaded region), confirming the efficacy of our method." (Results)
2. **Measure line intensities and rotational temperature**: Integrate lines; rotational diagram of three CH3OH lines  
  > "Using a rotational diagram analysis (cite: boc94), the best-fitting rotational temperature was found to be $T_{rot}=139\pm29$ K" (Results)
   - fitting: Rotational diagram fit  
  > "Using a rotational diagram analysis (cite: boc94), the best-fitting rotational temperature was found to be $T_{rot}=139\pm29$ K" (Results)
   - validation: _not stated_
3. **Non-LTE radiative transfer modeling for production rates**: Modified LIME, statistical equilibrium plus Monte Carlo, Haser spherical coma, collisions with H2O and electrons, fluorescent pumping; fit CH3OH for Tkin then derive Q  
  > "Our model employs a modified version of the Line Modeling Engine (cite: bri10)" (Radiative transfer modeling)
   - software: LIME
   - parameter: 5,000 cells Delaunay grid; expansion velocity 1.1 km/s; Tkin 145 K  
  > "The model coma is divided into 5,000 cells on an unstructured Delaunay grid with logarithmic radial sampling." (Radiative transfer modeling)
   - assumption: H13CN photodissociation and pumping rates same as HCN  
  > "the photodissociation and pumping rates for H$^{13}$CN were assumed to be the same as for HCN" (Radiative transfer modeling)
   - fitting: Simultaneous fit of all detected CH3OH transitions for Tkin  
  > "The coma kinetic temperature was derived by simultaneously fitting all the detected CH$_3$OH transitions, resulting in $T_{kin}= 145$ K." (Radiative transfer modeling)
   - validation: Collision rates varied by factor 2 changed line intensities by a few percent; alternative Tkin=100 K model run  
  > "varying them by a factor of 2 and found that the predicted line intensities changed by only a few percent" (Radiative transfer modeling)

## Software

- **CASA** : Standard calibration  
  > "standard calibration in CASA (cite: jae08)" (2 Observations and Calibration)
- **plotms** : Extracting autocorrelation spectra  
  > "then extracted using `plotms`" (2 Observations and Calibration)
- **LIME** modified version: Coma radiative transfer  
  > "a modified version of the Line Modeling Engine (cite: bri10)" (Radiative transfer modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H12CN/H13CN ratio | 88 | ±18 | dimensionless | 3 | reveal an H$^{12}$CN/H$^{13}$CN ratio of $88 \pm 18$ |
| CH3OH rotational temperature | 139 | ±29 | K | 2 | $T_{rot}=139\pm29$ K |
| Q(HCN) | 3.0e26 | ±0.1e26 | s-1 | 3 | $(3.0 \pm 0.1) \times 10^{26}$ |
| Q(H13CN) | 3.4e24 | ±0.7e24 | s-1 | 3 | $(3.4 \pm 0.7)\times 10^{24}$ |
| Ratio with Tkin=100 K | 82 | ±17 | dimensionless | 3 | The corresponding H$^{12}$CN/H$^{13}$CN ratio is $82\pm17$ |

## Qualitative findings

- Autocorrelation gives ~14x line brightness vs interferometer; H13CN not detectable in cross-correlation data  
  > "Note that H$^{13}$CN was not even detectable in the cross-correlation data" (Results)

## Claim tuples

- H: Autocorrelation data recover extended coma emission lost by the interferometer | E: Combined autocorrelation spectra of 28 antennas compared with interferometric spectra | R: 14-fold increase in line brightness; first H13CN detection | F: Autocorrelation spectroscopy is a useful new technique for extended sources | **supported**
- H: HCN in comet ISON shows 13C fractionation | E: Non-LTE modeling of HCN and H13CN | R: ratio 88±18 vs terrestrial 89 | F: No significant 13C fractionation | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Tkin=100 K (Trot=90 K from IRAM) alternative model gives ratio 82±17, same conclusion  
  > "we ran alternative models using $T_{rot}=90$ K ($T_{kin}=100$ K)" (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Ad-hoc use of phase calibrator scans for sky subtraction leaves standing waves and sky lines and high noise  
  > "Our ad-hoc use of phase calibration scans to subtract the sky and telescope background signal is far from ideal" (Discussion)
- Caveat (inferred, ours): Only three CH3OH lines constrain temperature, which affects Q
- Caveat (inferred, ours): Sky-subtraction residuals and 7 degree reference offset introduce systematics
- Caveat (inferred, ours): Single epoch, single comet

## Reproducibility

- Data public (paper): Archival ALMA data  
  > "This technique has been applied to archival observations of comet C/2012 S1 (ISON)." (Conclusion)
- Products in archive: _not stated_
- Missing: Radiative transfer code is a modified, unreleased LIME
- Missing: Exact scan selection and line-integration windows
- Data volume (inferred): tens to hundreds of GB (raw 28-antenna Band 7 data with autocorrelations)
- Score (inferred): 3/5, Public data and clear outline, but the modified model and some processing choices are not given.
- Rediscovery candidate: no, Requires custom modified non-LTE model and unspecified processing details.

## Links

- Method: (cite: bri10) (LIME radiative transfer code)
- Method: (cite: boc94) (rotational diagram analysis)
- Companion: (cite: cor14) (earlier ALMA ISON interferometric analysis)
- Companion: (cite: cor17) (further ALMA ISON details)

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 34,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
