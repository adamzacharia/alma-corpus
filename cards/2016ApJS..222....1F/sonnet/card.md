# ALMA Census of Faint 1.2 mm Sources Down to ~ 0.02 mJy: Extragalactic Background Light and Dust-poor, High-z Galaxies

`2016ApJS..222....1F` | The Astrophysical Journal Supplement Series 2016 | first author: Fujimoto, Seiji | arXiv: 1505.03523 | DOI: 10.3847/0067-0049/222/1/1

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: high_z_galaxies, cosmology
- Question: What fraction of the 1.2 mm extragalactic background light is resolved by faint (down to ~0.02 mJy) ALMA sources, and what is the physical nature (clustering, optical-NIR counterparts) of these sources?  
  > "To understand the physical origin of our faint ALMA sources, we measure the galaxy bias $b_{g}$ by the counts-in-cells technique" (abstract)
- Target **67 ALMA continuum maps (66 blank-field pointings, 1 Abell 1689 cluster mosaic)**: coordinates _not stated_; z/distance A1689 z = 0.183; assumed source z = 2.5  
  > "A1689 | 1.32 | 231 (6) | 38.4-40.6" (Table 2); "We construct a mass model for the cluster data (C) of A1689 at $z = 0.183$." (3.5 Mass Model); distance from assumed median SMG redshift z = 2.5 for flux scaling and magnification  
  > "A1689 | 1.32 | 231 (6) | 38.4-40.6" (Table 2); "We construct a mass model for the cluster data (C) of A1689 at $z = 0.183$." (3.5 Mass Model)

## Data provenance

- ALMA projects: 2012.1.00602.S, 2012.1.00088.S, 2012.1.00676.S, 2011.0.00319.S, 2012.1.00261.S, 2012.1.00323.S, 2012.1.00536.S, 2012.1.00934.S, 2012.1.00610.S, 2011.0.00648.S, 2012.1.00076.S, 2011.0.00115.S, 2011.0.00232.S, 2011.0.00243.S, 2011.0.00767.S, 2012.1.00719.S, 2012.1.00953.S, 2012.A.00040.S
- bands: Band 6 (63 maps) and Band 7 (4 maps), 1.03-1.32 mm  
  > "Our data set is composed of 63 Band 6 maps and 4 Band 7 maps (Table 2)" (3 Data Analysis)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 7.5 GHz with four spectral windows (for the observations where stated)  
  > "The available 7.5 GHz bandwidth with four spectral windows was centered at an observed frequency of 290.8 GHz" (2.1 Our Data)
