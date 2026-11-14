# Internal 1000 au Scale Structures of the R CrA Cluster-forming Cloud. I. Filamentary Structures

`2024ApJ...968..131T` | The Astrophysical Journal 2024 | first author: Tachihara, Kengo | arXiv: 2404.11113 | DOI: 10.3847/1538-4357/ad40a6

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: What filamentary sub-structures exist inside the dense, cluster-forming R CrA clump, what are their physical properties (widths, column density, line mass, velocity), are they gravitationally unstable and star-forming, and how do they form  
  > "How these structures further fragment and provide the initial conditions for cluster formation is an interesting question." (Introduction); "We identify 101 and 37 filamentary structures with a few thousand AU widths in C$^{18}$O and SO, respectively, called as *feathers*." (abstract)
- Target **R CrA cluster-forming cloud (Corona Australis, Coronet cluster)**: coordinates not stated (only an off-position at 18h58m38.3s, -37d39m22.2s is given)  
  > "The Corona Australis molecular cloud is one of the nearest star-forming regions at the distance of 149 pc (cite: galli2020)" (Introduction); z/distance 149 pc  
  > "The Corona Australis molecular cloud is one of the nearest star-forming regions at the distance of 149 pc (cite: galli2020)" (Introduction); distance from galli2020 (Galli et al. 2020)  
  > "The Corona Australis molecular cloud is one of the nearest star-forming regions at the distance of 149 pc (cite: galli2020)" (Introduction)

## Data provenance

- ALMA projects: 2018.A.00056.S
- bands: Band 6 (1.3 mm continuum)  
  > "Observations were carried out in Band 6 using the Atacama Compact Array (ACA) standalone mode of the ALMA telescope" (ALMA ACA observations); "mainly those from C$^{18}$O $J=$2–1, SO $J_N = 6_5$–$5_4$ emission lines and the 1.3 mm continuum observations" (Introduction)
- frequencies and spectral setup: Tuned for 12CO, 13CO, C18O (J=2-1), N2D+ (J=3-2) and continuum; SO JN=6_5-5_4 falls in the C18O spectral window; velocity resolution 0.1 km/s for 12CO and N2D+, 1.6 km/s for the other lines  
  > "SO $J_N = 6_5$–$5_4$ emission line falls in the Spectral Window (SpW) for the C$^{18}$O lines, and was obtained simultaneously." (ALMA ACA observations); "The velocity resolution of the spectra was 0.1 km s$^{-1}$ for $^{12}$CO and N$_2$D$^+$ and 1.6 km s$^{-1}$ for the other lines" (ALMA ACA observations)
- continuum bandwidth: 4 MHz assigned to the continuum; two SpWs of 2 GHz each (as printed)  
  > "and a bandwidth of 4 MHz was assigned to the continuum (two SpWs were used, both with a bandwidth of 2 GHz)" (ALMA ACA observations)
- arrays: ACA 7m array (standalone) plus Total Power (TP) array  
  > "In order to recover the missing flux of the extended emission, the total power (TP) array was also used." (ALMA ACA observations)
- configurations: Mosaic of 1501 pointings with the 7m array covering 175 arcmin^2 in 12 rectangular fields; TP covered 129 arcmin^2 (4 fields complete, 5 incomplete, 3 northern fields not observed)  
  > "the entire area of 175 arcmin$^2$ was divided into 12 rectangular fields, covered by mosaics of 1501 pointings with the 7m array." (ALMA ACA observations); "Only 4 fields of the TP array observations were complete and 5 fields incomplete, while the rest of northern 3 fields were not observed at all." (ALMA ACA observations)
- baselines: _not stated_
- angular resolution: Synthesized beam 7.89'' x 4.88'', PA = -77.4 deg (7m array)  
  > "while the synthesized beam has an extent of $7.89\ensuremath{''} \times 4.88\ensuremath{''}$ with PA = $-77.4\ensuremath{^\circ}$" (Data reduction)
