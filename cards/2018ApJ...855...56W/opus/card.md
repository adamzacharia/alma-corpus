# Resolved Millimeter Observations of the HR 8799 Debris Disk

`2018ApJ...855...56W` | The Astrophysical Journal 2018 | first author: Wilner, David J. | arXiv: 1803.00054 | DOI: 10.3847/1538-4357/aaacd7

Card schema 1.0 | model claude-opus-5-5 | depth full | type archival_reuse

## Science

- Fields: debris_disks, exoplanets
- Question: Determine the structure (inner/outer edge, width, inclination, PA) of the cold planetesimal belt of HR 8799 from combined SMA+ALMA 1.3 mm visibilities, use the inner edge to constrain the mass of planet b, and use the 1.3-9 mm spectral index to constrain the grain size distribution.  
  > "To better determine the properties of the cold belt of planetesimals in the HR 8799 system, we used the SMA to obtain new observations at 1.3 millimeters wavelength that are sensitive to larger angular scales" (Introduction); "We also obtained new observations at 9 millimeters wavelength with the Karl G. Jansky Very Large Array (VLA), to constrain the spectral index of the disk emission." (Introduction)
- Target **HR 8799**: coordinates phase center 23h07m28.72 +21d08m03.3s (J2000) (SMA and VLA)  
  > "i.e. the J2000 star position uncorrected for interim proper motion" (Submillimeter Array); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00482.S
- bands: Band 6 (1.3 mm)  
  > "We retrieved observations of HR 8799 from the ALMA archive that were made in Band 6 in 2015 January." (Atacama Large Millimeter/submillimeter Array)
- frequencies and spectral setup: four spectral windows, 2 GHz wide, 16 MHz channels, centered at 216, 218, 231, 233 GHz  
  > "the correlator setup consisted of four spectral windows with width 2 GHz and channel spacing 16 MHz, centered at 216, 218, 231 and 233 GHz, respectively." (Atacama Large Millimeter/submillimeter Array)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-meter array  
  > "The primary beam FWHM size of the 12-meter diameter array antennas" (Atacama Large Millimeter/submillimeter Array)
- configurations: _not stated_
- baselines: 15 to 349 m  
  > "The observations included baseline lengths from 15 to 349 meters." (Atacama Large Millimeter/submillimeter Array)
- angular resolution: ~1.5'' (ALMA natural-weighted image); ~3.8'' combined SMA+ALMA  
  > "The ALMA image is comparable to Figure 1 of (cite: booth16), with a beam size of" (Continuum Emission); "the two peaks visible on either side of the star are the signatures of limb brightening along the major axis of an inclined and optically thin emission belt." (Continuum Emission)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2015 January, five scheduling block executions (best weather on 2015 January 03)  
  > "We calibrated the five individual scheduling block executions using the associated `CASA` 4.3.1 reduction scripts." (Atacama Large Millimeter/submillimeter Array); "the execution on 2015 January 03 obtained in the best weather conditions dominates the sensitivity budget." (Atacama Large Millimeter/submillimeter Array)
- pi or archival as stated: archival ALMA data (details in Booth et al. 2016); new SMA and VLA data  
  > "Details of these observations are described in (cite: booth16)." (Atacama Large Millimeter/submillimeter Array)
- Line: 12CO J=2-1 (230.53800 GHz)
- Line: 13CO J=2-1 (220.39868 GHz)
- Other facility **Submillimeter Array (SMA)**: New 1.3 mm subcompact-configuration observations (6 tracks, 2016 Aug-Sep, baselines 6-69 m, SWARM correlator, 16 GHz continuum), providing short spacings; also 12CO/13CO 2-1  
  > "at a wavelength near 1.3 millimeters in the subcompact configuration that provides projected baselines as short as 6 meters." (Submillimeter Array); "This setup provided a total of 16 GHz of continuum bandwidth" (Submillimeter Array)
