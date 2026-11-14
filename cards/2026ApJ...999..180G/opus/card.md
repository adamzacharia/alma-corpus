# ATOMS-QUARKS Survey: Inflow and Infall in Massive Protocluster G318.049+00.086— Evidence of Competitive Accretion

`2026ApJ...999..180G` | The Astrophysical Journal 2026 | first author: Gupta, Shivani | arXiv: 2602.01238 | DOI: 10.3847/1538-4357/ae40fd

Card schema 1.0 | model claude-opus-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: What are the multi-scale gas dynamics (filament inflow and core infall) in protocluster G318.049+00.086, and which massive star formation theory do they support?  
  > "In this paper, we studied the multi-scale gas dynamics of a massive protocluster (G318.049+00.086) that has reported evidence of the presence of multiple filaments and several prestellar and protostellar cores to understand the underlying star formation mechanism." (Introduction)
- Target **G318.049+00.086 (I14498-5856)**: coordinates _not stated_; z/distance 2.90 (+0.52/-0.47) kpc; V_lsr = -49.82 km/s  
  > "The protocluster G318.049+00.086, also known as I14498-5856, is located at a distance of 2.90$^{+0.52}_{-0.47}$ kpc (cite: 2019ApJ...885..131R)" (Selected region); distance from (cite: 2019ApJ...885..131R)  
  > "The protocluster G318.049+00.086, also known as I14498-5856, is located at a distance of 2.90$^{+0.52}_{-0.47}$ kpc (cite: 2019ApJ...885..131R)" (Selected region)

## Data provenance

- ALMA projects: 2019.1.00685.S, 2017.1.00545.S
- bands: 3 mm (ATOMS), ~345 GHz / 870 μm (ASSEMBLE), 1.3 mm (QUARKS)  
  > "The 3 mm ($\sim$99.93 GHz) dust continuum map having a beam size of 2.34$^{\prime\prime}$ $\times$ 2.16$^{\prime\prime}$ is constructed using data from line-free spectral channels." (ATOMS survey); "The corresponding 1.3 mm dust continuum map is prepared from the available line-free spectral channels (cite: 2024RAA....24b5009L)." (QUARKS survey)
- frequencies and spectral setup: Spectral resolution 0.422 (H13CO+), 0.419 (CCH), 2.973 (CS) km/s in ATOMS; 0.98 km/s in ASSEMBLE  
  > "In this study, we utilized the H$^{13}$CO$^{+}$ (1–0), CCH F(2–1), and CS (2–1) transitions, with spectral resolutions of 0.422 km s$^{-1}$, 0.419 km s$^{-1}$, and 2.973 km s$^{-1}$, respectively." (ATOMS survey); "were employed to determine the core systemic velocity, with a spectral resolution of 0.98 km s$^{-1}$" (ASSEMBLE survey)
