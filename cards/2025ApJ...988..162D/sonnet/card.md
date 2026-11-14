# Constraining Resolved Extragalactic R<SUB>21</SUB> Variation with Well-calibrated ALMA Observations

`2025ApJ...988..162D` | The Astrophysical Journal 2025 | first author: den Brok, Jakob | arXiv: 2506.09125 | DOI: 10.3847/1538-4357/addf4c

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies
- Question: How does the CO(2-1)/CO(1-0) line ratio R21 vary between and within nearby galaxies at 1.7 kpc resolution, using well calibrated ALMA data, and how does it depend on SFR surface density, radius, specific SFR and metallicity?  
  > "We investigate $\ensuremath{R_{21}}$ variation to understand its dependence on global galaxy properties, kpc-scale environmental factors, and its correlation with star formation rate (SFR) surface density and metallicity." (abstract)
- Target **14 PHANGS-ALMA galaxies (NGC 0685, 1087, 1300, 1317, 1385, 1433, 2566, 2835, 3627, 4457, 4540, 5068, 5236, 7496)**: coordinates _not stated_; z/distance 4.89-23.44 Mpc (Table 1)  
  > "Galaxy distance drawn from (cite: Anand2021)" (Table 1); "All galaxies in our sample are within a distance of $D{<}25$ Mpc" (2.1 The sample); distance from Anand2021  
  > "Galaxy distance drawn from (cite: Anand2021)" (Table 1); "All galaxies in our sample are within a distance of $D{<}25$ Mpc" (2.1 The sample)

## Data provenance

- ALMA projects: 2022.1.01479.S, 2015.1.01538.S, 2017.1.00079.S
- bands: Band 3 (CO(1-0)); PHANGS CO(2-1) in Band 6  
  > "This paper presents new Band 3 ALMA CO(1-0) observations of 12 nearby galaxies" (2.2.1)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ACA 7m + TP for CO(1-0); 12m+7m+TP for CO(2-1)  
  > "using both the total power (TP) and seven meter array (7m) portions of the Morita Atacama Compact Array (ACA)" (2.2.1); "The set of CO(2-1) observations include 12m+7m+TP ALMA data" (2.2.2)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~14'' to 15'' native for CO(1-0); common 1.7 kpc working resolution  
  > "the final observations achieved an angular resolution of approximately 14$''$ to 15$''$" (2.2.1)
- max recoverable scale: _not stated_
- sensitivity: CO(1-0) 1 to 16 mK at 2.5 km/s channels at 1.7 kpc; CO(2-1) <4 mK  
  > "At 1.7 kpc angular resolution, the sensitivity ranges from 1 to 16 mK" (2.2.1)
- time on source: _not stated_
- observing dates: September 2022 to November 2023  
  > "All observations were carried out between September 2022 and November 2023." (2.2.1)
- pi or archival as stated: New Cycle 9 PI program (den Brok) plus archival NGC 3627, NGC 5236 and PHANGS-ALMA CO(2-1)  
  > "we include two more archival ALMA CO(1-0) mapping observations: NGC3627 (cite: denBrok2023b) and NGC5236 (cite: Koda2023)" (1 Introduction)
- Line: CO J=1-0 (115.271 GHz)
- Line: CO J=2-1 (230.5 GHz)
- Other facility **Hα narrowband (du Pont 2.5 m, ESO/MPG 2.2 m) and WISE**: SFR surface density  
  > "we use a combination of narrowband H$\alpha$ and Wide-field Infrared Survey Explorer (WISE) 22 $\mu$m data" (2.3.1)
- Other facility **Spitzer IRAC 3.6 micron**: stellar mass surface density  
  > "estimated using Spitzer IRAC 3.6$\mu$m near-infrared maps" (2.3.1)
- Other facility **PHANGS-MUSE**: metallicity maps for 8 galaxies  
  > "For 8 of our 14 targets, we use metallicity measurements obtained from PHANGS-MUSE observations" (2.3.2)
- External data: PHANGS-ALMA CO(2-1) 12m+7m+TP data cubes (team version 4)  
  > "We use first public release (team version 4) of the PHANGS-ALMA data products" (2.2.2) [from (cite: Leroy2021)]
- External data: Galaxy orientation, distances, integrated SFR and stellar mass  
  > "The galaxy integrated SFR and stellar mass are adopted from (cite: Leroy2022)." (Table 1) [from Lang2020; Anand2021; Leroy2022]
