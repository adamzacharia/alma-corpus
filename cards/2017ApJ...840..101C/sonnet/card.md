# Near-infrared MOSFIRE Spectra of Dusty Star-forming Galaxies at 0.2 &lt; z &lt; 4

`2017ApJ...840..101C` | The Astrophysical Journal 2017 | first author: Casey, Caitlin M. | arXiv: 1703.10168 | DOI: 10.3847/1538-4357/aa6cb1

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: What are the redshifts and rest-frame optical properties (nebular lines, obscuration, outflows) of 450um/850um-selected SCUBA-2 DSFGs in COSMOS, and how reliable are their photometric redshifts?  
  > "We present near-infrared and optical spectroscopic observations of a sample of 450$\mu$m and 850$\mu$m-selected dusty star-forming galaxies (DSFGs) identified in a 400 arcmin$^2$ area in the COSMOS field." (abstract)
- Target **SCUBA-2 selected DSFGs in COSMOS (31 confirmed of 114 targets)**: coordinates COSMOS field (mask centres near 10:00 +02:2x)  
  > "Thirty-one sources of the 114 targets were spectroscopically confirmed at $0.2<z<4$" (abstract); z/distance 0.2<z<4; median z_spec=1.55  
  > "Thirty-one sources of the 114 targets were spectroscopically confirmed at $0.2<z<4$" (abstract); distance from spectroscopic redshifts from MOSFIRE/DEIMOS/LRIS  
  > "Thirty-one sources of the 114 targets were spectroscopically confirmed at $0.2<z<4$" (abstract)

## Data provenance

