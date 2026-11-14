# High-z Sudoku: a diagnostic tool for identifying robust (sub)mm redshifts

`2022MNRAS.515..678B` | Monthly Notices of the Royal Astronomical Society 2022 | first author: Bakx, Tom J. L. C. | arXiv: 2204.06011 | DOI: 10.1093/mnras/stac1306

Card schema 1.0 | model gemini-4-argon | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: high_z_galaxies
- Question: How to graphically identify robust spectroscopic redshifts of high-z galaxies from (sub)mm lines, evaluate the capabilities of (sub)mm redshift search practices, and optimise future ALMA observations.  
  > "We present methods to (i) graphically identify robust redshifts using emission lines in the (sub)mm regime, (ii) evaluate the capabilities of different (sub)mm practices for measuring spectroscopic redshifts, and (iii) optimise future (sub)mm observations towards increasing the fraction of robust redshifts." (Abstract)

## Data provenance

- ALMA projects: 2016.2.00133.S, 2018.1.00804.S, 2019.2.00155.S
- bands: Band 3 (3 mm) and Band 4 (2 mm)  
  > "the optimum lying at the middle frequencies in band 3 (3 mm) and at higher frequencies in band 4 (2 mm)" (Optimising ALMA tunings for spectroscopic redshifts); "Figure 1 shows the effect of including band 4 (2 mm)." (Combined 3 and 2 mm tunings)
