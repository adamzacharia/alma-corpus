# Spiral Arms, Infall, and Misalignment of the Circumbinary Disk from the Circumstellar Disks in the Protostellar Binary System L1551 NE

`2017ApJ...837...86T` | The Astrophysical Journal 2017 | first author: Takakuwa, Shigehisa | arXiv: 1702.05562 | DOI: 10.3847/1538-4357/aa6116

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: What are the spiral-arm structure, gas kinematics (infall/expansion), and circumstellar disk properties and alignment of the circumbinary disk in the Class I binary L1551 NE at 25 AU resolution?  
  > "However, the Cycle 0 resolution was still too coarse to fully characterize the spiral-arm structures, the gas motions within the spiral-arm and inter-arm regions, and within the circumstellar disks." (Introduction)
- Target **L1551 NE**: coordinates (04h31m44.5s, +18d08m31.67s) J2000 field center  
  > "located in the L1551 region at a distance $d$=140 pc (cite: tak11; tak12; tak13; tak14; tak15)" (Introduction); "Field Center" (Table 1); z/distance 140 pc  
  > "located in the L1551 region at a distance $d$=140 pc (cite: tak11; tak12; tak13; tak14; tak15)" (Introduction); "Field Center" (Table 1); distance from previous work of the group (Takakuwa et al. 2011-2015)  
  > "located in the L1551 region at a distance $d$=140 pc (cite: tak11; tak12; tak13; tak14; tak15)" (Introduction); "Field Center" (Table 1)

## Data provenance

- ALMA projects: 2013.1.00349.S
- bands: Band 7 (0.9 mm)  
  > "Four molecular lines in Band 7, that is, the C$^{18}$O ($J$=3-2; 329.3305453 GHz)" (2.1 ALMA Observations)
- frequencies and spectral setup: 4 spectral windows of 468.75 MHz; C18O 3840 channels of 122.07 kHz, Hanning smoothed to 0.22 km/s; 13CO 0.44, SO 0.86, CS 0.85 km/s  
  > "The resultant velocity resolutions are 0.44 km s$^{-1}$, 0.86 km s$^{-1}$, and 0.85 km s$^{-1}$ for the $^{13}$CO, SO, and the CS lines, respectively." (2.1 ALMA Observations)
- continuum bandwidth: 1.845 GHz centered at 335.85 GHz  
  > "which has a central frequency of 335.85 GHz (= 0.893 mm) and a total bandwidth of 1.845 GHz." (2.1 ALMA Observations)
- arrays: _not stated_
- configurations: C34-7/(6), 36 antennas (35 for SO and CS)  
  > "The C34-7/(6) configuration was adopted, which provides the minimum and maximum baseline lengths of 33.7 m and 1.6 km, respectively." (2.1 ALMA Observations)
- baselines: projected 29 m to 1575 m  
  > "The projected baseline length on the source ranges from 29 m to 1575 m." (2.1 ALMA Observations)
- angular resolution: 0.190x0.169 arcsec natural continuum; 0.134x0.123 uniform; 0.119x0.105 (>=450 m uniform); C18O 0.195x0.168  
  > "0$\ensuremath{''}$190$\times$0$\ensuremath{''}$169 (P.A. = 178.1$\ensuremath{^\circ}$)" (Table 1)
- max recoverable scale: ~50% of peak flux for Gaussian FWHM ~2.8" (~390 AU); ~10% for ~5.2"  
  > "can recover $\sim$50$\%$ of the peak flux for a Gaussian emission distribution with a FWHM of $\sim$2$\ensuremath{''}$8 ($\sim$390 AU)" (2.1 ALMA Observations)
- sensitivity: continuum rms 0.48 mJy/beam; C18O rms 6.59 mJy/beam  
  > "0.48 mJy beam$^{-1}$ = 0.16 K" (Table 1)
- time on source: 34 minutes  
  > "Excluding overheads for calibration, the total time on source was 34 minutes." (2.1 ALMA Observations)
- observing dates: 2015 June 27  
  > "Our ALMA observations of L1551 NE were made on 2015 June 27." (2.1 ALMA Observations)
