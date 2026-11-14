# [CII] luminosity models and large-scale image cubes based on COSMOS 2020 and ALPINE-ALMA [CII] data back to the epoch of reionisation

`2024A&A...689A.101C` | Astronomy and Astrophysics 2024 | first author: Clarke, J. | arXiv: 2404.05352 | DOI: 10.1051/0004-6361/202450300

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: cosmology, high_z_galaxies
- Question: Build mock [CII] line intensity mapping cubes from the COSMOS 2020 catalogue with literature and ALPINE-derived [CII] luminosity models, to give lower limits on power spectra and S/N forecasts for FYST EoR-Spec  
  > "We have implemented a novel method to create simulated \[CII\] emission line intensity mapping (LIM) data cubes using COSMOS 2020 galaxy catalogue data." (abstract)
- Target **COSMOS field (COSMOS 2020 FARMER LP sub-sample, E-COSMOS)**: coordinates 149.6-150.8 deg RA, 1.6-2.8 deg Dec (1.2x1.2 deg^2)  
  > "we covered a $1.2\times1.2\deg^2$ area corresponding to 149.6–150.8 $\deg$ RA and 1.6–2.8 $\deg$ Dec" (Map creation); "We took LP_zPDF as photometric redshift, MASS_MED for stellar mass, SFR_MED for SFR" (Data: COSMOS 2020); "We use a flat $\Lambda$CDM dark matter universe, taking $H_0=70 \textrm{kms}^{-1}\textrm{Mpc}^{-1}$, $\Omega_\textrm{M}=0.3$, and $\Omega_\Lambda=0.7$." (Introduction); z/distance photometric redshifts 3.42<z<3.87, 4.14<z<4.76, 5.34<z<6.31, 6.75<z<8.27  
  > "we covered a $1.2\times1.2\deg^2$ area corresponding to 149.6–150.8 $\deg$ RA and 1.6–2.8 $\deg$ Dec" (Map creation); "We took LP_zPDF as photometric redshift, MASS_MED for stellar mass, SFR_MED for SFR" (Data: COSMOS 2020); "We use a flat $\Lambda$CDM dark matter universe, taking $H_0=70 \textrm{kms}^{-1}\textrm{Mpc}^{-1}$, $\Omega_\textrm{M}=0.3$, and $\Omega_\Lambda=0.7$." (Introduction); distance from COSMOS 2020 FARMER LP photometric redshift (LP_zPDF); flat LCDM H0=70, Omega_M=0.3  
  > "we covered a $1.2\times1.2\deg^2$ area corresponding to 149.6–150.8 $\deg$ RA and 1.6–2.8 $\deg$ Dec" (Map creation); "We took LP_zPDF as photometric redshift, MASS_MED for stellar mass, SFR_MED for SFR" (Data: COSMOS 2020); "We use a flat $\Lambda$CDM dark matter universe, taking $H_0=70 \textrm{kms}^{-1}\textrm{Mpc}^{-1}$, $\Omega_\textrm{M}=0.3$, and $\Omega_\Lambda=0.7$." (Introduction)
- Target **ALPINE galaxies in COSMOS (65 with [CII] detections, used to fit models)**: coordinates _not stated_; z/distance 4.4<z<4.65 (45 galaxies) and 5.05<z<5.9 (20 galaxies)  
  > "We therefore took the 65 galaxies that have successful \[CII\] detection above 3.5 $\sigma$, lie within the COSMOS field, and have the empirical bulk property data (stellar masses and SFRs) required to create \[CII\] models." (Data: ALPINE); "Of these galaxies, 45 lie within $4.4<z<4.65$ and 20 lie within $5.05<z<5.9$." (Data: ALPINE); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: Band 7 (275-373 GHz) for ALPINE  
  > "falling within ALMA band 7 (275–373 GHz)" (Data: ALPINE)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: mid-2018 to early 2019  
  > "The ALPINE survey was undertaken between mid-2018 and early 2019 as an Atacama Large Millimeter/submillimeter Array (ALMA) Large Program" (Data: ALPINE)
- pi or archival as stated: ALMA Large Program (ALPINE); published ALPINE results used, not reduced here  
  > "The ALPINE survey was undertaken between mid-2018 and early 2019 as an Atacama Large Millimeter/submillimeter Array (ALMA) Large Program" (Data: ALPINE)
