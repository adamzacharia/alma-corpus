# A new measurement of the Galactic <SUP>12</SUP>C/<SUP>13</SUP>C gradient from sensitive HCO<SUP>+</SUP> absorption observations

`2024A&A...690A.372L` | Astronomy and Astrophysics 2024 | first author: Luo, Gan | arXiv: 2409.11821 | DOI: 10.1051/0004-6361/202451412

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, astrochemistry
- Question: What is the Galactic 12C/13C radial gradient, measured from H12CO+ and H13CO+ J=1-0 absorption against strong continuum sources (quasars and UCH II regions)?  
  > "In this work, we present a new measurement of the Galactic $^{12}$C/$^{13}$C gradient by using absorption lines of H$^{12}$CO$^+$ and H$^{13}$CO$^+$" (1 Introduction)
- Target **Five ALMA quasar sight lines (J1603-4904, J1720-3552, J1832-1035, J1851+0035, J1922+1530)**: coordinates _not stated_; z/distance not stated (foreground gas R_GC from kinematic distances, Table 2)  
  > "Five were observed with ALMA (2022.1.01438.S, PI: Thomas G. Bisbas) during March 20–30, 2023" (2.1 Quasar sight lines); distance from Monte Carlo kinematic distance method of Wenger et al. 2018 (cite: Wenger2018)  
  > "Five were observed with ALMA (2022.1.01438.S, PI: Thomas G. Bisbas) during March 20–30, 2023" (2.1 Quasar sight lines)
- Target **3C 111 (NOEMA quasar sight line)**: coordinates _not stated_; z/distance foreground cloud within 300 pc  
  > "one source (3C 111) was observed with NOEMA (W20BB, PI: Gan Luo) in December 2020 and January 2021." (2.1 Quasar sight lines); "the 3D extinction indicates that the cloud is within 300 pc from the Sun (cite: Lucas1998)" (Gaussian decomposition of absorption profiles toward 3C 111); distance from 3D extinction (cite: Lucas1998)  
  > "one source (3C 111) was observed with NOEMA (W20BB, PI: Gan Luo) in December 2020 and January 2021." (2.1 Quasar sight lines); "the 3D extinction indicates that the cloud is within 300 pc from the Sun (cite: Lucas1998)" (Gaussian decomposition of absorption profiles toward 3C 111)
- Target **Ten UCH II region sight lines from ATOMS (nine listed in Table 2, e.g. I15254-5621, I15502-5302, I15567-5236, I16060-5146, I16164-5046, I16172-5028, I18479-0005, I18507+0110, I19078+0901)**: coordinates _not stated_; z/distance not stated (foreground gas R_GC from kinematic distances, Table 2)  
  > "The ALMA observations toward ten UCH ii regions (red crosses in Fig. [1](#fig:srn)), which were selected from the ALMA Three-millimeter Observations of Massive Star-forming regions (ATOMS) survey" (2.2 UCH ii sight lines); distance from Monte Carlo kinematic distance method of Wenger et al. 2018 (cite: Wenger2018)  
  > "The ALMA observations toward ten UCH ii regions (red crosses in Fig. [1](#fig:srn)), which were selected from the ALMA Three-millimeter Observations of Massive Star-forming regions (ATOMS) survey" (2.2 UCH ii sight lines)

## Data provenance

- ALMA projects: 2022.1.01438.S, 2019.1.00685.S
- bands: Band 3 (UCH II sight lines, ATOMS); HCO+ and H13CO+ J=1-0 near 89 GHz for quasar sight lines  
  > "with both 12-m and 7-m arrays at band 3" (2.2 UCH ii sight lines); "The angular resolution of ALMA is $\sim$0.6$''$ at 89 GHz." (2.1 Quasar sight lines)
- frequencies and spectral setup: ALMA quasars: 122 kHz channels (~0.4 km/s); UCH II: 0.2 km/s (HCO+) and 0.422 km/s (H13CO+); NOEMA 3C 111: ~0.21 km/s, PolyFiX covers HCN, H13CN, HNC, HN13C J=1-0  
  > "The spectral resolution of ALMA is 122 kHz, corresponding to a velocity resolution of $\sim$0.4 km s$^{-1}$ at 89 GHz." (2.1 Quasar sight lines); "The spectral resolution of H$^{12}$CO$^+$ and H$^{13}$CO$^+$ *J*=1-0 transitions are 0.2 km s$^{-1}$ and 0.422 km s$^{-1}$, respectively." (2.2 UCH ii sight lines); "The PolyFiX backend of NOEMA covers H$^{12}$CN, H$^{13}$CN, HN$^{12}$C, and HN$^{13}$C *J*=1-0 transitions simultaneously." (2.1 Quasar sight lines)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m and 7-m arrays (UCH II sight lines)  
  > "were observed from September to November 2019 with both 12-m and 7-m arrays at band 3." (2.2 UCH ii sight lines)
