# Molecular gas and dust properties in z &gt; 7 quasar hosts

`2025A&A...695A..23S` | Astronomy and Astrophysics 2025 | first author: Salvestrini, Francesco | arXiv: 2412.02688 | DOI: 10.1051/0004-6361/202453226

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Measure CO(6-5)/(7-6) and dust continuum in the five z>7 quasars observed with NOEMA, add archival ALMA band 6 continuum, model the FIR SED to get dust mass and SFR, derive molecular gas mass limits and a new [CII]-based M_H2 calibration, and study gas-to-dust ratio, depletion time and SFE.  
  > "we present new observations targeting CO(6-5) and (7-6) emission lines and the underlying continuum in five quasars" (Introduction); "Based on these measurements, we studied the growth of host galaxies and the implications for their coevolution with SMBHs in the reionization era." (Introduction)
- Target **J0313-1806**: coordinates 03:13:43.84, -18:06:36.40 (J2000)  
  > "03:13:43.84, $-$18:06:36.40" (Table 1); "7.6423" (Table 1); z/distance z_[CII] = 7.6423  
  > "03:13:43.84, $-$18:06:36.40" (Table 1); "7.6423" (Table 1); distance from z_[CII] column of Table 1  
  > "03:13:43.84, $-$18:06:36.40" (Table 1); "7.6423" (Table 1)
- Target **J1243+0100**: coordinates 12:43:53.93, +01:00:38.50 (J2000)  
  > "12:43:53.93, +01:00:38.50" (Table 1); "7.0749" (Table 1); z/distance z_[CII] = 7.0749  
  > "12:43:53.93, +01:00:38.50" (Table 1); "7.0749" (Table 1); distance from z_[CII] column of Table 1  
  > "12:43:53.93, +01:00:38.50" (Table 1); "7.0749" (Table 1)
- Target **J0038-1527**: coordinates 00:38:36.10, -15:27:23.60 (J2000)  
  > "00:38:36.10, $-$15:27:23.60" (Table 1); "7.034" (Table 1); z/distance z_[CII] = 7.034  
  > "00:38:36.10, $-$15:27:23.60" (Table 1); "7.034" (Table 1); distance from z_[CII] column of Table 1  
  > "00:38:36.10, $-$15:27:23.60" (Table 1); "7.034" (Table 1)
- Target **J2356+0017**: coordinates 23:56:46.33, +00:17:47.30 (J2000)  
  > "23:56:46.33, +00:17:47.30" (Table 1); "7.01" (Table 1); z/distance z_[CII] = 7.01  
  > "23:56:46.33, +00:17:47.30" (Table 1); "7.01" (Table 1); distance from z_[CII] column of Table 1  
  > "23:56:46.33, +00:17:47.30" (Table 1); "7.01" (Table 1)
- Target **J0252-0503**: coordinates 02:52:16.64, -05:03:31.80 (J2000)  
  > "02:52:16.64, $-$05:03:31.80" (Table 1); "7.0006" (Table 1); z/distance z_[CII] = 7.0006  
  > "02:52:16.64, $-$05:03:31.80" (Table 1); "7.0006" (Table 1); distance from z_[CII] column of Table 1  
  > "02:52:16.64, $-$05:03:31.80" (Table 1); "7.0006" (Table 1)

## Data provenance

- ALMA projects: 2018.1.01188.S, 2019.A.00017.S, 2019.1.00074.S, 2019.1.01025.S, 2021.1.00934.S, 2021.1.01262.S, 2023.1.00443.S
- bands: ALMA Band 6 (B6) continuum, sky frequencies ~220-240 GHz (archival); NOEMA 3 mm LSB/USB (new)  
  > "which cover sky frequencies $\sim220-240$ GHz" (2 Sample and observations); "ALMA band 6 (B6) fluxes are the integrated emission of best-fit 2D Gaussian function model of the cleaned continuum map." (Table 1 notes)
- frequencies and spectral setup: NOEMA: receivers tuned to CO(6-5) in LSB and CO(7-6) in USB plus continuum; ALMA: archival data covering [CII] and underlying continuum; cubes binned to 20 MHz (~60 km/s)  
  > "receivers were tuned to detect the CO(6–5) and CO(7–6) and the underlying continuum in the lower and upper side band (LSB and USB), respectively." (2 Sample and observations); "Continuum-subtracted cubes were binned to spectral resolutions of 20 MHz" (2 Sample and observations)
