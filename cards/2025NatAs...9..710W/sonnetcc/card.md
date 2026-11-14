# A giant disk galaxy two billion years after the Big Bang

`2025NatAs...9..710W` | Nature Astronomy 2025 | first author: Wang, Weichen | arXiv: 2409.17956 | DOI: 10.1038/s41550-025-02500-2

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies
- Question: Is the z~3.25 galaxy 'Big Wheel' a giant rotationally supported disk, and what do its size, mass and kinematics imply for disk formation in an overdense region  
  > "Our observations reveal that the Big Wheel is a giant rotating disk with physical properties unique for" (abstract)
- Target **Big Wheel (galaxy in a bright-quasar field)**: coordinates RA 00h41m35.113s, Dec -49d37m12.42s (J2000)  
  > "00h41m35.113s" (Table 1); "-49d37m12.42s" (Table 1); "we fixed the redshift to the value measured from the NIRSpec spectrum" (Methods); z/distance z = 3.2452  
  > "00h41m35.113s" (Table 1); "-49d37m12.42s" (Table 1); "we fixed the redshift to the value measured from the NIRSpec spectrum" (Methods); distance from Redshift measured from the NIRSpec spectrum (H-alpha, [N II], H-beta lines)  
  > "00h41m35.113s" (Table 1); "-49d37m12.42s" (Table 1); "we fixed the redshift to the value measured from the NIRSpec spectrum" (Methods)

## Data provenance

- ALMA projects: 2021.1.00793.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.4'' x 1.3'' synthesized beam (FWHM) of the cleaned cube at 109.00 GHz  
  > "The synthesized beam size (FWHM) of the “cleaned" data cube is $1\rlap{.}''4\times1\rlap{.}''3$ at $109.00\,{\rm GHz}$." (Methods)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Cycle 8, PI: Cantalupo  
  > "The Big Wheel was also observed with the Atacama Large (sub-)Millimeter Array (ALMA) in Cycle 8 (ID: 2021.1.00793.S; PI: Cantalupo)" (Methods)
- Line: CO 4-3 (not stated)
- Other facility **JWST NIRCam**: Imaging in F150W2 and F322W2 (1632 s each), used for sizes and SED photometry  
  > "using the NIRCam filters, F150W2 and F322W2, each for 1632s of exposure" (Methods)
- Other facility **JWST NIRSpec (MSA)**: H-alpha slit spectroscopy of three slits (F170LP/G235H, R~3200) for rotation curve and redshift  
  > "Follow-up spectroscopic observations using NIRSpec were obtained as a part of the same JWST program as above." (Methods); "The exposure time was $\sim 3$ hours for each of the three MSA slits." (Methods)
- Other facility **HST ACS/WFC**: F625W and F814W imaging, used for photometry and morphology  
  > "HST filters ACS/WFC F625W and ACS/WFC F814W, for 10 and 12 orbits, respectively." (Methods)
- Other facility **VLT HAWK-I**: Ground-layer AO near-infrared imaging in CH4, H and Ks for SED photometry  
  > "We also obtained near-infrared data with the Very Large Telescope (VLT) in 2022 as part of a program in P110 (PI: Cantalupo)." (Methods)
- Other facility **Chandra ACIS**: 634 ks X-ray observation used to identify an AGN and in CIGALE SED fitting  
  > "The Big Wheel was also observed using the Advanced CCD Imaging Spectrometer onboard the Chandra X-ray Observatory during 2022-2023 (PI: Cantalupo), with a total of 634 ks of exposure." (Methods)
- External data: ALMA CO(4-3) observation of the Big Wheel and its quasar-field overdensity analysed in an earlier paper  
  > "was discovered serendipitously in a bright-quasar field at redshift ($z$) of 3.25 (cite: Pensabene2024)" (main text); "its serendipitous discovery in one of the largest overdensities of galaxies found so far at $z\gtrsim3$ (cite: Pensabene2024)" (main text) [from (cite: Pensabene2024)]
- External data: Literature kinematically confirmed disk galaxies at z=3-4 with sizes and masses, used for comparison in Fig. 3a  
  > "Disk galaxies at $z$=3-4 from the literature that were confirmed by kinematics and measured for size are included in Fig." (Methods) [from (cite: Gnerucci2011; Livermore2015; Turner2017; Gillman2019; Swinbank2015; Wu2023)]