- Other facility **Karl G. Jansky Very Large Array (VLA)**: New 9 mm D-configuration continuum observations (4 dates in 2017, 8 GHz bandwidth at 30-36 GHz) for the spectral index  
  > "We observed the HR 8799 system with the VLA at 9 mm wavelength in the most compact D configuration." (Very Large Array); "The correlator was used to obtain the maximum continuum bandwidth of 8 GHz, comprised of 4 bands centered at 30, 32, 34, and 36 GHz, for two polarizations." (Very Large Array)
- External data: Location of a compact background source to the northwest of the disk, included as a point source in the model  
  > "shows the presence of a compact background source to the northwest of the disk, we also include an unresolved point source at this location in the model" (SMA/ALMA Disk Model Fits) [from Herschel (cite: matthews14) and JCMT (cite: holland17)]
- External data: Submillimeter-predicted 1.3 mm flux ~3.5 mJy (assuming spectral index 2.5) used for Gaussian flux prior in ALMA-only fit  
  > "motivated by submillimeter observations (cite: matthews14) that predict a flux density of" (SMA/ALMA Disk Model Fits) [from (cite: matthews14); spectral index typical of debris disks (cite: macgregor16)]
- External data: Planet b semi-major axis a_pl = 68 AU and stellar mass M* = 1.56 Msun  
  > "For this calculation, we adopt the planet semi-major axis" (Dynamical Constraints on the Mass of Planet b) [from dynamical analysis (cite: soummer11), consistent with (cite: gray99)]
- External data: Small-grain dust opacity index beta_s = 1.8±0.2 for interstellar grain materials  
  > "is the dust opacity power law index in the small grain limit" (Grain Size Distribution) [from (cite: draine06)]
- External data: Planet orbital inclination (38±7 deg for b) and ascending node range 40-70 deg used for coplanarity comparison  
  > "The (cite: konopacky16) astrometric analysis indicates $\Omega$ lies in the range of 40 to" (System Geometry) [from (cite: konopacky16)]

## Processing

### Calibration

- pipeline or manual: ALMA: calibrated with the associated CASA reduction scripts; SMA: standard procedures in MIR; VLA: VLA pipeline  
  > "We calibrated the five individual scheduling block executions using the associated `CASA` 4.3.1 reduction scripts." (Atacama Large Millimeter/submillimeter Array); "All of the basic calibration was performed using standard procedures in the MIR software package." (Submillimeter Array)
- casa version: CASA 4.3.1 (ALMA calibration); CASA 4.7.2 (imaging, VLA pipeline)  
  > "Imaging was carried out with the `clean` task in `CASA` (version 4.7.2)." (Atacama Large Millimeter/submillimeter Array)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: SMA: Uranus; VLA: 3C48 (ALMA not stated)  
  > "The absolute flux scale was set using observations of Uranus obtained in each track, with 10% overall accuracy." (Submillimeter Array)
- flux scale uncertainty: 10% (SMA and VLA; ALMA not stated)  
  > "The absolute flux scale was set using observations of Uranus obtained in each track, with 10% overall accuracy." (Submillimeter Array)
- self calibration: _not stated_

### Imaging

- task: clean in CASA 4.7.2  
  > "Imaging was carried out with the `clean` task in `CASA` (version 4.7.2)." (Atacama Large Millimeter/submillimeter Array)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "These images were obtained with natural weighting" (Continuum Emission)
- uv taper: 4'' FWHM Gaussian taper for images including SMA data; 5'' for VLA  
  > "those including SMA data use a $4\ensuremath{''}$ FWHM Gaussian taper to improve surface brightness sensitivity" (Continuum Emission)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: channels with CO line emission flagged before continuum output (exact channels not given)  
  > "Continuum visibilities were output for analysis after flagging the channels with CO line emission, averaging in time to 30 seconds, and averaging in frequency to 2 GHz bandwidth." (Atacama Large Millimeter/submillimeter Array)
