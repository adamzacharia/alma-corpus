# Monitoring of 3C 286 with ALMA, IRAM, and SMA from 2006 to 2025: Stability, Synchrotron Ages, and Frequency-dependent Polarization Attributed to Core-shift

`2025ApJ...994..196K` | The Astrophysical Journal 2025 | first author: Kam, Minchul | arXiv: 2510.05540 | DOI: 10.3847/1538-4357/ae10b1

Card schema 1.0 | model claude-haiku-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars
- Question: Is the total flux, fractional polarization and EVPA of 3C 286 stable from 2006 to 2025 across ALMA, IRAM 30-m and SMA, and what causes the frequency-dependent EVPA and polarization?  
  > "The polarization properties of 3C 286 are stable across all observing frequencies." (abstract); "This trend is consistent with the core-shift effect expected in a conical jet." (abstract)
- Target **3C 286**: coordinates _not stated_; z/distance z=0.849  
  > "3C 286 is a quasar (z=0.849; (cite: burbidge69))" (Introduction); "obtained from the Type Ia supernovae in the local universe (cite: riess22)" (Introduction); "At a redshift of z=0.849, this leads to a linear scale of 1 mas = 7.23 pc." (Introduction); distance from redshift from burbidge69; cosmology H0 and q0 from riess22 (cite: riess22)  
  > "3C 286 is a quasar (z=0.849; (cite: burbidge69))" (Introduction); "obtained from the Type Ia supernovae in the local universe (cite: riess22)" (Introduction); "At a redshift of z=0.849, this leads to a linear scale of 1 mas = 7.23 pc." (Introduction)

## Data provenance

- ALMA projects: 2011.0.00001.CAL
- bands: ALMA Band 3 (91.5 and 103.5 GHz), Band 6 (233.0 GHz), Band 7 (343.4 GHz); IRAM 86 and 229 GHz; SMA 225 GHz  
  > "The data has been primarily obtained in Band 3 (91.5 and 103.5 GHz) and Band 7 (343.4 GHz) since May 2018." (Data, ALMA); "Data in Band 6 (233.0 GHz) has been obtained less frequently as a complement to the Band 7 data (cite: remijan19)." (Data, ALMA)
- frequencies and spectral setup: SMA LSB and USB centred about 20 GHz apart at 225 GHz, each sideband 12 GHz in six 2 GHz chunks; ALMA and IRAM frequencies as listed above  
  > "The separation between the center frequencies of the lower sideband (LSB) and upper sideband (USB) was set to about 20 GHz, centered at 225 GHz." (Data, SMA); "The bandwidth of each sideband is 12 GHz, consisting of six chunks with a bandwidth of 2 GHz." (Data, SMA)
- continuum bandwidth: _not stated_
- arrays: ALMA 7-m Array (grid source monitoring); IRAM 30-m Telescope; SMA  
  > "3C 286, a point-source calibrator for the ALMA 7-m Array, has been monitored as one of the grid sources" (Data, ALMA); "3C 286 has been monitored with the IRAM 30-m Telescope at 86 and 229 GHz as part of the following three programs" (Data, IRAM 30-m Telescope)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: IRAM 28 arcsec at 86 GHz and 11 arcsec at 229 GHz (telescope beam)  
  > "The angular resolution of the telescope corresponds to 28" and 11" at 86 and 229 GHz, respectively." (Data, IRAM 30-m Telescope)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: ALMA 2018 May to 2024 Dec (Band 3/7; Band 6 to 2024 Aug); IRAM Oct 2006 to May 2024 (86 GHz) and 2010 May to 2022 Jul (229 GHz); SMA 2022 Jun to 2025 Feb; overall Oct 2006 to Feb 2025  
  > "spanning from October 2006 to February 2025" (Introduction); "SMAPOLA is a program initiated in 2022 June to regularly monitor the polarization properties of 40 AGN jets" (Data, SMA)
- pi or archival as stated: Monitoring programs: ALMA grid-source monitoring; IRAM POLAMI, MAPI and OJ 287 polarimetric monitoring; SMA SMAPOLA  
  > "the Polarimetric Monitoring of AGN at Millimeter Wavelengths (POLAMI) program" (Data, IRAM 30-m Telescope); "Consequently, we only included recent data which were calibrated using a consistent process and model under the SMAPOLA" (Data, SMA)
- Other facility **IRAM 30-m Telescope**: Total flux and polarization monitoring at 86 and 229 GHz, 2006 to 2024  
  > "Here we present all the data obtained from October 2006 to May 2024 to extend the period of investigation." (Data, IRAM 30-m Telescope)
