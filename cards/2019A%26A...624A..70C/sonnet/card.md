# Astrophysical detections and databases for the mono deuterated species of acetaldehyde CH<SUB>2</SUB>DCOH and CH<SUB>3</SUB>COD

`2019A&A...624A..70C` | Astronomy and Astrophysics 2019 | first author: Coudert, L. H. | arXiv: - | DOI: 10.1051/0004-6361/201834827

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: astrochemistry, star_formation
- Question: Build spectroscopic databases for CH2DCOH and CH3COD from lab spectra and search for both species in IRAS 16293-2422 B using ALMA PILS data  
  > "Spectroscopic databases for astrophysical purposes are built for the two mono deuterated isomeric species CH 2 DCOH and CH 3 COD of the complex organic molecule acetaldehyde." (abstract)
- Target **IRAS 16293-2422 source B**: coordinates α J2000 = 16h32m22.5375s; δ J2000 = −24°28′32.555″ (position ~1″ east of source B)  
  > "in a 0.5 ′′ beam located ∼1 ′′ east of source B (α J2000 = 16 h 32 m 22.5375 s; δ J2000 = −24 ◦ 28 ′ 32.555 ′′ )" (3. Astrophysical observations); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00278.S
- bands: Band 7, about 329–363 GHz  
  > "covering a frequency range of about [329–363] GHz of ALMA’s Band 7" (3. Astrophysical observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12 m array only, ~38 antennas  
  > "we only used the data obtained with the 12 m dishes array (∼38 antennas in the array at the time of observations)" (3. Astrophysical observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.5″ beam; spectral resolution ~0.25 km/s  
  > "ultimate spectral resolution of δ v ∼ 0.25 km s [−][1], in a 0.5 [′′] beam" (3. Astrophysical observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **IRAM-30m ASAI Large Program**: Single-dish 80–272 GHz survey searched; species not detected  
  > "We conclude that these species are not detected in all ASAI sources with the single-dish observations" (3. Astrophysical observations)
- Other facility **Lille submillimeter spectrometer**: Laboratory spectra of CH2DCOH, 150–990 GHz  
  > "The transitions measured in this work were recorded in the 150–990 GHz frequency range using the Lille spectrometer" (2.1 Experimental)
- External data: PILS survey data and observational details  
  > "Full observational details are given in Jørgensen et al. 2016." (3. Astrophysical observations) [from Jørgensen et al. 2016]
- External data: CH3COD spectroscopic analysis used for its database  
  > "For CH 3 COD, the results of the analysis carried out by Elkeurti et al. (2010) were used" (2.4 Spectroscopic database for CH2DCOH and CH3COD) [from Elkeurti et al. (2010)]

## Processing

### Calibration

- pipeline or manual: Reprocessed with standard pipeline scripts  
  > "that we reprocessed using the standard pipeline scripts to obtain data-cubes" (3. Astrophysical observations)
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

- Full observational details of PILS  
  > "Full observational details are given in Jørgensen et al. 2016." (3. Astrophysical observations) [from Jørgensen et al. 2016]

### Not stated but needed to reproduce (our reading)

- CASA/pipeline version and calibration scripts
- Imaging parameters (weighting, cell, continuum subtraction)
- How the spectrum was extracted at the chosen position
- Fitted column densities/temperature (model was not optimized)
- Distance to the source

## Analysis recipe

1. **Fit laboratory transitions and build line lists**: Least-squares fit of 2556 transitions with an internal-axis-method torsion-rotation model, then JPL-format catalogs  
  > "experimental frequencies were introduced in a least-squares fit procedure where they were given a weight equal to the inverse of their experimental uncertainty squared" (2.3 Line assignment and line frequency analysis)
   - fitting: _not stated_
   - validation: unitless standard deviation 2.3  
  > "The unitless standard deviation of this final analysis is 2.3" (2.3 Line assignment and line frequency analysis)
2. **Search for lines in PILS cubes with LTE models**: CASSIS LTE synthetic spectra compared with the ALMA spectrum in a 10 GHz band  
  > "We first computed local thermodynamic equilibrium (LTE) synthetic spectra, using the CASSIS software, of the expected brightest lines" (3. Astrophysical observations)
   - software: CASSIS
   - parameter: Aij ≥ 0.001 s-1, Eup ≤ 500 K; source size 3″, Tex 100 K, linewidth 0.8 km/s, N = 5e14 (CH2DCOH), 3.5e14 cm-2 (CH3COD)  
  > "an excitation temperature of 100 K, a line width of 0.8 km s [−][1], and a column density of 5 × 10 [14] cm [−][2] for CH 2 DCOH" (3. Astrophysical observations)
   - fitting: _not stated_
   - validation: Visual comparison; undetected lines explained by Eup or sensitivity  
  > "The nondetection of some lines is therefore only due to the sensitivity limit of the PILS survey." (3. Astrophysical observations)

## Software

- **CASSIS** : Line identification and LTE synthetic spectra  
  > "We used the CASSIS [2] software for the line identification in the publicly available ASAI data" (3. Astrophysical observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of CH2DCOH lines detected | 93 | not stated | lines | 2 | Figures A.1 and A.2 show the detection of 93 CH 2 DCOH lines and 43 CH 3 COD lines |
| Number of CH3COD lines detected | 43 | not stated | lines | 2 | Figures A.1 and A.2 show the detection of 93 CH 2 DCOH lines and 43 CH 3 COD lines |
| Unitless standard deviation of lab fit | 2.3 | not stated | dimensionless | 1 | The unitless standard deviation of this final analysis is 2.3 |
| RMS of fit, all transitions | 0.151 | not stated | MHz | 1 | and 0.151 MHz for all transitions |

## Qualitative findings

- First detection of CH2DCOH; CH3COD detected toward IRAS 16293-2422 B  
  > "We report the first detection of CH 2 DCOH (93 transitions)" (abstract)

## Claim tuples

- H: CH2DCOH and CH3COD are present in IRAS 16293 B | E: Search PILS ALMA cubes with new databases and CASSIS LTE models | R: 93 CH2DCOH and 43 CH3COD lines detected in a 10 GHz band | F: First detection of CH2DCOH and detection of CH3COD | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Neither data processing nor LTE modeling was optimized to reproduce line intensities  
  > "we did not optimize neither the data processing, nor the CASSIS LTE modeling to reproduce the line intensities" (3. Astrophysical observations)
- Caveat (inferred, ours): No column densities or abundance ratio derived despite the stated motivation
- Caveat (inferred, ours): Detection claim rests on visual matching, with no significance test
- Caveat (inferred, ours): Many lines blended or unidentified

## Reproducibility

- Data public (paper): PILS data publicly available  
  > "The entire raw dataset of this survey is accessible on the ALMA website." (3. Astrophysical observations)
- Products in archive: _not stated_
- Missing: Pipeline version, imaging settings and spectrum extraction details
- Data volume (inferred): Large; PILS 12 m raw data likely hundreds of GB, only a 10 GHz band used
- Score (inferred): 3/5, The lab fit is detailed, but the ALMA reduction is sparse and the detection is qualitative.
- Rediscovery candidate: no, Processing details are missing and results are mainly line counts.

## Links

- Method: Margulès et al. 2009 (Torsion-rotation model for mono-deuterated methyl formate, applied here)
- Companion: Jørgensen et al. 2016 (PILS survey description)
- Related: ALMA PILS
- Related: ASAI

## Checks

```json
{
 "quotes": 28,
 "quotes_ok": 28,
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
  "facts": 58,
  "stated": 20,
  "rate": 0.345
 },
 "evidence_ok": true
}
```
