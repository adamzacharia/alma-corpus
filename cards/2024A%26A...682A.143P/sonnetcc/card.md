# A dynamic view of V Hydrae. Monitoring of a spectroscopic-binary AGB star with an alkaline jet

`2024A&A...682A.143P` | Astronomy and Astrophysics 2024 | first author: Planquart, L. | arXiv: 2405.07820 | DOI: 10.1051/0004-6361/202347947

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: evolved_stars, stellar_physics
- Question: Confirm the binary nature of V Hya by deriving its orbital parameters and test the effect of the orbital motion on the circumbinary environment (conical jet from the companion), then compare the jet orientation with ALMA CO high-velocity emission  
  > "we aim to confirm the binary nature of V Hydrae by deriving its orbital parameters and investigating the effect of the orbital motion on the circumbinary environment." (abstract)
- Target **V Hya (V Hydrae)**: coordinates _not stated_; z/distance 434 +/- 21 pc  
  > "corresponding to a distance of 434$\pm$21 pc" (3.1.2 Orbital parameters with ORVARA (step 2)); distance from Gaia DR3 parallax  
  > "corresponding to a distance of 434$\pm$21 pc" (3.1.2 Orbital parameters with ORVARA (step 2))

## Data provenance

- ALMA projects: 2018.1.01113.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival data from another team's program (PI: Sahai R., Project ID: 2018.1.01113.S); only used as a comparison overlay  
  > "on the high-velocity emission obtained from ALMA observations (PI: Sahai R., Project ID: 2018.1.01113.S)" (7.3 Connection to large-scale bipolar outflows)
- Line: 12CO J = 2-1 (ALMA, high-velocity bipolar jet) (not stated)
- Line: Na I D1 line (HERMES optical, modelled) (5895.92 Angstrom)
- Line: K I resonance doublet (HERMES optical) (7664.89 and 7698.96 Angstrom)
- Other facility **HERMES spectrograph on the 1.2m Mercator telescope**: 130 high-resolution optical spectra 2011-2023, used for RVs and line profiles  
  > "A total of 130 spectra were taken on different dates between 2011 and 2023, with an average exposure time of 900 seconds." (2.1 Spectroscopic data)
- Other facility **AAVSO**: Archival visual photometry, 9000 measurements 1913-2023  
  > "The overall dataset (9000 measurements) covers a time interval from 1913 to 2023" (2.2 Photometric data)
- Other facility **Hipparcos and Gaia**: Astrometry (proper motions, parallax) used to constrain inclination  
  > "have been used to constrain additional parameters that are not accessible from spectroscopic data alone, such as the orbital inclination." (2.3 Astrometric data)
- Other facility **UVES POP archive**: Archival carbon-star spectra, X Tra used as unattenuated template  
  > "We kept X Tra as a template model." (Appendix: Dynamic model spectrum)
- External data: Nine additional RV values added to the HERMES RV curve  
  > "nine additional RV values obtained by (cite: Barnbaum) have been added to the RV curve obtained with the HERMES spectrograph." (3.1.1 Disentangling the pulsation (step 1)) [from (cite: Barnbaum)]
- External data: Hipparcos-Gaia catalog of accelerations (instantaneous proper motions at Hipparcos epoch)  
  > "We thus decided to keep the 60/40 mean value computed in the catalog of acceleration (cite: acceleration_2021ApJS..254...42B)" (3.3 Sensitivity with respect to the Hipparcos data) [from (cite: acceleration_2021ApJS..254...42B)]
- External data: Photometric periods of V Hya (17 y and 530 d) and 2700 K AGB temperature  
  > "a long period of 6160 $\pm$ 400 d with an amplitude of 3 mag and a short period of 530 $\pm$ 30 d with an amplitude of 1.5 mag (cite: Knapp_LC_1999)" (1 Introduction) [from (cite: Knapp_LC_1999)]
- External data: Large-scale CO high-velocity bipolar outflow and S II jet used as comparison for jet orientation  
  > "Its direction is consistent with previous measurements, at a larger scale, of the high-velocity blue-shifted \[S II\] emission" (7.3 Connection to large-scale bipolar outflows) [from (cite: Sahai1; Sahai_ALMA_2022ApJ...929...59S)]
- Simulation/model as data: Kurucz model spectrum of an A0 star (9950 K) used for the companion in the SED test  
  > "The V Hya B spectrum was modelled as an A0 star with a temperature of 9950 K from Kurucz models" (3.4 Nature of the companion)

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

