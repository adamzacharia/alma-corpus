# Cosmo-tomography toward PKS 1830‒211: Variability of the quasar and of its foreground molecular absorption monitored with ALMA

`2023A&A...674A.101M` | Astronomy and Astrophysics 2023 | first author: Muller, S. | arXiv: 2304.09002 | DOI: 10.1051/0004-6361/202245768

Card schema 1.0 | model gemini-4-argon | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, astrochemistry, high_z_galaxies
- Question: How do the submillimeter continuum emission and foreground molecular absorption of the lensed quasar PKS 1830-211 vary over time, and what constraints do these variations place on the quasar's activity and small-scale ISM structures in the z=0.89 absorber?  
  > "We aim to study the time variations of the system (the two main lensed images of the quasar and the two corresponding sightlines in the absorber) in order to obtain constraints on both the quasar activity and small-scale structures in the interstellar medium of the absorber." (abstract)
- Target **PKS 1830-211**: coordinates _not stated_; z/distance z = 2.5 (blazar), z = 0.89 / 0.88582 (lens/absorber)  
  > "PKS 1830$-$211 is a blazar at $z=2.5$ (cite: lid99) with strong gravitational lensing due to an intervening nearly face-on spiral galaxy at $z=0.89$ (cite: wik96; win02)." (Introduction); "Sky frequencies are calculated for $z$=0.88582." (Spectroscopic data); distance from (cite: lid99); (cite: wik96; win02)  
  > "PKS 1830$-$211 is a blazar at $z=2.5$ (cite: lid99) with strong gravitational lensing due to an intervening nearly face-on spiral galaxy at $z=0.89$ (cite: wik96; win02)." (Introduction); "Sky frequencies are calculated for $z$=0.88582." (Spectroscopic data)

## Data provenance

- ALMA projects: 2011.0.00405.S, 2012.1.00056.S, 2013.1.00020.S, 2015.1.00075.S, 2018.1.00051.S, 2021.A.00028.S
- bands: Band 7  
  > "The correlator setup was chosen to simultaneously cover the ground-state transitions of H$_2$O (557 GHz, rest frequency) and CH (two $\Lambda$-doublets at $\sim 533$ and 537 GHz, rest frequency) redshifted into Band 7." (2016 monitoring campaign)
- frequencies and spectral setup: 3 spectral windows at ~282.4, 284.6, 295.4 GHz (938 MHz bandwidth, 0.56 MHz / 0.6 km/s resolution after Hanning smoothing); 1 continuum window at 296.8 GHz (31.25 MHz resolution)  
  > "To cover these lines, three spectral windows were centered at $\sim$282.4, 284.6, and 295.4 GHz sky frequency, with a bandwidth of 938 MHz and a spectral resolution of 0.56 MHz, resulting in a velocity resolution of 0.6 km s$^{-1}$ after Hanning smoothing." (2016 monitoring campaign); "A fourth spectral window, not including any detectable spectral line, was centered at 296.8 GHz with a coarser spectral resolution of 31.25 MHz in order to provide extra continuum data." (2016 monitoring campaign)
- continuum bandwidth: _not stated_
- arrays: 12m array (36 to 45 antennas)  
  > "Table notes: $a)$ Modified Julian day; $b)$ Number of 12m antennas in the array" (2016 monitoring campaign)
- configurations: _not stated_
- baselines: longest baseline > 450 m  
  > "During the monitoring, the array configuration changed, but the longest baseline was always longer than 450 m, such that the synthesized beam was always smaller than 0.5$\ensuremath{''}$ and the two main lensed images of the quasar are therefore always well resolved." (2016 monitoring campaign)
- angular resolution: < 0.5''  
  > "During the monitoring, the array configuration changed, but the longest baseline was always longer than 450 m, such that the synthesized beam was always smaller than 0.5$\ensuremath{''}$ and the two main lensed images of the quasar are therefore always well resolved." (2016 monitoring campaign)
- max recoverable scale: _not stated_
- sensitivity: 0.47% to 2.14% of SW continuum per 0.6 km/s channel (individual visits); < 0.1%-0.2% (2016 averaged spectrum); 0.1% to 1.3% (complementary spectra)  
  > "$i)$ rms noise level of the spectrum between 295.0 and 295.4 GHz (i.e., a line-free region in the spectral window centered on the redshifted H$_2$O transition), in % of the continuum level of the SW image, at the native spectral resolution of $\sim 0.6$ km s$^{-1}$." (2016 monitoring campaign); "The resulting high-sensitivity spectra have a noise level of better than $0.1\%-0.2$% of the normalized continuum level" (2016 averaged spectra)
- time on source: < 10 min per visit (17 visits)  
  > "The on-source integration time for each visit was slightly less than 10 min, set by our original goal, which is to be able to track changes in the spectral line profiles down to a few percent during each individual visit." (2016 monitoring campaign)
- observing dates: March to September 2016 (monitoring); 2012-2022 (complementary data)  
  > "Observations were made during ALMA Cycle 3, between March and September 2016." (2016 monitoring campaign); "In addition to the 2016 monitoring data, we also used observations of PKS 1830$-$211 available in the ALMA archive to extract continuum information (flux density and flux density ratio) between 2012 and 2022" (Complementary data)
- pi or archival as stated: _not stated_
- Line: ortho-H2O J_{Ka,Kc} = 1_{1,0} - 1_{0,1} (556.9359877 GHz)
- Line: ortho-H2(18)O J_{Ka,Kc} = 1_{1,0} - 1_{0,1} (547.676440 GHz)
- Line: ortho-H2(17)O J_{Ka,Kc} = 1_{1,0} - 1_{0,1} (552.020960 GHz)
- Line: CH J = 3/2 - 1/2 (two Lambda-doublets) (532.7215886 - 536.7955695 GHz)
- Line: 13CH J = 3/2 - 1/2 (two Lambda-doublets) (531.859975 - 536.132344 GHz)
- External data: ALMA CH+ (1-0) spectrum from 2015  
  > "To these water spectra, we can add the observations of the CH$^+$ (1-0) line in 2015 (reported by (cite: mul17))." (Long-term variations (2012 - 2022)) [from (cite: mul17)]
