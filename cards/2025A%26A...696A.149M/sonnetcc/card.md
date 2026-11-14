# ALMAGAL: I. The ALMA evolutionary study of high-mass protocluster formation in the Galaxy: Presentation of the survey and early results

`2025A&A...696A.149M` | Astronomy and Astrophysics 2025 | first author: Molinari, S. | arXiv: 2503.05555 | DOI: 10.1051/0004-6361/202452702

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: star_formation, milky_way_ism
- Question: What physical processes govern fragmentation of cluster-forming clumps into cores across evolutionary stage and Galactic environment; this first paper presents the ALMAGAL survey, revised clump properties and a first morphology analysis of the 5 sigma 1.38 mm continuum  
  > "Fundamental questions about the physics responsible for fragmenting molecular parsec-scale clumps into cores of a few thousand astronomical units (au) are still open" (abstract); "In this first paper, we present a complete review of the target clumps physical properties, with a first analysis of the morphological properties of the dust continuum emission." (Conclusions)
- Target **ALMAGAL clump sample (1013 fields)**: coordinates _not stated_; z/distance Galactic clumps with d <= 7.5 kpc at selection; revised per-source distances in Table 1 (CDS)  
  > "we removed them from the ALMAGAL sample data considered in the rest of the paper and, thus, from further scientific analysis (amounting to 1013 targets)" (3.1 Initial selection and survey planning); "Target sources are spread over 3-14 kpc in Galactocentric distance from the near tip of the Galactic bar to the outskirts of the Milky Way" (3.1 Initial selection and survey planning); "To obtain a homogenized set of properties for the sample of target clumps and to take advantage of the ALMAGAL spectroscopy that offers the ideal database to improve existing kinematic distance estimate" (3.2.1 Revision of targets distance); distance from Kinematic distances from ALMAGAL-derived vLSR using the final module of the Mege+2021 algorithm  
  > "we removed them from the ALMAGAL sample data considered in the rest of the paper and, thus, from further scientific analysis (amounting to 1013 targets)" (3.1 Initial selection and survey planning); "Target sources are spread over 3-14 kpc in Galactocentric distance from the near tip of the Galactic bar to the outskirts of the Milky Way" (3.1 Initial selection and survey planning); "To obtain a homogenized set of properties for the sample of target clumps and to take advantage of the ALMAGAL spectroscopy that offers the ideal database to improve existing kinematic distance estimate" (3.2.1 Revision of targets distance)

## Data provenance

- ALMA projects: 2019.1.00195.L
- bands: Band 6 (1.38 mm), 217 to 220 GHz  
  > "The ALMA Band 6 217 to 220 GHz frequency range is ideally suited to provide access to" (2 Observational setup); "we observed the 1.38 mm continuum and lines toward more than 1000 dense clumps in our Galaxy" (abstract)
- frequencies and spectral setup: Two 1.875-GHz wide windows (~1.4 km/s resolution) plus two higher resolution windows (~0.34 km/s)  
  > "The correlator was configured to produce two 1.875-GHz wide windows" (2 Observational setup)
- continuum bandwidth: _not stated_
- arrays: ACA (7m) plus two 12-m array configurations per source, single pointing  
  > "all the targets have been observed in single-pointing, with the ACA plus two configurations of the 12-m array with two different antenna configuration combinations, depending on the source distances" (2 Observational setup)
- configurations: C-5/C-2/ACA for d<4.7 kpc ('near', 538 objects); C-6/C-3/ACA for d>4.7 kpc ('far', 479 objects)  
  > "the C-5/C-2/ACA setup was chosen for sources with" (2 Observational setup)
- baselines: _not stated_
- angular resolution: Maximum resolution 0.13 arcsec (C-6, far) and 0.24 arcsec (C-5, near); target minimum resolution ~1000 au  
  > "Two different combinations of ALMA Compact Array (ACA) and 12-m array setups were used to deliver a minimum resolution of" (abstract)
- max recoverable scale: about 30 arcsec  
  > "along with a largest recoverable scale of about 30" (2 Observational setup)
- sensitivity: 0.1 mJy continuum sensitivity required for all targets  
  > "We required a 0.1 mJy continuum sensitivity for all targets irrespective of clump properties" (2 Observational setup)
