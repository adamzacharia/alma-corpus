# ALMA spectral line and imaging survey of a low and a high mass-loss rate AGB star between 335 and 362 GHz

`2018A&A...615A..28D` | Astronomy and Astrophysics 2018 | first author: Decin, L. | arXiv: 1801.09291 | DOI: 10.1051/0004-6361/201732216

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, astrochemistry
- Question: What are the dominant physical, dynamical and chemical processes in the inner wind of the low mass-loss rate AGB star R Dor and the high mass-loss rate AGB star IK Tau, as traced by an ALMA band 7 spectral line and imaging survey?  
  > "We aim to characterise the dominant physical, dynamical, and chemical processes in the inner wind region of two archetypical oxygen-rich (C/O$<$1) AGB stars" (abstract)
- Target **IK Tau**: coordinates _not stated_; z/distance 260 pc  
  > "due to their proximity (260 pc and 59 pc, respectively)" (Introduction); distance from Table 1, cited from Decin et al. 2017 (Decin2017arXiv170405237D)  
  > "due to their proximity (260 pc and 59 pc, respectively)" (Introduction)
- Target **R Dor**: coordinates _not stated_; z/distance 59 pc  
  > "due to their proximity (260 pc and 59 pc, respectively)" (Introduction); distance from Table 1, cited from Decin et al. 2017 (Decin2017arXiv170405237D)  
  > "due to their proximity (260 pc and 59 pc, respectively)" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00166.S
- bands: Band 7, 335-362 GHz  
  > "IK Tau and R Dor were observed with ALMA in Band 7 during August-September 2015" (2.1 ALMA observations)
- frequencies and spectral setup: Full scan 335-362 GHz with four observations per star, each with four 1.875 GHz spectral windows  
  > "A full spectral scan between 335–362 GHz was made using four separate observations per star. Each observation used four 1.875 GHz spectral windows." (2.1 ALMA observations)
- continuum bandwidth: 15.2e3 MHz (IK Tau), 11.6e3 MHz (R Dor)  
  > "Width is the continuum bandwidth (spread over total spectral span)" (Table 2)
- arrays: An average of 39 good antennas  
  > "An average of 39 good antennas were present." (2.1 ALMA observations)
- configurations: _not stated_
- baselines: 0.04-1.6 km  
  > "The range of baseline lengths was 0.04–1.6 km" (2.1 ALMA observations)
- angular resolution: ~150 mas  
  > "allowing imaging of structure on angular scales up to 2$^{\prime\prime}$ at angular resolution $\sim$150 mas" (2.1 ALMA observations)
- max recoverable scale: ~2 arcsec  
  > "allowing imaging of structure on angular scales up to 2$^{\prime\prime}$ at angular resolution $\sim$150 mas" (2.1 ALMA observations)
- sensitivity: Channel rms 3-9 mJy (IK Tau), 2.7-5.7 mJy (R Dor); continuum rms 0.047 mJy  
  > "The range in IK Tau was 3–9 mJy and in R Dor the range was 2.7–5.7 mJy" (2.2 Data reduction)
- time on source: 10 min (IK Tau), 25 min (R Dor)  
  > "IK Tau | 2015-08-13 | 0.2–1.7 | 10" (Table 2.1 (obs))
- observing dates: August-September 2015  
  > "observed with ALMA in Band 7 during August-September 2015" (2.1 ALMA observations)
- pi or archival as stated: _not stated_
- Line: CO 3-2 (345.7960 GHz)
- Line: SiO 8-7 (v=0 to 5) (347.3306 GHz (v=0))
- Line: HCN 4-3 (354.5055 GHz)
- External data: Stellar and wind properties (D, L, T*, R*, Mdot, r_dust, v_inf) of both stars  
  > "Overview of stellar and wind properties of R Dor and IK Tau (cite: Decin2017arXiv170405237D)." (Table 1) [from (cite: Decin2017arXiv170405237D)]
- External data: Dust opacity ~7 cm2/g  
  > "for an opacity of $\sim$7 cm$^2$/g (cite: Demyk2017arXiv170609801D)" (3 Continuum image) [from (cite: Demyk2017arXiv170609801D)]
- External data: Dust temperature ranges 200-650 K (IK Tau) and 400-1530 K (R Dor)  
  > "dust temperature of varying between 200–650 K for IK Tau and 400–1530 K for R Dor (cite: Decin2017arXiv170405237D)" (3 Continuum image) [from (cite: Decin2017arXiv170405237D)]
