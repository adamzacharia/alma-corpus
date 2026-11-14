# High-resolution Optical IFU Spectroscopy of the Complex Galaxy Merger II Zw 096

`2025ApJ...990..136R` | The Astrophysical Journal 2025 | first author: Riesco, Clemente | arXiv: 2507.06339 | DOI: 10.3847/1538-4357/adee18

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What are the morphology, kinematics, ionization and merger stage of the merging LIRG II ZW 096, and does the compact D1 region host an obscured AGN?  
  > "By combining this information with Chandra X-ray and ALMA Band 3 data, we aim to understand the nature of regions like D1 and reconstruct the system’s dynamical stage" (Introduction)
- Target **II ZW 096**: coordinates _not stated_; z/distance z = 0.0365  
  > "It is a local ($z=0.0365$) merging system with $L_{\text{IR}} = 8.7 \times 10^{11}\,L_{\odot}$ (cite: Armus2009)." (Introduction); distance from Armus2009 (GOALS)  
  > "It is a local ($z=0.0365$) merging system with $L_{\text{IR}} = 8.7 \times 10^{11}\,L_{\odot}$ (cite: Armus2009)." (Introduction)

## Data provenance

- ALMA projects: 2017.1.01235.S
- bands: Band 3 continuum (84–116 GHz)  
  > "The ALMA Band 3 continuum emission (84–116 GHz) can trace thermal dust emission." (6.2 Evidence for an AGN in D1)
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
- Other facility **VLT/MUSE**: WFM and NFM-AO optical IFU cubes (main data set)  
  > "II ZW 096 was observed with MUSE in the Wide Field Mode (WFM) on September 23, 2016 (program ID 097.B-0427; PI G. Privon)" (2.1 Data description and basic reduction)
- Other facility **Chandra ACIS**: Soft and hard X-ray images for hardness ratios (archival, 14.57 ks)  
  > "on 2007-09-10, with an exposure time of 14.57 ks" (5.1 Data description)
- Other facility **JWST and HST**: MIRI F560W, NIRCam F356W and HST ACS/NICMOS images for context and stellar masses  
  > "HST/ACS F435W (optical; blue) (PID 11196, PI A. Evans, (cite: Inami2010))" (3 Morphological Description)
- External data: CO/ALMA source detections at 0.16'' resolution used to mark sources in figures  
  > "The blue sources correspond to CO/ALMA detections (cite: Wu2022), with a spatial resolution of 0.16$''$" (3 Morphological Description) [from Wu2022]
- External data: X-ray flux of the C+D region used with the 100 GHz flux for the NH limit  
  > "Using the X-ray flux from the C+D region (cite: Ricci2021) and the 100 GHz flux from ALMA Band 3" (6.2 Evidence for an AGN in D1) [from Ricci2021]

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

- F(2-10 keV)/F(100 GHz) relation used for NH upper limit  
  > "we can compute an upper limit for the column density, $\text{N}_{\text{H}}$, by applying the $\text{F}_{2-10\text{:keV}}/\text{F}_{100\text{\:GHz}}$ relation from (cite: Ricci2023)" (6.2 Evidence for an AGN in D1) [from Ricci2023]

### Not stated but needed to reproduce (our reading)

- ALMA Band 3 observation details, calibration and imaging (beam, rms, CASA version) are not given
- How the 100 GHz flux of 1.4e-3 Jy was measured (aperture, region) is not stated
- X-ray flux value of C+D used in the ratio is not given

## Analysis recipe

1. **Derive the 100 GHz AGN-based NH limit**: Assume all 100 GHz emission is AGN, apply F(2-10keV)/F(100GHz) relation with C+D X-ray flux  
  > "If we assume that all the 100 GHz emission comes from the AGN, we can compute an upper limit for the column density" (6.2 Evidence for an AGN in D1)
   - parameter: S_nu(100 GHz) = 1.4e-3 Jy  
  > "the 100 GHz flux from ALMA Band 3 ($S_{\nu} = 1.4 \times 10^{-3} \, \text{Jy}$)" (6.2 Evidence for an AGN in D1)
   - assumption: All 100 GHz emission from AGN  
  > "If we assume that all the 100 GHz emission comes from the AGN" (6.2 Evidence for an AGN in D1)
   - fitting: _not stated_
   - validation: Compared with log NH ~ 24.1-24.4 from Garcia-Bernete2024  
  > "consistent with the results obtained by (cite: Garcia-Bernete2024) of a log N$_{\text{H}} (\text{cm}^{-2}) \; \sim$ 24.1 - 24.4" (6.2 Evidence for an AGN in D1)

