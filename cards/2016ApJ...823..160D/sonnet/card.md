# An ALMA Search for Substructure, Fragmentation, and Hidden Protostars in Starless Cores in Chamaeleon I

`2016ApJ...823..160D` | The Astrophysical Journal 2016 | first author: Dunham, Michael M. | arXiv: 1604.04027 | DOI: 10.3847/0004-637X/823/2/160

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Do starless cores in Chamaeleon I show substructure/fragmentation or hide protostars undetected by Spitzer+Herschel, and is the protostar census complete?  
  > "We show that the *Spitzer*+*Herschel* census of protostars in Chamaeleon I is complete" (abstract)
- Target **Chamaeleon I dense cores (73 LABOCA-selected pointings, CHAI-xx)**: coordinates phase centers listed per source in Table 1 (e.g. CHAI-01 11:08:03.22 -77:39:17.9)  
  > "the Chamaeleon I molecular cloud, which is located at a distance of 150 pc (cite: belloche2011:chami)" (1.3 An ALMA Survey of Chamaeleon I); z/distance 150 pc  
  > "the Chamaeleon I molecular cloud, which is located at a distance of 150 pc (cite: belloche2011:chami)" (1.3 An ALMA Survey of Chamaeleon I); distance from Belloche et al. 2011 (cite: belloche2011:chami)  
  > "the Chamaeleon I molecular cloud, which is located at a distance of 150 pc (cite: belloche2011:chami)" (1.3 An ALMA Survey of Chamaeleon I)

## Data provenance

- ALMA projects: 2012.1.00031.S
- bands: Band 3 (106 GHz; 2.8 mm), Cycle 1  
  > "we present the results of a Band 3 (106 GHz; 2.8 mm) ALMA Cycle 1 survey" (1.3 An ALMA Survey of Chamaeleon I)
- frequencies and spectral setup: three 2 GHz continuum windows at 101, 103, 114 GHz; fourth window on 12CO(1-0) at 115 GHz (not presented)  
  > "Three out of the four available spectral windows were configured to measure the continuum at 101, 103, and 114 GHz, each with a bandwidth of 2 GHz" (2 Observations)
- continuum bandwidth: 6 GHz total  
  > "for a total continuum bandwidth of 6 GHz (2.8 mm) at a central frequency of 106 GHz" (2 Observations)
- arrays: _not stated_
- configurations: relatively compact configuration, 25-27 antennas  
  > "Between 25 and 27 antennas were available for our observations, with the array configured in a relatively compact configuration" (2 Observations)
- baselines: _not stated_
- angular resolution: ~2'' FWHM (300 AU)  
  > "to provide a resolution of approximately 2$''$ FWHM (300 AU at the distance to Chamaeleon I)" (2 Observations)
- max recoverable scale: ~25''  
  > "The maximum angular scale that can be recovered in these ALMA data is $\sim$25$''$." (2 Observations)
- sensitivity: ~0.1 mJy/beam 1σ rms (0.08-0.14)  
  > "These continuum observations achieved a 1$\sigma$ rms noise of approximately 0.1 mJy beam$^{-1}$." (2 Observations)
- time on source: ~1 minute per target  
  > "Each target was observed in a single pointing with approximately 1 minute of on-source integration time." (2 Observations)
- observing dates: 2013 Nov 29 to 2014 Mar 08  
  > "between 2013 November 29 and 2014 March 08" (2 Observations)
- pi or archival as stated: _not stated_
- Other facility **APEX LABOCA 870 um**: target core catalog (Belloche et al. 2011)  
  > "We target all 73 sources detected by (cite: belloche2011:chami) in a single-dish 870 $\mu$m continuum survey" (1.3 An ALMA Survey of Chamaeleon I)
- Other facility **Herschel Gould Belt survey**: 70 um images and YSO catalog for associations/SEDs  
  > "Figure [2](#fig_herschel) shows images of each detected source overlaid with contours of the *Herschel* 70 $\mu$m emission from the Gould Belt survey" (3.1)
- Other facility **Spitzer / 2MASS**: protostar catalog and photometry for SEDs  
  > "constructed from 2MASS$+$*Spitzer*, *Herschel*, and LABOCA photometry" (3.1)
- External data: LABOCA core catalog, positions, masses, peak densities  
  > "the phase center of our ALMA observations (taken directly from the core positions given by Belloche et al.)" (2 Observations) [from Belloche et al. 2011 (cite: belloche2011:chami)]
