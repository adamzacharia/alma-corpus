# ALMA Observations of the Gamma-Ray Binary System PSR B1259-63/LS 2883 during the 2024 Periastron Passage

`2024ApJ...977L..22F` | The Astrophysical Journal Letters 2024 | first author: Fujita, Yutaka | arXiv: 2411.11950 | DOI: 10.3847/2041-8213/ad93d1

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: stellar_physics, other
- Question: How the millimeter/submillimeter flux of the gamma-ray binary B1259 changes around the 2024 periastron passage, and what this implies for the pulsar wind and the circumstellar disk  
  > "These observations were aimed at capturing for the first time the behavior of the system around the periastron passage." (Introduction); "We discuss the implications of these results for the interaction between the pulsar wind and the circumstellar disk, such as the possible disk expansion after periastron." (abstract)
- Target **PSR B1259-63/LS 2883 (B1259)**: coordinates _not stated_; z/distance ~2.6 kpc  
  > "B1259 is located at a distance of $\sim 2.6$ kpc from Earth" (Introduction); distance from Miller-Jones et al. 2018 (cite: 2018MNRAS.479.4849M)  
  > "B1259 is located at a distance of $\sim 2.6$ kpc from Earth" (Introduction)

## Data provenance

- ALMA projects: 2017.1.01188.S, 2019.1.00320.S, 2023.1.00271.S
- bands: Band 3 (97 GHz), Band 6 (233 GHz), Band 7 (343 GHz)  
  > "The observations were made in Band 3 (97 GHz), Band 6 (233 GHz), and Band 7 (343 GHz)." (Observations and Data Reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam sizes from ~0.2'' to 2'' depending on band and array configuration  
  > "The ALMA observations used ranged from 41 to 45 antennas, providing beam sizes from $\sim 0.2''$ to $2''$ depending on the frequency band and array configuration" (Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 5 to 6 minutes per observation  
  > "The total on-source integration time for each observation ranged from 5 to 6 minutes." (Observations and Data Reduction)
- observing dates: Epochs from -61 to +29 days from the 2024 periastron (June 30)  
  > "Our new data were obtained over several epochs, ranging from -61 to +29 days from the periastron passage in 2024." (abstract); "We performed observations of B1259 with ALMA around the 2024 periastron passage (June 30)." (Observations and Data Reduction)
- pi or archival as stated: _not stated_
- External data: Distance of ~2.6 kpc  
  > "B1259 is located at a distance of $\sim 2.6$ kpc from Earth" (Introduction) [from (cite: 2018MNRAS.479.4849M)]
- External data: Orbital period of about 3.4 years, eccentricity 0.87  
  > "has an orbital period of about 3.4 years, with an eccentricity of 0.87" (Introduction) [from (cite: 2014MNRAS.437.3255S)]
- External data: 2017 (Paper I) and 2019 (Paper II) ALMA fluxes, plotted in Figure 1 for reference  
  > "For reference, we show the results of our 2017 (Paper I) and 2019 (Paper II) observations" (Results) [from Paper I (cite: 2019PASJ...71L...3F); Paper II (cite: 2020PASJ...72L...9F)]
- External data: Thermal disk emission model used to estimate disk size (~20-30 R_star before periastron, ~40 R_star after)  
  > "In fact, a comparison with the thermal emission model of" (Discussion) [from (cite: 2011MNRAS.412.1721V)]
- External data: H-alpha equivalent width behaviour after periastron (~30% increase, peak at t_p ~ +10 to +20 days)  
  > "the H$\alpha$ equivalent width of B1259 also has a large ($\sim 30$%) post-periastron increase" (Discussion) [from (cite: 2021Univ....7..242C; 2024arXiv241102128C)]
- External data: Near-infrared brightening of at most ~0.1 mag (~10%) around periastron  
  > "but the resulting brightening is only $\lesssim 0.1$ mag ($\lesssim 10$%)" (Discussion) [from (cite: 2021PASJ...73..545K)]
- Simulation/model as data: Thermal emission model of the circumstellar disk (van Soelen & Meintjes 2011) compared to the SEDs  
  > "In fact, a comparison with the thermal emission model of" (Discussion)

## Processing

### Calibration

- pipeline or manual: ALMA Pipeline, standard manner  
  > "ALMA Pipeline version 2023.1.0.124 in a standard manner" (Observations and Data Reduction)
- casa version: CASA 6.5.4.9  
  > "Common Astronomy Software Applications (CASA) package version 6.5.4.9" (Observations and Data Reduction)
- pipeline version: ALMA Pipeline 2023.1.0.124  
  > "ALMA Pipeline version 2023.1.0.124 in a standard manner" (Observations and Data Reduction)
- archive products used as is: _not stated_
- flux calibrator: Flux scale set on the bandpass calibrator with flux information from JAO (calibrator names in Table 1)  
  > "The flux scaling was derived on the bandpass calibrator using flux information provided by the Joint ALMA Observatory (JAO)." (Observations and Data Reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN algorithm within CASA, image per observation  
  > "After calibration, we created images for each observation using the CLEAN algorithm within CASA." (Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: Briggs weighting, robust = 0.5  
  > "We employed Briggs weighting with a robust parameter of 0.5, balancing between sensitivity and resolution." (Observations and Data Reduction)
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
- final beam: Beam sizes ~0.2'' to 2'' depending on band and configuration (per-epoch values in Table 1)  
  > "providing beam sizes from $\sim 0.2''$ to $2''$ depending on the frequency band and array configuration" (Observations and Data Reduction)
- final rms: _not stated_

### Inherited from earlier work

- Interpretation of Band 7 (and Band 6) emission as thermal emission from the circumstellar disk  
  > "The most plausible explanation is that this emission is thermal (blackbody and/or bremsstrahlung) and comes from the circumstellar disk (Paper I)." (Introduction) [from Paper I (cite: 2019PASJ...71L...3F)]
- Interpretation of near-periastron emission as unpulsed synchrotron from electrons accelerated in the stellar wind and/or disk  
  > "This suggests the emergence of unpulsed synchrotron emission from electrons accelerated as the pulsar passes through the stellar wind and/or circumstellar disk (Papers I and II)." (Results) [from Papers I and II (cite: 2019PASJ...71L...3F; 2020PASJ...72L...9F)]

### Not stated but needed to reproduce (our reading)

- Target coordinates / phase centre and calibrator coordinates
- Which ALMA project code and execution blocks correspond to each epoch in Table 1
- How the source flux and its uncertainty were measured (point-source fit, peak pixel or aperture) and whether the uncertainty includes absolute flux scale error
- CLEAN parameters other than robust (task, niter, threshold, masking, cell size, image size, deconvolver)
- Whether the archive pipeline products were used as is or the data were re-imaged by the authors
- Flux density values and models adopted for the bandpass/flux calibrators
- Spectral windows and continuum channel selection used for imaging
- Parameters of the thermal disk model comparison and of the synchrotron/pulsed spectral lines drawn in Figure 2 (normalisation, indices, disk temperature and density)
- Primary beam correction and any flux correction for resolved-out emission (not stated)

## Analysis recipe

1. **Calibrate the ALMA observations**: Standard ALMA Pipeline calibration in CASA; flux scale from the bandpass calibrator using JAO flux information  
  > "ALMA Pipeline version 2023.1.0.124 in a standard manner" (Observations and Data Reduction); "The flux scaling was derived on the bandpass calibrator using flux information provided by the Joint ALMA Observatory (JAO)." (Observations and Data Reduction)
   - software: CASA, ALMA Pipeline
   - parameter: CASA 6.5.4.9; ALMA Pipeline 2023.1.0.124  
  > "Common Astronomy Software Applications (CASA) package version 6.5.4.9" (Observations and Data Reduction); "ALMA Pipeline version 2023.1.0.124 in a standard manner" (Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Image each observation**: CLEAN imaging per observation with Briggs weighting  
  > "After calibration, we created images for each observation using the CLEAN algorithm within CASA." (Observations and Data Reduction)
   - software: CASA
   - parameter: Briggs weighting, robust = 0.5  
  > "We employed Briggs weighting with a robust parameter of 0.5, balancing between sensitivity and resolution." (Observations and Data Reduction)
   - assumption: Source is unresolved; image size consistent with a point source, upper limit given by beam sizes  
  > "The image size of B1259 is consistent with a point source and the upper limit is given by the beam sizes." (Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure fluxes and build light curves**: Flux of the point source measured for each band and epoch and plotted versus time from periastron, together with the 2017 and 2019 data  
  > "Our ALMA observations of B1259 reveal significant variability in the millimeter and submillimeter emission across different orbital phases and frequency bands." (Light Curves); "For reference, we show the results of our 2017 (Paper I) and 2019 (Paper II) observations" (Light Curves)
   - fitting: _not stated_
   - validation: _not stated_
4. **Construct SEDs at four orbital phases and derive spectral indices**: SEDs built at early approach, mid-approach, near-periastron and post-periastron; spectral index defined as S_nu proportional to nu^alpha and compared with pulsed, unpulsed synchrotron (alpha ~ -0.75) and thermal disk components  
  > "we constructed spectral energy distributions (SEDs) for the system at different orbital phases" (Spectral Energy Distributions); "where the index is defined as $S_\nu \propto \nu^{\alpha}$" (Light Curves); "typical unpulsed synchrotron emission ($\alpha\sim -0.75$" (Spectral Energy Distributions)
   - fitting: _not stated_
   - validation: _not stated_
5. **Estimate disk size from thermal disk emission model**: Comparison of the SEDs with a published thermal emission model of the circumstellar disk  
  > "In fact, a comparison with the thermal emission model of" (Discussion)
   - assumption: Band 6 and 7 emission before and after periastron is thermal disk emission  
  > "reveal a significant contribution from thermal emission from the companion" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.5.4.9: Data processing and CLEAN imaging  
  > "Common Astronomy Software Applications (CASA) package version 6.5.4.9" (Observations and Data Reduction); "After calibration, we created images for each observation using the CLEAN algorithm within CASA." (Observations and Data Reduction)
- **ALMA Pipeline** 2023.1.0.124: Standard calibration of the data  
  > "ALMA Pipeline version 2023.1.0.124 in a standard manner" (Observations and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band 3 (97 GHz) flux at t_p = -1 day (peak) | 3.17 | 0.20 | mJy | 3 | emission peaking at $3.17\pm 0.20$ mJy at $t_p= -1$ days |
| Band 3 (97 GHz) flux at t_p = +29 days | 1.34 | 0.10 | mJy | 3 | measuring $1.34\pm 0.10$ mJy |
| Band 6 (233 GHz) flux at t_p = -1 day | 2.48 | 0.23 | mJy | 3 | the flux near periastron ($2.48 \pm 0.23$ mJy) being only about 2.7 times higher than the initial measurement ($0.93 \pm 0.18$ mJy at $t_p=-61$ days) |
| Band 6 (233 GHz) flux at t_p = -61 days | 0.93 | 0.18 | mJy | 3 | the flux near periastron ($2.48 \pm 0.23$ mJy) being only about 2.7 times higher than the initial measurement ($0.93 \pm 0.18$ mJy at $t_p=-61$ days) |
| Band 6 (233 GHz) flux at t_p = +29 days | 1.89 | 0.15 | mJy | 3 | The post-periastron measurement at $t_p=+29$ days ($1.89 \pm 0.15$ mJy) |
| Band 7 (343 GHz) flux at t_p = +24 days | 3.11 | 0.54 | mJy | 3 | The post-periastron observation at $t_p =+24$ days shows a slight increase in flux to $3.11 \pm 0.54$ mJy. |
| Spectral index between Bands 3 and 6 near periastron | ~ -0.3 | not stated | dimensionless | 4 | the spectral index between Bands 3 and 6 is $\alpha\sim -0.3$ |
| Disk size well before periastron | ~20-30 | not stated | stellar radii (R_star) | 5 | the disk size is $\sim 20$–$30\: R_\star$, where $R_\star$ is the radius of the companion, well before periastron |
| Disk size at t_p ~ +24 to +29 days | ~40 | not stated | stellar radii (R_star) | 5 | while it is $\sim 40\: R_\star$ at $t_p\sim +24$–29 days |
| Change in Band 7 luminosity after periastron | about 200% | not stated | percent | 3 | the change in luminosity at Band 7 was about 200% |

## Qualitative findings

- Band 3 flux rises about tenfold toward periastron, consistent with synchrotron emission from shock-accelerated electrons  
  > "This is a tenfold increase from pre-periastron levels." (Light Curves); "consistent with synchrotron radiation from shock-accelerated electrons in the pulsar-stellar wind interaction" (Conclusions)
- Band 6 and 7 spectra rise with frequency away from periastron, indicating thermal emission from the circumstellar disk; synchrotron dominates Band 6 only near t_p ~ -1 day  
  > "the synchrotron emission becomes dominant at periastron ($t_p\sim -1$ days), whereas the thermal emission is the dominant emission mechanism at other phases" (Conclusions)
- Band 7 brightening after periastron suggests the disk survives the pulsar passage and may have expanded  
  > "The post-periastron brightening in Band 7 (343 GHz) indicates the resilience of the circumstellar disk and possible expansion of the disk." (Conclusions)

## Claim tuples

- H: Does the Band 3 emission near periastron come from synchrotron emission produced by the pulsar-wind interaction? | E: Band 3 (97 GHz) observations at t_p = -61, -28, -1 and +29 days | R: Flux rises from low early values to 3.17 +/- 0.20 mJy at t_p = -1 day, then falls to 1.34 +/- 0.10 mJy at +29 days | F: The Band 3 emission near periastron is synchrotron from relativistic electrons accelerated in the pulsar wind and stellar wind or disk interaction | **supported**
- H: Does the dominant mechanism at Band 6 change between thermal disk emission and synchrotron around periastron? | E: Band 6 (233 GHz) observations at -61, -31, -1 and +29 days and SEDs against Band 3 and Band 7 | R: Spectrum inverts between Bands 3 and 6 near periastron with alpha ~ -0.3, less steep than typical synchrotron (-0.75); Band 6 decays more slowly after periastron | F: Synchrotron dominates at Band 6 near periastron, while thermal disk emission dominates at other phases, with possible disk contribution even at periastron | **partially**
- H: Is the circumstellar disk destroyed by the pulsar passage? | E: Band 7 (343 GHz) observations at -57 and +24 days compared with 2017 and 2019 Band 7 data and a thermal disk model | R: Band 7 flux at +24 days is 3.11 +/- 0.54 mJy, higher than before periastron; model disk size grows from ~20-30 R_star to ~40 R_star | F: The disk is not immediately destroyed and may have expanded, possibly through the pulsar wind pushing the disk outward | **supported**

## Reasoning

- Why this data: ALMA allows study of emission above ~100 GHz with excellent sensitivity, and earlier mm data only covered other orbital phases; new data target behaviour around periastron  
  > "The advent of the Atacama Large Millimeter/submillimeter Array (ALMA) allowed us to study the emission at higher frequencies ($\gtrsim 100$ GHz) with excellent sensitivity." (Introduction); "These observations were aimed at capturing for the first time the behavior of the system around the periastron passage." (Introduction)
- Why this method: _not stated_
- Alternative: Tidal interaction alone as the cause of the Band 7 post-periastron brightening was judged insufficient  
  > "However, even taking this into account, it would be difficult to explain the 2-fold brightening by tidal interactions alone." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Few ALMA epochs, so the double-peaked light curve seen at low frequencies cannot be tested  
  > "We note that since the number of our ALMA observations is small, the double peaks found in the light curves for the low frequency radio and X-ray bands" (Light Curves)
- Limitation (authors): Band 7 has few data points  
  > "despite fewer data points" (Light Curves)
- Limitation (authors): The flux at a given orbital phase can vary from one orbital period to the next  
  > "although the flux at a given $t_p$ can vary for each orbital period" (Light Curves)
- Caveat (inferred, ours): Only 1-2 epochs in Band 7 and at most four per band, so claims on disk expansion and the thermal-to-synchrotron transition rest on very few points
- Caveat (inferred, ours): Flux errors in Table 1 are not tied to a stated measurement method and absolute flux-scale uncertainty is not discussed
- Caveat (inferred, ours): Different array configurations give very different beams (0.11'' to 2''), and the paper does not discuss possible resolved-out disk emission or beam-dependent flux
- Caveat (inferred, ours): Disk size estimates from a literature thermal model are given without model parameters or fit quality
- Caveat (inferred, ours): Light curve comparison mixes different orbital cycles (2017, 2019, 2024), which the paper admits vary cycle to cycle

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Flux extraction method and error budget
- Missing: Full CLEAN parameters, spectral window selection and mask
- Missing: Target position, calibrator flux models, and mapping of project codes to epochs
- Missing: Parameters of the thermal disk model and of the synchrotron/pulsar components overplotted in the SEDs
- Data volume (inferred): About 10 short (5-6 min) observations in three bands; raw data likely a few to tens of GB, pipeline products smaller
- Score (inferred): 3/5, ALMA project codes and per-epoch fluxes are given, and calibration and robust are stated, but flux measurement, CLEAN details, target coordinates and the disk model are not specified
- Rediscovery candidate: no, Flux extraction and SED/disk-model recipe are underspecified, and the public status of the 2023.1.00271.S data is not stated in the paper

## Links

- Method: (cite: 2007ASPC..376..127M) (CASA reference cited for data processing)
- Companion: Paper I (cite: 2019PASJ...71L...3F) (2017 ALMA Band 3 and 7 observations of B1259 at t_p = +69 to +84 days)
- Companion: Paper II (cite: 2020PASJ...72L...9F) (2019 ALMA observations near apastron (t_p ~ +771 to +776 days))
- Companion: (cite: 2021Univ....7..242C) (Compilation of multi-wavelength light curves of B1259 used for comparison)
- Related: 2017.1.01188.S
- Related: 2019.1.00320.S
- Related: 2023.1.00271.S

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 42,
  "rate": 0.525
 },
 "evidence_ok": true
}
```
