# Duration and properties of the embedded phase of star formation in 37 nearby galaxies from PHANGS-JWST

`2026A&A...706A.186R` | Astronomy and Astrophysics 2026 | first author: Ramambason, Lise | arXiv: 2507.01508 | DOI: 10.1051/0004-6361/202556206

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, star_formation
- Question: How long does the dust-embedded (obscured) phase of star formation last in nearby galaxies, and how do 21 micron timescales depend on galactic and GMC properties?  
  > "we extend the analysis of the embedded phase of star formation to the largest sample to date, consisting of 37 galaxies drawn from the PHANGS surveys" (Introduction)
- Target **37 PHANGS galaxies (e.g. NGC 628, NGC 1512, NGC 3351)**: coordinates _not stated_; z/distance within 23.5 Mpc  
  > "Our sample consists of 37 galaxies, drawn from the PHANGS surveys" (2.1 Sample selection); "located within 23.5 Mpc" (2.1 Sample selection); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00650.S, 2013.1.01161.S, 2015.1.00925.S, 2015.1.00956.S, 2017.1.00392.S, 2017.1.00886.L, 2018.1.01651.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m, 7-m and total power combined  
  > "we used the maps resulting from a combination of 12-m, 7-m, and total power antennas of ALMA." (2.2.1 Tracers of the molecular gas and of the exposed phase of star formation)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1'' (~25-180 pc)  
  > "The maps have a resolution of $\sim$1$''$, resulting in a physical scale of $\sim$25-180 pc for the galaxies considered here." (2.2.1 Tracers of the molecular gas and of the exposed phase of star formation)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Other facility **JWST/MIRI**: 21 micron maps at 0.67'' (PHANGS-JWST Cycles 1 and 2)  
  > "We focus on the MIRI/21 $\mu$m maps obtained at a spatial resolution of 0.67$''$" (2.2.2 21 micron as tracer of the embedded star formation)
- Other facility **PHANGS-Halpha ground-based imaging**: continuum-subtracted narrowband Halpha maps  
  > "We use the continuum-subtracted narrowband H$\alpha$ imaging from PHANGS–H$\alpha$ (Razza et al. subm.)." (2.2.1 Tracers of the molecular gas and of the exposed phase of star formation)
- Other facility **PHANGS-MUSE**: metallicity maps for 20/37 galaxies  
  > "For most of the galaxies in our sample (20/37), we have access to gas-phase metallicity estimates based on MUSE observations" (2.3.2 Metallicity)
- External data: PHANGS-ALMA CO(2-1) moment-0 maps, first public release, broad masking  
  > "We use the first public release version of moment-0 maps generated with an inclusive signal masking scheme" (2.2.1 Tracers of the molecular gas and of the exposed phase of star formation) [from (cite: Leroy_2021_phang_alma)]
- External data: metallicity-dependent Halpha reference timescale t_ref = 4.32 (Z/Zsun)^-0.086 Myr  
  > "We note that the $t_{\rm CO}$ measurements are tied to a metallicity-dependent reference timescale (duration of the isolated H$\alpha$ emission) calibrated in (cite: Haydon_2020)." (3.4 Reference timescale) [from (cite: Haydon_2020)]
