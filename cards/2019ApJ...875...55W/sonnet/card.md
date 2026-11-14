# The MESAS Project: Long-wavelength Follow-up Observations of Sirius A

`2019ApJ...875...55W` | The Astrophysical Journal 2019 | first author: White, Jacob Aaron | arXiv: 1903.03481 | DOI: 10.3847/1538-4357/ab0e7f

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: stellar_physics, debris_disks
- Question: What is the long-wavelength (1.4-9 mm) emission of Sirius A, and is it consistent with PHOENIX stellar atmosphere models and stable over time?  
  > "These observations complement our previous millimeter data on Sirius A and are entirely consistent with the PHOENIX stellar atmosphere models constructed to explain them." (abstract)
- Target **Sirius A**: coordinates RA = 06 h 45 m 08.30 s, Dec = -16° 43' 18.91" (J2000)  
  > "The observations were centered on Sirius A using J2000 coordinates RA = 06 h 45 m 08.30 s and $\delta = -16^{\circ} ~43' ~18.91''$." (2.1 ALMA); "Located only $2.64\pm0.01$ pc (cite: vanleeuwen) from our Solar System" (Introduction); z/distance 2.64 ± 0.01 pc  
  > "The observations were centered on Sirius A using J2000 coordinates RA = 06 h 45 m 08.30 s and $\delta = -16^{\circ} ~43' ~18.91''$." (2.1 ALMA); "Located only $2.64\pm0.01$ pc (cite: vanleeuwen) from our Solar System" (Introduction); distance from van Leeuwen 2007  
  > "The observations were centered on Sirius A using J2000 coordinates RA = 06 h 45 m 08.30 s and $\delta = -16^{\circ} ~43' ~18.91''$." (2.1 ALMA); "Located only $2.64\pm0.01$ pc (cite: vanleeuwen) from our Solar System" (Introduction)

## Data provenance

- ALMA projects: 2017.1.00698.S
- bands: ALMA Bands 3, 4, 5  
  > "The observations in ALMA Bands 3, 4, and 5 were taken in 3 separate executions blocks (EBs) from January through August." (2.1 ALMA)
- frequencies and spectral setup: 4 SPWs per band, 128x15.625 MHz channels each; Band 5 centered 196/198/208/210 GHz; Band 4 143/145/155/157 GHz; Band 3 93/95/105/107 GHz  
  > "Each SPW has $128\times 15.625$ MHz channels for a total bandwidth of 2 GHz." (2.1 ALMA); "The SPWs were centered at 93 GHz, 95 GHz, 105 GHz, and 107 GHz, giving an effective continuum frequency of 100 GHz (3.0 mm)." (2.1 ALMA)
- continuum bandwidth: 8 GHz total per band  
  > "Each band utilized an instrument configuration with a total bandwidth of 8 GHz split among 4 spectral windows (SPW)." (2.1 ALMA)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15-457 m (Band 5), 15-500 m (Band 4), 15-1397 m (Band 3)  
  > "This EB used a 43 antenna configuration with baselines ranging from 15 m to 1397 m." (2.1 ALMA)
