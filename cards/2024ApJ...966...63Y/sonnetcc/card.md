# The First Spatially Resolved Detection of <SUP>13</SUP>CN in a Protoplanetary Disk and Evidence for Complex Carbon Isotope Fractionation

`2024ApJ...966...63Y` | The Astrophysical Journal 2024 | first author: Yoshida, Tomohiro C. | arXiv: 2403.00626 | DOI: 10.3847/1538-4357/ad2fb4

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Detect 13CN in the TW Hya disk and measure the spatially resolved 12CN/13CN ratio to constrain carbon isotope fractionation in disks  
  > "we present a detection of the $\rm ^{13}CN$ $N=2-1$ hyperfine lines in the TW Hya disk with the Atacama Large Millimeter/submillimeter Array" (abstract); "For a clearer understanding of the isotopic link between disks and planets, it is important to measure the carbon isotope ratios in various species." (abstract)
- Target **TW Hya disk**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01375.S, 2018.A.00021.S, 2017.1.01199.S
- bands: _not stated_
- frequencies and spectral setup: 13CN N=2-1 in spectral window 1 of baseband 1, spectral resolution ~0.67 km/s (project 2016.1.01375.S)  
  > "The $\rm ^{13}CN$ $N=2-1$ lines were observed in the spectral window 1 of the baseband 1 with the spectral resolution of $\sim 0.67\ {\rm km\ s^{-1}}$" (Observations / 13CN)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15-704 m (13CN data, 2016.1.01375.S)  
  > "the baseline range was 15-704 m" (Observations / 13CN)
- angular resolution: All cubes convolved to a circular 0.5 arcsec FWHM beam, the smallest common resolution  
  > "convolved by an elliptical Gaussian to match the final beam to a circular Gaussian with an FWHM of $0.5\ensuremath{''}$" (Observations); "which is the smallest common resolution we can achieve" (Observations)
- max recoverable scale: _not stated_
- sensitivity: 13CN cube RMS 1.0 mJy (per channel, after beam matching)  
  > "The root mean square (RMS) noise level is estimated to be 1.0 mJy" (Observations / 13CN)
- time on source: 41 minutes per execution block (13CN data)  
  > "For both EBs, the integration time was 41 minutes" (Observations / 13CN)
- observing dates: 13CN: Nov. 19, 2016 (43 antennas) and Nov. 20, 2016 (42 antennas)  
  > "The first EB was observed on Nov.19, 2016 with 43 antennas, while the second EB was observed on Nov.20, 2016 with 42 antennas." (Observations / 13CN)
- pi or archival as stated: Archival ALMA data (PIs C. Rab, R. Teague, R. Loomis)  
  > "We analyzed ALMA archival observations of the" (Observations); "We also used the" (Observations / 12CN)
- Line: 13CN N=2-1 hyperfine lines (brightest J=5/2-3/2, F1=3-2, F=4-3) (217.467150 GHz (representative))
- Line: 12CN N=2-1 (226.874781 GHz (representative))
- Line: 12CN N=1-0 (113.490970 GHz (representative))
- Other facility **LAMDA database**: Spectroscopic and collisional data for the 12CN RADEX grids  
  > "We adopted publically available spectroscopic data (cite: klis95; thom68; kalu15) via the LAMDA database (cite: scho05)" (Analysis and Results / non-LTE modeling)
- Other facility **EMAA database**: LAMDA-format file for 13CN used in RADEX grids  
  > "we used the LAMDA format file in the EMAA database [^2] which is based on (cite: mull05) and (cite: flow15)." (Analysis and Results / non-LTE modeling)
- Other facility **CDMS database**: 13CN hyperfine line list (frequencies, A coefficients, g_u, E_up)  
  > "The data is taken from the CDMS database (cite: mull01; mull05; endr16)." (Table 2 notes)
- External data: Dust optical depth at each wavelength used in the three-layer model  
  > "are the dust optical depth at each wavelength taken from (cite: maci21)" (Analysis and Results / non-LTE modeling) [from Macias et al. 2021 (cite: maci21)]
- External data: Fiducial TW Hya disk model (gas surface density and scale height at r=60 au) used to convert n(H2) to altitude z/r  
  > "in the fiducial TW Hya disk model of (cite: cala21)" (Analysis and Results / Fitting Results) [from Calahan et al. 2021 (cite: cala21)]
