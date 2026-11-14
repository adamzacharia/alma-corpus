# ALMA observations of PSR B1259-63/LS 2883 in an inactive period: Variable circumstellar disk?

`2020PASJ...72L...9F` | Publications of the Astronomical Society of Japan 2020 | first author: Fujita, Yutaka | arXiv: 2005.00017 | DOI: 10.1093/pasj/psaa067

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: stellar_physics, star_formation
- Question: Do the 97 GHz and 343 GHz fluxes of PSR B1259-63/LS 2883 change between just after the 2017 periastron and the apastron period, and what does this imply about the origin of the emission and the circumstellar disk?  
  > "If the 97 GHz flux is associated with that emission, it should significantly decrease or disappear accordingly." (Introduction); "if the 343 GHz emission actually comes from the disk, changes of the flux implies a long-term variability of the disk." (Introduction)
- Target **PSR B1259-63/LS 2883**: coordinates _not stated_; z/distance 2.6 (+0.4/-0.3) kpc  
  > "The distance to the system is $2.6^{+0.4}_{-0.3}$ kpc (cite: 2018MNRAS.479.4849M)." (Introduction); distance from Miller-Jones et al. 2018 (cite: 2018MNRAS.479.4849M)  
  > "The distance to the system is $2.6^{+0.4}_{-0.3}$ kpc (cite: 2018MNRAS.479.4849M)." (Introduction)

## Data provenance

- ALMA projects: 2019.1.00320.S, 2017.1.01188.S
- bands: Band 3 (97 GHz) and Band 7 (343 GHz)  
  > "The observations were carried out in ALMA Band 3 and Band 7 in 2019 November." (2 Observations and Results)
- frequencies and spectral setup: Time Division Mode (TDM) centered at 97 GHz and 343 GHz  
  > "The data were taken in Time Division Mode (TDM) centered at the frequency of 97 GHz and 343 GHz at Band 3 and Band 7, respectively." (2 Observations and Results)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2019 November; Band 7 on Nov. 7 and Nov. 27  
  > "the second observation in Band 7 (Nov. 27) was at most 1.5 times larger than that for the first observation (Nov. 7)" (2 Observations and Results)
- pi or archival as stated: _not stated_
- Other facility **ATCA**: Low-frequency unpulsed and pulsed fluxes at the 2004 periastron passage, used for comparison  
  > "we compared our 2017 observations with ATCA observations at low-frequencies at the 2004 periastron passage" (3.1 Comparison with 2017 observations)
- External data: Averaged pulsed ATCA fluxes between t_p-21.5 d and t_p+186.1 d at the 2004 periastron  
  > "red open triangles are the averaged pulsed fluxes obtained with ATCA during the period between $t_p - 21.5$ d and $t_p + 186.1$ d at the 2004 periastron passage" (3.2 Origin of the radio emissions) [from Johnston et al. 2005 (cite: 2005MNRAS.358.1069J)]
- External data: Theoretical disk spectra model  
  > "we show the disk spectra predicted by (cite: 2011MNRAS.412.1721V) up to the optical band." (3.1 Comparison with 2017 observations) [from van Soelen & Meintjes 2011 (cite: 2011MNRAS.412.1721V)]

## Processing

### Calibration

- pipeline or manual: ALMA Pipeline-CASA56-P1-B, standard manner  
  > "The data were processed using CASA 5.6.1-8 and ALMA Pipeline-CASA56-P1-B in a standard manner." (2 Observations and Results)
- casa version: CASA 5.6.1-8  
  > "The data were processed using CASA 5.6.1-8 and ALMA Pipeline-CASA56-P1-B in a standard manner." (2 Observations and Results)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Flux scaling derived on the bandpass calibrator using JAO flux information  
  > "Flux scaling was derived on the bandpass calibrator using the flux information provided by the Joint ALMA Observatory (JAO)." (2 Observations and Results)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean with multifrequency synthesis  
  > "The image deconvolution was done using the CASA task `tclean` with the multifrequency synthesis." (2 Observations and Results)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: uv-taper applied to second Band 7 observation to match the first beam  
  > "we applied uv-taper option to have a beam size similar to the first observation." (2 Observations and Results)
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

- 2017 ALMA observations and the disk-size interpretation (~30 R_*) come from Paper I  
  > "we estimated that the disk size is $\sim 30\: R_*$ in 2017" (3.1 Comparison with 2017 observations) [from Paper I (cite: 2019PASJ...71L...3F)]
- Assume R_* ~ 6 R_sun following van Soelen & Meintjes  
  > "Following (cite: 2011MNRAS.412.1721V), we here assume that $R_*\sim 6\: R_\odot$" (3.1 Comparison with 2017 observations) [from (cite: 2011MNRAS.412.1721V)]

### Not stated but needed to reproduce (our reading)

- tclean parameters: robust, cell size, image size, niter, threshold, mask
- uv-taper value
- imfit region and settings
- Flux scale uncertainty
- Table values of antennas, integration times, calibrators (not in text)
- Details of how spectral indices and their uncertainties were computed
- Disk model parameters used for the van Soelen & Meintjes spectra

