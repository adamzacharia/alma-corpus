# Spatially resolved radio-to-far-infrared SED of the luminous merger remnant NGC 1614 with ALMA and VLA

`2016PASJ...68...20S` | Publications of the Astronomical Society of Japan 2016 | first author: Saito, Toshiki | arXiv: 1512.05133 | DOI: 10.1093/pasj/psv136

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: What are the physical origins of the spatially resolved radio-to-FIR continuum SED of NGC 1614, and how do its sub-kpc star formation relation and gas depletion time compare with other galaxies along the merger sequence?  
  > "In this paper, we focus on the sub-kpc properties of the radio-to-FIR SED of a luminous merger remnant NGC 1614 using ALMA and VLA." (INTRODUCTION)
- Target **NGC 1614**: coordinates _not stated_; z/distance z = 0.015938; D_L = 67.8 Mpc used in the SED fit (68.6 Mpc in the Introduction)  
  > "NGC 1614 is one of the nearby ($D_{\rm{L}}$ = 68.6 Mpc; 1$''$ = 330 pc) gas-rich LIRGs" (INTRODUCTION); "we fix z = 0.015938, $D_{\rm{L}}$ = 67.8 Mpc (cite: xu15)" (SED Formulation for Starburst-dominated Galaxies); distance from Xu et al. 2015 (cite: xu15) for the SED-fit values  
  > "NGC 1614 is one of the nearby ($D_{\rm{L}}$ = 68.6 Mpc; 1$''$ = 330 pc) gas-rich LIRGs" (INTRODUCTION); "we fix z = 0.015938, $D_{\rm{L}}$ = 67.8 Mpc (cite: xu15)" (SED Formulation for Starburst-dominated Galaxies)

## Data provenance

- ALMA projects: 2013.1.01172.S, 2011.0.00182.S, 2011.0.00768.S
- bands: ALMA Bands 3, 6 (Cycle 2), 7, 9 (Cycle 0); VLA C and X bands  
  > "NGC 1614 was observed using ALMA band 7 and band 9 as two cycle 0 programs" (Archival ALMA and VLA Data); "The band 3 and 6 receivers were tuned to the $^{12}$CO (1–0) and $^{12}$CO (2–1) line emission in the upper sideband." (ALMA Observations)
