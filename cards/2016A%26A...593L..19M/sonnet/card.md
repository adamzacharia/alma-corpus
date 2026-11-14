# The MHz-peaked radio spectrum of the unusual γ-ray source PMN J1603-4904

`2016A&A...593L..19M` | Astronomy and Astrophysics 2016 | first author: Müller, C. | arXiv: 1609.01992 | DOI: 10.1051/0004-6361/201629547

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars
- Question: Does the radio spectrum of the gamma-ray source PMN J1603-4904 show a low-frequency (MHz) turnover, as expected for a young compact radio galaxy?  
  > "we investigate the behavior of the spectrum at lower frequencies to search for a low-frequency turnover." (abstract)
- Target **PMN J1603-4904**: coordinates _not stated_; z/distance z=0.23  
  > "Together with the optical-spectroscopic redshift of $z=0.23$ from X-shooter observations (cite: Goldoni2016)" (1 Introduction); distance from optical-spectroscopic redshift from X-shooter observations (Goldoni2016)  
  > "Together with the optical-spectroscopic redshift of $z=0.23$ from X-shooter observations (cite: Goldoni2016)" (1 Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: ALMA Band 7 (343.5 GHz) point taken from the ALMA calibrator database; new data are GMRT 325 and 610 MHz  
  > "the ALMA measurement at 343.5 GHz (Band 7) could indicate a break in the synchrotron spectrum." (3 The MHz to GHz spectrum of PMN J1603–4904)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: GMRT 325 MHz: 2014-01-31; 610 MHz: 2014-03-23  
  > "(project code: 25_038, observation date: 2014-01-31)" (2 Observations and data reduction)
- pi or archival as stated: archival GMRT data (pointed at pulsar PSR 1600-48); TGSS catalog at 150 MHz  
  > "we analyzed archival GMRT data of PMN J1603–4904" (2 Observations and data reduction)
- Other facility **GMRT**: Archival 325 and 610 MHz observations (project 25_038)  
  > "we analyzed archival GMRT data of PMN J1603–4904 at 325 GHz" (2 Observations and data reduction)
- Other facility **TGSS ADR**: 150 MHz flux density 702.3±71.6 mJy  
  > "It has a flux density of $702.3\pm71.6\,\mathrm{mJy}$" (2 Observations and data reduction)
- Other facility **ALMA calibrator database**: Band 7 flux density used in the broadband spectrum  
  > "measurements from the ALMA calibrator database[^2]" (3 The MHz to GHz spectrum of PMN J1603–4904)
- External data: GHz radio spectrum (ATCA, VLBI, etc.) of PMN J1603-4904  
  > "the data presented in (cite: Mueller2014a)" (3 The MHz to GHz spectrum of PMN J1603–4904) [from (cite: Mueller2014a)]
- External data: 843 MHz MGPS flux density 1.54±0.5 Jy  
  > "| 843 | $1.54\pm0.5$ | – | MGPS |" (Table 1) [from (cite: Murphy2007_MGPS)]

## Processing

### Calibration

- pipeline or manual: Manual GMRT calibration in AIPS using a single RFI-free channel; no phase calibration  
  > "we used one channel that is not corrupted to perform the amplitude calibration." (2 Observations and data reduction); "Note that PMN J1603–4904 is not resolved, therefore we did not calibrate the phases." (2 Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 3C 286  
  > "Using the flux calibrator 3C 286 we calibrated the amplitudes of PMN J1603–4904" (2 Observations and data reduction)
- flux scale uncertainty: 10% systematic added  
  > "In order to account for systematic errors we add a 10% uncertainty (cite: Chandra2004)." (2 Observations and data reduction)
- self calibration: Iterative self-calibration in DIFMAP  
  > "where we used an iterative self-calibration procedure to image the field." (2 Observations and data reduction)

### Imaging

- task: DIFMAP imaging with Gaussian model fits for flux densities  
  > "We used Gaussian model fits to obtain the flux densities of the individual sources." (2 Observations and data reduction)
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

- Sky-temperature flux scale correction factors for GMRT following the TGSS method (3.56±0.2 at 325 MHz, 1.58±0.2 at 610 MHz)  
  > "Following (cite: TGSS), the radio images at 325 and 610 MHz were corrected for this effect by a scaling factor depending on frequency and sky position." (2 Observations and data reduction) [from (cite: TGSS)]
- Peak frequency-linear size relation used to estimate source size  
  > "Using the anticorrelation between rest-frame peak frequency (i.e., $\sim490$ MHz at $z=0.23$) and size" (3 The MHz to GHz spectrum of PMN J1603–4904) [from (cite: Odea1997)]

### Not stated but needed to reproduce (our reading)

- Fit method/optimizer and weighting for SSA/FFA models
- Which data points (ATCA, ALMA, VLBI) are in the fit and their values
- Channel used for amplitude calibration and DIFMAP imaging parameters
- How the sky-position scaling factors were computed
- Source coordinates

## Analysis recipe

1. **Calibrate and image archival GMRT data**: AIPS amplitude calibration on one clean channel with 3C 286, BPASS, FLGIT flagging, channel averaging, DIFMAP self-cal imaging and Gaussian fits; sky-temperature flux correction  
  > "With the AIPS task `FLGIT` we flagged RFI noise." (2 Observations and data reduction)
   - software: AIPS, DIFMAP
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit SSA and FFA models to the broadband spectrum**: Fit SSA and FFA absorbed power-law models with alpha fixed at -0.35 to all unresolved-image data  
  > "We use $\alpha=-0.35$ from a fit to the ATCA and ALMA data above $>$1 GHz." (3 The MHz to GHz spectrum of PMN J1603–4904)
   - assumption: No variability at sub-GHz frequencies over the time period (non-simultaneous spectrum)  
  > "hence, we expect that PMN J1603–4904 exhibits no major flux change at sub-GHz frequencies over this time period." (3 The MHz to GHz spectrum of PMN J1603–4904)
   - fitting: _not stated_
   - validation: Compared reduced chi-square with Callingham2015  
  > "The $\chi^2_\mathrm{red}$ values are comparable to results by (cite: Callingham2015)" (3 The MHz to GHz spectrum of PMN J1603–4904)
3. **Estimate maximum linear size**: Apply O'Dea & Baum relation to rest-frame peak frequency  
  > "we can estimate the maximum size of PMN J1603–4904 to be $\sim 1.4$ kpc." (3 The MHz to GHz spectrum of PMN J1603–4904)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **AIPS** : GMRT calibration and RFI flagging  
  > "The GMRT data were calibrated using the Astronomical Imaging Processing System (cite: Greisen2003_AIPS)." (2 Observations and data reduction)
- **DIFMAP** : Self-calibration, imaging, Gaussian model fits  
  > "exported the data to DIFMAP (cite: Shepherd1997)" (2 Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| TGSS 150 MHz flux density | 702.3 | 71.6 | mJy | 0 | It has a flux density of $702.3\pm71.6\,\mathrm{mJy}$ |
| GMRT 325 MHz corrected flux density | 2.18 | 0.23 | Jy | 1 | / 300 / $0.61\pm0.07$ / $2.18\pm0.23$ / this work / |
| GMRT 610 MHz corrected flux density | 1.91 | 0.25 | Jy | 1 | / 600 / $1.21\pm0.10$ / $1.91\pm0.25$ / this work / |
| FFA turnover frequency (observed) | 0.40 | 0.04 | GHz | 2 | / FFA / 1.7$\pm$0.2 / 0.02$\pm$0.01 / 0.40$\pm$0.04 / 4.4 / |
| SSA turnover frequency (observed) | 0.39 | 0.03 | GHz | 2 | / SSA / 98$\pm$24 / 0.02$\pm$0.01 / 0.39$\pm$0.03 / 4.5 / |
| Rest-frame peak frequency | ~490 | not stated | MHz | 2 | The radio spectrum clearly shows a rest-frame spectral turnover at $\sim 490$ MHz. |
| Maximum linear size | ~1.4 | not stated | kpc | 3 | we determine the linear size of PMN J1603–4904 to be $\sim 1.4$ kpc. |
| ALMA-only spectral index | ~-0.8 | not stated | dimensionless | 2 | A power-law fit to the ALMA data only yields $\alpha_\mathrm{ALMA}\sim -0.8$. |
| Core spectral index (VLBI 8, 22 GHz + ALMA Band 7) | ~-0.16 | not stated | dimensionless | 2 | yields a spectral index of $\alpha_\mathrm{core}\sim
-0.16$. |

## Qualitative findings

- SSA and FFA models describe the data equally well; the data cannot distinguish them.  
  > "Both models can describe the data equally well (see Fig. [2](#fig:spec) and Table [2](#table:fits))." (3 The MHz to GHz spectrum of PMN J1603–4904)

## Claim tuples

- H: PMN J1603-4904 has a low-frequency spectral turnover like a young compact radio galaxy | E: Built the 150 MHz–GHz spectrum from TGSS, archival GMRT and literature data and fitted SSA/FFA models | R: Turnover at ~400 MHz observed (~490 MHz rest frame) | F: It is an MPS-like source, the second confirmed gamma-ray-detected such object | **supported**
- H: The turnover mechanism (SSA vs FFA) can be identified | E: Fitted both models | R: Reduced chi-square 4.4 (FFA) vs 4.5 (SSA) | F: Cannot distinguish them with sparse sub-GHz coverage | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Non-simultaneous spectrum assuming no variability; sparse sub-GHz coverage.  
  > "With this assumption we construct a non-simultaneous MHz to GHz spectrum of PMN J1603–4904." (3 The MHz to GHz spectrum of PMN J1603–4904)
- Caveat (inferred, ours): Large flux scale correction factors (3.56 at 325 MHz) make the turnover sensitive to calibration
- Caveat (inferred, ours): Reduced chi-square of ~4.4 indicates poor fits
- Caveat (inferred, ours): Variability assumption not tested at low frequencies
- Caveat (inferred, ours): Peak-size relation has large scatter

## Reproducibility

- Data public (paper): Archival GMRT data and TGSS catalog used  
  > "we analyzed archival GMRT data of PMN J1603–4904" (2 Observations and data reduction)
- Products in archive: _not stated_
- Missing: Full list and values of ATCA/ALMA/VLBI points
- Missing: Fitting procedure details
- Missing: DIFMAP and AIPS parameters
- Data volume (inferred): ~ a few GB (two archival GMRT datasets)
- Score (inferred): 3/5, Small analysis with public data, but fitting details and the complete input spectrum are not given.
- Rediscovery candidate: no, Key recipe details (fits, data table, calibration channels) are missing and ALMA plays only a minor role.

## Links

- Method: (cite: TGSS) (Flux scale correction method for GMRT)
- Companion: (cite: Mueller2014a) (Earlier multiwavelength study and GHz radio spectrum)
- Related: TANAMI
- Related: TGSS ADR
- Related: Fermi/LAT

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 64,
  "stated": 28,
  "rate": 0.438
 },
 "evidence_ok": true
}
```
