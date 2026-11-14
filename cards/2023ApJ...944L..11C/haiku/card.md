# PHANGS-JWST First Results: Variations in PAH Fraction as a Function of ISM Phase and Metallicity

`2023ApJ...944L..11C` | The Astrophysical Journal Letters 2023 | first author: Chastenet, Jérémy | arXiv: 2301.00578 | DOI: 10.3847/2041-8213/acadd7

Card schema 1.0 | model claude-haiku-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies
- Question: How the PAH fraction, traced by R_PAH = (F770W+F1130W)/F2100W from JWST/MIRI, varies with ISM phase (Hα to HI+H2 ratio, molecular fraction), environment and metallicity across four PHANGS-JWST galaxies.  
  > "We find that H II regions traced by MUSE H$\alpha$ show a systematically low PAH fraction." (abstract)
- Target **IC 5332**: coordinates 23:34:27.488 -36:06:3.89  
  > "IC 5332 | 23:34:27.488 | -36:06:3.89 | 9.01" (Table (TabData)); z/distance 9.01 Mpc  
  > "IC 5332 | 23:34:27.488 | -36:06:3.89 | 9.01" (Table (TabData)); distance from _not stated_
- Target **NGC 628**: coordinates 01:36:41.745 +15:47:1.11  
  > "NGC 628 | 01:36:41.745 | +15:47:1.11 | 9.84" (Table (TabData)); z/distance 9.84 Mpc  
  > "NGC 628 | 01:36:41.745 | +15:47:1.11 | 9.84" (Table (TabData)); distance from _not stated_
- Target **NGC 1365**: coordinates 03:33:36.458 -36:08:26.37  
  > "NGC 1365 | 03:33:36.458 | -36:08:26.37 | 19.57" (Table (TabData)); z/distance 19.57 Mpc  
  > "NGC 1365 | 03:33:36.458 | -36:08:26.37 | 19.57" (Table (TabData)); distance from _not stated_
- Target **NGC 7496**: coordinates 23:09:47.288 -43:25:40.28  
  > "NGC 7496 | 23:09:47.288 | -43:25:40.28 | 18.72" (Table (TabData)); z/distance 18.72 Mpc  
  > "NGC 7496 | 23:09:47.288 | -43:25:40.28 | 18.72" (Table (TabData)); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00650.S, 2013.1.01161.S, 2015.1.00925.S, 2015.1.00956.S, 2017.1.00392.S, 2017.1.00766.S, 2017.1.00886.L, 2018.1.01651.S, 2018.A.00062.S
