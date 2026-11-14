# Impacts of Bar-driven Shear and Shocks on Star Formation

`2024ApJ...968...87K` | The Astrophysical Journal 2024 | first author: Kim, Taehyun | arXiv: 2405.00107 | DOI: 10.3847/1538-4357/ad410e

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, star_formation
- Question: Whether star formation is promoted or suppressed along barred-galaxy dust lanes where bar-driven shear and shocks are strong, and whether emission-line ratios change there  
  > "In this study, we aim to examine whether SF is promoted or suppressed along the bar where strong shear and shocks are expected." (1 Introduction); "Another aim of this paper is to examine whether the emission-line ratios are modified due to the bar-driven shocks and shear." (1 Introduction)
- Target **NGC 1365**: coordinates _not stated_; z/distance 19.57 Mpc  
  > "(4): Distance ((cite: anand_21))." (Table 1 notes); distance from (cite: anand_21)  
  > "(4): Distance ((cite: anand_21))." (Table 1 notes)
- Target **NGC 1512**: coordinates _not stated_; z/distance 18.83 Mpc  
  > "(4): Distance ((cite: anand_21))." (Table 1 notes); distance from (cite: anand_21)  
  > "(4): Distance ((cite: anand_21))." (Table 1 notes)
- Target **NGC 1672**: coordinates _not stated_; z/distance 19.40 Mpc  
  > "(4): Distance ((cite: anand_21))." (Table 1 notes); distance from (cite: anand_21)  
  > "(4): Distance ((cite: anand_21))." (Table 1 notes)
- Target **NGC 3627**: coordinates _not stated_; z/distance 11.32 Mpc  
  > "(4): Distance ((cite: anand_21))." (Table 1 notes); distance from (cite: anand_21)  
  > "(4): Distance ((cite: anand_21))." (Table 1 notes)

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PHANGS-ALMA survey data products (CO (2-1) flux and velocity maps), cite: leroy_21b  
  > "emission-line flux and velocity maps are drawn from the PHANGS-ALMA survey" (2 Data)
- Line: CO J=2-1 (not stated)
- Line: H alpha (PHANGS-MUSE, optical) not stated (not stated)
- Other facility **PHANGS-MUSE (VLT/MUSE)**: Mosaicked datacubes, Halpha and stellar kinematics and emission-line fluxes (copt) used for the velocity gradients, SFR and BPT maps  
  > "We make use of data products from the PHANGS-MUSE survey" (2 Data); "We use the mosaicked datacubes and emission-line fluxes, gas and stellar kinematics" (2 Data)
- External data: PHANGS-ALMA CO (2-1) flux and velocity maps  
  > "emission-line flux and velocity maps are drawn from the PHANGS-ALMA survey" (2 Data) [from (cite: leroy_21b)]
- External data: Galaxy inclination, systemic velocity, disk position angle and centre (fixed in the 3D-BAROLO rotation model)  
  > "The position angle, inclination of the galaxies, and center are fixed to the values from Table 2 of (cite: lang_20) in running 3D–BAROLO." (2 Data); "(9): Inclination ((cite: lang_20))." (Table 1 notes) [from (cite: lang_20)]
- External data: Galaxy distances  
  > "(4): Distance ((cite: anand_21))." (Table 1 notes) [from (cite: anand_21)]
- External data: Stellar mass and star formation rate in Table 1  
  > "(3): Stellar mass ((cite: leroy_21b)). (4): Distance ((cite: anand_21)). (5): Star formation rate ((cite: leroy_21b))." (Table 1 notes) [from (cite: leroy_21b)]
- External data: Bar position angle from 3.6 micron images  
  > "(8): Position angle of bar measured using 3.6 $\mu$m images ((cite: salo_15))." (Table 1 notes) [from (cite: salo_15)]
- External data: Environmental masks defining bar, bar ends and nuclear regions  
  > "We use the environmental masks from (cite: querejeta_21) to define the bar, bar ends, and nuclear regions." (5 Impact of shear and shock on star formation) [from (cite: querejeta_21)]