- time on source: 117.7 h (12-m array, all configurations) and 88.4 h (ACA) granted  
  > "for a total granted observing time of 117.7 hours for all the 12-m array configurations, and 88.4 hours for the ACA observations" (2 Observational setup)
- observing dates: _not stated_
- pi or archival as stated: ALMA Cycle 7 Large Program 2019.1.00195.L (ALMAGAL Consortium)  
  > "The ALMAGAL Large Program (2019.1.00195.L) was approved in ALMA Cycle 7" (2 Observational setup)
- Line: 13CO and C18O J=2-1 (not stated)
- Line: SiO 5-4 (not stated)
- Line: H2CO three lines (not specified) (not stated)
- Line: CH3OH not stated (not stated)
- Line: CH3CN and CH3(13)CN 12-11 K-ladder (not stated)
- Line: DCN 3-2 (not stated)
- Line: OCS 19-18 (not stated)
- Line: HC3N 24-23 (not stated)
- Line: SO 6_5-5_4 (not stated)
- Other facility **Herschel (Hi-GAL)**: Hi-GAL clump catalog used to select 915 targets, 250 um peak positions for pointing, and clump mass, luminosity, temperature, surface density and 350 um fluxes  
  > "The larger fraction of the sample (915 objects) was selected from the complete catalog of dense clumps from (cite: Elia+2017)" (3.1 Initial selection and survey planning); "The position of the 250 $\mu$m peak was adopted for the ALMA observations." (3.1 Initial selection and survey planning)
- Other facility **RMS survey**: 98 additional, more evolved targets (L > 3000 Lsun) from the RMS catalog  
  > "we also included 98 objects drawn from the Red Midcourse Space Experiment Source (RMS) catalog of star-forming regions (cite: Lumsden+2013)" (3.1 Initial selection and survey planning)
- Other facility **ATLASGAL**: Evolutionary classification (Urquhart+2022) for about 65% of sources  
  > "Roughly 65% of the ALMAGAL sources were cross-matched with the ATLASGAL catalog and the classification adopted from there." (3.2.2 A homogeneous methodology for SED fitting.)
- External data: Clump mass, bolometric luminosity, dust and bolometric temperature, surface density from the Hi-GAL catalogs (rescaled to revised distance), or derived with the same methodology  
  > "Clump mass and bolometric luminosity from (cite: Elia+2021), or derived with the same methodology" (ALMAGAL Clumps Properties); "Cols. 11-12: cold dust temperature and bolometric temperature as in (cite: Elia+2021), or derived with the same methodology." (ALMAGAL Clumps Properties) [from Elia et al. 2021 (cite: Elia+2021); Elia et al. 2017 (cite: Elia+2017)]
- External data: Evolutionary class (quiescent, protostellar, YSO, HII) of each clump  
  > "we also report the classification according to the method from (cite: Urquhart+2022) who define classes as quiescent, protostellar, YSO, and HII regions based on visual inspection at different wavelengths" (3.2.2 A homogeneous methodology for SED fitting.) [from Urquhart et al. 2022 (cite: Urquhart+2022)]
- External data: Dust opacity law (beta=1.75) used for the core mass sensitivity estimate  
  > "assuming dust temperature of 20K and opacity from (cite: OH1994) with index $\beta=1.75$" (2 Observational setup) [from Ossenkopf & Henning 1994 (cite: OH1994)]

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
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Fluxes measured on primary beam-corrected images (PBCOR)  
  > "we computed the fluxes (peak, total, and median fluxes) by projecting the RoI mask onto the primary beam-corrected images (PBCOR)" (4 Properties of continuum emission)
- array combination: Joint deconvolution of ACA 7m + TM2 (7m+tm2 products) and 7m + TM2 + TM1 (full resolution 7m+tm2+tm1 products)  
  > "A fundamental step in data processing was the production of continuum images and spectral cubes by jointly deconvolving the combined data taken with ACA" (2 Observational setup); "In a subsequent step, the TM1 data were also combined to obtain the full resolution *7m+tm2+tm1* products." (2 Observational setup)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: Per-field rms from the residual map outside the largest CLEAN mask, stored in FITS keyword AGSTDREM  
  > "This noise level is computed in each field using the residual map outside of the largest CLEAN mask used in the ALMAGAL pipeline processing (cite: SanchezMonge+2025)" (4 Properties of continuum emission)

### Inherited from earlier work

