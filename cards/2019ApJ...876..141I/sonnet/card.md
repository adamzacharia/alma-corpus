# ALMA Observations of Giant Molecular Clouds in the Starburst Dwarf Galaxy Henize 2-10

`2019ApJ...876..141I` | The Astrophysical Journal 2019 | first author: Imara, Nia | arXiv: 1812.02180 | DOI: 10.3847/1538-4357/ab16cc

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: What are the molecular gas distribution and giant molecular cloud properties in the starburst dwarf Henize 2-10, and how do they compare with Milky Way and other galaxies?  
  > "Our main goals are to (1) use this exquisite data set to identify molecular clouds; (2) characterize their properties; and (3) discover whether and why there are differences between stellar nurseries in Henize 2-10 and the Milky Way and other galaxies." (Introduction)
- Target **Henize 2-10**: coordinates 08h36m15.20s, -26d24m34.0s (J2000)  
  > "A single position ($08^{\rm h}36^{\rm m}15.20s, -26\ensuremath{^\circ} 24\ensuremath{'}34.0\ensuremath{''}$ \[J2000\]) was observed." (Observations); "Henize 2-10 is located in the constellation Pyxis at a distance of $8.7$ Mpc (cite: Tully_1988)." (Introduction); z/distance 8.7 Mpc  
  > "A single position ($08^{\rm h}36^{\rm m}15.20s, -26\ensuremath{^\circ} 24\ensuremath{'}34.0\ensuremath{''}$ \[J2000\]) was observed." (Observations); "Henize 2-10 is located in the constellation Pyxis at a distance of $8.7$ Mpc (cite: Tully_1988)." (Introduction); distance from Tully 1988 (cite: Tully_1988)  
  > "A single position ($08^{\rm h}36^{\rm m}15.20s, -26\ensuremath{^\circ} 24\ensuremath{'}34.0\ensuremath{''}$ \[J2000\]) was observed." (Observations); "Henize 2-10 is located in the constellation Pyxis at a distance of $8.7$ Mpc (cite: Tully_1988)." (Introduction)

## Data provenance

- ALMA projects: 2015.1.01569.S, 2015.1.01395.S
- bands: Band 3  
  > "The ALMA Band 3 correlator was set up to have a velocity resolution of 244.141 kHz (0.637 km s$^{-1}$) and a bandwidth of 469 MHz" (Observations)
- frequencies and spectral setup: 469 MHz bandwidth centered at 114.936 GHz, 244.141 kHz (0.637 km/s) resolution  
  > "a bandwidth of 469 MHz, centered at 114.936 GHz to cover the $^{12}$CO(1-0) line" (Observations)
- continuum bandwidth: _not stated_
- arrays: 12-m array, 36 antennas  
  > "The ALMA 12-m array was in configuration C36-4 for the two observing nights, with 36 antennas each night" (Observations)
- configurations: C36-4  
  > "The ALMA 12-m array was in configuration C36-4 for the two observing nights" (Observations)
- baselines: 15 m to 1124 m  
  > "arranged with baselines from 15 m to 1124 m" (Observations)
- angular resolution: 0.67" x 0.58" (28 x 24 pc)  
  > "The synthesized beam was measured to be $0.67\ensuremath{''}\times 0.58\ensuremath{''}$" (Observations)
- max recoverable scale: 6.7"  
  > "a maximum recoverable scale of $6.7\ensuremath{''}$ (at 115.27 GHz)" (Observations)
- sensitivity: 3.7 mJy per 1 km/s channel  
  > "The rms sensitivity is $3.7$ mJy per $1~\mbox{km~s$^{-1}$}$ channel." (Observations)
- time on source: 31.75 min per night  
  > "On-source time | 31.75 min | 31.75 min" (Table 2)
- observing dates: 2016 July 31 and Aug 2  
  > "Date | 2016 July 31 | 2016 Aug 2" (Table 2)
- pi or archival as stated: PI: Nia Imara  
  > "project code 2015.1.01569.S; PI: Nia Imara" (Observations)
- Line: 12CO J=1-0 (115.2712 GHz)
- External data: Distance 8.7 Mpc  
  > "at a distance of $8.7$ Mpc (cite: Tully_1988)" (Introduction) [from (cite: Tully_1988)]
- External data: Metallicity 12+log(O/H)=8.55  
  > "We take their resulting measurement of $12+\log(\rm{O/H})=8.55\pm0.02$ $(\sim 0.7\ensuremath{Z_\odot})$ to be the most reliable in the literature" (3.2 Molecular Mass) [from (cite: Esteban_2014)]
