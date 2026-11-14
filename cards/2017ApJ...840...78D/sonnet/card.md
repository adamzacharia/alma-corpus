# An ALMA Survey of Submillimeter Galaxies in the Extended Chandra  Deep Field South: Spectroscopic Redshifts

`2017ApJ...840...78D` | The Astrophysical Journal 2017 | first author: Danielson, A. L. R. | arXiv: 1705.03503 | DOI: 10.3847/1538-4357/aa6caf

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: What are the spectroscopic redshifts, redshift distribution, spectral properties, outflow signatures and SED-derived stellar masses of ALMA-identified SMGs in the ECDFS (ALESS)?  
  > "The first necessary step in this process is to derive the precise spectroscopic redshifts." (1 Introduction)
- Target **ALESS SMGs in the ECDFS (131 main+supp sources)**: coordinates Table 2 lists RA/Dec per source (e.g. ALESS 001.1 at 53.310270, -27.937366)  
  > "the ALESS SMG catalogue was formed, comprising a main (hereafter main) catalogue of the 99 of the most reliable ALMA-identified SMGs" (2.1 Sample definition); z/distance spectroscopic z = 0.7-5.0, median 2.4  
  > "the ALESS SMG catalogue was formed, comprising a main (hereafter main) catalogue of the 99 of the most reliable ALMA-identified SMGs" (2.1 Sample definition); distance from optical/NIR spectroscopy; two from ALMA [CII]  
  > "the ALESS SMG catalogue was formed, comprising a main (hereafter main) catalogue of the 99 of the most reliable ALMA-identified SMGs" (2.1 Sample definition)

## Data provenance