- continuum bandwidth: _not stated_
- arrays: ATOMS: 12-m + ACA; ASSEMBLE: 12 m only; QUARKS: 12 m + 7 m (ACA)  
  > "as the ASSEMBLE data include only the 12 m array, whereas the QUARKS data combine the 12 m and 7 m arrays, enabling better recovery of extended emission." (Selected region); "Calibration of the 12-m array data and ACA data were done separately" (ATOMS survey)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 3 mm continuum 2.34" x 2.16"; H13CO+ 2.66" x 2.52"; ASSEMBLE ~1.1" x 0.8"; QUARKS 1.3 mm 0.40" x 0.34" (~0.3")  
  > "complementing the ATOMS survey with an improved angular resolution ($\sim$ 0.3$^{\prime\prime}$)." (QUARKS survey); "H$^{13}$CO$^{+}$ | (1–0) | 86.754288 | 0.422 | 2.66 $\times$ 2.52 | 11.1" (Table 1); "| mm continuum | $\cdots$ | $\cdots$ | $\cdots$ | 0.40 $\times$ 0.34 |" (Table 1)
- max recoverable scale: ~87" (ATOMS 12m+ACA); ~8.45" (ASSEMBLE); ~8.45" (QUARKS combined)  
  > "The maximum recoverable scale (MRS) of 12m + ACA combine data reaches $\sim$ 87$^{\prime\prime}$ (cite: 2023MNRAS.520.3259X)." (ATOMS survey); "The MRS of this data is $\sim$ 8.45$^{\prime\prime}$ (cite: 2023MNRAS.520.3259X)." (ASSEMBLE survey); "The combine data has MRS of $\sim$ 8.45$^{\prime\prime}$ (cite: 2024RAA....24f5011X)." (QUARKS survey)
- sensitivity: line rms 11.1 mJy/beam (H13CO+), 11.3 (CCH), 5.0 (CS), ~6.3-6.5 (ASSEMBLE lines); spectral rms 0.27 K  
  > "CCH | (1–0) | 87.316898 | 0.419 | 2.63 $\times$ 2.50 | 11.3" (Table 1); "The S/N ratio was calculated based on an rms noise level of 0.27 K, estimated from the line-free channels using `FUNStools`." (Gas infall rates in cores)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Survey data (ATOMS, ASSEMBLE PI: Tie Liu; QUARKS)  
  > "(ASSEMBLE; Project ID: 2017.1.00545.S; PI: Tie Liu)" (ASSEMBLE survey)
- Line: H13CO+ (1–0) (86.754288 GHz)
- Line: CCH (1–0), J=3/2–1/2 F(2–1) (87.316898 GHz)
- Line: H13CN (1–0) (86.339918 GHz)
- Line: CS (2–1) (97.980953 GHz)
- Line: CH3OH 13_1,12–13_0,13 (342.729781 GHz)
- Line: H13CN (4–3) (345.339760 GHz)
- External data: 16 dense cores (mass, radius, classification prestellar/protostellar) from ALMA 870 μm map  
  > "In total, they reported the presence of 4 protostellar cores and 12 prestellar core candidates in this protocluster. We adopted these cores in our analyses." (Selected region) [from (cite: 2024ApJS..270....9X)]
- External data: Clump mass 1023.3 Msun and dust temperature 26.7 K  
  > "The mass and dust temperature ($T_{\rm{dust}}$) of the protocluster are 1023.3 M$_{\odot}$ and 26.7 K, respectively (cite: 2018MNRAS.473.1059U)." (Selected region) [from (cite: 2018MNRAS.473.1059U)]
- External data: Distance 2.90 kpc  
  > "is located at a distance of 2.90$^{+0.52}_{-0.47}$ kpc (cite: 2019ApJ...885..131R)" (Selected region) [from (cite: 2019ApJ...885..131R)]
- External data: V_lsr -49.82 km/s and global CO(4–3) infall rate (1.56±0.03)e4 Msun/Myr  
  > "has a local standard of rest velocity (V$_{\rm{lsr}}$) of -49.82 km s$^{-1}$ (cite: 2021RAA....21...14Y)." (Selected region) [from (cite: 2021RAA....21...14Y)]
- External data: CO (3–2) outflows used to classify cores  
  > "based on their association with the bipolar outflows traced in the CO (3–2) line by (cite: 2020ApJ...890...44B)." (Selected region) [from (cite: 2020ApJ...890...44B)]
- External data: H13CO+/H2 abundance range 1e-10 to 1e-12 (mean 1e-11 adopted)  
  > "Thus, we derived the $N(\rm H_{2})$ from $N({\rm H^{13}CO^{+}})$ using the mean of the reported abundance ratio of 10$^{-11}$." (Column density map) [from (cite: 1987ApJ...315..621B; 1987ApJ...313..320F; 2000A&A...355..499G; 2006ApJ...636..261H; 2021A&A...648A.120R; 2024MNRAS.535.1364Z)]
- External data: H13CO+ molecular constants mu = 3.89 D, B = 43.377302 GHz  
  > "we used $J$ = 0, $\mu$ = 3.89 D, and $B$ = 43.377302 GHz" (Column density map) [from (cite: FT9938902219; 1994JChPh.101.8945Y; 2007ApJ...662..771L; 2012ApJ...756...60S)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.6 (ATOMS)  
  > "Calibration of the 12-m array data and ACA data were done separately using the Common Astronomy Software Applications (CASA) package version 5.6 (cite: mcmullin2007asp)" (ATOMS survey)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum maps made from line-free channels  
  > "is constructed using data from line-free spectral channels." (ATOMS survey)
- line free channels: _not stated_
- primary beam correction: all images primary beam corrected  
  > "All the images used in our analysis are primary beam corrected." (ATOMS survey)
- array combination: 12-m and ACA calibrated separately, visibilities combined and re-imaged  
  > "subsequently the visibility data were combined and re-imaged to recover the extended emission." (ATOMS survey)
- smoothing: _not stated_
- final beam: 3 mm cont 2.34"x2.16"; H13CO+ 2.66"x2.52"; CCH 2.63"x2.50"; 1.3 mm cont 0.40"x0.34"  
  > "The 3 mm ($\sim$99.93 GHz) dust continuum map having a beam size of 2.34$^{\prime\prime}$ $\times$ 2.16$^{\prime\prime}$" (ATOMS survey)
- final rms: 11.1 mJy/beam (H13CO+), 11.3 (CCH, H13CN 1–0), 5.0 (CS), 6.5 (CH3OH), 6.3 (H13CN 4–3)  
  > "H$^{13}$CN | (4–3) | 345.339760 | 0.980 | 1.08 $\times$ 0.80 | 6.3" (Table 1)

### Inherited from earlier work

- ATOMS survey and data reduction details  
  > "Further details about the survey and data reduction can be found in (cite: 2020MNRAS.496.2790L)." (ATOMS survey) [from (cite: 2020MNRAS.496.2790L)]
- QUARKS 1.3 mm continuum preparation and ACA observations  
  > "QUARKS also have ACA observations ((cite: 2024RAA....24f5011X), Quarks paper II)." (QUARKS survey) [from (cite: 2024RAA....24b5009L); (cite: 2024RAA....24f5011X)]
- Core catalogue, masses, radii and classification  
  > "where $M_{\rm{in}}$ is the core mass, and $R_{\rm in}$ is the core radius, adopted from (cite: 2024ApJS..270....9X)." (Gas infall rates in cores) [from (cite: 2024ApJS..270....9X)]
- Filament identification in H13CO+ moment-0 with FilFinder, reproduced from previous ATOMS study  
  > "In our analysis, the previously identified filamentary structures were well-reproduced with the same `FilFinder` algorithm." (Identification of filaments) [from (cite: 2022MNRAS.514.6038Z)]
- Mass inflow rate methodology (cylindrical model)  
  > "To quantify the mass flow along the filaments, we followed a similar methodology described in (cite: 2013ApJ...766..115K)." (Mass inflow rate along the filaments) [from (cite: 2013ApJ...766..115K)]
- LTE optically thin column density formula  
  > "it was derived using the formula obtained under the assumption of local thermodynamic equilibrium and the emission is optically thin (cite: 1991ApJ...374..540G)" (Column density map) [from (cite: 1991ApJ...374..540G)]
- Hill5 infall model  
  > "fitting the observed spectral profiles of H$^{13}$CO$^{+}$ and CCH with the Hill5 infall model (cite: 2005ApJ...620..800D)." (Gas infall rates in cores) [from (cite: 2005ApJ...620..800D)]
- Mass infall rate equation  
  > "The estimated infall velocities were further used to derive the mass infall rate ($\dot{M}_{\rm{in}}$) of gaseous material following the equation (cite: 2001ApJS..136..703L; 2022ApJ...940..112K; 2025arXiv251116978M):" (Gas infall rates in cores) [from (cite: 2001ApJS..136..703L; 2022ApJ...940..112K; 2025arXiv251116978M)]
- PV diagram approach along filaments  
  > "To assess for such possibility, we examined the position-velocity (PV) diagram of the filaments (cite: 2022ApJ...940..112K)." (Dynamical properties of filaments) [from (cite: 2022ApJ...940..112K)]

### Not stated but needed to reproduce (our reading)

- QUARKS ALMA project code, spectral setup and line/continuum rms of the 1.3 mm map
- Imaging parameters (weighting/robust, cell size, deconvolver, masks) for all three surveys
- FilFinder parameters (thresholds, beam/distance inputs, branch pruning) for both maps
- Moment-0/moment-1 velocity integration ranges and clipping for H13CO+
- Jy/beam to K conversion and which image (beam) was used for the N(H2) map
- Filament segment endpoints/widths used for mass and least-squares velocity gradient fits
- Apertures used to average core spectra
- Hill5 initial guesses, prior bounds, number of walkers/steps/burn-in in emcee
- Treatment of CCH hyperfine structure in Hill5 fits

## Analysis recipe

1. **identify filaments**: FilFinder applied to H13CO+ moment-0 map and QUARKS 1.3 mm continuum map; skeletons overlaid  
  > "We also employed the `FilFinder` algorithm to the 1.3 mm continuum map obtained in the QUARKS survey, as the continuum emission has good spatial resolution." (Identification of filaments)
   - software: FilFinder
   - fitting: _not stated_
   - validation: Longest filaments from H13CO+ and 1.3 mm coincide; reproduces earlier ATOMS filaments  
  > "We note that the longest filaments obtained from both the emissions strongly coincide with each other." (Identification of filaments)
2. **build H2 column density map**: LTE, optically thin H13CO+ (1–0) column density from integrated intensity, converted with abundance 1e-11  
  > "For the construction of the column density map ($N({\rm H^{13}CO^{+}})$), we considered only the pixels with integrated intensity $>5\sigma$ in the moment-0 map." (Column density map)
   - parameter: >5σ moment-0 mask  
  > "we considered only the pixels with integrated intensity $>5\sigma$ in the moment-0 map." (Column density map)
   - assumption: T_ex = T_dust of clump (26.7 K), constant across region  
  > "In this calculation, we assume that $T_{\rm ex}$ is equal to the dust temperature of the clump ($T_{\rm dust}$)." (Column density map)
   - assumption: [H13CO+/H2] = 1e-11  
  > "While we adopted a representative value of $[\rm{H^{13}CO^+}/\rm{H}_2]=10^{-11}$, reported values span a wide range from $10^{-10}$ to $10^{-12}$." (Column density map)
   - fitting: _not stated_
   - validation: Uncertainty discussion for opacity, temperature and abundance  
  > "A plausible uncertainty of $\pm 10$ K to our adopted value introduces an uncertainty of approximately 33% to 36% in the derived $N(\mathrm{H}_2)$." (Column density map)
3. **measure velocity gradients along filaments**: PV diagrams of H13CO+ centroid velocity along 1.3 mm filament skeletons (grouped F1&F2, F3&F4); least-squares linear fits  
  > "The PV diagrams of the filaments were constructed by determining the centroid velocity along each of these filament skeletons." (Dynamical properties of filaments); "For estimation of the velocity gradients, we performed least-square fits to different parts of the PV diagrams signifying the filaments" (Dynamical properties of filaments)
   - fitting: least-squares; uncertainties from fit errors  
  > "The uncertainties for these gradients are obtained from the error associated with the least-squares fit" (Dynamical properties of filaments)
   - validation: _not stated_
4. **derive filament masses and mass inflow rates**: Filament mass from N(H2) map; Mdot = ∇V M_fil / tan α  
  > "The filament mass was estimated from the H$_{2}$ column density map." (Mass inflow rate along the filaments)
   - parameter: α = 45° (tan α = 1)  
  > "We thus assume $\tan$ $\alpha$ = 1 in our calculation" (Mass inflow rate along the filaments)
   - assumption: simple cylindrical model; distance uncertainty 0.5 kpc  
  > "The uncertainty in $M_{\rm fil}$ is derived by adopting the uncertainty in distance to the protocluster (0.5 kpc) and the standard deviation in H$_{2}$ column density within the filament segment." (Mass inflow rate along the filaments)
   - fitting: _not stated_
   - validation: Factor-of-2 uncertainty for α between 30° and 60°  
  > "the estimated velocity gradients and mass inflow rates are expected to be uncertain by a factor of 2 when the $\alpha$ changes between 30$^{\circ}$ and 60$^{\circ}$ (cite: 2025A&A...704A..64W)." (Mass inflow rate along the filaments)
5. **classify core line profiles and confirm self-absorption**: Inspect H13CO+ and CCH average spectra for blue/red asymmetry; Gaussian fits to optically thin CH3OH and H13CN (4–3) to get core V_lsr  
  > "We fit Gaussians to the average spectra of these optically thin tracers to determine the V$_{\rm lsr}$ of each core." (Gas infall rates in cores)
   - fitting: Gaussian fits  
  > "The optically thin CH$_3$OH (13$_{1,12}$–13$_{0,13}$) line is fitted with a single Gaussian profile to determine the centroid velocity ($\mu$) and velocity dispersion ($\sigma$)" (Spectral profiles of core 5 and core 7)
   - validation: Thin-tracer V_lsr coincides with H13CO+ dip for cores 8, 10, 13  
  > "further confirming that the double-peaked shapes arise from self-absorption and not from multi-component cloud." (Gas infall rates in cores)
6. **fit infall velocities**: Hill5 model fits to averaged H13CO+ and CCH spectra with emcee MCMC, two-stage bounds  
  > "the fitting was performed by Markov Chain Monte Carlo (MCMC) sampling using the `emcee` Python package (cite: 2013ascl.soft03002F)." (Hill5 Model Fit to the Infall Profiles)
   - software: emcee, FUNStools
   - parameter: S/N ≳ 15; rms 0.27 K  
  > "we applied a signal-to-noise (S/N) threshold $\gtrsim$ 15 to the observed spectra." (Gas infall rates in cores)
   - parameter: five free parameters: T_peak, tau, V_infall, V_LSR, sigma  
  > "These five parameters were set as free with initial guesses and bounds to fit the observed spectra with the model." (Hill5 Model Fit to the Infall Profiles)
   - assumption: T_0 = 0 at core edges; equal velocity dispersion in both layers  
  > "The model consists of a core with a peak excitation temperature ($T_{\rm peak}$) at the center and an excitation temperature of $T_{0}=0$ at the near and far edges of the core." (Hill5 Model Fit to the Infall Profiles)
   - fitting: emcee MCMC; broad bounds first trial, refined bounds second trial  
  > "The second trial uses this result to set more reasonable bounds on the parameters for a final fit." (Hill5 Model Fit to the Infall Profiles)
   - validation: Corner plots inspected; consistency between tracers for cores 10, 11, 12  
  > "Note that for cores where V$_{\rm in}$ is derived for both the tracers (cores 10, 11 and 12), the obtained values are found to be consistent with each other." (Gas infall rates in cores)
7. **compute core mass infall rates**: Mdot_in = 3 M_in V_in / R_in with core mass and radius from literature  
  > "where $M_{\rm{in}}$ is the core mass, and $R_{\rm in}$ is the core radius, adopted from (cite: 2024ApJS..270....9X)." (Gas infall rates in cores)
   - fitting: _not stated_
   - validation: _not stated_
8. **assess core mass-radius relation**: Compare cores to m(r) > 870 Msun (r/pc)^1.33 and surface density thresholds 0.05 and 1.0 g cm^-2  
  > "The shaded region represents the area of low-mass star-forming cores that does not satisfy the criteria of m(r) $>$ 870 M$_\odot$ (r/$\mathrm{pc}$)$^{1.33}$ (cite: 2013ApJ...765L..35K)." (M-R relationship of the cores)
   - fitting: _not stated_
   - validation: _not stated_
9. **estimate hub mass accumulation**: Fraction (SFE 20%, also 30%) of filament inflow over 2e4 yr  
  > "With a typical conjecture of mass inflow through the filaments $2 \times 10^4$ years at a constant efficiency of 20%, the additional mass accreted by the hub would rise by 35 M$_\odot$" (Possible evolution of the cores)
   - parameter: SFE 20%; timescale 2e4 yr  
  > "(8) Mass accretion rates assuming an SFE of 20$\%$. (9) Mass gain by the hub in $2\times10^{4}$ years with the adopted SFE." (Table 2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.6: calibration of ATOMS 12-m and ACA data  
  > "Calibration of the 12-m array data and ACA data were done separately using the Common Astronomy Software Applications (CASA) package version 5.6 (cite: mcmullin2007asp)" (ATOMS survey)
- **FilFinder** : filament identification  
  > "by applying the Python-based `FilFinder` algorithm (cite: 2015MNRAS.452.3435K) on the moment-0 map of H$^{13}$CO$^{+}$ emission." (Identification of filaments)
- **FUNStools** : rms noise from line-free channels  
  > "The S/N ratio was calculated based on an rms noise level of 0.27 K, estimated from the line-free channels using `FUNStools`." (Gas infall rates in cores)
- **emcee** : MCMC sampling of Hill5 fits  
  > "the fitting was performed by Markov Chain Monte Carlo (MCMC) sampling using the `emcee` Python package (cite: 2013ascl.soft03002F)." (Hill5 Model Fit to the Infall Profiles)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| N(H2) range | (0.5-4.0)e24 | lower limit | cm^-2 | 2 | Note that the $N$(H$_2$) ranges between (0.5-4.0)$\times$10$^{24}$ cm$^{-2}$ with the highest being at the hub region. |
| F1 mass / line mass / velocity gradient / inflow rate | 99 / 1414 / 17.8 / 1762 | ±33 / ±473 / ±1.1 / ±598 | Msun / Msun pc^-1 / km s^-1 pc^-1 / Msun Myr^-1 | 4 | F1 / 0.07 / 99$\pm$33 / 1414$\pm$473 / 17.8$\pm$1.1 / 1762$\pm$598 |
| F3 mass / line mass / velocity gradient / inflow rate | 227 / 1746 / 22.1 / 5017 | ±76 / ±585 / ±2.0 / ±1735 | Msun / Msun pc^-1 / km s^-1 pc^-1 / Msun Myr^-1 | 4 | F3 / 0.13 / 227$\pm$76 / 1746$\pm$585 / 22.1$\pm$2.0 / 5017$\pm$1735 |
| F4 mass / line mass / velocity gradient / inflow rate | 119 / 992 / 10.9 / 1297 | ±40 / ±333 / ±0.8 / ±445 | Msun / Msun pc^-1 / km s^-1 pc^-1 / Msun Myr^-1 | 4 | F4 / 0.12 / 119$\pm$40 / 992$\pm$333 / 10.9$\pm$0.8 / 1297$\pm$445 |
| Infall velocity range of cores | -0.73 to 1.24 | not stated | km s^-1 | 6 | V$_{\rm in}$ vary from -0.73 to 1.24 km s$^{-1}$ for the cores |
| Core 5 V_in (H13CO+) and mass infall rate | 1.05; 54.9e-5 | +0.12/-0.11; ±35.1e-5 | km s^-1; Msun yr^-1 | 7 | / 5 / 4.0$\pm$2.4 / 4550 / $-$50.61 / 1.05$^{+0.12}_{-0.11}$ / \- / 54.9$\pm$35.1 / |
| Core 7 V_in (CCH) and mass infall rate | 1.24; 196.2e-5 | +0.26/-0.27; ±110.9e-5 | km s^-1; Msun yr^-1 | 7 | / 7 / 9.7$\pm$5.2 / 3680 / $-$50.70 / \- / 1.24$^{+0.26} _{-0.27}$ / \- / 196.2$\pm$110.9 / |
| Core 8 V_in (H13CO+) and mass infall rate | 0.80; 33.1e-5 | +0.16/-0.18; ±19.9e-5 | km s^-1; Msun yr^-1 | 7 | / 8 / 1.0$\pm$0.6 / 1530 / $-$50.18 / 0.80$^{+0.16}_{-0.18}$ / \- / 33.1$\pm$19.9 / |
| Core 9 V_in (H13CO+) and mass infall rate | 1.08; 20.1e-5 | ±0.10; ±11.0e-5 | km s^-1; Msun yr^-1 | 7 | / 9 / 1.0$\pm$0.6 / 3740 / \- / 1.08$^{+0.10}_{-0.10}$ / \- / 20.1$\pm$11.0 / |
| Core 10 V_in (H13CO+) and mass rate (expansion) | -0.16; -68.9e-5 | +0.06/-0.07; ±41.7e-5 | km s^-1; Msun yr^-1 | 7 | / 10 / 6.0$\pm$4.1 / 3360 / $-$49.31 / $-$0.16$^{+0.06}_{-0.07}$ / $-$0.14$^{+0.03}_{-0.03}$ / $-$68.9$\pm$41.7 / $-$46.3$\pm$31.7 / |
| Core 11 V_in (H13CO+) and mass rate (expansion) | -0.73; -39.3e-5 | +0.32/-0.56; ±30.2e-5 | km s^-1; Msun yr^-1 | 7 | / 11 / 1.3$\pm$1.0 / 1530 / \- / $-$0.73$^{+0.32}_{-0.56}$ / $-$0.73$^{+0.18}_{-0.32}$ / $-$39.3$\pm$30.2 / |
| Hub mass gain over 2e4 yr | 35 (SFE 20%); 52.5 (SFE 30%) | not stated | Msun | 9 | the additional mass accreted by the hub would rise by 35 M$_\odot$, while it will increase by 52.5 M$_\odot$ if an efficiency of 30% is assumed. |

## Qualitative findings

- Four filaments (F1-F4) converge on a central hub, forming a hub-filament system  
  > "Filamentary structures are identified using the 1.3 mm dust continuum map, with four of them converge into a dense central region, forming a hub-filament system (HFS)." (abstract)
- Most cores show blue asymmetric profiles; some prestellar candidates (10, 11, 13) show red profiles  
  > "Among the prestellar candidates, cores 3, 12, 15, and 16 show blue profiles, while cores 10, 11, and 13 show red profiles suggestive of expanding gas." (Gas infall rates in cores)
- Hierarchical accretion: ~1e4 Msun/Myr at 0.74 pc, 1e3 at filament scale, 1e2 at core scale  
  > "at larger scales (R $\sim$ 0.74 pc), the accretion rate is on the order of 10$^4$M$_\odot$ Myr$^{-1}$; at filament scales ($\sim$0.3 pc), it drops to 10$^{3}$M$_\odot$ Myr$^{-1}$" (Infall and inflow rates: an overview)
- Core 7 exceeds surface density threshold and 8 Msun limit, candidate massive star  
  > "The protostellar core, Core 7 residing in the hub-region exceeds both the surface density threshold and the 8 M$_{\odot}$ mass limit, making it a potential candidate to evolve into a massive star." (M-R relationship of the cores)

## Claim tuples

- H: Filaments transport gas into the central hub | E: H13CO+ PV diagrams along 1.3 mm filament skeletons, least-squares gradients, cylindrical inflow model | R: Velocity gradients 10.9-22.1 km/s/pc; inflow rates 1297-5017 Msun/Myr | F: Mass inflow onto the hub capable of forming massive stars | **supported**
- H: Cores are gravitationally collapsing | E: Asymmetry of H13CO+ and CCH profiles vs thin-tracer V_lsr; Hill5 fits with emcee | R: Majority blue profiles; hub protostellar cores have high infall rates | F: Hub cores infall faster than filament cores | **supported**
- H: Massive cores on filaments with red profiles are feeding the hub (competitive accretion) | E: M-R relation plus velocity/intensity profile along F3-F4 | R: Cores 10, 11, 14 in massive regime show red profiles; cores 10, 11 at velocity gradient/dip and intensity minima | F: Gas funnels from less gravitationally dominant cores to hub cores, supporting competitive accretion | **partially**
- H: Hub can accumulate enough mass to form massive stars | E: Assume 20-30% of filament inflow over 2e4 yr | R: 35-52.5 Msun gained | F: Accumulated mass sufficient for massive stars in hub | **supported**

## Reasoning

- Why this data: 1.3 mm QUARKS continuum chosen for filament finding due to resolution; 12m+7m combination recovers extended emission  
  > "as the continuum emission has good spatial resolution." (Identification of filaments); "The ACA observations help to cover the missing flux up to 30$^{\prime\prime}$, which is important to the science goals." (QUARKS survey)
- Why this method: H13CO+ and CCH used as infall tracers because HCO+ outflow-contaminated and CS spectrally coarse  
  > "in our protocluster, the HCO$^{+}$ line is significantly contaminated by outflow activities from the embedded protostars, while the CS line has a coarse spectral resolution of about 3 km s$^{-1}$" (Gas infall rates in cores)
- Alternative: HCO+ (1–0) and CS (2–1) rejected as infall tracers  
  > "In general, tracers like HCO$^{+}$ (1–0) or CS (2–1) are best-served for this purpose." (Gas infall rates in cores)
- Alternative: Multi-component cloud origin of double peaks rejected  
  > "further confirming that the double-peaked shapes arise from self-absorption and not from multi-component cloud." (Gas infall rates in cores)
- Alternative: Red profile as infall due to temperature inversion dismissed  
  > "Such profile is generally expected when inversion of temperature gradient occurs from core to the envelope due to the presence of an external heating source (cite: 2002ApJ...577..798D), but this is not the case here." (Gas infall rates in cores)
- Alternative: Extreme inclinations 0° and 90° excluded  
  > "However, such possibilities can be excluded from the fact that the filamentary structures do exist and the velocity variation along them is also significantly measurable." (Mass inflow rate along the filaments)
- How they decided it was enough: S/N ≳ 15 threshold for Hill5 fits; unreliable fits excluded  
  > "Fit to a few spectra (cores 7, 10, and 14 for H$^{13}$CO$^{+}$, and cores 5, 8, 9, 13, and 14 for CCH) were unreliable due to the complex nature of their spectra, and hence, they were excluded from further analysis." (Gas infall rates in cores)
- Limitation (authors): N(H2) is lower limit because H13CO+ not always optically thin  
  > "The derived $N$(H$_2$) value represents a lower limit to the true column density, as the assumption of the line to be optically thin is not always valid" (Column density map)
- Limitation (authors): Abundance uncertainty implies mass uncertain by up to factor 10  
  > "implying that the total mass estimates could vary by up to a factor of 10." (Column density map)
- Limitation (authors): No consistent velocity gradient for F2  
  > "Note that we were unable to determine a consistent velocity gradient along the filament F2 due to significant velocity fluctuations along this filament." (Dynamical properties of filaments)
- Limitation (authors): Thin-tracer H13CN (4–3) spectra missing for most prestellar candidates  
  > "For other prestellar core candidates, we could not obtain the H$^{13}$CN (4–3) spectra might be because of lower flux level and/or significant missing flux." (Gas infall rates in cores)
- Limitation (authors): Cores 1-4, 15, 16 excluded (FOV or not compact in QUARKS)  
  > "Note that cores 15 and 16 are not present within the Field of View (FOV) of the 1.3 mm QUARKS data. Hence, we have not considered these cores in our subsequent analysis." (Selected region)
- Caveat (inferred, ours): F1 velocity gradient inconsistent: 22.5 km/s/pc in text vs 17.8 in Table and Summary; F3 inflow quoted as 5135 and 5017
- Caveat (inferred, ours): Summary gives core infall rates in Msun Myr^-1 with 1e-5 factor, inconsistent with Table units (Msun yr^-1)
- Caveat (inferred, ours): Cores 3, 15, 16 reported with blue profiles despite being excluded from analysis
- Caveat (inferred, ours): Using single clump T_dust and constant abundance for N(H2) in a hub with hot cores may bias hub masses
- Caveat (inferred, ours): Core masses/radii taken from 870 μm 12m-only data while profiles measured at different resolution
- Caveat (inferred, ours): Red profiles interpreted as mass transfer to the hub without direct measurement of flow from cores

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: QUARKS project code and data details
- Missing: Imaging parameters for cubes and continuum
- Missing: FilFinder settings
- Missing: Filament segment definitions and spectral averaging apertures
- Missing: Hill5 priors/bounds and MCMC settings
- Missing: Jy-to-K conversion details
- Data volume (inferred): Single target from three surveys (ATOMS Band 3 12m+ACA, ASSEMBLE ~345 GHz 12m, QUARKS 1.3 mm 12m+ACA); likely tens of GB of calibrated visibilities, or a few GB if only image cubes are used
- Score (inferred): 3/5, Data sources and project codes (two of three) given, and analysis formulas explicit, but imaging, FilFinder, PV extraction and MCMC settings are absent and internal numeric inconsistencies exist
- Rediscovery candidate: no, Paper does not state data public, QUARKS code not printed, and key settings (apertures, Hill5 bounds, filament segments) are missing, though results are numeric

## Links

- Method: (cite: 2015MNRAS.452.3435K) (FilFinder algorithm)
- Method: (cite: 2005ApJ...620..800D) (Hill5 infall model)
- Method: (cite: 2013ApJ...766..115K) (filament mass inflow rate method)
- Method: (cite: 1991ApJ...374..540G) (LTE column density formula)
- Method: (cite: 2013ascl.soft03002F) (emcee MCMC sampler)
- Method: (cite: 2013ApJ...765L..35K) (mass-radius massive star formation threshold)
- Companion: (cite: 2020MNRAS.496.2790L) (ATOMS survey overview and data reduction)
- Companion: (cite: 2024ApJS..270....9X) (core catalogue for this protocluster)
- Companion: (cite: 2022MNRAS.514.6038Z) (earlier ATOMS filament/velocity gradient study)
- Companion: (cite: 2024RAA....24b5009L) (QUARKS 1.3 mm continuum)
- Companion: (cite: 2024RAA....24f5011X) (QUARKS paper II, ACA observations)
- Companion: (cite: 2023MNRAS.520.3259X) (ASSEMBLE survey data/MRS)
- Related: ATOMS
- Related: ASSEMBLE
- Related: QUARKS

## Checks

```json
{
 "quotes": 115,
 "quotes_ok": 115,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 112,
  "stated": 78,
  "rate": 0.696
 },
 "evidence_ok": true
}
```