- configurations: _not stated_
- baselines: ATOMS baselines 15 to 783.5 m  
  > "The baselines of ATOMS range from 15 to 783.5 m" (2.2 UCH ii sight lines)
- angular resolution: ALMA quasars ~0.6 arcsec at 89 GHz; NOEMA ~2.1 arcsec; ATOMS UCH II ~1.2 arcsec  
  > "The angular resolution of ALMA is $\sim$0.6$''$ at 89 GHz." (2.1 Quasar sight lines); "The NOEMA observations have an angular resolution of $\sim$2.1$''$ at 89 GHz" (2.1 Quasar sight lines); "corresponding to an angular resolution of $\sim$1.2$''$ at 89 GHz." (2.2 UCH ii sight lines)
- max recoverable scale: _not stated_
- sensitivity: optical depth noise 3-7e-3 per 0.4 km/s channel (ALMA quasars), 2e-3 per 0.21 km/s channel (NOEMA); UCH II RMS per source in Table 2  
  > "The typical optical depth noise levels are 3$\sim$7$\times$10$^{-3}$ per 0.4 km s$^{-1}$ velocity channel for ALMA observations and 2$\times$10$^{-3}$ per 0.21 km s$^{-1}$ velocity channel for NOEMA observations." (2.1 Quasar sight lines)
- time on source: _not stated_
- observing dates: Quasars: ALMA 20-30 March 2023, NOEMA Dec 2020 and Jan 2021; UCH II: Sept-Nov 2019  
  > "during March 20–30, 2023, and one source (3C 111) was observed with NOEMA (W20BB, PI: Gan Luo) in December 2020 and January 2021." (2.1 Quasar sight lines); "were observed from September to November 2019" (2.2 UCH ii sight lines)
- pi or archival as stated: 2022.1.01438.S PI Thomas G. Bisbas; 2019.1.00685.S (ATOMS) PI Tie Liu; NOEMA W20BB PI Gan Luo  
  > "Five were observed with ALMA (2022.1.01438.S, PI: Thomas G. Bisbas)" (2.1 Quasar sight lines); "survey (2019.1.00685.S, PI: Tie Liu)" (2.2 UCH ii sight lines)
- Line: H12CO+ J=1-0 (89188.5247 MHz)
- Line: H13CO+ J=1-0 (86754.2884 MHz)
- Line: HN12C and HN13C (3C 111 only) J=1-0 (90663.568 MHz and 87090.85 MHz)
- Line: H12CN and H13CN (3C 111 only, hyperfine) J=1-0 (88630.4156 MHz (F=1-1) and 86338.7352 MHz (F=1-1), plus other hyperfine components)
- Other facility **NOEMA**: HCO+, H13CO+ (and HCN, HNC isotopologue) absorption spectra toward 3C 111  
  > "one source (3C 111) was observed with NOEMA (W20BB, PI: Gan Luo) in December 2020 and January 2021." (2.1 Quasar sight lines)
- Other facility **ATOMS survey**: ALMA band 3 data toward the UCH II regions  
  > "which were selected from the ALMA Three-millimeter Observations of Massive Star-forming regions (ATOMS) survey" (2.2 UCH ii sight lines)
- Other facility **BeSSeL Survey**: trigonometric parallaxes of high-mass star-forming regions underlying the rotation curve model  
  > "This model is obtained through the trigonometric parallax results from the high-mass star-forming regions (HMSFRs) in the BeSSeL Survey" (3.2 The 12C/13C gradient)
- External data: Galactic rotation curve and updated solar motion parameters for Monte Carlo kinematic distances  
  > "using the latest rotational curve and updated solar motion parameters (cite: Wenger2018)" (3.2 The 12C/13C gradient) [from (cite: Wenger2018)]
- External data: Tilted-disk model used for R_GC of components with V_lsr < -140 km/s toward J1720-3552  
  > "we used the tilted-disk model presented by (cite: Burton1978) to estimate the velocity components" (3.2 The 12C/13C gradient) [from (cite: Burton1978)]
