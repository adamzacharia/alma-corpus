# Carbon- and Oxygen-rich Asymptotic Giant Branch (AGB) Stars in the Bulge Asymmetries and Dynamical Evolution (BAaDE) Survey

`2020ApJ...892...52L` | The Astrophysical Journal 2020 | first author: Lewis, Megan O. | arXiv: 2002.11095 | DOI: 10.3847/1538-4357/ab7920

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: evolved_stars, milky_way_ism
- Question: Where do O-rich AGB stars, C-rich AGB stars and YSOs lie in IR color-color diagrams, using SiO maser detection rates in the BAaDE survey, and what are their numbers and Galactic distributions?  
  > "In this work, the detection rate of SiO masers as a function of IR color is used to determine the IR color ranges where O-rich AGB stars are found" (Introduction)
- Target **BAaDE sample (14742 analyzed sources: 13314 VLA, 1428 ALMA)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.01180.S, 2015.1.01289.S, 2017.1.01077.S
- bands: _not stated_
- frequencies and spectral setup: ALMA: v=0,1,2 J=2-1 SiO at 86 GHz plus 29SiO; VLA: v=0-3 J=1-0 near 43 GHz  
  > "being observed by ALMA covering the v=0, 1, and 2 $J=2-1$ transitions at 86 GHz (as well as a transition from $^{29}$SiO)" (2 Observations/BAaDE)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: ALMA: approximately the same noise level as VLA (15-20 mJy/beam); spectral resolution 0.8 km/s  
  > "collected in 2015, 2016, and 2018 at a spectral resolution of 0.8 km s$^{-1}$ and to approximately the same noise level as the VLA data" (2 Observations/BAaDE)
- time on source: _not stated_
- observing dates: ALMA: 2015, 2016, 2018  
  > "collected in 2015, 2016, and 2018 at a spectral resolution of 0.8 km s$^{-1}$" (2 Observations/BAaDE)
- pi or archival as stated: _not stated_
- Line: SiO v=0,1,2 J=2-1 (ALMA) (86 GHz)
- Other facility **VLA**: SiO J=1-0 spectra near 43 GHz for most of the sample  
  > "About 70% (19000) of the sources have been observed with the VLA" (2 Observations/BAaDE)
- Other facility **MSX**: Point source catalog magnitudes [A],[C],[D],[E] for selection and colors  
  > "BAaDE sources were chosen from the MSX Point Source Catalogue version 2.3" (2.1 IR data)
- Other facility **2MASS**: Ks magnitudes  
  > "The work presented here relies on MSX data as well as 2MASS \[K$_s$\] magnitudes" (2.1 IR data)
- Other facility **AKARI**: [18] magnitudes  
  > "AKARI \[18\] magnitudes (centered at 18$\mu$m)" (2.1 IR data)
- External data: BAaDE IR cross-match with 2MASS, AKARI, WISE, MIPSGAL  
  > "The cross-matching is discussed in Hilburn (cite: eddie)" (2.1 IR data) [from Hilburn (cite: eddie)]
- External data: CS emission images of BAaDE ALMA sources (morphology)  
  > "Stroh et al. (2019) mapped the CS emission." (3.1.4 CS emission distribution) [from Stroh et al. 2019 (cite: michael2)]

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

- Full BAaDE survey description, ALMA calibration strategy  
  > "For a more complete description of the BAaDE survey see (cite: baade)." (2 Observations/BAaDE) [from Sjouwerman et al. 2020, in preparation (cite: baade)]
- Zero-magnitude flux densities for MSX, 2MASS, AKARI  
  > "zero-magnitude flux densities of 55.810 Jy, 26.423 Jy, 18.267 Jy, 8.666 Jy, 665 Jy, and 12.001 Jy are applied" (2.1 IR data) [from SCC09; (cite: 2mass); (cite: akari)]

### Not stated but needed to reproduce (our reading)

- ALMA data reduction/calibration details and CASA version
- Detection finding procedure and noise estimation
- Gaussian fit procedure details for D-E
- How the Ks-A vs A-E dividing line was optimized
- Per-source list and quality flags for IR magnitudes
- Cross-match radii

## Analysis recipe

