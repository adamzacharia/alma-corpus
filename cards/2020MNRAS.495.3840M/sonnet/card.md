# A large amount of diffuse molecular gases in the bar of the strongly barred galaxy NGC 1300: cause of the low star formation efficiency

`2020MNRAS.495.3840M` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Maeda, Fumiya | arXiv: 2005.03019 | DOI: 10.1093/mnras/staa1296

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: Does a large amount of diffuse molecular gas in the bar of NGC 1300 (not contributing to star formation) make the star formation efficiency appear low there?  
  > "we investigate the possibility that the presence of a large amount of diffuse molecular gas, which would not contribute to the SF, makes the SFE low in appearance." (abstract)
- Target **NGC 1300**: coordinates 03h19m41s.036, -19d24m40s.00 (J2000, peak of V-band image)  
  > "Distance$^d$ | 20.7 Mpc" (Table 1); "Inclination$^c$ | $50^\circ.2$" (Table 1); z/distance 20.7 Mpc  
  > "Distance$^d$ | 20.7 Mpc" (Table 1); "Inclination$^c$ | $50^\circ.2$" (Table 1); distance from systemic velocity 1511 km/s with Virgo/Great Attractor/Shapley corrections (Mould et al. 2000) and H0 = 73 km/s/Mpc  
  > "Distance$^d$ | 20.7 Mpc" (Table 1); "Inclination$^c$ | $50^\circ.2$" (Table 1)

## Data provenance

- ALMA projects: 2017.1.00248.S, 2015.1.00925.S
- bands: Band 3 (12CO(1-0)); Band 6 (12CO(2-1), ACA)  
  > "We used the Band 3 receiver with the central frequency of 114.664 GHz" (2.2.1 Observations and data reduction); "absolute flux calibration accuracy of $\pm 10$ percent in Band 6" (2.3.1 CO(2-1) emission from ALMA observations)
