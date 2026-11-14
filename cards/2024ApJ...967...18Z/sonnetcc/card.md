# Magnetic Field of Molecular Gas Measured with the Velocity Gradient Technique. II. Curved Magnetic Field in kpc-scale Bubble of NGC 628

`2024ApJ...967...18Z` | The Astrophysical Journal 2024 | first author: Zhao, Mengke | arXiv: 2404.02651 | DOI: 10.3847/1538-4357/ad3a62

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, milky_way_ism
- Question: Does the magnetic field traced by the Velocity Gradient Technique on PHANGS-ALMA 12CO(2-1) in NGC 628 align with the spiral arms and curve around kpc-scale bubbles seen in JWST mid-infrared emission?  
  > "In this work, we aim to study the magnetic field in and around the bubbles structures of the spiral galaxy NGC 628 at the distance of 7.3 Mpc (cite: 2004AJ....127.2031K)" (1 Introduction); "The large-scale magnetic field is oriented parallel to the spiral arms and curves around the galactic bubble structures in the mid-infrared emission observed by the James Webb Space Telescope (JWST)." (abstract)
- Target **NGC 628**: coordinates _not stated_; z/distance 7.3 Mpc  
  > "In this work, we aim to study the magnetic field in and around the bubbles structures of the spiral galaxy NGC 628 at the distance of 7.3 Mpc (cite: 2004AJ....127.2031K)" (1 Introduction); distance from (cite: 2004AJ....127.2031K)  
  > "In this work, we aim to study the magnetic field in and around the bubbles structures of the spiral galaxy NGC 628 at the distance of 7.3 Mpc (cite: 2004AJ....127.2031K)" (1 Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1.12'' (FWHM ~53.5 pc); velocity resolution ~2.5 km/s  
  > "The spatial resolution for NGC 628 is $\sim$ 1.12$''$ (FWHM $\sim$ 53.5 pc) and the velocity resolution is around 2.5 km s$^{-1}$ (cite: 2021ApJS..257...43L)." (2.1 The spectral line emission)
- max recoverable scale: _not stated_
- sensitivity: RMS noise ~0.30 +/- 0.13 K km/s  
  > "high signal-to-noise ratio data with the RMS noise level of $\sim$ 0.30 $\pm$ 0.13 K km s$^{-1}$." (2.1 The spectral line emission)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival data from the PHANGS-ALMA survey  
  > "The details of the archival data are shown in Section [2](#sect2)." (1 Introduction); "The spectral cube data comes from the PHANGS-ALMA survey (cite: 2021ApJS..257...43L), which includes 90 nearby galaxies" (2.1 The spectral line emission)
- Line: 12CO J=2-1 (not stated)
- Other facility **JWST MIRI (Early Release Observations)**: Mid-infrared continuum (F770W, F1000W, F1130W, F2100W) showing bubble structures  
  > "The filters F770W (7.7 $\mu$m), F1000W (10 $\mu$m), F1130W (11.3 $\mu$m), and F2100W (21 $\mu$m) from the JWST Mid Infrared Instrument (MIRI) will be used in this work." (2.2 The continuum emission)
- Other facility **PHANGS-MUSE (VLT)**: OIII emission used to trace shocks  
  > "In addition, the OIII emission in NGC 628 has been selected to trace the shocks, which comes from the PHANGS-MUSE Survey (cite: 2022A&A...659A.191E) with a sub-arcsec beam scale size." (2.1 The spectral line emission)
- Other facility **JVLA S-band**: Synchrotron polarization B-field orientations at 3.1 GHz, ~18'' resolution, used for comparison with VGT  
  > "compared with previously determined B-field structures derived from synchrotron polarization ($\sim$ 18$''$) with JVLA at 3.1 GHz (cite: 2017A&A...600A...6M)" (4.3 Comparison of the B-fields from VGT and from Synchrotron Polarization)
- External data: Catalog of bubbles in NGC 628 (diameters 12 to 1164 pc); 21 large bubbles selected from it, and a 1694-bubble sample used for size and galactocentric distance distributions  
  > "From the bubble catalog of (cite: 2023ApJ...944L..24W),we have identified 21 sizable bubbles exceeding twice the beam width of the magnetic field measured with VGT" (4.2 Bubbles in extragalactic sources); "A more complete sample of bubbles in NGC 628 includes 1694 bubbles with different sizes and is provided by (cite: 2023ApJ...944L..24W)." (5.2 Bubble Size and Galactic Distribution) [from Watkins et al. 2023 (cite: 2023ApJ...944L..24W)]
- External data: JVLA 3.1 GHz synchrotron polarization data used to derive the B-field orientation for comparison  
  > "compared with previously determined B-field structures derived from synchrotron polarization ($\sim$ 18$''$) with JVLA at 3.1 GHz (cite: 2017A&A...600A...6M)" (4.3 Comparison of the B-fields from VGT and from Synchrotron Polarization) [from Mulcahy, Beck & Heald 2017 (cite: 2017A&A...600A...6M)]
- External data: Distance to NGC 628 of 7.3 Mpc  
  > "In this work, we aim to study the magnetic field in and around the bubbles structures of the spiral galaxy NGC 628 at the distance of 7.3 Mpc (cite: 2004AJ....127.2031K)" (1 Introduction) [from Karachentsev et al. 2004 (cite: 2004AJ....127.2031K)]
- External data: PHANGS-ALMA 12CO(2-1) spectral cube of NGC 628  
  > "The spectral cube data comes from the PHANGS-ALMA survey (cite: 2021ApJS..257...43L), which includes 90 nearby galaxies" (2.1 The spectral line emission) [from Leroy et al. 2021 (cite: 2021ApJS..257...43L)]

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

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.2''  
  > "Using the VGT technique, the magnetic field is derived at a scale of 191 pc ($\sim$ 4$''$) with the sub-block size set at 20$\times$20 pixels and with a pixel size of the $^{12}$CO emission of 0.2$''$." (4.1 The magnetic fields in NGC 628)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ~1.12'' (FWHM ~53.5 pc)  
  > "The spatial resolution for NGC 628 is $\sim$ 1.12$''$ (FWHM $\sim$ 53.5 pc) and the velocity resolution is around 2.5 km s$^{-1}$ (cite: 2021ApJS..257...43L)." (2.1 The spectral line emission)
- final rms: ~0.30 +/- 0.13 K km/s  
  > "high signal-to-noise ratio data with the RMS noise level of $\sim$ 0.30 $\pm$ 0.13 K km s$^{-1}$." (2.1 The spectral line emission)

### Inherited from earlier work

- Sub-block averaging method for the velocity gradient orientations  
  > "A sub-block averaging (cite: 2017ApJ...837L..24Y) method has been used to export the velocity gradients from the raw gradients within a sub-block of interest" (3.2 The Velocity Gradient Technique) [from (cite: 2017ApJ...837L..24Y)]
- Velocity Decomposition Algorithm used to separate velocity and density contributions  
  > "the Velocity Decomposition Algorithm (VDA) is a new technique that separates the velocity and density contribution from the PPV cube (cite: 2021ApJ...910..161Y)" (3.3 The Velocity Decomposition Algorithm) [from (cite: 2021ApJ...910..161Y)]
- Line integral convolution (LIC) used to display the B-field orientations  
  > "presented as an LIC (cite: Cabral_lic)" (3.2 The Velocity Gradient Technique) [from (cite: Cabral_lic)]
- Alignment Measure used to compare VGT and polarization orientations  
  > "The alignment between the B-field orientations measured with polarization $\theta_B$ and VGT $\Phi_B$ is quantified as the **Alignment Measure** (AM; (cite: 2017ApJ...835...41G)):" (4.3 Comparison of the B-fields from VGT and from Synchrotron Polarization) [from (cite: 2017ApJ...835...41G)]

### Not stated but needed to reproduce (our reading)

- Which PHANGS-ALMA product was used (12m+7m+TP combined cube, moment-masked or broad, native or convolved resolution) and its release version
- How the pixel size of 0.2'' relates to the ~1.12'' beam and whether the cube was resampled or smoothed before the gradient calculation
- Number and velocity range of the thin channels n_v and whether channels were smoothed before computing gradients
- Noise-clipping details beyond S/N > 3 and how gradients at edges of masked regions were handled
- Exact sub-block averaging implementation (histogram bins, peak or mean selection, overlap of blocks)
- Polygon or mask definitions of Bubble 1 and Bubble 2 and the regions used to compute AM
- How the VGT map was smoothed and regridded to the 18'' JVLA map and how the Q/U polarization map was sampled
- OIII intensity map smoothing and threshold used to define the shock front region where VGT orientation is re-rotated by 90 degrees
- Fitting method for the flux versus scale relation (alpha ~ 1), the flux map used, and the aperture definition for each bubble

## Analysis recipe

1. **Select CO cube and thin velocity channels**: Use the PHANGS-ALMA 12CO(2-1) PPV cube as VGT input and treat velocity channels as thin channels  
  > "The input of the VGT technique is the high-resolution position-position-velocity (PPV) data cube of the $^{12}$CO emission in this work." (3.2 The Velocity Gradient Technique)
   - parameter: velocity channel width ~2.5 km/s  
  > "The spatial resolution for NGC 628 is $\sim$ 1.12$''$ (FWHM $\sim$ 53.5 pc) and the velocity resolution is around 2.5 km s$^{-1}$ (cite: 2021ApJS..257...43L)." (2.1 The spectral line emission)
   - fitting: _not stated_
   - validation: _not stated_
2. **Compute per-channel velocity gradient orientations**: Pixelised x and y gradients of each thin channel map, orientation from arctan(grad_y/grad_x), for pixels with S/N > 3  
  > "The (x,y) two-dimensional position will be displayed in the (RA,DEC) plane of the sky for pixels whose spectral line emission has a signal-to-noise ratio greater than 3, which is high enough for credibility." (3.2 The Velocity Gradient Technique)
   - software: VGT
   - parameter: S/N > 3 per pixel  
  > "The (x,y) two-dimensional position will be displayed in the (RA,DEC) plane of the sky for pixels whose spectral line emission has a signal-to-noise ratio greater than 3, which is high enough for credibility." (3.2 The Velocity Gradient Technique)
   - assumption: B-field is perpendicular to the velocity gradient in each sub-region  
  > "The orientation of the magnetic field is perpendicular to the velocity gradient direction in each sub-region." (3.2 The Velocity Gradient Technique)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive B-field orientation map by sub-block averaging**: Sub-block averaging of gradient orientations, pseudo-Stokes Q_g and U_g weighted by channel intensity, psi_g = 0.5 arctan(U_g/Q_g), psi_B = psi_g + 90 deg; displayed with LIC  
  > "The size of the sub-block is set as 20 $\times$ 20 pixels, which determines the size of the final magnetic field resolution." (3.2 The Velocity Gradient Technique)
   - software: VGT
   - parameter: sub-block 20x20 pixels, pixel size 0.2'', B-field scale 191 pc (~4'')  
  > "Using the VGT technique, the magnetic field is derived at a scale of 191 pc ($\sim$ 4$''$) with the sub-block size set at 20$\times$20 pixels and with a pixel size of the $^{12}$CO emission of 0.2$''$." (4.1 The magnetic fields in NGC 628)
   - fitting: _not stated_
   - validation: Compared with synchrotron polarization B-field using AM (step 6)  
  > "We smooth the magnetic field derived by VGT to the same scale as that from JVLA resolution ($\sim$ 18$''$) and compare the two versions of the magnetic field." (4.3 Comparison of the B-fields from VGT and from Synchrotron Polarization)
4. **Refine with Velocity Decomposition Algorithm for the two largest bubbles**: Replace channel intensity with the VDA velocity component before computing gradients, to remove density contribution  
  > "Using these velocity properties $p_v$ to replace the values for Ch(x,y) in Eq. [\[eq.a4\]](#eq.a4) and [\[eq.a5\]](#eq.a5), this VGT-VDA method can trace the magnetic field better." (3.3 The Velocity Decomposition Algorithm)
   - software: VDA
   - parameter: sound speed c_s ~186 m/s from uniform temperature ~10 K  
  > "The velocity of sound $c_s$ can be calculated by assuming a uniform temperature $\sim$ 10 K, which results in a value $c_s$ $\sim$ 186 m s$^{-1}$." (3.3 The Velocity Decomposition Algorithm)
   - assumption: uniform temperature ~10 K  
  > "The velocity of sound $c_s$ can be calculated by assuming a uniform temperature $\sim$ 10 K, which results in a value $c_s$ $\sim$ 186 m s$^{-1}$." (3.3 The Velocity Decomposition Algorithm)
   - fitting: _not stated_
   - validation: AM with polarization higher for VGT-VDA than VGT for both bubbles  
  > "The AM value of Bubble 1 and Bubble 2 is up to 0.74 and 0.64, which is larger than the AM of VGT (Bubble 1 = 0.7 and Bubble 2 = 0.54)." (4.3.2 The B-field at the Bubbles)
5. **Correct VGT orientation at shock fronts**: Where the OIII-traced shock front is parallel to the polarization B-field, re-rotate the VGT orientation by 90 degrees  
  > "The VGT orientation in this region is re-rotated by 90 degrees to achieve the B-field orientation, as dictated by Eq. [\[eqfrontparal\]](#eqfrontparal)." (4.3.2 The B-field at the Bubbles)
   - parameter: OIII smoothed to 18'', intensity over 3e-16 erg cm^-2 s^-1 marks the shock front  
  > "The OIII emission may be smoothed to trace the shock front at a scale of 18$''$, where the intensity is over 3$\times$10$^{-16}$ cm$^{-2}$ erg s$^{-1}$." (4.3.2 The B-field at the Bubbles)
   - fitting: _not stated_
   - validation: AM between the two B-field measures after re-rotation  
  > "By re-rotating the VGT orientation at the shock front, the AM between two measures of magnetic fields is 0.54" (4.3.2 The B-field at the Bubbles)
6. **Compare VGT and synchrotron polarization B-fields with the Alignment Measure**: Smooth VGT field to 18'' and compute AM = 2(<cos^2(theta_B - Phi_B)> - 1/2); uncertainty is standard deviation over square root of sample size  
  > "The uncertainty in the AM value $\sigma_{AM}$ may be given by a standard deviation divided by the square root of the sample size." (4.3 Comparison of the B-fields from VGT and from Synchrotron Polarization)
   - parameter: JVLA B-field orientation theta_B = 0.5 arctan(U,Q) + 0.5 pi  
  > "The orientation of the magnetic field $\theta_B$ derived from the JVLA polarization data are estimated by:" (2.3 The polarization data)
   - fitting: _not stated_
   - validation: _not stated_
7. **Select large-scale bubbles**: From the Watkins et al. catalog keep bubbles larger than twice the B-field beam (~390 pc); exclude the central one, leaving 20 bubbles  
  > "The scale of our structures is all larger than 390 pc, where 390 pc is twice the beam for measuring the magnetic field structure accurately." (4.2 Bubbles in extragalactic sources)
   - parameter: size threshold ~390 pc  
  > "The scale of our structures is all larger than 390 pc, where 390 pc is twice the beam for measuring the magnetic field structure accurately." (4.2 Bubbles in extragalactic sources)
   - fitting: _not stated_
   - validation: _not stated_
8. **Estimate supernova remnant numbers per bubble**: Fit power law between total synchrotron flux and bubble scale (I proportional to R^alpha); estimate N(SNR) = k (R/R_0) with R_0 = 6 pc and k = 1  
  > "Because of the unknown characteristic flux $I_0$, we assume the factor k as 1." (5.3 The origin of large-scale bubbles)
   - parameter: R_0 ~6 pc (maximum single SNR size in the Milky Way)  
  > "We adopt a maximum size of a single SNR in the Milky Way ($\sim$ 6 pc) as the characteristic scale populating the bubbles." (5.3 The origin of large-scale bubbles)
   - assumption: k = 1 because characteristic flux I_0 is unknown  
  > "Because of the unknown characteristic flux $I_0$, we assume the factor k as 1." (5.3 The origin of large-scale bubbles)
   - fitting: Power-law fit of total flux versus bubble scale; method, sampler and priors not stated  
  > "By fitting the total flux and scale of each large-scale bubble, the derived alpha converges around 1 (less than 2)." (5.3 The origin of large-scale bubbles)
   - validation: _not stated_

## Software

- **VGT (Velocity Gradient Technique)** : Measure B-field orientation from velocity gradients of CO thin channel maps  
  > "The velocity gradient technique (VGT; (cite: 2017ApJ...835...41G; 2018ApJ...853...96L; 2018MNRAS.480.1333H)) is the main analysis tool used in this work." (3 Using the VGT Method)
- **VDA (Velocity Decomposition Algorithm)** : Separate velocity and density contributions to improve VGT accuracy  
  > "the Velocity Decomposition Algorithm (VDA) is a new technique that separates the velocity and density contribution from the PPV cube (cite: 2021ApJ...910..161Y)" (3.3 The Velocity Decomposition Algorithm)
- **LIC (line integral convolution)** : Display B-field orientation maps  
  > "presented as an LIC (cite: Cabral_lic)" (3.2 The Velocity Gradient Technique)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| VGT B-field resolution scale in NGC 628 | 191 pc (~4'') | not stated | pc | 3 | Applying the Velocity Gradient Technique (VGT) on CO spectroscopic data from the ALMA-PHANGS, the magnetic field of NGC 628 is measured at the scale of 191 pc |
| Mean AM, VGT versus 3.1 GHz polarization over the disk | 0.53 | not stated | dimensionless | 6 | shows that the mean AM value is approaching 0.53 |
| Mean AM, Bubble 1 (VGT versus polarization) | 0.70 | 0.01 | dimensionless | 6 | By comparison between the magnetic field for VGT and that for polarization, the mean AM is 0.70 ($\pm$ 0.01). |
| AM, Bubble 2 after re-rotating VGT at the shock front | 0.54 | not stated | dimensionless | 5 | By re-rotating the VGT orientation at the shock front, the AM between two measures of magnetic fields is 0.54 |
| AM with VGT-VDA, Bubble 1 and Bubble 2 | 0.74 and 0.64 | not stated | dimensionless | 4 | The AM value of Bubble 1 and Bubble 2 is up to 0.74 and 0.64, which is larger than the AM of VGT (Bubble 1 = 0.7 and Bubble 2 = 0.54). |
| Slope alpha of flux versus scale for large-scale bubbles | ~1 | not stated | dimensionless | 8 | By fitting the total flux and scale of each large-scale bubble, the derived alpha converges around 1 (less than 2). |
| Estimated number of SNRs in Bubble 1 (scale ~1164 pc) | 194 | not stated | dimensionless | 8 | Then the largest bubble, Bubble 1 (scale $\sim$ 1164 pc) contains an estimated 194 SNRs. |
| Peak of bubble size and galactocentric distance distribution (1694 bubbles) | 50 pc and 3 kpc | not stated | pc; kpc | 7 | shows a peak in the extended distribution at a bubble size of 50 pc and at a galacto-centric distance of 3 kpc |

## Qualitative findings

- The large-scale B-field from VGT runs parallel to the spiral arms and curves around bubble shells, matching low-resolution synchrotron polarization  
  > "The large-scale magnetic field is oriented parallel to the spiral arms and curves around the galactic bubble structures in the mid-infrared emission observed by the James Webb Space Telescope (JWST)." (abstract)

## Claim tuples

- H: VGT on PHANGS-ALMA CO traces the same B-field as synchrotron polarization at matched resolution | E: Smooth the VGT B-field to 18'' and compute AM against the JVLA 3.1 GHz polarization field | R: Mean AM approaches 0.53 over the disk; 0.70 for Bubble 1 | F: VGT B-field orientations are nearly parallel to those inferred from synchrotron polarization | **supported**
- H: VGT orientation must be corrected where shocks parallel to B change the velocity gradient | E: Re-rotate VGT by 90 degrees along the OIII-traced shock front of Bubble 2 and recompute AM | R: AM is 0.54 after re-rotation | F: VGT tracing is tested in the shock front region and requires a 90 degree re-rotation there | **partially**
- H: Removing the density contribution (VDA) improves VGT accuracy | E: Apply VGT-VDA to the two largest bubbles and compare AM with VGT alone | R: AM rises to 0.74 (Bubble 1) and 0.64 (Bubble 2) | F: VGT-VDA traces the B-field more accurately than VGT alone | **supported**
- H: Large-scale bubbles are caused by multiple supernovae and shape the local B-field | E: Compare B-field curvature, OIII shocks, mid-IR emission and synchrotron flux scaling for 20 bubbles | R: B-field is curved and parallel to the bubble shells; alpha ~ 1; up to 194 estimated SNRs in Bubble 1 | F: The bubbles are likely produced by multiple supernova explosions and prolonged star formation | **partially**

## Reasoning

- Why this data: PHANGS-ALMA provides high-resolution CO data from which turbulence anisotropy and velocity gradients can be extracted  
  > "The PHANGS-ALMA survey provides high-resolution CO isotopolog data where anisotropies of the turbulence can be extracted and used to trace the velocity gradients of eddies." (1 Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): It is unknown how many supernovae contributed to the typical bubble size  
  > "it is unknown how many SNs actually contributed to this large size." (5.2 Bubble Size and Galactic Distribution)
- Limitation (authors): The characteristic flux I_0 is unknown, so the SNR number estimate assumes k = 1  
  > "Because of the unknown characteristic flux $I_0$, we assume the factor k as 1." (5.3 The origin of large-scale bubbles)
- Caveat (inferred, ours): No uncertainties are given on most AM values, and the AM depends on arbitrary sub-regions and smoothing to 18''.
- Caveat (inferred, ours): The 90 degree re-rotation at shocks is applied only after comparing with polarization, which makes the Bubble 2 AM partly circular.
- Caveat (inferred, ours): SNR counts rest on k = 1 and R_0 = 6 pc and are order-of-magnitude estimates only.
- Caveat (inferred, ours): The paper does not say which PHANGS-ALMA data product, mask or smoothing was used.

## Reproducibility

- Data public (paper): Archival PHANGS-ALMA, PHANGS-MUSE, JWST ERO and JVLA data are cited as survey or published products  
  > "The details of the archival data are shown in Section [2](#sect2)." (1 Introduction)
- Products in archive: _not stated_
- Missing: Exact PHANGS-ALMA cube product and release
- Missing: VGT and VDA code version and parameter files
- Missing: Channel selection, velocity range and noise clipping details
- Missing: Region masks for Bubbles 1 and 2 and for the shock front
- Missing: Flux measurements and fitting details behind alpha and the SNR counts
- Missing: No ALMA project code printed in the paper
- Data volume (inferred): Small (a single PHANGS-ALMA NGC 628 CO(2-1) cube, order of a few GB) plus JWST, MUSE and JVLA maps
- Score (inferred): 2/5, Data are public survey products, but VGT parameters, region definitions and fitting details are not given and no code is released.
- Rediscovery candidate: no, The key results (AM values) depend on unstated masks, smoothing and VGT settings, so the recipe is not complete enough to redo.

## Links

- Method: Yuen & Lazarian 2017 (cite: 2017ApJ...837L..24Y) (Sub-block averaging method for VGT)
- Method: Yuen, Ho & Lazarian 2021 (cite: 2021ApJ...910..161Y) (Velocity Decomposition Algorithm)
- Method: Hu, Lazarian & Wang 2022b (cite: 2022MNRAS.511..829H) (Thin velocity channel map VGT application)
- Method: Leroy et al. 2021 (cite: 2021ApJS..257...43L) (PHANGS-ALMA data reduction and cube products)
- Method: Gonzalez-Casanova & Lazarian 2017 (cite: 2017ApJ...835...41G) (VGT and Alignment Measure definition)
- Companion: Watkins et al. 2023 (cite: 2023ApJ...944L..24W) (Source of the JWST bubble catalog of NGC 628)
- Companion: Mulcahy, Beck & Heald 2017 (cite: 2017A&A...600A...6M) (JVLA 3.1 GHz polarization data used for comparison)
- Companion: Hu et al. 2022a (cite: 2022ApJ...941...92H) (VGT tested on molecular gas in nearby galaxies)
- Companion: Zhao et al. 2022 (cite: 2022ApJ...934...45Z) (VDA improves VGT accuracy)
- Related: PHANGS-ALMA
- Related: PHANGS-MUSE
- Related: JWST Early Release Observations

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00650.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 95,
  "stated": 51,
  "rate": 0.537
 },
 "evidence_ok": true
}
```