- External data: Dipole matrix element, upper energy level and rest frequency for each transition  
  > "were taken from the Cologne Database for Molecular Spectroscopy (cite: Muller2001; Muller2005)" (3.1 Absorption spectra and integrated optical depth) [from (cite: Muller2001; Muller2005)]
- External data: GCE models compared with the measured gradient  
  > "The comparison between the derived $^{12}$C/$^{13}$C gradient and the GCE models presented in (cite: Colzi2022) is shown in Fig. [4](#fig:fig3)" (4.3 The 12C/13C gradient and comparison with GCE models) [from (cite: Colzi2022); (cite: Romano2019; Romano2021)]
- External data: Literature 12C/13C gradients from other tracers (C18O, CN, H2CO, C34S, combined) plotted for comparison  
  > "The gradients from different methodologies are shown with different curves in Fig. [3](#fig:fig2)." (4.3 The 12C/13C gradient and comparison with GCE models) [from (cite: Langer1990; Langer1993; Wouterloot1996; Giannetti2014; Savage2002; Milam2005; Sun2024; Henkel1982; Yan2019; Yan2023; Halfen2017; Jacob2020)]
- External data: Optical CH+ solar-neighbourhood ratio (74.4+-7.6) used as comparison  
  > "which is consistent with those measured from CH$^+$ (74.4$\pm$7.6)." (5 Conclusion) [from (cite: Ritchey2011)]

## Processing

### Calibration

- pipeline or manual: standard pipeline (CASA)  
  > "The raw data was calibrated using the standard pipeline with the Common Astronomy Software Applications" (2.1 Quasar sight lines)
- casa version: UCH II data calibrated with CASA 5.6; combination and imaging with CASA 6.4.1; quasar CASA version not stated  
  > "The raw data were calibrated using CASA version 5.6, and the combination and imaging of 12-m and 7-m data were performed with CASA version 6.4.1." (2.2 UCH ii sight lines)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean (quasar sight lines)  
  > "The imaging of the calibrated visibilities was performed using the *tclean* algorithm with Briggs weighting (robust = 0.5)." (2.1 Quasar sight lines)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5 (quasar sight lines)  
  > "The imaging of the calibrated visibilities was performed using the *tclean* algorithm with Briggs weighting (robust = 0.5)." (2.1 Quasar sight lines)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12-m and 7-m data combined with CASA 6.4.1 (UCH II sight lines)  
  > "the combination and imaging of 12-m and 7-m data were performed with CASA version 6.4.1." (2.2 UCH ii sight lines)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Detailed description of the ATOMS UCH II observations and per-source sensitivity  
  > "a detailed description of observations can be found in (cite: Liu2020)." (2.2 UCH ii sight lines) [from (cite: Liu2020)]
- Monte Carlo kinematic distance method details  
  > "A detailed description of this method can be found in (cite: Wenger2018)." (3.2 The 12C/13C gradient) [from (cite: Wenger2018)]
- Column density formula in terms of integrated optical depth  
  > "The molecular column density can be written as a function of $\int \tau_\nu d\upsilon$ (cite: Mangum2015)" (3.1 Absorption spectra and integrated optical depth) [from (cite: Mangum2015)]
- Linear-molecule partition function  
  > "For linear molecules, the simplified partition function is given by (cite: McDowell1987)" (3.1 Absorption spectra and integrated optical depth) [from (cite: McDowell1987)]

### Not stated but needed to reproduce (our reading)

- Continuum-peak pixel selection and exact spectrum normalisation procedure (continuum level, continuum subtraction) used to turn spectra into optical depth
- Exact velocity integration ranges per component (only the V_lsr centres are tabulated) and the RMS used in the uncertainty formula for each source
- CASA version used for the five quasar data sets, line-free channels, cell size, image size, masking, deconvolution and cleaning thresholds
- Whether archive-delivered products or a re-run pipeline were used, and flux/bandpass/gain calibrators
- Likelihood, priors, number of walkers/steps and treatment of limits in the emcee linear fit
- Identity of the tenth UCH II source (only nine appear in Table 2) and which components were excluded for tau >= 3
- Observational settings for 3C 111 NOEMA data (baselines, integration time, calibrators)

## Analysis recipe

