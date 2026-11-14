# PHANGS-JWST First Results: Variations in PAH Fraction as a Function of ISM Phase and Metallicity

`2023ApJ...944L..11C` | The Astrophysical Journal Letters 2023 | first author: Chastenet, Jérémy | arXiv: 2301.00578 | DOI: 10.3847/2041-8213/acadd7

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, milky_way_ism
- Question: How does the PAH fraction, traced by R_PAH=(F770W+F1130W)/F2100W from JWST/MIRI, vary with ISM phase, environment and metallicity in four nearby galaxies?  
  > "We present maps tracing the fraction of dust in the form of polycyclic aromatic hydrocarbons (PAHs) in IC 5332, NGC 628, NGC 1365, and NGC 7496 from JWST/MIRI observations." (abstract)
- Target **IC 5332**: coordinates 23:34:27.488 -36:06:3.89  
  > "| IC 5332 | $23:34:27.488$ | $-36:06:3.89$ | 9.01 | 74.4 | 26.9 | 3.03 | 3.3 | $1.8 - 4.8$ |" (Table 1); z/distance 9.01 Mpc  
  > "| IC 5332 | $23:34:27.488$ | $-36:06:3.89$ | 9.01 | 74.4 | 26.9 | 3.03 | 3.3 | $1.8 - 4.8$ |" (Table 1); distance from _not stated_
- Target **NGC 628**: coordinates 01:36:41.745 +15:47:1.11  
  > "| NGC 628 | $01:36:41.745$ | $+15:47:1.11$ | 9.84 | 20.7 | 8.9 | 4.94 | 4.7 | $3.8 - 5.6$ |" (Table 1); z/distance 9.84 Mpc  
  > "| NGC 628 | $01:36:41.745$ | $+15:47:1.11$ | 9.84 | 20.7 | 8.9 | 4.94 | 4.7 | $3.8 - 5.6$ |" (Table 1); distance from _not stated_
- Target **NGC 1365**: coordinates 03:33:36.458 -36:08:26.37  
  > "| NGC 1365 | $03:33:36.458$ | $-36:08:26.37$ | 19.57 | 201.1 | 55.4 | 6.01 | 5.1 | $3.8 - 6.3$ |" (Table 1); z/distance 19.57 Mpc  
  > "| NGC 1365 | $03:33:36.458$ | $-36:08:26.37$ | 19.57 | 201.1 | 55.4 | 6.01 | 5.1 | $3.8 - 6.3$ |" (Table 1); distance from _not stated_