- Line: [CII] 2P3/2-2P1/2 (158 um) (1900.537 GHz)
- Other facility **COSMOS 2020 catalogue (FARMER LP)**: Galaxy positions, photometric redshifts, stellar masses and SFRs used to populate the mock cubes  
  > "We created our intensity cubes using data from the COSMOS 2020 galaxy catalogue, release version 4.1.1" (Data: COSMOS 2020)
- Other facility **FYST EoR-Spec DSS (assumed survey)**: Assumed bands, resolutions and noise levels for the mock observations  
  > "The frequency range of EoR-Spec DSS, 420–210 GHz, is to be split into four frequency bands." (EoR-Spec DSS)
- Other facility **CANDELS (HST)**: Deeper galaxy counts used to estimate incompleteness of FARMER LP  
  > "We primarily used the Cosmic Assembly Near-infrared Deep Extragalactic Legacy Survey" (Using CANDELS data)
- Other facility **REBELS (ALMA)**: IR luminosity function comparison for the 6.75<z<8.27 band  
  > "a survey targeting 42 galaxies at $6.4<z<7.7$ including 15 spectroscopically confirmed \[CII\] sources" (Assumptions made for constructing intensity cubes and power spectra)
- External data: ALPINE stellar masses and SFRs (LePhare SED fits)  
  > "The bulk properties were determined using the LePhare code, as done in COSMOS 2015" (Data: ALPINE) [from (cite: Arnouts_2002); (cite: Davidzon_2017)]
- External data: Literature [CII]-SFR linear log-log relations (DL14 Entire/Starburst, Si15, Sc20, Ro22; Table 1)  
  > "The authors derived empirical linear log-log \[CII\]-SFR relations based on the ALPINE sample." ([CII] modelling) [from (cite: DeLooze_2014), (cite: Silva_2015), (cite: Schaerer_2020), (cite: Romano_2022)]
- External data: Metallicity relation used to compute metallicity for ALPINE galaxies  
  > "Metallicity is not included in the ALPINE sample data, but we calculated it for each galaxy using" ([CII] modelling) [from (cite: Mannucci_2010)]
- External data: COSMOS 2020 mass Schechter fit parameters (Table 6)  
  > "fit parameters were taken from" (Table 6 notes) [from (cite: Weaver_2022b)]
- External data: EoR-Spec survey sensitivity per pixel (2.2e4, 1.2e4, 6.2e3, 3.9e3 Jy/sr)  
  > "the survey sensitivity per pixel in units of Jy sr$^{-1}$, is described for EoR-Spec in Table 1 of" (Power spectra error) [from (cite: Chung_2020)]
- Simulation/model as data: [CII] luminosity models (literature and ALPINE-derived m1-m4) applied to COSMOS 2020 galaxies to make mock LIM cubes  
  > "We applied \[CII\]158$\mu$m luminosity models to COSMOS 2020 to create LIM cubes" (abstract)

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
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALPINE [CII] model fitting approach  
  > "In order to create models from ALPINE data, we fitted \[CII\] results to bulk property data in a similar manner to" ([CII] modelling) [from (cite: Schaerer_2020) and (cite: Romano_2022)]
- Power spectrum error formulation  
  > "we followed the adapted version of their process as used by" (Power spectra) [from formulated by (cite: Li_2016), adapted by (cite: Chung_2020) and (cite: Karoumpis_2022)]
- EoR-Spec frequency bands  
  > "We took the specific bands used in past work" (EoR-Spec DSS) [from (cite: Chung_2020); (cite: Karoumpis_2022); (cite: Roy_2023)]
- Mass completeness limit procedure  
  > "In addition to these methods we also manually calculated the $M_{\textrm{lim}}$ value by following the same procedure as" (Using CANDELS data) [from (cite: Weaver_2022b)]

### Not stated but needed to reproduce (our reading)

- Identifiers and values of the 65 ALPINE galaxies (stellar mass, SFR, L[CII] with errors) are not tabulated; they must be taken from the public ALPINE catalogues
- Number of Monte Carlo draws and error model used for the fit-parameter uncertainties
- Which least-squares routine and weights were used for the model fits and the 5-bin fits
- Random seeds and sampling used for the ten random stellar-mask realisations and for placing extrapolated galaxies
- Exact Schechter fit ranges and the specific fits chosen for each model and band; several valid fits exist
- The stellar mask definition and the numerical handling of galaxies near cube edges
- No analysis code is released, so the voxel assignment, binning and S/N code must be rewritten
- How the model-dependent luminosity function binning was set up beyond dex=0.1

