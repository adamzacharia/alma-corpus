# Exploring the formation pathways of formamide. Near young O-type stars

`2020A&A...636A..67A` | Astronomy and Astrophysics 2020 | first author: Allen, V. | arXiv: 1912.12347 | DOI: 10.1051/0004-6361/201935791

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry
- Question: Is formamide (NH2CHO) chemically related to HNCO and/or H2CO, as tested by comparing moment maps and LTE-modelled abundances in three high-mass star-forming regions?  
  > "We aim to find empirical evidence to support the chemical relationships of formamide to HNCO and H$_2$CO." (abstract)
- Target **G17.64+0.16 (G17)**: coordinates 18:22:26.370 -13:30:12.06 (J2000, spectral extraction point)  
  > "is located at a distance of 2.2 kpc, has a bolometric luminosity of 1 $\times 10^{5}$ L$_{\odot}$" (2.1 Source sample); z/distance 2.2 kpc  
  > "is located at a distance of 2.2 kpc, has a bolometric luminosity of 1 $\times 10^{5}$ L$_{\odot}$" (2.1 Source sample); distance from RMS database  
  > "is located at a distance of 2.2 kpc, has a bolometric luminosity of 1 $\times 10^{5}$ L$_{\odot}$" (2.1 Source sample)
- Target **G24.78+0.08 (G24: A1, A2(N), A2(S))**: coordinates A1 18:36:12.544 -07:12:11.14 (J2000, spectral extraction point)  
  > "is located at a distance of 6.7 kpc (cite: Reid2019), determined by trigonametric parallax" (2.1 Source sample); z/distance 6.7 kpc  
  > "is located at a distance of 6.7 kpc (cite: Reid2019), determined by trigonametric parallax" (2.1 Source sample); distance from Reid et al. 2019, trigonometric parallax  
  > "is located at a distance of 6.7 kpc (cite: Reid2019), determined by trigonametric parallax" (2.1 Source sample)
- Target **G345.49+1.47 (G345: Main, NW spur)**: coordinates Main 16:59:41.628 -40:03:43.63 (J2000, spectral extraction point)  
  > "is located at a distance of 2.4 kpc with a bolometric luminosity of 1.5 $\times 10^{5}$ L$_{\odot}$" (2.1 Source sample); z/distance 2.4 kpc  
  > "is located at a distance of 2.4 kpc with a bolometric luminosity of 1.5 $\times 10^{5}$ L$_{\odot}$" (2.1 Source sample); distance from RMS database  
  > "is located at a distance of 2.4 kpc with a bolometric luminosity of 1.5 $\times 10^{5}$ L$_{\odot}$" (2.1 Source sample)

## Data provenance

- ALMA projects: 2013.1.00489.S
- bands: Band 6  
  > "in Band 6 with baselines from 40 to 1500 m" (2.2 Observations)