- frequencies and spectral setup: Band 3 central freq 114.664 GHz, channel 244.1 kHz (~0.64 km/s), bandwidth 468.8 MHz  
  > "channel width of 244.1 kHz ($\sim 0.64~\rm km~s^{-1}$), and bandwidth of 468.8 MHz ($\sim 1225~\rm km~s^{-1}$)" (2.2.1 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: ALMA 12-m (CO 1-0); ACA 7-m + TP (CO 2-1)  
  > "observed with ACA (7-m + TP)" (2.3.1 CO(2-1) emission from ALMA observations)
- configurations: C43-5, about 44 antennas  
  > "We used about 44 antennas with C43-5 configuration" (2.2.1 Observations and data reduction)
- baselines: 15.1 m to 2.5 km  
  > "the projected baseline length ranged from 15.1 m to 2.5 km" (2.2.1 Observations and data reduction)
- angular resolution: 0.44 x 0.30 arcsec (CO 1-0 ALMA); 7.6 x 4.1 arcsec (CO 2-1 ACA)  
  > "The data cube has an angular resolution of $0.44~{\rm arcsec} \times 0.30~{\rm arcsec}$" (2.2.1 Observations and data reduction)
- max recoverable scale: ~21.4 arcsec at 115 GHz (2.14 kpc)  
  > "which corresponds to a maximum recoverable scale (MRS) of $\sim 21.4$ arcsec at 115 GHz" (2.2.1 Observations and data reduction)
- sensitivity: 0.51 mJy/beam (0.36 K) at 5 km/s (CO 1-0); 11.0 mJy/beam per 10 km/s (CO 2-1)  
  > "The resultant rms noise is 0.51 $\rm mJy~beam^{-1}$, corresponding to 0.36 K." (2.2.1 Observations and data reduction)
- time on source: 5.31 hours (2.65 h per position), two pointings  
  > "The total on-source time was 5.31 hours (2.65 hours for each position)." (2.2.1 Observations and data reduction)
- observing dates: _not stated_
- pi or archival as stated: 2017.1.00248.S PI F. Maeda; 2015.1.00925.S archival, proposed by B. Guillermo et al.  
  > "using the archival data which was observed with ACA (7-m + TP) under project 2015.1.00925.S" (2.3.1 CO(2-1) emission from ALMA observations)
- Line: 12CO J=1-0 (115.271202 GHz)
- Line: 13CO J=1-0 (110.201353 GHz)
- Line: 12CO J=2-1 (230.538000 GHz)
- Other facility **NRO 45-m (FOREST, SAM45)**: Total 12CO(1-0) and 13CO(1-0) maps via OTF mapping  
  > "employing the on-the-fly (OTF) mapping mode" (2.1.1)
- Other facility **HST ACS (proposal 10342)**: F555W and F658N images for Halpha SFR  
  > "archival images observed with the ACS on the HST (proposal ID = 10342, PI = K. Noll)" (2.3.2)
- Other facility **GALEX**: FUV image for SFR  
  > "we also use GALEX FUV" (2.3.3)
- Other facility **WISE**: 22 micron image for SFR  
  > "WISE 22 $\mu$m (cite: Wright2010AJ) archival data" (2.3.3)
- External data: GMC catalogue of 233 GMCs in NGC 1300 used for Sigma_GMC  
  > "The $\Sigma_{\rm GMC}$ is derived using the GMC catalogue in NGC 1300 obtained by (cite: Maeda2020MNRAS)." (5.2) [from (cite: Maeda2020MNRAS)]
- External data: HI image used to assume H2/(HI+H2)=0.7  
  > "Comparing the HI image (cite: England1989a) and H$_2$ map we obtained, we assume $\Sigma_{\rm H_2}/(\Sigma_{\rm H_I}+\Sigma_{\rm H_2}) = 0.7$." (3.2.2) [from (cite: England1989a)]
- Simulation/model as data: Noise-free simobserve simulation of circular Gaussian (1 Jy, FWHM 100-2200 pc) in the same ALMA configuration to get recovery fraction vs size  
  > "we simulated the observation under the same configuration and noise-free condition by using the task of `simobserve` in CASA." (2.2.2 Missing flux)

## Processing

### Calibration

- pipeline or manual: Observatory-provided calibration script  
  > "Raw visibility data was calibrated by using the Common Astronomy Software Applications (CASA) ver. 5.1.1. and the observatory-provided calibration script." (2.2.1)
- casa version: CASA 5.1.1 (calibration); 5.4.0 (imaging)  
  > "We reconstructed the two-field mosaic image using CASA ver. 5.4.0" (2.2.1)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ±5% Band 3; ±10% Band 6  
  > "we consider the absolute flux calibration accuracy of $\pm 5$ percent in Band 3" (2.2.1)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: multiscale CLEAN  
  > "using the `multiscale` CLEAN algorithm (cite: Cornwell2008)" (2.2.1)
- weighting robust: Briggs robust = 0.5 (both CO 1-0 and CO 2-1)  
  > "with Briggs weighting with robust = 0.5" (2.2.1)
- uv taper: _not stated_
- cell size: 0.12 arcsec  
  > "a pixel size of 0.12 arcsec" (2.2.1)
- image size: _not stated_
- masking: 3D mask: S/N>=4 in at least two adjacent channels, expanded to adjacent pixels with S/N>=2  
  > "we first identify the 3D (position-position-velocity) regions with a signal-to-noise ratio (S/N) $\geq$ 4 in at least two adjacent velocity channels." (2.2.1)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Applied; region with correction factor < 2.0 kept  
  > "we extracted the region within the primary beam correction factor smaller than 2.0" (2.2.1)
- array combination: CO(2-1) 7-m image feathered with TP image  
  > "The resulting image is feathered with the total power image to recover the extended emission." (2.3.1)
- smoothing: Convolved to common 16.7 arcsec beam, regridded to 6.0 arcsec pixels  
  > "Then, we convolved this data cube to the common beam size of 16.7 arcsec." (2.2.1)
- final beam: 16.7 arcsec (common)  
  > "which have the poorest beam size of $16.7$ arcsec" (2.1.1)
- final rms: 0.51 mJy/beam at 5 km/s (native resolution)  
  > "The resultant rms noise is 0.51 $\rm mJy~beam^{-1}$" (2.2.1)

### Inherited from earlier work

- ALMA CO(1-0) observations and data reduction details  
  > "The details of the observations of $^{12}{\rm CO}(1-0)$ line with ALMA and data reduction of them are described in Section 2 in (cite: Maeda2020MNRAS)." (2.2.1) [from (cite: Maeda2020MNRAS)]
- Adopted galaxy parameters  
  > "which is the same as those in (cite: Maeda2020MNRAS)" (1 Introduction) [from (cite: Maeda2020MNRAS)]
- Halpha continuum subtraction method  
  > "adopting a method developed by (cite: Boker1999ApJS)" (2.3.2) [from (cite: Boker1999ApJS)]
- Stacking with velocity alignment  
  > "stacking analysis of CO spectra with velocity axis alignment devised by (cite: Schruba2011AJ; Schruba2012AJ)" (3.3 Stacking Analysis) [from (cite: Schruba2011AJ; Schruba2012AJ)]

### Not stated but needed to reproduce (our reading)

- Multiscale scales, cleaning threshold, niter and mask for the CO(1-0) tclean
- Line-free channels / continuum subtraction for ALMA CO cubes
- Calibration and imaging details (and image parameters) for the ACA CO(2-1) data and feathering
- Exact definition of pixel grid origin and environment masks (only in figure)
- Spectral smoothing details for CO(2-1)
- Number of Gaussian-simulation parameters (e.g. pixel scale, direction) for simobserve

## Analysis recipe

1. **Make total CO(1-0) map from NRO 45-m**: OTF data reduced with NOSTAR: flag, baseline subtract (2nd order), regrid to 6 arcsec, bin to 20 km/s, convert to Tmb; integrate channels above 3 sigma expanded to 1 sigma  
  > "a baseline (second-order polynomial function with small curvature) was subtracted, and the data were regridded to 6.0 arcsec per pixel" (2.1.1)
   - software: NOSTAR
   - parameter: main beam efficiency 35 ± 3 percent  
  > "using the main beam efficiency of $35 \pm 3$ percent" (2.1.1)
   - fitting: _not stated_
   - validation: Compared with single-pointing NRO data of Maeda et al. 2018; agreement within factor 1.5  
  > "may contain systematic errors up to a factor of 1.5" (2.1.3)
2. **Image ALMA CO(1-0) and CO(2-1) and match resolution**: CASA calibration and multiscale CLEAN mosaic; convolve to 16.7 arcsec, mask, regrid to 6 arcsec  
  > "Finally, we regrided this data cube to 6.0 arcsec grid." (2.2.1)
   - software: CASA
   - parameter: robust = 0.5; 5 km/s channels  
  > "We chose a velocity resolution of $5~\rm km~s^{-1}$." (2.2.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Quantify ALMA recovery vs source size**: simobserve of mock Gaussian components of 1 Jy, FWHM 100-2200 pc, noise-free, same configuration  
  > "The FWHM was set from 100 pc to 2200 pc in 100 pc interval." (2.2.2)
   - software: CASA simobserve
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive SFR surface density**: Halpha from HST F658N with F555W-scaled continuum subtraction (robust Tukey biweight regression, W=4) per environment; [NII] correction 0.79; Av=1 mag; Calzetti+2007 conversion. Alternative FUV+22um hybrid (Casasola+2017) with old-star 22um correction  
  > "We use Tukey’s biweight to down-weight outliers" (2.3.2)
   - parameter: Av = 1.0 mag; C_NII = 0.79; alpha 5.3e-42 conversion  
  > "we assumed an extinction of $A_{\rm V} = 1.0$ mag" (3.2.1)
   - assumption: H2/(HI+H2) = 0.7 for old-star 22 micron correction  
  > "we assume $\Sigma_{\rm H_2}/(\Sigma_{\rm H_I}+\Sigma_{\rm H_2}) = 0.7$" (3.2.2)
   - fitting: Iterative Tukey biweight robust least squares of f_F658N vs f_F555W  
  > "This is repeated until $a$ and $b$ are converged." (2.3.2)
   - validation: Compared SFR(Halpha) and SFR(IR); differ by factors <2 above 1e-3 Msun/yr/kpc2  
  > "the magnitude of systematic differences rarely exceeds a factor of two (0.3 dex)" (3.2.3)
5. **Stack spectra per environment**: Shift CO(1-0) and 13CO spectra by CO(2-1) intensity-weighted velocity and average in each environment; ALMA CO(1-0) uses pixel mean  
  > "Then, the $^{12}$CO($1-0$) spectra are shifted along the velocity axis based on the $\bar{v}_{\rm CO(2-1)}$." (3.3)
   - fitting: _not stated_
   - validation: _not stated_
6. **Compute Sigma_mol, SFE, f_dif, R21/10**: Sigma_mol = alpha_CO I cos i; SFE = Sigma_SFR/Sigma_H2; f_dif = 1 - I_ALMA/I_tot; R21/10 = I(2-1)/I(1-0)  
  > "f_{\rm dif} = 1 - f_{\rm re} = 1 -  \frac{I_{\rm ^{12}CO(1-0)}^{\rm ALMA}}{I_{\rm ^{12}CO(1-0)}^{\rm tot}}" (4.2)
   - parameter: alpha_CO = 4.4 Msun (K km/s pc2)^-1 including helium factor 1.36; inclination 50.2 deg  
  > "we adopt the standard $\alpha_{\rm CO}$ of 4.4 $M_\odot (\rm K~km~s^{-1}~pc^2)^{-1}$ including a factor of 1.36" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
7. **SFE excluding diffuse gas using GMC catalogue**: SFE_GMC = Sigma_SFR(Halpha)/Sigma_GMC using total GMC mass in each environment from Maeda2020 CPROPS catalogue  
  > "We first measured the total mass of the GMCs in the environments, and then divided it by the area of the environment." (5.2)
   - software: CPROPS
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.1 (calibration), 5.4.0 (imaging): Calibration, multiscale CLEAN imaging, simobserve, feathering  
  > "We reconstructed the two-field mosaic image using CASA ver. 5.4.0" (2.2.1)
- **NOSTAR** : NRO 45-m OTF data analysis  
  > "The observed data were analyzed using the software package NOSTAR (cite: Sawada2008PASJ)" (2.1.1)
- **CPROPS** : GMC identification in the catalogue used (Maeda 2020)  
  > "Using 3D clumps finding algorithm CPROPS (cite: RosolowskyLeroy)" (5.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| f_dif in bar regions | 0.74-0.91 | 0.07-0.10 | dimensionless | 6 | The $f_{\rm dif}$ and ${\rm SFE}$ are $0.74 - 0.91$ and $(0.06 - 0.16) ~\rm Gyr^{-1}$ in the bar regions |
| SFE in bar regions | 0.06-0.16 | 0.02-0.04 | Gyr^-1 | 6 | $(0.06 - 0.16) ~\rm Gyr^{-1}$ in the bar regions |
| f_dif in arm and bar-end regions | 0.28-0.65 | 0.02-0.06 | dimensionless | 6 | $0.28 - 0.65$ and $(0.23 - 0.96) ~\rm Gyr^{-1}$ in the arm and bar-end regions |
| SFE in arm and bar-end regions | 0.23-0.96 | not stated | Gyr^-1 | 6 | $0.28 - 0.65$ and $(0.23 - 0.96) ~\rm Gyr^{-1}$ in the arm and bar-end regions |
| SFE_GMC in bar-B | 0.17 | 0.04 | Gyr^-1 | 7 | ${\rm SFE}_{\rm GMC}$ / ($\rm Gyr^{-1}$) / $<0.04$ / $0.17 \pm 0.04$ |
| NRO 45-m 12CO(1-0) rms | 13.9 | not stated | mK (20 km/s bin) | 1 | The resultant rms noise is 13.9 mK and 7.7 mK for $^{12}$CO($1-0$) and $^{13}$CO($1-0$), respectively |
| Size above which more than half of ALMA flux is missed | FWHM >= 700 pc | not stated | pc | 3 | For the large Gaussian component with the FWHM $\geq 700$ pc, more than half of the flux is missed. |

## Qualitative findings

- SFE decreases with increasing f_dif; tighter with FUV+22um tracer  
  > "A tighter relationship is seen when using the FUV and 22$\mu$m as an SFR tracer rather than using H$\alpha$ emission." (4.3)
- R21/10 is lowest in bar and anticorrelates with f_dif  
  > "This tendency is the opposite of $f_{\rm dif}$" (5.1)
- No 13CO(1-0) detected in any environment  
  > "we did not detect the significant $^{13}$CO($1-0$) emission line in any environments" (3.3)

## Claim tuples

- H: Diffuse molecular gas makes bar SFE appear low | E: Compared f_dif (1 - ALMA/NRO flux) with SFE per environment | R: Bar f_dif 0.74-0.91 with SFE 0.06-0.16 Gyr^-1; arm/bar-end f_dif 0.28-0.65, SFE 0.23-0.96 | F: SFE decreases with f_dif, supporting diffuse gas as a cause | **supported**
- H: Diffuse gas alone explains the low bar SFE | E: SFE_GMC using only GMC-bound gas | R: SFE_GMC still lower in bar (0.17 and <0.04 vs ~1.6 in arms) | F: Other mechanisms such as fast CCCs also needed | **partially**

## Reasoning

- Why this data: ALMA 12-m lacking ACA is insensitive to extended gas, so combined with NRO total flux it measures diffuse fraction  
  > "which has no sensitivity on extended molecular gases due to lack of Atacama Compact Array (ACA; 7-m + TP) data" (1 Introduction)
- Why this method: _not stated_
- Alternative: Unbound clouds (virial parameter) scenario disfavoured by Maeda 2020 and Fujimoto 2020  
  > "these results suggest that the SF suppression in the bar can not be explained by a systematic difference of virial parameter." (5.2)
- How they decided it was enough: _not stated_
- Limitation (authors): alpha_CO may be a factor of a few lower in the bar, so Sigma_mol could be overestimated  
  > "there is a possibility that the $\Sigma_{\rm mol}$ in the bar regions of NGC 1300 may be overestimated by a factor of a few" (3.1)
- Limitation (authors): SFR below 1e-3 Msun/yr/kpc2 should be considered upper limits  
  > "should be considered to be an upper limit" (3.2.3)
- Caveat (inferred, ours): f_dif depends on a single ALMA configuration's uv coverage; compact-source vs extended structure is not unique
- Caveat (inferred, ours): NRO calibration uncertainty (factor up to 1.5) is large compared with differences in f_dif
- Caveat (inferred, ours): Assumed constant Av and alpha_CO across environments
- Caveat (inferred, ours): Only seven environment-averaged points, one galaxy

## Reproducibility

- Data public (paper): Archival ALMA and HST/GALEX/WISE; ALMA codes given; NRO data observed by authors  
  > "We made a map of $^{12}$CO($2-1$) (rest frequency: 230.538000 GHz) emission using the archival data" (2.3.1)
- Products in archive: _not stated_
- Missing: NRO 45-m data availability and environment mask definitions
- Missing: Multiscale scales and clean thresholds
- Missing: GMC catalogue from Maeda 2020
- Missing: ACA CO(2-1) calibration/imaging details
- Data volume (inferred): ~100-300 GB raw ALMA (12-m Band 3 plus ACA), plus small archival optical/UV/IR images
- Score (inferred): 5/5, Main recipe is clear and numbers tabulated, but ALMA reduction is deferred to a previous paper and NRO data and masks are not public/specified.
- Rediscovery candidate: no, Requires NRO 45-m data not clearly public and inherited reduction from Maeda 2020.

## Links

- Method: (cite: Maeda2020MNRAS) (ALMA CO(1-0) observation and reduction details; GMC catalogue)
- Method: (cite: Boker1999ApJS) (Halpha continuum subtraction method)
- Method: (cite: Schruba2011AJ) (stacking with velocity alignment)
- Companion: (cite: Maeda2020MNRAS) (ALMA GMC study of NGC 1300)
- Companion: (cite: Fujimoto2020MNRAS) (hydrodynamical simulation of NGC 1300 with fast cloud-cloud collisions)

## Checks

```json
{
 "quotes": 82,
 "quotes_ok": 82,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 89,
  "stated": 63,
  "rate": 0.708
 },
 "evidence_ok": true
}
```
