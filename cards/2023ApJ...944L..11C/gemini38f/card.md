# PHANGS-JWST First Results: Variations in PAH Fraction as a Function of ISM Phase and Metallicity

`2023ApJ...944L..11C` | The Astrophysical Journal Letters 2023 | first author: Chastenet, Jérémy | arXiv: 2301.00578 | DOI: 10.3847/2041-8213/acadd7

Card schema 1.0 | model gemini-3.8-flash | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, milky_way_ism
- Question: How does the PAH fraction vary as a function of ISM phase (ionized, neutral, molecular) and metallicity across nearby galaxy disks?  
  > "In this Letter, we investigate the variations of the PAH fraction traced by a combination of JWST/MIRI filters across the full disk of four nearby galaxies, IC 5332, NGC 628, NGC 1365, and NGC 7496." (1 Introduction)
- Target **IC 5332**: coordinates 23:34:27.488 -36:06:3.89  
  > "IC 5332 | 23:34:27.488 | -36:06:3.89 | 9.01 | 74.4 | 26.9 | 3.03" (Table 1); z/distance 9.01 Mpc  
  > "IC 5332 | 23:34:27.488 | -36:06:3.89 | 9.01 | 74.4 | 26.9 | 3.03" (Table 1); distance from _not stated_
- Target **NGC 628**: coordinates 01:36:41.745 +15:47:1.11  
  > "NGC 628 | 01:36:41.745 | +15:47:1.11 | 9.84 | 20.7 | 8.9 | 4.94" (Table 1); z/distance 9.84 Mpc  
  > "NGC 628 | 01:36:41.745 | +15:47:1.11 | 9.84 | 20.7 | 8.9 | 4.94" (Table 1); distance from _not stated_
- Target **NGC 1365**: coordinates 03:33:36.458 -36:08:26.37  
  > "NGC 1365 | 03:33:36.458 | -36:08:26.37 | 19.57 | 201.1 | 55.4 | 6.01" (Table 1); z/distance 19.57 Mpc  
  > "NGC 1365 | 03:33:36.458 | -36:08:26.37 | 19.57 | 201.1 | 55.4 | 6.01" (Table 1); distance from _not stated_
