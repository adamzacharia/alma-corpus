# The Bulge Asymmetries and Dynamical Evolution (BAaDE) SiO Maser Survey at 86 GHz with ALMA

`2019ApJS..244...25S` | The Astrophysical Journal Supplement Series 2019 | first author: Stroh, Michael C. | arXiv: 1909.02090 | DOI: 10.3847/1538-4365/ab3c35

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: milky_way_ism, evolved_stars
- Question: Detect 86 GHz SiO masers toward MSX-selected AGB candidates to obtain line-of-sight velocities, and characterize the CS-emitting and SiO-emitting populations and the SiO line properties  
  > "aims to obtain tens of thousands of line-of-sight velocities from SiO masers in Asymptotic Giant Branch (AGB) stars in the Milky Way." (abstract)
- Target **BAaDE sources (1432 MSX-selected AGB candidates, southern sample)**: coordinates per-source RA/Dec in Table 2 (2MASS or MSX positions)  
  > "The VLA cannot observe 9,074 BAaDE sources (32% of the full sample) since they are located at declinations below $-35\degree$." (1 Introduction); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.01180.S, 2015.1.01289.S, 2017.1.01077.S
- bands: Band 3 (86 GHz SiO plus 98 GHz CS)  
  > "The ALMA spectral setup in Band 3 is described in Table [1](#tab_alma_spw_config)" (2.1 Observations)
