# ALMA-IMF. X. The core population in the evolved W33-Main (G012.80) protocluster

`2024A&A...686A.122A` | Astronomy and Astrophysics 2024 | first author: Armante, M. | arXiv: 2401.09203 | DOI: 10.1051/0004-6361/202347595

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: star_formation
- Question: Measure the core mass function (CMF) of the evolved W33-Main protocluster and compare it with CMFs from other Galactic star-forming regions, including other ALMA-IMF fields  
  > "We aimed to measure the CMF in the evolved W33-Main star-forming protocluster to compare it with CMF recently obtained in other Galactic star-forming regions, including the ones included in the ALMA-IMF program." (abstract)
- Target **W33-Main (G012.80)**: coordinates 18h14m13.370s, -17d55m45.200s (J2000), field centre  
  > "The W33-Main field was centred on the 18$^{\rm h}$14$^{\rm m}$13.370s, $-$17$^\circ$55$'$45.200$''$" (Observations and data reduction); "A parallax study of this complex by (cite: Immer2013) located the W33 complex in the Scutum spiral arm, in the first quadrant of the Galaxy, at a distance of 2.40$^{+0.17}_{-0.15}$ kpc." (The G012.80 region); "For W33-Main, we adopted a 2.4 kpc value for the distance" (The global Core Mass Function in W33-Main); z/distance 2.4 kpc (parallax 2.40 +0.17/-0.15 kpc)  
  > "The W33-Main field was centred on the 18$^{\rm h}$14$^{\rm m}$13.370s, $-$17$^\circ$55$'$45.200$''$" (Observations and data reduction); "A parallax study of this complex by (cite: Immer2013) located the W33 complex in the Scutum spiral arm, in the first quadrant of the Galaxy, at a distance of 2.40$^{+0.17}_{-0.15}$ kpc." (The G012.80 region); "For W33-Main, we adopted a 2.4 kpc value for the distance" (The global Core Mass Function in W33-Main); distance from Parallax study of the W33 complex by Immer et al. 2013; adopted value discussed in I14  
  > "The W33-Main field was centred on the 18$^{\rm h}$14$^{\rm m}$13.370s, $-$17$^\circ$55$'$45.200$''$" (Observations and data reduction); "A parallax study of this complex by (cite: Immer2013) located the W33 complex in the Scutum spiral arm, in the first quadrant of the Galaxy, at a distance of 2.40$^{+0.17}_{-0.15}$ kpc." (The G012.80 region); "For W33-Main, we adopted a 2.4 kpc value for the distance" (The global Core Mass Function in W33-Main)

## Data provenance

- ALMA projects: 2017.1.01355.L
- bands: Band 3 (3 mm) and Band 6 (1.3 mm)  
  > "Both the 12 m and 7 m antennas of the interferometer were used in bands 3 and 6 respectively at 3 mm and 1.3 mm" (Observations and data reduction)