- ALMA projects: 2013.1.00118.S, 2013.1.00151.S, 2011.1.00539.S
- bands: 1.1 mm dust continuum (archival)  
  > "1.1 mm ALMA dust continuum maps available from the ALMA archive" (Observations & Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: RMS 0.08-0.15 mJy/beam; median S/N=10  
  > "The ALMA 1.1 mm maps range in RMS from 0.08–0.15 mJy/beam, sources are detected with a median S/N=10" (Observations & Data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival  
  > "1.1 mm ALMA dust continuum maps available from the ALMA archive" (Observations & Data)
- Other facility **Keck MOSFIRE**: H- and K-band spectra of 102 DSFG targets  
  > "In total, 102 DSFG targets were observed with MOSFIRE." (Observations & Data)
- Other facility **Keck DEIMOS**: optical spectra of the same SCUBA-2 sample  
  > "We also present observations obtained with the DEIMOS instrument on Keck II" (Observations & Data)
- Other facility **JCMT SCUBA-2**: 450 and 850 um parent sample selection  
  > "The parent sample for spectroscopic follow-up we use in this analysis is the full set of 165 Scuba-2-identified DSFGs in COSMOS" (Observations & Data)
- External data: SCUBA-2 COSMOS parent catalog, positions and counterparts  
  > "as summarized in (cite: casey13a)" (Observations & Data) [from (cite: casey13a)]
- External data: updated COSMOS2015 photometric redshift catalog  
  > "we update those photometric redshifts to the most current catalog (cite: laigle16a)" (Photometric Redshift Analysis) [from (cite: laigle16a)]

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

- Far-IR modified blackbody plus mid-IR power-law SED fitting for L_IR, dust mass, peak wavelength  
  > "We use the SED fitting procedure outlined in (cite: casey12a), using an emissivity spectral index of $\beta=1.8$." (Photometric Redshift Analysis) [from (cite: casey12a)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging details; archival maps used only as published
- Which ALMA project maps correspond to which source
- MOSFIRE flux calibration details
- Redshift measurement procedure for individual sources
- MAGPHYS configuration

## Analysis recipe

1. **Extract 1D spectra and measure redshifts**: IRAF apall extraction of MOSFIRE/DEIMOS spectra with optimal variance weighting  
  > "All spectra, from MOSFIRE and DEIMOS, were extracted using the iraf routine apall." (Observations & Data)
   - software: IRAF, MOSPY
   - fitting: _not stated_
   - validation: _not stated_
2. **SED fitting for stellar mass and IR properties**: MAGPHYS for stellar mass; modified blackbody plus MIR power law for L_IR, M_dust, SFR  
  > "fitting spectral energy distributions (SEDs) to the UV through millimeter photometry using the MAGPHYS code (cite: da-cunha08a)" (Photometric Redshift Analysis)
   - software: MAGPHYS
   - parameter: beta=1.8; alpha=2.5 if <4 far-IR points; T_dust=35 K if <2 far-IR points  
  > "When there are fewer than 4 far-IR photometric points, the mid-infrared powerlaw slope is fixed to $\alpha=2.5$" (Photometric Redshift Analysis)
   - assumption: Chabrier IMF; H0=71, Om=0.27  
  > "We also assume a Chabrier initial mass function (cite: chabrier03a)." (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Stack Halpha-detected spectra and measure composite lines**: Shift to rest frame, subtract polynomial continuum, unweighted co-add, multi-Gaussian fit of Halpha+[NII]  
  > "Continuum-subtracted spectra are combined using an unweighted co-addition." (DSFG Composite Spectrum)
   - fitting: four Gaussians for Halpha and [NII]  
  > "using four co-added Gaussian fits, with the narrow band component of  H$\alpha$ and the two  \[NII\] features at a fixed width" (DSFG Composite Spectrum)
   - validation: tested several weighting schemes; brightest source contributes 16%  
  > "All combinations produce similar spectra" (DSFG Composite Spectrum)
4. **Check ALMA counterpart identification**: Compare archival ALMA 1.1 mm positions with MOSFIRE targets  
  > "Five of the seven sources were correctly identified using multiwavelength counterparts (71%)" (Observations & Data)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **MAGPHYS** : SED fitting for stellar mass and photo-z diagnostics  
  > "using the MAGPHYS code (cite: da-cunha08a)" (Photometric Redshift Analysis)
- **IRAF apall** : 1D spectral extraction  
  > "extracted using the iraf routine apall" (Observations & Data)
- **MOSPY** : MOSFIRE spectral reduction  
  > "We used the MOSPY Data Reduction Pipeline (DRP) package for spectral reduction." (Observations & Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Confirmed DSFGs | 31 of 114 targets | not stated | sources | 1 | Thirty-one sources of the 114 targets were spectroscopically confirmed |
| Median spectroscopic redshift | 1.55 | 0.14 | dimensionless | 1 | $\langle z_{\rm spec}\rangle=1.55\pm0.14$ |
| Composite Balmer decrement | 21.0 | 2.4 | dimensionless | 3 | is 21.0$\pm$2.4 which translates to an $A_{V}=6.8\pm0.5$ |
| Na absorption blueshift | -200 | 30 | km/s | 3 | Na absorption blueshifted by $-$200$\pm$30 kms$^{-1}$ |
| Fraction with good ALMA counterpart ID | 5/7 (71%) | not stated | fraction | 4 | Five of the seven sources were correctly identified using multiwavelength counterparts (71%) |

## Qualitative findings

- Photometric redshifts fail catastrophically for about a third of DSFGs, attributed to decoupled obscured and unobscured emission  
  > "these have very distinct spectral energy distributions from the remaining DSFGs, suggesting a decoupling of highly obscured and unobscured components" (abstract)

## Claim tuples

- H: Can DSFG redshifts be confirmed efficiently in the near-IR? | E: MOSFIRE and DEIMOS follow-up of SCUBA-2 sources in COSMOS | R: 31 of 114 confirmed | F: Confirmation is low due to obscuration and redshift-range limits | **supported**
- H: Are photometric redshifts reliable for DSFGs? | E: Compare COSMOS photo-z with spec-z | R: 11/31 inaccurate or missing | F: Roughly half are good, the rest poor | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Some ALMA-identified counterparts show the MOSFIRE targets were mis-identified  
  > "Inevitably the positional uncertainty in bolometer maps will lead to some mis-identifications and ambiguities" (4.4 Mis-identifications)
- Caveat (inferred, ours): ALMA is a minor component; no ALMA data processing is described
- Caveat (inferred, ours): Small sample for BPT and composite conclusions

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: ALMA maps from the archive  
  > "1.1 mm ALMA dust continuum maps available from the ALMA archive" (Observations & Data)
- Missing: Keck spectra not stated as public
- Missing: ALMA map processing and photometry details
- Data volume (inferred): small for ALMA (7 continuum maps); Keck data separate
- Score (inferred): 2/5, ALMA role is minor and mostly undescribed; Keck spectroscopic analysis is only partially specified.
- Rediscovery candidate: no, Main results depend on Keck data and unspecified fitting details, not ALMA.

## Links

- Method: (cite: casey12a) (FIR SED fitting procedure)
- Method: (cite: da-cunha15a) (MAGPHYS high-z version)
- Companion: (cite: casey13a) (SCUBA-2 COSMOS parent catalog)
- Companion: (cite: danielson16a) (ALESS spectroscopic survey comparison)
- Related: ALESS
- Related: COSMOS
- Related: KBSS
- Related: MOSDEF

## Checks

```json
{
 "quotes": 38,
 "quotes_ok": 38,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.1.00539.S"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00539.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 27,
  "rate": 0.397
 },
 "evidence_ok": true
}
```
