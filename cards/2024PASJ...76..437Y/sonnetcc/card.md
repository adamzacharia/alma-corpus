# ALMA 2D super-resolution imaging of Taurus-Auriga protoplanetary disks: Probing statistical properties of disk substructures

`2024PASJ...76..437Y` | Publications of the Astronomical Society of Japan 2024 | first author: Yamaguchi, Masayuki | arXiv: 2404.13570 | DOI: 10.1093/pasj/psae022

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: What are the statistical properties of gaps and rings in the substructures of 43 Taurus-Auriga disks, as seen in 2D super-resolution (sparse modeling) images of archival ALMA Band 6 continuum data, and what do they imply for their origin (planet-disk interaction)?  
  > "Their origin may be probed through statistical studies on the physical properties of the substructures." (abstract); "We employ a novel 2D super-resolution imaging technique based on sparse modeling to obtain images with high fidelity and spatial resolution." (abstract)
- Target **43 Taurus-Auriga disks (39 Class II and 4 Herbig Ae), e.g. AB Aur, GM Aur, CI Tau, DL Tau, DM Tau, LkCa 15, AA Tau, GO Tau, MWC 480, MWC 758, CQ Tau, RW Aur**: coordinates _not stated_; z/distance ~140 pc (Taurus-Auriga); per-target Gaia DR2 distances are in a table not reproduced in the text  
  > "Consequently, we have in total 43 YSOs that comprise 29 single stars, 12 stars within binary or multiple systems with large ($> 50$ au) separation, and two spectroscopic binaries" (Source Selection); "At the distance of 140 pc (e.g., Taurus-Auriga region; (cite: Galli2018))" (Introduction); "DR2 parallax (cite: Gaia2016; Gaia2018)" (Table of stellar properties (note)); distance from Gaia DR2 parallax (cite: Gaia2016; Gaia2018); region distance (cite: Galli2018)  
  > "Consequently, we have in total 43 YSOs that comprise 29 single stars, 12 stars within binary or multiple systems with large ($> 50$ au) separation, and two spectroscopic binaries" (Source Selection); "At the distance of 140 pc (e.g., Taurus-Auriga region; (cite: Galli2018))" (Introduction); "DR2 parallax (cite: Gaia2016; Gaia2018)" (Table of stellar properties (note))

## Data provenance

- ALMA projects: 2013.1.00105.S, 2013.1.00498.S, 2013.1.01070.S, 2015.1.00889.S, 2015.1.01207.S, 2015.1.01268.S, 2016.1.00724.S, 2016.1.00846.S, 2016.1.01164.S, 2016.1.01205.S, 2016.1.01370.S, 2016.A.00026.S, 2017.1.00940.S, 2017.1.01151.S, 2017.1.01404.S, 2017.1.01460.S, 2017.1.01631.S, 2018.1.00945.S, 2018.1.01230.S, 2018.1.01255.S, 2018.1.01631.S, 2018.1.01755.S, 2018.1.01829.S, 2019.1.00579.S, 2019.1.01108.S
- bands: Band 6 (1.1-1.3 mm) continuum  
  > "The total flux density at Band 6 (1.1-1.3 mm) spans the wide range of $10-300$ mJy." (Source Selection); "All target sources are taken from Band 6 observations." (Table of observations (note))
- frequencies and spectral setup: Central observing frequency per target, 224-261 GHz (e.g. 226 GHz AB Aur, 261 GHz GM Aur, 225 GHz for most); spectral window layout not stated  
  > "(2) Observing central frequency in GHz. All target sources are taken from Band 6 observations." (Table of observations (note))
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Long-baseline data; compact-configuration data combined when MRS is smaller than the radii of known gap and ring features  
  > "If MRS is smaller than the radii of the known gap and ring features of the objects, we combine the data of the compact array configuration." (Data Reduction and CLEAN Imaging)
- baselines: Per-target ranges; overall 15-16196 m (e.g. AB Aur 15-16196 m; DL Tau 17-3638 m)  
  > "(3) Range of baseline lengths (BL) in meters from minimum to maximum lengths." (Table of observations (note))
- angular resolution: CLEAN beams listed per target in a table not reproduced; SpM effective resolution 0''.02-0''.1, 2-3 times better than CLEAN  
  > "we have obtained images with spatial resolutions comparable to a few au ($0''.02 - 0''.1$), which is two to three times better than conventional CLEAN methods" (abstract)
- max recoverable scale: Per-target MRS 1.0-5.1 arcsec (AA Tau 1.0; AB Aur 5.1)  
  > "(4) Maximum recoverable scale (MRS) in arc-second of data sets." (Table of observations (note))
- sensitivity: Selection requires CLEAN-image SNR better than 30; per-target CLEAN rms (sigma_cl) and SpM detection threshold (I_DT) are tabulated per target  
  > "The ALMA data should have Signal-to-Noise Ratios (SNRs) better than 30 in the CLEAN image domain" (Source Selection)
- time on source: Per-target total on-source time 1.4-361.7 min (IQ Tau 1.4; MWC 758 361.7)  
  > "(5) Total on-source time (OST) in minutes." (Table of observations (note))
- observing dates: _not stated_
- pi or archival as stated: Archival ALMA data (one CW Tau data set supplied by T. Ueda)  
  > "We present the analyses of archival ALMA Band 6 continuum data of 43 disks" (abstract); "Takahiro Ueda for giving us the ALMA data of CW Tau." (Acknowledgments)
- Other facility **SMA (Andrews2013 survey)**: Total 1.3 mm-band fluxes for 41 Class II disks used to check ALMA total fluxes  
  > "We take the total fluxes taken by the SMA (cite: Andrews2013) for 41 Class II disks" (Comparison with Other Telescopes)
- Other facility **Plateau de Bure Interferometer**: Total fluxes for the Herbig disks CQ Tau and MWC 758  
  > "those by the Plateau de Bure Interferometer (cite: Chapillon2008) for the two Herbig disks of CQ Tau and MWC 758" (Comparison with Other Telescopes)
- Other facility **IRAM 30m**: Single-dish total flux densities for 21 single-star disks, used to estimate envelope-scale emission  
  > "obtained by the IRAM 30m single-dish telescope" (Comparison with Other Telescopes); "we use the data only for 21 disks with single-star systems to avoid contamination by dust emission from companions" (Comparison with Other Telescopes)
- Other facility **Gaia DR2**: Distances to the host stars  
  > "DR2 parallax (cite: Gaia2016; Gaia2018)" (Table of stellar properties (note))
- External data: SMA total flux densities of Taurus Class II disks  
  > "We take the total fluxes taken by the SMA (cite: Andrews2013) for 41 Class II disks" (Comparison with Other Telescopes) [from (cite: Andrews2013)]
- External data: PdBI fluxes for CQ Tau and MWC 758  
  > "those by the Plateau de Bure Interferometer (cite: Chapillon2008) for the two Herbig disks of CQ Tau and MWC 758" (Comparison with Other Telescopes) [from (cite: Chapillon2008)]
- External data: IRAM 30m single-dish flux densities  
  > "obtained by the IRAM 30m single-dish telescope" (Comparison with Other Telescopes) [from (cite: Beckwith1990; Osterloh1995)]
- External data: Spectral indices used to scale AA Tau (1.2 mm) and GM Aur (1.1 mm) fluxes to 1.3 mm: 1.6 and 2.7  
  > "applying spectral indices $\alpha_{\rm mm}$ of 1.6 for AA Tau (cite: Andrews2005) and 2.7 for GM Aur (cite: Huang2020)" (Comparison with Other Telescopes) [from (cite: Andrews2005); (cite: Huang2020)]
- External data: Stellar masses (dynamical where measured, otherwise evolutionary-track), spectral types and luminosities  
  > "We use dynamical stellar masses. For stars not measured dynamical masses, we use stellar masses derived from an evolutionary track model." (Table of stellar properties (note)) [from References (a)-(k) in the stellar-property table note: Vioque2018, Herczeg2014, Kenyon2008, Simon2019, Akeson2019, Braun2021, Long2019, Vieira2003, Podio2013, Kraus2009, Mora2001]
