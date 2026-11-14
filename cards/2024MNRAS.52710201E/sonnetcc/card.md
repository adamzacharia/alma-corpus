# The ALMaQUEST Survey XI: a strong but non-linear relationship between star formation and dynamical equilibrium pressure

`2024MNRAS.52710201E` | Monthly Notices of the Royal Astronomical Society 2024 | first author: Ellison, Sara L. | arXiv: 2312.03132 | DOI: 10.1093/mnras/stad3778

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: Does the resolved dynamical equilibrium pressure (P_DE) vs Sigma_SFR relation hold, and agree with the PRFM model, across a diverse sample of 66 galaxies including mergers and central starbursts, and is P_DE a more fundamental predictor of Sigma_SFR than Sigma_H2 or Sigma_star?  
  > "Here, we aim to further the comparison of the PRFM model with an additional dataset that includes a wider range of galaxies than those previously assessed." (Introduction); "Finally, we compare the observed rPDE relation with contemporary theories of star formation in order to assess whether (and under what conditions) the models can reproduce the data." (Introduction)
- Target **Extended ALMaQUEST sample (66 MaNGA galaxies)**: coordinates _not stated_; z/distance z given per galaxy in the sample table  
  > "The extended ALMaQUEST sample consists of a total of 66 galaxies, all of which were drawn from the MaNGA DR15." (2 The extended ALMaQUEST sample); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.01225.S, 2017.1.01093.S, 2018.1.00558.S, 2018.1.00541.S, 2019.1.00260.S
- bands: _not stated_
- frequencies and spectral setup: One high-resolution spectral window on CO line plus one to three low-resolution continuum windows  
  > "using one high resolution spectral window focused on the CO line and one to three additional low resolution continuum windows for calibration" (3.2 ALMA data)
- continuum bandwidth: _not stated_
- arrays: ALMA 12m array, C43-2 configuration (array type itself not named)  
  > "second most compact configuration (C43-2)" (3.2 ALMA data)
- configurations: C43-2 (second most compact)  
  > "second most compact configuration (C43-2)" (3.2 ALMA data)
- baselines: _not stated_
- angular resolution: ~2.5 arcsec (primary beam ~50 arcsec)  
  > "The single pointing primary beam size for this configuration is $\sim$ 50 arcsec with an angular resolution $\sim$ 2.5 arcsec." (3.2 ALMA data)
- max recoverable scale: _not stated_
- sensitivity: channel width 11 km/s; RMS 0.2 - 2 mJy/beam  
  > "The final cubes have channel widths of 11 km s$^{-1}$ and root mean square (RMS) noise of $\sigma_{rms}$ = 0.2 – 2 mJy beam$^{-1}$." (3.2 ALMA data)
- time on source: 0.2 to 2.5 hours on source  
  > "Integration times ranged from 0.2 to 2.5 hours on source" (3.2 ALMA data)
- observing dates: 2016-2020  
  > "CO(1-0) (hereafter, simply CO) spectral line observations were obtained between 2016-2020" (3.2 ALMA data)
- pi or archival as stated: Five regular proposals: PI Lin (2015.1.01225.S, 2017.1.01093.S, 2018.1.00558.S), PI Ellison (2018.1.00541.S), PI Pan (2019.1.00260.S)  
  > "ALMA observations (described below) were obtained through five separate regular proposals." (2 The extended ALMaQUEST sample); "More recently, in ALMA Cycle 7 (2019.1.00260.S, PI Pan), we obtained CO(1-0) data for a further 20 MaNGA selected galaxies." (2 The extended ALMaQUEST sample)
- Line: CO J=1-0 (not stated)
- Other facility **SDSS-IV MaNGA (DR15) with PIPE3D**: Resolved optical emission-line fluxes and stellar mass surface densities for all spaxels  
  > "We use MaNGA data from the Data Release 15 as the source of all resolved quantities such as emission line fluxes and stellar mass surface densities." (3.1 MaNGA data)
- Other facility **SDSS and DECaLS imaging**: Visual inspection for morphological disturbances to define the merger sample  
  > "by visually inspecting both the SDSS imaging, as well as the deeper Dark Energy Camera Legacy Survey (DECaLS) imaging that exists for the full sample" (2 The extended ALMaQUEST sample)
- Other facility **NASA Sloan Atlas (NSA)**: Half-light radius R50 used to derive the stellar scale length  
  > "We determine $R_{\star}$ by taking the half-light (effective) radius ($R_{50}$) from the NASA Sloan Atlas (NSA)" (4.4 The Resolved Dynamical Equilibrium Pressure Relation)
- External data: PIPE3D optical emission-line data cubes and surface densities (Sigma_star)  
  > "Optical emission line fluxes are taken from the public PIPE3D data cubes (Sánchez et al. 2016a,b, 2018)" (3.1 MaNGA data) [from Sánchez et al. 2016a,b, 2018]
