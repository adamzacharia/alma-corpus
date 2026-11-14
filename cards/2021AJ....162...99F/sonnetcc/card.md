# The Chemical Inventory of the Planet-hosting Disk PDS 70

`2021AJ....162...99F` | The Astronomical Journal 2021 | first author: Facchini, Stefano | arXiv: 2101.08369 | DOI: 10.3847/1538-3881/abf0a4

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry, exoplanets
- Question: What is the chemical inventory of the planet-hosting PDS 70 disk (detections, radial profiles, column densities, deuteration and N fractionation, C/O) and what does it imply for the gas accreted by the two planets?  
  > "As host to two accreting planets, PDS 70 provides a unique opportunity to probe the chemical complexity of atmosphere-forming material." (abstract); "In this paper, we present a spatially resolved chemical inventory of the disk around PDS 70 using observations obtained with the Atacama Large Millimeter Array (ALMA)." (Introduction)
- Target **PDS 70**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2019.1.01619.S, 2015.1.00888.S, 2017.A.00006.S
- bands: Band 6 (new data, program 2019.1.01619.S); Band 7 (archival, HCO+ 4-3 and 12CO 3-2)  
  > "We present ALMA Band 6 observations of the PDS 70 disk" (abstract); "Band 7 observations of HCO$^+$ $J$=4-3 and $^{12}$CO $J$=3-2 are included in the analysis." (Observations and data reduction)
- frequencies and spectral setup: Two Band 6 setups: 217.194-233.955 GHz (7 spws) and 243.570-262.081 GHz (9 spws); channel widths 61-977 kHz (Table of spectral setup); FDM windows  
  > "In particular, the lower frequency setup in the 217.194 - 233.955 GHz spectral range consisted of 7 spectral windows, while the higher frequency setup had 9 spectral windows." (Observations and data reduction); "243.570 - 262.081 GHz" (Table 1)
- continuum bandwidth: one 1.875 GHz wide spw per setup; bandwidth-weighted mean continuum frequencies 225.56 GHz (1.33 mm) and 252.80 GHz (1.19 mm)  
  > "In both cases one of the spectral windows has a bandwidth of $1.875\,$GHz to increase the continuum signal-to-noise ratio (snr)" (Observations and data reduction); "The bandwidth-weighted mean continuum frequencies are 225.56 GHz (1.33 mm) and 252.80 GHz (1.19 mm)." (Observations and data reduction)
- arrays: array type not stated; 43-46 antennas after flagging per execution block (Table 1)  
  > "Number of antennas after flagging." (Table 1)
- configurations: _not stated_
- baselines: 15-783 m and 15-969 m (low-frequency setup); 15-783 m (high-frequency setup)  
  > "15-783 m" (Table 1); "15-969 m" (Table 1)
- angular resolution: 0.4''-0.5'' (~50 au) for the line data  
  > "With a spatial resolution of $0.4\ensuremath{''}-0.5\ensuremath{''}$ ( $\sim50\,$au), 12 species are detected" (abstract)
- max recoverable scale: _not stated_
- sensitivity: ~1 mJy/beam in a 1 km/s channel at ~0.4''-0.5''  
  > "Achieving a typical sensitivity of $\sim1\,$mJy beam$^{-1}$ in a 1 km s$^{-1}$ channel with an angular resolution of $\sim0.4\ensuremath{''}-0.5\ensuremath{''}$" (Conclusions)
- time on source: ~40 min per execution block, two EBs per setup (42 min x2 low-frequency, 38 min x2 high-frequency)  
  > "with two execution blocks of $\sim40\,$min per spectral setup" (Observations and data reduction); "42 min" (Table 1); "38 min" (Table 1)
- observing dates: 2 Mar, 6 Mar and 16 Mar 2020 (Band 6)  
  > "06 Mar 2020" (Table 1); "16 Mar 2020" (Table 1); "02 Mar 2020" (Table 1)
- pi or archival as stated: Band 6: program 2019.1.01619.S (PI S. Facchini), short-spacing part of a program aiming at 0.1'' resolution; Band 7 data from programs 2015.1.00888.S and 2017.A.00006.S  
  > "These data represent the short spacing of a program aiming at imaging molecular lines at $0.1\ensuremath{''}$ resolution in the system, for which the long baseline data have not been taken yet." (Observations and data reduction); "The #2015.1.00888.S and #2017.A.00006.S data were calibrated as described in (cite: isella19)." (Observations and data reduction)
- Line: 12CO 3-2 (345.7959 GHz)
- Line: 12CO 2-1 (230.5380 GHz)
- Line: 13CO 2-1 (220.3986 GHz)
- Line: C18O 2-1 (219.5603 GHz)
- Line: H2CO 3_03-2_02 (218.2221 GHz)
- Line: H2CO 3_21-2_20 (218.7600 GHz)
- Line: CH3OH 10_2-9_3 (A+) (232.4185 GHz)
- Line: CH3OH 5_1-4_1 (A-) (243.9157 GHz)
- Line: C2H N=3-2, J=7/2-5/2, F=4-3 (262.0042 GHz)
- Line: C2H N=3-2, J=7/2-5/2, F=3-2 (262.0064 GHz)
- Line: C2H N=3-2, J=5/2-3/2, F=3-2 (262.0648 GHz)
- Line: c-C3H2 3_21-2_12 (244.2221 GHz)
- Line: c-C3H2 7_16-7_07 (218.7327 GHz)
- Line: H13CN 3-2 (259.0117 GHz)
- Line: HC15N 3-2 (258.1571 GHz)
- Line: DCN 3-2 (217.2386 GHz)
- Line: HCO+ 4-3 (Band 7) (356.7342 GHz)
- Line: H13CO+ 3-2 (260.2553 GHz)
- Line: CS 5-4 (244.9355 GHz)
- Line: SO 7_6-6_5 (261.8436 GHz)
- Line: SO 6_6-5_5 (258.2558 GHz)
- Line: 34SO 5_6-4_5 (246.6636 GHz)
- Other facility **Submillimeter Array (SMA)**: archival 1.33 mm flux density used for comparison (recalibrated by M. Gurwell: 63 mJy for baselines <15 klambda vs ~38 mJy published)  
  > "The flux density at 1.33 mm is consistent with the Submillimeter Array (SMA) observations presented in (cite: hashimoto15)." (Continuum); "a new calibration of the data leads to a flux density of 63 mJy for baselines $<15\,$k$\lambda$ (Mark Gurwell, private communication)" (Continuum)
- Other facility **ALMA Band 7 archival data (2015.1.00888.S, 2017.A.00006.S)**: HCO+ 4-3 and 12CO 3-2 lines  
  > "Band 7 observations of HCO$^+$ $J$=4-3 and $^{12}$CO $J$=3-2 are included in the analysis." (Observations and data reduction)
- Other facility **ALMA Band 3 and Band 7 flux-calibrator observations (J1427-4207)**: spectral index used to correct the Band 6 flux scale  
  > "the Band 6 flux was corrected by deriving a spectral index from a Band 3 and Band 7 observation of the flux calibrator J1427-4207." (Observations and data reduction)
- Other facility **ALMA 0.85 mm continuum (Keppler+2019 data, re-analysed by Isella+2019)**: 0.85 mm flux density 177 mJy and 855 micron continuum image for comparison  
  > "who re-analyzed the 0.85 mm data by (cite: keppler19) correcting for a flux density offset" (Continuum)
- Other facility **J-band polarized intensity (scattered light) profile**: IR scattered-light radial profile used to compare with line peak radii  
  > "The radial polarized intensity profile in $J$-band (cite: keppler18) shows a pronounced peak at $\sim0.48\ensuremath{''}$ from the central star" (Derivation of disk physical parameters)
- External data: Disk geometry and kinematics: M_star = 0.875 Msun, i = 51.7 deg, PA = 160.4 deg  
  > "We use the following geometrical parameters: M$_{\rm star}=0.875\,M_\odot$, $i=51.7^\circ$, PA$=160.4^\circ$ (cite: keppler19)." (Observations and data reduction) [from (cite: keppler19)]