## Analysis recipe

1. **Select the COSMOS 2020 FARMER LP sub-sample per redshift band**: Adopt the FARMER LP sub-sample of COSMOS 2020 and select galaxies by photometric redshift within the square area for each band, removing galaxies with IRAC Ch1 AB mag above 26  
  > "we adopted that sub-sample and refer to it as FARMER LP" (Data: COSMOS 2020); "removed galaxies with IRAC Channel 1 AB magnitudes above 26 as these galaxies are likely to be artefacts" (Data: COSMOS 2020)
   - parameter: Columns LP_zPDF (redshift), MASS_MED (stellar mass), SFR_MED (SFR)  
  > "We took LP_zPDF as photometric redshift, MASS_MED for stellar mass, SFR_MED for SFR" (Data: COSMOS 2020)
   - assumption: Quiescent-galaxy incompleteness is not a significant source of uncertainty  
  > "this quiescent galaxy incompleteness and subsequent missing \[CII\] signal is unlikely to be a significant source of uncertainty for our study." (Data: COSMOS 2020)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive ALPINE-based [CII] luminosity models m1-m4**: Least-squares fits of L[CII] to combinations of bulk properties (SFR, stellar mass, sSFR, metallicity), on individual galaxies and on 5-bin averages, then selection of acceptable models  
  > "These fits were applied to all 65 data points using standard least-squares fitting procedures, as well as to these data points sorted into 5 bins." ([CII] modelling)
   - parameter: chi2_nu acceptance limit of 4 sigma around 1  
  > "A model was viewed as acceptable when its $\chi^2_\nu$ is within $4\,\sigma$ of the expected value for a good model, 1." (ALPINE model checks)
   - parameter: No second-order or higher models converged  
  > "We did attempt to fit to second-order terms, but no higher order models successfully converged." ([CII] modelling)
   - assumption: Only physical bulk properties used; no fits with spectral lines, IR emission or redshift  
  > "We did not attempt to fit models with spectral lines (such as \[OIII\]), IR emission, or redshift" ([CII] modelling)
   - fitting: Least-squares fits; parameter errors from Monte Carlo methods  
  > "We calculated the errors in the fit parameters using Monte Carlo methods." ([CII] modelling)
   - validation: Outlier-input test, comparison of resulting L[CII] distributions with ALPINE (<20% difference in mean and standard deviation) and a physical-sense check  
  > "If these distributions had similar means and standard deviations ($<20$% difference), we accepted the model." (ALPINE model checks); "Finally, we checked that each model made basic physical sense." (ALPINE model checks)
3. **Apply [CII] models to FARMER LP galaxies**: Apply the literature and ALPINE [CII] models to the bulk properties of each galaxy to get L[CII]  
  > "We applied the \[CII\] models to the bulk property data (i.e. stellar masses, SFRs) of the sub-sample to estimate \[CII\] luminosity data" (Method)
   - assumption: Models taken from empirical literature rather than PDR or simulation-based models, to reduce assumptions  
  > "We took models from previous literature that used empirical data instead of those that used PDR modelling and other simulations, in order to reduce the number of assumptions made when creating our intensity cubes and power spectra." ([CII] modelling)
   - fitting: _not stated_
   - validation: _not stated_
4. **Build mock LIM intensity cubes with stellar-mask extrapolation**: Insert each galaxy luminosity in a voxel by RA, Dec and luminosity distance, convert to intensity in Jy/sr, and fill stellar-masked regions with randomly drawn galaxies  
  > "depending on its RA, Dec, and luminosity distance which we calculated using its redshift" (Map creation); "we added a number of galaxies to the sample in the masked regions to ensure the galaxy density of masked and unmasked regions was made equal" (Map creation)
   - parameter: Cube dimensions 117x117x10, 112x112x11, 94x94x14, 82x82x18 voxels  
  > "this results in cube dimensions of $117\times117\times10$, $112\times112\times11$, $94\times94\times14$, and $82\times82\times18$ voxels, respectively" (Map creation)
   - parameter: Ten random masks averaged  
  > "we created ten random masks to use in intensity cube creation, and averaged the resulting power spectra of these cubes" (Map creation)
   - assumption: Photometric redshift scatter does not meaningfully change the power spectrum (<0.1 dex)  
  > "Upon investigation we found that the difference in power spectra magnitude from this scatter is less than 0.1 dex" (Map creation)
   - fitting: _not stated_
   - validation: Power spectra with and without mask extrapolation compared for Si15  
  > "We verified this by comparing the power spectra of intensity cubes with and without mask extrapolation over all redshift bands using Si15" (Assumptions made for constructing intensity cubes and power spectra)
