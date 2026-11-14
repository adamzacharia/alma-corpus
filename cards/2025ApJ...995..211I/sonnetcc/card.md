# ALMA Subparsec Resolution Dense Molecular Line Observations of the NGC 1068 Nucleus

`2025ApJ...995..211I` | The Astrophysical Journal 2025 | first author: Imanishi, Masatoshi | arXiv: 2511.04772 | DOI: 10.3847/1538-4357/ae1caa

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What are the dense-gas morphology, kinematics (apparent counter-rotation) and excitation of the NGC 1068 torus at sub-pc resolution in HCN and HCO+ J=4-3, and does a physically counter-rotating torus model reproduce them?  
  > "line observations of the NGC 1068 nucleus to further scrutinize various properties of the dense molecular torus around the AGN in NGC 1068." (Introduction); "We apply a physically counter-rotating torus model, in which a compact dense gas clump collided with the western side of the existing rotating torus from the opposite direction" (abstract)
- Target **NGC 1068 nucleus**: coordinates C-peak (continuum peak, ICRS): 02h 42m 40.709s, -00d 00m 47.946s  
  > "(02$^{\rm h}$ 42$^{\rm m}$ 40.709$^{\rm s}$, $-$00$^{\circ}$ 00$'$ 47.946$''$) (C-peak)" (Table 2); "very nearby ($\sim$14 Mpc, $z =$ 0.0038, 1 arcsec = 70 pc) type 2 AGN, NGC 1068" (Introduction); z/distance ~14 Mpc, z = 0.0038, 1 arcsec = 70 pc  
  > "(02$^{\rm h}$ 42$^{\rm m}$ 40.709$^{\rm s}$, $-$00$^{\circ}$ 00$'$ 47.946$''$) (C-peak)" (Table 2); "very nearby ($\sim$14 Mpc, $z =$ 0.0038, 1 arcsec = 70 pc) type 2 AGN, NGC 1068" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2022.1.00005.S, 2018.1.00037.S