- pi or archival as stated: _not stated_
- Line: C18O J=3-2 (329.3305453 GHz)
- Line: 13CO J=3-2 (330.587965 GHz)
- Line: SO JN=7_8-6_7 (340.71416 GHz)
- Line: CS J=7-6 (342.882857 GHz)
- Other facility **JVLA 7-mm (Lim et al. 2016b)**: higher-resolution CSD parameters (NUKER fits) for comparison  
  > "Lim et al. (2016b) have made higher-resolution ($\sim$54 mas = 7.6 AU) JVLA 7-mm observations of the CSDs in L1551 NE" (3.1 0.9-mm Dust-Continuum Emission)
- External data: CBD position angle 167 deg and inclination 62 deg and binary mass 0.8 Msun from SMA Keplerian fitting  
  > "the position and inclination angles of the CBD have been estimated to be $\theta$ = 167$\ensuremath{^\circ}^{+23\ensuremath{^\circ}}_{-27\ensuremath{^\circ}}$" (3.1 0.9-mm Dust-Continuum Emission) [from Takakuwa et al. 2012 (cite: tak12)]
- External data: JVLA 7-mm NUKER fit sizes, PA and inclination of CSDs  
  > "From the fitting of the JVLA 7-mm image to the NUKER function by Lim et al. (2016b)." (Table 2) [from Lim et al. (2016b) (cite: lim16b)]
- External data: Bolometric luminosity 4.2 Lsun  
  > "The source bolometric temperature and luminosity are $T_{bol}$ = 91 K and $L_{bol}$ = 4.2 $L_{\odot}$ (cite: fro05)." (Introduction) [from Froebrich 2005 (cite: fro05)]
- External data: C18O abundance 1.7e-7  
  > "$X$(C$^{18}$O)=1.7$\times$10$^{-7}$ (cite: cra04)" (4.2 Infall onto the Protostellar Binary) [from Crapsi et al. 2004 (cite: cra04)]
- Simulation/model as data: SFUMATO AMR hydrodynamic simulation, 73rd orbit snapshot, with LTE radiative transfer and CASA observing simulation, compared with observed images  
  > "Here, we have adopted the simulation result at the 73rd orbital period of the binary, which appears to best resemble the observed 0.9-mm dust-continuum image." (2.2 Numerical Simulations)

## Processing

### Calibration

- pipeline or manual: ALMA observatory pipeline plus manual flagging of one integration  
  > "Calibration of the raw visibility data was performed by the ALMA observatory through the pipeline using the Common Astronomy Software Applications (CASA) version 4.2.2." (2.1 ALMA Observations)