- frequencies and spectral setup: Four spws in Band 3 (3.7 GHz total) and eight in Band 6 (2.9 GHz total), re-divided into smaller windows centred on individual lines  
  > "A total of four and eight spectral windows (spw) were set up respectively in bands 3 and 6, for total bandwidths of respectively 3.7 GHz and 2.9 GHz." (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: ALMA 12m and 7m mosaics (67 and 27 pointings at 1.3 mm; 13 and 5 pointings at 3 mm); this paper's core extraction uses 12m-only images  
  > "mosaics were performed by the ALMA 12m and 7m arrays, respectively composed of 67 (12m) and 27 (7m) pointings at 1.3mm and 13 (12m) and 5 (7m) pointings at 3 mm." (Observations and data reduction); "observed by the ALMA 12m only antennas" (abstract)
- configurations: 12m (42 antennas) in C43-2 / C43-4 / C43-1 configurations (TM1 long-baseline, TM2 short-baseline) plus 7m (10 antennas)  
  > "C43-2, C43-4, C43-1 and 7M refers to the observation time using respectively the 12m (42 antennas) and 7m (10 antennas)." (Table 1 notes); "The long- and short-baseline observations are denoted TM1 and TM2, respectively." (Table 1 notes)
- baselines: _not stated_
- angular resolution: ~1 arcsec, ~2400 au at 2.4 kpc  
  > "The angular resolution is of the order of 1$''$, enabling the detection of structures of 2400 au size." (Observations and data reduction)
- max recoverable scale: ~6.6 arcsec at 1.3 mm and ~9.9 arcsec at 3 mm (12m data)  
  > "For the 12m data, the maximum recoverable scales are $\sim$6.6$\ensuremath{''}$ at 1.3 mm and $\sim$9.9$''$ at 3 mm" (Observations and data reduction)
- sensitivity: 1 sigma = 0.20 mJy/beam (1.3 mm) and 0.26 mJy/beam (3 mm), used for the 5 sigma cleaning threshold; bsens maps detect cores down to ~2 Msun at 5 sigma  
  > "with 1$\sigma$ = 0.20 mJy beam$^{-1}$ at 1.3 mm and 1$\sigma$ = 0.26 mJy beam$^{-1}$ at 3 mm" (Data reduction); "allowing the detection of cores with masses down to $\sim2$ $M_{\odot }$ at 5$\sigma$" (Data reduction)
- time on source: _not stated_
- observing dates: December 2017 to December 2018 (whole ALMA-IMF program)  
  > "Between December 2017 and December 2018, as part of the ALMA-IMF" (Observations and data reduction)
- pi or archival as stated: ALMA-IMF Large Program 2017.1.01355.L (PIs Motte, Ginsburg, Louvet, Sanhueza); the paper uses the ALMA-IMF consortium's delivered continuum images and line cubes  
  > "PIs: Motte, Ginsburg, Louvet, Sanhueza" (Observations and data reduction); "The W33-Main data that we used correspond to the continuum images and line cubes delivered by G22 and C23 respectively." (Data reduction)
- Line: CO 2-1 (not stated)
- Line: SiO 5-4 (not stated)
- Line: N2H+ v=0, J=1-0 (not stated)
- Line: H41alpha (and He41alpha+C41alpha blend) H41alpha recombination line (92.034 GHz (spw central frequency used for free-free estimate))
- Other facility **APEX ATLASGAL (LABOCA 870 um) and SABOCA 350 um**: Far-infrared/submm maps used as inputs to PPMAP dust temperature fitting  
  > "two APEX observations (the ATLASGAL one at 870 $\mu$m with the LABOCA receiver" (The dust temperature in W33-Main)
- Other facility **Herschel Hi-GAL (PACS, SPIRE)**: 70, 160 and 500 um maps used in PPMAP  
  > "observations at 70, 160, and 500 $\mu$m" (The dust temperature in W33-Main)
- Other facility **SOFIA/HAWC+**: 89 and 214 um maps used in PPMAP  
  > "two SOFIA/HAWC+ maps at 89 and 214 $\mu$m" (The dust temperature in W33-Main)
- Other facility **MGPS90 (Mustang-2 Galactic Plane Survey pilot) and BGPS**: Single-dish data merged with ALMA-IMF 3 mm and 1.3 mm maps for the spectral index map  
  > "merged with the pilot of the Mustang-2 Galactic Plane Survey (MGPS90, (cite: Ginsburg2020)) at 3 mm" (Free-free contamination); "the Bolocam Galactic Plane Survey (BGPS, (cite: Aguirre2011), (cite: Ginsburg2013)) at 1.3 mm." (Free-free contamination)
- Other facility **2MASS and WISE**: Near/mid-IR point sources used to look for Class I/II and other young stellar objects  
  > "2MASS operates between 1.235 $\mu$m and 2.159 $\mu$m, and WISE between 3.4 $\mu$m and 22 $\mu$m." (2MASS and WISE all-sky surveys)
- Other facility **Spitzer/IRAC GLIMPSE**: 3.6-8.0 um point sources used to search for young stellar objects  
  > "GLIMPSE I imaged at wavelengths 3.6, 4.5, 5.8 and 8.0 $\mu$m using the IRAC instrument" (GLIMPSE Galactic Plane survey)
- External data: Distance to W33-Main (2.4 kpc)  
  > "A parallax study of this complex by (cite: Immer2013) located the W33 complex in the Scutum spiral arm, in the first quadrant of the Galaxy, at a distance of 2.40$^{+0.17}_{-0.15}$ kpc." (The G012.80 region) [from Immer2013 (parallax), see also I14 (Immer2014)]
- External data: [Ne II] 12.81 um emission map used with H41alpha to define H II region zones  
  > "emission at 12.81 $\rm \mu$m presented by (cite: Beilis2022)" (H II regions) [from Beilis et al. 2022 (cite: Beilis2022)]
- External data: Dust opacity per unit gas+dust mass at 1.3 mm, 0.01 (+0.005/-0.0033) cm2 g-1  
  > "we adopted the value of 0.01$^{+0.005}_{-0.0033}$ cm$^2$ g$^{-1}$ from (cite: Ossenkopf1994)" (The global Core Mass Function in W33-Main) [from Ossenkopf & Henning 1994 (cite: Ossenkopf1994); errorbars as in Pouteau2022]
- External data: PPMAP dust temperature products for ALMA-IMF fields  
  > "The systematic application of PPMAP to regions observed by the ALMA-IMF program is ongoing and is the object of Dell’Ova et al., in prep." (The dust temperature in W33-Main) [from Dell’Ova et al., in prep.]
- External data: Free-free subtracted 1.3 mm 'pure dust' continuum map and H41alpha-based free-free estimates  
  > "Galván-Madrid et al., (in prep.) provide the details on how such calculations were used to produce ‘pure’ dust, free-free subtracted maps of continuum emission at 1.3 mm." (Free-free contamination) [from Galván-Madrid et al., in prep.]
- External data: Automatic methyl formate hot core search giving 4 hot core candidates  
  > "This procedure provided a list of 4 hot core candidates in W33-Main." (Identification of hot cores) [from Bonfand et al., in prep.]
- External data: Continuum images (bsens, cleanest) and line cubes of W33-Main  
  > "The W33-Main data that we used correspond to the continuum images and line cubes delivered by G22 and C23 respectively." (Data reduction) [from G22 (Ginsburg2022), C23 (Cunningham2023)]
- External data: Catalogued masers, star cluster and O-type star in the field  
  > "the point sources catalogued by (cite: Messineo2015): one star cluster, one O-type star, two water masers and one methanol maser." (2MASS and WISE all-sky surveys) [from Messineo et al. 2015 (cite: Messineo2015)]
- Simulation/model as data: About 800 synthetic Gaussian sources (FWHM 1.3 arcsec) injected into a getsf background image of the 1.3 mm bsens map to measure completeness  
  > "We then injected $\sim$800 synthetic sources over this background image." (Extraction of compact sources)

## Processing

### Calibration

- pipeline or manual: Automatic CASA pipeline developed by the ALMA-IMF consortium (described in G22)  
  > "developed by the ALMA-IMF consortium and fully described in G22 was used to produce two continuum" (Data reduction)
- casa version: CASA 6.2  
  > "An automatic CASA 6.2 pipeline" (Data reduction)
- pipeline version: _not stated_
- archive products used as is: No: uses ALMA-IMF consortium reprocessed continuum images and line cubes (G22, C23), corrected for system temperature and spectral normalisation  
  > "The ALMA consortium corrected these data for system temperature and spectral normalisation following the problems detected in data from cycle 3 to 7" (Data reduction)
- flux calibrator: _not stated_
- flux scale uncertainty: 10% for ALMA (adopted in PPMAP, from G22)  
  > "10% for ALMA (G22) observations" (The dust temperature in W33-Main)
- self calibration: Self-calibration applied to continuum data, details in G22; noise reduction up to ~46% in Band 3  
  > "because of the extended emission in this field, self-calibration of the data was necessary to achieve the requested sensitivity for continuum images." (Data reduction); "This calibration phase resulted in a significant noise reduction of up to $\sim 46\%$, for Band 3." (Data reduction)

### Imaging

- task: CASA tclean within the ALMA-IMF pipeline  
  > "The cleaning was done using the `TCLEAN` task of CASA." (Data reduction)
- deconvolver: Multi-scale clean; continuum start model used for cubes  
  > "The use of the multi-scale option as well as the use of a continuum start model on the cubes improved the cleaning, especially on the extended emission." (Data reduction)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: cleanest continuum maps made by removing line-contaminated channels (Find_Continuum routine by Todd Hunter); bsens maps keep all spws  
  > "we removed channels contaminated by line emission" (Data reduction)
- line free channels: More than 80% of the continuum bandwidth used for the W33-Main cleanest maps (channel list in G22)  
  > "To produce these maps for the W33-Main field, more than 80% of the continuum bandwidth was used" (Data reduction)
- primary beam correction: Uncorrected 1.3 mm bsens image for source detection; primary-beam-corrected images for size and flux measurements  
  > "We then used the primary beam corrected version of this image to measure the cores’ size and estimate their flux." (Extraction of compact sources)
- array combination: _not stated_
- smoothing: Free-free subtraction map made at the 3 mm angular resolution; spectral index map made at minimum common beam of bands 3 and 6  
  > "performed at the 3 mm angular resolution" (Free-free contamination); "That map was built from bands 3 and 6 continuum maps at their minimum common beam" (Free-free contamination)
- final beam: ~1 arcsec (1.1 x 0.7 arcsec at 1.3 mm from Table 1)  
  > "The angular resolution is of the order of 1$''$" (Observations and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- Self-calibration details and imaging pipeline  
  > "Complete information about the self-calibration of the data can be found in G22." (Data reduction) [from G22 (Ginsburg2022, ALMA-IMF Paper II)]
- Source filtering criteria (goodness/significance, S/N, ellipticity)  
  > "and in line with what was done by (cite: Pouteau2022), compact sources for which i) the goodness and significance factor (defined in (cite: Menshchikov2021a)) are less than 1" (Extraction of compact sources) [from Pouteau2022 (Paper III)]
- Gext2D cross-check of the getsf catalog  
  > "Following the work done by (cite: Pouteau2022), we also used the" (Extraction of compact sources) [from Pouteau2022]
- Spectral index map construction  
  > "(cite: DiazGonzalez2023), see their Equation 2" (Free-free contamination) [from DiazGonzalez2023]
- Hot core identification procedure  
  > "We independently followed the procedure described in Paper IV by (cite: Brouillet2022)." (Identification of hot cores) [from Brouillet2022 (Paper IV)]
- Outflow search method  
  > "Here we followed the same method as presented in e.g. (cite: Nony2023)." (Search for outflows) [from Nony2023 (Paper V)]
- PPMAP configuration (resolution, highpass filter, optical-depth correction)  
  > "Dell’Ova et al. followed the procedure first introduced by (cite: Motte2018Nat) for a number of parameters." (The dust temperature in W33-Main) [from Dell’Ova et al., in prep.; Motte2018Nat]
- Small-scale temperature replacement within cores  
  > "First, following (cite: Pouteau2022), we replaced the temperature distribution within cores by 2D gaussian" (The dust temperature in W33-Main) [from Pouteau2022]
- Core mass formula (optically thick correction)  
  > "we used the formula in (cite: Motte2018Nat) and (cite: Pouteau2022) to our core sample" (The global Core Mass Function in W33-Main) [from Motte2018Nat; Pouteau2022]
- Power-law fitting method for CMF slope  
  > "Like (cite: Pouteau2022), we used the Alstott fitting method ((cite: Alstott2014), using a Maximum Likelihood Estimate approach)" (The global Core Mass Function in W33-Main) [from Pouteau2022; Alstott2014]
- Bootstrap procedure for slope and uncertainty  
  > "This procedure is fully described in (cite: Pouteau2023)." (The global Core Mass Function in W33-Main) [from Pouteau2023 (Paper VI)]

### Not stated but needed to reproduce (our reading)

- getsf run parameters beyond the maximum source size (detection thresholds, filtering scales, number of scales)
- tclean parameters for the delivered images (robust weighting, cell size, image size, masks, multiscale scales) are only in G22/C23
- Self-calibration solution intervals and the exact line-free channel list for the cleanest maps
- H41alpha LTE free-free calculation inputs (electron temperature, line width treatment) and the delivered pure-dust map: both in Galvan-Madrid et al. in prep
- Full PPMAP setup (temperature grid, highpass wavelengths, dilution parameter, optical-depth correction) and the delivered temperature map: in Dell'Ova et al. in prep
- Per-core mean temperatures and uncertainties used in the mass formula
- Exact line transitions and rest frequencies of CH3OCHO, CH3CN, CH3OH, C2H5CN and H2CS used for hot core detection, and how the 2 sigma detection was measured
- Criteria for visual outflow association (subjective eye inspection), and how monopolar/bipolar counts were decided
- Solid angle of beam and flux values per core for mass calculation (Table lists fluxes but not masses or temperatures)
- Mass-driven uncertainty sigma per core and bootstrap random seeds

## Analysis recipe

1. **Define H II region, surroundings and rest-of-cloud zones**: Use 5 sigma and 1 sigma contours of H41alpha and [Ne II] emission to divide the field into three zones  
  > "we defined everything that lies within the 5$\sigma$ contours of the H41$\alpha$ emission" (H II regions); "Finally, outside these $\sigma$ contours, we defined ‘the rest of the cloud’ without significant influence of free-free emission." (H II regions)
   - fitting: _not stated_
   - validation: Compared H41alpha with continuum and [Ne II] morphology and with the structures of I14  
  > "we found a broad correlation of the H41$\alpha$ emission with the 3 and 1.3 mm continuum emission on the one hand and the Ne II emission on the other hand" (H II regions)
2. **Extract compact continuum sources**: Run getsf on the 1.3 mm bsens 12m image (not primary-beam corrected) for detection, then measure sizes and fluxes on primary-beam-corrected images (1.3 and 3 mm bsens and cleanest); filter by getsf goodness and significance, S/N and ellipticity  
  > "we used the 1.3 mm `bsens` 12m array image, uncorrected for primary beam effects for the detection of compact continuum sources." (Extraction of compact sources); "After application of these criteria, the filtered *getsf* catalog contains 94 sources." (Extraction of compact sources)
   - software: getsf, Gext2D
   - parameter: Maximum source size set to three times the beam size (geometric mean of major and minor axes) in each image  
  > "is set to three times the beam size (geometric average of its major and minor extents) in each of the images" (Extraction of compact sources)
   - parameter: First catalog of 101 sources before filtering  
  > "After running *getsf*, we obtained a first catalog of 101 sources." (Extraction of compact sources)
   - assumption: Sources must be relatively round emission peaks; very elongated or complex structures are not compact cores  
  > "If a structure is too elongated or has a very complex shape, it is unlikely to be a compact core." (Extraction of compact sources)
   - fitting: _not stated_
   - validation: Cross-check with Gext2D extraction: more than 75% of sources matched  
  > "we also used the *Gext2D* method, and found that more than 75$\%$ of the sources have a match with those extracted by *getsf*" (Extraction of compact sources)
3. **Measure catalog completeness**: Inject synthetic Gaussian sources into the getsf background image, re-extract with the same parameters and compare injected and recovered mass and position  
  > "We ran the extraction algorithm *getsf* on all these synthetic images with the same parameter as for the observations." (Extraction of compact sources)
   - software: getsf
   - parameter: ~800 sources in ten log-spaced mass bins between 0.15 and 3.0 Msun; Gaussian profile with FWHM 1.3 arcsec (3000 au)  
  > "These synthetic sources were split into ten bins of mass, logarithmically spaced between 0.15 and 3.0 $M_{\odot}$." (Extraction of compact sources); "FWHM of 1.3$''$ ie. 3000 au at 2.4 kpc" (Extraction of compact sources)
   - fitting: _not stated_
   - validation: Five series of simulations with different source locations to dilute grid effects and estimate error bars  
  > "We performed five series of completeness simulations, varying the location of synthetic sources to dilute the effects of the chosen grid and to allow to estimate the error bars." (Extraction of compact sources)
4. **Identify and correct free-free contaminated cores**: Flag cores within 1 sigma contours of H41alpha or [Ne II]; check with a band 3-6 spectral index map; build a 'pure dust' 1.3 mm map by estimating free-free from H41alpha under LTE and extrapolating to 1.3 mm; remove cores with negative pure-dust signal and correct fluxes of contaminated and uncertain cores  
  > "was first estimated using the H41$\alpha$ recombination line under the LTE assumption, and then extrapolated to 1.3 mm wavelength using an optically thin emission of $I_{ff,\nu} \propto \nu^{-0.1}$" (Free-free contamination); "We call them ‘free-free dominated’ and hence remove them from our final core catalog." (Free-free contamination)
   - parameter: Spectral index thresholds: below 0.5 free-free dominated, 0.5 to 2.0 contaminated, above 2.0 dust dominated (where 3 mm emission above 3 sigma)  
  > "Below 0.5 is where the 1.3 mm emission is expected to be dominated by the free-free emission. Between 0.5 and 2.0 is where it should be contaminated by the free-free emission." (Free-free contamination)
   - parameter: Result: 10 free-free dominated (removed), 7 uncertain, 18 contaminated cores  
  > "we identified 10 free-free dominated cores (which are in the following study removed from our core catalog), 7 free-free ‘uncertain’ cores and 18 free-free contaminated cores." (Free-free contamination)
   - assumption: H41alpha free-free estimate under LTE; optically thin free-free emission scaling as nu^-0.1 between 3 and 1.3 mm  
  > "under the LTE assumption" (Free-free contamination)
   - fitting: _not stated_
   - validation: Line-based flagging (35 cores) recovered by spectral index map (17 dominated plus 18 contaminated); pure-dust ratio compared with spectral index  
  > "we found that 17 cores are located inside the free-free dominated parts and 18 inside the contaminated parts of the map, recovering the 35 sources listed based on line emission." (Free-free contamination)
5. **Remove or correct line-contaminated cores**: Subtract CO(2-1) from the 1.3 mm bsens map, re-run getsf with the same parameters, remove sources that vanish (outflow knots) and use cleanest fluxes for sources that survive but lie in outflow lobes  
  > "we subtracted the CO (2–1) line (the brightest line in our dataset) from the `bsens` map at 1.3 mm and performed a new *getsf* extraction on this specific data product" (Line contamination)
   - software: getsf
   - parameter: 4 sources removed as CO-dominated; 4 kept with cleanest flux densities  
  > "In summary, among the 94 sources of our *getsf* filtered catalog, we removed 10 free-free dominated and 4 CO emission-dominated sources." (Line contamination); "Our final *getsf* catalog hence contains 80 cores." (Line contamination)
   - fitting: _not stated_
   - validation: _not stated_
6. **Classify cores as pre- or protostellar**: Hot cores: at least three COM lines detected at 2 sigma toward a core; outflows: eye inspection of CO and SiO blue/red integrated maps plus moment 1, moment 2, SO and PV diagrams; Class I association from WISE; define scenario A (21 protostellar) and B (37 protostellar)  
  > "We considered that the cores where at least three of these lines were simultaneously detected were ‘hot core candidates’." (Identification of hot cores); "We also generated and used complementary maps: moment 1 (central velocity in km/s) and moment 2 (velocity dispersion in km/s), SO integrated intensity maps, and we produced PV-diagrams to confirm or infirm our detections." (Search for outflows)
   - parameter: Outflow velocity ranges: ambient within +-5 km/s of vlsr = 37 km/s; blue [12;32] km/s and red [42;62] km/s  
  > "$\pm~5$ km s$^{-1}$ around W33-Main $v_{lsr} = 37$ km s$^{-1}$ for the ‘ambient gas’, and \[12;32\] km s$^{-1}$ and \[42;62\] km s$^{-1}$ for the blue- and red-shifted components." (Search for outflows)
   - parameter: COM search at 2 sigma for CH3OCHO, CH3CN, CH3OH, C2H5CN and H2CS in named spectral windows  
  > "we searched for 2$\sigma$ detections of methyl formate (CH$_3$OCHO, in spectral window 0 of Band 6)" (Identification of hot cores)
   - parameter: Scenario A: 21 protostellar (26%) and 59 prestellar; scenario B: 37 protostellar (46%) and 43 prestellar  
  > "in scenario A, only the 21 cores mentioned in the previous paragraph are considered protostellar (26% of the sample), and the 59 others are prestellar." (Search for outflows); "resulting in 37 protostellar cores (46% of the sample) and 43 prestellar ones" (Search for outflows)
   - assumption: A hot core is a sufficient but not necessary condition for a protostellar core; presence of an outflow indicates a protostellar object  
  > "which would be a sufficient but not necessary condition to put them in the protostellar category" (Identification of hot cores); "The presence of an outflow around a compact source is usually considered as a tracer of the presence of a protostellar object." (Search for outflows)
   - fitting: _not stated_
   - validation: Hot core list cross-checked with independent automatic search (Bonfand et al., in prep.) giving the same 4 candidates; COM line forests checked in Band 6 spws 6 and 7  
  > "This procedure led us to identify the same 4 hot core candidates toward sources $\#1$, $\#2$, $\#7$ and $\#13$." (Identification of hot cores)
7. **Derive dust temperature map**: PPMAP SED fitting of eight single-dish and interferometric maps from 70 um to 1.3 mm, giving column-density-weighted dust temperature at 2.5 arcsec; correct for optical depth at 70 um; replace temperature within cores by 2D Gaussians (mean core temperature +4 K protostellar, -2 K prestellar)  
  > "We estimated the dust temperature in W33-Main using the Point Process MAPping procedure (hereafter PPMAP, (cite: Marsh2015))." (The dust temperature in W33-Main); "increased of 4 K for protostellar cores to take into acount internal heating, and decreased of 2 K for prestellar ones" (The dust temperature in W33-Main)
   - software: PPMAP
   - parameter: Flat prior on log(T); fixed beta = 1.8 with +-0.2 explored; kappa_300 = 0.1 cm2 g-1 per gas+dust mass  
  > "a flat prior was used for log$(T)$, and a fixed value of 1.8 was used for the spectral emissivity index prior" (The dust temperature in W33-Main); "a value of $\kappa_{300} = 0.1$ cm$^2$ g$^{-1}$ for the dust opacity per unit (gas + dust) at 300 $\mu$m was adopted" (The dust temperature in W33-Main)
   - parameter: Eight modified blackbody components between 21 and 39 K; output resolution 2.5 arcsec; flux uncertainties 15% LABOCA, 20% SABOCA, 10% PACS, 7% SPIRE, 20% HAWC+, 10% ALMA  
  > "we first used eight modified black body components between 21 and 39 K to fit the observations" (The dust temperature in W33-Main); "First, PPMAP products were generated with an expected angular resolution of 2.5$''$." (The dust temperature in W33-Main)
   - assumption: Optical-depth correction applied a posteriori raised the maximum field temperature from 39 K to 44 K; for the cores the correction was not applied before the small-scale replacement  
  > "it resulted in an increase of the maximum temperature in our field from 39 K to 44 K" (The dust temperature in W33-Main)
   - fitting: Bayesian PPMAP fit of modified blackbody building blocks with a dilution factor prior  
  > "In this Bayesian procedure, the spectral energy distribution from the dust emission is described by a combination of modified blackbody functions at given temperatures and given spectral emissivity indices." (The dust temperature in W33-Main)
   - validation: Average of 27 +-3.5 K compared with M22 evolved regions and with earlier Herschel PPMAP, I14 and NH3 temperatures  
  > "The average value of 27 $\pm$ 3.5 K is in agreement with that provided by M22 for evolved regions." (The dust temperature in W33-Main)
8. **Convert 1.3 mm flux densities to core masses**: Optically thick mass formula using integrated and peak 1.3 mm flux, beam solid angle, kappa at 1.3 mm and core-averaged dust temperature; flux from cleanest for line-contaminated and hot core candidates, free-free corrected where needed, bsens otherwise  
  > "This equation assumes that thermal dust emission at 1.3 mm is optically thick ($\tau_{\rm 1.3mm} \gtrsim 1$)" (The global Core Mass Function in W33-Main); "For the 47 remaining sources , it is given by our `bsens` dataset." (The global Core Mass Function in W33-Main)
   - parameter: d = 2.4 kpc; kappa_1.3mm = 0.01 (+0.005/-0.0033) cm2 g-1  
  > "we adopted the value of 0.01$^{+0.005}_{-0.0033}$ cm$^2$ g$^{-1}$ from (cite: Ossenkopf1994)" (The global Core Mass Function in W33-Main); "For W33-Main, we adopted a 2.4 kpc value for the distance" (The global Core Mass Function in W33-Main)
   - assumption: Dust opacity per unit gas+dust mass from Ossenkopf & Henning 1994; optical thickness correction applicable to the 10 densest cores (5 to 10% mass increase)  
  > "This correction results in a 5 to 10$\%$ increase of the masses of these 10 cores." (The global Core Mass Function in W33-Main)
   - fitting: _not stated_
   - validation: Test with a uniform 27 K temperature gave masses from 0.03 to 28.2 Msun and CMF slope compatible with the non-uniform one  
  > "using a uniform dust temperature equal to the average of Fig. [10](#fig:ppmap), $T_{\rm dust}$ = 27 K, the core masses range from $0.03~M_{\odot}$ to $28.2~M_{\odot}$" (The global Core Mass Function in W33-Main)
9. **Fit the global CMF high-mass slope**: Maximum-likelihood power-law fit (Alstott method) of the cumulative CMF above the 1 Msun completeness; then bootstrap of 5000 resampled core samples with Gaussian mass perturbation and EMG fit to the histogram of slopes  
  > "Like (cite: Pouteau2022), we used the Alstott fitting method ((cite: Alstott2014), using a Maximum Likelihood Estimate approach), and obtained a first estimate: $\alpha = -1.43 \pm 0.06$" (The global Core Mass Function in W33-Main); "5000 core samples were generated from the observed core sample." (The global Core Mass Function in W33-Main)
   - software: Alstott power-law fitting method
   - parameter: Fit above completeness 1 Msun (best lower mass limit also estimated by the fit); 2000 randomly generated CMFs for mass-driven uncertainty (~0.06) plus fit uncertainty (~0.02)  
  > "It was obtained by performing the fit over 2000 CMFs randomly generated from individual core masses" (The global Core Mass Function in W33-Main); "The fit uncertainty was generally on the order of $\sigma \simeq 0.02$ estimated from the associated $\chi^2$ value." (The global Core Mass Function in W33-Main)
   - parameter: Bootstrap: each core mass drawn from a normal distribution centred on its mass with standard deviation equal to half the mass sigma  
  > "The center of this distribution is the core mass value, and its standard deviation value was equal to half the $\sigma$ value associated to a core mass mentioned in the previous paragraph." (The global Core Mass Function in W33-Main)
   - assumption: CMF high-mass end follows a single power law N(>=logM) proportional to M^alpha  
  > "We note that if we don’t apply flux correction for the 18 free-free ‘contaminated’ cores we are changing the value from $\alpha = -1.44^{+0.16}_{-0.22}$ to $\alpha = -1.30^{+0.14}_{-0.19}$, that is consistent with the Salpeter slope." (The global Core Mass Function in W33-Main)
   - fitting: Maximum likelihood (Alstott et al. 2014); histogram of bootstrap slopes fitted with an Exponentially Modified Gaussian whose peak gives the best slope; uncertainties from +-1 sigma around the peak  
  > "All histograms are then fitted by an Exponentially Modified Gaussian (EMG), whose peak locates the best fit value for each core sample" (The global Core Mass Function in W33-Main)
   - validation: Sensitivity tests: without free-free flux correction slope -1.30; also without correction for uncertain cores -1.22; uniform T of 27 K gives -1.28  
  > "The resulting CMF has a slope value of $\alpha = -1.28^{+0.14}_{-0.22}$" (The global Core Mass Function in W33-Main)
10. **Fit pre- and protostellar CMFs**: Repeat the MLE and bootstrap fits on prestellar and protostellar sub-samples for scenarios A and B  
  > "We used the bootstrap procedure again, with resulting, final slope values $\alpha = -1.69^{+0.20}_{-0.31}$ for the prestellar cores and $\alpha = -1.04^{+0.15}_{-0.31}$ for the protostellar ones" (Prestellar vs. protostellar CMFs)
   - software: Alstott power-law fitting method
   - parameter: First MLE estimates in scenario A: prestellar -1.67 +-0.06; protostellar -1.06 +-0.08  
  > "We found first estimates for slope values of $\alpha = -1.67 \pm 0.06$ for the prestellar cores, and $\alpha = -1.06 \pm 0.08$ for the protostellar ones" (Prestellar vs. protostellar CMFs)
   - fitting: Same as step 9 (MLE plus 5000-sample bootstrap)  
  > "We used the bootstrap procedure again" (Prestellar vs. protostellar CMFs)
   - validation: Scenario B gives similar results; temperature offsets of -2/+4 K do not change slopes significantly; authors warn about small samples  
  > "The numbers we obtained for scenario B were not substantially different, with bootstrap values $\alpha = -1.75^{+0.24}_{-0.42}$, $\alpha = -1.25^{+0.17}_{-0.33}$." (Prestellar vs. protostellar CMFs); "All these results were obtained on relatively small samples, and should be treated with caution." (Prestellar vs. protostellar CMFs)
11. **Compare core number and mass across H II zones**: Count cores, area fraction and enclosed mass in the three zones; compare maximum core mass and protostellar fraction; relate to column density  
  > "we found 12 cores in the H II regions (representing 2.5% of the 1.3 mm map in surface, and containing approximately 700 $M_\odot$)" (A tentative global view on star formation in W33-Main); "12 cores in their surroundings (2%, 700 $M_\odot$), and 56 cores in the rest of the cloud (95.5%, 10700 $M_\odot$)" (A tentative global view on star formation in W33-Main)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.2: ALMA-IMF automatic calibration/imaging pipeline producing continuum images and line cubes  
  > "An automatic CASA 6.2 pipeline" (Data reduction)
- **tclean** : Cleaning of continuum and line images  
  > "The cleaning was done using the `TCLEAN` task of CASA." (Data reduction)
- **Find_Continuum (Todd Hunter)** : Identify and remove line-contaminated channels for cleanest continuum maps  
  > "Using the `Find_Continuum` routine developed by Todd Hunter" (Data reduction)
- **getsf** : Extraction of compact sources and catalogue completeness tests  
  > "After running *getsf*, we obtained a first catalog of 101 sources." (Extraction of compact sources)
- **Gext2D** : Cross-check source extraction  
  > "we also used the *Gext2D* method, and found that more than 75$\%$ of the sources have a match with those extracted by *getsf*" (Extraction of compact sources)
- **PPMAP** : Dust temperature and column density maps from multi-wavelength data  
  > "We estimated the dust temperature in W33-Main using the Point Process MAPping procedure (hereafter PPMAP, (cite: Marsh2015))." (The dust temperature in W33-Main)
- **Alstott et al. power-law fitting method** : Maximum likelihood power-law fits to the CMF  
  > "we used the Alstott fitting method ((cite: Alstott2014), using a Maximum Likelihood Estimate approach)" (The global Core Mass Function in W33-Main)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Sources in first getsf catalog | 101 | not stated | sources | 2 | After running *getsf*, we obtained a first catalog of 101 sources. |
| Sources in filtered getsf catalog | 94 | not stated | sources | 2 | After application of these criteria, the filtered *getsf* catalog contains 94 sources. |
| 90% completeness mass limit | 1.0 | +-0.2 | Msun | 3 | We estimated a $90\%$ global completeness level of $1.0 \pm 0.2~\rm M_{\odot}$ for the *getsf* catalog |
| Final core catalogue size | 80 | not stated | cores | 5 | Our final *getsf* catalog hence contains 80 cores. |
| Number of cores with outflows | 20 (9 monopolar, 9 bipolar, 2 multipolar) | not stated | cores | 6 | we found 20 cores with outflows, of which 9 monopolar, 9 bipolar and 2 multipolar |
| Hot core candidates | 4 (cores #1, #2, #7, #13) | not stated | cores | 6 | This procedure led us to identify the same 4 hot core candidates toward sources $\#1$, $\#2$, $\#7$ and $\#13$. |
| Average dust temperature of the field | 27 | +-3.5 | K | 7 | The temperatures vary from 20 to 55 K. The average value of 27 $\pm$ 3.5 K is in agreement with that provided by M22 for evolved regions. |
| Mean temperature of hot core candidates #1 and #2 | 55 K (core #1) and 49 K (core #2) | +-10 K each | K | 7 | we found temperatures of 55$\pm$10 K for core $\#$1 and 49$\pm$10 K for core $\#$2 |
| Core mass range | 0.03 to 13.2 | not stated | Msun | 8 | We measured core masses from 0.03 $M_{\odot}$ to 13.2 $M_{\odot}$. |
| Global CMF slope, first MLE estimate | -1.43 | +-0.06 | dimensionless | 9 | and obtained a first estimate: $\alpha = -1.43 \pm 0.06$ |
| Global CMF slope, bootstrap (final) | -1.44 | +0.16/-0.22 | dimensionless | 9 | The resulting, final slope value for the global CMF in W33-Main is $\alpha = -1.44^{+0.16}_{-0.22}$ |
| Global CMF slope without free-free flux correction for the 18 contaminated cores | -1.30 | +0.14/-0.19 | dimensionless | 9 | to $\alpha = -1.30^{+0.14}_{-0.19}$, that is consistent with the Salpeter slope |
| Global CMF slope with uniform T = 27 K | -1.28 | +0.14/-0.22 | dimensionless | 9 | The resulting CMF has a slope value of $\alpha = -1.28^{+0.14}_{-0.22}$ |
| Prestellar CMF slope, scenario A (bootstrap) | -1.69 | +0.20/-0.31 | dimensionless | 10 | final slope values $\alpha = -1.69^{+0.20}_{-0.31}$ for the prestellar cores |
| Protostellar CMF slope, scenario A (bootstrap) | -1.04 | +0.15/-0.31 | dimensionless | 10 | $\alpha = -1.04^{+0.15}_{-0.31}$ for the protostellar ones |
| Prestellar and protostellar CMF slopes, scenario B (bootstrap) | -1.75 (prestellar) and -1.25 (protostellar) | +0.24/-0.42 and +0.17/-0.33 | dimensionless | 10 | with bootstrap values $\alpha = -1.75^{+0.24}_{-0.42}$, $\alpha = -1.25^{+0.17}_{-0.33}$. |
| Cores in H II regions / surroundings / rest of cloud | 12 / 12 / 56 | not stated | cores | 11 | 12 cores in their surroundings (2%, 700 $M_\odot$), and 56 cores in the rest of the cloud (95.5%, 10700 $M_\odot$) |

## Qualitative findings

- Core masses are low across the field (maximum ~13 Msun)  
  > "We also found that the cores’ masses were rather low (maximum mass of $\sim$13 $M_\odot$)." (abstract)
- Scenario where turbulent cores individually collapse is ruled out in W33-Main  
  > "is ruled out in W33-Main, because i) we see a break in the slope of the CMF fit between the prestellar and protostellar phase" (Prestellar vs. protostellar CMFs)
- Star formation proceeds more efficiently in the central H II regions, attributed to compression fronts  
  > "It seems that the increased star formation efficiency in the central regions is favored by the creation of compression fronts associated with the H II regions." (A tentative global view on star formation in W33-Main)

## Claim tuples

- H: W33-Main is an evolved protocluster | E: Identify H II regions from H41alpha and [Ne II], and filaments and outflows from N2H+, CO and SiO | R: Three H II regions within the field; extended N2H+ filaments and outflows | F: W33-Main is evolved in the ALMA-IMF sense | **supported**
- H: The CMF of an evolved protocluster differs from top-heavy CMFs of young ones | E: getsf core census on 1.3 mm bsens map, PPMAP temperatures, MLE and bootstrap power-law fit | R: alpha = -1.44 +0.16/-0.22 above ~1 Msun, 80 cores | F: Global CMF is slightly steeper than but consistent with Salpeter, in contrast with young regions | **supported**
- H: Pre- and protostellar CMFs differ | E: Split cores by hot core, outflow and Class I criteria (scenarios A and B) and fit each CMF | R: Prestellar alpha = -1.69 +0.20/-0.31, protostellar alpha = -1.04 +0.15/-0.31 (scenario A) | F: Prestellar CMF steeper than Salpeter and protostellar CMF slightly top-heavy; small samples | **partially**
- H: H II regions influence core formation and masses | E: Count cores and masses in H II regions, surroundings and the rest of the cloud | R: 12 cores in 2.5% of the area, 12 in 2%, 56 in 95.5%; maximum mass ~7 Msun in H II regions versus ~13 Msun elsewhere | F: Higher proportion of cores in H II regions and surroundings, and low maximum core masses across the field | **supported**
- H: Star formation in W33-Main follows a clump-fed scenario with stellar feedback | E: Compare pre- and protostellar mass distributions and zone statistics with W43 results | R: Excess of massive protostellar cores, no massive prestellar cores, low core masses | F: Results could be compatible with a clump-fed scenario in an evolved cloud under feedback | **partially**

## Reasoning

- Why this data: 1.3 mm bsens 12m image chosen for source detection because it has the best sensitivity and resolution and the least free-free contamination  
  > "As it is the image with the best sensitivity, resolution and the least contamination by free-free emission, we used the 1.3 mm `bsens` 12m array image" (Extraction of compact sources)
- Why this method: Bootstrap used because the core sample is small  
  > "Because the number of cores in our *getsf* catalog is small, we then used a bootstrap procedure to better estimate the most probable slope value and its associated uncertainty." (The global Core Mass Function in W33-Main)
- Alternative: Two pre/protostellar scenarios: A (21 protostellar) and B (37 protostellar, adding cores whose outflow association is unclear)  
  > "We hence decided to study two scenarios: in scenario A" (Search for outflows)
- Alternative: CMF recomputed without free-free flux corrections and with uniform temperature to test sensitivity  
  > "Without any flux correction for free-free contamination, we would have found a slightly top-heavy CMF." (The global Core Mass Function in W33-Main)
- How they decided it was enough: _not stated_
- Limitation (authors): Small samples; results should be treated with caution  
  > "All these results were obtained on relatively small samples, and should be treated with caution." (Prestellar vs. protostellar CMFs)
- Limitation (authors): Outflow search difficult in H II regions and surroundings, so nature of many cores unclear  
  > "Our search for outflows was particularly difficult in the H II regions and their surroundings" (Search for outflows)
- Limitation (authors): Same prescriptions as Pouteau2022 applied to sub-samples gave inconclusive outcomes  
  > "yielded a too broad variety of outcomes to be conclusive" (Prestellar vs. protostellar CMFs)
- Caveat (inferred, ours): Slope depends on the free-free flux correction (-1.44 vs -1.30 vs -1.22) and on a core-by-core temperature recipe tied to unpublished PPMAP products
- Caveat (inferred, ours): Pre/protostellar split relies on subjective eye inspection of outflows and on scenario choice; sub-samples are small
- Caveat (inferred, ours): Mass formula uses a single kappa (Ossenkopf) and an optically thick assumption only for the densest cores
- Caveat (inferred, ours): Several key inputs are 'in prep.' papers, so the chain cannot be audited from this paper alone

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Galvan-Madrid et al. in prep free-free subtracted 1.3 mm map and H41alpha products
- Missing: Dell'Ova et al. in prep PPMAP temperature map and per-core temperatures
- Missing: getsf configuration beyond maximum size and exact images used
- Missing: Core masses and temperatures per core (Table gives fluxes only)
- Missing: Outflow association decisions are visual and not scripted
- Data volume (inferred): Delivered ALMA-IMF continuum images and line cubes for one field are a few GB; raw measurement sets for the 12m and 7m mosaics in Bands 3 and 6 would be hundreds of GB; single-dish and IR maps are small.
- Score (inferred): 2/5, Core catalogue (positions and fluxes) is tabulated and methods are described, but temperature maps, free-free corrections and calibration details depend on unpublished or companion papers
- Rediscovery candidate: no, Data are linked to ALMA project 2017.1.01355.L, but the paper does not state public availability and critical inputs (PPMAP temperatures, pure-dust maps) come from in-prep papers, so the CMF slopes cannot be redone from the paper alone.

## Links

- Method: Ginsburg2022 (G22, ALMA-IMF Paper II) (Continuum image pipeline, self-calibration, bsens and cleanest maps)
- Method: Cunningham2023 (C23, ALMA-IMF Paper VII) (Line cube pipeline)
- Method: Motte2022 (M22, ALMA-IMF Paper I) (Program description and evolutionary classification)
- Method: Menshchikov2021a (getsf) (Source extraction method)
- Method: Pouteau2022 (Paper III) (Core filtering, mass and temperature prescriptions, CMF fitting)
- Method: Pouteau2023 (Paper VI) (Bootstrap fitting procedure)
- Method: Nony2023 (Paper V) (Outflow and pre/protostellar classification method)
- Method: Brouillet2022 (Paper IV) (Hot core identification procedure)
- Method: Motte2018Nat (Mass formula and PPMAP-based temperature procedure)
- Companion: Louvet et al., subm. (Global core population of all 15 ALMA-IMF protoclusters)
- Companion: Galván-Madrid et al., in prep. (H41alpha free-free maps and pure-dust continuum)
- Companion: Dell’Ova et al., in prep. (PPMAP temperature maps of ALMA-IMF fields)
- Companion: Bonfand et al., in prep. (Hot core search)
- Companion: Towner et al., subm.; Valeille-Manet et al., in prep. (SiO and CO outflow searches in all ALMA-IMF fields)
- Related: ALMA-IMF Large Program
- Related: W43-MM1, MM2 and MM3 (ALMA-IMF)
- Related: ATLASGAL
- Related: Hi-GAL
- Related: GLIMPSE
- Related: BGPS
- Related: MGPS90

## Checks

```json
{
 "quotes": 173,
 "quotes_ok": 173,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 138,
  "stated": 112,
  "rate": 0.812
 },
 "evidence_ok": true
}
```
