# Multiphase Gas Structure in the Circumnuclear Region of NGC 5506 Observed with ALMA

`2026ApJ..1002..100T` | The Astrophysical Journal 2026 | first author: Takechi, Kana | arXiv: 2604.07587 | DOI: 10.3847/1538-4357/ae5703

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Multiphase gas distribution and kinematics of the circumnuclear disk of NGC 5506 in atomic, molecular and ionized gas, compared with theoretical torus/fountain/SN-turbulence models  
  > "In this study, we analyze ALMA and Hubble Space Telescope (HST) observations of the circumnuclear region of NGC 5506 to characterize the distribution and kinematics of atomic, molecular, and ionized gas, and to compare these results with theoretical models." (Introduction)
- Target **NGC 5506**: coordinates AGN position (R.A., decl.) = 14h13m14.877s, -3d12m27.66s (Band 7 continuum peak)  
  > "We adopt a luminosity distance of 23.8 Mpc for NGC 5506 (cite: Karachensev2014)" (Introduction); "This position is determined from the peak of the Band 7 continuum" (Results); "(R.A., decl.) = (14$^{\rm h}$13$^{\rm m}$14$^{\rm s}$.877, $-$3$\ensuremath{^\circ}$12$\ensuremath{'}$27$\ensuremath{''}$.66)" (Results); z/distance luminosity distance 23.8 Mpc; 1 arcsec = 114 pc (redshift not stated; Vsys = 1872 km/s)  
  > "We adopt a luminosity distance of 23.8 Mpc for NGC 5506 (cite: Karachensev2014)" (Introduction); "This position is determined from the peak of the Band 7 continuum" (Results); "(R.A., decl.) = (14$^{\rm h}$13$^{\rm m}$14$^{\rm s}$.877, $-$3$\ensuremath{^\circ}$12$\ensuremath{'}$27$\ensuremath{''}$.66)" (Results); distance from Karachentsev et al. 2014 (cite: Karachensev2014)  
  > "We adopt a luminosity distance of 23.8 Mpc for NGC 5506 (cite: Karachensev2014)" (Introduction); "This position is determined from the peak of the Band 7 continuum" (Results); "(R.A., decl.) = (14$^{\rm h}$13$^{\rm m}$14$^{\rm s}$.877, $-$3$\ensuremath{^\circ}$12$\ensuremath{'}$27$\ensuremath{''}$.66)" (Results)

## Data provenance

- ALMA projects: 2017.1.00082.S, 2022.1.00410.S
- bands: [C I](1-0): Band 8 (Cycle 9); CO(3-2) and HCO+(4-3): Band 7 (Cycle 5, archival)  
  > "We observed \[C I\](1–0) with ALMA Band 8 in Cycle 9. CO(3–2) and HCO$^{+}$(4–3) were obtained from archival Band 7 observations." (2.1 ALMA)
- frequencies and spectral setup: Rest frequencies 492.2 GHz ([C I]), 345.8 GHz (CO 3-2), 356.7 GHz (HCO+ 4-3); detailed spectral windows not stated  
  > "| 370.4 $\rm$ | 492.2 | $4.7\times10^2$ |" (Line properties table); "| 867.0 | 345.8 | $8.4\times10^3$ |" (Line properties table); "| 840.4 | 356.7 | $1.8\times10^6$ |" (Line properties table)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 14-1198 m ([C I](1-0)); 14-2309 m (CO(3-2), HCO+(4-3))  
  > "Baseline lengths are 14–1198 m for" (2.1 ALMA); "14–2309 m for CO(3–2) and HCO$^{+}$(4–3)" (2.1 ALMA)
