# Constraining the stellar masses and origin of the protostellar VLA 1623 system

`2024A&A...687A.308S` | Astronomy and Astrophysics 2024 | first author: Sadavoy, Sarah I. | arXiv: 2406.12984 | DOI: 10.1051/0004-6361/202348859

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Constrain the stellar masses of the VLA 1623 components by Keplerian disk modelling of C17O (3-2), and use them to test the origin of the system (ejection, chance alignment, in situ formation) and its stability  
  > "We used these data and radiative transfer models of rotating disks to constrain the stellar masses for the stellar components in VLA 1623." (Introduction); "Constraining the stellar masses is an important step towards examining the origins of the VLA 1623 system." (Introduction)
- Target **VLA 1623 (components A, B, W)**: coordinates phase centre 16:26:26.35 -24:24:30.55 (between VLA 1623A and VLA 1623B)  
  > "The data phase centre was at 16:26:26.35 -24:24:30.55, between VLA 1623A and VLA 1623B" (Data); "star-forming region at 140 pc (cite: OrtizLeon18)" (Introduction); z/distance 140 pc  
  > "The data phase centre was at 16:26:26.35 -24:24:30.55, between VLA 1623A and VLA 1623B" (Data); "star-forming region at 140 pc (cite: OrtizLeon18)" (Introduction); distance from (cite: OrtizLeon18)  
  > "The data phase centre was at 16:26:26.35 -24:24:30.55, between VLA 1623A and VLA 1623B" (Data); "star-forming region at 140 pc (cite: OrtizLeon18)" (Introduction)

## Data provenance

- ALMA projects: 2018.1.01089.S
- bands: Band 7  
  > "ALMA observed VLA 1623 in Band 7 on 20 and 22 April 2019 for project 2018.1.01089.S in the C-4 configuration" (Data)
- frequencies and spectral setup: Spectral windows on C17O (3-2) 337.061 GHz, H13CO+ (4-3) 346.998 GHz, SO2 (8_2,6-7_4,4) 334.673 GHz, H13CN (4-3) and SO2 (13_2,12-12_1,11) at 345.34 GHz; plus one continuum window  
  > "The observations were set up with spectral windows on C$^{17}$O (3 – 2) at 337.061 GHz, H$^{13}$CO$^+$ (4 – 3) at 346.998 GHz, SO$_2$ ($8_{2,6}-7_{4,4}$) at 334.673 GHz" (Data); "H$^{13}$CN (4 – 3) and SO$_2$ ($13_{2,12}-12_{1,11}$) at 345.34 GHz" (Data)
- continuum bandwidth: one continuum window, centre 348.2227 GHz, bandwidth 1.85 GHz  
  > "There was also one continuum window with a central frequency of 348.2227 GHz and bandwidth of 1.85 GHz." (Data)
- arrays: _not stated_
- configurations: C-4  
  > "ALMA observed VLA 1623 in Band 7 on 20 and 22 April 2019 for project 2018.1.01089.S in the C-4 configuration with baselines of 15 m – 740 m." (Data)
- baselines: 15 m – 740 m  
  > "ALMA observed VLA 1623 in Band 7 on 20 and 22 April 2019 for project 2018.1.01089.S in the C-4 configuration with baselines of 15 m – 740 m." (Data)
- angular resolution: continuum beam 0.3'' x 0.24'' (robust = -0.5)  
  > "for a beam of $0.3\ensuremath{''} \times 0.24\ensuremath{''}$ with Briggs weighting and $\mbox{\texttt{robust}}=-0.5$" (Data)
- max recoverable scale: 3.8'' (5th percentile baseline)  
  > "The maximum recoverable scale for the data is 3.8$''$ using the 5th percentile baseline." (Data)
- sensitivity: 95 uJy/beam in the final continuum map at 341.8541 GHz  
  > "have a sensitivity of 95 $\mu$Jy beam$^{-1}$ at 341.8541 GHz" (Data)
- time on source: 52.74 minutes in total  
  > "The time on source was 52.74 minutes in total." (Data)
- observing dates: 20 and 22 April 2019  
  > "ALMA observed VLA 1623 in Band 7 on 20 and 22 April 2019" (Data)
- pi or archival as stated: described as new observations (not stated whether PI or archival)  
  > "We present new ALMA molecular line observations of the VLA 1623 system." (Conclusions)
