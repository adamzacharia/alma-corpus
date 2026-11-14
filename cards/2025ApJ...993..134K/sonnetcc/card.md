# A New Precise Measurement of the Cosmic Microwave Background Radiation Temperature at z = 0.89 toward PKS1830─211

`2025ApJ...993..134K` | The Astrophysical Journal 2025 | first author: Kotani, Tatsuya | arXiv: 2509.20760 | DOI: 10.3847/1538-4357/ae0a1e

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: cosmology, agn_and_quasars
- Question: What is the CMB temperature at z = 0.89, measured from HCN absorption (J=2–1 to 5–4) toward PKS1830–211 SW, and is it consistent with the standard Big Bang model?  
  > "we analyzed millimeter-wave data toward the quasar PKS1830–211 observed with the Atacama Large Millimeter/submillimeter Array to obtain absorption spectra of HCN" (abstract); "this is highly consistent with that expected from the standard model of the universe." (abstract)
- Target **PKS1830–211 SW (lensed quasar, absorber at z=0.88582)**: coordinates _not stated_; z/distance absorber z = 0.88582 (quasar z = 2.507)  
  > "This absorption line system is attributed to an almost face-on spiral galaxy in the foreground" (Introduction); "The redshift of the absorber ($z\!=\!0.88582$) corresponds to the systemic velocity of $V_\mathrm{sys}\!=\!1.6820\!\times\!10^{5}$ $\mathrm{km\,s^{-1}}$." (Data Processing); distance from Wiklind_1996 (absorber), Lidman_1999 (quasar), as cited in Introduction  
  > "This absorption line system is attributed to an almost face-on spiral galaxy in the foreground" (Introduction); "The redshift of the absorber ($z\!=\!0.88582$) corresponds to the systemic velocity of $V_\mathrm{sys}\!=\!1.6820\!\times\!10^{5}$ $\mathrm{km\,s^{-1}}$." (Data Processing)

## Data provenance

- ALMA projects: 2013.1.01099.S, 2017.1.01119.S, 2018.1.00051.S, 2018.1.00692.S
- bands: ALMA bands 3–6 (band 4 included)  
  > "We retrieved ALMA bands 3–6 data toward PKS1830–211 from the ALMA Science Archive" (Data Processing)
- frequencies and spectral setup: spectral windows of 1.9 GHz (0.94 GHz for band 4) containing the HCN J=2–1, 3–2, 4–3, 5–4 absorption lines; velocity resolutions 2.672, 1.179, 1.561, 2.728 km/s  
  > "task in CASA to extract spectral windows with bandwidths of 1.9 GHz (0.94 GHz for band 4) that include the HCN absorption lines" (Data Processing); "The resulting velocity resolutions are 2.672, 1.179, 1.561, and 2.728 $\mathrm{km\,s^{-1}}$ for the HCN $J$=2–1, $J$=3–2, $J$=4–3, and $J$=5–4 transitions, respectively." (Data Processing)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: multiple epochs 2014–2019; HCN J=4–3 on July 28 (2019) and J=5–4 on April 11, 2019  
  > "The ALMA data used in this study span multiple epochs between 2014 and 2019." (Time Variability); "spectra were observed on July 28 and April 11, 2019, respectively" (Time Variability)
- pi or archival as stated: archival data from ALMA Science Archive; PIs Kawaguchi, Wallström, Muller, Martí-Vidal  
  > "Project codes of the datasets used are 2013.1.01099.S (PI: K. Kawaguchi), 2017.1.01119.S (PI: S. Wallström), 2018.1.00051.S (PI: S. Muller), and 2018.1.00692.S (PI: I. Martí-Vidal)." (Data Processing)
- Line: HCN J=2–1, J=3–2, J=4–3, J=5–4 (not stated)
- External data: Present-day CMB temperature T0 = 2.72548 ± 0.00057 K  
  > "where $T_0$ ($=2.72548\pm0.00057\,\mathrm{K}$; (cite: Fixsen_2009)) represents the current CMB temperature." (Introduction) [from Fixsen 2009 (cite: Fixsen_2009)]
