# HCN as a probe of the inner disc in a candidate proto-brown dwarf

`2024MNRAS.532L..36R` | Monthly Notices of the Royal Astronomical Society 2024 | first author: Riaz, B. | arXiv: 2405.11321 | DOI: 10.1093/mnrasl/slae044

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Whether HCN (3-2) line emission can trace the inner (Keplerian) disk of the Class 0 proto-brown dwarf candidate Ser-emb 16  
  > "We have investigated the high-density tracer HCN as a probe of the inner disk in a Class 0 proto-brown dwarf candidate." (abstract); "We have explored if the HCN (3-2) line emission could be a useful tracer of the inner Keplerian disk in a proto-brown dwarf system." (Conclusions)
- Target **Ser-emb 16**: coordinates _not stated_; z/distance d = 440 +/- 9 pc  
  > "located in the Serpens region ($d$=440$\pm$9 pc) (Ortiz-León et al. 2017; Gong et al. 2021)." (Introduction); distance from Ortiz-León et al. 2017; Gong et al. 2021  
  > "located in the Serpens region ($d$=440$\pm$9 pc) (Ortiz-León et al. 2017; Gong et al. 2021)." (Introduction)

## Data provenance

- ALMA projects: 2021.1.00134.S
- bands: Band 6  
  > "We observed Ser-emb 16 with ALMA in the HCN (3-2) line at 265.8865 GHz in Band 6." (Observations and Data Analysis)
- frequencies and spectral setup: HCN (3-2) at 265.8865 GHz; bandwidth 117.18 MHz, 244.14 kHz resolution (~0.3-0.4 km/s); HCO+ (3-2) also in the setup  
  > "The bandwidth was set to 117.18 MHz, which provides a resolution of 244.14 kHz, or a velocity resolution of $\sim$0.3-0.4 km s$^{-1}$ at 265.8 GHz." (Observations and Data Analysis); "The spectral setup in our ALMA observations included the HCO$^{+}$ (3-2) line." (Comparison of HCN and HCO$^{+}$ maps)
- continuum bandwidth: One baseband for continuum: 976 kHz channels, 1875 MHz total bandwidth  
  > "One baseband was used for continuum observations where the spectral resolution was set to 976 kHz and the total bandwidth was 1875 MHz." (Observations and Data Analysis)
- arrays: ALMA 12m dishes  
  > "The primary beam of the ALMA 12m dishes covers a field of $\sim$30 arcsec in diameter." (Observations and Data Analysis)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.4 arcsec; synthesized beam 0.47 x 0.38 arcsec  
  > "Our chosen configuration was a maximum recoverable scale of $\sim$4 arcsec, and an angular resolution of $\sim$0.4 arcsec." (Observations and Data Analysis); "The synthesized beam size of the observations is 0.47$^{\prime\prime} \times$0.38$^{\prime\prime}$." (Observations and Data Analysis)
- max recoverable scale: ~4 arcsec  
  > "Our chosen configuration was a maximum recoverable scale of $\sim$4 arcsec, and an angular resolution of $\sim$0.4 arcsec." (Observations and Data Analysis)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Cycle 8, September 2022  
  > "The observations were obtained in Cycle 8 (PID: 2021.1.00134.S) in September, 2022." (Observations and Data Analysis)
- pi or archival as stated: _not stated_
- Line: HCN J=3-2 (hyperfine components A, B, C) (265.8865 GHz)
- Line: HCO+ J=3-2 (not stated)
- Other facility **IRAM 30m**: Earlier single-dish molecular line surveys finding Ser-emb 16 chemically rich, with strong HCN (3-2) hyperfine emission  
  > "Previous single-dish IRAM 30m molecular line surveys have identified Ser-emb 16 to be chemically rich" (Introduction); "with strong emission in the HCN (3-2) hyperfine lines (Riaz et al. 2018)." (Introduction)
- External data: Distance to Ser-emb 16 / Serpens, d = 440 +/- 9 pc  
  > "located in the Serpens region ($d$=440$\pm$9 pc) (Ortiz-León et al. 2017; Gong et al. 2021)." (Introduction) [from Ortiz-León et al. 2017; Gong et al. 2021]
