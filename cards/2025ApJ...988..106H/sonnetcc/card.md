# Grand Design Spiral Arms in the Compact, Embedded Protoplanetary Disk of Haro 6-13

`2025ApJ...988..106H` | The Astrophysical Journal 2025 | first author: Huang, Jane | arXiv: 2506.06433 | DOI: 10.3847/1538-4357/ade1d8

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Does the compact Haro 6-13 disk host millimeter continuum spiral arms at ~5 au resolution, and what could form them (gravitational instability, infall, companions, flybys)?  
  > "Millimeter continuum spiral arms have so far only been detected in a handful of protoplanetary disks, and thus we have a limited understanding of the circumstances in which they can form." (abstract); "To investigate the nature of the substructures in the Haro 6-13 disk, we used ALMA to obtain high angular resolution 1.3 mm continuum observations." (Introduction)
- Target **Haro 6-13**: coordinates ICRS RA=04:32:15.417, DEC=+24:28:59.58  
  > "Haro 6-13 (ICRS coordinates RA=04:32:15.417, DEC= +24:28:59.58) is a K5.5 T Tauri star" (Introduction); "located $127.7\substack{+1.7\\-1.6}$ pc away in the Taurus Molecular Cloud complex (cite: 2014ApJ...786...97H; 2021AA...649A...1G; 2021AJ....161..147B)" (Introduction); z/distance 127.7 +1.7/-1.6 pc  
  > "Haro 6-13 (ICRS coordinates RA=04:32:15.417, DEC= +24:28:59.58) is a K5.5 T Tauri star" (Introduction); "located $127.7\substack{+1.7\\-1.6}$ pc away in the Taurus Molecular Cloud complex (cite: 2014ApJ...786...97H; 2021AA...649A...1G; 2021AJ....161..147B)" (Introduction); distance from (cite: 2014ApJ...786...97H; 2021AA...649A...1G; 2021AJ....161..147B)  
  > "Haro 6-13 (ICRS coordinates RA=04:32:15.417, DEC= +24:28:59.58) is a K5.5 T Tauri star" (Introduction); "located $127.7\substack{+1.7\\-1.6}$ pc away in the Taurus Molecular Cloud complex (cite: 2014ApJ...786...97H; 2021AA...649A...1G; 2021AJ....161..147B)" (Introduction)

## Data provenance

- ALMA projects: 2022.1.01365.S, 2016.1.01042.S
- bands: 1.3 mm continuum (both programs)  
  > "Long-baseline 1.3 mm continuum observations of Haro 6-13 were obtained as part of ALMA program 2022.1.01365.S (PI: J. Huang)." (2 Observations and Data Reduction)
- frequencies and spectral setup: 2022.1.01365.S: four SPWs at 224, 226, 240, 242 GHz, 128 channels each over 2 GHz. 2016.1.01042.S: 8 SPWs incl. 232.4 and 217.0 GHz (2 GHz, 128 ch) and 468.75 MHz SPWs covering 12CO, 13CO, C18O J=2-1  
  > "The correlator was configured with four spectral windows (SPWs) centered at 224, 226, 240, and 242 GHz, each of which had 128 channels across a bandwidth of 2 GHz." (2 Observations and Data Reduction); "The correlator was configured with 8 SPWs. Two SPWs were centered at 232.4 and 217.0 GHz, respectively, each with bandwidths of 2 GHz and 128 channels." (2 Observations and Data Reduction)
- continuum bandwidth: 2022.1.01365.S: four 2 GHz SPWs  
  > "each of which had 128 channels across a bandwidth of 2 GHz." (2 Observations and Data Reduction)
- arrays: _not stated_
- configurations: 2022.1.01365.S long-baseline; a more compact configuration was requested but not taken, so 2016.1.01042.S was used for short baselines  
  > "Observations in a more compact antenna configuration were requested as part of the same program but ultimately were not taken." (2 Observations and Data Reduction)
- baselines: 2016.1.01042.S: 15.1 m - 704.1 m (2016 Nov 28), 54.5 m - 3.3 km (2017 Aug 02); 2022.1.01365.S: 230.2 m - 15.2 km  
  > "15.1 m - 704.1 m" (Table 1); "54.5 m - 3.3 km" (Table 1); "230.2 m - 15.2 km" (Table 1)
- angular resolution: ~0.04 arcsec (~5 au); continuum beam 0.037 x 0.022 arcsec (19.08 deg)  
  > "at a resolution of $\sim0.04\ensuremath{''}$ ($\sim5$ au)" (abstract); "$0.037\ensuremath{''}\times0.022\ensuremath{''}$ $(19.08\ensuremath{^\circ})$" (Table 2)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.019 mJy/beam, measured from an off-source region  
  > "0.019" (Table 2); "and from an off-source region for the continuum emission" (Table 2 notes)
- time on source: 2016.1.01042.S: 1.2 min and 3 min; 2022.1.01365.S: 32 min  
  > "1.2 min" (Table 1); "32 min" (Table 1)
- observing dates: 2016 Nov 28, 2017 Aug 02 (2016.1.01042.S); 2023 Jul 19 (2022.1.01365.S)  
  > "2016 November 28" (Table 1); "2017 August 02" (Table 1); "2023 July 19" (Table 1)
- pi or archival as stated: 2022.1.01365.S new program (PI J. Huang); 2016.1.01042.S archival (PI C. Chandler)  
  > "ALMA program 2022.1.01365.S (PI: J. Huang)" (2 Observations and Data Reduction); "program 2016.1.01042.S (PI: C. Chandler) via the ALMA archive" (2 Observations and Data Reduction)
- Line: 12CO J=2-1 (230.538 GHz (Table 2 frequency))
- Line: 13CO J=2-1 (220.3986842 GHz (Table 2 frequency))
- Line: C18O J=2-1 (219.5603541 GHz (Table 2 frequency))
- Other facility **CARMA (literature)**: Disk fluxes at 229 and 113 GHz used for a consistency check of the spectral index  
  > "Using CARMA, (cite: 2015ApJ...808..102K) measured disk fluxes of 111.2 mJy at 229 GHz and 28.7 mJy at 113 GHz." (Evidence for high millimeter continuum optical depths)
- External data: 3 mm (97.5 GHz) flux of 24.96 mJy  
  > "(cite: 2019ApJ...877L...2H) reported a flux of 24.96 mJy at 97.5 GHz (3 mm)." (Evidence for high millimeter continuum optical depths) [from (cite: 2019ApJ...877L...2H)]
- External data: CARMA fluxes of 111.2 mJy at 229 GHz and 28.7 mJy at 113 GHz  
  > "measured disk fluxes of 111.2 mJy at 229 GHz and 28.7 mJy at 113 GHz." (Evidence for high millimeter continuum optical depths) [from (cite: 2015ApJ...808..102K)]
