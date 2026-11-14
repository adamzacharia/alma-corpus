# Properties of H<SUB>2</SUB>O Masers and Their Associated Sources in Sagittarius B2

`2025ApJ...989...52B` | The Astrophysical Journal 2025 | first author: Budaiev, Nazar | arXiv: 2506.09115 | DOI: 10.3847/1538-4357/adea3b

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, milky_way_ism
- Question: Properties and nature of 22 GHz H2O masers in Sgr B2: catalog them with VLA, associate them with HII regions and protostellar cores (ALMA-based catalogs), classify as outflow- or YSO-associated, and compare with continuum and SiO outflow emission  
  > "To investigate the nature of the masers, we analyze their spatial distribution and cross-match with catalogs of  regions and protostellar cores." (abstract); "Based on the spatial extent of the groups of masers, we classify them as either outflow-associated or young stellar object (YSO)-associated." (abstract)
- Target **Sagittarius B2 (Sgr B2 N, M, S, DS)**: coordinates _not stated_; z/distance d=8.277 (unit not preserved in text)  
  > "The observations of the 22.2350798maser line towards Sgr B2 are a part of VLA project 18A-229 (PI: A. Ginsburg)." (2.1 Observation description); "We report the isotropic maser luminosities for each detection assuming d=8.277 (cite: GRAVITY2022)." (3.2 Completeness estimation); distance from GRAVITY Collaboration 2022 (cite: GRAVITY2022)  
  > "The observations of the 22.2350798maser line towards Sgr B2 are a part of VLA project 18A-229 (PI: A. Ginsburg)." (2.1 Observation description); "We report the isotropic maser luminosities for each detection assuming d=8.277 (cite: GRAVITY2022)." (3.2 Completeness estimation)

## Data provenance

- ALMA projects: 2016.1.00550.S
- bands: VLA K-band, 22 GHz (1.3 cm continuum); ALMA 3 mm continuum used for alignment  
  > "but only for K-band observations" (2.1 Observation description); "We then cross-correlate the 3 mm ALMA continuum image (cite: Budaiev2024) with the 1.3 cm continuum image." (2.7 WCS shift)
- frequencies and spectral setup: 16 MHz total bandwidth, 0.07 km/s channel width; imaged velocity range -39.14 to 172.06 km/s  
  > "with a total bandwidth of 16 MHz and a channel width of 0.07km s$^{-1}$" (2.1 Observation description); "The final imaged velocity range is from -39.14km s$^{-1}$ and 172.06km s$^{-1}$, with a spectral resolution of 0.07km s$^{-1}$." (2.6 Cube imaging)
- continuum bandwidth: _not stated_
- arrays: VLA (not ALMA), A configuration  
  > "The data were collected in two observing sessions on March 28th and 29th, 2018 using A configuration." (2.1 Observation description)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: typical noise in a signal-free channel is 11 (units not preserved in text)  
  > "The typical noise in a signal-free channel is 11." (3.2 Completeness estimation)
- time on source: just under 42 minutes for each of the three fields  
  > "The total on-source time is just under 42 minutes for each of the three fields." (2.1 Observation description)
- observing dates: VLA: March 28th and 29th, 2018  
  > "The data were collected in two observing sessions on March 28th and 29th, 2018 using A configuration." (2.1 Observation description)
- pi or archival as stated: VLA project 18A-229 (PI: A. Ginsburg); ALMA data used only for alignment and SiO outflow comparison  
  > "The observations of the 22.2350798maser line towards Sgr B2 are a part of VLA project 18A-229 (PI: A. Ginsburg)." (2.1 Observation description)
- Line: H2O maser not stated (22.2350798 (GHz, per abstract '22 GHz'))
- Line: SiO 5-4 (ALMA, comparison only) (not stated)
- Other facility **VLA**: Primary data: 22 GHz water maser cubes and 1.3 cm continuum for Sgr B2  
  > "We present high-resolution Karl G. Jansky Very Large Array observations of the 22 GHz maser line in the extended Sagittarius B2 cloud." (abstract)