- External data: Bolometric luminosity 0.06 +/- 0.01 Lsun and total (dust+gas) mass ~28 MJup of Ser-emb 16  
  > "The bolometric luminosity for Ser-emb 16 is 0.06$\pm$0.01 L$_{\odot}$ and the total (dust+gas) mass (central object mass and circumstellar material) is $\sim$28 M$_{Jup}$ (Riaz et al. 2024)" (Introduction) [from Riaz et al. 2024]
- External data: Systemic velocity V_lsr ~8.0 km/s  
  > "With respect to the V$_{lsr}\sim$8.0 km s$^{-1}$ for Ser-emb 16 (Riaz et al. 2024)" (Kinematics) [from Riaz et al. 2024]
- Simulation/model as data: MHD simulations of magnetized rotating clouds (Machida, Hirano & Kitta 2020), with rotation axis misaligned with the global magnetic field by 0-90 deg, modified as in Riaz et al. 2024; used as physical input to the radiative transfer model  
  > "We consider the magnetohydrodynamical simulations presented in Machida, Hirano, & Kitta (2020) of magnetized rotating clouds" (Line radiative transfer modelling); "We have modified the simulations of the Machida et al. (2020) model. The modifications are described in Riaz et al. (2024)." (Line radiative transfer modelling)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated data delivered by the EU-ARC were used  
  > "We employed the calibrated data delivered by the EU-ARC." (Observations and Data Analysis)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: uniform weighting  
  > "Data analysis was performed on the uniform-weighted synthesized images using the CASA software." (Observations and Data Analysis)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.47 x 0.38 arcsec  
  > "The synthesized beam size of the observations is 0.47$^{\prime\prime} \times$0.38$^{\prime\prime}$." (Observations and Data Analysis)
- final rms: _not stated_

### Inherited from earlier work

- ALMA continuum and HCO+ (3-2) results of the same data set are presented in Paper 1  
  > "Paper 1 (Riaz et al. 2024) presented the results in the ALMA continuum and HCO$^{+}$ (3-2) line." (Introduction) [from Riaz et al. 2024]
- Line radiative transfer modelling method  
  > "We conducted line radiative transfer modelling following the method described in detail in Riaz et al. (2019b)." (Line radiative transfer modelling) [from Riaz et al. (2019b)]
- Modifications to the Machida et al. (2020) simulations  
  > "We have modified the simulations of the Machida et al. (2020) model. The modifications are described in Riaz et al. (2024)." (Line radiative transfer modelling) [from Riaz et al. (2024)]