- External data: Rest frequency of H2O  
  > "For H$_2$O, the frequency is taken from (cite: caz09)." (Spectroscopic data) [from (cite: caz09)]
- External data: Rest frequencies and relative intensities of CH  
  > "For CH, frequencies are taken from (cite: tru14) and line relative intensities ($S_{ul}$) from (cite: nij12)." (Spectroscopic data) [from (cite: tru14), (cite: nij12)]
- External data: Spectroscopic data for 13CH  
  > "For $^{13}$CH, spectroscopic data are taken from (cite: hal08) and the JPL molecular spectroscopy database." (Spectroscopic data) [from (cite: hal08), JPL molecular spectroscopy database]
- External data: Galactic abundance ratios [CH]/[H2] and [H2O]/[H2]  
  > "(cite: she08) derive a quasi-linear relationship between the column densities of CH and H$_2$, with an average abundance ratio of [CH]/[H$_2$] $= 3.5 _{-1.4}^{+2.1} \times 10^{-8}$ along diffuse molecular sightlines and dark clouds." (Correlation H2O – CH); "For water, (cite: fla13) also find a remarkably constant abundance ratio relative to H$_2$ in Galactic translucent clouds, with [H$_2$O]/[H$_2$] $= (4.8 \pm 0.3) \times 10^{-8}$." (Correlation H2O – CH) [from (cite: she08), (cite: fla13)]
- Simulation/model as data: Synthetic spectra with injected periodic Gaussian perturbations used to validate PCA retrieval  
  > "In order to test the PCA performances, we ran experiments synthetic spectra with similar noise properties and time sampling as in the ALMA monitoring, in which we introduced a time varying component (with a given period) in the form of a Gaussian perturbation with a given amplitude, full width at half maximum (FWHM), and velocity." (Principal component analysis)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.7.2  
  > "The calibration was done with the CASA (version 4.7.2) package (cite: CASA2022)." (2016 monitoring campaign)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (Butler-JPL-Horizons 2012 model), Pallas, J 1924-2914 (J 1924-292), or J 1733-130  
  > "The flux calibration was carried out using Titan (Butler-JPL-Horizons 2012 model), Pallas, J 1924$-$2914, or J 1733$-$130" (2016 monitoring campaign)
- flux scale uncertainty: 10%-20% (conservative ~20% adopted in Table 1)  
  > "We expect an absolute flux accuracy of the order of 10%-20% according to the ALMA Technical Handbook (cite: cor22)." (2016 monitoring campaign); "We adopt a conservative absolute flux accuracy of $\sim 20$%" (2016 monitoring campaign)
- self calibration: Phase-only self-calibration with 10 s solution interval  
  > "After the standard calibration, a step of phase-only self-calibration on PKS 1830$-$211 was done with a short solution interval of 10 s." (2016 monitoring campaign)

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
- line free channels: 295.0 to 295.4 GHz (for rms measurement); channels outside absorption features flagged for spectral index and baseline fitting  
  > "$i)$ rms noise level of the spectrum between 295.0 and 295.4 GHz (i.e., a line-free region in the spectral window centered on the redshifted H$_2$O transition), in % of the continuum level of the SW image, at the native spectral resolution of $\sim 0.6$ km s$^{-1}$." (2016 monitoring campaign); "The spectral indices were measured directly from the spectra corresponding to each lensed image after flagging channels associated with absorption features." (Spectral index)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Differential polarimetry formalism and double polarization ratio R_pol  
  > "Although the ALMA data were not taken in full polarization mode, we can use the data obtained separately from the two orthogonal polarizers, XX and YY, in the alt-azimuth frame of the antennas to retrieve some source polarization properties using a differential polarimetry analysis (see, e.g., (cite: mar15; mar16; mar19))." (Differential polarimetry) [from (cite: mar15; mar16; mar19)]
- Measure-of-randomness analysis using the Von Neumann estimator  
  > "Nonetheless, we applied a measure-of-randomness analysis (see, e.g., (cite: che17)) using the Von Neumann estimator ($\mathcal{E}_{\rm VN}$)" (The time delay and the differential magnification factor) [from (cite: che17)]

### Not stated but needed to reproduce (our reading)

- Exact relative positions or constraints on the two point-like components in UVMultiFit
- Details of the MCMC sampler, number of walkers/steps, and prior distributions for the core+plasmon continuum model
- Exact velocity channel masks used for flagging absorption lines during continuum spectral index and polynomial baseline fitting
- Details of the Clean algorithm implementation used to deconvolve the CH hyperfine structure

## Analysis recipe