- External data: Herschel YSO catalog and classes  
  > "list the YSO from (cite: winston2012:chami) associated with each detected source" (3.2.2) [from (cite: winston2012:chami)]
- External data: Spitzer protostar compilation  
  > "list the associated protostar from the (cite: dunham2013:luminosities) compilation of protostars detected by *Spitzer*" (3.2.3) [from (cite: dunham2013:luminosities)]
- External data: Peak intensities of Perseus candidate FHSCs  
  > "Peak Flux Densities of Candidate First Hydrostatic Cores in Perseus" (Table 5) [from chen2010:fhsc; schnee2010:starless; dunham2011:fhsc; pineda2011:fhsc]
- External data: OH5 dust opacity kappa=0.23 cm2/g at 106 GHz  
  > "We adopt the dust opacities of (cite: ossenkopf1994:oh5) appropriate for thin ice mantles" (3.1) [from (cite: ossenkopf1994:oh5)]
- Simulation/model as data: Two orion AMR MHD simulations of collapsing starless cores (C04: 0.4 Msun; C4: 4 Msun) and Bonnor-Ebert sphere models via RADMC-3D, turned into synthetic ALMA observations  
  > "We perform two magneto-hydrodynamic (MHD) simulations of isolated, collapsing starless cores." (5.1.1)

## Processing

### Calibration