- External data: Disk geometry and stellar mass used for the Keplerian mask and stacking (i=5.8 deg, PA=151.6 deg, M*=0.81 Msun, vsys=2.84 km/s)  
  > "following (cite: teag19)" (Observations / 13CN) [from Teague et al. 2019 (cite: teag19)]
- External data: LTE relative optical depth spectrum at T=40 K for the matched filter figure  
  > "a predicted relative optical depth spectrum at $T=40$ K suggested by (cite: teag20)" (Analysis and Results / matched filter) [from Teague & Loomis 2020 (cite: teag20)]
- Simulation/model as data: Fiducial TW Hya disk model of Calahan et al. used only to map derived n(H2) to altitude z/r  
  > "in the fiducial TW Hya disk model of (cite: cala21)" (Analysis and Results / Fitting Results)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline calibration via scriptForPI.py for 13CN; pipeline calibration also run for 12CN data, then self-calibration  
  > "For data reduction, we first executed the pipeline calibration by running `scriptForPI.py`." (Observations / 13CN); "After downloading the data and running the pipeline calibration" (Observations / 12CN)
- casa version: CASA modular 6.2.5 for reduction/imaging; pipeline calibration in the CASA version of the original publication (version not given)  
  > "Common Astronomy Software Applications (cite: mcmu07) modular version 6.2.5 with the exception of the pipeline calibration which was performed in the CASA version used for the original publication." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 13CN data: J1107-4449 flux calibrator; J1037-2934 gain calibrator; bandpass J1037-2934 (EB1) and J1107-4449 (EB2)  
  > "the quasar J1037-2934 was used as the gain calibrator while J1107-4449 was used as a flux calibrator." (Observations / 13CN); "As the bandpass calibrator, J1037-2934 and J1107-4449 were used for the first and second EBs, respectively." (Observations / 13CN)
- flux scale uncertainty: Absolute flux consistency checked via continuum SED; deviations small so flux-scale uncertainty neglected  
  > "Since these deviations are sufficiently small, we neglect the uncertainty on the absolute flux scaling in the following analysis." (Observations / 12CN)
- self calibration: 13CN: 5 phase rounds (EB duration, 1200 s, 600 s, 300 s, 100 s) + 1 amplitude round (EB duration). 12CN N=2-1: 6 phase rounds from EB duration down to 30 s + 1 amplitude round (EB duration); N=1-0 as in Teague & Loomis 2020  
  > "We performed five rounds of phase self-calibration with solution intervals of the duration of the EBs, 1200s, 600s, 300s, and 100s as well as one round of amplitude self-calibration with the duration of the EBs." (Observations / 13CN); "We performed six rounds of phase self-calibration to the combined data." (Observations / 12CN); "The solution interval is decreased from the duration of EBs to 30 seconds." (Observations / 12CN)

### Imaging

- task: tclean (CASA)  
  > "two SPWs that contain the $\rm ^{12}CN$ lines were CLEANed using `tclean`" (Observations / 12CN)
- deconvolver: _not stated_
- weighting robust: 13CN: robust 0.5 in text (Table 1 lists 0.0); 12CN N=2-1: robust 1.0; 12CN N=1-0: robust 0  
  > "robust parameter of 0.5" (Observations / 13CN); "and robust parameter of 1.0" (Observations / 12CN); "CLEANed with a robust parameter of 0" (Observations / 12CN)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian_mask script; i=5.8 deg, PA=151.6 deg, M*=0.81 Msun, vsys=2.84 km/s; outer radius 3.0 arcsec (13CN)  
  > "a Keplerian mask made with a Python script `Keplerian_mask` (cite: kepmask) was used assuming the disk inclination angle of $5.8^\circ$, position angle of $151.6^\circ$" (Observations / 13CN); "The outer radius of the mask was set to 3.0 arcsec to contain all emissions in the mask." (Observations / 13CN)
- multiscale scales: _not stated_
- continuum subtraction: Linear fit to line-free channels in visibility space with uvcontsub (13CN)  
  > "the continuum emission was subtracted by fitting a linear function to line-free channels on the visibility space using the `uvcontsub` task." (Observations / 13CN)
- line free channels: _not stated_
- primary beam correction: impbcor (13CN cube)  
  > "primary beam correction was applied with `impbcor`" (Observations / 13CN)