- bands: _not stated_
- frequencies and spectral setup: 1.875 GHz mode, 1920 channels per spw; HCN and HCO+ J=4-3 (+HCN-VIB) in USB, CS J=7-6 in LSB  
  > "We employed the widest 1.875 GHz mode with 1920 channels for each spectral window." (Observations and Data Analysis); "lines were simultaneously observed in one sideband (USB)." (Observations and Data Analysis); "In LSB, the CS J=7–6 line" (Observations and Data Analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: longest baseline (~16 km) configuration, Cycle 9  
  > "To achieve the highest angular resolution, the longest baseline" (Observations and Data Analysis)
- baselines: 230–16196 m (first five executions); 83–16196 m (Aug 9 and 11)  
  > "230–16196" (Table 1); "83–16196" (Table 1)
- angular resolution: ~350 GHz continuum and J=4-3 lines: 0.014 x 0.013 arcsec (~1 pc); reanalysed ~260 GHz: 0.019 x 0.017 arcsec (continuum), 0.020 x 0.018 (J=3-2 lines)  
  > "the synthesized beam size (0.014$''$ $\times$ 0.013$''$)" (Results); "0.019$\times$0.017 (56$^{\circ}$)" (Table 2)
- max recoverable scale: MRS >~ 0.14 arcsec (>~10 pc), from the Cycle 9 Proposer's Guide  
  > "The maximum recoverable scale (MRS) of our ALMA Cycle 9 data is $\gtrsim$0.14$''$" (Observations and Data Analysis)
- sensitivity: rms ~0.3 mJy/beam per 10 km/s channel for HCN and HCO+ J=4-3; ~0.2 mJy/beam for J=3-2  
  > "The derived rms noise level for the 10 km s$^{-1}$ velocity resolution is $\sim$0.3 mJy beam$^{-1}$ for both HCN J=4–3 and HCO$^{+}$ J=4–3." (Observations and Data Analysis); "The derived rms noise level for the 10 km s$^{-1}$ velocity resolution is $\sim$0.2 mJy beam$^{-1}$ for both HCN J=3–2 and HCO$^{+}$ J=3–2." (Observations and Data Analysis)
- time on source: 44 min net on-source per execution, 7 executions (Cycle 9)  
  > "Net on source integration time in minutes." (Table 1 notes)
- observing dates: 2023 July 28 to 2023 August 11 (7 executions)  
  > "2023 July 28" (Table 1); "2023 August 11" (Table 1)
- pi or archival as stated: Cycle 9 program 2022.1.00005.S (PI = M. Imanishi) for J=4-3; Cycle 6 2018.1.00037.S (published in Imanishi et al. 2020) reanalysed for J=3-2  
  > "were conducted in our ALMA Cycle 9 program 2022.1.00005.S (PI = M. Imanishi)." (Observations and Data Analysis); "We reanalyzed the HCN J=3–2 and HCO$^{+}$ J=3–2 data" (Observations and Data Analysis)
- Line: HCN J=4-3 (354.505 GHz)
- Line: HCO+ J=4-3 (356.734 GHz)
- Line: HCN v2=1, l=1f (HCN-VIB) J=4-3 (356.256 GHz)
- Line: CS J=7-6 (342.883 GHz)
- Line: HCN J=3-2 (Cycle 6, reanalysed) (265.886 GHz)
- Line: HCO+ J=3-2 (Cycle 6, reanalysed) (267.558 GHz)
- Other facility **VLBI 22 GHz H2O maser data (literature)**: Velocities and positions of redshifted 22 GHz H2O maser spots within ~0.5-1.2 pc of the SMBH, compared with the ALMA HCN J=4-3 velocity profile  
  > "Figure [6](#fig:Wtorus) compares the velocity profiles of the VLBI-detected 22 GHz H$_{2}$O maser emitting spots and the ALMA-detected HCN J=4–3 emission." (Results)
- External data: 22 GHz H2O maser spot velocities and positions (VLBI), most redshifted at V ~ 1470 km/s ~0.5 pc NW of the SMBH  
  > "The most redshifted H$_{2}$O maser emission has an intensity-weighted velocity of V $\sim$ 1470 km s$^{-1}$" (Results) [from (cite: gre97; gal04; mor23; gal23; gal24)]
- External data: Best-fit analytical collision-induced counter-rotating torus model used for the position-velocity and spectra comparison  
  > "Figure [10](#fig:VollmerPV) shows a detailed comparison of the position-velocity diagrams of the HCN J=4–3 and HCO$^{+}$ J=4–3 lines between our new $\lesssim$1 pc resolution data and the best-fit model of (cite: vol22)." (Discussion) [from (cite: vol22)]
- External data: Integrated torus fluxes HCN J=4-3 5.3 Jy km/s and HCO+ J=4-3 3.0 Jy km/s (their Table 4), compared with the new 6.8 pc aperture fluxes  
  > "This recovers $\gtrsim$80% of the integrated HCN J=4–3 flux from the torus (5.3 Jy km s$^{-1}$) reported in Table 4 of (cite: vol22)." (Discussion) [from (cite: vol22)]
- External data: SMBH mass M_SMBH ~ 1e7 Msun, used for Keplerian velocity estimates  
  > "M$_{\rm SMBH}$ $\sim$ 1 $\times$ 10$^{7}$M$_{\odot}$ (cite: gre96; hur02; lod03; gal23; gal24)" (Results) [from (cite: gre96; hur02; lod03; gal23; gal24)]
- External data: Critical densities and upper energy levels of HCN and HCO+ transitions  
  > "are n$_{\rm crit}$ $\gtrsim$ 10$^{6}$ cm$^{-3}$ at a gas kinetic temperature of 50–100 K (cite: shi15)" (Discussion) [from (cite: shi15)]
- External data: Luminosity-to-dense-H2-mass conversion factors: 6-12 for HCN J=1-0 and 2-5 for HCO+ J=1-0 (Msun per K km/s pc2)  
  > "M$_{\rm dense-H_2}$(HCN) = 6–12 $\times$ L(HCN J=1–0)" (Discussion); "M$_{\rm dense-H_2}$(HCO$^{+}$) = 2–5 $\times$ L(HCO$^{+}$ J=1–0)" (Discussion) [from (cite: gao04; kri08; ler17) for HCN; (cite: ler17) for HCO+]
- External data: Beam-sized spectra and absorption features of the J=3-2 lines, and the Cycle 6 HCN/HCO+ J=3-2 maps  
  > "(cite: ima20) presented cleaned maps of" (Observations and Data Analysis) [from (cite: ima20)]
- External data: HCO+ column density of 3e15 cm-2 used in the RADEX absorbing-cloud model  
  > "column density of 3 $\times$ 10$^{15}$ cm$^{-2}$ for HCO$^{+}$ (cite: gam25) and HCN" (Appendix A) [from (cite: gam25)]
- Simulation/model as data: Analytical collision-induced counter-rotating torus model of Vollmer et al. (2022) compared with the new data  
  > "We applied the analytical model based on this assumption presented by (cite: vol22)" (Summary)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline-calibrated data used as starting point  
  > "We started our analysis with pipeline-calibrated data provided by ALMA, using CASA 6.5.4-9 (cite: CASA22; hun23)." (Observations and Data Analysis)
- casa version: CASA 6.5.4-9  
  > "using CASA 6.5.4-9 (cite: CASA22; hun23)" (Observations and Data Analysis)
- pipeline version: _not stated_
- archive products used as is: Pipeline-calibrated data provided by ALMA  
  > "We started our analysis with pipeline-calibrated data provided by ALMA" (Observations and Data Analysis)
- flux calibrator: J0238+1636 (also bandpass); phase calibrator J0239-0234  
  > "J0238$+$1636" (Table 1); "J0239$-$0234" (Table 1)
- flux scale uncertainty: <~10% at ~350 GHz (Cycle 9); <~10% at ~260 GHz (Cycle 6)  
  > "The absolute flux calibration uncertainty is expected to be $\lesssim$10% at the observed frequency ($\sim$350 GHz) of the ALMA Cycle 9 data." (Observations and Data Analysis)
- self calibration: _not stated_

### Imaging

- task: CASA tclean (after uvcontsub), Briggs weighting, gain = 0.1  
  > "task (Briggs-weighting; robust $=$ 0.5, gain $=$ 0.1) to the continuum-subtracted molecular line and continuum data" (Observations and Data Analysis)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "task (Briggs-weighting; robust $=$ 0.5, gain $=$ 0.1) to the continuum-subtracted molecular line and continuum data" (Observations and Data Analysis)
- uv taper: _not stated_
- cell size: 0.0015 arcsec/pixel (1.5 mas/pixel); velocity resolution 10 km/s  
  > "with a pixel scale of 0.0015$''$ pixel$^{-1}$ (1.5 mas pixel$^{-1}$) and a velocity resolution of 10 km s$^{-1}$." (Observations and Data Analysis)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CASA uvcontsub with continuum level set from line-free channels (no obvious emission or absorption)  
  > "We determined the continuum level by selecting channels that did not show obvious emission or absorption lines and subtracted it using the CASA task" (Observations and Data Analysis)
- line free channels: Continuum extracted from 340.4–344.2 and 352.4–356.2 GHz (~350 GHz) and 263.6–269.1 GHz (~260 GHz); lines excluded  
  > "Frequency range (in GHz) used to extract continuum emission. Frequencies of obvious emission and absorption lines are excluded." (Table 2 notes)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Synthesized beams made identical for J=4-3 / J=3-2 ratio maps  
  > "after making their synthesized beams identical" (Results)
- final beam: Continuum ~350 GHz: 0.014 x 0.013 arcsec, PA -86 deg; J=4-3 lines: 0.014 x 0.013, PA -83 deg  
  > "0.014$\times$0.013 ($-$86$^{\circ}$)" (Table 2); "0.014$\times$0.013 ($-$83$^{\circ}$)" (Table 3)
- final rms: Continuum ~350 GHz 0.059 mJy/beam; ~260 GHz 0.075 mJy/beam; HCN J=4-3 moment 0 0.056 Jy km/s/beam  
  > "0.059" (Table 2); "0.075" (Table 2)

### Inherited from earlier work

- Cycle 6 HCN/HCO+ J=3-2 data first presented and cleaned in earlier work, here reanalysed on a common 1.5 mas pixel and 10 km/s grid  
  > "We reanalyzed the HCN J=3–2 and HCO$^{+}$ J=3–2 data with pixel scale of 1.5 mas pixel$^{-1}$ and velocity resolution of 10 km s$^{-1}$ to compare them with the newly taken" (Observations and Data Analysis) [from (cite: ima20)]
- Position-velocity diagram axis (PA = 114 deg east of north)  
  > "along the position angle PA = 114$^{\circ}$ east of north, following (cite: gam25)" (Results) [from (cite: gam25)]
- Line luminosity equation L' = 3.25e7 nu^-2 (1+z)^-1 D_L^2 S dV  
  > "from their fluxes (Table [4](#tab:Gauss)), using the following equation (cite: sol05)" (Discussion) [from (cite: sol05)]
- Dense H2 mass conversion from HCN and HCO+ J=1-0 luminosities  
  > "M$_{\rm dense-H_2}$(HCN) = 6–12 $\times$ L(HCN J=1–0)" (Discussion); "M$_{\rm dense-H_2}$(HCO$^{+}$) = 2–5 $\times$ L(HCO$^{+}$ J=1–0)" (Discussion) [from (cite: gao04; kri08; ler17)]
- Counter-rotating torus model compared with the data  
  > "Figure [10](#fig:VollmerPV) shows a detailed comparison of the position-velocity diagrams of the HCN J=4–3 and HCO$^{+}$ J=4–3 lines between our new $\lesssim$1 pc resolution data and the best-fit model of (cite: vol22)." (Discussion) [from (cite: vol22)]
- Foreground absorbing-cloud column density for RADEX  
  > "column density of 3 $\times$ 10$^{15}$ cm$^{-2}$ for HCO$^{+}$ (cite: gam25) and HCN" (Appendix A) [from (cite: gam25)]

### Not stated but needed to reproduce (our reading)

- tclean deconvolver, niter, threshold, cleaning masks and image size for the Cycle 9 cubes
- Exact line-free channel ranges used for uvcontsub and the fit order for each spectral window
- Weighting, uv taper and CASA version used for the reanalysed Cycle 6 J=3-2 cubes, and whether they were re-calibrated
- Whether any self-calibration or uv-range cuts were applied; whether executions were combined before imaging
- Primary-beam correction and the exact spectral frame/velocity definition used for cubes (optical V_sys = 1130 km/s is given)
- Moment-map clipping thresholds and how the beam-sized and circular-aperture spectra were extracted (center pixel, units)
- Gaussian-fit details in Appendix B (number of components, baseline treatment, error estimation)
- Procedure for the J=4-3 / J=3-2 ratio maps (regridding, clipping, mask)
- D_L value used in the luminosity equation
- RADEX setup (collision data, molecular data files, beam-filling) and how optical depths were compared
- Position-velocity slice width and how the VLBI maser spots were overplotted (the ~9 mas shift is stated, its direction/derivation is not)

## Analysis recipe

1. **Calibrate and image the Cycle 9 and Cycle 6 data**: Start from pipeline-calibrated data, subtract continuum with uvcontsub, then tclean line and continuum cubes on a common 1.5 mas, 10 km/s grid  
  > "We started our analysis with pipeline-calibrated data provided by ALMA, using CASA 6.5.4-9 (cite: CASA22; hun23)." (Observations and Data Analysis); "with a pixel scale of 0.0015$''$ pixel$^{-1}$ (1.5 mas pixel$^{-1}$) and a velocity resolution of 10 km s$^{-1}$." (Observations and Data Analysis)
   - software: CASA, uvcontsub, tclean
   - parameter: Briggs weighting, robust = 0.5, gain = 0.1  
  > "task (Briggs-weighting; robust $=$ 0.5, gain $=$ 0.1) to the continuum-subtracted molecular line and continuum data" (Observations and Data Analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum and line moment-0 peaks**: Continuum peak and integrated-intensity (moment 0) peaks of HCN, HCO+, CS at W-torus, E-torus and absorption peak, taking the highest-flux 1.5 mas pixel  
  > "The value at the highest flux pixel (1.5 mas pixel$^{-1}$) is adopted." (Table 2 notes); "The value at the highest or most negative flux pixel (1.5 mas pixel$^{-1}$) in the integrated intensity (moment 0) map" (Table 3 notes)
   - software: CASA
   - assumption: Continuum peak (C-peak) regarded as the position of the mass-accreting SMBH  
  > "which we regard as the position of the mass-accreting SMBH" (Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Extract beam-sized and area-integrated spectra**: Beam-sized spectra at C-peak, W-peak, E-peak; circular-aperture spectra of 1.7 pc diameter around W-peak and E-peak, and 3.4 and 6.8 pc diameter around C-peak  
  > "obtained with a 1.7 pc (24 mas) diameter circle around the W-peak and E-peak" (Results); "obtained with 3.4 pc (48 mas) and 6.8 pc (96 mas) diameter circles around the C-peak" (Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit Gaussians to emission lines to get fluxes**: Gaussian fits to HCN and HCO+ emission lines in area-integrated spectra (Appendix B) giving velocity-integrated fluxes  
  > "Gaussian fits are applied to the detected HCN and HCO$^{+}$ emission lines in the area-integrated spectra (Appendix B)." (Results)
   - fitting: Gaussian line profiles; sampler, priors and likelihood not stated  
  > "Gaussian fits are applied to the detected HCN and HCO$^{+}$ emission lines in the area-integrated spectra (Appendix B)." (Results)
   - validation: _not stated_
5. **Map kinematics: moment 1, moment 2, PV diagrams, compare with H2O masers**: Intensity-weighted mean velocity (moment 1) and velocity dispersion (moment 2) maps, PV diagrams along PA = 114 deg, and comparison of the HCN J=4-3 velocity profile with VLBI H2O maser spots after a ~9 mas positional shift  
  > "Figure [5](#fig:mom1) displays intensity-weighted mean velocity (moment 1) maps of the J=4–3 lines of HCN and HCO$^{+}$" (Results); "Intensity-weighted velocity dispersion (moment 2) maps of the J=4–3 lines of HCN and HCO$^{+}$" (Results); "Allowing for a slight ($\sim$9 mas) positional shift between the ALMA $\sim$350 GHz and VLBI $\sim$22 GHz data" (Results)
   - software: CASA
   - parameter: Systemic velocity V_sys = 1130 km/s; moment-1 redshift/blueshift ranges V_sys ± 110 km/s (J=4-3) and ± 60 km/s (J=3-2) for Figures 5e,f  
  > "V$_{\rm sys}$ ± 110 km s$^{-1}$ and V$_{\rm sys}$ ± 60 km s$^{-1}$, respectively" (Results)
   - fitting: _not stated_
   - validation: _not stated_
6. **Derive J=4-3 / J=3-2 and HCN/HCO+ flux-ratio maps**: Ratio maps in Jy beam-1 km s-1 after matching synthesized beams, compared with 16/9 expected for thermalised optically thick emission  
  > "after making their synthesized beams identical" (Results); "If the emission is thermalized and optically thick, the expected flux ratio is 16/9 (=1.8) when calculated in units of Jy beam$^{-1}$ km s$^{-1}$." (Results)
   - assumption: Absolute flux calibration uncertainty <~10% per observation gives a maximum ratio ~2.2 for thermalised, optically thick emission  
  > "which could produce the ratio with maximum $\sim$2.2 (=1.1/0.9 $\times$ 1.8) for the thermalized, optically thick emission" (Results)
   - fitting: _not stated_
   - validation: _not stated_
7. **Convert fluxes to line luminosities**: L' (K km/s pc2) = 3.25e7 nu_rest^-2 (1+z)^-1 D_L^2 S dV applied to the Gaussian-fit fluxes  
  > "where S$\Delta$V is the Gaussian-fit, velocity-integrated emission line flux (in Jy km s$^{-1}$) and D$_{L}$ is the luminosity distance (in Mpc)." (Discussion)
   - fitting: _not stated_
   - validation: _not stated_
8. **Compare data with the counter-rotating torus model**: Compare PV diagrams and spectra along the major axis (PA = 110 deg) with the best-fit model of Vollmer et al. (2022)  
  > "Observed and predicted spectra at multiple positions along the major axis (PA = 110$^{\circ}$) are compared in Figure [11](#fig:VollmerSpectra)." (Discussion)
   - fitting: No new fit; existing best-fit model compared  
  > "The overall properties largely agree between the model and observations, as in the case for other molecular lines (cite: vol22)." (Discussion)
   - validation: Qualitative agreement; east-west asymmetry not reproduced  
  > "The observed east-west asymmetry of dense molecular line emission appears not to be adequately reproduced by the best-fit model of (cite: vol22)" (Discussion)
9. **Estimate dense H2 gas mass in the torus**: Assume HCN (HCO+) J=1-0 luminosity equals the J=4-3 / J=3-2 luminosity (~20e4 and ~12e4 K km/s pc2 for the 6.8 pc aperture) and apply the literature conversion factors  
  > "Assuming that the HCN J=1–0 luminosity in these units is also comparable to that of HCN J=3–2 and J=4–3" (Discussion); "Assuming that the HCO$^{+}$ J=1–0 luminosity in these units is comparable to that of HCO$^{+}$ J=4–3 and J=3–2" (Discussion)
   - assumption: Optically thick, thermalised emission; standard HCN and HCO+ abundances  
  > "because standard HCN and HCO$^{+}$ abundances are assumed for the above conversion from line luminosity to dense H$_{2}$ mass" (Discussion)
   - fitting: _not stated_
   - validation: HCO+ mass compared with the Vollmer et al. adopted value of 3.6e5 Msun  
  > "The HCO$^{+}$-derived torus dense H$_{2}$ mass is roughly comparable to the value adopted (3.6 $\times$ 10$^{5}$ M$_{\odot}$) in the modeling of (cite: vol22)" (Discussion)
10. **Test the ~400 km/s redshifted HCO+ absorption scenarios with RADEX**: RADEX models of a foreground absorbing cloud; compare HCO+ J=4-3 vs HCN J=3-2 absorption optical depth for background temperatures of ~3 K and ~350 K  
  > "We ran RADEX calculations (cite: van07) for a foreground absorbing gas cloud" (Appendix A); "By inputting a background temperature of 350 K for our RADEX calculations" (Appendix A)
   - software: RADEX
   - parameter: Volume density 1e5-1e6 cm-3, Tkin 50-150 K, N = 3e15 cm-2 for HCO+ and HCN, line width 300 km/s  
  > "for a volume density of 10$^{5-6}$ cm$^{-3}$, kinetic temperature of 50–150 K" (Appendix A)
   - assumption: HCN and HCO+ abundances comparable  
  > "The above comparison implicitly assumes that the HCN and HCO$^{+}$ abundances are comparable." (Appendix A)
   - assumption: Background temperature ~350 K from the continuum brightness temperature  
  > "We obtain a brightness temperature of $\sim$350 K from these continuum data." (Appendix A)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.5.4-9: Calibration products, continuum subtraction and imaging  
  > "using CASA 6.5.4-9 (cite: CASA22; hun23)" (Observations and Data Analysis)
- **uvcontsub** : Continuum subtraction  
  > "subtracted it using the CASA task" (Observations and Data Analysis)
- **tclean** : Imaging of lines and continuum with Briggs robust = 0.5  
  > "task (Briggs-weighting; robust $=$ 0.5, gain $=$ 0.1) to the continuum-subtracted molecular line and continuum data" (Observations and Data Analysis)
- **RADEX** : Absorption optical depth of foreground gas for HCO+ and HCN  
  > "We ran RADEX calculations (cite: van07) for a foreground absorbing gas cloud" (Appendix A)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum peak flux at ~350 GHz | 6.8 | 116 sigma; rms 0.059 mJy/beam | mJy/beam | 2 | 6.8 (116$\sigma$) |
| Continuum peak flux at ~260 GHz | 6.7 | 89 sigma; rms 0.075 mJy/beam | mJy/beam | 2 | 6.7 (89$\sigma$) |
| HCN J=4-3 moment-0 peak, W-torus | 0.77 | 13.9 sigma | Jy km/s/beam | 2 | 0.77 (13.9$\sigma$) |
| HCO+ J=4-3 moment-0 peak, W-torus | 0.68 | 11.8 sigma | Jy km/s/beam | 2 | 0.68 (11.8$\sigma$) |
| HCN J=4-3 flux, W-torus (1.7 pc diameter) | 0.96 | 0.10 | Jy km/s | 4 | 0.96$\pm$0.10 |
| HCN J=4-3 flux, E-torus (1.7 pc diameter) | 0.73 | 0.05 | Jy km/s | 4 | 0.73$\pm$0.05 |
| HCN J=4-3 flux, 6.8 pc diameter aperture | 4.3 | 0.3 | Jy km/s | 4 | We estimate the HCN J=4–3 emission line flux within the 6.8 pc diameter aperture around the central continuum-emitting AGN to be 4.3$\pm$0.3 Jy km s$^{-1}$ |
| HCO+ J=4-3 flux, 6.8 pc diameter aperture | 2.5 | 0.2 | Jy km/s | 4 | The HCO$^{+}$ J=4–3 emission line flux within the same 6.8 pc aperture is estimated to be 2.5$\pm$0.2 Jy km s$^{-1}$ |
| HCN J=4-3 luminosity, W-torus (1.7 pc) | 4.8e4 | 0.5e4 | K km/s pc^2 | 7 | 4.8$\pm$0.5 |
| HCN J=3-2 luminosity, W-torus (1.7 pc) | 2.8e4 | 0.6e4 | K km/s pc^2 | 7 | 2.8$\pm$0.6 |
| HCN J=4-3 luminosity, 6.8 pc aperture | 21.7e4 | 1.5e4 | K km/s pc^2 | 7 | 21.7$\pm$1.5 |
| HCN J=3-2 luminosity, 6.8 pc aperture | 18.0e4 | 0.9e4 | K km/s pc^2 | 7 | 18.0$\pm$0.9 |
| J=4-3 to J=3-2 flux ratio near W-peak and innermost torus | >~2.5 | not stated | dimensionless | 6 | show flux ratios with $\gtrsim$2.5. |
| Most redshifted HCN J=4-3 velocity on NW side | V ~ 1470 (dV_red ~ +340) | not stated | km/s | 5 | the most redshifted component on the NW side has an intensity-weighted velocity as high as V $\sim$ 1470 km s$^{-1}$ ($\Delta$V$_{\rm red}$ $\sim$ $+$340 km s$^{-1}$) |
| Outer blueshifted HCN J=4-3 velocity along NW direction | ~ -40 relative to V_sys = 1130 | not stated | km/s | 5 | but the outer blueshifted velocity is only $\Delta$V$_{\rm blue}$ $\sim$ $-$40 km s$^{-1}$ relative to the systemic velocity |
| Dense H2 mass from HCN | (1.2–2.4)e6 | not stated | Msun | 9 | we obtain HCN-derived torus dense molecular H$_{2}$ gas mass of M$_{\rm dense-H_2}$(HCN) = (1.2–2.4) $\times$ 10$^{6}$ M$_{\odot}$. |
| Dense H2 mass from HCO+ | (2.4–6.0)e5 | not stated | Msun | 9 | we obtain HCO$^{+}$-derived torus dense H$_{2}$ mass of M$_{\rm dense-H_2}$(HCO$^{+}$) = (2.4–6.0) $\times$ 10$^{5}$ M$_{\odot}$. |
| HCN-VIB J=4-3 absorption optical depth toward the continuum peak | ~0.08 (~7% of 6.8 mJy/beam continuum; dip ~0.5 mJy/beam) | not stated | dimensionless | 10 | or $\sim$7% ($\tau$ $\sim$ 0.08) for the $\sim$350 GHz continuum flux of $\sim$6.8 mJy beam$^{-1}$ |
| Brightness temperature of the continuum | ~350 | not stated | K | 10 | We obtain a brightness temperature of $\sim$350 K from these continuum data. |

## Qualitative findings

- HCN and HCO+ J=4-3 are in absorption at the continuum peak  
  > "At the C-peak, the HCN J=4–3 and HCO$^{+}$ J=4–3 lines are observed in absorption" (Results)
- J=4-3 emission is more compact than J=3-2 for both HCN and HCO+  
  > "the J=4–3 emission is spatially more compact than the J=3–2 emission for both HCN and HCO$^{+}$." (Results)
- No gap at the putative collision interface is seen even at the highest resolution  
  > "we see no clear signature of such a gap even in our highest-spatial-resolution" (Discussion)
- HCN is brighter than HCO+ in both the western and eastern torus, and the western torus is brighter than the eastern  
  > "the western torus is brighter than the eastern torus for both the HCN J=4–3 and HCO$^{+}$ J=4–3 lines." (Results)
- Blueshifted absorption wing toward the SMBH is stronger in HCN than HCO+, consistent with enhanced HCN abundance  
  > "is stronger for HCN J=4–3 than for HCO$^{+}$ J=4–3" (Summary)

## Claim tuples

- H: Does the apparent counter-rotation seen at ~1.5 pc in J=3-2 persist at higher resolution in J=4-3? | E: Moment-1 maps and spectra of HCN and HCO+ J=4-3 compared with reanalysed J=3-2 | R: Inner western torus is redshifted and outer part blueshifted for both J=4-3 lines; in the east the outer redshifted component is not clearly seen | F: Apparent counter-rotation is confirmed in the western torus | **supported**
- H: Is HCN brighter than HCO+ in the compact torus at J=4-3? | E: Moment-0 maps and Gaussian-fit fluxes | R: HCN J=4-3 brighter than HCO+ J=4-3 in the western and eastern torus | F: Consistent with enhanced HCN abundance, as at J=3-2 | **supported**
- H: Is dense-gas emission near the W-peak and E-peak optically thin and turbulent? | E: J=4-3 vs J=3-2 luminosities and flux ratios in 1.7 pc apertures versus the 6.8 pc aperture | R: J=4-3 luminosity is a factor >~1.7 higher than J=3-2 in the 1.7 pc apertures, while the 6.8 pc values are within ~20% | F: Emission is optically thin there, with high turbulence a natural explanation | **partially**
- H: Does the collision-induced physically counter-rotating torus model of Vollmer et al. reproduce the J=4-3 data? | E: Compare PV diagrams and spectra with the model; look for a predicted gap and shock excitation | R: Absorption at the systemic velocity and overall properties agree; east-west asymmetry not reproduced; no gap or shock-driven line-ratio increase detected | F: Model largely reproduces the data but definitive confirmation is not possible at ~1 pc resolution | **partially**
- H: Is the innermost redshifted HCN gas connected to the H2O maser disk? | E: Compare HCN J=4-3 velocity profile with VLBI maser spots after a ~9 mas shift | R: HCN J=4-3 reaches V ~ 1470 km/s on the NW side, similar to the redshifted maser | F: Redshifted HCN gas is physically connected to the redshifted maser-emitting disk | **supported**
- H: What causes the ~400 km/s redshifted HCO+ absorption: HCN-VIB at the systemic velocity or an infalling cloud? | E: Frequency coincidence with HCN-VIB and RADEX absorption models with a ~350 K background | R: Both scenarios can reproduce absorption seen in HCO+ but not HCN | F: Neither scenario can be excluded | **partially**

## Reasoning

- Why this data: Longest baseline and higher-frequency J=4-3 lines give sub-pc resolution and a more compact, warmer/denser gas probe  
  > "To achieve the highest angular resolution, the longest baseline" (Observations and Data Analysis); "the highest-angular-resolution HCN J=4–3 line data will enable us to better elucidate the dense molecular gas properties of the NGC 1068 torus." (Introduction)
- Why this method: J=3-2 data reanalysed on the same pixel and velocity grid for a straightforward comparison  
  > "We reanalyzed the HCN J=3–2 and HCO$^{+}$ J=3–2 data with pixel scale of 1.5 mas pixel$^{-1}$ and velocity resolution of 10 km s$^{-1}$ to compare them with the newly taken" (Observations and Data Analysis)
- Alternative: Outflow-origin scenario for the apparent counter-rotation: considered; difficult to reproduce the west-east asymmetry  
  > "the significant asymmetry of molecular gas emission observed between the western and eastern tori is difficult to reproduce solely with this outflow-origin model" (Discussion)
- Alternative: Infalling cloud without strong torus interaction (Gamez Rosas et al.): considered; no direct way to reduce line opacity near the W-peak  
  > "has no direct way to reduce the opacity of molecular line emission in the small areas around the W-peak" (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): ~1 pc resolution is still insufficient to resolve the predicted collision interface  
  > "the achieved $\lesssim$1 pc resolution is still insufficient to investigate the predicted collision interface between two counter-rotating gas components in detail." (Discussion)
- Limitation (authors): Systematic uncertainties from flux calibration and continuum level choice are not included in the quoted errors  
  > "Possible systematic uncertainties coming from absolute flux calibration ambiguity in individual ALMA observations and the choice of frequency range to determine the continuum level are not taken into account." (Table 2 notes)
- Caveat (inferred, ours): Imaging details (mask, threshold, niter, deconvolver) are absent, so flux and moment values may depend on them
- Caveat (inferred, ours): The J=3-2 and J=4-3 data come from different observations; ratios depend on beam matching and flux scale, and the 1.7 pc aperture ratio of ~1.7 is close to the stated 10% calibration effect only marginally
- Caveat (inferred, ours): Dense-gas masses assume J=1-0 luminosity equals J=3-2 and J=4-3 luminosity, which is untested here
- Caveat (inferred, ours): Optically thin interpretation at the peaks is inferred from luminosity ratios, not from radiative transfer fits
- Caveat (inferred, ours): Astrometric alignment with VLBI used a ~9 mas shift that is larger than the stated ALMA astrometric accuracy
- Caveat (inferred, ours): Only a qualitative comparison with the Vollmer model, no new model fit or goodness-of-fit metric

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Analysis starts from pipeline-calibrated data provided by ALMA  
  > "We started our analysis with pipeline-calibrated data provided by ALMA" (Observations and Data Analysis)
- Missing: Cleaning masks, thresholds and number of iterations
- Missing: Exact line-free channels for continuum subtraction
- Missing: Details of Gaussian fits (Appendix B)
- Missing: D_L used for luminosities
- Missing: RADEX inputs beyond those listed
- Missing: Weighting and imaging parameters for the Cycle 6 reanalysis
- Missing: Details of the model data from Vollmer et al. (2022)
- Data volume (inferred): Seven long-baseline Band 7 execution blocks (44 min each) plus one Cycle 6 dataset; raw data likely hundreds of GB, imaged cubes a few GB
- Score (inferred): 3/5, Projects and key tclean parameters (robust 0.5, 1.5 mas pixel, 10 km/s) and the luminosity equation are given, but masking, line-free channels, fit details and the comparison model are not; many numeric results are tabulated.
- Rediscovery candidate: yes, Both projects are cited by code and the recipe is mostly stated with tabulated numeric fluxes, luminosities and masses, though public status is not stated by the paper and cleaning details are missing.

## Links

- Method: The CASA Team et al. 2022, PASP, 134, 114501 (cite: CASA22) (CASA reference)
- Method: Hunter et al. 2023, PASP, 135, 074501 (cite: hun23) (Cited with CASA for the processing software)
- Method: Solomon & Vanden Bout 2005, ARA&A, 43, 677 (cite: sol05) (Line luminosity equation)
- Method: van der Tak et al. 2007, A&A, 468, 627 (cite: van07) (RADEX)
- Companion: Imanishi et al. 2020, ApJ, 902, 99 (cite: ima20) (Cycle 6 HCN/HCO+ J=3-2 data and earlier analysis)
- Companion: Impellizzeri et al. 2019, ApJL, 884, L28 (cite: imp19) (Earlier J=3-2 counter-rotation result)
- Companion: Vollmer et al. 2022, A&A, 665, A102 (cite: vol22) (Counter-rotating torus model compared with the data)
- Companion: Gamez Rosas et al. 2025, A&A, 699, A187 (cite: gam25) (Concurrent HCO+ J=4-3 and CO J=3-2 observations with the infalling cloud scenario)
- Related: ALMA Cycle 6 project 2018.1.00037.S
- Related: VLBI 22 GHz H2O maser observations of NGC 1068

## Checks

```json
{
 "quotes": 139,
 "quotes_ok": 139,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 19,
 "numeric_problems": 0,
 "fill": {
  "facts": 110,
  "stated": 79,
  "rate": 0.718
 },
 "evidence_ok": true
}
```
