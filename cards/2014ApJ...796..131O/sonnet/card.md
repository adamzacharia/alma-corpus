# Formation of a Keplerian Disk in the Infalling Envelope around L1527 IRS: Transformation from Infalling Motions to Kepler Motions

`2014ApJ...796..131O` | The Astrophysical Journal 2014 | first author: Ohashi, Nagayoshi | arXiv: 1410.0172 | DOI: 10.1088/0004-637X/796/2/131

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: Does the infalling, rotating envelope of the class 0 protostar L1527 IRS show the transition from infall and angular-momentum-conserving rotation to Keplerian rotation, and what do the C18O and SO kinematics say about infall velocities?  
  > "it is still extremely crucial for us to observationally investigate how Keplerian disks are formed around protostars, particularly those in the earliest evolutional stage." (Introduction)
- Target **L1527 IRS**: coordinates RA 4h39m53.9000s, Dec +26d03m10.000s (J2000, coordinate center)  
  > "is located in one of the closest low-mass star forming region, Taurus Molecular Cloud at a distance of about 140 pc" (Introduction); "R.A. (J2000)=4$^{\rm h}$39$^{\rm m}$53$^{\rm s}\!\!$.9000" (Table 1); z/distance about 140 pc  
  > "is located in one of the closest low-mass star forming region, Taurus Molecular Cloud at a distance of about 140 pc" (Introduction); "R.A. (J2000)=4$^{\rm h}$39$^{\rm m}$53$^{\rm s}\!\!$.9000" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00210.S
- bands: 1.3 mm continuum, C18O 2-1, SO 6_5-5_4 (cycle 0)  
  > "ALMA) cycle 0 observations of C$^{18}$O ($J=2-1$), SO ($J _N= 6_5-5_4$) and 1.3 mm dust continuum" (abstract)
- frequencies and spectral setup: SO 219.9494 GHz; C18O 219.5603 GHz; continuum 225.4336 GHz; line velocity resolution 0.17 km/s  
  > "Frequency | 219.9494 GHz | 219.5603 GHz | 225.4336 GHz" (Table 1)
- continuum bandwidth: 94 MHz channel width listed for continuum  
  > "Velocity resolution | 0.17 km$\,$s$^{-1}$ | 0.17 km$\,$s$^{-1}$ | 94 MHz" (Table 1)
- arrays: 25 12-m antennas  
  > "The total number of the 12 m antenna was 25, and the total on-source time was $\sim$37 minutes." (2 Observations)
- configurations: _not stated_
- baselines: 18.0 – 372.5 m projected (text: max 366 m, min 18 m)  
  > "Projected baseline length      | 18.0 – 372.5 m" (Table 1)
