# Dusty starburst galaxies in the early Universe as revealed by gravitational lensing

`2013Natur.495..344V` | Nature 2013 | first author: Vieira, J. D. | arXiv: 1303.2723 | DOI: 10.1038/nature12001

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What is the redshift distribution of SPT millimetre-selected dusty starburst galaxies, especially at z>4, and are they gravitationally lensed?  
  > "It has, however, been difficult to measure the complete redshift" (abstract)
- Target **26 SPT dusty-spectrum sources (spectroscopic sample); 47 imaged at 870 um**: coordinates _not stated_; z/distance z from 1.85 (placeholder) up to 5.7; median z = 3.5  
  > "We selected 47 sources for imaging and 26 sources for spectroscopy with ALMA; 24 of the 26 spectroscopic sources were also in the imaging sample." (Sample Selection); distance from CO/CI line redshifts from ALMA 3 mm spectra, with VLT/APEX for some  
  > "We selected 47 sources for imaging and 26 sources for spectroscopy with ALMA; 24 of the 26 spectroscopic sources were also in the imaging sample." (Sample Selection)

## Data provenance

- ALMA projects: _none stated_
- bands: 3 mm spectroscopy and 870 um continuum imaging  
  > "we imaged 47 SPT sources with ALMA at 870 µm in two array configurations" (main text)
- frequencies and spectral setup: 3 mm window, 84.2-114.9 GHz, five spectral tunings  
  > "We conducted a redshift search in the 3 mm atmospheric transmission window with ALMA" (main text); "using five spectral tunings of the ALMA receivers to cover" (main text)
- continuum bandwidth: _not stated_
- arrays: ALMA Cycle 0, 16 antennas, compact and extended configurations  
  > "even with its restricted early science capabilities and only 16 antennas" (main text)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 870 um: 1.5'' and 0.5''; 3 mm beam 7''x5'' to 5''x3''  
  > "which provide angular resolutions of 1.5 [′′] and 0.5 [′′] (FWHM)." (main text); "The synthesized beam size ranges from 7 [′′] ×5 [′′] to 5 [′′] ×3 [′′] over the frequency range of the search" (Figure 2 caption)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: about 1 min per source per config at 870 um (about 2 min total); about 10 min per source at 3 mm  
  > "Integration times of only one minute per source are adequate to show that the sources are resolved into arcs or Einstein" (main text); "Total integration times for each source were roughly ten minutes." (Figure 2 caption)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO CO(3-2), CO(4-3), CO(5-6), CO(6-5) (not stated)
- Line: CI 3P1-3P0 (not stated)
- Other facility **SPT**: Source selection from 1.4 and 2.0 mm survey  
  > "by selecting sources with dust-like spectral indexes in the 1.4 and 2.0 mm SPT bands" (main text)
- Other facility **APEX/LABOCA**: 870 um follow-up for positions and photometry  
  > "followup observations with the LABOCA 870 µm camera on the Atacama Pathfinder Experiment telescope to improve the accu" (Sample Selection)
- Other facility **Herschel/SPIRE**: 500, 350, 250 um photometry for dust temperatures  
  > "SPT 2 & 1 mm, APEX/LABOCA 870 µm and _Herschel_ /SPIRE 500, 350, 250 µm observations [23]" (main text)
- Other facility **HST, VLT, SART, Spitzer**: Near-IR imaging of foreground lenses; VLT redshifts  
  > "The greyscale images are NIR exposures from the _Hubble Space Telescope_ (co-added F160W and F110W filters), the Very Large Telescope" (Figure 1 caption)
- External data: Comparison redshift distributions of radio-identified and COSMOS mm-identified starbursts  
  > "The redshift distribution [24] of millimetre-identified starburst galaxies" (Figure 3 caption) [from Smolcic et al. (cite: 24)]
- External data: Two additional SPT sources with spectroscopic redshifts  
  > "we include an additional two SPT sources with spectroscopic redshifts [22]" (main text) [from Greve et al. (cite: 22)]

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

- Lens modelling in visibility space with simultaneous phase-error correction  
  > "treats the interferometer data in their native measurement space, rather than through reconstructed sky" (main text) [from Hezaveh et al. 2012 (cite: 11)]
- Full line analysis, redshift determination, selection effects  
  > "is reported in a companion paper [23] ." (main text) [from Weiß et al. (cite: 23)]