- External data: Metallicity maps  
  > "We specifically use the metallicity maps from (cite: Williams2022)." (2.3.2) [from (cite: Williams2022)]
- External data: Radially varying alpha_CO prescription for KS analysis  
  > "we use a radially varying CO-to-H$_2$ conversion factor based on the prescription from (cite: Bolatto2013) and computed for the galaxies in our sample by (cite: Sun2022)." (5.1) [from (cite: Sun2022)]

## Processing

### Calibration

- pipeline or manual: Observatory pipeline, no manual flagging  
  > "Our quality assurance did not reveal any issues with the pipeline, and the data did not require any manual flagging." (2.2.1)
- casa version: CASA v6.4.1  
  > "which used CASA (v6.4.1) and the ALMA calibration pipeline" (2.2.1)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~5% adopted conservatively  
  > "Therefore, we infer a conservative estimate of a ${\sim}5\%$ flux calibration uncertainty for the ALMA data." (2.2.3)
- self calibration: _not stated_

### Imaging

- task: PHANGS-ALMA imaging pipeline v3.1 with CASA tclean; feather for short-spacing combination  
  > "short-spacing correction using CASA’s `feather` task, and finally convolution of the channels to a common, circularized beam" (2.2.1)
- deconvolver: multi-scale clean to ~4σ then single-scale to ~1σ in regions with signal  
  > "The routine performs a multi-scale cleaning down to ${\sim}4\sigma$ followed by a single-scale cleaning down to ${\sim}1\sigma$ focused on regions with detected signal." (2.2.1)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: zeroth-order polynomial  
  > "the continuum is subtracted using a zeroth-order polynomial" (2.2.1)
- line free channels: _not stated_
- primary beam correction: applied in pipeline post-processing  
  > "which include primary-beam correction, conversion of the cube units to brightness temperature expressed in Kelvin" (2.2.1)
- array combination: 7m+TP feathered; CO(2-1) 12m+7m+TP  
  > "we use the 12m+7m+TP products and convolve them to our working resolution" (2.2.2)
- smoothing: Gaussian convolution to 1.7 kpc, hexagonal half-beam regridding  
  > "we convolve the cubes to a common physical resolution of 1.7 kpc using a Gaussian beamsize and regrid to a hexagonal grid" (2.4 Homogenizing and processing the data)
- final beam: _not stated_
- final rms: CO(1-0) 1-16 mK per 2.5 km/s channel at working resolution  
  > "At 1.7 kpc angular resolution, the sensitivity ranges from 1 to 16 mK" (2.2.1)

### Inherited from earlier work

- Imaging pipeline details  
  > "For a detailed description of the pipeline’s functionalities and methods, we refer to the dedicated paper (cite: Leroy2021)" (2.2.1) [from (cite: Leroy2021); Appendix A of (cite: Liu2023)]
- Signal mask construction and moment uncertainties  
  > "The signal mask over the entire cube is then determined using a method adapted from (cite: Leroy2021)." (2.4) [from (cite: Leroy2021)]
- Aperture correction method  
  > "To quantify the corresponding *aperture* correction we follow the approach outlined in (cite: Leroy2021)." (2.4) [from (cite: Leroy2021)]
- SFR calibration  
  > "follows the new calibration presented in (cite: Belfiore2023)" (2.3.1) [from (cite: Belfiore2023)]
- Stellar mass surface density method  
  > "We refer to (cite: Leroy2021_PHANGS) for a detailed description of the approach used to estimate the stellar mass surface density." (2.3.1) [from (cite: Leroy2021_PHANGS)]
- Spectral stacking method  
  > "The spectral stacking method resembles the one detailed in (cite: Schruba2011)" (3.2) [from (cite: Schruba2011); (cite: Neumann2023_stacking)]
- Ratio-of-sums definition  
  > "following definition in (cite: Leroy2022)" (3.2) [from (cite: Leroy2022)]

### Not stated but needed to reproduce (our reading)

- Exact bin edges and bin widths for r_gal, SFR surface density, sSFR and metallicity
- Regression method for binned fits and how the uncertainties on m and q were derived
- Details of the fit to all sightlines (slope 0.11) and treatment of uncertainties
- Spectral setup, channel width and line-free channels for the CO(1-0) cubes
- Robust weighting, cell size and image size used by the PHANGS pipeline
- Exact definitions of the arm/interarm environments
- Specific PHANGS-ALMA CO(2-1) project codes per galaxy and CO(1-0) per-galaxy execution details
- Hα data are from an unpublished work (Razza et al. in preparation)