- External data: Integrated stellar masses and SFRs from the PIPE3D value-added catalog (sample table)  
  > "presents their integrated stellar masses and SFRs taken from the PIPE3D (Sánchez et al., 2016a, 2016b) value-added catalog (VAC, Sánchez et al. 2018)" (2 The extended ALMaQUEST sample) [from Sánchez et al. 2016a,b; 2018]
- External data: PRFM theoretical rPDE relation fitted to TIGRESS simulation output  
  > "the theoretical prediction of the PRFM model of Ostriker & Kim (2022), derived by fitting to the output of the high resolution TIGRESS simulation (their Equation 26c)" (4.4 The Resolved Dynamical Equilibrium Pressure Relation) [from Ostriker & Kim (2022)]
- External data: EDGE-CALIFA and PHANGS rPDE data overplotted for comparison  
  > "we overplot the EDGE-CALIFA dataset (blue crosses; Barrera-Ballesteros et al. 2021a) as well as the PHANGS data (purple points, taken from Sun et al. 2020a)" (5 Discussion) [from Barrera-Ballesteros et al. 2021a; Sun et al. 2020a]
- External data: Krumholz et al. (2018) star formation model equations used to predict the rPDE relation  
  > "Our starting point is Equation 30 of Krumholz et al. (2018) who express the star formation rate as" (5.4 What causes the discrepancy) [from Krumholz et al. (2018)]
- External data: Alternative P_DE formulation for starbursts (unpublished)  
  > "Hassan, Ostriker & Kim (in prep) have recently presented a new analytic expression for $P_{DE}$ specifically designed to account for ISM conditions in starburst galaxies" (5.4 What causes the discrepancy) [from Hassan, Ostriker & Kim (in prep)]
- Simulation/model as data: PRFM prediction (Ostriker & Kim 2022, from TIGRESS) and Krumholz et al. (2018) model curves used as comparison models, not as fitted data  
  > "the theoretical prediction of the PRFM model of Ostriker & Kim (2022), derived by fitting to the output of the high resolution TIGRESS simulation (their Equation 26c)" (4.4 The Resolved Dynamical Equilibrium Pressure Relation)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
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
- cell size: 0.5 arcsec pixels  
  > "A fixed restoring beam size of 2.5 arcsec with pixel size of 0.5 arcsec was then applied to the ALMA cube." (3.2 ALMA data)
- image size: Trimmed to the size of each galaxy's MaNGA cube (IFU bundles 12 - 32 arcsec)  
  > "the ALMA data were first trimmed to the size of that galaxy" (3.2 ALMA data)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Convolved to common 2.5 arcsec beam; MaNGA also smoothed up to 3 arcsec as a test with no qualitative difference  
  > "A fixed restoring beam size of 2.5 arcsec with pixel size of 0.5 arcsec was then applied to the ALMA cube." (3.2 ALMA data); "we have repeated all of our analysis smoothing to a range of angular scales (up to 3 arcseconds) and find no qualitative difference in our results" (3.1 MaNGA data)
- final beam: fixed restoring beam of 2.5 arcsec  
  > "A fixed restoring beam size of 2.5 arcsec with pixel size of 0.5 arcsec was then applied to the ALMA cube." (3.2 ALMA data)
- final rms: 0.2 - 2 mJy/beam per 11 km/s channel  
  > "root mean square (RMS) noise of $\sigma_{rms}$ = 0.2 – 2 mJy beam$^{-1}$." (3.2 ALMA data)

### Inherited from earlier work

- Acquisition and processing of ALMaQUEST data (calibration, imaging) taken from earlier papers  
  > "Since the acquisition and processing of ALMaQUEST data have been described extensively in our previous works (e.g. Lin et al. 2019, 2020; Ellison et al. 2020a, b, 2021a, b)" (3 Data) [from Lin et al. 2019, 2020; Ellison et al. 2020a, b, 2021a, b]
- ALMA acquisition and processing for the original 46 galaxies  
  > "The acquisition and processing of ALMA data for the main sample of 46 galaxies is described in detail in Lin et al. (2020)." (3.2 ALMA data) [from Lin et al. (2020)]
- Cycle 7 galaxies processed with identical procedures  
  > "follows identical procedures (described in more detail in Thorp et al. 2022)" (3.2 ALMA data) [from Thorp et al. 2022]
- Fixed alpha_CO = 4.3 convention  
  > "In keeping with our previous ALMaQUEST papers, we assume a fixed conversion factor" (3.2 ALMA data) [from previous ALMaQUEST papers]
- Central starburst selection  
  > "Following Ellison et al. (2020a), central starburst galaxies are identified by plotting the radial profiles of" (2 The extended ALMaQUEST sample) [from Ellison et al. (2020a)]