- casa version: CASA 4.2.2  
  > "using the Common Astronomy Software Applications (CASA) version 4.2.2" (2.1 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+180 (~2.4 Jy); passband J0423-0120  
  > "The quasar J0510+180, with estimated flux of $\sim$2.4 Jy, was adopted as the gain and absolute flux calibrators." (2.1 ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: not performed  
  > "We did not perform self-calibration, since the signal-to-noise ratio of the present ALMA data is high." (2.1 ALMA Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Natural for lines and CBD continuum; uniform and uniform with baselines >450 m for CSD continuum  
  > "For the molecular line imaging, Natural weighting of the visibility data was adopted to enhance sensitivity." (2.1 ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum from line-free channels in all four spectral windows  
  > "Channels in all four spectral windows, which are devoid of line emission, were used to create the continuum image" (2.1 ALMA Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.190x0.169 arcsec (natural continuum)  
  > "0$\ensuremath{''}$190$\times$0$\ensuremath{''}$169 (P.A. = 178.1$\ensuremath{^\circ}$)" (Table 1)
- final rms: 0.48 mJy/beam continuum; 6.59 mJy/beam C18O  
  > "6.59 mJy beam$^{-1}$ = 2.27 K" (Table 1)

### Inherited from earlier work

- Simulation model parameters, radiative transfer details, dust opacity and temperature range  
  > "We adopted the same model parameters as those in Takakuwa et al. (2014), except for the orbital time in the simulation" (2.2 Numerical Simulations) [from Takakuwa et al. (2014) (cite: tak14)]
- Dust temperature range 10-42 K and kappa_0.9mm = 0.053 cm2/g  
  > "The same range of the dust temperature as that adopted in Takakuwa et al. (2014), $T_d$ = 10 - 42 K, is adopted" (3.1 0.9-mm Dust-Continuum Emission) [from Takakuwa et al. (2014) (cite: tak14)]
- CBD systemic velocity 6.9 km/s  
  > "have found that the systemic velocity of the CBD is $V_{\rm LSR}$=6.9 km s$^{-1}$ (cite: tak12; tak13; tak14; tak15)" (3.3 C18O (3–2) Emission) [from (cite: tak12; tak13; tak14; tak15)]

### Not stated but needed to reproduce (our reading)

- Pixel size and image size for tclean/clean
- Clean threshold, masks and number of iterations
- Line-free channel ranges for continuum
- Whether primary beam correction was applied
- Details of the Gaussian fitting (task, region)
- Moment map and PV extraction parameters (cuts, widths)
- Simulation code/initial conditions not given here (in Takakuwa 2014)
- How the Keplerian curves for CSDs were chosen (mass, inclination)

## Analysis recipe

1. **Calibrate and image visibilities**: Pipeline-calibrated data, manual flagging, CLEAN with natural weighting for lines and several weightings for continuum  
  > "The calibrated visibility data were then Fourier-transformed and CLEANed to create the continuum and molecular-line images." (2.1 ALMA Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Checked pipeline tables and calibrated data  
  > "We checked the tables of the pipeline calibration as well as the calibrated visibility data." (2.1 ALMA Observations)
2. **Measure CSD sizes, PAs, inclinations, fluxes**: 2D Gaussian fitting to continuum images; i = arccos(Dmin/Dmaj)  
  > "From the 2-dimensional Gaussian fitting, the deconvolved sizes of the CSDs along the major and minor axes" (3.1 0.9-mm Dust-Continuum Emission)
   - fitting: 2D Gaussian; errors statistical only  
  > "The errors in the ALMA fitting results only include the statistical errors of the Gaussian fittings." (3.1 0.9-mm Dust-Continuum Emission)
   - validation: Compared to JVLA 7-mm results  
  > "there is no significant difference in the disk position angles between the ALMA and JVLA results." (3.1 0.9-mm Dust-Continuum Emission)
3. **Estimate CBD orientation**: Subtract CSDs, binarize at 5 sigma, chi2 fit of uniform circular ring  
  > "We then regarded the simplified structure of the CBD as an uniform circular ring, and performed $\chi^2$ model fitting" (3.1 0.9-mm Dust-Continuum Emission)
   - parameter: free parameters: theta, i, ring inner diameter, ring width  
  > "with $\theta$, $i$, the ring inner diameter, and the ring width as the fitting parameters" (3.1 0.9-mm Dust-Continuum Emission)
   - fitting: chi2 minimization  
  > "We then regarded the simplified structure of the CBD as an uniform circular ring, and performed $\chi^2$ model fitting with $\theta$, $i$, the ring inner diameter, and the ring width as the fitting parameters." (3.1 0.9-mm Dust-Continuum Emission)
   - validation: Consistent with the SMA values  
  > "consistent with our canonical values adopted in our numerical simulation" (3.1 0.9-mm Dust-Continuum Emission)
4. **Derive disk masses**: M = S d^2/(kappa B(Td)) with Td=10-42 K  
  > "The masses of the CSDs and CBD ($\equiv M_{d}$) are estimated from their individual continuum fluxes" (3.1 0.9-mm Dust-Continuum Emission)
   - assumption: gas-to-dust 100, kappa0.9mm=0.053 cm2/g (kappa250um=0.1, beta=0.5), d=140 pc  
  > "on the assumption of a gas-to-dust mass ratio of 100" (3.1 0.9-mm Dust-Continuum Emission)
   - fitting: _not stated_
   - validation: Agree with Cycle 0 masses  
  > "These mass estimates are in close agreement with those from our previous Cycle 0 observation (cite: tak14)." (3.1 0.9-mm Dust-Continuum Emission)
5. **Analyze C18O kinematics**: Channel maps, PV diagrams along CSD and CBD axes compared with Keplerian and free-fall curves  
  > "Red curves in the upper and lower panels of Figure [7](#fig:pvA) shows the inferred Keplerian rotation curves" (3.3.1 CSDs)
   - assumption: binary mass 0.8 Msun, i=62 deg, Source A 0.675 Msun  
  > "the spatial-velocity distribution is consistent with the Keplerian rotation curve on the assumption of the central stellar mass of 0.8 $M_{\odot}$ and the disk inclination angle of 62$\ensuremath{^\circ}$." (3.3.2 CBD)
   - fitting: _not stated_
   - validation: Velocity differences below resolution 0.22 km/s  
  > "The differences of the velocities are less than the observational velocity resolution ($\sim$0.22 km s$^{-1}$)." (3.3.1 CSDs)
6. **Infall mass, rate and accretion luminosity**: LTE C18O mass of infalling gas; Mdot = M_r v_r / r; L_acc = G M Mdot / R_in  
  > "$$\begin{equation} \dot{M}=\frac{M_r v_r}{r}, \end{equation}$$" (4.2 Infall onto the Protostellar Binary)
   - assumption: Tex=42 K, X(C18O)=1.7e-7, LTE, R_in = 4 Rsun  
  > "on the assumption of the excitation temperature of the C$^{18}$O emission of 42 K (cite: bar93; mor94)" (4.2 Infall onto the Protostellar Binary)
   - fitting: _not stated_
   - validation: L_acc compared with L_bol  
  > "the accretion luminosity is $\sim$5.4 $L_{\odot}$, similar to the bolometric luminosity of L1551 NE (= 4.2 $L_{\odot}$; Froebrich 2005)." (4.2 Infall onto the Protostellar Binary)
7. **Compare with hydrodynamic simulation**: SFUMATO simulation, LTE radiative transfer, CASA observing simulation, same imaging  
  > "We then made simulated theoretical images with the same imaging methods as those of the real data." (2.2 Numerical Simulations)
   - software: SFUMATO, CASA
   - fitting: parameters fixed from Cycle 0 fine tuning  
  > "These parameters were originally derived from our fine tuning to match the outputs from the radiative transfer calculations and the observing simulation with the real observed Cycle 0 images." (2.2 Numerical Simulations)
   - validation: Reproduces arms, m=1 mode and expansion  
  > "Our simulation reproduces the observed curling features of Arms A and B, connection of Arm B to the CSD around Source B, and the brightness distribution skewed to the west." (3.1 0.9-mm Dust-Continuum Emission)

## Software

- **CASA** 4.2.2: calibration, imaging, observing simulations  
  > "using the Common Astronomy Software Applications (CASA) version 4.2.2" (2.1 ALMA Observations)
- **SFUMATO** : AMR hydrodynamic simulation  
  > "adaptive mesh refinement (AMR) code SFUMATO (cite: mat07)" (2.2 Numerical Simulations)
- **Miriad** : listed in Software section, use not described  
  > "CASA, Miriad" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Source A CSD deconvolved size | 0.29 x 0.19 arcsec (40 x 26 AU), PA 144 deg | PA +-3 deg | arcsec / AU / deg | 2 | 0$\ensuremath{''}$29 $\times$ 0$\ensuremath{''}$19 (= 40 $\times$ 26 AU) (P.A. = 144$\ensuremath{^\circ}$) |
| Source B CSD deconvolved size | 0.26 x 0.20 arcsec (36 x 27 AU), PA 147 deg | PA +-11 deg | arcsec / AU / deg | 2 | 0$\ensuremath{''}$26 $\times$ 0$\ensuremath{''}$20 (= 36 $\times$ 27 AU) (P.A. = 147$\ensuremath{^\circ}$) |
| CSD inclinations A, B | 50 and 41 | +2/-3 and +8/-11 | deg | 2 | are calculated to be 50$\ensuremath{^\circ}$ for Source A and 41$\ensuremath{^\circ}$ for Source B |
| CBD PA and inclination | 160 and 62 | +12/-14 and +9/-8 | deg | 3 | The estimated position and inclination angles are $\theta$ = 160$\ensuremath{^\circ}^{+12\ensuremath{^\circ}}_{-14\ensuremath{^\circ}}$ and $i$ = 62$\ensuremath{^\circ}^{+9\ensuremath{^\circ}}_{-8\ensuremath{^\circ}}$ |
| Masses of CSD A, CSD B, CBD | 0.005-0.043, 0.002-0.016, 0.009-0.076 | range for Td=10-42 K | Msun | 4 | a mass for the CSD of Source A is calculated to be $\sim$0.005 - 0.043 $M_{\odot}$, that of Source B $\sim$0.002 - 0.016 $M_{\odot}$ |
| Infalling gas mass | 8.1e-5 | not stated | Msun | 6 | The mass of the infalling component is estimated to be $M_r$ $\sim$8.1$\times$10$^{-5}$ $M_{\odot}$. |
| Mass infall rate | 1.0e-6 | not stated (lower limit) | Msun/yr | 6 | the value is $\dot{M} \sim$1.0$\times$10$^{-6}$ $M_{\odot}~yr^{-1}$ |
| Accretion luminosity | 5.4 | not stated | Lsun | 6 | the accretion luminosity is $\sim$5.4 $L_{\odot}$ |

## Qualitative findings

- CBD comprises northern and southern spiral arms with western side brighter (m=1 mode)  
  > "The western parts of the spiral arms are brighter than the eastern parts, suggesting the presence of an $m=1$ spiral mode." (abstract)
- SO emission concentrated near Source A, possible accretion shocks  
  > "the SO (7$_8$–6$_7$) emission is concentrated around Source A" (4.3 Misalignments of the CSDs from the CBD in L1551 NE)

## Claim tuples

- H: Does the CBD show spiral arms with infall in inter-arm and expansion in arms driven by binary torques? | E: ALMA Cycle 2 continuum and C18O PV analysis compared with SFUMATO simulations | R: Two arms, east-west velocity gradients indicating infall near Source A and opposite gradients across arms | F: Gravitational torques explain arm expansion and inter-arm infall | **supported**
- H: Are the CSDs misaligned with the CBD? | E: Compare PA and inclination of CSDs with ring fit CBD | R: CSD A PA 144 vs CBD 160, inclinations differ | F: CSDs are misaligned and not co-planar with the CBD | **supported**
- H: Does C18O trace Keplerian rotation of the Source A CSD? | E: PV diagram along CSD major axis vs Keplerian curve for 0.675 Msun | R: Velocities match within 0.22 km/s | F: Keplerian rotation of misaligned disk around Source A | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: C18O used for kinematics since it best traces the CBD and has the best velocity resolution  
  > "Since the C$^{18}$O emission appears to trace the CBD structure as seen in the 0.9-mm dust-continuum emission most straightforwardly" (3.2 Distributions of the Molecular-Line Emission in L1551 NE)
- Alternative: Blueshifted emission near Source B rejected as Keplerian CSD rotation; possibly gas flowing into Roche lobe  
  > "this high-velocity blueshifted emission may trace a gas component flowing into the Roche lobe." (3.3.1 CSDs)
- How they decided it was enough: _not stated_
- Limitation (authors): Mass infall rate is only a lower limit; infall perpendicular to line of sight is not measurable  
  > "the mass infalling rate estimated above should be regarded as the lower limit of the entire infall toward Source A" (4.2 Infall onto the Protostellar Binary)
- Limitation (authors): Model cannot reproduce infall near Source A due to opacity masks  
  > "Therefore, the observed infalling components in the vicinity of Source A cannot be reproduced with our model." (4.1 Kinematics of the CBD)
- Caveat (inferred, ours): Misalignment significance relies on a crude binarized ring fit with statistical errors only
- Caveat (inferred, ours): Simulation assumes CSDs coplanar with CBD and has no fine-tuning to Cycle 2
- Caveat (inferred, ours): Infall mass uses assumed Tex 42 K and LTE
- Caveat (inferred, ours): Single-epoch short observation; missing flux affects Source B >450 m

## Reproducibility

- Data public (paper): ALMA data identified with project 2013.1.00349.S via acknowledgment  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00349.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Simulation initial conditions and code (in Takakuwa 2014)
- Missing: Cleaning parameters
- Missing: Exact fitting regions
- Data volume (inferred): ~10-30 GB raw single-execution Band 7 dataset
- Score (inferred): 3/5, Observational parts are reproducible from public data with standard steps, but imaging parameters are unstated and simulations rely on prior work.
- Rediscovery candidate: no, Imaging parameters and fitting details are incomplete and the simulation comparison depends on unreleased code.

## Links

- Method: Takakuwa et al. 2014 (cite: tak14) (Simulation, radiative transfer and Cycle 0 analysis)
- Companion: Lim et al. 2016b (cite: lim16b) (JVLA 7-mm CSD observations)
- Companion: Takakuwa et al. 2012 (cite: tak12) (SMA CBD Keplerian model)
- Related: ALMA Cycle 0 observations of L1551 NE

## Checks

```json
{
 "quotes": 82,
 "quotes_ok": 82,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 85,
  "stated": 62,
  "rate": 0.729
 },
 "evidence_ok": true
}
```
