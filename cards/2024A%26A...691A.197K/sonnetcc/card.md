# Compact and high excitation molecular clumps in the extended ultraviolet disk of M83

`2024A&A...691A.197K` | Astronomy and Astrophysics 2024 | first author: Koda, Jin | arXiv: 2410.00180 | DOI: 10.1051/0004-6361/202451506

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: Do clouds in the XUV disk of M83 have compact, dense CO(3-2)-emitting clumps embedded in CO-deficient envelopes (clump-envelope hypothesis of Koda et al. 2022), consistent with the CO(2-1) non-detection?  
  > "We test the hypothesis introduced to explain the non-detections and recent detection simultaneously" (abstract); "This work aims to test this hypothesis with higher-resolution CO(3-2) observations, in conjunction with a consideration of the previous CO(2-1) non-detection." (Introduction)
- Target **M83 XUV disk (11 CO(3-2) clouds in the Cy9 field)**: coordinates (RA, Dec) J2000 = (13:37:05.18, -29:59:53.6) (field center, 3 pointings)  
  > "sensitivity contours at 70, 50, and 30% of the peak sensitivity at the center, which is (RA, Dec)$_{\rm J2000}$=(13:37:05.18, -29:59:53.6)" (Observations and data reduction); "M83 is one of the closest XUV disks at $d=4.5\, {\rm Mpc}$ (cite: Thim:2003aa)." (Introduction); z/distance d = 4.5 Mpc  
  > "sensitivity contours at 70, 50, and 30% of the peak sensitivity at the center, which is (RA, Dec)$_{\rm J2000}$=(13:37:05.18, -29:59:53.6)" (Observations and data reduction); "M83 is one of the closest XUV disks at $d=4.5\, {\rm Mpc}$ (cite: Thim:2003aa)." (Introduction); distance from Thim et al. 2003 (cite: Thim:2003aa)  
  > "sensitivity contours at 70, 50, and 30% of the peak sensitivity at the center, which is (RA, Dec)$_{\rm J2000}$=(13:37:05.18, -29:59:53.6)" (Observations and data reduction); "M83 is one of the closest XUV disks at $d=4.5\, {\rm Mpc}$ (cite: Thim:2003aa)." (Introduction)

## Data provenance

- ALMA projects: 2013.1.00861.S, 2017.1.00065.S, 2022.1.00359.S
- bands: _not stated_
- frequencies and spectral setup: Cy9: one spectral window on CO(3-2), 937.5 MHz band, 564.5 kHz (0.4894 km/s) channels; three further spectral windows for continuum; continuum central frequency 351.3 GHz (Cy7+Cy9)  
  > "with band and channel widths of 937.5 MHz ($812.8\, {\rm km \, s^{-1}}$) and 564.5 kHz ($0.4894\, {\rm km \, s^{-1}}$)" (Observations and data reduction); "The central frequency of the continuum emission in the combination of the Cy7 and Cy9 data is 351.3 GHz" (Observations and data reduction)
- continuum bandwidth: 3 continuum spectral windows, 1.875 GHz bandwidth each, 128 channels per spectral window  
  > "The other three spectral windows were configured to cover different sky frequencies for the continuum emission with a bandwidth of 1.875 GHz with 128 channels per spectral window." (Observations and data reduction)