- frequencies and spectral setup: 216.9-236.5 GHz in 13 spectral windows; 488.3 kHz resolution in most windows (244.1 kHz at 220.303-220.767 GHz, 1953.1 kHz at ~216.976-218.849 GHz)  
  > "The observed frequency range was between 216.9 GHz to 236.5 GHz divided into 13 spectral windows." (2.2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 40 to 1500 m  
  > "in Band 6 with baselines from 40 to 1500 m" (2.2 Observations)
- angular resolution: ~0.2''  
  > "The angular resolution is about 0.2$''$" (2.2 Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.2-1.0 mJy/beam  
  > "The rms noise of the continuum maps ranges between 0.2 and 1.0 mJy beam$^{-1}$." (2.2 Observations)
- time on source: _not stated_
- observing dates: July and September 2015 (Cycle 2)  
  > "observed with ALMA in Cycle 2 in July and September 2015" (2.2 Observations)
- pi or archival as stated: P.I. Riccardo Cesaroni  
  > "ADS/JAO.ALMA 2013.1.00489.S (P.I. Riccardo Cesaroni)" (Acknowledgements)
- Line: HNCO 10(0,10)-9(0,9) [HNCO (1)] (219798.27 MHz)
- Line: HNCO 10(1,9)-9(1,8) [HNCO (2)] (220584.75 MHz)
- Line: HNCO 10(3,7)-9(3,6) [HNCO (3)] (219656.77 MHz)
- Line: NH2CHO 10(1,9)-9(1,8) (218459.21 MHz)
- Line: NH2CHO 11(2,10)-10(2,9) (232273.64 MHz)
- Line: H2CO 3(0,3)-2(0,2) (218222.19 MHz)
- Line: H2CO 3(2,2)-2(2,1) (218475.63 MHz)
- Line: H2CO 3(2,1)-2(2,0) (218760.07 MHz)
- Other facility **RMS survey database**: Distances and bolometric luminosities  
  > "Distance and luminosity values from the RMS database (cite: RMS)" (Table 1)
- External data: Free-free corrected continuum: direct H30alpha-based measurements for G17  
  > "direct measurements for G17 from (cite: Maud2018), G24 A1 from (cite: Moscadelli2018)" (2.2 Observations) [from (cite: Maud2018); (cite: Moscadelli2018)]
- External data: G345 free-free emission calculated from spectral index  
  > "calculated for G345 using the spectral index fit from (cite: Guzman2016)" (2.2 Observations) [from (cite: Guzman2016)]
- External data: G24 distance and Lbol  
  > "except distance and L$_{bol}$ for G24.78+0.08 which is from (cite: Reid2019)" (Table 1) [from (cite: Reid2019)]
- External data: Previous HNCO-NH2CHO abundance relation X(NH2CHO)=0.04 X(HNCO)^0.93  
  > "the best power-law fit was *X*(NH$_2$CHO) = 0.04 *X*(HNCO)$^{0.93}$" (5.2 XCLASS analysis) [from (cite: Ana2015)]

## Processing

### Calibration

- pipeline or manual: calibration and imaging in CASA; details deferred to Cesaroni et al. 2017  
  > "The calibration and imaging were carried out using CASA" (2.2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan and Ceres  
  > "The flux calibrators were Titan and Ceres" (2.2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: STATCONT statistical method, because few line-free channels  
  > "A statistical method (cite: Alvaro2018) was used within the Python-based tool STATCONT[^2] for continuum subtraction as there were very few line free channels." (2.2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observation, calibration and continuum subtraction details  
  > "For full details on observations and continuum subtraction see (cite: Cesaroni2017)." (2.2 Observations) [from (cite: Cesaroni2017)]
- H2 core column density method  
  > "N$_{core}$ was determined as in (cite: Alvaro2014) using the continuum intensity at the spectral extraction point" (Table 2 notes) [from (cite: Alvaro2014)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (robust, cell, image size, deconvolver, CLEAN threshold)
- CASA version
- Moment map clipping thresholds and velocity ranges
- XCLASS version, source sizes and MCMC settings
- Beam-matching or smoothing before differencing moment maps
- Line-free channels used for STATCONT

## Analysis recipe

1. **Extract spectra and model with LTE**: Extract spectra at NH2CHO peak pixels from continuum-subtracted images; fit NH2CHO, HNCO, H2CO and potential blenders (C2H5OH, CH3CN v8=1, CH3(18)OH) simultaneously in XCLASS  
  > "performing simultaneous fits of the species NH$_2$CHO, HNCO, H$_2$CO, and species that were potentially blended with NH$_2$CHO" (2.3 Line identification)
   - software: CASA, XCLASS
   - parameter: Tex 50-300 K for HNCO and NH2CHO, 70-400 K for H2CO; FWHM and vLSR constrained by Gaussian fits, vLSR free within ±0.5 km/s  
  > "The $T_\mathrm{ex}$ free parameter was allowed to vary between 50 and 300 K for HNCO and NH$_2$CHO and between 70 and 400 K for H$_2$CO." (2.3 Line identification)
   - assumption: LTE; H2CO modeled with source size ~0.15'' below beam  
  > "The temperature of H$_2$CO was modeled using higher temperatures and a source size smaller than the beam size ($\sim0.15''$)" (2.3 Line identification)
   - assumption: N(H2) from continuum with Tdust=100 K, kappa=1.0 cm2/g, gas-to-dust 100  
  > "assuming a T$_{dust}$ of 100 K, a dust opacity of 1.0 cm$^2$ g$^{-1}$ (cite: Ossenkopf1994), and a gas-to-dust ratio of 100" (Table 2 notes)
   - fitting: XCLASS errorestim_ins MCMC for errors  
  > "The errors shown were determined using the *errorestim$\_$ins* algorithm using the Markov chain Monte Carlo (MCMC) method built into the XCLASS software." (3.4)
   - validation: Blending checked with ethanol comparison line at 217803.69 MHz  
  > "the peak integrated emission of NH$_2$CHO (1) is $\sim$8 times stronger than that of C$_2$H$_5$OH" (2.3 Line identification)
2. **Compare moment-0 peak positions and extent**: Locate emission peaks with 2D Gaussian fits and measure peak separations between NH2CHO and HNCO/H2CO  
  > "we locate the peak of line emission to high accuracy with a 2D-Gaussian fit accuracy to 0.01$''$" (3)
   - software: CASA
   - assumption: Species with same peak, velocity and line width are in the same gas and related  
  > "if two species peak in the same location, and have the same velocity and line width, then they are in the same gas" (3)
   - fitting: _not stated_
   - validation: RADEX optical depths estimated: H2CO 33-430, HNCO 0.4-69  
  > "the optical depths for the H$_2$CO lines range from 33-430 while those for HNCO lines are much lower ranging from 0.4-69" (3)
3. **Compare velocity fields and dispersions**: Subtract moment-1 and moment-2 maps between species; histogram absolute differences and use mean and standard deviation; same-species transition pairs give an internal error  
  > "The average value and standard deviation of these histograms were used to determine which species was most similar to NH$_2$CHO." (3.2)
   - fitting: _not stated_
   - validation: Internal error from two transitions of the same species  
  > "two transitions from the same species were also compared to determine the "internal error"" (3.2)
4. **Correlate abundances**: Divide modeled Ncol by core N(H2); fit power laws between species pairs  
  > "Modeled $N_\mathrm{col}$ values were divided by the H$_2$ column densities listed in Table [2](#spectrapoints) to obtain abundances for comparison" (3.4)
   - software: XCLASS
   - fitting: Power-law fits with R^2  
  > "The fit for NH$_2$CHO vs. HNCO is \[*X*(NH$_2$CHO)=0.06 *X*(HNCO)$^{0.95}$\] (R$^2$=0.93)." (3.4)
   - validation: Compared with Lopez-Sepulcre et al. 2015 relation  
  > "the relationship between the abundances of HNCO and NH$_2$CHO in this work is almost exactly the same as that reported in (cite: Ana2015)" (5.2 XCLASS analysis)

## Software

- **CASA** : calibration, imaging, spectral extraction  
  > "The calibration and imaging were carried out using CASA" (2.2 Observations)
- **STATCONT** : continuum subtraction  
  > "A statistical method (cite: Alvaro2018) was used within the Python-based tool STATCONT" (2.2 Observations)
- **XCLASS** : LTE spectral modeling and MCMC error estimation  
  > "via the XCLASS[^4] software (cite: XCLASS) assuming local thermal equilibrium (LTE)" (2.3 Line identification)
- **RADEX** : optical depth estimates  
  > "Using RADEX (cite: RADEX), a one dimensional non-LTE radiative transfer code, we have determined that the optical depths" (3)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| X(NH2CHO) vs X(HNCO) power-law fit | X(NH2CHO)=0.06 X(HNCO)^0.95 | 0.06±0.03; exponent ±0.05 | dimensionless | 4 | *X*(NH$_2$CHO)=0.06($\pm$0.03) *X*(HNCO)$^{0.95 (\pm0.05)}$ |
| X(NH2CHO) vs X(H2CO) fit | X(NH2CHO)=0.618 X(H2CO)^1.103, R^2=0.943 | not stated | dimensionless | 4 | The fit for NH$_2$CHO vs. H$_2$CO is \[*X*(NH$_2$CHO)=0.618 *X*(H$_2$CO)$^{1.103}$\] |
| X(HNCO) vs X(H2CO) fit | X(HNCO)=4.796 X(H2CO)^1.111, R^2=0.936 | not stated | dimensionless | 4 | *X*(HNCO)=4.796 *X*(H$_2$CO)$^{1.111}$\] (R$^2$=0.936) |
| Tex range of NH2CHO | 50-150 | not stated | K | 1 | The $T_\mathrm{ex}$ range for NH$_2$CHO is 50-150 K |
| H2CO optical depths | 33-430 | not stated | dimensionless | 2 | the optical depths for the H$_2$CO lines range from 33-430 |

## Qualitative findings

- HNCO emission peaks are closer to NH2CHO than H2CO peaks, and H2CO is much more extended  
  > "it is clear that the integrated emission peaks of HNCO are closer to the peaks of NH$_2$CHO than the H$_2$CO peaks." (3.1.4)

## Claim tuples

- H: NH2CHO is spatially and kinematically more related to HNCO than to H2CO | E: Moment-0, 1 and 2 map comparisons in six subsources | R: Peaks and dispersions mostly favor HNCO; velocity fields split equally | F: HNCO has a slightly stronger relationship with NH2CHO | **partially**
- H: Abundances of NH2CHO correlate with HNCO and H2CO | E: XCLASS LTE abundances and power-law fits | R: All pairs R^2>0.93; HNCO relation matches Lopez-Sepulcre et al. 2015 | F: Abundance correlation is not a good indicator of direct chemical relationship | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): H2CO opacity may cause the differences in distribution and kinematics  
  > "It is possible that the greater differences in spatial distribution, velocity, and dispersion between H$_2$CO and NH$_2$CHO compared to HNCO arise from optical depth issues." (5.1)
- Caveat (inferred, ours): Only 2-3 transitions per species; LTE single-pixel fits with H2CO optically thick
- Caveat (inferred, ours): Only six subsources, so abundance correlations are not independent tests
- Caveat (inferred, ours): Similarity metric lacks formal significance threshold

## Reproducibility

- Data public (paper): ALMA project 2013.1.00489.S cited with PI named; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA 2013.1.00489.S (P.I. Riccardo Cesaroni)." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: XCLASS configuration files and versions
- Missing: Moment map thresholds
- Data volume (inferred): ~50-200 GB raw (13 spws, three fields, Band 6)
- Score (inferred): 5/5, Data public and methods outlined, but imaging and moment settings are missing and deferred to earlier work.
- Rediscovery candidate: no, Key processing parameters are missing, and the result is partly qualitative comparison of moment maps.

## Links

- Method: (cite: Alvaro2018) (STATCONT continuum subtraction)
- Method: (cite: XCLASS) (LTE modeling software)
- Companion: (cite: Cesaroni2017) (Source paper for the observations, calibration and continuum subtraction)
- Companion: (cite: Allen) (Earlier HNCO/NH2CHO study of G35.20-0.74N)
- Related: Red MSX Source survey

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
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 48,
  "rate": 0.615
 },
 "evidence_ok": true
}
```