1. **Extract continuum flux densities, flux-density ratios, differential polarimetry, and absorption spectra from calibrated visibilities**: Visibility fitting with a two point-source model in UVMultiFit on Stokes I, XX, and YY separately; extraction of spectral indices after flagging absorption channels  
  > "The calibrated visibilities were finally fitted using the Python task UVMultiFit (cite: mar14) with a source model consisting of two point-like components, where the flux density of the NE image and the flux-density ratio, $\Re = f_{\rm NE}/f_{\rm SW}$, were set as free parameters." (2016 monitoring campaign); "Different fit runs were carried out using Stokes I data and data from the XX and YY polarizers separately in order to extract differential polarimetric information (see Sect. 3.4)." (2016 monitoring campaign); "The spectral indices were measured directly from the spectra corresponding to each lensed image after flagging channels associated with absorption features." (Spectral index)
   - software: UVMultiFit
   - parameter: Two point-like components; free parameters: f_NE and R = f_NE/f_SW  
  > "The calibrated visibilities were finally fitted using the Python task UVMultiFit (cite: mar14) with a source model consisting of two point-like components, where the flux density of the NE image and the flux-density ratio, $\Re = f_{\rm NE}/f_{\rm SW}$, were set as free parameters." (2016 monitoring campaign)
   - assumption: Third lensed image and small Einstein ring extensions are negligible and ignored  
  > "The additional weak features of PKS 1830$-$211 reported from ALMA observations by (cite: mul20b), namely the third image (about 150 times weaker than the NE and SW images) and the small extensions from the NE and SW images (corresponding to the start of the Einstein ring and with a steep spectral index), have a negligible impact on the fitting process and were therefore not considered." (2016 monitoring campaign)
   - fitting: Visibility model fitting in UVMultiFit  
  > "The calibrated visibilities were finally fitted using the Python task UVMultiFit (cite: mar14) with a source model consisting of two point-like components" (2016 monitoring campaign)
   - validation: Smooth light curve across four different flux calibrators without significant outliers  
  > "The data points follow a relatively smooth light curve, which is free of significant outliers, giving confidence that potential systematic effects in the flux calibration are limited." (Results from continuum data)
2. **Estimate time delay and differential magnification via randomness minimization**: Measure-of-randomness analysis on the combined NE and time-shifted, scaled SW light curves using the Von Neumann estimator  
  > "Nonetheless, we applied a measure-of-randomness analysis (see, e.g., (cite: che17)) using the Von Neumann estimator ($\mathcal{E}_{\rm VN}$), which is defined as: $$\begin{equation} \label{eq:vonneumann} \mathcal{E}_{\rm VN}(\Delta t, \hbox{$\mathcal{R}_q$}) = \frac{1}{N-1} \sum _{i=1}^{N-1} \left [ \mathcal{F}(t_i) - \mathcal{F}(t_{i+1}) \right ]^2 , \end{equation}$$" (The time delay and the differential magnification factor)
   - parameter: Grid over time delay Delta t and differential magnification R_q  
  > "By varying the two quantities $\Delta t$ and $\mathcal{R}_q$, we can calculate the corresponding values of $\mathcal{E}_{\rm VN}$." (The time delay and the differential magnification factor)
   - assumption: Minimum randomness corresponds to the most likely values of Delta t and R_q  
  > "The assumption of minimum randomness (as in the $\chi^2$ minimization) points to the most likely values of the two parameters $\mathcal{R}_q$ and $\Delta t$." (The time delay and the differential magnification factor)
   - fitting: Minimization of Von Neumann estimator E_VN  
  > "By varying the two quantities $\Delta t$ and $\mathcal{R}_q$, we can calculate the corresponding values of $\mathcal{E}_{\rm VN}$." (The time delay and the differential magnification factor)
   - validation: Comparison with MCMC parametric continuum model results  
  > "In Sect. 3.6, we further present a simple parametric model of the continuum evolution during the monitoring, from which we extract best-fit values of the time delay, namely $25 \pm 3$ days, and of the differential magnification, $1.25 \pm 0.04$, which fall in the valley of lowest Von Neumann randomness in Fig.3." (The time delay and the differential magnification factor)
3. **Model continuum light curve, spectral index evolution, and polarization with a core + ballistic plasmon model**: Simultaneous parametric fit to NE/SW flux densities, NE spectral index, and spectral-index difference using MCMC; qualitative extension to Stokes Q polarization  
  > "We show the results of this simple model simultaneously fitted to the light curve and spectral-index differences in Fig. 4." (Simple scenario of the continuum evolution); "The corner plot results of a Markov-chain Monte Carlo (MCMC) exploration of the plasmon injection time, $I_c$, $I_p$, $\beta$, $\alpha_p$, the time delay, $\Delta t$, and the differential magnification are shown in Fig. 5." (Simple scenario of the continuum evolution)
   - parameter: Plasmon injection time t_0, core flux I_c (< 0.18 Jy), plasmon flux I_p, decay power beta, plasmon spectral index alpha_p, time delay Delta t, differential magnification R_q; for polarization exploration: Gaussian F(t-t0) with width 100 days, m_c = 0.05, m_p = 0.2  
  > "The corner plot results of a Markov-chain Monte Carlo (MCMC) exploration of the plasmon injection time, $I_c$, $I_p$, $\beta$, $\alpha_p$, the time delay, $\Delta t$, and the differential magnification are shown in Fig. 5." (Simple scenario of the continuum evolution); "For the sole purpose of a qualitative exploration, we set $F(t-t_0)$ to be Gaussian, with a width of 100 days, $m_c = 0.05$, and $m_p = 0.2$." (Modeling with polarization evolution)
   - assumption: No micro- or milli-lensing; stable optically thick core (alpha_c = 0, I_c < 0.18 Jy); single ballistic plasmon injection; adiabatic losses dominate over radiative losses; electron energy index p = 3  
  > "Integrating this equation for an initial electron population $N \propto E^{-p}$ (fixing $p=3$) and computing the resulting synchrotron spectrum (with the assumption that $r \gg r_0$) results in $\beta = \frac{1}{v\sin{\theta} + k}$, where $k$ depends on the choice of initial time, $t_0$." (Simple scenario of the continuum evolution); "The emission from the core, $I_c$, is stable in time and is considered to be optically thick ($\alpha_c = 0$)." (Simple scenario of the continuum evolution); "The value of the core flux density is bound to be lower than the lowest flux density measured in the last epoch." (Simple scenario of the continuum evolution)
   - fitting: MCMC exploration with 10% systematic uncertainty added to flux densities and spectral indices  
  > "In this MCMC exploration, we have added a 10% systematic uncertainty to the flux densities and spectral indices, and have computed the error function using the flux densities of NE and SW images, the spectral index of NE, and the difference in spectral index between NE and SW." (Simple scenario of the continuum evolution)
   - validation: Tested sensitivity to relative weights of spectral index in error function (changing weight by factor 2 shifts Delta t by ~3 or 7 days)  
  > "For instance, if the weight of the spectral index is increased or decreased by a factor 2, the value of $\Delta t$ decreases or increases by $\sim$ 3 or $7$ days, respectively." (Simple scenario of the continuum evolution)