- array combination: 12CN N=2-1: short-baseline continuum imaged and self-calibrated first, then combined with longer-baseline EBs; one EB with deviant amplitude-vs-uv flagged  
  > "Then, the data was combined with the longer baseline EBs." (Observations / 12CN); "therefore, that EB is totally flagged" (Observations / 12CN)
- smoothing: imsmooth to a circular 0.5 arcsec Gaussian for all cubes and continuum images  
  > "convolved by an elliptical Gaussian to match the final beam to a circular Gaussian with an FWHM of $0.5\ensuremath{''}$ using the CASA tasks ` imsmooth`" (Observations); "re-convolved by a Gaussian that matches the final beam to the $0.5\ensuremath{''}$ circular Gaussian for consistency." (Observations / 12CN)
- final beam: 0.5 arcsec circular Gaussian  
  > "re-convolved by a Gaussian that matches the final beam to the $0.5\ensuremath{''}$ circular Gaussian for consistency." (Observations / 12CN)
- final rms: 13CN cube: 1.0 mJy, mean of first and last three line-free channels before primary beam correction  
  > "which is calculated by averaging the RMS value of the first and last three line-free channels of the image cube before primary beam correction" (Observations / 13CN); "The root mean square (RMS) noise level is estimated to be 1.0 mJy" (Observations / 13CN)

### Inherited from earlier work

- 12CN N=2-1 observation details and processing come from the original publication  
  > "Details about these observations are described in (cite: teag22)." (Observations / 12CN) [from Teague et al. 2022 (cite: teag22)]
- 12CN N=1-0 pipeline calibration and self-calibration done similarly to the earlier paper  
  > "We ran pipeline calibration and self-calibration in a similar way of (cite: teag20)" (Observations / 12CN) [from Teague & Loomis 2020 (cite: teag20)]
- Disk geometry and stellar mass adopted for the Keplerian mask  
  > "following (cite: teag19)" (Observations / 13CN) [from Teague et al. 2019 (cite: teag19)]
- Matched filter technique and VISIBLE script  
  > "we also ran the matched filter analysis (cite: loom18)" (Analysis and Results / matched filter) [from Loomis et al. 2018 (cite: loom18)]
- Line-overlap-tolerant molecular layer intensity formula  
  > "following (cite: hsie15)" (Analysis and Results / non-LTE modeling) [from Hsieh et al. 2015 (cite: hsie15)]
- Reason for non-LTE treatment: 12CN lines found not to be in LTE earlier  
  > "previously found that the $\rm ^{12}CN$ lines are not in LTE by comparing independently derived kinetic and excitation temperatures" (Analysis and Results / non-LTE modeling) [from Teague & Loomis 2020 (cite: teag20)]

### Not stated but needed to reproduce (our reading)

- tclean parameters: cell size, image size, deconvolver, niter, threshold, weighting for the continuum and line cubes (beyond robust and channel width)
- Which channels/frequencies were flagged as line emission for continuum imaging and which are the line-free channels for uvcontsub
- Exact self-calibration solution intervals for the 12CN N=1-0 data and intermediate solints for the 12CN N=2-1 data (six phase rounds, only first and last given)
- Which 12CN N=2-1 execution block was flagged
- Robust value for 13CN is 0.5 in text but 0.0 in Table 1; a reproducer must decide which
- CASA version used for the original pipeline calibration of each dataset
- Distance to TW Hya used to convert arcsec to au
- Disk centre positions from the 2D Gaussian fits and radial bin width/annulus spacing for gofish stacking
- Dust optical depth values tau_d and the continuum intensity I_c actually used at each radius
- MCMC initialisation, convergence diagnostics and how the 16/84 percentile uncertainties were propagated into the ratio
- How sigma_obs was derived per bin for the 12CN cubes after beam matching and correlated noise between oversampled channels
- Which hyperfine groups define the four SPWs (j=1-4) and the reference line used in each group for the velocity axis
- Primary beam correction details for the 12CN cubes

## Analysis recipe