## Analysis recipe

1. **Image the continuum**: tclean with multifrequency synthesis; uv-taper for second Band 7 data  
  > "The image deconvolution was done using the CASA task `tclean` with the multifrequency synthesis." (2 Observations and Results)
   - software: CASA
   - fitting: _not stated_
   - validation: Check source J1337-6509 compared to assess phase error  
  > "a similar level of shift and image distortion is seen in a calibrator J1337-6509, which was observed as the check source" (2 Observations and Results)
2. **Measure flux densities**: Gaussian fitting with imfit for integrated flux; peak intensity as lower limit for distorted image  
  > "we made Gaussian model fitting to the images using the CASA task `imfit` and measured the integrated flux density." (2 Observations and Results)
   - software: CASA imfit
   - fitting: 2D Gaussian  
  > "For the flux estimation, we made Gaussian model fitting to the images using the CASA task `imfit` and measured the integrated flux density." (Observations and Results)
   - validation: _not stated_
3. **Compare with models and low-frequency data to interpret emission**: Compute spectral indices; compare with disk model and ATCA unpulsed/pulsed fluxes  
  > "where the index is defined as $S_\nu\propto \nu^\alpha$." (3.1 Comparison with 2017 observations)
   - assumption: R_* ~ 6 R_sun; distance 2.6 kpc; 343 GHz flux as black-body disk radiation  
  > "Assuming that the the 343 GHz flux is the black-body radiation from the disk" (3.2 Origin of the radio emissions)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.6.1-8: Data processing, tclean imaging, imfit flux measurement  
  > "The data were processed using CASA 5.6.1-8 and ALMA Pipeline-CASA56-P1-B in a standard manner." (2 Observations and Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spectral index 97-343 GHz, 2017 | 0.7 | +0.2/-0.3 | dimensionless | 3 | $\alpha =0.7^{+0.2}_{-0.3}$ for the 2017 observations |
| Spectral index 97-343 GHz, 2019 | 1.4 | +0.2/-0.1 | dimensionless | 3 | $\alpha =
1.4^{+0.2}_{-0.1}$ for the 2019 observations |
| 97 GHz flux, 2019 | 0.19 | not stated | mJy | 2 | the flux of 0.19 mJy measured in 2019 ($t_p+771$ d in figure [3](#fig:radio)) |

## Qualitative findings

- Image is consistent with a point source; no sign of ejecta in radio  
  > "This means that in the radio band there is no sign of ejecta that had been observed in X-rays." (Conclusions)

## Claim tuples

- H: Fluxes at 97 and 343 GHz vary between 2017 and apastron 2019 | E: New ALMA Band 3/7 observations compared with 2017 data | R: Fluxes decreased by a factor of six at 97 GHz and two at 343 GHz | F: 97 GHz unpulsed synchrotron has disappeared; 343 GHz disk emission changed | **supported**
- H: The 2019 97 GHz flux is from the pulsar's pulsed emission | E: Compare with extrapolated ATCA pulsed fluxes | R: The 97 GHz flux lies on the pulsed-flux extrapolation | F: Consistent with pulsed emission, but pulses could not be tested | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Disk destruction/recovery would predict increased disk flux, contrary to observations  
  > "the flux from the disk in 2019 is expected to increase from that in 2017, which is opposite to our observational results." (3.2 Origin of the radio emissions)
- How they decided it was enough: _not stated_
- Limitation (authors): Second Band 7 observation affected by poor phase calibration and coherence loss, so excluded from discussion  
  > "Because of the poor phase calibration, the second observation data is likely affected by coherence loss." (2 Observations and Results)
- Limitation (authors): Pulses cannot be detected because of 2 s integration  
  > "we cannot uncover the pulse (47.76 ms) from the ALMA data, because they are integrated at every two seconds." (3.2 Origin of the radio emissions)
- Caveat (inferred, ours): Interpretation is speculative and lacks numerical simulation
- Caveat (inferred, ours): Few flux points; spectral index uncertainties large
- Caveat (inferred, ours): Extrapolations from 2004 ATCA data to 2019 assume orbital repeatability
- Caveat (inferred, ours): Only one usable Band 7 epoch in 2019

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Flux values (in tables not in text)
- Missing: Disk model details
- Data volume (inferred): ~10-50 GB raw for the 2019 data
- Score (inferred): 3/5, Archival codes and standard pipeline are given, but the imaging parameters and flux tables are missing, and the interpretation is model-based.
- Rediscovery candidate: no, Key flux numbers are not in the text and imaging settings are missing.

## Links

- Companion: Fujita et al. 2019 (cite: 2019PASJ...71L...3F) (Paper I: 2017 ALMA observations of the same system)

## Checks

```json
{
 "quotes": 36,
 "quotes_ok": 36,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 63,
  "stated": 27,
  "rate": 0.429
 },
 "evidence_ok": true
}
```
