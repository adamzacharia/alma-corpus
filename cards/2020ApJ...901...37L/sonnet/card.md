# The Family of Amide Molecules toward NGC 6334I

`2020ApJ...901...37L` | The Astrophysical Journal 2020 | first author: Ligterink, Niels F. W. | arXiv: 2008.09157 | DOI: 10.3847/1538-4357/abad38

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: astrochemistry, star_formation
- Question: Which amide(-like) molecules are present toward NGC 6334I, what are their abundances, and what do abundance ratios reveal about their formation?  
  > "In this work, ALMA observations are used to study a number of amide(-like) molecules toward the high-mass star-forming region NGC 6334I." (abstract)
- Target **NGC 6334I (MM1 and MM2)**: coordinates Spectra extracted at 14 positions, e.g. MM1-i 17:20:53.373 -35:46:58.341  
  > "MM1-i | 17:20:53.373 | -35.46.58.341 | -7.0 | 3.25 | 135" (Table 1); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00661.S, 2015.A.00022.T, 2017.1.00717.S
- bands: Bands 4, 7 and 10  
  > "In this work, ALMA observations of NGC 6334I in bands 4, 7, and 10 are analyzed." (2.1 Observational Data of NGC 6334I)
- frequencies and spectral setup: B4 130.03-132.02, 144.00-145.87 GHz; B7 279.17-282.94, 291.18-294.94, 336.18-339.94, 348.18-351.94 GHz; B10 873.88-881.33, 890.25-897.70 GHz; resolution 1.1 km/s (B10 0.5)  
  > "Spectral Resolution (km s$^{-1}$) | 1.1 | 1.1 | 1.1 | 0.5" (Table 2)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-6 (B4); C36-4, C36-5 (B7); C43-3 (B10)  
  > "Configuration(s) | C43-6 | C36-4, C36-5 | C36-4, C36-5 | C43-3" (Table 2)
- baselines: _not stated_
- angular resolution: 0.21-0.25 x 0.15-0.19 arcsec native; all convolved to 0.26 x 0.26 arcsec  
  > "all of the observations were convolved to a common synthesized beam size of $0.26^{\prime\prime} \times 0.26^{\prime\prime}$" (2.1 Observational Data of NGC 6334I)
- max recoverable scale: _not stated_
- sensitivity: rms 0.8 (B4), 2.0 (B7 low), 3.3 (B7 high), 44 (B10) mJy/beam km/s  
  > "rms (mJy beam$^{-1}$ km s$^{-1}$) | 0.8 | 2.0 | 3.3 | 44" (Table 2)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: NH2CN, HNCO (and 13C), NH2CHO (and 13C), CH3C(O)NH2, CH3NHCHO, NH2C(O)NH2 many rotational lines (see Table 5)
- External data: 12C/13C ratio of 62 for NGC 6334I  
  > "multiplied with the $^{12/13}$C ratio of 62 for NGC 6334I, as determined by (cite: bogelund2018)" (Results) [from (cite: bogelund2018)]
- External data: Comparison abundance ratios for other sources (G+0.693, Sgr B2, IRAS 16293B, Orion KL, etc.)  
  > "Comparisons are made with the following works: IRAM 30m and Green Bank Telescope (GBT) single dish observations of G+0.693-0.027" (4.1 Chemical comparisons) [from (cite: zeng2018; jimenez-serra2020; coutens2018; belloche2019; cernicharo2016)]
