# CMZoom. II. Catalog of Compact Submillimeter Dust Continuum Sources in the Milky Way's Central Molecular Zone

`2020ApJS..251...14H` | The Astrophysical Journal Supplement Series 2020 | first author: Hatchfield, H. Perry | arXiv: 2009.05052 | DOI: 10.3847/1538-4365/abb610

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: milky_way_ism, star_formation
- Question: Which compact sources (<10'', ~0.4 pc) exist in the 1.3 mm SMA CMZoom continuum maps of the Central Molecular Zone, what are their properties and completeness, and what do they imply for CMZ star formation potential?  
  > "In this paper we present the *CMZoom* Survey’s catalog of compact sources (\< 10$''$, $\sim$0.4pc) within the Central Molecular Zone (CMZ)." (abstract)
- Target **Central Molecular Zone (CMZoom survey footprint, incl. Sgr B2, Dust Ridge, Brick)**: coordinates l = -0.87 to 1.69 deg, b = -0.25 to 0.07 deg (catalog leaves)  
  > "Galactic Center distance of 8.178 $\pm$ 0.013 (stat.) $\pm$ 0.022 (sys.) kpc" (2 Description of the Data); z/distance 8.178 kpc  
  > "Galactic Center distance of 8.178 $\pm$ 0.013 (stat.) $\pm$ 0.022 (sys.) kpc" (2 Description of the Data); distance from GRAVITY Collaboration 2019  
  > "Galactic Center distance of 8.178 $\pm$ 0.013 (stat.) $\pm$ 0.022 (sys.) kpc" (2 Description of the Data)

## Data provenance

- ALMA projects: 2013.1.00617.S, 2017.1.00687.S, 2018.1.00850.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **SMA (CMZoom)**: 1.3 mm dust continuum maps (compact+subcompact) from which the catalogs are built  
  > "The survey uses the SMA in both its compact and subcompact configurations" (2 Description of the Data)
- Other facility **Herschel**: Column density and dust temperature maps at 36'' used for masses and column density comparison  
  > "These are cloud scale column density measurements at a resolution of 36$''$ (1.5 pc)." (4.2 Comparison with Cloud Scale Column Densities)
- Other facility **ALMA**: Higher-resolution 1.1 mm (Dust Ridge D, E, F) and 3 mm (Sgr B2) maps from other papers, compared by eye to catalog leaves  
  > "we used 1.1mm continuum maps from Dust Ridge clouds D, E, and F (cite: barnes_young_2019), as well as the Sgr B2 complex at 3mm (cite: ginsburg_distributed_2018)." (10 Comparison with Sgr B2 ALMA Data)
- External data: ALMA 1.1 mm maps of Dust Ridge clouds D, E, F  
  > "we used 1.1mm continuum maps from Dust Ridge clouds D, E, and F (cite: barnes_young_2019)" (10 Comparison with Sgr B2 ALMA Data) [from (cite: barnes_young_2019)]
- External data: ALMA 3 mm Sgr B2 continuum maps and HII region identifications  
  > "as well as the Sgr B2 complex at 3mm (cite: ginsburg_distributed_2018)" (10 Comparison with Sgr B2 ALMA Data) [from (cite: ginsburg_distributed_2018)]
- External data: Herschel dust SED column density and temperature maps  
  > "from the *Herschel* property maps created using the dust SED fitting technique detailed in (cite: battersby_characterizing_2011), to be presented in Battersby et al (in preparation)." (4.2 Comparison with Cloud Scale Column Densities) [from (cite: battersby_characterizing_2011); (cite: mills_origins_2017)]
- External data: Gas masses for Sgr B2 North and Main replacing catalog masses in the SFR estimate  
  > "we replace the extreme masses measured in this work (described in Section [\[sec:phys_prop\]](#sec:phys_prop)) for Sgr B2 North and Main with more reliable gas masses derived in (cite: schmiedeke_physical_2016)" (5.2 Maximum Star Formation Potential of the CMZ) [from (cite: schmiedeke_physical_2016)]
- Simulation/model as data: CASA simobserve simulated SMA observations of ten randomly placed point sources, used for completeness and false-positive tests  
  > "An artificial image is randomly populated with ten point-sources at a fixed intensity representing the emission of a field of unresolved core-like objects." (3.2 Source Recovery and Simulated Observations)

## Processing

### Calibration

