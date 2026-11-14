# PHANGS-JWST First Results: Variations in PAH Fraction as a Function of ISM Phase and Metallicity

`2023ApJ...944L..11C` | The Astrophysical Journal Letters 2023 | first author: Chastenet, Jérémy | arXiv: 2301.00578 | DOI: 10.3847/2041-8213/acadd7

Card schema 1.0 | model claude-opus-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, milky_way_ism
- Question: How does the PAH fraction, traced by (F770W+F1130W)/F2100W, vary with ISM phase, galactic environment, radius and metallicity in four nearby galaxies?  
  > "In this Letter, we investigate the variations of the PAH fraction traced by a combination of JWST/MIRI filters across the full disk of four nearby galaxies, IC 5332, NGC 628, NGC 1365, and NGC 7496." (Introduction)
- Target **IC 5332**: coordinates 23:34:27.488 -36:06:3.89  
  > "IC 5332 | $23:34:27.488$ | $-36:06:3.89$ | 9.01" (Table 1); z/distance 9.01 Mpc  
  > "IC 5332 | $23:34:27.488$ | $-36:06:3.89$ | 9.01" (Table 1); distance from _not stated_
- Target **NGC 628**: coordinates 01:36:41.745 +15:47:1.11  
  > "NGC 628 | $01:36:41.745$ | $+15:47:1.11$ | 9.84" (Table 1); z/distance 9.84 Mpc  
  > "NGC 628 | $01:36:41.745$ | $+15:47:1.11$ | 9.84" (Table 1); distance from _not stated_
- Target **NGC 1365**: coordinates 03:33:36.458 -36:08:26.37  
  > "NGC 1365 | $03:33:36.458$ | $-36:08:26.37$ | 19.57" (Table 1); z/distance 19.57 Mpc  
  > "NGC 1365 | $03:33:36.458$ | $-36:08:26.37$ | 19.57" (Table 1); distance from _not stated_
