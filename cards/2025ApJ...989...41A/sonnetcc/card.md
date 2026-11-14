# Discovery of Jet─Bubble─Disk Interaction: Jet Feedback on a Protoplanetary Disk Via an Expanding Bubble in WSB 52

`2025ApJ...989...41A` | The Astrophysical Journal 2025 | first author: Aizawa, Masataka | arXiv: 2501.10121 | DOI: 10.3847/1538-4357/add47e

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Do stellar jets directly affect a protoplanetary disk? Identify and characterise an expanding 12CO bubble around WSB 52 and test whether it interacts with and deforms the disk.  
  > "We identify an expanding bubble that interacts with its protoplanetary disk." (abstract); "While stellar jets and outflows are fueled by accretion from disks, their direct influence on disks remain unexplored." (abstract)
- Target **WSB 52**: coordinates not stated (only offsets from the observational center, x*=-0.12 arcsec, y*=-0.43 arcsec, are given)  
  > "The target in this paper, WSB 52, is a T Tauri star in Class II phase, located $135.27\pm0.92$ pc away from the Earth (cite: gaia2016; gaia2023), in the Ophiuchus region." (Observation and Data Reduction); z/distance 135.27 +/- 0.92 pc  
  > "The target in this paper, WSB 52, is a T Tauri star in Class II phase, located $135.27\pm0.92$ pc away from the Earth (cite: gaia2016; gaia2023), in the Ophiuchus region." (Observation and Data Reduction); distance from Gaia (cite: gaia2016; gaia2023)  
  > "The target in this paper, WSB 52, is a T Tauri star in Class II phase, located $135.27\pm0.92$ pc away from the Earth (cite: gaia2016; gaia2023), in the Ophiuchus region." (Observation and Data Reduction)

## Data provenance

