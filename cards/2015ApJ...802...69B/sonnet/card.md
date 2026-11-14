# Radio and Millimeter Monitoring of Sgr A*: Spectrum, Variability, and Constraints on the G2 Encounter

`2015ApJ...802...69B` | The Astrophysical Journal 2015 | first author: Bower, Geoffrey C. | arXiv: 1502.06534 | DOI: 10.1088/0004-637X/802/1/69

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, agn_and_quasars
- Question: Did the G2 encounter change the radio-to-millimeter flux density or spectrum of Sgr A*, and what is the millimeter spectral index?  
  > "we find no evidence for a change in the mean flux density or spectrum of Sgr A\* that can be attributed to interaction with the G2 source." (abstract)
- Target **Sgr A***: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00635.S
- bands: ALMA Band 6 (230 GHz) and Band 7 (345 GHz); eight epochs  
  > "over eight epochs, each with band 6 (230 GHz) and band 7 (345 GHz) receivers." (2.2 ALMA Observations)
- frequencies and spectral setup: four spectral windows per band (B6: 217-234.8 GHz; B7: 340.6-354.6 GHz); one high-resolution window per band (3840 channels)  
  > "| ALMA | B6-3 |         231.0 |         232.9 |     3840 |" (Table 2)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: snapshots of a few minutes  
  > "Observations were snapshots with durations of a few minutes." (2.2 ALMA Observations)
- observing dates: mid-2013 to mid-2014 (ALMA)  
  > "We carried out ALMA observations between mid-2013 and mid-2014" (2.2 ALMA Observations)
- pi or archival as stated: _not stated_
- Other facility **VLA**: 1-41 GHz snapshot monitoring, 15 epochs, Oct 2012-May 2014  
  > "between late 2012 and mid-2014 (Table 1) at frequencies between 1 and 41 GHz" (2.1 VLA Observations)
- Other facility **SMA**: 212-356 GHz flux densities of Sgr A* and J1733-130  
  > "Flux densities from the SMA for Sgr A\* and J1733-130 are tabulated in Table 6." (2.3 SMA Observations)
- External data: Historical 230, 345 and 690 GHz flux densities of Sgr A* (2001-2012)  
  > "presents historical data for Sgr A\* at 230, 345, and 690 GHz with dates from 2001 through 2012." (4.2 Changes in the Mean Spectrum) [from (cite: 2014MNRAS.442.2797D)]
- External data: Historical radio mean spectra of Sgr A*  
  > "We plot the total intensity spectrum alongside historical average spectra" (2.1 VLA Observations) [from (cite: 1998ApJ...499..731F; 2001ApJ...547L..29Z; 2004AJ....127.3399H)]
- External data: 230-690 GHz spectral index in four epochs, -0.4 to +0.2, mean -0.13  
  > "found that the 230 to 690 GHz spectral index ranged in four epochs from -0.4 to +0.2, with a mean of -0.13." (3 Results) [from (cite: 2006JPhCS..54..354M)]

## Processing

### Calibration