- Detailed observation setup, calibration and imaging of the ALMAGAL data  
  > "More details about the observations setup are given in the companion paper (cite: SanchezMonge+2025)." (2 Observational setup) [from Sanchez-Monge et al. 2025 (cite: SanchezMonge+2025)]
- CLEAN masks and pipeline processing that define the continuum maps and noise  
  > "the largest CLEAN mask used in the ALMAGAL pipeline processing (cite: SanchezMonge+2025)" (4 Properties of continuum emission) [from Sanchez-Monge et al. 2025 (cite: SanchezMonge+2025)]
- Kinematic distance conversion of vLSR to distance  
  > "applied the final module of the (cite: Mege+2021) algorithm" (3.2.1 Revision of targets distance) [from Mege et al. 2021 (cite: Mege+2021)]
- Hi-GAL-like SED fitting used for RMS sources lacking Hi-GAL physical parameters  
  > "hence they required a custom analysis of their SED to estimate parameters with the same approach as in Hi-GAL" (3.2.2 A homogeneous methodology for SED fitting.) [from Elia et al. 2017, 2021 (cite: Elia+2017; Elia+2021)]
- Core detection limits and compact-source extraction details  
  > "More details are given in (cite: SanchezMonge+2025; Coletta+2025)." (2 Observational setup) [from Sanchez-Monge et al. 2025; Coletta et al. 2025 (cite: SanchezMonge+2025; Coletta+2025)]

### Not stated but needed to reproduce (our reading)

- CASA/pipeline version, calibrators, flux scale and self-calibration used to make the ALMAGAL images (deferred to the companion paper)
- tclean settings for the 7m+tm2 and 7m+tm2+tm1 continuum images: weighting/robust, deconvolver, cell and image size, masks, uv taper, multiscale scales
- Continuum channel selection and line-free channels used to build the 1.38 mm continuum
- Per-field beam sizes and AGSTDREM rms values, and which version of the images (not yet public) was used
- Herschel 350 um flux extraction (aperture, background) and the specific T/beta/opacity chosen for each point versus the 20-50 K, 1.5-2 envelope
- Exact perimeter and area algorithm (pixel connectivity, boundary treatment), convex hull implementation, and units/normalisation of the Delta-circ distance
- Silverman test implementation (bandwidth, number of bootstrap samples) behind the 100% bimodality probability
- Gaussian line-fit configuration, line rest frequencies and the 'good fit' criterion used for the vLSR measurement
- Tables 1 and 2 are only at the CDS; Herschel SED fitting parameters for RMS-only sources are not given

## Analysis recipe

1. **Revise clump vLSR and kinematic distances from ALMAGAL lines**: Co-add 7m subcubes over the emitting region for dense-gas lines, fit Gaussians to the integrated spectra, average line centers, convert vLSR to distance with the Mege+2021 module  
  > "For each line, the cubes were co-added over the emitting region, defined by selecting the spatial pixels where the moment zero map is above three times its noise level" (3.2.1 Revision of targets distance); "to obtain integrated spectra that were fed to an automatic 3$\sigma$-clipping line detection and Gaussian fitting algorithm" (3.2.1 Revision of targets distance)
   - software: Mege et al. 2021 kinematic-distance algorithm
   - parameter: Subcubes over +/-180 km/s around the target lines  
  > "we extracted subcubes from the ALMAGAL *7m* datacubes over large velocity ranges ($\pm$180km s$^{-1}$) centered on" (3.2.1 Revision of targets distance)
   - parameter: vLSR from lines with critical density above 1e5 cm-3 (CH3OH, H2CO, DCN, SO, HC3N, SiO); C18O and 13CO only for 207 targets  
  > "The $v_{\rm LSR}$ of the targets were then derived averaging the fitted line centers of all the detected lines with a good fit among the transitions with critical density higher than 10$^5$ cm$^{-3}$" (3.2.1 Revision of targets distance)
   - parameter: vLSR uncertainty adopted as 1.4 km/s (spectral resolution)  
  > "We assigned an uncertainty to the derived $v_{\rm LSR}$ of 1.4 km s$^{-1}$, which is the spectral resolution of the data." (3.2.1 Revision of targets distance)
   - assumption: Hi-GAL sources with unresolved KDA placed at the near distance  
  > "we chose for this study to adopt the same approach of the RMS catalog and place the Hi-GAL sources for which KDA could not be resolved" (3.2.1 Revision of targets distance)
   - assumption: Distance error from a 7 km/s velocity offset for non-circular and proper motions  
  > "we considered possible deviations from purely circular motions and proper motions as anticipated above, by applying an additional offset to the velocity of 7 km s$^{-1}$ as in (cite: Mege+2021)" (3.2.1 Revision of targets distance)
   - assumption: Twice the relative distance uncertainty propagates to luminosity and mass  
  > "Error propagation transfers twice the distance relative uncertainty to source luminosity and masses." (3.2.1 Revision of targets distance)
   - fitting: Gaussian line fits with 3 sigma clipping; priors and likelihood not stated  
  > "to obtain integrated spectra that were fed to an automatic 3$\sigma$-clipping line detection and Gaussian fitting algorithm" (3.2.1 Revision of targets distance)
   - validation: New distances compared with the original proposal-time distances  
  > "We find that for 95 objects out of the total 1013 sources sample, the new distance differs by more than 0.5 kpc from the original one." (3.2.1 Revision of targets distance)
