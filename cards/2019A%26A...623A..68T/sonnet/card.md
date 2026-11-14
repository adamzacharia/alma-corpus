# Small-scale physical and chemical structure of diffuse and translucent molecular clouds along the line of sight to Sgr B2

`2019A&A...623A..68T` | Astronomy and Astrophysics 2019 | first author: Thiel, V. | arXiv: 1901.03231 | DOI: 10.1051/0004-6361/201834467

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: milky_way_ism, astrochemistry
- Question: What is the spatial and kinematic structure, physical nature and chemistry of diffuse and translucent molecular clouds seen in absorption along the line of sight to Sgr B2(N)?  
  > "We aim to resolve and investigate the spatial structure of molecular clouds traced by several molecules detected in absorption along the line of sight to Sgr B2(N)." (abstract)
- Target **Sgr B2(N)**: coordinates phase centre EQ J2000: 17h47m19.87s, −28°22′16″  
  > "the white cross the phase centre (EQ J2000: 17 h 47 m 19.87 s, −28 ◦ 22 ′ 16 ′′ )" (Figure 1 caption); "The GC has a distance of 8.34 ± 0.16 kpc to the Sun (Reid et al. 2014)." (1. Introduction); z/distance GC at 8.34 ± 0.16 kpc; line-of-sight clouds at 1.0-7.0 kpc (Table 3)  
  > "the white cross the phase centre (EQ J2000: 17 h 47 m 19.87 s, −28 ◦ 22 ′ 16 ′′ )" (Figure 1 caption); "The GC has a distance of 8.34 ± 0.16 kpc to the Sun (Reid et al. 2014)." (1. Introduction); distance from Reid et al. 2014 for GC; approximate arm distances in Table 3  
  > "the white cross the phase centre (EQ J2000: 17 h 47 m 19.87 s, −28 ◦ 22 ′ 16 ′′ )" (Figure 1 caption); "The GC has a distance of 8.34 ± 0.16 kpc to the Sun (Reid et al. 2014)." (1. Introduction)

## Data provenance