- External data: Spectral line catalogues for line identification  
  > "spectral line catalogues of the Jet Propulsion Laboratory (cite: Pickett1998JQSRT..60..883P) and the Cologne Database for Molecular Spectroscopy" (4.1 Line identification) [from (cite: Pickett1998JQSRT..60..883P); (cite: Muller2001A&A...370L..49M)]

## Processing

### Calibration

- pipeline or manual: CASA following standard scripts  
  > "All data reduction was done using CASA(cite: McMullin2007ASPC..376..127M)[^1], following standard scripts for the application of calibration" (2.2 Data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-013 (IK Tau); J0519-454 (R Dor)  
  > "IK Tau | 2015-08-13 | 0.2–1.7 | 10 | 1.95 | J0423-013" (Table 2.1 (obs))
- flux scale uncertainty: ~7% or better  
  > "so the net flux scale accuracy is $\sim$7% or better" (2.2 Data reduction)
- self calibration: Self-calibration on line-free continuum channels, applied to all data  
  > "Line-free continuum channels were identified and used for self-calibration, applied to all data." (2.2 Data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust 0.5  
  > "all images discussed used partial uniform weighting (CASA ‘robust 0.5’)." (2.2 Data reduction)
- uv taper: _not stated_
- cell size: 0.04 arcsec (IK Tau), 0.03 arcsec (R Dor)  
  > "| IK Tau | 15.2e3 |  180$\times$160, 27$^{\circ}$  | 0.047 |    10    |   0.04   |" (Table 2)
- image size: 10 arcsec (IK Tau), 7.6 arcsec (R Dor)  
  > "| R Dor  | 11.6e3 | 150$\times$140, $-$5$^{\circ}$ | 0.047 |   7.6    |   0.03   |" (Table 2)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum subtracted, then entire cubes imaged  
  > "The continuum was subtracted and the entire cubes were imaged." (2.2 Data reduction)
- line free channels: _not stated_
- primary beam correction: Not applied initially, to keep flat noise  
  > "We did not apply the primary beam correction initially, since it is more straightforward to measure the largest angular size (LAS)" (2.2 Data reduction)
- array combination: _not stated_
- smoothing: Hanning smoothing in correlator; averaged every 4 (IK Tau) or 2 (R Dor) channels  
  > "Hanning smoothing was applied in the correlator and the data were finally averaged every four (two) channels for IK Tau (R Dor)" (2.1 ALMA observations)
- final beam: Continuum 180x160 mas PA 27 (IK Tau); 150x140 mas PA -5 (R Dor)  
  > "| IK Tau | 15.2e3 |  180$\times$160, 27$^{\circ}$  | 0.047 |    10    |   0.04   |" (Table 2)
- final rms: Continuum 0.047 mJy  
  > "The $\sigma_{\mathrm{rms}}$ for the continuum image is 0.047 mJy." (2.2 Data reduction)

### Inherited from earlier work

- Stellar/wind parameters, dust temperatures and the Al-molecule analysis  
  > "Overview of stellar and wind properties of R Dor and IK Tau (cite: Decin2017arXiv170405237D)." (Table 1) [from (cite: Decin2017arXiv170405237D)]
- Gas/drift/dust velocity profile from the momentum equation  
  > "Solving the momentum equation (cite: Decin2006A&A...456..549D), we calculate the gas, drift, and dust velocity profile" (3 Continuum image) [from (cite: Decin2006A&A...456..549D)]
- Soft-parabola function for line fitting  
  > "fitted using a so-called soft-parabola-function (cite: DeBeck2010A&A...523A..18D)" (4.1 Line identification) [from (cite: DeBeck2010A&A...523A..18D)]

### Not stated but needed to reproduce (our reading)

- Number of execution blocks and exact calibrator assignment per spectral window
- Line-free channel ranges used for continuum and self-calibration
- Self-calibration solution intervals and number of iterations
- tclean deconvolver, masks, clean thresholds and iteration counts
- Per-cube beam and rms for each spectral window
- Exact adopted stellar flux model at 345 GHz
- Parameters of the RADEX models used for line identification
- Whether archive products or a re-reduction were used

## Analysis recipe

1. **Calibrate and image continuum and line cubes**: Standard CASA calibration scripts, self-calibration on continuum channels, continuum subtraction, imaging of full cubes  
  > "Line-free continuum channels were identified and used for self-calibration, applied to all data." (2.2 Data reduction)
   - software: CASA
   - parameter: robust 0.5  
  > "all images discussed used partial uniform weighting (CASA ‘robust 0.5’)." (2.2 Data reduction)
   - fitting: _not stated_
   - validation: Astrometric accuracy checked using phase-reference solutions and check sources; 17 mas adopted  
  > "it seems reasonable to adopt 17 mas astrometric accuracy for both targets." (2.2 Data reduction)
2. **Derive dust mass and dust mass-loss rate from continuum**: Subtract convolved stellar point source from continuum, convert the residual to dust mass assuming optically thin emission, and compute crossing time from the momentum equation solution  
  > "we can estimate the 345 GHz emission from dust by subtracting a (stellar) point source, convolved with the natural synthesised beam, from the continuum" (3 Continuum image)
   - parameter: Drift velocity forced below 20 km/s  
  > "We force the drift velocity to be lower than 20 km/s" (3 Continuum image)
   - assumption: Optically thin dust, opacity ~7 cm2/g, dust temperature 200-650 K (IK Tau) and 400-1530 K (R Dor)  
  > "Assuming that the dust is optically thin and for an opacity of $\sim$7 cm$^2$/g" (3 Continuum image)
   - fitting: _not stated_
   - validation: Compared with dust-to-gas ratios from SED/SPHERE studies in literature; uncertainty factor ~5  
  > "subject to large uncertainties (being around a factor of 5)" (3 Continuum image)
3. **Identify spectral lines**: Extract spectra in circular apertures, accept lines above 3x local rms, match with JPL/CDMS catalogues and the SMA VY CMa atlas, check with non-LTE spectra, fit soft-parabola to find blends  
  > "lines were required to have continuous emission above 3$\times$ the local channel-map off-source rms." (4.1 Line identification)
   - software: RADEX, CASA
   - parameter: Apertures 80/320/800 mas (IK Tau), 75/300/1000 mas (R Dor)  
  > "of 80, 320 and 800 mas in radius (IK Tau) or 75, 300 and 1000 mas (R Dor)" (4.1 Line identification)
   - assumption: vLSR 33 km/s (IK Tau), 7 km/s (R Dor)  
  > "$v_{\rm{LSR}}$, of 33 km/s for IK Tau and of 7 km/s for R Dor" (4.1 Line identification)
   - fitting: Soft-parabola profile, not aimed at best-fit parameters  
  > "This fit was not aimed to retrieve the best-fit parameters since many lines display complex profiles." (4.1 Line identification)
   - validation: Manual inspection of blends  
  > "to identify in a last step by manual inspection blended lines and to determine the main component in the case of blends." (4.1 Line identification)
4. **Measure line widths, fluxes and angular extents**: Velocity span as continuous extent above 3.5 sigma; zeroth-moment maps; angular extent from annuli down to 1.5x off-source rms; azimuthal averages  
  > "The velocity span $\Delta v$ of single lines (or hyperfine blends of a single species) is taken to be the continuous extent above 3.5$\sigma_{\mathrm{chn\_rms}}$." (4.2 Analysis of the spectral cubes)
   - parameter: Annulus cutoff 1.5x off-source moment-map rms  
  > "until the flux density fell below 1.5 times the off-source rms of the moment map" (4.2 Analysis of the spectral cubes)
   - fitting: _not stated_
   - validation: Two angular size measures compared; difference gives asymmetry uncertainty  
  > "the difference providing the uncertainty in angular size due to source asymmetry." (4.2 Analysis of the spectral cubes)
5. **Compute isotopic ratios**: Intensity ratios of isotopologue lines with same quantum numbers, corrected for Einstein A / CDMS predicted intensity, frequency, partition function and lower energy  
  > "Line intensity ratios are corrected for the difference in Einstein A-coefficient" (5.4 Isotopic ratios)
   - assumption: Optically thin, LTE, no radiative pumping differences; masers excluded  
  > "the method of line intensities ratios is only valid under the assumption of optically thin emission in LTE" (5.4 Isotopic ratios)
   - fitting: _not stated_
   - validation: No formal uncertainty possible when a single transition pair is available  
  > "As a consequence, no formal uncertainty on the derived ratio can be calculated." (5.4 Isotopic ratios)
6. **Trace wind velocity versus radius**: Plot half-width at zero intensity versus half the spatial FWHM and compare with beta-law velocity profiles from literature  
  > "we plot the half-line width at zero intensity as a measurement of the wind velocities as a function of the radial distance" (5.3 Wind kinematics)
   - parameter: beta=1 (IK Tau), beta=5 (R Dor) from literature; beta=10 shown as guide  
  > "we have plotted, just to guide the eye, a model with a large but arbitrary value of $\beta$ = 10" (5.3 Wind kinematics)
   - fitting: _not stated_
   - validation: Compared with IRAM-30m widths using IRAM 3 sigma limit  
  > "If we were to determine the line widths of the brightest lines using the 3$\sigma$-values of IRAM as the limit, the velocities would shift down considerably" (5.3 Wind kinematics)

## Software

- **CASA** : Calibration, self-calibration, imaging and continuum subtraction  
  > "All data reduction was done using CASA(cite: McMullin2007ASPC..376..127M)" (2.2 Data reduction)
- **RADEX** : Non-LTE spectra for a fixed excitation temperature to help line identification  
  > "a non-LTE spectrum was calculated for a fixed excitation temperature using the -code (cite: vanderTak2007A&A...468..627V)" (4.1 Line identification)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum peak IK Tau | 0.069 | not stated | Jy/beam | 1 | The continuum peak is 0.069 Jy/beam for IK Tau and 0.596 Jy/beam for R Dor |
| Continuum peak R Dor | 0.596 | not stated | Jy/beam | 1 | The continuum peak is 0.069 Jy/beam for IK Tau and 0.596 Jy/beam for R Dor |
| Dust mass IK Tau | 3.7e-7 | factor ~5 | Msun | 2 | we obtain a dust mass within the 3$\sigma$ contour of $3.7 \times 10^{-7}$ M$_{\odot}$ and $2 \times 10^{-8}$ M$_{\odot}$ |
| Dust mass R Dor | 2e-8 | factor ~5 | Msun | 2 | we obtain a dust mass within the 3$\sigma$ contour of $3.7 \times 10^{-7}$ M$_{\odot}$ and $2 \times 10^{-8}$ M$_{\odot}$ |
| Dust mass-loss rate IK Tau | ~1e-8 | factor ~5 | Msun/yr | 2 | dust mass loss rate of $\sim$1$\times10^{-8}$ M$_{\odot}$/yr for IK Tau and of $\sim$5$\times10^{-9}$ M$_{\odot}$/yr for R Dor |
| Dust mass-loss rate R Dor | ~5e-9 | factor ~5 | Msun/yr | 2 | dust mass loss rate of $\sim$1$\times10^{-8}$ M$_{\odot}$/yr for IK Tau and of $\sim$5$\times10^{-9}$ M$_{\odot}$/yr for R Dor |
| Number of lines detected | 168 (IK Tau), 197 (R Dor); 66 unidentified | not stated | lines | 3 | A total of 168 lines is detected in IK Tau and of 197 lines in R Dor arising from 15 molecules |
| Maximum wind velocity traced | 36 (IK Tau), 23 (R Dor) | not stated | km/s | 6 | the maximum velocity traced for IK Tau is 36 km/s and for R Dor 23 km/s |
| 29Si/30Si IK Tau | 4.1 | not stated | dimensionless | 5 | For IK Tau, we derive that $^{29}$Si/$^{30}$Si$\approx$4.1 |
| 34S/33S IK Tau | 5.6 | 0.36 | dimensionless | 5 | $^{34}$S/$^{33}$S$\approx$5.6$\pm$0.36 |
| 35Cl/37Cl IK Tau | 1.1 | 0.21 | dimensionless | 5 | $^{35}$Cl/$^{37}$Cl$\approx$1.1$\pm$0.21 |
| 34S/33S R Dor | 7.8 | 0.7 | dimensionless | 5 | while for R Dor $^{34}$S/$^{33}$S$\approx$7.8$\pm$0.7 |

## Qualitative findings

- Sulphur chemistry dichotomy: CS, SiS, SO, SO2 in IK Tau but only SO and SO2 in R Dor  
  > "while CS, SiS, SO, and SO$_2$ are abundantly present in IK Tau, only SO and SO$_2$ are detected in R Dor." (abstract)
- Channel maps show blobs, arcs and/or a disk in the inner wind of both stars  
  > "both large and small-scale inhomogeneities persist in the inner wind of both stars in the form of blobs, arcs, and/or a disk" (abstract)

## Claim tuples

- H: Do line widths in the inner wind exceed the previously determined terminal velocities? | E: Measured half-width at zero intensity of many lines versus radius from ALMA spectra | R: Maximum velocities 36 km/s (IK Tau) and 23 km/s (R Dor) versus v_inf 17.7 and 5.5 km/s | F: The wind velocities are much larger than canonical values, explained by 3D morphology and/or more forceful acceleration | **supported**
- H: Do the two stars differ in molecular content? | E: Line identification in both spectral surveys | R: CS, SiS, NaCl, NS detected in IK Tau only; both have SO, SO2, TiO, TiO2 | F: Chemistry is vastly different between the high and low mass-loss rate stars | **supported**
- H: What are the dust masses in the inner wind? | E: Continuum minus stellar point source, optically thin dust | R: 3.7e-7 Msun (IK Tau) and 2e-8 Msun (R Dor) | F: Dust-to-gas ratios ~1/800 and ~1/250 with factor 5 uncertainty | **partially**
- H: Can fractal grain growth explain the accelerating wind? | E: Argument from velocity versus excitation energy trends beyond 400 mas and theory | R: Velocity correlates with upper-state energy | F: Fractal grain growth beyond ~400 mas may increase radiation pressure efficiency; only tentative | **partially**

## Reasoning

- Why this data: Resolution of ~150 mas matches the main dust formation region of both stars  
  > "at a spatial resolution of $\sim$150 mas, which corresponds to the locus of the main dust formation region of both targets" (abstract)
- Why this method: Population diagrams not used because lines are not isothermal and LTE  
  > "We refrain from performing a population diagram analysis of the molecules observed in the ALMA survey." (5.4 Isotopic ratios)
- Alternative: Thermal motions and pulsations rejected as the origin of the large velocities  
  > "the origin of the large velocities in both stars is a genuine physical mechanism not linked to thermal motions of the gas or pulsation behaviour of the atmospheric layers" (5.3 Wind kinematics)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust masses and dust-to-gas ratios uncertain by about a factor of 5  
  > "subject to large uncertainties (being around a factor of 5)" (3 Continuum image)
- Limitation (authors): Extended emission may be resolved out  
  > "we have resolved-out extended emission" (2.2 Data reduction)
- Caveat (inferred, ours): Stellar flux subtraction dominates dust mass uncertainty, especially for R Dor where the stellar part is ~90% of continuum
- Caveat (inferred, ours): Isotope ratios from single line pairs, with possible optical depth and pumping effects
- Caveat (inferred, ours): High-velocity wings could partly reflect lower noise or blends rather than genuine kinematics
- Caveat (inferred, ours): Fractal grain scenario is speculative and untested quantitatively

## Reproducibility

- Data public (paper): Data from ALMA project 2013.1.00166.S, acknowledged as ADS/JAO.ALMA2013.1.00166.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA2013.1.00166.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: tclean parameters and masks
- Missing: Line-free channel selection
- Missing: Self-calibration parameters
- Missing: RADEX model parameters
- Missing: Stellar flux model details
- Data volume (inferred): ~100-500 GB raw for 8 observations
- Score (inferred): 3/5, Data are public and the line measurement recipe is clear, but imaging and self-calibration details are sparse and many results are tabulated measurements.
- Rediscovery candidate: yes, Public data, with numeric results (dust masses, line widths, isotope ratios), though processing details are incomplete.

## Links

- Method: (cite: DeBeck2010A&A...523A..18D) (Soft-parabola line profile function)
- Method: (cite: Decin2006A&A...456..549D) (Momentum equation wind model)
- Companion: (cite: Decin2017arXiv170405237D) (Aluminium-bearing molecules in the same ALMA data)
- Companion: (cite: Homan2018) (Disk and companion in R Dor from the same data)
- Related: ATOMIUM

## Checks

```json
{
 "quotes": 86,
 "quotes_ok": 86,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 65,
  "rate": 0.756
 },
 "evidence_ok": true
}
```
