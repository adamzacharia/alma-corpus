# Fire in the Heart: A Characterization of the High Kinetic Temperatures and Heating Sources in the Nucleus of NGC 253

`2019ApJ...871..170M` | The Astrophysical Journal 2019 | first author: Mangum, Jeffrey G. | arXiv: 1812.09219 | DOI: 10.3847/1538-4357/aafa15

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, astrochemistry
- Question: What is the kinetic temperature of the dense star-forming gas in the NGC 253 nucleus, and what heating processes (cosmic rays, mechanical, PDR/XDR) drive it?  
  > "Specifically, what is the kinetic temperature within the dense gas that is in the process of forming stars, and what are the heating processes that drive those kinetic temperatures?" (Introduction)
- Target **NGC 253**: coordinates RA(J2000)=00:47:33.1339, Dec(J2000)=-25:17:19.68  
  > "The phase center was at RA(J2000)=00:47:33.1339, Dec(J2000)=$-25$:17:19.68, V$_{hel}$=258.8 km/s." (2 Observations); "$1^{\prime\prime} \simeq 17$ pc" (abstract); z/distance D = 3.5 Mpc; V_hel = 258.8 km/s  
  > "The phase center was at RA(J2000)=00:47:33.1339, Dec(J2000)=$-25$:17:19.68, V$_{hel}$=258.8 km/s." (2 Observations); "$1^{\prime\prime} \simeq 17$ pc" (abstract); distance from 3.5 Mpc adopted in table notes; Rekola2005 cited for proximity  
  > "The phase center was at RA(J2000)=00:47:33.1339, Dec(J2000)=$-25$:17:19.68, V$_{hel}$=258.8 km/s." (2 Observations); "$1^{\prime\prime} \simeq 17$ pc" (abstract)

## Data provenance

- ALMA projects: 2013.1.00099.S, 2015.1.00476.S
- bands: Band 6 and Band 7  
  > "Total Power (TP) antennas at Bands 6 and 7" (2 Observations)
- frequencies and spectral setup: 3 spectral windows per band; B6 217.3-219.2, 219.0-220.8, 233.7-235.7 GHz; B7 350.8-352.7, 362.5-364.4, 363.9-365.8 GHz  
  > "Three separate spectral windows for each frequency band in these 12m Array and ACA measurements were employed." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 12m Array and ACA (TP unusable, not used)  
  > "The TP measurements have proven to be unusable owing to incomplete telluric line removal" (2 Observations)
- configurations: _not stated_
- baselines: 12m: 15-349 m (B6), 21-650 m (B7); ACA: 9-49 m  
  > "| 7 | 12m | 2014-05-19 09:15:59 | 34.3 | 34 | (21,650) |" (Table 1)
- angular resolution: 1.5"-0.4" (12m Array: ~1.5x0.9" Band 6, ~0.45x0.29" Band 7)  
  > "imaged at $1.^{\prime\prime}$5–$0.^{\prime\prime}$4 resolution" (abstract)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Band 6: 44.9 min (12m), 72.6 min (ACA); Band 7: 34.3 min (12m), 65.6 min (ACA)  
  > "At Band 7 the total on-source integration time toward NGC 253 for each type of measurement was 34.3 min (12m Array) and 65.6 minutes (ACA)," (2 Observations)
- observing dates: 2014-05-19 to 2015-05-02  
  > "| 6 | 12m | 2015-05-02 16:18:28 | 38.1 | 34 | (15,349) |" (Table 1)
- pi or archival as stated: _not stated_
- Line: H2CO 3_03-2_02 (218.222192 GHz)
- Line: H2CO 5_15-4_14 (351.768645 GHz)
- Line: C18O 2-1 (219.560358 GHz)
- Line: HNC 4-3 (362.630 GHz)
- Other facility **Br gamma / [FeII] imaging (Rosenberg2013)**: Near-IR tracers of young massive stars and shocks compared to ALMA continuum  
  > "(cite: Rosenberg2013) imaged the Br$\gamma$, H$_2$, and \[FeII\] emission toward NGC 253" (7.1 Radio, Near-Infrared, and X-Ray Diagnostics of Dense Gas Heating)
- Other facility **Radio continuum (Ulvestad1997)**: 2 cm compact source positions and spectral indices  
  > "we note that (cite: Ulvestad1997) calculated spectral indices for all of the radio sources they detected." (7.1 Radio, Near-Infrared, and X-Ray Diagnostics of Dense Gas Heating)
