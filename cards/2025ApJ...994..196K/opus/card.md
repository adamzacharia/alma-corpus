# Monitoring of 3C 286 with ALMA, IRAM, and SMA from 2006 to 2025: Stability, Synchrotron Ages, and Frequency-dependent Polarization Attributed to Core-shift

`2025ApJ...994..196K` | The Astrophysical Journal 2025 | first author: Kam, Minchul | arXiv: 2510.05540 | DOI: 10.3847/1538-4357/ae10b1

Card schema 1.0 | model claude-opus-5-5 | depth full | type technical_calibration_or_instrument

## Science

- Fields: agn_and_quasars, instrumentation
- Question: Are the total flux, fractional polarization and EVPA of 3C 286 stable at mm/submm wavelengths, and what explains their frequency dependence (synchrotron cooling, core-shift, Faraday rotation)?  
  > "The combined data from these three monitoring programs allows for a precise investigation of the stability and properties of 3C 286 at millimeter and submillimeter wavelengths." (Introduction)
- Target **3C 286**: coordinates _not stated_; z/distance z=0.849  
  > "3C 286 is a quasar ($z=0.849$; (cite: burbidge69)) classified as a compact steep-spectrum (CSS) source" (Introduction); "At a redshift of $z$=0.849, this leads to a linear scale of 1 mas = 7.23 pc." (Introduction); distance from (cite: burbidge69); cosmology from (cite: riess22)  
  > "3C 286 is a quasar ($z=0.849$; (cite: burbidge69)) classified as a compact steep-spectrum (CSS) source" (Introduction); "At a redshift of $z$=0.849, this leads to a linear scale of 1 mas = 7.23 pc." (Introduction)

## Data provenance

- ALMA projects: 2011.0.00001.CAL
- bands: Band 3 (91.5 and 103.5 GHz), Band 6 (233.0 GHz), Band 7 (343.4 GHz)  
  > "The data has been primarily obtained in Band 3 (91.5 and 103.5 GHz) and Band 7 (343.4 GHz) since May 2018." (2.1 ALMA); "Data in Band 6 (233.0 GHz) has been obtained less frequently as a complement to the Band 7 data" (2.1 ALMA)
- frequencies and spectral setup: 91.5, 103.5, 233.0, 343.4 GHz; full polarization mode (all four Stokes)  
  > "The observations of 3C 286 were performed with a full polarization mode to obtain all four Stokes parameters." (2.1 ALMA)
- continuum bandwidth: _not stated_
- arrays: ALMA 7-m Array (grid source monitoring)  
  > "About 40 bright calibrators, known as “grid sources" and evenly distributed across the sky, are observed with the 7-m Array at least every two weeks" (2.1 ALMA)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2018 May - 2024 Dec. (Band 6: 2018 May - 2024 Aug.)  
  > "2018 May - 2024 Dec." (Table 1)
- pi or archival as stated: ALMA calibrator (grid source) monitoring data reduced with AMAPOLA  
  > "For polarization analysis, we collected data reduced using the Analytic Matrix for ALMA POLArimetry" (2.1 ALMA)
- Other facility **IRAM 30-m Telescope (XPOL)**: Total flux and polarization at 86 and 229 GHz, 2006-2024 (POLAMI, MAPI, OJ 287 programs); Uranus flux monitoring  
  > "3C 286 has been monitored with the IRAM 30-m Telescope at 86 and 229 GHz as part of the following three programs" (2.2 The IRAM 30-m Telescope)
- Other facility **SMA (SMAPOL)**: Polarization at 225 GHz, 2022 Jun. - 2025 Feb.  
  > "Consequently, we only included recent data which were calibrated using a consistent process and model under the SMAPOL" (2.3 SMA)
- Other facility **VLA (literature)**: Total flux at 1-50 GHz, EVPA and fractional polarization at cm wavelengths  
  > "we adopted the total flux measurements using VLA at 1–50 GHz (cite: perley13_flux), along with polarization measurements from the same instrument." (2.4 VLA)
- External data: VLA total flux at 1-50 GHz  
  > "we adopted the total flux measurements using VLA at 1–50 GHz (cite: perley13_flux)" (2.4 VLA) [from (cite: perley13_flux)]
- External data: VLA EVPA at 5, 15, 25, 33, 45 GHz (Table 2)  
  > "we took the EVPA measurements at 5, 15, 25, 33, and 45 GHz from Table 2 in (cite: perley13_pol)" (2.4 VLA) [from (cite: perley13_pol)]