- Other facility **ALMA**: 3 mm continuum image and core catalog (Budaiev2024) used for astrometric alignment and core associations; SiO data from 2016.1.00550.S for the Sgr B2 N outflow  
  > "We then cross-correlate the 3 mm ALMA continuum image (cite: Budaiev2024) with the 1.3 cm continuum image." (2.7 WCS shift); "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00550.S, ADS/JAO.ALMA#2017.1.00114." (Acknowledgements)
- Other facility **JWST (MIRI)**: Used (unpublished, in prep.) to augment HII region catalog and confirm an evolved star classification  
  > "We confirm the classification with JWST data (N. Budaiev 2025, in prep.)" (4.3 Maser associations)
- External data: ALMA 3 mm continuum image of Sgr B2 and ~1000 au resolution protostellar core catalog (used for astrometric alignment and core cross-matching)  
  > "We utilize the $\sim$1000 au resolution catalog from (cite: Budaiev2024)" (4.3 Maser associations); "We then cross-correlate the 3 mm ALMA continuum image (cite: Budaiev2024) with the 1.3 cm continuum image." (2.7 WCS shift) [from Budaiev2024]
- External data: ~5000 au resolution protostellar core catalog covering the extended cloud; also ALMA HII region catalog  
  > "and a $\sim$5000 au resolution catalog that covers the extended cloud (cite: Ginsburg2018)" (4.3 Maser associations) [from Ginsburg2018]
- External data: VLA-based HII region catalogs  
  > "We use VLA- (cite: DePree1998; DePree2015; Meng2022)" (4.3 Maser associations) [from DePree1998; DePree2015; Meng2022]
- External data: Earlier 22 GHz maser catalog of Sgr B2 for comparison and relative proper motions  
  > "We cross-match our catalog with the catalog from (cite: McGrath2004)" (4.1 Comparison with McGrath 2004 catalog) [from McGrath2004]
- External data: Distance to Sgr B2 d=8.277 used for maser luminosities  
  > "We report the isotropic maser luminosities for each detection assuming d=8.277 (cite: GRAVITY2022)." (3.2 Completeness estimation) [from GRAVITY2022]
- External data: Evolved-star cross-match with ACES survey masers (unpublished, in prep.)  
  > "We identify evolved stars by cross-matching isolated masers with masers from the large ALMA survey ACES (S. Longmore in prep)." (4.3 Maser associations) [from S. Longmore in prep]

## Processing

### Calibration

- pipeline or manual: VLA pipeline rerun with manually specified continuum channels and Hanning smoothing off; antennas ea18 and ea05 and the fourth scan of the March 28th data flagged  
  > "We reran the VLA pipeline (version 6.4.1.12) with manually specified continuum (signal-free) channels and Hanning smoothing turned off." (2.2 Pipeline rerun); "Thus, we excluded the fourth scan for both measurement sets." (2.3 Antenna flagging, channel flagging, scan flagging)
- casa version: CASA 6.6.0.2 (listed in Software section)  
  > "CASA version version 6.6.0.2 (cite: McMullin2007)" (Software)
- pipeline version: VLA pipeline 6.4.1.12  
  > "We reran the VLA pipeline (version 6.4.1.12)" (2.2 Pipeline rerun)
- archive products used as is: _not stated_
- flux calibrator: 1331+305=3C286 (bandpass J1733-1304)  
  > "The observations used 1331+305=3C286 as the flux calibrator, J1733-1304 as the bandpass calibrator" (2.1 Observation description)
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration on the brightest maser channel in each field, first round with a manual single-pixel model at the average position of the brightest maser between the two measurement sets  
  > "We self-calibrated the data on the channel with the brightest maser emission in each field." (2.5 Maser self-calibration); "The model consists of a single pixel located in the average position of the brightest maser between two measurement sets." (2.5 Maser self-calibration)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: First and last 32 channels excluded; imaged area restricted per field; one cube ~700 GB  
  > "we exclude the first and last 32 channels" (2.6 Cube imaging); "With these restrictions the size of one cube for each field was $\sim$700 GB." (2.6 Cube imaging)
