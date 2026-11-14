# Calculated brightness temperatures of solar structures compared with ALMA and Metsähovi measurements

`2024AN....34530149M` | Astronomische Nachrichten 2024 | first author: Matković, Filip | arXiv: 2402.18978 | DOI: 10.1002/asna.20230149

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type theory_or_simulation_compared_to_alma

## Science

- Fields: sun
- Question: Which semiempirical atmosphere model (AL or ATLCW) better reproduces ALMA and Metsähovi mm brightness temperatures of the quiet Sun, and what density and temperature scaling of the ATLCW model fits the quiet Sun, an active region and a coronal hole  
  > "The main idea of this work is to compare the predictions of AL and ATLCW models with QS measurements from ALMA and Metsähovi observatories" (Introduction); "Then, the better model (in our case ATLCW model) is modified to fit the observations of three different solar regions (QS, AR, and CH) returning their estimated electron temperatures and densities." (Introduction)
- Target **Quiet Sun (QS) region at the centre of the solar disc**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **Active region (AR) near the centre of the solar disc, sunspots excluded**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **Southern polar coronal hole (CH)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00020.SV
- bands: Band 3 (2.80 mm) full-disc map, new analysis; Band 6 (1.21 mm) measurements taken from Brajša et al. (cite: Brajsa2018b); Band 7 (0.86 mm) and Band 5 (1.50 mm) QS values from Alissandrakis et al.  
  > "by including an analysis of the same solar structures in the Band 3 ALMA full-disc map" (Observational results / ALMA data); "the results of the first analysis of solar structures in the Band 6 full-disc ALMA image" (Observational results / ALMA data); "In addition to the ALMA Band 3 and Band 6 measurements, we also included the observational results of Alissandrakis et al." (Observational results / ALMA data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: single-dish full-disc ALMA maps  
  > "a comparison between the results of single-dish (as in this work) and interferometric observations could be useful" (Discussion and conclusions)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 3 beam size = 58 arcsec; Band 6 beam size = 26 arcsec; Metsähovi 60, 72 and 144 arcsec  
  > "beam size = 58 arcsec" (Observational results / ALMA data); "beam size = 26 arcsec" (Observational results / ALMA data); "at 3.40 mm (beam size = 60 arcsec), 3.90 mm (beam size = 72 arcsec), and 8.10 mm (beam size = 144 arcsec)" (Observational results / Metsähovi data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Band 3: December 17, 2015; Band 6: December 18, 2015  
  > "taken on the previous day, December 17, 2015." (Observational results / ALMA data); "for December 18, 2015 are given in Table 1 in that paper." (Observational results / ALMA data)
- pi or archival as stated: _not stated_
- Other facility **Metsähovi 14-m radio telescope**: Full-disc Sun brightness temperatures at 3.40, 3.90 and 8.10 mm extending the ALMA wavelength range  
  > "we extend the currently observed ALMA wavelength range to longer wavelengths by including observations from the Metsähovi 14-m diameter radio telescope" (Observational results / Metsähovi data); "we use full-disc Metsähovi observations of the mentioned solar structures at 3.40 mm" (Observational results / Metsähovi data)
- External data: Band 6 (1.21 mm) QS, AR and CH brightness temperatures for 2015-12-18  
  > "for December 18, 2015 are given in Table 1 in that paper." (Observational results / ALMA data); "These results are repeated here in Table" (Observational results / ALMA data) [from Brajša et al. (cite: Brajsa2018b)]
- External data: Band 7 (0.86 mm) and Band 5 (1.50 mm) QS brightness temperatures (corrigendum values with Gaunt factor frequency variation)  
  > "Here we use the brightness temperature values from the corrigendum" (Observational results / ALMA data); "The results for Band 5 and 7, available only for QS" (Observational results / ALMA data) [from Alissandrakis et al. (cite: Alissandrakis2023)]
- External data: Metsähovi QS brightness temperatures at 3.40 and 3.90 mm (1994-1995 observations)  
  > "Urpo et al." (Table 1) [from Urpo et al. (cite: Urpo1997)]
- External data: Metsähovi QS brightness temperature at 8.10 mm (2018 observations)  
  > "Kallunki & Tornikoski" (Table 1) [from Kallunki & Tornikoski (cite: Kallunki2018)]
- External data: Compiled older QS brightness temperature observations, used for comparison only  
  > "Other earlier and much older observational results for the QS compiled by Loukitcheva et al." (Modeling results / Quiet sun) [from Loukitcheva et al. (cite: Loukitcheva2004); Benz (cite: Benz2009)]
- Simulation/model as data: ATLCW semiempirical QS atmosphere model (electron density and temperature versus height) used as reference and input model  
  > "The starting point is the semiempirical ATLCW model of the QS atmosphere, giving density and temperature as a function of height." (Introduction)
- Simulation/model as data: Older AL QS model computed for comparison  
  > "the older original AL QS model (black dashed curve)" (Modeling results / Quiet sun)

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
- cell size: Band 3 full-disc map pixel = 6 arcsec on the Sun  
  > "The size of a single pixel of the Band 3 full-disc map is 6 arcsec on the Sun." (Observational results / ALMA data)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Band 3: 58 arcsec; Band 6: 26 arcsec  
  > "beam size = 58 arcsec" (Observational results / ALMA data); "beam size = 26 arcsec" (Observational results / ALMA data)
- final rms: _not stated_

### Inherited from earlier work

- Procedure for measuring Band 3 brightness temperatures of QS, AR and CH follows the Band 6 analysis  
  > "Following the procedure described in Brajša et al." (Observational results / ALMA data) [from Brajša et al. (cite: Brajsa2018b)]
- Brightness temperature calculation procedure is similar to the earlier FAL-based work, with a different atmosphere model and Gaunt factor  
  > "We note that the calculation procedure in the present work is similar to that used by Brajša et al." (Models / Obtaining theoretical models) [from Brajša et al. (cite: Brajsa2018a)]
- Gaunt factor computed with the van Hoof et al. interpolation method as implemented in earlier solar work  
  > "implemented in the solar context by Simões et al." (Models) [from van Hoof et al. (cite: vanHoof2014); Simões et al. (cite: Simoes2017); Selhorst et al. (cite: Selhorst2019)]
- Bremsstrahlung optical depth expression for solar abundances  
  > "neglecting the magnetic field is given by (e.g., Benz" (Models) [from Benz (cite: Benz2002)]
- Range of the density factor for CH models based on a published hybrid network corona model  
  > "chosen based on the hybrid network model of Gabriel" (Modeling results / Coronal hole) [from Gabriel (cite: Gabriel1992)]
- Measurement errors of ALMA and Metsähovi data adopted from earlier work  
  > "These measurement errors are estimated to be about 5%$-$10%" (Modeling results / Quiet sun) [from Shimojo et al. (cite: Shimojo2017); White et al. (cite: White2017)]

### Not stated but needed to reproduce (our reading)

- Which ALMA SV data product (file, execution block, calibration/reduction version) the Band 3 full-disc map of 2015-12-17 is, and how it was reduced and flux calibrated
- Pixel positions of the QS, AR and CH regions used for averaging in the Band 3 map
- The numerical brightness temperature threshold that defines the AR
- The per-point brightness temperature uncertainties actually used in chi2 (the paper gives only a general 5-10%)
- The ATLCW QS model height grid and Te, ne values (from Avrett et al. 2015) and the implementation of the van Hoof Gaunt factor
- Search grid steps and algorithm for the (f_n, f_T) minimisation
- Details of the limb brightening correction and of the Metsähovi map reduction (data values are only tabulated)
- Heights used for the AR range are inconsistent in the text (minimum 400 km, maximum 57 km) versus Table 3 (400-57797 km)

## Analysis recipe

1. **measure Band 3 brightness temperatures of QS, AR and CH**: Average pixels in the Band 3 full-disc map: QS within ~15 pixel radius at disc centre; CH within 10 pixel radius away from the limb; AR from all pixels above a brightness threshold so sunspots are excluded; non-QS structures compared with QS at the same radial distance for limb brightening  
  > "by averaging the values of all pixels within a radius of about 15 pixels." (Observational results / ALMA data); "The brightness temperature is then averaged over all pixels brighter than this threshold." (Observational results / ALMA data); "Limb brightening was taken into account by comparing the brightness temperature measurements of each non-QS structure with the brightness temperature values averaged over a 10-pixel radius QS region located at the same radial distance from the solar center" (Observational results / ALMA data)
   - parameter: Band 3 pixel size 6 arcsec; QS radius ~15 pixels; CH radius 10 pixels  
  > "The size of a single pixel of the Band 3 full-disc map is 6 arcsec on the Sun." (Observational results / ALMA data); "within an area of a radius of 10 pixels within the visible CH structure" (Observational results / ALMA data)
   - assumption: Limb brightening correction applied to measured brightness temperatures before the modelling  
  > "we applied the limb brightening correction to the measured brightness temperatures before the modeling was done." (Observational results / ALMA data)
   - fitting: _not stated_
   - validation: _not stated_
2. **assemble multi-wavelength brightness temperature table**: Combine the new Band 3 values with Band 6 values from Brajša et al. (2018b), Band 5 and 7 QS values from Alissandrakis et al. (2023) and Metsähovi values at 3.40, 3.90 and 8.10 mm  
  > "The Metsähovi results for the brightness temperature were obtained using a similar procedure as described for ALMA, but with the limb brightening effect already accounted for" (Observational results / Metsähovi data); "The results for Band 5 and 7, available only for QS" (Observational results / ALMA data)
   - fitting: _not stated_
   - validation: _not stated_
3. **compute model brightness temperature versus wavelength**: Integrate thermal bremsstrahlung radiative transfer through the ATLCW QS model (Tb = integral of Te exp(-tau) dtau) over the structure's height range, per wavelength; Gaunt factor from van Hoof et al. interpolation; model density and temperature scaled by factors f_n and f_T within the structure height range  
  > "These contributions are integrated over all heights defined for a given solar structure, yielding the total brightness temperature for a given wavelength" (Models / Obtaining theoretical models); "the Gaunt factor for the observed frequency is calculated using the accurate interpolation method recently developed by van Hoof et al." (Models); "The model is modified only in the height range defined for a given solar structure." (Models / Obtaining theoretical models)
   - parameter: AR modified from 400 km to the model top; CH from 2 km to the model top; QS over the entire model height range  
  > "For ARs, we assumed a minimum height of 400 km and a maximum of 57 km (maximum height value available in the ATLCW QS model)." (Models / Obtaining theoretical models); "For QS on the other hand, the entire height range from the photosphere to the maximum available height in the ATLCW QS model was considered." (Models / Obtaining theoretical models)
   - assumption: Thermal bremsstrahlung is the dominant emission mechanism; Rayleigh-Jeans approximation; solar abundances; magnetic field neglected  
  > "Then the radiation mechanism is chosen, in this case thermal bremsstrahlung, and the radiative transfer equation is numerically solved for each input model." (Introduction); "neglecting the magnetic field is given by (e.g., Benz" (Models)
   - fitting: _not stated_
   - validation: _not stated_
4. **fit density and temperature scaling factors by chi-squared minimisation**: Vary f_n and f_T, recompute the profile for each pair, and take the global chi2 minimum over all observed wavelengths; AR and CH fitted with two measurement procedures (a: Delta Tb added to measured central QS; b: Delta Tb added to original ATLCW QS profile); CH fitted in three cases of f_T freedom  
  > "for each pair of the two multiplicative factors the brightness temperature calculation is repeated until the global minimum of Equation" (Models / Fitting theoretical models); "In the first procedure, which corresponds to the actual measurement, the brightness temperature of AR is determined by adding the difference" (Modeling results / Active region); "while in the second procedure, the difference" (Modeling results / Active region); "Here we investigate three cases, in which the same" (Modeling results / Coronal hole)
   - parameter: Range over which f_n and f_T are varied is set so the model matches observations in the height range  
  > "The range of values within which the two multiplicative factors are varied" (Models / Fitting theoretical models)
   - assumption: For CH, f_T range is wide in case 1, restricted near 1 in case 2 and fixed to 1 in case 3; coronal temperature changes do not affect optically thin coronal emission  
  > "As the coronal radiation is optically thin, a change in coronal temperature would not result in a significant change in brightness temperature." (Modeling results / Coronal hole)
   - fitting: Standard chi2 minimisation over (f_n, f_T); 1 sigma uncertainties from Delta chi2 = 1 above the minimum; sampler and priors not stated  
  > "The best-fitting brightness temperature profile minimizes the above sum." (Models / Fitting theoretical models); "where the $\chi^2$ value reaches $\Delta\chi^2=1$ above the minimum" (Models / Fitting theoretical models)
   - validation: Procedures a and b used to test whether small changes in the measurements change the output profile  
  > "This approach was chosen to investigate whether a small change in the measurements would lead to a significant change in the output brightness temperature profile." (Modeling results / Active region)
5. **compare fitted structures with earlier results**: Compare best-fit AR and CH densities and temperatures with earlier model/observational studies and the earlier FAL-based modelling  
  > "Furthermore, we compare the current modeling results based on the modified ATLCW model presented in this work with earlier efforts by Brajša et al." (Discussion and conclusions)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Band 3 (2.80 mm) brightness temperature of central QS | 7114 | not stated | K | 1 | ALMA / 2015-12-17 / 2.80/107 / 58 / 7114 / 7114 / $0$ |
| Band 3 (2.80 mm) brightness temperature of AR and difference from QS | 7928 (Delta Tb +625) | not stated | K | 1 | 2015-12-17 / 2.80/107 / 58 / 7303 / 7928 / $+625$ |
| Band 3 (2.80 mm) brightness temperature of CH and difference from QS | 7398 (Delta Tb -145) | not stated | K | 1 | 2015-12-17 / 2.80/107 / 58 / 7543 / 7398 / $-145$ |
| Metsähovi 8.10 mm brightness temperature of AR and difference from QS | 8580 (Delta Tb +480) | not stated | K | 2 | 2015-12-19 / 8.10/37 / 144 / 8100 / 8580 / $+480$ |
| Metsähovi 8.10 mm brightness temperature of CH and difference from QS | 8020 (Delta Tb -80) | not stated | K | 2 | 2015-12-19 / 8.10/37 / 144 / 8100 / 8020 / $-80$ |
| QS best-fit density factor f_n (QS_best) | 1.13 | +0.14/-0.13 | dimensionless | 4 | $1.13^{+0.14}_{-0.13}$; the QS density is 13% higher than the value predicted by the original ATLCW model |
| QS best-fit temperature factor f_T (QS_best) | 0.99 | +0.02/-0.02 | dimensionless | 4 | $0.99^{+0.02}_{-0.02}$; factor differs from unity by only 1% |
| QS chi2_min | 1.19 | not stated | dimensionless | 4 | $1.19$ |
| AR best-fit density factor f_n, procedure a (AR_best) | 1.09 | +0.18/-0.16 | dimensionless | 4 | $1.09^{+0.18}_{-0.16}$ |
| AR best-fit temperature factor f_T, procedure a (AR_best) | 1.10 | +0.04/-0.03 | dimensionless | 4 | $1.10^{+0.04}_{-0.03}$ |
| AR best-fit density factor f_n, procedure b | 1.13 | +0.17/-0.16 | dimensionless | 4 | $1.13^{+0.17}_{-0.16}$ |
| AR best-fit temperature factor f_T, procedure b | 1.09 | +0.03/-0.04 | dimensionless | 4 | $1.09^{+0.03}_{-0.04}$ |
| AR density and temperature relative to QS (procedures a, b) | density 9%-13% higher; temperature 9%-10% higher | not stated | percent | 4 | the density of the AR is 9%$-$13% higher than the QS level; the temperature of AR is 9%$-$10% higher than that of QS |
| CH1_best density factor f_n, procedure a | 1/1.34 | +1.34/-0.33 on the 1.34 | dimensionless | 4 | $1/\left(1.34^{+1.34}_{-0.33}\right)$ |
| CH1_best density factor f_n, procedure b | 1/1.67 | +3.84/-0.75 on the 1.67 | dimensionless | 4 | $1/\left(1.67^{+3.84}_{-0.75}\right)$ |
| CH density relative to QS across the three CH cases | 1-1.7 times lower | not stated | dimensionless | 4 | give a CH density 1$-$1.7 times lower than the QS value |

## Qualitative findings

- The original ATLCW QS model reproduces ALMA and Metsähovi QS observations over the whole ALMA wavelength range, while the AL model departs from them beyond about 2 mm  
  > "We see that the original ATLCW QS model (black solid curve) reproduces well the ALMA and Metsähovi observations over the entire ALMA wavelength range." (Modeling results / Quiet sun); "differs significantly from both the measurements and the profile from the original ATLCW QS model already after a wavelength of 2 mm." (Modeling results / Quiet sun)
- AR measurements and fitted profiles lie significantly above the original ATLCW QS profile  
  > "both the observations and the AR profiles lie significantly higher than the brightness temperature profile for the original ATLCW QS model" (Modeling results / Active region)
- CH is slightly darker than the surrounding QS at ALMA wavelengths  
  > "indicating that CH is slightly darker than the surrounding QS atmosphere in the ALMA wavelength range." (Modeling results / Coronal hole)

## Claim tuples

- H: The newer ATLCW QS atmosphere model describes mm brightness temperatures better than the older AL model | E: Computed Tb(lambda) from both models with thermal bremsstrahlung and compared with ALMA and Metsähovi QS measurements | R: ATLCW matches the measurements over the ALMA range; AL differs significantly beyond about 2 mm | F: ATLCW is the better reference model | **supported**
- H: The ATLCW QS model needs modification to fit the QS data | E: chi2 fit of f_n and f_T to QS ALMA and Metsähovi measurements | R: f_T = 0.99 and f_n = 1.13 with no significant change in the profile | F: No additional modification of the ATLCW QS model is needed | **supported**
- H: ARs have higher density and temperature than the QS | E: Fit f_n and f_T of the ATLCW model to Band 3, Band 6 and Metsähovi AR measurements (two procedures) | R: AR density 9%-13% and temperature 9%-10% higher than QS | F: AR brightness is mainly due to enhanced density, with somewhat higher temperature | **supported**
- H: CH brightness temperature depends on electron density rather than temperature | E: Fit f_n and f_T to CH measurements in three cases of f_T freedom, with procedures a and b | R: All three cases give similar CH profiles despite different f_n and f_T; CH slightly less dense than QS | F: CH brightness temperature is set by density, not temperature, though constraints are weak with three wavelengths | **partially**

## Reasoning

- Why this data: Metsähovi data added because ALMA solar observations above 3 mm were unavailable  
  > "Due to the current unavailability of the ALMA measurements above the wavelength of 3 mm, we are missing a large part of the mm range reachable for ALMA" (Observational results / Metsähovi data)
- Why this method: ALMA observations used to discriminate between semiempirical models and assess physical parameters of solar structures  
  > "ALMA observations provide a good basis for discrimination between various models and assessment of physical parameters of solar structures." (Introduction)
- Alternative: AR and CH brightness fitted with two measurement procedures (a, b) to test sensitivity to small changes in the measurements; CH fitted in three f_T cases  
  > "This approach was chosen to investigate whether a small change in the measurements would lead to a significant change in the output brightness temperature profile." (Modeling results / Active region); "Here we investigate three cases, in which the same" (Modeling results / Coronal hole)
- How they decided it was enough: Model modified iteratively until best agreement with measured brightness temperatures  
  > "The cycle is repeated until the best correspondence between calculated and measured brightness temperatures is reached." (Introduction)
- Limitation (authors): Only three observed wavelengths for AR and CH  
  > "It should be noted that for structures other than QS we had only three observed wavelengths on which to base our analysis and conclusions." (Discussion and conclusions)
- Limitation (authors): Single-dish beams may average in surrounding regions and lead to incorrect conclusions  
  > "single-dish measurements could potentially lead to incorrect conclusions about the solar structure depending on how much of the surrounding region is included in the average brightness temperature measurement." (Discussion and conclusions)
- Limitation (authors): One-dimensional models give only mean brightness temperature of a structure  
  > "the one-dimensional approach has a significant disadvantage compared to multidimensional models." (Discussion and conclusions)
- Limitation (authors): Models are hydrostatic while AR and CH profiles appear not to follow that trend  
  > "It should be noted that the ATLCW, AL, and similar atmosphere models are hydrostatic models." (Discussion and conclusions)
- Caveat (inferred, ours): Two free parameters (f_n, f_T) are fitted to three data points for AR and CH, so fits are nearly degenerate and CH f_T errors exceed the value
- Caveat (inferred, ours): Brightness temperatures combine epochs from 1994 to 2020 and different beams (21 to 144 arcsec), so the quiet Sun reference is not simultaneous
- Caveat (inferred, ours): Fractional measurement errors of 5-10% are assumed rather than derived, which sets chi2 and the quoted uncertainties
- Caveat (inferred, ours): Single-dish full-disc beams of tens of arcsec blur the small structures, particularly the limb coronal hole
- Caveat (inferred, ours): Independent scaling of density and temperature ignores hydrostatic consistency of the atmosphere

## Reproducibility

- Data public (paper): Metsähovi data cited as a public solar database; public status of the ALMA SV data not stated explicitly  
  > "Metsähovi Radio Observatory public solar database" (References); "In this paper, ALMA data ADS/JAO.ALMA#2011.0.00020.SV were used." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Identification and reduction details of the Band 3 map
- Missing: AR brightness threshold and exact pixel regions
- Missing: ATLCW model tables and Gaunt factor implementation
- Missing: Fit search grid and per-point uncertainties
- Missing: No code released
- Data volume (inferred): Small: one ALMA Band 3 full-disc map (likely under 1 GB) plus tabulated Metsähovi and literature values
- Score (inferred): 3/5, ALMA project code and numeric tables of inputs and fit results are given, and the model fit is simple, but the Band 3 map reduction, region selection thresholds, model tables and fit implementation are not specified.
- Rediscovery candidate: no, The Band 3 map selection and reduction, the AR threshold and the model implementation are not specified, so the main fits cannot be redone from the paper alone.

## Links

- Method: Brajša et al. (cite: Brajsa2018b) (Band 6 measurement procedure and values followed here)
- Method: Brajša et al. (cite: Brajsa2018a) (Earlier FAL-based brightness temperature calculation procedure)
- Method: van Hoof et al. (cite: vanHoof2014) (Gaunt factor interpolation method)
- Method: Avrett et al. (cite: Avrett2015) (ATLCW atmosphere model)
- Companion: Alissandrakis et al. (cite: Alissandrakis2023) (Band 5 and Band 7 QS brightness temperatures)
- Companion: de Oliveira e Silva et al. (cite: deOliveiraeSilva2022) (SSC-model modelling of the same active region)
- Companion: Urpo et al. (cite: Urpo1997) (Metsähovi QS values at 3.40 and 3.90 mm)
- Related: ALMA Band 3 and Band 6 full-disc solar observations of December 2015
- Related: Metsähovi Radio Observatory solar observations

## Checks

```json
{
 "quotes": 98,
 "quotes_ok": 98,
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
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 92,
  "stated": 46,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
