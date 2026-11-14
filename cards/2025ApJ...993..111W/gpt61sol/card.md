# A Multiwavelength Study of ELAN Environments (AMUSE<SUP>2</SUP>): The Impact of Dense Environment on Massive Dusty Star-forming Galaxies at Cosmic Noon

`2025ApJ...993..111W` | The Astrophysical Journal 2025 | first author: Wang, Yu-Jan | arXiv: 2509.03027 | DOI: 10.3847/1538-4357/adff7d

Card schema 1.0 | model gpt-6.1-sol | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: Determine SMG redshifts and association with quasars, and test environmental impacts on molecular gas and dust properties.  
  > "The ultimate goal is to determine their redshifts (hence association with the quasars) and quantify their ISM properties (e.g., molecular gas and dust content) to verify the presence of any environmental impact on the evolution of such galaxies." (Introduction)
- Target **Submillimeter sources around nine quasars hosting Lyα nebulae**: coordinates _not stated_; z/distance z=2~3  
  > "These observations target submillimeter sources discovered in single-dish surveys around nine quasars hosting Ly$\alpha$ nebulae at $z=2\sim3$, including two Enormous Ly$\alpha$ nebulae (ELANe)." (abstract); "In total we target 91 objects around eight quasar fields with known Ly$\alpha$ extended emission." (ALMA); distance from _not stated_
- Target **Q2355**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **SDSSJ0819**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **SDSSJ1020 and SDSSJ1209**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2019.1.01514.S
- bands: band 3 (6 fields); band 4 (2 fields)  
  > "Since the central quasars are located at $z=2-3$, these spectral windows are in band 3 (for 6 fields) and band 4 (for 2 fields)." (ALMA)
- frequencies and spectral setup: Four spectral windows: one tuned to central-quasar CO(4-3), three continuum; USB and LSB cubes with 256 channels each; 15 MHz channels.  
  > "one window tuned to the redshift of the central quasar to search for the CO(4-3) emission line of the SMGs, and the other three windows capturing their continuum." (ALMA); "Both sidebands contain 256 channels." (ALMA); "per channel of 15 MHz ($\sim$40 km s$^{-1}$)." (ALMA)
- continuum bandwidth: _not stated_
- arrays: 36 to 46 12-meter antennas  
  > "Data were taken with 36 to 46 12-meter antennas, and the baselines ranged from 15.0 to 783.5 meters." (ALMA)
- configurations: _not stated_
- baselines: 15.0 to 783.5 meters  
  > "Data were taken with 36 to 46 12-meter antennas, and the baselines ranged from 15.0 to 783.5 meters." (ALMA)
- angular resolution: Major axis: ~2.0''–4.3'' USB; ~2.2''–4.7'' LSB; continuum averages USB and LSB.  
  > "ranged from $\sim$2.0$''$ - 4.3$''$ for USB, and $\sim$2.2$''$ - 4.7$''$ for LSB." (ALMA); "The spatial resolution of the continuum is the average value between the USB and LSB." (ALMA)
- max recoverable scale: _not stated_
- sensitivity: ~40 μJy beam−1 continuum; ~0.4 mJy beam−1 per 15 MHz (~40 km s−1) channel  
  > "The final cleaned continuum image has a sensitivity (1-$\sigma$ noise level) of $\sim40\,\mu$Jy beam$^{-1}$" (ALMA); "the mean sensitivity for the cleaned image cube is $\sim0.4$ mJy beam$^{-1}$ per channel of 15 MHz ($\sim$40 km s$^{-1}$)." (ALMA)
- time on source: Approximately 40 to 60 minutes per EB; about 6 hours total  
  > "For each execution block (EB), the total on-source time (ToS) is approximately 40 to 60 minutes, totaling about 6 hours, as reported in the QA2 report." (ALMA)
- observing dates: November 2019 to January 2020  
  > "The ALMA observations for this work were carried out from November 2019 to January 2020 (PID: 2019.1.01514.S )." (ALMA)
- pi or archival as stated: _not stated_
- Line: CO 4-3 (not stated)
- Line: CO 3-2 (not stated)
- Other facility **NOEMA**: Compact (9D), 10-antenna observations; CO(3-2) and continuum.  
  > "NOEMA observations were secured on June 13, 16 and 24 2019 using the compact (9D) configuration array, with 10 antennas, as part of the S19CK program (PI: F. Arrigoni Battaia)." (NOEMA); "Given the redshifts of the central quasars, we identify these line detections to be most likely CO(4-3) from ALMA and CO(3-2) from NOEMA." (Line extraction from spectral datacubes); "ALMA at 3 mm or NOEMA at 2 mm." (Continuum)
- Other facility **JCMT/SCUBA-2**: Archival 450 and 850 μm maps; original target selection.  
  > "To aid our analyses, we make use of the SCUBA-2 archival data at both 450 and 850 $\mu$m." (JCMT/SCUBA-2); "The target submillimeter sources were selected as significant detections (SNR$\ge4.5$) in the original SCUBA-2 survey that targeted $z\sim2-3$ ELAN and quasar fields ((cite: Nowotka2022; FAB2023))." (ALMA)
- Other facility **Herschel/SPIRE**: 250, 350 and 500 μm photometry for Q2355 and SDSSJ0819.  
  > "Additionally, we used the public Herschel data for Q2355 and SDSSJ0819 at 250 $\mu$m, 350 $\mu$m, 500 $\mu$m." (Continuum)
- Other facility **ESA Herschel Science Archive**: Pipeline-reduced Herschel level-2 maps at 250, 350 and 500 μm.  
  > "We retrieved the data from the ESA Herschel Science Archive, and we simply used the level-2 map reduced by the pipeline from the archive at 250, 350, and 500 $\mu$m." (Herschel)
- External data: Original SCUBA-2 source surveys used to select ALMA targets.  
  > "The target submillimeter sources were selected as significant detections (SNR$\ge4.5$) in the original SCUBA-2 survey that targeted $z\sim2-3$ ELAN and quasar fields ((cite: Nowotka2022; FAB2023))." (ALMA) [from (cite: Nowotka2022; FAB2023)]
- External data: SCUBA-2 number counts for estimating excess sources and expected detection rates.  
  > "based on the number count measurements reported by (cite: FAB2023), we calculate the excess number of sources relative to the field (cite: 2017MNRAS.465.1789G) based on the survey area." (Detection rate) [from (cite: FAB2023); (cite: 2017MNRAS.465.1789G)]
- External data: Protocluster relative-velocity dispersion used to motivate membership limits.  
  > "According to previous studies in protocluster environment ((cite: 2021A&A...652A..11J); (cite: 2024arXiv240616637W)), the standard deviation of relative velocity between central QSO and the member galaxies is $\sim$ 2500 km/s." (Line extraction from spectral datacubes) [from (cite: 2021A&A...652A..11J); (cite: 2024arXiv240616637W)]
- External data: Minimum SMG line width (~180 km/s) used to reject narrow detections.  
  > "After removing spikes detections that have FWHM values below the minimum ($\sim$180 km/s) of the reported lines for SMGs in the literature (cite: 2021MNRAS.501.3926B)" (Line extraction from spectral datacubes) [from (cite: 2021MNRAS.501.3926B)]
- External data: Field-SMG redshift probability distribution used for alternative CO identifications.  
  > "based on the redshift-dependent probability distribution of field SMGs reported by (cite: 2016ApJ...820...82C)" (CO Luminosity Function) [from (cite: 2016ApJ...820...82C)]
- External data: CO excitation ratios r31=0.63±0.12 and r41=0.34±0.04.  
  > "using the relationship described by (cite: 2021MNRAS.501.3926B): $L'_{\rm CO(1-0)}=L'_{\rm CO}/r_{j1}$, with $r_{31}= 0.63\pm0.12$ ; $r_{41}= 0.34\pm0.04$ ." (Line extraction from spectral datacubes) [from (cite: 2021MNRAS.501.3926B)]
- External data: COSMOS super-deblended catalog and deblended Herschel fluxes.  
  > "We consider the COSMOS super-deblended catalog reported by (cite: 2018ApJ...864...56J)" (Continuum); "calculate the median ratio between the extracted flux and the deblended flux provided in the catalog." (Continuum) [from (cite: 2018ApJ...864...56J)]
- External data: SCUBA-2 maps used to estimate 450 and 850 μm deblending ratios.  
  > "The same steps are applied to the SCUBA-2 maps to obtain the deblending ratios at 450 $\mu$m and 850 $\mu$m (cite: 2024ApJ...971..117G)." (Continuum) [from (cite: 2024ApJ...971..117G)]
- External data: Three field-SMG comparison samples.  
  > "we made comparisons with mainly three field SMG samples (cite: 2020MNRAS.494.3828D; 2021MNRAS.501.3926B; 2024ApJ...961..226L)" (Molecular Gas and Dust Properties) [from (cite: 2020MNRAS.494.3828D; 2021MNRAS.501.3926B; 2024ApJ...961..226L)]