- External data: total SFR maps from GALEX+WISE  
  > "we use the SFR maps from the z0mgs atlas (cite: Leroy_2019_z0mgs)" (2.3.1 Total SFR) [from (cite: Leroy_2019_z0mgs)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: PHANGS-ALMA public release products used  
  > "We use the first public release version of moment-0 maps" (2.2.1 Tracers of the molecular gas and of the exposed phase of star formation)
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
- masking: 'broad' masking scheme for moment-0 maps  
  > "the ‘broad’ masking scheme" (2.2.1 Tracers of the molecular gas and of the exposed phase of star formation)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12m+7m+TP combined  
  > "we used the maps resulting from a combination of 12-m, 7-m, and total power antennas of ALMA." (2.2.1 Tracers of the molecular gas and of the exposed phase of star formation)
- smoothing: all maps convolved to coarsest resolution (CO) following Aniano 2011, using WebbPSF kernels for 21 um  
  > "by convolving all the maps to the coarsest resolution, following (cite: Aniano_2011_convolution)" (3.1 Data homogenization)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA CO data reduction and the same CO and Halpha datasets as previous study  
  > "Data reduction is described in detail in (cite: Leroy_CO_phangs_2021)." (2.2.1 Tracers of the molecular gas and of the exposed phase of star formation) [from (cite: Leroy_CO_phangs_2021); Kim et al. 2022 (cite: Kim_2022_environmental_dep)]
- Fourier high-pass filtering of diffuse emission  
  > "we follow the methodology developed in (cite: Hygate_2019_diffuse)" (3.2 Filtering diffuse emission) [from (cite: Hygate_2019_diffuse)]
- HEISENBERG tuning-fork method and default parameters  
  > "(cite: Kruijssen_tf_2018) for the default quantities chosen to run HEISENBERG." (Table notes) [from (cite: Kruijssen_tf_2018)]

### Not stated but needed to reproduce (our reading)

- Exact versions of PHANGS-ALMA and PHANGS-JWST products
- Halpha maps are unpublished (Razza et al. subm.)
- Peak-masking thresholds beyond Table values and other HEISENBERG settings inherited from earlier work
- Details of the CLUMPFIND contour levels for Halpha

## Analysis recipe

1. **homogenize maps**: convolve to CO resolution and regrid to common pixel grid  
  > "The two maps are then reprojected to a common pixel grid using the `reproject_interp` function from `astropy`." (3.1 Data homogenization)
   - software: WebbPSF, astropy
   - assumption: ALMA PSF assumed Gaussian  
  > "which is assumed to be Gaussian" (3.1 Data homogenization)
   - fitting: _not stated_
   - validation: _not stated_
2. **mask bright peaks and centers, filter diffuse emission, identify peaks**: CLUMPFIND peaks; Gaussian high-pass Fourier filter with iterated lambda  
  > "filtering the diffuse component in Fourier space using a Gaussian high-pass filter" (3.2 Filtering diffuse emission)
   - software: CLUMPFIND
   - parameter: flux losses in compact regions < 10%  
  > "we ensure that the relative flux losses in compact regions due to the Fourier filtering are less than 10% in all three tracers" (3.2 Filtering diffuse emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **measure relative timescales**: tuning-fork fits to CO-to-21um flux ratio deviation vs aperture size, converted with reference t_CO  
  > "The resulting “tuning-fork” shape is then fitted using two functional forms (equations 81 and 82 from (cite: Kruijssen_tf_2018))" (3.4 Measuring evolutionary timescales)
   - software: HEISENBERG
   - assumption: emission follows Gaussian profile around each peak  
  > "Assuming that the emission follows a Gaussian profile centered around each of the peaks" (3.4 Measuring evolutionary timescales)
   - fitting: _not stated_
   - validation: accuracy criteria of Sect. 4.4 of Kruijssen 2018 checked  
  > "we verified that the requirements listed in Sect. 4.4 of (cite: Kruijssen_tf_2018) were fulfilled." (Accuracy of the results)
4. **correlate timescales with galaxy properties**: Spearman rank correlations with Holm-Bonferroni significance  
  > "we further determine whether these correlations are statistically significant according to the Holm-Bonferroni method" (4.2.2 Statistical framework)
   - software: SciPy
   - parameter: p_ref=0.05, N_corr=17  
  > "resulting in an estimate of N$_{\rm corr}= 17$" (4.2.2 Statistical framework)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **HEISENBERG** : convert spatial decorrelation to timescales  
  > "We then used the HEISENBERG code to convert these spatial offsets into timescales associated with 21 $\mu$m emission." (Conclusion)
- **CLUMPFIND** : peak identification  
  > "identified using the CLUMPFIND (cite: clumpfind_Williams_1994) algorithm" (3.2 Filtering diffuse emission)
- **WebbPSF** 1.2.1: JWST 21 um PSF  
  > "which uses the `WebbPSF` simulation tool (cite: Perrin_2014_webbpsf) version 1.2.1" (3.1 Data homogenization)
- **astropy** : reprojection with reproject_interp  
  > "using the `reproject_interp` function from `astropy`" (3.1 Data homogenization)
- **STARBURST99** : Halpha luminosity for sensitivity-matching check  
  > "We use the STARBURST99 model (cite: Starburst99_Leitherer_1999) to estimate H$\alpha$ luminosity" (Accuracy of the results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| median t_21um | 3.9 | +1.4/-0.9 | Myr | 3 | $t_{\rm 21~\mu m}$= $3.9^{+1.4}_{-0.9}$ Myr |
| median t_fb,21um | 3.4 | +1.5/-1.2 | Myr | 3 | $t_{\rm fb, 21~\mu m}$=$3.4^{+1.5}_{-1.2}$  Myr |
| median t_obscured | 0.8 | +1.5/-0.8 | Myr | 3 | $t_{\rm obscured}$=$0.8^{+1.5}_{-0.8}$  Myr |
| median t_CO | 13.3 | +3.3/-2.7 | Myr | 3 | $t_{\rm CO}$=$13.3^{+3.3}_{-2.7}$ Myr |
| diffuse 21um fraction range | 48-74% (median 62±4%) | ±4% | percent | 2 | in the range of $48-74$%, with a median value of $62\pm4$% |

## Qualitative findings

- Obscured phase is short (<=4 Myr) in all galaxies and <=1 Myr in 28/37  
  > "with 28/37 galaxies displaying an almost absent ($\leq$ 1 Myr) obscured star-formation phase" (4.1.2 Timescales associated with 21 um emission)

## Claim tuples

- H: The dust-embedded phase of star formation is short | E: Tuning-fork analysis of CO vs 21 um peaks in 37 galaxies | R: median t_obscured 0.8 Myr; max 4 Myr | F: obscured phase is very short | **supported**
- H: 21 um timescales depend on GMC properties | E: Spearman correlations with Holm-Bonferroni | R: moderate correlations (rho~0.5) of t_21um with GMC mass and velocity dispersion | F: longer 21 um emission in galaxies with massive clouds | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): CO resolution only allows upper limits on t_fb and t_obscured in 25/37 galaxies  
  > "for 25 out of the 37 galaxies, we derived $\lambda \leq 1.4 \times l_{\rm ap, min}$" (4.1.2 Timescales associated with 21 um emission)
- Caveat (inferred, ours): Upper limits dominate the key obscured-phase result
- Caveat (inferred, ours): Metallicity trends rest on 20 galaxies with many limits
- Caveat (inferred, ours): CO sensitivity mismatch may bias 21 um timescales long

## Reproducibility

- Data public (paper): PHANGS-ALMA first public release used; JWST data on MAST  
  > "We use the first public release version of moment-0 maps" (2.2.1 Tracers of the molecular gas and of the exposed phase of star formation)
- Products in archive: _not stated_
- Code: HEISENBERG publicly available on GitHub  
  > "which is publicly available on GitHub." (3.4 Measuring evolutionary timescales)
- Missing: Halpha maps (unpublished)
- Missing: full HEISENBERG configuration inherited from Kim et al. 2022
- Data volume (inferred): tens of GB (moment maps plus JWST images for 37 galaxies)
- Score (inferred): 3/5, Public data and code, but many inherited settings and unpublished Halpha maps.
- Rediscovery candidate: no, Depends on unpublished Halpha data and inherited configurations; ALMA role is only moment-0 maps.

## Links

- Method: (cite: Kruijssen_tf_2018) (HEISENBERG tuning-fork method)
- Method: (cite: Hygate_2019_diffuse) (diffuse emission filtering)
- Method: (cite: Leroy_2021_phang_alma) (PHANGS-ALMA survey data)
- Companion: (cite: Kim_2022_environmental_dep) (previous CO-Halpha timescales on same sample)
- Companion: (cite: Kim_pah_2025) (PAH band timescales)
- Related: PHANGS-ALMA
- Related: PHANGS-JWST
- Related: PHANGS-MUSE

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 7,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 35,
  "rate": 0.461
 },
 "evidence_ok": true
}
```
