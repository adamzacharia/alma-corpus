# The properties and kinematics of HCN emission across the closest starburst galaxy NGC 253 observed with ALMA

`2024A&A...689A.122B` | Astronomy and Astrophysics 2024 | first author: Bešlić, I. | arXiv: 2403.13751 | DOI: 10.1051/0004-6361/202347568

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: How dense gas traced by HCN(1-0) is distributed and moves across NGC 253 relative to CO(2-1), how the HCN/CO(2-1) ratio varies by environment, and how the dense-gas star formation efficiency depends on environment and velocity dispersion  
  > "We aim to study the properties of molecular gas, the contrast in intensity between two tracers that probe different density regimes" (abstract); "What is the kinematics of the HCN-tracing gas, and how does it compare with the CO emission" (Introduction)
- Target **NGC 253 (Sculptor galaxy)**: coordinates RA 00h47m33s, Dec -25d17m19s (J2000, galaxy center)  
  > "00h47m33s" (Table 1); "-25d17m19s" (Table 1); "(b) Distance from (cite: anand_2020)." (Table 1); z/distance 3.7 Mpc  
  > "00h47m33s" (Table 1); "-25d17m19s" (Table 1); "(b) Distance from (cite: anand_2020)." (Table 1); distance from Anand et al. 2020 (cite: anand_2020)  
  > "00h47m33s" (Table 1); "-25d17m19s" (Table 1); "(b) Distance from (cite: anand_2020)." (Table 1)

## Data provenance

- ALMA projects: 2019.2.00236.S, 2018.1.01321.S
- bands: Band 3 (84 – 116 GHz)  
  > "Band 3 (84 – 116 GHz)" (2.1 ALMA+ACA observations)
- frequencies and spectral setup: 4 spectral windows, ~1.8 GHz wide, 0.4 MHz resolution; HCN(1-0) in spw2  
  > "The spectral setup consisted of 4 spectral windows with $\sim1.8$ GHz width and 0.4 MHz resolution" (2.1 ALMA+ACA observations); "we focus on the HCN(1–0) line covered by spectral window 2" (2.1 ALMA+ACA observations)