- External data: Elevated emission surface z(r)=0.33 (r/1'')^0.76 for 12CO and HCO+  
  > "using the best fit parameters by (cite: keppler19): $z(r)[\ensuremath{''}]=0.33\times(r / 1\ensuremath{''})^{0.76}$" (Observations and data reduction) [from (cite: keppler19)]
- External data: Systemic velocity 5505 +/- 2 m/s  
  > "with the systemic velocity being $5505\pm2\,$m s$^{-1}$ (cite: keppler19)" (Line fluxes) [from (cite: keppler19)]
- External data: Initial parameters for the visibility-plane ring fit taken from the Band 7 continuum fit  
  > "with the parameters initialized from the fit to the ALMA Band 7 continuum reported in (cite: keppler19)" (Observations and data reduction) [from (cite: keppler19)]
- External data: 0.85 mm flux density 177 mJy (re-analysed with flux offset correction)  
  > "By using their estimated flux density of 177 mJy, we obtain a spectral index of $2.49\pm0.44$ and $2.84\pm0.59$ in the 0.85-1.33 and 0.85-1.19 mm range." (Continuum) [from (cite: isella19)]
- External data: SMA 1.33 mm flux density ~38 mJy as published; 63 mJy after recalibration (private communication)  
  > "While they report a flux density of $\sim38$ mJy, a new calibration of the data leads to a flux density of 63 mJy for baselines $<15\,$k$\lambda$ (Mark Gurwell, private communication)." (Continuum) [from (cite: hashimoto15)]
- External data: 12C/13C = 68 +/- 15 used to convert H13CN to HCN  
  > "In order to derive HCN column densities, a $^{12}$C/$^{13}$C ratio of 68$\pm15$ is assumed (cite: milam2005)." (Deuteration and N fractionation) [from (cite: milam2005)]
- External data: Molecular data (E_u, A_ul, g_u, partition functions) from CDMS  
  > "taken from the CDMS catalogue (cite: cdms), and interpolate the partition function, $Q$, with a cubic spline." (Column Densities and Optical Depths) [from (cite: cdms)]
- External data: PDS 70c semi-major axis 33.2 au (used to define the high-velocity channels inside the planet orbit)  
  > "From (cite: wang_ea_2021), planet c has an orbit with semi-major axis of 33.2 au." (Integrated maps) [from (cite: wang_ea_2021)]
- External data: Model N(CS)/N(SO) ~0.03 for solar C/O; ~10 for C/O ~1  
  > "Their reference model produces a disk averaged column density ratio $N$(CS)/$N$(SO)$\sim0.03$, while observations indicate a ratio with a lower limit $>1$." (C/O ratio); "A C/O ratio of $\sim1$ leads to a $N$(CS)/$N$(SO) ratio of $\sim10$ (cite: semenov_ea_2018)." (C/O ratio) [from (cite: semenov_ea_2018)]
- External data: C2H/13CO flux-ratio criterion: C/O>1 required when C2H 3-2 F=4-3 to 13CO 2-1 ratio >~0.2  
  > "they showed that C/O$>1$ is required when the ratio of the C$_2$H $N$=3-2 $J$=$\frac{7}{2}$-$\frac{5}{2}$ $F$=4-3 line to the $^{13}$CO $J$=2-1 line is $\gtrsim 0.2$." (C/O ratio) [from (cite: fedele_ea_2020)]
- External data: Thermochemical models: high C2H flux cannot be obtained with solar C/O; C/O ~1.5 required  
  > "In the thermo-chemical models by (cite: miotello_ea_2019), such a high flux cannot be obtained with a solar C/O ratio, and elemental ratios close to $\sim1.5$ are required." (C/O ratio) [from (cite: miotello_ea_2019)]
- Simulation/model as data: Literature thermochemical models (Miotello+2019 Lupus grid; Semenov+2018 DM Tau grid; Fedele & Favre 2020) used as comparison for C/O  
  > "With a grid of thermo-chemical models, the authors show that the only models able to reproduce their observations of sulfur-bearing molecules (in particular CS and SO) is with a C/O ratio $\gtrsim1$." (C/O ratio)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline calibration with minor manual flagging  
  > "The data were pipeline calibrated using the `CASA` package, version 5.6." (Observations and data reduction); "After minor manual flagging, we imaged the continuum of each execution block separately" (Observations and data reduction)