- External data: Comparison GMC catalogs for Milky Way, LMC, NGC 300, IC 10, II Zw 40  
  > "we compare their scaling relations to those of clouds in a sample of galaxies collected from the literature." (4.4 Molecular Clouds in Other Galaxies) [from (cite: Heyer_2009; Oka_2001; Wong_2011; Faesi_2018; Leroy_2006; Kepley_2016)]

## Processing

### Calibration

- pipeline or manual: Manual calibration by North American ALMA Science team  
  > "The North American ALMA Science team used CASA version 4.5.3 to manually calibrate the data." (Observations)
- casa version: CASA 4.5.3 (calibration)  
  > "The North American ALMA Science team used CASA version 4.5.3 to manually calibrate the data." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1037-2934 (July 31), J1107-4449 (Aug 2)  
  > "Flux calibrator | J1037-2934 | J1107-4449" (Table 2)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA multiscale CLEAN  
  > "We imaged our data in CASA using the `multiscale` CLEAN algorithm." (Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "natural weighting was chosen in order maximize sensitivity" (Observations)
- uv taper: _not stated_
- cell size: 0.1" x 0.1" x 1 km/s voxels  
  > "The final data cube has voxels with dimensions of $0.1\ensuremath{''}\times 0.1\ensuremath{''} \times 1~\mbox{km~s$^{-1}$}$" (Observations)
- image size: _not stated_
- masking: Mask drawn by hand around significant coherent emission in each channel  
  > "a mask was drawn around all the significant and coherent emission. This mask was then used to deconvolve all image planes." (Observations)
- multiscale scales: _not stated_
- continuum subtraction: Continuum (~25 mJy) subtracted in visibility domain  
  > "We detected continuum emission with a total flux of about 25 mJy and subtracted this from the line emission in the visibility domain." (Observations)
- line free channels: _not stated_
- primary beam correction: Applied  
  > "Finally, we applied a primary beam correction" (Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.67" x 0.58"  
  > "The synthesized beam was measured to be $0.67\ensuremath{''}\times 0.58\ensuremath{''}$" (Observations)
- final rms: 3.7 mJy per 1 km/s channel  
  > "The rms sensitivity is $3.7$ mJy per $1~\mbox{km~s$^{-1}$}$ channel." (Observations)

### Inherited from earlier work

- CPROPS cloud decomposition, deconvolution and bootstrap error method  
  > "we used the `CPROPS` algorithm of (cite: Rosolowsky_2006)." (4.1 GMC Identification) [from (cite: Rosolowsky_2006)]
- Velocity-gradient plane fit to first-moment map  
  > "by fitting a plane to the intensity-weighted first-moment map of velocity centroids, following (cite: Imara_2011a)" (3.1 Dynamics) [from (cite: Imara_2011a)]
- Mass spectrum fitting with mspecfit.pro  
  > "using the `mspecfit.pro` IDL routine of (cite: Rosolowsky_2005)" (4.3 The GMC mass spectrum) [from (cite: Rosolowsky_2005)]

### Not stated but needed to reproduce (our reading)

- Multiscale CLEAN scales, threshold and gain
- Line-free channels used for continuum subtraction
- Cleaning threshold and number of iterations
- Exact masks used in imaging
- How spectra in Figure 1 and moment maps were made (CASA tasks)
- Details of the second project 2015.1.01395.S and whether its data were used
- Flux calibration accuracy and any self-calibration

## Analysis recipe

1. **Calibrate and image CO(1-0) cube**: Manual CASA calibration, continuum subtraction in uv, multiscale CLEAN with natural weighting, primary beam correction  
  > "We imaged our data in CASA using the `multiscale` CLEAN algorithm." (Observations)
   - software: CASA
   - parameter: natural weighting; 0.1" pixels; 1 km/s channels  
  > "The final data cube has voxels with dimensions of $0.1\ensuremath{''}\times 0.1\ensuremath{''} \times 1~\mbox{km~s$^{-1}$}$" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Global molecular mass and kinematics**: Sum integrated-intensity map to get mass with Galactic XCO; Gaussian fit to spectrum; plane fit to moment 1; PV diagram and dynamical mass  
  > "We calculate the total luminous molecular mass $M_{\rm tot}$ by summing over all pixels in the integrated intensity map" (3.2 Molecular Mass)
   - parameter: masked cube: seed pairs of channels >5 sigma, expand to >1.5 sigma  
  > "seed the mask by identifying pairs of channels in a given pixel with signal $>5\sigma_{\rm pix}$" (3.2 Molecular Mass)
   - assumption: XCO = 2e20 cm^-2 (K km/s)^-1, factor 1.36 for helium, distance 8.7 Mpc, edge-on rotation for dynamical mass  
  > "a typical conversion factor is $\ensuremath{X_{\mathrm{CO}}}= 2\times 10^{20}\mbox{cm$^{-2}$ (K km s$^{-1}$)$^{-1}$}$" (3.2 Molecular Mass)
   - fitting: Least-squares fit to binned velocities within 70 pc  
  > "We perform a least-squares fit to the binned velocities within 70 pc ($1.7\ensuremath{''}$) of starburst region A" (3.1 Dynamics)
   - validation: Compared to Kobulnicky 1995 mass and dynamical mass  
  > "This value is in agreement with that obtained by (cite: Kobulnicky_1995)" (3.2 Molecular Mass)
3. **Identify GMCs and measure properties**: CPROPS with default parameters, modified CLUMPFIND, extrapolation to 0 K, beam and channel deconvolution  
  > "we ultimately used the default parameters to decompose our data cube into GMCs and estimate their properties." (4.1 GMC Identification)
   - software: CPROPS, CLUMPFIND
   - parameter: 4 sigma seed, 2 sigma edge, 15 pc x 15 pc x 2 km/s moving box  
  > "Clouds were decomposed from within these islands using a moving box of $15~\ensuremath{\mbox{pc}}\times 15~\ensuremath{\mbox{pc}}\times 2~\mbox{km~s$^{-1}$}$." (4.1 GMC Identification)
   - assumption: alpha_CO = 4.35 Msun (K km/s pc^2)^-1; Mvir=1040 R sigma_v^2 (spherical, rho~R^-1)  
  > "This calculation for $M_{\rm vir}$ assumes spherical symmetry and a power law volume density ($\rho$) profile $\rho \propto R^{-1}$" (4.2 Distributions of Cloud Properties)
   - fitting: Bootstrap errors, 500 iterations  
  > "calculated using a bootstrapping method, which estimates errors by creating several trial samples from the initial cloud data (cite: Rosolowsky_2006), with 500 iterations." (4.2 Distributions of Cloud Properties)
   - validation: CPROPS recovery of model clouds shown by Rosolowsky & Leroy 2006  
  > "`CPROPS` is able to accurately recover the properties of model clouds similar to real objects in the Milky Way" (4.4 Molecular Clouds in Other Galaxies)
4. **Mass spectrum**: Truncated power-law maximum-likelihood fit of cumulative mass distribution above completeness limit  
  > "which implements a maximum likelihood algorithm that incorporates uncertainties in the cloud mass" (4.3 The GMC mass spectrum)
   - software: mspecfit.pro (IDL)
   - parameter: completeness limit 1.1e5 Msun  
  > "We estimate a completeness limit of $1.1\times 10^5 \ensuremath{M_\odot}$." (4.3 The GMC mass spectrum)
   - fitting: _not stated_
   - validation: Repeated with completeness limit 2e5 Msun, consistent  
  > "fully consistent with the results above." (4.3 The GMC mass spectrum)
5. **Scaling relations and virial analysis**: Pearson correlations, orthogonal distance regression for size-linewidth, bilinear least squares for Mvir-Mlum and Mlum-R; virial alphaCO  
  > "We conduct a fit to the size and linewidth using nonlinear orthogonal distance regression" (4.6.1 Size-linewidth relation)
   - assumption: Single Milky Way alpha_CO for all clouds  
  > "we use a single, Milky Way value for the conversion factor of $\alpha_{\rm CO}=4.3$" (4.6.2 Virial relation)
   - fitting: _not stated_
   - validation: Checked resolution and completeness limits; Galactic slope recomputed above completeness limit  
  > "for clouds above the completeness limit, the slope is 1.7" (4.6.3 Mass-size relation)

## Software

- **CASA** 4.5.3: Calibration and imaging  
  > "Our data were processed and imaged using the Common Astronomy Software Applications (CASA) package" (Observations)
- **CPROPS** : GMC identification and property measurement  
  > "we used the `CPROPS` algorithm of (cite: Rosolowsky_2006)." (4.1 GMC Identification)
- **CLUMPFIND** : Modified version to assign all emission to clouds  
  > "we used the modified `CLUMPFIND` (cite: Williams_1994) routine" (4.1 GMC Identification)
- **mspecfit.pro** : Mass spectrum fitting  
  > "using the `mspecfit.pro` IDL routine of (cite: Rosolowsky_2005)" (4.3 The GMC mass spectrum)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total molecular mass | 1.2e8 | 0.4e8 | Msun | 2 | yields a molecular gas mass of $(1.2\pm 0.4)\times 10^8~\ensuremath{M_\odot}$ |
| Integrated CO intensity | 146 | 3 | K km/s | 2 | a total integrated CO intensity of $I_{\rm CO}=146\pm 3$ K km s$^{-1}$ |
| Dynamical mass within 70 pc (edge-on) | 2.7e6 | not stated | Msun | 2 | of $2.7\times10^6$ $M_\odot$ |
| Number of clouds (resolved/total) | 119 / 178 | not stated | clouds | 3 | we identify 178 clouds, of which 59 are unresolved |
| Mass spectrum slope | -1.54 | 0.10 | dimensionless | 4 | we derive a slope of $\gamma=-1.54\pm 0.10$ |
| Truncation mass | 4.7e6 | 0.8e6 | Msun | 4 | a truncation mass of $M_0 = (4.7\pm 0.8) \times 10^6$ $M_\odot$ |
| Size-linewidth slope | 1.31 | 0.14 | dimensionless | 5 | The derived slope is $1.31\pm0.14$ |
| Mvir-Mlum slope | 1.2 | 0.1 | dimensionless | 5 | to derive a slope of $1.2\pm0.1$ |
| Mlum-R slope | 3.0 | 0.3 | dimensionless | 5 | yields a slope of $3.0\pm 0.3$ |
| Median virial alphaCO | 3.7 | not stated | Msun (K km/s pc^2)^-1 | 5 | the median value is $3.7$ $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ |
| Median GMC surface density | 180 | not stated | Msun pc^-2 | 3 | The median surface density is $180$ $M_\odot$ pc$^{-2}$ |

## Qualitative findings

- About 75% of molecular gas lies in the northern region near the SSCs; a 320 pc southern stream is a likely tidal tail  
  > "The bulk of the molecular gas, about $75\%$ by mass, resides in the northern region of the galaxy" (3.2 Molecular Mass)

## Claim tuples

- H: Henize 2-10 GMCs resemble Milky Way GMCs in basic properties | E: CPROPS decomposition and comparison with literature cloud samples | R: Median size ~26 pc, Mlum ~4e5 Msun, Sigma ~180 Msun/pc2 similar to Milky Way; velocity dispersions ~50% higher | F: Similar clouds apart from higher linewidths | **supported**
- H: Clouds are in virial equilibrium | E: Mvir vs Mlum fit | R: Slope 1.2±0.1, Pearson 0.90 | F: Clouds tend to be virialized | **supported**
- H: Mass-size scaling follows the constant-surface-density Milky Way relation | E: Fit Mlum vs R | R: Slope 3.0±0.3 | F: Steeper, suggesting constant volume density, but dependent on a constant alphaCO | **partially**
- H: Massive GMCs can form next-generation SSCs | E: Compare cloud masses with SSC masses at given efficiency | R: 47 clouds have enough mass at 5% efficiency to match region B | F: Clouds are potential SSC precursors | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Multiscale CLEAN to recover extended emission; natural weighting for sensitivity  
  > "With the aim of measuring the CO-derived properties of molecular clouds, natural weighting was chosen in order maximize sensitivity." (Observations)
- Alternative: Varying CPROPS parameters was tried, then defaults were adopted  
  > "After performing several experiments using various parameters of the `CPROPS` algorithm, we ultimately used the default parameters" (4.1 GMC Identification)
- How they decided it was enough: _not stated_
- Limitation (authors): A single Galactic alphaCO is applied despite likely metallicity and starburst variations  
  > "we do not attempt to account for these effects in our calculations." (4.6.2 Virial relation)
- Limitation (authors): Power-law size-linewidth fit is a poor model and bulk motions were not subtracted  
  > "We thus caution the over-interpretation of the exact value of this power law slope." (4.6.1 Size-linewidth relation)
- Caveat (inferred, ours): Galactic alphaCO assumed despite the metallicity gradient; mass and surface density are uncertain
- Caveat (inferred, ours): Comparison samples used different CPROPS settings, resolutions and CO lines
- Caveat (inferred, ours): Single-pointing mosaic with no total-power data; missing extended flux is not assessed in detail

## Reproducibility

- Data public (paper): ALMA project codes are given; archive acknowledgement printed  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01395.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CLEAN scales, thresholds and mask
- Missing: Line-free channel selection
- Missing: Cloud table is printed but CPROPS input details beyond defaults are not given
- Data volume (inferred): ~10-30 GB raw for two 12-m execution blocks
- Score (inferred): 6/5, Public data and well-defined CPROPS analysis with a cloud table, but imaging parameters are underspecified.
- Rediscovery candidate: yes, Data public, CPROPS recipe with defaults and numeric results (cloud counts, slopes) are checkable.

## Links

- Method: (cite: Rosolowsky_2006) (CPROPS algorithm)
- Method: (cite: Rosolowsky_2005) (mass spectrum fitting)
- Companion: (cite: Johnson_2018) (Dense gas observations of Henize 2-10)
- Companion: (cite: Kobulnicky_1995) (Earlier CO(1-0) observations)

## Checks

```json
{
 "quotes": 82,
 "quotes_ok": 82,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 60,
  "rate": 0.759
 },
 "evidence_ok": true
}
```