- primary beam correction: _not stated_
- array combination: SMA and ALMA visibilities imaged together and fit jointly; proper motion (0.20'') between epochs ignored  
  > "The combination of SMA and ALMA data results in an even better image of this circumstellar structure." (Continuum Emission); "was ignored, given its insignificance at the low angular resolution of the SMA observations." (SMA/ALMA Disk Model Fits)
- smoothing: _not stated_
- final beam: ~1.5'' (ALMA); ~3.8'' (SMA+ALMA); 6.2''x5.8'' (VLA)  
  > "The ALMA image is comparable to Figure 1 of (cite: booth16), with a beam size of" (Continuum Emission)
- final rms: VLA 4.3 uJy/beam (ALMA rms not stated)  
  > "and rms noise of 4.3 $\mu$Jy/beam." (Continuum Emission)

### Inherited from earlier work

- ALMA observation details  
  > "Details of these observations are described in (cite: booth16)." (Atacama Large Millimeter/submillimeter Array) [from (cite: booth16)]
- Visibility fitting procedure for the belt model  
  > "we model the observations using the visibility fitting procedure described in (cite: macgregor13)." (SMA/ALMA Disk Model Fits) [from (cite: macgregor13)]
- Inner edge vs chaotic zone formula R_in = a_pl + 5 a_pl (M_pl/3M*)^(1/3) (zero eccentricity)  
  > "If we adopt the (cite: pearce14) formula, then we can translate the radial location of the inner edge of the millimeter belt" (Dynamical Constraints on the Mass of Planet b) [from (cite: pearce14)]

### Not stated but needed to reproduce (our reading)

- ALMA flux calibrator and flux scale uncertainty, and whether it was included in the fit
- Whether self-calibration was applied to any dataset
- Exact CO channels flagged in ALMA spws
- Pixel size / grid of model images and clean parameters (cell, imsize, threshold, niter)
- Exact primary beam models used for SMA and ALMA in the model
- Relative weighting between SMA and ALMA after statwt (any reweighting)
- Distance adopted to convert arcsec to AU
- Prior ranges on i, PA and point-source offsets/flux; burn-in length
- Source of the 39.7 K dust temperature and how alpha_Pl = 1.92 was computed
- Whether flux calibration uncertainty enters the spectral index error
- Aperture diameter in arcsec used for the VLA flux

## Analysis recipe

1. **calibrate archival ALMA data and prepare continuum visibilities**: Run CASA 4.3.1 reduction scripts on five SBs, homogenize weights with statwt, flag CO channels, average to 30 s and 2 GHz  
  > "We used the `CASA` task `statwt` to homogenize the visibility weights among scheduling blocks" (Atacama Large Millimeter/submillimeter Array); "Continuum visibilities were output for analysis after flagging the channels with CO line emission, averaging in time to 30 seconds, and averaging in frequency to 2 GHz bandwidth." (Atacama Large Millimeter/submillimeter Array)
   - software: CASA, statwt
   - parameter: 30 s time averaging, 2 GHz frequency averaging  
  > "averaging in time to 30 seconds, and averaging in frequency to 2 GHz bandwidth." (Atacama Large Millimeter/submillimeter Array)
   - fitting: _not stated_
   - validation: _not stated_
2. **image continuum and compute deprojected visibility profile**: Natural-weighted clean images (4'' taper for SMA-including images); real/imaginary visibilities averaged in annular bins using the fitted belt geometry  
  > "obtained by averaging the real and imaginary parts of of the complex visibilities in concentric annular bins, adopting the belt geometry derived in" (Continuum Emission)
   - software: CASA, clean
   - parameter: natural weighting, 4'' FWHM Gaussian taper  
  > "These images were obtained with natural weighting" (Continuum Emission)
   - fitting: _not stated_
   - validation: SMA and ALMA visibilities consistent in overlap; imaginary parts consistent with zero  
  > "The visibilities from the two telescopes are consistent where they overlap at higher spatial frequencies that sample the small scale structure." (Continuum Emission)