- arrays: ALMA 12-m array  
  > "with the ALMA 12-m array in CO(3-2) and dust continuum emission" (Observations and data reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: CY7NA 0.89 arcsec (19 pc); CY9NA 0.40 arcsec (8.6 pc); CY9UN 0.28 arcsec (6.1 pc)  
  > "The CY7NA cube has a resolution of 0.89" (19 pc), approximately the diameter of a molecular cloud, and the CY9NA and CY9UN cubes have 0.40" (8.6 pc) and 0.28" (6.1 pc), respectively," (Cloud and clump identifications and parameters)
- max recoverable scale: uv-coverage at the CO(3-2) frequency spans angular scales 0.23-12.2 arcsec (largest scale ~12.2 arcsec); formal maximum recoverable scale not stated  
  > "The final $uv$-coverage at the CO(3-2) frequency ranges over angular scales of 0.23-12.2" (Observations and data reduction)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Cy9 data newly observed by the authors; Cy3 and Cy7 data re-analysed (details in Koda et al. 2022)  
  > "We analyzed the Cy3, Cy7, and Cy9 data." (Observations and data reduction); "The details of the Cy3 and Cy7 observations are in (cite: Koda:2022aa)." (Observations and data reduction)
- Line: CO J=3-2 (not stated)
- Line: CO J=2-1 (Cy3 data) (not stated)
- External data: Previous Cy3 CO(2-1) ALMA data over a larger region of the XUV disk (non-detection), re-used for the CO(2-1) upper limits  
  > "within the larger region of the non-detection in CO(2-1) (cite: Bicalho:2019aa)" (Introduction) [from Bicalho et al. 2019 (cite: Bicalho:2019aa)]
- External data: Galactic, LMC, SMC and WLM cloud size-velocity dispersion data used as the comparison sample in Fig. 5  
  > "For reference, it also shows clouds in the Milky Way, Large and Small Magellanic Clouds (LMC and SMC), and the dwarf galaxy WLM (cite: Solomon:1987pr; Bolatto:2008nz; Wong:2011fk; Rubio:2015aa)." (The size-velocity dispersion relation) [from (cite: Solomon:1987pr; Bolatto:2008nz; Wong:2011fk; Rubio:2015aa)]
- External data: Orion A cloud diameter of 20 pc used as comparison for cloud/clump sizes  
  > "For example, the Orion A cloud has a diameter of 20 pc (cite: Nakamura:2019wt)." (Hypothesis and predictions) [from Nakamura et al. 2019 (cite: Nakamura:2019wt)]

## Processing

### Calibration

- pipeline or manual: ALMA Observatory-provided data reduction scripts run in CASA  
  > "The visibility data are calibrated using the data reduction scripts provided by the ALMA Observatory using the Common Astronomy Software Application" (Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: MIRIAD (not CASA tclean) used for imaging  
  > "For imaging, we used the Multichannel Image Reconstruction, Image Analysis, and Display package (cite: Sault:1995kl; Sault:1996uq)." (Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: natural (NA) and uniform (UN) weighting  
  > "We used the natural (NA) and uniform (UN) weightings." (Observations and data reduction)
- uv taper: _not stated_
- cell size: 0.05 arcsec for all CO(3-2) cubes and the continuum; 0.15 arcsec for Cy3 CO(2-1)  
  > "Cy7 CO(3-2) | CY7NA | 2.54 | 0.05 | NA | 0.96, 0.82, -84.05 | 0.89 | 19 | 1.05 | 13.0" (Table 1); "Cy3 CO(2-1) | CY3NA | 2.54 | 0.15 | NA | 0.75, 0.54, -87.47 | 0.64 | 14 | 10.7 | 56.8" (Table 1)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: peak intensities and fluxes corrected for primary beam attenuation  
  > "are the values corrected for primary beam attenuation." (Parameters)
- array combination: Cy7 and Cy9 CO(3-2) data imaged separately and together; the combined cubes (CY7+9NA, CY7+9UN) are used for reference only, not for measurements  
  > "The CO(3-2) data from Cy7 and Cy9 were imaged separately and together." (Observations and data reduction); "Since the sensitivity and beam shape vary in an asymmetric way across the field of the Cy7 and Cy9 combined data, CY7+9NA and CY7+9UN, they are used only for reference, but not for measurements." (Observations and data reduction)
- smoothing: _not stated_
- final beam: CY7NA 0.96x0.82 arcsec PA -84.05; CY9NA 0.41x0.38 arcsec PA -49.83; CY9UN 0.30x0.26 arcsec PA -44.73  
  > "Cy7 CO(3-2) | CY7NA | 2.54 | 0.05 | NA | 0.96, 0.82, -84.05 | 0.89 | 19 | 1.05 | 13.0" (Table 1); "Cy9 CO(3-2) | CY9NA | 2.54 | 0.05 | NA | 0.41, 0.38, -49.83 | 0.40 | 8.6 | 0.98 | 65.6" (Table 1); "Cy9 CO(3-2) | CY9UN | 2.54 | 0.05 | UN | 0.30, 0.26, -44.73 | 0.28 | 6.1 | 1.29" (Table 1)
- final rms: Per-channel RMS (2.54 km/s channels): CY7NA 1.05, CY9NA 0.98, CY9UN 1.29 mJy/beam; measured on dirty cubes where primary beam response > 0.95  
  > "The RMS noise per channel is calculated using the dirty cubes before deconvolution in the areas where the primary beam attenuation is practically negligible" (Observations and data reduction); "Cy9 CO(3-2) | CY9NA | 2.54 | 0.05 | NA | 0.41, 0.38, -49.83 | 0.40 | 8.6 | 0.98 | 65.6" (Table 1); "Cy9 CO(3-2) | CY9UN | 2.54 | 0.05 | UN | 0.30, 0.26, -44.73 | 0.28 | 6.1 | 1.29" (Table 1)

### Inherited from earlier work

- Details of the Cy3 and Cy7 observations  
  > "The details of the Cy3 and Cy7 observations are in (cite: Koda:2022aa)." (Observations and data reduction) [from (cite: Koda:2022aa)]
- Cloud identification procedure repeated as in Koda et al. 2022 on the new CY7NA cube  
  > "For the sake of consistency, we repeated the same identification procedure on the new CY7NA data" (Clouds) [from (cite: Koda:2022aa)]
- Upper-limit treatment of sizes (R measurable only if size exceeds beam by 20%)  
  > "We followed (cite: Koda:2022aa) to set the upper limit of their size" (Parameters) [from (cite: Koda:2022aa)]
- Radius definition R = 1.92 sigma_r  
  > "the definition by (cite: Solomon:1987pr), which is supposed to represent the whole radial extent of the object." (Parameters) [from (cite: Solomon:1987pr)]
- Splitting of overlapping cloud envelopes with the watershed algorithm  
  > "which are split with the watershed algorithm (cite: Williams:1994cq)" (Clouds) [from (cite: Williams:1994cq)]
- Crude clump mass estimate method  
  > "The masses of the clumps (i.e., CO(3-2)-emitting regions) can be crudely estimated (cite: Koda:2022aa)" (Mass and radius of the CO(3-2)-emitting regions) [from (cite: Koda:2022aa)]

### Not stated but needed to reproduce (our reading)

- CASA version and the version/name of the ALMA calibration scripts for each of the three projects
- Which cycle corresponds to which project code (Cy3 vs 2013.1.00861.S, Cy7 vs 2017.1.00065.S is implied but not stated) and per-project array configurations, dates and on-source times
- MIRIAD tasks and parameters (invert/clean/restor settings, clean threshold, niter, masks, gridding) and the exact uv-ranges and tapering used for each cube
- CO(3-2) rest frequency, velocity frame and line-free channels / continuum subtraction method for the 351 GHz continuum and CO cubes
- How the 2.54 and 0.85 km/s cubes were produced from the 0.4894 km/s native channels (regridding, averaging, smoothing)
- How the S/N cubes were constructed (noise map definition across the primary-beam-varying field) and the exact clump-finder implementation
- Re-reduction details of the Cy3 CO(2-1) data (CY3NA) and of the stacking procedure for the CO(2-1) cutouts, including the velocity ranges
- Absolute flux calibration uncertainty used for the fluxes in Tables

## Analysis recipe

1. **calibrate and image the CO(3-2) and continuum data**: Calibrate with ALMA-provided scripts in CASA; image Cy7, Cy9 and combined data in MIRIAD with natural and uniform weighting; 2.54 and 0.85 km/s channel cubes  
  > "The visibility data are calibrated using the data reduction scripts provided by the ALMA Observatory using the Common Astronomy Software Application" (Observations and data reduction); "The CO(3-2) data from Cy7 and Cy9 were imaged separately and together. We used the natural (NA) and uniform (UN) weightings." (Observations and data reduction)
   - software: CASA, MIRIAD
   - parameter: Default channel width 2.54 km/s; 0.85 km/s cubes used for FWHM_v and sigma_v; cell 0.05 arcsec  
  > "Unless stated otherwise, we adopted the cubes with a $2.54\, {\rm km \, s^{-1}}$ channel width." (Cloud and clump identifications and parameters); "Cy9 CO(3-2) | CY9NA | 2.54 | 0.05 | NA | 0.41, 0.38, -49.83 | 0.40 | 8.6 | 0.98 | 65.6" (Table 1)
   - parameter: RMS per channel measured on the dirty cubes in the region with primary beam response > 0.95  
  > "The RMS noise per channel is calculated using the dirty cubes before deconvolution in the areas where the primary beam attenuation is practically negligible" (Observations and data reduction)
   - fitting: _not stated_
   - validation: Bandpass and gain calibrator amplitude and phase checked to be flat over time and frequency  
  > "The amplitude and phase of the bandpass and gain calibrators are confirmed to be flat over time and frequency after the calibrations." (Observations and data reduction)
2. **identify clouds in the CY7NA S/N cube**: S/N cubes; find pixels above 5 sigma and extend to 3 sigma per channel; split overlapping envelopes with watershed  
  > "To remove the effects of sensitivity variations across the observed fields, we generated and used signal-to-noise ratio (S/N) cubes for the identifications." (Cloud and clump identifications and parameters); "In the S/N cube, we first find pixels with $>5\sigma$ significance and extend their volumes down to pixels with $3\sigma$ per channel." (Clouds); "In some cases, the envelopes of two clouds overlap, which are split with the watershed algorithm (cite: Williams:1994cq)." (Clouds)
   - parameter: Seed threshold 5 sigma, envelope threshold 3 sigma per channel, 2.54 km/s channels  
  > "In the S/N cube, we first find pixels with $>5\sigma$ significance and extend their volumes down to pixels with $3\sigma$ per channel." (Clouds)
   - fitting: _not stated_
   - validation: Recovers the same 23 clouds as Koda et al. 2022  
  > "We find the same set of 23 molecular clouds as in (cite: Koda:2022aa)." (Clouds)
3. **identify hierarchical Level A and Level B clumps**: Search CY9NA cube inside CY7NA cloud masks (Level A), then CY9UN cube inside CY9NA clump masks (Level B), with relaxed thresholds  
  > "We first searched the CY9NA cube, finding clumps within the cloud volumes identified in CY7NA (in the CY7NA mask), and then searched the CY9UN cube to find clumps within the volumes of the CY9NA clumps." (Clumps (Level A and B)); "For Level B clumps, we did the same as for the CY9UN cube, using the same detection thresholds, but within the volumes of the CY9NA clumps as masks." (Clumps (Level A and B))
   - parameter: Level A and B thresholds: peaks above 4 sigma extended to 3 sigma envelopes  
  > "Hence, we started from $>4\sigma$ peaks and extended them to the $3\sigma$ envelopes." (Clumps (Level A and B))
   - fitting: _not stated_
   - validation: _not stated_
4. **measure cloud and clump parameters**: Intensity-weighted centroids and second moments inside the 3D masks; FWHM = sqrt(8 ln2) sigma; correct sizes and velocity dispersions for beam and channel dilution; R = 1.92 sigma_r; sizes treated as upper limits unless 20% larger than the beam  
  > "The coordinates are the intensity-weighted centroid positions." (Parameters); "To remove their effects, we calculated the second moments in radius and velocity as" (Parameters); "considered $R$ to be measurable only when the measured size is at least 20% larger than the beam size." (Parameters)
   - parameter: R = 1.92 sigma_r  
  > "R=1.92\sigma_{\rm r}" (Parameters)
   - parameter: Channel second moment sigma_ch = w/sqrt(12) for a top-hat channel; w = 0.85 km/s for sigma_v and FWHM_v  
  > "$\sigma_{\rm ch}=w/\sqrt{12}$ for a top-hat function with a full width of $w$." (Parameters)
   - parameter: Flux uncertainty from standard noise propagation using the number of beams in the object volume  
  > "$\Delta F$ was calculated with the standard noise propagation starting from $\Delta I_{\rm p}$ by taking into account the number of beams in the volume of objects." (Parameters)
   - assumption: Gaussian profiles in space and velocity for the FWHM calculation  
  > "assuming Gaussian profiles in space and velocity" (Parameters)
   - fitting: _not stated_
   - validation: Conclusion that no cloud or clump is spatially resolved  
  > "Therefore, we consider that none of the clouds nor the clumps are spatially resolved in any of the measurements." (Parameters)
5. **test compactness via clump/cloud peak-intensity and flux ratios and filling factor**: Compare peak intensity of the brightest clump and summed clump flux with the parent cloud, and compare with areal beam ratios; bound the beam filling factor from peak brightness temperature assuming optically thick CO  
  > "Each row gives measurements within each cloud." (Implications of the peak intensities and fluxes); "The high ratios indicate that approximately the same amount of flux is enclosed within the large and small beams, and hence, the CO(3-2) sources are not much spatially resolved even with the small beams." (Implications of the peak intensities and fluxes)
   - parameter: T_p = f * Gamma(nu_32, T_32) * T_32 for T_32 = 10-30 K  
  > "This gives $T_{\rm p}= (3.9 f$ - $22.5f)$ K for $T_{32}=$10-30 K with $f$ as an unknown factor." (Implications of the peak intensities and fluxes)
   - assumption: CO emission optically thick  
  > "The CO emission easily becomes optically thick on theoretical and empirical bases (cite: Goldreich:1974ab; Solomon:1979px), and thus, we assumed that it is optically thick." (Implications of the peak intensities and fluxes)
   - fitting: _not stated_
   - validation: Authors caution that missing short spacings and uniform weighting reduce apparent flux  
  > "We also caution that interferometer imaging without short spacing data (or with the uniform weighting) often reduces the apparent flux." (Implications of the peak intensities and fluxes)
6. **predict CO(2-1) flux from CO(3-2) and compare with Cy3 limit and stack**: Minimum CO(2-1) flux from thermalized condition F21 = (4/9) alpha_th F32; compare with CY3NA noise; also non-thermalized case T32/T21 ~ 0.5; stack CO(2-1) cutouts of the 11 clouds  
  > "The CO(2-1) flux of a CO(3-2)-emitting dense clump, without the cloud envelope, can be estimated from its CO(3-2) flux." (Non-detection in CO(2-1)); "A stacking analysis does not provide a significant CO(2-1) detection in this case." (The stacked cutout images)
   - parameter: alpha_th ~ 1.10, 1.16, 1.40 at T = 30, 20, 10 K  
  > "where $\alpha_{\rm th} \approx$1.10, 1.16, and 1.40 for $T$=30, 20, and 10 K, respectively." (Non-detection in CO(2-1))
   - assumption: Equal beam filling factors for CO(3-2) and CO(2-1)  
  > "We assumed that the beam filling factors of the two transitions are equal." (Non-detection in CO(2-1))
   - assumption: CMB contribution neglected  
  > "Here, we neglected the contribution of the cosmic microwave background radiation since its temperature is low for the CO(3-2)-emitting gas." (Non-detection in CO(2-1))
   - fitting: _not stated_
   - validation: Stacked CO(2-1) peak is only 1.9 sigma, consistent with but not conclusive for the thermalized prediction  
  > "The consistency is supportive of the model (Fig. [1](#fig:schematic)) but is not conclusive with this CO(2-1) data." (The stacked cutout images)
7. **estimate clump masses and radii**: Crude CO(3-2)-based clump mass with Galactic X_CO and thermalized R_3-2/1-0 = 1, including factor 1.37 for helium; convert mass to radius assuming n_H2 ~ 1e3 cm^-3; compare with virial mass  
  > "the clump mass, including helium and other heavier elements (i.e., multiplying the total hydrogen mass by 1.37), is" (Mass and radius of the CO(3-2)-emitting regions)
   - parameter: X_CO(1-0) = 3e20 cm^-2 (K km/s)^-1  
  > "$X_{\rm CO(1-0)}=3\times 10^{20}\,\rm cm^{-2}\,[K\cdot \, {\rm km \, s^{-1}}]^{-1}$ can be applied to the clumps" (Mass and radius of the CO(3-2)-emitting regions)
   - parameter: n_H2 ~ 1e3 cm^-3 as average density of the CO(3-2)-emitting region  
  > "The CO(3-2) excitation requires a density of $n_{\rm H_2}\sim 10^3\,\rm cm^{-3}$, to within an order of magnitude." (Mass and radius of the CO(3-2)-emitting regions)
   - assumption: Thermalized gas, CO 3-2/1-0 brightness temperature ratio of unity  
  > "the gas is thermalized and hence the CO 3-2/1-0 brightness temperature ratio is unity" (Mass and radius of the CO(3-2)-emitting regions)
   - fitting: _not stated_
   - validation: Mass estimates quoted as uncertain by a factor of 2-3 and roughly consistent with virial mass  
  > "These mass estimations easily have a factor of 2-3 uncertainty." (Mass and radius of the CO(3-2)-emitting regions)
8. **compare sigma_v and R upper limits with other galaxies' clouds**: Plot sigma_v against R upper limits for clouds and clumps together with Milky Way, LMC, SMC and WLM clouds from the literature  
  > "For reference, it also shows clouds in the Milky Way, Large and Small Magellanic Clouds (LMC and SMC), and the dwarf galaxy WLM (cite: Solomon:1987pr; Bolatto:2008nz; Wong:2011fk; Rubio:2015aa)." (The size-velocity dispersion relation)
   - fitting: _not stated_
   - validation: Caveat that reference clouds are measured in lower-excitation CO transitions and that only R upper limits exist  
  > "There is also a caveat in this comparison, since these reference clouds are observed in the lower-excitation transitions, CO(1-0) or CO(2-1)." (The size-velocity dispersion relation)

## Software

- **CASA** : Calibration of the visibility data with ALMA-provided scripts  
  > "The visibility data are calibrated using the data reduction scripts provided by the ALMA Observatory using the Common Astronomy Software Application (cite: McMullin:2007aa; CASA-Team:2022aa)." (Observations and data reduction)
- **MIRIAD** : Imaging of the CO(3-2) cubes and continuum  
  > "For imaging, we used the Multichannel Image Reconstruction, Image Analysis, and Display package (cite: Sault:1995kl; Sault:1996uq)." (Observations and data reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of molecular clouds identified in CY7NA (full field) | 23 | not stated | count | 2 | We find the same set of 23 molecular clouds as in (cite: Koda:2022aa). |
| Number of Level A (CY9NA) clumps | 11 | not stated | count | 3 | the eleven CY9NA clumps are labeled in the format |
| Number of Level B (CY9UN) clumps | 9 | not stated | count | 3 | We find nine CY9UN clumps. |
| Cloud 4 CO(3-2) integrated flux | 258.2 | 11.2 | mJy km/s | 4 | 4 / 13:37:04.984 / -29:59:46.15 / 564.4 / 3973 / 1438 / 1.02 / 0.96 / 6.21 / 0.34 / 26.47 / 1.25 / 258.2 / 11.2 |
| Brightest clump peak brightness temperature (Clump 4-1-1) | 2.49 | not stated | K | 4 | 4-1-1 / 13:37:05.010 / -29:59:46.22 / 562.7 / 77 / 61 / 0.26 / 0.22 / 2.32 / 2.49 / 19.04 / 1.92 |
| Minimum measurable radius R_min for clouds / Level A / Level B | 0.50 arcsec (10.9 pc) / 0.22 arcsec (4.8 pc) / 0.16 arcsec (3.5 pc) | not stated | arcsec (pc) | 4 | This is 0.50" (10.9 pc), 0.22" (4.8 pc), and 0.16" (3.5 pc) for the clouds (CY7NA), Level A clumps (CY9NA), and Level B clumps (CY9UN), respectively. |
| Mean peak-intensity ratio of brightest clump to parent cloud | 77% (Level A), 68% (Level B) | not stated | dimensionless | 5 | with the averages of 77% for Level A and 68% for Level B. |
| Beam filling factor upper bound from peak brightness temperature | f = 0.64 or smaller | not stated | dimensionless | 5 | the filling factor is $f=0.64$ or smaller, again indicating unresolved or marginally resolved objects. |
| Minimum predicted CO(2-1) flux of Cloud 4 (thermalized, T = 30, 20, 10 K) | 126.2, 133.1, 160.7 | not stated | mJy km/s | 6 | this translates to the minimum expected CO(2-1) flux of $F_{21}=$126.2, 133.1, and 160.7 |
| Significance of predicted thermalized CO(2-1) in CY3NA data | 1.9, 2.0, 2.4 sigma at 30, 20, 10 K | not stated | sigma | 6 | These are at 1.9, 2.0, and 2.4$\sigma$ significance, respectively. |
| Significance expected in CY3NA if T32/T21 ~ 0.5 (T = 30, 20, 10 K) | 5.2, 6.6, 15.2 sigma | not stated | sigma | 6 | It should have been detected in CO(2-1) at 5.2, 6.6, and 15.2$\sigma$ in the CY3NA data. |
| Stacked CO(2-1) peak flux of the 11 clouds | 263 (noise 140) | 140 | mJy km/s | 6 | Indeed, the peak flux is $F_{21}=263\, {\rm mJy}\, {\rm km \, s^{-1}}$ in CO(2-1); Thus, it is only at a $1.9\sigma$ significance. |
| Stacked CO(3-2) peak flux of the 11 clouds | 550 (noise 16) | 16 | mJy km/s | 6 | Panel (a) shows the peak CO(3-2) flux of $F_{32}=550\, {\rm mJy} \, {\rm km \, s^{-1}}$. The noise of this image is $16\, {\rm mJy} \, {\rm km \, s^{-1}}$. |
| Clump mass range from CO(3-2) fluxes | 2.1e2 to 9.3e3 | factor of 2-3 | Msun | 7 | give $M_{\rm clump}=2.1\times 10^2$-$9.3\times 10^3{\rm M_{\odot}}$.; These mass estimations easily have a factor of 2-3 uncertainty. |
| Implied clump radius | 1-4 | not stated | pc | 7 | The range of the clump masses estimated above then corresponds to $R=$1-4 pc. |

## Qualitative findings

- None of the eleven clouds is detected above 3 sigma in CO(2-1) or in 351 GHz continuum  
  > "None of the eleven clouds is above the $3\sigma$ detection limit in the CO(2-1) line and 351 GHz continuum emission." (Clouds)
- Clumps are unresolved at 6-9 pc, with some indication they may begin to be resolved at 6 pc  
  > "but there is some indication that they may be starting to be resolved at the 6 pc resolution." (Summary)
- CO(3-2)-emitting regions in the XUV clouds must be close to thermalized  
  > "The CO(3-2)-emitting regions in the XUV clouds must be close to thermalized since, otherwise, the CO(2-1) flux would be brighter and thus would have been detected in past observations." (Summary)

## Claim tuples

- H: CO(3-2) in XUV-disk clouds comes from compact dense clumps much smaller than typical cloud sizes | E: Hierarchical clump finding in CY7NA, CY9NA (0.40 arcsec) and CY9UN (0.28 arcsec) cubes; compare sizes, peak intensities and fluxes of clumps with parent clouds | R: FWHM of clumps similar to beams; mean clump/cloud peak ratio 77% (A) and 68% (B); clump flux fractions mostly 50-100% (A) | F: CO(3-2) clumps are not resolved, with diameters below 6-9 pc, similar to the dense region of Orion A | **supported**
- H: Dense clumps are close to thermalized so their CO(2-1) emission is faint and consistent with the earlier CO(2-1) non-detection | E: Predict CO(2-1) flux from CO(3-2) flux for the brightest cloud and compare to CY3NA noise; stack CO(2-1) cutouts of the 11 clouds | R: Thermalized prediction is 1.9-2.4 sigma in CY3NA (below detection); non-thermalized T32/T21 ~ 0.5 would give 5.2-15.2 sigma; stack shows 1.9 sigma only | F: The CO(3-2)-emitting gas must be close to thermalized and the envelopes cannot be CO-rich; the CO(2-1) data remain inconclusive | **supported**
- H: XUV-disk clouds follow a size-velocity dispersion relation like clouds in dwarfs and the Milky Way | E: Plot sigma_v versus R upper limits for clouds and Level A/B clumps with literature cloud samples | R: XUV clouds appear consistent with those in dwarf galaxies, with radii only upper limits | F: Consistency supports the hypothesis within the limitation of R upper limits | **partially**
- H: Dense star-forming clumps are common between normal and XUV disks | E: Compare clump size to the dense CO(3-2)-bright region of Orion A (~10 pc) and estimate clump masses and radii | R: Clump masses 2.1e2-9.3e3 Msun correspond to R of 1-4 pc, consistent with the unresolved sizes | F: XUV-disk clumps resemble Orion A dense regions; star formation may be governed by internal cloud physics | **partially**

## Reasoning

- Why this data: Field chosen from earlier ALMA CO(2-1) and CO(3-2) observations of the XUV disk, with bright UV and H-alpha peaks and multiple clouds  
  > "This region is selected based on previous ALMA observations" (Observations and data reduction)
- Why this method: Hierarchical search starting in the most sensitive cube (CY7NA), then relaxed thresholds inside its masks at higher resolution  
  > "We adopted this approach because the CY7NA data have the highest sensitivity, albeit the lowest spatial resolution" (Cloud and clump identifications and parameters)
- Alternative: Clouds may evolve and develop dense clumps only late in their lifetime, so CO(3-2) may trace only evolved clouds (not tested)  
  > "It is possible that the clouds evolve and develop dense clumps only at a later stage of their lifetime." (Cloud evolution and distribution)
- How they decided it was enough: _not stated_
- Limitation (authors): Size measurements are not very accurate because the detection thresholds are low  
  > "We note that our size measurements are not very accurate because our clump detection thresholds are not high" (Size measurements)
- Limitation (authors): The planned deep CO(2-1) observations in Cy9 were not executed  
  > "Such CO(2-1) observations were approved in ALMA Cy9, but were not executed due largely to the loss of observing times in small array configurations as a result of the cyberattack in 2022-2023." (Hypothesis and predictions)
- Limitation (authors): Clump mass and radius estimates are crude, uncertain by a factor of 2-3  
  > "These mass estimations easily have a factor of 2-3 uncertainty." (Mass and radius of the CO(3-2)-emitting regions)
- Caveat (inferred, ours): Clump sizes are only upper limits at 6-9 pc; the compactness claim rests on unresolved sources whose detection thresholds (3-5 sigma) are low
- Caveat (inferred, ours): CY7+9 combined cubes are excluded from measurements because of non-uniform sensitivity, so the highest-sensitivity data are unused for clump parameters
- Caveat (inferred, ours): The thermalization argument relies on a single cloud and a low-significance (1.9-2.4 sigma) CY3NA limit; the stacked CO(2-1) is inconclusive
- Caveat (inferred, ours): Clump masses use the Galactic X_CO and R_3-2/1-0 = 1, which are themselves the hypothesis being tested
- Caveat (inferred, ours): Only 11 clouds in one small region of one galaxy; no independent CO(2-1) or CO(1-0) detection

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: MIRIAD imaging parameters and clean/mask settings for each cube
- Missing: Clump-finder implementation and S/N cube construction details
- Missing: CASA / calibration script versions and mapping of cycles to project codes
- Missing: CO(3-2) line-free channel selection and continuum subtraction details
- Missing: Cy3 CO(2-1) cube re-reduction and stacking details
- Data volume (inferred): Roughly 50-150 GB of raw data across the three ALMA projects (12-m array Band 7, one line SPW plus three continuum SPWs per execution); the imaged cubes themselves are small
- Score (inferred): 3/5, ALMA data come from three archive projects and the cloud/clump tables give many numeric answer keys, but imaging parameters, MIRIAD settings, line-free channels and the clump-finder implementation are not given and the paper does not state data availability.
- Rediscovery candidate: no, Numeric results exist and the archive projects are identified, but the imaging and clump-finding recipe lacks the parameters needed to redo it, and public availability is not stated in the paper.

## Links

- Method: Koda et al. 2022, ApJ, 941, 3 (cite: Koda:2022aa) (Original hypothesis, Cy3/Cy7 observations details, cloud identification, size upper limit and mass estimate methods)
- Method: Sault et al. 1995 (cite: Sault:1995kl) (MIRIAD package used for imaging)
- Companion: Bicalho et al. 2019, A&A, 623, A66 (cite: Bicalho:2019aa) (Previous sensitive ALMA CO(2-1) non-detection over a 2x4 kpc2 region of the M83 XUV disk)
- Companion: Lee et al. 2024, ApJ, 968, 97 (cite: Lee:2024aa) (Virial mass and X_CO dependence on cloud population)
- Related: ALMA Cy3 project 2013.1.00861.S
- Related: ALMA Cy7 project 2017.1.00065.S
- Related: ALMA Cy9 project 2022.1.00359.S
- Related: GALEX XUV disk surveys

## Checks

```json
{
 "quotes": 120,
 "quotes_ok": 120,
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
  "facts": 101,
  "stated": 69,
  "rate": 0.683
 },
 "evidence_ok": true
}
```