- masking: CASA automultithresh, parameters tuned to at most 10 masks per channel; cubes cleaned to several threshold levels (2, 0.5, 0.1; units not preserved)  
  > "Thus, we adjusted *automultithresh* parameters until there were no more than 10 masks per channel." (2.6 Cube imaging); "We then clean each cube to several threshold levels (2, 0.5, 0.1)" (2.6 Cube imaging)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Source extraction run on non-primary-beam-corrected images  
  > "Finally, we run `astrodendro` on each of the channel chunks on the non-primary-beam-corrected images." (3.1 Source extraction)
- array combination: Two measurement sets (two sessions) imaged together after self-calibration to a common location  
  > "so the measurement sets can be imaged together." (2.5 Maser self-calibration)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA 3 mm continuum image and core catalog taken from earlier work for alignment and associations  
  > "We then cross-correlate the 3 mm ALMA continuum image (cite: Budaiev2024) with the 1.3 cm continuum image." (2.7 WCS shift) [from (cite: Budaiev2024)]
- Estimate that at least twice as many masers exist below the sensitivity limit  
  > "Following the conclusions of Section 3.2 from (cite: Moscadelli2020), there exist at least twice as many masers in Sgr B2 below our sensitivity limit." (5.2 Properties of the associated continuum sources) [from Section 3.2 of (cite: Moscadelli2020)]
- VLA phase calibrator J1744-3116 coordinate issue reported previously  
  > "As reported in (cite: Budaiev2024), VLA phase calibrator J1744-3116, which is used for many observations of Sgr B2, has wrong coordinates recorded in the VLA catalogs" (Footnote 1) [from (cite: Budaiev2024)]

### Not stated but needed to reproduce (our reading)

- CASA task parameters for tclean (deconvolver, weighting/robust, cell size, image size in pixels, niter)
- Actual automultithresh parameter values (sidelobethreshold, noisethreshold, etc.) and threshold units
- Which channels were specified as continuum/signal-free in the pipeline rerun
- Self-calibration solution intervals, number of rounds and solve modes
- Exact position used for the manual single-pixel starting model
- Which VLA data are public archive products and whether the pipeline-rerun products are released (only continuum files and catalog are stated)
- Pointing/field centers and exact cube velocity frame
- astrodendro num_pix/min_delta handling per chunk and the per-chunk noise values
- DBSCAN eps and min_samples values (only 100 au and 500 au separations stated)
- Units for noise and flux values lost in the converted text (mJy/beam, Jy)

## Analysis recipe

1. **Re-run VLA calibration pipeline and flag**: Rerun the VLA pipeline with manual continuum channels and Hanning smoothing off; flag antennas ea18, ea05 and the fourth scan of the March 28th set  
  > "We reran the VLA pipeline (version 6.4.1.12) with manually specified continuum (signal-free) channels and Hanning smoothing turned off." (2.2 Pipeline rerun)
   - software: VLA pipeline
   - fitting: _not stated_
   - validation: _not stated_
2. **Self-calibrate on brightest maser**: Self-calibrate on the brightest maser channel per field using a manual single-pixel model so both measurement sets converge to one location  
  > "We self-calibrated the data on the channel with the brightest maser emission in each field." (2.5 Maser self-calibration)
   - software: CASA
   - fitting: _not stated_
   - validation: Visual improvement: better phase solutions give more concentrated emission  
  > "better phase solutions result in more concentrated emission" (2.5 Maser self-calibration)
3. **Image spectral cubes**: CASA cleaning with automultithresh masks, cleaned to several thresholds and inspected for divergence  
  > "We then clean each cube to several threshold levels (2, 0.5, 0.1) and inspect the results for divergence or overcleaning when each cleaning threshold is reached." (2.6 Cube imaging)
   - software: CASA
   - parameter: first and last 32 channels excluded and inspected separately  
  > "We inspect these channels separately to ensure that there are no masers present." (2.6 Cube imaging)
   - fitting: _not stated_
   - validation: Per-channel MAD-based standard deviation used as noise estimate  
  > "The per-channel median-absolute-deviation-based (MAD) standard deviation for each channel, which is used as a noise estimate, is shown in Figure" (2.6 Cube imaging)