- ALMA projects: 2011.0.00017.S, 2012.1.00012.S
- bands: _not stated_
- frequencies and spectral setup: 84.1 to 114.4 GHz (3 mm), spectral resolution 488 kHz (1.7 to 1.3 km/s)  
  > "The survey covers the frequency range from 84.1 to 114.4 GHz with a spectral resolution of 488 kHz (1.7 to 1.3 km s [−][1] ) at a median angular resolution of 1. [′′] 6." (2. Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: median 1.6″  
  > "at a median angular resolution of 1. [′′] 6. The median largest angular scale is 21. [′′] 4." (2. Observations)
- max recoverable scale: median largest angular scale 21.4″  
  > "The median largest angular scale is 21. [′′] 4." (2. Observations)
- sensitivity: average ~3 mJy/beam per channel  
  > "The average noise level is ~3 mJy beam [−][1] per channel." (2. Observations)
- time on source: _not stated_
- observing dates: ALMA Cycles 0 and 1  
  > "This spectral line survey was observed with ALMA in Cycles 0 and 1." (2. Observations)
- pi or archival as stated: _not stated_
- Line: ortho c-C3H2 2(1,2)-1(0,1) (85338.894 MHz)
- Line: HCO+ / H13CO+ 1-0 (H13CO+ 86754.288 MHz)
- Line: CS 2-1 (97980.953 MHz)
- Line: SiO 2-1 (86846.985 MHz)
- Line: HNC 1-0 (90663.568 MHz)
- Other facility **Mopra 22 m (Jones et al. 2008 survey)**: 3 mm imaging survey of HCO+, HNC, CS, 13CO emission used to test whether clouds are dense  
  > "The observations were carried out with the 22 m Mopra Millimetre Telescope in June 2006 in on-the-fly mode" (2. Observations)
- External data: EMoCA survey ALMA data, calibration and deconvolution  
  > "Details about the calibration and deconvolution of the data are reported in Belloche et al. (2016)." (2. Observations) [from Belloche et al. 2016]
- External data: Mopra 3 mm imaging survey of Sgr B2  
  > "3 mm imaging spectral survey of Sgr B2 performed by Jones et al. (2008)" (2. Observations) [from Jones et al. (2008)]
- External data: HCO+ abundance 3e-9 relative to H2 for diffuse clouds  
  > "assuming an HCO [+] abundance of 3×10 [−][9] relative to H 2 typical for diffuse clouds (Liszt et al. 2010)" (Table 11) [from Liszt et al. 2010]
- External data: 12C/13C ratios used to derive HCO+ column densities  
  > "assume the same 12 C/ 13 C ratios as Belloche et al. (2013) to derive the HCO + column densities" (4.7 Nature of the detected line-of-sight clouds) [from Belloche et al. (2013)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibration and deconvolution deferred to Belloche et al. (2016)  
  > "Details about the calibration and deconvolution of the data are reported in Belloche et al. (2016)." (2. Observations)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.3″ pixels in continuum map; analysis sampled at 0.6″  
  > "The pixel size in this image is 0. [′′] 3." (Figure 1 caption); "With a sampling of 0.6 [′′], the Nyquist-sampling condition is still fulfilled" (3.1 Selected data sample)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: noise derived from continuum map not corrected for primary beam attenuation; example spectra corrected  
  > "in the continuum map not corrected for primary beam attenuation" (3.1 Selected data sample)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Calibration and deconvolution of the EMoCA data  
  > "Details about the calibration and deconvolution of the data are reported in Belloche et al. (2016)." (2. Observations) [from Belloche et al. (2016)]
- Same 12C/13C ratios as Belloche et al. (2013) for HCO+ column densities  
  > "assume the same 12 C/ 13 C ratios as Belloche et al. (2013) to derive the HCO + column densities" (4.7 Nature of the detected line-of-sight clouds) [from Belloche et al. 2013]
- PDF normalisation of opacity maps  
  > "We use the following normalisation (see, e.g. Schneider et al. 2013)" (3.7 Probability distribution function of the optical depth) [from Schneider et al. 2013]
- Forcing parameter b / turbulence relations  
  > "calculating the forcing parameter b (e.g. Federrath et al. 2010)" (4.5 Turbulence in diffuse and translucent clouds) [from Federrath et al. 2010]

### Not stated but needed to reproduce (our reading)

- Calibrated/imaged EMoCA cubes and continuum map (from Belloche et al. 2016) are required; imaging parameters not given here
- Initial guesses and exact tolerance settings of the automatic MCWeeds fit for reproducing the 2838 components
- Exact ellipses excluded around hot cores N1 and N2
- Baseline fitting (polynomial order, line-free windows) in CLASS
- Primary-beam correction details
- Exact noise-channel selection for tests

## Analysis recipe

1. **select pixels and compute opacity cubes**: Select pixels with continuum >4 RMS and outside ellipses around hot cores; compute tau=-ln(1+Il/Ic); create 1000 noise realisations  
  > "we analyse the absorption features towards positions where the continuum emission is brighter than four times the RMS noise level." (3.1 Selected data sample); "Using this assumption we randomly create 1000 opacity cubes from the original line intensity cube." (3.2 Opacity cubes)
   - software: GILDAS GREG, python
   - parameter: keep pixels with Il <= 3.1 sigma_RMS; opacity set to infinity if -Il >= Ic  
  > "We keep all pixels with I l ≤ 3.1σ RMS ." (3.2 Opacity cubes)
   - assumption: Tex = TCMB = 2.73 K; Gaussian noise  
  > "We assume the excitation temperature to be equal to the temperature of the CMB (2.73 K)" (3.3 Modelling)
   - fitting: _not stated_
   - validation: _not stated_
2. **decompose c-C3H2 absorption into velocity components**: Automatic fitting of Weeds synthetic spectra with Gaussian opacity components per pixel using MCWeeds and Powell minimisation; fitted N_tot, FWHM, v0  
  > "we use the fitting routine MCWeeds (Giannetti et al. 2017), which combines the python package PyMC2 (Patil et al. 2010) and Weeds (Maret et al. 2011)." (3.3 Modelling); "We use a modified version of this method ( fmin_powell from scipy 3 ) with MCWeeds." (3.4 Minimisation method)
   - software: Weeds, MCWeeds, PyMC2, scipy, GILDAS CLASS
   - parameter: detect dips >4 sigma; four velocity ranges; velocity prior uniform ±3 km/s; FWHM max 30 km/s  
  > "Search in the continuum-subtracted spectrum for absorption dips with a peak signal-to-noise ratio higher than 4" (Appendix B)
   - assumption: LTE, beam filling factor 1  
  > "This means that our assumption of a beam filling factor of 1 to fit the spectra is reasonable." (5.4 Cloud sizes)
   - fitting: Powell local minimisation, MCWeeds priors: uniform velocity, truncated normal FWHM, normal log N width 2  
  > "the probability distribution for the velocity is uniform over the chosen interval" (Appendix B)
   - validation: residual peaks above 5 sigma then 4 sigma searched for missing components  
  > "The programme looks for peaks above a threshold of 5σ in the residuals." (Appendix B)
3. **two-point auto-correlation of opacity maps**: Compute C(r) averaged over pixel pairs for 1000 realisations; mean and dispersion as estimate/uncertainty; significance thresholds from noise channels  
  > "We take the average of the 1000 two-point auto-correlation functions as the best estimate and their dispersion as the uncertainty." (3.6 Two-point auto-correlation of opacity maps)
   - software: python
   - parameter: at least 50 pixel pairs per bin  
  > "is only determined if at least 50 pairs of pixels are available" (3.6 Two-point auto-correlation of opacity maps)
   - fitting: _not stated_
   - validation: noise channels: significant only if SNR>5 for r<6″ and >4 beyond  
  > "higher than 5 for r < 6 [′′] and higher than 4 beyond 6 [′′]" (Appendix C.1)
4. **PDF width and turbulence forcing**: Compute PDF of eta=ln(tau/mean tau) in 0.1 bins; width as direct standard deviation; Mach number from FWHM; derive b and zeta from sigma_s^2=f^2 sigma_eta^2=ln(1+b^2M^2)  
  > "we measure the width of each PDF by directly calculating its standard deviation, excluding the noise tail towards lower values of η." (4.5 Turbulence in diffuse and translucent clouds)
   - software: python
   - parameter: Tkin assumed 20, 40, 80 K; mean molecular weight 2.37; pixels above 3 sigma  
  > "Here, we assume temperatures of 20, 40, and 80 K." (4.5 Turbulence in diffuse and translucent clouds)
   - assumption: thermal linewidth neglected; f linear interpolation between 2.0 and 2.9  
  > "f = 2.9 × ζ + (1−ζ)×2.0" (4.5 Turbulence in diffuse and translucent clouds)
   - fitting: Gaussian fit to log-PDF (only when peak counts >10 and <10% infinite pixels)  
  > "The fit is only performed if the number of counts per log-bin at the peak of the PDF is higher than 10" (3.7 Probability distribution function of the optical depth)
   - validation: noise-tail masking tested; reduced molecule sub-sample compared  
  > "the two categories of velocity components still have mean PDF widths that differ, with values of 0.43 (Category I) and 0.50 (Category II)." (4.5 Turbulence in diffuse and translucent clouds)
5. **principal component analysis of opacity maps**: Normalise each molecule's opacity array, PCA with scikit-learn; uncertainties from 1000 realisations aligned with orthogonal procrustes rotation  
  > "the PCA is performed with the Python package scikit-learn (Pedregosa et al. 2011)" (3.8 Principal component analysis)
   - software: scikit-learn, scipy.linalg
   - parameter: peak SNR>=10 and at least 125 pixels with SNR>5; at least four molecules  
  > "The peak signal-to-noise ratio must be at least 10 and there must be at least 125 pixels" (3.8 Principal component analysis)
   - fitting: _not stated_
   - validation: noise-channel PCA and robustness tests on grid size, pixel and molecule selection  
  > "Altogether the PCA seems to be robust to all these tests for the velocity component at 24.7 km s [−][1]" (Appendix D)
6. **determine cloud nature (H2, Av, density)**: Fit HCO+/H13CO+ absorption towards K4 with Weeds; N(H2) from HCO+ abundance 3e-9; Av=N(H2)/9.4e20; test against Mopra emission with RADEX non-LTE grids  
  > "We perform non-LTE radiative transfer calculations with RADEX (van der Tak et al. 2007) to estimate the densities and kinetic temperatures" (4.7 Nature of the detected line-of-sight clouds)
   - software: Weeds, RADEX
   - parameter: Tkin 10–130 K, nH2 10–1e7 cm-3; Mopra Tmb = 1.7 × TA*  
  > "10–130 K for the kinetic temperature and 10–10 [7] cm [−][3] for the H 2 density" (4.7 Nature of the detected line-of-sight clouds)
   - assumption: HCO+ abundance 3e-9 (diffuse), 2e-8 for N>9.4e13, log-interpolated between  
  > "2 × 10 [−][8] for N(HCO [+] ) > 9.4 × 10 [13] cm [−][2], and an interpolated value (in log-log space) in between." (Table 11)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **GILDAS (GREG, CLASS)** : noise estimation (go noise) and baseline subtraction  
  > "we use the command go noise in the GILDAS package GREG" (3.1 Selected data sample)
- **Weeds** : synthetic LTE absorption spectra  
  > "We model the spectra with Weeds (Maret et al. 2011)" (3.3 Modelling)
- **MCWeeds** : automatic fitting of spectra  
  > "we use the fitting routine MCWeeds (Giannetti et al. 2017)" (3.3 Modelling)
- **PyMC2** : MCMC component of MCWeeds  
  > "combines the python package PyMC2 (Patil et al. 2010) and Weeds" (3.3 Modelling)
- **scipy** : Powell minimisation and procrustes rotation  
  > "fmin_powell from scipy" (3.4 Minimisation method)
- **scikit-learn** : PCA  
  > "the PCA is performed with the Python package scikit-learn" (3.8 Principal component analysis)
- **RADEX** : non-LTE modelling of Mopra emission  
  > "non-LTE radiative transfer calculations with RADEX (van der Tak et al. 2007)" (4.7 Nature of the detected line-of-sight clouds)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Velocity components detected in c-C3H2 across 322 positions | 2838 | not stated | components | 2 | In total, 2838 velocity components are detected towards the 322 selected positions. |
| Median FWHM Category I | 5.4 | not stated | km/s | 2 | Category I has a median linewidth of 5.4 km s [−][1] . |
| Median FWHM Category II | 7.5 | not stated | km/s | 2 | have a somewhat larger median linewidth of 7.5 km s [−][1] . |
| Mean PDF width, all molecules and components | 0.53 (median 0.52) | not stated | dimensionless | 4 | with values of 0.52 and 0.53 for the total distribution, respectively. |
| Mean PDF width Category I vs II | 0.48 vs 0.56 | not stated | dimensionless | 4 | Category I has a mean width of 0.48, somewhat smaller than Category II (0.56). |
| Mach number range | 5.8–28.3 (20 K), 2.9–14.2 (80 K) | not stated | dimensionless | 4 | We obtain Mach number values between 5.8 and 28.3 for T kin = 20 K and between 2.9 and 14.2 for 80 K. |
| Median forcing parameter b (Tkin=40 K) | 0.26 | not stated | dimensionless | 4 | The median value of the forcing parameter b is 0.26 |
| H2 column densities from HCO+ | 3.3e20 to 9.0e22 | not stated | cm-2 | 6 | We obtain H 2 column densities ranging from 3.3 × 10 [20] to 9.0 × 10 [22] cm [−][2] |
| 12C/13C ratio of GC clouds from CN | 20 | ±3 | dimensionless | 0 | derived isotopic ratios of 1312 CC [=] 20±3 for these clouds |
| PC1 power at 24.7 km/s | 72.9 | not stated | percent | 5 | 73% of the total variance in the data is described by the first principal component. |

## Qualitative findings

- Most molecules trace homogeneous structures more extended than the ~15″ field of view; SO and SiO show clumps of ~5–8″  
  > "SO and SiO show more complex structures with smaller clumps of size ∼5–8 [′′] ." (abstract)
- HCO+ abundance is higher in translucent than diffuse clouds, so HCO+ is a poor H2 tracer there; CCH and CH are good tracers, c-C3H2 is not  
  > "We further find that CCH and CH are good probes of H 2 in translucent clouds, but that c-C 3 H 2 is not." (6. Conclusions)

## Claim tuples

- H: Line-of-sight clouds fall into distinct categories | E: Decomposed c-C3H2 absorption into components and compared column densities, linewidths and PDF widths | R: Category I has lower column density, FWHM 5.4 vs 7.5 km/s, PDF width 0.48 vs 0.56 | F: Two categories of clouds exist | **supported**
- H: Turbulence driving is solenoidal or compressive | E: Compared PDF widths and derived b with simulations of Federrath et al. | R: Mean width 0.52 vs 0.46 (solenoidal); b<0.5 for all components | F: Driving mainly solenoidal | **supported**
- H: Clouds are diffuse, translucent or dense | E: HCO+ column densities to H2 and Av; Mopra emission with RADEX densities | R: Densities <~1e3–5e3 cm-3 and Av mostly 1–5 mag with variable HCO+ abundance | F: Most clouds are translucent, including those with COMs | **supported**
- H: Clouds have sub-structure at ALMA resolution | E: Two-point auto-correlation of opacity maps | R: Most structures extended ≥15″; small structures mostly noise-limited except SO, SiO | F: Relatively homogeneous clouds | **partially**

## Reasoning

- Why this data: EMoCA resolves continuum of Sgr B2(N), allowing spatially resolved absorption  
  > "The angular resolution of this survey is high enough to resolve the continuum emission of Sgr B2(N) (see Fig. 1)." (1. Introduction)
- Why this method: Powell minimisation chosen for many free parameters  
  > "A good method to deal with a large number of free parameters is the Powell minimisation method" (3.4 Minimisation method)
- Alternative: Two-Gaussian decomposition of PDFs rejected in favour of direct standard deviation  
  > "to avoid being biased by the decomposition of the PDFs into two Gaussians, in the following we measure the width of each PDF by directly calculating its standard deviation" (4.5 Turbulence in diffuse and translucent clouds)
- How they decided it was enough: _not stated_
- Limitation (authors): Field of view limited by background continuum and finite resolution; ACA combination would help  
  > "the limited size of the continuum background emission, which results from the spatial filtering of the interferometer, and the finite angular resolution." (6. Conclusions)
- Limitation (authors): PDF width likely underestimated due to limited field of view  
  > "Hence, the width of their PDFs is likely underestimated." (5.5 Turbulence)
- Caveat (inferred, ours): Kinetic temperature unconstrained, so Mach number and b depend on assumed 20/40/80 K
- Caveat (inferred, ours): Overlapping velocity components may bias linewidths and column densities
- Caveat (inferred, ours): HCO+ abundance profile is assumed and interpolated, not measured
- Caveat (inferred, ours): Local-minimum Powell fits depend on initial guesses of a custom code
- Caveat (inferred, ours): Distances to arms are approximate

## Reproducibility

- Data public (paper): Interferometric data available in the ALMA archive  
  > "The interferometric data are available in the ALMA archive at https://almascience.eso.org/aq/." (Acknowledgements)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Calibrated EMoCA cubes and imaging parameters (in Belloche et al. 2016)
- Missing: Custom fitting programme not released
- Missing: Hot-core exclusion ellipses
- Missing: Version numbers of software
- Data volume (inferred): Large: EMoCA 3 mm survey cubes, hundreds of GB raw; tens of GB for relevant cubes
- Score (inferred): 3/5, Methods and algorithms are described in detail with appendices, data are public, but processing is deferred to prior work and custom code is not released.
- Rediscovery candidate: no, Depends on prior calibrated cubes and an unreleased automated fitting code with many unstated settings.

## Links

- Method: Belloche et al. 2016 (EMoCA survey, calibration and deconvolution)
- Method: Giannetti et al. 2017 (MCWeeds fitting routine)
- Method: Maret et al. 2011 (Weeds radiative transfer)
- Method: Federrath et al. 2010 (turbulence forcing relations)
- Companion: Thiel et al. 2017 (complex organic molecules detected in absorption in same survey)
- Related: EMoCA (Exploring Molecular Complexity with ALMA)
- Related: Mopra 3 mm survey (Jones et al. 2008)

## Checks

```json
{
 "quotes": 87,
 "quotes_ok": 87,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 93,
  "stated": 58,
  "rate": 0.624
 },
 "evidence_ok": true
}
```
