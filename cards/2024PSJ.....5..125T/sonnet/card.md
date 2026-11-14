# Observations of Titan's Stratosphere during Northern Summer: Temperatures, CH<SUB>3</SUB>CN and CH<SUB>3</SUB>D Abundances

`2024PSJ.....5..125T` | The Planetary Science Journal 2024 | first author: Thelen, Alexander E. | arXiv: 2405.02535 | DOI: 10.3847/PSJ/ad47bd

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: How do Titan's stratospheric temperatures, CH3CN and CH3D (and inferred CH4) abundances vary with latitude in northern summer/early fall (2022), compared with earlier epochs?  
  > "stratospheric measurements remain sparse during Titan’s northern summer and fall." (abstract)
- Target **Titan**: coordinates _not stated_; z/distance angular size ~1.0 arcsec at time of observation  
  > "Compared to Titan’s angular size of $\sim1.0''$ (including its 2575 km solid-body radius and atmosphere up to 1200 km) during the time of observation" (2 Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2021.1.01388.S
- bands: Band 9 (602-720 GHz; ~0.4-0.5 mm)  
  > "Titan was observed by 44–48 antennas on 2022 June 18 and 29 in ALMA Band 9 ($602-720$ GHz; $\sim0.4-0.5$ mm)" (2 Observations)
- frequencies and spectral setup: Spectral resolutions 488 kHz (HCN), 977 kHz (CH3CN, CH3D), 1129 kHz (CO, continuum window)  
  > "The targeted spectral windows were set to resolutions of 488 kHz (HCN), 977 kHz (CH$_3$CN, CH$_3$D), and 1129 kHz (CO, continuum window)." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m array, 44-48 antennas  
  > "Titan was observed by 44–48 antennas on 2022 June 18 and 29" (2 Observations)
- configurations: C-5, max separation ~1.4 km  
  > "which was set to configuration C-5, with maximum antenna separations of up to $\sim1.4$ km." (2 Observations)
- baselines: _not stated_
- angular resolution: 0.172 x 0.148 arcsec, PA 71.49 deg (~1000 km on Titan)  
  > "resulting in a final angular resolution (represented by the ALMA beam) of $0.172\times0.148''$ ($\sim1000$ km on Titan at the time of observation) with a position angle of $71.49^\circ$." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2022 June 18 and 29  
  > "Titan was observed by 44–48 antennas on 2022 June 18 and 29 in ALMA Band 9" (2 Observations)
- pi or archival as stated: _not stated_
- Line: CO 6-5 (691.473 GHz)
- Line: CH3D 3_2-2_2, 3_1-2_1, 3_0-2_0 (697.691, 697.759, 697.781 GHz)
- Line: CH3CN 38_K-37_K, K=0-9 (697.209-698.281 GHz)
- Line: HCN 8-7 (not stated)
- External data: Disk-averaged stratospheric temperature profile from 2019 ALMA, used as initial/prior  
  > "These models were initialized using the stratospheric temperature profile retrieved from recent, unresolved ALMA observations of Titan in 2019 (cite: thelen_20)" (3 Radiative Transfer Modeling) [from (cite: thelen_20)]
- External data: Tropospheric temperature profiles from Cassini Radio Science  
  > "tropospheric temperature profiles (which are not expected to show significant seasonal variability) from Cassini Radio Science measurements (cite: schinder_20)" (3 Radiative Transfer Modeling) [from (cite: schinder_20)]
- External data: Huygens/GCMS vertical profiles of gases; CH4 = 1.48% stratosphere  
  > "The *a priori* CH$_3$D profile was generated from the constant stratospheric measurement of CH$_4=1.48\%$ from the Huygens/GCMS (cite: niemann_10)" (3 Radiative Transfer Modeling) [from (cite: niemann_10)]
- External data: D/H = 1.2e-4 weighted average from ALMA and Cassini/CIRS  
  > "the D/H from the weighted average of measurements from ALMA and Cassini/CIRS of $1.2\times10^{-4}$" (3 Radiative Transfer Modeling) [from (cite: thelen_19b), (cite: nixon_12)]
- External data: N2-broadening parameters for CH3CN  
  > "The N$_2$-broadening parameters for CH$_3$CN were taken from (cite: dudaryonok_15b)" (3 Radiative Transfer Modeling) [from (cite: dudaryonok_15b)]
- External data: A priori CH3CN profile from Marten 2002 observations and Loison 2015 photochemistry above ~400 km  
  > "starting with a combination of abundance profiles from observations by (cite: marten_02) and photochemical predictions by (cite: loison_15) above $\sim400$ km" (3 Radiative Transfer Modeling) [from (cite: marten_02); (cite: loison_15)]

## Processing

### Calibration

- pipeline or manual: Standard JAO pipeline, plus iterative self-calibration  
  > "While the ALMA data were reduced with the standard pipeline procedures provided by the Joint ALMA Observatory in the Common Astronomy Software Applications" (2 Observations)
- casa version: CASA 6.2  
  > "(CASA; (cite: jaeger_08)) ver. 6.2" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: up to 20% at high frequencies; fitted scaling factors 0.85-1.15 per spectral window  
  > "ALMA flux calibration uncertainties at high frequencies can be as high as $20\%$" (3 Radiative Transfer Modeling); "The spectral scaling factors were found to be between 0.85–1.15 for each spectral window." (3 Radiative Transfer Modeling)
- self calibration: Phase-only self-cal on combined continuum image (CH3CN spw + ~712 GHz spw), successively smaller solution intervals until phase scatter ~±10%; applied to line data  
  > "we solved for phase solutions as a function of time on this continuum image with successively smaller solution intervals until phase scatter due to noisy antenna baselines were sufficiently minimized" (2 Observations)

### Imaging

- task: CASA tclean  
  > "This round of imaging was performed using the CASA `tclean` task with the Högbom algorithm, natural antenna weighting, and $0.01''$ square pixels" (2 Observations)
- deconvolver: Högbom  
  > "CASA `tclean` task with the Högbom algorithm" (2 Observations)
- weighting robust: natural weighting  
  > "natural antenna weighting" (2 Observations)
- uv taper: _not stated_
- cell size: 0.01 arcsec  
  > "$0.01''$ square pixels" (2 Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: strong line channels flagged for continuum; concatenated with multi-frequency synthesis  
  > "We flagged out all strong spectral line channels from atmospheric trace species and then concatenated the remaining averaged continuum channels using the multi-frequency synthesis settings" (2 Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.172 x 0.148 arcsec, PA 71.49 deg  
  > "$0.172\times0.148''$ ($\sim1000$ km on Titan at the time of observation) with a position angle of $71.49^\circ$" (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Self-calibration and imaging procedure similar to that for Galilean satellites and giant planets  
  > "executed similarly to those used for the Galilean Satellites and Giant Planets (cite: de_pater_19; de_kleer_21a; camarca_23; thelen_24a)" (2 Observations) [from (cite: de_pater_19; de_kleer_21a; camarca_23; thelen_24a)]
- Construction of emission angles representing ALMA beam shape  
  > "see (cite: thelen_18) for additional details on the construction of emission angles to represent the ALMA beam shape." (3 Radiative Transfer Modeling) [from (cite: thelen_18)]
- Collision-induced absorption parameterization as in previous Titan studies  
  > "Collisionally-induced absorption of N$_2$, CH$_4$, and H$_2$ pairs were parameterized as in previous studies of Titan with ALMA and Cassini/CIRS" (3 Radiative Transfer Modeling) [from (cite: borysow_86a; borysow_86b; borysow_86c; borysow_87; borysow_91; borysow_93)]
- CH3CN a priori profile construction as in previous ALMA observations  
  > "as was done with previous ALMA observations (cite: thelen_19a)" (3 Radiative Transfer Modeling) [from (cite: thelen_19a)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals and number of iterations
- Flux and bandpass calibrator names
- Number of clean iterations/threshold and masks
- Which channels were flagged as line-free for continuum
- Exact spectral extraction regions' coordinates and latitude-bin centers
- NEMESIS version, a priori covariance/errors, and temperature a priori errors
- How the Titan limb-darkened starting model temperature was set
- Exact D/H uncertainty handling for the weighted average

## Analysis recipe

1. **Self-calibrate and image**: Phase-only self-cal on combined continuum image with disk starting model; apply solutions to line data; tclean to make cube  
  > "Once the continuum phase distribution was on order $\pm10\%$, we applied these phase solutions to the full calibrated spectral line data and performed further image deconvolution" (2 Observations)
   - software: CASA
   - parameter: Hogbom, natural weighting, 0.01 arcsec pixels  
  > "the Högbom algorithm, natural antenna weighting, and $0.01''$ square pixels" (2 Observations)
   - assumption: Flat or limb-darkened disk starting model at Titan's Band 9 brightness temperature  
  > "Using a starting model of a flat or limb-darkened disk at the appropriate brightness temperature of Titan’s Band 9 continuum" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract latitudinal spectra**: Spectra extracted in ~20 deg latitude bins, averaged over surrounding 5x5 pixel grid  
  > "approximate $20^{\circ}$ latitude bins, which were averaged with the surrounding $5\times5$ pixel grid such as to improve the spectral S/N" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Determine flux scaling factors**: NEMESIS forward models of continuum-only spectral regions to derive multiplicative scaling per spectral window  
  > "NEMESIS forward models were generated for spectral regions containing only continuum emission (formed from the above absorption pairs and thermal radiation) to determine constant, multiplicative scaling factors" (3 Radiative Transfer Modeling)
   - software: NEMESIS
   - parameter: 30 line-of-sight emission angles per extraction; Doppler wavenumber offsets ~1e-5 cm-1  
  > "30 line-of-sight emission angles were calculated for each individual spectrum extraction location" (3 Radiative Transfer Modeling)
   - fitting: _not stated_
   - validation: _not stated_
4. **Retrieve temperature profiles**: NEMESIS optimal-estimation retrieval of temperature vs altitude from CO 6-5 per latitude bin  
  > "The temperature profiles between the stratosphere and mesosphere were then retrieved using the CO ($J=6$–5) emission line." (3 Radiative Transfer Modeling)
   - software: NEMESIS
   - parameter: Correlation length 1.5 scale heights; profiles varied above ~100 km up to 1200 km  
  > "The correlation length was taken to be 1.5 scale heights, and though the profiles were allowed to vary up to 1200 km" (3 Radiative Transfer Modeling)
   - assumption: CO abundance ~50 ppm held constant; tropospheric temperatures fixed to Cassini RS  
  > "a nominal CO abundance of $\sim50$ parts-per-million (ppm; $1\times10^{-6}$), as determined by a number of studies" (3 Radiative Transfer Modeling)
   - fitting: Levenberg-Marquardt minimizing cost function / reduced chi2  
  > "Atmospheric temperatures were varied iteratively with the NEMESIS retrieval algorithm (based on the Levenberg-Marquardt principle" (3 Radiative Transfer Modeling)
   - validation: Residual spectra inspected  
  > "Residual spectra show that the spectral lines are fit well using the methods described above." (3 Radiative Transfer Modeling)
5. **Retrieve CH3CN vertical profiles**: NEMESIS retrieval using strongest 5 CH3CN J=38-37 transitions with fixed temperatures  
  > "The strongest 5 spectral transitions of the CH$_3$CN ($J=38$–37) band were used to retrieve the vertical profile without interference from the nearby CH$_3$D ($J=3$–2) triplet" (3 Radiative Transfer Modeling)
   - software: NEMESIS
   - assumption: A priori from Marten 2002 and Loison 2015 profiles  
  > "starting with a combination of abundance profiles from observations by (cite: marten_02) and photochemical predictions by (cite: loison_15) above $\sim400$ km" (3 Radiative Transfer Modeling)
   - fitting: _not stated_
   - validation: _not stated_
6. **Retrieve CH3D abundance and convert to CH4**: Scale a priori CH3D profile, fit East and West hemisphere spectra simultaneously; convert to CH4 via D/H  
  > "we performed retrievals on spectra from the East and West hemispheres simultaneously to better constrain the CH$_3$D abundance." (3 Radiative Transfer Modeling)
   - software: NEMESIS
   - assumption: D/H = 1.2e-4 (range 1.0-1.4e-4); a priori CH4 = 1.48%  
  > "which range from $\sim(1.0-1.4)\times10^{-4}$ as derived and discussed in (cite: nixon_12) and (cite: thelen_19b)" (4.3 CH3D Abundances)
   - fitting: Simple scaling of input profile  
  > "These models were parameterized as a simple scaling of the input profile" (3 Radiative Transfer Modeling)
   - validation: CH3CN lines nearby fit well  
  > "Nearby CH$_3$CN lines were included in the model, and were fit well by the input profiles from the previous retrievals." (3 Radiative Transfer Modeling)

## Software

- **CASA** 6.2: Pipeline calibration, self-calibration, tclean imaging  
  > "(CASA; (cite: jaeger_08)) ver. 6.2" (2 Observations)
- **NEMESIS** : Radiative transfer and retrievals  
  > "radiative transfer package NEMESIS: the Non-linear optimal Estimator for MultivariatE spectral analySIS" (3 Radiative Transfer Modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3D abundance range | 4-8 | not stated | ppm | 6 | The range of measurements, $\sim4-8$ ppm |
| Weighted average CH3D | 5.54e-6 | 0.10e-6 | dimensionless (mixing ratio) | 6 | the weighted average of all latitudes is $(5.54\pm0.10)\times10^{-6}$ |
| Global weighted average CH4 | 1.15 | ±0.02 (stat); +0.21/-0.15 including D/H range | % | 6 | The converted weighted average CH$_4$ abundance = $1.15\pm0.02\%$; global weighted average of $1.15^{+0.21}_{-0.15}\%$ |
| Highest southern stratopause temperature | 190 K at 320-350 km (>77S) | not stated | K | 4 | exhibits the highest and warmest stratopause at 190 K between 320–350 km |
| CH3CN enhancement 77S vs equator | ~1.5 | not stated | dimensionless | 5 | We measure an enhancement factor of $\sim1.5$ when comparing the profiles retrieved from spectra at $\sim77^{\circ}$S |
| Northern CH3CN decrease since 2015 | ~16 | not stated | factor | 5 | we see a decrease in northern abundances by a factor of $\sim16$ over roughly a Titan season (7 yr) |
| Flux scaling factors | 0.85-1.15 | not stated | dimensionless | 3 | The spectral scaling factors were found to be between 0.85–1.15 for each spectral window. |

## Qualitative findings

- 2022 stratospheric temperature structure mirrors northern-winter Cassini structure, with warm southern stratopause  
  > "increasing temperatures towards high-southern latitudes, currently in winter, resemble those observed during Titan’s northern winter by the Cassini mission." (abstract)

## Claim tuples

- H: Titan's temperature field in northern summer mirrors the Cassini-era northern winter | E: Retrieve T profiles from CO 6-5 in latitude bins | R: Warm northern stratosphere, elevated warm southern stratopause (190 K) | F: Distribution mirrors northern winter and agrees with circulation models | **supported**
- H: CH3CN distribution tracks circulation | E: Retrieve CH3CN vertical profiles by latitude; compare with 2015 ALMA | R: Southern enhancement 1.5-5x; northern depletion up to 16x since 2015 | F: Long-lived species concentrate at winter pole | **supported**
- H: Stratospheric CH4 is uniform at the Huygens value | E: Convert CH3D to CH4 using D/H | R: CH4 0.8-1.9%, global 1.15% | F: CH4 is variable and lower than the Huygens value; interpretation limited by D/H uncertainty | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Low S/N of CH3D prevents vertical profile; CH4 inference relies on prior D/H; beam smooths latitudinal structure  
  > "Currently, the relatively low S/N CH$_3$D emission also prohibits the retrieval of a vertical profile" (4.3 CH3D Abundances)
- Caveat (inferred, ours): CH4 conversion depends on assumed D/H and a priori profile
- Caveat (inferred, ours): Flux scaling factors absorb systematic errors
- Caveat (inferred, ours): Latitude bins ~20 deg vs beam smoothing
- Caveat (inferred, ours): No stated retrieval error covariance/priors

## Reproducibility

- Data public (paper): ALMA project 2021.1.01388.S cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2021.1.01388.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: NEMESIS publicly available online  
  > "NEMESIS is publicly available online" (3 Radiative Transfer Modeling)
- Missing: Self-cal parameters
- Missing: NEMESIS setup (priors, errors, versions)
- Missing: Extraction region coordinates
- Missing: Calibrator information
- Data volume (inferred): ~50-150 GB raw (two Band 9 executions)
- Score (inferred): 4/5, Data identified and methods described at a high level, but self-cal and retrieval priors lack detail.
- Rediscovery candidate: no, Recipe lacks detail on self-calibration and retrieval setup; results depend on external priors.

## Links

- Method: (cite: irwin_08) (NEMESIS retrieval code)
- Method: (cite: thelen_18) (ALMA beam emission angle construction)
- Method: (cite: thelen_19a) (Previous ALMA CH3CN retrieval approach)
- Companion: (cite: thelen_20) (2019 disk-averaged temperature profile used as prior)
- Companion: (cite: thelen_19b) (Prior CH3D/D-H measurement with ALMA)
- Related: Cassini CIRS/VIMS
- Related: Huygens GCMS/DISR

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 51,
  "rate": 0.614
 },
 "evidence_ok": true
}
```