- arrays: 12-m array (43 antennas for NB816, 55 for NB101; 20-37 antennas for A1689)  
  > "with 43 12-m antennae array in the range of $18-650$ m baseline" (2.1 Our Data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.45''x0.33'' to 1.88''x0.90''  
  > "The final cleaned maps achieve angular resolutions of $0.45\ensuremath{''}\times0.33\ensuremath{''}$ $- 1.88\ensuremath{''}\times0.90\ensuremath{''}$." (2.3 Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: 8.5 to 95.2 uJy/beam before primary beam correction  
  > "The sensitivities of these ALMA maps range from 8.5 to 95.2 $\mu$Jy beam$^{-1}$ before the primary beam corrections." (2.3 Data Reduction)
- time on source: NB816-S-61269 ~2.3 h; NB101-S-2904 ~5.2 h; A1689 ~5.5 h; archival 6 min to 60 min per map  
  > "The total on-source observed time was $\sim$ 2.3 hours." (2.1 Our Data); "Throughout these four observing sets, the total on-source integration is $\sim5.5$ hour." (2.2.2 Cluster Data)
- observing dates: _not stated_
- pi or archival as stated: 4 maps from the authors' programs, 62 field maps and the cluster map from the ALMA archive (cycles 0-2, public by 2015 June)  
  > "4 and 62 out of which are taken from our programs and the ALMA archive, respectively." (2 Data and Reduction)
- Other facility **SXDS multi-wavelength data (XMM, CFHT, Subaru, UKIRT, Spitzer, Herschel HerMES, VLA)**: Optical-NIR to radio/X-ray counterpart catalogs and photometry in SXDS  
  > "In the SXDS region, we use published photometry catalogs in 0.5-10 keV" (6.1 Optical-NIR Counterparts)
- Other facility **HST, Spitzer, Herschel in A1689**: Optical/NIR/IR photometry and images for A1689, used for the mass model and counterparts  
  > "conducting source extractions in the optical images of $g_{475},\ r_{625},$ and $i_{775}$ bands taken with $Hubble\ Space\ Telescope$ (HST)" (3.5 Mass Model)
- External data: COBE FIRAS total 1.2 mm EBL, 22 (+14/-8) Jy/deg2  
  > "total IR EBL measurement at 1.2 mm ($22^{+14}_{-8}$ Jy deg$^{-2}$; (cite: fixsen1998))" (4.3 Contributions to the EBL) [from (cite: fixsen1998)]
- External data: Bright-source number counts at 2-10 mJy from AzTEC  
  > "we use the number counts at $2-10$ mJy obtained from a survey for six blank fields with a single-dish telescope instrument of AzTEC (cite: scott2012)" (4.3 Contributions to the EBL) [from (cite: scott2012)]
- External data: ALMA 1.1 mm number counts used in the Schechter fit  
  > "those from the 1.1-mm observations with AzTEC (cite: scott2012) and ALMA (cite: carniani2015)" (4.3 Contributions to the EBL) [from (cite: carniani2015)]
- External data: Photometric redshift catalog for SXDS  
  > "as well as the photometric redshift ($z_{\rm phot}$) catalog (cite: williams2009)" (6.1 Optical-NIR Counterparts) [from (cite: williams2009)]
- External data: Multiple-image positions of A1689 used to constrain the mass model  
  > "Using the positions of the multiple images presented in the literature (cite: coe2010; diego2015)" (3.5 Mass Model) [from (cite: coe2010; diego2015)]

## Processing

### Calibration

- pipeline or manual: Standard CASA reduction using observatory-provided scripts; calibrated data from the observatory used for some cycle 0 data  
  > "Basically, the data are reduced with CASA version 4.3.0 in a standard manner with the scripts used for the data reduction provided by the ALMA observatory." (2.3 Data Reduction); "Exceptionally for the cycle 0 data with the high noise level or the patterned noise, we use the calibrated data produced by the ALMA observatory." (2.3 Data Reduction)
- casa version: CASA 4.3.0 (also 3.4 to 4.2.2 when problems arise)  
  > "we also use previous CASA versions from 3.4 to 4.2.2, if we find problems in the final image" (2.3 Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Solar-system objects and bright QSOs with 'Bulter-JPL-Horizons 2012' models and ALMA Calibrator Source Catalog  
  > "using solar-system objects and bright QSOs with the flux models of 'Bulter-JPL-Horizons 2012' and ALMA Calibrator Source Catalog, respectively" (2.3 Data Reduction)
- flux scale uncertainty: typically 10% in Bands 6 and 7  
  > "The systematic flux uncertainty is typically 10% in bands 6 and 7" (2.3 Data Reduction)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: auto CLEAN to 3 sigma of the dirty map  
  > "We process the maps with the auto CLEAN algorithm down to the depth of 3$\sigma$ noise levels of the dirty maps" (2.3 Data Reduction)
- weighting robust: natural weighting  
  > "We process the maps with the auto CLEAN algorithm down to the depth of 3$\sigma$ noise levels of the dirty maps, using natural weighting." (2.3 Data Reduction)
- uv taper: 1'' circular Gaussian taper for A1689 (beam 1.31''x1.12'') for flux measurement  
  > "we make a low-resolution map of A1689 produced with a $1''$ circular gaussian uv-taper" (3.4 Flux Measurement)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: all line-free channels of four spectral windows (selection not specified)  
  > "The continuum maps are made using all the line free channels of the four spectral windows." (2.3 Data Reduction)
- primary beam correction: _not stated_
- array combination: cluster: statwt reweighting then concat of the datasets  
  > "we recalculate the data weights with the $statwt$ task in CASA" (2.3 Data Reduction)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Summary of the Himiko and NB921-N-79144 cycle-0 observations  
  > "See (cite: ono2014) for the summary of these observations." (2.1 Our Data) [from (cite: ono2014)]
- Negative-peak analysis for spurious sources  
  > "we conduct negative peak analysis (cite: hatsukade2013; ono2014; carniani2015)" (3.2 Spurious Sources and Source Catalog) [from (cite: hatsukade2013; ono2014; carniani2015)]
- Number-count derivation method  
  > "we basically follow the methods used in the previous ALMA studies (cite: hatsukade2013; ono2014; carniani2015)" (4.1 Number Counts at 1.2 mm) [from (cite: hatsukade2013; ono2014; carniani2015)]
- A1689 mass model construction  
  > "We make the mass model with the parametric gravitational lensing package GLAFIC (cite: oguri2010) in the same manner as (cite: ishigaki2015)." (3.5 Mass Model) [from (cite: ishigaki2015)]
- Recalibrated #2011.0.00648.S data (corrected phase calibrator position)  
  > "we use a re-calibrated data provided by Seko et al. because they find that the coordinate of a phase calibrator of #2011.0.00648.S is wrong" (2.3 Data Reduction) [from (cite: hatsukade2015b)]
- Galaxy bias from correlation length for literature populations  
  > "we calculate the galaxy biases in the same manner as (cite: ono2014)" (5.2 Comparison with Other Populations) [from (cite: ono2014)]

### Not stated but needed to reproduce (our reading)

- Which channels are line-free for each map and how line contamination was excluded
- CLEAN mask, cell size, image size and number of iterations
- Exact CASA version used per dataset
- The recalibrated 2011.0.00648.S data come from private communication (Seko et al.)
- Parameters of the SExtractor extraction (detection thresholds, filters, background)
- Fitted values of the spurious-rate and completeness function parameters
- Mass model parameters and the GLAFIC best-fit values for A1689
- Bin edges and handling of the catalog for the Schechter fit and counts-in-cells fields
- Table of 133-source catalog is given but flux-to-S1.2mm conversion applied per map must be reproduced

## Analysis recipe

1. **Reduce and image ALMA data**: Standard CASA calibration with observatory scripts, natural-weighted auto-CLEAN continuum maps; statwt and concat for the cluster  
  > "We process the maps with the auto CLEAN algorithm down to the depth of 3$\sigma$ noise levels of the dirty maps, using natural weighting." (2.3 Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract sources and estimate spurious fraction**: SExtractor peak detection above 3.0 sigma in regions with >50% primary beam sensitivity; negative-peak analysis; selection at spurious rate <~70% (3.4, 3.4, 3.9 sigma for A, B, C)  
  > "We use sources down to an SNR whose spurious source rate is $\lesssim 70$%, and adopt 3.4, 3.4, and $3.9\sigma$" (3.2 Spurious Sources and Source Catalog)
   - software: SExtractor
   - parameter: Peak counts fit with a_n 10^(-b_n SNR) (+ a_p 10^(-b_p SNR)) functions; f_sp = N_np/N_pp  
  > "We estimate spurious source rates $f_{\rm sp}$ defined by the ratio of negative to positive peak numbers" (3.2 Spurious Sources and Source Catalog)
   - assumption: Sources unresolved  
  > "assuming the sources are not resolved out in our ALMA maps" (3.1 Source Detection)
   - fitting: _not stated_
   - validation: Negative-peak counts as a control  
  > "To evaluate the number of the spurious sources, we conduct negative peak analysis" (3.2 Spurious Sources and Source Catalog)
3. **Completeness and flux boosting**: Monte-Carlo injection of flux-scaled beams at random positions, SNR 3-7, 100 iterations per bin; fit 1-exp(a SNR - b)  
  > "We fit the function of $1-\exp(a {\rm SNR} -b)$ to our completeness estimates, where $a$ and $b$ are free parameters." (3.3 Completeness and Flux Boosting)
   - fitting: _not stated_
   - validation: Flux boosting ratio input/output near unity with 5% variance, so negligible  
  > "We find that the ratios of the input to output flux densities are almost unity with a variance of only 5% over the wide SNR range" (3.3 Completeness and Flux Boosting)
4. **Measure source fluxes**: imfit integrated flux for resolved sources with SNR>=5, otherwise peak flux; tapered maps for A1689; scale to 1.2 mm with modified blackbody  
  > "we use the integrated flux densities of $imfit$ only for the sources which are identified as 'resolved' with an SNR of $\geq$ 5." (3.4 Flux Measurement)
   - software: CASA imfit
   - assumption: beta_d=1.8, T_d=35 K, z=2.5  
  > "Here we assume a source redshift of $z=2.5$ that is a median redshift value of SMGs" (3 Data Analysis)
   - fitting: 2D Gaussian  
  > "We estimate the source fluxes of our 133 objects from the integrated flux densities measured with the 2D Gaussian-fitting routine of $imfit$ in CASA." (3.4 Flux Measurement)
   - validation: Flux recovery simulations with 200 Gaussian sources give ratio 0.8-1.0  
  > "we find that the flux recovery ratio (defined by the ratio of the output to input fluxes) is $1.0\pm0.1$ ($1.0\pm0.2$) for ID22 (ID55) data." (3.4 Flux Measurement)
5. **Lens model and survey area**: GLAFIC parametric mass model of A1689 with chi2 minimization on multiple images; effective area from sensitivity times magnification  
  > "we optimize free parameters of the mass profiles based on the standard $\chi^{2}$ minimization to determine the best-fit mass model" (3.5 Mass Model)
   - software: GLAFIC
   - assumption: source redshift z=2.5 for magnification  
  > "we assume our source redshift of $z = 2.5$" (3.5 Mass Model)
   - fitting: chi2 minimization  
  > "we optimize free parameters of the mass profiles based on the standard $\chi^{2}$ minimization to determine the best-fit mass model" (3.5 Mass Model)
   - validation: All multiple-image offsets within 1.0'' in image plane  
  > "all of the offsets between the model and observed positions of multiple images are within $1.0\ensuremath{''}$ in the image plane" (3.5 Mass Model)
6. **Derive number counts**: xi(S)=(1-f_sp)/(C A_eff), summed per flux bin; errors from Gehrels Poisson plus 1000 Monte-Carlo flux realizations  
  > "We repeat this processes 1000 times, and calculate the standard deviation of the number counts per flux bin caused by the flux uncertainties." (4.1 Number Counts at 1.2 mm)
   - fitting: _not stated_
   - validation: Comparison with previous ALMA and single-dish lensing counts  
  > "After the flux density scaling, all of these previous number counts agree with our measurements within the $1\sigma$ uncertainties." (4.2 Comparison with Previous Number Count Measurements)
7. **Fit Schechter function and integrate EBL**: chi2 fit of Schechter (and DPL) to our counts plus AzTEC and ALMA 1.1 mm counts; integrate above S_limit=0.015 mJy  
  > "We vary three Schechter parameters, and search for the best-fit parameter set of ($\phi_{*}$,$S_{*}$,$\alpha$) that minimizes $\chi^{2}$." (4.3 Contributions to the EBL)
   - fitting: chi2 minimization  
  > "We vary three Schechter parameters, and search for the best-fit parameter set of ($\phi_{*}$,$S_{*}$,$\alpha$) that minimizes $\chi^{2}$." (4.3 Contributions to the EBL)
   - validation: chi2/dof 16.9/19 for Schechter, 12.8/18 for DPL  
  > "the $\chi^{2}/dof$ of 16.9/19 (Table [4](#tab:ncfit_param)) indicate that the number counts are well represented by the Schechter function down to $\sim0.02$ mJy." (4.3 Contributions to the EBL)
8. **Galaxy bias**: Counts-in-cells on 66 field maps with top-hat z=1-4, sigma_V from Mo & White, 1000 Poisson mocks  
  > "We first make 1000 mock catalogs of faint ALMA sources consisting of source counts that follow the Poission probability distribution function" (5.1 Galaxy Bias of our Faint ALMA Sources)
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: Agrees with b_g<4 of Ono et al. 2014  
  > "This $1\sigma$ upper limit agrees with the previous $b_{g}$ estimate for faint ALMA sources, $b_{g}<4$, given by (cite: ono2014)." (5.1 Galaxy Bias of our Faint ALMA Sources)
9. **Counterpart identification and characterization**: Match within 1.0'' to optical-NIR catalogs in SXDS and A1689; compare colors with BX/BM, LBG, sBzK, pBzK criteria; mid-IR AGN diagram; IRX-beta  
  > "The optical-NIR counterparts are defined by the criterion that the distance between optical-NIR and ALMA source centers is within a $1.0\ensuremath{''}$." (6.1 Optical-NIR Counterparts)
   - software: SExtractor
   - fitting: _not stated_
   - validation: Chance projection probability ~10% (about 2 contaminants)  
  > "obtain $\sim10\%$ in the $P$-value (cite: downes1986). Multiplying this probability with the number of optical-NIR counterparts, 17, we expect that $\sim 2$ objects would be the foreground/background contamination." (6.1 Optical-NIR Counterparts)

## Software

- **CASA** 4.3.0: Data reduction, CLEAN imaging, statwt, concat, imfit  
  > "the data are reduced with CASA version 4.3.0 in a standard manner" (2.3 Data Reduction)
- **SExtractor** 2.5.0: Source extraction in ALMA maps and optical/NIR photometry  
  > "We conduct source extraction for our ALMA maps before primary beam corrections with SExtractor version 2.5.0" (3.1 Source Detection)
- **GLAFIC** : Parametric lens mass model of A1689  
  > "We make the mass model with the parametric gravitational lensing package GLAFIC" (3.5 Mass Model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of faint sources | 133 | not stated | sources | 2 | we obtain a source catalog consisting of 133 sources: 122 from the field data (A and B) and 11 from the cluster data (C) |
| Integrated 1.2 mm flux density above 0.015 mJy | 22.9 | +6.7/-5.6 | Jy deg^-2 | 7 | We calculate the integrated flux density to be $22.9^{+6.7}_{-5.6}$ Jy deg$^{-2}$ at 1.2 mm. |
| Resolved fraction of EBL | 104 | +31/-25 | % | 7 | find that the resolved fraction in our study is $104^{+31}_{-25}\%$ |
| Schechter faint-end slope alpha | -2.12 | +0.07/-0.06 | dimensionless | 7 | $-2.12^{+0.07}_{-0.06}$ |
| Schechter S_* | 2.35 | +0.16/-0.16 | mJy | 7 | $2.35^{+0.16}_{-0.16}$ |
| Galaxy bias upper limit | b_g < 3.5 | 1 sigma upper limit | dimensionless | 8 | we cannot obtain the measurement of $b_{g}$ but place a $1\sigma$ upper limit of $b_{g}<3.5$ for our faint ALMA sources |
| Dark halo mass upper limit | 5e12 | 1 sigma upper limit | Msun | 8 | We obtain the $1\sigma$ upper limit dark halo mass of $\lesssim 5\times10^{12}\ M_{\odot}$. |
| Optical-NIR counterpart fraction | 59 (17/29) | not stated | % | 9 | the counterpart-identification fraction that is the ratio of the total optical-NIR counterpart ALMA sources to the real ALMA sources is estimated to be 59% (=17/29) |
| Truncation flux for EBL saturation | 0.004 | not stated | mJy | 7 | We find $S_{\rm trunc}\simeq 0.004$ mJy |

## Qualitative findings

- Faint ALMA sources have optical-NIR colors, luminosities and IRX-beta consistent with sBzKs and LBGs, not scaled-down (U)LIRGs, and show no AGN signatures.  
  > "these faint ALMA sources are not miniature (U)LIRGs simply scaled down with the infrared brightness" (abstract)

## Claim tuples

- H: Faint ALMA sources resolve the 1.2 mm EBL | E: Number counts to 0.02 mJy, Schechter fit, integrate to 0.015 mJy | R: 22.9 Jy/deg2 = 104% of COBE EBL | F: Sources >=0.02 mJy are the major EBL contributors; fainter sources contribute negligibly (flattening/truncation) | **supported**
- H: Faint ALMA sources cluster like SMGs/DRGs | E: Counts-in-cells galaxy bias | R: b_g<3.5 | F: Clustering is comparable to sBzKs and LBGs, weaker than SMGs/DRGs | **supported**
- H: Faint ALMA sources are dust-poor UV-bright galaxies | E: Counterpart identification, color selection, IRX-beta | R: 59% have counterparts, most meet BX/BM/LBG or sBzK criteria | F: About half are dust-poor high-z galaxies, not miniature (U)LIRGs | **partially**

## Reasoning

- Why this data: Use all deep archival ALMA Band 6/7 data to reduce cosmic variance and increase source numbers, with criteria excluding bright sources  
  > "To increase the number of ALMA sources, we make full use of ALMA archival data of cycles 0 and 1 that became public by 2015 June." (2.2 Archival Data)
- Why this method: _not stated_
- Alternative: DPL fit also good (chi2/dof 12.8/18) but Schechter adopted for simplicity  
  > "we use the Schechter function fitting results for simplicity in the following discussion" (4.3 Contributions to the EBL)
- How they decided it was enough: _not stated_
- Limitation (authors): Remaining ~41% of faint ALMA sources have no optical-NIR counterpart and their origin is unclear  
  > "For the remaining half of the faint ALMA sources, the physical origin is unclear." (6.3.5 What are the Optical-NIR Counterparts)
- Limitation (authors): Bright-source number counts are still under debate  
  > "It should be noted that the number counts of bright sources are still under debate" (4.3 Contributions to the EBL)
- Caveat (inferred, ours): EBL fraction relies on a fixed z=2.5, T_d=35 K, beta=1.8 flux scaling across bands
- Caveat (inferred, ours): Spurious fraction up to 70% makes low-SNR sources and counterpart statistics (subtraction of 31 of 54 SXDS sources) uncertain
- Caveat (inferred, ours): Heterogeneous archival data with different beams and taper choices
- Caveat (inferred, ours): Counterpart match radius of 1'' for sources at mostly low SNR
- Caveat (inferred, ours): Counts-in-cells assumed redshift distribution and small numbers give only an upper limit

## Reproducibility

- Data public (paper): Archival ALMA cycle 0-2 data public by 2015 June  
  > "we make full use of ALMA archival data of cycles 0 and 1 that became public by 2015 June" (2.2 Archival Data)
- Products in archive: _not stated_
- Missing: Recalibrated 2011.0.00648.S data from private source
- Missing: Full CLEAN/mask settings and SExtractor configuration
- Missing: Fitted completeness and spurious-rate parameters
- Missing: GLAFIC mass model parameters
- Data volume (inferred): Large: ~120 pointings from 18 projects plus A1689 mosaic; likely several hundred GB to ~1 TB raw
- Score (inferred): 3/5, Data public and method described in detail, but several processing and model parameters are unstated and some data came privately.
- Rediscovery candidate: no, Many projects with heavy reduction and incomplete settings plus private recalibrated data and external multiwavelength catalogs make a full redo hard, though numeric results are clear.

## Links

- Method: (cite: hatsukade2013) (Negative-peak and number counts methods)
- Method: (cite: ono2014) (Number counts and galaxy bias methods, summary of Himiko observations)
- Method: (cite: oguri2010) (GLAFIC lens modelling)
- Companion: (cite: carniani2015) (Parallel ALMA multi-field number counts)
- Companion: (cite: watson2015) (A1689-zD1 observations with same cluster data)
- Related: SXDS
- Related: A1689 ALMA lensing survey
- Related: COSMOS ALMA

## Checks

```json
{
 "quotes": 100,
 "quotes_ok": 100,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 18,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 95,
  "stated": 65,
  "rate": 0.684
 },
 "evidence_ok": true
}
```
