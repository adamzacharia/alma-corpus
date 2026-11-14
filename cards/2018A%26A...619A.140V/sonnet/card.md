# Millimeter-wave spectroscopy and modeling of 1,2-butanediol . Laboratory spectrum in the 59.6-103.6 GHz region and comparison with the ALMA archived observations

`2018A&A...619A.140V` | Astronomy and Astrophysics 2018 | first author: Vigorito, A. | arXiv: - | DOI: 10.1051/0004-6361/201833489

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: astrochemistry, star_formation
- Question: Can the laboratory rotational spectrum of 1,2-butanediol conformers be characterized and used to search for the molecule toward IRAS 16293-2422 B in archival ALMA Band 3 data?  
  > "We explore the conformational space of 1,2-butanediol and provide sets of spectroscopic parameters to facilitate searches for this molecule at millimeter wavelengths." (abstract)
- Target **IRAS 16293-2422 B**: coordinates RA = 16h32m22.612s, Dec = −24°28'32.588"  
  > "centered on the 102.690 GHz peak of 12ED in component B (RA = 16h 32m 22.s612; Dec = −24◦ 28′ 32′′.588)" (6 Search on ALMA data archives); "corrected for the system V LSR of 2.7 km s −1 ; Jørgensen et al. 2011" (Figure 6 caption); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00712.S
- bands: Band 3  
  > "publicly available ALMA Band 3 data on IRAS 16293-2422 B" (abstract)
- frequencies and spectral setup: 89.49–89.72, 92.78–93.01, 102.49–102.72, 103.18–103.41 GHz; 60 kHz channel spacing  
  > "frequency coverage (89.49–89.72, 92.78–93.01, 102.49–102.72, 103.18–103.41 GHz) and the spectral resolution (60 kHz channel spacing)" (6 Search on ALMA data archives)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: rms 1.89 mJy/beam from an off-source spectrum  
  > "rms level (1.89 mJy beam −1 ) represented by a spectrum extracted from an off source position" (Figure 6 caption)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Public archival data  
  > "Several observations on this source were found in the public data of the ALMA Science Archive." (6 Search on ALMA data archives)
- Line: aG'Ag-1,2-butanediol 30(x,30)-29(x,29) mu_b and mu_c R-type quartet (~102496–102503 MHz)
- External data: Ethylene glycol line width of 1 km/s and 300 K source temperature used as assumptions  
  > "Assuming a temperature of 300 K and a line width of 1 km s −1, as measured for ethylene glycol (Jørgensen et al. 2016)" (6 Search on ALMA data archives) [from Jørgensen et al. 2016]
- Simulation/model as data: B3LYP-D3/aug-cc-pVTZ quantum chemical calculations of 24 hydrogen-bonded conformers (Gaussian 09)  
  > "Their structures were optimized at the B3LYPD3/aug-cc-pVTZ level of calculation using the Gaussian 09 quantum chemistry package" (2 Conformational analysis)

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

- Laboratory spectrometer setup  
  > "With respect to the ordinary experimental setup described in Melandri et al. (1995, 1996) and Calabrese et al. (2015)" (3 Experiment) [from Melandri et al. (1995, 1996); Calabrese et al. (2015)]

### Not stated but needed to reproduce (our reading)

- Calibration details, flux calibrator and whether archive products or a re-run pipeline were used
- Imaging parameters (weighting, robust, cell, image size, beam)
- Continuum subtraction and line-free channels
- MCWeeds priors, source size and fit setup
- Line-width and velocity assumptions beyond the stated 1 km/s and VLSR
- Which ALMA execution blocks and spectral windows were used

## Analysis recipe

1. **Extract spectrum from archival ALMA data**: Standard CASA reduction; spectrum extracted within one 1″×1″ synthesized beam size at the 12ED peak position in component B  
  > "The reduction of the data proceeded according to standard recipes exploiting the Common Astronomical Software Applications package (v4.2.1; McMullin et al. 2015)." (6 Search on ALMA data archives)
   - software: CASA
   - fitting: _not stated_
   - validation: Methylformate and methylacetylene lines clearly recognizable in the same spectrum  
  > "are clearly recognizable, while a lack of detection is observed for 12BD." (6 Search on ALMA data archives)