4. **Align VLA astrometry to ALMA**: Phase cross-correlation of the 1.3 cm VLA continuum with the 3 mm ALMA continuum over five bright extended regions; bootstrap to other fields by 2D Gaussian fits of four bright masers and edit CRVAL in the FITS headers  
  > "We select five regions of bright, extended emission to perform cross-correlation" (2.7 WCS shift); "We take the average offset from the four measurements and apply it to the remaining two fields by editing the ‘CRVAL’ in the FITS headers of the maser cubes." (2.7 WCS shift)
   - software: scikit-image
   - assumption: Proper motions between ALMA and VLA epochs (8 months) negligible  
  > "The ALMA observations happened 8 months prior to the VLA observations, thus any expected deviations due to proper motions are negligible." (2.7 WCS shift)
   - fitting: _not stated_
   - validation: Cross-correlation error 0.19 pixels (3.6 mas); four-maser shift variation no larger than 3% of offset  
  > "the final cross-correlation error is 0.19 pixels (3.6 mas)" (2.7 WCS shift); "the calculated coordinate shift variation was no larger than 3% of the offset distance" (2.7 WCS shift)
5. **Extract maser sources**: Split the cube into channel chunks by noise bins (factor-of-two noise bins, chunks overlap by two channels), run astrodendro per chunk, drop edge-channel detections, merge catalogs  
  > "Then, all consecutive channels that fall into the same noise bin are grouped into chunks." (3.1 Source extraction); "we remove all detections in the edge channels for each of the chunks" (3.1 Source extraction)
   - software: astrodendro
   - parameter: min_value 16 for MN, 14 for MS, 10 for SDS (num_pix 45, min_delta 0.7 of min_value per text)  
  > "for each field were: 16 for MN, 14 for MS, and 10 for SDS." (3.1 Source extraction)
   - fitting: _not stated_
   - validation: min_value raised until false positives fewer than true positives by eye  
  > "gradually increased the threshold until the number of false positives was less than number of true positives with a by-eye inspection" (3.1 Source extraction)
6. **Estimate catalog completeness**: Used the noise below which 93% of sources were extracted (0.046) and a representative 14 sigma threshold  
  > "93% of sources were extracted from channels with noise below 0.046." (3.2 Completeness estimation)
   - assumption: Representative sigma and threshold chosen for the whole sample  
  > "While several assumptions were made to obtain this catalog completeness, it should be representative for the majority of the sample." (3.2 Completeness estimation)
   - fitting: _not stated_
   - validation: _not stated_
7. **Fit positions and spectra**: 2D Gaussian fit in the brightest channel, then pyspeckit spectral fit over 140 channels with extra guesses from neighbors and FWHM guess 0.1 km/s; manual inspection and refit  
  > "First, we fit sources spatially with a 2D Gaussian fitting in the channel with brightest emission." (3.3 Spatial fitting, spectral fitting with pyspeckit); "We center on each detection with a range of 140 channels." (3.3 Spatial fitting, spectral fitting with pyspeckit)
   - software: pyspeckit
   - fitting: 2D Gaussian (spatial) and pyspeckit spectral fit; sampler and priors not stated  
  > "We then fit the sources spectrally using `pyspeckit` package (cite: pyspeckit)." (3.3 Spatial fitting, spectral fitting with pyspeckit)
   - validation: Visual inspection of each detection and fit; 8 of 499 flagged as unsatisfactory  
  > "Only 8 sources out of the 499 had unsatisfactory fits and are marked as such in the catalog" (3.3 Spatial fitting, spectral fitting with pyspeckit)
8. **Compare with McGrath 2004 and derive relative proper motions**: Cross-match catalogs within 0.5 arcsec, select isolated matches with <5 km/s velocity difference (nine sources), remove systemic offset, compute relative proper motions  
  > "Since a large fraction of masers are detected in groups, only nine sources meet the above criteria." (4.2 Maser relative proper motion)
   - assumption: 10 mas representative positional uncertainty for error bars  
  > "Thus, we choose 10 mas as a representative uncertainty for the error bars." (4.2 Maser relative proper motion)
   - fitting: _not stated_
   - validation: Described as proof-of-concept rather than robust  
  > "We note that such relative proper motions are proof-of-concept rather than robust measurements." (4.2 Maser relative proper motion)