- External data: Median size-mass trend of a z=0.1-0.5 galaxy sample  
  > "The size-mass relation of Mowla et al(cite: Mowla2019) is determined in the work as the median trend of a statistical galaxy sample at $z=0.1-0.5$." (Methods) [from (cite: Mowla2019)]
- External data: Observed size-mass relations at z~3 from two JWST studies (log-normal scatter 0.22 and 0.28 dex)  
  > "the most recent observations at $z\simeq3$, find a log-normal size distribution with an intrinsic scatter of $\simeq0.22-0.28$(cite: Ward2023; Varadaraj2024)" (main text) [from (cite: Ward2023; Varadaraj2024)]
- Simulation/model as data: Cosmological simulation size-mass predictions compared with the Big Wheel (Costantin2023; LaChance2024)  
  > "To the best of our knowledge, current cosmological simulations (cite: Costantin2023; LaChance2024), some of which are presented in Fig." (main text)

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

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Cleaned down to 1.5 sigma with a circular mask of 2'' radius  
  > "Data cleaning was performed down to $1.5\sigma$ with a circular mask of $2''$ in radius, which encloses emission of the galaxy in the cube." (Methods)
- multiscale scales: _not stated_
- continuum subtraction: Zeroth-order polynomial continuum fit, subtracted with CASA imcontsub  
  > "We fit the spectral continua with zeroth-order polynomials and subtracted them from the cube using the task" (Methods)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.4'' x 1.3'' (FWHM) at 109.00 GHz  
  > "The synthesized beam size (FWHM) of the “cleaned" data cube is $1\rlap{.}''4\times1\rlap{.}''3$ at $109.00\,{\rm GHz}$." (Methods)
- final rms: _not stated_

### Inherited from earlier work

- ALMA observation and data details given in the earlier ALMA paper  
  > "The Big Wheel was also observed with the Atacama Large (sub-)Millimeter Array (ALMA) in Cycle 8 (ID: 2021.1.00793.S; PI: Cantalupo), the details of which are provided in" (Methods) [from [14] (reference key not resolved in the text; the ALMA map is attributed to (cite: Pensabene2024))]
- CO-to-H2 conversion factors used for the gas mass  
  > "In addition, the gas mass was also measured from the ALMA data and listed in Tab. 1, obtained using the CO-to-H$_2$ conversion factors described in" (Methods) [from [14] (reference key not resolved in the text)]
- Bayesian priors and other SED-fitting assumptions  
  > "Other assumptions of the fitting procedure, including the forms of the Bayesian priors, are the same as described in" (Methods) [from [] (reference key lost in the text)]
- Relation combining v_rot and sigma_int to get circular velocity  
  > "Combining $v_\mathrm{rot}$ and $\sigma_\mathrm{int}$ using the commonly adopted relation in the literature(cite: Ubler2017)" (main text) [from (cite: Ubler2017)]

### Not stated but needed to reproduce (our reading)

- ALMA band, array configuration(s), spectral setup, observing dates and time on source (all deferred to the earlier ALMA paper)
- CASA version and calibration route (pipeline or manual), flux calibrator and flux-scale uncertainty
- tclean parameters: weighting and robust, cell size, image size, channel width, deconvolver, cleaning threshold basis (rms)
- Rest frequency adopted for CO(4-3) and the line-free channels used for the zeroth-order continuum fit
- Moment-1 threshold or masking and how the ALMA PSF was applied to the H-alpha model in Extended Data Fig. 9
- CO(4-3) line luminosity derivation, CO excitation ratio (r41 or similar) and alpha_CO used for the H2 mass
- Priors, walker counts, burn-in and likelihood for the emcee velocity-map fit and the 1D Gaussian fits
- Prospector priors, dust law and AGN parameters (deferred to unresolved references)

## Analysis recipe

1. **clean ALMA cube and subtract continuum**: Cleaned to 1.5 sigma inside a 2'' radius circular mask, then fit zeroth-order polynomial continuum and subtract with imcontsub  
  > "Data cleaning was performed down to $1.5\sigma$ with a circular mask of $2''$ in radius, which encloses emission of the galaxy in the cube." (Methods); "We fit the spectral continua with zeroth-order polynomials and subtracted them from the cube using the task" (Methods)
   - software: CASA
   - parameter: Cleaning depth 1.5 sigma; circular mask radius 2''  
  > "Data cleaning was performed down to $1.5\sigma$ with a circular mask of $2''$ in radius" (Methods)
   - parameter: Continuum model: zeroth-order polynomial  
  > "We fit the spectral continua with zeroth-order polynomials" (Methods)
   - fitting: _not stated_
   - validation: _not stated_