- Line: C17O 3 – 2 (337.061 GHz)
- Line: H13CO+ 4 – 3 (346.998 GHz)
- Line: SO2 8_2,6 - 7_4,4 (334.673 GHz)
- Line: H13CN 4 – 3 (345.34 GHz (spectral window))
- Line: SO2 13_2,12 - 12_1,11 (345.34 GHz (spectral window))
- External data: Distance to VLA 1623 of 140 pc  
  > "star-forming region at 140 pc (cite: OrtizLeon18)" (Introduction) [from (cite: OrtizLeon18)]
- External data: c-C3H2 contours at 217.8 GHz compared with C17O integrated intensity  
  > "Figure [3](#cavitywall) compares the C$^{17}$O integrated intensity data with contours of c-C$_3$H$_2$ at 217.8 GHz from (cite: Murillo18gas)." (Results) [from (cite: Murillo18gas)]
- External data: Positions of VLA 1623B and VLA 1623W at earlier epochs, used for proper motions  
  > "We took positions of VLA 1623B and VLA 1623W from the literature" (Proper motion and closest approach) [from Sadavoy19, Harris18, Murillo13, Maury12, Chen13 (as listed in the appendix table)]
- External data: Companion probability P(c) = 0.2 (separations <~1000 au)  
  > "We also used $P(c) = 0.2$ from (cite: Tobin22)" (Discussion) [from (cite: Tobin22)]