2. **Homogenise clump physical properties by SED fitting**: RMS-selected sources without Hi-GAL parameters were re-processed with the Hi-GAL SED approach, with flags for irregular, rebuilt, saturated or few-band SEDs  
  > "hence they required a custom analysis of their SED to estimate parameters with the same approach as in Hi-GAL" (3.2.2 A homogeneous methodology for SED fitting.)
   - parameter: Hi-GAL inclusion requires a convex SED with at least 4 adjacent Herschel bands  
  > "where the requirement for inclusion was that a source should have a convex SED with at least 4 adjacent *Herschel* bands" (3.2.2 A homogeneous methodology for SED fitting.)
   - fitting: Grey-body fit to Herschel fluxes (dust temperature hard limit of 40 K reached for some sources, refit); priors and likelihood not stated  
  > "due to a 40K hard limit that was reached in the grey-body fit" (ALMAGAL Clumps Properties)
   - validation: _not stated_
3. **Identify 5 sigma continuum regions of interest and measure their area, perimeter and flux**: Mask pixels above 5 sigma in each field, label connected pixels as RoIs, discard RoIs smaller than the beam, compute area, perimeter and fluxes on PBCOR images  
  > "For each of the 1013 independent fields we produce masks containing the pixels of the continuum images with flux above the 5$\sigma$ level, which we call RoI (Region of Interest)." (4 Properties of continuum emission); "For each RoI, we compute the area and the perimeter, and all RoIs smaller than the beam are discarded from further analysis." (4 Properties of continuum emission)
   - parameter: rms from residual map outside the largest CLEAN mask (keyword AGSTDREM)  
  > "This noise level is computed in each field using the residual map outside of the largest CLEAN mask used in the ALMAGAL pipeline processing (cite: SanchezMonge+2025)" (4 Properties of continuum emission)
   - parameter: Each cluster of connected pixels is one RoI  
  > "Each cluster of connected pixels constitutes an individual RoI, so that each field may have many RoIs." (4 Properties of continuum emission)
   - fitting: _not stated_
   - validation: 5 sigma threshold chosen to limit noise residuals  
  > "The 5$\sigma$ threshold was adopted to minimize the inclusion of noise residuals in the morphological analysis." (4 Properties of continuum emission)
4. **Compare ALMA 7m+tm2 flux with Herschel 350 um flux to quantify missing flux**: Extrapolate the PBCOR 7m+tm2 1.38 mm flux inside the 4 sigma contour to 350 um with a modified black body and compare with the Herschel 350 um flux  
  > "In particular, we extrapolated the mm flux to 350$\mu$m using a modified black-body assuming different dust opacities and temperatures (see below)." (4.1 ALMA 1.38 mm emission vs Herschel clump properties); "the total 1.38 mm continuum in the 4$\sigma$ contour of the PBCOR images in the *7m+tm2* configuration, provided that the area of the contour is larger than the synthesized beam" (4.1 ALMA 1.38 mm emission vs Herschel clump properties)
   - parameter: 7m+tm2 PBCOR continuum images used  
  > "we chose to use the *7m+tm2* continuum images with primary-beam-corrected fluxes (PBCOR)" (4.1 ALMA 1.38 mm emission vs Herschel clump properties)
   - assumption: T = 20-50 K and beta = 1.5-2  
  > "varying the temperature between 20 K and 50 K, dust spectral index $\beta$ between 1.5 and 2" (4.1 ALMA 1.38 mm emission vs Herschel clump properties)
   - assumption: Opacities from Preibisch+1993, Ossenkopf & Henning 1994 and Draine 2003  
  > "and assuming opacities from (cite: preib93), (cite: OH1994) and (cite: Draine2003)" (4.1 ALMA 1.38 mm emission vs Herschel clump properties)
   - fitting: _not stated_
   - validation: Checked whether discrepancy could come from different areas sampled by Herschel and ALMA  
  > "We conclude that it was only in 10% of the targets that the discrepancy in recovered flux could be attributed to differences in the areas of the sky sampled by *Herschel* and ALMA." (4.1 ALMA 1.38 mm emission vs Herschel clump properties)