1. **calibrate, self-calibrate and image archival cubes**: Pipeline calibration, phase+amplitude self-calibration on continuum, application to line SPWs, uvcontsub, tclean with Keplerian mask, imsmooth to 0.5 arcsec circular beam, impbcor  
  > "The solutions were applied to the SPW containing $\rm ^{13}CN$ $N=2-1$ lines without flagging lines" (Observations / 13CN); "The solutions of the self-calibration were applied to the spectral windows containing the $\rm ^{12}CN$ lines." (Observations / 12CN)
   - software: CASA, Keplerian_mask
   - parameter: 13CN cube channel spacing 0.34 km/s (half the velocity resolution), robust 0.5  
  > "imaged with a channel spacing of 0.34 $\rm km\ s^{-1}$ (half of the velocity resolution)" (Observations / 13CN); "robust parameter of 0.5" (Observations / 13CN)
   - parameter: 12CN N=2-1 cube channel width 0.1 km/s, robust 1.0  
  > "velocity channel width of $0.1\ {\rm km\ s^{-1}}$ and robust parameter of 1.0" (Observations / 12CN)
   - assumption: Keplerian mask geometry: i=5.8 deg, PA=151.6 deg, M*=0.81 Msun, vsys=2.84 km/s  
  > "a Keplerian mask made with a Python script `Keplerian_mask` (cite: kepmask) was used assuming the disk inclination angle of $5.8^\circ$, position angle of $151.6^\circ$" (Observations / 13CN)
   - fitting: _not stated_
   - validation: _not stated_
2. **check absolute flux consistency across datasets**: Continuum peak intensities at 0.5 arcsec resolution fitted with a power-law SED; deviations of the three datasets compared  
  > "We extracted a spectral energy distribution (SED) from the peak intensity of continuum images" (Observations / 12CN); "The SED can be well fitted by a power-law curve with an index of 2.13" (Observations / 12CN)
   - fitting: Power-law fit to continuum SED  
  > "The SED can be well fitted by a power-law curve with an index of 2.13" (Observations / 12CN)
   - validation: Index consistent with literature; deviations small so flux uncertainty neglected  
  > "Since these deviations are sufficiently small, we neglect the uncertainty on the absolute flux scaling in the following analysis." (Observations / 12CN)
3. **detect 13CN via moment maps and matched filter**: Stacked moment-zero maps of the three brightest hyperfine lines with the Keplerian mask; matched filter cross-correlating visibilities with a Keplerian-mask kernel  
  > "and then stacked each of these moment zero maps to maximize the signal-to-noise ratio." (Analysis and Results / matched filter); "The cross-correlation between the observed visibilities and filter kernel was calculated by a Python script `VISIBLE` (cite: loom18)." (Analysis and Results / matched filter)
   - software: CASA, VISIBLE
   - parameter: Filter-kernel mask outer radius 1.6 arcsec  
  > "but with a smaller outer radius of 1.6 arcsec just to contain the emission of the brightest line" (Analysis and Results / matched filter)
   - assumption: LTE relative optical depth spectrum at T=40 K overplotted for comparison  
  > "a predicted relative optical depth spectrum at $T=40$ K suggested by (cite: teag20)" (Analysis and Results / matched filter)
   - fitting: _not stated_
   - validation: Five hyperfine lines above 5 sigma in the matched-filter response; brightest line ~20 sigma  
  > "Five hyperfine lines are detected in a significance of $>5\sigma$" (Analysis and Results / matched filter)
4. **azimuthally stack spectra by radius**: Shift-and-stack of spectra assuming Keplerian rotation with gofish, using the CLEAN-mask geometry and disk centre from 2D Gaussian fit to continuum  
  > "the spectra at each position were azimuthally stacked assuming Keplerian rotation using the python package `gofish` (cite: teag16)." (Analysis and Results / non-LTE modeling); "We also specified the disk center position by fitting a 2D Gaussian to the corresponding continuum images." (Analysis and Results / non-LTE modeling)
   - software: gofish
   - parameter: Same geometry as for the CLEAN mask; disk outer radius 3.0 arcsec for the 13CN disk-integrated spectrum  
  > "We used the same disk geometric parameters as used for the CLEAN mask." (Analysis and Results / non-LTE modeling); "Here, we adopted the disk outer radius of 3.0 arcsec." (Analysis and Results / non-LTE modeling)
   - fitting: _not stated_
   - validation: Stable best-fit systemic velocities with radius indicate successful shift-and-stack  
  > "The stable systemic velocities as a function of radius verify that the shift-and-stack process was successful." (Fitting Results)