- External data: Stellar luminosity L* = 0.79 Lsun  
  > "The luminosity of Haro 6-13 is $L_\ast = 0.79$ $L_\odot$ (cite: 2019ApJ...882...49L)." (Evidence for high millimeter continuum optical depths) [from (cite: 2019ApJ...882...49L)]
- External data: Stellar mass M* = 0.91 Msun  
  > "Finally, $Q$ is calculated assuming that $M_\ast = 0.91$ $M_\odot$ (cite: 2019ApJ...882...49L)" (Gravitational instability) [from (cite: 2019ApJ...882...49L)]
- External data: Distance 127.7 +1.7/-1.6 pc  
  > "located $127.7\substack{+1.7\\-1.6}$ pc away in the Taurus Molecular Cloud complex (cite: 2014ApJ...786...97H; 2021AA...649A...1G; 2021AJ....161..147B)" (Introduction) [from (cite: 2014ApJ...786...97H; 2021AA...649A...1G; 2021AJ....161..147B)]
- External data: Systemic velocity 5.9 km/s  
  > "the systemic velocity of 5.9 km s$^{-1}$ (cite: 2021AA...645A.145G)" (CO isotopologue emission) [from (cite: 2021AA...645A.145G)]
- External data: DSHARP dust opacities at 1.3 mm (kappa_abs = 0.4, 1.9, 1.0 cm2/g for a_max = 0.1, 1, 10 mm)  
  > "These values correspond to the DSHARP dust opacities at a wavelength of 1.3 mm" (Gravitational instability) [from (cite: 2018ApJ...869L..45B; 2018zndo...1495277B)]
- External data: Flaring angle phi = 0.02 for the passive-disk dust temperature  
  > "As in (cite: 2018ApJ...869L..46D), we set the flaring angle $\varphi$ to 0.02." (Evidence for high millimeter continuum optical depths) [from (cite: 2018ApJ...869L..46D)]
- External data: Grid of thermochemical models of compact disks used to turn the C18O flux into a disk mass  
  > "Based on the grid of thermochemical models of compact disks presented in (cite: 2021AA...651A..48M), which assume an ISM-like CO:H$_2$ abundance" (Gravitational instability) [from (cite: 2021AA...651A..48M)]
- External data: Gaia RUWE of 2.4  
  > "Haro 6-13’s RUWE value is 2.4 (cite: 2023AA...674A...1G)" (Planetary or stellar companions) [from (cite: 2023AA...674A...1G)]
- External data: Age 2.6 +2.1/-1.1 Myr  
  > "estimated an age of $2.6\substack{+2.1\\-1.1}$ Myr" (Introduction) [from (cite: 2019ApJ...882...49L)]
- Simulation/model as data: Grid of thermochemical models of compact disks (Miotello et al. 2021) used to convert the C18O flux to a maximum disk mass  
  > "the C$^{18}$O flux translates to a maximum disk mass of $\sim10^{-2}$ $M_\odot$" (Gravitational instability)

## Processing

### Calibration

- pipeline or manual: 2022.1.01365.S: calibrated MS from ALMA staff (pipeline). 2016.1.01042.S: 2016 Nov 28 by pipeline, 2017 Aug 02 by manual archive scripts  
  > "A calibrated measurement set was produced by ALMA staff using the `CASA 6.4.1` pipeline" (2 Observations and Data Reduction); "while the data from 2017 August 02 were processed using manual calibration scripts from the archive." (2 Observations and Data Reduction)