5. **Correlate 5 sigma emission area with Herschel flux, surface density and L/M**: Pearson correlation of the total 5 sigma emission area in 7m+tm2+tm1 images against Herschel 350 um flux, clump surface density, L/M and mass; distance-bin checks  
  > "the 1.38 mm total emission area above 5$\sigma$ level in the ALMA *7m+tm2+tm1* image as a function of the *Herschel* 350 $\mu$m flux" (4.1 ALMA 1.38 mm emission vs Herschel clump properties)
   - assumption: Optically thin 1.38 mm emission, so emitting area is a proxy for resolved dust column density  
  > "The 1.38 mm emitting area, under the optically thin assumption, is a proxy for the dust column density spatially resolved in the ALMAGAL maps" (4.1 ALMA 1.38 mm emission vs Herschel clump properties)
   - fitting: _not stated_
   - validation: Distance bias excluded by repeating the plots in separate distance bins  
  > "To illustrate how we excluded the possible presence of a bias introduced by the different distances of the targets" (4.1 ALMA 1.38 mm emission vs Herschel clump properties)
6. **Quantify departure from circularity with the perimeter-area metric**: Plot summed perimeter against summed area of 5 sigma RoIs per field and define Delta-circ as the perpendicular distance from the single-circle line P = k A^(d/2)  
  > "Figure [10](#area_perim_roi) illustrates the perimeter-area plot for the 5$\sigma$ RoIs identified in each ALMAGAL field, where the two parameters have been summed over all RoI." (4.2.1 Area vs perimeter); "we defined a parameter $\Delta^{\rm circ} _{5\sigma}$ computed as the distance between each point and the black line (along the direction perpendicular to the line)" (4.2.1 Area vs perimeter)
   - parameter: k = 4 for a square and k = 2 sqrt(pi) for a circle; ellipse line uses P ~ pi sqrt(2(a^2+b^2)) with aspect ratio 3 (red line)  
  > "for instance, in 2D we have $k$=4 for a square or $k=2\sqrt{\pi}$ for a circle." (4.2.1 Area vs perimeter); "For the ellipse we adopted an approximation for $k$ obtained from the approximation formula P$_{\rm ellipse}\sim \pi\sqrt{2(a^2+b^2)}$." (footnote 3)
   - fitting: _not stated_
   - validation: Distance-bin check of the Delta-circ versus surface density trend  
  > "we exclude the presence of remarkable distance biases in Fig. [12](#deltacirc_surfd_fig) as similar trends are found if the two parameters are plotted for sources in 1 kpc-bin distances" (4.2.1 Area vs perimeter)
7. **Quantify convexity with the area to convex hull ratio**: Define Q_hull as the ratio of the largest RoI area to its convex hull area at 5 sigma, test bimodality, relate to L/M  
  > "we define the parameter $Q^{\rm hull} _{5\sigma}$ as the ratio $A_{RoI}/A_{C-Hull}$ between the area of the largest RoI and its convex hull area computed over the areas with signal above the 5$\sigma$ level" (4.2.2 Area versus convex hull)
   - parameter: Regular (Q_hull >= 0.8) versus irregular (Q_hull <= 0.8) split from the distribution  
  > "and suggests that there may possibly be two peaks in the distribution, separated at a value of $\sim$0.8" (4.2.2 Area versus convex hull)
   - fitting: Silverman multimodality test on kernel density estimates of the unbinned data; implementation details not stated  
  > "We ran the Silverman test (cite: Silverman1981) to characterize multi-modality using kernel density estimates over the distribution of the original data, and hence not on binned histograms." (4.2.2 Area versus convex hull)
   - validation: Checked that regular-looking fields are not only beam-like compact patches  
  > "There is, of course, a bias introduced by the finite resolution of the images." (4.2.2 Area versus convex hull)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of independent ALMAGAL fields analysed | 1013 | not stated | fields | 0 | (amounting to 1013 targets) |