5. **build non-LTE RADEX grids**: 3D grids of Tk, column density and n(H2) giving peak optical depth and excitation temperature of each hyperfine line, via SpectralRadex  
  > "calculated in three-dimensional grids for each SPW by using a Python wrapper of the non-LTE radiative transfer code RADEX (cite: vand07)" (Analysis and Results / non-LTE modeling)
   - software: RADEX, SpectralRadex
   - parameter: 100 grid points per dimension; Tk linear, N and n(H2) logarithmic  
  > "The number of the grid is 100 along each dimension." (Analysis and Results / non-LTE modeling); "While $T_{\rm kin}$ is gridded linearly, $N$ and $n({\rm H_2})$ are sampled logarithmically." (Analysis and Results / non-LTE modeling)
   - parameter: Ranges: log10 n(H2) [6,12] cm^-3; log10 N [11,16] cm^-2; Tk [10,100] K  
  > "$[6, 12]$" (Table 1); "$[11, 16]$" (Table 1); "$[10, 100]$" (Table 1)
   - assumption: All lines share the same Tk and n(H2); line width equals thermal width  
  > "Here, we assumed that all lines share the same $T_k$ and $n({\rm H_2})$, and the line width is identical to the thermal width." (Analysis and Results / non-LTE modeling)
   - assumption: Background black body at 2.73 K  
  > "We also adopted the background emission of the black body radiation at 2.73 K." (Analysis and Results / non-LTE modeling)
   - assumption: Only collisions with para-H2 (rate coefficients available only for para-H2); ortho-H2 ignored  
  > "Note that the rate coefficients are available only for collision with para-$\rm H_2$, so we ignored ortho-$\rm H_2$ in our analysis." (Analysis and Results / non-LTE modeling)
   - fitting: _not stated_
   - validation: _not stated_
6. **fit synthetic spectra to stacked spectra with MCMC**: Three-layer model (molecules behind, dust at midplane, molecules in front) giving synthetic spectra convolved with Gaussian broadening, compared with stacked spectra at each radius  
  > "To derive the physical quantities, we generated synthetic spectra and compared them with the azimuthally stacked spectra." (Analysis and Results / non-LTE modeling); "Since we consider the three-layer (molecules in the backside, dust grains at the midplane, and molecules in the frontside) model along the line of sight" (Analysis and Results / non-LTE modeling)
   - software: emcee, SpectralRadex
   - parameter: Nine free parameters per radius: n(H2), Tk, N(12CN), N(13CN), vsys, and Delta v_j for four SPWs  
  > "we have nine free parameters at each radius" (Analysis and Results / non-LTE modeling)
   - parameter: Model spectrum generated with a 15 kHz interval  
  > "The model spectrum $I_{\rm mod}(v)$ is generated with a $15$ kHz interval" (Analysis and Results / non-LTE modeling)
   - parameter: 13CN sigma multiplied by sqrt(2) because channel width is half the velocity resolution  
  > "the standard deviation calculated in the $\rm ^{13}CN$ spectra is multiplied by $\sqrt{2}$ because the channel width is half of the velocity resolution" (Analysis and Results / non-LTE modeling)
   - assumption: Molecular and dust emitting regions are vertically distinct: dust settled at midplane, molecular emission from higher altitudes  
  > "We assumed that the molecular and dust emitting regions are vertically distinct" (Analysis and Results / non-LTE modeling)
   - fitting: emcee MCMC, uniform priors over Table 1 ranges, 64 walkers, 10,000 steps, burn-in 6,000; Gaussian log-likelihood summed over velocity channels with sigma_obs from stacked spectra; ratio reported as median and 16-84th percentiles  
  > "We set our MCMC chains with 64 walkers and 10,000 steps and a burn-in of the first 6,000 steps." (Analysis and Results / non-LTE modeling); "$I_{\rm obs}(v)$ and $\sigma_{\rm obs}$ are the azimuthally stacked spectra and their standard deviation, respectively." (Analysis and Results / non-LTE modeling); "We calculated the median and \[16, 84\] th percentiles of posteriors" (Fitting Results)
   - validation: Marginal posteriors almost Gaussian; corner plots shown at r=56 and 101 au  
  > "The marginal posterior distributions are almost Gaussian for all parameters and radii." (Analysis and Results / non-LTE modeling)
