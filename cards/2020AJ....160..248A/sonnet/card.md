# An ALMA Survey of λ Orionis Disks: From Supernovae to Planet Formation

`2020AJ....160..248A` | The Astronomical Journal 2020 | first author: Ansdell, Megan | arXiv: 2010.00012 | DOI: 10.3847/1538-3881/abb9af

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Do massive OB stars, in particular a possible supernova ~1 Myr ago, reduce the planet-forming material in the evolved λ Orionis cluster, and why do some massive outlier disks persist in evolved regions?  
  > "We assess how massive OB stars impact planet formation, in particular from the supernova that may have occurred ∼ 1 Myr ago in the core of λ Orionis" (abstract)
- Target **λ Orionis cluster disks (44 protoplanetary disks)**: coordinates not stated (per-source coordinates in Table 1; cluster centered on λ Ori)  
  > "We therefore adopt a distance of 400 pc for λ Orionis in the remainder of this work." (3.2 Host Star Properties); "Table 1 gives our final sample of the 44 protoplanetary disks analyzed in the remainder of this work." (3.1 Disk Sample Selection); z/distance 400 pc  
  > "We therefore adopt a distance of 400 pc for λ Orionis in the remainder of this work." (3.2 Host Star Properties); "Table 1 gives our final sample of the 44 protoplanetary disks analyzed in the remainder of this work." (3.1 Disk Sample Selection); distance from Gaia DR2 average of non-disk-bearing members, 404 ± 4 pc (Kounkel et al. 2018)  
  > "We therefore adopt a distance of 400 pc for λ Orionis in the remainder of this work." (3.2 Host Star Properties); "Table 1 gives our final sample of the 44 protoplanetary disks analyzed in the remainder of this work." (3.1 Disk Sample Selection)

## Data provenance

- ALMA projects: 2017.1.00466.S, 2016.1.00447.S
- bands: Band 6 (1.25 mm)  
  > "for a bandwidth-weighted mean continuum frequency of 239.36 GHz (1.25 mm)" (4.1 ALMA Observations)