- P_DE implementation  
  > "Specifically, we follow the implementation of Sun et al. (2020a) who express $P_{DE}$ as" (4.4 The Resolved Dynamical Equilibrium Pressure Relation) [from Sun et al. (2020a)]
- Fixed vertical gas velocity dispersion of 11 km/s  
  > "we follow Barrera-Ballesteros et al. (2021a) and assume a fixed value of $\sigma_{gas,z}$ = 11 km s$^{-1}$" (4.4 The Resolved Dynamical Equilibrium Pressure Relation) [from Barrera-Ballesteros et al. (2021a)]
- Delta SFR offset from global SFMS via matched control sample  
  > "(see Ellison et al. 2018 for more details)" (5.1 Is the rPDE relation universal?) [from Ellison et al. 2018]
- Random forest methodology  
  > "Our approach follows closely the analyses presented in our previous works (e.g. Baker et al. 2022, 2023)" (5.2 Is the rPDE relation the most fundamental star formation scaling relation?) [from Baker et al. 2022, 2023; Bluck et al. (2022) Appendix B]

### Not stated but needed to reproduce (our reading)

- Band, spectral window frequencies, and number of execution blocks per project for the CO(1-0) data
- CASA version, pipeline vs manual calibration, flux calibrator and flux scale uncertainty
- tclean parameters (weighting/robust, deconvolver, masking, cleaning threshold) and continuum subtraction / line-free channels
- Primary beam correction and how the integrated CO flux/moment maps were made (clipping, masks)
- Conversion from Jy km/s to L'(CO) per pixel, including the distances/redshifts used
- Random forest hyperparameters (number of trees, depth, train/validation/test split) and software
- ODR fitting setup (software, errors/weights used) for the scaling relations
- Broken power-law fitting method and uncertainties on its parameters
- Orbital times, Toomre Q and other inputs used for the Krumholz et al. (2018) curves
- Whether the integrated gas masses use alpha_CO = 4.3 or 4.35 (both values appear)

## Analysis recipe

