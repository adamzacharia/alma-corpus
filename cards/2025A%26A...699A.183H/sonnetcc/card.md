# Spatially resolved spectrophotometric SED modeling of NGC 253's central molecular zone: I. Star formation in extragalactic giant molecular clouds

`2025A&A...699A.183H` | Astronomy and Astrophysics 2025 | first author: Humire, Pedro K. | arXiv: 2501.15082 | DOI: 10.1051/0004-6361/202553897

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, star_formation
- Question: Build the first spatially-resolved panchromatic (near-UV to cm) SED of GMCs in the NGC 253 central molecular zone at 3 arcsec (~51 pc) and derive SFRs, stellar and dust masses, and test monochromatic SFR tracers against the SED values  
  > "This study aims to produce and analyze the physical properties of the first spatially-resolved multi-wavelength SED of an extragalactic source that covers six decades in frequency" (abstract); "we also highlight the importance of testing tracers or proxies that focus on a single wavelength range against the values provided by the full SED" (1 Introduction)
- Target **NGC 253 CMZ, GMCs 1-10**: coordinates ICRS positions of GMC 1-10 listed in Table 1 (RA 00h47m31.93s-34.24s, Dec -25d17'29.00''..07.84''); e.g. GMC 5 at 33.16s / 17.30''  
  > "GMC positions taken from (cite: Harada2024) except for GMCs 3, 4, and 10, that were obtained using CPROPS (cite: Rosolowsky2006) on ALCHEMI data" (Table 1 notes); "the redshift was taken from the SIMBAD Astronomical Database (cite: Wenger2000)" (2.5 EVLA / 3.1 GalaPy); "we have assumed a distance of 3.5 Mpc to NGC 253 (cite: Rekola2005)" (4.3.3 Radio cm continuum and FIR); z/distance d = 3.5 Mpc; z = 0.000864 (SIMBAD, as input to GalaPy)  
  > "GMC positions taken from (cite: Harada2024) except for GMCs 3, 4, and 10, that were obtained using CPROPS (cite: Rosolowsky2006) on ALCHEMI data" (Table 1 notes); "the redshift was taken from the SIMBAD Astronomical Database (cite: Wenger2000)" (2.5 EVLA / 3.1 GalaPy); "we have assumed a distance of 3.5 Mpc to NGC 253 (cite: Rekola2005)" (4.3.3 Radio cm continuum and FIR); distance from Rekola et al. 2005 for 3.5 Mpc; SIMBAD for redshift  
  > "GMC positions taken from (cite: Harada2024) except for GMCs 3, 4, and 10, that were obtained using CPROPS (cite: Rosolowsky2006) on ALCHEMI data" (Table 1 notes); "the redshift was taken from the SIMBAD Astronomical Database (cite: Wenger2000)" (2.5 EVLA / 3.1 GalaPy); "we have assumed a distance of 3.5 Mpc to NGC 253 (cite: Rekola2005)" (4.3.3 Radio cm continuum and FIR)

## Data provenance

- ALMA projects: 2017.1.00161.L, 2018.1.00162.S
- bands: Bands 3 to 7 (84-373 GHz) complete spectral scan; continuum maps shown at Bands 3, 4, 6, 7; photometry tabulated for B3-B7  
  > "unbiased complete spectral scan across the ALMA bands 3 to 7 (84–373 GHz," (2.4 ALMA); "continuum emission (in mJy) of the CMZ of NGC 253 at ALMA Bands 3, 4, 6, and 7 (100, 144, 243, and 324 GHz, respectively)" (2.4 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m and 7m arrays  
  > "The observations were carried out using both 12m and 7m antenna arrays aiming to retrieve extended emission" (2.4 ALMA)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.6 arcsec common beam; ~8-9 km/s spectral resolution  
  > "the data were imaged to common angular and spectral resolutions of 1.6$''$ and $\sim$8–9 km s$^{-1}$, respectively" (2.4 ALMA)
- max recoverable scale: theta_LAS = 15 arcsec for ALMA photometric points  
  > "| ALMA/B7 | 9,252,854 | $1.6$ | 15 |" (Table of photometry (observations))
- sensitivity: RMS 0.18 to 5.0 mJy/beam in 8-9 km/s channels  
  > "The flux density RMS noise ranges from 0.18 to 5.0 mJy beam$^{-1}$ in the 8–9 km s$^{-1}$ channels." (2.4 ALMA)
- time on source: _not stated_
- observing dates: Cycles 5 and 6  
  > "ALMA observations of NGC 253 were conducted during Cycles 5 and 6 as part of the ALCHEMI large program." (2.4 ALMA)
- pi or archival as stated: Archival ALCHEMI large program data  
  > "We retrieve archival data from near-UV to centimeter wavelengths, covering six decades of spectral range." (abstract)
- Line: H40alpha (RRL) H40alpha (99.02 GHz)
- Line: 13CS and 13C34S 13C34S Ju=2 to 8 (13CS transitions not listed) (not stated)
- Other facility **S-PLUS**: 12-filter optical photometry (DR5, internal collaboration), 1.5 arcsec resolution  
  > "we have used images in all 12 available filters from the S-PLUS fifth data release (available for internal collaboration)" (2.1 S-PLUS)
- Other facility **VLT/NaCo, VLT/VISIR and HST**: Near/mid-IR and optical images taken from Fernandez-Ontiveros et al. 2009  
  > "This study incorporates the dataset presented in (cite: FernandezOntiveros2009), including Adaptive Optics images from the Very Large Telescope/NaCo" (2.2 VLT and HST)
- Other facility **Spitzer/IRAC**: 3.6-8.0 micron mosaics from the Spitzer Heritage Archive  
  > "We retrieved Spitzer/IRAC mosaic images from the Spitzer Heritage Archive" (2.3 Spitzer/IRAC)
- Other facility **EVLA**: X-band (3 cm) archival image and Ka-band (33 GHz) image from Kepley et al. 2011  
  > "we used a 1 cm (33 GHz; Ka-Band) continuum image presented in (cite: Kepley2011)" (2.5 EVLA)
- Other facility **VLA**: Continuum maps processed with the AIPS VLA pipeline  
  > "We retrieve Karl G. Jansky Very Large Array (VLA) continuum maps processed with the AIPS VLA pipeline by Lorant Sjouwerman (NRAO)" (2.6 VLA)
- Other facility **VLT/MUSE**: Archival optical IFU spectra (ID 0102.B-0078(A)) for STARLIGHT and emission-line diagnostics  
  > "We fit archival MUSE data (ID:0102.B-0078(A), PI: Laura Zschaechner) in the 4600–9350Å range" (4.2 Optical spectral fitting)
- Other facility **Herschel/PACS**: Level 2.5 images at 70, 100, 160 micron used only in a 9 arcsec aperture test  
  > "we further retrieved archival Herschel PACS observations selecting level 2.5 PACS images at 70, 100, and 160 $\mu$m" (5.1 Reliability of our SED model along the FIR window)
- External data: GMC positions (except GMCs 3, 4, 10)  
  > "GMC positions taken from (cite: Harada2024) except for GMCs 3, 4, and 10" (Table 1 notes) [from Harada et al. 2024 (cite: Harada2024)]
- External data: Optical/IR VLT and HST images/dataset  
  > "This study incorporates the dataset presented in (cite: FernandezOntiveros2009)" (2.2 VLT and HST) [from (cite: FernandezOntiveros2009)]
- External data: 33 GHz Ka-band EVLA continuum image  
  > "we used a 1 cm (33 GHz; Ka-Band) continuum image presented in (cite: Kepley2011)" (2.5 EVLA) [from (cite: Kepley2011)]
- External data: GMC 3, 4, 10 coordinates  
  > "A. K. Leroy (private communication) provided modified GMC coordinates tailored to the ALCHEMI data for the collaboration" (2.7 GMC positions) [from A. K. Leroy, private communication; (cite: Leroy2015)]
- External data: 70% free-free correction of H40alpha total emission  
  > "after applying a correction of 70% to H40$\alpha$’s total emission, as described in (cite: Bendo2015)" (4.3.2 Radio recombination lines) [from (cite: Bendo2015)]
- External data: Distance of NGC 253 (3.5 Mpc)  
  > "we have assumed a distance of 3.5 Mpc to NGC 253 (cite: Rekola2005)" (4.3.3 Radio cm continuum and FIR) [from (cite: Rekola2005)]
- External data: Age-metallicity relation of sub-giant stars  
  > "Comparing this latter result with the age-metallicity relation presented in Fig. 2a of (cite: Xiang2022)" (9 Sulfur ratios and Age-metallicity relation in GMC 5) [from (cite: Xiang2022)]
- External data: 32S/34S versus [Fe/H] relation  
  > "using the relation in Table 3 of (cite: Kobayashi2011)" (9 Sulfur ratios and Age-metallicity relation in GMC 5) [from (cite: Kobayashi2011)]
- Simulation/model as data: GalaPy parsec22.NTL SSP library (refined version) and CIGALE Bruzual and Charlot 2003 SSPs used as model grids  
  > "This library ensures a dense wavelength grid with a minimum of 128 values per order of magnitude within its 2189-point grid." (3.1.2 Simple stellar populations); "The modeling was based on the widely-used (cite: Bruzual2003) SSPs" (3.2 CIGALE photometric SED fitting)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: ALCHEMI data products imaged by the ALCHEMI team; calibration and imaging deferred to Martin et al. 2021  
  > "A full description of the dataset, calibration, and imaging is provided by (cite: Martin2021)." (2.4 ALMA)
- flux calibrator: _not stated_
- flux scale uncertainty: absolute 10-15%, adopted 15% for ALCHEMI fluxes  
  > "The absolute flux density uncertainty was reported to be of order 10 to 15%." (2.4 ALMA); "We conservatively assume an uncertainty of 15% for our extracted ALCHEMI fluxes." (2.4 ALMA)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: hogbom, standard gridder (applied to EVLA X-band data, not ALMA)  
  > "with a standard gridder and a hogbom deconvolver inside the Common Astronomy Software Applications (CASA) package" (2.5 EVLA)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.6 arcsec common beam for ALCHEMI maps; EVLA X-band convolved to 1.6 arcsec circular; Ka-band 1.8 arcsec  
  > "to convolve the X Band EVLA continuum image to a common circular beam of 1.6$''$, matching that of ALCHEMI" (2.5 EVLA)
- final rms: 0.18 to 5.0 mJy/beam in 8-9 km/s channels  
  > "The flux density RMS noise ranges from 0.18 to 5.0 mJy beam$^{-1}$ in the 8–9 km s$^{-1}$ channels." (2.4 ALMA)

### Inherited from earlier work

- ALCHEMI dataset, calibration and imaging  
  > "A full description of the dataset, calibration, and imaging is provided by (cite: Martin2021)." (2.4 ALMA) [from (cite: Martin2021)]
- VLT/HST observation details  
  > "We refer the reader to (cite: FernandezOntiveros2009) for further details." (2.2 VLT and HST) [from (cite: FernandezOntiveros2009)]
- H40alpha SFR approach  
  > "Following the approach of (cite: Bendo2015)" (4.3.2 Radio recombination lines) [from (cite: Bendo2015)]
- CIGALE delayed SFH plus burst  
  > "with an additional burst component (cite: ciesla2015)" (3.2 CIGALE photometric SED fitting) [from (cite: ciesla2015)]
- LTE spectra of GMCs and LSR velocities  
  > "(see (cite: Humire2022) for further information)" (Table 1 notes) [from (cite: Humire2022)]

### Not stated but needed to reproduce (our reading)

- How the 3 arcsec aperture fluxes were measured from the ALCHEMI continuum maps (continuum definition, line-free channels, primary-beam correction, aperture centering software)
- ALMA continuum bandwidth/frequency selection behind each band flux, and flux scale/calibrator details (deferred to Martin et al. 2021)
- GalaPy sampler settings (number of walkers, steps, convergence) and likelihood form
- Full per-GMC GalaPy prior table beyond the listed ranges, and the GalaPy version
- CIGALE module versions and exact parameter grid for each GMC, including the IMF actually used
- STARLIGHT configuration (base file, masks, weight scheme values)
- Access to S-PLUS DR5 images (internal to the collaboration) and the exact VLA/EVLA image files
- How GMC 4/5 stellar masses and ages were propagated into dust-to-stellar ratios and aperture corrections

## Analysis recipe

1. **Extract 3 arcsec aperture photometry for 10 GMCs**: Fluxes extracted in a uniform 3 arcsec diameter aperture from images of all facilities at each GMC position  
  > "we extract fluxes using a uniform aperture size with a 3$\ensuremath{''}$ diameter, despite the varying angular resolutions across the sample" (2 Observations)
   - software: CASA
   - parameter: Aperture diameter 3 arcsec (~51 pc); uncertainties 10% for all data and 15% for ALMA  
  > "Uncertainties were assumed to be of the order of 10% for all the sample except for ALMA data, where we assume 15%." (Table notes (photometry))
   - assumption: Distance 3.5 Mpc  
  > "at the assumed distance of NGC 253 of 3.5 Mpc" (2.7 GMC positions)
   - fitting: _not stated_
   - validation: _not stated_
2. **Homogenize EVLA/VLA radio images**: EVLA X-band cleaned with tclean and smoothed to a common beam with imsmooth; Jy/beam converted to Jy by dividing by beam area; VLA maps not convolved  
  > "we converted them into Janskys by dividing their flux by the beam area in pixels" (2.5 EVLA); "we decided not to convolve our VLA continuum maps" (2.6 VLA)
   - software: CASA
   - fitting: _not stated_
   - validation: Summed fluxes before and after imsmooth convolution differ by less than 10% for VLA  
  > "we observed differences of less than 10% (i.e., less than the instrumental uncertainties)" (2.6 VLA)
3. **Fit panchromatic SEDs with GalaPy (primary)**: In-Situ SFH model with parsec22.NTL SSPs, two-component age-dependent dust model, Chabrier IMF, one isolated molecular cloud per GMC, with free parameters over given priors  
  > "We perform the SED fitting of our selected GMCs with GalaPy (cite: Ronconi2024)" (3.1 GalaPy photometric SED fitting); "For our models, we use the default In-Situ SFH model" (3.1.1 The In-Situ model)
   - software: GalaPy
   - parameter: Parameter ranges for all GMCs and per-GMC tuned ranges listed in Tables 2 and variable-parameter table  
  > "A list of all common parameter ranges and individual values used to model the SEDs in the ten GMCs is provided in Table" (3.1.3 Dust model)
   - parameter: Ages restricted to 10^6-11 or 10^6-12 yr  
  > "a permitted range of 10$^{6-11}$ or 10$^{6-12}$ years was imposed to all GMCs" (8 Individual GMC properties)
   - assumption: Chabrier IMF; flat LCDM with h about 0.7; N_MC=1 (isolated GMCs)  
  > "GalaPy assumes a Chabrier initial mass function (cite: Chabrier2003)" (3.1 GalaPy photometric SED fitting); "as in this work we are assuming isolated GMCs" (3.1.3 Dust model)
   - fitting: _not stated_
   - validation: Cross-validated against CIGALE; best-fit SEDs compared with FIR 9 arcsec test including Herschel PACS  
  > "To cross-validate the results obtained from GalaPy, we compared them with those from the broadly used Code Investigating GALaxy Emission (CIGALE)." (3 Analysis)
4. **Fit SEDs with CIGALE for validation**: CIGALE 2022.1 UV-to-radio fits with delayed SFH plus burst, BC03 SSPs, Calzetti attenuation (dustatt_modified_starburst), Draine 2014 dust emission, radio module (q_IR); AGN version adds SKIRTOR  
  > "simultaneous UV-to-radio SED modeling with the CIGALE 2022.1 version (cite: Yang22)" (3.2 CIGALE photometric SED fitting); "Dust attenuation was modeled following the (cite: Calzetti2000) attenuation law" (3.2 CIGALE photometric SED fitting)
   - software: CIGALE
   - parameter: Parameter grid in CIGALE input table (tau_main 300-5000 Myr, f_burst, age, U_min, q_PAH, q_IR etc.)  
  > "The list of input parameters to CIGALE analysis without and with AGN component is given in Table" (7 CIGALE SED modeling with AGN component)
   - assumption: Solar-like metallicity; text states Chabrier IMF while the parameter table lists Salpeter  
  > "adopting the IMF of (cite: Chabrier2003) and assuming a solar-like metallicity" (3.2 CIGALE photometric SED fitting)
   - fitting: chi-squared minimization of data minus model weighted by uncertainties  
  > "CIGALE minimizes $\chi^2$ by measuring the difference between observed data and the model predictions, weighted by the uncertainties in the observations." (3.2 CIGALE photometric SED fitting)
   - validation: Mean reduced chi2 of 2.2 over ten GMCs  
  > "These CIGALE inputs have yielded a mean reduced $\chi^2$ of 2.2 for the ten GMCs studied in this work." (7 CIGALE SED modeling with AGN component)
5. **Fit stellar populations with STARLIGHT**: Simultaneous fit of MUSE spectra and S-PLUS photometry (3500-10000 A), MUSE scaled to iSDSS flux; non-parametric combination of SSPs  
  > "STARLIGHT uses a chi-squared minimization technique to find the best-fit non-parametric combination of stellar populations of different ages and metallicities from a pre-defined library." (3.3 Stellar population fitting with STARLIGHT); "we scale MUSE spectra to match the iSDSS band flux of S-PLUS" (4.2 Optical spectral fitting)
   - software: STARLIGHT
   - parameter: 16 log-spaced age bins, 5 metallicities, two-component extinction (A_V and extra for stars <=10 Myr)  
  > "assuming constant SFRs in 16 logarithmically spaced age bins with 5 different metallicities" (3.3 Stellar population fitting with STARLIGHT)
   - assumption: Charlot and Bruzual 2019 SSPs with PARSEC tracks, Chabrier IMF  
  > "using PARSEC (*PA*dova T *R*ieste *S*tellar *E*volution *C*ode) evolutionary tracks" (3.3 Stellar population fitting with STARLIGHT)
   - fitting: chi-squared minimization  
  > "STARLIGHT uses a chi-squared minimization technique" (3.3 Stellar population fitting with STARLIGHT)
   - validation: GalaPy stellar ages compared with STARLIGHT ages  
  > "In most cases (GMCs 1–9), GalaPy yields stellar age estimates that are consistent with those from STARLIGHT" (4.2 Optical spectral fitting)
6. **Derive attenuation and emission-line diagnostics**: Balmer-decrement A_V with Calzetti law, comparison with CIGALE and STARLIGHT A_V; BPT and WHAN diagrams from emission lines after stellar continuum subtraction  
  > "The attenuation from dust in HII regions can be estimated using the Balmer lines H$\alpha$ and H$\beta$" (4.2.2 Attenuation estimations); "The fluxes of emission lines from the MUSE spectra were measured in the pure nebular spectra" (4.2.1 Emission line diagnostic diagrams)
   - software: STARLIGHT
   - parameter: Intrinsic Halpha/Hbeta = 2.86  
  > "The intrinsic H$\alpha$/H$\beta$ flux ratio is 2.86 under typical conditions" (4.2.2 Attenuation estimations)
   - assumption: Calzetti reddening law A_Hbeta/A_V=1.14 and A_Halpha/A_V=0.82  
  > "where $A_{\mathrm{H}\beta}/A_{\rm{V}} = 1.14$ and $A_{\mathrm{H}\alpha}/A_{\rm{V}} = 0.82$ for a (cite: Calzetti2000) reddening law" (4.2.2 Attenuation estimations)
   - fitting: _not stated_
   - validation: Balmer A_V compared with CIGALE and STARLIGHT (median 16% and 27% differences)  
  > "CIGALE values of $A_{\rm{V}}$ are, in median, 16% lower than those from the Balmer decrement" (4.2.2 Attenuation estimations)
7. **Compare monochromatic SFR tracers with SED SFR**: Linear regression in log space: scipy linregress for initial values then emcee MCMC with uncertainties on both axes; Halpha (Kennicutt 1998), H40alpha RRL, cm radio continuum and IR bands against GalaPy SFR  
  > "The second step applied Bayesian inference through Markov Chain Monte Carlo (MCMC) sampling using the `emcee` Python package (cite: Foreman-Mackey2013)." (4.2.3 Linear regression); "by performing a linear regression in logarithmic space with all retrieved (E)VLA continuum images that detect at least four GMCs" (4.3.3 Radio cm continuum and FIR)
   - software: emcee, scipy, CASA
   - parameter: 1,000 iterations per fit, 50 walkers, first 100 discarded as burn-in  
  > "We ran 1,000 iterations per fit with 50 walkers, discarding the first 100 as burn-in to ensure convergence." (4.2.3 Linear regression)
   - assumption: Halpha SFR with A_Halpha = 0.82 x A_V(Balmer); distance 3.5 Mpc for mJy to erg/s/Hz  
  > "where $L(\mathrm{H\alpha})$ is corrected for extinction using $A_{\rm{H}\alpha} = 0.82 \times A_{\rm{V}}^{\rm Balmer}$." (4.3.1 Kennicutt (1998))
   - fitting: MCMC (emcee) priors initialised from scipy linregress; likelihood form not stated  
  > "to obtain initial priors" (4.2.3 Linear regression)
   - validation: Pearson correlation and slope vs 1:1 line; comparison with Bendo et al. 2015 total SFR  
  > "In general, the correlation is strong ($\langle R \rangle =$0.97)" (4.3.2 Radio recombination lines)
8. **Derive spaxel SFR from H40alpha and Ka-band**: H40alpha SFR following Bendo et al. 2015 with 70% free-free correction; Ka-band 32.8 GHz SFR via the log-log regression to GalaPy SFR  
  > "we derived the SFR for the nuclear GMCs (specifically GMCs 3 to 6)" (4.3.2 Radio recombination lines)
   - software: CASA
   - assumption: 70% of H40alpha emission is free-free  
  > "after applying a correction of 70% to H40$\alpha$’s total emission, as described in (cite: Bendo2015)" (4.3.2 Radio recombination lines)
   - fitting: _not stated_
   - validation: Total SFR over GMCs 3-7 consistent with Bendo et al. 2015 within uncertainties  
  > "consistent with (cite: Bendo2015)’s (free-free) value within uncertainties" (4.3.2 Radio recombination lines)
9. **Estimate age from 32S/34S metallicity in GMC 5**: LTE fit of 13CS and 13C34S spectra, 32S/34S converted to [Fe/H], compared to age-metallicity relation with skewed Gaussian least-squares fit  
  > "Assuming LTE conditions, we fitted the observed spectra with a single component to account for the very dense regions that CS isotopologues trace." (9 Sulfur ratios and Age-metallicity relation in GMC 5); "The fitting process involved optimizing the parameters of the skewed Gaussian function" (9 Sulfur ratios and Age-metallicity relation in GMC 5)
   - software: CASSIS, RADEX
   - parameter: 32S/34S range limited to values giving [Fe/H] <= 0.5 (ratio >= 13.3)  
  > "we expect $^{32}$S/$^{34}$S isotopologue ratios no lower than 13.3" (9 Sulfur ratios and Age-metallicity relation in GMC 5)
   - assumption: LTE, single component; CDMS spectroscopy  
  > "we have utilized the Cologne Database for Molecular Spectroscopy (cite: Mueller2005) for spectroscopic data" (9 Sulfur ratios and Age-metallicity relation in GMC 5)
   - fitting: Least-squares fit of skewed Gaussian to the age distribution; line fit by CASSIS (method not further described)  
  > "using a least-squares approach" (9 Sulfur ratios and Age-metallicity relation in GMC 5)
   - validation: Compared with Kobayashi et al. 2020 bulge-outflow model ages  
  > "Both results are in good agreement with the AMR-derived estimations." (9 Sulfur ratios and Age-metallicity relation in GMC 5)

## Software

- **GalaPy** : Primary panchromatic SED fitting (In-Situ SFH, parsec22.NTL SSPs, two-component dust)  
  > "we selected GalaPy as the primary tool for SED modeling, particularly for testing the radio-SF correlation" (3 Analysis)
- **CIGALE** 2022.1: UV-to-radio SED fitting for cross-validation, with and without SKIRTOR AGN  
  > "the CIGALE 2022.1 version (cite: Yang22)" (3.2 CIGALE photometric SED fitting)
- **STARLIGHT** latest version (Werle et al. 2019): Fitting MUSE spectra plus S-PLUS photometry and subtracting stellar continuum for emission lines  
  > "we applied the latest version of the code, described by (cite: Werle2019), to fit simultaneously the combined MUSE and S-PLUS data" (3.3 Stellar population fitting with STARLIGHT)
- **CASA** : tclean of EVLA X-band image; imsmooth for common beam; beam area statistics  
  > "inside the Common Astronomy Software Applications (CASA) package" (2.5 EVLA)
- **CPROPS** : Determining GMC 3, 4, 10 positions from ALCHEMI data  
  > "that were obtained using CPROPS (cite: Rosolowsky2006) on ALCHEMI data" (Table 1 notes)
- **emcee** : MCMC linear regressions with errors on both axes  
  > "using the `emcee` Python package (cite: Foreman-Mackey2013)" (4.2.3 Linear regression)
- **CASSIS** : LTE modeling of 13CS and 13C34S spectra  
  > "When performing non-LTE modeling, CASSIS functions as a wrapper for the RADEX code (cite: vanderTak2007)" (9 Sulfur ratios and Age-metallicity relation in GMC 5)
- **SKIRTOR** : AGN module in CIGALE  
  > "we incorporated the SKIRTOR module (cite: Stalevski2012; Stalevski2016)" (7 CIGALE SED modeling with AGN component)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SFR (GalaPy instantaneous), total of GMCs 4-6 in a 9 arcsec aperture | 1.620 | +0.201/-0.156 | Msun/yr | 3 | yields a SFR of $1.620^{+0.201}_{-0.156}~\text{M}_{\odot}\,\text{yr}^{-1}$ |
| Total SFR GMCs 3-7 (GalaPy, 9 arcsec region plus GMCs 3 and 7) | 1.729 | +0.201/-0.156 | Msun/yr | 3 | the total SFR raises to $1.729^{+0.201}_{-0.156}~\text{M}_{\odot}\,\text{yr}^{-1}$ |
| GMC 5 instantaneous SFR (GalaPy) | 6450e-4 (0.645) | +600/-590 (x1e-4) | Msun/yr | 3 | / 5 / 6450$_{-590}^{+600}$ / 8.620$_{-0.105}^{+0.124}$ / |
| Diffuse dust temperature T_DD, 9 arcsec aperture SED | 68.8 | +7.8/-13.9 | K | 3 | of 68.8$_{-13.9}^{+7.8}$ K |
| Correlation between Ka-band and H40alpha SFR (all spaxels): mean Pearson R | 0.97 | not stated | dimensionless | 8 | In general, the correlation is strong ($\langle R \rangle =$0.97) |
| General slope of H40alpha SFR vs Ka-band SFR | 1.07 | 0.01 | dimensionless | 8 | with a general slope of 1.07$\pm$0.01 |
| Median log(Mdust/Mstar), CIGALE values | -2.32 | 0.29 | dex | 4 | $\log(M_{\rm dust}/M_{\star}) = -2.32 \pm 0.29$ (values from CIGALE) |
| Median log(Mdust/Mstar), GalaPy values | -2.89 | 0.45 | dex | 3 | $\log(M_{\rm dust}/M_{\star}) = -2.89 \pm 0.45$ |
| AGN fraction in CIGALE with AGN module | <7.5 (negligible) | not stated | percent | 4 | is negligible ($<$7.5%) |
| 32S/34S column density ratio in GMC 5 | 14.26 | +7.53/-4.72 | dimensionless | 9 | The resulting $^{32}$S/$^{34}$S column density ratio is 14.26$^{7.53}_{-4.72}$ |
| Age from age-metallicity relation for GMC 5 | 7.85 | +0.18/-5.39 | Gyr | 9 | is 7.85$^{+0.18}_{-5.39}$ Gyrs |
| Mean reduced chi2 of CIGALE fits | 2.2 | not stated | dimensionless | 4 | a mean reduced $\chi^2$ of 2.2 for the ten GMCs studied in this work |

## Qualitative findings

- Internal GMCs (3-6) have higher SFR, stellar and dust mass than external GMCs; dust mass is the clearest distinction  
  > "The above indicates that the dust mass is the clearest distinction between the two primary groups" (4.1.1 GMC characteristics)
- GMCs fall in the composite BPT zone, interpreted as starburst plus shocks rather than AGN  
  > "Instead, we prefer to describe them as “starburst$+$shocks” composites" (4.2.1 Emission line diagnostic diagrams)
- Two-component Charlot and Fall attenuation describes the GMC attenuation better than Calzetti  
  > "The better agreement of our model-inferred attenuation laws with the (cite: CharlotFall2000) prescription compared to (cite: Calzetti2000)" (4.2.2 Attenuation estimations)

## Claim tuples

- H: Do internal and external GMCs of the NGC 253 CMZ differ in star-forming properties? | E: GalaPy and CIGALE SED fits of 10 GMCs in 3 arcsec apertures | R: Internal GMCs have higher SFR, stellar mass, dust mass and bolometric luminosity | F: Significant heterogeneity within the CMZ, central GMCs more active | **supported**
- H: Which monochromatic bands best trace the panchromatic SFR on GMC scales? | E: Log-space MCMC regressions of cm radio, RRL and IR luminosities against GalaPy SFR | R: 33 GHz, H40alpha RRL and total IR (and 60 micron) correlate best, Ka-band closest to 1:1 | F: Certain cm bands reliably estimate SFR on GMC scales | **supported**
- H: Does an AGN contribute significantly to the CMZ emission? | E: BPT and WHAN diagrams from MUSE lines and CIGALE with SKIRTOR AGN module | R: GMCs lie in the composite zone, CIGALE AGN fraction below 7.5% | F: Shocks from stellar winds and supernovae, not AGN | **supported**
- H: Is Halpha a reliable SFR tracer in the dust-obscured CMZ? | E: Kennicutt Halpha SFR with Balmer extinction compared to SED SFRs | R: GalaPy SFRs tend to exceed Kennicutt-relation values | F: Halpha has significant limitations here and should be supplemented with dust-insensitive tracers | **supported**
- H: Are NGC 253 GMCs as dusty relative to stellar mass as high-z starbursts? | E: Compare Mdust/Mstar with literature CIGALE-based high-z values | R: Median log(Mdust/Mstar) -2.32 (CIGALE) and -2.89 (GalaPy) | F: Ratios are close to young dusty starbursts at high z | **supported**

## Reasoning

- Why this data: GMC selection is driven by ALCHEMI ALMA data  
  > "The selection of GMC positions to be analyzed in this study is driven by the ALMA data from the ALCHEMI project." (2.7 GMC positions)
- Why this method: GalaPy chosen because it self-consistently models radio emission in the SFH, needed for the radio data  
  > "Given that our study relies on extensive radio data, we selected GalaPy as the primary tool for SED modeling, particularly for testing the radio-SF correlation." (3 Analysis)
- Alternative: Allowing GMC 1 ages of ~1e5 yr was rejected; ages limited to >=1e6 yr because CO is observed  
  > "This restriction yielded SED shapes that are closer to the observed ones compared to those with an age of $\sim$10$^{5}$ years" (8 Individual GMC properties)
- How they decided it was enough: _not stated_
- Limitation (authors): No FIR photometry at 3 arcsec, so SED models have large freedom in the FIR  
  > "our SED models experienced considerable freedom in this specific wavelength range" (5.1 Reliability of our SED model along the FIR window)
- Limitation (authors): Large uncertainties on the observed Halpha/Hbeta ratio (10 to nearly 90%)  
  > "ranging from 10 to nearly 90%" (4.2.2 Attenuation estimations)
- Caveat (inferred, ours): ALMA enters only as 3 arcsec aperture fluxes with a flat 15% error from the ALCHEMI release; the flux extraction is not described
- Caveat (inferred, ours): CIGALE IMF is stated as Chabrier in text but Salpeter in the parameter table
- Caveat (inferred, ours): SFR comparisons use IR points derived from the GalaPy fit, so tracer tests are not independent
- Caveat (inferred, ours): GalaPy priors were tuned per GMC to remove bimodality, which can bias parameters
- Caveat (inferred, ours): Ka-band LAS (44 arcsec) is nominal while apertures sample extended emission; ALMA LAS 15 arcsec may miss flux

## Reproducibility

- Data public (paper): ALMA, VLA, Spitzer, MUSE and Herschel data described as archival; S-PLUS DR5 internal to the collaboration  
  > "(available for internal collaboration)" (2.1 S-PLUS); "We retrieve archival data from near-UV to centimeter wavelengths" (abstract)
- Products in archive: _not stated_
- Code: GalaPy is open source; the modified SSP library for VISIR bands is not yet released  
  > "an open-source application programming interface" (3.1 GalaPy photometric SED fitting); "This adjustment will be available in the next release of GalaPy." (3.1.2 Simple stellar populations)
- Missing: ALMA flux extraction details (continuum definition, aperture photometry tool)
- Missing: GalaPy and CIGALE per-GMC configuration files and GalaPy version
- Missing: S-PLUS DR5 images are internal; exact VLA/EVLA image products
- Missing: STARLIGHT configuration and base
- Data volume (inferred): Original ALCHEMI scan is large (hundreds of GB to TB); reproducing the SED fits needs only the published flux table (tiny), while re-measuring ALMA fluxes needs ALCHEMI continuum maps (several GB)
- Score (inferred): 3/5, The tabulated 3 arcsec fluxes, priors and public codes allow redoing the SED fits, but ALMA photometry extraction, per-GMC configs and some inputs (S-PLUS DR5) are not fully specified or public
- Rediscovery candidate: no, Part of the data is internal to a collaboration and the recipe lacks per-GMC settings and sampler details, so a clean redo is not guaranteed

## Links

- Method: Martin et al. 2021 (cite: Martin2021) (ALCHEMI dataset, calibration and imaging)
- Method: Ronconi et al. 2024 (cite: Ronconi2024) (GalaPy code and parameter table)
- Method: Yang et al. 2022 (cite: Yang22) (CIGALE 2022.1)
- Method: Werle et al. 2019 (cite: Werle2019) (STARLIGHT fitting spectra and photometry)
- Method: Bendo et al. 2015 (cite: Bendo2015) (H40alpha SFR approach)
- Companion: Harada et al. 2024 (cite: Harada2024) (GMC positions and ALCHEMI molecular PCA)
- Companion: Humire et al. 2022 (cite: Humire2022) (Methanol LTE modeling and LSR velocities)
- Companion: Leroy et al. 2015 (cite: Leroy2015) (Earlier GMC definition in NGC 253)
- Related: ALCHEMI
- Related: S-PLUS

## Checks

```json
{
 "quotes": 136,
 "quotes_ok": 136,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 122,
  "stated": 92,
  "rate": 0.754
 },
 "evidence_ok": true
}
```