4. **Characterize absorption line variability using Principal Component Analysis (PCA)**: PCA decomposition of monitoring absorption spectra to extract eigenspectra and time-evolving eigenvalues, followed by sinusoidal fitting to eigenvalue time series  
  > "We used the `sklearn.decomposition.PCA` class in the scikit-learn Python package (cite: ped11) to retrieve the eigenspectra (i.e., as a function of velocity) and eigenvalues (i.e., as a function of time) of the monitoring spectra." (Principal component analysis); "Fitting such a sinusoidal function, we find periods of $272 \pm 15$ days, $186 \pm 20$ days, and $117 \pm 12$ days, for PC1, PC2, and PC3, respectively." (Principal component analysis)
   - software: scikit-learn
   - parameter: Velocity intervals: SW H2O [-100, 100], [-100, 0], [0, 100] km/s; SW CH1 and CH2 [-60, 60] km/s; NE H2O [-240, -120] km/s  
  > "| SW | H$_2$O | [-100,100] | 28 | $272 \pm 15$ |" (Table 1)
   - assumption: All eigenvalues taken with equal weight in sine function fit  
  > "Table notes: $a)$ The errors quoted for the period are those coming out of the fit of a sine function to the PC1 eigenvalues versus time, all eigenvalues taken with the same weight." (Table 1)
   - fitting: Sine function fit to PCA eigenvalues vs. time  
  > "Table notes: $a)$ The errors quoted for the period are those coming out of the fit of a sine function to the PC1 eigenvalues versus time, all eigenvalues taken with the same weight." (Table 1)
   - validation: Tested on noisy synthetic spectra with injected periodic Gaussian perturbations, and on line-free noise channels  
  > "A final test, taking a velocity range outside of any absorption features (i.e., purely noisy channels), shows no significant structure in the PCA decomposition." (Principal component analysis); "In order to test the PCA performances, we ran experiments synthetic spectra with similar noise properties and time sampling as in the ALMA monitoring, in which we introduced a time varying component (with a given period) in the form of a Gaussian perturbation with a given amplitude, full width at half maximum (FWHM), and velocity." (Principal component analysis)
5. **Construct deep averaged 2016 spectra and measure 12CH/13CH ratio**: Remove first-order polynomial baseline from each visit's spectrum, compute inverse-variance weighted average, and simultaneously fit multi-Gaussian velocity components convolved with hyperfine structure to 12CH and 13CH doublets  
  > "To achieve the best sensitivity and quality, we removed a spectral baseline as a first-order polynomial (i.e., corresponding to the intrinsic spectral index of each lensed image) on each individual spectrum." (2016 averaged spectra); "In order to estimate the $^{12}$CH/$^{13}$CH ratio, we performed a simultaneous fit of the two $\Lambda$-doublets of $^{12}$CH and $^{13}$CH for the SW absorption spectrum using the same intrinsic velocity profile for both CH and $^{13}$CH convolved to their corresponding fine structure, respectively, and with the $^{12}$CH/$^{13}$CH ratio as free scaling parameter." (Detection of 13CH)
   - parameter: About 10 Gaussian velocity components  
  > "We made several attempts with increasing numbers of Gaussian velocity components to reproduce the absorption profile of CH, and obtained satisfying results using about ten components." (Detection of 13CH)
   - assumption: Same intrinsic velocity profile for 12CH and 13CH; optically thin lines; no chemical fractionation  
  > "In order to estimate the $^{12}$CH/$^{13}$CH ratio, we performed a simultaneous fit of the two $\Lambda$-doublets of $^{12}$CH and $^{13}$CH for the SW absorption spectrum using the same intrinsic velocity profile for both CH and $^{13}$CH convolved to their corresponding fine structure, respectively, and with the $^{12}$CH/$^{13}$CH ratio as free scaling parameter." (Detection of 13CH)
   - fitting: Simultaneous multi-Gaussian profile fit with free scaling factor for 12CH/13CH  
  > "In order to estimate the $^{12}$CH/$^{13}$CH ratio, we performed a simultaneous fit of the two $\Lambda$-doublets of $^{12}$CH and $^{13}$CH for the SW absorption spectrum using the same intrinsic velocity profile for both CH and $^{13}$CH convolved to their corresponding fine structure, respectively, and with the $^{12}$CH/$^{13}$CH ratio as free scaling parameter." (Detection of 13CH)
   - validation: Tested stability of ratio across increasing numbers of Gaussian velocity components  
  > "During the process, we found that the ratio was relatively stable around approximately $150$, while the uncertainties and fit residuals decrease with an increasing number of velocity components." (Detection of 13CH)