5. **Compute spherically averaged 3D power spectra and lower limits**: FFT of the intensity cube, normalised by voxel volume per voxel, spherically averaged in k shells  
  > "We then took the 3D intensity cubes and performed a Fast Fourier Transform (FFT) over all elements in the cube" (Power spectra)
   - parameter: Wide k bins of Delta k = 0.3 Mpc^-1 as the alternative to narrowest bins  
  > "The second method used far broader $k$ bins with $\Delta k=0.3$ Mpc$^{-1}$" (Power spectra)
   - parameter: Output as k^3 P(k)/2pi^2 in (Jy/sr)^2  
  > "By convention we multiplied $P(k)$ through to find $k^3P(k)/2\pi^2$ in units of $(\textrm{Jy\,sr}^{-1})^2$" (Power spectra)
   - fitting: _not stated_
   - validation: _not stated_
6. **Estimate noise and S/N for FYST EoR-Spec**: Analytic error sigma(k) from instrumental thermal noise, sample variance of k modes and beam smoothing  
  > "This error, $\sigma$, depends on instrumental thermal noise, the sample variance from binning $k$ modes, and instrumental beam smoothing." (Power spectra)
   - parameter: Assumed 2000 h observation; also tested tripled time  
  > "We recalculated these for greater observation time than our assumed 2000 hours" (Error analysis)
   - assumption: Fixed observing conditions, 45 degree elevation angle and 0.4 mm PWV; 100% signal extraction efficiency  
  > "This assumes fixed observing conditions, notably a 45 degree observing angle with 0.4mm precipitable water vapour." (Power spectra error); "These calculations also assume that signal extraction is 100% efficient" (Error analysis)
   - fitting: _not stated_
   - validation: _not stated_
7. **Extrapolate missing galaxies using CANDELS ratios and Schechter fits**: Add galaxies above the mass threshold following FARMER LP/CANDELS ratios, then add galaxies equal to the difference between a Schechter fit and the FARMER LP mass or luminosity function per dex interval  
  > "We always extrapolated additional galaxies above the mass thresholds in the FARMER LP sample following these ratios before applying the other extrapolation methods." (Using CANDELS data); "we generated a number of galaxies equivalent to the difference between the Schechter fit and the actual FARMER LP function for each dex interval" (Extrapolating from mass and luminosity functions using Schechter curves)
   - parameter: FARMER LP/CANDELS number ratios 78%, 78%, 51%, 58%  
  > "which were 78%, 78%, 51%, and 58% respectively" (Using CANDELS data)
   - parameter: Extrapolation floor 1e5 Lsun or 1e7 Msun; dex interval 0.1  
  > "we only extrapolated down to $10^5L_\odot$ or $10^7M_\odot$" (Extrapolating from mass and luminosity functions using Schechter curves); "As before, we always used dex=mass or luminosity interval=0.1" (Extrapolating from mass and luminosity functions using Schechter curves)
   - assumption: Mass and luminosity functions follow a Schechter function  
  > "we assumed that the mass and luminosity functions of galaxy populations are likely to follow a Schechter function" (Extrapolating from mass and luminosity functions using Schechter curves)
   - assumption: SFR for added galaxies from the redshift-band main sequence  
  > "then used the galaxy main sequence of the given redshift band to calculate SFR" (Extrapolating from mass and luminosity functions using Schechter curves)
   - fitting: Schechter fits chosen to minimise least-squares errors with gradients consistent with Weaver et al.  
  > "Our approach was to select fits that minimised errors according to least-squares fitting procedures and with gradients that were in alignment with previous studies" (Discussion)
   - validation: Compared fits that over- and under-estimate and different end points; negligible changes except the overestimate fit  
  > "While we found negligible differences between the power spectra for the other fits, the shot-noise for the overestimate fit was inflated by at least 0.2 dex." (Extrapolating from mass and luminosity functions using Schechter curves)
