# The solar chromosphere at millimetre and ultraviolet wavelengths. I. Radiation temperatures and a detailed comparison

`2019A&A...622A.150J` | Astronomy and Astrophysics 2019 | first author: Jafarzadeh, S. | arXiv: 1901.05763 | DOI: 10.1051/0004-6361/201834205

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: sun
- Question: How do chromospheric radiation temperatures from ALMA Band 6 (1.3 mm) compare with those from IRIS UV lines in regions of different magnetic field strength?  
  > "The present work provides distributions of the radiation temperature at various chromospheric heights sampled by the ALMA 1.3 mm passband and the IRIS observations at near- and far-UV wavelengths" (Introduction)
- Target **Solar active region AR 12470**: coordinates _not stated_; z/distance near disc centre, cos(heliocentric angle) ≈ 0.97  
  > "The field of view (FOV) includes the leading sunspot of the active region AR 12470 surrounded by plages and quasi-quiet[^1] areas, close to the solar disc-center (with cosine of heliocentric angle $\approx0.97$)." (2.1 Observations with ALMA); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00020.SV
- bands: Band 6 (centred at 239 GHz; 1.25 mm)  
  > "was obtained in ALMA band 6 (centred at 239 GHz; 1.25 mm) on 18 December 2015" (2.1 Observations with ALMA)
- frequencies and spectral setup: Four spectral windows of 2 GHz each, 128 channels each (TDM); SW0-SW3 at 1.303, 1.292, 1.219, 1.209 mm (230, 232, 246, 248 GHz)  
  > "Four spectral windows (sub bands), with a bandwidth of 2 GHz each, were recorded. Each spectral window (SW) includes 128 channels" (2.1 Observations with ALMA)
- continuum bandwidth: _not stated_
- arrays: Twenty-one 12 m and nine 7 m antennas plus total-power array  
  > "The data was taken using a heterogeneous array configuration consisting of twenty-one 12 m and nine 7 m antennas." (2.1 Observations with ALMA)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Beam about 2.2'' x 0.7'' (Gaussian kernel equivalent to the ALMA PSF)  
  > "equivalent to a $2.2\ensuremath{''}\times0.7\ensuremath{''}$ Gaussian kernel" (3.2 Relationships between ALMA and IRIS)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 149-point mosaic, 6.048 s integration per point  
  > "an integration time of 6.048 s for each point" (2.1 Observations with ALMA)
- observing dates: 18 December 2015, 19:39:25–20:02:34 UT  
  > "on 18 December 2015 between 19:39:25–20:02:34 UT" (2.1 Observations with ALMA)
- pi or archival as stated: _not stated_
- Other facility **IRIS**: Near/far-UV spectra (Mg II h/k, C II, O I, Si IV) in a 320-step raster  
  > "The ALMA observations were supported by the IRIS spacecraft in the “very large dense 320-step raster” mode with 2 s exposure time per step." (2.2 IRIS observations)
- Other facility **SDO (AIA, HMI)**: Co-alignment images and HMI VFISV field strength maps for region masks  
  > "We also use the results of the Milne-Eddington Stokes inversion of the HMI data with the VFISV code (cite: Borrero2011) to obtain the photospheric magnetic field strength." (2.4 SDO images)

## Processing

### Calibration

