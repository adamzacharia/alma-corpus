# Exploring the Complex Ionization Environment of the Turbulent DM Tau Disk

`2024ApJ...972...88L` | The Astrophysical Journal 2024 | first author: Long, Deryl E. | arXiv: 2406.18657 | DOI: 10.3847/1538-4357/ad5c67

Card schema 1.0 | model gpt-6.1-sol | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Constrain DM Tau’s radially resolved ionization structure and the roles of CRs and X-rays.  
  > "In this work we constrain the radially resolved ionization structure of the DM Tau protoplanetary disk using HCO$^+$, H$^{13}$CO$^+$, and N$_2$H$^+$." (Introduction)
- Target **DM Tau**: coordinates _not stated_; z/distance 144.5 pc  
  > "All of the models assume a distance of 144.5 pc (cite: lindegren_2018) and an inclination of 35.2$^{\circ}$ (cite: Kudo_2018)." (Synthetic Observation Comparison); distance from (cite: lindegren_2018)  
  > "All of the models assume a distance of 144.5 pc (cite: lindegren_2018) and an inclination of 35.2$^{\circ}$ (cite: Kudo_2018)." (Synthetic Observation Comparison)

## Data provenance

- ALMA projects: 2019.1.00379.S, 2015.1.00678.S
- bands: Band 7: HCO+ J = 4 - 3, N2H+ J = 4 - 3; Band 6: H13CO+ J = 3 - 2  
  > "The Band 7 HCO$^+$ $J = 4 - 3$ and N$_2$H$^+$ $J = 4 - 3$ data were taken on 2019 October 17-18 with 43 antennas covering 15m-740m baselines." (ALMA Observations); "The Band 6 H$^{13}$CO$^+$ $J = 3 - 2$ data were taken on 2021 July 7 with 43 antennas covering 14m-2492m baselines." (ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 1875 MHz at 1 mm and 1.3 mm  
  > "| Continuum | 1 mm | 0$.\!\!^{\prime\prime}$25 $\times$ 0$.\!\!^{\prime\prime}$16 (53$^{\circ}$) | 1875 MHz$^{b}$ | 0.15 | 0.08 $\pm$ 0.008 Jy |" (Introduction); "| Continuum | 1.3 mm | 0$.\!\!^{\prime\prime}$38 $\times$ 0$.\!\!^{\prime\prime}$28 (-17$^{\circ}$) | 1875 MHz | 0.27 | 0.16 $\pm$ 0.016 Jy |" (Introduction)
- arrays: _not stated_
- configurations: _not stated_
- baselines: Band 7: 15m-740m, 43 antennas; Band 6 H13CO+: 14m-2492m, 43 antennas  
  > "The Band 7 HCO$^+$ $J = 4 - 3$ and N$_2$H$^+$ $J = 4 - 3$ data were taken on 2019 October 17-18 with 43 antennas covering 15m-740m baselines." (ALMA Observations); "The Band 6 H$^{13}$CO$^+$ $J = 3 - 2$ data were taken on 2021 July 7 with 43 antennas covering 14m-2492m baselines." (ALMA Observations)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Band 7: 2019 October 17-18; Band 6 H13CO+: 2021 July 7  
  > "The Band 7 HCO$^+$ $J = 4 - 3$ and N$_2$H$^+$ $J = 4 - 3$ data were taken on 2019 October 17-18 with 43 antennas covering 15m-740m baselines." (ALMA Observations); "The Band 6 H$^{13}$CO$^+$ $J = 3 - 2$ data were taken on 2021 July 7 with 43 antennas covering 14m-2492m baselines." (ALMA Observations)
- pi or archival as stated: 2019.1.00379.S (PI: Cleeves); archival N2H+ J = 3 - 2 from 2015.1.00678.S (PI: Qi)  
  > "Observations of HCO$^+$ $J = 4 - 3$, N$_2$H$^+$ $J = 4 - 3$, and H$^{13}$CO$^+$ $J = 3 - 2$ were taken with ALMA under project code 2019.1.00379.S (PI: Cleeves)." (ALMA Observations); "We also made use of data from project 2015.1.00678.S (PI: Qi) to constrain N$_2$H$^+$ $J = 3 - 2$." (ALMA Observations); "Using these observations along with archival observations of N$_2$H$^+$ $J = 3 - 2$, we aim to forward model DM Tau’s ionization environment." (Conclusions)
- Line: N2H+ J = 4 - 3 (372.672 GHz)
- Line: HCO+ J = 4 - 3 (356.734 GHz)
- Line: N2H+ J = 3 - 2 (279.512 GHz)
- Line: H13CO+ J = 3 - 2 (260.255 GHz)
- Other facility **University of Virginia’s Rivanna High Performance Computing Cluster**: Computing for the modeling  
  > "The modeling conducted in this paper was carried out on the University of Virginia’s Rivanna High Performance Computing Cluster." (Acknowledgments)
- External data: Gas density and temperature structure constrained by CO observations  
  > "Our physical model combines a well-constrained gas density and temperature structure from (cite: flaherty) with a dust structure based on continuum visibilities and spectral energy distribution (SED) fitting presented in (cite: Andrews_2011)." (Physical Model) [from (cite: flaherty)]
- External data: Dust structure from continuum visibilities and SED fitting; Rc = 135 au  
  > "Our physical model combines a well-constrained gas density and temperature structure from (cite: flaherty) with a dust structure based on continuum visibilities and spectral energy distribution (SED) fitting presented in (cite: Andrews_2011)." (Physical Model); "where the characteristic scaling radius $R_c$ = 135 au was determined by (cite: Andrews_2011) and the surface density gradient is set to $\gamma$ = 1." (Physical Model) [from (cite: Andrews_2011)]
- External data: 0.54 solar-mass star; estimated lifetime ~3–7 Myr  
  > "DM Tau is a large (cite: dartois_2003), well studied disk around a 0.54 M$_{\odot}$ T Tauri star (cite: Simon_2000)." (Introduction); "DM Tau’s estimated lifetime of $\sim$ 3–7 Myr (cite: Simon_2000)" (Ionization Model) [from (cite: Simon_2000)]
- External data: Observed stellar UV spectrum for TW Hya, scaled by 2.16  
  > "We use an observed stellar UV spectrum for TW Hya and scale it to DM Tau’s FUV luminosity by a factor of 2.16." (Ionization Model) [from not stated]
- External data: Quiescent and flaring template X-ray spectra  
  > "We explore the effects of both quiescent and “flaring" X-ray states using template spectra from (cite: cleeves15_twhya)." (Ionization Model) [from (cite: cleeves15_twhya)]
- External data: X-ray luminosity upper limit: 4.6 × 10^29 erg s^-1 after excluding energies <1 keV  
  > "the upper limit of 4.6 $\times$ 10$^{29}$ erg s$^{-1}$ from (cite: damiani_1995) after excluding energies $<$ 1 keV." (Ionization Model) [from (cite: damiani_1995)]
- External data: M02 local interstellar cosmic-ray spectrum  
  > "The (cite: mosk_2002) spectrum is the best-fit model based on the diffuse $\gamma$-ray background as well as other data including the proton, antiproton, and alpha particle spectra." (Ionization Model) [from (cite: mosk_2002)]
- External data: W98 dense-ISM cosmic-ray conditions based on Voyager and Pioneer  
  > "The rate from (cite: webber_1998) approximates the conditions of the dense ISM based on measurements taken by *Voyager* and *Pioneer*." (Ionization Model) [from (cite: webber_1998)]
- External data: T Tauri Maximum-Modulation cosmic-ray model  
  > "Our lowest CR rate is the T Tauri Maximum-Modulation (TTX), which was extrapolated by (cite: cleeves13a) to account for enhanced CR modulation by the higher stellar wind outflow rates measured for T Tauri stars." (Ionization Model) [from (cite: cleeves13a)]
- External data: Constant 12C/13C ratio of 60  
  > "we retrieve H$^{13}$CO$^+$ abundances by applying a constant $^{12}$C/$^{13}$C ratio of 60 (cite: langer_penzias_1993)" (Chemical Model) [from (cite: langer_penzias_1993)]
- External data: DM Tau radial CO depletion range of a factor 1-10  
  > "However, it has been shown that DM Tau’s CO depletion ranges from a factor of 1-10 radially across the disk (cite: Zhang_2019)." (Chemical Model) [from (cite: Zhang_2019)]
- External data: LAMDA collisional rates  
  > "We use collisional rates from the LAMDA database (cite: schoer_2005; daniel_2005; denis_2020)." (Synthetic Observation Comparison) [from (cite: schoer_2005; daniel_2005; denis_2020)]
- External data: Conservative turbulence estimate: 0.25cs  
  > "This degree of turbulence is slightly lower than the conservative turbulence estimate (0.25c$_{s}$) from (cite: flaherty)." (Synthetic Observation Comparison) [from (cite: flaherty)]
- External data: Distance: 144.5 pc  
  > "All of the models assume a distance of 144.5 pc (cite: lindegren_2018) and an inclination of 35.2$^{\circ}$ (cite: Kudo_2018)." (Synthetic Observation Comparison) [from (cite: lindegren_2018)]
- External data: Inclination: 35.2 degrees  
  > "All of the models assume a distance of 144.5 pc (cite: lindegren_2018) and an inclination of 35.2$^{\circ}$ (cite: Kudo_2018)." (Synthetic Observation Comparison) [from (cite: Kudo_2018)]
- External data: Dust disk smooth beyond the gap at 111 au  
  > "In terms of disk structure, the dust disk is smooth beyond the gap at 111 au (cite: hashimoto_2021)" (Outer Disk Fitting) [from (cite: hashimoto_2021)]
- External data: C18O integrated flux: 3.0 Jy km s^-1  
  > "the 3.0 Jy km s$^{-1}$ C$^{18}$O flux reported by (cite: Zhang_2019)." (N$_2$H$^+$ Radial Structure) [from (cite: Zhang_2019)]
- External data: VIRaM temperature model reproducing the N2H+ J = 3 - 2 radial profile  
  > "(cite: qi_2019) are able to reproduce the N$_2$H$^+$ $J = 3 - 2$ radial profile by including a Vertically Isothermal Region above the Midplane (VIRaM layer) in their temperature model." (N$_2$H$^+$ Radial Structure) [from (cite: qi_2019)]
- External data: Stellar energetic-particle models: enhanced inner-disk ion columns and ionization  
  > "Modeling by (cite: rab_2017) suggests that while SPs cannot penetrate the disk midplane, they can dominate ionization in the warm molecular layer for regions close to the star." (The Ionization Environment of DM Tau) [from (cite: rab_2017)]
- Simulation/model as data: Ten chemical models: five CR ionization rates × two X-ray fields  
  > "With five different CR ionization rates and two XR fields we have a total of ten models." (Chemical Model)
- Simulation/model as data: Table 2 initial abundances relative to total Hydrogen density  
  > "Model Initial Abundances relative to total Hydrogen density." (Table 2); "Our initial abundances (Table [2](#tab:abunds)) are representative of the chemical conditions in a typical molecular cloud." (Chemical Model)
- Simulation/model as data: Non-LTE LIME model cubes with standard and high turbulence  
  > "For our “standard turbulence" models we use b = 0.2c$_{s}$." (Synthetic Observation Comparison); "We also run `LIME` models with high turbulent velocities (b = 0.5c$_{s}$) for comparison." (Synthetic Observation Comparison)
- Simulation/model as data: Additional CO-depletion comparisons: no depletion, factor 5, factor 10  
  > "We compared the radial profile results from our “average" (factor of 5) depletion model to those from models with no CO depletion and a factor of 10 CO depletion." (N$_2$H$^+$ Radial Structure)

## Processing

### Calibration

- pipeline or manual: CASA Pipeline; H13CO+ standard pipeline only  
  > "These data were calibrated with the CASA Pipeline, with J0423-0120 as the band-pass calibrator and J0510+1800 as the phase calibrator." (ALMA Observations); "For the H$^{13}$CO$^+$ data set we saw no improvement in the continuum RMS with phase self-calibration, so the data were calibrated only with the standard pipeline and subsequently imaged." (ALMA Observations)
- casa version: v5.6.1 for observed-data continuum subtraction and imaging; calibration version not stated  
  > "We performed continuum subtraction and imaging for all lines using the `uvcontsub` and `tclean` commands from CASA `v5.6.1` and Keplerian masks generated with the `keplerianmask`[^1] Python package (cite: teague_2020_kep)." (ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10%  
  > "Errors were estimated by applying the mask to line-free channels and include the nominal 10$\%$ flux calibration uncertainty from ALMA." (Introduction)
- self calibration: HCO+ / N2H+ J = 4 - 3: one phase round, 1.1x continuum RMS improvement; H13CO+: no adopted phase self-calibration  
  > "For the H$^{13}$CO$^+$ data set we saw no improvement in the continuum RMS with phase self-calibration, so the data were calibrated only with the standard pipeline and subsequently imaged." (ALMA Observations); "we applied one round of phase self-calibration which resulted in a small factor of 1.1x improvement in the RMS of the continuum data." (ALMA Observations)

### Imaging

- task: CASA tclean; observed data v5.6.1, model measurement sets v.5.6.0  
  > "We performed continuum subtraction and imaging for all lines using the `uvcontsub` and `tclean` commands from CASA `v5.6.1` and Keplerian masks generated with the `keplerianmask`[^1] Python package (cite: teague_2020_kep)." (ALMA Observations); "We perform continuum subtraction and image the model measurement sets in CASA `v.5.6.0` with the same parameters described in Section 2." (Synthetic Observation Comparison)
- deconvolver: _not stated_
- weighting robust: HCO+: Briggs, robust = 0.5; H13CO+ and both N2H+ lines: natural  
  > "For the line imaging of HCO$^+$ we used Briggs weighting and a robust parameter of 0.5." (ALMA Observations); "For H$^{13}$CO$^+$ and N$_2$H$^+$ $J = 4 - 3$ we used natural weighting and a `uvtaper` of 0$.\!\!^{\prime\prime}$5 to maximize sensitivity." (ALMA Observations); "Following (cite: qi_2019) we imaged N$_2$H$^+$ $J = 3 - 2$ using natural weighting." (ALMA Observations)
- uv taper: 0.5 arcsec for H13CO+ and N2H+ J = 4 - 3  
  > "For H$^{13}$CO$^+$ and N$_2$H$^+$ $J = 4 - 3$ we used natural weighting and a `uvtaper` of 0$.\!\!^{\prime\prime}$5 to maximize sensitivity." (ALMA Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian masks from keplerianmask; three components for each N2H+ line  
  > "We performed continuum subtraction and imaging for all lines using the `uvcontsub` and `tclean` commands from CASA `v5.6.1` and Keplerian masks generated with the `keplerianmask`[^1] Python package (cite: teague_2020_kep)." (ALMA Observations); "The masks for both N$_2$H$^+$ lines contain three components to capture the hyperfine emission structures." (ALMA Observations)
- multiscale scales: _not stated_
- continuum subtraction: CASA uvcontsub  
  > "We performed continuum subtraction and imaging for all lines using the `uvcontsub` and `tclean` commands from CASA `v5.6.1` and Keplerian masks generated with the `keplerianmask`[^1] Python package (cite: teague_2020_kep)." (ALMA Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Synthetic spectra over-sampled and channel averaged by a factor of 20  
  > "The `LIME` models for HCO$^+$, H$^{13}$CO$^+$, and N$_2$H$^+$ are spectrally over-sampled and channel averaged by a factor of 20 to mimic channel smearing seen in real observations." (Synthetic Observation Comparison)
- final beam: N2H+ 4-3: 0.66 × 0.64 arcsec (7.0°); HCO+ 4-3: 0.42 × 0.32 arcsec (-6.2°); N2H+ 3-2: 0.29 × 0.27 arcsec (0.99°); H13CO+ 3-2: 0.67 × 0.55 arcsec (46°)  
  > "0$.\!\!^{\prime\prime}$66 $\times$ 0$.\!\!^{\prime\prime}$64 (7.0$^{\circ}$) | 0.114 | 46 | 0.7 $\pm$ 0.24 |
| HCO$^+$ $J = 4 - 3$ | 356.734 | 0$.\!\!^{\prime\prime}$42 $\times$ 0$.\!\!^{\prime\prime}$32 (-6.2$^{\circ}$)" (Introduction); "| N$_2$H$^+$ $J = 3 - 2$ | 279.512 | 0$.\!\!^{\prime\prime}$29 $\times$ 0$.\!\!^{\prime\prime}$27 (0.99$^{\circ}$) | 0.150 | 3.9 | 1.3 $\pm$ 0.14 |" (Introduction); "| H$^{13}$CO$^+$ $J = 3 - 2$ | 260.255 | 0$.\!\!^{\prime\prime}$67 $\times$ 0$.\!\!^{\prime\prime}$55 (46$^{\circ}$) | 0.163 | 3.2 | 0.41 $\pm$ 0.046 |" (Introduction)
- final rms: N2H+ 4-3: 46; HCO+ 4-3: 8.6; N2H+ 3-2: 3.9; H13CO+ 3-2: 3.2 mJy beam^-1, in line-free channels  
  > "46 | 0.7 $\pm$ 0.24 |
| HCO$^+$ $J = 4 - 3$ | 356.734 | 0$.\!\!^{\prime\prime}$42 $\times$ 0$.\!\!^{\prime\prime}$32 (-6.2$^{\circ}$) | 0.119 | 8.6" (Introduction); "3.9 | 1.3 $\pm$ 0.14 |
| H$^{13}$CO$^+$ $J = 3 - 2$ | 260.255 | 0$.\!\!^{\prime\prime}$67 $\times$ 0$.\!\!^{\prime\prime}$55 (46$^{\circ}$) | 0.163 | 3.2" (Introduction); "We report the RMS measured in line-free channels." (ALMA Observations)

### Inherited from earlier work

- Archival N2H+ J = 3 - 2 observations and calibration details  
  > "We also made use of data from project 2015.1.00678.S (PI: Qi) to constrain N$_2$H$^+$ $J = 3 - 2$." (ALMA Observations); "A detailed description of those observations and their calibration can be found in (cite: qi_2019)." (ALMA Observations) [from (cite: qi_2019)]
- Natural weighting for N2H+ J = 3 - 2  
  > "Following (cite: qi_2019) we imaged N$_2$H$^+$ $J = 3 - 2$ using natural weighting." (ALMA Observations) [from (cite: qi_2019)]
- CO-derived gas structure and temperature parametrization  
  > "A detailed description of the CO modeling and temperature parametrization can be found in (cite: flaherty)." (Physical Model) [from (cite: flaherty)]
- SED-based inner dust gap: depletion factor 4.8 inside 19 au  
  > "Following the SED fitting results in (cite: Andrews_2011), we account for the disk’s inner gap by depleting the dust by a factor $\delta_{cav}$ = 4.8 in the region $R < R_{cav}$ = 19 au." (Physical Model) [from (cite: Andrews_2011)]
- MRN size distribution for both grain populations  
  > "Both the small and large dust grain populations follow an MRN size distribution (cite: Mathis_77) within their respective size ranges." (Physical Model) [from (cite: Mathis_77)]
- Monte Carlo UV/X-ray radiative transfer and cross sections  
  > "Two-dimensional stellar X-ray and UV fluxes (Figure [3](#fig:structure_all)) were obtained using the (cite: bethell_bergin) Monte Carlo radiative transfer code and cross sections." (Ionization Model) [from (cite: bethell_bergin)]
- Quiescent and flaring X-ray templates  
  > "We explore the effects of both quiescent and “flaring" X-ray states using template spectra from (cite: cleeves15_twhya)." (Ionization Model) [from (cite: cleeves15_twhya)]
- CR attenuation versus column density and CR-rate prescriptions  
  > "Our modeling suite includes five different incident CR–ionization rates ($\zeta_{CR}$) listed in Table [1](#tab:cr) and CR attenuation as a function of column density, as described in (cite: cleeves13a)." (Ionization Model); "Additional details for the CR rates can be found in (cite: cleeves13a)." (Ionization Model) [from (cite: cleeves13a)]
- 2D time-dependent rate-equation chemical code and adaptations  
  > "Chemical abundances are calculated as a function of position and time using a 2D time–dependent rate equation chemical code from (cite: fogel_2011) adapted in (cite: cleeves_2014_water) and (cite: anderson_2021)." (Chemical Model) [from (cite: fogel_2011); (cite: cleeves_2014_water); (cite: anderson_2021)]
- Constant carbon-isotope conversion  
  > "we retrieve H$^{13}$CO$^+$ abundances by applying a constant $^{12}$C/$^{13}$C ratio of 60 (cite: langer_penzias_1993)" (Chemical Model) [from (cite: langer_penzias_1993)]

### Not stated but needed to reproduce (our reading)

- Spectral-window/channel selections and polynomial order for uvcontsub.
- Phase self-calibration solution interval, reference antenna, solution combination and gain-application settings.
- tclean cell size, image size, deconvolver, stopping threshold and iteration limits.
- Keplerian-mask stellar mass, systemic velocity, position angle, radial limits and mask broadening.
- Velocity-integration limits, radial-bin spacing and profile uncertainty calculation.
- Inherited gas-density normalization and complete gas-temperature parametrization.
- Exact updated 18,608-reaction network, reaction rates and chemical solver settings.
- UV spectrum file, X-ray template files and radiation-transfer numerical settings.
- LIME sampling, convergence settings and exact molecular data files.
- Reduced-chi-squared normalization, degrees of freedom and treatment of correlated radial bins.

## Analysis recipe

1. **Make continuum-subtracted line images**: uvcontsub and tclean with Keplerian masks; line-dependent weighting and taper  
  > "We performed continuum subtraction and imaging for all lines using the `uvcontsub` and `tclean` commands from CASA `v5.6.1` and Keplerian masks generated with the `keplerianmask`[^1] Python package (cite: teague_2020_kep)." (ALMA Observations)
   - software: CASA, uvcontsub, tclean, keplerianmask
   - parameter: HCO+: Briggs robust = 0.5  
  > "For the line imaging of HCO$^+$ we used Briggs weighting and a robust parameter of 0.5." (ALMA Observations)
   - parameter: H13CO+ and N2H+ J = 4 - 3: natural weighting, 0.5 arcsec taper  
  > "For H$^{13}$CO$^+$ and N$_2$H$^+$ $J = 4 - 3$ we used natural weighting and a `uvtaper` of 0$.\!\!^{\prime\prime}$5 to maximize sensitivity." (ALMA Observations)
   - parameter: N2H+ J = 3 - 2: natural weighting; both N2H+ masks have three hyperfine components  
  > "Following (cite: qi_2019) we imaged N$_2$H$^+$ $J = 3 - 2$ using natural weighting." (ALMA Observations); "The masks for both N$_2$H$^+$ lines contain three components to capture the hyperfine emission structures." (ALMA Observations)
   - fitting: _not stated_
   - validation: RMS measured in line-free channels  
  > "We report the RMS measured in line-free channels." (ALMA Observations)
2. **Measure line emission**: Masked integrated fluxes, zeroth moments and radial intensity profiles; matched filter for N2H+ J = 4 - 3  
  > "The disk integrated flux was measured within the same Keplerian masks used for imaging." (Introduction); "We create velocity integrated intensity (zeroth moment) maps (Figure [2](#fig:moments)) for the resolved detections using the `bettermoments`[^3] Python package (cite: teague_2018_bm)." (ALMA Observations); "We produce radial line intensity profiles using the `GoFish`[^4] Python package (cite: GoFish)" (ALMA Observations)
   - software: bettermoments, GoFish, VISIBLE, matchedfilter
   - parameter: HCO+ detection used as the N2H+ J = 4 - 3 matched-filter template  
  > "We used the `matchedfilter` command from the `VISIBLE`[^2] Python package (cite: Loomis_2018) with our HCO$^+$ detection as a filter." (ALMA Observations)
   - parameter: Channel widths: N2H+ 4-3 0.114; HCO+ 4-3 0.119; N2H+ 3-2 0.150; H13CO+ 3-2 0.163 km s^-1  
  > "0.114 | 46 | 0.7 $\pm$ 0.24 |
| HCO$^+$ $J = 4 - 3$ | 356.734 | 0$.\!\!^{\prime\prime}$42 $\times$ 0$.\!\!^{\prime\prime}$32 (-6.2$^{\circ}$) | 0.119" (Introduction); "| N$_2$H$^+$ $J = 3 - 2$ | 279.512 | 0$.\!\!^{\prime\prime}$29 $\times$ 0$.\!\!^{\prime\prime}$27 (0.99$^{\circ}$) | 0.150 | 3.9 | 1.3 $\pm$ 0.14 |" (Introduction); "| H$^{13}$CO$^+$ $J = 3 - 2$ | 260.255 | 0$.\!\!^{\prime\prime}$67 $\times$ 0$.\!\!^{\prime\prime}$55 (46$^{\circ}$) | 0.163 | 3.2 | 0.41 $\pm$ 0.046 |" (Introduction)
   - assumption: Nominal 10% ALMA flux calibration uncertainty included  
  > "Errors were estimated by applying the mask to line-free channels and include the nominal 10$\%$ flux calibration uncertainty from ALMA." (Introduction)
   - fitting: _not stated_
   - validation: Line-free masked flux errors; 6 sigma matched-filter response for unresolved N2H+ J = 4 - 3  
  > "Errors were estimated by applying the mask to line-free channels and include the nominal 10$\%$ flux calibration uncertainty from ALMA." (Introduction); "We saw a 6$\sigma$ response, indicating the presence of N$_2$H$^+$ $J = 4 - 3$." (ALMA Observations)
3. **Construct the disk physical structure**: Combine inherited CO-based gas structure with continuum/SED-based dust structure  
  > "Our physical model combines a well-constrained gas density and temperature structure from (cite: flaherty) with a dust structure based on continuum visibilities and spectral energy distribution (SED) fitting presented in (cite: Andrews_2011)." (Physical Model)
   - software: EMCEE
   - parameter: Rc = 135 au; gamma = 1  
  > "where the characteristic scaling radius $R_c$ = 135 au was determined by (cite: Andrews_2011) and the surface density gradient is set to $\gamma$ = 1." (Physical Model)
   - parameter: H100 = 9.75 au; psi = 1.2  
  > "where $H_{100}$ = 9.75 au and $\psi$ = 1.2." (Physical Model)
   - parameter: Dust depleted by factor 4.8 for R < 19 au  
  > "Following the SED fitting results in (cite: Andrews_2011), we account for the disk’s inner gap by depleting the dust by a factor $\delta_{cav}$ = 4.8 in the region $R < R_{cav}$ = 19 au." (Physical Model)
   - parameter: Small grains: 0.005 micrometre–1 micrometre; large grains: 0.005 micrometre–1 mm  
  > "we calculate dust densities for small (0.005 $\mu$m – 1 $\mu$m) and large (0.005 $\mu$m – 1 mm) grains" (Physical Model)
   - assumption: Global dust-to-gas ratio xi = 0.01  
  > "Our model assumes a global dust-to-gas ratio of $\xi$ = 0.01." (Physical Model)
   - assumption: Settling parameters f = 0.85 and chi = 0.2  
  > "where *f* and $\chi$ are settling parameters fixed at 0.85 and 0.2 respectively" (Physical Model)
   - assumption: MRN grain-size distributions  
  > "Both the small and large dust grain populations follow an MRN size distribution (cite: Mathis_77) within their respective size ranges." (Physical Model)
   - fitting: Inherited gas density and temperature fit with EMCEE MCMC and high-resolution CO observations; priors and likelihood not stated  
  > "The gas density and temperature structures were parameterized and fit using the Markov Chain Monte Carlo (MCMC) routine EMCEE (cite: foreman_mackey) and high resolution CO observations." (Physical Model)
   - validation: _not stated_
4. **Calculate the ionizing radiation fields**: 2D Monte Carlo UV/X-ray radiative transfer; column-dependent CR attenuation  
  > "Two-dimensional stellar X-ray and UV fluxes (Figure [3](#fig:structure_all)) were obtained using the (cite: bethell_bergin) Monte Carlo radiative transfer code and cross sections." (Ionization Model); "Our modeling suite includes five different incident CR–ionization rates ($\zeta_{CR}$) listed in Table [1](#tab:cr) and CR attenuation as a function of column density, as described in (cite: cleeves13a)." (Ionization Model)
   - software: (cite: bethell_bergin) Monte Carlo radiative transfer code
   - parameter: TW Hya UV spectrum scaled by 2.16 to DM Tau’s FUV luminosity  
  > "We use an observed stellar UV spectrum for TW Hya and scale it to DM Tau’s FUV luminosity by a factor of 2.16." (Ionization Model)
   - parameter: X-ray luminosity: 2.5 × 10^29 erg s^-1; energies: 1–20 keV  
  > "Both spectra are scaled to an X-ray luminosity of 2.5 $\times$ 10$^{29}$ erg s$^{-1}$ for DM Tau" (Ionization Model); "Our X-ray models include energies from 1–20 keV." (Ionization Model)
   - parameter: Quiescent HR = -0.8; flaring HR = 0.3  
  > "The quiescent model (HR = -0.8) is soft X-ray dominated, while the hardened “flaring" model (HR = 0.3) is hard X-ray dominated." (Ionization Model)
   - parameter: M02 zeta_CR = 6.8 × 10^-16 s^-1  
  > "| (cite: mosk_2002)    |  M02  | 6.8 $\times$ 10$^{-16}$ |     |     |     |" (Table 1)
   - parameter: W98 zeta_CR = 2.0 × 10^-17 s^-1  
  > "| (cite: webber_1998)  |  W98  | 2.0 $\times$ 10$^{-17}$ |     |     |     |" (Table 1)
   - parameter: SSM zeta_CR = 1.1 × 10^-18 s^-1  
  > "| Solar System Min Mod |  SSM  | 1.1 $\times$ 10$^{-18}$ |     |     |     |" (Table 1); "The observed emission profiles for all four lines are best fit by a model with a hard X-ray spectrum and a CR ionization rate of 1.1 $\times$ 10$^{-18}$ s$^{-1}$." (Standard Turbulence Models)
   - parameter: SSX zeta_CR = 1.6 × 10^-19 s^-1  
  > "| Solar System Max Mod |  SSX  | 1.6 $\times$ 10$^{-19}$ |     |     |     |" (Table 1)
   - parameter: TTX zeta_CR = 1.0 × 10^-21 s^-1  
  > "| T Tauri Max Mod      |  TTX  | 1.0 $\times$ 10$^{-21}$ |     |     |     |" (Table 1)
   - assumption: Ionization from UV photons, X-ray photons and CRs; inherited SLR effects excluded  
  > "Our models include ionization from three sources: UV photons, X-ray photons, and CRs." (Ionization Model); "We exclude effects of inherited short-lived radionuclides (SLRs) for now since their initial abundance is uncertain" (Ionization Model)
   - fitting: _not stated_
   - validation: _not stated_
5. **Evolve the disk chemistry**: 2D time-dependent rate-equation chemistry over the ten radiation models  
  > "Chemical abundances are calculated as a function of position and time using a 2D time–dependent rate equation chemical code from (cite: fogel_2011) adapted in (cite: cleeves_2014_water) and (cite: anderson_2021)." (Chemical Model)
   - software: 2D time–dependent rate equation chemical code
   - parameter: 18,608 reactions; 1038 species, including deuterium isotopologues  
  > "The results presented in this work utilize our latest updated chemical network with 18,608 reactions and 1038 species, including deuterium isotopologues." (Chemical Model)
   - parameter: Chemical evolution time: 1 Myr  
  > "Models are computed out to a time of 1 Myr, at which point the ion chemistry has settled into a pseudo-steady state." (Chemical Model)
   - assumption: Table 2 molecular-cloud initial abundances  
  > "Our initial abundances (Table [2](#tab:abunds)) are representative of the chemical conditions in a typical molecular cloud." (Chemical Model)
   - assumption: Average CO depletion factor 5; starting CO abundance 2.6 × 10^-5  
  > "Based on this range we choose to use an “average" CO depletion factor of 5 such that our starting CO abundance is 2.6 $\times$ 10$^{-5}$." (Chemical Model)
   - assumption: H13CO+ from HCO+ using constant 12C/13C = 60  
  > "we retrieve H$^{13}$CO$^+$ abundances by applying a constant $^{12}$C/$^{13}$C ratio of 60 (cite: langer_penzias_1993)" (Chemical Model)
   - fitting: _not stated_
   - validation: Ion chemistry described as pseudo-steady at 1 Myr  
  > "Models are computed out to a time of 1 Myr, at which point the ion chemistry has settled into a pseudo-steady state." (Chemical Model)
6. **Generate synthetic line cubes**: LIME non-LTE radiative transfer of chemical abundances to emergent flux and optical depth  
  > "The resulting disk abundances are input to the `LIME` non-LTE radiative transfer code (cite: brinch_2010) in order to calculate the emergent flux and optical depth for HCO$^+$, N$_2$H$^+$, and H$^{13}$CO$^+$." (Synthetic Observation Comparison)
   - software: LIME, LAMDA
   - parameter: Doppler b = 0.2cs and 0.5cs  
  > "For our “standard turbulence" models we use b = 0.2c$_{s}$." (Synthetic Observation Comparison); "We also run `LIME` models with high turbulent velocities (b = 0.5c$_{s}$) for comparison." (Synthetic Observation Comparison)
   - parameter: Spectral over-sampling and channel averaging by factor 20  
  > "The `LIME` models for HCO$^+$, H$^{13}$CO$^+$, and N$_2$H$^+$ are spectrally over-sampled and channel averaged by a factor of 20 to mimic channel smearing seen in real observations." (Synthetic Observation Comparison)
   - assumption: Distance 144.5 pc; inclination 35.2 degrees  
  > "All of the models assume a distance of 144.5 pc (cite: lindegren_2018) and an inclination of 35.2$^{\circ}$ (cite: Kudo_2018)." (Synthetic Observation Comparison)
   - assumption: LAMDA collisional rates  
  > "We use collisional rates from the LAMDA database (cite: schoer_2005; daniel_2005; denis_2020)." (Synthetic Observation Comparison)
   - fitting: _not stated_
   - validation: Synthetic cubes match observed channel counts and channel widths  
  > "The resulting fits cubes have the same number of channels and the same channel widths as the observations listed in Table [\[tab:obs\]](#tab:obs)." (Synthetic Observation Comparison)
7. **Match synthetic observations to ALMA sampling**: vissample using observed measurement sets; CASA imaging; GoFish radialprofile extraction  
  > "We use `vissample` (cite: Loomis_2018) to perform visibility sampling of our LIME fits cubes." (Synthetic Observation Comparison); "We perform continuum subtraction and image the model measurement sets in CASA `v.5.6.0` with the same parameters described in Section 2." (Synthetic Observation Comparison); "Radial profiles are generated using the `radialprofile` function in the `GoFish` program (cite: GoFish)." (Synthetic Observation Comparison)
   - software: vissample, CASA, GoFish, radialprofile
   - parameter: Same Keplerian masks and velocity ranges as observed moment maps  
  > "We apply the same Keplerian masks used to image the observations and integrate emission over the same velocity ranges used to produce the moment zero maps shown in Figure [2](#fig:moments)." (Synthetic Observation Comparison)
   - fitting: _not stated_
   - validation: Observed measurement sets ensure matching uv coverage  
  > "By using the ALMA measurement sets from our observations as inputs, we ensure that our simulated observations have the same uv coverage as the real observations." (Synthetic Observation Comparison)
8. **Select ionization models**: Compare observed and modeled radial profiles using reduced chi-squared; fit global and outer-disk regions for both turbulence choices  
  > "We measure the goodness of fit for each model by calculating the reduced $\chi^{2}$ values for the model radial profiles of HCO$^+$, H$^{13}$CO$^+$, and N$_2$H$^+$." (Results)
   - parameter: Global fitting: radii <500 au  
  > "Observed emission reaches zero for all four lines by 500 au, so we consider radii $<$ 500 au when calculating the global goodness of fit." (Global Model Fitting)
   - parameter: Outer disk: radii >200 au  
  > "We consider the outer disk to be radii $>$ 200 au, as this is the radius at which HCO$^+$ and H$^{13}$CO$^+$ are no longer universally under-bright." (Outer Disk Fitting)
   - assumption: Image-plane fitting weights all radii equally; combined comparison weights all four lines equally  
  > "We choose to work in the image plane so that all radii are weighted equally in our fitting routine" (Results); "SSM-F is the best global fit ($\chi^{2}_{red, mean}$ = 13.8) when we consider all four lines weighted equally." (Standard Turbulence Models)
   - fitting: Discrete model-grid ranking by radial-profile reduced chi-squared; no sampler, priors or likelihood stated for this fit  
  > "We use the radial profile reduced $\chi^{2}$ values as a guide for identifying the best-fit models." (Results); "this analysis ultimately provides a strong constraint on the best-fit model relative to the rest of the model grid." (Results)
   - validation: Compare individual-line preferences, global versus outer-disk fits and standard versus high turbulence  
  > "The resulting best-fit model for each line remains unchanged aside from N$_2$H$^+$ $J = 4 - 3$, which changes from SSM-F to SSX-F." (High Turbulence Models); "The best-fit model for all four lines is still SSM-F, for both the standard ($\chi^{2}_{red}$ = 17.3) and high turbulence ($\chi^{2}_{red}$ = 12.8) models." (Outer Disk Fitting)
9. **Test sensitivity to CO depletion**: Compare radial profiles for no depletion, factor 5 and factor 10 depletion; check modeled C18O flux against literature  
  > "We compared the radial profile results from our “average" (factor of 5) depletion model to those from models with no CO depletion and a factor of 10 CO depletion." (N$_2$H$^+$ Radial Structure); "Our average-depleted model yields an C$^{18}$O integrated flux of 4.9 Jy km s$^{-1}$" (N$_2$H$^+$ Radial Structure)
   - parameter: No-depletion initial CO abundance = 1.3 × 10^-4  
  > "We tested the sensitivity of our models to the CO depletion profile by running an additional model grid with no CO depletion (initial CO abundance = 1.3 $\times$ 10$^{-4}$)." (Sensitivity to CO Depletion Profile)
   - fitting: Radial-profile comparison  
  > "We compared the radial profile results from our “average" (factor of 5) depletion model to those from models with no CO depletion and a factor of 10 CO depletion." (N$_2$H$^+$ Radial Structure)
   - validation: N2H+ J = 3 - 2 flux changes by <2; reduced ionization still needed without CO depletion  
  > "The resulting N$_2$H$^+$ $J = 3 - 2$ radial profiles are relatively insensitive to the level of CO depletion (varying by a factor of $<$ 2 in flux)" (N$_2$H$^+$ Radial Structure); "Thus, even if we leave CO undepleted, a reduced rate of ionization is required to fit the observations." (N$_2$H$^+$ Radial Structure)
10. **Check the N2H+ temperature interpretation**: RADEX interpretation of the observed N2H+ J = 4 - 3 / J = 3 - 2 flux ratio at 100 au  
  > "using the `RADEX` radiative transfer code (cite: radex), the ratio of observed fluxes between the $J = 4 - 3$ and $J = 3 - 2$ transitions at 100 au suggests a temperature of 25 K." (N$_2$H$^+$ Radial Structure)
   - software: RADEX
   - fitting: _not stated_
   - validation: 25 K agrees with physical-model temperatures of 20-30 K at 100 au  
  > "This agrees with our model temperatures at 100 au, which range between 20-30 K from midplane to surface." (N$_2$H$^+$ Radial Structure)

## Software

- **CASA** v5.6.1 (observations); v.5.6.0 (synthetic measurement sets): Pipeline calibration, continuum subtraction and imaging  
  > "These data were calibrated with the CASA Pipeline, with J0423-0120 as the band-pass calibrator and J0510+1800 as the phase calibrator." (ALMA Observations); "We performed continuum subtraction and imaging for all lines using the `uvcontsub` and `tclean` commands from CASA `v5.6.1` and Keplerian masks generated with the `keplerianmask`[^1] Python package (cite: teague_2020_kep)." (ALMA Observations); "We perform continuum subtraction and image the model measurement sets in CASA `v.5.6.0` with the same parameters described in Section 2." (Synthetic Observation Comparison)
- **uvcontsub** CASA v5.6.1: Continuum subtraction  
  > "We performed continuum subtraction and imaging for all lines using the `uvcontsub` and `tclean` commands from CASA `v5.6.1` and Keplerian masks generated with the `keplerianmask`[^1] Python package (cite: teague_2020_kep)." (ALMA Observations)
- **tclean** CASA v5.6.1: Line imaging  
  > "We performed continuum subtraction and imaging for all lines using the `uvcontsub` and `tclean` commands from CASA `v5.6.1` and Keplerian masks generated with the `keplerianmask`[^1] Python package (cite: teague_2020_kep)." (ALMA Observations)
- **keplerianmask** : Generate Keplerian imaging masks  
  > "We performed continuum subtraction and imaging for all lines using the `uvcontsub` and `tclean` commands from CASA `v5.6.1` and Keplerian masks generated with the `keplerianmask`[^1] Python package (cite: teague_2020_kep)." (ALMA Observations)
- **VISIBLE** : Matched-filter detection of N2H+ J = 4 - 3  
  > "We used the `matchedfilter` command from the `VISIBLE`[^2] Python package (cite: Loomis_2018) with our HCO$^+$ detection as a filter." (ALMA Observations); "We saw a 6$\sigma$ response, indicating the presence of N$_2$H$^+$ $J = 4 - 3$." (ALMA Observations)
- **matchedfilter** : Filter noisy N2H+ data using the HCO+ detection  
  > "We used the `matchedfilter` command from the `VISIBLE`[^2] Python package (cite: Loomis_2018) with our HCO$^+$ detection as a filter." (ALMA Observations)
- **bettermoments** : Zeroth-moment maps of resolved detections  
  > "We create velocity integrated intensity (zeroth moment) maps (Figure [2](#fig:moments)) for the resolved detections using the `bettermoments`[^3] Python package (cite: teague_2018_bm)." (ALMA Observations)
- **GoFish** : Observed and modeled radial emission profiles  
  > "Radial profiles are generated using the `radialprofile` function in the `GoFish` program (cite: GoFish)." (Synthetic Observation Comparison)
- **radialprofile** : GoFish radial-profile extraction  
  > "Radial profiles are generated using the `radialprofile` function in the `GoFish` program (cite: GoFish)." (Synthetic Observation Comparison)
- **EMCEE** : MCMC fitting of the inherited CO-based gas density and temperature structure  
  > "The gas density and temperature structures were parameterized and fit using the Markov Chain Monte Carlo (MCMC) routine EMCEE (cite: foreman_mackey) and high resolution CO observations." (Physical Model)
- **(cite: bethell_bergin) Monte Carlo radiative transfer code** : 2D stellar X-ray and UV fluxes  
  > "Two-dimensional stellar X-ray and UV fluxes (Figure [3](#fig:structure_all)) were obtained using the (cite: bethell_bergin) Monte Carlo radiative transfer code and cross sections." (Ionization Model)
- **2D time–dependent rate equation chemical code** : Time- and position-dependent chemical abundances  
  > "Chemical abundances are calculated as a function of position and time using a 2D time–dependent rate equation chemical code from (cite: fogel_2011) adapted in (cite: cleeves_2014_water) and (cite: anderson_2021)." (Chemical Model)
- **LIME** : Non-LTE emergent flux and optical-depth calculations  
  > "The resulting disk abundances are input to the `LIME` non-LTE radiative transfer code (cite: brinch_2010) in order to calculate the emergent flux and optical depth for HCO$^+$, N$_2$H$^+$, and H$^{13}$CO$^+$." (Synthetic Observation Comparison)
- **LAMDA** : Database of collisional rates  
  > "We use collisional rates from the LAMDA database (cite: schoer_2005; daniel_2005; denis_2020)." (Synthetic Observation Comparison)
- **vissample** : Visibility sampling of LIME cubes with observed ALMA measurement sets  
  > "We use `vissample` (cite: Loomis_2018) to perform visibility sampling of our LIME fits cubes." (Synthetic Observation Comparison); "By using the ALMA measurement sets from our observations as inputs, we ensure that our simulated observations have the same uv coverage as the real observations." (Synthetic Observation Comparison)
- **RADEX** : Temperature check from the N2H+ transition flux ratio at 100 au  
  > "using the `RADEX` radiative transfer code (cite: radex), the ratio of observed fluxes between the $J = 4 - 3$ and $J = 3 - 2$ transitions at 100 au suggests a temperature of 25 K." (N$_2$H$^+$ Radial Structure)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| N2H+ J = 4 - 3 integrated flux | 0.7 | ± 0.24 | Jy km s^-1 | 2 | / N$_2$H$^+$ $J = 4 - 3$ / 372.672 / 0$.\!\!^{\prime\prime}$66 $\times$ 0$.\!\!^{\prime\prime}$64 (7.0$^{\circ}$) / 0.114 / 46 / 0.7 $\pm$ 0.24 / |
| HCO+ J = 4 - 3 integrated flux | 6.8 | ± 0.69 | Jy km s^-1 | 2 | / HCO$^+$ $J = 4 - 3$ / 356.734 / 0$.\!\!^{\prime\prime}$42 $\times$ 0$.\!\!^{\prime\prime}$32 (-6.2$^{\circ}$) / 0.119 / 8.6 / 6.8 $\pm$ 0.69 / |
| N2H+ J = 3 - 2 integrated flux | 1.3 | ± 0.14 | Jy km s^-1 | 2 | / N$_2$H$^+$ $J = 3 - 2$ / 279.512 / 0$.\!\!^{\prime\prime}$29 $\times$ 0$.\!\!^{\prime\prime}$27 (0.99$^{\circ}$) / 0.150 / 3.9 / 1.3 $\pm$ 0.14 / |
| H13CO+ J = 3 - 2 integrated flux | 0.41 | ± 0.046 | Jy km s^-1 | 2 | / H$^{13}$CO$^+$ $J = 3 - 2$ / 260.255 / 0$.\!\!^{\prime\prime}$67 $\times$ 0$.\!\!^{\prime\prime}$55 (46$^{\circ}$) / 0.163 / 3.2 / 0.41 $\pm$ 0.046 / |
| 1 mm continuum integrated flux | 0.08 | ± 0.008 | Jy | 0 | / Continuum / 1 mm / 0$.\!\!^{\prime\prime}$25 $\times$ 0$.\!\!^{\prime\prime}$16 (53$^{\circ}$) / 1875 MHz$^{b}$ / 0.15 / 0.08 $\pm$ 0.008 Jy / |
| 1.3 mm continuum integrated flux | 0.16 | ± 0.016 | Jy | 0 | / Continuum / 1.3 mm / 0$.\!\!^{\prime\prime}$38 $\times$ 0$.\!\!^{\prime\prime}$28 (-17$^{\circ}$) / 1875 MHz / 0.27 / 0.16 $\pm$ 0.016 Jy / |
| N2H+ J = 4 - 3 matched-filter response | 6 | not stated | sigma | 2 | We saw a 6$\sigma$ response, indicating the presence of N$_2$H$^+$ $J = 4 - 3$. |
| HCO+ observed emission-peak radius | 30 | not stated | au | 2 | The observed HCO$^+$ and H$^{13}$CO$^+$ emission profiles each exhibit a small inner deficit and emission peaks at 30 and 40 au respectively. |
| H13CO+ observed emission-peak radius | 40 | not stated | au | 2 | The observed HCO$^+$ and H$^{13}$CO$^+$ emission profiles each exhibit a small inner deficit and emission peaks at 30 and 40 au respectively. |
| N2H+ J = 3 - 2 observed emission-peak radius | 100 | not stated | au | 2 | The observed N$_2$H$^+$ $J = 3 - 2$ emission profile exhibits a peak at 100 au and an emission “plateau" between $\sim$ 200-350 au followed by a stark drop-off. |
| N2H+ J = 3 - 2 observed emission-plateau radii | ~ 200-350 | not stated | au | 2 | The observed N$_2$H$^+$ $J = 3 - 2$ emission profile exhibits a peak at 100 au and an emission “plateau" between $\sim$ 200-350 au followed by a stark drop-off. |
| Best-fit CR ionization rate | 1.1 × 10^-18 | not stated | s^-1 | 8 | The observed emission profiles for all four lines are best fit by a model with a hard X-ray spectrum and a CR ionization rate of 1.1 $\times$ 10$^{-18}$ s$^{-1}$. |
| Preferred X-ray hardness ratio | 0.3 | not stated | dimensionless | 8 | Our observations appear to trace a flaring state of DM Tau (HR = 0.3). |
| Standard-turbulence HCO+ best global reduced chi-squared, W98-F | 19.3 | not stated | dimensionless | 8 | W98-F emerges as the best global fit for both HCO$^+$ ($\chi^{2}_{red}$ = 19.3) and H$^{13}$CO$^+$ ($\chi^{2}_{red}$ = 2.3). |
| Standard-turbulence H13CO+ best global reduced chi-squared, W98-F | 2.3 | not stated | dimensionless | 8 | W98-F emerges as the best global fit for both HCO$^+$ ($\chi^{2}_{red}$ = 19.3) and H$^{13}$CO$^+$ ($\chi^{2}_{red}$ = 2.3). |
| Standard-turbulence N2H+ J = 3 - 2 best global reduced chi-squared, SSM-F | 23.7 | not stated | dimensionless | 8 | Overall, SSM-F emerges as the best global fit for both N$_2$H$^+$ $J = 3 - 2$ ($\chi^{2}_{red}$ = 23.7) and N$_2$H$^+$ $J = 4 - 3$ ($\chi^{2}_{red}$ = 1.48). |
| Standard-turbulence N2H+ J = 4 - 3 best global reduced chi-squared, SSM-F | 1.48 | not stated | dimensionless | 8 | Overall, SSM-F emerges as the best global fit for both N$_2$H$^+$ $J = 3 - 2$ ($\chi^{2}_{red}$ = 23.7) and N$_2$H$^+$ $J = 4 - 3$ ($\chi^{2}_{red}$ = 1.48). |
| Standard-turbulence all-line global mean reduced chi-squared, SSM-F | 13.8 | not stated | dimensionless | 8 | SSM-F is the best global fit ($\chi^{2}_{red, mean}$ = 13.8) when we consider all four lines weighted equally. |
| High-turbulence all-line global best reduced chi-squared, SSM-F | 12.3 | not stated | dimensionless | 8 | The $\chi^{2}_{red}$ score for the best fit model for all four lines is slightly improved from 13.8 to 12.3.; Thus we consider the high turbulence SSM-F model to be our best fit |
| Standard-turbulence outer-disk all-line best reduced chi-squared, SSM-F | 17.3 | not stated | dimensionless | 8 | The best-fit model for all four lines is still SSM-F, for both the standard ($\chi^{2}_{red}$ = 17.3) and high turbulence ($\chi^{2}_{red}$ = 12.8) models. |
| High-turbulence outer-disk all-line best reduced chi-squared, SSM-F | 12.8 | not stated | dimensionless | 8 | The best-fit model for all four lines is still SSM-F, for both the standard ($\chi^{2}_{red}$ = 17.3) and high turbulence ($\chi^{2}_{red}$ = 12.8) models. |
| Best-fit model surface ionization fraction | > 1 × 10^-4 | not stated | dimensionless | 8 | the ionization fraction in DM Tau varies from $\chi_{e}$ $>$ 1 $\times$ 10$^{-4}$ at the surface to $\chi_{e}$ $<$ 1 $\times$ 10$^{-10}$ in the midplane |
| Best-fit model midplane ionization fraction | < 1 × 10^-10 | not stated | dimensionless | 8 | the ionization fraction in DM Tau varies from $\chi_{e}$ $>$ 1 $\times$ 10$^{-4}$ at the surface to $\chi_{e}$ $<$ 1 $\times$ 10$^{-10}$ in the midplane |
| Average-depleted model C18O integrated flux | 4.9 | not stated | Jy km s^-1 | 9 | Our average-depleted model yields an C$^{18}$O integrated flux of 4.9 Jy km s$^{-1}$ |
| Temperature suggested by the N2H+ transition ratio at 100 au | 25 | not stated | K | 10 | using the `RADEX` radiative transfer code (cite: radex), the ratio of observed fluxes between the $J = 4 - 3$ and $J = 3 - 2$ transitions at 100 au suggests a temperature of 25 K. |
| High-CR modeled HCO+ peak-intensity change under an X-ray flare | 5 | not stated | mJy beam^-1 km s^-1 | 8 | only changing the peak profile intensity ($\Delta$I$_{peak}$) by an average of 5 mJy beam$^{-1}$ km s$^{-1}$.; in the presence of a high $\zeta_{CR}$ (M02, W98), the effect of an X-ray flare on the emission of optically thick HCO$^+$ is subtle |
| Low-CR modeled HCO+ peak-intensity change under an X-ray flare | 50–80 | not stated | mJy beam^-1 km s^-1 | 8 | an X-ray flare under low $\zeta_{CR}$ conditions (SSM, SSX, TTX) will have a more noticeable effect on the observed HCO$^+$ emission, with $\Delta$I$_{peak}$ = 50–80 mJy beam$^{-1}$ km s$^{-1}$. |

## Qualitative findings

- High-turbulence SSM-F is the best combined model, but the turbulence improvement is not significant.  
  > "Thus we consider the high turbulence SSM-F model to be our best fit" (High Turbulence Models); "The improvement with high turbulent velocity is not significant, but leads to slightly better fits." (Conclusions)
- Models underproduce inner-disk emission and miss the N2H+ J = 3 - 2 plateau and edge.  
  > "All of the models for HCO$^+$ and H$^{13}$CO$^+$ are under-bright in the inner disk" (Outer Disk Fitting); "None of the models reproduce the observed emission plateau and edge." (Standard Turbulence Models)
- CO depletion changes alone cannot explain the simultaneous inner-disk emission enhancement.  
  > "Since brighter inner disk fluxes are required to fit the observed emission for both species, the CO depletion profile itself cannot account for the “boost" in emission in the inner disk." (Sensitivity to CO Depletion Profile)
- Resolved optically thin tracers at different emitting heights are needed to constrain ionization gradients.  
  > "Thus, studies of disk ionization should include resolved observations of at least two optically thin tracers tracing distinct disk emitting heights." (Uses of Different Ionization Tracers)

## Claim tuples

- H: Which CR rate and X-ray state best reproduce the molecular-ion emission? | E: Forward-model four lines and compare global and outer-disk radial profiles. | R: SSM-F is preferred; zeta_CR = 1.1 × 10^-18 s^-1; hard X-ray spectrum; high-turbulence global score 12.3. | F: A reduced CR rate and hardened X-ray spectrum best fit the tested grid. | **supported**
- H: Can one ionization prescription reproduce both the inner and outer disk? | E: Inspect radial-profile residuals and compare global with outer-disk fitting. | R: The models require brighter inner-disk ion emission while reduced CR ionization fits the outer disk. | F: An inner-disk ionization enhancement or additional physics is suggested; its mechanism is unresolved. | **partially**
- H: Can changing CO depletion alone explain the inner-disk discrepancies? | E: Compare factor-5 depletion with undepleted and factor-10 models. | R: Increasing CO brightens H13CO+ but dims N2H+ in the inner disk. | F: The CO depletion profile alone cannot provide the required enhancement in both species. | **refuted**
- H: Do the observations indicate a flaring X-ray state? | E: Compare quiescent and hardened X-ray models for each line. | R: All four lines prefer hardened X-ray models, HR = 0.3. | F: The observations appear to trace a flaring state; multi-epoch observations are needed to test variability. | **partially**
- H: Do these line data independently establish high turbulence? | E: Compare b = 0.2cs and b = 0.5cs synthetic observations. | R: The best combined global reduced chi-squared improves from 13.8 to 12.3. | F: The improvement is insufficient evidence for high turbulence alone. | **refuted**

## Reasoning

- Why this data: Multiple tracers probe different disk emitting heights and ionization gradients.  
  > "It is important to use multiple tracers that probe different disk emitting heights to interpret the ionization environments of protoplanetary disks." (Uses of Different Ionization Tracers)
- Why this method: Image-plane radial fitting weights radii equally and exposes ionization gradients.  
  > "We choose to work in the image plane so that all radii are weighted equally in our fitting routine" (Results); "Thus by working in the image plane and with the radial profiles, we can more easily examine where our models are in agreement and identify ionization gradients if present." (Results)
- Alternative: High versus standard turbulent line broadening  
  > "For our “standard turbulence" models we use b = 0.2c$_{s}$." (Synthetic Observation Comparison); "We also run `LIME` models with high turbulent velocities (b = 0.5c$_{s}$) for comparison." (Synthetic Observation Comparison)
- Alternative: No CO depletion and factor-10 depletion compared with factor 5  
  > "We compared the radial profile results from our “average" (factor of 5) depletion model to those from models with no CO depletion and a factor of 10 CO depletion." (N$_2$H$^+$ Radial Structure)
- Alternative: Midplane temperature changes and a VIRaM layer as possible explanations for the N2H+ peak  
  > "Finally, another mechanism that could reproduce the N$_2$H$^+$ peak is a change in the model’s midplane temperature." (N$_2$H$^+$ Radial Structure); "(cite: qi_2019) are able to reproduce the N$_2$H$^+$ $J = 3 - 2$ radial profile by including a Vertically Isothermal Region above the Midplane (VIRaM layer) in their temperature model." (N$_2$H$^+$ Radial Structure)
- Alternative: Stellar energetic particles and CR acceleration near the star as additional ionization sources  
  > "Both of these results suggest that SPs and CR acceleration close to the central star could play a role in boosting inner disk ionization." (The Ionization Environment of DM Tau)
- Alternative: Magnetic shearing as a possible source of stronger vertical CR attenuation  
  > "One possible theory is cosmic ray exclusion within the disk itself by magnetic shearing (cite: fujii_2022)" (The Ionization Environment of DM Tau)
- Alternative: Inherited short-lived radionuclide ionization excluded  
  > "We exclude effects of inherited short-lived radionuclides (SLRs) for now since their initial abundance is uncertain" (Ionization Model)
- How they decided it was enough: Chemistry evolved to pseudo-steady state at 1 Myr; global fitting restricted to <500 au where emission disappears.  
  > "Models are computed out to a time of 1 Myr, at which point the ion chemistry has settled into a pseudo-steady state." (Chemical Model); "Observed emission reaches zero for all four lines by 500 au, so we consider radii $<$ 500 au when calculating the global goodness of fit." (Global Model Fitting)
- Limitation (authors): N2H+ J = 4 - 3 is noisy and unresolved.  
  > "The data for N$_2$H$^+$ $J = 4 - 3$ was significantly more noisy than the other lines due to its close proximity to atmospheric water vapour features." (ALMA Observations); "Though the N$_2$H$^+$$J = 4 - 3$ line is not resolved in the observations we still report the integrated flux and include this line in our analysis." (ALMA Observations)
- Limitation (authors): Best-fit ranking does not yield a satisfactory reproduction of all radial morphology.  
  > "None of the models reproduce the observed emission plateau and edge." (Standard Turbulence Models); "While the SSM-F model emerges as the best global fit for this line ($\chi^{2}$ = 23.7), it does not reproduce the observed emission peak." (N$_2$H$^+$ Radial Structure)
- Limitation (authors): Ionization, temperature and gas-phase CO abundance are degenerate.  
  > "Ultimately, the emission morphology of N$_2$H$^+$ is dependent on a combination of effects from ionization, temperature, and gas-phase CO abundance." (N$_2$H$^+$ Radial Structure); "These parameters/processes are degenerate with one another, and additional modeling efforts are necessary to disentangle their effects." (N$_2$H$^+$ Radial Structure)
- Limitation (authors): Carbon isotopes are absent from the network; a constant isotope ratio is imposed despite possible radial variations.  
  > "Our network does not include carbon isotopes $^{12}$C and $^{13}$C" (Chemical Model); "however in reality we expect that the gas-phase $^{12}$C/$^{13}$C ratio may have radial variations, particularly across the CO snowline (cite: yoshida_22)." (Chemical Model)
- Limitation (authors): The CO-based temperature model does not explicitly probe the midplane.  
  > "Our temperature model was derived from observations of CO, which do not explicitly probe the midplane." (N$_2$H$^+$ Radial Structure)
- Limitation (authors): The data do not definitively establish MRI-driven turbulence.  
  > "Our results alone do not suggest definitively that DM Tau’s turbulence is MRI-driven." (The Ionization Environment of DM Tau)
- Limitation (authors): Sensitivity is insufficient to establish the proposed steeper vertical ionization gradient.  
  > "perhaps the data are pointing to a steeper vertical gradient than what is captured in the present models." (The Ionization Environment of DM Tau); "The sensitivity of the data is not sufficient to definitively say, but it provides an interesting avenue for future follow up." (The Ionization Environment of DM Tau)
- Caveat (inferred, ours): The preferred CR rate is a discrete-grid choice; parameter confidence intervals are not supplied.
- Caveat (inferred, ours): Large reduced chi-squared values make the ranking a relative model comparison rather than an adequate absolute fit.
- Caveat (inferred, ours): Radial-bin covariance and correlated flux-scale errors could affect combined fit statistics.
- Caveat (inferred, ours): The flaring interpretation comes from template preference rather than contemporaneous X-ray monitoring described here.
- Caveat (inferred, ours): A temperature estimate at 100 au from an unresolved, noisy N2H+ 4-3 line needs the extraction and RADEX assumptions to be assessed.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: keplerian_mask: https://github.com/richteague/keplerian_mask  
  > "[^1]: <https://github.com/richteague/keplerian_mask>" (Azimuthally averaged optical depth profiles)
- Code: VISIBLE: https://github.com/AstroChem/VISIBLE  
  > "[^2]: <https://github.com/AstroChem/VISIBLE>" (Azimuthally averaged optical depth profiles)
- Code: bettermoments: https://github.com/richteague/bettermoments  
  > "[^3]: <https://github.com/richteague/bettermoments>" (Azimuthally averaged optical depth profiles)
- Code: gofish: https://github.com/richteague/gofish  
  > "[^4]: <https://github.com/richteague/gofish>" (Azimuthally averaged optical depth profiles)
- Missing: Paper-specific calibration, imaging, masking, profile-extraction and fitting scripts.
- Missing: Full inherited physical structure and the exact updated chemical network.
- Missing: Input radiation spectra, opacity/cross-section inputs and molecular-data files.
- Missing: Self-calibration and continuum-subtraction settings.
- Missing: Image grid, deconvolution stopping rules, mask parameters and integration ranges.
- Missing: Radiative-transfer convergence settings and synthetic-observation configuration.
- Missing: Exact chi-squared implementation and radial-profile uncertainties.
- Missing: Explicit public-data status and identification of available calibrated or model products.
- Data volume (inferred): not stated
- Score (inferred): 5/5, 5/10: project codes, major software, model grid and numeric targets are given, but inherited structures, the updated chemical network and several essential processing settings are missing.
- Rediscovery candidate: no, Numeric results and project codes are supplied, but public availability is not explicitly stated and essential model inputs and processing settings are missing.

## Links

- Method: (cite: casa_mcmullin_2007) (CASA calibration and imaging software.)
- Method: (cite: teague_2020_kep) (Keplerian imaging masks.)
- Method: (cite: Loomis_2018) (Matched filtering and visibility sampling.)
- Method: (cite: teague_2018_bm) (Zeroth-moment maps with bettermoments.)
- Method: (cite: GoFish) (Radial emission profiles.)
- Method: (cite: foreman_mackey) (EMCEE MCMC for the inherited gas structure.)
- Method: (cite: bethell_bergin) (UV/X-ray Monte Carlo transfer and cross sections.)
- Method: (cite: cleeves13a) (CR modulation models and column-dependent attenuation.)
- Method: (cite: fogel_2011) (Base 2D time-dependent chemical code.)
- Method: (cite: cleeves_2014_water) (Chemical-code adaptation.)
- Method: (cite: anderson_2021) (Chemical-code adaptation.)
- Method: (cite: brinch_2010) (LIME non-LTE line transfer.)
- Method: (cite: schoer_2005; daniel_2005; denis_2020) (LAMDA collisional data.)
- Method: (cite: radex) (RADEX temperature check from the N2H+ line ratio.)
- Method: (cite: Mathis_77) (MRN grain-size distributions.)
- Companion: (cite: qi_2019) (Earlier N2H+ J = 3 - 2 observations, calibration and natural-weighting choice.)
- Companion: (cite: flaherty) (Inherited CO-constrained gas structure and turbulence comparison.)
- Companion: (cite: Andrews_2011) (Continuum/SED-based dust structure and inner-gap parameters.)
- Companion: (cite: cleeves15_twhya) (Quiescent and flaring X-ray templates.)
- Companion: (cite: Zhang_2019) (Radial CO-depletion constraints and C18O flux comparison.)

## Checks

```json
{
 "quotes": 259,
 "quotes_ok": 259,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 27,
 "numeric_problems": 0,
 "fill": {
  "facts": 180,
  "stated": 151,
  "rate": 0.839
 },
 "evidence_ok": true
}
```