- max recoverable scale: _not stated_
- sensitivity: 7m: 0.67 mJy/beam continuum; Trms = 0.025 K lines at 1.6 km/s, 0.076 K at 0.1 km/s; TP: 1.1 mK to 6.2 mK  
  > "a sensitivity of 0.67 mJy beam$^{-1}$ was achieved for the continuum and $T_{\rm rms} = 0.025$ K for the emission lines with a velocity resolution of 1.6 km s$^{-1}$" (Data reduction); "The TP-array sensitivity ranges from 1.1 mK to 6.2 mK." (Data reduction)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: C18O J=2-1 (not stated)
- Line: SO JN=6_5-5_4 (not stated)
- Line: 12CO, 13CO (J=2-1) and N2D+ (J=3-2), observed but not presented J=2-1 / J=3-2 (not stated)
- Other facility **Herschel Gould Belt Survey**: Dust column density and temperature maps used for context and the assumed 15 K temperature  
  > "This research has made use of data from the Herschel Gould Belt survey (HGBS) project" (Conclusions); "referring to the Herschel’s dust temperature map and the peak $T_{\rm mb}$ of $^{12}$CO ($J=$1–0) line taken by NANTEN" (Column density distributions and embedded feathers)
- Other facility **NANTEN telescope**: Unpublished 12CO J=1-0 large-scale map of the whole cloud (cloud mass, context)  
  > "integrated intensity map of $^{12}$CO $J=$1–0 line observed by the NANTEN telescope (unpublished data)" (Introduction)
- Other facility **Spitzer and SMA catalogues**: Positions of Class 0/I YSOs used to test continuum detection and feather association  
  > "Among the 11 Class 0/I sources identified by the Spitzer and SMA observations (cite: peterson11; groppi07)" (Overall properties of the cloud)
- Other facility **ALMA 12m array (part 2 paper)**: Higher resolution data inspected visually to associate IRS 7 YSOs with feathers; not analysed here  
  > "After careful visual inspection of high resolution 12m array data, we judged that IRS 7B is associated with the highest line mass feature" (Line mass and dynamical stability of the feathers)
- External data: Cloud distance 149 pc  
  > "The Corona Australis molecular cloud is one of the nearest star-forming regions at the distance of 149 pc (cite: galli2020)" (Introduction) [from (cite: galli2020)]
- External data: C18O-to-H2 abundance relation used to get N(H2)  
  > "assuming a constant molecular abundance of C$^{18}$O relative to H$_2$" (Column density distributions and embedded feathers) [from (cite: frerking82)]
- External data: Class 0/I protostar catalogue positions  
  > "Among the 11 Class 0/I sources identified by the Spitzer and SMA observations (cite: peterson11; groppi07)" (Overall properties of the cloud) [from (cite: peterson11; groppi07)]
- External data: Herschel dust column density and temperature maps  
  > "Herschel Gould Belt Survey (cite: andre10)" (Distribution of the feather structures) [from (cite: andre10)]
- External data: Herschel filament identification and ~30 Msun/pc line mass of the large filaments  
  > "the filaments identified in the Herschel data by (cite: bresnahan2018) have a line mass of about" (Filament formation mechanisms) [from (cite: bresnahan2018)]
- External data: HI shells with line-of-sight velocities 3.3 and 7.4 km/s overlapping at the cloud  
  > "(cite: bracco20) points out that the CrA cloud is located on the boundary where two H I shells overlap." (Comparison with MHD simulations) [from (cite: bracco20)]
- Simulation/model as data: MHD simulation of colliding gas flows (Abe et al., in prep.; abe2024), max resolution 0.001 pc, 4000 cm^-3 sheet of 0.1 pc thickness, 50 uG in-plane field, +-1 km/s flows, isothermal, self-gravity and ambipolar diffusion; column density at 1.3 Myr compared with observed feathers  
  > "Abe et al. (in prep.) performed MHD numerical simulations of colliding gas flows at a maximum resolution of 0.001 pc." (Comparison with MHD simulations); "Initially, a sheet of gas with a density of 4000 cm$^{-3}$ and thickness of 0.1 pc is placed, and a magnetic field of 50 $\mu$G penetrates in the in-plane $x$ direction." (Comparison with MHD simulations); "Isothermal condition is assumed, adding fluctuations to the collision surface, and self-gravity and ambipolar diffusion are taken into account in the calculations." (Comparison with MHD simulations)