- bands: not stated for ALMA; JWST MIRI filters F770W, F1130W, F2100W  
  > "We use MIRI (cite: rieke2015) observations in the F770W, F1130W, and F2100W filters" (Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: CO (2-1) at about 1 arcsec; all maps convolved to 1 arcsec  
  > "to trace molecular gas, at" (Ancillary data); "We convolve all three filter maps to" (Data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO 12CO (2-1), broad moment 0 maps (not stated)
- Other facility **JWST/MIRI (PHANGS-JWST Treasury program #2107)**: F770W, F1130W and F2100W imaging used to build R_PAH  
  > "The data used in this paper are part of the PHANGS-JWST Treasury program #2107" (Data)
- Other facility **MUSE (PHANGS-MUSE)**: Hα maps tracing ionized gas and H II region data  
  > "from the PHANGS-MUSE survey (cite: PHANGSMUSE2022Survey) to trace ionized gas" (Ancillary data)
- Other facility **MeerKAT and THINGS**: HI maps for NGC 7496 (MeerKAT) and NGC 628 (THINGS)  
  > "We use Hi measurements from MeerKAT (C. Eibensteiner et al., in prep), at $15''$ resolution for NGC 7496, and from THINGS (cite: Walter2008) for NGC 628" (Ancillary data)
- Other facility **Spitzer**: Background anchoring of JWST data  
  > "The background removal is done by anchoring the JWST data with *Spitzer*" (Noise properties and masks)
- External data: Metallicity 2D maps (12+log(O/H)) from interpolated H II region metallicities  
  > "we use the 2D maps by (cite: Williams2022)" (Ancillary data) [from (cite: Williams2022)]
- External data: Galactic environment masks (5 categories)  
  > "identified by (cite: Querejeta2021). We use their spatial mask to separate pixels in 5 different categories" (Variation of PAH fraction with ISM environment) [from (cite: Querejeta2021)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: STScI Calibration pipeline 1.7.0 for MIRI (1.7.1 for NIRCam)  
  > "The PHANGS-JWST team used the STScI Calibration pipeline 1.7.1 for NIRCam and 1.7.0 for MIRI" (JWST/MIRI data)
- archive products used as is: PHANGS-ALMA CO moment 0 and error maps used as provided  
  > "maps and corresponding error maps from the PHANGS-ALMA survey combining 12m+7m+Total Power" (Ancillary data)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: MIRI pixel grid about 0.11 arcsec for HI reprojection  
  > "We reproject these maps to the MIRI pixel grid, with pixel size" (Ancillary data)
- image size: _not stated_
- masking: Pixels with S/N ≤ 3 removed in all MIRI bands; central AGN pixels masked in NGC 1365 and NGC 7496  
  > "We remove pixels with signal-to-noise" (Noise properties and masks); "In NGC 1365 and NGC 7496, we mask pixels in the center due to IR brightness of the active galactic nuclei" (Noise properties and masks)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: CO maps from 12m+7m+Total Power combined  
  > "combining 12m+7m+Total Power" (Ancillary data)
- smoothing: Convolution to 1 arcsec (filters, CO, Hα where coarser); kernels from WebbPSF with Aniano2011 method  
  > "The convolution kernels were computed using the theoretical PSFs of each filter provided by the WEBBPSF (cite: WebbPSF), and the method described in (cite: Aniano2011)" (Data)
- final beam: 1 arcsec  
  > "We convolve all three filter maps to $1''$ resolution" (Data)
- final rms: not stated (background noise 0.05, 0.05, 0.1 MJy/sr)  
  > "with background noise values of 0.05, 0.05, and 0.1 MJy sr" (Noise properties and masks)

### Inherited from earlier work

- Convolution kernel method for matching MIRI PSFs  
  > "and the method described in (cite: Aniano2011)" (Data) [from (cite: Aniano2011)]
- Constant CO-to-H2 conversion factor alpha_CO = 4.35 for solar metallicity, star-forming galaxies  
  > "as recommended for solar metallicity, star-forming galaxies" (Ancillary data) [from (cite: Bolatto2013)]
- CO(2-1)/CO(1-0) line ratio R21 = 0.65 and CO(2-1) conversion  
  > "line ratio $R_{21} = 0.65$" (Ancillary data) [from (cite: denBrok2021; Leroy2022)]
- Atomic gas mass from 21 cm emission, optically thin prescription  
  > "using the prescription from (cite: Leroy2012)" (Ancillary data) [from (cite: Leroy2012)]
- Flat HI distribution assumed for IC 5332 and NGC 1365  
  > "we assume that the atomic gas has a flat distribution with" (Ancillary data) [from (cite: Schruba2011; Bigiel2012; KennicuttReview; Wong2013)]
- Data reduction details, noise and background removal for JWST data  
  > "(cite: LEE_PHANGSJWST) give details of the reduction of the data, including noise." (Noise properties and masks) [from (cite: LEE_PHANGSJWST)]
- Gas-phase metallicity maps from HII regions with S-calibration and Gaussian Process Regression  
  > "The maps were created by interpolating H II regions-derived metallicity maps (with S-calibration)" (Ancillary data) [from (cite: Williams2022)]
- PHANGS-ALMA CO data products and pipeline  
  > "from the PHANGS-ALMA survey combining 12m+7m+Total Power (cite: PHANGSALMA2021Pipeline; PHANGSALMA2021Survey)" (Ancillary data) [from (cite: PHANGSALMA2021Pipeline; PHANGSALMA2021Survey)]

### Not stated but needed to reproduce (our reading)

- ALMA CO data reduction and calibration details for the PHANGS-ALMA moment maps (only cited)
- HI maps for IC 5332 and NGC 1365 (none; flat 8 Msun/pc^2 assumed, so results depend on that assumption)
- Exact MIRI background subtraction and Spitzer anchoring procedure
- Sigma_HI for NGC 628 and NGC 7496 sizes/maps used in the convolution to 1 arcsec
- Exact bin widths and bin edges for radial, Halpha-ratio and metallicity binned medians
- Treatment of error propagation for R_PAH and for the Halpha/gas ratio
- Coordinates of AGN masks and exact masked radius

## Analysis recipe

1. **match resolution of all maps**: Convolve MIRI F770W, F1130W, F2100W maps to 1 arcsec with WebbPSF-derived kernels; CO and H-alpha/metallicity maps degraded to match; HI reprojected to MIRI grid  
  > "We convolve all three filter maps to" (Data)
   - software: WebbPSF
   - parameter: 1 arcsec common resolution; MIRI pixel size about 0.11 arcsec  
  > "We reproject these maps to the MIRI pixel grid, with pixel size" (Ancillary data)
   - fitting: _not stated_
   - validation: _not stated_
2. **build the PAH fraction map**: R_PAH = (F770W+F1130W)/F2100W after removing S/N ≤ 3 pixels and masking AGN centres  
  > "We remove pixels with signal-to-noise" (Noise properties and masks)
   - parameter: S/N threshold 3 in all MIRI bands  
  > "We remove pixels with signal-to-noise" (Noise properties and masks)
   - assumption: F2100W dominated by small hot dust grains, not PAHs  
  > "We assume the F2100W filter is free from contribution from PAHs and is instead dominated by small, hot dust grains" (PAH Fraction)
   - fitting: _not stated_
   - validation: Assumption said to be validated by difference in behaviour of F2100W vs PAH bands  
  > "This assumption is validated by a clear difference in behavior between the F2100W and PAH–dominated band emission" (PAH Fraction)
3. **derive gas surface densities and ionized-to-total gas ratio**: Sigma_H2 from CO(2-1) with alpha_CO and R21; Sigma_HI from 21 cm or flat 8 Msun/pc^2; ratio of Halpha intensity to Sigma_HI+H2  
  > "We combine the Hi and H$_2$ maps to estimate the total gas surface density" (Variation of PAH fraction with ISM environment)
   - parameter: alpha_CO = 4.35 Msun/pc^2 (K km/s)^-1; R21 = 0.65; Sigma_HI = 8 Msun/pc^2 for IC 5332 and NGC 1365  
  > "we assume that the atomic gas has a flat distribution with" (Ancillary data)
   - assumption: Flat atomic gas distribution in inner disks  
  > "Based on the observed flatness of the atomic gas surface density over the inner parts of galaxy disks" (Ancillary data)
   - fitting: _not stated_
   - validation: Footnote says alpha_CO choice is not dominant uncertainty under flat HI assumption  
  > "With the assumption of a flat Hi distribution, the choice of" (Ancillary data)
4. **bin R_PAH against ISM and metallicity proxies and find thresholds**: Median R_PAH in bins of r/r25, 12+log(O/H), I_Halpha/Sigma_gas, CO fraction, and Querejeta2021 environment masks; SEM error bars  
  > "In all panels, the error bars are 3 times the standard error of the mean (SEM)" (Qualitative description)
   - parameter: Five environment categories from Querejeta2021  
  > "We use their spatial mask to separate pixels in 5 different categories" (Variation of PAH fraction with ISM environment)
   - fitting: No fit; threshold read from binned trends  
  > "The abundance of PAHs appears to stay rather flat until a threshold" (Variation of PAH fraction with ISM environment)
   - validation: _not stated_

## Software

- **WebbPSF** : Theoretical PSFs for convolution kernels and centring the F2100W PSF to mask the AGN  
  > "This is done using the WEBBPSF package (cite: WebbPSF), and centering the F2100W PSF on the central coordinates of each target." (Noise properties and masks)
- **STScI Calibration pipeline** 1.7.0 (MIRI): JWST/MIRI data calibration  
  > "The PHANGS-JWST team used the STScI Calibration pipeline 1.7.1 for NIRCam and 1.7.0 for MIRI" (JWST/MIRI data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| average R_PAH in IC 5332 | 3.3 | not stated | dimensionless | 2 | values of 3.3, 4.7, 5.1, and 3.6 in IC 5332, NGC 628, NGC 1365, and NGC 7496, respectively |
| average R_PAH in NGC 628 | 4.7 | not stated | dimensionless | 2 | values of 3.3, 4.7, 5.1, and 3.6 in IC 5332, NGC 628, NGC 1365, and NGC 7496, respectively |
| average R_PAH in NGC 1365 | 5.1 | not stated | dimensionless | 2 | values of 3.3, 4.7, 5.1, and 3.6 in IC 5332, NGC 628, NGC 1365, and NGC 7496, respectively |
| average R_PAH in NGC 7496 | 3.6 | not stated | dimensionless | 2 | values of 3.3, 4.7, 5.1, and 3.6 in IC 5332, NGC 628, NGC 1365, and NGC 7496, respectively |
| threshold of I_Halpha/Sigma_HI+H2 above which PAH fraction decreases | ~10^37.5 | not stated | erg s^-1 kpc^-2 (Msun pc^-2)^-1 | 4 | the PAH fraction decreases above a value of |
| flat HI surface density assumed for IC 5332 and NGC 1365 | 8 | not stated | Msun pc^-2 | 3 | we assume that the atomic gas has a flat distribution with |

## Qualitative findings

- R_PAH is systematically low within H II regions traced by MUSE Hα  
  > "We find that H II regions traced by MUSE H$\alpha$ show a systematically low PAH fraction." (abstract)
- PAH fraction decreases with increasing radius and lower metallicity  
  > "Radial profiles also show a decreasing PAH fraction with increasing radius, correlated with lower metallicity" (abstract)

## Claim tuples

- H: Does the PAH fraction depend on the ionized gas environment? | E: R_PAH binned against I_Halpha/Sigma_HI+H2 in four galaxies | R: R_PAH flat then decreasing above about 10^37.5 erg/s/kpc^2/(Msun/pc^2)^-1 in all four galaxies | F: PAH destruction in ionized gas operates similarly across the four targets | **partially**
- H: Does the PAH fraction correlate with metallicity? | E: Radial profiles and R_PAH versus 12+log(O/H) from Williams2022 maps | R: Average R_PAH differs between galaxies and decreases with lower metallicity | F: Offset in PAH fraction tracks global metallicity gradients | **partially**
- H: Does the PAH fraction depend on molecular gas content? | E: R_PAH versus molecular fraction traced by CO in four galaxies | R: Variations are rather small and galaxy-dependent | F: PAH abundance is not particularly sensitive to the molecular fraction compared with ionized gas | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Three-filter MIRI ratio used as a proxy for PAH fraction, with 7.7 and 11.3 micron bands over 21 micron continuum  
  > "Here, we use the JWST/MIRI $R{\rm_{PAH} = (F770W+F1130W)/F2100W}$ ratio as a proxy for the PAH fraction." (PAH Fraction)
- Alternative: Using resolved HI maps for IC 5332 and NGC 1365 rejected because none exist; flat HI assumed instead  
  > "We lack resolved 21 cm mapping for IC 5332 and NGC 1365." (Ancillary data)
- How they decided it was enough: Resolution matched to the lowest-resolution dataset (HI) so that all maps share a common beam of 1 arcsec  
  > "we choose to work at the MIRI F2100W resolution to retain as much information about the distribution of the PAH emission" (Ancillary data)
- Limitation (authors): No universal threshold can be established because similar-resolution HI is missing for IC 5332 and NGC 1365  
  > "and therefore a universal threshold across all environments is left for future studies" (Variation of PAH fraction with ISM environment)
- Limitation (authors): The sample covers a small range of metallicity  
  > "although it should be noted that the sample included in this work covers a small range of metallicity" (Variation of PAH fraction with ISM environment)
- Limitation (authors): AGN influence on the central PAH fraction is not clear  
  > "The definitive impact of AGNs on the PAH population is not yet completely clear." (Qualitative description)
- Caveat (inferred, ours): Flat HI assumption for two of four galaxies drives the gas-ratio threshold and is not tested
- Caveat (inferred, ours): Metallicity maps are interpolated, so the metallicity trend rests on a model product
- Caveat (inferred, ours): Central masks for AGN are hand-made, which may bias the radial trends in NGC 1365 and NGC 7496
- Caveat (inferred, ours): ALMA CO data are only cited and not described, so reproduction depends on external PHANGS-ALMA products
- Caveat (inferred, ours): Averages are given without uncertainties

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Paper says the specific observations can be accessed via a blank pointer; ALMA projects linked by the archive  
  > "The specific observations analyzed can be accessed via ." (Acknowledgments)
- Code: _not stated_
- Missing: Exact MIRI and CO map versions and data access path
- Missing: Background and noise-estimation procedure per target
- Missing: Flat HI treatment details and any HI maps for NGC 628 and NGC 7496 beyond the citation
- Missing: Bin definitions and error propagation
- Missing: Code for R_PAH maps and AGN masks
- Data volume (inferred): Small: a few MIRI image mosaics and CO/Hα/HI maps, likely well under 1 GB (inferred)
- Score (inferred): 3/5, Recipe is clear at the level of filters, kernels and gas conversions, but depends on unreleased HI maps, cited ALMA products and hand-made AGN masks
- Rediscovery candidate: no, Public data availability is not stated and key inputs (HI for two galaxies, metallicity maps, masks) are missing or in preparation

## Links

- Method: (cite: Aniano2011) (Convolution kernel method for matching PSFs)
- Method: (cite: Bolatto2013) (alpha_CO conversion factor)
- Method: (cite: Querejeta2021) (Environment masks used in the analysis)
- Companion: (cite: LEE_PHANGSJWST) (PHANGS-JWST data reduction and noise)
- Companion: (cite: LEROY1_PHANGSJWST) (Reference-file choice and PAH versus F2100W behaviour)
- Companion: (cite: EGOROV_PHANGSJWST) (Companion analysis of PAH within H II regions)
- Companion: (cite: CHASTENET2_PHANGSJWST) (Companion analysis of PAH grain size vs molecular gas)
- Related: PHANGS-JWST Treasury program 2107
- Related: PHANGS-ALMA
- Related: PHANGS-MUSE

## Checks

```json
{
 "quotes": 80,
 "quotes_ok": 80,
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
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 93,
  "stated": 57,
  "rate": 0.613
 },
 "evidence_ok": true
}
```

## Figures

- **Figure 1** (moment_map, 4 panel(s), data): Spatial maps of the PAH fraction R_PAH in four PHANGS galaxies (IC 5332, NGC 628, NGC 1365, NGC 7496), with contours marking bright HII regions that appear as depressions in R_PAH.
  - axes: colour: R_PAH (PAH fraction) [not labelled]; scale bar: physical scale [kpc]
  - supports step 2
  - read off the plot: approx. 5 kpc scale bar in each panel; approx. HII-region contours appear as local R_PAH depressions in NGC 628 and NGC 7496
  - reproduction target
- **Figure 2** (radial_profile, 5 panel(s), data): Running medians of R_PAH versus r/r25, metallicity 12+log(O/H), ionized-to-total gas surface density ratio, molecular gas fraction, and environmental mask categories for four galaxies.
  - axes: x: r/r25 [dimensionless]; x: 12 + log(O/H) [dex]; x: I_Halpha / Sigma_HI+H2 [erg s^-1 kpc^-2 (M_sun pc^-2)^-1]; x: Sigma_H2 / Sigma_HI+H2 [dimensionless]; x: environmental mask [categorical]; y: R_PAH [dimensionless]
  - supports step 4
  - read off the plot: approx. R_PAH about 4.5 at centre of NGC 628 and 4.9 at bar; approx. R_PAH about 1.0 at r/r25 near 0.9 in NGC 7496; approx. R_PAH about 5.5 peak in NGC 1365 at r/r25 near 0.3; approx. R_PAH about 2.5 to 3.0 for IC 5332 at r/r25 near 0.5
  - reproduction target
- **Figure 3** (scatter_or_relation, 4 panel(s), data): 2D histograms of R_PAH versus the ionized-to-total gas surface density ratio, colour-coded by metallicity, for four galaxies with running medians overlaid.
  - axes: x: I_Halpha / Sigma_HI+H2 [erg s^-1 kpc^-2 (M_sun pc^-2)^-1 (log10)]; y: R_PAH [dimensionless]; colour: metallicity 12+log(O/H) [dex]
  - supports step 4
  - read off the plot: approx. R_PAH about 4.9 peak in NGC 628 near log10 ratio 37.5; approx. R_PAH about 5.2 peak in NGC 1365 near log10 ratio 37.1; approx. log10 ratio range 36.0 to 39.0
  - reproduction target
- **Figure 4** (other, 1 panel(s), data): Maps of R_PAH for four galaxies colour-coded by Querejeta et al. (2021) environmental masks: centre, bar, interarm, spiral arms and disk.
  - axes: colour: environmental mask category [categorical]
  - supports step 4