## Analysis recipe

1. **Image the calibrated ALMA CO(1-0) 7m+TP data**: PHANGS-ALMA imaging pipeline: channel regridding, continuum subtraction, tclean, primary beam correction, feather with TP, convolution to circular beam  
  > "We used the PHANGS-ALMA pipeline[^2] to image the calibrated data and produce science-ready data cubes." (2.2.1)
   - software: CASA, tclean, feather, PHANGS-ALMA pipeline
   - parameter: multi-scale clean to ~4σ, then single-scale to ~1σ  
  > "The routine performs a multi-scale cleaning down to ${\sim}4\sigma$ followed by a single-scale cleaning down to ${\sim}1\sigma$" (2.2.1)
   - fitting: _not stated_
   - validation: _not stated_
2. **Homogenize cubes and maps to common 1.7 kpc hexagonal grid**: Convolve to 1.7 kpc, regrid onto half-beam spaced hexagonal grid, deproject with PA, inclination and distance  
  > "The points of the resulting grid are half-beam spaced in a hexagonal pattern." (2.4)
   - software: PyStructure, astropy
   - parameter: 1.7 kpc working resolution  
  > "we convolve the cubes to a common physical resolution of 1.7 kpc" (2.4)
   - fitting: _not stated_
   - validation: _not stated_
3. **Build signal masks and compute moment maps**: Mask from the CO(2-1) prior line: 4σ seed, expanded into 2σ mask, extended 10 km/s along velocity; rms via mad_std x1.4826; moments computed  
  > "Then the pipeline first selects all voxels that satisfies the high ($4\sigma$) S/N threshold." (2.4)
   - software: PyStructure, astropy
   - parameter: 4σ high, 2σ low, +10 km/s  
  > "Finally, the signal mask is extended along the velocity axis by another 10 km s$^{-1}$." (2.4)
   - fitting: _not stated_
   - validation: Completeness of S/N>5 mask vs full map: median 98% CO(1-0), 96% CO(2-1)  
  > "We find a median completeness of the ALMA data across the sample of 98% for CO(1-0) and 96% for CO(2-1)" (3.1)
4. **Measure R21 per sightline and averages**: R21 = W_CO(2-1)/W_CO(1-0) for S/N>5 sightlines; average via area-weighted median, ratio-of-sums, and spectrally stacked ratio  
  > "we include those sightlines for which both the CO(1-0) and CO(2-1) integrated intensities exceed a S/N${>}$5." (3.1)
   - software: PyStructure, PyStacker
   - parameter: 5% flux calibration uncertainty included in Gaussian error propagation  
  > "which incorporates the channel rms and a flux calibration uncertainty of 5%" (3.1)
   - fitting: _not stated_
   - validation: Compared survey permutations (COMING, EMPIRE, NROATLAS, HERACLES, PHANGS, ALMA)  
  > "we present the distribution of line ratio values per sightline for different combinations of surveys" (4.3)
5. **Bin R21 and fit scaling relations**: Bin by r_gal, Σ_SFR, sSFR, metallicity; linear (radius, metallicity) or power-law (SFR, sSFR) regression to binned values; Kendall tau  
  > "we fit a regression line to the equally weighted binned means. For the regression line, we either assume a linear relation (galactocentric radius) or a power-law" (4.1.2)
   - fitting: Linear regression y = m x + q to binned values; no sampler or priors stated  
  > "We fit a linear regression of the form $y = mx+q$." (Table 3)
   - validation: Compared single, broken and two-component power laws via reduced chi2  
  > "the simple power law prescription is used." (Appendix: Comparing different R21 Fitting Prescriptions)