- casa version: CASA 5.6  
  > "The data were pipeline calibrated using the `CASA` package, version 5.6." (Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1427-4206 (Table 1; text writes J1427-4207); Band 6 flux corrected using a spectral index from Band 3 and Band 7 observations of the calibrator  
  > "For all execution blocks, the Band 6 flux was corrected by deriving a spectral index from a Band 3 and Band 7 observation of the flux calibrator J1427-4207." (Observations and data reduction); "J1427-4206" (Table 1)
- flux scale uncertainty: 10% absolute flux calibration  
  > "The uncertainties are dominated by the 10% absolute flux calibration in all datasets." (Continuum)
- self calibration: Three rounds of phase self-cal (first for polarization offsets at scan length; then 120 s and 60 s (low-frequency) or 120 s and 30 s (high-frequency), polarizations and spws combined), then one amplitude round at scan length; improvement 119% and 54% (peak snr 434 and 503)  
  > "A first one accounting for polarization offsets with scan length as solution interval, and then two rounds combining polarizations and spectral windows with 120 and 60 s solution intervals for the low frequency setting" (Observations and data reduction); "and 120 and 30 s solution intervals for the high frequency one." (Observations and data reduction); "A final step of amplitude self-calibration at scan length was performed in both cases." (Observations and data reduction)

### Imaging

- task: tclean (continuum and lines)  
  > "Image reconstruction was performed with the `tclean` task by using the `multiscale` deconvolver, cleaning down to the $1\sigma$ level." (Observations and data reduction)
- deconvolver: multiscale, allowing for point sources (lines); clean to 1 sigma (continuum)  
  > "Imaging of the spectral lines was performed with `tclean` with the `multiscale` deconvolver, allowing for point sources in the emission" (Observations and data reduction)
- weighting robust: self-cal model: Briggs robust 0.5; continuum: robust 2 and superuniform (npixels=3); lines: natural or Briggs robust 0 (per line, Table 2)  
  > "When cleaning with Briggs weighting with a robust parameter of 2, we obtain a very high peak snr of 714 and 608" (Continuum); "we re-image the data at high angular resolution using `superuniform` weighting, with a `npixels` parameter equalling 3 in the `tclean` task." (Continuum); "natural weighting and uvtapering is used to maximize line detection, while Briggs weighting with robust parameter of 0 is used to maximize the spatial resolution" (Observations and data reduction)
- uv taper: 0.7'' uv-taper for c-C3H2 3_21-2_12 and H2CO 3_21-2_20  
  > "In order to increase the significance of the detections, we image the lines with an additional $uv$-tapering of $0.7\ensuremath{''}$." (Line fluxes)
- cell size: _not stated_
- image size: _not stated_
- masking: self-cal: elliptical mask PA 160.4 deg, semi-major axis 1.7'', inclination 51.7 deg; lines: Keplerian masks (keplerian_mask.py) from Keppler+2019 geometry  
  > "with a Briggs robust parameter of $0.5$ and an elliptical mask with a position angle (PA) of $160.4^\circ$, semi-major axis of 1.7$''$ and a ratio of major to minor axis given by an inclination of $51.7^\circ$" (Observations and data reduction); "we apply so-called Keplerian masks, i.e. exploit the rotation of the disk well fitted by a Keplerian model in the $^{12}$CO $J$=3-2 line to have a prior on where the molecular lines originate." (Observations and data reduction); "The channel masks were created with the `keplerian_mask.py` tool[^1]." (Observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, first-order fit  
  > "Continuum subtraction was performed using first order fitting with the `uvcontsub` task." (Observations and data reduction)
- line free channels: for the self-cal continuum, channels within +/-20 km/s (~14.5-17.5 MHz) of listed lines were flagged; channels used for uvcontsub not stated  
  > "after flagging channels within $\pm20\,$km s$^{-1}$ ($\sim14.5-17.5\,$MHz depending on the central rest frequency) from all the lines listed in Tab." (Observations and data reduction)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: HCN-isotopologue cubes smoothed to a common circular 0.42'' beam with CASA imsmooth  
  > "and then smoothed to a common circular beam of $0.42\ensuremath{''}$ with the CASA `imsmooth` task." (Deuteration and N fractionation)
- final beam: superuniform continuum beams 0.30''x0.24'' (PA 107.3 deg) at 1.19 mm and 0.28''x0.24'' (PA 67.9 deg) at 1.33 mm; line-cube beams in Table 2  
  > "The 1.19 mm and 1.33$\,$mm images respectively present a synthesized beam of 0.30$''$$\times$0.24$''$ (PA = 107.3$^\circ$) and 0.28$''$$\times$0.24$''$ (PA = 67.9$^\circ$), with an rms of 71 and 53 $\mu$Jy beam$^{-1}$." (Continuum)
- final rms: continuum rms 21 uJy/beam (robust=2), 71 and 53 uJy/beam (superuniform); line channel rms in Table 2  
  > "Within the same mask used for self-calibration the disk shows a flux density of 68.7 and 57.6 mJy, respectively, with an rms of 21 $\mu$Jy beam$^{-1}$ in both images." (Continuum); "with an rms of 71 and 53 $\mu$Jy beam$^{-1}$." (Continuum)

### Inherited from earlier work

- Self-calibration setup: re-centre each EB first to build the best self-cal model  
  > "we preferred to re-center each execution block beforehand in order to construct the best model for self-calibration from the first step (cite: andrews18)" (Observations and data reduction) [from (cite: andrews18)]
- Flux-offset correction between execution blocks with gaincal  
  > "we followed the procedure used in the DSHARP collaboration (cite: andrews18), correcting for flux offsets using the `gaincal` task." (Observations and data reduction) [from DSHARP, (cite: andrews18)]
- Calibration of the Band 7 data (2015.1.00888.S, 2017.A.00006.S)  
  > "The #2015.1.00888.S and #2017.A.00006.S data were calibrated as described in (cite: isella19)." (Observations and data reduction) [from (cite: isella19)]
- Line stacking technique (deproject and shift spectra to systemic velocity)  
  > "we use the same technique used in (cite: Teague16), similar to the one developed by (cite: yen2016) and (cite: matra2017)." (Line fluxes) [from (cite: Teague16); (cite: yen2016); (cite: matra2017)]
- emcee-based column density and excitation temperature fit  
  > "Following, e.g., (cite: loomis2018), we use `emcee` (cite: Foreman-Mackey+13) to explore the posterior distributions for" (H2CO) [from (cite: loomis2018)]
- Optical-depth correction of the optically thin column density  
  > "following, for example, (cite: GoldsmithLanger1999)." (Column Densities and Optical Depths) [from (cite: GoldsmithLanger1999)]
- Excitation temperatures 20, 30, 50 K for single-transition molecules  
  > "guided by previous analyses of C$_2$H in other sources (cite: bergner2019)" (C2H) [from (cite: bergner2019)]
- HCN-isotopologue deuteration and 14N/15N procedure  
  > "We follow the same procedure used in (cite: bergner2020) to extract the column density ratio between the three isotopologues." (Deuteration and N fractionation) [from (cite: bergner2020)]

### Not stated but needed to reproduce (our reading)

- Image size and cell size for continuum and every line cube
- Multiscale scales and clean thresholds/niter per line cube
- Line-free channels and spw handling used in uvcontsub
- Keplerian mask parameters (mask radii, velocity tolerance, per-line settings)
- Per-EB flux-scale factors found with gaincal and the Band 3/Band 7 calibrator flux values
- Amplitude self-cal solution interval details and which self-cal tasks and parameters (combine, gaintype, minsnr)
- Pipeline version used for the calibration
- Prior ranges and likelihood (noise model) for the emcee column-density fits, and the Delta v and Omega used for each annulus
- Exact GoFish settings (annulus widths, deprojection options) for the stacked spectra
- How the 3-sigma line-flux upper limits were computed (velocity range, aperture)
- Which exact Gaussian-ring parameter values were obtained per EB in the visibility fit
- How HCO+ and 12CO 3-2 Band 7 data were imaged beyond 'natural weighting' (cell, size, channel)

## Analysis recipe

1. **Align execution blocks**: Per-EB continuum imaging showed pointing offsets; ring fitted in the visibility plane per EB, then phase centres shifted with fixvis and EBs re-aligned with fixplanet  
  > "After minor manual flagging, we imaged the continuum of each execution block separately, and noticed that likely due to poor weather conditions the pointing was offset between execution blocks by a significant fraction of the beam." (Observations and data reduction); "We thus fitted the outer ring using a Gaussian ring model in the visibility plane, with seven free parameters (intensity normalization, radius and width of the ring, inclination, position angle and disk center)." (Observations and data reduction)
   - software: CASA, GALARIO, emcee
   - parameter: 60 walkers, 2000 steps after burn-in  
  > "a Python implementation of the Metropolis-Hastings ensemble sampler, with 60 walkers and 2000 steps after burn-in." (Observations and data reduction)
   - parameter: baselines <650 klambda used in the fit  
  > "Baselines were selected to be $<650\,$k$\lambda$ to have the most uniform $(u,v)$-coverage across different execution blocks." (Observations and data reduction)
   - parameter: phase-centre shift with fixvis, alignment with fixplanet  
  > "We then shifted the phase center of each execution block using the `fixvis` task, and re-aligned all the execution blocks to the same coordinate system using the `fixplanet` task." (Observations and data reduction)
   - assumption: outer ring modelled as a Gaussian ring because no inner disk is detected in single EBs  
  > "that no clear emission from an inner disk is present in the single execution blocks" (Observations and data reduction)
   - fitting: emcee ensemble sampler (via GALARIO model), flat priors, initialised from Keppler+2019 Band 7 fit; likelihood not stated  
  > "Flat priors were used, with the parameters initialized from the fit to the ALMA Band 7 continuum reported in (cite: keppler19)." (Observations and data reduction)
   - validation: _not stated_
2. **Correct Band 6 flux scale**: Spectral index of the flux calibrator from Band 3 and Band 7 used to correct Band 6 flux; offsets between EBs of the same setup corrected relative to the EB closest in time to the Band 7 calibrator measurement, following DSHARP, with gaincal  
  > "We thus decided to correct for flux offsets between execution blocks with the same spectral setup by using the flux from the observation that was closest in time to the Band 7 calibrator estimate." (Observations and data reduction); "correcting for flux offsets using the `gaincal` task." (Observations and data reduction)
   - software: CASA
   - assumption: Band 7 calibrator measurement was 8-18 days from the science observations  
  > "the closest observation in Band 7 was from February 27, 2020, 18 days before the latest observation of PDS 70." (Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Self-calibrate the continuum**: EBs of the same setup combined with concat; self-cal on the two setups separately: 3 rounds of phase self-cal and one amplitude round, applied afterwards to the unflagged, unaveraged visibilities  
  > "The datasets with same spectral setup were combined using the `concat` task, and then self-calibration was performed on the two frequency settings separately." (Observations and data reduction); "The self-calibration tables were then applied to the unflagged, unaveraged visibilities." (Observations and data reduction)
   - software: CASA
   - parameter: channels within +/-20 km/s of listed lines flagged before self-cal  
  > "after flagging channels within $\pm20\,$km s$^{-1}$ ($\sim14.5-17.5\,$MHz depending on the central rest frequency) from all the lines listed in Tab." (Observations and data reduction)
   - parameter: continuum averaged with channels <500 MHz  
  > "The resulting continuum was channel averaged with channels $<500\,$MHz to avoid bandwidth smearing." (Observations and data reduction)
   - parameter: model imaged down to 5 sigma of initial data, Briggs robust 0.5, elliptical mask; rms in annulus 2.55''-4.25''  
  > "At every step of the self-calibration the model was imaged cleaning down to $5\sigma$ of the initial data, with a Briggs robust parameter of $0.5$" (Observations and data reduction); "The rms is estimated over an elliptical annulus with the same PA and axes ratio between 2.55$''$ and 4.25$''$." (Observations and data reduction)
   - fitting: _not stated_
   - validation: overall improvement 119% and 54%, peak snr 434 and 503 (low and high frequency setups)  
  > "The overall improvement was 119% and 54%, for a peak snr of 434 and 503, for the low and high frequency setups respectively." (Observations and data reduction)
4. **Image the continuum and derive flux densities and spectral index**: tclean multiscale continuum images with robust=2 for flux density, superuniform weighting for high resolution; spectral index vs 0.85 mm flux; inner-disk upper limit from the cavity-centre intensity  
  > "we re-image the data at high angular resolution using `superuniform` weighting, with a `npixels` parameter equalling 3 in the `tclean` task." (Continuum); "By estimating the intensity at the center of the disk, we determine an upper limit for the inner disk flux density of 0.34 mJy at 1.33 mm." (Continuum)
   - software: CASA tclean
   - parameter: flux density measured within the self-cal mask  
  > "Within the same mask used for self-calibration the disk shows a flux density of 68.7 and 57.6 mJy, respectively, with an rms of 21 $\mu$Jy beam$^{-1}$ in both images." (Continuum)
   - assumption: 0.85 mm flux density of 177 mJy from Isella+2019 and 10% absolute flux uncertainty in all datasets  
  > "The uncertainties are dominated by the 10% absolute flux calibration in all datasets." (Continuum)
   - fitting: _not stated_
   - validation: no flux density loss in superuniform imaging; 1.33 mm flux consistent with recalibrated SMA flux  
  > "There is no flux density loss in the imaging." (Continuum)
5. **Image the line cubes**: uvcontsub first-order continuum subtraction; tclean multiscale with Keplerian masks; lines imaged -6 to +17 km/s with natural and robust 0 weighting, final per-line choice in Table 2; elevated emission surface for 12CO and HCO+  
  > "Imaging of the spectral lines was performed with `tclean` with the `multiscale` deconvolver, allowing for point sources in the emission" (Observations and data reduction); "were imaged between -6 and +17 km s$^{-1}$ with both natural and Briggs weighting with a robust parameter equalling zero." (Observations and data reduction)
   - software: CASA tclean, CASA uvcontsub, keplerian_mask.py
   - parameter: Keplerian mask geometry from Keppler+2019: M_star 0.875 Msun, i 51.7 deg, PA 160.4 deg  
  > "We use the following geometrical parameters: M$_{\rm star}=0.875\,M_\odot$, $i=51.7^\circ$, PA$=160.4^\circ$ (cite: keppler19)." (Observations and data reduction)
   - parameter: elevated surface z(r)=0.33 x (r/1'')^0.76 for 12CO and HCO+  
  > "using the best fit parameters by (cite: keppler19): $z(r)[\ensuremath{''}]=0.33\times(r / 1\ensuremath{''})^{0.76}$" (Observations and data reduction)
   - parameter: weak lines c-C3H2 3_21-2_12 and H2CO 3_21-2_20 additionally uv-tapered by 0.7''  
  > "In order to increase the significance of the detections, we image the lines with an additional $uv$-tapering of $0.7\ensuremath{''}$." (Line fluxes)
   - assumption: line emission follows the Keplerian model fitted to 12CO 3-2  
  > "exploit the rotation of the disk well fitted by a Keplerian model in the $^{12}$CO $J$=3-2 line to have a prior on where the molecular lines originate." (Observations and data reduction)
   - fitting: _not stated_
   - validation: multiple imaging runs per line to balance resolution, intensity and channel spacing  
  > "multiple imaging runs have been performed on each line to obtain the best compromise between angular resolution, intensity and channel spacing." (Observations and data reduction)
6. **Stack spectra and measure line fluxes and detections**: Deproject and shift local spectra to systemic velocity with GoFish using the Keppler+2019 Keplerian fit, integrate within 3'' (4'' for 12CO 2-1), integrate spectrum over velocity windows; C2H F=4-3 and F=3-2 blend fitted with a double Gaussian; weak lines checked by azimuthally averaged spectra and a VISIBLE matched filter  
  > "at every spatial location we de-project the emission and then shift the local spectrum to the systemic velocity using the `GoFish` package (cite: gofish)." (Line fluxes); "We then integrate the spectra within $3\ensuremath{''}$ from the disk center" (Line fluxes); "and fluxes have been estimated by fitting a double Gaussian to the profile." (Line fluxes)
   - software: GoFish, VISIBLE, CASA
   - parameter: integration window 3-8 km/s (default); 1.5-9.5 km/s for the two 12CO and HCO+; 2-9 km/s for 13CO, H13CN and C2H  
  > "To obtain line fluxes, we spectrally integrate the spatially integrated stacked spectrum between 3-8 km s$^{-1}$, with the systemic velocity being $5505\pm2\,$m s$^{-1}$ (cite: keppler19)." (Line fluxes); "The two $^{12}$CO and the HCO$^+$ lines are integrated between 1.5-9.5 km s$^{-1}$" (Line fluxes)
   - parameter: flux uncertainty from standard deviation of unused velocity bins times sqrt(number of integrated bins)  
  > "The flux uncertainty for all lines is estimated as standard deviation of the velocity bins not included in the velocity integration, times the square root of the number of bins over which we integrate." (Line fluxes)
   - parameter: C2H J=5/2-3/2 only half covered: only the part of the disk within 80 deg of the red-shifted major axis is used, azimuthal symmetry assumed  
  > "we consider only the part of the disk within $80^\circ$ of the red-shifted major axis and then assume azimuthal symmetry to extract the total flux." (Line fluxes)
   - assumption: Keplerian kinematics from Keppler+2019 apply to all lines  
  > "Exploiting the kinematical fit of the Keplerian disk obtained by (cite: keppler19)" (Line fluxes)
   - fitting: double Gaussian fit to blended C2H J=7/2-5/2 lines  
  > "and fluxes have been estimated by fitting a double Gaussian to the profile." (Line fluxes)
   - validation: weak-line detections checked in channel maps, in azimuthally averaged spectra on annuli of 1/4 beam major axis, and with a VISIBLE matched filter on the visibilities  
  > "As a final test to assess the robustness of the detection of the two lines, we divide the projected emission in concentric annuli, separated by one quarter of the major axis of the beam." (Line fluxes); "This method requires a model image as matched filter, and we thus run the analysis onto the continuum subtracted visibilities with the CS and H$^{13}$CO$^+$ channel maps as filters." (Line fluxes)
7. **Make integrated intensity maps and radial profiles**: Integrated intensity maps over whole cubes with 2.5 sigma clipping and Keplerian masking; azimuthal average of deprojected moment-0 maps in annuli of 1/4 beam major axis  
  > "Integrated intensity maps of the 14 detected lines are then created integrating over the whole cubes with a $2.5\sigma$ clipping." (Integrated maps); "we azimuthally average the de-projected integrated intensity maps shown in Fig." (Radial profiles)
   - software: CASA, GoFish
   - parameter: annulus width = 1/4 of the beam major axis  
  > "The width of the annuli are a quarter of the beam major axis." (Radial profiles)
   - parameter: error bars: standard deviation within annuli divided by sqrt of number of independent beams  
  > "Error bars are estimated from the standard deviations of the emission within the annuli, divided by the square root of the number of independent beams across the azimuthal range." (Radial profiles)
   - fitting: _not stated_
   - validation: compared with GoFish stacking-based radial profiles; agreement outside one beam major axis, stacking underestimates inner regions  
  > "For radii larger than the beam major axis, the agreement between the two methods is remarkable" (Radial profiles with GoFish)
8. **Derive column densities, optical depths and H2CO excitation temperature**: Optically thin column density with optical-depth correction, LTE; H2CO N and Tex fitted jointly from two transitions per 0.1'' annulus; other molecules fitted at fixed Tex of 20, 30, 50 K with tau<1 prior; c-C3H2, SO, CH3OH disk-averaged (upper limits from 3 sigma flux limits)  
  > "Instead we follow a similar approach to that used for H$_2$CO, but for each individual component separately, which implicitly assumes that local thermodynamic equilibrium (LTE) is valid." (C2H); "We add a prior on the optical depth to be $<1$ for all molecules" (Other Molecules); "From the upper limits on the SO and CH$_3$OH we can derive upper limits on the disk averaged column density following the same approach." (c-C3H2 and upper limits on SO and CH3OH)
   - software: emcee, scipy.optimize.curve_fit, GoFish
   - parameter: H2CO: 128 walkers, 1000 burn-in steps, 500 sampling steps per radial bin  
  > "For each radial bin, we use 128 walkers, each taking 1,000 steps to burn in, and then an additional 500 steps to sample the posterior distributions." (H2CO)
   - parameter: C2H: Tex fixed to 20, 30, 50 K; 128 walkers, 1000 burn-in, 500 sampling steps  
  > "As only a single transition is considered, $T_{\rm ex}$ was held constant at values of $\{20,\, 30,\, 50\}$ K" (C2H); "The 128 walkers took 1,000 steps to burn in and an additional 500 to sample the posteriors." (C2H)
   - parameter: radial bins 0.1'' wide; c-C3H2 disk average uses a 3'' radius  
  > "binned into annuli of $0.1\ensuremath{''}$" (Other Molecules); "A radius of $3\ensuremath{''}$ is used to compute $\Omega$." (c-C3H2 and upper limits on SO and CH3OH)
   - parameter: C2H blended lines fitted with two Gaussians (scipy curve_fit), line centres fixed to the rest frequencies  
  > "we fit two Gaussian components using the `scipy.optimize.curve_fit` routine, fixing the line centers to the rest frequency of the two transitions" (C2H)
   - assumption: LTE, top-hat line profile for tau, partition function interpolated with cubic spline, CDMS molecular data  
  > "taken from the CDMS catalogue (cite: cdms), and interpolate the partition function, $Q$, with a cubic spline." (Column Densities and Optical Depths)
   - fitting: emcee; H2CO posteriors Gaussian, median with 16th-84th percentile uncertainty; priors and likelihood not stated beyond tau<1  
  > "As the posteriors were found to be Gaussian, we take the median value for each parameter as the most likely value, and the 16th to 84th percentile as a quantification of the uncertainty on this." (H2CO)
   - validation: concordance of the three C2H components supports well-constrained N and LTE  
  > "The concordance between these three transitions suggests that the C$_2$H column density is well constrained and that LTE is a reasonable assumption." (C2H)
9. **Derive HCN deuteration and 14N/15N fractionation**: Column-density ratios of H13CN, DCN, HC15N (disk-averaged within 3'' and radial profiles), HCN = 68 x H13CN, Tex 30 K (20-50 K for uncertainty); cubes smoothed to a common 0.42'' beam  
  > "We assume that the emission from the three isotopologues is at the same excitation temperature, which we fix at 30 K." (Deuteration and N fractionation); "and then smoothed to a common circular beam of $0.42\ensuremath{''}$ with the CASA `imsmooth` task." (Deuteration and N fractionation)
   - software: CASA imsmooth
   - parameter: H13CN and HC15N compared in natural-weighted images; H13CN and DCN in robust=0 images  
  > "The H$^{13}$CN and HC$^{15}$N lines are instead compared from images with natural weighting, which lead to the same beam." (Deuteration and N fractionation)
   - parameter: profiles limited to r <~ 1.8'' due to low snr  
  > "The analysis is limited to $r\lesssim 1.8\ensuremath{''}$ due to the low snr at larger radii." (Deuteration and N fractionation)
   - assumption: uniform 12C/13C = 68 +/- 15 and equal Tex for the three isotopologues  
  > "In order to derive HCN column densities, a $^{12}$C/$^{13}$C ratio of 68$\pm15$ is assumed (cite: milam2005)." (Deuteration and N fractionation)
   - fitting: _not stated_
   - validation: uncertainties include flux rms, 12C/13C, flux calibration and Tex systematics; carbon-fractionation caveat noted  
  > "Other sources of uncertainty are included in the error estimate (flux rms, $^{12}$C/$^{13}$C, absolute flux calibration)" (Deuteration and N fractionation)
10. **Infer C/O from C2H and CS/SO**: Compare C2H flux and C2H/13CO ratio with thermochemical models (Miotello+2019, Fedele & Favre 2020) and the lower limit on N(CS)/N(SO) with Semenov+2018  
  > "For PDS 70, this ratio ranges between 0.25-0.35 throughout the whole disk out to $r\sim2\ensuremath{''}$, indicating again a C/O ratio above unity for this particular disk." (C/O ratio); "we obtain a lower limit on the $N$(CS)/$N$(SO) ratio of $\sim109$." (C/O ratio)
   - assumption: literature model grids (not tailored to a large cavity) apply qualitatively  
  > "However, we note that all these models have been fine tuned for disks that do not exhibit a large cavity, as is the case for PDS 70." (C/O ratio)
   - fitting: _not stated_
   - validation: two independent proxies agree on C/O > 1; quantitative forward model deferred to future work  
  > "In summary, a comparison of the PDS 70 inventory with thermo-chemical models of protoplanetary disks from the literature suggests a disk-average C/O ratio $>1$ using different proxies" (C/O ratio)
11. **Compare radial peak locations with continuum and scattered light**: Radius of peak integrated intensity (r>0.2'' for 12CO and HCO+) read from radial profiles without smoothing or fitting, error = 1/4 beam major axis; compared with 855 micron continuum and J-band polarized intensity  
  > "the radius of the peak intensity is derived without any smoothing or fitting." (Comparing mm Continuum, IR Scattered Light and Molecular Emission Profiles); "An error of one quarter of the beam major axis is assigned to the peak location." (Comparing mm Continuum, IR Scattered Light and Molecular Emission Profiles)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.6: pipeline calibration, flagging, concat, fixvis, fixplanet, gaincal, self-calibration, tclean, uvcontsub, imsmooth  
  > "The data were pipeline calibrated using the `CASA` package, version 5.6." (Observations and data reduction)
- **tclean** : continuum and line imaging with multiscale deconvolver  
  > "Image reconstruction was performed with the `tclean` task by using the `multiscale` deconvolver, cleaning down to the $1\sigma$ level." (Observations and data reduction)
- **GALARIO** : visibility-plane Gaussian ring fit used to align execution blocks  
  > "Each execution was fitted separately using the `GALARIO` code (cite: galario)" (Observations and data reduction)
- **emcee** : posterior sampling for the ring fit and for column density and Tex fits  
  > "sampling the posterior distributions with the `emcee` package (cite: Foreman-Mackey+13)" (Observations and data reduction); "we use `emcee` (cite: Foreman-Mackey+13) to explore the posterior distributions for" (H2CO)
- **GoFish** : deprojecting, velocity-shifting and azimuthally averaging spectra (stacking, annular spectra, radial profile test)  
  > "at every spatial location we de-project the emission and then shift the local spectrum to the systemic velocity using the `GoFish` package (cite: gofish)." (Line fluxes)
- **VISIBLE** : matched-filter line search in the uv-plane  
  > "we exploit the `VISIBLE` package by (cite: VISIBLE), which has been successfully applied to protoplanetary disks observations" (Line fluxes)
- **keplerian_mask.py** : channel masks for cleaning  
  > "The channel masks were created with the `keplerian_mask.py` tool[^1]." (Observations and data reduction)
- **scipy.optimize.curve_fit** : Gaussian fits to C2H spectra  
  > "we fit two Gaussian components using the `scipy.optimize.curve_fit` routine" (C2H)
- **Matplotlib and numpy** : listed in the paper's software section; specific use not stated  
  > "`Matplotlib` (cite: matplotlib), `numpy` (cite: numpy)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux density at 1.19 mm (robust=2) | 68.7 | not stated | mJy | 4 | Within the same mask used for self-calibration the disk shows a flux density of 68.7 and 57.6 mJy, respectively, with an rms of 21 $\mu$Jy beam$^{-1}$ in both images. |
| Continuum flux density at 1.33 mm (robust=2) | 57.6 | not stated | mJy | 4 | Within the same mask used for self-calibration the disk shows a flux density of 68.7 and 57.6 mJy, respectively, with an rms of 21 $\mu$Jy beam$^{-1}$ in both images. |
| Spectral index 0.85-1.33 mm | 2.49 | 0.44 | dimensionless | 4 | By using their estimated flux density of 177 mJy, we obtain a spectral index of $2.49\pm0.44$ and $2.84\pm0.59$ in the 0.85-1.33 and 0.85-1.19 mm range. |
| Spectral index 0.85-1.19 mm | 2.84 | 0.59 | dimensionless | 4 | By using their estimated flux density of 177 mJy, we obtain a spectral index of $2.49\pm0.44$ and $2.84\pm0.59$ in the 0.85-1.33 and 0.85-1.19 mm range. |
| Inner disk flux density upper limit at 1.33 mm | <0.34 | not stated | mJy | 4 | By estimating the intensity at the center of the disk, we determine an upper limit for the inner disk flux density of 0.34 mJy at 1.33 mm. |
| Inner disk 0.85-1.33 mm spectral index lower limit | 1.61 | 0.44 | dimensionless | 4 | we obtain a lower limit on the 0.85-1.33 mm spectral index of the inner disk of $1.61\pm0.44$ |
| 12CO 3-2 line flux (text value) | 12.3 | 0.1 | Jy km/s | 6 | the bright $^{12}$CO 3-2 line ($12.3\pm0.1\,$Jy km s$^{-1}$) and the faint c-C$_3$H$_2$ 3$_{21}$-2$_{12}$ line ($60\pm14$ mJy km s$^{-1}$) |
| 12CO 3-2 line flux (Table 2) | 12421 | 147 | mJy km/s | 6 | 345.7959 / nat / 0.11$''$$\times$0.10$''$ (90.3$^\circ$) / 0.42 / 1.1 / 12421 / 147 / |
| 12CO 2-1 line flux | 6109 | 26 | mJy km/s | 6 | 230.5380 / r=0 / 0.37$''$$\times$0.33$''$ (67.1$^\circ$) / 0.09 / 4.1 / 6109 / 26 / |
| 13CO 2-1 line flux | 1846 | 14 | mJy km/s | 6 | 220.3986 / r=0 / 0.39$''$$\times$0.35$''$ (69.6$^\circ$) / 0.19 / 3.0 / 1846 / 14 / |
| C18O 2-1 line flux | 465 | 9 | mJy km/s | 6 | 219.5603 / r=0 / 0.39$''$$\times$0.35$''$ (68.3$^\circ$) / 0.19 / 2.4 / 465 / 9 / |
| H2CO 3_03-2_02 line flux | 710 | 7 | mJy km/s | 6 | 218.2221 / r=0 / 0.40$''$$\times$0.35$''$ (69.0$^\circ$) / 0.39 / 1.5 / 710 / 7 / |
| H2CO 3_21-2_20 line flux | 53 | 12 | mJy km/s | 6 | 218.7600 / nat / 0.57$''$$\times$0.52$''$ (100.8$^\circ$) / 0.39 / 1.2 / 53 / 12 / |
| C2H J=7/2-5/2 F=4-3 line flux | 741 | 12 | mJy km/s | 6 | 262.0042 / r=0 / 0.39$''$$\times$0.32$''$ (107.7$^\circ$) / 0.16 / 3.0 / 741 / 12 / |
| C2H J=7/2-5/2 F=3-2 line flux | 586 | 14 | mJy km/s | 6 | 262.0064 / r=0 / 0.39$''$$\times$0.32$''$ (107.7$^\circ$) / 0.16 / 3.0 / 586 / 14 / |
| C2H J=5/2-3/2 F=3-2 line flux (half of the line covered, corrected assuming symmetry) | 603 | 17 | mJy km/s | 6 | 262.0648 / r=0 / 0.39$''$$\times$0.32$''$ (107.7$^\circ$) / 0.16 / 3.0 / 603$^d$ / 17 / |
| C2H J=7/2-5/2 total line flux | ~1327 | 18 | mJy km/s | 6 | with a total flux of the $J$=$\frac{7}{2}$-$\frac{5}{2}$ transition of $\sim1327\pm18\,$mJy km s$^{-1}$ |
| c-C3H2 3_21-2_12 line flux | 60 | 14 (text); 11 (Table 2) | mJy km/s | 6 | the bright $^{12}$CO 3-2 line ($12.3\pm0.1\,$Jy km s$^{-1}$) and the faint c-C$_3$H$_2$ 3$_{21}$-2$_{12}$ line ($60\pm14$ mJy km s$^{-1}$) |
| H13CN 3-2 line flux | 326 | 17 | mJy km/s | 6 | 259.0117 / r=0 / 0.39$''$$\times$0.32$''$ (107.1$^\circ$) / 0.33 / 1.9 / 326 / 17 / |
| HC15N 3-2 line flux | 197 | 16 | mJy km/s | 6 | 258.1571 / nat / 0.56$''$$\times$0.46$''$ (100.6$^\circ$) / 0.33 / 1.7 / 197 / 16 / |
| DCN 3-2 line flux | 209 | 11 | mJy km/s | 6 | 217.2386 / r=0 / 0.40$''$$\times$0.35$''$ (70.8$^\circ$) / 0.39 / 1.7 / 209 / 11 / |
| HCO+ 4-3 line flux | 5199 | 122 | mJy km/s | 6 | 356.7342 / nat / 0.21$''$$\times$0.18$''$ (73.1$^\circ$) / 0.21 / 3.3 / 5199 / 122 / |
| H13CO+ 3-2 line flux | 344 | 12 | mJy km/s | 6 | 260.2553 / r=0 / 0.39$''$$\times$0.32$''$ (108.8$^\circ$) / 0.16 / 3.0 / 344 / 12 / |
| CS 5-4 line flux | 450 | 6 | mJy km/s | 6 | 244.9355 / r=0 / 0.42$''$$\times$0.34$''$ (108.8$^\circ$) / 1.38 / 0.9 / 450 / 6 / |
| SO 7_6-6_5 line flux 3-sigma upper limit | <27 | not stated | mJy km/s | 6 | 261.8436 / nat / 0.56$''$$\times$0.44$''$ (103.6$^\circ$) / 1.38 / 1.1 / $<$27$^{c}$ / ... / |
| SO 6_6-5_5 line flux 3-sigma upper limit | <52 | not stated | mJy km/s | 6 | 258.2558 / nat / 0.56$''$$\times$0.47$''$ (104.4$^\circ$) / 1.38 / 1.0 / $<$52$^{c}$ / ... / |
| CH3OH 10_2-9_3 (A+) line flux 3-sigma upper limit | <32 | not stated | mJy km/s | 6 | 232.4185 / nat / 0.53$''$$\times$0.50$''$ (96.7$^\circ$) / 1.45 / 0.6 / $<$32$^{c}$ / ... / |
| CH3OH 5_1-4_1 (A-) line flux 3-sigma upper limit | <62 | not stated | mJy km/s | 6 | 243.9157 / nat / 0.60$''$$\times$0.49$''$ (107.0$^\circ$) / 1.38 / 0.7 / $<$62$^{c}$ / ... / |
| c-C3H2 7_16-7_07 line flux 3-sigma upper limit | <29 | not stated | mJy km/s | 6 | 218.7327 / nat / 0.57$''$$\times$0.52$''$ (100.8$^\circ$) / 1.00 / 0.9 / $<$29$^{c}$ / ... / |
| Radius of peak integrated intensity, 12CO 3-2 | 0.40 | 0.03 | arcsec | 11 | 0.11$''$$\times$0.10$''$ (90.3$^\circ$) / 0.40 / 0.03 / 57.1 / |
| Radius of peak integrated intensity, 12CO 2-1 | 0.42 | 0.09 | arcsec | 11 | 0.37$''$$\times$0.33$''$ (67.1$^\circ$) / 0.42 / 0.09 / 46.0 / |
| Radius of peak integrated intensity, 13CO 2-1 | 0.54 | 0.10 | arcsec | 11 | (69.6$^\circ$) / 0.54 / 0.10 / 17.0 / |
| Radius of peak integrated intensity, C18O 2-1 | 0.64 | 0.10 | arcsec | 11 | (68.3$^\circ$) / 0.64 / 0.10 / 5.6 / |
| Radius of peak integrated intensity, H2CO 3_03-2_02 | 0.55 | 0.10 | arcsec | 11 | (69.0$^\circ$) / 0.55 / 0.10 / 5.4 / |
| Radius of peak integrated intensity, C2H | 0.63 | 0.10 | arcsec | 11 | (107.7$^\circ$) / 0.63 / 0.10 / 6.8 / |
| Radius of peak integrated intensity, c-C3H2 3_21-2_12 | 0.93 | 0.27 | arcsec | 11 | (104.6$^\circ$) / 0.93 / 0.27 / 0.1 / |
| Radius of peak integrated intensity, H13CN 3-2 | 0.44 | 0.10 | arcsec | 11 | (107.1$^\circ$) / 0.44 / 0.10 / 4.4 / |
| Radius of peak integrated intensity, DCN 3-2 | 0.45 | 0.10 | arcsec | 11 | (70.8$^\circ$) / 0.45 / 0.10 / 2.7 / |
| Radius of peak integrated intensity, HCO+ 4-3 | 0.45 | 0.05 | arcsec | 11 | (73.1$^\circ$) / 0.45 / 0.05 / 23.4 / |
| Radius of peak integrated intensity, H13CO+ 3-2 | 0.54 | 0.10 | arcsec | 11 | (108.8$^\circ$) / 0.54 / 0.10 / 3.3 / |
| Radius of peak integrated intensity, CS 5-4 | 1.09 | 0.10 | arcsec | 11 | (108.8$^\circ$) / 1.09 / 0.10 / 2.7 / |
| H2CO excitation temperature range | ~10-40 | large (low snr) | K | 8 | The excitation temperature ranges between $\sim10-40\,$K, with the temperature decreasing in the outer disk regions. |
| H2CO column density across 0.5''-2'' | 10^13-10^14 | not stated | cm^-2 | 8 | Column densities across the $0.5-2\ensuremath{''}$ interval range between $10^{13}-10^{14}\,$cm$^{-2}$ |
| Peak N(C18O) at Tex 30 K | 6.2e15 | +0.2/-2.8 e15 | cm^-2 | 8 | 28.81 / $6.2^{+0.2}_{-2.8} \times10^{15}$ / $9.8^{+0.02}_{-0.41} \times10^{-1}$ / |
| Peak optical depth tau(C18O 2-1) | 0.98 | +0.02/-0.41 (in 1e-1 units: 9.8) | dimensionless | 8 | 28.81 / $6.2^{+0.2}_{-2.8} \times10^{15}$ / $9.8^{+0.02}_{-0.41} \times10^{-1}$ / |
| Peak N(H2CO) (Tex fitted) | 8.4e13 | +1.8/-1.4 e13 | cm^-2 | 8 | 361.72 / $8.4^{+1.8}_{-1.4} \times10^{13}$ / $8.8^{+11.3}_{-5.8} \times10^{-1}$ / |
| Peak N(C2H) from J=7/2-5/2 F=4-3 (Tex 30 K) | 2.0e14 | +0.5/-0.1 e14 | cm^-2 | 8 | 144.71 / $2.0^{+0.5}_{-0.1} \times10^{14}$ / $3.5^{+0.2}_{-1.1} \times10^{-2}$ / |
| Peak N(C2H) from J=7/2-5/2 F=3-2 (Tex 30 K) | 3.4e14 | +2.0/-1.5 e14 | cm^-2 | 8 | 144.71 / $3.4^{+2.0}_{-1.5} \times10^{14}$ / $7.4^{+1.7}_{-1.8} \times10^{-2}$ / |
| Peak N(C2H) from J=5/2-3/2 F=3-2 (Tex 30 K) | 1.8e14 | +0.3/-0.1 e14 | cm^-2 | 8 | 144.71 / $1.8^{+0.3}_{-0.1} \times10^{14}$ / $3.8^{+2.2}_{-0.1} \times10^{-2}$ / |
| Disk-averaged N(c-C3H2) (r=3'', Tex 20-50 K) | 5.7e12 | +4.0/-1.6 e12 | cm^-2 | 8 | A column density of $5.7^{+4.0}_{-1.6}\times10^{12}$ cm$^{-2}$ is obtained |
| Peak N(H13CN) (Tex 30 K) | 5.4e12 | +0.4/-1.3 e12 | cm^-2 | 8 | 109.62 / $5.4^{+0.4}_{-1.3} \times10^{12}$ / $6.9^{+3.0}_{-3.0} \times10^{-1}$ / |
| Peak N(HC15N) (Tex 30 K) | 1.1e12 | +0.2/-0.1 e12 | cm^-2 | 8 | 36.66 / $1.1^{+0.2}_{-0.1} \times10^{12}$ / $1.4^{+1.2}_{-0.5} \times10^{-1}$ / |
| Peak N(DCN) (Tex 30 K) | 3.7e12 | +0.5/-0.3 e12 | cm^-2 | 8 | 130.51 / $3.7^{+0.5}_{-0.3} \times10^{12}$ / $3.6^{+3.7}_{-1.4} \times10^{-1}$ / |
| Peak N(H13CO+) (Tex 30 K) | 2.2e12 | +0.3/-0.1 e12 | cm^-2 | 8 | 36.37 / $2.2^{+0.3}_{-0.1} \times10^{12}$ / $4.9^{+4.7}_{-1.9} \times10^{-1}$ / |
| Peak N(CS) (Tex 30 K) | 1.0e13 | +2.6/-0.6 e13 | cm^-2 | 8 | 64.15 / $1.0^{+2.6}_{-0.6} \times10^{13}$ / $5.0^{+4.8}_{-1.8} \times10^{-1}$ / |
| Disk-averaged N(CS) used for the CS/SO ratio | 1.8e12 | +0.4/-0.2 e12 (as printed: +0.4, 0.2) | cm^-2 | 10 | the disk averaged CS column density of $1.8^{+0.4}_{0.2}\times10^{12}$ cm$^{-2}$ |
| N(SO) disk-averaged 3-sigma upper limit from SO 7_6-6_5 (Table 4) | <1.5e10 | not stated | cm^-2 | 8 | 197.51 / $<1.5\times10^{10}$ / ...$^c$ / |
| N(CH3OH) disk-averaged upper limit from 5_1-4_1 (A-) | <6.5e12 | not stated | cm^-2 | 8 | 731.07 / $<6.5 \times10^{12}$ / ...$^c$ / |
| Disk-averaged H/D from H13CN/DCN | 60 | 17 | dimensionless | 9 | The derived disk averaged H/D and $^{14}$N/$^{15}$N in HCN isotopologues are $60\pm17$ and $111\pm27$, respectively |
| Disk-averaged 14N/15N from H13CN/HC15N | 111 | 27 | dimensionless | 9 | The derived disk averaged H/D and $^{14}$N/$^{15}$N in HCN isotopologues are $60\pm17$ and $111\pm27$, respectively |
| Ratio of C2H 3-2 J=7/2-5/2 F=4-3 to 13CO 2-1 across the disk out to ~2'' | 0.25-0.35 | not stated | dimensionless | 10 | For PDS 70, this ratio ranges between 0.25-0.35 throughout the whole disk out to $r\sim2\ensuremath{''}$ |
| Lower limit on N(CS)/N(SO) | >~109 | not stated | dimensionless | 10 | we obtain a lower limit on the $N$(CS)/$N$(SO) ratio of $\sim109$. |

## Qualitative findings

- All detected lines show a large central cavity; only 12CO and HCO+ trace gas inside the planet-carved gap, while other lines show a bright ring outside the planet orbits  
  > "Only the two $^{12}$CO and the HCO$^+$ lines are associated with emission from gas within the cavity carved by planets b and c." (Conclusions)
- Most lines peak inside the radial maximum of the sub-mm continuum; only CS and c-C3H2 peak outside the continuum ring  
  > "The only two exceptions are CS and c-C$_3$H$_2$, peaking at $r\gtrsim0.9\ensuremath{''}$ outside the continuum ring" (Comparing mm Continuum, IR Scattered Light and Molecular Emission Profiles)
- H2CO shows a shoulder of emission outside the continuum ring at 1-1.5''  
  > "The H$_2$CO line shows a shoulder of emission outside the continuum ring between 1-$1.5\ensuremath{''}$" (Radial profiles)
- HCN deuteration and 15N fractionation both increase radially outward  
  > "Both D/H and $^{14}$N/$^{15}$N profiles show some radial dependence, with enhanced deuteration and nitrogen fractionation in outer regions of the disk." (Deuteration and N fractionation)
- An inner disk is detected in the 1.33 mm continuum only at limited significance (outer ring contributes at the cavity centre)  
  > "We detect an inner disk in the 1.33 mm image, even though the outer ring still contributes to the observed intensity at the center of the cavity" (Continuum)

## Claim tuples

- H: Which molecules does the PDS 70 disk host at ~0.4''-0.5'' resolution? | E: Band 6 spectral scans of two setups plus archival Band 7 data, stacked spectra, channel maps and a matched filter | R: 16 transitions of 12 species detected; SO and CH3OH not detected | F: A first chemical inventory of PDS 70 with CO isotopologues, H2CO, C2H, c-C3H2, HCN and HCO+ isotopologues and CS | **supported**
- H: Do molecular lines trace the planet-sculpted gas and dust structure differently? | E: Radial profiles of integrated intensity and radius of peak compared with the 855 micron continuum and J-band scattered light | R: Lines peak at different radii; most inside the mm ring, CS and c-C3H2 outside; HCN and HCO+ isotopologues peak with the scattered light | F: Emission is set by an interplay of density, temperature and illumination; C18O traces bulk density while HCN and HCO+ trace the illuminated cavity wall | **supported**
- H: Does HCN deuteration and 15N fractionation vary radially in PDS 70? | E: H13CN/DCN and H13CN/HC15N column density ratios in smoothed maps with fixed Tex of 30 K and 12C/13C of 68 | R: Disk-averaged H/D = 60 +/- 17 and 14N/15N = 111 +/- 27, increasing radially | F: Radially increasing fractionation, suggesting low-temperature exchange reactions outside the cavity wall | **supported**
- H: Is the disk gas accreted by the planets carbon rich? | E: Comparison of the C2H flux, the C2H/13CO ratio and the N(CS)/N(SO) lower limit with literature thermochemical model grids | R: C2H/13CO = 0.25-0.35 (criterion 0.2); N(CS)/N(SO) > ~109 versus ~10 for C/O~1 | F: Molecular layer C/O > 1, qualitative evidence for accretion of high C/O gas by the planets | **supported**
- H: What are the column densities and excitation of the detected molecules? | E: emcee fits with optical depth correction; H2CO two-line Tex fit, fixed Tex 20-50 K for others | R: H2CO Tex ~10-40 K and N ~1e13-1e14 cm^-2; other columns 1e12-1e15 cm^-2 (Table 4); upper limits on SO and CH3OH | F: Column densities and optical depths derived for all detected molecules, upper limits for non-detections | **supported**

## Reasoning

- Why this data: PDS 70 hosts two directly imaged accreting planets and a well-characterised disk, making it the best case to link planets and their host environment  
  > "PDS 70 thus provides the best candidate where to establish a link between massive protoplanets and their host environment" (Introduction)
- Why this method: Spectral setup built to target simple molecules because complex organics are hard to detect in disks  
  > "The spectral setup was built to target simple molecules, since complex organic molecules (COMs) are difficult to detect in in protoplanetary disks due to the low temperatures and large partition functions of the numerous transitions." (Line fluxes)
- Alternative: Other weightings (low-robust Briggs, uniform) did not give an inner-disk detection because of lower angular resolution  
  > "Different imaging parameters aimed at suppressing the side-lobes of the PSF (e.g. Briggs weighting with low robust values, or `uniform` weighting) do not lead to a detection of the inner disk" (Continuum)
- Alternative: GoFish stacking-based radial profiles tested but integrated-intensity-map profiles preferred  
  > "Since most of the analysis in the paper focuses on the inner two-three beams, radial profiles from integrated intensity maps were preferred." (Radial profiles with GoFish)
- Alternative: Standard hyperfine-fitting methods not usable for C2H because of blending  
  > "were sufficiently blended that typical hyperfine-fitting methods" (C2H)
- How they decided it was enough: Imaging parameters chosen per line as a compromise among resolution, intensity and channel spacing after multiple imaging runs  
  > "multiple imaging runs have been performed on each line to obtain the best compromise between angular resolution, intensity and channel spacing." (Observations and data reduction)
- Limitation (authors): Literature C/O models are tuned for disks without large cavities; a PDS 70-specific forward model is needed  
  > "However, we note that all these models have been fine tuned for disks that do not exhibit a large cavity, as is the case for PDS 70." (C/O ratio); "Thermo-chemical models of PDS 70 are needed to extract a more quantitative conclusion." (C/O ratio)
- Limitation (authors): Fractionation conclusions depend on assumed uniform carbon fractionation  
  > "We thus caution that our conclusions about deuteration and nitrogen fractionation may be affected by the carbon fractionation profile, were this not uniform" (Deuteration and N fractionation)
- Limitation (authors): Long-baseline (0.1'') data not yet taken; resolution only ~50 au  
  > "for which the long baseline data have not been taken yet." (Observations and data reduction)
- Caveat (inferred, ours): Table 2 and text disagree for 12CO 3-2 (12421 +/- 147 vs 12.3 +/- 0.1 Jy km/s) and for c-C3H2 flux uncertainty (11 vs 14 mJy km/s).
- Caveat (inferred, ours): SO column-density upper limit is 1.5e10 cm^-2 in Table 4 but 1.5e11 in the text; the N(CS)/N(SO) ~109 limit depends on which is right.
- Caveat (inferred, ours): Flux calibrator written as J1427-4206 in Table 1 and J1427-4207 in the text.
- Caveat (inferred, ours): Disk-averaged N(CS)=1.8e12 cm^-2 used in the CS/SO ratio differs from the peak 1.0e13 in Table 4 without explanation.
- Caveat (inferred, ours): Single-transition columns assume LTE and fixed Tex of 20-50 K; beam of ~50 au does not resolve planet orbits.
- Caveat (inferred, ours): C/O > 1 relies on qualitative comparison with models not tuned to cavity disks.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Image/cell sizes, clean thresholds and multiscale scales for all cubes
- Missing: Line-free channels for uvcontsub
- Missing: Keplerian mask parameters
- Missing: Per-EB flux scaling and calibrator fluxes
- Missing: Priors/likelihood for column-density fits and the Delta v, Omega used
- Missing: Treatment of the Band 7 data beyond reference to Isella+2019 and Keppler+2019
- Data volume (inferred): Roughly tens to ~100 GB raw for four Band 6 execution blocks (16 spws up to 1920 channels), plus Band 7 archival data from two programs
- Score (inferred): 3/5, Project codes and many processing parameters (self-cal intervals, robust values, weighting per line, integration windows, Tex grid, emcee set-up) are given and results are numeric, but cell/image sizes, masks, line-free channels, flux factors and priors are missing and several numbers are inconsistent between text and tables.
- Rediscovery candidate: yes, Band 6 data from a single program (2019.1.01619.S) are expected to be archive-public, the line-flux and column-density recipe is largely given and results are numeric, though several imaging details would need to be inferred.

## Links

- Method: Andrews et al. 2018 (DSHARP) (cite: andrews18) (self-calibration and flux-offset procedure followed)
- Method: Isella et al. 2019 (cite: isella19) (calibration of the Band 7 data and 0.85 mm flux density)
- Method: Keppler et al. 2019 (cite: keppler19) (disk geometry, kinematics and elevated surface used for masks and stacking)
- Method: Bergner et al. 2020 (cite: bergner2020) (procedure for HCN-isotopologue fractionation ratios)
- Method: Teague et al. 2016 (cite: Teague16) (line stacking technique)
- Method: Loomis et al. 2018 (cite: loomis2018) (emcee-based column density and Tex approach)
- Companion: Keppler et al. 2019 (cite: keppler19) (earlier ALMA Band 7 study of PDS 70 gas and dust)
- Companion: Isella et al. 2019 (cite: isella19) (re-analysis of ALMA 0.85 mm data and Band 7 calibration)
- Companion: Wang et al. 2021 (cite: wang_ea_2021) (planet orbits and atmosphere characterisation)
- Related: DSHARP
- Related: Lupus C2H survey (Miotello et al. 2019)
- Related: Planned long-baseline (0.1'') ALMA program for PDS 70

## Checks

```json
{
 "quotes": 262,
 "quotes_ok": 262,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 62,
 "numeric_problems": 0,
 "fill": {
  "facts": 151,
  "stated": 126,
  "rate": 0.834
 },
 "evidence_ok": true
}
```