1. **Calibrate and image the interferometer data**: ALMA data calibrated with the standard CASA pipeline and imaged with tclean (Briggs robust 0.5); UCH II 12-m and 7-m data combined in CASA 6.4.1; NOEMA data calibrated with clic in GILDAS  
  > "The imaging of the calibrated visibilities was performed using the *tclean* algorithm with Briggs weighting (robust = 0.5)." (2.1 Quasar sight lines); "The calibration of the raw data was performed using clic software in the gildas." (2.1 Quasar sight lines)
   - software: CASA, tclean, GILDAS clic
   - parameter: Briggs weighting, robust = 0.5 (quasar sight lines)  
  > "Briggs weighting (robust = 0.5)" (2.1 Quasar sight lines)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract absorption spectra and convert to optical depth**: Spectra extracted at the continuum peak of each source and normalised; optical depth from absorption depth (sigma_tau = RMS / e^-tau)  
  > "were extracted from the continuum peak of each source." (3.1 Absorption spectra and integrated optical depth); "is the uncertainty of $\tau$ at the $i$th channel." (3.1 Absorption spectra and integrated optical depth)
   - fitting: _not stated_
   - validation: _not stated_
3. **Integrate optical depths of HCO+ and H13CO+ over matched velocity ranges**: Integrate tau over the same velocity range for both lines, with four selection criteria (no contamination of H13CO+, non-overlapping ranges, HCO+ not saturated, no emission contamination for UCH II); uncertainty by error propagation  
  > "We set four criteria when identifying the integrated range:" (3.1 Absorption spectra and integrated optical depth); "should be distinguished from the others (no overlap)" (3.1 Absorption spectra and integrated optical depth)
   - parameter: HCO+ unsaturated: e^-tau > rms  
  > "the absorption profile of HCO$^+$ should not be saturated" (3.1 Absorption spectra and integrated optical depth)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive HCO+/H13CO+ column density ratios**: Column density from integrated optical depth (Mangum & Shirley 2015) with CDMS constants; ratio simplified to 0.974 x ratio of integrated optical depths  
  > "The molecular column density can be written as a function of $\int \tau_\nu d\upsilon$ (cite: Mangum2015)" (3.1 Absorption spectra and integrated optical depth); "were taken from the Cologne Database for Molecular Spectroscopy (cite: Muller2001; Muller2005)" (3.1 Absorption spectra and integrated optical depth)
   - software: CDMS
   - parameter: T_ex = 2.73 K for both HCO+ and H13CO+  
  > "take $T_{\rm ex} = 2.73$ K for both HCO$^+$ and H$^{13}$CO$^+$, the column density ratios can be simplified as" (3.1 Absorption spectra and integrated optical depth)
   - assumption: T_ex of HCO+ close to T_CMB in diffuse molecular clouds  
  > "The excitation temperature of HCO$^+$ in diffuse molecular clouds is usually close to the cosmic microwave background temperature" (3.1 Absorption spectra and integrated optical depth)
   - fitting: _not stated_
   - validation: Varying T_ex from 2.73 to 5 K changes the ratio by less than 1%  
  > "only results in a variance of the column density ratio of less than 1%." (3.1 Absorption spectra and integrated optical depth)
5. **Determine galactocentric radius of each velocity component**: Monte Carlo kinematic distance method with the Wenger et al. 2018 rotation curve; optical-depth-weighted V_lsr; tilted-disk model for V_lsr < -140 km/s toward J1720-3552  
  > "We calculated the $R_{\rm GC}$ for each velocity component with the Monte Carlo kinematic distance method, using the latest rotational curve and updated solar motion parameters (cite: Wenger2018)." (3.2 The 12C/13C gradient); "resulting in an $R_{\rm GC}$ between 1.24 to 1.5 kpc." (3.2 The 12C/13C gradient)
   - parameter: Median uncertainty of 13% relative to parallax distances  
  > "resulting in a median uncertainty of 13% to the parallax distances." (3.2 The 12C/13C gradient)
   - assumption: Pure circular motions outside the GC region  
  > "We note that such an estimation with pure circular motions may fail to predict the $R_{\rm GC}$ near the GC" (3.2 The 12C/13C gradient)
   - fitting: _not stated_
   - validation: _not stated_
