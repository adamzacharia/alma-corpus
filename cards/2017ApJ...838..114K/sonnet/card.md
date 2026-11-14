# ALMA Observations of Starless Core Substructure in Ophiuchus

`2017ApJ...838..114K` | The Astrophysical Journal 2017 | first author: Kirk, H. | arXiv: 1703.00506 | DOI: 10.3847/1538-4357/aa63f8

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Do starless cores in Ophiuchus show compact substructure in ALMA Band 3 continuum, and is the number of detections consistent with turbulent fragmentation predictions (vs Chamaeleon I)?  
  > "The number of our detections is consistent with estimates from a combination of synthetic observations of numerical simulations and analytical arguments." (abstract)
- Target **Ophiuchus dense cores (66 SCUBA cores; 60 after removing spurious)**: coordinates not stated (per-source coordinates in Table 2)  
  > "We assume a slightly warmer dust temperature for Ophiuchus than assumed for Chamaeleon I (15 K versus 10 K), based on the NH$_3$ results of (cite: Friesen09), and a distance of 140 pc." (3.2 Mass Estimates); "Ophiuchus is one of the nearest molecular clouds, at only $\sim$140 pc (cite: OrtizLeon17), similar to Chamaeleon." (1 Introduction); z/distance ~140 pc  
  > "We assume a slightly warmer dust temperature for Ophiuchus than assumed for Chamaeleon I (15 K versus 10 K), based on the NH$_3$ results of (cite: Friesen09), and a distance of 140 pc." (3.2 Mass Estimates); "Ophiuchus is one of the nearest molecular clouds, at only $\sim$140 pc (cite: OrtizLeon17), similar to Chamaeleon." (1 Introduction); distance from Ortiz-León et al. (OrtizLeon17)  
  > "We assume a slightly warmer dust temperature for Ophiuchus than assumed for Chamaeleon I (15 K versus 10 K), based on the NH$_3$ results of (cite: Friesen09), and a distance of 140 pc." (3.2 Mass Estimates); "Ophiuchus is one of the nearest molecular clouds, at only $\sim$140 pc (cite: OrtizLeon17), similar to Chamaeleon." (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.00187.S
- bands: Band 3, Cycle 2; continuum effective mean frequency 107 GHz  
  > "The ALMA Band 3 data were observed during Cycle 2 on 31 January, 2015 with 37 antennas." (2.2 ALMA Data)
- frequencies and spectral setup: Three continuum SPWs at 101, 103, 113 GHz (2 GHz each); one SPW for 12CO(1-0) at 115 GHz  
  > "Three of the four spectral windows available were configured for continuum measurements at 101 GHz, 103 GHz, and 113 GHz, each covering a bandwidth of 2 GHz, and giving an effective mean frequency of 107 GHz." (2.2 ALMA Data)
- continuum bandwidth: _not stated_
- arrays: 12 m array only, no ACA or total power  
  > "Only the 12 m array was used, i.e., no compact array or total power observations were included." (2.2 ALMA Data)
- configurations: _not stated_
- baselines: ~15 m to 350 m  
  > "Antenna separations ranged from $\sim$15 m to 350 m." (2.2 ALMA Data)
- angular resolution: median beam 3.5" x 1.8", PA 71 deg  
  > "with a median synthesized beam of $3.5 \ensuremath{''} \times 1.8\ensuremath{''}$ at a position angle of 71$^o$" (2.2 ALMA Data)
- max recoverable scale: ~23"  
  > "a maximum recoverable scale of $\sim$23$''$" (2.2 ALMA Data)
- sensitivity: ~0.16 mJy/beam continuum rms  
  > "The noise level of the continuum observations about the phase centres is roughly 0.16 mJy beam$^{-1}$." (2.2 ALMA Data)
- time on source: two observations per core, ~1 minute on-source  
  > "Each core was observed twice with a single pointing using roughly 1 minute of on-source integration time." (2.2 ALMA Data)
- observing dates: 31 January 2015  
  > "The ALMA Band 3 data were observed during Cycle 2 on 31 January, 2015 with 37 antennas." (2.2 ALMA Data)
- pi or archival as stated: _not stated_
- Line: 12CO 1-0 (115 GHz)
- Other facility **Spitzer**: YSO catalogue (Dunham15) used to classify cores and associate detections  
  > "We use the updated *Spitzer* YSO catalogue of (cite: Dunham15) for this determination" (2.1 Target Selection: SCUBA)
- Other facility **SCUBA / JCMT**: 850 um core catalogue (Jorgensen08) for target selection; SCUBA-2 map (Pattle15) for comparison  
  > "(cite: Jorgensen08) identified 66 dense cores in the Ophiuchus molecular cloud." (2.1 Target Selection: SCUBA)
- Other facility **Herschel**: 70 and 100 um images to search for protostellar counterparts  
  > "We first searched for signs of compact protostellar emission in *Herschel* 70 $\mu$m and 100 $\mu$m observations of Ophiuchus" (3.3.1 Herschel)
- External data: Core catalogue incl. central concentrations from SCUBA 850 um  
  > "Central concentration of each core as reported in (cite: Jorgensen08)." (Table 1 notes) [from (cite: Jorgensen08)]
- External data: Spitzer YSO catalogue and classes  
  > "Protostellar class based on the *Spitzer* catalogue of (cite: Dunham15)." (Table 1 notes) [from (cite: Dunham15)]
- External data: Dust opacity 0.23 cm2/g at 107 GHz (OH5)  
  > "which corresponds to the OH5 model of (cite: Ossenkopf94)" (3.2 Mass Estimates) [from (cite: Ossenkopf94)]
- Simulation/model as data: Orion AMR simulation of 0.4 Msun turbulent magnetized core, re-observed synthetically with simobserve/simanalyze  
  > "Similar to the synthetic observations generated by , the synthetic observations were generated using the CASA tasks simobserve and simanalyze." (5 Substructure from Turbulent Fragmentation)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline-calibrated data; manual phase and amplitude self-calibration for bright fields  
  > "For fields where a bright enough source was detected, we manually self-calibrated the data in both phase and amplitude using the Common Astronomy Software Applications (CASA) package" (2.2 ALMA Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Used pipeline calibrated data for Cycle 2  
  > "We used the pipeline calibrated data available for Cycle 2 data (cite: Shinnaga15)." (2.2 ALMA Data)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: phase and amplitude self-cal, ≤10% rms improvement  
  > "In nearly all cases, self-calibration gave only a modest (ten percent or less) improvement on the rms noise level in the final image." (2.2 ALMA Data)

### Imaging

- task: interactive clean in CASA with manual clean boxes  
  > "we then imaged the data using manually defined clean boxes in an interactive clean session" (2.2 ALMA Data)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: manually defined clean boxes  
  > "we then imaged the data using manually defined clean boxes in an interactive clean session" (2.2 ALMA Data)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Applied before Gaussian fitting; rms measured on non-PB-corrected image  
  > "After correcting for the primary beam, we use CASA’s *imfit* package to fit two-dimensional Gaussians" (3 Detections)
- array combination: Overlapping fields mosaicked  
  > "In these cases, we mosaicked the fields together to improve the final sensitivity." (2.2 ALMA Data)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 0.097-0.827 mJy/beam per field (Table 1), typically ~0.16  
  > "| 163223-24284 | 0.827 | – | 0+I | 0.94 |" (Table 1)

### Inherited from earlier work

- Observational setup mimics Chamaeleon I ALMA survey  
  > "Our observational setup mimics that described in for their earlier observations in Chamaeleon I." (2.2 ALMA Data) [from Dunham16]
- Dust opacity 0.23 cm2/g at 107 GHz and mean density formula  
  > "Following , we assume $\kappa_{\nu} = 0.23$ cm $^2$g$^{-1}$ at an effective frequency of 107 GHz" (3.2 Mass Estimates) [from Dunham16]
- Expected-detections framework (freefall-time lifetime, factor 2/3) and column density-temperature relation  
  > "we apply the same relationship as in ." (5 Substructure from Turbulent Fragmentation) [from Dunham16]

### Not stated but needed to reproduce (our reading)

- tclean/clean parameters: weighting/robust, cell and image size, threshold, niter
- Self-calibration solution intervals and which fields were self-calibrated
- CASA version and pipeline version
- Flux calibrator and flux scale uncertainty
- Detection threshold / source-finding criteria beyond 'compact sources' (apart from source 37 at 4.9 sigma)
- Which fields were mosaicked in what way (imaging parameters)
- Details of Dunham16 column density-temperature relation and simulation snapshots
- Bandpass/phase calibrators, flagged data fractions

## Analysis recipe

1. **Select and classify targets**: Classify SCUBA cores as protostellar if within 15" of a Spitzer YSO; remove six spurious cores using SCUBA-2  
  > "We apply a simple definition that protostellar dense cores are separated by no more than 15$''$ (i.e., roughly one SCUBA 850 $\mu m$ beam) from one (or more) *Spitzer*-identified YSOs." (2.1 Target Selection: SCUBA)
   - fitting: _not stated_
   - validation: Compared with SCUBA-2 Pattle15 catalogue  
  > "We examined our adopted dense core catalogue using this improved SCUBA-2 dataset." (2.1.1 Comparison of SCUBA and SCUBA-2 data)
2. **Calibrate and image continuum**: Pipeline calibration, optional self-cal, interactive clean, mosaic overlapping fields  
  > "we then imaged the data using manually defined clean boxes in an interactive clean session" (2.2 ALMA Data)
   - software: CASA
   - fitting: _not stated_
   - validation: rms measured with imstat on non-PB-corrected images  
  > "calculated using CASA’s imstat command" (Table 1 notes)
3. **Measure compact source properties**: 2D Gaussian fits to primary-beam-corrected maps; beam-deconvolved sizes  
  > "we use CASA’s *imfit* package to fit two-dimensional Gaussians to all compact sources of emission within the single maps and mosaicked areas." (3 Detections)
   - software: CASA imfit
   - fitting: imfit Gaussian  
  > "After correcting for the primary beam, we use CASA’s *imfit* package to fit two-dimensional Gaussians to all compact sources of emission within the single maps and mosaicked areas." (Detections)
   - validation: _not stated_
4. **Derive masses, radii, densities**: Optically thin dust mass M=100 d^2 S/(B(T)kappa); R_eff geometric mean of deconvolved semi-axes; n from M/R^3 with mu=2.37  
  > "where $\mu = 2.37$ is the mean molecular weight per particle and $m_H$ is the mass of a hydrogen atom." (3.2 Mass Estimates)
   - parameter: kappa=0.23 cm2/g at 107 GHz; T=15 K; d=140 pc; gas-to-dust 100  
  > "the factor of 100 represents the assumed gas-to-dust ratio" (3.2 Mass Estimates)
   - assumption: T=15 K (10 K gives 2x higher masses; 25 K gives ~2x lower)  
  > "A temperature of 10 K would imply masses that are a factor of two higher than what we report." (3.2 Mass Estimates)
   - fitting: _not stated_
   - validation: Systematic uncertainties discussed  
  > "The temperature and dust opacity contribute a factor of several to the uncertainty in the masses we estimate" (3.2 Mass Estimates)
5. **Assess protostellar nature of detections**: Compare with Spitzer YSO separation, Herschel 70/100 um, c2d catalogue, SIMBAD/X-ray, outflow catalogues, quick ALMA CO clean  
  > "We searched through the literature to look for any evidence that the ALMA detections separated by more than 3$''$ from a (cite: Dunham15) *Spitzer* YSO may harbour hidden protostars." (3.3 Unidentified low luminosity protostars)
   - software: CASA clean, SIMBAD
   - fitting: _not stated_
   - validation: Multiple independent lines of evidence  
  > "These results are summarized in Table [2](#tab_detects_pt1), which includes multiple lines of evidence of a protostellar nature where appropriate." (Detections and Protostellar Associations / Summary)
6. **Predict expected starless detections and compare**: Synthetic ALMA observations of 0.4 Msun simulated core at 140 pc with actual antenna configuration; derive detectable density; apply Detections > 2/3 N_total (n_det/n_lim)^-0.5  
  > "We cleaned to a threshold of 0.30 mJy beam$^{-1}$, i.e., approximately 2$\sigma$, using non-interactive cleaning with no clean mask set a priori." (5 Substructure from Turbulent Fragmentation)
   - software: CASA simobserve, CASA simanalyze
   - parameter: 60 s total, 1 s integrations, 107 GHz, 6 GHz bandwidth, phase centre 16:30:00 -24:30:00  
  > "with an effective mean frequency of 107 GHz and bandwidth of 6 GHz." (5 Substructure from Turbulent Fragmentation)
   - assumption: Continuous star formation; core lifetime scales with freefall time  
  > "Under the important assumption that star formation is continuous in the region, with the dense core lifetime at different densities described by the freefall time" (5 Substructure from Turbulent Fragmentation)
   - fitting: _not stated_
   - validation: Poisson statistics of 1 or 2 detections vs expected 2.1  
  > "the chance of having one or two detections is equally likely (27% in both cases)" (5 Substructure from Turbulent Fragmentation)

## Software

- **CASA** : self-calibration, imaging, imstat, imfit, simobserve/simanalyze  
  > "using the Common Astronomy Software Applications (CASA) package" (2.2 ALMA Data)
- **CuTEx** : core-finding in the Pattle15 comparison catalogue (not run by authors)  
  > "(cite: Pattle15) used the core-finding algorithm CuTEx (cite: Molinari11)" (2.1.1 Comparison of SCUBA and SCUBA-2 data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Compact ALMA detections | 38 | not stated | sources | 3 | Table [2](#tab_detects_pt1) lists the the 38 sources detected with ALMA |
| Detections >14" from Spitzer YSO | 8 | not stated | sources | 5 | We detect eight compact substructures which are $>$15$''$ from the nearest *Spitzer* YSO. |
| Source 37 detection significance | 4.9 | not stated | sigma | 3 | which was detected at a level of $4.9~\sigma$ |
| Source 37 mass | 0.0686 | not stated | Msun | 4 | /    37     /    0.0686     / ... /       502       / ... /  1.94E+07   / |
| Detectable central density in synthetic obs | 3.7e7 | not stated | cm^-3 | 6 | when the central density of the core reaches $3.7\times 10^7$ cm$^{-3}$ |
| Expected minimum starless detections | 2.1 | not stated | sources | 6 | we would therefore predict a minimum of 2.1 (two) starless cores to have detectable substructure |
| Median core mass at 140 pc | 0.55 | not stated | Msun | 6 | we find a median core mass of 0.55 M$_{\odot}$ |
| Fraction of detections with companion within 3000 au | 14 of 38 | not stated | sources | 3 | Altogether 14 of our 38 detections, or one third, have a second source with projected distance $\lesssim 3,000$ au. |

## Qualitative findings

- Only source 37 has strong evidence of being starless; extended emission around Oph-SM1N is tentatively starless.  
  > "Only one of these has strong evidence for being truly starless after considering ancillary data" (abstract)
- Starless SCUBA cores with concentration <0.6 were not detected; all four with >0.6 had detections.  
  > "None of the SCUBA starless cores with concentrations below 0.6 were detected with ALMA" (4.1 SCUBA Core Concentration)

## Claim tuples

- H: Ophiuchus starless cores have compact substructure at the rate predicted by turbulent fragmentation simulations | E: ALMA Band 3 survey of 60 cores plus synthetic observations of simulations | R: One strong plus one tentative starless detection vs 2.1 predicted | F: Number of detections consistent with predictions; cores not well described by smooth Bonnor-Ebert spheres | **supported**
- H: The Chamaeleon I null result reflects the peculiar evolutionary state of its cores | E: Compare Ophiuchus detection numbers with Chamaeleon I | R: Ophiuchus detections match expectation while Chamaeleon I had none | F: Lends credence to Chamaeleon I cores being in an unusual evolutionary state | **partially**

## Reasoning

- Why this data: Extend Chamaeleon I ALMA study to a second nearby cloud with identical setup  
  > "The Ophiuchus molecular cloud presents an optimal environment to extend the study." (1 Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): No ACA/total power so extended structure and outflows are filtered; Spitzer catalogue incomplete; mass uncertain by factor of several  
  > "without compact array or total power observations, it may be difficult to identify outflow emision" (3.3.3 ALMA CO)
- Caveat (inferred, ours): Starless classification of source 37 and SM1N rests on non-detection in ancillary data of limited sensitivity
- Caveat (inferred, ours): Expected-detection estimate relies on one simulated 0.4 Msun core and strong assumptions (continuous SF, freefall lifetime)
- Caveat (inferred, ours): Small number statistics (1-2 detections)
- Caveat (inferred, ours): Detection threshold for starless sources not rigorously defined

## Reproducibility

- Data public (paper): ALMA data identified by project code in acknowledgments; SCUBA-2 data programme MJLSG32  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA# 2013.1.00187.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Clean parameters and self-cal details
- Missing: Simulation snapshots and column density-temperature relation
- Missing: Detection criteria
- Data volume (inferred): ~100-300 GB raw for 66 short Band 3 fields; products much smaller
- Score (inferred): 3/5, Public data and simple analysis, but imaging parameters, simulations and detection criteria are underspecified.
- Rediscovery candidate: no, Imaging recipe incomplete and key results depend on simulations not available and classification via multi-wavelength ancillary data.

## Links

- Method: (cite: Dunham16) (Chamaeleon I ALMA survey; setup, mass assumptions and expected-detection framework)
- Companion: (cite: Dunham16) (Chamaeleon I counterpart survey)
- Related: JCMT Gould Belt Survey
- Related: Herschel Gould Belt Survey
- Related: Spitzer c2d

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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 54,
  "rate": 0.675
 },
 "evidence_ok": true
}
```
