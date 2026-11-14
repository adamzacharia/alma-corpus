# Morphology and kinematics of the gas envelope of protostar L1527 as obtained from ALMA observations of the C<SUP>18</SUP>O(2-1) line emission

`2016MNRAS.463.3563T` | Monthly Notices of the Royal Astronomical Society 2016 | first author: Tuan-Anh, P. | arXiv: 1604.03801 | DOI: 10.1093/mnras/stw2206

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation
- Question: What are the morphology and kinematics (rotation, in-fall, central mass, accretion rate, orientation) of the L1527 gas envelope from C18O(2-1) emission, using a simple axisymmetric 3D parameterisation avoiding absorption-dominated regions?  
  > "we have reconstructed its morphology and kinematics under the assumption of axisymmetry about the west-east axis." (abstract)
- Target **L1527 IRS**: coordinates RA 4h35m53.870s, Dec 26d3m9.54s (continuum maximum)  
  > "L1527 IRS is a class 0 protostar, at a distance of $\sim$140 pc, in its earliest stages of formation." (1 Introduction); "right ascension of 4 h 35 m 53.870 s and declination of 26$^\circ$ 3 arcmin 9.54 arcsec." (2.1 Observations and data reduction); z/distance 140 pc  
  > "L1527 IRS is a class 0 protostar, at a distance of $\sim$140 pc, in its earliest stages of formation." (1 Introduction); "right ascension of 4 h 35 m 53.870 s and declination of 26$^\circ$ 3 arcmin 9.54 arcsec." (2.1 Observations and data reduction); distance from assumed  
  > "L1527 IRS is a class 0 protostar, at a distance of $\sim$140 pc, in its earliest stages of formation." (1 Introduction); "right ascension of 4 h 35 m 53.870 s and declination of 26$^\circ$ 3 arcmin 9.54 arcsec." (2.1 Observations and data reduction)

## Data provenance

- ALMA projects: 2012.1.00647.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 35-36 antennas, longest baseline 783.5 m  
  > "the longest baseline being 783.5 m" (2.1 Observations and data reduction)
