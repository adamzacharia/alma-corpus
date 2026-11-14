# ALMA-IMF: XVIII. The assembly of a star cluster: Dense N<SUB>2</SUB>H<SUP>+</SUP> (1─0) kinematics in the massive G351.77 protocluster

`2025A&A...696A.202S` | Astronomy and Astrophysics 2025 | first author: Sandoval-Garrido, N. A. | arXiv: 2410.09843 | DOI: 10.1051/0004-6361/202452589

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: star_formation, milky_way_ism
- Question: Kinematics of the cold, dense gas in the G351.77 protocluster traced by N2H+ (1-0): velocity structure, inflow signatures (V- and Straight-shapes in PV diagrams), timescales and mass inflow rates  
  > "In this paper, we focus on the kinematics of dense and cold gas within the massive G351.77 protocluster using the N$_2$H$^+$ (1-0) spectral line emission." (1 Introduction)
- Target **G351.77 protocluster (G351.77-0.53, IRAS 17233-3606)**: coordinates _not stated_; z/distance ~2 ± 0.14 kpc  
  > "The high-mass star-forming region G351.77-0.53 (IRAS 17233-3606) is a filamentary infrared dark cloud (IRDC)" (1 Introduction); "located at $\sim\,2\,\pm\,0.14$ kpc and whose estimated mass is $\sim\,10200$ $\hbox{\rm M}_{\odot}$ for the entire filament within an area of 11 pc$^2$ (cite: Simon)" (1 Introduction); distance from Reyes-Reyes et al. 2024 (cite: Simon)  
  > "The high-mass star-forming region G351.77-0.53 (IRAS 17233-3606) is a filamentary infrared dark cloud (IRDC)" (1 Introduction); "located at $\sim\,2\,\pm\,0.14$ kpc and whose estimated mass is $\sim\,10200$ $\hbox{\rm M}_{\odot}$ for the entire filament within an area of 11 pc$^2$ (cite: Simon)" (1 Introduction)

## Data provenance

- ALMA projects: 2017.1.01355.L, 2013.1.01365.S, 2015.1.01273.S
- bands: 3 mm band for N2H+ (1-0) (ALMA-IMF also uses 1.3 mm)  
  > "We analyze the N$_2$H$^+$ (1-0) observations of the G351.77 protocluster in the 3 mm spectral band" (2 Data)
- frequencies and spectral setup: N2H+ (1-0) at ~93.173 GHz; spectral resolution 0.23 km/s; 215 channels in cube, 110 emission channels from -13.35 to 11.72 km/s  
  > "This gas is accessed here via the N$_2$H$^+$ (1-0) line at $\sim$ 93.173 GHz." (1 Introduction); "Out of the 215 channels of the data-cube, there are 110 that correspond to emission channels, which goes from -13.35 to 11.72 $\rm km\,s^{-1}$, with a spectral line resolution of 0.23 $\rm km\,s^{-1}$." (Appendix: N2H+ raw data)
