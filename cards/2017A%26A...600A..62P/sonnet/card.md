# The hybrid disks: a search and study to better understand evolution of disks

`2017A&A...600A..62P` | Astronomy and Astrophysics 2017 | first author: Péricaud, J. | arXiv: 1612.06582 | DOI: 10.1051/0004-6361/201629371

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: debris_disks, protoplanetary_disks
- Question: Are there more CO-gas-rich (hybrid) young debris disks, and how do CO-to-continuum flux ratios of hybrid disks compare with those of protoplanetary and debris disks?  
  > "The survey is complemented with a bibliographic study of the ratio between the emission of the gas and the continuum (S$_{\rm CO}$/F$_{\rm cont}$) in CTTS, Herbig Ae, WTTS, hybrid, and debris disks." (abstract)
- Target **HD 23642**: coordinates _not stated_; z/distance 138 +/- 1.5 pc  
  > "Its distance has been revised to $138\pm1.5$ pc by (cite: Groenewegen+etal_2007), in agreement with the recent works on the distance of the Pleiades." (3.2 A possible new hybrid disk candidate in the Pleiades); distance from Groenewegen et al. 2007  
  > "Its distance has been revised to $138\pm1.5$ pc by (cite: Groenewegen+etal_2007), in agreement with the recent works on the distance of the Pleiades." (3.2 A possible new hybrid disk candidate in the Pleiades)

## Data provenance

- ALMA projects: 2011.0.00150.S, 2013.1.00163.S, 2011.0.00780.S
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
- Line: 12CO J=2-1 (not stated)
- Line: 12CO J=3-2 (not stated)
- Other facility **APEX (SHeFI)**: CO J=3-2 survey of southern targets  
  > "we used the *APEX* telescope at 345 GHz to search for the CO J=3$\rightarrow$2 transition with the SHeFI receiver" (2.1 APEX and IRAM observations)
- Other facility **IRAM-30m (EMIR)**: CO J=2-1 survey of northern targets  
  > "For northern targets, we used the *IRAM-30m* telescope (project 172-14), attempting to detect the CO J=2$\rightarrow$1 line with the EMIR receiver" (2.1 APEX and IRAM observations)
- External data: CO and mm continuum fluxes for CTTS, Herbig, WTTS, hybrid and debris disks (compilation)  
  > "We have compiled measurements of the CO J=2$\rightarrow$1 and CO J=3$\rightarrow$2 emission from the literature, as well as the continuum emission at the corresponding wavelength for a wide variety of disks." (2.2 Compilation of existing CO and mm continuum data) [from Table references, e.g. (cite: Hardy+etal_2015), (cite: Lieman-Sifry+etal_2016)]

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

### Not stated but needed to reproduce (our reading)

- How ALMA archival CO and continuum fluxes were extracted (calibration, imaging, aperture)
- CASA version and pipeline for archival data
- APEX/IRAM reduction details and baseline fitting
- DiskFit fit settings

## Analysis recipe

1. **Derive upper limits and gas masses**: 3 sigma integrated-intensity limits, converted to H2 mass via Scoville formula and DiskFit disk model  
  > "We derive the gas mass using two methods. The first is based on the rms obtained from the data." (3.3 CO mass upper limits)
   - software: DiskFit
   - parameter: Tex = 40 K, tau = 1; Rout = 200 au, Rin = 5 au, T = 30 K at 100 au, q = 0.4, p = 1.5  
  > "The temperature law is set to 30 K at 100 au with the exponent of the radial variation $q= 0.4$." (3.3 CO mass upper limits)
   - assumption: CO/H2 abundance 1e-4  
  > "Conversion to H2 content is done using the standard value of 10$^{-4}$ for the CO to H$_2$ abundance ratio." (3.3 CO mass upper limits)
   - fitting: _not stated_
   - validation: Two methods agree within a factor three  
  > "The methods give consistent results within a factor three." (Comparison of the two methods)
2. **Compare CO and continuum fluxes**: Linear regression of compiled CO vs dust fluxes scaled to 100 pc; S_CO/F_cont ratios vs stellar parameters  
  > "The equivalent width, that is, the ratio $S_{\rm CO}/F_{\rm cont}$, has been calculated for the whole sample of 103 sources." (3.5)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **DiskFit** : Keplerian disk model fits to CO spectra  
  > "Using the DiskFit tool (see Sect.[0.1](#subsec:co_mass_survey)), the best-fit model yields $R_{out} =450 \pm 210$ au" (3.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HD 23642 integrated CO J=2-1 flux | 710 | 180 | mJy km/s | 1 | estimated to 710 $\pm$ 180 mJy km s$^{-1}$ |
| HD 23642 disk outer radius | 450 | 210 | au | 1 | the best-fit model yields $R_{out} =450 \pm 210$ au |
| Occurrence of CO gas in young debris disks | 7.1 | 2.6 | % | 0 | $7.1 \pm 2.6$ % (1$\sigma$ uncertainty, 7 detections among 98 observed systems) |

## Qualitative findings


## Claim tuples

- H: Are hybrid disks distinct in CO-to-dust flux ratio? | E: Compilation of CO and continuum fluxes | R: Hybrid disks lie above the CO-dust correlation | F: Hybrid disks may be transient with dust evolved faster than gas | **supported**
- H: Does the survey find new CO-rich debris disks? | E: APEX/IRAM CO survey of 25 stars | R: Tentative 4 sigma detection around HD 23642 | F: Possible new hybrid disk candidate | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): ALMA data used only as archival flux compilation without stated processing
- Caveat (inferred, ours): Heterogeneous literature sample

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Archival ALMA flux extraction details
- Data volume (inferred): small (<10 GB archival ALMA)
- Score (inferred): 3/5, Main data are APEX/IRAM; ALMA minor and processing unstated.
- Rediscovery candidate: no, ALMA role minor and recipe incomplete.

## Links


## Checks

```json
{
 "quotes": 23,
 "quotes_ok": 23,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 55,
  "stated": 12,
  "rate": 0.218
 },
 "evidence_ok": true
}
```
