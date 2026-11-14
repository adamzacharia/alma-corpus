# Gas inflows from cloud to core scales in G332.83-0.55: Hierarchical hub-filament structures and tide-regulated gravitational collapse

`2024A&A...686A.146Z` | Astronomy and Astrophysics 2024 | first author: Zhou, J. W. | arXiv: 2403.13442 | DOI: 10.1051/0004-6361/202449514

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: star_formation, milky_way_ism
- Question: Whether shear and tides from the protocluster and from all external material regulate (slow down) the gravitational collapse of dense gas structures in the hub-filament region G332.83-0.55, using LAsMA and ALMA data to trace inflows from cloud to core scales  
  > "High-resolution LAsMA and ALMA observations can directly trace the gas inflows from cloud to core scales." (abstract); "We investigated the effects of shear and tides from the protocluster on the surrounding local dense gas structures." (abstract)
- Target **G332.83-0.55**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2019.1.00685.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m array and 7m array (details given in earlier papers)  
  > "The details of the 12m array and 7m array ALMA observations were summarized in (cite: Liu2020; Liuh2021)." (2.2 ALMA data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: continuum synthesized beam FWHM ~2.2 arcsec  
  > "The continuum image reaches a typical 1 $\sigma$ rms noise of $\sim$0.2 mJy in a synthesized beam FWHM size of $\sim2.2\ensuremath{''}$." (2.2 ALMA data)
- max recoverable scale: _not stated_
- sensitivity: continuum 1 sigma rms ~0.2 mJy; H13CO+ J=1-0 cube noise ~0.008 Jy/beam; HCO+ J=1-0 cube noise ~0.012 Jy/beam  
  > "The continuum image reaches a typical 1 $\sigma$ rms noise of $\sim$0.2 mJy in a synthesized beam FWHM size of $\sim2.2\ensuremath{''}$." (2.2 ALMA data); "The final noise levels of the H$^{13}$CO$^+$ J=1-0 and HCO$^+$ J=1-0 data cubes are $\sim$0.008 Jy beam$^{-1}$ and $\sim$0.012 Jy beam$^{-1}$, respectively." (2.2 ALMA data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ATOMS survey source, Project ID 2019.1.00685.S, PI Tie Liu  
  > "We selected one source from the ATOMS survey (Project ID: 2019.1.00685.S; PI: Tie Liu)." (2.2 ALMA data)
- Line: H13CO+ J=1-0 (not stated)
- Line: HCO+ J=1-0 (not stated)
- Other facility **APEX/LAsMA**: 12CO and 13CO J=3-2 cubes of the G333 complex (0.25 km/s, 19.5 arcsec) used for cloud-to-clump scales  
  > "The seven pixel Large APEX sub-Millimeter Array (LAsMA) receiver of the APEX telescope was used to observe the $J=3-2$ transitions of $^{12}$CO and $^{13}$CO in the G333 molecular cloud complex." (2.1 LAsMA data); "The final data cubes have a velocity resolution of 0.25 km s$^{-1}$ and an angular resolution of $19.5 \ensuremath{''}$ and the pixel size is $6 \ensuremath{''}$." (2.1 LAsMA data)
- Other facility **ATLASGAL+Planck 870 um**: 870 um dust emission at ~21 arcsec, sensitive to a wide range of spatial scales  
  > "We also used ATLASGAL+Planck 870 $\mu$m data (ATLASGAL combined with Planck data), which are sensitive to a wide range of spatial scales at a resolution of $\sim21\ensuremath{''}$ (cite: Csengeri2016-585)." (2.3 Archival data)
- External data: Dust temperature T ~31.4 K used in the dust mass estimate  
  > "The temperature $T$ takes the value $\sim$31.4 K listed in Table A1 of (cite: Liu2020)." (3.2 Infall+rotation motions) [from Liu et al. 2020b (cite: Liu2020)]
- External data: H2 column density from ATLASGAL+Planck 870 um used for the tide from the envelope  
  > "Using the H$_{2}$ column density derived from ATLASGAL+Planck 870 $\mu$m in (cite: Zhou2024-682), the matter in the FOV of ALMA observation was first masked" (3.7.3 Tide from the envelope) [from Zhou et al. 2024b (cite: Zhou2024-682)]
- External data: Gaussian decomposition of the 13CO (3-2) PPV cube (GAUSSPY+) carried out in an earlier paper  
  > "the decomposition was carried out in (cite: Zhou2023-676)" (3.1 Connection of gas inflows) [from Zhou et al. 2023 (cite: Zhou2023-676)]
- External data: UC HII region in the hub identified in an earlier paper  
  > "feedback from the central UC-HII region identified in (cite: Zhang2023-520) has destroyed the surrounding molecular gas structure" (3.1 Connection of gas inflows) [from Zhang et al. 2023 (cite: Zhang2023-520)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 5.6  
  > "Calibration and imaging were carried out using the CASA software package version 5.6 (cite: McMullin2007); more details can be found in (cite: Zhou2021-508)." (2.2 ALMA data)
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
- primary beam correction: all images primary-beam corrected  
  > "All images have been primary-beam corrected." (2.2 ALMA data)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: continuum synthesized beam FWHM ~2.2 arcsec  
  > "The continuum image reaches a typical 1 $\sigma$ rms noise of $\sim$0.2 mJy in a synthesized beam FWHM size of $\sim2.2\ensuremath{''}$." (2.2 ALMA data)
- final rms: continuum ~0.2 mJy; H13CO+ ~0.008 Jy/beam; HCO+ ~0.012 Jy/beam  
  > "The final noise levels of the H$^{13}$CO$^+$ J=1-0 and HCO$^+$ J=1-0 data cubes are $\sim$0.008 Jy beam$^{-1}$ and $\sim$0.012 Jy beam$^{-1}$, respectively." (2.2 ALMA data)

### Inherited from earlier work

- ALMA 12m and 7m observation details (setup, configurations)  
  > "The details of the 12m array and 7m array ALMA observations were summarized in (cite: Liu2020; Liuh2021)." (2.2 ALMA data) [from (cite: Liu2020; Liuh2021)]
- ALMA calibration and imaging details  
  > "more details can be found in (cite: Zhou2021-508)" (2.2 ALMA data) [from (cite: Zhou2021-508)]
- LAsMA calibration, imaging and product creation  
  > "A detailed description of data calibration, imaging, and product creation procedures is presented in (cite: Zhou2023-676)." (2.1 LAsMA data) [from (cite: Zhou2023-676)]
- Filament identification method  
  > "Following the method described in (cite: Zhou2022-514) and (cite: Zhou2023-676), we used the integrated intensity (Moment 0) maps to identify filaments." (3.1 Connection of gas inflows) [from (cite: Zhou2022-514); (cite: Zhou2023-676)]
- Dendrogram identification of dense gas structures  
  > "thus we adopted the same method as in (cite: Zhou2024-682) and (cite: Zhou2024-682-173) to identify dense gas structures" (3.3 Local dense gas structures) [from (cite: Zhou2024-682); (cite: Zhou2024-682-173)]
- LTE column density from H13CO+ and HCO+ J=1-0  
  > "using the same method described in Sec.3.3 of (cite: Zhou2024-682-173) by the local thermodynamic equilibrium (LTE) analysis" (3.3 Local dense gas structures) [from Sec. 3.3 of (cite: Zhou2024-682-173)]
- Gravitational potential energy and internal kinetic energy of structures  
  > "The gravitational potential energy $E_{\rm g}$ and internal kinetic energy $E_{\rm k}$ were calculated in the same way as presented in (cite: Zhou2024-682)." (5.1 Tide-regulated gravitational collapse) [from (cite: Zhou2024-682)]
- Protocluster mass from the centrifugal barrier radius  
  > "According to equations (1) and (2) in (cite: Sakai2014-507), we can estimate the mass of the gravitational center according to $r_{\rm c}$ by" (3.2 Infall+rotation motions) [from (cite: Sakai2014-507)]

### Not stated but needed to reproduce (our reading)

- ALMA band, spectral setup, rest frequencies and spectral resolution of the HCO+ and H13CO+ cubes
- Array configurations, baselines and 12m+7m combination recipe, and tclean/weighting parameters (robust, taper, cell, image size, masks, deconvolver)
- Line-free channels and continuum subtraction used for the cubes and the 3 mm continuum
- Distance to G332.83-0.55 used for masses, sizes and the dust mass formula
- Total 3 mm continuum flux used for the 3% dust fraction
- FILFINDER parameters used to extract skeletons
- Dendrogram parameters (min_value, min_delta, min_npix) and number of leaf structures kept
- Gaussian fitting of the average spectra for velocity dispersion, including how blended components were handled
- LTE assumptions for the column density (excitation temperature, abundance ratios) are only given by reference to Zhou et al. 2024a
- How V_rotation and r_c were read from the velocity jump along the filaments
- Regression method and uncertainty estimation for the sigma-N*R slopes
- Pixel scale, smoothing and mass-to-surface-density conversion used for the 2D potential and tidal tensor

## Analysis recipe

1. **calibrate and image ALMA data**: Calibration and imaging with CASA 5.6, details deferred to an earlier paper  
  > "Calibration and imaging were carried out using the CASA software package version 5.6 (cite: McMullin2007); more details can be found in (cite: Zhou2021-508)." (2.2 ALMA data)
   - software: CASA
   - parameter: All images primary-beam corrected  
  > "All images have been primary-beam corrected." (2.2 ALMA data)
   - fitting: _not stated_
   - validation: _not stated_
2. **identify filaments and velocity structure**: FILFINDER on Moment 0 maps of H13CO+ (1-0) and 13CO (3-2); extract velocity and intensity along filaments and PV diagrams  
  > "The FILFINDER algorithm (cite: Koch2015) was used to identify and characterize filaments traced by H$^{13}$CO$^{+}$ (1-0) and $^{13}$CO (3$-$2) emission." (3.1 Connection of gas inflows)
   - software: FILFINDER
   - parameter: Filaments selected through the redshifted and blueshifted peaks (LAsMA-f3 and ALMA-f3)  
  > "We selected the filaments through the redshifted and blueshifted peaks (LAsMA-f3 and ALMA-f3), and extracted the velocity and intensity along the filaments" (3.1 Connection of gas inflows)
   - fitting: _not stated_
   - validation: Skeletons compared by eye with the gas structures  
  > "are highly consistent with the gas structures" (3.1 Connection of gas inflows)
3. **estimate protocluster mass from velocity jump**: Use the shift of blueshifted and redshifted peaks to get the centrifugal barrier radius and rotation velocity, then M = V_rotation^2 r_c / (2G)  
  > "the shift of blueshifted and redshifted peaks can be used to estimate the radius of the centrifugal barrier $r_{\rm c}$, where the rotation velocity $V_{\rm rotation}$ has its maximum value." (3.2 Infall+rotation motions)
   - parameter: V_rotation,ALMA ~3.29 km/s and r_c,ALMA ~0.21 pc  
  > "$V_{\rm rotation,ALMA} \approx$3.29 km/s and $r_{\rm c, ALMA} \approx$ 0.21 pc." (3.2 Infall+rotation motions)
   - assumption: Infalling and rotating envelope model as in Sakai et al. 2014  
  > "In the schematic diagram of an infalling and rotating envelope model for IRAS 04368+2557 (cite: Sakai2014-507)" (3.2 Infall+rotation motions)
   - fitting: _not stated_
   - validation: Compared with the mass from 3 mm dust emission  
  > "which agrees with the mass estimated by 3mm dust emission" (6 Summary)
4. **cross-check protocluster mass with dust emission**: Dust mass formula of Kauffmann et al. 2008, inverted to find the 3 mm dust flux that gives 264 Msun  
  > "following the method described in (cite: Kauffmann2008), the mass can be computed by dust emission using" (3.2 Infall+rotation motions)
   - parameter: beta = 1.5; T ~31.4 K from Liu et al. 2020  
  > "Here, we consider $\beta=1.5$," (3.2 Infall+rotation motions); "The temperature $T$ takes the value $\sim$31.4 K listed in Table A1 of (cite: Liu2020)." (3.2 Infall+rotation motions)
   - assumption: 3 mm continuum of UC HII regions is mostly free-free, so a ~3% dust fraction is reasonable  
  > "This value is $\sim$3% of the total flux of 3mm continuum emission in ALMA observations." (3.2 Infall+rotation motions)
   - fitting: _not stated_
   - validation: Dust flux of ~0.12 Jy is ~3% of the total 3 mm continuum flux, judged reasonable  
  > "A mass $\sim$264M$_{\odot}$ corresponds to the flux of 3mm dust emission $\sim$0.12 Jy." (3.2 Infall+rotation motions)
5. **identify dense leaf structures and derive their properties**: Dendrogram on the H13CO+ (1-0) Moment 0 map, average spectrum per structure, LTE column density from H13CO+ and HCO+, then masses and virial ratios  
  > "We directly identified hierarchical (sub)structures based on the 2D integrated intensity (Moment 0) map of H$^{13}$CO$^{+}$ (1$-$0) emission, and then extracted the average spectrum of each structure" (3.3 Local dense gas structures); "Then the masses and virial ratios of all leaf structures were calculated." (3.3 Local dense gas structures)
   - software: astrodendro
   - parameter: Only leaf structures, types 1 (single component) and 3 (blended component); structures with absorption removed  
  > "we only consider type1 (single velocity component) and type3 (blended velocity component) structures" (3.3 Local dense gas structures); "In this work, we focus on leaf structures, which are local gravitational centers." (3.3 Local dense gas structures)
   - assumption: Local thermodynamic equilibrium for column density  
  > "using the same method described in Sec.3.3 of (cite: Zhou2024-682-173) by the local thermodynamic equilibrium (LTE) analysis" (3.3 Local dense gas structures)
   - fitting: Average spectra fitted for velocity dispersion; fit function not stated  
  > "and then extracted the average spectra to fit the velocity dispersion" (6 Summary)
   - validation: _not stated_
6. **test shear and tide from the protocluster**: Shear parameter S_g = Sigma_cri/Sigma with Sigma_cri from Dib et al. 2012; Kepler rotation curve gives tide T = 3GM0/R'^3 and sigma_t^2 ~ T*R^2  
  > "Following equation.7 of (cite: Dib2012-758)," (3.4 Shear and tide from the protocluster); "Inserting the Keplerian rotation curve, $T = 3GM_{0}/R'^{3}$, which is similar to equation.[\[point\]](#point)." (3.4 Shear and tide from the protocluster)
   - parameter: Density contrast C = 100  
  > "The ratio between the average surface density derived from $^{13}$CO (3$-$2) emission in the FOV of the ALMA observation and the highest surface density of leaf structures is $\sim 100$, and thus we consider $C$=100." (3.4 Shear and tide from the protocluster)
   - assumption: Velocity of surrounding structures from a Kepler rotation curve around the protocluster mass M0  
  > "In our case, for gas structures in the clump around the protocluster, $V$ was estimated by the Kepler rotation curve, as discussed in Sec.[3.2](#infall)." (3.4 Shear and tide from the protocluster)
   - fitting: _not stated_
   - validation: S_g << 1 and sigma_t^2/sigma^2 << 1 except for two structures, so protocluster shear and tide are unimportant  
  > "except for two structures adjacent to the protocluster, the results seem to deny the importance of the shear and tide from the protocluster." (3.4 Shear and tide from the protocluster)
7. **derive tidal field from the surface density map**: Compute 2D gravitational potential from the surface density map, form the 2D tidal tensor, split into internal and external parts, and take the mean external strength per structure (T_d,1, T_d,2, T_d,3)  
  > "Calculating the gravitational potential field $\phi(x, y)$ based on the surface density map $\Sigma(x, y)$ has been discussed in (cite: Gong2011-729; He2023-526)." (3.5 Tidal field); "For three limiting cases, the external tides can be measured by $\lambda_{1}$, $\lambda_{2}$, and $(\lambda_{2}-\lambda_{1})/2$ and they are called T$_{\rm d,1}$, T$_{\rm d,2}$, and T$_{\rm d,3}$, respectively." (3.5 Tidal field)
   - assumption: 2D projected tide used because only projected surface density is observed; G332.83-0.55 assumed sheet-like so 2D is comparable to 3D  
  > "To align with other projected physical quantities derived from the observations, we also calculated the 2D projected tide." (3.5 Tidal field); "Therefore, 2D-projected tidal field strength should be comparable to those for 3D ones" (3.6 Structure of G332.83-0.55)
   - fitting: _not stated_
   - validation: 2D and 3D estimates confirmed comparable in Fig. 8(a)  
  > "should still be effective for a 2D situation, which is confirmed in Fig.[8](#compare)(a)." (3.6 Structure of G332.83-0.55)
8. **cross-check tides with pixel-by-pixel computation**: Mask each dendrogram structure, compute tide at each pixel from all other material with T ~ 2GM/R^3, average over the structure; maximum (T_max), scalar minimal (T_min,s) and vector minimal (T_min,v) variants, plus T_out from material outside the ALMA FOV  
  > "a simple calculation involves using equation.[\[point\]](#point) to directly calculate the tidal strength at that point pixel by pixel" (3.7.1 Maximum computation)
   - parameter: Minimal case: external material moved vertically 0.03 pc (mean leaf effective radius)  
  > "Using the average effective radius ($\sim$0.03 pc) of all leaf structures as the characteristic scale height of G332.83-0.55, all external material apart from the calculated structure was moved vertically to 0.03 pc away" (3.7.2 Minimal computation)
   - parameter: T_min,s adopted as the external tide in later analysis  
  > "As a compromise, we use the value of T$_{\rm min,s}$ to represent the external tides in the subsequent analysis." (3.7.4 Comparison)
   - assumption: Scalar superposition of tides to measure overall tidal strength  
  > "Therefore, we used the scalar superposition to measure the overall tidal strength in the structure from the external gravity." (3.7.1 Maximum computation)
   - fitting: _not stated_
   - validation: T_d,1, T_d,2, T_d,3, T_min,s and T_min,v are comparable; T_max is significantly larger as expected; T_out is negligible  
  > "Especially, they are also comparable with T$_{\rm min,s}$ and T$_{\rm min,v}$. As expected, T$_{\rm max}$ is significantly larger than others." (3.7.4 Comparison)
9. **refit scaling relation with tides and test energy balance with external pressure**: Add tidal velocity dispersion to observed dispersion, refit sigma_s-N*R; compare E_k+E_t with E_g+E_p using cloud pressure P_cl = pi G Sigma_bar Sigma_r  
  > "After adding the contribution of the tidal interactions to the observed velocity dispersion, the effective velocity dispersion $\sigma_{\rm s}=\sqrt{\sigma_{\rm t}^{2}+\sigma^{2}}$, then the $\sigma_{\rm s}-N*R$ relation was fitted again." (4.1 Tide-regulated gravitational collapse)
   - parameter: E_t ~ 0.5 M T_min,s R^2; E_p = -4 pi P_cl R^3  
  > "The effective velocity dispersion from the external tides of the structure is $\sigma_{t}^{2} \approx T_{\rm min,s}*R^2$" (4.1 Tide-regulated gravitational collapse)
   - assumption: External pressure considered only from the ambient cloud  
  > "here we mainly consider the external pressure from the ambient cloud for each decomposed structure using" (4.1 Tide-regulated gravitational collapse)
   - fitting: _not stated_
   - validation: E_k+E_t exceeds E_g alone but is below E_g+E_p once external pressure is included  
  > "after considering the external pressure, $E_{\rm k}+E_{\rm t}<E_{\rm g}+E_{\rm p}$." (4.1 Tide-regulated gravitational collapse)

## Software

- **CASA** 5.6: ALMA calibration and imaging  
  > "Calibration and imaging were carried out using the CASA software package version 5.6 (cite: McMullin2007)" (2.2 ALMA data)
- **FILFINDER** : Identify and characterize filaments in H13CO+ (1-0) and 13CO (3-2) Moment 0 maps  
  > "The FILFINDER algorithm (cite: Koch2015) was used to identify and characterize filaments traced by H$^{13}$CO$^{+}$ (1-0) and $^{13}$CO (3$-$2) emission." (3.1 Connection of gas inflows)
- **GAUSSPY+** : Gaussian decomposition of the 13CO (3-2) PPV cube, done in an earlier paper  
  > "decomposed by the fully automated Gaussian decomposer `GAUSSPY+` (cite: Lindner2015-149; Riener2019-628); the decomposition was carried out in (cite: Zhou2023-676)" (3.1 Connection of gas inflows)
- **astrodendro** : Dendrogram of astronomical data to identify hierarchical structures  
  > "This research made use of astrodendro, a Python package to compute dendrograms of Astronomical data (http://www.dendrograms.org/)." (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Slope of the sigma-N*R relation for all structures, before and after adding tides | 0.20 -> 0.52 | +/-0.04 and +/-0.03 | dimensionless | 9 | the slope of the $\sigma-N*R$ relation changes from 0.20$\pm$0.04 to 0.52$\pm$0.03 |
| Rotation velocity and centrifugal barrier radius (ALMA) | V_rotation,ALMA ~3.29 km/s; r_c,ALMA ~0.21 pc | not stated | km/s; pc | 3 | $V_{\rm rotation,ALMA} \approx$3.29 km/s and $r_{\rm c, ALMA} \approx$ 0.21 pc. |
| Mass of the gravitational center (protocluster) | ~264 | not stated | Msun | 3 | the mass of the gravitational center (i.e., the protocluster) is $\sim$264 M$_{\odot}$. |
| 3 mm dust flux corresponding to 264 Msun | ~0.12 | not stated | Jy | 4 | A mass $\sim$264M$_{\odot}$ corresponds to the flux of 3mm dust emission $\sim$0.12 Jy. |
| Dust share of the total 3 mm continuum flux | ~3 | not stated | percent | 4 | This value is $\sim$3% of the total flux of 3mm continuum emission in ALMA observations. |
| Averaged external tidal strength from material outside the ALMA FOV (T_out) | ~1.4e-25 | not stated | s^-2 | 8 | The averaged tidal strength of all pixels is $\sim$1.4 $\times 10^{-25}$ s$^{-2}$. |
| Mean effective radius of leaf structures | ~0.03 | not stated | pc | 5 | Using the average effective radius ($\sim$0.03 pc) of all leaf structures |
| LAsMA cube noise, 12CO (3-2) and 13CO (3-2) | ~0.32 and ~0.46 | not stated | K | 0 | The final noise levels of the $^{12}$CO (3–2) and $^{13}$CO (3–2) data cubes are $\sim$0.32 K and $\sim$0.46 K, respectively. |

## Qualitative findings

- G332.83-0.55 shows at least two levels of hub-filament structures (cloud-to-clump and clump-to-core)  
  > "To conclude, G332.83-0.55 shows at least two levels of hub-filament structures." (3.1 Connection of gas inflows)
- Gas inflows converge on the hub, described as gravitational focusing, which may form the hub-filament structure  
  > "Similar to lights converging to the focus, now the gas inflows are converging to the gravitational center, that is, the hub region of G332.83-0.55." (5.2 Gravitational focusing)
- The ALMA view shows anisotropic filamentary accretion in what single-dish data show as a spherical clump  
  > "However, in the eyes of ALMA, the spherical clump displays anisotropic and filamentary accretion structures (hub-filament)" (3.1 Connection of gas inflows)

## Claim tuples

- H: Does G332.83-0.55 show hub-filament structure at more than one scale? | E: Moment maps, FILFINDER skeletons and PV diagrams of LAsMA 13CO (3-2) and ALMA H13CO+ (1-0) | R: Hub-filament morphology and velocity jumps are seen at cloud-to-clump and clump-to-core scales, with connected velocity fields | F: At least two levels of hub-filament structure; inflows extend from cloud to core scales | **supported**
- H: Is the protocluster collapsing with rotation, and what is its mass? | E: Read the blueshifted/redshifted peak separation and velocity difference from the PV/velocity profiles, apply the centrifugal barrier mass formula, check with 3 mm dust mass | R: V_rotation ~3.29 km/s, r_c ~0.21 pc, M ~264 Msun, dust flux ~3% of total 3 mm continuum | F: The region is collapsing with rotation and the mass agrees with the dust estimate | **supported**
- H: Do shear and tides from the protocluster alone slow the collapse of surrounding structures? | E: Compute S_g and sigma_t^2/sigma^2 for leaf structures using a Kepler rotation curve around the protocluster | R: S_g << 1 and sigma_t^2/sigma^2 << 1 except for two structures adjacent to the protocluster | F: Protocluster shear and tide appear unimportant | **supported**
- H: Do total external tides from all gas plus external pressure explain the shallow sigma-N*R slope? | E: Derive the tidal field from the surface density map, compare with pixel-by-pixel estimates, add sigma_t to sigma and refit the relation, compare energy terms with and without external pressure | R: Slope changes from 0.20+/-0.04 to 0.52+/-0.03; E_k+E_t < E_g+E_p once pressure is included | F: External tides slow free-fall collapse, balanced by external pressure (tide-regulated gravitational collapse) | **supported**

## Reasoning

- Why this data: Combining single-dish LAsMA and interferometric ALMA data traces inflows across scales  
  > "High-resolution LAsMA and ALMA observations can directly trace the gas inflows from cloud to core scales." (abstract)
- Why this method: Protocluster-only shear and tide are incomplete, so a full tidal field from the density distribution is derived  
  > "To fully consider the tidal interactions, we directly derived the tidal field according to the density distribution." (3.5 Tidal field)
- Alternative: T_max (2D pixel-by-pixel) judged too large and T_min,v slightly larger than others; T_min,s adopted as a compromise  
  > "As expected, T$_{\rm max}$ is significantly larger than others." (3.7.4 Comparison); "As a compromise, we use the value of T$_{\rm min,s}$ to represent the external tides in the subsequent analysis." (3.7.4 Comparison)
- How they decided it was enough: _not stated_
- Limitation (authors): External tidal strength may be overestimated and E_k likely overestimated  
  > "The external tidal strength may be overestimated." (4.1 Tide-regulated gravitational collapse); "Thus, E$_{\rm k}$ should be overestimated." (4.1 Tide-regulated gravitational collapse)
- Limitation (authors): Only projected 2D surface density is observed; the 3D structure is unknown  
  > "Only the projected surface density map is available in the observations." (3.5 Tidal field); "The 3D structure of the molecular gas is unknown" (3.7.2 Minimal computation)
- Caveat (inferred, ours): The 3 mm 'agreement' of mass relies on assuming only ~3% of the continuum is dust, which is chosen to fit rather than measured independently
- Caveat (inferred, ours): V_rotation and r_c are read by eye ('roughly estimate') with no uncertainties, so the 264 Msun mass has no error bar
- Caveat (inferred, ours): The sigma-N*R slope change from 0.20 to 0.52 depends on the adopted tidal strength (T_min,s), a limiting-case estimate that the authors say may be overestimated
- Caveat (inferred, ours): Distance, LTE excitation temperature and abundance ratios are not given in the paper, so masses and column densities cannot be checked
- Caveat (inferred, ours): Only one ALMA field and one source is analysed; generality of tide-regulated collapse is inferred from earlier papers

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA band and spectral setup, imaging parameters and line-free channels
- Missing: Distance and LTE inputs for column density and mass
- Missing: Dendrogram and FILFINDER parameters and the list of leaf structures
- Missing: Tidal tensor implementation details (map resolution, mass conversion, boundaries) and the fitting procedure for the slopes
- Missing: Several steps depend on Zhou et al. 2024a, 2024b and 2023 and are not self-contained
- Data volume (inferred): Tens of GB (one ATOMS band 3 field, 12m + 7m raw data); the ATLASGAL+Planck and LAsMA cubes add a few GB at most
- Score (inferred): 2/5, The ALMA project code is given but imaging, LTE and dendrogram settings are deferred to other papers or omitted; main slopes and the 264 Msun mass are numeric but depend on unstated choices.
- Rediscovery candidate: no, Recipe is not complete without the companion papers and the distance, and the tidal analysis needs details that are not published here.

## Links

- Method: Zhou et al. 2021 (cite: Zhou2021-508) (ALMA calibration and imaging details)
- Method: Zhou et al. 2024a (cite: Zhou2024-682-173) (Dendrogram identification of structures and LTE column density method)
- Method: Zhou et al. 2023 (cite: Zhou2023-676) (LAsMA data processing and GAUSSPY+ decomposition)
- Method: Ganguly et al. 2024 (cite: Ganguly2024) (Tidal tensor decomposition into internal and external parts)
- Companion: Zhou et al. 2022 (cite: Zhou2022-514) (Hub-filament systems in ATOMS and filament identification method)
- Companion: Zhou et al. 2024b (cite: Zhou2024-682) (Dendrogram structures, scaling relations and energies in the G333 complex)
- Companion: Liu et al. 2020b (cite: Liu2020) (ATOMS survey description and clump temperatures)
- Related: ATOMS (ALMA Three-millimeter Observations of Massive Star-forming regions)
- Related: ATLASGAL
- Related: APEX programme M-0109.F-9514A-2022 (G333 complex, LAsMA)

## Checks

```json
{
 "quotes": 97,
 "quotes_ok": 97,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 110,
  "stated": 68,
  "rate": 0.618
 },
 "evidence_ok": true
}
```
