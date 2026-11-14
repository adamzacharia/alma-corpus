# Discovery of radio jets in the Phoenix galaxy cluster center

`2020PASJ...72...62A` | Publications of the Astronomical Society of Japan 2020 | first author: Akahori, Takuya | arXiv: 2004.05724 | DOI: 10.1093/pasj/psaa039

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: galaxy_clusters_and_sz, agn_and_quasars
- Question: Are there spatially resolved radio jets/lobes (AGN feedback) in the Phoenix cluster BCG, and what is the origin of the radio emission near the center?  
  > "Key information missing so far is whether or not there are radio jets/lobes, which are firm evidence of AGN feedback activities." (Introduction)
- Target **Phoenix cluster (SPT-CLJ2344-4243) BCG**: coordinates Source C1 (R.A., Dec.) = (23:44:43.90, -42:43:12.51) (J2000)  
  > "The Phoenix cluster is a distant cluster located at the redshift of $z=0.596$." (Introduction); "leading to $1'' \sim 6.7$ kpc at the source redshift of $z=0.596$." (2.1 Introduction); z/distance z = 0.596; 1'' ~ 6.7 kpc  
  > "The Phoenix cluster is a distant cluster located at the redshift of $z=0.596$." (Introduction); "leading to $1'' \sim 6.7$ kpc at the source redshift of $z=0.596$." (2.1 Introduction); distance from standard LCDM, H0=70, OmegaM=0.3, OmegaL=0.7  
  > "The Phoenix cluster is a distant cluster located at the redshift of $z=0.596$." (Introduction); "leading to $1'' \sim 6.7$ kpc at the source redshift of $z=0.596$." (2.1 Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: ALMA Band 3, center 92 GHz (combined with ATCA 15 mm data)  
  > "we combined ALMA Band 3 data of the Phoenix cluster (see (cite: kit20) for details). The center frequency is 92 GHz" (4.2 Frequency Spectra)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.9'' x 1.6'' (using >30k lambda baselines)  
  > "the beam FWHM is $1.9\ensuremath{''} \times 1.6\ensuremath{''}$ (using $>30k\lambda$ baselines)" (4.2 Frequency Spectra)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **ATCA**: Primary 15 mm (17 and 19 GHz) observations, 6A configuration, Project C3190  
  > "Our observations were made with the ATCA in November 1 and 2 in 2017 (Project C3190, see Table [\[t01\]](#t01))." (2 Observation and Data Reduction)
- Other facility **Chandra**: Archival soft X-ray data (ObsID 13401, 16135, 16545) for residual map  
  > "we made an X-ray surface brightness residual map using *Chandra X-ray Observatory* archival data of the Phoenix cluster (ObsID: 13401, 16135, and 16545)." (5.3 Radio Lobes)
- Other facility **HST**: F814W image for comparison  
  > "*Hubble Space Telescope* (*HST*) F814W (814 nm, I band, (cite: mcd15), the coordinate offset is not corrected)" (5.2 Extended Emissions)
- External data: ALMA Band 6 233 GHz continuum and CO(3-2) data / upper limits  
  > "we made superposed images with ALMA CO(3-2) and ALMA 233 GHz continuum (cite: rus17)" (5.2 Extended Emissions) [from Russell et al. 2017 (cite: rus17)]
- External data: ALMA Band 3 data details  
  > "we combined ALMA Band 3 data of the Phoenix cluster (see (cite: kit20) for details)" (4.2 Frequency Spectra) [from Kitayama et al. 2020 (cite: kit20)]

## Processing

### Calibration

- pipeline or manual: ATCA data reduced with MIRIAD; ALMA calibration not described  
  > "Data reduction was performed with the MIRIAD software (cite: sau95) version 1.5 following the standard procedures unless otherwise specified." (2 Observation and Data Reduction)
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

- ALMA Band 3 data reduction and imaging details  
  > "we combined ALMA Band 3 data of the Phoenix cluster (see (cite: kit20) for details)." (4.2 Frequency Spectra) [from Kitayama et al. 2020 (cite: kit20)]

### Not stated but needed to reproduce (our reading)

- ALMA project code, calibration, imaging parameters for Band 3 data
- ALMA Band 3 flux density of Sources C1-C4 and W
- ALMA Band 6 upper limits values

## Analysis recipe

1. **ATCA flux measurement and spectral index**: Point-source fits with IMFIT; error-weighted least-squares power-law fit of four in-band images  
  > "We evaluated flux densities of Sources C1 and W using the MIRIAD task IMFIT with the option OBJECT=POINT." (4.1 Synthesized Images)
   - software: MIRIAD
   - fitting: _not stated_
   - validation: _not stated_
2. **Combine ATCA 18 GHz with ALMA 92 GHz for spectra and astrometric cross-match**: Spectral index from ATCA 18 GHz and ALMA 92 GHz; positions cross-matched  
  > "The results of the spectral index measurement using ATCA 18 GHz and ALMA 92 GHz data are shown in figure [2](#f02)." (4.2 Frequency Spectra)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **MIRIAD** 1.5: ATCA data reduction, imaging, self-calibration, flux fitting  
  > "Data reduction was performed with the MIRIAD software (cite: sau95) version 1.5" (2 Observation and Data Reduction)
- **CIAO** 4.9: Chandra data reprocessing  
  > "we reprocessed the data using *Chandra* Interactive Analysis of Observations (CIAO; (cite: fru06)) version 4.9" (5.3 Radio Lobes)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Source C1 flux density at 18 GHz | 3.395 | 0.132 | mJy | 1 | We obtained the flux densities of 3.395 $\pm$ 0.132 mJy for Source C1 |
| Source C1 spectral index ATCA+ALMA | -0.37 | not stated | dimensionless | 2 | We obtain a flatter ($\alpha=-0.37$) spectrum for Source C1 compared to the in-band spectrum |
| Source C1 in-band spectral index | -0.50 | not stated | dimensionless | 1 | We obtained the in-band spectral index of $\alpha=-0.50$ for the brightest Source C1. |
| Source W spectral index | -0.58 (with 19.5 GHz), -0.62 (without) | not stated | dimensionless | 2 | for Source W, $\alpha= -0.58$ and $-0.62$ with and without the data at 19.5 GHz in the fit |

## Qualitative findings

- Diffuse bipolar structures aligned with X-ray cavities are likely radio lobes; C3 and C4 are likely young jets  
  > "They are likely radio jets/lobes, whose sizes are $\sim 10$–$20$ kpc and locations are aligned with X-ray cavities." (abstract)

## Claim tuples

- H: Radio jets/lobes exist in the Phoenix BCG | E: ATCA 15 mm imaging at sub-arcsec resolution, compared with Chandra residuals | R: Bipolar diffuse structures C5, C6 aligned with X-ray cavities | F: They are radio lobes with ages ~10 Myr | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): ALMA used only for spectra; its processing is deferred to another paper
- Caveat (inferred, ours): Interpretation of extended emission mechanisms is qualitative

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA data processing details and project code
- Missing: ATCA Band 3 flux values
- Data volume (inferred): small to moderate for ALMA; ATCA data separate (~10s GB)
- Score (inferred): 2/5, ALMA is a minor component and its processing is inherited from another paper.
- Rediscovery candidate: no, ALMA role minor; project code not stated.

## Links

- Companion: Kitayama et al. 2020 (cite: kit20) (ALMA Band 3 data details)

## Checks

```json
{
 "quotes": 27,
 "quotes_ok": 27,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.00894.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 58,
  "stated": 18,
  "rate": 0.31
 },
 "evidence_ok": true
}
```