6. **Derive water isotopolog and oxygen isotopic ratios (16O/18O and 18O/17O)**: Simultaneous multi-Gaussian opacity profile fitting to H2(16)O, H2(18)O, H2(17)O, and CH spectra from 2014 and 2022 epochs, then combining with statistical weights  
  > "For a given epoch, we assumed the same opacity profile (starting with five Gaussian velocity components) for all water isotopologs, as well as for CH when available in order to make the link between the high-opacity line of H$_2^{16}$O and the optically thin rare water isotopologs. We then fitted the opacity ratios as free scaling factors." (Water isotopologs and oxygen isotopic ratios)
   - parameter: N_gauss = 3, 5, or 9 Gaussian components; continuum covering factor f_c free (when H2(16)O included) or fixed to 1  
  > "When including the main water isotopolog, we also added the continuum-covering factor as a free parameter of the fit; otherwise, we fixed it to unity for the fit of the H$_2^{18}$O and H$_2^{17}$O isotopologs alone." (Water isotopologs and oxygen isotopic ratios)
   - assumption: Same opacity velocity profile for all isotopologs and CH; no fractionation for water isotopologs  
  > "Those are not expected to be affected by fractionation effects and should therefore reflect the true elemental isotopic ratios of oxygen." (Water isotopologs and oxygen isotopic ratios); "For a given epoch, we assumed the same opacity profile (starting with five Gaussian velocity components) for all water isotopologs, as well as for CH when available in order to make the link between the high-opacity line of H$_2^{16}$O and the optically thin rare water isotopologs." (Water isotopologs and oxygen isotopic ratios)
   - fitting: Chi-squared minimization of multi-Gaussian opacity profiles and statistical weighting of epochs  
  > "The values of the $^{16}$O/$^{18}$O ($= 65.3 \pm 0.7$ after combining the measurements with their statistical weights) and $^{18}$O/$^{17}$O ($= 11.5 \pm 0.5$) ratios are consistent with the previous measurements made from the HCO$^+$ isotopologs by (cite: mul06; mul11), albeit with much better accuracy." (Water isotopologs and oxygen isotopic ratios)
   - validation: Compared 5 vs 9 Gaussian components on July 2014 data and checked consistency across epochs  
  > "Due to the somewhat better signal-to-noise ratio of the data in July 2014, we used a higher number of Gaussian velocity components to obtain a better match of the profile and decrease the reduced $\chi$-squared. However, we found that the fitted ratios were not drastically affected and remained similar within the uncertainties." (Water isotopologs and oxygen isotopic ratios)
7. **Deconvolve CH hyperfine structure and correlate H2O and CH optical depths**: Convert absorption profiles to optical depth assuming f_c = 1, deconvolve CH hyperfine structure using a Clean algorithm, and compare tau(H2O) with tau(CH*)  
  > "With this assumption, it is also possible to deconvolve the hfs pattern of the CH doublets, for example using a Clean algorithm method assuming that the relative intensities of the hfs components follow their statistical weights." (Correlation H$_2$O – CH)
   - parameter: f_c = 1; T_CMB = 5.14 K at z = 0.89; H2O ortho-to-para ratio = 3  
  > "Taking these relative abundances with their uncertainties, and assuming (i) that the relative abundances of H$_2$O and CH for the absorbing material in the PKS 1830$-$211 absorber are similar to the Galactic clouds, (ii) an ortho-to-para ratio of three for H$_2$O, and (iii) that the molecules are at excitation equilibrium with cosmic-microwave-background photons ($\hbox{$T_\mathrm{CMB}$}= 5.14$ K at $z=0.89$, (cite: mul13)), we would expect opacity ratios $\tau$(H$_2$O)/$\tau$(CH$^*$) of between 3 and 9 (at the 1$\sigma$ confidence level)" (Correlation H2O – CH)
   - assumption: f_c = 1 (excluding saturated [-10, +10] km/s center); hfs intensities follow statistical weights; LTE with CMB at 5.14 K; H2O OPR = 3  
  > "With this assumption, it is also possible to deconvolve the hfs pattern of the CH doublets, for example using a Clean algorithm method assuming that the relative intensities of the hfs components follow their statistical weights." (Correlation H2O – CH)
   - fitting: Clean algorithm deconvolution of hyperfine structure  
  > "With this assumption, it is also possible to deconvolve the hfs pattern of the CH doublets, for example using a Clean algorithm method assuming that the relative intensities of the hfs components follow their statistical weights." (Correlation H2O – CH)
   - validation: Excluded saturated [-10, +10] km/s region where f_c ~ 95% violates f_c = 1 assumption  
  > "Discarding the center of the SW line profile (velocities between $\sim -10$ and +10 km s$^{-1}$), for which the water line is heavily saturated and has $\hbox{$f_c$}\sim 95$% (which is therefore not consistent with our working assumption $\hbox{$f_c$}=1)$, we find that the H$_2$O/CH opacity ratios along the SW line of sight are roughly around 9" (Correlation H2O – CH)

## Software

- **CASA** 4.7.2: Calibration of ALMA visibility data  
  > "The calibration was done with the CASA (version 4.7.2) package (cite: CASA2022)." (2016 monitoring campaign)
- **UVMultiFit** : Fitting calibrated visibilities with a two point-like component model to extract flux densities, flux-density ratios, polarization ratios, and spectra  
  > "The calibrated visibilities were finally fitted using the Python task UVMultiFit (cite: mar14) with a source model consisting of two point-like components, where the flux density of the NE image and the flux-density ratio, $\Re = f_{\rm NE}/f_{\rm SW}$, were set as free parameters." (2016 monitoring campaign)