- External data: Previous best T_CMB(z=0.89) = 5.08 ± 0.10 K from ATCA molecular absorption  
  > "(cite: Muller_2013) determined $T_\mathrm{CMB}(z\!=\!0.89)\!=\!5.08\pm 0.10 \,\mathrm{K}$ (errors are at 68% confidence level) using the 10 different molecular absorption line spectra" (Introduction) [from Muller et al. 2013 (cite: Muller_2013)]
- External data: Absorber density n_H2 ~ 2600 cm^-3 and kinetic temperature T_kin ~ 80 K (used to argue collisions are negligible)  
  > "The density and kinetic temperature of the PKS1830–211 SW absorber are estimated to be $n_\mathrm{H_2}\!\sim\!{2600}\,\mathrm{cm^{-3}}$ (cite: Henkel_2009) and $T_\mathrm{kin}\!\sim\!{80 \,\mathrm{K}}$ (cite: Henkel_2008), respectively." (TCMB Calculations) [from Henkel et al. 2009 (cite: Henkel_2009); Henkel et al. 2008 (cite: Henkel_2008)]
- External data: Covering factor range 0.91–0.97 from saturated line bottoms  
  > "The value of $f_\mathrm{c}$ in SW is evaluated from the bottoms of saturated absorption lines, which ranges from 0.91–0.97 (cite: Muller_2014; Muller_2016; Muller_2017) with no widely accepted value yet." (Continuum Covering Factor) [from Muller_2014; Muller_2016; Muller_2017]
- External data: Flare-epoch variability of absorption (integrated optical depth of blueshifted component up by factor two) used as proxy for HCN J=4–3 and 5–4  
  > "(cite: Muller_2020) reported a flare event of PKS1830–211 over this period, which is considered to be responsible for the observed variations." (Time Variability) [from Muller et al. 2020 (cite: Muller_2020)]
- External data: Lognormal column-density PDF parameters from Orion A  
  > "The parameters of N-PDF determined in the Orion A giant molecular cloud (cite: Ma_2020) were employed for our calculation" (Correction of Non-Uniformity) [from Ma et al. 2020 (cite: Ma_2020)]
- External data: Collisional rate coefficients for RADEX test (appendix only)  
  > "Collisional rate coefficients were taken from the Leiden Atomic and Molecular Database (cite: Schoier_2005)." (Appendix: RADEX Output Behavior) [from Schöier et al. 2005 (cite: Schoier_2005)]
- External data: About 80 literature T_CMB(z) measurements plotted and fitted with the new point  
  > "The results from about 80 measurements of $T_\mathrm{CMB}(z)$ (cite: Battistelli_2002; Luzzi_2009; Muller_2013; Klimenko_2020; Riechers_2022) were plotted with that from this study." (Redshift Dependence of TCMB) [from Battistelli_2002; Luzzi_2009; Muller_2013; Klimenko_2020; Riechers_2022]
- External data: Riechers et al. beta = (3.4 +8.1/-7.3)e-3 for comparison  
  > "complementary to the recent value of $\beta=(3.4^{+8.1}_{-7.3})\times10^{-3}$ reported by (cite: Riechers_2022)" (Redshift Dependence of TCMB) [from Riechers et al. 2022 (cite: Riechers_2022)]
- Simulation/model as data: Lognormal N-PDF model used to correct observed optical depth to real optical depth (Figure 1 relation)  
  > "Assuming the lognormal probability distribution function for column density (N-PDF), we calculated the correction factor between the observed optical depth" (Correction of Non-Uniformity)

## Processing

### Calibration

- pipeline or manual: standard CASA procedure (pipeline vs manual not specified)  
  > "Data calibration and reduction were performed by the standard procedure within the CASA reduction package" (Data Processing)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1924–2914 or J2000–1748 (bandpass and flux); J1832–2039 (phase)  
  > "Quasars J1924–2914 or J2000–1748 were used for calibrating the bandpass and flux, and J1832–2039 was used for phase calibration." (Data Processing)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: no imaging; spectra extracted from visibilities with UVMULTIFIT after CASA mstransform  
  > "The spectra toward both NE and SW components of PKS1830–211 were extracted by the Python-based package $\texttt{UVMULTIFIT}$ (cite: MartiVidal_2014)." (Data Processing)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum handled by fitting delta-function visibility models per channel; peak positions fitted excluding absorption channels  
  > "to all visibilities except for frequency channels where the absorption lines are visible" (Data Processing)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: spectra resampled onto the J=5–4 velocity grid (2.728 km/s)  
  > "Absorption spectra were resampled onto the velocity grid of the" (Excitation Temperature Profile)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Spectrum extraction method (UVMULTIFIT point-source visibility fitting)  
  > "The spectra toward both NE and SW components of PKS1830–211 were extracted by the Python-based package $\texttt{UVMULTIFIT}$ (cite: MartiVidal_2014)." (Data Processing) [from (cite: MartiVidal_2014)]