- pipeline or manual: CASA, standard routines of Petry et al. 2014 and Schnee et al. 2014  
  > "following the standard routines described in (cite: petry2014:alma) and (cite: schnee2014:alma)" (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: two rounds (phase-only, then amplitude+phase) on sources brighter than ~3 mJy  
  > "two rounds of self-calibration, the first phase-only and the second with amplitude and phase corrections" (2 Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.25''  
  > "With a pixel size of 0.25$''$" (3.1)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: flux measurements on primary-beam-corrected images  
  > "All measurements were made on images corrected for primary beam attenuation." (3.1)
- array combination: overlapping fields mosaicked  
  > "Overlapping fields were mosaiced together." (2 Observations)
- smoothing: _not stated_
- final beam: ~2.5-2.7'' x 1.8-1.9'' (Table 1)  
  > "CHAI-01 | 11:08:03.22 | $-$77:39:17.9 | $2.72 \times 1.89$" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Calibration and imaging follow standard CASA routines  
  > "following the standard routines described in (cite: petry2014:alma) and (cite: schnee2014:alma)" (2 Observations) [from (cite: petry2014:alma); (cite: schnee2014:alma)]
- Detection association radius 10.6'' (LABOCA half-power radius)  
  > "within a projected separation of 10.6$''$ (cite: belloche2011:chami)" (3.2.1) [from (cite: belloche2011:chami)]

### Not stated but needed to reproduce (our reading)

- robust/weighting, deconvolver, clean threshold and masks for the real data
- flux calibrator and flux scale uncertainty, CASA version
- primary beam correction and mosaic details
- how the 5-sigma limit and rms per field were measured
- orion simulation snapshots and initial setup files (not released)
- how orientation averaging gave 'at least two' detections

## Analysis recipe

1. **Detect and measure continuum sources**: imfit elliptical Gaussian fits to primary-beam-corrected images; 5 sigma detection threshold  
  > "results from an elliptical Gaussian fit to each source using the imfit task in CASA" (3.1)
   - software: CASA
   - parameter: 5 sigma minimum significance  
  > "we thus adopt 5$\sigma$ as the minimum significance required for detection in this paper." (3.1)
   - fitting: _not stated_
   - validation: Gaussian statistics: >500 pixels above 3 sigma but <1 above 5 sigma from noise  
  > "Gaussian statistics predict over 500 pixels above 3$\sigma$ simply due to random noise, but $<$1 above 5$\sigma$." (3.1)
2. **Derive masses and densities**: M = 100 d^2 S/(B(T_D) kappa); n = 3M/(4 pi mu m_H r_eff^3)  
  > "$$\begin{equation}
\label{eq_dustmass}
M = 100 \frac{d^2 S_{\nu}}{B_{\nu}(T_D) \kappa_{\nu}} \quad ,
\end{equation}$$" (3.1)
   - parameter: T_D = 10 K, d = 150 pc, kappa=0.23 cm2/g, mu=2.37  
  > "With the integrated flux densities listed in Table [2](#tab_continuum) and an assumed $T_D = 10$ K" (3.1)
   - assumption: gas-to-dust ratio 100, OH5 dust, optically thin isothermal dust  
  > "the factor of 100 is the assumed gas-to-dust ratio" (3.1)
   - fitting: _not stated_
   - validation: discussed that T and opacity dominate uncertainty (factor 2 in T gives factor 2 in mass)  
  > "a factor of two uncertainty in dust temperature directly translates into a factor of two uncertainty in mass" (3.1)
3. **Classify evolutionary status via multiwavelength associations and SEDs**: cross-match ALMA detections with LABOCA, Herschel, Spitzer catalogs; SEDs to assign protostellar/starless/disk  
  > "we classify these objects as disks rather than starless or protostellar dense cores" (3.3)
   - fitting: _not stated_
   - validation: _not stated_
4. **Test census completeness**: scale peak intensities of four Perseus faint protostars to 150 pc and 106 GHz with I ∝ nu^(2+beta), 0<=beta<=2, compare to rms  
  > "assuming $I_{\nu} \propto \nu^{2+\beta}$" (4)
   - assumption: same dust temperatures in Chamaeleon I as in Perseus; emission compact/unresolved  
  > "The sources are assumed to have the same dust temperatures in Chamaeleon I as in Perseus" (4)
   - fitting: _not stated_
   - validation: _not stated_
5. **Synthetic ALMA observations of simulated cores and BE spheres**: convert column density to 106 GHz maps with BE-derived T(N) and OH5 opacity; simobserve/simanalyze with alma.cycle1.3.cfg, 72 s, 6 GHz; clean to 0.3 mJy  
  > "We then generate synthetic ALMA observations of these simulated 106 GHz continuum intensity maps using the CASA tasks simobserve and simanalyze." (5.1.2)
   - software: CASA, orion, RADMC-3D
   - parameter: cloud background A_V=35.6 added; pixel 20 AU; distance 150 pc  
  > "adopting a value of $\Sigma$ representing the maximum visual extinction toward the Chamaeleon I cloud of $A_{V} = 35.6$" (5.1.2)
   - fitting: _not stated_
   - validation: BE temperature profiles agree with Evans et al. 2001; background offset test gave identical results  
  > "calculated by RADMC-3D and agree with those calculated by (cite: evans2001:starless)" (Appendix A)
6. **Predict expected detections and Poisson probability**: Detections > N_total (n_Detectable/n_Limit)^-0.5 with tau ∝ n^-0.5, then Poisson probability of zero  
  > "Equation [\[eq_detect2\]](#eq_detect2) results in a total of at least three expected detections." (5.2)
   - parameter: N_total=56, n_Detectable=8.9e7 cm-3, n_Limit>2.8e5 cm-3  
  > "With N$_{\rm total} = 56$, n$_{\rm Detectable} = 8.9 \times 10^7$ cm$^{-3}$, and n$_{\rm Limit} > 2.8 \times 10^5$ cm$^{-3}$" (5.2)
   - assumption: continuous star formation; free-fall evolution; simulations applicable  
  > "(1) starless cores evolve on timescales proportional to the free-fall time, (2) star formation is continuous in Chamaeleon I, and (3) the simulations are applicable" (5.3)
   - fitting: power-law fits of lifetime vs central density  
  > "with a power-law fit giving $\tau~\propto~n^{-0.50 \pm 0.01}$" (5.3.1)
   - validation: _not stated_

## Software

- **CASA** : calibration, imaging, imfit, simobserve/simanalyze  
  > "The calibration and imaging were done using the Common Astronomy Software Applications (CASA) package" (2 Observations)
- **orion** : AMR MHD simulations of collapsing cores  
  > "We use the orion Adaptive Mesh Refinement (AMR) code" (5.1.1)
- **RADMC-3D** : BE sphere temperature profiles and 106 GHz model images  
  > "We then solved for the temperature profiles in each BE sphere using the three-dimensional Monte Carlo radiative transfer package RADMC-3D" (Appendix A)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| continuum sources detected at >=5 sigma | 24 sources in 19 fields | not stated | sources | 1 | We detect a total of 24 106 GHz continuum sources to 5$\sigma$ or greater significance in 19 different target fields |
| starless cores, all undetected | 56 | not stated | cores | 3 | leaving us with 56 starless cores, none of which are detected by our ALMA continuum observations |
| misclassification rate of protostellar cores as starless | <1/56 (<2%) | not stated | dimensionless | 4 | the rate at which protostellar cores in Chamaeleon I have been misclassified as starless cores is $<$1/56, or $<$ 2% |
| detected masses range | 0.012 to 1.7 | statistical only | Msun | 2 | gives total masses ranging from 0.012 M$_\odot$ to 1.7 M$_\odot$ |
| C04 detection threshold central density | 8.9e7 | not stated | cm-3 | 5 | The C04 simulation is detected over the last 8200 yr of the starless stage, when the central number density exceeds $8.9 \times 10^{7}$ cm$^{-3}$. |
| C4 detection threshold central density | 3.3e7 | not stated | cm-3 | 5 | The C4 simulation is detected over the last 11000 yr of the starless stage, when the central number density exceeds $3.3 \times 10^{7}$ cm$^{-3}$. |
| expected detections (orientation averaged) | at least 2 | not stated | cores | 6 | the total number of expected detections is reduced from at least three to at least two |
| Poisson probability of zero detections | 13.5 | not stated | percent | 6 | the probability of detecting zero cores when two detections are expected is 13.5% |
| C04 lifetime-density index | -0.50 | 0.01 | dimensionless | 6 | with a power-law fit giving $\tau~\propto~n^{-0.50 \pm 0.01}$ |

## Qualitative findings

- All known Class 0 and I protostars detected; other detections are Flat/Class II objects  
  > "All previously known Class 0 and Class I protostars in Chamaeleon I are detected in our continuum observations." (6 Summary)
- Bonnor-Ebert spheres remain undetected to central densities of at least 1e10 cm-3  
  > "there are no 5$\sigma$ detections, not even for the $n_c = 10^{10}$ cm$^{-3}$ model" (Appendix A)

## Claim tuples

- H: Are Spitzer+Herschel protostar censuses of Cha I complete? | E: Scale Perseus faint protostars to Cha I and compare with ALMA rms | R: predicted peaks 0.7-17.7 mJy/beam vs rms 0.08-0.14 | F: census complete; misclassification <2% | **supported**
- H: Do starless cores show turbulent-fragmentation substructure? | E: Synthetic ALMA observations of MHD simulations vs 56 non-detections | R: at least 2 detections expected, 0 observed (13.5% chance) | F: likely declining star formation / non-collapsing cores, or less-substructured models like BE spheres; cannot distinguish | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: ALMA sensitivity can detect substructure in starless cores that CARMA could not  
  > "These same synthetic observations have shown that the Atacama Large Millimeter/submillimeter Array (ALMA) is capable of detecting substructure and fragmentation in starless cores" (1.1)
- Alternative: Protostars viewed face-on rejected as explanation for Class II SEDs (no double-peaked SEDs)  
  > "such objects tend to feature double-peaked SEDs (cite: whitney2003:geometry1) not seen in Figure [3](#fig_seds)" (3.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass uncertainties dominated by dust temperature and opacity assumptions  
  > "The true uncertainties are likely dominated by the dust temperature and opacity assumptions." (3.1)
- Limitation (authors): Only two simulations; full parameter space needed  
  > "a full parameter space exploration is required" (5.3.3)
- Caveat (inferred, ours): Non-detections rely on an assumed temperature model (4-5 K centers); a 7 K floor changes thresholds by a factor of ~3
- Caveat (inferred, ours): Few simulations, one magnetic setup
- Caveat (inferred, ours): Imaging parameters of real data not given

## Reproducibility

- Data public (paper): ALMA project data cited; archive code given  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA# 2012.1.00031.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: clean parameters
- Missing: simulation snapshots
- Missing: CASA version
- Missing: flux calibration details
- Data volume (inferred): ~50-100 GB raw visibilities for 73 short pointings
- Score (inferred): 3/5, Data public and photometric results are simple, but imaging settings and simulation inputs are unstated.
- Rediscovery candidate: yes, Public data and numeric detections/flux densities with a simple mass formula; synthetic part is harder.

## Links

- Method: (cite: petry2014:alma) (standard CASA calibration/imaging routines)
- Method: (cite: schnee2014:alma) (standard CASA calibration/imaging routines)
- Companion: (cite: belloche2011:chami) (LABOCA parent catalog)
- Companion: (cite: offner2010:turbfrag) (turbulent fragmentation simulations revisited)
- Related: APEX LABOCA survey of Chamaeleon I
- Related: Herschel Gould Belt survey
- Related: Spitzer c2d and Gould Belt surveys

## Checks

```json
{
 "quotes": 70,
 "quotes_ok": 70,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 57,
  "rate": 0.655
 },
 "evidence_ok": true
}
```