- casa version: CASA 6.4.1 pipeline (2022 data); CASA 4.7.2 pipeline (2016 Nov 28 EB); further processing with CASA 6.5  
  > "A calibrated measurement set was produced by ALMA staff using the `CASA 6.4.1` pipeline" (2 Observations and Data Reduction); "The raw data from 2016 November 28 were calibrated with the `CASA 4.7.2` pipeline" (2 Observations and Data Reduction); "Further processing of the datasets was performed with `CASA` 6.5." (2 Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% systematic flux calibration uncertainty  
  > "the dominant source of uncertainty is the 10% systematic flux calibration uncertainty." (Evidence for high millimeter continuum optical depths)
- self calibration: Short-baseline EBs combined: 3 phase rounds (scan length, 60 s, 15 s) + 1 amplitude (scan length). Long-baseline: 1 phase round (full-observation interval), aligned, combined; then 2 phase rounds (scan length, 30 s) + 1 amplitude (scan length)  
  > "We combined the two EBs and performed three rounds of phase self-calibration with intervals corresponding to the scan length, 60 s, and 15 s, and then one round of amplitude self-calibration with a scan-length solution interval." (2 Observations and Data Reduction); "performed one round of phase self-calibration with a solution interval spanning the length of the observation." (2 Observations and Data Reduction); "We performed two rounds of phase self-calibration on the combined data with scan-length and 30 s intervals, and then one round of amplitude self-calibration with a scan-length interval." (2 Observations and Data Reduction)

### Imaging

- task: tclean (continuum images per EB); multiscale CLEAN for combined data and CO cubes  
  > "Separate continuum images were generated for the two execution blocks (EBs) using `tclean`." (2 Observations and Data Reduction); "The combined data were imaged with multiscale CLEAN and a robust value of 0.5." (2 Observations and Data Reduction)
- deconvolver: multiscale CLEAN  
  > "The combined data were imaged with multiscale CLEAN and a robust value of 0.5." (2 Observations and Data Reduction)
- weighting robust: robust = 0.5 (combined continuum and CO cubes)  
  > "The combined data were imaged with multiscale CLEAN and a robust value of 0.5." (2 Observations and Data Reduction); "We used a robust value of 0.5 and applied a $uv$-taper of $0.3''$" (2 Observations and Data Reduction)
- uv taper: CO cubes: 0.3 arcsec; residual-visibility continuum image: 0.02 arcsec  
  > "We used a robust value of 0.5 and applied a $uv$-taper of $0.3''$ to improve the signal-to-noise ratio of the fainter, larger-scale emission." (2 Observations and Data Reduction); "employing a $uv$ taper of $0.02\ensuremath{''}$ to improve the signal-to-noise ratio of the residual emission." (Spiral arm properties)
- cell size: _not stated_
- image size: _not stated_
- masking: auto-multithresh for CO cubes  
  > "the `auto-multithresh` algorithm (cite: 2020PASP..132b4505K) was used to create the CLEAN masks." (2 Observations and Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: uv-plane subtraction with uvcontsub (for CO cubes)  
  > "Continuum subtraction was performed in the $uv$ plane using `uvcontsub`." (2 Observations and Data Reduction)
- line free channels: channels covered by CO isotopologue lines flagged before averaging to pseudo-continuum (ranges not given)  
  > "We began by flagging the channels covered by CO isotopologue line emission in the short-baseline measurement sets from program 2016.1.01042.S" (2 Observations and Data Reduction)
- primary beam correction: applied to CO cubes and to the final continuum image  
  > "After applying a primary beam correction to the image cubes" (2 Observations and Data Reduction); "Finally, a primary beam correction was applied." (2 Observations and Data Reduction)
- array combination: short-baseline 2016.1.01042.S EBs self-calibrated, then long-baseline 2022.1.01365.S data aligned and combined  
  > "To provide coverage on shorter baselines, we retrieved 1.3 mm observations of Haro 6-13 from program 2016.1.01042.S" (2 Observations and Data Reduction); "Then, the long-baseline observations were spatially aligned with the self-calibrated short-baseline continuum observations using the same procedure described above." (2 Observations and Data Reduction)
- smoothing: CO integrated intensity maps use velocity resolution 0.65 km/s (12CO) and 1.35 km/s (13CO, C18O)  
  > "image $^{12}$CO at a velocity resolution of 0.65 km s$^{-1}$ and $^{13}$CO and C$^{18}$O at a resolution of 1.35 km s$^{-1}$" (2 Observations and Data Reduction)
- final beam: continuum 0.037 x 0.022 arcsec (19.08 deg); 12CO 0.47 x 0.42 arcsec (-31.62 deg)  
  > "$0.037\ensuremath{''}\times0.022\ensuremath{''}$ $(19.08\ensuremath{^\circ})$" (Table 2); "$0.47\ensuremath{''}\times0.42\ensuremath{''}$ $(-31.62\ensuremath{^\circ})$" (Table 2)
- final rms: continuum 0.019 mJy/beam; 12CO 7.5, 13CO 4.9, C18O 4.0 mJy/beam per channel  
  > "0.019" (Table 2); "Measured from line-free channels for the image cubes ($\Delta v = 0.65$ km s$^{-1}$ for $^{12}$CO and 1.35 km s$^{-1}$ for $^{13}$CO and C$^{18}$O)" (Table 2 notes)

### Inherited from earlier work

- Procedure to locate the disk center (imfit 2D Gaussian), phaseshift to phase center and fixplanets to match EB coordinates  
  > "Following the procedure described in (cite: 2018ApJ...869L..41A), we used the `imfit` task in `CASA` to fit a 2D Gaussian to each continuum image in order to locate the disk center" (2 Observations and Data Reduction) [from (cite: 2018ApJ...869L..41A)]
- Algorithm implemented in protomidpy (Fourier-Bessel series radial intensity model)  
  > "using the publicly available code `protomidpy`" (Spiral arm properties) [from (cite: 2024MNRAS.532.1361A)]
- Method used by visread to rescale visibility weights  
  > "which implements the method described in (cite: 2023PASP..135f4503Z)" (Spiral arm properties) [from (cite: 2023PASP..135f4503Z)]
- Flaring angle phi = 0.02 and passive-disk dust temperature formula  
  > "As in (cite: 2018ApJ...869L..46D), we set the flaring angle $\varphi$ to 0.02." (Evidence for high millimeter continuum optical depths) [from (cite: 2018ApJ...869L..46D)]
- DSHARP dust composition for scattering and opacity estimates  
  > "Assuming a standard power-law grain size distribution and a DSHARP dust composition (cite: 2018ApJ...869L..45B)" (Evidence for high millimeter continuum optical depths) [from (cite: 2018ApJ...869L..45B)]

### Not stated but needed to reproduce (our reading)

- tclean parameters for the continuum images (cell size, image size, multiscale scales, niter, threshold, continuum mask)
- gaincal settings for self-calibration (solution combine, spw mapping, minimum SNR, reference antenna, which flux/gain calibrators were used for the flux scale)
- Flux-scale alignment between the 2016/2017 EBs and the 2023 EB (not stated)
- Channel ranges flagged as CO line emission and uvcontsub fit order
- Exact imfit regions, phaseshift/fixplanets offsets used for alignment
- protomidpy version and settings (number and spacing of Fourier-Bessel terms, radial grid, outer radius, MCMC initialization, how the MAP I(r) was chosen)
- Per-SPW weight scaling factors from visread for each dataset (only the range ~1 to ~5 is given)
- Pixel scale of the residual image used for filfinder, and how filfinder branches were selected into S1/S2
- Whether the radial-profile and contrast measurements use the 5-au-inner masks or beam-matched sampling beyond what is stated
- Procedure for measuring the 1 arcsec aperture flux (center, background treatment)
- Spectral-index calculation details for CARMA fluxes beyond assuming 10% flux uncertainty

## Analysis recipe

1. **Self-calibrate, combine and image the continuum**: Align EBs on disk center, self-calibrate short-baseline EBs, align and combine with long-baseline data, self-calibrate again and image with multiscale CLEAN at robust 0.5, then apply primary beam correction  
  > "We combined the two EBs and performed three rounds of phase self-calibration with intervals corresponding to the scan length, 60 s, and 15 s, and then one round of amplitude self-calibration with a scan-length solution interval." (2 Observations and Data Reduction); "We performed two rounds of phase self-calibration on the combined data with scan-length and 30 s intervals, and then one round of amplitude self-calibration with a scan-length interval." (2 Observations and Data Reduction)
   - software: CASA, tclean, imfit, phaseshift, fixplanets
   - parameter: robust = 0.5  
  > "The combined data were imaged with multiscale CLEAN and a robust value of 0.5." (2 Observations and Data Reduction)
   - parameter: Long-baseline data: 1 phase round with a solution interval spanning the observation before combining  
  > "performed one round of phase self-calibration with a solution interval spanning the length of the observation." (2 Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Image CO isotopologue cubes and moment maps**: uvcontsub, multiscale CLEAN with auto-multithresh, primary beam correction, integrated intensity and intensity-weighted velocity maps, spectra from circular apertures  
  > "Continuum subtraction was performed in the $uv$ plane using `uvcontsub`." (2 Observations and Data Reduction); "The $^{12}$CO and $^{13}$CO spectra were extracted from circular apertures centered on the disk with radii of $6''$ (770 au)." (CO isotopologue emission)
   - software: CASA, uvcontsub, tclean, auto-multithresh
   - parameter: Velocity resolution 0.65 km/s (12CO), 1.35 km/s (13CO, C18O)  
  > "image $^{12}$CO at a velocity resolution of 0.65 km s$^{-1}$ and $^{13}$CO and C$^{18}$O at a resolution of 1.35 km s$^{-1}$" (2 Observations and Data Reduction)
   - parameter: robust 0.5 with 0.3 arcsec uv-taper  
  > "We used a robust value of 0.5 and applied a $uv$-taper of $0.3''$ to improve the signal-to-noise ratio of the fainter, larger-scale emission." (2 Observations and Data Reduction)
   - parameter: Integration ranges 0.2-10.6 km/s (12CO) and 2.75-8.15 km/s (13CO, C18O) in LSRK, negative pixels clipped  
  > "summing up emission at LSRK velocities between 0.2 and 10.6 km s$^{-1}$ and of $^{13}$CO and C$^{18}$O by summing emission between 2.75 and 8.15 km s$^{-1}$" (2 Observations and Data Reduction)
   - parameter: Velocity maps use a 4 sigma clip  
  > "Intensity-weighted velocity maps were then produced using a 4$\sigma$ clip." (2 Observations and Data Reduction)
   - parameter: C18O spectrum aperture radius 1.5 arcsec  
  > "was extracted with a circular aperture with a radius of $1.5\ensuremath{''}$" (CO isotopologue emission)
   - fitting: _not stated_
   - validation: The velocity ranges were chosen from emission above 3 sigma  
  > "The velocity ranges were chosen based on the detection of emission above the $3\sigma$ level." (2 Observations and Data Reduction)
3. **Unsharp-mask image and azimuthally averaged radial profile**: Unsharp masking for visual enhancement; deprojected radial intensity profile from the original CLEAN image  
  > "To enhance the spiral arm contrast, we applied unsharp masking, which subtracts a smoothed version of an image from the original image and then adds a scaled version of the difference image back to the original image." (Overview of continuum morphology)
   - software: scikit-image
   - parameter: scale factor 2, Gaussian filter sigma 0.06 arcsec  
  > "specifying a scale factor of 2 and a Gaussian filter with a sigma parameter of $0.06\ensuremath{''}$" (Overview of continuum morphology)
   - fitting: _not stated_
   - validation: Unsharp-masked image not used for quantitative analysis because it truncates the outer disk emission  
  > "We do not use the version of the image with unsharp masking for quantitative analysis because the process truncates the outer disk emission, which may bias spiral measurements" (Spiral arm properties)
4. **Rescale visibility weights**: Per-SPW correction of absolute weight scaling with visread  
  > "we used the `visread` package (cite: ian_czekala_2021_4432520), which implements the method described in (cite: 2023PASP..135f4503Z), to correct the absolute scaling of the weights in our measurement sets on a per-SPW basis." (Spiral arm properties)
   - software: visread
   - parameter: weights downscaled by factors from ~1 to ~5  
  > "the weights were ultimately downscaled by factors ranging from $\sim1$ (weights were essentially correct) to $\sim5$." (Spiral arm properties)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit non-parametric axisymmetric visibility model**: protomidpy fits the 1D radial intensity profile as a Fourier-Bessel series, with disk P.A., inclination and offsets, directly to the visibilities  
  > "`protomidpy` assumes that the disk is axisymmetric and geometrically thin and models the 1D radial intensity profile $I(r)$ as a Fourier-Bessel series." (Spiral arm properties); "Model visibilities are calculated from the 1D radial intensity profile given the disk P.A., $i$, and offsets from the phase center ($\Delta x$ and $\Delta y$)." (Spiral arm properties)
   - software: protomidpy, emcee
   - parameter: Flat priors: cos i [0,1]; P.A. [0,180] deg; dx, dy [-0.1,0.1] arcsec; gamma [0.01,0.15] arcsec; log alpha [-4,5]  
  > "We set flat priors with bounds of $[0,1]$ for $\cos i$, $[0^\circ, 180^\circ]$ for P.A., $[-0.1\ensuremath{''}, 0.1\ensuremath{''}]$ for $\Delta x$ and $\Delta y$, $[0.01\ensuremath{''}, 0.15\ensuremath{''}]$ for $\gamma$, and $[-4,5]$ for $\log\alpha$." (Spiral arm properties)
   - parameter: 24 walkers, 15000 steps, first 1000 steps discarded as burn-in  
  > "The MCMC modeling was performed using 24 walkers over 15000 steps." (Spiral arm properties); "After discarding the first 1000 steps for each walker as burn-in, we computed the medians and the 68% confidence interval." (Spiral arm properties)
   - assumption: Disk is axisymmetric and geometrically thin  
  > "`protomidpy` assumes that the disk is axisymmetric and geometrically thin" (Spiral arm properties)
   - fitting: Affine-invariant MCMC (emcee) sampling P.A., i, dx, dy, alpha, gamma while estimating I(r); radial basis function kernel regularization with hyperparameters alpha (weight) and gamma (scale)  
  > "`protomidpy` uses the affine invariant Markov Chain Monte Carlo (MCMC) code `emcee` (cite: 2013PASP..125..306F) to sample the posteriors for P.A., $i$, $\Delta x$, $\Delta y$, $\alpha$, and $\gamma$ while simultaneously estimating $I(r)$." (Spiral arm properties); "The radial intensity profile model is regularized by a radial basis function kernel with hyperparameters $\alpha$ (which controls the weight of this prior) and $\gamma$ (which controls the spatial scale of the kernel)." (Spiral arm properties)
   - validation: Chains at least 50x longer than the integrated autocorrelation time  
  > "The length of the chains was chosen to ensure that they were at least $50\times$ longer than the integrated autocorrelation time." (Spiral arm properties)
6. **CLEAN the model and the residual visibilities**: CLEAN the maximum a posteriori model visibilities like the data, then CLEAN residual visibilities (observed minus model) with a uv taper  
  > "We then CLEANed the model visibilities generated by `protomidpy` from its *maximum a posteriori* estimate of $I(r)$ in the same manner as the observations" (Spiral arm properties); "Next, we CLEANed the residual visibilities created by subtracting the model visibilities from the observed visibilities, employing a $uv$ taper of $0.02\ensuremath{''}$ to improve the signal-to-noise ratio of the residual emission." (Spiral arm properties)
   - software: CASA, protomidpy
   - parameter: residual image uv taper 0.02 arcsec; synthesized beam 0.046 x 0.030 arcsec (15.9 deg)  
  > "The resulting synthesized beam is $0.046\ensuremath{''}\times0.030\ensuremath{''}$ $(15.9\ensuremath{^\circ})$." (Spiral arm properties)
   - fitting: _not stated_
   - validation: Radial profiles of CLEANed model and observations compared  
  > "comparison of the radial profiles calculated from the CLEAN images of the model and observations" (Spiral arm properties)
7. **Extract spiral arm sky coordinates**: filfinder run on the protomidpy residual image; coordinates converted to disk R and theta  
  > "we used `filfinder` (cite: 2015MNRAS.452.3435K; 2016ascl.soft08009K) to extract the sky coordinates of the spiral arms from the `protomidpy` residual image." (Spiral arm properties); "The spiral coordinates identified by `filfinder` were then converted to disk polar coordinates $R$ and $\theta$" (Spiral arm properties)
   - software: filfinder
   - parameter: smoothing size 2 pixels (0.006 arcsec); intensity threshold 0.03 mJy/beam  
  > "we set a smoothing size of 2 pixels (corresponding to $0.006\ensuremath{''}$), an intensity threshold of 0.03 mJy beam$^{-1}$," (Spiral arm properties)
   - parameter: adaptive-threshold mask width 4 pixels (0.012 arcsec, ~1.5 au)  
  > "a threshold of 4 pixels (corresponding to $0.012\ensuremath{''}\sim1.5$ au) for the width of the adaptive thresholding mask," (Spiral arm properties)
   - parameter: size threshold 300 au^2; minimum length 3 synthesized beams  
  > "a size threshold of 300 au$^2$, and a minimum length of 3 synthesized beams." (Spiral arm properties)
   - assumption: For S2, points with R < 10 au not used because they belong to the central bar-like residual  
  > "For S2, the points identified by `filfinder` with $R<10$ au are not plotted because they are associated with the central bar-like residual." (Spiral arm properties)
   - fitting: _not stated_
   - validation: Parameters set after some experimentation  
  > "After some experimentation, we set a smoothing size of 2 pixels" (Spiral arm properties)
8. **Fit Archimedean spirals with Gaussian-process regression and derive pitch angles**: Each arm fit independently with R(theta)=a-b*theta, GP regression (white noise + squared exponential kernel) in log parameter space; pitch angle from tan(beta)=|d ln R/d theta|  
  > "We thus model S1 and S2 as Archimedean spirals, which take the form $R(\theta) = a-b\theta$." (Spiral arm properties); "we used the `george` package (cite: 2015ITPAM..38..252A) to perform Gaussian process regression." (Spiral arm properties)
   - software: george, emcee
   - parameter: Priors: ln a [3,5] (S1), [1,4] (S2)  
  > "For $\ln a$, we set a flat prior with bounds of $[3,5]$ for S1 and $[1,4]$ for S2." (Spiral arm properties)
   - parameter: Priors for both arms: ln b [1,3], ln sigma^2 [-5,5], ln A [-4,4], ln C [-10,0]  
  > "For both arms, we set flat priors with bounds of $[1,3]$ for $\ln b$, $[-5, 5]$ for $\ln \sigma^2$, $[-4,4]$ for $\ln A$, and $[-10, 0]$ for $\ln C$." (Spiral arm properties)
   - parameter: 30 walkers, 5,000 burn-in steps plus 10,000 steps per arm; median and 68% interval reported  
  > "an ensemble of 30 walkers was evolved for 5,000 burn-in steps and then an additional 10,000 steps." (Spiral arm properties)
   - assumption: Continuum disk geometrically thin  
  > "Our spiral geometry measurements assume that the millimeter continuum disk is geometrically thin." (Spiral arm properties)
   - assumption: Adjacent pixels correlated because the beam is oversampled, modeled via GP kernel  
  > "Adjacent pixels are not independent because the synthesized beam is oversampled." (Spiral arm properties)
   - fitting: emcee posterior sampling of ln a, ln b, ln sigma^2, ln A, ln C with covariance K_ij = sigma^2 delta_ij + A exp[-(theta_i-theta_j)^2/(2C)]  
  > "The elements of the covariance matrix are modelled as the sum of a white noise component and a squared exponential kernel:" (Spiral arm properties); "We used `emcee` to sample the posterior distributions." (Spiral arm properties)
   - validation: Model spirals compared with data and appear to reproduce them reasonably  
  > "the model Archimedean spirals, which appear to reasonably reproduce the observations." (Spiral arm properties)
9. **Measure spiral arm contrast**: Extract intensities from the original CLEAN image along the best-fit spirals and divide by an interpolated background of per-1-au-bin minimum disk intensity  
  > "The spiral arm intensities were extracted from the original CLEAN image of the disk" (Spiral arm properties); "The “background” was estimated by measuring the minimum intensity of the disk in radial bins of 1 au and then interpolating at the radial locations of the pixels that fall along the model spiral arms." (Spiral arm properties)
   - parameter: radial bins of 1 au for the background  
  > "measuring the minimum intensity of the disk in radial bins of 1 au" (Spiral arm properties)
   - assumption: Uncertainty on arm and background intensity equals the image rms  
  > "The uncertainty on the spiral arm and background intensity measurements was assumed to be the rms of the image." (Spiral arm properties)
   - fitting: _not stated_
   - validation: _not stated_
10. **Measure continuum flux and disk-averaged spectral index**: Flux within a 1 arcsec radius circle at 229.5 GHz combined with literature 97.5 GHz flux; alpha computed from the two fluxes  
  > "we measure a flux of 144.8 mJy at 229.5 GHz (1.3 mm) inside a circular region with a $1''$ radius." (Evidence for high millimeter continuum optical depths); "The flux measurements at 229.5 and 97.5 GHz yield a disk-averaged spectral index of $\alpha = \ln\frac{I_{\nu_1}}{I_{\nu_2}}/\ln{\frac{\nu_1}{\nu_2}} = 2.1\pm0.2$." (Evidence for high millimeter continuum optical depths)
   - parameter: 10% systematic flux calibration uncertainty dominates  
  > "the dominant source of uncertainty is the 10% systematic flux calibration uncertainty." (Evidence for high millimeter continuum optical depths)
   - assumption: Disk-averaged index only; 3 mm data only marginally resolve the disk  
  > "Because the 3 mm observations from (cite: 2019ApJ...877L...2H) only marginally resolve the disk, we cannot meaningfully estimate a radially resolved spectral index profile." (Evidence for high millimeter continuum optical depths)
   - fitting: _not stated_
   - validation: Consistent with the index from CARMA fluxes (alpha = 1.9 +/- 0.2)  
  > "their measurements yield a disk-averaged $\alpha = 1.9\pm0.2$, which is consistent with our estimate from ALMA." (Evidence for high millimeter continuum optical depths)
11. **Compare brightness temperature with dust temperature**: Analytic passively irradiated disk dust temperature compared with observed brightness temperature from the CLEAN image, with and without scattering (chi = 0.6)  
  > "We use the following analytic formula for a passively irradiated disk from (cite: 2018ApJ...869L..46D) to estimate the dust temperature:" (Evidence for high millimeter continuum optical depths); "calculated from the CLEAN image using the full Planck function" (Evidence for high millimeter continuum optical depths)
   - parameter: flaring angle 0.02; L* = 0.79 Lsun  
  > "As in (cite: 2018ApJ...869L..46D), we set the flaring angle $\varphi$ to 0.02." (Evidence for high millimeter continuum optical depths); "The luminosity of Haro 6-13 is $L_\ast = 0.79$ $L_\odot$ (cite: 2019ApJ...882...49L)." (Evidence for high millimeter continuum optical depths)
   - parameter: scattering case chi = I_nu/B_nu = 0.6 for DSHARP composition  
  > "with $\chi \equiv \frac{I_\nu}{B_\nu}$ as low as $\sim0.6$ for the DSHARP dust composition" (Evidence for high millimeter continuum optical depths)
   - assumption: Dust temperature set by passive irradiation; the estimate is crude  
  > "while we only have a crude estimate of the dust temperature" (Evidence for high millimeter continuum optical depths)
   - fitting: _not stated_
   - validation: _not stated_
12. **Estimate Toomre Q from optically thick dust surface density**: Sigma_dust = tau/kappa_abs with tau = -cos i ln(1 - I/B(Td)); Q = c_s Omega_K/(pi G Sigma) with gas-to-dust 100; Td = max(observed brightness temperature, analytic Td)  
  > "The dust temperature at each value of $R$ is calculated by taking the maximum of either the observed brightness temperature or the dust temperature calculated with Equation" (Gravitational instability); "Finally, $Q$ is calculated assuming that $M_\ast = 0.91$ $M_\odot$ (cite: 2019ApJ...882...49L) and the gas-to-dust ratio is 100." (Gravitational instability)
   - software: dsharp_opac
   - parameter: tau estimated only for R > 5 au; tau = 4 set where brightness temperature exceeds dust temperature in the inner disk  
  > "We restrict the estimate of $\tau$ to $R>5$ au because beam dilution leads to artificially low estimates of $\tau$ in the inner disk." (Gravitational instability); "we set $\tau=4$ under the assumption that $\tau$ is no lower than the values calculated outside this region." (Gravitational instability)
   - parameter: kappa_abs = 0.4, 1.9, 1.0 cm2/g for a_max = 0.1, 1, 10 mm, n(a) ~ a^-3.5  
  > "Then, $\Sigma_\mathrm{dust}$ is calculated using values of $\kappa_\nu^\mathrm{abs} = 0.4$, $1.9$, and $1.0$ cm$^{2}$ g$^{-1}$." (Gravitational instability); "for a grain size distribution of $n(a)\,da\propto a^{-3.5}\,da$ and maximum grain sizes of $a_\mathrm{max} = 0.1$, $1$, and $10$ mm, respectively" (Gravitational instability)
   - assumption: mean molecular weight 2.37; gas-to-dust ratio 100; M* = 0.91 Msun; absorption-only opacity  
  > "$\mu=2.37$ is the mean molecular weight" (Gravitational instability); "In the absence of scattering, the dust surface density is given by" (Gravitational instability)
   - fitting: _not stated_
   - validation: Authors note Q is highly sensitive to the temperature profile; scattering could lower Q further  
  > "In the optically thick regime, the derived value of $Q$ is highly sensitive to the temperature profile, which is not well-constrained by our data." (Gravitational instability)
13. **Estimate disk mass from C18O flux**: C18O flux within a 1 arcsec radius circle mapped to a maximum disk mass using a thermochemical model grid  
  > "The flux measured within a circle centered on the disk with a $1''$ radius (130 au) is 460 mJy km s$^{-1}$." (Gravitational instability); "Based on the grid of thermochemical models of compact disks presented in (cite: 2021AA...651A..48M), which assume an ISM-like CO:H$_2$ abundance" (Gravitational instability)
   - assumption: ISM-like CO:H2 abundance  
  > "which assume an ISM-like CO:H$_2$ abundance" (Gravitational instability)
   - fitting: _not stated_
   - validation: Authors caution C18O may be affected by foreground absorption and continuum optical depth, so it may not trace the surface density in the arm region  
  > "If C$^{18}$O is similarly afflicted, then it would not be a reliable probe of the surface density in the spiral arm region of the disk." (Gravitational instability)

## Software

- **CASA** 6.4.1 (pipeline), 4.7.2 (pipeline, 2016 Nov 28 EB), 6.5 (further processing): Pipeline calibration, tclean imaging, imfit, phaseshift, fixplanets, self-calibration, uvcontsub  
  > "Further processing of the datasets was performed with `CASA` 6.5." (2 Observations and Data Reduction); "Separate continuum images were generated for the two execution blocks (EBs) using `tclean`." (2 Observations and Data Reduction)
- **protomidpy** : Non-parametric axisymmetric visibility fit and model/residual visibilities  
  > "we estimated and subtracted an axisymmetric intensity profile using the publicly available code" (Spiral arm properties)
- **emcee** : MCMC sampling for protomidpy and for the spiral fits  
  > "We used `emcee` to sample the posterior distributions." (Spiral arm properties)
- **visread** : Rescaling visibility weights per SPW  
  > "we used the `visread` package (cite: ian_czekala_2021_4432520)" (Spiral arm properties)
- **filfinder** : Extracting spiral arm coordinates from the residual image  
  > "we used `filfinder` (cite: 2015MNRAS.452.3435K; 2016ascl.soft08009K) to extract the sky coordinates of the spiral arms" (Spiral arm properties)
- **george** : Gaussian process regression for spiral fits  
  > "we used the `george` package (cite: 2015ITPAM..38..252A) to perform Gaussian process regression." (Spiral arm properties)
- **scikit-image** : Unsharp masking  
  > "We used the implementation from `scikit-image`" (Overview of continuum morphology)
- **dsharp_opac** v1.1.0 (from reference list): DSHARP dust opacities (cited alongside kappa values)  
  > "(cite: 2018ApJ...869L..45B; 2018zndo...1495277B)" (Gravitational instability)
- **analysisUtils** : _not stated_
- **AstroPy** : _not stated_
- **cmasher** : _not stated_
- **matplotlib** : _not stated_
- **SciPy** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum synthesized beam | 0.037 x 0.022 arcsec, PA 19.08 deg | not stated | arcsec | 1 | $0.037\ensuremath{''}\times0.022\ensuremath{''}$ $(19.08\ensuremath{^\circ})$ |
| Continuum rms | 0.019 | not stated | mJy/beam | 1 | 0.019 |
| Disk offset Delta x | 3.61 | 0.06 | mas | 5 | $3.61\pm0.06$ |
| Disk offset Delta y | 0.81 | 0.08 | mas | 5 | $0.81\pm0.08$ |
| Position angle | 154.09 | 0.14 | deg | 5 | $154.09\pm0.14$ |
| Inclination | 39.47 | 0.09 | deg | 5 | $39.47\pm0.09$ |
| Hyperparameter gamma | 0.079 | 0.003 | arcsec | 5 | $0.079\pm0.003$ |
| Hyperparameter log alpha | 0.5 | 0.2 | dimensionless | 5 | $0.5\pm0.2$ |
| Residual image synthesized beam | 0.046 x 0.030 arcsec, PA 15.9 deg | not stated | arcsec | 6 | The resulting synthesized beam is $0.046\ensuremath{''}\times0.030\ensuremath{''}$ $(15.9\ensuremath{^\circ})$. |
| Spiral S1 parameter a | 37.6 | 0.7 | au | 8 | $37.6\pm0.7$ |
| Spiral S1 parameter b | 7.2 | 0.3 | au | 8 | $7.2\pm0.3$ |
| Spiral S2 parameter a | 14.6 | 0.5 | au | 8 | $14.6\pm0.5$ |
| Spiral S2 parameter b | 6.4 | 0.2 | au | 8 | $6.4\pm0.2$ |
| S1 pitch angle range | 25 deg at R=15 au to 13 deg at R=31 au | not stated | deg | 8 | For S1, the pitch angle ranges from $25^\circ$ at $R=15$ au to $13^\circ$ at $R=31$ au. |
| S2 pitch angle range | 33 deg at R=10 au to 10 deg at R=38 au | not stated | deg | 8 | For S2, the pitch angle ranges from $33^\circ$ at $R=10$ au to $10^\circ$ at $R=38$ au. |
| Spiral arm contrast | <1.5 where both arms are detected | not stated | dimensionless | 9 | their contrasts are similar to one another and generally low ($<1.5$) |
| Flux within 1 arcsec radius at 229.5 GHz | 144.8 | 10% systematic | mJy | 10 | we measure a flux of 144.8 mJy at 229.5 GHz (1.3 mm) inside a circular region with a $1''$ radius. |
| Disk-averaged spectral index 1.3-3 mm | 2.1 | 0.2 | dimensionless | 10 | $\alpha = \ln\frac{I_{\nu_1}}{I_{\nu_2}}/\ln{\frac{\nu_1}{\nu_2}} = 2.1\pm0.2$ |
| Spectral index from CARMA fluxes | 1.9 | 0.2 | dimensionless | 10 | their measurements yield a disk-averaged $\alpha = 1.9\pm0.2$ |
| Toomre Q over the spiral-arm radii | <4 generally; dips to <~2 for a_max = 100 um and 1 cm | not stated | dimensionless | 12 | the Toomre Q parameter values are generally low ($<4$).; For certain choices of grain properties ($a_\mathrm{max}$ = 100 $\mu$m and $a_\mathrm{max}$ = 1 cm), $Q$ dips into the gravitationally unstable regime ($\lessapprox2$). |
| C18O flux within 1 arcsec radius | 460 | not stated | mJy km/s | 13 | is 460 mJy km s$^{-1}$. |
| Maximum disk mass from C18O | ~1e-2 | not stated | Msun | 13 | the C$^{18}$O flux translates to a maximum disk mass of $\sim10^{-2}$ $M_\odot$, corresponding to a disk-to-stellar mass ratio of $\sim0.01$. |

## Qualitative findings

- A pair of low-contrast spiral arms is detected in the 1.3 mm continuum at disk radii of ~10-35 au  
  > "A pair of low-contrast spiral arms are detected at disk radii from $\sim10-35$ au." (abstract)
- No clear gaps, rings or cavities in the azimuthally averaged profile; a slope change near 15 au may trace an unresolved gap  
  > "No clear gaps, rings, or cavities are visible, but it is possible that the slope change at $R\sim15$ au traces an unresolved gap." (Overview of continuum morphology)
- S2 appears connected to a bar-like central structure whose reality needs higher resolution to confirm  
  > "S2 appears to be connected to a bar-like structure at the center of the disk." (Spiral arm properties)
- 12CO and 13CO are dominated by envelope emission extending to hundreds of au south and west of the star  
  > "$^{12}$CO and $^{13}$CO are dominated by envelope emission extending to hundreds of au south and west of the star." (CO isotopologue emission)
- S2 pitch angle decreases with radius  
  > "S2 flattens out as $R$ increases, indicating that the pitch angle is decreasing with radius." (Spiral arm properties)

## Claim tuples

- H: Does the compact Haro 6-13 disk show millimeter continuum spiral arms? | E: Long-baseline ALMA 1.3 mm imaging (~0.04 arcsec) with subtraction of an axisymmetric protomidpy model | R: Two spiral arms (S1, S2) in the residuals at ~10-35 au, modelled as Archimedean spirals with pitch angles ~10-30 deg | F: Haro 6-13 is one of the smallest disks with millimeter continuum spiral arms | **supported**
- H: Is the 1.3 mm continuum optically thick? | E: Disk-averaged spectral index from 1.3 and 3 mm fluxes and brightness temperatures compared with an analytic dust temperature | R: alpha = 2.1 +/- 0.2 and brightness temperatures near the dust temperature | F: Emission is likely optically thick, though optically thin large grains are not excluded by the index alone | **partially**
- H: Could the disk be gravitationally unstable? | E: Lower-bound dust surface density from optically thick emission converted to an upper bound on Toomre Q; C18O disk mass from thermochemical grid | R: Q generally <4 and <~2 for some opacities; C18O gives a maximum disk-to-star mass ratio of ~0.01 | F: GI is plausible and worth further exploration but not established; C18O may be unreliable | **partially**
- H: Do the spiral arms have constant pitch angle? | E: Gaussian-process Archimedean spiral fits to filfinder-extracted arm coordinates | R: S2 flattens in ln R vs theta, pitch angle decreasing with radius | F: Spirals modeled as Archimedean; decreasing pitch angle is at odds with constant-pitch GI simulations but similar to some massive cold-disk simulations | **supported**
- H: Are companions or flybys a likely origin of the spirals? | E: Literature review of companion searches, Gaia RUWE, imaging constraints and CO morphology | R: No known companions, RUWE 2.4 within single-star range, no tidal CO structures reported | F: Companions and flybys are unlikely; infall or GI are favored | **partially**

## Reasoning

- Why this data: Earlier 0.1 arcsec data showed no clear substructure, so high-resolution long-baseline observations were requested  
  > "To investigate the nature of the substructures in the Haro 6-13 disk, we used ALMA to obtain high angular resolution 1.3 mm continuum observations." (Introduction)
- Why this method: Subtract an axisymmetric model to isolate spirals; unsharp mask not used quantitatively because it truncates the outer disk  
  > "To isolate the spiral structures from the disk background, we estimated and subtracted an axisymmetric intensity profile using the publicly available code" (Spiral arm properties); "We do not use the version of the image with unsharp masking for quantitative analysis because the process truncates the outer disk emission, which may bias spiral measurements" (Spiral arm properties)
- Alternative: frank-like visibility modeling not used because it requires the user to specify orientation, offset and hyperparameters; protomidpy fits them  
  > "but the latter requires the user to specify the disk orientation, offset, and regularization hyperparameters." (Spiral arm properties)
- Alternative: Flyby origin disfavored: no nearby perturber and no tidal CO structures  
  > "Haro 6-13 does not have any known nearby stellar-mass perturbers." (Stellar flybys)
- Alternative: Constant-pitch GI simulations would be at odds with the observed decreasing pitch angle  
  > "found that the pitch angles were approximately constant, which would be at odds with our observations" (Gravitational instability)
- How they decided it was enough: MCMC chain length chosen to exceed 50x the autocorrelation time  
  > "The length of the chains was chosen to ensure that they were at least $50\times$ longer than the integrated autocorrelation time." (Spiral arm properties)
- Limitation (authors): Spiral geometry assumes a geometrically thin disk  
  > "Our spiral geometry measurements assume that the millimeter continuum disk is geometrically thin." (Spiral arm properties)
- Limitation (authors): Structure within about a beam of the center can be distorted, so the bar-like structure is unconfirmed  
  > "spiral structure can appear significantly distorted within a beam or so from the disk center" (Spiral arm properties)
- Limitation (authors): Toomre Q is highly sensitive to the poorly constrained temperature profile  
  > "In the optically thick regime, the derived value of $Q$ is highly sensitive to the temperature profile, which is not well-constrained by our data." (Gravitational instability)
- Limitation (authors): Coarse spectral resolution prevents separating disk and envelope in C18O  
  > "Given the coarse spectral resolution of the data, it is not straightforward to distinguish disk and envelope contributions to the C$^{18}$O emission." (CO isotopologue emission)
- Limitation (authors): Only a disk-averaged spectral index could be derived since the 3 mm data barely resolve the disk  
  > "we cannot meaningfully estimate a radially resolved spectral index profile." (Evidence for high millimeter continuum optical depths)
- Caveat (inferred, ours): Optical depth, dust temperature and Q rest on an analytic passive-disk temperature and absorption-only opacities with no independent mass constraint; conclusions about GI remain qualitative
- Caveat (inferred, ours): Spiral detection is made in residuals of a single axisymmetric model, so arm extent depends on the protomidpy fit and its regularization; no injection-recovery test is reported here
- Caveat (inferred, ours): Pitch-angle trends assume a thin disk and S1 covers a small angular range, so the radial pitch-angle behaviour of S1 is weakly constrained
- Caveat (inferred, ours): The 3 mm flux comes from a different observation and epoch, with calibration uncertainty only assumed at 10%

## Reproducibility

- Data public (paper): Both ALMA programs obtained from the ALMA archive / acknowledged as public ALMA data  
  > "we retrieved 1.3 mm observations of Haro 6-13 from program 2016.1.01042.S (PI: C. Chandler) via the ALMA archive." (2 Observations and Data Reduction); "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2022.1.01365.S and #2016.1.01042.S." (Acknowledgements)
- Products in archive: ALMA-staff calibrated MS for 2022.1.01365.S; the authors' self-calibrated visibilities and images are on Zenodo (doi 10.5281/zenodo.15002753)  
  > "A calibrated measurement set was produced by ALMA staff using the `CASA 6.4.1` pipeline" (2 Observations and Data Reduction); "The visibilities and images can be downloaded from Zenodo:" (Footnote 1)
- Code: protomidpy is publicly available (GitHub link given); no authors' scripts for CASA processing, filfinder or george fits stated  
  > "we estimated and subtracted an axisymmetric intensity profile using the publicly available code" (Spiral arm properties)
- Missing: tclean parameters and masks for the continuum images
- Missing: gaincal and flux-scale details for self-calibration
- Missing: protomidpy configuration (basis size, radial grid, version)
- Missing: filfinder pixel scale and branch selection
- Missing: Exact aperture and background choices for fluxes and contrast
- Data volume (inferred): ~10-50 GB of raw/calibrated data for three EBs (rough estimate); Zenodo products are much smaller
- Score (inferred): 4/5, Public ALMA data, Zenodo self-calibrated products and a public fitting code with stated priors, walkers and filfinder parameters give a nearly complete recipe with many numeric results; tclean and calibration details are missing.
- Rediscovery candidate: yes, Data are public, Zenodo products exist, the protomidpy and spiral-fit recipe is largely specified, and the main results (orientation, spiral parameters, pitch angles, alpha, Q) are numeric.

## Links

- Method: (cite: 2024MNRAS.532.1361A) (Algorithm behind protomidpy non-parametric visibility fitting)
- Method: (cite: 2023PASP..135f4503Z) (Method used by visread for weight rescaling)
- Method: (cite: 2018ApJ...869L..41A) (Procedure for disk-center alignment of EBs)
- Method: (cite: 2018ApJ...869L..45B) (DSHARP dust opacities)
- Method: (cite: 2018ApJ...869L..46D) (Analytic passive-disk dust temperature)
- Method: (cite: 2020PASP..132b4505K) (auto-multithresh CLEAN masking)
- Method: (cite: 2021AA...651A..48M) (Thermochemical model grid for C18O disk masses)
- Companion: (cite: 2019ApJ...882...49L) (Earlier 0.1 arcsec Taurus survey including Haro 6-13; source of L*, M*, age)
- Companion: (cite: 2021AA...645A.145G) (ALMA molecular line observations showing the envelope and Keplerian disk)
- Companion: (cite: 2024PASJ...76..437Y) (Super-resolution imaging of the earlier data)
- Companion: (cite: 2023ApJ...952..108Z) (Visibility modeling of the earlier data finding a gap at 16 au and ring at 20 au)
- Companion: (cite: 2019ApJ...877L...2H) (3 mm flux used for the spectral index)
- Related: DSHARP
- Related: 2016.1.01042.S
- Related: 2022.1.01365.S

## Checks

```json
{
 "quotes": 216,
 "quotes_ok": 216,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 22,
 "numeric_problems": 0,
 "fill": {
  "facts": 160,
  "stated": 132,
  "rate": 0.825
 },
 "evidence_ok": true
}
```
