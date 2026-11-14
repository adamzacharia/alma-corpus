# Unusually high CO abundance of the first active interstellar comet

`2020NatAs...4..861C` | Nature Astronomy 2020 | first author: Cordiner, M. A. | arXiv: 2004.09586 | DOI: 10.1038/s41550-020-1087-2

Card schema 1.0 | model gpt-6.1-sol | depth full | type observational_alma_primary

## Science

- Fields: solar_system, astrochemistry
- Question: Parent volatile composition of 2I/Borisov and implications for its natal environment.  
  > "Observations of the interstellar comet 2I/Borisov provide unique new insights into the chemistry that occurred during planet formation in another stellar system." (Unusually High CO Abundance of the First Active Interstellar Comet); "This shows that 2I/Borisov must have formed in a relatively CO-rich environment" (abstract)
- Target **2I/Borisov**: coordinates _not stated_; z/distance Heliocentric distance 2.01 au; geocentric distance 1.96 au.  
  > "at a heliocentric distance $r_H=2.01$ au and a geocentric distance $\Delta=1.96$ au." (Unusually High CO Abundance of the First Active Interstellar Comet); distance from _not stated_

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: 342.9-355.6 GHz (0.84-0.87 mm); CS 342.883 GHz / 282 kHz; CO 345.796 GHz / 244 kHz; HCN 354.505 GHz / 244 kHz; CH3OH 355.603 GHz / 488 kHz.  
  > "in the frequency range 342.9-355.6 GHz (0.84-0.87 mm)" (Unusually High CO Abundance of the First Active Interstellar Comet); "The correlator was configured to observe rotational transitions of CS (342.883 GHz), CO (345.796 GHz), HCN (354.505 GHz) and CH$_3$OH (355.603 GHz)" (Observations); "with spectral resolutions of 282 kHz, 244 kHz, 244 kHz, and 488 kHz, respectively." (Observations)
- continuum bandwidth: _not stated_
- arrays: 42 active 12 m antennas; simultaneous interferometric and autocorrelation spectra.  
  > "Autocorrelation (total power) spectra were recorded using each of the forty-two 12 m ALMA antennas, simultaneously with the interferometric (cross correlation) observations." (Observations)
- configurations: C43-1  
  > "There were 42 active antennas in the array (configuration C43-1)" (Observations)
- baselines: 15-317 m  
  > "spanning baselines 15-317 m" (Observations)
- angular resolution: 1.02'' × 0.73'' at 355 GHz; autocorrelation beam FWHM 16.8''.  
  > "resulting in a spatial resolution (elliptical beam FWHM) of $1.02''\times0.73''$ at 355 GHz." (Observations); "The zenith sky opacity was 0.11 and the single-dish beam FWHM was $16.8''$." (Observations)
- max recoverable scale: _not stated_
- sensitivity: Combined cubes: σc = 2.6 mJy for CO and 2.9 mJy for HCN; continuum 3σ upper limit 0.11 mJy beam^-1.  
  > "The resulting, combined image cubes are in the rest frame of the comet, with $\sigma_c=2.6$ mJy for CO and 2.9 mJy for HCN." (Observations); "the RMS noise on our combined continuum image resulted in a $3\sigma$ upper limit to the dust/nucleus thermal emission of 0.11 mJy beam$^{-1}$." (Observations)
- time on source: 1:11 on-source  
  > "with a total observing time of 1:11 on-source." (Observations)
- observing dates: UT 2019-12-15 8:50–12:03; UT 2019-12-16 11:37–12:56.  
  > "ALMA observations were performed as part of program 2019.01008.T on UT 2019-12-15 8:50–12:03 and UT 2019-12-16 11:37–12:56, with a total observing time of 1:11 on-source." (Observations)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (345.796 GHz)
- Line: HCN J=4-3 (354.505 GHz)
- Line: CS J=7-6 (342.883 GHz)
- Line: CH3OH J_K=13_0 - 12_1 A^+ (355.603 GHz)
- Other facility **SWIFT satellite**: UV observations of OH used for the H2O production rate.  
  > "The comet’s H$_2$O production rate was obtained from UV observations of OH using the SWIFT satellite(cite: bod20)." (Radiative Transfer Modeling)
- Other facility **60 cm TRAPPIST-South telescope, La Silla Observatory**: CN narrow-band and broad-band optical images on December 15, 18 and 19.  
  > "2I/Borisov was observed with the 60 cm TRAPPIST-South telescope located at La Silla Observatory, Chile(cite: jeh11) on December 15, 18 and 19 (UT)." (Optical Observations of CN); "On each night a long (1500 s) exposure was obtained trough a CN (0-0) narrow-band filter(cite: far00) centered at 387 nm and various broad band filters (Johnson-Cousins B, V, Rc, Ic)." (Optical Observations of CN)
- External data: SWIFT OH-derived H2O production rates: December 1, (10.7±1.2)×10^26 s^-1; December 21, (4.9±0.9)×10^26 s^-1.  
  > "The comet’s H$_2$O production rate was obtained from UV observations of OH using the SWIFT satellite(cite: bod20)." (Radiative Transfer Modeling); "the observed values on December 1st ($(10.7\pm1.2)\times10^{26}$ s$^{-1}$) and December 21st ($(4.9\pm0.9)\times10^{26}$ s$^{-1}$)" (Radiative Transfer Modeling) [from Xing et al.(cite: bod20)]
- External data: H2 collisional rates substituted for HCN collisions with H2O and CO.  
  > "Collisional rates for HCN with H$_2$O and CO were taken from the H$_2$ collisional rates in the Leiden Atomic and Molecular Database (cite: sch05)." (Radiative Transfer Modeling) [from (cite: sch05)]
- External data: Radiative pumping and photodissociation rates scaled to r_H = 2.01 au.  
  > "Radiative pumping and photodissociation rates(cite: hue15) were appropriately scaled for the comet’s heliocentric distance ($r_H=2.01$ au)." (Radiative Transfer Modeling) [from (cite: hue15)]
- External data: Aperture efficiency η_A = 0.63 at 345 GHz.  
  > "the aperture efficiency ($\eta_A=0.63$ at 345 GHz)(cite: alm19)" (Observations) [from (cite: alm19)]
- External data: Previously observed radio and infrared coma temperatures at 1.7-2.4 au, compiled in Supplementary Table 1.  
  > "based on the temperatures previously observed at radio and infrared wavelengths for comets in the distance range 1.7-2.4 au (Supplementary Table 1)." (Radiative Transfer Modeling) [from Supplementary Table 1]
- External data: Typical coma outflow velocities ∼0.5-0.7 km s^-1 at r_H = 2 au.  
  > "given typical coma outflow velocities $\sim0.5$-$0.7$ km s$^{-1}$ at $r_H=2$ au(cite: coc93; biv99; biv19)" (Radiative Transfer Modeling) [from (cite: coc93; biv99; biv19)]
- External data: Effective scale lengths for the optical CN Haser model.  
  > "using effective scale lengths from Cochran & Schleicher(cite: coc93) and an outflow velocity of 0.5 km s$^{-1}$." (Optical Observations of CN) [from Cochran & Schleicher(cite: coc93)]
- External data: Solar System comet HCN average abundance 0.12%; CS and CH3OH comparison abundance ranges.  
  > "HCN is close to the average abundance of 0.12% observed previously in Solar System comets(cite: boc18)" (Unusually High CO Abundance of the First Active Interstellar Comet); "with CS in the range 0.02–0.2% and CH$_3$OH is in the range 0.6–6.2%)(cite: boc18)." (Radiative Transfer Modeling) [from (cite: boc18)]
