# PHANGS-JWST First Results: Variations in PAH Fraction as a Function of ISM Phase and Metallicity

`2023ApJ...944L..11C` | The Astrophysical Journal Letters 2023 | first author: Chastenet, Jérémy | arXiv: 2301.00578 | DOI: 10.3847/2041-8213/acadd7

Card schema 1.0 | model gemini-3.8-flash | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies
- Question: How does the fraction of dust in the form of polycyclic aromatic hydrocarbons (PAHs) vary as a function of ISM phase, galactic environment, and metallicity across nearby galaxies?  
  > "In this Letter, we investigate the variations of the PAH fraction traced by a combination of JWST/MIRI filters across the full disk of four nearby galaxies, IC 5332, NGC 628, NGC 1365, and NGC 7496." (Introduction); "By tracking the PAH fraction across the multi-phase ISM, we are able to determine how a range of ISM properties affect the relative abundance of PAHs with respect to large dust grains." (Introduction)
- Target **IC 5332**: coordinates R. A. 23:34:27.488, Dec -36:06:3.89  
  > "| IC 5332 | $23:34:27.488$ | $-36:06:3.89$ | 9.01 | 74.4 | 26.9 | 3.03 | 3.3 | $1.8 - 4.8$ |" (Table 1); z/distance 9.01 Mpc  
  > "| IC 5332 | $23:34:27.488$ | $-36:06:3.89$ | 9.01 | 74.4 | 26.9 | 3.03 | 3.3 | $1.8 - 4.8$ |" (Table 1); distance from _not stated_
- Target **NGC 628**: coordinates R. A. 01:36:41.745, Dec +15:47:1.11  
  > "| NGC 628 | $01:36:41.745$ | $+15:47:1.11$ | 9.84 | 20.7 | 8.9 | 4.94 | 4.7 | $3.8 - 5.6$ |" (Table 1); z/distance 9.84 Mpc  
  > "| NGC 628 | $01:36:41.745$ | $+15:47:1.11$ | 9.84 | 20.7 | 8.9 | 4.94 | 4.7 | $3.8 - 5.6$ |" (Table 1); distance from _not stated_
- Target **NGC 1365**: coordinates R. A. 03:33:36.458, Dec -36:08:26.37  
  > "| NGC 1365 | $03:33:36.458$ | $-36:08:26.37$ | 19.57 | 201.1 | 55.4 | 6.01 | 5.1 | $3.8 - 6.3$ |" (Table 1); z/distance 19.57 Mpc  
  > "| NGC 1365 | $03:33:36.458$ | $-36:08:26.37$ | 19.57 | 201.1 | 55.4 | 6.01 | 5.1 | $3.8 - 6.3$ |" (Table 1); distance from _not stated_
