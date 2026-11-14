# Spiral arms and instability within the AFGL 4176 mm1 disc

`2020A&A...634L..11J` | Astronomy and Astrophysics 2020 | first author: Johnston, Katharine G. | arXiv: 1911.09692 | DOI: 10.1051/0004-6361/201937154

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Does the disc around the forming massive star AFGL 4176 mm1 show spiral structure and gravitational instability (Toomre Q < ~1.5-1.7)?  
  > "In this Letter, we present observations which show spiral structure within the disc of the forming massive star AFGL 4176 mm1, which lies at a distance of 4.2 kpc (cite: green11a)." (Introduction)
- Target **AFGL 4176 mm1 (mm1-main)**: coordinates 13:43:01.689 -62:08:51.25 (ICRS, pointing centre)  
  > "the forming massive star AFGL 4176 mm1, which lies at a distance of 4.2 kpc (cite: green11a)" (Introduction); "with one pointing centred on 13$^{h}$43$^{m}$01.689$^{s}$ $-$62$^{\circ}$08$'$51.25$''$ (ICRS)" (2 Observations); z/distance 4.2 kpc  
  > "the forming massive star AFGL 4176 mm1, which lies at a distance of 4.2 kpc (cite: green11a)" (Introduction); "with one pointing centred on 13$^{h}$43$^{m}$01.689$^{s}$ $-$62$^{\circ}$08$'$51.25$''$ (ICRS)" (2 Observations); distance from Green & McClure-Griffiths 2011 (cite: green11a)  
  > "the forming massive star AFGL 4176 mm1, which lies at a distance of 4.2 kpc (cite: green11a)" (Introduction); "with one pointing centred on 13$^{h}$43$^{m}$01.689$^{s}$ $-$62$^{\circ}$08$'$51.25$''$ (ICRS)" (2 Observations)

## Data provenance

- ALMA projects: 2017.1.00700.S
- bands: Band 6, ~250 GHz (1.2 mm)  
  > "The observations were taken in dual polarisation mode in Band 6 at a frequency of $\sim$250 GHz (1.2 mm)" (2 Observations)
- frequencies and spectral setup: Four spectral windows centred 239.298, 241.478, 253.106, 255.411 GHz; 1920 channels each; Hanning smoothed  
  > "| 239.298           | 0.469     | 1920      | 282        | 0.353         |" (Table 1)
- continuum bandwidth: _not stated_
- arrays: 12 m array, Cycle 5  
  > "We observed AFGL 4176 with the 12 m antenna array of ALMA Cycle 5" (2 Observations)
- configurations: _not stated_
- baselines: 118.1 m-15.0 km, 113.0 m-13.9 km, 92.1 m-8.5 km  
  > "with baseline lengths ranging between 118.1 m-15.0 km, 113.0 m-13.9 km, and 92.1 m-8.5 km" (2 Observations)
- angular resolution: ~30 mas (~130 au), robust=0.5  
  > "the angular resolution for the continuum is $\sim$30 mas or $\sim$130 au (d=4.2 kpc, robust=0.5 weighting)" (2 Observations)
- max recoverable scale: ~1.6 arcsec (6700 au)  
  > "the largest angular scale that the observations are sensitive to is $\sim$1.6$''$ (or 6700 au, corresponding to a baseline of 92.1 m)" (2 Observations)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 3 Oct, 4 Nov, 25 Nov 2017  
  > "on 3 October 2017, 4 November 2017, and 25 November 2017" (2 Observations)
- pi or archival as stated: _not stated_
- Line: CH3CN J=13-12 K-ladder (K=3 shown) (not stated)
- Other facility **ATCA**: 1.23 cm compact continuum source, 1.33 mJy (Johnston et al., submitted)  
  > "there is a coincident compact continuum source at 1.23 cm measured with ATCA with an integrated flux of 1.33 mJy (Johnston et al., submitted)" (3.1 1.2 mm continuum)
- External data: Previous ALMA results: 50±4 mJy flux at ~0.3'' and radiative transfer disc mass 12 Msun, radius 2000 au, i=30 deg  
  > "(50$\pm$4 mJy)" (3.1 1.2 mm continuum) [from Johnston et al. 2015 (cite: johnston15a)]
