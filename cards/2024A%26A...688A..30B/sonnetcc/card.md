# Emergence of high-mass stars in complex fiber networks (EMERGE). II. The need for data combination in ALMA observations

`2024A&A...688A..30B` | Astronomy and Astrophysics 2024 | first author: Bonanomi, Francesca | arXiv: 2405.09290 | DOI: 10.1051/0004-6361/202348920

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type theory_or_simulation_compared_to_alma

## Science

- Fields: star_formation, milky_way_ism, instrumentation
- Question: How strongly do interferometric filtering and the missing short-spacing information bias the recovered flux, peak, FWHM and radial profile of simulated cores and filaments in ALMA continuum data, and how much do 12m+7m, Feather, MACF and 12m+IRAM-30m combinations fix it?  
  > "We aim to systematically quantify the impact of the interferometric response and the effects of the short-spacing information during the characterization of the ISM structure using ALMA observations." (abstract)
- Target **Synthetic Gaussian cores, filaments and Plummer filaments (simulated field)**: coordinates RA=12h00m00.0s, Dec=-23d00m00.0s (field centre of the simulations)  
  > "All these synthetic objects are placed at the center of a 6.25 arcmin wide field located at coordinates" (ALMA simulations); "the optimal position in the sky that can be observed by ALMA in terms of source elevation and overall sensitivity" (ALMA simulations); z/distance _not stated_; distance from _not stated_
- Target **OMC-3 (Orion A), real ALMA N2H+ (1-0) data**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **Synthetic core mass function sample (500 cores)**: coordinates _not stated_; z/distance D=414 pc (Orion)  
  > "at a distance of Orion (D=414 pc)" (Observing the core mass function); distance from _not stated_

## Data provenance

- ALMA projects: 2019.1.00641.S
- bands: Band 3 (3 mm); simulations at 100 GHz  
  > "representative of standard the continuum ALMA observations at 3mm (Band 3)" (ALMA simulations)
