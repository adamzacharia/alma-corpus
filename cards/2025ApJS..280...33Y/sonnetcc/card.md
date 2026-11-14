# The ALMA-QUARKS Survey. III. Clump-to-core Fragmentation and Searches for High-mass Starless Cores

`2025ApJS..280...33Y` | The Astrophysical Journal Supplement Series 2025 | first author: Yang, Dongting | arXiv: 2508.03229 | DOI: 10.3847/1538-4365/adf847

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: star_formation, milky_way_ism
- Question: How do IR-bright massive protocluster clumps fragment into cores (observed core separation vs thermal Jeans length), and are there candidate high-mass starless cores among them?  
  > "This study investigates clump-to-core fragmentation and searches for candidate high-mass starless cores within IR-bright clumps using combined ALMA 12-m (C-2) and Atacama Compact Array (ACA) 7-m data" (abstract)
- Target **139 IR-bright massive protocluster clumps of the QUARKS sample (156 single pointings)**: coordinates _not stated_; z/distance median distance 3.7 kpc; per-source distances in the core table  
  > "we observed in the QUARKS survey 139 IR-bright massive protocluster clumps" (2.1 QUARKS sample and ALMA observations); "is the distance for each source, adopted from (cite: 2024RAA....24b5009L)" (3.3 Physical parameters of dense cores); "at a median distance of 3.7 kpc for the QUARKS survey" (2.3 Continuum imaging with self-calibration); distance from adopted from (cite: 2024RAA....24b5009L)  
  > "we observed in the QUARKS survey 139 IR-bright massive protocluster clumps" (2.1 QUARKS sample and ALMA observations); "is the distance for each source, adopted from (cite: 2024RAA....24b5009L)" (3.3 Physical parameters of dense cores); "at a median distance of 3.7 kpc for the QUARKS survey" (2.3 Continuum imaging with self-calibration)

## Data provenance

- ALMA projects: 2021.1.00095.S
- bands: Band 6 (~1.3 mm), dual polarization  
  > "The ALMA band 6 receivers were used in a dual-polarization mode for the QUARKS observations." (2.1 QUARKS sample and ALMA observations)
- frequencies and spectral setup: 4 SPWs (SPW1-4), ~2 GHz bandwidth each, ~1.3 km/s velocity resolution; centred at ~217.92, 220.32, 231.37, 233.52 GHz  
  > "Four spectral windows (SPWs 1–4) were configured with a bandwidth of $\sim$2 GHz, a velocity resolution of $\sim\rm 1.3\,km\,s^{-1}$ for each SPW." (2.1 QUARKS sample and ALMA observations); "The frequencies of the four SPWs were centered at approximately 217.92 GHz, 220.32 GHz, 231.37 GHz, and 233.52 GHz, respectively." (2.1 QUARKS sample and ALMA observations)
- continuum bandwidth: all four SPWs used for continuum (line-free channels)  
  > "All four SPWs visibility data were used to ensure a rather high sensitivity for the QUARKS TM2+ACA continuum image." (2.3 Continuum imaging with self-calibration)
- arrays: ALMA 12-m (C-2, TM2) combined with ACA 7-m  
  > "using combined ALMA 12-m (C-2) and Atacama Compact Array (ACA) 7-m data" (abstract)
- configurations: TM2 = 12-m C-2 and ACA 7-m used here (QUARKS also has extended C-5 TM1, not used in this paper)  
  > "ACA 7-m array, ALMA 12-m compact array C-2 (TM2) and extended C-5 (TM1) configurations, respectively" (2.1 QUARKS sample and ALMA observations)
- baselines: ~15.1-313.7 m for TM2 (Group 1: 15.1/500.6 m)  
  > "all Groups have similar minimum and maximum baselines (BL; $\sim$ 15.1-313.7 m)" (2.1 QUARKS sample and ALMA observations)
- angular resolution: ~1 arcsec for TM2; TM2+ACA continuum beam ~1.3 x 1.1 arcsec; line beam ~1.4 x 1.1 arcsec  
  > "angular resolution (AR; $\sim$1$''$), and maximum recoverable scale (MRS; $\sim$ 11$''$)" (2.1 QUARKS sample and ALMA observations); "with an average beam size of $\sim1.3$ $''$$\times1.1$ $''$" (2.3 Continuum imaging with self-calibration)
- max recoverable scale: ~11 arcsec for TM2 (before adding ACA)  
  > "angular resolution (AR; $\sim$1$''$), and maximum recoverable scale (MRS; $\sim$ 11$''$)" (2.1 QUARKS sample and ALMA observations)
- sensitivity: continuum ~0.6 mJy/beam; line rms ~10 mJy/beam per channel (~0.2 K)  
  > "the average noise level of the reduced TM2+ACA continuum data is $\sim\rm 0.6\,mJy\,beam^{-1}$" (2.3 Continuum imaging with self-calibration); "the average rms level of the reduced line data is $\sim \rm 10\,mJy\,beam^{-1}$ ($\sim \rm 0.2\,K$) per channel" (2.4 Line Imaging)
- time on source: _not stated_
- observing dates: TM2: 9 April 2022 to 22 March 2024 (ACA first completed late May 2022)  
  > "starting on April 9, 2022, and completed on March 22, 2024" (2.1 QUARKS sample and ALMA observations); "ACA observations were first completed in late May 2022" (2.1 QUARKS sample and ALMA observations)
