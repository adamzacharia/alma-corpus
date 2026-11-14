# Characterizing the dust content of disk substructures in TW Hydrae

`2021A&A...648A..33M` | Astronomy and Astrophysics 2021 | first author: Macías, E. | arXiv: 2102.04648 | DOI: 10.1051/0004-6361/202039812

Card schema 1.0 | model gpt-6.1-sol | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Characterize the dust content of substructures in TW Hya and their role in planet formation.  
  > "In order to shed some light on the origin and role that disk substructures play in planet formation, we aim to characterize the dust content of substructures in the disk of TW Hya." (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance d=59.5 (unit not stated)  
  > "It is among the closest protoplanetary disks to Earth ($d=59.5$; (cite: bai18; gai18))" (Introduction); "as determined from the position and proper motions reported by Gaia DR2 (cite: gai18)" (Observations); distance from (cite: bai18; gai18)  
  > "It is among the closest protoplanetary disks to Earth ($d=59.5$; (cite: bai18; gai18))" (Introduction); "as determined from the position and proper motions reported by Gaia DR2 (cite: gai18)" (Observations)

## Data provenance

- ALMA projects: 2015.1.00686.S, 2015.1.00845.S, 2015.A.00005.S, 2016.1.00173.S, 2016.1.00229.S, 2016.1.00629.S, 2016.1.00842.S, 2016.1.01158.S, 2017.1.00520.S, 2018.1.01218.S
- bands: Band 7: 0.87 mm; Band 6: 1.3 mm; Band 4: 2.1 mm; Band 3: 3.1 mm.  
  > "The obtained images at 0.87 mm (Band 7), 1.3 mm (Band 6), 2.1 mm (Band 4), and 3.1 mm (Band 3)" (Observational results)
- frequencies and spectral setup: New Band 3: 90.5, 92.5, 102.5, 104.5 GHz; archival SPWs selected near other datasets' central frequencies; channel averaging to ~125 MHz.  
  > "| 2018.1.01218.S | E. Macías     | 2019 Jun 24 | 43.5       | 83 – 16196  | 90.5, 92.5, 102.5, 104.5   | J1037-2934 | 5.4.0         |" (Table 1); "with central frequencies within $\sim0.5$ GHz of the central frequency of the other datasets in the band to avoid issues when combining them." (Observations); "Since we are only interested in the continuum emission, we performed channel averaging to each dataset up to a width $\sim125$ MHz." (Observations)
- continuum bandwidth: Archival spectral windows: ~2 GHz each; narrow line spectral windows avoided.  
  > "When retrieving archival data, we used only spectral windows with bandwidth $\sim2$ GHz (i.e., we avoided using narrow spectral windows dedicated to line observations)" (Observations)
- arrays: _not stated_
- configurations: Short and long baseline antenna configurations combined.  
  > "Some projects had two different scheduling blocks using different antenna configurations to cover short and long baselines." (Observations)
- baselines: New Band 3, 2019 Jun 24: 83–16196 m; archival Band 3, 2017 Aug 01: 17–3108 m.  
  > "| 2018.1.01218.S | E. Macías     | 2019 Jun 24 | 43.5       | 83 – 16196  | 90.5, 92.5, 102.5, 104.5   | J1037-2934 | 5.4.0         |" (Table 1); "| 2016.1.00229.S | E. Bergin     | 2017 Aug 01 | 43.0       | 17 – 3108   | 97.8                       | J1037-2934 | 4.7.2         |" (Table 1)
- angular resolution: New 3.1 mm observations: ~50 milliarcseconds; modeling images: 0.05 arcsec circular beam.  
  > "We present new $\sim50$ milliarcsecond angular resolution ALMA observations of the 3.1 mm continuum emission of the protoplanetary disk around TW Hya." (Summary and conclusions); "To this end, new images with a common beam size of $0\rlap.''05\times0\rlap.''05$ were produced." (Dust characterization)
- max recoverable scale: _not stated_
- sensitivity: Band 3: 4.5 microJy beam^-1 at robust=0.5; 13 microJy beam^-1 at robust=-1.0.  
  > "| 3 | 97.5 | 3.08 | 0.5 | $0\rlap.''052\times0\rlap.''050$, PA$=-10^{\circ}$ | 4.5 | 164 | $59.8\pm0.3$ ($\pm3$) |" (Table 2); "| \- | 97.5 | 3.08 | -1.0 | $0\rlap.''034\times0\rlap.''033$, PA$=74^{\circ}$ | 13 | 43 | $42.3\pm1.3$ ($\pm3$) |" (Table 2)
- time on source: 2019 Jun 24 Band 3 execution: 43.5 min; 2017 Aug 01 archival Band 3 execution: 43.0 min.  
  > "| 2018.1.01218.S | E. Macías     | 2019 Jun 24 | 43.5       | 83 – 16196  | 90.5, 92.5, 102.5, 104.5   | J1037-2934 | 5.4.0         |" (Table 1); "| 2016.1.00229.S | E. Bergin     | 2017 Aug 01 | 43.0       | 17 – 3108   | 97.8                       | J1037-2934 | 4.7.2         |" (Table 1)
- observing dates: New Band 3: five executions, 2019 June 24–2019 July 08.  
  > "The new ALMA long baseline observations at 3 mm (Band 3) were obtained during Cycle 6 in five different executions carried out from 2019 June 24 to 2019 July 08 (project code: 2018.1.01218.S)." (Observations)
- pi or archival as stated: New Band 3 PI: E. Macías; archival shorter-baseline Band 3 and Bands 7, 6, 4.  
  > "| 2018.1.01218.S | E. Macías     | 2019 Jun 24 | 43.5       | 83 – 16196  | 90.5, 92.5, 102.5, 104.5   | J1037-2934 | 5.4.0         |" (Table 1); "Additionally, we retrieved lower resolution archival data at 3 mm to cover the shorter baselines, as well as archival data at Bands 7, 6, and 4." (Observations)
- Other facility **Gaia DR2**: Position and proper motions for phase-center corrections.  
  > "as determined from the position and proper motions reported by Gaia DR2 (cite: gai18), using the task `fixvis` in `CASA`." (Observations)
- Other facility **Herschel**: Literature HD-based total gas mass for gas-to-dust ratios.  
  > "the total gas mass in TW Hya has been estimated to be around $0.05~M_{\odot}$ using *Herschel* observations of HD line transitions (cite: ber13)." (On the total dust mass of TW Hya)
- External data: Distance d=59.5; unit not stated in supplied text.  
  > "It is among the closest protoplanetary disks to Earth ($d=59.5$; (cite: bai18; gai18))" (Introduction) [from (cite: bai18; gai18)]
- External data: Gaia DR2 position and proper motions.  
  > "as determined from the position and proper motions reported by Gaia DR2 (cite: gai18)" (Observations) [from Gaia DR2 (cite: gai18)]
- External data: Deprojection inclination 5 degrees and position angle 152 degrees.  
  > "The deprojection was performed using an inclination of $5^{\circ}$ and a position angle of $152^{\circ}$ (cite: hua18a)." (Observational results) [from (cite: hua18a)]
- External data: Locations of bright and dark annular features.  
  > "This figure also shows the position of some of the bright (i.e., "rings") and dark (i.e., "gaps") annular features in the disk listed by (cite: hua18b)." (Observational results) [from (cite: hua18b)]
- External data: Stellar luminosity 0.23 L_sun used to center the temperature prior.  
  > "assuming a normal distribution for $L_{\star}$ centered at $0.23$ L$_{\odot}$ (cite: sok18) with a standard deviation of $15\%$" (Dust characterization) [from (cite: sok18)]
- External data: Stellar mass 0.6 M_sun for Toomre Q.  
  > "as well as a stellar mass of $0.6~M_{\odot}$ (cite: sok18)." (Modeling results) [from (cite: sok18)]
- External data: Gas surface-density estimates and C18O-based midplane temperature around 27 K at 20 au.  
  > "the current estimates of its gas surface density (cite: zha17)" (Dust grain size in TW Hya: small ($a_{max}<50~\mu$m) or large ($a_{max}>1$ mm)); "midplane temperature estimations based on C$^{18}$O observations yield values around 27 K at 20 au (cite: zha17)" (Dust grain size in TW Hya: small ($a_{max}<50~\mu$m) or large ($a_{max}>1$ mm)) [from (cite: zha17)]
- External data: Previous 9 mm free-free estimate ~0.1 mJy (~5%) and 9 mm visibility profile.  
  > "with an estimated relatively small contribution of $\sim0.1$ mJy ($\sim5\%$) at 9 mm according to (cite: men14)." (Free-free emission inside the 3 au cavity); "Such a high contribution from a central compact source seems extremely unlikely given the visibility profile of the 9 mm data (cite: men14)." (Free-free emission inside the 3 au cavity) [from (cite: men14)]
- External data: Low-S/N polarized continuum detection with toroidal polarization angles; detected only beyond 40 au.  
  > "So far, only a low S/N detection of (sub)millimeter polarized continuum emission toward the disk of TW Hya has been reported (cite: vle19)." (Dust grain size in TW Hya: small ($a_{max}<50~\mu$m) or large ($a_{max}>1$ mm)); "The polarization angle of the emission shows a toroidal geometry, indicating an origin different than self-scattering." (Dust grain size in TW Hya: small ($a_{max}<50~\mu$m) or large ($a_{max}>1$ mm)); "However, polarized emission is only detected in the outer regions of the disk ($r>40$ au)." (Dust grain size in TW Hya: small ($a_{max}<50~\mu$m) or large ($a_{max}>1$ mm)) [from (cite: vle19)]
- External data: Inner-disk comparison model: a_max=300 micrometers and Sigma_d=10 g cm^-2 at 10 au.  
  > "the results obtained by (cite: ued20), who modeled the SED of the inner disk of TW Hya and found $a_{max}=300~\mu$m and $\Sigma_d=10$ g cm$^{-2}$ at 10 au." (The optically thick inner disk ($r<20$ au)) [from (cite: ued20)]
- External data: Total gas mass ~0.05 M_sun.  
  > "the total gas mass in TW Hya has been estimated to be around $0.05~M_{\odot}$ using *Herschel* observations of HD line transitions (cite: ber13)." (On the total dust mass of TW Hya) [from (cite: ber13)]
- External data: Gas radial extent ~200 au.  
  > "The radial extent of the millimeter dust ($\sim70$ au) is much lower than that of the gas ($\sim200$ au; (cite: hua18a))" (On the total dust mass of TW Hya) [from (cite: hua18a)]
- External data: CO sublimation temperature 23–28 K.  
  > "the only major volatile snowline that could coincide with the substructures at $r>20$ au is the CO one ($T_{sub}=23-28$ K; (cite: zha15))." (Insights on the origin of disk substructures) [from (cite: zha15)]
- External data: DSHARP dust composition and opacity prescription.  
  > "Additionally, we adopt the dust composition used by the DSHARP program, computed with the Python package `dsharp_opac` (cite: bir18)." (Dust characterization) [from (cite: bir18)]
- Simulation/model as data: Streaming-instability simulations: ~1–10 mm particles concentrated at local gas-to-dust mass ratios smaller than 25.  
  > "According to numerical simulations, the streaming instability can be triggered in protoplanetary disks as long as $\sim1-10$ mm particles are concentrated with local gas-to-dust mass ratios smaller than 25 (cite: car15; yan17)." (Introduction)
- Simulation/model as data: Dust-settling model comparison: high optical depths can bias inferred maximum grain sizes.  
  > "This effect was explored by (cite: sie20), who showed that the combination of settling and high optical depth might indeed result in an incorrect estimate of the maximum grain size if $\Sigma_d\gtrsim3$ g cm$^{-2}$." (The optically thick inner disk ($r<20$ au))
- Simulation/model as data: MRI-driven zonal-flow comparison predicts shallow gas-density perturbations ~10–20%.  
  > "On the other hand, zonal flows driven by MRI turbulence should produce relatively shallow gas density perturbations ($\sim10-20\%$; (cite: sim14))." (Insights on the origin of disk substructures)

## Processing

### Calibration

- pipeline or manual: ALMA staff calibration pipeline and scripts; execution inspection and additional flagging as necessary.  
  > "Data calibration was performed using the calibration pipeline and scripts developed by ALMA staff." (Observations); "The data for each execution were revised, and additional flagging was applied when necessary." (Observations)
- casa version: 5.4.0 for new Band 3 calibration; 5.6.1 for further processing and cleaning.  
  > "| 2018.1.01218.S | E. Macías     | 2019 Jun 24 | 43.5       | 83 – 16196  | 90.5, 92.5, 102.5, 104.5   | J1037-2934 | 5.4.0         |" (Table 1); "For further data processing and cleaning, `CASA` version 5.6.1 was used." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: New Band 3: J1037-2934 and J1307-2934.  
  > "| 2018.1.01218.S | E. Macías     | 2019 Jun 24 | 43.5       | 83 – 16196  | 90.5, 92.5, 102.5, 104.5   | J1037-2934 | 5.4.0         |" (Table 1); "|                |               | 2019 Jun 27 | 43.5       | 83 – 14969  | 90.5, 92.5, 102.5, 104.5   | J1307-2934 | 5.4.0         |" (Table 1)
- flux scale uncertainty: 10% at Band 7; 5% at Bands 6, 4, 3.  
  > "We set this systematic error to the nominal values of $10\%$ at Band 7, and $5\%$ at Bands 6, 4, and 3." (Dust characterization)
- self calibration: Iterative phase self-calibration with decreasing solution intervals; amplitude self-calibration attempted; separate scheduling blocks, then combined datasets.  
  > "Phase self-calibration was performed first, in an iterative process starting with longer time solution intervals and decreasing them until no improvement was seen in the peak signal-to-noise ratio (S/N) or until reaching the integration time of the data." (Observations); "Then, amplitude self-calibration was attempted, although it only provided improvements in the S/N in a few cases with low resolution and very high S/N." (Observations); "For these projects each scheduling block was first self-calibrated separately after combining the multiple executions of each scheduling block." (Observations)

### Imaging

- task: CASA statwt, then tclean.  
  > "Once the final self-calibrated combined measurement sets were obtained, the `CASA` task `statwt` was used to recompute the weights." (Observations); "Finally, the data were imaged using the task `tclean`." (Observations)
- deconvolver: mtmfs, nterms=2.  
  > "The `mtmfs` deconvolver was employed, setting $nterms=2$, and using multiple scales at 0 (point-source), 1, 3, and 5 times the beam size." (Observations)
- weighting robust: Self-calibration: briggs, robust=0.5; final-image robust values explored for resolution/sensitivity balance.  
  > "and `briggs` weighting with $robust=0.5$." (Observations); "Different values of the $robust$ parameter were explored to find a balance between angular resolution and sensitivity." (Observations)
- uv taper: Different Band 4 uv-tapers explored to circularize its elongated beam; common-beam modeling images also used robust/uvtaper exploration.  
  > "The original synthesized beam shape of the Band 4 data was quite elongated, so we also explored different uv-taper values to get a more circular beam shape." (Observations); "This was done by first exploring different robust and uvtaper parameters that yielded beam sizes slightly smaller than $0\rlap.''05\times0\rlap.''05$" (Dust characterization)
- cell size: ~0.1 times the beam size.  
  > "The pixel size was set to $\sim0.1$ times the beam size." (Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: 0, 1, 3, 5 times the beam size; self-calibration of data poorer than ~1 arcsec used scales=0.  
  > "The `mtmfs` deconvolver was employed, setting $nterms=2$, and using multiple scales at 0 (point-source), 1, 3, and 5 times the beam size." (Observations); "For datasets with angular resolution poorer than $\sim1''$, a single point-source scale was used ($scales=0$)." (Observations)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Align positions, rescale fluxes, correct offsets, combine short/long baselines and projects, then self-calibrate together.  
  > "Afterward, the short and long baseline data were combined and self-calibrated." (Observations); "the coordinates were shifted and aligned to correct for proper motions, the flux was rescaled, position offsets were corrected if present, and finally the data were combined and self-calibrated together." (Observations)
- smoothing: CASA imsmooth convolution to a common 0.05 arcsec circular beam.  
  > "and then using the `CASA` task `imsmooth` to convolve these images to the desired common beam." (Dust characterization); "To this end, new images with a common beam size of $0\rlap.''05\times0\rlap.''05$ were produced." (Dust characterization)
- final beam: Modeling: 0.05 x 0.05 arcsec; Band 3 standard image: 0.052 x 0.050 arcsec, PA=-10 degrees.  
  > "To this end, new images with a common beam size of $0\rlap.''05\times0\rlap.''05$ were produced." (Dust characterization); "| 3 | 97.5 | 3.08 | 0.5 | $0\rlap.''052\times0\rlap.''050$, PA$=-10^{\circ}$ | 4.5 | 164 | $59.8\pm0.3$ ($\pm3$) |" (Table 2)
- final rms: Band 3 standard image: 4.5 microJy beam^-1; rms measured in a 2–4 arcsec annulus.  
  > "| 3 | 97.5 | 3.08 | 0.5 | $0\rlap.''052\times0\rlap.''050$, PA$=-10^{\circ}$ | 4.5 | 164 | $59.8\pm0.3$ ($\pm3$) |" (Table 2); "The rms was measured within an annulus with $2''$ of inner radius and $4''$ of outer radius." (Observations)

### Inherited from earlier work

- Relative flux rescaling from overlapping, deprojected real visibilities.  
  > "we rescaled the fluxes following a similar procedure to (cite: and18a)" (Observations) [from (cite: and18a)]
- Gaia DR2 astrometry for execution-dependent phase centers.  
  > "as determined from the position and proper motions reported by Gaia DR2 (cite: gai18)" (Observations) [from Gaia DR2 (cite: gai18)]
- Inclination 5 degrees and position angle 152 degrees.  
  > "The deprojection was performed using an inclination of $5^{\circ}$ and a position angle of $152^{\circ}$ (cite: hua18a)." (Observational results) [from (cite: hua18a)]
- DSHARP annular-feature naming convention, including plateau-like features.  
  > "We follow the naming convention from DSHARP (cite: hua18b)" (Observational results); "Following the naming criterion for "plateau"-like features by (cite: hua18b), we label these three features as B7, B16, and B54." (Observational results) [from DSHARP (cite: hua18b)]
- 1D vertically isothermal slab emergent-intensity prescription.  
  > "Given these assumptions, the emergent intensity at a particular radius can be computed as a 1D vertically isothermal slab (cite: sie19; car19)" (Dust characterization) [from (cite: sie19; car19)]
- Anisotropic scattering approximation using an effective scattering coefficient.  
  > "Following (cite: car19), we also include an approximation for anisotropic scattering by replacing the scattering coefficient $\sigma_{\nu}$ with an effective scattering coefficient" (Dust characterization) [from (cite: car19)]
- Compare fixed p=3.5 with a free-p model.  
  > "a model with the slope fixed to the standard $p=3.5$, as well as a model where we let $p$ be a free parameter (cite: mac19)." (Dust characterization) [from (cite: mac19)]
- DSHARP dust composition computed with dsharp_opac.  
  > "Additionally, we adopt the dust composition used by the DSHARP program, computed with the Python package `dsharp_opac` (cite: bir18)." (Dust characterization) [from DSHARP program (cite: bir18)]
- Passively irradiated flared-disk temperature prescription for the temperature prior.  
  > "we use a prior for the dust temperature at each radius based on the expected temperature profile of a passively irradiated flared disk in radiative equilibrium (cite: chi97; dul01)" (Dust characterization) [from (cite: chi97; dul01)]
- Flaring-angle range 0.01–0.06 for the temperature prior.  
  > "We compute this prior by varying $\varphi$ within the typical values $0.01-0.06$ (cite: hua18b)" (Dust characterization) [from (cite: hua18b)]
- Stellar luminosity 0.23 L_sun and mass 0.6 M_sun.  
  > "assuming a normal distribution for $L_{\star}$ centered at $0.23$ L$_{\odot}$ (cite: sok18)" (Dust characterization); "as well as a stellar mass of $0.6~M_{\odot}$ (cite: sok18)." (Modeling results) [from (cite: sok18)]
- Survey-style mass comparison: kappa=10 cm^2 g^-1 at 1000 GHz, beta=1, T=20 K.  
  > "Assuming the same standard dust opacity law ($\kappa=10$ cm$^2$ g$^{-1}$ at 1000 GHz, with $\beta=1$) and dust temperature (20 K) as (cite: and05)" (On the total dust mass of TW Hya) [from (cite: and05)]

### Not stated but needed to reproduce (our reading)

- Exact SPW and execution selection, including the role of 2016.1.01158.S, which appears in the acknowledgements but not the observation table.
- Additional flagging selections for each execution.
- Reference execution, overlapping uv-distance bins, and multiplicative flux-rescaling factor at each band.
- Exact astrometric shifts and Gaussian-fit regions applied to each scheduling block.
- Self-calibration solution intervals, gain-solver settings, accepted rounds, and which amplitude solutions were applied.
- Cleaning masks, image dimensions, stopping thresholds, iteration limits, and exact pixel sizes.
- Numerical uv-tapers, including the Band 4 table footnote whose content is absent from the supplied text.
- Exact robust and uv-taper settings for the common-beam modeling images.
- Radial annulus widths, sampling grid, and outer integration boundary for dust masses.
- dsharp_opac version, dust-mixture numerical inputs, and opacity-grid interpolation details.
- Prior sampling measure for flaring angle and uniform priors on logarithmically gridded parameters.
- Whether the large-particle posterior upper limit is 10 cm or 100 cm.
- Inner radius used when extrapolating the surface-density power law and integrating total masses.
- Procedure for propagating radial posterior uncertainties and correlated flux-scale errors into mass uncertainties.

## Analysis recipe

1. **Align and rescale calibrated executions**: Shift phase centers using Gaia DR2, align field coordinates with table, compare binned overlapping deprojected real visibilities, rescale with gencal, and combine executions.  
  > "as determined from the position and proper motions reported by Gaia DR2 (cite: gai18), using the task `fixvis` in `CASA`." (Observations); "Then, the `table` tool in `CASA` was used to modify the coordinates of the field to align the different executions" (Observations); "One of the two datasets was then rescaled using the task `gencal`." (Observations)
   - software: CASA, fixvis, table, gencal
   - parameter: Compare overlapping uv coverage with an upper limit of 800 klambda.  
  > "selected a range of uv-distances where the uv coverage of two datasets overlaps (with an upper limit of 800 $k\lambda$ to avoid decorrelation issues)" (Observations)
   - parameter: Select reference dataset using flux calibrator, time since flux monitoring, and calibrator behavior.  
  > "The reference dataset at each band was selected based on the flux calibrator used, the time between the observation and the last flux monitoring of that calibrator, and the behavior of the calibrator during that time." (Observations)
   - assumption: Keep measurement sets in ICRS.  
  > "In order to keep our data in the ICRS system we used the `table` tool to manually change the coordinates of the field in the measurement sets." (Observations)
   - fitting: Gaussian image fits to measure significant scheduling-block position offsets.  
  > "it was corrected by measuring the position of the emission with Gaussian fits to the images and then aligning the visibilities." (Observations)
   - validation: Check scheduling-block offsets; correct offsets larger than one-third of the extended-configuration beam.  
  > "If a significant offset was found (offsets larger than $1/3$ the extended configuration beam size)" (Observations)
2. **Self-calibrate and combine datasets**: Iterative phase self-calibration, amplitude trials, separate scheduling-block calibration, then combined-data self-calibration and final interband centering.  
  > "Afterward, the short and long baseline data were combined and self-calibrated." (Observations); "A final shift was applied to the self-calibrated combined data to ensure that the data at the different bands were centered at the same position." (Observations)
   - software: CASA, tclean, mtmfs
   - parameter: mtmfs, nterms=2; briggs robust=0.5.  
  > "Imaging during self-calibration was performed using the task `tclean` with the `mtmfs` deconvolver (cite: rau11)" (Observations); "assuming that the frequency dependency of the emission follows a Taylor expansion to quadratic terms (i.e., $nterms=2$), and `briggs` weighting with $robust=0.5$." (Observations)
   - fitting: _not stated_
   - validation: Stop decreasing solution intervals at no peak-S/N improvement or integration time; inspect data and solutions after each step.  
  > "until no improvement was seen in the peak signal-to-noise ratio (S/N) or until reaching the integration time of the data." (Observations); "The data and self-calibration solutions were checked after each step to verify that self-calibration did correct for small shifts in position." (Observations)
3. **Image continuum and measure integrated flux**: Recompute weights with statwt, image with multiscale mtmfs tclean, produce higher-resolution maps, and integrate emission in a 2 arcsec radius circle.  
  > "Once the final self-calibrated combined measurement sets were obtained, the `CASA` task `statwt` was used to recompute the weights." (Observations); "The `mtmfs` deconvolver was employed, setting $nterms=2$, and using multiple scales at 0 (point-source), 1, 3, and 5 times the beam size." (Observations); "The flux densities were obtained by integrating the emission within a $2''$ radius circle." (Observations)
   - software: CASA, statwt, tclean, mtmfs
   - parameter: Band 7 standard image: 346.8 GHz, robust=-0.2, beam 0.036 x 0.028 arcsec, rms 26 microJy beam^-1.  
  > "| 7 | 346.8 | 0.865 | -0.2 | $0\rlap.''036\times0\rlap.''028$, PA$=73^{\circ}$ | 26 | 90 | $1542\pm3$ ($\pm150$) |" (Table 2)
   - parameter: Band 6 standard image: 233.0 GHz, robust=0.0, beam 0.036 x 0.031 arcsec, rms 9.5 microJy beam^-1.  
  > "| 6 | 233.0 | 1.29 | 0.0 | $0\rlap.''036\times0\rlap.''031$, PA$=-85^{\circ}$ | 9.5 | 135 | $575.4\pm0.9$ ($\pm30$) |" (Table 2)
   - parameter: Band 4 standard image: 145.0 GHz, robust=-0.6, beam 0.046 x 0.039 arcsec, rms 12 microJy beam^-1.  
  > "| 4 | 145.0 | 2.07 | -0.6$^{b}$ | $0\rlap.''046\times0\rlap.''039$, PA$=46^{\circ}$ | 12 | 62 | $151.1\pm0.9$ ($\pm8$) |" (Table 2)
   - parameter: Band 3 standard image: 97.5 GHz, robust=0.5, beam 0.052 x 0.050 arcsec, rms 4.5 microJy beam^-1.  
  > "| 3 | 97.5 | 3.08 | 0.5 | $0\rlap.''052\times0\rlap.''050$, PA$=-10^{\circ}$ | 4.5 | 164 | $59.8\pm0.3$ ($\pm3$) |" (Table 2)
   - fitting: _not stated_
   - validation: Explore robust for resolution/sensitivity balance; measure rms in a 2–4 arcsec annulus.  
  > "Different values of the $robust$ parameter were explored to find a balance between angular resolution and sensitivity." (Observations); "The rms was measured within an annulus with $2''$ of inner radius and $4''$ of outer radius." (Observations)
4. **Measure radial intensity profiles**: Deproject images and average emission in concentric ellipses; estimate errors of the mean using beam areas as independent units.  
  > "The radial intensity profiles were obtained by averaging the emission in concentric ellipses with this same inclination and position angle." (Observational results); "The uncertainty of the radial profiles is computed as the error of the mean at each radius, considering the beam size as the smallest independent unit of area" (Observational results)
   - assumption: Inclination 5 degrees; position angle 152 degrees.  
  > "The deprojection was performed using an inclination of $5^{\circ}$ and a position angle of $152^{\circ}$ (cite: hua18a)." (Observational results)
   - fitting: _not stated_
   - validation: Plot within-ellipse standard deviations alongside errors of the mean.  
  > "For comparison, the standard deviation at each radius is also potted in the radial profiles" (Observational results)
5. **Measure spectral-index structure**: Joint multiband tclean imaging with mtmfs nterms=2; azimuthally average spectral-index maps.  
  > "Furthermore, spectral index ($\alpha$) maps were obtained combining data at multiple bands in the task `tclean`." (Observations); "The deconvolver algorithm `mtmfs` was employed for this purpose, using `nterms=2`." (Observations); "The solid line in each panel shows the azimuthally averaged value of the spectral index, with the shaded colored region indicating the error of the mean." (Spectral index profiles)
   - software: CASA, tclean, mtmfs
   - parameter: Bands 7+6: robust=0.0, beam 0.037 x 0.031 arcsec.  
  > "| 7+6 | 290.5 | 1.03 | 0.0 | $0\rlap.''037\times0\rlap.''031$, PA$=-89^{\circ}$ |" (Table 3)
   - parameter: Bands 6+4: robust=0.2, beam 0.043 x 0.036 arcsec.  
  > "| 6+4 | 190.0 | 1.58 | 0.2 | $0\rlap.''043\times0\rlap.''036$, PA$=64^{\circ}$ |" (Table 3)
   - parameter: Bands 4+3: robust=0.3, beam 0.048 x 0.044 arcsec.  
  > "| 4+3 | 121.3 | 2.47 | 0.3 | $0\rlap.''048\times0\rlap.''044$, PA$=39^{\circ}$ |" (Table 3)
   - assumption: Absolute flux uncertainties: 10% in Band 7, 5% in Bands 6, 4, 3.  
  > "assuming the nominal errors of 10% at Band 7, and 5% at Bands 6, 4, and 3" (Spectral index profiles)
   - fitting: _not stated_
   - validation: Compare profiles with previous results and display possible systematic shifts from flux calibration.  
  > "Our spectral index profiles at 0.87-1.3 mm and 1.3-2.1 mm are similar to those obtained by (cite: hua18a) and (cite: tsu16), respectively." (Spectral index profiles); "This shift, however, will not affect the relative changes with radius seen in the individual profiles." (Spectral index profiles)
6. **Characterize central free-free emission**: Measure high-resolution flux inside r<2 au, calculate interband spectral indices, and extrapolate the 3.1 mm flux to 9 mm.  
  > "We do so by measuring the flux inside the $r<2$ au region around the star." (Free-free emission inside the 3 au cavity); "Using the 3.1 mm flux, and assuming a constant $2.1-9$ mm spectral index of $0.72\pm0.18$, we would obtain a 9 mm free-free contribution of $0.34\pm0.06$ mJy" (Free-free emission inside the 3 au cavity)
   - parameter: Central-source aperture r<2 au.  
  > "We do so by measuring the flux inside the $r<2$ au region around the star." (Free-free emission inside the 3 au cavity)
   - assumption: Constant spectral index 0.72±0.18 between 2.1 and 9 mm for the extrapolation.  
  > "assuming a constant $2.1-9$ mm spectral index of $0.72\pm0.18$" (Free-free emission inside the 3 au cavity)
   - fitting: _not stated_
   - validation: Compare aperture-derived indices with spectral-index maps; check flat-spectrum alternatives against the 9 mm visibility profile.  
  > "These indices are very similar to the values found at the position of the star in the spectral index maps (1.8, 1.3, and 0.6, respectively)." (Free-free emission inside the 3 au cavity); "Such a high contribution from a central compact source seems extremely unlikely given the visibility profile of the 9 mm data (cite: men14)." (Free-free emission inside the 3 au cavity)
7. **Prepare common-resolution dust models**: Convolve images to a common beam; model radial intensities with a 1D vertically isothermal slab including absorption and anisotropic scattering.  
  > "and then using the `CASA` task `imsmooth` to convolve these images to the desired common beam." (Dust characterization); "Given these assumptions, the emergent intensity at a particular radius can be computed as a 1D vertically isothermal slab (cite: sie19; car19)" (Dust characterization); "Following (cite: car19), we also include an approximation for anisotropic scattering" (Dust characterization)
   - software: CASA, imsmooth, dsharp_opac
   - parameter: Common beam 0.05 x 0.05 arcsec; fit starts at 5 au.  
  > "To this end, new images with a common beam size of $0\rlap.''05\times0\rlap.''05$ were produced." (Dust characterization); "Our model is fitted to the azimuthally averaged intensity profiles from these images, starting at 5 au to avoid the inner regions with free-free contribution." (Dust characterization)
   - parameter: Minimum grain size fixed to 0.01 micrometers.  
  > "We fix this value to $0.01$ $\mu$m." (Dust characterization)
   - parameter: Effective scattering coefficient sigma_eff=(1-g_nu)sigma_nu.  
  > "defined as $\sigma^{\rm{eff}}_{\nu}=(1-g_{\nu})\sigma_{\nu}$, where $g_{\nu}$ is the forward scattering parameter." (Dust characterization)
   - assumption: Axisymmetric, geometrically thin, vertically isothermal disk.  
  > "we aim at modeling the radial intensity profiles at each wavelength assuming an axisymmetric protoplanetary disk." (Dust characterization); "The disk is also assumed to be geometrically thin and vertically isothermal" (Dust characterization)
   - assumption: DSHARP dust composition; power-law particle-size distribution n(a) proportional to a^-p.  
  > "assuming that the particle size distribution follows a power law with slope $p$ ($n(a)\propto a^{-p}$, where $a$ is the particle radius)" (Dust characterization); "Additionally, we adopt the dust composition used by the DSHARP program, computed with the Python package `dsharp_opac` (cite: bir18)." (Dust characterization)
   - fitting: Fit each radius independently; do not convolve the model.  
  > "We note that we do not convolve the model, since each radius is fitted independently." (Dust characterization)
   - validation: _not stated_
8. **Infer radial dust posteriors**: Bayesian uniform-grid exploration of T_d, Sigma_d, a_max; compare fixed p=3.5 with free p; marginalize posteriors and calculate expected values.  
  > "We adopt a Bayesian approach to obtain the posterior probability distributions of the model parameters at each radius." (Dust characterization); "Given the low number of free parameters, we can compute the posteriors by simply exploring the parameter space with a uniform grid within reasonable values." (Dust characterization); "a model with the slope fixed to the standard $p=3.5$, as well as a model where we let $p$ be a free parameter (cite: mac19)." (Dust characterization)
   - parameter: T_d x Sigma_d x a_max grid: 115 x 225 x 100; free-p model adds 60 values.  
  > "We vary $T_d$, $\Sigma_d$, and $a_{max}$ in a $115\times225\times100$ grid, respectively." (Dust characterization); "The model with a varying $p$ additionally explores 60 values of this parameter." (Dust characterization)
   - parameter: T_d=4–50 K in 0.4 K steps.  
  > "$T_d$ is varied from $4$ to $50$ K, in steps of $0.4$ K." (Dust characterization)
   - parameter: Sigma_d=10^-3–10^1.5 g cm^-2, 0.02 dex; a_max=10^-3–100 cm, 0.05 dex.  
  > "$\Sigma_d$ and $a_{max}$ are explored in logarithmic space in steps of $0.02$ dex from $10^{-3}$ g cm$^{-2}$ to $10^{1.5}$ g cm$^{-2}$, and in steps of $0.05$ dex from $10^{-3}$ cm ($10~\mu$m) to $100$ cm, respectively." (Dust characterization)
   - parameter: p=2.5–4.3 in 0.03 steps.  
  > "Finally, $p$ is varied from 2.5 to 4.3 in steps of 0.03." (Dust characterization)
   - parameter: Intensity uncertainty combines radial error of the mean and absolute flux-calibration error in quadrature; calibration errors 10%, 5%, 5%, 5% for Bands 7, 6, 4, 3.  
  > "\hat{\sigma}_{\bar{I},i} = \sqrt{\sigma_{\bar{I},i}^2 + (\delta_i \bar{I}_i)^2}" (Dust characterization); "We set this systematic error to the nominal values of $10\%$ at Band 7, and $5\%$ at Bands 6, 4, and 3." (Dust characterization)
   - assumption: Temperature prior from passive irradiated-disk radiative equilibrium; flaring angle 0.01–0.06; normal stellar luminosity 0.23 L_sun with 15% standard deviation.  
  > "we use a prior for the dust temperature at each radius based on the expected temperature profile of a passively irradiated flared disk in radiative equilibrium (cite: chi97; dul01)" (Dust characterization); "We compute this prior by varying $\varphi$ within the typical values $0.01-0.06$ (cite: hua18b)" (Dust characterization); "assuming a normal distribution for $L_{\star}$ centered at $0.23$ L$_{\odot}$ (cite: sok18) with a standard deviation of $15\%$" (Dust characterization)
   - assumption: Uniform priors for Sigma_d, a_max, and p.  
  > "The priors for the other three model parameters are set as uniform priors." (Dust characterization)
   - fitting: Standard log-normal likelihood as named in the paper; direct grid evaluation, without a named sampler.  
  > "We use a standard log-normal likelihood function" (Dust characterization); "we can compute the posteriors by simply exploring the parameter space with a uniform grid within reasonable values." (Dust characterization)
   - validation: Compare maximum-posterior intensity profiles with observations and inspect 2D parameter posteriors at 25, 30, 45 au.  
  > "the intensity profile of the model with maximum posterior probability at each wavelength" (Modeling results); "three corner plots with the 2D posteriors at some representative radii (25 au, 30 au, and 45 au)." (Modeling results)
9. **Test grain-size families and optical depth**: Split small/large-grain posteriors, compare physical temperatures and gravitational stability, and calculate posterior-weighted optical depths.  
  > "we compute the posterior probability distributions after splitting the $a_{max}$ range into small ($10~\mu$m$<a_{max}<200~\mu$m) and large particles ($200~\mu$m$<a_{max}<10$ cm)." (Modeling results); "For comparison, we also plot the dust surface density profiles for which the Toomre $Q$ parameter would be equal to 1, assuming two different values of the gas-to-dust mass ratio (100 and 10)." (Modeling results); "we computed the expected value of the optical depth at each radius" (The optically thick inner disk ($r<20$ au))
   - parameter: Small-grain split: 10<a_max<200 micrometers; large-grain split: 200 micrometers<a_max<10 cm.  
  > "small ($10~\mu$m$<a_{max}<200~\mu$m) and large particles ($200~\mu$m$<a_{max}<10$ cm)." (Modeling results)
   - parameter: Optical-depth posterior marginalized over T_d.  
  > "is the posterior probability of our model at each cell of the grid, marginalized over $T_d$." (The optically thick inner disk ($r<20$ au))
   - assumption: Toomre comparison: gas-to-dust ratios 100 and 10; stellar mass 0.6 M_sun; fitted expected temperature.  
  > "assuming two different values of the gas-to-dust mass ratio (100 and 10)." (Modeling results); "We use the expected value of the temperature" (Modeling results); "as well as a stellar mass of $0.6~M_{\odot}$ (cite: sok18)." (Modeling results)
   - fitting: Posterior marginalization and expectation values within each grain-size family.  
  > "we compute the posterior probability distributions after splitting the $a_{max}$ range" (Modeling results); "The red curve in these plots indicates the expected value of each parameter" (Modeling results)
   - validation: Favor large grains using disk axisymmetry, gas-density estimates, and C18O temperatures; identify poor inner-disk fits and optical-depth coincidence.  
  > "midplane temperature estimations based on C$^{18}$O observations yield values around 27 K at 20 au (cite: zha17)" (Dust grain size in TW Hya: small ($a_{max}<50~\mu$m) or large ($a_{max}>1$ mm)); "The high degree of axisymmetry of the disk of TW Hya indicates that its density profile should be below these limits." (Modeling results); "the jump at $r\sim20$ au is coincident with the region of the disk where the optical depth is larger than 1 at all wavelengths." (The optically thick inner disk ($r<20$ au))
10. **Interpret rings and gaps**: Compare radial Sigma_d, a_max, and p across rings/gaps; estimate density-contrast lower limits and compare snowline, MHD, and planet-disk scenarios.  
  > "our analysis also shows that the ringed substructures in TW Hya are reproduced with higher dust densities paired with higher abundances of large dust particles" (The dust content at $r>20$ au and its impact on planet formation); "From the predicted dust surface density, we estimate contrasts $\gtrsim2$." (Insights on the origin of disk substructures)
   - parameter: Contrast lower limits at D25 and D41.  
  > "we can estimate lower limits at the two wide gaps in TW Hya (D25 and D41)." (Insights on the origin of disk substructures)
   - assumption: Flatter particle-size slopes imply a higher abundance of large particles.  
  > "a flatter slope of the particle size distribution will result in a higher abundance of large dust particles." (The dust content at $r>20$ au and its impact on planet formation)
   - fitting: _not stated_
   - validation: Account for ring contamination of gaps; compare inferred contrasts and axisymmetry with proposed mechanisms.  
  > "some emission from the rings will contaminate these features." (The dust content at $r>20$ au and its impact on planet formation); "The high degree of axisymmetry displayed by TW Hya also appears hard to reconcile with the dead zone scenario (cite: rug16)." (Insights on the origin of disk substructures)
11. **Estimate dust masses and survey bias**: Integrate expected dust surface density outside 20 au; extrapolate an inner power law for total mass; compare with literature gas mass and survey-style continuum masses.  
  > "By integrating the expected value of the dust surface density obtained with our multiwavelength analysis, we can also obtain an estimate of the total mass of solids in the disk of TW Hya." (On the total dust mass of TW Hya); "In order to obtain an estimate of the total dust mass we assume that the dust surface density profile at $r<20$ au follows a power law" (On the total dust mass of TW Hya)
   - parameter: Inner profile normalized to Sigma_d at 20 au; gamma explored between 1 and 1.5.  
  > "where $\Sigma_{d,20}$ is the dust surface density at 20 au." (On the total dust mass of TW Hya); "By exploring values of $\gamma$ between 1 and 1.5" (On the total dust mass of TW Hya)
   - assumption: Gas mass ~0.05 M_sun from Herschel HD literature measurements.  
  > "the total gas mass in TW Hya has been estimated to be around $0.05~M_{\odot}$ using *Herschel* observations of HD line transitions (cite: ber13)." (On the total dust mass of TW Hya)
   - assumption: Survey comparison assumes optically thin emission, kappa=10 cm^2 g^-1 at 1000 GHz, beta=1, T=20 K.  
  > "These measurements are obtained from a flux at (sub)millimeter wavelengths assuming that the dust emission is optically thin, a single dust temperature, and a single value for the dust opacity" (On the total dust mass of TW Hya); "Assuming the same standard dust opacity law ($\kappa=10$ cm$^2$ g$^{-1}$ at 1000 GHz, with $\beta=1$) and dust temperature (20 K) as (cite: and05)" (On the total dust mass of TW Hya)
   - fitting: Integrate posterior-derived surface densities; explore inner-profile slopes rather than fit the optically thick inner disk.  
  > "our results at $r<20$ au are likely incorrect, which prevents us from obtaining a robust total disk mass." (On the total dust mass of TW Hya); "By exploring values of $\gamma$ between 1 and 1.5" (On the total dust mass of TW Hya)
   - validation: Compare fixed/free-p masses and survey-style estimates; check optical depth against the optically thin assumption.  
  > "The range of dust masses decreases to $210-310~M_{\oplus}$ if $p$ is fixed to 3.5." (On the total dust mass of TW Hya); "the optical depth at 0.87 mm is higher than 1 up to $r\sim55$ au, so the optically thin assumption is surely far from valid for TW Hya." (On the total dust mass of TW Hya)

## Software

- **CASA** 5.6.1 for further processing and cleaning: Data processing and cleaning; calibration versions vary by dataset.  
  > "For further data processing and cleaning, `CASA` version 5.6.1 was used." (Observations); "used for the calibration of each dataset." (Observations)
- **fixvis** : Shift visibility phase centers using Gaia DR2 positions and proper motions.  
  > "as determined from the position and proper motions reported by Gaia DR2 (cite: gai18), using the task `fixvis` in `CASA`." (Observations)
- **table** : Modify field coordinates to align executions in ICRS.  
  > "In order to keep our data in the ICRS system we used the `table` tool to manually change the coordinates of the field in the measurement sets." (Observations)
- **gencal** : Rescale dataset fluxes.  
  > "One of the two datasets was then rescaled using the task `gencal`." (Observations)
- **tclean** : Self-calibration imaging, final continuum imaging, and multiband spectral-index maps.  
  > "Imaging during self-calibration was performed using the task `tclean`" (Observations); "Finally, the data were imaged using the task `tclean`." (Observations); "Furthermore, spectral index ($\alpha$) maps were obtained combining data at multiple bands in the task `tclean`." (Observations)
- **mtmfs** : Multiscale continuum and spectral-index deconvolution with nterms=2.  
  > "The `mtmfs` deconvolver was employed, setting $nterms=2$, and using multiple scales at 0 (point-source), 1, 3, and 5 times the beam size." (Observations); "The deconvolver algorithm `mtmfs` was employed for this purpose, using `nterms=2`." (Observations)
- **statwt** : Recompute measurement-set weights after final self-calibration and combination.  
  > "Once the final self-calibrated combined measurement sets were obtained, the `CASA` task `statwt` was used to recompute the weights." (Observations)
- **imsmooth** : Convolve images to a common beam for modeling.  
  > "and then using the `CASA` task `imsmooth` to convolve these images to the desired common beam." (Dust characterization)
- **dsharp_opac** : Compute adopted DSHARP dust opacities.  
  > "Additionally, we adopt the dust composition used by the DSHARP program, computed with the Python package `dsharp_opac` (cite: bir18)." (Dust characterization)
- **fixplanets** : Discussed as an alternative for field-coordinate changes; not used because the data were kept in ICRS.  
  > "This step is sometimes performed using the task `fixplanets` in `CASA`." (Observations); "However, this task only works if the data are in the FK5 celestial reference system." (Observations); "In order to keep our data in the ICRS system we used the `table` tool to manually change the coordinates of the field in the measurement sets." (Observations)
- **Astropy** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Integrated Band 7 flux density, standard image | 1542 | ±3 (±150) | mJy | 3 | / 7 / 346.8 / 0.865 / -0.2 / $0\rlap.''036\times0\rlap.''028$, PA$=73^{\circ}$ / 26 / 90 / $1542\pm3$ ($\pm150$) / |
| Integrated Band 6 flux density, standard image | 575.4 | ±0.9 (±30) | mJy | 3 | / 6 / 233.0 / 1.29 / 0.0 / $0\rlap.''036\times0\rlap.''031$, PA$=-85^{\circ}$ / 9.5 / 135 / $575.4\pm0.9$ ($\pm30$) / |
| Integrated Band 4 flux density, standard image | 151.1 | ±0.9 (±8) | mJy | 3 | / 4 / 145.0 / 2.07 / -0.6$^{b}$ / $0\rlap.''046\times0\rlap.''039$, PA$=46^{\circ}$ / 12 / 62 / $151.1\pm0.9$ ($\pm8$) / |
| Integrated Band 3 flux density, standard image | 59.8 | ±0.3 (±3) | mJy | 3 | / 3 / 97.5 / 3.08 / 0.5 / $0\rlap.''052\times0\rlap.''050$, PA$=-10^{\circ}$ / 4.5 / 164 / $59.8\pm0.3$ ($\pm3$) / |
| Central spectral index, 0.87–1.3 mm | 2.0 | ±0.3 | dimensionless | 6 | From these measurements we estimate a spectral index of $2.0\pm0.3$ at 0.87-1.3 mm, $1.24\pm0.16$ at 1.3-2.1 mm, and $0.72\pm0.18$ at 2.1-3.1 mm. |
| Central spectral index, 1.3–2.1 mm | 1.24 | ±0.16 | dimensionless | 6 | From these measurements we estimate a spectral index of $2.0\pm0.3$ at 0.87-1.3 mm, $1.24\pm0.16$ at 1.3-2.1 mm, and $0.72\pm0.18$ at 2.1-3.1 mm. |
| Central spectral index, 2.1–3.1 mm | 0.72 | ±0.18 | dimensionless | 6 | From these measurements we estimate a spectral index of $2.0\pm0.3$ at 0.87-1.3 mm, $1.24\pm0.16$ at 1.3-2.1 mm, and $0.72\pm0.18$ at 2.1-3.1 mm. |
| Extrapolated 9 mm free-free flux | 0.34 | ±0.06 | mJy | 6 | Using the 3.1 mm flux, and assuming a constant $2.1-9$ mm spectral index of $0.72\pm0.18$, we would obtain a 9 mm free-free contribution of $0.34\pm0.06$ mJy |
| Inferred 9 mm free-free fraction | ~20 | not stated | % | 6 | our observations indicate that the free-free contribution at 9 mm was likely underestimated, and that it is closer to $\sim20\%$ of the total flux at this wavelength. |
| Maximum grain-size lower limit at 20<r<60 au | >1 | not stated | mm | 9 | Despite this uncertainty, our model places an important constraint: $a_{max}$ must be larger than 1 mm at $20<r<60$ au. |
| Free-p radial slope trend at 20<r<60 au | ~3.5 to ~4.1 | not stated | dimensionless | 8 | Instead, the slope $p$ is robustly constrained, with a positive trend with radius (from $\sim3.5$ to $\sim4.1$), steeper slopes at the position of the gaps, and flatter ones at the rings. |
| Inner optically thick region at all wavelengths | <20 | not stated | au | 9 | The inner 20 au are completely optically thick at all four bands |
| Radius out to which 0.87 mm optical depth exceeds 1 | ~55 | not stated | au | 9 | the optical depth at 0.87 mm is higher than 1 up to $r\sim55$ au |
| Dust surface-density contrast lower limit at D25 and D41 | gtrsim2 | not stated | dimensionless | 10 | we can estimate lower limits at the two wide gaps in TW Hya (D25 and D41).; From the predicted dust surface density, we estimate contrasts $\gtrsim2$. |
| Dust mass outside 20 au, free p and a_max>200 micrometers | 158 | +17/-15 | M_earth | 11 | we obtain a dust mass at $r>20$ au of $158^{+17}_{-15}~M_{\oplus}$ for the model with $p$ as a free parameter |
| Dust mass outside 20 au, fixed p=3.5 and a_max>200 micrometers | 91 | +9/-8 | M_earth | 11 | and $91^{+9}_{-8}~M_{\oplus}$ with a fixed $p=3.5$. |
| Total dust mass with inner-profile extrapolation, free p | 250-330 | not stated | M_earth | 11 | By exploring values of $\gamma$ between 1 and 1.5, we estimate a range of total dust masses of $250-330~M_{\oplus}$ for the model with $p$ as a free parameter. |
| Total dust mass with inner-profile extrapolation, fixed p=3.5 | 210-310 | not stated | M_earth | 11 | The range of dust masses decreases to $210-310~M_{\oplus}$ if $p$ is fixed to 3.5. |
| Global gas-to-dust mass ratio, free-p mass estimate | 50-70 | not stated | dimensionless | 11 | Our estimated dust masses for the model with a varying $p$ would thus translate into global gas-to-dust mass ratios of $50-70$ |
| Survey-style dust mass from 0.87 mm | 54 | ±5 | M_earth | 11 | a dust mass of $54\pm5~M_{\oplus}$ would be obtained from our 0.87 mm flux of $1540\pm150$ mJy. |
| Survey-style dust mass from 1.3 mm | 57 | ±6 | M_earth | 11 | A similar dust mass of $57\pm6~M_{\oplus}$ would be obtained from our 1.3 mm flux of $575\pm30$ mJy. |
| Multiwavelength total dust mass relative to survey-style estimates | 4.5-5.9 | not stated | dimensionless | 11 | These masses are between a factor of 4.5 and 5.9 lower than the total dust mass estimated with our multiwavelength analysis. |

## Qualitative findings

- Most previously known annular substructures are resolved at all four wavelengths.  
  > "Most previously known annular substructures in the disk of TW Hya are resolved at the four wavelengths." (abstract)
- Rings accumulate large dust particles and work as dust traps.  
  > "At $r>20$ au, we find evidence of the accumulation of large dust particles at the position of the bright rings, indicating that these are working as dust traps." (abstract)
- Inner-disk optical depth and settling prevent accurate dust-density and grain-size estimates.  
  > "Coupled with the effects of dust settling, this prevents the derivation of accurate density and grain size estimates in these regions." (abstract)
- Temperature posteriors are mostly set by the prior.  
  > "On the other hand, no clear trends are seen in the temperature profile, with its posterior being set mostly by the prior." (Modeling results)
- Snowlines are unlikely to drive most ring substructures.  
  > "Therefore, we conclude that snowlines are unlikely to be the driving mechanism of most ring substructures in TW Hya" (Insights on the origin of disk substructures)

## Claim tuples

- H: The central millimeter source contains free-free emission from an ionized jet. | E: Measure central aperture fluxes, spectral-index maps, and long-wavelength extrapolations. | R: Central 2.1–3.1 mm spectral index 0.72±0.18; emission remains positive-slope at 3.1 mm. | F: Free-free emission is significant; an ionized jet retaining an optically thick component is favored. | **partially**
- H: The continuum requires millimeter-sized or larger dust rather than only small grains. | E: Fit four-wavelength slab models and compare small/large-grain solution families with physical constraints. | R: Small-grain solutions demand unrealistically high surface densities and low temperatures; a_max>1 mm is favored. | F: Maximum grain size in TW Hya exceeds 1 mm. | **supported**
- H: The inner disk can be characterized by the same thin, vertically isothermal slab model as the outer disk. | E: Fit radial intensities independently and compare optical depths and spectral indices across wavelengths. | R: The model fails inside ~20 au, where spectral indices are below 2 and optical depths are high. | F: High optical depth combined with settling likely causes wavelength-dependent emitting heights and unreliable inner-disk dust estimates. | **refuted**
- H: Bright rings trap large particles and provide sites favorable for planetesimal formation. | E: Compare fixed-p and free-p radial dust distributions across rings and gaps. | R: Rings have higher dust densities and higher abundances of large particles; free-p fits yield flatter slopes at rings. | F: Rings are dust traps and promising locations for streaming instability; planetesimal formation is inferred rather than directly measured. | **partially**
- H: Gap contrasts and disk morphology distinguish the origin of D25 and D41. | E: Estimate dust-density contrast lower limits and compare snowline, zonal-flow, dead-zone, and planet-disk explanations. | R: Dust-density contrasts are at least ~2, and the disk is highly axisymmetric. | F: Planet-disk interactions are the most likely origin of D25 and D41, with remaining MHD uncertainties. | **partially**
- H: Standard survey assumptions underestimate TW Hya's dust mass. | E: Integrate modeled surface density with an inner power-law extrapolation and compare with standard single-temperature, optically thin estimates. | R: Total dust mass 250–330 M_earth, 4.5–5.9 times the survey-style estimate. | F: Optical depth and dust-property variations cause substantial mass underestimation; the total mass remains conditional on the inner extrapolation. | **partially**

## Reasoning

- Why this data: High-resolution 3.1 mm data probe lower optical depth than previous observations; four wavelengths constrain dust properties.  
  > "These data represent the longest wavelength at which high sensitivity and high spatial resolution observations have been obtained for TW Hya, providing a detailed view of the disk substructures at a lower optical depth than previous ALMA observations." (Introduction)
- Why this method: Multiple wavelengths distinguish grain-size effects from optical-depth effects; free p propagates size-distribution uncertainty.  
  > "In order to resolve this dichotomy and better characterize the dust content in disk substructures, a detailed analysis of observations at multiple wavelengths is required." (Introduction); "Including $p$ as a free parameter allows us to account for the uncertainties on this parameter in the estimates of dust density and maximum grain size." (The dust content at $r>20$ au and its impact on planet formation)
- Alternative: Small-grain solutions a_max=10–50 micrometers reproduce intensities but are disfavored by density, stability, and temperature requirements.  
  > "Overall, the physical conditions predicted with $a_{max}=10-50~\mu$m appear to be physically unrealistic" (Modeling results)
- Alternative: Fixing temperature to the passive-disk relation was considered; a temperature prior was used to propagate its uncertainty.  
  > "an alternative approach could be to fix the temperature at each radius to the value predicted by this equation (cite: lon20)" (Dust characterization); "letting the temperature be a free parameter in the model allows us to introduce the inherent uncertainty" (Dust characterization)
- Alternative: Photoionized-wind or flat-spectrum free-free emission considered; positive spectral slopes favor a partially optically thick jet.  
  > "the free-free emission from a photoionized wind is expected to be optically thin at millimeter and centimeter wavelengths, hence presenting a flat spectral index too (cite: pas12)." (Free-free emission inside the 3 au cavity); "our observations appear to indicate that the spectral index of the central component remains positive at least up to 3.1 mm" (Free-free emission inside the 3 au cavity)
- Alternative: A sudden fragmentation change near 20 au is possible, but high optical depth is preferred.  
  > "the dust grains might experience a sudden and significant increase in fragmentation efficiency at $r\sim20$ au" (The optically thick inner disk ($r<20$ au)); "Overall, we conclude that the high optical depth scenario is a more likely explanation of our results at $r<20$ au." (The optically thick inner disk ($r<20$ au))
- Alternative: Dust sintering and snowlines are disfavored as the origin of most outer rings.  
  > "we can at least discard effects that result in the formation of rings of smaller particles, such as the process dubbed as dust sintering (cite: oku16)." (Insights on the origin of disk substructures); "Therefore, we conclude that snowlines are unlikely to be the driving mechanism of most ring substructures in TW Hya" (Insights on the origin of disk substructures)
- Alternative: Full radiative-transfer modeling could tighten temperature constraints but would limit explored parameter space through computational cost.  
  > "These could be placed by using a more complete radiative transfer modeling that considers the irradiation of the disk by the central star." (The dust content at $r>20$ au and its impact on planet formation); "However, this analysis would require a significant computational effort that would probably limit the parameter space explored by the model." (The dust content at $r>20$ au and its impact on planet formation)
- How they decided it was enough: Self-calibration stopped when peak S/N stopped improving or solution intervals reached the integration time.  
  > "until no improvement was seen in the peak signal-to-noise ratio (S/N) or until reaching the integration time of the data." (Observations)
- Limitation (authors): Central-source aperture fluxes may contain emission from the ring at 3 au.  
  > "our flux estimates might include some dust contribution from the ring at 3 au." (Free-free emission inside the 3 au cavity)
- Limitation (authors): Low inclination prevents resolving jet elongation.  
  > "the low inclination of TW Hya makes it unfeasible to resolve any elongation in our data." (Free-free emission inside the 3 au cavity)
- Limitation (authors): Independent radius fitting without model convolution permits beam dilution, especially in narrow gaps.  
  > "We note that we do not convolve the model, since each radius is fitted independently." (Dust characterization); "Therefore, beam dilution might affect our results, particularly at the position of the gaps." (Modeling results)
- Limitation (authors): Free-p models cannot tightly constrain a_max over 0.1–100 cm.  
  > "once the slope of the particle size distribution is allowed to vary, the model is unable to constrain $a_{max}$ within the $0.1-100$ cm range." (Modeling results)
- Limitation (authors): Temperature posterior is largely prior-driven.  
  > "no clear trends are seen in the temperature profile, with its posterior being set mostly by the prior." (Modeling results)
- Limitation (authors): Inner-disk optical depths are highly uncertain because of poor fits.  
  > "We note that the values of the optical depth at $r\lesssim19$ au are highly uncertain due to the poor quality of our fit in these regions." (The optically thick inner disk ($r<20$ au))
- Limitation (authors): Small inferred inner-disk grains cannot be firmly ruled out.  
  > "we cannot firmly conclude that the estimated $a_{max}$ values of $\sim300~\mu$m at $r<20$ au are wrong." (The optically thick inner disk ($r<20$ au))
- Limitation (authors): Total dust mass is not robust because inner-disk surface density is extrapolated.  
  > "our results at $r<20$ au are likely incorrect, which prevents us from obtaining a robust total disk mass." (On the total dust mass of TW Hya)
- Limitation (authors): Dust-density contrast cannot be reliably translated into gas-pressure perturbation amplitude.  
  > "It is unclear how to translate from a contrast in dust surface density to the amplitude of the underlying gas density perturbation" (Insights on the origin of disk substructures)
- Caveat (inferred, ours): Treat total dust masses as conditional extrapolations, rather than direct measurements of the optically thick inner disk.
- Caveat (inferred, ours): Assess sensitivity of grain-size and mass posteriors to adopted dust composition and temperature priors.
- Caveat (inferred, ours): A flux-calibration offset is shared across radii; treating it only as a per-radius error may omit correlations important for integrated masses.
- Caveat (inferred, ours): Clarify the inconsistent large-grain upper bounds: the initial grid reaches 100 cm, while the posterior split states 10 cm.
- Caveat (inferred, ours): Check the stated grid counts against bounds and increments before implementing them.
- Caveat (inferred, ours): The small-grain discussion associates gravitational instability with Q>1, contrary to its own Q=1 threshold discussion; resolve this textual inconsistency.
- Caveat (inferred, ours): Direct evidence for gas pressure bumps, streaming instability, or planets is not supplied by continuum fitting alone.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Reduction, imaging, opacity-generation, and posterior-analysis scripts or released products.
- Missing: Exact execution/SPW manifest, especially the unexplained 2016.1.01158.S acknowledgement.
- Missing: Per-execution flagging, astrometric corrections, flux-rescaling factors, and self-calibration settings.
- Missing: Complete cleaning commands and common-beam imaging parameters.
- Missing: Radial extraction bins, integration boundaries, and uncertainty-propagation implementation.
- Missing: Resolved grid/prior conventions and the 10 cm versus 100 cm upper-bound discrepancy.
- Missing: Explicit public availability of the complete input dataset.
- Data volume (inferred): Not reliably estimable: multiple executions in four bands, without visibility counts or dataset sizes.
- Score (inferred): 6/5, On a 0–10 scale: detailed data provenance, imaging strategy, equations, grids, and numeric results; exact calibration, imaging, opacity, prior, and integration implementations remain incomplete.
- Rediscovery candidate: no, Main results are numeric and archival reuse is explicit, but complete public availability is not stated and exact reduction/modeling choices are missing.

## Links

- Method: (cite: mcm07) (CASA software reference.)
- Method: (cite: rau11) (mtmfs deconvolution.)
- Method: (cite: and18a) (Relative visibility-based flux rescaling.)
- Method: (cite: sie19; car19) (Isothermal slab emission with scattering.)
- Method: (cite: car19) (Effective anisotropic-scattering approximation.)
- Method: (cite: bir18) (DSHARP dust composition and dsharp_opac.)
- Method: (cite: mac19) (Free particle-size-distribution slope.)
- Method: (cite: chi97; dul01) (Passive flared-disk temperature prior.)
- Method: (cite: hua18b) (Annular-feature naming and flaring-angle range.)
- Method: (cite: and05) (Standard opacity and temperature for survey-style dust masses.)
- Method: (cite: sie20) (Interpretation of settling and optical-depth biases.)
- Related: DSHARP

## Checks

```json
{
 "quotes": 284,
 "quotes_ok": 284,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 10,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 22,
 "numeric_problems": 0,
 "fill": {
  "facts": 173,
  "stated": 153,
  "rate": 0.884
 },
 "evidence_ok": true
}
```