7. **convert n(H2) to emitting-layer altitude and compare with literature**: Compare fitted n(H2) with the fiducial TW Hya disk model of Calahan et al. at r=60 and 100 au to infer z/r  
  > "corresponds to an altitude of $z/r\sim0.27$ in the model" (Fitting Results)
   - parameter: At r=60 au model gas surface density ~4 g/cm^2 and scale height ~5 au  
  > "The gas surface density and gas scale height at $r=60$ au are $\sim 4\ {\rm g\ cm^{-2}}$ and $\sim5$ au, respectively, in the fiducial TW Hya disk model of (cite: cala21)." (Fitting Results)
   - assumption: Mean molecular weight 2.37; Gaussian vertical gas distribution  
  > "Assuming these values, a mean molecular weight of 2.37, and that vertical gas distribution follows a Gaussian" (Fitting Results)
   - fitting: _not stated_
   - validation: Derived kinetic temperature and n(H2) compared with Teague & Loomis 2020, Munoz-Romero et al. 2023 and disk models  
  > "The derived kinetic temperature and $\rm H_2$ volume density are consistent with the previous analysis by (cite: teag20)" (Fitting Results)

## Software

- **CASA** 6.2.5 (modular); pipeline calibration in the CASA version of the original publication: Pipeline calibration, tclean imaging, uvcontsub, imsmooth, impbcor, immoments  
  > "Then, we CLEANed the continuum SPW using the CASA task `tclean` after flagging the detected emission lines." (Observations / 13CN); "modular version 6.2.5" (Observations)
- **Keplerian_mask** : Generating CLEAN masks and matched-filter kernels  
  > "a Keplerian mask made with a Python script `Keplerian_mask` (cite: kepmask)" (Observations / 13CN)
- **VISIBLE** : Matched filter cross-correlation of visibilities with a kernel  
  > "was calculated by a Python script `VISIBLE` (cite: loom18)" (Analysis and Results / matched filter)
- **gofish** : Azimuthal stacking of spectra assuming Keplerian rotation; disk-integrated 13CN spectrum  
  > "azimuthally stacked assuming Keplerian rotation using the python package `gofish` (cite: teag16)" (Analysis and Results / non-LTE modeling)
- **RADEX** : Non-LTE radiative transfer for peak optical depth and excitation temperature of hyperfine lines  
  > "a Python wrapper of the non-LTE radiative transfer code RADEX (cite: vand07)" (Analysis and Results / non-LTE modeling)
- **SpectralRadex** : Python wrapper of RADEX used to compute the grids  
  > "`SpectralRadex`[^1] (cite: hold21)" (Analysis and Results / non-LTE modeling)
- **emcee** : MCMC sampling of the posterior distribution at each radius  
  > "we used `emcee` (cite: fore13) and sampled the posterior distribution by the Markov Chain Monte Carlo (MCMC) method" (Analysis and Results / non-LTE modeling)
- **astropy** : Named in the Software list; specific use not stated  
  > "astropy (cite: astropy:2013; astropy:2018; astropy:2022), CASA (cite: mcmu07)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 12CN/13CN column density ratio at 30<r<80 au | 70 | +9/-6 | dimensionless | 6 | The $\rm ^{12}CN$/$\rm ^{13}CN$ ratio is measured to be $70^{+9}_{-6}$ at $30 < r < 80$ au from the central star |
| 12CN/13CN ratio at the local minimum near r~100 au | 48 | +5/-4 | dimensionless | 6 | At the local minimum, $\rm ^{12}CN$/$\rm ^{13}CN$ is estimated to be $48^{+5}_{-4}$. |
| H2 volume density range | (4-10)x10^7 | not stated | cm^-3 | 6 | The ${\rm H_2}$ volume density is found to range between $(4 - 10)\times10^7 \ {\rm cm^{-3}}$ |
| 12CN column density at r=30-120 au | 10^14-10^15 | not stated | cm^-2 | 6 | The column density of $\rm ^{12}CN$ ranges $10^{14-15}\ {\rm cm^{-2}}$ at r = $30-120$ au. |
| Altitude of CN emission at r=60 au (n(H2)=4e7 cm^-3) | z/r ~0.27 | not stated | dimensionless | 7 | corresponds to an altitude of $z/r\sim0.27$ in the model |
| Altitude of CN emission at r=100 au (n(H2)~1e8 cm^-3) | z/r ~0.22 | not stated | dimensionless | 7 | which corresponds to $z/r\sim0.22$ in the fiducial model of (cite: cala21) |
| Continuum SED power-law index across the three datasets | 2.13 | not stated | dimensionless | 2 | The SED can be well fitted by a power-law curve with an index of 2.13 |
| 13CN cube RMS noise | 1.0 | not stated | mJy | 1 | The root mean square (RMS) noise level is estimated to be 1.0 mJy |