3. **fit parametric belt model to visibilities**: Axisymmetric geometrically thin belt with power-law surface brightness I ∝ r^x between R_in and R_out, plus inclination, PA and background point source; model times primary beam, sampled with vissample; MCMC with emcee; SMA, ALMA, and joint fits  
  > "we make the simple assumption that the structure can be represented by an axisymmetric and geometrically thin belt" (SMA/ALMA Disk Model Fits); "For comparison with observed visibilities, the model emission is multiplied by the appropriate primary beam response of each telescope." (SMA/ALMA Disk Model Fits)
   - software: vissample, emcee
   - parameter: 100 walkers x 5,000 steps (50,000 iterations)  
  > "We explore the posterior with 50,000 iterations ($100$ walkers and $5,000$ steps each)" (SMA/ALMA Disk Model Fits)
   - parameter: background point source omitted in ALMA-only fit  
  > "When modeling the ALMA data alone, this additional background source is omitted on account of primary beam attenuation at the offset location." (SMA/ALMA Disk Model Fits)
   - assumption: axisymmetric, geometrically thin belt; proper motion between epochs ignored  
  > "we make the simple assumption that the structure can be represented by an axisymmetric and geometrically thin belt" (SMA/ALMA Disk Model Fits)
   - fitting: chi^2 likelihood lnL = -chi^2/2 with visibility weights; uniform priors (0<R_in<R_out, F_belt>0, -3<x<3); ALMA-only adds Gaussian flux prior 3.0-4.0 mJy and logistic R_out prior (k=-10, x0=512 AU); 68% marginalized uncertainties  
  > "For modeling the SMA observations alone, we adopt uniform priors for all parameters, in particular" (SMA/ALMA Disk Model Fits); "In addition, we implemented a logistic function" (SMA/ALMA Disk Model Fits); "together with their 68% uncertainties determined from the marginalized posterior probability distributions." (SMA/ALMA Disk Model Fits)
   - validation: Gelman-Rubin R-hat < 1.1; noise-like residual image after subtracting best-fit model  
  > "check that the Gelman-Rubin statistic (cite: gelman14) is" (SMA/ALMA Disk Model Fits); "The goodness-of-fit is demonstrated by the noise-like residual image." (SMA/ALMA Disk Model Fits)
4. **measure VLA 9 mm flux**: Circular aperture flux in CASA centered on disk with diameter from SMA+ALMA model; uncertainty from same aperture at ten random locations  
  > "we measure the flux density in `CASA` within a circular aperture centered at the location of the disk, assuming the diameter of the disk determined from the combined modeling of the SMA and ALMA data." (VLA 9 millimeter Flux Estimate); "We determine the uncertainty by measuring the flux density in the same circular aperture at ten random locations in the image and taking the average." (VLA 9 millimeter Flux Estimate)
   - software: CASA
   - assumption: primary beam correction negligible  
  > "(correction for primary beam attenuation is negligible)" (VLA 9 millimeter Flux Estimate)
   - fitting: _not stated_
   - validation: _not stated_
5. **convert inner edge into planet b mass**: Translate R_in posterior through Pearce & Wyatt (2014) chaotic-zone formula assuming planet b truncates the belt  
  > "shows the result of this translation of the inner radius posterior distribution from our modeling, assuming planet b truncates the belt." (Dynamical Constraints on the Mass of Planet b)
   - parameter: a_pl = 68 AU, M* = 1.56 Msun  
  > "For this calculation, we adopt the planet semi-major axis" (Dynamical Constraints on the Mass of Planet b)
   - assumption: zero eccentricity limit; chaotic zone of planet b truncates planetesimals  
  > "taken in the limit of zero eccentricity." (Dynamical Constraints on the Mass of Planet b)
   - fitting: _not stated_
   - validation: _not stated_
6. **infer surface density profile**: Convert brightness index x to surface density index assuming T ∝ r^-0.5  
  > "to approximate radiative equilibrium with stellar heating, then this implies a surface density profile" (Stirring Mechanisms)
   - assumption: T(r) ∝ r^-0.5  
  > "If we assume a radial temperature profile" (Stirring Mechanisms)
   - fitting: _not stated_
   - validation: _not stated_