8. **Place extrapolated galaxies with a weighting cube and recompute power spectra and S/N**: Weighting cube based on FARMER LP stellar mass, similar to Voronoi tessellation, used to draw x, y, z positions of added galaxies; then repeat power spectrum and S/N analysis and compare with literature  
  > "we implemented a weighting cube. This is an array that has the same dimensions of the intensity cube and stores relative weights in each voxel" (Voronoi tessellation for galaxy distribution)
   - parameter: Baseline weight equal to one average galaxy per voxel  
  > "Furthermore, we added a baseline weight equivalent to adding an average galaxy to each voxel." (Voronoi tessellation for galaxy distribution)
   - assumption: Extrapolated dim galaxies lie within clusters traced by the most massive galaxies; filaments not modelled  
  > "This process assumes the majority of extrapolated dim galaxies lie within these clusters, however does not meaningfully account for other structures such as cosmological filaments." (Voronoi tessellation for galaxy distribution)
   - fitting: _not stated_
   - validation: Voronoi-tessellation placement compared with random placement and with no extrapolation  
  > "However the structure component is very different, with the clustering in the random location case regressing to the no extrapolation case" (Assumptions made for constructing intensity cubes and power spectra)

## Software

- **astropy** : Python package used extensively (specific use not stated)  
  > "We made extensive use of the Python packages astroPy" (Acknowledgements)
- **numpy** : Python package used extensively (specific use not stated)  
  > "We made extensive use of the Python packages astroPy" (Acknowledgements)
- **scipy** : Python package used extensively (specific use not stated)  
  > "We made extensive use of the Python packages astroPy" (Acknowledgements)
- **matplotlib** : Python package used extensively (specific use not stated)  
  > "We made extensive use of the Python packages astroPy" (Acknowledgements)
- **LePhare** : Derivation of ALPINE bulk properties (stellar mass, SFR) in the cited work  
  > "The bulk properties were determined using the LePhare code" (Data: ALPINE)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| k^3P(k)/2pi^2 at k=1 Mpc^-1, 3.42<z<3.87 (lower limit) | 3.06e7 | not stated | (Jy sr^-1)^2 | 5 | the amplitudes at $k=1\,\textrm{Mpc}^{-1}$ are $3.06\times10^7, 1.43\times10^7, 9.80\times10^5, 2.77\times10^5\,(\textrm{Jy\,sr}^{-1})^2$ |
| k^3P(k)/2pi^2 at k=1 Mpc^-1, 4.14<z<4.76 (lower limit) | 1.43e7 | not stated | (Jy sr^-1)^2 | 5 | the amplitudes at $k=1\,\textrm{Mpc}^{-1}$ are $3.06\times10^7, 1.43\times10^7, 9.80\times10^5, 2.77\times10^5\,(\textrm{Jy\,sr}^{-1})^2$ |
| k^3P(k)/2pi^2 at k=1 Mpc^-1, 5.34<z<6.31 (lower limit) | 9.80e5 | not stated | (Jy sr^-1)^2 | 5 | the amplitudes at $k=1\,\textrm{Mpc}^{-1}$ are $3.06\times10^7, 1.43\times10^7, 9.80\times10^5, 2.77\times10^5\,(\textrm{Jy\,sr}^{-1})^2$ |
| k^3P(k)/2pi^2 at k=1 Mpc^-1, 6.75<z<8.27 (lower limit) | 2.77e5 | not stated | (Jy sr^-1)^2 | 5 | the amplitudes at $k=1\,\textrm{Mpc}^{-1}$ are $3.06\times10^7, 1.43\times10^7, 9.80\times10^5, 2.77\times10^5\,(\textrm{Jy\,sr}^{-1})^2$ |
| FARMER LP galaxy counts per band after IRAC cut | 14611, 9322, 1732, 510 | not stated | galaxies | 1 | we obtained 14 611, 9322, 1732, 510 galaxies respectively |
| Model m2 coefficients (log L[CII] = a + b log Mstar) | a=4.02, b=0.476 | a +/-0.35, b +/-0.035 | dimensionless | 2 | 4.02(\pm0.35)+0.476(\pm0.035) |
| Model m3 coefficients (a, SFR term, Mstar term) | a=3.31, SFR coeff=-0.33, Mstar coeff=0.601 | +/-0.38, +/-0.16, +/-0.057 | dimensionless | 2 | 3.31(\pm0.38)-0.33(\pm0.16); 0.601(\pm0.057) |
| Model m1 leading coefficients (a, Mstar term) | a=48.22, Mstar coeff=-3.49 | +/-12.07, +/-2.24 | dimensionless | 2 | 48.22(\pm12.07)-3.49(\pm2.24) |
| Model m4 leading coefficients (a, sSFR term) | a=6.14, sSFR coeff=-0.31 | +/-1.29, +/-0.15 | dimensionless | 2 | 6.14(\pm1.29)-0.31(\pm0.15) |
| Stellar-masked area | 0.12 deg^2 (~10% of FARMER LP area) | not stated | deg^2 | 4 | regions span over a total area of $0.12\deg^2$, approximately 10% of the area of FARMER LP |
| Narrow k-bin width per band | 0.043, 0.040, 0.037, 0.035 | not stated | Mpc^-1 | 5 | $\Delta k=0.043,0.040,0.037,0.035$ Mpc$^{-1}$ respectively |
| Stellar mass thresholds for CANDELS correction | 10^9.2, 10^9.3, 10^9.5, 10^9.7 | within 0.05 dex across three methods | Msun | 7 | $10^{9.2}$, $10^{9.3}$, $10^{9.5}$, $10^{9.7}M_\odot$ for |
| FARMER LP to CANDELS number ratio above mass threshold | 78%, 78%, 51%, 58% | not stated | percent | 7 | which were 78%, 78%, 51%, and 58% respectively |
| Power spectrum increase from extrapolation | 0.2-0.4 dex (3.42<z<3.87); 0.5-0.8 dex (5.34<z<6.31) | not stated | dex | 8 | The power spectra magnitude increase is relatively small at low redshift ($0.2-0.4$ dex at $3.42<z<3.87$) but is more significant at high redshift ($0.5-0.8$ dex at $5.34<z<6.31$). |