- continuum bandwidth: _not stated_
- arrays: 12m-array, 7m-array and Total Power (TP)  
  > "The ALMA-IMF Large Program utilized the 12m-array, 7m-array and Total Power (TP) antennas of the Atacama Large Millimeter/Submillimeter Array (ALMA), employing the 1.3 mm and 3 mm bands" (1 Introduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Beams 2.3'' x 2.1'' (12m), 16.9'' x 10.1'' (7m), 69.6'' x 69.6'' (TP); maximum spatial resolution ~4000 au  
  > "Our data has a maximum spatial resolution of $\sim$ 4000 au and a spectral resolution of 0.23 $\rm km\,s^{-1}$." (2 Data); "The beam sizes are (2.3$''$ $\times$ 2.1$''$), (16.9$''$ $\times$ 10.1$''$), and (69.6$''$ $\times$ 69.6$''$) for the 12m-array, 7m-array, and TP, respectively." (2 Data)
- max recoverable scale: _not stated_
- sensitivity: mean rms ~0.66 K across the map; ~0.40 K in regions with S/N > 9  
  > "The mean rms value across the entire map is $\sim$ 0.66 K, whereas the mean value in regions with S/N \> 9 is $\sim$ 0.40 K." (2.1 N2H+ data imaging)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Data obtained from the ALMA-IMF Large Program (cite: motte22)  
  > "observed by the 12m-array, 7m-array and TP configurations obtained from the ALMA-IMF Large Program" (2 Data)
- Line: N2H+ (1-0), seven hyperfine components (~93.173 GHz)
- Line: DCN (3-2) (ancillary, from Cunningham et al. 2023) (not stated)
- Line: H2CO (3-2) in Sect. 2.2 but (2-1) in Sect. 6.5 (paper is inconsistent) (not stated)
- Other facility **SOFIA/HAWC+ (53, 89, 214 um)**: Contributed to the dust-based H2 column density map of G351.77 (intermediate product at 6'' resolution)  
  > "derived from a combination of 1.3 mm band, SOFIA/HAWC+ (53 $\mu$m, 89 $\mu$m, and 214 $\mu$m), APEX/SABOCA (350 $\mu$m) and APEX/LABOCA (870 $\mu$m) observations (cite: Pierre)" (2.2 Other ALMA-IMF data)
- Other facility **APEX/SABOCA (350 um)**: Contributed to the dust-based H2 column density map  
  > "derived from a combination of 1.3 mm band, SOFIA/HAWC+ (53 $\mu$m, 89 $\mu$m, and 214 $\mu$m), APEX/SABOCA (350 $\mu$m) and APEX/LABOCA (870 $\mu$m) observations (cite: Pierre)" (2.2 Other ALMA-IMF data)
- Other facility **APEX/LABOCA (870 um)**: Contributed to the dust-based H2 column density map  
  > "derived from a combination of 1.3 mm band, SOFIA/HAWC+ (53 $\mu$m, 89 $\mu$m, and 214 $\mu$m), APEX/SABOCA (350 $\mu$m) and APEX/LABOCA (870 $\mu$m) observations (cite: Pierre)" (2.2 Other ALMA-IMF data)
- External data: Smoothed getsf 1.3 mm core catalog (18 cores; masses and sizes used for associations and free-fall times)  
  > "core catalog from (cite: Fabien), derived from the continuum images of the 1.3 mm band (cite: adam22)" (2.2 Other ALMA-IMF data) [from Louvet et al. 2024 (cite: Fabien)]
- External data: DCN (3-2) core kinematics, integrated intensity map and mean velocity map from the 12m-array  
  > "We also utilize the core kinematics, integrated intensity map, and mean velocity map obtained from the DCN (3-2) spectral line fits from the 12m-array (cite: Nichol)." (2.2 Other ALMA-IMF data) [from Cunningham et al. 2023 (cite: Nichol)]
- External data: H2CO integrated intensity and mean velocity maps from the 12m-array ALMA-IMF spectral setup  
  > "Further, we make use of the integrated intensity map and mean velocity map of H$_2$CO (3-2) derived from the 12m-array observations as part of the spectral setup of the ALMA-IMF Large Program (cite: motte22)." (2.2 Other ALMA-IMF data) [from Motte et al. 2022 (cite: motte22)]
- External data: H2 column density map at 6'' resolution (intermediate product), used for abundance, masses and X(N2H+)  
  > "we use an intermediate product of the H$_2$ column density map of G351.77 at 6$''$ resolution" (2.2 Other ALMA-IMF data) [from Dell'Ova et al. 2024 (cite: Pierre)]
- External data: Distance ~2 kpc and Mother Filament mass ~10200 Msun  
  > "located at $\sim\,2\,\pm\,0.14$ kpc and whose estimated mass is $\sim\,10200$ $\hbox{\rm M}_{\odot}$ for the entire filament within an area of 11 pc$^2$ (cite: Simon)" (1 Introduction) [from Reyes-Reyes et al. 2024 (cite: Simon)]
- External data: Average relative abundances X(DCN) = 2.06e-10 and X(H2CO) = 4.66e-10  
  > "using average relative abundances, where X(DCN) $=2.06~\times~10^{-10}$ and X(H$_2$CO) $=4.66~\times~10^{-10}$ (cite: Maret; Minh)" (6.5 Multi-tracer modeling) [from Maret et al. 2004; Minh et al. 2018 (cite: Maret; Minh)]
- External data: SiO outflow catalog compared with PV features  
  > "we do not observe agreement between the position of outflow catalogs (cite: towner) and the position of cores associated with V-shapes in PV diagrams" (5.1 Kinematic analysis on small scales) [from Towner et al. 2023 (cite: towner)]
- Simulation/model as data: Own toy model: sphere with power-law density (gamma = 3.1), gravitational infall V_in = -sqrt(2GM/r) and Keplerian rotation V_rot = sqrt(GM/r), r_min = 0.007 pc, r_max = 0.8 pc, M = 270 and 2700 Msun, used to make model PV diagrams  
  > "we utilize a $r_{\rm min} = 0.007$pc and a $r_{\rm max}$ = 0.8 pc, which correspond approximately to the coverage radius of N$_2$H$^+$." (6.5 Multi-tracer modeling); "Also, we define $\gamma$ = 3.1 based on the maximum velocities that the data reach and in how well are the model fits to the data." (6.5 Multi-tracer modeling)

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

- task: CASA tclean on 12m data, then tclean on 12m+7m (7M12M), imcontsub, feather with TP  
  > "Initially, we imaged the 12m-array data to determine the optimal parameter settings to achieve the highest quality results." (2.1 N2H+ data imaging); "Subsequently, we applied the same parameter values to combine the 12m-array and 7m-array data with *tclean* to increase the Fourier coverage (7M12M, henceforth)." (2.1 N2H+ data imaging)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: pbmask and pblimit explored; pblimit raised from 0.05 to 0.2 for the 7M12M product to remove edge artifacts  
  > "we explored different imaging results by varying: *threshold*, *deconvolver*, *pbmask*, *pblimit* and *scales*." (2.1 N2H+ data imaging); "by increasing the pblimit value from 0.05 to 0.2 for this product" (2.1 N2H+ data imaging)
- multiscale scales: _not stated_
- continuum subtraction: CASA imcontsub using line-free channels to build the continuum model, applied to the 7M12M data  
  > "Continuum subtraction was accomplished using the CASA task *imcontsub*." (2.1 N2H+ data imaging); "This task uses the channels free of line emission to generate a continuum model, which is subtracted from the line emission channels." (2.1 N2H+ data imaging)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12m + 7m combined in tclean (7M12M); 7M12M continuum-subtracted data feathered with TP (7M12M = high resolution, TP = low resolution)  
  > "As a final step, we employed the CASA task *feather* to combine the 7M12M continuum subtracted data with the TP data to recover the extended line emission." (2.1 N2H+ data imaging); "Here we define the 7M12M continuum subtracted data as the high resolution data, and the TP as the low resolution data." (2.1 N2H+ data imaging)
- smoothing: For the X(N2H+) analysis, data brought to matched resolution and pixel scale with the 6'' N(H2) map and the cube was re-fit  
  > "In the first step, we convolved to a matched resolution and pixel scales the N(H$_2$) data." (4.2 N2H+ relative abundance)
- final beam: 2.3'' x 2.1'', BPA 89 deg  
  > "and whose size final synthesized beam is 2.3$''$ $\times$ 2.1$''$ and a Beam-Position-Angle (BPA) of 89$^{\circ}$" (2.1 N2H+ data imaging)
- final rms: mean rms ~0.66 K across map; ~0.40 K where S/N > 9  
  > "The mean rms value across the entire map is $\sim$ 0.66 K, whereas the mean value in regions with S/N \> 9 is $\sim$ 0.40 K." (2.1 N2H+ data imaging)

### Inherited from earlier work

- Imaging parameter values (threshold, deconvolver, pbmask, pblimit, scales) come from the ALMA-IMF imaging_parameters.py file  
  > "These parameter values [^4] were selected based on the analysis of the residuals, model, and the image returned after each imaging process" (2.1 N2H+ data imaging) [from https://github.com/ALMA-IMF/reduction/blob/master/reduction/imaging_parameters.py (footnote 4)]
- Imaging done with CASA 6.2 together with the ALMA-IMF data pipeline  
  > "The data imaging process was performed using CASA 6.2 (cite: CASA) along with the ALMA-IMF data pipeline" (2.1 N2H+ data imaging) [from ALMA-IMF reduction pipeline, https://github.com/ALMA-IMF/reduction (footnote 2)]
- PySpecKit n2hp_vtau cube fitting approach follows earlier N2H+ studies  
  > "(cite: PySpecKit11; PySpecKit22) to fit the cube (cite: Elena; Valentina19; Rodrigo21)" (3 Line fitting procedure) [from (cite: Elena; Valentina19; Rodrigo21)]
- Constant Tex for spectra with tau < 1  
  > "assigning them a constant T$_{\rm ex}$ value (cite: Caselli1; Caselli2)" (3.1 One-velocity-component fit) [from (cite: Caselli1; Caselli2)]
- Optically thick-transition column density expression for N2H+  
  > "we use the optically thick transitions approximation given by the following expression (cite: Caselli2; Elena):" (4.1 N2H+ column density and mass) [from (cite: Caselli2; Elena); constants from (cite: Laurent; Jeffrey; Elena)]
- Velocity-gradient timescale t_VG = 1/VG, PV diagram construction and V-shape interpretation  
  > "we estimate their associated timescales as $t_{\text{VG}} = \frac{1}{\text{VG}}$, (cite: Rodrigo21; rodrigo24)" (5.1 Kinematic analysis on small scales); "and $b$ or $l$ coordinates (cite: Henshaw; Valentina19; Rodrigo21; Elena22; rodrigo24)" (5 Kinematic analysis) [from (cite: Rodrigo21; rodrigo24; Henshaw; Valentina19; Elena22)]
- Evolutionary-stage classification of G351.77 as Intermediate  
  > "it is classified as being in an Intermediate evolutionary stage compared to other ALMA-IMF protoclusters" (1 Introduction) [from (cite: motte22; Roberto)]

### Not stated but needed to reproduce (our reading)

- Actual tclean settings (threshold, deconvolver, scales, pbmask, weighting/robust, cell, imsize, niter) are only in the external imaging_parameters.py; paper gives none of them
- Line-free channels used by imcontsub and feather parameters (e.g. sdfactor) not given
- Calibration state of the ALMA-IMF 12m/7m/TP data (pipeline vs manual, CASA version, flux calibrator, self-calibration) not given; which MOUS/execution blocks of 2017.1.01355.L vs 2013.1.01365.S and 2015.1.01273.S enter the cube is not said
- PySpecKit version, fitter/optimiser and how S/N is defined per spectrum (peak over rms of which channels) not given
- Spectroscopic constants for the column density equation (Q, A_ul, g_u, E_u, nu) and the hyperfine set used are not tabulated
- Exact N(H2) intermediate map (6'' product, 'Dell'Ova, private communication 2024') and the convolution/regridding kernel used to match it are not given
- How V-/Straight-shape points are picked for the linear VG fits (manual envelope selection, intensity cutoffs, vertex position) and how M_tot is summed over those points is not specified
- Core sizes, masses and positions needed for the 6x-radius PV analysis come from external tables (Louvet et al. 2024), not reproduced
- Code for the fits, PV/PPV analysis and the toy model is not released

## Analysis recipe

1. **Image and combine 12m, 7m and TP data into a continuum-subtracted N2H+ cube**: Tune tclean on 12m data, apply same parameters to 12m+7m (7M12M), subtract continuum with imcontsub, feather with TP to recover extended emission  
  > "Initially, we imaged the 12m-array data to determine the optimal parameter settings to achieve the highest quality results." (2.1 N2H+ data imaging); "Subsequently, we applied the same parameter values to combine the 12m-array and 7m-array data with *tclean* to increase the Fourier coverage (7M12M, henceforth)." (2.1 N2H+ data imaging); "As a final step, we employed the CASA task *feather* to combine the 7M12M continuum subtracted data with the TP data to recover the extended line emission." (2.1 N2H+ data imaging)
   - software: CASA 6.2, tclean, imcontsub, feather, ALMA-IMF data pipeline
   - parameter: pblimit increased from 0.05 to 0.2 for the 7M12M product  
  > "by increasing the pblimit value from 0.05 to 0.2 for this product" (2.1 N2H+ data imaging)
   - parameter: Final cube: 0.23 km/s resolution, beam 2.3'' x 2.1'', BPA 89 deg  
  > "and whose size final synthesized beam is 2.3$''$ $\times$ 2.1$''$ and a Beam-Position-Angle (BPA) of 89$^{\circ}$" (2.1 N2H+ data imaging)
   - fitting: _not stated_
   - validation: Parameters chosen by inspecting residuals, model and image to minimise residuals  
  > "were selected based on the analysis of the residuals, model, and the image returned after each imaging process, in a way that minimized the residuals in the final product" (2.1 N2H+ data imaging)
2. **Fit hyperfine N2H+ (1-0) spectra with 1- and 2-velocity-component LTE models**: PySpecKit n2hp_vtau LTE hyperfine model fitted to every spectrum with S/N > 9; independent 1- and 2-component fits (First Fitting Procedures); initial guesses refined by averaging fitted parameters over the cube until they stop changing (Final guesses); 4 parameters per component (Tex, tau, V_LSR, sigma_v)  
  > "We only fit spectra with S/N $>$ 9." (3 Line fitting procedure); "This is repeated until no variations are observed in the averages obtained for each parameter compared to previous fits." (3.1 One-velocity-component fit); "In addition to the guesses, each parameter is assigned both a lower and upper limit value, defining the range within which the final fitted values will lie." (3 Line fitting procedure)
   - software: PySpecKit
   - parameter: 1-component FFP guesses (Tex K, tau, V_LSR km/s, sigma_v km/s) = 20.0, 1.0, -3.0, 1.0  
  > "FFP guesses | 20.0 | 1.0 | -3.0 | 1.0" (Table (guesses and limits))
   - parameter: 1-component Final guesses = 12.4, 3.64, -3.77, 1.0  
  > "Final guesses | 12.4 | 3.64 | -3.77 | 1.0" (Table (guesses and limits))
   - parameter: Limits (all fits): Tex (2.73, 100) K, tau (0, 100), V_LSR (-13, 3) km/s, sigma_v (0, 6) km/s  
  > "Limits | (2.73, 100) | (0, 100) | (-13, 3) | (0, 6)" (Table (guesses and limits))
   - parameter: 2-component FFP guesses = 20.0, 1.0, -5.0, 1.0 and 20.0, 1.0, -2.0, 1.0  
  > "FFP guesses | 20.0 | 1.0 | -5.0 | 1.0 | 20.0 | 1.0 | -2.0 | 1.0" (Table (guesses and limits))
   - parameter: 2-component Final guesses = 9.22, 4.60, -5.0, 0.83 and 9.0, 7.4, -2.6, 0.66  
  > "Final guesses | 9.22 | 4.60 | -5.0 | 0.83 | 9.0 | 7.4 | -2.6 | 0.66" (Table (guesses and limits))
   - assumption: LTE hyperfine model with rest frequencies and hyperfine structure from known molecular data  
  > "This model is an LTE model, whose spectroscopic predictions come from known molecular data under the LTE assumption, such as rest frequencies and hyperfine structures." (3 Line fitting procedure)
   - fitting: PySpecKit n2hp_vtau with bounded parameters and iterated guesses; optimiser, priors and likelihood not stated  
  > "In addition to the guesses, each parameter is assigned both a lower and upper limit value, defining the range within which the final fitted values will lie." (3 Line fitting procedure)
   - validation: Synthetic test: fit a high S/N spectrum, add noise on a grid of S/N, refit and compare; more than 200 tests; reliable for S/N > 9, deviations of 3 sigma or more and >30% uncertainties below S/N 9  
  > "This process was repeated for different spectra from the data-cube, fitting 1- and 2-velocity-components, conducting more than 200 different tests." (Appendix: PySpecKit experiment); "The results of this experiment are consistent for both 1- and 2-velocity-component fits, showing that PySpecKit returns reliable values for S/N \> 9." (Appendix: PySpecKit experiment)
3. **Refit low-opacity (tau < 1) spectra with a fixed Tex**: Spectra with tau < 1 are separated and refit with Tex bounded to a range set by the mean Tex of tau >= 1 spectra (1-comp: 2.73-12.4 K; 2-comp: three conditions on tau1/tau2, then conditions a and b); resulting models merged  
  > "Thus, spectra with $\tau\,<\,1$ are selected and separated from the cube to be re-fitted by a 1-velocity-component with a constant T$_{\rm ex}$ value, whose value comes from averaging T$_{\rm ex}$ from spectra with $\tau\,>\,1$." (3.1 One-velocity-component fit); "However, the T$_{\rm ex}$ limits are now 2.73 K to 12.4 K." (3.1 One-velocity-component fit); "At the end of this process, we obtain six separate model spectra and parameter cubes fitted by 2-velocity-components." (3.2 Two-velocity-component fit)
   - software: PySpecKit
   - parameter: 2-comp refit a/b limits: Tex = (2.73 K, 9.22 K) for condition a and (2.73 K, 9.0 K) for condition b  
  > "However, the T$_{\rm ex}$ limits are now T$_{\rm ex}$ = (2.73 K, 9.22 K) for the condition “a” and T$_{\rm ex}$ = (2.73 K, 9.0 K) for the condition “b”." (3.2 Two-velocity-component fit)
   - assumption: Single-transition degeneracy makes Tex and tau inseparable at tau < 1, so a constant Tex is assigned  
  > "This problem arises due to the intrinsic degeneracy when fitting a single transition, which makes it impossible to measure both T$_{\rm ex}$ and $\tau$ from the same transition when $\tau~<~1$." (3.1 One-velocity-component fit)
   - fitting: _not stated_
   - validation: _not stated_
4. **Choose 1- vs 2-component fit per spectrum and merge into a final model cube**: Adopt 1-component where 2-comp fit has sigma_v = 0 or the weaker component peak is below 5x the spectrum noise; remove fits with centroid-velocity errors above 5x the median; for column densities also drop fits with errors above 10% (line width), 30% (Tex), 30% (tau)  
  > "we find some “false component” spectra without emission whose $\sigma_v$ is equal to 0" (3.3 Best fit and merging models); "if the peak intensity is lower than five times the noise measured in that spectrum from the data-cube, the 1-velocity-component fit is adopted." (3.3 Best fit and merging models); "spectra with errors exceeding 10% for the line width, 30% for T$_{\rm ex}$, and 30% for $\tau$ are also excluded" (3.3 Best fit and merging models)
   - software: PySpecKit
   - parameter: Centroid velocity error cut: > 5x median error (~0.2 km/s)  
  > "Additionally, all fitted spectra with errors higher than five times the median error estimated for the centroid velocity" (3.3 Best fit and merging models)
   - fitting: _not stated_
   - validation: Visual inspection of good and bad fits (appendix figures)  
  > "The two methods applied over the model fitted with 1- and 2-velocity-components" (Appendix: Good and bad fitting examples)
5. **Split velocity structure into Blue and Red components**: Cut-off velocity at the midpoint between the First- and Second-component centroid distributions, <V1> + X*sigma1 = <V2> - X*sigma2; 1-component spectra assigned to Blue or Red by the cut; mean V_LSR measured  
  > "To make this somewhat arbitrary but necessary velocity separation, we define the cut-off velocity as the midpoint based on the velocity distributions of the First-velocity-component and the Second-velocity-component" (3.4 Blue and Red velocity component); "we obtain a $X=0.025$." (3.4 Blue and Red velocity component)
   - parameter: X = 0.025  
  > "we obtain a $X=0.025$." (3.4 Blue and Red velocity component)
   - fitting: _not stated_
   - validation: _not stated_
6. **Derive N2H+ column density and mass maps**: Optically-thick-transition column density expression applied to Blue and Red components with fitted sigma_v, tau, Tex; total is the sum; mass per pixel = N * pixel area * m(N2H+), m = 4.817e-23 g; errors by propagation  
  > "given that T$_{ex}$ is not well constrained due to the low optical depth of some spectrum, we use the optically thick transitions approximation given by the following expression (cite: Caselli2; Elena):" (4.1 N2H+ column density and mass); "corresponds to the mass of N$_2$H$^+$ molecule, where $m_{\text{N}_2\text{H}^+} = 4.817 \times 10^{-23}$ g" (4.1 N2H+ column density and mass)
   - parameter: m(N2H+) = 4.817e-23 g  
  > "corresponds to the mass of N$_2$H$^+$ molecule, where $m_{\text{N}_2\text{H}^+} = 4.817 \times 10^{-23}$ g" (4.1 N2H+ column density and mass)
   - assumption: Optically thick transition approximation because Tex is poorly constrained at low tau  
  > "given that T$_{ex}$ is not well constrained due to the low optical depth of some spectrum" (4.1 N2H+ column density and mass)
   - fitting: _not stated_
   - validation: _not stated_
7. **Derive N2H+ relative abundance and H2 column density and mass**: X(N2H+) = N(N2H+)/N(H2) per pixel after refitting the cube at the resolution/pixel scale of the N(H2) map, S/N > 4 in both column densities; representative X = mode of the log-normal distribution with Freedman-Diaconis bin width; X then converts N(N2H+) at original resolution to N_tot and M_tot  
  > "we restrict our analysis to N(N$_2$H$^+$) and N(H$_2$) regions with S/N in column densities $\,>\,4$." (4.2 N2H+ relative abundance); "our objective is to determine a representative value of X(N$_2$H$^+$), whose value will be equal to the mode of this distribution" (4.2 N2H+ relative abundance); "we implement the *Freedman Diaconis Estimator* method in order to derive the most representative value for the protocluster." (4.2 N2H+ relative abundance)
   - software: PySpecKit
   - parameter: Optimal number of bins 119  
  > "the estimated optimal number of bins for our data distribution is 119" (4.2 N2H+ relative abundance)
   - assumption: One representative X(N2H+) for the whole protocluster  
  > "Thus, we define the representative relative abundance of G351.77 in the protocluster zone as" (4.2 N2H+ relative abundance)
   - fitting: _not stated_
   - validation: Modes converge to 1.66e-10 as bin number increases while keeping the log-normal shape; masses within uncertainties of dust-based estimate  
  > "we find that the modes converge to X(N$_2$H$^+$) $=\,1.66\,\times\,10^{-10}$" (4.2 N2H+ relative abundance); "This mass is within our uncertainties and hence represent a good agreement considering the different tracers and techniques involved in this comparison." (4.2 N2H+ relative abundance)
8. **Identify PV features and fit velocity gradients**: Intensity-weighted PV diagrams from centroid velocity, integrated intensity (> 11 K km/s) and b or l; PPV diagrams to separate structures; V- and Straight-shapes identified within 6x core size of catalog cores; linear fit to VGs with integrated intensity as weight  
  > "These parameters are the centroid velocity, integrated intensity (excluding points with emission below 11 K $\rm km\,s^{-1}$ to avoid introducing noise and to better highlight the dominant structures in the diagrams), and $b$ or $l$ coordinates" (5 Kinematic analysis); "We analyze the N$_2$H$^+$ (1-0) velocities around the dense cores within a radius 6 times the size of the core" (5.1 Kinematic analysis on small scales); "For the linear fitting process the integrated intensity is used as a statistical weight." (5.1 Kinematic analysis on small scales)
   - software: PPV diagram web tool
   - parameter: Integrated intensity cut 11 K km/s  
  > "excluding points with emission below 11 K $\rm km\,s^{-1}$ to avoid introducing noise" (5 Kinematic analysis)
   - assumption: Average 45 deg inclination for all timescales and mass inflow rates  
  > "The assumptions here are equivalent to assuming a 45$^{\circ}$ average inclination angle for all timescales and $\dot{\textup{M}}_{\text{tot,in}}$." (5.1 Kinematic analysis on small scales)
   - fitting: Linear fit weighted by integrated intensity to selected enveloping points of each V- or Straight-shape; no sampler stated  
  > "we apply a linear fit to the observed VGs" (5.1 Kinematic analysis on small scales)
   - validation: Gradients said not to depend on the orientation angle of the PV axis (Alvarez-Gutierrez et al. 2024)  
  > "do not depend on the orientation angle of the spatial axis used in the PV diagrams" (5.1 Kinematic analysis on small scales)
9. **Derive timescales, mass inflow rates, free-fall and depletion times**: t_VG = 1/VG; mass inflow rate = M_tot / t_VG with M_tot summed over the points used for each VG; mean free-fall time of V-shape cores from catalog mass and size; depletion time = total mass / summed V-shape inflow rate  
  > "we estimate their associated timescales as $t_{\text{VG}} = \frac{1}{\text{VG}}$, (cite: Rodrigo21; rodrigo24)" (5.1 Kinematic analysis on small scales); "in order to estimate the mass inflow rate $\dot{\textup{M}}_{\textup{tot,in}}$ following:" (5.1 Kinematic analysis on small scales); "we can estimate the depletion timescales given by $t_{\rm dep}$ = M$_{\rm tot}$/$\dot{\text{M}}_{\text{in},\text{T}}$, obtaining a $t_{\rm dep}\,\sim$ 0.3 Myr." (6.2 G351.77 on small scales)
   - parameter: Total protocluster mass used for t_dep: ~2820 Msun (dust-based)  
  > "Considering the total mass of the protocluster is $\sim$ 2820 $\hbox{\rm M}_{\odot}$" (6.2 G351.77 on small scales)
   - parameter: Mean free-fall time of V-shape cores ~13.6 kyr  
  > "we measure the free-fall time (t$_{ff}$) for each dense core, whose average is $\sim$ 13.6 kyr" (6.2 G351.77 on small scales)
   - assumption: 45 deg average inclination; V-shape gas with no confirmed inflow onto a central mass may overestimate depletion  
  > "We caution that without direct confirmation of inflow onto a central mass (the cores in this case), the depletion timescales associated with the total sample of all V-shapes may be overestimated." (6.2 G351.77 on small scales)
   - fitting: _not stated_
   - validation: Compared with G353.41 values from Alvarez-Gutierrez et al. 2024 (same order of magnitude)  
  > "are similar (within the same order of magnitude) as those measured here for G351.77" (6.1 G351.77 vs G353.41 protoclusters)
10. **Delineate large-scale filaments F1-F4 and interpret inflow**: Emission divided into four regions guided by integrated intensity, S/N and column density maps, with boundaries where integrated intensity drops below 50 K km/s (except F3) and velocity jumps exceed ~0.9 km/s  
  > "we divided the emission into four regions (F1, F2, F3, and F4) defining clear boundaries for each." (5.2 Kinematics analysis on large scales); "The criteria used include integrated intensities drop below 50 K $\rm km\,s^{-1}$ (excluding F3) and velocity differences larger than $\sim$ 0.9 $\rm km\,s^{-1}$" (5.2 Kinematics analysis on large scales)
   - software: PPV diagram web tool
   - fitting: _not stated_
   - validation: _not stated_
11. **Compare with a rotating and infalling sphere toy model**: Model PV diagrams from a sphere with power-law density, infall V_in = -sqrt(2GM/r) and Keplerian rotation V_rot = sqrt(GM/r) (rotation-only, infall-only and combined), overlaid on H2CO and DCN PV diagrams  
  > "we modeled three possible cases for gas spheres: rotation-only, infall-only, and a combination between rotation and infall" (6.5 Multi-tracer modeling); "we utilize a $r_{\rm min} = 0.007$pc and a $r_{\rm max}$ = 0.8 pc, which correspond approximately to the coverage radius of N$_2$H$^+$." (6.5 Multi-tracer modeling)
   - parameter: gamma = 3.1; M = 270 and 2700 Msun giving rho_0 = 3.466 and 34.66 Msun/pc^3  
  > "Also, we define $\gamma$ = 3.1 based on the maximum velocities that the data reach and in how well are the model fits to the data." (6.5 Multi-tracer modeling)
   - assumption: Simple sphere with only infall and Keplerian rotation  
  > "which is simple and only considers two kinematic processes" (6.5 Multi-tracer modeling)
   - fitting: gamma set by eye from maximum velocities and fit quality; no formal fit  
  > "Also, we define $\gamma$ = 3.1 based on the maximum velocities that the data reach and in how well are the model fits to the data." (6.5 Multi-tracer modeling)
   - validation: Model velocity spread ~44 km/s vs ~14 km/s observed (overestimated by factor ~3) but PV shapes similar  
  > "Specifically, the model would predict velocity spreads of order $\Delta$v $\sim$ 44 $\rm km\,s^{-1}$, whereas the spreads that we observe are $\Delta$v $\sim$ 14 $\rm km\,s^{-1}$." (6.5 Multi-tracer modeling)

## Software

- **CASA** 6.2: Imaging, continuum subtraction and feathering of the ALMA-IMF data  
  > "The data imaging process was performed using CASA 6.2 (cite: CASA) along with the ALMA-IMF data pipeline" (2.1 N2H+ data imaging)
- **tclean** : Imaging 12m data and 7m+12m combination (7M12M)  
  > "Subsequently, we applied the same parameter values to combine the 12m-array and 7m-array data with *tclean* to increase the Fourier coverage (7M12M, henceforth)." (2.1 N2H+ data imaging)
- **imcontsub** : Continuum subtraction using line-free channels  
  > "Continuum subtraction was accomplished using the CASA task *imcontsub*." (2.1 N2H+ data imaging)
- **feather** : Combining 7M12M continuum-subtracted data with Total Power data  
  > "As a final step, we employed the CASA task *feather* to combine the 7M12M continuum subtracted data with the TP data to recover the extended line emission." (2.1 N2H+ data imaging)
- **ALMA-IMF data pipeline** : Imaging scripts and parameter settings for the ALMA-IMF data  
  > "The data imaging process was performed using CASA 6.2 (cite: CASA) along with the ALMA-IMF data pipeline" (2.1 N2H+ data imaging)
- **PySpecKit** : Fitting the N2H+ (1-0) hyperfine structure with the n2hp_vtau LTE model (1- and 2-velocity components)  
  > "Here we use the N$_2$H$^+$ (1-0) line model *n2hp_vtau*[^5] from PySpecKit[^6] (cite: PySpecKit11; PySpecKit22) to fit the cube" (3 Line fitting procedure)
- **getsf** : Used by Louvet et al. to build the core catalog employed here (not run in this paper)  
  > "we use the smoothed *getsf* (cite: Menshchikov) core catalog from (cite: Fabien)" (2.2 Other ALMA-IMF data)
- **GExt2D** : Cores detected by GExt2D in the Louvet et al. catalog compared with PV-feature vertices  
  > "between the dense cores candidates and the cores detected by *GExt2D* (cite: Fabien)" (5.1 Kinematic analysis on small scales)
- **PPV diagram web tool (first author's github.io page)** : Creating and inspecting PPV diagrams to separate PV structures  
  > "In addition, we create and analyze PPV diagrams[^8], in order to inspect and distinguish PPV structures." (5 Kinematic analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean rms of final cube over the map | 0.66 | not stated | K | 1 | The mean rms value across the entire map is $\sim$ 0.66 K, whereas the mean value in regions with S/N \> 9 is $\sim$ 0.40 K. |
| Mean rms in regions with S/N > 9 | 0.40 | not stated | K | 1 | The mean rms value across the entire map is $\sim$ 0.66 K, whereas the mean value in regions with S/N \> 9 is $\sim$ 0.40 K. |
| Fraction of 1-component spectra with tau >= 1 (vs tau < 1) | 64% (36%) | not stated | percent | 3 | which correspond to the 64% and 36% of the spectra, respectively |
| Systemic velocity <V_LSR> of G351.77 | -3.843 | 0.001 | km/s | 5 | a careful measurement of the V$_{\text{LSR}}$ of G351.77 where $<$V$_{\rm LSR}>~=~-3.843~\pm~0.001~\rm km\,s^{-1}$ |
| Median centroid velocity uncertainty | 0.034 | not stated | km/s | 4 | the centroid velocity is the one that has the lowest uncertainties with median values of 0.034 $\rm km\,s^{-1}$ |
| Blue/Red cut-off parameter X | 0.025 | not stated | dimensionless | 5 | we obtain a $X=0.025$. |
| Blue-component mean N(N2H+) | 1.49e13 | 0.41e13 | cm^-2 | 6 | 1.49 $\pm$ 0.41 / 1.77 $\pm$ 0.49 |
| Red-component mean N(N2H+) | 1.79e13 | 0.49e13 | cm^-2 | 6 | 1.79 $\pm$ 0.49 / 2.19 $\pm$ 0.61 |
| Total mean N(N2H+) (as printed; not equal to B+R) | 2.28e13 | 0.56e13 | cm^-2 | 6 | 2.28 $\pm$ 0.56 / 3.96 $\pm$ 0.78 |
| N2H+ mass, Blue component | 1.77e-6 | 0.49e-6 | Msun | 6 | 1.49 $\pm$ 0.41 / 1.77 $\pm$ 0.49 |
| N2H+ mass, Red component | 2.19e-6 | 0.61e-6 | Msun | 6 | 1.79 $\pm$ 0.49 / 2.19 $\pm$ 0.61 |
| N2H+ mass, total | 3.96e-6 | 0.78e-6 | Msun | 6 | 2.28 $\pm$ 0.56 / 3.96 $\pm$ 0.78 |
| Representative relative abundance X(N2H+) | 1.66e-10 | 0.46e-10 | dimensionless | 7 | X(N$_2$H$^+$) $=\,(1.66\,\pm\,0.46)\,\times\,10^{-10}$ |
| Total mean H2 column density derived from N2H+ | 1.370e23 | 0.38e23 | cm^-2 | 7 | 1.370 $\pm$ 0.38 / 1657 $\pm$ 326 |
| Total protocluster mass in N2H+ emitting gas | 1657 | 326 | Msun | 7 | 1.370 $\pm$ 0.38 / 1657 $\pm$ 326 |
| Mass in Blue-velocity component | 740 | 205 | Msun | 7 | 0.89 $\pm$ 0.24 / 740 $\pm$ 205 |
| Mass in Red-velocity component | 917 | 253 | Msun | 7 | 1.08 $\pm$ 0.29 / 917 $\pm$ 253 |
| Number of PV features with dense cores | 6 (3 V-shapes, 3 Straight-shapes) | not stated | count | 8 | However, only six dense cores have identifiable kinematic patterns in the PV diagram (3 V-shapes and 3 Straight-shapes |
| PV features without associated dense cores | 16 | not stated | count | 8 | we find 16 PV features both V- and Straight-shapes in the protocluster without associated dense cores |
| Mean t_VG over 17 V-shapes | 43.73 | 0.94 | kyr | 9 | where the average values of $t_{\rm VG}\,=\,$ 43.73 $\pm$ 0.94 kyr |
| Mean mass inflow rate over 17 V-shapes | 5.59e-4 | 0.34e-4 | Msun/yr | 9 | $\dot{\textup{M}}_{\textup{tot,in}}$ $=\,5.59\,\pm$ 0.34) $\times~10^{-4}$ $\hbox{\rm M}_{\odot}\,\rm{yr}^{-1}$ |
| Mean t_VG, V-shapes associated with dense cores | 32.96 | 1.58 | kyr | 9 | we estimate a timescale $\sim$ 32.96 $\pm$ 1.58 kyr |
| Mean t_VG, V-shapes without dense cores | 43.12 | 1.10 | kyr | 9 | we estimate a timescales of $\sim$ 43.12 $\pm$ 1.10 kyr. |
| Mean t_VG, all V-shapes (second quoted value) | 41.33 | 0.95 | kyr | 9 | we estimate a timescale of $\sim$ 41.33 $\pm$ 0.95 kyr. |
| Most prominent V-shape (L19): VG, t_VG, M_tot, mass inflow rate | VG 85.69 km/s/pc; t_VG 11.42 kyr; M_tot 15.36 Msun; Mdot 13.45e-4 Msun/yr | 8.54; 1.13; 3.13; 3.04e-4 | km/s/pc; kyr; Msun; Msun/yr | 9 | 85.69 $\pm$ 8.54 / 11.42 $\pm$ 1.13 / 15.36 $\pm$ 3.13 / 13.45 $\pm$ 3.04 |
| Longest V-shape timescale | 69.17 | 8.95 | kyr | 9 | The longest timescale we measure for a V-shape is 69.17 $\pm$ 8.95 kyr |
| Mean free-fall time of V-shape cores | 13.6 | not stated | kyr | 9 | we measure the free-fall time (t$_{ff}$) for each dense core, whose average is $\sim$ 13.6 kyr |
| Total mass inflow rate summed over V-shapes | 9.84e-3 | 0.63e-3 | Msun/yr | 9 | The total mass accretion rate measured is $\dot{\text{M}}_{\text{in},\text{T}}\,=\,(9.84\,\pm\,0.63)\,\times\,10^{-3}$ $\hbox{\rm M}_{\odot}\,\rm{yr}^{-1}$. |
| Depletion timescale of V-shape gas | ~0.3 | not stated | Myr | 9 | obtaining a $t_{\rm dep}\,\sim$ 0.3 Myr. |
| Velocity separation of the two large-scale N2H+ structures | ~2 | not stated | km/s | 10 | reveals two distinct large-scale structures, separated by $\sim$ 2 $\rm km\,s^{-1}$ |
| Angle of large-scale velocity gradient to Mother Filament direction | ~83 | not stated | deg | 5 | almost perpendicular ($\sim$ 83 $^{\circ}$) to the direction in which the molecular cloud filament that hosts the protocluster extends |
| Model velocity spread vs observed spread | model ~44 km/s vs observed ~14 km/s (factor ~3 overestimate) | not stated | km/s | 11 | Specifically, the model would predict velocity spreads of order $\Delta$v $\sim$ 44 $\rm km\,s^{-1}$, whereas the spreads that we observe are $\Delta$v $\sim$ 14 $\rm km\,s^{-1}$. |

## Qualitative findings

- Two large-scale velocity structures, one dominated by the Blue and one by the Red component, are spatially and kinematically distinct  
  > "we realize that these large-scale structures are not only separated in velocity but also by spatial position" (5.2 Kinematics analysis on large scales)
- Filament F1 appears to inflow toward the core hosting the most prominent V-shape  
  > "we show that the F1 filamentary structure seems to be inflowing toward a dense core, where we observe the most prominent V-shape in the PV diagram" (6.3 G351.77 on large scales)
- Hot cores may explain the lack of N2H+ emission in the protocluster center  
  > "These hot cores may explain the lack of N$_2$H$^+$ (1-0) emission in the center of the protocluster" (1 Introduction)
- SiO outflows lie at the edges of the N2H+ emission and are not tied to PV structures  
  > "these outflows are located at the edges of the N$_2$H$^+$ emission rather than the internal regions of the filaments" (6.3 G351.77 on large scales)
- Multiple velocity components exist over a significant number of spectra  
  > "multiple velocity components exist over a significant number of spectra" (3 Line fitting procedure)

## Claim tuples

- H: Do V- and Straight-shaped PV features near dense cores trace inflowing gas along filaments? | E: PV diagrams of N2H+ centroid velocities around catalog cores within 6x core size, linear fits to VGs | R: 3 V-shapes and 3 Straight-shapes near cores, plus further features without cores; VG, t_VG and Mdot tabulated | F: V-shapes describe inflow in filaments with cores near the vertex; Straight-shapes describe inflowing filaments with cores following the gas | **partially**
- H: Are V-shape properties in G351.77 similar to those in G353.41 and generic to forming protoclusters? | E: Mean t_VG and Mdot of 17 V-shapes compared with G353.41 results | R: Mean t_VG 43.73 kyr and Mdot 5.59e-4 Msun/yr, same order of magnitude as G353.41 | F: V-shapes are generic kinematic features of forming protoclusters | **supported**
- H: How fast is the dense gas depleted by inflow onto cores? | E: Sum of V-shape mass inflow rates compared with total protocluster mass | R: Total Mdot (9.84 +/- 0.63)e-3 Msun/yr giving t_dep ~0.3 Myr | F: Fast depletion implies fast cluster formation and/or continuous feeding from larger scales | **partially**
- H: Is the protocluster fed by the Mother Filament through large-scale filaments? | E: PV/PPV analysis of large-scale structures F1-F4 | R: F1 converges on the most prominent V-shape core and connects through F4 to the Mother Filament | F: Inflow from the Mother Filament toward the protocluster is suggested | **partially**
- H: Does a combined infall and rotation sphere reproduce the PV structure of H2CO, DCN and N2H+? | E: Toy model with infall and Keplerian rotation, compared with PV diagrams of H2CO, DCN and N2H+ | R: Rotation-only fits the central H2CO and DCN shapes best; model velocities exceed observed ones by a factor ~3 | F: Qualitative consistency with slow contraction plus inner rotation, but velocities not matched | **partially**
- H: What evolutionary stage is G351.77 in relative to G353.41? | E: Comparison of numbers of cores, V-shapes and timescales with G353.41 and with the Global Hierarchical Collapse picture | R: More V-shapes, fewer cores and shorter timescales than G353.41 | F: G351.77 is still in an early evolutionary stage and younger than G353.41 | **partially**

## Reasoning

- Why this data: N2H+ (1-0) probes cold, dense extended gas outside compact cores  
  > "a critical yet under-exploited aspect in the above studies is pinpointing the properties of the cold, dense extended gas outside the relatively compact cores." (1 Introduction); "These characteristics make N$_2$H$^+$ (1-0) a reliable tracer for dense and cold gas." (1 Introduction)
- Why this method: PV diagrams give velocity gradients, timescales and mass inflow rates; 2-component fits are needed because 1 component cannot describe the kinematics  
  > "Additionally, PV diagrams provide a valuable tool for characterizing velocity gradients, measuring timescales, and estimating mass inflow rates at small scales" (1 Introduction); "Consequently, a 1-velocity-component fit is not sufficient to describe the global kinematics of the data." (3.2 Two-velocity-component fit)
- Alternative: Free Tex fits for tau < 1 spectra rejected because Tex and tau are degenerate in a single transition; constant Tex used instead  
  > "This problem arises due to the intrinsic degeneracy when fitting a single transition, which makes it impossible to measure both T$_{\rm ex}$ and $\tau$ from the same transition when $\tau~<~1$." (3.1 One-velocity-component fit)
- Alternative: pblimit 0.05 rejected for 7M12M because of edge artifacts; 0.2 adopted  
  > "by increasing the pblimit value from 0.05 to 0.2 for this product" (2.1 N2H+ data imaging)
- Alternative: Higher-resolution (2.5'') final N(H2) map not used; 6'' intermediate product used to reduce uncertainties  
  > "we use this intermediate product in order to reduce the uncertainties of our estimations that could be produced by the combination of the data of H$_2$ and from our fits." (2.2 Other ALMA-IMF data)
- Alternative: Outflow origin of V-shapes (suggested by Henshaw et al.) not supported by positions of cataloged outflows  
  > "we do not observe agreement between the position of outflow catalogs (cite: towner) and the position of cores associated with V-shapes in PV diagrams" (5.1 Kinematic analysis on small scales)
- How they decided it was enough: S/N > 9 chosen from synthetic fitting experiments; fit guesses iterated until averages stop changing  
  > "This approach stems from our experimental findings, which reveal that spectra with a S/N $<$ 9 are inadequately fitted, yielding high uncertainties in the returned parameters" (3 Line fitting procedure); "This is repeated until no variations are observed in the averages obtained for each parameter compared to previous fits." (3.1 One-velocity-component fit)
- Limitation (authors): Inclination of structures cannot be measured; 45 deg assumed  
  > "For our purposes, we can not measure the inclination of any given structure." (5.1 Kinematic analysis on small scales)
- Limitation (authors): Total N2H+-derived mass is a lower limit  
  > "which we consider a lower limit since this corresponds to the mass derived only from the regions with N$_2$H$^+$ emission" (4.2 N2H+ relative abundance)
- Limitation (authors): Blue/Red velocity separation is somewhat arbitrary  
  > "To make this somewhat arbitrary but necessary velocity separation" (3.4 Blue and Red velocity component)
- Limitation (authors): 7M12M combination produces edge artifacts  
  > "This combination produces artifacts such as peaks and bowls of intensity around the edges." (2.1 N2H+ data imaging)
- Limitation (authors): Hot cores sit where N2H+ S/N < 9, limiting kinematic information  
  > "hot cores are located in regions with N$_2$H$^+$ emission with S/N $<$ 9, limiting the kinematic information available from them" (6.3 G351.77 on large scales)
- Limitation (authors): Toy model is simple and only includes infall and rotation  
  > "which is simple and only considers two kinematic processes" (6.5 Multi-tracer modeling)
- Caveat (inferred, ours): Table 2 total <N(N2H+)> (2.28e13) does not equal blue + red (1.49e13 + 1.79e13) although the mass column does add up
- Caveat (inferred, ours): Mean t_VG for all V-shapes is given as 43.73 kyr in Sect. 5.1 and 41.33 kyr in Sect. 6.1; H2CO is (3-2) in Sect. 2.2 but (2-1) in Sect. 6.5; G354.41 and G351.41 typos for G353.41
- Caveat (inferred, ours): Mass inflow rates use total mass from one global X(N2H+) applied everywhere; abundance varies by two decades pixel to pixel, so Mdot and t_dep carry large systematic error
- Caveat (inferred, ours): Total mass quoted as 1660, 2820, 2700 and 2720 Msun in different places, and the toy model uses 270 Msun against 2700 Msun measured
- Caveat (inferred, ours): V-shape/Straight-shape identification and VG point selection is subjective with no reproducible criterion or completeness test
- Caveat (inferred, ours): Depletion time sums V-shapes that may overlap along the line of sight and assumes all gas flows onto cores; vertex-as-hidden-core claim untested
- Caveat (inferred, ours): Core-less V-shapes interpreted as undetected cores without any check against deeper continuum data

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: ALMA-IMF imaging pipeline repository (https://github.com/ALMA-IMF/reduction) and imaging_parameters.py  
  > "https://github.com/ALMA-IMF/reduction" (Footnote 2); "https://github.com/ALMA-IMF/reduction/blob/master/reduction/imaging_parameters.py" (Footnote 4)
- Code: PPV diagram web page by the first author  
  > "https://nicolas11399.github.io/Nicolas.Sandoval-Garrido_PVV.github.io/" (Footnote 8)
- Missing: Dust-based 6'' N(H2) intermediate map (private communication) needed for X(N2H+) and all masses
- Missing: Imaging parameter values (only in external repo file) and line-free channel choices
- Missing: Core catalog tables (Louvet et al. 2024) and DCN/H2CO maps from companion papers
- Missing: Fit and PV analysis code, VG point selection and the toy model code
- Missing: Explicit calibration/product version of ALMA-IMF data and which projects feed the cube
- Data volume (inferred): Raw MS for three ALMA projects likely hundreds of GB; ALMA-IMF delivered N2H+ 12m/7m/TP cubes for one field likely a few GB
- Score (inferred): 3/5, Project codes, line, software and fit guesses/limits are given and the pipeline is public, but imaging settings sit in an external file, the N(H2) map is private, and PV feature selection is subjective.
- Rediscovery candidate: no, Spectral fitting is replicable from the cube, but X(N2H+), masses, Mdot and depletion time depend on a private N(H2) map and subjective V-shape selection, so the full recipe cannot be redone.

## Links

- Method: Motte et al. 2022 (cite: motte22) (ALMA-IMF Large Program design, data and source of H2CO maps and classification)
- Method: Alvarez-Gutierrez et al. 2024 (cite: rodrigo24) (PV V-shape analysis of N2H+ in G353.41 on which the VG, t_VG and Mdot method is based)
- Method: Alvarez-Gutierrez et al. 2021 (cite: Rodrigo21) (PV velocity-gradient timescale method)
- Method: Gonzalez Lobos & Stutz 2019 (cite: Valentina19); Redaelli et al. 2019 (cite: Elena) (PySpecKit N2H+ cube fitting and column density approach)
- Method: Ginsburg et al. 2022a (cite: adam22) (ALMA-IMF continuum images underlying the core catalog)
- Method: Men'shchikov 2021 (cite: Menshchikov) (getsf source extraction used for the core catalog)
- Method: Caselli et al. 2002 (cite: Caselli1; Caselli2) (Constant Tex for low opacity and optically thick column density expression)
- Companion: Louvet et al. 2024 (cite: Fabien) (ALMA-IMF core catalog used for core positions, masses and sizes)
- Companion: Cunningham et al. 2023 (cite: Nichol) (DCN (3-2) kinematics of ALMA-IMF cores)
- Companion: Dell'Ova et al. 2024 (cite: Pierre) (H2 column density maps)
- Companion: Reyes-Reyes et al. 2024 (cite: Simon) (Mother Filament mass, distance and star formation rate)
- Companion: Towner et al. 2023 (cite: towner) (SiO outflow catalog)
- Companion: Bonfand et al. 2024 (cite: Melisse) (Hot cores in G351.77)
- Related: ALMA-IMF Large Program (2017.1.01355.L)
- Related: ALMA projects 2013.1.01365.S and 2015.1.01273.S
- Related: SOFIA/HAWC+ and APEX SABOCA/LABOCA maps used for N(H2)

## Checks

```json
{
 "quotes": 191,
 "quotes_ok": 191,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 32,
 "numeric_problems": 0,
 "fill": {
  "facts": 143,
  "stated": 107,
  "rate": 0.748
 },
 "evidence_ok": true
}
```