- External data: Gaia-corrected YSO catalogue used for the 11th-nearest-neighbour surface density  
  > "we calculated the 11th nearest neighbour at the position of VLA 1623 from the *Gaia*-corrected YSO catalogue of (cite: Grasser21)" (Discussion) [from (cite: Grasser21)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: flux/bandpass J1924-2914 (20 April) and J1517-2422 (22 April); phase calibrator J1650-2943  
  > "The phase calibrator was J1650-2943, and the flux/bandpass calibrator was J1924-2914 (20 April) and J1517-2422 (22 April)." (Data)
- flux scale uncertainty: _not stated_
- self calibration: 3 rounds phase-only (3 min, 60.6 s, 30.3 s) then 2 rounds amplitude+phase (3 min, 90.9 s); clean depths 0.92, 0.45, 0.20, 0.17, 0.13 mJy/beam; applied to continuum and the three line windows using line-free channels  
  > "We applied self-calibration to the continuum window and the three line windows using line-free channels." (Data); "We used solution intervals of 3 min, 60.6 s, and 30.3 s for the phase-only self-calibration and 3 min and 90.9 s for the amplitude and phase self-calibration." (Data); "The clean depths for the five rounds were 0.92, 0.45, 0.20, 0.17, and 0.13 mJy beam$^{-1}$." (Data)

### Imaging

- task: tclean, run interactively for the line cubes  
  > "The final line cubes are made using `tclean` interactively with $\mbox{\texttt{robust}}=0.5$." (Data)
- deconvolver: _not stated_
- weighting robust: continuum Briggs robust = -0.5; line cubes robust = 0.5  
  > "with Briggs weighting and $\mbox{\texttt{robust}}=-0.5$" (Data); "The final line cubes are made using `tclean` interactively with $\mbox{\texttt{robust}}=0.5$." (Data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: fit order 1  
  > "We applied continuum subtraction using a fit order of 1." (Data)
- line free channels: _not stated_
- primary beam correction: Moment 0 maps not primary-beam-corrected (for clarity)  
  > "For the sake of clarity, the Moment 0 maps have not been primary-beam-corrected." (Results)
- array combination: _not stated_
- smoothing: spectrally smoothed to 0.4 km/s channels for Moment 1 maps  
  > "we spectrally smoothed the data to 0.4 km s$^{-1}$ channels" (Circumstellar disks)
- final beam: continuum 0.3'' x 0.24''  
  > "for a beam of $0.3\ensuremath{''} \times 0.24\ensuremath{''}$ with Briggs weighting" (Data)
- final rms: 95 uJy/beam (continuum, 341.8541 GHz)  
  > "have a sensitivity of 95 $\mu$Jy beam$^{-1}$ at 341.8541 GHz" (Data)

### Inherited from earlier work

- pdspy disk-model technique (details of how the code works)  
  > "Full details of how the code works can be found in (cite: SheehanEisner18), but we describe the technique briefly here" (Modelling) [from (cite: SheehanEisner18)]
- Fitting Keplerian disk models to line data directly in the uv plane with pdspy  
  > "which fits Keplerian rotating disk models to spectral line datasets directly in the $uv$ plane (cite: Sheehan19)" (Modelling) [from (cite: Sheehan19)]
- C17O/CO abundance factor 1/2240 and CO abundance 1e-4 relative to H2  
  > "assuming a constant C$^{17}$O abundance with a factor of 1/2240 relative to CO and a fixed CO abundance of $10^{-4}$ relative to molecular hydrogen (cite: Czekala15)" (Modelling) [from (cite: Czekala15)]
- Position-angle convention (angular momentum vector, east of north)  
  > "the position angle is defined based on the direction of the angular momentum vector of the disk, east of north, following (cite: Czekala15)" (Modelling) [from (cite: Czekala15)]
- Bayesian companion-probability method  
  > "Following (cite: Tobin22), we estimated the probability that VLA 1623W is a companion source using Bayes theorem" (Chance alignment) [from (cite: Tobin22)]
- Position uncertainties from map resolution scaled by peak S/N  
  > "We follow (cite: Sadavoy18b) in using the map resolution scaled by the source peak S/N to estimate the position uncertainties." (Proper motion and closest approach) [from (cite: Sadavoy18b)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether the standard pipeline or manual calibration was used
- Which channels are line-free for self-calibration and continuum subtraction
- tclean settings: image size, cell size, deconvolver, masks, thresholds, niter, number of channels per line cube
- Gain-solution details for self-calibration (combine, spw mapping, minimum SNR)
- Thresholds in Moment 0 and dust continuum used to mask the Moment 1 maps
- pdspy version, prior ranges for all free parameters, likelihood definition, and dynesty settings (live points, stopping criterion)
- Channel restriction used for the VLA 1623W fit (only uv cut is given)
- How CO hyperfine structure of C17O and the line width/channel handling are treated in the model
- Fit details of the proper-motion least-squares and Monte Carlo sampling beyond those listed

## Analysis recipe

1. **Self-calibrate and image the continuum**: Three rounds of phase-only and two rounds of amplitude+phase self-calibration on the continuum and line windows using line-free channels, then continuum imaging with Briggs weighting  
  > "We used three rounds of phase-only self-calibration, starting with a shallow clean and a long solution interval and progressing to deeper cleans with shorter solution intervals." (Data); "we also used two rounds of phase and amplitude self-calibration using long integration times" (Data)
   - parameter: Solution intervals 3 min, 60.6 s, 30.3 s (phase-only); 3 min, 90.9 s (amp+phase); clean depths 0.92, 0.45, 0.20, 0.17, 0.13 mJy/beam  
  > "We used solution intervals of 3 min, 60.6 s, and 30.3 s for the phase-only self-calibration and 3 min and 90.9 s for the amplitude and phase self-calibration." (Data); "The clean depths for the five rounds were 0.92, 0.45, 0.20, 0.17, and 0.13 mJy beam$^{-1}$." (Data)
   - parameter: Continuum robust = -0.5  
  > "with Briggs weighting and $\mbox{\texttt{robust}}=-0.5$" (Data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Make continuum-subtracted line cubes**: Apply self-cal gain solutions to line windows, continuum-subtract with fit order 1, tclean interactively with robust 0.5  
  > "The self-calibration gain solutions were applied to each of the line spectral windows." (Data); "We applied continuum subtraction using a fit order of 1." (Data); "The final line cubes are made using `tclean` interactively with $\mbox{\texttt{robust}}=0.5$." (Data)
   - software: tclean
   - parameter: Channel widths 0.106-0.219 km/s; per-channel rms about 3 mJy/beam (Table of lines)  
  > "Table [\[line_info\]](#line_info) gives the rest frequency, channel width, sensitivity per channel, and beam size for each detected line." (Data)
   - fitting: _not stated_
   - validation: _not stated_
3. **Moment maps and velocity gradients**: Moment 0 maps over listed velocity ranges; Moment 1 maps with immoments after smoothing to 0.4 km/s, masked with Moment 0 and continuum thresholds  
  > "we calculated the Moment 1 velocities using `immoments` in CASA with strict channel selections to avoid lower velocity gas that could be confused with emission outside of the disks" (Circumstellar disks); "we masked each map using thresholds in Moment 0 and dust continuum to isolate the Moment 1 data for each disk" (Circumstellar disks)
   - software: CASA
   - parameter: Moment 1 velocity ranges for VLA 1623A: 0.8-3.2 and 5.6-7.2 km/s  
  > "The velocity ranges used were $0.8-3.2$ km s$^{-1}$ and $5.6-7.2$ km s$^{-1}$ for VLA 1623A" (Circumstellar disks)
   - fitting: _not stated_
   - validation: Gradient for VLA 1623W compared with C18O (2-1) gradient from literature  
  > "This gradient agrees well with the C$^{18}$O (2 – 1) gradient presented by (cite: Mercimek23)." (Circumstellar disks)
4. **Fit Keplerian disk models to C17O in the uv plane**: pdspy 2D axisymmetric disk models, RADMC-3D ray tracing, Fourier transformed with galario, fit separately to VLA 1623A, B and W in the uv plane  
  > "which fits Keplerian rotating disk models to spectral line datasets directly in the $uv$ plane (cite: Sheehan19)" (Modelling); "`pdspy` then uses the radiative transfer modelling code `RADMC-3D` and ray tracing to generate synthetic channel maps of the model disk" (Modelling)
   - software: pdspy, RADMC-3D, galario, dynesty
   - parameter: Free parameters include M*, M_disk, R_disk, gamma, T0, q, a_turb, i, p.a., v_sys, x0, y0 (R_in free for A, fixed at 0.1 au for B and W)  
  > "The model parameter values as well as the source system velocity, $v_{sys}$, and location in the field ($x_0$, $y_0$) are optimized to the observations." (Modelling); "For VLA 1623B and VLA 1623W, we fixed $R_{in}$, the inner radius where the disk is truncated, to 0.1 au." (Modelling)
   - parameter: Strict priors on source position so each source is fit separately  
  > "we provided `pdspy` with relatively strict priors on the location of the source" (Modelling)
   - parameter: Channel cuts: exclude 3.25-5.5 km/s for A and -2.5 to 6.75 km/s for B  
  > "For the channel restrictions, we excluded velocities between 3.25 and 5.5 km s$^{-1}$ from the fit to A and between -2.5 and 6.75 km s$^{-1}$ from the fit to B." (Modelling)
   - parameter: uv cuts: exclude uv < 100 klambda for B and < 200 klambda for W  
  > "For the $uv$ restriction, we excluded baselines with $uv <100$ k$\lambda$ ($\gtrsim2\ensuremath{''}$) for B and $uv <200$ k$\lambda$ ($\gtrsim1\ensuremath{''}$) for W." (Modelling)
   - assumption: Surface density follows a power law; temperature power law in radius, vertically isothermal  
  > "The surface density is described by a power-law function" (Modelling); "and that the disk is vertically isothermal" (Modelling)
   - assumption: Constant C17O abundance (1/2240 of CO), CO abundance 1e-4 relative to H2, no dust in the line model  
  > "assuming a constant C$^{17}$O abundance with a factor of 1/2240 relative to CO and a fixed CO abundance of $10^{-4}$ relative to molecular hydrogen (cite: Czekala15)" (Modelling)
   - assumption: C17O emission solely traces rotationally supported disks; envelope and streamer contributions negligible  
  > "we assumed that the C$^{17}$O (3 – 2) emission solely traces the rotationally supported disks and that any potential contributions from the surrounding envelope or gas streamers are negligible" (Results)
   - fitting: dynesty nested sampling; best fit is the maximum-likelihood model from the posterior; priors beyond source position not stated  
  > "`dynesty` uses nested sampling to integrate the likelihood function and calculate the Bayesian evidence and the posteriors for each parameter." (Modelling); "The best-fit values are determined from the maximum likelihood models from the posterior" (Modelling)
   - validation: Residual channel maps show little emission above 5 sigma near the target disk; PV diagrams compared with Keplerian curves  
  > "We find that the models fit the data well, with little or no contours above the $5\sigma$ level appearing in the residual channel maps associated with the target disk." (Modelling)
5. **Derive parameter uncertainties**: 68% range of posterior samples, plus 10% added in quadrature to most parameters  
  > "the uncertainties are calculated as the range around the best-fit values that include 68% of the posterior samples" (Modelling); "We also added a 10% uncertainty in quadrature to most parameters" (Modelling)
   - parameter: 10% not added to x0, y0, i, p.a., v_sys  
  > "An additional 10% uncertainty has been added in quadrature to the best-fit values for all parameters except" (Table 1)
   - assumption: The 10% term represents systematic errors such as flux calibration and source distance  
  > "to represent additional uncertainties on those values imparted by systematic errors in, for example, flux calibration and source distance" (Modelling)
   - fitting: _not stated_
   - validation: _not stated_
6. **Compare disk masses with stability thresholds and ODISEA**: Disk-to-star mass ratio compared with the ~30% fragmentation threshold; dust mass of VLA 1623W from gas-to-dust ratio compared with ODISEA  
  > "we used the disk-to-star mass ratio to assess the gravitational stability of the circumstellar and circumbinary disks" (VLA 1623 stability); "assuming a gas-to-dust mass ratio of 100" (In situ formation)
   - assumption: Gas-to-dust mass ratio of 100  
  > "assuming a gas-to-dust mass ratio of 100" (In situ formation)
   - fitting: _not stated_
   - validation: Ratio threshold checked against the L1448 IRS3 system  
  > "This cutoff matches what is seen in the L1448 IRS3 system" (VLA 1623 stability)
7. **Proper motions and closest approach of VLA 1623W and B**: Linear least-squares proper motion from multi-epoch positions with 15 mas pointing error added in quadrature; constant velocities extrapolated back; Monte Carlo error analysis  
  > "before fitting for the proper motion using linear least squares" (Proper motion and closest approach); "We combined the above proper motions for VLA 1623W and VLA 1623B to determine when the two objects had their closest approach in the plane of the sky, assuming constant velocities." (Proper motion and closest approach)
   - parameter: Minimum position error 5 mas for high S/N data; 15 mas pointing error added in quadrature  
  > "both sources had peak S/N $>100$, so we adopted a minimum error of 5 mas" (Proper motion and closest approach); "we can expect a 1 $\sigma$ pointing accuracy of $\sim 15$ mas" (Proper motion and closest approach)
   - parameter: 10000 Monte Carlo draws; uncertainties treated as the FWHM of a Gaussian  
  > "We assumed that the proper motion uncertainties given above correspond to the FWHM of a Gaussian distribution and then draw 10000 random values to add to the nominal proper motions." (Proper motion and closest approach)
   - assumption: New measurement and the Maury12 point excluded from the proper-motion fit  
  > "We excluded the data point from (cite: Maury12), because they did not provide sufficient precision for a proper motion analysis (cite: Sadavoy18b)." (Proper motion and closest approach)
   - fitting: Linear least squares  
  > "before fitting for the proper motion using linear least squares" (Proper motion and closest approach)
   - validation: Monte Carlo results compared with the nominal best-fit proper-motion case  
  > "These results are in good agreement with the nominal case using the best-fit proper motions (without the errors)." (Proper motion and closest approach)
8. **Probability that VLA 1623W / VLA 1623B are companions**: Bayes theorem with detection probabilities and local YSO surface density (11th nearest neighbour)  
  > "Following (cite: Tobin22), we estimated the probability that VLA 1623W is a companion source using Bayes theorem" (Chance alignment)
   - parameter: P(d|c) = 0.75; P(c) = 0.2 (W), 0.14 (B, separations <500 au); r = 10'' (W), 1.5'' (B)  
  > "We adopted $P(d|c) = 0.75$, similar to (cite: Tobin22)." (Chance alignment); "We used $r = 10\ensuremath{''}$ for the area." (Chance alignment); "assuming $P(c) = 0.14$ for separations $<500$ au (cite: Tobin22) and a distance of $r = 1.5\ensuremath{''}$" (VLA 1623 stability)
   - fitting: _not stated_
   - validation: _not stated_
9. **Test whether VLA 1623W is gravitationally bound**: Compare potential energy (star and disk masses, projected separation) with kinetic energy from relative 3D motion  
  > "For simplicity, we ignored any contributions from the surrounding dense core, and calculated the potential energy between VLA 1623W and VLA 1623A/B using the star and disk masses in" (VLA 1623 stability)
   - parameter: Projected separation 10''; system velocities 3 km/s for A/B and 1.75 km/s for W  
  > "assuming 3 km s$^{-1}$ for A/B and 1.75 km s$^{-1}$ for W" (VLA 1623 stability)
   - assumption: Surrounding dense core ignored; gravitational energy is an upper limit because only projected separation is known  
  > "the calculated gravitational energy is an upper limit, since we only have a projected separation" (VLA 1623 stability)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Moment 1 maps with immoments (self-calibration and imaging software not named)  
  > "we calculated the Moment 1 velocities using `immoments` in CASA" (Circumstellar disks)
- **tclean** : Making the final line cubes interactively  
  > "The final line cubes are made using `tclean` interactively with $\mbox{\texttt{robust}}=0.5$." (Data)
- **pdspy** : Fitting Keplerian rotating disk models to C17O in the uv plane  
  > "We modelled the C$^{17}$O (3 – 2) data for VLA 1623A, VLA 1623B and VLA 1623W using the `pdspy` code" (Modelling)
- **RADMC-3D** : Radiative transfer and ray tracing to make synthetic channel maps  
  > "`pdspy` then uses the radiative transfer modelling code `RADMC-3D` and ray tracing to generate synthetic channel maps of the model disk" (Modelling)
- **galario** : Fourier transforming synthetic channel maps into the uv plane  
  > "Fourier transforms the synthetic channel maps into the $uv$ plane using the `galario` code (cite: Tazzari18)" (Modelling)
- **dynesty** : Nested sampling to find best-fit values and posteriors  
  > "we use the `dynesty` code (cite: Speagle20) instead of a Monte Carlo Markov chain (MCMC) to find the best-fit values." (Modelling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum sensitivity at 341.8541 GHz | 95 | not stated | uJy/beam | 1 | have a sensitivity of 95 $\mu$Jy beam$^{-1}$ at 341.8541 GHz |
| Maximum recoverable scale | 3.8 | not stated | arcsec | 1 | The maximum recoverable scale for the data is 3.8$''$ using the 5th percentile baseline. |
| Stellar mass VLA 1623A (Aa+Ab combined) | 0.27 | +0.03/-0.03 | Msun | 4 | a combined stellar mass of $M_\star = 0.27 \pm 0.03$ for VLA 1623A; We measure stellar masses of 0.27 M$_{\odot}$, 1.9 M$_{\odot}$, and 0.64 M$_{\odot}$ for VLA 1623A (Aa and Ab combined), VLA 1623B, and VLA 1623W, respectively. |
| Stellar mass VLA 1623B | 1.9 | +0.3/-0.2 | Msun | 4 | $M_\star = 1.9^{+0.3}_{-0.2}$ M$_{\odot}$ for VLA 1623B |
| Stellar mass VLA 1623W | 0.64 | +0.06/-0.06 | Msun | 4 | $M_\star = 0.64 \pm 0.06$ M$_{\odot}$ for VLA 1623W |
| Disk radius R_disk of VLA 1623A / B / W | 316 / 43 / 108 | +32/-32 ; +5/-5 ; +11/-11 | au | 4 | $R_{disk}$ (au) / $316^{+32}_{-32}$ / $43^{+5}_{-5}$ / $108^{+11}_{-11}$ |
| Inclination of VLA 1623A / B / W | 58.9 / 91 / 74.8 | +0.6/-0.3 ; +16/-2 ; +0.5/-0.5 | deg | 4 | $i$ ($^{\circ}$) / $58.9^{+0.6}_{-0.3}$ / $91^{+16}_{-2}$ / $74.8^{+0.5}_{-0.5}$ |
| Disk mass M_disk (gas+dust) of VLA 1623A / B / W | 54 / >1 / 1.7 (x1e-3) | +5/-5 ; not stated ; +0.2/-0.2 | 1e-3 Msun | 4 | $M_{disk}$ ($10^{-3}$ M$_{\odot}$) / $54^{+5}_{-5}$ / $>1$ / $1.7^{+0.2}_{-0.2}$ |
| Equivalent disk dust mass of VLA 1623W | 6 | not stated | Mearth | 6 | Table [1](#table:best_fits) gives an equivalent disk dust mass of 6 M$_{\oplus}$, assuming a gas-to-dust mass ratio of 100. |
| Disk-to-star mass ratio: circumbinary disk of A; B and W | about 20% (A); about 0.3% (B and W) | not stated | percent | 6 | we calculate ratios of $M_{disk}/M_\star \approx 20$% for the circumbinary disk around VLA 1623A and $M_{disk}/M_\star \approx 0.3$% for both VLA 1623B and VLA 1623W |
| Closest plane-of-sky approach of W and B (nominal proper motions) | about 4.6 arcsec (about 650 au) at about 1400 yr ago | not stated | arcsec; au; yr | 7 | The closest approach is shown with open circles at a time of $\sim$ 1400 years, when the two sources were separated by $\sim$ 4.6 arcsec ($\sim$ 650 au) in the plane of the sky. |
| Monte Carlo median minimum separation and time since closest approach | 4.9 arcsec; 1150 yr | quartiles 2.7-6.6 arcsec; 830-1590 yr | arcsec; yr | 7 | we find a median minimum separation of 4.9 arcsec (first and third quartiles are 2.7 arcsec and 6.6 arcsec) and a median time of 1150 years (first and third quartiles are 830 years and 1590 years) |
| Stellar surface density Sigma_11 at VLA 1623 | 1470 | not stated | YSO pc^-2 | 8 | The 11th nearest neighbour gives $\Sigma_{11} = 1470$ YSO pc$^{-2}$. |
| Probability VLA 1623W is a companion, P(c|d) | 0.55 | not stated (stated as likely a lower limit) | dimensionless | 8 | we calculate a probability that VLA 1623W is a companion protostar of VLA 1623 of $P(c/d) = 0.55$ |
| Probability VLA 1623B is a companion of A, P(c|d) | 0.95 | not stated | dimensionless | 8 | we find $P(c/d) = 0.95$ for VLA 1623A and VLA 1623B to be companion YSOs |
| Gravitational energy of W relative to A/B | about -0.2e37 | not stated (upper limit) | J | 9 | The resulting energies are $\Omega = -GM_{AB}M_W/r \approx -0.2 \times 10^{37}$ J for the gravitational energy |
| Kinetic energy of W relative to A/B | about 1e37 | not stated | J | 9 | $K = \frac{1}{2}M_W\sigma_{3D}^2 \approx 1 \times 10^{37}$ J for the kinetic energy |

## Qualitative findings

- C17O at the circumstellar disks shows velocity gradients consistent with Keplerian rotation, while on larger scales it traces outflow cavity walls  
  > "we find that the high velocity gas towards the circumstellar disks have velocity gradients consistent with Keplerian rotation indicating that the compact emission indeed arises from the circumstellar disk." (Circumstellar disks)
- VLA 1623B is the most massive component, with more than twice the mass of A and W combined  
  > "VLA 1623B has the highest mass, with more than twice the mass of the other two stellar components combined." (Stellar masses)
- VLA 1623W appears unbound to A/B and may disperse  
  > "VLA 1623W appears to be unbound to the other protostars, suggesting that it may disperse." (Conclusions)

## Claim tuples

- H: Can the stellar masses of VLA 1623A, B and W be measured from C17O (3-2) Keplerian rotation? | E: uv-plane radiative transfer fits of Keplerian disk models with pdspy and dynesty to each source separately | R: M* = 0.27 (A, combined), 1.9 (B), 0.64 (W) Msun | F: Masses agree with previous estimates that used other tracers and techniques | **supported**
- H: VLA 1623W was ejected from the central core | E: Compared the measured masses and the extrapolated proper motions of W and B | R: A is the lowest-mass component; closest approach of W and B is about 650 au, below 100 au only at the 6th percentile | F: Ejection of VLA 1623W is disfavoured | **supported**
- H: VLA 1623W is a genuine companion rather than a chance-aligned YSO | E: Bayesian companion probability following Tobin22 with local YSO surface density | R: P(c|d) = 0.55, likely a lower limit | F: Cannot rule out an unrelated YSO but a genuine companion is favoured from disk youth and streamers | **partially**
- H: How did the VLA 1623 components form? | E: Compared separations, misaligned disk orientations and masses with turbulent and disk fragmentation expectations | R: A, B and W wide and misaligned; A is a tight binary | F: A, B and W formed via turbulent fragmentation, with Aa/Ab possibly from disk fragmentation | **partially**
- H: Are the disks gravitationally unstable? | E: Disk-to-star mass ratios from the best-fit models | R: About 0.3% for B and W, about 20% for the circumbinary disk of A | F: B and W disks appear stable; the circumbinary disk is intermediate | **supported**

## Reasoning

- Why this data: C17O is optically thinner within the envelope than previously used tracers, helping to separate the Keplerian disks  
  > "C$^{17}$O is a rarer species that is less optically thick within the envelope than the line tracers that have previously been observed" (Introduction)
- Why this method: dynesty nested sampling chosen over MCMC; fitting visibilities lets the model constrain sub-beam scales  
  > "We opted to use `dynesty` here because we find nested sampling to be more robust with multi-modal posteriors and it also has well-defined stopping criteria." (Modelling); "In addition, `pdspy` fits visibility data." (Stellar masses)
- Alternative: X-shaped C17O emission attributed to outflow cavity walls, not envelope gas streamers as in Hsieh20  
  > "We note that (cite: Hsieh20) instead identify similar structures in C$^{18}$O (2 – 1) as gas streams in the envelope." (Outflows and infall); "Broadly, we find good agreement between c-C$_3$H$_2$ and the X-shaped extended emission in C$^{17}$O, which is why we attribute this material to the outflow wall rather than a gas streamer." (Outflows and infall)
- Alternative: SO2 and H13CN emission interpreted as a mix of infall and outflow, not a rotating disk  
  > "Therefore, the SO$_2$ and (blended) H$^{13}$CN data may be tracing a mix of both infall and outflow." (Outflows and infall)
- How they decided it was enough: _not stated_
- Limitation (authors): Disk parameters other than stellar mass are poorly constrained because strict velocity and uv cuts were needed  
  > "We caution against over-interpreting the value of these disk parameters given that we had to impose strict velocity and $uv$ limits." (Modelling)
- Limitation (authors): Additional systematic effects such as the model choice may give larger errors than quoted  
  > "There may be additional systematic effects such as the choice of model that lead to larger errors on the measured values than those presented here (cite: Premnath20)." (Modelling)
- Limitation (authors): Emission assumed to trace only rotating disks; infall and streamer contributions assumed negligible  
  > "we assumed that the C$^{17}$O (3 – 2) emission solely traces the rotationally supported disks and that any potential contributions from the surrounding envelope or gas streamers are negligible" (Results)
- Caveat (inferred, ours): Masses depend on the assumed 140 pc distance and fixed inclination/geometry; B has i = 91 deg with large uncertainty
- Caveat (inferred, ours): Fixed C17O/CO and CO/H2 abundances and no treatment of C17O hyperfine structure are not tested for their effect on M*
- Caveat (inferred, ours): Strict channel and uv cuts differ per source and could bias M* and the other parameters; no sensitivity test is shown
- Caveat (inferred, ours): The 10% error floor is an ad hoc addition, not a fitted systematic
- Caveat (inferred, ours): Prior ranges and dynesty convergence settings are not given, so posteriors cannot be judged

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version and the exact self-calibration and tclean parameter files
- Missing: pdspy prior ranges, likelihood and dynesty settings
- Missing: Line-free channel selections and masks
- Missing: Moment 1 masking thresholds
- Data volume (inferred): About 10-30 GB of raw and calibrated data for two Band 7 C-4 executions (about 53 min on source); line cubes a few GB
- Score (inferred): 3/5, Project code, array, calibrators, spectral setup, self-cal intervals, robust values and a full parameter table are given, but CASA version, masks, priors and sampler settings are missing, so the fits cannot be redone exactly.
- Rediscovery candidate: no, The ALMA project code is given and results are numeric, but the paper does not state the data are public and the imaging and fitting recipe is missing key settings.

## Links

- Method: (cite: Sheehan19) (pdspy uv-plane Keplerian disk fitting)
- Method: (cite: SheehanEisner18) (full description of the pdspy technique)
- Method: (cite: Tazzari18) (galario code used to Fourier transform models)
- Method: (cite: Speagle20) (dynesty nested sampler)
- Method: (cite: Tobin22) (companion probability method)
- Companion: (cite: Murillo13) (earlier Keplerian rotation modelling of the VLA 1623A circumbinary disk in C18O (2-1))
- Companion: (cite: Harris18) (binary nature of VLA 1623A and proper motion of VLA 1623W)
- Companion: (cite: Ohashi22) (mass estimate of VLA 1623B from CS (5-4))
- Companion: (cite: Mercimek23) (mass estimate of VLA 1623W and streamers in C18O (2-1))
- Companion: (cite: Michel22) (VLA 1623W disk flaring and lack of envelope)
- Related: ODISEA (Ophiuchus disk survey)

## Checks

```json
{
 "quotes": 141,
 "quotes_ok": 141,
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
  "facts": 115,
  "stated": 86,
  "rate": 0.748
 },
 "evidence_ok": true
}
```