- pipeline or manual: SMA data calibrated in MIR IDL with standard SMA procedures  
  > "All data were calibrated in MIR IDL using standard SMA calibration procedures" (2 Description of the Data)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean (simulated data); real data imaged with MIR IDL and CASA  
  > "imaging and deconvolution were completed in a combination of MIR IDL and CASA." (2 Description of the Data)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Briggs weighting with a robust parameter of 0.5 was used throughout." (3.2 Source Recovery and Simulated Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: auto-multithresh, continuum threshold 1 mJy/beam  
  > "We used the `auto-multithresh`[^5] feature (with identical input parameters to those detailed in ), and a continuum threshold of 1 mJy beam${-1}$." (3.2 Source Recovery and Simulated Observations)
- multiscale scales: [0, 3, 9, 27]  
  > "The `tclean` task was called with multi-scale parameter set to scales \[0, 3, 9, and 27\]." (3.2 Source Recovery and Simulated Observations)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: SMA-only data used for catalogs (no single-dish feathering)  
  > "For the catalogs created in this work, we used the SMA-only data, as we are interested only in the most compact emission structures." (2 Description of the Data)
- smoothing: _not stated_
- final beam: typical ~3.2'' (0.13 pc)  
  > "we achieve a typical spatial resolution of $~3.2$" (0.13 pc)" (2 Description of the Data)
- final rms: median local RMS 13 MJy/sr; lowest 3 MJy/sr  
  > "We find a median RMS over all surveyed regions is 13 MJy sr$^{-1}$." (3.1 Pruned Dendrogram Algorithm)

### Inherited from earlier work

- Observations, calibration, imaging pipeline, RMS maps and auto-multithresh parameters described in Paper I  
  > "All the *CMZoom* pointings, SMA configurations, and imaging pipeline details are described in more detail in and the data products have been made available" (2 Description of the Data) [from (cite: battersby_cmzoom_2020)]
- Dust opacity kappa0 and beta=1.75, gas-to-dust 100, Herschel SED fitting  
  > "(extrapolating from $\kappa_{0}=0.899$ cm$^{2}$g$^{-1}$ at $\nu_{0}=230$ GHz with $\beta=1.75$; e.g. (cite: battersby_characterizing_2011))" (4.3 Physical properties) [from (cite: battersby_characterizing_2011)]
- Isothermal mass estimate method  
  > "Following the method described in (cite: battersby_infrared_2010), we find an isothermal estimate for the mass of each leaf using" (4.3 Physical properties) [from (cite: battersby_infrared_2010)]

### Not stated but needed to reproduce (our reading)

- Exact dendrogram parameter values in the appendix-referenced setup (min_value, min_npix, min_delta numeric values beyond 3 MJy/sr scaling)
- Access/processing of CMZoom SMA maps from Dataverse versus Paper I imaging details
- Simulated observation antenna configuration, integration time and weather settings
- Herschel temperature map not yet published (in prep.)
- Exact point-source flux values and mass grid used for completeness curve

## Analysis recipe

1. **Build local RMS map**: Spatially averaged standard deviation of clean residual images using Gaussian kernel  
  > "where $R_{x,y}$ corresponds to the residual value at pixel coordinates $(x,y)$, and $\ast G$ denotes convolution with a Gaussian kernel with $\sigma=14$ pixels, or $\sim$ 7$''$." (3.1 Pruned Dendrogram Algorithm)
   - software: CASA
   - parameter: kernel sigma = 14 pixels (~7'')  
  > "Gaussian kernel with $\sigma=14$ pixels, or $\sim$ 7$''$" (3.1 Pruned Dendrogram Algorithm)
   - fitting: _not stated_
   - validation: Kernel size chosen from simulated-observation false-positive parameter study  
  > "We chose to use the 14 pixel kernel as this choice also has a slightly lower average completeness mass." (8 Catalog Parameter Studies)
2. **Run dendrogram and prune leaves by local noise**: Dendrogram on continuum map in MJy/sr, then keep leaves with peak >6 sigma (robust) or >4 sigma (high-completeness) and mean >2 sigma of local RMS  
  > "the former prioritizing only the most robust leaves with a peak flux at least 6$\sigma$ above the local RMS estimate and the latter prioritizing a higher catalog completeness, which includes leaves with a peak flux at least 4$\sigma$ above the local RMS estimate." (3.1 Pruned Dendrogram Algorithm)
   - software: astrodendro
   - parameter: min value = 3x global noise (3 MJy/sr); min pixels ~ half average beam; min significance = global low noise  
  > "The minimum pixel value is chosen to be a factor of three greater than this global noise estimate." (3.1 Pruned Dendrogram Algorithm)
   - fitting: _not stated_
   - validation: Parameter study of delta and kernel in Appendix  
  > "we find that the mass and radius distribution of leaf properties in the catalog is well preserved" (8 Catalog Parameter Studies)
