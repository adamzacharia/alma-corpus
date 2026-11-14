# Unveiling Stellar Feedback and Cloud Structure in the ρ Ophiuchi-A Region Using ALMA and JWST: Discovery of Substellar Cores, C<SUP>18</SUP>O Striations, and Protostellar Outflows

`2025ApJ...994..225N` | The Astrophysical Journal 2025 | first author: Nakamura, Fumitaka | arXiv: 2509.01122 | DOI: 10.3847/1538-4357/adfddd

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: How do stellar feedback (S1 HII/PDR bubble, protostellar outflows) shape the cloud structure of Oph A, and what faint substellar cores exist, using ALMA 1.3 mm continuum and CO lines plus JWST F470N  
  > "In this paper, through a comparison of ALMA and JWST images of the Oph A region, we aim to uncover the detailed cloud structures of Oph A, with a particular focus on stellar feedback." (Introduction)
- Target **Oph A (rho Ophiuchi A)**: coordinates 16h27m26.507s, -24d31m28.63s (mosaic reference position)  
  > "located at a distance of 138 pc (cite: lombardi08; ortiz17a; zucker20)" (Introduction); "The reference position for both arrays was set to ($\alpha_{J2000.0}$, $\delta_{J2000.0}$) = (16$^h$27$^m$26$''$.507, –24$^\circ$31$'$28$''$.63)" (2.1 ALMA Observations); z/distance 138 pc  
  > "located at a distance of 138 pc (cite: lombardi08; ortiz17a; zucker20)" (Introduction); "The reference position for both arrays was set to ($\alpha_{J2000.0}$, $\delta_{J2000.0}$) = (16$^h$27$^m$26$''$.507, –24$^\circ$31$'$28$''$.63)" (2.1 ALMA Observations); distance from Lombardi08; Ortiz-Leon17; Zucker20  
  > "located at a distance of 138 pc (cite: lombardi08; ortiz17a; zucker20)" (Introduction); "The reference position for both arrays was set to ($\alpha_{J2000.0}$, $\delta_{J2000.0}$) = (16$^h$27$^m$26$''$.507, –24$^\circ$31$'$28$''$.63)" (2.1 ALMA Observations)

## Data provenance

- ALMA projects: 2013.1.00839.S
- bands: Band 6 (1.3 mm)  
  > "using the ALMA 12-m Array and the 7-m Array (ACA) in Band 6 during Cycle 2" (2.1 ALMA Observations)