- External data: VLA fractional polarization (Table 5), epoch 2000.0  
  > "The fractional polarization values were taken from Table 5 of (cite: perley13_pol)" (2.4 VLA) [from (cite: perley13_pol)]
- External data: I0 = 7.297 Jy at 4.885 GHz for equipartition field  
  > "the total flux of $I_{0}$=7.297 Jy at $\nu_0$=4.885 GHz" (4.2 Synchrotron age and magnetic field strength) [from (cite: perley13_flux)]
- External data: Equipartition parameter xi = 1.23e-12  
  > "We adopt $\xi(\alpha, \nu_1, \nu_2)=1.23\times10^{-12}$, which is given for $\alpha\sim0.7$ between the turnover and break frequencies (cite: govoni04)" (4.2 Synchrotron age and magnetic field strength) [from (cite: govoni04)]
- External data: IRAM Kelvin-to-Jansky conversion factors (6.1±0.1) and (8.6±0.4) Jy/K  
  > "the conversion factor was determined to be ($6.1\pm0.1$) Jy K$^{-1}$ and ($8.6\pm0.4$) Jy K$^{-1}$ for 86 and 229 GHz, respectively (cite: agudo18_1)" (2.2 The IRAM 30-m Telescope) [from (cite: agudo18_1)]
- External data: ALMA Uranus/Neptune brightness ratio showing 4% Uranus increase  
  > "the ratio of the brightness of Uranus to Neptune, monitored with ALMA from 2018 to 2024, also suggests that the brightness of Uranus has increased by 4% during the monitoring period" (3.1 Total flux) [from (cite: kneissl23)]
- External data: Inner jet apparent speed beta_app = 0.6±0.5  
  > "the apparent speed $\beta_{\rm app}=0.6\pm0.5$ observed in the inner jet at 5 mas from the core (cite: an17)" (4.2 Synchrotron age and magnetic field strength) [from (cite: an17)]
- Simulation/model as data: Uranus ESA4 brightness model and Lellouch & Amri Mars model for flux scales  
  > "For Uranus, the ESA4 model used for the Herschel Space Observatory mission (cite: bendo13; griffin13; orton14) was adopted." (2.2 The IRAM 30-m Telescope)

## Processing

### Calibration