- angular resolution: ~20 pc; beams 0.166x0.143 arcsec ([C I]), 0.176x0.135 arcsec (CO 3-2), 0.174x0.134 arcsec (HCO+)  
  > "at a spatial resolution of $\sim20$ pc" (abstract); "producing synthesized beam sizes of $0.^{\prime\prime}166 \times 0.^{\prime\prime}143$ and $0.^{\prime\prime}176 \times 0.^{\prime\prime}135$, respectively" (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: rms 7.7 mJy/beam ([C I]), 2.2 mJy/beam (CO 3-2), 0.69 mJy/beam (HCO+) in 20 km/s channels; peaks 87, 56, 4.7 mJy/beam  
  > "| 19.1 $\times$ 16.4 | 7.7 | 87 |" (Imaging properties table); "| 20.2 $\times$ 15.5 | 2.2 | 56 |" (Imaging properties table); "| 20.0 $\times$ 15.4 | 0.69 | 4.7 |" (Imaging properties table)
- time on source: 2:00:57 ([C I]); 0:33:24 (CO 3-2, HCO+ 4-3)  
  > "| (1–0) | 2022.1.00410.S | 2023 Apr 13, 20 | 42 | 14–1198 | 2:00:57 | 2022.2.0.68 |" (Observation table); "| CO(3–2) | 2017.1.00082.S | 2017 Dec 31 | 44 | 14–2309 | 0:33:24 | Pipeline-CASA51-P2-B |" (Observation table)
- observing dates: [C I]: 2023 Apr 13, 20 (UT); CO/HCO+: 2017 Dec 31  
  > "| (1–0) | 2022.1.00410.S | 2023 Apr 13, 20 | 42 | 14–1198 | 2:00:57 | 2022.2.0.68 |" (Observation table); "| CO(3–2) | 2017.1.00082.S | 2017 Dec 31 | 44 | 14–2309 | 0:33:24 | Pipeline-CASA51-P2-B |" (Observation table)
- pi or archival as stated: [C I](1-0) newly observed by the authors in Cycle 9; CO(3-2) and HCO+(4-3) archival Cycle 5  
  > "We observed \[C I\](1–0) with ALMA Band 8 in Cycle 9. CO(3–2) and HCO$^{+}$(4–3) were obtained from archival Band 7 observations." (2.1 ALMA)
- Line: C 3P1 -> 3P0 ([C I](1-0)) (492.2 GHz)
- Line: CO J=3-2 (345.8 GHz)
- Line: HCO+ J=4-3 (356.7 GHz)
- Other facility **HST FOC (F501N, f/96), [O III] 5007**: [O III] lambda5007 image tracing the ionized biconical outflow (observation ID x2740302t); astrometry tied to STIS and Pan-STARRS1  
  > "\[O III\]$\lambda$5007 was observed with the HST Faint Object Camera (FOC) using the f/96 aperture and the F501N filter (cite: Nota1996)." (2.2 HST); "observed with HST (observation ID: x2740302t)" (Observation and Data Analysis)
- Other facility **HST STIS and Pan-STARRS1 (astrometric references)**: STIS image and PS1 catalog star used to correct the FOC WCS offset of ~3 arcsec  
  > "The STIS image was first aligned to the PS1 catalog, then used to determine the position of Star B." (2.2 HST)
- External data: SMBH mass 2.0 (+8.0/-1.6) x 10^7 Msun  
  > "NGC 5506 hosts an SMBH with a mass of $2.0^{+8.0}_{-1.6}\times 10^7~M_{\odot}$ (cite: Gofford2015)" (Introduction) [from (cite: Gofford2015), from (cite: Papadakis2004) and (cite: Nikolajuk2009)]
- External data: Bolometric luminosity 1.3e44 erg/s  
  > "The bolometric luminosity is 1.3 $\times$ 10$^{44}$ erg s$^{-1}$ (cite: Davies2020)" (Introduction) [from (cite: Davies2020)]
- External data: Eddington ratio 0.05 (+0.21/-0.04)  
  > "the Eddington ratio is $\lambda_{\rm Edd} = 0.05^{+0.21}_{-0.04}$ (cite: Esposito2024)" (Introduction) [from (cite: Esposito2024)]
- External data: Luminosity distance 23.8 Mpc  
  > "We adopt a luminosity distance of 23.8 Mpc for NGC 5506 (cite: Karachensev2014)" (Introduction) [from (cite: Karachensev2014)]
- External data: Flat LCDM cosmology H0=67.66, Om=0.3111, OL=0.6889  
  > "We assume a flat $\Lambda$CDM cosmology with $H_0=67.66$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm m}=0.3111$, and $\Omega_{\Lambda}=0.6889$ (cite: Planck2020)." (Introduction) [from (cite: Planck2020)]
- External data: [O III] biconical outflow model overlaid on line-ratio map (inclination 10 deg, max velocity 550 km/s on 300 pc scales)  
  > "and the corresponding biconical outflow model (cite: Fischer2013)" (4.3 [C I](1-0)/CO(3-2) Line Ratio); "reveal a biconical ionized outflow with an inclination of $10^\circ$ and a maximum velocity of 550 km s$^{-1}$ on scales of 300 pc (cite: Fischer2013)" (Introduction) [from (cite: Fischer2013)]
- External data: Star formation rate 0.3 (+0.7/-0.2) Msun/yr from 11.3 micron PAH feature  
  > "The star formation rate of NGC 5506 is SFR$=0.3^{+0.7}_{-0.2}~M_\odot~\mathrm{yr^{-1}}$, derived from the 11.3 $\mu$m polycyclic aromatic hydrocarbon feature (cite: Ruschel2017)" (4.4 Interpretation) [from (cite: Ruschel2017)]
- External data: CO-to-H2 conversion factor 0.8 Msun (K km/s pc^2)^-1  
  > "we adopt the canonical CO-to-H$_2$ conversion factor for active environments $M_{\rm H_{2}} / L^{\prime}_{\rm CO} = 0.8 M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$ (cite: Downes&Solomon1998)" (Molecular Gas Mass and Column Density) [from (cite: Downes&Solomon1998)]
- External data: Astrometric reference star from the Pan-STARRS1 catalog  
  > "Star A is listed in the Pan-STARRS1 (PS1) catalog and serves as the primary astrometric reference (cite: Chambers2016)" (2.2 HST) [from (cite: Chambers2016)]
- Simulation/model as data: SN-driven turbulence model of Kawakatu et al. 2020: obscuring fraction f_obs vs Eddington ratio and BH mass; turbulent velocity v_t formula  
  > "(cite: Kawakatu2020) derive the AGN luminosity and black hole mass dependence of the obscuring fraction $f_{\rm obs}$" (4.4 Interpretation); "The predicted turbulent velocity is $v_{\rm t}\sim30~\mathrm{km~s^{-1}}$ at $r\sim100$ pc." (4.4 Interpretation)
- Simulation/model as data: Radiation-driven fountain simulations (Wada 2012, 2016; Baba 2024) used qualitatively for predicted C, CO, HCO+ distributions  
  > "Simulations by (cite: Baba2024) further predict distinct spatial distributions for C, CO, and HCO$^{+}$" (4.4 Interpretation)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline; one, two and two antennas flagged for [C I], CO(3-2), HCO+(4-3)  
  > "Calibration was performed using the ALMA pipeline in Common Astronomy Software Applications (cite: Casa2022), with one, two, and two antennas flagged for" (2.1 ALMA)
- casa version: CASA 6.5.6 used for imaging; calibration CASA version not stated apart from pipeline tags  
  > "Calibrated data were imaged using CASA (version 6.5.6) task" (2.1 ALMA)
- pipeline version: 2022.2.0.68 ([C I], 2022.1.00410.S); Pipeline-CASA51-P2-B (CO, HCO+, 2017.1.00082.S)  
  > "| 14–1198 | 2:00:57 | 2022.2.0.68 |" (Observation table); "| 14–2309 | 0:33:24 | Pipeline-CASA51-P2-B |" (Observation table)
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10% for Band 7 and 8 (from the Cycle 9 Proposer's Guide)  
  > "The ALMA Cycle 9 Proposer’s Guide indicates absolute flux uncertainties of $\sim10\%$ for both Band 7 and 8." (2.1 ALMA)
- self calibration: _not stated_

### Imaging

- task: CASA tclean, channel width 20 km/s  
  > "Calibrated data were imaged using CASA (version 6.5.6) task `tclean` with a channel width of 20 km s$^{-1}$." (2.1 ALMA)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.8 ([C I]), 1.3 (CO 3-2), 2.0 (natural; HCO+), tuned to match beams  
  > "HCO$^{+}$(4–3) data were imaged with `robust` = 2.0 (natural weighting)" (2.1 ALMA); "For \[C I\](1–0) and CO(3–2), `robust` values of 0.8 and 1.3 were used" (2.1 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Automasking per CASA automasking guide parameters; nsigma = 2 (threshold 2x rms)  
  > "Automasking was applied following the parameters recommended in the CASA automasking guide." (2.1 ALMA); "We set the `nsigma` parameter to 2, corresponding to a cleaning threshold of $2\times$ the rms noise (cite: Casa2022)." (2.1 ALMA)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.166x0.143 arcsec PA 70.6 ([C I]); 0.176x0.135 PA -52.8 (CO 3-2); 0.174x0.134 PA -54.4 (HCO+)  
  > "| (1–0)$^1$ | ALMA | 492.2 | 0.166 $\times$ 0.143, (70.6) |" (Imaging properties table); "| CO(3–2)$^2$ | ALMA | 345.8 | 0.176 $\times$ 0.135, (-52.8) |" (Imaging properties table); "| HCO$^{+}$(4–3)$^2$ | ALMA | 356.7 | 0.174 $\times$ 0.134, (-54.4) |" (Imaging properties table)
- final rms: 7.7 ([C I]), 2.2 (CO 3-2), 0.69 (HCO+) mJy/beam  
  > "| 19.1 $\times$ 16.4 | 7.7 | 87 |" (Imaging properties table); "| 20.2 $\times$ 15.5 | 2.2 | 56 |" (Imaging properties table); "| 20.0 $\times$ 15.4 | 0.69 | 4.7 |" (Imaging properties table)

### Inherited from earlier work

- Automasking parameters taken from the CASA automasking guide  
  > "Automasking was applied following the parameters recommended in the CASA automasking guide." (2.1 ALMA) [from CASA automasking guide (as written)]
- H2 gas mass and column density derived following Izumi et al. 2018  
  > "The H$_2$ gas mass and column density are derived from the moment 0 map of CO(3–2), following (cite: Izumi2018)." (Molecular Gas Mass and Column Density) [from (cite: Izumi2018)]
- Vdisp/Vrot used as proxy for H/R under hydrostatic equilibrium  
  > "Under the assumption of hydrostatic equilibrium, this ratio serves as a proxy for the disk scale height-to-radius ratio ($H/R$; (cite: Izumi2018))." (4.2.1 Disk Thickness Inferred from Gas Dynamics) [from (cite: Izumi2018)]
- Biconical [O III] outflow model geometry taken from Fischer et al. 2013  
  > "and the corresponding biconical outflow model (cite: Fischer2013)" (4.3 [C I](1-0)/CO(3-2) Line Ratio) [from (cite: Fischer2013)]
- Turbulent velocity formula and f_obs model from the SN-driven turbulence model  
  > "and $r$ is the distance from the black hole (cite: Kawakatu2020)" (4.4 Interpretation) [from (cite: Kawakatu2020), built on (cite: Kawakatu2008)]

### Not stated but needed to reproduce (our reading)

- Continuum subtraction method and line-free channels for each cube
- Cell size, image size, spectral window selection and rest-frequency/velocity frame used in tclean
- Any self-calibration, and whether pipeline products were reprocessed manually (pipeline calibration used as stated, no manual flagging details beyond antenna counts)
- Which antennas were flagged in each dataset
- Primary beam correction and whether moment maps used primary-beam-corrected cubes
- Moment map generation details (masking, noise estimate used for 3.5 sigma), and the moment-0 integration velocity range
- 3D Barolo parameters (mask, number of rings, initial guesses, normalisation, free-parameter bounds, version) and how Vdisp/Vrot uncertainties were obtained
- How the inside/outside bicone regions for the line ratio were defined and registered (pixel mask, HST-to-ALMA alignment)
- How the 3 sigma/error bars on FWHM and line ratio were propagated
- Redshift and exact CO(3-2) velocity-integrated flux used in the mass calculation

## Analysis recipe

1. **Calibrate and image ALMA cubes with matched beams**: ALMA pipeline calibration, then tclean with 20 km/s channels, automasking, nsigma=2, Briggs robust tuned per line to give comparable ~0.17x0.14 arcsec beams  
  > "Calibrated data were imaged using CASA (version 6.5.6) task `tclean` with a channel width of 20 km s$^{-1}$." (2.1 ALMA); "Because this study compares geometrical thicknesses among different gas phases, the Briggs `robust` parameter was adjusted to synthesize comparable beam sizes across all three lines." (2.1 ALMA)
   - software: CASA 6.5.6, tclean, ALMA pipeline
   - parameter: robust = 0.8 ([C I]), 1.3 (CO 3-2), 2.0 (HCO+)  
  > "HCO$^{+}$(4–3) data were imaged with `robust` = 2.0 (natural weighting)" (2.1 ALMA); "For \[C I\](1–0) and CO(3–2), `robust` values of 0.8 and 1.3 were used" (2.1 ALMA)
   - parameter: nsigma = 2 (cleaning threshold 2x rms)  
  > "We set the `nsigma` parameter to 2, corresponding to a cleaning threshold of $2\times$ the rms noise (cite: Casa2022)." (2.1 ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Astrometrically correct HST [O III] image and measure PSF**: FOC WCS offset (~3 arcsec) corrected via a STIS image and two reference stars tied to Pan-STARRS1; star centroids with DAOStarFinder; PSF measured with SExtractor  
  > "The FOC image exhibits an astrometric offset of approximately 3$\ensuremath{''}$." (2.2 HST); "Centroids of both stars were measured using `DAOStarFinder` from the `photutils` package (cite: Bradley2024)." (2.2 HST)
   - software: photutils DAOStarFinder, SExtractor
   - parameter: [O III] PSF FWHM 0.054 arcsec  
  > "This yields a full width at half-maximum (FWHM) of 0$^{\prime\prime}$.054." (2.2 HST)
   - fitting: Point-source fit with SExtractor for the PSF  
  > "was measured using `SExtractor` (cite: Bertin1996) by fitting a point source at" (2.2 HST)
   - validation: Astrometric accuracy better than 0.2 arcsec  
  > "resulting in an astrometric accuracy better than 0$\ensuremath{''}$.2" (2.2 HST)
3. **Make moment maps and major-axis profiles; define the CND**: Moment 0/1 maps from pixels with S/N > 3.5; CND defined as >3.5 sigma emission in a 5 x 1.4 arcsec box centred on the AGN; AGN position from Band 7 continuum peak; intensity profiles along the major axis  
  > "generated using pixels with a signal-to-noise ratio $>3.5$." (3 Results); "we define the CND of NGC 5506 as the region where emission is detected at $>3.5\sigma$ within a 5$^{\prime\prime}\times1^{\prime\prime}.4$ box centered on the AGN" (Introduction)
   - software: CASA
   - parameter: AGN position from the Band 7 continuum peak  
  > "This position is determined from the peak of the Band 7 continuum" (3 Results)
   - fitting: _not stated_
   - validation: AGN position consistent with the Band 8 continuum peak; PVDs symmetric about Vsys and AGN position  
  > "and is consistent with the Band 8 continuum peak." (3 Results); "The PVDs appear symmetric about both the systemic velocity and the AGN position, confirming the validity of these reference values." (3.3 Velocity structure)
4. **Measure geometrical thickness via minor-axis Gaussian FWHM**: Slice profiles of moment 0 maps parallel to the minor axis, every 4 pixels along the major axis, averaged over 3 pixels; each fitted with a Gaussian with peak fixed to the major-axis position; FWHM used as emission width  
  > "at 4 pixel ($\sim9$ pc) intervals along the major axis and averaged over a 3 pixel ($\sim7$ pc) width." (4.1.2 Geometrical Thickness of the Circumnuclear Disk); "The FWHM of each best-fit Gaussian is then derived as a measure of the emission width." (4.1.2 Geometrical Thickness of the Circumnuclear Disk)
   - parameter: Gaussian peak fixed to the corresponding major axis position  
  > "with the peak fixed to the corresponding major axis position." (4.1.2 Geometrical Thickness of the Circumnuclear Disk)
   - assumption: Because the disk is highly inclined (i = 79 deg), thickness can be inferred from emission width along the minor axis  
  > "the geometrical thickness of the CND can be inferred from the emission width along the minor axis direction" (4.1.2 Geometrical Thickness of the Circumnuclear Disk)
   - fitting: Gaussian fit per slice (sampler/priors/likelihood not stated)  
  > "Each profile is fitted with a Gaussian" (4.1.2 Geometrical Thickness of the Circumnuclear Disk)
   - validation: _not stated_
5. **Fit rotating-disk models with 3D Barolo**: 3D tilted-ring fit to CO(3-2) to get Vsys, i, PA (radial velocity fixed to 0, single plane, no warp, radii < 200 pc, ring separation 0.176 arcsec, innermost radius 0.088 arcsec); then Vsys, i, PA fixed and Barolo applied independently to the three cubes with Vrot and Vdisp free per ring  
  > "We model the kinematics of the CND in NGC 5506 using a three-dimensional tilted-ring approach with `3D BAROLO` (cite: DiTeodoro&Fraternali2015)." (4.2.1 Disk Thickness Inferred from Gas Dynamics); "At each radius, the rotational velocity ($V_{\rm rot}$) and the velocity dispersion ($V_{\rm disp}$) are treated as free parameters." (4.2.1 Disk Thickness Inferred from Gas Dynamics)
   - software: 3D Barolo
   - parameter: Radial velocity fixed to 0 km/s in the geometry fit  
  > "During this step, the radial velocity is fixed to $0$ km s$^{-1}$." (4.2.1 Disk Thickness Inferred from Gas Dynamics)
   - parameter: Fit restricted to radii < 200 pc  
  > "The fit is restricted to radii smaller than 200 pc to focus on the AGN vicinity" (4.2.1 Disk Thickness Inferred from Gas Dynamics)
   - parameter: Ring separation 0.176 arcsec  
  > "The ring separation is set to 0.176$^{\prime\prime}$, comparable to the major-axis FWHM of the CO(3–2) synthesized beam." (4.2.1 Disk Thickness Inferred from Gas Dynamics)
   - parameter: Innermost radius 0.088 arcsec  
  > "The innermost radius is fixed at 0.088$^{\prime\prime}$, ensuring that the first ring lies outside a single beam element." (4.2.1 Disk Thickness Inferred from Gas Dynamics)
   - assumption: Single-plane disk, no warp  
  > "A single-plane disk model is adopted with warping disabled, as no evidence for a warped disk has been reported in NGC 5506." (4.2.1 Disk Thickness Inferred from Gas Dynamics)
   - assumption: Vdisp/Vrot proxies H/R under hydrostatic equilibrium  
  > "Under the assumption of hydrostatic equilibrium, this ratio serves as a proxy for the disk scale height-to-radius ratio" (4.2.1 Disk Thickness Inferred from Gas Dynamics)
   - fitting: 3D BAROLO tilted-ring fit (optimizer, priors and likelihood not stated)  
  > "using a three-dimensional tilted-ring approach with `3D BAROLO`" (4.2.1 Disk Thickness Inferred from Gas Dynamics)
   - validation: Vsys, i and PA agree with Esposito et al. 2024 (1872 km/s, 80 deg, 265 deg)  
  > "consistent with the values reported by (cite: Esposito2024) ($V_{\rm sys}=1872$ km s$^{-1}$, $i=80^{\circ}$, and PA$=265^{\circ}$)" (4.2.1 Disk Thickness Inferred from Gas Dynamics)
6. **Derive mean radial (outflow) velocity**: Refit with a constant outward radial velocity Vout stepped from 0 to 40 km/s in 10 km/s steps; choose Vout minimising the residual rms  
  > "We therefore include a constant outward radial velocity (hereafter outflow velocity, $V_{\rm out}$) and repeat the fitting with $V_{\rm out}$ values from 0 to 40 km s$^{-1}$ in steps of 10 km s$^{-1}$." (4.2.2 Radial Velocity)
   - software: 3D Barolo
   - parameter: Vout grid 0-40 km/s, step 10 km/s  
  > "values from 0 to 40 km s$^{-1}$ in steps of 10 km s$^{-1}$" (4.2.2 Radial Velocity)
   - fitting: Grid search over Vout minimising residual rms  
  > "including the optimal outflow that minimizes the residual rms" (4.2.2 Radial Velocity)
   - validation: CO(3-2) Vout consistent with Esposito et al. 2024  
  > "The optimal outflow velocity of CO(3–2) is consistent with the value reported by (cite: Esposito2024)." (4.2.2 Radial Velocity)
7. **Map the [C I](1-0)/CO(3-2) line ratio and compare with the [O III] bicone**: Ratio of moment 0 maps on a brightness temperature scale; mean ratio over the CND and inside/outside the HST [O III] bicone (Fischer et al. 2013 model)  
  > "from the moment 0 maps." (4.3 [C I](1-0)/CO(3-2) Line Ratio); "on a brightness temperature scale." (4.3 [C I](1-0)/CO(3-2) Line Ratio); "summarizes the mean $R_{\rm [C~I]/CO}$ for the entire CND and for regions inside and outside the bicone." (4.3 [C I](1-0)/CO(3-2) Line Ratio)
   - assumption: Elevated ratio interpreted as CO dissociation by the AGN-driven ionized outflow; southern cone not detected in HST because of obscuration  
  > "This suggests that CO is preferentially dissociated at the interface where the ionized outflow interacts with the CND." (4.3 [C I](1-0)/CO(3-2) Line Ratio)
   - fitting: _not stated_
   - validation: Qualitative comparison with the NGC 1068 [C I]/CO(1-0) vs [S III]/[S II] correlation (Saito et al. 2022)  
  > "consistent with the scenario proposed here for NGC 5506." (4.3 [C I](1-0)/CO(3-2) Line Ratio)
8. **Derive molecular gas mass and column density**: CO(3-2) line luminosity from the moment 0 map, converted to H2 mass with alpha_CO = 0.8 Msun (K km/s pc^2)^-1, assuming CO(3-2) thermalised with CO(2-1)  
  > "L^\prime_{\rm CO(3-2)}=3.25\times10^7S_{\rm CO(3-2)}\Delta v~\nu^{-2}_{\rm obs}D_{\rm L}^2(1+z)^{-3}," (Molecular Gas Mass and Column Density); "The H$_2$ gas mass and column density are derived from the moment 0 map of CO(3–2), following (cite: Izumi2018)." (Molecular Gas Mass and Column Density)
   - parameter: M_H2/L'_CO = 0.8 Msun (K km/s pc^2)^-1  
  > "we adopt the canonical CO-to-H$_2$ conversion factor for active environments $M_{\rm H_{2}} / L^{\prime}_{\rm CO} = 0.8 M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$ (cite: Downes&Solomon1998)" (Molecular Gas Mass and Column Density)
   - assumption: CO(3-2) thermalised with CO(2-1)  
  > "Assuming CO(3–2) emission is thermalized with that of CO(2–1) (cite: Solomon&Bout2015)" (Molecular Gas Mass and Column Density)
   - fitting: _not stated_
   - validation: _not stated_
9. **Compare observed H/R and velocity dispersion with SN-driven turbulence and fountain models**: Convert model f_obs to H/R via H/R = f_obs/sqrt(1 - f_obs^2); evaluate the Kawakatu et al. 2020 turbulent velocity v_t with SFR, M_gas, M_BH and compare with observed Vdisp at r ~100 pc  
  > "via the relation $H/R=f_{\rm obs}$/$\sqrt{(1-f_{\rm obs}^2})$." (4.4 Interpretation); "where $C_\ast=\mathrm{star\ formation\ rate\ (SFR)}/M_{\rm gas}$ is the star formation efficiency" (4.4 Interpretation)
   - parameter: SFR = 0.3 (+0.7/-0.2) Msun/yr; M_gas = (4.1 +/- 0.6)e7 Msun; M_BH = 2.0e7 Msun  
  > "and the molecular gas mass ($M_{\rm gas}$) is  $(4.1\pm 0.6)\times10^{7}~M_\odot$" (4.4 Interpretation)
   - assumption: Fountain flow in NGC 5506 less prominent than simulated because Eddington ratio is lower and BH mass higher than the simulation values  
  > "These differences suggest that the fountain flow in NGC 5506 is likely less prominent than in the simulation" (4.4 Interpretation)
   - fitting: _not stated_
   - validation: v_t ~30 km/s at r~100 pc is consistent with observed Vdisp = 20-40 km/s; agreement less robust at other radii  
  > "This is consistent with the observed velocity dispersion of \[C I\](1–0) and CO(3–2), $V_{\rm disp}=20\text{--}40~\mathrm{km~s^{-1}}$." (4.4 Interpretation); "the agreement between $v_{\rm t}$ and $V_{\rm disp}$ is less robust at radii other than 100 pc." (4.4 Interpretation)

## Software

- **CASA** 6.5.6: Imaging of calibrated data (tclean)  
  > "Calibrated data were imaged using CASA (version 6.5.6) task `tclean` with a channel width of 20 km s$^{-1}$." (2.1 ALMA)
- **ALMA pipeline** 2022.2.0.68 ([C I]); Pipeline-CASA51-P2-B (CO, HCO+): Calibration of the ALMA data  
  > "Calibration was performed using the ALMA pipeline in Common Astronomy Software Applications (cite: Casa2022)" (2.1 ALMA)
- **3D Barolo** : 3D tilted-ring kinematic modelling (Vsys, i, PA, Vrot, Vdisp, Vout)  
  > "We model the kinematics of the CND in NGC 5506 using a three-dimensional tilted-ring approach with `3D BAROLO` (cite: DiTeodoro&Fraternali2015)." (4.2.1 Disk Thickness Inferred from Gas Dynamics)
- **photutils (DAOStarFinder)** 1.12.0 (reference list): Centroids of astrometric reference stars in the HST image  
  > "Centroids of both stars were measured using `DAOStarFinder` from the `photutils` package (cite: Bradley2024)." (2.2 HST); "(ref: Bradley2024) Bradley, L., Sipőcz, B., Robitaille, T., et al. 2024, Zenodo, 1.12.0." (References)
- **SExtractor** : Measuring the PSF FWHM of the [O III] image  
  > "was measured using `SExtractor` (cite: Bertin1996) by fitting a point source at" (2.2 HST)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Systemic velocity Vsys (CO 3-2 fit) | 1872 | 10 | km/s | 5 | determined by fitting a rotating disk model to CO(3–2) data ($1872\pm10$ km s$^{-1}$ |
| Disk inclination i and position angle PA | i = 79 deg, PA = 268 deg | not stated | deg | 5 | The fit yields $V_{\rm sys}$ = 1872 km s$^{-1}$, $i=79^{\circ}$, and PA $=268^{\circ}$ |
| Flux-weighted mean velocity at AGN ([C I], CO 3-2, HCO+ 4-3) | 1859, 1865, 1889 | 10 each | km/s | 3 | At the AGN position, the flux-weighted mean line-of-sight velocities are $1859\pm10$ km s$^{-1}$, $1865\pm10$ km s$^{-1}$, and $1889\pm10$ km s$^{-1}$ for |
| Major-axis intensity peak positions (east/west) in [C I], CO(3-2), HCO+(4-3) | 21 and 64 pc; 35 and 60 pc; 5 and 51 pc | 9 pc each | pc | 3 | at $21\pm9$ pc and $64\pm9$ pc for \[C I\](1–0), $35\pm9$ pc and $60\pm9$ pc for CO(3–2), and $5\pm9$ pc and $51\pm9$ pc for HCO$^{+}$(4–3) |
| Maximum minor-axis FWHM, [C I] and CO(3-2) vs HCO+(4-3) | >~80 pc ([C I], CO); ~50 pc (HCO+) | not stated | pc | 4 | Both \[C I\](1–0) and CO(3–2) reach maximum FWHM values of $\gtrsim 80$ pc, whereas HCO$^{+}$(4–3) forms a thinner disk with a maximum FWHM of $\sim 50$ pc. |
| Vdisp/Vrot at innermost radius ([C I], CO 3-2) | >~0.9 | not stated | dimensionless | 5 | The ratio reaches particularly high values ($\gtrsim 0.9$) at the innermost radius for both |
| Optimal outflow velocity Vout ([C I], CO 3-2, HCO+ 4-3) | 20, 30, 20 | 5 each | km/s | 6 | The optimal outflow velocities are 20$~\pm~5$ km s$^{-1}$ for \[C I\](1–0), 30$~\pm~5$ km s$^{-1}$ for CO(3–2), and 20$~\pm~5$ km s$^{-1}$ for HCO$^{+}$(4–3). |
| Mean [C I](1-0)/CO(3-2) ratio over the CND | 0.52 | 0.07 | dimensionless | 7 | The mean ratio across the entire CND is $0.52\pm0.07$ |
| Mean [C I](1-0)/CO(3-2) ratio inside / outside the bicone | 0.82 inside; 0.47 outside | 0.11; 0.07 | dimensionless | 7 | The mean ratio inside the bicone ($0.82\pm0.11$) is higher than that outside the bicone ($0.47\pm0.07$). |
| Total molecular hydrogen mass of the CND | 4.1e7 | 0.6e7 | Msun | 8 | The resulting total molecular hydrogen mass is $M_{\rm H_2}=(4.1\pm 0.6)\times10^7$ $M_\odot$ |
| Mean H2 column density | 4.3e22 | 0.6e22 | cm^-2 | 8 | the mean column density is $N_{H_2}=(4.3 \pm 0.6)\times10^{22}$ cm$^{-2}$. |
| Predicted SN-driven turbulent velocity at r ~100 pc | ~30 | not stated | km/s | 9 | The predicted turbulent velocity is $v_{\rm t}\sim30~\mathrm{km~s^{-1}}$ at $r\sim100$ pc. |
| Observed velocity dispersion of [C I] and CO(3-2) | 20-40 | not stated | km/s | 5 | $V_{\rm disp}=20\text{--}40~\mathrm{km~s^{-1}}$ |
| Astrometric accuracy of the corrected HST image | <0.2 | not stated | arcsec | 2 | resulting in an astrometric accuracy better than 0$\ensuremath{''}$.2 |

## Qualitative findings

- [C I](1-0) and CO(3-2) have comparable geometrical thickness and velocity structure, while HCO+(4-3) is more concentrated toward the disk plane  
  > "No significant differences in geometrical thickness or velocity structure are found between" (abstract)
- The CND is dominated by rotation; western side redshifted, eastern side blueshifted; HCO+ at the AGN is redshifted by ~17 km/s, possibly inflow  
  > "In all three tracers, the western side is redshifted, and the eastern side is blueshifted, consistent with rotational motion." (3.3 Velocity structure)
- Elevated [C I]/CO regions correlate spatially with the HST [O III] bicone, suggesting CO dissociation by the AGN-driven ionized outflow  
  > "suggesting that CO is preferentially dissociated by the AGN-driven biconical ionized outflow." (abstract)

## Claim tuples

- H: Do atomic and molecular gas differ in geometrical thickness in the NGC 5506 CND, as predicted by the radiation-driven fountain model? | E: Gaussian FWHM of minor-axis slices of moment 0 maps and Vdisp/Vrot from 3D Barolo for [C I](1-0), CO(3-2) and HCO+(4-3) at ~20 pc resolution | R: [C I] and CO FWHM differ by less than a factor of 2 with no systematic trend and similar Vdisp/Vrot; HCO+ is thinner (max FWHM ~50 pc vs >~80 pc) | F: [C I] and CO have comparable thickness; only the dense gas tracer HCO+ is more concentrated toward the disk plane | **supported**
- H: Is the inner CND geometrically thick? | E: Vdisp/Vrot as proxy for H/R from 3D Barolo fits | R: Vdisp/Vrot >~0.9 at the innermost radius (<~30 pc) for [C I] and CO(3-2) | F: Both tracers indicate geometrically thick structures in the central region, thicker than reported for Circinus | **supported**
- H: Is CO preferentially dissociated by the AGN-driven ionized outflow? | E: Mapped [C I](1-0)/CO(3-2) from moment 0 maps and compared with the HST [O III] bicone | R: Mean ratio 0.82 +/- 0.11 inside the bicone vs 0.47 +/- 0.07 outside (CND mean 0.52 +/- 0.07) | F: Ratio is elevated within the bicone, suggesting CO dissociation at the outflow-CND interface (mechanism is plausible, not tested) | **partially**
- H: Does SN-driven turbulence provide the vertical support of the CND? | E: Compared observed H/R and Vdisp with the Kawakatu et al. 2020 model using SFR, M_gas and M_BH | R: Model f_obs >~0.6 gives H/R ~0.9; predicted v_t ~30 km/s at 100 pc vs observed Vdisp 20-40 km/s, with radial dependence differing between model and data | F: Order-of-magnitude consistency supports SN-driven turbulence as the dominant vertical support | **partially**

## Reasoning

- Why this data: Edge-on CND increases sensitivity to thickness differences among gas phases  
  > "The circumnuclear disk (CND) of NGC 5506 is viewed at a nearly edge-on inclination, which enhances the sensitivity to differences in geometrical thickness among multiple gas phases." (Introduction)
- Why this method: Briggs robust tuned so all three lines have comparable beams, since thicknesses are compared  
  > "Because this study compares geometrical thicknesses among different gas phases, the Briggs `robust` parameter was adjusted to synthesize comparable beam sizes across all three lines." (2.1 ALMA)
- Alternative: AGN X-ray irradiation likely contributes to CO dissociation but cannot explain the nonaxisymmetric distribution of elevated [C I]/CO, so the outflow-interaction scenario is favoured  
  > "it cannot account for the nonaxisymmetric distribution of the elevated $R_{\rm [C~I]/CO}$ regions." (4.3 [C I](1-0)/CO(3-2) Line Ratio)
- Alternative: Radiation-driven fountain flow likely not stably established in NGC 5506 given its Eddington ratio and BH mass  
  > "suggest that a stable radiation-driven fountain flow may not be established." (Conclusion)
- How they decided it was enough: _not stated_
- Limitation (authors): Quoted errors are statistical only  
  > "Throughout this paper, error values represent only statistical uncertainties unless otherwise noted." (2.1 ALMA)
- Limitation (authors): HST [O III] dataset covers only the northern side of the emission; southern cone undetected  
  > "The dataset covers only the northern side of the emission (cite: Ruiz2005)." (2.2 HST)
- Limitation (authors): Agreement between model v_t and observed Vdisp is less robust away from 100 pc  
  > "the agreement between $v_{\rm t}$ and $V_{\rm disp}$ is less robust at radii other than 100 pc." (4.4 Interpretation)
- Caveat (inferred, ours): Vdisp/Vrot as H/R proxy ignores beam smearing, inclination (79 deg) mixing and non-thermal/non-circular motions; no beam-smearing test is described
- Caveat (inferred, ours): Conclusions on [C I] vs CO thickness rely on matched beams tuned by robust, which gives different uv weighting per line (Band 8 vs Band 7 sampling) and may bias thickness
- Caveat (inferred, ours): Single-trial Vout grid with coarse 10 km/s steps and ~5 km/s uncertainty; model-dependent
- Caveat (inferred, ours): Line ratio inside/outside bicone depends on HST registration (0.2 arcsec) and FOC covering only the northern cone
- Caveat (inferred, ours): Model comparison with Kawakatu et al. 2020 is order-of-magnitude with large BH mass and SFR uncertainties (BH mass spans a factor ~10)
- Caveat (inferred, ours): CO(3-2) mass assumes alpha_CO = 0.8 and thermalised CO(3-2)/CO(2-1); no uncertainty propagated from alpha_CO

## Reproducibility

- Data public (paper): HST data in MAST; ALMA CO and HCO+ data are archival Band 7 (project 2017.1.00082.S); Band 8 data are from project 2022.1.00410.S (public status not stated)  
  > "CO(3–2) and HCO$^{+}$(4–3) were obtained from archival Band 7 observations." (2.1 ALMA); "*HST* data analyzed in this paper can be found in MASTat ." (Acknowledgments)
- Products in archive: _not stated_
- Missing: tclean parameters beyond robust, nsigma and channel width (cell size, imsize, spw/rest frequency, niter, other automasking settings)
- Missing: Continuum subtraction and line-free channels
- Missing: 3D Barolo configuration and version, and how uncertainties are derived
- Missing: Definition of the bicone mask and the HST-to-ALMA registration used for the line-ratio regions
- Missing: Moment-map integration ranges and noise estimates
- Data volume (inferred): Roughly 50-200 GB of raw ALMA data across the two projects; calibrated cubes a few GB
- Score (inferred): 3/5, Data projects and key imaging parameters (robust, nsigma, 20 km/s channels, CASA 6.5.6) and Barolo setup are given with numeric results, but many tclean, continuum subtraction and mask details are missing and Band 8 data status is not stated.
- Rediscovery candidate: no, Public status of the Cycle 9 Band 8 data is not stated and several imaging and Barolo settings are missing, so the recipe is not complete enough to redo the main results.

## Links

- Method: (cite: DiTeodoro&Fraternali2015) (3D Barolo tilted-ring fitting code)
- Method: (cite: Casa2022) (CASA and ALMA pipeline calibration/imaging)
- Method: (cite: Izumi2018) (Method for H2 gas mass and Vdisp/Vrot proxy for H/R)
- Companion: (cite: Esposito2024) (Reported Vsys, i, PA, outflow velocity and Eddington ratio for NGC 5506 used for comparison)
- Companion: (cite: Izumi2018) ([C I](1-0) and CO(3-2) study of the Circinus galaxy used as comparison for H/R)
- Companion: (cite: Fischer2013) ([O III] biconical outflow model of NGC 5506)
- Companion: (cite: Kawakatu2020) (SN-driven turbulence model compared with the observations)
- Related: ALMA 2017.1.00082.S
- Related: ALMA 2022.1.00410.S
- Related: HST program 5144

## Checks

```json
{
 "quotes": 154,
 "quotes_ok": 154,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 119,
  "stated": 92,
  "rate": 0.773
 },
 "evidence_ok": true
}
```