- Other facility **Submillimeter Array (SMA)**: Full-polarization flux and polarization monitoring at 225 GHz (2022 to 2025); earlier SMA flux data excluded  
  > "we do not include these measurements in our analysis due to inconsistencies in the flux calibration process" (Data, SMA)
- External data: VLA total flux at 1–50 GHz used for spectral index and equipartition flux (I0 = 7.297 Jy at 4.885 GHz)  
  > "we adopted the total flux measurements using VLA at 1–50 GHz (cite: perley13_flux)" (Data, VLA); "the total flux of $I_{0}$=7.297 Jy at $\nu_0$=4.885 GHz[^18] (cite: perley13_flux)" (Discussion, Synchrotron age and magnetic field strength) [from (cite: perley13_flux)]
- External data: VLA EVPA at 5, 15, 25, 33 and 45 GHz and fractional polarization at 1.5–43.3 GHz  
  > "we took the EVPA measurements at 5, 15, 25, 33, and 45 GHz from Table 2 in (cite: perley13_pol)" (Data, VLA) [from (cite: perley13_pol)]
- External data: IRAM 86 GHz EVPA 37.3 deg and 229 GHz earlier IRAM data (2010 to 2022) from earlier publications; agudo12 data reprocessed in this paper  
  > "$37.3^\circ\pm0.8^\circ$ at 86 GHz with the IRAM Pico Veleta 30-meter Telescope (IRAM) (cite: agudo12)" (Introduction); "The dataset presented in our paper includes measurements previously published in (cite: agudo12) and (cite: agudo18_1)." (Footnote 8) [from (cite: agudo12); (cite: agudo18_1)]
- External data: ESA4 brightness model of Uranus and Butler-JPL-Horizons 2012 planet models  
  > "The CASA brightness temperature models for planets follow the Butler-JPL-Horizons 2012 framework, as explained in ALMA memo 594 (cite: butler12)." (Data, ALMA) [from (cite: butler12)]
- External data: Equipartition parameter xi = 1.23e-12 from table of equipartition parameters  
  > "which is given for $\alpha\sim0.7$ between the turnover and break frequencies (cite: govoni04)" (Discussion, Synchrotron age and magnetic field strength) [from (cite: govoni04)]
- External data: MeerKAT EVPA at 1.4 GHz (29.2 deg) excluded from RM calculation  
  > "We did not include $\chi=29.2^\circ$ at 1.4 GHz obtained with MeerKAT in the RM calculation" (Footnote 20) [from (cite: taylor24)]
- Simulation/model as data: Lellouch & Amri Mars model and ESA4 Uranus model used as planet flux references for IRAM Kelvin-to-Jansky conversion  
  > "The Mars model is based on the Lellouch & Amri model" (The IRAM 30-m Telescope); "For Uranus, the ESA4 model used for the Herschel Space Observatory mission (cite: bendo13; griffin13; orton14) was adopted." (The IRAM 30-m Telescope)

## Processing

### Calibration