## Qualitative findings

- 13CN N=2-1 emission shows a ring-like morphology similar to 12CN and extends beyond the continuum disk  
  > "The $\rm ^{13}CN$ $N=2-1$ emission exhibits a ring-like morphology, which is similar to the $\rm ^{12}CN$ lines (cite: teag20)." (Analysis and Results / matched filter)
- CN molecules mainly reside in the disk upper layer  
  > "suggesting that CN molecules mainly reside in the disk upper layer" (abstract)
- The CN ratio differs from earlier CO and HCN carbon isotope ratios in TW Hya  
  > "However, this value differs from the previously reported values found for other carbon-bearing molecules (CO and HCN) in the TW Hya disk." (abstract)

## Claim tuples

- H: Are the 13CN N=2-1 hyperfine lines detectable and spatially resolved in the TW Hya disk archival data? | E: Stacked moment-zero maps and a visibility-plane matched filter on the 2016.1.01375.S data | R: Five hyperfine lines detected above 5 sigma; the brightest at ~20 sigma | F: First spatially resolved detection of 13CN in a protoplanetary disk | **supported**
- H: What vertical layer of the disk does CN trace? | E: Non-LTE fit of 12CN and 13CN lines to get Tk and n(H2), mapped to z/r via a disk model | R: n(H2) ~4e7 cm^-3 at r<80 au, z/r ~0.2-0.3 | F: CN traces the disk upper layer inside ~80 au and lies closer to the midplane outside | **supported**
- H: Is the 12CN/13CN ratio ISM-like and consistent with CO and HCN carbon isotope ratios in TW Hya? | E: Radial 12CN/13CN column density ratio from MCMC non-LTE fits | R: 70 (+9/-6) at 30<r<80 au, ISM-like but different from CO (~20-40) and HCN (86) | F: Different carbon-bearing molecules show different carbon isotope ratios in the same disk | **supported**
- H: Can layer-dependent emission combined with sequestration of 12C into solids explain the isotope ratios? | E: Qualitative discussion with isotope exchange reactions and literature chemistry, no new chemical model | R: Scenario consistent with the ratios and emitting heights | F: Different emission heights plus preferential 12C locking into solids could explain the pattern | **partially**
- H: Is there a dip in 12CN/13CN near r~100 au? | E: Radial ratio profile from the MCMC fits | R: 48 (+5/-4) at r~100 au, ~3 sigma below the ISM value | F: Tentative dip, possibly from radial or vertical variation | **partially**

## Reasoning

- Why this data: 13CN lines in the archival data cover hyperfine lines with larger A*g_u than the MAPS coverage, enabling detection; archival 12CN data available  
  > "This is because they only covered the first seven hyperfine lines listed in Table" (Analysis and Results / matched filter)
- Why this method: Non-LTE modeling because 12CN lines were previously found not in LTE  
  > "Therefore, we performed non-LTE modeling." (Analysis and Results / non-LTE modeling)
- Alternative: Prestellar cloud of TW Hya being an outlier in local 12C/13C cannot be excluded, but is judged less likely  
  > "Another scenario to explain the low carbon isotope ratio in CO, which is less likely but cannot be ruled out" (Discussion / Carbon isotope fractionation scenarios)
- Alternative: Dip at r~100 au could be radial variation, vertical variation, or both  
  > "We note that these two possibilities are not mutually exclusive" (Discussion / dip at r~100 au)
- How they decided it was enough: _not stated_
- Limitation (authors): RADEX does not treat overlap of hyperfine lines  
  > "our non-LTE modeling uses the RADEX code, which does not treat e.g. the overlap effect of emission lines." (Discussion / Caveats)
- Limitation (authors): Homogeneous medium assumed: same Tk and n(H2) for all hyperfine lines, though real disks have vertical gradients  
  > "we assume that the kinetic temperature and $\rm H_2$ volume density are the same among all hyperfine lines" (Discussion / Caveats)
