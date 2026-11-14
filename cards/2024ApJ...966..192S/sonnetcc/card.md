# Multiple Outflows around a Single Protostar IRAS 15398−3359

`2024ApJ...966..192S` | The Astrophysical Journal 2024 | first author: Sai, Jinshi | arXiv: 2403.10857 | DOI: 10.3847/1538-4357/ad34b7

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Are there additional, misaligned outflows around the single Class 0 protostar IRAS 15398, and what causes the multiple outflow directions (turbulence vs magnetic-field misalignment)?  
  > "In this paper, we report the discovery of a third outflow around IRAS 15398, which is misaligned with the known primary and secondary outflows, and discuss the possible origins of the misaligned, multiple outflows." (Introduction)
- Target **IRAS 15398-3359 (Class 0 protostar, Lupus I)**: coordinates RA, Dec (J2000) = 15:43:02.24, -34:09:06.8 (cite: Yen:2017aa)  
  > "We adopted the source position of ($\alpha_\mathrm{J2000}$, $\delta_\mathrm{J2000}$)$=$(15:43:02.24, $-34$:09:06.8)" (ACA 7-m array Observations); "at a distance of $155~\pc$ (cite: Zucker:2020aa; Santamaria-Miranda:2021aa; Thieme:2023aa)" (Introduction); z/distance 155 pc  
  > "We adopted the source position of ($\alpha_\mathrm{J2000}$, $\delta_\mathrm{J2000}$)$=$(15:43:02.24, $-34$:09:06.8)" (ACA 7-m array Observations); "at a distance of $155~\pc$ (cite: Zucker:2020aa; Santamaria-Miranda:2021aa; Thieme:2023aa)" (Introduction); distance from (cite: Zucker:2020aa; Santamaria-Miranda:2021aa; Thieme:2023aa)  
  > "We adopted the source position of ($\alpha_\mathrm{J2000}$, $\delta_\mathrm{J2000}$)$=$(15:43:02.24, $-34$:09:06.8)" (ACA 7-m array Observations); "at a distance of $155~\pc$ (cite: Zucker:2020aa; Santamaria-Miranda:2021aa; Thieme:2023aa)" (Introduction)

## Data provenance

- ALMA projects: 2019.1.01063.S
- bands: Band 6  
  > "on 2019 December 19 during ALMA Cycle 7 with 10 antennae in Band 6." (ACA 7-m array Observations)
- frequencies and spectral setup: CO J=2-1 (230.538000 GHz); one FDM spectral window, 62.5 MHz bandwidth, 61.0 kHz resolution, ~0.080 km/s velocity resolution  
  > "The observations were carried out in the frequency division mode (FDM)." (ACA 7-m array Observations); "A spectral window with a bandwidth of 62.5 MHz and a spectral resolution of 61.0 kHz was assigned to the CO" (ACA 7-m array Observations); "which provided a velocity resolution of $\sim$0.080 $\kmps$." (ACA 7-m array Observations)
- continuum bandwidth: _not stated_
- arrays: ACA 7-m array, 10 antennae, mosaic of 28 pointings covering ~2' square  
  > "using the 7-m array of Atacama Compact Array (ACA) on 2019 December 19 during ALMA Cycle 7 with 10 antennae in Band 6." (ACA 7-m array Observations); "The mosaic observations with 28 pointings covered" (ACA 7-m array Observations)
- configurations: _not stated_
- baselines: 6.5 to 37 k-lambda at 230 GHz (projected)  
  > "The projected baseline lengths ranged from 6.5 to 37 k$\lambda$ at 230 GHz." (ACA 7-m array Observations)