- **scikit-learn** : Principal component analysis (sklearn.decomposition.PCA) of the monitoring absorption spectra  
  > "We used the `sklearn.decomposition.PCA` class in the scikit-learn Python package (cite: ped11) to retrieve the eigenspectra (i.e., as a function of velocity) and eigenvalues (i.e., as a function of time) of the monitoring spectra." (Principal component analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| NE image continuum flux density drop (2016 monitoring) | 1.17 to 0.19 | 20% | Jy | 1 | / 2016/03/05 / 7452.545 / 36 / 1.2 / Titan / 101 / 1.17 / 1.06 / 1.100 (3) / $44.3\pm 1.3$ / 0.146(7) / 0.49 /; / 2016/09/08 / 7639.162 / 39 / 0.6 / J 1924$-$292 / 104 / 0.19 / 0.19 / 1.010 (2) / $2.9\pm 0.6$ / 0.111(21) / 1.16 / |
| Average flux-density ratio R (2016 monitoring) | 1.04 | not stated | dimensionless | 1 | In contrast to the large decrease in flux density during the 2016 monitoring, the instantaneous flux-density ratios $\Re = f_{\rm NE}/f_{\rm SW}$ show only mild ($\sim 10$%) variations around an average value of $\sim 1.04$, with extreme values of 0.96 and 1.15 (Fig. 1 b). |
| Average ALMA flux-density ratio R (2012-2022) | 1.38 | 0.35 | dimensionless | 1 | Taken at face value, the average value of all the ALMA flux-density ratios measured between 2012 and 2022 is $1.38 \pm 0.35$ (with 1$\sigma$ dispersion) and the median is 1.29. |
| Time delay between NE and SW images (Delta t) | 25 | 3 | days | 3 | We propose a simple parametric model of a core plus a ballistic plasmon to account for the continuum evolution, from which we constrain a time delay of $25 \pm 3$ days between main lensed images.; / Lensing / Time delay (days) / $\Delta t$ / 25 $\pm$ 3 / depends on plasmon model and data weights / |
| Differential magnification factor (R_q) | 1.24 | 0.04 | dimensionless | 3 | / / Differential magnification / $\mathcal{R}_q$ / 1.24 $\pm$ 0.04 / weakly coupled to $\Delta t$ /; From this parametric model, we also obtain a new measurement of the time delay between the NE and SW images of $\Delta t = 25 \pm 3$ days, and of their differential magnification, namely $1.24 \pm 0.04$ |
| Core flux density (I_c) | 0.178 | 0.010 | Jy | 3 | / Core / Flux density of the core (Jy) / $I_c$ / $0.178 \pm 0.010$ / bounded $<0.18$ Jy / |
| Plasmon flux density at t_0 (I_p) | 1.51 | 0.09 | Jy | 3 | / / Flux density of the plasmon at $t_0$ (Jy) / $I_p$ / $1.51 \pm 0.09$ / weakly coupled to $t_0$ / |
| Power of plasmon flux-density decay (beta) | -2.2 | 0.4 | dimensionless | 3 | / / Power of the plasmon flux-density decay / $\beta$ / $-2.2 \pm 0.4$ / strongly coupled to $t_0$ / |
| Plasmon spectral index (alpha_p) | -0.89 | 0.02 | dimensionless | 3 | / / Plasmon spectral index / $\alpha_p$ / $-0.89 \pm 0.02$ / / |
| PCA PC1 period for SW H2O [-100, 100] km/s | 272 | 15 | days | 4 | Fitting such a sinusoidal function, we find periods of $272 \pm 15$ days, $186 \pm 20$ days, and $117 \pm 12$ days, for PC1, PC2, and PC3, respectively. |
| Average PCA PC1 period across lines/sightlines | 230 | not stated | days | 4 | All these measurements (Table 1; except overlapping velocity range for measurements from H$_2$O spectra) are independent, but still yield a consistent signal period of $\sim 230$ days for PC1, within error bars. |
| 12CH/13CH abundance ratio toward SW image | 150 | 10 | dimensionless | 5 | Our final $^{12}$CH/$^{13}$CH ratio is $150 \pm 10$. |
| 16O/18O isotopic ratio in z=0.89 absorber | 65.3 | 0.7 | dimensionless | 6 | We also measure the oxygen isotopic ratios, $^{16}$O/$^{18}$O $= 65.3 \pm 0.7$ and $^{18}$O/$^{17}$O $= 11.5 \pm 0.5$ in the $z=0.89$ absorber.; The values of the $^{16}$O/$^{18}$O ($= 65.3 \pm 0.7$ after combining the measurements with their statistical weights) and $^{18}$O/$^{17}$O ($= 11.5 \pm 0.5$) ratios are consistent with the previous measurements made from the HCO$^+$ isotopologs by (cite: mul06; mul11), albeit with much better accuracy. |
| 18O/17O isotopic ratio in z=0.89 absorber | 11.5 | 0.5 | dimensionless | 6 | We also measure the oxygen isotopic ratios, $^{16}$O/$^{18}$O $= 65.3 \pm 0.7$ and $^{18}$O/$^{17}$O $= 11.5 \pm 0.5$ in the $z=0.89$ absorber. |
| Width of broad shallow H2O absorption trough toward SW | 500 | not stated | km s^-1 | 5 | Finally, we find a remarkable continuous shallow trough in the water absorption spanning a velocity interval of nearly 500 km s$^{-1}$. |
| Source-covering factor f_c of SW image (2016 monitoring) | 96 | 1 | % | 1 | The covering factor is $\sim 96$% with only mild variations of the order of 1%, which contrast with the large variations of the flux density between the beginning and the end of our monitoring (Fig. 1). |

## Qualitative findings

- The quasar submillimeter flux density dropped monotonically by ~80% over 6 months in 2016 while the NE/SW flux-density ratio varied by only ~10%.  
  > "The submm light curve shows a dramatic and nearly monotonic decrease of 80% in the flux density during our monitoring." (Summary and conclusions); "In contrast, the flux-density ratios between the two lensed images of the quasar show only mild variations of less than 10%." (Summary and conclusions)
- PCA of the absorption spectra reveals wavy variations with a ~230-day period across both sightlines and species, potentially tied to the helical jet precession of the quasar.  
  > "A principal component analysis of the absorption spectra toward both images of PKS 1830$-$211 reveals a seemingly wavy behavior of the variations during the monitoring, with an apparent period of $\sim 230$ days, although this timescale is longer than the time span of our survey and would therefore need to be confirmed with a longer monitoring." (Summary and conclusions)
- A continuous, shallow (tau < 0.01) water absorption trough spanning nearly 500 km/s is detected toward the SW sightline, suggesting extra-planar or circumgalactic molecular gas.  
  > "In addition, the ALMA “super” spectrum of the H$_2$O absorption now reveals an even more surprising structure in the form of a weak ($\tau < 0.01$) continuous absorption trough covering a wide velocity range of nearly 500 km s$^{-1}$ toward the SW image (Fig. 15c)." (Weak and broad water absorption trough in the SW sightline)
- The H2O/CH optical depth ratio in the z=0.89 absorber is comparable to that in Milky Way translucent clouds, with higher H2O/CH toward SW than NE, similar to the Galactic CMZ vs disk trend.  
  > "Moreover, the differences in H$_2$O and CH$^*$ opacity ratios between the SW and NE lines of sight follow a similar trend to that observed in the Milky Way between clouds in the central molecular zone (CMZ) and the Galactic disk" (Correlation H2O – CH)

## Claim tuples

- H: A simple parametric model of a stable optically thick core plus a single adiabatically expanding ballistic plasmon can explain both the 80% flux decay and the systematic spectral-index difference between the NE and SW lensed images, while constraining the lensing time delay and differential magnification. | E: Fit the 7-parameter core+plasmon model via MCMC simultaneously to the NE and SW flux densities, NE spectral index, and spectral-index difference across the 17 monitoring epochs. | R: The model reproduces the light-curve decay and spectral-index difference, yielding a time delay of 25 +/- 3 days and differential magnification of 1.24 +/- 0.04, consistent with the Von Neumann randomness valley. | F: A single cooling plasmon plus stable core accounts for the continuum and polarization evolution and yields a lensing time delay consistent with lens models, though the delay value is model- and weight-dependent. | **supported**
- H: Time variations in the foreground molecular absorption profiles are driven by periodic changes in background illumination from a precessing helical jet in the quasar. | E: Perform Principal Component Analysis (PCA) on the 2016 monitoring spectra of H2O and CH toward both SW and NE images and fit sine functions to the first principal component eigenvalues. | R: PC1 eigenvalues across independent velocity ranges, species (H2O, CH), and sightlines (SW, NE) show sinusoidal variations with a consistent period of ~230 days. | F: The wavy absorption variations likely originate from background continuum illumination modulated by the quasar's helical jet, though confirmation requires monitoring over a timespan longer than the ~230-day period. | **partially**
- H: The elemental 12C/13C and oxygen isotopic ratios in the z=0.89 absorber reflect a less nucleosynthetically processed ISM compared to the local Milky Way, while other carbon-bearing species suffer from chemical fractionation. | E: Stack all 17 monitoring spectra to detect 13CH and simultaneously fit multi-Gaussian hyperfine profiles to 12CH and 13CH; similarly fit H2(16)O, H2(18)O, and H2(17)O in 2014 and 2022 spectra. | R: Measured 12CH/13CH = 150 +/- 10 (higher than CH+, CH3OH, HCO+, HCN, HNC along the same sightline), 16O/18O = 65.3 +/- 0.7, and 18O/17O = 11.5 +/- 0.5. | F: CH and H2O isotopologs provide unfractionated isotopic ratios indicating a less processed ISM dominated by massive-star nucleosynthesis at z=0.89, whereas other C-bearing molecules are affected by fractionation. | **supported**

## Reasoning

- Why this data: PKS 1830-211 has high submm brightness, superluminal jet motions, lens magnification, and rich foreground molecular absorption; Band 7 simultaneously covers saturated ortho-H2O (probing line wings and optically thin NE sightline) and optically thin CH (tau ~ 1, probing SW line center) with <0.5'' resolution to separate the 1'' lensed images.  
  > "During the monitoring, the array configuration changed, but the longest baseline was always longer than 450 m, such that the synthesized beam was always smaller than 0.5$\ensuremath{''}$ and the two main lensed images of the quasar are therefore always well resolved." (2016 monitoring campaign); "The H$_2$O absorption is deeply saturated toward the SW image near $v \sim 0$ km s$^{-1}$ (cite: mul14), but its large opacity is well suited to investigating the variations of the line wings. The H$_2$O line is also well suited to probing changes in the presumably optically thin NE absorption. On the other hand, the CH absorption reaches an apparent peak opacity of $\tau \sim 1$ along the SW line of sight, complementing the H$_2$O line in tracing variations in the line center of the SW absorption." (Results from spectral lines)
- Why this method: Fitting visibilities directly with UVMultiFit and taking relative ratios (flux ratio R, double polarization ratio R_pol, spectral index difference Delta alpha) removes instrumental and absolute flux calibration systematics; PCA isolates coherent multi-channel spectral variations.  
  > "In addition, while the absolute flux accuracy is of $\sim 10\%-20$%, we emphasize that the accuracy of relative quantities, such as the flux-density ratio of both lensed images and the polarization ratio, is much higher (e.g., at a per mil level for the flux density ratio), and can therefore offer subtle diagnostics of the quasar activity, as discussed in the following subsections." (Results from continuum data); "To extract more information from the variations of the absorption line profile, we ran a principal component analysis (PCA)." (Principal component analysis)
- Alternative: Micro-lensing or intrinsic absorber cloud motions/chemistry as the primary cause of the 2016 short-term absorption variations — rejected in favor of intrinsic quasar continuum morphology changes because ISM dynamical/chemical timescales are too long and variations are coherent across both sightlines during an 80% intrinsic flux drop.  
  > "To further characterize the absorption variations, we can assume that the absorbing screen is constant in time, that is, $d\tau(x,y)/dt =0$. This is justified by the fact that the timescales associated with potential causes of variations in the absorber are much longer than those we are interested in, even for small-scale structures on AU- to pc scales." (Analysis of the absorption profiles and their time variations); "Given the quasi-monotonic and severe decrease in the flux density of PKS 1830$-$211 during our six-month monitoring (by $\sim 80$% ), the short (timescale of the order of one week) and regular variations of the absorption spectra, and the apparent coherence (periodicity?) of the variations over $\gtrsim 200$ days seen toward both lensed images, we conclude that they are most likely due to intrinsic changes in the background continuum distribution, that is, the activity of the quasar, rather than to micro-lensing events." (Possible causes of time variations of the continuum distribution)
- How they decided it was enough: 10 min on-source per visit was chosen to reach <1% continuum rms to track percent-level line variations; Gaussian components were added to CH and water isotopolog fits until residuals/reduced chi-squared stabilized.  
  > "The on-source integration time for each visit was slightly less than 10 min, set by our original goal, which is to be able to track changes in the spectral line profiles down to a few percent during each individual visit." (2016 monitoring campaign); "During the process, we found that the ratio was relatively stable around approximately $150$, while the uncertainties and fit residuals decrease with an increasing number of velocity components." (Detection of 13CH)
- Limitation (authors): The nearly monotonic, featureless light curve in 2016 causes a strong degeneracy between time delay and differential magnification in the Von Neumann analysis.  
  > "Given the quasi-monotonic and relatively featureless light curve of PKS 1830$-$211 during our monitoring, there is a strong degeneracy between the two parameters." (The time delay and the differential magnification factor)
- Limitation (authors): The time delay constraint from the parametric continuum model is highly model-dependent and sensitive to the relative weighting of flux densities and spectral indices.  
  > "The constraint on the time delay, $\Delta t$, is highly model dependent" (Simple scenario of the continuum evolution)
- Limitation (authors): Limited parallactic angle coverage and Dual-Pol (XX, YY) observations prevent quantitative constraints on the core and plasmon EVPAs.  
  > "we notice that the parallactic angle coverage of our data is very limited, which prevents us from putting robust constraints on the core and plasmon EVPAs." (Modeling with polarization evolution)
- Limitation (authors): The ~230-day period found by PCA is comparable to the 6-month monitoring duration and requires longer monitoring to confirm true periodicity.  
  > "These periods are comparable to the duration of our monitoring and it remains to be seen if the evolution is truly periodic with monitoring over longer timescales." (Principal component analysis)
- Limitation (authors): Mass of the gas producing the 500 km/s water absorption trough cannot be meaningfully estimated due to unknown spatial distribution.  
  > "Given the lack of constraints on the distribution of such material in the halo (probably fragmented in filamentary structures), it is not possible to get a meaningful estimate of its mass content." (Weak and broad water absorption trough in the SW sightline)
- Caveat (inferred, ours): Fitting a sinusoid to PCA eigenvalues over a 187-day baseline to claim a ~230-272 day period is susceptible to red-noise / random-walk drift producing apparent half-or-single-cycle waves.
- Caveat (inferred, ours): The parametric time delay (25 +/- 3 days) relies entirely on the assumed functional form of adiabatic plasmon decay to break the strong light-curve degeneracy.

## Reproducibility

- Data public (paper): ALMA project codes are listed and archival data from 2012-2022 were retrieved from the ALMA archive.  
  > "In addition to the 2016 monitoring data, we also used observations of PKS 1830$-$211 available in the ALMA archive to extract continuum information (flux density and flux density ratio) between 2012 and 2022" (Complementary data); "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00405.S (observations of H$_2$O and CH in April 2012), ADS/JAO.ALMA#2012.1.00056.S (observations of H$_2$O and CH in May 2014), ADS/JAO.ALMA#2013.1.00020.S (observations of H$_2$O, CH, H$_2^{18}$O, and H$_2^{17}$O in July 2014), ADS/JAO.ALMA#2015.1.00075.S (2016 monitoring of H$_2$O and CH), ADS/JAO.ALMA#2018.1.00051.S (observations of H$_2^{18}$O in 2019), ADS/JAO.ALMA#2021.A.00028.S (observations of H$_2^{18}$O and H$_2^{17}$O in 2022)." (Summary and conclusions)
- Products in archive: _not stated_
- Missing: Exact spectral channel masks used for continuum baseline and spectral index fitting
- Missing: Initial guesses and priors for the MCMC continuum model fit
- Missing: Initial parameters and bounds for the 10-component Gaussian hyperfine fits to CH/13CH and 3-9 component fits to H2O isotopologs
- Data volume (inferred): ~50-150 GB of raw ALMA visibilities across 6 projects (17 short Band 7 executions in 2015.1.00075.S plus 7 executions in complementary projects)
- Score (inferred): 8/5, All ALMA project codes, calibration settings (CASA 4.7.2, 10s phase self-cal, calibrators), visibility fitting tool (UVMultiFit), PCA tool (scikit-learn), spectroscopic constants (Table A.1), and per-visit intermediate measurements (Table 1) are explicitly provided; only minor fitting priors and channel masks are omitted.
- Rediscovery candidate: yes, All six ALMA datasets are public, visibility modeling with UVMultiFit is straightforward for two point sources, and the main results (flux ratios, PCA periods, 12CH/13CH = 150 +/- 10, 16O/18O = 65.3 +/- 0.7, 18O/17O = 11.5 +/- 0.5, and time delay 25 +/- 3 days) are crisp numeric targets.

## Links

- Method: (cite: mar14) (UVMultiFit visibility fitting software used to extract flux densities, flux ratios, and spectra of the two lensed images)
- Method: (cite: mar15; mar16; mar19) (Differential polarimetry method and R_pol definition for dual-polarization ALMA data)
- Method: (cite: che17) (Von Neumann randomness estimator for time-delay measurement)
- Method: (cite: ped11) (scikit-learn package used for Principal Component Analysis)
- Companion: (cite: mul14) (Earlier 2012 ALMA observations of H2O and CH absorption toward PKS 1830-211)
- Companion: (cite: mul20b) (ALMA lensing model and detection of the third lensed image of PKS 1830-211)
- Companion: (cite: mar20) (ALMA continuum and polarimetric study of the 2019 flare of PKS 1830-211)
- Companion: (cite: mul20a) (ALMA study of deuterated species during the 2019 flare)

## Checks

```json
{
 "quotes": 141,
 "quotes_ok": 141,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 38,
 "unsupported_facts": 0,
 "project_codes": 6,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 99,
  "stated": 76,
  "rate": 0.768
 },
 "evidence_ok": true
}
```