- angular resolution: Band 5 1.46x0.85"; Band 4 1.43x1.17"; Band 3 1.02x0.69"  
  > "The size of the resulting synthesized beam is $1.02''\times0.69''$ at a position angle of $68.2^{\circ}$, corresponding to $\sim2.3$ au." (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: RMS 0.040 (B5), 0.029 (B4), 0.032 (B3) mJy/beam  
  > "These Band 4 data achieve a RMS sensitivity of $0.029~\rm mJy~beam^{-1}$ in the CLEANed image." (2.1 ALMA)
- time on source: ~5.1 min on-source per band  
  > "The Band 5 observations were made on 2018 August 22 for 20.24 min (5.1 min on-source)." (2.1 ALMA)
- observing dates: 2018 Jan 25 (B3), Apr 21 (B4), Aug 22 (B5)  
  > "The Band 3 observations were made on 2018 January 25 for 19.75 min (5.12 min on-source)." (2.1 ALMA)
- pi or archival as stated: Cycle 5 program, PI White  
  > "during Cycle 5 (ID 2017.1.00698.S, PI White)" (2.1 ALMA)
- Other facility **VLA**: 6.7 and 9.0 mm continuum, D configuration (18A-328)  
  > "The data from the VLA were acquired in Semester 18A on 2018 September 07 and 2018 September 11 (ID 18A-328, PI White)." (2.2 VLA)
- Other facility **GBT (MUSTANG2)**: 3.33 mm flux, 104 min on source  
  > "The total on-source time was 104 min split roughly equally between nights." (2.3 GBT)
- External data: Previous JCMT, SMA, VLA long-wavelength data and PHOENIX LTE model of Sirius A  
  > "Previous long wavelength observations of Sirius A are summarized in (cite: white18) and are shown in Fig. [1](#tb_plot) (black circles)." (2 Observations) [from (cite: white18)]
- External data: Sirius B Teff 25369 K and radius 0.008098 Rsun  
  > "effective temperature of T$_{eff}=25369~\rm K$ and radius of $\rm 0.008098~R_{\odot}$ (cite: bond17)" (Discussion) [from (cite: bond17)]
- External data: Fomalhaut ALMA fluxes 1.79 mJy (0.87 mm) and 0.88 mJy (1.3 mm)  
  > "observed a flux of 1.79 mJy and 0.88 mJy, respectively (cite: su16; white_fom)" (Discussion) [from (cite: su16; white_fom)]
- Simulation/model as data: PHOENIX 1D spherical LTE atmosphere model of Sirius A from White et al. 2018  
  > "we include the LTE atmosphere model of Sirius A from (cite: white18)" (Discussion)

## Processing

### Calibration

- pipeline or manual: CASA pipeline (WVR, Tsys, flux, bandpass, phase)  
  > "All of the data were reduced using the Common Astronomy Software Applications (CASA 5.4.0) pipeline (cite: casa_reference)" (2.1 ALMA)
- casa version: CASA 5.4.0  
  > "Data were reduced using the CASA 5.4.0 pipeline" (2.2 VLA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: ALMA: J0750+1231 (B5), J0522-3627 (B4, B3); VLA: 3C48  
  > "The flux and bandpass were calibrated with quasar J0750+1231, the phase with J0648-1744" (2.1 ALMA)
- flux scale uncertainty: ALMA 10%; VLA 20% (3C48 flaring)  
  > "For ALMA, we adopt an absolute flux calibration uncertainty of $10\%$ and for VLA $20\%$" (3 Visibility Model Fitting)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: VLA natural weighting  
  > "The data were imaged with a natural weighting and cleaned using CASA’s *CLEAN* algorithm down to a threshold of 1/2 the RMS noise." (2.2 VLA)
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
- final rms: ALMA 0.029-0.040 mJy/beam; VLA 0.014-0.028 mJy/beam  
  > "The 2018 September 11 observations achieve sensitivities of $0.028~\rm mJy~beam^{-1}$ and $0.014~\rm mJy~beam^{-1}$, respectively." (2.2 VLA)

### Inherited from earlier work

- VLA scheduling block setup identical to earlier Sirius A observations  
  > "The Scheduling Block (SB) for each observation was setup identically to the previous VLA observations of Sirius A (cite: white18)" (2.2 VLA) [from (cite: white18)]
- Point-source flux fitting with uvmodelfit  
  > "As in (cite: white18), we use the CASA task *uvmodelfit* to obtain a flux at each wavelength." (3 Visibility Model Fitting) [from (cite: white18)]

### Not stated but needed to reproduce (our reading)

- uvmodelfit starting parameters and fit options
- Which ALMA channels/SPWs were averaged and any flagging
- ALMA imaging details (weighting, cell size, deconvolver, masks)
- MUSTANG2 data pipeline details
- Data points and weights used in the power-law fit
- Fitting range handling for Sirius B

## Analysis recipe

1. **Fit point-source fluxes to ALMA and VLA visibilities**: Point-source fit to visibilities per SPW with minimum chi-squared iteration  
  > "This approach fits a point source to the visibilities of a given data set. A minimum $\chi^{2}$ is converged on through an iterative procedure." (3 Visibility Model Fitting)
   - software: CASA uvmodelfit
   - assumption: Sirius A is a point source (0.00602")  
  > "Sirius A is effectively a point source ($0.00602''$)" (3 Visibility Model Fitting)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure GBT flux**: Map of all GBT data, Gaussian fit at Sirius A position  
  > "we generated a map of all the GBT data and fit a Gaussian at the location of Sirius A." (3 Visibility Model Fitting)
   - fitting: _not stated_
   - validation: Fake sources injected into timestreams and recovered  
  > "fake sources of known amplitude were added to the raw timestreams and were recovered with high accuracy." (3 Visibility Model Fitting)
3. **Fit power-law brightness temperature template**: Non-linear least squares fit of T_obs = C0 T_phot (lambda/0.45mm)^alpha over 0.45-9.0 mm  
  > "Using a non-linear least squares model fitting procedure with the Python SciPy function *curve_fit*, we find best fit values of C$_{0} = 0.67\pm 0.03$ and $\alpha = 0.05\pm 0.02$." (Discussion)
   - software: SciPy curve_fit
   - assumption: Rayleigh-Jeans limit, T_obs substituted for T_B  
  > "by assuming the stellar emission is in the Rayleigh-Jeans limit and substituting $T_{obs}$ for T$_{B}$" (Discussion)
   - fitting: curve_fit least squares  
  > "Using a non-linear least squares model fitting procedure with the Python SciPy function *curve_fit*, we find best fit values of C$_{0} = 0.67\pm 0.03$ and $\alpha = 0.05\pm 0.02$." (Discussion)
   - validation: Applied to Fomalhaut, predictions consistent with ALMA fluxes  
  > "yields a predicted flux of 1.88 mJy and 0.84 mJy for the 2 ALMA wavelengths, respectively." (Discussion)

## Software

- **CASA** 5.4.0: Pipeline calibration, CLEAN imaging, uvmodelfit  
  > "CASA 5.4.0 (cite: casa_reference)" (Software)
- **SciPy curve_fit** : Power-law fit of brightness temperature  
  > "Python SciPy function *curve_fit*" (Discussion)
- **PHOENIX** : Stellar atmosphere model  
  > "a spherical 1D PHOENIX code (cite: hauschildt10)" (Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| GBT 3.33 mm flux | 0.90 | 0.11 | mJy | 2 | This yields a total flux of $0.90\pm0.11$ mJy. |
| ALMA 1.43 mm flux | 5.60 | 0.60 | mJy | 1 | 1.43 / ALMA / 2018 AUG 22 / J0750+1231 / 5.60 / 0.60 / 1.34 |
| ALMA 3.22 mm flux | 1.35 | 0.14 | mJy | 1 | 3.22 / ALMA / 2018 JAN 25 / J0522-3627 / 1.35 / 0.14 / 3.73 |
| VLA 9.0 mm flux (2018 Sep 07) | 0.125 | 0.029 | mJy | 1 | 9.0 / VLA / 2018 SEP 07 / 3C48$^{b}$ / 0.125 / 0.029 / 4.46 |
| C0 | 0.67 | 0.03 | dimensionless | 3 | C$_{0} = 0.67\pm 0.03$ and $\alpha = 0.05\pm 0.02$ |
| alpha (temperature spectral index) | 0.05 | 0.02 | dimensionless | 3 | C$_{0} = 0.67\pm 0.03$ and $\alpha = 0.05\pm 0.02$ |
| Predicted Fomalhaut flux at 0.87 and 1.3 mm | 1.88 and 0.84 | not stated | mJy | 3 | yields a predicted flux of 1.88 mJy and 0.84 mJy for the 2 ALMA wavelengths, respectively. |

## Qualitative findings

- Sirius B was not detected in any observation.  
  > "Sirius A’s white dwarf companion, Sirius B, was not detected in any of the observations." (Discussion)

## Claim tuples

- H: New ALMA/GBT/VLA data of Sirius A agree with the PHOENIX LTE model | E: Point-source flux measurements at 1.43-9.0 mm compared with model | R: Data largely consistent with the model | F: Model describes submm-cm emission of Sirius A | **supported**
- H: Sirius A long-wavelength emission is variable | E: Compare 2017 SMA through 2018 GBT data | R: No significant variability within 20% calibration uncertainty | F: Emission likely constant over ~2 yr | **supported**
- H: Sirius A spectrum can serve as template for A-type stars, e.g. Fomalhaut | E: Power-law fit and prediction of Fomalhaut flux | R: Predicted fluxes match observed within ~10% | F: Fomalhaut inner-disk ALMA flux consistent with stellar emission alone | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Cannot exclude short-lived mm flares; Sirius A not necessarily a template for rapid rotators like Altair  
  > "Indeed, we can not exclude the possibility of short-lived mm flares" (Discussion)
- Caveat (inferred, ours): Only 3 short ALMA EBs; high reduced chi2 (3-4) in fits not discussed
- Caveat (inferred, ours): Power-law template calibrated on one star
- Caveat (inferred, ours): 20% VLA uncertainty limits variability constraints

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00698.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: uvmodelfit settings
- Missing: ALMA imaging parameters
- Missing: GBT reduction pipeline details
- Missing: Model spectrum values from White et al. 2018
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Simple point-source fits with public ALMA pipeline data, but several settings are unstated.
- Rediscovery candidate: yes, Data are likely public, recipe is simple, and results are numeric fluxes.

## Links

- Method: (cite: white18) (Original Sirius A observations, model, and uvmodelfit approach)
- Companion: (cite: white18) (Previous MESAS Sirius A paper)
- Related: MESAS Project

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
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
  "facts": 67,
  "stated": 41,
  "rate": 0.612
 },
 "evidence_ok": true
}
```