- Detailed modelling of the large-scale HCO+ spiral  
  > "A detailed modelling of the large-scale spiral structure seen in the HCO$^{+}$ (3-2) line is presented in Riaz et al. (2024)." (HCO$^{+}$ Modelling) [from Riaz et al. (2024)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration route (archive pipeline version, manual or not, flux/bandpass/phase calibrators, flux scale uncertainty)
- Array configuration name, baseline range and time on source
- Imaging task and parameters (tclean settings, cell size, image size, masking, number of iterations, threshold) and final image rms
- Continuum subtraction method and line-free channels used for HCN
- Source coordinates of Ser-emb 16
- uvmodelfit/imfit starting guesses, fit regions and the continuum size used to measure HCN line fluxes
- Moment map settings (velocity ranges per hyperfine component, clipping threshold) and the moment 8 intensity cut defining the bar vs spiral
- Method, excitation temperature and molecular data used to derive HCN column density, gas mass and H2 number density
- The modified Machida et al. (2020) simulation snapshot and the modifications themselves (Riaz et al. 2024), plus the Riaz et al. (2019b) MOLLIE set-up (grid, abundance profile functional form, line widths tested, number of models, reduced chi-square channel range)

## Analysis recipe

1. **Measure source size, position and fluxes by Gaussian fitting**: Fit one or more elliptical Gaussian components to continuum and HCN (3-2) images with uvmodelfit and imfit; continuum size used to measure HCN line fluxes  
  > "by fitting one or more elliptical Gaussian components on the continuum and HCN (3-2) line images." (Observations and Data Analysis); "The size of Ser-emb 16 measured in the continuum image was used to measure the HCN line fluxes." (Sizes, gas masses and densities)
   - software: CASA, uvmodelfit, imfit
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract the HCN (3-2) spectrum and measure hyperfine component ratios**: Collapse spectrum over all channels in a 3x3 arcsec area; compare B/A and C/A ratios with the optically thin LTE expectation (0.04)  
  > "the observed HCN (3-2) spectrum collapsed over all velocity channels and measured over an area of 3x3 arcsecond that covers the full spatial scale of the observed structures" (Anomalous hyperfine structure); "Under optically thin LTE conditions, the relative weightings of the HCN (3-2) hyperfine lines are 0.037:0.926:0.037." (Anomalous hyperfine structure)
   - parameter: Area 3x3 arcsec  
  > "measured over an area of 3x3 arcsecond that covers the full spatial scale of the observed structures" (Anomalous hyperfine structure)
   - assumption: LTE level populations proportional to statistical weights give B/A = C/A = 0.04  
  > "assuming that the level populations of the hyperfine states are in LTE and hence proportional to the statistical weights." (Anomalous hyperfine structure)
   - fitting: _not stated_
   - validation: Anomaly checked against radiative transfer model, which reproduces ratios of ~0.05 before abundance changes  
  > "The line radiative transfer model originally produces B/A and C/A hyperfine intensity ratios in HCN of $\sim$0.05, which is close to the LTE value of 0.04." (Line radiative transfer modelling)
3. **Make moment 0 and moment 8 maps and size the bar-like structure**: Moment 0 maps per hyperfine component; moment 8 map of HCN-A to isolate the peak; 2D Gaussian fit to the bar excluding the spiral  
  > "the moment 0 (integrated value of the spectrum) maps individually for the B ($\sim$4-6 km/s), A ($\sim$6.2-8.3 km/s), C ($\sim$8.3-10 km/s) hyperfine components" (Moment maps); "restricting the fit to a region excluding the filamentary (or spiral) structure." (Moment maps)
   - software: CASA, imfit
   - parameter: Moment 0 velocity ranges B ~4-6, A ~6.2-8.3, C ~8.3-10 km/s  
  > "maps individually for the B ($\sim$4-6 km/s), A ($\sim$6.2-8.3 km/s), C ($\sim$8.3-10 km/s) hyperfine components" (Moment maps)
   - parameter: Moment 8 intensity range selected near the peak of ~0.04 Jy/beam to show the bar  
  > "To highlight the bar-like feature, we selected a range in intensities close to the peak value of $\sim$0.04 Jy/beam." (Moment maps)
   - fitting: 2D Gaussian fit with imfit, restricted to exclude the spiral  
  > "This size was determined by performing a 2D Gaussian fit using the *imfit* task in CASA and restricting the fit to a region excluding the filamentary (or spiral) structure." (Moment maps)
   - validation: Bar/spiral distinction is made visually  
  > "The distinction between the spiral and bar features is made visually." (Moment maps)
4. **Search for rotation or velocity gradients with moment 9 and PVDs**: Moment 9 (velocity of the maximum of the spectrum) map; position-velocity diagram not constructed because of limited velocity resolution  
  > "the moment 9 map shows the velocity of the maximum value of the spectrum." (Kinematics); "This makes it difficult to constrain the position angle and build a position-velocity diagram (PVD) that can help probe the infall and/or Keplerian kinematics for the proto-brown dwarf and the spiral." (Kinematics)
   - assumption: Central object mass of 18 MJup  
  > "For a central object mass of 18 M$_{Jup}$ measured for Ser-emb 16, we may find evidence for Keplerian rotation if the velocity spread was $\sim$0.3 km s$^{-1}$ or larger." (Kinematics)
   - fitting: _not stated_
   - validation: _not stated_
5. **Model HCN with non-LTE 3D radiative transfer on the MHD simulation**: Use simulated density, temperature and velocity profiles as input to MOLLIE, convolve synthetic profiles with the ALMA beam, compare with the observed spectrum, then compare model moment maps with observed maps  
  > "The physical structure, i.e. the radial profiles of density, temperature, and velocity from the simulations is used as an input to the 3D non-LTE radiative transfer code MOLLIE (Keto et al. 2004)." (Line radiative transfer modelling); "Synthetic HCN line profiles convolved by the ALMA beam size are compared with the observed spectrum." (Line radiative transfer modelling)
   - software: MOLLIE
   - parameter: Varied: abundance profile, line width, inclination angle, angle between rotation axis and global magnetic field  
  > "from varying the abundance profile, the line width, the inclination angle of the system, and the angle between the rotation axis and the global magnetic field." (Line radiative transfer modelling)
   - parameter: Best fit: HCN abundance (1-2)e-8 relative to H2, misalignment 30 deg, inclination 60 deg  
  > "We find a model with the HCN molecular abundance relative to H$_{2}$ of (1-2)$\times$10$^{-8}$, an initial misalignment angle of 30$\ensuremath{^\circ}$, and an inclination angle of 60$\ensuremath{^\circ}$ provides the best-fit to the observed spectrum" (Line radiative transfer modelling)
   - assumption: MOLLIE accounts for HCN hyperfine splitting and relative optical depth effects  
  > "We note that MOLLIE will account for the splitting in the HCN hyperfine components and their relative optical depth effects" (Line radiative transfer modelling)
   - fitting: Reduced chi-square between synthetic and observed spectrum; lowest value taken as best fit; no sampler or priors stated  
  > "For each synthetic spectrum, a reduced-$\chi^{2}$ value is computed to determine the goodness of fit." (Line radiative transfer modelling)
   - validation: Model moment maps from the best fit, convolved by the beam, compared with observed maps; intensity scale and velocity range matched  
  > "From the best line model fit (lowest reduced-$\chi^{2}$ value), model moment maps convolved by the beamsize are produced and compared with the observed maps." (Line radiative transfer modelling); "we had matched the intensity scale and the range in velocities in the model with the observations." (Line radiative transfer modelling)
6. **Model HCO+ (3-2) near the source with the same model**: Same modified Machida et al. (2020) physical model as for HCN, fit to HCO+ close to the central source; edge-on model image used to locate emission regions  
  > "We used the same modified physical model by Machida et al. (2020) as used for the HCN data." (HCO$^{+}$ Modelling)
   - software: MOLLIE
   - fitting: _not stated_
   - validation: _not stated_
7. **Derive H2 gas masses and densities from HCN column density**: _not stated_
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data analysis on the uniform-weighted images; source size, position and flux fitting  
  > "Data analysis was performed on the uniform-weighted synthesized images using the CASA software." (Observations and Data Analysis)
- **uvmodelfit** : Fit elliptical Gaussian components to measure source size, peak position, position angle and line fluxes  
  > "to measure the source size, peak position, position angle, and the line fluxes by fitting one or more elliptical Gaussian components on the continuum and HCN (3-2) line images." (Observations and Data Analysis)
- **imfit** : 2D Gaussian fit to the bar-like peak emission region and flux measurements  
  > "restricting the fit to a region excluding the filamentary (or spiral) structure." (Moment maps)
- **MOLLIE** : 3D non-LTE line radiative transfer modelling of HCN and HCO+  
  > "the 3D non-LTE radiative transfer code MOLLIE (Keto et al. 2004)." (Line radiative transfer modelling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HCN-A peak main-beam temperature | 0.83 | not stated | K | 2 | the HCN-B and HCN-C components have an equal intensity of T$_{mb}$ = 0.16 K, and the HCN-A component is $\sim$5 times stronger with T$_{mb}$ = 0.83 K |
| HCN-B and HCN-C peak main-beam temperature | 0.16 | not stated | K | 2 | the HCN-B and HCN-C components have an equal intensity of T$_{mb}$ = 0.16 K |
| HCN hyperfine B/A and C/A ratios | ~0.2 | not stated | dimensionless | 2 | This implies B/A and C/A line ratios of $\sim$0.2. |
| Deconvolved size of HCN bar-like peak region | ~0.11 arcsec (~50 au), PA 58.8 deg | not stated | arcsec; au; deg | 3 | The size of this peak emission region deconvolved by the beam is $\sim$0.11$\ensuremath{''}$ ($\sim$50 au) with a PA of 58.8$\ensuremath{^\circ}$. |
| Offset of HCN-A peak from continuum peak | ~0.1 arcsec (~44 au) | not stated | arcsec; au | 3 | lies very close ($\sim$0.1$\ensuremath{''}$ or $\sim$44 au) to the continuum peak position. |
| Integrated HCN (3-2) flux of Ser-emb 16 | 37.88 | 5.3 | mJy | 1 | The integrated and peak HCN (3-2) flux for Ser-emb 16 is 37.88$\pm$5.3 mJy and 31.6$\pm$2.0 mJy beam$^{-1}$. |
| Peak HCN (3-2) flux of Ser-emb 16 | 31.6 | 2.0 | mJy/beam | 1 | The integrated and peak HCN (3-2) flux for Ser-emb 16 is 37.88$\pm$5.3 mJy and 31.6$\pm$2.0 mJy beam$^{-1}$. |
| H2 gas mass from HCN column density, Ser-emb 16 | 2.8 | 0.3 | MJup | 7 | The H$_{2}$ gas mass derived from the HCN column density is 2.8$\pm$0.3 M$_{Jup}$, and the H$_{2}$ gas number density is (1.2$\pm$0.2)$\times$10$^{7}$ cm$^{-3}$. |
| H2 gas number density, Ser-emb 16 | 1.2e7 | 0.2e7 | cm^-3 | 7 | The H$_{2}$ gas mass derived from the HCN column density is 2.8$\pm$0.3 M$_{Jup}$, and the H$_{2}$ gas number density is (1.2$\pm$0.2)$\times$10$^{7}$ cm$^{-3}$. |
| HCN spiral size (major x minor axis) and PA | 3.0 x 2.1 arcsec, PA 128.9 deg | 0.6 and 0.1 arcsec; 4.6 deg | arcsec; deg | 1 | The size of the spiral, both convolved and deconvolved with the beam, is 3.0$\ensuremath{''} \pm$0.6$\ensuremath{''}$ along the major axis and 2.1$\ensuremath{''} \pm$0.1$\ensuremath{''}$ along the minor axis, with a PA of 128.9$\ensuremath{^\circ}$$\pm$4.6$\ensuremath{^\circ}$. |
| Projected size of the HCN spiral | 1610 | 264 | au | 1 | The projected size of the spiral is 1610$\pm$264 au. |
| Integrated HCN (3-2) flux of the spiral | 23.4 | 3.2 | mJy | 1 | The integrated and peak HCN (3-2) flux for the spiral is 23.4$\pm$3.2 mJy and 23.1$\pm$2.7 mJy beam$^{-1}$. |
| Peak HCN (3-2) flux of the spiral | 23.1 | 2.7 | mJy/beam | 1 | The integrated and peak HCN (3-2) flux for the spiral is 23.4$\pm$3.2 mJy and 23.1$\pm$2.7 mJy beam$^{-1}$. |
| H2 gas mass from HCN column density, spiral | 12.2 | 0.5 | MJup | 7 | The H$_{2}$ gas mass derived from the HCN column density is 12.2$\pm$0.5 M$_{Jup}$, and the H$_{2}$ gas number density is (0.2$\pm$0.01)$\times$10$^{7}$ cm$^{-3}$. |
| H2 gas number density, spiral | 0.2e7 | 0.01e7 | cm^-3 | 7 | The H$_{2}$ gas mass derived from the HCN column density is 12.2$\pm$0.5 M$_{Jup}$, and the H$_{2}$ gas number density is (0.2$\pm$0.01)$\times$10$^{7}$ cm$^{-3}$. |
| Best-fit HCN abundance relative to H2 | (1-2)e-8 | not stated | dimensionless | 5 | We find a model with the HCN molecular abundance relative to H$_{2}$ of (1-2)$\times$10$^{-8}$, an initial misalignment angle of 30$\ensuremath{^\circ}$, and an inclination angle of 60$\ensuremath{^\circ}$ provides the best-fit to the observed spectrum |
| Best-fit initial misalignment angle | 30 | not stated | deg | 5 | We find a model with the HCN molecular abundance relative to H$_{2}$ of (1-2)$\times$10$^{-8}$, an initial misalignment angle of 30$\ensuremath{^\circ}$, and an inclination angle of 60$\ensuremath{^\circ}$ provides the best-fit to the observed spectrum |
| Best-fit inclination angle | 60 | not stated | deg | 5 | We find a model with the HCN molecular abundance relative to H$_{2}$ of (1-2)$\times$10$^{-8}$, an initial misalignment angle of 30$\ensuremath{^\circ}$, and an inclination angle of 60$\ensuremath{^\circ}$ provides the best-fit to the observed spectrum |
| HCN vs HCO+ peak offset from continuum position | HCN ~0.15 arcsec (~66 au); HCO+ ~0.4 arcsec (~176 au) | not stated | arcsec; au | 0 | the HCN emission peaks at an offset of $\sim$0.15$\ensuremath{''} \sim$66 au while HCO$^{+}$ peaks at an offset of $\sim$0.4$\ensuremath{''} \sim$176 au |
| Spatial extent near the source, HCO+ vs HCN | HCO+ ~167 au; HCN ~123 au | not stated | au | 0 | The HCO$^{+}$ is also more spatially extended, with a spatial extent of $\sim$167 au vs $\sim$123 au for HCN emission close to the central proto-brown dwarf source |
| HCO+ to HCN peak intensity ratio | ~2.6 | not stated | dimensionless | 0 | The HCO$^{+}$ peak intensity is $\sim$2.6 times higher than HCN. |
| Velocity range of the moment 9 emission | ~7-7.5 | not stated | km/s | 4 | does not show any clear velocity gradient with the distance (or radius) over the narrow velocity range of $\sim$7-7.5 km s$^{-1}$ |

## Qualitative findings

- HCN-A emission shows an extended spiral from the proto-brown dwarf position, with a compact bar-like peak close to the continuum peak  
  > "One is a flattened, compact, bar-like structure of size $\sim$50 au, and the other is a spatially extended spiral-shaped structure of size $\sim$1610 au." (Conclusions)
- HCN survives in the gas phase in the dense core center while HCO+ is centrally depleted  
  > "There is an enhancement in the HCN abundance towards the core center, which suggests that HCN can survive in the gas phase in the inner, dense regions of the proto-brown dwarf." (Line radiative transfer modelling); "In contrast, modelling of the HCO$^{+}$ (3-2) line emission indicates that it originates from the outer pseudo-disk/envelope region and is centrally depleted." (abstract)
- No streamer is seen in HCN, unlike HCO+  
  > "Interestingly, there is no streamer seen in the HCN (3-2) line map, unlike the impressive large-scale streamer seen in the HCO$^{+}$ (3-2) line" (Comparison of HCN and HCO$^{+}$ maps)

## Claim tuples

- H: HCN (3-2) can trace the inner Keplerian disk of a Class 0 proto-brown dwarf | E: Mapped HCN (3-2) at ~0.4 arcsec, fit the bar-like peak, and compared with non-LTE radiative transfer models of an MHD simulation | R: Compact bar-like peak of ~50 au near the continuum peak, reproduced by the model as the inner dense region; no velocity gradient found in moment 9 | F: Bar likely traces the inner disk, but Keplerian kinematics cannot be confirmed with the present velocity resolution | **partially**
- H: The HCN hyperfine line ratios deviate from optically thin LTE values | E: Measured B/A and C/A ratios from the collapsed spectrum and compared with the LTE value and with radiative transfer models including hyperfine splitting | R: B/A and C/A ~0.2 versus 0.04 in LTE; model initially gives ~0.05 | F: The hyperfine anomalies are real and likely reflect different hyperfine components tracing different physical regions, not one single effect | **supported**
- H: The extended spiral in HCN traces the pseudo-disk/envelope | E: Compared observed moment maps with the best-fit model moment maps | R: Model reproduces the spiral for a 30 deg misalignment and 60 deg inclination | F: The spiral traces a pseudo-disk twisted by core rotation | **supported**
- H: HCN and HCO+ probe different regions, with HCN surviving and HCO+ depleted at the core center | E: Modelled both lines with the same physical model and compared their moment 0 maps, peak offsets and spectra | R: HCN peaks ~66 au and HCO+ ~176 au from the continuum position; HCN abundance enhanced and HCO+ depleted toward the center in the models | F: HCN reveals small-scale structure in regions where HCO+ is depleted | **supported**

## Reasoning

- Why this data: Disks of <=10 au expected in brown dwarfs are hard to resolve, so a high-density tracer is used to probe the innermost regions  
  > "An alternative way is to use high-density molecular line tracers that can probe the innermost densest regions in compact, dense proto-brown dwarfs." (Introduction)
- Why this method: Moment 8 chosen over moment 0 to show where the spectral peak originates for the bar  
  > "we want to highlight the region of origin of the peak or maximum value of the spectrum, due to which moment 8 is preferred over moment 0 map." (Moment maps)
- Alternative: Moment 1 map not used for kinematics because no velocity gradient is seen, so moment 9 is shown instead  
  > "Since there is no velocity gradient seen within the spiral or bar structures, the moment 1 map does not show any velocity fields." (Kinematics)
- How they decided it was enough: _not stated_
- Limitation (authors): Limited velocity resolution prevents confirming Keplerian rotation or building a PVD  
  > "The non-detection of Keplerian rotation in the bar-like structure is thus mainly due to the limited velocity resolution of the observations." (Kinematics); "Thus, velocity dispersions of $<$0.6-0.8 km s$^{-1}$ cannot be resolved." (Kinematics)
- Limitation (authors): Bar and spiral are separated visually by an intensity cut  
  > "The distinction between the spiral and bar features is made visually." (Moment maps)
- Limitation (authors): HCN B and C components only barely detected, so the bar is not visible there  
  > "These fainter components are barely detected at a $\sim$3-$\sigma$ level compared to A that is detected at a $>$10-$\sigma$ level." (Moment maps)
- Caveat (inferred, ours): The bar-as-inner-disk interpretation rests on a modified MHD simulation and a model-by-eye comparison; no uncertainties on best-fit model parameters and no alternative physical models are tested
- Caveat (inferred, ours): Kinematics unconstrained: no rotation signature detected, so the Keplerian disk claim is not observationally confirmed
- Caveat (inferred, ours): Offset of the bar from the continuum peak (~44 au) and the 60 deg viewing angle are used to explain asymmetric emission without independent test
- Caveat (inferred, ours): Gas mass and density derivation (excitation temperature, HCN abundance, optical depth) is not described
- Caveat (inferred, ours): Single source, single data set, with bar and spiral separation done visually

## Reproducibility

- Data public (paper): Data available in the ALMA archive  
  > "The data underlying this article are available in the ALMA archives through the ALMA online database." (Data Availability)
- Products in archive: Calibrated data delivered by the EU-ARC were used  
  > "We employed the calibrated data delivered by the EU-ARC." (Observations and Data Analysis)
- Missing: Imaging parameters (tclean setup, cell and image size, masks, rms) and continuum subtraction
- Missing: Modified Machida et al. (2020) simulation snapshot and its modifications, which are in Riaz et al. (2024)
- Missing: MOLLIE model grid, abundance profile form and line widths explored
- Missing: Column density and gas mass derivation method
- Missing: Moment map clipping and the bar/spiral intensity cut
- Data volume (inferred): Likely a few GB of calibrated measurement set for a single Band 6 execution with one narrow 117 MHz line window plus continuum
- Score (inferred): 2/5, Scale 1-5. Observation details and archive code are given and data are public, but imaging, continuum subtraction, simulation modifications and radiative transfer set-up are deferred to other papers or not stated, and the core model comparison cannot be redone from this paper alone.
- Rediscovery candidate: no, The data are public and measured numbers are given, but the headline interpretation depends on a modified simulation and MOLLIE set-up that are not in this paper, and imaging settings are not stated.

## Links

- Method: Riaz et al. (2019b) (Describes the line radiative transfer modelling method followed here)
- Method: Keto et al. 2004 (MOLLIE 3D non-LTE radiative transfer code)
- Companion: Riaz et al. 2024 (Paper 1) (ALMA continuum and HCO+ (3-2) results for Ser-emb 16, and the modifications to the Machida et al. (2020) simulation)
- Related: IRAM 30m molecular line surveys of Ser-emb 16 (Riaz et al. 2018; 2019a; 2022abc; 2023)

## Checks

```json
{
 "quotes": 103,
 "quotes_ok": 103,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 22,
 "numeric_problems": 0,
 "fill": {
  "facts": 92,
  "stated": 56,
  "rate": 0.609
 },
 "evidence_ok": true
}
```