- Target **NGC 7496**: coordinates 23:09:47.288 -43:25:40.28  
  > "| NGC 7496 | $23:09:47.288$ | $-43:25:40.28$ | 18.72 | 193.7 | 35.9 | 1.67 | 3.6 | $1.8 - 5.3$ |" (Table 1); z/distance 18.72 Mpc  
  > "| NGC 7496 | $23:09:47.288$ | $-43:25:40.28$ | 18.72 | 193.7 | 35.9 | 1.67 | 3.6 | $1.8 - 5.3$ |" (Table 1); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00650.S, 2013.1.01161.S, 2015.1.00925.S, 2015.1.00956.S, 2017.1.00392.S, 2017.1.00766.S, 2017.1.00886.L, 2018.1.01651.S, 2018.A.00062.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m+7m+Total Power  
  > "combining ${\rm 12m+7m+Total~Power}$" (2.2 Ancillary data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1'' (~40-90 pc)  
  > "at $\sim 1''$ ($\sim 40 - 90$ pc in our sample) resolution" (2.2 Ancillary data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO 2-1 (not stated)
- Other facility **JWST/MIRI**: F770W, F1130W, F2100W maps (PHANGS-JWST program 2107)  
  > "We use MIRI (cite: rieke2015) observations in the F770W, F1130W, and F2100W filters" (2.1 JWST/MIRI data)
- Other facility **VLT/MUSE (PHANGS-MUSE)**: Halpha maps  
  > "We use H$\alpha$ maps from the PHANGS-MUSE survey (cite: PHANGSMUSE2022Survey) to trace ionized gas." (2.2 Ancillary data)
- Other facility **MeerKAT / THINGS**: HI maps for NGC 7496 and NGC 628  
  > "We use Hi measurements from MeerKAT (C. Eibensteiner et al., in prep), at $15''$ resolution for NGC 7496, and from THINGS (cite: Walter2008) for NGC 628" (2.2 Ancillary data)
- External data: PHANGS-ALMA CO(2-1) broad moment 0 and error maps  
  > "from the PHANGS-ALMA survey combining ${\rm 12m+7m+Total~Power}$ (cite: PHANGSALMA2021Pipeline; PHANGSALMA2021Survey)" (2.2 Ancillary data) [from (cite: PHANGSALMA2021Pipeline; PHANGSALMA2021Survey)]
- External data: 2D metallicity maps  
  > "we use the 2D maps by (cite: Williams2022)" (2.2 Ancillary data) [from (cite: Williams2022)]
- External data: Environment masks  
  > "We use their spatial mask to separate pixels in 5 different categories (see their Table 1)." (3.2 Variation of PAH fraction with ISM environment) [from (cite: Querejeta2021)]

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
- smoothing: MIRI maps convolved to 1'' to match CO and Halpha  
  > "We convolve all three filter maps to $1''$ resolution, which is larger than the full-width at half-maximum of the F2100W filter ($0.67''$)." (2.1 JWST/MIRI data)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- CO-to-H2 conversion factor and R21 ratio  
  > "$^{12}\mathrm{CO}(2-1)/^{12}\mathrm{CO}(1-0)$ line ratio $R_{21} = 0.65$ (cite: denBrok2021; Leroy2022)" (2.2 Ancillary data) [from (cite: denBrok2021; Leroy2022)]
- JWST data reduction  
  > "(cite: LEE_PHANGSJWST) give details of the reduction of the data, including noise." (2.3 Noise properties and masks) [from (cite: LEE_PHANGSJWST)]

### Not stated but needed to reproduce (our reading)

- Exact PHANGS-ALMA product versions and which project codes map to which galaxy
- Binning of R_PAH profiles (bin widths in r/r25 and Halpha/gas)
- Convolution of CO to exactly 1'' details
- Halpha intensity units conversion

## Analysis recipe

1. **Build R_PAH maps**: Convolve MIRI maps to 1'', mask S/N<=3, compute (F770W+F1130W)/F2100W  
  > "we use the JWST/MIRI $R{\rm_{PAH} = (F770W+F1130W)/F2100W}$ ratio as a proxy for the PAH fraction" (3 PAH Fraction)
   - software: WebbPSF
   - parameter: background noise 0.05, 0.05, 0.1 MJy/sr  
  > "with background noise values of 0.05, 0.05, and 0.1 MJy sr$^{-1}$" (2.3 Noise properties and masks)
   - assumption: F2100W free of PAH contribution  
  > "We assume the F2100W filter is free from contribution from PAHs and is instead dominated by small, hot dust grains" (3 PAH Fraction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive gas surface densities**: CO to H2 with alpha_CO and R21; HI from maps or flat 8 Msun/pc2  
  > "we assume that the atomic gas has a flat distribution with ${\rm \Sigma_{H{\sc I}} = 8~M_\odot~pc^{-2}}$ (including helium)." (2.2 Ancillary data)
   - parameter: alpha_CO = 4.35, R21 = 0.65  
  > "$\alpha_{\rm CO} = 4.35$ M$_\odot$ pc$^{-2}$ (K km s$^{-1})^{-1}$" (2.2 Ancillary data)
   - fitting: _not stated_
   - validation: _not stated_
3. **Trends of R_PAH with environment**: Median R_PAH in bins of r/r25, metallicity, Halpha/(HI+H2), molecular fraction and Querejeta environments; errors 3 SEM  
  > "In all panels, the error bars are 3 times the standard error of the mean (SEM)." (3.1 Qualitative description)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **WebbPSF** : theoretical PSFs for convolution kernels and AGN masking  
  > "The convolution kernels were computed using the theoretical PSFs of each filter provided by the WEBBPSF" (2.1 JWST/MIRI data)
- **STScI Calibration pipeline** 1.7.0 (MIRI): JWST reduction  
  > "The PHANGS-JWST team used the STScI Calibration pipeline 1.7.1 for NIRCam and 1.7.0 for MIRI" (2.1 JWST/MIRI data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean R_PAH IC 5332 | 3.3 | 16-84th perc. 1.8-4.8 | dimensionless | 3 | / IC 5332 / $23:34:27.488$ / $-36:06:3.89$ / 9.01 / 74.4 / 26.9 / 3.03 / 3.3 / $1.8 - 4.8$ / |
| Mean R_PAH NGC 628 | 4.7 | 16-84th perc. 3.8-5.6 | dimensionless | 3 | / NGC 628 / $01:36:41.745$ / $+15:47:1.11$ / 9.84 / 20.7 / 8.9 / 4.94 / 4.7 / $3.8 - 5.6$ / |
| Mean R_PAH NGC 1365 | 5.1 | 16-84th perc. 3.8-6.3 | dimensionless | 3 | / NGC 1365 / $03:33:36.458$ / $-36:08:26.37$ / 19.57 / 201.1 / 55.4 / 6.01 / 5.1 / $3.8 - 6.3$ / |
| Mean R_PAH NGC 7496 | 3.6 | 16-84th perc. 1.8-5.3 | dimensionless | 3 | / NGC 7496 / $23:09:47.288$ / $-43:25:40.28$ / 18.72 / 193.7 / 35.9 / 1.67 / 3.6 / $1.8 - 5.3$ / |
| Threshold Halpha/Sigma_gas where R_PAH decreases | ~10^37.5 | not stated | erg s^-1 kpc^-2 (Msun pc^-2)^-1 | 3 | the PAH fraction decreases above a value of ${\rm I_{H\alpha}/\Sigma_{H{\sc I}+H_2}}~\sim~10^{37.5} |

## Qualitative findings

- R_PAH is systematically low in HII regions and decreases with radius, correlating with metallicity  
  > "We find that H II regions traced by MUSE H$\alpha$ show a systematically low PAH fraction." (abstract)

## Claim tuples

- H: PAH fraction drops in strongly ionized gas at a common threshold | E: R_PAH versus Halpha/(HI+H2) in four galaxies | R: flat then steep decrease near 10^37.5 in all four | F: PAH destruction in ionized gas operates similarly across targets | **supported**
- H: PAH fraction depends on metallicity | E: Radial profiles and metallicity maps | R: R_PAH decreases with radius, with lower metallicity | F: consistent with previous metallicity dependence | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): No resolved HI for IC 5332 and NGC 1365, so a universal threshold is left for future work; small metallicity range  
  > "there are (currently) no similar resolution Hi data for IC 5332 and NGC 1365, and therefore a universal threshold across all environments is left for future studies." (3.2 Variation of PAH fraction with ISM environment)
- Caveat (inferred, ours): Flat HI assumption for two galaxies drives the threshold comparison
- Caveat (inferred, ours): Noise from NGC 7496 assumed for all galaxies
- Caveat (inferred, ours): Manual masking of AGN artifacts

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Binning details
- Missing: Reduced JWST maps not given with versions
- Missing: Masking by hand details
- Data volume (inferred): ~tens of GB (PHANGS-ALMA moment maps are small; JWST maps are from MAST)
- Score (inferred): 3/5, Recipe is simple ratio maps, but bins and some data products are unspecified; ALMA role is only ancillary.
- Rediscovery candidate: no, ALMA is a minor ancillary input and the key JWST data processing is inherited from other papers.

## Links

- Method: (cite: LEE_PHANGSJWST) (PHANGS-JWST data reduction)
- Method: (cite: PHANGSALMA2021Pipeline) (PHANGS-ALMA pipeline)
- Companion: (cite: EGOROV_PHANGSJWST) (PAH fraction within HII regions)
- Companion: (cite: LEROY1_PHANGSJWST) (PHANGS-JWST first results on PAH and CO)
- Related: PHANGS-ALMA
- Related: PHANGS-JWST
- Related: PHANGS-MUSE

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
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
  "facts": 76,
  "stated": 30,
  "rate": 0.395
 },
 "evidence_ok": true
}
```