7. **derive mm spectral index and grain size index**: alpha_mm from combined 1.3 mm model flux and VLA 9 mm flux; q = (alpha_mm - alpha_Pl)/beta_s + 3  
  > "we use the best-fit total flux density from the combined SMA and ALMA models at 1.3 millimeters and the VLA flux density measured at 9 millimeters to obtain a millimeter spectral index" (Grain Size Distribution)
   - assumption: beta_s = 1.8±0.2 (interstellar grains); alpha_Pl = 1.92±0.10 from 39.7 K dust temperature; valid for 3<q<4  
  > "(the Rayleigh-Jeans limit modified by a small correction factor from the 39.7 K dust temperature assumed for HR 8799)" (Grain Size Distribution)
   - fitting: _not stated_
   - validation: compared with weighted mean q = 3.36±0.02 for 15 debris disks  
  > "for a sample of 15 debris disks observed over a similar wavelength range." (Grain Size Distribution)

## Software

- **CASA** 4.3.1 (ALMA calibration scripts); 4.7.2 (imaging, VLA pipeline): ALMA calibration, imaging with clean, statwt, VLA pipeline, aperture photometry  
  > "Fourier inversion for continuum and spectral line imaging and `clean` deconvolution were done in the `CASA` software package (version 4.7.2)." (Submillimeter Array)
- **MIR** : SMA basic calibration  
  > "All of the basic calibration was performed using standard procedures in the MIR software package." (Submillimeter Array)
- **VLA pipeline** : VLA basic calibration  
  > "The basic calibration was done using VLA pipeline processing in the `CASA` package (version 4.7.2)" (Very Large Array)
- **vissample** : computing synthetic model visibilities  
  > "a python package for visibility sampling that improves on the sampling and interpolation of the `uvmodel` task in the Miriad software package" (SMA/ALMA Disk Model Fits)
- **emcee** : MCMC posterior sampling  
  > "We make use of the `emcee` package (cite: foreman13) to sample the posterior probability distribution" (SMA/ALMA Disk Model Fits)
- **Miriad** : mentioned as the uvmodel task that vissample improves on (not used directly)  
  > "improves on the sampling and interpolation of the `uvmodel` task in the Miriad software package" (SMA/ALMA Disk Model Fits)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Belt inner edge R_in (SMA+ALMA) | 104 | +8/-12 | AU | 3 | Belt inner edge [AU]; The models constrain the radial location of the inner edge of the belt to |
| Belt outer edge R_out (SMA+ALMA) | 361 | +16/-18 | AU | 3 | Belt outer edge [AU] |
| Total belt flux density F_belt (SMA+ALMA, 1.3 mm) | 3.44 | +0.31/-0.56 | mJy | 3 | Total belt flux density [mJy] |
| Surface brightness power-law index x (SMA+ALMA) | -0.38 | ±0.47 | dimensionless | 3 | the best-fit power law index for the millimeter emission radial profile is |
| Disk inclination (SMA+ALMA) | 32.8 | +5.6/-9.6 | deg | 3 | Model fits to the combined SMA and ALMA visibilities constrain the millimeter belt inclination |
| Disk position angle (SMA+ALMA) | 35.6 | +9.4/-10.1 | deg | 3 | determined from the joint analysis of the SMA and ALMA data is compatible with the low end of this range. |
| Background point source flux (SMA+ALMA) | 0.45 | +0.12/-0.15 | mJy | 3 | background source flux density [mJy] |
| Belt flux from SMA alone | 5.13 | +0.34/-1.01 | mJy | 3 | We note that the fit to the SMA data alone yields a higher flux density of |
| R_in from ALMA alone (strong priors) | 115 | +16/-17 | AU | 3 | Adopting strong priors on the total belt flux density and belt outer edge parameters |
| VLA 9 mm disk flux density | 32.6 | ±9.9 | uJy | 4 | The measured total flux density of the disk from our VLA observations is |
| Planet b mass | 5.8 | +7.9/-3.1 | M_Jup | 5 | this inner edge location translates into a constraint on the planet b mass of |
| Surface density power-law index | 0.12 | ±0.47 | dimensionless | 6 | then this implies a surface density profile |
| Millimeter spectral index alpha_mm | 2.41 | ±0.17 | dimensionless | 7 | Flux density measurements at 1.3 and 9 millimeters from the SMA and VLA, respectively, give a spectral index of |
| Grain size distribution index q | 3.27 | ±0.10 | dimensionless | 7 | the resulting grain size distribution power-law index is |
| VLA image rms | 4.3 | not stated | uJy/beam | 0 | and rms noise of 4.3 $\mu$Jy/beam. |