- External data: Field-SMG luminosity and line-width distribution used for detection bias ratios.  
  > "Based on the distribution of luminosity and line width of SMGs in the field (cite: 2021MNRAS.501.3926B), we calculate the fraction of sources that would have been detected given our sensitivity limits." (Detection rate) [from (cite: 2021MNRAS.501.3926B)]
- External data: DSFG/SMG measurements at hundred-kpc to Mpc distances from quasars.  
  > "we included some ALMA-identified DSFG/SMGs samples located in the vicinity of quasars with distance ranged from hundred kpc to Mpc scales (cite: 2021ApJ...923..200C; 2022ApJ...930...72A; Garcia2022; Li2023; 2024A&A...684A.119P; 2024arXiv240616637W)" (Gas mass fraction) [from (cite: 2021ApJ...923..200C; 2022ApJ...930...72A; Garcia2022; Li2023; 2024A&A...684A.119P; 2024arXiv240616637W)]
- External data: Plane-of-sky filament rotation angles.  
  > "We therefore adopted the rotation angles of the filament on the plane-of-sky, $\alpha$, derived from 2D spatial distribution reported by (cite: FAB2023)" (Spatial Distribution) [from (cite: FAB2023)]
- External data: 18 spectroscopically confirmed SMGs around HS 1549+19 at z=2.85.  
  > "another sample of 18 SMGs that are spectroscopically confirmed to be associated with a $z = 2.85$ proto-cluster hosted by the quasar HS 1549+19 (cite: 2024arXiv240616637W)" (Spatial Distribution) [from (cite: 2024arXiv240616637W)]
- External data: FOREVER22 cumulative-SFR and SFRD predictions and comparison volumes.  
  > "we first make use of a cosmological hydrodynamical simulation called FOREVER22 (cite: 2022MNRAS.509.4037Y)." (Cumulative SFR); "a projected depth of 28.6 cMpc and a volume of (25.7 cMpc$)^3$, for cumulative SFRs and SFRDs, respectively (cite: 2022MNRAS.509.4037Y)." (Cumulative SFR) [from (cite: 2022MNRAS.509.4037Y)]
- External data: Observational protocluster SFR measurements for comparison.  
  > "observational studies are also used for comparison with our results (cite: Clements2014; kato2016; 2015ApJ...808L..33C; 2016ApJ...826..130H; 2018ApJ...856...72O; 2014A&A...570A..55D; 2024arXiv240616637W; 2018Natur.556..469M)." (Cumulative SFR) [from (cite: Clements2014; kato2016; 2015ApJ...808L..33C; 2016ApJ...826..130H; 2018ApJ...856...72O; 2014A&A...570A..55D; 2024arXiv240616637W; 2018Natur.556..469M)]
- External data: ASPECS and HDFN CO luminosity functions.  
  > "they are widely consistent with previous surveys in the field, e.g., ASPECS (cite: 2020ApJ...902..110D) and HDFN (cite: 2023ApJ...945..111B)." (CO Luminosity Function) [from (cite: 2020ApJ...902..110D); (cite: 2023ApJ...945..111B)]
- Simulation/model as data: FOREVER22 cosmological hydrodynamical simulation: comparison cumulative SFRs and SFRDs.  
  > "we first make use of a cosmological hydrodynamical simulation called FOREVER22 (cite: 2022MNRAS.509.4037Y)." (Cumulative SFR); "the simulation provides predictions for cumulative SFRs and total SFRDs around haloes with masses comparable to those of quasars ($\sim 10^{13}~M_\odot$) at $z = 3$." (Cumulative SFR)
- Simulation/model as data: NFW halo potential for escape-velocity curves.  
  > "we calculate the escape velocity of quasar halos assuming an NFW halo potential ((cite: 1996ApJ...462..563N))" (Gas mass fraction)

## Processing

### Calibration

- pipeline or manual: Run corresponding SCRIPTFORPI.PY scripts on raw visibilities; adopt QA2 calibrations.  
  > "For data reduction, we calibrate the raw visibilities by running the corresponding SCRIPTFORPI.PY scripts under CASA5.6.1." (ALMA); "This means that the calibrations performed by the QA2 team members are adopted." (ALMA)