- Target **NGC 7496**: coordinates R. A. 23:09:47.288, Dec -43:25:40.28  
  > "| NGC 7496 | $23:09:47.288$ | $-43:25:40.28$ | 18.72 | 193.7 | 35.9 | 1.67 | 3.6 | $1.8 - 5.3$ |" (Table 1); z/distance 18.72 Mpc  
  > "| NGC 7496 | $23:09:47.288$ | $-43:25:40.28$ | 18.72 | 193.7 | 35.9 | 1.67 | 3.6 | $1.8 - 5.3$ |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00650.S, 2013.1.01161.S, 2015.1.00925.S, 2015.1.00956.S, 2017.1.00392.S, 2017.1.00766.S, 2017.1.00886.L, 2018.1.01651.S, 2018.A.00062.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m+7m+Total Power  
  > "We use $^{12}{m CO}~(2-1)$“broad” moment 0 maps and corresponding error maps from the PHANGS-ALMA survey combining ${m 12m+7m+Total~Power}$ (cite: PHANGSALMA2021Pipeline; PHANGSALMA2021Survey)" (Ancillary data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1'' (~40 - 90 pc in our sample)  
  > "to trace molecular gas, at $\sim 1''$ ($\sim 40 - 90$ pc in our sample) resolution." (Ancillary data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: archival  
  > "We use $^{12}{m CO}~(2-1)$“broad” moment 0 maps and corresponding error maps from the PHANGS-ALMA survey combining ${m 12m+7m+Total~Power}$" (Ancillary data)
- Line: 12CO 2-1 (not stated)
- Other facility **JWST**: MIRI F770W, F1130W, and F2100W imaging of PAH features and hot dust continuum  
  > "We use MIRI (cite: rieke2015) observations in the F770W, F1130W, and F2100W filters, from the latest reference files at the time of processing, as described by (cite: LEE_PHANGSJWST) and (cite: LEROY1_PHANGSJWST)." (JWST/MIRI data)
- Other facility **VLT (MUSE)**: H-alpha maps at ~0.8'' resolution tracing ionized gas and derived metallicity maps  
  > "We use H$\alpha$ maps from the PHANGS-MUSE survey (cite: PHANGSMUSE2022Survey) to trace ionized gas. We use the ‘native’ resolution maps, with an average $\sim 0.8''$ resolution, and a $0.2''$ pixel size." (Ancillary data)
- Other facility **MeerKAT**: H I 21 cm measurements at 15'' resolution for NGC 7496  
  > "We use Hi measurements from MeerKAT (C. Eibensteiner et al., in prep), at $15''$ resolution for NGC 7496" (Ancillary data)
- Other facility **VLA (THINGS)**: H I 21 cm measurements at ~11'' resolution for NGC 628  
  > "and from THINGS (cite: Walter2008) for NGC 628 ($\sim 11''$ for the ‘natural’ weighted map)." (Ancillary data)
- Other facility **Spitzer**: Anchoring JWST background removal  
  > "The background removal is done by anchoring the JWST data with Spitzer, where the background in these sources was better estimated." (Noise properties and masks)
- External data: 2D 12+log(O/H) metallicity maps constructed via Gaussian Process Regression from H II region metallicities  
  > "To trace the ${m 12+log(O/H)}$ metallicity in our targets, we use the 2D maps by (cite: Williams2022)." (Ancillary data) [from (cite: Williams2022)]
- External data: Spatial masks classifying pixels into five galactic environments  
  > "we plot the median values of $R_{m PAH}$ in different galactic environments, identified by (cite: Querejeta2021). We use their spatial mask to separate pixels in 5 different categories" (Variation of PAH fraction with ISM environment) [from (cite: Querejeta2021)]
- External data: Catalogs of brightest H II regions  
  > "The white contours show the brightest H II regions (cite: GROVES_HIICAT; PHANGSMUSE2022HII)." (Qualitative description) [from (cite: GROVES_HIICAT; PHANGSMUSE2022HII)]

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
- masking: S/N <= 3 removed; central AGN saturation and diffraction spikes masked  
  > "We remove pixels with signal-to-noise ${m S/N \leq 3}$ in all MIRI bands, with background noise values of 0.05, 0.05, and 0.1 MJy sr$^{-1}$." (Noise properties and masks); "In NGC 1365 and NGC 7496, we mask pixels in the center due to IR brightness of the active galactic nuclei (AGN), which saturate the signal mostly in the F2100W band." (Noise properties and masks)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 1''  
  > "We convolve all three filter maps to $1''$ resolution, which is larger than the full-width at half-maximum of the F2100W filter ($0.67''$)." (JWST/MIRI data)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- CO-to-H2 conversion factor alpha_CO = 4.35 M_sun pc^-2 (K km s^-1)^-1  
  > "we use a constant CO-to-H$_2$ conversion factor $\alpha_{m CO} = 4.35$ M$_\odot$ pc$^{-2}$ (K km s$^{-1})^{-1}$ as recommended for solar metallicity, star-forming galaxies (cite: Bolatto2013)" (Ancillary data) [from (cite: Bolatto2013)]
- CO(2-1) to CO(1-0) line ratio R_21 = 0.65  
  > "and a $^{12}\mathrm{CO}(2-1)/^{12}\mathrm{CO}(1-0)$ line ratio $R_{21} = 0.65$ (cite: denBrok2021; Leroy2022)." (Ancillary data) [from (cite: denBrok2021; Leroy2022)]
- Prescription for atomic gas mass surface density from 21 cm emission  
  > "We convert the maps to have units of atomic gas mass surface density including helium assuming optically thin 21 cm emission, using the prescription from (cite: Leroy2012)." (Ancillary data) [from (cite: Leroy2012)]
- Assumed flat atomic gas surface density distribution of Sigma_HI = 8 M_sun pc^-2  
  > "we assume that the atomic gas has a flat distribution with ${m \Sigma_{H{\sc I}} = 8~M_\odot~pc^{-2}}$ (including helium)." (Ancillary data) [from (cite: Schruba2011; Bigiel2012; KennicuttReview; Wong2013)]
- Convolution method using theoretical PSFs  
  > "The convolution kernels were computed using the theoretical PSFs of each filter provided by the WEBBPSF (cite: WebbPSF), and the method described in (cite: Aniano2011)." (JWST/MIRI data) [from (cite: Aniano2011)]
- Galactic environment definitions and spatial masks  
  > "we plot the median values of $R_{m PAH}$ in different galactic environments, identified by (cite: Querejeta2021). We use their spatial mask to separate pixels in 5 different categories" (Variation of PAH fraction with ISM environment) [from (cite: Querejeta2021)]

### Not stated but needed to reproduce (our reading)

- Precise spatial boundaries and aperture radii for masking the central AGN regions in NGC 1365 and NGC 7496.
- Exact pixel coordinates or hand-drawn polygonal definitions for masking central diffraction spikes in NGC 1365 and NGC 7496.

## Analysis recipe

1. **Convolve and reproject images to a common 1'' spatial resolution**: Convolve MIRI F770W, F1130W, and F2100W maps and ancillary maps with resolution lower than 1'' to a common 1'' resolution using WebbPSF theoretical PSFs and Aniano et al. (2011) convolution kernels. Reproject HI maps to the MIRI pixel grid (0.11'' pixel size).  
  > "We convolve all three filter maps to $1''$ resolution, which is larger than the full-width at half-maximum of the F2100W filter ($0.67''$)." (JWST/MIRI data); "We reproject these maps to the MIRI pixel grid, with pixel size $\sim 0.11''$." (Ancillary data)
   - software: WEBBPSF
   - parameter: common angular resolution = 1''; MIRI pixel grid = ~0.11''  
  > "We convolve all three filter maps to $1''$ resolution, which is larger than the full-width at half-maximum of the F2100W filter ($0.67''$)." (JWST/MIRI data)
   - assumption: Theoretical PSFs from WebbPSF accurately represent the instrument beam  
  > "The convolution kernels were computed using the theoretical PSFs of each filter provided by the WEBBPSF (cite: WebbPSF), and the method described in (cite: Aniano2011)." (JWST/MIRI data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Subtract background, threshold low-S/N pixels, and mask AGN artifacts**: Subtract background anchored by Spitzer; estimate background noise in NGC 7496 and apply to all targets; mask pixels with S/N <= 3 in all MIRI bands; mask central AGN saturated pixels using WebbPSF centered on nucleus; mask remaining AGN diffraction spikes by hand.  
  > "We remove pixels with signal-to-noise ${m S/N \leq 3}$ in all MIRI bands, with background noise values of 0.05, 0.05, and 0.1 MJy sr$^{-1}$." (Noise properties and masks); "In NGC 1365 and NGC 7496, we mask pixels in the center due to IR brightness of the active galactic nuclei (AGN), which saturate the signal mostly in the F2100W band." (Noise properties and masks)
   - software: WEBBPSF
   - parameter: S/N threshold = 3; background noise values = 0.05, 0.05, and 0.1 MJy sr^-1 for F770W, F1130W, and F2100W  
  > "We remove pixels with signal-to-noise ${m S/N \leq 3}$ in all MIRI bands, with background noise values of 0.05, 0.05, and 0.1 MJy sr$^{-1}$." (Noise properties and masks)
   - assumption: MIRI maps across all four targets have similar background noise to NGC 7496  
  > "We find that MIRI maps have similar noise, and we assume NGC 7496 estimates throughout the sample." (Noise properties and masks)
   - fitting: _not stated_
   - validation: Visual hand inspection to mask residual central AGN spikes  
  > "We mask these by hand to ensure they do not bias our initial results." (Noise properties and masks)
3. **Calculate the PAH fraction proxy R_PAH**: Calculate the ratio R_PAH = (F770W + F1130W) / F2100W pixel-by-pixel.  
  > "Here, we use the JWST/MIRI $R{m_{PAH} = (F770W+F1130W)/F2100W}$ ratio as a proxy for the PAH fraction." (PAH Fraction)
   - parameter: R_PAH = (F770W + F1130W) / F2100W  
  > "Here, we use the JWST/MIRI $R{m_{PAH} = (F770W+F1130W)/F2100W}$ ratio as a proxy for the PAH fraction." (PAH Fraction)
   - assumption: F770W traces ionized PAHs, F1130W traces neutral PAHs, and F2100W traces small hot dust grains free from PAH contribution  
  > "the 7.7 $\mu$m feature is more representative of the ionized PAH population, and the 11.3 $\mu$m feature of the neutral population (cite: Rapacioli2005; Draine2021). We assume the F2100W filter is free from contribution from PAHs" (PAH Fraction)
   - fitting: _not stated_
   - validation: Validated by distinct behavior between F2100W and PAH-dominated bands shown in Leroy et al. (2022a)  
  > "This assumption is validated by a clear difference in behavior between the F2100W and PAH–dominated band emission, demonstrated in (cite: LEROY1_PHANGSJWST)." (PAH Fraction)
4. **Convert CO intensity and 21 cm data into molecular, atomic, and total gas surface densities**: Convert 12CO(2-1) broad moment 0 maps to Sigma_H2 using constant alpha_CO and R_21; determine Sigma_HI from 21 cm emission (or assume flat 8 M_sun pc^-2 for IC 5332 and NGC 1365); sum to get Sigma_HI+H2.  
  > "To convert CO intensity to molecular gas surface density, $\Sigma_{m H_2}$ in ${m M_\odot~pc^{-2}}$, we use a constant CO-to-H$_2$ conversion factor $\alpha_{m CO} = 4.35$ M$_\odot$ pc$^{-2}$ (K km s$^{-1})^{-1}$ as recommended for solar metallicity, star-forming galaxies (cite: Bolatto2013)" (Ancillary data); "we assume that the atomic gas has a flat distribution with ${m \Sigma_{H{\sc I}} = 8~M_\odot~pc^{-2}}$ (including helium)." (Ancillary data)
   - parameter: alpha_CO = 4.35 M_sun pc^-2 (K km s^-1)^-1; R_21 = 0.65; Sigma_HI = 8 M_sun pc^-2  
  > "we use a constant CO-to-H$_2$ conversion factor $\alpha_{m CO} = 4.35$ M$_\odot$ pc$^{-2}$ (K km s$^{-1})^{-1}$ as recommended for solar metallicity, star-forming galaxies (cite: Bolatto2013)" (Ancillary data); "and a $^{12}\mathrm{CO}(2-1)/^{12}\mathrm{CO}(1-0)$ line ratio $R_{21} = 0.65$ (cite: denBrok2021; Leroy2022)." (Ancillary data)
   - assumption: Constant alpha_CO and R_21; optically thin 21 cm emission; flat HI distribution over inner galaxy disks where resolved HI data are unavailable  
  > "assuming optically thin 21 cm emission, using the prescription from (cite: Leroy2012). We lack resolved 21 cm mapping for IC 5332 and NGC 1365." (Ancillary data)
   - fitting: _not stated_
   - validation: _not stated_
5. **Analyze PAH fraction trends with ISM phase, metallicity, radius, and galactic environment**: Compute I_Halpha / Sigma_HI+H2; bin R_PAH radially in r/r25 bins; evaluate medians and 16th-84th percentile ranges; compare R_PAH against I_Halpha / Sigma_HI+H2, molecular gas fraction, 12+log(O/H) metallicity maps, and environmental masks.  
  > "We combine the Hi and H$_2$ maps to estimate the total gas surface density, and use the ratio of H$\alpha$ intensity to total gas to follow the variations of the ISM conditions in each target (in units of ${m erg~s^{-1}~kpc^{-2}~(M_\odot~pc^{-2})^{-1}}$)." (Variation of PAH fraction with ISM environment)
   - parameter: Radial bins in r/r25; 5 morphological environments (bar, interarm, spiral arms, center, disk)  
  > "The top left panel of Figure 2 shows the radial profiles of $R_{m PAH}$, in bins of $r/r_{25}$." (Qualitative description); "We use their spatial mask to separate pixels in 5 different categories (see their Table 1)." (Variation of PAH fraction with ISM environment)
   - assumption: I_Halpha / Sigma_HI+H2 traces the fraction of line-of-sight gas in the ionized phase  
  > "Considering $I_{m H{\alpha}}/\Sigma_{m H{\sc I}+H_2}$ traces the fraction of ionized gas per unit of total gas, this common threshold could be a limit at which the amount of radiation producing the intense H$\alpha$ emission is able to destroy the PAHs" (Variation of PAH fraction with ISM environment)
   - fitting: _not stated_
   - validation: Error bars defined as 3 times the standard error of the mean (SEM)  
  > "In all panels, the error bars are 3 times the standard error of the mean (SEM)." (Qualitative description)

## Software

- **WEBBPSF** : Computing theoretical PSFs for convolution kernels and centering PSF on AGN coordinates for saturation masking  
  > "The convolution kernels were computed using the theoretical PSFs of each filter provided by the WEBBPSF (cite: WebbPSF), and the method described in (cite: Aniano2011)." (JWST/MIRI data); "This is done using the WEBBPSF package (cite: WebbPSF), and centering the F2100W PSF on the central coordinates of each target." (Noise properties and masks)
- **STScI Calibration pipeline** 1.7.0 for MIRI (1.7.1 for NIRCam): Pipeline calibration of JWST observations  
  > "The PHANGS-JWST team used the STScI Calibration pipeline 1.7.1 for NIRCam and 1.7.0 for MIRI, and Calibration Reference Data context number 0968 for both instruments." (JWST/MIRI data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| average R_PAH in IC 5332 | 3.3 | 1.8 - 4.8 | dimensionless | 3 | / IC 5332 / $23:34:27.488$ / $-36:06:3.89$ / 9.01 / 74.4 / 26.9 / 3.03 / 3.3 / $1.8 - 4.8$ / |
| average R_PAH in NGC 628 | 4.7 | 3.8 - 5.6 | dimensionless | 3 | / NGC 628 / $01:36:41.745$ / $+15:47:1.11$ / 9.84 / 20.7 / 8.9 / 4.94 / 4.7 / $3.8 - 5.6$ / |
| average R_PAH in NGC 1365 | 5.1 | 3.8 - 6.3 | dimensionless | 3 | / NGC 1365 / $03:33:36.458$ / $-36:08:26.37$ / 19.57 / 201.1 / 55.4 / 6.01 / 5.1 / $3.8 - 6.3$ / |
| average R_PAH in NGC 7496 | 3.6 | 1.8 - 5.3 | dimensionless | 3 | / NGC 7496 / $23:09:47.288$ / $-43:25:40.28$ / 18.72 / 193.7 / 35.9 / 1.67 / 3.6 / $1.8 - 5.3$ / |
| inflection threshold in I_Halpha / Sigma_HI+H2 for PAH fraction decrease | 10^37.5 | not stated | erg s^-1 kpc^-2 (M_sun pc^-2)^-1 | 5 | find that the PAH fraction decreases above a value of ${m I_{H\alpha}/\Sigma_{H{\sc I}+H_2}}~\sim~10^{37.5}~{m erg~s^{-1}~kpc^{-2}~(M_\odot~pc^{-2}})^{-1}$, in all four galaxies. |
| F770W background noise | 0.05 | not stated | MJy sr^-1 | 2 | with background noise values of 0.05, 0.05, and 0.1 MJy sr$^{-1}$. |
| F1130W background noise | 0.05 | not stated | MJy sr^-1 | 2 | with background noise values of 0.05, 0.05, and 0.1 MJy sr$^{-1}$. |
| F2100W background noise | 0.1 | not stated | MJy sr^-1 | 2 | with background noise values of 0.05, 0.05, and 0.1 MJy sr$^{-1}$. |

## Qualitative findings

- R_PAH shows clear depressions within bright H II regions traced by MUSE H-alpha.  
  > "In all cases, it appears that $R_{m PAH}$ shows clear depressions within H II regions, though NGC 628 and NGC 7496 show this contrast most clearly." (Qualitative description)
- R_PAH decreases with increasing radius and decreasing metallicity, with the galaxy-to-galaxy offset tracking average metallicity.  
  > "All galaxies show an overall decreasing trend with radius." (Qualitative description); "Overall, this offset nicely tracks the global galaxy metallicity gradients (cite: Kreckel2019; PHANGSMUSE2022HII; GROVES_HIICAT), in the lower H$\alpha$ intensity regions." (Variation of PAH fraction with ISM environment)
- R_PAH remains relatively constant across galactic morphological environments, peaking slightly in bar and interarm regions.  
  > "Here, we can see that $R_{m PAH}$ is the highest in the bar, and interarm regions, with lower values in the spiral arms, followed by the center and finally in the disk." (Variation of PAH fraction with ISM environment)

## Claim tuples

- H: Can the combination of JWST/MIRI filters R_PAH = (F770W + F1130W) / F2100W serve as an effective proxy to map the fraction of dust in PAHs relative to small hot grains across nearby galaxies? | E: Convolve JWST/MIRI F770W, F1130W, and F2100W maps to 1'' resolution across IC 5332, NGC 628, NGC 1365, and NGC 7496, remove noise and AGN saturation, and map R_PAH. | R: Average R_PAH values range between 3.3 and 5.1 across the targets and drop conspicuously within bright H II regions identified by MUSE H-alpha. | F: R_PAH is an effective tracer of the PAH fraction and confirms that PAHs are systematically depleted in H II regions. | **supported**
- H: Does the PAH fraction vary systematically with the interstellar gas phase as traced by ionized to total gas ratio? | E: Compare R_PAH against I_Halpha / Sigma_HI+H2 combining MUSE H-alpha with ALMA CO and MeerKAT/THINGS/assumed HI surface densities. | R: R_PAH remains flat up to I_Halpha / Sigma_HI+H2 ~ 10^37.5 erg s^-1 kpc^-2 (M_sun pc^-2)^-1, above which it systematically and steeply decreases in all four galaxies. | F: PAH destruction in ionized gas operates similarly across targets once the ionizing radiation is strong enough to overcome neutral gas shielding. | **supported**
- H: How does the resolved PAH fraction correlate with radial distance and gas metallicity? | E: Evaluate radial profiles in r/r25 bins and 2D distributions of R_PAH as a function of 12+log(O/H) metallicity maps. | R: R_PAH decreases with galactocentric radius, and the overall average R_PAH per galaxy correlates positively with galaxy-scale metallicity, while local metallicity variations within a galaxy produce no strong gradient in R_PAH. | F: Average galaxy metallicity sets the overall baseline abundance of the PAH population in the diffuse/neutral ISM, but local variations are governed primarily by ISM phase. | **supported**

## Reasoning

- Why this data: JWST/MIRI F770W and F1130W filters cover prominent ionized and neutral PAH features at high spatial resolution and sensitivity outside the Local Group, while F2100W traces larger, hot dust grains.  
  > "The MIRI F770W and F1130W filters provide coverage of two of the most prominent PAH features at 7.7$\mu$m and 11.3$\mu$m, while the F2100W filter lends a useful comparison, tracing emission from larger dust grains (cite: DL2007)." (Introduction)
- Why this method: Normalizing PAH features by F2100W isolates the PAH-only fraction and removes significant dependence on the interstellar radiation field because both PAH emission and 21 um dust continuum arise from stochastic heating.  
  > "As both the PAH features and the 21 $\mu$m continuum are from stochastic heating, using these fluxes to determine the PAH fraction removes any significant dependence on the radiation field (cite: DL2007)." (PAH Fraction)
- Alternative: Working at native F2100W resolution (0.67'') was rejected in favor of convolving to 1'' to boost S/N in F2100W and match the resolution of ancillary CO and H-alpha data.  
  > "We choose to slightly degrade the data to increase the signal-to-noise (S/N) in the F2100W band. By doing so, we are also able to match the resolution of the CO and H$\alpha$ data (see below)." (JWST/MIRI data)
- How they decided it was enough: These four galaxies constitute the first four targets observed and released as part of the PHANGS-JWST Treasury program #2107.  
  > "In this letter, we have used a combination of the JWST/MIRI F770W, F1130W, and F2100W filters to trace the abundance of PAHs relative to small dust grains in four nearby galaxies, IC 5332, NGC 628, NGC 1365, and NGC 7496, as part of the Treasury GO program PHANGS-JWST #2107." (Conclusions)
- Limitation (authors): Lack of resolved 21 cm mapping for IC 5332 and NGC 1365 required assuming a constant flat atomic gas surface density of 8 M_sun pc^-2.  
  > "We lack resolved 21 cm mapping for IC 5332 and NGC 1365. Based on the observed flatness of the atomic gas surface density over the inner parts of galaxy disks... we assume that the atomic gas has a flat distribution with ${m \Sigma_{H{\sc I}} = 8~M_\odot~pc^{-2}}$" (Ancillary data)
- Limitation (authors): Central AGN saturation and diffraction spikes required manual masking by hand in NGC 1365 and NGC 7496.  
  > "For this preliminary work, we remove additional conspicuous artifacts from the central AGN that remain after this analysis... We mask these by hand to ensure they do not bias our initial results." (Noise properties and masks)
- Limitation (authors): The sample contains only four galaxies spanning a narrow range of metallicity, leaving universal threshold determination to future expanded studies.  
  > "However, it should be pointed out that there are (currently) no similar resolution Hi data for IC 5332 and NGC 1365, and therefore a universal threshold across all environments is left for future studies." (Variation of PAH fraction with ISM environment)
- Caveat (inferred, ours): Assuming a constant flat HI surface density for IC 5332 and NGC 1365 may introduce systematic trends in the total gas surface density and ionized-to-total gas ratios.
- Caveat (inferred, ours): Manual by-hand masking of AGN diffraction spikes introduces subjectivity in the central regions.
- Caveat (inferred, ours): Applying the NGC 7496 background noise estimate across all four galaxies might slightly over- or under-mask pixels in the other targets.

## Reproducibility

- Data public (paper): yes  
  > "Some/all of the data presented in this paper were obtained from the Mikulski Archive for Space Telescopes (MAST) at the Space Telescope Science Institute... This paper makes use of the following ALMA data" (Acknowledgments)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Specific mask geometry files for the central AGN and manual diffraction spike masks in NGC 1365 and NGC 7496.
- Missing: The unpublished MeerKAT HI map for NGC 7496.
- Data volume (inferred): 50 GB - 200 GB
- Score (inferred): 7/5, The primary JWST/MIRI, ALMA CO, and MUSE H-alpha data are publicly available from MAST, the ALMA archive, and ESO/PHANGS releases. The definitions of R_PAH and the gas surface density conversion formulas are fully specified. Exact numerical reproduction is slightly hindered by manual masking of AGN diffraction spikes and reliance on an unpublished MeerKAT HI map for NGC 7496.
- Rediscovery candidate: yes, The core numeric results (mean R_PAH values, radial trends, and the universal I_Halpha/Sigma_gas threshold of ~10^37.5) can be rediscovered using public PHANGS survey data (MIRI, ALMA, MUSE) following the described filter combination and masking recipes.

## Links

- Method: (cite: Aniano2011) (Method for constructing convolution kernels to match theoretical PSF resolutions)
- Method: (cite: Bolatto2013) (Prescription for alpha_CO conversion factor in star-forming galaxies)
- Method: (cite: Leroy2012) (Prescription for calculating atomic gas surface density assuming optically thin 21 cm emission)
- Method: (cite: DL2007) (PAH and dust physical models justifying stochastic heating band ratios as proxies for PAH mass fraction)
- Companion: (cite: LEE_PHANGSJWST) (PHANGS-JWST Treasury program survey overview and initial data description)
- Companion: (cite: LEROY1_PHANGSJWST) (PHANGS-JWST data reduction and initial results on dust emission bands)
- Companion: (cite: EGOROV_PHANGSJWST) (PHANGS-JWST companion paper focusing on PAH fraction inside H II regions)
- Companion: (cite: CHASTENET2_PHANGSJWST) (PHANGS-JWST companion paper analyzing PAH size and charge distributions)
- Related: PHANGS-JWST
- Related: PHANGS-ALMA
- Related: PHANGS-MUSE
- Related: THINGS

## Checks

```json
{
 "quotes": 92,
 "quotes_ok": 89,
 "quote_pass_rate": 0.967,
 "quotes_too_long": 6,
 "unsupported_facts": 0,
 "project_codes": 9,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2018.A.00062.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 101,
  "stated": 59,
  "rate": 0.584
 },
 "evidence_ok": false
}
```