3. **Completeness and false-positive from simulated observations**: Inject 10 point sources, simobserve, tclean, make RMS map, dendrogram and prune, count recovered sources  
  > "A given point-source is considered to be recovered if its coordinates are located anywhere within a pruned leaf." (3.2 Source Recovery and Simulated Observations)
   - software: CASA simobserve, CASA tclean, AATM
   - parameter: masses from flux assuming Td = 20 K  
  > "we assume a constant dust temperature of 20K" (3.2 Source Recovery and Simulated Observations)
   - assumption: Point-source-like emission model  
  > "can be modeled by point-source-like emission for the purposes of this simplistic completeness estimate." (3.2 Source Recovery and Simulated Observations)
   - fitting: _not stated_
   - validation: Completeness resilient to atmospheric variation  
  > "The completeness results for our catalogs constructed from the simulated observations is resilient to variations typical in atmospheric conditions" (3.2 Source Recovery and Simulated Observations)
4. **Derive leaf physical properties**: Reff, optically thin column density, isothermal mass, density and freefall time using Herschel Td  
  > "Assuming optically thin dust continuum emission, the beam-averaged column density at the location of peak emission, $N_{\rm H_{2}}$ is estimated for each dendrogram leaf" (4.3 Physical properties)
   - software: astrodendro
   - parameter: kappa = 0.867 cm2/g at ~226 GHz; d = 8.178 kpc  
  > "At a frequency of $\sim226$ GHz we adopt a value of $\kappa_{\nu}\approx0.867$ cm$^{2}$g$^{-1}$" (4.3 Physical properties)
   - assumption: gas-to-dust 100; mu_H2 = 2.8; beta = 1.75  
  > "$R_{\rm gd}$ is the gas to dust mass ratio (for which we assume a value of 100" (4.3 Physical properties)
   - fitting: _not stated_
   - validation: PPMAP temperatures differ by only a few K; systematic mass uncertainty factor ~2  
  > "subject to a systematic uncertainty of a factor of approximately two due to uncertainty in the dust opacity" (4.3 Physical properties)
5. **Maximum SFR potential and missed massive-star precursors**: Sum eps*m/tff over leaves; IMF sampling (Kroupa) weighted by 1-P(m) for missing massive precursors  
  > "We then average the number of massive ($\geq 8$ M$_\odot$) stars for 1000 iterations of each leaf mass bin." (5.3 High-Mass Star Precursor Completeness)
   - parameter: SFE 0.1-0.75  
  > "a star formation efficiencies ranging between 0.1-0.75" (5.3 High-Mass Star Precursor Completeness)
   - assumption: each leaf collapses on a freefall time  
  > "assuming each compact source in our catalog collapses on a freefall time and forms stars with an assumed star formation efficiency" (5.2 Maximum Star Formation Potential of the CMZ)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : imaging and simulated observations (simobserve, tclean)  
  > "A simulated observation of the artificial skymap is generated using the `CASA simobserve` function." (3.2 Source Recovery and Simulated Observations)
- **astrodendro** : dendrogram and leaf property extraction  
  > "using the `PP_Statistic` package in the `Astrodendro` package" (4.3 Physical properties)
- **MIR IDL** : SMA calibration and imaging  
  > "All data were calibrated in MIR IDL using standard SMA calibration procedures" (2 Description of the Data)