- angular resolution: 0.96" x 0.73" in C18O (0.8" geometric mean)  
  > "providing an angular resolution of $0.96\ensuremath{''}\times0.73\ensuremath{''}$ in C$^{18}$O ($0.8\ensuremath{''}$ in geometrical mean)" (2 Observations)
- max recoverable scale: ~9" for 30% level, ~7" for 50% level  
  > "setting the maximum detectable size at $\sim9\ensuremath{''}$ for 30% level detection or $\sim7\ensuremath{''}$ for 50% level detection" (2 Observations)
- sensitivity: C18O 8.0 mJy/beam (0.29 K), SO 9.5 mJy/beam (0.35 K) at 0.17 km/s; continuum ~5.3 mJy  
  > "The rms noise levels (1 $\sigma$) of C$^{18}$O and SO are 8.0 mJy beam$^{-1}$, corresponding to 0.29 K in brightness temperature" (2 Observations)
- time on source: ~37 minutes  
  > "The total number of the 12 m antenna was 25, and the total on-source time was $\sim$37 minutes." (2 Observations)
- observing dates: August 26, 2012  
  > "1.3 mm dust continuum emissions on August 26, 2012." (2 Observations)
- pi or archival as stated: _not stated_
- Line: C18O J=2-1 (219.5603 GHz)
- Line: SO 6_5-5_4 (219.94944 GHz)
- Other facility **Nobeyama 45 m**: C18O 1-0 systemic velocity ~5.7 km/s (literature)  
  > "The systemic velocity of L1527 was measured to be $\sim$5.7 km s$^{-1}$ from C$^{18}$O $J=1-0$ observations using the Nobeyama 45 m single-dish telescope" (Introduction)
- Other facility **SMA**: Previous C18O 2-1 rotation measurements (Yen et al. 2013) used for comparison  
  > "For a comparison purpose, previous measurements of the SMA observations (cite: yen13) were also plotted together." (4.1)
- External data: SMA rotation-velocity measurements of L1527  
  > "For a comparison purpose, previous measurements of the SMA observations (cite: yen13) were also plotted together." (4.1) [from Yen et al. 2013 (cite: yen13)]
- External data: Observed SO 7_6-6_5 and 7_8-6_7 brightness temperatures for LVG (reference 2)  
  > "Observed Brightness Temperature (K) | 6.16$\pm$0.30 | 6.00$\pm$0.15 | 5.64$\pm$0.11" (Table 2) [from not stated (Table 2 reference 2a; likely Sakai et al. 2014 (cite: sakai14))]
- External data: SO energy levels, A-coefficients, frequencies from LAMDA; collisional rates from Lique et al.  
  > "Rotational energy levels, statistical weights, Einstein A-Coefficients, and line frequencies of SO are taken from the LAMDA database(cite: schoier05)." (Appendix) [from (cite: schoier05); (cite: lique07); (cite: lique06)]
- External data: Envelope model and L1527 luminosity 2.75 Lsun  
  > "The model envelope is based on that discussed by (cite: tobin08), who modified the infalling envelope model of (cite: terebey84)" (4.3) [from (cite: tobin08)]
- Simulation/model as data: Model envelope + SO ring + Keplerian disk (Models 1 and 2), line emission by LTE radiative transfer, observed with CASA simulator  
  > "the CASA simulator was used to reproduce the observed line profiles and PV diagrams." (4.3)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto (passband J0522-364, gain J0510+180)  
  > "Flux calibrator                | Callisto" (Table 1)
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
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: C18O/SO 0.96" x 0.73"; continuum 0.93" x 0.70"  
  > "Synthesized beam (P.A.)        | $0.96\ensuremath{''}\times 0.73\ensuremath{''}\ (+10^{\circ })$" (Table 1)
- final rms: C18O 8.0 mJy/beam, SO 9.5 mJy/beam (detected channels)  
  > "9.5 mJy beam$^{-1}$, corresponding to 0.35 K, respectively with the velocity resolution of 0.17 km s$^{-1}$." (2 Observations)

### Inherited from earlier work

- Method for fitting the rotation power-law from PV diagram  
  > "The method to examine the power-law dependence of the rotation profile is the same as that described in Yen et al. (2013)" (4.1) [from Yen et al. (2013) (cite: yen13)]
- Dust mass opacity 0.1 cm2/g at 220 GHz extrapolated with beta=0  
  > "which is extrapolated from 0.1 cm$^2$ g$^{-1}$ (cite: beckwith90) at 1 THz with $\beta$=0 (cite: tobin13)" (4.1) [from (cite: beckwith90); (cite: tobin13)]
- Keplerian disk model  
  > "a Keplerian disk orbiting a central star of 0.3 $M_{\ensuremath{\odot}}$ is considered, based on the power-law disk model(cite: kitamura02)." (4.3) [from (cite: kitamura02)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/imaging procedure (tclean/clean parameters, weighting, robust, cell, image size)
- Continuum subtraction and line-free channels
- How PV data points were extracted (cut width, position angle, peak/edge criterion)
- Model envelope density normalization and numerical radiative transfer code details
- Reference 1 data and details of 2a SO lines used in LVG
- Measurement of gas mass abundances/errors

## Analysis recipe

1. **Measure continuum and line maps**: Gaussian fits to continuum and SO moment 0; moment 0/1 maps and line profile at protostar position  
  > "The peak position measured with a Gaussian fitting is consistent with a previous measurement at high angular resolutions" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit rotation profile from C18O PV diagram**: Least-squares power-law fits to PV data points, single and broken power laws within 100 AU  
  > "the measured data points within 100 AU are fitted with two power-laws having a break at a certain radius." (4.1)
   - parameter: systemic velocity 5.9 km/s  
  > "We adopt 5.9 km s$^{-1}$ for the systemic velocity of the L1527 system in this paper." (Introduction)
   - assumption: Radii <100 AU used because resolved-out large scales overestimate rotation velocity  
  > "For this reason, we focus on the measurements at radii less than 100 AU" (4.1)
   - fitting: Least-squares; compared sum of squared residuals per degree of freedom  
  > "The sum of squared residuals, $\sum(\log V_{\rm obs}-\log V_{\rm model})^2/n$, where $n$ is degrees of freedom, is $2.6\times10^{-4}$." (4.1)
   - validation: Comparison with SMA and Tobin et al. 2012 rotation curves; two-power-law residual lower than single  
  > "suggesting that the fitting with two power-laws is somewhat better than that with the single power-law" (4.1)
3. **Derive masses (gas and disk)**: Optically thin C18O mass; dust continuum disk mass  
  > "on the assumption that the line is optically thin, the C$^{18}$O excitation temperature is 10 K, and the the relative abundance of C$^{18}$O is $3\times10^{-7}$." (3.2)
   - assumption: kappa=0.1 cm2/g at 220 GHz (beta=0) or 0.022 (beta=1), Td~50 K  
  > "the dust temperature is $\sim$50 K, which is estimated from the temperature profile" (4.1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Estimate SO gas kinetic temperature**: LVG statistical equilibrium on three SO lines with chi2 test and filling factor for edge-on ring  
  > "Brightness temperatures of each SO line are calculated with various sets of the three parameters, and are compared with the observed brightness temperatures with a $\chi^2$ test" (Appendix)
   - software: RADEX (cross-check)
   - parameter: lines resampled to 0.28 km/s, convolved to 0.96"x0.73", measured in 0.75"x0.75" box  
  > "all the three SO lines were resampled with the same velocity resolution (0.28 km s$^{-1}$)" (Appendix)
   - assumption: static spherically symmetric escape probability; chi2<10 accepted  
  > "We consider that parameter sets with $\chi^2<10$ can reproduce the observations very well." (Appendix)
   - fitting: chi2 grid over Tkin, n(H2), X/(dV/dr)  
  > "There are three free parameters for the LVG calculations, i.e., the kinetic temperature, the number density of H$_2$, and $\frac{X}{dV/dr}$" (Appendix)
   - validation: Results same as RADEX  
  > "We confirmed that our calculations provide the same results as those from the RADEX code(cite: tak07)." (Appendix)
5. **Model line profiles and PV diagrams with infall**: Envelope+SO ring+Keplerian disk model, LTE radiative transfer, CASA simulator; Model 1 free-fall vs Model 2 reduced infall  
  > "Expected line emissions along line of sights were calculated with radiative transfer equations assuming the local thermal equilibrium and an edge-on configuration" (4.3)
   - software: CASA simulator
   - parameter: SO ring 70-120 AU, 32 K, SO abundance 9e-7 (5000x outside); disk 54 AU, 0.3 Msun; j=6.1e-4 km/s pc  
  > "Within the SO ring region, the fractional abundance of SO is $9\times10^{-7}$, which is 5000 times higher than that outside and inside of the hot ring." (4.3)
   - assumption: edge-on, inclination 90 deg  
  > "their inclination angles are 90$\ensuremath{^\circ}$" (4.3)
   - fitting: Manual adjustment of infall velocity; no formal fit  
  > "Infall velocities in model envelopes are adjusted to reproduce the observations" (4.3)
   - validation: Qualitative comparison of line profiles and PV diagrams; robust against 0.2 Msun  
  > "our conclusion is still valid even if we use the smaller mass of the central protostar, $0.2~M_{\ensuremath{\odot}}$" (4.3)

## Software

- **CASA** : CASA simulator for model line profiles and PV diagrams  
  > "the CASA simulator was used to reproduce the observed line profiles and PV diagrams." (4.3)
- **RADEX** : cross-check of LVG calculation  
  > "We confirmed that our calculations provide the same results as those from the RADEX code(cite: tak07)." (Appendix)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum peak | ~130 | not stated | mJy/beam | 1 | Compact emission of 1.31 mm continuum having a peak of $\sim$130 mJy beam$^{-1}$ was detected. |
| Continuum total flux density (>3 sigma) | ~0.20 | not stated | Jy | 1 | Total flux density integrated over the area with more than 3 $\sigma$ level is measured to be $\sim$0.20 Jy. |
| Continuum deconvolved size | 0.64" x 0.36" (~90 AU x 50 AU) | not stated | arcsec | 1 | providing a deconvolved size of $0.64\ensuremath{''}\times0.36\ensuremath{''}$ (PA$\sim0.9\ensuremath{^\circ}$) |
| C18O integrated intensity | 2.7 | not stated | Jy km/s | 1 | The total integrated intensity of C$^{18}$O is measured to be 2.7 Jy km s$^{-1}$ |
| C18O envelope H2 mass (upper limit) | 1.1e-3 | not stated | Msun | 3 | the total H$_2$ gas mass of the C$^{18}$O envelope is estimated to be $1.1\times10^{-3}~M_{\ensuremath{\odot}}$ |
| SO deconvolved size | 1.4" x 0.68" (200 AU x 95 AU) | not stated | arcsec | 1 | The deconvolved size of the SO emission was measured to be $1.4\ensuremath{''}\times0.68\ensuremath{''}$ |
| Rotation power-law index, all data | ~-0.7 | not stated | dimensionless | 2 | the overall rotation profile can be fitted with a power-law having an index of $\sim-0.7$ |
| Rotation power-law index within 100 AU | ~-1 | not stated | dimensionless | 2 | the rotation profile at the radius less than 100 AU can be fitted with a power-law having an index of $\sim-1$ |
| Break radius of two power-law fit | 53.7 | 0.4 | AU | 2 | having a break at a radius of $53.7\pm0.4$ AU |
| Inner power-law index | -0.41 | 0.24 | dimensionless | 2 | The shallower rotation profile within $\sim$54 AU has an power-law index of $\sim-0.41\pm0.24$ |
| Outer power-law index | -1.16 | 0.13 | dimensionless | 2 | whereas the index outside $\sim$54 AU is $\sim-1.16\pm0.13$ |
| Dynamical mass of protostar (lower limit) | ~0.3 | not stated | Msun | 2 | the dynamical mass of the central protostar is estimated to be $\sim0.3~M_{\ensuremath{\odot}}$ |
| Disk mass (beta=0 / beta=1) | ~2.8e-3 / ~1.3e-2 | not stated | Msun | 3 | the mass of the disk is estimated to be $\sim 2.8 \times 10^{-3}~M_\ensuremath{\odot}$ |
| SO gas kinetic temperature | ~32 | not stated | K | 4 | we consider that the kinetic temperature of the SO gas within the ring is $\sim$32 K. |

## Qualitative findings

- C18O shows redshifted absorption against continuum (inverse P-Cygni), indicating infall  
  > "C$^{18}$O emission shows strong redshifted absorption against the bright continuum emission associated with L1527 IRS, strongly suggesting infall motions in the C$^{18}$O envelope." (abstract)
- SO shows rigid-body-like rotation, explained by a ring with enhanced SO abundance  
  > "The rigid-body like rotation can be naturally explained when the SO emission has a ring like structure" (Conclusions)

## Claim tuples

- H: Does the inner envelope show a transition to Keplerian rotation? | E: Power-law fits to C18O PV diagram within 100 AU | R: Index ~-1 overall; break at 53.7 AU with inner index -0.41±0.24 | F: Possible Keplerian disk of ~54 AU around ~0.3 Msun protostar | **partially**
- H: Is infall velocity equal to free fall? | E: Compare Model 1 and Model 2 to observed profiles and PV diagrams | R: Free-fall model fails; reduced infall reproduces features | F: Infall velocity is slower than free-fall | **supported**
- H: What produces rigid-like SO rotation? | E: LVG analysis and ring model | R: Tkin ~32 K; ring 70-120 AU | F: SO traces a ring in the infalling envelope with local abundance enhancement likely from shock | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: C18O is likely optically thin and thus a reliable tracer of innermost envelope kinematics compared with 13CO  
  > "We note that C$^{18}$O is more likely optically thin, and thus a reliable tracer to investigate kinematics of the innermost envelope" (Introduction)
- Alternative: Tobin et al. 2012 Keplerian (-0.5) rotation curve is inconsistent with this data  
  > "apparently demonstrating that their rotation curve is inconsistent with ours." (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Missing flux on large scales biases rotation velocities at large radii  
  > "50% of emission arising from the structures having a $\sim$1000 AU scale (500 AU in radius) is missed in our current ALMA measurements" (4.1)
- Limitation (authors): SO is optically thick so density and abundance unconstrained  
  > "Since SO is optically thick, it is impossible for us to estimate the H$_2$ density and the abundance of SO." (Appendix)
- Caveat (inferred, ours): Break in rotation profile has large error and rests on a low-resolution (0.8") dataset with ~54 AU radius below the beam
- Caveat (inferred, ours): Infall models tuned by eye with no quantitative goodness-of-fit
- Caveat (inferred, ours): Edge-on ring interpretation of SO is not unique
- Caveat (inferred, ours): Missing flux affects inferred rotation

## Reproducibility

- Data public (paper): ALMA cycle 0 project cited in acknowledgments  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00210.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: PV extraction details
- Missing: Model envelope code and full parameters
- Data volume (inferred): ~10-30 GB raw single-EB cycle 0 data
- Score (inferred): 4/5, Single public cycle 0 dataset and clear quantitative fits, but processing and model details missing.
- Rediscovery candidate: no, Calibration/imaging and PV extraction recipe not given in enough detail, and modeling is by-eye.

## Links

- Method: Yen et al. 2013 (cite: yen13) (Rotation-profile power-law method)
- Companion: Tobin et al. 2012 (cite: tobin12) (Previous high-resolution L1527 Keplerian-disk result)

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
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
  "facts": 82,
  "stated": 53,
  "rate": 0.646
 },
 "evidence_ok": true
}
```
