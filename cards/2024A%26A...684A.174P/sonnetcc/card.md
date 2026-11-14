# High turbulence in the IM Lup protoplanetary disk. Direct observational constraints from CN and C<SUB>2</SUB>H emission

`2024A&A...684A.174P` | Astronomy and Astrophysics 2024 | first author: Paneque-Carreño, T. | arXiv: 2312.04618 | DOI: 10.1051/0004-6361/202347757

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Can turbulence in the IM Lup disk be measured directly, without radiative transfer or thermochemical models, from the nonthermal broadening of optically thin CN emission at a known vertical and radial location?  
  > "we present a new way of directly measuring turbulence without the need of radiative transfer or thermochemical models" (abstract); "By using an optically thin tracer, it is possible to directly measure turbulence from the nonthermal broadening of the line." (abstract)
- Target **IM Lup**: coordinates _not stated_; z/distance 158 pc  
  > "the protoplanetary disk around the young K5 star IM Lup, located at a distance of 158 pc (cite: Gaia_DR3)" (1 Introduction); distance from Gaia DR3 (cite: Gaia_DR3)  
  > "the protoplanetary disk around the young K5 star IM Lup, located at a distance of 158 pc (cite: Gaia_DR3)" (1 Introduction)

## Data provenance

- ALMA projects: 2019.1.01357.S
- bands: Band 7  
  > "New, higher-energy ALMA Band 7 transitions have sufficient S/N for an adequate characterization of their radial, azimuthal, and vertical features." (1 Introduction)
- frequencies and spectral setup: Native spectral resolution 50 m/s; analysis cubes with 200 m/s channels (C2H) and 100 m/s channels (CN)  
  > "The images used in the analysis where obtained using a channel spacing of 200 m s$^{-1}$ for C$_2$H and 100 m s$^{-1}$ for CN" (2 Observations); "stacked spectra for the data imaged at the native spectral resolution, 50 m s$^{-1}$" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Seven execution blocks: two short-baseline EBs (longest baseline 0.3 km) and five long-baseline EBs (maximum baseline 1.5 km)  
  > "The observations from each execution block (EB; seven in total) were aligned to a common phase center" (2 Observations); "Self-calibration was then applied to the short-baseline observations (two EBs, with a longest baseline of 0.3 km)." (2 Observations); "concatenated to the flux-calibrated long baselines (five EBs, with a maximum baseline of 1.5km)" (2 Observations)
- baselines: Short-baseline EBs: longest baseline 0.3 km; long-baseline EBs: maximum baseline 1.5 km  
  > "Self-calibration was then applied to the short-baseline observations (two EBs, with a longest baseline of 0.3 km)." (2 Observations); "concatenated to the flux-calibrated long baselines (five EBs, with a maximum baseline of 1.5km)" (2 Observations)
- angular resolution: C2H: 0.27'' x 0.25'' (PA 64.83 deg); CN: 0.22'' x 0.19'' (PA 57.56 deg)  
  > "resulting in a 0.27$\ensuremath{''} \times$ 0.25$\ensuremath{''}$ beam (PA: 64.83$^{\circ}$)" (2 Observations); "CN is imaged using a 0.5 robust parameter with a final beam of 0.22$\ensuremath{''} \times$ 0.19$\ensuremath{''}$ (PA: 57.56$^{\circ}$)" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: Final image rms 0.6 mJy/beam (C2H) and 1 mJy/beam (CN)  
  > "The final rms of the images for each molecule are 0.6 mJy/beam and 1 mJy/beam for C$_2$H and CN, respectively." (2 Observations)
- time on source: _not stated_
- observing dates: Second semester of 2019 and first semester of 2021  
  > "taken during the second semester of 2019 and first semester of 2021" (2 Observations)
- pi or archival as stated: Project 2019.1.01357.S, PI R. Teague (not described as archival)  
  > "Project code: #2019.1.01357.S, PI: R.Teague" (2 Observations)