## Qualitative findings

- ALMA alone cannot constrain R_out or total flux; requires strong priors, whereas SMA+ALMA joint fit does not  
  > "When modeling the ALMA observations alone, informative constraints were not obtained for the outer radius or total flux parameters using these assumptions." (SMA/ALMA Disk Model Fits); "By contrast, modeling the SMA and ALMA observations simultaneously does not require strong priors on the disk parameters to obtain meaningful constraints." (SMA/ALMA Disk Model Fits)
- No significant azimuthal asymmetries or stellar offset in residuals  
  > "Notably, the imaged residuals reveal no significant azimuthal brightness asymmetries" (SMA/ALMA Disk Model Fits)
- CO emission detected by SMA appears associated with extended molecular cloud rather than the disk; no rotation signature  
  > "there is no clear evidence for any systematic motions that might be associated with rotation of gas in the debris disk." (Line Emission)
- No need for an additional unseen planet beyond b  
  > "Given this result, there is no need to posit the presence of an additional unseen planet orbiting beyond planet b" (Dynamical Constraints on the Mass of Planet b)

## Claim tuples

- H: The HR 8799 cold belt is a broad axisymmetric belt | E: Joint MCMC visibility fit of SMA+ALMA 1.3 mm data with power-law belt model | R: R_in ≈104 AU, R_out ≈361 AU, noise-like residuals | F: Broad (ΔR/R ≳ 1), axisymmetric inclined belt, no clumps | **supported**
- H: The belt is coplanar with the planet orbits | E: Compare fitted i and PA with astrometric orbital elements | R: i = 32.8 (+5.6/-9.6) deg, PA = 35.6 (+9.4/-10.1) deg | F: Consistent with coplanarity within large mutual uncertainties | **partially**
- H: Planet b truncates the inner edge of the belt | E: Translate R_in posterior via Pearce & Wyatt chaotic zone formula | R: M_pl = 5.8 (+7.9/-3.1) M_Jup | F: Consistent with hot-start luminosity-based masses; no extra planet needed | **supported**
- H: The grain size distribution follows a classical collisional cascade | E: 1.3-9 mm spectral index from SMA+ALMA model flux and VLA flux | R: alpha_mm = 2.41±0.17, q = 3.27±0.10 | F: Close to steady-state collisional cascade | **supported**
- H: The disk is planet-stirred rather than self-stirred | E: Infer surface density gradient from brightness index | R: Σ ∝ r^(0.12±0.47) | F: Shallow profile not predicted by self-stirring; favors planet-stirring | **partially**

## Reasoning

- Why this data: ALMA filtered out extended emission; SMA subcompact short baselines recover large scales; VLA for spectral index  
  > "The shorter baselines from the SMA capture the steep rise in visibility amplitude at low spatial frequencies that are missed by ALMA" (Continuum Emission)
- Why this method: Visibility-domain fitting preferred over image-based fitting of ALMA dirty images, whose uncertainties are suspected underestimated; aperture photometry for VLA due to low S/N  
  > "We suspect that the $\sim10\%$ uncertainties on the disk parameters quoted by (cite: booth16) from an image-based analysis of the ALMA observations are underestimated" (SMA/ALMA Disk Model Fits); "In the VLA image, the disk is detected only at the $\sim3\sigma$ per beam level, and we do not apply the same MCMC modeling technique to these data." (VLA 9 millimeter Flux Estimate)