- External data: Intrinsic Halpha/Hbeta = 2.86 (Case B, T = 10^4 K, n_e = 10^2 cm^-3)  
  > "We assume the value of the intrinsic H$\alpha$/H$\beta$ to be 2.86, corresponding to a temperature $T =10^4$ K and an electron density $n_{e} = 10^2 \rm cm^{-3}$ for Case B recombination" (5 Impact of shear and shock on star formation) [from (cite: baker_38)]
- External data: Standard Milky Way CO-to-H2 conversion factor alpha_CO(1-0) = 4.35  
  > "We use $\alpha^{1-0}_{\rm CO}$ of the standard Milky Way (4.35" (5 Impact of shear and shock on star formation) [from (cite: bolatto_13a)]
- External data: CO(2-1)-to-CO(1-0) line ratio, R21^-1 = 0.65  
  > "we use $R^{-1}_{21}=0.65$ ((cite: leroy_13b; denbrok_21))" (5 Impact of shear and shock on star formation) [from (cite: leroy_13b; denbrok_21)]
- External data: BPT demarcation lines: maximum starburst line, pure star-forming line, Seyfert/LINER division  
  > "A theoretical maximum starburst line ((cite: kewley_01), solid line in Figure [9](#fig:bpt_diagram_1365)) is defined by the upper limit of the theoretical pure stellar photo-ionization model." (6.1 BPT map); "The dashed line ((cite: cidfernandes_11)) divides Seyfert and low-ionization narrow emission-line regions (LINER)." (6.1 BPT map) [from (cite: kewley_01); (cite: kauffmann_03c); (cite: cidfernandes_11)]
- External data: Halpha SFR calibration  
  > "We estimate the SFR using the following relation ((cite: calzetti_07; kennicutt_12))" (5 Impact of shear and shock on star formation) [from (cite: calzetti_07; kennicutt_12)]

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
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- PHANGS-MUSE data processing and Halpha / stellar kinematics fitting (pPXF) details  
  > "Detailed descriptions can be found in (cite: emsellem_22)." (2 Data) [from (cite: emsellem_22)]
- Environmental masks for bar, bar ends and nuclear regions  
  > "We use the environmental masks from (cite: querejeta_21) to define the bar, bar ends, and nuclear regions." (5 Impact of shear and shock on star formation) [from (cite: querejeta_21)]
- 3D-BAROLO orientation parameters (PA, inclination, centre) taken from earlier work  
  > "The position angle, inclination of the galaxies, and center are fixed to the values from Table 2 of (cite: lang_20) in running 3D–BAROLO." (2 Data) [from (cite: lang_20)]
- Velocity gradient from CO computed with the same steps as for Halpha  
  > "following the same steps presented in Section [3.1](#sec:deriving_vg)" (9 Comparing velocity gradients from Halpha and CO) [from Section 3.1 of this paper]

### Not stated but needed to reproduce (our reading)

- Which PHANGS-ALMA data release and which CO (2-1) product (resolution, moment-map type, masking) were used, and the ALMA project codes
- How CO velocity maps were regridded and matched to the MUSE pixel grid and PSF for the V_CO - V_star gradients and CO contours
- Positions, lengths and widths of the pseudo slits and how velocities were averaged across a slit
- Number and spacing of 3D-BAROLO rings and other BAROLO settings beyond fixed PA, inclination, centre, dispersion and scale height
- How the bar radius and interbar (IB) region were defined for each galaxy
- Whether the 'upper 5th percentile' for H regions is computed on pixels or spaxels and after which masks
- Extinction-law details beyond the Balmer decrement and which Halpha luminosity per spaxel enters the SFR
- Exact BPT line equations and the 'lighter/darker shade' thresholds used in classification
- Whether the inclination is applied to the velocity gradients (stated as not corrected) and exact deprojection used for velocity jumps

## Analysis recipe