6. **Assess impact of R21 on KS relation and depletion time**: Compare KS index and depletion time from CO(1-0) vs CO(2-1) with fixed R21  
  > "we fit the relation to the same points when using the CO(2-1) measurements and a fixed $R_{21}$." (5.1)
   - assumption: Radially varying alpha_CO (Bolatto2013/Sun2022); alpha_CO(1-0)=4.35 for sensitivity estimate  
  > "we use a radially varying CO-to-H$_2$ conversion factor based on the prescription from (cite: Bolatto2013)" (5.1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 6.4.1: calibration pipeline and imaging (tclean, feather)  
  > "which used CASA (v6.4.1) and the ALMA calibration pipeline" (2.2.1)
- **PHANGS-ALMA pipeline** v3.1: imaging and cube production  
  > "We used the PHANGS-ALMA pipeline[^2] to image the calibrated data" (2.2.1)
- **PyStructure** v3.0.1: convolution, hexagonal regridding, deprojection, moment maps  
  > "We use the publicly available `PyStructure` pipeline[^4]" (2.4)
- **PyStacker** : spectral stacking  
  > "We use the tool `PyStacker`[^6] to perform the spectral stacking." (3.2)
- **astropy** : mad_std noise estimation  
  > "using the `mad_std` function from `astropy`" (2.4)
- **numpy** : general computation (listed)  
  > "numpy (cite: harris2020array)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Sample-wide resolved median R21 | 0.64 | +0.16/-0.14 (16-84th percentile) | dimensionless | 4 | $\langle \ensuremath{R_{21}}\rangle=0.64^{+0.16}_{-0.14}$ |
| Ratio-of-sums R21 | 0.70 | ±0.05 | dimensionless | 4 | $\langle \ensuremath{R_{21}}\rangle_{\Sigma}=0.70^{+0.05}_{-0.05}$ |
| Stacked R21 | 0.71 | ±0.05 | dimensionless | 4 | $\langle \ensuremath{R_{21}}\rangle_{\rm stacked}=0.71^{+0.05}_{-0.05}$ |
| Central (r<=2 kpc) R21 | 0.75 | +0.09/-0.12 | dimensionless | 4 | $\langle \ensuremath{R_{21}}\rangle_{\rm center}=0.75^{+0.09}_{-0.12}$ |
| Galaxy-to-galaxy scatter (ALMA) vs single-dish | 0.05 dex vs 0.11 dex | not stated | dex | 5 | we find a scatter of 0.05 dex for our ALMA-based observations vs. 0.11 dex for the single-dish sample |
| Slope of log R21 vs log Σ_SFR (binned medians) | 0.12 | +0.03/-0.04 | dimensionless | 5 | a slope of $m{=}0.12^{+0.03}_{-0.04}$ or $m{=}0.10^{+0.02}_{-0.02}$ |
| Slope of log R21 vs log sSFR (binned) | 0.14 | ±0.03 | dimensionless | 5 | yields a slope of $m{=}0.14^{+0.03}_{-0.03}$ |
| Radial slope of R21 (median) | -0.017 | +0.006/-0.01 | per kpc | 5 | $-0.017^{+0.006}_{-0.01}$ |
| Metallicity slope | -1.1 | +0.8/-0.6 | dimensionless | 5 | yields a negative slope of $m=-1.1^{+0.8}_{-0.6}$ |
| KS index change CO(1-0) to CO(2-1), all sightlines | 0.80 to 0.78 | not stated | dimensionless | 6 | the KS index only changes by $-2\%$, from $N_{10}{=}0.80$ to $N_{21}{=}0.78$ |
| R21 vs stellar mass relation | log R21 = -0.07 log M* + 0.57 | ±0.02 (slope), ±0.09 (intercept) | dimensionless | 5 | -0.07{\pm}0.02 \log_{10}\left(\frac{M_*^{\rm gal}}{M_\odot}\right) + 0.57{\pm}0.09 |

## Qualitative findings

- R21 increases toward centers in several galaxies (5/14 visually); within-galaxy variation exceeds galaxy-to-galaxy scatter  
  > "5/14 sources show a clear increase of the line ratio towards the center" (4.2)
- Mixing facilities changes mean R21 by 10-20%, comparable to physical range  
  > "this telescope-dependent variation is on a similar magnitude (i.e., 10%–20%) to the overall dynamical range" (4.3)

## Claim tuples

- H: Previously reported galaxy-to-galaxy R21 scatter is inflated by single-dish flux calibration | E: Compute R21 from all-ALMA CO(1-0) and CO(2-1) for 14 galaxies and compare scatter with single-dish samples | R: Scatter about the fitted relation 0.05 dex vs 0.11 dex for single-dish | F: Calibration uncertainties dominate the earlier scatter | **supported**
- H: R21 correlates with local conditions such as Σ_SFR | E: Bin and fit sightlines against Σ_SFR, sSFR, radius, metallicity | R: Σ_SFR power-law slope 0.10-0.12; Kendall tau ~1 | F: Σ_SFR is the best predictor | **supported**
- H: A fixed R21 biases kpc-scale gas scaling relations | E: Compare KS index and depletion time from CO(1-0) vs CO(2-1) with fixed R21 | R: KS index changes by -2% overall; <10% for most galaxies | F: Fixed R21=0.64 does not significantly bias samples | **supported**

## Reasoning

- Why this data: ALMA is the only facility with sufficient sensitivity and low calibration uncertainty  
  > "Currently, the interferometer ALMA is the only facility that can provide the the high sensitivity and low calibration uncertainty that are crucial for such a study." (1 Introduction)
- Why this method: CO(2-1) used as prior line for masks due to higher S/N  
  > "we select the CO(2-1) emission line due to its higher S/N than the CO(1-0)" (2.4)
- Alternative: Broken and two-component power laws not adopted because the improvement was insignificant given limited Σ_SFR range  
  > "the statistical improvement (in terms of reduced $\chi^2$) is insignificant." (Appendix: Comparing different R21 Fitting Prescriptions)
- How they decided it was enough: _not stated_
- Limitation (authors): Small sample; individual outliers can affect galaxy-to-galaxy trends  
  > "Given the small number of galaxies within our sample, we caution, however, that individual outliers can affect the observed trends." (4.1.1)
- Limitation (authors): Metallicity covers only ~0.25 dex and 8 galaxies  
  > "we only cover a small dynamical range of metallicities (${\sim}$0.25 dex)" (4.1.2)
- Caveat (inferred, ours): Fits to binned medians with few bins give Kendall tau of exactly 1 or -1, so significance is overstated
- Caveat (inferred, ours): Sample of 14 is a pilot, and selection and field of view may bias the central/disk results
- Caveat (inferred, ours): Flux uncertainty of 5% is adopted from literature, not measured for these data
- Caveat (inferred, ours): Uncertainty on regression parameters is not described

## Reproducibility

- Data public (paper): Archival ALMA data with project codes listed; PyStructure and pipeline are public  
  > "We use the publicly available `PyStructure` pipeline[^4]" (2.4)
- Products in archive: _not stated_
- Code: PyStructure, PyStacker and the PHANGS imaging scripts are on GitHub  
  > "v3.1; <https://github.com/akleroy/phangs_imaging_scripts>" (Footnote 2)
- Missing: Bin definitions and regression implementation
- Missing: Hα maps are unpublished
- Missing: Per-galaxy CO(1-0) imaging parameters
- Data volume (inferred): ~100s GB to ~1 TB (12 ACA 7m+TP CO(1-0) datasets plus PHANGS CO(2-1) products)
- Score (inferred): 3/5, Data and code public, but binning and fitting details and some ancillary data are incompletely specified.
- Rediscovery candidate: no, Analysis depends on heavy pipeline processing and several ancillary maps (some unpublished), with binning details unstated.

## Links

- Method: (cite: Leroy2021) (PHANGS-ALMA imaging pipeline and masking)
- Method: (cite: Neumann2023_stacking) (spectral stacking of interferometric data)
- Companion: (cite: Leroy2021_PHANGS) (PHANGS-ALMA CO(2-1) survey data)
- Companion: (cite: denBrok2021) (earlier single-dish R21 study)
- Companion: (cite: Leroy2022) (single-dish R21 comparison sample and scaling relation)
- Related: PHANGS-ALMA
- Related: PHANGS-MUSE
- Related: HERACLES
- Related: EMPIRE
- Related: COMING
- Related: NROATLAS

## Checks

```json
{
 "quotes": 86,
 "quotes_ok": 86,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00650.S",
  "2013.1.01161.S",
  "2015.1.00121.S",
  "2015.1.00925.S",
  "2015.1.00956.S",
  "2016.1.00386.S",
  "2017.1.00392.S",
  "2017.1.00886.L",
  "2018.1.01321.S",
  "2018.1.01651.S",
  "2019.2.00129.S"
 ],
 "codes_printed_but_missing": [
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
  "2018.1.01321.S",
  "2018.1.01651.S",
  "2018.A.00062.S",
  "2019.1.01235.S",
  "2019.2.00129.S"
 ],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 92,
  "stated": 63,
  "rate": 0.685
 },
 "evidence_ok": true
}
```