- angular resolution: 7.7'' x 4.1'' (PA 87 deg)  
  > "The angular resolution and root-mean-square (rms) noise level are $7.7\ensuremath{''}\times 4.1\ensuremath{''}$ (87$^\circ$) and $0.13~\jypbm$, respectively." (ACA 7-m array Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 0.13 Jy/beam (final 0.16 km/s cube)  
  > "The angular resolution and root-mean-square (rms) noise level are $7.7\ensuremath{''}\times 4.1\ensuremath{''}$ (87$^\circ$) and $0.13~\jypbm$, respectively." (ACA 7-m array Observations)
- time on source: _not stated_
- observing dates: 2019 December 19  
  > "on 2019 December 19 during ALMA Cycle 7" (ACA 7-m array Observations)
- pi or archival as stated: Authors' own observations ('We have conducted mosaic observations')  
  > "We have conducted mosaic observations of IRAS 15398 using the 7-m array" (ACA 7-m array Observations)
- Line: CO J=2-1 (230.538000 GHz)
- Other facility **JCMT (850 micron continuum)**: 850 micron flux (2.9 Jy) and 3-sigma core radius used for the core mass; from the in-preparation eDisk paper  
  > "The core mass is estimated from the JCMT $850~\ensuremath{\mu}m$ flux, which is presented by (cite: Yen:inprep)" (5.2.1 Turbulence Scenario)
- Other facility **SOFIA**: Magnetic field orientation on ~9000 au scales, mean position angle ~225 deg (previous work)  
  > "providing a mean position angle of the magnetic field is $\rtsim225^\circ$ (cite: Redaelli:2019aa)" (5.2.2 Misalignment Scenario)
- External data: JCMT 850 micron flux and 3-sigma core radius of the IRAS 15398 core (F = 2.9 Jy; R_core = 6700+-800 au)  
  > "The core mass is estimated from the JCMT $850~\ensuremath{\mu}m$ flux, which is presented by (cite: Yen:inprep)" (5.2.1 Turbulence Scenario) [from (cite: Yen:inprep)]
- External data: C18O J=2-1 2' square map of IRAS 15398 used to measure turbulent velocity  
  > "presented by (cite: Sai:2023aa) to measure the turbulent velocity in two ways." (5.2.1 Turbulence Scenario) [from (cite: Sai:2023aa)]
- External data: Velocity-deviation vs spatial-scale scaling relation used to get turbulent velocity across the core  
  > "(cite: Sai:2023aa) provide a scaling relation between the velocity deviation" (5.2.1 Turbulence Scenario) [from (cite: Sai:2023aa)]
- External data: Perseus dense-core catalog (850 micron fluxes, core radii, C18O and N2H+ line widths) used for comparison  
  > "from the catalog provided by (cite: Kirk:2007aa)" (5.3.1 Is IRAS 15398 a Peculiar Source?) [from (cite: Kirk:2007aa)]
- External data: Perseus distance 282+-28 pc from Gaia distances  
  > "derived from the mean and standard deviation of Gaia distances to different regions of the Perseus star-froming region (cite: Zucker:2022aa)" (5.3.1 Is IRAS 15398 a Peculiar Source?) [from (cite: Zucker:2022aa)]
- External data: Primary-outflow dynamical timescale ~5e2 yr (inclination-corrected)  
  > "A previous work estimated the dynamical timescale of the primary outflow to be $\rtsim 5 \times 10^2~\yr$ with correction of the inclination angle in the same manner (cite: Bjerkeli:2016ab)" (4.2 Physical Properties of the Outflows) [from (cite: Bjerkeli:2016ab)]
- External data: Systemic velocity of 5.4 km/s  
  > "with respect to the systemic velocity of 5.4 $\kmps$ (cite: Thieme:2023aa)" (3 Results) [from (cite: Thieme:2023aa)]
- External data: Dust opacity kappa = 0.02 g^-1 cm^2  
  > "We adopt the dust opacity $\kappa_\nu = 0.02~\mathrm{g^{-1} cm^2}$ (cite: Ossenkopf:1994aa), and the dust temperature of $15\pm5~\kelv$." (5.2.1 Turbulence Scenario) [from (cite: Ossenkopf:1994aa)]
- Simulation/model as data: Literature simulations: disk orientation changes with time when turbulent-to-gravitational energy ratio is ~0.06-0.09 (used as comparison threshold)  
  > "($\beturb$) is $\rtsim0.06$–$0.09$ (cite: Seifried:2013aa; Matsumoto:2017aa)" (5.2.1 Turbulence Scenario)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "The data were calibrated with the pipeline version 42866M (Pipeline-CASA56-P1-B)" (ACA 7-m array Observations)
- casa version: CASA 5.6.1  
  > "We produced images from the visibility data using CASA 5.6.1 with the" (ACA 7-m array Observations)
- pipeline version: 42866M (Pipeline-CASA56-P1-B)  
  > "The data were calibrated with the pipeline version 42866M (Pipeline-CASA56-P1-B)" (ACA 7-m array Observations)
- archive products used as is: _not stated_
- flux calibrator: J1337-1257 (bandpass and flux); J1534-3526 (phase)  
  > "J1534$-$3526 and J1337$-$1257 were observed for the phase calibration and for the bandpass and flux calibrations, respectively." (ACA 7-m array Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "We produced images from the visibility data using CASA 5.6.1 with the" (ACA 7-m array Observations)
- deconvolver: multiscale clean  
  > "Multiscale clean was used with the scale parameters of zero and 10, which correspond to the point source and about one beam size, respectively." (ACA 7-m array Observations)
- weighting robust: Briggs, robust = 0.5  
  > "We adopted the Briggs style weighting with the robust parameter of 0.5 and the velocity resolution of" (ACA 7-m array Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: 0 and 10 (point source and ~one beam)  
  > "Multiscale clean was used with the scale parameters of zero and 10, which correspond to the point source and about one beam size, respectively." (ACA 7-m array Observations)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied to the cleaned image  
  > "The primary beam correction was applied to the cleaned image." (ACA 7-m array Observations)
- array combination: _not stated_
- smoothing: Two velocity channels binned (0.08 to 0.16 km/s) for the analysis cube  
  > "for analysis by binning two velocity channels." (ACA 7-m array Observations)
- final beam: 7.7'' x 4.1'' (PA 87 deg)  
  > "The angular resolution and root-mean-square (rms) noise level are $7.7\ensuremath{''}\times 4.1\ensuremath{''}$ (87$^\circ$) and $0.13~\jypbm$, respectively." (ACA 7-m array Observations)
- final rms: 0.13 Jy/beam  
  > "The angular resolution and root-mean-square (rms) noise level are $7.7\ensuremath{''}\times 4.1\ensuremath{''}$ (87$^\circ$) and $0.13~\jypbm$, respectively." (ACA 7-m array Observations)

### Inherited from earlier work

- Source position adopted for figures and analyses  
  > "We adopted the source position of ($\alpha_\mathrm{J2000}$, $\delta_\mathrm{J2000}$)$=$(15:43:02.24, $-34$:09:06.8) for the figures and analyses in this paper (cite: Yen:2017aa)." (ACA 7-m array Observations) [from (cite: Yen:2017aa)]
- Wind-driven shell model of the outflow cavity  
  > "we perform fitting with a wind-driven shell model (cite: Shu:1991aa; Lee:2000aa)" (4.2 Physical Properties of the Outflows) [from (cite: Shu:1991aa; Lee:2000aa)]
- Dynamical-timescale method (length / maximum velocity)  
  > "following the method used in previous works (cite: Yildiz:2015aa; Okoda:2021aa)." (4.2 Physical Properties of the Outflows) [from (cite: Yildiz:2015aa; Okoda:2021aa)]
- Outflow dissipation timescale from momentum vs drag force, C_D = 1  
  > "The dissipation timescale of the observed outflows can be estimated by equating their momentum and the drag force that the outflows experience (cite: Codella:1999aa)." (5.3.2 Age of the System and Outflow Dissipation Timescale) [from (cite: Codella:1999aa)]
- Core mass, radius and 850 micron flux taken from the eDisk paper  
  > "The core mass is estimated from the JCMT $850~\ensuremath{\mu}m$ flux, which is presented by (cite: Yen:inprep)" (5.2.1 Turbulence Scenario) [from (cite: Yen:inprep)]
- Perseus core definition (3-sigma contour) matched to Kirk et al.  
  > "Our definition of the core radius for IRAS 15398 is almost identical with theirs" (5.3.1 Is IRAS 15398 a Peculiar Source?) [from (cite: Kirk:2007aa)]

### Not stated but needed to reproduce (our reading)

- tclean threshold, masking strategy, niter and gridder/mosaic settings (only robust, scales and velocity resolution are given)
- Weblog or QA outcome of the pipeline run, and whether any manual flagging was added
- Which channels/velocity range were used to define each moment map and the integration limits for the moment 0 maps in Figure 2
- Continuum subtraction or absence thereof for the CO cube
- Priors, walker count, burn-in and likelihood for the emcee fits of the shell model
- Exact selection of PV cut widths and offsets sampling beyond 'half the beam size'
- The JCMT 850 micron flux map, core radius and POL-2 data come from an unpublished in-preparation paper
- C18O map and velocity-deviation relation come from Sai et al. 2023 (data not described here)
- How the outflow length and maximum velocity values in the dynamical-timescale table were measured (edge of map? threshold?)
- Excitation temperature choice within 50-200 K and how the CO mass was computed from the mean integrated flux

## Analysis recipe

1. **Calibrate and image the ACA CO 2-1 mosaic**: Pipeline calibration in CASA 5.6.1, then tclean with Briggs weighting (robust 0.5), multiscale clean, primary beam correction, 0.08 km/s channels binned to 0.16 km/s  
  > "The data were calibrated with the pipeline version 42866M (Pipeline-CASA56-P1-B)" (ACA 7-m array Observations); "We adopted the Briggs style weighting with the robust parameter of 0.5 and the velocity resolution of" (ACA 7-m array Observations); "The primary beam correction was applied to the cleaned image." (ACA 7-m array Observations)
   - software: CASA, tclean
   - parameter: robust = 0.5  
  > "We adopted the Briggs style weighting with the robust parameter of 0.5 and the velocity resolution of" (ACA 7-m array Observations)
   - parameter: multiscale scales 0 and 10  
  > "Multiscale clean was used with the scale parameters of zero and 10, which correspond to the point source and about one beam size, respectively." (ACA 7-m array Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Make moment maps and velocity-component moment 0 maps**: Moment 0 and 1 maps, then moment 0 maps of separate velocity ranges and channel maps to identify outflow components (primary, SB, NR1, NR2, SEB, WB, WR)  
  > "In order to probe further details of the velocity structures of the CO emission, moment 0 maps of different velocity components are presented in Figure" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure position-velocity structure of the lobes**: PV diagrams cut along each component at its position angle; PA from a Gaussian fit to the emission peak position through the protostar  
  > "The position angle of each component is measured as an angle from north to the line passing through the protostellar position and the peak position of the emission, which is determined by a Gaussian fit." (4.1 Velocity Structure)
   - parameter: P.A. 355 deg (NR1), 182 deg (SB), 332 deg (NR2), 155 deg (SEB)  
  > "Figure [3](#fig:pvds-3rdoutflow) presents position-velocity (PV) diagrams cut toward the NR1 (P.A.$=355^\circ$) and SB (P.A.$=182^\circ$) components." (4.1 Velocity Structure)
   - assumption: Absence of emission near the systemic velocity attributed to resolved-out optically thick foreground CO  
  > "This would be because the optically thick, extended foreground CO emission is resolved out." (4.1 Velocity Structure)
   - fitting: Gaussian fit for peak position and PA only  
  > "the peak position of the emission, which is determined by a Gaussian fit." (4.1 Velocity Structure)
   - validation: _not stated_
4. **Fit wind-driven shell model to outflow lobes**: Two-step fit: first morphology from moment 0 maps (5 sigma contours) to constrain C sin i; then velocity structure from PV diagrams (5+-1 sigma contours) for v0 and i, with MCMC  
  > "First, we fit the outflow shell morphology to constrain $C\sin i$ using the moment 0 maps presented in Figure [2](#fig:maps_diffvel)." (4.2 Physical Properties of the Outflows); "Then, adopting the constrained $C\sin i$, we fit the velocity structure using the PV diagrams." (4.2 Physical Properties of the Outflows)
   - software: emcee
   - parameter: 5 sigma contours define morphology and velocity structure; data sampled at half-beam offsets  
  > "In both steps, $5\sigma$ contours of the emission are used to define morphologies and velocity structures of the observed outflows." (4.2 Physical Properties of the Outflows)
   - parameter: Velocity data points below 4.4 km/s (SB), above 6.34 km/s (NR1) and 6.25 km/s (NR2) excluded  
  > "data points at velocities less than $4.4~\kmps$ are removed from the fitting for the SB lobe" (8 Wind-driven Shell Model Fitting)
   - assumption: R0 and z0 fixed at 1 arcsec  
  > "The constants $R_0$ and $z_0$ are fixed at $1''$" (4.2 Physical Properties of the Outflows)
   - assumption: Inclination angle defined between line of sight and outflow axis  
  > "Here, we define the inclination angle as an angle between the line-of-sight and the outflow axis" (4.2 Physical Properties of the Outflows)
   - fitting: MCMC with emcee; uncertainties are standard deviation of the posteriors; priors and likelihood not stated  
  > "by fitting the data points with the Markov-Chain Monte Carlo (MCMC) code" (8 Wind-driven Shell Model Fitting); "Uncertainties of the fitting parameters are calculated as the standard deviation of the posterior distributions." (8 Wind-driven Shell Model Fitting)
   - validation: Refit including all data points (cloud-contaminated velocities) gives similar results; systematic errors ~10% (v0) and ~1% (i)  
  > "Note that these fitting results do not change significantly even if we include the data points that are likely affected by the cloud contamination." (8 Wind-driven Shell Model Fitting)
5. **Estimate lobe dynamical timescales**: Dynamical timescale from lobe length and maximum velocity (lengths are lower limits as lobes reach the map edge); inclination correction tau_dyn = tau_dyn'/tan i  
  > "We use their lengths and the maximum velocities to calculate the dynamical timescales, following the method used in previous works (cite: Yildiz:2015aa; Okoda:2021aa)." (4.2 Physical Properties of the Outflows); "$\tau_\mathrm{dyn} = \tau_\mathrm{dyn}'/\tan i$" (Table 2)
   - assumption: Lobe lengths are lower limits because lobes extend to the map edge  
  > "Note that all these lobes are extended to the map edge, and thus, the outflow lengths represent lower limits." (4.2 Physical Properties of the Outflows)
   - fitting: _not stated_
   - validation: _not stated_
6. **Compute turbulent-to-gravitational energy ratio of the IRAS 15398 core**: beta_turb = E_turb/E_grav for a uniform-density core; core mass from 850 micron flux, turbulent velocity from C18O FWHM (non-thermal) or from the velocity-deviation scaling relation  
  > "we calculate $\beturb$ in the dense core of IRAS 15398 assuming the uniform density distribution" (5.2.1 Turbulence Scenario); "One way is to measure the full width at half maximum (FWHM) of a spectrum and subtract the thermal line width." (5.2.1 Turbulence Scenario)
   - parameter: F_850 = 2.9 Jy (10% uncertainty); dust temperature 15+-5 K; kappa = 0.02 g^-1 cm^2  
  > "$F_\nu$ is measured to be $2.9~\Jy$ with a typical flux uncertainty of 10%." (5.2.1 Turbulence Scenario); "We adopt the dust opacity $\kappa_\nu = 0.02~\mathrm{g^{-1} cm^2}$ (cite: Ossenkopf:1994aa), and the dust temperature of $15\pm5~\kelv$." (5.2.1 Turbulence Scenario)
   - parameter: C18O FWHM measured within 8'' radius circle at an off position 40'' north of the protostar  
  > "within a circle with a radius of $8''$ at an off position, $40''$ north of the protostellar position" (5.2.1 Turbulence Scenario)
   - assumption: Uniform density core; gas temperature equals dust temperature  
  > "By assuming the gas temperature same as the dust temperature above" (5.2.1 Turbulence Scenario); "assuming the uniform density distribution" (5.2.1 Turbulence Scenario)
   - fitting: _not stated_
   - validation: Two independent turbulent-velocity estimates (C18O line width: upper limit; scaling relation) bracket beta_turb  
  > "This would give an upper limit of the turbulent velocity of the dense core, as the C$^{18}$O $J=2$–1 emission may include the surrounding cloud component." (5.2.1 Turbulence Scenario)
7. **Compare core turbulence with Perseus dense cores**: Recompute core mass, non-thermal velocity and beta_turb for Perseus cores from the Kirk et al. catalog with the same dust opacity and temperature; compare histograms (C18O and N2H+ line widths)  
  > "Then, we calculated the core masses and non-thermal velocities assuming the same dust opacity and temperature as for IRAS 15398." (5.3.1 Is IRAS 15398 a Peculiar Source?)
   - parameter: Perseus distance 282+-28 pc  
  > "We adopted the distance of $282 \pm28~\pc$ for the Perseus dense cores" (5.3.1 Is IRAS 15398 a Peculiar Source?)
   - assumption: Same dust opacity and temperature as for IRAS 15398  
  > "assuming the same dust opacity and temperature as for IRAS 15398." (5.3.1 Is IRAS 15398 a Peculiar Source?)
   - fitting: _not stated_
   - validation: Core radius definition and 850 micron rms for IRAS 15398 checked to be comparable to the Perseus catalog  
  > "Our definition of the core radius for IRAS 15398 is almost identical with theirs" (5.3.1 Is IRAS 15398 a Peculiar Source?)
8. **Estimate outflow dissipation timescale**: t_diss = P_out/F_D ~ 2 (rho_out/rho_core)(l_out/v_out), with outflow mass from CO integrated flux in LTE  
  > "The dissipation timescale of the observed outflows can be estimated by equating their momentum and the drag force that the outflows experience (cite: Codella:1999aa)." (5.3.2 Age of the System and Outflow Dissipation Timescale)
   - parameter: core density 1.0e4 cm^-3 (rho_core ~4.7e-20 g cm^-3); outflow length ~8500 au, width ~1600 au; v_out ~3 km/s; i ~70 deg  
  > "By adopting outflow lengths of $\rtsim8500~\au$ (or $\rtsim55''$) and widths of $\rtsim1600~\au$ (or $\rtsim10''$) based on Figure" (5.3.2 Age of the System and Outflow Dissipation Timescale)
   - assumption: C_D = 1; CO abundance 1e-4; mean molecular weight 2.8; LTE; T_ex = 50-200 K; outflow mass scaled up to ~1e-2 Msun to account for missing low-velocity gas  
  > "a CO molecular abundance of $10^{-4}$, the mean molecular weight of 2.8 and the local thermal equilibrium (LTE)" (5.3.2 Age of the System and Outflow Dissipation Timescale); "Hence, we adopt an outflow mass of $\rtsim 1 \times10^{-2}~\Msun$ for an order of magnitude estimate." (5.3.2 Age of the System and Outflow Dissipation Timescale)
   - fitting: _not stated_
   - validation: Density ratio ~2 compared with ratio in numerical simulations  
  > "is roughly consistent with the density ratio found in numerical simulations (cite: Machida:2012aa)" (5.3.2 Age of the System and Outflow Dissipation Timescale)

## Software

- **CASA** 5.6.1 (pipeline 42866M, Pipeline-CASA56-P1-B): Pipeline calibration and tclean imaging  
  > "The data were calibrated with the pipeline version 42866M (Pipeline-CASA56-P1-B) of the Common Astronomy Software Applications package" (ACA 7-m array Observations); "We produced images from the visibility data using CASA 5.6.1 with the" (ACA 7-m array Observations)
- **tclean** : Imaging with Briggs weighting and multiscale clean  
  > "Multiscale clean was used with the scale parameters of zero and 10, which correspond to the point source and about one beam size, respectively." (ACA 7-m array Observations)
- **emcee** : MCMC fitting of the wind-driven shell model morphology and velocity structure  
  > "by fitting the data points with the Markov-Chain Monte Carlo (MCMC) code" (8 Wind-driven Shell Model Fitting)
- **Numpy** : _not stated_
- **Scipy** : _not stated_
- **Astropy** : _not stated_
- **Matplotlib** : _not stated_
- **Clumpfind** : Identified the Perseus dense cores in the Kirk et al. catalog (not run by the authors)  
  > "identified the dense cores using the `Clumpfind` algorithm" (5.3.1 Is IRAS 15398 a Peculiar Source?)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SB lobe C sin i | 0.81 | 0.02 | arcsec^-1 | 4 | SB    /  $0.81\pm0.02$  / $0.1129\pm0.0004$ / $71.83 \pm 0.05$ |
| SB lobe v0 | 0.1129 | 0.0004 | km/s | 4 | SB    /  $0.81\pm0.02$  / $0.1129\pm0.0004$ / $71.83 \pm 0.05$ |
| SB lobe inclination i | 71.83 | 0.05 | deg | 4 | SB    /  $0.81\pm0.02$  / $0.1129\pm0.0004$ / $71.83 \pm 0.05$ |
| NR1 lobe C sin i | 1.24 | 0.02 | arcsec^-1 | 4 | NR1   / $1.24 \pm 0.02$ / $0.1017\pm0.0006$ / $74.24 \pm 0.12$ |
| NR1 lobe v0 | 0.1017 | 0.0006 | km/s | 4 | NR1   / $1.24 \pm 0.02$ / $0.1017\pm0.0006$ / $74.24 \pm 0.12$ |
| NR1 lobe inclination i | 74.24 | 0.12 | deg | 4 | NR1   / $1.24 \pm 0.02$ / $0.1017\pm0.0006$ / $74.24 \pm 0.12$ |
| NR2 lobe C sin i | 0.89 | 0.02 | arcsec^-1 | 4 | NR2   / $0.89\pm 0.02$  / $0.0542\pm0.0016$ / $69.75 \pm 0.71$ |
| NR2 lobe v0 | 0.0542 | 0.0016 | km/s | 4 | NR2   / $0.89\pm 0.02$  / $0.0542\pm0.0016$ / $69.75 \pm 0.71$ |
| NR2 lobe inclination i | 69.75 | 0.71 | deg | 4 | NR2   / $0.89\pm 0.02$  / $0.0542\pm0.0016$ / $69.75 \pm 0.71$ |
| SB lobe dynamical timescale (inclination corrected) | >=0.49e4 | lower limit | yr | 5 | SB / $\gtrsim12,000$ / 1.72 / 3.68 / $\gtrsim1.5$ / $\gtrsim0.49$ / |
| NR1 lobe dynamical timescale (inclination corrected) | >=0.59e4 | lower limit | yr | 5 | NR1 / $\gtrsim12,000$ / 8.12 / 2.72 / $\gtrsim2.1$ / $\gtrsim0.59$ / |
| NR2 lobe dynamical timescale (inclination corrected) | >=1.1e4 | lower limit | yr | 5 | NR2 / $\gtrsim12,000$ / 7.32 / 1.92 / $\gtrsim3.0$ / $\gtrsim1.1$ / |
| Misalignment angle between the three outflows on the plane of the sky | ~20-90 | not stated | deg | 3 | The three outflows are all misaligned by $\rtsim20$–$90^\circ$ |
| C18O FWHM at off position (40'' north) | 0.50 | 0.02 | km/s | 6 | The FWHM of the spectrum is measured to be $0.50\pm0.02~\kmps$ |
| Non-thermal velocity from C18O line width | 0.20 | 0.02 | km/s | 6 | is estimated to be $0.20 \pm 0.02~\kmps$ |
| beta_turb from C18O non-thermal velocity | ~1.4 | 0.9 | dimensionless | 6 | These parameters yield $\beturb \tsim 1.4\pm0.9$ |
| Turbulent velocity across the core from scaling relation | 0.10 | 0.01 | km/s | 6 | the turbulent velocity across the dense core is estimated to be $0.10 \pm 0.01~\kmps$ |
| beta_turb from scaling-relation turbulent velocity | ~0.33 | 0.20 | dimensionless | 6 | This estimate results in $\beturb \tsim 0.33 \pm 0.20$ |
| Average outflow mass from CO | ~(0.32-1.1)e-3 | not stated | Msun | 8 | An averaged mass of the outflows are estimated to be $\rtsim(0.32\mbox{--}1.1)\times10^{-3}~\Msun$ |
| Outflow dissipation timescale | ~2e4 | not stated | yr | 8 | yield the dissipation timescale of $\rtsim 2 \times 10^4~\yr$ |

## Qualitative findings

- New elongated redshifted and blueshifted components at ~30''-75'' show Hubble-law like velocity structures, interpreted as a third outflow  
  > "These elongated components exhibit Hubble-law like velocity structures, i.e., an increase of velocity with increasing distance from the protostar, suggesting that it is the third outflow associated with the protostar." (abstract)
- NR2 redshifted component likely the counterpart of the previously blueshifted-only secondary outflow  
  > "This redshifted component also exhibits a Hubble-law like velocity profile, which could be the counterpart of the secondary outflow mostly detected at blueshifted velocities in a previous study." (abstract)
- Authors favor turbulence in the dense core over field/rotation misalignment as origin of the multiple outflows  
  > "We favor the second scenario as the origin of the multiple outflows in IRAS 15398" (abstract)

## Claim tuples

- H: Do the NR1 and SB components trace a third outflow from IRAS 15398? | E: ACA CO 2-1 mosaic; PV diagrams along NR1 and SB; wind-driven shell fits | R: NR1 and SB are symmetric about the protostar with Hubble-law like velocity profiles; v0 ~0.10-0.11 km/s and i ~72-74 deg | F: NR1 and SB are two lobes of a third outflow misaligned with the primary and secondary outflows | **supported**
- H: Is the NR2 component part of the secondary outflow? | E: PV diagram and shell fit of NR2, comparison of its direction with SEB and the known secondary outflow | R: NR2 has a Hubble-law like profile, v0 about half that of NR1/SB, and is aligned with SEB and the secondary outflow | F: NR2 is a separate ejection event and probably the redshifted counterpart of the secondary outflow | **partially**
- H: Has the outflow launch direction changed with time? | E: Compare position angles and dynamical timescales of primary, secondary and third outflows | R: Outflows misaligned by ~20-90 deg; dynamical timescales differ by about an order of magnitude (lower limits >=0.49-1.1e4 yr vs ~5e2 yr for the primary) | F: The outflow launch direction has significantly changed with time | **supported**
- H: Is the time-varying outflow direction due to core turbulence or to a magnetic-field/rotation-axis misalignment? | E: Compute beta_turb for the core from JCMT 850 micron flux and C18O line widths; estimate probability of large 3D misalignment from SOFIA/JCMT field and C18O velocity gradient directions | R: beta_turb ~0.33-1.4, above the ~0.06-0.09 in simulations; projected field/angular-momentum misalignment 20-35 deg, probability of >80 deg in 3D less than 10% | F: Turbulence could cause the changing outflow direction; large field misalignment is less likely but not ruled out | **partially**
- H: Is the IRAS 15398 core unusually turbulent compared with other dense cores? | E: Compare core mass, turbulent velocity and beta_turb with Perseus dense cores (Kirk et al. catalog) | R: Core mass, turbulent velocity and beta_turb of IRAS 15398 are comparable to or lower than typical Perseus values | F: Turbulence in the IRAS 15398 core is not notably stronger than in other cores, so multiple outflows may be common but short-lived | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: A wind-driven shell model is used to characterize outflow lobe geometry and velocity structure  
  > "To characterize their geometry and velocity structures, we perform fitting with a wind-driven shell model (cite: Shu:1991aa; Lee:2000aa)." (4.2 Physical Properties of the Outflows)
- Alternative: Unresolved close binary driving the multiple outflows: rejected as unlikely  
  > "Thus, these multiple outflows would not be likely driven by unresolved very close binary protostars." (5.2 Origin of the Multiple Outflows)
- Alternative: NR1 and NR2 as two sides of a single outflow cavity: rejected because of distinct expansion velocities  
  > "Hence, the NR1 and NR2 lobes are most likely two different outflows but not different sides of the same outflow cavity." (5.1 Configurations of the Multiple Outflows)
- Alternative: WB and WR filaments treated as ambient cloud rather than outflow  
  > "The constant velocities close to the cloud velocity suggest that the WB and WR filamentary structures are part of the ambient cloud." (4.1 Velocity Structure)
- How they decided it was enough: _not stated_
- Limitation (authors): Lobe lengths and dynamical timescales are only lower limits because lobes reach the map edge  
  > "Note that all these lobes are extended to the map edge, and thus, the outflow lengths represent lower limits." (4.2 Physical Properties of the Outflows)
- Limitation (authors): SEB velocity structure not well resolved at the ACA resolution  
  > "Its velocity structures are not well resolved with our limited spatial resolution." (4.1 Velocity Structure)
- Limitation (authors): Fit uncertainties exclude systematic errors of the fitting method  
  > "do not take into account systemic errors of the fitting method itself." (8 Wind-driven Shell Model Fitting)
- Limitation (authors): Inclination (cos i) does not converge in the morphology fit, so it is left free in the velocity fit  
  > "The cavity shape, $C \sin i$, is well constrained, while the cosine of the inclination angle, $\cos i$, does not converge." (8 Wind-driven Shell Model Fitting)
- Limitation (authors): Outflow mass likely underestimated because low-velocity gas is hidden by optically thick foreground gas  
  > "Note that the mass of the outflows is likely underestimated, because we do not take into account low-velocity components obscured by the optically thick, extended foreground gas." (5.3.2 Age of the System and Outflow Dissipation Timescale)
- Caveat (inferred, ours): Only a single-execution ACA 7-m dataset with a ~8'' beam: lobe and PV measurements near the systemic velocity are dominated by resolved-out foreground CO
- Caveat (inferred, ours): Hubble-law identification of the third outflow rests on low-velocity (1-3.5 km/s relative) emission that can be confused with ambient cloud; no total-power data are mentioned
- Caveat (inferred, ours): Turbulence-vs-misalignment comparison uses inputs from an unpublished paper and a C18O map from another paper, and beta_turb is compared with only two simulation studies
- Caveat (inferred, ours): Inclination from the fit is poorly constrained in the morphology step and shell-model priors are not described
- Caveat (inferred, ours): Dynamical timescales are lower limits so the ordering of the secondary and third outflows is not established

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging mask, threshold and niter, and moment-map velocity limits
- Missing: emcee priors, likelihood and walker settings
- Missing: The JCMT 850 micron flux/radius and POL-2 results (unpublished eDisk paper), and the C18O data of Sai et al. 2023
- Missing: Exact lengths and maximum velocities behind the dynamical-timescale table
- Missing: Statement of data availability or archive products
- Data volume (inferred): Small: one ACA 7-m Band 6 mosaic execution (28 pointings, one 62.5 MHz window); a few GB of raw data, under 1 GB of image products
- Score (inferred): 3/5, ALMA project and calibration/imaging recipe are largely given with numeric fit results, but masks, priors and the core-mass inputs (unpublished paper) are missing, and data availability is not stated.
- Rediscovery candidate: no, Public availability of the data is not stated in the paper, and key inputs (core mass/radius from in-preparation work, fit priors, masks) are missing, so the main numeric results cannot be redone from the text alone.

## Links

- Method: (cite: Shu:1991aa; Lee:2000aa) (Wind-driven shell model used to fit the outflow lobes)
- Method: (cite: Yildiz:2015aa; Okoda:2021aa) (Dynamical timescale method)
- Method: (cite: Codella:1999aa) (Outflow dissipation timescale from momentum and drag force)
- Method: (cite: Sai:2023aa) (C18O data and velocity-deviation scaling relation for turbulent velocity)
- Companion: (cite: Okoda:2021aa) (Earlier ALMA detection of the monopolar blueshifted secondary outflow)
- Companion: (cite: Thieme:2023aa) (Disk/protostellar mass and systemic velocity of IRAS 15398)
- Companion: (cite: Yen:inprep) (eDisk paper providing JCMT 850 micron flux and core radius)
- Companion: (cite: Yen:2017aa) (Source position and primary outflow position angles)
- Related: eDisk (cited as the eDisk team in the Yen in-preparation reference)
- Related: Perseus dense-core surveys (Kirk et al.)

## Checks

```json
{
 "quotes": 136,
 "quotes_ok": 136,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 20,
 "numeric_problems": 0,
 "fill": {
  "facts": 119,
  "stated": 87,
  "rate": 0.731
 },
 "evidence_ok": true
}
```
