# Gas and dust around A-type stars at tens of Myr: signatures of cometary breakup

`2016MNRAS.461.3910G` | Monthly Notices of the Royal Astronomical Society 2016 | first author: Greaves, J. S. | arXiv: 1607.03695 | DOI: 10.1093/mnras/stw1569

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: debris_disks, protoplanetary_disks
- Question: Do A-type debris hosts show CO gas at tens of Myr, is the gas asymmetric relative to the dust, and can the CO be explained by a proto-planetary disc?  
  > "Here we find the sixth example of a CO-hosting disc, around the $\sim$30 Myr-old A0-star HD 32997." (abstract); "The gas-plus-dust systems are also tested here against model predictions that the short-lived CO component could be more spatially asymmetric than the dust." (Introduction)
- Target **HD 32297**: coordinates _not stated_; z/distance 112 pc  
  > "| HD32297 |  | A0V | 112 | 30 (6) | Yes | Yes | u.l. |  |" (Table 1); distance from Table 1 (source not given)  
  > "| HD32297 |  | A0V | 112 | 30 (6) | Yes | Yes | u.l. |  |" (Table 1)
- Target **49 Cet**: coordinates _not stated_; z/distance 59 pc  
  > "approximately 6.7 arcsec or 395 AU at 59 pc" (Results); distance from _not stated_
- Target **HD 21997**: coordinates _not stated_; z/distance 72 pc  
  > "| HD21997 | HR1082 | A3IV/V | 72 | 45 (8) | Yes | u.l. | u.l. |  |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (HD 32297, JCMT) (not stated)
- Other facility **JCMT SCUBA-2**: 450 and 850 micron continuum images of HD 21997 and 49 Cet (SONS)  
  > "HD 21997 and 49 Cet were observed with the SCUBA-2 camera (Holland et al. 2013) in 2012-2015" (Observations)
- Other facility **JCMT RxA3**: CO 2-1 spectrum of HD 32297  
  > "The CO data for HD 32297 at 1.3 mm were taken as part of a poor weather backup programme in 2013" (Observations)
- Other facility **ALMA (archival/literature)**: Archival CO 2-1 of beta Pic used for disc-integrated spectrum; literature ALMA images compared  
  > "For $\beta$ Pic, archival ALMA observations in CO J=2-1 were used to generate disc-integrated spectra" (Asymmetries)
- External data: Census of CO/CII/OI detections, ages and distances for 27 A-star debris hosts  
  > "The most recent systematic survey is that of Moór et al. (2015), who also summarise previous work." (CO census) [from Moór et al. (2015)]
- Simulation/model as data: ProDiMo models of CO flux versus disc mass; Jackson et al. (2014) asymmetry model spectra  
  > "using the ProDiMo code (Woitke et al. 2016) to solve self-consistently for chemistry and radiative transfer in steady-state" (Correlations)

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

- JCMT observing procedures  
  > "Observing procedures have been described by, for example, Panić et al. (2013, 2010)." (Observations) [from Panić et al. (2013, 2010)]

### Not stated but needed to reproduce (our reading)

- SPLAT baseline channel ranges and polynomial orders for narrow fit
- ALMA beta Pic project code and processing for spectrum
- ProDiMo model parameters
- Method of the power-law fit of F(CO) vs F(860um)

## Analysis recipe

1. **Reduce SCUBA-2 continuum**: makemap with high-pass filtering and zero-masking  
  > "The continuum data reduction used the makemap task in the SMURF package (Jenness et al. 2011)" (Observations)
   - software: SMURF
   - fitting: _not stated_
   - validation: _not stated_
2. **Detect CO 2-1 in HD 32297**: makecube, baseline fits in SPLAT with wide and narrow polynomial; integrate line  
  > "Figure 3 shows the CO spectrum towards HD 32297, reduced by two different methods to test for robustness." (CO spectroscopy)
   - software: SMURF, SPLAT
   - fitting: _not stated_
   - validation: Two baseline methods compared; sliding 14-channel window for false positives  
  > "the maximum integrated signal found in a sliding 14-channel-wide window was 17.1 mK km/s" (CO spectroscopy)