9. **Associate masers with HII regions, evolved star, and cores**: Cross-match with HII region catalogs, ACES for evolved stars, then ALMA core catalogs with a smaller then larger search radius  
  > "We then cross-match the masers with mm continuum data to find protostellar core associations." (4.3 Maser associations)
   - fitting: _not stated_
   - validation: JWST detection used to confirm one evolved-star classification  
  > "We confirm the classification with JWST data (N. Budaiev 2025, in prep.)" (4.3 Maser associations)
10. **Classify masers as outflow- or YSO-associated and count sites**: DBSCAN clustering; groups with maximum member separation below 100 au are YSO-associated, otherwise outflow-associated; minimum separation between groups 500 au; visual inspection  
  > "We the use DBSCAN algorithm to cluster the maser features." (5.1.1 Classifying masers around protostellar cores); "If the maximum separation between members of each cluster is below 100 au" (5.1.1 Classifying masers around protostellar cores)
   - software: DBSCAN
   - assumption: Selection criteria do not perfectly distinguish populations (e.g. face-on outflows classed as YSO-associated)  
  > "We note that these selection criteria do not distinguish between the populations perfectly." (5.1.1 Classifying masers around protostellar cores)
   - fitting: _not stated_
   - validation: Comparison with SiO (5-4) outflow structure  
  > "We find that the sources with structured outflows have associated masers distributed over hundreds of au, consistent with their outflow-correlated classifications." (5.1.1 Classifying masers around protostellar cores)
11. **Compare populations and continuum fluxes**: KS test on flux distributions of outflow- and YSO-associated masers; compare 3 mm flux of cores with and without masers; velocity histograms  
  > "We perform the Kolmogorov-Smirnov (KS) test on the flux distributions of the outflow-associated and YSO-associated masers." (5.1.2 Properties of different populations of masers)
   - fitting: _not stated_
   - validation: Noise-filtered YSO-associated sample to check the velocity gap is not data-driven  
  > "We filter the YSO-associated masers to match the average noise in the" (5.1.2 Properties of different populations of masers)

## Software

- **CASA** 6.6.0.2: Imaging with automultithresh masking and cleaning  
  > "automatic masking algorithm to generate cleaning masks" (2.6 Cube imaging); "CASA version version 6.6.0.2 (cite: McMullin2007)" (Software)
- **VLA pipeline** 6.4.1.12: Calibration rerun with manual continuum channels  
  > "We reran the VLA pipeline (version 6.4.1.12)" (2.2 Pipeline rerun)
- **astrodendro** : Dendrogram-based source extraction in channel chunks  
  > "We utilized `astrodendro` (cite: Rosolowsky2008), a dendrogram-based python package to extract sources." (3.1 Source extraction)
- **pyspeckit** : Spectral fitting of detections  
  > "We then fit the sources spectrally using `pyspeckit` package (cite: pyspeckit)." (3.3 Spatial fitting, spectral fitting with pyspeckit)
- **scikit-image** : Phase cross-correlation for VLA-ALMA alignment  
  > "we use the phase cross-correlation algorithm from the `scikit-image` python package" (2.7 WCS shift)
- **astropy** : _not stated_
- **DBSCAN** : Clustering maser features into groups/sites  
  > "We the use DBSCAN algorithm to cluster the maser features." (5.1.1 Classifying masers around protostellar cores)
- **DUCHAMP** : Tested for source extraction and rejected (could not de-blend clustered sources)  
  > "We tested source extraction software `DUCHAMP` (cite: duchamp)." (Source extraction with Duchamp)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of masers detected | 499 | not stated | count | 5 | We detect 499 masers across the observed velocities between -39 and 172 km s$^{-1}$. |
