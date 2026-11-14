# The Massive Protostellar Cluster NGC 6334I at 220 au Resolution: Discovery of Further Multiplicity, Diversity, and a Hot Multi-core

`2016ApJ...832..187B` | The Astrophysical Journal 2016 | first author: Brogan, C. L. | arXiv: 1609.07470 | DOI: 10.3847/0004-637X/832/2/187

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What is the multiplicity, nature and SED of the sources in the massive protocluster NGC6334I at ~220 AU resolution from 5 cm to 1.3 mm?  
  > "In this paper, we present sub-arcsecond, comparable-resolution continuum imaging of NGC6334I from 5 cm to 1.3 mm using the Karl G. Jansky Very Large Array (VLA) and the Atacama Large Millimeter/submillimeter Array (ALMA)." (1 Introduction)
- Target **NGC6334I**: coordinates MM1 17:20:53.415 -35:46:57.88 (J2000)  
  > "For the distance to NGC6334I, we adopt 1.3 kpc based on recent H$_2$O and CH$_3$OH maser parallax studies toward source I(N)" (1 Introduction); z/distance 1.3 kpc  
  > "For the distance to NGC6334I, we adopt 1.3 kpc based on recent H$_2$O and CH$_3$OH maser parallax studies toward source I(N)" (1 Introduction); distance from maser parallax of source I(N) (Reid14; Wu14; Chibueze14)  
  > "For the distance to NGC6334I, we adopt 1.3 kpc based on recent H$_2$O and CH$_3$OH maser parallax studies toward source I(N)" (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.00600.S
- bands: ALMA 3 mm and 1.3 mm (Cycle 2); VLA 5 cm, 1.5 cm, 7 mm  
  > "We also observed this source using ALMA in Cycle 2 at 3 mm and 1.3 mm." (2.1 New VLA and ALMA Observations)
- frequencies and spectral setup: 3 mm: 4 spws, basebands 90.5, 92.4, 102.5, 104.5 GHz; 1.3 mm: 7 spws, 220.8, 223.0, 237.24, 238.76 GHz  
  > "Baseband Frequencies (GHz) | 5.0, 7.0 | 19.5, 20.6 | 43.25, 45.00 (40.44, 42.76)$^{a}$ | 90.5, 92.4, 102.5, 104.5 | 220.8, 223.0, 237.24, 238.76" (Table 1)
- continuum bandwidth: 4.6 GHz (3 mm); 0.4 GHz (1.3 mm)  
  > "Continuum bandwidth (GHz) | 1.8 | 1.7 | 1.7 | 4.6 | 0.4" (Table 1)
- arrays: _not stated_
- configurations: ALMA C32-6 at both bands  
  > "Configuration(s) | A | BnA | B, B, BnA | C32-6 | C32-6" (Table 1)
- baselines: 12-508 kλ (3 mm); 11-1140 kλ (1.3 mm)  
  > "Proj. baseline lengths (k$\lambda$) | 7 - 671 | 10 - 872 | 13 - 1600 (1310)$^{b}$ | 12 - 508 | 11 - 1140" (Table 1)
- angular resolution: 0.51x0.35 arcsec (3 mm); 0.20x0.15 arcsec (1.3 mm)  
  > "$0.51\times 0.35$ ($+66$) | $0.20\times 0.15$ ($-80$)" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: rms 0.5 mJy/beam (3 mm); 1.2 mJy/beam (1.3 mm)  
  > "rms noise (mJy beam$^{-1}$)$^{c}$ | 0.04 | 0.06 | 0.07 | 0.5 | 1.2" (Table 1)
- time on source: 3 mm 7.3 min; 1.3 mm 49.3 min  
  > "Total time on source (min) | 83.8 | 66.1 | 257.7 | 7.3 | 49.3" (Table 1)
- observing dates: 3 mm 2015 Aug 11; 1.3 mm 2015 Aug 29  
  > "Observation date(s) | 2011 Jul 07 | 2011 May 29 | 2011 Feb 12, Mar 25, May 20 | 2015 Aug 11 | 2015 Aug 29" (Table 1)
- pi or archival as stated: _not stated_
- Other facility **VLA**: 5 cm, 1.5 cm, 7 mm continuum, CH3OH masers, archival 22 GHz H2O maser data  
  > "We observed NGC6334I using the VLA at three wavelengths: 5 cm, 1.5 cm, and 7 mm." (2.1 New VLA and ALMA Observations)
- External data: SMA 1.3 mm total integrated intensity 10.7±0.1 Jy at 1.6'' resolution  
  > "The total 1.3 mm integrated intensity reported by (cite: Hunter06) for NGC6334I using $1.6''$ resolution SMA data is $10.7\pm 0.1$ Jy." (4.1 Fitted Properties) [from (cite: Hunter06)]

## Processing

### Calibration

- pipeline or manual: ALMA calibration pipeline; VLA scripted pipeline; archival water maser data manually processed  
  > "The ALMA data were calibrated using the CASA 4.3.1 version of the ALMA calibration pipeline." (2.1 New VLA and ALMA Observations)
- casa version: CASA 4.3.1 (calibration); CASA 4.6.0 (imaging)  
  > "The continuum data for all bands were imaged in CASA 4.6.0 using multi-frequency synthesis" (2.1 New VLA and ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 1.3 mm: Titan; 3 mm: Ceres, recalibrated using J1733-1304 monitored flux  
  > "The absolute flux calibrator for the 3 mm data was Ceres, and in this case we found that the derived flux density of J1733-1304 was too high by $\sim 12\%$" (2.1 New VLA and ALMA Observations)
- flux scale uncertainty: ~10% for ALMA  
  > "there is still an overall absolute flux uncertainty of $\sim 10\%$ for the ALMA data." (2.1 New VLA and ALMA Observations)
- self calibration: Iterative self-calibration on bright continuum emission  
  > "The data were iteratively self-calibrated, using the bright continuum emission." (2.1 New VLA and ALMA Observations)

### Imaging

- task: CASA 4.6.0, multi-frequency synthesis with nterms=2  
  > "imaged in CASA 4.6.0 using multi-frequency synthesis and *nterms=2*" (2.1 New VLA and ALMA Observations)
- deconvolver: Multi-scale clean  
  > "Multi-scale clean was also employed with scales 0, 5, and 15 times the image pixel size" (2.1 New VLA and ALMA Observations)
- weighting robust: robust = -1.0 for both ALMA bands  
  > "Robust clean parameter | -1.0 | 0.0 | 0.0 | -1.0 | -1.0" (Table 1)
- uv taper: _not stated_
- cell size: typically 1/5 of the synthesized beam  
  > "(typically 1/5 of the synthesized beam)" (2.1 New VLA and ALMA Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: 0, 5, 15 pixels  
  > "Multi-scale clean was also employed with scales 0, 5, and 15 times the image pixel size" (2.1 New VLA and ALMA Observations)
- continuum subtraction: Line-free channels identified from dirty cubes  
  > "we first made dirty cubes containing both the line and continuum emission of each spectral window (spw), and used these cubes to carefully identify line-free channels" (2.1 New VLA and ALMA Observations)
- line free channels: _not stated_
- primary beam correction: applied to final images  
  > "The final images were corrected for primary beam attenuation" (2.1 New VLA and ALMA Observations)
- array combination: _not stated_
- smoothing: 1.3 mm image convolved to the 3 mm beam for spectral index map  
  > "(the 1.3 mm image was first convolved to the 3 mm beam)" (3.1 Continuum Emission)
- final beam: 0.20x0.15 arcsec PA -80 (1.3 mm)  
  > "$0.51\times 0.35$ ($+66$) | $0.20\times 0.15$ ($-80$)" (Table 1)
- final rms: _not stated_

### Inherited from earlier work

- Gas mass equation approach  
  > "Similar to (cite: Brogan09) and (cite: Hunter14), we estimated dust-derived gas masses" (5.1 SEDs) [from (cite: Brogan09); (cite: Hunter14)]
- Greybody SED function  
  > "we fit the SED of each of these sources with a modified greybody function (cite: Rathborne10)" (5.1 SEDs) [from (cite: Rathborne10)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges and threshold per spw
- Image sizes, clean thresholds and masks
- Self-calibration solution intervals
- Greybody fit code and frequency/flux inputs details
- Initial guesses for Gaussian fits and fitting software
- Details of the rms measurement regions

## Analysis recipe

1. **Continuum imaging**: Line-free continuum imaging with MTMFS and multiscale clean, self-cal, primary-beam correction  
  > "The continuum data for all bands were imaged in CASA 4.6.0 using multi-frequency synthesis and *nterms=2*" (2.1 New VLA and ALMA Observations)
   - software: CASA
   - parameter: robust -1.0; scales 0,5,15 pixels  
  > "Robust clean parameter | -1.0 | 0.0 | 0.0 | -1.0 | -1.0" (Table 1)
   - fitting: _not stated_
   - validation: Residual line contamination of MM1/MM2 <5% from threshold tests  
  > "suffers from residual line contamination of $<5\%$ in flux density for the adopted threshold level" (2.1 New VLA and ALMA Observations)
2. **Spectral index map 3-1.3 mm**: Linear spectral index S∝ν^α from 3 and 1.3 mm images, 1.3 mm convolved to 3 mm beam  
  > "Figure [3](#spix) shows the linear spectral index $\alpha_{mm}$ ( using the equation $S_{\nu}\propto \nu^{\alpha}$) between 3 and 1.3 mm" (3.1 Continuum Emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit Gaussian components to sources**: Multi-step 2D Gaussian decomposition of MM1 (7 components), MM2 core/halo, MM4A/MM6, subtracting components iteratively  
  > "we attempted to decompose the emission into Gaussian components. Since it has the best angular resolution, we first used the 1.3 mm image toward MM1 in a multi-step approach" (4.1 Fitted Properties)
   - parameter: extra 10% (Band 6) and 30% (Band 3) uncertainty added in quadrature for confused sources  
  > "adding an extra $10\%$ and $30\%$ uncertainty (in quadrature) to the formal fitting errors in Band 6 and 3, respectively" (4.1 Fitted Properties)
   - assumption: MM1B 1.3 mm flux extrapolated from 7 mm with spectral index 3.05  
  > "using a spectral index of 3.05" (4.1 Fitted Properties)
   - fitting: Gaussian fits; upper limits 3x local rms  
  > "For non-detections, $3\sigma$ upper limits are given based on local measurements of the rms noise." (4.1 Fitted Properties)
   - validation: Residual image inspected; simultaneous 7-component fits gave elongated ellipsoids so rejected  
  > "Our tempered approach results in a more physically plausible model that is motivated and supported by the longer wavelength images." (4.1 Fitted Properties)
4. **SED modeling**: Free-free model V of Olnon75 (fit r_e) plus modified greybody dust fits with fixed beta=1.7; uncertainties from 1000 Monte Carlo realizations  
  > "The uncertainties on the fitted parameters were obtained by computing the standard deviation of the fitted parameters obtained from fitting an ensemble of 1000 realizations" (5.1 SEDs)
   - parameter: Te=1e4 K; ne = 3e5, 3e6, 3e7 cm-3 for MM1D, MM1B, CM1  
  > "we set $n_e$ to $3\times10^5$, $3\times10^6$, and $3\times10^7$ cm$^{-3}$ for MM1D, MM1B, and CM1, respectively" (5.1 SEDs)
   - assumption: beta=1.7 (MM1D uses 2.4)  
  > "we first chose to use a fixed value of $\beta=1.7$" (5.1 SEDs)
   - fitting: Least squares greybody; sampler/priors not stated  
  > "we fit the SED of each of these sources with a modified greybody function" (Discussion, Spectral Energy Distributions of Continuum Sources)
   - validation: Fitted tau compared with computed tau_dust  
  > "shows that our modeling approach is self-consistent" (5.1 SEDs)
5. **Derive masses, densities, luminosities**: Dust mass equation with opacity correction; brightness temperature in Rayleigh-Jeans limit; Stefan-Boltzmann luminosities  
  > "We assumed a distance of 1.3 kpc and a gas to dust ratio of $R=100$." (5.1 SEDs)
   - assumption: D=1.3 kpc, R=100, kappa_1.3mm=1 cm2/g (Ossenkopf & Henning 1994), spherical geometry  
  > "For the dust opacity coefficient, $\kappa_{1.3mm}$, we used 1 cm$^{2}$g$^{-1}$" (5.1 SEDs)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3.1 (calibration), 4.6.0 (imaging): ALMA calibration pipeline and continuum imaging  
  > "The ALMA data were calibrated using the CASA 4.3.1 version of the ALMA calibration pipeline." (2.1 New VLA and ALMA Observations)
- **Astropy** : general analysis  
  > "Astropy, a community-developed core Python package for Astronomy" (Acknowledgments)
- **APLpy** : plotting  
  > "APLpy, an open-source plotting package for Python" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total 1.3 mm flux of NGC6334I | 13.2 | not stated | Jy | 3 | The ALMA 1.3 mm data with a resolution of $\sim 0.17''$ actually recover more flux, 13.2 Jy, an increase of $23\%$. |
| MM4A brightness temperature | 97 | 5 | K | 5 | / MM4A / 97 (5) / 98$^{+5}_{-6}$ / 5.3$^{+1.6}_{-1.0}$ / 12.1$^{+3.2}_{-1.5}$ |
| MM4A dust temperature | 98 | +5/-6 | K | 4 | / MM4A / 97 (5) / 98$^{+5}_{-6}$ / 5.3$^{+1.6}_{-1.0}$ |
| MM1B 1.3 mm brightness temperature | 254 | 30 | K | 5 | / MM1B / 254 (30) / 442$^{+419}_{-120}$ |
| MM2A-core dust temperature | 152 | +48/-19 | K | 4 | / MM2Acore / 98 (4) / 152$^{+48}_{-19}$ |
| MM2B 7mm-1.3mm spectral index | 1.63 | 0.44 | dimensionless | 4 | The SED of MM2B exhibits a 7 mm-1.3 mm spectral index of $1.63\pm0.44$ |
| MM1 alpha_mm range | 2.6-3.4 | not stated | dimensionless | 2 | MM1 shows considerable variation and structure in $\alpha_{mm}$, varying from 2.6-3.4 |
| MM1B-MM1D projected separation | 440 | not stated | AU | 3 | The close proximity of MM1B and MM1D (440 AU) |
| MM1D beta | 2.4 | not stated | dimensionless | 4 | The fit shown in Fig. [6](#seds1) uses $\beta=2.4$ |

## Qualitative findings

- MM1 resolved into seven components; MM2 into two; five new mm and two new cm sources  
  > "The dominant hot core MM1 is resolved into seven components at 1.3 mm, clustered within a radius of 1000 AU." (abstract)

## Claim tuples

- H: Is MM1 a cluster of centrally heated protostars? | E: Gaussian decomposition of 1.3 mm image, brightness temperature and Stefan-Boltzmann luminosity | R: Four components Tb>200 K, r~300 AU, L>1e4 Lsun | F: MM1 is a hot multi-core with centrally heated protostars | **supported**
- H: Which source drives the CO outflow? | E: Water maser kinematics at MM1D | R: Red/blue maser gradient along outflow axis | F: MM1D is the likely driving source | **partially**
- H: Why do some MM1 SEDs show 7 mm non-detections? | E: Compare dust models, beta, uv coverage and epochs | R: MM1A, MM1C not explained by steep beta | F: Either unusual dust properties or variability | **partially**
- H: Nature of MM4A | E: SED fit, brightness temperature, maser detection | R: Tb 97 K, tau~5, no thermal lines | F: Optically thick 240 Lsun dust core, possibly transient stage | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Calibration errors and mismatched uv-coverage rejected as explanation of strange SEDs  
  > "mismatched uv-coverage leading to different degrees of spatial filtering for example is very unlikely to be an explanation" (5.2.2)
- How they decided it was enough: _not stated_
- Limitation (authors): SEDs lack points near peak so Tdust, tau, beta cannot be constrained simultaneously  
  > "we are unable to accurately constrain $T_{dust}$, the greybody opacity ($\tau_\nu$), and the grain emissivity index ($\beta$) simultaneously" (5.1 SEDs)
- Caveat (inferred, ours): Non-simultaneous VLA (2011) and ALMA (2015) data complicate SEDs
- Caveat (inferred, ours): Fixed beta and constant kappa drive masses
- Caveat (inferred, ours): Gaussian decomposition of confused MM1 may be non-unique
- Caveat (inferred, ours): No time-variability confirmation

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: ALMA data under 2013.1.00600.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00600.S." (Acknowledgments)
- Missing: Gaussian fit initial guesses and code
- Missing: Line-free channel lists
- Missing: Self-calibration parameters
- Missing: Greybody fitting implementation
- Data volume (inferred): ~50-100 GB raw for ALMA bands 3 and 6
- Score (inferred): 6/5, ALMA project code and most settings given, but fitting details and channel selections missing.
- Rediscovery candidate: yes, Data are archival, recipe is mostly described, results (fluxes, sizes, Tb) are numeric.

## Links

- Method: (cite: Hunter14) (similar mass derivation and companion NGC6334I(N) work)
- Companion: (cite: Hunter06) (earlier SMA study of NGC6334I)
- Related: VLA 10C-186

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
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
  "facts": 74,
  "stated": 54,
  "rate": 0.73
 },
 "evidence_ok": true
}
```
