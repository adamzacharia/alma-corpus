# Monitoring of 3C 286 with ALMA, IRAM, and SMA from 2006 to 2025: Stability, Synchrotron Ages, and Frequency-dependent Polarization Attributed to Core-shift

`2025ApJ...994..196K` | The Astrophysical Journal 2025 | first author: Kam, Minchul | arXiv: 2510.05540 | DOI: 10.3847/1538-4357/ae10b1

Card schema 1.0 | model gemini-3.8-flash | depth full | type archival_reuse

## Science

- Fields: agn_and_quasars, instrumentation
- Question: To determine whether the total flux and polarimetric properties (EVPA and fractional polarization) of the standard calibrator quasar 3C 286 remain stable at millimeter and submillimeter wavelengths over long timescales, and to characterize its frequency-dependent polarization and synchrotron aging.  
  > "In this paper, we present the result of polarimetric observations of 3C 286 using ALMA, IRAM, and SMA at 91.5–343.4 GHz, spanning from October 2006 to February 2025." (1 Introduction); "The combined data from these three monitoring programs allows for a precise investigation of the stability and properties of 3C 286 at millimeter and submillimeter wavelengths." (1 Introduction)
- Target **3C 286**: coordinates _not stated_; z/distance z = 0.849  
  > "3C 286 is a quasar (z=0.849; (cite: burbidge69)) classified as a compact steep-spectrum (CSS) source" (1 Introduction); distance from (cite: burbidge69)  
  > "3C 286 is a quasar (z=0.849; (cite: burbidge69)) classified as a compact steep-spectrum (CSS) source" (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00001.CAL
- bands: Band 3, Band 6, Band 7  
  > "The data has been primarily obtained in Band 3 (91.5 and 103.5 GHz) and Band 7 (343.4 GHz) since May 2018. Data in Band 6 (233.0 GHz) has been obtained less frequently as a complement to the Band 7 data" (2.1 ALMA)
- frequencies and spectral setup: 91.5, 103.5, 233.0, and 343.4 GHz  
  > "We present the results of multi-frequency monitoring of the radio quasar 3C 286, conducted using three instruments: ALMA at 91.5, 103.5, 233.0, and 343.4 GHz" (Abstract)
- continuum bandwidth: _not stated_
- arrays: 7-m Array  
  > "About 40 bright calibrators, known as “grid sources" and evenly distributed across the sky, are observed with the 7-m Array at least every two weeks to provide secondary flux calibrators in addition to solar system objects" (2.1 ALMA); "3C 286, a point-source calibrator for the ALMA 7-m Array, has been monitored as one of the grid sources" (2.1 ALMA)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: May 2018 to December 2024 (August 2024 for Band 6)  
  > "ALMA | 91.5 | 2018 May - 2024 Dec. | 207 | 330" (Table 1); "ALMA | 233.0 | 2018 May - 2024 Aug. | 32 | 73" (Table 1)
- pi or archival as stated: archival  
  > "For polarization analysis, we collected data reduced using the Analytic Matrix for ALMA POLArimetry (AMAPOLA). This is a set of CASA-friendly python scripts to reduce the ALMA polarimetric data" (2.1 ALMA); "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00001.CAL." (Conclusions)
- Other facility **IRAM 30-m Telescope**: Total flux and polarization monitoring data at 86 GHz and 229 GHz from October 2006 to May 2024 using the XPOL polarimeter under POLAMI, MAPI, and OJ 287 monitoring programs.  
  > "3C 286 has been monitored with the IRAM 30-m Telescope at 86 and 229 GHz as part of the following three programs: the Polarimetric Monitoring of AGN at Millimeter Wavelengths (POLAMI) program" (2.2 The IRAM 30-m Telescope); "The monitoring of 3C 286 was performed with the XPOL polarimeter (cite: thum08) installed at the IRAM." (2.2 The IRAM 30-m Telescope)
- Other facility **Submillimeter Array (SMA)**: Full polarization monitoring observations centered at 225 GHz from June 2022 to February 2025 using the SWARM correlator under the SMAPOL program.  
  > "Consequently, we only included recent data which were calibrated using a consistent process and model under the SMAPOL (SMA Monitoring of AGNs with POLarization) program." (2.3 SMA); "The separation between the center frequencies of the lower sideband (LSB) and upper sideband (USB) was set to about 20 GHz, centered at 225 GHz." (2.3 SMA)
- Other facility **Very Large Array (VLA)**: Historical total flux measurements from 1–50 GHz and polarization (EVPA and fractional polarization) measurements at 1.5–45 GHz.  
  > "For this comparison, we adopted the total flux measurements using VLA at 1–50 GHz (cite: perley13_flux), along with polarization measurements from the same instrument." (2.4 VLA)
- External data: VLA total flux measurements at 1–50 GHz, EVPA measurements at 5, 15, 25, 33, and 45 GHz (weighted mean from 1995 to 2012), and fractional polarization measurements at 1.5, 4.9, 8.4, 15.0, 22.5, and 43.3 GHz for epoch 2000.0  
  > "Specifically, we took the EVPA measurements at 5, 15, 25, 33, and 45 GHz from Table 2 in (cite: perley13_pol), representing the weighted mean of measurements obtained at each frequency from 1995 to 2012." (2.4 VLA); "The fractional polarization values were taken from Table 5 of (cite: perley13_pol), corresponding to measurements at 1.5, 4.9, 8.4, 15.0, 22.5, and 43.3 GHz for epoch 2000.0 in the same reference." (2.4 VLA) [from (cite: perley13_flux; perley13_pol)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus (ESA4 model via Butler-JPL-Horizons 2012 framework)  
  > "Observations of the grid sources include a scan of any available solar system object (SSO), with Uranus serving as the primary reference (cite: remijan19). The CASA brightness temperature models for planets follow the Butler-JPL-Horizons 2012 framework" (2.1 ALMA); "Specifically, the model for Uranus is based on the ESA4 model, and other SSOs are used with their flux scales referenced to Uranus within 5% uncertainties" (2.1 ALMA)
- flux scale uncertainty: <5% in Band 3 and 10% in Bands 6 and 7  
  > "As a result, the uncertainties originating from the absolute flux calibration are typically less than 5% in Band 3 and 10% in Bands 6 and 7 (cite: remijan19)." (2.1 ALMA)
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

- Pipeline and calibration scripts for reducing ALMA polarimetric data  
  > "For polarization analysis, we collected data reduced using the Analytic Matrix for ALMA POLArimetry (AMAPOLA). This is a set of CASA-friendly python scripts to reduce the ALMA polarimetric data, as described in (cite: kameno23)." (2.1 ALMA) [from (cite: kameno23)]
- Kelvin-to-Jansky conversion factors of (6.1 ± 0.1) Jy/K at 86 GHz and (8.6 ± 0.4) Jy/K at 229 GHz for IRAM data  
  > "Consequently, the conversion factor was determined to be (6.1±0.1) Jy K−1 and (8.6±0.4) Jy K−1 for 86 and 229 GHz, respectively (cite: agudo18_1). These factors were applied to the entire data obtained from 2006 to 2024" (2.2 The IRAM 30-m Telescope) [from (cite: agudo18_1)]

### Not stated but needed to reproduce (our reading)

- Exact execution block (EB) IDs or scheduling block names included under ALMA project 2011.0.00001.CAL
- Specific AMAPOLA pipeline parameter configuration used for Stokes extraction

## Analysis recipe

1. **Extract Stokes flux and polarization measurements from ALMA monitoring**: Reduced ALMA full polarization observations of the grid calibrator 3C 286 using the AMAPOLA python pipeline to derive total flux S_nu, EVPA, and fractional polarization m.  
  > "For polarization analysis, we collected data reduced using the Analytic Matrix for ALMA POLArimetry (AMAPOLA). This is a set of CASA-friendly python scripts to reduce the ALMA polarimetric data, as described in (cite: kameno23)." (2.1 ALMA)
   - software: AMAPOLA, CASA
   - assumption: Uranus absolute brightness follows the ESA4 model within Butler-JPL-Horizons 2012 framework.  
  > "Specifically, the model for Uranus is based on the ESA4 model, and other SSOs are used with their flux scales referenced to Uranus within 5% uncertainties (cite: kneissl23)." (2.1 ALMA)
   - fitting: _not stated_
   - validation: Comparison across monitoring periods Period I (MJD 58230–59000), Period II (MJD 59200–59900), and Period III (after MJD 60100).  
  > "To investigate this in further detail, we divided the ALMA data into three groups: the first, obtained between MJD 58230 and 59000, referred to as Period I, the second, obtained between MJD 59200 and 59900, referred to as Period II, and the third, after MJD 60100, referred to as Period III." (3.1 Total flux)
2. **Assess secular temporal variations in total flux, EVPA, and fractional polarization**: Linear least-squares fitting of flux, EVPA, and fractional polarization as a function of observation date: S_nu = c_0 * (t - 58000) + c_1.  
  > "To further investigate the long-term trend in the ALMA data, we fitted all the total flux measurements at each frequency with the following function: S_{\nu} = c_0 \times (t-58000) + c_1" (3.1 Total flux)
   - fitting: Linear regression fitting of secular slope c_0 and baseline offset c_1.  
  > "The best-fit parameters are summarized in Table [tab:flux_summary], indicating that the flux has decreased by 2%–15% over the ALMA monitoring period." (3.1 Total flux)
   - validation: Comparing secular changes against measurement standard deviations and systematic calibration uncertainties.  
  > "The decrease of 4% at 91.5 GHz and 2% at 103.5 GHz might not be significant given the typical measurement uncertainty of 5% in Band 3 (cite: remijan19). However, the declines of 11% at 233.0 GHz and 15% at 343.4 GHz exceed the typical uncertainties" (3.1 Total flux)
3. **Determine spectral indices, break frequency, and synchrotron cooling age**: Fit power-law spectral indices between 3–50 GHz (VLA) and 86–229 GHz (IRAM), calculate spectral break frequency nu_br, and estimate synchrotron age tau_syn using continuous injection model and equipartition magnetic field.  
  > "Specifically, the spectral index between 3 and 50 GHz, where the flux nearly follows a simple power-law, yields a spectral index of alpha=0.712±0.003. In contrast, the spectral index between 86 and 229 GHz is alpha=1.039±0.008 (Table 3). This difference in spectral index between the two frequency ranges leads to a spectral break at 67.2±1.2 GHz" (4.1 Synchrotron cooling); "Assuming (i) a continuous injection model, where new relativistic electrons with a power-law energy distribution are continuously injected to the synchrotron-emitting source, (ii) no expansion of the emitting source, and (iii) constant magnetic field strength, the time elapsed after the formation of the emitting source, tau_syn (in Myrs), can be expressed as" (4.2 Synchrotron age and magnetic field strength)
   - parameter: Source size = 50 mas; depth d = 0.36 kpc; energy ratio k = 1; xi(alpha) = 1.23 x 10^-12; I_0 = 7.297 Jy at 4.885 GHz  
  > "We adopt xi(alpha, nu_1, nu_2)=1.23*10^-12, which is given for alpha~0.7 between the turnover and break frequencies (cite: govoni04), and the total flux of I_0=7.297 Jy at nu_0=4.885 GHz" (4.2 Synchrotron age and magnetic field strength); "we adopt a source size of 50 mas. This corresponds to a depth of d=3.6*10^-1 kpc, assuming a spherical geometry for simplicity." (4.2 Synchrotron age and magnetic field strength)
   - assumption: Equipartition between magnetic field and relativistic particle energy densities.  
  > "We estimate the average magnetic field strength in the emitting region by assuming the equipartition condition, in which the total energy is minimized and the energy densities of relativistic particles and magnetic fields are approximately equal" (4.2 Synchrotron age and magnetic field strength)
   - fitting: _not stated_
   - validation: Checked consistency of derived apparent jet speed with VLBI kinematic measurements.  
  > "Given that the source size of 50 mas corresponds to 362 pc, this age implies an average apparent speed beta_app=2.6. However, these apparent speeds are significantly faster than the apparent speed beta_app=0.6±0.5 observed in the inner jet" (4.2 Synchrotron age and magnetic field strength)
4. **Model EVPA and RM frequency dependence to test jet core-shift**: Fit EVPA as a power-law function of wavelength squared log(chi) = k * log(lambda^2) + C, calculate RM between frequency intervals, and fit RM vs rest-frame frequency with power-law |RM| proportional to nu^a.  
  > "To investigate the frequency dependency of the RM in more detail, we fit all the EVPA values with a single power-law function of the form log(chi) = k log(lambda^2) + C" (4.3 EVPA rotation as a function of frequency); "The best-fit line represents |RM_core,nu| proportional to nu^a with the power-law index a=2.05±0.06, which is consistent with the theoretically expected value of a=2 for the BK conical jet model." (4.3 EVPA rotation as a function of frequency)
   - assumption: Blandford & Konigl (BK) conical jet model where core position shifts as r_nu proportional to nu^-k_r.  
  > "In case of the BK conical jet expanding conically, we may expect (i) a power-law electron density distribution as a function of distance from the core n_e proportional to d^-a with a=2" (4.3 EVPA rotation as a function of frequency)
   - fitting: Weighted power-law regression fitting.  
  > "The resulting coefficients from the weighted fit are k=-0.016±0.002 and C=1.547±0.003." (4.3 EVPA rotation as a function of frequency)
   - validation: Comparison of fitted power-law index a = 2.05 ± 0.06 with the theoretical expectation a = 2 from conical jet models.  
  > "The best-fit line represents |RM_core,nu| proportional to nu^a with the power-law index a=2.05±0.06, which is consistent with the theoretically expected value of a=2 for the BK conical jet model." (4.3 EVPA rotation as a function of frequency)

## Software

- **AMAPOLA** : ALMA polarimetric data reduction  
  > "For polarization analysis, we collected data reduced using the Analytic Matrix for ALMA POLArimetry (AMAPOLA). This is a set of CASA-friendly python scripts to reduce the ALMA polarimetric data, as described in (cite: kameno23)." (2.1 ALMA)
- **CASA** : AMAPOLA environment and planetary brightness temperature models  
  > "The CASA brightness temperature models for planets follow the Butler-JPL-Horizons 2012 framework, as explained in ALMA memo 594 (cite: butler12)." (2.1 ALMA)
- **MIR** : Initial calibration (flagging, bandpass, cross-receiver delays, complex gains, flux calibration, RL-phase offset) of SMA data  
  > "The initial data calibration such as flagging, bandpass, cross-receiver delays, complex gains, flux calibration, and RL-phase offset was performed using the MIR software package" (2.3 SMA)
- **MIRIAD** : Instrumental polarization calibration of SMA data  
  > "and the instrumental polarization was calibrated with the MIRIAD (cite: sault95)." (2.3 SMA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA weighted reference EVPA at 91.5 GHz | 36.74 | 0.03 | deg | 1 | ALMA / 91.5 / - / 36.74±0.03 / 14.32±0.03 |
| ALMA weighted reference fractional polarization at 91.5 GHz | 14.32 | 0.03 | % | 1 | ALMA / 91.5 / - / 36.74±0.03 / 14.32±0.03 |
| ALMA weighted reference EVPA at 343.4 GHz | 38.93 | 0.08 | deg | 1 | ALMA / 343.4 / - / 38.93±0.08 / 16.37±0.07 |
| ALMA weighted reference fractional polarization at 343.4 GHz | 16.37 | 0.07 | % | 1 | ALMA / 343.4 / - / 38.93±0.08 / 16.37±0.07 |
| IRAM spectral index alpha between 86 and 229 GHz | 1.039 | 0.008 | dimensionless | 3 | 86–229 / 1.039±0.008 |
| Synchrotron spectral break frequency nu_br | 67.2 | 1.2 | GHz | 3 | 67.2±1.2 |
| Equipartition magnetic field strength B_eq | 4.4 | not stated | mG | 3 | Assuming an energy ratio between electrons and protons of k=1, as commonly adopted in the literature, these parameters yield an equipartition magnetic field strength of B_eq~4.4 mG. |
| Synchrotron age tau_syn under continuous injection model | 450 | not stated | yr | 3 | Substituting the magnetic field strength of 4.4 mG into Equation [eq:tau_syn], we derive the age of 3C 286 to be tau_syn=450 years. |
| EVPA power-law slope k vs log(lambda^2) | -0.016 | 0.002 | dimensionless | 4 | The resulting coefficients from the weighted fit are k=-0.016±0.002 and C=1.547±0.003. |
| Power-law index a of Faraday rotation measure |RM| vs frequency | 2.05 | 0.06 | dimensionless | 4 | The Faraday rotation measure increases as a function of frequency up to (3.2±1.5)x10^4 rad m^-2, following /RM/ proportional to nu^alpha with alpha=2.05±0.06. |
| Fractional polarization power-law slope k prime vs log(lambda^2) | -0.047 | 0.001 | dimensionless | 4 | the fractional polarization, spanning four orders of magnitude in wavelength squared, is well-described by a single power-law function with coefficients k'=-0.047±0.001 and C'=1.108±0.001 |

## Qualitative findings

- The polarization angle (EVPA) and fractional polarization of 3C 286 are stable over 20 years up to 343.4 GHz, making it an excellent high-frequency polarization calibrator.  
  > "The polarization properties of 3C 286 are stable across all observing frequencies. The electric vector position angle (EVPA) gradually rotates as a function of wavelength squared, which is well described by a single power-law over the full frequency range." (Abstract)
- The apparent 2%-15% total flux decrease seen in ALMA monitoring between 2018 and 2024 is at least partly (up to ~4%) an artifact of the secular brightening of Uranus as its northern pole rotates toward Earth, which is unmodeled by the constant-brightness ESA4 planetary model.  
  > "ALMA data from 2018 to 2024 exhibit a decrease in flux, which up to 4% could be attributed to an apparent increase in the absolute brightness of Uranus, the primary flux calibrator for ALMA with the ESA4 model." (Abstract)
- The rotation measure increases with frequency as |RM| proportional to nu^2.05, perfectly aligning with the core-shift prediction of a Blandford-Konigl conical jet.  
  > "The best-fit line represents |RM_core,nu| proportional to nu^a with the power-law index a=2.05±0.06, which is consistent with the theoretically expected value of a=2 for the BK conical jet model. This supports the interpretation that the observed EVPA rotation as a function of wavelength squared is primarily due to the core-shift effect in a conical jet" (4.3 EVPA rotation as a function of frequency)

## Claim tuples

- H: The apparent long-term flux decrease of 3C 286 in ALMA data is not intrinsic to the quasar but driven by calibrator model systematics. | E: Compare long-term ALMA flux light curves to ~20-year IRAM 30-m flux monitoring and examine the Uranus residual flux from IRAM and ALMA. | R: IRAM 86 GHz flux shows no secular decrease, while Uranus shows an ~6.6% residual brightness increase since 2006 (and ~4% in ALMA), accounting for up to 4% of the apparent ALMA flux decrease. | F: 3C 286 intrinsic flux has remained stable up to 229 GHz over 20 years; the ALMA ESA4 Uranus model needs revision due to pole rotation. | **supported**
- H: The EVPA rotation of 3C 286 from centimeter to submillimeter wavelengths is governed by core-shift and Faraday rotation in a conical jet. | E: Fit the EVPA vs wavelength squared relation from 5 to 343.4 GHz with a single power-law and measure the frequency scaling of the Faraday rotation measure. | R: EVPA follows log(chi) = (-0.016 ± 0.002) log(lambda^2) + (1.547 ± 0.003), and |RM| increases with frequency as nu^(2.05 ± 0.06). | F: The observed EVPA rotation is consistent with the core-shift effect predicted by the Blandford-Konigl conical jet model (expected a = 2), allowing theoretical EVPA values from this curve to calibrate EVPA from 5 to 343.4 GHz. | **supported**
- H: Synchrotron radiation from 3C 286 experiences high-frequency radiative cooling. | E: Combine VLA (3-50 GHz) and IRAM (86-229 GHz) spectral flux densities to test for a spectral break and infer synchrotron cooling age. | R: The spectral index steepens from alpha = 0.712 ± 0.003 to 1.039 ± 0.008, revealing a break at 67.2 ± 1.2 GHz, corresponding to an age of 450 years for a single-zone continuous injection model with B = 4.4 mG. | F: The spectrum exhibits synchrotron cooling, though the inferred apparent speed implies that a multi-zone jet structure is needed rather than a simple one-zone model. | **supported**

## Reasoning

- Why this data: 3C 286 is the primary absolute polarization calibrator at radio frequencies, and long-term monitoring across ALMA, IRAM, and SMA is needed to establish its polarization stability and reference values into the submillimeter regime.  
  > "The combined data from these three monitoring programs allows for a precise investigation of the stability and properties of 3C 286 at millimeter and submillimeter wavelengths." (1 Introduction)
- Why this method: AMAPOLA provides automated, consistent reduction of ALMA polarimetric calibration scans, enabling statistical analysis across hundreds of epochs.  
  > "This is a set of CASA-friendly python scripts to reduce the ALMA polarimetric data, as described in (cite: kameno23). The dataset has been validated and used in previous studies of AGN jets" (2.1 ALMA)
- Alternative: Older SMA monitoring data over the past two decades were excluded due to inconsistencies in flux calibration and model transitions.  
  > "The total flux of 3C 286 has been monitored with SMA over the past two decades. However, we do not include these measurements in our analysis due to inconsistencies in the flux calibration process and transitions from older solar system models to the CASA-standard models during the monitoring." (2.3 SMA)
- Alternative: MeerKAT EVPA measurement at 1.4 GHz was excluded from the RM calculation due to frequency-dependent uncertainties up to 3 degrees.  
  > "We did not include chi=29.2 deg at 1.4 GHz obtained with MeerKAT in the RM calculation, due to its frequency-dependent uncertainties of up to 3 deg (see Figure 2 in (cite: taylor24))." (4.3 EVPA rotation as a function of frequency)
- How they decided it was enough: _not stated_
- Limitation (authors): Uranus pole brightening of 4% cannot explain the entire >10% flux decrease seen in ALMA Bands 6 and 7, indicating unquantified instrumental effects or short-term variations.  
  > "Nevertheless, the change in the brightness of Uranus alone cannot fully account for the decreasing trend observed in the ALMA measurements, as the magnitudes of the decrease in Band 6 and 7 exceed 10%." (3.1 Total flux)
- Limitation (authors): 3C 286 is observed at low elevation with ALMA (<37 deg) and has opposite RA to major planetary calibrators, making direct flux scaling harder.  
  > "However, 3C 286 is at low elevations for ALMA (with the maximum elevation of 37 deg) and its flux is relatively weak at higher frequencies. In addition, its flux calibration primarily relies on flux transfer from quasars, as its right ascension is opposite to the main planetary primary calibrators." (2.1 ALMA)
- Caveat (inferred, ours): The 229 GHz IRAM EVPA scatter is substantially higher than reported measurement errors, suggesting underestimated systematic uncertainties in the IRAM 1mm receiver polarization angle.
- Caveat (inferred, ours): A one-zone continuous injection synchrotron model overpredicts apparent jet speed, requiring qualitative multi-zone jet assumptions without spatially resolved millimeter VLBI verification.

## Reproducibility

- Data public (paper): ALMA calibration observations are publicly accessible under project code 2011.0.00001.CAL in the ALMA Science Archive, and AMAPOLA products are hosted on Zenodo.  
  > "This is a set of CASA-friendly python scripts to reduce the ALMA polarimetric data, as described in (cite: kameno23)." (2.1 ALMA); "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00001.CAL." (Conclusions)
- Products in archive: _not stated_
- Code: AMAPOLA reduction scripts are available via Zenodo.  
  > "AMAPOLA: ALMA Polarization Monitoring for Calibrator Sources, Zenodo. https://zenodo.org/records/10245760" (2.1 ALMA)
- Missing: Table listing individual ALMA execution blocks and exact AMAPOLA-processed polarization values per epoch.
- Data volume (inferred): 100 GB - 1 TB
- Score (inferred): 75/5, The paper uses publicly accessible calibrator monitoring data (2011.0.00001.CAL) reduced using an openly accessible Zenodo tool (AMAPOLA). Key analysis equations for linear trends, spectral breaks, synchrotron age, and power-law EVPA/RM fitting are explicit, and summary tables provide all derived values. A minor drawback is that individual per-epoch extracted Stokes values for all hundreds of ALMA scans are shown in figures rather than provided as a complete machine-readable table.
- Rediscovery candidate: yes, The raw ALMA calibrator monitoring data and AMAPOLA scripts are public. The mathematical model for EVPA rotation log(chi) = k*log(lambda^2) + C and |RM| vs frequency can be directly refit to verify the k, a, and reference polarization quantities.

## Links

- Method: (cite: kameno23) (AMAPOLA python scripts for ALMA polarimetric data reduction)
- Method: (cite: thum08) (XPOL polarimeter setup and calibration procedures on the IRAM 30m telescope)
- Method: (cite: govoni04) (Equipartition magnetic field formulation and parameters)
- Companion: (cite: perley13_pol) (VLA polarization monitoring reference values for 3C 286 from 1 to 50 GHz)
- Companion: (cite: kneissl23) (ALMA grid calibrator monitoring and investigation of Uranus brightness temperature variations)
- Related: POLAMI
- Related: MAPI
- Related: SMAPOL
- Related: ALMA Calibrator Survey / Grid Source Monitoring

## Checks

```json
{
 "quotes": 78,
 "quotes_ok": 60,
 "quote_pass_rate": 0.769,
 "quotes_too_long": 8,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00001.CAL"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 45,
  "rate": 0.584
 },
 "evidence_ok": false
}
```