- External data: Dust temperature Td = 35 K and GMC component numbering  
  > "Assuming then that $R_{gd} = 150$, $\beta = 1.5$, and $T_d = 35$ K (cite: Leroy2015)" (3.3 Spatial Component Hydrogen Column Density and Mass) [from (cite: Leroy2015)]
- External data: H2CO LVG model grid and temperature-sensitive ratio limits  
  > "The detailed properties of our implementation of the LVG approximation are described in (cite: Mangum1993)." (5 Kinetic Temperature Derivation Using Formaldehyde) [from (cite: Mangum1993)]
- External data: Assumed log N(H2CO)/dv = 12.5 and log n(H2) = 5.0  
  > "$\log(n(H_2)) = 5.0$ (cite: Mangum2013)" (5 Kinetic Temperature Derivation Using Formaldehyde) [from (cite: Mangum2013)]
- External data: Chemical PDR/CR/mechanical heating model abundance predictions  
  > "The adapted chemical PDR models of (cite: Meijerink2011) and (cite: Bayet2011) are of this type" (7.2 Chemical Diagnostics of Dense Gas Heating) [from (cite: Meijerink2011; Bayet2011)]
- External data: Radio spectral indices and 2 cm source positions  
  > "To identify possible sources of CRs, we note that (cite: Ulvestad1997) calculated spectral indices for all of the radio sources they detected." (7.2 Chemical Diagnostics of Dense Gas Heating) [from (cite: Ulvestad1997)]
- Simulation/model as data: LVG models (RADEX, van der Tak 2007) of CH3OH over n=1e4-1e7, N=1e13-1e16, TK=50-300 K, FWHM 50 km/s  
  > "we have run LVG models (cite: vanderTak2007) over representative ranges in n(H$_2$), N(CH$_3$OH), and T$_K$:" (8 Vibrationally Excited Molecules and Possible Non-LTE Methanol Emission)

## Processing

### Calibration

- pipeline or manual: Manual or pipeline calibrated by NA ARC staff using CASA  
  > "All measurements were either manually or pipeline calibrated by ALMA North American Regional Center staff using the CASA reduction package." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: B6: Uranus, Mars, Neptune; B7: J2258-2758, Neptune, Uranus  
  > "At Band 7 flux calibration was effected using J2258$-$2758 (390 mJy), Neptune (25.8–27.8 Jy), and Uranus (63.8–66.6 Jy)." (2 Observations)
- flux scale uncertainty: 5% Uranus, 10% Mars, 10% Neptune, 15% J2258-2758; overall 10% (B6), 15% (B7)  
  > "The ALMA Calibration Catalog lists the flux uncertainty for this quasar as 15%" (2 Observations); "absolute amplitude calibration uncertainties of 10% and 15% at Bands 6 and 7, respectively" (7.2 Chemical Diagnostics of Dense Gas Heating)
- self calibration: One iteration of phase-only self-cal, 60 s averaging, on NGC 253 continuum  
  > "For all measurement groups at both Bands 6 and 7 one iteration of phase-only self-calibration utilizing a 60 second averaging time was used." (2 Observations)

### Imaging

- task: CASA clean per spectral window; feather to combine 12m and ACA  
  > "Images of each self-calibrated spectral window image cube for NGC 253 were created using the `clean` task within CASA." (3.1 Imaging and Spectral Baseline Fitting)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: imcontsub; zeroth-order polynomials mostly, a few first-order  
  > "Almost all baselines were fit with zeroth-order polynomials, with only a few exceptions requiring the use of first-order polynomials." (3.1 Imaging and Spectral Baseline Fitting)
- line free channels: Only 10 line-free channels per window (70 for Band 6 window near 219 GHz)  
  > "only 10 spectral channels are believed to be line-free (the Band 6 spectral window near 219 GHz is estimated to have 70 line-free channels)" (3.1 Imaging and Spectral Baseline Fitting)
- primary beam correction: _not stated_
- array combination: CASA feather of 12m and ACA cubes  
  > "Combination of the 12m Array and ACA measurements for each spectral window was done by employing the CASA implementation of the feathering technique, using the task `feather`." (3.1 Imaging and Spectral Baseline Fitting)
- smoothing: _not stated_
- final beam: 12m: 1.52x0.87" (218 GHz) to 0.43x0.28" (365 GHz)  
  > "| 218.222192     | 5.5        | $1.52\times0.87$@$+82.15$                 | 2.5             |" (Table 3)