- continuum bandwidth: _not stated_
- arrays: NOEMA (new observations); ALMA (archival)  
  > "obtained with the Northern Extended Millimeter Array (NOEMA)" (Introduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Synthesized beams of the continuum maps listed per target in Table 1  
  > "The synthesized beams, root-mean-square (rms) noise levels, and representative frequencies of the continuum maps are reported in Table" (2 Sample and observations)
- max recoverable scale: _not stated_
- sensitivity: Continuum rms per target in Table 1; NOEMA rms estimated using a 20 MHz channel width; J0313 did not reach requested sensitivity (bad weather) and J0038 was limited by shadowing  
  > "R.m.s. is estimated using a channel width of 20 MHz." (Table 1 notes); "The observation targeting quasar J0313 was executed in bad weather conditions, so it did not reach the requested sensitivity to detect either continuum emission or CO lines in both LSB and USB." (2 Sample and observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA data archival (calibrated visibilities retrieved from the science archive); NOEMA data new, project S23CX  
  > "were retrieved from the science archive (see the acknowledgements for the list of ALMA project IDs)" (2 Sample and observations); "The five quasars for which we acquired new NOEMA observations under project S23CX" (2 Sample and observations)
- Line: CO J=6-5 (NOEMA, LSB) (not stated)
- Line: CO J=7-6 (NOEMA, USB) (not stated)
- Line: C+ ([CII]) 158 micron line (covered by archival ALMA data; continuum used here) (not stated)
- Other facility **NOEMA**: New CO(6-5)/(7-6) and 3 mm continuum observations of the five quasars (project S23CX)  
  > "The five quasars for which we acquired new NOEMA observations under project S23CX" (2 Sample and observations)
- External data: Dust temperature T_d = 55 K fixed, from mean of 10 z>6 quasars  
  > "we adopted a fixed temperature, $T_d=55$ K, for all five quasars based on the mean dust temperature in a sample of 10 $z>6$ quasars (cite: Tripodi24b)" (3.1 Dust properties and star formation rates) [from (cite: Tripodi24b)]
- External data: Local emissivity index beta = 1.6 fixed for three quasars  
  > "we fixed $\beta=1.6$, the local value ((cite: Beelen06) and (cite: Witstok23))" (3.1 Dust properties and star formation rates) [from (cite: Beelen06); (cite: Witstok23)]
- External data: CO SLED correction r_6,1 = 0.92 and r_7,1 = 0.65  
  > "We adopted the CO spectral line energy distribution (SLED) correction from (cite: Kaasinen24), that is, $r_{6,1}=0.92$ for CO(6-5) and $r_{7,1}=0.65$." (3.2 Molecular gas mass) [from (cite: Kaasinen24)]
- External data: M_BH and L_bol of z>7 quasars  
  > "We refer to Table 1 in (cite: Fan23) for the references for $M_{BH}$ and $L_{bol}$ for all $z>7$ quasars." (Table 2 notes) [from (cite: Fan23)]
- External data: Properties of 21 z>~6 comparison quasars, with CO and FIR SED-derived quantities, collected from the literature  
  > "the information collected from the literature for 21 quasars at redshift" (Comparison sample of high-z quasars) [from References [1-18] listed in the comparison table (not resolved in the paper text)]
- External data: Stellar masses and upper limit for four EoR quasars  
  > "We took the estimate and upper limit of the stellar mass from (cite: Yue24) for four quasars at the EoR" (4.2 Gas depletion and star formation efficiency) [from (cite: Yue24)]
- External data: M_H2 and IR measurements of J1120, J1007 and J1342  
  > "References for $M_{H2}$, \[CII\], and IR measurements are (1) This work; (2) (cite: Venemans17a); (3) (cite: Feruglio23); (4) (cite: Yang20); (5) (cite: Novak19)" (Table 2 notes) [from (cite: Venemans17a); (cite: Feruglio23); (cite: Yang20); (cite: Novak19)]
- Simulation/model as data: GAEA semi-analytic model coupled to the P-Millennium simulation, 42 predicted AGN with L_bol > 3e46 erg/s at z>6, used for comparison  
  > "To further investigate this scenario, we contrasted our findings against theoretical predictions from the GAlaxy Evolution and Assembly (GAEA) model." (4.2 Gas depletion and star formation efficiency); "resulting in a sample of 42 individual sources" (4.2 Gas depletion and star formation efficiency)

## Processing

### Calibration

- pipeline or manual: NOEMA: CLIC pipeline of GILDAS; ALMA: archive-calibrated visibilities  
  > "We calibrated the visibilities using the CLIC pipeline of the GILDAS software" (2 Sample and observations); "were retrieved from the science archive (see the acknowledgements for the list of ALMA project IDs)" (2 Sample and observations)
- casa version: CASA 6.5.5-21 (imaging)  
  > "The imaging was performed through the Common Astronomy Software Applications (CASA; (cite: McMullin07)), version 6.5.5-21." (2 Sample and observations)
- pipeline version: _not stated_
- archive products used as is: ALMA-calibrated visibilities retrieved from the science archive  
  > "were retrieved from the science archive (see the acknowledgements for the list of ALMA project IDs)" (2 Sample and observations)
- flux calibrator: _not stated_
- flux scale uncertainty: NOEMA calibration error <~10%; 10% calibration uncertainty added in quadrature in SED fit  
  > "The associated error accounts for both the statistical uncertainty of the fit and the calibration error ($\lesssim10\%$" (3.1 Dust properties and star formation rates); "we added in quadrature a 10% calibration uncertainty to the continuum flux errors" (3.1 Dust properties and star formation rates)
- self calibration: _not stated_

### Imaging

- task: tclean (CASA) for ALMA; MAPPING (GILDAS) for NOEMA  
  > "procedures using natural weighting, a 3$\sigma$ cleaning threshold, and a channel width of 20 MHz" (2 Sample and observations); "Imaging was performed with MAPPING in GILDAS" (2 Sample and observations)
- deconvolver: _not stated_
- weighting robust: natural weighting (ALMA and NOEMA)  
  > "using a natural weighting scheme for visibilities, with a detection threshold equal to the noise of the pre-imaging visibilities" (2 Sample and observations); "procedures using natural weighting, a 3$\sigma$ cleaning threshold, and a channel width of 20 MHz" (2 Sample and observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Constant function fit to all line-free channels (imfit in CASA)  
  > "fitting a constant function to all line-free channels" (2 Sample and observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: NOEMA continuum-subtracted cubes binned to 20 MHz (~60 km/s)  
  > "Continuum-subtracted cubes were binned to spectral resolutions of 20 MHz" (2 Sample and observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- EOS-Dustfit modelling details are in the earlier paper  
  > "Details about the modeling can be found on the GitHub page and in (cite: Tripodi24b)." (Footnote 4) [from (cite: Tripodi24b)]
- MBB model prescription (optically thin) for cold dust  
  > "following the prescription by (cite: DraineLi07), the cold dust continuum emission is modeled with a modified blackbody (MBB) function" (3.1 Dust properties and star formation rates) [from (cite: DraineLi07)]
- CO SLED correction factors  
  > "We adopted the CO spectral line energy distribution (SLED) correction from (cite: Kaasinen24)" (3.2 Molecular gas mass) [from (cite: Kaasinen24)]
- SFR-L_FIR relation with Chabrier IMF  
  > "SFR is computed with the relation by (cite: Kennicutt98), $SFR/(M_{\odot}\,yr^{-1}) = 10^{-10}\,L_{FIR}/L_{\odot}$, assuming a Chabrier initial mass function" (3.1 Dust properties and star formation rates) [from (cite: Kennicutt98); (cite: Chabrier03)]

### Not stated but needed to reproduce (our reading)

- Which ALMA project and execution blocks map to which of the four targets (and which target J2356 lacks)
- ALMA array configurations, baselines, on-source times and observing dates
- Line-free channel ranges used in the CASA continuum fit and the continuum spectral windows
- tclean cell size, image size, clean mask, niter, deconvolver, uv-range and primary beam correction
- NOEMA array configuration, on-source time, observing dates and project ID (text gives both S23CS and S23CX)
- EOS-Dustfit internal settings (CMB contrast correction, handling of observed vs rest frame, solid angle used) beyond the stated priors
- Exact 40-1000 micron L_FIR integration conventions and the size assumed for flux conversions
- Precise linmix settings and the full L_[CII] values used in the 25-object calibration sample
- Whether the NOEMA data are public and their archive location

## Analysis recipe

1. **calibrate and image NOEMA data**: CLIC calibration and MAPPING imaging with natural weighting; LSB and USB merged for J0313 and J0038 to extract continuum upper limits  
  > "We calibrated the visibilities using the CLIC pipeline of the GILDAS software" (2 Sample and observations); "we merged LSB and USB to increase the signal-to-noise ratio" (2 Sample and observations)
   - software: GILDAS
   - parameter: cubes binned to 20 MHz (~60 km/s)  
  > "Continuum-subtracted cubes were binned to spectral resolutions of 20 MHz" (2 Sample and observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **image archival ALMA band 6 data**: tclean with natural weighting, 3 sigma threshold, 20 MHz channels; continuum from constant fit to line-free channels  
  > "procedures using natural weighting, a 3$\sigma$ cleaning threshold, and a channel width of 20 MHz" (2 Sample and observations); "fitting a constant function to all line-free channels" (2 Sample and observations)
   - software: CASA
   - parameter: CASA version 6.5.5-21  
  > "The imaging was performed through the Common Astronomy Software Applications (CASA; (cite: McMullin07)), version 6.5.5-21." (2 Sample and observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **measure continuum flux densities and sizes**: NOEMA: point-source model fit to visibilities; ALMA: 2D Gaussian fit to cleaned continuum map, size taken as FWHM; upper limits at 3 sigma  
  > "We measured continuum flux densities of NOEMA maps with a fit of the visibilities with a point source model." (3.1 Dust properties and star formation rates); "which is assumed to be equal to the full width half maximum (FWHM) of the best-fit 2D Gaussian function" (3.1 Dust properties and star formation rates)
   - software: GILDAS, CASA
   - parameter: upper limits at 3 sigma assuming a size equal to the beam size  
  > "Flux upper limits are estimated at a 3$\sigma$ significance level using the rms noise and assuming a size equal to the beam size." (3.1 Dust properties and star formation rates)
   - assumption: J2356 source size set to 0.75x0.64 arcsec2, the median FWHM of the four ALMA-resolved quasars  
  > "we assumed a size of $0.75\times0.64$ arcsec$^{\rm 2}$, based on the median value of the FWHM dimensions measured for the four quasars of our sample with ALMA observations" (3.1 Dust properties and star formation rates)
   - fitting: _not stated_
   - validation: For J0252, J1243 and J2356 the Gaussian-integrated flux agrees with the point-source flux within uncertainties  
  > "The two approaches provide flux estimates that are consistent within the uncertainties." (3.1 Dust properties and star formation rates)
4. **fit the cold dust SED**: Modified blackbody, optically thin, fit with EOS-Dustfit; free parameters M_d (and beta for J0252 and J1243)  
  > "following the prescription by (cite: DraineLi07), the cold dust continuum emission is modeled with a modified blackbody (MBB) function, assuming an optically thin regime" (3.1 Dust properties and star formation rates)
   - software: EOS-Dustfit, emcee
   - parameter: T_d = 55 K fixed; beta = 1.6 fixed for J0038, J0313, J2356  
  > "we adopted a fixed temperature, $T_d=55$ K, for all five quasars" (3.1 Dust properties and star formation rates); "we fixed $\beta=1.6$, the local value ((cite: Beelen06) and (cite: Witstok23))" (3.1 Dust properties and star formation rates)
   - parameter: 40 chains, 3000 trials, burn-in 150 steps; 10% calibration uncertainty added in quadrature  
  > "We ran 40 chains, with 3000 trials and a burn-in phase of 150 steps for each dataset" (3.1 Dust properties and star formation rates)
   - parameter: Upper limits included as 1 sigma detection with 2 sigma error  
  > "The upper limits of the continuum emission were included in the fit as a 1$\sigma$ detection with a 2$\sigma$ error." (3.1 Dust properties and star formation rates)
   - assumption: Source size does not vary significantly between ~80 and ~230 GHz  
  > "we assumed that the size does not vary significantly with frequency in the observed range $\sim80$ GHz to $\sim 230$ GHz" (3.1 Dust properties and star formation rates)
   - fitting: MCMC with uniform priors 5<log(M_d/Msun)<9 (all) and 0.5<beta<3.0 (J0252, J1243); best fit = 50th percentile, errors from 16th and 84th percentiles  
  > "A uniform distribution for priors is assumed for fitting parameters in the range: $5<\log(M_{d}/M_{\odot})<9$ for all the quasars, and $0.5<\beta<3.0$ for both J0252 and J1243." (3.1 Dust properties and star formation rates); "We adopted the 50th percentile of the posterior distribution as the best-fit value, while the errors are calculated considering the 16th and 84th percentiles" (3.1 Dust properties and star formation rates)
   - validation: Tested alternative T_d (40, 70 K), beta (1.2, 1.6, 2) and source area; changes in M_d and L_FIR reported  
  > "We tested the consistency of our assumptions (namely, $T_d$, $\beta$) on the results of the SED fitting." (3.1 Dust properties and star formation rates)
5. **derive L_FIR and SFR**: Integrate best-fit model over 40-1000 micron; SFR from Kennicutt relation with Chabrier IMF  
  > "We measured the FIR luminosity ($L_{FIR}$) by integrating the 40-1000 $\mu$m emission of the best-fit model produced by EOS-Dustfit in the five quasars." (3.1 Dust properties and star formation rates); "SFR is computed with the relation by (cite: Kennicutt98), $SFR/(M_{\odot}\,yr^{-1}) = 10^{-10}\,L_{FIR}/L_{\odot}$, assuming a Chabrier initial mass function" (3.1 Dust properties and star formation rates)
   - software: EOS-Dustfit
   - assumption: Chabrier IMF  
  > "assuming a Chabrier initial mass function (IMF; (cite: Chabrier03))" (3.1 Dust properties and star formation rates)
   - fitting: _not stated_
   - validation: SFR consistent within 7% with a Kroupa IMF  
  > "is roughly consistent with the SFR derived assuming a (cite: Kroupa01) IMF (within $7\%$)" (3.1 Dust properties and star formation rates)
6. **derive M_H2 upper limits from CO**: 3 sigma upper limits from the rms at the expected CO(6-5)/(7-6) frequency, converted with CO SLED correction and alpha_CO  
  > "we derived 3$\sigma$ upper limits on the cold $H_2$ mass using the rms at the expected frequency of CO(6–5) and (7–6) emission lines" (3.2 Molecular gas mass)
   - parameter: line width FWHM = 300 km/s; galaxy size equal to the beam  
  > "We assumed a line width of FWHM = 300 km/s" (3.2 Molecular gas mass); "a galaxy size equal to the beam of the observations" (3.2 Molecular gas mass)
   - assumption: alpha_CO = 0.8 Msun (K km/s pc^2)^-1; r_6,1 = 0.92, r_7,1 = 0.65  
  > "Assuming a luminosity to mass conversion factor $\alpha_{co}=0.8$" (3.2 Molecular gas mass); "We adopted the CO spectral line energy distribution (SLED) correction from (cite: Kaasinen24), that is, $r_{6,1}=0.92$ for CO(6-5) and $r_{7,1}=0.65$." (3.2 Molecular gas mass)
   - fitting: _not stated_
   - validation: Compared with [CII]-based M_H2 estimates  
  > "To test the consistency of our $\rm M_{H2}$ upper limits, we compared the CO-derived measurement with that obtained from the" (3.2 Molecular gas mass)
7. **calibrate M_H2-L_[CII] relation**: Linear Bayesian regression of 25 quasars (z>7 sample plus 21 z>~6 literature quasars) with errors on both variables and upper limits on M_H2  
  > "We fitted data points of the resulting quasar sample of 25 objects with a linear regression based on a Bayesian approach, using the Python package" (3.2 Molecular gas mass)
   - software: linmix
   - assumption: Same alpha_CO and CO SLED as for the new data; r_7,6=0.65, r_6,5=0.9, r_2,1=1 for the comparison sample  
  > "assuming for all objects the same fixed CO SLED that we used in Sect." (Comparison sample of high-z quasars)
   - fitting: linmix Bayesian linear regression  
  > "with a linear regression based on a Bayesian approach, using the Python package" (3.2 Molecular gas mass)
   - validation: Compared with Zanella et al. and Madden et al. relations, which overestimate CO-based M_H2  
  > "both relations overestimate significantly the $\rm M_{H2}$ measurement and upper limit derived from $\rm L^{\prime}_{CO}$ in quasars at $z>5$" (3.2 Molecular gas mass)
8. **derive gas-to-dust ratios and trend with M_d**: GDR = M_H2/M_d for 7 of 8 z>7 quasars; GDR vs M_d slope fitted with linmix  
  > "the gas-to-dust ratio (GDR=$\rm M_{H2}$/$\rm M_{d}$) is a crucial parameter" (4.1 Dust enrichment at high redshifts); "by fitting the GDR versus $\rm M_{d}$ with linmix" (4.1 Dust enrichment at high redshifts)
   - software: linmix
   - assumption: Constant alpha_CO  
  > "our $\rm M_{H2}$ estimates are derived with a constant" (4.1 Dust enrichment at high redshifts)
   - fitting: linmix  
  > "by fitting the GDR versus $\rm M_{d}$ with linmix" (4.1 Dust enrichment at high redshifts)
   - validation: Effect of T_d on GDR noted: up to factor ~2 for T_d=65 K or 45 K  
  > "assuming a higher (lower) $\rm T_{d}$ value would result in a higher (lower) GDR up to a factor of $\sim2$" (4.1 Dust enrichment at high redshifts)
9. **depletion time, SFE and GAEA comparison**: t_dep = M_H2/SFR and SFE = 1/t_dep vs redshift, L_FIR and L_bol, compared with literature samples and GAEA predictions  
  > "we show the depletion time ($t_{dep}=M_{H2}/SFR$) as a function of redshift" (4.2 Gas depletion and star formation efficiency); "we then derived the gas SFE, defined as $\rm SFE_{gas}=1/t_{dep}=SFR/M(H_2)$" (4.2 Gas depletion and star formation efficiency)
   - parameter: GAEA quasars: L_bol > 3e46 erg/s at z>6, evolution over ~4e7 yr Eddington time  
  > "We extracted all predicted AGN galaxies from the simulated box with a $L_{\rm bol} > 3\times10^{46}$ erg s$^{-1}$ at $z>6$" (4.2 Gas depletion and star formation efficiency)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **GILDAS** : NOEMA visibility calibration (CLIC)  
  > "We calibrated the visibilities using the CLIC pipeline of the GILDAS software" (2 Sample and observations)
- **MAPPING** : NOEMA imaging  
  > "Imaging was performed with MAPPING in GILDAS" (2 Sample and observations)
- **CASA** 6.5.5-21: Imaging of archival ALMA data (tclean, imfit)  
  > "The imaging was performed through the Common Astronomy Software Applications (CASA; (cite: McMullin07)), version 6.5.5-21." (2 Sample and observations)
- **tclean** CASA 6.5.5-21: Cleaning of archival ALMA data  
  > "procedures using natural weighting, a 3$\sigma$ cleaning threshold, and a channel width of 20 MHz" (2 Sample and observations)
- **EOS-Dustfit** : Modified blackbody fit to the cold dust SED  
  > "we fitted the cold dust SED of the target galaxies" (3.1 Dust properties and star formation rates)
- **emcee** : MCMC sampling within EOS-Dustfit  
  > "using a Markov chain Monte Carlo algorithm implemented in the" (3.1 Dust properties and star formation rates)
- **linmix** : Bayesian linear regression for the M_H2-L_[CII] calibration and GDR trend  
  > "with a linear regression based on a Bayesian approach, using the Python package" (3.2 Molecular gas mass)
- **Astropy** : _not stated_
- **Matplotlib** : _not stated_
- **NumPy** : _not stated_
- **Seaborn** : _not stated_
- **Scipy** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust mass range of the five quasars | 0.6-4e8 | not stated | Msun | 4 | in the range $0.6-4\times10^{8}$ M$_{\odot}$ |
| Dust emissivity index beta of J0252 | 0.93 | +0.20/-0.21 | dimensionless | 4 | For J0252, we derived $\beta=0.93^{+0.20}_{-0.21}$ |
| M_H2 upper limits of the four non-detected NOEMA quasars | ~0.9-1.5e10 | 3 sigma upper limits | Msun | 6 | we derive an upper limit $M(H_2)$ in the range $\sim 0.9-1.5\times 10^{10}$ M$_{\odot}$ |
| Best-fit M_H2-L_[CII] relation | log(M_H2/Msun) = 0.75 log(L_[CII]) + 2.87 | slope +0.31/-0.31; intercept +0.07/-0.07 | dimensionless | 7 | (0.75^{+0.31}_{-0.31} \log(L_{[CII]}) + (2.87^{+0.07}_{-0.07}) |
| M_H2-to-L_[CII] ratio in the 1e9-1e10 Lsun regime | ~3.9 | +1.7/-2.3 | Msun/Lsun | 7 | ratio of $\sim3.9^{+1.7}_{-2.3}$ in the |
| Pearson correlation of L_[CII] with SFR in z>6 quasar hosts | ~0.71 | not stated | dimensionless | 7 | tightly correlated (Pearson correlation coefficient $\sim0.71$) |
| Mean gas-to-dust ratio of EoR quasars | 80 | 40 | dimensionless | 8 | consistent (GDR$_{\rm mean}=80\pm40$) with the local value GDR=100 |
| Slope of GDR vs M_d for EoR quasars | -0.41 | 0.16 | dimensionless | 8 | we find a negative slope ($=-0.41\pm0.16$) when considering only quasars at the EoR |
| SFE of J1007 | 9.7e-9 | 2.5e-9 | 1/yr | 9 | $\rm SFE=9.7\pm2.5\times 10^{-9}$ yr$^{-1}$ |
| SFE lower limits of z>7 quasar hosts | >1e-8 | lower limits | 1/yr | 9 | we find lower SFE limits of $\rm >10^{-8}$ yr$^{-1}$ |

## Qualitative findings

- No clear evolution of dust mass with redshift between z>7 quasars and later epochs  
  > "there is no clear evolution of $\rm M_{d}$ as a function of the redshift" (3.1 Dust properties and star formation rates)
- No clear evidence of efficient quenching of host star formation by quasar feedback among EoR quasars  
  > "there is no clear evidence of an efficient quenching of the host-galaxy star formation due to quasar feedback" (4.2 Gas depletion and star formation efficiency)
- Quasars at the EoR show short depletion times (<~0.1 Gyr)  
  > "the quasars at the EoR show relatively low $t_{dep}$ values ($\lesssim0.1$ Gyr)" (4.2 Gas depletion and star formation efficiency)

## Claim tuples

- H: Do z>7 quasar hosts contain massive molecular gas reservoirs? | E: NOEMA CO(6-5)/(7-6) observations of five quasars, upper limits on M_H2 with alpha_CO = 0.8 | R: No significant CO detections; M_H2 upper limits ~0.9-1.5e10 Msun | F: No massive gas reservoirs (M_H2 less than a few times 1e10 Msun) at z>7; only J1007 has a significant detection | **supported**
- H: Can M_H2 be calibrated from L_[CII] for z>~6 quasars? | E: linmix regression on 25 quasars including the new limits | R: log(M_H2) = 0.75 log(L_[CII]) + 2.87; M_H2/L_[CII] ~3.9 | F: A new quasar-specific calibration, roughly an order of magnitude lower than Zanella et al. | **supported**
- H: Did z>7 quasar hosts already build large dust reservoirs? | E: MBB SED fits with EOS-Dustfit using NOEMA and ALMA continuum, T_d = 55 K | R: M_d ~0.6-4e8 Msun | F: Dust masses ~1e8 Msun in a few hundred Myr, implying efficient dust enrichment processes | **supported**
- H: Is the local gas-to-dust ratio valid for z>7 quasars? | E: GDR = M_H2/M_d from limits and J1007, compared with lower-z quasars and Seyferts | R: Mean GDR 80 +/- 40; limits consistent with or below local value 100 | F: Assuming the local GDR is reasonable up to z~7.5 | **supported**
- H: Are EoR quasar hosts in an intense starburst phase coeval with the quasar? | E: Depletion time, SFE vs L_FIR and L_bol, comparison with literature and GAEA | R: Short t_dep and SFE up to an order of magnitude above non-AGN galaxies | F: Bright quasar phase coeval with rapid host buildup | **supported**

## Reasoning

- Why this data: Aim for a complete census of molecular gas in all known z>=7 quasars  
  > "aiming to obtain a complete census of the molecular gas content in these objects" (2 Sample and observations)
- Why this method: Limited SED sampling prevents fitting three free MBB parameters, so T_d and beta are fixed for most sources  
  > "the limited amount of data prevents us from modeling the FIR SED with three free parameters" (3.1 Dust properties and star formation rates)
- Alternative: Upper limits treated as detections with large errors rather than a zero-likelihood treatment above the limit  
  > "one could either treat them as detections with large errors (as we do" (3.1 Dust properties and star formation rates)
- How they decided it was enough: _not stated_
- Limitation (authors): SED peak not sampled, so dust temperature is hard to constrain  
  > "In particular, the peak of the SED is not sampled by current data, making it challenging to constrain the dust temperature." (3.1 Dust properties and star formation rates)
- Limitation (authors): J0313 NOEMA observation executed in bad weather and did not reach requested sensitivity  
  > "The observation targeting quasar J0313 was executed in bad weather conditions, so it did not reach the requested sensitivity to detect either continuum emission or CO lines in both LSB and USB." (2 Sample and observations)
- Limitation (authors): No standard approach for upper limits in SED fitting  
  > "There is not yet a standard approach for dealing with upper limits in the fitting procedure" (3.1 Dust properties and star formation rates)
- Caveat (inferred, ours): ALMA plays a supporting role; most claims rest on NOEMA non-detections and literature compilations
- Caveat (inferred, ours): Fixed T_d = 55 K from a different sample drives M_d and L_FIR; systematic only partly propagated
- Caveat (inferred, ours): New [CII] calibration is fitted on only 25 objects, mostly upper limits, with a slope uncertainty of 0.31
- Caveat (inferred, ours): Fixed alpha_CO = 0.8 and an assumed CO SLED may bias M_H2 and GDR trends
- Caveat (inferred, ours): Heterogeneous literature data (different SED fits, IMFs, CO transitions) were combined without homogenisation
- Caveat (inferred, ours): Text gives both S23CS and S23CX as the NOEMA project, an inconsistency

## Reproducibility

- Data public (paper): ALMA data retrieved from the science archive; one ALMA project (2023.1.00443.S) was proprietary at the time; NOEMA data status not stated  
  > "were retrieved from the science archive (see the acknowledgements for the list of ALMA project IDs)" (2 Sample and observations); "J2356 observation with project ID 2023.1.00443.S is still in a proprietary period at the moment of this analysis" (Footnote 2)
- Products in archive: _not stated_
- Code: EOS-Dustfit is a publicly available tool (GitHub)  
  > "EOS-Dustfit is a publicly available tool for fitting the cold dust SED of galaxies" (Footnote 4)
- Missing: Mapping of ALMA projects to targets and full observing details (configs, times, dates)
- Missing: Line-free channels, clean mask and imaging parameters for the ALMA continuum
- Missing: NOEMA data access and reduction details beyond CLIC/MAPPING with natural weighting
- Missing: EOS-Dustfit run configuration details and flux tables in machine-readable form
- Missing: Full L_[CII] and M_H2 values for the 25-object calibration sample with exact transformations
- Data volume (inferred): Archival ALMA band 6 measurement sets for four targets across several projects, likely tens of GB raw; NOEMA data additional and not stated as public
- Score (inferred): 3/5, The ALMA data are archival and the SED/regression methods are described with priors and chain settings plus a public code, but the key CO results come from NOEMA data of unstated public status, and imaging and calibration details for ALMA are sparse.
- Rediscovery candidate: no, The headline CO limits rely on new NOEMA data not stated to be public, and the ALMA imaging recipe lacks line-free channels and mask details, so the main results cannot be cleanly redone from stated public data alone.

## Links

- Method: (cite: Tripodi24b) (Describes EOS-Dustfit modelling and the mean dust temperature of z>6 quasars adopted here)
- Companion: (cite: Feruglio23) (Only confirmed individual CO detection at z>7 (J1007), used as the comparison point)
- Companion: (cite: Kaasinen24) (Source of the CO SLED correction adopted)
- Related: NOEMA project S23CX
- Related: GAEA semi-analytic model on P-Millennium

## Checks

```json
{
 "quotes": 156,
 "quotes_ok": 156,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 7,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2023.1.00443.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 129,
  "stated": 93,
  "rate": 0.721
 },
 "evidence_ok": true
}
```
