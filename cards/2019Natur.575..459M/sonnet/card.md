# Observation of inverse Compton emission from a long γ-ray burst

`2019Natur.575..459M` | Nature 2019 | first author: MAGIC Collaboration | arXiv: 2006.07251 | DOI: 10.1038/s41586-019-1754-6

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: transients
- Question: What is the broadband emission of GRB 190114C from radio to TeV, and is the TeV emission a distinct inverse Compton (SSC) component of the afterglow?  
  > "This demonstrates that the newly discovered TeV radiation is not a simple extension of the known afterglow synchrotron emission, but rather a separate spectral component that has never been clearly seen before." (main text)
- Target **GRB 190114C**: coordinates _not stated_; z/distance z = 0.4245 ± 0.0005; luminosity distance ~2.3 Gpc  
  > "Owing to the relatively low redshift z = 0.4245 ± 0.0005 (see Methods) of the GRB (corresponding to a luminosity distance of ∼ 2.3 Gpc)" (Main text); distance from GTC OSIRIS spectroscopy (CaII, [OII], Hβ, [OIII] lines)  
  > "Owing to the relatively low redshift z = 0.4245 ± 0.0005 (see Methods) of the GRB (corresponding to a luminosity distance of ∼ 2.3 Gpc)" (Main text)

## Data provenance