- final rms: 2.0-3.2 mJy/beam per channel (Band 7); continuum 0.3-1.5 mJy/beam  
  > "| 364.819285     | 3.5        | $0.43\times0.28$@$-86.00$                 | 3.2             |" (Table 3)

### Inherited from earlier work

- Hildebrand-style optically thin dust mass/column formulae  
  > "using the well-worn dust emission assumptions elucidated by (cite: Hildebrand1983)" (3.3 Spatial Component Hydrogen Column Density and Mass) [from (cite: Hildebrand1983)]
- Gas-to-dust ratio Rgd = 150  
  > "Our assumption of $R_{gd} = 150$ follows that of (cite: Leroy2015) and (cite: Weiss2008)" (3.3 Spatial Component Hydrogen Column Density and Mass) [from (cite: Leroy2015; Weiss2008)]
- Optically thin column density formula and line strengths  
  > "from (cite: Mangum2015) we adopt the total molecular column density in the optically thin limit" (6 Molecular Spectral Line Column Density) [from (cite: Mangum2015)]

### Not stated but needed to reproduce (our reading)

- clean parameters (weighting/robust, cell size, image size, niter, threshold, masks)
- self-calibration solution intervals beyond 60 s averaging, reference antenna, which datasets and whether archive products were used
- feather parameters (sdfactor, uv cut) and primary beam correction details
- which channels were line-free in each window and where polynomial order exceptions apply
- exact ALMA/CASA versions used
- how Gaussian fit regions and Band 6 vs 7 averaged values combined
- exact LVG grid values and interpolation scheme for the Tk ratio mapping
- how upper limits and uncertainties on column densities were propagated

## Analysis recipe

1. **Self-calibrate and image cubes, combine 12m+ACA**: Phase-only self-cal on continuum, clean imaging per spw, feather 12m and ACA cubes  
  > "Combination of the 12m Array and ACA measurements for each spectral window was done by employing the CASA implementation of the feathering technique, using the task `feather`." (3.1 Imaging and Spectral Baseline Fitting)
   - software: CASA
   - parameter: phase-only self-cal, 60 s averaging, one iteration  
  > "one iteration of phase-only self-calibration utilizing a 60 second averaging time was used" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Subtract baseline and make pseudo-continuum images**: imcontsub with low-order polynomial, then collapse line-free channels  
  > "the line-free channels from each spectral window were collapsed to form a pseudo-continuum image of NGC 253 in each spectral window." (3.1 Imaging and Spectral Baseline Fitting)
   - software: CASA
   - fitting: _not stated_
   - validation: Visual inspection of baseline removal  
  > "Visual inspections of the quality of the baseline removal for all spectral windows indicate good quality overall." (3.1 Imaging and Spectral Baseline Fitting)
3. **Identify GMC components and derive H2 column density and mass from dust**: Single-component elliptical Gaussian fits to continuum peaks; optically thin dust formulae  
  > "we have fit single-component elliptical Gaussians to each of the continuum peaks in these images." (3.2 Spatial Component Identification)
   - parameter: Rgd=150, beta=1.5, Td=35 K, D=3.5 Mpc  
  > "Assuming R$_{gd} = 150$, T$_d = 35$ K, $\tau_d
  \ll 1$, $\beta = 1.5$, and D = 3.5 Mpc." (Table 5)
   - assumption: Thermal dust, optically thin; hydrogen dominated by H2  
  > "assuming that the continuum emission is dominated by thermal dust emission" (3.3 Spatial Component Hydrogen Column Density and Mass)
   - fitting: _not stated_
   - validation: Compared with Leroy2015 masses and PerezBeaupuits2018 total CMZ mass  
  > "The GMC hydrogen masses we derive are consistent with those measured by (cite: Leroy2015)" (3.3 Spatial Component Hydrogen Column Density and Mass)
4. **Identify lines and extract integrated intensities**: ALMA Data-Mining Toolkit plus by-eye line lists; CubeLineMoment masking with Gaussian PPV masks; gaussfit_catalog spatial fits  
  > "we have developed a python script, called `CubeLineMoment`, which uses a series of spectral and spatial masks to extract integrated intensities for a defined list of target spectral frequencies." (4.2 Spectral Line Signal Extraction and Spatial Component Fitting)
   - software: CubeLineMoment, spectral-cube, gaussfit_catalog, pyspeckit, ALMA Data-Mining Toolkit
   - parameter: Tracer lines C18O 2-1 (B6) and H2CO 5_15-4_14 (B7); mask at 1-sigma on model Gaussian; detections >2 sigma  
  > "For each spatial pixel, spectral pixels are masked out below the 1-$\sigma$ level evaluated on the model Gaussian." (4.2 Spectral Line Signal Extraction and Spatial Component Fitting)
   - fitting: Gaussian spatial fits with pyspeckit  
  > "which uses `pyspeckit` to perform gaussian fits of the spatial molecular spectral line components" (4.2 Spectral Line Signal Extraction and Spatial Component Fitting)
   - validation: H2CO peak positions compared with continuum and literature positions  
  > "all peak H$_2$CO positions are consistent within respective measurement uncertainties with their corresponding ALMA Band 6 and 7 continuum positions" (4.2 Spectral Line Signal Extraction and Spatial Component Fitting)