- Assumption T_CMB = T_ex (CMB-dominated excitation of polar molecules)  
  > "The analyses in this study follow this as well." (TCMB Calculations) [from (cite: Wiklind_1996; Menten_1999)]
- Initial values for fit: T_CMB = 5.14 K and N = 3.041e14 cm^-2  
  > "were set to the standard Big Bang model prediction of $T_\mathrm{CMB}(z = 0.89) = 5.14\,\mathrm{K}$ and $N = 3.041 \times 10^{14}\,\mathrm{cm^{-2}}$, as reported by (cite: Muller_2011)" (Excitation Temperature Profile) [from (cite: Muller_2011)]
- Variability of HCN J=4–3 and 5–4 optical depth during flare adopted from optically thin lines  
  > "Based on the results of (cite: Muller_2020), the integrated optical depth derived from our flare-epoch HCN" (Time Variability) [from (cite: Muller_2020)]
- Column-density PDF parameters for non-uniformity correction  
  > "The parameters of N-PDF determined in the Orion A giant molecular cloud (cite: Ma_2020) were employed for our calculation" (Correction of Non-Uniformity) [from (cite: Ma_2020)]
- T_CMB(z) model relation T0(1+z)^(1-beta)  
  > "was fitted by the model relationship (cite: Lima_2000)" (Redshift Dependence of TCMB) [from (cite: Lima_2000)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration pipeline vs manual and CASA version for each of the four projects
- Exact execution blocks, spectral window IDs and scheduling blocks used from each project
- Whether calibration products from the archive were used as-is or re-run
- UVMULTIFIT settings (model parameters, flux starting values, weighting, per-channel fit options) and fitted positions
- Handling of continuum level I_c and its per-channel uncertainty used in optical depth
- Rest frequencies and molecular constants (A coefficients, level energies, partition function) for HCN
- Hyperfine structure treatment of HCN lines
- Numerical lognormal N-PDF parameters (mean, dispersion) and the exact tau_obs to tau_real function
- Weights and exact weighted least-squares implementation, including how the 5.14 K start and N start were used
- How the upper/lower asymmetric Tex errors from Monte Carlo were combined with systematic term
- Exact velocity bins used in the weighted mean and how the +-0.06 K error was formed
- Data and fitting procedure for the beta fit (selection of about 80 literature points, fitter)
- Random seed and Monte Carlo implementation details

## Analysis recipe

1. **Calibrate archival ALMA data**: standard CASA calibration with bandpass/flux calibrators J1924–2914 or J2000–1748 and phase calibrator J1832–2039  
  > "Data calibration and reduction were performed by the standard procedure within the CASA reduction package" (Data Processing); "Quasars J1924–2914 or J2000–1748 were used for calibrating the bandpass and flux, and J1832–2039 was used for phase calibration." (Data Processing)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract and regrid spectral windows around HCN**: mstransform to select spw with 1.9 GHz (0.94 GHz band 4) bandwidth, barycentric frame, regrid to the minimum velocity resolution in the archive  
  > "task in CASA to extract spectral windows with bandwidths of 1.9 GHz (0.94 GHz for band 4) that include the HCN absorption lines" (Data Processing); "task, which regridded the spectral axis to match the minimum velocity resolution specified in the ALMA archive" (Data Processing)
   - software: CASA mstransform
   - parameter: velocity resolutions 2.672, 1.179, 1.561, 2.728 km/s for J=2–1, 3–2, 4–3, 5–4  
  > "The resulting velocity resolutions are 2.672, 1.179, 1.561, and 2.728 $\mathrm{km\,s^{-1}}$ for the HCN $J$=2–1, $J$=3–2, $J$=4–3, and $J$=5–4 transitions, respectively." (Data Processing)
   - fitting: _not stated_
   - validation: _not stated_
3. **Extract NE and SW spectra from visibilities**: UVMULTIFIT: fit two 2D delta functions to line-free visibilities for positions, then at fixed positions per channel; SW spectrum used  
  > "to all visibilities except for frequency channels where the absorption lines are visible" (Data Processing); "at fixed positions to the visibilities of each spectral channel for obtaining the spectra" (Data Processing)
   - software: UVMULTIFIT
   - fitting: two two-dimensional delta-function point sources fitted to visibilities  
  > "at fixed positions to the visibilities of each spectral channel for obtaining the spectra" (Data Processing)
   - validation: _not stated_
4. **Convert frequency to velocity offset**: relativistic Doppler relation with absorber z=0.88582 as V_sys  
  > "The frequency in the obtained spectrum was converted to the radial velocity using the relativistic Doppler relationship" (Data Processing)
   - parameter: V_sys = 1.6820e5 km/s for z = 0.88582  
  > "The redshift of the absorber ($z\!=\!0.88582$) corresponds to the systemic velocity of $V_\mathrm{sys}\!=\!1.6820\!\times\!10^{5}$ $\mathrm{km\,s^{-1}}$." (Data Processing)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compute optical depth per channel with covering-factor Monte Carlo**: tau = -ln(1 - (1/fc) DeltaI/Ic); Monte Carlo over fc and observed intensity, median and 1 sigma interval adopted  
  > "We employed a Monte Carlo approach to rigorously assess these uncertainties." (Continuum Covering Factor); "This process was repeated 100,000 times to construct the probability distribution of the optical depth." (Continuum Covering Factor)
   - parameter: fc uniform over 0.90–1.00; 100,000 draws per velocity bin and transition  
  > "follows a uniform distribution over the range 0.90–1.00" (Continuum Covering Factor); "This process was repeated 100,000 times to construct the probability distribution of the optical depth." (Continuum Covering Factor)
   - parameter: observed intensity normal with mean = observed value and sigma = its uncertainty  
  > "follows a normal distribution characterized by the observed value as its mean and the associated uncertainty as its standard deviation" (Continuum Covering Factor)
   - assumption: one uniform cloud overlapping the quasar line of sight  
  > "We assume one uniform cloud overlapping in the foreground on the quasar line of sight." (Fundamentals)
   - fitting: Monte Carlo sampling, uniform prior on fc and Gaussian on intensity  
  > "follows a normal distribution characterized by the observed value as its mean and the associated uncertainty as its standard deviation" (Continuum Covering Factor)
   - validation: _not stated_
6. **Add systematic uncertainty for flare-epoch variability in HCN J=4–3 and 5–4**: assign downward systematic uncertainty of 0.5 S_i to integrated optical depth in V_bar = -10 to 0 km/s; upward error purely statistical  
  > "We therefore assigned a systematic downward uncertainty to the integrated optical depth in the velocity range" (Time Variability); "The upward uncertainty was taken to be purely statistical." (Time Variability)
   - parameter: sigma_sys,i = 0.5 S_i; total downward = sqrt(sigma_sta^2 + sigma_sys^2)  
  > "we adopted a systematic uncertainty of $\sigma_{\mathrm{sys},i}=0.5S_i$" (Time Variability)
   - assumption: flare-induced variability in optically thin lines (Muller 2020) is a proxy for HCN J=4–3 and 5–4; optical depth could decrease by about a factor of two in quiescence  
  > "we adopted this variability, observed in the optically thin molecular lines, as a proxy for potential flare-induced variability in these transitions" (Time Variability)
   - fitting: _not stated_
   - validation: _not stated_
7. **Correct optical depth for non-uniform column density**: lognormal N-PDF with Orion A parameters gives tau_obs to tau_real relation (Figure 1), applied to all data points  
  > "The parameters of N-PDF determined in the Orion A giant molecular cloud (cite: Ma_2020) were employed for our calculation" (Correction of Non-Uniformity); "This correction of non-uniformity was applied to all data points." (Correction of Non-Uniformity)
   - assumption: Orion A N-PDF applicable because its average column density is comparable to the z=0.89 absorber  
  > "because its average column density ($N({\rm H}_2)\!\simeq\! 1.5\!\times\! 10^{22}\,{\rm cm}^{-2}$) is comparable to that of the $z\!=\!0.89$ absorber" (Correction of Non-Uniformity)
   - fitting: _not stated_
   - validation: _not stated_
8. **Fit excitation temperature profile per velocity bin**: weighted least-squares fit of the LTE optical-depth relation to optical depths, using only tau < 1; Tex and N free  
  > "were determined by the weighted least-squares-fitting of equation" (Excitation Temperature Profile); "Only optical depths lower than unity—where photon trapping and collisional excitation are expected to be negligible" (Excitation Temperature Profile)
   - software: SciPy
   - parameter: initial T_CMB = 5.14 K, N = 3.041e14 cm^-2; spectra resampled to 2.728 km/s grid  
  > "were set to the standard Big Bang model prediction of $T_\mathrm{CMB}(z = 0.89) = 5.14\,\mathrm{K}$ and $N = 3.041 \times 10^{14}\,\mathrm{cm^{-2}}$, as reported by (cite: Muller_2011)" (Excitation Temperature Profile)
   - assumption: LTE, CMB-dominated excitation, negligible collisions, T_CMB = T_ex  
  > "Assuming local thermodynamic equilibrium and neglecting molecular collisions" (abstract)
   - fitting: weighted least squares; asymmetric 68% intervals from the Monte Carlo sampling; standard error = average of upper and lower bounds  
  > "are asymmetric and correspond to the 68% confidence intervals derived from the Monte Carlo sampling" (Excitation Temperature Profile)
   - validation: _not stated_
9. **Average Tex over the most reliable velocity range to get T_CMB**: inverse-variance weighted mean of Tex for the central component (-12 to +13 km/s)  
  > "we regard the temperatures obtained for the $-3$ to $+3\,\mathrm{km\,s^{-1}}$ component ($-12 \leq V_{\mathrm{bar}} \leq +13\,\mathrm{km\,s^{-1}}$ ) as the most reliable estimate of the CMB temperature" (Excitation Temperature Profile); "by taking a weighted average of calculated excitation temperatures" (abstract)
   - assumption: central component chosen because J=2–1 and 3–2 are saturated, constraining fc to 0.9–1.0, while the -13 and +17 km/s components are unconstrained  
  > "By contrast, the $-13\,\mathrm{km\,s^{-1}}$ and $+17\,\mathrm{km\,s^{-1}}$ components show no saturation, leaving their covering factors unconstrained and the derived excitation temperatures uncertain." (Excitation Temperature Profile)
   - fitting: _not stated_
   - validation: compared with the 5.14 K value expected from the standard Big Bang model and the previous 5.08 ± 0.10 K  
  > "This is in good agreement with the value ($5.14 \,\mathrm{K}$) expected from the standard Big Bang model within the uncertainty." (Redshift Dependence of TCMB)
10. **Constrain deviation from standard model (beta)**: fit T_CMB(z) = T0 (1+z)^(1-beta) to about 80 literature measurements plus this result  
  > "was fitted by the model relationship (cite: Lima_2000)" (Redshift Dependence of TCMB); "The results from about 80 measurements of $T_\mathrm{CMB}(z)$ (cite: Battistelli_2002; Luzzi_2009; Muller_2013; Klimenko_2020; Riechers_2022) were plotted with that from this study." (Redshift Dependence of TCMB)
   - fitting: _not stated_
   - validation: compared with Riechers et al. 2022 beta  
  > "complementary to the recent value of $\beta=(3.4^{+8.1}_{-7.3})\times10^{-3}$ reported by (cite: Riechers_2022)" (Redshift Dependence of TCMB)

## Software

- **CASA** : data calibration and reduction (including mstransform)  
  > "Data calibration and reduction were performed by the standard procedure within the CASA reduction package" (Data Processing)
- **mstransform** : extract spectral windows, set barycentric frame, regrid to archive velocity resolution  
  > "task, which regridded the spectral axis to match the minimum velocity resolution specified in the ALMA archive" (Data Processing)
- **UVMULTIFIT** : extract NE and SW spectra from visibilities  
  > "The spectra toward both NE and SW components of PKS1830–211 were extracted by the Python-based package $\texttt{UVMULTIFIT}$ (cite: MartiVidal_2014)." (Data Processing)
- **RADEX** : examined for non-LTE analysis but not adopted (appendix test)  
  > "Another powerful approach to constraining the CMB temperature is non-LTE analysis with the RADEX code (cite: vanderTak_2007)." (TCMB Calculations)
- **Matplotlib** : _not stated_
- **NumPy** : _not stated_
- **SciPy** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| T_CMB at z=0.89 (weighted mean Tex) | 5.13 | ±0.06 | K | 9 | The final value obtained is $\left<T_{\rm ex} \right>\!=\!5.13\pm0.06\,\mathrm{K}$ |
| beta in T_CMB(z)=T0(1+z)^(1-beta) | 3.2e-3 | +7.5e-3/-8.4e-3 | dimensionless | 10 | which yields ${\beta=(3.2^{+7.5}_{-8.4})\times10^{-3}}$ |
| Continuum covering factor for central two components | 0.91–0.92 | not stated | dimensionless | 5 | The values of these saturated bottoms provide the continuum covering factor of $f_{\rm c}\!=\!0.91\mbox{--}0.92$ for the central two components. |
| Absorption component velocity centers | -13, -3, +3, +17 | not stated | km/s | 3 | We clearly see at least four components centered at $V_{\rm bar}\!=\! -13$, $-3$, $+3$, and $+17\,\mathrm{km\,s^{-1}}$. |
| Reduction in T_CMB uncertainty relative to Muller et al. 2013 | ~40 | not stated | % | 9 | The uncertainty is reduced by $\sim\!40$% relative to the previous best estimate of (cite: Muller_2013). |

## Qualitative findings

- HCN J=2–1 and J=3–2 are saturated at the two central components, so their optical depths are highly uncertain  
  > "The *J*=2–1 and *J*=3–2 absorption profiles of the central two components are fully saturated at each velocity center" (Optical Depth Profiles)
- RADEX in the optically thin limit gives Tex rising with J above T_CMB, contradicting basic radiative transfer, so non-LTE RADEX analysis was not used  
  > "This behavior is inconsistent with basic radiative transfer in the optically thin limit, particularly at higher" (Appendix: RADEX Output Behavior)

## Claim tuples

- H: Does the CMB temperature at z=0.89 follow the standard T0(1+z) prediction of 5.14 K? | E: Weighted mean of HCN-derived excitation temperatures from ALMA absorption spectra toward PKS1830–211 SW over -12 to +13 km/s | R: T_CMB = 5.13 ± 0.06 K | F: Consistent with the standard Big Bang model value 5.14 K | **supported**
- H: Can a more precise T_CMB(z=0.89) be obtained than the previous best (5.08 ± 0.10 K) using a few high-S/N HCN lines with careful covering factor, variability and non-uniformity treatment? | E: Optical depth profiles with Monte Carlo covering factor, flare systematic term and N-PDF correction, followed by Tex fitting | R: Uncertainty reduced by about 40% relative to Muller et al. 2013 | F: New value is the most precise at this redshift | **supported**
- H: Does the compiled T_CMB(z) data set deviate from T0(1+z)^(1-beta) with beta different from 0? | E: Fit of about 80 literature measurements plus this one with the Lima et al. 2000 relation | R: beta = (3.2 +7.5/-8.4)e-3 | F: Measurements remain compatible with the standard Big Bang model | **supported**
- H: Is RADEX non-LTE analysis a reliable alternative for the optically thin HCN lines? | E: RADEX runs over n_H2 = 1e2–1e4 cm^-3 and N/dV = 1e11–1e13, T_CMB = 5.14 K, T_kin = 80 K | R: Tex rises systematically with J for J≥4 even at tau << 1e-3 | F: RADEX unreliable in this regime; not used | **supported**

## Reasoning

- Why this data: only four high-S/N HCN spectra used to minimize uncertainty  
  > "Only four HCN spectra with high signal-to-noise ratio were used in the analysis to minimize uncertainty" (Introduction)
- Why this method: more species would add uncertain physical parameters without necessarily improving accuracy; opaque species with per-channel optical depth used instead of velocity-integrated optically thin lines  
  > "Increasing the number of molecular species used in the analysis does not necessarily improve accuracy because it increases the number of uncertain physical parameters." (Introduction); "In this study, we took a different approach, employing an opaque species, evaluating optical depths at each velocity channel, and taking a weighted mean of the calculated" (Optical Depth Profiles)
- Alternative: Non-LTE analysis with RADEX not adopted because of anomalous optically thin behaviour at higher J  
  > "Therefore, we did not adopt non-LTE analysis based on RADEX calculations in the present study." (Appendix: RADEX Output Behavior)
- How they decided it was enough: _not stated_
- Limitation (authors): Time variability and covering factors in multiple subcomponents of the HCN spectra cannot yet be quantified directly  
  > "Direct quantification of uncertainties associated with temporal variability and covering factors in the multiple subcomponents of the HCN spectra remains a key challenge for future studies." (Summary and Future Prospects)
- Limitation (authors): Components at -13 and +17 km/s show no saturation so covering factors are unconstrained  
  > "leaving their covering factors unconstrained and the derived excitation temperatures uncertain" (Excitation Temperature Profile)
- Limitation (authors): No pre-flare HCN J=4–3 and 5–4 profiles exist; variability taken from other molecules as proxy  
  > "we adopted this variability, observed in the optically thin molecular lines, as a proxy for potential flare-induced variability in these transitions" (Time Variability)
- Caveat (inferred, ours): Excitation temperature equals T_CMB assumption relies on literature density and kinetic temperature, not tested here
- Caveat (inferred, ours): Flare variability factor of two comes from other molecules and is applied as a fixed 0.5 S_i term
- Caveat (inferred, ours): Orion A N-PDF borrowed for a cosmological absorber with no direct check
- Caveat (inferred, ours): Final T_CMB only uses the central component; choice of velocity range could bias result
- Caveat (inferred, ours): Covering factor prior of 0.90–1.00 is uniform and fixed, though fc varies with time and frequency
- Caveat (inferred, ours): Four datasets from different epochs and instrument setups combined without cross-calibration check stated
- Caveat (inferred, ours): Tension between RADEX anomaly and LTE assumption is dismissed rather than resolved

## Reproducibility

- Data public (paper): data retrieved from the ALMA Science Archive with project codes listed  
  > "We retrieved ALMA bands 3–6 data toward PKS1830–211 from the ALMA Science Archive" (Data Processing)
- Products in archive: _not stated_
- Missing: CASA version and calibration route
- Missing: UVMULTIFIT configuration details
- Missing: Numerical N-PDF correction function
- Missing: Molecular constants and partition function inputs
- Missing: Weighting and bin selection for the final weighted mean
- Missing: Beta fit implementation and data table of 80 measurements
- Data volume (inferred): Four archival band 3–6 projects; visibilities of a bright point-like quasar with 1.9 GHz spectral windows, likely tens to a few hundred GB raw, much less after spw extraction
- Score (inferred): 3/5, Public archival data and clear statistical recipe with a headline number, but CASA version, UVMULTIFIT setup, N-PDF parameters and averaging details are not given.
- Rediscovery candidate: no, Data are public and the result is numeric (5.13 ± 0.06 K), but key inputs (N-PDF correction function, UVMULTIFIT settings, bin weighting, molecular constants) are not given, so the recipe is not complete enough to redo.

## Links

- Method: Martí-Vidal et al. 2014 (cite: MartiVidal_2014) (UVMULTIFIT visibility-fitting package used to extract spectra)
- Method: Muller et al. 2013 (cite: Muller_2013) (previous best T_CMB(z=0.89) with ATCA molecular absorption lines; method contrasted with this study)
- Method: Muller et al. 2020 (cite: Muller_2020) (flare-epoch variability of absorption used for systematic uncertainty)
- Companion: Muller et al. 2013 (cite: Muller_2013) (earlier T_CMB measurement toward the same absorber)
- Companion: Riechers et al. 2022 (cite: Riechers_2022) (recent beta constraint compared with this result)
- Related: 2013.1.01099.S
- Related: 2017.1.01119.S
- Related: 2018.1.00051.S
- Related: 2018.1.00692.S

## Checks

```json
{
 "quotes": 99,
 "quotes_ok": 99,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 113,
  "stated": 67,
  "rate": 0.593
 },
 "evidence_ok": true
}
```