- **AATM** : atmospheric noise in simulated observations  
  > "using the `AATM` package[^4], an atmospheric modeling package designed for use with ALMA" (3.2 Source Recovery and Simulated Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Robust catalog leaves | 285 | not stated | leaves | 2 | The robust catalog contains 285 leaves |
| High-completeness catalog leaves | 816 | not stated | leaves | 2 | The change produces a catalog of 816 leaves as compared to the robust catalog with its 285 leaves. |
| Median local RMS | 13 | not stated | MJy/sr | 1 | We find a median RMS over all surveyed regions is 13 MJy sr$^{-1}$. |
| Median leaf mass (robust) | ~86 | factor ~2 systematic | Msun | 4 | with a median value of $\sim 86 {\rm M_{\odot}}$ |
| Median H2 column density | 1.2e23 | not stated | cm^-2 | 4 | with a median value of $N_{\rm H_{2}}\sim 1.2\times10^{23}\,{\rm cm^{-2}}$ |
| 95% completeness mass, robust | 80 | not stated | Msun | 3 | point-sources above 80 solar masses, under the typical observational conditions for the *CMZoom* survey, are detected with more than 95% completeness |
| 95% completeness mass, high-completeness | ~50 | not stated | Msun | 3 | with a 95% completeness of $\sim 50$ M$_\odot$ (assuming T$_d$=20K) |
| Maximum SFR potential CMZ | 0.08 - 2.20 | not stated | Msun/yr | 5 | the maximum star formation potential of the CMZ is between 0.08 - 2.20M$_\odot$ yr$^{-1}$ |
| Maximum SFR potential excluding Sgr B2 | 0.04 - 0.47 | not stated | Msun/yr | 5 | or, excluding Sgr B2, between 0.04 - 0.47M$_\odot$ yr$^{-1}$ |
| Missed massive-star precursors | <~1% | not stated | percent | 5 | which we find to be $\lessapprox1$% (if we assume a star formation efficiency of 0.75) |

## Qualitative findings

- Sgr B2 sources form a separate high-mass mode in the mass-radius plane, likely from free-free contamination, higher dust temperatures and line-of-sight confusion  
  > "This separation is likely caused by a combination of several factors" (6 Summary)

## Claim tuples

- H: Can a pruned dendrogram yield a reliable catalog of CMZ compact sources? | E: Dendrogram plus local-noise pruning on CMZoom 1.3 mm maps with simulated-observation tests | R: 285 robust and 816 high-completeness leaves; >95% complete above 80 and 50 Msun | F: Two catalogs with characterized completeness | **supported**
- H: Does the robust catalog miss high-mass star precursors? | E: Completeness curve combined with Kroupa IMF sampling | R: <~1% missed | F: Catalog >99% complete for high-mass star formation sites | **supported**
- H: Are Sgr B2 masses reliable? | E: Compare mass-radius, vary temperature, background subtraction | R: Sgr B2 sources form separate mode | F: Masses likely unreliable | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Higher-resolution PPMAP temperatures considered; differ only by a few K so Herschel SED temperatures used  
  > "higher resolution temperature maps derived using the PPMAP procedure (cite: Marsh_multitemperature_2017) differ only by a few degrees K" (4.3 Physical properties)
- How they decided it was enough: _not stated_
- Limitation (authors): Completeness assumes point sources and does not capture extended emission; masses uncertain by factor ~2  
  > "These mass completeness estimates account only for the observational biases in observing point-source-like emission" (3.2 Source Recovery and Simulated Observations)
- Caveat (inferred, ours): Completeness derived only for point sources; extended leaves not tested
- Caveat (inferred, ours): 20 K assumed for completeness masses vs Herschel Td for catalog masses
- Caveat (inferred, ours): ALMA comparison only by eye, no quantitative cross-match
- Caveat (inferred, ours): Free-free contamination not corrected

## Reproducibility

- Data public (paper): CMZoom data products and catalogs on Harvard Dataverse; simulation scripts on GitHub  
  > "The scripts to generate this completeness percentage have been made available on Github" (3.2 Source Recovery and Simulated Observations)
- Products in archive: _not stated_
- Code: https://github.com/CMZoom/core_catalogue  
  > "https://github.com/CMZoom/core_catalogue" (footnote 3)
- Missing: Paper I imaging details
- Missing: Herschel temperature maps (unpublished)
- Missing: explicit dendrogram numeric parameters
- Data volume (inferred): ~tens of GB for SMA maps; ALMA data only used via cited maps
- Score (inferred): 3/5, Catalog public with scripts, but depends on Paper I and unpublished Herschel maps; ALMA role minor.
- Rediscovery candidate: no, Core data are SMA, not ALMA, and the recipe depends on Paper I and unpublished Herschel products.

## Links

- Method: (cite: battersby_cmzoom_2020) (Survey data, imaging and RMS maps)
- Method: (cite: rosolowsky_structural_2008) (Dendrogram algorithm)
- Companion: (cite: battersby_cmzoom_2020) (CMZoom Paper I)
- Related: CMZoom
- Related: Herschel Hi-GAL

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00269.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 49,
  "rate": 0.576
 },
 "evidence_ok": true
}
```