- Limitation (authors): Only para-H2 collision rates used for 13CN; new ortho-H2 data needed  
  > "New spectroscopic data for collision with ortho-$\rm H_2$ are required to model the $\rm ^{13}CN$ lines more robustly." (Analysis and Results / non-LTE modeling)
- Limitation (authors): 13CN column density may be affected by optically thick 12CN hyperfine lines; deeper multi-transition 13CN data needed  
  > "it may be possible that the retrieved $\rm ^{13}CN$ column density is affected by the optically thick $\rm ^{12}CN$ hyper-fine lines" (Discussion / Caveats)
- Caveat (inferred, ours): Only one 13CN transition (N=2-1) is used, so Tk, n(H2) and N(13CN) are degenerate and mostly set by 12CN lines
- Caveat (inferred, ours): Text and Table 1 disagree on the 13CN robust value (0.5 vs 0.0)
- Caveat (inferred, ours): Beam-matching to 0.5 arcsec and oversampled channels create correlated noise that the independent-channel chi-square likelihood ignores
- Caveat (inferred, ours): Flux-scale uncertainty is neglected in the ratio uncertainties
- Caveat (inferred, ours): The 12CN/13CN dip at ~100 au is only ~3 sigma and depends on the homogeneous-slab assumption
- Caveat (inferred, ours): Posterior uncertainties are statistical only; no systematic uncertainty from collision rates or the three-layer geometry is included

## Reproducibility

- Data public (paper): All three ALMA datasets are archival and identified by project code  
  > "We analyzed ALMA archival observations of the" (Observations); "from the archive (ID: 2017.1.01199.S, PI: R. Loomis)" (Observations / 12CN)
- Products in archive: _not stated_
- Missing: Self-calibration intermediate solints for 12CN N=2-1 and details for 12CN N=1-0
- Missing: Complete tclean parameters (imsize, cell, niter, threshold) and line-free channel ranges
- Missing: Distance used for au conversion and gofish binning parameters
- Missing: Exact dust optical depths tau_d used and the continuum intensity I_c per radius
- Missing: No analysis scripts or machine-readable results released
- Missing: Resolution of the robust discrepancy for the 13CN cube
- Data volume (inferred): Roughly 50-150 GB of raw ALMA measurement sets for the three projects (13CN 2 EBs of 41 min; 12CN 2-1 228 min; 12CN 1-0 105 min); estimate only
- Score (inferred): 3/5, Data are public with project codes and the radiative-transfer and MCMC recipe is described with equations, priors, grids and chain settings, but imaging parameters, line-free channels, distance and several self-calibration details are missing.
- Rediscovery candidate: yes, Archival data, a described pipeline (self-cal, tclean, matched filter, RADEX grids, emcee) and numeric key results (70 +9/-6 and 48 +5/-4) make the headline ratio redoable, with some gaps to fill.

## Links

- Method: Teague & Loomis 2020 (cite: teag20) (Earlier 12CN analysis of TW Hya data; non-LTE justification and processing for the N=1-0 data)
- Method: Loomis et al. 2018 (cite: loom18) (Matched filter method and VISIBLE script)
- Method: Hsieh et al. 2015 (cite: hsie15) (Intensity formula treating line overlap)
- Method: Holdship et al. 2021 (cite: hold21) (SpectralRadex Python wrapper of RADEX)
- Method: Teague et al. 2022 (cite: teag22) (Details of the 12CN N=2-1 observations)
- Companion: Yoshida et al. 2022 (cite: yosh22) (12CO/13CO ratio in TW Hya, compared with the CN result)
- Companion: Hily-Blant et al. 2019 (cite: hily19) (H12CN/H13CN ratio in TW Hya, compared with the CN result)
- Companion: Zhang et al. 2017 (cite: zhan17) (12C18O/13C18O ratio in TW Hya)
- Companion: Macias et al. 2021 (cite: maci21) (Dust optical depth used in the model)
- Related: MAPS ALMA Large Program (cite: ober21maps), which covered fewer 13CN hyperfine lines and did not detect them

## Checks

```json
{
 "quotes": 139,
 "quotes_ok": 139,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 112,
  "stated": 87,
  "rate": 0.777
 },
 "evidence_ok": true
}
```