- ALMA projects: 2018.A.00020.T, 2018.1.01410.T
- bands: Band 3 (97.500 GHz) and Band 6 (235.0487 GHz)  
  > "observations are reported in Band 3 (central observed frequency of 97.500 GHz) and Band 6 (235.0487 GHz), between 2019 January 15 and 2019 January 19." (Methods, ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2019 January 15 to 19  
  > "between 2019 January 15 and 2019 January 19" (Methods, ALMA)
- pi or archival as stated: _not stated_
- Other facility **MAGIC**: 0.2-1 TeV afterglow detection and spectra  
  > "We used the Major Atmospheric Gamma Imaging Cherenkov (MAGIC) standard software" (Methods, MAGIC)
- Other facility **Swift (XRT, BAT, UVOT), Fermi (GBM, LAT), AGILE**: X-ray, gamma-ray and UV/optical data  
  > "The Swift X-Ray Telescope (XRT) started observing 68 s after T0" (Methods)
- Other facility **ATCA, GMRT, MeerKAT, JCMT SCUBA-2**: radio and sub-mm light curves  
  > "Sub-millimeter observations were performed simultaneously at 850 µm and 450 µm on three nights using the SCUBA-2 continuum camera" (Methods)
- Other facility **GROND, GTC, HST, LT, NTT, NOT, REM, VLT, OASDG**: NIR/optical photometry and spectroscopy, host imaging  
  > "The Hubble Space Telescope (HST) imaged the afterglow and host galaxy of GRB 190114C on 11 February and 12 March 2019." (Methods)
- External data: Early ALMA 97.5 GHz observations  
  > "ALMA early observations at 97.5 GHz are taken from [15]." (Methods, ALMA) [from Laskar et al. 2019, ApJ 878, L26 (ref 15)]
- External data: EBL attenuation model  
  > "taking into account the extragalactic background light (EBL) effect using the model of Dom´ınguez et al. [46]" (Methods, MAGIC) [from Dominguez et al. 2011]

## Processing

### Calibration

- pipeline or manual: CASA pipeline calibration  
  > "Data were calibrated within CASA (Common Astronomy Software Applications, version 5.4.0 [74]) using the pipeline calibration." (Methods, ALMA)
- casa version: CASA 5.4.0  
  > "version 5.4.0 [74]" (Methods, ALMA)
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

- Early ALMA 97.5 GHz data taken from earlier paper  
  > "ALMA early observations at 97.5 GHz are taken from [15]." (Methods, ALMA) [from Laskar et al. 2019 (ref 15)]

### Not stated but needed to reproduce (our reading)

- ALMA flux values and uncertainties are not tabulated
- photometry method (aperture, fitting) and calibrators not given
- ALMA flux scale uncertainty not given
- imaging parameters not given
- numerical afterglow code not public

## Analysis recipe

1. **ALMA calibration and photometry**: Pipeline calibration and photometric measurements in CASA  
  > "Photometric measurements were also performed within CASA." (Methods, ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Model broadband SED and light curves as synchrotron plus SSC forward shock**: Numerical code solving electron distribution evolution with synchrotron, SSC, adiabatic losses, gamma-gamma absorption, pairs, self-absorption  
  > "we use a numerical code that solves the evolution of the electron distributions and derives the radiative" (Methods, Afterglow model)
   - parameter: s = 0, eps_e = 0.07, eps_B = 8e-5, p = 2.6, n0 = 0.5, Ek = 8e53 erg  
  > "we have used s = 0, ϵ e = 0.07, ϵ B = 8 × 10 −5, p = 2.6, n 0 = 0.5, and E k = 8 × 10 53 erg." (Methods, Afterglow model)
   - assumption: Power-law density profile s=0 or s=2; power-law electron distribution  
  > "We consider two types of power law radial profiles n(R) = n0 R −s for the external environment: s = 0 (homogeneous medium) and s = 2" (Methods, Afterglow model)
   - fitting: _not stated_
   - validation: Model curves compared by eye with data (Fig. 3, Extended Data Figs 6, 7)  
  > "The results of the modeling are overlaid to the data in Fig. 3, and Extended Data Figs. 6 and 7." (Methods, Afterglow model)

## Software

- **CASA** 5.4.0: ALMA calibration and photometry; also ATCA reduction  
  > "Data were calibrated within CASA (Common Astronomy Software Applications, version 5.4.0 [74]) using the pipeline calibration." (Methods, ALMA)
- **MIRIAD** : ATCA data reduction  
  > "reduced with the software packages MIRIAD [76] and CASA [74] using standard techniques." (Methods, ATCA)
- **PyBDSF** v.1.8.15: MeerKAT flux estimation  
  > "MeerKAT flux estimation was done by finding and fitting the source with the software PyBDSF v.1.8.15 [83]." (Methods, MeerKAT)
- **XSPEC** : XMM-Newton/NuSTAR spectral fits  
  > "were derived by fitting the spectrum with XSPEC adopting the same power law model" (Methods)
- **IRAF** : GROND reduction and photometry  
  > "Image reduction and photometry were carried out with standard IRAF tasks [53]" (Methods, GROND)
- **LePhare** : host galaxy SED analysis  
  > "The SED analysis was performed with LePhare" (Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Redshift | 0.4245 | 0.0005 | dimensionless | 0 | z = 0.4245 ± 0.0005 |
| Synchrotron energy, 68-110 s | 1.5e52 | not stated | erg | 2 | ∼ 1.5 × 10 52 erg and ∼ 6.0 × 10 51 erg respectively in the time interval 68-110 s |
| SSC energy, 68-110 s | 6.0e51 | not stated | erg | 2 | ∼ 1.5 × 10 52 erg and ∼ 6.0 × 10 51 erg respectively in the time interval 68-110 s |
| TeV light curve decay index | -1.51 | 0.04 | dimensionless | 0 | α TeV ∼ −1.51 ± 0.04 |
| Bulk Lorentz factor at 100 s | ~140-160 | not stated | dimensionless | 2 | the bulk Lorentz factor is ∼ 140-160 at 100 s |

## Qualitative findings

- The TeV emission is a distinct spectral component, explained by SSC in the afterglow forward shock.  
  > "as synchrotron plus SSC radiation, within the framework of the theory of afterglow emission from external forward shocks." (main text)

## Claim tuples

- H: Is the TeV emission an extension of synchrotron emission or a separate component? | E: Multi-band SEDs in five time intervals | R: Spectral hardening above 0.2 TeV in the first interval | F: TeV emission is a separate component, interpreted as SSC | **supported**
- H: Are the conditions for SSC unusual? | E: Forward-shock synchrotron+SSC modeling | R: Parameters fall within typical ranges | F: SSC is probably common in GRBs | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Hadronic and prompt-SSC origins of the TeV flux rejected (prompt SSC at most ~20%)  
  > "prompt SSC radiation can account at most for a limited fraction" (Main text)
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): ALMA is a minor part; no ALMA flux table or error analysis
- Caveat (inferred, ours): Model parameters are degenerate and not fitted statistically

## Reproducibility

- Data public (paper): Data available from the corresponding authors upon request  
  > "Data are available from the corresponding authors upon request." (Data Availability Statement)
- Products in archive: _not stated_
- Code: Proprietary MAGIC codes; information available on request  
  > "Proprietary data reconstruction codes were generated at the MAGIC telescopes large-scale facility." (Code Availability Statement)
- Missing: ALMA photometry details
- Missing: Afterglow code
- Missing: MAGIC proprietary data and software
- Data volume (inferred): ALMA part: a few GB
- Score (inferred): 2/5, ALMA minor; proprietary multi-facility data and unreleased code.
- Rediscovery candidate: no, The main results rely on MAGIC proprietary data and a non-public model code.

## Links

- Companion: MAGIC Collaboration, Nature 575, 455 (2019) (ref 10) (TeV detection companion paper)
- Companion: Laskar et al. 2019 (ref 15) (ALMA reverse-shock paper)

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 29,
  "rate": 0.433
 },
 "evidence_ok": true
}
```