5. **Derive kinetic temperature from H2CO ratios**: Interpolate measured H2CO integrated-intensity ratios onto LVG model grid  
  > "we have interpolated our measured integrated intensity ratios onto our LVG model grid assuming $\log(N(species-H_2CO)/\Delta
v) = 12.5$ cm$^{-2}$/(km s$^{-1}$) and $\log(n(H_2)) = 5.0$" (5 Kinetic Temperature Derivation Using Formaldehyde)
   - software: LVG code (Mangum & Wootten 1993)
   - parameter: Ratios: 3_03-2_02/3_21-2_20, 5_15-4_14/5_3-4_3, 5_24-4_23/5_4-4_4, 5_23-4_22/5_4-4_4; sensitivity upper limits applied  
  > "We rely then on the $\frac{Sdv(3_{03}-2_{02})}{Sdv(3_{21}-2_{20})}$, $\frac{Sdv(5_{15}-4_{14})}{Sdv(5_{3}-4_{3})}$" (5 Kinetic Temperature Derivation Using Formaldehyde)
   - assumption: LVG approximation; collisional rate uncertainties (up to 50%) not included  
  > "uncertainties in the collisional excitation rates (cite: Green1991), which can be as high as 50% for state-to-state rates, are not included in our analysis uncertainties" (5 Kinetic Temperature Derivation Using Formaldehyde)
   - fitting: _not stated_
   - validation: Compared with previous Tk measurements (NH3, SED fits)  
  > "These previous dense molecular gas kinetic temperature measurements are consistent with our H$_2$CO-derived kinetic temperatures in NGC 253." (5.1 Comparison to Previous Kinetic Temperature Measurements)
6. **Derive molecular column densities and abundances**: Optically thin LTE formula at TK=150 K; abundance = N/N(H2) from dust  
  > "We have chosen T$_K = 150$ K as the representative kinetic temperature for our molecular column density calculations" (6 Molecular Spectral Line Column Density)
   - parameter: Tex=Tkin=Trot=150 K, filling factor 1  
  > "the excitation temperature of the measured position is much larger than the background temperature and equal to the kinetic temperature and that the source filling factor is unity" (6 Molecular Spectral Line Column Density)
   - assumption: Optically thin emission  
  > "we assume a kinetic temperature derived from our H$_2$CO measurements (see Section [5](#H2COTk)) in the optically thin limit." (6 Molecular Spectral Line Column Density)
   - fitting: _not stated_
   - validation: LVG check gives tau ~0.1 for 13CO/C18O; tau ~0.8 and 0.4 for H2CO 3_03 and 3_22  
  > "we find that $\tau\simeq 0.1$ for both $^{13}$CO and C$^{18}$O $3-2$" (6 Molecular Spectral Line Column Density)
7. **Compare abundances with chemical heating models and radio/IR diagnostics**: Compare abundance patterns with Meijerink2011 and Bayet2011 predictions; examine H3O+/SO ratio  
  > "we have made a direct comparison of the abundances of these two direct CR tracers for the different regions" (7.2 Chemical Diagnostics of Dense Gas Heating)
   - fitting: _not stated_
   - validation: _not stated_
8. **Test CH3OH level inversion**: LVG grid over density, column and Tk  
  > "we could not find *any* set of physical conditions where the populations of the CH$_3$OH $9_{5}-10_{4}E$ and $13_{0}-12_{1}A^+$ transitions were *not* inverted." (8 Vibrationally Excited Molecules and Possible Non-LTE Methanol Emission)
   - software: RADEX (van der Tak 2007 LVG)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration, clean, feather, imcontsub  
  > "Spectral cube imaging was performed using the CASA package." (3.1 Imaging and Spectral Baseline Fitting)