3. **Model CO versus disc mass**: ProDiMo steady-state chemistry and radiative transfer  
  > "The disc is assumed to have evolved into a ‘late’ proto-planetary stage, with a gas-to-dust mass ratio of 10" (Correlations)
   - software: ProDiMo
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **SMURF** : makemap and makecube reduction  
  > "The spectral reduction used the makecube task in SMURF plus the SPLAT package for baselining and binning." (Observations)
- **SPLAT** : baselining and binning spectra  
  > "The spectral reduction used the makecube task in SMURF plus the SPLAT package for baselining and binning." (Observations)
- **SExtractor** : disc axis of 49 Cet at 450 um  
  > "The SExtractor tool for automatic object detection[^2] was used here" (Dust imaging)
- **ProDiMo** : CO radiative transfer models  
  > "using the ProDiMo code (Woitke et al. 2016)" (Correlations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HD 32297 CO 2-1 integrated signal, wide-fit baseline | 200.0 | 19.1 | mK km/s | 2 | The wide-fit baseline yields a 10.5 sigma detection of 200.0 $\pm$ 19.1 mK km/s. |
| HD 32297 CO 2-1 integrated signal, narrow-fit baseline | 106.4 | 17.5 | mK km/s | 2 | results in a detection with 6.1 sigma confidence, and integrated line signal of 106.4 $\pm$ 17.5 mK km/s. |
| F(CO) vs F(860um) power-law index | 1.7 | not stated | dimensionless | 0 | F(CO) $\propto$ F(860$\mu$m)$^{1.7}$ |
| CO-detection incidence in 5-50 Myr A-star debris hosts | 7/16 | not stated | dimensionless | 0 | now shows 7/16 detections of carbon-bearing gas within the 5-50 Myr epoch, with no detections in 11 older systems |

## Qualitative findings

- ProDiMo proto-planetary models give CO fluxes far below those observed  
  > "the absolute values of the line flux are too small compared to those observed." (Correlations)

## Claim tuples

- H: CO is common around young A-star debris hosts | E: JCMT CO 2-1 of HD 32297 plus census of 27 hosts within 125 pc | R: CO detected in HD 32297; 7/16 detections at 5-50 Myr, 0/11 older | F: Carbon-bearing gas appears in nearly half of A-star debris systems up to 50 Myr | **supported**
- H: CO is more asymmetric than dust owing to short lifetime | E: Compared blue/red line asymmetry with dust asymmetry | R: Only beta Pic clearly, 49 Cet tentatively | F: Only limited support | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Evolved proto-planetary disc origin for CO disfavoured by ProDiMo  
  > "This supports the hypothesis that these are *not* simply evolved proto-planetary discs" (Correlations)
- How they decided it was enough: _not stated_
- Limitation (authors): Few data points and eclectic asymmetry data  
  > "The available data are rather eclectic" (Asymmetries)
- Caveat (inferred, ours): ALMA is minor; main new data are JCMT
- Caveat (inferred, ours): Asymmetry significance low (2.5 sigma)
- Caveat (inferred, ours): Baseline choice changes detection significance

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: JCMT raw data reduction parameters
- Missing: ProDiMo inputs
- Missing: archival ALMA beta Pic project
- Data volume (inferred): small (<10 GB, JCMT data)
- Score (inferred): 2/5, ALMA minor, recipe sparse.
- Rediscovery candidate: no, Main data are JCMT and recipe is incomplete.

## Links

- Method: Panić et al. (2013) (SONS survey and observing procedures)
- Companion: Moór et al. (2015) (CO survey of debris discs)
- Related: SONS (SCUBA-2 Survey of Nearby Stars)

## Checks

```json
{
 "quotes": 32,
 "quotes_ok": 32,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00142.S",
  "2012.1.00195.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 22,
  "rate": 0.31
 },
 "evidence_ok": true
}
```