- External data: Inclination and position angle from molecular-line Keplerian rotation for AB Aur, MWC 758 and CQ Tau  
  > "“R” indicates the use of references taken from Keplerian rotation with molecular line observations; AB Aur (cite: Tang2017), MWC 758 (cite: Isella2010mwc758; Boehler2018), and CQ Tau (cite: Ubeira2019)." (Table of stellar properties (note)) [from (cite: Tang2017); (cite: Isella2010mwc758; Boehler2018); (cite: Ubeira2019)]
- External data: Near-infrared-excess TD/PTD classification used to compare with the paper's own TD/PTD labels  
  > "Here, we have used the TD/PTD classification based on infrared presented in (cite: Francis2020)." (Ring-cavity) [from (cite: Francis2020)]
- External data: ALMA fluxes of DK Tau A and V710 Tau A at the same wavelength used to check the SMA discrepancy  
  > "have obtained the total flux values that are consistent with our results within $10\%$ for the two disks (cite: Rota2022)" (Comparison with Other Telescopes) [from (cite: Rota2022)]
- External data: Gap-width/depth/planet-mass scaling relations and constants A, B (tabulated) of the planet-disk interaction model  
  > "where the parameters $A$ and, $B$ are the parameters that appear in Equation" (Inferred Planet Mass in Gap Structure); "We follow the methods outlined in (cite: Zhang2018)" (Inferred Planet Mass in Gap Structure) [from (cite: Zhang2018)]
- External data: Upper-limit planet-mass formula for narrow gaps  
  > "the empirical relationship between planet mass and gap width (Equation 5 in (cite: Kanagawa2016))" (Implication of planet formation) [from (cite: Kanagawa2016)]
- External data: Dust opacity 0.43 cm2/g (DSHARP model, s_max = 0.1 mm, 1.3 mm)  
  > "which is the value of DSHARP opacity model (cite: Birnstiel2018) with $s_{\mathrm{max}} = 0.1$ mm at $\lambda=1.3$ mm" (Inferred Planet Mass in Gap Structure) [from (cite: Birnstiel2018)]
- External data: Envelope dust temperature 15 K and opacity 0.023 cm2/g  
  > "Assuming that the gas and dust are at the same temperature of $T = 15$ K (cite: Federman2023)" (Remnants of Dust Envelope); "the opacity of $\kappa_{\nu} = 0.023$ cm$^{2}$ g$^{-1}$ (cite: Beckwith1991)" (Remnants of Dust Envelope) [from (cite: Federman2023); (cite: Beckwith1991)]
- External data: Maximum grain size 0.1 mm adopted from ALMA observations  
  > "based on ALMA observations by (cite: Bacciotti2018)" (Possible Origin of Gap Formation) [from (cite: Bacciotti2018)]
- Simulation/model as data: Planet-disk interaction model of Zhang et al. (2018, DSHARP DSD1 model) predicting the gap depth vs normalized width relation, compared with observed gaps  
  > "The planet-disk interaction model outlined in (cite: Zhang2018) predicts the relationship between the gap depth" (Possible Origin of Gap Formation)
- Simulation/model as data: Secular gravitational instability criterion (ring spacing over gap scale height < 3.6) from Tominaga et al.  
  > "falls below a threshold of 3.6" (Possible Origin of Gap Formation)

## Processing

### Calibration

- pipeline or manual: ALMA Regional Center CASA pipeline reduction scripts  
  > "The data were initially calibrated with the $\tt CASA$ pipeline reduction scripts provided by the ALMA Regional Centers." (Data Reduction and CLEAN Imaging)
- casa version: Pipeline calibration: different CASA versions (not listed); self-calibration and CLEAN imaging in CASA 6.1.0  
  > "Given that the data were obtained over a period of several years, different versions of $\tt CASA$ were used for these calibrations." (Data Reduction and CLEAN Imaging); "using a CLEAN model as a reference calibrator in the $\tt CASA$ version 6.1.0 environment" (Data Reduction and CLEAN Imaging)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% absolute calibration error adopted for ALMA flux densities  
  > "The uncertainty is the $10\%$ absolute calibration error for ALMA observations." (Table of full sample (note))
- self calibration: Initial CLEAN SNR > 100: phase-only solint=inf, phase-only solint=OST/5, then amplitude+phase solint=OST/5. Initial SNR < 100: phase-only solint=inf, then amplitude+phase solint=OST/5. Final CLEAN image = best SNR among rounds  
  > "we conducted two rounds of phase calibration ($\tt calmode = p$) with different integration times: $\tt solint = inf$ and $\tt solint =$ OST/5, where OST indicates on-source time" (Data Reduction and CLEAN Imaging); "We then performed one round of amplitude and phase calibration ($\tt calmode = ap$) with an integration time of $\tt solint$=OST/5." (Data Reduction and CLEAN Imaging); "For data with initial SNR less than 100, we applied one round of phase calibration with an integration time of $\tt solint = inf$, followed by one round of amplitude and phase self-calibration" (Data Reduction and CLEAN Imaging)

### Imaging

- task: CASA tclean for CLEAN images and self-cal models; PRIISM for sparse-modeling images  
  > "The CLEAN model was generated through the $\tt tclean$ task (hereafter referred to as CLEAN)." (Data Reduction and CLEAN Imaging)
- deconvolver: Cotton-Schwab for disks without substructure; multi-scale CLEAN for disks with substructure; nterm = 1 multi-frequency synthesis  
  > "We consistently employed multi-frequency synthesis ($\tt nterm = 1$; (cite: Rau2011))" (Data Reduction and CLEAN Imaging); "the Cotton–Schwab algorithm (cite: Schwab1984) for disks lacking substructures, such as gaps or rings" (Data Reduction and CLEAN Imaging)
- weighting robust: Briggs, robust = 0.5 (all images)  
  > "applied Briggs weighting with $\tt robust = 0.5$" (Data Reduction and CLEAN Imaging)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: [0, 1, 3] x CLEAN beam size (theta_cl)  
  > "a multi-scale approach (cite: Cornwell2008) with scale parameters of $[0, 1, 3] \theta_{\rm cl}$ (where $\theta_{\rm cl}$ represents the CLEAN beam size) for disks with substructures" (Data Reduction and CLEAN Imaging)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Compact-configuration data combined with long-baseline data when MRS < radii of known gap/ring features; phase centers aligned with fixvis and fixplanets  
  > "If MRS is smaller than the radii of the known gap and ring features of the objects, we combine the data of the compact array configuration." (Data Reduction and CLEAN Imaging); "the datasets from different observations are assigned to a common phase center using task $\tt fixplanets$" (Data Reduction and CLEAN Imaging)
- smoothing: _not stated_
- final beam: Listed per target (CLEAN beam, peak, rms) in the full-sample table; values not in the provided text  
  > "The final CLEAN beam size $\theta_{\rm cl}$, peak intensity, and RMS noise level $\sigma_{\rm cl}$ (collected noise value from the dust emission-free area)" (Data Reduction and CLEAN Imaging)
- final rms: CLEAN rms taken from dust-emission-free area, listed per target; SpM uses detection threshold I_DT (maximum of emission-free area) instead of rms  
  > "$I_{\rm DT}$ is the maximum intensity on the emission-free area, while $\sigma_{\rm cl}$ is the RMS value in the emission-free area" (Evaluation of Noise Levels in Images)

### Inherited from earlier work

- Self-calibration to improve SNR  
  > "We then applied self-calibration to improve SNR (cite: Richards2022)" (Data Reduction and CLEAN Imaging) [from (cite: Richards2022)]
- Flux rescaling of long-baseline data with the DSHARP rescale_flux function (script publicly available)  
  > "After the coordinates of each dataset were corrected, the visibility of long baseline data was re-scaled using the DSHARP" (Data Reduction and CLEAN Imaging) [from (cite: Andrews2018a)]