1. **Regrid ALMA CO cubes to MaNGA sampling**: Trim ALMA cubes to MaNGA cube size, apply fixed 2.5 arcsec restoring beam with 0.5 arcsec pixels  
  > "A fixed restoring beam size of 2.5 arcsec with pixel size of 0.5 arcsec was then applied to the ALMA cube." (3.2 ALMA data); "These two steps resulted in ALMA data cubes with the same size and sampling as the MaNGA data products." (3.2 ALMA data)
   - software: CASA
   - parameter: beam 2.5 arcsec, pixel 0.5 arcsec  
  > "A fixed restoring beam size of 2.5 arcsec with pixel size of 0.5 arcsec was then applied to the ALMA cube." (3.2 ALMA data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Convert CO luminosity to molecular gas surface density**: Per-pixel L'(CO) converted to Sigma_H2 with a fixed alpha_CO, inclination corrected with b/a  
  > "were converted to molecular gas surface densities" (3.2 ALMA data); "All surface density quantities are inclination corrected using the axial ratio ($b/a$) listed in Table" (3.1 MaNGA data)
   - parameter: alpha_CO = 4.3 Msun pc^-2 (K km/s)^-1 including helium  
  > "we assume a fixed conversion factor $\alpha_{CO}$ = 4.3 M$_{\odot}$ pc$^{-2}$ (K km s$^{-1}$)$^{-1}$ (including the contribution from helium)" (3.2 ALMA data)
   - parameter: Alternative metallicity-dependent alpha_CO (Sun et al. 2020b) used only where 12+log(O/H) is available  
  > "we therefore also compute $\Sigma_{\rm H_2}$ with the metallicity dependent formalism of Sun et al. (2020b)" (3.2 ALMA data)
   - assumption: Milky Way-like fixed alpha_CO  
  > "which is a typical value adopted for the Milky Way" (3.2 ALMA data)
   - fitting: _not stated_
   - validation: Alternative conversion factors tested in discussion  
  > "Nonetheless, we next embark on a quantitative assessment of alternative values of $\alpha_{CO}$." (5.3.2 Assumption of a fixed CO-to-H2 conversion factor)
3. **Derive Sigma_SFR and Sigma_star from MaNGA/PIPE3D**: Halpha luminosities (extinction corrected) converted to Sigma_SFR with Kennicutt (1998) Eq. 2; Sigma_star from PIPE3D; Salpeter to Chabrier IMF conversion  
  > "are computed from H$\alpha$ luminosities using Equation 2 from Kennicutt (1998)" (3.1 MaNGA data); "This conversion from Salpeter to Chabrier IMFs is achieved by multiplying the former by a factor of 0.61, see Madau & Dickinson (2014)." (2 The extended ALMaQUEST sample)
   - software: PIPE3D
   - parameter: Intrinsic Halpha/Hbeta = 2.85 with Milky Way extinction curve  
  > "corrected for internal extinction by assuming an intrinsic H$\alpha$/H$\beta$=2.85 and a Milky Way extinction curve" (3.1 MaNGA data)
   - parameter: Salpeter to Chabrier factor 0.61  
  > "multiplying the former by a factor of 0.61" (2 The extended ALMaQUEST sample)
   - fitting: _not stated_
   - validation: Method said to reproduce UV and IR SFRs in IFU data (cited work)  
  > "a technique that has been shown to reproduce the UV and IR SFRs well in integral field unit (IFU) data" (3.1 MaNGA data)
4. **Select star-forming spaxels with CO detections**: S/N>2 in four BPT lines, below Kauffmann et al. (2003) line, Halpha EW>6 A, and CO S/N>3  
  > "we require that the MaNGA spaxel has a S/N$>$2 in each of the four optical emission lines" (3.1 MaNGA data); "the emission line ratios of the spaxel must lie below the criterion defined by Kauffmann et al. (2003)" (3.1 MaNGA data); "have detections in CO with a S/N$>$3" (3.2 ALMA data)
   - parameter: Halpha EW cut > 6 A  
  > "we impose an H$\alpha$ equivalent width (EW) cut H$\alpha>6$ Å" (3.1 MaNGA data)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compute dynamical equilibrium pressure P_DE per spaxel**: Sun et al. (2020a) P_DE formula with gas self-gravity and stellar gravity terms, using Sigma_gas = Sigma_H2 + Sigma_HI, stellar volume density from Sigma_star and R_star  
  > "Specifically, we follow the implementation of Sun et al. (2020a) who express $P_{DE}$ as" (4.4 The Resolved Dynamical Equilibrium Pressure Relation); "We determine $R_{\star}$ by taking the half-light (effective) radius ($R_{50}$) from the NASA Sloan Atlas (NSA) and then convert to the scale length using" (4.4 The Resolved Dynamical Equilibrium Pressure Relation)
   - parameter: Sigma_HI = 7 Msun pc^-2 fixed  
  > "we assume a fixed value of $\Sigma_{HI}$ = 7 M$_{\odot}$ pc$^{-2}$" (4.4 The Resolved Dynamical Equilibrium Pressure Relation)
   - parameter: sigma_gas,z = 11 km/s fixed  
  > "we follow Barrera-Ballesteros et al. (2021a) and assume a fixed value of $\sigma_{gas,z}$ = 11 km s$^{-1}$" (4.4 The Resolved Dynamical Equilibrium Pressure Relation)
   - parameter: Disk flattening R_star/H_star = 7.3  
  > "The second step assumes a fixed disk flattening of $R_{\star}/H_{\star}$=7.3." (4.4 The Resolved Dynamical Equilibrium Pressure Relation)
   - assumption: Isothermal plane-parallel gas and stellar disks; smooth disk (no clumping)  
  > "where the gas and stars in the galactic disk are modelled as isothermal fluids in a plane-parallel geometry" (4.4 The Resolved Dynamical Equilibrium Pressure Relation); "Clumpy sub-structure contributes additional weight to the mid-plane pressure compared to the assumption (used here) of a smooth disk." (4.4 The Resolved Dynamical Equilibrium Pressure Relation)
   - fitting: _not stated_
   - validation: Impact of assumptions tested in Section 5.3  
  > "In this sub-section, we consider whether the assumptions used in our calculation of $P_{DE}$ might explain the observed discrepancy between the PRFM model and the extended ALMaQUEST data" (5.3 Uncertainties in the measurement of P_DE)
6. **Fit the four scaling relations (rSK, rMGMS, rSFMS, rPDE) and compare scatter**: Orthogonal distance regression fits per sample, scatter around fit compared, and a free broken power law fitted to rPDE  
  > "The dashed line in each panel shows the orthogonal distance regression (ODR) fit, with fit coefficients given explicitly in each panel." (4.1 The Resolved Schmidt-Kennicutt Relation); "we experimented with fitting a broken power law to the full star-forming spaxel sample, leaving both the exponents and the break point as free parameters" (4.4 The Resolved Dynamical Equilibrium Pressure Relation)
   - fitting: ODR for linear fits; broken power law with free exponents and break point; fitting software, priors and errors not stated  
  > "leaving both the exponents and the break point as free parameters" (4.4 The Resolved Dynamical Equilibrium Pressure Relation)
   - validation: Broken power law residuals only 0.01 dex smaller than single power law  
  > "the residuals of the best fit broken power law are only 0.01 dex smaller than the single power law fit" (4.4 The Resolved Dynamical Equilibrium Pressure Relation)
7. **Compare rPDE with the PRFM prediction**: Overplot the Ostriker & Kim (2022) PRFM relation on the spaxel data in the full, control, central starburst and merger samples  
  > "In addition to the ODR fit (black dashed line), we also show (red dot-dashed line) the theoretical prediction of the PRFM model of Ostriker & Kim (2022)" (4.4 The Resolved Dynamical Equilibrium Pressure Relation)
   - fitting: _not stated_
   - validation: _not stated_
8. **Split by offset from the global SFMS (Delta SFR)**: Compute Delta SFR vs a control sample matched in stellar mass, 5th nearest neighbour density and redshift; bin galaxies and compare rPDE per bin; median per-galaxy offset from the PRFM relation vs Delta SFR  
  > "This is achieved by comparing a given galaxy’s SFR to a control sample matched within 0.1 dex in total stellar mass, within 0.1 dex of 5th nearest neighbour density and within 0.005 in redshift" (5.1 Is the rPDE relation universal?); "either at least a factor of two below the SFMS (bottom panel), within a factor of two of the SFMS (middle panel) or at least a factor of two above the SFMS (top panel)" (5.1 Is the rPDE relation universal?)
   - parameter: Control matching tolerances: 0.1 dex mass, 0.1 dex 5th-NN density, 0.005 redshift  
  > "within 0.1 dex in total stellar mass, within 0.1 dex of 5th nearest neighbour density and within 0.005 in redshift" (5.1 Is the rPDE relation universal?)
   - fitting: Pearson correlation test between offset and Delta SFR (values only in figure)  
  > "Pearson correlation test results are given in the lower left of the panel" (5.1 Is the rPDE relation universal?)
   - validation: _not stated_
9. **Random forest ranking of predictors of Sigma_SFR**: Random forest with Sigma_SFR as target and Sigma_H2, Sigma_star, P_DE (plus two combination variables and a random variable) as features; importances over 100 realizations  
  > "The target variable of our random forest is $\Sigma_{\rm SFR}$." (5.2 Is the rPDE relation the most fundamental star formation scaling relation?); "where the error bars represent the variance in 100 independent realizations of the training, validation and testing data" (5.2 Is the rPDE relation the most fundamental star formation scaling relation?)
   - assumption: Relative importances are only valid for the fixed feature set (sum to one)  
  > "their quantitative values are only relevent for the fixed feature set included in our test" (5.2 Is the rPDE relation the most fundamental star formation scaling relation?)
   - fitting: Random forest; hyperparameters not stated  
  > "A random forest consists of a series of decision trees which can be used to assess the relative importance of input variables in determining a given target variable." (5.2 Is the rPDE relation the most fundamental star formation scaling relation?)
   - validation: Random variable and two alternative Sigma_star/Sigma_H2 combinations included as controls; MSE reported for training and testing data  
  > "for reference, a random variable is shown in the final bar" (5.2 Is the rPDE relation the most fundamental star formation scaling relation?); "The mean squared error (MSE) is reported in the top right of the figure for both the training and testing data." (5.2 Is the rPDE relation the most fundamental star formation scaling relation?)
10. **Test whether P_DE assumptions explain the PRFM discrepancy**: Vary Sigma_HI, alpha_CO prescriptions, use measured CO velocity dispersion, remove extreme spaxels, and use the Hassan et al. (in prep) P_DE formula  
  > "We have to increase the atomic contribution to $\Sigma_{\rm HI}$ $\sim$ 14 M$_{\odot}$ pc$^{-2}$ before there is some reasonable agreement between the data and the model at low $P_{DE}$." (5.3.1 Assumption of a fixed Sigma_HI); "Artificially lowering the conversion factor by only 50% is sufficient to bring the high $P_{DE}$ spaxels into line with the model" (5.3.2 Assumption of a fixed CO-to-H2 conversion factor)
   - parameter: Spaxel purges: line width > 20 km/s, Sigma_tot > 300 Msun pc^-2, within 2 kpc of galaxy centre  
  > "We try removing spaxels with line widths larger than 20 km s$^{-1}$" (5.3.2 Assumption of a fixed CO-to-H2 conversion factor)
   - fitting: _not stated_
   - validation: No tested variation removes the disagreement with the PRFM model  
  > "In summary, we have not identified any methodological cause for the disagreement between the observed rPDE relation in the extended ALMaQUEST sample and the PRFM model." (5.3 Uncertainties in the measurement of P_DE)
11. **Compare rPDE with the Krumholz et al. (2018) turbulence-driven model**: Evaluate Sigma_SFR(P_DE) from the Krumholz et al. (2018) Toomre-timescale model with KMT+ molecular fraction for three orbital times and overplot on data  
  > "Indeed, reasonable choices of the orbital time result in predictions that encompass all of the data." (5.4 What causes the discrepancy)
   - parameter: epsilon_ff = 0.015  
  > "is set to be 0.015, consistent with a wide range of environments" (5.4 What causes the discrepancy)
   - parameter: f_g,P = 0.33 (median in extended ALMaQUEST)  
  > "since this is the median value in the extended ALMaQUEST dataset" (5.4 What causes the discrepancy)
   - parameter: clumping factor 5  
  > "following Krumholz et al. 2009, we adopt a value of 5" (5.4 What causes the discrepancy)
   - assumption: Flat rotation curve (beta = 0)  
  > "We also use a fixed value of $\beta = 0$, i.e. a flat rotation curve." (5.4 What causes the discrepancy)
   - fitting: _not stated_
   - validation: Qualitative agreement with data at high P_DE  
  > "It can be seen that the flatter slope predicted by the Krumholz et al. (2018) model is in much better agreement with the data at high $P_{DE}$" (5.4 What causes the discrepancy)

## Software

- **CASA** : Processing of the ALMA data cubes  
  > "The data cubes were all processed using the Common Astronomy Software Applications (CASA; McMullin et al. 2007) package." (3.2 ALMA data)
- **PIPE3D** : Source of MaNGA emission-line cubes, stellar mass surface densities and VAC masses/SFRs  
  > "Optical emission line fluxes are taken from the public PIPE3D data cubes (Sánchez et al. 2016a,b, 2018)" (3.1 MaNGA data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of galaxies in extended ALMaQUEST sample | 66 | not stated | galaxies | 0 | The extended ALMaQUEST sample consists of a total of 66 galaxies, all of which were drawn from the MaNGA DR15. |
| Control sample size | 16 | not stated | galaxies | 0 | consists of 16 galaxies which have axial ratios |
| Central starburst sample size | 11 | not stated | galaxies | 0 | there are 11 central starburst galaxies in our sample |
| Merger sample size | 19 | not stated | galaxies | 0 | 19 galaxies fulfill this requirement |
| Full star-forming CO-detected spaxel sample | 19,999 | not stated | spaxels | 4 | There is a total of 19,999 spaxels that fulfill both the star-forming criteria |
| Star-forming spaxels in control, central starburst, merger samples | 8321, 5357, 4176 | not stated | spaxels | 4 | The control, central starburst and merger samples contain 8321, 5357 and 4176 star-forming spaxels respectively |
| Spaxels with metallicity measurements | 16,254 | not stated | spaxels | 2 | only 16,254 have metallicity measurements |
| Typical uncertainty in Sigma_H2 | < 0.1 | not stated | dex | 2 | Typical uncertainties in $\Sigma_{\rm H_2}$ are $<$ 0.1 dex. |
| Scatter of rSK relation across sub-samples | 0.2-0.3 | not stated | dex | 6 | A strong rSK exists for all of these galaxy sub-samples with scatter of 0.2–0.3 dex |
| Maximum scatter of rSFMS | 0.34 | not stated | dex | 6 | the scatter is larger than the previous two relations, up to 0.34 dex |
| rSFMS scatter in central starbursts (ODR) | 0.21 | not stated | dex | 6 | only 0.21 dex in the ODR fit |
| Range of rSFMS best-fit slopes across samples | 0.65 to 1.55 | not stated | dimensionless | 6 | ranging between 0.65 and 1.55 |
| rPDE scatter across the samples | ~0.2-0.3 | not stated | dex | 6 | with a scatter whose magnitude of $\sim$ 0.2 – 0.3 dex is broadly consistent with that of the other three star formation scaling relations |
| Break pressure of rPDE broken power law | log P_DE/k_B = 4.528 | not stated | K cm^-3 | 6 | for values of log $P_{DE}/k_B$ below and above 4.528 K cm$^{-3}$ respectively |
| Broken power law, below break: intercept and slope | log Sigma_SFR = -7.09 + 1.12 log(P_DE/k_B) | not stated | dimensionless | 6 | -7.09 + 1.12 |
| Broken power law, above break: intercept and slope | log Sigma_SFR = -4.87 + 0.63 log(P_DE/k_B) | not stated | dimensionless | 6 | -4.87 + 0.63 |
| Improvement in residual scatter, broken vs single power law | 0.01 | not stated | dex | 6 | the residuals of the best fit broken power law are only 0.01 dex smaller than the single power law fit |
| Spaxels in galaxies with Delta SFR > +0.3 dex | over 11,000 | not stated | spaxels | 8 | Containing over 11,000 spaxels |
| Median CO line-of-sight velocity dispersion | ~11 (tail to 80) | not stated | km/s | 10 | Although the median value in the data is $\sim$ 11 km s$^{-1}$ (which is also the spectral resolution of the ALMaQUEST data), there is a tail to values as large as 80 km s$^{-1}$. |
| Sigma_HI needed to match model at low P_DE | ~14 | not stated | Msun pc^-2 | 10 | We have to increase the atomic contribution to $\Sigma_{\rm HI}$ $\sim$ 14 M$_{\odot}$ pc$^{-2}$ |
| Reduction in P_DE with Hassan et al. formulation | ~5 | not stated | percent | 10 | find that $P_{DE}$ is typically reduced by $\sim$ 5% compared with the fiducial calculation |

## Qualitative findings

- The rPDE relation flattens at high pressure in the full sample, a turnover not predicted by the PRFM model  
  > "the presence of more vigourously star-forming galaxies in the extended ALMaQUEST sample reveals a marked turnover in the relation at high pressures" (abstract)
- Random forest finds P_DE far more important than Sigma_H2 or Sigma_star for predicting Sigma_SFR  
  > "Our random forest therefore demonstrates that $P_{DE}$ is a far superior predictor of $\Sigma_{\rm SFR}$ than $\Sigma_{\rm H_2}$ or $\Sigma_{\star}$ alone" (5.2 Is the rPDE relation the most fundamental star formation scaling relation?)
- The rPDE relation is not universal between galaxies  
  > "We conclude that the rPDE relation is not universal between galaxies." (5.1 Is the rPDE relation universal?)

## Claim tuples

- H: Do the rSK, rMGMS and rSFMS relations persist in mergers and central starbursts as well as normal galaxies? | E: ODR fits and scatter of each relation in the full, control, central starburst and merger spaxel samples | R: Strong relations in all sub-samples with scatter of about 0.2-0.3 dex (rSFMS up to 0.34 dex) | F: The three standard relations persist even under more extreme conditions | **supported**
- H: Does the rPDE relation follow the linear PRFM prediction across the diverse extended sample? | E: ODR and broken power law fits to rPDE for the full sample and sub-samples, compared with the Ostriker & Kim (2022) relation | R: Relation flattens above log P_DE/k_B of about 4.5; break at 4.528 K cm^-3; central starbursts flatter than predicted | F: The data are non-linear and deviate from the PRFM model at high pressure | **supported**
- H: Is P_DE a more fundamental predictor of Sigma_SFR than Sigma_H2 or Sigma_star? | E: Compare RMS scatter around linear fits, then run a random forest with Sigma_SFR as target | R: rPDE scatter is no smaller than the other relations, but the random forest ranks P_DE far above Sigma_H2 and Sigma_star | F: P_DE is the most predictive variable tested even though the linear scatter does not show it | **partially**
- H: Does the PRFM model agree with galaxies on, above and below the global SFMS? | E: rPDE relation in three Delta SFR bins, plus per-galaxy median offset from the PRFM relation vs Delta SFR | R: Agreement for galaxies within a factor of two of the SFMS; significant deviations above and below | F: PRFM works for main-sequence galaxies and breaks down for extreme SFRs | **supported**
- H: Can extra sources of turbulence (Krumholz et al. 2018) account for the high-SFR deviations? | E: Evaluate the Krumholz et al. (2018) model for three orbital times and overplot on the rPDE data | R: Model curves with reasonable orbital times encompass the data, with flatter slope at high P_DE | F: Data are qualitatively consistent with turbulence not always coming from star formation alone | **partially**

## Reasoning

- Why this data: Extended ALMaQUEST adds mergers and starbursts to test PRFM beyond normal main-sequence spirals  
  > "Here, we aim to further the comparison of the PRFM model with an additional dataset that includes a wider range of galaxies than those previously assessed." (Introduction)
- Why this method: Random forest chosen because the rPDE relation is non-linear and linear scatter is inadequate  
  > "We therefore turn to a random forest analysis, which is powerful at extracting non-linear dependences in data." (5.2 Is the rPDE relation the most fundamental star formation scaling relation?)
- Alternative: Metallicity-dependent alpha_CO, Accurso et al. alpha_CO, lower alpha_CO, Sigma_tot and line-width dependent alpha_CO all tested; none reconciled data and PRFM model  
  > "we have not identified a physically motivated formalism that can achieve this" (5.3.2 Assumption of a fixed CO-to-H2 conversion factor)
- Alternative: Using the measured CO velocity dispersion instead of 11 km/s did not reduce the offset in high SFR galaxies  
  > "We find that using the measured values of the CO velocity dispersion does not reduce the offset between the model and theory in high SFR galaxies." (5.3.3 Assumption of a fixed gas velocity dispersion)
- Alternative: Hassan et al. (in prep) P_DE formulation does not resolve the discrepancy  
  > "The disagreement between our highly star-forming galaxies and the PRFM model is therefore not resolved by using this new formalism." (5.4 What causes the discrepancy)
- How they decided it was enough: _not stated_
- Limitation (authors): No HI measurement; Sigma_HI fixed at 7 Msun pc^-2  
  > "In the absence of a measurement of $\Sigma_{HI}$, we assume a fixed value of $\Sigma_{HI}$ = 7 M$_{\odot}$ pc$^{-2}$" (4.4 The Resolved Dynamical Equilibrium Pressure Relation)
- Limitation (authors): Fixed alpha_CO is almost certainly incorrect  
  > "This is almost certainly an incorrect assumption" (5.3.2 Assumption of a fixed CO-to-H2 conversion factor)
- Limitation (authors): Measured CO velocity dispersions are upper limits for the vertical dispersion (rotation not removed)  
  > "since we have not modelled and removed disk rotation, these velocity dispersions represent an upper limit to the possible value of $\sigma_{gas,z}$" (5.3.3 Assumption of a fixed gas velocity dispersion)
- Limitation (authors): Unresolved clumping may lead to an underestimate of P_DE  
  > "the impact of sub-structure may lead to an under-estimate of $P_{DE}$ in the ALMaQUEST data" (4.4 The Resolved Dynamical Equilibrium Pressure Relation)
- Caveat (inferred, ours): alpha_CO appears as both 4.3 and 4.35 in the text; unclear which is used for the integrated masses
- Caveat (inferred, ours): Inclination correction using b/a for all surface densities is uncertain for mergers and face-on galaxies
- Caveat (inferred, ours): Constant Sigma_HI, sigma_gas,z and R_star/H_star shift P_DE together with Sigma_star and Sigma_H2, so part of the rPDE tightness may be built in
- Caveat (inferred, ours): Random forest importances depend on the chosen feature set and the P_DE feature contains Sigma_star and Sigma_H2 by construction
- Caveat (inferred, ours): Cycle 7 and earlier data are processed with different proposals and depths; uniformity of CO S/N>3 selection across the sample is not shown

## Reproducibility

- Data public (paper): Spaxel-level table (Sigma_SFR, Sigma_star, Sigma_H2) released with the paper  
  > "The data used in this paper are all released in a supplementary table in the electronic version of this paper." (Data Availability); "we provide a public release of the star formation rate, stellar mass and molecular gas surface densities for all star-forming spaxels in the extended sample of 66 galaxies to permit a reproduction of these relations" (Introduction)
- Products in archive: _not stated_
- Missing: Raw ALMA calibration and imaging recipe (deferred to Lin et al. 2020 and Thorp et al. 2022)
- Missing: Random forest hyperparameters and code
- Missing: ODR and broken power-law fitting code and error treatment
- Missing: Inputs for the Krumholz et al. (2018) curves (orbital times, Q)
- Missing: Per-spaxel velocity dispersions and metallicities used in robustness tests are not stated as released
- Data volume (inferred): Five ALMA projects of 66 CO(1-0) cubes; raw plus products likely tens of GB, but the released spaxel table (about 20,000 rows) suffices for the main analysis
- Score (inferred): 3/5, Spaxel-level table is public and the P_DE, fitting and comparison recipe is mostly given, but ALMA processing is inherited from earlier papers and random forest and fitting details are missing.
- Rediscovery candidate: yes, The derived spaxel table is released and the main results (ODR fits, scatter, broken power law break at 4.528, P_DE formula with fixed Sigma_HI and sigma) are numeric; the random forest ranking is only reproducible qualitatively.

## Links

- Method: Lin et al. (2020) (Describes ALMaQUEST sample and ALMA acquisition and processing for the original 46 galaxies)
- Method: Thorp et al. (2022) (Describes the Cycle 7 merger observations and identical processing)
- Method: Sun et al. (2020a) (P_DE implementation followed)
- Method: Bluck et al. (2022) (Appendix B gives the random forest methodology)
- Companion: Ellison et al. (2021a) (Earlier ALMaQUEST scaling-relation analysis)
- Companion: Lin et al. (2019) (Introduced the rSK/rMGMS/rSFMS ALMaQUEST analysis)
- Companion: Ellison et al. (2020a) (Central starburst sample and selection)
- Companion: Baker et al. (2022) (Earlier random forest analysis of Sigma_H2 and Sigma_star)
- Related: ALMaQUEST
- Related: SDSS-IV MaNGA
- Related: PHANGS
- Related: EDGE-CALIFA
- Related: KINGFISH
- Related: DYNAMO

## Checks

```json
{
 "quotes": 139,
 "quotes_ok": 139,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 21,
 "numeric_problems": 0,
 "fill": {
  "facts": 125,
  "stated": 88,
  "rate": 0.704
 },
 "evidence_ok": true
}
```