- Spatio-kinematic jet modelling engine and fitting routine reused and adapted to the Na I line  
  > "To deduce the jet structure (geometry, velocity, and density profile) we used the same spatio-kinematic modelling engine" (6 Spatio-kinematic modelling of the outflow) [from (cite: Dylan2) Bollen et al. 2019; stellar jet configuration from (cite: Dylan_vel_profile_2020A&A...641A.175B)]
- ORVARA numerical implementation (parallel-tempering MCMC fit of RV plus absolute astrometry)  
  > "Details on the numerical implementation can be found in the reference paper (cite: orvara_2021AJ....162..186B)." (3.1.2 Orbital parameters with ORVARA (step 2)) [from (cite: orvara_2021AJ....162..186B)]
- HERMES data reduction with the dedicated pipeline and long-term RV stability estimate  
  > "The dedicated python-based pipeline was used for the data reduction." (2.1 Spectroscopic data) [from (cite: HERMES) Raskin et al. 2011]
- Radiative transfer and numerical implementation of the jet model  
  > "We refer to the reference paper (cite: Dylan2) for additional details on the numerical implementation of the radiative transfer equation and the spatio-kinematic modelling." (Appendix: Radiative transfer through the jet) [from (cite: Dylan2)]

### Not stated but needed to reproduce (our reading)

- Everything about the ALMA data processing: calibration, CASA version, imaging, continuum subtraction, beam, rms, velocity channels of the high-velocity 12CO(2-1) emission used in the overlay (apparently the published product from the PI team is used)
- How the ALMA map was made into the overlay and which velocity range or moment was shown
- Sky coordinates of V Hya
- Number of walkers, steps, priors and likelihood used for the MCMC jet fit (only parameter ranges are tabulated)
- Exact HERMES RV for all 100 non-shock spectra beyond the partial table and the full HERMES spectra themselves
- Flux modulation law used to build the dynamic X Tra template and the scattering-source normalisation constants
- Random seeds and initial points of the ORVARA runs

## Analysis recipe