- External data: Solar System comet average CO abundance 4%; CO-rich Oort Cloud comet CO/H2O ratios 10%-24%.  
  > "the CO abundance is much higher than the average value of 4%(cite: pag14a)." (Unusually High CO Abundance of the First Active Interstellar Comet); "Even Oort Cloud comets previously designated as CO-rich only have CO/H$_2$O ratios in the range 10% to 24%(cite: pag14a)" (Unusually High CO Abundance of the First Active Interstellar Comet) [from (cite: pag14a)]
- External data: C/2016 R2 CO/H2O = 30,800%.  
  > "which had CO/H$_2$O = 30,800%(cite: mck19)." (Unusually High CO Abundance of the First Active Interstellar Comet) [from (cite: mck19)]
- External data: C/2016 R2 CO/HCN = 26,400 at r_H = 2.8 au.  
  > "which had CO/HCN = 26,400 (at $r_H=2.8$ au)(cite: biv18)." (Unusually High CO Abundance of the First Active Interstellar Comet) [from (cite: biv18)]
- External data: Literature CO and HCN data for five comets observed at r_H = 1.7–2.4 au.  
  > "Supplementary Table 1 provides literature data for CO and HCN in five comets observed at $r_H=1.7$–$2.4$ au, including several CO-rich comets." (Unusually High CO Abundance of the First Active Interstellar Comet) [from Supplementary Table 1]
- External data: C/2006 W3 CO/HCN = 238±21 at r_H = 3.3 au.  
  > "the next highest CO/HCN ratio ($238\pm21$) was for C/2006 W3 (Christensen), at a relatively large heliocentric distance $r_H=3.3$ au(cite: boc10)." (Unusually High CO Abundance of the First Active Interstellar Comet) [from (cite: boc10)]
- External data: HCN and H2O sublimation temperatures 95-150 K, expected on illuminated comet surfaces within r_H ∼3 au.  
  > "the 95-150 K sublimation temperatures ($T_{sub}$) of HCN and H$_2$O are expected to be reached on the illuminated surfaces of comets within $r_H\sim3$ au(cite: wom17)" (Unusually High CO Abundance of the First Active Interstellar Comet) [from (cite: wom17)]
- External data: AKARI comet sample: relative reduction in H2O production only at r_H > 2.5 au.  
  > "in a sample of 17 comets with CO$_2$ measured by the AKARI satellite, a relative reduction in the H$_2$O production rate was only found to occur at distances $r_H>2.5$ au(cite: oot12)." (Unusually High CO Abundance of the First Active Interstellar Comet) [from (cite: oot12)]
- External data: Protosolar CO ice-line estimate 17-35 au.  
  > "The CO ice line in our protosolar nebula has been estimated to be located in the outer part of the cometary formation zone, between about 17-35 au(cite: qi13; mor19)." (Unusually High CO Abundance of the First Active Interstellar Comet) [from (cite: qi13; mor19)]
- External data: Kuiper Belt density drop-off close to 50 au.  
  > "Currently, the outer edge of the Solar System (as defined by a drop-off in the Kuiper Belt density), is close to 50 au(cite: gla08)." (Unusually High CO Abundance of the First Active Interstellar Comet) [from (cite: gla08)]
- External data: CO ice-lines in other systems at similar or greater stellar distances.  
  > "In other planetary systems, the CO ice-line has been identified at similar or greater distances from the star(cite: qi13; zha19; qi19)" (Unusually High CO Abundance of the First Active Interstellar Comet) [from (cite: qi13; zha19; qi19)]
- External data: Young planetary disks with outer radii 5-200 au.  
  > "Observations of disks during the initial stages of planetary assembly find that their outer radii extend 5-200 au(cite: and20)." (Unusually High CO Abundance of the First Active Interstellar Comet) [from (cite: and20)]
- External data: ALMA-inferred Neptune to Saturnian sized objects at outer-disk distances.  
  > "Furthermore, ALMA has recently inferred the presence of large, Neptune to Saturnian sized objects at these distances(cite: zha18)." (Unusually High CO Abundance of the First Active Interstellar Comet) [from (cite: zha18)]
- External data: Chemical evolution models near H2O, CO and CO2 ice-lines.  
  > "Models for the formation and composition of cometary ices suggest significant chemical evolution within the protoplanetary disk close to the ice-lines of key volatiles such as H$_2$O, CO, and CO$_2$ (cite: obe11; eis18)." (Unusually High CO Abundance of the First Active Interstellar Comet) [from (cite: obe11; eis18)]
- External data: Outward diffusion of evaporated ice as an ice-enrichment mechanism.  
  > "It has long been theorized that evaporated ices inside the vapor region of a given ice-line would diffuse outwards (away from the star) and potentially enhance the ice-content of materials at larger radii(cite: ste88)." (Unusually High CO Abundance of the First Active Interstellar Comet) [from (cite: ste88)]
- External data: Radiogenic heating and re-freezing as a mechanism for CO-enriched layers.  
  > "Radiogenic heating of larger Kuiper-belt objects/small planets can enable the sublimation/diffusion of interior CO ice, which may then re-freeze in the cooler regions closer to the object’s surface, thus leading to CO-enriched layers (cite: des01)." (Unusually High CO Abundance of the First Active Interstellar Comet) [from (cite: des01)]
- Simulation/model as data: Cometary ice chemical-evolution models used to interpret formation near ice-lines.  
  > "Models for the formation and composition of cometary ices suggest significant chemical evolution within the protoplanetary disk close to the ice-lines of key volatiles such as H$_2$O, CO, and CO$_2$ (cite: obe11; eis18)." (Unusually High CO Abundance of the First Active Interstellar Comet)
- Simulation/model as data: Radiogenic differentiation models considered as an alternative source of CO-rich material.  
  > "Radiogenic heating of larger Kuiper-belt objects/small planets can enable the sublimation/diffusion of interior CO ice, which may then re-freeze in the cooler regions closer to the object’s surface, thus leading to CO-enriched layers (cite: des01)." (Unusually High CO Abundance of the First Active Interstellar Comet)

## Processing

### Calibration

- pipeline or manual: Flagged and calibrated using automated pipeline scripts supplied by the Joint ALMA Observatory.  
  > "Data were flagged and calibrated with CASA version 5.6(cite: jae08) using the automated pipeline scripts supplied by the Joint ALMA Observatory." (Observations)
- casa version: CASA 5.6  
  > "Data were flagged and calibrated with CASA version 5.6(cite: jae08)" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1209-2406; also the phase calibrator.  
  > "Flux and phase calibration were performed using the quasar J1209-2406." (Observations)
- flux scale uncertainty: Autocorrelation amplitude calibration error ±10%.  
  > "Modeling the autocorrelation data assuming isotropic outgassing from the nucleus results in a CO production rate of $(5.0\pm0.5)\times10^{26}$ s$^{-1}$ (assuming an amplitude calibration error of $\pm10$%)." (Unusually High CO Abundance of the First Active Interstellar Comet)
- self calibration: _not stated_

### Imaging

- task: tclean; deconvolution, Doppler correction and imaging.  
  > "Deconvolution, Doppler correction and imaging were performed using the `tclean` (Clark) algorithm" (Observations)
- deconvolver: Clark  
  > "Deconvolution, Doppler correction and imaging were performed using the `tclean` (Clark) algorithm" (Observations)