- pi or archival as stated: PI observations of the QUARKS survey (PIs: Lei Zhu, Guido Garay, Tie Liu)  
  > "The QUARKS survey (PIs: Lei Zhu, Guido Garay, and Tie Liu; Project ID: 2021.1.00095.S" (2.1 QUARKS sample and ALMA observations)
- Line: N2D+ 3-2 (not stated)
- Line: CO 2-1 (not stated)
- Line: SiO 5-4 (not stated)
- Line: CH3CN 12-11 (not stated)
- Line: H30alpha recombination line (ionized gas tracer) (not stated)
- Other facility **ALMA ATOMS survey (Band 3, ~3 mm)**: 3 mm continuum and H40alpha comparison images; clump parameters; catalog of ATOMS 'unknown' sources cross-matched with QUARKS cores  
  > "a comparison of continuum images between the 3 mm ATOMS data (left panels) and the 1.3 mm QUARKS TM2+ACA data (right panels) for two example targets" (3.1 Core extraction)
- Other facility **MeerKAT 1.3 GHz radio continuum**: cross-match to check free-free contamination of the 27 cores above 100 Msun  
  > "From the cross-match between these cores and MeerKAT 1.3 GHz radio continuum arising from free-free emission" (Appendix: Physical parameters)
- External data: Per-source distances to the clumps  
  > "is the distance for each source, adopted from (cite: 2024RAA....24b5009L)" (3.3 Physical parameters of dense cores) [from (cite: 2024RAA....24b5009L)]
- External data: Clump number densities and dust temperatures (clump SED-derived) used for Jeans length and starless upper-limit temperature  
  > "Using physical parameters from Table A1 in (cite: 2020MNRAS.496.2790L), we find that the clump number densities range from" (3.5 Analysis of thermal Jeans length) [from (cite: 2020MNRAS.496.2790L), Table A1; SED method (cite: 2004A&A...426...97F)]
- External data: Dust opacity kappa = 0.9 cm2/g at 1.3 mm  
  > "is taken as 0.9 $\rm cm^{2}\,g^{-1}$ (cite: 1994A&A...291..943O)" (3.3 Physical parameters of dense cores) [from (cite: 1994A&A...291..943O)]
- External data: Warm-core dust temperature of 30 K  
  > "For candidate warm cores, a dust temperature of 30 K was adopted (cite: 2023MNRAS.520.2306T)" (3.3 Physical parameters of dense cores) [from (cite: 2023MNRAS.520.2306T)]
- External data: Laboratory spectral line database used to build the model spectrum for line-free channel identification  
  > "matching the ALMA pipeline reduced datacube with the laboratory database of spectral lines (CDMS; (cite: 2001A&A...370L..49M))" (2.2.1 Data Flag and Basic Setups of Data Reduction) [from CDMS (cite: 2001A&A...370L..49M)]