- casa version: 5.6.1  
  > "For data reduction, we calibrate the raw visibilities by running the corresponding SCRIPTFORPI.PY scripts under CASA5.6.1." (ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: TCLEAN  
  > "Next, we apply TCLEAN to perform an inverse Fourier transformation on both the continuum and continuum-subtracted visibilities." (ALMA)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We apply natural weighting for the baselines." (ALMA)
- uv taper: _not stated_
- cell size: 0.43''  
  > "with a pixel size of 0.43$''$." (ALMA)
- image size: 240×240 pixels  
  > "The final images are transformed into 240$\times$240 pixels in R.A. and DEC. directions, respectively" (ALMA)
- masking: usemask = auto-multithresh; noisethreshold = 4; lownoisethreshold = 2.5; clean masked regions to 2σ.  
  > "we use an automasking approach in TCLEAN by setting “auto-multithresh” as the usemask parameter to increase the efficiency of CLEAN (noisethreshold = 4; lownoisethreshold = 2.5)." (ALMA); "Finally, the cubes within the masked regions are cleaned down to 2 $\sigma$ level." (ALMA)
- multiscale scales: _not stated_
- continuum subtraction: Exclude significant line-emission channels; use continuum channels for continuum generation and subtraction.  
  > "During the imaging process, we first perform continuum subtraction. Specifically, we exclude channels that include significant line emissions." (ALMA); "The continuum channels are then used for both continuum generation and subtraction." (ALMA)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: IMSMOOTH to a common resolution per cube, typically its largest pre-smoothed beam.  
  > "we apply the CASA routine IMSMOOTH to the reduced data cubes, allowing each cube to have a common resolution." (ALMA); "This common resolution is typically the largest beam size of the pre-smoothed cube." (ALMA)
- final beam: Major axis: ~2.0''–4.3'' USB; ~2.2''–4.7'' LSB.  
  > "ranged from $\sim$2.0$''$ - 4.3$''$ for USB, and $\sim$2.2$''$ - 4.7$''$ for LSB." (ALMA)
- final rms: ~40 μJy beam−1 continuum; ~0.4 mJy beam−1 per 15 MHz (~40 km s−1) channel.  
  > "The final cleaned continuum image has a sensitivity (1-$\sigma$ noise level) of $\sim40\,\mu$Jy beam$^{-1}$" (ALMA); "the mean sensitivity for the cleaned image cube is $\sim0.4$ mJy beam$^{-1}$ per channel of 15 MHz ($\sim$40 km s$^{-1}$)." (ALMA)

### Inherited from earlier work

- SCUBA-2 target selection.  
  > "The target submillimeter sources were selected as significant detections (SNR$\ge4.5$) in the original SCUBA-2 survey that targeted $z\sim2-3$ ELAN and quasar fields ((cite: Nowotka2022; FAB2023))." (ALMA) [from (cite: Nowotka2022; FAB2023)]
- TCLEAN automasking imaging method.  
  > "Following the imaging method described in (cite: 2022ApJ...929..159C), we use an automasking approach in TCLEAN" (ALMA) [from (cite: 2022ApJ...929..159C)]
- SCUBA-2 archival-data details.  
  > "The details of these data can be found in (cite: FAB2023)." (JCMT/SCUBA-2) [from (cite: FAB2023)]
- SCUBA-2 data reduction.  
  > "We perform data reduction following (cite: 2024ApJ...971..117G)" (JCMT/SCUBA-2) [from (cite: 2024ApJ...971..117G)]
- AICc selection of single versus double Gaussian models.  
  > "To determine if the spectra are better fit by a single Gaussian or double Gaussian model, we employed the Akaike information criterion (AICc) (as detailed in (cite: 2022ApJ...929..159C))." (Line extraction from spectral datacubes) [from (cite: 2022ApJ...929..159C)]
- Curve-of-growth spectral-aperture analysis.  
  > "To derive the total flux intensity, we follow the curve-of-growth analyses performed in the case with other ALMA data sets (cite: 2022ApJ...929..159C)." (Curve-of-Growth Analyses) [from (cite: 2022ApJ...929..159C)]
- CO intensity-to-luminosity conversion.  
  > "we convert them to the CO luminosity following the method outlined by (cite: 2013ARA&A..51..105C)" (Line extraction from spectral datacubes) [from (cite: 2013ARA&A..51..105C)]
- CO(3-2) and CO(4-3) conversion to CO(1-0).  
  > "using the relationship described by (cite: 2021MNRAS.501.3926B): $L'_{\rm CO(1-0)}=L'_{\rm CO}/r_{j1}$, with $r_{31}= 0.63\pm0.12$ ; $r_{41}= 0.34\pm0.04$ ." (Line extraction from spectral datacubes) [from (cite: 2021MNRAS.501.3926B)]
- Single-temperature modified-blackbody SED model.  
  > "we adopt a single temperature modified black-body (MBB) as usually done in the literature (cite: 2012MNRAS.425.3094C; 2021ApJ...919...30D)" (SED Fitting) [from (cite: 2012MNRAS.425.3094C; 2021ApJ...919...30D)]
- Fixed β=2.0 baseline SED fits.  
  > "We simply fixed $\beta = 2.0$, representing the usual condition for dusty galaxies (e.g., (cite: 2021ApJ...923..215C; 2021ApJ...919...30D; Cooper:2022aa; 2024ApJ...961..226L))." (SED Fitting) [from (cite: 2021ApJ...923..215C; 2021ApJ...919...30D; Cooper:2022aa; 2024ApJ...961..226L)]
- Fixed β=1.8 for the dust-temperature comparison.  
  > "Because (cite: 2020MNRAS.494.3828D) adopted a fixed $\beta$ = 1.8, to make a fair comparison, the results plotted in this figure are based on the same assumption of $\beta$." (Dust properties) [from (cite: 2020MNRAS.494.3828D)]
- Dynamical gas-fraction estimator; re=3 kpc, αCO=1.0 and fDM=0.12.  
  > "Following (cite: 2021ApJ...923..200C), we set the half-light radius to $r_{e}$= 3 kpc, $\alpha_{\rm CO}$= 1.0, and dark matter fraction as $f_{\rm DM}$ = 0.12, based on recent measurements." (Gas mass fraction) [from (cite: 2021ApJ...923..200C)]
- αCO=1.0 for gas masses and depletion times.  
  > "we calculate $M_{gas}$ by adopting $\alpha_{\rm CO} = 1.0$, same as the value adopted by studies of field SMGs (cite: 2021MNRAS.501.3926B)." (Depletion timescale) [from (cite: 2021MNRAS.501.3926B)]
- Infrared-luminosity-to-SFR calibration.  
  > "${\rm log(SFR\,[M_{\odot}\,yr^{-1}]) = log(}\rm L_{IR}\,[\rm erg/s])-43.41$$ , given by (cite: Kennicut2012)." (Depletion timescale) [from (cite: Kennicut2012)]
- NFW potential and halo concentration c=3.5 for escape velocities.  
  > "we calculate the escape velocity of quasar halos assuming an NFW halo potential ((cite: 1996ApJ...462..563N))" (Gas mass fraction); "$c$ is the concentration ($c = 3.5$; (cite: 2018MNRAS.479.3879W); (cite: 2014MNRAS.441.3359D))" (Gas mass fraction) [from (cite: 1996ApJ...462..563N); (cite: 2018MNRAS.479.3879W); (cite: 2014MNRAS.441.3359D)]
- Filament rotation angles and exponential distance-distribution model.  
  > "We therefore adopted the rotation angles of the filament on the plane-of-sky, $\alpha$, derived from 2D spatial distribution reported by (cite: FAB2023)" (Spatial Distribution); "According to (cite: FAB2023), the empirical probability distribution (ePDF) of $|y|$ (distance to the x-axis) of each SMG in the quasar fields is related to the width of the filament by this formula:" (Spatial Distribution) [from (cite: FAB2023)]
- Simulation-matched depth and volume for cumulative SFR and SFRD.  
  > "a projected depth of 28.6 cMpc and a volume of (25.7 cMpc$)^3$, for cumulative SFRs and SFRDs, respectively (cite: 2022MNRAS.509.4037Y)." (Cumulative SFR) [from (cite: 2022MNRAS.509.4037Y)]
- Planck cosmology: H0=67.8 km s−1 Mpc−1, Ω_MΛ=0.307, ΩΛ=0.69.  
  > "Throughout this paper, we assume the Planck cosmology: $H_0$ = 67.8 $km s^{-1} Mpc^{-1}$ , $\Omega_MΛ$ = 0.307, and $\Omega_\Lambda$ = 0.69 (cite: 2014A&A...571A..16P)." (Introduction) [from (cite: 2014A&A...571A..16P)]

### Not stated but needed to reproduce (our reading)

- Complete target coordinates, central-quasar redshifts and source-level measurement tables; the referenced tables are absent from the supplied text.
- Per-field spectral-window frequencies, channel grids, effective continuum frequencies and continuum bandwidths.
- Exact line-emission channel exclusions and continuum-subtraction task, fit order and settings.
- Per-field calibrators and flux-scale uncertainty; the referenced calibrator table is absent.
- Remaining TCLEAN settings, including deconvolver, spectral gridding and automask parameters.
- Whether primary-beam corrections were applied, and how spatially varying noise entered detection and photometry.
- Per-cube common-beam major/minor axes and position angles, and spectral-noise covariance after processing.
- LINESEEKER version, search-kernel settings, SNR normalization and duplicate-detection handling.
- Injected-line width and intensity grids, sampling distributions and random seeds.
- Gaussian-fit optimizer, parameter bounds, noise model, AICc implementation and uncertainty propagation.
- Per-band deblending factors and exact COSMOS comparison-source selection.
- SED-fitting software, likelihood, priors or bounds, treatment of nondetections and calibration uncertainties.
- Dust-opacity normalization or coefficient A needed to recover absolute dust masses.
- Per-field rotation angles, inversion-search implementation, filament-fit estimator and width-error calculation.
- SFR summation membership cuts and uncertainty propagation within the adopted comparison volumes.

## Analysis recipe

1. **Make continuum images and spectral cubes**: Subtract continuum using channels excluding significant lines; image continuum and residual visibilities with TCLEAN; smooth each cube to a common beam.  
  > "The continuum channels are then used for both continuum generation and subtraction." (ALMA); "Next, we apply TCLEAN to perform an inverse Fourier transformation on both the continuum and continuum-subtracted visibilities." (ALMA); "we apply the CASA routine IMSMOOTH to the reduced data cubes, allowing each cube to have a common resolution." (ALMA)
   - software: CASA, TCLEAN, IMSMOOTH
   - parameter: Natural weighting; 240×240 pixels; 0.43'' pixels.  
  > "The final images are transformed into 240$\times$240 pixels in R.A. and DEC. directions, respectively, with a pixel size of 0.43$''$." (ALMA); "We apply natural weighting for the baselines." (ALMA)
   - parameter: auto-multithresh; noisethreshold=4; lownoisethreshold=2.5; clean to 2σ.  
  > "we use an automasking approach in TCLEAN by setting “auto-multithresh” as the usemask parameter to increase the efficiency of CLEAN (noisethreshold = 4; lownoisethreshold = 2.5)." (ALMA); "Finally, the cubes within the masked regions are cleaned down to 2 $\sigma$ level." (ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Choose line-detection thresholds**: Inject Gaussian lines at random spatial and spectral positions; rerun extraction; measure completeness and false detection rate.  
  > "First, we generate fake emission lines with a single Gaussian profile with various line widths (FWHM) and line intensity with the same spatial shape as the beam size of the original cube." (Survey Depth Analyses); "Second, we inject five fake lines into random spectral cubes of the same quasar field, at random locations and frequency channels." (Survey Depth Analyses); "Then, we perform spectral extraction again on the spectral cubes containing the fake lines, considering different SNR limits." (Survey Depth Analyses)
   - parameter: Five lines per injection, repeated 10 times: 50 fake sources per field.  
  > "We repeat this step 10 times, resulting in a total of 50 fake line sources, and perform this process for each quasar field." (Survey Depth Analyses)
   - parameter: ALMA USB SNR≥8.0; LSB SNR over 7.0; same thresholds for NOEMA.  
  > "This motivated our choice of the detection threshold (SNR $\geq$ 8.0) for the ALMA USB cubes." (Survey Depth Analyses); "Thus, for the selection of LSB sources, we choose the detections whose SNRs is over 7.0." (Survey Depth Analyses); "we adopt the same detection thresholds for NOEMA as those for ALMA." (Survey Depth Analyses)
   - assumption: Injected lines are CO(4-3), single Gaussian and beam-shaped.  
  > "First, we generate fake emission lines with a single Gaussian profile with various line widths (FWHM) and line intensity with the same spatial shape as the beam size of the original cube." (Survey Depth Analyses); "we assume these lines to be CO(4-3), as this is the most likely transition for the majority of our detections." (Survey Depth Analyses)
   - fitting: _not stated_
   - validation: USB FDR is zero for most grids at SNR≥8.0; LSB and NOEMA assessed by the same procedure.  
  > "the FDR for a SNR $\geq$ 8.0 cut is zero for most of the grids." (Survey Depth Analyses); "We now apply the same steps to the LSB of the ALMA data cubes" (Survey Depth Analyses); "Likewise, the same steps are applied to the NOEMA cubes." (Survey Depth Analyses)
3. **Detect lines and select associated sources**: Search cubes with LINESEEKER, reject narrow spikes, and classify detections into primary and supplementary samples.  
  > "To search for line emitting sources in the reduced data cubes, we utilized the publicly available code LINESEEKER" (Line extraction from spectral datacubes); "After removing spikes detections that have FWHM values below the minimum ($\sim$180 km/s) of the reported lines for SMGs in the literature (cite: 2021MNRAS.501.3926B)" (Line extraction from spectral datacubes); "We classified these 28 line detections into two types: primary and supplementary." (Line extraction from spectral datacubes)
   - software: LINESEEKER
   - parameter: Reject FWHM below ~180 km/s.  
  > "After removing spikes detections that have FWHM values below the minimum ($\sim$180 km/s) of the reported lines for SMGs in the literature (cite: 2021MNRAS.501.3926B)" (Line extraction from spectral datacubes)
   - parameter: Primary sources require continuum detection and velocity offsets within ±7000 km/s of their quasars.  
  > "primary sources are those that are detected in continuum and have velocity offsets within $\pm$7000 km/s with respect to their corresponding quasars." (Line extraction from spectral datacubes)
   - assumption: The ±7000 km/s interval selects membership in the targeted large-scale structures.  
  > "the relative velocity of primary samples is restricted to this range, ensuring their membership within the large-scale structure of the targeted proto-clusters." (Line extraction from spectral datacubes)
   - fitting: _not stated_
   - validation: Detection thresholds exceed maximum negative-signal SNRs; continuum supports primary-source fidelity.  
  > "exceeding the maximum SNRs of the negative signals." (Line extraction from spectral datacubes); "Primary sources are those that are more likely to be genuine line emissions based on their continuum detections" (Line extraction from spectral datacubes)
4. **Measure line profiles and total intensities**: Extract beam-aperture spectra, select single or double Gaussians with AICc, integrate best-fit models and apply a curve-of-growth correction.  
  > "We extract spectral lines using apertures of the synthesized beams at the locations reported by LINESEEKER." (Line extraction from spectral datacubes); "To determine if the spectra are better fit by a single Gaussian or double Gaussian model, we employed the Akaike information criterion (AICc) (as detailed in (cite: 2022ApJ...929..159C))." (Line extraction from spectral datacubes); "With the chosen best-fit model for the CO emission line, we then derived line properties by integrating the model." (Line extraction from spectral datacubes)
   - parameter: Curve-of-growth apertures: 0.25–4.00 times beam size; multiply one-beam intensities by 2.  
  > "We varied our aperture from 0.25 to 4.00 times the beam size and repeated all steps of the spectral extraction analyses." (Curve-of-Growth Analyses); "As a result, we multiplied our intensity results, which were extracted within one beam size, by a factor of 2 to obtain the total flux intensity." (Curve-of-Growth Analyses)
   - parameter: Single-Gaussian redshift from peak-channel frequency; FWHM=2.355σ; double-Gaussian redshift and width from intensity-weighted frequency moments.  
  > "For single Gaussian models, redshifts are determined based on the frequency of the flux peak channel, and the FWHM is 2.355 times the standard deviation." (Line extraction from spectral datacubes); "$\bar{\nu} = \frac{\int \nu I_{\nu} \,d\nu}{\int I_{\nu} \,d\nu}," (Line extraction from spectral datacubes); "the FWHM was determined as 2.355 times the dispersion" (Line extraction from spectral datacubes)
   - fitting: Single and double Gaussian models; AICc model selection. Optimizer, likelihood and parameter bounds not stated.  
  > "To determine if the spectra are better fit by a single Gaussian or double Gaussian model, we employed the Akaike information criterion (AICc) (as detailed in (cite: 2022ApJ...929..159C))." (Line extraction from spectral datacubes)
   - validation: Mean/median curve-of-growth intensity converges to twice the one-beam intensity above beam factor 2.  
  > "We found that the median/mean line intensity converges to two times the intensity extracted with one beam at beam factors larger than 2." (Curve-of-Growth Analyses)
5. **Identify transitions and derive CO luminosities**: Identify ALMA lines as CO(4-3) and NOEMA lines as CO(3-2); convert integrated intensity to luminosity and then to CO(1-0).  
  > "Given the redshifts of the central quasars, we identify these line detections to be most likely CO(4-3) from ALMA and CO(3-2) from NOEMA." (Line extraction from spectral datacubes); "$$L'_{CO} = \frac{3.257\times{10}^7}{1+z}\frac{I_{CO}D_L^2}{\nu_0^2}\  [{\rm K\,km\,s^{-1}\,{pc}^{2}}]$$" (Line extraction from spectral datacubes); "using the relationship described by (cite: 2021MNRAS.501.3926B): $L'_{\rm CO(1-0)}=L'_{\rm CO}/r_{j1}$, with $r_{31}= 0.63\pm0.12$ ; $r_{41}= 0.34\pm0.04$ ." (Line extraction from spectral datacubes)
   - parameter: r31=0.63±0.12; r41=0.34±0.04.  
  > "$r_{31}= 0.63\pm0.12$ ; $r_{41}= 0.34\pm0.04$ ." (Line extraction from spectral datacubes)
   - assumption: Planck cosmology: H0=67.8 km s−1 Mpc−1, Ω_MΛ=0.307, ΩΛ=0.69.  
  > "Throughout this paper, we assume the Planck cosmology: $H_0$ = 67.8 $km s^{-1} Mpc^{-1}$ , $\Omega_MΛ$ = 0.307, and $\Omega_\Lambda$ = 0.69 (cite: 2014A&A...571A..16P)." (Introduction)
   - fitting: _not stated_
   - validation: Alternative CO-transition chance-projection probability estimated at ~10%; median CO(4-3) luminosity errors computed by bootstrapping.  
  > "the probability of these lines being other CO transitions in chance projection is $\sim$10%" (Line extraction from spectral datacubes); "with errors computed via bootstrapping." (Line extraction from spectral datacubes)
6. **Locate CO emission and check spatial structure**: Stack channels within fitted FWHM; locate peak pixels; separately stack double-Gaussian components; fit emission maps with IMFIT.  
  > "we stacked the channels that fall within the FWHM determined by the best model to generate the line emission maps" (Line extraction from spectral datacubes); "For sources that are better fit by the double Gaussian model, we also separately stacked the channels corresponding to each component" (Line extraction from spectral datacubes); "We perform CASA task IMFIT to the emission maps." (CO emission maps)
   - software: CASA, IMFIT
   - parameter: Channel stacking interval: fitted line FWHM.  
  > "we stacked the channels that fall within the FWHM determined by the best model to generate the line emission maps" (Line extraction from spectral datacubes)
   - fitting: CASA IMFIT on CO emission maps.  
  > "We perform CASA task IMFIT to the emission maps." (CO emission maps)
   - validation: Red/blueshifted component offsets are smaller than the beam; most CO emission is unresolved.  
  > "Although there are offsets between the redshifted and blueshifted components, the offsets are smaller than the beam size." (Line extraction from spectral datacubes); "As expected, most CO emissions are unresolved." (CO emission maps)
7. **Measure and deblend continuum photometry**: Search for map peaks within one beam of CO peak positions; estimate blending corrections using COSMOS extracted-to-deblended flux comparisons.  
  > "we obtained the continuum fluxes for our sample sources by searching the peak value within the beam size of the corresponding maps centered at the peak pixels of the CO emission lines." (Continuum); "calculate the median ratio between the extracted flux and the deblended flux provided in the catalog." (Continuum)
   - parameter: Deblending ratios ~0.7–1.0 applied to extracted fluxes.  
  > "As a result, we obtain the deblending ratios ranging from $\sim$0.7 - 1.0, which are then applied to the extracted fluxes of our sample." (Continuum)
   - assumption: Estimate target-field blending using COSMOS data and catalogs.  
  > "we estimate the amount of blending using data and catalogs in the well-known COSMOS field." (Continuum)
   - fitting: _not stated_
   - validation: Compare extracted COSMOS fluxes against the super-deblended catalog.  
  > "We apply our method to extract continuum flux at the corresponding locations of the sources in the super-deblended catalog, and calculate the median ratio between the extracted flux and the deblended flux provided in the catalog." (Continuum)
8. **Fit dust SEDs and infrared luminosities**: Fit a single-temperature, optically thin MBB; integrate from 8 to 1000 μm; repeat selected fits with free β and comparison fits with β=1.8.  
  > "we adopt a single temperature modified black-body (MBB) as usually done in the literature (cite: 2012MNRAS.425.3094C; 2021ApJ...919...30D)" (SED Fitting); "Integrating the model from 8 $\mu m$ to 1000 $\mu m$ in wavelength, we can derive the infrared luminosity" (SED Fitting); "Because (cite: 2020MNRAS.494.3828D) adopted a fixed $\beta$ = 1.8, to make a fair comparison, the results plotted in this figure are based on the same assumption of $\beta$." (Dust properties)
   - parameter: Baseline β=2.0; eight robust Herschel-detected SMGs refitted with free β.  
  > "Initially, we assumed a fixed $\beta$ = 2.0 for the MBB fitting." (Dust properties); "we performed free-$\beta$ fitting again for 8 SMGs in our sample" (Dust properties); "that have robust Herschel detections" (Dust properties)
   - assumption: Optically thin: τν≪1; Sν proportional to A Mdust νβ Bν(Tdust); A combines constants.  
  > "In our case, for simplicity, we assume an optically thin case, with $\tau_\nu \ll 1$." (SED Fitting); "$$S_\nu \propto \tau_\nu B_\nu(T_{dust}) = A M_{dust} \nu^\beta B_\nu(T_{dust})$$" (SED Fitting); "Here, we assume that coefficient A combines all constants." (SED Fitting)
   - fitting: Fixed-β and free-β MBB fits; sampler, priors and likelihood not stated.  
  > "Initially, we assumed a fixed $\beta$ = 2.0 for the MBB fitting." (Dust properties); "we performed free-$\beta$ fitting again for 8 SMGs in our sample" (Dust properties)
   - validation: Free-β median 2.0±0.2 agrees with fixed β=2.0.  
  > "derived a median value of $2.0 \,\pm\, 0.2$." (Dust properties); "This is consistent with the general assumption of $\beta$ = 2.0." (Dust properties)
9. **Explain detection incompleteness**: Predict rates from excess number counts multiplied by spectral coverage and detection bias ratios; search lower-SNR sources as a check.  
  > "We then derive the expected detection rates by multiplying the excess number of sources deduced from the number counts by SCR and DBR, and dividing the results by the total number observed." (Detection rate); "To estimate how many sources we missed because of the current detection limit, we search for fainter sources under our SNR threshold" (Detection rate)
   - parameter: Number-count calculation restricted to S850μm>5 mJy.  
  > "We limit the calculation to the flux regime greater than 5 mJy at 850$\,\mu m$, which is our original selection for ALMA and NOEMA follow-up observations." (Detection rate)
   - parameter: Lower-SNR search: SNR≥5.0, within SCUBA-2 beam, FWHM≥~180 km/s, fidelity≥0.5.  
  > "we search for sources whose SNR is at least 5.0" (Detection rate); "(1) source location within the beam of the 850$\,\mu m$ SCUBA-2 image;" (Detection rate); "(2) FWHM of lines $\geq$ the minimum ($\sim$180 km/s) of the reported lines for literature SMGs (cite: 2021MNRAS.501.3926B); (3) fidelity $\geq$ 0.5" (Detection rate)
   - assumption: Use field-SMG luminosity and line-width distributions to estimate detection bias.  
  > "Based on the distribution of luminosity and line width of SMGs in the field (cite: 2021MNRAS.501.3926B), we calculate the fraction of sources that would have been detected given our sensitivity limits." (Detection rate)
   - fitting: _not stated_
   - validation: Seven additional lower-SNR detections bring the average observed-to-expected rate toward unity.  
  > "Following these criteria, we found 7 additional detections." (Detection rate); "When considering the additional sources, the average ratio between real and expected rate approaches unity." (Detection rate)
10. **Derive gas masses, SFRs and depletion times**: Use αCO=1.0 for gas masses; convert LIR to SFR; calculate Tdep=Mgas/SFR and gas-to-dust ratio Mgas/Mdust; compare with field SMGs.  
  > "we calculate $M_{gas}$ by adopting $\alpha_{\rm CO} = 1.0$, same as the value adopted by studies of field SMGs (cite: 2021MNRAS.501.3926B)." (Depletion timescale); "$$T_{\rm dep} = \frac{M_{\rm gas}}{\rm SFR},$$" (Depletion timescale); "$$\delta_{gdr} = \frac{M_{gas}}{M_{dust}}$$" (Gas to dust ratio)
   - parameter: log(SFR [M⊙ yr−1])=log(LIR [erg/s])−43.41.  
  > "${\rm log(SFR\,[M_{\odot}\,yr^{-1}]) = log(}\rm L_{IR}\,[\rm erg/s])-43.41" (Depletion timescale)
   - assumption: Depletion times assume no gas inflow or outflow.  
  > "assuming that there is no gas inflow or outflow" (Depletion timescale)
   - assumption: Dust masses for target and field SMGs use the same MBB assumptions.  
  > "the dust masses used here for both our sample SMGs and field SMG are calculated based on the same MBB fitting assumptions." (Gas to dust ratio)
   - fitting: _not stated_
   - validation: Compare median depletion time and gas-to-dust ratio with field SMGs.  
  > "we therefore find no significant difference in depletion time between our SMGs in the dense environments and those in the field." (Depletion timescale); "Our final result shows that our sample SMGs are consistent with typical field SMGs (cite: 2021MNRAS.501.3926B; 2024ApJ...961..226L) also for this parameter" (Gas to dust ratio)
11. **Test gas fraction against quasar-halo distance**: Estimate gas fractions from CO linewidths and luminosities using the dynamical relation; compare with projected quasar distances; calculate NFW escape velocities.  
  > "With this formula, we estimate $f_{gas}$ from the measured line width FWHM and the CO line luminosity." (Gas mass fraction); "then depicted the distribution as a function of their projected distances from the central quasars" (Gas mass fraction); "we calculate the escape velocity of quasar halos assuming an NFW halo potential ((cite: 1996ApJ...462..563N))" (Gas mass fraction)
   - parameter: re=3 kpc; αCO=1.0; fDM=0.12.  
  > "Following (cite: 2021ApJ...923..200C), we set the half-light radius to $r_{e}$= 3 kpc, $\alpha_{\rm CO}$= 1.0, and dark matter fraction as $f_{\rm DM}$ = 0.12, based on recent measurements." (Gas mass fraction)
   - parameter: NFW c=3.5; halo mass 10^12.5 M⊙ at z~3.  
  > "$c$ is the concentration ($c = 3.5$; (cite: 2018MNRAS.479.3879W); (cite: 2014MNRAS.441.3359D))" (Gas mass fraction); "for halo masses of $10^{12.5}$ $M_\odot$ at $z\sim3$." (Gas mass fraction)
   - assumption: Dynamical equilibrium of rotation-dominated disks.  
  > "The formula assumes dynamical equilibrium of rotation-dominated disks" (Gas mass fraction)
   - assumption: For literature comparisons, include only lines appearing single-peaked or better fit by single Gaussians.  
  > "As most works only reported fitting results using single Gaussian model, we only include lines that appear single peak or could be better fit by single Gaussian models." (Gas mass fraction)
   - fitting: _not stated_
   - validation: Focus on average trends because unknown disk inclinations introduce large scatter.  
  > "the unknown inclination angle of the disks inevitably introduces large scatter of the estimates." (Gas mass fraction); "We therefore focus primarily on the average trend rather than on individual source values." (Gas mass fraction)
12. **Test coherent spatial structure and measure its width**: Rotate fields with literature angles; test all 180° inversion scenarios; select strongest x-z correlation; fit exponential distance distributions in x-y and x-z.  
  > "We therefore adopted the rotation angles of the filament on the plane-of-sky, $\alpha$, derived from 2D spatial distribution reported by (cite: FAB2023)" (Spatial Distribution); "we tested every possible inversion scenario for the quasar field studied and applied Pearson correlation testing to each scenario." (Spatial Distribution); "$$PDF(|y|) = exp(-|y|/\lambda)/\lambda,$$" (Spatial Distribution)
   - parameter: Invert SDSSJ0819, SDSSJ1020 and SDSSJ1209; minimum p=0.05.  
  > "We finally found the lowest p-value = 0.05 in the scenario where SDSSJ0819, SDSSJ1020 and SDSSJ1209 were inverted." (Spatial Distribution)
   - parameter: x-z distance measured from Δz=3.2Δx+14.4 cMpc.  
  > "the distance from SMGs to the best fit line ($\Delta z = 3.2\Delta x+14.4$ \[cMpc\])." (Spatial Distribution)
   - assumption: Straight filament spine; redshift differences indicate radial distance in the Hubble flow.  
  > "the filament spine is assumed to be a straight line" (Spatial Distribution); "the redshift differences likely indicate differences in radial distance, rather than peculiar velocity." (Spatial Distribution)
   - fitting: Exponential PDF with scale width λ; Pearson testing for inversion selection.  
  > "$$PDF(|y|) = exp(-|y|/\lambda)/\lambda,$$ where $\lambda$ is the scale width of the filament." (Spatial Distribution); "we tested every possible inversion scenario for the quasar field studied and applied Pearson correlation testing to each scenario." (Spatial Distribution)
   - validation: 1000 randomized-z realizations with x-y positions and z signs fixed; Spearman tests; 0.5% have p≤0.05. Also apply width method to HS 1549+19.  
  > "random values were assigned to the z-axis while keeping the blue and red fixed, i.e., fixing the positive and negative values of the z-axis" (Spatial Distribution); "We repeated this process 1000 times and performed Spearman correlation testing for each condition." (Spatial Distribution); "We found that the ratio of the p-values $\leq$ 0.05 (same as our result) is 0.5%" (Spatial Distribution)
13. **Compare cumulative SFR and SFR density with simulations**: Sum SFRs for SDSSJ0819 and the field average; calculate SFR per comoving volume; compare with FOREVER22 and literature observations.  
  > "we calculate the cumulative SFR and SFRD for SDSSJ0819 (the field with the most detections) and the average value for all fields in our observation." (Cumulative SFR); "we computed the total SFR per unit comoving volume to estimate the star formation rate density (SFRD)." (Cumulative SFR); "we first make use of a cosmological hydrodynamical simulation called FOREVER22 (cite: 2022MNRAS.509.4037Y)." (Cumulative SFR)
   - parameter: Cumulative-SFR projected depth 28.6 cMpc; SFRD volume (25.7 cMpc)^3.  
  > "a projected depth of 28.6 cMpc and a volume of (25.7 cMpc$)^3$, for cumulative SFRs and SFRDs, respectively (cite: 2022MNRAS.509.4037Y)." (Cumulative SFR)
   - assumption: Match observational calculation volumes to simulation definitions.  
  > "to make a fair comparison with the model predictions, we adopt the volumes defined in the simulations" (Cumulative SFR)
   - fitting: _not stated_
   - validation: Compare with model predictions and recalculate literature cumulative SFRs using the same volume.  
  > "if we take the measurements reported in the literature and adopt the same volume for the calculations, some of the reported values for the cumulative SFRs become lower and closer to the model predictions" (Cumulative SFR)
14. **Check the nature of supplementary detections**: Calculate completeness-corrected CO luminosity functions for seven sources outside ±7000 km/s, weighting alternative transitions by field-SMG redshift probabilities.  
  > "there are 7 sources whose velocities are far from the center QSOs and cannot be considered as members of the structure (velocity excess $\pm$ 7000 km/s)." (CO Luminosity Function); "the range between the maximum and minimum CO luminosity among the 7 detections corrected for completeness, and divided by the total survey volume." (CO Luminosity Function); "We derive the luminosity functions of each transition using these corresponding probabilities." (CO Luminosity Function)
   - parameter: CO(2-1), CO(3-2), CO(4-3), CO(5-4) probabilities: 24.0%, 57.3%, 16.6%, 2.2%.  
  > "we derived the probabilities of these lines being CO(2-1), CO(3-2), CO(4-3), CO(5-4) to be 24.0%, 57.3%, 16.6%, 2.2%, respectively." (CO Luminosity Function)
   - assumption: Use the field-SMG redshift-dependent probability distribution.  
  > "based on the redshift-dependent probability distribution of field SMGs reported by (cite: 2016ApJ...820...82C)" (CO Luminosity Function)
   - fitting: _not stated_
   - validation: Compare luminosity functions with ASPECS and HDFN.  
  > "they are widely consistent with previous surveys in the field, e.g., ASPECS (cite: 2020ApJ...902..110D) and HDFN (cite: 2023ApJ...945..111B)." (CO Luminosity Function)

## Software

- **CASA** 5.6.1: ALMA raw-visibility calibration; imaging, smoothing and emission-map fitting through named tasks.  
  > "For data reduction, we calibrate the raw visibilities by running the corresponding SCRIPTFORPI.PY scripts under CASA5.6.1." (ALMA); "we apply the CASA routine IMSMOOTH to the reduced data cubes" (ALMA); "We perform CASA task IMFIT to the emission maps." (CO emission maps)
- **SCRIPTFORPI.PY** : Calibrate raw ALMA visibilities using QA2 calibrations.  
  > "For data reduction, we calibrate the raw visibilities by running the corresponding SCRIPTFORPI.PY scripts under CASA5.6.1." (ALMA); "This means that the calibrations performed by the QA2 team members are adopted." (ALMA)
- **TCLEAN** : Image continuum and continuum-subtracted visibilities with automasking.  
  > "Next, we apply TCLEAN to perform an inverse Fourier transformation on both the continuum and continuum-subtracted visibilities." (ALMA); "we use an automasking approach in TCLEAN by setting “auto-multithresh” as the usemask parameter" (ALMA)
- **IMSMOOTH** : Give each reduced cube a common resolution.  
  > "we apply the CASA routine IMSMOOTH to the reduced data cubes, allowing each cube to have a common resolution." (ALMA)
- **IMFIT** : Fit CO emission maps.  
  > "We perform CASA task IMFIT to the emission maps." (CO emission maps)
- **GILDAS** : Suite containing CLIC used for NOEMA reduction and calibration.  
  > "We used the software CLIC from the GILDAS suite to reduce and calibrate the data, resample the observations in 20 MHz–wide channels, and extract the calibrated visibilities." (NOEMA)
- **CLIC** : Reduce and calibrate NOEMA data, resample to 20 MHz channels and extract calibrated visibilities.  
  > "We used the software CLIC from the GILDAS suite to reduce and calibrate the data, resample the observations in 20 MHz–wide channels, and extract the calibrated visibilities." (NOEMA)
- **MAPPING** : Fourier transform NOEMA data.  
  > "We then used MAPPING to perform the Fourier transform." (NOEMA)
- **LINESEEKER** : Search reduced spectral cubes for line-emitting sources.  
  > "To search for line emitting sources in the reduced data cubes, we utilized the publicly available code LINESEEKER" (Line extraction from spectral datacubes)
- **MUSIC** : Generate initial conditions in the external FOREVER22 simulation.  
  > "In FOREVER22, the MUSIC code (cite: Hahn2011) was used to generate the initial conditions." (Cumulative SFR)
- **FOREVER22** : External simulation comparison for cumulative SFR and SFRD.  
  > "we first make use of a cosmological hydrodynamical simulation called FOREVER22 (cite: 2022MNRAS.509.4037Y)." (Cumulative SFR); "the simulation provides predictions for cumulative SFRs and total SFRDs" (Cumulative SFR)
- **ESA Herschel Science Archive** : Retrieve pipeline-reduced Herschel level-2 maps.  
  > "We retrieved the data from the ESA Herschel Science Archive, and we simply used the level-2 map reduced by the pipeline from the archive at 250, 350, and 500 $\mu$m." (Herschel)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total detected line emitters | 28 | not stated | sources | 3 | Of the 101 SCUBA-2 sources targeted by our ALMA and NOEMA observations, we detect 28 line-emitting sources in total, and 15 are confirmed physically associated with their corresponding quasars. |
| Physically associated primary sources | 15 | not stated | sources | 3 | Of the 101 SCUBA-2 sources targeted by our ALMA and NOEMA observations, we detect 28 line-emitting sources in total, and 15 are confirmed physically associated with their corresponding quasars. |
| Primary sources better described by double Gaussian models | 73 | +29/-21; Poisson error | % | 4 | We find that $73^{+29}_{-21}\%$ (considering Poisson error) of our primary samples are better described by double Gaussian models |
| Median double-Gaussian peak separation | 350 | ±25 | km s−1 | 4 | we derive the median separation of the two Gaussian peaks to be $350\,\pm\,25\ {\rm km\  s^{-1}}$ |
| Median CO-line FWHM | 498 | ±36 | km s−1 | 4 | The median FWHM value for our samples is 498 $\pm$ 36 km s$^{-1}$ |
| Median primary-set L′CO(4-3) | 3.9 × 10^10 | ±0.5 × 10^10; bootstrapping | K km s−1 pc² | 5 | the median value of $L'_{\rm CO(4-3)}$ for the primary set is $(3.9\pm0.5)\times 10^{10}$ K km s$^{-1}$ pc$^{2}$, with errors computed via bootstrapping. |
| Median L′CO(1-0) | 11.7 × 10^10 | ±1.5 × 10^10 | K km s−1 pc² | 5 | In this work, the median value of $L'_{\rm CO(1-0)}$ is (11.7 ± 1.5) $\times 10^{10}$ K km s$^{-1}$ pc$^2$ |
| Median dust temperature, baseline SED fits | 34 | ±3 | K | 8 | The median values of $T_{\rm dust}$ and ${\rm log}(L_{\rm IR}/[L_\odot])$ are $34 \pm 3\ K$ and $12.8 \pm 0.1$, respectively. |
| Median log(LIR/L⊙) | 12.8 | ±0.1 | dex | 8 | the median of log$(L_{\rm IR}/L_{\odot})$ is 12.8 ± 0.1 dex. |
| Median free-fit dust emissivity index for eight Herschel-detected SMGs | 2.0 | ±0.2 | dimensionless | 8 | we performed free-$\beta$ fitting again for 8 SMGs in our sample; derived a median value of $2.0 \,\pm\, 0.2$. |
| Detection bias ratio for CO(4-3) | ~81 | not stated | % | 9 | As a result, the DBRs are $\sim$81% and $\sim$77% for CO(4-3) and CO(3-2), respectively. |
| Detection bias ratio for CO(3-2) | ~77 | not stated | % | 9 | As a result, the DBRs are $\sim$81% and $\sim$77% for CO(4-3) and CO(3-2), respectively. |
| Additional lower-SNR detections | 7 | not stated | sources | 9 | Following these criteria, we found 7 additional detections. |
| Median depletion timescale | 0.20 | ±0.03 | Gyr | 10 | For our sample at $z\sim3$, we calculate a median depletion timescale of 0.20 $\pm$ 0.03 \[Gyr\] |
| Median fgas inside quasar virial radius, reported numerical scale | 26 | ±13 | dimensionless | 11 | with a mdeian $f_{gas}$ of 26 $\pm$ 13 |
| Median fgas beyond quasar virial radius, reported numerical scale | 92 | ±40 | dimensionless | 11 | Beyond $R_{vir}$, the $f_{gas}$ of DSFGs (median of 92 $\pm$ 40) is comparable to that of field SMGs |
| Minimum correlation p-value after field-inversion search | 0.05 | not stated | dimensionless | 12 | We finally found the lowest p-value = 0.05 in the scenario where SDSSJ0819, SDSSJ1020 and SDSSJ1209 were inverted. |
| Filament scale width in x-y, Spatial Distribution section | 4.0 | ±2.6 | cMpc | 12 | we derive $\lambda = 4.0 \pm 2.6$ cMpc in the x-y plane and $\lambda = 3.5 \pm 2.2$ cMpc in the x-z plane. |
| Filament scale width in x-z, Spatial Distribution section | 3.5 | ±2.2 | cMpc | 12 | we derive $\lambda = 4.0 \pm 2.6$ cMpc in the x-y plane and $\lambda = 3.5 \pm 2.2$ cMpc in the x-z plane. |
| Filament scale width in x-y, conflicting Conclusion value | 4.9 | ±2.3 | cMpc | 12 | By estimating the scale widths of the filament, we obtained 4.9 $\pm$ 2.3 cMpc and 5.8 $\pm$ 3.1 cMpc for the x-y and x-z distribution, respectively. |
| Filament scale width in x-z, conflicting Conclusion value | 5.8 | ±3.1 | cMpc | 12 | By estimating the scale widths of the filament, we obtained 4.9 $\pm$ 2.3 cMpc and 5.8 $\pm$ 3.1 cMpc for the x-y and x-z distribution, respectively. |
| Filament scale width for reanalyzed HS 1549+19 sample | 3.6 | ±2.1 | cMpc | 12 | obtained $\lambda = 3.6 \pm 2.1$ cMpc in the sky projected (x-y) direction |
| Randomized realizations with correlation p≤0.05 | 0.5 | not stated | % | 12 | We found that the ratio of the p-values $\leq$ 0.05 (same as our result) is 0.5% |
| SDSSJ0819 SFRD, likely lower limit | 0.34 | ±0.07 | M⊙ yr−1 cMpc−3 | 13 | we obtain SFRDs of 0.34 $\pm$ 0.07 $M_\odot\, \rm yr^{-1}\, cMpc^{-3}$ for SDSSJ0819; our measurements are likely lower limits |
| All-quasar-field SFRD, likely lower limit | 0.07 | ±0.04 | M⊙ yr−1 cMpc−3 | 13 | 0.07 $\pm$ 0.04 $M_\odot\, \rm yr^{-1}\, cMpc^{-3}$ for all of our quasar fields, respectively.; our measurements are likely lower limits |

## Qualitative findings

- No significant CO-line-profile difference from field SMGs after accounting for sensitivity limits.  
  > "After accounting for the sensitivity limits, we conclude that there is no significant difference in CO line profiles between our samples and field SMGs." (CO line properties)
- Gas and dust properties beyond quasar virial radii show no significant environmental effect; within-halo samples show decreasing gas fractions.  
  > "the gas and dust properties of SMGs located beyond the virial radii of quasar halos are not significantly affected by their presumably denser surroundings." (Summary on gas and dust properties); "For DSFGs/SMGs that are within the halo, we observe evidence of decreasing gas fractions." (Summary on gas and dust properties)
- Outside-virial-radius SMGs are consistent with being unbound and in the Hubble flow.  
  > "our sample SMGs outside the virial radius are consistent with being not bound." (Gas mass fraction); "Given the large distance separations, they are most likely part of the Hubble flow." (Gas mass fraction)
- Tentative coherent filamentary structure; comparable widths suggest a cylinder or elongated pancake.  
  > "our reported detection of filaments is tentative." (Spatial Distribution); "it suggests that the large-scale filaments traced by quasars and DSFGs resemble the shape of a cylinder or elongated pancake." (Spatial Distribution)
- Supplementary detections are consistent with field sources.  
  > "our analyses suggest that our supplementary sample sources are drawn from the field." (CO Luminosity Function)
- Volume-matched cumulative SFRs and SFRDs generally agree with models, but are likely lower limits.  
  > "For cumulative SFRs, we see that model predictions generally agree with our measurements" (Cumulative SFR); "We see a similar behavior in the comparison on SFRDs, where the models generally agree with our measurements." (Cumulative SFR); "our measurements are likely lower limits" (Cumulative SFR)

## Claim tuples

- H: Bright SCUBA-2 sources trace galaxies physically associated with the targeted quasar structures. | E: Search ALMA/NOEMA cubes for CO lines and require continuum detections plus quasar-relative velocity membership. | R: 28 line emitters; 15 physically associated primary sources; seven additional lower-SNR candidates. | F: Low detection rates can be explained by spectral coverage and sensitivity; about half of associated sources lie below the current limit. | **supported**
- H: SMGs in dense quasar environments have different gas and dust properties from field SMGs. | E: Compare CO profiles, luminosities, MBB-derived dust properties, depletion times and gas-to-dust ratios with field samples. | R: Median Tdust=34±3 K, free-fit β=2.0±0.2 and depletion time=0.20±0.03 Gyr; comparisons show similar properties. | F: No significant environmental effect is detected for the sample beyond quasar virial radii. | **refuted**
- H: Environmental gas depletion becomes important near or within quasar halos. | E: Combine target and literature CO measurements, estimate dynamical gas fractions and compare against projected quasar distance. | R: Gas fractions are lower inside the virial radius and comparable to field SMGs outside it. | F: Dusty galaxies appear affected when approaching or within the halo; undetected faint sources outside remain a limitation. | **partially**
- H: Spectroscopically confirmed SMGs trace coherent large-scale filaments. | E: Align fields with literature angles, optimize 180° inversions, fit spatial widths and test randomized radial positions. | R: Minimum correlation p=0.05; 0.5% of randomized realizations meet p≤0.05; x-y and x-z widths agree within large errors. | F: Tentative filament detection with cylindrical or elongated pancake geometry. | **partially**
- H: Observed protocluster star formation agrees with simulations when comparison volumes are matched. | E: Calculate cumulative SFR and SFRD in FOREVER22-matched depths and volumes. | R: SFRDs are 0.34±0.07 for SDSSJ0819 and 0.07±0.04 M⊙ yr−1 cMpc−3 for all fields. | F: Measurements generally agree with model predictions, but incomplete bright-source targeting yields lower limits. | **partially**

## Reasoning

- Why this data: Spectroscopic follow-up is needed to establish physical association beyond the original projected SCUBA-2 distributions.  
  > "these surveys at 850 $\mu m$ could only provide us with the distribution in 2D projected space, and spectroscopic follow-up observations are needed to confirm if these submillimeter sources are physically associated with the central quasars." (Introduction)
- Why this method: Use dynamical gas fractions because direct stellar-mass estimates are unavailable; match simulation volumes for fair SFR comparisons.  
  > "The lack of optical and infrared data means that direct estimates of stellar masses for our sources are not yet possible." (Gas mass fraction); "To bypass this difficulty, we adopt a method that utilizes the dynamical mass and gas mass estimates enabled by our data." (Gas mass fraction); "to make a fair comparison with the model predictions, we adopt the volumes defined in the simulations" (Cumulative SFR)
- Alternative: Single versus double Gaussian line models compared using AICc.  
  > "To determine if the spectra are better fit by a single Gaussian or double Gaussian model, we employed the Akaike information criterion (AICc) (as detailed in (cite: 2022ApJ...929..159C))." (Line extraction from spectral datacubes)
- Alternative: Alternative CO transitions considered; chance-projection probability ~10%.  
  > "the probability of these lines being other CO transitions in chance projection is $\sim$10%" (Line extraction from spectral datacubes)
- Alternative: Optically thick/general MBB would yield higher dust temperatures; optically thin assumptions retained for comparison.  
  > "it would systematically yield a higher $T_{\rm dust}$ due to differences in model assumptions" (Dust properties); "To make fair comparisons, we adopt the same assumptions as those employed by previous studies." (Dust properties)
- Alternative: Fixed β=2.0 tested with free-β fits; β=1.8 used for a matched field comparison.  
  > "To verify this assumption, we performed free-$\beta$ fitting again for 8 SMGs in our sample" (Dust properties); "Because (cite: 2020MNRAS.494.3828D) adopted a fixed $\beta$ = 1.8, to make a fair comparison, the results plotted in this figure are based on the same assumption of $\beta$." (Dust properties)
- Alternative: Do not interpret low detection rates as proof of intrinsically lower CO luminosities in dense environments.  
  > "Since there could also be a detection bias in the field SMGs, we refrain ourselves from concluding that this is evidence that SMGs in dense environments have lower CO line luminosity than those in the field." (Detection rate)
- Alternative: Including supplementary sources within ±7000 km/s yields only marginal improvement in spatial significance.  
  > "including the supplementary sources" (Spatial Distribution); "that fall within the velocity range associated with the proto-cluster ($\pm 7000\, \rm km/s$) in our analysis." (Spatial Distribution); "We found a marginal improvement in the significance of the result." (Spatial Distribution)
- How they decided it was enough: Clean to 2σ; choose USB threshold where FDR is zero for most grids; adopt total-flux correction where mean/median growth curves converge.  
  > "Finally, the cubes within the masked regions are cleaned down to 2 $\sigma$ level." (ALMA); "the FDR for a SNR $\geq$ 8.0 cut is zero for most of the grids." (Survey Depth Analyses); "We found that the median/mean line intensity converges to two times the intensity extracted with one beam at beam factors larger than 2." (Curve-of-Growth Analyses)
- Limitation (authors): Spatial resolution cannot establish significant red/blueshifted component offsets.  
  > "we do not find evidence of significant offsets between the two components at the given spatial resolution" (Line extraction from spectral datacubes)
- Limitation (authors): Some aperture growth curves decline or increase monotonically, suspected to reflect large-scale noise.  
  > "some curves exhibit a downward trend or a monotonically increasing pattern." (Curve-of-Growth Analyses); "We suspect that this behavior is attributed to larger-scale noise structures" (Curve-of-Growth Analyses)
- Limitation (authors): Herschel blending corrections rely on COSMOS because relevant high-resolution target-field maps are lacking.  
  > "the low spatial resolution of the Herschel maps makes them prone to blending and overestimating the continuum flux." (Continuum); "Due to a lack of high-resolution maps at relevant wavelengths in our target fields, particularly mid-infrared and radio, we estimate the amount of blending using data and catalogs in the well-known COSMOS field." (Continuum)
- Limitation (authors): Unknown disk inclinations introduce large scatter in dynamical gas-fraction estimates.  
  > "the unknown inclination angle of the disks inevitably introduces large scatter of the estimates." (Gas mass fraction)
- Limitation (authors): Faint CO sources outside halos may be undetected; their gas fractions remain untested.  
  > "the limited sensitivity of our ALMA data prevents us from detecting sources with CO luminosity comparable to those around quasars." (Gas mass fraction); "Whether these fainter CO sources that are located outside the virial radius have gas fractions as high as those with higher CO luminosity remains to be tested with deeper observations in the future." (Gas mass fraction)
- Limitation (authors): Small spectroscopic sample permits only statistical spatial analyses; filament detection is tentative.  
  > "Due to the small sample size of SMGs with spectroscopic redshifts, we can only perform statistical analyses" (Spatial Distribution); "our reported detection of filaments is tentative." (Spatial Distribution)
- Limitation (authors): Spatial PDFs are truncated by SCUBA-2 footprint and spectral-window coverage.  
  > "This limitation imposes a boundary on the PDF in the x-y distribution." (Spatial Distribution); "the z-axis value, which is limited by the wavelength range of the spectral window ($\sim$-40-100 cMpc)." (Spatial Distribution)
- Limitation (authors): Cumulative SFR and SFRD are lower limits because only the brightest objects were targeted; reliable incompleteness correction is unavailable.  
  > "our ALMA observations only targeted the top 10-20 brightest objects based on their S/N at 850 $\mu m$, resulting in incompleteness." (Cumulative SFR); "Without deeper surveys that allow us to uncover the true distribution of lower SFR sources, it is difficult to apply a reliable correction for incompleteness." (Cumulative SFR)
- Limitation (authors): Indicative infrared-luminosity limits have approximately ±0.2 dex uncertainty from redshift and SED assumptions.  
  > "uncertainties in the assumed redshifts and SED shapes introduce an uncertainty of approximately $\pm$0.2 dex in $\log(L_{\rm IR})$." (CO line properties); "Therefore, these values should be considered indicative only." (CO line properties)
- Caveat (inferred, ours): Filament widths conflict between Spatial Distribution (4.0±2.6 and 3.5±2.2 cMpc) and Conclusion (4.9±2.3 and 5.8±3.1 cMpc); neither pair can be selected as the unique answer key.
- Caveat (inferred, ours): Gas-fraction medians are printed as 26 and 92 without explicit percent signs; their numerical scaling must be resolved before physical use.
- Caveat (inferred, ours): The field-inversion search selects the minimum Pearson p-value, while mock significance uses Spearman tests; the complete selection procedure is not clearly reproduced in the null experiment.
- Caveat (inferred, ours): A common factor-of-two line-flux correction may conceal source-dependent aperture losses or noise effects.
- Caveat (inferred, ours): Transfer of COSMOS blending corrections to overdense quasar fields needs validation.
- Caveat (inferred, ours): Fixed radius, conversion factor and disk-equilibrium assumptions can affect inferred gas-fraction contrasts.
- Caveat (inferred, ours): Target-selection thresholds differ between the ALMA description and Conclusion.
- Caveat (inferred, ours): The NOEMA program is called S19CK in Observations and W18EM in the acknowledgments.
- Caveat (inferred, ours): Supplied tables and figure captions are missing, limiting checks of source-level measurements and sample membership.

## Reproducibility

- Data public (paper): Public Herschel data for Q2355 and SDSSJ0819.  
  > "Additionally, we used the public Herschel data for Q2355 and SDSSJ0819 at 250 $\mu$m, 350 $\mu$m, 500 $\mu$m." (Continuum)
- Products in archive: Pipeline-reduced Herschel level-2 maps.  
  > "We retrieved the data from the ESA Herschel Science Archive, and we simply used the level-2 map reduced by the pipeline from the archive at 250, 350, and 500 $\mu$m." (Herschel)
- Missing: Explicit ALMA and NOEMA public-access status and complete observation inventory.
- Missing: Referenced target, calibrator, line-measurement and photometry tables.
- Missing: Exact imaging, continuum subtraction and source-search configuration files.
- Missing: Spectral and SED fitting code with statistical specifications and uncertainty propagation.
- Missing: Dust-mass opacity normalization.
- Missing: Per-band blending corrections and literature comparison inputs.
- Missing: Inherited field rotation angles and exact spatial-test implementation.
- Missing: Resolution of conflicting filament widths and gas-fraction scaling.
- Data volume (inferred): Not reliably estimable: raw visibility sizes and complete per-observation metadata are absent.
- Score (inferred): 5/5, 5/10: project code, CASA version, imaging parameters and the main recipe are given, but missing tables, fitting specifications, inherited inputs and inconsistent spatial results prevent an exact reproduction.
- Rediscovery candidate: no, Main results are numeric, but ALMA public status is not stated and the supplied recipe lacks essential inputs and contains conflicting filament widths.

## Links

- Method: (cite: 2017A&A...597A..41G) (LINESEEKER line-search code.)
- Method: (cite: 2022ApJ...929..159C) (Automasking imaging, AICc line-model selection and curve-of-growth analysis.)
- Method: (cite: 2024ApJ...971..117G) (SCUBA-2 reduction and deblending reference.)
- Method: (cite: 2013ARA&A..51..105C) (CO intensity-to-luminosity conversion.)
- Method: (cite: 2021MNRAS.501.3926B) (CO excitation ratios, field distributions and gas-mass conversion assumptions.)
- Method: (cite: 2012MNRAS.425.3094C; 2021ApJ...919...30D) (Modified-blackbody SED modeling.)
- Method: (cite: 2021ApJ...923..200C) (Dynamical gas-fraction estimator and fixed physical parameters.)
- Method: (cite: Kennicut2012) (Infrared-luminosity-to-SFR conversion.)
- Method: (cite: 1996ApJ...462..563N) (NFW halo potential for escape velocities.)
- Method: (cite: FAB2023) (Field rotation angles and filament-width probability model.)
- Method: (cite: 2022MNRAS.509.4037Y) (FOREVER22 comparison and matched depth/volume definitions.)
- Companion: (cite: Nowotka2022) (Original SCUBA-2 survey supplying follow-up targets.)
- Companion: (cite: FAB2023) (Original SCUBA-2 survey, number counts and projected spatial analysis.)
- Related: A MUltiwavelength Study of ELAN Environments (AMUSE^2)
- Related: SCUBA-2 surveys of ELAN and quasar fields
- Related: HerMES Large Mode Survey
- Related: COSMOS super-deblended catalog
- Related: FOREVER22
- Related: ASPECS
- Related: HDFN

## Checks

```json
{
 "quotes": 309,
 "quotes_ok": 309,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 25,
 "numeric_problems": 0,
 "fill": {
  "facts": 201,
  "stated": 164,
  "rate": 0.816
 },
 "evidence_ok": true
}
```