| Independent sites of maser emission | 144 | not stated | count | 10 | Bringing the total number of independent sites of maser emission to 144. |
| Catalog completeness | 0.66 | not stated | dimensionless | 6 | Thus, we estimate our catalog completeness to be 0.66. |
| Fraction of masers associated with HII regions | 162 masers (32%) | not stated | count (percent) | 9 | 162 masers (32%) are associated with regions, with none associated with regions larger than 0.025 pc (5000 au). |
| Masers associated with protostellar cores via cross-matching | 259 | not stated | count | 9 | In total, we find 259 sources associated with protostellar cores via cross-matching. |
| Sites by class: YSO / outflow / region | 18 / 33 / 23 | not stated | count | 10 | We identify 18 sites of YSO-associated masers with 53 individual detections, 33 sites of outflow-associated masers with 214 detections, 23 sites of region-associated masers with 162 detections |
| KS test p-value, outflow vs YSO maser flux distributions | 0.0022 | not stated | dimensionless | 11 | The resulting p-value of 0.0022 indicates the underlying distributions are a likely different between the two populations of masers. |
| Protostellar cores with a corresponding maser | 31 of 371 (Sgr B2 N and M) | not stated | count | 11 | Of the 371 protostellar cores in Sgr B2 N and M, 31 have a corresponding maser |
| Best-case absolute positional accuracy | 0.3 pixels (6 mas, 50 au) | not stated | pixels (mas, au) | 4 | The best-case absolute positional accuracy of our observations is $\sim$0.3 pixels (6 mas, 50 au). |
| Median spatial fit uncertainty | 0.1 pixels (2 mas) in RA; 0.2 pixels (4 mas) in Dec | not stated | pixels (mas) | 7 | The median fit uncertainty is 0.1 pixels (2 mas) in Right Ascension and 0.2 pixels (4 mas) in Declination. |
| Spectral FWHM of masers | <0.1 (1.5 channels) | upper limit | km/s | 7 | The full width at half maximum for each source is $<$0.1km s$^{-1}$ (1.5 channels), indicating that all sources are unresolved spectrally. |
| Masers detected relative to McGrath 2004 in overlapping field | ~2.5 times more | not stated | dimensionless | 8 | we detect $\sim$2.5 times more masers in the overlapping part of the fields of view. |
| Sensitivity improvement over McGrath 2004 | 12 times better | not stated | dimensionless | 8 | Accounting for their slightly larger beam, our absolute sensitivity is 12 times better than their rms noise. |
| Isolated cross-matched sources used for relative proper motion | 9 | not stated | count | 8 | only nine sources meet the above criteria. |
| Cross-correlation alignment error | 0.19 pixels (3.6 mas) | not stated | pixels (mas) | 4 | the final cross-correlation error is 0.19 pixels (3.6 mas) |

## Qualitative findings

- Outflow-associated maser emission is confined to small scales compared with extended SiO emission  
  > "despite shocked emission extending over tens of thousands of au." (abstract)
- YSO-associated masers lack detections in a velocity range, possibly due to self-absorption  
  > "which we suggest may be due to maser self-absorption." (abstract)
- Maser-hosting cores have brighter 3 mm continuum on average, with no strong flux correlation  
  > "protostellar cores with associated masers tend to have brighter 3 mm continuum emission on average, although there is no strong correlation between maser brightness and continuum flux." (abstract)

## Claim tuples

- H: What are the nature and associations of the 22 GHz masers across Sgr B2? | E: Cross-matching the VLA maser catalog with HII region and ALMA protostellar core catalogs | R: 62% of masers are associated with protostellar cores and 32% with HII regions; 144 sites | F: Most masers trace protostellar cores; HII regions host a sizeable minority | **supported**
- H: Do outflow-associated and YSO-associated masers differ in observable properties? | E: DBSCAN clustering by spatial extent, KS test on fluxes and velocity histograms | R: Flux distributions differ (p = 0.0022); YSO-associated masers lack detections in a velocity range and are on average blue-shifted | F: The populations differ; the velocity gap may be self-absorption but is not demonstrated | **partially**
- H: Do masers in protostellar cores correlate with 3 mm continuum brightness? | E: Compare 3 mm fluxes of cores with and without masers and maser luminosity versus continuum | R: Cores with masers brighter on average; no strong correlation with maser luminosity | F: Maser presence tracks brighter cores but brightness does not scale with continuum flux | **supported**
- H: Do masers trace the large-scale outflow in Sgr B2 N? | E: Compare maser positions with ALMA SiO outflow map | R: Masers align with the edges of the SiO outflow | F: Masers trace shocked outflow boundaries; the outflow may come from one or two accreting objects | **partially**
- H: Can maser relative motions between 1998 and 2018 constrain cloud proper motion? | E: Cross-match with McGrath 2004 for nine isolated sources | R: Systemic offset implies unrealistically high cloud motion; two masers exceed 100 km/s | F: Maser proper motions are unreliable for cloud motion without establishing maser nature | **supported**