- SPT target extraction procedure  
  > "according to the procedure described in a previous paper [4]" (Sample Selection) [from Vieira et al. 2010 (cite: 4)]

### Not stated but needed to reproduce (our reading)

- ALMA project codes
- CASA version and calibration procedure
- imaging weighting, cleaning and continuum subtraction details
- line detection criteria and line fitting method
- lens model parameters
- source coordinates

## Analysis recipe

1. **Select sources**: SPT dusty spectral index selection, removing IRAS and SUMSS counterparts, 1.4 mm flux > 20 mJy  
  > "counterparts in the IRAS Faint Source Catalog [6] (typically z < 0.03) were removed" (main text)
   - fitting: _not stated_
   - validation: _not stated_
2. **Determine redshifts from 3 mm lines**: Identify CO/CI lines in five tunings; unique redshift where multiple lines; single-line cases resolved by dust temperature from photometry  
  > "after excluding redshift choices for which the implied dust temperature, derived" (main text)
   - assumption: No-line sources placed at z = 1.85 in the redshift desert  
  > "We tentatively and conservatively place these at z = 1.85, in the middle of the" (main text)
   - fitting: _not stated_
   - validation: VLT/APEX data confirmed 6 redshifts  
  > "or with the addition of data from the Very Large Telescope and/or the Atacama" (main text)
3. **Lens modelling and magnification**: Visibility-space lens models for four complete and eight preliminary lenses  
  > "indicate lensing magnifications between 4 and 22." (main text)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare redshift distributions**: Kolmogorov-Smirnov test against radio-identified and COSMOS samples  
  > "< 10 [−][5] by the Kolmogorov-Smirnov test." (main text)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Sources with lines detected | 23 of 26 | not stated | dimensionless | 2 | We detect spectral lines in 23 out of 26 sources |
| Median redshift of full sample | 3.5 | not stated | dimensionless | 2 | The median redshift of our full sample is z med = 3.5. |
| Lensing magnifications | 4 to 22 | not stated | dimensionless | 3 | indicate lensing magnifications between 4 and 22. |
| KS probability vs radio-identified sample (z>2) | <1e-5 | not stated | dimensionless | 4 | < 10 [−][5] by the Kolmogorov-Smirnov test. |
| KS probability vs COSMOS sample (z>2) | 0.43 | not stated | dimensionless | 4 | these objects and the SPT-selected sources are drawn from the same parent distribution is 0.43 |

## Qualitative findings

- At least 10 sources lie at z>4; two at z=5.7  
  > "At least 10 of the sources are found to lie at z > 4" (abstract)

## Claim tuples

- H: Are the brightest mm sources strongly lensed? | E: ALMA 870 um imaging of 47 sources | R: Arcs and rings; emission coincides with foreground massive galaxies at different redshifts | F: Sources are strongly lensed | **supported**
- H: Is the high-z fraction of dusty starbursts larger than thought? | E: 3 mm redshift survey, KS comparison with radio-identified sample | R: Median z 3.5 vs 2.2 | F: High-z fraction greater than previously thought | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): 3 mm beam too large to resolve velocity structure  
  > "inadequate to spatially resolve the velocity structure of the lensed sources." (Figure 2 caption)
- Caveat (inferred, ours): Lensing selection biases comparison with unlensed samples
- Caveat (inferred, ours): Single-line redshifts rely on dust temperature priors
- Caveat (inferred, ours): Lens models mostly preliminary

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: project codes
- Missing: reduction details
- Missing: line-finding criteria
- Missing: lens model code and inputs
- Data volume (inferred): tens of GB
- Score (inferred): 2/5, Short Nature letter; methods deferred to companion papers; no processing details.
- Rediscovery candidate: no, Recipe incomplete; details are in companion papers.

## Links

- Method: Hezaveh et al. 2012 (cite: 11) (Visibility-space lens modelling)
- Companion: Weiß et al. (cite: 23) (Full line and redshift analysis)
- Related: SPT survey
- Related: ALMA Cycle 0

## Checks

```json
{
 "quotes": 38,
 "quotes_ok": 38,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00957.S",
  "2011.0.00958.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 25,
  "rate": 0.373
 },
 "evidence_ok": true
}
```
