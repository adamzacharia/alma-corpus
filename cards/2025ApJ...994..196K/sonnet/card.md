# Monitoring of 3C 286 with ALMA, IRAM, and SMA from 2006 to 2025: Stability, Synchrotron Ages, and Frequency-dependent Polarization Attributed to Core-shift

`2025ApJ...994..196K` | The Astrophysical Journal 2025 | first author: Kam, Minchul | arXiv: 2510.05540 | DOI: 10.3847/1538-4357/ae10b1

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, instrumentation
- Question: Is the flux, polarization and EVPA of the calibrator 3C 286 stable at mm/submm wavelengths over ~20 years, and what explains its spectral break and frequency-dependent EVPA and polarization?  
  > "The combined data from these three monitoring programs allows for a precise investigation of the stability and properties of 3C 286 at millimeter and submillimeter wavelengths." (Introduction)
- Target **3C 286**: coordinates _not stated_; z/distance z = 0.849  
  > "3C 286 is a quasar ($z=0.849$; (cite: burbidge69)) classified as a compact steep-spectrum (CSS) source" (Introduction); distance from Burbidge & Burbidge 1969  
  > "3C 286 is a quasar ($z=0.849$; (cite: burbidge69)) classified as a compact steep-spectrum (CSS) source" (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 3 (91.5, 103.5 GHz), Band 6 (233.0 GHz), Band 7 (343.4 GHz)  
  > "The data has been primarily obtained in Band 3 (91.5 and 103.5 GHz) and Band 7 (343.4 GHz) since May 2018." (2.1 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA 7-m Array (grid source monitoring)  
  > "are observed with the 7-m Array at least every two weeks to provide secondary flux calibrators" (2.1 ALMA)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: ALMA 2018 May - 2024 Dec; IRAM 2006 Oct - 2024 May; SMA 2022 Jun - 2025 Feb  
  > "| ALMA   | 91.5      | 2018 May - 2024 Dec.  | 207           | 330           |" (Table 1)
- pi or archival as stated: ALMA grid-source monitoring data reduced with AMAPOLA; IRAM POLAMI/MAPI data; SMA SMAPOL data  
  > "For polarization analysis, we collected data reduced using the Analytic Matrix for ALMA POLArimetry (AMAPOLA)." (2.1 ALMA)
- Other facility **IRAM 30-m**: Total flux and polarization at 86 and 229 GHz, 2006-2024 (XPOL)  
  > "3C 286 has been monitored with the IRAM 30-m Telescope at 86 and 229 GHz" (2.2 The IRAM 30-m Telescope)
- Other facility **SMA**: Polarization at 225 GHz (SMAPOL, 2022-2025)  
  > "SMAPOL is a program initiated in 2022 June to regularly monitor the polarization properties of 40 AGN jets" (2.3 SMA)
- Other facility **VLA**: Literature flux, EVPA and fractional polarization at 1-50 GHz  
  > "we adopted the total flux measurements using VLA at 1–50 GHz (cite: perley13_flux), along with polarization measurements from the same instrument." (2.4 VLA)
- External data: VLA EVPA at 5, 15, 25, 33, 45 GHz (Table 2)  
  > "we took the EVPA measurements at 5, 15, 25, 33, and 45 GHz from Table 2 in (cite: perley13_pol)" (2.4 VLA) [from (cite: perley13_pol)]
- External data: VLA fractional polarization at 1.5-43.3 GHz (Table 5)  
  > "The fractional polarization values were taken from Table 5 of (cite: perley13_pol)" (2.4 VLA) [from (cite: perley13_pol)]
- External data: VLA total flux at 1-50 GHz; I0 = 7.297 Jy at 4.885 GHz  
  > "the total flux of $I_{0}$=7.297 Jy at $\nu_0$=4.885 GHz" (4.2) [from (cite: perley13_flux)]
- External data: IRAM Kelvin-to-Jansky factors 6.1 and 8.6 Jy/K  
  > "the conversion factor was determined to be ($6.1\pm0.1$) Jy K$^{-1}$ and ($8.6\pm0.4$) Jy K$^{-1}$ for 86 and 229 GHz, respectively" (2.2 The IRAM 30-m Telescope) [from (cite: agudo18_1)]
- Simulation/model as data: ESA4 Uranus brightness model (Butler-JPL-Horizons 2012 framework) for flux scale  
  > "Specifically, the model for Uranus is based on the ESA4 model" (2.1 ALMA)

## Processing

### Calibration

- pipeline or manual: AMAPOLA CASA-friendly python scripts for polarization reduction  
  > "This is a set of CASA-friendly python scripts to reduce the ALMA polarimetric data, as described in (cite: kameno23)." (2.1 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus (ESA4 model) as ALMA primary; SSOs referenced to Uranus within 5%  
  > "Observations of the grid sources include a scan of any available solar system object (SSO), with Uranus serving as the primary reference" (2.1 ALMA)
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

- ALMA polarization reduction following AMAPOLA  
  > "as described in (cite: kameno23)" (2.1 ALMA) [from (cite: kameno23)]
- IRAM XPOL setup and calibration  
  > "The standard XPOL setup and calibration processes summarized in (cite: thum08) has been maintained throughout the monitoring" (2.2 The IRAM 30-m Telescope) [from (cite: thum08)]
- Synchrotron age formula (continuous injection)  
  > "can be expressed as (cite: murgia99; murgia03):" (4.2) [from (cite: murgia99; murgia03)]

### Not stated but needed to reproduce (our reading)

- Exact ALMA execution blocks/project codes and the AMAPOLA product version used
- Weighting scheme for weighted means and flux-trend fits
- Fitting method details for power-law fits and spectral break
- Selection/flagging criteria for individual epochs
- SMA reduction parameters

## Analysis recipe

1. **Long-term flux trend**: Linear fit S=c0*(t-58000)+c1 to flux, EVPA and fractional polarization per frequency, and Period I-III averages  
  > "we fitted all the total flux measurements at each frequency with the following function" (3.1 Total flux)
   - fitting: _not stated_
   - validation: Compared ALMA with IRAM trends and Uranus residuals  
  > "Nevertheless, the change in the brightness of Uranus alone cannot fully account for the decreasing trend observed in the ALMA measurements, as the magnitudes of the decrease in Band 6 and 7 exceed 10%." (Results, Total flux)
2. **Spectral index and break**: Power-law indices 3-50 GHz and 86-229 GHz; break from intersection  
  > "This difference in spectral index between the two frequency ranges leads to a spectral break at $67.2\pm1.2$ GHz" (4.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Equipartition B and synchrotron age**: B_eq from Govoni & Feretti formula, then tau_syn from continuous injection model  
  > "these parameters yield an equipartition magnetic field strength of $B_{\rm eq}$$\sim$4.4 mG" (4.2)
   - parameter: source size 50 mas, k=1, xi=1.23e-12  
  > "we adopt a source size of 50 mas" (4.2)
   - assumption: spherical geometry, no expansion, constant B  
  > "(ii) no expansion of the emitting source, and (iii) constant magnetic field strength" (4.2)
   - fitting: _not stated_
   - validation: Compared apparent speed with VLBI and CSS typical speeds  
  > "However, these apparent speeds are significantly faster than the apparent speed $\beta_{\rm app}=0.6\pm0.5$ observed in the inner jet at 5 mas from the core (cite: an17)." (Discussion, Synchrotron age and magnetic field strength)
4. **EVPA vs lambda^2 and RM**: Single power-law fit log(chi)=k log(lambda^2)+C; RM between adjacent model points; |RM|~nu^a fit  
  > "we fit all the EVPA values with a single power-law function of the form" (4.3)
   - assumption: rest-frame RM=(1+z)^2 RM_obs  
  > "\left|RM_{\rm rest}\right| = (1+z)^2 \left|RM_{\rm obs}\right|" (4.3)
   - fitting: weighted fit  
  > "The resulting coefficients from the weighted fit are $k=-0.016\pm0.002$" (4.3)
   - validation: Index compared with a=2 expected for BK conical jet  
  > "with the power-law index $a=2.05\pm0.06$, which is consistent with the theoretically expected value of $a=2$ for the BK conical jet model." (Discussion, EVPA rotation as a function of frequency)
5. **Fractional polarization vs lambda^2**: Single power-law fit log(m)=k' log(lambda^2)+C'  
  > "we fit the fractional polarization values with a single power-law function of the form" (4.4)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **AMAPOLA** : ALMA polarimetric reduction  
  > "we collected data reduced using the Analytic Matrix for ALMA POLArimetry (AMAPOLA" (2.1 ALMA)
- **CASA** : Planet models and AMAPOLA scripts  
  > "The CASA brightness temperature models for planets follow the Butler-JPL-Horizons 2012 framework" (2.1 ALMA)
- **MIR** : SMA initial calibration  
  > "was performed using the MIR software package" (2.3 SMA)
- **MIRIAD** : SMA instrumental polarization calibration  
  > "the instrumental polarization was calibrated with the MIRIAD (cite: sault95)" (2.3 SMA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spectral index 3-50 GHz | 0.712 | 0.003 | dimensionless | 2 | yields a spectral index of $\alpha=0.712\pm0.003$ |
| Spectral index 86-229 GHz | 1.039 | 0.008 | dimensionless | 2 | / 86–229                          / $1.039\pm0.008$ / |
| Break frequency | 67.2 | 1.2 | GHz | 2 | / 3–50                            / $0.712\pm0.003$ / $67.2\pm1.2$           / $1.2\pm0.1$         / |
| Equipartition magnetic field | 4.4 | not stated | mG | 3 | $B_{\rm eq}$$\sim$4.4 mG |
| Synchrotron age | 450 | not stated | years | 3 | we derive the age of 3C 286 to be $\tau_{\rm syn}$=450 years |
| RM power-law index | 2.05 | 0.06 | dimensionless | 4 | with the power-law index $a=2.05\pm0.06$ |
| EVPA fit coefficients | k=-0.016, C=1.547 | 0.002, 0.003 | dimensionless | 4 | $k=-0.016\pm0.002$ and $\rm C=1.547\pm0.003$ |
| Fractional polarization fit coefficients | k'=-0.047, C'=1.108 | 0.001, 0.001 | dimensionless | 5 | $k'=-0.047\pm0.001$ and $\rm C'=1.108\pm0.001$ |
| ALMA EVPA at 343.4 GHz (weighted mean) | 38.93 | 0.08 | deg | 1 | / 343.4         / $-$              / $38.93\pm0.08$      / $16.37\pm0.07$ / |
| Uranus residual flux increase at 86 GHz (IRAM) 2006-2024 | 6.6 | 1.5 | % | 1 | indicates a systematic increase of 6.6%$\pm$1.5% from 2006 to 2024 |

## Qualitative findings

- IRAM flux stable 2006-2024; ALMA flux decline partly attributable to Uranus brightening under ESA4  
  > "which up to 4% could be attributed to an apparent increase in the absolute brightness of Uranus" (abstract)

## Claim tuples

- H: Is the total flux of 3C 286 stable up to 229 GHz? | E: Linear trend fits to IRAM and ALMA light curves | R: IRAM shows no trend; ALMA decreases 2-15% | F: Intrinsic flux stable; ALMA decline partly from Uranus calibration | **partially**
- H: Is polarization stable and EVPA rotating with frequency? | E: Period comparisons, trend fits, weighted means | R: No significant secular change; EVPA 33 to 38.9 deg from 5 to 343.4 GHz | F: Stable polarization; model curve proposed for EVPA calibration | **supported**
- H: Does RM increase with frequency as expected from core-shift? | E: Power-law fit of EVPA vs lambda^2 and RM vs frequency | R: a=2.05±0.06 | F: Consistent with core-shift in a conical jet | **supported**
- H: Is the spectral break explained by synchrotron aging of the whole jet? | E: Break at 67 GHz, equipartition B, age | R: Age 450 yr implies beta_app=2.6, too fast | F: One-zone model insufficient; multi-zone needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Older SMA flux data excluded due to inconsistent flux calibration  
  > "we do not include these measurements in our analysis due to inconsistencies in the flux calibration process" (2.3 SMA)
- How they decided it was enough: _not stated_
- Limitation (authors): Uranus change cannot fully explain >10% ALMA decrease in Bands 6 and 7  
  > "the change in the brightness of Uranus alone cannot fully account for the decreasing trend observed in the ALMA measurements" (3.1 Total flux)
- Caveat (inferred, ours): Break frequency from only two IRAM points plus VLA, so break position is model dependent
- Caveat (inferred, ours): Equipartition B and age depend on assumed 50 mas size and spherical geometry
- Caveat (inferred, ours): Faraday-rotation interpretation of EVPA assumes RM at core; alternative opacity explanation not distinguished
- Caveat (inferred, ours): Unexplained ALMA decline limits flux stability claim

## Reproducibility

- Data public (paper): AMAPOLA ALMA products on Zenodo; ALMA data public in archive  
  > "AMAPOLA: ALMA Polarization Monitoring for Calibrator Sources, Zenodo." (References)
- Products in archive: _not stated_
- Missing: Project codes and per-epoch data tables
- Missing: IRAM and SMA reduced data availability
- Missing: Fit weighting details
- Data volume (inferred): small; reduced AMAPOLA tables, ~10 GB if raw ALMA data are needed
- Score (inferred): 6/5, Derived products are simple and numeric, but processed inputs are inherited from AMAPOLA, IRAM and SMA pipelines and fitting details are sparse.
- Rediscovery candidate: no, IRAM and SMA data are not clearly public, and the paper gives no project codes or fitting details.

## Links

- Method: (cite: kameno23) (AMAPOLA polarization calibration)
- Method: (cite: agudo18_1) (IRAM POLAMI calibration and conversion factors)
- Method: (cite: kneissl23) (ALMA grid-source flux calibration)
- Companion: (cite: perley13_pol) (VLA polarization comparison)
- Related: POLAMI
- Related: MAPI
- Related: SMAPOL
- Related: AMAPOLA

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2011.0.00001.CAL"
 ],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 41,
  "rate": 0.519
 },
 "evidence_ok": true
}
```