- Target **NGC 7496**: coordinates 23:09:47.288 -43:25:40.28  
  > "NGC 7496 | 23:09:47.288 | -43:25:40.28 | 18.72 | 193.7 | 35.9 | 1.67" (Table 1); z/distance 18.72 Mpc  
  > "NGC 7496 | 23:09:47.288 | -43:25:40.28 | 18.72 | 193.7 | 35.9 | 1.67" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00650.S, 2013.1.01161.S, 2015.1.00925.S, 2015.1.00956.S, 2017.1.00392.S, 2017.1.00766.S, 2017.1.00886.L, 2018.1.01651.S, 2018.A.00062.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m+7m+Total Power  
  > "We use 12CO (2-1)“broad” moment 0 maps and corresponding error maps from the PHANGS-ALMA survey combining 12m+7m+Total Power (cite: PHANGSALMA2021Pipeline; PHANGSALMA2021Survey), to trace molecular gas" (2.2 Ancillary data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~ 1'' (~ 40 - 90 pc)  
  > "to trace molecular gas, at ~ 1'' (~ 40 - 90 pc in our sample) resolution." (2.2 Ancillary data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO (2-1) (not stated)
- Other facility **JWST**: MIRI F770W, F1130W, and F2100W imaging from Treasury program #2107  
  > "The data used in this paper are part of the PHANGS-JWST Treasury program #2107 (cite: LEE_PHANGSJWST). We use MIRI (cite: rieke2015) observations in the F770W, F1130W, and F2100W filters" (2.1 JWST/MIRI data)
- Other facility **VLT/MUSE**: Halpha maps and metallicity maps from the PHANGS-MUSE survey  
  > "We use Halpha maps from the PHANGS-MUSE survey (cite: PHANGSMUSE2022Survey) to trace ionized gas." (2.2 Ancillary data)
- Other facility **MeerKAT**: H I 21 cm measurements at 15'' resolution for NGC 7496  
  > "We use Hi measurements from MeerKAT (C. Eibensteiner et al., in prep), at 15'' resolution for NGC 7496" (2.2 Ancillary data)
- Other facility **VLA (THINGS)**: H I 21 cm measurements at ~11'' resolution for NGC 628  
  > "and from THINGS (cite: Walter2008) for NGC 628 (~ 11'' for the ‘natural’ weighted map)." (2.2 Ancillary data)
- External data: 2D metallicity maps based on Gaussian Process Regression of H II region metallicity  
  > "To trace the 12+log(O/H) metallicity in our targets, we use the 2D maps by (cite: Williams2022)." (2.2 Ancillary data) [from (cite: Williams2022)]
- External data: Morphological environment masks separating galaxy pixels into categories  
  > "In the bottom left panel of Figure 2, we plot the median values of RPAH in different galactic environments, identified by (cite: Querejeta2021). We use their spatial mask to separate pixels in 5 different categories" (3.2 Variation of PAH fraction with ISM environment) [from (cite: Querejeta2021)]

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

- CO moment 0 maps and error maps processing  
  > "from the PHANGS-ALMA survey combining 12m+7m+Total Power (cite: PHANGSALMA2021Pipeline; PHANGSALMA2021Survey)" (2.2 Ancillary data) [from (cite: PHANGSALMA2021Pipeline; PHANGSALMA2021Survey)]
- CO-to-H2 conversion factor and line ratio R21  
  > "alpha_CO = 4.35 M_sun pc^-2 (K km s^-1)^-1 as recommended for solar metallicity, star-forming galaxies (cite: Bolatto2013), and 12CO (2-1) conversion factor and a 12CO(2-1)/12CO(1-0) line ratio R_21 = 0.65 (cite: denBrok2021; Leroy2022)." (2.2 Ancillary data) [from (cite: Bolatto2013; denBrok2021; Leroy2022)]

## Analysis recipe

1. **Convolve imaging and ancillary maps to common angular resolution**: Convolve MIRI F770W, F1130W, and F2100W filter maps to 1'' resolution using theoretical PSFs from WEBBPSF and kernels constructed following Aniano et al. (2011); convolve ancillary maps with resolution lower than 1'' to 1'' and reproject H I maps to MIRI grid.  
  > "We convolve all three filter maps to 1'' resolution, which is larger than the full-width at half-maximum of the F2100W filter (0.67''). The convolution kernels were computed using the theoretical PSFs of each filter provided by the WEBBPSF (cite: WebbPSF)" (2.1 JWST/MIRI data)
   - software: WEBBPSF
   - parameter: Target resolution = 1''  
  > "We convolve all three filter maps to 1'' resolution" (2.1 JWST/MIRI data)
   - assumption: Flat atomic gas surface density Sigma_HI = 8 M_sun pc^-2 for IC 5332 and NGC 1365  
  > "Based on the observed flatness of the atomic gas surface density over the inner parts of galaxy disks... we assume that the atomic gas has a flat distribution with Sigma_HI = 8 M_sun pc^-2 (including helium)." (2.2 Ancillary data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive molecular gas surface density from CO**: Convert 12CO (2-1) broad moment 0 map to Sigma_H2 adopting constant alpha_CO and R_21  
  > "To convert CO intensity to molecular gas surface density, Sigma_H2 in M_sun pc^-2, we use a constant CO-to-H2 conversion factor alpha_CO = 4.35 M_sun pc^-2 (K km s^-1)^-1... and a 12CO(2-1)/12CO(1-0) line ratio R21 = 0.65" (2.2 Ancillary data)
   - parameter: alpha_CO = 4.35 M_sun pc^-2 (K km s^-1)^-1; R_21 = 0.65  
  > "alpha_CO = 4.35 M_sun pc^-2 (K km s^-1)^-1 as recommended for solar metallicity, star-forming galaxies (cite: Bolatto2013), and 12CO (2-1) conversion factor and a 12CO(2-1)/12CO(1-0) line ratio R21 = 0.65" (2.2 Ancillary data)
   - assumption: Constant conversion factors across the targets  
  > "we use a constant CO-to-H2 conversion factor alpha_CO = 4.35 M_sun pc^-2 (K km s^-1)^-1 as recommended for solar metallicity, star-forming galaxies" (2.2 Ancillary data)
   - fitting: _not stated_
   - validation: _not stated_
3. **Compute PAH fraction proxy and analyze trends with ISM phase and metallicity**: Calculate R_PAH = (F770W + F1130W) / F2100W pixel-by-pixel after S/N thresholding (S/N > 3) and AGN masking; measure radial profiles, trends with I_Halpha / Sigma_(HI + H2), molecular gas fraction, and environment  
  > "Here, we use the JWST/MIRI R_PAH = (F770W+F1130W)/F2100W ratio as a proxy for the PAH fraction." (3 PAH Fraction); "We remove pixels with signal-to-noise S/N <= 3 in all MIRI bands, with background noise values of 0.05, 0.05, and 0.1 MJy sr^-1." (2.3 Noise properties and masks)
   - parameter: S/N > 3 threshold; background noise 0.05, 0.05, 0.1 MJy sr^-1 for F770W, F1130W, F2100W  
  > "We remove pixels with signal-to-noise S/N <= 3 in all MIRI bands, with background noise values of 0.05, 0.05, and 0.1 MJy sr^-1." (2.3 Noise properties and masks)
   - assumption: F2100W filter is dominated by small, hot dust grains and free from PAH contribution  
  > "We assume the F2100W filter is free from contribution from PAHs and is instead dominated by small, hot dust grains" (3 PAH Fraction)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **WEBBPSF** : Computing theoretical PSFs for MIRI convolution kernels and AGN PSF masking  
  > "The convolution kernels were computed using the theoretical PSFs of each filter provided by the WEBBPSF (cite: WebbPSF)" (2.1 JWST/MIRI data); "This is done using the WEBBPSF package (cite: WebbPSF), and centering the F2100W PSF on the central coordinates of each target." (2.3 Noise properties and masks)
- **STScI Calibration pipeline** 1.7.0 (MIRI), 1.7.1 (NIRCam): Calibration pipeline for PHANGS-JWST data  
  > "The PHANGS-JWST team used the STScI Calibration pipeline 1.7.1 for NIRCam and 1.7.0 for MIRI, and Calibration Reference Data context number 0968 for both instruments." (2.1 JWST/MIRI data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| average R_PAH in IC 5332 | 3.3 | 1.8 - 4.8 | dimensionless | 3 | IC 5332 / 23:34:27.488 / -36:06:3.89 / 9.01 / 74.4 / 26.9 / 3.03 / 3.3 / 1.8 - 4.8 |
| average R_PAH in NGC 628 | 4.7 | 3.8 - 5.6 | dimensionless | 3 | NGC 628 / 01:36:41.745 / +15:47:1.11 / 9.84 / 20.7 / 8.9 / 4.94 / 4.7 / 3.8 - 5.6 |
| average R_PAH in NGC 1365 | 5.1 | 3.8 - 6.3 | dimensionless | 3 | NGC 1365 / 03:33:36.458 / -36:08:26.37 / 19.57 / 201.1 / 55.4 / 6.01 / 5.1 / 3.8 - 6.3 |
| average R_PAH in NGC 7496 | 3.6 | 1.8 - 5.3 | dimensionless | 3 | NGC 7496 / 23:09:47.288 / -43:25:40.28 / 18.72 / 193.7 / 35.9 / 1.67 / 3.6 / 1.8 - 5.3 |
| PAH fraction breakdown threshold in I_Halpha / Sigma_(HI + H2) | 10^37.5 | not stated | erg s^-1 kpc^-2 (M_sun pc^-2)^-1 | 3 | We use CO+Hi+Halpha to trace the interstellar gas phase and find that the PAH fraction decreases above a value of I_Halpha/Sigma_HI+H2 ~ 10^37.5 erg s^-1 kpc^-2 (M_odot pc^-2)^-1, in all four galaxies. |

## Qualitative findings

- R_PAH shows clear depressions within H II regions traced by MUSE Halpha.  
  > "In all cases, it appears that R_PAH shows clear depressions within H II regions, though NGC 628 and NGC 7496 show this contrast most clearly." (3.1 Qualitative description)
- PAH fraction decreases with increasing galactocentric radius, tracking metallicity gradients.  
  > "All galaxies show an overall decreasing trend with radius." (3.1 Qualitative description); "Radial profiles also show a decreasing PAH fraction with increasing radius, correlated with lower metallicity, in line with previous results showing a strong metallicity dependence to the PAH fraction." (abstract)
- The PAH fraction remains relatively constant across morphological environments with only slight variations (highest in bars and interarms, lower in spiral arms, centers, and disks).  
  > "In this panel, it appears that there is no striking differences between environments, again showing minimal variations of a few tens of percent, for individual galaxies." (3.2 Variation of PAH fraction with ISM environment)

## Claim tuples

- H: The PAH fraction varies with ISM phase and drops in ionized gas-dominated environments due to PAH destruction. | E: Compare R_PAH = (F770W + F1130W)/F2100W from JWST/MIRI against I_Halpha / Sigma_(HI + H2) derived from MUSE Halpha and PHANGS-ALMA CO + 21 cm H I data. | R: R_PAH remains flat until I_Halpha / Sigma_(HI + H2) reaches ~ 10^37.5 erg s^-1 kpc^-2 (M_sun pc^-2)^-1, above which it declines sharply across all four galaxies. | F: The process of PAH destruction in ionized gas operates similarly across diverse galactic targets at a common ionized-to-total gas threshold. | **supported**
- H: The PAH fraction correlates strongly with local and global metallicity. | E: Trace R_PAH against radial distance r/r_25 and gas-phase 12+log(O/H) maps derived from MUSE H II regions. | R: Global offsets in mean R_PAH correspond to average galaxy metallicity, and radial gradients show lower R_PAH at larger radii / lower metallicity. | F: Global metallicity sets the average PAH abundance in the neutral/diffuse ISM, though moderate local metallicity variations have secondary effects compared to ionized gas destruction. | **supported**

## Reasoning

- Why this data: MIRI F770W and F1130W trace ionized and neutral PAH emission respectively, while F2100W traces small hot dust continuum, allowing high-resolution mapping of the PAH fraction.  
  > "The MIRI F770W and F1130W filters provide coverage of two of the most prominent PAH features at 7.7um and 11.3um, while the F2100W filter lends a useful comparison, tracing emission from larger dust grains" (1 Introduction)
- Why this method: _not stated_
- Alternative: Using Voronoi binning instead of pixel-by-pixel analysis  
  > "It will also be possible to test a Voronoï binning, to check whether the trends seen in Figure 2 would be significantly pulled down by taking into account more low-S/N pixels." (3.2 Variation of PAH fraction with ISM environment)
- How they decided it was enough: _not stated_
- Limitation (authors): Lack of high-resolution H I mapping for IC 5332 and NGC 1365 required assuming a constant Sigma_HI = 8 M_sun pc^-2.  
  > "We lack resolved 21 cm mapping for IC 5332 and NGC 1365. Based on the observed flatness of the atomic gas surface density over the inner parts of galaxy disks... we assume that the atomic gas has a flat distribution with Sigma_HI = 8 M_sun pc^-2" (2.2 Ancillary data)
- Limitation (authors): Central saturation and artifacts from active galactic nuclei in NGC 1365 and NGC 7496 required masking.  
  > "In NGC 1365 and NGC 7496, we mask pixels in the center due to IR brightness of the active galactic nuclei (AGN), which saturate the signal mostly in the F2100W band." (2.3 Noise properties and masks)

## Reproducibility

- Data public (paper): JWST data are accessible via MAST, ALMA data via ALMA archive, and ESO MUSE data via ESO archive.  
  > "Some/all of the data presented in this paper were obtained from the Mikulski Archive for Space Telescopes (MAST) at the Space Telescope Science Institute" (Acknowledgments); "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00650.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Hand-drawn masks for central AGN diffraction spikes
- Missing: Specific scripts or routines used to compute median trends in radial and ISM parameter bins
- Data volume (inferred): 50 GB - 200 GB
- Score (inferred): 7/5, The paper uses published science products from the PHANGS-ALMA, PHANGS-MUSE, and PHANGS-JWST surveys. Key processing choices (convolution to 1'', conversion factors, S/N clipping) are documented, but some manual masking was performed by hand.
- Rediscovery candidate: no, ALMA data play a supporting role providing CO moment 0 maps for molecular gas surface densities; the primary observational advance is JWST/MIRI imaging.

## Links

- Method: (cite: Aniano2011) (Convolution kernels to match PSF resolutions)
- Method: (cite: PHANGSALMA2021Pipeline) (PHANGS-ALMA imaging and data processing pipeline)
- Companion: (cite: LEE_PHANGSJWST) (Survey overview paper for PHANGS-JWST Treasury program)
- Companion: (cite: LEROY1_PHANGSJWST) (First results and validation of MIRI band behavior in PHANGS-JWST)
- Companion: (cite: EGOROV_PHANGSJWST) (Detailed study of PAH emission and destruction within H II regions)
- Companion: (cite: CHASTENET2_PHANGSJWST) (Companion study on PAH grain size variations across the ISM)
- Related: PHANGS-JWST
- Related: PHANGS-ALMA
- Related: PHANGS-MUSE
- Related: THINGS

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 52,
 "quote_pass_rate": 0.839,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 9,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2018.A.00062.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 38,
  "rate": 0.458
 },
 "evidence_ok": false
}
```