1. **Measure radial velocities from HERMES spectra**: Cross-correlate each spectrum with a carbon-star template mask and fit a Gaussian to the CCF  
  > "The radial velocity (RV) was obtained by cross-correlating the object spectrum with a carbon-star template and fitting a Gaussian function to the mean line profile" (2.1 Spectroscopic data)
   - software: HERMES pipeline
   - parameter: Mask lines deeper than relative level 0.8, wavelength range 476.9 - 654.7 nm  
  > "All lines with a depth getting below the relative level of 0.8 with respect to the local continuum were kept in the mask." (2.1 Spectroscopic data); "This mask, covering the wavelength range 476.9 — 654.7 nm" (2.1 Spectroscopic data)
   - parameter: 0.07 km/s added in quadrature for long-term stability; 30 spectra near maximum light excluded for shocks  
  > "Thirty spectra were excluded from the orbital analysis because they bear the signature of shocks." (2.1 Spectroscopic data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Disentangle pulsation from orbit with RV only**: Fit asymmetric sine (fixed 530 d) plus Keplerian orbit, subtract pulsation, refit Keplerian by chi-square minimisation  
  > "The RV curve was fitted by a combination of two functions: a Keplerian orbit and an asymmetric sine" (3.1.1 Disentangling the pulsation (step 1)); "the cleaned signal is fitted with a Keplerian orbit alone using a $\chi^2$-minimisation." (3.1.1 Disentangling the pulsation (step 1))
   - software: python
   - parameter: Keplerian period limited to 6310 +/- 1220 d from the Lomb-Scargle periodogram of the light curve (3 sigma)  
  > "the asymmetric sine period was fixed at 530 d and the Keplerian period was forced to remain in the range 6310$\pm$1220 days." (3.1.1 Disentangling the pulsation (step 1))
   - parameter: Nine Barnbaum RVs added; extra 0.2 km/s uncertainty on HERMES RVs  
  > "an additional 0.2 $\rm km\,s^{-1}$ uncertainty is added to the RV data from HERMES" (3.1.1 Disentangling the pulsation (step 1))
   - assumption: Period imposed from the light curve  
  > "The method allows us to get precise orbital parameters at the price of imposing the period." (3.1.1 Disentangling the pulsation (step 1))
   - fitting: chi-square minimisation; parameter errors from square root of covariance diagonal  
  > "The standard deviations of the orbital parameters are obtained by computing the square root of the diagonal elements of the covariance matrix." (3.1.1 Disentangling the pulsation (step 1))
   - validation: Compared with the independent ORVARA solution  
  > "another independent method was used on the RV curve cleaned from the pulsation." (3.1.2 Orbital parameters with ORVARA (step 2))
3. **Fit full orbit with RV plus Hipparcos-Gaia astrometry**: ORVARA parallel-tempering MCMC fitting RV, proper motions and parallax simultaneously  
  > "uses a parallel tempering MCMC method to simultaneously fit radial-velocity and astrometric measurements." (3.1.2 Orbital parameters with ORVARA (step 2))
   - software: ORVARA
   - parameter: 15 temperatures, 100 walkers, 5e6 steps per walker  
  > "We used 15 MCMC temperatures and for each temperature, with 100 walkers run with 5 $\times10^6$ steps per walker." (3.1.2 Orbital parameters with ORVARA (step 2))
   - parameter: Primary mass Gaussian prior 1.9 +/- 1 Msun; Gaia DR3 parallax prior (434 +/- 21 pc); eccentricity prior e<0.15 added after bimodality  
  > "the primary mass was set as a Gaussian prior of 1.9 $\pm$1 $\rm M_{\odot}$" (3.1.2 Orbital parameters with ORVARA (step 2)); "We therefore re-started the MCMC with an additional prior on the eccentricity ($e<0.15$) to favour the orbital solution with the shorter period" (3.1.2 Orbital parameters with ORVARA (step 2))
   - assumption: Companion more massive than V Hya initial mass rejected as inconsistent with its evolutionary stage  
  > "Such a high mass ratio would imply a companion that is more massive than V Hya initial mass, which is inconsistent with its evolutionary stage." (3.1.2 Orbital parameters with ORVARA (step 2))
   - fitting: Parallel tempering MCMC; likelihood from RV and astrometric chi-square  
  > "taken as the sum of the $\chi^2$ for the Hipparcos proper motion ($\chi^2_{H}$), the Gaia proper motion ($\chi^2_{G}$), and the long-term Hipparcos-Gaia proper motion ($\chi^2_{HG}$)." (3.2 Astrometric-spectrometric orbit (step 2))
   - validation: PSRF convergence test; alternative distance priors; sensitivity test offsetting the Hipparcos mu_alpha point by +4,+2,-2,-4 mas/yr  
  > "The convergence of the chains was assessed by comparing the variance between chains with the variance within each single chain through the potential scale reduction factor (PSRF) estimator" (Appendix B Convergence study); "We conclude that the obtained orbital parameters are robust against the unreliable $\mu^H_{\alpha*}$ value." (3.3 Sensitivity with respect to the Hipparcos data)
4. **Test companion nature against the UV excess with an SED**: Superimpose Kurucz A0 spectrum plus 2700 K black body on UV to NIR photometry, reddened by interstellar and circumstellar (amorphous carbon) extinction  
  > "The AGB star was modelled by a black-body of 2700 K (inferred temperature from (cite: Knapp_LC_1999))" (3.4 Nature of the companion)
   - parameter: A0 star 9950 K, radius 1.5 Rsun, mass 2 Msun  
  > "The V Hya B spectrum was modelled as an A0 star with a temperature of 9950 K from Kurucz models" (3.4 Nature of the companion)
   - parameter: Photometric uncertainties set to 2 mag optical, 1 mag NIR  
  > "the uncertainties of the photometric data points have been set to 2 mag in the optical and 1 mag in the near-infrared." (3.4 Nature of the companion)
   - assumption: AV(interstellar) = 0.09 mag; amorphous carbon grains, MNR size distribution a^-3.5, 0.005 to 0.25 micron  
  > "The visual interstellar extinction was estimated to be $A_{V}$ = 0.09 mag" (3.4 Nature of the companion); "with their radius $a$ distributed following the standard MNR distribution ($dn/da = a^{-3.5}$, with $a_{min}$ = 0.005 $\mu$m and $a_{max}$ = 0.25 $\mu$m" (3.4 Nature of the companion)
   - fitting: _not stated_
   - validation: The A0 spectrum reproduces the GALEX NUV and FUV points  
  > "reproduces perfectly the GALEX photometric data in the NUV and FUV filters." (3.4 Nature of the companion)
5. **Compare RV signals with the AAVSO light curve**: Remove 17 yr trend from light curve via 530-d rolling mean; plot RV and light curve versus pulsation and orbital phase  
  > "the 17 yr signal was fitted by taking a 530-d rolling mean" (4.1 The pulsation cycle)
   - fitting: _not stated_
   - validation: _not stated_
6. **Analyse time variation of Na I, K I, C2 and H-alpha lines**: Plot spectra versus orbital phase and interpolate between phases; compare with a reference carbon star  
  > "the spectra are plotted as a function of the orbital phase and interpolated between the phases to obtain a smooth representation of the variation." (5.1 Sodium doublet)
   - fitting: _not stated_
   - validation: _not stated_
7. **Fit a conical stellar-jet model to the phase-resolved Na I D1 absorption**: Spatio-kinematic jet model with absorption plus re-scattering source term, fitted to the dynamic Na I spectrum in three steps  
  > "the general fitting procedure is a three-step process: first, the synthetic model spectrum is used to fit the stellar-jet model to the phase-dependent observations and to obtain the best-fitting absorbing jet." (6 Spatio-kinematic modelling of the outflow)
   - software: spatiokm
   - parameter: Fit over velocity range 0 to -250 km/s; ten free parameters with ranges in Table 3  
  > "to fit V Hya sodium spectral line over the range 0 to -250 $\rm km\,s^{-1}$" (6 Spatio-kinematic modelling of the outflow)
   - parameter: Template for unattenuated spectrum: X Tra, Doppler-shifted for orbit and modulated at 530 d  
  > "we used the high-resolution spectrum of the carbon star X Tra as template for the unattenuated spectrum." (6 Spatio-kinematic modelling of the outflow)
   - assumption: Inclination fixed in range from orbital analysis because of strong degeneracy with opening angle  
  > "we constrained the inclination angle" (6.1 Best-fit model)
   - assumption: Blue-shifted emission interpreted as re-scattering of V Hya light  
  > "We interpreted the blue-shifted emission as re-scattering of V Hya light in our line of sight." (6 Spatio-kinematic modelling of the outflow)
   - fitting: MCMC routine as in the cited jet-modelling approach; sampler settings, priors beyond ranges and likelihood not given  
  > "Their modelling approach consists in fitting the model spectral lines created by a parametric jet model to the phase-resolved H$\alpha$ profile using an MCMC routine." (6 Spatio-kinematic modelling of the outflow)
   - validation: Visual comparison of observed and modelled dynamic spectrum  
  > "It can be seen that the model reproduces the temporal modulation of the blue-shifted absorption quite well." (6.1 Best-fit model)
8. **Compare jet axis and line of nodes with ALMA 12CO(2-1) high-velocity emission**: Overlay the sky-projected jet axis and line of nodes on the ALMA high-velocity emission map and compare geometry and orientation  
  > "on the high-velocity emission obtained from ALMA observations (PI: Sahai R., Project ID: 2018.1.01113.S). Both geometry and orientation between the two structures match." (7.3 Connection to large-scale bipolar outflows)
   - parameter: Jet axis and line of nodes angle uncertainty +/-10 deg due to inclination degeneracy  
  > "The line of nodes and jet axis angle have an uncertainty of $\pm$10° due to the inclination degeneracy" (7.3 Connection to large-scale bipolar outflows)
   - assumption: Jet axis is perpendicular to the orbital plane  
  > "the jet axis (perpendicular to the orbital plane) points towards the east." (7.3 Connection to large-scale bipolar outflows)
   - fitting: _not stated_
   - validation: Independent observations agree qualitatively  
  > "This result is to be underlined as the two sets of observations, having entirely independent approaches, provide a complementary set of evidence for the system morphology." (7.3 Connection to large-scale bipolar outflows)

## Software

- **ORVARA** : Joint RV plus Hipparcos-Gaia astrometry orbit fit  
  > "The software package ORVARA, developed by (cite: orvara_2021AJ....162..186B), uses a parallel tempering MCMC method" (3.1.2 Orbital parameters with ORVARA (step 2))
- **spatiokm (spatio-kinematic jet modelling engine)** : Fit the conical jet model to the Na I D1 dynamic spectrum  
  > "freely available on <https://github.com/bollend/spatiokm>" (Footnote 4)
- **HERMES python pipeline** : Reduction of HERMES spectra  
  > "The dedicated python-based pipeline was used for the data reduction." (2.1 Spectroscopic data)
- **Numpy, Matplotlib, SciPy, Astropy** : General analysis and plotting  
  > "This research made use of Numpy, Matplotlib, SciPy and Astropy, a community-developed core Python package for Astronomy" (Acknowledgements)
- **Lomb-Scargle periodogram** : Period search in the AAVSO light curve  
  > "Figure [12](#fig:Lombscragle) displays the Lomb-Scargle periodogram of the AAVSO light curve" (Appendix A Light-curve periodogram)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Orbital period, RV-only fit | 17.22 | 0.92 | yr | 2 | 17.22$\pm$ 0.92 |
| Orbital period, RV plus astrometry (ORVARA) | 17.45 | +0.34/-0.29 | yr | 3 | ${17.45}_{-0.29}^{+0.34}$ |
| Eccentricity, RV-only | 0.02 | 0.02 | dimensionless | 2 | a low eccentricity ($e = 0.02\pm0.02$) |
| Orbital inclination (ORVARA) | 37.7 | +2.2/-2.0 | deg | 3 | ${37.7}_{-2.0}^{+2.2}$ |
| Companion mass M2 (ORVARA) | 2.63 | +0.63/-0.69 | Msun | 3 | ${2.63}_{-0.69}^{+0.63}$ |
| Mass function f(m) | 0.176 | 0.003 | Msun | 2 | 0.176 $\pm$ 0.003 |
| Pulsation asymmetric-sine amplitude | 5.18 | 0.18 | km/s | 2 | 5.18 $\pm$ 0.18 |
| Pulsation radial distance covered over half a period | 0.25 | not stated | au | 2 | $\Delta R$ = 0.25 au |
| Total visual extinction in SED model | 3.90 | not stated | mag | 4 | the total $A_{V}$ is 3.90 mag |
| Na I D2/D1 equivalent-width ratio | 0.8 to 1 | not stated | dimensionless | 6 | The ratio between D2 and D1 equivalent widths range from 0.8 to 1, for a spectral window of 2 Å. |
| Maximum blue-shifted Na I absorption velocity | -150 | not stated | km/s | 6 | reaches its maximum blue-shifted value, -150 $\rm km\,s^{-1}$ at phase 0.5 |
| Jet inclination (best fit) | 38.3 | 1.5 | deg | 7 | 38.3 $\pm$ 1.5 |
| Jet opening angle alpha | 62 | 2 | deg | 7 | 62 $\pm$ 2 |
| Jet cavity angle theta_cav | 6.9 | 2.5 | deg | 7 | 6.9$\pm$ 2.5 |
| Jet velocity on axis v0 | 194.7 | 20.5 | km/s | 7 | 194.7 $\pm$ 20.5 |
| Jet velocity at cone edge v_alpha | 26.4 | 9.0 | km/s | 7 | 26.4$\pm$ 9.0 |
| Stellar radius R1 in jet model | 2.19 | 0.16 | Rsun | 7 | 2.19$\pm$ 0.16 |

## Qualitative findings

- Minimum light always corresponds to superior conjunction, so obscuration occurs when the companion passes in front of V Hya  
  > "the minimum light found by the AAVSO monitoring always corresponds to the superior conjunction" (4.2 The 17-yr cycle)
- Jet axis and line of nodes match the orientation of the large-scale ALMA 12CO high-velocity structure  
  > "Both geometry and orientation between the two structures match." (7.3 Connection to large-scale bipolar outflows)
- Hollow cone with velocity gradient along its radial direction  
  > "The obtained jet model is described as a hollow cone with a wide opening angle and a velocity gradient along its radial direction." (8 Conclusion)

## Claim tuples

- H: The 17 yr periodic variation of V Hya is due to a binary companion | E: HERMES RV monitoring combined with Hipparcos-Gaia astrometry, fitted with a Keplerian plus pulsation model and ORVARA | R: Low-eccentricity orbit with period near 17 yr and inclination about 38 deg | F: The periodic variation is likely due to orbital motion | **supported**
- H: The obscuration event and alkaline-line absorption are tied to the companion passage | E: Compare RV orbit with AAVSO light curve and Na I and K I line variations versus orbital phase | R: Light-curve minima at superior conjunction; blue-shifted absorption varies with phase | F: The companion passage across the line of sight correlates with obscuration and blue-shifted absorption | **supported**
- H: A conical jet launched from the companion can reproduce the Na I line modulation | E: Spatio-kinematic jet model fitted to the phase-resolved Na I D1 dynamic spectrum | R: Best-fit hollow cone with wide opening angle reproduces the modulation of the blue-shifted absorption | F: A wide conical jet from the companion explains the line variations | **supported**
- H: The modelled jet orientation matches the large-scale CO bipolar outflow | E: Overlay the sky-projected jet axis and line of nodes on ALMA 12CO J=2-1 high-velocity emission | R: Geometry and orientation match | F: The modelled jet may be the innermost part of the large-scale parabolic structure | **supported**
- H: The companion is a hot main-sequence star able to explain the GALEX UV excess | E: SED with A0 Kurucz spectrum plus 2700 K black body for the AGB star, reddened | R: A0 spectrum reproduces the GALEX NUV and FUV photometry | F: The companion is likely a main-sequence star | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: The most generic jet model with fewest free parameters and fewest assumptions about the launch site was chosen  
  > "we choose the most generic model containing the smallest number of free parameters and assumptions about the launching site of the outflow." (6 Spatio-kinematic modelling of the outflow); "The choice of such a modelling tool was motivated by previous large-scale observations of high-velocity outflows" (6.2 Limitation of the model)
- Alternative: Simple eclipse by a stellar body rejected; a more extended opaque object attached to the companion is needed  
  > "Due to the particular shape of the eclipse, with a long duration and a deep obscuration, and the system inclination, a simple eclipsing scenario by a stellar body has to be rejected." (4.2 The 17-yr cycle)
- Alternative: Long secondary pulsation and episodic dust condensation considered less likely than the binary  
  > "we consider intrinsic variability scenarios to be less likely to explain the long-term periodicity of the star" (7.2 Origin of the long-period variability)
- How they decided it was enough: _not stated_
- Limitation (authors): Astrometric orbital parameters are indicative only and the direction of orbital motion is undetermined  
  > "derived from the astrometry as indicative, rather than precise" (3.3 Sensitivity with respect to the Hipparcos data)
- Limitation (authors): Exact launch site of the jet unknown; no direct evidence of companion motion in the spectrum  
  > "the exact launch site of the jet remains unknown." (6.2 Limitation of the model)
- Caveat (inferred, ours): The ALMA data play only a qualitative overlay role; no ALMA processing or quantitative position-angle comparison is given
- Caveat (inferred, ours): Hipparcos mu_alpha point is an outlier (VIM flag) and the inclination and ascending node depend on it
- Caveat (inferred, ours): Reduced chi-square of 13.65 and 14.0 indicate poor RV fit quality
- Caveat (inferred, ours): Jet fit has no stated priors, sampler settings or likelihood, and a fixed inclination
- Caveat (inferred, ours): Eccentricity prior e<0.15 was imposed to select the 17 yr solution

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: ORVARA is public (third-party code used); the spatiokm jet engine is freely available; authors own analysis scripts not stated as released  
  > "<https://github.com/t-brandt/orvara>" (Footnote 3); "freely available on <https://github.com/bollend/spatiokm>" (Footnote 4)
- Missing: ALMA calibration, imaging and the exact map used in the overlay
- Missing: Public availability statement for HERMES spectra
- Missing: MCMC settings, priors and likelihood of the jet fit
- Missing: Pulsation flux modulation of the X Tra template
- Data volume (inferred): Optical part: small (130 spectra plus tables). ALMA part: one archival 12CO(2-1) cube of project 2018.1.01113.S (size not estimated from the paper); overlay needs only the final image
- Score (inferred): 2/5, The orbit and jet analysis can be partly redone from published RV table and public codes, but HERMES spectra are not stated public and the ALMA overlay has no processing recipe.
- Rediscovery candidate: no, ALMA role is a qualitative comparison, the HERMES data availability is not stated, and the jet fit settings are incomplete.

## Links

- Method: (cite: orvara_2021AJ....162..186B) (ORVARA joint RV and astrometry orbit fitting)
- Method: (cite: Dylan2) (Spatio-kinematic jet modelling and radiative transfer implementation)
- Method: (cite: HERMES) (HERMES spectrograph and its reduction pipeline)
- Companion: (cite: Sahai_ALMA_2022ApJ...929...59S) (ALMA observations of V Hya from project 2018.1.01113.S showing high-velocity CO outflow and rings)
- Companion: (cite: VHya_MATISSE) (Companion interferometric study that could lift the inclination degeneracy)
- Related: ALMA project 2018.1.01113.S (PI: Sahai R.)

## Checks

```json
{
 "quotes": 101,
 "quotes_ok": 101,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 110,
  "stated": 64,
  "rate": 0.582
 },
 "evidence_ok": true
}
```