## Qualitative findings

- Lower-limit power spectra from COSMOS 2020 are almost always below previous simulation predictions and below the expected instrument sensitivity  
  > "Our power spectra are almost always lower in magnitude when compared to the previous literature, including lying below the expected sensitivity of the instrument." (Power spectra, comparison to previous work, and lower limits)
- With extrapolation the power spectra are consistent with prior predictions  
  > "For the extrapolated sample, the power spectra are consistent with prior predictions, indicating that extrapolation is a viable method for creating mock LIM cubes." (abstract)
- High-redshift results are inconclusive because of COSMOS 2020 incompleteness  
  > "However, our high-redshift results remain inconclusive because of the poor completeness of COSMOS 2020 at $z>6.3$." (abstract)
- Only the ALPINE models reach the uppermost predicted limits, suggesting those predictions may be optimistic  
  > "only the ALPINE models m1-m4 reach the uppermost predicted limits" (Discussion)

## Claim tuples

- H: Empirical catalogue data plus [CII] models give robust lower limits to the [CII] LIM power spectrum | E: Mock LIM cubes from FARMER LP with literature and ALPINE [CII] models, power spectra in four EoR-Spec bands | R: Amplitudes at k=1 Mpc^-1 of 3.06e7, 1.43e7, 9.80e5, 2.77e5 (Jy/sr)^2 | F: These are lower limits that cannot exclude the lower ends of previous simulated spectra | **supported**
- H: Extrapolating from the COSMOS 2020 faint end reproduces earlier simulation-based predictions | E: CANDELS-ratio correction, Schechter extrapolation and weighting-cube placement, then power spectra | R: Extrapolated spectra overlap literature predictions; increase of about 0.5 dex over the original sample | F: Extrapolation is a viable way to build mock LIM cubes | **supported**
- H: FYST EoR-Spec can detect the predicted power spectra | E: Analytic S/N from instrument noise for original and extrapolated samples | R: S/N>1 only with wide k bins in extrapolated samples (100% extraction efficiency assumed) | F: Detection is plausible only for the more complete samples with wide bins | **partially**
- H: ALPINE galaxy bulk properties yield useful [CII] models beyond the [CII]-SFR relation | E: Fits of L[CII] to SFR, stellar mass, sSFR, metallicity combinations, four models retained | R: Four models m1-m4 within the 4 sigma chi2 limit, spanning about 1 dex in power spectra | F: Models diverge from linear log-log [CII]-SFR and are less constrained outside ALPINE redshifts | **supported**
- H: The method works at 6.75<z<8.27 | E: Mask extrapolation and comparison with REBELS luminosity functions | R: Large mask extrapolation roughly doubles the sample and results eclipse simulations | F: Results in the highest redshift band are not reliable | **refuted**