- pipeline or manual: VLA: standard CASA pipeline by NRAO staff; ALMA: pipeline plus custom Tsys correction and self-calibration  
  > "Standard pipeline calibration techniques in CASA were carried out by NRAO staff" (2.1 VLA Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: ALMA: Titan and Neptune; bandpass J1427-421; VLA: 3C 286  
  > "We set absolute amplitude calibration with observations of Titan and Neptune and set bandpass gains with observations of the compact source J1427-421." (2.2 ALMA Observations)
- flux scale uncertainty: 5% systematic calibration error, from calibrator variability  
  > "Thus, we take 5% as the systematic calibration error in the Sgr A\* flux density." (2.2 ALMA Observations)
- self calibration: Phase self-cal on 10 s integration; for Sgr A* only baselines >50 klambda  
  > "All calibrator sources and Sgr A\* were phase-self-calibrated on timescales of a single integration (10 sec)." (2.2 ALMA Observations)

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

- Long baselines (>50 klambda) exclude extended structure for Sgr A* flux  
  > "Past experience has shown that these long baselines are sufficient to exclude the effects of extended structure on the flux density of Sgr A\*" (2.1 VLA Observations) [from (cite: 2004AJ....127.3399H)]
- VLA pipeline calibration done by NRAO staff  
  > "Standard pipeline calibration techniques in CASA were carried out by NRAO staff" (2.1 VLA Observations) [from (cite: 2014IAUS..303..327S)]
- SMA Uranus/Neptune broadband spectral model  
  > "For Uranus and Neptune, we used the broadband spectral model from" (2.3 SMA Observations) [from (cite: 1993Icar..105..537G)]

### Not stated but needed to reproduce (our reading)

- CASA version used for ALMA and VLA
- ALMA flux models for Titan/Neptune and calibrator flux values adopted
- Details of the fitted system-temperature opacity correction
- The authors' custom code for VLA visibility subtraction and ALMA point-source fitting
- Which spectral windows/channels were averaged for ALMA fluxes
- Coordinates and distance of Sgr A*

## Analysis recipe

1. **Measure ALMA Sgr A* flux densities**: Fit a point source of unknown flux to visibilities on baselines >50 klambda after self-calibration and Tsys correction  
  > "Flux densities for Sgr A\* were obtained through fitting a point-source of unknown flux to visibilities on baselines longer than $50\, k\lambda$." (2.2 ALMA Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with SMA light curves and calibrator variability (5%, 9%, 14%)  
  > "Where the data are contemporaneous, we see very good agreement in both ALMA bands." (2.2 ALMA Observations)
2. **Measure VLA flux and differential flux**: Average visibility amplitudes on baselines >50 klambda; visibility subtraction of each epoch against the ensemble with 1/(u,v) distance weighting  
  > "We applied a weighting scheme that scales as the inverse of the $(u,v)$ distance." (2.1 VLA Observations)
   - fitting: _not stated_
   - validation: Different weighting schemes do not qualitatively alter conclusions  
  > "Different weighting schemes do not qualitatively alter our conclusions." (2.1 VLA Observations)
3. **Constrain bow shock area from 1 GHz excess**: Extrapolate excess at 1.5, 3.1, 5.4 GHz to 1 GHz and compare with model predictions  
  > "We extrapolate the flux density excess at 1.5, 3.1, and 5.4 GHz to 1 GHz, assuming a power-law spectrum with index $\alpha=-0.7$" (4.1 Presence of a Bow Shock)
   - assumption: optically thin synchrotron index -0.7  
  > "assuming a power-law spectrum with index $\alpha=-0.7$, appropriate for optically thin synchrotron emission." (4.1 Presence of a Bow Shock)
   - fitting: _not stated_
   - validation: _not stated_
4. **Spectral index and variability**: Power-law fits of VLA and ALMA spectra; Fourier power spectrum of 220 GHz light curve with bootstrap errors; KS tests vs historical data  
  > "The error bar was determined by bootstrap resampling." (4.2 Changes in the Mean Spectrum)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : VLA pipeline calibration  
  > "Standard pipeline calibration techniques in CASA were carried out by NRAO staff" (2.1 VLA Observations)
- **MIR** : SMA calibration  
  > "Data from each observing period were calibrated with the millimeter interferometer reduction (MIR) suite of reduction routines developed by the SMA" (2.3 SMA Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| VLA mean spectral index 1-40 GHz | 0.28 | 0.03 | dimensionless | 4 | the mean spectral index $\alpha$ is $0.28 \pm 0.03$ |
| ALMA mean spectral index 217-355 GHz | -0.06 | 0.26 | dimensionless | 4 | $\alpha = -0.06 \pm 0.26$ |
| Upper limit on G2 cross-sectional area (95%) | 2e29 | not stated | cm^2 | 3 | we can set an upper limit to the size of G2 of $\sim 2\times 10^{29} {\rm\, cm^2}$ |
| Mean ALMA Band 6 flux density | 3.6 | 0.6 | Jy | 1 | The mean ALMA Band 6 (230 GHz) flux density is $3.6 \pm 0.6$ Jy |
| 220 GHz light curve power-law index | -0.15 | 0.08 | dimensionless | 4 | $\alpha$ was found to be $-0.15 \pm 0.08$. |

## Qualitative findings

- Millimeter variability (~20% modulation index) exceeds that at <=40 GHz (8%)  
  > "is 8% at 40 GHz and below, while it is $\sim 20\%$ at millimeter wavelengths." (3 Results)

## Claim tuples

- H: G2 produced a low-frequency bow shock | E: VLA visibility subtraction at 1.5-5.4 GHz extrapolated to 1 GHz | R: excess upper limits 0.4-0.8 Jy | F: G2 cross-section <2e29 cm^2 | **supported**
- H: G2 enhanced accretion and mm emission | E: Compare ALMA/SMA/VLA mean fluxes with historical | R: increase no more than 20% | F: No evidence for G2-driven enhancement | **supported**
- H: Spectral break between 230 and 690 GHz | E: ALMA spectral index vs earlier measurements | R: flat index | F: No break; emission near optically thick/thin transition | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA lacked Tsys measurements on Sgr A* itself, requiring a correction  
  > "ALMA observations did not include system temperature measurements on Sgr A\* itself." (2.2 ALMA Observations)
- Caveat (inferred, ours): Historical comparisons mix instruments with different calibration
- Caveat (inferred, ours): Snapshot observations with sparse sampling
- Caveat (inferred, ours): No statistical errors reported for ALMA fluxes

## Reproducibility

- Data public (paper): ALMA project 2012.1.00635.S acknowledged; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA# 2012.1.00635.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Custom analysis code
- Missing: CASA version and ALMA calibration details
- Data volume (inferred): ~10-50 GB for eight short ALMA epochs
- Score (inferred): 3/5, Tables give flux densities and simple analysis, but custom code and details are unstated.
- Rediscovery candidate: no, Custom code, unspecified calibration details, and VLA/SMA data needed.

## Links

- Method: (cite: 2014IAUS..303..327S) (VLA service observing and pipeline)
- Companion: (cite: 2014MNRAS.442.2797D) (historical millimeter variability)
- Related: VLA G2 monitoring program
- Related: SMA Sgr A* monitoring

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 29,
  "rate": 0.42
 },
 "evidence_ok": true
}
```