- l1+TSV sparse-modeling imaging with 10-fold cross-validation scheme  
  > "in conjunction with $\tt CASA$ to perform $\ell _1$+TSV imaging and the cross-validation (CV) scheme as illustrated in (cite: Yamaguchi2021)" (Imaging with Sparse Modeling) [from (cite: Yamaguchi2021)]
- Point-source injection method for effective resolution  
  > "method outlined in (cite: Yamaguchi2021)" (Imaging with Sparse Modeling) [from (cite: Yamaguchi2021)]
- Cross-check method for image fidelity (short-baseline SpM vs long-baseline CLEAN)  
  > "wherein a comparison is made between the CLEAN image derived from the visibility data including the long baseline observations" (Image Fidelity) [from (cite: Yamaguchi2020)]
- Curve-of-growth method for dust disk radius  
  > "We use the curve of growth method (e.g., (cite: Ansdell2016)) to measure the dust disk radius" (Disk Size and Total Flux Density) [from (cite: Ansdell2016)]
- Gap edge definition via I_edge midpoint of ring and gap intensities  
  > "In previous studies (e.g., (cite: Huang2018; Zhang2018)), the location of the outer gap edge" (Gap Width and Depth) [from (cite: Huang2018; Zhang2018)]
- Ring (B) and gap (D) labelling notation  
  > "Following the notation of (cite: ALMAPartnership2015), we label the ring features with" (Definition of Rings, Gaps, and Inflections) [from (cite: ALMAPartnership2015)]
- Size-luminosity check with cos i rescaling  
  > "Following their approach, we checked the correlation between the disk size and the luminosity re-scaled by $\cos i$" (Relation of Flux and Disk Size) [from (cite: Tazzari2021)]
- Planet mass from gap width following the DSHARP planet-disk scheme  
  > "We follow the methods outlined in (cite: Zhang2018)" (Inferred Planet Mass in Gap Structure) [from (cite: Zhang2018)]
- Envelope temperature assumption  
  > "Assuming that the gas and dust are at the same temperature of $T = 15$ K (cite: Federman2023)" (Remnants of Dust Envelope) [from (cite: Federman2023)]

### Not stated but needed to reproduce (our reading)

- Which CASA pipeline version was used for each of the 25 projects, and which execution blocks were taken (including which compact-configuration data sets were combined for which targets).
- tclean settings: cell size, image size, threshold/niter, CLEAN masks, spectral-window/continuum channel selection, and the per-target self-calibration rounds actually kept.
- PRIISM settings: image grid (pixel size, field of view), per-target (log Lambda_l, log Lambda_tsv) grid ranges and CV details; final pairs are in a table not reproduced in the text.
- Per-target phase-center offsets and the reference execution block used for the DSHARP rescale_flux flux correction.
- Definition of the emission-free area used for sigma_cl and I_DT, and which spectral windows were averaged for the visibility profiles.
- Radial-profile bin width, smoothing and derivative scheme used to compute D(r), and kneed parameters (curve type, sensitivity) for inflection points.
- Linmix priors and run settings for the Bayesian regressions.
- Per-target inclination, position angle, stellar mass and luminosity values (in tables) needed for deprojection and temperature/aspect-ratio calculations.
- The CW Tau data set was supplied by a colleague and is not identified by project code.

## Analysis recipe