- frequencies and spectral setup: 4 spectral windows at 85.65, 86.25, 86.85 and 97.99 GHz; channel width 244.141 kHz  
  > "Each channel has a width of $244.141$ kHz." (2.1 Observations); "| 3        | 97 988.0684 |   0.747 |     3840 | CS                          |" (Table 1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: synthesized beam ≈3'' (imaged 86.25 GHz window ≈3''×2'')  
  > "The synthesized beam of the spectral window imaged at 86.25 GHz consisting of 3840 channels was approximately $3\ensuremath{''}\times2\ensuremath{''}$." (3.2 Continuum field sources)
- max recoverable scale: _not stated_
- sensitivity: planned 15 mJy/beam/channel; achieved average 14 mJy/beam/channel  
  > "For the three cycles, an average rms sensitivity of 14 mJy/beam/channel was obtained." (2.1 Observations)
- time on source: _not stated_
- observing dates: Cycles 2, 3, 5: Jan 2015–Apr 2015, Dec 2015–Jan 2016, Jan 2018  
  > "Cycle 3 observations occurred between December 27th, 2015 and January 21st, 2016, and Cycle 5 observations were performed on January 28th, 2018." (2.1 Observations)
- pi or archival as stated: _not stated_
- Line: SiO J=2-1 v=1 (86 243.370 MHz)
- Line: CS J=2-1 (97 980.950 MHz)
- Line: SiO J=2-1 v=0 (86 846.995 MHz)
- Line: SiO J=2-1 v=2 (85 640.452 MHz)
- Other facility **MSX**: Infrared colors used for source selection  
  > "All sources were selected from version 2.3 of the MSX point source catalog" (1 Introduction)
- Other facility **2MASS**: Source positions for phase-center shifting  
  > "if a 2MASS association existed for a BAaDE source, the phase center was shifted to the 2MASS position using the task *fixvis*." (2.2 Calibration)
- External data: Literature SiO and OH maser velocities for comparison  
  > "A $4\ensuremath{''}$ search radius was used to search for possible SiO and OH maser associations in the extensive Database of Astronomical Maser Sources" (4.2 The SiO maser line velocities) [from (cite: 10.1017/S1743921317008948)]
- External data: Variability periods for 61 sources  
  > "The International Variable Star Index (cite: 2006SASS...25...47W) contains periods for 61 sources with SiO $v$=1 maser emission in our observed ALMA sample." (4.2 The SiO maser line velocities) [from (cite: 2006SASS...25...47W)]

## Processing

### Calibration

- pipeline or manual: BAaDE CASA pipeline adapted from the BAaDE VLA pipeline  
  > "The BAaDE ALMA calibration pipeline is based on the VLA calibration pipeline developed for the BAaDE survey" (2.2 Calibration)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: QSO B1424–41, QSO B1921–293, PKS 1613–586; spectral slope from 91.46 and 103.49 GHz catalog fluxes  
  > "these quasars were used for flux and bandpass calibration." (2.2 Calibration)
- flux scale uncertainty: <5% difference from Butler-JPL-Horizons 2012 solar system calibration  
  > "differed by less than 5% from flux calibration using resolved solar system objects and the ’Butler-JPL-Horizons 2012’ standard" (2.2 Calibration)
- self calibration: Phase-only self-cal on brightest line channel; applied to all four spws; fails for CS  
  > "the brightest channel with a line detection was subsequently used for phase-only self-calibration." (2.3 Line Detections)

### Imaging

- task: tclean (for continuum/CS field images only)  
  > "CASA’s task *tclean* was used with the Högbom clean deconvolver, Briggs weighting, and Briggs robustness parameter 0.5" (3.2 Continuum field sources)
- deconvolver: Högbom  
  > "CASA’s task *tclean* was used with the Högbom clean deconvolver, Briggs weighting, and Briggs robustness parameter 0.5" (3.2 Continuum field sources)
- weighting robust: Briggs, robust = 0.5  
  > "Briggs robustness parameter 0.5 (equivalent to robust=0.0 in AIPS)" (3.2 Continuum field sources)
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

- Calibration pipeline derived from the BAaDE VLA pipeline  
  > "The BAaDE ALMA calibration pipeline is based on the VLA calibration pipeline developed for the BAaDE survey, see L. O. Sjouwerman et al. (2019, in preparation)." (2.2 Calibration) [from L. O. Sjouwerman et al. (2019, in preparation)]
- Source selection from MSX region iiia  
  > "All sources were selected from version 2.3 of the MSX point source catalog (cite: 2003yCat.5114....0E) that coincide with MSX color region *iii*a (cite: 10.1088/0004-637X/705/2/1554)." (1 Introduction) [from (cite: 10.1088/0004-637X/705/2/1554)]

### Not stated but needed to reproduce (our reading)

- Exact pipeline script/code (not released in text)
- Line-free channel and spectral-window noise algorithm details beyond 8-sigma clipping
- Number of antennas, array configurations, baselines and exposure per source
- Cell size, image size, masks and clean thresholds for field images
- Bandpass and phase calibrator per execution block
- Details of the gamma and Gaussian fits for FWZM and colors

## Analysis recipe

1. **Shift phase centers and calibrate**: fixvis to 2MASS positions, then flux/bandpass/phase calibration with CASA pipeline  
  > "The phase center was adjusted before any standard calibration was performed." (2.2 Calibration)
   - software: CASA
   - fitting: _not stated_
   - validation: Flux scale compared with Butler-JPL-Horizons 2012, <5% difference  
  > "differed by less than 5% from flux calibration using resolved solar system objects" (2.2 Calibration)
2. **Detect lines and self-calibrate**: SNR thresholds on spectra at phase center; phase-only self-cal on brightest channel; final spectra  
  > "Single line detections were required to have an SNR above 5$\sigma$. Multiple line detections could be made down to a 4.5$\sigma$ level, if the velocities from each line agreed within 30 km s$^{-1}$." (2.3 Line Detections)
   - software: CASA
   - parameter: Spectral regions above 8x initial rms removed before robust rms  
  > "spectral regions exceeding 8 times the initial rms noise were removed first." (2.3 Line Detections)
   - fitting: _not stated_
   - validation: _not stated_
3. **Image continuum and CS fields**: tclean imaging of fields with continuum or CS emission; match to SIMBAD  
  > "In order to better understand the nature of these sources, and to determine whether the continuum emission may be associated with the BAaDE sources, the fields were imaged." (3.2 Continuum field sources)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit color distributions and velocity statistics**: Gaussian fits to [D]-[E] distributions; Wilcoxon signed-rank test of SiO velocity differences; gamma fit to FWZM; Spearman test; Anderson–Darling test  
  > "Fitting the SiO maser and CS emission populations to individual Gaussian probability distributions with the *fitdistr* function" (4.1.1 Color distribution)
   - software: fitdistr, MASS
   - fitting: maximum-likelihood Gaussian via fitdistr  
  > "Fitting the SiO maser and CS emission populations to individual Gaussian probability distributions with the *fitdistr* function" (Color distribution)
   - validation: _not stated_

## Software

- **CASA** : calibration pipeline, fixvis, tclean  
  > "we use the *Common Astronomy Software Applications* (cite: 2007ASPC..376..127M) package." (2.2 Calibration)
- **fitdistr (R MASS)** : Gaussian distribution fits  
  > "CASA (cite: 2007ASPC..376..127M), *fitdistr* (cite: ISBN0-387-95457-0), MASS (cite: ISBN0-387-95457-0), *mclust* (cite: ISSN2073-4859_doi10.21236/ada459792)" (Software)
- **mclust** : listed in software; specific use not stated  
  > "*mclust* (cite: ISSN2073-4859_doi10.21236/ada459792)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SiO v=1 detection rate | 71.2% (1020 sources) | not stated | percent | 2 | / $\phantom{^{28}}$SiO ($J$=2–1) $v$=1 / 86 243.370 / 1020 / 71.2% / |
| CS detection rate | 3.5% (50 sources) | not stated | percent | 2 | / $\phantom{^{29}}$CS ($J$=2–1) / 97 980.950 / 50 / 3.5% / |
| Mean [D]-[E] of SiO emitters | 0.691 | ±0.013 | mag | 4 | the mean and standard deviations of the SiO emission distribution in $[\textnormal{D}]-[\textnormal{E}]$ are $0.691 \pm 0.013$ and $0.264 \pm 0.009$ magnitudes |
| Mean [D]-[E] of CS emitters | 1.84 | ±0.10 | mag | 4 | $1.84 \pm 0.10$ and $0.70 \pm 0.07$ magnitudes |
| SiO detection rate for [D]-[E] ≤ 1.38 | 80% | not stated | percent | 2 | the detection rate jumps to 80% if limiting source selection to $[\textnormal{D}]-[\textnormal{E}] \le 1.38$ |
| Velocity range containing 90% of SiO v=1 emission | 13 | not stated | km/s | 4 | for 90% of the sources with SiO $v$=1 emission, the emission is limited to a velocity range of 13 km s$^{-1}$ |
| SiO v=0 / v=1 line ratio | 5.4e-2 | ±0.5e-2 | dimensionless | 4 | / $\phantom{^{28}}$SiO $v$=0 / $(5.4 \pm 0.5) \times10^{-2}$ |
| SiO v=2 / v=1 line ratio | 2.3e-1 | ±0.3e-1 | dimensionless | 4 | / $\phantom{^{28}}$SiO $v$=2 / $(2.3 \pm 0.3) \times10^{-1}$ |

## Qualitative findings

- Most CS emitters have extended emission and are likely YSOs rather than AGB stars  
  > "The majority of fields show extended CS emission, thus arguing against unresolved carbon-rich stars or compact HII regions dominating the population of CS emitters." (4.1.2 CS line images)

## Claim tuples

- H: SiO detection rate is high among color-selected oxygen-rich sources | E: Pipeline line detection in 1432 ALMA fields | R: 71% overall, 80% for [D]-[E] ≤ 1.38 | F: MSX selection efficiently yields SiO masers | **supported**
- H: Sources with [D]-[E] > 1.38 are not late-type AGB stars | E: Colors, CS imaging, Galactic distribution, l-v | R: Extended CS, low |b|, spiral-arm velocities | F: Likely YSOs or possibly PNe | **supported**
- H: Any SiO transition gives the same stellar velocity | E: Wilcoxon test of velocity differences relative to v=1 | R: No systematic shift within channel width | F: Any SiO transition suitable | **supported**

## Reasoning

- Why this data: ALMA reaches the low-declination sources the VLA cannot observe  
  > "Since ALMA cannot observe the 43 GHz frequencies associated with $J$=1–0 SiO maser transitions, the ALMA sample is instead surveyed in the $J$=2–1 rotational transitions at 86 GHz." (1 Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Spectra assume source at phase center; positional errors can cause non-detections; SiO variability makes brightness only indicative  
  > "Especially for weaker sources, a 2$\ensuremath{''}$ positional error could result in a non-detection in the pipeline." (2.2 Calibration)
- Caveat (inferred, ours): Far-IR confusion and variability limit the interpretation of detection rates
- Caveat (inferred, ours): YSO/PN classification is indirect (colors, morphology)
- Caveat (inferred, ours): Single-epoch SiO observations; no distances for CS emitters

## Reproducibility

- Data public (paper): Spectra on BAaDE website; project codes given; machine-readable tables  
  > "A complete list of spectra are available at the BAaDE survey’s website www.phys.unm.edu/$\sim$baade." (3 Results)
- Products in archive: _not stated_
- Missing: Pipeline code
- Missing: Antenna/configuration details
- Missing: Exact detection-algorithm parameters
- Data volume (inferred): Several hundred GB to ~1 TB raw for ~1400 short pointings across three projects
- Score (inferred): 4/5, Data are public with project codes and stated thresholds, but pipeline code is unreleased and several settings are unspecified.
- Rediscovery candidate: no, Pipeline details are unreleased and the recipe is not complete enough to redo.

## Links

- Method: L. O. Sjouwerman et al. (2019, in preparation) (BAaDE VLA calibration pipeline on which the ALMA pipeline is based)
- Companion: (cite: 10.3847/1538-4357/aaccf3) (Stroh et al. 2018, 86 GHz re-detection of known BAaDE SiO sources)
- Companion: (cite: 10.3847/1538-4357/aae77d) (Pihlström et al. 2018, 43 GHz BAaDE VLA positions and detections)
- Related: BAaDE VLA survey

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 34,
  "rate": 0.507
 },
 "evidence_ok": true
}
```
