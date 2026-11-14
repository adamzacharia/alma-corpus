# Constraining the nature of two Lyα emitters detected by ALMA at z = 4.7

`2014MNRAS.439.2096W` | Monthly Notices of the Royal Astronomical Society 2014 | first author: Williams, R. J. | arXiv: 1401.3791 | DOI: 10.1093/mnras/stu119

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Are the two Lyα emitters near BRI1202-0725, detected in [CII] by ALMA, physically associated with the system and powered by quasar photoionisation or in situ star formation?  
  > "We detect Ly$\rm{\alpha}$ emission from both sources and so confirm that these Ly$\rm{\alpha}$ emitter candidates are physically associated with the BRI1202-0725 system." (abstract)
- Target **BRI1202-0725 Lyα-1 and Lyα-2**: coordinates _not stated_; z/distance z = 4.703 (Lyα-1), z = 4.698 (Lyα-2)  
  > "Fitting the Ly$\rm{\alpha}$ line profile with a Gaussian gives the central wavelength of the emission at $\lambda = 6933.46~\rm{\AA}$ which means this source is at redshift $z=4.703$." (Results); distance from Gaussian fit to Lyα in FORS2 spectra  
  > "Fitting the Ly$\rm{\alpha}$ line profile with a Gaussian gives the central wavelength of the emission at $\lambda = 6933.46~\rm{\AA}$ which means this source is at redshift $z=4.703$." (Results)

## Data provenance

- ALMA projects: 2011.0.00006.SV
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
- Line: [CII] 158 μm (not stated)
- Other facility **VLT FORS2**: Multi-object optical spectroscopy of both Lyα emitters, 300I grating, 6000-11000 Å  
  > "The 300I grating centred at $8600$ $\AA$ was used yielding a wavelength coverage between $6000-11000$ Å." (2 Observations and Data reduction)
- External data: ALMA [CII] line profiles and FIR/continuum properties of Lyα-1 and Lyα-2, used for comparison with Lyα  
  > "we compare our Ly$\rm{\alpha}$ profile to that of the \[CII\] emission from (cite: carilli_feb13)" (Results) [from (cite: carilli_feb13)]
- External data: Average high-ionisation line ratios of QSO2s and Sy2s  
  > "compared to the average ratios for the (cite: nagao_mar06) sample of QSO2s and Sy2s." (Table 2) [from (cite: nagao_mar06)]

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

- [CII]-to-SFR conversion factor  
  > "together with the (cite: sargsyan_aug12) conversion factor, indicate a SFR$\sim$$19~$M$_{\odot}$yr$^{-1}$ for this system" (Discussion) [from (cite: sargsyan_aug12)]

### Not stated but needed to reproduce (our reading)

- ALMA data reduction and [CII] measurements are taken from earlier papers; no ALMA processing is described
- Gaussian fitting method and uncertainty estimation for FORS2 lines not specified
- Method for deriving line flux upper limits not specified
- Exact sky alignment procedure parameters

## Analysis recipe


## Software

- **FORS2 pipeline** : calibration recipes fors_calib and fors_science for wavelength calibration  
  > "The *‘fors_calib’* recipe from the pipeline is used to process the calibration exposures associated with each scientific observation" (2 Observations and Data reduction)
- **IDL** : self-written routines for reduction and sky subtraction, cosmic ray removal  
  > "we employ part of the FORS2 pipeline as well as self written IDL routines to optimise the data reduction" (2 Observations and Data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Lyα-1 Lyα flux | 2.53 | 0.08 | 1e-16 erg cm^-2 s^-1 | 0 | / $2.53 \pm 0.08$ / $103 \pm 15$ / $4.703$ / $1381 \pm 124$ / |
| Lyα-1 FWHM | 1381 | 124 | km/s | 0 | / $2.53 \pm 0.08$ / $103 \pm 15$ / $4.703$ / $1381 \pm 124$ / |
| Lyα-2 Lyα flux | 0.33 | 0.06 | 1e-16 erg cm^-2 s^-1 | 0 | / $0.33 \pm 0.06$ / $67 \pm 15$ / $4.698$ / $1225 \pm 257$ / |
| Lyα-2 FWHM | 1225 | 257 | km/s | 0 | / $0.33 \pm 0.06$ / $67 \pm 15$ / $4.698$ / $1225 \pm 257$ / |
| Lyα-1 He II/Lyα upper limit | <0.018 | not stated | dimensionless | 0 | / Ly$\rm{\alpha}$-1 / $<0.019$ / $<0.017$ / $<0.033$ / $<0.018$ / |
| Lyα-[CII] velocity offset, Lyα-1 | 49 | not stated | km/s | 0 | We find the two profiles to be slightly shifted with respect to each other by $\Delta v = 49$ kms$^{-1}$ |
| Lower limit on HII sphere radius | >15 | not stated | kpc | 0 | we can place a lower limit on the radius of the HII sphere at greater than $15$ kpc. |

## Qualitative findings

- No high-ionisation lines detected, so in situ star formation powers the Lyα; fraction produced by QSO ionisation <10%  
  > "we estimate that the fraction of Ly$\rm{\alpha}$ produced as a consequence of ionisation by the QSO must be less than $10\%$." (Discussion)

## Claim tuples

- H: Lyα-1 and Lyα-2 are physically associated with BRI1202-0725 | E: FORS2 spectroscopy of both emitters | R: Lyα detected at z=4.703 and z=4.698 | F: Both are associated with the system | **supported**
- H: The LAEs are photoionised by the quasar | E: Search for NV, SiIV, CIV, HeII | R: No detections, upper limits well below AGN ratios | F: Powered by in situ star formation | **supported**
- H: Lyα kinematics match [CII] | E: Compare Lyα and ALMA [CII] profiles | R: Lyα much broader (~1100-1400 km/s) than [CII] | F: Broad Lyα may indicate positive-feedback induced star formation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Tidal shearing and starburst superwinds considered but judged unlikely  
  > "suggests that the tidal scenario is unlikely." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Lyα-2 constraints on high-ionisation lines are much looser, so AGN photoionisation cannot be excluded from those lines  
  > "in principle we cannot exclude the presence of N V, Si IV, C IV or He II at a level" (Discussion)
- Caveat (inferred, ours): Slit losses may affect absolute Lyα fluxes
- Caveat (inferred, ours): Lyα-2 detection is low significance
- Caveat (inferred, ours): Lyα width may be affected by slit and sky subtraction systematics

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA data are used only via a published paper; no processing described
- Data volume (inferred): Small; ALMA data used only from literature, FORS2 spectra small
- Score (inferred): 2/5, ALMA role is minor; the main results come from FORS2 data, with incomplete fitting details.
- Rediscovery candidate: no, Main results come from ESO FORS2 optical data, and ALMA is used only from published results.

## Links

- Method: (cite: vandokkum_nov01) (Cosmic ray removal)
- Companion: (cite: carilli_feb13) (ALMA [CII] detection of the LAEs)
- Companion: (cite: wagg_jun12) (ALMA observations of the system)

## Checks

```json
{
 "quotes": 25,
 "quotes_ok": 25,
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
  "facts": 52,
  "stated": 12,
  "rate": 0.231
 },
 "evidence_ok": true
}
```