1. **Select the sample**: Choose Taurus-Auriga Class II/Herbig Ae stars with existing Band 6 data better than 0''.2 resolution, then apply spectral type, multiplicity and SNR cuts  
  > "We select targets from those in the Taurus-Auriga region that are identified as Class II YSOs or Herbig Ae stars (cite: Rebull2010; Luhman2010; Vioque2018) with existing ALMA Band 6 data at spatial resolutions higher than $0''.2$." (Source Selection)
   - parameter: Spectral type M3 to A1  
  > "The spectral type of M3 to A1 (cite: Mora2001; Herczeg2014)" (Source Selection)
   - parameter: Single stars or primaries with companion separation > 0''.4 (~50 au)  
  > "Single stars or the primary stars of binary/multiple systems with separation larger than $0''.4$ ($\sim$50 au)" (Source Selection)
   - parameter: CLEAN-image SNR > 30  
  > "The ALMA data should have Signal-to-Noise Ratios (SNRs) better than 30 in the CLEAN image domain" (Source Selection)
   - assumption: Distance ~140 pc for the region  
  > "At the distance of 140 pc (e.g., Taurus-Auriga region; (cite: Galli2018))" (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Calibrate, align and flux-scale the visibilities**: Use ARC CASA pipeline calibration, combine compact data if MRS too small, shift/align phase centers, rescale long-baseline flux with DSHARP function  
  > "The data were initially calibrated with the $\tt CASA$ pipeline reduction scripts provided by the ALMA Regional Centers." (Data Reduction and CLEAN Imaging); "After the phase center for each dataset is shifted by the $\tt CASA$ task $\tt fixvis$, the datasets from different observations are assigned to a common phase center using task $\tt fixplanets$." (Data Reduction and CLEAN Imaging)
   - software: CASA, fixvis, fixplanets, rescale_flux (DSHARP)
   - parameter: MRS computed from the 5th percentile uv-distance D5 of the long-baseline data  
  > "where $\lambda$ is the observing wavelength and $D_{5}$ is the 5th percentile of $uv$-distance" (Data Reduction and CLEAN Imaging)
   - parameter: Phase center = local CLEAN peak, or ellipse center for ring-like disks  
  > "We use the CLEAN images of each dataset and determine the phase center as the local peak of the emission around the center of the image." (Data Reduction and CLEAN Imaging)
   - fitting: _not stated_
   - validation: _not stated_
3. **Self-calibrate and make CLEAN images**: Self-calibration using a tclean model; Briggs robust 0.5, nterm=1; Cotton-Schwab or multi-scale CLEAN depending on substructure; best-SNR image kept as final CLEAN image  
  > "We consistently employed multi-frequency synthesis ($\tt nterm = 1$; (cite: Rau2011)) and applied Briggs weighting with $\tt robust = 0.5$." (Data Reduction and CLEAN Imaging); "We choose the image with the best SNR among those obtained in the course of self-calibration processes as the final CLEAN image." (Data Reduction and CLEAN Imaging)
   - software: CASA tclean
   - parameter: SNR > 100: 2 phase rounds (solint=inf, OST/5) + 1 amp+phase (OST/5); SNR < 100: 1 phase (inf) + 1 amp+phase (OST/5)  
  > "we conducted two rounds of phase calibration ($\tt calmode = p$) with different integration times: $\tt solint = inf$ and $\tt solint =$ OST/5, where OST indicates on-source time" (Data Reduction and CLEAN Imaging); "For data with initial SNR less than 100, we applied one round of phase calibration with an integration time of $\tt solint = inf$, followed by one round of amplitude and phase self-calibration" (Data Reduction and CLEAN Imaging)
   - parameter: Multi-scale scales [0, 1, 3] x CLEAN beam for disks with substructures  
  > "a multi-scale approach (cite: Cornwell2008) with scale parameters of $[0, 1, 3] \theta_{\rm cl}$ (where $\theta_{\rm cl}$ represents the CLEAN beam size) for disks with substructures" (Data Reduction and CLEAN Imaging)
   - fitting: _not stated_
   - validation: Self-calibration improves SNR by a factor ~1.5 (max baseline ~10 Mlambda) to several (~2 Mlambda) and mitigates patchy artifacts  
  > "We see that the self-calibration process mitigated patchy artifacts outside the region of source emission." (Data Reduction and CLEAN Imaging)
4. **Make sparse-modeling (SpM) images**: PRIISM l1+TSV regularized imaging of self-calibrated visibilities; hyper-parameters (Lambda_l, Lambda_tsv) chosen by 10-fold cross-validation, minimum CV error, with Lambda_tsv raised by one order of magnitude for five disks  
  > "The image was reconstructed by minimizing a cost function, which is the weighted chi-square error between the visibility model derived by the model image and observed visibility" (Imaging with Sparse Modeling); "To select a pair of $(\Lambda_{l}, \Lambda_{tsv})$ for the optimal image, we employ the 10-fold cross-validation (CV) approach" (Imaging with Sparse Modeling)
   - software: PRIISM, CASA
   - parameter: PRIISM version 0.7.2  
  > "ver. 0.7.2 (cite: Nakazato2020) in conjunction with $\tt CASA$ to perform" (Imaging with Sparse Modeling)
   - parameter: DM Tau, GO Tau, DS Tau, DN Tau, RW Aur: Lambda_tsv one order of magnitude larger than the CV minimum  
  > "For five objects (DM Tau, GO Tau, DS Tau, DN Tau, and RW Aur), we conservatively choose the image with $\Lambda_{tsv}$ one order of magnitude larger than $\Lambda_{tsv, \min}$ as optimal." (Imaging with Sparse Modeling)
   - parameter: Visual inspection within delta log Lambda <= 1 of the CV minimum when the minimum-CVE image is patchy  
  > "we visually inspect a set of images obtained by hyper-parameters with $\Delta \log \Lambda_{l}\leq 1$ and $\Delta \log \Lambda_{tsv}\leq 1$" (Imaging with Sparse Modeling)
   - assumption: SpM image has only non-negative intensities  
  > "The SpM image has only positive intensity in the off-source area" (Evaluation of Noise Levels in Images)
   - fitting: Minimum of cross-validation error over the (Lambda_l, Lambda_tsv) grid  
  > "We first find a set of hyper-parameters $(\Lambda_{l,\min}, \Lambda_{tsv,\min})$ which give the minimum cross-validation error (CVE)." (Imaging with Sparse Modeling)
   - validation: SpM total fluxes agree with CLEAN fluxes within 5-10%  
  > "The total fluxes of those SpM images are consistent with those of CLEAN images within $5-10\%$ errors." (Imaging with Sparse Modeling)
5. **Measure effective resolution of SpM images**: Inject an artificial point source into the visibilities, re-image with the same hyper-parameters, fit an elliptical Gaussian to get FWHM = theta_eff  
  > "We inject an artificial point source into the visibility data using the $\tt CASA$ task $\tt addcomponent$, $\tt ft$, and $\tt uvsub$." (Imaging with Sparse Modeling); "We fit it with an elliptical Gaussian function to obtain the Full Width at Half Maximum (FWHM)" (Imaging with Sparse Modeling)
   - software: CASA addcomponent, CASA ft, CASA uvsub, PRIISM
   - parameter: Point-source flux 5% of target total flux, placed north of the star in an emission-free area within MRS  
  > "and its flux is set to be $5\%$ of the total flux density of the target" (Imaging with Sparse Modeling)
   - fitting: Elliptical Gaussian fit to the injected source  
  > "We fit it with an elliptical Gaussian function to obtain the Full Width at Half Maximum (FWHM)" (Imaging with Sparse Modeling)
   - validation: Resolution changes only by a few percent for other injection positions; injected flux recovered within 10%  
  > "the total flux density of the point source is recovered within a $10\%$ error range" (Imaging with Sparse Modeling)
6. **Compare SpM and CLEAN: resolution gain and goodness of visibility fit**: Compute theta_eff/theta_cl for each disk, fit its dependence on CLEAN SNR and disk size; compute reduced chi-square of CLEAN, CLEAN model and SpM images against binned, deprojected real visibilities  
  > "We use the reduced chi-square $\rm Red\chi^2$ as a measure of goodness-of-fit." (Goodness of Visibility Fits); "The observation $O$ and the model $M$ are deprojected in the $uv$ plane (cite: Butler1999) using the disk inclination and position angle" (Radial Visibility Profile)
   - software: NumPy fft, SciPy RectBivariateSpline, Linmix
   - parameter: Re-weighting factor f_i = stddev^-2 / mean weight, typically 0.1-0.3  
  > "The re-weighting factors vary with the observed data and typically fall in the range of $0.1-0.3$" (Radial Visibility Profile)
   - fitting: Linmix Bayesian linear regression in log space  
  > "Using Bayesian linear regression in logarithmic space, this trend can be described as" (Spatial Resolution)
   - validation: SpM gives better chi-square than CLEAN in 40/42 cases; comparable to CLEAN model  
  > "SpM produces a better fit in $95\%$ of the cases (40/42)." (Goodness of Visibility Fits)
7. **Check SpM image fidelity by cross-check**: Compare SpM image of short-baseline data (Data 1) with CLEAN image of long-baseline data (Data 2) for RY Tau, DG Tau, CI Tau; flux of Data 1 SpM scaled to Data 2 CLEAN  
  > "We compare the SpM image of the short baseline data and the CLEAN image of the long baseline data to investigate whether the substructures in the SpM image are real." (Evaluation of Sparse Modeling with Three Disks); "The total flux density of the Data 1 SpM image is scaled to that of the Data 2 CLEAN image to minimize the effects of errors in the flux calibration." (Evaluation of Sparse Modeling with Three Disks)
   - software: PRIISM, CASA
   - fitting: _not stated_
   - validation: Radial profiles agree within ~10% (except ~30% in the RY Tau inner cavity); no artificial gap created in DG Tau  
  > "The profiles of the Data 1 SpM image and the Data 2 CLEAN image agree within $\sim 10\%$, except in the inner cavity of the RY Tau disk" (Evaluation of Sparse Modeling with Three Disks)
8. **Measure disk geometry, total flux and dust radius**: Fit ellipse to outer ring (or elliptical Gaussian to central emission) for inclination/PA, deproject, and use the curve of growth to get total flux and 95% radius  
  > "For disks showing clear ring structures in the outer region, we fit the shape of the ring with an ellipse." (Disk Size and Total Flux Density); "The disk radius $r_{\rm disk}$ is then measured by $0.95~F_{\nu} =  F_{\nu}(r)$." (Disk Size and Total Flux Density)
   - parameter: Radius uncertainty = mean effective resolution /(2 sqrt(2 ln 2))  
  > "We estimate the uncertainty $\sigma_r$ of the disk radius using the effective spatial resolution." (Disk Size and Total Flux Density)
   - fitting: Ellipse fit or elliptical Gaussian fit (algorithm not stated)  
  > "we fit the surface brightness distribution around the central star with an elliptical Gaussian function" (Disk Size and Total Flux Density)
   - validation: _not stated_
9. **Compare total fluxes with other telescopes and fit size-luminosity relation**: Compare ALMA fluxes with SMA, PdBI and IRAM 30m via Monte Carlo flux-ratio histograms; regress log r_disk on log luminosity scaled to 140 pc, with and without cos i  
  > "The top right panel shows the probability histogram of the flux ratios generated by a Monte Carlo routine, which uses random sampling of iterative 5000 calculations by incorporating the errors associated with each flux ratio measurement." (Comparison with Other Telescopes); "Employing the Bayesian linear regression, we have obtained" (Relation of Flux and Disk Size)
   - software: Linmix
   - parameter: AA Tau (1.2 mm) and GM Aur (1.1 mm) fluxes scaled to 1.3 mm with alpha_mm = 1.6 and 2.7  
  > "applying spectral indices $\alpha_{\rm mm}$ of 1.6 for AA Tau (cite: Andrews2005) and 2.7 for GM Aur (cite: Huang2020)" (Comparison with Other Telescopes)
   - assumption: Distance rescaling of luminosity to 140 pc (individual distances from Gaia DR2)  
  > "millimeter luminosity (total flux density re-scaled to a common distance)" (Relation of Flux and Disk Size)
   - fitting: Bayesian linear regression (Linmix)  
  > "Linear regression on the logarithmic scale gives" (Relation of Flux and Disk Size)
   - validation: Compared ALMA fluxes to SMA/PdBI/IRAM; DK Tau A and V710 Tau A checked against other ALMA data (Rota2022)  
  > "We see that most of the flux values measured with ALMA are consistent with those obtained from other compact interferometers." (Comparison with Other Telescopes)
10. **Extract azimuthally averaged radial intensity profiles**: Deproject SpM images to face-on and average in azimuth (full azimuth or restricted ranges per disk); uncertainty as standard error of the mean with one beam as independent unit  
  > "The uncertainty $\hat{\sigma}_{I}$ of the radial intensity profiles is computed as the standard error of the mean at each radius $r_{i}$, considering one beam size as the smallest independent unit." (Methods of Extracting Radial Profiles)
   - parameter: i >= 60 deg disks (AA Tau, CW Tau, IQ Tau, V409 Tau): azimuthal average 20-40 deg from semi-major axis; other restricted ranges listed in the substructure table  
  > "For four highly inclined disks with $i \geq 60^{\circ}$ (AA Tau, CW Tau, IQ Tau, and V409 Tau), the azimuthal average is taken in the range from $20^{\circ}$ to $40^{\circ}$ relative to the semi-major axis" (Methods of Extracting Radial Profiles)
   - fitting: _not stated_
   - validation: Azimuthal averaging suppresses SpM clump/speckle artifacts; profiles compared with CLEAN-model profiles  
  > "These artifacts can be suppressed by taking the azimuthal average and extracting the radial intensity profile." (Image Fidelity)
11. **Identify rings, gaps, inflections and measure gap width and depth**: Use D(r) = (1/I) dI/dr: rings are local maxima, gaps local minima, inflections where D''=0; gap edges at I_edge midpoint (Case 1) or using inner peak (Case 2); width and depth from edges and ring/gap intensities  
  > "Rings are defined as the local maximum of the radial intensity profile" (Definition of Rings, Gaps, and Inflections); "Gaps are defined as the local minimum of the radial intensity profile" (Definition of Rings, Gaps, and Inflections); "We define the gap width in units of length $\Delta_{\rm I, unit}$ and normalized gap width $\Delta_{\rm I}$ as" (Gap Width and Depth)
   - software: Kneed
   - parameter: Gap depth delta_I = I(r_ring)/I(r_gap); depths treated as upper limits for AB Aur (D62), LkCa 15 (D17), AA Tau (D14)  
  > "\delta_{\rm I} = \frac{I_{\nu}\left(r_{\rm ring}\right)}{ I_{\nu}\left(r_{\rm gap}\right)}" (Gap Width and Depth); "Therefore, we consider these to be upper limits of depth and exclude them from our analyses when we use $\delta_{\mathrm{I}}$." (Gap Width and Depth)
   - parameter: Ring-Gap if normalized width < 0.5; Ring-Cavity if width > 0.5 or ring > 10 au; Central Hole if ring < 10 au  
  > "We denote a narrow gap with the width of $\Delta_{\rm I} < 0.5$ as “Ring-Gap”." (Rings-Gaps)
   - parameter: Inflection locations found partly with the Kneed package  
  > "a Python package that identifies the inflection point to fit the data based on Equation" (Definition of Rings, Gaps, and Inflections)
   - fitting: TD ring widths fitted with Gaussian by Levenberg-Marquardt least squares (scipy optimize.leastsq)  
  > "We use $\tt optimize.leastsq$ within $\tt Scipy$ that employs the Levenberg-Marquardt algorithm for a nonlinear least-squares problem." (Rings-Gaps)
   - validation: Comparison with frank non-parametric 1D fits (Jennings2022taurus), qualitatively consistent in many targets  
  > "From visual inspection, the published radial visibility and intensity profiles for several disks from their study qualitatively agree with our results." (Comparison with Frankenstein approach)
12. **Quantify correlations among gap and ring properties**: Pearson correlations and Bayesian linear regressions of ring vs gap radius, width vs gap radius, and width vs depth (log delta_I - 1) for spatially resolved gaps, excluding Ring-cavity outliers  
  > "The Pearson correlation coefficient after removing these outliers is $\rho = 0.994$" (Ring and Gap Radii); "We use $\delta_{\rm I}-1$ rather than $\delta_{\rm I}$ for gap depth so that the value is zero when there is no gap" (Gap Width and Gap Depth)
   - software: Linmix
   - parameter: 20 spatially resolved gaps; depth correlation also tested for outer-region gaps (r_ring > 30 au)  
  > "We consider 20 spatially resolved gaps listed in Figure" (Correlation of Disk Substructures)
   - fitting: Linmix Bayesian regression; quoted values are posterior medians with 68% intervals; priors not stated  
  > "The values quoted for $\mathcal{A}$ (intercept) and $\mathcal{B}$ (slope) are the medians of their posterior distribution, and the uncertainties are the $68\%$ confidence interval." (Table of gap width-depth relation (note))
   - validation: _not stated_
13. **Compare gap width-depth relation with planet-disk and SGI models and infer planet masses**: Compare observed delta_I vs Delta_I with the Zhang et al. (2018) planet-disk relation; for gaps within the model range, derive planet mass from normalized width using tabulated A, B, local aspect ratio and alpha_vis; test SGI via ring spacing over scale height  
  > "The planet-disk interaction model outlined in (cite: Zhang2018) predicts the relationship between the gap depth" (Possible Origin of Gap Formation); "For the 11 gaps that lie within the range of the planet-disk interaction model, we derive the planet mass." (Inferred Planet Mass in Gap Structure)
   - parameter: s_max = 0.1 mm (DSD1), alpha_vis = 1e-3, Sigma_g = 10 and 100 g/cm2, h_gap/r_gap = 0.05-0.1  
  > "We fix the maximum grain size $s_{\max}$ to be 0.1 mm (DSD1 model for (cite: Zhang2018)) based on ALMA observations by (cite: Bacciotti2018) and the viscous parameter $\alpha_{\rm vis}$ to be $10^{-3}$." (Possible Origin of Gap Formation)
   - parameter: Flaring angle phi = 0.02 (0.05 for DM Tau and GM Aur) in T_d(r)  
  > "The flaring angle is assumed to be constant at 0.02 except for DM Tau and GM Aur, for which we use 0.05" (Possible Origin of Gap Formation)
   - parameter: Dust opacity 0.43 cm2/g at 1.3 mm  
  > "The opacity $\kappa_{\nu}$ is assumed to be $0.43~\mathrm{cm}^{2}~\mathrm{g}^{-1}$ which is the value of DSHARP opacity model (cite: Birnstiel2018)" (Inferred Planet Mass in Gap Structure)
   - assumption: Dust temperature from irradiated passive disk; Sigma_d from simple optically-thick radiative transfer; Sigma_g from the Sigma_g-Sigma_d relation in Zhang2018 Fig. 18  
  > "we derive the radial dust surface density profile $\Sigma_{\mathrm{d}}(r)$ using the simple radiative transfer equation" (Inferred Planet Mass in Gap Structure); "we use the relationship between $\Sigma_{\mathrm{g}}$ and $\Sigma_{\mathrm{d}}$ presented in Figure 18 of (cite: Zhang2018)" (Inferred Planet Mass in Gap Structure)
   - fitting: _not stated_
   - validation: Derived planet mass insensitive to alpha_vis from 1e-4 to 1e-2; compared with Zhang2023 re-analysis  
  > "The derived planet mass does not vary much if we change the viscosity parameter $\alpha_{\rm vis}$ from $10^{-4}$ to $10^{-2}$." (Inferred Planet Mass in Gap Structure)
14. **Estimate upper-limit planet masses for shoulder features**: Apply the Kanagawa et al. (2016) width-mass relation assuming shoulder width <= effective resolution and r_p = r_inf  
  > "We estimate the upper limit of the planet mass by assuming that this gap width to be smaller than the effective spatial resolution, with $\Delta_{\rm I, unit}\leq\theta_{\rm eff}$ and $r_{\rm p} = r_{\rm inf}$." (Implication of planet formation)
   - parameter: h_p/r_p = 0.05, alpha_vis = 1e-3, applied to 21 shoulder features  
  > "We fix the disk scale height $h_{\rm p}/r_{\rm p}$ and viscous parameter $\alpha_{\mathrm{vis}}$ to be 0.05 and $10^{-3}$, respectively, and apply this formula to the 21 shoulder features." (Implication of planet formation)
   - assumption: Dust well coupled to gas  
  > "Here, we assume that the dust is well coupled with the gas." (Implication of planet formation)
   - fitting: _not stated_
   - validation: _not stated_
15. **Estimate envelope mass from the IRAM-ALMA flux excess**: Envelope flux = IRAM 30m flux minus ALMA flux; optically thin isothermal mass M_env = F d^2 / (kappa B(T))  
  > "Under the assumption that the envelope is isothermal and optically thin, the total mass is given by:" (Remnants of Dust Envelope)
   - parameter: T = 15 K; kappa = 0.023 cm2/g; 21 single-star targets  
  > "the opacity of $\kappa_{\nu} = 0.023$ cm$^{2}$ g$^{-1}$ (cite: Beckwith1991)" (Remnants of Dust Envelope)
   - assumption: Gas and dust at the same temperature of 15 K; uncertainty a factor of several from opacity choice  
  > "Assuming that the gas and dust are at the same temperature of $T = 15$ K (cite: Federman2023)" (Remnants of Dust Envelope); "This estimate has an uncertainty of a factor of several due to the assumed opacity values" (Remnants of Dust Envelope)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.1.0 for self-calibration/CLEAN; pipeline calibration versions not stated: Pipeline calibration, fixvis/fixplanets, self-calibration, tclean imaging, addcomponent/ft/uvsub point-source injection  
  > "We used the Common Astronomy Software Applications package ($\tt CASA$; (cite: CASA2022)) for the calibration." (Data Reduction and CLEAN Imaging); "in the $\tt CASA$ version 6.1.0 environment" (Data Reduction and CLEAN Imaging)
- **tclean** : CLEAN images and self-calibration models  
  > "The CLEAN model was generated through the $\tt tclean$ task (hereafter referred to as CLEAN)." (Data Reduction and CLEAN Imaging)
- **PRIISM** 0.7.2: l1+TSV sparse-modeling imaging with cross-validation  
  > "ver. 0.7.2 (cite: Nakazato2020) in conjunction with $\tt CASA$ to perform" (Imaging with Sparse Modeling)
- **Linmix** : Bayesian linear regression for all fitted relations  
  > "$\tt Linmix$ is a Bayesian approach to linear regression and is publicly available at" (Software footnote)
- **Kneed** : Locating inflection points on radial profiles  
  > "a Python package that identifies the inflection point to fit the data based on Equation" (Definition of Rings, Gaps, and Inflections)
- **SciPy** : optimize.leastsq Gaussian fits to ring profiles; RectBivariateSpline for model visibilities  
  > "We use $\tt optimize.leastsq$ within $\tt Scipy$ that employs the Levenberg-Marquardt algorithm for a nonlinear least-squares problem." (Rings-Gaps); "the bivariate spline approximation $\tt RectBivariateSpline$ in $\tt Scipy$ (cite: Virtanen2020)" (Radial Visibility Profile)
- **NumPy** : FFT of reconstructed images to model visibilities  
  > "using the Fast Fourier Transform algorithm $\tt fft$ in $\tt NumPy$ (cite: Harris2020)" (Radial Visibility Profile)
- **rescale_flux (DSHARP reduction_utils)** : Rescaling long-baseline visibilities to a common flux scale  
  > "After the coordinates of each dataset were corrected, the visibility of long baseline data was re-scaled using the DSHARP" (Data Reduction and CLEAN Imaging)
- **frank (Frankenstein)** : Compared against (published results of Jennings2022taurus), not run by the authors  
  > "The $\tt frank$ approach utilizes a Gaussian process to optimize the model of the deprojected real-part visibility profile" (Comparison with Frankenstein approach)
- **Astropy** : _not stated_
- **matplotlib** : _not stated_
- **AnalysisUtilities** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dust disk radii range and median (SpM images) | 8-238 au; median 45 au | not stated | au | 8 | The disk radii span a wide range from 8 to 238 au, with a median radius of 45 au. |
| Number of targets with 2-3x resolution improvement | 18 of 43 | not stated | dimensionless | 6 | 18 out of 43 targets show a factor of two to three improvement in spatial resolution compared to the conventional CLEAN method. |
| Best SpM effective resolution | 0''.01-0''.02; all but three images better than 0''.1 | not stated | arcsec | 5 | All but three images show spatial resolution better than $0''.1$, with the highest achieved resolution reaching $0''.01 - 0''.02$. |
| Resolution ratio vs CLEAN SNR: log(theta_eff/theta_cl [%]) = a - b log SNR | a = 2.30, b = 0.24; Pearson rho = -0.65; scatter 0.13 dex | a +/- 0.11, b +/- 0.05; scatter +/- 0.01 dex | dimensionless | 6 | (2.30\pm 0.11) - (0.24\pm0.05) \log \mathrm{SNR}; Pearson correlation coefficient $\rho = -0.65$, $p$-value $< 0.01$; with a Gaussian scatter perpendicular to this regression with a standard deviation of $0.13\pm0.01$ dex |
| Resolution ratio vs normalized disk size: log(theta_eff/theta_cl [%]) = a + b log(theta_disk/theta_cl) | a = 1.55, b = 0.22; rho = 0.78; scatter 0.11 dex | a +/- 0.03, b +/- 0.03; scatter +/- 0.01 dex | dimensionless | 6 | (1.55\pm 0.03) + (0.22\pm0.03); a robust relationship ($\rho = 0.78$ and $p-$value $< 0.01$) |
| Fraction of disks with better reduced chi-square for SpM vs CLEAN image | 95% (40/42) | not stated | dimensionless | 6 | SpM produces a better fit in $95\%$ of the cases (40/42). |
| Fraction of disks with better reduced chi-square for SpM vs CLEAN model | 69% (29/42) | not stated | dimensionless | 6 | SpM shows better performance for $69\%$ (29/42) |
| Resolution ratios in cross-check disks (RY Tau, DG Tau, CI Tau) | 35%, 39%, 86% of CLEAN beam | not stated | percent | 7 | The spatial resolutions of Data 1 SpM are $35\%$, $39\%$, and $86\%$ of the CLEAN beam sizes for RY Tau, DG Tau, and CI Tau, respectively. |
| Mean disk inclination | 42 deg | 15 deg | deg | 8 | The average of measured disk inclination is $42^{\circ} \pm 15^{\circ}$. |
| ALMA / other-interferometer total-flux ratio | 110% | 25% (standard deviation) | percent | 9 | The average of the histogram is $110\%\pm25\%$, where the error indicates the standard deviation. |
| ALMA / IRAM 30m total-flux ratio (21 single-star disks) | 79% | 19% | percent | 9 | The average flux ratio is $79\%\pm19\%$ |
| Size-luminosity relation log(r_disk/au) = a + b log[F (d/140 pc)^2] | a = 2.32, b = 0.50; rho = 0.63; scatter 0.36 dex | a +/-0.13, b +/-0.10; scatter +/-0.04 dex | dimensionless | 9 | (2.32_{-0.13}^{+0.13})+ (0.50_{-0.10}^{+0.10}); We see a strong correlation with $\rho = 0.63$ and a $p-$value of $<0.01$.; with a scattering of $0.36 \pm 0.04$ dex |
| Size-luminosity relation with cos i correction | a = 2.32, b = 0.58; rho = 0.69; scatter 0.30 dex | a +/-0.11, b +/-0.10; scatter +/-0.02 dex | dimensionless | 9 | (2.32_{-0.11}^{+0.11}) + (0.58_{-0.10}^{+0.10}); ($\rho = 0.69$ with a $p-$value of $<0.01$); with the scattering of $0.30 \pm 0.02$ dex |
| Mean disk-averaged Band 6 surface brightness and brightness temperature | 0.14 Jy arcsec^-2; ~8 K | not stated | Jy arcsec^-2; K | 9 | the averaged surface brightness is $\left\langle I_{\nu}\right\rangle \simeq 0.14~\rm Jyasec^{-2}$ and the corresponding brightness temperature is $\left\langle T_{\rm b} \right\rangle \simeq 8$ K |
| Gap-ring pairs detected | 33 gap-ring pairs in 21 disks; widths and depths measured for 30/33 | not stated | dimensionless | 11 | We have detected 33 gap–ring pairs in 21 disks and have been able to measure the widths, depths, and uncertainties for $90\%$ (30/33) of all gaps. |
| Narrow Ring-Gap structures | 24 in 17 disks (12 not previously identified in CLEAN images) | not stated | dimensionless | 11 | We find a total of 24 narrow gap/ring structures in 17 disks.; The improvement of spatial resolution by SpM has enabled us to detect 12 gap/ring structures that were not previously identified in the conventional CLEAN images |
| Ring-Cavity disks | 12 disks: three TDs and nine PTDs | not stated | dimensionless | 11 | The Ring-cavity structure is present in 12 disks, comprising three TDs and nine PTDs |
| Transition-disk ring widths (FWHM) for CIDA 9A, IP Tau, UX Tau | 0''.13 (22 au), 0''.11 (14 au), 0''.11 (15 au) | +/- 0''.01 | arcsec | 11 | The widths are $0''.13$ (22 au), $0''.11$ (14 au), and $0''.11$ (15 au) for CIDA 9A, IP Tau, and UX Tau, respectively |
| Disks with Disk-skirt features | 40% (17/43); 70% (15/21) of large disks vs 10% (2/22) of small disks | not stated | dimensionless | 11 | In total, we have observed the Disk-skirt features in $40\%$ (17/43) of all disks |
| Disks with Shoulder features | 19 (40%) | not stated | dimensionless | 11 | The number of disks showing Shoulder features amounts to 19, which is $40\%$ (19/43) of our sample. |
| Smooth disks | 4 (9%): V836 Tau, DH Tau A, HN Tau A, UY Aur A | not stated | dimensionless | 11 | Four ($=9\%$) disks of our 43 samples, V836 Tau, DH Tau A, HN Tau A, and UY Aur A, are categorized into this group. |
| Ring-gap radius relation r_ring = a + b r_gap (au) | a = 7.58 au, b = 1.09; rho = 0.994; scatter 3.65 au | a +2.59/-2.62, b +/-0.04; scatter +/-1.02 au | au | 12 | 7.58^{+2.59}_{-2.62} + 1.09^{+0.04}_{-0.04}; with a scatter of $3.65\pm 1.02$ au |
| Gap width (au) vs gap radius: log(Delta_I,unit/au) = a + b log(r_gap/au) | a = 0.47, b = 0.37; rho = 0.62; scatter 0.24 dex | a +/-0.27, b +/-0.16; scatter +/-0.12 dex | dimensionless | 12 | 0.47^{+0.27}_{-0.27}+0.37^{+0.16}_{-0.16}; with a scatter of $0.24\pm 0.12$ dex for the width with units |
| Normalized gap width vs gap radius: log Delta_I = a + b log(r_gap/au) | a = 0.21, b = -0.51; rho = -0.79; scatter 0.17 dex | a +0.22/-0.23, b +/-0.13; scatter +/-0.05 dex | dimensionless | 12 | 0.21^{+0.22}_{-0.23}-0.51^{+0.13}_{-0.13}; with a scatter of $0.17\pm 0.05$ dex for the normalized width |
| Power-law index B of log Delta_I vs log(delta_I - 1), outer-region gaps (30-100 au) | 0.23 | 0.09 | dimensionless | 12 | the derived power-law index of $\mathcal{B}={0.23 \pm 0.09}$ in the $\delta_{\rm I}-\Delta_{\rm I}$ relationship |
| Resolution ratio vs noise ratio: log(theta_eff/theta_cl [%]) = a - b log(I_DT/sigma_cl) | a = 2.08, b = 0.31; rho = -0.88; scatter 0.062 dex | a +/-0.03, b +/-0.03; scatter +/-0.004 dex | dimensionless | 6 | (2.08\pm 0.03) - (0.31\pm0.03); Pearson correlation coefficient $\rho = -0.88$, $p$-value $< 0.01$ |
| Point-source sensitivity factor X between SpM and CLEAN SNR (T Tau injection) | 2.5 | not stated | dimensionless | 6 | the factor $X$ is 2.5 |
| Fraction of resolved gaps within the Zhang2018 planet-disk model range | 65% (11 of 17) | not stated | dimensionless | 13 | We find that $65\%$ (11 out of 17) of the total sample falls in the range predicted by the model. |
| SGI ring-spacing/scale-height ratios for multi-ring disks | 4.0-14.9, average 8.6 (excluding GO Tau; GO Tau ratios 3.6 and 1.8) | not stated | dimensionless | 13 | the derived ratios range from 4.0 to 14.9 with an average of 8.6 |
| Inferred planet masses for 11 gaps | ~Neptune to ~Jupiter mass; Saturn-Jupiter at r~10 au, Neptune-mass at r~40-100 au | not stated | Neptune to Jupiter masses | 13 | All of our estimates of planet mass for the eleven gaps are in the range of $\sim$Neptune to $\sim$Jupiter mass. |
| Average upper-limit planet mass for 21 shoulder features | 0.6 M_Jup at mean resolution 66 mas | 0.5 M_Jup; 32 mas (standard deviations) | M_Jup | 14 | We have obtained the average upper limit of $M_{p} = 0.6\pm0.5~M_{\rm Jup}$ at the spatial resolutions of $66\pm32$ mas, where the errors represent standard deviations. |
| Resolution needed to resolve gaps from Neptune-mass planets | 24 mas | 17 mas | mas | 14 | we need an extremely high resolution of $24 \pm 17$ mas to resolve the gaps carved by Neptune mass planets |
| Average envelope mass over 21 single-star targets | 10 M_Jup | 8 M_Jup | M_Jup | 15 | average envelope masses over the 21 single-star targets is derived to be $M_{\rm env} = 10 \pm 8$ $M_{\rm Jup}$ |

## Qualitative findings

- Every gap has a ring just outside it  
  > "All the gaps have a ring outside of them." (Conclusion)
- No robust correlation between stellar mass and substructure properties  
  > "Meanwhile, we do not observe a robust correlation ($\rho < 0.3$) between stellar mass and disk substructure properties." (Overview of Correlations)
- Gap radii are bimodal: inner (<~20 au) and outer (>~30 au), with a gap desert between  
  > "The gaps are located either in the inner ($r\lesssim 20$ au) or the outer ($r\gtrsim 30$ au) part of the disk" (Distribution of Gap Radii)
- SpM images show many more substructures than CLEAN images  
  > "We clearly see many more disk substructures in the SpM images." (Reconstructed Images and SpM Imaging Performances)
- Observed gap width-depth trend consistent with planet-disk interaction but SGI ring spacing generally ruled out (GO Tau uncertain)  
  > "the sources except for GO Tau do not appear to be induced by the SGI model" (Possible Origin of Gap Formation)

## Claim tuples

- H: Sparse-modeling imaging of archival ALMA data yields higher-resolution, high-fidelity images than CLEAN for Taurus-Auriga disks | E: PRIISM l1+TSV imaging with cross-validation for 43 disks; compare with CLEAN, visibility chi-square and short/long-baseline cross-check | R: SpM resolution 0''.02-0''.1, 2-3x better for 18/43; better chi-square in 40/42; cross-check consistent within ~10% for three disks | F: SpM resolves all 43 disks and reveals substructure CLEAN misses, though it can create clumpy artifacts in some disks | **supported**
- H: Gap locations in disks follow a distinct radial distribution | E: Identify gaps in azimuthally averaged SpM radial profiles and histogram gap radii | R: Half of the disks show clear gaps, with peaks at <~20 au and >~30 au | F: Bimodal gap distribution with a gap desert in between; weak gap candidates (shoulders) appear at all radii | **supported**
- H: Gap width-depth scaling is consistent with planet-disk interaction | E: Regress gap width on depth for resolved gaps and compare with Zhang2018 and Kanagawa models; SGI spacing test | R: Power-law index 0.23 +/- 0.09 for outer gaps; 11/17 resolved gaps within model range; SGI spacing criterion rarely satisfied | F: Planet-disk interaction is a plausible origin for the outer gaps | **supported**
- H: The inferred planet population resembles the Solar System, and low-mass planets may exist at all radii | E: Planet masses from gap widths (Zhang2018) for 11 gaps; upper limits from 21 shoulder features (Kanagawa2016) | R: Saturn-Jupiter masses at ~10 au, Neptune masses at 40-100 au; shoulder upper limit 0.6 +/- 0.5 M_Jup | F: Planet distribution is analogous to the Solar System, with possible Neptune-or-lower mass planets at all radii | **partially**
- H: Class II Taurus disks retain envelope-scale dust that ALMA resolves out | E: Compare ALMA total fluxes with SMA and IRAM 30m fluxes and estimate envelope mass | R: ALMA/SMA flux ratio 110% +/- 25%; ALMA/IRAM ratio 79% +/- 19%; M_env = 10 +/- 8 M_Jup | F: About 20% of single-dish flux may arise in remnant envelope material, enough to form Jupiter-mass planets | **partially**

## Reasoning

- Why this data: Higher resolution is needed to capture substructure, and SpM can raise resolution of existing data without new observations  
  > "Higher spatial resolution is crucial in capturing the substructures in disks." (Introduction); "The increase in spatial resolution does not necessarily require new observations." (Introduction)
- Why this method: SpM needs no prior image (unlike MEM) and separates sparsity and smoothness constraints  
  > "In contrast to MEM, SpM does not impose such prior information." (Imaging with Sparse Modeling); "SpM has the advantage of imposing them separately so that it is easier to control the balance between the sparsity and smoothness constraints." (Imaging with Sparse Modeling)
- Alternative: Maximum Entropy Method rejected in favor of SpM because it requires a prior image that may bias the reconstruction  
  > "we briefly describe our motivation for choosing SpM over the Maximum Entropy Method (MEM; (cite: Narayan1986)), which is another regularization method." (Imaging with Sparse Modeling)
- Alternative: CLEAN model radial profiles considered as an alternative; useful only for outer-disk gap/ring locations  
  > "Therefore, the radial profiles obtained from the CLEAN model have the potential to constrain the structures in the outer part of the disks and identify substructure candidates." (Radial Profiles Derived from CLEAN Model)
- How they decided it was enough: Hyper-parameters chosen at the cross-validation error minimum, with visual inspection when images are patchy  
  > "we employ the 10-fold cross-validation (CV) approach" (Imaging with Sparse Modeling); "we find that the image with the minimum CVE exhibits artificial patchy structures" (Imaging with Sparse Modeling)
- Limitation (authors): SpM can create artificial clumps/speckles around bright inner disks  
  > "However, we note that SpM imaging can introduce artificial clumped/speckled features, especially for disks with the brightest emission in the central part (i.e., an inner disk) surrounded by the faint emission area (i.e., a ring skirt)." (Image Fidelity)
- Limitation (authors): 40% of gaps (13/33) are not fully spatially resolved  
  > "The remaining $40\%$ (13/33) of the gaps have not been fully spatially resolved." (Gap Width and Depth)
- Limitation (authors): Gaps in compact disks may be affected by insufficient resolution  
  > "Therefore, again, the statistical properties of gaps in compact disks may be affected by insufficient spatial resolution." (Distribution of Gap Radii)
- Limitation (authors): Inner disks are likely optically thick and hard to probe; gap models need optical depth effects  
  > "Moreover, the inner region of the disk is likely to be optically thick so it is hard to observe surface density structures." (Distribution of Gap Radii); "it is necessary to have better gap models that take into account optical depth effects that are crucial in analyzing high-resolution observations." (Implication of planet formation)
- Limitation (authors): Planet-disk model has large uncertainty for wide gaps opened by Jupiter-mass planets  
  > "The model actually has large uncertainty in the parameter space when a Jupiter-mass planet opens a very wide gap" (Possible Origin of Gap Formation)
- Caveat (inferred, ours): Planet masses depend on assumed alpha_vis, s_max, flaring angle and a Sigma_g-Sigma_d relation, plus optically-thin/thick treatment; systematic errors are not propagated.
- Caveat (inferred, ours): Gap and ring detection relies on SpM images whose artifacts (clumps, patchy structure) and hyper-parameter choice (manually adjusted for five disks) can affect substructure counts.
- Caveat (inferred, ours): Heterogeneous archival data (different configurations, SNR, combined EBs) make the sample non-uniform and statistics (bimodality, correlations) sensitive to resolution bias.
- Caveat (inferred, ours): Sample is limited to bright, resolved disks (SNR > 30) and excludes many binaries and M4-M9 stars, so the statistics are not representative of all Taurus disks.
- Caveat (inferred, ours): Small numbers (20 resolved gaps; 11 for planet masses) limit the strength of regression claims.

## Reproducibility

- Data public (paper): Archival ALMA data; project codes listed (one CW Tau data set provided privately)  
  > "We present the analyses of archival ALMA Band 6 continuum data of 43 disks" (abstract); "Takahiro Ueda for giving us the ALMA data of CW Tau." (Acknowledgments)
- Products in archive: _not stated_
- Code: PRIISM is public on GitHub  
  > "is an imaging tool for ALMA based on the sparse modeling technique, and is publicly available at <https://github.com/tnakazato/priism>" (Software footnote)
- Code: DSHARP rescale_flux script is public  
  > "function is publicly available at <https://almascience.eso.org/almadata/lp/DSHARP/scripts/reduction_utils.py>" (Software footnote)
- Code: _not stated_
- Missing: Per-target tclean settings (cell, image size, mask, threshold) and exact self-calibration products kept.
- Missing: Per-dataset CASA pipeline versions and execution-block selection, and which compact-configuration data were combined.
- Missing: Per-target PRIISM grid settings; final hyper-parameters are tabulated but the grid/search ranges are not stated.
- Missing: Gap-finding implementation details (profile smoothing, derivative estimation, Kneed settings) and Linmix settings.
- Missing: The CW Tau data set that was supplied privately.
- Data volume (inferred): 25 projects with 43 targets; raw Band 6 continuum/spectral-line measurement sets likely several hundred GB to ~2 TB if all execution blocks are downloaded; continuum-averaged products are tens of GB.
- Score (inferred): 3/5, Data are public archival ALMA projects and PRIISM is public, with numeric results and many stated parameters, but tclean grids, pipeline versions, PRIISM grid ranges and gap-finding details are missing and the 25-project volume is large.
- Rediscovery candidate: no, Data are public and results numeric, but the imaging and profile-extraction recipe is not complete enough (cell/image size, masks, per-target hyper-parameter grids, derivative smoothing) to redo the full 43-disk analysis; a single-disk redo is feasible.

## Links

- Method: (cite: Yamaguchi2021) (Original l1+TSV SpM method with cross-validation and point-source injection applied to T Tau)
- Method: (cite: Yamaguchi2020) (SpM imaging of ALMA disk data, cross-check fidelity method and noise characterization)
- Method: (cite: Nakazato2020) (PRIISM imaging package)
- Method: (cite: Andrews2018a) (DSHARP rescale_flux procedure)
- Method: (cite: Zhang2018) (Planet-disk interaction model and planet-mass relations)
- Companion: (cite: Long2019) (Taurus ALMA survey whose data overlap the sample)
- Companion: (cite: Jennings2022taurus) (frank non-parametric radial profiles for Taurus disks compared with this work)
- Companion: (cite: Zhang2023) (Reanalysis of Long2019 data with planet-mass estimates)
- Related: DSHARP
- Related: ALMA Taurus survey (Long et al. 2019)
- Related: SMA Taurus survey (Andrews et al. 2013)

## Checks

```json
{
 "quotes": 258,
 "quotes_ok": 258,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 25,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 33,
 "numeric_problems": 0,
 "fill": {
  "facts": 175,
  "stated": 141,
  "rate": 0.806
 },
 "evidence_ok": true
}
```