- Target **NGC 7496**: coordinates 23:09:47.288 -43:25:40.28  
  > "NGC 7496 | $23:09:47.288$ | $-43:25:40.28$ | 18.72" (Table 1); z/distance 18.72 Mpc  
  > "NGC 7496 | $23:09:47.288$ | $-43:25:40.28$ | 18.72" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00650.S, 2013.1.01161.S, 2015.1.00925.S, 2015.1.00956.S, 2017.1.00392.S, 2017.1.00766.S, 2017.1.00886.L, 2018.1.01651.S, 2018.A.00062.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m+7m+Total Power (PHANGS-ALMA)  
  > "from the PHANGS-ALMA survey combining ${\rm 12m+7m+Total~Power}$" (Ancillary data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1'' (~40-90 pc)  
  > "to trace molecular gas, at $\sim 1''$ ($\sim 40 - 90$ pc in our sample) resolution" (Ancillary data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PHANGS-ALMA survey data products (moment 0 maps)  
  > "“broad” moment 0 maps and corresponding error maps from the PHANGS-ALMA survey" (Ancillary data)
- Line: 12CO 2-1 (not stated)
- Other facility **JWST/MIRI**: F770W, F1130W, F2100W maps (PHANGS-JWST #2107)  
  > "We use MIRI (cite: rieke2015) observations in the F770W, F1130W, and F2100W filters" (JWST/MIRI data)
- Other facility **VLT/MUSE (PHANGS-MUSE)**: Hα maps tracing ionized gas  
  > "We use H$\alpha$ maps from the PHANGS-MUSE survey (cite: PHANGSMUSE2022Survey) to trace ionized gas." (Ancillary data)
- Other facility **MeerKAT**: HI for NGC 7496 at 15''  
  > "We use Hi measurements from MeerKAT (C. Eibensteiner et al., in prep), at $15''$ resolution for NGC 7496" (Ancillary data)
- Other facility **THINGS (VLA)**: HI for NGC 628 (~11'')  
  > "and from THINGS (cite: Walter2008) for NGC 628 ($\sim 11''$ for the ‘natural’ weighted map)" (Ancillary data)
- Other facility **Spitzer**: background anchoring of JWST data  
  > "The background removal is done by anchoring the JWST data with *Spitzer*" (Noise properties and masks)
- External data: 2D 12+log(O/H) metallicity maps (S-calibration, Gaussian Process Regression)  
  > "To trace the ${\rm 12+log(O/H)}$ metallicity in our targets, we use the 2D maps by (cite: Williams2022)." (Ancillary data) [from (cite: Williams2022)]
- External data: Galactic environment masks (5 categories)  
  > "We use their spatial mask to separate pixels in 5 different categories (see their Table 1)." (Variation of PAH fraction with ISM environment) [from (cite: Querejeta2021)]
- External data: HII region catalog contours  
  > "The white contours show the brightest H II regions (cite: GROVES_HIICAT; PHANGSMUSE2022HII)." (Qualitative description) [from (cite: GROVES_HIICAT; PHANGSMUSE2022HII)]
- External data: CO-to-H2 factor alpha_CO = 4.35  
  > "we use a constant CO-to-H$_2$ conversion factor $\alpha_{\rm CO} = 4.35$ M$_\odot$ pc$^{-2}$ (K km s$^{-1})^{-1}$ as recommended for solar metallicity, star-forming galaxies (cite: Bolatto2013)" (Ancillary data) [from (cite: Bolatto2013)]
- External data: CO(2-1)/CO(1-0) ratio R21 = 0.65  
  > "a $^{12}\mathrm{CO}(2-1)/^{12}\mathrm{CO}(1-0)$ line ratio $R_{21} = 0.65$ (cite: denBrok2021; Leroy2022)" (Ancillary data) [from (cite: denBrok2021; Leroy2022)]

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
- smoothing: all maps convolved to 1'' resolution, reprojected to MIRI ~0.11'' grid  
  > "We convolve all three filter maps to $1''$ resolution" (JWST/MIRI data); "We reproject these maps to the MIRI pixel grid, with pixel size $\sim 0.11''$." (Ancillary data)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- MIRI data reduction and noise/background handling  
  > "(cite: LEE_PHANGSJWST) give details of the reduction of the data, including noise." (Noise properties and masks) [from (cite: LEE_PHANGSJWST) and (cite: LEROY1_PHANGSJWST)]
- CO moment-0 map processing via PHANGS-ALMA pipeline  
  > "from the PHANGS-ALMA survey combining ${\rm 12m+7m+Total~Power}$ (cite: PHANGSALMA2021Pipeline; PHANGSALMA2021Survey)" (Ancillary data) [from (cite: PHANGSALMA2021Pipeline; PHANGSALMA2021Survey)]
- Convolution kernel method  
  > "and the method described in (cite: Aniano2011)" (JWST/MIRI data) [from (cite: Aniano2011)]
- HI conversion to surface density including helium  
  > "using the prescription from (cite: Leroy2012)" (Ancillary data) [from (cite: Leroy2012)]

### Not stated but needed to reproduce (our reading)

- Exact PHANGS-ALMA data release version and whether CO moment-0 maps were convolved from native to exactly 1''
- Treatment of CO non-detections / masked pixels in 'broad' moment maps
- Bin definitions in r/r25, metallicity, I_Hα/Σgas and molecular fraction
- Source of distances, P.A., inclination and r25
- Coordinates/shape of hand-drawn AGN artifact masks
- Hα extinction correction (if any)

## Analysis recipe

1. **Match resolution and grids**: Convolve MIRI, CO, Hα, metallicity maps to 1'' with WebbPSF-based kernels; reproject to MIRI grid  
  > "The convolution kernels were computed using the theoretical PSFs of each filter provided by the WEBBPSF (cite: WebbPSF), and the method described in (cite: Aniano2011)." (JWST/MIRI data)
   - software: WebbPSF
   - parameter: 1'' target resolution  
  > "We convolve all three filter maps to $1''$ resolution" (JWST/MIRI data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Mask low S/N and AGN pixels**: Remove pixels with S/N ≤ 3 in any MIRI band; mask AGN with F2100W PSF and by hand  
  > "We remove pixels with signal-to-noise ${\rm S/N \leq 3}$ in all MIRI bands, with background noise values of 0.05, 0.05, and 0.1 MJy sr$^{-1}$." (Noise properties and masks)
   - software: WebbPSF
   - assumption: NGC 7496 noise applies to all galaxies  
  > "We find that MIRI maps have similar noise, and we assume NGC 7496 estimates throughout the sample." (Noise properties and masks)
   - fitting: _not stated_
   - validation: _not stated_
3. **Build gas surface density maps**: CO(2-1) to Σ_H2 with alpha_CO and R21; HI to Σ_HI; flat Σ_HI where no HI maps  
  > "we assume that the atomic gas has a flat distribution with ${\rm \Sigma_{H{\sc I}} = 8~M_\odot~pc^{-2}}$ (including helium)" (Ancillary data)
   - parameter: alpha_CO = 4.35, R21 = 0.65  
  > "line ratio $R_{21} = 0.65$ (cite: denBrok2021; Leroy2022)" (Ancillary data)
   - assumption: optically thin 21 cm emission  
  > "assuming optically thin 21 cm emission" (Ancillary data)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compute R_PAH and compare with environment**: R_PAH=(F770W+F1130W)/F2100W; radial, metallicity, I_Hα/Σgas, molecular fraction and environment-mask profiles with 3×SEM error bars  
  > "In all panels, the error bars are 3 times the standard error of the mean (SEM)." (Qualitative description)
   - assumption: F2100W free of PAH contribution  
  > "We assume the F2100W filter is free from contribution from PAHs and is instead dominated by small, hot dust grains" (PAH Fraction)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **STScI JWST Calibration pipeline** 1.7.0 (MIRI): MIRI data reduction  
  > "The PHANGS-JWST team used the STScI Calibration pipeline 1.7.1 for NIRCam and 1.7.0 for MIRI" (JWST/MIRI data)
- **WebbPSF** : PSFs for convolution kernels and AGN masking  
  > "This is done using the WEBBPSF package (cite: WebbPSF), and centering the F2100W PSF on the central coordinates of each target." (Noise properties and masks)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| mean R_PAH IC 5332 | 3.3 | 16-84th perc. 1.8-4.8 | dimensionless | 4 | We find average $R{\rm_{PAH} = (F770W+F1130W)/F2100W}$ values of 3.3, 4.7, 5.1, and 3.6 in IC 5332, NGC 628, NGC 1365, and NGC 7496, respectively. |
| mean R_PAH NGC 628 | 4.7 | 16-84th perc. 3.8-5.6 | dimensionless | 4 | NGC 628 / $01:36:41.745$ / $+15:47:1.11$ / 9.84 / 20.7 / 8.9 / 4.94 / 4.7 / $3.8 - 5.6$ |
| mean R_PAH NGC 1365 | 5.1 | 16-84th perc. 3.8-6.3 | dimensionless | 4 | NGC 1365 / $03:33:36.458$ / $-36:08:26.37$ / 19.57 / 201.1 / 55.4 / 6.01 / 5.1 / $3.8 - 6.3$ |
| mean R_PAH NGC 7496 | 3.6 | 16-84th perc. 1.8-5.3 | dimensionless | 4 | NGC 7496 / $23:09:47.288$ / $-43:25:40.28$ / 18.72 / 193.7 / 35.9 / 1.67 / 3.6 / $1.8 - 5.3$ |
| I_Hα/Σ_HI+H2 threshold for PAH fraction decrease | ~10^37.5 | not stated | erg s^-1 kpc^-2 (M_sun pc^-2)^-1 | 4 | find that the PAH fraction decreases above a value of ${\rm I_{H\alpha}/\Sigma_{H{\sc I}+H_2}}~\sim~10^{37.5}~{\rm erg~s^{-1}~kpc^{-2}~(M_\odot~pc^{-2}})^{-1}$, in all four galaxies |

## Qualitative findings

- HII regions show systematically low PAH fraction  
  > "We find that H II regions traced by MUSE H$\alpha$ show a systematically low PAH fraction." (abstract)
- R_PAH weakly sensitive to molecular fraction  
  > "This could suggest that the abundance of PAHs is not particularly sensitive to the molecular fraction, compared to the ionized gas content." (Variation of PAH fraction with ISM environment)
- R_PAH highest in bar and interarm regions  
  > "Here, we can see that $R_{\rm PAH}$ is the highest in the bar, and interarm regions, with lower values in the spiral arms, followed by the center and finally in the disk." (Variation of PAH fraction with ISM environment)

## Claim tuples

- H: PAHs are destroyed in ionized-gas dominated regions | E: R_PAH vs I_Hα/Σ_HI+H2 binned per galaxy | R: flat until ~10^37.5 then steep decline in all four galaxies | F: PAH destruction in ionized gas operates similarly across targets | **supported**
- H: PAH fraction depends on metallicity | E: Radial and metallicity profiles; 2D histograms colored by metallicity | R: R_PAH decreases with radius; inter-galaxy offsets track average metallicity but no local gradient | F: global metallicity, not local variations, sets offset | **partially**
- H: PAH fraction correlates with molecular gas fraction (CO) | E: R_PAH vs molecular-to-total gas fraction from PHANGS-ALMA CO | R: varied behaviors, small variations | F: PAH abundance not particularly sensitive to molecular fraction | **partially**

## Reasoning

- Why this data: 1'' chosen to boost F2100W S/N and match CO/Hα resolution  
  > "We choose to slightly degrade the data to increase the signal-to-noise (S/N) in the F2100W band. By doing so, we are also able to match the resolution of the CO and H$\alpha$ data" (JWST/MIRI data)
- Why this method: F770W+F1130W over F2100W improves on Spitzer 8/24 μm PAH tracer and removes radiation field dependence  
  > "As both the PAH features and the 21 $\mu$m continuum are from stochastic heating, using these fluxes to determine the PAH fraction removes any significant dependence on the radiation field (cite: DL2007)." (PAH Fraction)
- Alternative: Voronoi binning deferred to future work  
  > "It will also be possible to test a Voronoï binning, to check whether the trends seen in Figure [2](#FigMediansPanel) would be significantly pulled down by taking into account more low-S/N pixels." (Variation of PAH fraction with ISM environment)
- How they decided it was enough: _not stated_
- Limitation (authors): No resolved HI for IC 5332 and NGC 1365; universal threshold left to future  
  > "there are (currently) no similar resolution Hi data for IC 5332 and NGC 1365, and therefore a universal threshold across all environments is left for future studies" (Variation of PAH fraction with ISM environment)
- Limitation (authors): Small metallicity range  
  > "although it should be noted that the sample included in this work covers a small range of metallicity" (Variation of PAH fraction with ISM environment)
- Limitation (authors): AGN impact uncertain  
  > "it is as of yet uncertain how the presence of an AGN may be related to this decrease" (Qualitative description)
- Caveat (inferred, ours): Threshold of 10^37.5 is by eye, no fit or uncertainty
- Caveat (inferred, ours): HI resolution (11-15'') much coarser than 1'' analysis; flat HI assumption for two galaxies
- Caveat (inferred, ours): Constant alpha_CO despite metallicity gradients
- Caveat (inferred, ours): S/N>3 cut in F2100W may bias trends toward bright regions

## Reproducibility

- Data public (paper): MIRI data from MAST; ALMA project codes listed  
  > "Some/all of the data presented in this paper were obtained from the Mikulski Archive for Space Telescopes (MAST)" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Binning scheme and environment-mask versions
- Missing: Hand-drawn AGN artifact masks
- Missing: MeerKAT HI maps (in prep)
- Missing: PHANGS-ALMA product version
- Data volume (inferred): Small: a few GB of public moment-0, MIRI, MUSE and HI image products for four galaxies
- Score (inferred): 3/5, Simple ratio maps from public products, but binning, masks and unpublished HI data are not fully specified
- Rediscovery candidate: no, Main ALMA role is ancillary; key threshold is qualitative and MeerKAT HI is unpublished

## Links

- Method: (cite: Aniano2011) (convolution kernels)
- Method: (cite: PHANGSALMA2021Pipeline) (CO map processing)
- Method: (cite: Leroy2012) (HI conversion prescription)
- Companion: (cite: LEE_PHANGSJWST) (PHANGS-JWST survey and data reduction)
- Companion: (cite: LEROY1_PHANGSJWST) (PHANGS-JWST first results; F2100W vs PAH behavior)
- Companion: (cite: EGOROV_PHANGSJWST) (PAH in HII regions)
- Companion: (cite: CHASTENET2_PHANGSJWST) (PAH grain size vs molecular gas)
- Related: PHANGS-JWST
- Related: PHANGS-ALMA
- Related: PHANGS-MUSE
- Related: THINGS
- Related: SINGS

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
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
  "facts": 92,
  "stated": 48,
  "rate": 0.522
 },
 "evidence_ok": true
}
```