- frequencies and spectral setup: four SPWs at 247.96, 245.46, 232.97, 230.51 GHz, 1.88 GHz usable bandwidth each; last SPW covers 12CO J=2-1 at ~1 km/s resolution  
  > "four spectral windows were centered on 247.96, 245.46, 232.97, and 230.51 GHz, each with usable bandwidths of 1.88 GHz" (4.1 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 13 execution blocks, range of configurations  
  > "the observations were conducted over 13 execution blocks" (4.1 ALMA Observations)
- baselines: 15–784 m to 15–1398 m (Table 3)  
  > "2018-01-24 44 15–1398 1.4" (Table 3)
- angular resolution: median beam 0.31″ × 0.29″  
  > "This results in a median continuum rms of 34 µJy and beam size of 0.31″ ×0.29″." (4.2 ALMA Continuum Results)
- max recoverable scale: _not stated_
- sensitivity: median continuum rms 34 µJy; 3σ dust mass ~0.4 M_earth  
  > "which has a 34 µJy median rms corresponding to 3σ dust mass upper limits of ∼ 0.4 M ⊕" (7. Summary)
- time on source: ~6 min per source  
  > "On-source integration times were ∼ 6 min per source" (4.1 ALMA Observations)
- observing dates: 2018-01-18 to 2018-09-09  
  > "2018-09-09 44 15–1213 2.1" (Table 3)
- pi or archival as stated: Cycle 5 program, PI Ansdell  
  > "taken in Cycle 5 under program 2017.1.00466.S (PI: Ansdell)" (4.1 ALMA Observations)
- Line: 12CO J=2-1 (not stated)
- Other facility **Gaia DR2**: proper motions, distances for interloper identification and cluster distance  
  > "We identify interlopers in the Spitzer sample by using distances from Gaia DR2 to find contaminant background sources" (3.1 Disk Sample Selection)
- Other facility **Spitzer**: disk census / sample selection (via Hernández et al. 2009, 2010)  
  > "Like most SFRs, the disk census in λ Orionis is based on targeted Spitzer observations" (3.1 Disk Sample Selection)
- Other facility **2MASS**: J-band magnitudes and positions for non-detections  
  > "or the Two Micron All-Sky Survey (2MASS; Skrutskie et al. 2006) positions for the non-detections" (3.2 Host Star Properties)
- External data: Spectral types, radial velocities of host stars  
  > "References for stellar spectral types (SpT) and radial velocities ( v LSR ): (1) Bayo et al. (2011), (2) Hern´andez et al. (2010)" (Table 1) [from Bayo et al. (2011); Hernández et al. (2010); Kounkel et al. (2018) etc.]
- External data: Comparison disk dust masses/fluxes for Lupus, σ Ori, Upper Sco, OMC-2  
  > "compares the M dust cumulative distribution for λ Orionis (this work) to that of OMC-2 (van Terwisga et al. 2019a), Lupus (Ansdell et al. 2018)" (5.2 Comparisons to Other Regions) [from van Terwisga et al. 2019a; Ansdell et al. 2018; Ansdell et al. 2017; Barenfeld et al. 2016]
- External data: Upper Sco stellar masses for two-sample tests  
  > "Using the M ⋆ values from Table 1 for λ Orionis and those from Barenfeld et al. (2016) for Upper Sco" (5.2 Comparisons to Other Regions) [from Barenfeld et al. (2016)]
- Simulation/model as data: Close & Pittard (2017) supernova-stripping hydrodynamic simulations compared to the disk masses  
  > "Close & Pittard (2017) ran three-dimensional hydrodynamic simulations of protoplanetary disks, with a range of masses and inclinations, subject to a supernova occurring 0.3 pc away." (6.1 Do Supernovae Impact Planet Formation?)

## Processing

### Calibration

- pipeline or manual: pipeline calibrated by NRAO staff  
  > "Data were pipeline calibrated by NRAO staff using the Common Astronomy Software Applications ( CASA ) package (McMullin et al. 2007) version 5.4.0." (4.1 ALMA Observations)
- casa version: CASA 5.4.0  
  > "package (McMullin et al. 2007) version 5.4.0." (4.1 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800 (bandpass/flux), J0423-0120 in one EB; phase J0532+0732  
  > "2018-09-09 44 15–1213 2.1 J0423 −0120," (Table 3)
- flux scale uncertainty: 10%  
  > "We assume an absolute flux calibration uncertainty of 10%" (4.1 ALMA Observations)
- self calibration: not performed  
  > "We do not perform selfcalibration as the detected sources are faint" (4.2 ALMA Continuum Results)

### Imaging

- task: split to average continuum, then tclean  
  > "by averaging over the continuum channels using the split task in CASA, then cleaning with a Briggs robust weighting parameter of +0.5 using the tclean task" (4.2 ALMA Continuum Results)
- deconvolver: _not stated_
- weighting robust: Briggs robust = +0.5  
  > "cleaning with a Briggs robust weighting parameter of +0.5 using the tclean task" (4.2 ALMA Continuum Results)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in CASA  
  > "by first subtracting the continuum using the uvcontsub task in CASA" (4.3 ALMA CO Results)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.31″ × 0.29″ median  
  > "median continuum rms of 34 µJy and beam size of 0.31″ ×0.29″" (4.2 ALMA Continuum Results)
- final rms: 34 µJy median  
  > "This results in a median continuum rms of 34 µJy" (4.2 ALMA Continuum Results)

### Inherited from earlier work

- 12CO detection procedure  
  > "To search for 12 CO emission, we follow the general procedure of Ansdell et al. (2017)." (4.3 ALMA CO Results) [from Ansdell et al. (2017)]
- Stellar mass estimation method  
  > "following the methods of Ansdell et al. (2017)" (3.2 Host Star Properties) [from Ansdell et al. (2017)]
- Dust opacity and β assumptions  
  > "these are the same assumptions as in Ansdell et al. (2016, 2017, 2018) and Cieza et al. (2019)" (5.1 Dust Masses) [from Ansdell et al. (2016, 2017, 2018); Cieza et al. (2019)]

### Not stated but needed to reproduce (our reading)

- Continuum channel selection / line-free channels used in split
- tclean image size, cell size, masking, niter/threshold
- Number of channels and velocity width for CO imaging; clean threshold
- Which sources used elliptical Gaussian beyond the three named, and uvmodelfit starting guesses
- Stacking procedure details (weights, positions)
- Kaplan-Meier details and two-sample test on dust mass (statistic/p-value for Upper Sco comparison not given)
- Curve-of-growth aperture sizes

## Analysis recipe

1. **Define sample and remove interlopers**: Spitzer disk census minus debris disks; remove Gaia DR2 background sources and non-member  
  > "We therefore remove five sources (LO 1310, 2357, 2404, 5042, and 7517) from our sample" (3.1 Disk Sample Selection)
   - parameter: Gaia DR2 lower distance bound >480 pc  
  > "the lower bounds of their estimated Gaia DR2 distances from Bailer-Jones et al. (2018) are >480 pc" (3.1 Disk Sample Selection)
   - fitting: _not stated_
   - validation: _not stated_
2. **Estimate stellar masses**: Spectral type and J-band to HR diagram, compare to Baraffe et al. 2015 (Siess et al. 2000 for HD 245185)  
  > "Estimates of M ⋆ are then found by comparing the positions on the HR diagram to the evolutionary models of Baraffe et al. (2015)." (3.2 Host Star Properties)
   - assumption: distance 400 pc  
  > "We therefore adopt a distance of 400 pc for λ Orionis in the remainder of this work." (3.2 Host Star Properties)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure continuum flux densities**: split + tclean images; uvmodelfit point source (or elliptical Gaussian for 3 resolved); errors rescaled to reduced chi2=1; stack non-detections  
  > "we measure continuum flux densities by fitting point source models to the visibility data with the uvmodelfit task in CASA ." (4.2 ALMA Continuum Results)
   - software: CASA
   - parameter: non-detections: position offsets fixed to zero  
  > "For the non-detections, we fix ∆ α and ∆ δ to zero when running uvmodelfit to avoid spurious detections" (4.2 ALMA Continuum Results)
   - parameter: resolved if a/σ_a > 5  
  > "We conservatively identify resolved sources as those where the ratio of a to its uncertainty is greater than five." (4.2 ALMA Continuum Results)
   - fitting: uvmodelfit least squares; uncertainties multiplied (typically x2) to give reduced chi2 of 1  
  > "we multiply the uncertainties on all the fitted parameters by the factor needed to produce a reduced χ 2 of 1 (typically a factor of two)" (4.2 ALMA Continuum Results)
   - validation: stacked mean compared to mean of Table 2 fluxes  
  > "We verify this result by calculating the mean continuum flux density and standard error on the mean for the 30 non-detections" (4.2 ALMA Continuum Results)
4. **Search for and measure 12CO**: uvcontsub, spectrum extraction (>3x channel rms), tclean, zero-moment ±3 km/s, curve-of-growth photometry  
  > "Zero-moment maps are then created by summing the channels ± 3 km s −1 from the systemic velocity unless clear emission was seen beyond these limits." (4.3 ALMA CO Results)
   - software: CASA
   - assumption: cluster v_LSR 12 km/s if source value unknown  
  > "else from the average v LSR of the cluster (12 km s −1 ; Kounkel et al. 2018)" (4.3 ALMA CO Results)
   - fitting: _not stated_
   - validation: errors from random same-size apertures; visual inspection of candidates  
  > "with errors ( E 12CO ) estimated by taking the standard deviation of fluxes measured within the same-sized aperture placed randomly within the field of view but away from the source." (4.3 ALMA CO Results)
5. **Derive dust masses**: optically thin isothermal relation M_dust ≈ 4.1 × F_1.25mm (M_earth, mJy)  
  > "where M dust is in Earth masses and F 1.25mm is in mJy." (5.1 Dust Masses)
   - parameter: kappa = 2.3 cm2/g at 230 GHz, beta_d = 1.0  
  > "We take the dust grain opacity, κ ν, as 2.3 cm 2 g −1 at 230 GHz and use an opacity power-law index of β d = 1.0" (5.1 Dust Masses)
   - assumption: T_dust = 20 K, d = 400 pc, optically thin  
  > "Here we use B ν ( T dust ) as the Planck function for a characteristic dust temperature of T dust = 20 K" (5.1 Dust Masses)
   - assumption: gas-to-dust ratio 100 for disk mass  
  > "assuming a gas-to-dust ratio of 100" (Figure 7 caption)
   - fitting: _not stated_
   - validation: alternative T_dust scaling from Andrews et al. 2013 considered for HD 245185 but not adopted  
  > "We do not use this scaling, however, as it remains uncertain whether such a clear relationship holds in the real disk population." (5.3 HD 245185)
6. **Compare dust-mass distributions with other regions**: Kaplan-Meier cumulative distributions; T-test and Wilcoxon rank-sum on stellar masses vs Upper Sco  
  > "The cumulative distributions are constructed using the Kaplan-Meier Estimator (with the Python lifelines package; Davidson-Pilon et al. 2020) to account for upper limits" (5.2 Comparisons to Other Regions)
   - software: lifelines, scipy.stats
   - assumption: Gaia DR2 distances ~150 pc (Lupus, Upper Sco), ~400 pc (σ Ori, OMC-2)  
  > "typical Gaia DR2 distances of ∼ 150 pc for Lupus and Upper Sco and ∼ 400 pc for σ Orionis and OMC-2" (5.2 Comparisons to Other Regions)
   - fitting: _not stated_
   - validation: stellar mass populations tested to be from same parent  
  > "we find p -values of 0.77 and 0.11 for the T-test and Wilcoxon rank-sum test, respectively" (5.2 Comparisons to Other Regions)

## Software

- **CASA** 5.4.0: pipeline calibration, split, tclean, uvmodelfit, uvcontsub  
  > "fitting point source models to the visibility data with the uvmodelfit task in CASA" (4.2. ALMA Continuum Results)
- **lifelines** v0.24.15: Kaplan-Meier estimator  
  > "with the Python lifelines package; Davidson-Pilon et al. 2020" (5.2 Comparisons to Other Regions)
- **scipy.stats** : T-test and Wilcoxon rank-sum test  
  > "(calculated with scipy.stats in Python)" (5.2 Comparisons to Other Regions)
- **astropy** : listed in software  
  > "Software: astropy (Astropy Collaboration et al. 2013, 2018)" (Acknowledgments)
- **ASURV** : listed in software (survival analysis)  
  > "ASURV (Lavalley et al. 1992)" (Acknowledgments)
- **matplotlib** : listed in software (plotting)  
  > "matplotlib (Hunter 2007)" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum detections | 14 of 44 | not stated | sources | 3 | Only 14 of the 44 sources are detected at ≥ 3 σ significance and only 3 of the detections are marginally resolved. |
| Median continuum rms | 34 | not stated | µJy | 3 | This results in a median continuum rms of 34 µJy |
| Stacked flux of 30 non-detections | 0.019 | 0.006 | mJy | 3 | finding a tentative detection of 0.019 ± 0.006 mJy (3.2 σ) in the stacked image |
| 12CO detections | 5 | not stated | sources | 4 | Only five sources (HD 245185, LO 4155, LO 4187, LO 4407, LO 6866) are detected |
| HD 245185 1.25 mm flux | 33.955 | 0.056 | mJy | 3 | HD 245185 33.955 ± 0.056 1915 ± 51 |
| Median dust mass of detections | ~2 | not stated | M_earth | 5 | the median M dust of the continuum detections in our λ Orionis survey is only ∼ 2 M ⊕ . |
| Median 3σ dust mass upper limit | ~0.4 | not stated | M_earth | 5 | median 3 σ upper limit of ∼ 0.4 M ⊕ for the individual non-detections |
| HD 245185 dust mass | ≈140 | not stated | M_earth | 5 | Equation 1 yields M dust ≈ 140 M ⊕ |
| Stellar mass test p-values vs Upper Sco | 0.77 (T-test), 0.11 (Wilcoxon) | not stated | dimensionless | 6 | we find p -values of 0.77 and 0.11 for the T-test and Wilcoxon rank-sum test, respectively |

## Qualitative findings

- λ Orionis dust mass distribution follows the age decline and is statistically indistinguishable from Upper Sco  
  > "the M dust distribution in λ Orionis is statistically indistinguishable from that of the similarly aged Upper Sco association" (5.2 Comparisons to Other Regions)
- No detected disks within 0.3 pc of cluster core; four non-detections there  
  > "we observe but do not detect four disks with projected separations < 0.3 pc from the cluster core" (6.1 Do Supernovae Impact Planet Formation?)

## Claim tuples

- H: Did a supernova/pre-supernova feedback significantly reduce disk dust mass in λ Orionis? | E: Compared Kaplan-Meier dust mass distribution to other regions, especially Upper Sco | R: Distribution follows age decline and matches Upper Sco | F: Massive-star feedback does not significantly reduce planet-forming material beyond expectation, except possibly very close to the supernova | **supported**
- H: Is CO non-detection due to gas dispersal or CO chemical processing from enhanced cosmic rays? | E: 12CO vs continuum flux compared to Lupus and σ Ori | R: CO detections follow the linear correlation; non-detections consistent with weak continuum | F: No clear chemical signature of supernova; sample too small to distinguish | **partially**
- H: Why do massive outlier disks persist in evolved regions? | E: Compared upper dust mass distributions and literature on outlier disks | R: Outlier disks in evolved regions show evidence of companions | F: Companions may extend primordial disk lifetimes (speculative) | **partially**

## Reasoning

- Why this data: ALMA sensitivity needed to reach dust masses comparable to nearby-region surveys  
  > "chosen so the 3 σ dust mass constraints would be comparable to the limits reached in the ALMA surveys of more nearby SFRs" (4.1 ALMA Observations)
- Why this method: _not stated_
- Alternative: Temperature scaling T_dust = 25 K (L/Lsun)^0.25 not adopted  
  > "We do not use this scaling, however, as it remains uncertain whether such a clear relationship holds in the real disk population." (5.3 HD 245185)
- How they decided it was enough: _not stated_
- Limitation (authors): Sample based on Spitzer may be incomplete  
  > "making it possible that our ALMA sample based solely on Spitzer data is incomplete" (3.1 Disk Sample Selection)
- Limitation (authors): Dust masses may be underestimated if optically thick or colder than 20 K  
  > "These dust masses may be underestimated, however, if the observed millimeter continuum emission is (partially) optically thick" (5.1 Dust Masses)
- Caveat (inferred, ours): Supernova occurrence is assumed, not demonstrated; comparison with Upper Sco is confounded by a possible supernova there
- Caveat (inferred, ours): Single-band, unresolved continuum with fixed T_dust and opacity
- Caveat (inferred, ours): Only ~6 min per source, so most constraints are upper limits
- Caveat (inferred, ours): Age differences between regions are imprecise

## Reproducibility

- Data public (paper): ALMA data cited with project codes (acknowledgments); public status not explicitly stated  
  > "This work makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00466.S and #2016.1.00447.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: tclean parameters (imaging size, cell, masks, continuum channels)
- Missing: Role of project 2016.1.00447.S not described in text
- Missing: Exact Kaplan-Meier comparison test results for dust masses
- Data volume (inferred): ~100-300 GB raw for 13 execution blocks; pipeline products smaller
- Score (inferred): 3/5, Recipe is simple (point-source fits, standard dust mass formula) and data are ALMA archive, but imaging settings are partly unspecified.
- Rediscovery candidate: yes, Public ALMA data, simple numeric recipe (fluxes, dust masses), though some imaging details are missing.

## Links

- Method: Ansdell et al. (2017) (CO search procedure and stellar mass method)
- Method: Hildebrand (1983) (dust mass relation)
- Companion: Ansdell et al. (2015) (previous JCMT/SCUBA-2 partial survey of λ Orionis)
- Related: ALMA surveys of Lupus, σ Orionis, Upper Sco, Chamaeleon I, ρ Ophiuchus, OMC-2

## Checks

```json
{
 "quotes": 85,
 "quotes_ok": 85,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 91,
  "stated": 66,
  "rate": 0.725
 },
 "evidence_ok": true
}
```
