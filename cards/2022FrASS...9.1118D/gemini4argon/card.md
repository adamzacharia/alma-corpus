# A Genetic Algorithm to Model Solar Radio Active Regions From 3D Magnetic Field Extrapolations

`2022FrASS...9.1118D` | Frontiers in Astronomy and Space Sciences 2022 | first author: de Oliveira e Silva, Alexandre José | arXiv: 2205.03385 | DOI: 10.3389/fspas.2022.911118

Card schema 1.0 | model gemini-4-argon | depth full | type archival_reuse

## Science

- Fields: sun
- Question: Determine the plasma temperature and electron density height profiles in the solar atmosphere of active region NOAA 12470 to reproduce observed radio brightness temperature maps at 17, 100, and 230 GHz.  
  > "In order to determine the best plasma temperature and density height profiles necessary to match the observations, the model uses a genetic algorithm that modifies a standard quiet Sun atmospheric model." (Abstract); "The purpose of this study is to estimate the temperature and electron density as a function of height in the solar atmosphere, as constrained by brightness temperature $T_\mathrm{b}$ maps of radio observations." (Atmospheric modelling via genetic algorithm)
- Target **AR NOAA 12470**: coordinates 17.40°N, 17.68°E (heliographic)  
  > "In this work, we selected the active region AR NOAA 12470 to test our algorithm." (Observations); "Due to the heliographic position of AR 12740 (17.40$^\circ$N, 17.68$^\circ$E), it is estimated that $|\vec{B}|$ is 7.5% greater than the observed $B_z$." (Gyroresonance contribution); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00020.SV
- bands: Band 3 (84–116 GHz), Band 6 (211–275 GHz)  
  > "The maps were obtained by the fast-scan single-dish method described in (cite: White2017), at Band 3 (84–116 GHz) and Band 6 (211–275 GHz)." (Radio maps)
- frequencies and spectral setup: 100 GHz (Band 3 reference) and 230 GHz (Band 6 reference)  
  > "Following (cite: Selhorst2019), we took 100 and 230 GHz as the reference frequencies for Bands 3 and 6, respectively." (Radio maps)
- continuum bandwidth: _not stated_
- arrays: 12m diameter antenna (fast-scan single-dish)  
  > "The maps were obtained by the fast-scan single-dish method described in (cite: White2017), at Band 3 (84–116 GHz) and Band 6 (211–275 GHz)." (Radio maps); "The maps were made from observations of a 12m diameter antenna, resulting in nominal spatial resolutions of 25” and 58” at 230 and 100 GHz, respectively." (Radio maps)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 25" at 230 GHz, 58" at 100 GHz  
  > "The maps were made from observations of a 12m diameter antenna, resulting in nominal spatial resolutions of 25” and 58” at 230 and 100 GHz, respectively." (Radio maps)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2015 December 17 (14:52 UT at 230 GHz, 19:35 UT at 100 GHz), within Science Verification period 2015 December 16–20  
  > "The ALMA maps used here were obtained during the Science Verification period, 2015 December 16–20 [^2]." (Radio maps); "The nominal time of the 230 GHz map is 14:52 UT, i.e., only 1 minute difference from the nominal time of the HMI observation, requiring just $-0.01^\circ$ of longitudinal rotation." (Radio maps); "The nominal time of the 100 GHz map was 19:35 UT, requiring a longitudinal rotation of $-2.85^\circ$." (Radio maps)
- pi or archival as stated: Science Verification archival data  
  > "The ALMA maps used here were obtained during the Science Verification period, 2015 December 16–20 [^2]." (Radio maps); "This paper makes use of the following ALMA data: ADS/JAO. ALMA#2011.0.00020.SV." (Acknowledgments)
- Other facility **Nobeyama Radioheliograph (NoRH)**: 17 GHz radio map observed on 2015 December 17 at 02:44 UT (512x512 pixels, 4.91" pixel resolution, 10-18" spatial resolution)  
  > "The observations at 17 GHz were made by the Nobeyama Radioheliograph (NoRH), while the observations at 100 and 230 GHz were obtained by the Atacama Large Millimeter/submillimeter Array (ALMA)." (Abstract); "We used a 17 GHz map observed at 02:44 UT and available in $512\times512$ pixels$^2$ format (4.91” resolution), rotated longitudinally by $7.31^\circ$ with respect to the HMI magnetogram." (Radio maps)
- Other facility **Helioseismic and Magnetic Imager (HMI) on Solar Dynamics Observatory (SDO)**: Photospheric line-of-sight (LOS) magnetogram at 6173 Å (Fe I) obtained on December 17, 2015 at 14:51 UT (4096x4096 pixels, ~0.5 arcsec resolution)  
  > "HMI operates at wavelengths around 6173 Å(Fe I) and provides LOS magnetograms of $4096\times4096$ pixels with $\sim0.5$ arcsec spatial resolution." (Observations); "Figure [1](#fig:magneto) (left panel) shows the HMI line of sight (LOS) magnetogram obtained on December 17, 2015 at 14:51 UT." (Magnetogram)
- External data: Quiet Sun brightness temperatures at 230 GHz (6210 ± 110 K) and 100 GHz (7110 ± 90 K)  
  > "While the quiet Sun brightness temperature ( $T_\mathrm{b,QS}$) at 230 GHz is $6210\pm110$ K (cite: Selhorst2019), the AR 12470 brightness temperature ($T_\mathrm{b}$) varies from 5800 to 6600 K" (Radio maps); "At 100 GHz, $T_{qS}=7110\pm90$ K (cite: Selhorst2019) and AR 12470 showed $T_\mathrm{b}$ varying from 7200 to 7650 K where $|\vec{B}|>1500$ G." (Radio maps) [from Selhorst et al. (2019) (cite: Selhorst2019)]
- External data: Initial 1D quiet Sun atmospheric seed model (SSC)  
  > "The atmospheric model developed by (cite: Selhorst2005b) is used as the seed in the genetic algorithm, that changes the seed model to find the best fit for the observational measurements." (Genetic Algorithm Features) [from Selhorst et al. (2005b) (cite: Selhorst2005b)]