6. **Fit the linear 12C/13C versus R_GC gradient**: MCMC with emcee on points with tau < 3; maximum-likelihood linear fit  
  > "We used the Markov chain Monte Carlo (MCMC) method within the $emcee$ code (cite: Foreman-Mackey2013) to sample the free parameters and the posterior probability distribution." (3.2 The 12C/13C gradient)
   - software: emcee
   - parameter: tau < 3 constraint  
  > "we set stricter constraints ($\tau < 3$) when fitting a gradient." (3.2 The 12C/13C gradient)
   - fitting: emcee MCMC; priors and likelihood not stated  
  > "The maximum likelihood fit of the data is shown with a red solid curve in Fig. [3](#fig:fig2)" (3.2 The 12C/13C gradient)
   - validation: Compared with other tracers' gradients and GCE models  
  > "Our result is reasonably consistent with the GCE models with a mass range of white dwarf progenitors 1–8 M$_\odot$" (4.3 The 12C/13C gradient and comparison with GCE models)
7. **Check chemical fractionation effects on HCO+/H13CO+**: Compare isotopic exchange reaction rate with H13CO+ formation pathways using literature rates and abundances  
  > "the formation of H$^{13}$CO$^+$ through reaction [\[r:R3\]](#r:R3) would overwhelm reaction [\[r:R2\]](#r:R2) by over four orders of magnitude" (4.4 Chemical effects on the measured 12C/13C ratios)
   - parameter: gas temperature ~50 K; 12C/13C = 70 scaling  
  > "scale the above abundance with $^{12}$C/$^{13}$C = 70" (4.4 Chemical effects on the measured 12C/13C ratios)
   - assumption: Constant HCO+ abundance to convert N(HCO+) to N(H2)  
  > "assuming a constant HCO$^+$ abundance" (4.4 Chemical effects on the measured 12C/13C ratios)
   - fitting: _not stated_
   - validation: _not stated_
8. **Gaussian decomposition of 3C 111 HCN/HNC absorption**: scipy curve_fit (Levenberg-Marquardt) with hyperfine lines constrained to the same linewidth and velocity offset  
  > "The Gaussian decomposition is performed with $curve\_fit$ package in $scipy$ using the Levenberg-Marquardt algorithm" (Gaussian decomposition of absorption profiles toward 3C 111); "all hyperfine lines have 1) the same linewidth ($\Delta V$) and 2) the same velocity offset with respect to $V_{\rm lsr}$." (Gaussian decomposition of absorption profiles toward 3C 111)
   - software: scipy
   - assumption: Hyperfine optical depth ratios optionally fixed to 1:3:5  
  > "we can fix the optical depth ratios at 1:3:5 instead of treating them as free parameters" (Gaussian decomposition of absorption profiles toward 3C 111)
   - fitting: Levenberg-Marquardt least squares  
  > "using the Levenberg-Marquardt algorithm" (Gaussian decomposition of absorption profiles toward 3C 111)
   - validation: _not stated_

## Software

- **CASA** 5.6 (UCH II calibration); 6.4.1 (UCH II combination and imaging); quasar version not stated: Calibration and imaging of ALMA data  
  > "The raw data were calibrated using CASA version 5.6, and the combination and imaging of 12-m and 7-m data were performed with CASA version 6.4.1." (2.2 UCH ii sight lines)
- **tclean** : Imaging calibrated visibilities with Briggs weighting  
  > "The imaging of the calibrated visibilities was performed using the *tclean* algorithm with Briggs weighting (robust = 0.5)." (2.1 Quasar sight lines)
- **GILDAS (clic)** : Calibration of NOEMA raw data  
  > "The calibration of the raw data was performed using clic software in the gildas." (2.1 Quasar sight lines)
- **emcee** : MCMC sampling of the gradient fit parameters  
  > "We used the Markov chain Monte Carlo (MCMC) method within the $emcee$ code (cite: Foreman-Mackey2013)" (3.2 The 12C/13C gradient)
- **scipy (curve_fit)** : Gaussian decomposition of 3C 111 absorption profiles  
  > "The Gaussian decomposition is performed with $curve\_fit$ package in $scipy$ using the Levenberg-Marquardt algorithm" (Gaussian decomposition of absorption profiles toward 3C 111)
- **CDMS** : Line frequencies, dipole moments and upper-level energies  
  > "were taken from the Cologne Database for Molecular Spectroscopy (cite: Muller2001; Muller2005)" (3.1 Absorption spectra and integrated optical depth)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Slope of HCO+/H13CO+ versus R_GC | 6.4 | 1.9 | per kpc | 6 | from HCO$^+$ absorption measurements is (6.4$\pm$1.9)$R_{\rm GC}$/kpc+(25.9$\pm$10.5) |