- angular resolution: 0.6 x 0.5 arcsec, PA -174 deg  
  > "The synthetized beam size (FWHM) is 0.6 $\times$ 0.5 arcsec$^2$ with a $-174^\circ$ position angle from north." (2.1 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: effective noise rms 3-5 mJy/beam  
  > "The rms value of the peak varies between 3 and 5 mJy beam$^{-1}$" (2.2 Line data)
- time on source: 36 minutes  
  > "The time spent on source was 36 minutes." (2.1 Observations and data reduction)
- observing dates: July 20, 2014 (Cycle 1)  
  > "The observations used in the present article were made in cycle 1 of ALMA operation on July 20, 2014." (2.1 Observations and data reduction)
- pi or archival as stated: Public archival data retrieved from JVO portal  
  > "The data are retrieved from the JVO portal (http://jvo.nao.ac.jp/portal) operated by the NAOJ." (Acknowledgements)
- Line: C18O 2-1 (not stated)
- External data: C18O to H2 ratio of 4.9e-8 used for accretion rate  
  > "a C$^{18}$O to molecular hydrogen ratio of 4.9 10$^{-8}$ (cite: Jorgensen2002)" (6.5 Accretion rate) [from (cite: Jorgensen2002)]

## Processing

### Calibration

- pipeline or manual: Merged and reduced by ALMA staff  
  > "the two sets of data have been merged and reduced by the ALMA staff." (2.1 Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.15 x 0.15 arcsec pixels; 0.16 km/s velocity bins  
  > "Pixels are 0.15 $\times$ 0.15 arcsec$^2$ and the velocity bins are 0.16 km s$^{-1}$ wide." (2.1 Observations and data reduction)
- image size: 17 x 57 pixels (2.55 x 8.55 arcsec) used  
  > "covering 17 pixels in $x$ and 57 pixels in $y$, namely 2.55 and 8.55 arcsec respectively" (2.1 Observations and data reduction)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- Imaging parameters (weighting, robust, deconvolver, continuum subtraction, line-free channels)
- Calibration details and CASA version
- Exact fitting algorithm/minimiser and starting values
- Rest frequency and spectral setup
- Exact mapping of chi2 5% sensitivity to uncertainties
- Procedure for corrections to neighbouring velocity bins
- Temperature/optical depth treatment details for accretion rate conversion

## Analysis recipe

1. **Define centre and noise**: Continuum Gaussian fits to define origin; effective noise per velocity bin from the low-value peak of flux density distribution, offset-corrected  
  > "We evaluated the position and width of the effective noise, meaning the peak observed at low values in the distribution of the flux density, in each velocity bin separately." (2.2 Line data)
   - parameter: 2-sigma cut on flux densities  
  > "We normally retain for the analysis, unless specified otherwise, flux densities exceeding twice the uncertainty (we speak of a 2-$\sigma$ cut)." (2.2 Line data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit 3D axisymmetric parametric envelope model**: Symmetrised data fit with effective-emissivity model with gas spiralling on paraboloids, rotation and in-fall; chi2 minimisation; velocity bins 0-0.32 km/s excluded  
  > "we describe the flux as spiralling on paraboloids having as axis the symmetry axis." (4.1 General description)
   - parameter: chi2 uncertainties: quadrature of noise uncertainties and 10% of flux density; line-of-sight integration to 7 arcsec  
  > "The $\chi^2$ is evaluated using as uncertainties the sum in quadrature of the above mentioned uncertainties and 10% of the measured flux density." (4.1 General description)
   - assumption: Axisymmetry about x axis, symmetry in x and y, optically thin C18O  
  > "We assume perfect symmetry in both $x$ and $y$ and rotation invariance about the $x$ axis." (4.1 General description)
   - fitting: chi2 best fit; parameter sensitivity as change for 5% chi2 increase  
  > "amounts by which the parameter has to increase ($\Delta^+$) or to decrease ($\Delta^-$) for $\chi^2$ to increase by 5%" (4.3 Result)
   - validation: Compared model and data maps and asymmetry; different reasonable choices give same results  
  > "We have checked that different reasonable choices essentially lead to the same results as presented below." (4.1 General description)
3. **Derive central mass and accretion rate**: Energy conservation V_tot = sqrt(2GM/r) at 1.5 arcsec; accretion rate from normalisation rho_0  
  > "The measured velocity $V_{tot}$=1.3 km s$^{-1}$at $r$=1.5 arcsec being then equal to $\sqrt{2GM/r}$" (6.3 Central mass)
   - assumption: Constant temperature 30 K, C18O/H2 = 4.9e-8  
  > "we assume a constant temperature of 30 K and a C$^{18}$O to molecular hydrogen ratio of 4.9 10$^{-8}$" (6.5 Accretion rate)
   - fitting: _not stated_
   - validation: Compared with Tobin et al. 2012 mass and accretion rate  
  > "This measurement agrees well with the evaluation made by (cite: Tobin2012)" (6.3 Central mass)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean in-fall velocity | 0.43 | 0.10 | km/s | 2 | we may retain a mean in-fall velocity of 0.43$\pm$0.10 km s$^{-1}$over the explored range |
| Central mass within 1.5 arcsec | 0.23 | 0.06 | Msun | 3 | 0.23$\pm$0.06 M$_{\odot}$ within a distance of 1.5 arcsec from the star |
| Accretion rate at 1 arcsec (140 au) | 3.5e-7 | 1.0e-7 | Msun/yr | 3 | 3.5$\pm$1.0 10$^{-7}$M$_{\odot}$ yr$^{-1}$at a distance of 1 arcsec (140 au) from the star |
| Rotation velocity scale V_rot0 | 1.66 | -0.06/+0.09 | km/s | 2 | / $V_{rot0}$ / Rotation velocity / 1.66 / 0.06 / 0.09 / |
| Non-stationarity q | 0.93 | 0.25 | dimensionless | 2 | 0.93$\pm$0.25 |
| Tilt about line of sight from mean velocity map | 9.6 | not stated | deg | 0 | corresponding to a tilt of $\tan^{-1}(0.17)=9.6^\circ$ east of north |

## Qualitative findings

- Strong depression of in-falling flux near the disc plane giving X-shaped flow, possibly from CO freeze-out  
  > "evidence for a strong disc plane depression of the in-falling flux resulting in an $X$ shaped flow possibly caused by the freeze-out of CO molecules on dust grains" (abstract)

## Claim tuples

- H: Envelope kinematics can be measured from non-absorbed regions only | E: Parametric axisymmetric model fitted to C18O(2-1) cube | R: Mean in-fall 0.43 km/s, no strong r-dependence; rotation toward Keplerian | F: Model reproduces data better than earlier attempts; no sudden in-fall jump needed | **supported**
- H: Central mass and accretion rate consistent with earlier estimates | E: Energy conservation on fitted V_tot | R: M=0.23±0.06 Msun; accretion 3.5±1.0e-7 Msun/yr | F: Mass agrees with Tobin; accretion about half of Tobin's | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Analysis too distant from star to observe the disc; delta values are not rigorous uncertainties  
  > "However, the range explored is too distant from the star to allow direct observation of the disc." (Summary)
- Caveat (inferred, ours): Delta parameter errors are not true uncertainties
- Caveat (inferred, ours): Absorption exclusion and ad hoc symmetrisation may bias results
- Caveat (inferred, ours): Temperature fixed at 30 K and ad hoc effective emissivity
- Caveat (inferred, ours): No comparison to radiative transfer modelling

## Reproducibility

- Data public (paper): Public ALMA data retrieved via JVO  
  > "The data are retrieved from the JVO portal (http://jvo.nao.ac.jp/portal) operated by the NAOJ." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Fitting code and minimiser
- Missing: Imaging/calibration details
- Missing: Exact correction procedure for neighbour bins
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Model equations and best-fit table given, but fitting code and cube processing details are missing.
- Rediscovery candidate: no, Fit procedure underspecified despite public data.

## Links

- Companion: (cite: Ohashi2014) (Earlier ALMA Cycle 0 C18O analysis of L1527 with absorption-based model)

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 59,
  "stated": 27,
  "rate": 0.458
 },
 "evidence_ok": true
}
```