1. **Obtain Halpha and stellar kinematics from PHANGS-MUSE**: Use PHANGS-MUSE copt mosaics; Halpha flux and kinematics from pPXF with Halpha fitted as an additional Gaussian while the stellar continuum is fitted simultaneously  
  > "H$\alpha$ flux and kinematics of the PHANGS-MUSE are obtained using pPXF ((cite: Cappellari_04))." (2 Data); "The H$\alpha$ emission-line is fitted treating as an additional Gaussian function, while the stellar continuum is fitted simultaneously." (2 Data)
   - software: pPXF
   - parameter: seeing of the copt data 0.96 to 1.25 arcsec  
  > "the seeing of the “copt” data of our sample spans from 0.96” to 1.25”" (2 Data)
   - parameter: spectral resolution ~50 km/s at Halpha  
  > "The spectral resolution is $\sim$50 km$\,\rm s^{-1}$ at H$\alpha$." (2 Data)
   - assumption: Halpha and Hbeta velocity and velocity dispersion tied together  
  > "The velocity and velocity dispersion for H$\alpha$ and H$\beta$ are tied together." (2 Data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Model galaxy rotation of the Halpha velocity field**: 3D tilted-ring fit to the Halpha datacube with 3D-BAROLO; PA, inclination and centre fixed to literature values  
  > "In order to model the galaxy rotation, we utilize ((cite: diteodoro_15)) which is a tool for fitting 3D tilted-ring models to emission-line datacubes." (2 Data); "The position angle, inclination of the galaxies, and center are fixed to the values from Table 2 of (cite: lang_20) in running 3D–BAROLO." (2 Data)
   - software: 3D-BAROLO
   - parameter: velocity dispersion fixed to 8 km/s, scale height fixed to 0 arcsec  
  > "Velocity dispersion and scale height of the disk are fixed to 8 km$\,\rm s^{-1}$ and 0 arcsec, respectively" (2 Data)
   - parameter: PA and inclination either fixed or free ring by ring; both results presented in the velocity-jump analysis  
  > "In fitting galaxy kinematics using 3D–BAROLO, position angles and inclinations can be fixed or freely modeled ring by ring." (4 Velocity Jumps)
   - fitting: _not stated_
   - validation: Rotation model is not used for the final gradient maps because non-smooth models give bumpy gradient maps; stellar velocity used instead  
  > "However, when galaxy rotation models are not smooth, the resulting velocity gradient maps becomes bumpy and thus unsuitable for investigating the velocity gradients." (3.1 Deriving gas velocity gradient maps)
3. **Derive Halpha velocity gradient maps**: Take the Halpha-minus-stellar (or Halpha-minus-rotation-model) velocity map, rotate it to align the bar horizontally, take 1-pixel differences left/right and up/down and add the horizontal and vertical gradients in quadrature  
  > "We rotate the velocity residual map to align the bar horizontally using the position angle of the bar presented in Table 1" (3.1 Deriving gas velocity gradient maps); "We move along the velocity residual map by 1 pixel (0.2”, 11 $\sim$ 19 pc depending on object) to the left ($V_{\rm res,-1pix}$) and to the right ($V_{\rm res,+1pix}$)" (3.1 Deriving gas velocity gradient maps); "We add in quadrature both the horizontal ($\nabla V_{x}$) and vertical ($\nabla V_{y}$) velocity gradients to obtain the full velocity gradient." (3.1 Deriving gas velocity gradient maps)
   - parameter: Halpha amplitude-over-noise > 3  
  > "we applied amplitude-over-noise ratio of H$\alpha$ greater than 3" (3.3 Velocity gradients due to bar-driven gas inflow)
   - parameter: Error mask constant C = 0.2 for NGC 1365 and NGC 3627; C = -0.05 for NGC 1512 and NGC 1672  
  > "Constant C is set to 0.2 for NGC 1365 and NGC 3627, while C is empirically set to $-0.05$ for NGC 1512 and NGC 1672" (3.3 Velocity gradients due to bar-driven gas inflow)
   - parameter: Pixels with stellar velocity error above the per-galaxy median removed (bin-edge artefacts)  
  > "We empirically find that those pixels can be removed if we remove pixels that have the stellar velocity errors greater than the median of stellar velocity errors of each galaxy." (3.3 Velocity gradients due to bar-driven gas inflow)
   - parameter: NGC 1365 rotated with the PA of the bar dust lane (65 deg) instead of the stellar bar PA  
  > "we rotate NGC 1365 with the PA of the bar dust lane when we obtain the velocity gradient map" (Table 1 notes)
   - assumption: Gradient not corrected for galaxy inclination  
  > "it is not corrected for galaxy inclination" (3.1 Deriving gas velocity gradient maps)
   - assumption: Stellar velocity field traces circular rotation because the sample is dynamically cold  
  > "as our sample of barred galaxies are relatively dynamically cold, Figure [3](#fig:NGC1365_vg_comparison) shows that we can use stellar velocity field to trace the galaxy rotation in order to obtain non-circular motions." (3.1 Deriving gas velocity gradient maps)
   - fitting: _not stated_
   - validation: Gradient maps from the rotation-model and stellar-velocity methods compared for NGC 1365; patterns almost the same  
  > "we find that the patterns are almost the same while the one from subtracting the galaxy rotation model is more patchy" (3.1 Deriving gas velocity gradient maps)
4. **Compare velocity gradients with PHANGS-ALMA CO**: Overlay CO (2-1) contours on the velocity gradient maps and compare Halpha gradients with CO gradients derived from the V_CO minus V_star map  
  > "We plot CO emission-line contours on top of velocity gradient map in Figure" (3.4 Comparison to the CO Map); "CO velocity gradients are correlated with H$\rm \alpha$ velocity gradients." (9 Comparing velocity gradients from Halpha and CO)
   - parameter: CO velocity gradient could not be obtained for NGC 1512 because CO is only marginally detected along the bar  
  > "CO in the bar of NGC 1512 is marginally detected along the bar, therefore we could not obtain CO velocity gradients for this object." (9 Comparing velocity gradients from Halpha and CO)
   - fitting: _not stated_
   - validation: Halpha gradients used as proxy for molecular gas gradients because the two are correlated, with spread at low gradients  
  > "This suggests that we can use H$\rm \alpha$ velocity gradients to trace molecular gas velocity gradients for these galaxies." (9 Comparing velocity gradients from Halpha and CO)
5. **Measure velocity jumps across high-gradient regions**: Pseudo slits placed perpendicular to the high velocity gradient regions in the bar; velocity changes read from Halpha, CO and stellar velocity maps, also after subtracting the rotation model  
  > "we place pseudo slits perpendicular to the regions of high velocity gradient in the bar region." (4 Velocity Jumps); "to exclude the effects of circular motions from galaxy rotation, we subtract the galaxy rotation model from H$\alpha$ velocity map." (4 Velocity Jumps)
   - software: 3D-BAROLO
   - assumption: Inclination correction scales jumps up (x1.2 for NGC 1365)  
  > "Thus, the velocity jump would become even higher (${\times}$1.2 for NGC 1365) if we correct for inclination." (4 Velocity Jumps)
   - fitting: _not stated_
   - validation: Jumps measured directly from the velocity map; results compared with earlier observations and simulations  
  > "We note that these velocity jumps are measured directly from the velocity map, and therefore are not model-dependent." (4 Velocity Jumps)
6. **Compute SFR surface density and molecular gas surface density per spaxel and compare with velocity gradients**: Extinction-correct Halpha using the Balmer decrement, convert Halpha luminosity to SFR, derive Sigma_mol from CO (2-1); plot SFR surface density versus velocity gradient for bar spaxels excluding nuclear regions and bar ends  
  > "To correct for extinction, we use the flux ratio of two emission-lines, H$\alpha$/H$\beta$ (Balmer decrement)" (5 Impact of shear and shock on star formation); "we select the bar regions outside the nuclear region and inside the bar ends" (5 Impact of shear and shock on star formation)
   - parameter: alpha_CO(1-0) = 4.35 (standard Milky Way); R21^-1 = 0.65  
  > "We use $\alpha^{1-0}_{\rm CO}$ of the standard Milky Way (4.35" (5 Impact of shear and shock on star formation); "we use $R^{-1}_{21}=0.65$" (5 Impact of shear and shock on star formation)
   - assumption: Intrinsic Halpha/Hbeta = 2.86, Case B, T = 10^4 K, n_e = 10^2 cm^-3  
  > "We assume the value of the intrinsic H$\alpha$/H$\beta$ to be 2.86" (5 Impact of shear and shock on star formation)
   - assumption: SFR from Halpha luminosity alone, chosen to conserve the resolution of the velocity gradients  
  > "to conserve the resolution of the H$\alpha$ velocity gradients, we use the SFR derived from H$\alpha$ luminosity in this study." (5 Impact of shear and shock on star formation)
   - fitting: _not stated_
   - validation: Qualitative: upper envelope of SFR surface density decreases with velocity gradient; no formal statistic  
  > "But as the velocity gradient increases, the upper envelope of SFR surface density decreases." (5 Impact of shear and shock on star formation)
7. **Classify ionisation source per spaxel with BPT and compare fractions in high/low gradient regions**: BPT diagram per spaxel using Kewley (2001), Kauffmann (2003) and Cid Fernandes (2011) lines; define H regions as above the upper 5th percentile of velocity gradient in the bar (nuclear regions and bar ends excluded), L as below, IB interbar, A all other regions; compare fraction of star-forming spaxels  
  > "All the spaxels which satisfy the amplitude-over-noise ratio of emission-lines greater than 5 are plotted." (6.1 BPT map); "We define the high velocity gradient regions in the bar (H) as those with their velocity gradients greater than the upper 5th percentile in the bar for each galaxy" (6.2 SF classified with the BPT); "Nuclear regions and bar ends are excluded in this “bar” region" (6.2 SF classified with the BPT)
   - parameter: emission-line amplitude-over-noise > 5  
  > "amplitude-over-noise ratio of emission-lines greater than 5" (6.1 BPT map)
   - fitting: _not stated_
   - validation: Result compared with the MaNGA bar BPT picture of Krishnarao et al. and checked with perpendicular and parallel gradient components separately  
  > "Figure [11](#fig:ratio_bpt) also shows that in the interbar region (IB), the majority of spaxels are either composite or LINER which is consistent with the results of (cite: Krishnarao_20b)." (6.2 SF classified with the BPT); "We obtain the same results that the ratio of SF group is lower in high velocity gradient regions compared to the others." (7 Velocity gradient perpendicular to the bar and parallel to the bar)

## Software

- **pPXF** : Halpha flux and kinematics in PHANGS-MUSE (stellar continuum and Halpha Gaussian fit)  
  > "H$\alpha$ flux and kinematics of the PHANGS-MUSE are obtained using pPXF ((cite: Cappellari_04))." (2 Data)
- **3D-BAROLO** : 3D tilted-ring galaxy rotation model of the Halpha velocity field  
  > "The position angle, inclination of the galaxies, and center are fixed to the values from Table 2 of (cite: lang_20) in running 3D–BAROLO." (2 Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Velocity gradient in the bar region of NGC 1365 | 0.1 - 1.0 | not stated | km/s/pc | 3 | The velocity gradients of bar region in NGC 1365 range between 0.1 – 1.0 |
| NGC 1365 slit 1 velocity jump within 5 arcsec (475 pc): CO / Halpha | CO up to 200, Halpha up to 150 | not stated | km/s | 5 | Within 5”(475 pc), the velocity of CO changes up to 200 km$\,\rm s^{-1}$, and that of H$\alpha$ changes up to 150 km$\,\rm s^{-1}$ in slit 1. |
| NGC 1365 slit 3 Halpha velocity jump within 2 arcsec (190 pc) after removing rotation model | 140 (170 after deprojection) | not stated | km/s | 5 | we still find the velocity changes reaching 140 km$\,\rm s^{-1}$ (170 km$\,\rm s^{-1}$ after deprojecion) within 2”(190 pc) in slit 3 |
| NGC 1365 slit 1 Halpha velocity jump within 4 arcsec (380 pc) after removing rotation model | 90 (110 after deprojection) | not stated | km/s | 5 | and 90 km$\,\rm s^{-1}$ (110 km$\,\rm s^{-1}$ after deprojection) within 4”(380 pc) in slit 1 for NGC 1365 |
| Velocity jumps in the other three galaxies after rotation removal, within 2 arcsec | 50 to 80 (75 to 95 after deprojection) | not stated | km/s | 5 | Velocity jumps of other sample galaxies after removal of the galaxy rotation span from 50 to 80 km$\,\rm s^{-1}$ (75 to 95 km$\,\rm s^{-1}$ after deprojection) within 2” |
| Fraction of star-forming (BPT) spaxels in high velocity gradient bar regions | ~2 - 40 | not stated | percent | 7 | The fraction of SF group in high velocity gradient regions of the bar spans $\sim$ 2 – 40$\%$. |
| Mean SFR surface density of SF spaxels relative to composite/LINER/Seyfert spaxels | ~5 times higher | not stated | dimensionless | 7 | the mean SFR surface density is $\sim$5 times higher on average compared to the spaxels of composite, LINER, and Seyfert |
| Mean velocity gradient of SF spaxels relative to others | ~20% lower on average | not stated | percent | 7 | SF spaxels span slightly narrow range of velocity gradients with lower ($\sim$20$\%$ on average) mean value. |

## Qualitative findings

- Velocity gradient maps highlight bar dust lanes and also pick up expanding shells around HII regions  
  > "Velocity gradient maps also efficiently pick up expanding shells around HII regions." (abstract)
- Enhanced velocity gradients either coincide with CO intensity peaks along the dust lanes or are slightly offset, depending on the object  
  > "In summary, the locations of enhanced velocity gradient regions either coincide with the peak of the CO emissions or are slightly offset to them, depending on the objects." (3.4 Comparison to the CO Map)
- Star formation is hindered in bar-driven shear and shocks  
  > "Our results imply that SF is hindered in bar-driven shear and shocks." (5 Impact of shear and shock on star formation)

## Claim tuples

- H: Bar-driven shocks and shear produce enhanced velocity gradients along the bar dust lanes | E: Halpha velocity gradient maps from V_Halpha - V_star (PHANGS-MUSE) for four barred galaxies | R: Enhanced velocity gradients along the dust lanes, covering almost the whole bar except for NGC 1365 | F: Velocity gradients are enhanced where shocks and shear are expected | **supported**
- H: Large velocity jumps occur across the high-gradient regions even without circular rotation | E: Pseudo slits across high-gradient regions in Halpha and PHANGS-ALMA CO velocity maps, with and without rotation-model subtraction | R: Halpha and CO velocities jump by up to ~170 km/s after rotation removal and deprojection (50 to 150 km/s range in summary) | F: Bar-driven shear and shocks produce velocity jumps comparable to earlier observations and simulations | **supported**
- H: Star formation is inhibited where bar-driven shear and shocks are strong | E: Compare extinction-corrected Halpha SFR surface density with velocity gradient per spaxel (coloured by Sigma_mol from CO) and compare BPT SF fractions in high versus low gradient bar regions | R: Upper envelope of SFR surface density decreases with velocity gradient; fraction of SF spaxels is lower in high-gradient bar regions | F: SF is inhibited in the high velocity gradient regions of the bar | **supported**
- H: Emission-line ratios are elevated toward composite or LINER by bar-driven shear and shocks | E: BPT classification of spaxels in high versus low velocity gradient bar regions | R: Most high-gradient regions are composite or LINER; difference negligible for NGC 1512 | F: Elevation may be due to shocks, but absence of recent SF revealing LINER-like emission cannot be ruled out | **partially**

## Reasoning

- Why this data: PHANGS-MUSE and PHANGS-ALMA give more resolved datasets (<~100 pc) than large IFS surveys  
  > "provide more resolved datasets (with spatial resolution $\lesssim$ 100 pc)" (1 Introduction)
- Why this method: Halpha rather than CO used for gradient maps because CO is patchy or not detected along parts of the bar  
  > "bar regions are not sufficiently detected or are patchy along and adjacent to the bar." (3.1 Deriving gas velocity gradient maps)
- Alternative: Gradient map from Halpha minus rotation model was rejected in favour of Halpha minus stellar velocity because non-smooth rotation models give bumpy maps  
  > "However, when galaxy rotation models are not smooth, the resulting velocity gradient maps becomes bumpy and thus unsuitable for investigating the velocity gradients." (3.1 Deriving gas velocity gradient maps)
- Alternative: CO velocity gradient maps over the full bar were tried but rejected  
  > "We also have tried to obtain the velocity gradient using CO from the PHANGS-ALMA data set." (3.1 Deriving gas velocity gradient maps)
- How they decided it was enough: _not stated_
- Limitation (authors): Velocity gradients are lower limits because of spatial and spectral smoothing  
  > "Our results should be considered as a lower limit of the velocity gradient because of the smoothing effect due to the spatial resolution" (3.3 Velocity gradients due to bar-driven gas inflow)
- Limitation (authors): Perpendicular or parallel gradients do not cleanly separate shear from shock because dust lanes are curved  
  > "Thus, even velocity gradients perpendicular (parallel) to the bar may not perfectly represent shear (shock)." (3.1 Deriving gas velocity gradient maps)
- Limitation (authors): Direct comparison of velocity jumps with simulations is not straightforward because only line-of-sight velocity is measured  
  > "It is not straightforward to directly compare the values of velocity jump from simulations with our observational data analysis, because we only measure the line of sight velocity." (4 Velocity Jumps)
- Caveat (inferred, ours): Only four galaxies; the SF-inhibition conclusion rests on a qualitative envelope in SFR surface density versus gradient plots with no stated statistical test
- Caveat (inferred, ours): High-gradient threshold (upper 5th percentile per galaxy) is relative, so each galaxy always has an H region regardless of absolute shear
- Caveat (inferred, ours): Halpha-based SFR in LINER/composite regions can be contaminated by non-SF ionisation, which is circular with the BPT-based SF fraction
- Caveat (inferred, ours): SFR relation printed with 5.3 x 10^42 (likely sign typo in exponent) and no stated uncertainty
- Caveat (inferred, ours): ALMA CO provides only context and Sigma_mol colouring; CO velocity gradients not obtainable over the whole bar so the shock/shear signal is entirely Halpha-based
- Caveat (inferred, ours): Masking constant C chosen empirically per galaxy (0.2 vs -0.05) may influence the gradient maps

## Reproducibility

- Data public (paper): PHANGS-MUSE raw and reduced data available at the ESO Science Archive Facility; PHANGS-ALMA release not stated as public in this paper  
  > "Raw and reduced data are available at the ESO Science Archive Facility." (Acknowledgments)
- Products in archive: _not stated_
- Missing: ALMA project codes and PHANGS-ALMA product version
- Missing: Pseudo-slit positions and averaging
- Missing: 3D-BAROLO ring setup and configuration
- Missing: Bar radius and interbar region definitions
- Missing: Exact BPT classification equations and extinction curve
- Missing: No analysis code released
- Data volume (inferred): Small to moderate: PHANGS-MUSE mosaic cubes (several GB each) plus PHANGS-ALMA CO moment maps for four galaxies; no raw ALMA visibility processing needed
- Score (inferred): 3/5, Public PHANGS data products and a fairly explicit gradient-map recipe with numeric thresholds, but pseudo slits, BAROLO ring settings, bar radius definitions and PHANGS-ALMA product details are missing and no code is released.
- Rediscovery candidate: no, ALMA plays a minor supporting role and the main Halpha/BPT results depend on MUSE products and several undefined region and slit choices.

## Links

- Method: (cite: emsellem_22) (PHANGS-MUSE data products and pPXF fitting description)
- Method: (cite: leroy_21b) (PHANGS-ALMA CO (2-1) data products)
- Method: (cite: diteodoro_15) (3D-BAROLO tilted-ring modelling)
- Method: (cite: Cappellari_04) (pPXF used for Halpha and stellar kinematics)
- Method: (cite: querejeta_21) (Environmental masks for bar, bar ends and nuclear regions)
- Companion: (cite: schinnerer_23) (JWST/MIRI, ALMA and MUSE study of NGC 1365 inflow along the dust lanes, discussed in the notes on NGC 1365)
- Related: PHANGS-MUSE
- Related: PHANGS-ALMA
- Related: TIMER
- Related: MAGNUM

## Checks

```json
{
 "quotes": 100,
 "quotes_ok": 100,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00650.S",
  "2013.1.00803.S",
  "2013.1.01161.S",
  "2015.1.00121.S",
  "2015.1.00782.S",
  "2015.1.00925.S",
  "2015.1.00956.S",
  "2016.1.00386.S",
  "2017.1.00392.S",
  "2017.1.00766.S",
  "2017.1.00886.L",
  "2018.1.00484.S",
  "2018.1.01321.S",
  "2018.1.01651.S",
  "2018.A.00062.S",
  "2019.2.00129.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 116,
  "stated": 69,
  "rate": 0.595
 },
 "evidence_ok": true
}
```
