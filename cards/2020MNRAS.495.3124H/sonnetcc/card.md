# Megaparsec-scale structure around the protocluster core SPT2349-56 at z = 4.3

`2020MNRAS.495.3124H` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Hill, Ryley | arXiv: 2002.11600 | DOI: 10.1093/mnras/staa1275

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, galaxy_clusters_and_sz
- Question: Spectroscopically confirm new members of the z=4.3 proto-cluster core SPT2349-56 with [CII] and CO(4-3), and spatially resolve the galaxies responsible for the intense star formation  
  > "which aimed to spectroscopically confirm new proto-cluster members and spatially resolve the galaxies responsible for the intense star-formation observed." (1 Introduction)
- Target **SPT2349-56 (core, northern component)**: coordinates 850-um flux-weighted centre of the core at 23:49:42.41 -56:38:23.6  
  > "flux-weighted centre at 23:49:42.41 $-$56:38:23.6" (Table 3 footnote c); "adopting the mean cluster redshift of 4.303" (3.4.2 Far-infrared luminosities); z/distance z = 4.303 (mean cluster redshift); core weighted mean 4.30280+/-0.00002  
  > "flux-weighted centre at 23:49:42.41 $-$56:38:23.6" (Table 3 footnote c); "adopting the mean cluster redshift of 4.303" (3.4.2 Far-infrared luminosities); distance from _not stated_
- Target **Red Herschel-SPIRE sources SPIREb, SPIREc, SPIREd, SPIREe**: coordinates _not stated_; z/distance SPIREc group: z = 4.28171+/-0.00018  
  > "the remaining four sources were targeted in dedicated Band 3 observations in Cycle 6" (2.2 Follow-up ALMA observations); distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00273.S, 2018.1.00058.S
- bands: Band 7 ([CII]) and Band 3 (CO(4-3)), Cycles 5 and 6  
  > "CO(4–3) transitions in Bands 7 and 3, respectively." (2.2 Follow-up ALMA observations)