- External data: Minimum magnetic field intensity of 1500 G to form a sunspot  
  > "The $|\vec{B}|$ limits used to classify each pixel are based on studies by (cite: Livingston2012), who derived a minimum necessary value of 1500 G for sunspot formation." (Results) [from Livingston et al. (2012) (cite: Livingston2012)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Science Verification fast-scan single-dish maps used directly and resized to match HMI magnetogram  
  > "The ALMA maps used here were obtained during the Science Verification period, 2015 December 16–20 [^2]." (Radio maps); "Thus for a better comparison with the model results they were resized to match the HMI magnetogram ($4096\times4096$ pixels$^2$)." (Radio maps)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 3" pixel at 230 GHz, 6" pixel at 100 GHz (ALMA native maps); resized to 256x256 pixels (~2" per pixel) for modeling  
  > "Moreover, the ALMA maps come in distinct sizes, $800\times800$ pixels$^2$ (3” pixel) at 230 GHz and $400\times400$ pixels$^2$ (6” pixel) at 100 GHz." (Radio maps); "To speed up the computational process, the datacubes and images were resized from $1024\times1024$ pixels$^2$ to $256\times256$ pixels$^2$, corresponding to a spatial resolution $\sim2''$ per pixel." (Results)
- image size: 800x800 pixels at 230 GHz, 400x400 pixels at 100 GHz; resized to 4096x4096 pixels to match HMI, and active region cropped and resized from 1024x1024 to 256x256 pixels  
  > "Moreover, the ALMA maps come in distinct sizes, $800\times800$ pixels$^2$ (3” pixel) at 230 GHz and $400\times400$ pixels$^2$ (6” pixel) at 100 GHz." (Radio maps); "Thus for a better comparison with the model results they were resized to match the HMI magnetogram ($4096\times4096$ pixels$^2$)." (Radio maps); "To speed up the computational process, the datacubes and images were resized from $1024\times1024$ pixels$^2$ to $256\times256$ pixels$^2$, corresponding to a spatial resolution $\sim2''$ per pixel." (Results)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Model results convolved with 2D Gaussian beam matching single-dish resolutions (25" at 230 GHz, 58" at 100 GHz, 10" at 17 GHz)  
  > "To compare the simulations with the observations, the model results were convolved with a 2D Gaussian beam that matches the resolution of the ALMA single-dish observations, i.e., 25” and 58” at 230 and 100 GHz, respectively." (Comparison of the synthetic and observed radio images); "If only free-free emission is considered, at 17 GHz the umbra appears darker in the model than the surrounding area, with a brightness temperature of $1.06\pm0.02\times T_{qS}$ at 10” resolution." (Comparison of the synthetic and observed radio images)
- final beam: 25" at 230 GHz and 58" at 100 GHz  
  > "The maps were made from observations of a 12m diameter antenna, resulting in nominal spatial resolutions of 25” and 58” at 230 and 100 GHz, respectively." (Radio maps)
- final rms: _not stated_

### Inherited from earlier work

- Fast-scan single-dish mapping method for ALMA solar observations  
  > "The maps were obtained by the fast-scan single-dish method described in (cite: White2017), at Band 3 (84–116 GHz) and Band 6 (211–275 GHz)." (Radio maps) [from White et al. (2017) (cite: White2017)]
- Reference frequencies of 100 and 230 GHz for ALMA Bands 3 and 6  
  > "Following (cite: Selhorst2019), we took 100 and 230 GHz as the reference frequencies for Bands 3 and 6, respectively." (Radio maps) [from Selhorst et al. (2019) (cite: Selhorst2019)]
- Seed quiet Sun atmospheric model (SSC)  
  > "The atmospheric model developed by (cite: Selhorst2005b) is used as the seed in the genetic algorithm, that changes the seed model to find the best fit for the observational measurements." (Genetic Algorithm Features) [from Selhorst et al. (2005b) (cite: Selhorst2005b)]
- Five free parameter definitions for modifying the AR atmospheric model  
  > "Five free parameters are supplied to the GA representing the atmospheric model. These parameters are based on the ideas presented in (cite: Selhorst2008), as follows:" (Genetic Algorithm Features) [from Selhorst et al. (2008) (cite: Selhorst2008)]
- Pikaia genetic algorithm optimization scheme  
  > "In order to determine the best plasma temperature and density height profiles necessary to match the observations, we employ the genetic algorithm Pikaia (cite: Charbonneau1995)." (Genetic Algorithm Features) [from Charbonneau (1995) (cite: Charbonneau1995)]
- Linear force-free magnetic field extrapolation algorithm in IDL  
  > "The extrapolation routine is based on the works of (cite: Nakagawa1972) and (cite: Seehafer1978) and was previously implemented in IDL by J. E. R. Costa and T. S. N. Pinto (cite: Selhorst2005d; Selhorst2008; Nita2018)." (Magnetic field extrapolation) [from Nakagawa & Raadu (1972) (cite: Nakagawa1972); Seehafer (1978) (cite: Seehafer1978); Selhorst et al. (2005a, 2008) (cite: Selhorst2005d; Selhorst2008); Nita et al. (2018) (cite: Nita2018)]
- Effective ion charge Z = 1.178 and radiative transfer formulation  
  > "Following (cite: Zirin1988), it was assumed $Z=1.178$, if a fully hydrogen atmosphere was considered, i.e. $Z=1$, the resulting $T_\mathrm{b}$ should be only $\sim 3\%$ smaller for all frequencies simulated here." (Emission mechanisms); "Following (cite: Zirin1988), radiative transfer yields the brightness temperature as a function of wavelength as:" (Emission mechanisms) [from Zirin (1988) (cite: Zirin1988)]
- Normalization of contribution functions by their maximum  
  > "Following (cite: Tapia2020), each CF shown in Figure [4](#fig:temp_dens) was normalized by its maximum, for a better comparison of the formation height of the emission at each frequency." (Free-free contribution) [from Tapia-Vázquez & De la Luz (2020) (cite: Tapia2020)]

### Not stated but needed to reproduce (our reading)

- Prior bounds (minimum and maximum values) chosen for each of the five GA free parameters (chromospheric temperature gradient, chromospheric electron density gradient, coronal temperature factor, coronal electron density factor, and TR position shift)
- Exact functional mathematical equations for how the five GA free parameters modify the SSC temperature and density height profiles
- Details of the initial seed parameters used for each distinct AR class (umbrae, penumbrae, plages) to speed up the GA
- Exact formulation of the chi-squared objective function (including observational uncertainty weights for the three frequencies and whether beam convolution is applied before or after pixel-by-pixel chi-squared evaluation)
- Which magneto-ionic mode (o-mode, x-mode, or average of both) was used in the radiative transfer integration to compare with total intensity maps

## Analysis recipe

1. **Prepare, deproject, and co-align magnetogram and radio maps**: Rotate AR in HMI LOS magnetogram to solar disk center, remove solar spherical curvature, correct magnetic field intensities for projection effects, longitudinally rotate radio maps to match magnetogram time, resize radio maps to match magnetogram grid (4096x4096), and crop/resize selected active region area from 1024x1024 to 256x256 pixels (~2"/pixel).  
  > "To correct for this, the AR has been rotated to solar disk center, solar spherical curvature has been removed, and the magnetic field intensities have been corrected for projection." (Magnetogram); "The nominal time of the 230 GHz map is 14:52 UT, i.e., only 1 minute difference from the nominal time of the HMI observation, requiring just $-0.01^\circ$ of longitudinal rotation. The nominal time of the 100 GHz map was 19:35 UT, requiring a longitudinal rotation of $-2.85^\circ$." (Radio maps); "To speed up the computational process, the datacubes and images were resized from $1024\times1024$ pixels$^2$ to $256\times256$ pixels$^2$, corresponding to a spatial resolution $\sim2''$ per pixel." (Results)
   - software: IDL
   - parameter: Longitudinal rotation: -0.01 deg (230 GHz), -2.85 deg (100 GHz), 7.31 deg (17 GHz)  
  > "The nominal time of the 230 GHz map is 14:52 UT, i.e., only 1 minute difference from the nominal time of the HMI observation, requiring just $-0.01^\circ$ of longitudinal rotation. The nominal time of the 100 GHz map was 19:35 UT, requiring a longitudinal rotation of $-2.85^\circ$." (Radio maps); "We used a 17 GHz map observed at 02:44 UT and available in $512\times512$ pixels$^2$ format (4.91” resolution), rotated longitudinally by $7.31^\circ$ with respect to the HMI magnetogram." (Radio maps)
   - parameter: Grid size: 256x256 pixels (~2" per pixel)  
  > "To speed up the computational process, the datacubes and images were resized from $1024\times1024$ pixels$^2$ to $256\times256$ pixels$^2$, corresponding to a spatial resolution $\sim2''$ per pixel." (Results)
   - assumption: |B| is 7.5% greater than observed B_z due to heliographic position (17.40°N, 17.68°E)  
  > "Due to the heliographic position of AR 12740 (17.40$^\circ$N, 17.68$^\circ$E), it is estimated that $|\vec{B}|$ is 7.5% greater than the observed $B_z$." (Gyroresonance contribution)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extrapolate 3D coronal and chromospheric magnetic field from photospheric magnetogram**: Perform linear force-free field (LFF) extrapolation above the photosphere starting from the line-of-sight magnetic field component to generate 3D cubes of Bx, By, Bz and field line positions, and interpolate voxel height resolution to 50 km.  
  > "Photospheric magnetograms are used as the boundary condition for an extrapolation of the field above the photosphere using the linear force-free field approximation." (Magnetic field extrapolation); "The result is three cubes of intensities, one for each component of the magnetic field vector ($B_x$, $B_y$, and $B_z$) and another data cube for the positions of the magnetic field lines." (Magnetic field extrapolation); "However, the radiative transfer calculations require better resolution in the height of the voxels ($h_z$) due to the relatively narrow width of the chromosphere, and they were re-scaled via interpolation from the resolution of the magnetogram to 50 km, similar to the resolution of the SSC model." (Results)
   - software: IDL
   - parameter: Force-free parameter alpha = -0.005  
  > "A low value for the $\alpha$ parameter in (1) does not significantly affect the extrapolated magnetic field configuration at low heights in the atmosphere: here $\alpha=-0.005$ was chosen for the LFF extrapolation since it generated a greater number of closed magnetic field lines in the selected region than did the potential-field extrapolation ($\alpha=0$)." (Results)
   - parameter: Minimum photospheric magnetic field |B|_min = 200 G  
  > "In this work, the extrapolated field lines were calculated only above positions with $|\vec{B}|_{min}=200$ G at the photosphere." (Magnetic field extrapolation)
   - parameter: Vertical voxel height resolution h_z = 50 km  
  > "However, the radiative transfer calculations require better resolution in the height of the voxels ($h_z$) due to the relatively narrow width of the chromosphere, and they were re-scaled via interpolation from the resolution of the magnetogram to 50 km, similar to the resolution of the SSC model." (Results)
   - assumption: Linear force-free field approximation (current density parallel to magnetic field at any point in space)  
  > "The fundamental equation that describes a force-free field (assuming that the current density is parallel to the magnetic field at any point in space) is" (Magnetic field extrapolation)
   - fitting: _not stated_
   - validation: Checked that |B|_min = 200 G avoided simulated ARs appearing much larger than observed ARs, and compared extrapolated field lines against SDO/AIA 193 Å image.  
  > "A different minimum value could be chosen by the user, but we found that the inclusion of magnetic fields below this limit resulted in the simulated ARs appearing much larger than the observed ARs." (Magnetic field extrapolation); "Figure [3](#fig:AIA) shows some of the magnetic field lines obtained in the extrapolation with $\alpha=-0.005$ and $|\vec{B}|_{min}=200$ G." (Results)
3. **Classify pixels by photospheric magnetic field strength**: Classify each pixel in the magnetogram into four classes based on photospheric magnetic field intensity |B|_0: umbra, penumbra, plage, and quiet Sun.  
  > "The resulting atmospheric profiles were grouped into four different classes corresponding to different atmospheric features: umbrae, penumbrae, plage and quiet Sun." (Results); "Each pixel in the magnetogram was classified as umbra, penumbra, or plage according to its intensity ($|\vec{B}|$), as follows: umbra, $|\vec{B}|\geq1500$ G ($\sim200$ pixels); penumbra, $1000\leq |\vec{B}_0|<1500$ G ($\sim$230 pixels); plages, $200\leq|\vec{B}_0|<1000$ G ($\sim$27200 pixels). All pixels with $|\vec{B}|\leq200$ G were classified as quiet Sun ($\sim$38000 pixels) and were assumed to have $T_B=T_{qS}$." (Results)
   - parameter: Umbra: |B| >= 1500 G (~200 pixels); Penumbra: 1000 <= |B_0| < 1500 G (~230 pixels); Plages: 200 <= |B_0| < 1000 G (~27200 pixels); Quiet Sun: |B| <= 200 G (~38000 pixels)  
  > "Each pixel in the magnetogram was classified as umbra, penumbra, or plage according to its intensity ($|\vec{B}|$), as follows: umbra, $|\vec{B}|\geq1500$ G ($\sim200$ pixels); penumbra, $1000\leq |\vec{B}_0|<1500$ G ($\sim$230 pixels); plages, $200\leq|\vec{B}_0|<1000$ G ($\sim$27200 pixels). All pixels with $|\vec{B}|\leq200$ G were classified as quiet Sun ($\sim$38000 pixels) and were assumed to have $T_B=T_{qS}$." (Results)
   - assumption: Pixels with |B| <= 200 G have quiet Sun brightness temperature T_B = T_qS  
  > "All pixels with $|\vec{B}|\leq200$ G were classified as quiet Sun ($\sim$38000 pixels) and were assumed to have $T_B=T_{qS}$." (Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit 1D atmospheric temperature and density profiles per pixel via genetic algorithm and radiative transfer**: Run Pikaia genetic algorithm independently for each vertical column (pixel) to modify the seed SSC quiet Sun model via 5 free parameters, compute thermal bremsstrahlung and gyroresonance absorption coefficients and 1D radiative transfer to obtain T_b at 17, 100, and 230 GHz, minimize chi-squared against observations, and average best-fit profiles per class.  
  > "An initial 1D atmospheric model is used as a seed for the GA: at each step, $T_\mathrm{b}$ is obtained via the calculation of radiative transfer incorporating opacity from both the thermal bremsstrahlung and gyroresonance emission mechanisms." (Atmospheric modelling via genetic algorithm); "The GA iteratively updates the atmospheric plasma trapped by magnetic field lines until a best model is found via $\chi^2$ minimization of the calculated and observed $T_\mathrm{b}$ values." (Atmospheric modelling via genetic algorithm); "We then obtained the average electron density and temperature profiles for each of the three AR classes by calculating the average of the profiles with the lowest $\chi^2$ values in the $T_\mathrm{b}$ calculation, in relation to the observed values at the three distinct observing frequencies." (Results)
   - software: Pikaia
   - parameter: 5 free parameters: chromospheric temperature gradient, chromospheric electron density gradient, coronal temperature factor N_T, coronal electron density factor N_n_e, and TR position shift Delta h  
  > "Five free parameters are supplied to the GA representing the atmospheric model." (Genetic Algorithm Features)
   - parameter: GA settings: full-generation replacement, 10 generations, 100 children per generation, crossover probability = 0.85, variable mutation mode, initial mutation rate = 0.005, mutation rate range = 0.0005 to 0.25  
  > "The method used here was full-generation replacement using ten generations with one hundred children each. The crossover probability was 0.85 and the mutation mode was variable. The initial mutation rate, that is, the initial probability that any gene locus will mutate in any generation, was 0.005. Finally, the mutation rate range was between 0.0005 and 0.25." (Genetic Algorithm Features)
   - parameter: Gyroresonance harmonics s <= 5 with 10% uncertainty in |B| (3rd harmonic at 2000±200 G, 4th at 1500±150 G, 5th at 1200±120 G)  
  > "Since the contribution of higher harmonics to the radio emission is very small (cite: Shibasaki1994), the gyroresonance emission was only calculated for harmonics smaller than 5 ($s\leq 5$)." (Emission mechanisms); "To investigate the gyroresonance contribution, $\kappa_g$ was calculated for harmonics $s\leq 5$, allowing for an uncertainty of $10\%$ in the $|\vec{B}|$ values." (Gyroresonance contribution)
   - assumption: Effective ion charge Z = 1.178, only electron-proton collisions considered, densities grouped as (n_e * n_i)^(1/2), plasma fully ionized above 1000 km in SSC model  
  > "Only the contributions of collisions with protons was considered, since its density is much larger than that of other ion species ($n_i$)." (Emission mechanisms); "Following (cite: Zirin1988), it was assumed $Z=1.178$, if a fully hydrogen atmosphere was considered, i.e. $Z=1$, the resulting $T_\mathrm{b}$ should be only $\sim 3\%$ smaller for all frequencies simulated here." (Emission mechanisms); "Although, the SSC model considers the plasma fully ionized above 1000 km, i.e. $n_e=n_i$, to simplify the GA the densities were grouped in a single variable, that is $(n_e\times n_i)^{1/2}$." (Free-free contribution)
   - fitting: Pikaia genetic algorithm with chi-squared minimization; full-generation replacement over 10 generations with 100 children each; stabilizes by ~7th generation.  
  > "A generation of child atmospheric models is created by the algorithm based on the parent models with the lowest $\chi^2$ values, using the genetic algorithm described in (cite: Charbonneau1995)." (Genetic Algorithm Features); "In our runs the $\chi^2$ measure typically stabilizes to a minimum value by about the seventh generation." (Genetic Algorithm Features)
   - validation: Monitored stabilization of chi-squared across generations and evaluated optical depth and contribution functions across atmospheric layers.  
  > "In our runs the $\chi^2$ measure typically stabilizes to a minimum value by about the seventh generation." (Genetic Algorithm Features); "In Figure [5](#fig:tau_cf) we show, for each atmospheric class, the optical depth ($\tau$, top row) and the contribution function (CF, bottom row), that represents the emission variation with the atmosphere height." (Free-free contribution)
5. **Convolve synthetic radio maps with instrumental beams and compare with observations**: Convolve the 2" resolution GA model brightness temperature maps with 2D Gaussian beams matching observational resolutions (25" at 230 GHz, 58" at 100 GHz, 10" at 17 GHz) and compare average brightness temperatures across umbra, penumbra, plages, and polarized/non-polarized regions.  
  > "To compare the simulations with the observations, the model results were convolved with a 2D Gaussian beam that matches the resolution of the ALMA single-dish observations, i.e., 25” and 58” at 230 and 100 GHz, respectively." (Comparison of the synthetic and observed radio images); "As summarized in Table [1](#Table:TB17_pol), when gyroresonance is taken into account the $T_\mathrm{b}$ values obtained for the highly polarized region are in agreement with those observed." (Comparison of the synthetic and observed radio images)
   - parameter: 2D Gaussian beam FWHM: 25" (230 GHz), 58" (100 GHz), 10" (17 GHz)  
  > "To compare the simulations with the observations, the model results were convolved with a 2D Gaussian beam that matches the resolution of the ALMA single-dish observations, i.e., 25” and 58” at 230 and 100 GHz, respectively." (Comparison of the synthetic and observed radio images); "If only free-free emission is considered, at 17 GHz the umbra appears darker in the model than the surrounding area, with a brightness temperature of $1.06\pm0.02\times T_{qS}$ at 10” resolution." (Comparison of the synthetic and observed radio images)
   - fitting: _not stated_
   - validation: Compared synthetic vs. observed average T_b values (normalized to T_qS) within uncertainties across AR regions in Tables.  
  > "All the simulated areas are consistent with the observations to within the uncertainties." (Comparison of the synthetic and observed radio images)

## Software

- **Pikaia** : Genetic algorithm optimization to determine best-fit plasma temperature and electron density height profiles  
  > "In order to determine the best plasma temperature and density height profiles necessary to match the observations, we employ the genetic algorithm Pikaia (cite: Charbonneau1995)." (Genetic Algorithm Features)
- **IDL** : Linear force-free 3D magnetic field extrapolation routine  
  > "The extrapolation routine is based on the works of (cite: Nakagawa1972) and (cite: Seehafer1978) and was previously implemented in IDL by J. E. R. Costa and T. S. N. Pinto (cite: Selhorst2005d; Selhorst2008; Nita2018)." (Magnetic field extrapolation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Transition region (TR) height for umbrae | 1080 | 20 | km | 4 | for umbrae the TR is located at $1080\pm20$ km above the solar surface;; In the Table [\[Table_TR\]](#Table_TR) we present the average height of the transition region (TR), which is one of the five free parameters fitted in the GA process, for each atmospheric class: thus, 1080$\pm$20 km above the solar surface for umbrae, 1800$\pm$50 km for penumbrae, and 2000$\pm$100 km for plages. |
| Transition region (TR) height for penumbrae | 1800 | 50 | km | 4 | for penumbrae, the TR is located at $1800\pm50$ km;; In the Table [\[Table_TR\]](#Table_TR) we present the average height of the transition region (TR), which is one of the five free parameters fitted in the GA process, for each atmospheric class: thus, 1080$\pm$20 km above the solar surface for umbrae, 1800$\pm$50 km for penumbrae, and 2000$\pm$100 km for plages. |
| Transition region (TR) height for plages (bright regions outside sunspots) | 2000 | 100 | km | 4 | and for bright regions outside sunspots, the TR is located at $2000\pm100$ km.; In the Table [\[Table_TR\]](#Table_TR) we present the average height of the transition region (TR), which is one of the five free parameters fitted in the GA process, for each atmospheric class: thus, 1080$\pm$20 km above the solar surface for umbrae, 1800$\pm$50 km for penumbrae, and 2000$\pm$100 km for plages. |
| Quiet Sun brightness temperature at 17 GHz | 10050 | 120 | K | 1 | At 17 GHz, $T_{qS}=10050\pm 120$ K, and AR 12470 has brightness temperatures varying from $5.3\times10^4$ to $6.8\times10^4$ K in the areas with $/\vec{B}/>1500$ G. |
| Observed AR 12470 brightness temperature range at 230 GHz (where |B| > 1500 G) | 5800 to 6600 | not stated | K | 1 | While the quiet Sun brightness temperature ( $T_\mathrm{b,QS}$) at 230 GHz is $6210\pm110$ K (cite: Selhorst2019), the AR 12470 brightness temperature ($T_\mathrm{b}$) varies from 5800 to 6600 K across locations with magnetic field intensities greater than 1500 G |
| Observed AR 12470 brightness temperature range at 100 GHz (where |B| > 1500 G) | 7200 to 7650 | not stated | K | 1 | At 100 GHz, $T_{qS}=7110\pm90$ K (cite: Selhorst2019) and AR 12470 showed $T_\mathrm{b}$ varying from 7200 to 7650 K where $/\vec{B}/>1500$ G. |
| Observed AR 12470 brightness temperature range at 17 GHz (where |B| > 1500 G) | 5.3e4 to 6.8e4 | not stated | K | 1 | At 17 GHz, $T_{qS}=10050\pm 120$ K, and AR 12470 has brightness temperatures varying from $5.3\times10^4$ to $6.8\times10^4$ K in the areas with $/\vec{B}/>1500$ G. |
| Observed Umbra averaged brightness temperature at 230 GHz | 0.99 | 0.04 | T_qS | 5 | / Umbra / $0.99\pm0.04$ / $0.98\pm0.01$ / $1.00 \pm0.01$ / $1.03\pm0.01$ / $1.02\pm0.01$ / $1.06\pm0.01$ / |
| Modeled Umbra averaged brightness temperature at 230 GHz (2" resolution) | 0.98 | 0.01 | T_qS | 5 | / Umbra / $0.99\pm0.04$ / $0.98\pm0.01$ / $1.00 \pm0.01$ / $1.03\pm0.01$ / $1.02\pm0.01$ / $1.06\pm0.01$ / |
| Modeled Umbra averaged brightness temperature at 230 GHz (25" resolution) | 1.00 | 0.01 | T_qS | 5 | / Umbra / $0.99\pm0.04$ / $0.98\pm0.01$ / $1.00 \pm0.01$ / $1.03\pm0.01$ / $1.02\pm0.01$ / $1.06\pm0.01$ / |
| Observed Umbra averaged brightness temperature at 100 GHz | 1.03 | 0.01 | T_qS | 5 | / Umbra / $0.99\pm0.04$ / $0.98\pm0.01$ / $1.00 \pm0.01$ / $1.03\pm0.01$ / $1.02\pm0.01$ / $1.06\pm0.01$ / |
| Modeled Umbra averaged brightness temperature at 100 GHz (2" resolution) | 1.02 | 0.01 | T_qS | 5 | / Umbra / $0.99\pm0.04$ / $0.98\pm0.01$ / $1.00 \pm0.01$ / $1.03\pm0.01$ / $1.02\pm0.01$ / $1.06\pm0.01$ / |
| Modeled Umbra averaged brightness temperature at 100 GHz (58" resolution) | 1.06 | 0.01 | T_qS | 5 | / Umbra / $0.99\pm0.04$ / $0.98\pm0.01$ / $1.00 \pm0.01$ / $1.03\pm0.01$ / $1.02\pm0.01$ / $1.06\pm0.01$ / |
| Observed Penumbra averaged brightness temperature at 230 GHz | 1.05 | 0.05 | T_qS | 5 | / Penumbra / $1.05\pm0.05$ / $1.04\pm0.01$ / $1.02 \pm~0.02$ / $1.05\pm0.02$ / $1.07\pm0.01$ / $1.07\pm0.02$ / |
| Modeled Penumbra averaged brightness temperature at 230 GHz (25" resolution) | 1.02 | 0.02 | T_qS | 5 | / Penumbra / $1.05\pm0.05$ / $1.04\pm0.01$ / $1.02 \pm~0.02$ / $1.05\pm0.02$ / $1.07\pm0.01$ / $1.07\pm0.02$ / |
| Observed Penumbra averaged brightness temperature at 100 GHz | 1.05 | 0.02 | T_qS | 5 | / Penumbra / $1.05\pm0.05$ / $1.04\pm0.01$ / $1.02 \pm~0.02$ / $1.05\pm0.02$ / $1.07\pm0.01$ / $1.07\pm0.02$ / |
| Modeled Penumbra averaged brightness temperature at 100 GHz (58" resolution) | 1.07 | 0.02 | T_qS | 5 | / Penumbra / $1.05\pm0.05$ / $1.04\pm0.01$ / $1.02 \pm~0.02$ / $1.05\pm0.02$ / $1.07\pm0.01$ / $1.07\pm0.02$ / |
| Observed Plages averaged brightness temperature at 230 GHz | 1.07 | 0.07 | T_qS | 5 | / Plages / $1.07\pm0.07$ / $1.08\pm0.05$ / $1.04 \pm0.04$ / $1.06\pm0.04$ / $1.10\pm0.04$ / $1.06\pm0.03$ / |
| Modeled Plages averaged brightness temperature at 230 GHz (25" resolution) | 1.04 | 0.04 | T_qS | 5 | / Plages / $1.07\pm0.07$ / $1.08\pm0.05$ / $1.04 \pm0.04$ / $1.06\pm0.04$ / $1.10\pm0.04$ / $1.06\pm0.03$ / |
| Observed Plages averaged brightness temperature at 100 GHz | 1.06 | 0.04 | T_qS | 5 | / Plages / $1.07\pm0.07$ / $1.08\pm0.05$ / $1.04 \pm0.04$ / $1.06\pm0.04$ / $1.10\pm0.04$ / $1.06\pm0.03$ / |
| Modeled Plages averaged brightness temperature at 100 GHz (58" resolution) | 1.06 | 0.03 | T_qS | 5 | / Plages / $1.07\pm0.07$ / $1.08\pm0.05$ / $1.04 \pm0.04$ / $1.06\pm0.04$ / $1.10\pm0.04$ / $1.06\pm0.03$ / |
| Observed Polarized region averaged brightness temperature at 17 GHz | 3.69 | 1.35 | T_qS | 5 | / Polarized / $3.69\pm 1.35$ / $1.06\pm 0.03$ / $1.06\pm 0.02$ / $9.41\pm 3.51$ / $4.08\pm1.19$ / |
| Modeled Polarized region averaged brightness temperature at 17 GHz with free-free + gyroresonance (10" resolution) | 4.08 | 1.19 | T_qS | 5 | / Polarized / $3.69\pm 1.35$ / $1.06\pm 0.03$ / $1.06\pm 0.02$ / $9.41\pm 3.51$ / $4.08\pm1.19$ / |
| Observed Non-polarized region averaged brightness temperature at 17 GHz | 1.58 | 0.32 | T_qS | 5 | / Non-polarized / $1.58\pm 0.32$ / $1.04\pm 0.06$ / $1.04\pm 0.06$ / $1.04\pm 0.06$ / $1.04\pm 0.05$ / |
| Modeled Non-polarized region averaged brightness temperature at 17 GHz with free-free + gyroresonance (10" resolution) | 1.04 | 0.05 | T_qS | 5 | / Non-polarized / $1.58\pm 0.32$ / $1.04\pm 0.06$ / $1.04\pm 0.06$ / $1.04\pm 0.06$ / $1.04\pm 0.05$ / |

## Qualitative findings

- Umbrae, penumbrae, and plages have a narrower temperature-minimum region and a thinner chromosphere than the quiet Sun, with compression most pronounced in umbral pixels.  
  > "Comparison with the quiet-Sun model indicates that the umbrae, penumbrae and plages have a narrower temperature-minimum region and a thinner chromosphere than the quiet Sun, as can be seen in Table [\[Table:profile\]](#Table:profile) and Figure [4](#fig:temp_dens)." (Free-free contribution); "Moreover, the compression of the temperature minimum and the chromosphere are most pronounced in umbral pixels, i.e. the region with more intense magnetic fields (Figure [4](#fig:temp_dens))." (Free-free contribution)
- The umbral region is the only region presenting a significant increase in coronal temperature, required to produce the high 17 GHz gyroresonance brightness temperatures.  
  > "Furthermore, the umbral region is the only one that presents a significant increase in the coronal temperature, which is necessary to reach the high $T_\mathrm{b}$ values observed in the gyroresonance source at 17 GHz (cite: Selhorst2008; Selhorst2009)." (Free-free contribution)
- At 17 GHz in the umbral core, the 3rd gyroresonance harmonic occurs between 1150 and 1900 km and provides an optical depth tau ~ 0.1 (three orders of magnitude larger than free-free), producing a contribution function peak ~20 times larger than free-free.  
  > "The 3rd harmonic occurs between 1150 and 1900 km in altitude, while the 4th harmonic occurs between 2550 and 4050 km." (Gyroresonance contribution); "The 3rd harmonic provides an optical depth of $\tau\sim10^{-1}$ (Figure [6](#fig:kappa17)b red curve) that is three orders of magnitude greater than the free-free optical depth (Figure [6](#fig:kappa17)b black curve)." (Gyroresonance contribution); "While the free-free CF shows a single peak at around 800 km (black curve), when the gyroresonance is included an intense peak appears at TR/coronal heights (red curve) that is $\sim 20$ times greater than the free-free contribution." (Gyroresonance contribution)

## Claim tuples

- H: A genetic algorithm modifying a 1D quiet Sun atmospheric model along 3D linear force-free extrapolated magnetic field lines can determine temperature and electron density profiles that reproduce observed active region brightness temperatures at 17, 100, and 230 GHz. | E: Applied the Pikaia genetic algorithm with 5 free parameters per pixel to AR NOAA 12470 using SDO/HMI magnetograms, ALMA 100 and 230 GHz single-dish maps, and NoRH 17 GHz maps, computing thermal bremsstrahlung and gyroresonance radiative transfer. | R: Derived distinct transition region heights for umbrae (1080 ± 20 km), penumbrae (1800 ± 50 km), and plages (2000 ± 100 km); simulated 230 and 100 GHz brightness temperatures match observations within uncertainties across all AR regions, and 17 GHz polarized emission matches when gyroresonance is included (4.08 ± 1.19 vs 3.69 ± 1.35 T_qS). | F: The GA-constrained atmospheric model successfully reproduces the ALMA 100 and 230 GHz maps and the 17 GHz polarized gyroresonance core, though it underpredicts the maximum T_b in 17 GHz non-polarized regions (1.2 vs 2.8 T_qS). | **partially**
- H: The dark sunspot umbra observed at 230 GHz and the bright polarized core at 17 GHz arise from a compressed chromosphere/transition region in strong magnetic fields combined with 17 GHz gyroresonance opacity in the corona/TR. | E: Evaluated optical depths and contribution functions for free-free and gyroresonance (s <= 5) emission in the umbral atmospheric model and compared synthetic images with and without gyroresonance and beam convolution. | R: At 230 GHz the unconvolved model umbra is darker than the quiet Sun (0.98 ± 0.01 T_qS, smoothed to 1.00 ± 0.01 T_qS at 25" resolution); at 17 GHz, free-free alone yields a dark umbra (1.06 ± 0.02 T_qS), whereas including 3rd and 4th harmonic gyroresonance opacity (tau ~ 0.1) increases T_b to 4.08 ± 1.19 T_qS at 10" resolution. | F: Thermal free-free emission from a compressed umbral atmosphere produces a dark umbra at millimeter wavelengths (and would at 17 GHz if alone), while 3rd-harmonic gyroresonance opacity in the hot umbral corona/TR dominates at 17 GHz to produce the bright polarized core. | **supported**

## Reasoning

- Why this data: AR NOAA 12470 was selected due to the availability of multi-frequency radio observations at 17 GHz (NoRH) and 100 and 230 GHz (ALMA Science Verification) along with SDO/HMI magnetograms, probing distinct atmospheric layers.  
  > "The different frequencies provide access to different layers of the atmosphere due to the frequency dependence of opacity." (Atmospheric modelling via genetic algorithm); "In this work, we selected the active region AR NOAA 12470 to test our algorithm. This region was selected due to the availability of radio observations at three frequencies: 17 GHz, from the Nobeyama Radio Heliograph (NoRH), 100 and 230 GHz from the Atacama Large Millimetric and submillimetric Array (ALMA) (cite: Shimojo2017; Valle2021)." (Observations)
- Why this method: A genetic algorithm modifying a seed quiet Sun model along 3D LFF extrapolated magnetic fields improves upon manual semi-empirical modeling (Selhorst et al. 2008, 2009) and PFSS modeling (Brajša et al. 2020) by automatically optimizing temperature and density profiles per pixel.  
  > "As an improvement of the AR modelling presented in (cite: Selhorst2008; Selhorst2009), in this work we apply a genetic algorithm (cite: Charbonneau1995) to modify a standard quiet Sun atmospheric model in order to determine the best plasma temperature and density height profiles necessary to match the observations of NOAA 12470 obtained by ALMA (single-dish maps at 100 and 230 GHz) and NoRH (17 GHz interferometric map)." (Introduction); "The general extrapolated magnetic structure is consistent with the ALMA observations, but a detailed analysis and comparison with ALMA small-scale features was not possible with the model used and requires a more detailed magnetic field extrapolation model, what is performed in the present work." (Introduction)
- Alternative: Potential-field extrapolation (alpha = 0) was rejected in favor of alpha = -0.005 because alpha = -0.005 generated a greater number of closed magnetic field lines in the selected region.  
  > "here $\alpha=-0.005$ was chosen for the LFF extrapolation since it generated a greater number of closed magnetic field lines in the selected region than did the potential-field extrapolation ($\alpha=0$)." (Results)
- Alternative: Including photospheric magnetic fields below |B|_min = 200 G was rejected because it resulted in simulated ARs appearing much larger than observed ARs.  
  > "A different minimum value could be chosen by the user, but we found that the inclusion of magnetic fields below this limit resulted in the simulated ARs appearing much larger than the observed ARs." (Magnetic field extrapolation)
- Alternative: Classifying AR regions using white light images (as in Nita et al. 2018) was rejected in favor of magnetogram field intensity thresholds because white light separation is not useful for faint or spotless ARs.  
  > "In (cite: Nita2018), the authors proposed a similar separation, however, in that work the separation was based on solar white light images instead of a magnetogram, which is not useful for faint or spotless ARs." (Results)
- How they decided it was enough: The GA was run for 10 generations of 100 children because chi-squared typically stabilizes by about the 7th generation, stopping when chi-squared ceases to reduce further.  
  > "In our runs the $\chi^2$ measure typically stabilizes to a minimum value by about the seventh generation." (Genetic Algorithm Features); "The final model is obtained when the $\chi^2$ from the GA process ceases to reduce further." (Results)
- Limitation (authors): The genetic algorithm is purely a mathematical solution and does not verify whether the atmospheric plasma is in local thermodynamic equilibrium (LTE).  
  > "Nevertheless, the GA used here is a mathematical solution and it does not verify if the atmospheric plasma is in local thermodynamic equilibrium (LTE) or not." (Genetic Algorithm Features)
- Limitation (authors): Low spatial resolution of ALMA single-dish observations (25" at 230 GHz, 58" at 100 GHz) smooths the dark umbra (25" diameter) with surrounding bright areas, masking the umbra at 100 GHz and reducing its contrast at 230 GHz.  
  > "The resulting low contrast of the dark umbra with respect to the quiet Sun in the model is due to the low resolution of the ALMA single-dish observations. Since the umbral size is almost equal to the ALMA 230 GHz beam, the umbral $T_\mathrm{b}$ is smoothed with the bright surrounding areas." (Comparison of the synthetic and observed radio images)
- Limitation (authors): The modeled atmospheric profiles that fit 230 and 100 GHz well cannot reach the high brightness temperatures observed at 17 GHz in non-polarized regions (reaching at most 1.2 T_qS vs. 2.8 T_qS observed).  
  > "However, the modeled atmospheric profiles that achieved good agreement with the $T_\mathrm{b}$ observations at 230 and 100 GHz were not able to reach the high $T_\mathrm{b}$ values observed at 17 GHz. While these regions showed observational values as high as $2.8\times T_{qS}$, the model was only able to reach a maximum $T_\mathrm{b}$ of $1.2\times T_{qS}$ (Figure [7](#fig:NoRH)b)." (Comparison of the synthetic and observed radio images)
- Limitation (authors): The modeled 17 GHz polarized gyroresonance source is smaller and rounder than the observed elliptical source.  
  > "Nevertheless, as can be observed in Figure [\[emiss_giro3\]](#emiss_giro3), the shape of the modelled polarized region is smaller and rounder, while the observed source appears elliptical." (Comparison of the synthetic and observed radio images)
- Caveat (inferred, ours): Fitting 5 free parameters per pixel against only 3 frequency data points (17, 100, and 230 GHz) is an under-constrained optimization problem per line of sight, relying heavily on parameter bounds and initial class seeds that are not explicitly tabulated.
- Caveat (inferred, ours): The pixel-by-pixel GA optimization compares 2" model columns against observed maps that have vastly different beam sizes (58" at 100 GHz, 25" at 230 GHz, 10-18" at 17 GHz) before final beam convolution, introducing beam-dilution biases into the un-deconvolved pixel fits.
- Caveat (inferred, ours): The observations at the three frequencies are non-simultaneous (02:44 UT at 17 GHz, 14:52 UT at 230 GHz, 19:35 UT at 100 GHz), spanning nearly 17 hours during which solar active region evolution can occur.

## Reproducibility

- Data public (paper): ALMA Science Verification data publicly available via the ALMA Science Portal (ADS/JAO.ALMA#2011.0.00020.SV, https://almascience.eso.org/alma-data/science-verification)  
  > "The ALMA maps used here were obtained during the Science Verification period, 2015 December 16–20 [^2]." (Radio maps); "This paper makes use of the following ALMA data: ADS/JAO. ALMA#2011.0.00020.SV." (Acknowledgments); "https://almascience.eso.org/alma-data/science-verification" (Footnote 2)
- Products in archive: Science Verification single-dish maps available in ALMA Science Verification archive  
  > "The ALMA maps used here were obtained during the Science Verification period, 2015 December 16–20 [^2]." (Radio maps); "https://almascience.eso.org/alma-data/science-verification" (Footnote 2)
- Code: _not stated_
- Missing: Exact mathematical equations defining how the 5 free parameters (chromospheric gradients, coronal multipliers, and TR shift) modify the seed SSC height profile
- Missing: Minimum and maximum parameter search bounds supplied to Pikaia for each of the 5 free parameters and for each of the 3 AR region classes
- Missing: Custom IDL code for the radiative transfer, Pikaia wrapper, and LFF extrapolation (unless using GX Simulator in SolarSoft)
- Missing: Exact bounding box coordinates used to crop the 1024x1024 active region area from the full-disk 4096x4096 HMI magnetogram
- Data volume (inferred): Small (< 1 GB): single-dish ALMA FITS maps (800x800 and 400x400 pixels), one NoRH 512x512 map, one SDO/HMI 4096x4096 magnetogram, and 256x256xN 3D model cubes.
- Score (inferred): 6/5, All observational data (ALMA SV, SDO/HMI, NoRH) are public and exact timestamps, rotation angles, grid dimensions, GA hyperparameters, radiative transfer equations, and final tabulated model profiles are provided; however, the exact mathematical parameterization of the 5 GA modifications to the SSC profile and their prior search ranges are not explicitly written out.
- Rediscovery candidate: yes, All input datasets (ALMA SV 2011.0.00020.SV, SDO/HMI, NoRH) are public, the physical equations and GA settings are well specified, and the paper provides clear numeric answer keys (TR heights and region-averaged brightness temperatures).

## Links

- Method: Charbonneau (1995) (cite: Charbonneau1995) (Pikaia genetic algorithm used for atmospheric profile optimization)
- Method: White et al. (2017) (cite: White2017) (Fast-scan single-dish solar mapping method for ALMA)
- Method: Selhorst et al. (2005b) (cite: Selhorst2005b) (SSC quiet Sun atmospheric model used as the seed model)
- Method: Selhorst et al. (2008) (cite: Selhorst2008) (5-parameter active region atmospheric modeling framework and IDL LFF extrapolation)
- Method: Nakagawa & Raadu (1972) (cite: Nakagawa1972) (Linear force-free magnetic field extrapolation method)
- Method: Seehafer (1978) (cite: Seehafer1978) (Linear force-free magnetic field extrapolation method)
- Companion: Valle Silva et al. (2021) (cite: Valle2021) (Previous study by overlapping authors analyzing the same AR 12470 with ALMA single-dish and NoRH data)
- Companion: Selhorst et al. (2019) (cite: Selhorst2019) (Previous study by overlapping authors establishing the reference frequencies and quiet Sun brightness temperatures for the ALMA SV data)
- Related: ALMA Solar Science Verification (2011.0.00020.SV)
- Related: SolarALMA

## Checks

```json
{
 "quotes": 144,
 "quotes_ok": 144,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 19,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00020.SV"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 25,
 "numeric_problems": 0,
 "fill": {
  "facts": 98,
  "stated": 66,
  "rate": 0.673
 },
 "evidence_ok": true
}
```