- pipeline or manual: AMAPOLA CASA-friendly Python scripts used to reduce ALMA polarimetric data; SMA data calibrated with MIR and instrumental polarization with MIRIAD; IRAM XPOL calibration  
  > "This is a set of CASA-friendly python scripts to reduce the ALMA polarimetric data, as described in (cite: kameno23)." (Data, ALMA); "the instrumental polarization was calibrated with the MIRIAD (cite: sault95)" (Data, SMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus (ESA4 model) as ALMA primary reference; other SSOs referenced to Uranus within 5%  
  > "Specifically, the model for Uranus is based on the ESA4 model" (Data, ALMA); "other SSOs are used with their flux scales referenced to Uranus within 5% uncertainties (cite: kneissl23)" (Data, ALMA)
- flux scale uncertainty: absolute flux calibration typically less than 5% in Band 3 and 10% in Bands 6 and 7 (ALMA); 5% planet-model uncertainty for IRAM  
  > "As a result, the uncertainties originating from the absolute flux calibration are typically less than 5% in Band 3 and 10% in Bands 6 and 7 (cite: remijan19)." (Data, ALMA); "the uncertainties in the planet models (conservatively considered as 5%, which typically dominates the final uncertainty)" (The IRAM 30-m Telescope)
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

- IRAM Kelvin-to-Jansky conversion factor derived from Mars and Uranus 2006 to 2014 and applied to all IRAM data  
  > "The Kelvin-to-Jansky conversion factor, which converts antenna temperatures to flux densities, was derived based on the flux of Mars and Uranus measured from 2006 to 2014 (cite: agudo18_1)." (The IRAM 30-m Telescope); "These factors were applied to the entire data obtained from 2006 to 2024" (The IRAM 30-m Telescope) [from (cite: agudo18_1)]
- XPOL setup and calibration processes maintained throughout monitoring  
  > "The standard XPOL setup and calibration processes summarized in (cite: thum08) has been maintained throughout the monitoring" (The IRAM 30-m Telescope) [from (cite: thum08)]
- ALMA grid-source flux scaling via Uranus and SSO consistency within 5%  
  > "any flux correction factors derived from other SSOs that deviate by more than 5% from those derived from Uranus were excluded from the flux calibration process (cite: kneissl23)" (Results, Total flux) [from (cite: kneissl23)]
- Synchrotron age model (continuous injection, B_CMB and tau formula)  
  > "Assuming (i) a continuous injection model, where new relativistic electrons with a power-law energy distribution are continuously injected to the synchrotron-emitting source" (Discussion, Synchrotron age and magnetic field strength) [from (cite: murgia99; murgia03)]
- Core-shift conical jet model (BK) and RM-to-core-shift relation with a = 2  
  > "According to the Blandford & Königl (BK) conical jet model, the core is defined as the region where the jet plasma becomes optically thin" (Discussion, EVPA rotation as a function of frequency) [from (cite: lobanov98; jorstad07; park18; hovatta19)]

### Not stated but needed to reproduce (our reading)

- ALMA CASA version and pipeline/manual reduction steps per epoch (AMAPOLA options, flagging, bandpass, leakage calibrators) are not given
- Per-epoch ALMA flux calibrator and gain calibrator identities are not listed
- Data selection and averaging for ALMA and IRAM epochs (quality cuts, time or frequency averaging) are not stated
- Exact MJD ranges and sample sizes for Periods I–III beyond the summary table
- Fitting method and weights for the linear flux and polarization trends (Eq. fit) and for the RM and EVPA fits beyond 'weighted fit'
- Exact list of the ten representative frequencies used to sample the model EVPA curve
- Conversion constant between RM and EVPA and the electron density and magnetic field values in the RM relation
- Equipartition inputs: value of k adopted for the spectral break fit and the break-frequency fit method
- Whether the 67.2 GHz break was fitted with a broken power law and its fit code
- Uranus model version and ring-correction assumptions used when computing flux scaling

## Analysis recipe

1. **measure ALMA epoch fluxes and polarization**: Polarimetric ALMA data reduced with AMAPOLA scripts; total flux, fractional polarization and EVPA measured per epoch  
  > "we collected data reduced using the Analytic Matrix for ALMA POLArimetry (AMAPOLA" (Data, ALMA)
   - software: AMAPOLA, CASA
   - parameter: Full-polarization observations; Uranus as flux reference  
  > "The observations of 3C 286 were performed with a full polarization mode to obtain all four Stokes parameters." (Data, ALMA)
   - assumption: ESA4 model for Uranus assumed constant brightness  
  > "which assumes its absolute brightness is constant over time" (Results, Total flux)
   - fitting: _not stated_
   - validation: AMAPOLA dataset validated in previous AGN studies  
  > "The dataset has been validated and used in previous studies of AGN jets such as M87 (cite: goddi21; goddi25)" (Data, ALMA)
2. **derive IRAM total flux via Kelvin-to-Jansky conversion**: Antenna temperatures converted to flux densities with fixed conversion factors derived from Mars and Uranus, applied to all data 2006 to 2024  
  > "These factors were applied to the entire data obtained from 2006 to 2024" (The IRAM 30-m Telescope)
   - parameter: Conversion factors 6.1 ± 0.1 Jy/K at 86 GHz and 8.6 ± 0.4 Jy/K at 229 GHz  
  > "Consequently, the conversion factor was determined to be" (The IRAM 30-m Telescope)
   - parameter: Mean total-flux uncertainty 5.1% at 86 GHz and 5.8% at 229 GHz  
  > "This leads to average uncertainties in the total flux measurements of 3C 286 of 5.1% at 86 GHz and 5.8% at 229 GHz, respectively." (The IRAM 30-m Telescope)
   - assumption: Mars model (Lellouch & Amri) and ESA4 Uranus model correct for 2006 to 2014 calibration  
  > "The Mars model is based on the Lellouch & Amri model" (The IRAM 30-m Telescope)
   - fitting: _not stated_
   - validation: Crab Nebula observed to cross-check polarization calibration  
  > "To cross-check the results of the polarization calibration, the Crab Nebula was observed" (The IRAM 30-m Telescope)
3. **test secular trends in flux, EVPA and polarization**: Linear trend fitted to all total-flux measurements at each frequency in time (MJD)  
  > "we fitted all the total flux measurements at each frequency with the following function" (Results, Total flux)
   - parameter: S = c0 × (t−58000) + c1, with t in MJD  
  > "where $S_{\nu}$ is the total flux in Jy, and $t$ is the observation date in MJD." (Results, Total flux)
   - assumption: Uranus brightness assumed constant in ESA4 model  
  > "which assumes its absolute brightness is constant over time" (Results, Total flux)
   - fitting: Linear least-squares style fit of c0 and c1 per frequency; weighting not stated  
  > "The best-fit parameters are summarized in Table" (Results, Total flux)
   - validation: Trend compared to standard deviations and measurement uncertainties per period  
  > "albeit the magnitude of the decline is comparable to the standard deviations of each period" (Results, Total flux)
4. **measure spectral index and break frequency**: Power-law spectral index fitted over 3–50 GHz (VLA) and 86–229 GHz (IRAM); break from the two indices  
  > "the spectral index between 3 and 50 GHz, where the flux nearly follows a simple power-law, yields a spectral index of $\alpha=0.712\pm0.003$" (Discussion, Synchrotron cooling)
   - parameter: alpha(3–50 GHz) = 0.712 ± 0.003; alpha(86–229 GHz) = 1.039 ± 0.008  
  > "This difference in spectral index between the two frequency ranges leads to a spectral break at $67.2\pm1.2$ GHz" (Discussion, Synchrotron cooling)
   - assumption: Synchrotron cooling interpretation of spectral steepening  
  > "Such a spectral break can be attributed to the process of synchrotron cooling (or aging)" (Discussion, Synchrotron cooling)
   - fitting: _not stated_
   - validation: _not stated_
5. **estimate synchrotron age and apparent speed**: Equipartition magnetic field from VLA flux and size; age from tau_syn formula with break frequency  
  > "we adopt a source size of 50 mas" (Discussion, Synchrotron age and magnetic field strength)
   - parameter: Equipartition xi = 1.23e-12; I0 = 7.297 Jy at 4.885 GHz; k = 1; source size 50 mas (depth 3.6e-1 kpc)  
  > "Assuming an energy ratio between electrons and protons of $k=1$" (Discussion, Synchrotron age and magnetic field strength)
   - assumption: Continuous injection, no expansion of the emitting source, constant magnetic field strength  
  > "(ii) no expansion of the emitting source, and (iii) constant magnetic field strength" (Discussion, Synchrotron age and magnetic field strength)
   - assumption: Spherical geometry for source depth  
  > "assuming a spherical geometry for simplicity" (Discussion, Synchrotron age and magnetic field strength)
   - fitting: _not stated_
   - validation: Comparison with CSS and inner-jet apparent speeds  
  > "this is also faster than the typical speeds observed in CSS sources" (Discussion, Synchrotron age and magnetic field strength)
6. **fit EVPA vs wavelength squared and derive RM**: Single power-law fit of EVPA vs lambda^2 across VLA, ALMA, IRAM and SMA; RM from slopes between adjacent pairs  
  > "we fit all the EVPA values with a single power-law function of the form" (Discussion, EVPA rotation as a function of frequency)
   - parameter: k = −0.016 ± 0.002, C = 1.547 ± 0.003 (weighted fit)  
  > "The resulting coefficients from the weighted fit are" (Discussion, EVPA rotation as a function of frequency)
   - parameter: Model EVPA sampled at ten representative frequencies  
  > "we sample the EVPA values along the best-fit curve at ten representative frequencies" (Discussion, EVPA rotation as a function of frequency)
   - assumption: RM rest frame defined as (1+z)^2 times observed RM  
  > "\rm \left|RM_{\rm rest}\right| = (1+z)^2 \left|RM_{\rm obs}\right|" (Discussion, EVPA rotation as a function of frequency)
   - fitting: weighted power-law fit in log space  
  > "The resulting coefficients from the weighted fit are" (Discussion, EVPA rotation as a function of frequency)
   - validation: Excluded MeerKAT point from RM calculation  
  > "Including this measurement could introduce a systematic deviation in the fit" (Footnote 20)
7. **fit fractional polarization vs lambda^2 and test Faraday depolarization**: Single power-law fit of fractional polarization vs lambda^2 from 1.5 to 343.4 GHz  
  > "we fit the fractional polarization values with a single power-law function of the form" (Discussion, Depolarization mechanism)
   - parameter: k' = −0.047 ± 0.001, C' = 1.108 ± 0.001  
  > "with coefficients $k'=-0.047\pm0.001$ and $\rm C'=1.108\pm0.001$" (Discussion, Depolarization mechanism)
   - assumption: Depolarization by foreground plasma within instrumental beam  
  > "If the foreground plasma is not uniform within an instrumental resolution element" (Discussion, Depolarization mechanism)
   - fitting: single power-law fit in log space  
  > "is well-described by a single power-law function with coefficients" (Discussion, Depolarization mechanism)
   - validation: _not stated_

## Software

- **AMAPOLA** : Reduction of ALMA polarimetric data (CASA-friendly Python scripts)  
  > "This is a set of CASA-friendly python scripts to reduce the ALMA polarimetric data, as described in (cite: kameno23)." (Data, ALMA)
- **CASA** : Planet brightness temperature models used for flux calibration  
  > "The CASA brightness temperature models for planets follow the Butler-JPL-Horizons 2012 framework" (Data, ALMA)
- **MIR** : SMA data calibration (flagging, bandpass, complex gains, flux calibration, RL-phase offset)  
  > "The initial data calibration such as flagging, bandpass, cross-receiver delays, complex gains, flux calibration, and RL-phase offset was performed using the MIR software package" (Data, SMA)
- **MIRIAD** : SMA instrumental polarization calibration  
  > "the instrumental polarization was calibrated with the MIRIAD (cite: sault95)" (Data, SMA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA total flux decrease at 233.0 GHz over 2018–2024 | 11% | not stated | percent | 3 | the declines of 11% at 233.0 GHz and 15% at 343.4 GHz exceed the typical uncertainties of 10% in Bands 6 and 7 |
| ALMA total flux decrease at 343.4 GHz over 2018–2024 | 15% | not stated | percent | 3 | the declines of 11% at 233.0 GHz and 15% at 343.4 GHz exceed the typical uncertainties of 10% in Bands 6 and 7 |
| Uranus brightness increase over ALMA monitoring period | 4 | not stated | percent | 3 | the brightness of Uranus has increased by 4% during the monitoring period |
| IRAM 86 GHz residual flux systematic increase 2006–2024 | 6.6 | ±1.5 | percent | 3 | indicates a systematic increase of 6.6%$\pm$1.5% from 2006 to 2024 |
| Spectral index 3–50 GHz | 0.712 | ±0.003 | dimensionless | 4 | yields a spectral index of $\alpha=0.712\pm0.003$ |
| Spectral index 86–229 GHz | 1.039 | ±0.008 | dimensionless | 4 | corresponds to a spectral index of $1.039\pm0.008$ |
| Spectral break frequency | 67.2 | ±1.2 | GHz | 4 | This difference in spectral index between the two frequency ranges leads to a spectral break at $67.2\pm1.2$ GHz |
| Equipartition magnetic field strength | 4.4 | not stated | mG | 5 | yield an equipartition magnetic field strength of |
| Synchrotron age of 3C 286 (continuous injection) | 450 | not stated | years | 5 | we derive the age of 3C 286 to be $\tau_{\rm syn}$=450 years |
| Average apparent speed from synchrotron age | 2.6 | not stated | dimensionless | 5 | this age implies an average apparent speed $\beta_{\rm app}=2.6$ |
| EVPA power-law slope vs lambda^2 | -0.016 | ±0.002 | dimensionless | 6 | The resulting coefficients from the weighted fit are $k=-0.016\pm0.002$ |
| Power-law index of RM vs frequency (core-shift) | 2.05 | ±0.06 | dimensionless | 6 | with the power-law index $a=2.05\pm0.06$ |
| Rest-frame |RM| increase from 5 to 343 GHz (lower value) | 23 | not stated | rad m^-2 | 6 | This corresponds to an increase from $\rm 23\ rad\ m^{-2}$ to $\rm 32000\ rad\ m^{-2}$ in the rest frame |
| Rest-frame |RM| at 343 GHz (upper value) | 32000 | not stated | rad m^-2 | 6 | This corresponds to an increase from $\rm 23\ rad\ m^{-2}$ to $\rm 32000\ rad\ m^{-2}$ in the rest frame |
| Fractional polarization power-law slope vs lambda^2 | -0.047 | ±0.001 | dimensionless | 7 | with coefficients $k'=-0.047\pm0.001$ and $\rm C'=1.108\pm0.001$ |
| EVPA at 5 GHz (reference fit result) | 33.0 | ±1.0 | degrees | 6 | from $33.0^\circ\pm1.0^\circ$ at 5 GHz to $38.9^\circ\pm0.1^\circ$ at 343.4 GHz |
| EVPA at 343.4 GHz (reference fit result) | 38.9 | ±0.1 | degrees | 6 | from $33.0^\circ\pm1.0^\circ$ at 5 GHz to $38.9^\circ\pm0.1^\circ$ at 343.4 GHz |
| Fractional polarization at 343.4 GHz | 16.4 | ±0.1 | percent | 7 | from $8.6\%$ at 1.1 GHz to $16.4\%\pm0.1\%$ at 343.4 GHz |

## Qualitative findings

- IRAM total flux nearly constant over 2006–2024 within measurement uncertainties  
  > "The IRAM measurements from 2006 to 2024 show that the total flux of 3C 286 is stable within measurement uncertainties" (abstract)
- ALMA flux decrease possibly partly due to brightening of Uranus (ESA4 model not time-dependent)  
  > "which up to 4% could be attributed to an apparent increase in the absolute brightness of Uranus" (abstract)
- Proposed use of model EVPA curve for absolute EVPA calibration from 5 to 343.4 GHz  
  > "We therefore propose using the theoretical EVPA values from this model curve for absolute EVPA calibration between 5 and 343.4 GHz." (abstract)

## Claim tuples

- H: Is the total flux of 3C 286 stable up to 229 GHz over 2006–2024/2025? | E: Compare IRAM total flux trends at 86 and 229 GHz with ALMA trends and Uranus brightness model | R: IRAM shows no clear trend; ALMA decreases by 2–15% with Uranus brightening up to 4% | F: Intrinsic total flux of 3C 286 remained stable up to 229 GHz over the monitoring period | **supported**
- H: Is the EVPA rotation with frequency due to core-shift in a conical jet? | E: Single power-law fit of EVPA vs lambda^2 and RM vs frequency fit with exponent | R: |RM| ∝ ν^a with a = 2.05 ± 0.06, close to the expected a = 2 | F: Observed EVPA rotation is primarily due to core-shift in a conical jet | **partially**
- H: Is the synchrotron age of 3C 286 representative of the whole jet? | E: Equipartition B field and continuous-injection age from the 67 GHz break and VLA flux | R: Age 450 yr, implied speed 2.6, faster than CSS sources | F: Spectrum may not represent entire jet age; one-zone model may be insufficient | **partially**
- H: Are EVPA and fractional polarization of 3C 286 stable over ~20 years? | E: Period-based averages and linear trend fits of ALMA and IRAM EVPA and polarization | R: Secular changes smaller than or comparable to standard deviations and uncertainties | F: No significant secular polarization trends; stable from 86 to 343.4 GHz | **supported**

## Reasoning

- Why this data: Multi-instrument monitoring allows precise investigation of stability at mm/submm wavelengths  
  > "The combined data from these three monitoring programs allows for a precise investigation of the stability and properties of 3C 286 at millimeter and submillimeter wavelengths." (Introduction)
- Why this method: Use of AMAPOLA-reduced ALMA data validated in prior AGN polarization studies  
  > "supporting the reliability of the polarization measurements." (Data, ALMA)
- Alternative: SMA total flux rejected due to inconsistent flux calibration; SMA flux not used for stability test  
  > "we do not include these measurements in our analysis due to inconsistencies in the flux calibration process" (Data, SMA)
- Alternative: Depolarization models considered but judged primarily for optically thin cases  
  > "However, those models are primarily suited for optically thin cases" (Discussion, Depolarization mechanism)
- How they decided it was enough: _not stated_
- Limitation (authors): Residual flux trend comparable to average residual uncertainty of 4.8%  
  > "albeit the magnitude of the increase is comparable to the average uncertainty in the residual flux of 4.8%" (Results, Total flux)
- Limitation (authors): IRAM EVPA uncertainties may be underestimated at 229 GHz  
  > "This discrepancy suggests that the EVPA uncertainties for IRAM may have been underestimated." (Results, Polarization)
- Limitation (authors): Synchrotron age depends on one-zone assumption and an adopted 50 mas size  
  > "This, in turn, implies that the overall spectrum may not be fully explained by a one-zone synchrotron model" (Discussion, Synchrotron age and magnetic field strength)
- Caveat (inferred, ours): ALMA flux trend attribution to Uranus is not demonstrated; the paper itself leaves instrumental effects open.
- Caveat (inferred, ours): Equipartition field and age depend on adopted k, source size and geometry; no uncertainties are propagated.
- Caveat (inferred, ours): The EVPA-based RM fit rests on heterogeneous data from VLA, ALMA, IRAM and SMA with different calibration chains.
- Caveat (inferred, ours): IRAM 229 GHz EVPA uncertainties are acknowledged to be possibly underestimated.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Only ALMA archive ID 2011.0.00001.CAL is printed; manifest lists no linked projects  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00001.CAL." (Conclusions (acknowledgment paragraph))
- Code: AMAPOLA scripts available from a public web page  
  > "<https://www.alma.cl/~skameno/AMAPOLA/>" (Data, ALMA footnote 5)
- Missing: ALMA raw or calibrated data identifiers for the 2018–2024 grid-source epochs
- Missing: Per-epoch ALMA calibration and imaging/extraction steps and CASA version
- Missing: IRAM and SMA processed data tables (only summary tables given)
- Missing: Fitting code and weighting for trend, spectral index, EVPA and RM fits
- Missing: Exact values used for break frequency fit and equipartition inputs
- Data volume (inferred): Several hundred single-pointing polarimetric measurements across ALMA, IRAM and SMA; likely modest total volume (order of gigabytes or less), not stated in the paper.
- Score (inferred): 3/5, Methods are described in reasonable detail for the flux and polarization trend analysis, but ALMA reduction settings, data identifiers, and fitting details are missing.
- Rediscovery candidate: no, Data availability is not stated and ALMA calibration/reduction settings and fitting details are incomplete, so the recipe cannot be redone from the paper alone.

## Links

- Method: (cite: kameno23) (AMAPOLA reduction scripts for ALMA polarimetry)
- Method: (cite: thum08) (XPOL polarimeter setup and calibration at IRAM)
- Method: (cite: butler12) (Planet brightness temperature models (ESA4 Uranus model))
- Method: (cite: murgia99; murgia03) (Synchrotron age formula with continuous injection)
- Method: (cite: govoni04) (Equipartition parameter and magnetic field estimate)
- Companion: (cite: agudo18_1) (Earlier IRAM monitoring and Kelvin-to-Jansky conversion factor)
- Companion: (cite: perley13_pol) (VLA polarization reference values used in comparisons)
- Companion: (cite: kneissl23) (ALMA grid source and solar system flux scale)
- Related: POLAMI
- Related: MAPI
- Related: SMAPOLA
- Related: AMAPOLA

## Checks

```json
{
 "quotes": 115,
 "quotes_ok": 113,
 "quote_pass_rate": 0.983,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00001.CAL"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 18,
 "numeric_problems": 0,
 "fill": {
  "facts": 108,
  "stated": 74,
  "rate": 0.685
 },
 "evidence_ok": false
}
```

## Figures

- **Figure 1** (light_curve_or_time_series, 3 panel(s), data): Total flux, fractional polarization and EVPA of 3C 286 from ALMA at 91.5, 103.5, 233.0 and 343.4 GHz versus MJD, with dotted lines giving the average at each frequency.
  - axes: x: MJD (top axis year) [days]; y (top): total flux density [Jy]; y (middle): fractional polarization m [%]; y (bottom): EVPA [degrees]
  - supports step 1
  - read off the plot: approx. 91.5 GHz mean flux 0.80 Jy; approx. 103.5 GHz mean flux 0.72 Jy; approx. 233.0 GHz mean flux 0.31 Jy; approx. 343.4 GHz mean flux 0.20 Jy; approx. mean EVPA 37 degrees
  - reproduction target
- **Figure 2** (light_curve_or_time_series, 2 panel(s), data): ALMA Band 3 and Bands 6/7 total flux of 3C 286 versus MJD, with period averages and standard deviations highlighted in three shaded epochs.
  - axes: x: MJD [days]; y (top): flux density [Jy]; y (bottom): flux density [Jy]
  - supports step 3
  - read off the plot: approx. 91.5 GHz mean flux 0.80 Jy; approx. 103.5 GHz mean flux 0.72 Jy; approx. 233.0 GHz mean flux 0.31 Jy; approx. 343.4 GHz mean flux 0.20 Jy
- **Figure 3** (light_curve_or_time_series, 3 panel(s), data): Total flux, fractional polarization and EVPA of 3C 286 from IRAM at 86 and 229 GHz and SMA at 225 GHz versus MJD, with dotted lines giving the average at each frequency.
  - axes: x: MJD (top axis year) [days]; y (top): total flux density [Jy]; y (middle): fractional polarization m [%]; y (bottom): EVPA [degrees]
  - supports step 3
  - read off the plot: approx. IRAM 86 GHz mean flux 0.89 Jy; approx. IRAM 229 GHz mean flux 0.32 Jy; approx. mean EVPA 37 degrees; approx. SMA 225 GHz polarization around 15-16 %
  - reproduction target
- **Figure 4** (light_curve_or_time_series, 2 panel(s), data): Total flux of 3C 286 from IRAM at 86 and 229 GHz over 2006-2025 overlaid with ALMA Band 3 and Bands 6/7 fluxes, with IRAM means as dashed lines.
  - axes: x: MJD (top axis year) [days]; y (top): total flux density [Jy]; y (bottom): total flux density [Jy]
  - supports step 2
  - validation: Compares ALMA fluxes with the IRAM monitoring over the same period to check cross-instrument consistency.
  - read off the plot: approx. IRAM 86 GHz mean 0.89 Jy; approx. IRAM 229 GHz mean 0.32 Jy; approx. ALMA 91.5 GHz flux near 0.80 Jy; approx. ALMA 343.4 GHz flux near 0.20 Jy
- **Figure 5** (model_vs_data, 2 panel(s), data, model, residual): Uranus total flux at 86 GHz measured with IRAM compared with the ESA4 model, and the normalized residual flux with binned averages and a linear trend fit.
  - axes: x: MJD (top axis year) [days]; y (top): Uranus flux density [Jy]; y (bottom): residual flux relative to model [%]
  - supports step 2
  - validation: Checks the Uranus-based IRAM flux calibration by comparing observed Uranus flux with the ESA4 model and testing for secular residual drift.
  - read off the plot: approx. Uranus flux range 6 to 8 Jy; approx. Uranus flux peak 8.3 Jy near MJD 55000; approx. binned residual near 0 % around MJD 55500; approx. largest negative residual -29 % near MJD 54350
- **Figure 6** (spectrum, 2 panel(s), data, literature_comparison): EVPA and fractional polarization of 3C 286 in the observing frame versus frequency for ALMA, IRAM, SMA and VLA.
  - axes: x: frequency [GHz]; y (left): EVPA [degrees]; y (right): fractional polarization m [%]
  - supports step 6
  - read off the plot: approx. EVPA 33 degrees at 5 GHz (VLA); approx. EVPA 37 degrees at 90 GHz (IRAM); approx. EVPA 39 degrees near 340 GHz (ALMA); approx. m 9.5 % at 1.5 GHz (VLA); approx. m 16.4 % near 340 GHz (ALMA)
  - reproduction target
- **Figure 7** (spectrum, 1 panel(s), data): Spectral flux density of 3C 286 from 1 to 229 GHz combining VLA and IRAM totals, with power-law fits and the break frequency marked.
  - axes: x: frequency [GHz]; y: total flux density [Jy]
  - supports step 4
  - read off the plot: approx. flux 26 Jy at 0.3 GHz; approx. flux 10 Jy near 4 GHz; approx. flux 1 Jy near 90 GHz; approx. break frequency marked at 67.2 GHz; approx. flux 0.3 Jy near 230 GHz
  - reproduction target
- **Figure 8** (scatter_or_relation, 1 panel(s), data, model): EVPA measurements from ALMA, IRAM, SMA and VLA plotted against lambda squared with the best-fit curve used to derive the rotation measure.
  - axes: x: wavelength squared [cm^2]; y: EVPA [degrees]
  - supports step 6
  - read off the plot: approx. EVPA 39 degrees at lambda^2 near 0; approx. EVPA 33 degrees at lambda^2 near 10.5 cm^2; approx. EVPA 38.3 degrees for SMA near 0 cm^2; approx. EVPA 35.8 degrees for VLA near 0.1 cm^2
  - reproduction target
- **Figure 9** (scatter_or_relation, 1 panel(s), data, model): Absolute rotation measure computed from adjacent VLA and ALMA frequency pairs plotted against geometric mean frequency, with a power-law fit.
  - axes: x: geometric mean frequency [GHz]; y: absolute rotation measure |RM| [rad m^-2]
  - supports step 6
  - read off the plot: approx. |RM| 23 rad m^-2 at 15 GHz; approx. |RM| 1.4e3 rad m^-2 at 115 GHz; approx. |RM| 3.2e4 rad m^-2 at 500 GHz; approx. power-law index 2.05 +/- 0.06
  - reproduction target
- **Figure 10** (scatter_or_relation, 1 panel(s), data, model): Fractional polarization from ALMA, IRAM, SMA and VLA plotted against lambda squared with the best-fit curve testing Faraday depolarization.
  - axes: x: wavelength squared [cm^2]; y: fractional polarization m [%]
  - supports step 7
  - validation: Tests whether fractional polarization decreases with lambda squared as expected from Faraday depolarization.
  - read off the plot: approx. m 16.4 % at lambda^2 near 0 cm^2; approx. m 13.8 % for IRAM near 0 cm^2; approx. m 9.5 % at lambda^2 near 123 cm^2; approx. m 13.1 % for VLA near 0 cm^2
  - reproduction target