- frequencies and spectral setup: Two continuum basebands (2000 MHz each, 128 channels, ~7.4 GHz effective); two line basebands (117.2 MHz, 3840 channels) for 12CO, 13CO, C18O J=2-1  
  > "The remaining two basebands were used for molecular line observations ($^{12}$CO J=2–1, $^{13}$CO J=2–1, C$^{18}$O J=2–1) in dual-polarization mode, with a correlator bandwidth of 117.2 MHz and 3840 channels." (2.1 ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m Array and 7-m Array (ACA), mosaic of 150 and 53 pointings  
  > "We used 150 pointings for the 12 m Array and 53 pointings for the 7 m Array, with spacings of 13.6$''$ and 23.2$''$, respectively." (2.1 ALMA Observations)
- configurations: _not stated_
- baselines: 12-m: 12.5–348 kλ; 7-m: 8.1–48 kλ  
  > "The uv ranges sampled by the 12-m Array and 7-m Array data were 12.5 – 348 $k \lambda$ and 8.1 – 48 $k \lambda$, respectively." (2.1 ALMA Observations)
- angular resolution: ~1.4" x 0.9"  
  > "The final images have a beam size of approximately 1.4$''$$\times$0.9$''$." (2.1 ALMA Observations)
- max recoverable scale: 25 arcsec (combined data)  
  > "The minimum uv distance of the combined data corresponds to a maximum spatial scale of 25$''$." (2.1 ALMA Observations)
- sensitivity: continuum 0.25 mJy/beam; 12CO 42, 13CO 55, C18O 36 mJy/beam (0.2 km/s channels)  
  > "noise level$^a$ | 0.25 mJy beam$^{-1}$ | 42 mJy beam$^{-1}$ | 55 mJy beam$^{-1}$ | 36 mJy beam$^{-1}$" (Table 2)
- time on source: 12-m 33 min; 7-m 50 min  
  > "On-Source Time           |     33 min      |     50 min      |" (Table 1)
- observing dates: 12-m: 2015 May 1; 7-m: 2014 Aug 14–17  
  > "Observation date         |   2015 May 1    | 2014 Aug. 14–17 |" (Table 1)
- pi or archival as stated: Own Cycle 2 program, PI F. Nakamura  
  > "(PI: F. Nakamura, Project code 2013.1.00839.S)" (2.1 ALMA Observations)
- Line: 12CO J=2-1 (230.538000 GHz)
- Line: 13CO J=2-1 (220.398684 GHz)
- Line: C18O J=2-1 (219.560358 GHz)
- Other facility **JWST NIRCam**: F470N image (H2 S(9) 4.69 um) and other filters, program 2739  
  > "as part of the mission’s first anniversary imaging campaign (Program ID: 2739, PI: K. Pontoppidan)" (2.2 JWST Observations)
- Other facility **Spitzer**: 4.5 um IRAC detections of compact sources  
  > "ALMA OphA 3 exhibits compact infrared emission detected in *Spitzer IRAC* at 4.5 $\mu$m and JWST at 4.7 $\mu$m." (4.1.2 Substellar Objects)
- External data: Dust opacity kappa_230GHz = 0.00529 cm2/g with beta=2  
  > "the opacity $\kappa_{230 \rm GHz} = 0.00529$ cm$^2$ g$^{-1}$ with $\beta=2$ (cite: hildebrand83)" (4.1.1 Pre-substellar cores) [from (cite: hildebrand83)]
- External data: Model 4.4 um magnitudes of 1-10 MJup objects at 1 Myr (Figure 3)  
  > "has a observed magnitude ($m_{\rm obs}$) of about 13.7 mag at $4.4 \ \mu$m from Figure 3 of (cite: defurio25)" (3.1 1.3 mm dust continuum image) [from (cite: defurio25)]
- External data: Magnetic field orientation and strength 0.2–30 mG from 154 um polarimetry  
  > "According to 154 $\mu$m continuum polarimetry (cite: tram24), the magnetic field orientation between S1 and the Oph A ridge is predominantly in the east-west direction" (4.2.2 C18O Striations) [from (cite: tram24)]
- External data: S1 systemic velocity –2.2 km/s  
  > "The systemic velocity of S1 is measured to be –2.2 km s$^{-1}$ (cite: gutirrez20)" (4.2.1 Outflow of warm gas) [from (cite: gutirrez20)]

## Processing

### Calibration

- pipeline or manual: Calibration run by authors with ALMA observatory scripts; 7-m bandpass shadowing criterion reduced from 7 m to 6 m  
  > "The calibration was carried out ourselves using scripts prepared by the ALMA observatory." (2.1 ALMA Observations); "the shadowing criterion for the bandpass data was reduced from 7 m to 6 m to recover some data previously flagged by the original scripts" (2.1 ALMA Observations)
- casa version: CASA 4.2.2 (calibration), 4.5.3 (imaging)  
  > "We used the Common Astronomy Software Applications package, CASA pipeline version 4.2.2 and version 4.5.3, for calibration and imaging, respectively" (2.1 ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (12-m), Mars (7-m); Butler-JPL-Horizons 2012 model  
  > "We used the Butler-JPL-Horizons 2012 model with the absolute flux scale of Titan and Mars." (2.1 ALMA Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean mosaic; statwt for weights, concat to combine 12-m and 7-m  
  > "The CASA task *statwt* was used to determine weights of the visibility data and the 12-m Array and 7-m Array data were combined using the CASA task *concat*." (2.1 ALMA Observations)
- deconvolver: multiscale clean  
  > "The multiscale clean (cite: cornwell08) option of *tclean* for the mosaic imaging of our multifield observations was applied." (2.1 ALMA Observations)
- weighting robust: natural weighting  
  > "We adopted natural weighting." (2.1 ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: images also smoothed to 2" x 2" with imsmooth  
  > "we created images smoothed to a 2$\ensuremath{''} \times 2\ensuremath{''}$ resolution using the *imsmooth* task in CASA" (2.1 ALMA Observations)
- final beam: 1.41"x0.90" (continuum), 1.48"x0.95" (C18O)  
  > "beam size | 1.41$''$$\times$ 0.90$''$ | 1.41$''$$\times$ 0.91$''$ | 1.47$''$$\times$ 0.94$''$ | 1.48$''$$\times$ 0.95$''$" (Table 2)
- final rms: 0.25 mJy/beam continuum  
  > "noise level$^a$ | 0.25 mJy beam$^{-1}$" (Table 2)

### Inherited from earlier work

- Observation parameters nearly identical to the Oph B2 observations; calibration script modification as with Oph B2  
  > "The observation parameters, summarized in Tables [1](#tab:obs) and [\[tab:obs2\]](#tab:obs2), are nearly identical to those of the Oph B2 observations reported by (cite: kamazaki19)." (2.1 ALMA Observations) [from (cite: kamazaki19)]
- JWST observational setup and data processing largely follow the first-anniversary campaign methodology  
  > "The observational setup and data processing were largely based on the methodology described in (cite: pontoppidan22)" (2.2 JWST Observations) [from (cite: pontoppidan22)]
- VLA 1623 outflow analysis deferred to earlier paper  
  > "as discussed in detail by (cite: hara21). Their analysis provides insights into the density and velocity structures of this outflow." (4.2.3 Protostellar Outflows) [from (cite: hara21)]

### Not stated but needed to reproduce (our reading)

- tclean cell size, image size, multiscale scales, mask and threshold
- Line-free channels / continuum selection and continuum subtraction
- Primary beam correction treatment
- Flux density measurement method (fitting/aperture) for the faint cores and core radii definition
- Details of JWST Stage 3 products and F470N continuum/PDR subtraction
- Details of position-velocity cut positions and striation measurement
- Details of astrodendro usage if used

## Analysis recipe

1. **Calibrate and image ALMA 7m+12m data**: CASA calibration scripts, statwt, concat, multiscale tclean mosaic with natural weighting  
  > "The multiscale clean (cite: cornwell08) option of *tclean* for the mosaic imaging of our multifield observations was applied." (2.1 ALMA Observations)
   - software: CASA
   - parameter: natural weighting; beam ~1.4"x0.9"  
  > "We adopted natural weighting." (2.1 ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify faint compact cores in the continuum**: Visual inspection of ALMA continuum and JWST images; criteria peak >8 sigma and more than two closed contours starting at 3 sigma with 1.5 sigma intervals  
  > "(1) The source must exhibit a peak intensity exceeding 8$\sigma$, and (2) It must show more than two closed contours when the dust continuum map is contoured starting at 3$\sigma$ with 1.5$\sigma$ intervals." (4.1 Discovery of Substellar Cores)
   - fitting: _not stated_
   - validation: Cross-check with JWST 4.7 um compact emission to classify protostellar/substellar vs pre-substellar  
  > "cores with 4.7 $\mu$m JWST emission are referred to as protostellar, proto-substellar, or young substellar objects, while those without infrared counterparts are considered prestellar or pre-substellar cores." (4.1 Discovery of Substellar Cores)
3. **Derive core masses and boundedness**: Optically thin dust mass formula with Planck function; Bonnor-Ebert mass ratio alpha_BE = Mc/MBE  
  > "To assess the gravitational boundedness of the four observed cores without associated infrared emission, we calculate the Bonnor-Ebert mass ratio" (4.1.1 Pre-substellar cores)
   - assumption: Td = 20 K, kappa230GHz = 0.00529 cm2/g (beta=2), gas-to-dust 100, D = 138 pc, tau<1  
  > "$T_d$ is the dust temperature assumed to be 20 K, the opacity $\kappa_{230 \rm GHz} = 0.00529$ cm$^2$ g$^{-1}$ with $\beta=2$ (cite: hildebrand83), and the gas-to-dust ratio is set to 100." (4.1.1 Pre-substellar cores)
   - fitting: _not stated_
   - validation: Temperature sensitivity: 10–30 K changes mass by factor 3.64 to 0.61  
  > "if the temperature varies between 10 K and 30 K, the mass estimate can change by a factor of 3.64 to 0.61." (4.1.1 Pre-substellar cores)
4. **Map CO outflows, S1 bubble gas and C18O striations**: 12CO and C18O integrated intensity maps, channel maps, averaged line profiles, position-velocity diagrams; compare with JWST F470N to identify jet driving sources  
  > "In Figure [6](#fig:12COpeak), we show the $^{12}$CO and C$^{18}$O integrated intensity maps." (4.2.1 Outflow of warm gas)
   - software: Astropy, APLpy, Matplotlib
   - assumption: Sound speed 0.3–0.5 km/s; B = 0.2 mG lower limit, T = 20 K, n = 1e4 cm-3 for plasma beta  
  > "assuming a magnetic field strength of 0.2 mG (its lower limit), a temperature of 20 K, and a density of $10^4$ cm$^{-3}$" (4.2.2 C18O Striations)
   - fitting: _not stated_
   - validation: Caveat that 12CO is affected by self-absorption and resolved-out emission so peak T is a lower limit  
  > "the observed peak temperature should be considered to be a lower limit of the actual gas kinetic temperature." (4.2.1 Outflow of warm gas)

## Software

- **CASA** 4.2.2 (calibration), 4.5.3 (imaging): calibration, statwt, concat, tclean, imsmooth  
  > "CASA pipeline version 4.2.2 and version 4.5.3, for calibration and imaging, respectively" (2.1 ALMA Observations)
- **reproject** : coadding JWST images  
  > "The images are visually inspected to mask artifacts and then coadded using the `reproject` package" (2.2 JWST Observations)
- **Astrodendro** : named in software list; use not described  
  > "Matplotlib (Hunter 2007) and Astrodendro (cite: rosolowsky08)." (Software)
- **Astropy, SciPy, Numpy, APLpy, Matplotlib** : data analysis and plotting  
  > "The data analysis in this paper uses python packages Astropy" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of new substellar cores | 7 (ALMA OphA 3/4/5 and PSS OphA 1/2/3/4) | not stated | dimensionless | 2 | we have identified 7 faint objects in this study (ALMA OphA 3/4/5 and PSS OphA 1/2/3/4) |
| 1.3 mm flux densities of PSS cores | 3 to 13 mJy; masses 0.01–0.035 | temperature factor 3.64 to 0.61 for 10-30 K | mJy; Msun | 3 | The 1.3 mm flux densities of these cores range from 3 mJy to 13 mJy, corresponding to estimated masses of 0.01–0.035 M$_\odot$. |
| ALMA OphA 3 envelope mass | 3.53e-3 | not stated | Msun | 3 | The envelope mass, derived from the 1.3 mm continuum emission, is estimated to be $3.53 \times 10^{-3}$ M$_\odot$. |
| Bonnor-Ebert ratio of PSS cores | alpha_BE ~ 1 (range 0.17–3.5) | not stated | dimensionless | 3 | all four cores without associated infrared emission have Bonnor-Ebert ratios close to unity ($\alpha_{\rm BE} \approx 1$) |
| Plasma beta of C18O striations | 8.9e-3 | not stated | dimensionless | 4 | \beta \equiv \frac{4\pi c_s^2 \rho}{B^2} \simeq 8.9 \times 10^{-3} |
| Striation separation | 20–25 arcsec (3000–3500 au) | not stated | arcsec | 4 | separations of approximately 20–25$''$ , ($\approx 3000-3500$ au |
| Maximum 12CO peak brightness (PDR shell) | 4.95 Jy/beam (89.6 K) | not stated | Jy/beam | 4 | brightness temperature ($T_{\rm mb}$) of 4.95 Jy/beam (= 89.6 K |
| Mach number of S1 outflowing gas | 6–10 | not stated | dimensionless | 4 | the estimated Mach number of the outflow reaches 6–10 |

## Qualitative findings

- Several new outflows/jets identified from combining 12CO and F470N, including VLA 1623W, [GY92]21, [GY92]23 and a bipolar jet from [GY92]20  
  > "we not only confirmed previously known outflows but also identified new faint outflow candidates and their potential driving sources such as VLA 1623W, \[GY92\]21, and \[GY92\]23." (4.2.3 Protostellar Outflows)

## Claim tuples

- H: Faint compact substellar cores exist in Oph A | E: Visual identification in 1.3 mm continuum with 8 sigma criterion, JWST cross-match | R: 7 new cores, 3 with JWST counterparts | F: Four are pre-substellar candidates, three are young substellar objects | **supported**
- H: Cores near VLA 1623 may have been ejected | E: Morphology of faint CO finger-like structures | R: Weak CO fingers connect cores to VLA 1623 | F: Ejection suggested but uncertain | **partially**
- H: S1 bubble shapes Oph A and feeds warm gas toward GSS 30 | E: 12CO maps and JWST comparison | R: Strong 12CO along eastern ridge edge; northern ridge blown out | F: Stellar feedback significantly influences cloud structure | **supported**
- H: C18O striations are magnetically controlled | E: Compare striation orientation with literature B field; PV diagrams | R: Striations align with B; plasma beta ~9e-3; wave-like PV patterns | F: Possibly MHD waves | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Visual core identification chosen because spatial filtering biases automated source finders  
  > "can bias automated source-finding algorithms, especially in regions with complex and spatially varying background emission." (4.1 Discovery of Substellar Cores)
- Alternative: Two core formation scenarios considered: turbulent fragmentation vs ejection from VLA 1623  
  > "Two primary formation scenarios are possible for these compact cores: turbulent fragmentation and ejection from a nearby stellar system like VLA 1623A/B." (4.1.1 Pre-substellar cores)
- How they decided it was enough: _not stated_
- Limitation (authors): Missing flux from interferometric filtering hinders prestellar core detection  
  > "Most prestellar cores have either very weak or undetectable emission, likely due to interferometric spatial filtering." (3.1 1.3 mm dust continuum image)
- Limitation (authors): Ejected cores may not survive; CO structures affected by missing flux  
  > "The actual structures may be affected by the interferometric missing flux." (4.1.1 Pre-substellar cores)
- Caveat (inferred, ours): Core identification is visual and not reproducible by algorithm
- Caveat (inferred, ours): Mass depends strongly on assumed 20 K temperature and opacity
- Caveat (inferred, ours): Bound-ness from Bonnor-Ebert with assumed T and no kinematics
- Caveat (inferred, ours): Wave interpretation of striations is qualitative
- Caveat (inferred, ours): Proper motion check deferred to in-prep paper

## Reproducibility

- Data public (paper): ALMA project 2013.1.00839.S acknowledged; JWST data from MAST publicly released  
  > "We retrieved the stage 3 imaging data products from the Mikulski Archive for Space Telescopes (MAST), which was publicly released on July 12, 2023." (2.2 JWST Observations)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, scales, thresholds, masks)
- Missing: Flux measurement method and core sizes
- Missing: Line-free channel and cut positions for PV
- Data volume (inferred): ~50-200 GB for the 12m+7m mosaic raw ALMA data
- Score (inferred): 3/5, Data public and basic processing stated, but imaging parameters and visual identification are underspecified.
- Rediscovery candidate: no, Core identification is visual and imaging parameters are missing.

## Links

- Method: (cite: kamazaki19) (Same observing setup and data reduction for Oph B2)
- Method: (cite: pontoppidan22) (JWST observation and processing methodology)
- Companion: (cite: hara21) (ALMA VLA 1623 outflow from the same data)
- Companion: (cite: kawabe18) (Earlier presentation of part of the Oph A data)
- Companion: (cite: yamagishi19) (Earlier presentation of part of the Oph A data)
- Related: JWST first anniversary imaging program 2739
- Related: Spitzer c2d

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
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
  "facts": 75,
  "stated": 52,
  "rate": 0.693
 },
 "evidence_ok": true
}
```