2. **make CO(4-3) velocity map and compare with H-alpha**: First-moment map of CO(4-3) profiles compared with the H-alpha velocity map  
  > "The CO velocity map of the Big Wheel galaxy from the ALMA observations was obtained through the first-moments of the CO(4–3) profiles." (Methods)
   - fitting: _not stated_
   - validation: CO kinematics consistent with H-alpha once the ALMA PSF is taken into account  
  > "The observed CO kinematics is quantitatively consistent with the H$\alpha$ kinematics once the ALMA PSF is taken into account" (Methods)
3. **derive molecular gas mass from CO**: Gas mass measured from the ALMA data using CO-to-H2 conversion factors described in the earlier ALMA paper  
  > "In addition, the gas mass was also measured from the ALMA data and listed in Tab. 1, obtained using the CO-to-H$_2$ conversion factors described in" (Methods)
   - fitting: _not stated_
   - validation: _not stated_
4. **measure H-alpha rotation and dispersion along NIRSpec slits**: 1D spectra from each 0.1 arcsec pixel row, convolved with the line spread function, fit with a Gaussian giving centroid (rotation) and width (dispersion)  
  > "One-dimensional H$\alpha$ kinematical profiles have been obtained from the 2D spectra from each pixel row, which spans 0.1 arcsec along the slit" (Methods); "The 1D spectra were then fit with a Gaussian using emcee." (Methods)
   - software: emcee
   - parameter: Smooth background and continua removed with a 3000 km/s median filter on each pixel row  
  > "The smooth background and galaxy continua have been removed by applying a median filter with a width of 3000 km/s to each pixel row of the 2D spectra" (Methods)
   - fitting: Gaussian line fit with emcee; priors not stated  
  > "The 1D spectra were then fit with a Gaussian using emcee." (Methods)
   - validation: _not stated_
5. **fit six-parameter disk model to velocity map**: Flat (pseudo-isothermal) rotation curve disk model built with galpy, fit to the observed velocity map with emcee; best fit from 50th percentiles  
  > "For the disk modeling, we adopted a flat rotation curve using the galpy python package (cite: Bovy2015)." (Methods); "The model map was fitted against the observed velocity map using emcee." (Methods)
   - software: galpy, emcee
   - parameter: Six free parameters: turnover location, plateau velocity, inclination, orientation, and centre (X, Y)  
  > "Then, we created a velocity map from this six-parameter disk model by calculating the velocity along the line of sight for each part of the disk." (Methods)
   - assumption: Rotation curve form corresponds to the pseudo-isothermal potential  
  > "The rotation curve model has a form corresponding to the commonly-used pseudo-isothermal potential(cite: Burkert1995)." (Methods)
   - fitting: emcee MCMC; 50th percentile of posteriors used for best fit, 16-84th percentiles for uncertainty; priors not stated  
  > "We calculated the 16-84th percentiles of the $v_\mathrm{rot}$ posterior as the 1-sigma uncertainty from fitting." (Methods)
   - validation: Beam smearing tested with a mock exponential-disk cube convolved with the PSF; velocity deviates by no more than 15 km/s except within 0.2 arcsec of the centre  
  > "We found that this map deviates from the intrinsic velocity map by no more than 15 km/s, except for the region within 0.2 arcsec of the center" (Methods)
6. **measure rest-frame optical half-light radius**: Non-parametric morphology (statmorph) on NIRCam F150W2 and F322W2 images, interpolated to rest-frame 0.5 micron  
  > "For each filter, we measured the radius of an ellipse enclosing half of the total light of the galaxy." (Methods); "It was calculated by interpolating between the radius values measured in the two NIRCam filters, under the assumption that the radius is a linear function of wavelength." (Methods)
   - software: statmorph
   - assumption: Radius is a linear function of wavelength between the two filters  
  > "under the assumption that the radius is a linear function of wavelength" (Methods)
   - fitting: Sersic profile fits with statmorph as a consistency check  
  > "As a check for consistency, we also measured the radius by fitting the Sérsic(cite: Sersic1963) profiles with statmorph using the PSFs measured from stars in the field." (Methods)
   - validation: 500 simulations of a convolved noisy exponential disk give size errors of 2.8% and 3.4%  
  > "We found from the distribution that the measured sizes deviate from the intrinsic value (1 arcsec) by only 2.8% and 3.4% for F150W2 and F322W2 at the 3-sigma confidence level" (Methods)