- Line: CN N=3-2, J=5/2-3/2, F=7/2-5/2 (strongest unblended component, used for the vertical profile and DISCMINER fit) (340.03155 GHz)
- Line: CN N=3-2, J=7/2-5/2 hyperfine group (F=7/2-5/2, 9/2-7/2, 5/2-3/2 and weaker components) (340.24759-340.26495 GHz)
- Line: C2H N=4-3, J=9/2-7/2 (F=5-4, 4-3) and J=7/2-5/2 (F=4-3, 3-2) hyperfine groups (349.33771-349.40067 GHz)
- Other facility **MAPS (ALMA large program) CO isotopolog data**: Optically thick 13CO and 12CO brightness temperatures and C18O J=2-1 data used as kinetic temperature tracers and for comparison  
  > "to match the resolution of the Molecules with ALMA at Planet-forming Scales (MAPS) Program data (cite: MAPS_Oberg)" (3.2 Brightness temperature); "we repeated our analysis on C$^{18}$O $J=2-1$ data from the MAPS program (cite: MAPS_Oberg)" (6.2 Origin of high turbulence in IM Lup)
- Other facility **Gaia DR3**: Distance to IM Lup (158 pc)  
  > "located at a distance of 158 pc (cite: Gaia_DR3)" (1 Introduction)
- External data: Vertical emission surfaces of CO isotopologs in IM Lup, used to compare with CN and C2H heights and brightness temperature profiles  
  > "Comparison with previously studied CO isotopolog emission from IM Lup (cite: Paneque_2023_vert) is presented in Figure" (3.1 Vertical profile) [from Paneque-Carreno et al. 2023 (cite: Paneque_2023_vert)]
- External data: Stellar mass of 1.1 Msun used for the Keplerian masks  
  > "A stellar mass of 1.1M$_\odot$ (cite: MAPS_Teague)" (2 Observations) [from Teague et al. 2021 (cite: MAPS_Teague)]
- External data: CN molecular mass m_X = 26.0 used in the thermal linewidth  
  > "in this case, for CN, $m_X$ = 26.0 (cite: Klisch_1995_CN; lambda_database_Schoier_2005)" (5 Turbulence as traced by CN) [from Klisch et al. 1995 (cite: Klisch_1995_CN); Schoier et al. 2005 (cite: lambda_database_Schoier_2005)]
- External data: Excitation temperature of 21 K for C18O gas assumed in the comparison analysis  
  > "previous works have assumed an excitation temperature of 21 K for the C$^{18}$O gas (cite: Pinte_2018_method; Paneque-Carreno_2022_Elias_CN)" (6.2 Origin of high turbulence in IM Lup) [from Pinte et al. 2018a (cite: Pinte_2018_method); Paneque-Carreno et al. 2022 (cite: Paneque-Carreno_2022_Elias_CN)]
- External data: Turbulence of Mach 0.18-0.3 from radiative transfer modelling of CO isotopologs in IM Lup, used as comparison  
  > "results in high nonthermal motions associated with turbulence of $\mathcal{M}$ = 0.18-0.3 (Flaherty et al. in prep)" (6.4 Comparison with other methods and results) [from Flaherty et al. in prep]