- frequencies and spectral setup: 89.1 - 112.0 GHz and 139.9 - 162.7 GHz (optimised B3 & B4); 84.2 - 114.9 GHz and 125 - 159.25 GHz (spectral scan B3 & B4); 84.2 - 114.9 GHz (ALMA B3 fill)  
  > "ALMA: | $89.1 - 112.0$ & | / | $3.37 - 2.68$ &" (Table 1); "Spectral scan: | $84.2 - 114.9$ & | / | $3.56-2.61$ &" (Table 1); "ALMA B3 fill $84.2 - 114.9$ / $3.56-2.61$" (Table 1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: P.I.: Bakx (2019.2.00155.S)  
  > "These results are in line with the impressive redshift search efficiency shown in (cite: Urquhart2022) (as well as in subsequent follow-up; P.I.: Bakx, 2019.2.00155.S), showing a robust redshift ratio of 72%, and even promising up to 93% with deeper observations." (Combined 3 and 2 mm tunings)
- Line: CO rotational ladder (CO(1-0) to CO(12-11)) (not stated)
- Line: [CI] 1-0 (not stated)
- Line: H2O not stated (not stated)
- Line: [CII] 158 um (not stated)
- Line: [OIII] 88 um (not stated)
- Line: [NII] 122 um (not stated)
- External data: CO SLED of typical bright DSFGs from Planck-selected sources  
  > "We show the CO SLED of typical bright DSFGs from Planck-selected sources (cite: Harrington2021), a CO SLED from the Milky Way (cite: Fixsen1996), and the maximum expected excitation from a thermalized profile." (Excluding redshift regimes) [from (cite: Harrington2021)]
- External data: CO SLED from the Milky Way  
  > "We show the CO SLED of typical bright DSFGs from Planck-selected sources (cite: Harrington2021), a CO SLED from the Milky Way (cite: Fixsen1996), and the maximum expected excitation from a thermalized profile." (Excluding redshift regimes) [from (cite: Fixsen1996)]
- External data: Redshift distribution of the Herschel-selected HerBS sample  
  > "Figure 1 shows the probability of a robust redshift of various configurations and instruments that are often used for redshift searches between $z = 0$ and 8, and for two different DSFG samples (HerBS; (cite: bakx18; Bakx2020Erratum), South Pole Telescope; (cite: reuter20) , see Fig. 2)." (Redshift searches) [from (cite: bakx18; Bakx2020Erratum)]
- External data: Redshift distribution of the South Pole Telescope (SPT) sample  
  > "Figure 1 shows the probability of a robust redshift of various configurations and instruments that are often used for redshift searches between $z = 0$ and 8, and for two different DSFG samples (HerBS; (cite: bakx18; Bakx2020Erratum), South Pole Telescope; (cite: reuter20) , see Fig. 2)." (Redshift searches) [from (cite: reuter20)]

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

- Graphical method for identifying robust redshifts  
  > "In this paper, we expand on the graphical method from (cite: Bakx2020IRAM) which provides a more user-friendly method for identifying robust redshifts." (Introduction) [from (cite: Bakx2020IRAM)]

### Not stated but needed to reproduce (our reading)

- Exact rest frequencies of all spectral lines included in the redshift-search-graphs code
- Exact atmospheric transmission model used to mask opaque regions (PWV > 0.5 mm, transmission < 80% of peak)

## Analysis recipe

1. **Graphically identify potential and robust spectroscopic redshifts from observed bandwidths and line frequencies**: Plot observed bandwidths and detected spectral line frequencies against redshift, marking intersections with redshifted CO, [CI], and H2O lines, and excluding alternative solutions where expected additional CO lines are undetected at >8 sigma  
  > "Where the observed lines cross the redshifted spectral lines, a circle marks the potential spectroscopic redshift, with the circle’s fill representing the underlying colour." (Explanation of the graphical method); "Taking into account measurement errors, as well as this line ratio, the exclusion method thus requires relatively-high signal-to-noise ($>8 \sigma$) detections to be robust." (Excluding redshift regimes)
   - software: redshift-search-graphs
   - parameter: Signal-to-noise > 8 sigma required to exclude alternative CO redshift solutions from non-detections  
  > "Taking into account measurement errors, as well as this line ratio, the exclusion method thus requires relatively-high signal-to-noise ($>8 \sigma$) detections to be robust." (Excluding redshift regimes)
   - assumption: Maximum thermalized CO SLED profile where velocity-integrated fluxes increase with J^2  
  > "The Milky Way CO SLED has a sharp drop-off in velocity-integrated fluxes for J$_{\rm up}$ transitions greater than 3, however for star-bursting galaxies, these SLEDs can approach the maximum thermalized profile, where velocity-integrated fluxes increase with $J^2$ (see (cite: carilli2013))." (Excluding redshift regimes)
   - assumption: 1-sigma uncertainty in sub-mm photometric redshifts is typically 13% or 7% in Delta z / (1+z)  
  > "This mis-identification is a non-negligible possiblity given the large 13% uncertainties in sub-mm derived photometric redshifts of around $\Delta z$ $\sim$ 1 (defined as $\Delta z / (1+z)$, e.g. (cite: pearson13; ivison16; bakx18)), although Bendo et al. in prep. finds a sharp reduction in uncertainty down to $\sim 7$%." (Explanation of the graphical method)
   - fitting: _not stated_
   - validation: Demonstrated on fiducial galaxy scenarios (Figures 1 to 5)  
  > "we show this graphical method for a fiducial $z_{\rm phot} = 3$ example source observed with an efficient ALMA tuning setup" (Explanation of the graphical method)
2. **Quantify the redshift search efficiency of (sub)mm instruments and tuning configurations**: Calculate the probability of obtaining robust (single- or multi-line) and ambiguous redshifts between z = 0 and 8, weighted by smoothed HerBS and SPT redshift distributions, defining robust CO detections by exclusion of all adjacent solutions within 5 sigma or detection of a non-CO line  
  > "Figure 1 shows the probability of a robust redshift of various configurations and instruments that are often used for redshift searches between $z = 0$ and 8, and for two different DSFG samples (HerBS; (cite: bakx18; Bakx2020Erratum), South Pole Telescope; (cite: reuter20) , see Fig. 2)." (Redshift searches); "We define a robust detection by either a detection in CO where all adjacent solutions within 5$\sigma$ (eq. [\[eq:Nsigma\]](#eq:Nsigma)) can be excluded, or through the detection of a non-CO line." (Redshift searches)
   - software: redshift-search-graphs
   - parameter: Redshift distributions smoothed by dz approx 0.5  
  > "The distributions are smoothed by $dz \approx 0.5$ to prevent small-number variations in the final efficiency metrics." (Redshift searches)
   - parameter: Robust CO detection threshold: adjacent solutions within 5 sigma excluded  
  > "We define a robust detection by either a detection in CO where all adjacent solutions within 5$\sigma$ (eq. [\[eq:Nsigma\]](#eq:Nsigma)) can be excluded, or through the detection of a non-CO line." (Redshift searches)
   - assumption: Remove frequency regions opaque under normal observing conditions (PWV > 0.5 mm, transmission > 80% of the peak)  
  > "For the calculation in Figure 1, we remove regions that are opaque under normal observing conditions (assuming precipitable water vapour $> 0.5$ mm, with transmission greater than 80% of the peak)." (Redshift searches)
   - assumption: Average redshift of HerBS sample is z_bar approx 2.5 and SPT sample is z_bar = 3.5  
  > "The average redshift of the Herschel-selected HerBS sample is $\bar{z} \approx 2.5$, while the SPT sample is selected at longer wavelengths and has an average $\bar{z} = 3.5$." (Redshift searches)
   - fitting: _not stated_
   - validation: Compared predicted efficiency with observational results of Urquhart et al. (2022) and project 2019.2.00155.S  
  > "These results are in line with the impressive redshift search efficiency shown in (cite: Urquhart2022) (as well as in subsequent follow-up; P.I.: Bakx, 2019.2.00155.S), showing a robust redshift ratio of 72%, and even promising up to 93% with deeper observations." (Combined 3 and 2 mm tunings)
3. **Optimise ALMA Band 3 and Band 4 tunings for spectroscopic redshift searches**: Evaluate figure of merit across combinations of three tunings at 3 mm and three tunings at 2 mm (six tunings total) on a smoothed HerBS-like redshift distribution, weighting robust redshifts by 100% and non-robust redshifts by 50%  
  > "The proposed configuration uses a total of six tunings to generate two near-contiguous frequency coverages at both 3 and 2 mm, which removes the overlapping region of the 3 mm scan." (Optimising ALMA tunings for spectroscopic redshifts); "The total figure of merit is determined not solely by robust redshifts (either through single- or multiple-lines), but we choose to additionally add non-robust redshifts, weighted down by 50%." (Optimising ALMA tunings for spectroscopic redshifts)
   - software: redshift-search-graphs
   - parameter: 6 tunings total (3 in Band 3 and 3 in Band 4)  
  > "The proposed configuration uses a total of six tunings to generate two near-contiguous frequency coverages at both 3 and 2 mm, which removes the overlapping region of the 3 mm scan." (Optimising ALMA tunings for spectroscopic redshifts)
   - parameter: Non-robust redshifts weighted down by 50% in figure of merit  
  > "The total figure of merit is determined not solely by robust redshifts (either through single- or multiple-lines), but we choose to additionally add non-robust redshifts, weighted down by 50%." (Optimising ALMA tunings for spectroscopic redshifts)
   - assumption: Photometric redshift uncertainty Delta z / (1+z) approx 7%  
  > "Figure 1 shows the figure of merit for each possible combination of 3 and 2 mm regions on a smoothed redshift distribution similar to the HerBS targets (cite: bakx18; Bakx2020Erratum), assuming a low uncertainty in the $z_{\rm phot}$ of $\Delta z / (1+z) \approx 7$%." (Optimising ALMA tunings for spectroscopic redshifts)
   - fitting: Grid search over all possible combinations of 3 and 2 mm frequency regions  
  > "Figure 1 shows the figure of merit for each possible combination of 3 and 2 mm regions on a smoothed redshift distribution similar to the HerBS targets (cite: bakx18; Bakx2020Erratum), assuming a low uncertainty in the $z_{\rm phot}$ of $\Delta z / (1+z) \approx 7$%." (Optimising ALMA tunings for spectroscopic redshifts)
   - validation: Compared with ALMA 12m array observations in Urquhart et al. (2022)  
  > "The frequencies of the ALMA 12m array observations in (cite: Urquhart2022) were derived using a similar method. They report redshift search efficiencies similar to the ones suggested by Figure 1, with a robust redshift fraction of 72%, and promising to go up to 93% with deeper observations." (Optimising ALMA tunings for spectroscopic redshifts)

## Software

- **redshift-search-graphs** : Python-based code and example scripts for graphically identifying robust redshifts, evaluating instrument efficiencies, and optimising receiver tunings  
  > "Using this publicly-available code (https://github.com/tjlcbakx/redshift-search-graphs), we discuss scenarios where robust redshifts can be identified using both single- and multiple-line detections, as well as scenarios where the redshift remains ambiguous, even after the detection of multiple lines." (Abstract); "The python-based code and example scripts for each of the graphs in this paper are publicly available at https://github.com/tjlcbakx/redshift-search-graphs, and can be easily and swiftly adapted for the reader’s own needs." (Introduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Required signal-to-noise ratio to exclude alternative CO redshift solutions from single-line detection | >8 | not stated | sigma | 1 | Taking into account measurement errors, as well as this line ratio, the exclusion method thus requires relatively-high signal-to-noise ($>8 \sigma$) detections to be robust. |
| Optimised ALMA Band 3 frequency coverage | 89.1 - 112.0 | not stated | GHz | 3 | ALMA: / $89.1 - 112.0$ & |
| Optimised ALMA Band 4 frequency coverage | 139.9 - 162.7 | not stated | GHz | 3 | B3 & B4 / $139.9 - 162.7$ / |
| Figure of merit for combined ALMA Band 3 and Band 4 tunings | 0.83 to 0.94 | not stated | dimensionless | 3 | The figure of merit varies between 0.83 to 0.94 for different combinations of the 3 and 2 mm window |
| Robust redshift fraction beyond z > 2 for combined ALMA 3 and 2 mm tunings | > 70 | not stated | % | 2 | While there exists some regions where multiple lines fail to provide robust redshifts assuming the Herschel-based photometry (cite: pearson13), the refined photometric redshifts from the 2 mm continuum (black dashed lines) result in high ($> 70$%) robust redshifts beyond $z > 2$, at the limited cost of including an additional tuning ($\sim 20$% longer observation). |

## Qualitative findings

- 2 mm (ALMA Band 4) observations are indispensable for deriving robust spectroscopic redshifts in the z = 2 - 4 regime alongside 3 mm (Band 3) observations.  
  > "Finally, we provide a method to optimise the observation strategy for future (sub)mm spectroscopic redshift searches with the Atacama Large Millimetre/submillimetre Array, where 2 mm proves indispensable for robust redshifts in the $z = 2 - 4$ region." (Abstract)
- Even multiple detected CO lines remain ambiguous when the ratio of their upper rotational transitions J_up can be multiplied to form another set of integers.  
  > "Such scenarios occur when the ratio of the upper transition (J$_{\rm up}$) of both CO line transitions can be multiplied to form another set of integer numbers." (Inconclusive redshifts from multiple CO lines)
- A single spectral line detected at >8 sigma can yield a robust redshift if neighbouring CO solutions would require additional lines within the observed bandwidth and low-z interlopers are excluded by photometric redshifts.  
  > "Using the photometric redshift as a guide, we can exclude this possibility, leaving only $z_{\rm spec} = 3.0$ as a solution, with the detected line being CO(5-4)." (Robust redshifts from single-line detections); "Taking into account measurement errors, as well as this line ratio, the exclusion method thus requires relatively-high signal-to-noise ($>8 \sigma$) detections to be robust." (Excluding redshift regimes)

## Claim tuples

- H: A graphical diagnostic tool can identify robust spectroscopic redshifts from single- and multiple-line detections while highlighting redshift degeneracies. | E: Developed the redshift-search-graphs code and demonstrated it on fiducial (sub)mm line detection scenarios (CO only, CO + [CI], single bright line, and degenerate multi-CO lines) alongside CO SLED excitation limits. | R: Demonstrated that non-detections of expected CO lines in covered bandwidths exclude alternative redshift solutions when the detected line has S/N > 8 sigma, while multi-CO detections with integer-multipliable J_up ratios remain degenerate. | F: The graphical method removes the need to manually cross-compare redshift options, enables exclusion of untenable redshift solutions, and highlights degeneracies. | **supported**
- H: Combining ALMA Band 3 (3 mm) and Band 4 (2 mm) tunings significantly improves the fraction of robust spectroscopic redshifts compared to filling the 3 mm band alone. | E: Calculated the probability of robust and ambiguous redshifts between z = 0 and 8 for ALMA B3 fill, combined B3 & B4, and spectral scans using HerBS and SPT redshift distributions, and optimised six tunings across B3 and B4. | R: Filling the 3 mm band alone guarantees single-line detections at z > 2 but gives only moderate robust CO redshifts, whereas adding 2 mm (89.1-112.0 GHz and 139.9-162.7 GHz) yields > 70% robust redshifts beyond z > 2 and a figure of merit up to 0.94. | F: 2 mm observations are indispensable for robust redshifts in the z = 2 - 4 regime with ALMA at the limited cost of an additional tuning (~20% longer observation). | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Numerically cross-comparing potential redshift solutions of individual lines is tedious, prone to confirmation bias towards z_phot, and fails to draw attention to redshift degeneracies or exclusions from non-detections.  
  > "This method is far from ideal, as it leads to confirmation bias for solutions close to the $z_{\rm phot}$ (cite: Yanai2020), and fails to draw attention to redshift degeneracies." (Introduction); "Numerically solving this cross-comparison is a tedious approach, prone to errors and overlooked options." (Graphical method)
- Alternative: Optical and radio redshift searches: struggled with positional uncertainty, dust extinction, limited bandwidth, and bias towards lower redshifts.  
  > "The first redshift searches used optical spectral lines, however they struggled with the positional uncertainty of SMGs and with a limited bandwidth. Radio observations improved the positions, but provide a strong bias towards lower redshifts, and are not workable for large, complete redshift samples (cite: chapman2005)." (Introduction)
- Alternative: Sub-mm photometric redshifts alone: remain only indicative of a redshift range due to the degeneracy between dust temperature and redshift.  
  > "Unfortunately, photometric redshifts from sub-mm colours remain only indicative of a redshift range (cite: casey2012; pearson13; ivison16; bakx18; Casey2020) due to the degeneracy between dust temperature and redshift (cite: Blain2003)." (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Exclusion of redshift regimes using non-detections is typically restricted to CO lines because the correlation between CO and [CI] emission strongly depends on ISM conditions.  
  > "These are typically restricted to CO lines, since the correlation between CO lines and [C i] emission strongly depends on the particular ISM conditions (see e.g., (cite: Valentino2018))." (Excluding redshift regimes)
- Limitation (authors): Dynamic follow-up observations in the 2 mm band with NOEMA/IRAM 30m do not lend themselves to easy generalization in the efficiency plot.  
  > "Follow-up observations in the 2 mm band do not lend themselves for easy generalization, which is why we were not able to generate a similar plot for a NOEMA 3- and 2 mm redshift search, although simply covering the 3- and 2 mm windows similar to the Band 3 & 4 linescan suggest a near-complete redshift coverage of the HerBS and SPT samples alike using four tunings." (NOEMA redshift searches)
- Limitation (authors): There is a small frequency gap (~0.5 GHz) around ~101 GHz and ~151 GHz in the optimum ALMA Band 3 & 4 configuration.  
  > "Note that there exist a small gap in frequency coverage ($\sim 0.5$ GHz) around $\sim 101$ GHz and $\sim 151$ GHz in the optimum ALMA Band 3 & 4 configuration." (Table 1)
- Caveat (inferred, ours): Efficiency calculations focus on frequency coverage and line multiplicity rather than full end-to-end sensitivity modelling of line luminosities and instrument noise per integration time.
- Caveat (inferred, ours): Although four ALMA project codes are acknowledged, no direct observational data reduction or source measurements from those projects are presented in the text.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: Publicly available Python code and example scripts at https://github.com/tjlcbakx/redshift-search-graphs  
  > "The python-based code and example scripts for each of the graphs in this paper are publicly available at https://github.com/tjlcbakx/redshift-search-graphs, and can be easily and swiftly adapted for the reader’s own needs." (Introduction); "All code used to derive the graphs in this paper are available at https://github.com/tjlcbakx/redshift-search-graphs in order to assist in the robust classification of redshifts in ongoing, future and past programs." (Data Availability)
- Missing: Exact version/commit of the GitHub repository used for the figures
- Data volume (inferred): < 10 MB (purely analytical/graphical scripts and 1D redshift distributions)
- Score (inferred): 9/5, All figures and tuning optimisations are generated by a lightweight, publicly released Python repository with example scripts included.
- Rediscovery candidate: no, Methodology paper presenting a graphical/analytical tool rather than empirical ALMA visibility/image analysis of astronomical targets.

## Links

- Method: (cite: Bakx2020IRAM) (Earlier paper introducing the initial version of the graphical redshift identification method expanded upon in this work)
- Companion: (cite: Urquhart2022) (Applied the optimised ALMA 12m array Band 3 and 4 tuning method to measure redshifts of Herschel-selected galaxies)
- Related: HerBS
- Related: South Pole Telescope (SPT)

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 16,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2019.1.01477.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 37,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
