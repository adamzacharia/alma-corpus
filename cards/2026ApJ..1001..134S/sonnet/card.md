# Protostellar Outflows Shed Light on the Dominant Close Companion Star Formation Pathways

`2026ApJ..1001..134S` | The Astrophysical Journal 2026 | first author: Sponzilli, Ryan | arXiv: 2603.01347 | DOI: 10.3847/1538-4357/ae4a29

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Are close-companion protostars (<~500 au) formed mainly by disk fragmentation or by turbulent fragmentation plus inward migration, as probed by alignment of 12CO outflows with the binary axis?  
  > "we seek to differentiate between these two mechanisms using angular momentum as a discriminant" (Introduction)
- Target **51 Class 0/I close-companion systems in Perseus (11) and Orion (40)**: coordinates field centers in Data by Field table (e.g. Per-emb-22 RA 51.34337, Dec 30.75368)  
  > "Distances to systems in Orion are adopted from (cite: Tobin_et_al_2022), and distances to systems in Perseus are adopted as an average of 300 pc (cite: Zucker+2018)." (2.1 Sample Selection); z/distance Perseus 300 pc average; Orion from Tobin et al. 2022  
  > "Distances to systems in Orion are adopted from (cite: Tobin_et_al_2022), and distances to systems in Perseus are adopted as an average of 300 pc (cite: Zucker+2018)." (2.1 Sample Selection); distance from Zucker+2018 (Perseus); Tobin et al. 2022 (Orion)  
  > "Distances to systems in Orion are adopted from (cite: Tobin_et_al_2022), and distances to systems in Perseus are adopted as an average of 300 pc (cite: Zucker+2018)." (2.1 Sample Selection)

## Data provenance

- ALMA projects: 2018.1.01038.S, 2017.1.00053.S
- bands: Band 6 (1.3 mm), both Orion and Perseus  
  > "The observations were in Band 6 at 1.3 mm." (2.2 Orion Data)
- frequencies and spectral setup: Orion: 12CO(2-1) 938 MHz window with 488 kHz channels; continuum 1.875 GHz centered at 233.5 GHz. Perseus: continuum 2 GHz at 232.5 GHz; 12CO in 234 MHz window with 488 kHz channels  
  > "The third baseband was configured with one 938 MHz spectral window with 488 kHz channels centered on $^{12}$CO ($J=2\rightarrow1$)." (2.2 Orion Data); "The correlator was configured for the first baseband to observe a 2 GHz continuum band centered at 232.5 GHz" (2.3 Perseus Data)
- continuum bandwidth: _not stated_
- arrays: ALMA main array (12 m)  
  > "The Orion multiple systems were observed with the ALMA main array (12 m)" (2.2 Orion Data)
- configurations: _not stated_
- baselines: ~15 m to ~2500 m  
  > "sampling baselines between $\sim$15 m and $\sim$2500 m" (2.2 Orion Data)
- angular resolution: Orion 12CO beam 0.22'' x 0.17''; Perseus 0.29'' x 0.21''  
  > "a synthesized beam of 0.22$''$$\times$0.17$''$" (2.2 Orion Data); "a synthesized beam of 0.29$''$$\times$0.21$''$" (2.3 Perseus Data)
- max recoverable scale: _not stated_
- sensitivity: Orion: continuum ~0.2 mJy/beam, 12CO ~2 mJy/beam; Perseus: continuum ~0.5 mJy/beam, 12CO 3.7 mJy/beam  
  > "The noise in the 1.3 mm continuum was $\sim$0.2 mJy beam$^{-1}$, and the noise in the $^{12}$CO ($J=2\rightarrow1$) cubes was $\sim$2 mJy beam$^{-1}$." (2.2 Orion Data); "The noise in the 1.3 mm continuum was $\sim$0.5 mJy beam$^{-1}$, and the noise in the $^{12}$CO ($J=2\rightarrow1$) cubes was 3.7 mJy beam$^{-1}$." (2.3 Perseus Data)
- time on source: ~20 min per source in Orion; ~19 min per source in Perseus  
  > "with approximately 20 minutes on each source" (2.2 Orion Data); "with approximately 19 minutes on each source" (2.3 Perseus Data)
- observing dates: Orion: Oct-Nov 2018; Perseus: Dec 2017 to Sep 2018  
  > "on 2017 December 17, 2018 January 7, 2018 January 11, 2018 January 19, and 2018 September 20" (2.3 Perseus Data)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Other facility **VLA (VANDAM survey)**: Source positions/separations and sample identification of close companions  
  > "The NSF’s Karl G. Jansky Very Large Array (VLA) conducted the VLA/ALMA Nascent Disk and Multiplicity Survey (VANDAM) in both Orion and Perseus" (2.1 Sample Selection)
