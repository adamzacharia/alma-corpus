# ISM Masses and the Star formation Law at Z = 1 to 6: ALMA Observations of Dust Continuum in 145 Galaxies in the COSMOS Survey Field

`2016ApJ...820...83S` | The Astrophysical Journal 2016 | first author: Scoville, N. | arXiv: 1511.05149 | DOI: 10.3847/0004-637X/820/2/83

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies
- Question: Does the cosmic evolution of star formation reflect larger ISM masses or higher star formation efficiency, and do galaxies above the Main Sequence have more gas or higher efficiency? Use RJ dust continuum as a calibrated gas mass tracer.  
  > "2) are galaxies above the MS converting their gas to stars with higher efficiency or do they simply have more gas than those on the MS?" (1. INTRODUCTION)
- Target **145 COSMOS-field star-forming galaxies at z~1.15, 2.2, 4.4**: coordinates individual RA/Dec in Tables B1-B3 (COSMOS field)  
  > "Our sample of 145 galaxies is taken from the COSMOS 2 deg [2] survey (Scoville et al. 2007)." (3. GALAXY SAMPLES FOR ALMA); z/distance z~1.15, 2.2, 4.4 (photometric, 48 spectroscopic)  
  > "Our sample of 145 galaxies is taken from the COSMOS 2 deg [2] survey (Scoville et al. 2007)." (3. GALAXY SAMPLES FOR ALMA); distance from Ilbert et al. 2013; Laigle 2015 photometric redshift catalogs  
  > "Our sample of 145 galaxies is taken from the COSMOS 2 deg [2] survey (Scoville et al. 2007)." (3. GALAXY SAMPLES FOR ALMA)

## Data provenance

- ALMA projects: 2013.1.00034.S, 2013.1.00111.S
- bands: Band 7 (345 GHz) for z=1.15 & 2.2; Band 6 (240 GHz) for z=4.4  
  > "The z = 1.15 & 2.2 samples were observed in Band 7 (345 GHz), the z = 4.4 sample in Band 6 (240 GHz)." (4. OBSERVATIONS AND FLUX MEASUREMENTS)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthesized beams ~0.6-1 arcsec  
  > "Synthesized beam sizes were _≃_ 0 _._ 6 _−_ 1 _[′′]_ ." (4. OBSERVATIONS AND FLUX MEASUREMENTS)
- max recoverable scale: _not stated_
- sensitivity: average rms 0.152 (Band 7) and 0.065 mJy/beam (Band 6)  
  > "average rms sensitivities were 0.152 (Band 7) and 0.065 mJy beam _[−]_ [1] (Band 6)." (4. OBSERVATIONS AND FLUX MEASUREMENTS)
- time on source: ~2 minutes per galaxy  
  > "On-source integration times were _∼_ 2 minutes per galaxy" (4. OBSERVATIONS AND FLUX MEASUREMENTS)
- observing dates: 2014-2015 (Cycle 2)  
  > "The ALMA Cycle 2 observations (#2013.1.00034.S) were obtained in 2014-2015." (4. OBSERVATIONS AND FLUX MEASUREMENTS)
- pi or archival as stated: _not stated_
- Other facility **Herschel PACS/SPIRE**: Far-IR photometry for SFRs of sample and SPIRE 350/500 um fluxes for calibration galaxies  
  > "they are derived from the rest frame UV continuum and infrared using Herschel PACS and SPIRE data" (3. GALAXY SAMPLES FOR ALMA)
- Other facility **JVLA**: CO(1-0) for the SMG calibration sample  
  > "we make use of a sample of 30 SMGs for which there exist good SNR measurements of CO (1-0) from JVLA." (A.4)
- External data: Photometric redshifts and stellar masses  
  > "The photometric redshifts and stellar masses of the galaxies are from McCracken et al. (2012); Ilbert et al." (3. GALAXY SAMPLES FOR ALMA) [from McCracken et al. 2012; Ilbert et al. 2013; Laigle 2015]
- External data: SFRs and Main Sequence definition  
  > "Here, we use Lee et al. (2015) with no evolution of the MS beyond z = 2.5" (3. GALAXY SAMPLES FOR ALMA) [from Lee et al. (2015)]
- External data: CO(1-0) fluxes of local galaxies  
  > "CO (1-0) line fluxes from Young et al. (1995)" (Table A1) [from Young et al. (1995)]