7. **derive stellar mass and SFR by SED fitting**: Prospector SED fit to seven-band photometry with redshift fixed, non-parametric continuity-prior SFH and Chabrier IMF  
  > "Second, we performed annulus-by-annulus spatially resolved SED fitting with prospector using the HST and JWST data." (Methods); "A non-parametric form of the star formation history with a prior favoring continuity(cite: Wang2024) was adopted, binned into seven consecutive ranges in look-back time" (Methods)
   - software: prospector, CIGALE, Source Extractor
   - parameter: Photometry in ACS F625W, ACS F814W, NIRCam F150W2, HAWKI CH4, H, Ks and NIRCam F322W2  
  > "Photometric flux densities measured from seven filters are used in the fit: ACS F625W, ACS F814W, NIRCam F150W2, HAWKI CH4, HAWKI H, HAWKI Ks, and NIRCam F322W2." (Methods)
   - assumption: Chabrier IMF  
  > "A Chabrier(cite: Chabrier2003) initial mass function (IMF)" (Methods)
   - fitting: Bayesian posteriors; 50th percentile as value, 5-95th percentiles as uncertainty, plus systematic term  
  > "The total stellar mass and SFR (averaged over 100 Myr) of the galaxy were calculated as the 50th-percentiles of the Bayesian posteriors." (Methods)
   - validation: Parametric delayed-exponential SFH refit (1.7e11 Msun) and CIGALE fit (2.5e11 Msun); AGN effect tested with aperture and annulus fits  
  > "Furthermore, we also performed SED fit using the code CIGALE" (Methods); "we conclude that the AGN has no significant impact on mass measurements." (Methods)
8. **estimate chance of finding such a large galaxy in random fields**: Compare observed size with expected size from two JWST size-mass relations and use their log-normal scatter  
  > "Therefore the corresponding probabilities of finding a galaxy equal to or larger than the Big Wheel in random fields are 2% and 0.6% according to the two studies, respectively." (Methods)
   - parameter: Observed size 0.41 dex and 0.70 dex larger than the two relations; scatter 0.22 and 0.28 dex  
  > "We found it to be 0.41 dex and 0.70 dex smaller than the observed size of the Big Wheel in log" (Methods)
   - assumption: Log-normal size distribution with intrinsic scatter from the cited studies  
  > "The distribution of sizes is well constrained as a log-normal in these studies with" (Methods)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Continuum subtraction of the ALMA cube with imcontsub  
  > "We fit the spectral continua with zeroth-order polynomials and subtracted them from the cube using the task" (Methods)
- **emcee** : Gaussian line fits and the disk-model velocity map fit  
  > "The model map was fitted against the observed velocity map using emcee." (Methods)
- **galpy** : Flat rotation curve disk model  
  > "For the disk modeling, we adopted a flat rotation curve using the galpy python package (cite: Bovy2015)." (Methods)
- **statmorph** : Non-parametric and Sersic half-light radius measurement  
  > "we also measured the radius by fitting the Sérsic(cite: Sersic1963) profiles with statmorph using the PSFs measured from stars in the field." (Methods)
- **prospector** : SED fitting for stellar mass and SFR  
  > "Second, we performed annulus-by-annulus spatially resolved SED fitting with prospector using the HST and JWST data." (Methods)
- **CIGALE** : Cross-check SED fit including X-ray flux  
  > "Furthermore, we also performed SED fit using the code CIGALE" (Methods)
- **Source Extractor** : Photometry in dual-image mode  
  > "Photometry was performed on the images described above using the Source Extractor tool" (Methods)
- **drizzle** : Resampling mosaics to a common 0.06 arcsec grid  
  > "the image mosaics were resampled to a common grid of 0.06$\times$0.06 arcsec pixels using the drizzle package" (Methods)
- **jwst pipeline** v1.9.3 (NIRCam); v1.11.3 (NIRSpec): Reduction of JWST imaging and NIRSpec data  
  > "official jwst pipeline (v1.9.3;" (Methods); "The data for each slit were reduced and combined using the official jwst pipeline (v1.11.3)" (Methods)
- **esorex** : Reduction of VLT HAWK-I images  
  > "The images of each filter were reduced and combined using the official pipeline esorex" (Methods)