- External data: Spectroscopic line lists (JPL, CDMS, literature)  
  > "Line lists from the JPL catalog for molecular spectroscopy (cite: pickett1998), the Cologne Database for Molecular Spectroscopy (cite: muller2001; muller2005), and literature are used." (2.2 Molecule identification & analysis) [from (cite: pickett1998; muller2001; muller2005)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Data self-calibrated following earlier procedures  
  > "The data were self-calibrated and continuum-subtracted following the procedures detailed in (cite: hunter2017; brogan2018)." (2.1 Observational Data of NGC 6334I)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum-subtracted following Hunter 2017 / Brogan 2018  
  > "The data were self-calibrated and continuum-subtracted following the procedures detailed in (cite: hunter2017; brogan2018)." (2.1 Observational Data of NGC 6334I)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Convolved to common 0.26 x 0.26 arcsec beam  
  > "all of the observations were convolved to a common synthesized beam size of $0.26^{\prime\prime} \times 0.26^{\prime\prime}$" (2.1 Observational Data of NGC 6334I)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Dataset reductions  
  > "The details of the individual datasets and their reductions have been published in detail elsewhere (cite: mcguire2017; mcguire2018; brogan2018)" (2.1 Observational Data of NGC 6334I) [from (cite: mcguire2017; mcguire2018; brogan2018)]
- Self-calibration and continuum subtraction  
  > "The data were self-calibrated and continuum-subtracted following the procedures detailed in (cite: hunter2017; brogan2018)." (2.1 Observational Data of NGC 6334I) [from (cite: hunter2017; brogan2018)]
- Spectrum extraction positions  
  > "spectra were extracted for analysis at the same positions as used in (cite: el-abd2019)" (2.1 Observational Data of NGC 6334I) [from (cite: el-abd2019)]
- Excitation temperature determination  
  > "following the formalism of (cite: turner1991) (cite: el-abd2019)" (2.2 Molecule identification & analysis) [from (cite: turner1991; el-abd2019)]
- CASSIS line analysis procedure  
  > "Further details on the CASSIS line analysis procedure can be found in (cite: ligterink2018b) and (cite: bogelund2019a)." (2.2 Molecule identification & analysis) [from (cite: ligterink2018b; bogelund2019a)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration details (deferred to earlier papers)
- Line-free channels and continuum subtraction specifics
- How T_BG was measured from the continuum (extraction details)
- Spectral extraction aperture size
- Source distance
- Exact lines selected for fitting per position and fit windows
- Grid step size of chi2 minimization
- Exact T_ex values derivation per position (given only in Table 1)

## Analysis recipe

1. **Prepare cubes and extract spectra**: Convolve all data to common 0.26 arcsec beam; extract spectra at 14 positions; determine background temperature from continuum level  
  > "From the data cubes, background temperatures ($T_{\rm BG}$) were determined based on the continuum level temperature and spectra were extracted for analysis" (2.1 Observational Data of NGC 6334I)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify lines and by-eye fit V_LSR and linewidth**: Identify rotational lines and make by-eye synthetic fit to get V_LSR and dV  
  > "In the first step of the data analysis, rotational lines of a molecule are identified and a by-eye synthetic fit of these lines is made." (2.2 Molecule identification & analysis)
   - software: CASSIS
   - parameter: V_LSR and dV errors +-0.3 km/s  
  > "The errors on both the $V_{\rm LSR}$ and $\Delta$V are conservatively estimated to be $\pm$0.3 km s$^{-1}$." (2.2 Molecule identification & analysis)
   - fitting: _not stated_
   - validation: Compared with values in El-Abd 2019  
  > "which in most cases yield similar values as given in (cite: el-abd2019)" (2.2 Molecule identification & analysis)
3. **Fit column densities**: Select optically thin, unblended lines; grid chi2 minimization of column density within +-1 order of magnitude of by-eye value  
  > "CASSIS then performs a regular grid $\chi^2$ minimization routine on the selected lines, where the column density is given as a free parameter within $\pm$1 order of magnitude of the by-eye determined value." (2.2 Molecule identification & analysis)
   - software: CASSIS
   - parameter: Error = 1 sigma fit error plus 10% flux uncertainty; 30% for CH3NHCHO  
  > "In most cases, the error on the column density is given by the 1$\sigma$ fit error plus a 10% flux uncertainty." (2.2 Molecule identification & analysis)
   - assumption: LTE, single T_ex per position, beam filling factor of one, T_BG included  
  > "the emission is assumed to be beam filling and thus has a beam filling factor of one." (2.2 Molecule identification & analysis)
   - assumption: 12C/13C = 62 to derive HNCO and NH2CHO main isotopologue columns  
  > "multiplied with the $^{12/13}$C ratio of 62 for NGC 6334I" (Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare abundance ratios with other sources**: Compute ratios relative to NH2CHO and compare with literature sources  
  > "In the following sections molecular ratios with respect to NH$_{2}$CHO are discussed." (4.1 Chemical comparisons)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASSIS** : Line analysis, synthetic spectra, chi2 column density fitting  
  > "All spectra are analyzed with the CASSIS[^2] line analysis software." (2.2 Molecule identification & analysis)
- **Astropy** : Acknowledged as used  
  > "Astropy, a community-developed core Python package for Astronomy" (Acknowledgments)
- **APLpy** : Plotting  
  > "APLpy, an open-source plotting package for Python" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| N(NH2CN) at MM1-i | 5.9e15 | 0.9e15 | cm^-2 | 3 | MM1-i / 135 / (5.9$\pm$0.9)$\times$10$^{15}$ |
| N(CH3C(O)NH2) at MM1-v | 2.3e17 | 0.2e17 | cm^-2 | 3 | (2.3$\pm$0.2)$\times$10$^{17}$ |
| N(CH3NHCHO) at MM1-nmf | 1.0e17 | 0.5e17 | cm^-2 | 3 | MM1-nmf / 150 / (1.1$\pm$0.2)$\times$10$^{16}$ / (1.9$\pm$0.3)$\times$10$^{16}$ / (1.6$\pm$0.3)$\times$10$^{16}$ / (6.8$\pm$1.3)$\times$10$^{16}$ / (1.0$\pm$0.5)$\times$10$^{17}$ |
| N(NH2C(O)NH2) tentative at MM1-v | 5.0e16 | 2.0e16 | cm^-2 | 3 | (5.0$\pm$2.0)$\times$10$^{16}$ |
| [NH2CN]/[NH2CHO] within NGC 6334I | ~1-2% | not stated | percent | 4 | in general is uniform at $\sim$1-2% |
| [CH3C(O)NH2]/[NH2CHO] average | ~0.15 | not stated | dimensionless | 4 | close to the observed average of $\sim$0.15 in NGC 6334I |

## Qualitative findings

- First detections of NH2CN, CH3C(O)NH2 and CH3NHCHO toward NGC 6334I; urea tentative  
  > "The first detections of cyanamide (NH$_{2}$CN), acetamide (CH$_{3}$C(O)NH$_{2}$) and N-methylformamide (CH$_{3}$NHCHO) are presented for this source." (abstract)
- NH2CN/NH2CHO varies by ~3 orders of magnitude across sources, high in low-mass/quiescent, low in high-mass  
  > "with high ratios toward low-mass and pre-stellar sources and low ratios toward high-mass sources" (Conclusion)

## Claim tuples

- H: Amides in NGC 6334I form via related ice chemistry | E: Column densities and ratios to NH2CHO at 14 positions | R: Ratios generally similar, often varying less than a factor of five | F: Amides plausibly formed on grain surfaces in the dense cloud stage | **supported**
- H: NH2CN abundance depends on source type | E: Compare [NH2CN]/[NH2CHO] with literature sources | R: Variation across three orders of magnitude | F: Physical conditions influence NH2CN production, possibly separate chemistry | **partially**
- H: HNCO and NH2CHO correlated in NGC 6334I | E: Compare [HNCO]/[NH2CHO] | R: Slightly above one in MM1, ~5 in MM2 | F: Follows the average interstellar trend | **supported**

## Reasoning

- Why this data: NGC 6334I as ideal laboratory: massive cluster analog and well-studied chemistry  
  > "An ideal interstellar laboratory to study amides is found in the high-mass star-forming region (HMSFR) NGC 6334I." (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Urea only tentative; CH3NHCHO lines heavily blended  
  > "While these lines are not enough for a secure detection, a tentative identification can be claimed." (Results)
- Limitation (authors): Source size uncertainties affect ratio comparisons, especially single dish  
  > "single dish telescopes do not have the spatial resolution to determine the source size and these are often assumed or estimated" (4.1 Chemical comparisons)
- Caveat (inferred, ours): Single T_ex per position for all molecules may be inappropriate
- Caveat (inferred, ours): Beam-filling factor of one assumed without test
- Caveat (inferred, ours): Comparison with literature sources uses heterogeneous methods
- Caveat (inferred, ours): No distance or optical depth treatment of continuum details given

## Reproducibility

- Data public (paper): Project codes given in acknowledgments; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00717.S, #2017.1.00661.S, and #2015.A.00022.T." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Calibrated/self-calibrated cubes from earlier papers
- Missing: T_BG extraction details
- Missing: Line selection per position
- Data volume (inferred): ~hundreds of GB raw for three projects; processed cubes tens of GB
- Score (inferred): 3/5, Fitting recipe and Table 1 parameters are clear, but data reduction is inherited and line selections are not fully specified.
- Rediscovery candidate: no, Calibration and self-calibration are inherited from earlier papers, so the data cannot be redone from the text alone.

## Links

- Method: (cite: ligterink2018b) (CASSIS line analysis procedure)
- Method: (cite: hunter2017) (Self-calibration and continuum subtraction)
- Method: (cite: turner1991) (T_ex formalism)
- Companion: (cite: el-abd2019) (Same positions and similar analysis)
- Companion: (cite: bogelund2019a) (N-bearing molecule analysis of NGC 6334I)
- Companion: (cite: brogan2018) (Band 7/10 data reduction)

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 36,
  "rate": 0.486
 },
 "evidence_ok": true
}
```