2. **Derive column density upper limit**: Model the spectrum with MCWeeds  
  > "We modeled the spectrum extracted from the ALMA data using MCWeeds (Giannetti et al. 2017) to obtain an upper limit for the 12BD column density." (6 Search on ALMA data archives)
   - software: MCWeeds
   - assumption: T = 300 K, line width 1 km/s  
  > "Assuming a temperature of 300 K and a line width of 1 km s −1" (6 Search on ALMA data archives)
   - fitting: 95% credible interval upper limit  
  > "we estimate N < 1 × 10 13 cm −2 (95% credible interval)." (6 Search on ALMA data archives)
   - validation: _not stated_

## Software

- **CASA** 4.2.1: Reduction of ALMA data  
  > "Common Astronomical Software Applications package (v4.2.1; McMullin et al. 2015)" (6 Search on ALMA data archives)
- **MCWeeds** : Modeling ALMA spectrum for column density upper limit  
  > "We modeled the spectrum extracted from the ALMA data using MCWeeds (Giannetti et al. 2017)" (6 Search on ALMA data archives)
- **CALPGM** : Fitting lab data and predicting rotational spectra  
  > "The CALPGM suite of programs (Pickett 1991) was used to fit the data and predict the rotational spectra" (4 Rotational spectrum of 1,2-butanediol)
- **Gaussian 09** Revision D.01: Conformer geometry optimization and frequencies  
  > "using the Gaussian 09 quantum chemistry package (Frisch et al. 2013)" (2 Conformational analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 1,2-butanediol column density upper limit toward IRAS 16293-2422 B | <1e13 | 95% credible interval | cm^-2 | 2 | we estimate N < 1 × 10 13 cm −2 (95% credible interval). |
| Off-source rms | 1.89 | not stated | mJy/beam | 1 | rms level (1.89 mJy beam −1 ) |
| Relative energy of g'G'Ag vs aG'Ag from population ratio | 3.9 | not stated | kJ/mol | 0 | the corresponding relative energy is 3.9 kJ mol −1 . |

## Qualitative findings

- Six conformers assigned; aG'Ag is the global minimum; no detection of 12BD in ALMA Band 3 data; best searches expected at 400–800 GHz (bands 8–9).  
  > "Search for the corresponding 30 x,30 −29 x,29 transition lines toward IRAS 16293-2422 B was unsuccessful." (abstract)

## Claim tuples

- H: 12BD can be detected toward IRAS 16293-2422 B in archival Band 3 data | E: Searched the predicted aG'Ag 30-29 quartet in the extracted ALMA spectrum | R: No detection; N < 1e13 cm^-2 | F: Non-detection is attributed to the emission peaking at higher frequencies; bands 8–9 are better | **supported**

## Reasoning

- Why this data: Project 2012.1.00712.S has frequency coverage and spectral resolution similar to the laboratory measurements  
  > "project 2012.1.00712.S was selected because the frequency coverage" (6 Search on ALMA data archives)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): The ALMA project was not aimed at searching this molecule; higher-frequency predictions need more lab data.  
  > "The ALMA project, from which the data were extracted, was in fact, not specifically aimed at searching this molecule." (7 Conclusions)
- Caveat (inferred, ours): Upper limit depends on assumed T, line width and source size, with no sensitivity to these shown
- Caveat (inferred, ours): Extraction over a single beam with no continuum/line-free treatment described
- Caveat (inferred, ours): Internal-rotation splitting not resolved in the lab, affecting prediction accuracy

## Reproducibility

- Data public (paper): Public ALMA archive data; lab line lists at CDS  
  > "Several observations on this source were found in the public data of the ALMA Science Archive." (6 Search on ALMA data archives)
- Products in archive: _not stated_
- Missing: Calibration/imaging parameters
- Missing: MCWeeds configuration and priors
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, ALMA part is brief with missing imaging and fit details, but the data are public and the upper limit is numeric.
- Rediscovery candidate: no, The ALMA recipe lacks imaging and fitting details; the main results are lab constants.

## Links

- Method: Giannetti et al. 2017 (MCWeeds modeling code)
- Method: Pickett 1991 (CALPGM spectral fitting)
- Companion: Jørgensen et al. 2016 (Ethylene glycol detection in IRAS 16293-2422 B with ALMA)
- Related: PRIMOS

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
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 59,
  "stated": 22,
  "rate": 0.373
 },
 "evidence_ok": true
}
```