1. **Cross-match and compute IR colors**: Cross-match BAaDE sources with MSX/2MASS/AKARI; convert to magnitudes with zero-point flux densities; no reddening correction  
  > "No other corrections (i.e., reddening corrections) were applied to any of the IR magnitudes or colors used in this work." (2.1 IR data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Separate YSOs by [D]-[E]**: Fit two Gaussians to [D]-[E] and take their intersection as the division  
  > "This value was determined by fitting a pair of Gaussians to the \[D\]$-$\[E\] values of all of the BAaDE sources with \[E\]-magnitudes" (3.1.1 IR color-color diagrams)
   - parameter: [D]-[E]=1.35  
  > "Two populations can be seen in our data, separated at $[D]-[E]=1.35$." (3.1.1 IR color-color diagrams)
   - fitting: _not stated_
   - validation: Compared with Lumsden et al. diagrams, spatial clustering, CS morphology  
  > "Comparison of our sample with that of Lumsden et al (2002; first panel of their figures 3, 4, and 5)" (3.1.1 IR color-color diagrams)
3. **Separate C-rich from O-rich AGB by Ks-A vs A-E**: Empirical dividing line using SiO detection rate in the color-color diagram  
  > "Empirically we define: $$\begin{equation}
    [K_s]-[A]=4.5([A]-[E])-1.2 
\end{equation}$$ as the division between the populations." (3.2 C-rich versus O-rich AGB populations)
   - fitting: _not stated_
   - validation: Known C-stars from Alksnis fall in C region; three CS-detected sources checked  
  > "the carbon-stars from Alksnis et al. (cite: alksnis) fall mostly into our C region." (3.2.1 Candidate C-rich AGB stars)
4. **Count populations and detection rates, apply cuts to full BAaDE sample**: Apply color cuts to all sources with reliable colors; compute SiO detection rates and C/O fraction  
  > "we find that our color criteria would yield 697 C-AGBs, 10084 O-AGBs, and 1638 YSO/non-AGB sources." (4.4 Numbers of C versus O)
   - fitting: _not stated_
   - validation: Compared with other surveys' C-AGB fractions  
  > "we can compare our fractional distributions among source types to several other surveys in the Galaxy" (4.4 Numbers of C versus O)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [D]-[E] YSO division | 1.35 | not stated | mag | 2 | Two populations can be seen in our data, separated at $[D]-[E]=1.35$. |
| SiO detection rate in O-AGB region | 73% | not stated | percent | 3 | In the O-AGB region of Fig. [4](#fig:kaae), the SiO detection rate is 73%. |
| SiO detection rate in C-AGB region | ~12% | not stated | percent | 3 | a high SiO detection rate ($\sim$73%) and one with a low rate ($\sim$12%) |
| C-AGB fraction | 6% (697 C-AGB, 10084 O-AGB, 1638 YSO/non-AGB) | approximate | percent | 4 | This gives a fraction of C-AGBs of 6% |
| Color-selected C-AGBs at |l|<30 deg | 228 | not stated | sources | 4 | there are still 228 color-selected C-AGBs at $/l/<30^{\circ}$ |

## Qualitative findings

- No C/O division is found in any color-color diagram using only MSX data.  
  > "We find no C/O division in any color-color diagram that utilizes only MSX data." (Conclusion)

## Claim tuples

- H: Can SiO detection rates with IR colors separate O-AGBs, C-AGBs and YSOs? | E: Plot detection rate across MSX and 2MASS color-color diagrams | R: [D]-[E]>1.35 isolates YSOs; Ks-A vs A-E separates O-rich (73% detection) from C-rich (12%) | F: Three populations are separable by IR colors | **supported**
- H: Is the OC-index a reliable chemistry predictor in BAaDE? | E: Check detection rate versus OC-index | R: Detection rate nearly constant across OC-index | F: OC-index is not reliable for thin-shell O-AGBs | **supported**
- H: Are many O-AGB non-detections due to variability/sensitivity? | E: Compare detection rates with re-observation studies | R: Re-observations of known masers give ~78% redetection | F: Most O-AGB non-detections are plausibly variability or sensitivity | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: [D]-WISE4 and [D]-MIPSGAL24 show no separation; [D]-[18] partially separates the DE-red population  
  > "neither \[D\]$-$\[WISE4\] nor \[D\]$-$\[24\] show significant separation of a red-colored low-detection-rate population" (4.1.1 Alternatives to [E] and the 18-micron feature)
- How they decided it was enough: _not stated_
- Limitation (authors): No reddening correction; non-simultaneous IR photometry; only ~10% ALMA, so few C-bearing molecule detections  
  > "our IR-colors have not been reddening corrected" (3.3 Sources which are exceptions)
- Caveat (inferred, ours): The C/O boundary is empirical and tuned on the same SiO detections it is tested on
- Caveat (inferred, ours): SiO non-detection is not a clean C-rich tracer
- Caveat (inferred, ours): Only 45% of sources have reliable [E] magnitudes
- Caveat (inferred, ours): Cross-match errors are not propagated

## Reproducibility

- Data public (paper): Spectra are available on the survey website  
  > "Spectra for each source can be found on the survey website" (2 Observations/BAaDE)
- Products in archive: _not stated_
- Missing: Full source table with IR magnitudes and detection flags
- Missing: ALMA/VLA reduction recipe (deferred to in-preparation paper)
- Data volume (inferred): Small for catalog-level reanalysis (survey tables); large if raw ALMA data are reprocessed
- Score (inferred): 3/5, Analysis is simple color cuts and counts, but depends on catalogs and detection tables not provided in the paper, and the ALMA processing is deferred to other papers.
- Rediscovery candidate: no, ALMA part is minor and the detection tables are not given in the paper.

## Links

- Method: Sjouwerman et al. 2020 (cite: baade) (BAaDE survey description)
- Method: Sjouwerman, Capen & Claussen 2009 (cite: scc) (MSX color selection and OC-index)
- Companion: Stroh et al. 2019 (cite: michael2) (ALMA CS imaging of BAaDE sources)
- Companion: Stroh et al. 2018 (cite: michael) (43 vs 86 GHz comparison)
- Related: BAaDE
- Related: MSX
- Related: 2MASS
- Related: AKARI

## Checks

```json
{
 "quotes": 37,
 "quotes_ok": 37,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 24,
  "rate": 0.358
 },
 "evidence_ok": true
}
```
