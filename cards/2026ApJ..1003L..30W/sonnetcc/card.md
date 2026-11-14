# First Detection of HC<SUB>5</SUB>N in a Class II Disk around TW Hya

`2026ApJ..1003L..30W` | The Astrophysical Journal Letters 2026 | first author: Wampler, Steven C. | arXiv: 2606.02815 | DOI: 10.3847/2041-8213/ae66e5

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Is the long cyanopolyyne HC5N present in the Class II TW Hya disk, what is its column density and HC3N/HC5N ratio, and what do chemical models say about its formation and emitting layer?  
  > "Here, we report the first detection of HC$_5$N toward the TW Hya protoplanetary disk, representing the largest cyanopolyyne identified to date in a Class II system." (abstract); "We compare HC$_5$N and HC$_3$N formation mechanisms and analyze the HC$_3$N / HC$_5$N ratio." (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance 60 pc (d = 59.5 pc used for the Keplerian mask)  
  > "The protoplanetary disk around TW Hya, located at a distance of 60 pc (cite: Gaia_Collaboration)" (Introduction); "distance 60 pc, and stellar mass 0.88" (3.3 GoFish Spectra and Flux Measurements); distance from Gaia Collaboration  
  > "The protoplanetary disk around TW Hya, located at a distance of 60 pc (cite: Gaia_Collaboration)" (Introduction); "distance 60 pc, and stellar mass 0.88" (3.3 GoFish Spectra and Flux Measurements)

## Data provenance

- ALMA projects: 2019.1.00769.S
- bands: Band 3  
  > "in Band 3 as part of the ALMA Cycle 6 project 2019.1.00769.S" (2.1 Observational Details)
- frequencies and spectral setup: TDM continuum window at 110.169 GHz; six FDM windows at 99.665, 100.078, 98.541, 96.982, 109.173, 108.715 GHz, each 58.594 MHz wide with 30.518 kHz channels (~0.08 km/s)  
  > "Frequency Division Mode (FDM) spectral windows centered at 99.665, 100.078, 98.541, 96.982, 109.173, and 108.715 GHz." (2.1 Observational Details); "These spectral windows had a bandwidth of 58.594 MHz and channel spacing of 30.518 kHz" (2.1 Observational Details)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: beam 1.07" x 0.86" (HC5N 37-36); 0.97" x 0.77" (HC5N 41-40 and HC3N 12-11)  
  > "This resulted in a beam of 1.07" x 0.86"" (2.2 Calibration and Imaging); "transition and 0.97" x 0.77"" (2.2 Calibration and Imaging)
- max recoverable scale: _not stated_
- sensitivity: rms ~1.1 mJy/beam (HC5N 37-36), ~1.3 mJy/beam (HC5N 41-40), ~1.3 mJy/beam (HC3N 12-11)  
  > "The achieved rms values were $\sim$1.1 and $\sim$1.3 mJy bm$^{-1}$ respectively for the J=37-36 and J=41-40 HC$_5$N transitions, and $\sim$1.3 mJy bm$^{-1}$ for HC$_3$N J=12-11." (2.2 Calibration and Imaging)
- time on source: 325 minutes total, 7 execution blocks  
  > "The total on-source integration time was 325 minutes." (2.1 Observational Details)
- observing dates: 22, 23, 25 and 28 March 2021  
  > "TW Hya was observed over 7 execution blocks on 22-Mar-2021, 23-Mar-2021, 25-Mar-2021, and 28-Mar-2021" (2.1 Observational Details)
- pi or archival as stated: _not stated_
- Line: HC3N J=12-11 (109173.63 MHz)
- Line: HC5N J=37-36 (98512.524 MHz)
- Line: HC5N J=41-40 (109160.973 MHz)
- Other facility **Gaia**: TW Hya distance (60 pc)  
  > "located at a distance of 60 pc (cite: Gaia_Collaboration)" (Introduction)
- External data: TW Hya disk geometry and stellar mass (i = 5 deg, PA = 152 deg, M* = 0.88 Msun, d = 59.5 pc) used for the Keplerian mask and GoFish shift-and-stack  
  > "based on the adopted TW Hya disk geometry" (2.2 Calibration and Imaging); "The well established parameters of TW Hya were adopted" (3.3 GoFish Spectra and Flux Measurements) [from (cite: Huang_2018; Andrews_2012; Gaia_Collaboration)]
- External data: Typical disk HC3N column densities used for comparison with the derived HC5N values  
  > "These values are one to two orders of magnitude lower than typical HC$_3$N column densities reported for disks (cite: Bergner_2018; Ilee_2021)" (3.4 Column Density Analysis) [from (cite: Bergner_2018; Ilee_2021)]
- External data: Assumed rotational temperature range 20-50 K reasonable for Class II T Tauri disks  
  > "that are reasonable rotational temperatures for Class II T Tauri disks (cite: Aikawa_2002; Oberg&Bergin_2021)" (3.4 Column Density Analysis) [from (cite: Aikawa_2002; Oberg&Bergin_2021)]
- External data: TW Hya FUV spectrum used in the chemical model  
  > "The TW Hya FUV spectrum from (cite: Herczeg_2002; Herczeg_2004)" (4.2 Comparison of Chemical Models and Observations) [from (cite: Herczeg_2002; Herczeg_2004)]
- External data: TW Hya X-ray spectrum used in the chemical model  
  > "the X-ray spectrum from (cite: Cleeves_2013) are used" (4.2 Comparison of Chemical Models and Observations) [from (cite: Cleeves_2013)]
- External data: Elevated outer-disk C/O in TW Hya motivating the C/O values of the models  
  > "TW Hya shows significant evidence for enhanced C/O ratios in its outer disk (cite: Bergin_2016; Kama_2016; Cleeves_2021)" (4.2 Comparison of Chemical Models and Observations) [from (cite: Bergin_2016; Kama_2016; Cleeves_2021)]
- Simulation/model as data: 2D time-dependent disk chemistry model (OSU gas-phase network, expanded), Rc = 40 AU, disk mass 0.1 Msun, 90% large grains, 1 Myr, C/O = 0.57, 1.0, 1.5, run to predict HC3N and HC5N column density profiles  
  > "with an exponential taper beyond a characteristic radius R$_c$ of 40 AU, and a total disk mass of 0.1" (4.2 Comparison of Chemical Models and Observations); "Three different C/O ratios were considered: 0.57 (solar-like), 1.0, and 1.5." (4.2 Comparison of Chemical Models and Observations); "and the model is evolved for 1 Myr." (4.2 Comparison of Chemical Models and Observations)

## Processing

### Calibration

- pipeline or manual: ALMA observatory pipeline calibration, then additional self-calibration by the authors  
  > "The data were initially calibrated by the ALMA Observatory using the ALMA pipeline version 2020.1.0.40 (cite: Hunter_2023) in CASA 6.1.1.15." (2.2 Calibration and Imaging)
- casa version: CASA 6.1.1.15  
  > "using the ALMA pipeline version 2020.1.0.40 (cite: Hunter_2023) in CASA 6.1.1.15." (2.2 Calibration and Imaging)
- pipeline version: ALMA pipeline 2020.1.0.40  
  > "using the ALMA pipeline version 2020.1.0.40 (cite: Hunter_2023)" (2.2 Calibration and Imaging)
- archive products used as is: _not stated_
- flux calibrator: J1107-4449 (also bandpass); phase calibrator J1037-2934  
  > "The quasar J1037-2934 was used for phase calibration and J1107-4449 was used as the bandpass and flux calibrator across all executions." (2.2 Calibration and Imaging)
- flux scale uncertainty: _not stated_
- self calibration: three rounds of phase-only and one round of phase and amplitude self-calibration  
  > "We then additionally self-calibrated the data with three rounds of phase-only and one round of phase and amplitude self-calibration." (2.2 Calibration and Imaging)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "natural weighting for maximum sensitivity in CASA 6.1.1.15." (2.2 Calibration and Imaging)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian mask for HC3N CLEAN; no mask for HC5N  
  > "For HC$_3$N a Keplerian mask based on the adopted TW Hya disk geometry" (2.2 Calibration and Imaging); "while no mask was used for the HC$_5$N transitions as there was no significant emission" (2.2 Calibration and Imaging)
- multiscale scales: _not stated_
- continuum subtraction: uv-plane continuum subtraction of the self-calibrated visibilities  
  > "we continuum subtracted the self-calibrated visibilities in the" (2.2 Calibration and Imaging)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.07" x 0.86" PA -84.531 deg (HC5N 37-36); 0.97" x 0.77" PA -85.550 deg (HC5N 41-40, HC3N 12-11)  
  > "This resulted in a beam of 1.07" x 0.86"" (2.2 Calibration and Imaging); "transition and 0.97" x 0.77"" (2.2 Calibration and Imaging)
- final rms: ~1.1 mJy/beam (HC5N 37-36), ~1.3 mJy/beam (HC5N 41-40), ~1.3 mJy/beam (HC3N 12-11)  
  > "The achieved rms values were $\sim$1.1 and $\sim$1.3 mJy bm$^{-1}$ respectively for the J=37-36 and J=41-40 HC$_5$N transitions, and $\sim$1.3 mJy bm$^{-1}$ for HC$_3$N J=12-11." (2.2 Calibration and Imaging)

### Inherited from earlier work

- TW Hya disk geometry and system parameters (i, PA, M*, d, radial sampling) for the Keplerian CLEAN mask  
  > "(cite: Huang_2018; Andrews_2012; Gaia_Collaboration)" (2.2 Calibration and Imaging) [from (cite: Huang_2018; Andrews_2012; Gaia_Collaboration)]
- Matched filtering technique for line detection  
  > "we employed a matched filtering technique (cite: Loomis_2018b) to enhance line detectability." (3.2 Matched Filtering Analysis) [from (cite: Loomis_2018b)]
- Shift-and-stack of spectra with GoFish, correcting for Keplerian rotation  
  > "We applied the `GoFish` package (cite: Teague_2019) to perform a shift and stack analysis (cite: Yen_2016)" (3.3 GoFish Spectra and Flux Measurements) [from (cite: Teague_2019); (cite: Yen_2016)]
- Optically thin column density formula  
  > "Following (cite: Loomis_2018a): assuming optically thin emission, we have:" (3.4 Column Density Analysis) [from (cite: Loomis_2018a)]
- Chemical model code, based on an earlier code and updated networks  
  > "The two dimensional time-dependent chemical code used is based on the one from (cite: Fogel_2011)." (4.2 Comparison of Chemical Models and Observations) [from (cite: Fogel_2011); (cite: Smith_2004); (cite: Cleeves_2014; Cleeves_2015; Cleeves_2018)]
- Stellar FUV and X-ray radiation transfer in the disk model  
  > "see (cite: Cleeves_2013; Cleeves_2014) for details" (4.2 Comparison of Chemical Models and Observations) [from (cite: Bethell_2011a); (cite: Cleeves_2013; Cleeves_2014)]
- Binding energy updates in the chemical network not described here  
  > "Additional updates to several binding energies were made and will be described in a forthcoming paper." (4.2 Comparison of Chemical Models and Observations) [from forthcoming paper (not cited)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals, reference antenna, spectral windows and which scans were used for each of the four rounds
- Line-free channels used for uv continuum subtraction and the fit order
- tclean parameters: deconvolver, cell size, image size, threshold/niter, spectral rebinning and velocity resolution of the cubes
- Whether the cubes were primary-beam corrected before flux extraction
- Matched-filter kernel construction details in VISIBLE and how significance and the 5.3 sigma stack were computed (noise estimate, weighting)
- GoFish settings beyond geometry: radial binning, annulus width, how uncertainties on the integrated flux were derived
- Emitting-region solid angle (Omega) and line FWHM adopted in the column density equation, and the partition function / Einstein A source
- How the two transition column densities were averaged and how the quoted ranges were propagated
- HC3N column-density derivation (flux, Omega, FWHM) behind the HC3N N_T values in Table 2
- Chemical model input files, network version and the forthcoming binding energy updates
- Archive product version / reprocessing used for 2019.1.00769.S

## Analysis recipe

1. **calibrate and self-calibrate visibilities**: Observatory pipeline calibration followed by three phase-only rounds and one phase plus amplitude round of self-calibration  
  > "We then additionally self-calibrated the data with three rounds of phase-only and one round of phase and amplitude self-calibration." (2.2 Calibration and Imaging)
   - software: CASA, ALMA pipeline
   - parameter: ALMA pipeline version 2020.1.0.40 in CASA 6.1.1.15  
  > "using the ALMA pipeline version 2020.1.0.40 (cite: Hunter_2023) in CASA 6.1.1.15." (2.2 Calibration and Imaging)
   - fitting: _not stated_
   - validation: _not stated_
2. **continuum-subtract and image line cubes**: uv-plane continuum subtraction then CLEAN with natural weighting; Keplerian mask for HC3N, no mask for HC5N  
  > "we continuum subtracted the self-calibrated visibilities in the" (2.2 Calibration and Imaging); "natural weighting for maximum sensitivity in CASA 6.1.1.15." (2.2 Calibration and Imaging)
   - software: CASA
   - parameter: Mask geometry i = 5 deg, PA = 152 deg, M* = 0.88 Msun, d = 59.5 pc, dr = 0.1  
  > "with a radial sampling of $dr=0.1$ (cite: Huang_2018; Andrews_2012; Gaia_Collaboration)" (2.2 Calibration and Imaging)
   - assumption: Keplerian rotation with the adopted TW Hya geometry for the HC3N mask  
  > "For HC$_3$N a Keplerian mask based on the adopted TW Hya disk geometry" (2.2 Calibration and Imaging)
   - fitting: _not stated_
   - validation: _not stated_
3. **look for HC5N in the image plane**: Moment 0 maps of HC3N J=12-11 and the two HC5N lines; HC5N maps show no strong signal  
  > "These moment maps show no strong signal." (3.1 HC$_3$N and HC$_5$N Integrated Intensity)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
4. **matched-filter detection of HC5N**: Matched filter applied to visibilities across all spectral windows using an empirical kernel from the strong HC3N J=12-11 emission; individual and stacked significances measured  
  > "use here an empirical filter kernel from the strong HC$_3$N J=12-11 emission illustrated in Figure" (3.2 Matched Filtering Analysis); "This kernel was applied to the observed visibilities across all spectral windows." (3.2 Matched Filtering Analysis)
   - software: VISIBLE
   - assumption: HC5N shares the spatio-kinematic structure and morphology of HC3N  
  > "with the assumption that HC$_3$N and HC$_5$N likely share a similar morphology." (3.2 Matched Filtering Analysis)
   - fitting: _not stated_
   - validation: Multiple filter kernels tried with similar results  
  > "We examined multiple filter kernels, all of which had similar results" (3.2 Matched Filtering Analysis)
5. **measure integrated line fluxes**: GoFish shift-and-stack correcting for Keplerian rotation, spectra extracted within 90 AU, integrated over 2.0-3.7 km/s defined from HC3N  
  > "Spectra were extracted within a radius of 90 AU, based on the emission extent of HC$_3$N" (3.3 GoFish Spectra and Flux Measurements); "GoFish analysis of HC3N J=12-11 shows emission from 2.0–3.7 km s$^{-1}$" (3.3 GoFish Spectra and Flux Measurements)
   - software: GoFish
   - parameter: i = 5 deg, PA = 152 deg, distance 60 pc, M* = 0.88 Msun  
  > "distance 60 pc, and stellar mass 0.88" (3.3 GoFish Spectra and Flux Measurements)
   - parameter: Extraction radius 90 AU; integration range 2.0-3.7 km/s  
  > "Using the same integration range between 2.0–3.7 km s$^{-1}$ yields fluxes of" (3.3 GoFish Spectra and Flux Measurements)
   - assumption: Well-established TW Hya parameters adopted from the literature  
  > "The well established parameters of TW Hya were adopted" (3.3 GoFish Spectra and Flux Measurements)
   - fitting: _not stated_
   - validation: Authors state the flux does not alone confirm the detection because of low signal to noise  
  > "however due to low signal to noise, this does not alone confirm the detection of these transitions." (3.3 GoFish Spectra and Flux Measurements)
6. **derive HC5N column densities**: Direct optically thin LTE column density from each flux at assumed T_rot (20, 30, 40, 50 K), then averaged; no rotation diagram  
  > "we opt to directly calculate column densities from the two fluxes and some assumed rotational temperature, and then average them." (3.4 Column Density Analysis)
   - parameter: T_rot range 20-50 K  
  > "we can then estimate column densities of HC$_5$N for a range of 20K-50K" (3.4 Column Density Analysis)
   - assumption: Optically thin emission in LTE  
  > "for assumed $T_{rot}$ = 20-50 K and optically thin emission in LTE" (abstract)
   - fitting: _not stated_
   - validation: Compared with HC3N column densities in disks and with model predictions  
  > "A comparison to predictions of 2D time-dependent chemical models is presented in Section 4.2." (3.4 Column Density Analysis)
7. **compare with a 2D disk chemistry model**: Ran a small set of disk chemistry models at three C/O ratios and compared vertically integrated HC3N and HC5N column density profiles with the observed values  
  > "To aid interpretation of the observations we ran a small set of disk chemistry models." (4.2 Comparison of Chemical Models and Observations)
   - parameter: C/O = 0.57, 1.0, 1.5; Rc = 40 AU; disk mass 0.1 Msun; evolved 1 Myr  
  > "Three different C/O ratios were considered: 0.57 (solar-like), 1.0, and 1.5." (4.2 Comparison of Chemical Models and Observations)
   - parameter: Cosmic ray ionization rate 1.3e-18 s-1  
  > "a cosmic ray ionization rate of $\zeta_{\rm CR} = (1.3)\times10^{-18}$ s$^{-1}$" (4.2 Comparison of Chemical Models and Observations)
   - assumption: 90% large dust grains; self-similar viscous surface density with exponential taper  
  > "The disk physical structure is described using a standard self-similar viscous surface-density prescription" (4.2 Comparison of Chemical Models and Observations)
   - fitting: _not stated_
   - validation: Model HC5N column density ~1e12 cm-2 in moderate agreement with estimate, especially for T_rot >= 30 K  
  > "This value is in moderate agreement with our estimated column density" (4.2 Comparison of Chemical Models and Observations)

## Software

- **CASA** 6.1.1.15: Calibration, continuum subtraction and CLEAN imaging  
  > "natural weighting for maximum sensitivity in CASA 6.1.1.15." (2.2 Calibration and Imaging)
- **ALMA pipeline** 2020.1.0.40: Initial observatory calibration  
  > "initially calibrated by the ALMA Observatory using the ALMA pipeline version 2020.1.0.40" (2.2 Calibration and Imaging)
- **GoFish** : Shift-and-stack spectra and integrated flux measurement  
  > "We applied the `GoFish` package (cite: Teague_2019) to perform a shift and stack analysis" (3.3 GoFish Spectra and Flux Measurements)
- **VISIBLE** : Matched filter analysis (cited as Loomis_2018b)  
  > "VISIBLE (cite: Loomis_2018b)" (Software); "we employed a matched filtering technique (cite: Loomis_2018b) to enhance line detectability." (3.2 Matched Filtering Analysis)
- **Astropy** : _not stated_
- **Matplotlib** : _not stated_
- **NumPy** : _not stated_
- **ChatGPT 5.1** 5.1: Limited text editing and code formatting assistance  
  > "for limited assistance with text editing and code formatting." (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HC5N J=37-36 matched-filter significance | 3.4 | not stated | sigma | 4 | individual line significances of 3.4$\sigma$ and 4.2$\sigma$ for the J=37-36 and J=41-40 transitions, respectively |
| HC5N J=41-40 matched-filter significance | 4.2 | not stated | sigma | 4 | individual line significances of 3.4$\sigma$ and 4.2$\sigma$ for the J=37-36 and J=41-40 transitions, respectively |
| HC5N stacked detection significance (two transitions) | 5.3 | not stated | sigma | 4 | A stacked spectrum of the two transitions produces a 5.3$\sigma$ detection of the species. |
| HC5N J=37-36 integrated flux density | 3.7 | 3.5 | mJy km/s | 5 | 3.7$\pm$3.5 |
| HC5N J=41-40 integrated flux density | 8.3 | 6.3 | mJy km/s | 5 | 8.3$\pm$6.3 |
| HC3N J=12-11 integrated flux density | 275 | 28 | mJy km/s | 5 | 275$\pm$28 |
| HC5N column density at T_rot = 20 K | 1.3e13 | 1.0e13 | cm-2 | 6 | $1.3\pm1.0\times10^{13}$ |
| HC5N column density at T_rot = 30 K | 3.4e12 | 2.7e12 | cm-2 | 6 | $3.4\pm2.7\times10^{12}$ |
| HC5N column density at T_rot = 40 K | 1.9e12 | 1.5e12 | cm-2 | 6 | $1.9\pm1.5\times10^{12}$ |
| HC5N column density at T_rot = 50 K | 1.4e12 | 1.1e12 | cm-2 | 6 | $1.4\pm1.1\times10^{12}$ |
| HC3N column density at T_rot = 20 K | 2.1e13 | 0.2e13 | cm-2 | 6 | $2.1\pm0.2\times10^{13}$ |
| HC3N/HC5N ratio at T_rot = 20 K | 0.9-7 | not stated | dimensionless | 6 | / 0.9–7 / |
| HC3N/HC5N ratio at T_rot = 50 K | 8-63 | not stated | dimensionless | 6 | / 8–63 / |
| Modelled disk-averaged HC5N column density | ~1e12 | not stated | cm-2 | 7 | while the HC$_5$N disk-averaged column density is $\sim$10$^{12}$ cm$^{-2}$. |

## Qualitative findings

- HC5N is consistently less abundant than HC3N across the assumed T_rot range, consistent with the steep decline with chain length seen in cold clouds such as TMC-1  
  > "we find that HC$_5$N is consistently less abundant than HC$_3$N" (4.1 Formation Chemistry & Emission Region of HC$_5$N)
- Models need elevated C/O (above 1.0) to raise HC3N and HC5N column densities, with enhanced formation in the inner 10 AU  
  > "Both show monotonically decreasing column densities with radius and elevated column densities when the C/O ratio is enhanced beyond 1.0" (4.2 Comparison of Chemical Models and Observations)

## Claim tuples

- H: Is HC5N, a larger cyanopolyyne, present in the Class II TW Hya disk? | E: Band 3 observations of two HC5N lines analysed with a matched filter built from HC3N J=12-11 and a GoFish shift-and-stack | R: 3.4 and 4.2 sigma individually, 5.3 sigma stacked; fluxes 3.7 +/- 3.5 and 8.3 +/- 6.3 mJy km/s | F: First (tentative) detection of HC5N in a Class II disk | **partially**
- H: What HC5N column density does the detection imply? | E: Optically thin LTE column densities from the two GoFish fluxes at assumed T_rot of 20-50 K | R: N_T of order 1e12 cm-2, 1.3e13 at 20 K down to 1.4e12 at 50 K | F: HC5N column density ~1e12 cm-2, one to two orders of magnitude below typical disk HC3N | **supported**
- H: Does the HC3N/HC5N ratio follow the decline of cyanopolyynes with chain length seen in cold clouds? | E: Compared HC5N and HC3N column densities from Table 2 across assumed temperatures | R: HC5N consistently less abundant than HC3N | F: Disk chemistry can reach long carbon chains, with abundance declining rapidly with size | **partially**
- H: Can a TW Hya-like disk chemistry model reproduce the HC5N abundance and where does it emit? | E: 2D time-dependent chemical models at C/O = 0.57, 1.0, 1.5 compared with the derived column densities | R: Model HC5N disk-averaged column density ~1e12 cm-2, in moderate agreement, better for T_rot >= 30 K; elevated C/O needed | F: HC5N plausibly originates in the warm molecular layer where CN and small hydrocarbons coexist, with elevated C/O | **partially**

## Reasoning

- Why this data: The observations targeted HC3N and isotopologues; two HC5N lines fell in the setup as bonus lines  
  > "two transitions of HC$_{5}$N were targeted as ancillary bonus lines" (2.1 Observational Details)
- Why this method: No obvious image-plane HC5N detection, so matched filtering was used to enhance detectability  
  > "Given the lack of an obvious image plane detection of the individual HC$_5$N transitions, we employed a matched filtering technique" (3.2 Matched Filtering Analysis)
- Alternative: Multiple matched-filter kernels were tried and gave similar results  
  > "We examined multiple filter kernels, all of which had similar results" (3.2 Matched Filtering Analysis)
- Alternative: A rotation diagram was not constructed because only two highly uncertain fluxes were available  
  > "Rather than attempting to construct a rotation diagram from two highly uncertain flux values" (3.4 Column Density Analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Measured HC5N fluxes are low signal to noise and do not alone confirm the detection  
  > "due to low signal to noise, this does not alone confirm the detection of these transitions." (3.3 GoFish Spectra and Flux Measurements)
- Limitation (authors): Column densities are rough, rely on assumed T_rot, and the emission is unresolved  
  > "These measured fluxes are quite uncertain, but allow us to roughly constrain a disk averaged column density" (3.4 Column Density Analysis); "Although our observations do not resolve any radial or vertical structure" (Summary)
- Limitation (authors): Inner 10 AU model results may be unreliable owing to model resolution and possible C/O depletion  
  > "we caution that interpretation of these regions of the disk may be difficult both due to model resolution" (4.2 Comparison of Chemical Models and Observations)
- Caveat (inferred, ours): The detection rests on a 5.3 sigma stack of two lines with individually marginal (3.4 and 4.2 sigma) significance and flux errors near 100 percent for one line
- Caveat (inferred, ours): The matched-filter kernel is taken from HC3N, which presumes identical morphology and may bias significance
- Caveat (inferred, ours): Column densities depend on an assumed T_rot and an unstated emitting area; HC3N/HC5N ratios span an order of magnitude
- Caveat (inferred, ours): Only a single chemical model family at three C/O values is compared, with no fit
- Caveat (inferred, ours): No independent confirmation (e.g. additional HC5N transitions) is presented

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Self-calibration solution intervals and line-free channels for continuum subtraction
- Missing: Full tclean parameters, cube velocity resolution and primary-beam handling
- Missing: VISIBLE matched-filter details and significance estimation
- Missing: Emitting solid angle and FWHM in the column density equation, and how Table 2 HC3N values were derived
- Missing: Chemical model code and updated binding energies, not released
- Data volume (inferred): Several tens of GB of raw/calibrated data for seven Band 3 execution blocks (7 EBs, 325 min on source, 7 spectral windows)
- Score (inferred): 3/5, ALMA project code and main settings (calibrators, pipeline/CASA versions, beam, rms, GoFish geometry, T_rot range) are given, but self-calibration and imaging parameters, matched-filter implementation and emitting area are not, and the model code is not released.
- Rediscovery candidate: no, Data public status is not stated and key self-calibration, imaging and column-density inputs are missing, so the 5.3 sigma detection and Table 2 values could not be redone exactly from the text alone.

## Links

- Method: (cite: Loomis_2018b) (Matched filter technique and VISIBLE)
- Method: (cite: Teague_2019) (GoFish package)
- Method: (cite: Yen_2016) (Shift and stack analysis)
- Method: (cite: Loomis_2018a) (Optically thin column density formula)
- Method: (cite: Hunter_2023) (ALMA pipeline)
- Method: (cite: Fogel_2011) (Base 2D time-dependent disk chemistry code)
- Companion: (cite: Huang_2018) (TW Hya disk geometry and Keplerian emission range)
- Companion: (cite: Bergner_2018) (HC3N column densities in disks for comparison)
- Companion: (cite: Ilee_2021) (HC3N column densities in disks for comparison)
- Related: ALMA Cycle 6 project 2019.1.00769.S

## Checks

```json
{
 "quotes": 112,
 "quotes_ok": 112,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 106,
  "stated": 71,
  "rate": 0.67
 },
 "evidence_ok": true
}
```