- **webbpsf** : Inferring the NIRSpec spatial resolution  
  > "The spatial resolution of the data, which is inferred with the webbpsf tool" (Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Maximum rotation velocity v_rot (inclination corrected) | 280 | +32/-31 | km/s | 5 | The maximum rotation velocity (corrected for inclination) $v_\mathrm{rot}$ is $280^{+32}_{-31}$ km/s, i.e. $4.5^{+1.4}_{-1.1}$ times the velocity dispersion $\sigma_\mathrm{int}$ ($61^{+17}_{-13}$ km/s |
| Intrinsic velocity dispersion sigma_int | 61 | +17/-13 | km/s | 4 | The maximum rotation velocity (corrected for inclination) $v_\mathrm{rot}$ is $280^{+32}_{-31}$ km/s, i.e. $4.5^{+1.4}_{-1.1}$ times the velocity dispersion $\sigma_\mathrm{int}$ ($61^{+17}_{-13}$ km/s |
| v_rot / sigma_int | 4.5 | +1.4/-1.1 | dimensionless | 5 | The maximum rotation velocity (corrected for inclination) $v_\mathrm{rot}$ is $280^{+32}_{-31}$ km/s, i.e. $4.5^{+1.4}_{-1.1}$ times the velocity dispersion $\sigma_\mathrm{int}$ ($61^{+17}_{-13}$ km/s |
| Circular velocity v_circ | 304 | +32/-31 | km/s | 5 | The calculated value of $v_\mathrm{circ}$ is $304^{+32}_{-31}\,$km/s. |
| Half-light radius at rest-frame 0.5 micron | 1.27 arcsec (9.6 kpc) | +0.07/-0.16 arcsec (+0.5/-1.2 kpc) | arcsec, kiloparsec | 6 | The final calculated half-light radius is $1.27^{+0.07}_{-0.16}$ arcsec, or equivalently $9.6^{+0.5}_{-1.2}$ kiloparsecs. |
| Stellar mass (non-parametric SFH) | 3.7e11 | +2.6/-2.2 e11 | solar mass | 7 | The inferred stellar mass and SFR are $3.7^{+2.6}_{-2.2} \times 10^{11}\,M_\odot$ and $2.5^{+7.5}_{-2.1} \times 10^2 \,M_\odot/$yr, respectively. |
| Star-formation rate (100 Myr average) | 2.5e2 | +7.5/-2.1 e2 | solar mass per year | 7 | The inferred stellar mass and SFR are $3.7^{+2.6}_{-2.2} \times 10^{11}\,M_\odot$ and $2.5^{+7.5}_{-2.1} \times 10^2 \,M_\odot/$yr, respectively. |
| CO(4-3) line luminosity | 1.3e8 | not stated | solar luminosity | 3 | $1.3\times 10^8$ |
| H2 mass estimated from CO | 1.8e11 | +1.0/-0.8 e11 | solar mass | 3 | $1.8^{+1.0}_{-0.8}\times 10^{11}$ |
| Probability of finding a galaxy this large in random fields | 2% and 0.6% (two size-mass relations) | not stated | percent | 8 | Therefore the corresponding probabilities of finding a galaxy equal to or larger than the Big Wheel in random fields are 2% and 0.6% according to the two studies, respectively. |
| 2-10 keV X-ray luminosity of the AGN | 9.8e43 | +1.8/-1.7 e43 | erg/s | 0 | $L_{2-10\, keV} = 9.8^{+1.8}_{-1.7} \times 10^{43}\,\mathrm{erg\cdot s}^{-1}$ |

## Qualitative findings

- Big Wheel has a red centre and a stellar disk at least 30 kpc in diameter with clumpy spiral-arm features  
  > "The Big Wheel features a red center, visible only in the JWST near-infrared filters (green and red channels), and a stellar disk extending to at least 30 kiloparsecs in diameter." (main text)
- Galaxy sits on the z~0 stellar-mass Tully-Fisher relation yet has an SFR consistent with typical z~3 star-forming galaxies  
  > "it is located on top of the stellar mass Tully-Fisher relation of the $z\sim 0$ disks" (main text)

## Claim tuples

- H: Is the Big Wheel a rotationally supported disk? | E: NIRSpec H-alpha slit kinematics fit with a flat-rotation-curve disk model | R: v_rot = 280 km/s, v_rot/sigma_int = 4.5 | F: Rotating, rotationally supported disk | **supported**
- H: Is the Big Wheel unusually large and massive for a kinematically confirmed disk at z~3? | E: Compare size and mass with literature disks and size-mass relations | R: Offset to high size and mass versus observed and simulated relations | F: Unique giant disk at z~3 | **supported**
- H: Could such a galaxy arise by chance in random fields, or does environment matter? | E: Compute probability from two JWST size-mass relations and survey areas | R: 2% and 0.6% chance in random fields | F: Environment may play a role in setting disk size, but this is not demonstrated | **partially**
- H: Does the molecular gas traced by ALMA CO(4-3) rotate like the ionized gas? | E: First-moment CO map compared with the H-alpha map accounting for the ALMA PSF | R: Smooth velocity gradient along the major axis, narrower velocity span due to beam smearing | F: Cold molecular and warm ionized gas rotate similarly | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gravitational lensing magnification rejected based on no foreground cluster or massive nearby galaxy  
  > "This possibility is rejected based on the non-detection of any foreground cluster according to the X-ray and galaxy redshift measurements available to the field" (Methods)
- How they decided it was enough: _not stated_
- Limitation (authors): CO map has a much larger PSF than the H-alpha map so beam smearing narrows its velocity span  
  > "The CO map has a substantially larger PSF than the H$\alpha$ map and, as a result, shows narrower spans of velocity due to the stronger beam-smearing effect" (Methods)
- Limitation (authors): NIRSpec slits cover only about 20% of the galaxy  
  > "We noticed though that the slits only cover about 20% of the galaxy." (Methods)
- Limitation (authors): H-alpha attenuation may be affected by NIRSpec flux calibration errors  
  > "we caution that it may be subject to NIRSpec flux calibration errors" (Methods)
- Caveat (inferred, ours): ALMA processing is entirely deferred to an earlier paper, so the CO moment map and gas mass cannot be reproduced from this text
- Caveat (inferred, ours): Rotation curve rests on three slits covering ~20% of the galaxy, so the disk-model fit may be sensitive to slit placement
- Caveat (inferred, ours): Possible companion clump and AGN could bias the kinematics and mass
- Caveat (inferred, ours): Probability estimate relies on two literature size-mass relations and a log-normal assumption

## Reproducibility

- Data public (paper): ALMA dataset 2021.1.00793.S obtainable from the ALMA science archive; JWST and HST data public via MAST  
  > "This paper also makes use of the ALMA dataset ADS/JAO.ALMA#2021.1.00793.S. which can be obtained at" (Data availability); "The JWST NIRCam data (Program ID: GO 1835) are publicly available at" (Data availability)
- Products in archive: _not stated_
- Code: Only third-party packages are pointed to (Source Extractor, statmorph, emcee, galpy, prospector, CIGALE, drizzle); no authors' own scripts stated  
  > "The prospector code is available to download at" (Data availability); "The CIGALE code is available at" (Data availability)
- Missing: ALMA observing setup, calibration, tclean settings and line-free channels (deferred to a cited earlier paper)
- Missing: CO(4-3) luminosity and alpha_CO/excitation assumptions behind the H2 mass
- Missing: MCMC priors, walker settings and likelihood for the disk fit
- Missing: Prospector prior and dust-law details (references unresolved in the text)
- Missing: Exact NIRSpec slit extraction and the velocity-map construction from the three slits
- Data volume (inferred): ALMA: one Cycle 8 project, likely tens of GB raw; plus several GB of JWST NIRCam/NIRSpec and HST ACS products from MAST
- Score (inferred): 2/5, JWST, HST and ALMA data are public and the JWST kinematic and SED methods are fairly described with numeric results, but the ALMA part is minor and delegated to an earlier paper, and fit priors and settings are missing.
- Rediscovery candidate: no, ALMA plays a minor role and its processing recipe is not given in this paper; the main results rely on JWST data and unstated priors.

## Links

- Method: (cite: Pensabene2024) (Holds the ALMA observation details and CO-to-H2 conversion factors)
- Method: (cite: Rodriguez-Gomez2019) (statmorph morphology method)
- Method: (cite: Leja2017); (cite: Johnson2021); (cite: Wang2024) (Prospector SED fitting and non-parametric SFH prior)
- Method: (cite: Ubler2017) (Relation to convert v_rot and sigma_int into v_circ)
- Companion: (cite: Pensabene2024) (ALMA study of the quasar field overdensity containing the Big Wheel)
- Related: JWST GO 1835 (PI: Cantalupo)
- Related: HST GO 17065 (PI: Cantalupo)
- Related: ESO programme 110.23ZX (VLT HAWK-I)
- Related: Chandra ACIS program (PI: Cantalupo)

## Checks

```json
{
 "quotes": 105,
 "quotes_ok": 105,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 109,
  "stated": 68,
  "rate": 0.624
 },
 "evidence_ok": true
}
```