- External data: Binary separations, classes and source coordinates for Orion/Perseus systems  
  > "These data are from Table 3 and Table 4 in (cite: Tobin_et_al_2022)." (Table 1 notes) [from Tobin_et_al_2022]
- External data: Perseus source coordinates  
  > "The binary separation PAs are derived using the coordinates from each YSO reported by (cite: Tobin_et_al_2018; Tobin_et_al_2022) and (cite: Reynolds_et_al_2024)." (3.1 Measuring Outflows) [from Tobin_et_al_2018; Reynolds_et_al_2024]
- External data: Perseus distance of 300 pc  
  > "distances to systems in Perseus are adopted as an average of 300 pc (cite: Zucker+2018)" (2.1 Sample Selection) [from Zucker+2018]
- Simulation/model as data: Monte Carlo models of projected delta-PA, 101 mixtures of orthogonal and random 3D alignment, 100,000 draws each  
  > "The 101 distributions were constructed with Monte Carlo-style simulations, each based on 100,000 random draws." (3.3 Model Comparisons)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline in CASA, plus additional self-calibration of continuum, applied to lines  
  > "The raw visibility data were reduced using the ALMA pipeline integrated within CASA 5.6.1 (cite: CASA)." (2.2 Orion Data)
- casa version: Orion CASA 5.6.1; Perseus CASA 5.4.0 (self-cal 5.6.1); L1448 IRS3C CASA 6.6.1  
  > "The raw visibility data were reduced by the ALMA pipeline integrated within CASA 5.4.0 (cite: CASA)." (2.3 Perseus Data); "we imaged those data with the ALMA pipeline included in CASA 6.6.1 using automated self-calibration" (2.3 Perseus Data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Two rounds phase-only (scan length, then 18.15 s or 6.05 s in Orion; 12.1 s or 6.05 s in Perseus), then amplitude self-cal with scan-length solint, solnorm=True  
  > "two rounds of phase-only self-calibration where the first solution interval corresponded to the length of a single scan and the second solution interval corresponded to 18.15 s or 6.05 s" (2.2 Orion Data); "we used the option `solnorm=True` to normalize the amplitude solutions to 1" (2.2 Orion Data)

### Imaging

- task: tclean via ALMA pipeline tasks hif_makeimlist/hif_makeimages/hif_editimlist  
  > "The continuum images were produced using standard calls to the ALMA pipeline tasks `hif_makeimlist` and `hif_makeimages`." (2.2 Orion Data)
- deconvolver: _not stated_
- weighting robust: Briggs robust=0.5  
  > "We used Briggs weighting with a `robust=0.5` with calls to `tclean`" (2.2 Orion Data)
- uv taper: _not stated_
- cell size: 12CO cubes 0.034'' (Orion), 0.041'' (Perseus); continuum 0.031'' / 0.03''  
  > "a pixel scale of 0.034$''$" (2.2 Orion Data); "a pixel scale of 0.041$''$" (2.3 Perseus Data)
- image size: 12CO cubes 1372x1372 (Orion), 1000x1000 (Perseus)  
  > "typically had 1372$\times$1372 pixels" (2.2 Orion Data); "typically had 1000$\times$1000 pixels" (2.3 Perseus Data)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 12CO channels 1 km/s (Orion), 0.66 km/s (Perseus), imaged ±100 km/s of source velocity  
  > "we used 1 km s$^{-1}$ channels and imaged $\pm$100 km s$^{-1}$ of the source velocity" (2.2 Orion Data); "we used 0.66 km s$^{-1}$ channels" (2.3 Perseus Data)
- final beam: 12CO: 0.22''x0.17'' Orion, 0.29''x0.21'' Perseus  
  > "a synthesized beam of 0.22$''$$\times$0.17$''$" (2.2 Orion Data)
- final rms: 12CO ~2 mJy/beam Orion, 3.7 mJy/beam Perseus  
  > "the noise in the $^{12}$CO ($J=2\rightarrow1$) cubes was 3.7 mJy beam$^{-1}$" (2.3 Perseus Data)

### Inherited from earlier work

- Close-companion definition (<~500 au), distances, separations, classes  
  > "we define close companions as protostars with projected separations $\lesssim$500 au (cite: Tobin_et_al_2022)" (2.1 Sample Selection) [from (cite: Tobin_et_al_2022)]
- Perseus targets identified from earlier ALMA Cycle 2 program  
  > "from the VANDAM Perseus survey and a previous ALMA Cycle 2 program (cite: Tobin_et_al_2018), we identified 11 close-companion protostars" (2.1 Sample Selection) [from (cite: Tobin_et_al_2018)]

### Not stated but needed to reproduce (our reading)

- Line-free channels / continuum subtraction for CO cubes
- Masks and clean thresholds, niter, deconvolver used in tclean
- Which velocity channel was used per outflow for edge tracing (only integrated ranges in appendix table)
- Exact flux calibrators and flux scale uncertainty
- Random seed and exact KS procedure details (which ΔPA folded to 0-90 range)
- Cubes' primary beam correction not stated
- Eye-measured PAs are subjective; no automated recipe

## Analysis recipe

1. **Calibrate, self-calibrate and image continuum and 12CO**: ALMA pipeline, phase and amplitude self-cal on continuum applied to lines, tclean imaging with robust=0.5  
  > "Following the completion of self-calibration on the continuum, the solutions were also applied to the spectral line data." (2.2 Orion Data)
   - software: CASA
   - parameter: robust=0.5; 12CO 1 km/s (Orion) and 0.66 km/s (Perseus) channels  
  > "using Briggs weighting with `robust=0.5` for all images" (2.3 Perseus Data)
   - fitting: _not stated_
   - validation: Automated vs manual self-cal compared for L1448 IRS3C, similar results  
  > "Comparison of self-calibration done through the automated imaging service versus the manual self-calibration showed very similar results" (2.3 Perseus Data)
2. **Measure outflow position angles by eye**: Trace both outflow edges of each lobe with the CARTA line tool through the continuum source position, measure with protractor counterclockwise from north, centre = mean of edges; average lobes; PA refers to blue lobe  
  > "We measure outflow PAs by eye with a protractor on the $^{12}$CO ($J=2\rightarrow1$) data within Cube Analysis and Rendering Tool for Astronomy (cite: carta)." (3.1 Measuring Outflows)
   - software: CARTA
   - parameter: Uncertainty 10 deg for high confidence, 30 deg for low confidence  
  > "We adopt uncertainties of 10$^\circ$ for HC outflows and 30$^\circ$ for LC outflows." (3.1 Measuring Outflows)
   - assumption: Outflow is a proxy for angular momentum, orthogonal to binary orbital plane  
  > "The outflow, as traced by $^{12}$CO ($J=2\rightarrow1$), is a useful proxy for the angular momentum of the system, expected to be orthogonal to the binary orbital plane." (abstract)
   - fitting: _not stated_
   - validation: Compared with previous Perseus outflow PA measurements, general agreement  
  > "we independently remeasured outflows in each Perseus system and found general agreement with previous results" (3.1 Measuring Outflows)
3. **Compute delta-PA between outflow PA and binary separation PA**: Binary PA from literature source coordinates; ΔPA = outflow PA minus binary PA; not computed for tertiary outflows  
  > "For each outflow, we then calculate $\Delta$PA, defined as the difference between the outflow PA and the binary separation PA." (3.1 Measuring Outflows)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare observed ΔPA to simulated alignment models**: 101 Monte Carlo models mixing orthogonal and random 3D alignment with random inclination (uniform in cos i) and binary PA; 2-sample KS test against observed ΔPA  
  > "For each of these simulated distributions, we compare them to our observed distribution of $\Delta$PA with a 2-sample Kolmogorov-Smirnov (KS) test." (3.3 Model Comparisons)
   - parameter: 100,000 draws per model; 1% steps; significance p=0.05  
  > "Using a significance level of p = 0.05, we fail to reject the null hypothesis of a dominantly orthogonal model" (3.3 Model Comparisons)
   - assumption: Inclination uniform in cos i between 0 and 90 deg (mean 60 deg)  
  > "with a uniform distribution in $\cos i$, yielding a mean inclination of 60$^\circ$" (3.3 Model Comparisons)
   - fitting: KS p-value scan over orthogonal fraction  
  > "We use these p-values to identify the fraction of orthogonal outflows for which the data is no longer consistent with the observations." (Model Comparisons)
   - validation: _not stated_

## Software

- **CASA** 5.4.0, 5.6.1, 6.6.1: Pipeline calibration, self-calibration, tclean imaging  
  > "We additionally performed self-calibration with CASA 5.6.1 on the continuum data" (2.2 Orion Data)
- **CARTA** : Measuring outflow PAs and viewing cubes  
  > "First, we load the $^{12}$CO ($J=2\rightarrow1$) and 1.3 mm (2 GHz band centered at 232.5 GHz) continuum data into CARTA." (3.1 Measuring Outflows)
- **Astropy** : General analysis  
  > "This work made use of Astropy, a community-developed core Python package" (Acknowledgments)
- **APLpy** : Plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Systems with measured outflows | 38 of 51 | not stated | systems | 2 | In total, we measure at least one outflow in 38 systems. |
| Number of ΔPA values | 42 | not stated | outflows | 3 | This leaves us with 42 values for $\Delta$PA |
| Best-fit orthogonal fraction (max KS p ~0.68) | 94% | not stated | percent | 4 | The highest KS-test p-value (p $\sim$0.68) occurs for a 94% orthogonal distribution |
| Minimum orthogonal fraction consistent at p=0.05 | >71% | not stated | percent | 4 | at this threshold, our data are consistent with a $>$71% orthogonal model |
| Binary separation range and median | min 24 au, max 573 au, median 100 au | not stated | au | 3 | the maximum binary separation is 573 au, the minimum is 24 au, and the median is 100 au |
| Binaries with one observable outflow | 34/38 (90%) | not stated | systems | 2 | Nearly all of our measured sample, 90% (34/38), contain a close binary system that has only one observable outflow. |

## Qualitative findings

- Observed ΔPA strongly skewed toward 70-90 deg, i.e. outflows nearly orthogonal to binary axis in projection  
  > "the observed $\Delta$PA values are strongly skewed toward large angles (70°–90°)" (3.2 Outflow Detections and Morphologies)
- Per-emb-27, Per-emb-35, HOPS-290 with two misaligned outflows favour turbulent fragmentation plus migration; Per-emb-33 a prime disk fragmentation example  
  > "Per-emb-33 is a prime example of disk fragmentation." (4.5 Hierarchical Triples with Two Outflows)

## Claim tuples

- H: Close companions are preferentially aligned (outflows orthogonal to binary axis), indicating disk fragmentation | E: Measured 42 outflow PAs in 38 systems and compared ΔPA to Monte Carlo models with KS tests | R: Data consistent with >71% orthogonal; best match 94% (p~0.68) | F: Disk fragmentation is likely the dominant pathway for close companions | **supported**
- H: Alignment uniquely discriminates the pathways | E: Discussion of reorientation via circumbinary accretion and scarcity of fragmenting disks | R: Turbulent fragmentation plus migration followed by realignment could also yield orthogonal outflows | F: Interpretation is complicated | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Outflow PA used as proxy for angular momentum direction  
  > "We use outflow position angles (PAs) as a proxy for the angular momentum directions of the protostars" (Introduction)
- Alternative: Turbulent fragmentation with migration plus realignment by circumbinary accretion  
  > "subsequent accretion from a reformed circumbinary disk could torque and similarly bring the outflows into alignment" (4.1 Alignment Interpretations)
- How they decided it was enough: _not stated_
- Limitation (authors): KS p-values reflect only consistency, not proof  
  > "We caution, however, that these p-values reflect only statistical consistency with, rather than proof of, the null model." (3.3 Model Comparisons)
- Caveat (inferred, ours): PAs measured by eye with subjective uncertainties of 10/30 deg, not propagated into the KS test
- Caveat (inferred, ours): Model assumes binary PA uniform and ignores uncertainty in binary PA and evolving orientation
- Caveat (inferred, ours): Single ΔPA test cannot separate disk fragmentation from realigned migrated systems
- Caveat (inferred, ours): Binary PA/outflow PA ambiguity for unresolved launching sources; 13 systems without outflows may bias sample
- Caveat (inferred, ours): Folding of ΔPA to 0-90 deg not explicit

## Reproducibility

- Data public (paper): ALMA data and reduction scripts available from ALMA archive; figures, tables, scripts, FITS images in Illinois Data Bank  
  > "The ALMA data and reduction scripts are available from the ALMA archive." (Acknowledgments)
- Products in archive: _not stated_
- Code: Figures, tables, scripts used to make them, and FITS images in Illinois Data Bank  
  > "The figures, tables, scripts used to make them, and FITS images are available in the Illinois Data Bank" (Acknowledgments)
- Missing: Cleaning masks/thresholds and line-free handling
- Missing: Per-outflow channel choices for edge tracing
- Missing: Exact KS/ΔPA folding implementation (scripts in Data Bank)
- Data volume (inferred): ~1-3 TB raw for two 12 m Band 6 projects (51 fields); image cubes ~tens of GB
- Score (inferred): 3/5, Data public and pipeline steps described, but PA measurements were by eye and imaging masks unstated; statistical model is simple and reproducible.
- Rediscovery candidate: no, Key measurements are subjective by-eye PAs, requiring large dataset reprocessing; model portion is reproducible given the table.

## Links

- Method: Tobin_et_al_2022 (Source of sample, separations, distances)
- Method: Tobin_et_al_2018 (Perseus source coordinates and prior ALMA program)
- Companion: Reynolds_et_al_2024 (Disk fragmentation vs turbulent fragmentation classifications for Perseus)
- Companion: Dunham_et_al_2024 (Prior Perseus outflow PA measurements)
- Related: VANDAM (VLA/ALMA Nascent Disk and Multiplicity Survey)
- Related: ALMA Cycle 3/4 Orion protostar survey

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
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
  "facts": 76,
  "stated": 52,
  "rate": 0.684
 },
 "evidence_ok": true
}
```
