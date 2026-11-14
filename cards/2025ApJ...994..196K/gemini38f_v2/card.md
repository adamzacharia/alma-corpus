# Monitoring of 3C 286 with ALMA, IRAM, and SMA from 2006 to 2025: Stability, Synchrotron Ages, and Frequency-dependent Polarization Attributed to Core-shift

`2025ApJ...994..196K` | The Astrophysical Journal 2025 | first author: Kam, Minchul | arXiv: 2510.05540 | DOI: 10.3847/1538-4357/ae10b1

Card schema 1.0 | model gemini-3.8-flash | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars
- Question: To determine the long-term stability of the total flux, fractional polarization, and electric vector position angle (EVPA) of the calibrator quasar 3C 286 at millimeter and submillimeter wavelengths, and test models of synchrotron cooling and core-shift.  
  > "In this paper, we present the result of polarimetric observations of 3C 286 using ALMA, IRAM, and SMA at 91.5–343.4 GHz, spanning from October 2006 to February 2025." (Introduction); "The combined data from these three monitoring programs allows for a precise investigation of the stability and properties of 3C 286 at millimeter and submillimeter wavelengths." (Introduction)
- Target **3C 286**: coordinates _not stated_; z/distance z = 0.849  
  > "3C 286 is a quasar ($z=0.849$; (cite: burbidge69)) classified as a compact steep-spectrum (CSS) source" (Introduction); "At a redshift of $z$=0.849, this leads to a linear scale of 1 mas = 7.23 pc." (Introduction); distance from (cite: burbidge69)  
  > "3C 286 is a quasar ($z=0.849$; (cite: burbidge69)) classified as a compact steep-spectrum (CSS) source" (Introduction); "At a redshift of $z$=0.849, this leads to a linear scale of 1 mas = 7.23 pc." (Introduction)

## Data provenance

- ALMA projects: 2011.0.00001.CAL
- bands: Band 3, Band 6, Band 7  
  > "The data has been primarily obtained in Band 3 (91.5 and 103.5 GHz) and Band 7 (343.4 GHz) since May 2018. Data in Band 6 (233.0 GHz) has been obtained less frequently as a complement to the Band 7 data" (2.1 ALMA)
- frequencies and spectral setup: 91.5, 103.5, 233.0, and 343.4 GHz  
  > "ALMA at 91.5, 103.5, 233.0, and 343.4 GHz" (Abstract); "ALMA | 91.5
ALMA | 103.5
ALMA | 233.0
ALMA | 343.4" (Table 1)
- continuum bandwidth: _not stated_
- arrays: 7-m Array  
  > "About 40 bright calibrators, known as “grid sources" and evenly distributed across the sky, are observed with the 7-m Array at least every two weeks to provide secondary flux calibrators" (2.1 ALMA); "3C 286, a point-source calibrator for the ALMA 7-m Array, has been monitored as one of the grid sources" (2.1 ALMA)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2018 May to 2024 Dec (91.5, 103.5, 343.4 GHz); 2018 May to 2024 Aug (233.0 GHz)  
  > "ALMA | 91.5 | 2018 May - 2024 Dec. | 207 | 330
ALMA | 103.5 | 2018 May - 2024 Dec. | 191 | 330
ALMA | 233.0 | 2018 May - 2024 Aug. | 32 | 73
ALMA | 343.4 | 2018 May - 2024 Dec. | 132 | 260" (Table 1)
- pi or archival as stated: _not stated_
- Other facility **IRAM 30-m Telescope**: Polarimetric monitoring data at 86 and 229 GHz from October 2006 to May 2024 using the XPOL polarimeter under POLAMI, MAPI, and OJ 287 programs  
  > "3C 286 has been monitored with the IRAM 30-m Telescope at 86 and 229 GHz as part of the following three programs: the Polarimetric Monitoring of AGN at Millimeter Wavelengths (POLAMI) program" (2.2 The IRAM 30-m Telescope); "The monitoring of 3C 286 was performed with the XPOL polarimeter (cite: thum08) installed at the IRAM." (2.2 The IRAM 30-m Telescope)
- Other facility **Submillimeter Array (SMA)**: Polarimetric monitoring data at 225 GHz from June 2022 to February 2025 under the SMAPOL program  
  > "Consequently, we only included recent data which were calibrated using a consistent process and model under the SMAPOL program." (2.3 SMA); "SMA | 225 | 2022 Jun. - 2025 Feb. | 56 | 56" (Table 1)