- pipeline or manual: ALMA polarimetric calibrator data reduced with AMAPOLA scripts  
  > "This is a set of CASA-friendly python scripts to reduce the ALMA polarimetric data" (2.1 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: AMAPOLA-reduced measurements collected  
  > "For polarization analysis, we collected data reduced using the Analytic Matrix for ALMA POLArimetry" (2.1 ALMA)
- flux calibrator: Uranus (ESA4 model) as primary reference; other SSOs referenced to Uranus within 5%  
  > "Observations of the grid sources include a scan of any available solar system object (SSO), with Uranus serving as the primary reference" (2.1 ALMA); "Specifically, the model for Uranus is based on the ESA4 model" (2.1 ALMA)
- flux scale uncertainty: <5% in Band 3, 10% in Bands 6 and 7  
  > "the uncertainties originating from the absolute flux calibration are typically less than 5% in Band 3 and 10% in Bands 6 and 7" (2.1 ALMA)
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

- ALMA polarimetric reduction via AMAPOLA  
  > "This is a set of CASA-friendly python scripts to reduce the ALMA polarimetric data, as described in (cite: kameno23)." (2.1 ALMA) [from (cite: kameno23)]
- IRAM XPOL setup and calibration  
  > "The standard XPOL setup and calibration processes summarized in (cite: thum08) has been maintained throughout the monitoring" (2.2 The IRAM 30-m Telescope) [from (cite: thum08; agudo10; agudo12; agudo18_3; agudo18_1; thum18_2)]
- IRAM conversion factor applied to the full 2006-2024 dataset, reprocessed  
  > "we have reprocessed the entire dataset using the conversion factor from (cite: agudo18_1)" (2.2 The IRAM 30-m Telescope) [from (cite: agudo18_1)]
- Synchrotron age formula under continuous injection  
  > "can be expressed as (cite: murgia99; murgia03):" (4.2 Synchrotron age and magnetic field strength) [from (cite: murgia99; murgia03)]
- Equipartition magnetic field formula  
  > "the energy densities of relativistic particles and magnetic fields are approximately equal (cite: govoni04)" (4.2 Synchrotron age and magnetic field strength) [from (cite: govoni04)]

### Not stated but needed to reproduce (our reading)

- Individual per-epoch ALMA flux/EVPA/polarization values and their uncertainties (AMAPOLA version/download date)
- How ALMA measurements were weighted in the weighted means and linear fits
- Exact frequencies and method used to fit the spectral break (how alpha 3-50 GHz was fit, which VLA points used)
- The ten representative frequencies sampled from the EVPA model curve and the fitting code for the RM power law
- How N_tot differs from N_pol selection (why fewer total flux points than polarization points)
- IRAM per-epoch data, which are not described as public

## Analysis recipe

1. **assemble multi-instrument monitoring data**: Collect ALMA AMAPOLA, IRAM XPOL and SMAPOL measurements of total flux, fractional polarization and EVPA  
  > "For polarization analysis, we collected data reduced using the Analytic Matrix for ALMA POLArimetry" (2.1 ALMA)
   - software: AMAPOLA, CASA, MIR, MIRIAD
   - fitting: _not stated_
   - validation: IRAM polarization cross-checked with Crab Nebula  
  > "To cross-check the results of the polarization calibration, the Crab Nebula was observed" (2.2 The IRAM 30-m Telescope)
2. **test temporal stability**: Average in Periods I-III and fit linear trend S = c0 (t-58000) + c1  
  > "the first, obtained between MJD 58230 and 59000, referred to as Period I, the second, obtained between MJD 59200 and 59900, referred to as Period II" (3.1 Total flux); "we fitted all the total flux measurements at each frequency with the following function:" (3.1 Total flux)
   - fitting: linear fit  
  > "To further investigate the long-term trend in the ALMA data, we fitted all the total flux measurements at each frequency with the following function:" (Results > Total flux)
   - validation: Compare secular change with standard deviation and measurement uncertainties  
  > "However, the declines of 11% at 233.0 GHz and 15% at 343.4 GHz exceed the typical uncertainties of 10% in Bands 6 and 7." (3.1 Total flux)
3. **assess Uranus brightening**: Fit linear trend to IRAM 86 GHz Uranus residual flux relative to ESA4 model  
  > "to the entire residual flux indicates a systematic increase of 6.6%$\pm$1.5% from 2006 to 2024" (3.1 Total flux)
   - fitting: _not stated_
   - validation: _not stated_
4. **derive reference values**: Weighted mean of EVPA, fractional polarization and flux over all epochs  
  > "Therefore, we provide the weighted mean of the EVPA and fractional polarization, as well as the total flux, as the reference values for 3C 286" (3.2 Polarization)
   - fitting: _not stated_
   - validation: _not stated_
5. **spectral index and break**: Power-law spectral index 3-50 GHz (VLA) and 86-229 GHz (IRAM only), intersection gives break  
  > "we use only the IRAM measurements to determine the spectral index, as the ALMA flux appears to vary with different rates in different frequency bands." (4.1 Synchrotron cooling)
   - fitting: _not stated_
   - validation: Break shifts to 71.4 GHz if IRAM fluxes underestimated by ~2%  
  > "if the IRAM flux measurements were underestimated by $\sim2\%$, the break frequency is shifted to 71.4 GHz." (4.1 Synchrotron cooling)
6. **equipartition field and synchrotron age**: Equipartition B (Govoni & Feretti) and continuous-injection age formula  
  > "Substituting the magnetic field strength of 4.4 mG into Equation [\[eq:tau_syn\]](#eq:tau_syn), we derive the age of 3C 286" (4.2 Synchrotron age and magnetic field strength)
   - parameter: source size 50 mas (depth 0.36 kpc, spherical)  
  > "we adopt a source size of 50 mas. This corresponds to a depth of $d=3.6\times10^{-1}$ kpc, assuming a spherical geometry for simplicity." (4.2 Synchrotron age and magnetic field strength)
   - assumption: k=1 proton/electron energy ratio  
  > "Assuming an energy ratio between electrons and protons of $k=1$, as commonly adopted in the literature" (4.2 Synchrotron age and magnetic field strength)
   - assumption: continuous injection, no expansion, constant B  
  > "(ii) no expansion of the emitting source, and (iii) constant magnetic field strength" (4.2 Synchrotron age and magnetic field strength)
   - fitting: _not stated_
   - validation: B_eq sensitivity to I0 (<~6%) and k (31 mG for k=1836)  
  > "$B_{\rm eq}$ varies by less than $\sim$6% when using other values of $I_0$ at frequencies between 1–40 GHz" (4.2 Synchrotron age and magnetic field strength)
7. **EVPA vs lambda^2 fit and RM**: Weighted single power-law fit log(chi)=k log(lambda^2)+C; sample model at ten frequencies and compute RM between adjacent pairs  
  > "we sample the EVPA values along the best-fit curve at ten representative frequencies and calculate the best-fit RM values between adjacent pairs." (4.3 EVPA rotation as a function of frequency)
   - parameter: MeerKAT 1.4 GHz point excluded  
  > "We did not include $\chi=29.2^\circ$ at 1.4 GHz obtained with MeerKAT in the RM calculation" (4.3 EVPA rotation as a function of frequency)
   - assumption: RM_rest = (1+z)^2 RM_obs  
  > "This corresponds to an increase from $\rm 23\ rad\ m^{-2}$ to $\rm 32000\ rad\ m^{-2}$ in the rest frame, where the rest frame RM is defined as" (EVPA rotation as a function of frequency)
   - fitting: weighted fit  
  > "The resulting coefficients from the weighted fit are $k=-0.016\pm0.002$ and $\rm C=1.547\pm0.003$." (4.3 EVPA rotation as a function of frequency)
   - validation: _not stated_
8. **RM frequency dependence**: Power-law fit |RM| ∝ ν^a in rest frame, compare with BK conical jet a=2  
  > "with the power-law index $a=2.05\pm0.06$, which is consistent with the theoretically expected value of $a=2$ for the BK conical jet model." (4.3 EVPA rotation as a function of frequency)
   - fitting: _not stated_
   - validation: _not stated_
9. **fractional polarization vs lambda^2**: Single power-law fit log(m)=k' log(lambda^2)+C'  
  > "we fit the fractional polarization values with a single power-law function of the form:" (4.4 Depolarization mechanism)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **AMAPOLA** : ALMA polarimetric data reduction  
  > "This is a set of CASA-friendly python scripts to reduce the ALMA polarimetric data" (2.1 ALMA)
- **CASA** : Planet brightness temperature models (Butler-JPL-Horizons 2012)  
  > "The CASA brightness temperature models for planets follow the Butler-JPL-Horizons 2012 framework" (2.1 ALMA)
- **MIR** : SMA initial calibration  
  > "RL-phase offset was performed using the MIR software package" (2.3 SMA)
- **MIRIAD** : SMA instrumental polarization calibration  
  > "the instrumental polarization was calibrated with the MIRIAD (cite: sault95)" (2.3 SMA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA flux decrease over monitoring (91.5/103.5/233.0/343.4 GHz) | 4%, 2%, 11%, 15% | not stated | % | 2 | The decrease of 4% at 91.5 GHz and 2% at 103.5 GHz might not be significant given the typical measurement uncertainty of 5% in Band 3 |
| Expected 91.5 GHz flux from IRAM spectral index | 0.84 | not stated | Jy | 5 | is 0.84 Jy. This is 5% larger than the 0.80 Jy measured with ALMA at the same frequency |
| Uranus residual flux increase 2006-2024 (IRAM 86 GHz) | 6.6 | 1.5 | % | 3 | to the entire residual flux indicates a systematic increase of 6.6%$\pm$1.5% from 2006 to 2024 |
| ALMA reference EVPA at 343.4 GHz | 38.9 | 0.1 | deg | 4 | from $33.0^\circ\pm1.0^\circ$ at 5 GHz to $38.9^\circ\pm0.1^\circ$ at 343.4 GHz. |
| Fractional polarization at 343.4 GHz | 16.4 | 0.1 | % | 4 | from $8.6\%$ at 1.1 GHz to $16.4\%\pm0.1\%$ at 343.4 GHz. |
| Spectral index 3-50 GHz | 0.712 | 0.003 | dimensionless | 5 | yields a spectral index of $\alpha=0.712\pm0.003$ |
| Spectral index 86-229 GHz | 1.039 | 0.008 | dimensionless | 5 | In contrast, the spectral index between 86 and 229 GHz is $\alpha=1.039\pm0.008$ |
| Break frequency | 67.2 | 1.2 | GHz | 5 | leads to a spectral break at $67.2\pm1.2$ GHz |
| Equipartition magnetic field | 4.4 | not stated | mG | 6 | these parameters yield an equipartition magnetic field strength of $B_{\rm eq}$$\sim$4.4 mG |
| Synchrotron age | 450 | not stated | years | 6 | we derive the age of 3C 286 to be $\tau_{\rm syn}$=450 years |
| Implied average apparent speed | 2.6 | not stated | c (beta_app) | 6 | this age implies an average apparent speed $\beta_{\rm app}=2.6$ |
| Outer jet synchrotron age (3.6 GHz break scenario) | 1950 | not stated | years | 6 | the inferred synchrotron age of the outer jet becomes 1950 years |
| EVPA power-law slope k and intercept C | k=-0.016, C=1.547 | ±0.002, ±0.003 | dimensionless | 7 | The resulting coefficients from the weighted fit are $k=-0.016\pm0.002$ and $\rm C=1.547\pm0.003$. |
| Maximum rest-frame RM (233-343 GHz) | 3.2e4 | 1.5e4 | rad m^-2 | 7 | The Faraday rotation measure increases as a function of frequency up to $\rm (3.2\pm1.5)\times10^4\ rad\ m^{-2}$ |
| Observed-frame RM range 5-343 GHz | 6.5 to 9100 | not stated | rad m^-2 | 7 | We find that the absolute value of the RM between 5 and 343 GHz increases from $\rm 6.5\ rad\ m^{-2}$ to $\rm 9100\ rad\ m^{-2}$ in the observing frame. |
| RM power-law index a | 2.05 | 0.06 | dimensionless | 8 | with the power-law index $a=2.05\pm0.06$ |
| Fractional polarization power-law k' and C' | k'=-0.047, C'=1.108 | ±0.001, ±0.001 | dimensionless | 9 | with coefficients $k'=-0.047\pm0.001$ and $\rm C'=1.108\pm0.001$ |

## Qualitative findings

- ALMA polarization (fractional pol and EVPA) shows no secular change across Periods I-III  
  > "In contrast to the total flux, no secular changes are observed in the fractional polarization and EVPA measured with ALMA" (3.2 Polarization)
- IRAM total flux shows no clear decreasing trend at 86 and 229 GHz  
  > "the total flux measurements obtained with IRAM do not exhibit any clear decreasing trend at both 86 and 229 GHz" (3.1 Total flux)
- ESA4 Uranus model may need revision for pole-rotation brightness variation  
  > "these results suggest that the ESA4 model may need to be revised to account for the brightness variation in Uranus caused by its pole rotation." (3.1 Total flux)

## Claim tuples

- H: 3C 286 total flux is stable at mm wavelengths | E: Linear-trend fits to ALMA (2018-2024) and IRAM (2006-2024) flux; Uranus residual analysis | R: ALMA declines 2-15%; IRAM shows no clear trend; Uranus brightened ~4-6.6% | F: Intrinsic flux stable up to 229 GHz; ALMA decline partly due to Uranus brightening | **partially**
- H: Polarization of 3C 286 is stable at mm/submm | E: Period averages and linear fits of EVPA and fractional polarization | R: Secular changes smaller than or comparable to scatter/uncertainties | F: Polarization stable at all observing frequencies over ~20 yr | **supported**
- H: Spectral steepening reflects synchrotron cooling and gives a source age | E: Spectral indices from VLA and IRAM, equipartition B and continuous injection age | R: Break at 67.2 GHz, B~4.4 mG, age 450 yr, beta_app=2.6 | F: One-zone model inconsistent with observed speeds; multi-zone interpretation suggested | **partially**
- H: EVPA rotation with frequency is due to core-shift-related Faraday rotation | E: Power-law fit of EVPA vs lambda^2 from 5-343.4 GHz and RM vs frequency fit | R: RM rises to (3.2±1.5)e4 rad m^-2; |RM|∝ν^2.05±0.06 | F: Consistent with BK conical jet core-shift; proposed model EVPA curve for absolute EVPA calibration | **supported**
- H: Fractional polarization increase reflects reduced Faraday depolarization | E: Power-law fit of m vs lambda^2 from 1.5-343.4 GHz | R: Single power law with k'=-0.047±0.001 | F: Higher polarization at short wavelengths may result from reduced Faraday depolarization and more ordered fields | **partially**

## Reasoning

- Why this data: Long-term multi-instrument monitoring needed because high-frequency polarization of 3C 286 was poorly constrained  
  > "These substantial uncertainties in EVPA and fractional polarization measurements at such high frequencies have made it challenging to investigate their stability and frequency-dependent trends" (Introduction)
- Why this method: Stability permits stacking data to obtain high-accuracy reference values  
  > "This stability allows us to obtain the fractional polarization and EVPA values with unprecedented accuracy at millimeter/submillimeter wavelengths by stacking all the data." (3.2 Polarization)
- Alternative: Historical SMA flux monitoring excluded due to calibration inconsistencies  
  > "However, we do not include these measurements in our analysis due to inconsistencies in the flux calibration process" (2.3 SMA)
- Alternative: MeerKAT 1.4 GHz EVPA excluded from RM fit  
  > "We did not include $\chi=29.2^\circ$ at 1.4 GHz obtained with MeerKAT in the RM calculation" (4.3 EVPA rotation as a function of frequency)
- Alternative: EVPA rotation via gradual magnetic field direction change with optical depth  
  > "If the direction of the magnetic field gradually changes with optical depth, it could explain the observed EVPA rotation with frequency" (4.3 EVPA rotation as a function of frequency)
- How they decided it was enough: _not stated_
- Limitation (authors): Uranus brightening cannot fully explain ALMA Band 6/7 flux decrease  
  > "However, the additional decrease observed in Band 6 and 7 may arise from instrumental effects, short-term variations intrinsic to Uranus and 3C 286, or a combination of both." (3.1 Total flux)
- Limitation (authors): IRAM 229 GHz EVPA uncertainties may be underestimated  
  > "This discrepancy suggests that the EVPA uncertainties for IRAM may have been underestimated." (3.2 Polarization)
- Limitation (authors): Depolarization models suited for optically thin cases only  
  > "However, those models are primarily suited for optically thin cases, whereas the emitting regions in 3C 286 are partially optically thick" (4.4 Depolarization mechanism)
- Caveat (inferred, ours): RM table row 103-233 GHz lists rest-frame (8.6±1.7)×10^4 while (1+z)^2×2.5×10^3 ≈ 8.6×10^3; likely typo and it breaks monotonic trend
- Caveat (inferred, ours): RM values derived from a smooth model curve make the |RM|∝ν^a fit partly a consequence of the assumed power-law form; uncertainties of sampled points are correlated
- Caveat (inferred, ours): EVPA fits combine VLA data from 1995-2012 with ALMA/IRAM/SMA data of different epochs and resolutions
- Caveat (inferred, ours): Equipartition B and age depend on assumed 50 mas spherical geometry and k=1
- Caveat (inferred, ours): Break frequency relies only on IRAM fluxes with a fixed conversion factor

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: AMAPOLA scripts referenced via URL/Zenodo  
  > "This is a set of CASA-friendly python scripts to reduce the ALMA polarimetric data, as described in (cite: kameno23)." (2.1 ALMA)
- Missing: Per-epoch ALMA/IRAM/SMA measurement tables
- Missing: Weighting scheme for means and fits
- Missing: Exact VLA data points used for 3-50 GHz spectral index and break fit method
- Missing: Representative frequencies for RM sampling and RM fit details
- Data volume (inferred): Small: hundreds of per-epoch flux/polarization measurements (tabular, <1 MB) from AMAPOLA; raw calibrator visibilities not needed
- Score (inferred): 3/5, ALMA calibrator products and project code are given and analysis is simple fits, but IRAM/SMA per-epoch data and fit weights are not provided.
- Rediscovery candidate: no, Main numeric results (spectral break, RM trend) depend on IRAM per-epoch data and VLA literature values; public availability of IRAM/SMA data not stated.

## Links

- Method: (cite: kameno23) (AMAPOLA ALMA polarimetric calibrator reduction)
- Method: (cite: thum08) (IRAM XPOL polarimeter setup and calibration)
- Method: (cite: murgia99; murgia03) (Synchrotron age formula)
- Method: (cite: govoni04) (Equipartition magnetic field)
- Method: (cite: butler12) (Solar system flux models (ALMA memo 594))
- Companion: (cite: agudo18_1) (Earlier IRAM 3C 286 data and conversion factors)
- Companion: (cite: kneissl23) (ALMA grid source flux monitoring and Uranus brightness)
- Companion: (cite: perley13_pol) (VLA polarization of 3C 286)
- Related: ALMA grid source calibrator monitoring
- Related: AMAPOLA
- Related: POLAMI
- Related: MAPI
- Related: SMAPOL

## Checks

```json
{
 "quotes": 96,
 "quotes_ok": 96,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00001.CAL"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 106,
  "stated": 65,
  "rate": 0.613
 },
 "evidence_ok": true
}
```