- External data: Emissivity index beta = 1.8 +/- 0.1  
  > "based on the extensive Planck data in the Galaxy (Planck Collaboration 2011a)" (2. LONG WAVELENGTH DUST CONTINUUM AS A GAS MASS TRACER) [from Planck Collaboration 2011a]

## Processing

### Calibration

- pipeline or manual: calibrated with CASA (details not given)  
  > "Data were calibrated and imaged with natural weighting using CASA." (4. OBSERVATIONS AND FLUX MEASUREMENTS)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Data were calibrated and imaged with natural weighting using CASA." (4. OBSERVATIONS AND FLUX MEASUREMENTS)
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

- SFR derivation from UV and Herschel IR  
  > "as detailed in Ilbert et al. (2013) and in Lee et al. (2015)" (3. GALAXY SAMPLES FOR ALMA) [from Ilbert et al. (2013); Lee et al. (2015)]
- L_IR from modified greybody plus mid-IR power law  
  > "coupled, modified greybody plus mid-infrared power law, as in Casey (2012)." (3. GALAXY SAMPLES FOR ALMA) [from Casey (2012)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/pipeline details
- Array configurations, baselines, spectral windows and bandwidth
- Image size, cell size, and CLEAN settings
- How stacking was done (positions, weighting, noise)
- Which galaxies of the original 180 were removed and the data of the second project 2013.1.00111.S
- Chu et al. in prep. SPIRE fluxes for ULIRGs
- Flux calibrators and flux scale uncertainty

## Analysis recipe

1. **Calibrate alpha_850 empirically**: Ratio of rest-frame 850um specific luminosity to CO(1-0)-derived molecular mass for 28 local galaxies, 12 ULIRGs and 30 SMGs; mean adopted  
  > "The mean of the local star-forming galaxies, ULIRGs and SMGs is" (A.4)
   - parameter: Td=25 K, beta=1.8  
  > "we adopt _**<**_ **T** **d** _**>**_ **M** **=** **25 K** for numerical estimates when necessary" (A.2)
   - assumption: Galactic XCO = 3e20 for all galaxies (alpha_CO=6.5 incl. He)  
  > "We have chosen to use a single conversion factor ( _α_ _CO_ or X _CO_ ) for all galaxies." (A.4)
   - fitting: _not stated_
   - validation: Agreement with Planck Galactic value 6.2e19  
  > "This value for _α_ 850 _µ_ m is in excellent agreement with that obtained from Planck data for the" (2. LONG WAVELENGTH DUST CONTINUUM AS A GAS MASS TRACER)
2. **Measure ALMA fluxes**: Peak or aperture-integrated flux within central 3 arcsec; detection 2 sigma in S_tot or 3.6 sigma in S_peak; noise from 100 displaced apertures  
  > "We required a 2 _σ_ detection in S tot or 3.6 _σ_ in S peak, in order that the detection be clas" (4. OBSERVATIONS AND FLUX MEASUREMENTS)
   - software: CASA
   - fitting: _not stated_
   - validation: Thresholds give less than one spurious detection in 145 objects  
  > "These limits ensure that there would be less than one spurious detection in the145 objects." (4. OBSERVATIONS AND FLUX MEASUREMENTS)
3. **Stack galaxies in cells of M_stellar and sSFR**: Average stacking of images per cell (preferred over median for small samples)  
  > "we used the average stack rather than the median; for such small samples the median can have higher dispersion." (5. STACKED SAMPLES)
   - fitting: _not stated_
   - validation: _not stated_
4. **Convert flux to molecular gas mass**: Equation A14 with RJ correction, using alpha_850 = 6.7e19  
  > "The mass of molecular gas is then derived from the observed flux density using Equation A14" (2. LONG WAVELENGTH DUST CONTINUUM AS A GAS MASS TRACER)
   - assumption: Td=25 K, beta=1.8  
  > "Here we advocate adoption of a single value _< T_ _D_ _>_ _M_ = 25K" (2.1. Dust Temperatures)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit gas fraction and star formation law**: Non-linear least squares fits to stacked cells (Eq. 1, Eq. 2)  
  > "we obtained a least-squares fit for the SFR dependence on gas mass, redshift and elevation above the main sequence" (5.3. Star Formation Law at High Redshift)
   - software: LMFIT
   - fitting: Levenberg-Marquardt; uncertainties from LM procedure  
  > "the parameter uncertainties in Equation 1 are those obtained from the Levenberg-Marquardt algorithm." (5. STACKED SAMPLES)
   - validation: Compared with 1.1 mm stacking results of Bethermin 2015 and Alvarez-Marquez 2015  
  > "Figure 8 indicates reasonable agreement between the ALMA results presented here and the 1.1 mm stacking results" (5.3. Star Formation Law at High Redshift)

## Software

- **CASA** : calibration and imaging  
  > "Data were calibrated and imaged with natural weighting using CASA." (4. OBSERVATIONS AND FLUX MEASUREMENTS)
- **LMFIT (IDL)** : Levenberg-Marquardt non-linear least squares fits  
  > "the Levenberg-Marquardt algorithm for non-linear least squares fitting (LMFIT)" (5.2. Gas Mass Fractions)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| alpha_850um | 6.7e19 | 1.7e19 | erg s-1 Hz-1 Msun-1 | 1 | **6** _**.**_ **7** _**±**_ **1** _**.**_ **7** _**×**_ **10** **[19]** **erg** **sec** |
| SF law normalization | 35 | 16 | Msun/yr | 5 | SFR=(35 _±_ 16) |
| SF law gas-mass exponent | 0.89 | 0.12 | dimensionless | 5 | 0 _._ 89 _±_ 0 _._ 12 |
| SF law sSFR/sSFR_MS exponent | 0.23 | 0.15 | dimensionless | 5 | 0 _._ 23 _±_ 0 _._ 15 |
| Detection rates at z=1.15, 2.2, 4.4 | ~70, 85, 50% | not stated | percent | 2 | The detection rates for individual galaxies are _∼_ 70, 85 and 50% at z = 1.15, 2.2 and 4.4 respectively. |
| Gas mass fractions | 0.2-0.5 on MS, up to 0.5-0.8 for highest sSFR cells | not stated | dimensionless | 4 | range from _∼_ 0 _._ 2 _−_ 0 _._ 5 on the MS (bottom two rows of cells) up to 0.5 - 0.8 for the highest sSFR cells. |

## Qualitative findings

- Starbursts are largely gas-rich galaxies rather than more efficient star formers  
  > "Thus, the so-called starburst population is largely a population of very gas-rich galaxies rather than galaxies converting gas to stars more efficiently." (6. ON VERSUS ABOVE THE MS)

## Claim tuples

- H: A single star formation law holds at z>1 for MS and above-MS galaxies | E: Fit stacked cells SFR vs gas mass, z, sSFR | R: SFR ∝ Mmol^0.89 (1+z)^0.95 sSFR^0.23 | F: Approximately linear SF law with higher efficiency at higher z | **supported**
- H: Galaxies above MS have higher efficiency than MS galaxies | E: Compare depletion times on and above MS | R: Depletion times differ by less than a factor 2 | F: Higher SFRs due to more gas, not efficiency | **supported**
- H: High-z gas depletion times differ from low z | E: Compare Mmol/SFR with nearby galaxies | R: 2-5 times shorter | F: Different star formation mode at high z | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Dust continuum detectable in minutes, versus an hour or more for CO  
  > "the dust continuum can also be detected by ALMA in just a few minutes of observing, whereas for the same galaxies, CO would require an hour or more with ALMA." (1. INTRODUCTION)
- Alternative: Variable dust temperature from SED fitting rejected since it is luminosity-weighted  
  > "it would be wrong to use a variable temperature correction based on fitting to the overall spectral energy distribution (SED)" (2.1. Dust Temperatures)
- How they decided it was enough: _not stated_
- Limitation (authors): Calibration restricted to high stellar mass; low-metallicity systems not probed  
  > "so we are not exploring low metallicity systems where the calibration may depart from constancy" (7. SUMMARY AND COMMENTS)
- Caveat (inferred, ours): Gas masses rest on a single XCO and Td=25 K, so conclusions depend on these assumptions
- Caveat (inferred, ours): Sample selection not representative and refined after observations
- Caveat (inferred, ours): Stack cells contain few galaxies, and cell values are not independent
- Caveat (inferred, ours): Calibration partly uses lensed SMGs

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration and imaging parameters
- Missing: Stacking procedure details
- Missing: Chu et al. in prep. fluxes
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, Tables give fluxes and masses, but processing and stacking details are sparse.
- Rediscovery candidate: no, Processing and stacking recipe incomplete, though tables allow partial re-derivation.

## Links

- Method: Scoville et al. (2013) (initial dust-continuum mass calibration)
- Companion: Lee et al. (2015) (Herschel SFRs and Main Sequence)
- Related: COSMOS
- Related: KINGFISH
- Related: Herschel VNGS
- Related: GOALS

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 37,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
