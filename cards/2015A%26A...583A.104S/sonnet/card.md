# The nuclear gas disk of NGC 1566 dissected by SINFONI and ALMA

`2015A&A...583A.104S` | Astronomy and Astrophysics 2015 | first author: Smajić, S. | arXiv: 1508.02664 | DOI: 10.1051/0004-6361/201424850

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Do the hot gas distribution and kinematics seen with SINFONI in the central 10''x10'' of NGC 1566 resemble the cold gas seen with ALMA, and is there evidence for feeding, feedback and star formation around the AGN?  
  > "We will investigate the central $10\ensuremath{''}\times10\ensuremath{''}$ to find if the hot gas distribution and kinematics are similar to the cold gas observed with ALMA." (1.2 NGC 1566)
- Target **NGC 1566**: coordinates _not stated_; z/distance z≈0.005017; 10 Mpc  
  > "harboring a low luminosity AGN (LLAGN) at a redshift of $z\approx0.005017$" (1.2 NGC 1566); "we adopt a systemic velocity of 1504  km s$^{-1}$ and a distance of 10 Mpc for NGC 1566, following (cite: alloin_recent_1985; combes_ALMA_2014)" (1.2 NGC 1566); distance from Alloin et al. 1985; Combes et al. 2014  
  > "harboring a low luminosity AGN (LLAGN) at a redshift of $z\approx0.005017$" (1.2 NGC 1566); "we adopt a systemic velocity of 1504  km s$^{-1}$ and a distance of 10 Mpc for NGC 1566, following (cite: alloin_recent_1985; combes_ALMA_2014)" (1.2 NGC 1566)

## Data provenance

- ALMA projects: 2011.0.00208.S
- bands: 350 GHz (0.87 mm), 12CO(3-2) and continuum  
  > "We use calibrated 350 GHz ALMA data and compare these with our NIR results." (2 Observation and Data Reduction)