## Processing

### Calibration

- pipeline or manual: Standard calibrations provided by the ALMA observatory  
  > "Standard calibrations provided by the ALMA observatory were applied to each measurement set" (Data reduction)
- casa version: CASA 6.4.4-31  
  > "Data was reduced using CASA (cite: casa22) version 6.4.4-31." (Data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean on concatenated visibilities of all pointings/fields  
  > "we concatenated all of the visibility files and imaged them together" (Data reduction); "We used `tclean` task with the `multi-scale` deconvolver (cite: Kepley20) to recover the extended emission." (Data reduction)
- deconvolver: multi-scale  
  > "We used `tclean` task with the `multi-scale` deconvolver (cite: Kepley20) to recover the extended emission." (Data reduction)
- weighting robust: natural weighting  
  > "We applied the natural weighting" (Data reduction)
- uv taper: _not stated_
- cell size: 1'' x 1'' grid spacings  
  > "The obtained images were exported to maps with $1\ensuremath{''} \times 1\ensuremath{''}$ grid spacings" (Data reduction)
- image size: _not stated_
- masking: CLEAN mask created automatically with auto-multithresh  
  > "the CLEAN mask was automatically created using the `auto-multithresh` procedure" (Data reduction)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: TP images for C18O and SO regridded to the 7m pixel scale and combined with the 7m image using CASA feather  
  > "The TP array data for C$^{18}$O and SO were regridded at the same pixel scale as the 7m-array image and combined by the `feather` task." (Data reduction)
- smoothing: _not stated_
- final beam: 7.89'' x 4.88'', PA = -77.4 deg  
  > "while the synthesized beam has an extent of $7.89\ensuremath{''} \times 4.88\ensuremath{''}$ with PA = $-77.4\ensuremath{^\circ}$" (Data reduction)
- final rms: 0.67 mJy/beam (continuum); 0.025 K at 1.6 km/s and 0.076 K at 0.1 km/s (lines, 7m only)  
  > "a sensitivity of 0.67 mJy beam$^{-1}$ was achieved for the continuum and $T_{\rm rms} = 0.025$ K for the emission lines with a velocity resolution of 1.6 km s$^{-1}$" (Data reduction)

### Inherited from earlier work

- Imaging strategy (tclean multi-scale, automasking, natural weighting)  
  > "The imaging strategy is the same as the previously reported ACA large-scale surveys (cite: Tokuda21; Muraoka23)." (Data reduction) [from previously reported ACA large-scale surveys (cite: Tokuda21; Muraoka23)]
- Multi-scale deconvolver choice  
  > "We used `tclean` task with the `multi-scale` deconvolver (cite: Kepley20) to recover the extended emission." (Data reduction) [from (cite: Kepley20)]
- C18O/H2 abundance relation N(H2)=[N(C18O)/1.7e14+1.3]e21  
  > "assuming a constant molecular abundance of C$^{18}$O relative to H$_2$" (Column density distributions and embedded feathers) [from (cite: frerking82)]
- Velocity-resolved structure, overlap of velocity components and 12m-array details deferred to the part 2 paper  
  > "These issues are discussed in detail in Fukaya et al. (part 2 paper) with higher resolution 12m-array data." (Properties of the filamentary substructures) [from Fukaya et al. (part 2 paper, in preparation)]

### Not stated but needed to reproduce (our reading)

- multi-scale scales list, niter, threshold, gain and the auto-multithresh parameters in tclean
- image size, phase centres and mosaic gridding per field, and primary-beam correction
- spectral window and channels used for the continuum and whether continuum was subtracted from the lines
- how the TP data were calibrated and imaged, and feather parameters (SDfactor, uv ranges)
- conversion of Jy/beam to brightness temperature and Tmb; efficiency used
- velocity range and procedure for building the peak T maps and moment maps
- FilFinder parameters other than adapt_thresh, smooth_size, size threshold and 3 sigma (e.g. global threshold, beam width, flatten percent), and FilFinder version
- how the column density and width were averaged along each branch (mask, spine pixels) and how the 7m-only versus 7m+TP line mass was computed
- how association of feathers with YSOs was decided (distance criterion)
- why 110 C18O structures appears in the overlap count versus 101 elsewhere
- the NANTEN 12CO map and the Abe et al. MHD simulation are unpublished and not available
- the 4 MHz versus 2 GHz continuum bandwidth is inconsistent as printed

## Analysis recipe

1. **Image the 7m data and combine with TP**: Concatenate all calibrated 7m and TP measurement sets, image with tclean (multi-scale, natural weighting, auto-multithresh), then feather TP with the 7m image  
  > "we concatenated all of the visibility files and imaged them together" (Data reduction); "The TP array data for C$^{18}$O and SO were regridded at the same pixel scale as the 7m-array image and combined by the `feather` task." (Data reduction)
   - software: CASA, tclean, feather
   - parameter: natural weighting, multi-scale deconvolver, auto-multithresh mask, 1'' x 1'' pixels  
  > "We applied the natural weighting" (Data reduction); "the CLEAN mask was automatically created using the `auto-multithresh` procedure" (Data reduction)
   - fitting: _not stated_
   - validation: Combined and TP images compared to check that 7m sub-structures are not edge artifacts  
  > "This can be confirmed by comparing the combined image with the TP array image." (Overall properties of the cloud)
2. **Identify filamentary structures (feathers) and measure widths**: FilFinder run on 7m-only peak antenna temperature maps; skeletons split at junctions into branches; Gaussian fit across the ridge for width  
  > "For the C$^{18}$O and SO images reported here in detail, an algorithm for filament identification, FilFinder, was used (cite: koch15)" (Properties of the filamentary substructures); "They were obtained by fitting the intensity distribution perpendicular to the ridge, assuming the Gaussian distributions." (Properties of the filamentary substructures)
   - software: FilFinder
   - parameter: detection limit 3 sigma = 0.075 K; minimum structure size 600 pixels (1 pixel = 1'' x 1'')  
  > "we set $3\sigma = 0.075$ K as the detection limit and the minimum size of the structure as 600 pixels" (Properties of the filamentary substructures)
   - parameter: skeleton ridge longer than 5 beam sizes; branches shorter than 3 beam sizes discarded  
  > "if the ridge has a length longer than 5 times the beam size" (Properties of the filamentary substructures); "After discarding short branches less than 3 times the beam size" (Properties of the filamentary substructures)
   - parameter: adapt_threth = 0.006 pc  
  > "FilFinder provides an input parameter, `adapt_threth` (0.006 pc in this case), which is an estimate of the filament width to be identified" (Properties of the filamentary substructures)
   - parameter: smooth_size = 0.003 pc  
  > "the `smooth_size` (0.003 pc in this case) were set to eliminate small noise fluctuations when creating the mask." (Properties of the filamentary substructures)
   - assumption: Peak T maps used instead of moment 0 to avoid velocity-range ambiguity; overlap of more than two velocity components along the line of sight judged not prominent  
  > "Technically, the use of the Peak $T$ maps, not the moment 0 maps, is advantageous as it allows us to exclude ambiguity related to velocity-range selection." (Properties of the filamentary substructures)
   - fitting: Gaussian fit to the intensity profile perpendicular to the ridge, implemented in FilFinder  
  > "They were obtained by fitting the intensity distribution perpendicular to the ridge, assuming the Gaussian distributions." (Properties of the filamentary substructures)
   - validation: Feathers found in 7m data lie inside the extended TP structures, not on edges, so not artifacts; width bias from the adapt_thresh input admitted  
  > "show that all the filamentary sub-structures found in the 7m array are embedded inside of the extended structures, rather than located at the edges" (Overall properties of the cloud); "so there remains a bias in the extracted filamentary structure width" (Properties of the filamentary substructures)
3. **Derive H2 column density from C18O**: LTE C18O column density computed per velocity channel with optical depth from Tmb, integrated over velocity, then converted to N(H2) with a constant abundance  
  > "The calculations were performed for each velocity channel and integrated over the velocity to obtain $N({\rm C^{18}O})$ for each pixel." (Column density distributions and embedded feathers)
   - parameter: Tex constant = 15 K  
  > "the excitation temperature ($T_{\rm ex}$) was assumed to be constant at 15 K" (Column density distributions and embedded feathers)
   - assumption: LTE, constant Tex, constant C18O abundance relative to H2 (Frerking et al. 1982); CO freeze-out makes N(H2) a lower limit  
  > "the C$^{18}$O emission lines were assumed to be in local thermodynamic equilibrium (LTE)" (Column density distributions and embedded feathers); "Thus $N({\rm H_2})$ derived here should be regarded as lower limit." (Column density distributions and embedded feathers)
   - fitting: _not stated_
   - validation: Column density cuts compared between 7m-only and 7m+TP  
  > "Those obtained with the 7m array alone are shown in blue, and those combined with the TP array are shown in red." (Column density distributions and embedded feathers)
4. **Line mass and stability of feathers**: Line mass from average column density and branch width for 7m-only and 7m+TP N(H2); compared with critical line mass 2Cs^2/G  
  > "we estimated the mass per unit length (line mass, $M_{\rm line}$) from the average column density and the filament width obtained above." (Column density distributions and embedded feathers); "The critical line mass for gas with temperature of 15 K is $24\ M_{\ensuremath{\odot}}\,{\rm pc}^{-1}$" (Column density distributions and embedded feathers)
   - parameter: SO: assumed density equal to critical density 2e6 cm^-3 and width 1500 AU  
  > "we assume the average density same as the critical density of $2 \times 10^6$ cm$^{-3}$ for the SO emission lines" (Column density distributions and embedded feathers)
   - assumption: Critical line mass evaluated at 15 K; large 0.1 pc filament taken as width 0.1 pc with N ~1.5e22 cm^-2  
  > "assuming that the extended structure with a column density of $\sim 1.5\times 10^{22}$ cm$^{-2}$ at the center is a filament with the width of 0.1 pc" (Column density distributions and embedded feathers)
   - fitting: _not stated_
   - validation: Median line masses much below critical; statistics of YSO association used as a consistency check  
  > "From these facts, it seems that the feather structures cannot be unstable with self-gravity alone and do not fragment and collapse." (Line mass and dynamical stability of the feathers)
5. **Associate feathers with YSOs and continuum sources**: Compare feather positions with catalogued Class 0/I YSOs; match 1.3 mm continuum peaks to IR coordinates within 2 arcsec  
  > "6 sources are clearly detected in the 1.3 mm continuum as the counterparts with the separations less than 2 arcsec between the 1.3 mm peak positions and the catalogued IR coordinates" (Overall properties of the cloud)
   - fitting: _not stated_
   - validation: _not stated_
6. **Inspect velocity field of feathers**: C18O moment 1 map of the 7m data compared across feathers  
  > "In spite of the poor velocity resolution, the moment 1 map exhibits noticeable velocity change among feathers." (Velocity fields)
   - fitting: _not stated_
   - validation: Limited by 1.6 km/s velocity resolution  
  > "In the present spectral setup, the velocity resolution of C$^{18}$O is 1.6 km s$^{-1}$, which is not sufficient to discuss small changes in the velocity field and spectral shapes." (Velocity fields)
7. **Compare with MHD colliding-flow simulation**: Qualitative comparison of simulated column density map and horizontal cut at 1.3 Myr with the observed feathers and column density cuts  
  > "A horizontal cut of this column density distribution is shown in Fig. [11](#fig:MHDsim) bottom." (Comparison with MHD simulations); "These visual characteristics reproduce the observation well." (Comparison with MHD simulations)
   - assumption: Initial sheet 4000 cm^-3, 0.1 pc thick, 50 uG in-plane field, +-1 km/s inflow, isothermal, ambipolar diffusion  
  > "Gas flow with a velocity of $\pm 1$ km s$^{-1}$ is given from both sides in the $x$ direction, and the gas is converged at the center." (Comparison with MHD simulations)
   - fitting: _not stated_
   - validation: Qualitative visual match of peak widths ~0.01 pc on ~0.1 pc structures and similar column densities  
  > "Sharp density peaks with widths of about 0.01 pc are seen on top of the structure that extends about 0.1 pc." (Comparison with MHD simulations)

## Software

- **CASA** 6.4.4-31: Data reduction, imaging and combination  
  > "Data was reduced using CASA (cite: casa22) version 6.4.4-31." (Data reduction)
- **tclean** : Imaging with multi-scale deconvolver  
  > "We used `tclean` task with the `multi-scale` deconvolver (cite: Kepley20) to recover the extended emission." (Data reduction)
- **auto-multithresh** : Automatic CLEAN masking  
  > "the CLEAN mask was automatically created using the `auto-multithresh` procedure" (Data reduction)
- **feather** : Combining TP and 7m images  
  > "The TP array data for C$^{18}$O and SO were regridded at the same pixel scale as the 7m-array image and combined by the `feather` task." (Data reduction)
- **FilFinder** : Filament skeleton identification and width measurement  
  > "For the C$^{18}$O and SO images reported here in detail, an algorithm for filament identification, FilFinder, was used (cite: koch15)" (Properties of the filamentary substructures)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of C18O filamentary branches (feathers) | 101 | not stated | dimensionless | 2 | We identify 101 and 37 filamentary structures with a few thousand AU widths in C$^{18}$O and SO, respectively |
| Number of SO filamentary branches (feathers) | 37 | not stated | dimensionless | 2 | We identify 101 and 37 filamentary structures with a few thousand AU widths in C$^{18}$O and SO, respectively |
| Branches with successful width estimates (C18O, SO) | 95 and 37 | not stated | dimensionless | 2 | we obtained successful estimations of widths for 95 and 37 branches of C$^{18}$O and SO, respectively |
| Median feather width (C18O, SO) | 0.0064 pc (1300 AU) and 0.0055 pc (1100 AU) | not stated | pc | 2 | with medians of 0.0064 pc (1300 AU) and 0.0055 pc (1100 AU), respectively |
| Maximum feather width | 0.01 | not stated | pc | 2 | The maximum width is 0.01 pc |
| C18O feathers overlapping SO structures | 19 of 110 C18O (as printed) and 16 of 37 SO | not stated | dimensionless | 2 | 19 out of the 110 C$^{18}$O structures overlap with the SO structures, while conversely 16 out of the 37 SO structures do |
| Typical C18O column density of feathers | about 1e22 | not stated | cm^-2 | 3 | The typical column density of the feathers in C$^{18}$O is about $10^{22}$ cm$^{-2}$ |
| Line mass range and median, 7m only | 0.1 - 4.8, median 0.5 | not stated | Msun/pc | 4 | They were distributed in the range of 0.1 – 4.8 $M_\ensuremath{\odot}\,{\rm pc}^{-1}$ with a median value of 0.5 $M_\ensuremath{\odot}\,{\rm pc}^{-1}$ |
| Line mass range and median, 7m+TP | 0.3 - 9.3, median 1.4 | not stated | Msun/pc | 4 | and 0.3 – 9.3 $M_\ensuremath{\odot}\,{\rm pc}^{-1}$ with a median value of 1.4 $M_\ensuremath{\odot}\,{\rm pc}^{-1}$, respectively |
| Critical line mass at 15 K | 24 | not stated | Msun/pc | 4 | The critical line mass for gas with temperature of 15 K is $24\ M_{\ensuremath{\odot}}\,{\rm pc}^{-1}$ |
| Line mass of the 0.1 pc extended structure | approximately 30 | not stated | Msun/pc | 4 | the line mass is approximately $30\ M_{\ensuremath{\odot}}\,{\rm pc}^{-1}$ |
| Median and highest feather volume density | 2.1e5 (median), 1.2e6 (highest) | not stated | cm^-3 | 4 | The median density of the feather is $2.1 \times 10^5$ cm$^{-3}$, and the highest one is $1.2 \times 10^6$ cm$^{-3}$. |
| Feathers associated with YSOs (C18O, SO) | 11 of 101 and 6 of 37 | not stated | dimensionless | 5 | Overall, only 11 and 6 out of the 101 C$^{18}$O and 37 SO filamentary structures, respectively, are associated with YSOs. |
| Class 0/I sources detected in 1.3 mm continuum | 6 of 11 | not stated | dimensionless | 1 | 6 sources are clearly detected in the 1.3 mm continuum as the counterparts with the separations less than 2 arcsec between the 1.3 mm peak positions and the catalogued IR coordinates |
| Velocity dispersion among feathers | ~1 | not stated | km/s | 6 | The velocity dispersion among feathers is about $\sim 1$ km s$^{-1}$. |

## Qualitative findings

- Feathers show complex velocity fields, but each is a relatively coherent velocity structure  
  > "it can be seen that each feather is defined as a relatively coherent velocity structure" (Velocity fields)
- C18O and SO distributions differ: C18O more extended to the north-east, SO more clumpy and filamentary in the middle and north-west  
  > "The overall distributions of the C$^{18}$O and SO lines are quite different as seen in Fig. [3](#fig:mom0_map) and [4](#fig:peakT_map)." (Overall properties of the cloud)
- Most feathers are not forming stars and are likely transient; exception at the cluster centre where 4 protostars lie along feathers  
  > "These suggest that most of the feathers are expected to be structures not forming stars but rather transient." (Line mass and dynamical stability of the feathers)

## Claim tuples

- H: Does the R CrA clump contain real small-scale filamentary sub-structures inside the 0.1 pc Herschel filaments, rather than interferometric edge artifacts? | E: FilFinder on 7m peak-T maps of C18O and SO, compared with 7m+TP combined images and column density cuts | R: 101 C18O and 37 SO branches with median widths ~1300 and ~1100 AU, embedded in extended TP emission | F: The feathers are real thin sub-filaments, only marginally resolved, with widths much smaller than 0.1 pc | **supported**
- H: Are the feathers gravitationally unstable and star-forming? | E: Line mass from C18O N(H2) and width compared with the critical line mass, plus association with YSOs | R: Median line masses 0.5 and 1.4 Msun/pc versus critical 24 Msun/pc; only 11 of 101 C18O feathers have YSOs | F: Most feathers are subcritical, do not collapse, and are transient | **supported**
- H: Can colliding gas flows with magnetic fields produce feather-like structures? | E: Visual comparison of an MHD colliding-flow simulation (Abe et al., in prep.) with observed column density maps and cuts | R: Simulation produces ~0.01 pc sharp peaks on a ~0.1 pc structure with similar column densities | F: Colliding gas flow with slow-shock instability and ambipolar diffusion reproduces the feather morphology | **partially**
- H: Is cluster formation in R CrA triggered by colliding gas flow? | E: Argument from cloud head-tail morphology, HI shell overlap from the literature, and the simulation | R: Cloud sits at the boundary of two HI shells; interior is turbulent | F: Moderate colliding gas flow may trigger the cluster formation | **partially**

## Reasoning

- Why this data: ACA mosaic with TP is suited to wide-field mapping of nearby extended clouds with zero-spacing coverage  
  > "thanks to the relatively wide field of view of the 7m array and the ability to cover zero spacing with the Total Power (TP) array" (Introduction)
- Why this method: Peak T maps chosen for FilFinder to avoid velocity-range ambiguity and for better signal-to-noise than moment 0  
  > "Technically, the use of the Peak $T$ maps, not the moment 0 maps, is advantageous as it allows us to exclude ambiguity related to velocity-range selection." (Properties of the filamentary substructures); "The peak $T$ maps have better signal-to-noise ratio than the integrated intensity maps" (Properties of the filamentary substructures)
- How they decided it was enough: _not stated_
- Limitation (authors): Velocity resolution of 1.6 km/s misses small velocity dispersion structures and cannot separate overlapping velocity components  
  > "Also, structures with different radial velocities that may overlap on the line-of-sight are not separated." (Properties of the filamentary substructures)
- Limitation (authors): TP coverage incomplete and non-uniform sensitivity  
  > "the achieved sensitivity is different for each of them, because the executions of the project timed out in the cycle" (ALMA ACA observations)
- Limitation (authors): N(H2) is a lower limit because of CO freeze-out and the assumed uniform abundance  
  > "However, such region is limited and a uniform abundance distribution is assumed in this paper." (Distribution of the feather structures)
- Limitation (authors): Widths only marginally resolved and biased by the FilFinder adapt_thresh input  
  > "and thus they are only marginally resolved" (Properties of the filamentary substructures)
- Caveat (inferred, ours): Widths are close to the beam (7.89'' x 4.88'' at 149 pc is ~1000 AU) and depend on the FilFinder adapt_thresh input, so the 'feather' width is not robust
- Caveat (inferred, ours): Tex fixed at 15 K and a constant C18O abundance make line masses uncertain, and the SO line mass uses an assumed density
- Caveat (inferred, ours): MHD comparison is qualitative and the simulation is unpublished (in prep.)
- Caveat (inferred, ours): Counts 101 vs 110 and 4 MHz vs 2 GHz continuum bandwidth are inconsistent as printed
- Caveat (inferred, ours): No uncertainties given for the headline numbers

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Full tclean parameter set and TP calibration/imaging details
- Missing: Complete FilFinder parameter file and version
- Missing: Details of line-mass averaging and YSO association rules
- Missing: Unpublished NANTEN data and MHD simulation outputs
- Data volume (inferred): Roughly 100-300 GB raw for 1501 7m mosaic pointings plus TP, uncertain
- Score (inferred): 3/5, The project code, CASA version, tclean choices and FilFinder thresholds are given, but multi-scale scales, masking and TP/feather details, line-mass averaging and the YSO association rule are missing, so the exact counts and medians would be hard to match.
- Rediscovery candidate: no, The paper does not state that the data are public, and the recipe lacks enough detail to reproduce the exact feather counts and line masses.

## Links

- Method: (cite: Tokuda21; Muraoka23) (Imaging strategy for ACA large-scale surveys)
- Method: (cite: Kepley20) (Multi-scale deconvolver with automasking)
- Method: (cite: koch15) (FilFinder algorithm)
- Method: (cite: frerking82) (C18O abundance relative to H2)
- Companion: Fukaya et al. (part 2 paper, in preparation) (Higher resolution ALMA 12m data on fragmentation and star formation in the feathers)
- Companion: Abe et al. (in prep.); (cite: abe2024) (MHD colliding-flow simulation used for comparison)
- Companion: (cite: Tokuda23Interc) (Protostellar magnetic flux transport explaining the ring-shaped feather)
- Related: Herschel Gould Belt Survey
- Related: ACA Taurus surveys (tokuda19MC5, tokuda20, fujishiro20)
- Related: NANTEN CO survey of the CrA cloud

## Checks

```json
{
 "quotes": 117,
 "quotes_ok": 117,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 102,
  "stated": 75,
  "rate": 0.735
 },
 "evidence_ok": true
}
```