## Software

- **ESO MUSE pipeline** 2.6 (WFM), 2.8.1 (NFM): MUSE data reduction  
  > "versions 2.6 and 2.8.1 for the WFM and NFM data, respectively" (2.1 Data description and basic reduction)
- **pPXF** : stellar continuum fitting  
  > "the penalized pixel-fitting (pPXF) package (cite: Cappellari2016) was employed" (2.2 Data analysis)
- **PySpecKit** : emission line Gaussian fits  
  > "The Python Spectroscopic Toolkit package (cite: Ginsburg2022) was used to perform the emission line fitting." (2.2 Data analysis)
- **Bbarolo** : 2D velocity field modeling  
  > "We use the `Bbarolo` software (cite: DiTeodoro2015) on its 2D version mode to model the velocity fields" (4.2.1 Kinematic modeling)
- **CIAO** 4.15: Chandra reduction and counts  
  > "using CIAO v.4.15 and the Chandra Calibration Database, CALDB v.4.10.7" (5.1 Data description)
- **CLOUDY** : starburst model for D1 line ratios  
  > "we use a pure SB model with `CLOUDY` (cite: Ferland2013)" (6.2 Evidence for an AGN in D1)
- **MAPPINGS III** : shock models  
  > "in combination with shocks emission modeled using `MAPPINGS III` (cite: Allen2008)" (6.2 Evidence for an AGN in D1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 100 GHz flux of D1 (ALMA Band 3) | 1.4e-3 | not stated | Jy | 1 | $S_{\nu} = 1.4 \times 10^{-3} \, \text{Jy}$ |
| log NH lower limit from X-ray/100 GHz ratio | > 24.5 | not stated | cm^-2 | 1 | we obtain a ratio $< 2.7$, suggesting log N$_{\text{H}} (\text{cm}^{-2}) \; > 24.5$ |
| Hardness ratio of D1 | 0.1 | 0.3 | dimensionless | 0 | The HR of D1 is 0.1$\pm$0.3. |
| II ZW 096A PA / inclination | 99 / 40 | 24 / 21 | deg | 0 | the model converge to a PA = 99$^\circ$ $\pm$ 24$^\circ$, and $i$ = 40$^\circ$ $\pm$ 21$^\circ$ |

## Qualitative findings


## Claim tuples

- H: Does D1 host an obscured AGN? | E: MUSE NFM diagnostics, SB+shock models, ALMA Band 3 flux and Chandra HR | R: Models cannot reproduce D1 ratios; log NH > 24.5; HR 0.1±0.3 | F: D1 likely hosts a highly obscured AGN with a compact starburst | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): The 100 GHz-based NH should be treated with caution because dust may contribute at 100 GHz  
  > "as dust may significantly contribute at 100 GHz" (6.2 Evidence for an AGN in D1)
- Caveat (inferred, ours): ALMA used only as a single flux and contours; synchrotron versus dust origin not resolved
- Caveat (inferred, ours): HR for D1 is not statistically significant

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA calibration and imaging details
- Missing: Aperture for ALMA flux
- Data volume (inferred): small for ALMA part; MUSE cubes several GB
- Score (inferred): 2/5, ALMA is minor and unspecified in processing; MUSE-centered analysis.
- Rediscovery candidate: no, ALMA role is a single flux value without processing recipe.

## Links

- Companion: Wu2022 (ALMA CO data of the same system)
- Related: GOALS

## Checks

```json
{
 "quotes": 30,
 "quotes_ok": 30,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 62,
  "stated": 22,
  "rate": 0.355
 },
 "evidence_ok": true
}
```