| Intercept of HCO+/H13CO+ versus R_GC | 25.9 | 10.5 | dimensionless | 6 | from HCO$^+$ absorption measurements is (6.4$\pm$1.9)$R_{\rm GC}$/kpc+(25.9$\pm$10.5) |
| Weighted-mean 12C/13C toward the GC | 42 | 1 | dimensionless | 4 | The weighted-mean $^{12}$C/$^{13}$C ratios increase from 42$\pm$1 toward the GC to 66$\pm$5 in the solar neighborhood. |
| Weighted-mean 12C/13C in the solar neighborhood (7.6 <= R_GC <= 8.6 kpc) | 66 | 5 | dimensionless | 4 | with a weighted mean value of 66$\pm$5. |
| Range of measured HCO+/H13CO+ ratios (lowest) | 12.7 | 0.2 | dimensionless | 4 | The calculated ratios in our samples range from 12.7$\pm$0.2 |
| Range of measured HCO+/H13CO+ ratios (highest; text gives 38.0, Table 2 gives 41.9) | 139.4 | 38.0 (text) | dimensionless | 4 | to 139.4$\pm$38.0 |
| 12C/13C at R_GC < 2 kpc, two components | 42.2 and 37.5 | 1.7 and 6.5 | dimensionless | 4 | The two measurements at $R_{\rm GC} < 2$ kpc from our observations have $^{12}$C/$^{13}$C ratios of 42.2$\pm$1.7 and 37.5$\pm$6.5 |
| Lower limits on 12C/13C at -181 and -162 km/s toward J1720-3552 | >19 and >31 | not stated | dimensionless | 4 | Furthermore, the two lower limits of $^{12}$C/$^{13}$C at $-$181 and $-$162 km s$^{-1}$ of J1720-3552 are $>19$ and $>31$. |
| Adopted R_GC of V_lsr < -140 km/s component toward J1720-3552 | 1.37 | 0.04 | kpc | 5 | Thus, we adopted a value of 1.37$\pm$0.04 kpc for this component. |
| 12C/13C at -0.9 km/s toward 3C 111 from H12CN/H13CN | 74 | 3 | dimensionless | 8 | The $^{12}$C/$^{13}$C ratio at $-0.9$ km s$^{-1}$ derived from H$^{12}$CN/H$^{13}$CN is 74$\pm$3 |
| 12C/13C at -0.9 km/s toward 3C 111 from HN12C/HN13C | 62 | 6 | dimensionless | 8 | Measurement from HN$^{12}$C/HN$^{13}$C (62$\pm$6) also show similar result. |
| 12C/13C at -2.5 km/s toward 3C 111 from H12CN/H13CN | 138 | 28 | dimensionless | 8 | derived from H$^{12}$CN/H$^{13}$CN is 138$\pm$28 |
| Highest HCO+ column density | ~3.4e13 | not stated | cm^-2 | 4 | is $\sim 3.4\times10^{13}$ cm$^{-2}$, corresponding to an H$_2$ column density of $10^{22}$ cm$^{-2}$ |

## Qualitative findings

- HCO+/H13CO+ measured in low-density gas is higher than ratios from higher-density tracers (C18O, H2CO, CS, CN), suggesting fractionation matters for the dense-gas tracers  
  > "The systematically increasing trend of the $^{12}$C/$^{13}$C gradient from high-density to low-density gas may again suggest that fractionation plays a crucial role" (4.3 The 12C/13C gradient and comparison with GCE models)
- An unusually low ratio (12.7) at -22 km/s toward J1720-3552 has an unclear origin  
  > "however, the reason is still unclear." (The unusual low H12CO+/H13CO+ toward J1720-3552)

## Claim tuples

