# ALMA Long Baseline Campaigns: Phase Characteristics of Atmosphere at Long Baselines in the Millimeter and Submillimeter Wavelengths

`2017PASP..129c5004M` | Publications of the Astronomical Society of the Pacific 2017 | first author: Matsushita, Satoki | arXiv: 1701.03032 | DOI: 10.1088/1538-3873/aa5787

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type technical_calibration_or_instrument

## Science

- Fields: instrumentation
- Question: What are the atmospheric phase fluctuation characteristics at ALMA baselines up to ~15 km, how well does WVR correction work, and how well would fast switching work?  
  > "we present the detailed characterization of phase fluctuation, improvement of phase fluctuation after the water vapor radiometer (WVR) phase correction method" (Introduction)
- Target **Bright quasars observed as single source stares (e.g. 3C279, 3C454.3, 0522-364, 1924-292)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: Bands 3, 6, 7 for all campaigns; Band 8 only in 2014  
  > "We used Bands 3 (100 GHz band), 6 (200 GHz band), and 7 (300 GHz band) for all the campaigns, except for Band 8 (400 GHz band), which was only used in the 2014 campaign." (Observations and Data Reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12 m antennas only, ten or more per measurement  
  > "We only used 12 m diameter antenna data and did not use data taken with 7 m diameter antennas" (Observations and Data Reduction)
- configurations: _not stated_
- baselines: longest 2 km (2012), 3 km (2013), 10-15 km (2014)  
  > "starting from the longest baseline length of 600 m in 2010 and 2011, 2 km in 2012, 3 km in 2013, and finally $10-15$ km in 2014" (Introduction)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 10-40 min per stare, ~1 s integration  
  > "for tens of minutes (usually $10-40$ minutes, depending on the longest baseline length) with $\sim1$ s integration time per data point" (Observations and Data Reduction)
- observing dates: 2012-2014 campaigns (Tables 3-5)  
  > "measured between 2012 and 2014 of Atacama Large Millimeter/submillimeter Array (ALMA) long baseline campaigns" (abstract)
- pi or archival as stated: _not stated_
- External data: Typical system temperatures per ALMA band used for thermal phase noise estimate  
  > "assume the source flux density is 1 Jy and the system temperature is a typical value for each ALMA Band (cite: rem15)" (Observations and Data Reduction) [from (cite: rem15)]
- External data: Site-testing radio seeing monitor 50% quartile slope 0.63 for comparison  
  > "consistent with the 50% quartile slope for the 3-year (1996 July – 1999 March) statistical data using the site testing 11.2 GHz radio seeing monitor of 0.63 (cite: but01)" (3.2.2 Slopes for the Spatial Structure Functions) [from (cite: but01)]

## Processing

### Calibration

- pipeline or manual: CASA standard ALMA calibration prescription; WVR correction with wvrgcal  
  > "The data were reduced using the Common Astronomy Software Applications (CASA) package (cite: mcm07), using a standard ALMA calibration prescription." (Observations and Data Reduction)
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
- smoothing: Data averaged to 10 s to suppress thermal noise  
  > "After this, we averaged the data points for 10 s to take out phase errors due to thermal noise." (Observations and Data Reduction)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Antenna position error causing linear phase drift, details in earlier paper  
  > "see (cite: fom15) for details" (Observations and Data Reduction) [from (cite: fom15)]

### Not stated but needed to reproduce (our reading)

- CASA version and wvrgcal options
- Exact ALMA project codes per execution block
- How SSF fit ranges and turn-over were selected per dataset
- Fast-switching simulation imaging parameters and self-cal solint
- Coherence-time calculation details beyond 0.9 threshold
- Data likely requires the 2014 long baseline science verification archive data

## Analysis recipe

1. **Reduce and clean phase data**: Apply WVR correction, remove linear phase drift, average to 10 s, compute rms phase per baseline as excess path length  
  > "We then calculated the rms phase fluctuation for each baseline. For the unit of phase, we express in path length." (Observations and Data Reduction)
   - software: CASA, wvrgcal
   - fitting: _not stated_
   - validation: Thermal phase noise estimated below measured fluctuation at 15 m baselines  
  > "We can therefore conclude that we successfully suppressed the effect of instrumental noise in our data with 10 s averaging." (Observations and Data Reduction)
2. **WVR improvement factor**: Ratio of rms excess path length without to with WVR, averaged over baselines, vs PWV  
  > "The improvement factor of the WVR phase correction method has been calculated as the ratio of the rms excess path length for each baseline without the WVR phase correction to that with the correction." (3.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit spatial structure function slopes and constants**: Fit log10(dL)=a log10(d)+b for d<500 m and d>1 km  
  > "We first fitted the slopes for the data points with baseline lengths shorter than 500 m and longer than 1 km for each SSF plot" (3.2.2)
   - fitting: Linear fit in log-log space  
  > "The fitting function is expressed as $$\begin{equation} \log_{10}(\Delta L) = a \times \log_{10}(d) + b," (3.2.2 Slopes for the Spatial Structure Functions)
   - validation: Compared with VLA and site-test slopes  
  > "The average slope without the WVR phase correction of $0.65\pm0.06$ is consistent with the 50% quartile slope for the 3-year (1996 July – 1999 March) statistical data using the site testing 11.2 GHz radio seeing monitor" (3.2.2 Slopes for the Spatial Structure Functions)
4. **Coherence time**: Median coherence time at >1 km baselines for coherence 0.9, calculation stopped at 400 s  
  > "Here, we calculate the coherence time that degrades the coherence to 0.9 (i.e., coherence loss of 10%)." (3.3)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fast switching simulation**: Split 2014 stares into target, calibrator, slew; calibrate, image, compare peak flux with self-calibrated image for cycle times 28, 48, 68 s  
  > "The coherence of the fast switching method is estimated by calculating the ratio of the peak flux densities between the fast switching simulation image and the self-calibrated one." (3.4)
   - software: CASA
   - parameter: Target time 3x calibrator time, 4 s slew  
  > "we used an integration time for the target of three times the integration time for the calibrator and a slew time of 4 s" (3.4)
   - assumption: Target and calibrator share identical atmospheric phase  
  > "since the “target” and the “calibrator” do have the same atmospheric phase fluctuation in this simulation" (3.4)
   - fitting: Linear fits of coherence vs cycle time  
  > "We also overplotted linear fitting results of coherence as a function of cycle time as solid lines." (3.4 Fast Switching Simulation)
   - validation: _not stated_

## Software

- **CASA** : Data reduction, imaging in fast switching simulation  
  > "The data were reduced using the Common Astronomy Software Applications (CASA) package (cite: mcm07)" (Observations and Data Reduction)
- **wvrgcal** : WVR phase correction and PWV  
  > "The WVR phase correction was applied using the program *wvrgcal* (cite: nik12) installed inside CASA." (Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean WVR improvement factor, all PWV | 2.1 | 0.7 | dimensionless | 2 | The mean improvement factor over all PWV conditions is $2.1\pm0.7$. |
| Improvement factor PWV>1 mm | 2.4 | 0.7 | dimensionless | 2 | with a mean improvement factor of $2.4\pm0.7$ |
| Improvement factor PWV<1 mm | 1.7 | 0.4 | dimensionless | 2 | In the case of PWV $<$ 1 mm, however, the ratio is $1.7\pm0.4$. |
| SSF slope <500 m, no WVR | 0.65 | 0.06 | dimensionless | 3 | $<500$ m        / $0.65\pm0.06$ |
| SSF slope >1 km, no WVR | 0.22 | 0.15 | dimensionless | 3 | The average slopes are $0.22\pm0.15$ and $0.29\pm0.13$ for the data before and after the WVR phase correction |
| SSF slope >1 km, with WVR | 0.29 | 0.13 | dimensionless | 3 | The average slopes are $0.22\pm0.15$ and $0.29\pm0.13$ for the data before and after the WVR phase correction |
| Mean rms excess path at 10 km after WVR, PWV<1 mm | 206 | not stated | micron | 3 | with a mean value of $206~\mu$m even at PWV $<$ 1 mm |
| Mean coherence time with WVR (0.9 coherence) | 184 | not stated | s | 4 | The average of the coherence time after the WVR phase correction is 184 s, about twice longer than that without (101 s). |
| Mean coherence time without WVR | 101 | not stated | s | 4 | about twice longer than that without (101 s) |

## Qualitative findings

- Most SSFs show a turn-over near 1 km, consistent with water vapor scale height; a few lack turn-over, implying a high scale-height constituent (water ice or dry component).  
  > "this large scale height turbulent constituent is likely to be water ice or a dry component." (abstract)

## Claim tuples

- H: Does WVR correction reduce phase fluctuation at long baselines? | E: Improvement factor vs PWV | R: Mean factor 2.1, 2.4 for PWV>1 mm | F: WVR works well especially for PWV>1 mm | **supported**
- H: Is water vapor the only turbulent constituent? | E: SSFs with/without WVR, turn-over analysis | R: Residual fluctuation remains; some SSFs without turn-over | F: Another high scale height constituent exists | **partially**
- H: Does fast switching improve coherence? | E: Simulation with 28, 48, 68 s cycle times | R: Coherence decreases almost linearly with cycle time | F: Shorter cycles linearly improve coherence | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Mountain-induced eddies, liquid water and LLC/correlator instrumental effects rejected as cause of residual phase fluctuation  
  > "Since we are looking for the cause of the remaining phase fluctuation *after* successful WVR phase correction, liquid water cannot be the cause." (3.2.5)
- How they decided it was enough: _not stated_
- Limitation (authors): Fast switching simulation is idealized, ignoring target-calibrator separation  
  > "This simulation is an idealized case" (3.4)
- Limitation (authors): Coherence time underestimated due to 400 s cutoff  
  > "since our calculation stops at 400 s, the coherence time is underestimated" (3.3)
- Caveat (inferred, ours): Large scatter makes PWV correlations weak
- Caveat (inferred, ours): Turn-over identification is by eye with fixed ranges
- Caveat (inferred, ours): Water ice/dry component attribution is speculative
- Caveat (inferred, ours): Weather parameters not analysed

## Reproducibility

- Data public (paper): ALMA data acknowledged as ADS/JAO.ALMA#0000.0.00341.CSV  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#0000.0.00341.CSV." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Software versions
- Missing: Fit selection criteria
- Missing: Fast switching imaging parameters
- Data volume (inferred): Tens to hundreds of GB (about 60 execution blocks)
- Score (inferred): 3/5, Execution blocks listed with IDs and methods clear, but versions, fit details and project codes missing.
- Rediscovery candidate: no, Data are listed but archive identification and several processing settings are unstated.

## Links

- Method: (cite: nik12) (wvrgcal WVR correction)
- Companion: (cite: fom15) (Overview of 2014 long baseline campaign)
- Companion: (cite: mat12; mat14; mat16) (Earlier results replaced by this paper)
- Related: ALMA long baseline campaigns 2012-2014

## Checks

```json
{
 "quotes": 42,
 "quotes_ok": 42,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00003.E"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 29,
  "rate": 0.42
 },
 "evidence_ok": true
}
```