- **CubeLineMoment** : Masked moment extraction of line integrated intensities  
  > "we have developed a python script, called `CubeLineMoment`" (4.2 Spectral Line Signal Extraction and Spatial Component Fitting)
- **spectral-cube** : Cube handling in CubeLineMoment  
  > "`CubeLineMoment` makes extensive use of `spectral-cube`" (4.2 Spectral Line Signal Extraction and Spatial Component Fitting)
- **gaussfit_catalog / pyspeckit** : Spatial Gaussian fits of line components  
  > "we have used the `gaussfit_catalog` application, which uses `pyspeckit`" (4.2 Spectral Line Signal Extraction and Spatial Component Fitting)
- **ALMA Data-Mining Toolkit** : Initial spectral line identification  
  > "the ALMA Data-Mining Toolkit (cite: Teuben2015) was used to search for the most appropriate identification of spectral features" (4.1 Spectral Line Identification)
- **Astropy** : Listed in software acknowledgment  
  > "CASA, spectral-cube (cite: Robitaille2016), PySpecKit (cite: Ginsburg2011b), Astropy (cite: astropy2018)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H2CO-derived Tk on ~5" (~80 pc) scales | >=50 (50 to >=150) | not stated | K | 5 | On $\sim
5^{\prime\prime}$ scales we measure $T_K \gtrsim 50$ K, while on size scales $\lesssim 1^{\prime\prime}$ we measure $T_K \gtrsim 300$ K. |
| Tk on <=1" (<=16 pc) scales | >300 | not stated | K | 5 | On $\sim
5^{\prime\prime}$ scales we measure $T_K \gtrsim 50$ K, while on size scales $\lesssim 1^{\prime\prime}$ we measure $T_K \gtrsim 300$ K. |
| Region 5 continuum Sν at 218 GHz | 68.24 | 6.00 | mJy | 3 | / 5            / $68.24\pm6.00$  / $25.33\pm2.23$                             / $26.60\pm2.34$                                       / |
| Region 6 averaged N(H2) at 360 GHz | 68.09e23 | 3.06e23 | cm^-2 | 3 | / 6              / $68.09\pm3.06$                                               / $4.93\pm0.22$                                                          / |
| Range of N(H2) across GMCs | 1.29-68.09e23 | not stated | cm^-2 | 3 | N(H$_2$) and M(H$_2$) range from $1.29-68.09\times10^{23}$ cm$^{-2}$ and $0.19-23.63\times10^{6}$ M$_\odot$, respectively. |
| H2CO total column density in Region 6 (TK=150 K) | 47.11e14 | 29.56e14 | cm^-2 | 6 | / H$_2$CO        / 7           / $11.12\pm5.11$   / $38.04\pm19.60$  / $41.34\pm10.28$  / $47.11\pm29.56$  / $22.68\pm5.14$   / |
| SO abundance Region 5 vs Region 7 | 1.37e-10 vs 23.18e-10 | 0.39e-10 / 8.20e-10 | dimensionless | 6 | / SO           / $2.54\pm0.70$  / $4.45\pm0.85$   / $1.37\pm0.39$   / $8.67\pm1.36$    / $23.18\pm8.20$   / |
| CH3OH excitation temperature (A-type) in LVG models | -8 to -32 | not stated | K | 8 | Excitation temperatures for these two transitions range from T$_{ex}$(CH$_3$OH-A) = $-8$ to $-32$ K |
| Self-cal S/N improvement Band 6 continuum (12m, ACA) | 2.9, 1.9 | not stated | dimensionless | 1 | signal-to-noise improvement by factors of 2.9 and 1.9 in the Band 6 continuum of our 12m Array and ACA data, respectively |

## Qualitative findings

- Molecular abundances of CR/mechanical-heating sensitive species are lowest toward central Region 5 and rise outward, consistent with CR heating concentrated near the center  
  > "Derived molecular column densities point to a radially decreasing abundance of molecules with sensitivity to cosmic-ray and mechanical heating within the NGC 253 CMZ." (abstract)
- Vibrationally excited HNC and HC3N and CH3OH peak at off-nuclear Region 6 with strong mid-IR source  
  > "vibrationally excited transitions from HNC and HC$_3$N are strongly peaked toward an off-nuclear (Region 6) GMC with an associated strong mid-infrared source." (Conclusions)
- Insufficient evidence for a low-luminosity AGN at the nucleus  
  > "there is insufficient evidence to support the existence of a low-luminosity AGN at the center of NGC 253." (Conclusions)

## Claim tuples