- frequencies and spectral setup: line cube of 50 channels of 10 km/s width  
  > "The line cube comprises 50 channels of 10 km/s width" (2 Observation and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam 0.64''x0.43'' at PA 123 deg  
  > "a beam of $0.64\ensuremath{''}\times0.43\ensuremath{''}$ at an PA of $123\ensuremath{^\circ}$" (2 Observation and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 0.05 mJy/beam continuum; ~1.3 mJy/beam in line cubes  
  > "The rms achieved is $0.05$ mJy beam$^{-1}$ in the continuum and $\sim1.3$ mJy beam$^{-1}$ in the line cubes." (2 Observation and Data Reduction)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archive data, PI Combes  
  > "The final product data is publicly available from the ALMA archive under project ID 2011.0.00208.S (PI: Combes)." (2 Observation and Data Reduction)
- Line: 12CO J=3-2 (not stated)
- Other facility **VLT SINFONI**: H- and K-band integral field spectroscopy of central 10''x10''  
  > "our ESO SINFONI (cite: eisenhauer_sinfoni_2003; bonnet_first_2004-1) observation of NGC 1566 with the Unit Telescope 4 of the Very Large Telescope" (2 Observation and Data Reduction)
- Other facility **HST**: images compared with Brγ emission  
  > "We used observations made with the NASA/ESA Hubble Space Telescope, obtained from the data archive at the Space Telescope Institute." (Acknowledgements)
- Other facility **2MASS**: flux calibration reference for the standard star  
  > "to the flux given by the 2MASS All-sky Point Source Catalogue" (2 Observation and Data Reduction)
- External data: Cold H2 to warm H2 mass ratio (0.3-1.6)e6  
  > "we use the conversion factor derived by (cite: mazzalay_molecular_2013)" (3.2 Gas masses) [from (cite: mazzalay_molecular_2013)]
- External data: Archival ALMA CO(3-2) mass 7e7 Msun in r=18'' FOV  
  > "(cite: combes_ALMA_2014) detect $7\times10^7M_{\odot}$ in their $r=18\ensuremath{''}$ FOV from CO(3-2) observations with ALMA." (3.2 Gas masses) [from (cite: combes_ALMA_2014)]
- External data: H2 UV-excitation models 1-5  
  > "compares our measured level population of the H$_2$ emission lines to UV-excitation models derived by (cite: davies_molecular_2003)." (3.3.2 Level population) [from (cite: davies_molecular_2003)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated final-product ALMA data from archive used  
  > "The final product data is publicly available from the ALMA archive under project ID 2011.0.00208.S (PI: Combes)." (2 Observation and Data Reduction)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: Imaging and parts of analysis with CASA  
  > "Imaging and parts of the analysis have been conducted with the CASA software (cite: mcmullin_casa_2007)." (2 Observation and Data Reduction)
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

- ALMA observational setup, calibration, imaging and quality  
  > "Details on observational setup, calibration, imaging and quality can be found in (cite: combes_ALMA_2014)" (2 Observation and Data Reduction) [from (cite: combes_ALMA_2014)]
- SINFONI reduction details and NIR continuum decomposition  
  > "For more details on the reduction see (cite: smajic_ALMA-backed_2014)." (2 Observation and Data Reduction) [from (cite: smajic_ALMA-backed_2014); (cite: smajic_unveiling_2012)]

### Not stated but needed to reproduce (our reading)

- CASA version and imaging parameters (weighting, cell, masking) for the ALMA cubes
- How the CO(3-2) flux and moment maps were extracted (masks, clipping)
- CO(3-2) to H2 conversion details beyond citing Bolatto et al. 2013
- Continuum-subtraction channels for ALMA data

## Analysis recipe

1. **Compare ALMA CO(3-2) and 0.87 mm maps with SINFONI H2 maps**: Visual comparison of flux, EW, LOSV and dispersion maps  
  > "In general, the $^{12}$CO(3-2) emission is very similar to the H$_2$(1-0)S(1) emission." (3.1.2 Molecular gas)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Estimate cold gas mass from CO(3-2) flux**: CO(3-2) flux with Milky Way conversion factors  
  > "using the Milky Way conversion values from (cite: bolatto_co–h2_2013)" (3.2 Gas masses)
   - assumption: Milky Way CO-to-H2 conversion  
  > "using the Milky Way conversion values from (cite: bolatto_co–h2_2013)" (3.2 Gas masses)
   - fitting: _not stated_
   - validation: Compared with H2-derived masses and Combes et al. 2014  
  > "The values are in good agreement since the bulk of the molecular mass in NGC 1566 is located in the inner 6$\ensuremath{''}$" (3.2 Gas masses)

## Software

- **CASA** : Imaging and parts of the analysis  
  > "Imaging and parts of the analysis have been conducted with the CASA software (cite: mcmullin_casa_2007)." (2 Observation and Data Reduction)
- **IDL routines** : Own routines for SINFONI OH correction, cube creation, line maps and spectra  
  > "was conducted using our own IDL routines." (2 Observation and Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 12CO(3-2) flux, central r=3'' disk | ~570 | not stated | Jy km/s | 2 | We measure a $^{12}$CO(3-2) flux of $\sim570$ Jy km s$^{-1}$ for the central $r=3\ensuremath{''}$ gas disk |
| Gas mass of r=3'' disk from CO(3-2) | ~6.6e7 | not stated | Msun | 2 | we estimate masses of $\sim6.6\times10^7$ M$_\odot$ and $\sim1.4\times10^6$ M$_\odot$ respectively |
| Cold H2 mass in central 10''x10'' from H2 lines | (1.7-9.1)e7 | not stated | Msun | 0 | We find a cold H$_2$ gas mass in the central $10\ensuremath{''}\times10\ensuremath{''}$ of $(1.7-9.1)\times10^{7}$ M$_{\odot}$. |
| Mean BH mass | (5.3±2.9)e6 | 2.9e6 | Msun | 0 | The mean BH mass is $(5.3\pm2.9)\times10^6$M$_\odot$. |

## Qualitative findings

- Warm H2 and cold CO(3-2) show a similar r=3'' disk with nuclear spiral and similar velocity fields  
  > "The LOSV-field is identical in shape, i.e., maxima and disturbances, and value" (3.1.2 Molecular gas)

## Claim tuples

- H: Is the hot gas distribution and kinematics similar to the cold gas seen with ALMA? | E: Compared SINFONI H2(1-0)S(1) maps with ALMA CO(3-2) maps | R: Both show an r=3'' disk with nuclear spiral and LOSV of ±150 km/s; dispersion differs by ~30 km/s | F: Warm and cold molecular gas distribution and velocities are very similar | **supported**
- H: Does NIR-derived cold gas mass agree with ALMA-based mass? | E: Converted warm H2 mass to cold mass and compared with CO(3-2) masses | R: (1.7-9.1)e7 Msun vs 7e7 Msun from Combes et al. | F: Masses agree | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Origin of dust continuum cannot be determined locally due to lack of high resolution radio data  
  > "To decide on the dominating mechanism in local emission regions is not possible due to the lack of high resolution radio data at other frequencies." (3.4.1 The millimeter continuum)
- Caveat (inferred, ours): ALMA data processing is entirely delegated to a previous paper
- Caveat (inferred, ours): Cold gas mass from H2 relies on a wide conversion range
- Caveat (inferred, ours): Resolution mismatch between SINFONI (0.59'') and ALMA beam (0.64x0.43'')

## Reproducibility

- Data public (paper): ALMA data publicly available  
  > "The final product data is publicly available from the ALMA archive under project ID 2011.0.00208.S (PI: Combes)." (2 Observation and Data Reduction)
- Products in archive: _not stated_
- Missing: SINFONI data reduction details
- Missing: ALMA imaging parameters
- Missing: Own IDL routines not released
- Data volume (inferred): ~ a few GB (ALMA Band 7 single-field cube, archive products)
- Score (inferred): 3/5, ALMA part is small and uses public products, but the main results are from SINFONI and the ALMA processing details are deferred to another paper.
- Rediscovery candidate: no, ALMA role is minor and main numeric results rely on non-ALMA SINFONI data.

## Links

- Method: (cite: smajic_ALMA-backed_2014) (SINFONI reduction details)
- Method: (cite: smajic_unveiling_2012) (NIR continuum decomposition)
- Companion: (cite: combes_ALMA_2014) (Source of ALMA observations and calibration)
- Related: NUGA

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
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
  "stated": 27,
  "rate": 0.435
 },
 "evidence_ok": true
}
```