- ALMA projects: 2011.1.00294.S
- bands: Band 7 (870 um)  
  > "Each LESS submillimetre source was targeted with ALMA at 870 $\mu$m (Band 7)." (1 Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1.5 arcsec synthesised beam FWHM  
  > "The typical FWHM of the ALMA synthesised beam was $\sim$ 1.5$''$" (1 Introduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 120 s per source  
  > "the 120 s observations for each source were taken between October and November 2011" (2.1 Sample definition)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [CII] 158 um (serendipitous, ALESS 61.1 and 65.1) (not stated)
- Other facility **VLT FORS2/VIMOS/XSHOOTER, Keck MOSFIRE/DEIMOS, Gemini GNIRS**: optical/NIR spectra used for the redshifts  
  > "we also obtained observations with XSHOOTER on VLT, the Gemini Near-Infrared Spectrograph (GNIRS) and the Multi-Object Spectrometer for Infra-Red Exploration (MOSFIRE)" (2.1 Sample definition)
- Other facility **ATCA**: 12CO(1-0) confirming the two [CII] redshifts  
  > "both redshifts have been confirmed by the identification of $^{12}$CO(1–0) emission using ATCA" (2.7 ALMA)
- External data: ALMA 870um maps and ALESS SMG catalogue  
  > "Details of the ALMA observations are described in (cite: Hodge13)" (2.1 Sample definition) [from (cite: Hodge13)]
- External data: UV-mid-IR photometry and photometric redshifts  
  > "The UV–mid-infrared photometry for the ALESS SMGs is given in (cite: Simpson14)" (5.1.2 UV-to-radio SEDs) [from (cite: Simpson14)]
- External data: Deblended Herschel, ALMA and radio photometry  
  > "the (deblended) *Herschel* / SPIRE+PACS, ALMA and radio photometry are given in (cite: Swinbank14) (cite: DaCunha15)" (5.1.2 UV-to-radio SEDs) [from (cite: Swinbank14; DaCunha15)]

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

- ALMA observations and reduction taken from the ALESS survey paper  
  > "Details of the ALMA observations are described in (cite: Hodge13)" (2.1 Sample definition) [from (cite: Hodge13)]

### Not stated but needed to reproduce (our reading)

- Magphys setup (priors, libraries, photometry used) beyond citing da Cunha 2015
- Exact procedure for SFR/sSFR derivation
- Main-sequence relations used for comparison

## Analysis recipe

1. **measure redshifts from spectra**: Two investigators inspected 1D and 2D spectra; lines fit with Gaussians; redshifts from nebular lines preferred, then UV ISM lines, then Lya; quality flags Q=1-4  
  > "Any emission / absorption features that were identified were fit with a Gaussian profiles to determine their central wavelengths." (3.1 Redshift identification)
   - fitting: _not stated_
   - validation: compared with photometric redshifts; median Δz/(1+z_spec)=0.00±0.02  
  > "median $\Delta z/(1+z_{\rm spec})$ = 0.00 $\pm$ 0.02 and a variance of $\sigma^2$ = 0.1" (3.1 Redshift identification)
2. **fit SEDs for stellar mass and extinction**: Magphys fit of UV-to-radio photometry at the spectroscopic redshift  
  > "For each SMG, we use magphys to fit the photometry at the spectroscopic redshift" (5.1.2 UV-to-radio SEDs)
   - software: Magphys
   - assumption: Chabrier IMF  
  > "a Chabrier initial mass function (IMF; (cite: Chabrier03))" (1 Introduction)
   - fitting: _not stated_
   - validation: compared with photometric-redshift-based estimates of Simpson+14  
  > "there is good agreement between the photometric and spectroscopic redshifts with a median $\Delta z/(1+z_{\rm spec})$ = 0.00 $\pm$ 0.02 and a variance of $\sigma^2$ = 0.1." (3.1 Redshift identification)

## Software

- **Magphys** : SED fitting for stellar mass, extinction, FIR luminosity  
  > "we employ the magphys SED fitting code from (cite: DaCunha15)" (5.1.2 UV-to-radio SEDs)
- **ESOREX** : VIMOS and XSHOOTER reduction  
  > "The data were reduced using the standard ESOREX pipeline package for VIMOS." (2.3 VIMOS)
- **mospy** : MOSFIRE reduction  
  > "Data reduction was completed with mospy." (2.5 MOSFIRE)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of SMGs with spectroscopic redshift | 52 | not stated | sources | 1 | In total 52 redshifts have been determined for the ALESS SMGs |
| Median spectroscopic redshift | 2.4 | 0.1 | dimensionless | 1 | with a median of $z$ = 2.4 $\pm$ 0.1 |
| Median stellar mass | 6e10 | 1e10 | Msun | 2 | $M_\star$ = (6 $\pm$ 1) $\times$ 10$^{10}$ M$_{\odot}$ |
| Median A_V | 1.9 | 0.2 | mag | 2 | median extinction of A$_{\rm V}$ = 1.9 $\pm$ 0.2 |
| Median L_FIR | 3.2e12 | 0.4e12 | Lsun | 2 | $L_{\rm FIR}$ =(3.2 $\pm$ 0.4) $\times$ 10$^{12}$ L$_{\odot}$ |
| Median sSFR | 6e-9 | 1e-9 | yr^-1 | 2 | sSFR = (6 $\pm$ 1) $\times$ 10$^{-9}$ yr$^{-1}$ |

## Qualitative findings

- SMGs lie on average a factor ~5 above the main sequence at z=1-3  
  > "the SMGs in our sample lie (on average) a factor $\sim$ 5 above the so-called “main-sequence” at all three redshifts" (5.1.2 UV-to-radio SEDs)

## Claim tuples

- H: Radio-independent SMG selection reveals a high-z tail | E: Spectroscopic redshifts for ALMA-identified SMGs | R: 52 redshifts, median 2.4, ~23% at z>=3 | F: Sample is not biased against high-z SMGs | **supported**
- H: SMGs drive galaxy-scale outflows | E: Velocity offsets between nebular, Lya and UV ISM lines | R: offsets up to ~3000 km/s | F: Likely strong outflows driven mainly by star formation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Redshifts not obtained for 57 observed SMGs; sample biased to bluer sources  
  > "illustrating a modest bias to bluer restframe UV continuua in those SMGs for which we can measure spectroscopic redshifts for" (3.1 Redshift identification)
- Caveat (inferred, ours): Q=3 redshifts depend on photometric redshifts
- Caveat (inferred, ours): ALMA only supplies sample and two redshifts

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Template SEDs released at a URL; catalog in tables  
  > "The template SEDs are available from: [http://astro.dur.ac.uk/$\sim$ams/zLESS/]" (Footnote 2)
- Missing: Raw spectra of non-ALMA instruments are ESO/Keck/Gemini archive data
- Missing: Magphys configuration
- Data volume (inferred): ALMA part small; optical spectra tens of GB
- Score (inferred): 2/5, ALMA minor; analysis is optical spectroscopy and SED fitting.
- Rediscovery candidate: no, ALMA is minor and the redshift recipe is manual.

## Links

- Method: (cite: DaCunha15) (Magphys SED fitting)
- Companion: (cite: Hodge13) (ALESS ALMA survey)
- Companion: (cite: Simpson14) (photometric redshifts)
- Related: ALESS
- Related: LESS
- Related: ECDFS

## Checks

```json
{
 "quotes": 36,
 "quotes_ok": 36,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.1.00294.S"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00294.S"
 ],
 "codes_printed_but_missing": [
  "2011.0.00294.S"
 ],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 61,
  "stated": 24,
  "rate": 0.393
 },
 "evidence_ok": true
}
```