- H: Dense gas in the NGC 253 CMZ is hot, with high Tk on small scales | E: H2CO transition ratios mapped to Tk with an LVG grid | R: Tk >~50 K on ~5" scales and >300 K on <=1" scales | F: Very high dense gas kinetic temperatures exist, beyond the technique's limits | **supported**
- H: Cosmic rays and/or mechanical heating drive the high Tk | E: Compared molecular abundances to PDR/CR/mechanical models plus radio spectral indices | R: Abundances of CR-sensitive molecules lower near center; steep-spectrum sources concentrated in Region 5 | F: CR heating plausible and favored, mechanical heating not excluded | **partially**
- H: Anomalous spatial distribution of CH3OH 9_5-10_4E and vibrational HNC/HC3N shares a common origin | E: LVG models of CH3OH over broad parameter ranges | R: Level populations always inverted | F: Amplification of a background continuum source is a plausible explanation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: H2CO is a kinetic temperature probe in dense gas due to K-ladder structure  
  > "the formaldehyde molecule possesses structural properties that allow for its rotational transitions to be used as probes of the kinetic temperature in dense molecular gas environs." (5 Kinetic Temperature Derivation Using Formaldehyde)
- Alternative: LLAGN explanation for the central radio source TH2 rejected based on flat spectral index, VLBI non-detection, no IR counterpart, no variability  
  > "There are several additional observations, though, which argue against the LLAGN explanation for TH2:" (7.1 Radio, Near-Infrared, and X-Ray Diagnostics of Dense Gas Heating)
- How they decided it was enough: _not stated_
- Limitation (authors): Rgd for diffuse Milky Way gas may not apply to the dense CMZ  
  > "Even though it is not clear whether a diffuse gas Milky Way value for $R_{gd}$ is appropriate to the dense CMZ of NGC 253" (3.3 Spatial Component Hydrogen Column Density and Mass)
- Limitation (authors): H3O+/SO ratio affected by optical depth and calibration; factor of two differences possible  
  > "Factor of two differences could be explained by these two effects." (7.2 Chemical Diagnostics of Dense Gas Heating)
- Limitation (authors): Total Power data unusable so no zero-spacing beyond ACA  
  > "The TP measurements have proven to be unusable owing to incomplete telluric line removal" (2 Observations)
- Caveat (inferred, ours): Single fixed TK=150 K and optically thin assumption for all species and regions drives abundances
- Caveat (inferred, ours): Abundances depend on dust-derived N(H2) with assumed Rgd, Td and beta, and compare Band 6 and 7 at different resolutions
- Caveat (inferred, ours): Single-density LVG grid (n=1e5, N/dv=1e12.5) assumed for Tk
- Caveat (inferred, ours): CR vs mechanical heating inferred qualitatively, no quantitative model fit
- Caveat (inferred, ours): Missing TP and weak ACA contribution may bias extended emission

## Reproducibility

- Data public (paper): Data from ALMA projects with acknowledgment of ADS/JAO.ALMA numbers; public status not explicitly stated  
  > "This article makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00099.S and ADS/JAO.ALMA#2015.1.00476.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: CubeLineMoment and gaussfit_catalog available on GitHub  
  > "<https://github.com/keflavich/mangum_galaxies/blob/master/CubeLineMoment.py>" (footnote 2)
- Missing: clean parameters and masks
- Missing: feather parameters
- Missing: LVG model grid and code
- Missing: CASA version
- Missing: self-cal details
- Data volume (inferred): ~100-300 GB raw for 12m+ACA Bands 6 and 7 (several execution blocks)
- Score (inferred): 3/5, Data and software partly public and main steps described, but imaging parameters, LVG grids and several choices are missing.
- Rediscovery candidate: no, Key imaging and LVG details are unstated, and conclusions are partly qualitative.

## Links

- Method: (cite: Mangum1993) (H2CO LVG kinetic temperature method)
- Method: (cite: Mangum2015) (Optically thin column density formalism)
- Method: (cite: Hildebrand1983) (Dust mass and column formulae)
- Companion: (cite: Leroy2015) (GMC component definitions, Td and Rgd)
- Companion: (cite: Ando2017) (Earlier ALMA Band 7 study of NGC 253 with similar components)
- Companion: (cite: Meier2015) (Earlier ALMA molecular line study of NGC 253 components)

## Checks

```json
{
 "quotes": 93,
 "quotes_ok": 93,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 100,
  "stated": 70,
  "rate": 0.7
 },
 "evidence_ok": true
}
```
