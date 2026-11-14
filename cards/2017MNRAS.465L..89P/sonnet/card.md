# A revised host galaxy association for GRB 020819B: a high-redshift dusty starburst, not a low-redshift gas-poor spiral

`2017MNRAS.465L..89P` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Perley, Daniel A. | arXiv: 1609.04016 | DOI: 10.1093/mnrasl/slw221

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, transients
- Question: Is the purported z=0.41 spiral really the host of GRB 020819B, or is the radio afterglow in an unrelated background galaxy?  
  > "We report new observations from VLT (MUSE and X-shooter) which demonstrate that the purported host is an unrelated foreground galaxy." (abstract)
- Target **GRB 020819B host candidate (blob at afterglow site)**: coordinates _not stated_; z/distance z = 1.9621 ± 0.0001  
  > "at a common redshift of $z = 1.9621\pm0.0001$." (X-shooter observations); distance from X-shooter [OIII]5007 and Halpha emission lines  
  > "at a common redshift of $z = 1.9621\pm0.0001$." (X-shooter observations)

## Data provenance

- ALMA projects: 2011.0.00232.S
- bands: _not stated_
- frequencies and spectral setup: four 1.875 GHz spectral windows centred at 245.072, 246.947, 260.500 and 262.375 GHz  
  > "covering four 1.875 GHz spectral frequency windows centred at 245.072, 246.947, 260.500 and 262.375 GHz" (ALMA Reanalysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival data first reported by Hatsukade et al. 2014 (H14)  
  > "The ALMA observations first reported by H14" (ALMA Reanalysis)
- Line: CO 3-2 (at z=0.41) (not stated)
- Other facility **VLT MUSE**: IFU data showing no Halpha or other lines at the afterglow location  
  > "We do not detect any significant H$\alpha$ emission at this location" (MUSE observations)
- Other facility **VLT X-shooter**: Optical/NIR spectroscopy giving z=1.9621 for the blob  
  > "These wavelengths identify them unambiguously as \[\]$\lambda$5007 and H$\alpha$ (respectively)" (X-shooter observations)
- Other facility **Keck LRIS (archival)**: Reanalysis of L10 spectra; no line emission at the blob  
  > "We downloaded their observations from the Keck Observatory Archive and independently reanalyzed them" (Archival Keck observations)
- External data: 1.2 mm continuum flux density 140 ± 30 uJy  
  > "1.2 mm flux density       | 140 $\pm$ 30 $\mu$Jy    | H14" (Table 1) [from Hatsukade+2014 (cite: Hatsukade+2014)]
- External data: 3 GHz flux density 31 ± 8 uJy  
  > "3 GHz flux density        | 31 $\pm$ 8 $\mu$Jy      | (cite: Greiner+2016)" (Table 1) [from (cite: Greiner+2016)]

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

- Calibration procedure and whether archive products or a re-run script were used
- Line search method, channel width and detection threshold for the blind search
- Imaging parameters (weighting, cell, mask)
- Continuum measurement method

## Analysis recipe

1. **Blind line search and continuum check in archival ALMA data**: Reanalysis of H14 ALMA observations in CASA, blind search of the entire spectrum at the afterglow site, continuum detection verified  
  > "performing a blind search of the entire spectrum at the afterglow site for line features. None were found" (ALMA Reanalysis)
   - software: CASA
   - fitting: _not stated_
   - validation: Continuum flux consistent with H14  
  > "we verify the continuum detection at a flux level consistent with value originally reported by H14" (ALMA Reanalysis)

## Software

- **CASA** 4.6: Reanalysis of the ALMA data  
  > "standard ALMA data analysis package CASA (version 4.6)" (ALMA Reanalysis)
- **ESO MUSE pipeline** 1.6: MUSE data reduction  
  > "using version `1.6` of the ESO pipeline" (MUSE observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Redshift of probable host | 1.9621 | 0.0001 | dimensionless | 0 | Redshift                  / 1.9621 $\pm$ 0.0001 |
| Minimum SFR from Halpha | 21 | not stated | Msun/yr | 0 | the H$\alpha$ flux corresponds to a minimum star-formation rate (SFR) of 21 M$_\odot$yr$^{-1}$ |
| Dust-corrected SFR | 76 | +103/-35 | Msun/yr | 0 | this increases to $76^{+103}_{-35} M_\odot$yr$^{-1}$. |

## Qualitative findings

- No line emission found in the ALMA spectra; the CO(3-2) nondetection is explained by the revised redshift  
  > "The revised redshift naturally explains the apparent nondetection of CO(3-2) line emission at the afterglow site from ALMA." (abstract)

## Claim tuples

- H: The blob at the afterglow site is a separate higher-redshift galaxy | E: MUSE and X-shooter spectroscopy plus Keck reanalysis | R: Lines at z=1.9621; no lines at z=0.41 | F: The z=0.41 spiral is not the host; the molecular gas deficiency claim is void | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Radio source unrelated to the GRB (probability 2-4%); lensing by the foreground galaxy considered but unproven  
  > "our own independent calculation using variability statistics from (cite: Ofek+2011) provides a similar value of 4%." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): The association with the z=1.96 galaxy is not definitive  
  > "This association is not definitive, although we argue that it is likely." (Discussion)
- Caveat (inferred, ours): ALMA part is a brief reanalysis with no quantitative upper limits given
- Caveat (inferred, ours): Late-time radio emission is unexplained

## Reproducibility

- Data public (paper): Archival ALMA and Keck data downloaded; ALMA program ID given  
  > "We downloaded their observations from the Keck Observatory Archive" (Archival Keck observations)
- Products in archive: _not stated_
- Missing: ALMA reduction and search details
- Data volume (inferred): ~10 GB
- Score (inferred): 2/5, ALMA part is a brief null-result reanalysis with few details.
- Rediscovery candidate: no, ALMA recipe is incomplete and results are mostly non-ALMA.

## Links

- Companion: Hatsukade+2014 (cite: Hatsukade+2014) (Original ALMA analysis)
- Companion: Levesque+2010 (cite: Levesque+2010) (Original Keck spectroscopy)

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
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 56,
  "stated": 18,
  "rate": 0.321
 },
 "evidence_ok": true
}
```