- frequencies and spectral setup: single frequency channel, central frequency 100 GHz (simulations)  
  > "We produce models characterized by a single frequency channel to avoid taking into consideration velocity effects." (ALMA simulations); "We select as central frequency 100 GHz" (ALMA simulations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12m, ACA-7m and Total Power simulated separately  
  > "We produce simulations of the three different ALMA arrays separately." (ALMA simulations)
- configurations: 12m C43-1 (most compact)  
  > "We perform our observations using the most compact configuration offered in ALMA 12m array, C43-1" (ALMA simulations)
- baselines: 12m: 15 m to 16 km; ACA-7m: 9 to 45 m  
  > "baselines between 15 meters and 16 kilometers" (Data combination with ALMA); "baselines between 9 and 45 meters" (Data combination with ALMA)
- angular resolution: 12m C43-1: 3.38 arcsec; ACA-7m: 12.5 arcsec; TP: 62.9 arcsec (at 100 GHz, from the Technical Handbook)  
  > "providing an angular resolution" (ALMA simulations); "of 3.38 arcsec and MRS" (ALMA simulations); "of 12.5 arcsec and 66.7 arcsec, respectively" (ALMA simulations)
- max recoverable scale: 12m C43-1: 28.5 arcsec; ACA-7m: 66.7 arcsec  
  > "of 28.5 arcsec." (ALMA simulations); "of 12.5 arcsec and 66.7 arcsec, respectively" (ALMA simulations)
- sensitivity: noisy runs use tsys-atm thermal noise with PWV = 1.8 mm (Band 3); most runs noise-free  
  > "we also produce (noisy) simulations including atmospheric thermal noise assuming standard weather conditions for Band 3 with precipitated water vapor (PWV) of 1.8 mm" (Thermal noise)
- time on source: 12m: 67-pointing mosaic, 2 x 30 s = 1 min per pointing; 7m: 33 pointings, 30 s x 14 repetitions, 3 days  
  > "Each pointing in our mosaic is observed in two iterations (repetitions), 30 sec each, for a total of 1 min integration per pointing" (Generation of visibilities with simobserve); "We thus obtained a 33-pointings mosaic, selecting as integration time 30s and 14 repetitions." (Generation of visibilities with simobserve)
- observing dates: real OMC-3 data: ALMA Cycle 7  
  > "observations carried out with the ALMA 12m-array (alone) in its most compact configuration (C43-1) during ALMA Cycle 7" (Comparisons with real ALMA observations)
- pi or archival as stated: PI: Hacar (project 2019.1.00641.S)  
  > "(proj. ID: 2019.1.00641.S; PI: Hacar)" (Comparisons with real ALMA observations)
- Line: N2H+ 1-0 (not stated)
- Other facility **IRAM-30m**: N2H+ (1-0) large-scale maps of OMC-3 (projects 032-13, 120-20) combined with ALMA 12m; also simulated as a large SD  
  > "The ALMA 12m array observations have been combined with additional IRAM-30m" (Comparisons with real ALMA observations); "(proj. IDs: 032-13, 120-20)" (Comparisons with real ALMA observations)
- Other facility **ALMA Science Archive (via ALminer)**: statistics on GOUS requesting 12m, 7m and TP data in Cycles 6-9  
  > "we queried the ALMA Science Archive using the ALminer toolkit (cite: 2023Ahmadi)" (Data combination with ALMA)
- External data: ALMA Cycle 10 Technical Handbook values for resolution and MRS of 12m, 7m and TP  
  > "All the values listed here are taken from the" (ALMA simulations (footnote)) [from ALMA Cycle 10 Technical Handbook (cite: 2023Cortes)]
- External data: dust emissivity frequency dependence beta=1.6 typical for Orion filaments and cores  
  > "typical for filaments and cores in Orion (cite: Sadavoy2016; Mason2020)" (Source brightness) [from (cite: Sadavoy2016; Mason2020)]
- External data: OMC-3 data reduction, imaging and combination products (12m + IRAM-30m Feather and MACF)  
  > "The observations, the data reduction and imaging procedures, and the data combination technique used are presented in (cite: 2024Hacar)." (Comparisons with real ALMA observations) [from (cite: 2024Hacar)]
- External data: identification of the 23 small-scale filaments (fibers) in OMC-3  
  > "(see Paper III for additional details)" (Comparisons with real ALMA observations) [from Paper III (cite: 2024Socci)]
- Simulation/model as data: 2D Gaussian cores with FWHM = 5, 10, 15, 20, 30, 40, 50, 70 arcsec  
  > "5, 10, 15, 20, 30, 40, 50, and 70 arcsec." (Observing isolated cores)
- Simulation/model as data: infinite 1D Gaussian filaments with FWHM = 5, 10, 15, 20, 30, 40, 50, 70 arcsec  
  > "We modeled Gaussian filaments with FWHM" (Single Gaussian filament analysis); "5, 10, 15, 20, 30, 40, 50 and 70 arcsec." (Single Gaussian filament analysis)
- Simulation/model as data: Plummer-like filaments with p=2.5 and p=4, Rflat=30 arcsec  
  > "we produce two noise-free, Plummer-like filaments with p=2.5 and 4 as representative values for shallow and steep filaments, respectively" (Filaments with Plummer-like profiles)
- Simulation/model as data: source peak intensity I0 = 7.5e-3 mJy/pix in all models (about NH2 1.5e23 cm-2 at Tdust = 15 K)  
  > "we have adopted a source peak intensity of" (Source brightness); "in all our synthetic models" (Source brightness)
- Simulation/model as data: synthetic CMF: 500 cores, Salpeter-like slope 1.35, 0.5-10 Msun, FWHM uniform 5-30 arcsec, T = 10 K, D = 414 pc  
  > "We created a synthetic CMF drawing 500 core mass values following" (Observing the core mass function); "assuming a homogeneous dust temperature of T=10K." (Observing the core mass function)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean (CLEAN), mfs continuum, one output channel  
  > "This task is based on the CLEAN algorithm (cite: 1974Hogbom)" (Generation of images with tclean); "In a second step, we image each simulated visibility dataset using the CASA task" (Generation of images with tclean)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "select a standard Briggs weighting with a robust parameter equal to" (Generation of images with tclean)
- uv taper: _not stated_
- cell size: 0.5 arcsec (12m), 2 arcsec (7m)  
  > "We set the pixel size as 0.5 arcsec and 2 arcsec" (Generation of images with tclean)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: impbcor, cutoff 0.85  
  > "Afterwards we correct the images for the PB attenuation using the task" (Generation of images with tclean); "value of 0.85." (Generation of images with tclean)
- array combination: 12m+7m: concat with weights 1 and 0.116 then joint tclean; with TP: feather (sdfactor 1.0) and MACF (SD image as tclean startmodel)  
  > "applying weights of 1 and 0.116 to the simulated 12m and 7m visibilities, respectively" (Data combination methods); "a parameter used to adjust the flux scale of the SD image, to 1.0" (Data combination methods); "the MACF method first introduces the SD image as source model during the cleaning process of the interferometric visibilities" (Data combination methods)
- smoothing: 12m and 7m images convolved to a symmetric beam with imsmooth  
  > "Finally, we convolve the 12m and ACA-7m array images to obtain a symmetric synthesized beam using the task" (Generation of images with tclean)
- final beam: 4.5 arcsec (12m), 16 arcsec (7m)  
  > "The final beam sizes are 4.5 arcsec and 16 arcsec for the 12m and ACA-7m array, respectively." (Generation of images with tclean)
- final rms: _not stated_

### Inherited from earlier work

- data combination methods (concat weighting 0.116 for 7m, Feather, MACF) implemented in CASA  
  > "applying weights of 1 and 0.116 to the simulated 12m and 7m visibilities, respectively, to take into account the different dish diameters (cite: 2023Plunkett)" (Data combination methods) [from (cite: 2023Plunkett)]
- MACF technique  
  > "Thirdly, we also tested the Model-Assisted CLEAN plus Feather Method (MACF) (cite: 2018Hacar; 2023Plunkett)." (Data combination methods) [from (cite: 2018Hacar; 2023Plunkett)]
- flux density to dust column density conversion (Eq. for F_nu with Planck function)  
  > "Following (cite: 2008Kauffmann), the conversion between the dust column density and flux density at a given frequency" (Source brightness) [from (cite: 2008Kauffmann)]
- reduction, imaging and data combination of the real OMC-3 ALMA and IRAM-30m data  
  > "The observations, the data reduction and imaging procedures, and the data combination technique used are presented in (cite: 2024Hacar)." (Comparisons with real ALMA observations) [from (cite: 2024Hacar)]
- IRAM-30m observation noise levels and the fiber sample definition in OMC-3  
  > "the noise level of our IRAM-30m observations (cite: 2017Hacarb)" (Comparisons with real ALMA observations); "(see Paper III for additional details)" (Comparisons with real ALMA observations) [from (cite: 2017Hacarb); Paper III (cite: 2024Socci)]
- SD to interferometer integration time ratio formula used to set SD noise  
  > "Following (cite: 2013Mason), we determined the expected ratio of integration time per pointing" (On the SD sensitivity for data combination) [from (cite: 2013Mason)]

### Not stated but needed to reproduce (our reading)

- simobserve antenna configuration list names for C43-1 and the ACA, mapsize/pointing spacing values, and spectral/continuum bandwidth of the simulated channel
- tclean gridder (mosaic), imsize per array, deconvolver and whether multiscale or any mask was used
- how the model image units (mJy/pix, 0.25 arcsec pixel) were converted to Jy/pixel at the clean pixel scales
- how the 12m (3.5 arcmin) and 7m (4.5 arcmin) mosaics map onto the 6.25 arcmin field, and the primary-beam cutoff handling at mosaic edges for the profile cuts
- how the flux fraction was integrated (aperture, cut length, treatment of negative sidelobes) and the Gaussian-fit routine, initial guesses and fit window
- where along the image the radial cut was taken for filaments and elongated cores, and whether cuts were averaged
- random seed and number of noise realisations for the noisy runs
- how the Feather and MACF products were scaled for SD flux calibration beyond sdfactor = 1.0, and the startmodel scaling in MACF
- the TP simulation beyond imsmooth to 62.9 arcsec (no TP-specific simobserve setup is given)
- CMF sample: core positions in the field, the mass estimator used on recovered cores and the core-finding method
- OMC-3 real data: fiber identification list, radial-cut spacing and length, fitting procedure and the exact IRAM-30m/ALMA reduction parameters (all deferred to Paper I and Paper III)

## Analysis recipe

1. **quantify use of data combination in ALMA archive**: Query ALMA Science Archive with ALminer for ISM mosaic GOUS in Cycles 6-9 and count 12m, 7m and TP requests per year  
  > "We searched for individual Group Observing Unit Sets (GOUS) in ALMA Cycles 6-9 (years 2018-2022) and selected those completed projects within the ISM category requesting mosaic observations." (Data combination with ALMA)
   - software: ALminer
   - assumption: selecting mosaics implies extended emission larger than the primary beam and so beyond the MRS  
  > "Our conservative selection of mosaics ensures that these observations are aiming for targets with extended emission larger than the ALMA 12m (or 7m) primary beam" (Data combination with ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **build idealized sky models**: Generate noise-free model images of Gaussian cores, infinite Gaussian filaments, finite elongated Gaussians and Plummer-like filaments, scaled to a fixed peak intensity  
  > "we create a series of synthetic observations of idealized Gaussian (cores) and cylinders (filaments) using the Common Astronomy Software Application" (ALMA simulations)
   - software: CASA
   - parameter: FWHM = 5, 10, 15, 20, 30, 40, 50, 70 arcsec for Gaussian cores and filaments  
  > "5, 10, 15, 20, 30, 40, 50, and 70 arcsec." (Observing isolated cores)
   - parameter: finite filaments: FWHM fixed at 15 arcsec, length varied to give aspect ratios from 1 to infinity  
  > "we fixed the FWHM of our synthetic structures to 15 arcsec" (Finite filaments)
   - assumption: dust emissivity k_nu = 0.01 cm2/g at 300 GHz, i.e. 0.002 cm2/g at 100 GHz, with beta = 1.6  
  > "at 100 GHz (3 mm) assuming a frequency dependence" (Source brightness); "typical for filaments and cores in Orion (cite: Sadavoy2016; Mason2020)" (Source brightness)
   - assumption: mean molecular weight mu_H2 = 2.8 and constant Tdust = 15 K (T = 10 K for the CMF test)  
  > "is the mean molecular weight per hydrogen molecule" (Source brightness)
   - fitting: _not stated_
   - validation: _not stated_
3. **simulate ALMA 12m and ACA-7m visibilities**: Run simobserve on the model image with hexagonal Nyquist mosaics: 12m 67 pointings over 3.5 arcmin, 2 x 30 s per pointing; 7m 33 pointings over 4.5 arcmin, 30 s x 14 repetitions over 3 days  
  > "We cover this area using a 67-pointings mosaic following a Nyquist-sampled, hexagonal pointing pattern." (Generation of visibilities with simobserve); "We repeat the observations for 3 consecutive days over transit mimicking a standard ALMA observing schedule." (Generation of visibilities with simobserve)
   - software: CASA, simobserve
   - parameter: CASA v.6.5.2  
  > "We run our simulations in CASA v.6.5.2" (ALMA simulations)
   - parameter: thermalnoise = tsys-atm for the noisy runs, PWV = 1.8 mm  
  > "We include noise in our ALMA simulations" (Thermal noise)
   - assumption: integration time ratio C43-1 : ACA-7m = 1 : 7 to match sensitivities  
  > "following the official recommendations to match the sensitivity of the different ALMA arrays" (Generation of visibilities with simobserve)
   - fitting: _not stated_
   - validation: _not stated_
4. **image the simulated visibilities**: tclean in mfs mode with Briggs robust 0.5, cleaning threshold from a dirty image, impbcor at cutoff 0.85, then imsmooth to a symmetric beam  
  > "We set mfs as spectral definition mode (continuum imaging with only one output image channel)" (Generation of images with tclean); "select a standard Briggs weighting with a robust parameter equal to" (Generation of images with tclean)
   - software: CASA, tclean, impbcor, imsmooth
   - parameter: cleaning threshold = 10% of the dirty-image emission peak, niter = 1e8  
  > "To select the cleaning threshold, we produce first a dirty image from which we estimate its emission peak and set the threshold at" (Generation of images with tclean); "of the value and the number of maximum iterations at" (Generation of images with tclean)
   - parameter: pixel 0.5 arcsec (12m), 2 arcsec (7m); final beams 4.5 and 16 arcsec  
  > "We set the pixel size as 0.5 arcsec and 2 arcsec" (Generation of images with tclean); "The final beam sizes are 4.5 arcsec and 16 arcsec for the 12m and ACA-7m array, respectively." (Generation of images with tclean)
   - fitting: _not stated_
   - validation: _not stated_
5. **simulate single-dish images**: Convolve the model image with imsmooth to 62.9 arcsec (ALMA TP) or 25 arcsec (IRAM-30m at 100 GHz); add radiometer-equation noise for noisy SD runs  
  > "We produce simulations of TP observations at a resolution" (Simulation of SD images with imsmooth); "we convolve the synthetic image at the resolution of 25 arcsec" (Data combination with a large SD); "Likewise, we add an additional thermal noise to our SD data using the radiometer formula with similar" (Thermal noise)
   - software: CASA, imsmooth
   - parameter: TP resolution 62.9 arcsec; IRAM-30m resolution 25 arcsec  
  > "of 62.9 arcsec." (Simulation of SD images with imsmooth); "we convolve the synthetic image at the resolution of 25 arcsec" (Data combination with a large SD)
   - fitting: _not stated_
   - validation: _not stated_
6. **combine interferometric and SD data**: 12m+7m via concat then joint tclean; add TP with CASA feather (sdfactor 1.0) or MACF; replace 7m+TP by an IRAM-30m image with MACF for the large-SD test  
  > "which concatenates several visibility datasets, applying weights of 1 and 0.116 to the simulated 12m and 7m visibilities, respectively" (Data combination methods); "a parameter used to adjust the flux scale of the SD image, to 1.0" (Data combination methods); "the MACF method first introduces the SD image as source model during the cleaning process of the interferometric visibilities" (Data combination methods)
   - software: CASA, concat, feather, tclean
   - parameter: concat weights 1 (12m) and 0.116 (7m)  
  > "applying weights of 1 and 0.116 to the simulated 12m and 7m visibilities, respectively" (Data combination methods)
   - parameter: feather sdfactor = 1.0  
  > "a parameter used to adjust the flux scale of the SD image, to 1.0" (Data combination methods)
   - fitting: _not stated_
   - validation: compared against the known input model; Feather and MACF differences stay below 10%  
  > "However their differences are always below 10" (Observing isolated cores)
7. **measure recovered flux, peak and FWHM**: Extract a radial profile from a cut along the x axis of each image, integrate it for total flux, fit a Gaussian for peak and FWHM, and compare with the input model and the beam-convolved expected FWHM  
  > "we extract a radial profile from a cut along the x axis of each image, as done for cores" (Effects on elongated geometries); "with respect to the input model (reference) for the different interferometric (inverted triangles) and combined (circles) reductions" (Quantifying the effects of the short-spacing information in simple geometries)
   - software: CASA
   - parameter: expected observed FWHM = input FWHM convolved with the beam in quadrature  
  > "convolved with the beam resolution (added in quadrature)" (Quantifying the effects of the short-spacing information in simple geometries)
   - fitting: Gaussian fit to the radial profile for intensity peak and FWHM; sampler, priors and likelihood not stated  
  > "We further fit the resulting radial profile with a Gaussian function to estimate the intensity peak and the FWHM, similar to observations." (Quantifying the effects of the short-spacing information in simple geometries)
   - validation: perfect-recovery expectation (grey line) and input reference profiles  
  > "convolved with the beam resolution (added in quadrature)" (Quantifying the effects of the short-spacing information in simple geometries)
8. **analyse the interferometric PSF**: Compare u-v coverage and PSF images and radial cuts of 12m, 7m and 12m+7m simulations against an ideal Gaussian PSF  
  > "The interferometer PSF is the inverse Fourier transform of the u-v components sampled during the observation." (Point-Spread-Function (PSF) analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
9. **test sensitivity requirement of SD data**: Compute the SD to interferometer integration time ratio from the Mason and Brogan formula, simulate IRAM-30m noise at 1, 5 and 10 times the prediction for a FWHM = 30 arcsec core and combine with MACF  
  > "We simulate these observations setting the SD noise as 1, 5, and 10 times the above theoretical predictions." (On the SD sensitivity for data combination)
   - software: CASA
   - parameter: tau_SD about 4 tau_int for 12m C43-1 in Cycle 9 and IRAM-30m  
  > "Considering the ALMA 12m array in configuration C43-1 in Cycle 9 and IRAM-30m" (On the SD sensitivity for data combination)
   - assumption: same spectral setup, antenna efficiencies and system temperature  
  > "These estimates assumed to observe with the same spectral setup, antenna efficiencies, and system temperature." (On the SD sensitivity for data combination (footnote))
   - fitting: _not stated_
   - validation: recovered peak, FWHM and profile remain stable within 10-20% as SD noise rises  
  > "Even when the noise significantly increases, the recovered characteristics of the target source (i.e. flux peak, FWHM, and radial profile) remain stable (within 10-20%)." (On the SD sensitivity for data combination)
10. **compare with real OMC-3 ALMA data**: Extract radial cuts perpendicular to each of 23 fibers in 12m-alone, 12m+IRAM-30m Feather and MACF images and compare flux, peak and FWHM normalised to the 12m+IRAM-30m MACF reference with the simulation trends  
  > "we extract several radial cuts perpendicular to each fiber axis and analyse their radial profiles." (Comparisons with real ALMA observations); "we assume the ALMA 12m + IRAM-30m MACF observations as reference and compare other results normalized against it" (Comparisons with real ALMA observations)
   - software: CASA
   - parameter: 23 small-scale filaments (fibers) in OMC-3  
  > "We have characterized the emission in these maps from the analysis of the 23 small-scale filaments" (Comparisons with real ALMA observations)
   - assumption: 12m + IRAM-30m MACF map taken as the true emission distribution  
  > "we assume the ALMA 12m + IRAM-30m MACF observations as reference and compare other results normalized against it" (Comparisons with real ALMA observations)
   - fitting: _not stated_
   - validation: observed trends agree with simulation predictions for cores and filaments  
  > "These new observational results are in close agreement with those in our simulations." (Comparisons with real ALMA observations)
11. **test bias on the core mass function**: Draw 500 core masses with Salpeter-like slope 1.35 in 0.5-10 Msun, assign FWHM uniformly in 5-30 arcsec, convert to column density and flux, simulate ALMA 12m, 7m and TP, then extract peak, FWHM and mass for the recovered CMF  
  > "We created a synthetic CMF drawing 500 core mass values following" (Observing the core mass function); "assign them random FWHM values from a uniform distribution between 5 (similar to" (Observing the core mass function)
   - software: CASA
   - parameter: homogeneous dust temperature T = 10 K; D = 414 pc  
  > "assuming a homogeneous dust temperature of T=10K." (Observing the core mass function); "at a distance of Orion (D=414 pc)" (Observing the core mass function)
   - fitting: not stated; slopes in the plot are representative lines, not fits  
  > "do not represent a fit of the distributions, but only representative slopes that can describe the data to better compare them" (Observing the core mass function)
   - validation: recovered CMFs compared with the input distribution  
  > "We display the distinct recovered CMFs (line histograms) and compare them with our input distribution (grey histogram)" (Observing the core mass function)

## Software

- **CASA** v.6.5.2: simulating ALMA observations and imaging them  
  > "We run our simulations in CASA v.6.5.2" (ALMA simulations)
- **simobserve** : simulating the visibility MeasurementSet from a model image  
  > "we generated their corresponding ALMA visibilities using the task" (Generation of visibilities with simobserve)
- **tclean** : CLEAN imaging of simulated visibilities and joint deconvolution  
  > "This task is based on the CLEAN algorithm (cite: 1974Hogbom)" (Generation of images with tclean)
- **imsmooth** : convolving images to a common beam and simulating SD images  
  > "which convolves the synthetic image at the required resolution" (Simulation of SD images with imsmooth)
- **concat** : concatenating 12m and 7m visibilities with weights  
  > "which concatenates several visibility datasets" (Data combination methods)
- **feather** : Feather combination of interferometric and TP images  
  > "The Feather method is implemented in CASA as the" (Data combination methods)
- **ALminer** : querying the ALMA Science Archive for GOUS statistics  
  > "we queried the ALMA Science Archive using the ALminer toolkit (cite: 2023Ahmadi)" (Data combination with ALMA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| fraction of GOUS requesting only 12m among ISM mosaic GOUS, Cycles 6-9 | >40% | not stated | percent | 1 | of GOUS requesting only 12m observations (blue squares) |
| fraction of GOUS requesting 12m+7m+TP | consistently below ~50% | not stated | percent | 1 | the number of GOUS requesting 12m+7m+TP (red circles) in the last years has been consistently below |
| ALMA 12m alone flux recovery for Gaussian cores near MRS (12m) | up to 20% | not stated | percent | 7 | the ALMA 12m alone is only able to recover only up to 20 |
| ALMA 12m + 7m flux recovery for FWHM = 30 arcsec core (profile peak) | ~80% | not stated | percent | 7 | On the other hand, the ALMA 12m + 7m array (orange line) recovers higher flux values |
| flux recovery of Feather and MACF for Gaussian cores | >=80% independent of core size | not stated | percent | 7 | independent of the core size. |
| recovered FWHM of cores with size about MRS(12m) in 12m alone | ~15 arcsec (almost a factor of 2 below input) | not stated | arcsec | 7 | the estimated FWHM is around 15 arcsec, almost a factor of 2 lower than |
| flux loss of 12m alone for Gaussian filaments near MRS(12m) | almost 95% | not stated | percent | 7 | the ALMA 12m alone is losing almost 95 |
| recovered FWHM of Gaussian filaments near MRS(12m) in 12m alone | ~10 arcsec (almost a factor of 3 below reference) | not stated | arcsec | 7 | the estimated FWHM is around 10 arcsec, almost a factor of 3 lower than the reference value. |
| 12m + 7m combined PSF sidelobe near 6 arcsec | ~7% of peak | not stated | percent | 8 | with an estimated peak intensity around 7 |
| tolerance of combined image to SD noise | stable within 10-20% up to 5x (and 10x) the theoretical SD noise | not stated | percent | 9 | remain stable (within 10-20%). |
| accuracy of ALMA 12m + IRAM-30m MACF versus model values | within less than ~10% | not stated | percent | 6 | with respect to the actual model values |
| scatter of real OMC-3 12m-alone results about the filament prediction | factor of ~2 | not stated | dimensionless | 10 | show a significant scatter of a factor of |
| CMF slope recovered with ALMA 12m alone (input alpha = 1.35) | alpha = -1.18 | not stated | dimensionless | 11 | The CMF observed using only the ALMA 12m alone (blue histogram) shows a shallower distribution |
| truncation of 12m-alone FWHM distribution in the CMF test | ~18 arcsec | not stated | arcsec | 11 | The distribution recovered by the ALMA 12m alone (blue histogram) is truncated at |

## Qualitative findings

- Interferometric filtering makes sources look narrower and fainter, with negative sidelobes, even for sizes below the MRS  
  > "As a result, sources observed with interferometers appear narrower and fainter than what they actually are." (Summary and conclusions)
- Elongated filaments suffer more than cores of similar FWHM  
  > "filtering effects in elongated (filament-like) structures appear to be more severe than in the case of cores of similar" (Filaments)
- Replacing 7m+TP with a large SD (IRAM-30m) improves recovery, even if the SD is noisier than expected  
  > "Additional tests demonstrate that the emission recovery of cores and filaments at all scales is further improved if the 7m+TP data are replaced by additional maps obtained by a larger SD telescope" (abstract)
- Lack of short spacings produces an apparent top-heavy CMF from 12m-alone data  
  > "leading to the systematic underestimation of all core masses in large statistical samples producing apparent top-heavy CMF" (Observing the core mass function)

## Claim tuples

- H: Does ALMA 12m-alone filtering corrupt core and filament properties before the MRS is reached? | E: Noise-free CASA simulations of Gaussian cores and filaments of increasing FWHM, measuring recovered flux, peak and FWHM with 12m alone | R: Large flux losses and FWHM underestimation already appear at sizes below the MRS (12m alone ~20% flux recovery at MRS for cores, ~95% loss for filaments) | F: 12m-alone data systematically bias derived physical properties well before the MRS | **supported**
- H: Does adding the ACA 7m array solve the short-spacing problem? | E: Compare 12m alone with 12m+7m in cores, filaments and PSF analysis | R: 12m+7m recovers more flux but still loses emission above ~30 arcsec and adds a ~7% PSF sidelobe | F: 7m improves recovery only partially and degrades the PSF | **partially**
- H: Does adding Total Power data recover the true sky emission? | E: Feather and MACF combinations of 12m+7m with simulated TP | R: Flux recovery >=80% for cores and ~100% for Gaussian filaments; MACF slightly better than Feather within 10% | F: Total Power is needed to recover emission down to a few beam sizes with <10% error | **supported**
- H: Is a large single dish such as the IRAM-30m better than ACA-7m+TP, and must its sensitivity match the interferometer? | E: Combine 12m with a simulated 25 arcsec SD using MACF and raise SD noise to 1, 5 and 10 times the prediction | R: 12m+IRAM-30m MACF is the best method (within ~10% of the model) and tolerates SD noise up to ~5x | F: A large SD gives better recovery and the sensitivity match can be relaxed | **supported**
- H: Do the simulated biases appear in real ALMA data? | E: Compare 12m alone and 12m+IRAM-30m Feather and MACF radial profiles of 23 OMC-3 fibers with simulated trends | R: 12m-alone fibers depart from the reference following the simulated trends with a scatter of a factor ~2 | F: Real OMC-3 data confirm the filtering effects | **supported**
- H: Can interferometric filtering bias the observed core mass function? | E: Simulate 500 cores with a Salpeter-like CMF and recover masses with 12m alone and MACF | R: 12m alone gives a shallower CMF (alpha = -1.18) shifted to low masses; MACF reproduces the input slope | F: Filtering can produce an apparent top-heavy CMF | **supported**

## Reasoning

- Why this data: OMC-3 chosen as a complex filament and core region used to test the simulations  
  > "OMC-3 shows a prominent and complex substructure of filaments and cores becoming an ideal testbed for our simulations." (Comparisons with real ALMA observations)
- Why this method: Observation times follow official recommendations to match array sensitivities; several CASA combination methods are compared  
  > "following the official recommendations to match the sensitivity of the different ALMA arrays" (Generation of visibilities with simobserve); "To overcome the short-spacing problem we test different data combination methods already implemented in CASA" (Data combination methods)
- Alternative: 12m alone, 12m+7m, Feather, MACF and 12m+IRAM-30m MACF were compared as alternatives  
  > "To overcome the short-spacing problem we test different data combination methods already implemented in CASA" (Data combination methods); "We simulate the observations of a SD telescope larger than the ALMA TP (12m antennas) to be combined with the ALMA 12m array, replacing the ACA-7m and the TP." (Data combination with a large SD)
- How they decided it was enough: _not stated_
- Limitation (authors): Only Band 3 and the most compact 12m configuration were simulated  
  > "Additional work is needed to quantify these effects using different ALMA baselines and bands." (Comparisons with real ALMA observations)
- Limitation (authors): Simple toy models differ from real complex ISM emission  
  > "Additional discrepancies are nonetheless expected given the simplicity of our synthetic toy models compared to the complex emission features seen in real ISM observations" (Comparisons with real ALMA observations)
- Limitation (authors): SD noise conclusions hold only for random high-frequency noise  
  > "We note that these conclusions might hold only in the case of SD data including random, high frequency noise." (On the SD sensitivity for data combination (footnote))
- Caveat (inferred, ours): Single noise-free realisation per model; no uncertainties are given on recovery fractions
- Caveat (inferred, ours): Only 100 GHz, one field position and C43-1, so conclusions at other bands and configurations are untested
- Caveat (inferred, ours): Real-data comparison uses the 12m+IRAM-30m MACF map as truth, which is itself not an independent ground truth
- Caveat (inferred, ours): TP is simulated by Gaussian smoothing only, not by a realistic scanning observation, so TP-specific systematics may be missing

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Antenna configuration files, imsize, gridder and deconvolver settings for tclean
- Missing: Profile cut definition, flux integration and fitting details
- Missing: Random seeds for noisy runs
- Missing: OMC-3 reduction, fiber catalogue and IRAM-30m data (deferred to Paper I and Paper III)
- Data volume (inferred): Simulations: well under 1 GB; optional OMC-3 Band 3 12m raw data plus IRAM-30m maps: tens of GB
- Score (inferred): 4/5, On a 1-5 scale: the simulation chain (CASA 6.5.2, array setups, imaging and combination parameters) is given in good detail, but several tclean and measurement settings are missing and the real-data part depends on other papers.
- Rediscovery candidate: yes, The core results come from synthetic observations that need no archive data and have numeric answers; the real OMC-3 part depends on Paper I processing.

## Links

- Method: Plunkett et al. 2023 (cite: 2023Plunkett) (Data combination methods in CASA including concat weighting and MACF)
- Method: Hacar et al. 2024 (cite: 2024Hacar) (Observations, reduction, imaging and combination of the OMC-3 data (EMERGE Paper I))
- Method: ALMA Cycle 10 Technical Handbook (cite: 2023Cortes) (Resolution, MRS and integration time recommendations)
- Method: Mason & Brogan 2013 (cite: 2013Mason) (Integration time ratio between interferometer and SD)
- Companion: Hacar et al. 2024 (cite: 2024Hacar) (EMERGE Paper I, survey and OMC-3 observations)
- Companion: Socci et al. 2024 (cite: 2024Socci) (EMERGE Paper III, fiber analysis of OMC-3)
- Related: EMERGE (Emergence of high-mass stars in complex fiber networks)
- Related: ALMA-IMF Large Program

## Checks

```json
{
 "quotes": 150,
 "quotes_ok": 150,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 133,
  "stated": 92,
  "rate": 0.692
 },
 "evidence_ok": true
}
```