- H: Does HCO+ absorption give a 12C/13C radial gradient consistent with GCE models? | E: Integrated tau ratios of HCO+ and H13CO+ per velocity component, kinematic R_GC, emcee linear fit | R: Gradient (6.4+-1.9) R_GC/kpc + (25.9+-10.5) | F: Gradient reasonably consistent with current GCE models (models 3 and 4 of Colzi et al. 2022) | **supported**
- H: Is the solar-neighbourhood 12C/13C from HCO+ consistent with CH+? | E: Weighted mean of HCO+/H13CO+ within 7.6-8.6 kpc compared with optical CH+ | R: 66+-5 versus CH+ 74.4+-7.6 | F: Consistent | **supported**
- H: Are Galactic-centre 12C/13C values as low as in dense gas tracers toward Sgr B2? | E: HCO+/H13CO+ absorption toward J1720-3552 at R_GC < 2 kpc | R: 37.5-42.2, two to three times higher than dense-gas values (11-24) | F: Dense-gas tracers likely affected by opacity and fractionation | **supported**
- H: Does carbon fractionation bias HCO+/H13CO+ in low-density gas? | E: Rate comparison of isotopic exchange and H13CO+ formation pathways | R: Formation through R3 exceeds R2 by over four orders of magnitude at ~50 K | F: Fractionation has little impact on measured ratios in low-density gas | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Absorption lines against strong continuum sources avoid opacity, beam dilution and sub-thermal excitation problems  
  > "Absorption lines against strong continuum sources can overcome such difficulties." (1 Introduction); "The advantage of using absorption lines is to measure the optical depth as well as the column density precisely even if the transition is sub-thermally excited." (1 Introduction)
- Alternative: HCO+ Gaussian decomposition toward 3C 111 rejected because HCO+ is almost saturated; HCN and HNC used instead  
  > "However, the HCO$^+$ absorption profile is almost saturated toward 3C 111 and we cannot get a good Gaussian decomposition." (Gaussian decomposition of absorption profiles toward 3C 111)
- How they decided it was enough: _not stated_
- Limitation (authors): Gradient depends on the accuracy of kinematic-distance-based R_GC  
  > "the formula of the isotopic gradient strongly depends on the accuracy of the $R_{\rm GC}$, which is mostly based on the kinematic distance estimation." (4.3 The 12C/13C gradient and comparison with GCE models)
- Limitation (authors): Limited R_GC range of the sample  
  > "Given the limited range of $R_{\rm GC}$ in the current samples" (4.3 The 12C/13C gradient and comparison with GCE models)
- Limitation (authors): Pure circular motions may fail near the GC  
  > "We note that such an estimation with pure circular motions may fail to predict the $R_{\rm GC}$ near the GC" (3.2 The 12C/13C gradient)
- Caveat (inferred, ours): Large scatter at 4-8 kpc and a ratio of 12.7 at -22 km/s are not explained, and may affect the weighted fit
- Caveat (inferred, ours): Text and Table 2 disagree on the uncertainty of the 139.4 ratio (38.0 versus 41.9)
- Caveat (inferred, ours): Table 2 lists nine UCH II sources while the text says ten
- Caveat (inferred, ours): T_ex = T_CMB is assumed for all components, including dense UCH II envelopes
- Caveat (inferred, ours): Limits and tau < 3 exclusions in the fit are not detailed

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Integration velocity ranges per component
- Missing: Continuum peak position and normalisation procedure
- Missing: CASA version, cell size, image size and cleaning parameters for quasar data
- Missing: emcee priors, likelihood and settings
- Missing: NOEMA calibration and observing details for 3C 111
- Data volume (inferred): Moderate: Band 3 spectral-line data for five quasar fields plus ten ATOMS 12-m+7-m fields, likely tens to a few hundred GB raw; NOEMA data not an ALMA download
- Score (inferred): 3/5, Project codes, line frequencies, tclean robust value and the full numeric table are given, but integration ranges, imaging geometry, calibrators and fit priors are not.
- Rediscovery candidate: no, Public availability of the data is not stated, integration ranges and imaging details are missing, and the 3C 111 results rely on NOEMA data.

## Links

- Method: (cite: Liu2020) (Describes the ATOMS observations and sensitivities)
- Method: (cite: Wenger2018) (Monte Carlo kinematic distance method)
- Method: (cite: Mangum2015) (Column density formalism from integrated optical depth)
- Companion: (cite: Lucas1998) (Earlier isotopic-ratio absorption measurement toward 3C 111)
- Companion: (cite: Liszt2018) (Earlier HCO+/H13CO+ absorption toward the Galactic bulge)
- Companion: (cite: Colzi2022) (GCE models compared to the measured gradient)
- Related: ATOMS (ALMA Three-millimeter Observations of Massive Star-forming regions)
- Related: BeSSeL Survey

## Checks

```json
{
 "quotes": 111,
 "quotes_ok": 111,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 108,
  "stated": 68,
  "rate": 0.63
 },
 "evidence_ok": true
}
```