- Alternative: Visibility fitting of VLA data rejected in favor of aperture photometry  
  > "We adopt this image-based approach instead of fitting to the millimeter visibilities due to the difficulty in selecting a function that adequately reproduces the complex structure of the observed surface brightness profile." (VLA 9 millimeter Flux Estimate)
- Alternative: Imaging CO line emission attempted with various weightings but artifacts persisted  
  > "Regardless of the choice of visibility weighting scheme and `clean` deconvolution parameters, all of our attempts at imaging the line emission show pronounced artifacts." (Line Emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Insufficient sensitivity for planet-disk interaction details or discriminating mass constraints  
  > "However, these observations still lack the sensitivity needed to reveal any details of planet-disk interactions" (Conclusions)
- Limitation (authors): Tension with Herschel inclination and PA  
  > "There is some tension between the millimeter result and the lower (and more precise) disk inclination of" (System Geometry)
- Limitation (authors): Extended CO structure poorly sampled by interferometers  
  > "remains poorly sampled and highly problematic to reconstruct, even with the lower spatial frequency information newly obtained with the SMA." (Line Emission)
- Caveat (inferred, ours): Flux calibration uncertainties (10%) not obviously propagated into alpha_mm and q
- Caveat (inferred, ours): Relative flux scale between SMA and ALMA not cross-checked or fitted as a free parameter
- Caveat (inferred, ours): VLA flux is a ~3σ detection; aperture size choice drives result
- Caveat (inferred, ours): Planet mass depends on zero-eccentricity Pearce formula and fixed a_pl/M*; systematic model uncertainty not included
- Caveat (inferred, ours): Geometrically thin, sharp-edged power-law model may bias R_in

## Reproducibility

- Data public (paper): ALMA data retrieved from archive (2012.1.00482.S); SMA/VLA availability not stated  
  > "We retrieved observations of HR 8799 from the ALMA archive that were made in Band 6 in 2015 January." (Atacama Large Millimeter/submillimeter Array)
- Products in archive: _not stated_
- Code: vissample is publicly available (third-party tool); fitting code not released  
  > "`vissample` is publicly available at <https://github.com/AstroChem/vis_sample>" (SMA/ALMA Disk Model Fits)
- Missing: SMA raw data access and MIR calibration details
- Missing: Model image pixel grid and primary-beam models used
- Missing: Priors on geometric and point-source parameters; burn-in
- Missing: Distance used for AU conversion
- Missing: VLA aperture diameter in arcsec
- Missing: Origin of 39.7 K temperature
- Data volume (inferred): ALMA: five Band 6 SBs, ~tens of GB raw; averaged continuum visibilities small (MB-scale). SMA/VLA a few tens of GB.
- Score (inferred): 3/5, ALMA archival data and model are clearly described, but full reproduction needs new SMA data (not stated public), and several fit/prior details are missing.
- Rediscovery candidate: no, Main joint-fit results depend on SMA data whose public availability is not stated; ALMA-only fit requires strong priors and is not the key result.

## Links

- Method: (cite: macgregor13) (visibility fitting procedure for belt model)
- Method: (cite: foreman13) (emcee MCMC sampler)
- Method: (cite: gelman14) (Gelman-Rubin convergence statistic)
- Method: (cite: pearce14) (inner edge vs planet mass formula)
- Method: (cite: draine06) (dust opacity index for q derivation)
- Companion: (cite: booth16) (original analysis of the same ALMA data)
- Companion: (cite: hughes11) (previous SMA 870 um detection of the disk)

## Checks

```json
{
 "quotes": 111,
 "quotes_ok": 111,
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
  "facts": 100,
  "stated": 70,
  "rate": 0.7
 },
 "evidence_ok": true
}
```