## Reasoning

- Why this data: Resolved ALMA and JWST data allow revisiting existing maser data in the context of resolved feedback and infall  
  > "The high-resolution multi-wavelength observations enable us to revisit existing maser data in the context of resolved feedback, infall, and dynamical interactions within the forming star clusters." (Introduction)
- Why this method: Cube split into noise-similar chunks because astrodendro cannot handle varying noise  
  > "Since `astrodendro` is not designed to work with varying noise, we implemented an approach to split the cube into smaller cube chunks with similar noise." (3.1 Source extraction)
- Alternative: DUCHAMP source finder rejected: poor de-blending of clustered sources  
  > "we find that it does not behave well with clustered groups of sources." (Source extraction with Duchamp)
- Alternative: Interactive cleaning rejected due to data volume  
  > "Due to the volume of data, it is impractical to perform interactive cleaning." (2.6 Cube imaging)
- How they decided it was enough: _not stated_
- Limitation (authors): Absolute astrometric uncertainty may not represent true uncertainty  
  > "we caution the reader that the reported uncertainty is not necessarily representative of true uncertainty" (2.7 WCS shift)
- Limitation (authors): Some clustered sources merged; automultithresh may leave fainter sources unmasked  
  > "While some sources were merged and thus identified as a single detection, the conclusions drawn in this work are unaffected." (3.3 Spatial fitting, spectral fitting with pyspeckit); "While some of the fainter sources in a channel may not get masked, the brightest ones, responsible for the most artifacts, do get masked." (2.6 Cube imaging)
- Limitation (authors): Offset between the two VLA measurement sets had no established cause  
  > "There are several possible explanations for this offset, but the true source could not be established." (2.4 Spatial offset between two measurement sets)
- Caveat (inferred, ours): The ALMA component is minor and inherited from earlier papers; the primary dataset is VLA 22 GHz
- Caveat (inferred, ours): Many parameters (tclean settings, automultithresh values, selfcal solints) are not stated, so the cubes cannot be reproduced from the text alone
- Caveat (inferred, ours): Completeness of 0.66 rests on a single representative noise and threshold across fields with different thresholds
- Caveat (inferred, ours): Association and classification depend on external catalogs, some unpublished (JWST, ACES)
- Caveat (inferred, ours): Each ~700 GB cube needed about a month of compute, making full reproduction costly

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Full tclean and automultithresh parameter values
- Missing: Self-calibration details
- Missing: Pipeline continuum channel selection
- Missing: Unpublished JWST and ACES catalogs
- Missing: Public/archive status of VLA project 18A-229 data not stated
- Data volume (inferred): About 2 TB of image cubes (3 x ~700 GB) plus larger VLA visibility data; ALMA data only as continuum image and catalogs from earlier work
- Score (inferred): 3/5, Methods for source extraction and fitting are well described, but VLA calibration and imaging settings are mostly unstated and processing is very expensive.
- Rediscovery candidate: no, Public status of VLA data not stated, imaging parameters incomplete, and cubes take about a month of compute each; ALMA role is minor.

## Links

- Method: (cite: Budaiev2024) (ALMA 3 mm continuum and core catalog used for alignment and associations)
- Method: (cite: Rosolowsky2008) (astrodendro algorithm)
- Method: (cite: Moscadelli2020) (Maser sensitivity-limit comparison)
- Companion: (cite: McGrath2004) (Previous 22 GHz maser catalog of Sgr B2 compared against)
- Companion: (cite: Ginsburg2018) (ALMA core catalog covering the extended cloud)
- Related: VLA project 18A-229
- Related: ACES (ALMA survey)
- Related: ALMA 2016.1.00550.S
- Related: ALMA 2017.1.00114

## Checks

```json
{
 "quotes": 122,
 "quotes_ok": 122,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2017.1.00114.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 110,
  "stated": 75,
  "rate": 0.682
 },
 "evidence_ok": true
}
```
