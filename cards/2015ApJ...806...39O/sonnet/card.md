# A Measurement of the Black Hole Mass in NGC 1097 Using ALMA

`2015ApJ...806...39O` | The Astrophysical Journal 2015 | first author: Onishi, K. | arXiv: 1506.05917 | DOI: 10.1088/0004-637X/806/1/39

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What is the SMBH mass of NGC 1097 from dense molecular gas (HCN and HCO+ J=1-0) kinematics measured with ALMA?  
  > "Dense molecular gas dynamics are traced with ${\rm HCN} (J=1-0)$ and ${\rm HCO^{+}} (J=1-0)$ emission lines." (abstract)
- Target **NGC 1097**: coordinates RA 02h46m18.96s, Dec -30d16'28.9'' (J2000; 6 cm peak)  
  > "is a nearby Type-1 Seyfert galaxy at a distance of 14.5 Mpc (cite: 1988ngc..book.....T) ($\sim70$ pc arcsecond$^{-1}$)." (NGC 1097); z/distance 14.5 Mpc  
  > "is a nearby Type-1 Seyfert galaxy at a distance of 14.5 Mpc (cite: 1988ngc..book.....T) ($\sim70$ pc arcsecond$^{-1}$)." (NGC 1097); distance from Tully 1988 Nearby Galaxies Catalog  
  > "is a nearby Type-1 Seyfert galaxy at a distance of 14.5 Mpc (cite: 1988ngc..book.....T) ($\sim70$ pc arcsecond$^{-1}$)." (NGC 1097)

## Data provenance

- ALMA projects: 2011.0.00108.S
- bands: Band 3  
  > "was observed with the band 3 receiver on ALMA using the two sideband dual-polarization setup as a cycle 0 observation" (2 Observations and Data Reduction)