- frequencies and spectral setup: [CII] placed in upper sideband (Band 7); CO(4-3) placed in lower sideband (Band 3); Cycle 6 setups similar to Cycle 5  
  > "while for the CO(4–3) observations the tuning was set to place the line in the lower sideband." (2.2 Follow-up ALMA observations); "The setup of these Band 3 observations was also chosen to be similar to that of the Cycle 5 CO(4–3) observations" (2.2 Follow-up ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Combined [CII] map beam 0.35/0.29 arcsec; combined CO(4-3) map beam 0.85/0.72 arcsec  
  > "the synthesized beam major/minor full width at half maximum (FWHM) was 0.35/0.29 arcsec." (3.1 Data reduction); "the synthesized beam major/minor FWHM was 0.85/0.72 arcsec." (3.1 Data reduction)
- max recoverable scale: _not stated_
- sensitivity: Deep CO(4-3) map 0.06 mJy/beam per 54 km/s channel; deep [CII] map 0.2 mJy/beam per 13 km/s channel  
  > "the maximum depth achieved was 0.06 mJy beam$^{-1}$ per 54 km s$^{-1}$ channel" (3.1 Data reduction); "was 0.2 mJy beam$^{-1}$ per 13 km s$^{-1}$ channel, and the synthesized beam" (3.1 Data reduction)
- time on source: _not stated_
- observing dates: ALMA Cycles 5 and 6  
  > "Here we report on a suite of new ALMA observations undertaken during Cycles 5 and 6, covering a much larger area with greater depth." (2.2 Follow-up ALMA observations)
- pi or archival as stated: _not stated_
- Line: [CII] 158 um (1900.537 GHz)
- Line: CO 4-3 (461.041 GHz)
- Other facility **South Pole Telescope (SPT)**: Discovery of SPT2349-56 in the SPT extragalactic mm-wave point-source catalogue  
  > "SPT2349$-$56 was initially discovered as part of the South Pole Telescope (SPT) extragalactic mm-wave point-source catalogue" (2.1 Selection from the South Pole Telescope survey)
- Other facility **APEX (LABOCA)**: 870-um follow-up used for flux selection and the single-dish 870-um flux density used as comparison  
  > "Of these, the brightest were followed up with the Atacama Pathfinder Experiment (APEX)" (2.1 Selection from the South Pole Telescope survey)
- Other facility **Herschel-SPIRE**: 250/350/500 um data used to identify five red sources as targets for Band 3 follow-up  
  > "identify five red *Herschel* sources surrounding SPT2349$-$56" (2.2 Follow-up ALMA observations)
- External data: 14 previously confirmed core galaxies and mean redshift 4.304 of the core  
  > "relative to the mean redshift of 4.304 reported by (cite: miller2018)" (3.2 Source extraction); "to securely identify 14 central galaxies (cite: miller2018)" (2.2 Follow-up ALMA observations) [from (cite: miller2018)]
- External data: 1.1 mm continuum flux densities re-measured from the earlier Band 7 imaging  
  > "we also give continuum flux densities at 1.1 mm independently derived from the Band 7 imaging described in (cite: miller2018) using the same method and apertures outlined above." (3.4.1 Line and continuum emission) [from (cite: miller2018)]
- External data: CO(4-3) to CO(1-0) line ratio r_{4,1} = 0.60+/-0.05  
  > "the average line strength ratio of SPT SMGs in (cite: spilker2014)" (4.2.3 Galaxy gas and halo masses) [from (cite: spilker2014)]
- External data: Gas-mass to halo-mass scaling factor of 42.8  
  > "(cite: rennehan2019) derive a scaling factor of 42.8 between gas mass and halo mass, assuming a gas mass fraction of 0.7 and a stellar mass-to-halo mass fraction of 0.01." (4.2.3 Galaxy gas and halo masses) [from (cite: rennehan2019)]
- External data: Velocity-dispersion to M200 scaling relation  
  > "We then convert this velocity dispersion into a mass using the scaling relation found by (cite: evrard2008)" (4.2.1 Mass from velocity dispersion) [from (cite: evrard2008)]
- External data: L_FIR to SFR conversion factor (Kennicutt, Chabrier IMF)  
  > "(from (cite: kennicutt1998), modified for a Chabrier initial mass function" (3.4.2 Far-infrared luminosities) [from (cite: kennicutt1998)]
- External data: Field SMG half-light sizes used for comparison  
  > "We compare our results to field SMG size measurements presented by (cite: simpson2015a)." (4.3 Far-infrared properties) [from (cite: simpson2015a)]
- External data: ALPINE comparison sample (L_IR, converted to L_FIR)  
  > "from the ALPINE survey (cite: schaerer2020)" (4.3 Far-infrared properties) [from (cite: schaerer2020)]
- External data: z=5-6 comparison galaxies  
  > "and 6 from (cite: capak2015)" (4.3 Far-infrared properties) [from (cite: capak2015)]
- External data: z=4 [CII] luminosity function models used for comparison  
  > "luminosity function from (cite: popping2016) and (cite: lagache2018)" (4.4 Number counts and luminosity functions) [from (cite: popping2016); (cite: lagache2018)]
- External data: z=2 Herschel-PACS cumulative number count  
  > "PACS survey of the GOODS field (cite: magnelli2013)" (4.4 Number counts and luminosity functions) [from (cite: magnelli2013)]
- External data: Cluster stellar mass functions at z=1 and 1.5  
  > "(cite: vanderburg2013) and (cite: nantais2016) give best-fitting stellar mass functions for clusters at" (5.2 Cluster mass of SPT2349-56) [from (cite: vanderburg2013); (cite: nantais2016)]
- External data: z=3.8-4.9 main-sequence relation  
  > "MS relation from (cite: pearson2018)" (5.1 Spatial distribution) [from (cite: pearson2018)]
- External data: Predicted largest cluster halos for 25 deg2, 2500 deg2 and full-sky surveys  
  > "we show predictions for the largest cluster halos expected in a 25 deg$^2$ survey, a 2500 deg$^2$ survey, and a full-sky survey (cite: harrison2013; marrone2018)." (5.2 Cluster mass of SPT2349-56) [from (cite: harrison2013; marrone2018)]
- External data: N-body merger timescale of about 100 Myr for the core galaxies  
  > "should indeed merge within a timescale of about 100 Myr (cite: rennehan2019)" (4.4 Number counts and luminosity functions) [from (cite: rennehan2019)]

## Processing

### Calibration

- pipeline or manual: casa with observatory-provided calibration scripts  
  > "and the observatory-provided calibration scripts." (3.1 Data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean  
  > "were produced using the casa function `tclean` with Briggs weighting and a robust parameter of 0.5." (3.1 Data reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "were produced using the casa function `tclean` with Briggs weighting and a robust parameter of 0.5." (3.1 Data reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum images made by multi-frequency synthesis from sidebands without line emission; line-free channels stacked for source continuum  
  > "Continuum images were also produced using `tclean` for the sidebands that did not contain any line emission using multi-frequency synthesis (MFS)." (3.1 Data reduction); "We also stacked the channels that did not contain line emission to produce continuum images." (3.4.1 Line and continuum emission)
- line free channels: _not stated_
- primary beam correction: Line and continuum measurements made on primary-beam-corrected maps; source search done on uncorrected cubes  
  > "All line and continuum measurements were made on primary beam-corrected maps." (3.4 Source properties)
- array combination: uv data of Cycle 5 and Cycle 6 observations combined (core [CII]; CO(4-3) around the entire structure)  
  > "similarly we combined the $uv$ tables from the Cycle 5 and 6 observations of CO(4–3) around the entire structure" (3.1 Data reduction)
- smoothing: _not stated_
- final beam: [CII] combined 0.35/0.29 arcsec; CO(4-3) combined 0.85/0.72 arcsec  
  > "the synthesized beam major/minor full width at half maximum (FWHM) was 0.35/0.29 arcsec." (3.1 Data reduction); "the synthesized beam major/minor FWHM was 0.85/0.72 arcsec." (3.1 Data reduction)
- final rms: CO(4-3) deep map 0.06 mJy/beam per 54 km/s channel; [CII] deep map 0.2 mJy/beam per 13 km/s channel  
  > "the maximum depth achieved was 0.06 mJy beam$^{-1}$ per 54 km s$^{-1}$ channel" (3.1 Data reduction); "was 0.2 mJy beam$^{-1}$ per 13 km s$^{-1}$ channel, and the synthesized beam" (3.1 Data reduction)

### Inherited from earlier work

- Cosmology: Lambda-CDM with Planck parameters  
  > "with parameters from (cite: planck2014-a15) throughout." (1 Introduction) [from (cite: planck2014-a15)]
- Greybody SED functional form  
  > "following the greybody function outlined in (cite: greve2012)" (3.4.2 Far-infrared luminosities) [from (cite: greve2012)]
- Definition and selection of red Herschel sources (250 um positions as priors, S/N above 3 at 250 and 500 um)  
  > "see (cite: miller2018) for details" (2.2 Follow-up ALMA observations) [from (cite: miller2018)]
- Source-search algorithm  
  > "we used the publicly-available code LineSeeker (cite: gonzalez-lopez2017; gonzalez-lopez2019)." (3.2 Source extraction) [from (cite: gonzalez-lopez2017; gonzalez-lopez2019)]
- Velocity-dispersion mass scaling relation (same relation as Miller et al. 2018)  
  > "(using the same scaling relation)" (4.2.1 Mass from velocity dispersion) [from (cite: evrard2008); (cite: miller2018)]
- Maximum-likelihood luminosity-function fitting approach  
  > "we use the maximum-likelihood approach to fit for model parameters, first described by (cite: marshall1983)" (4.4 Number counts and luminosity functions) [from (cite: marshall1983); (cite: wall2008)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the pipeline or manual scripts were used for each execution block
- Array configurations, baseline ranges, number of execution blocks and on-source times for each dataset
- Flux, bandpass and phase calibrators and absolute flux scale uncertainty
- Whether any self-calibration was applied
- tclean parameters other than robust: deconvolver, niter, threshold, masks, cell size, image size, spectral gridding and mosaic gridder
- Primary-beam response cut used and how mosaics were combined across pointings
- Exact weighting between Cycle 5 and Cycle 6 uv data when combining
- Line-free channel ranges used for the continuum stacks of each source
- The manually designed elliptical apertures for each source (positions, axes, angles)
- LineSeeker settings beyond the stated width range (kernel set, pixel treatment)
- Peak-finding algorithm used for the continuum search and local-rms map details
- MCMC sampler, priors, number of walkers and chain lengths for the luminosity-function fits
- Initial parameter values and bounds for the Sersic fits, and fitting code
- Luminosity-distance values used for line luminosities beyond the Planck cosmology reference

## Analysis recipe

1. **Calibrate and image the ALMA cubes and continuum**: Calibrate with CASA and observatory scripts; image cubes with tclean (Briggs); make MFS continuum from line-free sidebands  
  > "Dirty and cleaned data cubes for each of the observations reported in Table" (3.1 Data reduction); "and the observatory-provided calibration scripts." (3.1 Data reduction)
   - software: CASA, tclean
   - parameter: Briggs weighting, robust = 0.5  
  > "were produced using the casa function `tclean` with Briggs weighting and a robust parameter of 0.5." (3.1 Data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Combine Cycle 5 and 6 uv data into deep cubes**: Combine uv tables of Cycle 5 and 6 observations for the core [CII] and the CO(4-3) around the structure, then image  
  > "similarly we combined the $uv$ tables from the Cycle 5 and 6 observations of CO(4–3) around the entire structure" (3.1 Data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Blind line search for new members**: LineSeeker on dirty (uncleaned) primary-beam-uncorrected cubes; detections are positive peaks with S/N above the most significant negative peak in each cube  
  > "LineSeeker convolves a primary beam-uncorrected data cube with a number of Gaussians of varying width along the spectral axis." (3.2 Source extraction); "Within each data cube we took all positive-pixel line peaks with a S/N greater than the most significant negative-pixel line peak to be detections." (3.2 Source extraction)
   - software: LineSeeker
   - parameter: Line widths from a single channel to 1000 km/s FWHM  
  > "We searched for \[Cii\] peaks ranging from a single channel to 1000 km s$^{-1}$ in FWHM" (3.2 Source extraction)
   - parameter: Velocity range +/-1500 km/s about z = 4.304  
  > "relative to the mean redshift of 4.304 reported by (cite: miller2018)" (3.2 Source extraction)
   - parameter: Seven cubes searched; core [CII] threshold S/N 6.2 (negative-peak limit)  
  > "we found negative peaks down to a S/N of 6.2." (3.2 Source extraction)
   - assumption: Searching dirty cubes avoids cleaning artefacts  
  > "in order to minimize the possibility of picking up artefacts introduced by the cleaning." (3.2 Source extraction)
   - fitting: _not stated_
   - validation: Threshold set by the most significant negative peak in each cube (false-positive control)  
  > "Within each data cube we took all positive-pixel line peaks with a S/N greater than the most significant negative-pixel line peak to be detections." (3.2 Source extraction)
4. **Search for continuum-only sources**: Average all channels; local rms in 6 arcsec circles after masking line sources; peak-finding with cutoff set by most significant negative peak  
  > "calculating the local rms within circles of 6 arcsec (after masking all of the sources detected by their line emission)" (3.2 Source extraction); "This continuum search found negative peaks down to a S/N of 5.0 in the Band 3 data and 5.6 in the Band 7 data." (3.2 Source extraction)
   - fitting: _not stated_
   - validation: Negative-peak S/N cutoff used as false-positive threshold  
  > "Similar to our line search, we looked for positive flux density peaks with a higher significance than the most significant negative flux density peak." (3.2 Source extraction)
5. **Measure redshifts, line strengths and continuum flux densities**: Manually designed elliptical apertures; spectra fit with constant, single or double Gaussian; line strength integrated over -3 sigma to +3 sigma; continuum from line-free stacks  
  > "Instead, we choose to obtain these properties through aperture photometry" (3.4.1 Line and continuum emission); "Redshifts were determined from the best-fitting Gaussian means, and line strengths were obtained by integrating the spectra from $-3\sigma$ to $3\sigma$." (3.4.1 Line and continuum emission)
   - software: CASA
   - parameter: Initial 2 arcsec-diameter circular apertures; channels binned by 4 ([CII]) and 2 (CO(4-3))  
  > "First, 2 arcsec-diametre circular apertures were placed on each source" (3.4.1 Line and continuum emission); "binning the channels by a factor of 4 in order to reduce the noise" (3.4.1 Line and continuum emission)
   - fitting: Constant, single Gaussian and double Gaussian tried; best model has reduced chi-squared closest to 1  
  > "we tried fitting a constant, a single Gaussian and a double Gaussian model to the line profiles, and took the model with the reduced $\chi^2$ closest to 1 to be the best fit." (3.4.1 Line and continuum emission)
   - validation: Larger apertures tested on 10 bright isolated sources; peak-pixel versus aperture photometry compared to assess resolution  
  > "We checked that our apertures were not missing flux by comparing line strengths and continuum flux densities computed with larger aperture sizes." (3.4.1 Line and continuum emission); "was 0.52, and 0.80 for the continuum flux density ratio" (3.4.1 Line and continuum emission)
6. **Derive far-infrared luminosities and SFRs**: Fit greybody amplitude with fixed beta, lambda_0 and T_d; integrate 42-500 um; convert L_FIR to SFR  
  > "The best-fitting models were integrated from 42 to 500 $\mu$m in order to obtain far-infrared luminosities" (3.4.2 Far-infrared luminosities); "We lastly use a conversion factor of 0.95$\,{\times}\,10^{-10}$ M$_{\odot}$ yr$^{-1}$/L$_{\odot}$" (3.4.2 Far-infrared luminosities)
   - parameter: beta = 2, critical wavelength 100 um, z = 4.303  
  > "by fixing the emissivity index to 2, the critical wavelength to 100 $\mu$m, and adopting the mean cluster redshift of 4.303" (3.4.2 Far-infrared luminosities)
   - parameter: T_d = 39.6 K (range 35.2-44.8 K)  
  > "consistent dust temperatures range from 35.2 to 44.8 K" (3.4.2 Far-infrared luminosities)
   - assumption: Chabrier IMF in the L_FIR-to-SFR conversion  
  > "(from (cite: kennicutt1998), modified for a Chabrier initial mass function" (3.4.2 Far-infrared luminosities)
   - fitting: Amplitude-only scaling of the greybody for single detections; uncertainties combine fit error and the L_FIR change between T_d limits  
  > "for sources with one flux density detection, this simply amounts to scaling the greybody function." (3.4.2 Far-infrared luminosities); "uncertainties were estimated by adding in quadrature the uncertainty from the fit" (3.4.2 Far-infrared luminosities)
   - validation: Dust temperature range compared with earlier SPT SMG results  
  > "This is in agreement with results from (cite: strandet2016)" (3.4.2 Far-infrared luminosities)
7. **Measure half-light radii**: Fit elliptical Sersic profiles convolved with the synthesized beam to 3x3 arcsec high-resolution Band 7 continuum cutouts  
  > "We then modelled these images as elliptical Sérsic profiles convolved with the best-fitting elliptical Gaussian synthesized beam produced by `tclean` during the imaging process, and we allowed the Sérsic index to vary." (3.4.3 Half-light radii)
   - software: tclean
   - parameter: Fits only for sources brighter than 3 sigma in the continuum stacks; C7 not fit  
  > "fits were only done for sources brighter than 3$\sigma$ in the continuum stacks." (3.4.3 Half-light radii)
   - fitting: Elliptical Sersic with free Sersic index; sampler, priors and likelihood not stated  
  > "and we allowed the Sérsic index to vary." (3.4.3 Half-light radii)
   - validation: Models and residuals shown in an appendix  
  > "in Appendix [8](#appendix2) we show the high-resolution continuum images, best-fitting models, and residuals." (3.4.3 Half-light radii)
8. **Velocity distribution and virial mass of the core**: Lilliefors test of Gaussianity; biweight velocity dispersion within 90 kpc radius; Evrard et al. scaling to M200; escape-speed envelope for outer groups  
  > "To test the Gaussianity of our sample, we perform a Lilliefors test (cite: lilliefors1967)" (4.1 Velocity distribution); "We then convert this velocity dispersion into a mass using the scaling relation found by (cite: evrard2008)" (4.2.1 Mass from velocity dispersion)
   - parameter: Effective radius 90 kpc (primary beam response 0.5); removes galaxy C19  
  > "We therefore take this to be the effective radius of the core region where our data is approximately complete; this removes galaxy C19 from the analysis." (4.2.1 Mass from velocity dispersion)
   - assumption: Core is virialized  
  > "Under the assumption that the core of SPT2349$-$56 has virialized" (4.2.1 Mass from velocity dispersion)
   - fitting: Biweight estimator with bootstrap uncertainties  
  > "with the uncertainty estimated using bootstrap resampling" (4.2.1 Mass from velocity dispersion)
   - validation: Result compared with Miller et al. 2018 using the same 14 sources  
  > "which is entirely consistent with their result." (4.2.1 Mass from velocity dispersion)
9. **Dynamical, gas and halo masses of individual galaxies**: Isotropic virial estimator for M_dyn; CO(4-3) luminosity to CO(1-0) to gas mass; gas mass scaled to halo mass  
  > "Dynamical mass, calculated using the isotropic virial estimator" (Table 4 footnote d); "We have applied this factor to the galaxies in our sample and provide the results in Table" (4.2.3 Galaxy gas and halo masses)
   - parameter: r_{4,1} = 0.60+/-0.05; alpha_CO = 1 Msun/(K km/s pc^2); halo/gas factor 42.8  
  > "for simplicity, we adopt a conversion factor of $\alpha_{\rm CO}\,{=}\,1$ M$_{\odot}$/(K km s$^{-1}$ pc$^2$) to obtain gas masses" (4.2.3 Galaxy gas and halo masses)
   - parameter: Mean half-light radius 1.5+/-0.5 kpc adopted where R_1/2 not measured; double Gaussians treated as two components and masses summed  
  > "we treat each Gaussian separately and sum the two resulting masses to obtain the total dynamical mass" (4.2.2 Galaxy dynamical masses)
   - assumption: Gas is dispersion-dominated; alpha_CO chosen for simplicity and gas masses are order-of-magnitude  
  > "We note that this equation assumes the gas to be dispersion-dominated" (4.2.2 Galaxy dynamical masses); "and note that these quantities should be interpreted primarily as order-of-magnitude estimates" (4.2.3 Galaxy gas and halo masses)
   - fitting: _not stated_
   - validation: Total core gas mass compared with CO(2-1) estimate of Miller et al. 2018, consistent within a factor of a few  
  > "the two measurements do provide consistent results to within a factor of a few." (4.2.3 Galaxy gas and halo masses)
10. **Number counts and luminosity-function fits**: Cumulative and differential counts normalised by 0.1 Mpc^3; maximum-likelihood fit of single power law versus Schechter function  
  > "The resulting proper volume is 0.1 Mpc$^3$, and we use this to normalize our number counts." (4.4 Number counts and luminosity functions); "We test two models, a single power-law and a Schechter function" (4.4 Number counts and luminosity functions)
   - parameter: Sources restricted to those with both Band 3 and Band 7 coverage (removes N2, N3, SPIREc)  
  > "First, we restrict our analysis to include only sources with both Band 3 and Band 7 coverage" (4.4 Number counts and luminosity functions)
   - assumption: All sources selected from maps of uniform depth  
  > "we use the approximation that all sources were selected from maps of uniform depth." (4.4 Number counts and luminosity functions)
   - fitting: Negative log-likelihood minimised; posteriors from an MCMC; parameters from posterior means with 68 per cent intervals; priors not stated  
  > "We minimize the negative log-likelihood and obtain marginalized probability distributions for the model parameters using a Markov chain Monte Carlo (MCMC)" (4.4 Number counts and luminosity functions); "uncertainties are estimated by calculating the 68 per cent confidence intervals." (4.4 Number counts and luminosity functions)
   - validation: Models compared by likelihood ratio  
  > "The models are then compared by calculating the final likelihood ratios." (4.4 Number counts and luminosity functions)
11. **Star-formation rate density**: Sum galaxy SFRs within a projected radius and convert to density assuming spherical geometry  
  > "We can convert points on this plot into SFR densities by assuming spherical geometry." (5.3 Star formation)
   - parameter: Sphere of proper radius 360 kpc for the total LABOCA region  
  > "Using a sphere of proper radius 360 kpc we can thus estimate a total SFR density" (5.3 Star formation)
   - assumption: Spherical symmetry; volume somewhat arbitrary  
  > "since the volume specified is somewhat arbitrary" (5.3 Star formation)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration with observatory scripts and imaging  
  > "and the observatory-provided calibration scripts." (3.1 Data reduction)
- **tclean** : Producing dirty and cleaned cubes and MFS continuum images  
  > "were produced using the casa function `tclean` with Briggs weighting and a robust parameter of 0.5." (3.1 Data reduction)
- **LineSeeker** : Blind search for line emitters in the dirty cubes  
  > "we used the publicly-available code LineSeeker (cite: gonzalez-lopez2017; gonzalez-lopez2019)." (3.2 Source extraction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Newly identified associated galaxies at z = 4.3 | 15 | not stated | dimensionless | 3 | we identify a further 15 associated galaxies |
| Total sample (line plus continuum detections) | 29 line detections and 3 continuum detections | not stated | dimensionless | 4 | These 29 line detections and three continuum detections constitute our current sample of SPT2349$-$56 galaxies |
| Fraction of single-dish 870-um flux density resolved | 55 | +/-5 | per cent | 5 | resolving 55$\,{\pm}\,$5 per cent of the 870-$\mu$m flux density |
| Total 850-um flux density of ALMA sources | 60.3 | 0.4 | mJy | 5 | Our sources total 60.3$\,{\pm}\,$0.4 mJy at 850 $\mu$m |
| Weighted mean redshift of core sources | 4.30280 | 0.00002 | dimensionless | 5 | the weighted mean redshift of the sources located within the core is 4.30280$\pm$0.00002 |
| Weighted mean redshift of northern component | 4.31309 | 0.00016 | dimensionless | 5 | the weighted mean redshift of the northern component is 4.31309$\pm$0.00016 |
| Weighted mean redshift of SPIREc | 4.28171 | 0.00018 | dimensionless | 5 | that of SPIREc is 4.28171$\pm$0.00018 |
| Weighted mean S850um/S3.2mm flux density ratio (11 central sources) | 70 | weighted standard deviation 10 | dimensionless | 6 | we calculate the weighted mean flux density ratio to be 70 with a weighted standard deviation of 10 |
| Dust temperature giving closest match to mean colour | 39.6 (consistent range 35.2 to 44.8) | not stated | K | 6 | consistent dust temperatures range from 35.2 to 44.8 K; that $T_{\rm d}\,{=}\,39.6$ K provides the closest match to the observed weighted mean colour |
| Half-light radii range and mean | 0.7 to 2.1 kpc, mean 1.5 kpc | dispersion 0.5 kpc | kpc | 7 | We find that the half-light radii range from 0.7 to 2.1 kpc, with a mean of 1.5 kpc and a dispersion of 0.5 kpc. |
| Standard deviation of core relative radial velocities | 358 | not stated | km/s | 8 | The standard deviation of relative radial velocities within the central region was calculated to be 358 km s$^{-1}$ |
| Lilliefors p-value for Gaussian velocity distribution (max distance 0.15) | 0.20 | not stated | dimensionless | 8 | to be 0.20, meaning that the probability of obtaining a maximum distance of 0.15 or greater is 20 per cent if the relative radial velocities are Gaussian-distributed. |
| Biweight velocity dispersion of core galaxies | 370 | +67/-89 | km/s | 8 | $\sigma_r\,{=}\,$370$_{-89}^{+67}$ km s$^{-1}$ using the biweight estimator |
| Core mass from velocity dispersion | 9e12 | +/-5e12 | Msun | 8 | The resulting mass is (9$\pm$5)$\,{\times}\,$10$^{12}$ M$_{\odot}$ |
| Sum of galaxy dynamical masses in the core | 1.3e12 | not stated | Msun | 9 | the sum of the dynamical masses of the galaxies within the core is 1.3$\,{\times}\,10^{12}\,$M$_{\odot}$ |
| Sum of galaxy gas masses in the core | 2.9e11 | not stated | Msun | 9 | the sum of the gas masses within the core reach a total value of 2.9 ${\times}\,10^{11}\,$M$_{\odot}$ |
| Total halo mass summed over core, northern and SPIREc | 2.5e13 | large systematics not included | Msun | 9 | making the total mass about 2.5$\,{\times}\,$10$^{13}$ M$_{\odot}$ |
| Weighted mean ratio of [CII] to CO(4-3) FWHM | 1.07 | 0.02 (weighted std 0.08) | dimensionless | 5 | the weighted mean ratio of these linewidths is 1.07$\,{\pm}\,0.02$ |
| Survey volume for number counts | 0.1 | not stated | Mpc^3 | 10 | The resulting proper volume is 0.1 Mpc$^3$ |
| SFR density of the core (23 galaxies within 150 kpc) | 3.5e5 | not stated | Msun/yr/Mpc^3 | 11 | gives an SFR density of 3.5$\,{\times}\,10^5$ M$_{\odot}$ yr$^{-1}$ Mpc$^{-3}$ |
| Total SFR density of the LABOCA region (360 kpc sphere) | 3.7e4 | not stated | Msun/yr/Mpc^3 | 11 | we can thus estimate a total SFR density of 3.7$\,{\times}\,10^4$ M$_{\odot}$ yr$^{-1}$ Mpc$^{-3}$. |

## Qualitative findings

- The core, northern group and SPIREc group are offset in velocity by about 1000 km/s, but small numbers prevent strong conclusions  
  > "however small number statistics means that we cannot draw any strong conclusions here." (4.1 Velocity distribution)
- Proto-cluster galaxies resemble field galaxies in far-infrared luminosity, line strength, line width and size  
  > "We find good agreement between the far-infrared luminosities, line strengths, line widths, and physical radii," (6 Summary and conclusion)
- Extended [CII] emission arc around central galaxies C3, C6 and C13; nature left to future work  
  > "However, a more thorough analysis is required to understand what we are seeing here, and will be done in future work." (3.3 Extended [CII] emission)

## Claim tuples

- H: SPT2349-56 contains more proto-cluster members than the 14 previously confirmed galaxies | E: Blind LineSeeker search of deep [CII] and CO(4-3) cubes over the core, north and SPIREc, plus a continuum search | R: 15 new associated galaxies at z=4.3 (29 line detections in total) plus three continuum-only sources | F: The structure is a central core of 23 galaxies, a northern group of three and a three-galaxy SPIREc group | **supported**
- H: The core is virialized and has a mass consistent with a BCG progenitor | E: Lilliefors test and biweight velocity dispersion of core galaxies, converted with the Evrard et al. scaling | R: Gaussianity not rejected (p = 0.20); mass (9+/-5)e12 Msun | F: The core may be virialized, with mass comparable to BCG hosts | **partially**
- H: The northern and SPIREc groups are bound to the core mass | E: Compared line-of-sight velocities scaled by sqrt(3) with the escape speed of a 9e12 Msun point mass | R: Northern and SPIREc galaxies exceed the escape velocity | F: They will not fall into the core potential but likely remain bound to the whole proto-cluster | **supported**
- H: The [CII] and FIR luminosity functions show a break | E: Maximum-likelihood fits of single power law and Schechter models with MCMC | R: Schechter slightly favoured for [CII]; no improvement for FIR | F: Weak evidence for a break in the [CII] luminosity function; likelihood ratio close to 1 | **partially**
- H: The star-formation rate density of SPT2349-56 exceeds that in simulations | E: Summed galaxy SFRs within spheres and divided by volume, compared with published simulations | R: Total SFR density about 4e4 Msun/yr/Mpc^3, core 3.5e5 | F: May be an order of magnitude above the most extreme simulated examples; interpretation unclear because the volume is arbitrary | **partially**

## Reasoning

- Why this data: Cycle 6 [CII] at higher resolution to resolve morphologies; Cycle 6 CO(4-3) to cover the outskirts  
  > "The goal of the CO(4–3) observations was to provide coverage of the outskirts of the structure." (2.2 Follow-up ALMA observations)
- Why this method: Search dirty cubes to avoid cleaning artefacts; aperture photometry because uv-plane modelling of cubes with over 20 galaxies is too expensive  
  > "in order to minimize the possibility of picking up artefacts introduced by the cleaning." (3.2 Source extraction); "some of our data cubes contain over 20 galaxies, many of which are somewhat resolved, as well as extended emission" (3.4.1 Line and continuum emission)
- Alternative: Modelling galaxies directly in the uv plane was rejected as too computationally expensive  
  > "one could model the galaxies directly in the $uv$ plane; however, some of our data cubes contain over 20 galaxies" (3.4.1 Line and continuum emission)
- Alternative: Larger photometry apertures rejected because they gain little line flux but lose continuum flux  
  > "thus our apertures should be striking a good balance between these two measurements." (3.4.1 Line and continuum emission)
- Alternative: alpha_CO of 1 chosen over values up to 4 for quiescent galaxies  
  > "ranging from 1 for starbursting galaxies to 4 for more quiescently star-forming galaxies" (4.2.3 Galaxy gas and halo masses)
- How they decided it was enough: Detections are positive peaks exceeding the most significant negative peak in each cube  
  > "Within each data cube we took all positive-pixel line peaks with a S/N greater than the most significant negative-pixel line peak to be detections." (3.2 Source extraction)
- Limitation (authors): Dynamical masses uncertain to within a factor of a few  
  > "our dynamical mass estimates should therefore be treated as uncertain to within a factor of a few." (4.2.2 Galaxy dynamical masses)
- Limitation (authors): Gas masses are order-of-magnitude estimates  
  > "and note that these quantities should be interpreted primarily as order-of-magnitude estimates" (4.2.3 Galaxy gas and halo masses)
- Limitation (authors): Continuum data do not reach the SED peak, so only Rayleigh-Jeans slopes constrain the dust temperature  
  > "The continuum flux density measurements presented in this paper do not reach the peak of this SED" (3.4.2 Far-infrared luminosities)
- Limitation (authors): Large systematic uncertainties in the total mass are not incorporated  
  > "while there are large systematic uncertainties which have not been incorporated into this estimation" (5.2 Cluster mass of SPT2349-56)
- Caveat (inferred, ours): Detection threshold is set from the most negative peak per cube, not a calibrated purity or completeness test
- Caveat (inferred, ours): Photometry apertures were drawn by hand, so source fluxes are hard to reproduce exactly
- Caveat (inferred, ours): A single dust temperature of 39.6 K and beta = 2 are applied to all galaxies, so L_FIR and SFRs inherit that systematic
- Caveat (inferred, ours): The sample is not a field sample, so the luminosity-function comparison and normalisations are not like-for-like
- Caveat (inferred, ours): alpha_CO = 1 and a fixed halo scaling factor dominate the gas and halo mass budget

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Execution block list and calibrators per project code
- Missing: Full tclean parameter set and line-free channel ranges
- Missing: The hand-drawn aperture definitions
- Missing: MCMC priors and sampler settings for the luminosity-function fits
- Data volume (inferred): Large: about 20 mosaic pointings across two Band 7 and Band 3 projects; likely several hundred GB of raw data (estimate)
- Score (inferred): 3/5, Both project codes and the main tools (CASA tclean, robust 0.5, LineSeeker) are given and the per-source tables carry numeric answers, but manual apertures, line-free channels, most tclean settings and fit priors are missing.
- Rediscovery candidate: no, The paper does not state that the data are public and manual aperture design and unstated imaging settings prevent an exact redo, although the main results are numeric.

## Links

- Method: (cite: miller2018) (Earlier ALMA analysis of the core, the redshift and velocity-dispersion mass method and the red Herschel source definition)
- Method: (cite: gonzalez-lopez2017; gonzalez-lopez2019) (LineSeeker line-search code)
- Method: (cite: greve2012) (Greybody SED functional form)
- Companion: (cite: miller2018) (Prior ALMA observations of the SPT2349-56 core with 14 confirmed galaxies)
- Companion: (cite: rennehan2019) (N-body simulations and gas-to-halo mass scaling used for the mass estimates)
- Related: South Pole Telescope 2500 deg2 extragalactic mm-wave point-source survey
- Related: APEX LABOCA 870 um follow-up of SPT sources
- Related: Herschel-SPIRE follow-up of SPT2349-56

## Checks

```json
{
 "quotes": 157,
 "quotes_ok": 157,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 21,
 "numeric_problems": 0,
 "fill": {
  "facts": 135,
  "stated": 100,
  "rate": 0.741
 },
 "evidence_ok": true
}
```