- ALMA projects: 2015.1.00486.S, 2015.1.00964.S
- bands: _not stated_
- frequencies and spectral setup: 12CO (J=2-1) cube reconstructed over v_LSR = -15.70 to 29.45 km/s, channel spacing 0.35 km/s (actual velocity resolution about two channels)  
  > "extending the line-of-sight velocity range to $v_{\rm LSR} = -15.70$ km/s to $29.45$ km/s." (Observation and Data Reduction); "The reconstructed cube data have a channel spacing of $0.35$ km/s and an image pixel size of $0.01$ arcsec." (Observation and Data Reduction); "the actual velocity resolution is about two channels, because of Hanning smoothing in the ALMA correlators." (Observation and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.141 x 0.092 arcsec, PA -85.5 deg  
  > "The synthesized beam size is $0.141 \times 0.092$ arcsec with a position angle of $-85.5^{\circ}$." (Observation and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival ALMA data (DSHARP); raw measurement set downloaded from the ALMA archive  
  > "The measurement set, downloaded from the ALMA archive, is processed using the Common Astronomy Software Applications (CASA) pipeline (version 4.7.2)" (Observation and Data Reduction); "The star harbors a dusty disk with a gap structure, as observed by ALMA in DSHARP (The Disk Substructures at High Angular Resolution Project)" (Observation and Data Reduction)
- Line: 12CO J=2-1 (not stated)
- Other facility **Gaia**: Distance to WSB 52 (135.27 pc)  
  > "Distance \[pc\] | 135.27 | (cite: gaia2023)" (Table 1)
- Other facility **DSHARP data release**: Released 12CO(2-1) cube (insufficient velocity coverage), 1 mJy/beam continuum image used for the outer disk radius, and the standard imaging/self-calibration scripts  
  > "The image is taken from the DSHARP observation at <https://almascience.eso.org/almadata/lp/DSHARP/>, and a contour level of 1 mJy/beam is used to approximate the outer disk radius." (3.1 The expanding bubble); "We began our analysis by examining the $^{12}\mathrm{CO}\,(J=2\mbox{--}1)$ cube data, available on the DSHARP data release webpage." (Observation and Data Reduction)
- External data: Stellar and disk parameters used in modelling (stellar mass 0.4786 Msun, disk position, inclination 54.4 deg, PA 138.4 deg)  
  > "lists the stellar and disk parameters, as used or reported in (cite: andrews2018) and (cite: huang2018)." (Observation and Data Reduction) [from (cite: andrews2018); (cite: huang2018)]
- External data: Gaia distance, 135.27 pc  
  > "Distance \[pc\] | 135.27 | (cite: gaia2023)" (Table 1) [from (cite: gaia2023)]
- External data: WSB 52 mass accretion rate 10^(-7.6+/-0.5) Msun/yr, used for the jet-energy argument  
  > "the mass accretion rate for WSB 52 was estimated to be $10^{-7.6 \pm 0.5}, M_{\odot}/\mathrm{yr}$ (cite: Natta2006; andrews2018)" (4.1 The proposed scenario for the observation) [from (cite: Natta2006; andrews2018)]
- External data: Jet mass ejection rates of Class II T Tauri stars, 1e-9 to 1e-7 Msun/yr  
  > "The jet mass ejection rates for Class II T Tauri stars have been found to range from $10^{-9}$ to $10^{-7}$ $M_{\odot}/{\rm yr}$ (cite: Ellerbroek2013)." (4.1 The proposed scenario for the observation) [from (cite: Ellerbroek2013)]
- External data: Possible shallow gap/ring pairs in the dust disk at 13/17 and 21/25 au  
  > "with possible shallow gap/ring pairs at 13/17 and 21/25 au (cite: jennings2022)" (3.3 The deformation of the disk by the expanding bubble) [from (cite: jennings2022)]

## Processing

### Calibration

- pipeline or manual: Archive measurement set processed with the CASA pipeline by EA-ARC, then self-calibration with the standard DSHARP analysis script  
  > "is processed using the Common Astronomy Software Applications (CASA) pipeline (version 4.7.2) by the East Asian ALMA Regional Center (EA-ARC), followed by self-calibration with the standard DSHARP analysis script using CASA 6.6.5." (Observation and Data Reduction)
- casa version: CASA pipeline 4.7.2 (calibration); CASA 6.6.5 (self-calibration)  
  > "followed by self-calibration with the standard DSHARP analysis script using CASA 6.6.5." (Observation and Data Reduction); "(CASA) pipeline (version 4.7.2) by the East Asian ALMA Regional Center (EA-ARC)" (Observation and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Standard DSHARP analysis script (CASA 6.6.5); no solution intervals given  
  > "followed by self-calibration with the standard DSHARP analysis script using CASA 6.6.5." (Observation and Data Reduction)

### Imaging

- task: CLEAN with standard DSHARP script parameters except gain = 0.2, niter = 200000, threshold = 2.5 mJy, imsize = 2000  
  > "For CLEAN imaging, we basically adopt the same parameters as the standard script but slightly adjust the following parameters;" (Observation and Data Reduction); "${\tt gain}=0.2$, ${\tt niter}=200000$, ${\tt threshold}=2.5$ mJy, and ${\tt imsize}= 2000$." (Observation and Data Reduction)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.01 arcsec  
  > "an image pixel size of $0.01$ arcsec." (Observation and Data Reduction)
- image size: imsize = 2000  
  > "and ${\tt imsize}= 2000$." (Observation and Data Reduction)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: Applied to the image  
  > "We apply the primary beam correction to the image." (Observation and Data Reduction)
- array combination: _not stated_
- smoothing: For the mass estimate only: cube smoothed to a 0.25 arcsec beam  
  > "To reduce the biases, we also smooth the cube data using a beam size of 0.25 arcsec reducing the number of negative pixels." (Appendix: Estimation of mass and kinematic energy of bubble)
- final beam: 0.141 x 0.092 arcsec, PA -85.5 deg  
  > "The synthesized beam size is $0.141 \times 0.092$ arcsec with a position angle of $-85.5^{\circ}$." (Observation and Data Reduction)
- final rms: _not stated_

### Inherited from earlier work

- Remaining CLEAN imaging parameters (deconvolver, weighting, masking, etc.) taken from the standard DSHARP script  
  > "For CLEAN imaging, we basically adopt the same parameters as the standard script but slightly adjust the following parameters;" (Observation and Data Reduction) [from standard DSHARP analysis script (DSHARP Data Release; Andrews et al. 2018, (cite: andrews2018))]
- Self-calibration procedure  
  > "followed by self-calibration with the standard DSHARP analysis script using CASA 6.6.5." (Observation and Data Reduction) [from standard DSHARP analysis script]
- Effective velocity resolution about two channels due to Hanning smoothing  
  > "As noted in (cite: andrews2018), the actual velocity resolution is about two channels, because of Hanning smoothing in the ALMA correlators." (Observation and Data Reduction) [from (cite: andrews2018)]
- Keplerian disk model for iso-velocity masks  
  > "we compare a Keplerian disk model (cite: 2020zndo...4321137T; 2021ApJS..257....2C) with the observed disk." (3.3 The deformation of the disk by the expanding bubble) [from (cite: 2020zndo...4321137T; 2021ApJS..257....2C)]
- LTE column-density formalism from the integrated optical depth  
  > "we can derive the molecular column density from the observed optical depth as follows (cite: mangum2015; orihara2023)" (Appendix: Estimation of mass and kinematic energy of bubble) [from (cite: mangum2015; orihara2023)]

### Not stated but needed to reproduce (our reading)

- The DSHARP script settings not overridden in the paper: tclean/CLEAN deconvolver, weighting and robust value, masks, uv-taper, and the self-calibration solution intervals and rounds.
- Which execution blocks / configurations of 2015.1.00486.S and 2015.1.00964.S were combined, and the observing dates, baselines, and time on source.
- The continuum subtraction method and the line-free channels used before imaging the 12CO cube.
- Whether the cube was made at the 0.35 km/s channel width via regridding or restoring-frequency choices (rest frequency, velocity reference frame, interpolation) in the CLEAN call.
- The final rms noise of the cube, needed for the 3-sigma criterion in the mass estimate.
- The observed bubble-rim positions and the hand-digitised shock-boundary points (and the optimiser used) needed to reproduce the shock-boundary fit.
- The exact temperature grid (text says 25-100 K, appendix says 25-95 K in steps of 10 K) and which integration method gives which mass.
- Systemic-velocity choice for the Keplerian model is only approximate (3.9 km/s, uncertain by 0.5-1.0 km/s) and no goodness-of-fit metric is defined.

## Analysis recipe

1. **Rebuild the 12CO cube from raw archive data**: Download the measurement set, calibrate with the CASA pipeline at EA-ARC, self-calibrate with the DSHARP script, and re-image the 12CO(2-1) cube with extended velocity range and primary beam correction  
  > "we reconstruct the image cube from the raw data, extending the line-of-sight velocity range to $v_{\rm LSR} = -15.70$ km/s to $29.45$ km/s." (Observation and Data Reduction); "We apply the primary beam correction to the image." (Observation and Data Reduction)
   - software: CASA, DSHARP standard analysis script
   - parameter: gain = 0.2, niter = 200000, threshold = 2.5 mJy, imsize = 2000  
  > "${\tt gain}=0.2$, ${\tt niter}=200000$, ${\tt threshold}=2.5$ mJy, and ${\tt imsize}= 2000$." (Observation and Data Reduction)
   - parameter: channel spacing 0.35 km/s, pixel 0.01 arcsec  
  > "The reconstructed cube data have a channel spacing of $0.35$ km/s and an image pixel size of $0.01$ arcsec." (Observation and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit an expanding spherical bubble to the shell patterns**: Uniformly expanding spherical shell model giving the rim radius at each line-of-sight velocity; parameters (centre, radius, expansion velocity, systemic velocity) tuned to match observed rims in the channel maps  
  > "The model described above provides the location of the bubble rim for each observed line-of-sight velocity." (3.1 The expanding bubble); "we plot the circles with the center $(x_{\rm bubble}, y_{\rm bubble})$ and the radii of $r(v_{\rm LOS})$, and then compare them to the cube data." (3.1 The expanding bubble)
   - parameter: Free parameters: x_bubble, y_bubble, r_bubble, u_bubble, v_sys,bubble  
  > "characterized by the central position $(x_{\rm bubble}, y_{\rm bubble})$, bubble radius $r_{\rm bubble}$, radial expansion velocity $u_{\rm bubble}$, and systematic velocity $v_{\rm sys, bubble}$." (3.1 The expanding bubble)
   - assumption: Distance d = 135.27 pc to convert arcsec to au  
  > "we can convert it into physical scales by using the distance $d=135.27$ pc." (3.1 The expanding bubble)
   - assumption: Bubble centre lies on the disk axis (also in 3D)  
  > "We thus assume that the bubble center to be on the line of the disk axis in determining $(x_{\rm bubble}, y_{\rm bubble})$." (3.1 The expanding bubble)
   - fitting: Visual optimisation (no numerical optimiser, no priors or likelihood)  
  > "We have opted to employ a visual optimization of the parameters by comparing the observed bubble rims to the model prediction." (3.1 The expanding bubble)
   - validation: Model rims overlaid on the channel maps agree with the observed bubble  
  > "Despite its simplicity, the model demonstrates a high degree of agreement with the observational data." (3.1 The expanding bubble)
3. **Estimate bubble mass and kinetic energy from 12CO intensities**: LTE column density from optical depth derived from the observed intensity and the Planck function, integrated over pixels between two circles around the bubble; E = 1/2 M u_bubble^2  
  > "The mass is derived by integrating Eq. ([\[eq:sigma_mass\]](#eq:sigma_mass)) over each pixel, using the estimates of $\tau_{\rm g}$ obtained from the real cube data." (Appendix: Estimation of mass and kinematic energy of bubble); "The integration region is defined between two circles corresponding to the bubble models with radii $r_{\rm bubble} = 4$ and $7.0$ arcsec." (Appendix: Estimation of mass and kinematic energy of bubble)
   - parameter: Disk emission excluded within 1.5 arcsec of the star  
  > "To remove the contribution from disk emission, we exclude intensities within 1.5 arcsec from the star." (Appendix: Estimation of mass and kinematic energy of bubble)
   - parameter: Channels with v_LOS 1.45 to 6 km/s removed (cloud contamination)  
  > "We also remove channels with $v_{\rm LOS}$ between 1.45 and 6 km/s to eliminate cloud contamination." (Appendix: Estimation of mass and kinematic energy of bubble)
   - parameter: Gas temperature varied from 25 K to 95 K in steps of 10 K (appendix); main text says 25 K to 100 K  
  > "so we vary the temperature from $25$ K to $95$ K in steps of $10$ K." (Appendix: Estimation of mass and kinematic energy of bubble); "Assuming local thermodynamic equilibrium (LTE) with gas temperatures ranging from 25 K to 100 K" (3.1 The expanding bubble)
   - assumption: LTE, T_ex equal to gas temperature; 12CO not fully optically thick  
  > "under the assumption that the emission is not completely optically thick." (3.1 The expanding bubble); "which is assumed to be equal to the gas temperature in the LTE analysis" (Appendix: Estimation of mass and kinematic energy of bubble)
   - assumption: CO abundance relative to H2 X = 1e-4  
  > "We assume $X=10^{-4}$ for $^{12}$CO." (Appendix: Estimation of mass and kinematic energy of bubble)
   - assumption: u_bubble = 12.5 km/s used for the kinetic energy  
  > "Assuming $u_{\rm bubble} = 12.5$ km/s and the mass range" (Appendix: Estimation of mass and kinematic energy of bubble)
   - fitting: _not stated_
   - validation: Three integration treatments of negative intensities (zero-clip, 3-sigma only, unconditional) plus smoothing used to gauge mass uncertainty; described as order-of-magnitude  
  > "To understand the possible uncertainty in the mass, we employ three different integration methods" (Appendix: Estimation of mass and kinematic energy of bubble); "We perform an order-of-magnitude estimation of the bubble’s mass and kinematic energy" (Appendix: Estimation of mass and kinematic energy of bubble)
4. **Fit the shock boundary (concave region) between bubble and star**: Axisymmetric power-law surface zeta_surf(rho) = h_shock (rho/1 arcsec)^a + zeta_0 joined to the bubble sphere; predicted iso-velocity contours compared with hand-picked boundary points and parameters optimised numerically by minimising the summed point-to-contour distances  
  > "we manually approximate the observed shock boundaries by discrete points along each channel." (3.2 The shock boundary between bubble and the stellar vicinity); "We minimize this aggregate distance by adjusting the parameters of the bubble model." (3.2 The shock boundary between bubble and the stellar vicinity)
   - parameter: r_bubble fixed to 5.5 and 6.5 arcsec (two cases)  
  > "we adopt two values for $r_{\rm bubble}$, namely $5.5 \ensuremath{''}$ and $6.5\ensuremath{''}$." (3.2 The shock boundary between bubble and the stellar vicinity)
   - parameter: Fitted: a = 2.14, h_shock = 0.18 arcsec, zeta_0 = -0.28 arcsec  
  > "$h_{\rm shock}$ \[arcsec\] | 0.18" (Table 2 (Model Parameters)); "$a$ | 2.14" (Table 2 (Model Parameters))
   - assumption: Shock boundary nearly axisymmetric about the disk axis; bubble centre on the disk axis in 3D; star depth from inclination and projected separation  
  > "the shock boundary is nearly axisymmetric with respect to the disk axis, and (b) the bubble center lies on the disk axis in three-dimensional space" (3.2 The shock boundary between bubble and the stellar vicinity)
   - assumption: Velocity on the boundary radial from the bubble centre with constant amplitude u_bubble  
  > "we assume that the velocity direction aligns with the radial direction from the bubble center, and the velocity amplitude is constant, $u_{\rm bubble}$." (3.2 The shock boundary between bubble and the stellar vicinity)
   - fitting: Numerical minimisation of the sum over selected channels of the minimum point-to-contour distances (algorithm not named)  
  > "The total distance metric is defined as the sum of these minimum distances across all selected channels." (3.2 The shock boundary between bubble and the stellar vicinity)
   - validation: Optimised contours overlaid on channel maps reasonably replicate the observed boundary  
  > "Our model reasonably replicates the observed shock boundary morphology, supporting our estimation of the stellar position." (3.2 The shock boundary between bubble and the stellar vicinity)
5. **Compare a Keplerian flared-disk model with the observed disk kinematics**: Keplerian iso-velocity masks for the upper layer of a flared axisymmetric disk, plotted as dashed lines on zoomed channel maps and compared by eye  
  > "The dashed lines in Figure [5](#fig:channelszoom) present a Keplerian disk model, which delineates the iso-velocity surfaces of the disk’s flared upper layer as described." (3.3 The deformation of the disk by the expanding bubble); "we make the masked region with $|v_{\rm model} - v_{\rm chan}| < \Delta v_{\rm chan}$." (3.3 The deformation of the disk by the expanding bubble)
   - software: Keplerian_Mask_Generator (authors' code), keplerian_mask
   - parameter: h_0 = 5 au, p = 1  
  > "We present results using $h_0 = 5$ au and $p = 1$" (3.3 The deformation of the disk by the expanding bubble)
   - parameter: v_sys,* = 3.9 km/s (uncertain by 0.5-1.0 km/s)  
  > "As the reference value we assume it to be $3.9$ km/s, but it may vary 0.5-1.0 km/s based on the observed maps." (3.3 The deformation of the disk by the expanding bubble)
   - parameter: Outer disk radius 150 au  
  > "The outer disk radius is assumed to be $150$ au." (3.3 The deformation of the disk by the expanding bubble)
   - assumption: Stellar mass, inclination and PA from the literature table; axisymmetric disk; only the upper layer; intrinsic line width ignored  
  > "In the modeling, we adopt the stellar mass and the disk parameters in Table" (3.3 The deformation of the disk by the expanding bubble); "We assume an axisymmetric disk." (3.3 The deformation of the disk by the expanding bubble); "Here, we ignore the intrinsic line widths for the simplicity." (3.3 The deformation of the disk by the expanding bubble)
   - fitting: _not stated_
   - validation: Other parameter choices tested; discrepancies persist, so the curvature is attributed to deformation; high-velocity gas up to ~18 km/s exceeds the escape velocity  
  > "We also test other parameters but consistently observe significant discrepancies, indicating intrinsic deformations likely caused by external forces." (3.3 The deformation of the disk by the expanding bubble); "reaching up to approximately $v_{\rm LOS} = 18$ km/s" (3.3 The deformation of the disk by the expanding bubble)
6. **Estimate disk displacement from bubble ram pressure and check jet energy budget**: Ram-pressure momentum argument giving vertical displacement D_zeta = Sigma_flow v_flow dt / (2 Sigma_disk) with Sigma_flow = M_bubble / (4 pi r_bubble^2); two cases (current bubble; earlier closer phase); jet energy rate compared with the bubble energy  
  > "This deformation may be explained by considering the ram pressure exerted by the bubble on the disk" (4.2 Simple model for disk deformation by bubble expansion); "This energy output is sufficient to drive an expanding bubble with kinetic energy in the range of $0.4-4 \times 10^{41}$ erg within one to ten years." (4.1 The proposed scenario for the observation)
   - parameter: Current-bubble case: v_flow = 12.5 km/s, r_bubble = 700 au, dt = 50 yr, Sigma_disk = 1 g/cm^2  
  > "$\Delta t$ is taken to be 50 yr, approximately equal to the shell’s crossing time over 1 arcsec." (4.2 Simple model for disk deformation by bubble expansion)
   - parameter: Earlier-phase case: v_rel = 7.5 km/s, v_flow = 5 km/s, r_bubble = 30 au, dt = 20 yr  
  > "Assuming a relative velocity of $v_{\rm rel}= 7.5$ km/s ($\simeq$ 1.5 au/yr)" (4.2 Simple model for disk deformation by bubble expansion)
   - assumption: Sigma_disk = 1 g/cm^2; M_bubble = 1e-4 Msun fiducial  
  > "Under the assumption $\Sigma_{\rm disk}=1\,\text{g/cm}^2$, the vertical displacement is approximately 0.01 au." (4.2 Simple model for disk deformation by bubble expansion)
   - fitting: _not stated_
   - validation: Described as a preliminary interpretation; the present-day case is inconsistent with the observed deformation  
  > "Although the current model provides a preliminary interpretation of the disk deformation" (4.2 Simple model for disk deformation by bubble expansion)

## Software

- **CASA** 4.7.2 (pipeline); 6.6.5 (self-calibration and imaging): Pipeline calibration (EA-ARC), self-calibration and CLEAN imaging  
  > "followed by self-calibration with the standard DSHARP analysis script using CASA 6.6.5." (Observation and Data Reduction); "(CASA) pipeline (version 4.7.2) by the East Asian ALMA Regional Center (EA-ARC)" (Observation and Data Reduction)
- **DSHARP standard analysis script** : Self-calibration and baseline CLEAN parameters  
  > "The original code used for reconstrucing the images is available in the DSHARP Data Release at https://bulk.cv.nrao.edu/almadata/lp/DSHARP." (Code availability)
- **Keplerian_Mask_Generator** : Authors' own Keplerian mask code for the disk model comparison  
  > "we use our code for the Keplerian mask, which is publicly available at <https://github.com/rorihara/Keplerian_Mask_Generator>" (3.3 The deformation of the disk by the expanding bubble)
- **keplerian_mask** 1.0: Existing Keplerian mask code (Teague) cited as the alternative that the authors' code is faster than  
  > "overall faster than an existing code, `keplerian_mask` at <https://github.com/richteague/keplerian_mask>" (3.3 The deformation of the disk by the expanding bubble)
- **CARTA** : _not stated_
- **Astropy** : _not stated_
- **Jupyter Notebook** : _not stated_
- **Matplotlib** : _not stated_
- **NumPy** : _not stated_
- **Pandas** : _not stated_
- **SciPy** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Synthesized beam | 0.141 x 0.092 arcsec, PA -85.5 deg | not stated | arcsec, deg | 1 | The synthesized beam size is $0.141 \times 0.092$ arcsec with a position angle of $-85.5^{\circ}$. |
| Bubble radius | approximately 750 au (5.5 arcsec) | not stated | au | 2 | The inferred radius of the bubble is approximately 750 au, and the expansion velocity is 12.5 km/s. |
| Bubble expansion velocity u_bubble | 12.5 | not stated | km/s | 2 | The inferred radius of the bubble is approximately 750 au, and the expansion velocity is 12.5 km/s. |
| Bubble distance from the star | 580 | not stated | au | 2 | indicating a distance between the bubble center and the star of 580 au if $i = 58.4^{\circ}$ |
| Bubble systemic velocity v_sys,bubble | -0.25 | not stated | km/s | 2 | In addition, $v_\mathrm{{sys, bubble}}$, $-0.25$ km/s, is blue-shifted from the systemic velocity of the star. |
| Bubble gas mass M_shell | (0.2-1.1) x 10^-4 | range over T = 25-100 K and integration methods | Msun | 3 | we derive a total mass of $M_{\rm shell} = (0.2-1.1) \times10^{-4}$ $M_{\odot}$. |
| Bubble kinetic energy E_shell | (0.3-1.6) x 10^41 | range | erg | 3 | we estimate a kinetic energy of $E_{\rm shell} = (0.3-1.6) \times10^{41}$ erg. |
| Shock apex to star distance zeta_0 | -0.28 arcsec (about 38 au) | not stated | arcsec | 4 | is $\zeta_0 = -0.28\ensuremath{''}$, which corresponds to approximately 38 au. |
| Shock boundary power-law index a | 2.14 | not stated | dimensionless | 4 | $a$ / 2.14 |
| Shock boundary height h_shock | 0.18 | not stated | arcsec | 4 | $h_{\rm shock}$ \[arcsec\] / 0.18 |
| Bubble/shock intersection (rho_inter, theta_inter) for r_bubble = 5.5 and 6.5 arcsec | (2.23 arcsec, 23.9 deg) and (2.92 arcsec, 26.7 deg) | not stated | arcsec, deg | 4 | where $(\rho_{\rm inter}, \theta_{\rm inter}) = (2.23\ensuremath{''}, 23.9^{\circ})$ and $(2.92\ensuremath{''}, 26.7^{\circ})$, respectively. |
| Stellar systemic velocity v_sys,* | 3.9 | may vary 0.5-1.0 km/s | km/s | 5 | As the reference value we assume it to be $3.9$ km/s, but it may vary 0.5-1.0 km/s based on the observed maps. |
| Maximum high-velocity component near the disk | approximately 18 | not stated | km/s | 5 | reaching up to approximately $v_{\rm LOS} = 18$ km/s |
| Vertical disk displacement from present-day bubble ram pressure | approximately 0.01 | not stated | au | 6 | the vertical displacement is approximately 0.01 au. |

## Qualitative findings

- The bubble is not perfectly spherical and is brighter on the side near the star.  
  > "The bubble is not perfectly spherical but shows notable asymmetry, appearing particularly bright near the star." (3.1 The expanding bubble)
- The compact dust disk appears unaffected by the shock.  
  > "appears unaffected by the shock." (3.3 The deformation of the disk by the expanding bubble)
- No similar events were found in the other DSHARP targets.  
  > "Note that, aside from WSB 52, we also examined the other DSHARP targets but did not identify similar events in any of the other systems." (Observation and Data Reduction)

## Claim tuples

- H: Do the shell-like 12CO patterns trace a uniformly expanding bubble offset from the star? | E: Fit a uniform-expansion spherical shell model to the channel-map rims by visual optimisation. | R: Radius about 750 au, expansion 12.5 km/s, centre offset (2.50, 1.90) arcsec, v_sys,bubble -0.25 km/s; model rims agree with the data. | F: An expanding bubble centred on the disk axis, with the star inside it, explains the shell patterns. | **supported**
- H: Is the concave morphology near the star a shock boundary produced by the bubble-disk interaction? | E: Fit an axisymmetric power-law surface joined to the bubble sphere to hand-picked boundary points by numerical minimisation. | R: zeta_0 = -0.28 arcsec (about 38 au), a = 2.14, h_shock = 0.18 arcsec for r_bubble = 5.5 / 6.5 arcsec. | F: The model reasonably replicates the observed shock boundary. | **supported**
- H: Is the WSB 52 disk deformed and losing mass because of the bubble? | E: Compare Keplerian flared-disk iso-velocity masks with the zoomed channel maps and search for high-velocity gas; estimate ram-pressure displacement. | R: The simple flared Keplerian model cannot reproduce the curvature; gas reaches about 18 km/s, above the escape velocity; the present-day ram-pressure displacement is only about 0.01 au, but an earlier, closer phase could give a larger displacement. | F: The disk is deformed and may be losing mass through the bubble interaction, though a quantitative dynamical model is left to future work. | **partially**
- H: Can past stellar jets supply the bubble energy (jet-bubble-disk interaction)? | E: Estimate bubble mass and energy from 12CO under LTE and compare with a jet energy rate from literature mass-ejection rates. | R: Bubble energy (0.3-1.6)e41 erg; a jet outburst of 1e-7 Msun/yr at 200 km/s gives about 0.4e41 erg/yr. | F: The energy is consistent with jet-driven origin, though the bubble origin remains uncertain. | **partially**

## Reasoning

- Why this data: The released DSHARP cube lacked the velocity range needed, so the cube was rebuilt from the raw archive data.  
  > "we found that the velocity coverage of the released image cube was insufficient to fully capture the features of our interest" (Observation and Data Reduction)
- Why this method: Visual optimisation chosen for the bubble because numerical optimisation depends on arbitrary choices of metric.  
  > "This approach is motivated by the fact that a numerical optimization is susceptible to the arbitrary choices of the optimization function and criteria when analyzing such a complex phenomenon." (3.1 The expanding bubble)
- Alternative: Manual optimisation was tried for the shock boundary but replaced by numerical optimisation because of model complexity.  
  > "however, due to the model’s increased complexity, we relied on numerical optimization." (3.2 The shock boundary between bubble and the stellar vicinity)
- Alternative: A simple flared Keplerian disk (several parameter choices) rejected as an explanation of the disk curvature.  
  > "demonstrating that the observed curvature of the disk cannot be accounted for by a simple flared disk model." (3.3 The deformation of the disk by the expanding bubble)
- Alternative: Sideways bow-shock motions and outflow phenomena distinguished from the expanding bubble.  
  > "which is distinct from sideways motions of bow shocks perpendicular to the jet directions (cite: Tafalla2017) and from outflow phenomena (cite: harada2023)." (4.1 The proposed scenario for the observation)
- How they decided it was enough: Stopped when the model rims agreed well with the observed bubble.  
  > "The obtained solution is in strong agreement with the observed bubble" (3.1 The expanding bubble)
- Limitation (authors): Extended cloud emission obscures channels near the systemic velocity, leaving v_sys,* highly uncertain.  
  > "contamination from extended molecular cloud emission around WSB 52 obscured the circumstellar gas" (Observation and Data Reduction); "the star’s systemic velocity $v_{\text{sys},\star}$ remains highly uncertain." (3.3 The deformation of the disk by the expanding bubble)
- Limitation (authors): The bubble origin is uncertain; similar CO bubbles are not seen in XZ Tau or SVS 13.  
  > "We therefore caution that the origin of the bubble in WSB 52 remains uncertain and warrants further investigation." (4.1 The proposed scenario for the observation)
- Limitation (authors): The analysis relies on a single line, 12CO (J=2-1); isotopologue and other-species follow-up is needed.  
  > "Therefore, follow-up observations of CO isotopes are highly desirable to gain a better understanding of the mass and temperature distribution." (Conclusion)
- Limitation (authors): The disk-deformation model is only preliminary.  
  > "Although the current model provides a preliminary interpretation of the disk deformation" (4.2 Simple model for disk deformation by bubble expansion)
- Caveat (inferred, ours): Bubble fit is by eye with no uncertainties; the quoted parameters have no error bars, so exact reproduction of 12.5 km/s and 750 au is not defined.
- Caveat (inferred, ours): The inclination is quoted as 54.4 deg in Table 1 but 58.4 deg in the 580 au distance sentence in Sec 3.1.
- Caveat (inferred, ours): The gas temperature range is 25-100 K in the main text but 25-95 K in the appendix; the 12CO optical-depth mass is sensitive to the assumed T and to the CO/H2 abundance of 1e-4.
- Caveat (inferred, ours): No second tracer or isotopologue is used, so optically thin mass and the 12CO optical-depth treatment are weakly constrained.
- Caveat (inferred, ours): The jet origin is not tested; no jet is detected, and no other DSHARP system shows a bubble.
- Caveat (inferred, ours): The ram-pressure estimate gives a negligible displacement in the present geometry, so the disk deformation relies on an assumed earlier interaction phase.

## Reproducibility

- Data public (paper): Raw ALMA data are public in the ALMA archive; DSHARP data public in the DSHARP release  
  > "The raw ALMA data are publicly available via the ALMA archive https://almascience.nrao.edu/aq/." (Availability of data and materials); "The DSHARP data used in this article are available in the DSHARP Data Release at https://bulk.cv.nrao.edu/almadata/lp/DSHARP." (Availability of data and materials)
- Products in archive: The reconstructed 12CO(2-1) cube is provided on Zenodo (DOI 10.5281/zenodo.15314468)  
  > "image cube is provided in <https://doi.org/10.5281/zenodo.15314468>." (Availability of data and materials)
- Code: Keplerian mask code at github.com/rorihara/Keplerian_Mask_Generator  
  > "The Keplerian mask code is publicly available at <https://github.com/rorihara/Keplerian_Mask_Generator>." (Code availability)
- Code: Image reconstruction code is the DSHARP release script  
  > "The original code used for reconstrucing the images is available in the DSHARP Data Release at https://bulk.cv.nrao.edu/almadata/lp/DSHARP." (Code availability)
- Missing: Bubble-fit and shock-boundary fitting code, digitised boundary points, and the optimiser used.
- Missing: Mass and energy calculation code and the mapping of integration methods to results.
- Missing: Full CLEAN parameters and self-calibration settings beyond the four overridden parameters; ALMA execution blocks used.
- Missing: Continuum subtraction and line-free channel choices.
- Data volume (inferred): Raw measurement sets for two ALMA projects likely tens of GB; a 2000 x 2000 x ~129 channel cube is about 2 GB; the Zenodo cube avoids re-imaging.
- Score (inferred): 3/5, Data and the final cube are public and key numbers are given, but the bubble and Keplerian comparisons are done by eye, the shock-boundary points and code are not published, and most imaging settings are inherited from the DSHARP script.
- Rediscovery candidate: no, Data are public, but the central results come from visual model tuning and hand-picked boundary points that cannot be redone from the text alone.

## Links

- Method: Andrews et al. 2018 (cite: andrews2018) (DSHARP data, imaging script and WSB 52 parameters)
- Method: Huang et al. 2018 (cite: huang2018) (Disk inclination, PA and centre used in the models)
- Method: Mangum & Shirley 2015 (cite: mangum2015); Orihara et al. 2023 (cite: orihara2023) (LTE column density formalism)
- Method: Teague 2020 (cite: 2020zndo...4321137T); Czekala et al. 2021 (cite: 2021ApJS..257....2C) (Keplerian mask approach)
- Related: DSHARP (Disk Substructures at High Angular Resolution Project)
- Related: Gaia DR3

## Checks

```json
{
 "quotes": 133,
 "quotes_ok": 133,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 118,
  "stated": 84,
  "rate": 0.712
 },
 "evidence_ok": true
}
```