- External data: Dust opacity from Draine Milky-Way Rv=5.5 model  
  > "represented by the Draine Milky-Way $R_{\rm V}$=5.5 model" (Resolved Toomre Q map) [from (cite: draine03a; draine03b)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline plus phase-only self-calibration on continuum, applied to line data  
  > "In addition to the pipeline calibration, we performed phase-only self-calibration to the continuum and applied these solutions to the line data before imaging." (2 Observations)
- casa version: CASA 5.1.1-5 r40000 for reduction; 5.3.0 for imaging  
  > "version 5.1.1-5 r40000 via the pipeline version 40896 (Pipeline-CASA51-P2-B), and imaging was carried out in CASA version 5.3.0" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1427-4206 (bandpass and flux)  
  > "The bandpass and absolute flux calibrator was J1427-4206" (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: multiscale clean  
  > "The continuum was imaged using multiscale clean and a Briggs weighting parameter of 0.5." (2 Observations)
- weighting robust: continuum robust 0.5; line robust 1.0  
  > "imaged using multiscale clean, a robust parameter of 1.0, and a channel width of 1 km s$^{-1}$ to improve sensitivity" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: line channel width 1 km/s  
  > "a channel width of 1 km s$^{-1}$ to improve sensitivity" (2 Observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- CASSIS fitting setup of CH3CN K-ladder  
  > "We used the same setup as described in J15 but with slightly updated initial parameter ranges" (4 CH3CN line emission) [from Johnston et al. 2015 (cite: johnston15a)]
- Disc mass assumptions T=190 K, kappa=0.24 cm2/g, mass-to-dust 154  
  > "Using the same assumptions as J15, including $T=$190 K, $\kappa_\nu=$0.24 cm$^{2}$g$^{-1}$, and a total-mass-to-dust ratio of 154" (3.1 1.2 mm continuum) [from J15 (cite: johnston15a)]
- Spiral fitting approach following DSHARP  
  > "Similar to the analysis that was carried out for the Disk Substructures at High Angular Resolution Project (cite: kurtovic18a; huang18a)" (3.1 1.2 mm continuum) [from (cite: kurtovic18a; huang18a)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum
- Self-calibration solution intervals and number of iterations
- Cell size, image size, clean masks and multiscale scales
- Continuum-subtraction method for line data
- Final continuum rms and beam
- Pixel-wise CASSIS fitting details, S/N cuts and CH3CN/CH3 13CN ratio
- How the central source was subtracted and deprojection procedure
- Beam area and temperature used in the Sigma calculation per pixel

## Analysis recipe

1. **Measure continuum fluxes and disc mass**: Peak and integrated flux of mm1-main; mass from optically thin dust emission  
  > "the integrated flux above 1$\sigma$ is 42.67$\pm$0.03 mJy" (3.1 1.2 mm continuum)
   - software: CASA
   - assumption: T=190 K, kappa=0.24 cm2/g, mass-to-dust 154  
  > "including $T=$190 K, $\kappa_\nu=$0.24 cm$^{2}$g$^{-1}$, and a total-mass-to-dust ratio of 154" (3.1 1.2 mm continuum)
   - fitting: _not stated_
   - validation: Compared with J15 flux (within 2 sigma)  
  > "but it is still within 2$\sigma$" (3.1 1.2 mm continuum)
2. **Fit and subtract central compact source**: 2D Gaussian fit with imfit  
  > "We fitted this central source with a 2D Gaussian using imfit in CASA and subtracted it" (3.1 1.2 mm continuum)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Disc size and inclination**: Ellipse at 5 sigma, semi-major axis; minimum semi-minor axis gives inclination upper limit  
  > "The smallest semi-minor axis that is consistent with the shape of the disc is 0.15$''$" (3.1 1.2 mm continuum)
   - fitting: _not stated_
   - validation: Consistent with J15 i=30 deg  
  > "This is consistent with the inclination of 30$^{\circ}$ found for the best-fitting model of J15." (3.1 1.2 mm continuum)
4. **Fit spiral arm**: Fit peak radius vs position angle in deprojected residual map with logarithmic and Archimedean spirals  
  > "we fitted the peak positions of the western spiral arm with both logarithmic and Archimedean spirals using the `curve_fit` function in `scipy` with the Levenberg-Marquardt algorithm" (3.1 1.2 mm continuum)
   - software: scipy
   - parameter: Position error = half beam major axis / S/N of 5; points weighted by beam spacing  
  > "half the major axis of the beam divided by the lowest signal-to-noise ratio of the detected emission in the arm, that is, five" (3.1 1.2 mm continuum)
   - assumption: PA=60 deg, i=30 deg  
  > "assuming a position angle of 60$^{\circ}$ and an inclination angle of 30$^{\circ}$" (3.1 1.2 mm continuum)
   - fitting: Levenberg-Marquardt least squares, chi2 comparison  
  > "With a lower $\chi^2$ of 8.9, the Archimedean spiral model more closely reproduces the data." (3.1 1.2 mm continuum)
   - validation: _not stated_
5. **Temperature and velocity maps from CH3CN**: Per-pixel MCMC chi2 fit of CH3CN and CH3 13CN J=13-12 K-ladder in CASSIS under LTE  
  > "fitting the CH$_3$CN and CH$_3^{13}$CN J=13-12 K-ladder emission associated with each pixel with the Markov Chain Monte Carlo $\chi^2$ minimisation algorithm" (3.2 CH3CN line emission)
   - software: CASSIS
   - parameter: Tex 50-350 K, vLSR -58 to -48 km/s, vFWHM 0.5-15 km/s, N 1e15-1e18 cm-2  
  > "$T_{\rm ex}$ = 50 – 350 K, v$_{_{\rm LSR}}$ = -58 – -48 km s$^{-1}$, v$_{_{\rm FWHM}}$ = 0.5 – 15 km s$^{-1}$" (3.2 CH3CN line emission)
   - assumption: LTE so Tex approximates kinetic temperature  
  > "As we assume local thermodynamic equilibrium (LTE) in our analysis, $T_{\rm ex}$ therefore provides an estimate of the kinetic temperature." (3.2 CH3CN line emission)
   - fitting: _not stated_
   - validation: _not stated_
6. **Toomre Q map**: Q = c_s kappa/(pi G Sigma); c_s from CASSIS T, Omega from deprojected velocity/radius, Sigma from continuum  
  > "we used the results from previous sections to construct a map of the Toomre parameter $Q$ across the disc" (3.3 Resolved Toomre Q map)
   - parameter: vlsr = -52.5 km/s; mean molecular weight 2.37  
  > "subtracting the systematic velocity ($v_{\rm lsr}$=-52.5 km s$^{-1}$)" (3.3 Resolved Toomre Q map)
   - assumption: Keplerian kappa=Omega; Draine MW Rv=5.5 dust  
  > "Here we assume that the disc is close to Keplerian so that $\kappa=\Omega$" (3.3 Resolved Toomre Q map)
   - fitting: _not stated_
   - validation: Repeated without Keplerian assumption (Appendix) and with dust opacity doubled  
  > "In the case the assumed dust opacity $\kappa_{\nu}$ is a factor of two higher" (3.3 Resolved Toomre Q map)

## Software

- **CASA** 5.1.1-5 (calibration), 5.3.0 (imaging): Calibration, imaging, imfit  
  > "imaging was carried out in CASA version 5.3.0" (2 Observations)
- **scipy curve_fit** : Spiral fitting  
  > "using the `curve_fit` function in `scipy` with the Levenberg-Marquardt algorithm" (3.1 1.2 mm continuum)
- **CASSIS** : LTE MCMC fit of CH3CN maps  
  > "Instrumentaux et Synthétiques tool (CASSIS)" (3.2 CH3CN line emission)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| mm1-main peak flux | 10.72 | 0.02 | mJy/beam | 1 | The peak flux of mm1-main is 10.72$\pm$0.02 mJy beam$^{-1}$ |
| mm1-main integrated flux above 1 sigma | 42.67 | 0.03 | mJy | 1 | the integrated flux above 1$\sigma$ is 42.67$\pm$0.03 mJy |
| Disc mass | 6.6 (4.4 without compact source) | not stated | Msun | 1 | we find that the disc mass is 6.6 M$_{\odot}$ |
| Disc radius | ~1000 | not stated | au | 3 | giving a disc radius of $\sim$1000 au |
| Inclination upper limit | 51 | not stated | deg | 3 | providing an upper limit to the inclination of 51$^{\circ}$ |
| Central source integrated flux | 13.9 | not stated | mJy | 2 | an integrated flux of 13.9 mJy |
| cm-mm spectral index of compact source | ~0.9 | not stated | dimensionless | 2 | the spectral index between the centimetre and millimetre compact continuum sources is $\sim$0.9 |
| Archimedean spiral b | 337.9 | 10.5 | au | 4 | $337.9 \pm 10.5$ au |
| Logarithmic spiral chi2 | 17.8 (Archimedean 8.9) | not stated | dimensionless | 4 | $\arctan{(b)}= -27.4^{\circ}$ / 17.8 / |

## Qualitative findings

- Continuum shows a western spiral arm and eastern arc; mm1 splits into mm1-main, mm1b, mm1c, mm1d  
  > "now splits into four sources: mm1-main, mm1b, mm1c, and mm1d" (3.1 1.2 mm continuum)
- Eastern arc and densest parts of western spiral are Toomre unstable  
  > "the left (eastern) arc is clearly Toomre unstable" (3.3 Resolved Toomre Q map)

## Claim tuples

- H: The mm1 disc contains spiral structure | E: 1.2 mm continuum at ~30 mas, spiral fits | R: Western spiral arm and eastern arc; Archimedean fit better (chi2 8.9 vs 17.8) | F: Asymmetric spiral, likely shaped partly by companions | **supported**
- H: The disc is gravitationally unstable | E: Q map from CASSIS T, velocity and continuum surface density | R: Eastern arc and dense western spiral have Q below threshold | F: Disc may fragment | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Logarithmic (GI-like) spiral model fit worse than Archimedean  
  > "With a lower $\chi^2$ of 8.9, the Archimedean spiral model more closely reproduces the data." (3.1 1.2 mm continuum)
- How they decided it was enough: _not stated_
- Limitation (authors): CH3CN traces hotter upper layers, not midplane; local optical depth may underestimate Sigma; Q is an upper limit  
  > "We note that the CH$_3$CN does not trace the midplane, but hotter material higher in the disc atmosphere." (3.3 Resolved Toomre Q map)
- Caveat (inferred, ours): Q depends on assumed dust opacity, gas-to-dust ratio and LTE temperature
- Caveat (inferred, ours): Central Q values are artefacts
- Caveat (inferred, ours): Spiral fit uses peak positions with a single arm and assumed i=30, PA=60
- Caveat (inferred, ours): No Q uncertainty propagation

## Reproducibility

- Data public (paper): Program 2017.1.00700.S named; public status not stated  
  > "under program 2017.1.00700.S (PI: Johnston)" (2 Observations)
- Products in archive: _not stated_
- Missing: Clean parameters, masks and self-cal details
- Missing: CASSIS setup details from J15
- Missing: Deprojection and Q map pixel procedure
- Data volume (inferred): ~200-500 GB raw for three long-baseline EBs
- Score (inferred): 3/5, Data identified and main methods described, but imaging/self-cal and CASSIS details are missing or inherited.
- Rediscovery candidate: no, Recipe lacks key imaging and CASSIS parameters and relies on J15.

## Links

- Method: Johnston et al. 2015 (cite: johnston15a) (CASSIS setup and disc mass assumptions)
- Method: Kurtovic et al. 2018; Huang et al. 2018 (Spiral fitting approach)
- Companion: Johnston et al., submitted (ATCA 1.23 cm data)
- Related: DSHARP

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 48,
  "rate": 0.593
 },
 "evidence_ok": true
}
```