- frequencies and spectral setup: 87.275-100.917 GHz, four spectral windows of 1.875 GHz with 3840 channels, 0.488 MHz per channel  
  > "Each spectral window had a bandwidth of 1.875 GHz with 3840 channels. The frequency resolution was 0.488 MHz per channel." (2 Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Cycle 0 extended configuration (400 m baselines)  
  > "The antennas were in the Cycle 0 extended configuration (400m baselines)" (2 Observations and Data Reduction)
- baselines: _not stated_
- angular resolution: 1.60'' x 2.20'' at PA -81.2 deg (~112 pc x 154 pc)  
  > "synthesized beam of $1''.60 \times 2''.20$ at a position angle $-81.2^{\circ}$" (2 Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 105.24 minutes  
  > "a total on-source time of 105.24 minutes" (2 Observations and Data Reduction)
- observing dates: 2012 Jul 29 and 2012 Oct 19  
  > "The observations were conducted on 2012 Jul 29 and 2012 Oct 19" (2 Observations and Data Reduction)
- pi or archival as stated: Cycle 0 project, PI K. Kohno  
  > "(Project code = 2011.0.0108.S; PI = K. Kohno)" (2 Observations and Data Reduction)
- Line: HCN J=1-0 (not stated)
- Line: HCO+ J=1-0 (not stated)
- Other facility **HST ACS/WFC F814W**: I-band image for stellar luminosity profile and MGE  
  > "We use an I-band image observed with the Advanced Camera for Surveys Wide Field Channel F814W filter on *Hubble Space Telescope* (*HST*)" (3.1 The Mass Model)
- Other facility **HST NICMOS F190N**: 1.9 micron profile to test dust extinction  
  > "NICMOS on *HST* has a narrow band filter F190N which observes at 1.9 microns." (4.1)
- External data: Inclination 46±5 deg  
  > "| Inclination angle ($^{\circ}$) | 46$\pm$5 | 5 |" (Table 1) [from Ondrechen et al. 1989 (cite: 1989ApJ...342...39O)]
- External data: Major axis PA 130 deg  
  > "The major axis defined here is at a position angle of $130^{\circ}$ from (cite: 1991rc3..book.....D)." (3.1 The Mass Model) [from de Vaucouleurs et al. 1991 (cite: 1991rc3..book.....D)]
- External data: Velocity dispersion 196±5 km/s  
  > "with an observed $\sigma=196 \pm 5$ km s$^{-1}$" (NGC 1097) [from Lewis & Eracleous 2006 (cite: 2006ApJ...642..711L)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA 4.0  
  > "The data were reduced and imaged using CASA (Common Astronomy Software Applications) 4.0 with a robustness parameter of 0.5." (2 Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "with a robustness parameter of 0.5" (2 Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: binned by 2 channels, ~3 km/s (0.976 MHz)  
  > "We binned the data by 2 channels to improve the signal to noise ratio and our final resolution is 0.976 MHz or $\sim 3$ km s$^{-1}$." (2 Observations and Data Reduction)
- final beam: 1.60'' x 2.20''  
  > "synthesized beam of $1''.60 \times 2''.20$" (2 Observations and Data Reduction)
- final rms: moment-0 noise 22 (HCN) and 26 (HCO+) mJy/beam km/s  
  > "The noise in the integrated intensity maps is 22 (mJy beam$^{-1}$ km s$^{-1}$) in the ${\rm HCN} (J=1-0)$" (2 Observations and Data Reduction)

### Inherited from earlier work

- Method of SMBH mass from molecular gas kinematics (KinMS, MGE)  
  > "we use the method initially employed by (cite: 2013Natur.494..328D) and extend it to measure the SMBH mass" (Introduction) [from (cite: 2013Natur.494..328D)]
- Gravitational potential from MGE equations  
  > "The gravitational potential is derived by following the equations described in (cite: 2002ApJ...578..787C)" (3 Supermassive Black-hole mass Estimation) [from (cite: 2002ApJ...578..787C)]

### Not stated but needed to reproduce (our reading)

- Continuum subtraction and line-free channels
- Calibration details (calibrators, flux scale, pipeline vs manual)
- Image size and cell size, cleaning threshold, masking
- KinMS parameters: gas disk radial profile, thickness, number of clouds
- Details of MGE fit and HST image processing
- Exact PVD extraction slit width
- Spectral-line rest frequencies

## Analysis recipe

1. **Image the HCN and HCO+ cubes and make moment maps**: CASA imaging with robust 0.5, 2-channel binning; moment maps with Karma  
  > "The integrated intensity moment zero and intensity weighted velocity maps were made using Karma (cite: 1996ASPC..101...80G)." (2 Observations and Data Reduction)
   - software: CASA, Karma
   - fitting: _not stated_
   - validation: _not stated_
2. **Model stellar luminosity with MGE**: Fit multi-Gaussian expansion to HST F814W major-axis profile after subtracting AGN (PSF 0.2'') and masking starburst ring  
  > "We model the stellar luminosity profile by calculating the least-square value with the luminosity distribution without the ring and the AGN." (3.1 The Mass Model)
   - software: Tiny Tim
   - parameter: Ring at -11'' to -7'' and 8'' to 13''  
  > "The starburst ring region is determined to be in the range of radii from $-11''$ to $-7''$ and from $8''$ to $13''$ along the major axis." (3.1 The Mass Model)
   - assumption: Axisymmetric galaxy; constant I-band M/L radially  
  > "we are assuming that the radial difference of the M/L ratio is negligible" (3.1 The Mass Model)
   - fitting: least squares  
  > "We model the stellar luminosity profile by calculating the least-square value with the luminosity distribution without the ring and the AGN." (3.1 The Mass Model)
   - validation: AGN subtraction effect <6e6 Msun  
  > "Even the peak before subtraction gives a mass of less than $6.00\times10^{6}M_{\odot}$ for a M/L ratio 5.14" (3.1 The Mass Model)
3. **Compute circular velocity field and model PVD**: MGE_circular_velocity at i=46 deg, then KinMS thin axisymmetric disk convolved with beam, PA 130 deg  
  > "We convolve the model cloud distribution with our beamsize ($1''.60 \times 2''.20$) to express the beam-smearing, and assume the molecular gas disk to be an axisymmetric thin disk." (3.3)
   - software: MGE_circular_velocity, KinMS
   - parameter: inclination 46 deg  
  > "The inclination angle is set to be $46^{\circ}$" (3.2)
   - assumption: Streaming motion negligible  
  > "We assume that the streaming motion remaining in the PVD is negligible." (3.3)
   - fitting: _not stated_
   - validation: _not stated_
4. **Chi-square grid fit of M_BH and M/L to PVD**: Extract 106 points from observed PVD above 3 sigma ~8 mJy; grid M/L 4.80-5.35 (0.01), M_BH 0.5-2.5e8 (0.1e8); errors at Delta chi2<=9  
  > "the finer grid of model parameters is set to be from M/L$=4.80$ to 5.35 in steps of 0.01 and $M_{\rm BH}=0.5 \times 10^{8} M_{\odot}$ to $2.5 \times 10^{8} M_{\odot}$ in steps of $0.1 \times 10^{8} M_{\odot}$" (3.4)
   - parameter: kinematic PA 130±5 deg; velocity error = channel width 3.284 km/s plus Gaussian fit error  
  > "is defined to be a sum in quadrature of the channel width (3.284 km s$^{-1}$) and the error from Gaussian fitting" (3.4)
   - fitting: chi-square grid, 2 free parameters, 104 dof, polynomial fit to Delta chi2  
  > "Note that the degree of freedom becomes 104, because we have two free parameters" (3.4)
   - validation: Repeated with HCO+, F190N profile, and inclination 51 deg  
  > "We therefore repeat our method using the ${\rm HCO}^{+} (J=1-0)$ emission line." (4.3)

## Software

- **CASA** 4.0: data reduction and imaging  
  > "reduced and imaged using CASA (Common Astronomy Software Applications) 4.0" (2 Observations and Data Reduction)
- **Karma** : moment 0 and 1 maps  
  > "made using Karma (cite: 1996ASPC..101...80G)" (2 Observations and Data Reduction)
- **MGE_circular_velocity (JAM package)** : circular velocity from MGE potential  
  > "We use MGE_circular_velocity code, which is in the JAM modelling package of (cite: 2008MNRAS.390...71C)." (3.2)
- **KinMS** : PVD modelling with beam smearing  
  > "The observational effects are taken into account by utilizing KinMS (cite: 2013Natur.494..328D)." (3.3)
- **Tiny Tim** 6.3: check HST PSF  
  > "The PSF is also checked by using “Tiny Tim" package (version 6.3)" (3.1 The Mass Model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SMBH mass (HCN, i=46 deg) | 1.40e8 | +0.27/-0.32 e8 | Msun | 4 | the SMBH mass is thus estimated to be $1.40^{+0.27}_{-0.32} \times 10^{8} M_{\odot}$ |
| I-band M/L | 5.14 | +0.03/-0.04 | Msun/Lsun | 4 | The M/L ratio is estimated to be $5.14^{+0.03}_{-0.04}$ |
| Minimum chi-square | 113 (reduced 1.09) | not stated | dimensionless | 4 | The smallest chi-square value of 113 (reduced chi-square value is 1.09 when divided with the degree of freedom) |
| SMBH mass (HCO+, i=46 deg) | 1.40e8 | ±0.30e8 | Msun | 4 | estimate the SMBH mass to be $(1.40 \pm 0.30) \times 10^{8} M_{\odot}$ |
| SMBH mass at i=51 deg | 1.20e8 | +0.35/-0.34 e8 | Msun | 4 | evaluate the SMBH mass to be $1.20^{+0.35}_{-0.34} \times 10^{8} M_{\odot}$ |

## Qualitative findings

- Dust extinction in F814W is not serious for the mass measurement  
  > "We therefore conclude that the dust extinction effect with the F814W filter is not too serious for the measurement of the SMBH mass." (4.1)

## Claim tuples

- H: Dense gas kinematics with ALMA can measure the SMBH mass of NGC 1097 | E: PVD fit of HCN J=1-0 with MGE+KinMS model | R: M_BH=1.40e8 Msun, M/L=5.14 | F: SMBH mass measured, consistent with M-sigma | **supported**
- H: Result is independent of molecular tracer | E: Repeat with HCO+ J=1-0 | R: 1.40±0.30e8 Msun, M/L 5.15 | F: Consistent between lines | **supported**

## Reasoning

- Why this data: HCN used because of highest SNR  
  > "Our main result is obtained using the HCN line because it had the highest signal-to-noise ratio (SNR)." (4.3)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Inclination uncertainty and possible warp or asymmetry not modelled  
  > "this galaxy could have a warped or a misaligned structure, which could be interesting to investigate but requires a calculation for an asymmetric potential field." (4.2)
- Caveat (inferred, ours): Resolution (~112-154 pc) does not resolve the BH sphere of influence
- Caveat (inferred, ours): Only a major-axis PVD and 106 points with 2 free parameters; the inclination uncertainty is not propagated
- Caveat (inferred, ours): Quoted 3 sigma errors; gas treated as thin axisymmetric disk despite non-circular motions

## Reproducibility

- Data public (paper): ALMA Cycle 0 project cited; HST archive data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00108.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Calibration and continuum subtraction details
- Missing: KinMS gas distribution settings
- Missing: HST image processing details
- Data volume (inferred): ~10-30 GB raw Cycle 0 Band 3 data
- Score (inferred): 3/5, Public data and a clear chi-square grid, but KinMS and calibration settings are unspecified.
- Rediscovery candidate: yes, Public Cycle 0 data, a numeric answer (M_BH, M/L), and a mostly described recipe.

## Links

- Method: Davis et al. 2013 (cite: 2013Natur.494..328D) (KinMS and molecular-gas SMBH method)
- Method: Cappellari et al. 2002 (cite: 2002ApJ...578..787C) (MGE potential)
- Companion: Izumi et al. 2013 (cite: 2013PASJ...65..100I) (HCN J=4-3 study of NGC 1097)
- Companion: Fathi et al. 2013 (cite: 2013ApJ...770L..27F) (non-circular motions in the same data)
- Related: S4G

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2011.0.0108.S"
 ],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 45,
  "rate": 0.608
 },
 "evidence_ok": true
}
```