| Adopted vLSR uncertainty | 1.4 | not stated | km/s | 1 | We assigned an uncertainty to the derived $v_{\rm LSR}$ of 1.4 km s$^{-1}$, which is the spectral resolution of the data. |
| Targets where new vLSR differs from original by more than 7 km/s | 77 | not stated | sources | 1 | In 77 sources, the new $v_{\rm LSR}$ values differ from the original ones by more than 7 km s$^{-1}$ in absolute value. |
| Targets with more than one emission feature in C18O (2-1) | 257 | not stated | targets | 1 | It is worth noting that in 257 ALMAGAL targets we found that more than one emission feature is present in the spectrum centered toward the C$^{18}$O (2–1) frequency |
| Targets whose vLSR relied on C18O and 13CO only | 207 | not stated | targets | 1 | were used only for 207 targets where none of the other higher critical density lines were detected |
| Sources with new distance differing by more than 0.5 kpc from original | 95 of 1013 | not stated | sources | 1 | We find that for 95 objects out of the total 1013 sources sample, the new distance differs by more than 0.5 kpc from the original one. |
| Sources switching from near to far subsample | 24 | not stated | sources | 1 | For 24 objects the change in distance is such that the source would switch from the |
| Sources switching from far to near subsample | 39 | not stated | sources | 1 | Conversely, for 39 objects, the change in distance is such that the source would switch from the |
| Sources placed beyond the 7.5 kpc limit | 44 | not stated | sources | 1 | for 44 objects, the new distance would put them beyond the 7.5 kpc distance limit adopted for the initial source selection |
| Fields with 4 sigma 7m+tm2 signal and fields within 50% of the Herschel flux | 941 of 1013 detected (~93%); 336 of 941 (~36%) within 50% | not stated | fields | 4 | Signal is detected toward 941 out of 1013 fields ($\sim$93%), and in 336 out of 941 fields ($\sim$36%), the discrepancy between the fluxes is less than 50%. |
| Fraction of fields with 7m+tm2 recovered flux much below 50% of Herschel flux | about 64% | not stated | percent of fields | 4 | For about 64% of the fields the rescaled *7m+tm2* recovered flux is much less than 50% of the *Herschel* flux |
| Pearson r, 5 sigma area versus Herschel 350 um flux | 0.74 | not stated | dimensionless | 5 | The Pearson linear correlation coefficient is $r_P$=0.74. |
| Pearson r, 5 sigma area versus clump surface density | 0.57 | not stated | dimensionless | 5 | Here again a correlation is clearly apparent, with $r_P$=0.57 suggesting indeed a good correlation |
| Pearson r, 5 sigma area versus L/M (all clumps) | 0.53 | not stated | dimensionless | 5 | The correlation coefficient for the entire dataset in Fig. [9](#roi-area_lm) is $r_P$=0.53 |
| Pearson r, area versus L/M for higher surface density clumps | 0.66 | not stated | dimensionless | 5 | the higher $\Sigma_{\mathrm{Clump}}$ points for which we have $r_P$=0.66 |
| Pearson r, area versus L/M for lower surface density clumps | 0.42 | not stated | dimensionless | 5 | with correlation coefficient dropping to $r_P$=0.42 |
| Pearson r, Delta-circ versus L/M for clumps with surface density >= 1 g cm-2 | ~0.46 | not stated | dimensionless | 6 | we are left with a moderate but significant $\Delta^{\rm circ} _{5\sigma}$-$L/M$ trend with $r_P$$\sim0.46$. |
| Q_hull value separating the two modes | ~0.8 | not stated | dimensionless | 7 | and suggests that there may possibly be two peaks in the distribution, separated at a value of $\sim$0.8 |
| Probability that Q_hull distribution is better described by two modes (Silverman test) | 100% | not stated | percent | 7 | has a 100% probability of being better described by two modes instead of one |
| Fraction of Q_hull >= 0.8 fields with area above the maximum beam area | ~44% | not stated | percent of fields | 7 | that instead contains $\sim44$% of the fields with $Q^{\rm hull} _{5\sigma}$$\geq$0.8 |

## Qualitative findings

- More extended and morphologically complex continuum shapes are found toward more evolved, higher surface density clumps  
  > "We find that more extended and morphologically complex (significantly departing from circular or generally convex) shapes are found toward clumps that are relatively more evolved and have higher surface densities." (abstract)
- For many fields the 7m+tm2 data miss flux from larger angular scales, so clump masses from ALMA fluxes are unreliable  
  > "This indicates that for a significant fraction of targets we may be missing flux from larger angular scales" (4.1 ALMA 1.38 mm emission vs Herschel clump properties)
- The area-surface density correlation disappears when clump mass is used instead  
  > "Furthermore the correlation present in Fig. [8](#roi-area_surf_d) completely disappears if we use the clump mass instead of its surface density" (4.1 ALMA 1.38 mm emission vs Herschel clump properties)
- Findings do not support massive fragmentation seeds that grow regularly with column density or temperature  
  > "Conversely, these findings do not support the notion of relatively massive seeds of fragmentation that regularly grow in extension with increasing column density or temperatures." (4.2.2 Area versus convex hull)

## Claim tuples

- H: Continuum morphology becomes more complex with clump evolutionary stage (L/M) | E: Compute Delta-circ and Q_hull of 5 sigma RoIs for 1013 fields and compare with L/M | R: Median Delta-circ rises with L/M and Q_hull decreases with L/M | F: Emission morphology gets more complex and irregular as clumps evolve | **supported**
- H: Clump-averaged surface density modulates the complexity of continuum morphology | E: Plot Delta-circ against Herschel-based surface density, with distance bins | R: Positive correlation with large scatter; almost all denser clumps depart from circular shapes | F: Higher surface density clumps show more complex morphology | **supported**
- H: The 1.38 mm 5 sigma emission area tracks Herschel clump properties | E: Pearson correlations of area against 350 um flux, surface density, L/M and mass | R: r = 0.74 (flux), 0.57 (surface density), 0.53 (L/M); no correlation with mass | F: Area depends on both initial surface density and evolutionary stage | **supported**
- H: The 7m+tm2 data recover the Herschel clump flux | E: Rescale 1.38 mm flux to 350 um and compare with Herschel for 941 detected fields | R: Only ~36% agree within 50%; ~64% recover much less than 50% | F: Significant missing flux from larger scales, mostly in low surface density fields | **supported**
- H: Q_hull separates regular and complex continuum morphologies | E: Histogram of Q_hull with Silverman bimodality test and area check against beam | R: Two modes separated at ~0.8; ~44% of Q_hull >= 0.8 fields have areas above the beam-like limit | F: Q_hull is a useful metric to classify convex versus non-convex emission | **supported**

## Reasoning

- Why this data: The ALMAGAL Large Program was designed to map more than 1000 intermediate and high-mass clumps in Band 6 at about 1000 au resolution for statistically significant fragmentation studies  
  > "The ALMAGAL Large Program was specifically designed to deliver this key science by mapping more than 1000 intermediate and high-mass dense clumps with ALMA in band 6" (1 Introduction)
- Why this method: 5 sigma threshold to limit noise residuals in the morphology analysis; 4 sigma for the flux comparison to recover more emission area when assessing missing flux  
  > "The 5$\sigma$ threshold was adopted to minimize the inclusion of noise residuals in the morphological analysis." (4 Properties of continuum emission); "to make sure we could recover as much as possible the emission area for a most reliable assessment of a missing flux problem" (4.1 ALMA 1.38 mm emission vs Herschel clump properties)
- Alternative: Mege+2021 default of placing unresolved-KDA Hi-GAL sources at the far distance was replaced by the near distance, as for RMS sources  
  > "(cite: Mege+2021) adopted (by default) the far distance, while in similar conditions, RMS sources (Urquhart et al. 2018) were put at the near distance" (3.2.1 Revision of targets distance)
- How they decided it was enough: _not stated_
- Limitation (authors): Original selection criteria are no longer fully met after revising distances and properties  
  > "These selection criteria, adopted at the time of the proposal, are no longer 100% fulfilled, following a revision of target physical parameters using the ALMAGAL data itself" (3.1 Initial selection and survey planning)
- Limitation (authors): Masses from integrated ALMA mm fluxes are unreliable for most fields due to missing flux  
  > "the use of physical parameters such as the total clump mass that could be derived from integrated ALMA millimeter fluxes is not reliable for the majority of the fields" (4.1 ALMA 1.38 mm emission vs Herschel clump properties)
- Limitation (authors): Finite image resolution biases the convexity metric for compact emission  
  > "There is, of course, a bias introduced by the finite resolution of the images." (4.2.2 Area versus convex hull)
- Limitation (authors): Sources whose distance changed did not reach the target 1000 au linear scale  
  > "for these sources as well, the target resolved 1000 au linear scale was not reached" (3.2.1 Revision of targets distance)
- Caveat (inferred, ours): Morphology metrics depend on the 5 sigma threshold, beam size and distance-dependent linear resolution; only distance-bin plots are shown as a bias check
- Caveat (inferred, ours): Correlations are reported as Pearson r without significance or uncertainties and with large scatter
- Caveat (inferred, ours): Clump L/M and surface density come from Herschel with low resolution, so evolutionary trends mix clump and sub-clump scales
- Caveat (inferred, ours): Missing flux in 7m+tm2 images may affect the 5 sigma area for low surface density fields
- Caveat (inferred, ours): Silverman test result (100%) lacks stated bandwidth or bootstrap details

## Reproducibility

- Data public (paper): Continuum images to be publicly released by December 2025 and cubes by December 2026; raw data under project 2019.1.00195.L are cited as ALMA archive data  
  > "A first complete public release of the *7m+tm2+tm1* and *7m+tm2* continuum images will be done after the acceptance of the first round of continuum-based papers introduced above" (6 Forward outlook); "so that their public release takes place no later than December 2026" (6 Forward outlook)
- Products in archive: _not stated_
- Missing: Calibrated and imaged ALMAGAL continuum products are not yet public; imaging recipe is in the companion paper
- Missing: Table 1 and Table 2 are only at the CDS
- Missing: Herschel Hi-GAL fluxes and SED fits required for L/M and surface density
- Missing: Exact implementations of perimeter, convex hull, Delta-circ and the Silverman test
- Data volume (inferred): Very large; 1013 fields with ACA plus two 12-m configurations and four spectral windows (likely tens of TB raw, though only continuum images are needed for the main morphology results)
- Score (inferred): 2/5, Score on a 1-5 scale. Morphology metrics are clearly defined and results numeric, but imaging recipe, calibration and Herschel inputs are deferred to other papers or the CDS and the images are not yet public.
- Rediscovery candidate: no, Recipe depends on unpublished ALMAGAL continuum products and companion papers, and the paper gives no imaging or calibration settings.

## Links

- Method: Sanchez-Monge et al. 2025 (cite: SanchezMonge+2025) (Companion paper with full observing setup, calibration and imaging pipeline)
- Method: Mege et al. 2021 (cite: Mege+2021) (Kinematic distance algorithm used to convert vLSR to distances)
- Method: Elia et al. 2017, 2021 (cite: Elia+2017; Elia+2021) (Hi-GAL clump catalogs and SED fitting for clump physical parameters)
- Method: Urquhart et al. 2022 (cite: Urquhart+2022) (Evolutionary classification of clumps)
- Companion: Coletta et al. 2025 (cite: Coletta+2025) (First ALMAGAL continuum compact source catalog and core mass function)
- Companion: Mininni et al. 2025 (cite: Mininni+2025) (Multiscale morphology of dust continuum and molecular line emission)
- Companion: Wells et al. 2024 (cite: Wells+2024) (Flow dynamics in 100 ALMAGAL fields from H2CO lines)
- Related: Hi-GAL
- Related: RMS survey
- Related: ATLASGAL
- Related: CORNISH
- Related: ALMA-IMF
- Related: ASHES
- Related: ATOMS
- Related: TEMPO
- Related: SQUALO
- Related: ASSEMBLE

## Checks

```json
{
 "quotes": 126,
 "quotes_ok": 126,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 20,
 "numeric_problems": 0,
 "fill": {
  "facts": 99,
  "stated": 69,
  "rate": 0.697
 },
 "evidence_ok": true
}
```