- Other facility **Very Large Array (VLA)**: Archival total flux and polarization measurements from 1 to 50 GHz taken from Perley & Butler (2013a, 2013b)  
  > "For this comparison, we adopted the total flux measurements using VLA at 1–50 GHz (cite: perley13_flux), along with polarization measurements from the same instrument." (2.4 VLA)
- External data: VLA total flux measurements at 1-50 GHz  
  > "For this comparison, we adopted the total flux measurements using VLA at 1–50 GHz (cite: perley13_flux), along with polarization measurements from the same instrument." (2.4 VLA) [from (cite: perley13_flux)]
- External data: VLA EVPA measurements at 5, 15, 25, 33, and 45 GHz (weighted mean 1995-2012) and fractional polarization at 1.5, 4.9, 8.4, 15.0, 22.5, and 43.3 GHz (epoch 2000.0)  
  > "Specifically, we took the EVPA measurements at 5, 15, 25, 33, and 45 GHz from Table 2 in (cite: perley13_pol), representing the weighted mean of measurements obtained at each frequency from 1995 to 2012. The fractional polarization values were taken from Table 5 of (cite: perley13_pol)" (2.4 VLA) [from (cite: perley13_pol)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Solar system objects (SSOs) with Uranus serving as primary reference (ESA4 model)  
  > "Observations of the grid sources include a scan of any available solar system object (SSO), with Uranus serving as the primary reference (cite: remijan19)." (2.1 ALMA); "Specifically, the model for Uranus is based on the ESA4 model, and other SSOs are used with their flux scales referenced to Uranus within 5% uncertainties" (2.1 ALMA)
- flux scale uncertainty: < 5% in Band 3 and 10% in Bands 6 and 7  
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

- AMAPOLA calibration and polarimetric data reduction scripts for ALMA  
  > "For polarization analysis, we collected data reduced using the Analytic Matrix for ALMA POLArimetry (AMAPOLA). This is a set of CASA-friendly python scripts to reduce the ALMA polarimetric data, as described in (cite: kameno23)." (2.1 ALMA) [from (cite: kameno23)]
- IRAM 30m calibration, Kelvin-to-Jansky conversion factors, and XPOL processing  
  > "Consequently, the conversion factor was determined to be ($6.1\pm0.1$) Jy K$^{-1}$ and ($8.6\pm0.4$) Jy K$^{-1}$ for 86 and 229 GHz, respectively (cite: agudo18_1). These factors were applied to the entire data obtained from 2006 to 2024" (2.2 The IRAM 30-m Telescope) [from (cite: agudo18_1)]
- SMA polarization calibration procedure using MIR and MIRIAD  
  > "The initial data calibration such as flagging, bandpass, cross-receiver delays, complex gains, flux calibration, and RL-phase offset was performed using the MIR software package , and the instrumental polarization was calibrated with the MIRIAD (cite: sault95)." (2.3 SMA) [from (cite: sault95; marrone06; marrone08; myserlis25)]

### Not stated but needed to reproduce (our reading)

- Specific individual execution blocks / observation IDs for ALMA 7-m calibration scans
- AMAPOLA pipeline version and configuration parameters

## Analysis recipe

1. **Extract Stokes parameters and monitor total flux and polarization of 3C 286 with ALMA**: AMAPOLA python scripts for CASA polarimetric reduction of 7-m Array grid-source observations  
  > "For polarization analysis, we collected data reduced using the Analytic Matrix for ALMA POLArimetry (AMAPOLA). This is a set of CASA-friendly python scripts to reduce the ALMA polarimetric data, as described in (cite: kameno23)." (2.1 ALMA)
   - software: AMAPOLA, CASA
   - parameter: Frequencies: 91.5, 103.5, 233.0, 343.4 GHz  
  > "The data has been primarily obtained in Band 3 (91.5 and 103.5 GHz) and Band 7 (343.4 GHz) since May 2018. Data in Band 6 (233.0 GHz) has been obtained less frequently" (2.1 ALMA)
   - assumption: Planet flux calibration based on Butler-JPL-Horizons 2012 / ESA4 model for Uranus  
  > "The CASA brightness temperature models for planets follow the Butler-JPL-Horizons 2012 framework, as explained in ALMA memo 594 (cite: butler12). Specifically, the model for Uranus is based on the ESA4 model" (2.1 ALMA)
   - fitting: Linear regression over time: S_nu = c_0 * (t - 58000) + c_1  
  > "To further investigate the long-term trend in the ALMA data, we fitted all the total flux measurements at each frequency with the following function: S_{\nu} = c_0 \times (t-58000) + c_1" (3.1 Total flux)
   - validation: Division of ALMA data into three epochs (Period I, II, III) to check average flux and polarization values  
  > "To investigate this in further detail, we divided the ALMA data into three groups: the first, obtained between MJD 58230 and 59000, referred to as Period I, the second, obtained between MJD 59200 and 59900, referred to as Period II, and the third, after MJD 60100, referred to as Period III." (3.1 Total flux)
2. **Derive weighted reference values for flux, EVPA, and fractional polarization**: Weighted mean stacking across all epochs per frequency and instrument  
  > "Therefore, we provide the weighted mean of the EVPA and fractional polarization, as well as the total flux, as the reference values for 3C 286 (Table 2)." (3.2 Polarization)
   - parameter: Weighted mean combining all monitoring epochs  
  > "Therefore, we provide the weighted mean of the EVPA and fractional polarization, as well as the total flux, as the reference values for 3C 286 (Table 2)." (3.2 Polarization)
   - assumption: Intrinsic polarization properties are stationary over time  
  > "Likewise, long-term monitoring observations with ALMA and IRAM suggest that both EVPA and fractional polarization of 3C 286 have remained nearly constant over the last $\sim$20 years." (3.2 Polarization)
   - fitting: Weighted average  
  > "Therefore, we provide the weighted mean of the EVPA and fractional polarization, as well as the total flux, as the reference values for 3C 286 (Table 2)." (3.2 Polarization)
   - validation: Cross-instrument comparison between ALMA, IRAM, SMA, and VLA  
  > "In Figure 6, we present the reference values for the EVPA and fractional polarization of 3C 286, along with the values measured with VLA at 5–45 GHz (cite: perley13_pol)." (3.2 Polarization)
3. **Estimate synchrotron break frequency, spectral index, and source age**: Power-law fitting of flux density vs. frequency below and above break; continuous injection model calculation for synchrotron age  
  > "Specifically, the spectral index between 3 and 50 GHz, where the flux nearly follows a simple power-law, yields a spectral index of $\alpha=0.712\pm0.003$. In contrast, the spectral index between 86 and 229 GHz is $\alpha=1.039\pm0.008$" (4.1 Synchrotron cooling); "Assuming (i) a continuous injection model, where new relativistic electrons with a power-law energy distribution are continuously injected to the synchrotron-emitting source, (ii) no expansion of the emitting source, and (iii) constant magnetic field strength, the time elapsed after the formation of the emitting source, $\tau_{\rm syn}$ (in Myrs), can be expressed as (cite: murgia99; murgia03):" (4.2 Synchrotron age and magnetic field strength)
   - parameter: B_eq = 4.4 mG, k = 1, theta = 50 mas, d = 0.36 kpc, z = 0.849  
  > "Assuming an energy ratio between electrons and protons of $k=1$, as commonly adopted in the literature, these parameters yield an equipartition magnetic field strength of $B_{\rm eq}$$\sim$4.4 mG." (4.2 Synchrotron age and magnetic field strength); "Given that the total flux of 3C 286 at this frequency is dominated by emission within 50 mas from the core (cite: zhang94; jiang96; cotton97; an17), we adopt a source size of 50 mas. This corresponds to a depth of $d=3.6\times10^{-1}$ kpc" (4.2 Synchrotron age and magnetic field strength)
   - assumption: Equipartition between relativistic particles and magnetic fields; continuous injection synchrotron model  
  > "We estimate the average magnetic field strength in the emitting region by assuming the equipartition condition" (4.2 Synchrotron age and magnetic field strength)
   - fitting: Power law intersection finding the break frequency nu_br  
  > "This difference in spectral index between the two frequency ranges leads to a spectral break at $67.2\pm1.2$ GHz." (4.1 Synchrotron cooling)
   - validation: Checked sensitivity of equipartition magnetic field to energy ratio k  
  > "However, adopting $k=1836$ changes $B_{\rm eq}$ by only several factors ($B_{\rm eq}=31$ mG), indicating that $B_{\rm eq}$ is not highly sensitive to the choice of $k$." (4.2 Synchrotron age and magnetic field strength)
4. **Fit EVPA and fractional polarization vs wavelength squared, derive RM and test core-shift**: Weighted power-law fitting of EVPA vs lambda^2: log(chi) = k * log(lambda^2) + C, and fitting |RM_core,nu| proportional to nu^a  
  > "To investigate the frequency dependency of the RM in more detail, we fit all the EVPA values with a single power-law function of the form \mathrm{log(\chi)} = k\ \mathrm{log(\lambda^2) + C}" (4.3 EVPA rotation as a function of frequency); "The best-fit line represents $\mid$RM core,$\nu$\mid\propto \nu^{a}$ with the power-law index $a=2.05\pm0.06$" (4.3 EVPA rotation as a function of frequency)
   - parameter: Wavelength lambda in cm, EVPA chi in degrees, rest-frame RM = (1+z)^2 * RM_obs  
  > "where $\chi$ is the EVPA, and $\lambda$ is the wavelength in centimeter (Figure 8)." (4.3 EVPA rotation as a function of frequency); "$\rm \left|RM_{\rm rest}\right| = (1+z)^2 \left|RM_{\rm obs}\right|$" (4.3 EVPA rotation as a function of frequency)
   - assumption: Blandford & Konigl conical jet model with core-shift  
  > "This result aligns with the power-law index of $a=2$ expected for the core-shift effect in the BK conical jet model, suggesting that the observed EVPA rotation in 3C 286 can be explained in this framework." (4.3 EVPA rotation as a function of frequency)
   - fitting: Weighted linear least-squares in log-log space  
  > "The resulting coefficients from the weighted fit are $k=-0.016\pm0.002$ and $\rm C=1.547\pm0.003$." (4.3 EVPA rotation as a function of frequency)
   - validation: Comparison with theoretical expectation a=2 from Blandford & Konigl conical jet model  
  > "The best-fit line represents $\mid$RM core,$\nu$\mid\propto \nu^{a}$ with the power-law index $a=2.05\pm0.06$, which is consistent with the theoretically expected value of $a=2$ for the BK conical jet model." (4.3 EVPA rotation as a function of frequency)

## Software

- **CASA** : Planet brightness temperature modeling and execution environment for AMAPOLA scripts  
  > "The CASA brightness temperature models for planets follow the Butler-JPL-Horizons 2012 framework, as explained in ALMA memo 594 (cite: butler12)." (2.1 ALMA); "This is a set of CASA-friendly python scripts to reduce the ALMA polarimetric data, as described in (cite: kameno23)." (2.1 ALMA)
- **AMAPOLA** : Reduction of ALMA polarimetric monitoring data for calibrator sources  
  > "For polarization analysis, we collected data reduced using the Analytic Matrix for ALMA POLArimetry (AMAPOLA). This is a set of CASA-friendly python scripts to reduce the ALMA polarimetric data, as described in (cite: kameno23)." (2.1 ALMA)
- **MIR** : Initial calibration of SMA data (flagging, bandpass, delays, gains, flux calibration, RL-phase offset)  
  > "The initial data calibration such as flagging, bandpass, cross-receiver delays, complex gains, flux calibration, and RL-phase offset was performed using the MIR software package" (2.3 SMA)
- **MIRIAD** : Instrumental polarization calibration of SMA data  
  > "and the instrumental polarization was calibrated with the MIRIAD (cite: sault95)." (2.3 SMA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA Band 3 91.5 GHz reference EVPA | 36.74 | 0.03 | deg | 2 | ALMA / 91.5 / $-$ / $36.74\pm0.03$ / $14.32\pm0.03$ |
| ALMA Band 3 91.5 GHz reference fractional polarization | 14.32 | 0.03 | % | 2 | ALMA / 91.5 / $-$ / $36.74\pm0.03$ / $14.32\pm0.03$ |
| ALMA Band 3 103.5 GHz reference EVPA | 36.57 | 0.04 | deg | 2 | ALMA / 103.5 / $-$ / $36.57\pm0.04$ / $14.50\pm0.04$ |
| ALMA Band 3 103.5 GHz reference fractional polarization | 14.50 | 0.04 | % | 2 | ALMA / 103.5 / $-$ / $36.57\pm0.04$ / $14.50\pm0.04$ |
| ALMA Band 6 233.0 GHz reference EVPA | 37.14 | 0.06 | deg | 2 | ALMA / 233.0 / $-$ / $37.14\pm0.06$ / $16.07\pm0.07$ |
| ALMA Band 6 233.0 GHz reference fractional polarization | 16.07 | 0.07 | % | 2 | ALMA / 233.0 / $-$ / $37.14\pm0.06$ / $16.07\pm0.07$ |
| ALMA Band 7 343.4 GHz reference EVPA | 38.93 | 0.08 | deg | 2 | ALMA / 343.4 / $-$ / $38.93\pm0.08$ / $16.37\pm0.07$ |
| ALMA Band 7 343.4 GHz reference fractional polarization | 16.37 | 0.07 | % | 2 | ALMA / 343.4 / $-$ / $38.93\pm0.08$ / $16.37\pm0.07$ |
| IRAM 86 GHz reference total flux | 0.892 | 0.004 | Jy | 2 | IRAM / 86 / $0.892\pm0.004$ / $36.84\pm0.10$ / $13.83\pm0.08$ |
| IRAM 229 GHz reference total flux | 0.323 | 0.003 | Jy | 2 | IRAM / 229 / $0.323\pm0.003$ / $35.75\pm0.64$ / $14.48\pm0.38$ |
| Spectral break frequency | 67.2 | 1.2 | GHz | 3 | 3–50 / $0.712\pm0.003$ / $67.2\pm1.2$ / $1.2\pm0.1$ |
| Spectral break flux density S_br | 1.2 | 0.1 | Jy | 3 | 3–50 / $0.712\pm0.003$ / $67.2\pm1.2$ / $1.2\pm0.1$ |
| Spectral index 3-50 GHz | 0.712 | 0.003 | dimensionless | 3 | 3–50 / $0.712\pm0.003$ / $67.2\pm1.2$ / $1.2\pm0.1$ |
| Spectral index 86-229 GHz | 1.039 | 0.008 | dimensionless | 3 | 86–229 / $1.039\pm0.008$ |
| Synchrotron age tau_syn | 450 | not stated | yr | 3 | Substituting the magnetic field strength of 4.4 mG into Equation [eq:tau_syn], we derive the age of 3C 286 to be $\tau_{\rm syn}$=450 years. |
| Power-law index a of Faraday RM vs frequency | 2.05 | 0.06 | dimensionless | 4 | The best-fit line represents $\mid$RM core,$\nu$\mid\propto \nu^{a}$ with the power-law index $a=2.05\pm0.06$, which is consistent with the theoretically expected value of $a=2$ for the BK conical jet model. |
| EVPA vs lambda^2 power-law slope k | -0.016 | 0.002 | dimensionless | 4 | The resulting coefficients from the weighted fit are $k=-0.016\pm0.002$ and $\rm C=1.547\pm0.003$. |
| Rest-frame RM between 233 and 343 GHz | 3.2e4 | 1.5e4 | rad m^-2 | 4 | 233 / 343 / 282.7 / $(9.1\pm3.8)\times10^3$ / 522.7 / $(3.2\pm1.5)\times10^4$ |

## Qualitative findings

- The total flux of 3C 286 has remained stable up to 229 GHz over 2006-2024; the apparent decrease of 2-15% seen in ALMA data is partially due to the unmodeled brightening of Uranus (up to 4%) and possibly other instrumental/atmospheric factors.  
  > "The IRAM measurements from 2006 to 2024 show that the total flux of 3C 286 is stable within measurement uncertainties, indicating long-term stability up to 229 GHz, when applying a fixed Kelvin-to-Jansky conversion factor throughout its dataset." (Abstract); "ALMA data from 2018 to 2024 exhibit a decrease in flux, which up to 4% could be attributed to an apparent increase in the absolute brightness of Uranus, the primary flux calibrator for ALMA with the ESA4 model." (Abstract)
- EVPA and fractional polarization are stable across all millimeter/submillimeter observing frequencies over the 20-year period.  
  > "The polarization properties of 3C 286 are stable across all observing frequencies." (Abstract); "Likewise, long-term monitoring observations with ALMA and IRAM suggest that both EVPA and fractional polarization of 3C 286 have remained nearly constant over the last $\sim$20 years." (3.2 Polarization)
- The EVPA rotation and increasing Faraday RM with frequency are consistent with core-shift in a Blandford & Konigl conical jet, accompanied by reduced Faraday depolarization at shorter wavelengths.  
  > "The Faraday rotation measure increases as a function of frequency up to $\rm (3.2\pm1.5)\times10^4\ rad\ m^{-2}$, following $\mid$RM$\mid\propto \nu$^$\alpha$^ with $\alpha=2.05\pm0.06$. This trend is consistent with the core-shift effect expected in a conical jet." (Abstract)

## Claim tuples

- H: The intrinsic millimeter/submillimeter total flux of 3C 286 is stable over multi-year baselines. | E: Long-term monitoring with IRAM (2006-2024 at 86 and 229 GHz) and ALMA (2018-2024 at 91.5-343.4 GHz) combined with analysis of Uranus calibration variations. | R: IRAM measurements show constant flux within uncertainties (change of -2% at 86 GHz and +9% at 229 GHz), while ALMA apparent declines (2% to 15%) can be partially explained by a ~4% brightening of Uranus. | F: The intrinsic total flux of 3C 286 has remained stable up to 229 GHz over the 20-year period. | **supported**
- H: The EVPA of 3C 286 gradually rotates as a function of frequency due to core-shift in a conical jet. | E: Fit EVPA values from 5 GHz to 343.4 GHz with a single power-law function of wavelength squared and derive the frequency-dependent RM. | R: RM increases from 23 rad m^-2 to 3.2 x 10^4 rad m^-2 in the rest frame, scaling as nu^a with a = 2.05 +/- 0.06. | F: The observed frequency-dependent EVPA rotation is consistent with the core-shift effect predicted by the Blandford & Konigl conical jet model where a = 2. | **supported**
- H: The continuous increase in fractional polarization with frequency is driven by reduced Faraday depolarization at shorter wavelengths. | E: Fit fractional polarization as a function of wavelength squared from 1.5 GHz to 343.4 GHz with a single power law. | R: Fractional polarization follows log(m) = k' log(lambda^2) + C' with k' = -0.047 +/- 0.001 across four orders of magnitude in lambda^2. | F: Faraday depolarization decreases at shorter wavelengths because lambda^2 decreases much faster than RM increases. | **supported**

## Reasoning

- Why this data: Combining ALMA 7-m, IRAM 30-m, and SMA observations provides unprecedented frequency coverage (86 to 343.4 GHz) and time baseline (2006 to 2025) for high-accuracy millimeter/submillimeter polarimetry of a primary radio calibrator.  
  > "In this paper, we present the result of polarimetric observations of 3C 286 using ALMA, IRAM, and SMA at 91.5–343.4 GHz, spanning from October 2006 to February 2025. The combined data from these three monitoring programs allows for a precise investigation" (Introduction)
- Why this method: Stacking the stable polarimetric monitoring data allows derivation of reference EVPA and polarization fractions with sub-percent and sub-degree statistical uncertainties, resolving previously discordant millimeter measurements.  
  > "This stability allows us to obtain the fractional polarization and EVPA values with unprecedented accuracy at millimeter/submillimeter wavelengths by stacking all the data." (3.2 Polarization)
- Alternative: Excluded historical SMA data before June 2022 because changes in solar system models and calibration inconsistencies introduced unquantified systematic flux offsets.  
  > "However, we do not include these measurements in our analysis due to inconsistencies in the flux calibration process and transitions from older solar system models to the CASA-standard models during the monitoring." (2.3 SMA)
- Alternative: Excluded MeerKAT 1.4 GHz EVPA (29.2 deg) from the RM calculation due to large frequency-dependent uncertainties up to 3 deg.  
  > "We did not include $\chi=29.2^\circ$ at 1.4 GHz obtained with MeerKAT in the RM calculation, due to its frequency-dependent uncertainties of up to 3$^{\circ}$ (see Figure 2 in (cite: taylor24))." (Footnote 20)
- Alternative: Rejected a one-zone continuous injection synchrotron model for the entire source because it implies an apparent expansion speed (beta_app = 2.6) much faster than observed in the inner jet (beta_app = 0.6).  
  > "However, these apparent speeds are significantly faster than the apparent speed $\beta_{\rm app}=0.6\pm0.5$ observed in the inner jet at 5 mas from the core (cite: an17)." (4.2 Synchrotron age and magnetic field strength); "This discrepancy suggests that the spectrum may not represent the age of the entire jet, but instead may partially represent the age of electrons that were accelerated in situ as the jet propagates through the ambient medium." (4.2 Synchrotron age and magnetic field strength)
- How they decided it was enough: _not stated_
- Limitation (authors): The 4% brightening of Uranus cannot fully explain the >10% flux decrease observed in ALMA Bands 6 and 7, indicating additional unmodeled atmospheric or instrumental effects.  
  > "Nevertheless, the change in the brightness of Uranus alone cannot fully account for the decreasing trend observed in the ALMA measurements, as the magnitudes of the decrease in Band 6 and 7 exceed 10%." (3.1 Total flux)
- Limitation (authors): IRAM EVPA uncertainties at 229 GHz appear underestimated, given an average formal uncertainty of 5.1 deg versus an observed scatter of 9.6 deg.  
  > "Moreover, the average of the EVPA uncertainties for IRAM at 229 GHz is 5.1$^{\circ}$, while the standard deviation of those measurements is 9.6$^{\circ}$. This discrepancy suggests that the EVPA uncertainties for IRAM may have been underestimated." (3.2 Polarization)
- Caveat (inferred, ours): ALMA calibration scans were taken with the 7-m compact array, potentially affected by elevation limits and transfer calibration uncertainties since 3C 286 peaks at low elevation (<37 deg).
- Caveat (inferred, ours): Underlying jet sub-structure (C1 vs C2) is unresolved by the single-dish and compact interferometer beams, requiring multi-zone interpretation rather than a pure single-component jet.

## Reproducibility

- Data public (paper): ALMA calibration data are public under project code ADS/JAO.ALMA#2011.0.00001.CAL  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00001.CAL." (Conclusions)
- Products in archive: _not stated_
- Code: AMAPOLA python scripts for ALMA polarization calibration are available via Zenodo  
  > "For polarization analysis, we collected data reduced using the Analytic Matrix for ALMA POLArimetry (AMAPOLA). This is a set of CASA-friendly python scripts to reduce the ALMA polarimetric data, as described in (cite: kameno23)." (2.1 ALMA); "https://www.alma.cl/~skameno/AMAPOLA/" (Footnote 5)
- Missing: Specific execution block IDs for the hundreds of ALMA calibration scans of 3C 286
- Missing: Tabulated time-series data points for IRAM, SMA, and ALMA to reproduce the individual regressions without scraping figures
- Data volume (inferred): 500 GB - 2 TB
- Score (inferred): 7/5, The ALMA calibration data and reduction pipeline (AMAPOLA) are public, and the analytical fitting functions (power-law regressions) are mathematically explicit. However, exact reproduction requires downloading hundreds of grid-calibrator execution blocks from 2018-2024 from project 2011.0.00001.CAL and combining them with external IRAM/SMA datasets.
- Rediscovery candidate: yes, The core finding—the reference EVPA and fractional polarization values for 3C 286 across ALMA bands—can be directly recalculated by downloading the ALMA 7-m calibration scans under 2011.0.00001.CAL and executing AMAPOLA.

## Links

- Method: (cite: kameno23) (Describes the AMAPOLA polarimetry calibration pipeline for ALMA)
- Method: (cite: thum08) (Describes the XPOL polarimeter and standard calibration at IRAM 30m)
- Method: (cite: sault95) (Describes MIRIAD software used for SMA polarimetric calibration)
- Companion: (cite: kneissl23) (ALMA grid source monitoring and Uranus brightness trend analysis)
- Companion: (cite: agudo18_1) (POLAMI monitoring program at IRAM 30-m providing initial 3C 286 dataset and conversion factors)
- Related: POLAMI
- Related: MAPI
- Related: SMAPOL

## Checks

```json
{
 "quotes": 94,
 "quotes_ok": 82,
 "quote_pass_rate": 0.872,
 "quotes_too_long": 6,
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
  "facts": 84,
  "stated": 53,
  "rate": 0.631
 },
 "evidence_ok": false
}
```