- continuum bandwidth: _not stated_
- arrays: ACA 7m array plus Total Power (TP) antennas  
  > "We observe molecular line emission using the Atacama Compact Array (7m - ACA), which included the Total Power (TP) array in Band 3 (84 – 116 GHz)" (2.1 ALMA+ACA observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: native beam 21.40 x 10.36 arcsec, PA 83.5 deg; final cube convolved to circular 22 arcsec (~370 pc)  
  > "The beam size is $21.40$$^{\prime\prime}$$\times10.36\,$$^{\prime\prime}$, and the beam position angle is 83.5 degrees." (2.1 ALMA+ACA observations); "The final data cube is additionally primary beam corrected and convolved to have a circular beam size of 22 $^{\prime\prime}$($\sim$370 pc) and channel width of 10 $\, \ensuremath{\mathrm{km\,s^{-1}}}$." (2.1 ALMA+ACA observations)
- max recoverable scale: interferometer sensitive from ~14 arcsec (~240 pc); largest scale from TP ~100 arcsec (~1.7 kpc)  
  > "Our interferometric observations are sensitive to the emission from angular scales of $\sim$14 $^{\prime\prime}$($\sim$240 pc) to the largest angular scale obtained by the TP of $\sim$100 $^{\prime\prime}$($\sim$1.7 kpc)." (2.1 ALMA+ACA observations)
- sensitivity: ~2.5 mK (7.6 mJy/beam) at 22 arcsec and 10 km/s  
  > "The obtained sensitivity is $\sim$2.5 mK (7.6 mJy/beam)" (2.1 ALMA+ACA observations)
- time on source: 22.9 h (7m array) and 44.1 h (TP) total observing time  
  > "The total observing time is 22.9 and 44.1 hours for the 7 meter array and the TP antennas, respectively." (2.1 ALMA+ACA observations)
- observing dates: December 2019 and January 2020 (ALMA Cycle 7)  
  > "were obtained in December 2019 and January 2020" (2.1 ALMA+ACA observations)
- pi or archival as stated: HCN: new Cycle 7 observations (2019.2.00236.S); CO(2-1): ancillary PHANGS-ALMA data, PI C. Faesi (2018.1.01321.S)  
  > "We present new ALMA Atacama Compact Array and Total Power (ACA+TP) observations of the HCN emission across NGC 253." (abstract); "(PI: C. Faesi, 2018.1.01321.S), included in the PHANGS-ALMA survey" (2.3 ALMA-CO(2–1) observations from PHANGS)
- Line: HCN J=1-0 (not stated)
- Line: CO J=2-1 (not stated)
- Other facility **PHANGS-ALMA (ACA+TP CO(2-1))**: CO(2-1) ACA+TP cube at 8 arcsec, 2.5 km/s channels, used for masks, Sigma_mol and HCN/CO ratios  
  > "The angular resolution of these data is 8 $^{\prime\prime}$, and the channel width is 2.5 km s$^{-1}$." (2.3 ALMA-CO(2–1) observations from PHANGS)
- Other facility **Herschel (KINGFISH)**: 70, 160 and 250 micron IR maps used for Sigma_TIR and Sigma_SFR  
  > "we use a combination of IR Herschel data from the KINGFISH (Key Insights on Nearby Galaxies: a Far-Infrared Survey with Herschel) survey (cite: kennicutt_2011)" (2.4 Star formation rate)
- External data: Environmental masks (disk, ring, bar, center) for NGC 253  
  > "we use environmental masks defined for this galaxy based on infrared data (cite: querejeta_2021)" (2.2 Environmental masks) [from (cite: querejeta_2021)]
- External data: CO(2-1) ACA+TP cube from PHANGS-ALMA  
  > "included in the PHANGS-ALMA survey (cite: leroy_2021b; faesi_2023)" (2.3 ALMA-CO(2–1) observations from PHANGS) [from (cite: leroy_2021b; faesi_2023)]
- External data: Metallicity-dependent alpha_CO (4.2 at the centre to 20 at the outskirts)  
  > "is the metallicity-dependent conversion factor taken from (cite: sun_2020b)" (2.3 ALMA-CO(2–1) observations from PHANGS) [from (cite: sun_2020b)]
- External data: Scaling relation R21 proportional to Sigma_SFR^0.15  
  > "In this work, we use the scaling relation: $R_{21}\propto \Sigma_\mathrm{SFR}^{0.15}$ (cite: sun_2023)." (2.3 ALMA-CO(2–1) observations from PHANGS) [from (cite: sun_2023)]
- External data: Coefficients c_j for total infrared surface density from 70, 160, 250 micron  
  > "taken from (cite: galametz_2013)." (Table 2) [from (cite: galametz_2013)]
- External data: Herschel convolution kernels to 22 arcsec  
  > "using the kernels defined in (cite: aniano_2011)" (2.4 Star formation rate) [from (cite: aniano_2011)]
- External data: NGC 253 distance 3.7 Mpc  
  > "(b) Distance from (cite: anand_2020)." (Table 1) [from (cite: anand_2020)]
- External data: Systemic velocity 258 km/s  
  > "(d) Systemic velocity from (cite: casasola_2011)." (Table 1) [from (cite: casasola_2011)]
- External data: Inclination 76+-6 deg and position angle 52 deg  
  > "(a) (cite: hlavacek-larrondo_2011)." (Table 1) [from (cite: hlavacek-larrondo_2011)]
- External data: Outflow velocity of -43 km/s and HCN/CO(1-0) of ~0.1 in the outflow  
  > "consisted with the value for the outflow, $\upsilon=-43$ km s$^{-1}$ (cite: walter_2017)" (6.1 Enhancement of the HCN/CO(2–1) ratio in the inner 2 kpc of NGC 253) [from (cite: walter_2017)]
- External data: Mean R21 of 0.8 measured in NGC 253  
  > "we use a mean $R_{21}$ ratio of 0.8 measured in NGC 253 (cite: zschaechner_2018)" (6.1 Enhancement of the HCN/CO(2–1) ratio in the inner 2 kpc of NGC 253) [from (cite: zschaechner_2018)]
- External data: Molecular and dense-gas surface density thresholds (~10 and ~200 Msun/pc^2)  
  > "Dashed vertical lines in both panels show the gas surface density thresholds presented in (cite: bigiel_2008)." (5.1 Environmental dependence of the star formation efficiency of the dense gas) [from (cite: bigiel_2008)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 6.5  
  > "The raw data calibration is done in Common Astronomy Software Applications (CASA - (cite: mcmullin_2007)), version 6.5" (2.1 ALMA+ACA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean for the 7m data; feather for 7m+TP combination  
  > "The 7m data was imaged using CASA’s standard TCLEAN procedure." (2.1 ALMA+ACA observations); "we combine 7m observations with TP for the missing short-scale emission using the standard CASA task *feather*." (2.1 ALMA+ACA observations)
- deconvolver: single-scale clean  
  > "which is then combined with the single-scale clean during the imaging" (2.1 ALMA+ACA observations)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: CO(2-1)-based clean mask used as initial mask  
  > "We use the CO(2–1)-based clean mask (cite: leroy_2021a; leroy_2021b) as the initial clean mask for our imaging" (2.1 ALMA+ACA observations)
- multiscale scales: _not stated_
- continuum subtraction: emission lines flagged in each band, continuum calculated and subtracted  
  > "Firstly, we flag all the emission lines within each band to calculate and subtract the continuum emission." (2.1 ALMA+ACA observations)
- line free channels: _not stated_
- primary beam correction: applied to final cube  
  > "The final data cube is additionally primary beam corrected" (2.1 ALMA+ACA observations)
- array combination: 7m + TP combined with CASA feather; interferometric flux is 70% of single-dish flux  
  > "we combine 7m observations with TP for the missing short-scale emission using the standard CASA task *feather*." (2.1 ALMA+ACA observations); "The total flux from the interferometric data is $70\%$ of the total flux measured from the single-dish data." (2.1 ALMA+ACA observations)
- smoothing: convolved to circular 22 arcsec beam and 10 km/s channels  
  > "The final data cube is additionally primary beam corrected and convolved to have a circular beam size of 22 $^{\prime\prime}$($\sim$370 pc) and channel width of 10 $\, \ensuremath{\mathrm{km\,s^{-1}}}$." (2.1 ALMA+ACA observations)
- final beam: circular 22 arcsec (~370 pc)  
  > "convolved to have a circular beam size of 22 $^{\prime\prime}$($\sim$370 pc)" (2.1 ALMA+ACA observations)
- final rms: _not stated_

### Inherited from earlier work

- Imaging, post-processing and short-spacing correction with the PHANGS-ALMA pipeline  
  > "including short-spacing correction using the PHANGS-ALMA processing pipeline (cite: leroy_2021a)" (2.1 ALMA+ACA observations) [from (cite: leroy_2021a)]
- Total power data processing  
  > "The single-dish data are also processed using the PHANGS-ALMA total power processing pipeline (cite: herrera_2020)" (2.1 ALMA+ACA observations) [from (cite: herrera_2020), (cite: leroy_2021a)]
- CO(2-1)-based clean mask  
  > "We use the CO(2–1)-based clean mask (cite: leroy_2021a; leroy_2021b) as the initial clean mask for our imaging" (2.1 ALMA+ACA observations) [from (cite: leroy_2021a; leroy_2021b)]
- Spectral decomposition algorithm SCOUSE  
  > "We use a Semi-automated multi-COmponent Universal Spectral-line fitting Engine (cite: henshaw_2016a; henshaw_2019)" (4 Decomposed HCN emission) [from (cite: henshaw_2016a; henshaw_2019)]
- Sigma_TIR prescription and Sigma_SFR calibration  
  > "We calculate the total infrared surface density ($\Sigma_\mathrm{TIR}$) following the prescription from (cite: galametz_2013):" (2.4 Star formation rate) [from (cite: galametz_2013)]
- Use of Herschel 70, 160, 250 micron bands for direct comparison with earlier work  
  > "To compare our results with recent similar studies (cite: jimenez19)" (2.4 Star formation rate) [from (cite: jimenez19)]

### Not stated but needed to reproduce (our reading)

- tclean parameters: weighting/robust, cell size, image size, niter and threshold, number of Hanning/channel settings, deconvolver settings beyond 'single-scale'
- Line-free channel ranges used for continuum subtraction and the CASA pipeline/manual calibration details and calibrators
- PHANGS-ALMA pipeline version and configuration, feather scaling factor for the TP data and TP-to-Jy/K conversion
- Noise estimate method and per-pixel uncertainties on integrated intensities used for the ratio error propagation
- SCOUSE settings: S/N threshold, tolerances, maximum components, fit-acceptance criteria and how manual fits were chosen
- S/N cut used to include lines of sight in radial profiles, violin plots and SFE plots; hexagonal grid construction details
- Spiral-arm mask construction parameters (fit coefficients, manually defined widths in ds9)
- Rest frequencies used for HCN(1-0) and CO(2-1) and the velocity convention
- How alpha_CO map was built per pixel from the metallicity-dependent prescription, and which Sigma_SFR map was used in R21
- The PHANGS CO(2-1) cube is cited as in prep (Faesi), so its processing is not fully documented

## Analysis recipe

1. **Calibrate, image and combine ACA 7m and TP HCN data**: CASA calibration; lines flagged and continuum subtracted; 7m imaged with tclean using a CO(2-1)-based clean mask; combined with TP via feather inside the PHANGS-ALMA pipeline; primary beam corrected and convolved to 22 arcsec and 10 km/s  
  > "The raw data calibration is done in Common Astronomy Software Applications (CASA - (cite: mcmullin_2007)), version 6.5" (2.1 ALMA+ACA observations); "The 7m data was imaged using CASA’s standard TCLEAN procedure." (2.1 ALMA+ACA observations); "we combine 7m observations with TP for the missing short-scale emission using the standard CASA task *feather*." (2.1 ALMA+ACA observations)
   - software: CASA, tclean, feather, PHANGS-ALMA pipeline
   - parameter: final circular beam 22 arcsec, channel width 10 km/s  
  > "convolved to have a circular beam size of 22 $^{\prime\prime}$($\sim$370 pc) and channel width of 10 $\, \ensuremath{\mathrm{km\,s^{-1}}}$." (2.1 ALMA+ACA observations)
   - fitting: _not stated_
   - validation: 7m HCN flux in the clean mask is 99% of the full-image flux; interferometric flux is 70% of single-dish flux  
  > "The HCN 7m flux within the cleaning mask is 99$\%$ of the total flux within the full image." (2.1 ALMA+ACA observations); "The total flux from the interferometric data is $70\%$ of the total flux measured from the single-dish data." (2.1 ALMA+ACA observations)
2. **Make moment maps of HCN and CO(2-1)**: CO(2-1)-based mask applied to both cubes; moment 0, 1, 2 computed with SpectralCube  
  > "This mask is produced by selecting all voxels with a signal-to-noise ratio higher than 4 and then expanding it to include all contiguous voxels with signal-to-noise $>2\sigma$ level." (2.5 Moment maps); "Next, we apply this mask to the HCN and CO(2–1) data cubes." (2.5 Moment maps)
   - software: SpectralCube
   - parameter: mask seed S/N > 4, expanded to contiguous voxels with S/N > 2  
  > "selecting all voxels with a signal-to-noise ratio higher than 4 and then expanding it to include all contiguous voxels with signal-to-noise $>2\sigma$ level" (2.5 Moment maps)
   - parameter: moment 1 corrected for systemic velocity (258 km/s)  
  > "The velocity map is corrected for the systemic velocity" (2.5 Moment maps)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure radial HCN intensity and HCN/CO(2-1) ratio by environment**: Resample maps on a hexagonal half-beam-spaced grid; radial profiles of HCN integrated intensity; HCN/CO(2-1) ratio with propagated errors; sight lines split by environmental mask  
  > "we resample the HCN map on a hexagonal grid where adjacent pixels are half-beam spaced" (3.1 Radial distribution of the line of sight HCN intensity); "The uncertainty of the HCN/CO(2–1) ratio is computed from the uncertainties of their integrated intensities, using the standard error propagation technique" (3.2 Line of sight HCN/CO(2–1) intensity ratio)
   - software: SpectralCube
   - assumption: axisymmetric distribution for deprojected radii, inclination 76+-6 deg  
  > "assuming an axisymmetric distribution" (3.1 Radial distribution of the line of sight HCN intensity); "76$\pm$6" (Table 1)
   - fitting: _not stated_
   - validation: compared with HCN and CO trends in earlier galaxies and CO(1-0) of NGC 253  
  > "The HCN intensity distribution in NGC 253 follows the CO(1–0) distribution described in (cite: sorai_2000; paglione_2004)" (3.1 Radial distribution of the line of sight HCN intensity)
4. **Derive star formation rate surface density from Herschel**: Convolve Herschel 70, 160, 250 micron maps to 22 arcsec, compute Sigma_TIR as a weighted sum of bands, convert to Sigma_SFR with inclination correction  
  > "we choose to calculate $\Sigma_\mathrm{SFR}$ using Herschel bands at $\lambda=$70, 160, and 250 microns." (2.4 Star formation rate); "using the kernels defined in (cite: aniano_2011) and match the coordinate grid with the final HCN data image" (2.4 Star formation rate)
   - parameter: c_j = 1.018, 1.068, 0.402 for 70, 160, 250 micron  
  > "taken from (cite: galametz_2013)." (Table 2)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compute molecular surface density and dense gas mass**: Sigma_mol from CO(2-1) with metallicity-dependent alpha_CO and R21 scaling with Sigma_SFR; M_dense from HCN luminosity with constant X_HCN; both with cos(i) correction  
  > "is the metallicity-dependent conversion factor taken from (cite: sun_2020b)" (2.3 ALMA-CO(2–1) observations from PHANGS); "we compute the dense gas mass, $M_\mathrm{dense}$, assuming a constant $X_\mathrm{HCN} = 10\,[\mathrm{M_{\odot}\,(\mathrm{K\,km\,s^{-1}\,pc^2})^{-1}] }$ conversion factor (cite: gao_2004a)" (2.1 ALMA+ACA observations)
   - parameter: alpha_CO from 4.2 (centre) to 20 (outskirts)  
  > "has a range from 4.2 (at the centre) to 20" (2.3 ALMA-CO(2–1) observations from PHANGS)
   - parameter: R21 scales as Sigma_SFR^0.15  
  > "In this work, we use the scaling relation: $R_{21}\propto \Sigma_\mathrm{SFR}^{0.15}$ (cite: sun_2023)." (2.3 ALMA-CO(2–1) observations from PHANGS)
   - assumption: constant X_HCN = 10 Msun (K km/s pc^2)^-1 (Gao & Solomon 2004)  
  > "assuming a constant $X_\mathrm{HCN} = 10\,[\mathrm{M_{\odot}\,(\mathrm{K\,km\,s^{-1}\,pc^2})^{-1}] }$ conversion factor (cite: gao_2004a)" (2.1 ALMA+ACA observations)
   - fitting: _not stated_
   - validation: _not stated_
6. **Decompose HCN and CO(2-1) spectra into Gaussian components**: SCOUSE: spectra averaged over spectral averaging areas of 4 pixels, fitted with Gaussians, solutions propagated to individual pixels with user checks  
  > "In our case, each SAA contains 4 pixels." (10 Spectral decomposition using SCOUSE); "SCOUSE fits each SAA’s spectrum and suggests a model solution assuming the Gaussian line profile." (10 Spectral decomposition using SCOUSE)
   - software: SCOUSE
   - parameter: each SAA contains 4 pixels  
  > "In our case, each SAA contains 4 pixels." (10 Spectral decomposition using SCOUSE)
   - assumption: Gaussian line profiles  
  > "assuming the Gaussian line profile" (10 Spectral decomposition using SCOUSE)
   - fitting: Gaussian component fits (amplitude, centroid velocity, line width); sampler, priors and likelihood not stated  
  > "describes such lines using Gaussian fitting" (10 Spectral decomposition using SCOUSE)
   - validation: user inspects SCOUSE model solutions per pixel and can adjust components and parameters  
  > "In the third phase, the user checks the SCOUSE’s model solutions for each pixel." (10 Spectral decomposition using SCOUSE)
7. **Match HCN components to CO(2-1) components**: HCN component associated with a CO(2-1) component when centroid velocities differ by less than the mean of the two velocity dispersions; ratio computed component by component  
  > "we consider that the HCN line is associated with the CO(2–1) if:" (4.1 Decomposed HCN/CO(2–1) line intensity ratio); "Such a criterion assures us that clouds with higher line widths have a less strict association criterion." (4.1 Decomposed HCN/CO(2–1) line intensity ratio)
   - parameter: when two components have similar centroid velocities, take the one with higher T_peak  
  > "In exceptional cases, when two components have similar centroid velocities, we take the one with higher amplitude, i.e., the $T_\mathrm{peak}$." (4.1 Decomposed HCN/CO(2–1) line intensity ratio)
   - fitting: _not stated_
   - validation: compared component-by-component ratio with line-of-sight ratio from moment 0 maps  
  > "By comparing the distributions of HCN/CO(2–1) computed from SCOUSE with those presented in Section [3.2](#sec:los_hcn-co)" (4.1 Decomposed HCN/CO(2–1) line intensity ratio)
8. **Relate dense-gas SFE to surface density and velocity dispersion**: Plot TIR/HCN luminosity (L_IR/M_dense) against Sigma_mol with binned trends (16th/84th percentiles), and against SCOUSE HCN velocity dispersion, by environment  
  > "we show the TIR/HCN luminosity (TIR/$M_\mathrm{dense}$ on the right y-axis) ratio as a function of the molecular gas surface density." (5.1 Environmental dependence of the star formation efficiency of the dense gas); "The blue-shaded region corresponds to binned trends and their respective range of 16th and 84th percentiles." (5.1 Environmental dependence of the star formation efficiency of the dense gas)
   - assumption: constant X_HCN, alpha_CO and R21 prescriptions of earlier steps  
  > "When $X_\mathrm{HCN}$ varies, the relation between HCN luminosity and dense gas mass becomes non-linear" (5.1 Environmental dependence of the star formation efficiency of the dense gas)
   - fitting: _not stated_
   - validation: compared with HCN studies of other galaxies (Figure 14)  
  > "In Figure [14](#fig:gs), we summarize previous HCN surveys and studies" (6.3 Star formation efficiency)

## Software

- **CASA** 6.5: calibration, tclean imaging of 7m data, feather combination with TP  
  > "The raw data calibration is done in Common Astronomy Software Applications (CASA - (cite: mcmullin_2007)), version 6.5" (2.1 ALMA+ACA observations)
- **tclean** : imaging of the 7m data  
  > "The 7m data was imaged using CASA’s standard TCLEAN procedure." (2.1 ALMA+ACA observations)
- **feather** : combining 7m and TP data  
  > "we combine 7m observations with TP for the missing short-scale emission using the standard CASA task *feather*." (2.1 ALMA+ACA observations)
- **PHANGS-ALMA pipeline** : imaging, post-processing and short-spacing correction; total power processing  
  > "including short-spacing correction using the PHANGS-ALMA processing pipeline (cite: leroy_2021a)" (2.1 ALMA+ACA observations)
- **SCOUSE** : Gaussian spectral decomposition of HCN and CO(2-1) spectra  
  > "to decompose the observed emission into separate components along each line of sight" (4 Decomposed HCN emission)
- **SpectralCube** v0.4.4: moment maps from masked cubes  
  > "package SpectralCube (cite: spectral_cube)" (2.5 Moment maps); "radio-astro-tools/spectral-cube: v0.4.4" (References)
- **SAOImage ds9** : manual definition of spiral arm widths for the arm mask  
  > "The width of such constructed spiral arms is defined manually in the SAO-NASA ds9 software (cite: ds9)." (2.2 Environmental masks)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean HCN/CO(2-1) ratio in the center | 0.1197 | 0.0002 | dimensionless | 3 | have the highest mean of HCN/CO(2–1) of 0.1197$\pm$0.0002 |
| HCN/CO(2-1) range in the center | 0.1 to 0.13 | not stated | dimensionless | 3 | The highest values (from 0.1 to 0.13) of this line ratio are found within the center of NGC 253. |
| Radial extent of significant HCN emission | ~6.5 | not stated | kpc | 3 | We detect significant HCN emission up to $\sim6.5$ kpc. |
| Change in HCN/CO(2-1) over the inner 2 kpc (bar) | factor ~7 | not stated | dimensionless | 3 | we observe change by a factor of $\sim7$ in the inner 2 kpc |
| HCN/CO(1-0) of enhanced minor-axis sight lines (after R21 = 0.8) | 0.080 to 0.096 | not stated | dimensionless | 3 | correspond to values within the 0.080 to 0.096 range in HCN/CO(1–0) |
| Median velocity dispersion in the center (HCN and CO(2-1)) | 55 (HCN) and 65 (CO(2-1)) | not stated | km/s | 6 | The highest median in $\sigma$ is found within the center (55 km s$^{-1}$ and 65 km s$^{-1}$ for the HCN and CO(2–1)). |
| Median velocity dispersion in the bar (HCN and CO(2-1)) | 40 (HCN) and 30 (CO(2-1)) | not stated | km/s | 6 | within the bar, we find higher median values in HCN (40 km s$^{-1}$) than in CO(2–1)  emission (30 km s$^{-1}$) |
| Fraction of HCN components matched to CO(2-1) in the bar | 78% | not stated | percent | 7 | We matched $78\%$ of HCN emission to the CO(2–1) components within the bar. |
| Mean SFE_dense (intermediate vs high surface density) | ~500 (intermediate) and ~400 (high) | not stated | Lsun/Msun | 8 | The mean SFE$_\mathrm{dense}$  increases up to $\sim500\,\mathrm{L_{\odot}/M_{\odot}}$ in the intermediate density regime, while the high surface density part shows nearly constant SFE$_\mathrm{dense}$  of $\sim400\,\mathrm{L_{\odot}/M_{\odot}}$. |
| 7m HCN flux inside clean mask relative to full image | 99% | not stated | percent | 1 | The HCN 7m flux within the cleaning mask is 99$\%$ of the total flux within the full image. |
| Interferometric flux relative to single-dish flux | 70% | not stated | percent | 1 | The total flux from the interferometric data is $70\%$ of the total flux measured from the single-dish data. |

## Qualitative findings

- HCN spectra are mainly double or triple peaked in the center and bar, and narrow and single-peaked in the ring, spiral arms and disk  
  > "lines of sight from the central region and the bar have multiple line profiles, whereas spectra towards the ring structure, spiral arms, and the disk are mainly narrow and single-peaked" (4 Decomposed HCN emission)
- HCN lines are narrower than CO(2-1) lines, consistent with denser gas having smaller turbulent velocity dispersion  
  > "The HCN emission lines are narrower than the CO lines, as the data points typically lie below the diagonal line." (4.2 HCN velocity dispersion)
- The IR/HCN luminosity ratio decreases with increasing HCN velocity dispersion  
  > "The IR/HCN luminosity ratio decreases with increasing HCN velocity dispersion." (5.2 Star formation efficiency and velocity dispersion)

## Claim tuples

- H: How is dense gas distributed across the disk of NGC 253? | E: Radial profile of HCN integrated intensity on a hexagonal grid, split by environment | R: HCN is brightest in the center and drops by two orders of magnitude along the bar | F: Dense gas is strongly centrally concentrated, with weak variation in ring, arms and disk | **supported**
- H: Does the HCN spectral complexity depend on galactic environment? | E: SCOUSE Gaussian decomposition of HCN and CO(2-1) spectra by environment | R: Multiple components in center and bar; single narrow components elsewhere | F: Environment drives HCN spectral complexity and line widths | **supported**
- H: Does dense gas have lower velocity dispersion than bulk molecular gas? | E: Compare SCOUSE HCN and CO(2-1) velocity dispersions per line of sight | R: HCN lines typically narrower than CO(2-1) | F: HCN-tracing gas arises from smaller structures, in line with turbulence theory | **supported**
- H: Is the enhanced HCN/CO(2-1) ratio in the bar caused by a molecular outflow? | E: Inspect HCN spectra with SCOUSE components along the minor axis toward the SW outflow streamer and compare ratio with Walter et al. 2017 | R: A second HCN component near the literature outflow velocity; converted HCN/CO(1-0) of 0.080-0.096 | F: The outflow could explain the enhancement, though the outflow is not resolved and beam smearing is also invoked | **partially**
- H: Does the star formation efficiency of dense gas depend on environment? | E: TIR/HCN (L_IR/M_dense) versus Sigma_mol and HCN velocity dispersion by environment | R: Lines of sight with the highest HCN/CO(2-1) have the lowest IR/HCN | F: Processes regulating star formation vary with environment | **supported**

## Reasoning

- Why this data: Mapped region covers the brightest molecular gas and most star-forming parts of NGC 253  
  > "Thus, our observations cover the brightest regions in molecular gas and the most star-forming parts in NGC 253." (2.1 ALMA+ACA observations)
- Why this method: Spectral decomposition used to study gas structure along each line of sight by environment  
  > "To characterize the gas structure along each line of sight and its variation with the galactic environment, we study the spectra of the HCN emission in 5 different dynamical zones." (4 Decomposed HCN emission)
- Alternative: Higher-J HCN transitions could better probe dense gas mass in high-density regimes, left beyond the scope of this work  
  > "Alternatively, higher $J$ transitions of HCN can better probe dense gas mass relative to the average gas density in these regions." (5.1 Environmental dependence of the star formation efficiency of the dense gas)
- How they decided it was enough: _not stated_
- Limitation (authors): Spatial scales are not sufficient to resolve the outflow  
  > "It is worth noting that the spatial scales probed by our data are not sufficient to resolve the outflow." (6.1 Enhancement of the HCN/CO(2–1) ratio in the inner 2 kpc of NGC 253)
- Limitation (authors): Systemic rotation is not fully resolved, broadening observed lines  
  > "We note that, at the scales of our observations, the systemic rotation velocity is not fully resolved, which also broadens observed lines." (5.2 Star formation efficiency and velocity dispersion)
- Limitation (authors): No HCN information at low molecular surface densities  
  > "we do not have information about the HCN emission for molecular gas surface densities lower than a few" (5.1 Environmental dependence of the star formation efficiency of the dense gas)
- Limitation (authors): A non-constant X_HCN could introduce scatter in SFE_dense  
  > "When $X_\mathrm{HCN}$ varies, the relation between HCN luminosity and dense gas mass becomes non-linear" (5.1 Environmental dependence of the star formation efficiency of the dense gas)
- Caveat (inferred, ours): Abstract says SFE_dense is anticorrelated with Sigma_mol up to ~200 Msun/pc^2, but Section 5.1 says it rises up to ~100 and then decreases; the trend description is inconsistent
- Caveat (inferred, ours): Constant X_HCN and a single alpha_CO/R21 prescription drive M_dense and Sigma_mol; no sensitivity test shown
- Caveat (inferred, ours): Outflow interpretation rests on spectral components at 22 arcsec resolution and a literature outflow velocity; beam smearing is an equally supported explanation
- Caveat (inferred, ours): Coverage fractions of CO mass and SFR are quoted as 90%/85% in Section 2.1 and 95%/85% in the Summary
- Caveat (inferred, ours): Companion CO(2-1) cube is cited as in prep, so inputs are not fully documented

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: tclean imaging parameters, line-free channels and PHANGS pipeline version/config
- Missing: SCOUSE tolerances and manual-fit choices; S/N cuts for plotted sight lines
- Missing: Exact alpha_CO and Sigma_SFR maps and the PHANGS CO(2-1) cube processing (in prep)
- Missing: Environmental mask files and spiral-arm mask definition
- Data volume (inferred): Roughly 100-300 GB raw for the ACA 7m and TP execution blocks (project 2019.2.00236.S) plus the PHANGS ACA CO(2-1) data (2018.1.01321.S); product cubes are a few GB
- Score (inferred): 3/5, ALMA projects are named and the pipeline route (CASA 6.5, PHANGS pipeline, SCOUSE) is clear, but imaging parameters, SCOUSE settings and masks are not given, and numeric results are mostly stated in figures and ranges.
- Rediscovery candidate: no, Public status of the data is not stated in the paper and key imaging and SCOUSE parameters are missing, so the recipe is not complete enough to redo from the text alone.

## Links

- Method: (cite: leroy_2021a) (PHANGS-ALMA processing pipeline used for imaging and short-spacing correction)
- Method: (cite: herrera_2020) (PHANGS-ALMA total power processing)
- Method: (cite: henshaw_2016a; henshaw_2019) (SCOUSE spectral decomposition)
- Method: (cite: galametz_2013) (Sigma_TIR and Sigma_SFR prescription from Herschel bands)
- Companion: (cite: faesi_2023) (CO(2-1) ACA+TP data of NGC 253 used throughout (in prep))
- Companion: (cite: leroy_2021b) (PHANGS-ALMA survey paper)
- Companion: (cite: beslic_2021) (Earlier HCN study of NGC 3627 with similar methods)
- Companion: (cite: walter_2017) (NGC 253 outflow in CO(1-0) and HCN used for interpretation)
- Related: PHANGS-ALMA
- Related: EMPIRE
- Related: ALMOND
- Related: ALCHEMI
- Related: KINGFISH
- Related: S4G

## Checks

```json
{
 "quotes": 131,
 "quotes_ok": 131,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 114,
  "stated": 85,
  "rate": 0.746
 },
 "evidence_ok": true
}
```