- weighting robust: Natural weighting.  
  > "with natural weighting, a flux threshold of twice the RMS noise per channel ($\sigma_c$) in each image" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: 6''-diameter circular mask about the phase center; cleaning threshold twice the RMS noise per channel.  
  > "a flux threshold of twice the RMS noise per channel ($\sigma_c$) in each image, and a $6''$-diameter circular mask about the phase center." (Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.02'' × 0.73'' at 355 GHz.  
  > "resulting in a spatial resolution (elliptical beam FWHM) of $1.02''\times0.73''$ at 355 GHz." (Observations)
- final rms: σc = 2.6 mJy for CO; 2.9 mJy for HCN.  
  > "The resulting, combined image cubes are in the rest frame of the comet, with $\sigma_c=2.6$ mJy for CO and 2.9 mJy for HCN." (Observations)

### Inherited from earlier work

- Autocorrelation calibration and combination method.  
  > "These were calibrated and combined following the method of Cordiner et al.(cite: cor19)" (Observations) [from Cordiner et al.(cite: cor19)]
- Modified LIME adapted for cometary comae.  
  > "using a modified version of the LIne Modeling Engine (LIME)(cite: bri10), adapted for cometary comae as described by Cordiner et al.(cite: cor19)." (Radiative Transfer Modeling) [from Cordiner et al.(cite: cor19)]
- H2 collision rates used for HCN collisions with H2O and CO.  
  > "Collisional rates for HCN with H$_2$O and CO were taken from the H$_2$ collisional rates in the Leiden Atomic and Molecular Database (cite: sch05)." (Radiative Transfer Modeling) [from (cite: sch05)]
- Beam efficiency from aperture efficiency using η_MB = 0.8899 k^2 η_A, k = 1.13.  
  > "using the standard relationship(cite: dow89) $\eta_{\rm MB}=0.8899k^2\eta_A$, with k=1.13 for the ALMA 12-m antennas." (Observations) [from (cite: dow89)]
- Optical reduction and standard-star zero-point flux calibration procedures.  
  > "Data reduction followed standard procedures using frequently updated master bias, flat, dark frames and the flux calibration was performed with zero points obtained from regular standard star observations(cite: opi16; mou18)." (Optical Observations of CN) [from (cite: opi16; mou18)]
- Effective scale lengths for the CN Haser fit.  
  > "using effective scale lengths from Cochran & Schleicher(cite: coc93) and an outflow velocity of 0.5 km s$^{-1}$." (Optical Observations of CN) [from Cochran & Schleicher(cite: coc93)]

### Not stated but needed to reproduce (our reading)

- The paper's program identifier is printed as 2019.01008.T; an unambiguous archive identifier is needed.
- Spectral-window bandwidths, channel selections, and the construction of the combined continuum image.
- Image cell size, image dimensions, exact spectral regridding, and primary-beam correction treatment.
- Exact line-free channels, polynomial orders, and interpolation interval for the autocorrelation telluric residual.
- Autocorrelation scan and antenna rejection, weighting, and combination details delegated to Cordiner et al.
- The modified LIME implementation, grid and radial boundaries, density prescriptions, and electron density profile underlying x_ne.
- Nonlinear optimizer, parameter bounds, spectral weights, and uncertainty calculation.
- Exact Supplementary Table 1 inputs and optical CN effective scale lengths.

## Analysis recipe

1. **Image the interferometric data**: Deconvolve, Doppler-correct and image calibrated data with tclean, producing combined cubes in the comet rest frame.  
  > "Deconvolution, Doppler correction and imaging were performed using the `tclean` (Clark) algorithm" (Observations); "The resulting, combined image cubes are in the rest frame of the comet" (Observations)
   - software: CASA, tclean
   - parameter: Clark; natural weighting; threshold 2σc; 6''-diameter circular mask.  
  > "with natural weighting, a flux threshold of twice the RMS noise per channel ($\sigma_c$) in each image, and a $6''$-diameter circular mask about the phase center." (Observations); "using the `tclean` (Clark) algorithm" (Observations)
   - fitting: _not stated_
   - validation: Combined-cube RMS: 2.6 mJy for CO and 2.9 mJy for HCN.  
  > "with $\sigma_c=2.6$ mJy for CO and 2.9 mJy for HCN." (Observations)
2. **Measure maps, spectra and continuum limits**: Integrate cubes over cometocentric velocities; extract spectra at species flux peaks and measure per-beam integrated fluxes; inspect combined continuum.  
  > "Spectra for CO and HCN were then extracted at the respective flux peaks for each species (both of which were within $0.3''$ of the phase center)." (Observations); "Integrated fluxes (per beam) for each species are given in Table 1." (Observations); "No continuum emission was detected" (Observations)
   - parameter: Map integration: HCN −0.3 to 0.3 km s^-1; CO −0.6 to 0.6 km s^-1.  
  > "The spectral cubes were integrated over the cometocentric velocity range $-0.3$ to $0.3$ km s$^{-1}$ for HCN and $-0.6$ to $0.6$ km s$^{-1}$ for CO to produce the maps shown in Figure 1." (Observations)
   - parameter: CS and CH3OH spectra extracted at the HCN peak, 0.2'' East of center.  
  > "For CS and CH$_3$OH (not detected), the spectra were extracted at the HCN peak ($0.2''$ East of center)." (Observations)
   - fitting: _not stated_
   - validation: Integrated-flux significance: HCN 5.2σ; CO 5.9σ.  
  > "Spectrally integrated fluxes are given in Table 1, and correspond to a statistical significance of $5.2\sigma$ for HCN and $5.9\sigma$ for CO." (Unusually High CO Abundance of the First Active Interstellar Comet)
3. **Reduce the autocorrelation spectra**: Calibrate and combine individual-antenna spectra using interleaved sky references; correct beam efficiency, Doppler shift, subtract polynomial baselines, and interpolate over residual telluric CO.  
  > "using the interleaved sky reference position to subtract thermal contributions from the sky, receiver and telescope optics from each scan." (Observations); "The calibrated autocorrelation spectra were then Doppler shifted from the topocentric frame to the comet’s rest velocity." (Observations); "A spectral baseline offset was subtracted using low-order polynomial fits to the line-free channels." (Observations)
   - parameter: Sky reference 2' North; sequence 30 s calibrator, 2 min comet, 2 min reference.  
  > "The observing sequence consisted of 30 s on the phase calibrator, 2 min on the comet, and 2 min on a sky reference position $2'$ North of the comet" (Observations)
   - parameter: η_MB = 0.72; η_A = 0.63 at 345 GHz; η_MB = 0.8899 k^2 η_A with k = 1.13.  
  > "The data were corrected for a beam efficiency $\eta_{\rm MB}=0.72$, which was derived from the aperture efficiency ($\eta_A=0.63$ at 345 GHz)(cite: alm19)" (Observations); "using the standard relationship(cite: dow89) $\eta_{\rm MB}=0.8899k^2\eta_A$, with k=1.13 for the ALMA 12-m antennas." (Observations)
   - parameter: Residual telluric CO at 6.6 km s^-1 removed by linear interpolation.  
  > "A narrow residual feature due to incomplete telluric CO cancellation (at 6.6 km s$^{-1}$ in the comet’s rest frame) was removed by linear interpolation." (Observations)
   - fitting: Low-order polynomial fits to line-free channels.  
  > "A spectral baseline offset was subtracted using low-order polynomial fits to the line-free channels." (Observations)
   - validation: _not stated_
4. **Estimate water production at the ALMA epoch**: Linearly interpolate SWIFT OH-derived H2O production rates from December 1 and December 21.  
  > "A linear interpolation of the observed values on December 1st ($(10.7\pm1.2)\times10^{26}$ s$^{-1}$) and December 21st ($(4.9\pm0.9)\times10^{26}$ s$^{-1}$) results in $Q({\rm H_2O})=(6.5\pm1.0)\times10^{26}$ s$^{-1}$ at the epoch of our ALMA observations." (Radiative Transfer Modeling)
   - assumption: Linear interpolation between the two observed water production rates.  
  > "A linear interpolation of the observed values on December 1st" (Radiative Transfer Modeling)
   - fitting: _not stated_
   - validation: _not stated_
5. **Construct molecular excitation models**: Modified cometary LIME: three-dimensional NLTE radiative transfer with molecular and electron collisions and solar pumping; use LTE for CO.  
  > "using a modified version of the LIne Modeling Engine (LIME)(cite: bri10), adapted for cometary comae as described by Cordiner et al.(cite: cor19)." (Radiative Transfer Modeling); "This three-dimensional, non-local-thermodynamic-equilibrium (NLTE) radiative transfer model incorporates a calculation of the rotational energy level populations resulting from collisions with gas-phase molecules and electrons, as well as pumping by solar radiation." (Radiative Transfer Modeling); "LTE was found to be appropriate for modeling our observations of this molecule, with the benefit of improved computational efficiency." (Radiative Transfer Modeling)
   - software: LIME
   - parameter: Scale radiative pumping and photodissociation rates to r_H = 2.01 au.  
  > "Radiative pumping and photodissociation rates(cite: hue15) were appropriately scaled for the comet’s heliocentric distance ($r_H=2.01$ au)." (Radiative Transfer Modeling)
   - assumption: HCN-H2O and HCN-CO collisions represented by H2 collisional rates.  
  > "Collisional rates for HCN with H$_2$O and CO were taken from the H$_2$ collisional rates in the Leiden Atomic and Molecular Database (cite: sch05)." (Radiative Transfer Modeling)
   - assumption: Nominal electron density scaling x_ne = 1.0; kinetic temperature 50 K.  
  > "Our nominal model assumed a standard electron density scaling factor of $x_{n_e}=1.0$ and kinetic temperature $T_{kin}=$ 50 K to obtain the results given in Table 1" (Radiative Transfer Modeling)
   - fitting: _not stated_
   - validation: Scaling H2 collision rates by 0.1-10 changed HCN production rates by only 2%.  
  > "The impact of this assumption was tested by scaling the H$_2$ collision rates by a factor of 0.1-10, but the resulting HCN production rates changed by only 2%." (Radiative Transfer Modeling)
6. **Account for interferometric filtering**: Process three-dimensional synthetic coma images through simobserve; clean and image synthetic visibilities with the science-image parameters.  
  > "Flux losses due to the filtering of large-scale coma structures by the interferometer were simulated by processing the (three-dimensional) synthetic coma images using the CASA `simobserve` task" (Radiative Transfer Modeling); "The resulting synthetic visibilities were cleaned and imaged with the same parameters used for the observed cometary images." (Radiative Transfer Modeling)
   - software: CASA, simobserve
   - parameter: Same hour angle, observation duration and array configuration as the science observations.  
  > "with the same hour angle, observation duration and array configuration parameters used for our science observations." (Radiative Transfer Modeling)
   - fitting: _not stated_
   - validation: _not stated_
7. **Fit molecular production and outflow**: Fit extracted spectra with nonlinear least squares; start with isotropic uniform expansion, refit HCN at the CO velocity, and test a conical HCN jet.  
  > "The observed spectra were modeled with a nonlinear least-squares fitting procedure" (Radiative Transfer Modeling); "The molecules of interest (X) were initially modeled assuming an isotropic, uniformly expanding coma, with outflow velocity ($v_{out}$) and production rate $Q({\rm X})$ allowed to vary as free parameters." (Radiative Transfer Modeling); "An excellent fit to the HCN spectrum was also obtained using a conical jet model (see Figure 1)" (Radiative Transfer Modeling)
   - software: LIME
   - parameter: Refit HCN with v_out fixed at 0.47 km s^-1.  
  > "so this fit was re-done, fixing the outflow velocity at the best-fitting value for CO ($v_{out}=0.47$ km s$^{-1}$" (Radiative Transfer Modeling)
   - parameter: Jet axis perpendicular to the line of sight; all outgassing in a cone; v_out = 0.47 km s^-1.  
  > "with $v_{out}=0.47$ km s$^{-1}$, and assuming all outgassing was confined to a conical region emanating from the nucleus, with its axis perpendicular to the line of sight" (Radiative Transfer Modeling)
   - assumption: CO and HCN well mixed; constant kinetic temperature 50 K.  
  > "assuming CO and HCN were well mixed, with a constant kinetic temperature of $T_{kin}=50$ K." (Unusually High CO Abundance of the First Active Interstellar Comet)
   - assumption: HCN optically thin; its derived production rate scales linearly with assumed outflow velocity.  
  > "The HCN emission is optically thin, so the derived production rate scales linearly with the assumed outflow velocity." (Radiative Transfer Modeling)
   - fitting: Nonlinear least squares; initially free v_out and Q(X); assess reduced chi-squared.  
  > "The observed spectra were modeled with a nonlinear least-squares fitting procedure" (Radiative Transfer Modeling); "with outflow velocity ($v_{out}$) and production rate $Q({\rm X})$ allowed to vary as free parameters." (Radiative Transfer Modeling); "The quality of the fits was monitored using the reduced chi-squared statistic ($\chi_r^2$)" (Radiative Transfer Modeling)
   - validation: CO interferometric χr² = 1.03; HCN χr² changes 1.07 to 1.13 when velocity is fixed; autocorrelation CO production agrees within errors.  
  > "resulting in $\chi_r^2=1.03$ for our best fit to the CO interferometric data (Figure 2)." (Radiative Transfer Modeling); "This led to only a minor degradation of the HCN $\chi_r^2$ value, from 1.07 to 1.13" (Radiative Transfer Modeling); "This is consistent with the value obtained from the interferometric data (within errors), adding confidence to our CO measurements." (Unusually High CO Abundance of the First Active Interstellar Comet)
8. **Test excitation uncertainties**: Vary kinetic temperature and electron density scaling; assess changes in molecular production and CO/HCN.  
  > "Modeling was carried out for a range of coma kinetic temperatures $T_{kin}=20$–70 K" (Radiative Transfer Modeling); "However, in the case of $x_{n_e}=0.2$, the HCN production rate is more sensitive to the value of $T_{kin}$" (Radiative Transfer Modeling)
   - software: LIME
   - parameter: T_kin = 20–70 K; nominal x_ne = 1.0; low-electron case x_ne = 0.2.  
  > "For $x_{n_e}=1.0$, the CO and HCN production rates are relatively insensitive to the assumed kinetic temperature, changing by less than 8% across the range $T_{kin}=$ 20–70 K." (Radiative Transfer Modeling); "However, in the case of $x_{n_e}=0.2$, the HCN production rate is more sensitive to the value of $T_{kin}$" (Radiative Transfer Modeling)
   - assumption: Temperature range based on prior radio and infrared comet observations at 1.7-2.4 au.  
  > "based on the temperatures previously observed at radio and infrared wavelengths for comets in the distance range 1.7-2.4 au (Supplementary Table 1)." (Radiative Transfer Modeling)
   - fitting: _not stated_
   - validation: At nominal electron scaling, production rates change by less than 8%; even the low-temperature, low-electron case remains CO-rich.  
  > "For $x_{n_e}=1.0$, the CO and HCN production rates are relatively insensitive to the assumed kinetic temperature, changing by less than 8% across the range $T_{kin}=$ 20–70 K." (Radiative Transfer Modeling); "2I/Borisov’s CO/HCN ratio could plausibly be as low as $370\pm80$, but this is still higher than the range of values (1.25–238) observed in previous Solar System comets" (Radiative Transfer Modeling)
9. **Test hemispheric CO outgassing**: Fit the CO autocorrelation spectrum with sunward and anti-sunward hemispheres and compare against isotropic outgassing.  
  > "Assuming hemispheric asymmetry along the Sun-comet vector" (Radiative Transfer Modeling); "Statistically, the 2-component, asymmetric model is therefore favoured." (Radiative Transfer Modeling)
   - software: LIME
   - parameter: Sunward and anti-sunward expansion velocities and production-rate asymmetry factor.  
  > "an expansion velocity of $v_{out}(1)=0.49$ km s$^{-1}$ in the sunward hemisphere, and $v_{out}(2)=0.26$ km s$^{-1}$ in the anti-sunward hemisphere, with an asymmetry factor (ratio of sunward to anti-sunward production rates) of 3.3." (Radiative Transfer Modeling)
   - assumption: Hemispheric asymmetry along the Sun-comet vector; CO J=3-2 optically thin; T_kin = 50 K.  
  > "Assuming hemispheric asymmetry along the Sun-comet vector" (Radiative Transfer Modeling); "Since the CO $J=3-2$ emission is optically thin" (Radiative Transfer Modeling); "($Q({\rm CO})=(5.0\pm0.5)\times10^{26}$ s$^{-1}$ at $T_{kin}=50$ K)." (Radiative Transfer Modeling)
   - fitting: Compare reduced chi-squared and probability P for isotropic and asymmetric models.  
  > "The isotropic model has a best-ftting $\chi^2_r=1.21$ (corresponding to $P = 0.02$" (Radiative Transfer Modeling); "whereas the asymmetric model has $\chi^2_r=1.01$ and $P = 0.45$." (Radiative Transfer Modeling)
   - validation: Asymmetric model favoured; production rate unchanged from the isotropic model because CO emission is optically thin.  
  > "Statistically, the 2-component, asymmetric model is therefore favoured." (Radiative Transfer Modeling); "Since the CO $J=3-2$ emission is optically thin, the production rate for our asymmetric model is the same as that obtained using the standard, isotropic model" (Radiative Transfer Modeling)
10. **Bound undetected molecular production**: Use integrated spectral noise to obtain three-sigma CS and CH3OH production limits and mixing-ratio limits.  
  > "Three-sigma upper limits were obtained for the CS and CH$_3$OH production rates from the integrated spectral noise within a cometocentric velocity range $-0.8$ to $+0.6$ km s$^{-1}$" (Radiative Transfer Modeling)
   - parameter: Velocity interval −0.8 to +0.6 km s^-1, based on detected CO autocorrelation flux.  
  > "within a cometocentric velocity range $-0.8$ to $+0.6$ km s$^{-1}$ (based on the velocity range of detected flux in the CO autocorrelation spectrum)." (Radiative Transfer Modeling)
   - assumption: Kinetic temperature 50 K for Table 1 production rates.  
  > "Derived production rates from the ALMA interferometric data, assuming a kinetic temperature of 50 K (see Methods)." (Table 1)
   - fitting: _not stated_
   - validation: Limits consistent with previously observed Solar System comet abundances.  
  > "These correspond to mixing ratios of $<0.1$% for CS and $<68$% for CH$_3$OH, which are consistent with the values previously observed in other Solar System comets" (Radiative Transfer Modeling)
11. **Measure optical CN production**: Derive median CN and Rc radial profiles, subtract dust using the continuum filter, convert flux to column density and fit a Haser profile.  
  > "To compute the CN production rate from the narrow-band images, we derived median radial brightness profiles for the CN and Rc images and used the continuum filter to remove the dust contamination." (Optical Observations of CN); "We then converted the flux to column density and fitted the profile with a Haser model at 10,000 km from the nucleus" (Optical Observations of CN)
   - parameter: Haser fit at 10,000 km from nucleus; outflow velocity 0.5 km s^-1.  
  > "fitted the profile with a Haser model at 10,000 km from the nucleus, using effective scale lengths from Cochran & Schleicher(cite: coc93) and an outflow velocity of 0.5 km s$^{-1}$." (Optical Observations of CN)
   - assumption: Effective scale lengths from Cochran & Schleicher.  
  > "using effective scale lengths from Cochran & Schleicher(cite: coc93)" (Optical Observations of CN)
   - fitting: Fit column-density profile with a Haser model.  
  > "We then converted the flux to column density and fitted the profile with a Haser model at 10,000 km from the nucleus" (Optical Observations of CN)
   - validation: December 15 CN production consistent within uncertainties with ALMA HCN production.  
  > "Observations of near-UV CN fluorescence using the TRAPPIST-South telescope on UT 2019-12-15 gave $Q({\rm CN})=(9.5\pm1.8)\times10^{23}$ s$^{-1}$, which is consistent (within uncertainties) with our derived HCN production rate." (Unusually High CO Abundance of the First Active Interstellar Comet)
12. **Compare volatile abundances and infer origin**: Calculate HCN/H2O, CO/H2O and CO/HCN; include excitation uncertainties; compare with Solar System comets and discuss formation environments.  
  > "we find that the HCN abundance (relative to H$_2$O) was 0.06%-0.16% and the CO abundance was 35%-105%." (Unusually High CO Abundance of the First Active Interstellar Comet); "Accounting for additional uncertainties in the HCN production rate due to possible variations in the coma kinetic temperature and electron abundance (see Methods), we find that the maximum error margin for CO/HCN is $630^{+200}_{-340}$." (Unusually High CO Abundance of the First Active Interstellar Comet); "comparison with other comets observed at similar heliocentric distances reveals an unusual, CO-rich composition for this interstellar object" (Unusually High CO Abundance of the First Active Interstellar Comet)
   - parameter: Use water production range 4.9-10.7×10^26 s^-1 for relative-to-water abundances.  
  > "Assuming 2I/Borisov’s water production rate on December 15th-16th was within the range 4.9-10.7$\times10^{26}$ s$^{-1}$ observed by Xing et al.(cite: bod20) (see Methods)" (Unusually High CO Abundance of the First Active Interstellar Comet)
   - assumption: Measured CO/HCN at 2.0 au likely represents the interior ice mixing ratio.  
  > "Our measured CO/HCN ratio in 2I/Borisov at 2.0 au is therefore likely to be representative of the interior ice mixing ratio." (Unusually High CO Abundance of the First Active Interstellar Comet)
   - fitting: _not stated_
   - validation: Compare against comets at similar heliocentric distances; consider differential sublimation and insulating surface layers.  
  > "Supplementary Table 1 provides literature data for CO and HCN in five comets observed at $r_H=1.7$–$2.4$ au, including several CO-rich comets." (Unusually High CO Abundance of the First Active Interstellar Comet); "whether the differential sublimation rates as a function of temperature for CO, HCN and H$_2$O could play a role." (Unusually High CO Abundance of the First Active Interstellar Comet); "There remains a possibility that 2I/Borisov’s enhanced CO/H$_2$O ratio arises as a consequence of thermally-insulating exterior layers" (Unusually High CO Abundance of the First Active Interstellar Comet)

## Software

- **CASA** 5.6: Flagging and calibration with JAO pipeline scripts; synthetic-observation processing.  
  > "Data were flagged and calibrated with CASA version 5.6(cite: jae08) using the automated pipeline scripts supplied by the Joint ALMA Observatory." (Observations); "processing the (three-dimensional) synthetic coma images using the CASA `simobserve` task" (Radiative Transfer Modeling)
- **tclean** : Clark deconvolution, Doppler correction and imaging.  
  > "Deconvolution, Doppler correction and imaging were performed using the `tclean` (Clark) algorithm" (Observations)
- **simobserve** : Simulate interferometric filtering of synthetic coma images.  
  > "Flux losses due to the filtering of large-scale coma structures by the interferometer were simulated by processing the (three-dimensional) synthetic coma images using the CASA `simobserve` task" (Radiative Transfer Modeling)
- **LIne Modeling Engine (LIME)** : Modified cometary three-dimensional radiative transfer and nonlinear least-squares spectral modeling.  
  > "The observed spectra were modeled with a nonlinear least-squares fitting procedure, using a modified version of the LIne Modeling Engine (LIME)(cite: bri10), adapted for cometary comae as described by Cordiner et al.(cite: cor19)." (Radiative Transfer Modeling)
- **Leiden Atomic and Molecular Database** : Source of H2 collisional rates used for HCN collisions with H2O and CO.  
  > "Collisional rates for HCN with H$_2$O and CO were taken from the H$_2$ collisional rates in the Leiden Atomic and Molecular Database (cite: sch05)." (Radiative Transfer Modeling)
- **JPL ephemeris** : Real-time comet tracking using solution #48, generated 2019-12-05.  
  > "The array phase-center was updated in real-time to track 2I/Borisov’s position on the sky, following JPL ephemeris solution #48 (generated on 2019-12-05)." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO integrated flux per beam | 8.6 | ±1.5 | mJy km s^-1 bm^-1 | 2 | / CO / $J=3-2$ / 345.796 / $8.6\pm1.5$ / $(4.4\pm0.7)\times10^{26}$ / |
| HCN integrated flux per beam | 6.5 | ±1.2 | mJy km s^-1 bm^-1 | 2 | / HCN / $J=4-3$ / 354.505 / $6.5\pm1.2$ / $(7.0\pm1.1)\times10^{23}$ / |
| HCN detection significance | 5.2 | not stated | σ | 2 | correspond to a statistical significance of $5.2\sigma$ for HCN and $5.9\sigma$ for CO. |
| CO detection significance | 5.9 | not stated | σ | 2 | correspond to a statistical significance of $5.2\sigma$ for HCN and $5.9\sigma$ for CO. |
| Detected CO extended component distance from nucleus | up to 4000 | not stated | km | 2 | an extended flux component is detectable for CO, at distances up to 4000 km from the nucleus. |
| Dust/nucleus continuum emission upper limit | <0.11 | 3σ upper limit | mJy beam^-1 | 2 | a $3\sigma$ upper limit to the dust/nucleus thermal emission of 0.11 mJy beam$^{-1}$. |
| Interpolated H2O production at the ALMA epoch | 6.5×10^26 | ±1.0×10^26 | s^-1 | 4 | results in $Q({\rm H_2O})=(6.5\pm1.0)\times10^{26}$ s$^{-1}$ at the epoch of our ALMA observations. |
| CO production rate from interferometric data | 4.4×10^26 | ±0.7×10^26 | mol. s^-1 | 7 | / CO / $J=3-2$ / 345.796 / $8.6\pm1.5$ / $(4.4\pm0.7)\times10^{26}$ / |
| HCN production rate from interferometric data | 7.0×10^23 | ±1.1×10^23 | mol. s^-1 | 7 | / HCN / $J=4-3$ / 354.505 / $6.5\pm1.2$ / $(7.0\pm1.1)\times10^{23}$ / |
| CO production rate from autocorrelation data | 5.0×10^26 | ±0.5×10^26 | s^-1 | 7 | Modeling the autocorrelation data assuming isotropic outgassing from the nucleus results in a CO production rate of $(5.0\pm0.5)\times10^{26}$ s$^{-1}$ (assuming an amplitude calibration error of $\pm10$%). |
| CO spectral FWHM | 1.1 | ±0.1 | km s^-1 | 7 | For CO, the spectral line profile (with FWHM = $1.1\pm0.1$ km s$^{-1}$) |
| HCN spectral FWHM | 0.57 | ±0.09 | km s^-1 | 7 | HCN exhibits a narrower spectral line shape (with FWHM = $0.57\pm0.09$ km s$^{-1}$) |
| CO isotropic outflow velocity from interferometric data | 0.47 | ±0.04 | km s^-1 | 7 | with best-fitting outflow velocity $v_{out}=0.47\pm0.04$ km s$^{-1}$. |
| CO isotropic outflow velocity from autocorrelation data | 0.45 | ±0.03 | km s^-1 | 7 | the CO autocorrelation data also gave $v_{out}=0.45\pm0.03$ km s$^{-1}$ |
| HCN initial free-fit outflow velocity | 0.23 | ±0.06 | km s^-1 | 7 | The best fit for HCN resulted in a surprisingly small value of $v_{out}=0.23\pm0.06$ km s$^{-1}$ |
| HCN conical jet opening angle | 96 | not stated | degrees | 7 | a best-fitting cone opening angle of $96^{\circ}$. |
| HCN production increase for the conical jet model | 13 | not stated | % | 7 | This resulted in a $13$% increase in the derived HCN production rate, which is within the range of our observational uncertainties. |
| HCN production at T_kin = 20 K and x_ne = 0.2 | 1.2×10^24 | not stated | s^-1 | 8 | resulting in a value of $Q({\rm HCN})=1.2\times10^{24}$ s$^{-1}$ at 20 K; However, in the case of $x_{n_e}=0.2$, the HCN production rate is more sensitive to the value of $T_{kin}$ |
| CO production at T_kin = 20 K | 4.6×10^26 | not stated | s^-1 | 8 | For comparison, we found $Q({\rm CO})=4.6\times10^{26}$ s$^{-1}$ at $T_{kin}=20$ K. |
| CO/HCN in the low-temperature, low-electron-collision regime | 370 | ±80 | dimensionless | 8 | Consequently, in the regime of very low kinetic temperature and electron collision rates, 2I/Borisov’s CO/HCN ratio could plausibly be as low as $370\pm80$ |
| Sunward CO expansion velocity | 0.49 | not stated | km s^-1 | 9 | an expansion velocity of $v_{out}(1)=0.49$ km s$^{-1}$ in the sunward hemisphere |
| Anti-sunward CO expansion velocity | 0.26 | not stated | km s^-1 | 9 | $v_{out}(2)=0.26$ km s$^{-1}$ in the anti-sunward hemisphere |
| Sunward/anti-sunward CO production-rate asymmetry | 3.3 | not stated | dimensionless | 9 | an asymmetry factor (ratio of sunward to anti-sunward production rates) of 3.3. |
| Isotropic CO autocorrelation model reduced chi-squared | 1.21 | not stated | dimensionless | 9 | The isotropic model has a best-ftting $\chi^2_r=1.21$ |
| Isotropic CO autocorrelation model P | 0.02 | not stated | dimensionless | 9 | The isotropic model has a best-ftting $\chi^2_r=1.21$ (corresponding to $P = 0.02$ |
| Asymmetric CO autocorrelation model reduced chi-squared | 1.01 | not stated | dimensionless | 9 | whereas the asymmetric model has $\chi^2_r=1.01$ and $P = 0.45$. |
| Asymmetric CO autocorrelation model P | 0.45 | not stated | dimensionless | 9 | whereas the asymmetric model has $\chi^2_r=1.01$ and $P = 0.45$. |
| CS integrated flux upper limit | <5.2 | not stated | mJy km s^-1 bm^-1 | 10 | / CS / $J=7-6$ / 342.883 / $<5.2$ / $<6.5\times10^{23}$ / |
| CH3OH integrated flux upper limit | <4.4 | not stated | mJy km s^-1 bm^-1 | 10 | / CH$_3$OH / $J_K=13_0 - 12_1 A^+$ / 355.603 / $<4.4$ / $<4.4\times10^{26}$ / |
| CS production-rate upper limit | <6.5×10^23 | 3σ upper limit | mol. s^-1 | 10 | / CS / $J=7-6$ / 342.883 / $<5.2$ / $<6.5\times10^{23}$ /; Three-sigma upper limits were obtained for the CS and CH$_3$OH production rates |
| CH3OH production-rate upper limit | <4.4×10^26 | 3σ upper limit | mol. s^-1 | 10 | / CH$_3$OH / $J_K=13_0 - 12_1 A^+$ / 355.603 / $<4.4$ / $<4.4\times10^{26}$ /; Three-sigma upper limits were obtained for the CS and CH$_3$OH production rates |
| CS mixing-ratio upper limit | <0.1 | 3σ upper limit | % | 10 | These correspond to mixing ratios of $<0.1$% for CS and $<68$% for CH$_3$OH; Three-sigma upper limits were obtained for the CS and CH$_3$OH production rates |
| CH3OH mixing-ratio upper limit | <68 | 3σ upper limit | % | 10 | These correspond to mixing ratios of $<0.1$% for CS and $<68$% for CH$_3$OH; Three-sigma upper limits were obtained for the CS and CH$_3$OH production rates |
| CN production rate on December 15 | 9.5×10^23 | ±1.8×10^23 | s^-1 | 11 | The CN production rates obtained on December 15, 18 and 19, were respectively $(9.5\pm1.8)\times10^{23}$ s$^{-1}$, $(11.6\pm1.9)\times10^{23}$ s$^{-1}$, and $(9.2\pm1.7)\times10^{23}$ s$^{-1}$. |
| CN production rate on December 18 | 11.6×10^23 | ±1.9×10^23 | s^-1 | 11 | The CN production rates obtained on December 15, 18 and 19, were respectively $(9.5\pm1.8)\times10^{23}$ s$^{-1}$, $(11.6\pm1.9)\times10^{23}$ s$^{-1}$, and $(9.2\pm1.7)\times10^{23}$ s$^{-1}$. |
| CN production rate on December 19 | 9.2×10^23 | ±1.7×10^23 | s^-1 | 11 | The CN production rates obtained on December 15, 18 and 19, were respectively $(9.5\pm1.8)\times10^{23}$ s$^{-1}$, $(11.6\pm1.9)\times10^{23}$ s$^{-1}$, and $(9.2\pm1.7)\times10^{23}$ s$^{-1}$. |
| HCN abundance relative to H2O | 0.06%-0.16% | not stated | % | 12 | we find that the HCN abundance (relative to H$_2$O) was 0.06%-0.16% and the CO abundance was 35%-105%. |
| CO abundance relative to H2O | 35%-105% | not stated | % | 12 | we find that the HCN abundance (relative to H$_2$O) was 0.06%-0.16% and the CO abundance was 35%-105%. |
| CO/HCN mixing ratio with maximum error margin | 630 | +200/-340 | dimensionless | 12 | we find that the maximum error margin for CO/HCN is $630^{+200}_{-340}$. |
| Inferred upper bound on interior temperature during interstellar travel | ≲25 | not stated | K | 12 | maintained a very low interior temperature ($\lesssim25$ K) for the duration of its interstellar journey. |

## Qualitative findings

- HCN and CO detected at the expected nucleus position.  
  > "Our observations reveal emission from hydrogen cyanide (HCN), and carbon monoxide (CO), coincident with the expected position of 2I/Borisov’s nucleus" (abstract)
- HCN abundance resembles typical Solar System comets; CO is unusually abundant.  
  > "While the HCN abundance relative to water (0.06–0.16%) appears similar to that of typical, previously observed comets in our Solar System, the abundance of CO (35–105%) is among the highest observed in any comet within 2 au of the Sun." (abstract)
- HCN absent from autocorrelation data, consistent with faster depopulation of HCN J=4 than CO J=3.  
  > "HCN was not detected in the autocorrelation data, which is consistent with a faster drop in HCN flux with radius, due to more rapid radiative cooling (depopulation) of the HCN $J=4$ level than for the $J=3$ level of CO." (Unusually High CO Abundance of the First Active Interstellar Comet)
- CO autocorrelation data favour enhanced outgassing on the illuminated hemisphere.  
  > "Our autocorrelation data are thus consistent with an enhanced CO sublimation rate on the illuminated side of the nucleus, which can be explained as a result of the increased Solar heating there." (Radiative Transfer Modeling)
- Probable origin in the icy outer regions of a distant protoplanetary disk.  
  > "showing that it probably originated from the icy, outer regions of a distant protoplanetary disk" (Unusually High CO Abundance of the First Active Interstellar Comet)

## Claim tuples

- H: Parent volatiles can reveal the composition of the active interstellar comet. | E: Observe HCN and CO rotational emission with ALMA and fit radiative transfer models. | R: Q(HCN) = (7.0±1.1)×10^23 s^-1; Q(CO) = (4.4±0.7)×10^26 s^-1. | F: Simple carbon-, nitrogen- and oxygen-bearing molecular ices were abundant in the natal environment. | **supported**
- H: 2I/Borisov has an unusual volatile composition compared with Solar System comets. | E: Derive abundance ratios, vary temperature and electron abundance, and compare with comets at similar heliocentric distances. | R: HCN/H2O = 0.06%-0.16%; CO/H2O = 35%-105%; CO/HCN = 630 with +200/-340 maximum error margin. | F: HCN is ordinary but 2I/Borisov is among the most CO-rich comets observed. | **supported**
- H: CO outgassing is asymmetric along the Sun-comet direction. | E: Compare isotropic and two-hemisphere fits to the CO autocorrelation spectrum. | R: Sunward/anti-sunward production ratio 3.3; asymmetric χr² = 1.01 and P = 0.45 versus isotropic χr² = 1.21 and P = 0.02. | F: The asymmetric model is statistically favoured, consistent with enhanced sunward sublimation. | **supported**
- H: CO-rich coma abundances indicate formation in a cold, CO-rich outer disk. | E: Interpret measured abundance ratios using comet comparisons and ice-line formation scenarios. | R: Unusually CO-rich coma; inferred interior temperature ≲25 K during interstellar travel. | F: A cold outer-disk origin is probable, but coma abundances may not equal bulk nucleus composition. | **partially**

## Reasoning

- Why this data: Microwave and sub-mm rotational emission probes parent volatiles stored as nucleus ices.  
  > "observations of rotational emission in the microwave and sub-mm part of the spectrum(cite: boc18) can reveal parent volatiles" (Unusually High CO Abundance of the First Active Interstellar Comet)
- Why this method: Simulate spatial filtering; use efficient LTE for CO; autocorrelations recover extended CO flux.  
  > "Flux losses due to the filtering of large-scale coma structures by the interferometer were simulated by processing the (three-dimensional) synthetic coma images using the CASA `simobserve` task" (Radiative Transfer Modeling); "LTE was found to be appropriate for modeling our observations of this molecule, with the benefit of improved computational efficiency." (Radiative Transfer Modeling); "because they include flux from angular scales $\gtrsim10''$, which was filtered out by the interferometer due to a lack of very short baselines in the telescope array." (Unusually High CO Abundance of the First Active Interstellar Comet)
- Alternative: HCN conical jet versus isotropic outgassing: both fit; jet production rate is 13% higher.  
  > "An excellent fit to the HCN spectrum was also obtained using a conical jet model" (Radiative Transfer Modeling); "This resulted in a $13$% increase in the derived HCN production rate, which is within the range of our observational uncertainties." (Radiative Transfer Modeling)
- Alternative: Low temperature and electron collision rates reduce the inferred CO/HCN ratio but preserve unusually high CO.  
  > "2I/Borisov’s CO/HCN ratio could plausibly be as low as $370\pm80$, but this is still higher than the range of values (1.25–238) observed in previous Solar System comets" (Radiative Transfer Modeling)
- Alternative: Differential sublimation may affect whether coma abundance ratios represent nucleus composition.  
  > "whether the differential sublimation rates as a function of temperature for CO, HCN and H$_2$O could play a role." (Unusually High CO Abundance of the First Active Interstellar Comet)
- Alternative: Thermally insulating exterior layers could suppress water without significantly suppressing CO.  
  > "thermally-insulating exterior layers, which could inhibit heat penetration, leading to a drop in the overall water production rate without significantly affecting that of the more volatile CO." (Unusually High CO Abundance of the First Active Interstellar Comet)
- Alternative: Fragmentation and ejection of a chemically differentiated parent body could generate CO-rich planetesimals.  
  > "through fragmentation (and subsequent ejection) of a chemically-differentiated parent body — as was considered previously for C/2016 R2 (PanSTARRS)(cite: biv18; mck19)." (Unusually High CO Abundance of the First Active Interstellar Comet)
- How they decided it was enough: Detection significance, reduced chi-squared, interferometric/autocorrelation agreement, and excitation sensitivity tests.  
  > "Spectrally integrated fluxes are given in Table 1, and correspond to a statistical significance of $5.2\sigma$ for HCN and $5.9\sigma$ for CO." (Unusually High CO Abundance of the First Active Interstellar Comet); "The quality of the fits was monitored using the reduced chi-squared statistic ($\chi_r^2$)" (Radiative Transfer Modeling); "This is consistent with the value obtained from the interferometric data (within errors), adding confidence to our CO measurements." (Unusually High CO Abundance of the First Active Interstellar Comet)
- Limitation (authors): Detailed coma morphology largely hidden by noise.  
  > "Our HCN and CO detections are robust, but the detailed coma morphology in Figure 1 is largely hidden by noise" (Unusually High CO Abundance of the First Active Interstellar Comet)
- Limitation (authors): HCN signal-to-noise cannot distinguish a jet from isotropic outgassing.  
  > "However, the signal-to-noise is too low to conclusively distinguish this scenario from isotropic outgassing." (Unusually High CO Abundance of the First Active Interstellar Comet)
- Limitation (authors): Interferometric observations filter emission on angular scales ≳10''.  
  > "because they include flux from angular scales $\gtrsim10''$, which was filtered out by the interferometer due to a lack of very short baselines in the telescope array." (Unusually High CO Abundance of the First Active Interstellar Comet)
- Limitation (authors): Observed coma abundances may not represent bulk nucleus volatiles.  
  > "While it is difficult to be sure that the observed coma abundances represent the bulk composition of volatiles in 2I/Borisov’s nucleus" (Unusually High CO Abundance of the First Active Interstellar Comet)
- Limitation (authors): Internal physical structure is poorly constrained; surface processing requires further investigation.  
  > "Given the (lack of) information on 2I/Borisov’s internal physical structure" (Unusually High CO Abundance of the First Active Interstellar Comet); "A more complete investigation of the importance of such effects is warranted." (Unusually High CO Abundance of the First Active Interstellar Comet)
- Caveat (inferred, ours): Detection significance supports integrated emission more strongly than detailed morphology.
- Caveat (inferred, ours): The two CO measurements share an observing session and are not fully independent calibration checks.
- Caveat (inferred, ours): Water-relative abundances depend on observations bracketing the ALMA epoch rather than simultaneous water measurements.
- Caveat (inferred, ours): The cold formation environment is an interpretation; surface insulation and differentiated-parent scenarios remain viable.
- Caveat (inferred, ours): The asymmetric-model comparison lacks enough optimizer and parameter-count detail for an independent model-selection audit.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Unambiguous archive identifier and a statement of data or calibrated-product availability.
- Missing: Modified cometary LIME source, executable model configurations, and fitting scripts.
- Missing: Detailed autocorrelation reduction inherited from Cordiner et al.(cite: cor19).
- Missing: Image grid, channel selections, continuum construction, and exact synthetic-observation setup.
- Missing: Autocorrelation baseline and telluric-interpolation selections.
- Missing: Supplementary Table 1, numerical molecular-rate inputs, and optical CN scale lengths.
- Missing: Parameter bounds, weighting, uncertainty propagation, and the electron density prescription.
- Data volume (inferred): Not estimable from the supplied text: correlator bandwidths, channel counts and integration sampling are missing.
- Score (inferred): 6/5, On a 0–10 scale: substantial observing, imaging, modeling and validation detail, but custom code, inherited procedures, several exact settings and public availability are missing.
- Rediscovery candidate: no, Main results are numeric, but the text does not establish public data availability and the custom radiative-transfer and autocorrelation recipe is incomplete.

## Links

- Method: Cordiner et al.(cite: cor19) (Inherited autocorrelation calibration/combination and cometary LIME adaptations.)
- Method: (cite: bri10) (LIME radiative-transfer engine.)
- Method: (cite: jae08) (CASA calibration and imaging software.)
- Method: (cite: sch05) (Leiden molecular collisional-rate database.)
- Method: (cite: hue15) (Rates used for radiative pumping and photodissociation.)
- Method: (cite: alm19) (ALMA aperture efficiency used for autocorrelation beam-efficiency correction.)
- Method: (cite: dow89) (Relationship between aperture and main-beam efficiencies.)
- Method: Cochran & Schleicher(cite: coc93) (CN effective scale lengths for Haser modeling.)
- Method: (cite: opi16; mou18) (Optical reduction and flux-calibration procedures.)
- Method: (cite: far00) (CN narrow-band filter reference.)

## Checks

```json
{
 "quotes": 233,
 "quotes_ok": 233,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2019.1.01008.T"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 40,
 "numeric_problems": 0,
 "fill": {
  "facts": 158,
  "stated": 127,
  "rate": 0.804
 },
 "evidence_ok": true
}
```