- External data: ATOMS 'unknown' source catalog (280 compact fragments) used for cross-match  
  > "identified 280 compact fragments lacking signatures of HMCs or UCHii regions" (4.2 Comparison with ATOMS unknown source catalog) [from (cite: 2021MNRAS.505.2801L)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline-reduced datacube used to identify lines; continuum self-calibration done manually and iteratively (the calibration of the raw data itself is not described)  
  > "matching the ALMA pipeline reduced datacube with the laboratory database of spectral lines" (2.2.1 Data Flag and Basic Setups of Data Reduction); "Self-calibration was carried out manually and iteratively to optimize the cleaning thresholds" (2.3 Continuum imaging with self-calibration)
- casa version: CASA 6.6.0 (used for combining and imaging)  
  > "Common Astronomy Software Applications (CASA, version 6.6.0" (2.2 Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Bandpass/Flux calibrators listed per Group in the observation table (Col. 9)  
  > "The phase and bandpass calibrators are listed in Column 8 and Column 9 of Table" (2.1 QUARKS sample and ALMA observations)
- flux scale uncertainty: _not stated_
- self calibration: three rounds of phase self-calibration on continuum (hogbom), calibration tables later applied to line data  
  > "we performed three rounds of phase self-calibration" (2.3 Continuum imaging with self-calibration); "we applied to four SPWs all the calibration tables from three rounds of continuum self-calibration" (2.4 Line Imaging)

### Imaging

- task: CASA tclean on concatenated TM2+ACA visibilities (continuum and lines)  
  > "The combined imaging processes of both continuum and lines were performed using the CASA task *tclean*, with a *briggs* robust weighting of 0.5." (2.2.1 Data Flag and Basic Setups of Data Reduction)
- deconvolver: hogbom during phase self-cal rounds; mtmfs (nterm=2) for final continuum; multiscale for line cubes  
  > "we selected the *hogbom* deconvolving algorithm" (2.3 Continuum imaging with self-calibration); "the Multi-Term Multi-Frequency Synthesis (*mtmfs*) with an *nterm* of 2 was employed for the last *tclean* procedure" (2.3 Continuum imaging with self-calibration); "with the *mutilscale* deconvolution approach and a uniform cleaning threshold of 25$\,\rm mJy\,beam^{-1}$" (2.4 Line Imaging)
- weighting robust: briggs, robust = 0.5  
  > "with a *briggs* robust weighting of 0.5" (2.2.1 Data Flag and Basic Setups of Data Reduction)
- uv taper: _not stated_
- cell size: 0.15 arcsec (Group 1); 0.2 arcsec (Groups 2-15)  
  > "the image size for each field in Group 1 was set to be \[300, 300\] pixels, with a pixel size of 0.15$''$" (2.2.1 Data Flag and Basic Setups of Data Reduction); "for the fields in Groups 2-15 each image was set to have \[250, 250\] pixels, with a pixel size of 0.2$''$" (2.2.1 Data Flag and Basic Setups of Data Reduction)
- image size: 300x300 pixels (Group 1); 250x250 pixels (Groups 2-15)  
  > "the image size for each field in Group 1 was set to be \[300, 300\] pixels, with a pixel size of 0.15$''$" (2.2.1 Data Flag and Basic Setups of Data Reduction); "for the fields in Groups 2-15 each image was set to have \[250, 250\] pixels, with a pixel size of 0.2$''$" (2.2.1 Data Flag and Basic Setups of Data Reduction)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in the uv plane, linear fit (fitorder=1), line-free channels  
  > "employing the CASA task *uvcontsub* with a linear fitting (fitorder=1)" (2.2.1 Data Flag and Basic Setups of Data Reduction)
- line free channels: automatic selection from CDMS model spectrum shifted to field Vlsr and widened to 50 km/s, then manually re-identified per field with Linemarker; the channel lists are not given  
  > "we shifted the model spectrum and expanded it to a width of 50 $\rm km\,s^{-1}$" (2.2.1 Data Flag and Basic Setups of Data Reduction); "we manually reidentified the line-free channels for each field based on the TM2+ACA first version data using *Linemarker*" (2.2.1 Data Flag and Basic Setups of Data Reduction)
- primary beam correction: pblimit = 0.2 in tclean; getsf run on images without primary beam correction, with getsf fluxes then corrected for the primary beam response  
  > "The image cleaning procedure was conducted with in *pblimit* of 0.2 in each field." (2.2.1 Data Flag and Basic Setups of Data Reduction); "the *getsf* was applied to images without primary beam correction" (3.1 Core extraction)
- array combination: ACA and TM2 raw visibilities concatenated (concat) and imaged jointly; two-pointing clumps mosaicked except I12572-6316 and I17269-3312  
  > "the raw visibility data for the QUARKS ACA and TM2 observations were first concatenated using the CASA task *concat*" (2.2.1 Data Flag and Basic Setups of Data Reduction); "For 15 of them, we made the mosaic before imaging." (2.2.1 Data Flag and Basic Setups of Data Reduction)
- smoothing: _not stated_
- final beam: continuum ~1.3 x 1.1 arcsec; line cubes ~1.4 x 1.1 arcsec (averages)  
  > "with an average beam size of $\sim1.3$ $''$$\times1.1$ $''$" (2.3 Continuum imaging with self-calibration); "at an average synthesized beam of $\sim 1.4$ $''$$\times1.1$ $''$" (2.4 Line Imaging)
- final rms: continuum ~0.6 mJy/beam; line ~10 mJy/beam per channel at ~1.3 km/s  
  > "the average noise level of the reduced TM2+ACA continuum data is $\sim\rm 0.6\,mJy\,beam^{-1}$" (2.3 Continuum imaging with self-calibration); "the average rms level of the reduced line data is $\sim \rm 10\,mJy\,beam^{-1}$ ($\sim \rm 0.2\,K$) per channel" (2.4 Line Imaging)

### Inherited from earlier work

- Line-free channel identification method (CDMS-matched model spectrum)  
  > "we followed the method developed by (cite: 2024RAA....24b5009L) for the QUARKS survey" (2.2.1 Data Flag and Basic Setups of Data Reduction) [from (cite: 2024RAA....24b5009L)]
- ALMA configurations and observing details deferred to the QUARKS overview paper  
  > "see Table 1 in (cite: 2024RAA....24b5009L)" (2.1 QUARKS sample and ALMA observations) [from (cite: 2024RAA....24b5009L)]
- Minimum core radius of half the beam size to mitigate deconvolution artifacts  
  > "was enforced, following (cite: 2022A&A...664A..26P)" (3.3 Physical parameters of dense cores) [from (cite: 2022A&A...664A..26P)]
- Monte Carlo uncertainty propagation for mass, density and surface density  
  > "using the Monte Carlo approach as adopted in (cite: 2024ApJ...974..239S)" (3.3 Physical parameters of dense cores) [from (cite: 2024ApJ...974..239S)]
- Projection correction factor 4/pi applied to core separations  
  > "consider the factor of $4/\pi$, e.g., (cite: 2024ApJ...974...95I)" (3.5 Analysis of thermal Jeans length) [from (cite: 2024ApJ...974...95I)]
- Cold-gas upper-level energy criterion (Eu below 22 K) for candidate starless cores  
  > "with upper energy levels ($E_u$) below 22 K (cite: 2019ApJ...886..102S)" (3.2.1 Candidate starless and warm cores) [from (cite: 2019ApJ...886..102S)]

### Not stated but needed to reproduce (our reading)

- Per-field line-free channel lists (the manual Linemarker step cannot be repeated without them)
- Self-calibration solution intervals, per-round cleaning thresholds, masks and number of iterations per field for the continuum
- tclean multiscale scales, continuum cleaning thresholds, niter and spectral-cube channel/velocity gridding for each field
- getsf version and configuration beyond min/max size (e.g. filtering scales, background settings) and the exact edge-exclusion rule
- How the original ALMA data were calibrated (pipeline version / manual scripts) and which products were used
- Per-clump Vlsr used to shift the model spectrum
- Method and thresholds for identifying CO outflows and H30alpha detections for each core (flagging as star-forming signatures)
- How cores are assigned to clumps for the MST and how clump density, temperature and Jeans length were computed per clump (exact density-to-length chain, mean molecular weight for c_s)
- Velocity dispersions adopted for the virial parameter of the two high-mass starless candidates
- Full per-core table values behind the starless/warm/evolved medians (only partial tables printed)

## Analysis recipe

1. **Concatenate ACA+TM2 and set line-free channels**: Concatenate visibilities; auto-flag line channels from CDMS-matched model spectrum (width 50 km/s around Vlsr); uvcontsub; first tclean; then manual re-identification of line-free channels with Linemarker and iterate  
  > "the raw visibility data for the QUARKS ACA and TM2 observations were first concatenated using the CASA task *concat*" (2.2.1 Data Flag and Basic Setups of Data Reduction); "we manually reidentified the line-free channels for each field based on the TM2+ACA first version data using *Linemarker*" (2.2.1 Data Flag and Basic Setups of Data Reduction)
   - software: CASA, Linemarker, CDMS
   - parameter: model spectrum width 50 km/s, shifted by field Vlsr  
  > "we shifted the model spectrum and expanded it to a width of 50 $\rm km\,s^{-1}$" (2.2.1 Data Flag and Basic Setups of Data Reduction)
   - parameter: uvcontsub linear fit, fitorder=1  
  > "employing the CASA task *uvcontsub* with a linear fitting (fitorder=1)" (2.2.1 Data Flag and Basic Setups of Data Reduction)
   - fitting: _not stated_
   - validation: First-version data showed skewed baselines for some fields, motivating manual line-free re-selection  
  > "the TM2+ACA first version data reveal a skewed baseline for some fields instead of a constant level" (2.2.1 Data Flag and Basic Setups of Data Reduction)
2. **Make self-calibrated continuum image**: Three rounds of phase self-calibration with hogbom tclean, final tclean with mtmfs (nterm=2) using all four SPWs  
  > "we performed three rounds of phase self-calibration" (2.3 Continuum imaging with self-calibration); "the Multi-Term Multi-Frequency Synthesis (*mtmfs*) with an *nterm* of 2 was employed for the last *tclean* procedure" (2.3 Continuum imaging with self-calibration)
   - software: CASA
   - parameter: briggs robust 0.5; pblimit 0.2; cell 0.15 arcsec (Group 1) or 0.2 arcsec (Groups 2-15)  
  > "with a *briggs* robust weighting of 0.5" (2.2.1 Data Flag and Basic Setups of Data Reduction); "The image cleaning procedure was conducted with in *pblimit* of 0.2 in each field." (2.2.1 Data Flag and Basic Setups of Data Reduction)
   - fitting: _not stated_
   - validation: Cleaning thresholds tuned manually to improve sensitivity while preventing divergence  
  > "Self-calibration was carried out manually and iteratively to optimize the cleaning thresholds" (2.3 Continuum imaging with self-calibration)
3. **Make line cubes**: Apply continuum self-cal tables, uvcontsub, then tclean multiscale with a uniform threshold  
  > "we applied to four SPWs all the calibration tables from three rounds of continuum self-calibration" (2.4 Line Imaging); "with the *mutilscale* deconvolution approach and a uniform cleaning threshold of 25$\,\rm mJy\,beam^{-1}$" (2.4 Line Imaging)
   - software: CASA
   - parameter: cleaning threshold 25 mJy/beam (~0.4 K) for all fields  
  > "with the *mutilscale* deconvolution approach and a uniform cleaning threshold of 25$\,\rm mJy\,beam^{-1}$" (2.4 Line Imaging)
   - fitting: _not stated_
   - validation: _not stated_
4. **Extract compact cores from 1.3 mm continuum**: getsf run on the continuum image without primary beam correction, minimum/maximum source size half and three times the beam; post-select on SIGNM > 5 and GOODM > 1, excluding edge cores  
  > "to identify compact structures within the TM2+ACA continuum data at 1.3 mm" (3.1 Core extraction); "we set the minimum and maximum sizes of the extracted compact sources to half and three times the synthesized beam size, respectively" (3.1 Core extraction); "we retained only the cores with a significance level (*SIGNM*; detection significance from monochromatic single scales) greater than 5" (3.1 Core extraction)
   - software: getsf
   - parameter: GOODM greater than unity  
  > "a goodness (*GOODM*; monochromatic goodness combining significance and signal-to-noise ratio) greater than unity" (3.1 Core extraction)
   - fitting: _not stated_
   - validation: Reliability via getsf quality parameters; admitted that a few weak peaks are missed  
  > "a few potential sources could be still missing" (3.1 Core extraction)
5. **Classify cores by evolutionary stage**: Count line peaks above 3 sigma in core-averaged spectra (N_line), combine with CO outflows and H30alpha: starless (N_line<=6, no outflow/H30alpha), warm (6<N_line<=15 or N_line<=6 with outflow, no H30alpha), evolved (HMC, UCHii-h, UCHii-l)  
  > "we identified the number of line emission peaks from the core-averaged spectra exceeding a $3\sigma$ noise level across the four SPWs" (3.2 Classification of cores); "candidate starless cores are required to only have such cold gas emission of lines with $N_{\rm line} \leq 6$" (3.2.1 Candidate starless and warm cores); "the number of emission lines for candidate warm cores to be $6 < N_{\rm line} \leq 15$" (3.2.1 Candidate starless and warm cores)
   - software: CASA
   - parameter: 1 sigma = std of line-free channel amplitudes per core (~20 mJy/beam on average)  
  > "The $1\sigma$ noise level was calculated as the standard deviation of the amplitudes in the line-free emission channels for each core" (3.2 Classification of cores)
   - assumption: Candidate starless cores lack outflows (CO) and ionized gas (H30alpha)  
  > "such candidates should lack any star formation signatures, such as outflows traced by CO emission or ionized gas by H30$\alpha$ emission" (3.2.1 Candidate starless and warm cores)
   - fitting: _not stated_
   - validation: Checked starless candidates for broad line wings in H2CO and DCN spectra; none seen  
  > "no broad line-wings were observed in the spectral line profiles (not shown here)" (3.2.1 Candidate starless and warm cores)
6. **Derive core masses, densities and surface densities**: Optically thin dust mass at 1.3 mm with class-dependent T_dust; spherical geometry for n_H2 and surface density; deconvolved radius from getsf sizes; Monte Carlo uncertainties  
  > "Assuming dust continuum emission at 1.3 mm to be optically thin, the masses of the cores can be estimated as follows" (3.3 Physical parameters of dense cores); "a minimum radius of half the beam size ($\sim0.5$ $''$) was enforced" (3.3 Physical parameters of dense cores)
   - parameter: T_dust: starless 20 K lower limit to clump average (upper limit); warm 30 K; evolved 100 K  
  > "we adopted here a lower limit of temperature of 20 K for all candidate starless cores" (3.3 Physical parameters of dense cores); "For candidate warm cores, a dust temperature of 30 K was adopted" (3.3 Physical parameters of dense cores); "Finally, for candidate evolved cores, we assumed a dust temperature of 100 K" (3.3 Physical parameters of dense cores)
   - parameter: kappa = 0.9 cm2/g  
  > "is taken as 0.9 $\rm cm^{2}\,g^{-1}$ (cite: 1994A&A...291..943O)" (3.3 Physical parameters of dense cores)
   - assumption: gas-to-dust ratio 100  
  > "is the gas-to-dust ratio, assumed to be 100" (3.3 Physical parameters of dense cores)
   - assumption: mean molecular weight mu = 2.8; spherical geometry  
  > "Assuming a spherical geometry, the number density of the cores was calculated as" (3.3 Physical parameters of dense cores); "where $\mu = 2.8$ is the mean molecular weight" (3.3 Physical parameters of dense cores)
   - fitting: _not stated_
   - validation: Uncertainty ~50% for mass, density and surface density via Monte Carlo  
  > "we estimated the uncertainty of mass, number density, and surface density of $\rm\sim 50\%$, using the Monte Carlo approach as adopted in (cite: 2024ApJ...974..239S)" (3.3 Physical parameters of dense cores)
7. **Measure core separations**: Minimum spanning tree of core positions within each clump; linear separations from distance; separations treated as lower limits due to projection  
  > "method was used to determine the shortest separation between the cores within each clump" (3.4 Core Separation); "the measured core separations could represent lower limits due to projection effects, with actual values being potentially 1–2 times greater" (3.4 Core Separation)
   - fitting: _not stated_
   - validation: Distance dependence of separations assessed with Spearman tests; attributed to observational effects  
  > "This reflects an observational effect rather than a physical phenomenon" (3.4 Core Separation)
8. **Compare separations with thermal Jeans length**: Compute thermal Jeans length per clump from SED-derived clump density and temperature (Liu et al. 2020), form lambda_obs/lambda_J, apply 4/pi projection correction  
  > "These conditions yield Jeans lengths ($\lambda_{\rm J}=c_s(\pi/G\rho)^{1/2}$) of $\rm\sim [0.07, 1.1]\,pc$" (3.5 Analysis of thermal Jeans length); "consider the factor of $4/\pi$, e.g., (cite: 2024ApJ...974...95I)" (3.5 Analysis of thermal Jeans length)
   - assumption: Clump number densities ~1e3-1e5 cm-3 and dust temperatures 19.5-45.5 K from literature  
  > "Using physical parameters from Table A1 in (cite: 2020MNRAS.496.2790L), we find that the clump number densities range from" (3.5 Analysis of thermal Jeans length)
   - fitting: _not stated_
   - validation: Ratio less distance-dependent than lambda_obs or lambda_J alone (Spearman tests)  
  > "Both $\lambda_{\rm obs}$ and $\lambda_{\rm J}$ exhibit positive correlations with source distance" (3.5 Analysis of thermal Jeans length)
9. **Search for high-mass starless core candidates**: Select starless cores with M >= 16 Msun at 20 K (assuming 50% star formation efficiency); check virial parameter with literature velocity dispersions  
  > "only two candidates (with $M_{\rm core} \geq 16\,M_{\odot}$ at $T_{\rm d} = 20\,\rm K$) could potentially form high-mass stars independently" (4.3 Search for candidate high-mass starless cores); "we find $\alpha_{\rm vir} < 2$ for the two candidates studied here" (4.3 Search for candidate high-mass starless cores)
   - parameter: star formation efficiency 50%  
  > "Assuming a star formation efficiency of 50% as adopted in (cite: 2018A&A...618L...5N)" (4.3 Search for candidate high-mass starless cores)
   - assumption: total velocity dispersion ~0.4-0.8 km/s from literature high-mass prestellar cores  
  > "Considering typical total velocity dispersions of high-mass prestellar cores in the literature" (4.3 Search for candidate high-mass starless cores)
   - fitting: _not stated_
   - validation: CO outflow maps and line spectra of the two candidates shown  
  > "Line spectra of the two candidate cores and detection maps of CO outflows within their natal clumps are shown in Figures" (4.3 Search for candidate high-mass starless cores)
10. **Cross-match with ATOMS unknown sources**: Cross-match 280 ATOMS unknown sources with the 1562 QUARKS cores (Venn diagram)  
  > "while the remaining 211 correspond to 464 QUARKS cores" (4.2 Comparison with ATOMS unknown source catalog)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.6.0: concat, flag, uvcontsub, tclean, self-calibration of combined TM2+ACA data  
  > "Common Astronomy Software Applications (CASA, version 6.6.0" (2.2 Data Reduction)
- **getsf** : compact core extraction in 1.3 mm continuum  
  > "to identify compact structures within the TM2+ACA continuum data at 1.3 mm" (3.1 Core extraction)
- **Linemarker** : manual identification of line-free channels  
  > "we manually reidentified the line-free channels for each field based on the TM2+ACA first version data using *Linemarker*" (2.2.1 Data Flag and Basic Setups of Data Reduction)
- **CDMS** : laboratory line database to build the model spectrum for automatic line-free channel selection  
  > "matching the ALMA pipeline reduced datacube with the laboratory database of spectral lines" (2.2.1 Data Flag and Basic Setups of Data Reduction)
- **ALMA pipeline** : pipeline-reduced datacube used to identify lines for the model spectrum  
  > "matching the ALMA pipeline reduced datacube with the laboratory database of spectral lines" (2.2.1 Data Flag and Basic Setups of Data Reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of compact cores extracted | 1562 | not stated | cores | 4 | a total of 1562 compact structures (i.e., cores) were identified across 156 fields |
| Candidate starless cores | 127 (8.1%) | not stated | cores | 5 | 127 (8.1%) out of 1562 cores were finally classified as candidate starless cores |
| Candidate warm cores | 971 (62.2%) | not stated | cores | 5 | 971 cores (62.2%) were identified as candidate warm cores |
| Candidate evolved cores | 464 (~30%) | not stated | cores | 5 | the remaining 464 cores ($\sim$30%) were classified as evolved cores |
| Candidate hot molecular cores (HMCs) | 314 | not stated | cores | 5 | 314 candidate HMCs without associated |
| UCHii-h candidate cores | 63 | not stated | cores | 5 | 63 UCHii-*h* candidates with associated |
| UCHii-l candidate cores | 87 | not stated | cores | 5 | 87 UCHii-*l* candidates with associated |
| Average continuum noise (TM2+ACA) | ~0.6 | not stated | mJy/beam | 2 | the average noise level of the reduced TM2+ACA continuum data is $\sim\rm 0.6\,mJy\,beam^{-1}$ |
| Continuum mass sensitivity at 30 K and median distance 3.7 kpc | ~0.3 | not stated | Msun | 2 | corresponding to a mass sensitivity of $\sim 0.3$ $M_{\odot}$ for a 30 K dust temperature |
| Average line rms per channel | ~10 | not stated | mJy/beam | 3 | the average rms level of the reduced line data is $\sim \rm 10\,mJy\,beam^{-1}$ ($\sim \rm 0.2\,K$) per channel |
| Starless core masses at 20 K: range and median | 0.2-21.0 (median 1.5) | ~50% (per-core mass) | Msun | 6 | candidate starless cores have masses (at 20 K) ranging from \[0.2–21.0\] M$_{\odot}$, with a median of 1.5 M$_{\odot}$ |
| Median radius of candidate starless cores (20 K) | 2800 | not stated | au | 6 | The median radius, number density, and surface density of candidate starless cores are 2800 au, $2.0 \times 10^6$ cm$^{-3}$, and 0.5 g cm$^{-2}$, respectively |
| Median number density of candidate starless cores (20 K) | 2.0e6 | not stated | cm^-3 | 6 | The median radius, number density, and surface density of candidate starless cores are 2800 au, $2.0 \times 10^6$ cm$^{-3}$, and 0.5 g cm$^{-2}$, respectively |
| Median surface density of candidate starless cores (20 K) | 0.5 | not stated | g cm^-2 | 6 | The median radius, number density, and surface density of candidate starless cores are 2800 au, $2.0 \times 10^6$ cm$^{-3}$, and 0.5 g cm$^{-2}$, respectively |
| Angular core separation range | 0.9-17.9 | not stated | arcsec | 7 | spanning \[0.9, 17.9\] $''$ (corresponding to $\rm [0.005, 0.72]\,pc$) |
| Peak of angular separation distribution | 2.5 | not stated | arcsec | 7 | The distribution peaks at 2.5 $''$ |
| Peak of linear core separation distribution | ~0.05 | not stated | pc | 7 | the peak of the core separation distribution at $\sim$0.05 pc |
| Clump thermal Jeans length range | ~0.07-1.1 | not stated | pc | 8 | These conditions yield Jeans lengths ($\lambda_{\rm J}=c_s(\pi/G\rho)^{1/2}$) of $\rm\sim [0.07, 1.1]\,pc$ |
| lambda_obs/lambda_J without projection correction: fraction below 1 and peak | ~99% (1407/1421) below 1; peak ~0.1 | not stated | dimensionless | 8 | Almost all ratios ($\sim99\%$, 1407/1421) are below 1, peaking at $\sim\rm 0.1$ |
| lambda_obs/lambda_J with 4/pi projection correction: fraction below 1 and peak | ~98% (1391/1421) below 1; peak ~0.2 | not stated | dimensionless | 8 | shows that $\sim98\%$ (1391/1421) of the ratios remain below unity, with a peak at $\sim\rm 0.2$ |
| High-mass starless candidates (>=16 Msun at 20 K): radii and masses | 2 cores; radii 5000-7000 au; masses 17-21 Msun | not stated | au; Msun | 9 | which have radii of 5000–7000 au and masses of 17–21 M$_{\odot}$ |
| Virial parameter of the two high-mass starless candidates | < 2 | not stated | dimensionless | 9 | we find $\alpha_{\rm vir} < 2$ for the two candidates studied here |
| Fraction of candidate starless cores with M <= 8 Msun | 90% | not stated | percent | 9 | we find that 90% of candidate starless cores ($M_{\rm core} \leq 8\,M_{\odot}$) lack sufficient mass |
| ATOMS unknown sources inside QUARKS field and number of matching QUARKS cores | 211 sources correspond to 464 QUARKS cores | not stated | counts | 10 | while the remaining 211 correspond to 464 QUARKS cores |

## Qualitative findings

- Thermal Jeans fragmentation has occurred in the IR-bright protocluster clumps, with core separations well below the thermal Jeans length  
  > "This indicates that thermal Jeans fragmentation has taken place within the IR-bright protocluster clumps studied here." (abstract)
- Few high-mass starless candidates favour competitive accretion over turbulent core accretion in these clumps  
  > "The scarcity of such candidates suggests that competitive accretion-type models could be more applicable than turbulent core accretion-type models" (abstract)
- Linear separation dependence on distance is an observational effect  
  > "This reflects an observational effect rather than a physical phenomenon" (3.4 Core Separation)
- Total flux increases with core evolution but mass, radius, density and surface density show no significant differences between categories  
  > "no significant differences are observed in other parameters" (3.3 Physical parameters of dense cores)

## Claim tuples

- H: Fragmentation of IR-bright protocluster clumps into cores follows thermal Jeans fragmentation | E: Extract cores with getsf, measure MST separations, compare with clump thermal Jeans length | R: lambda_obs/lambda_J peaks at ~0.2 (after projection correction) with ~98% of ratios below unity | F: Thermal Jeans fragmentation has taken place; the low ratio may come from evolving core separation or hierarchical fragmentation | **supported**
- H: Cores in the QUARKS clumps span a range of evolutionary stages that can be separated using line richness, outflows and ionized gas | E: Classify 1562 cores using N_line, CO outflows and H30alpha emission | R: 127 starless, 971 warm, 464 evolved cores | F: Most cores already show star-formation signatures; starless cores are a small minority | **supported**
- H: High-mass starless cores exist in IR-bright clumps in numbers that would favour turbulent core accretion | E: Mass of starless cores at 20 K compared with a 16 Msun threshold; virial check | R: Only two starless cores exceed 16 Msun (17-21 Msun); 90% have M <= 8 Msun | F: Scarcity of candidates suggests competitive accretion-type models are more applicable; candidate count is a lower limit | **partially**
- H: Observed linear core separation depends on source distance for physical reasons | E: Compare separations, minimum core mass and core counts versus distance (Spearman tests) | R: Linear separation grows with distance; ratio to Jeans length is weakly distance dependent | F: Distance trend is an observational effect of sensitivity and linear resolution | **supported**

## Reasoning

- Why this data: Evolved IR-bright clumps may harbour more massive starless cores, motivating a search beyond IR-dark clouds  
  > "This finding motivates searches for high-mass starless cores not only in IR-dark clouds but also in more evolved IR-bright environments." (1 Introduction)
- Why this method: Core separation is used instead of mass-based Jeans mass because mass estimates carry large uncertainties  
  > "core separation could serve as a more suitable proxy for analyzing fragmentation properties in clumps" (3.4 Core Separation)
- Alternative: Half-beam vs one-beam minimum size for getsf: half-beam chosen to recover weaker cores for a complete fragment sample  
  > "the choice of minimum size (whether half- or one-beam size) does not significantly influence the parameters (e.g., size, flux) of the extracted sources with strong emission" (3.1 Core extraction)
- Alternative: Lower starless dust temperature of 10-15 K would move six cores from 8-16 Msun to above 16 Msun  
  > "this would shift the masses of six cores (i.e., $8-16\,M_{\odot}$ at 20 K) to values greater than 16 $M_{\odot}$" (4.3 Search for candidate high-mass starless cores)
- Alternative: Hierarchical fragmentation (clump to subclumps to cores) as alternative to evolving core separation for the low lambda_obs/lambda_J  
  > "An alternative explanation for the observed $\lambda_{\rm obs}/\lambda_{\rm J} \sim 0.2$ significantly below unity could be due to the existence of a hierarchical fragmentation mode within the clumps." (4.1 Fragmentation of Protocluster clumps)
- How they decided it was enough: Each clump has enough cores (4 to 33, with two exceptions of 3) for fragmentation analysis  
  > "our clump sample contains 4 to 33 cores, which provides rather sufficient core numbers for our following fragmentation analysis" (3.1 Core extraction)
- Limitation (authors): A few weak continuum peaks are missed by getsf  
  > "a few potential sources could be still missing" (3.1 Core extraction)
- Limitation (authors): Core separations are lower limits owing to projection  
  > "the measured core separations could represent lower limits due to projection effects" (3.4 Core Separation)
- Limitation (authors): N_line can be underestimated for line-rich cores  
  > "could be underestimated for cores having a large number of complex molecular transitions" (3.2 Classification of cores)
- Limitation (authors): Free-free emission may inflate the 1.3 mm flux and masses of 27 cores above 100 Msun  
  > "The 1.3 mm flux of these 27 cores could be significantly affected by free-free emission, potentially leading to mass overestimation." (Appendix: Physical parameters)
- Limitation (authors): 1.3 mm high-resolution data trace core kernels and filter out envelope mass, so high-mass candidates are a lower limit  
  > "primarily trace dense kernels of cores, likely filtering out significantly their envelope mass" (4.3 Search for candidate high-mass starless cores)
- Caveat (inferred, ours): Dust temperatures are assigned by core class rather than measured, so the 16 Msun threshold and starless counts depend on T = 20 K
- Caveat (inferred, ours): Starless classification relies on N_line<=6 and absence of CO outflow and H30alpha, limited by 1 arcsec resolution and sensitivity
- Caveat (inferred, ours): Virial parameters use velocity dispersions borrowed from the literature rather than QUARKS measurements
- Caveat (inferred, ours): Core-scale separations are compared with clump-scale Jeans lengths built from lower-resolution ATOMS-era clump parameters
- Caveat (inferred, ours): Single ALMA configuration pair (TM2+ACA); TM1 data not used so close cores below ~1 arcsec are unresolved
- Caveat (inferred, ours): Distance-dependent mass completeness may bias separation statistics

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: Linemarker tool (third-party, hosted on gitee) used for line-free channel selection; no new code from this paper stated  
  > "A tool for manually identifying the line-free or line-emission channels in an astronomical spectrum." (Footnote 1); "https://gitee.com/liuxunchuan/linemarker" (Footnote 1)
- Missing: Per-field line-free channel lists and Linemarker choices
- Missing: Self-calibration and continuum cleaning parameters per field
- Missing: getsf configuration files and version
- Missing: Per-core line detections used for N_line, outflow and H30alpha flags
- Missing: Per-clump density and temperature inputs (from another paper) for the Jeans lengths
- Missing: Complete core catalogue (tables printed only as excerpts)
- Data volume (inferred): Several TB of raw visibilities for 156 fields of TM2+ACA with four SPWs; roughly tens of GB per field after imaging cubes, much less for continuum-only reproduction of a few fields
- Score (inferred): 3/5, ALMA project code and software (CASA 6.6.0, getsf) are given and the physical-parameter recipe is clear, but manual line-free channel selection, self-calibration settings and getsf configuration are not given.
- Rediscovery candidate: no, Results are numeric and the project code is stated, but the manual Linemarker channel selection, self-calibration and getsf details are missing, so counts such as 1562 cores cannot be matched exactly.

## Links

- Method: (cite: 2024RAA....24b5009L) (QUARKS survey overview: observations, line-free channel method, distances)
- Method: (cite: 2024RAA....24f5011X) (QUARKS ACA data and clump sample)
- Method: (cite: 2021A&A...649A..89M) (getsf core extraction algorithm)
- Method: (cite: 2022A&A...664A..26P) (core radius definition and minimum size)
- Companion: (cite: 2020MNRAS.496.2790L) (ATOMS survey and clump parameters (Table A1))
- Companion: (cite: 2021MNRAS.505.2801L) (ATOMS cores, N_line and unknown-source catalog)
- Companion: (cite: 2024ApJS..270....9X) (ALMA study of core separations in IR-bright clumps)
- Companion: (cite: 2024ApJ...976..241Y) (QUARKS study of I08448-4343)
- Related: QUARKS (2021.1.00095.S)
- Related: ATOMS
- Related: ALMA-IMF
- Related: ALMAGAL
- Related: ALMA-ASHES

## Checks

```json
{
 "quotes": 170,
 "quotes_ok": 170,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 24,
 "numeric_problems": 0,
 "fill": {
  "facts": 119,
  "stated": 96,
  "rate": 0.807
 },
 "evidence_ok": true
}
```