- pipeline or manual: Optimised standard pipeline (SoAP) with sub-bands and channels separated; CASA calibration, imaging, feathering with TP maps  
  > "We have optimised the standard reduction pipeline by tuning various parameters, also separating the sub-bands and the spectral channels" (2.1 Observations with ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: about 5% in brightness temperature  
  > "is the brightness temperature (with an uncertainty in the order of 5%)" (3 Analysis and results)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: ≈0.15 arcsec/pixel  
  > "with a sampling resolution of $\approx0.15$ arcsec/pixel" (2.1 Observations with ALMA)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Interferometric data feathered with total-power maps for absolute brightness temperature  
  > "The TP maps are used to derive absolute brightness temperatures for the interferometric data" (2.1 Observations with ALMA)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- CASA calibration, imaging and feathering steps for solar ALMA data  
  > "included standard CASA calibrations, imaging, and feathering steps (see (cite: Shimojo2017) for details)" (2.1 Observations with ALMA) [from Shimojo2017]
- SoAP pipeline description  
  > "The first version of this Solar ALMA Pipeline (SoAP) will be described in a forthcoming publication (cite: Szydlarski2018)." (2.1 Observations with ALMA) [from Szydlarski2018]

### Not stated but needed to reproduce (our reading)

- SoAP pipeline parameters (not yet published)
- CASA version
- Imaging weighting, deconvolver, masks
- Exact IRIS observation ID and file names
- Details of cross-correlation co-alignment
- Linear regression method used

## Analysis recipe

1. **Derive ALMA sub-band brightness temperature maps**: Pipeline reduction per spectral window, feathered with TP maps; brightness temperature used directly  
  > "Thus, it directly enters our analysis with no further processing." (3 Analysis and results)
   - software: CASA, SoAP
   - fitting: _not stated_
   - validation: _not stated_
2. **Compute IRIS line features and radiation temperatures**: Gaussian fits with MOSiC; intensity from radiometric calibration converted via inverse Planck function  
  > "We calculate the near- and far-UV radiation temperature $T_{rad}$ in the solar chromosphere at a given wavelength $\lambda$ by solving the Planck function" (3 Analysis and results)
   - software: MOSiC, IRIS radiometric calibration routine v4
   - fitting: Single then multiple Gaussians, reduced chi-square  
  > "The goodness of the fits at each step is evaluated by means of reduced chi-square statistics" (2.2 IRIS observations)
   - validation: _not stated_
3. **Define magnetic regions**: HMI VFISV field strength thresholds: umbra B≥2 kG, sunspot+pores B≥0.8 kG, penumbra 0.8–2 kG, plage 0.2–0.8 kG, quasi-quiet B<0.1 kG  
  > "0.8 kG$>B\geq0.2$ kG defining the plage areas, and $B<0.1$ kG to represent the quasi-quiet regions" (2.5 Definition of regions)
   - software: VFISV
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare Trad distributions and pixel-to-pixel relations**: Histograms per region; IRIS convolved with ALMA PSF, resampled, pixels limited to max 2 min (and 0.5 min) time difference; Pearson r, Spearman rho, linear slope, K-S test  
  > "we only include pixels, from either of the first two IRIS scans, which have a maximum observing-time difference of two minutes" (3.2 Relationships between ALMA and IRIS)
   - assumption: ALMA brightness temperature represents gas temperature (LTE, Rayleigh-Jeans)  
  > "the temperature can be simply measured under the assumption of local thermodynamic equilibrium (LTE)" (Introduction)
   - fitting: Linear regression  
  > "Furthermore, the linear regression coefficient of the linear fit $m$, which measures the steepness of a linear relationship, is calculated." (3.2 Relationships between ALMA and IRIS)
   - validation: Repeated with 0.5 min maximum time difference  
  > "we also repeated the analyses with a maximum time difference of 0.5 min" (3.2 Relationships between ALMA and IRIS)

## Software

- **CASA** : ALMA calibration, imaging, feathering  
  > "included standard CASA calibrations, imaging, and feathering steps" (2.1 Observations with ALMA)
- **SoAP** : Solar ALMA Pipeline reduction  
  > "The first version of this Solar ALMA Pipeline (SoAP) will be described in a forthcoming publication" (2.1 Observations with ALMA)
- **MOSiC** : IRIS line feature fitting  
  > "are computed with the MOSiC analysis tool (cite: Rezaei2017)" (2.2 IRIS observations)
- **VFISV** : HMI Milne-Eddington inversion for field strength  
  > "Milne-Eddington Stokes inversion of the HMI data with the VFISV code" (2.4 SDO images)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 1.3 mm mean brightness temperature, entire FOV | 6.6 | 0.5 kK (std) | kK | 4 | varies between 4.6–8.1 kK in the entire FOV with an average and standard variation of 6.6 kK and 0.5 kK |
| ALMA mean Tb in umbra | 5.6 | 0.4 kK (std) | kK | 4 | Its mean value is the smallest in the umbra ($5.6\pm0.4$ kK |
| ALMA mean Tb in plage | 7.0 | 0.4 kK (std) | kK | 4 | is the largest in the plage region ($7.0\pm0.4$ kK) |
| Fraction of FOV with time difference ≤2 min | 28 | not stated | percent | 4 | this selection limits us to only 28% of the entire FOV |

## Qualitative findings

- Splitting ALMA sub-bands resolves finer structures than averaging  
  > "spectral splitting of the ALMA observations in a particular Band (here, in Band 6) results in a slightly higher spatial resolution." (4 Summary and conclusions)

## Claim tuples

- H: Do ALMA Band 6 and IRIS Trad agree? | E: Compared histograms and K-S tests in magnetic regions | R: C II agrees best with ALMA (mean 6.6 kK each in the FOV); Mg II is lower (about 5.2–5.6 kK) | F: Only C II is compatible with ALMA; Mg II radiation temperatures are lower, likely due to non-LTE | **supported**
- H: Are UV and mm temperatures correlated pixel to pixel? | E: Scatter plots with Pearson/Spearman for pixels within 2 min and 0.5 min | R: Moderate-to-good positive correlations (0.5<r<0.9) except in umbra | F: UV and ALMA temperature variations are similar spatially, with offsets from the y=x line | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Time differences between ALMA and IRIS and few umbra pixels limit the comparison  
  > "could partly be due to a large uncertainty introduced by the very few data points entering the analysis" (4 Summary and conclusions)
- Caveat (inferred, ours): The 5% ALMA calibration uncertainty is not derived
- Caveat (inferred, ours): Non-LTE Trad vs gas temperature offsets are not modelled
- Caveat (inferred, ours): Different formation heights are not quantified

## Reproducibility

- Data public (paper): ALMA SV data cited by project code; IRIS and SDO public  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00020.SV." (Acknowledgements)
- Products in archive: _not stated_
- Missing: SoAP pipeline and its parameters
- Missing: IRIS observation IDs
- Missing: Co-alignment details
- Data volume (inferred): tens of GB (ALMA solar SV mosaic plus IRIS raster and SDO)
- Score (inferred): 3/5, Public data and a clear statistical analysis, but the pipeline is unpublished and imaging parameters are missing.
- Rediscovery candidate: no, Depends on the unpublished SoAP reduction, so the ALMA maps cannot be reproduced exactly.

## Links

- Method: Shimojo2017 (Solar ALMA calibration, imaging and feathering)
- Method: Rezaei2017 (MOSiC IRIS analysis tool)
- Method: Szydlarski2018 (SoAP pipeline)
- Companion: Bastian2017 (Earlier analysis of the same ALMA/IRIS data)
- Related: IRIS
- Related: SDO

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00020.SV"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 31,
  "rate": 0.47
 },
 "evidence_ok": true
}
```