- frequencies and spectral setup: Each spw 1.875 GHz with 3840 channels; two spws per sideband, ~7.5 GHz total coverage (Bands 3 and 6)  
  > "Each spectral window had a bandwidth of 1.875 GHz with 3840 channels, and two spectral windows were set to each sideband to achieve a total frequency coverage of $\sim$ 7.5 GHz." (ALMA Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Band 3: 28-1060 m; Band 6: 15-349 m; Band 7: 18-1341 m; Band 9: 20-394 m  
  > "The band 3 data were obtained on August 30, 2014 (on-source time of $T_{\rm{integ}}$ = 16.9 min.) using the projected baseline lengths of 28 - 1060 m." (ALMA Observations)
- angular resolution: 1.0'' x 1.0'' (convolved)  
  > "We convolved all images into a same beam (1.0$''$ $\times$ 1.0$''$)." (Data Reduction and Imaging)
- max recoverable scale: 4.6'' (~1.5 kpc) after clipping at 45 kλ  
  > "the produced images have a same MRS of 4.6$''$ ($\simeq$ 1.5 kpc)" (Data Reduction and Imaging)
- sensitivity: rms 32, 7.4, 51, 143, 68, 736 uJy at 4.81, 8.36, 108, 233, 352, 691 GHz  
  > "The rms level of 4.81, 8.36, 108, 233, 352, and 691 GHz images (Figure [1](#fig_1)) are 32, 7.4, 51, 143, 68, and 736 $\mu$Jy, respectively." (Data Reduction and Imaging)
- time on source: Band 3 16.9 min; Band 6 22.0 min; Band 7 88.8 min; Band 9 24.7 min  
  > "The band 7 data were obtained on July 31 and August 14, 2012 ($T_{\rm{integ}}$= 88.8 min.)" (Archival ALMA and VLA Data)
- observing dates: Band 3: 2014 Aug 30; Band 6: 2014 Dec 8; Band 7: 2012 Jul 31 and Aug 14; Band 9: 2012 Aug 13 and 28  
  > "The band 6 data were obtained on December 8, 2014" (ALMA Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=1-0 (Band 3 target; line subtracted for continuum) (not stated)
- Line: 12CO J=2-1 (Band 6 target; line subtracted for continuum) (not stated)
- Other facility **VLA**: Archival 4.81 and 8.36 GHz continuum visibilities  
  > "We use the archival calibrated visibility data (see (cite: cnd90), (cite: sch06), (cite: ols10), and (cite: hi14) for the details of the data)." (Archival ALMA and VLA Data)
- Other facility **GBT 91 m**: 4.83 GHz single-dish flux to estimate VLA recovered flux  
  > "A comparison of the 4.81 GHz flux observed by the VLA with the 4.83 GHz flux obtained by the Green Bank 91 m (GBT) telescope (cite: bic95)" (4.81, 8.36, and 108 GHz Emission)
- Other facility **JCMT**: 352 and 691 GHz single-dish fluxes for recovered flux comparison  
  > "relative to those in the James Clerk Maxwell Telescope (JCMT; (cite: dun00; d&e01)) observations are 18 $\pm$ 4 and 27 $\pm$ 4 %, respectively." (233, 352, and 691 GHz Emission)
- External data: z = 0.015938, D_L = 67.8 Mpc, T_d = 35 ± 2 K (from Spitzer/Herschel)  
  > "$T_d$ = 35 $\pm$ 2 K (cite: xu15) which is derived by using Spitzer/MIPS 24 $\mu$m and Herschel 70 - 500 $\mu$m data" (SED Formulation for Starburst-dominated Galaxies) [from (cite: xu15)]
- External data: VV 114, NGC 34, SDP.81 KS-relation data  
  > "compare with similar spatial resolution (0.3 - 0.8 kpc) data of U/LIRGs in the literature (VV 114, NGC 34, and SDP.81; (cite: xu14; hat15; TS15))" (MERGER EVOLUTION ON THE STAR-FORMING RELATION) [from (cite: xu14; hat15; TS15)]
- External data: Nearby spiral galaxy KS data at ~0.75 kpc  
  > "We also make a comparison with $\sim$ 0.75 kpc resolution data of nearby spiral galaxies (cite: big08)." (MERGER EVOLUTION ON THE STAR-FORMING RELATION) [from (cite: big08)]
- External data: Dust absorption coefficient kappa_352 = 0.43 ± 0.04 cm2 g-1  
  > "$\kappa_{352}$ is the dust absorption coefficient (0.43 $\pm$ 0.04 cm$^2$ g$^{-1}$; (cite: l&d01))" (Dust Mass and Gas Surface Density Derivation) [from (cite: l&d01)]
- External data: Gas-to-dust ratio 264 ± 68  
  > "Assuming a gas-to-dust ratio of 264 $\pm$ 68 (cite: wil08)" (Dust Mass and Gas Surface Density Derivation) [from (cite: wil08)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.2.2  
  > "The data processing was accomplished using `CASA` (version 4.2.2; (cite: CASA))." (Data Reduction and Imaging)
- pipeline version: _not stated_
- archive products used as is: Delivered calibrated uv data for Bands 3 and 6; calibrated archival uv data for the others  
  > "We used the delivered calibrated $uv$ data for the band 3 and 6 observations, and the calibrated archival $uv$ data for the others." (Data Reduction and Imaging)
- flux calibrator: Bands 3/6: Uranus; Band 7: Callisto; Band 9: Ceres; VLA C-band: 3C48, 3C138, J0134+329, J0420-013; X-band: 3C48, J0134+329  
  > "For the band 7 and 9 observations, Callisto and Ceres were used for the flux calibration, respectively." (Archival ALMA and VLA Data); "Uranus was used for the flux calibration." (ALMA Observations)
- flux scale uncertainty: 3%, 3%, 5%, 10%, 10%, 15% at 4.81, 8.36, 108, 233, 352, 691 GHz  
  > "The systematic errors of absolute flux calibration are estimated to be 3%, 3%, 5%, 10%, 10%, and 15% for 4.81, 8.36, 108, 233, 352, and 691 GHz, respectively." (Data Reduction and Imaging)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs weighting with robust = 0.5 (per table note)  
  > "“briggs" means Briggs weighting with `robust` = 0.5." (Table notes)
- uv taper: uv data clipped at minimum baseline 45 kλ before imaging  
  > "the minimum baseline of all data shown in this paper is clipped at 45 k$\lambda$ (i.e., minimum baseline of the band 9 observation) before imaging processes" (Data Reduction and Imaging)
- cell size: 0.2''/pixel  
  > "Throughout this paper, the pixel scales of all images are set to 0.2$''$/pixel." (Data Reduction and Imaging)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Strong lines (e.g., CO, CN) excluded by masking ±500 km/s around rest frequencies before continuum imaging  
  > "We subtracted all strong line emission features (e.g., CO and CN) before the imaging of continuum emission by masking the velocity range of $\pm$ 500 km s$^{-1}$ centered on their rest frequencies." (Data Reduction and Imaging)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: All images convolved to a common 1.0'' x 1.0'' beam  
  > "We convolved all images into a same beam (1.0$''$ $\times$ 1.0$''$)." (Data Reduction and Imaging)
- final beam: 1.0'' x 1.0''  
  > "We convolved all images into a same beam (1.0$''$ $\times$ 1.0$''$)." (Data Reduction and Imaging)
- final rms: 32, 7.4, 51, 143, 68, 736 uJy (4.81 to 691 GHz)  
  > "The rms level of 4.81, 8.36, 108, 233, 352, and 691 GHz images (Figure [1](#fig_1)) are 32, 7.4, 51, 143, 68, and 736 $\mu$Jy, respectively." (Data Reduction and Imaging)

### Inherited from earlier work

- Details of archival ALMA Band 7 and 9 data  
  > "We obtained the calibrated archival visibility data from the ALMA archive (see (cite: slw14) and (cite: xu15) for the details of the data)." (Archival ALMA and VLA Data) [from (cite: slw14), (cite: xu15)]
- SED formulation for starburst galaxies  
  > "We modeled the radio-to-FIR continuum emission by using the formulation described in (cite: y&c02)" (SED Formulation for Starburst-dominated Galaxies) [from (cite: y&c02)]
- Dust mass equation  
  > "using the following equation (cite: wil08)" (Dust Mass and Gas Surface Density Derivation) [from (cite: wil08)]
- VV 114 Sigma_H2 and Sigma_SFR derivation  
  > "We used the ALMA CO (1–0) and the miniTAO Paschen $\alpha$ emission to derive the $\Sigma_{\rm{H_2}}$ and $\Sigma_{\rm{SFR}}$ of VV 114, respectively (see (cite: TS15) for details)." (MERGER EVOLUTION ON THE STAR-FORMING RELATION) [from (cite: TS15)]

### Not stated but needed to reproduce (our reading)

- Imaging task/deconvolver, masks, threshold and number of iterations
- Bandpass/phase calibrators for VLA beyond those listed, and the VLA calibration details
- Exact line-free channels and rest frequencies used for the masking
- Priors, sampler/optimizer and likelihood for the SED fit, and which parameters were free per ring
- Exact ring radii and flux-measurement procedure (3 sigma contour vs ring)
- Procedure for converting SFR to Sigma_SFR (area/inclination correction)
- Which D_L (68.6 vs 67.8 Mpc) was used in each calculation
- How Sigma_H2 was derived from dust mass (pixel area, inclination)

## Analysis recipe

1. **Make continuum images matched in uv and beam**: Clip uv at 45 kλ, mask lines ±500 km/s, image and convolve to 1.0'' x 1.0''  
  > "We convolved all images into a same beam (1.0$''$ $\times$ 1.0$''$)." (Data Reduction and Imaging)
   - software: CASA
   - parameter: uv min 45 kλ; pixel 0.2''; Briggs robust 0.5  
  > "Throughout this paper, the pixel scales of all images are set to 0.2$''$/pixel." (Data Reduction and Imaging)
   - assumption: Missing flux negligible for structures smaller than MRS  
  > "we assume that the missing flux effect (i.e., absence of short spacings) is negligible" (Data Reduction and Imaging)
   - fitting: _not stated_
   - validation: Compared recovered flux with single-dish GBT and JCMT fluxes  
  > "The recovered fluxes at 352 and 691 GHz in the ALMA observations relative to those in the James Clerk Maxwell Telescope" (233, 352, and 691 GHz Emission)
2. **Measure source sizes and inclinations**: 2D Gaussian fit in the image plane, deconvolved size, cos i = minor/major  
  > "The source size is derived by fitting a 2D gaussian in the image plane using `imfit` in `CASA`" (4.81, 8.36, and 108 GHz Emission)
   - software: CASA imfit
   - assumption: Circular thin disk geometry  
  > "Assuming a circular disk geometry for simplicity, we estimate the inclination of the disk from the axial ratio" (233, 352, and 691 GHz Emission)
   - fitting: 2D Gaussian least-squares via imfit  
  > "The source size is derived by fitting a 2D gaussian in the image plane using `imfit` in `CASA` as shown in Figure [2](#fig_2)." (RESULTS, 4.81, 8.36, and 108 GHz Emission)
   - validation: Residual images inspected  
  > "All of the residual images show a same strong negative peak at the nuclear position and a same positive ring-like structure" (4.81, 8.36, and 108 GHz Emission)
3. **Build spatially-resolved SED**: Measure flux densities in concentric rings of 0.2'' width from 4.81 to 691 GHz  
  > "by measuring the flux densities contained in concentric rings defined by the width of 0.2$''$" (Spatially-resolved radio-to-FIR SED)
   - fitting: _not stated_
   - validation: Noted adjacent rings are not independent but trend is robust  
  > "We note that the flux values between adjacent rings are not independent because the width of the ring is smaller than the convolved beam." (Spatially-resolved radio-to-FIR SED)
4. **Fit SED with synchrotron + free-free + dust model**: Fit the Yun & Carilli (2002) starburst SED model to each ring  
  > "We modeled the radio-to-FIR continuum emission by using the formulation described in (cite: y&c02)" (SED Formulation for Starburst-dominated Galaxies)
   - parameter: Fixed: z = 0.015938, D_L = 67.8 Mpc, nu_c = 2 THz, T_d = 35 ± 2 K; free: f_nth, alpha, SFR, beta  
  > "we fix z = 0.015938, $D_{\rm{L}}$ = 67.8 Mpc (cite: xu15), $\nu_c$ = 2 THz (cite: y&c02), and $T_d$ = 35 $\pm$ 2 K (cite: xu15)" (SED Formulation for Starburst-dominated Galaxies)
   - assumption: Starburst-dominated, negligible AGN contribution  
  > "This formulation is only valid for starburst-dominated galaxies (i.e., AGN contribution to the radio-to-FIR SED is negligible)" (SED Formulation for Starburst-dominated Galaxies)
   - fitting: _not stated_
   - validation: Compared f_nth, alpha, Sigma_SFR with global fits and Pa-alpha/radio-based estimates  
  > "This is consistent with $f_{\rm{nth}}$ derived by global SED fitting" (SED Formulation for Starburst-dominated Galaxies)
5. **Derive dust mass and molecular gas surface density**: Dust mass from 352 GHz flux (Wilson et al. 2008 equation), then gas via gas-to-dust ratio  
  > "We calculate the dust mass from the 352 GHz (852 $\mu$m) continuum emission assuming that the 352 GHz flux is dominated by the cold dust component" (Dust Mass and Gas Surface Density Derivation)
   - parameter: kappa_352 = 0.43 cm2/g; T_d = 35 K; gas-to-dust 264 ± 68  
  > "Assuming a gas-to-dust ratio of 264 $\pm$ 68 (cite: wil08)" (Dust Mass and Gas Surface Density Derivation)
   - assumption: 352 GHz dominated by cold dust; synchrotron and free-free neglected  
  > "Here, we ignore the $S_{\rm{nth}}$ and the $S_{\rm{ff}}$ contributions to the 352 GHz flux" (Dust Mass and Gas Surface Density Derivation)
   - fitting: _not stated_
   - validation: Compared with CO(6-5)-derived Sigma_H2 and alpha_CO from Sliwa et al.  
  > "The derived $\Sigma_{\rm{H_2}}$ are consistent with the values estimated from the high-resolution CO (6–5) image (cite: xu15)." (Dust Mass and Gas Surface Density Derivation)
6. **Compute gas depletion time and compare KS relation with other galaxies**: tau_gas = Sigma_H2/Sigma_SFR; compare with VV 114, NGC 34, SDP.81 and spirals  
  > "we derive the molecular gas depletion time ($\tau_{\rm{gas}}$ = $\Sigma_{\rm{H_2}}$/$\Sigma_{\rm{SFR}}$ yr)" (MERGER EVOLUTION ON THE STAR-FORMING RELATION)
   - assumption: alpha_CO = 0.8 for the U/LIRG comparison data  
  > "derived by simply assuming a CO luminosity-to-H$_2$ mass conversion factor ($\alpha_{\rm{CO}}$) of 0.8" (MERGER EVOLUTION ON THE STAR-FORMING RELATION)
   - fitting: _not stated_
   - validation: Index of 1.4 argued robust to alpha_CO choice  
  > "Therefore, the index of 1.4 does not change significantly." (MERGER EVOLUTION ON THE STAR-FORMING RELATION)

## Software

- **CASA** 4.2.2: Data processing, imaging, imfit Gaussian fitting  
  > "The data processing was accomplished using `CASA` (version 4.2.2; (cite: CASA))." (Data Reduction and Imaging)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Deconvolved major axis, low frequency (≤108 GHz) | 1.28 (~420 pc) | 0.03 | arcsec | 2 | deconvolved major axis and minor axis of 1.28$''$ $\pm$ 0.03$''$ ($\sim$ 420 pc) |
| Deconvolved minor axis, low frequency | 1.15 (~380 pc) | 0.05 | arcsec | 2 | 1.15$''$ $\pm$ 0.05$''$ ($\sim$ 380 pc) |
| Deconvolved major axis, high frequency (≥233 GHz) | 1.70 (~560 pc) | 0.09 | arcsec | 2 | 1.70$''$ $\pm$ 0.09$''$ ($\sim$ 560 pc) |
| Deconvolved minor axis, high frequency | 1.18 (~390 pc) | 0.13 | arcsec | 2 | 1.18$''$ $\pm$ 0.13$''$ ($\sim$ 390 pc) |
| VLA 4.81 GHz recovered flux fraction | 42 | 8 | % | 1 | suggests that the VLA data recovers 42 $\pm$ 8 % of the total emission |
| ALMA recovered flux at 352 GHz | 18 | 4 | % | 1 | are 18 $\pm$ 4 and 27 $\pm$ 4 %, respectively |
| ALMA recovered flux at 691 GHz | 27 | 4 | % | 1 | are 18 $\pm$ 4 and 27 $\pm$ 4 %, respectively |
| Averaged f_nth | 0.66 | 0.13 | dimensionless | 4 | The derived $f_{\rm{nth}}$ ranges between 0.43 - 1.45 (averaged $f_{\rm{nth}}$ = 0.66 $\pm$ 0.13). |
| Synchrotron spectral index alpha | -0.9 | within error | dimensionless | 4 | The synchrotron spectral index $\alpha$ shows a constant index of $-$0.9 within the error |
| Dust optical depth at 691 GHz (central 1.8'') | 0.06 - 0.21 | not stated | dimensionless | 4 | we found that the $\tau_{\rm{691GHz}}$ is optically thin (0.06 - 0.21) in the nuclear region of NGC 1614 |
| Dust mass range | 3.3e5 - 2.6e6 | not stated | Msun | 5 | The derived dust masses range between 3.3 $\times$ 10$^5$ and 2.6 $\times$ 10$^6$ $M_{\odot}$ |
| Sigma_H2 range | 10^3.0 - 10^3.8 | not stated | Msun pc^-2 | 5 | the surface densities of molecular gas ($\Sigma_{\rm{H_2}}$) are estimated to be in the range 10$^{3.0}$ - 10$^{3.8}$ $M_{\odot}$ pc$^{-2}$ |
| Sigma_SFR range | 10^0.9 - 10^2.1 | not stated | Msun yr^-1 kpc^-2 | 4 | $\Sigma_{\rm{SFR}}$ (= 10$^{0.9 - 2.1}$ $M_{\odot}$ yr$^{-1}$ kpc$^{-2}$) |
| Average gas depletion time, nuclear/ring region | 49 - 77 | not stated | Myr | 6 | (averaged $\tau_{\rm{gas}}$ = 49 - 77 Myr) |
| Average gas depletion time, outer region | 74 - 226 | not stated | Myr | 6 | than the outer region (averaged $\tau_{\rm{gas}}$ = 74 - 226 Myr) |

## Qualitative findings

- Peaks of all continuum maps are ~0.8'' west of the nucleus, owing to the asymmetric starburst ring  
  > "The offset arises due to the asymmetric starburst ring structure (cite: hi14; xu15)." (4.81, 8.36, and 108 GHz Emission)

## Claim tuples

- H: Do low- and high-frequency continuum have different spatial distributions reflecting different physical origins? | E: Gaussian fits and radial profiles of beam- and uv-matched ALMA and VLA images | R: ≤108 GHz is 420 x 380 pc; ≥233 GHz is 560 x 390 pc, elongated N-S | F: Different emission mechanisms dominate low and high frequencies | **supported**
- H: Can the resolved SED be explained by synchrotron, free-free and dust components? | E: Ring-by-ring SED fit with Yun & Carilli model | R: 4.81/8.36 GHz synchrotron, 108 GHz free-free, 352/691 GHz dust | F: Three-component model explains the SED | **supported**
- H: Is gas depletion time in NGC 1614 shorter than in normal disks and a mid-stage merger? | E: Derived resolved KS relation and tau_gas, compared with VV 114, NGC 34, SDP.81, spirals | R: tau_gas 49-77 Myr (ring) and 70-226 Myr (outer), versus ~2 Gyr in normal disks and 0.1-1 Gyr in VV 114 | F: Star formation efficiency increases as the merger stage proceeds | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Used the Li & Draine dust model because kappa from the SED fit has a large error and constant T_d may affect beta  
  > "because the $\kappa_{352}$ derived from the SED fitting has a large error" (Dust Mass and Gas Surface Density Derivation)
- How they decided it was enough: _not stated_
- Limitation (authors): Large fractions of 352 and 691 GHz emission are more extended than the MRS; constant T_d assumed; small sample for KS comparison  
  > "Large amounts of the 352 and 691 GHz emission are more extended than the MRS scale ($\sim$ 1.5 kpc)." (233, 352, and 691 GHz Emission); "High-resolution high-frequency observations are required to constrain the $T_{\rm{d}}$ gradient in the nuclear region of NGC 1614." (Dust Mass and Gas Surface Density Derivation)
- Caveat (inferred, ours): Missing flux (only 18-42% recovered) may bias SED shapes and Sigma_SFR, Sigma_H2
- Caveat (inferred, ours): Fixed T_d = 35 K across rings; likely varies with radius
- Caveat (inferred, ours): Adjacent rings are non-independent, so fit uncertainties are underestimated
- Caveat (inferred, ours): Merger sequence conclusion rests on three-four objects with heterogeneous methods and alpha_CO assumptions
- Caveat (inferred, ours): Ignoring free-free and synchrotron at 352 GHz and SFR driven by the 108 GHz flux are model-dependent

## Reproducibility

- Data public (paper): Archival ALMA data were obtained from the ALMA archive; ALMA data codes listed  
  > "We obtained the calibrated archival visibility data from the ALMA archive" (Archival ALMA and VLA Data)
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust, pixel scale and uv cut
- Missing: SED fit algorithm and ring definitions
- Missing: Calibrated archival VLA visibilities (several epochs, old data)
- Missing: Literature comparison data tables for VV 114, NGC 34, SDP.81
- Data volume (inferred): ~50-200 GB raw for four ALMA bands; plus archival VLA
- Score (inferred): 3/5, ALMA data are public and the SED formulae are given, but imaging and fitting details are sparse and VLA data are archival with complex combination.
- Rediscovery candidate: no, Imaging recipe is incomplete and the fitting procedure is not specified, although the results are numeric.

## Links

- Method: Yun & Carilli 2002 (cite: y&c02) (SED model formulation)
- Method: Wilson et al. 2008 (cite: wil08) (dust mass equation and gas-to-dust ratio)
- Companion: Xu et al. 2015 (cite: xu15) (Prior ALMA Band 9 study of NGC 1614 supplying T_d, z, D_L)
- Companion: Sliwa et al. 2014 (cite: slw14) (Prior ALMA study of NGC 1614 data)
- Companion: Saito et al. 2015 (cite: TS15) (VV 114 ALMA analysis used in the KS comparison)

## Checks

```json
{
 "quotes": 89,
 "quotes_ok": 89,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 60,
  "rate": 0.714
 },
 "evidence_ok": true
}
```