## Reasoning

- Why this data: ALPINE galaxies lie in the COSMOS field and are in COSMOS 2020, so models from them suit the wider COSMOS field  
  > "This sample is ideal for creating models of \[CII\] emission for the wider COSMOS field, as ALPINE galaxies are also present in the COSMOS 2020 galaxy catalogue" (Data: ALPINE)
- Why this method: Empirical literature models chosen to minimise assumptions  
  > "in order to reduce the number of assumptions made when creating our intensity cubes and power spectra." ([CII] modelling)
- Alternative: Vallini 2015, Lagache 2018 and Padmanabhan 2019 [CII] models rejected for the cubes (simulation based or needing halo mass)  
  > "but they were inappropriate for our purposes, either being based on simulated galaxies or requiring bulk properties, such as halo mass, which were not recorded in FARMER LP." ([CII] modelling)
- Alternative: Random placement of extrapolated galaxies rejected because it removes clustering  
  > "However the structure component is very different, with the clustering in the random location case regressing to the no extrapolation case" (Assumptions made for constructing intensity cubes and power spectra)
- How they decided it was enough: Fits stopped at first-order combinations because higher order did not converge  
  > "We did attempt to fit to second-order terms, but no higher order models successfully converged." ([CII] modelling)
- Limitation (authors): ALPINE sample biased toward star-forming galaxies  
  > "this sample is biased towards SFGs over quiescent galaxies" (Data: ALPINE)
- Limitation (authors): Error budget excludes foregrounds and sky noise  
  > "While we cannot presently include all possible error contributions, such as errors from foreground contamination removal and sky noise" (Error analysis)
- Limitation (authors): Multiple Schechter fits are valid and change the extrapolated counts  
  > "In many cases we could produce multiple valid Schechter fits for a given function" (Extrapolating from mass and luminosity functions using Schechter curves)
- Caveat (inferred, ours): The ALMA data enter only as published ALPINE bulk properties; no ALMA data processing is done
- Caveat (inferred, ours): m1-m4 are fit to 65 galaxies with 4 sigma chi2 leniency and 1-5 data points in binned fits, so they are weakly constrained
- Caveat (inferred, ours): Lower limits depend on photometric redshifts with scatter wider than the frequency channels
- Caveat (inferred, ours): Extrapolated clustering relies on an ad hoc weighting cube
- Caveat (inferred, ours): S/N assumes 100% signal extraction and no foregrounds

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: No code released
- Missing: ALPINE galaxy table not given in the paper
- Missing: Random seeds and exact Schechter fits for each model not stated
- Missing: Stellar mask definition not given in the paper
- Data volume (inferred): Small: COSMOS 2020 FARMER LP catalogue (about 1.7 million rows, a table of order a GB) plus published ALPINE catalogue values; no ALMA visibilities needed
- Score (inferred): 3/5, Public catalogues and equations are given with numeric tables, but no code, random draws and Schechter fit choices are not fully specified
- Rediscovery candidate: yes, COSMOS 2020 and ALPINE catalogues are public and the lower-limit power spectra (Table 2) follow from a simple published recipe with numeric results, though extrapolated results depend on unstated fit choices

## Links

- Method: (cite: Weaver_2022a); (cite: Weaver_2022b) (COSMOS 2020 catalogue and its mass completeness and mass function fits)
- Method: (cite: Li_2016); (cite: Chung_2020) (Power spectrum error and S/N formulation)
- Method: (cite: Schaerer_2020); (cite: Romano_2022) (ALPINE-based [CII]-SFR fitting approach)
- Companion: (cite: Bethermin_2020); (cite: Faisst_2020); (cite: Le_F_vre_2020) (ALPINE survey papers providing the [CII] and bulk property data)
- Companion: (cite: Karoumpis_2022) (Previous EoR-Spec mock power spectra used for comparison)
- Related: ALPINE
- Related: COSMOS 2020
- Related: EoR-Spec DSS (FYST)
- Related: REBELS
- Related: CANDELS
- Related: CONCERTO
- Related: TIME

## Checks

```json
{
 "quotes": 109,
 "quotes_ok": 109,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2017.1.00428.L"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 117,
  "stated": 72,
  "rate": 0.615
 },
 "evidence_ok": true
}
```