- Simulation/model as data: Thermochemical model gas temperatures of IM Lup used to check that CO brightness temperatures are not underestimated  
  > "We confirmed this by comparing our temperature profiles to the gas temperature from dedicated thermochemical models of IM Lup (cite: Cleeves_LupusModel_2016)" (6.3 Possible overestimation of the nonthermal component)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline initial calibration, then manual flux scaling and self-calibration in CASA  
  > "After initial calibration through the ALMA pipeline (cite: Hunter_2023_ALMA_pipeline), the data were flux-calibrated and self-calibrated in phase and amplitude" (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: Relative flux scale variations between EBs <10%, corrected by amplitude scaling following DSHARP  
  > "an amplitude scaling was applied to correct for the relative flux scale variations between EBs, which were $<$10%" (2 Observations)
- self calibration: Short baselines: 5 phase rounds + 1 amplitude round, starting solint 3360 s, halving each round (S/N 190 to 1380). Joint dataset: 3 phase + 1 amplitude rounds, initial solint 4800 s (S/N 301 to 1289). Done on line-free channels, solutions applied to the whole dataset  
  > "Five rounds of phase and one round of amplitude calibration were performed, until there was no further improvement of the S/N, starting with a solution interval of 3360s" (2 Observations); "Three rounds of phase and one round of amplitude calibration were performed, the initial time solution interval was 4800s" (2 Observations); "Each of the calibration solutions from the continuum analysis was then applied to the whole dataset" (2 Observations)

### Imaging

- task: CASA tclean with Briggs weighting and Keplerian masking, one image per hyperfine group  
  > "Each C$_2$H and CN hyperfine group was imaged using tclean with Briggs weighting and Keplerian masking" (2 Observations)
- deconvolver: _not stated_
- weighting robust: robust = 2.0 (C2H); robust = 0.5 (CN)  
  > "C$_2$H emission was imaged using a robust parameter of 2.0" (2 Observations); "CN is imaged using a 0.5 robust parameter" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian masks, one per expected hyperfine component; M* = 1.1 Msun, constant z/r = 0.2 (C2H) and 0.3 (CN)  
  > "Multiple Keplerian masks, one for each of the expected hyperfine components, were used in the cleaning." (2 Observations); "a constant $z/r$ value of 0.2 and 0.3 was used for C$_2$H and CN emission, respectively" (2 Observations)
- multiscale scales: _not stated_
- continuum subtraction: CASA uvcontsub, producing continuum-subtracted measurement sets per target line  
  > "Using the CASA task uvcontsub, we produced continuum-subtracted measurement sets for each of our target emission lines." (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Self-calibrated short baselines concatenated with the flux-calibrated long baselines  
  > "concatenated to the flux-calibrated long baselines (five EBs, with a maximum baseline of 1.5km)" (2 Observations)
- smoothing: _not stated_
- final beam: C2H 0.27'' x 0.25'' (PA 64.83 deg); CN 0.22'' x 0.19'' (PA 57.56 deg)  
  > "resulting in a 0.27$\ensuremath{''} \times$ 0.25$\ensuremath{''}$ beam (PA: 64.83$^{\circ}$)" (2 Observations); "CN is imaged using a 0.5 robust parameter with a final beam of 0.22$\ensuremath{''} \times$ 0.19$\ensuremath{''}$ (PA: 57.56$^{\circ}$)" (2 Observations)
- final rms: 0.6 mJy/beam (C2H), 1 mJy/beam (CN)  
  > "The final rms of the images for each molecule are 0.6 mJy/beam and 1 mJy/beam for C$_2$H and CN, respectively." (2 Observations)

### Inherited from earlier work

- Amplitude scaling between EBs follows the DSHARP procedures  
  > "following the procedures of ALMA large program DSHARP (cite: DSHARP_Andrews)" (2 Observations) [from ALMA large program DSHARP (cite: DSHARP_Andrews)]
- JvM correction applied to final images (epsilon 0.24 for C2H, 0.52 for CN)  
  > "JvM correction (cite: MAPS_Czekala) was applied to our final images to account for the noise caused by having non-Gaussian beams." (2 Observations) [from (cite: MAPS_Czekala)]
- Two-Gaussian fit to the radial intensity profiles (broad component plus ring)  
  > "a set of two Gaussians are fitted to the radial profiles as done in (cite: MAPS_Law_radial)" (Appendix A) [from (cite: MAPS_Law_radial)]
- Radial profile deprojection using only a 60 degree wedge along the semimajor axis  
  > "Only emission from within a 60$^{\circ}$ wedge along the semimajor axis is considered, to avoid deprojection effects from emission close to the minor axis (cite: MAPS_Law_radial)." (Appendix A) [from (cite: MAPS_Law_radial)]
- Exponentially tapered power-law parametrisation of the emission surface  
  > "The resulting vertical distribution is parametrized with an exponentially tapered power law to capture the inner flared surface, plateau and turnover regions at larger radii (cite: Teague_2019_meridonial)" (3.1 Vertical profile) [from (cite: Teague_2019_meridonial)]

### Not stated but needed to reproduce (our reading)

- CASA version and ALMA pipeline version used
- Names and spectral windows of the line-free channels used for self-calibration and for uvcontsub, and the continuum-subtraction fit order
- Cell size, image size, tclean deconvolver/threshold/niter, mask widths for the Keplerian masks, and primary-beam correction
- Self-calibration solution interval for each round after the first beyond 'half the time step', gain types and combine/spw-map settings
- ALFAHOR mask definitions (visually drawn) and which channels were selected
- emcee settings for the surface fit (priors, walkers, steps, likelihood and error model)
- DISCMINER setup: priors, optimizer/sampler, initial guesses, fitting region (radial limits, mask), noise model, and the velocity range of the cut-out CN cube
- How the radial CO brightness temperature profile was converted to a kinetic temperature at the CN radius (which CO cube, averaging, beam matching)
- Value of mean molecular weight mu used for the sound speed
- Details of the linewidth measurement from per-pixel spectra shown in Figure 6 (method for line fitting)

## Analysis recipe

1. **Calibrate, self-calibrate and image the CN and C2H lines**: Pipeline calibration, EB alignment on continuum peak (imfit), amplitude scaling, phase and amplitude self-calibration on line-free continuum, solutions applied to line data, uvcontsub, tclean per hyperfine group with Keplerian masks, JvM correction  
  > "considering the peak of the continuum emission of each EB as fitted by CASA task imfit" (2 Observations); "Using the CASA task uvcontsub, we produced continuum-subtracted measurement sets for each of our target emission lines." (2 Observations)
   - software: CASA, tclean, uvcontsub, imfit, ALMA pipeline, keplerian_mask
   - parameter: robust = 2.0 (C2H), 0.5 (CN); channel spacing 200 m/s (C2H), 100 m/s (CN)  
  > "C$_2$H emission was imaged using a robust parameter of 2.0" (2 Observations); "CN is imaged using a 0.5 robust parameter" (2 Observations)
   - fitting: _not stated_
   - validation: Self-calibration rounds continued until no further improvement of the S/N  
  > "until there was no further improvement of the S/N" (2 Observations)
2. **Trace the vertical emission surfaces of CN and C2H**: Emission maxima on the near and far sides traced from channel maps with ALFAHOR inside visually defined masks, then fitted with an exponentially tapered power law using MCMC; only the strongest unblended CN component and the C2H J=9/2-7/2 group used  
  > "we used the code ALFAHOR (cite: Paneque_2023_vert), which traces the maxima of emission within a given masked region" (3.1 Vertical profile); "The best-fit values for $z_0$, $\phi$, $\psi,$ and $r_{\mathrm{taper}}$ were found using a Markov chain Monte Carlo sampler as implemented by emcee (cite: emcee_ref)" (3.1 Vertical profile)
   - software: ALFAHOR, emcee
   - parameter: Free parameters z0, phi, r_taper, psi of an exponentially tapered power law in r/100 au  
  > "The resulting vertical distribution is parametrized with an exponentially tapered power law" (3.1 Vertical profile)
   - assumption: Intensity maxima trace a single isovelocity along each channel; the selected component is representative of all transitions of the molecule  
  > "A key assumption of this method is that the intensity maxima trace a single isovelocity along each channel." (3.1 Vertical profile); "We expect that these transitions are representative of the spatial location of all the detected transitions of the same molecule" (3.1 Vertical profile)
   - fitting: emcee MCMC; priors and likelihood not stated  
  > "using a Markov chain Monte Carlo sampler as implemented by emcee (cite: emcee_ref)" (3.1 Vertical profile)
   - validation: Compared with CO isotopolog surfaces and with the z/r ~0.2 expected from the visual channel map analysis  
  > "our result on the average vertical profile (panel C of Fig. [3](#best_fit_heights)) is consistent with $z/r \sim$0.2 expected from the visual channel map analysis" (3.1 Vertical profile)
3. **Measure peak brightness temperature profiles and compare with CO isotopologs**: Peak intensity (moment 8) maps converted to brightness temperature with Planck's law, deprojected on the best-fit surfaces, using cubes at 0.2 km/s resolution to match MAPS  
  > "the radial peak brightness temperature profiles were extracted from the peak intensity maps (moment 8)" (3.2 Brightness temperature); "all brightness temperature profiles were calculated using cubes with an equal spectral resolution of 0.2 km s$^{-1}$" (3.2 Brightness temperature)
   - parameter: Spectral resolution 0.2 km/s for all tracers  
  > "all brightness temperature profiles were calculated using cubes with an equal spectral resolution of 0.2 km s$^{-1}$" (3.2 Brightness temperature)
   - assumption: 12CO and 13CO are optically thick so their brightness temperature traces the kinetic temperature; CN and C2H are optically thin  
  > "therefore their brightness temperature may be taken as a tracer of the kinetic temperature in the region" (3.2 Brightness temperature)
   - fitting: _not stated_
   - validation: CN and C2H brightness temperatures lower than 13CO, consistent with optically thin emission  
  > "which is corroborated by the lower brightness temperatures measured in this work" (3.2 Brightness temperature)
4. **Fit a parametric DISCMINER model to CN to extract the linewidth**: DISCMINER model with Gaussian line kernel for upper and lower surfaces, exponentially tapered power-law surfaces, power-law plus Gaussian peak intensity, power-law linewidth, fitted to per-pixel spectra of a cube covering only the unblended CN J=5/2-3/2 F=7/2-5/2 component  
  > "Therefore, we used a Gaussian kernel for each surface such that" (4.1 Model setup); "we created a cube that only covers the emission of the strongest unblended hyperfine component of CN 3-2, J = 5/2 - 3/2 F= 7/2-5/2" (4.1 Model setup)
   - software: DISCMINER
   - parameter: Linewidth Delta V = L0 (R/D0)^p (z/D0)^q with D0 = 100 au; best fit L0 = 0.415 km/s, p = -0.205, q = -0.238  
  > "$D_0$ = 100 au is a normalization factor" (Table 2); "0.415" (Table 3)
   - assumption: Optically thin emission, so the model intensity is the direct sum of upper and lower surface contributions  
  > "Since we assumed fully optically thin emission, the final model intensity is given by the direct sum of the upper and lower disk surface intensity contributions" (4.1 Model setup)
   - fitting: Best fit parameters of orientation, velocity, surface, intensity and linewidth found by DISCMINER; sampler, priors and likelihood not stated  
  > "DISCMINER determines the best orientation, velocity, surface and line profile parameters for the observed emission" (4.1 Model setup)
   - validation: Model channel maps convolved with the beam; 5 sigma residuals show no coherent pattern; comparison of vertical and azimuthally averaged profiles  
  > "The 5$\sigma$ residuals are presented in the bottom row, no coherent or systematic pattern is identified." (4.2 Comparison to CN observations)
5. **Separate thermal and nonthermal linewidth and derive turbulence**: Delta V^2 = 2kT_kin/m_X + v_turb^2 with T_kin taken from 13CO and 12CO brightness temperatures, Mach number = v_turb/(sqrt2 c_s), alpha ~ Mach^2  
  > "Therefore, the two components of the measured linewidth can be decomposed as" (5 Turbulence as traced by CN); "it is possible to relate the turbulence Mach number $\mathcal{M}$ to $\alpha$ following, $\alpha \sim \mathcal{M}^{2}$" (5 Turbulence as traced by CN)
   - parameter: CN molecular mass 26.0; uncertainty band from a 50 m/s linewidth error; only radii beyond 150 au considered  
  > "The shaded regions of the plot represent the variation of our results considering a 50 m s$^{-1}$ error in the linewidth measurement." (5 Turbulence as traced by CN); "we only considered the values beyond 150 au as accurate measurements" (5 Turbulence as traced by CN)
   - assumption: Nonthermal broadening is entirely turbulent; CN emits at the kinetic temperature traced by optically thick CO at the same location  
  > "The nonthermal broadening is assumed to be completely due to turbulence" (5 Turbulence as traced by CN); "By spatially localizing the CN emission vertically and radially close to the optically thick CO isotopes" (5 Turbulence as traced by CN)
   - fitting: _not stated_
   - validation: Statistical fit error <5 m/s; a 50 m/s error adopted as the largest possible deviation (native resolution, Hanning smoothing)  
  > "While the statistical error of our fit is $<$5 m s$^{-1}$, we took the native resolution of our data as the largest possible deviation" (5 Turbulence as traced by CN)
6. **Test robustness: opacity, vertical layer width, C18O comparison**: Estimated opacity broadening contribution, computed Keplerian shear broadening for CN layers of different vertical width along the line of sight (sampled every 1 au), and repeated the analysis on MAPS C18O J=2-1  
  > "to be sensitive to these variations, we sampled the line-of-sight path every 1 au" (Appendix D); "we repeated our analysis on C$^{18}$O $J=2-1$ data from the MAPS program (cite: MAPS_Oberg)" (6.2 Origin of high turbulence in IM Lup)
   - parameter: Vertical widths up to 50 au give linewidth variation <=25 m/s beyond 150 au  
  > "the variation in the linewidth caused by vertical widths of up to 50 au is always $\leq$25 m s$^{-1}$" (6.3 Possible overestimation of the nonthermal component)
   - assumption: Constant intrinsic thermal linewidth across the layer; CN layer lower edge at the best-fit CN surface  
  > "we assumed a constant intrinsic thermal linewidth in the Gaussian profiles for our estimation" (Appendix D)
   - fitting: _not stated_
   - validation: All C18O-based turbulence profiles are comparable to CN within uncertainty  
  > "all profiles are comparable within their uncertainty" (6.2 Origin of high turbulence in IM Lup)

## Software

- **CASA** : Imaging (tclean), imfit, uvcontsub, self-calibration  
  > "with the tools of Common Astronomy Software Applications (cite: McMullin_CASA)" (2 Observations)
- **ALMA pipeline** : Initial calibration  
  > "After initial calibration through the ALMA pipeline (cite: Hunter_2023_ALMA_pipeline)" (2 Observations)
- **keplerian_mask** : Keplerian masking in tclean  
  > "https://github.com/richteague/keplerian_mask" (Footnote 1)
- **GoFish** : Integrated spectra and radial intensity profiles  
  > "The spectra were computed using the GoFish (cite: gofish) function, integrated_spectrum, over the whole disk." (2 Observations)
- **ALFAHOR** : Tracing emission maxima to obtain vertical profiles from channel maps  
  > "we used the code ALFAHOR (cite: Paneque_2023_vert), which traces the maxima of emission within a given masked region" (3.1 Vertical profile)
- **emcee** : MCMC fit of the vertical surface parameters  
  > "using a Markov chain Monte Carlo sampler as implemented by emcee (cite: emcee_ref)" (3.1 Vertical profile)
- **DISCMINER** : Parametric model fit to CN spectra to extract the linewidth  
  > "To this end, we used DISCMINER (cite: izquierdo_2021_discminer1), which allowed us to find the best-fit parametrization of our emission." (4 Parametric emission model: DISCMINER fit)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CN emission surface z0 (tapered power law) | 40.29 | +12.36/-13.87 | au | 2 | 40.29 $^{+12.36}_{-13.87}$ |
| C2H emission surface z0 (tapered power law) | 8.03 | +4.79/-3.33 | au | 2 | 8.03 $^{+4.79}_{-3.33}$ |
| CN surface power-law index phi | 4.91 | +0.22/-0.38 | dimensionless | 2 | 4.91 $^{+0.22}_{-0.38}$ |
| CN surface taper radius r_taper | 65.72 | +26.77/-11.49 | au | 2 | 65.72 $^{+26.77}_{-11.49}$ |
| Radial extent of CN and C2H emission at z/r = 0.2-0.3 | z/r = 0.2-0.3, radially between 50 and 350 au | not stated | dimensionless (z/r), au | 2 | at $z/r=$0.2-0.3 constrained radially between 50 and 350 au |
| Ring peak radius in CN and C2H integrated intensity | ~106 | not stated | au | 0 | all tracers display a ringed structure peaking at $\sim$106 au |
| DISCMINER best-fit stellar mass (CN) | 1.22 | not stated | Msun | 4 | 1.22 |
| DISCMINER best-fit inclination (CN) | 50.53 | not stated | degrees | 4 | 50.53 |
| DISCMINER best-fit position angle (CN) | 143.76 | not stated | degrees | 4 | 143.76 |
| DISCMINER best-fit systemic velocity (CN) | 4.49 | not stated | km/s | 4 | 4.49 |
| Average total CN linewidth outward of 150 au | ~221 | 50 m/s adopted systematic error | m/s | 4 | The average total linewidth measured outward of 150 au is $\sim$221 m s$^{-1}$. |
| Thermal broadening outward of 150 au (13CO and 12CO temperatures) | 105-132 | not stated | m/s | 5 | Thermal broadening only accounts for 105-132 m s$^{-1}$ |
| Nonthermal broadening outward of 150 au | 177-194 | not stated | m/s | 5 | the nonthermal broadening ranges between 177 and 194 m s$^{-1}$ |
| Turbulence Mach number beyond ~150 au at z/r ~0.25 | 0.4-0.6 | shaded band from 50 m/s linewidth error | dimensionless | 5 | IM Lup shows a high turbulence of Mach 0.4-0.6 |
| Turbulence alpha | ~10^-1 | not stated | dimensionless | 5 | Our measurements indicate $\alpha \sim 10^{-1}$. |
| Integrated flux of CN J=5/2-3/2 F=7/2-5/2 line | 1.594 | 0.001 | Jy km/s | 1 | 1.594 |
| Average ring width in CN and C2H | ~89 (CN), ~109 (C2H) | not stated | au | 0 | Overall the feature shows an average width of $\sim$89 au in CN and $\sim$109 au in C$_2$H. |

## Qualitative findings

- CN and C2H emit from a localized upper disk layer at z/r = 0.2-0.3, CN comparable to 13CO and C2H comparable to C18O, in agreement with thermochemical models  
  > "CN and C$_2$H are both emitting from a localized upper disk region at $z/r =$0.2-0.3, in agreement with thermochemical models." (abstract)
- No coherent non-Keplerian pattern except a radially localized rotation residual near 220 au  
  > "There are no immediate signs of non-Keplerian motion" (6.3 Possible overestimation of the nonthermal component)

## Claim tuples

- H: Turbulence can be measured directly from an optically thin tracer without radiative transfer models | E: Located CN emission surface, took CO brightness temperature as kinetic temperature, fitted linewidth with DISCMINER and separated thermal and nonthermal parts | R: Total linewidth ~221 m/s, thermal 105-132 m/s, nonthermal 177-194 m/s | F: Direct turbulence profile obtained for CN beyond 150 au | **supported**
- H: IM Lup has high turbulence in its upper disk layers | E: Mach number from the CN nonthermal linewidth at z/r ~0.25 beyond 150 au | R: Mach 0.4-0.6, alpha ~10^-1 | F: Strong turbulence in the upper layers of IM Lup | **supported**
- H: There is a vertical gradient of turbulence in IM Lup | E: Compared the CN-based upper-layer turbulence with literature constraints of low midplane turbulence from dust | R: High turbulence in the upper layer versus alpha ~10^-3 near the midplane from dust modelling | F: Evidence for higher turbulence in the upper layers, a key MRI prediction | **partially**
- H: CN and C2H trace a vertically elevated layer similar to 13CO | E: Traced emission maxima in channel maps with ALFAHOR and fitted tapered power laws | R: CN comparable to 13CO, C2H slightly below tracing the same region as C18O | F: First observational evidence of vertically elevated C2H in the outer disk | **supported**

## Reasoning

- Why this data: Higher-energy Band 7 CN and C2H transitions have enough S/N to measure vertical profiles that earlier lower transitions could not provide  
  > "previous studies have been unable to extract CN or C$_2$H vertical profiles due the low signal-to-noise ratio (S/N) of the lower rotational transitions" (1 Introduction)
- Why this method: Optically thin emission allows nonthermal broadening to be read directly, while a parametric model is needed to account for elevated surfaces, upper and lower sides and beam convolution  
  > "Extracting the linewidth is not straightforward, it requires a parametric model that accounts for the vertically elevated emission" (4 Parametric emission model: DISCMINER fit)
- Alternative: Analysis of the other CN hyperfine components and of C2H in DISCMINER rejected because of blending and low S/N  
  > "DISCMINER is not built to fit emission with multiple hyperfine components" (4.1 Model setup)
- Alternative: Photo-evaporative wind broadening not included because no sign of winds in the spectra or image plane  
  > "as we do not detect any indication of them in the spectra or image plane, we did not include this uncertainty in our analysis" (6.3 Possible overestimation of the nonthermal component)
- How they decided it was enough: Self-calibration iterated until the S/N stopped improving; a 50 m/s linewidth error adopted as the largest plausible deviation  
  > "until there was no further improvement of the S/N" (2 Observations)
- Limitation (authors): The vertical width of the CN layer cannot be estimated with the current analysis  
  > "It is not possible to estimate the vertical width of the CN emission with our current analysis" (6.3 Possible overestimation of the nonthermal component)
- Limitation (authors): Turbulence differs by a factor of 2 from radiative transfer results, with only one system available to compare methods  
  > "With only one system where it is possible compare both methods, we are not able to conclude if this is a systematic difference" (6.4 Comparison with other methods and results)
- Limitation (authors): Linewidth values inward of 150 au are unreliable because of overlapping velocities  
  > "therefore, we only considered the values beyond 150 au as accurate measurements" (5 Turbulence as traced by CN)
- Caveat (inferred, ours): Kinetic temperature taken from CO brightness temperature at a surface that is only comparable to, not identical with, the CN surface; temperature error not propagated
- Caveat (inferred, ours): Turbulence rests on a single IM Lup CN component with one DISCMINER fit and a fixed 50 m/s error rather than a posterior
- Caveat (inferred, ours): Nonthermal term assumed fully turbulent; opacity, wind and unresolved vertical extent only partly excluded
- Caveat (inferred, ours): Factor of 2 offset from the radiative transfer result is unexplained

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: keplerian_mask code on GitHub (used for masking); no release of the analysis scripts stated  
  > "https://github.com/richteague/keplerian_mask" (Footnote 1)
- Missing: DISCMINER priors, optimizer settings, fit region and exact cube cut
- Missing: Line-free channel selection, cell/image sizes and CLEAN thresholds
- Missing: CASA and pipeline versions
- Missing: Procedure for the per-pixel linewidth and the temperature profile used for T_kin
- Data volume (inferred): Seven EBs of Band 7 line data (about tens of GB raw, a few GB after averaging); cubes at 50-200 m/s resolution
- Score (inferred): 3/5, Project code and the imaging, self-calibration and DISCMINER parametrisation are described and key numbers tabulated, but data availability is not stated and the fit settings, line-free channels and temperature handling are missing.
- Rediscovery candidate: no, The paper does not state that the data are public and several essential fit and imaging settings are missing, so the Mach number result could not be redone from the text alone.

## Links

- Method: Izquierdo et al. 2021 (cite: izquierdo_2021_discminer1) (DISCMINER method)
- Method: Izquierdo et al. 2023 (cite: Izquierdo_2023_discminer2) (DISCMINER application and extension)
- Method: Paneque-Carreno et al. 2023 (cite: Paneque_2023_vert) (ALFAHOR emission surface extraction and CO isotopolog surfaces)
- Method: Hacar et al. 2016 (cite: Hacar_2016_optdepth) (Opacity and nonthermal broadening of optically thin lines)
- Method: Czekala et al. 2021 (cite: MAPS_Czekala) (JvM correction)
- Method: Andrews et al. 2018 (cite: DSHARP_Andrews) (Amplitude scaling procedure between EBs)
- Companion: Oberg et al. 2021 (cite: MAPS_Oberg) (MAPS CO isotopolog data used for temperatures and C18O comparison)
- Companion: Cleeves et al. 2016 (cite: Cleeves_LupusModel_2016) (Thermochemical model of IM Lup)
- Companion: Bosman et al. 2023 (cite: Bosman_2023_imlup) (Proposed inner turbulent disk in IM Lup)
- Related: MAPS
- Related: DSHARP
- Related: ALMA project 2019.1.01357.S

## Checks

```json
{
 "quotes": 132,
 "quotes_ok": 132,
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
  "facts": 100,
  "stated": 77,
  "rate": 0.77
 },
 "evidence_ok": true
}
```
